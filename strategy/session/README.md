# 时段覆盖层（Session）

> **状态：Strategy / Index**
>
> 本页说明时段覆盖层的职责：它是加在四个情景之上的约束层，不是独立情景，也不建立新家族。

## 定位

Core 的 [周期与时段 Context](../../core/02_context/02_time_and_timeframes.md) 定义时段如何影响 context：开盘常有快速定价与突破尝试；完成大运动后的中段更可能双边交易；临近结束时剩余时间可能不足以支持新 swing。本目录把这些影响实例化为覆盖层：只增加候选起点、最晚入场、目标可达性与强制退出约束，不替代任何策略页的 premise。

使用时先判断当前时段属于哪一阶段，再叠加到已选情景策略上。同一底层机会发生覆盖、冲突或过期时，以时段约束为准并更新 Trade Plan。

## 页面

| 页面 | 覆盖内容 |
| --- | --- |
| [Opening BOM](opening_bom.md) | 开盘首根两侧测试与反转形成的早期双向候选区间 |
| [Opening Reversal](opening_reversal.md) | 早段初始方向在已知位置附近失去接受后的反向路径 |
| [Trend from the open](trend_from_open.md) | 开盘即趋势时，第一次可交易回调的顺势恢复 |
| [尾盘时间风险](late_session_time_risk.md) | 剩余时间不足对 stop、limit、scale-in 与新 swing 的约束 |

## 边界

- 时段页不定义新的最低概念；Opening BOM、first swing、first-18 heuristic、Opening Reversal 的边界全部以 core 为权威；
- 盘中只能描述截至当时的状态；最终 day type 是事后标签，不能反向参与候选与入场判断；
- 跨 session 持仓或不使用日内结算边界的方案，按自己的持仓期限重新定义时间风险，本覆盖层不适用；
- 具体"多早/多晚"随品种、session 和 bar interval 校准，不设跨市场硬分钟数。

## 相关来源

- [周期与时段 Context](../../core/02_context/02_time_and_timeframes.md)
