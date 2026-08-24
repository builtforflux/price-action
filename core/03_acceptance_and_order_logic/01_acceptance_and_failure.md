# 接受、失望与失败证据

> **状态：Core / Definition**
>
> 本文用可观察的价格行为理解触发后的结果，不要求猜测真实订单簿或参与者身份。

## 触发之后看什么

价格越过关键位置时，可能同时遇到 stop entry、protective stop、limit order 和获利了结。我们无法知道每笔订单来自谁，真正可观察的是市场是否接受新的方向：

- Entry bar 是否有力度。
- 后续是否出现 follow-through。
- 回调是否浅，突破点或关键区域是否守住。
- 反方是否快速收回关键位置。
- 原方向恢复，还是失败后形成反向运动。

触发本身不等于成功，单根强 K 线也不等于持续趋势。

## Follow-through、surprise 和惯性

Follow-through 的最低含义是初始运动之后，后续一根或多根 K 线继续延伸该运动。强收盘、浅回调和反方失败可以作为更广的 acceptance evidence，但不改变这个最低定义。

Surprise 是明显超出交易者预期的强行为。强 surprise 常使错过者追随、站错者退出，因此市场往往还会尝试形成第二腿；这只是概率倾向，不表示价格必须直线延伸。

没有 follow-through 会削弱突破或 setup，但不能仅凭下一根普通回调就宣告失败。

## Disappointment、premise 变化和交易结果

这里的 protective stop 是保护实际持仓的退出 stop；`scalper's profit` 是在 stop 先到之前，价格路径已经提供符合当前语境的合理 scalp 利润机会，完整边界见[Minimum Scalp 与 Scalper's Profit](../06_trade_plan_and_management/01_scalp_vs_swing.md#minimum-scalp-与-scalpers-profit)。它们只界定结果，不提供新的 entry 依据。本节必须结合 [Stop Entry 和 Protective Stop](00_stop_entry_vs_protective_stop.md) 的完整定义理解，不能混用两类 stop。

Brooks glossary 把 **failure (a failed move)** 定义为 protective stop 先于 scalper's profit，或先于交易者 objective 到达；**success** 则表示交易者 objective 先于 protective stop 到达。结合这两个词条，本仓库复核时必须写明正在评价的 move、objective 和 outcome criterion；这是为消除目标歧义采用的记录规则，不是 Brooks 另给的一套 taxonomy。官方词条中的 `or` 不支持再建立“scalper's profit 和 swing objective 都未出现”的更窄 failure 分类，不同的预声明目标口径则可能对同一价格路径给出不同结果。

`Failed breakout`、`failed H2` 或“旧极值测试失败”描述的是某次价格运动未达到预期，不自动表示某位交易者已经触及 protective stop。若把 success / failure 用于一笔实际交易，还必须先确认 actual entry、适用 objective、protective stop 和事件顺序；账户实际 P&L 另由成交、退出、数量和成本决定。

实际交易还要区分三种不同事情：

- **Entry disappointment**：entry 弱、价格暂时没有离开入场区，结果尚未确定。它可能只是正常 pullback。
- **Premise 不再成立**：新的 price action 已经让交易者认为原计划错误，可以在最远 protective stop 触发前退出。
- **Success / failure**：按当前明确声明的 objective 与 protective stop 谁先到达复核；同一路径更换 objective，结果也可能不同。

Trade Plan 的 outcome criterion 负责把上述目标落到可复核事实，而不另造一套 success / failure 术语。二结果计划应记录原 objective 与 protective stop 谁先到达；方向短暂走对或只先获得一个并非原 objective 的 scalper's profit，不自动等于该 objective 成功。若价格先提供 scalper's profit，随后 protective stop 先于 swing objective 到达，应分别记录 `scalper's profit observed` 和“相对于 swing objective 的 failure”。只有预先声明的 scalp outcome criterion 也已满足时，才能另记相对于 scalp objective 的 success；若该 criterion 要求实际成交，图表路径曾提供机会仍不够。

“到达”必须使用 Trade Plan 事先声明的 outcome criterion：价格目标应区分图表触及、按既定执行假设可成交和账户实际成交，目标区域应写明以哪个边界算进入，部分退出应写明对应数量。若同一根回放 K 线同时包含 objective 和 stop，而更低周期、逐笔路径或订单记录无法确定先后，则结果应记为“顺序不明”，不能事后选择更有利的顺序。计划本来包含部分退出、scratch、breakeven 或主动退出时，应按预先写出的互斥结果分别记录，并另记实际退出、数量、成本和 P&L，不能事后硬改成二结果。

Entry disappointment 和 premise 变化描述不同阶段的价格行为，两者都不自动等于 Brooks failure；正常 swing pullback 也不能仅因令人失望就宣告 failure。实际交易的结果复核以 actual entry 已经发生为前提；没有成交的候选只能记录为未触发、过期、拒绝或失效。在 protective stop 前提前退出时，分别记录当时 premise 判断、actual exit 和实际 P&L，不把主动小亏退出改写成 stop-first failure。

### 从失望到退出，以及退出后的重新入场

管理不能只在“继续持有”和“等待最远 stop”之间二选一。实际持仓还应使用[Trade Plan 的三层退出保护](../06_trade_plan_and_management/00_trade_plan.md#三层退出保护)：在场 protective stop 负责最后保护；premise invalidation 通过合理反向结构或足够强的反向动量两类证据路径支持主动退出。普通小反向 K 线仍可能只是正常 pullback，必须按原 Context、管理周期和失效条件判断。

提前退出只表示当前计划不再值得承担风险，不表示原方向永远错误。若反向尝试随后失败、原方向重新获得接受，可以根据新的 trigger 建立新 Trade Plan；原 entry、概率、stop 和目标不能自动复用。

## Trapped traders

课程至少使用两种方向不同的 `trapped` 语言，必须分开：

- **Trapped in a trade**：一方已经实际入场、没有先获得 scalper's profit、仍处于开放亏损，并在反向运动中很可能被迫亏损退出。若反向运动已经迫使他们退出，可以描述为“曾被困并退出”，但不再属于当前开放的 `trapped in a trade` 状态。
- **Trapped out of a trade**：一方因为等待更好价格、止损距离不舒服、过早退出或其他原因没有建立或没有保留原本想要的仓位，随后行情沿该方向快速发展，使其被挡在交易之外。这里没有开放亏损仓位；潜在压力来自追价、回调重新入场或放弃参与，而不是亏损持仓的 protective stop。

`Trapped out` 也不等于“曾 trapped in 后已经止损退出”。前者描述错过或过早离开机会，后者描述一笔实际持仓的历史结果。两种 trapped 叙述都只是订单行为解释模型，必须由价格、可见 entry / stop 区域、follow-through 和目标空间支持，不能声称已经观察到所有参与者的真实仓位。

### Pain Trade

Pain Trade 是一种行为与价格路径模型：当许多交易者已经押注某一方向或等待市场按常见预期行动，行情却沿低预期方向持续扩展时，`trapped in` 一方的退出和 `trapped out` 一方的追入可能共同增加运动压力。这里描述的是从可见价格行为推断的潜在响应，而不是已经看见真实订单、持仓或参与者身份。

Pain Trade 不是新的 Setup，也不是独立的 failure state。实际判断仍回到本页的接受 / 失败框架：是否出现有效突破、follow-through、关键位置守住或快速收回，以及前方是否仍有现实空间。

判断时问：

- 当前讨论的是 `trapped in`、`trapped out`，还是曾被困后已经退出？
- 若为 `trapped in`：是否有足够交易者可能已经入场，且未先获得 scalper's profit、当前仍处于开放亏损？
- 若为 `trapped out`：哪些可见价格行为支持他们曾等待更好价格、过早退出或未能保留仓位？
- 后续运动是否强到足以迫使亏损退出、追价或重新入场？
- 反向运动前方是否有现实空间？

## Failed Failure（运动尝试）

失败的价格运动也可能失败。例如突破后快速收回，但随后原突破方向再次触发并获得强跟进。此时第一次 failed breakout 转成 breakout pullback，逆向交易者反而可能被困。这里描述两次运动尝试的结果，不表示同一笔交易连续两次触及 protective stop。

Failed failure 往往比第一次尝试更可靠，但名称本身仍不能替代 context、follow-through 和目标空间。

相关来源见 [`reference/official_sources.md`](../../reference/official_sources.md) 中的 `SRC-GLOSSARY`、`SRC-STOP-ORDERS`、`SRC-STRONG-LEGS-2016`、`SRC-GOOD-TRADE-2017`、`SRC-COURSE-01-36`（课程 02C、08C–10B、15A–15G、18A–20A、30A–30E、33D、36A–36B）与 `SRC-COURSE-37-52`（课程 40A–42C、49C–51D、52A–52B）。
