# 压缩结构突破（Breakout Mode）

> **状态：Strategy / Application**
>
> 本文把突破命题实例化为压缩/扩张结构中的双向候选等待；它不生成具体订单参数。

## 交易命题

Triangle、ii/ioi/oo、窄幅震荡等压缩结构处于 breakout mode：任一方向突破都可能获得跟进，方向未定。策略不是预测方向，而是等待市场表态：突破是否强、是否有跟进、是否回到压缩区、首次突破是否失败、失败后反向是否更强。

## 情景判定

- 完整 triangle 至少有五次反转（两次 higher low 加一次 lower high 或其镜像）；
- ii / iii 是连续两根/三根内包 K 线；ioi 是 inside-outside-inside；oo 是一根 outside bar 后紧接一根更大的 outside bar；
- 波动压缩很常见，但不是定义本身；
- 强趋势中的 ii 或未成熟压缩可能保留趋势偏置，不能只凭名称断言方向中立。
- Expanding triangle（扩张三角形）是独立区间变体，不属本页收敛压缩结构；其 MTR 候选见 [扩张三角形 MTR 候选](../reversal/expanding_triangle_mtr.md)。

定义见 [Triangles、ii、ioi 和 oo](../../core/04_patterns/06_triangles_ii_ioi_oo.md) 与 [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md#breakout-mode)。

## 触发类别

统一观察顺序：压缩或双边状态 → 实际突破方向与强度 → follow-through → 回踩守住或重新进入原压缩区。双向候选可以提前挂好两套计划，但必须分别计算各自的 entry、stop、target 与 Trader's Equation。

## 失效

- 首次越界后无跟进并回到压缩区，突破尝试失败；
- 重新进入原压缩区后，原方向候选失效；
- 压缩结构被重新接受。

Stop 锚点类别：足以否定该方向候选的结构外——通常是触发 signal bar 极值外，或价格重新进入压缩区并获反向接受的边界外；双向候选必须各自给出自己的 stop 锚点。

## 目标与管理

突破获得接受后，再进入对应突破策略的量度或第二腿目标；首破失败后的反向接受则进入区间 fade 或新突破命题，不能因原 wedge/triangle 名称预设其必然失败或必然延续。管理：方向选择前空仓等待；选定方向后按对应突破策略管理（scalp/swing 由突破强度与目标空间决定）；首破失败后的反向按新命题重新计算 entry、stop 与目标，不沿用原候选。

## 语境数字

- Triangle 突破方向接近 50/50，首次突破经常失败；
- 突破模式的重点是等待市场表态，不保证首破获得接受。

## 常见误读

- 看到任一压缩结构就预设一定有大突破；
- 只登记第一次越界，不登记 follow-through、回踩或重新进入；
- 把 triangle 的 50/50 写成固定胜率或固定方向。

## 相关来源

- [Triangles、ii、ioi 和 oo](../../core/04_patterns/06_triangles_ii_ioi_oo.md)
- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md)
- [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md)
