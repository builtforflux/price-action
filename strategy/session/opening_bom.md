# Opening BOM（开盘突破模式）

> **状态：Strategy / Application（覆盖层页，不建立新家族）**

## 覆盖内容

开盘后价格对首根 K 线两侧先后进行测试和反转，形成早期双向候选区间：边界随早期新高、新低和失败尝试更新，不由固定根数单独定义。这是 core 对 Opening BOM 的操作性收窄子型（课程用法更宽泛）。

## 叠加规则

- 尚未突破时按 trading-range / breakout-mode 逻辑处理：边缘未获接受的测试按 [区间 fade](../range/README.md) 家族，压缩等待按 [压缩结构突破](../breakout/compression_breakout_mode.md)；
- 只有强突破和跟进才切换为顺势，按 [突破延续](../breakout/README.md) 家族；
- 双向候选可以提前挂两套计划，但必须分别计算各自的 entry、stop、target 与 Trader's Equation；
- 未突破前不预设方向；首次越界只是 breakout attempt。

## 与 first-18 / first swing 的边界

- First swing 是描述性阶段（终点常事后才清楚），不能实时假装存在精确结束 K 线；
- First-18-bar heuristic 是课程对相应日内图表的近似成熟度提示，不是硬阈值；
- 需要固定 opening range 的研究必须观察前声明窗口来源（仓库预设窗口是可复现 schema，不宣称等同 Brooks 官方概念）。

## 状态更新（不是失效）

- **单方向突破候选失效**：某方向越界后无跟进并回到候选区间，该方向候选结束；另一方向仍可保持候选；
- **Opening BOM 整体结束**：某方向获得接受的突破形成方向控制后，BOM 覆盖结束，转入趋势/突破管理（见 [突破延续](../breakout/README.md)）；
- **价格重新进入候选区间**通常继续支持 BOM 的双向候选状态，不构成覆盖层失效。

## 相关来源

- [周期与时段 Context](../../core/02_context/02_time_and_timeframes.md#开盘概念的分层)
- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md)
