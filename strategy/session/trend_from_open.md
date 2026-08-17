# 开盘趋势（Trend from the Open）

> **状态：Strategy / Application（覆盖层页，不建立新家族）**

## 覆盖内容

开盘后很快形成方向，初始极值在随后许多根中保持且没有真正 pullback。它比普通 trend day 更强调趋势从 session 开始阶段形成。

## 叠加规则

- 第一次可交易回调后的顺势恢复按 [趋势延续](../trend/README.md) 家族：符合强趋势首次浅回调时使用[第一次小回调](../trend/first_small_pullback.md)，否则仍完整满足趋势延续母命题时使用[普通趋势回调](../trend/pullback_continuation.md)；
- 开盘强突破的收盘跟随按 [突破延续](../breakout/README.md) 家族（[收盘跟随](../breakout/buy_sell_the_close.md)）；
- 未出现合格回调时，不因开盘强势机械追价；理想价格不出现时采用"小仓、宽结构 stop"的预设计参与，须满足正 Trader's Equation（见 [风险与心理纪律](../../core/06_trade_plan_and_management/03_risk_psychology.md)）；
- 开盘趋势中的第一次回调属于趋势延续语境，不重复制造阶段转换。

## 失效

- 开盘初始极值被收回并获反向接受；
- 早段快速定价后转入区间，按区间逻辑重新判断。

## 相关来源

- [周期与时段 Context](../../core/02_context/02_time_and_timeframes.md#开盘概念的分层)
- [趋势延续 Setup](../../core/05_setups/01_trend_continuation.md)
