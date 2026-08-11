# 趋势情景

> **状态：Strategy / Index**
>
> 本页说明趋势情景下各策略命题的职责与文件入口。

## 情景判定

趋势情景要求同时成立：

- 当前 market cycle 是 trend（breakout phase / spike 或 channel），一方控制明显；
- 回调属于原趋势或通道内的测试，未破坏主要结构（major higher low / lower high）；
- 反方尝试缺乏跟进，Always In 或其他累积压力仍支持原趋势方；
- 前方保留到现实 magnet 的空间。

完整定义见 [趋势和通道](../../core/01_market_cycle/01_trends_and_channels.md) 与 [趋势延续 Setup](../../core/05_setups/01_trend_continuation.md)。

## 策略页

| 策略 | 针对的回调 / 结构 | 触发类别 | 直接预期 |
| --- | --- | --- | --- |
| [第一次小回调](first_small_pullback.md) | 强趋势（spike 或紧通道）建立后的第一次浅回调 | stop entry 越过回调末端顺势 signal bar | 重新测试刚形成的趋势极值 |
| [第二次恢复信号](second_signal_continuation.md) | 第一次恢复无延伸后的 H2/L2 二次触发 | buy/sell stop 越过第二次 signal bar | 原趋势恢复 |
| [三推楔形回调](wedge_pullback_continuation.md) | 反趋势回调形成三推，上层趋势完整 | 顺势第一个信号 | 原趋势恢复 |
| [双测试旗形](double_flag_continuation.md) | 回调两次测试近似低位/高位（含 micro double） | 双测试后的恢复触发 | 原趋势恢复 |
| [均线缺口回调](moving_average_gap_bar.md) | 三类 moving-average gap bar 语境 | stop entry 越过 MAG bar 信号极值 | 测试旧趋势极值 |
| [宽通道参与区](broad_channel_buy_zone.md) | 宽通道中最近一腿的下部回调区域 | 参与区内的顺势触发 | 测试最近极值或继续原通道 |

覆盖说明：普通成熟趋势回调中的第一次恢复尝试（H1/L1）不单独设页——H1/L1 只是几何计数，不构成独立策略；短浅的首次回调由 [第一次小回调](first_small_pullback.md) 覆盖，多次尝试由 [第二次恢复信号](second_signal_continuation.md) 处理；回调已经区间化则转入 [区间情景](../range/README.md) 或等待重新建立趋势控制，不再由趋势 H2/L2 页处理。

## 状态检查点（约束，不构成独立策略页）

- **Staircase / shrinking stairs**：回调覆盖前一突破点形成阶梯，说明开放空间关闭、状态向通道或区间移动；阶梯本身不确认 opposite trend。
- **Endless pullback**：回调延长到约 20 根以上时（课程线索，非阈值），停止机械沿用普通短回调假设，并按实际证据重新归类为长回调、反向通道、trading range 或 breakout mode；反向 breakout + follow-through 建立持续控制后才更新为 opposite trend。
- **紧通道寿命检查**：紧通道持续约 20 根后可能进入高潮，顺势追价风险上升；随后约 70% 出现至少约 20 根、两腿的横向至反向调整（主要是 trading range 和 minor reversal，不是 opposite trend）。两个"20 根"都是经验尺度，不是机械阈值。
- **50% 回调参考**：强趋势中回调不足一半即恢复支持趋势方仍强；超过一半且重叠、双边获利增加时才更有力说明趋势质量下降。
- **Trending trading range**：一系列局部区间与短突破逐级迁移；每个局部区间仍按区间双边行为处理。

## 语境先验（绑定事件，不写成胜率）

| 语境 | 先验 |
| --- | --- |
| 紧通道（且没有清楚 MTR 或宽楔形顶/底）第一次逆势反转 | 约 70% 只是 minor reversal（支持先按 pullback 处理） |
| 具有清楚倾斜趋势属性的通道长期演化 | 约 75% 先反向趋势线突破转向区间；约 25% 强同向突破；越平的通道越向 50/50 靠近 |
| 同向通道突破 | 约 75% 在包含该通道的最高适用周期五根内失败（与"最终区间化"是不同分母） |

## 相关来源

- [趋势和通道](../../core/01_market_cycle/01_trends_and_channels.md)
- [市场周期](../../core/01_market_cycle/00_market_cycle.md)
- [趋势延续 Setup](../../core/05_setups/01_trend_continuation.md)
- [H1、H2、L1、L2](../../core/04_patterns/02_h1_h2_l1_l2.md)
