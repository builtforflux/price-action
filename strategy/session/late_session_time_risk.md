# 尾盘时间风险（Late-Session Time Risk）

> **状态：Strategy / Application（覆盖层页，不建立新家族）**

## 覆盖内容

接近 session 结束时，剩余时间可能不足以让反转重新测试 entry 或让新 swing 到达远端目标；同一反向证据因此可能要求更快降低日内风险。这只适用于不准备跨 session 持有的计划。

## 叠加规则

- 早段可行的宽 protective stop、逆向 limit entry 或 scale-in 可能依赖价格有足够时间回到成本区；进入尾段后该前提可能已消失；
- 不能因价格 stop 尚未触发就忽略收盘前被迫退出的路径风险，也不能继续加仓等待已经缺少实现时间的均值回归；
- 尾段才由反转形成的弱 channel 更可能只是 trading range 的一条腿；除非随后出现清楚突破、跟进和足够目标空间，否则不能直接借用较早形成趋势通道的延续假设；
- 新 swing 候选在剩余时间不足时降级为 scalp 或放弃；到达重要 target、follow-through 消失或 premise 被强反向证据否定时，按原管理方式处理。

## 失效

- 计划允许跨 session 或全天候持有：按自己的持仓期限重新定义时间风险，本页约束不适用。

## 相关来源

- [周期与时段 Context](../../core/02_context/02_time_and_timeframes.md#时段如何影响-context)
- [Scalp 与 Swing](../../core/06_trade_plan_and_management/01_scalp_vs_swing.md)
