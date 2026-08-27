# 价格行为交易系统总流程

> **状态：Trading System / Runtime Contract**

本页是唯一运行入口。它规定交易者现在观察什么、本步形成什么输出、何时进入下一步，以及何时等待、不交易或转入账户异常处理。检查可以是观察、心中确认或快速勾选；只有计划、风险、执行或复盘边界发生变化时才记录。

```text
Safety Guard ──异常──→ Safety Exception

市场—决策运行图：
Frame
→ Price Map
→ Current Move
→ Active Test
→ Context Update
→ Long / Short Opportunity Scan
├─ 至少一侧 OPPORTUNITY → Context Permission + Trade Construction
│  ├─ Candidate 完整 → Decision
│  ├─ 仍需明确下一事件 → Decision
│  └─ 无现实表达或事件 → Decision
├─ 只有 WATCH → Next Event → Decision
└─ 两侧 EXCLUDED 且无事件 → Decision

Decision
├─ EXECUTE → Ready → Order / Position / Protection → Exit / Review
├─ WAIT → Flat / Observing；事件发生或到期后从最早变化步骤重开
└─ NO_TRADE → Flat / Observing；新事件、问题或 Reframe 后重开

Frame 是运行前提；Frame 完成后的停止点统一进入 Decision：
存在明确下一事件与有效边界 → WAIT
没有完整 Candidate，也没有值得等待的事件 → NO_TRADE
```

## 一、选择运行模式

| 当前情形 | 运行方式 | 结束条件 |
| --- | --- | --- |
| 首次看图、交易周期或主导组织改变、原 Context 不再可用 | 先过 Safety Guard，再从 Frame 运行[完整 Checklist](#三完整-checklist) | 得到 Execute / Wait / No Trade，或进入账户异常处理 |
| 普通新 K 线、价格事件、时间边界或计划条件发生 | 运行[增量更新](#四增量更新只沿变化传播)，从最早改变的步骤向后传播 | 下游结论不再改变即停止 |
| 准备提交、存在工作订单或仓位、交易结束或账户异常 | 按[账户状态分派](#五账户状态分派)运行所有适用入口 | 真实账户状态、保护和当前动作得到确认 |

完整 Checklist 是防遗漏的观察顺序，不是每根 K 线都要填写的表。普通新 K 线若没有改变 Frame、市场读取、双向机会、计划、风险或动作，数秒内结束且不记录。

### 盘中一屏卡

```text
SAFE？          全局 Guard：仓位/订单一致性、总 Stop 风险、实际保护、数据与连接
判断边界？      交易周期、Session、剩余时间、事件/流动性约束、外层参照
价格在哪里？    Active Area、最近上方/下方区域、两侧空间
怎样来到这里？  当前段/角色、连续性、gap/overlap、回调、反方反应、双方 Pressure
正在测试什么？  Object / Objective、当前反应、接受/失败、下一观察、有效边界
Context？       Operating State、Direction、Conditions；沿用还是 Reframe
Long / Short？  各自 Opportunity / Watch / Excluded；目标、缺什么、怎样失效
怎样承担风险？  Trigger、Stop/Limit/Market、Planned Stop、Targets、Size、方程
当前决定？      Execute / Wait / No Trade
```

## 二、Checklist 的用法与职责

Checklist 负责防遗漏和路由，不要求盘中填写完整对象。每一步必须检查所有会改变事实、路径、概率、计划、风险或动作的条件，并形成结构化的本步判断；字段定义、边界条件和复杂计划在权威文档中展开。判断必须完整，只有书面记录遵循最小充分原则。

| 层次 | 盘中用途 | 权威文档 |
| --- | --- | --- |
| Frame | 固定周期、时间与外层约束 | 本页 |
| Market Read | 回答价格在哪里、怎样来到这里、正在测试什么及 Context 是否重构 | [Market Read 与 Opportunity](market_read_and_opportunities.md) |
| Opportunity Scan | 分别回答 Long / Short 当前有路径、需等待还是应排除 | [Market Read 与 Opportunity](market_read_and_opportunities.md#十从-market-read-到-opportunity-set) |
| Trade Construction | 把一条可表达路径变成 Entry、Stop、Target、Size 与管理 | [交易决策与计划](decision_and_plan.md) |
| Decision | 根据 Candidate 或下一事件输出 Execute / Wait / No Trade | [交易决策与计划](decision_and_plan.md#十四decision-与唯一决定) |
| Execution | 按真实订单、敞口、保护和风险采取动作 | [执行、持仓与复盘](execution_management_and_review.md) |

`UNRESOLVED` 表示当前事实不足；`PENDING` 表示问题已定义但结果未发生；`WATCH` 是某一方向等待下一事实；`WAIT` 是整体不执行并等待一个明确事件；`NO_TRADE` 结束当前交易表达。Checklist 统一显示 `Valid Until`；内部模型按对象分别保存 Test、Watch、Opportunity、Entry 或 Decision 的有效边界。

运行图只画会改变下一步的判断，不把所有观察问题变成分支：事实问题留在当前节点，状态归纳成为本步判断，决策门形成分支，动作形成下一跳。每个分支必须进入另一个节点、明确的终点或 Safety Exception；Wait 必须有 Next Event 与有效边界，订单终态必须按真实账户状态重新分派。市场—决策图由本页维护；并行账户入口和完整订单转换只由[执行、持仓与复盘](execution_management_and_review.md)维护。

## 三、完整 Checklist

完整 Checklist 只在首次看图、周期改变或 Reframe 时逐步运行。每一步采用同一结构：先完成全部必看条件，形成能够支持后续步骤的本步判断，再按路由继续。

### Safety Guard｜现在可以继续正常运行并新增风险吗？

**必看**

- 仓位、工作订单与回执是否一致？
- 所有仍可能形成的 Stop 风险是否在上限内？
- 实际保护是否可确认并覆盖真实数量？
- 数据、账户和连接是否可靠？

**本步判断与路由**

- 全部确认：`SAFE → Frame`；
- 任一不一致、超限、保护不足或无法确认：`SAFETY_EXCEPTION`，停止新增风险。

### 1. Frame｜本轮判断的边界是什么？

**必看**

- 用哪个 Trading Timeframe 判断结构和正常波动？
- Session、剩余时间、事件、波动或流动性是否限制目标、Entry、Size 或新增风险？
- 哪个外层区域或结构真正改变本周期目标、正常回调、Stop 或管理？
- 上一次 Context 是否仍可作为比较基线？

**本步判断**

```text
Trading Timeframe + Session / Remaining Time
Trading Constraint + Relevant Outer Constraint
Context Baseline：继承 / 首次读取 / Unresolved
```

Scalp / Swing 属于 Opportunity 的 Outcome Horizon，不在 Frame 预先决定。

**路由**

- 必要边界未定义：先补齐 Frame，不承担新风险；
- `NO_NEW_RISK`：继续读取市场，只管理已有订单和仓位；
- 边界明确：进入 Price Map。

### 2. Price Map｜价格在哪里，前方有什么？

**必看**

- 当前正在互动哪个区域，还是处于两个区域之间？
- 新 swing high / low、突破点、运动起点、固定 MM 或保护锚点是否刚获得运行职责？
- 上方和下方最近哪个区域会改变目标、障碍、失效、Stop 或动作？
- 到两侧第一现实区域还有多少可用空间？同一价格带是否被多个名称重复登记？

**本步判断**

```text
Current Area + 所有当前相关 Areas Above / Below
到两侧第一现实障碍的 Space Up / Down
```

已检查且没有现实障碍为 `OPEN_SPACE`；尚未识别为 `UNRESOLVED`。

**路由**

- 地图足以支持当前判断：进入 Current Move；
- 某侧位置或空间仍未解决：可以继续读取，但该侧不能形成完整 Opportunity。

### 3. Current Move｜价格怎样来到这里？

**必看**

- 价格从哪里出发；现在是上涨段、下跌段、暂停还是局部平衡？
- 当前段是 continuation、pullback、range leg 还是 reversal attempt？
- K 线实体、收盘、影线、连续性和 follow-through 怎样？
- separation / gap 在扩大、保持、缩小还是关闭；overlap 与回调深度、持续时间怎样？
- 反方只有单根反应，还是已经建立自己的强 K、连续性、分离或恢复？

**本步判断**

```text
From + Now + Role
一条去重的 Bars / Continuity / Separation / Pullback / Opponent 事实链
Bull Pressure：增强 / 保持 / 减弱 / 未建立
Bear Pressure：增强 / 保持 / 减弱 / 未建立
Control：Bull / Bear / Balanced / Unclear
```

一侧减弱不等于另一侧建立；同一突破产生的大实体、gap、Pressure、Control 和接受仍属于同一事实链。

**路由**

- 能说明当前运动与双方压力：进入 Active Test；
- 暂时无法分类但下一事实明确：把该事实作为 Decision 的 Next Event；
- 无法形成当前问题且没有现实下一事件：进入 No Trade 判断。

### 4. Active Test｜市场正在解决什么问题？

**必看**

- 正在测试哪个区域、边界或旧 Control；哪一方试图完成什么？
- 当前是接近、触及、反应、突破尝试还是跟随阶段？
- 这是同一问题的第几次尝试；本次延伸和反应相对上一次怎样？
- 怎样算 Tested Objective 获得接受；怎样算失败或旧区域重新获得接受？
- 下一项真正会改变判断的事实是什么；当前问题最迟何时仍有效？

**本步判断**

```text
价格正在测试 [Object]，试图 [Objective]；
当前 [Phase / Resolution / Attempt / Response]；接受需要 [A]，失败需要 [B]；
下一观察 [Next Observation]，有效至 [Valid Until]。
```

H2、Double Bottom、Wedge、Triangle、ii / ioi 或 MTR 只帮助说明次序、几何和过程作用；signal bar 与实际入场边界属于后续 Candidate。

**路由**

- 问题仍 Pending 或刚被接受 / 失败：进入 Context Update；
- 问题到期或被替代：终止旧 Test；有新问题就从最早变化步骤重建，没有新问题则进入 Wait / No Trade；
- Object、结果条件和下一事实都无法表达：进入 No Trade 判断。

### 5. Context Update｜外层价格组织是否仍可沿用？

**必看**

- 新事实仍属于原 Context 的正常回调、目标和双边获利能力吗？
- 原方向只是减弱，还是反方已经建立持续 Pressure 与接受？
- 正常回调、目标、Control 或管理边界是否已经跨过原分类？
- Breakout Mode、Climax 或 Transition 等条件是否新增、解除或改变 Permission？

**本步判断**

```text
Current Context：Operating State + Direction + Conditions
Range Condition：Width + Maturity（仅 Trading Range）
Reframe：NO / YES
```

内部模型可以保存完整 Context delta；盘中只需明确当前 Context 和是否 Reframe。`Current Move.Control` 是当前窗口结论，`Context.Direction` 是交易周期持续组织。

**路由**

- Context 沿用或条件更新：进入 Opportunity Scan；
- Reframe 同时替代 Price Map 或 Active Test：从最早变化步骤重开；
- 分类不清：保留 `UNCLEAR` 并应用保守 Context Permission。

### 6. Opportunity Scan｜Long 与 Short 分别准备完成什么？

对 Long、Short 各运行一次同样的检查。

**每侧必看**

- 当前是否存在现实 Objective、Outcome Horizon 和第一目标？
- 已发生事实怎样支持该路径；还缺什么 Activation？
- 哪个区域与什么价格事件使路径失效？
- 目标前是否有足够空间和时间；适用概率是否与目标、周期和时点一致？
- 对手是否已有完整 Opportunity；除此之外还有什么最强 Counterevidence？

**每侧判断必须覆盖**

```text
Path：Role + Outcome Horizon；Objective + Target
Evidence：Support / Already；Activation + Status
Opposition：竞争 Opportunity；其余最强 Counterevidence
Boundary：Invalidation + Valid Until
Probability：Market Probability + Rule Match
```

完成判断后，本侧只进入一种运行状态：

| 状态 | 继续运行所需信息 |
| --- | --- |
| `OPPORTUNITY` | 上述五组判断 |
| `WATCH` | 下一可观察事实 + Valid Until |
| `EXCLUDED` | 一句排除原因 |

同方向不同 Objective 或 Outcome Horizon 分开表达；只有会改变当前选择或管理时才保存 `Likely Sequence`。

**路由**

- 至少一侧为 `OPPORTUNITY`：无论 Activation 当前是 `MET` 还是 `PENDING`，都进入 Context Permission 与 Trade Construction；
- 没有 Opportunity、只有 `WATCH`：选最早会改变流程的 Next Event，进入 Wait 判断；
- 两侧都被排除且没有现实下一事件：进入 No Trade 判断。

### 7. Trade Construction｜现在怎样承担风险？

**必看**

- 当前 Context Permission 是否允许该 Role、方向和 Early / Confirmed 风险承担时点？
- 承担风险前必须完成的 Activation 是否已经发生；订单 Trigger 能否完整表达尚缺条件？
- 应使用 Stop、Limit 还是 Market / close；Entry 规则与有效期是什么？
- Planned Stop 是否引用有效结构并容纳管理周期正常波动？
- First / Main Target 是否来自已登记区域；扣除近端障碍后空间是否足够？
- Size 是否由 Entry 到 Stop 的风险反推；成本、时间和管理是否仍形成正方程？
- 成交后必须看到什么、允许多久；怎样区分普通失望与计划失败？

**本步判断**

```text
Selected Opportunity + Risk Timing / Activation Status
Trigger / Entry Method / Entry Rule
Planned Stop + First / Main Target + Size / Risk
Entry Validity + Management / Time Exit
Candidate Outcome Probability / Range + Net Reward:Risk / Trader's Equation
```

Stop 用确认换价格，Limit 用较少确认换价格改善，Market / close 只在前置条件完成后使用。完整 Candidate 字段见[交易决策与计划](decision_and_plan.md)。

**路由**

- Candidate 完整且方程成立：提交 Decision；
- 只缺一个明确、现实的新 Candidate 事件：提交该 Next Event 与 Valid Until；
- 没有现实表达或下一事件：进入 No Trade 判断。

### 8. Decision｜当前是否建立新的交易表达？

**检查与唯一输出**

| 当前事实 | Decision | 动作 |
| --- | --- | --- |
| 有完整 Candidate，双向扫描、Permission、风险与方程均成立 | `EXECUTE` | 冻结一份 Trade Plan，进入 Ready to Submit |
| 没有 Candidate，但有明确且未过期的 Next Event | `WAIT` | 不保留隐藏 Candidate；事件发生或到期后重算 |
| 既无 Candidate，也无值得等待的事件 | `NO_TRADE` | 结束当前交易表达；新的相关市场事件、问题或 Reframe 后再评 |

Decision 一次只建立一份单侧交易表达。双向 Breakout Mode 等待实际突破、失败或其他预先声明的事件，再以新的判断时点重读双向机会并构造 Candidate。已经提交的 Stop / Limit 属于 Working Order，不是 Wait。

## 四、增量更新｜只沿变化传播

普通新 K 线、价格事件、Session / 时间边界或计划条件发生时只问：

```text
1. Safety 或 Frame 边界改变了吗？
2. 新 Region 是否形成或获得职责；Price Map / Current Move / Active Test 改变了吗？
3. Context、Long / Short Opportunity 或 Likely Sequence 改变了吗？
4. Candidate、Trade Plan、风险、保护或动作改变了吗？
```

全为“否”：`NO_CHANGE`，继续观察、继续工作原订单或按计划持仓，不记录。

任一项为“是”：从最早改变的步骤重开，沿因果链向后传播；下游输出未变即停止。价格事件用[市场决策事件导航](market_decision_events.md)定位起点；Frame / Session 事件从 Frame 开始；订单、仓位、保护或风险变化直接进入账户状态分派。

只有 Trading Timeframe、主导 Context、当前价格问题或 Opportunity Set 被替代时，才重做完整 Market Read。EMA 首次测试、surprise、breakout pullback、第二/第三次测试、三推、ii/ioi、MTR 和目标到达只是通用路由快捷卡，不建立新状态。

## 五、账户状态分派

Safety Guard 优先抢占；安全确认后，以下条件独立判断，所有成立的入口并行运行：

```text
账户、连接、回执或保护不可靠
→ Safety Exception

安全确认后：
├─ 存在实际 Exposure → Open Position
├─ 存在未提交且仍有效的 Entry / Add 执行意图 → Ready to Submit
├─ 存在 Working / Cancel Pending 订单 → Working Order
├─ 存在待执行的 Reduce / Exit 动作或相关订单，且仍有 Exposure → Exiting
├─ 交易或路径刚结束，盘中终结确认 / Review 交接尚未完成 → Closed / Review
└─ 以上全部不成立，且没有待完成的盘中关闭动作 → Flat / Observing
```

以下入口只规定盘中必须检查什么和下一步去哪里；Order Purpose、Order State、Exposure、Protection 及其完整转换由[执行、持仓与复盘](execution_management_and_review.md)唯一规定。

### Flat / Observing

- 当前 Market Read 是否仍有效；若失效，从 Frame 重开；
- Long / Short 各自的 Side Scan Result 和下一事实是什么；
- 没有 Candidate 就继续观察；只有 Decision 输出 `EXECUTE` 才进入 Ready。

### Ready to Submit

```text
Intent Purpose：ENTRY / ADD
Plan Validity：VALID / CHANGED / EXPIRED / ABANDONED
Account / Risk：CONFIRMED / NOT_ALLOWED / UNKNOWN
Order Parameters：CONFIRMED / CHANGED
Cumulative Fills → Remaining Intended Quantity：CONFIRMED / ZERO / INCONSISTENT
Protection on Fill：READY / UNRESOLVED
```

Remaining Intended Quantity 由原计划数量和平台累计成交直接计算，只需核对，不新增人工记录对象。

- 全部有效且确认、剩余计划数量大于零：只提交扣除本执行意图累计成交后的剩余数量，立即进入订单生命周期；已有 Exposure 时继续并行运行 Open Position；
- 剩余计划数量为零：关闭当前执行意图并按真实状态重新分派；数量不一致：不提交，先按原计划数量、累计成交、当前 Exposure 与风险修正；
- Entry 意图的 Market Read、Opportunity、Candidate 或订单参数改变：从最早变化步骤重开，经 Trade Construction 与 Decision 形成新计划；
- Add 意图的原 Opportunity、Add 条件、风险或订单参数改变：关闭旧意图并返回 Open Position / Add Gate；只有计划外的新 Opportunity 才重新经过 Candidate 与 Decision；
- 到期或主动放弃且未提交：关闭当前执行意图，再按真实 Exposure、订单和其他有效意图重新分派，不固定返回 Flat；
- 提交状态不明：进入 `Submitted Unknown`，核对账户且不重复提交。

### Working Order

```text
订单用途、经纪商状态、实际成交量和剩余数量是什么？
实际 Exposure 与 Active Protective Stop 是否一致？
若是 Entry / Add：Opportunity、Entry Validity 和原方程是否仍成立？
若是 Reduce / Exit：退出动作是否仍有效，剩余 Exposure 是否仍需处理？
现在应保持、撤单、补足保护，还是按成交后的真实状态重新分派？
```

- 回执不明或 Cancel Pending：核对账户，不重复提交，按订单仍可能成交计算暴露；
- Entry / Add 的 Opportunity 不再 `ACTIVE`、Entry Validity 结束或方程失效：撤单并等待确认；
- Entry / Add 被拒、取消或到期：关闭该订单；执行意图仍有效则重新进入 Ready，否则按真实状态重新分派；
- Reduce / Exit 被拒、取消或到期且仍有 Exposure：维持实际保护并进入 Exiting；退出动作仍有效则修复或重新提交，无法可靠执行或保护不足则进入 Safety Exception；
- 发生 Partial / Filled：按订单用途和剩余 Exposure 进入 Open Position、继续 Working / Exiting，或在仓位归零并确认残留状态后进入 Closed / Review；具体转换只引用[订单生命周期](execution_management_and_review.md#二订单生命周期)。

### Open Position

每个相关事件依次回答：

```text
1. 实际数量、工作订单与 Active Protective Stop 一致吗？
2. Price Map / Current Move / Active Test 出现什么新事实？
3. Selected Lifecycle：ACTIVE / ACHIEVED / INVALIDATED / EXPIRED /
                       SUPERSEDED / SEQUENCE_UNKNOWN
   Active Update（仅 ACTIVE）：STRENGTHENED / UNCHANGED / WEAKENED
4. Competing Opportunity：NONE / PRESENT
   Competing Acceptance：NOT_ESTABLISHED / PENDING / ACCEPTED
5. Target、Stop、时间或原计划条件发生了吗？
6. 是否形成能容纳正常波动并降低风险的新保护锚点？
7. Action：HOLD / STOP_ADDING / REDUCE / TRAIL / EXIT
```

| 所选与竞争路径 | 允许动作 |
| --- | --- |
| 所选增强或不变；竞争仍弱或仅出现 | 按计划持有；计划内 Add 运行 Add Gate |
| 所选削弱但未失效；竞争增强但未接受 | Hold、Stop Adding，或执行预写 Reduce / 目标收缩 |
| Structural Invalidation 或强反向动量否定所选路径 | 取消新增风险并主动退出；归零前维持保护 |
| 竞争 Opportunity 获得接受并否定所选路径 | 先处理原仓位；反向交易重新构造 Candidate |
| `SUPERSEDED` | 停止新增风险并退出；新路径只在归零后重新构造交易表达 |
| `ACHIEVED / EXPIRED / SEQUENCE_UNKNOWN`，或 Target、Active Stop、时间或账户条件发生 | 按 Outcome Criterion 处理并核对剩余仓位；顺序未知时不选择有利解释 |

Trailing / Breakeven 只使用已经形成、与管理周期一致、能容纳正常波动并降低开放风险的新保护锚点。Stop amend / replace 以确认后的新价格和数量为准；确认后原保护由修改后的 Stop 直接取代。

### Exiting｜减仓或退出是否真正完成？

```text
剩余 Exposure、退出订单状态和成交数量是什么？
Active Protective Stop 是否覆盖尚未退出的真实数量？
是否还有可能成交的订单或残留保护？
```

Reduce / Exit 请求不等于仓位已经减少。仍有 Exposure 时继续运行 Open Position，并按实际退出订单状态同时运行 Working Order；仓位归零后确认残留订单与保护的最终状态，才进入 Closed / Review。部分成交、回执不明和退出竞态的完整转换只引用[主动退出与退出订单](execution_management_and_review.md#主动退出与退出订单)。

退出订单被拒、取消或到期但仍有 Exposure 时，先保持实际保护：退出动作仍有效就修复参数或重新提交；新事实使退出动作不再有效就返回 Open Position 重新判断；无法确认仓位、保护或可靠退出时进入 Safety Exception。

### Add Gate｜是否使用计划内剩余风险？

```text
原 Opportunity 仍有效，竞争路径尚未获得接受？
→ Add 条件已发生，Cancel Add 未发生？
→ 当前 Entry Method、共同/独立 Stop、Targets、时间与管理仍形成正方程？
→ Risk Available 足以容纳按实际价格计算的新数量？
→ ADD_TO_READY / HOLD_RESERVE / CANCEL_ADD
```

`ADD_TO_READY` 只冻结本层 Entry、数量、Stop、触发依据和加仓后风险，再进入 Ready to Submit。剩余额度或 Trail 后释放的数值容量不构成加仓理由；计划外新增风险必须建立新 Candidate。

### Safety Exception

- 核对真实净仓位、所有可能成交订单、保护、最坏暴露和连接状态；
- 只允许恢复保护、撤单、减仓或退出，不新增风险；
- 异常解除后重新应用并行状态分派；原 Entry / Add 意图必须重新通过 Ready 检查，不能因异常前有效而自动提交；
- 若 Market Read 已经过期，再从 Frame 重开。

### Closed / Review

- 先确认仓位归零，剩余工作订单和保护订单最终状态明确；
- 分开 Market Result、Trade Outcome 与 Account Result；
- 判断按计划、正常不确定结果或系统违规；
- 只保存会改变后续计划、风险或规则样本的一两项关键差异。

Closed / Review 可以在仓位已归零但残留订单仍待确认时与 Working Order 并行。盘中只需完成终结确认、保存必要终结事实，并把需要深入分析的问题交给盘后 Review；该交接完成后即可返回 Flat / Observing，盘后详细复盘不阻止继续观察或下一笔交易。关联 Opportunity 独立更新为 `ACTIVE / ACHIEVED / INVALIDATED / EXPIRED / SUPERSEDED / SEQUENCE_UNKNOWN`；若仍 Active 就继续当前 Market Read，否则等待新问题或在 Context 过期时从 Frame 重开。

## 六、必要记录

系统按事件保存最小增量：

| 事件 | 保存内容 |
| --- | --- |
| 普通观察，机会、风险和动作未变 | 无 |
| 新市场问题或 Side Scan 实质改变下一观察 | 更新所引用的 Next Event / 对应 Expiry；需要跨事件保留时合入 Decision Record |
| 需要跨事件跟踪的 Wait | 最小 Decision Record |
| Execute / 选中 Candidate | 冻结 Trade Plan |
| 普通 No Trade | 无；只有改变观察计划、风险或规则样本时记原因 |
| 实质修改计划、仓位、保护或风险 | 在原 Trade Plan 追加 Delta |
| 成交、拒单、部分成交、撤单确认、异常、减仓或退出 | 平台原始事实 + 必要差异 |
| Opportunity 或交易结束 | 终结事实；盘后复盘 |

```text
Decision Record
- 时点 + 品种 / Trading Timeframe
- Long / Short 结论（一短句）
- WAIT 的 Next Event + Valid Until
- 重要 NO_TRADE 的排除原因（普通扫描不记录）

Trade Plan
- 时点 + 所选路径及最强反方（一短句）
- Entry Method / Price + Entry Validity
- Planned Stop + Target + Size / Risk
- Invalidation / Cancel Condition
- 多层计划另加 Risk Limit / Initial Limit / Add / Cancel Add / Stop Rule
```

概率或 Rule Match 只有在它们实质决定当前方程或用于样本校准时保存。平台已可靠保存的订单、成交和费用不人工重抄；完整字段只在多层、多目标、跨 Session、自动化或异常计划中按需展开。

## 七、运行不变量

- Context 先继承，后由 Price Map、Current Move 与 Active Test 确认或重构；首次读取直接初始化。
- Market Read 先固定位置与连续价格事实，再分别扫描 Long / Short；双向完成后才构造 Candidate。
- Price Map 唯一登记 Region；Opportunity 和 Candidate 通过引用为它分配角色，不维护平行位置清单。
- Pattern 名称只解释 Price Process；新位置、新测试、新反应和 follow-through 才提供事实增量。
- Correction、reversal、continuation 与 range return 按 objective 和 Outcome Horizon 分开，并可按 Likely Sequence 先后发生。
- Opportunity 描述市场路径；Candidate 描述当前风险表达；Decision 描述动作；Execution 只接受真实账户事实。
- WAIT 必须有 Next Event + Valid Until（内部对应 Decision Expiry），不保存隐藏 Candidate；Working Order 不是 Wait。
- Ready、Working、Open 与 Exiting 按事实并行适用；任何订单终态先关闭该订单事实，再按剩余 Exposure、其他订单和有效执行意图重新分派。
- 持仓退出不提供反向许可；反向风险始终重新经过 Opportunity、Candidate 和 Decision。
