# 双向突破模式（Breakout Mode）

> **状态：Strategy / Application**
>
> 本文把通用 breakout mode 实例化为双向候选；压缩结构是常见子型，不是唯一成立方式。

## 交易命题

市场处于任一方向突破都可能获得跟进的双向候选状态。策略不是预先猜方向，而是分别准备两套候选，并等待实际突破方向、强度、follow-through、回踩或失败来决定哪一套获得交易资格。

Breakout mode 可以叠加在 trend 或 trading range 上，不是第三种基础状态。Triangle、窄幅震荡、ii/iii、ioi、oo 等压缩结构常见；双方连续反转、双向测试和快速收回形成的非压缩双向候选也可以成立。

## 适用情景与路由

- 当前没有一侧突破已经获得足以排除另一侧候选的持续接受；
- 两个方向各自存在可声明的结构边界、失效事实和现实目标空间；
- 压缩子型中：采用官方 abbreviations 口径时，完整 triangle 至少有五次反转；若采用课程 26A 的腿数口径，则保留“一侧三推且总体至少五腿”并注明观察周期；ii/iii、ioi、oo 按 Core 几何定义记录；
- 非压缩子型中：双方均有实际突破/反转能力，最近单向尝试被快速收回，不能只凭“看起来混乱”命名 BOM；
- 强趋势中的局部 ii 或暂停仍可能保留明显趋势偏置；偏置影响两套方程，但不能抹掉仍有效的另一方向候选。

Expanding triangle 是扩张区间变体；若其尺度和反向压力形成 MTR 候选，使用 [扩张三角形 MTR 候选](../reversal/expanding_triangle_mtr.md)。

## 触发类别

统一观察顺序：双向候选状态 → 实际越界方向与突破质量 → follow-through → 回踩守住或重新进入原区域。两套计划必须分别给出 entry、stop、target 与 Trader's Equation；某一方向只有在自己的可观察触发出现后才获得资格。

## Premise 失效

- 某方向首次越界后无跟进并重新进入原区域：该方向候选失效，另一方向不因此自动触发；
- 某方向获得持续接受并建立控制：Breakout Mode 整体结束，转入该方向的突破/趋势管理；
- 两侧目标空间都不足：NO_TRADE；
- 状态退化为无法声明边界或没有交易空间的 barbwire：等待脱离。

## Protective Stop 锚点

每个方向足以否定该方向候选的结构外，通常是触发结构极值外，或重新进入并反向接受原区域的边界外。不能让两套候选共享一个未经分别验证的 stop。

## 直接预期与目标

压缩高度、清楚 breakout leg、Leg 1 = Leg 2 或其他当时可见结构可以提供目标候选；非压缩 BOM 不因名称自动获得压缩高度投射。

## 管理边界

突破获得接受后，本双向候选状态结束，按对应 breakout continuation 管理；失败后重新运行候选选择，不能机械反手。两套候选不能互借 entry、stop、target 或概率。

## 语境数字与先验

- Triangle 突破方向常接近 50/50，首次突破经常失败；这些数字只属于相应 triangle 语境；
- 通用 Breakout Mode 不保证方向对半，也不保证首破失败。

## 常见误读

- 把 Breakout Mode 等同于低波动压缩；
- 看到任意混乱行情就准备双向交易；
- 首次刺穿即取消另一侧计划并追价；
- 把 triangle 的方向先验复制给全部 BOM。

## 相关来源

- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md#breakout-mode)
- [Triangles、ii、ioi 和 oo](../../core/04_patterns/06_triangles_ii_ioi_oo.md)
- [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md)
- [接受、失望与失败证据](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md)
