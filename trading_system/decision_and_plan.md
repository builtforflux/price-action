# 交易决策与计划

> **状态：Trading System / Decision Contract**

本页规定怎样应用 Context Permission，把完成双向扫描且具备当前表达资格的 Opportunity 变成 `Trade Candidates`，以及怎样由唯一 `Decision` 根据完整 Candidate 或下一事件输出 `EXECUTE / WAIT / NO_TRADE`。Trade Construction 确定判断时点、Entry Method、Planned Protective Stop、Targets 与 Size；只有 `EXECUTE` 才把 Candidate 冻结为 `Trade Plan`。

本页首先是完整的内部决策契约，不是盘中默认表单。交易者必须在承担风险前明确所有会改变风险或动作的输入，但只按[必要记录](overall_flow.md#六必要记录)保存最小决策信息；其余内容可以观察、心中确认或由工具自动计算。

## 一、决策顺序

```text
Market Read
→ Opportunity Set：分别构造现实的多空机会
→ Opportunity qualification：目标、Activation rule、Invalidation、Outcome Horizon 与市场目标概率完整
→ Context Permission：当前市场是否允许这种表达
→ Trade Construction：为当前允许且可表达的少数机会构造判断时点、Trigger、Entry Method、Planned Stop、Targets 与 Size
→ Decision：完整 Candidate / 明确下一事件 / 两者皆无
→ Execute / Wait / No Trade
```

Opportunity 是“市场可能怎样走”；Candidate 是“现在怎样承担风险”。一个 Opportunity 可以在不同判断时点产生不同 Candidate，例如强突破后的 close entry、等待 follow-through、或回调后的 H1/H2。目标必须先于 Entry；不能先看到触发，再寻找远端目标修复 reward/risk。

## 二、Opportunity 资格与 Candidate 生成

Opportunity 进入交易构造前必须具备：

- Direction、Role 与 Outcome Horizon 清楚；
- 一个可观察的 Objective 和 Market Outcome Criterion；
- 来自 Price Map 或事前固定投射的 Market Targets；
- `Support / Already`：去重后的已发生价格事实链；
- 明确 Activation：哪些后续事实使机会具备交易表达资格；
- 明确 Invalidation：哪些市场事实真正否定机会；
- 所有 Support / Resistance、Potential Entry Area、Obstacle、Magnet、Targets 与 Invalidation Reference 直接引用 Price Map 中唯一登记的 Region；
- `Counterevidence`：尚未由完整对手 Opportunity 表达的最强反方价格事实；没有则 `NONE`；
- `Opportunity Expiry`：当前 Objective 在 Outcome Horizon 内仍有意义的最迟边界；
- 与 Objective、周期、Outcome Horizon 和时点一致的 Market Probability / Rule Match。

缺少 Objective、Invalidation 或 Outcome Horizon 时不伪造 Opportunity。双向扫描只有 `OPPORTUNITY / WATCH / EXCLUDED` 三种侧面结果：WATCH 保存 Next Event 与 Expiry，EXCLUDED 保存排除原因；这些结果与 Candidate 一起进入 Decision，由 Decision 唯一输出 `WAIT / NO_TRADE / EXECUTE`。

双向考虑不要求为每个方向制造 Candidate。明显没有现实目标、空间或时间的一侧只需说明排除原因；只有当前具有可观察 Entry、合理 Stop 和可计算结果的少数 Opportunity 进入 Candidate 计算。

```text
Trade Candidate
- Opportunity 引用与判断时点
- Early / Confirmed 风险承担时点
- Activation Status / Trigger 是否完整执行剩余 Activation
- Trigger Boundary
- Entry Method / Entry Price Rule / Entry Validity
- 引用 Opportunity Invalidation / Planned Protective Stop
- First Target / Main Target / Outcome Criterion
- Candidate Outcome Probability / Reward / Risk / Cost / Time
- Size / Management
```

结构失效属于 Opportunity；Trigger、Entry 和实际保护性 Stop 属于 Candidate。Trade Plan 为审计冻结 Invalidation 的当时值，但不能重新定义它。Stop 的距离会决定这个机会是否值得、是否需要等待更好 Entry，却不是额外的方向证据。Long 与 Short Opportunity 天然互为竞争对象；Counterevidence 只保存尚未形成完整对手 Opportunity 的反方价格事实。

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

比较机会时不得只选择裸概率较高或支持名称较多的一侧。相同 Objective、周期和 Outcome Horizon 的 Opportunity 可以比较 Market Probability；不同 Objective 或 Outcome Horizon 必须分别构造当前 Entry、Stop、Target、成本和结果方程，再比较完整风险交换。未决、超时、scratch 等结果意味着双向概率不必相加为 `100%`。

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

Entry 可以引用 Price Region、signal-bar 高低或其他 Active Test 边界；Target 引用 Opportunity 已固定的区域或投射；Structural Invalidation 同时包含区域引用和否定路径的市场事件；Planned Protective Stop 引用当前 Candidate 的局部结构、正常波动与账户风险。无法说明价格来源的 Candidate 不能成为 Ready Candidate。

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
- Entry Validity：
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

Limit entry 用更好价格交换更少确认。计划必须明确成交后期待的拒绝、重新进入旧区域、Pressure 变化或其他反应，以及允许这些事实出现的时间。价格 touch / cross 不保证账户全部成交；若计划依赖 scale-in，第一笔 entry 前必须确定整份计划的风险上限、首层最大额度、共同或独立 Stop、允许 Add 的区域或事件以及取消条件。未来层的准确价格和数量可以在条件发生时按剩余风险计算。

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

Outcome Horizon 结束而目标和失效均未发生时，Opportunity 进入 `EXPIRED`，不记为市场事实否定。若目标和失效在同一观察 K 线内且顺序无法确认，记为 `SEQUENCE_UNKNOWN`；当前问题尚未解决则仍是 `ACTIVE`，两者不同。

账户预算、成本、Session 持仓限制、基础设施或执行条件可以淘汰当前 Candidate 或使 Trade Plan 失效，却不改变市场目标是否仍可能发生。Plan invalidation 要求停止新增风险、撤销对应工作订单或按计划收缩风险；只有市场事实或 Outcome Horizon 才关闭 Opportunity。

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

只有 `可运行` 的当前匹配可以成为 Opportunity 的 Market Probability。模板若缺少当前目标、周期、Outcome Horizon 或判断时点，只能提供 Context 或概率语言；不能用计划临时选择的远端目标补齐来源规则，也不能把相同方向但不同目标的规则当作更具体替代。

Brooks 教学中的 `likely / probably` 通常表示约 `60%+`，`unlikely` 表示约 `40%-`；它们是近似语言，不是经过统一样本校准的统计模型。

70%–80% 的结构概率只有在当前目标事件、周期、时间范围和条件与原规则完全相同时才能直接使用。结构生命周期概率、突破方向先验、某次目标先于 Stop 的交易概率和基础结构/阶段频率不是同一对象。

无法说明当前路径为什么属于某条规则时，使用诚实的 40%–60% 近似语言或继续等待，不以标签数量制造精度。规则选择与隔离项见[条件规则台账](conditional_rules_registry.md)。

```text
Market Probability
= P(Opportunity Objective 在 Outcome Horizon 内按口径发生 | 当前市场条件)

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

概率、Reward 和 Risk 必须描述同一 Entry、Planned Stop、Target、时间和管理方式。`Execution Cost` 只计会实质改变当前结果的手续费、点差和预计滑点；正常高流动性执行中预计滑点可以配置为零，异常流动性、跳空或平台状态统一进入执行安全路径。

在“赢家 `2R`、失败 `1R`”且暂不计成本的二结果中，正期望要求成功概率大于 `1/3`；这不表示任何 `2R` 远端目标都合理。约 40% 的较早或较低概率路径通常需要更大现实 Reward，约 60% 的条件可以在约 1R 时仍可能成立，但均须使用当前实际输入。

计划包含部分退出、scale-in、scratch 或主动退出时，应列出互斥结果 `i`：

```text
Σ [P(result_i) × payoff_i] - cost > 0
```

没有可靠样本时不构造伪精确的完整概率树；至少保证所有计划内的重要结果没有被二结果公式隐藏。

## 十、风险口径

| 风险 | 含义 | 使用时点 |
| --- | --- | --- |
| Initial / price risk | 计划 Entry 到 Planned Protective Stop 的结构距离 | 事前计划输入 |
| Actual Risk / MAE | 交易结束后实际经历的最大不利距离 | 事后样本统计 |
| Account risk | 风险距离 × 数量 × 每点价值，再计实质相关的 Execution Cost 和计划加仓 | 事前预算并按实际成交更新 |

盘中只计算 Initial / price risk 与 Account risk；Actual Risk / MAE 只在复盘使用。希望、恐惧、仓位过大或破坏规则归入行为纪律。Actual Risk 不能用单笔赢家的事后浅回调替代事前 Stop，也不能证明原交易天然具有高 reward/risk。结构决定 Stop，仓位决定账户金额风险。

## 十一、Position Size 与数量变化

仓位服从 Planned Stop 和整份 Trade Plan 的账户风险上限，不服务于信心。多层计划在第一笔 Entry 前冻结：

```text
Risk Limit      整份计划最多承担的账户风险
Initial Limit   第一层最多使用的风险
Add Permission  后续允许使用剩余额度的区域或确认事件
Cancel Add      取消剩余层的市场、时间、方程或执行条件
Stop Rule       各层共同或独立的保护规则
```

`Risk Limit = 账户配置的风险资本 × 本计划风险比例`。账户配置统一提供风险资本与默认比例，每份计划只保存本次计算得到的金额或比例上限。

Risk Limit 属于当前 Trade Plan。多个计划同时存在时，账户当前承诺风险等于各计划 Risk Committed 之和；有效 Risk Available 为 `max(0, min(本计划剩余额度, 账户总上限剩余额度))`。只有一个计划时两者相同，无需展开组合对象。

未来层在 Add 决策事件到达后，以实际价格计算 Entry、数量和订单：

```text
Open Position Stop Risk = max(0, 实际仓位在 Active Stop 成交时的损失)
Working Order Stop Risk = Σ max(0, 每个仍可能增加暴露的订单成交后到 Planned Stop 的损失)
Risk Committed = Open Position Stop Risk + Working Order Stop Risk
                 + 实质相关的 Execution Cost
Risk Available = max(0, Risk Limit - Risk Committed)
```

Risk Limit、Initial Limit、Add Permission、Cancel Add 和 Stop Rule 冻结在 Trade Plan；Risk Committed / Available 由 Execution State 根据订单、仓位和保护动态计算。保留额度不等于已经承担的暴露，也不授权加仓。Trail 最多把已有仓位的 Stop Risk 降到零；已保护利润不作为负风险抵消其他订单风险。释放的数值容量也不自动产生新的 Add Permission。原 Opportunity、Add Permission、当前方程和保护必须同时允许，新增数量才可使用 Risk Available。

若多次 Entry 的价格为 `eᵢ`、数量为 `qᵢ`：

```text
Q = Σqᵢ
weighted average entry = Σ(qᵢ × eᵢ) / Q
```

多单共用 Stop `s` 时：

```text
gross stop loss = max(0, Σ[qᵢ × (eᵢ - s)])
```

空单镜像。账户风险还要乘每点价值，并只加入实质相关的 Execution Cost。

若第 `i` 层最多分配账户风险 `rᵢ`、每点价值为 `v`、每单位实质相关的 Execution Cost 为 `cᵢ`，数量近似为：

```text
qᵢ = rᵢ / (|eᵢ - s| × v + cᵢ)
```

同为账户 `1%` 风险的两层若 Entry 不同，数量通常也不同。已经提交并仍可能增加暴露的层计入 Risk Committed；仅保留资格、尚未形成订单的层仍属于 Risk Available。提交或保留任何新增风险订单时，已成交仓位与所有仍可能增加暴露的订单按共同或各自 Stop 计算的总风险必须不超过 Risk Limit。

Scale-in 不凭空提高 Market Probability。计划内新层可以来自两类可观察依据：预先定义的更好价格区域，或成交后出现的新确认。前者通常用 Limit 换取价格改善，只改善 Entry 和平均成本，不增加方向证据；后者在确认事实完成后使用适合当前 Trigger 的 Stop / Market / Limit 表达，可以更新 Opportunity 或 Candidate Outcome Probability，但仍增加总数量和回撤暴露。只有原 Opportunity 仍有效、Add 条件已经发生、取消条件未发生、保护正常且加仓后 Risk Committed 仍在上限内，才允许新增数量。强反向证据出现时取消剩余额度的使用资格；无限摊平不是计划。

Scaling out 改变剩余数量、目标分布和成本。到计划目标部分退出、按预写分支降低风险或保留 runner 都必须在原方程中体现，不能用任意弱 K 线临时重写管理。

## 十二、Scalp、Swing 与时间

Scalp 与 Swing 不是交易类别，而是同一 Opportunity 的不同目标、持有时间和风险实现：

- Scalp 使用较近目标和更快退出，成本占比更高；小目标常要求更高概率；
- Swing 使用较远结构目标，必须容纳正常 pullback，并以更小仓位承担更宽风险；
- TBTL 只描述约十根、两段的时间与路径预期，不是价格目标或最低成立根数。

管理方式必须在承担风险前确定。按较低概率大目标进入后改用小 scalp 退出，或把区间内小目标临时改成趋势 swing，都会破坏原交易方程。若预写部分退出与 runner，可分别保存数量和结果条件。

## 十三、完整 Trade Plan

完整 Trade Plan 是被选 Candidate 的冻结快照，用于复杂计划、自动化实现和盘后审计，不是每次 scalp 都要在盘中填完的文档。盘中记录负担按复杂度分层：

| 情况 | 必须保存 |
| --- | --- |
| 单次 Entry、单一 Stop、单一 Target 的普通计划 | 时点；所选路径与最强反方（一短句）；Entry Method / Price 与 Entry Validity；Planned Stop；Target；Size / Risk；Invalidation / Cancel Condition |
| 多层入场、多目标、runner 或条件化管理 | 在最小计划上增加 Risk Limit、首层额度、Add / 取消条件和分支触发 |
| 预挂条件单、跨 Session、异常处置或高执行风险 | 展开与实际风险相关的完整字段 |

心中确认不能替代必须冻结的风险数字；反过来，与当前计划无关的备选字段不得为了填满模板而虚构。下列完整字段在语义上仍然有效：

```text
Trade Plan

Decision
- 判断时点：
- Runtime Snapshot：
- 当时适用规则：

Selected Opportunity
- Direction：
- Role：
- Outcome Horizon：
- Objective：
- Market Outcome Criterion：
- Market Targets：
- Support / Already（去重后的价格链）：
- Activation：
- Activation Status：
- Counterevidence：
- Opportunity Expiry：
- Structural Invalidation：
- 引用的 Price Map Regions 及其当前角色：
- Market Probability：
- Rule Match：

Entry
- Risk Timing：Early / Confirmed：
- Trigger Boundary：
- 条件：
- Entry Method：Stop / Limit / Market-Close：
- 订单价格规则：
- Entry Validity：
- Cancel Condition：
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
- Risk Limit：
- Initial Limit：
- Execution Cost 假设：

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
- Scale-in：Add Permission / Cancel Add / Stop Rule：
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

执行决定形成时保留当时适用的原始计划字段；首次成交对应这份计划。新事实可以改变当前路径评价和管理动作，却不能覆盖原目标、重选量度端点或把另一 Outcome Horizon 的路径改写成原计划。计划内 Add 发生时只在 Execution State / Plan Delta 追加 Entry Method、价格、数量、Stop、加仓后 Risk Committed 和触发依据；出现原计划外的新 Opportunity、目标、失效或 Stop 时，新增风险才必须作为新 Candidate 评价。只有新计划本身复杂时才要求展开全部模板。

## 十四、Decision 与唯一决定

Market Read、Opportunity Scan 和 Trade Construction 只产生继续所需的对象，或指出下一项现实事件。Decision 的输入是：

```text
Candidate：[COMPLETE / NONE]
Next Event：[可观察事件 / NONE]
Decision Expiry：[时间或替代事件 / N/A]
```

Decision 一次只接收一条 Candidate。Candidate 完整时可以得到 `EXECUTE`；没有 Candidate、但存在明确、现实且尚未过期的 Next Event 时得到 `WAIT`；两者都没有时得到 `NO_TRADE`。Decision 只拥有当前新交易表达；实际订单参数、保护激活和提交时账户状态由 Ready to Submit 复核，持仓动作与原计划内 Add 分别由 Open Position 和 Add Gate 处理。

### 执行

双向扫描完成，Context Permission 允许，Activation 已满足或由许可 Trigger 完整执行，Entry / Stop / Targets 可追溯，且概率、Reward、Risk、成本、时间、Size 与管理形成正方程时，完整 Candidate 得到 `EXECUTE`。Decision 冻结原始 Trade Plan 并进入 Ready to Submit，尚未产生订单意图；[执行前复核](execution_management_and_review.md#一执行前复核)确认关键输入仍成立后，才提交计划规定的订单。即时订单要求前置条件已经成立；预挂 Stop / Limit 要求计划明确允许在 Trigger 或成交前工作。提交仍不表示订单已被确认或账户已经成交。

### 等待

下一事件可以来自三个阶段：

1. Market Read 尚未解决：等待区域接受、拒绝或 Control 变化；
2. Opportunity 尚未 Activation：等待预先声明的 follow-through、第二次测试或结构破坏；
3. Opportunity 已 Activation，但当前没有正方程：只有 Decision Expiry 前存在明确、现实的更好价格或新 Candidate 事件时才等待。

Decision 只有在没有 Candidate、但存在 `Next Event + Decision Expiry` 时才输出 Wait。缺少现实下一事件，或空间、时间、风险已经排除当前机会时，输出 No Trade。只在 Wait 需要跨事件持续跟踪时，才保存这两个边界。

等待不保留隐藏的可执行计划。未来事实发生时使用新的判断时点重新计算；已经提交并等待成交的 Stop / Limit order 属于执行状态，不属于等待决定。

Decision 一次只冻结一份 Trade Plan。Breakout Mode 等双向条件先等待实际突破、失败或其他预先声明的事件，再以新的判断时点重读双向机会并构造一条单侧 Candidate。

### 不交易

Market Read 没有现实问题、两侧均被排除、Opportunity 已失效，或现实 Target、剩余时间、风险、成本和执行条件使当前 Outcome Horizon 内既不存在 Candidate 也没有值得等待的事件。以后若出现新的相关市场事件、Active Test 或 Reframe，从最早发生变化的步骤重开，重新建立 Opportunity 与 Trade Plan，不复用旧计划。

### Decision Record 与 Trade Plan

需要跨事件跟踪的 Wait，以及[总流程规定的少数重要 No Trade](overall_flow.md#六必要记录)，保存一份最小 Decision Record。普通扫描得到 No Trade 不记录；Execute 直接把被选 Candidate 冻结为 Trade Plan。

```text
Decision Record

时点 + 品种/周期：
决定：Wait / No Trade
Long / Short 结论（一短句）：
Wait：Next Event + Decision Expiry
重要 No Trade：排除原因
```

Execute 的最小保存字段直接使用本页上一节的普通 Trade Plan；复杂计划只按对应条件展开额外字段。概率或 Rule Match 只有在它们实质决定当前方程或用于样本校准时保存；若 Market Probability 与 Candidate Outcome Probability 因 Protective Stop、部分退出或管理方式而实质不同，复杂计划或复盘中再分别保留。Wait 后形成 Execute 时，保留原 Wait 时点与下一条件，追加新的判断时点并冻结 Trade Plan。执行阶段只在原 Trade Plan 追加实质改变的计划/风险 Delta 和必要执行事实。

## 十五、证据追溯

本页依据 [课程概念索引](../reference/course/concept_index.md)、[重复矩阵](../reference/course/repetition_matrix.md)、[边界与冲突](../reference/course/boundaries_and_conflicts.md)、[正式来源台账](../reference/official_sources.md)和逐讲材料对概率、风险、订单、目标和管理关系进行条件化整理。Reference 负责证据；本页负责统一决策契约。
