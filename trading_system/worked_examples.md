# 完整流程场景测试

> **状态：Trading System / Worked Examples**

以下价格只验证同一运行流程怎样处理不同 Context、结构视图、跟随和执行状态，不建立 Setup 路由。

## 一、Tight Bear Channel：三推与 H2 Setup 仍不许可逆势

```text
Context
- 5m Tight Bear Channel；Always In Short；分离保持，反弹浅

Price Map
- 当前位于新低和通道下沿；上方 EMA 很近，逆势净空间有限

Price Process
- From：连续、低重叠的空头段
- Now：第三推后反弹，再次下探形成 Double Bottom / H2 recovery setup
- Role：当前 Down Leg 仍是空头 continuation attempt；多头只形成 reversal attempt
- Pressure：Bear 仅略减；Bull 尚未建立，没有连续 bull bars，gap 未关闭；Bear Control 保持
- Testing：空头是否仍能维持旧低下方控制
- Next Observation：强 bull breakout + follow-through，或空头恢复
```

第一段第三次下探可形成 `三推 / Wedge Bottom / H3 Setup` 视图；后续反弹已经形成第一次向上恢复 Trigger 后，再次下探可形成 `H2 recovery setup / Double Bottom`。它们是两段实际测试链，名称本身不改变 Tight Channel Permission。定义潜在边界的完成 K 线可以按课程称为 H2 Signal Bar，但当前运行只把它作为 Response：Context Permission 不允许 Long Candidate；其高点尚未被越过时，也不能把 H2 Trigger 或 Chart Entry 写成已经发生。

```text
Up / Correction Opportunity
- Objective：EMA 或很小两段修正
- Activation：强 bull breakout、follow-through，并开始关闭分离
- Invalidation：旧低下方重新建立空头分离与跟随
- 当前状态：未 Activation

Down / Continuation Opportunity
- Objective：下一现实空头 magnet
- Activation：空头恢复并保持新低下方接受
- Invalidation：强 bull breakout 与 follow-through 破坏 tight-channel control
```

当前只有一根普通 bull reversal bar：

- Context Permission 不允许生成逆势 Long Candidate；
- 不在通道底部直接追空，因为位置与空间可能不利；
- Decision = `WAIT`：等多头完成 Activation，或等空头恢复后重新计算顺势 Candidate。

这验证：H2 Setup 可以真实存在，却仍然不是入场许可；即使随后 Trigger 发生，卖压减弱也不等于买压已建立或 Always In 翻转。

## 二、Broad Bear Channel：修正 scalp 与 major reversal 分开

5 分钟 Bear Broad Channel 第三推到 `100`，反弹到颈线 `101`，随后第二次下探 `100.10` 且卖压明显更弱。`102` 同时接近下跌段 50%、EMA 和 Double Bottom 高度投射：`101 + (101 - 100) = 102`。

```text
Price Process
- From：Bear Broad Channel 的第三次 Down Leg
- Now：反弹后的第二次低位测试
- Role：空头 continuation attempt，同时测试能否激活短期 Up / Correction
- Pressure：Bear 相对上次减弱；Bull 在局部开始建立但尚待 signal / follow-through；Bear Control 减弱但未转移
- Testing：旧低守住后先修正，还是空头恢复
- Next Observation：bull signal + follow-through，或 100 下方接受
```

| Opportunity | Objective | Activation | Invalidation | Market Probability |
| --- | --- | --- | --- | --- |
| Up / Correction | `102` target cluster；短期 scalp / 两段修正 | Broad Channel 边缘第二次测试被拒绝并完成合格 bull signal；保守 Candidate 另等实际跟随 | `100` 下方重新接受 | 与 Broad Channel 边缘反应、第二次测试及当前时点匹配 |
| Up / Reversal | `103` 通道起点及更高；swing | 强 bull breakout、follow-through、破坏 lower high，回调形成 HL 且空头恢复失败 | 空头重新建立主要结构控制 | 当前尚未匹配；不能借用 correction 概率 |
| Down / Continuation | `99` 旧低或下一 magnet | 直接在 `100` 下方接受，或先反弹到 `102` 后恢复卖压 | 多头破坏空头结构并获得接受 | 仍受 Bear Context 支持，但直接追空位置差 |

若形成高点 `100.50`、低点 `99.80` 的强 bull signal bar，并有足够空间：

```text
Long Correction Candidate
- Entry Basis：完成的 H2 bull response / Signal Bar
- Trigger / Entry：buy stop above 100.50
- Opportunity Invalidation：100 下方重新接受
- Planned Stop：按该候选正常波动和账户风险确定，不改写市场 Invalidation
- Target：102
- Candidate Outcome Probability：按当前 Entry、Stop、退出与成本估计
- Management：逆主要趋势，只按 scalp / correction 管理
```

此时 Double Bottom 是测试几何，完成 K 线在课程图表语言中是 H2 Signal Bar；因为当前 Long / Correction Opportunity、Permission 和方程都成立，Candidate 才把该 Signal Bar 纳入 Entry Basis。价格随后越过 `100.50` 才形成 H2 Trigger，该越界所在 K 线是 Chart Entry Bar；账户只有真实成交后才产生 Actual Fill Bar、Exposure 与 Active Protective Stop。

没有 follow-through 时 Opportunity 削弱；不能因为已经成交就把 correction 改写成 reversal。到 `102` 后若出现强 bear response，当前多头目标结束，重新计算 Down / Continuation Candidate。

## 三、强突破：买收盘、等跟随还是等 H2

成熟区间上沿 `200` 被大 bull bar 突破并收于 `202`；区间高度事前固定，主要目标为 `206`。

```text
Up / Balance Breakout Opportunity
- Objective：206 measured-move area
- Support / Already：区间上破 + 强实体 / 强收盘（同一突破链）
- Activation：计划若允许早期风险，可由强收盘激活；保守表达等待 follow-through 或回踩守住
- Invalidation：重新接受 200 下方并形成 bear follow-through
- Market Probability：只匹配当前 breakout quality、objective 和 Outcome Horizon
```

| 判断时点 | Candidate | 新信息 | 代价 |
| --- | --- | --- | --- |
| 强 bar 收盘 | Entry Basis 为强 breakout close；Buy close near `202` | 最早表达 | Acceptance 尚不完整，Stop 可能较宽 |
| 下一根跟随后 | Entry Basis 为新增 follow-through；Buy near `202.8` | 新增独立持续事实 | Entry 更差，剩余 Reward 下降 |
| 回踩突破点后 | 等 H1/H2 recovery setup；路径仍现实时把完成 Response / Signal Bar 纳入 Entry Basis | 可能获得结构更清楚的 Entry | 可能踏空；深回区间会使 Opportunity 失效 |

每个 Candidate 都重新估计交易结果概率和方程；不能用 follow-through 后的概率配合 `202` 的旧 Entry，也不能因为出现 H2 Setup、Double Bottom 与 Signal Bar 三个名称再增加票数。

强第一段与实际跟随可以建立第二段预期，但不自动等于 TBTL。若第二段随后在 `206` 或其他事前标出的边界吸引追随者，却不能保持接受并重新进入旧区域，才调用第二段陷阱视图；原 Up Opportunity 先按失败事实更新，Down Opportunity 仍需独立 Activation，不能把“有人被困”再算一份反向证据。

## 四、同一个 ioi：趋势 Flag 与 Range Breakout Mode

### A. 多头趋势中的 ioi

```text
Context：Bull Broad Channel
From：强 bull leg
Now：ioi 压缩且未破坏 major higher low
Role：Bull Flag / Local Balance
Testing：多头能否恢复，还是回调扩大为 Range
```

- `ioi / Triangle` 描述几何压缩；`Flag` 描述它在外层多头路径中的作用；
- 上破后仍需 follow-through 或回踩守住；
- 下破若很弱且快速收回，可能只是更深 pullback；
- 下破并获得接受、改变正常回调和 Control 后，才重分类。

### B. 成熟 Trading Range 中部的 ioi

```text
Context：Mature Trading Range + Breakout Mode
Price Process：中部 Local Balance；Bull / Bear Pressure balanced
Permission：中部不做 range fade；形态不提供方向
Decision：WAIT；Next Event = breakout + follow-through + hold；Decision Expiry = 压缩边界被重画或当前 Session 时间不足
```

同一 `ioi` 在两个 Context 中拥有不同 Role、目标和 Candidate Permission。系统没有切换“ioi 策略”，只更新外层作用和后续接受。

## 五、Failed Breakout、Gap 与 trapped traders

区间上沿 `300` 上破后形成小 gap，但下一根缺少 bull follow-through，随后跌回 `300` 下并连续收在旧区间内：

```text
From：Bull Breakout Attempt
Now：gap 关闭并重新进入旧区域
Role：原突破 failure test；当前 Down Leg 尝试成为 Range Return
Pressure：Bull Separation 关闭、Bull Pressure 减弱；Bear Pressure 随重新进入和跟随建立
Testing：旧区间是否重新获得接受
Next Observation：区间内 bear follow-through，或多头再次收复 300
```

- 第一次回到 `300` 下只削弱 Up / Balance Breakout；
- 旧区间获得接受后，Up / Balance Breakout 才失效；
- `trapped breakout buyers` 解释潜在退出压力，但不在 gap 关闭、re-entry 和 bear follow-through 之外重复增加证据；
- Down / Range Return 只有在自己的 Activation、目标、Invalidation 和 Context Permission 完整后才生成 Candidate。

## 六、订单异常不改写市场判断

某个已选 Candidate 计划 `Entry 301`、`Stop 299.8`、`Target 303.4`、`Size 2`。提交 buy stop 后回执不明：

1. Order State = `Submitted Unknown`，不重复下单；
2. 核对经纪商账户；若部分成交 1 单，Exposure = `Open(1)`；
3. Active Protective Stop 未确认覆盖时，Protection = `Deficient`，停止新增风险并恢复保护、减仓或退出；
4. 撤单请求未确认前，剩余数量仍按可能成交计入最坏暴露。

Execution State 只更新订单、敞口和保护，不倒推 Opportunity、Market Probability 或当时 Trade Plan。

## 七、标普 5 分钟：强空头 surprise 到旧突破区域

该场景按当时可见信息分段，不把最终反弹或后续下跌回填到早期判断。价格为图上近似区域，只验证运行关系。

### A. 大阴线出现前｜继承外层上涨，但区间化增加

```text
Frame
- Trading Timeframe：5m
- 当前无额外 Session / Event Constraint

Context
- 外层 Bull Broad Channel / Trending Trading Range 倾向
- 多头仍控制，但回调变深、双边逐渐可以获利

Price Map
- 4958–4960：先前整理与上涨突破起点
- 上方旧高与 4990–5000 区域
- EMA：当前方向组织参考

Current Move
- 上涨持续创新高，但高位重叠和反向 K 线增加

Active Test
- 高位是否继续获得接受，还是进入更深回调
```

此时保留 `Long / Continuation` 与 `Short / Correction`，但没有最终反转事实。

### B. 大阴线收盘｜决策事件，重新展开 Market Read

大阴线从高位快速跌向 `4958–4960`：

```text
Current Move
- Bars：异常大的 bear trend bar，靠近低点收盘
- Continuity：当前只有初始 surprise，后续跟随未知
- Separation：快速形成向下分离
- Bull Pressure：显著减弱，但外层结构尚未被一根 K 线完全否定
- Bear Pressure：由 surprise 显著建立，后续连续性未知
- Control：外层 Bull 进入 Transition；短期 Bear Control 候选

Active Test
- Object：4958–4960 旧整理 / 突破起点
- Tested Objective：当前向下 surprise 能否在该区域下方建立接受
- Phase：Touch / Overshoot 后进入 Reaction
- Resolution：Pending
- Acceptance Criterion：区域下方继续收盘、跟随或回踩受阻
- Failure Criterion：重新进入区域并形成向上拒绝与恢复
- Next Observation：空头在区域下方获得跟随与接受，或区域产生实际拒绝
- Test Expiry：区域被一侧接受，或新 Context 取代当前问题

Context Update
- Context Change：UPDATED
- Conditions：TRANSITION；不以单根 K 线直接确认完整 Bear Trend
```

`Short / Continuation` 已有强 surprise，但直接追空面对支撑、Stop 距离和空间问题；`Long / Correction` 尚无局部 Trigger。当前 Decision = `WAIT`。

### C. 局部第二次测试与反转 K｜同时更新两侧

第一次反应后再次下探近似低位，形成局部小双底；完成的 bull reversal bar 具有长下影并收在自身中点以上：

```text
Current Move
- From：强 bear surprise 到达 4958–4960 后的第一次反应
- Now：再次 Down Leg 测试近似低位，并形成局部 Reversal Attempt
- Bars：第二次测试的延伸有限；bull reversal bar 下影长、收在自身中点以上
- Continuity：空头没有立即跟随；多头 signal 已完成，向上触发与 follow-through 未知
- Separation：向下分离缩小，外层区域尚未在任一侧获得持续接受
- Bull Pressure：在局部开始建立，仍需触发或跟随
- Bear Pressure：相对 surprise 减弱，但强空头第二段风险仍在
- Control：外层 Transition；局部尚未确认 Bull Control

Active Test
- Object：4958–4960 支撑 / 突破回测
- Tested Objective：第二次向下测试能否突破区域并延续
- Phase：Reaction
- Resolution：Pending
- Attempt：第一次向上恢复 Trigger 已发生；当前第二次向下测试形成 Double Bottom / H2 recovery setup
- Response：卖出被拒绝；本根长下影并收在中点以上
- Acceptance Criterion：区域下方获得持续跟随
- Failure Criterion：向上触发并恢复到区域上方
- Next Observation：向上触发并跟随，或 signal failure 后在区域下方接受
```

外层区域、局部二次测试和 reversal-bar response 分别承担位置、次序和反应质量。该完成 K 线先更新卖压减弱与 Bull Pressure 开始建立，并在课程图表语言中是 H2 Signal Bar；只有 Long / Correction Opportunity 成立后，Candidate 才决定是否选择它作为 Entry Basis。H2、小双底、微型 W、Signal Bar 与第二次下探不按名称重复计数。

```text
Long / Correction
- Objective：向 EMA、4970 附近或大阴线内部修正
- Support / Already：重要区域 + 空头无立即跟随 + 局部第二次测试 + bull signal
- Activation：外层区域的局部第二次测试被拒绝，合格 bull signal 已完成
- Next Candidate Event：早期 Candidate 使用 signal-bar 高点 Stop Trigger；保守 Candidate 等 bull follow-through
- Invalidation：局部低点失守并在 4958–4960 下方获得接受
- Counterevidence：NONE；强 bear surprise 与第二段风险由 Short / Continuation 独立表达

Short / Continuation
- Objective：完成 bear surprise 的第二段并测试更低 magnet
- Support / Already：强空头运动与短期 Selling Pressure
- Activation：强 bear surprise 已使延续路径具备表达资格，但当前位置使直接追空 Candidate 方程不利
- Next Candidate Event：bull signal failure、局部低点下破并在区域下方跟随 / 接受，届时重算更好的 Candidate
- Invalidation：多头持续脱离低点并重新控制大阴线内部

Likely Sequence
- Up / Correction 可先到 EMA；该区域若出现 bear recovery，再重算 Down / Continuation
```

较早的 Long Candidate 把完成的 H2 Signal Bar 作为 Entry Basis，使用其上方 `Buy Stop`；越过边界的 K 线成为 Chart Entry Bar，账户实际成交后才进入 Open Position。Planned Protective Stop 引用局部双底结构并容纳正常波动，First Target 引用 EMA / 4970 区域。直接在支撑内 `Limit Buy` 以该 Region 作为 Entry Basis，是确认更少的另一 Candidate；若两个 Candidate 同时成立，Candidate Choice 只能选择当前一条表达，不能同时保留为隐藏计划。

### D. 触发后的分支｜新事实使用新 Candidate

- 向上触发并出现 bull follow-through：Long / Correction 增强，按原计划持有；一根盈利 K 线尚未形成新的保护锚点，不机械移动到 breakeven；
- 后续形成 higher low、回调守住且多头成功恢复：该 higher low 可以进入 Price Map；容纳 5m 正常波动且降低开放风险时，提交原 Active Stop 的 amend / replace，并以确认后的新价格和数量为准；
- 向上触发后重叠增加、缺少跟随，但仍守住外层区域：Long / Correction 削弱而未失效，停止新增风险，按原计划 Hold 或 Reduce；Short / Continuation 只属于竞争路径增强；
- 向上触发但立即失败：Long Candidate 削弱或结束，更新 Short / Continuation；是否反手仍使用当前 Entry、Stop 和 Targets 重建 Candidate；
- 跌破局部低点但没有接受：仍是 breakout attempt，不从一跳越界推出空头目标；
- 在 `4958–4960` 下方获得接受：Long / Correction 失效，按当前价格构造 Short Candidate；
- 修正到 EMA / 4970 后出现强 bear response：多头第一目标完成，重新运行双向扫描，不把原 Long Correction 改写成 Long Reversal。

### E. 三种运行模式怎样衔接

1. 大阴线出现前首次读取图表：运行完整 Checklist，得到外层 Bull 但区间化增加的 Market Read，以及 `Long / Continuation`、`Short / Correction` 两侧观察路径；没有 Candidate 时停在 Flat / Observing。
2. 大阴线收盘：运行增量问题。Frame 未变，Current Move 与 Active Test 改变，因此只从 Current Move 向后重开；Context Change = `UPDATED` 且 Conditions 加入 `TRANSITION`。两个方向更新后仍缺合适表达，向 Decision 提交 Next Event 与 Decision Expiry，由 Decision 输出 `WAIT`。
3. 局部第二次测试与 bull signal 完成：再次从 Current Move / Active Test 向后传播。Long / Correction 完成 Activation，才进入 Trade Construction；Short / Continuation 保留为竞争路径，但不为形式对称制造当前 Candidate。
4. Long Candidate 提交 Decision 并得到 `EXECUTE` 后冻结 Trade Plan，进入 Ready to Submit；执行前复核仍成立才提交 Buy Stop。提交后立即进入订单生命周期；回执未确认时按 `Submitted Unknown` 核对且不重复下单，确认工作后成为 Working Order。图表触发后只按实际成交进入 Open Position，并确认 Active Protective Stop 覆盖真实数量。
5. 持仓中的普通 K 线：只运行 Open Position checklist；所选与竞争 Opportunity、风险、保护和动作均未改变时，结果是 `NO_CHANGE`，不记录。出现 follow-through、signal failure、区域外接受、目标到达或新保护锚点时，才从最早变化处向后更新并追加必要 Delta。
6. 目标、Stop 或主动退出决定发生后：按退出订单生命周期处理 Unknown / Working / Rejected / Canceled / Expired / Partial / Filled；归零前保持剩余数量的实际保护，退出动作仍有效时修复或重新提交失败订单。归零终结当前 Trade Plan 时，关闭其 Entry / Add Intent、Add Permission 和仍可能新增 Exposure 的工作订单；撤销确认前继续按可能成交处理，确认残留订单与保护最终状态后再运行 Closed / Review。复盘分开 Market Result、Trade Outcome 与 Account Result；当前 Trade Plan / Candidate 关闭，关联 Opportunity 按市场事实独立更新，若仍为 ACTIVE 就返回 Flat / Observing。

该场景验证：重要位置只登记一次；Active Test 以该位置为 Object，局部第二次测试进入 Attempt / Response 并形成 signal-bar 边界，Candidate 只选择是否采用；Long / Short 路径同时存在且可能顺序实现。

## 八、Trading Range 下沿：2% 风险额度与动态第二层

BTC 5 分钟成熟 Trading Range 下沿形成现实 Long / Range Return Opportunity。示例账户配置为整份计划最多承担 `2%` 风险、第一层最多使用 `1%`；这些数字只演示额度分配，不表示通用安全比例。Planned Stop 位于能够容纳 TR 下沿正常测试的位置之外；空方在区域下方获得接受才构成市场 Structural Invalidation，Protective Stop 可以更早结束当前 Candidate。正常高流动性执行假设下预计滑点配置为零，实质相关的手续费仍进入方程。

第一笔 Entry 前只冻结：

```text
Risk Limit：2%
Initial Limit：1%
Stop Rule：两层共用结构保护 S
Add Permission：当前 Context Permission 仍允许新增风险；价格进入更低的预定区域 A，且原 Long Opportunity 仍有效；
                或区域 A 出现拒绝、bull signal / follow-through
Cancel Add：A 下方形成强 bear breakout 与 follow-through、获得接受、
            目标空间消失、时间过期或保护异常
```

第一层按当前 Entry 到 `S` 的距离使用不超过 `1%` 风险。此时另一部分只是 `Risk Available`，不是已经承诺的风险，也不是“下跌就加”的授权。

价格随后下跌几个 ticks 到区域 `A`：

- 若原计划允许在成熟区间下沿用更少确认换价格改善，且卖压没有增强、`A` 下方没有接受，可以把 Region `A` 作为 Entry Basis，按当前价格重新计算数量并使用 Limit Add；
- 若下跌动量使直接接多不再合适，则等待拒绝、micro double bottom、合格 bull signal 或 follow-through，再把必要的 Signal Bar、multi-bar response 或 follow-through 纳入 Entry Basis，并选择对应 Trigger 的 Stop / Market / Limit Add；
- 若连续强 bear bars、分离和跟随使下沿转为向下接受，执行 `CANCEL_ADD`，并按原 Long Opportunity 的 Invalidation 管理第一层。

前两种情况只有当前方程和 Risk Available 同时允许时才输出 `ADD_TO_READY`；由于第一层仍是实际 Exposure，随后并行运行 Open Position 与 Ready to Submit，重新确认实际仓位、全部工作订单、当前保护、总风险和订单参数，再提交新增层。

第二层最多使用：

```text
Risk Available = max(0, Risk Limit - Risk Committed)
q₂ = 可分配风险 / (|e₂ - S| × 每点价值 + 每单位 Execution Cost)
```

更低的 `e₂` 距共同 Stop 更近，因此同样最多 `1%` 风险时，第二层数量通常大于第一层；实际数量仍受当前目标空间、方程和最小单位限制，不要求用满。成交后立即修改并确认 Active Protective Stop 的数量覆盖整仓，再更新加权均价、Risk Committed / Available。计划内 Add 只保存 Entry Basis、Trigger、Entry Method、价格、数量、共同 Stop、加仓后总风险和触发依据。

这个例子验证：账户层只提供固定的 `2%` 风险上限；市场读取决定是否有资格使用剩余额度，当前 Entry 到共同 Stop 的距离才决定第二层数量。

## 九、长期未触 EMA 后的首次测试

标普 5 分钟处于 Bear Tight Channel，约 20 根以上 K 线未触 EMA。旧低在 `4000`，EMA、下跌段 50% 与先前小 lower high 汇合在 `4011–4013`。价格从 `4000` 反弹到该区域；反弹 K 线偏小、重叠较多，bull follow-through 一般。

```text
Event：长期分离后的首次 EMA 测试

Price Map
- 4011–4013：EMA + 50% + prior lower high
- 4000：旧低 / 顺势第一目标

Current Move
- From：连续 Bear Tight Channel 与长期 EMA 分离
- Now：Up Leg / Pullback 到 4011–4013
- Bull Pressure：略有建立，但连续性和分离较弱
- Bear Pressure：回调中减弱，尚未被反向接受否定
- Control：Bear 保持；当前是 correction，未升级为 bull reversal

Active Test
- Object：首次 EMA / target cluster 测试
- Tested Objective：当前 correction 能否突破该区域并破坏 Bear Control
- Phase：Touch 后等待 Reaction
- Resolution：Pending
- Acceptance Criterion：强 bull breakout、follow-through 并守在区域上方
- Failure Criterion：区域拒绝后 bear pressure 恢复
- Next Observation：bear signal + 向下恢复；或强 bull breakout、follow-through 并守在区域上方
- Test Expiry：区域反复穿越、测试完成，或 Context Reframe
```

双向路径不是“到 EMA 就做空”：

```text
Down / Continuation
- Objective：重测 4000；接受后再看更低 magnet
- Support / Already：Bear Control + 首次 EMA 测试 + 弱反弹
- Activation：区域内形成合格 bear signal 并向下触发；保守路径再等 bear follow-through
- Invalidation：4011–4013 上方出现强 bull breakout、跟随并守住，破坏原 lower-high 约束
- Counterevidence：首次测试也可能扩大成更深修正，当前位置的单根 signal 可能失败

Up / Reversal
- Objective：破坏 bear structure，测试更高旧公平区域
- Support / Already：反弹到 EMA；Bear Pressure 暂时减弱
- Activation：强 bull breakout + follow-through、EMA 上方回踩守住并形成 HL
- 当前状态：未 Activation；弱反弹到 EMA 本身只完成 correction objective
```

若在 `4012` 形成高点 `4013`、低点 `4010.5` 的合格 bear signal bar：

- `Sell Stop below 4010.5`：让价格先完成向下 Trigger；Planned Stop 锚定该 EMA 测试的结构高点上方并容纳 5 分钟正常波动；First Target 为 `4000`；
- `Limit Sell in 4011–4013`：以更好价格交换更少确认，只在强 Bear Context、区域与风险计划事前允许时构造，使用自己的 Entry、Stop、概率和方程；
- 等 bear follow-through 后 Market / pullback entry：确认更多但剩余空间变小，必须重新计算 Candidate，不能沿用 signal bar 时的方程。

若第一次向下恢复 Trigger 后没有延续，价格再次测试 `4011–4013` 并形成近似双顶，则当前测试可以同时表达为 `L2 recovery setup / Double Top / Bear Flag Test`。完成的 bear response 先更新卖压与区域反应，并在课程图表语言中是 L2 Signal Bar；只有 Down / Continuation Opportunity 仍现实且 Permission、方程允许时，Candidate 才把该 Signal Bar 纳入 Entry Basis。价格跌破其低点才完成 L2 Trigger，跌破所在 K 线是 Chart Entry Bar，账户真实成交仍单独确认。若区域上方先获得 bull acceptance，这组 L2 / Double Top 解释随原测试失效，不能继续提供卖出许可。

若 bull breakout 和 follow-through 先发生，取消未成交的顺势卖出计划并 Reframe 当前测试；这只使 Long / Reversal 获得新的 Already，仍需用当前目标、Entry、Stop 和剩余空间构造自己的 Candidate。若顺势空单成交后没有恢复、反而在 EMA 上方获得接受，所选 Opportunity 削弱或失效；按原计划 Reduce / Exit，不把首次 EMA 测试当作继续持有的理由。

这个例子验证：事件卡只保证及时重开正确步骤；压力、跟随、接受、位置与交易方程共同决定动作。EMA、50% 和 prior lower high 是独立来源的区域汇合，但“首次测试、EMA touch、bear flag”若描述同一回调链，不重复计票。

## 十、共同闭环

```text
Inherited Context + Price Map
→ Observable Change：由事件导航调用本次相关概念与条件规则，只从最早变化处重开
→ Current Move：From / Now / Role；Bars / Continuity / Separation / Pullback / Opponent → Bull / Bear Pressure → Control
→ Active Test：Object / Tested Objective / Phase / Resolution；H/L Trigger 次序 + Double/Wedge/Triangle 几何 + Response；Acceptance / Failure / Next Observation / Test Expiry
→ Context Update：Updated Context + Context Change
→ Long / Short Side Scan + Likely Sequence：Objective、Targets、Activation、Invalidation、Market Probability
→ Context Permission
→ Trade Construction：Entry Basis + Reference、Trigger Boundary、Entry Method、Planned Stop、Targets、Size 与管理
→ Candidate Choice：当前多个表达只选择一条；否则等待明确事件或不交易
→ Decision：Selected Candidate / 明确下一事件 / 两者皆无 → Execute / Wait / No Trade
→ Chart Entry、Actual Fill、Follow-through、Acceptance、Failure 与账户事件持续更新
```

H2、Double Bottom、Wedge、Flag、ioi、Triangle、Gap、MTR 和 trapped traders 只是示例。任何进入系统的 Brooks 知识都必须改变这条共同过程中的某一部分，或改变条件概率、Candidate、执行管理与复盘；否则只保留为同源视图、Reference 或隔离项，不建立独立路由，也不按名称数量投票。
