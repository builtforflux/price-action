# 完整流程场景测试

> **状态：Trading System / Worked Examples**

以下价格只验证同一运行流程怎样处理不同 Context、结构视图、跟随和执行状态，不建立 Setup 路由。

## 一、Tight Bear Channel：三推与 H2 仍不许可逆势

```text
Context
- 5m Tight Bear Channel；Always In Short；分离保持，反弹浅

Price Map
- 当前位于新低和通道下沿；上方 EMA 很近，逆势净空间有限

Price Process
- From：连续、低重叠的空头腿
- Now：第三推后反弹，再次下探形成 Double Bottom / H2 视图
- Role：当前 Down Leg 仍是空头 continuation attempt；多头只形成 reversal attempt
- Change：Selling Pressure 仅略减；没有连续 bull bars，gap 未关闭
- Testing：空头是否仍能维持旧低下方控制
- Next：强 bull breakout + follow-through，或空头恢复
```

`三推 / Wedge / L3` 是第一段推进的视图，`H2 / Double Bottom` 是后续第二次测试的视图；它们可以是两条增量价格链，但形态名称本身不改变 Tight Channel Permission。

```text
Up / Correction Opportunity
- Objective：EMA 或很小两腿修正
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

这验证：H2 可以真实存在，却仍然不是入场许可；卖压减弱也不等于买压建立或 Always In 翻转。

## 二、Broad Bear Channel：修正 scalp 与 major reversal 分开

5 分钟 Bear Broad Channel 第三推到 `100`，反弹到颈线 `101`，随后第二次下探 `100.10` 且卖压明显更弱。`102` 同时接近下跌腿 50%、EMA 和 Double Bottom 高度投射：`101 + (101 - 100) = 102`。

```text
Price Process
- From：Bear Broad Channel 的第三次 Down Leg
- Now：反弹后的第二次低位测试
- Role：空头 continuation attempt，同时测试能否激活短期 Up / Correction
- Change：延伸缩小、Overlap 增加、第二次测试 Selling Pressure 更弱
- Testing：旧低守住后先修正，还是空头恢复
- Next：bull signal + follow-through，或 100 下方接受
```

| Opportunity | Objective | Activation | Invalidation | Market Probability |
| --- | --- | --- | --- | --- |
| Up / Correction | `102` target cluster；短期 scalp / 两腿修正 | 好 bull signal，突破微型下降线并出现实际跟随 | `100` 下方重新接受 | 与 Broad Channel 边缘反应、第二次测试及当前时点匹配 |
| Up / Reversal | `103` 通道起点及更高；swing | 强 bull breakout、follow-through、破坏 lower high，回调形成 HL 且空头恢复失败 | 空头重新建立主要结构控制 | 当前尚未匹配；不能借用 correction 概率 |
| Down / Continuation | `99` 旧低或下一 magnet | 直接在 `100` 下方接受，或先反弹到 `102` 后恢复卖压 | 多头破坏空头结构并获得接受 | 仍受 Bear Context 支持，但直接追空位置差 |

若形成高点 `100.50`、低点 `99.80` 的强 bull signal bar，并有足够空间：

```text
Long Correction Candidate
- Trigger / Entry：buy stop above 100.50
- Opportunity Invalidation：100 下方重新接受
- Planned Stop：按该候选正常波动和账户风险确定，不改写市场 Invalidation
- Target：102
- Candidate Outcome Probability：按当前 Entry、Stop、退出与成本估计
- Management：逆主要趋势，只按 scalp / correction 管理
```

没有 follow-through 时 Opportunity 削弱；不能因为已经成交就把 correction 改写成 reversal。到 `102` 后若出现强 bear response，当前多头目标结束，重新计算 Down / Continuation Candidate。

## 三、强突破：买收盘、等跟随还是等 H2

成熟区间上沿 `200` 被大 bull bar 突破并收于 `202`；区间高度事前固定，主要目标为 `206`。

```text
Up / Breakout Opportunity
- Objective：206 measured-move area
- Why：区间上破 + 强实体 / 强收盘（同一突破链）
- Activation：计划若允许早期风险，可由强收盘激活；保守表达等待 follow-through 或回踩守住
- Invalidation：重新接受 200 下方并形成 bear follow-through
- Market Probability：只匹配当前 breakout quality、objective 和 horizon
```

| 判断时点 | Candidate | 新信息 | 代价 |
| --- | --- | --- | --- |
| 强 bar 收盘 | Buy close near `202` | 最早表达 | Acceptance 尚不完整，Stop 可能较宽 |
| 下一根跟随后 | Buy near `202.8` | 新增独立持续事实 | Entry 更差，剩余 Reward 下降 |
| 回踩突破点后 | Buy pullback / H1-H2 | 可能获得结构更清楚的 Entry | 可能踏空；深回区间会使 Opportunity 失效 |

每个 Candidate 都重新估计交易结果概率和方程；不能用 follow-through 后的概率配合 `202` 的旧 Entry，也不能因为出现 H2 再增加一票。

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
Price Process：中部 Local Balance，Pressure balanced
Permission：中部不做 range fade；形态不提供方向
Decision：WAIT for breakout + follow-through + hold
```

同一 `ioi` 在两个 Context 中拥有不同 Role、目标和 Candidate Permission。系统没有切换“ioi 策略”，只更新外层作用和后续接受。

## 五、Failed Breakout、Gap 与 trapped traders

区间上沿 `300` 上破后形成小 gap，但下一根缺少 bull follow-through，随后跌回 `300` 下并连续收在旧区间内：

```text
From：Bull Breakout Attempt
Now：gap 关闭并重新进入旧区域
Role：原突破 failure test；当前 Down Leg 尝试成为 Range Return
Change：Bull Separation 关闭，Selling Pressure 建立
Testing：旧区间是否重新获得接受
Next：区间内 bear follow-through，或多头再次收复 300
```

- 第一次回到 `300` 下只削弱 Up / Breakout；
- 旧区间获得接受后，Up / Breakout 才失效；
- `trapped breakout buyers` 解释潜在退出压力，但不在 gap 关闭、re-entry 和 bear follow-through 之外重复增加证据；
- Down / Range Return 只有在自己的 Activation、目标、Invalidation 和 Context Permission 完整后才生成 Candidate。

## 六、订单异常不改写市场判断

某个已选 Candidate 计划 `Entry 301`、`Stop 299.8`、`Target 303.4`、`Size 2`。提交 buy stop 后回执不明：

1. Order State = `Submitted Unknown`，不重复下单；
2. 核对经纪商账户；若部分成交 1 单，Exposure = `Open(1)`；
3. Active Protective Stop 未确认覆盖时，Protection = `Deficient`，停止新增风险并恢复保护、减仓或退出；
4. 撤单请求未确认前，剩余数量仍按可能成交计入最坏暴露。

Execution State 只更新订单、敞口和保护，不倒推 Opportunity、Market Probability 或当时 Trade Plan。

## 七、共同闭环

```text
Inherited Context + Price Map
→ From–Now–Role–Change–Testing–Next：Bars / Continuity / Separation / Pullback / Opponent → Pressure / Control
→ Confirm Context / Transition / Reframe
→ Long / Short Opportunity：Objective、Activation、Invalidation、Market Probability
→ Context Permission
→ Candidate：Trigger、Entry、Stop、Target、交易结果概率与方程
→ Execute / Wait / No Trade
→ Follow-through、Acceptance、Failure 与账户事件持续更新
```

H2、Double Bottom、Wedge、Flag、ioi、Triangle、Gap、MTR 和 trapped traders 都只能改变这条共同过程中的某一部分，不建立独立路由，也不按名称数量投票。
