# 什么是 Setup

> **状态：Core / Definition**
>
> 本文是 Setup 的权威定义页，只界定交易命题及其与 Pattern、Trade Plan 的边界。

本目录中的 Setup 家族页说明某类价格行为为何可能成为入场依据。

## Setup 的定义

Setup 是处在具体 Context 中、可以作为放置入场单依据的一组价格行为。它至少包含：

- 当前 market cycle、location 与控制权背景。
- 准备交易的价格行为命题，即 premise。
- 支持该命题的一根或多根 K 线或 pattern。
- 明确方向和可观察的入场触发条件。
- 哪些可观察事实会使 premise 失效，以及该命题直接期待哪类价格运动。

一项实际 Setup 必须有明确触发；本目录的家族原型只规定应回答的触发类别和结构关系，不替具体机会填写 K 线顺序、订单价格或有效期。

一个 wedge、H2 或 double bottom 可以只是 Pattern；只有当交易者说明为什么在当前背景下交易它、准备怎样触发时，它才形成 Setup。涉及的 K 线角色以 [K 线类型](../04_patterns/01_bar_types.md)为准。

## Two Reasons 与证据汇合

Brooks 用“需要两个理由”提醒交易者：孤立的一根 K 线、一个形态名称或一次触及通常不足以承担风险。本仓库把它操作化为 **evidence convergence**：一项可交易 Setup 至少应能说明两个相互补充的理由，而且这些理由应尽量增加不同的信息，而不是把同一价格事实换名后重复计票。

理由通常来自五个维度：

| 维度 | 回答的问题 | 例子 |
| --- | --- | --- |
| Market state | 当前主要是哪种环境？ | trend、trading range、breakout mode |
| Control / pressure | 哪一方正在保持或失去控制？ | Always In、连续强收盘、反方失败 |
| Location | 价格在哪里，前方有没有空间？ | 区间边缘、趋势线、均线、旧极值、突破点 |
| Structure | 当前价格行为怎样组织？ | H2、wedge、double bottom、failed breakout |
| Trigger / response | 哪个事实让候选可以行动，市场怎样回应？ | signal bar、second entry、stop trigger、follow-through、拒绝或重新接受 |

例如“牛趋势仍有控制 + 回调到旧突破点与趋势线汇合区 + H2 stop-entry 触发”包含状态/控制、位置和触发三个层面的支持。相反，`H2 + second entry + H1 失败`可能只是同一段两次尝试的三种说法；`broad channel + trending trading range`也可能是同一结构的两个观察角度。相关或同义标签可以帮助描述，却不能据此伪造额外优势。

两个理由只使候选值得继续评估，不表示它自动具有正期望。理由质量、反方证据、合理 stop、现实 target、成本与 Trader's Equation 仍可能淘汰它。多个支撑阻力对象的汇合边界见[支撑阻力与目标](../02_context/01_support_resistance_targets.md#test-与-confluence)。

上述五维分类、独立性检查和计票边界是仓库为避免重复归因建立的综合；它不把 Brooks 的教学启发式改写成固定评分模型，也不要求每一维都必须出现。

## TRADE / WAIT / REJECT

候选分析允许三个正式结果，而不是识别出 Pattern 后必须产生交易：

- **TRADE**：至少两个相互补充的理由仍有效，明确 trigger 已经出现或订单可按计划等待触发，而且可以建立一致的 stop、target、仓位、management 与正的 Trader's Equation。这里表示候选获准进入完整 Trade Plan 或执行流程，不表示已经成交。
- **WAIT**：premise 仍有可能成立，但缺少独立理由、可观察 trigger、必要 follow-through、清楚 stop / target，或当前证据仍相互冲突。等待必须写明要等什么新事实，不能只是无限延长候选寿命。
- **REJECT**：market state、location、控制权或新证据已经否定 premise，或者合理 stop、现实 target、成本和剩余时间使 Trader's Equation 不成立。之后若市场出现新结构，必须作为新候选重新评估。

区间中部、barbwire、目标空间不足、只能靠重复计票凑理由，以及无法定义结构失效点，都是常见的 WAIT / REJECT 语境。选择 WAIT 或 REJECT 是完成分析，不是遗漏交易。

## Setup 不等于完整交易

Setup 回答“在什么背景下，准备交易什么价格行为、怎样触发，以及什么事实会使命题失效”。Setup 家族可以说明 stop 需要锚定哪类结构和直接期待哪类结果，但不独自固定最终 protective-stop 价格、实际退出价格、position size、scalp/swing 方案或成交后管理。

这些决定可能反过来淘汰一个 Setup：如果合理 stop 太远、现实 target 太近，或概率不足以补偿风险，那么候选仍然存在，但不应形成实际交易。完整闭环由 [Trade Plan](../06_trade_plan_and_management/00_trade_plan.md) 定义，数学约束由 [Trader's Equation](../00_method/01_probability_risk_reward.md) 定义。

## 三层边界

下面的 `Pattern → Setup → Trade Plan` 是仓库为消除职责重叠建立的组织模型，不是 Brooks 官方给出的固定三层分类。各层中的价格行为关系由来源支持；层名之间的权限边界属于仓库综合。

| 层次 | 回答的问题 | 不负责 |
| --- | --- | --- |
| Pattern | 看到了什么价格行为？ | 给出交易许可 |
| Setup | 为什么在这里交易、怎样触发、什么使 premise 失效？ | 固化最终订单价格、仓位与完整管理 |
| Trade Plan | 用哪套 entry、stop、target、仓位和 management 执行？ | 重新定义 Pattern 或 Context |

## Setup 家族不是穷尽分类

本目录用趋势延续、突破延续、交易区间 fade、MTR 和逆势修正 scalp 比较不同交易命题。这些是组织核心差异的示例家族，不是所有 Setup 的固定清单。

Second entry 和 trap 描述触发顺序与失败机制，必须服务于某个上层交易命题，因此归入[接受与订单逻辑专题](../03_acceptance_and_order_logic/03_second_entries_and_traps.md)，不与其他 Setup 家族并列。

## 相关来源

相关来源见 [`reference/official_sources.md`](../../reference/official_sources.md) 中的 `SRC-GLOSSARY`、`SRC-MANUAL`、`SRC-10-PATTERNS`、`SRC-STOP-ORDERS`、`SRC-RISK-113`、`SRC-BOOK-TR`（Ch26）、`SRC-COURSE-01-36`（课程 08D、13A–13C、21A–21D、30A–30E）与 `SRC-COURSE-37-52`（课程 37A–37B、49A–49E）。
