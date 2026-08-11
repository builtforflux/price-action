# 均线缺口回调（Moving-Average Gap Bar）

> **状态：Strategy / Application**
>
> 本文把趋势延续命题实例化为三类 moving-average gap bar 语境；它不生成具体订单参数。

## 交易命题

这三类语境都描述原趋势对旧极值的最后测试：市场触及均线反侧后，原趋势通常仍会测试旧极值。

## 三类语境

1. **强趋势首次深回调穿过均线**：整根 K 线来到均线反侧（牛趋势中该 K 线最高价低于当根均线值；熊趋势镜像）。市场通常仍会测试原趋势极值。
2. **长期未触均线后的首次触及**：连续约 20 根或更多 K 线未触及均线后，首次触及均线常成为测试原趋势极值的背景。
3. **Second moving-average gap bar**：第一次朝均线的反转若未能触及均线、价格又远离，下一次朝均线的反转可称 second MAG bar setup。

最低几何定义见 [缺口](../../core/04_patterns/07_gaps.md#术语边界)。根数是典型线索，不是硬阈值。

## 触发类别

均线反侧 K 线之后出现顺势触发（stop entry 越过后续 signal bar 极值），仍需趋势强度、具体触发和可承担的 stop 支持；不是机械均线挂单规则。

## 失效与 Stop 锚点

- 测试旧极值失败，随后形成趋势线破坏、旧极值测试和反方触发——此时本语境升级为 MTR 的背景（见 [主要趋势反转](../../core/05_setups/04_major_trend_reversal.md)）；
- 原趋势失去控制。

Stop 锚点类别：定义测试失败的结构外。

## 目标与管理

直接预期是"测试旧趋势极值"，支持 swing 到旧极值或其他现实 magnet。后续若测试失败，按 MTR 的失效与目标重新判断。

## 常见误读

- 把 moving-average gap bar 当成机械均线挂单规则；
- 把首次均线测试本身提前命名为完整 MTR；
- 忽略趋势强度与目标空间。

## 相关来源

- [缺口](../../core/04_patterns/07_gaps.md)
- [趋势延续 Setup](../../core/05_setups/01_trend_continuation.md)
- [支撑阻力与目标](../../core/02_context/01_support_resistance_targets.md)
