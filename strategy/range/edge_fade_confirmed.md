# 边缘确认 fade（确认型 stop entry）

> **状态：Strategy / Application**
>
> 本文把区间 fade 命题实例化为"等待边缘突破失败后再入场"；它不生成具体订单参数。

## 交易命题

成熟区间测试或短暂跌破下边缘（做多）/升破上边缘（做空），突破尝试缺乏跟进或重新进入旧区域，反向触发后价格回到区间内部价值区域。

失败突破回归是本家族下以"越界—回归"为背景的具名子型，见 [失败突破回归](failed_breakout_return.md)。

## 情景判定

- 区间已由多次双向测试和重叠建立；
- entry 位于边缘附近而非中部；
- 突破方未获得接受（无跟进、快速回区、反向 K 线出现）；
- 到区间内部现实目标仍有空间。

## 触发类别

确认型 stop entry：等待突破尝试失败、价格重新进入区间并形成反向触发（例如 H2/L2 或其他反转结构）。Double bottom/top、wedge 或 failed breakout 只描述局部结构，不能替代区间成熟度等条件。

## 失效与 Stop 锚点

- 价格离开边缘后形成足够强的向下/向上 breakout；
- 突破后出现持续跟进；
- 再次跌破失败极值（底部做多）或再次升破失败极值（顶部做空）并在区间外获得接受。

单次轻微越界或只有普通强外观的一根 K 线通常不足以推翻成熟区间的 fade 先验；但异常强的反向 breakout 本身就可以要求先退出。

Stop 锚点类别：failed-breakout 完整极值外（只有在再次越过它足以证明突破方向重新获得接受时）；必须容许正常边缘 overshoot。更远 catastrophe stop 只能作为后备保护，不能替代对区间外 acceptance 的判断。

## 目标与管理

核心结果是 buy low, sell high, scalp：从区间边缘回到内部价值区域。Midpoint、均线、opening price、前 swing 和上/下半区都可能是现实目标；是否争取另一侧边缘取决于区间宽度、内部障碍和原管理方案。管理：默认按 scalp 管理内部回归目标；边缘被有效突破并获接受时按 premise 变化退出；时段尾段剩余时间不足时，不继续等待均值回归。

## 常见误读

- 在仍未成熟的暂停区或区间中部做 fade；
- 看到强边缘腿就认定区间必然突破或必然反转；
- 忽略合理 stop 可能远于视觉上的区间边缘；
- 紧区间没有扣除成本后的 scalp 空间，仍强行交易。

## 相关来源

- [交易区间 Fade Setup](../../core/05_setups/03_trading_range_fade.md)
- [交易区间](../../core/01_market_cycle/02_trading_ranges.md)
- [Stop 入场与保护性 Stop](../../core/03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md)
