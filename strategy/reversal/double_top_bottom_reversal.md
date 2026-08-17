# 双顶双底逆势修正（含头肩边界）

> **状态：Strategy / Application**
>
> 本文把尚未完成完整 MTR 证据链的双顶/双底反转尝试实例化为 minor-reversal scalp；完整 MTR 另行路由。

## 交易命题

趋势后期第二次测试旧极值区域失败，随后跌破中间 swing low（双顶 neckline）或突破中间 swing high（双底 neckline），说明原趋势延续遇阻并形成可交易的反转尝试。完整 MTR 链尚未成立时，本页只押注两腿修正或进入 trading range，默认按 minor-reversal scalp 管理。

## 适用情景与路由

- 两个测试位于近似价格区域（不要求完全相等）；
- 第二次测试失败；
- 上下文决定家族归属：
  - **趋势后期且完整 MTR 链未成立**：由本页按 minor reversal 承接；
  - **通道/趋势线破坏、旧极值测试失败和反方控制转移均成立**：双顶/双底只作为结构证据，路由到 [MTR 早期与确认两版本](mtr_early_and_confirmed.md)；
  - **成熟区间顶部/底部语境**属于区间 fade 家族（见 [区间内第二次信号](../range/edge_second_signal.md)），不自动属于本页反转命题；
  - **趋势内回调语境**的双测试是 double top/bottom flag（延续逻辑），见 [双测试旗形延续](../trend/double_flag_continuation.md)。
- 头肩不作为独立家族：只有完整 MTR 骨架成立时才路由 MTR；否则仍只是本页所述的双测试 minor attempt，不能缩成“右肩 + neckline = MTR”。

定义见 [双顶、双底和旗形变体](../../core/04_patterns/04_double_tops_bottoms.md)。

## 触发类别

Neckline 突破确认一次可交易的反转尝试；更强的 follow-through 或第二信号会改变当前计划的概率与价格，但不能反向借给较早入场。Neckline 的单次越界不等于相反趋势已经确认。

## Premise 失效

- 已确认的双顶下破失败后，价格重新上穿 neckline 并恢复上涨——保留"先突破、再失败、重新接受"的事件顺序，并可以提出反向量度假设；
- 已确认的双底上破失败后，价格重新下穿 neckline 并恢复下跌，完全镜像；
- 只有价格位于 neckline 哪一侧不能追认失败。

## Protective Stop 锚点

完整反转结构外，或足以确认 neckline 已被原方向重新接受的边界外。

## 直接预期与目标

直接预期是两腿修正或进入 trading range，目标优先使用均线、前 swing、旧公平区域或区间内部等附近现实 magnet。形态高度量度只在结构清楚且 neckline 外价格获得接受时作为候选，实际目标选择回到 [支撑阻力与目标](../../core/02_context/01_support_resistance_targets.md)。

## 管理边界

默认按 scalp 管理。只有入场前已经把 runner 与 scalp 分开预算，或原 scalp 退出后出现新的完整 MTR 触发并建立新计划，才允许转入 MTR swing；不能用入场后补齐的 MTR 证据事后改写原计划。

## 常见误读

- 把双测试直接当成反转信号；
- 忽略 neckline 确认或失败链；
- 把不足以构成 MTR 的双顶/双底借用 MTR 的 swing 目标和概率；
- 把 micro double 在 spike 内（one-bar flag）与 flag 末端（reversal setup）的含义混用。

## 相关来源

- [双顶、双底和旗形变体](../../core/04_patterns/04_double_tops_bottoms.md)
- [逆势修正 Scalp](../../core/05_setups/05_minor_reversal_scalp.md)
- [主要趋势反转](../../core/05_setups/04_major_trend_reversal.md)
- [接受、失望与失败证据](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md)
