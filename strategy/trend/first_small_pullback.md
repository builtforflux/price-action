# 强趋势第一次小回调

> **状态：Strategy / Application**
>
> 本文把趋势延续命题实例化为"强趋势建立后的第一次浅回调"；它不生成具体订单参数。

## 交易命题

强趋势（breakout phase 或 tight channel）刚刚建立，第一次获利了结或反方尝试只形成短而浅的停顿；原趋势随后恢复并重新测试刚形成的趋势极值。

## 情景判定

- 前段是已形成方向控制的 breakout phase（spike）或 tight channel；
- 当前是趋势建立后的第一次可识别回调（bar pullback 或 pause bar 均可开始计数；同根两者同时成立只计一根）；
- 回调浅：典型 1—4 根（许多强例只有 1—3 根），重叠少，常保留缺口或近似缺口；
- 主要 higher low / lower high 未被破坏；
- 不是宽通道、成熟区间或已覆盖前一突破点的 staircase。

小回调趋势不要求每根 K 线都有大实体；关键是平均回调相对趋势较小。定义见 [趋势和通道](../../core/01_market_cycle/01_trends_and_channels.md#small-pullback-trend-和-micro-channel)。

## 触发类别

回调末端出现方向清晰、收盘较强的顺势 signal bar（core 对 signal bar 不设固定半幅阈值，收盘质量须服从 context），用 stop entry 越过其高点（牛）或低点（熊）。Micro channel 或强 spike 中理想回调可能不出现；若采用"小仓、宽结构 stop"的预设计早期参与，必须满足 [风险与心理纪律](../../core/06_trade_plan_and_management/03_risk_psychology.md) 中正 Trader's Equation 的前提，不能把焦虑当入场依据。

## 失效与 Stop 锚点

- 主要结构被反向有效突破（牛：major higher low 被向下跌破；熊：major lower high 被向上突破）；
- 回调已变成连续双向重叠的局部交易区间或宽通道；
- 反向运动获得足以改变 market-cycle 判断的跟进。

Stop 锚点类别：完整回调极值外，或足以否定趋势 premise 的主要摆动点外。Signal bar 另一端只有在同时就是完整 premise 失效边界时才足够作为 stop；合理 stop 更远时应调整仓位或放弃，不能把 stop 塞进正常回调。

## 目标与管理

直接预期是测试回调前记录的最近趋势极值；可能按 scalp 管理，趋势仍强且空间足够时支持 swing。Measured move 只有当前走势另有清楚的 breakout leg、旗形高度或 Leg 1 = Leg 2 时才加入。

## 语境数字

- small-pullback 的 1—4 根是课程典型语境（许多强例只有 1—3 根），不是硬阈值，也不构成订单有效期；回调是否仍可等待由结构失效与目标空间决定。
- 强控制环境中理想价格可能不出现；第一笔逆势交易通常危险。

## 常见误读

- 只看到一根大 K 线就宣称强趋势成立；
- 把更深的后续回调硬当成"第一次"小回调；
- 在宽通道边缘追随第一次信号；
- 因害怕错过而追单、缩小 stop 或更换目标。

## 相关来源

- [趋势和通道](../../core/01_market_cycle/01_trends_and_channels.md)
- [趋势延续 Setup](../../core/05_setups/01_trend_continuation.md)
- [K 线类型](../../core/04_patterns/01_bar_types.md)
- [Stop 入场与保护性 Stop](../../core/03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md)
