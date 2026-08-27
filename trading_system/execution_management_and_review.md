# 执行、持仓与复盘

> **状态：Trading System / Execution Contract**

本页负责把被选 Candidate 冻结的 Trade Plan 转成实际订单和账户状态，并在成交后继续更新 Market Read、所选 Opportunity 与现实竞争机会。图表事实、订单事实和账户事实必须分开；计划正确不表示订单已生效，图表触发也不表示账户已成交或受到保护。

本页定义的状态必须真实，但不要求交易者在每次状态转换后手工抄写完整对象。订单、回执、成交和仓位优先使用经纪商或平台的可靠记录；人工只快速核对它们是否一致，并在计划/风险改变或异常时补充最小说明。

执行环境固定保证：杠杆只用于资本效率；账户使用 Cross Margin 或为 Isolated Position 配置足够保证金，使强平边界天然位于 Planned / Active Protective Stop 之外。该条件由账户配置持续保证，不进入每笔交易清单；一旦不再成立即进入 `SAFETY_EXCEPTION`。

## 账户—执行运行图｜按真实状态分派

Flat、Ready、Working、Open、Exiting 和 Closed / Review 是可并行适用的运行入口，不是掩盖并存事实的单一账户枚举。Safety Exception 优先抢占；安全确认后对每项事实独立判断，并运行所有成立的入口：

```text
数据、连接、回执、仓位或保护无法可靠确认
→ SAFETY_EXCEPTION

安全确认后：
├─ 存在实际 Exposure → Open Position
├─ 存在尚未提交且仍有效的 Entry / Add 执行意图 → Ready to Submit
├─ 存在 Working / Cancel Pending 订单 → Working Order
├─ 存在待执行的 Reduce / Exit 动作或相关订单，且仍有 Exposure → Exiting
├─ 交易或路径刚结束，盘中终结确认 / Review 交接尚未完成 → Closed / Review
└─ 以上全部不成立，且没有待完成的盘中关闭动作 → Flat / Observing
```

计划内 Add 可以同时进入 `Open Position + Ready to Submit`；部分成交可以同时进入 `Open Position + Working Order`；退出中可以同时进入 `Open Position + Working Order + Exiting`；仓位归零而残留订单仍待确认时可以同时进入 `Working Order + Closed / Review`。Safety Exception 解除后也按已确认的真实状态重新分派，但异常前的 Entry / Add 意图必须重新通过执行前复核；若 Market Read 已经过期，再从 Frame 重开。

## 一、执行前复核

提交任何新增风险前重新同步：

- 所选 Opportunity 仍有效，Activation、Invalidation、目标、周期和时间范围未改变；
- Entry Basis、Entry Method、适用的 Trigger Boundary、Planned Protective Stop 与 First / Main Target 仍引用原 Price Map / Active Test；
- Market / close order 所需的 Entry 前置条件已经发生；或 Trade Plan 明确允许 Stop / Limit 在 Trigger 或成交前预先工作；
- 以计划订单价格、允许成交范围和当前剩余空间计算的 Planned Stop、Reward、实质相关的 Execution Cost 和 Trader's Equation 仍成立；
- Position Size 与 Risk Limit、现有仓位和全部仍可能增加暴露的订单一致；
- 本执行意图已有累计成交时，待提交数量只等于原计划数量减去累计成交，并按当前 Exposure、Stop 和 Risk Available 重新确认；剩余为零时关闭意图；
- 订单方向、类型、价格规则、数量和有效期正确；
- 成交后 Protective Stop 怎样激活、覆盖实际数量；
- 回执不明、部分成交、保护不足、连接或平台异常的处理已经明确。

Entry 意图的 Market Read、Opportunity、Candidate 方程或订单参数改变时，从最早变化步骤重开，并重新经过 Trade Construction 与 Decision。Add 意图发生这些变化时，关闭旧意图并返回 Open Position / Add Gate；只有计划外的新 Opportunity 才重新建立 Candidate 并提交 Decision。不因订单已经准备好就沿用过期意图。

## 二、订单生命周期

```text
冻结的 Entry / Add 执行意图
→ 提交计划规定的 market / stop / limit order
├─ 提交状态不明 → 核对账户，不重复下单
├─ 已确认工作   → 等待触发、成交、取消或过期
├─ 提交前关键输入改变 → 不提交；Entry 返回 Candidate / Decision，Add 返回 Open Position / Add Gate
└─ 未提交即到期或主动放弃 → 关闭当前执行意图，按真实账户状态重新分派

Working Order
├─ 回执不明 → 核对账户，不重复下单
├─ 部分成交 → 按 Order Purpose 更新实际 Exposure；剩余订单继续 Working
└─ 全部成交 → 按 Order Purpose 与剩余 Exposure 路由

Order Purpose = ENTRY / ADD
├─ Opportunity 不再 ACTIVE、Entry Validity 结束或方程失效 → 撤单并确认
├─ 未成交且仍有效 → 继续等待或按计划取消
└─ Rejected / Canceled / Expired
   → 关闭该订单；执行意图仍有效则只以扣除累计成交后的剩余计划数量重新进入 Ready，否则按真实状态重新分派

Order Purpose = REDUCE / EXIT
├─ Submitted Unknown / Working / Cancel Pending → 继续核对；原保护覆盖剩余 Exposure
└─ Rejected / Canceled / Expired 且仍有 Exposure
   → 进入 Exiting；退出动作仍有效则修复或重新提交
   → 无法可靠执行或保护不足则进入 SAFETY_EXCEPTION
```

订单意图、经纪商确认、图表触发和账户成交是不同事实。撤单请求也不等于订单已经取消；在取消状态得到确认前，仍按可能成交的暴露处理。

Entry / Add 的成交增加 Exposure：部分成交进入 `Open Position + Working Order`，全部成交进入 `Open Position`。Reduce / Exit 的成交减少 Exposure：仍有仓位时继续 `Open Position`，仍有退出订单时并行 `Exiting / Working Order`；仓位归零后先确认残留工作订单与保护的最终状态，再进入 `Closed / Review`。任何订单进入 Rejected、Canceled 或 Expired 后，都关闭该订单事实，再依据剩余 Exposure、其他订单和仍有效的执行意图重新分派。

没有提交订单的“等待图表确认”属于新的市场事件和决策时点，不保留隐藏的可执行计划。已提交的 Stop / Limit order 则属于 Working Order，并在每个相关事件后复核 Opportunity、有效期、计划成交范围下的风险和取消条件。

Execution State 分别保存以下事实面，而不是用一个枚举掩盖并存事实：

```text
Order Purpose：ENTRY / ADD / REDUCE / EXIT
Order State：Intent / Submitted Unknown / Working / Partial / Filled
             / Cancel Pending / Canceled / Rejected / Expired
Exposure：Flat / Open(quantity)
Protection：Not Required / Pending / Adequate / Deficient
Risk：Committed / Available
```

部分成交可以同时表现为 `Partial + Open + Pending/Adequate`；撤单中可以同时存在 `Cancel Pending` 与可能新增的实际暴露。`Exiting` 是存在 Reduce / Exit 订单且仍有 Exposure 时的并行检查入口，不是另一种 Exposure。任何状态转换都以经纪商和账户事实确认，不凭订单意图推定。

`Order Purpose` 决定成交后的路由：Entry / Add 的成交增加 Exposure，Reduce / Exit 的成交减少 Exposure；它不建立另一套 Order State。退出请求、触发或订单意图都不等于仓位已经减少。

## 三、成交事实

每次实际成交必须能从可靠账户记录还原以下事实；平台已留存时不手工重抄：

```text
成交方向：
成交数量：
成交价格：
成交时间：
Actual fill bar：
剩余工作数量：
平均成交价：
费用与已知滑点：
```

Limit price 被 touch 或 cross 不保证成交；Stop order 触发不保证最终成交价。队列、流动性、跳空、停牌、连接和平台异常都可能造成未成交、部分成交或更差 fill。

Chart Entry Bar 只表示 Candidate 的图表 Trigger 已经发生；Actual Fill Bar 才表示账户获得真实仓位，两者可以不同。Entry Bar、follow-through 或 failure 无论账户是否成交都会返回 Current Move / Active Test 更新市场路径；未成交不会改写当时的 Opportunity，只表示没有实际仓位。部分成交则只按实际数量计算账户风险，剩余订单是否继续工作服从原计划和当前 Opportunity。

## 四、实际保护生命周期

```text
实际成交或部分成交
↓
核对当前仓位数量与平均价格
↓
确认 Active Protective Stop
├─ 状态可确认且覆盖全部实际数量 → 正常持仓
└─ 无法确认、数量不足或状态异常 → 保护不足
                                    → 不新增风险
                                    → 按预写异常流程恢复保护、减仓或退出
```

只在心里记住退出价不等于受到保护。Active Protective Stop 必须是实际在场、状态可确认并覆盖当前仓位的订单或平台保护机制。

Stop price 是图表上的保护触发依据，不保证最终 fill。正常高流动性执行可以把预计滑点配置为零；异常流动性、跳空、停牌或平台异常进入 `SAFETY_EXCEPTION`，不在普通计划中反复增加字段。若另有 Catastrophe Backup，必须独立记录价格、数量、最坏损失和撤换条件，不能把它当成正常 Active Stop。

## 五、保留并关联原始计划

执行决定时已经保留原始 Trade Plan；首次成交只确认实际仓位对应这份计划。此后保留：

- 入场时的 Opportunity、目标事件和 Outcome Horizon；
- 当时可见的 Support / Already、Activation、Invalidation、Counterevidence 与竞争 Opportunity；
- 原 Market Probability、Candidate Outcome Probability 和判断时点；
- 原 Entry、Planned Stop、Targets、数量和管理方式；
- 原 Outcome Criterion 与 Trader's Equation。

成交后的当前状态与原计划分开维护；只有改变风险、动作或后续复盘的 Delta 才另行保存。不得因最终结果覆盖原始目标、重选 measured-move 端点、借用后来出现的证据，或把另一条 Opportunity 改写成原交易理由。

## 六、持仓中的 Opportunity 更新

持仓管理仍遵守完整 Market Read 与 Opportunity 语义。每根计划观察周期 K 线及其他相关事件只做数秒扫描：先判断认知是否实质改变，再决定是否产生动作或记录。

```text
新市场事实
→ 继承当前 Context，更新 Price Map、Current Move 与 Active Test
→ 确认原 Context、标记 Transition 或 Reframe
→ 同时更新所选 Opportunity、现实竞争机会与 Likely Sequence
→ 先更新所选 Opportunity 生命周期；仍 Active 时再更新强弱
→ 单独判断竞争 Opportunity 是否出现、是否获得接受
→ 按原计划和当前账户状态采取动作
```

同一根 K 线只识别一次底层事实：它可以先改变 Pressure / Continuity，再改变 Active Test 和 Opportunity，最后触发账户动作，但不能因分别被称为 entry bar、follow-through、disappointment 或 trapped evidence 而重复计票。K 线颜色本身不直接产生 Hold、Add 或 Exit。

持仓中的双向检查以所选 Opportunity 和现实竞争 Opportunity 为核心，不因已有仓位省略反方，也不为每根 K 线重建两份 Candidate：

```text
1. 实际仓位、工作订单与 Active Protective Stop 一致吗？
2. Price Map / Current Move / Active Test 出现了什么新事实？
3. Context 是 UNCHANGED、UPDATED 还是 REFRAMED？
4. 所选 Opportunity 是 ACTIVE、ACHIEVED、INVALIDATED、EXPIRED、SUPERSEDED 还是 SEQUENCE_UNKNOWN？
5. 若仍 ACTIVE，是 STRENGTHENED、UNCHANGED 还是 WEAKENED？
6. 竞争 Opportunity 是否存在；尚未建立、仍待确认，还是已经获得接受？
7. Target、Stop、时间、Add / Cancel Add 或原计划条件发生了吗？
8. 是否形成了能容纳正常波动的新保护锚点？
9. 当前 Actions：Hold / Cancel Add / Add to Ready / Reduce / Trail Stop / Exit？
```

| 所选 Opportunity | 竞争 Opportunity | 当前动作边界 |
| --- | --- | --- |
| `ACTIVE + STRENGTHENED / UNCHANGED` | 不存在或尚未获得接受 | 按计划持有；计划内 Add 运行 Add Gate，计划外新增风险构造新 Candidate |
| `ACTIVE + WEAKENED` | 存在但尚未获得接受 | Hold、Cancel Add，或执行预写减仓 / 目标收缩 |
| `INVALIDATED` | 任意状态 | 主动退出；不必等待最远 Active Stop |
| 因竞争路径接受而 `INVALIDATED / SUPERSEDED` | 已获得接受并实质否定所选路径 | 先退出原交易；反向交易重新经过完整流程 |
| `SUPERSEDED` | 新 Context、价格问题或机会取代原路径 | 停止新增风险并退出；新路径只在归零后重新构造交易表达 |
| `ACHIEVED / EXPIRED / SEQUENCE_UNKNOWN`，或 Target / Stop / Time 条件发生 | 任意状态 | 按 Outcome Criterion 处理并核对实际仓位与保护；顺序未知时不选择有利解释 |

认知更新不自动产生交易动作。普通波动、单根反色 K 线或计划周期内正常 pullback 可以使局部证据变化，却不自动要求加仓、减仓、移动 Stop 或退出。

Actions 可以组合：`CANCEL_ADD + HOLD`、`REDUCE + TRAIL_STOP`、`EXIT + CANCEL_ADD` 都是合法输出；组合只表示同一判断要求完成的动作，不允许从决定跳过订单事实。Cancel Add 终止剩余额度并撤销仍可能增加暴露的 Add Order；Reduce / Exit 进入退出订单生命周期；`REDUCE + TRAIL_STOP` 按实际减仓成交更新 Exposure 后，再 amend / replace 唯一 Active Protective Stop 覆盖剩余仓位。只有动作或风险发生变化时保存 Delta。

若所选 Opportunity、竞争机会、风险、保护、动作和下一条件均未实质改变，只继续观察，不产生逐 K 线记录。

### Opportunity 增强

- 按计划持有；
- 新 breakout、follow-through 或主要结构支持延伸目标时，按预写条件保留 runner；
- 新的 major higher low / lower high 或完整结构形成后，可以降低开放风险。

Opportunity 增强不自动许可加仓。新增数量仍须通过 Context Permission，并有当前 Trigger、Entry、Stop、Target、总风险和正 Trader's Equation。

### Opportunity 仍成立但减弱

- 区分普通 pullback、entry disappointment 和实质 premise 变化；
- 按预写分支保持、减仓、收缩当前管理目标或 Cancel Add；
- 未重新形成完整正方程前不新增风险；
- 不因一根普通反向 K 线自动反向；
- 不以原 Opportunity 名称否认实际分离关闭、重叠增加或反方接受。

### Opportunity 失效

- 主动退出，不必等待最远 Active Stop；
- 仓位归零前 Active Stop 继续有效；
- 取消同一 Opportunity 下的剩余工作订单和计划加仓；
- 记录哪个可观察事实触发 Invalidation。

退出只说明当前风险交换不再成立，不表示原方向永久错误。若原方向后来重新获得接受，必须建立新的 Opportunity、Entry、Stop、Target 和方程。

### 竞争 Opportunity 获得接受

- 先退出原交易；
- 反方向是否值得承担风险，重新运行完整流程；
- 原交易者 Stop、旧概率或被困叙述不能直接成为反向交易计划。

反方事实尚未形成完整竞争 Opportunity 时更新所选路径的 `Counterevidence`；形成后独立更新该竞争 Opportunity。只有竞争路径获得足够接受并实质否定所选 Opportunity，才触发 Structural Invalidation。退出原方向后，反方向仍必须以当前价格形成自己的 Opportunity、Candidate 与 Decision。

### 目标、Stop 或时间条件发生

- 目标到达：按 Outcome Criterion 和计划数量减仓或退出；
- Active Stop 触发：核对实际成交与剩余仓位；部分成交时继续保护剩余 Exposure，全部成交归零后确认残留订单与保护最终状态，再进入 Closed / Review；
- Session、最迟退出时间或账户约束触发：按计划减仓或退出；
- 同一回放 K 线同时包含目标和 Stop 且顺序无法确定：记为 `SEQUENCE_UNKNOWN`，不选择有利结果。

完整 Stop、完整目标或主动退出使仓位归零并终结当前 Trade Plan 的账户结果时，关闭该计划尚未提交的 Entry / Add Execution Intent，终止剩余 Add Permission，并撤销仍可能增加 Exposure 的 Entry / Add Working Order。撤销确认前继续运行 `Working Order + Closed / Review`，按订单仍可能成交计算最坏暴露；若其间发生新成交，立即按真实 Exposure 重新分派并恢复保护或完成退出，不能假定账户仍为 Flat。同方向仍有市场机会时，也必须以当前价格重新建立 Candidate 与 Decision，不能让旧 Intent 或 Add Order 充当重新入场。

### 主动退出与退出订单

Open Position 输出 `REDUCE / EXIT` 后，使用同一订单生命周期处理真实退出，不从动作直接跳到 Closed：

```text
Reduce / Exit 决定
→ 提交 Order Purpose = REDUCE / EXIT 的订单
├─ Submitted Unknown / Working / Cancel Pending
│  → 核对账户，不重复提交；Active Stop 继续覆盖尚未退出的实际数量
├─ Rejected / Canceled / Expired
│  → 若仍有 Exposure，Active Stop 继续覆盖真实数量
│  → 退出动作仍有效：修复或重新提交；无法可靠执行：SAFETY_EXCEPTION
│  → 退出动作已被新事实替代：返回 Open Position 重新判断
├─ Partial
│  → 更新剩余仓位、平均价格、退出订单与 Active Stop 覆盖；继续 Exiting
└─ Filled
   → 若仍有仓位，返回 Open Position
   → 若仓位归零，确认残留工作订单与保护最终状态，再进入 Closed / Review
```

退出订单和 Active Stop 可能竞态成交时，先核对真实净仓位；归零前不撤除剩余保护。异常形成反向仓位、保护不足或回执不明时进入 `SAFETY_EXCEPTION`。

## 七、三层退出保护

退出保护只有一张最终在场 Stop，另有两条主动判断路径：

1. **Active Protective Stop**：执行或主动判断失败时限制最坏风险；
2. **结构 Invalidation**：合理反向结构已经否定原 Opportunity；
3. **强反向动量 Invalidation**：即使尚无漂亮形态，异常强反向 K 线、连续低重叠反向运动或 Always In 明确切换也可能要求退出。

第二、三项可以重叠，都是 Invalidation 证据，不是另外两张 Stop。普通小反向 K 线和所选管理周期的正常 pullback 不自动触发退出。

## 八、Trailing 与 Breakeven

Trailing Stop 只能向降低开放风险方向移动：多头向上，空头向下。一个更近的高低点或价格区域只有同时满足以下条件，才成为新的保护锚点：

1. 新结构已经形成，并与原 Opportunity、Price Map 和 Management Horizon 一致；
2. 价格已从该结构建立足够分离、follow-through 或成功恢复；
3. 新 Stop 仍能容纳该周期的正常波动，不落在普通 pullback 内；
4. 调整降低开放风险，并符合原计划或保存为风险 Delta；
5. 通过 amend / replace 修改当前 Active Protective Stop；以经纪商 / 交易所确认后的新价格与数量为准。确认前仍按原 Stop 和最坏暴露处理，确认后原保护由修改后的 Stop 直接取代。

可用锚点包括：

- 新 breakout 建立的 major higher low / lower high；
- 完整走势段或回调结构；
- 原 Opportunity 仍成立时的其他有效失效边界。

重要位置本身不自动要求 Trail；任意次要 swing、每根盈利 K 线或固定点数也不形成新保护边界。强反向动量或 Structural Invalidation 可以要求主动退出，无需等待一个适合 Trailing 的新锚点。

Breakeven Stop 是把 Active Stop 调整到计划 Entry 或整仓加权平均 Entry 附近的管理选择，也必须通过上述结构与正常波动资格门。它降低名义价格风险，但佣金、滑点、跳空和数量差异意味着账户结果未必为零。Scale-in 后必须使用加权均价，不能机械使用第一笔 Entry 或简单中点。

## 九、数量更新

### Scale-in

第一笔 Entry 前确定 Risk Limit、Initial Limit、共同或独立 Stop、Add Permission 与 Cancel Add；未来层在决策事件发生时计算准确 Entry Basis、价格和数量。新增层通过[总流程 Add Gate](overall_flow.md#add-gate是否使用计划内剩余风险)得到 `ADD_TO_READY` 后进入 Ready to Submit，执行阶段再确认两件事：

- 当前 Context Permission、Entry Basis / Trigger、订单方向、Entry Method、价格、数量与有效期正确，加仓后的 Risk Committed 不超过 Risk Limit；
- 当前保护正常，新层成交后可以修改 Active Protective Stop 覆盖实际总数量。

`Price-improvement scale-in` 在预定更好价格增加数量，只改善 Entry 和均价，不提高 Market Probability；若该价格只是临场看到浮亏后选择，则不属于原计划。`Confirmation scale-in` 依赖新的顺势证据，可以更新 Market Probability 或 Candidate Outcome Probability，但仍增加总数量和回撤暴露。无论哪一种，Opportunity 失效、保护异常或总风险不再合规时都取消剩余层，不强制完成计划数量。

每层按其 Entry 到共同或独立 Stop 的距离计算账户风险；同为账户 `1%` 风险的两层不要求数量相同。尚未下单的保留额度不是实际暴露；已提交并仍可能增加暴露的订单必须计入 Risk Committed。Active Stop 位于盈利区域时，该仓位的 Stop Risk 以零为下限，不用已保护利润抵消新订单风险。Trail 后释放的额度也不自动授权 Add。新层成交后立即修改并确认 Active Protective Stop 覆盖实际总数量，再更新实际仓位、剩余工作订单、Execution Cost 与 Risk Committed / Available。

`CANCEL_ADD` 时，尚无加仓订单则撤销剩余额度的使用资格；已有 Working Add 则撤单并确认，确认前继续计入 Risk Committed。计划内 Add 只在原 Trade Plan 追加 Entry Basis、Trigger、Entry Method、价格、数量、Stop、加仓后 Risk Committed 与触发依据。原计划之外出现新的 Opportunity、目标、失效或 Stop 时，必须建立新的 Candidate；决定 Execute 时冻结新的 Trade Plan，并在提交前把已有仓位、全部工作订单、共同或独立 Stop 及新增层纳入 Risk Limit。它不能事后改写成原计划的 scale-in 层。

### Scale-out

减仓必须来自：

- 已到计划目标；
- 预写的风险收缩或 runner 分支；
- Opportunity 实质削弱或 Invalidation；
- 账户、时间或异常处置。

减仓后更新实际数量、平均价格、Active Stop 覆盖、剩余目标和开放风险。不能因为仓位变小就保留已经失效的 Opportunity。

## 十、Scalp / Swing 管理一致性

Scalp、Swing、部分退出和 runner 都是原 Trade Plan 的目标与持有实现。成交后不得因为害怕回吐把 Swing 临时管成 Scalp，也不得把区间内的 Scalp 变成远端 Trend Swing。

若计划预先分配：

```text
Scalp 部分 → 近端目标与较快退出
Runner      → 仅在路径增强和延伸目标启用时继续持有
```

则分别记录数量、Stop、目标和结果。TBTL 只帮助容忍反向 swing 的时间与段数，不覆盖价格目标、Invalidation 或 Session 约束。

## 十一、交易结果与价格结果

必须分开：

- `Move / Pattern result`：某个突破、H2、旧极值测试或其他价格路径是否达到其目标；
- `Trade outcome`：实际 Entry 发生后，计划 objective、Stop、主动退出等结果顺序；
- `Account result`：实际成交、数量、费用、滑点与退出共同产生的 P&L。

Failed breakout 或 failed H2 不表示某位交易者已经触及 Stop；价格曾提供目标机会也不表示账户实际成交退出。

没有实际成交的候选只能记录为未触发、未成交、过期、等待、不交易或 Opportunity 失效，不能记为交易 success / failure。

## 十二、Trapped 与行为路径

- `Trapped in`：一方已经实际入场、未先获得其结果目标、仍处于开放亏损并可能被迫退出；
- `Trapped out`：一方等待更好价格、过早退出或未建立所需仓位，随后行情快速发展；
- 曾被困并已退出是历史结果，不再属于当前开放 trapped-in 状态。

Pain Trade 描述两类潜在反应共同推动低预期方向的行为路径。它只能由可见 Entry / Stop 区域、follow-through 和现实空间支持，不表示系统观察到真实订单身份，也不是新的交易类别或 failure state。

Trapped、disappointment 和预期退出压力若由已经记录的 Entry、failure 或 follow-through 推断，不在这些价格事实之外再次增加证据。后续新发生的 follow-through、回测或退出加速仍各自更新路径一次；行为解释只说明它们为何可能发生，不能重复增加概率。

## 十三、行为纪律作为系统约束

行为内容只在能改变系统动作时保留：

- 仓位大到使交易者移动 Stop、提前截断赢家或忽略 Invalidation 时，必须降低仓位；
- FOMO、希望回到 Entry、已有浮盈和已实现盈亏不构成新的价格证据；
- 沉没亏损不能降低下一条 Opportunity 的资格标准；
- Mental stop 不替代实际保护；
- 临场改变周期、目标、Scalp / Swing 或计划加仓属于计划变化，必须重新计算或停止执行；
- 退出后可以重新入场，因此主动承认当前 Opportunity 失效不等于永久放弃方向。

规则内亏损与规则错误分开：前者是具有合理方程的计划仍然发生失败结果；后者包括坏位置入场、没有保护、移动 Stop、无计划加仓、改变管理周期或拒绝执行 Invalidation。

## 十四、执行事件的必要记录

记录时点由[总流程](overall_flow.md#六必要记录)统一规定。执行阶段分开处理三类信息：

| 类型 | 最小处理 |
| --- | --- |
| 普通订单、回执、成交、费用和当时仓位 | 使用经纪商/平台原始记录，只快速核对，不人工重抄 |
| 修改计划、新增或降低风险、加减仓、移动保护、主动退出 | 在原 Trade Plan 上追加 Delta：时点 + 变化 + 原因 + 确认后的数量/保护 |
| 状态不明、部分成交、保护不足、意外反向仓位或基础设施异常 | 保存：发现时的最坏暴露 + 处置动作 + 最终确认结果 |

普通持有、订单按原计划继续工作、或无成交的正常到期，若未改变计划、风险或复盘结论，不生成叙事性记录。订单意图、图表 Trigger 和账户事实在语义上仍然分开；保存方式可以分别是计划简记、图表标记和平台记录。

## 十五、交易与路径复盘

复盘在交易或路径结束后进行，不与 5 分钟图上的实时管理争夺注意力。盘中只需确保原计划、必要 Delta、执行事实和终结事实没有丢失。

每笔交易的最小盘后复盘只需：

```text
关联：原 Trade Plan；未成交路径复盘使用 Decision Record
结果：Market result + Trade outcome + Account result
流程：按计划 / 正常不确定 / 系统违规
关键差异：最多一两项，无则记无
```

只有异常、系统违规、计划多分支、路径顺序不明，或样本要用于规则校准时，才展开下列完整 Review Record：

```text
Review Record

原始判断
- Opportunity：
- 原目标事件和 Outcome Criterion：
- 原 Market Probability / Candidate Outcome Probability：
- 原 Trade Plan：

执行
- 订单、回执和实际成交：
- Active Protective Stop：
- 部分成交、加减仓和异常：

持仓更新
- 路径怎样增强、削弱或失效：
- Stop 与目标怎样按计划调整：
- 是否遵守原周期和管理方式：

结果
- 原目标事件是否在时间范围内发生：
- Market result、Trade outcome 和 Account result：
- 费用、滑点与 P&L：
- 偏差来源：价格结果 / 结构 / 目标 / 概率 / 计划 / 风险 / 执行
- Process result：正常不确定结果还是系统违规：
```

单笔赢家、输家或错过不能证明一条规则正确或错误。概率校准要求条件、目标事件、周期、Outcome Horizon 和判断时点一致的连续样本；样本规则的改变必须进入规则台账，不在复盘中静默修改。

仓位归零后必须先应用本页的 Trade Plan 终结规则，并确认剩余工作订单和保护订单的最终状态，再进入 Closed / Review。盘中终结事实保存、需要深入分析的问题已交给盘后 Review 后，即可返回 Flat / Observing；详细复盘不阻止下一笔交易。关联 Opportunity 若仍为 `ACTIVE` 则继续更新；若已结束则等待新问题；若 Context 已经过期则从 Frame 重开。

## 十六、证据追溯

本页的订单、成交、Stop、管理和结果边界由 [课程概念索引](../reference/course/concept_index.md)、[边界与冲突](../reference/course/boundaries_and_conflicts.md)、[正式来源台账](../reference/official_sources.md)和逐讲课程 30–36、40–52 的相关材料支持。Reference 负责证据与现实限制；本页负责统一执行契约。
