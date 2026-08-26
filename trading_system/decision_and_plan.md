# 交易决策与计划

> **状态：Trading System / Decision Contract**

本页规定怎样应用 Context Permission，把完成双向扫描且具备当前表达资格的 Opportunity 变成 `Trade Candidates`：先在 Trade Construction 中确定判断时点、Entry Method、Planned Protective Stop、Targets 与 Size，再由 Trade Gate 比较完整风险交换，并把被选 Candidate 冻结为 `Trade Plan`。

本页首先是完整的内部决策契约，不是盘中默认表单。交易者必须在承担风险前明确所有会改变风险或动作的输入，但只按[必要记录](overall_flow.md#九必要记录)保存最小决策信息；其余内容可以观察、心中确认或由工具自动计算。

## 一、决策顺序

```text
Market Read
→ Opportunity Set：分别构造现实的多空机会
→ Opportunity qualification：目标、Activation rule、Invalidation、horizon 与市场目标概率完整
→ Context Permission：当前市场是否允许这种表达
→ Trade Construction：为当前允许且可表达的少数机会构造判断时点、Trigger、Entry Method、Planned Stop、Targets 与 Size
→ Trade Gate：比较交易结果概率 / Reward / Risk / Cost / Time / Management
→ 执行 / 等待 / 不交易
```

Opportunity 是“市场可能怎样走”；Candidate 是“现在怎样承担风险”。一个 Opportunity 可以在不同判断时点产生不同 Candidate，例如强突破后的 close entry、等待 follow-through、或回调后的 H1/H2。目标必须先于 Entry；不能先看到触发，再寻找远端目标修复 reward/risk。

## 二、Opportunity 资格与 Candidate 生成

Opportunity 进入交易构造前必须具备：

- Direction、Role 与 Horizon 清楚；
- 一个可观察的 Objective 和 Market Outcome Criterion；
- 来自 Price Map 或事前固定投射的 Market Targets；
- 去重后的理由链，以及已经发生与下一步需要发生的价格事实；
- 明确 Activation：哪些后续事实使机会具备交易表达资格；
- 明确 Invalidation：哪些市场事实真正否定机会；
- Support / Resistance、Potential Entry Area、Obstacle、Magnet、Targets 与 Invalidation Reference 的 Price Region Roles；
- 当前最强反方事实或竞争 Opportunity；
- 过期条件；
- 与 Objective、周期、horizon 和时点一致的 Market Probability / Rule Match。

缺少 Objective、Invalidation 或 horizon 时仍是未解决的 Market Read，不伪造 Opportunity。Market Read 未解决、Opportunity 尚未 Activation，或当前没有值得承担的 Candidate 时，都可以输出 `Wait`；只说明下一事实与过期条件。

双向考虑不要求为每个方向制造 Candidate。明显没有现实目标、空间或时间的一侧只需说明排除原因；只有当前具有可观察 Entry、合理 Stop 和可计算结果的少数 Opportunity 进入 Candidate 计算。

```text
Trade Candidate
- Opportunity 引用与判断时点
- Early / Confirmed 风险承担时点
- Trigger Boundary
- Entry Method / Entry Price Rule / Expiry
- 引用 Opportunity Invalidation / Planned Protective Stop
- First Target / Main Target / Outcome Criterion
- Candidate Outcome Probability / Reward / Risk / Cost / Time
- Size / Management
```

结构失效属于 Opportunity；Trigger、Entry 和实际保护性 Stop 属于 Candidate。Trade Plan 为审计冻结 Invalidation 的当时值，但不能重新定义它。Stop 的距离会决定这个机会是否值得、是否需要等待更好 Entry，却不是额外的方向证据。

### Context Permission

Context 先决定当前表达的最低证据，而不是事后调整同一个 Pattern 的胜率：

| Context | 默认表达 | 逆势或突破 Candidate 的最低条件 |
| --- | --- | --- |
| Breakout / Spike | 沿 Control 方向 | 等强反向 breakout、follow-through 与接受 |
| Tight Channel | 顺势 continuation | 普通三推、H2 或一根 reversal bar 不足；先完成控制转移 |
| Broad Channel | 顺势 swing；边缘可逆势 scalp | 有效边缘、独立测试、反向 Pressure、可用空间和实际 Trigger |
| Trending Trading Range | 顺势略占优；局部双边 | 分开 range return、continuation 与长期 reversal |
| Trading Range | 边缘 range return；中部等待 | 外部突破、follow-through 并守住后转 breakout |
| Breakout Mode | 等待实际突破结果 | 突破、跟随、守住或回踩成功后重算 |
| Climax / Transition | 原方向减弱 | 后续停止延续、反向 Pressure 与接受决定是否允许逆势 |

保守 fallback 服从 Market Read：Tight/Broad 不清按 Tight，只沿 Control；Broad Channel/Range 不清按 Range，不在中部制造 Candidate。

## 三、证据汇合，而不是理由计数

承担风险前必须有足以支持当前路径的可观察价格事实。支持可以由一条强而一致的价格链主导，也可以由来源独立、相互补充的事实汇合；系统不设置固定理由数量。支持通常来自：

| 维度 | 回答的问题 | 例子 |
| --- | --- | --- |
| 活动结构 | 当前主要怎样运动？ | Trend、Channel、Range、Breakout Mode |
| Pressure / Control | 哪一方正在保持或失去控制？ | 连续强收盘、浅回调、反方失败 |
| 位置与目标 | 价格在哪里，前方是否有现实空间？ | 区间边缘、突破点、旧极值、magnet |
| 测试与次序 | 当前价格怎样组织测试？ | 第二次测试、三推、回踩、failed breakout |
| Trigger / Response | 哪个新事实允许承担风险？ | stop trigger、follow-through、拒绝、重新接受 |

这些维度用于检查支持是否完整，不是评分器，也不要求全部出现。以下通常只是一份证据：

- H2、Double Bottom、Second Signal 和 H1 失败来自同一两次尝试；
- 同一突破产生的大实体、gap、pressure、control 和 acceptance；
- 同一突破或失败链产生的 disappointment、trapped / Pain Trade 推断和预期退出压力；
- Broad Channel 与 Trending Trading Range 描述同一方向移动；
- 旧高、区间边界、double-top 区域和 measured-move 落在同一价格区域。

独立同向证据通常增强路径，但概率仍由与目标事件匹配的条件规则提供，不能按理由数量制造百分比。一个强反方事实可以覆盖多个弱支持理由。

比较机会时不得只选择裸概率较高或支持名称较多的一侧。相同 Objective、周期和 horizon 的 Opportunity 可以比较 Market Probability；不同 Objective 或 horizon 必须分别构造当前 Entry、Stop、Target、成本和结果方程，再比较完整风险交换。未决、超时、scratch 等结果意味着双向概率不必相加为 `100%`。

## 四、Trade Construction｜Trigger 与判断时点

Trigger 只说明当前 Candidate 可以用某个价格表达，不保证 Opportunity 的目标实现。Candidate 必须明确 Trigger 是在承担风险前必须完成，还是成交后继续验证。

Activation 表示哪些市场事实使 Opportunity 具备交易表达资格；Trigger 表示选定 Candidate 怎样进入市场。通常先完成 Activation，再构造 Trigger。例如完成第二次测试并形成合格 signal bar 可以激活早期 Opportunity，随后 signal-bar 高点 / 低点才是 Stop-entry Trigger。

计划只有在明确允许预挂条件单、且订单 Trigger 本身完整执行尚缺的 Activation 条件时，才可在 Activation 前提交。若 Activation 还要求 bar close、follow-through、回踩守住或 acceptance，单纯越过一个 stop price 不能替代这些事实；需要平台可验证的复合条件，否则继续 Wait。订单触发不回填未发生的背景条件。

Trade Construction 中的所有可执行价格都必须能沿当前判断链追溯：

```text
Price Map 中唯一登记的 Region
→ Active Test 的互动与 Trigger Boundary
→ Opportunity 分配 Entry Area / Obstacle / Target / Invalidation Reference
→ Candidate 选择 Entry Method、Planned Protective Stop 与 First / Main Target
```

Entry 可以引用 Price Region、signal-bar 高低或其他 Active Test 边界；Target 引用 Opportunity 已固定的区域或投射；Structural Invalidation 同时包含区域引用和否定路径的市场事件；Planned Protective Stop 引用当前 Candidate 的局部结构、正常波动与账户风险。无法说明价格来源的 Candidate 不进入 Trade Gate。

### Signal bar、chart entry 与 actual fill

- `Prospective signal bar`：仍在形成、可能提供触发依据的 K 线；
- `Signal bar`：完成后为当前路径提供可观察入场依据的 K 线，即使订单最终未触发；
- `Chart entry bar`：图表上既定触发条件第一次被越过或满足的 K 线，不要求账户下单；
- `Actual fill bar`：账户真实获得成交的 K 线。

这些角色可能落在同一根，也可能不同。没有实际成交不能抹去图表触发，没有图表触发也不能从账户意图制造 Pattern 事实。

### Signal-bar 评价

只有 Context Permission、Opportunity、位置、目标和交易方向已经明确后，才评价 signal bar：

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
| 较早参与 | 结构和触发可定义，但尚无独立跟随 | Entry 较好，Candidate Outcome Probability 通常较低或更不确定 |
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

订单类型由 Activation 与当前愿意承担的确认程度决定：

- 需要价格先向计划方向触发时，使用 Stop entry，或等条件完成后使用 Market / close；
- 位置与 Context 已提供足够优势、计划允许在较少确认下换取价格改善时，使用 Limit entry；
- breakout、follow-through 或 acceptance 已经完成，继续等待的代价高于立即表达时，可以使用 Market / close。

“等待回调后的 H2”通常是先等待新的局部测试，再在其 signal bar 上方或下方使用 Stop entry；它不因价格比突破收盘更好就自动属于 Limit entry。

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

Structural Invalidation 由 Opportunity 唯一定义，是新价格事实已经使该市场结果不再成立，例如：

- 原结构关键边界被有效突破并在反侧获得接受；
- 目标所依赖的分离、控制或测试关系被实质否定；
- 强反向 breakout、连续动量或 Always In 切换建立了反路径。

Invalidation 可以在最远 Protective Stop 触发前要求主动退出。普通反色 K 线、正常 pullback 或短暂失望不自动构成 Invalidation。

horizon 结束而目标和失效均未发生时，Opportunity 进入 `EXPIRED`，不记为市场事实否定。若目标和失效在同一观察 K 线内且顺序无法确认，记为 `SEQUENCE_UNKNOWN`；当前问题尚未解决则仍是 `ACTIVE`，两者不同。

账户预算、成本、Session 持仓限制、基础设施或执行条件可以淘汰当前 Candidate 或使 Trade Plan 失效，却不改变市场目标是否仍可能发生。Plan invalidation 要求停止新增风险、撤销对应工作订单或按计划收缩风险；只有市场事实或 horizon 才关闭 Opportunity。

### Planned 与 Active Protective Stop

- `Planned Protective Stop`：承担风险前确定的价格或价格规则，用于风险、仓位和激活计划；
- `Active Protective Stop`：实际成交后，状态可确认且覆盖实际仓位的在场保护；
- `Trailing Stop`：新结构形成后，只向降低开放风险方向移动的 Active Stop；
- `Catastrophe Backup`：若使用，作为另行预算的更远灾难保护，不能与 Planned / Active Stop 共用同一字段。

合理 Stop 引用 Opportunity Invalidation，并位于能够容纳所选周期正常波动的位置。它可以在结构彻底确认失效前限制账户尾部风险，也可以因执行假设选择更近退出，但这代表 Candidate 的账户边界，不改写市场 Invalidation。Signal bar 另一端、完整 pullback、major swing 或结构边界都可能合理；不能为了漂亮 reward/risk 把 Stop 塞进正常波动。

同一图表可以存在多个合理 Stop 候选，但它们代表不同计划。Stop 较远时缩小仓位、等待更好 Entry 或不交易，不任意缩短结构风险。

## 七、Market Target、Candidate Target 与 Outcome Criterion

Opportunity 先保存市场自然生成的 Market Targets；Candidate 再根据当前 Entry、近端障碍、剩余空间、时间与管理选择 First Target、Main Target 和可选延伸目标。等待确认或改用另一 Entry Method 后必须重新选择当前可交易目标，不能越过近端区域借远端 MM 修复方程。

Trade Candidate 从 Opportunity 已经定义的目标事件中选择实际准备兑现的价格和数量；被选后这些字段成为 Trade Plan：

| 层次 | 职责 |
| --- | --- |
| 候选目标 | 结构可量度后事前生成，用于判断路径空间 |
| 第一现实目标 | Entry 后最近、当前路径确实可能测试的 magnet |
| 主要结构目标 | 所选 Opportunity 直接生成的目标事件 |
| 延伸目标 | 只有新突破和跟随继续支持原 Opportunity 时才启用 |

Outcome Criterion 必须规定：

- 评价哪个 objective；
- 目标是价格还是区域，哪个边界算到达；
- 图表触及是否足够，还是要求按执行假设或账户实际成交；
- 部分退出对应多少数量；
- Stop 与目标在同一回放 K 线内且顺序不明时怎样记录；
- scratch、breakeven、主动退出和时间退出怎样构成互斥结果。

价格曾提供 scalper's profit，不自动等于账户捕获，也不等于 swing objective 成功。不同 objective 可以对同一路径产生不同 success / failure 结果，必须分别记录。

## 八、市场目标概率与交易结果概率

条件规则台账保存可匹配模板；模板中的相对条件只有绑定当前 Opportunity 后才能成为可运行的 Rule Match。概率判断格式：

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

只有 `可运行` 的当前匹配可以成为 Opportunity 的 Market Probability。模板若缺少当前目标、周期、horizon 或判断时点，只能提供 Context 或概率语言；不能用计划临时选择的远端目标补齐来源规则，也不能把相同方向但不同目标的规则当作更具体替代。

Brooks 教学中的 `likely / probably` 通常表示约 `60%+`，`unlikely` 表示约 `40%-`；它们是近似语言，不是经过统一样本校准的统计模型。

70%–80% 的结构概率只有在当前目标事件、周期、时间范围和条件与原规则完全相同时才能直接使用。结构生命周期概率、突破方向先验、某次目标先于 Stop 的交易概率和基础结构/阶段频率不是同一对象。

无法说明当前路径为什么属于某条规则时，使用诚实的 40%–60% 近似语言或继续等待，不以标签数量制造精度。规则选择与隔离项见[条件规则台账](conditional_rules_registry.md)。

```text
Market Probability
= P(Opportunity Objective 在 horizon 内按口径发生 | 当前市场条件)

Candidate Outcome Probability
= P(各交易结果 | Trigger、Entry、Stop、Targets、数量、时间与管理)
```

若 Candidate 的胜负事件恰好等于“Objective 先于 Invalidation”，Market Probability 可以成为交易结果估计的主要输入；存在更近 Protective Stop、部分退出、主动退出、scale-in 或不同时间条件时，两者不相同。Trader's Equation 只使用与 Candidate 互斥结果相容的概率或诚实区间，不能直接复制裸市场目标概率。

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

Scale-in 不凭空提高 Market Probability。计划内新层可以来自两类可观察依据：预先定义的更好价格，或成交后出现的新确认。前者只改善价格和平均成本，不增加方向证据；后者可以更新 Opportunity 或 Candidate Outcome Probability，但仍增加总数量和回撤暴露。只有原 Opportunity 仍有效、层数和价格规则符合原计划、保护正常且全部实际与剩余层的最坏总风险仍在上限内，才允许新增数量。强反向证据出现时取消剩余层；无限摊平不是计划。

Scaling out 改变剩余数量、目标分布和成本。到计划目标部分退出、按预写分支降低风险或保留 runner 都必须在原方程中体现，不能用任意弱 K 线临时重写管理。

## 十二、Scalp、Swing 与时间

Scalp 与 Swing 不是交易类别，而是同一 Opportunity 的不同目标、持有时间和风险实现：

- Scalp 使用较近目标和更快退出，成本占比更高；小目标常要求更高概率；
- Swing 使用较远结构目标，必须容纳正常 pullback，并以更小仓位承担更宽风险；
- TBTL 只描述约十根、两腿的时间与路径预期，不是价格目标或最低成立根数。

管理方式必须在承担风险前确定。按较低概率大目标进入后改用小 scalp 退出，或把区间内小目标临时改成趋势 swing，都会破坏原交易方程。若预写部分退出与 runner，可分别保存数量和结果条件。

## 十三、完整 Trade Plan

完整 Trade Plan 是被选 Candidate 的冻结快照，用于复杂计划、自动化实现和盘后审计，不是每次 scalp 都要在盘中填完的文档。盘中记录负担按复杂度分层：

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

Selected Opportunity
- Direction / Role / Horizon：
- Objective 与到达口径：
- Market Targets：
- Why（去重后的价格链）：
- Already → Next：
- Activation：
- Against：
- Expiry / Structural Invalidation：
- Price Map 引用：Support / Resistance / Potential Entry Area / Obstacles / Magnets / Targets / Invalidation Reference：
- Market Probability / Rule Match：

Entry
- 判断时点：Early / Confirmed：
- Trigger Boundary：
- 条件：
- Entry Method：Stop / Limit / Market-Close：
- 订单价格规则：
- 有效期与取消条件：
- 是否允许在 Trigger 前预先提交条件订单：
- 承担风险前必须看到：
- 成交后预期看到：
- 允许预期反应出现的时间：
- 正常波动与 disappointment：

Risk
- Opportunity Invalidation Snapshot：
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
- 互斥结果、Candidate Outcome Probability 与 payoff：

Trader's Equation：
```

执行决定形成时保留当时适用的原始计划字段；首次成交对应这份计划。新事实可以改变当前路径评价和管理动作，却不能覆盖原目标、重选量度端点或把另一 horizon 的路径改写成原计划。任何计划外新增风险必须作为新计划评价并保存相应风险字段；只有新计划本身复杂时才要求展开全部模板。

## 十四、Trade Gate 与唯一决策

Trade Gate 只评价已经完成 Trade Construction 的 Candidate。进入唯一决策前确认：双向扫描完成，Context Permission 允许，Activation 已满足或由许可的条件 Trigger 完整执行，Entry / Stop / Targets 的价格来源可追溯，且当前结果概率、Reward、Risk、成本、时间、Size、管理和执行可靠性形成完整方程。

### 执行

路径、目标、概率、Entry、Invalidation、Stop、仓位、成本、时间、成交后预期和管理完整，交易方程成立。执行时保留原始计划并提交计划规定的订单意图：即时订单要求前置条件已经成立；预挂 Stop / Limit 要求计划明确允许在 Trigger 或成交前工作。提交不表示订单已被确认或账户已经成交。

### 等待

等待可以发生在三个阶段：

1. Market Read 尚未解决：等待区域接受、拒绝或 Control 变化；
2. Opportunity 尚未 Activation：等待预先声明的 follow-through、第二次测试或结构破坏；
3. Opportunity 已 Activation，但当前没有正方程：只有 Expiry 前存在明确、现实的更好价格或新 Candidate 事件时才等待。

等待必须明确下一可观察事实和 Expiry。缺少现实下一事件，或空间、时间、风险已经排除当前机会时，输出 No Trade。只在 Wait 需要跨事件持续跟踪时，才保存下一事实和 Expiry。

等待不保留隐藏的可执行计划。未来事实发生时使用新的判断时点重新计算；已经提交并等待成交的 Stop / Limit order 属于执行状态，不属于等待决定。

Breakout Mode 等双向条件下可以分别形成相反方向的 Trade Plan，但每份计划仍只表达一条 Opportunity。若同时提交相反方向的工作订单，提交前必须定义 OCO 或独立取消关系，并把双边先后或同时成交的最坏暴露计入总风险。

### 不交易

Opportunity 已失效，或现实 Target、剩余时间、风险、成本和执行条件使当前 horizon 内不存在值得跟踪的 Candidate。以后若发生新 Reframe，建立新的 Opportunity 与 Trade Plan，不复用旧计划。

### Decision Record

首次形成执行或需跨事件跟踪的等待，以及[总流程规定的关键节点](overall_flow.md#九必要记录)，保存一份最小 Decision Record。普通扫描得到 No Trade 不记录；只有它改变观察计划、风险或规则样本时才保存原因。

```text
Decision Record

时点 + 品种/周期：
决定：Execute / Wait / No Trade
依据：Market Read + 所选 Opportunity 或排除原因（一短句）
双向：Long / Short 结论 + Likely Sequence
边界：Activation / 目标 + 最强反方 / Invalidation / Expiry
计划（如执行）：Entry Method + Entry + Planned Stop + Target + Size
下一条件：触发 / 过期 / 重构
```

这些字段是必须固定的最小充分信息，可由简写、图表标记或工具自动生成。复杂执行直接关联本页上一节的完整 Trade Plan；系统不再维护一份重复的 Extended Decision Record。等待与不交易没有 Trade Plan 时，不填交易字段；执行阶段只在原记录追加实质改变的计划/风险 Delta 和必要执行事实。

## 十五、证据追溯

本页依据 [课程概念索引](../reference/course/concept_index.md)、[重复矩阵](../reference/course/repetition_matrix.md)、[边界与冲突](../reference/course/boundaries_and_conflicts.md)、[正式来源台账](../reference/official_sources.md)和逐讲材料对概率、风险、订单、目标和管理关系进行条件化整理。Reference 负责证据；本页负责统一决策契约。
