# 价格行为交易系统总流程

> **状态：Trading System / Runtime Contract**

本页是唯一运行入口。它规定交易者现在运行哪一套检查、每一步必须得到什么输出、什么时候进入下一步，以及何时停止、等待或转入异常处理。检查可以是观察、心中确认或快速勾选；只有跨过计划、风险、执行或复盘边界的变化才记录。

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

## 一、选择运行模式

| 当前情形 | 运行方式 | 结束条件 |
| --- | --- | --- |
| 首次看图、交易周期或主导组织改变、原 Context 不再可用 | 从 Safety 开始运行[完整 Checklist](#三完整-checklist) | 得到 Execute / Wait / No Trade，或在某一步明确停止 |
| 普通新 K 线、价格事件、时间边界或计划条件发生 | 运行[增量更新](#四增量更新只沿变化传播)，从最早改变的步骤向后传播 | 下游结论不再改变即停止 |
| 准备提交、订单工作中、持仓中、交易结束或账户异常 | 运行对应[账户状态路由](#五账户状态路由) | 状态得到确认，并完成当前允许动作或复盘 |

完整 Checklist 是防遗漏的观察顺序，不是每根 K 线都要填写的表。普通新 K 线若没有改变 Frame、市场读取、双向机会、计划、风险或动作，数秒内结束且不记录。

### 盘中一屏卡

```text
SAFE？          仓位、订单、总 Stop 风险、实际保护、数据与连接
判断边界？      交易周期、horizon、Session、剩余时间、外层约束
价格在哪里？    Active Area、上方/下方最近相关区域、两侧空间
怎样来到这里？  当前腿、K 线质量、连续性、gap/overlap、回调、反方反应
正在测试什么？  Object、Stage、Response、Attempt、双向接受/失败条件、Next、Expiry
Context？       Keep / Transition / Reframe / Unclear
Long / Short？  各自 Objective、Targets、Already → Next、Invalidation、Against
怎样承担风险？  Trigger、Stop / Limit / Market、Planned Stop、Targets、Size
当前决定？      Execute / Wait / No Trade
```

## 二、运行对象与职责

| 对象或门 | 唯一职责 | 权威文档 |
| --- | --- | --- |
| Market Read | 继承 Context，更新 Price Map、Current Move 与 Active Test，再确认或重构 Context；不选择交易方向 | [Market Read 与 Opportunity](market_read_and_opportunities.md) |
| Opportunity Set | 分别表达现实 Long / Short 的 objective、目标、Already → Next、Activation、Invalidation、Against、horizon 与可能顺序 | [Market Read 与 Opportunity](market_read_and_opportunities.md#十从-market-read-到-opportunity-set) |
| Trade Candidate / Plan | 为当前允许且可表达的 Opportunity 构造 Trigger、Entry、Planned Protective Stop、Targets、Size、结果概率与管理；选中后冻结 Trade Plan | [交易决策与计划](decision_and_plan.md) |
| Execution State | 保存实际订单、成交、敞口、风险容量与 Active Protective Stop | [执行、持仓与复盘](execution_management_and_review.md) |

Frame、Safety、Decision 和 Review 是运行门，不另建复杂对象。Pattern 只压缩结构、次序或外层作用；H2、Double Bottom、Wedge、Flag、MTR、ii / ioi 等名称只有在改变现有运行对象时才有作用，不产生 Setup 路由或额外证据票数。

## 三、完整 Checklist

### 0. Safety｜现在可以继续正常运行并新增风险吗？

**检查**

- 实际净仓位、全部工作订单与回执是否一致？
- 现有仓位与所有仍可能增加暴露的订单到各自 Stop 的总风险是否在上限内？
- Active Protective Stop 是否状态可确认并覆盖实际数量？
- 行情、账户、连接和已知事件风险是否可靠？

**输出与门**

- `SAFE`：进入 Frame；
- `SAFETY_EXCEPTION`：停止新增风险，只允许核对、恢复保护、撤单、减仓或退出。

### 1. Frame｜本轮判断的边界是什么？

**检查**

- Trading Timeframe 与实际管理周期是什么？
- 当前路径是 scalp、swing，还是只观察一个尚未解决的测试？
- 当前 Session、剩余时间、波动、流动性和已知事件窗口是否影响目标可达性或执行？
- 哪个外层约束会真正改变本周期的目标、正常回调、Stop 或管理？
- 上一次确认的 Context 是什么；首次看图时能否暂定，还是应标为 `UNCLEAR`？

**输出与门**

输出 `Trading Timeframe + Horizon + Session / Remaining Time + Relevant Outer Constraint + Inherited Context`。Inherited Context 只是本轮比较基线，须由当前价格过程确认；周期或目标时间范围说不清时，不进入概率和 Trade Construction。

### 2. Price Map｜价格在哪里，前方有什么？

**检查**

- 当前正在互动的 Current / Active Area 是什么？
- 上方和下方最近哪些区域会改变目标、障碍、Entry、Invalidation、Stop、空间或动作？
- 每个相关区域来自哪些相对独立的来源；哪些名称只是同一价格带？
- 当前价格到两侧第一现实区域分别还有多少可用空间？

区域来源可以包括旧高低、区间边界和中部、突破点与运动起点、gap、50%、EMA、趋势线 / 通道线、事前固定 MM 和 Session 水平。同一价格带只登记一次；其他历史高低保持休眠，获得运行职责时再激活。

**输出与门**

输出 `Active Area + Nearest Relevant Area Above / Below + Available Space Up / Down`。一侧经过检查、在当前 horizon 内确实没有相关障碍时标为 `OPEN_SPACE`；尚未识别或信息不足时标为 `UNRESOLVED`，两者不能互换。可以继续读取 Current Move，但当前区域或现实空间仍为 `UNRESOLVED` 时不进入 Candidate；不能用远端目标绕过近端障碍来修复 Reward / Risk。

Price Map 只拥有位置、来源、汇合、距离和空间。Support / Resistance、Potential Entry Area、Obstacle、Magnet、Target 与 Invalidation Reference 是后续 Opportunity 对同一区域分配的角色。

### 3. Current Move｜价格怎样来到这里？

在能回答当前过程的同一最小窗口中检查：当前腿、当前区域测试，或上次 Reframe 以来。

**检查**

- 价格从哪个区域、运动或反应开始；现在是 Up Leg、Down Leg、Pause 还是 Local Balance？
- 当前运动承担 Continuation、Pullback、Range Leg、Reversal Attempt 还是 Unresolved？
- K 线实体、收盘、影线与相对大小怎样；同向连续性和 follow-through 怎样？
- gap / breakout separation 是扩大、保持、缩小还是关闭；overlap 是否增加？
- 回调的深度、持续时间、gap 与原方向恢复速度怎样？
- 反方只有单根反应，还是已有自己的强 K、连续性、分离或失败后的恢复？

**输出与门**

输出一条连续价格事实链，并分别给出 `Bull Pressure` 与 `Bear Pressure` 的增强、保持、减弱或未建立，以及对 Control 的含义。一侧减弱不等于另一侧建立；大实体、强收盘、gap、Pressure、Control 和 Acceptance 若来自同一次运动，仍是一条来源链。

能够说明哪一方正在保持或失去分离、连续性和控制后，进入 Active Test；冲突时保留 `Mixed / Unclear`，不以 Pattern 名称补齐结论。

### 4. Active Test｜市场正在解决什么问题？

**检查**

- 当前运动正在测试 Price Map 中哪个区域、边界、突破点或旧 Control？
- 当前处于 Approach、Touch、Reaction、Breakout Attempt、Follow-through、Acceptance、Failure 还是 Pending？
- 价格目前怎样回应这个测试：分离、拒绝、突破、重叠，还是重新进入旧区域？
- 这是当前逻辑的第一次、第二次还是第三次尝试？
- 当前 horizon 的外层位置测试和局部触发测试分别是什么；额外尺度是否会改变目标、正常波动、失效或动作？
- 向上怎样才算获得接受；向下怎样才算获得接受或使原路径失败？
- 下一项可以解决当前测试的可观察事实是什么；什么时候该问题过期？

**输出与门**

压缩成一句过程问题：

```text
价格正在测试 X；当前处于 Y，Response 为 R；向上需要 A，向下需要 B；下一事实是 C，最迟到 D。
```

说不清 Object、双向结果条件、Next 或 Expiry 时，停在 Market Read / Wait，不构造交易路径。H2、Double Bottom、Wedge、Triangle、ii / ioi、MTR 等可以帮助说明 Attempt、Scale、几何或过程作用，但不能替代这个输出。

### 5. Context Update｜当前过程改变外层组织了吗？

**检查**

- 新事实仍属于原 Context 的正常回调、目标和双边获利能力吗？
- 原方向只是 Pressure 减弱，还是反方已经建立持续 Pressure 与接受？
- 正常回调、目标、Control、双边获利能力或管理边界是否跨过原分类？
- 当前结果应为 `KEEP / TRANSITION / REFRAME / UNCLEAR`？

**输出与门**

输出确认后的 Operating State、Direction / Control 和必要 Overlay，再应用对应 Context Permission。普通反色 K、一个形态名称或轻微边界越过不能单独确认控制转移；`UNCLEAR` 是合法输出，并使用保守 Permission。

只有确认后的 Context 进入 Opportunity。完整分类、状态转换和 fallback 由 [Market Read 与 Opportunity](market_read_and_opportunities.md#六context继承后由当前过程确认)拥有。

### 6. Opportunity Set｜多空分别准备完成什么？

每次决策事件分别扫描 Long 与 Short。每一侧使用同一组问题：

**检查**

- Direction、Role 与 Horizon 是什么；这是 continuation、correction、reversal、range return 还是 breakout？
- Objective 与可观察的 Market Outcome Criterion 是什么？
- 第一现实目标和主要 Market Targets 来自哪些已登记区域或事前固定投射？
- 去重后的价格事实链已经完成什么；下一项 Activation 是什么？
- 哪个区域和什么市场事件真正使该路径失效？
- 当前最强反方事实或竞争 Opportunity 是什么？
- 与当前目标、周期和 horizon 一致的 Market Probability / Rule Match 是什么；没有可运行规则时能否诚实表达不确定性？
- 空间、剩余时间和目标可达性是否现实；什么时候路径过期？

**每侧输出**

- `REAL OPPORTUNITY`：字段足以表达现实市场路径；
- `WAIT`：保留下一可观察事实与 Expiry；
- `EXCLUDED`：只说明没有现实 objective、空间、时间、有效 horizon，或当前事实已经否定该路径的原因，不制造伪 Opportunity。

随后检查两侧是竞争关系，还是可能按 `Likely Sequence` 先后发生。例如强空头背景可以先有 `Up / Correction` 到 EMA 或 50%，再有 `Down / Continuation` 测试旧低；短期修正目标不能借给长期反转。

**进入下一步条件**

双向扫描完成后按结果路由：至少一条 `REAL OPPORTUNITY` 才进入 Trade Construction；没有现实 Opportunity、但至少一侧存在可观察 Next 时输出 `WAIT + Next + Expiry`；两侧都被排除且没有现实下一事件时输出 `NO_TRADE`。Context Permission 不删除现实市场路径，只决定它能否在当前时点产生 Candidate。

### 7. Trade Construction｜现在怎样承担风险？

只对 Context Permission 允许且值得表达的 Opportunity 构造 Candidate。现实 Opportunity 尚未取得 Permission 时，若存在明确的控制转移、接受或其他许可条件，输出 `WAIT + Next + Expiry`；没有现实许可路径时，当前交易表达为 `NO_TRADE`，但市场 Opportunity 保持自身生命周期。

**检查**

- 当前承担 Early 还是 Confirmed 风险；判断时点已经具备哪些证据？
- Activation 已经完成，还是计划明确允许订单 Trigger 完整执行尚缺条件？若仍要求 bar close、follow-through、回踩守住或 acceptance，单纯越过价格是否不足？
- Trigger Boundary 来自哪个 Region、signal bar 或 Active Test 边界？
- 应使用 Stop、Limit 还是 Market / close Entry；价格规则、有效期和取消条件是什么？
- Opportunity 的 Structural Invalidation 是什么；Planned Protective Stop 应放在哪里才能容纳管理周期正常波动？
- First Target、Main Target 和 Outcome Criterion 来自哪个已有区域或投射；近端障碍后的净空间是否足够？
- 当前 Entry 到 Stop 的 Planned Risk 对应多大 Size；多层时 Risk Limit、Initial Limit、Add 与 Cancel Add 是否完整？
- Candidate Outcome Probability、Reward、Risk、实质相关成本、剩余时间和管理是否描述同一计划？
- 成交后必须看到什么，允许多久；普通 disappointment 与计划失败怎样区分？

**输出与门**

输出完整 Trade Candidate；当前仍有明确的更好 Entry 或确认事件时返回 `WAIT + Next + Expiry`，没有现实下一事件时进入 `NO_TRADE`。需要价格先向计划方向越过 Trigger 时使用 Stop entry；位置与 Context 已允许承担较少确认并换取价格改善时才使用 Limit；breakout、follow-through 或 acceptance 已完成且继续等待代价更高时可以使用 Market / close。

Entry、Stop 与 Target 必须沿同一引用链形成：

```text
Price Map 中的 Region
→ Active Test 的互动和 Trigger Boundary
→ Opportunity 分配目标、障碍与 Invalidation 角色
→ Candidate 选择 Entry、Planned Protective Stop 与 First / Main Target
```

Structural Invalidation 属于 Opportunity；Planned Protective Stop 是 Candidate 的账户风险边界；成交后状态可确认并覆盖实际数量的 Active Protective Stop 属于 Execution State。Protective Stop 先触发可以结束 Candidate，而市场 Opportunity 未必已经失效。

### 8. Trade Gate｜当前唯一决定是什么？

**检查**

1. 双向扫描是否完成，为什么选择当前 Opportunity？
2. Context Permission 是否允许；Activation 已满足，还是由许可的条件 Trigger 完整执行？
3. Entry、Stop 与 Targets 是否能追溯到 Price Map 或 Active Test？
4. Candidate Outcome Probability、净 Reward、Risk、实质相关成本、剩余时间和管理是否形成正方程？
5. Planned Risk、Size 和执行可靠性是否允许；多层、已有暴露或新增风险订单时，Risk Limit / Committed / Available 是否允许？

| 输出 | 动作 | 必须明确 |
| --- | --- | --- |
| Candidate 完整、方程成立、账户可靠表达 | `EXECUTE` | 冻结 Trade Plan，进入 Ready to Submit；尚未产生订单意图 |
| 当前问题值得跟踪，但缺 Next / Activation 或当前表达 | `WAIT` | 下一可观察事实与 Expiry |
| 当前没有现实 Candidate 或值得等待的事件 | `NO_TRADE` | 排除原因；新 Reframe 后再评 |

已经提交并等待成交的 Stop / Limit 属于 Working Order，不是 Wait。

## 四、增量更新｜只沿变化传播

普通新 K 线、价格事件、Session / 时间边界或计划条件发生时只问：

```text
1. Frame、Safety 或账户事实发生边界变化了吗？
2. Price Map / Current Move / Active Test 出现了什么新事实？
3. Context / Long / Short Opportunity / Likely Sequence 因此改变了吗？
4. Candidate / Trade Plan / Risk / Action 因此改变了吗？
```

全为“否”：`NO_CHANGE`，继续观察、继续工作原订单或按计划持仓，不产生人工记录。

任一项为“是”：从最早改变的步骤重开，沿因果链向后传播；后续输出未变即停止。价格事件用[市场决策事件导航](market_decision_events.md)定位最小重开范围；Frame / Session 事件从 Frame 开始；计划、订单、仓位、保护或风险变化直接进入对应状态路由。

只有交易周期、主导组织、Control、当前区域问题或 Opportunity Set 被替代时，才重做完整 Market Read。常见 EMA 首次测试、surprise、breakout pullback、第二/第三次测试、三推、ii / ioi、MTR 和目标到达只是通用路由的快捷卡，不建立新状态。

## 五、账户状态路由

完整订单、成交、保护和复盘语义由[执行、持仓与复盘](execution_management_and_review.md)拥有。以下状态入口引用完整 Checklist 已确认的上游结论，并只检查当前账户状态需要解决的问题。

### Flat / Observing

- 当前完整 Market Read 是否仍有效，还是需要 Reframe？
- Long 与 Short 分别准备完成什么，下一事实是什么？
- 当前是 `NO_CHANGE`、需要跨事件保存的 `WAIT`，还是已经产生并完成 Trade Gate 的 Candidate？

没有 Candidate 就继续观察；Candidate 先经过 Trade Gate，只有 `EXECUTE` 才冻结 Trade Plan 并进入 Ready to Submit。

### Ready to Submit

- 所选 Opportunity、Activation、Invalidation、Targets、周期和时间范围是否仍有效？
- Safety、实际仓位、全部工作订单、保护和总 Stop 风险是否仍允许新增风险？
- Entry 使用 Stop、Limit 还是 Market / close；方向、价格规则、数量、有效期与取消条件是否正确？
- Planned Stop、Targets、Size、风险和方程是否仍按当前允许成交范围成立？
- 成交后保护怎样覆盖实际数量；部分成交、拒单、回执不明或连接异常怎样处理？

关键输入改变时不提交，返回 Trade Construction。提交订单只产生订单意图，并立即进入订单生命周期；状态未确认时按 `Submitted Unknown` 核对账户且不重复提交，确认工作后才是 `Working`。

### Working Order

- 实际 Order State、仍可能增加的 Exposure、Risk Committed 与总 Stop 风险是什么？
- Opportunity、允许成交范围、方程、有效期和取消条件仍成立吗？
- 如果现在成交，Active Protective Stop 能否按计划覆盖实际数量？

继续有效则保持工作；Opportunity 失效、过期或成交范围外方程不再成立时撤单并确认。部分成交、撤单中或 OCO 另一侧未确认取消时，按所有仍可能成交的最坏暴露处理；图表触发、撤单请求和账户确认不是同一事实。

### Open Position

每个相关事件按以下顺序检查：

```text
1. 实际数量、工作订单与 Active Protective Stop 一致吗？
2. Price Map / Current Move / Active Test 出现了什么新事实？
3. 所选 Opportunity 增强、保持、削弱、失效、完成还是过期？
4. 竞争 Opportunity 只是出现或增强，还是已经获得接受？
5. Target、Invalidation、Active Stop、时间或原计划条件发生了吗？
6. 是否形成了能容纳管理周期正常波动并降低风险的新保护锚点？
7. 当前动作：Hold / Stop Adding / Reduce / Trail / Exit？
```

| 所选路径与竞争路径 | 允许动作 |
| --- | --- |
| 所选 Opportunity 增强或保持；竞争路径仍弱或仅出现 | 按计划持有；计划内 Add 运行 Add Gate，计划外新增风险构造新 Candidate |
| 所选 Opportunity 削弱但未失效；竞争路径增强但未接受 | Hold、Stop Adding，或执行预写减仓 / 目标收缩 |
| Structural Invalidation 或强反向动量已经否定所选路径 | 取消剩余新增风险并主动退出；归零前维持保护 |
| 竞争 Opportunity 获得接受并否定所选路径 | 先处理原仓位；反向交易重新构造 Candidate |
| Target、Active Stop、时间或账户条件发生 | 按 Outcome Criterion 处理并核对实际剩余仓位 |

退出原方向不提供反向交易许可。Trapped traders 和预期退出压力只解释已发生的失败与跟随链。Trailing / Breakeven 只能使用已经形成、与管理 horizon 一致、能容纳正常波动并降低开放风险的新保护锚点；Stop amend / replace 以确认后的新价格和数量为准，确认后原保护由修改后的 Stop 直接取代。

### Add Gate｜是否使用剩余风险？

同一 Trade Plan 可以预留未使用风险。Add Gate 是冻结计划内新增层的短版 Trade Construction / Trade Gate，不是绕过风险门的授权；到达计划内价格改善区域或确认事件时运行：

```text
原 Opportunity 仍有效，竞争路径尚未获得接受？
→ Add 条件已发生，取消条件未发生？
→ 当前使用 Limit 取得价格改善，还是用 Stop / Market 等待确认？
→ 当前 Entry、共同或独立 Stop、Targets、时间与管理仍形成正方程？
→ 当前 Risk Available 足以容纳按实际价格计算的新数量？
→ ADD_TO_READY / HOLD RESERVE / CANCEL ADD
```

`ADD_TO_READY` 只冻结本层的 Entry Method、价格规则、数量、Stop、触发依据和加仓后风险，并进入 Ready to Submit；实际提交仍由执行前复核负责。`HOLD RESERVE` 保持 Open Position，`CANCEL ADD` 撤销剩余额度的使用资格；已有 Working Add 需撤单并确认，确认前继续计入风险。Risk Limit、Initial Limit、Add Permission、Cancel Add 与 Stop Rule 属于冻结 Trade Plan；Risk Committed / Available 由 Execution State 根据实际仓位、仍可能增加暴露的订单和保护动态维护。剩余额度或 Trail 后释放的容量不构成加仓理由。

### Safety Exception

- 真实净仓位、所有可能成交订单和最坏暴露是什么？
- 保护、数据、连接、回执或账户事实哪里不一致？
- 当前安全动作是核对、恢复保护、撤单、减仓还是退出？

异常解除并重新确认实际状态前不新增风险。市场分析不能替代账户恢复。

### Closed / Review

- 实际仓位已经归零，剩余工作订单与保护订单的最终状态都确认了吗？
- 原 Opportunity 的 Market Result、计划表达的 Trade Outcome 和实际 Account Result 分别是什么？
- 执行属于按计划、正常不确定结果，还是系统违规？
- 哪一两项关键差异会改变后续计划、风险或规则样本；没有则记无？
- 若进入概率校准，条件、目标事件、周期、horizon 和判断时点是否与样本定义一致？

输出最小 Review，并关闭当前 Trade Plan / Candidate。关联 Opportunity 按自身事实更新为 `ACHIEVED / INVALIDATED / EXPIRED / SUPERSEDED / SEQUENCE_UNKNOWN`；若仍为 `ACTIVE`，返回 Flat / Observing，并使用新的判断时点决定是否形成另一 Candidate。只有异常、违规、多分支、顺序不明或规则校准样本才展开完整 Review Record；复盘不改写原始计划和当时可见事实。

## 六、必要记录

系统按事件保存最小增量：

| 事件 | 保存内容 |
| --- | --- |
| 普通观察，机会、风险和动作未变 | 无 |
| 新市场问题或 Opportunity 实质改变下一观察 | 更新 Next / Expiry；需要跨事件保留时合入 Decision Record |
| 需要跨事件跟踪的 Wait | 最小 Decision Record |
| 形成 Execute / 选中 Candidate | 直接冻结 Trade Plan |
| 普通扫描得到 No Trade | 无；只有改变观察计划、风险或规则样本时记原因 |
| 实质修改计划、仓位、保护或风险 | 在原 Trade Plan 追加 Delta |
| 成交、拒单、部分成交、撤单确认、异常、减仓或退出 | 平台原始事实 + 必要差异 |
| Opportunity 或交易结束 | 终结事实；盘后复盘 |

```text
Decision Record（跨事件 Wait；重要 No Trade 按需使用）
- 时点 + 品种 / 周期
- 决定：Wait / No Trade
- Market Read：Context + 当前区域 / 测试（一短句）
- Long / Short 结论 + 必要的 Likely Sequence
- 边界：Next / Activation / 最强反方 / Invalidation / Expiry

Trade Plan（Execute）
- 时点 + Market Read + Long / Short 结论
- 所选 Opportunity：Direction / Role / Horizon + Objective / Target
- Against / Invalidation / Expiry
- Entry Method + Entry + Planned Stop + Target + Size
- Candidate Outcome Probability / 区间 + 净 Reward:Risk
- 直接使用条件规则时附目标事件、Market Probability / Rule Match
- 多层计划另加 Risk Limit / Initial Limit / Add 与取消条件
```

Wait 后形成 Execute 时，保留原 Wait 时点并追加新的判断时点，再升级为 Trade Plan。复杂多层、多目标、跨 Session、OCO 或异常计划才展开完整字段。平台已可靠保存的订单、成交和费用不人工重抄。

## 七、运行不变量

- Context 先继承，后由 Price Map、Current Move 与 Active Test 确认、转换或重构。
- Market Read 先固定位置与连续价格事实，再分别构造 Long / Short Opportunity；双向扫描完成后才构造 Candidate。
- Price Map 唯一登记区域；Opportunity 为区域分配 Support / Resistance、Entry Area、Obstacle、Magnet、Target 与 Invalidation Reference 角色。
- Pattern 名称只解释 Price Process；新位置、新测试、新反应和 follow-through 才提供事实增量，同一价格链不重复计数。
- Correction、reversal、continuation 与 range return 按 objective 和 horizon 分开，并可按 Likely Sequence 先后发生。
- Market Targets 与 Structural Invalidation 属于 Opportunity；Trigger、Entry、Planned Protective Stop 和 Candidate Targets 属于 Candidate；Active Protective Stop 属于 Execution State。
- Market Probability 与 Candidate Outcome Probability 分开；Trader's Equation 只使用与当前 Entry、Stop、退出、成本、时间和管理一致的结果概率。
- 认知变化不自动产生交易动作；新 Opportunity 或计划外新增风险重新经过完整 Trade Construction / Trade Gate，冻结计划内 Add 经过 Add Gate；两者都进入 Ready to Submit 并重新确认 Safety。
- 普通未变事件不记录；Wait、No Trade、未成交机会、实际交易和规则样本分别闭环。
