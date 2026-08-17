# 双测试旗形延续（Double Bottom / Top Flag）

> **状态：Strategy / Application**
>
> 本文把趋势延续命题实例化为"回调中的双测试旗形"；它不生成具体订单参数。

## 交易命题

牛趋势中回调两次测试近似低位（double bottom bull flag），或熊趋势中反弹两次测试近似高位（double top bear flag）；第二次测试不能改变原控制，原趋势恢复并获得跟进。

## 适用情景与路由

| 当前控制 | Pullback 测试 | 失败事实 | 延续证据 |
| --- | --- | --- | --- |
| 牛趋势仍偏多 | 回调两次测试近似低位 | 第二次下探没有破坏多头结构 | 多头恢复并获得跟进 |
| 熊趋势仍偏空 | 反弹两次测试近似高位 | 第二次测试不能改变空头控制 | 空头恢复并获得跟进 |

两个测试只需位于近似价格区域，不要求完全相等；定义见 [双顶、双底和旗形变体](../../core/04_patterns/04_double_tops_bottoms.md)。

## 触发类别

双测试后的恢复触发（例如越过两次测试之间的中间 swing 结构），用 stop entry 执行。小型 double bottom 常可理解为 High 2 bull flag，小型 double top 常可理解为 Low 2 bear flag。

## Premise 失效

- 第二次测试破坏原趋势的主要结构；
- 双测试之后出现反向跟进，市场转成 trading range 或反向突破。

## Protective Stop 锚点

两次测试的共同极值外，或足以否定趋势 premise 的结构外。

## 直接预期与目标

直接预期是原趋势恢复并测试旧极值；double flag 名称本身不产生独立量度目标。

## 管理边界

可能按 scalp 管理，趋势仍强且空间足够时支持 swing。微型变体（micro double bottom / top）在 spike 内可承担 one-bar flag 功能；出现在 flag 末端并形成反向证据时路由到反转策略，不能沿用本页管理。

## 常见误读

- 把双测试直接当成反转信号；
- 忽略"第二次测试失败"这个核心事实；
- 把 micro double 在 spike 内和 flag 末端的相反含义混用。

## 相关来源

- [双顶、双底和旗形变体](../../core/04_patterns/04_double_tops_bottoms.md)
- [趋势延续 Setup](../../core/05_setups/01_trend_continuation.md)
- [H1、H2、L1、L2](../../core/04_patterns/02_h1_h2_l1_l2.md)
