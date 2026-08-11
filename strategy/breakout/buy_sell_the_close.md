# 强突破收盘跟随（Buy / Sell The Close）

> **状态：Strategy / Application**
>
> 本文把突破延续命题实例化为强突破阶段在顺势收盘附近承担风险的两个版本；它不生成具体订单参数。

## 交易命题

市场正在或已经接受旧边界外的新价格；在强突破的顺势收盘附近承担风险，期待延续、第二腿或量度目标。Buy The Close 是多头版本，Sell The Close 是空头镜像。

## 两个版本是两份独立 Trade Plan

| 版本 | 承担风险的时点 | 确认程度 | 代价 |
| --- | --- | --- | --- |
| 预判 / 早期版 | 首根足够强的 breakout bar 收盘时，尚无独立 follow-through | 确认较少 | 不能借用后续 acceptance evidence 的概率 |
| 确认版 | 连续强收盘或 follow-through 出现后 | 确认较多 | entry 更差、stop 可能更远、剩余目标更近 |

确认版不能继承早期版更好的价格；早期版不能借用尚未出现的 follow-through 概率。每次参与都只使用承担风险当时可见的证据，重算自己的 entry、结构 stop、剩余 target 和 Trader's Equation。

## 触发类别

收盘或收盘附近的市价参与（早期版：首根强 breakout bar 收盘时；确认版：连续强收盘或 follow-through 后）。突破前/收盘前以 stop entry 在 breakout mode 承担风险属于突破延续 Setup 的预判版本，不在 BTC/STC 的行为定义内，见 [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md#两种风险承担时点)。

## 失效与 Stop 锚点

- 价格明确回到旧区域并在其中获得反向跟进，延续 premise 才失效；单纯回测突破点不构成失败；
- 趋势 K 线缩小、影线和重叠增加、反方 K 线出现、关键收盘持续失去跟进，或价格接近重大目标进入尾段时，应停止机械 BTC 并重新判断阶段（channel、trading range 或 climax / transition）。

Stop 锚点类别：完整 breakout leg 外。

## 目标与管理

强 breakout 才常支持至少第二腿或 measured move；量度对象必须在当时可见并固定。强趋势中若选择按 scalp 很快退出，应事先承认回调可能不给出舒服的重新入场机会——这是强趋势中常让至少部分仓位按 swing 管理的行为理由之一。

## 常见误读

- 把单根顺势收盘当成自动入场；
- 用早期版的价格配合确认版的概率；
- 忽略完整 breakout leg 所要求的真实 stop 距离；
- 为凑 reward/risk 跳过前方强障碍。

## 相关来源

- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md#buy--sell-the-close)
- [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md)
- [风险与心理纪律](../../core/06_trade_plan_and_management/03_risk_psychology.md)
- [概率、风险和回报](../../core/00_method/01_probability_risk_reward.md)
- [BTC/STC 决策协议](../protocols/buy_sell_the_close.md)（版本选择与参数绑定）
