# 开盘区间突破（Opening-Range Breakout）

> **状态：Strategy / Application**
>
> 本文把突破命题实例化为离开明确声明的开盘范围；它不生成具体订单参数或固定窗口。

## 交易命题

价格离开当前计划明确声明的 opening-range 边界，首先只构成 breakout event / attempt；接受证据成立（至少一根完成 K 线收在边界外，且出现沿突破方向的跟进，或突破点未被快速收回；若发生回踩，守住属于额外证据）后，按突破延续处理。

## 边界来源必须声明

记录时必须注明 opening-range 边界来自哪一项：

- **Opening BOM 动态边界**：首根 K 线之后，价格对首根两侧先后测试和反转形成的早期双向候选区间；边界随新高、新低和失败尝试更新，不由固定根数单独定义；
- **First-18-bar range**：课程对相应日内图表的前 18 根高低范围的近似成熟度提示，是启发式不是硬阈值；
- **仓库预设窗口**：观察前明确根数或时间窗口的内部可复现 schema，不宣称等同于 Brooks 官方概念；
- **其他观察前显式声明的来源**。

完整分层见 [周期与时段 Context](../../core/02_context/02_time_and_timeframes.md#开盘概念的分层)。

## 触发类别

越界事件 + 接受证据：强突破收盘、follow-through、回踩守住。单次刺穿不够。

## 失效

- 价格快速回到开盘范围并获反向接受；
- 未突破前按 trading-range / breakout-mode 逻辑处理，只有强突破和跟进才切换为顺势。

Stop 锚点类别：足以否定"边界外新价格获接受"的结构外——通常是突破 leg 结构外，或价格重新进入开盘范围并获反向跟进的位置外。

## 目标与管理

开盘量度（范围高度投射）或前高前低等 magnet；时段结束时剩余时间不足会压缩新 swing 的目标可达性。管理：scalp 或 swing 取决于突破强度与剩余时间；回踩正常波动允许，重新进入开盘范围并获接受时按 premise 变化退出。

## 常见误读

- 把 first swing 或 first-18 heuristic 当成可精确预知的固定窗口；
- 单次刺穿就当突破；
- 盘中用最终 day type 回填判断。

## 相关来源

- [周期与时段 Context](../../core/02_context/02_time_and_timeframes.md)
- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md)
- [缺口](../../core/04_patterns/07_gaps.md)
