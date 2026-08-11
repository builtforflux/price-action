# 突破情景

> **状态：Strategy / Index**
>
> 本页说明突破情景下各策略命题的职责与文件入口。

## 情景判定

突破情景要求价格越过清楚旧边界（前高低、区间边界、趋势线、通道线等），且新价格**获得接受**：至少一根完成 K 线收在边界外，且随后出现沿突破方向的跟进，或突破点未被快速收回。回踩守住是额外证据，不是接受成立的必要步骤。单次越界只是 breakout attempt，不构成交易理由。

完整定义见 [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md) 与 [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md)。

## 策略页

| 策略 | 针对的风险承担时点 / 结构 | 触发类别 | 直接预期 |
| --- | --- | --- | --- |
| [收盘跟随](buy_sell_the_close.md) | 强突破的顺势收盘（预判版与确认版） | 收盘附近承担风险 | 第二腿或量度目标 |
| [突破回踩](breakout_pullback_test.md) | 突破获接受后的回调/回测守住旧边界 | 回踩后的重新触发 | 第二腿或量度目标 |
| [失败再失败](failed_failure_continuation.md) | 首破失败→反向失败→原方向再次突破 | 第二次原方向触发 | 第二腿或量度目标 |
| [量度目标构造](measured_move_breakout.md) | 目标构造页（非独立策略）：供突破/趋势/反转策略引用 | 随承载它的策略页 | 区间高度 / breakout height / Leg 1 = Leg 2 |
| [压缩结构突破](compression_breakout_mode.md) | triangle、ii/ioi/oo 等 breakout mode 候选 | 等待市场表态后触发 | 突破方向 + follow-through |
| [开盘区间突破](opening_range_breakout.md) | 离开明确声明的 opening-range 边界 | 越界事件 + 接受证据 | 开盘量度或延续 |

## 状态检查点（约束，不构成独立策略页）

- **三层粒度**：breakout event / attempt、接受证据累积、breakout phase（spike）必须分开；"获接受"是证据状态，不给交易许可，也不要求先回踩。
- **Surprise 与惯性**：强且获接受的突破常构成 surprise，随后市场往往还会尝试第二腿；这只是概率倾向，不保证直线延伸。
- **第二腿陷阱**：第二腿发生在旧交易区间内部时，不能因运动强就借用已获接受突破的延续逻辑。
- **强反向突破**：可以同时完成一个 MTR 的确认；两类标签不互斥，MTR 解释旧趋势失控，本类解释新方向在边界外获接受。

## 语境先验（绑定事件，不写成胜率）

| 语境 | 先验 |
| --- | --- |
| 普通交易区间内单次突破尝试 | 约 80% 失败 |
| 成熟区间进入 breakout mode | 双向约 50/50（方向不确定，不代表两侧期望相同） |
| Triangle 突破方向 | 约 50/50，且首次突破经常失败 |
| 同向通道突破 | 约 75% 在包含该通道的最高适用周期五根内失败 |

## 相关来源

- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md)
- [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md)
- [接受、失望与失败证据](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md)
- [支撑阻力与目标](../../core/02_context/01_support_resistance_targets.md)
