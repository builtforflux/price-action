# 交易区间情景

> **状态：Strategy / Index**
>
> 本页说明交易区间情景下各策略命题的职责与文件入口。

## 情景判定

交易区间情景要求：

- 区间已经由多次双向测试和重叠建立（成熟区间），多空双方都能赚钱；
- entry 位于边缘附近而非中部；
- 边缘突破尝试未被接受；
- 到区间内部现实目标仍有空间。

完整定义见 [交易区间](../../core/01_market_cycle/02_trading_ranges.md) 与 [交易区间 Fade Setup](../../core/05_setups/03_trading_range_fade.md)。

## 策略页

| 策略 | 进入方式 | 触发类别 | 直接预期 |
| --- | --- | --- | --- |
| [边缘确认 fade](edge_fade_confirmed.md) | 等待突破尝试失败并形成反向触发 | 确认型 stop entry | 回到区间内部价值区域 |
| [边缘限价探针与预设加仓](edge_fade_limit_scalein.md) | 更好价格换更少确认 | limit entry / scale-in | 回到区间内部价值区域 |
| [失败突破回归](failed_breakout_return.md) | 越界后缺乏跟进、重新进入旧区域 | 反向触发或真空 fade | 回到区间内部价值区域 |
| [区间内第二次信号](edge_second_signal.md) | 方向指向区间内部的 H2/L2 或边缘双测试/三推 | stop entry | 回到区间内部价值区域 |

## 回避规则（约束，不构成独立策略页）

- **区间中部**：中间三分之一通常没有优势，尤其避免追随普通信号；必须堆很多理由才能证明中部交易成立时，通常说明交易不够清晰。
- **Barbwire / TTR**：三根以上大量重叠、带显著影线且至少一根 doji 的紧密区间，信号质量低，没有足够目标空间和跟进；经验不足的交易者更适合等待市场脱离。
- **紧区间**：扣除成本后没有 scalp 空间时，多数交易者应等待 breakout，而不是用加仓制造空间。
- **强区间腿**：第一腿强不等于第二腿承诺；若边界未被真正突破并守住，所谓第二腿可能只是测试边界的最后一段并形成追随者陷阱。

## 语境先验（绑定事件，不写成胜率）

| 语境 | 先验 |
| --- | --- |
| 普通区间内单次突破尝试 | 约 80% 失败 |
| 成熟区间进入 breakout mode（前序趋势影响衰减、双向 swing setup 并存） | 双向约 50/50 |
| 强腿后的第二腿 | 不保证；先确认是否真正离开区间并在外部获得接受 |

## 相关来源

- [交易区间](../../core/01_market_cycle/02_trading_ranges.md)
- [交易区间 Fade Setup](../../core/05_setups/03_trading_range_fade.md)
- [限价单市场](../../core/03_acceptance_and_order_logic/02_limit_order_market.md)
- [支撑阻力与目标](../../core/02_context/01_support_resistance_targets.md)
