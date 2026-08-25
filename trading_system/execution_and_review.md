# 执行、持仓与复盘

> **状态：Trading System / Execution Contract**

本页负责把执行决定所依据的原始 Trade Plan 转成实际订单和账户状态，并在成交后继续更新 Primary Test、Context / Competing Tests、所选 Market Path、对手路径和 Pending Outcome。图表事实、订单事实和账户事实必须分开；计划正确不表示订单已生效，图表触发也不表示账户已成交或受到保护。

## 一、执行前复核

提交任何新增风险前重新同步：

- 所选 Market Path 仍有效，目标、周期和时间范围未改变；
- Market / close order 所需的 Entry 前置条件已经发生；或 Trade Plan 明确允许 Stop / Limit 在 Trigger 或成交前预先工作；
- 以计划订单价格、允许成交范围和当前剩余空间计算的 Planned Stop、Reward、成本和 Trader's Equation 仍成立；
- Position Size 与当前风险预算、现有仓位和全部计划层一致；
- 订单方向、类型、价格规则、数量和有效期正确；
- 成交后 Protective Stop 怎样激活、覆盖实际数量；
- 回执不明、部分成交、保护不足、连接或平台异常的处理已经写明。

任何关键输入改变，都返回[交易决策与计划](decision_and_plan.md)重新计算，不因订单已经准备好就沿用过期计划。

## 二、订单生命周期

```text
Trade Plan
→ 提交计划规定的 market / stop / limit order
├─ 提交状态不明 → 核对账户，不重复下单
├─ 已确认工作   → 等待触发、成交、取消或过期
└─ 提交前关键输入改变 → 不提交，建立新的 Decision Record

Working Order
├─ 回执不明 → 核对账户，不重复下单
├─ 被拒绝   → 记录原因，不假定有订单
├─ 路径失效或过期 → 撤单并确认
├─ 未成交   → 继续等待或按计划取消
├─ 部分成交 → 更新实际仓位、剩余数量与保护
└─ 全部成交 → 更新实际仓位与保护
```

订单意图、经纪商确认、图表触发和账户成交是不同事实。撤单请求也不等于订单已经取消；在取消状态得到确认前，仍按可能成交的暴露处理。

没有提交订单的“等待图表确认”属于新的市场事件和决策时点，不保留隐藏的可执行计划。已提交的 Stop / Limit order 则属于 Working Order，并在每个相关事件后复核路径、有效期、计划成交范围下的风险和取消条件。

Execution State 分别保存三个状态面，而不是用一个枚举掩盖并存事实：

```text
Order State：Intent / Submitted Unknown / Working / Partial / Filled
             / Cancel Pending / Canceled / Rejected / Expired
Exposure：Flat / Open(quantity) / Exiting(quantity)
Protection：Not Required / Pending / Adequate / Deficient
```

部分成交可以同时表现为 `Partial + Open + Pending/Adequate`；撤单中可以同时存在 `Cancel Pending` 与可能新增的实际暴露。任何状态转换都以经纪商和账户事实确认，不凭订单意图推定。

相反方向的条件订单若按 OCO 工作，一侧触发、成交或发出撤单请求都不证明另一侧已经取消。确认取消前按两侧都可能成交计算暴露；若异常形成双向或反向实际仓位，先核对净仓位与保护，再按预写异常路径减仓或退出。

## 三、成交事实

每次实际成交记录：

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

未成交不会改写当时的 Market Path；它只表示没有实际仓位。部分成交则只按实际数量计算账户风险，剩余订单是否继续工作服从原计划和当前路径。

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

Stop price 是图表上的保护触发依据，不保证最终 fill。真实账户风险必须容纳合理滑点和异常边界。若另有 Catastrophe Backup，必须独立记录价格、数量、最坏损失和撤换条件，不能把它当成正常 Active Stop。

## 五、保留并关联原始计划

执行决定时已经保留原始 Trade Plan；首次成交只确认实际仓位对应这份计划。此后保留：

- 入场时的 Market Path、目标事件和 horizon；
- 当时可见的支持与反方事实；
- 原条件概率和判断时点；
- 原 Entry、Planned Stop、Targets、数量和管理方式；
- 原 Outcome Criterion 与 Trader's Equation。

成交后的更新另行保存为 current state。不得因最终结果覆盖原始目标、重选 measured-move 端点、借用后来出现的证据，或把另一条 Market Path 改写成原交易理由。

## 六、持仓中的路径更新

持仓管理仍运行完整市场认知和结果路径流程。每根计划观察周期 K 线及其他相关事件先更新认知，再决定是否产生动作：

```text
新市场事实
→ 更新 Market Context、Location 与 Current Structural Tests
→ 同时更新所选路径、对手路径和 Pending Outcome
→ 增强 / 保持 / 削弱 / 失效 / 目标完成 / 新结构替代
→ 按原计划和当前账户状态采取动作
```

认知更新不自动产生交易动作。普通波动、单根反色 K 线或计划周期内正常 pullback 可以使局部证据变化，却不自动要求加仓、减仓、移动 Stop 或退出。

### 路径增强

- 按计划持有；
- 新 breakout、follow-through 或主要结构支持延伸目标时，按预写条件保留 runner；
- 新的 major higher low / lower high 或完整结构形成后，可以降低开放风险。

路径增强不自动许可加仓。新增数量仍须有当前 Entry、Stop、Target、总风险和正 Trader's Equation。

### 路径仍成立但减弱

- 区分普通 pullback、entry disappointment 和实质 premise 变化；
- 按预写分支保持、减仓、收缩当前管理目标或停止新增风险；
- 未重新形成完整正方程前不新增风险；
- 不因一根普通反向 K 线自动反向；
- 不以原路径名称否认实际分离关闭、重叠增加或反方接受。

### 路径失效

- 主动退出，不必等待最远 Active Stop；
- 仓位归零前 Active Stop 继续有效；
- 取消同一路径下的剩余工作订单和计划加仓；
- 记录哪个可观察事实触发 Invalidation。

退出只说明当前风险交换不再成立，不表示原方向永久错误。若原方向后来重新获得接受，必须建立新的 Market Path、Entry、Stop、Target 和方程。

### 强反路径获得接受

- 先退出原交易；
- 反方向是否值得承担风险，重新运行完整流程；
- 原交易者 Stop、旧概率或被困叙述不能直接成为反向交易计划。

对手路径轻微增强只属于所选路径的反方更新；只有它获得足够接受并实质否定所选路径，才触发 Path Invalidation。退出原方向后，反方向仍必须以当前价格经过完整决策门。

### 目标、Stop 或时间条件发生

- 目标到达：按 Outcome Criterion 和计划数量减仓或退出；
- Active Stop 触发：核对实际成交与剩余仓位；
- Session、最迟退出时间或账户约束触发：按计划减仓或退出；
- 同一回放 K 线同时包含目标和 Stop 且顺序无法确定：记为 `SEQUENCE_UNKNOWN`，不选择有利结果。

## 七、三层退出保护

退出保护只有一张最终在场 Stop，另有两条主动判断路径：

1. **Active Protective Stop**：执行或主动判断失败时限制最坏风险；
2. **结构 Invalidation**：合理反向结构已经否定原 Market Path；
3. **强反向动量 Invalidation**：即使尚无漂亮形态，异常强反向 K 线、连续低重叠反向运动或 Always In 明确切换也可能要求退出。

第二、三项可以重叠，都是 Invalidation 证据，不是另外两张 Stop。普通小反向 K 线和所选管理周期的正常 pullback 不自动触发退出。

## 八、Trailing 与 Breakeven

Trailing Stop 只能向降低开放风险方向移动：多头向上，空头向下。只有新结构能够容纳所选周期正常波动，并且替换保护已确认生效后，新 Stop 才成立；撤旧挂新的过程中不能留下无保护空档。

可用锚点包括：

- 新 breakout 建立的 major higher low / lower high；
- 完整走势腿或回调结构；
- 原路径仍成立时的其他有效失效边界。

任意次要 swing、每根盈利 K 线或固定点数不要求机械 trailing。

Breakeven Stop 是把 Active Stop 调整到计划 Entry 或整仓加权平均 Entry 附近的管理选择。它降低名义价格风险，但佣金、滑点、跳空和数量差异意味着账户结果未必为零。Scale-in 后必须使用加权均价，不能机械使用第一笔 Entry 或简单中点。

## 九、数量更新

### Scale-in

原 Trade Plan 内的所有层必须在第一笔 Entry 前进入最坏总风险。新增层前检查：

- 原 Market Path 仍有效；
- 新层来自原计划中的价格改善区域，或来自成交后预写的新确认；不是因为浮亏本身；
- 层数、价格规则和数量仍符合原计划；
- 共同 Stop 与全部实际、剩余层的账户风险仍在上限；
- 强反向证据、时间或成本尚未使方程失效。

`Price-improvement scale-in` 在预定更好价格增加数量，只改善 Entry 和均价，不提高 Market Path 概率；若该价格只是临场看到浮亏后选择，则不属于原计划。`Confirmation scale-in` 依赖新的顺势证据，但仍增加总数量和回撤暴露。无论哪一种，路径失效、保护异常或总风险不再合规时都取消剩余层，不强制完成计划数量。

每层按其 Entry 到共同或独立 Stop 的距离计算账户风险；同为账户 `1%` 风险的两层不要求数量相同。第二层成交后立即按实际总数量确认 Active Protective Stop 覆盖，并把实际仓位、剩余工作订单、成本与滑点重新计入最坏总风险。

原计划之外出现新的可交易结构时，必须建立新的 Decision Record 和完整 Trade Plan，并在提交前把已有仓位、全部工作订单、共同或独立 Stop 及新增层纳入合并最坏风险。它不能事后改写成原计划的 scale-in 层。

### Scale-out

减仓必须来自：

- 已到计划目标；
- 预写的风险收缩或 runner 分支；
- 实质路径削弱或 Invalidation；
- 账户、时间或异常处置。

减仓后更新实际数量、平均价格、Active Stop 覆盖、剩余目标和开放风险。不能因为仓位变小就保留已经失效的 Market Path。

## 十、Scalp / Swing 管理一致性

Scalp、Swing、部分退出和 runner 都是原 Trade Plan 的目标与持有实现。成交后不得因为害怕回吐把 Swing 临时管成 Scalp，也不得把区间内的 Scalp 变成远端 Trend Swing。

若计划预先分配：

```text
Scalp 部分 → 近端目标与较快退出
Runner      → 仅在路径增强和延伸目标启用时继续持有
```

则分别记录数量、Stop、目标和结果。TBTL 只帮助容忍反向 swing 的时间与腿数，不覆盖价格目标、Invalidation 或 Session 约束。

## 十一、交易结果与价格结果

必须分开：

- `Move / Pattern result`：某个突破、H2、旧极值测试或其他价格路径是否达到其目标；
- `Trade outcome`：实际 Entry 发生后，计划 objective、Stop、主动退出等结果顺序；
- `Account result`：实际成交、数量、费用、滑点与退出共同产生的 P&L。

Failed breakout 或 failed H2 不表示某位交易者已经触及 Stop；价格曾提供目标机会也不表示账户实际成交退出。

没有实际成交的候选只能记录为未触发、未成交、过期、等待、不交易或路径失效，不能记为交易 success / failure。

## 十二、Trapped 与行为路径

- `Trapped in`：一方已经实际入场、未先获得其结果目标、仍处于开放亏损并可能被迫退出；
- `Trapped out`：一方等待更好价格、过早退出或未建立所需仓位，随后行情快速发展；
- 曾被困并已退出是历史结果，不再属于当前开放 trapped-in 状态。

Pain Trade 描述两类潜在反应共同推动低预期方向的行为路径。它只能由可见 Entry / Stop 区域、follow-through 和现实空间支持，不表示系统观察到真实订单身份，也不是新的交易类别或 failure state。

## 十三、行为纪律作为系统约束

行为内容只在能改变系统动作时保留：

- 仓位大到使交易者移动 Stop、提前截断赢家或忽略 Invalidation 时，必须降低仓位；
- FOMO、希望回到 Entry、已有浮盈和已实现盈亏不构成新的价格证据；
- 沉没亏损不能降低下一条 Market Path 的资格标准；
- Mental stop 不替代实际保护；
- 临场改变周期、目标、Scalp / Swing 或计划加仓属于计划变化，必须重新计算或停止执行；
- 退出后可以重新入场，因此主动承认当前路径失效不等于永久放弃方向。

规则内亏损与规则错误分开：前者是具有合理方程的计划仍然发生失败结果；后者包括坏位置入场、没有保护、移动 Stop、无计划加仓、改变管理周期或拒绝执行 Invalidation。

## 十四、决策记录

普通 Observation Event 只保存相对上次判断的事实与路径变化。首次作出执行、等待或不交易，或其依据实质改变；提交、修改或取消订单；加减仓、移动保护或退出；Primary Test、Selected Path 或计划关键输入改变；以及路径闭环时，形成：

```text
Decision Record

判断时点：
当时的 Market Model 与适用规则：
运行边界：
Market Context、Location 与 Primary Test：
Bull / Bear / Pending Opportunity Set：
目标事件、周期与时间范围：
支持事实与最强反方事实：
条件概率及适用规则：
Entry / Invalidation / Stop / Target：
Trader's Equation：
决定：执行 / 等待 / 不交易
决定原因与等待项：
路径过期或替代条件：
```

这使未交易路径也能进入后续校准，避免只分析已成交样本。

## 十五、交易与路径复盘

```text
Review Record

原始判断
- Market Path：
- 原目标事件和 Outcome Criterion：
- 原条件概率：
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

单笔赢家、输家或错过不能证明一条规则正确或错误。概率校准要求条件、目标事件、周期、horizon 和判断时点一致的连续样本；样本规则的改变必须进入规则台账，不在复盘中静默修改。

## 十六、证据追溯

本页的订单、成交、Stop、管理和结果边界由 [课程概念索引](../reference/course/concept_index.md)、[边界与冲突](../reference/course/boundaries_and_conflicts.md)、[正式来源台账](../reference/official_sources.md)和逐讲课程 30–36、40–52 的相关材料支持。Reference 负责证据与现实限制；本页负责统一执行契约。
