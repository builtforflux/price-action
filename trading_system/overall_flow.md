# 价格行为交易系统总流程

> **状态：Trading System / Runtime Contract**

本页是唯一运行入口。盘中沿一条因果链工作：确认账户安全，读取位置与过程，分别构造现实多空路径，把选中路径转成当前可执行的 Entry / Stop / Target，最后按账户事实执行和更新。

```text
Safety
→ Frame + Inherited Context
→ Price Map
→ Current Move
→ Active Test
→ Confirm / Transition / Reframe Context
→ Long / Short Opportunity Set + Likely Sequence
→ Trade Construction
→ Trade Gate：Execute / Wait / No Trade
→ Order / Position / Protection
→ Event Update / Exit / Review
```

## 盘中一屏卡

首次看图、Reframe 或决策事件使用完整卡；普通 K 线只运行后面的三问增量扫描。所有项目都是观察顺序，只有跨过计划、风险、执行或复盘边界的变化才记录。

```text
Safety   仓位 / 工作订单 / 最坏暴露 / 实际保护 / 数据与连接

Frame    交易周期 / horizon / Session / 剩余时间 / 相关外层约束
Context  继承的市场组织 / Control / Breakout Mode、Climax、Transition

Map      Current Area；Above / Below Regions；来源、汇合、距离与空间

Move     From / Now / Role
  Bars        实体、收盘、影线、相对大小
  Continuity  同向连续性与 follow-through
  Separation  gap 保持、缩小、关闭；overlap 是否增加
  Pullback    深度、持续时间、gap 与原方向恢复速度
  Opponent    反方 K 线、跟随和失败尝试
  Result      Buying / Selling Pressure；Control 保持、减弱或转移

Test     Object / Stage / Attempt / Scale / Response / Next / Expiry
Confirm  Keep Context / Transition / Reframe

Long     Role / horizon；Objective / Targets；Already → Next；
         Activation / Invalidation；Areas；Against；Expiry
Short    使用相同字段
Sequence 两侧能否顺序实现，哪个事实会切换当前路径

Construct  判断时点；Trigger；Stop / Limit / Market Entry；
           Planned Protective Stop；First / Main Target；Size / Management
Gate       Permission；Probability；Reward / Risk / Cost / Time；
           Execute / Wait / No Trade
```

普通新 K 线只问：

1. `Price Map / Current Move / Active Test` 出现了什么新事实？
2. `Context / Long / Short Opportunity` 是否因此改变？
3. `Candidate / Plan / Risk / Action` 是否因此改变？

都是“否”就结束，不记录。

## 一、运行对象与职责

| 对象 | 唯一职责 | 权威文档 |
| --- | --- | --- |
| Market Read | 继承 Context，更新 Price Map、Current Move 与 Active Test，再确认或重构 Context；不选择交易方向 | [Market Read 与 Opportunity](market_read_and_opportunities.md) |
| Opportunity Set | 分别表达现实 Long / Short 市场结果的 objective、目标、Already → Next、Activation、Invalidation、Against、horizon 与可能顺序 | [Market Read 与 Opportunity](market_read_and_opportunities.md#十从-market-read-到-opportunity-set) |
| Trade Candidate / Plan | 为当前允许且可表达的 Opportunity 构造 Trigger、Entry、Planned Protective Stop、Targets、Size、结果概率与管理；选中后冻结为 Trade Plan | [交易决策与计划](decision_and_plan.md) |
| Execution State | 保存实际订单、成交、敞口与 Active Protective Stop | [执行、持仓与复盘](execution_management_and_review.md) |

Frame、Safety、Decision 和 Review 是运行门，不需要另建复杂对象。Pattern 只压缩结构、次序或外层角色；H2、Double Bottom、Wedge、Flag、MTR、ii / ioi 等名称通过 Market Read 改变现有对象，不产生 Setup 路由。

## 二、Safety｜真实风险优先

每次承担新风险或处理账户事件前确认：

```text
实际净仓位与可能暴露
→ 全部工作订单与回执
→ Active Protective Stop 是否覆盖实际数量
→ 行情、账户、连接与已知事件风险是否可靠
```

结果为 `SAFE` 才进入市场与交易决策；不一致时进入 `SAFETY_EXCEPTION`，动作限于核对、恢复保护、撤单、减仓或退出。

## 三、Market Read｜先读位置与过程，再确认背景

### 1. Frame + Inherited Context

首次看图或 Context 已失效时，从暂定分类或 `UNCLEAR` 开始；连续观察时继承上一次确认结果。只取得本轮判断需要的边界：

- Trading Timeframe、scalp / swing horizon、相关外层约束；
- Session、剩余时间、波动、流动性与已知事件风险；
- 继承的 Breakout / Spike、Tight Channel、Broad Channel、Trending Trading Range、Trading Range 或 Unclear；
- Bull / Bear / Balanced / Unclear Control；
- Breakout Mode、Climactic Move Candidate、Confirmed Climax 或 Transition。

这一步的 Context 是比较基线。当前价格事实在第 5 步决定保持、转换还是重构它。

### 2. Price Map｜唯一登记价格区域

1. 确定 Current / Active Area；
2. 标出当前 horizon 相关的上方与下方区域；
3. 每个区域保留来源、汇合、距离和可用空间，同一价格带只登记一次；
4. 当前运动到达、穿越或离开的区域优先进入活动地图。

来源包括旧高低、区间边界、突破点与运动起点、gap、50%、EMA / 趋势线 / 通道线、事前固定 MM 和 Session 水平。

Price Map 不永久分配方向角色。同一区域可以是一条 Opportunity 的 Potential Entry Area / Target / Obstacle / Invalidation Reference，同时承担对手机会的另一角色；角色在第 6 步分配。

### 3. Current Move｜价格怎样来到这里

```text
From    此前是什么方向运动、回调或区域反应
Now     Up Leg / Down Leg / Pause / Local Balance
Role    Continuation / Pullback / Range Leg / Reversal Attempt / Unresolved
Bars    实体、收盘、影线和相对大小
Continuity  同向连续性与 follow-through
Separation  gap / breakout separation 保持、缩小或关闭；overlap
Pullback    深度、持续时间、gap 与原方向恢复速度
Opponent    反方 K 线质量、跟随和失败尝试
Result      Buying / Selling Pressure 与 Control 变化
```

输出是一条连续价格事实链，不是形态名称清单。

### 4. Active Test｜市场正在解决什么问题

```text
Object    正在测试 Price Map 中哪个区域、边界或旧 Control
Stage     Approach / Touch / Reaction / Breakout Attempt /
          Follow-through / Acceptance / Failure / Pending
Attempt   第一次、第二次或第三次尝试
Scale     外层位置测试与局部触发测试
Response  分离、拒绝、突破、重叠或重新进入旧区域
Next      下一项能够解决当前测试的可观察事实
Expiry    最迟何时该问题仍有意义
```

默认检查当前 horizon 的外层位置和局部触发两个尺度。更大或更小尺度只有在会改变目标、正常波动、失效或动作时才进入本轮判断。

### 5. Confirm / Transition / Reframe

- 新事实仍符合原 Context 的正常回调、目标和双边获利能力：`KEEP`；
- 原方向 Pressure 减弱，反方尚未建立持续接受，但正常回调或管理边界开始改变：`TRANSITION`；
- 新区域接受、Control、正常回调、目标或双边获利能力跨过原边界：`REFRAME`；
- 证据仍不足：保留 `UNCLEAR`，使用对应保守 Permission。

Pressure 减弱、反方 Pressure 建立与 Control 转移是不同结果。只有确认后的 Context 才进入 Opportunity 和 Context Permission。

## 四、Opportunity Set｜先完成双向路径，再选择表达

每次决策事件分别扫描 Long 与 Short。现实路径使用同一契约：

```text
Opportunity
- Direction + Role + Horizon
- Objective + Market Outcome Criterion
- Market Targets
- Why：来源去重后的价格事实链
- Already → Next
- Activation
- Invalidation：区域引用 + 否定路径的市场事件
- Price Region Roles：Support / Resistance / Potential Entry Area / Obstacles /
  Magnets / Targets /
  Invalidation Reference
- Against：最强反方事实或竞争 Opportunity
- Market Probability / Rule Match
- Expiry
```

每一侧都应得出明确结果：形成现实 Opportunity、继续等待下一事实，或因没有现实 objective、空间、时间而排除。排除一侧只需保留原因，不为形式对称构造完整对象。

### Likely Sequence

Correction、continuation、range return 与 reversal 可以顺序发生。例如强空头背景可以先形成 `Up / Correction` 到 EMA 或 50%，随后 `Down / Continuation` 再测试旧低。只有顺序会改变当前选择或管理时，才保存一句 `Likely Sequence`。

同方向的不同 objective 或 horizon 分开表达：`Long / Correction` 的目标、概率和失效不能借给 `Long / Reversal`。双向扫描完成前不得进入 Trade Construction。

### 价格区域怎样获得运行角色

```text
Price Map 中唯一的 Region
→ Active Test 说明价格怎样与它互动
→ Long / Short Opportunity 分别赋予 Support / Resistance、Entry Area、
  Obstacle、Magnet、Target 或 Invalidation Reference 角色
→ Trade Candidate 把选中角色转成可执行价格
```

Target 必须来自已经形成的区域、固定结构或事前投射，并明确 touch、进入区域、越过或 acceptance 的到达口径。Invalidation 必须同时说明引用区域和否定路径的市场事件。

## 五、Trade Construction｜把路径转成 Entry / Stop / Target

Objective、horizon、Activation rule 与 Invalidation 完整，且 Context Permission 允许时才考虑构造 Candidate。通常要求 Activation 已完成；唯一例外是计划明确允许预挂条件单，并且订单 Trigger 本身完整执行尚缺的 Activation 条件。若 Activation 还要求 bar close、follow-through、回踩守住或 acceptance，单纯越过一个 stop price 不能替代这些事实，当前结果仍是 Wait。

```text
Trade Candidate
- Opportunity Snapshot / 判断时点
- Early / Confirmed：当前承担哪一阶段的风险
- Trigger Boundary
- Entry：Stop / Limit / Market-Close；价格规则、有效期与取消条件
- Opportunity Invalidation 引用
- Planned Protective Stop：结构锚点、正常波动与账户风险
- First Target / Main Target / Outcome Criterion
- Position Size + Cost / Slippage + Time + Management
- Candidate Outcome Probability + Trader's Equation
- 成交后必须看到的事实
```

订单类型服从当前仍需怎样承担风险：Candidate 需要价格先向计划方向越过 Trigger Boundary 时使用 Stop entry；位置与 Context 已足以承担较少确认、且计划允许价格改善时使用 Limit entry；breakout、follow-through 或 acceptance 已完成且延迟成本更高时可以使用 Market / close entry。

同一 Opportunity 的早期 trigger、follow-through、回踩或 H1/H2 是不同判断时点。每个 Candidate 都使用当前 Entry、Stop、剩余空间、成本与结果概率重新计算。

### Entry、Invalidation、Stop 与 Target 的引用链

- Entry 引用 Price Region、signal-bar 边界或 Active Test 的 Trigger Boundary；
- Market Target 引用 Price Map 中已有区域或事前固定投射；Candidate 再选择 First / Main Target；
- Structural Invalidation 引用 Price Region，并规定怎样才算反侧获得接受或原路径失败；
- Planned Protective Stop 引用局部结构并容纳对应周期正常波动；它是 Candidate 的账户风险边界；
- 成交后的 Active Protective Stop 是真实工作并覆盖实际数量的订单。

Protective Stop 先于完整 Structural Invalidation 触发时，原 Candidate 结束，但市场 Opportunity 未必已经失效。

## 六、Trade Gate｜当前唯一决定

构造完成后依次检查：

1. 双向扫描是否完成，为什么选择当前 Opportunity；
2. Context Permission 是否允许；Activation 已满足，还是由许可的条件 Trigger 完整执行；
3. Entry、Stop、Targets 是否能追溯到 Price Map 或 Active Test；
4. 当前 Entry 到合理 Stop 的 Risk；
5. 第一现实目标和主要目标前的净 Reward；
6. Candidate Outcome Probability、成本、滑点、剩余时间与管理；
7. Size、账户风险与执行可靠性。

| 结果 | 动作 | 必须明确 |
| --- | --- | --- |
| Candidate 完整、方程成立、账户可靠表达 | `EXECUTE` | 提交订单、有效期、成交后保护与预期 |
| 当前问题仍值得跟踪，但缺 Next / Activation 或当前表达 | `WAIT` | 下一可观察事件与 Expiry |
| 当前没有现实 Candidate 或值得等待的事件 | `NO_TRADE` | 排除原因；新 Reframe 后再评 |

已提交并等待成交的 Stop / Limit 属于 Working Order，不是 Wait。

## 七、Event Update｜只沿变化传播

```text
1. Safety 或账户事实变了吗？
2. Price Map / Current Move / Active Test 变了吗？
3. Context 需要 Keep、Transition 或 Reframe 吗？
4. Long / Short Opportunity、Likely Sequence 或区域角色变了吗？
5. Candidate、Trade Plan、Risk 或 Action 需要变吗？
```

第 2–5 步没有跨过原边界时，结果是 `NO_CHANGE`：继续观察、继续工作原订单或按计划持仓，不产生人工记录。

以下事件展开相关步骤：首次看图或 Reframe、surprise bar、到达重要区域、第二或第三次测试、breakout / failed breakout、gap 状态显著变化、新 Trigger / Candidate，以及计划、订单、仓位、保护或风险变化。只有交易周期、主导组织、Control、当前区域问题或 Opportunity Set 被替代时，才重做完整 Market Read。

## 八、订单与持仓路由

完整生命周期由[执行、持仓与复盘](execution_management_and_review.md)拥有。

### Working Order

- 核对订单回执、可能最坏 Exposure、有效期和成交后保护；
- Opportunity 失效、成交范围外方程不再成立或订单过期时撤单并确认；
- 部分成交、撤单中或 OCO 另一侧未确认撤销时，按仍可成交的最坏暴露处理。

### Open Position

每个相关事件先同步实际仓位与保护，再更新所选 Opportunity 和竞争 Opportunity，最后映射到原 Trade Plan：

```text
Account / Protection
→ Price Map / Current Move / Active Test
→ Confirm / Reframe Context
→ Selected Opportunity vs Competing Opportunity
→ Target / Invalidation / Time / Plan Conditions
→ Hold / Stop Adding / Reduce / Trail / Exit
→ 确认实际仓位、订单与 Active Protective Stop
```

| 机会与计划变化 | 允许动作 |
| --- | --- |
| 增强或保持 | 按计划持有；新增风险仍需新 Candidate |
| 削弱但未失效 | 持有、停止新增风险，或执行预写减仓 / 目标收缩 |
| 所选 Opportunity 失效 | 取消剩余新增风险并主动退出；归零前维持保护 |
| 反方 Opportunity 获得接受 | 先处理原仓位；反向交易重新构造 Candidate |
| Target、Active Stop、时间或账户条件发生 | 按 Outcome Criterion 处理并核对实际剩余仓位 |
| 新结构形成有效保护锚点 | 只有容纳正常波动并降低开放风险时才提交 Stop amend / replace；以确认后的新价格和数量为准 |

退出原方向不提供反向交易许可。Trapped traders 和预期退出压力只解释已发生的失败与跟随链。

## 九、必要记录

系统按事件保存最小增量：

| 事件 | 保存内容 |
| --- | --- |
| 普通观察，机会、风险和动作未变 | 无 |
| 新市场问题或 Opportunity 实质改变下一观察 | 变化 + Next / Expiry |
| 形成 Execute，或需要跨事件跟踪的 Wait | 最小 Decision Record |
| 普通扫描得到 No Trade | 无；只有改变观察计划、风险或规则样本时记原因 |
| 选中 Candidate 或实质修改计划、仓位、保护或风险 | 冻结 Trade Plan 或追加 Delta |
| 成交、拒单、部分成交、撤单确认、异常、减仓或退出 | 平台原始事实 + 必要差异 |
| Opportunity 或交易结束 | 终结事实；盘后复盘 |

```text
Decision Record
- 时点 + 品种 / 周期
- 决定：Execute / Wait / No Trade
- Market Read：Context + 当前区域 / 测试（一短句）
- Long / Short 结论 + 所选 Opportunity / Likely Sequence
- 边界：Next / Activation / Target / Invalidation / Expiry
- 如执行：Entry Method + Entry + Planned Stop + Target + Size
```

复杂多层、多目标、跨 Session、OCO 或异常计划才展开完整字段。平台已可靠保存的订单、成交和费用不人工重抄。

## 十、账户状态快速清单

### 空仓观察

- 当前 Context、Active Area、Current Move 与 Active Test 是什么？
- Long 和 Short 分别准备完成什么，下一事实是什么？
- 当前只需继续观察，还是出现了决策事件？

### 准备下单

- 双向扫描完成了吗，为什么选择当前 Opportunity？
- Context Permission 是否允许；Activation 已满足还是由许可的条件 Trigger 完整执行？
- Entry 使用 Stop、Limit 还是 Market；引用哪个 Trigger / Region？
- Structural Invalidation、Planned Stop、First / Main Target 分别来自哪里？
- Size、成本、有效期与成交后预期清楚吗？
- 当前账户可以可靠表达它吗？

### 订单工作中

- 实际 Order State 和最坏 Exposure 是什么？
- Opportunity、成交范围、有效期和方程仍成立吗？
- 如果现在成交，保护会立即覆盖实际数量吗？

### 持仓管理

- 实际数量与 Active Protective Stop 一致吗？
- `Price Map / Current Move / Active Test` 出现了什么新事实？
- 所选 Opportunity 增强、保持、削弱还是失效？
- 竞争 Opportunity 只是出现，还是已经获得接受？
- Target、Active Stop、时间或原计划条件发生了吗？
- 是否形成了能容纳正常波动的新保护锚点？
- 现在的计划动作是 Hold、Stop Adding、Reduce、Trail 还是 Exit？

### 异常状态

- 真实净仓位、所有可能成交订单和最坏暴露是什么？
- 保护、数据、连接或回执哪里不一致？
- 当前安全动作是核对、恢复保护、撤单、减仓还是退出？

## 十一、系统不变量

- Market Read 先固定位置与价格事实，再分别构造 Long / Short Opportunity。
- Context 先继承，后由 Current Move 与 Active Test 确认、转换或重构。
- Price Map 唯一登记区域；Support / Resistance、Entry Area、Obstacle、Magnet、Target 和 Invalidation Reference 是 Opportunity 角色。
- Pattern 名称只解释 Price Process；新位置、新测试、新反应和 follow-through 才提供事实增量。
- Correction、reversal、continuation 与 range return 按 objective 和 horizon 分开，并可按 Likely Sequence 顺序发生。
- 双向 Opportunity 扫描完成后，才为当前可表达的少数机会构造 Candidate。
- Market Targets 与 Structural Invalidation 属于 Opportunity；Candidate 选择 First / Main Targets，并拥有 Trigger、Entry 和 Planned Protective Stop；Active Protective Stop 属于 Execution State。
- Market Probability 与 Candidate Outcome Probability 分开；只有后者与当前 Entry、Stop、退出、成本和管理进入 Trader's Equation。
- 认知变化不自动产生交易动作；新增风险永远重新经过 Trade Construction、Trade Gate 和账户安全检查。
- 普通未变事件不记录；Wait、No Trade、未成交机会、实际交易和规则样本分别闭环。
