# 价格行为交易系统总流程

> **状态：Trading System / Runtime Contract**

本页是唯一运行入口。系统为持续变化和不确定性而设计：稳定的是事实边界、更新规则、风险上限和行动纪律，不是某次市场判断。入场前判断是否值得承担风险，入场后判断是否仍值得承担当前风险。

```text
相关事件
→ Safety Gate：先核对订单、敞口、保护和数据
→ Event Gate：判断增量更新还是完整重构
→ 更新 Market Context、Location 与 Current Structural Tests
→ 更新向上 / 向下 Market Paths 与 Pending Outcome
→ 比较当前可表达的风险交换
→ 按 Execution State 执行允许的动作
→ 记录决定、变化和下一观察条件
→ 等待下一相关事件
```

## 一、运行对象与权威边界

| 对象 | 唯一职责 |
| --- | --- |
| Runtime Snapshot | 固定判断时点及当时可见的市场、时间、订单、账户、数据和适用规则 |
| Market Model | 保存 Market Context、Location、Pressure / Control、活动边界和结构测试 |
| Current Structural Test | 表达价格正在从什么方向检验哪个区域或结构命题 |
| Opportunity Set | 保存同一 Primary Test 下的向上、向下与 Pending 结果 |
| Market Path | 描述从当前测试到一个明确市场目标事件的条件路径 |
| Decision Record | 记录重要决策时点使用的事实、路径、规则、账户状态和决定 |
| Trade Plan | 把一条 Market Path 转成当前时点完整的风险表达 |
| Execution State | 保存实际订单、成交、敞口和 Active Protective Stop |

图表事实、订单事实和账户事实分别保存。图表 Trigger 不能证明账户成交，价格触及 Limit 不能证明实际 fill，计划中的 Stop 也不能证明仓位已经受到保护。

Pattern 只是同一底层事实的结构、位置、次序或角色视图。H2、Double Bottom、Wedge、Flag、MTR 等名称若来自同一次运动、同一位置或同一测试次序，只形成一份证据簇，不选择另一套运行逻辑。

执行决定形成时保留原始 Trade Plan；首次实际成交对应这份计划。Execution State 随账户事实更新，不能写回原计划。后续新增风险不属于原计划层时，必须形成新的 Decision Record 和 Trade Plan。

## 二、Safety Gate 与 Event Gate

### Safety Gate

每次运行先处理实际暴露，再考虑市场机会：

```text
账户与订单对账
> 未保护或保护不足的敞口
> 过期、失效或状态不明的工作订单
> 已有持仓管理
> 新增风险
```

账户状态不明、关键数据不完整或实际保护不足时，不新增风险；按预写异常路径核对、恢复保护、撤单、减仓或退出。

### Event Gate

系统只处理能够改变风险、判断或下一观察条件的相关事件：

| 事件 | 处理 |
| --- | --- |
| Safety Event | 成交、拒单、撤单、部分成交、保护或基础设施异常；立即处理实际暴露 |
| Observation Event | 观察 K 线完成，重要区域被接近、触及、越过、重新进入，或 Entry、目标、时间条件发生；增量更新 |
| Reframe Event | 主要边界、周期、Market Context 或 Primary Test 被解决、失效或替代；完整重构 Market Model 与 Opportunity Set |

初始化和 Reframe Event 才要求完整重扫。普通 Observation Event 从上一次判断出发，只记录新增事实怎样增强、保持、削弱、完成或否定已有路径。认知可以改变而不产生交易动作。

## 三、更新 Market Frame

市场知识按照[市场结构与结果路径](market_structure_and_paths.md)更新：

```text
K 线、价格运动与参照区域
→ Separation / Overlap
→ Approach / Test / Breakout Attempt
→ Reaction / Follow-through
→ Acceptance / Failure / Still Pending
→ Pressure / Control
→ Market Context + Location + Current Structural Tests
```

Market Context 至少区分交易周期的 Trend / Trading Range、Trend 阶段和外层关系；Breakout Mode、Climax、Transition、Session 等作为叠加信息。未知、冲突和不同周期可以并存，不把不确定性伪装成唯一标签。

不同周期或区域的 Current Structural Tests 可以同时存在，但必须标明角色：

- `Primary`：当前价格正在直接解决、当前 Trade Plan 可以绑定的测试；
- `Context`：更大周期或外围测试，约束 Primary 的目标、空间和正常波动；
- `Competing`：可能取代 Primary 的竞争解释或反路径测试。

角色相对于当前评价范围定义。一个 Trade Plan 只绑定一个 Primary Test 和一条 Market Path；不同周期或 horizon 若要独立承担风险，必须建立各自的 Decision Record 与 Trade Plan。Context 与 Competing Tests 继续作为支持、反方或替代事实更新，不因未被选择而删除。

这一阶段只使用当时可见事实。Candidate measuring gap、potential exhaustion、final flag、climax 等包含后续结果的名称不能用最终结果回填当前判断。必要周期、区域或边界无法识别时，记录未知并等待或不交易。

## 四、建立并更新双向路径

每个 Primary Test 都从三个问题展开：

| 问题 | 证据范围 |
| --- | --- |
| 价格在哪里？ | 当前与外层 Context、Location、前方障碍和剩余时间 |
| 价格怎样到达？ | Push、Leg、Pullback、H/L、Gap、Overlap、Pressure 与 Control |
| 市场怎样回应？ | Touch、Reaction、Breakout、Follow-through、Acceptance 与 Failure |

然后建立：

```text
Opportunity Set
├─ 向上路径
├─ 向下路径
└─ Pending Outcome
```

双向考虑的最低要求是说明：双方为什么可能承担风险、各自期待什么市场目标、需要什么后续证据，以及在哪里被证明错误。Pending Outcome 描述当前测试继续未决的现实方式。明显缺少目标、空间、时间或必要条件的方向记录排除原因即可，不为形式完整制造伪路径，也不必为双方都构造 Trade Plan。

每条值得跟踪的 Market Path 绑定来源测试、目标事件与到达口径、周期、horizon、支持与最强反方事实、下一预期、增强和削弱条件、失效条件及适用概率。路径生命周期为：

```text
ACTIVE
├─ 目标事件发生             → ACHIEVED
├─ 市场事实实质否定         → INVALIDATED
├─ horizon 结束             → EXPIRED
├─ 新结构或测试取代         → SUPERSEDED
└─ 目标与失效顺序无法确认   → SEQUENCE_UNKNOWN
```

增强、保持和削弱是 `ACTIVE` 内一次事件的更新结果，不是生命周期状态。市场路径是否有效也不等于当前是否值得交易：账户预算、Entry、成本、时间或目标空间只能使 Trade Plan 不成立，不能改写市场目标本身。

## 五、比较风险表达并作出决定

概率只属于明确的条件、目标事件、周期、horizon 和判断时点。规则匹配与替代见[条件规则台账](conditional_rules_registry.md)。理由数量不生成概率；结构生命周期概率、市场目标概率和账户盈利概率不是同一对象。

系统先独立评价双向 Market Paths，再按照[交易决策与计划](decision_and_plan.md)为当前可交易路径构造：

```text
Market Path
+ Entry
+ Invalidation / Planned Stop
+ Target / Outcome Criterion
+ Cost / Time
+ Position Size / Management
+ Execution Reliability
= 当前风险交换
```

选择的不是理由最多、裸概率最高或最熟悉的一侧。即使一侧市场目标更可能发生，当前 Entry 太差、Stop 太远、成本太高或剩余空间不足时仍可等待或不交易。

决策只有三种：

| 决定 | 含义 | 后续 |
| --- | --- | --- |
| 执行 | 当前 Trade Plan 完整且方程成立 | 保留原始计划并提交计划规定的订单意图 |
| 等待 | 路径仍现实，但缺少已声明的必要事实或完整计划 | 保存等待项和过期条件；下一相关事件重新评价 |
| 不交易 | 已知条件使当前交换不值得承担 | 关闭本次评价；新结构、新 Entry 或新时点建立新判断 |

等待不保留隐藏的可执行计划。未来 Trigger、Follow-through 或更好价格出现时，使用当时事实重新构造；预先提交并等待触发的 Stop / Limit order 已属于执行状态。

## 六、按 Execution State 分派动作

执行生命周期由[执行、持仓与复盘](execution_management_and_review.md)负责。订单、敞口和保护是三个可以并存变化的状态面：

```text
Order State：Intent / Submitted Unknown / Working / Partial / Filled
             / Cancel Pending / Canceled / Rejected / Expired
Exposure：Flat / Open(quantity) / Exiting(quantity)
Protection：Not Required / Pending / Adequate / Deficient
```

共同顺序为：

```text
提交订单
→ 确认订单状态
→ 确认实际成交与数量
→ 确认 Active Protective Stop 覆盖实际仓位
→ 持仓中继续更新所选路径、对手路径与 Pending Outcome
→ 目标、Invalidation、Stop、时间或账户条件结束风险
→ 确认仓位归零和剩余订单清理完毕
```

撤单请求、退出请求或 Stop 触发都不等于风险已经结束。部分成交可以同时存在实际持仓、剩余工作订单和待确认保护；确认最终账户事实前按可能发生的最坏暴露管理。

持仓中的每个相关事件先更新认知，再按原计划与当前账户状态映射动作：

| 路径变化 | 动作边界 |
| --- | --- |
| 增强或保持 | 按计划持有；不自动增加风险 |
| 削弱但未失效 | 停止新增风险；按预写分支保持、减仓或收缩管理目标 |
| 对手获得接受或所选路径失效 | 取消剩余新增风险并主动退出；归零前保护继续有效 |
| 目标、Stop 或时间条件发生 | 按 Outcome Criterion 处理并核对实际剩余仓位 |

退出原方向不自动许可反向交易。反方向必须以当前事实重新经过目标、概率、Entry、Stop、仓位和方程检查。

计划内 Scale-in 可以来自预写的更好价格，或成交后出现的新确认；前者改善价格但不提高路径概率，后者提供新证据但仍增加账户暴露。所有层必须在第一笔新增风险前进入最坏总风险，执行时仍要求原路径有效、保护正常且总风险合规。计划外新增风险必须建立新计划。

## 七、记录与闭环

普通 Observation Event 只保存相对上次判断的事实与路径变化。以下重要决策时点形成 Decision Record：

- 首次作出执行、等待或不交易，或其依据实质改变；
- 提交、修改或取消订单；
- 加仓、减仓、移动保护或退出；
- Primary Test、Selected Path 或 Trade Plan 的关键输入改变；
- 路径目标发生、失效、过期、替代或顺序不明。

每份记录至少能回答：发生了什么、当时的 Market Model 和适用规则是什么、哪些路径改变、采取或拒绝什么动作，以及下一项预期、失效或过期条件。等待与不交易也要进入连续样本，不能只留下实际成交。

结果分别闭环：

- `Market result`：目标路径实际达成、失效、过期、替代或顺序不明；
- `Trade outcome`：实际 Entry 后各计划结果发生的顺序；
- `Account result`：实际成交、数量、费用、滑点、退出和 P&L；
- `Process result`：正常不确定结果，或违反系统契约。

没有实际成交的机会不能记为交易成功或失败，但其 Market Path 仍须在 horizon 结束时闭环。持仓归零后还要确认剩余订单已清理、保护已撤换，单次交易才真正结束。

规则校准是独立的离线闭环：使用条件、目标、周期、horizon 和判断时点一致的连续样本，区分市场、交易、账户和流程结果，再登记规则修订的生效时间与替代关系。单笔赢家、输家或错过不能直接修改概率，后来的规则不能回写历史判断。

## 八、最小运行输出

人工看盘或机器处理一次相关事件，至少回答：

```text
Safety：订单、敞口、保护和数据是否正常？
Delta：相对上次判断，什么事实发生了变化？
Frame：当前 Primary Test 是什么？Context / Competing Tests 怎样约束它？
Paths：向上、向下与 Pending 分别期待什么结果？
Opposition：当前最强反路径及其获得接受的条件是什么？
Expression：Selected Path 的 Entry、Stop、Target、成本和总风险是否成立？
Action：执行、等待、不交易、持有、加仓、减仓、撤单还是退出？
Next：下一预期、失效、到期或强制检查条件是什么？
```

完整知识用于生成这些答案，不要求人工在每个普通事件重填全部对象；没有变化的事实沿用上一次判断，发生变化的事实必须可追溯。

## 九、系统不变量

- 所有方向使用同一套 Market Context、Location、Current Test 和证据更新；系统不按 Pattern 或 Setup 切换流程。
- 每个现实 Primary Test 都考虑向上、向下和 Pending 结果；双向考虑不要求双向同时交易。
- 没有明确市场目标事件，不匹配 Market Path 概率，也不建立 Trade Plan。
- 一个概率必须绑定条件、目标、周期、horizon 和判断时点；同源名称不重复计数。
- 一个 Trade Plan 只表达一个 Primary Test、一条 Market Path 和一个判断时点。
- 市场路径失效、交易计划失效和执行异常分别记录，并产生各自的动作。
- 每个相关事件可以改变认知而不改变动作；普通波动不自动触发加仓、减仓或退出。
- 没有实际成交就没有持仓，没有可确认的保护就不能假定风险受控。
- 实时候选、原始判断和后续更新分别保存，最终结果不能回填当时理由。
- 等待、不交易、未成交路径、实际交易和规则样本都有各自的闭环。
