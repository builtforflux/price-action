# 支撑阻力与目标

> **状态：Core / Definition**
>
> 本文界定核心概念；价格行为结论由本页、相关专题与来源共同支持。

## 它解决什么问题

目标和支撑阻力决定交易是否有足够空间。方向判断正确但目标太近，仍可能不是好交易。

市场不断上下测试，寻找“多远算太远”。这些测试留下的区域会成为支撑阻力和目标，而不是精确到一跳的固定线。

在当前时点，support 位于现价下方，是下跌可能停顿或反转的候选区域；resistance 位于现价上方，是上涨可能停顿或反转的候选区域。同一价格区被有效穿越后可以交换角色，因此名称描述它相对当前价格和当前运动的功能，不是永久属性。触及候选区域不保证反转，强趋势也可能直接穿越较小支撑阻力。

## 常见目标

常见 profit targets 和 magnets 包括：

- 前高和前低。
- 日内高低点。
- 昨日高低点。
- 当时已经可见的日、周、月 open / high / low / close，例如已完成周期的 OHLC，以及当前周期已经形成的 open、high 和 low；尚未形成的当前周期 close 不能事先当成固定价位。
- 交易区间中部公平区域和另一侧边缘；具体退出点由当前计划决定。
- 突破点回探。
- 合理 entry、关键 signal close、最高或最低收盘附近的测试区域；失望交易者可能在回测时寻求保本或小亏退出。
- 大整数位。
- 均线。
- 趋势线和通道线。
- 相关 gap 的边界、旧价格区域和回补路径。
- 量度目标。

目标是区域，不是保证。将区域用于实际 Trade Plan 时，必须另行声明哪个边界算目标到达、图表触及是否足够、是否要求账户成交以及对应退出数量；这些结果口径见[从 Setup 到交易计划](../06_trade_plan_and_management/00_trade_plan.md#trade-plan-的定义)。

Entry price 成为 magnet 只说明已有参与者可能关注该区域，不保证市场一定回测，也不提供统一的“一至三根或二十根”期限。等待回测必须服从 active protective stop、原 premise、成本和剩余时间，不能把保本愿望当作目标可达性证据。

使用 gap 作为目标时，必须先写明比较对象和哪一个边界才算进入或关闭。Gap 被测试可以削弱原方向的强度证据，但“缺口迟早回补”不是目标可达性依据；仍要检查控制权、路径障碍和剩余时间。

## Test 与 Confluence

`Test` 只表示价格接近、触及或重新访问一个已有价格关系；它不自行说明该位置会守住、突破或反转。为避免把“到达位置”提前写成“测试成功”，按以下顺序记录：

```text
Approach -> Touch / Overshoot -> Reaction -> Follow-through / Acceptance
```

- **Approach**：价格正在接近候选区域，尚未触及。
- **Touch / Overshoot**：价格触及或短暂越过区域，只确认 test event 已经发生。
- **Reaction**：出现停顿、反向 K 线、拒绝或加速，但结果仍可能缺少延续。
- **Follow-through / Acceptance**：后续价格支持拒绝、守住或在另一侧接受，才让测试结果获得更多确认。

因此，测试均线不自动反转，测试旧高不自动形成可交易双顶，回踩突破点也不自动证明突破成功；到达 measured-move target 同样只说明目标被测试，不能单独授权逆势交易。具体接受、失望和失败边界见[接受、失望与失败证据](../03_acceptance_and_order_logic/01_acceptance_and_failure.md)。

多个相对独立的支撑阻力对象在同一区域交汇，可以形成 `confluence`；Brooks 书中也用 `Dueling Lines` 描述 pullback 同时测试两条重要线或价格关系的情形。例如趋势线与 pullback channel line、均线与旧 swing、突破点与区间边缘在同一区域相遇。汇合可以增强 location 理由，但位置仍须结合 reaction、trigger、follow-through 和目标空间，不能单独生成 Setup。

线条或名称的数量不等于独立理由的数量。两条线若由同一组 swing 推导，或“旧高”“区间上沿”“double-top 区域”只是同一价格事实的不同标签，应视为高度相关证据；只有新增了不同价格关系或观察维度的汇合，才真正增加信息。理由独立性的完整规则见[什么是 Setup](../05_setups/00_what_is_a_setup.md#two-reasons-与证据汇合)。

## 量度目标

Measured move 用已经形成的结构估算下一段运动可能测试的区域，而不是用固定点数预测未来；没有清晰测量结构时，不需要为交易强行构造投射。

常见测算来源包括：

- Leg 1 = Leg 2：第二腿预计与第一腿长度接近。
- 交易区间、开盘区间或其他边界清楚的形态高度，在突破后从突破点投射。
- Breakout height；必须明确量的是哪一个 breakout 结构，不能把任意大 K 线都当成投射基准。
- 在特定结构中，可使用日内 gap 作为运动中间参照；它不是默认测量方式。

使用 measured move 时要同时知道“复制哪段距离”和“从哪里开始投射”。Leg 1 = Leg 2 通常从第二腿起点投射；区间/形态高度通常从突破点投射。Measuring gap 是最终带来 measured move 的 breakout，不等于事前已知的运动中点。

Measured move 是近似等距关系，没有一套跨所有图表唯一的端点算法。常见构造可以写成：

```text
Leg 1 = Leg 2：第一腿 A -> B，第二腿起点 C，目标 = C + (B - A)
区间 / 形态高度：H = 上边界 - 下边界
  向上突破目标 = 上边界 + H
  向下突破目标 = 下边界 - H
Breakout height（复制当前选定的完整突破段）：Δ = breakout 结束价 - breakout 起始价，目标 = breakout 结束价 + Δ
```

所有端点都必须来自当时可见的同一结构；形态边界倾斜或不规则时，要记录实际采用的价格和时间。Breakout height 必须先固定突破段的起止价格，不能在事后改用另一根 K 线的 close 或 high/low。只有把 gap 明确当作运动中间参考时，gap-based projection 才把仍开放 gap 的中点，或特定案例中靠近运动起点的一侧边缘，当作参考并再投射相同距离；许多 measuring gap 的目标仍来自此前区间/形态高度。实时只能称为候选 measuring gap；是否最终成为 measuring gap 取决于后续延续，而不是名称本身。

量度目标常用于趋势延续、强突破、开盘区间突破和 swing 管理。它也常和前高前低、整数位、大周期支撑阻力重合，形成更明显的 magnet。

它不是入场理由，也不是保证到达。如果到量度目标前已经有更近的前高前低、区间中轴、均线或大周期关键位，交易者仍要先评估这些目标是否会压缩风险回报。

## Setup 决定目标

先确定当前 setup 正在押注哪一种价格运动，再选择相应目标：

- 趋势 flag 可能按 scalp，也可能在强趋势中 swing 到旧极值或其他 magnet。
- 强 breakout 可以使用 breakout height、区间高度或 Leg 1 = Leg 2。
- Trading range 以区间内部的 buy low, sell high, scalp 为主。
- MTR 寻找反向两腿和 swing profit；[TBTL](../06_trade_plan_and_management/01_scalp_vs_swing.md#tbtl-是时间与腿数预期)描述路径而不是价格。

沿交易方向标出 support/resistance 和 magnets，区分路径障碍与准备获利的 target。明显障碍会影响更远目标的到达概率，但不要求在每个较近价位退出；强 trend 或 strong breakout 可以穿越较小障碍，trading range 或弱 channel 则更常使用近目标。

Trader's Equation 使用当前计划真实采用的退出价格和相应到达概率。不能忽略近端障碍而只选择一个与当前 setup 无关的远端投射，也不能把 measured move 当成保证。

## 磁吸目标

价格经常被明显目标吸引，例如前高、前低、区间边缘、量度目标和整数位。Vacuum test 指价格快速接近明显目标，看起来像强趋势，但有时只是目标附近订单集中。

到达目标后，市场可能突破、停顿、回补、失败或进入交易区间。不能因为目标到达就预设反转。

日、周、月 OHLC 也只属于预先标出的候选 magnet / support / resistance。它们不自行生成 entry，也不保证价格会在当前 session 结束前到达。具体交易仍需低周期的突破、反转、跟进或失败证据，并检查路径障碍、剩余时间和真实目标空间；不能因为临近高周期收盘，就把价格会“为了形成某种 K 线”移动到某个价位当成 premise。

## 目标和管理

目标近、概率较高的交易更像 scalp。目标远、需要趋势延伸的交易更像 swing。

入场前需要知道这笔 setup 的 profit target 和管理方式，否则无法判断风险回报。部分止盈需要按仓位比例计算；measured move 是目标候选，不保证到达。

相关来源见 [`reference/official_sources.md`](../../reference/official_sources.md) 中的 `SRC-GLOSSARY`、`SRC-STOP-ORDERS`、`SRC-10-PATTERNS`、`SRC-STRONG-LEGS-2016`、`SRC-BREAKOUTS-2025`、`SRC-LIVE-TR-BO-2021`、`SRC-BOOK-TR`（Ch19、Ch26）、`SRC-COURSE-01-36`（课程 11D、18E p1565–1574、19A–19E、20A–20B、29A–29E、33F、34B）与 `SRC-COURSE-37-52`（课程 40A–40B、42A–42B、48A–48K、52B）。
