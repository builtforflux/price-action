# 失败突破回归（Failed Breakout Return）

> **状态：Strategy / Application**
>
> 本文把区间 fade 命题实例化为"越界后缺乏跟进并重新进入旧区域"；它不生成具体订单参数。

## 交易命题

价格真实越界并收在边界外（或短暂越界），但突破缺乏跟进并快速回到区间内，价格恢复区间内轮动；真空快冲到明显目标/边缘附近且未获接受时，也适用同一回归逻辑。

本页是 [边缘确认 fade](edge_fade_confirmed.md) 的具名子型：以"越界并收在外/短暂越界后重新进入旧区域"为触发上下文，premise、失效边界与内部目标继承边缘确认 fade；差异在于本页显式覆盖真空快冲场景。

## 情景判定

- 区间成熟，边缘突破尝试未被接受；
- 重新进入旧区域后反向证据出现（反向触发或持续反向 K 线）；
- 到区间内部现实目标仍有空间。

## 触发类别

- 重新进入旧区域后的反向触发（stop entry）；
- 真空快冲场景中，价格快速接近明显目标、看起来像强趋势但只是目标附近订单集中时，等待未获接受的确认后再按 fade 处理。

Vacuum 定义见 [支撑阻力与目标](../../core/02_context/01_support_resistance_targets.md#磁吸目标) 与 [交易区间](../../core/01_market_cycle/02_trading_ranges.md)。

## 失效与 Stop 锚点

- 突破获得接受并形成方向控制（回踩守住边界外、跟进持续）——基础状态可能更新为 trend，原 fade 命题结束；
- 再次跌破失败极值（底部做多）或再次升破失败极值（顶部做空）并在区间外获得接受。

Stop 锚点类别：失败极值外（只有在再次越过它足以否定 fade premise 时）。

## 目标与管理

回到区间内部价值区域；若区间另一侧随后发生成功突破，区间高度 measured move 属于新的 breakout 命题，不再沿用 fade 目标。管理：按 scalp 管理区间内部目标；再次越界获接受时按 premise 变化退出；时段尾段剩余时间不足时，不继续加仓等待均值回归。

## 常见误读

- 把单次越界当成新价格已被接受；
- 突破失败后机械反手而不建立新的反向 Setup；
- 把 gap 边界或中点机械设为 target（"缺口迟早回补"不是目标可达性依据）。

## 相关来源

- [交易区间](../../core/01_market_cycle/02_trading_ranges.md#区间突破)
- [接受、失望与失败证据](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md)
- [交易区间 Fade Setup](../../core/05_setups/03_trading_range_fade.md)
