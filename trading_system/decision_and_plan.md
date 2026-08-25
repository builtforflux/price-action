# 交易决策与计划

> **状态：Trading System / Decision Contract**

本页规定怎样从 Primary Test 的双向 Opportunity Set 中选择一条 Market Path，并在当前价格下形成 Trade Plan。系统不选择预设策略，也不因识别出 Pattern 就产生交易；只有目标事件、条件概率和当前风险交换一致时，才允许承担风险。

本页首先是完整的内部决策契约，不是盘中默认表单。交易者必须在承担风险前明确所有会改变风险或动作的输入，但只按[总流程的三层使用接口](overall_flow.md#三层使用接口)保存最小决策信息；其余内容可以观察、心中确认或由工具自动计算。

## 一、决策顺序

```text
Frame + Environment + Location + Price Action Now + Active Test
→ 向上 / 向下 / Pending Opportunity Set
→ 候选目标与 Market Paths
→ 独立评价双向路径
→ 条件概率
→ 当前 Entry
→ Invalidation 与 Protective Stop
→ 实际 Reward / Risk / Cost / Time
→ Position Size 与 Management
→ Trader's Equation
→ 执行 / 等待 / 不交易
```

目标必须先于 Entry。先看到 signal bar、突破或其他触发，再寻找远端目标修复 reward/risk，属于反向构造，不得进入计划。

## 二、候选资格

Market Path 进入交易构造前必须具备：

- 来源 Primary Test、边界和当前位置清楚；
- 一个可观察的目标事件和到达口径；
- 观察周期与现实时间范围；
- 到达目标需要出现的价格序列；
- 至少一个能够实质否定该路径的事实；
- 当前最强反路径或反方事实；
- 可匹配的条件概率或诚实的近似概率语言。

缺少目标、失效事实或时间范围时只能等待；合理 Stop 无法定位、目标空间已不足或成本使方程不成立时不交易。

双向考虑不要求为每个方向制造完整 Trade Plan。系统先独立说明向上、向下路径的目标、支持、反方事实与失效条件，并说明测试继续 Pending 的现实方式；明显缺少现实空间、时间或条件的路径只需识别排除原因。只有当前具有可观察 Entry、合理 Stop 和可计算结果的路径进入交易构造。

## 三、证据汇合，而不是理由计数

承担风险前至少能指出两个来源独立、相互补充的支持事实。支持通常来自：

| 维度 | 回答的问题 | 例子 |
| --- | --- | --- |
| 活动结构 | 当前主要怎样运动？ | Trend、Channel、Range、Breakout Mode |
| Pressure / Control | 哪一方正在保持或失去控制？ | 连续强收盘、浅回调、反方失败 |
| 位置与目标 | 价格在哪里，前方是否有现实空间？ | 区间边缘、突破点、旧极值、magnet |
| 测试与次序 | 当前价格怎样组织测试？ | 第二次测试、三推、回踩、failed breakout |
| Trigger / Response | 哪个新事实允许承担风险？ | stop trigger、follow-through、拒绝、重新接受 |

这些维度不是评分器，也不要求全部出现。以下通常只是一份证据：

- H2、Double Bottom、Second Signal 和 H1 失败来自同一两次尝试；
- 同一突破产生的大实体、gap、pressure、control 和 acceptance；
- 同一突破或失败链产生的 disappointment、trapped / Pain Trade 推断和预期退出压力；
- Broad Channel 与 Trending Trading Range 描述同一方向移动；
- 旧高、区间边界、double-top 区域和 measured-move 落在同一价格区域。

独立同向证据通常增强路径，但概率仍由与目标事件匹配的条件规则提供，不能按理由数量制造百分比。一个强反方事实可以覆盖多个弱支持理由。

比较机会时不得只选择裸概率较高或支持名称较多的一侧。相同目标、周期和 horizon 的路径可以比较条件概率；不同目标或 horizon 必须分别构造当前 Entry、Stop、Target、成本和结果方程，再比较完整风险交换。未决、超时、scratch 等结果意味着双向概率不必相加为 `100%`。

## 四、Trigger 与判断时点

Trigger 只说明当前可以用某个价格表达 Market Path，不保证目标实现。计划必须明确 Trigger 是在承担风险前必须完成，还是成交后继续验证。

### Signal bar、chart entry 与 actual fill

- `Prospective signal bar`：仍在形成、可能提供触发依据的 K 线；
- `Signal bar`：完成后为当前路径提供可观察入场依据的 K 线，即使订单最终未触发；
- `Chart entry bar`：图表上既定触发条件第一次被越过或满足的 K 线，不要求账户下单；
- `Actual fill bar`：账户真实获得成交的 K 线。

这些角色可能落在同一根，也可能不同。没有实际成交不能抹去图表触发，没有图表触发也不能从账户意图制造 Pattern 事实。

### Signal-bar 评价

只有结构、位置、目标路径和交易方向已经明确后，才评价 signal bar：

| 观察 | 较强多头表达 | 较强空头表达 |
| --- | --- | --- |
| 位置 | 结构与目标支持向上路径 | 结构与目标支持向下路径 |
| 收盘 | 至少在本根上半部，靠近高点更强 | 至少在本根下半部，靠近低点更强 |
| 反向影线 | 上影较短；反转时下影可表示拒绝 | 下影较短；反转时上影可表示拒绝 |
| 实体 | 多头实体相对较大 | 空头实体相对较大 |
| 相对大小 | 有足够力度，但不使合理 Stop 过远或表现为末端高潮 | 镜像 |

强控制背景可以允许较弱的顺势 signal bar；逆控制方向通常要求更清楚的反转、压力、第二次测试或 follow-through。漂亮外观不能修复错误位置、缺少目标空间或不利交易方程。

### 两个风险承担时点

同一市场路径可以在不同判断时点形成不同 Trade Plan：

| 时点 | 已有证据 | 代价 |
| --- | --- | --- |
| 较早参与 | 结构和触发可定义，但尚无独立跟随 | Entry 较好，条件概率通常较低或更不确定 |
| 等待确认 | entry bar、follow-through、回踩守住或 acceptance 已出现 | 证据增加，但 Entry 更差、Stop 可能更远、剩余 Reward 更近 |

等待确认后必须使用新价格重新计算整份计划，不能继承较早 Entry、较窄 Stop 或尚未出现证据前的方程。

## 五、Entry

Entry 必须定义为可观察条件、订单表达和有效期：

```text
Entry
- 条件：
- 方向：
- 订单类型与价格规则：
- 有效期：
- 过期或取消条件：
- 承担风险前必须看到：
- 成交后预期看到：
- 是否允许在 Trigger 前预先提交条件订单：
```

Market / close order 只能在承担风险前置条件已经成立后提交。Stop / Limit order 可以在 Trigger 或成交前预先提交，但 Trade Plan 必须明确许可，并固定价格规则、有效期、撤单条件和成交后的保护方式；订单一经提交即属于执行状态，不再属于“等待图表确认”。

### Stop entry

Stop entry 用较差价格交换触发确认，常以 signal bar 高低点附近的条件表达。成交后仍要观察 entry-bar 表现、follow-through、触发区域是否守住和分离是否建立；触发本身不证明目标路径成立。Buy stop / sell stop 是入场用途，不是保护性 Stop。

### Limit entry

Limit entry 用更好价格交换更少确认。计划必须明确成交后期待的拒绝、重新进入旧区域、Pressure 变化或其他反应，以及允许这些事实出现的时间。价格 touch / cross 不保证账户全部成交；若计划依赖 scale-in，全部层、总数量、共同 Stop 和总风险必须在第一笔 entry 前确定。

### Market / close entry

强 breakout 中可以在首根强收盘或后续 follow-through 后承担风险。两个时点的证据、价格和剩余空间不同；Buy / Sell The Close 是执行行为，不是独立交易类别。

没有符合当前计划的 Entry 时，不因 FOMO 追入。临时追价改变 Entry、Stop、目标和方程，必须视为新的判断时点并重新构造计划。

## 六、Invalidation 与 Protective Stop

### Invalidation

Invalidation 是新价格事实已经使所选 Market Path 不再成立，例如：

- 原结构关键边界被有效突破并在反侧获得接受；
- 目标所依赖的分离、控制或测试关系被实质否定；
- 强反向 breakout、连续动量或 Always In 切换建立了反路径。

Invalidation 可以在最远 Protective Stop 触发前要求主动退出。普通反色 K 线、正常 pullback 或短暂失望不自动构成 Invalidation。

horizon 结束而目标和失效均未发生时，Market Path 进入 `EXPIRED`，不记为市场事实否定。若目标和失效在同一观察 K 线内且顺序无法确认，记为 `SEQUENCE_UNKNOWN`；它不同于测试仍在进行的 Pending Outcome。

账户预算、成本、Session 持仓限制、基础设施或执行条件可以使当前 Trade Plan 失效，却不改变市场目标是否仍可能发生。Plan invalidation 要求停止新增风险、撤销对应工作订单或按计划收缩风险；只有市场事实或 horizon 才关闭 Market Path。

### Planned 与 Active Protective Stop

- `Planned Protective Stop`：承担风险前确定的价格或价格规则，用于风险、仓位和激活计划；
- `Active Protective Stop`：实际成交后，状态可确认且覆盖实际仓位的在场保护；
- `Trailing Stop`：新结构形成后，只向降低开放风险方向移动的 Active Stop；
- `Catastrophe Backup`：若使用，作为另行预算的更远灾难保护，不能与 Planned / Active Stop 共用同一字段。

合理 Stop 位于真正否定当前路径、同时能够容纳所选周期正常波动的位置。Signal bar 另一端、完整 pullback、major swing 或结构边界都可能合理，取决于当前路径；不能为了漂亮 reward/risk 把 Stop 塞进正常波动。

同一图表可以存在多个合理 Stop 候选，但它们代表不同计划。Stop 较远时缩小仓位、等待更好 Entry 或不交易，不任意缩短结构风险。

## 七、Target 与 Outcome Criterion

Trade Plan 从 Market Path 已经定义的目标事件中选择实际准备兑现的价格和数量：

| 层次 | 职责 |
| --- | --- |
| 候选目标 | 结构可量度后事前生成，用于判断路径空间 |
| 第一现实目标 | Entry 后最近、当前路径确实可能测试的 magnet |
| 主要结构目标 | 所选 Market Path 直接生成的目标事件 |
| 延伸目标 | 只有新突破和跟随继续支持原路径时才启用 |

Outcome Criterion 必须规定：

- 评价哪个 objective；
- 目标是价格还是区域，哪个边界算到达；
- 图表触及是否足够，还是要求按执行假设或账户实际成交；
- 部分退出对应多少数量；
- Stop 与目标在同一回放 K 线内且顺序不明时怎样记录；
- scratch、breakeven、主动退出和时间退出怎样构成互斥结果。

价格曾提供 scalper's profit，不自动等于账户捕获，也不等于 swing objective 成功。不同 objective 可以对同一路径产生不同 success / failure 结果，必须分别记录。

## 八、条件概率

条件规则台账保存可匹配模板；模板中的相对条件只有绑定当前 Market Path 后才能成为可运行的 Rule Match。概率判断格式：

```text
候选规则模板：
已经成立的条件：
目标事件：
观察周期：
时间范围：
判断时点：
适用近似概率：
替代当前判断的新事实：
匹配状态：可运行 / 仅背景 / 字段不完整 / 已被更具体条件替代
```

只有 `可运行` 的当前匹配可以进入 Trader's Equation。模板若缺少当前目标、周期、horizon 或判断时点，只能提供 Context 或概率语言；不能用计划临时选择的远端目标补齐来源规则，也不能把相同方向但不同目标的规则当作更具体替代。

Brooks 教学中的 `likely / probably` 通常表示约 `60%+`，`unlikely` 表示约 `40%-`；它们是近似语言，不是经过统一样本校准的统计模型。

70%–80% 的结构概率只有在当前目标事件、周期、时间范围和条件与原规则完全相同时才能直接使用。结构生命周期概率、突破方向先验、某次目标先于 Stop 的交易概率和基础结构/阶段频率不是同一对象。

无法说明当前路径为什么属于某条规则时，使用诚实的 40%–60% 近似语言或继续等待，不以标签数量制造精度。规则选择与隔离项见[条件规则台账](conditional_rules_registry.md)。

Market Path 概率描述市场目标事件；Trader's Equation 使用的结果概率还必须与当前 Entry、Planned Stop、Targets、退出数量、时间和管理方式相容。市场目标概率不能在没有结果定义的情况下直接当作账户盈利概率。

## 九、Trader's Equation

二结果近似：

```text
成功概率 × Reward
>
失败概率 × Risk + 成本
```

概率、Reward 和 Risk 必须描述同一 Entry、Planned Stop、Target、时间和管理方式。佣金、点差、滑点与异常余量进入真实净结果。

在“赢家 `2R`、失败 `1R`”且暂不计成本的二结果中，正期望要求成功概率大于 `1/3`；这不表示任何 `2R` 远端目标都合理。约 40% 的较早或较低概率路径通常需要更大现实 Reward，约 60% 的条件可以在约 1R 时仍可能成立，但均须使用当前实际输入。

计划包含部分退出、scale-in、scratch 或主动退出时，应列出互斥结果 `i`：

```text
Σ [P(result_i) × payoff_i] - cost > 0
```

没有可靠样本时不构造伪精确的完整概率树；至少保证所有计划内的重要结果没有被二结果公式隐藏。

## 十、四种风险

| 风险 | 含义 | 使用时点 |
| --- | --- | --- |
| Initial / price risk | 计划 Entry 到 Planned Protective Stop 的结构距离 | 事前计划输入 |
| Actual Risk / MAE | 交易结束后实际经历的最大不利距离 | 事后样本统计 |
| Account risk | 风险距离 × 数量，再计合约价值、成本、滑点和计划加仓 | 事前预算并按实际成交更新 |
| Personal risk | 因希望、恐惧、仓位过大或破坏规则产生的额外损失 | 通过计划和纪律限制 |

Actual Risk 不能用单笔赢家的事后浅回调替代事前 Stop，也不能证明原交易天然具有高 reward/risk。结构决定 Stop，仓位决定账户金额风险。

## 十一、Position Size 与数量变化

仓位服从 Planned Stop 和账户风险预算，不服务于信心。若多次 Entry 的价格为 `eᵢ`、数量为 `qᵢ`：

```text
Q = Σqᵢ
weighted average entry = Σ(qᵢ × eᵢ) / Q
```

多单共用 Stop `s` 时：

```text
gross stop risk = Σ[qᵢ × (eᵢ - s)]
```

空单镜像。真实风险还要乘每点价值并加入成本、滑点和异常余量。

若第 `i` 层预分配账户风险 `rᵢ`、每点价值为 `v`，数量近似为：

```text
qᵢ = (rᵢ - 该层成本与滑点预留) / (|eᵢ - s| × v)
```

同为账户 `1%` 风险的两层若 Entry 不同，数量通常也不同。提交或保留任何层时，已成交仓位与所有仍可能成交的计划层按共同或各自 Stop 计算的最坏风险总和，必须不超过计划总账户风险。

Scale-in 不凭空提高目标路径概率。计划内新层可以来自两类可观察依据：预先定义的更好价格，或成交后出现的新确认。前者只改善价格和平均成本，不增加方向证据；后者可以增强路径，但仍增加总数量和回撤暴露。只有原路径仍有效、层数和价格规则符合原计划、保护正常且全部实际与剩余层的最坏总风险仍在上限内，才允许新增数量。强反向证据出现时取消剩余层；无限摊平不是计划。

Scaling out 改变剩余数量、目标分布和成本。到计划目标部分退出、按预写分支降低风险或保留 runner 都必须在原方程中体现，不能用任意弱 K 线临时重写管理。

## 十二、Scalp、Swing 与时间

Scalp 与 Swing 不是交易类别，而是同一 Market Path 的不同目标、持有时间和风险实现：

- Scalp 使用较近目标和更快退出，成本占比更高；小目标常要求更高概率；
- Swing 使用较远结构目标，必须容纳正常 pullback，并以更小仓位承担更宽风险；
- TBTL 只描述约十根、两腿的时间与路径预期，不是价格目标或最低成立根数。

管理方式必须在承担风险前确定。按较低概率大目标进入后改用小 scalp 退出，或把区间内小目标临时改成趋势 swing，都会破坏原交易方程。若预写部分退出与 runner，可分别保存数量和结果条件。

## 十三、完整 Trade Plan

完整 Trade Plan 是系统语义的权威模板，用于复杂计划、自动化实现和盘后审计，不是每次 scalp 都要在盘中填完的文档。盘中记录负担按复杂度分层：

| 情况 | 必须保存 |
| --- | --- |
| 单次 Entry、单一 Stop、单一 Target 的普通计划 | 时点，路径目标，最强反方/失效，Entry、Stop、Target、Size，最迟有效条件 |
| 多层入场、多目标、runner 或条件化管理 | 在最小计划上增加数量分配、总风险、分支触发和取消条件 |
| 预挂条件单、OCO、跨 Session、异常处置或高执行风险 | 展开与实际风险相关的完整字段 |

心中确认不能替代必须冻结的风险数字；反过来，与当前计划无关的备选字段不得为了填满模板而虚构。下列完整字段在语义上仍然有效：

```text
Trade Plan

Decision
- 判断时点与 Runtime Snapshot：
- 当时适用规则：

Market Path
- Primary Test：
- 来源结构：
- 目标事件与到达口径：
- 周期与时间范围：
- 当前条件概率：
- 支持事实：
- 最强反方事实：
- 向上 / 向下 / Pending Opportunity Set 摘要：
- 增强 / 削弱 / 失效条件：

Entry
- 条件：
- 订单类型和价格规则：
- 有效期与取消条件：
- 是否允许在 Trigger 前预先提交条件订单：
- 承担风险前必须看到：
- 成交后预期看到：
- 允许预期反应出现的时间：
- 正常波动与 disappointment：

Risk
- Invalidation：
- Planned Protective Stop：
- Catastrophe Backup（如有）：
- Position Size：
- 全部层总账户风险：
- 成本与滑点假设：

Targets
- 第一现实目标：
- 主要结构目标：
- 延伸目标及启用条件：
- 各目标退出数量：
- Outcome Criterion：

Management
- Scalp / Swing：
- 正常回调容忍：
- 减仓规则：
- Runner：
- Trailing / Breakeven 条件：
- Scale-in 全部层与取消条件：
- 最迟退出时间：

Execution
- 订单生命周期：
- 成交后保护激活：
- 部分成交处理：
- 回执不明或保护不足处理：

Trade Outcomes
- 互斥结果、概率与 payoff：

Trader's Equation：
```

执行决定形成时保留当时适用的原始计划字段；首次成交对应这份计划。新事实可以改变当前路径评价和管理动作，却不能覆盖原目标、重选量度端点或把另一 horizon 的路径改写成原计划。任何计划外新增风险必须作为新计划评价并保存相应风险字段；只有新计划本身复杂时才要求展开全部模板。

## 十四、唯一决策

### 执行

路径、目标、概率、Entry、Invalidation、Stop、仓位、成本、时间、成交后预期和管理完整，交易方程成立。执行时保留原始计划并提交计划规定的订单意图：即时订单要求前置条件已经成立；预挂 Stop / Limit 要求计划明确允许在 Trigger 或成交前工作。提交不表示订单已被确认或账户已经成交。

### 等待

路径仍可能成立，但缺少：

- 明确目标或到达口径；
- 独立支持事实；
- Trigger / follow-through / acceptance；
- 合理 Entry、Stop 或现实空间；
- 当前价格下成立的方程。

等待必须明确所等事实和路径过期条件。只在它成为需要后续跟踪的正式 Wait 决定时，才保存这两项的简短记录。

等待不保留隐藏的可执行计划。未来事实发生时使用新的判断时点重新计算；已经提交并等待成交的 Stop / Limit order 属于执行状态，不属于等待决定。

Breakout Mode 等双向条件下可以分别形成相反方向的 Trade Plan，但每份计划仍只表达一条 Market Path。若同时提交相反方向的工作订单，提交前必须定义 OCO 或独立取消关系，并把双边先后或同时成交的最坏暴露计入总风险。

### 不交易

路径已失效，或现实 Target、剩余时间、风险、成本和执行条件使交换不值得承担。以后若形成新结构或新价格，建立新的 Market Path 与 Trade Plan，不复用旧计划。

### Decision Record

首次形成执行、可跟踪的等待或不交易决定，以及[总流程规定的关键节点](overall_flow.md#七必要记录与闭环)，保存一份最小 Decision Record：

```text
Decision Record

时点 + 品种/周期：
决定：Execute / Wait / No Trade
依据：Environment / Location + 所选路径或排除原因（一短句）
边界：目标 + 最强反方/失效条件
计划（如执行）：Entry + Stop + Target + Size
下一条件：触发 / 过期 / 重构
```

这些字段是必须固定的最小充分信息，可由简写、图表标记或工具自动生成。只有决定依据复杂、存在多周期/多分支、需要审计规则匹配，或盘后调查异常时，才展开下列完整格式：

```text
Extended Decision Record

判断时点与 Runtime Snapshot：
当时的 Market Model：
运行边界：
Frame、Environment、Location、Price Action Now 与 Active Test：
向上 / 向下 / Pending Opportunity Set：
目标事件、周期与时间范围：
支持事实与最强反方事实：
Rule Match 及其条件、目标、周期、horizon 和判断时点：
Entry / Invalidation / Stop / Target：
Trader's Equation：
Execution State（如适用）：
决定或实际动作：
决定原因、等待项或拒绝原因：
路径过期或替代条件：
订单、敞口、保护和动作确认结果（如适用）：
```

等待与不交易没有 Trade Plan 时，不填不适用的交易字段，也不从未来事实回填。执行阶段以原记录为锚，只补充实质改变的计划/风险 Delta 和必要执行事实；经纪商已可靠留存的普通提交、回执和成交不重复抄写，也不另建第二种决策记录。

## 十五、证据追溯

本页依据 [课程概念索引](../reference/course/concept_index.md)、[重复矩阵](../reference/course/repetition_matrix.md)、[边界与冲突](../reference/course/boundaries_and_conflicts.md)、[正式来源台账](../reference/official_sources.md)和逐讲材料对概率、风险、订单、目标和管理关系进行条件化整理。Reference 负责证据；本页负责统一决策契约。
