# MTR 早期与确认两版本

> **状态：Strategy / Application**
>
> 本文把 Major Trend Reversal 命题实例化为两个风险承担时点；它不生成具体订单参数。

## 交易命题

成熟趋势失去控制：反向突破原通道/趋势线 → 原趋势测试旧高或形成 lower high（镜像）→ 测试失败并出现反方触发 → 反向两腿或较大的 trading range。

## 两个风险承担时点

| 版本 | 时点 | 典型概率交换 | 代价 |
| --- | --- | --- | --- |
| 早期版 | 强反向 breakout 前：依据通道破坏和旧极值测试失败入场 | 约 40% | 需要较大潜在回报（约 2R 基线） |
| 确认版 | 强反向 breakout 与 follow-through 后 | 约 60% | entry 更差、stop 可能更远、剩余 reward 更小 |

两个版本必须形成两份 Trade Plan，不能拼接前者的 entry、后者的概率和基于候选 K 线的更窄 stop。概率数字是这一特定风险交换的典型范围，不是固定胜率。

## 触发类别

- **早期版（强反向 breakout 前）**：旧极值测试失败后，反向 signal 的 stop entry——逆势多单 buy stop 越过反向 signal bar 高点，逆势空单 sell stop 越过其低点；或等价的可观察触发（例如趋势线破坏后的回抽触发）。入场前必须已经出现通道/趋势线破坏与旧极值测试失败，只凭"通道破坏"或"旧极值测试失败"中的单项不构成触发。
- **确认版（强反向 breakout 与 follow-through 后）**：三种可观察触发之一——follow-through bar 或后续连续强收盘附近的顺势参与、回调后的 stop entry（越过回踩 signal bar 极值）、或回踩守住旧边界后的重新触发。首根强反向 breakout 收盘附近的参与属于预测/早期版（BTC/STC 的早期版本，见 [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md#buy--sell-the-close)），不配用确认版约 60% 的语境。确认版不能继承早期版更好的价格，早期版也不能借用确认版的 follow-through 概率。

两个版本分别使用自己的 entry、active protective stop、target 与 Trader's Equation。

## 情景判定

- 成熟趋势；
- 通道或趋势线被破坏（证据有时效）；
- 原趋势对旧极值的测试失败（higher high / lower high / lower low / higher low 只是四种几何结果）；
- 反方触发并（视版本）获得后续支持：对早期版是入场后的管理验证，对确认版是入场前条件。

## 失效与 Stop 锚点

- 价格重新越过并接受旧趋势极值；
- 原趋势以强 breakout 和 follow-through 恢复控制（此时 MTR 证据链重置）；
- 反向腿缺少质量时，更常见结果是 minor reversal、原趋势 flag 或 trading range。

Stop 锚点类别：早期版在旧趋势极值测试或完整反转结构外；确认版可依赖新反向趋势的 major higher low / lower high、回踩结构或完整 breakout 起点。

## 目标与管理

成功 MTR 的直接预期是反向两腿和 swing profit，且常先发展成较大的 trading range，而不是立即成为无回调新趋势。TBTL 帮助描述持有时间与腿数，但不是价格目标；实际 target 必须落在均线、前 swing、旧公平区域、区间边界或其他现实 magnet 上。

## 语境数字

- 反向压力启发式：约五根强反向 K 线，或约十根普通/较弱反向 K 线逐步累积；根数既非必要也非充分条件；
- 课程结果分类：约 60% 的 MTR 最终只形成次要反转，约 40% 形成波段（与入场时点 40/60 分母不同）；
- 低概率版本常以约 2R 检查是否有足够补偿。

## 常见误读

- 把 climax、wedge、final flag 或第一根反向强 K 线直接当成完整 MTR；
- 通道破坏后没有等待或识别旧极值测试；
- 用突破确认后的概率配合突破前的理想 entry；
- 把 TBTL 当成固定价格目标或最低成立根数。

## 相关来源

- [主要趋势反转](../../core/05_setups/04_major_trend_reversal.md)
- [概率、风险和回报](../../core/00_method/01_probability_risk_reward.md)
- [Scalp 与 Swing](../../core/06_trade_plan_and_management/01_scalp_vs_swing.md)
