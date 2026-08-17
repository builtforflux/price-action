# 边缘限价探针与预设加仓（LOM）

> **状态：Strategy / Application**
>
> 本文把区间 fade 命题实例化为限价单环境中的探针与分批参与；它不生成具体订单参数。

## 交易命题

本页属于区间 fade 家族，premise 限定在成熟区间边缘：双边限价行为使交易者可以在价格朝暂时不利方向移动时用逆向 limit entry 参与，并管理分批风险，从价格回到区间内部的运动中获利。LOM 行为环境本身也出现在宽通道和弱趋势（core 定义），但那些语境的 premise 分别继承趋势延续（见 [宽通道参与区](../trend/broad_channel_buy_zone.md)）或按实际 market-cycle 重新归类，不能自动继承区间 fade 的失效与目标。

## 适用情景与路由

- 区间已经成熟，当前位于清楚边缘而非中部；
- 双边限价行为仍占主导，边缘突破尚未获得接受；
- 计划能容许正常 overshoot，且全部预设层到共同 stop 的总风险在上限内；
- 若状态属于宽通道或弱趋势，路由到对应趋势 premise；若区间外突破获接受，路由到突破策略而不是继续加仓。

## 触发类别

- **Limit probe**：在 K 线上方卖、下方买（sell above / buy below），用更好价格交换更少确认，通常必须容许更深 overshoot；
- **预先设计的 scale-in**：层数、间距、共同 stop 与全部计划数量的总风险在第一笔 entry 前确定。

完整数量与风险数学见 [加仓与减仓](../../core/06_trade_plan_and_management/02_scaling_in_out.md)。

## Premise 失效

- 成功突破使区间 fade 失效；区间另一侧形成获接受的 breakout 后，原 fade premise 已结束；
- 区间外获得接受并持续跟进；
- 原 premise 改变时继续加仓不再由原计划支持。

## Protective Stop 锚点

计划中最外侧、足以否定区间 fade premise 的共同结构 stop。更远 catastrophe stop 必须单独预算，不能替代对区间外 acceptance 的判断；合理 stop 要容许正常边缘 overshoot。

## 直接预期与目标

直接预期是回到区间内部价值区域，例如 midpoint、均线、opening price 或前 swing。紧区间若高度不足以支持扣除成本后的 scalp，应等待 breakout，不能用加仓制造空间。

## 管理边界

全部计划数量按共同 stop 统一预算，并按 scalp 管理内部回归目标。成功突破获接受时按 premise 变化退出，不继续完成剩余层；未实现浮盈不能作为放宽 stop 的理由（OPM 纪律）。

## 常见误读

- 把限价入场当成亏损后无上限摊平；
- 在趋势环境里逆势 buy below 或 sell above；
- 只因价格"便宜"或"贵"就入场；
- 忽略成功突破会让区间 fade 失效。

## 相关来源

- [限价单市场](../../core/03_acceptance_and_order_logic/02_limit_order_market.md)
- [加仓与减仓](../../core/06_trade_plan_and_management/02_scaling_in_out.md)
- [交易区间 Fade Setup](../../core/05_setups/03_trading_range_fade.md)
