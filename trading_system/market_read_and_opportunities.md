# Market Read 与 Opportunity

> **状态：Trading System / Market Model**

本页定义 `Market Read = Context + Price Map + Price Process` 怎样从连续价格事实形成，以及它怎样生成可证伪的双向 `Opportunity Set`。Price Process 在实盘中按 `Current Move → Active Test` 读取；连续运行时先继承当前有效 Context，再以位置、运动和测试的新事实确认或重构它。首次看图或 Reframe 可从暂定分类或 `UNCLEAR` 开始。

本页是系统知识与内部模型，不是盘中标注任务。下文的区分首先是语义边界；交易者通常只需观察或心中确认，记录负担由[总流程](overall_flow.md#六必要记录)规定。

## 一、统一价格命题

市场不断在旧公平区域与可能的新公平区域之间测试：

```text
方向运动创造分离
→ 回调或反向尝试检验分离
→ 新区域获得接受：控制保持或建立，价格寻找下一目标
→ 分离被关闭：控制减弱，价格返回旧区域或进入双边状态
→ 反方在另一侧获得接受：旧路径失效，结构重新分类
```

这些知识分别描述价格组织、事件、结构、次序、空间、行为或外层功能，但都通过这条共同测试链进入运行系统。

## 二、价格行为知识融合契约

所有进入 Market Read 的价格行为知识都使用同一条运行链，不建立 Pattern、Setup 或 Concept 的平行路线。每项知识必须满足五个维度：

```text
1. Formation：由哪些可观察事实形成；使用什么周期与观察窗口？
2. Role / Owner：在价格组织、位置、过程、结构、次序、外层功能或行为中承担什么职责；改变哪个 Market Read 对象？
3. Derivation：可以直接形成哪些 Region、Pressure / Test / Context、目标、Rule Match 或 Opportunity；通过共同链最终可能影响哪些 Candidate 或动作？
4. Lifecycle：什么确认、增强、削弱、失效、替代或重置它？
5. Boundary / Dedup：它不能单独推出什么；哪些关系同源；什么才算新的独立事实？
```

这是价格行为知识的维护与去重契约，不是实盘逐项 Checklist，也不把 Candidate、风险或执行动作的定义移交给 Market Contract；这些下游对象仍由 Decision Contract 与 Execution Contract 唯一定义。

不能给出 Formation、Owner 和更新边界的价格行为名称，不进入运行系统。包含最终结果的名称必须区分实时候选和事后确认；不同目标、周期、Outcome Horizon 或判断时点不得因名称相同而合并。

底层事实只登记一次，但可以沿共同链路产生多个不同后果：

```text
一组 K 线、运动与区域互动事实
→ Current Move：Pressure / Continuity / Separation
→ Active Test：结构、次序、Response、Acceptance / Failure
→ Price Map：结构锚点、Neckline、边界与事前固定投射
→ Context：正常回调、目标、Control 或状态是否改变
→ Opportunity：Activation、Invalidation、Market Target 与路径强弱
→ Candidate：是否采用其中的 Signal、Region、Trigger、Stop 或 Target
```

这些是同一事实的不同运行后果，不是多个独立理由。汇合判断时，不得把同一来源价格链派生出的名称、Pressure、结构角色、Signal 和目标重新当成多个来源；不同区域、独立后续反应、真实 follow-through 或新的测试才可能增加事实。

概念之间常见以下关系；它们可以同时成立，不是互斥分类：

| 关系 | 保留的差异 | 示例 |
| --- | --- | --- |
| 本质归属 | 阶段与上位状态 | 当前周期被判定为方向 Trend 时，Channel 是其阶段 |
| 同源但职责不同 | 共用底层事实，分别保留结构、次序、位置、目标或图表角色 | Double Bottom 与 H2 可以重合；前者保留测试结构、锚点和 MM，后者保留恢复次序、Signal / Trigger |
| 外层角色 | 局部结构在另一周期或路径中的功能 | Rising Channel 同时可以是外层 Bear Flag |
| 条件演化 | 同一过程在新事实后更新状态和适用规则 | Breakout Attempt → Acceptance 或 Failed Breakout |
| 周期展开 | 同一价格在不同尺度形成不同结构与目标 | 高周期 Breakout Bar 在低周期展开为 Channel / Range |

Pattern 是对价格事实之间结构、过程或外层功能关系的压缩描述，不只是几何名称，也不是交易类别。结构若产生持续的运行结果，只把结果落入现有对象：锚点和投射进入 Price Map，当前互动进入 Active Test，目标与失效进入 Opportunity，Signal / Trigger 是否用于承担风险由 Candidate 决定。结构名称不建立并行记录对象。

## 三、原始价格事实

### 外部信息的边界

价格运动的任何表示都属于价格行为。Volume、DOM、新闻、NYSE TICK 等辅助指标和日程事件可以作为背景、流动性、时机或尾部风险输入，却不能独立保证方向；运行证据仍是这些信息怎样反映在突破、跟随、回调、接受或失败上。产品报价、pip、tick、保证金、rollover 和平台机制属于外部产品事实，只通过成本、仓位、订单和风险边界进入系统。已知事件、波动和流动性约束由 Frame 处理；数据、连接、订单或保护异常由 Execution State 处理。

### K 线几何

设本根最高、最低、开盘、收盘为 `H`、`L`、`O`、`C`：

```text
总范围   = H - L
实体     = abs(C - O)
实体占比 = abs(C - O) / (H - L)
收盘位置 = (C - L) / (H - L)
上影占比 = [H - max(O, C)] / (H - L)
下影占比 = [min(O, C) - L] / (H - L)
```

`H = L` 时按零波幅 K 线处理，不计算比例。观察还包括：

- 方向、开高低收和相对附近 K 线的范围与实体大小；
- 与前一根、突破区域和局部结构的共享价格范围；
- 高低点相对前高前低的变化；
- 实体、影线和收盘变化是否具有连续性。

Trend bar 与 trading-range bar 是连续谱。实体相对大、影线较小、收盘靠近方向端点时更像 trend bar；小实体、大影线和重叠增加时更像 trading-range bar。单根 K 线不能建立趋势。

其他几何只承担局部描述：

- `Inside bar`：`high ≤ 前高` 且 `low ≥ 前低`；一端相等仍可成立；
- `Outside bar`：来源对相等边界存在不同口径，运行或标注必须预先声明使用严格越过还是允许两端相等；
- `Doji`：实体相对周围很小或为零；
- `Shaved`：实体一端与本根极值严格相等；若允许一跳容差必须另行声明；
- `Reversal bar`：相对当前 trend / leg 承担反向趋势或拒绝角色，必须结合方向、收盘、相对实体、位置和后续反应；
- `Two-bar / multi-bar reversal`：由两根或多根共同完成反向压力，不能用单一吞没几何覆盖全部课程用法。

几何名称不生成方向优势。强趋势中的顺势弱 bar 仍可能表达有效路径，错误位置的漂亮 reversal bar 也不能修复目标和交易方程。

### 价格运动

- `Push / Leg`：较大结构中一段具有方向的运动，不自动构成独立 Trend。
- `Pullback`：当前方向运动中的暂停或暂时反向运动；反向运动获得足够接受并改变结构后，不能继续只称旧趋势回调。
- `Pause`：停止扩展趋势方向极值或形成横向停顿。
- `Actual pullback`：当前周期已满足高低点反向运动的几何事实。
- `Implied pullback`：当前周期的停顿角色；在较低周期常已展开成实际回调，不能改写当前周期几何。

第二段是条件路径倾向：第一段足够强并使参与者期待延续时，市场常再尝试一次。第二段可以很短、横向、未创新极值或很快失败；它不保证 `Leg 1 = Leg 2`，也不同于 second signal、second entry 或第二次实际成交。

### 参照区域

系统把以下对象视为区域而非精确屏障：

- 前高低、swing high / low、日周月已经形成的 OHLC；
- 区间边界、中部和内部公平区域；
- 突破点、旧结构起点和可见入场区域；
- 趋势线、通道线、EMA、大整数位；
- gap 边界和已固定结构生成的 measured-move 区域。

Support 位于当前价格下方，Resistance 位于当前价格上方；穿越后可以交换角色。位置本身不保证反转或突破。

多个来源相对独立的区域在相近价格与时间汇合，可以称为 confluence / Dueling Lines。若两条线由同一组 swing 推导，或旧高、区间上沿和 double-top 只是同一位置的不同名称，它们仍是一份位置证据。

汇合的运行作用取决于当前 Opportunity：当前价格处的多项支撑/阻力汇合可以增强停顿或反应倾向；前方多个事前固定投射汇合，可以增强目标区的 magnet 与到达后反应意义。它们都不单独生成 Entry，也不替代实际 rejection、breakout、follow-through、目标空间和当前 Market Probability。

### Price Map

相关区域进入同一张位置地图；同一价格带先合并，再按当前价格上方、下方和距离排序。当前运动正在到达、穿越或离开的区域优先进入 Active Area：

```text
Price Map
├─ Current / Active Area
├─ Above Price
│  └─ Region + Sources + Distance + Confluence
├─ Below Price
│  └─ Region + Sources + Distance + Confluence
└─ Nearest Relevant Area / Available Space：Up / Down
```

地图只唯一登记价格带、来源、汇合与距离。Active Area 是当前正在互动的区域；Potential Entry Area、Support / Resistance、Obstacle、Magnet、Target 和 Invalidation Reference 是相对某条 Opportunity 的运行角色。因此同一 `50%`、EMA 或旧高可以是一条机会的 Target，同时是另一条机会的 Potential Entry Area 或 Invalidation Reference；底层仍只保留一个价格带。Acceptance 与 Re-entry 属于 Price Process 事件，不是区域属性。

区域在以下任一条件成立时进入当前地图：价格正在互动；它是当前 Trading Timeframe 与 Frame 时间边界内的现实目标或障碍；它会改变正常 Stop、Invalidation、空间或动作；它是当前 Context 必须保留的外层约束。其他历史高低保持休眠，接近或获得新职责时再激活。

结构拥有独立下游用途时，其可见锚点和派生区域也进入同一地图。例如 Double Bottom / Top 可以登记两个测试区域、Neckline 与端点固定后的高度投射；Range、Breakout、Channel、Wedge 或 Leg 关系可以登记相应边界和 measured-move 候选。底层结构仍只使用一次，Opportunity 再为这些 Region 分配 Target、Obstacle、Potential Entry Area 或 Invalidation Reference 角色。

## 四、Price Process｜先读当前运动，再读活动测试

Price Process 保存前后关系，不把当前 K 线、位置反应或形态从其来源运动中截断。实盘分两步读取，内部仍属于同一连续过程。

### Current Move

```text
From：此前的方向运动、回调或区域反应
Now：UP_LEG / DOWN_LEG / PAUSE / LOCAL_BALANCE
Role：CONTINUATION / PULLBACK / RANGE_LEG / REVERSAL_ATTEMPT / UNRESOLVED
Bars：实体、收盘、影线与相对大小
Continuity：同向连续性与 follow-through
Separation：gap / breakout separation 与 overlap
Pullback：深度、持续时间、gap 与恢复速度
Opponent：反方 K 线质量、跟随与失败尝试
Result：Bull Pressure 变化；Bear Pressure 变化；Control 含义
```

Now 与 Role 分开：同一段 Down Leg 在多头方向状态中可能承担 Pullback 角色，在 Trading Range 中可能只是 Range Leg。`PAUSE` 尚未形成清楚方向段；`LOCAL_BALANCE` 表示局部小区间已经比单段或暂停更能组织价格。反向运动获得持续接受并改变外层正常回撤、目标或管理方式后，Role 才升级为新的 Context。

同一根或同一组 K 线不跨层复制为多份证据，而是沿既有对象产生不同后果：

```text
Bar Facts：实体、收盘、影线、相对大小和与前后价格的关系
→ Current Move：Pressure、Continuity、Separation、Pullback、Opponent
→ Active Test：Response、Attempt、Follow-through、Acceptance / Failure
→ Opportunity：对 Long / Short 的 Activation、增强、削弱、失效或目标完成
→ Candidate：只有被当前机会采用时，才成为 Entry Basis 的一部分
→ Execution：Chart Trigger、Actual Fill、持仓动作和账户事实
```

前层识别事实，后层引用同一事实的运行影响；一根强 K 线使 Pressure、Acceptance 和某条 Opportunity 同时改变，不表示获得三份独立证据。普通观察先停在 Current Move / Active Test，只有路径或动作因此改变时才继续传播。

### Active Test

Current Move 与 Price Map 的互动形成当前要解决的问题：

```text
Object：正在测试哪个区域、边界或旧 Control
Tested Objective：当前运动试图在 Object 完成什么
Phase：APPROACH / TOUCH / REACTION / BREAKOUT_ATTEMPT / FOLLOW_THROUGH
Resolution：PENDING / ACCEPTED / FAILED
Attempt：绑定当前 Object 与逻辑的测试次序；适用 H/L 时分开已完成 Trigger 与正在形成的下一恢复 setup / boundary
Response：可并存的分离、拒绝、突破、重叠或重新进入旧区域
Acceptance Criterion：哪些价格事实完成 Tested Objective
Failure Criterion：哪些价格事实否定 Tested Objective
Next Observation：下一项值得观察、并使测试接近接受或失败的增量事实
Test Expiry：最迟何时当前问题仍有意义
```

每个 Active Test 只表达当前真正驱动下一步的一个市场问题，Object、Tested Objective 和当前判断周期共同限定尺度。`ACCEPTED / FAILED` 始终回答该 Tested Objective，不能只写一个没有方向和对象的“接受/失败”。Acceptance / Failure Criterion 定义终局；Next Observation 只指出最近的增量，并在它成为最早流程变化条件时由 Watch、Activation 或 Decision 引用。外层位置由 Object 引用 Price Map；局部第二次测试、双底、双顶或三推在这里保存其当前结构、Attempt 次序与 Response，并可形成恢复 setup、潜在 Trigger Boundary、Neckline 或其他结构边界。结构端点固定后产生的投射进入 Price Map / Market Targets；课程图表语言可以把定义触发边界的完成 K 线称为 signal bar。Opportunity 决定这组事实是否支持现实路径，Candidate 再决定是否把其中的 K 线、Region、结构边界或确认过程用于 Entry Basis。

Active Test 若识别出新的结构锚点、边界或固定投射，先登记到同一 Price Map。若它改变 Object、Space、Target 或 Invalidation Reference，就从最早受影响步骤重新传播；若没有改变下游判断，则继续进入 Context Update，不建立第二张地图或独立结构对象。

Test Expiry 是当前问题的终止边界，不是第四种 Resolution。到期、被替代或已经解决后终止旧 Test：若新区域或运动已经形成现实问题，从最早变化步骤建立新的 Active Test；若只有明确下一事件则进入 Wait 判断；若没有新问题或值得等待的事件则进入 No Trade。只有另一个价格问题会独立改变目标、正常波动、失效或动作时才建立新的 Active Test，不维护通用主次或嵌套层级。

所有边界互动按同一顺序更新 Phase，并单独更新 Resolution：

```text
Approach
→ Touch / Overshoot
→ Reaction 或 Breakout Attempt
→ Follow-through / No Follow-through
→ Resolution：Accepted / Failed / Pending
```

- `Approach`：正在接近区域，尚未触及。
- `Touch / Overshoot`：触及或短暂越过，只确认测试事件发生。
- `Reaction`：停顿、拒绝、反向或加速，结果仍可能缺少延续。
- `Breakout event / attempt`：高低点越过重要边界；此时新区域是否被接受仍未知。
- `Follow-through`：初始运动后，后续一根或多根继续延伸。
- `Accepted`：边界外收盘、跟随、保持在外或回踩守住等证据支持新价格；它是测试结果，不直接许可交易。
- `Failed`：原目标路径未获得接受并被新价格实质否定；必须明确失败的是哪个 move 或 objective。
- `Pending`：当前 Object 与双向结果条件已经明确，但结果尚未发生；它不是另一个 Phase。

没有立即 follow-through 会削弱路径，但普通回调不自动确认失败。Failed breakout 要求旧区域被重新接受；若反向尝试随后失败、原突破方向重新获得接受，则形成 failed failure / breakout-pullback 路径。

### Attempt、Geometry 与 Response

`Attempt` 记录同一周期、Object 与恢复逻辑中已经发生的方向恢复触发，并指出当前是否正在形成下一次触发边界。H/L 编号描述触发次序，不是 K 线几何，也不是尚未越过边界时已经完成的交易：

```text
牛向恢复
完成的第一次向上 Trigger → H1
回调继续，新的已完成 K 线定义第二次向上边界 → H2 recovery setup；课程称该完成 K 线为 H2 Signal Bar
价格越过该 K 线高点 → H2 Trigger；越界所在 K 线为 Chart Entry Bar

熊向恢复
完成的第一次向下 Trigger → L1
回调继续，新的已完成 K 线定义第二次向下边界 → L2 recovery setup；课程称该完成 K 线为 L2 Signal Bar
价格跌破该 K 线低点 → L2 Trigger；越界所在 K 线为 Chart Entry Bar
```

H2 / L2 recovery setup 提供潜在触发边界。定义边界的完成 K 线在 Brooks chart language 中分别是 H2 / L2 Signal Bar，即使最终没有值得下单的 setup；运行 Checklist 不要求交易者因此扫描或优先标记 Signal Bar。Opportunity 与 Context Permission 先判断该位置、结构和方向是否值得表达，Candidate 再从 Signal Bar、multi-bar response、Region、breakout close 或其他已经完成的必要事实中形成最小 Entry Basis。图表 Trigger 是否发生与账户是否实际成交仍由后续价格和 Execution 分开确认。Market / close entry 可以使同一根 K 线同时承担 Signal Bar 与 Chart Entry Bar。

H1 / H2 / H3 与 L1 / L2 / L3 使用完全镜像的过程语言：

```text
第二次向上恢复
├─ 次序：H2 Setup / Trigger
├─ 两次下探近似区域：Double Bottom
├─ 外层多头延续仍有效：Bull Flag
└─ 旧空头结构已受破坏：MTR Component

第二次向下恢复
├─ 次序：L2 Setup / Trigger
├─ 两次上探近似区域：Double Top
├─ 外层空头延续仍有效：Bear Flag
└─ 旧多头结构已受破坏：MTR Component
```

在 Brooks 的功能语言中，Double Bottom 常与 H2 buy setup 重合，Double Top 常与 L2 sell setup 重合；Wedge Bottom / Top 也可与 H3 / L3 恢复过程重合。这些不是完全等价的名称：Double Test 保留测试结构、区域、Neckline 与可能的高度投射，H/L 保留恢复尝试次序、Signal Bar、Trigger 和 Chart Entry 关系，Wedge 保留三推、倾斜、推进质量及其外层 Flag / Climax 作用。严格实时标注仍须绑定同一计数窗口：Double Test 可以在 Trigger 前形成；H/L 边界只有被实际越过后才成为完成的 Trigger；严格 second entry 还要求第一次 chart entry opportunity 已经触发。它们可以共用底层事实，但各自不可替代的运行职责必须保留。

Wedge 描述三次可区分的推动或测试；H3/L3 描述第三次恢复触发。Wedge 可以是趋势回调中的 Flag、成熟通道末端的 reversal candidate，或 Trading Range 中没有优势的局部结构。只有观察尺度、倾斜方向、三推、Context、位置和目标满足具体规则时，才能匹配倾斜 Wedge 的方向先验；接近水平的成熟结构仍按 Triangle / Range 条件处理。三推不单独确认 Broad Channel，后者仍要求深而反复的回调、重叠增加和双边逐渐能够获利。Parabolic Wedge 是 Tight Channel 中至少三次 surge 构成的高潮式三推；没有反向接受时，第一笔反向运动通常仍只是 minor correction 或 Range 路径。

H4/L4 及更高编号首先要求重读 Context：当前过程可能已经成为 Triangle、Trading Range、endless pullback 或新趋势。局部重计和全局累计必须绑定明确周期、Object 与重置点，不能在结果出现后选择更漂亮的计数。

Triangle、ii、ioi 与 oo 描述局部平衡的几何。Triangle 可以按多次反转，或一侧三推且总体至少五段理解；不同来源和观察尺度会改变计数，运行只使用当前明确边界，不做机械换算：

- `ii / iii`：连续 inside bars，表示压缩；
- `ioi`：inside–outside–inside；
- `oo`：连续 outside bars，表示双边扩张；
- Triangle：成熟双边测试与压缩；Expanding Triangle 则逐步扩张两侧极值。

它们统一进入“平衡 → 实际突破 → follow-through → 守住或重新进入”的测试链。Flag 只说明 pullback、channel 或局部 balance 在外层 continuation / reversal 中的作用；Final Flag 在顺势恢复失败和后续结果出现前只能是候选。Broad Channel、Trending Trading Range、Triangle、H/L 或 Flag 若来自同一运动，只保留各自承担的过程职责，不按名称增加概率。

第一次逆势尝试默认先按 minor reversal、修正或 Trading Range 路径处理；只有后续过程破坏旧结构并建立反方接受，才升级为更大反转。MTR 同样附着于 Active Test，而不是另一套交易方法：

```text
成熟趋势
→ 趋势线或主要结构被破坏
→ 原趋势测试旧极值
→ 测试失败或形成 HL / LH
→ 反方 Trigger 并尝试建立 swing
→ 强反向 breakout 与 follow-through 进一步确认控制转移
```

约五根强反向 K 线或约十根普通 / 较弱反向 K 线，只是比较反向压力强度与持续时间的启发式；一两根足够强的 surprise 也可能更快改变控制。Wedge、Double Top/Bottom、Head and Shoulders、rounding top/bottom、Final Flag 或 Climax 可以描述其中组件，不能替代结构破坏、旧极值测试和后续接受。旧趋势重新建立控制、新 breakout 获得接受、成熟区间切断旧运动、主要结构被替换或观察周期改变时，旧 H/L、段数和反转组件重置。

### Process Question

Price Process 最后把 Current Move 与 Active Test 压缩成一句双向问题：

```text
当前运动从哪里来，质量怎样？
正在测试哪个区域；此前完成了几次恢复 Trigger，当前是否形成新的 H/L recovery setup 与潜在边界？
当前 Response 是什么几何或 K 线事实；它承担什么外层作用？
怎样算在外侧获得接受？
怎样算拒绝、失败或重新接受旧区域？
Next Observation 和 Test Expiry 是什么？
```

例如：`强空头段第三推延伸缩小，反弹后第二次下探卖压更弱；旧低下方会获得接受，还是多头先建立修正？`

价格进入新区域或 Context 重新分类时，新的 Current Move / Active Test 取代旧问题；旧结构只保留对新目标或正常回调仍有作用的部分。Active Test 形成 Response、恢复 setup 与潜在 Trigger Boundary；是否把某根 K 线、区域或确认过程选作 Entry Basis，使用哪种订单以及账户是否成交，由 Opportunity、Candidate 与 Execution 继续完成。

发生关键变化时，用[市场决策事件导航](market_decision_events.md)确定只需重开哪些步骤。事件卡压缩常见过程，不拥有独立状态、概率或入场许可。

## 五、压力与状态更新

每个相关事件先更新 Price Map、Current Move 或 Active Test，再汇总 Pressure / Control：

```text
新的区域、运动或测试事实
→ Bars：实体、收盘、影线与相对强度
→ Continuity：同向连续性与 Follow-through
→ Separation：Gap 保持/关闭与 Overlap
→ Pullback：深度、持续时间、Gap 与恢复速度
→ Opponent Response：反方 K 线质量、跟随与失败尝试
→ Bull Pressure 变化 + Bear Pressure 变化
→ Bull / Bear / Balanced / Unclear Control
→ 确认原 Context、标记 Transition 或 Reframe
→ Long / Short Opportunity 或 Likely Sequence 是否改变
```

使用能回答当前过程的最小时间窗口：当前段、当前区域测试，或上次 Reframe 以来。更早或更高周期事实留在 Context，不混入眼前 Pressure。

事实按来源价格链合并。一个强突破产生的大实体、强收盘、gap、Pressure、Control 和 Acceptance 可以影响机会的多个环节，但仍只是一条价格链。新的二次测试、后续 follow-through、反方尝试失败或独立价格区域才可能提供增量。

### Separation / Gap

Gap 的最低职责是描述两个价格对象之间是否保持分离。识别 Gap 时必须明确比较对象和边界：

- 完整范围 gap；
- body gap；
- micro gap；
- breakout point 与回调之间的开放、negative 或 overlap gap；
- 整根 K 线未触及 EMA 的 moving-average gap bar；
- session opening gap 或单根 `open` 相对前 `close` 的 Gap Open Bar。

这些名称不能互换。完整、实体、微型和 EMA 分离若来自同一次运动，只属于一个 Separation 证据组。运行更新使用：

- `NOT_RELEVANT`：当前窗口没有需要评价的分离关系；
- `NOT_PRESENT`：比较对象明确，但当前没有开放分离；
- `EXPANDING / HOLDING / CLOSING / CLOSED`：已经存在或刚刚关闭的分离怎样变化。

`CLOSED` 保留“先前存在、现在关闭”的事件语义；初始化时本来就没有 gap 使用 `NOT_PRESENT`。两者都要结合旧区域是否重新获得接受解释。

```text
Gap 保持且跟随良好
→ 原方向分离与控制增强

完整 gap 关闭但 body gap 保持
→ 原方向减弱但未失败

所有分离快速关闭并重新进入旧区域
→ 延续路径削弱，通道化或区间化增加

关闭后反方获得跟随
→ 原突破路径失效或重新分类
```

Measuring gap 与 exhaustion gap 含有事后结果。实时只能记录 candidate measuring gap 或 potential exhaustion；前者需要后续 measured move，后者需要后续停止延续、区间化或反转结果。Gap 不因“迟早回补”自动成为目标。

Moving-average gap bar 的两个常见语境不能混用：整根 K 线位于 EMA 反侧是严格几何；长期约 20 根未触 EMA 后的首次测试则是时间与趋势背景。前者可以增加反方压力，后者常仍保留原趋势测试旧极值的路径；两者都不机械生成 Entry。

### Pressure / Control / Always In

Bull / Bear Pressure 分别汇总同一段窗口中的可观察事实：

- 顺势 K 线、实体和强收盘的数量与连续性；
- 反向影线和失败尝试；
- breakout、gap、follow-through 与是否快速收回；
- pullback 深度、持续时间和恢复速度；
- 反方能否获得 scalp 或持续路径。

同一根 K 线的“大实体、强收盘、顺势 K 线”不能算成三个独立理由。每次更新分别回答两侧是增强、保持、减弱还是尚未建立；一侧减弱不自动等于另一侧建立。Pressure 是事实簇的方向汇总；一侧明显占优才支持 Control，控制足够强时才支持 Always In。Always In 不是必须持仓，也不能替代位置、目标和交易方程。这是观察输出，只有它改变 Opportunity、计划或动作时才记录。

通常需要足够强的反向运动和跟进改变 Always In。单根异常强反转只有在方向、相对强度、重要位置和对旧控制的否定同时清楚时，才可能直接完成切换；普通反色 K 线不够。

### 行为路径模型

Trapped、Disappointment 与 Pain Trade 是由价格路径支持的参与者行为推断，不是可直接观察的账户身份或持仓数量：

- `Trapped in`：图表曾给出一方可见的入场机会，该方向没有先完成其价格结果，随后持续处于不利路径；系统只推断部分参与者可能被困并形成退出压力；
- `Trapped out`：等待更好价格、过早退出或错过重新参与的一方，随后面对价格加速；系统只推断其追入或放弃等待的潜在压力；
- `Pain Trade`：上述两类潜在反应共同推动低预期方向的行为路径。

该模型必须由可见 Entry / Stop 区域、failure、follow-through 与现实空间支持，只更新 Opportunity 的 Support、Counterevidence、Activation 或结果路径，不建立独立 setup、状态或概率。若推断来自已经登记的 Entry、failure 或 follow-through，它不再增加证据；后续独立发生的回测、跟随或加速才作为新事实更新一次。实际参与者是否入场、退出或亏损仍不可由图表证明。

### 从事件到状态转换

证据增强或削弱不一定立即改变外层状态。只有新事实开始改变正常回撤、目标、两侧获利能力或管理方式时才重分类：

| 当前外层状态 | 累积的新事实 | 状态更新 |
| --- | --- | --- |
| Breakout / Spike | 出现第一次可识别回调，分离仍较好 | Tight Channel |
| Breakout / Spike | gap 缩小或关闭、Overlap 增加，但尚无完整回调 | 原状态减弱；标记 Transition，不抢先改名 |
| Tight Channel | 回调反复加深、穿回突破点，双边开始获利 | Broad Channel |
| Broad Channel | 相邻突破与回调重叠、延伸缩小 | Staircase / shrinking-stairs 视图；区间化增强 |
| Broad Channel | 局部区间经短突破迁移到新区间 | TTR 可以成为主导状态；若仍由方向 swing 支配，只作同源视图 |
| 任一方向状态 | 双方持续在同一公平区域获得接受，单边控制无法保持 | Trading Range |
| Trading Range / Breakout Mode | 强突破、跟随并守住区间外 | Breakout / Spike |
| Trading Range | 突破尝试后重新接受旧区域 | 保持 Trading Range，测试记为 FAILED |

这张表规定转换条件，不规定机械根数，也不是不可逆的单向周期。

## 六、Context｜继承后由当前过程确认

Context 只保存当前交易周期真正支配目标、正常回撤和管理方式的价格组织：

```text
Context
├─ Operating State
│  ├─ BREAKOUT_SPIKE
│  ├─ TIGHT_CHANNEL
│  ├─ BROAD_CHANNEL
│  ├─ TRENDING_TRADING_RANGE
│  ├─ TRADING_RANGE
│  └─ UNCLEAR
├─ Direction：BULL / BEAR / BALANCED / UNCLEAR
├─ Range Condition（仅 TRADING_RANGE）
│  ├─ Width：TIGHT / BROAD / UNCLEAR
│  └─ Maturity：DEVELOPING / MATURE / UNCLEAR
└─ Conditions：[NONE，或可并存：BREAKOUT_MODE / CLIMACTIC_MOVE_CANDIDATE /
                CONFIRMED_CLIMAX / TRANSITION]
```

Operating State 在当前交易周期内只选择一个主导值。Range Condition 只在 `TRADING_RANGE` 下启用，不恢复跨状态的通用 Variant。Broad Channel 与 Trending Trading Range 同时可见时，选择真正决定正常回撤、目标与管理的一项，另一项只作同源视图。只解释某段过程的第三推、Wedge 或局部 Triangle 留在 Price Process；Session、剩余时间、事件和流动性约束属于 Frame。

连续观察中的 Context 是上一次确认结果，也是本次 Price Process 的比较基线；它不是无需复核的先验结论。普通新事实没有跨过正常回调、目标、Control 或双边获利能力边界时保持原值；跨过边界才按上节转换表更新。首次看图没有可继承状态时，先用相关窗口作暂定分类，无法确认就保留 `UNCLEAR`。

Context Update 是更新操作，输出 Updated Context 与相对基线的 `Context Change`：

- `INITIALIZED`：首次读取，没有可继承基线；
- `UNCHANGED`：运行职责没有变化；
- `UPDATED`：主状态未被替代，但 Conditions 或运行边界实质改变；
- `REFRAMED`：主导价格组织、方向、正常回调、目标或管理方式被替代。

不确定性直接保留在 Operating State、Direction 或 Range Condition 的 `UNCLEAR`，不与变化类型混合。`TRANSITION` 只作为 Updated Context 中持续影响 Permission 的 Condition；Context Change 不包含同义状态。

分类依据是回调深度和持续时间、Overlap、Separation 是否保持、双边获利能力，以及新旧公平区域是否仍在方向迁移。`UNCLEAR` 是允许结果；Overlay 只描述当前附加条件，不与 Operating State 并列计数。

### 方向状态

方向状态表示市场持续寻找更高或更低价格，一侧控制明显、反方尝试经常失败。Breakout / Spike 是接受证据已经建立方向控制且几乎没有回调的阶段；第一次可识别回调使当前状态进入 Channel，但不结束整个方向运动。

Channel 是 Trend 的方向结构：

- Tight Channel 回调浅、重叠少、分离保持，第一次逆势尝试通常先按 minor 处理；
- Microchannel 是没有明显回调、每根顺势极值持续推进的局部 tight-channel 表现；Small Pullback Trend 则持续以浅回调、保留 gap 或反方难以获利维持控制。两者只增强当前延续路径，不保证任意位置都值得入场；
- Broad Channel 回调更深、更久、常穿回突破点，双边逐渐都能获利；
- Staircase 表示相邻突破与回调开始重叠；shrinking stairs 表示连续延伸缩小，区间化证据增加；
- Trending Trading Range 强调“局部区间—短突破—新区间”的公平区域迁移。

Broad Channel 与 Trending Trading Range 可以是同一行情的两个观察视图：前者强调方向 swing 和深回调，后者强调局部平衡区迁移，只形成一份结构证据。

回调接近先前 leg 的一半可作为几何参照，但 `50%` 不是独立支撑或固定反转阈值。回调持续扩大为 endless pullback、反向 channel 或双边都能获利的区域时，应更新活动结构，而不是继续沿用“浅回调”名称。

Rising Channel 在当前周期属于多头趋势；同时保留其完整生命周期中向下突破趋势线并通常区间化的 Bear Flag 视角。若它位于外层空头趋势，本身直接承担外层 Bear Flag 角色。短期恢复旧高与长期向下突破属于不同 Outcome Horizon，不能放进同一交易方程；Falling Channel 完全镜像。

趋势线或通道线只是候选区域。轻微 overshoot / undershoot 不使结构自动失效；强越界、边界外收盘、follow-through 或旧线长期不再组织价格，才支持重画或重新分类。

### 平衡状态

Trading Range 表示市场围绕公平区域反复双向测试，双方都能获利而没有一侧持续控制。Range Condition 只保存会改变当前动作的两个维度：

- `Width = TIGHT`：barbwire 或压缩重叠多，通常缺少扣除成本后的目标空间；
- `Width = BROAD`：边缘可能生成路径，中部通常缺少优势；
- `Maturity = DEVELOPING`：前序方向和初始段仍可能明显约束测试与目标；
- `Maturity = MATURE`：价格已经反复双向测试公平区域，前序方向影响减弱，任一方向突破获得跟随的可能性上升；
- 强区间段可能只是 vacuum test，不因运动强就取得趋势突破后的延续概率。只有足够强的第一段已经合理建立第二段预期、第二段实际出现并吸引延续交易者，随后又无法在边界或目标外获得接受并反转，才使用“第二段陷阱”解释；它是这条失败价格链的过程视图，不另增证据或交易许可；
- 边界越过先记 breakout attempt，只有外部接受和控制形成后才更新为 Trend。

Width 与 Maturity 都是连续判断，`UNCLEAR` 是合法值；系统不使用固定根数或绝对点数强制分类。Breakout Mode 仍需双向突破可能性等当前事实，不能只由 `MATURE` 自动推出。

Limit Order Market 是从重叠、影线、反转尝试和双边获利等事件事实归纳出的行为条件，常见于区间、宽通道和弱趋势，不是新的 Context 状态。价格 touch / cross limit price 也不证明账户成交。

### Conditions：Breakout Mode、Climax 与 Transition

Breakout Mode 表示任一方向突破都有可能获得跟进；它常叠加在成熟 Trading Range、Triangle、ii、ioi、oo 或压缩上，不是 Trading Range 的同义词。由这些 Geometry Views 归纳出 Breakout Mode 不构成第二份证据。Breakout Mode 不预测方向，也不保证首次突破成功。

`CLIMACTIC_MOVE_CANDIDATE` 表示进行时的过快过远或异常强运动；`CONFIRMED_CLIMAX` 只在后续已经停止延续并进入区间或反向结构后成立。前者用于实时路径更新，后者用于已经发生的状态转换和复盘。Final Trend Bar、Final Flag、Give-up Bar 同样包含事后角色，实时只保存候选并观察 follow-through、剩余空间和反向接受。

回调加深、双边交易增加、趋势线突破、旧极值测试失败和顺势突破缺少跟随构成 transition evidence；单项线索通常不足以确认 opposite trend。

### 分类不清时的运行 fallback

- 方向状态与 Trading Range 分不清：按 Trading Range 管理；
- Breakout / Spike 与 Channel 分不清：按 Breakout / Spike 管理，只沿控制方向；
- Tight 与 Broad Channel 分不清：按 Tight Channel 管理；
- Broad Channel 与 Trading Range 分不清：先按 Trading Range 处理。

Fallback 只决定当前允许动作，不把未决事实写成永久标签。

## 七、多周期与时间范围

每个 Context、当前问题、Opportunity、目标和概率都绑定周期与观察窗口。同一价格在高周期可能是一根 breakout bar，在交易周期是 Tight Channel，在更低周期又展开成 Broad Channel 或 Range。

内部模型至少分开：

```text
Context
- Trading Timeframe、Relevant Outer Constraint 与已经确认的价格组织

Market Read
- Context、Price Map、Current Move、Active Test

Opportunity
- Direction、Role、Objective、Outcome Horizon、价格区域引用与结构失效

Trade Candidate
- 当前 Entry、Planned Stop、Target、Size 与管理
```

较小周期可以提前触发，但必须在承担风险前定义；成交后不能因盈亏情绪临时切换到更小噪声周期。小周期 Entry 若追求大周期目标，Stop、仓位和持有时间必须容纳大周期正常波动。

Session 只通过剩余时间、波动、流动性、目标可达性和是否允许跨 Session 进入路径。盘中只能描述实时 session state，最终 day type 不能回填当时判断。Opening、first swing、Opening Breakout Mode、first-18 heuristic 和内部固定 opening window 不是同一对象，使用时必须声明边界来源。

## 八、目标怎样生成

目标来自已经固定的结构、可见参照区域和当前正在解决的价格问题。它先是市场结果，不是交易者为了修复 reward/risk 而事后选择的退出价。

| 来源结构 | 候选目标事件 |
| --- | --- |
| Trend / Channel 内恢复 | 测试旧极值、通道边界或下一现实 magnet |
| Trading Range 边缘反应 | 返回内部公平区域、中部或另一侧 |
| Range / Pattern 突破并接受 | 测试按固定高度投射的 measured-move 区域 |
| 强 Breakout 与回调 | 尝试第二段、旧极值或 Leg 1 = Leg 2 |
| Failed Breakout | 返回旧结构、内部目标、中部或另一侧 |
| 通道反向突破并接受 | 通道起点或更大 Trading Range |
| MTR 路径 | 反向两段、旧公平区域或其他实际 swing magnet |

常见投射：

```text
Leg 1 = Leg 2：第一段 A → B，第二段起点 C，目标 = C + (B - A)
Range height：H = upper boundary - lower boundary
  向上目标 = upper boundary + H
  向下目标 = lower boundary - H
Double-bottom height = neckline - bottom area
Double-top height    = top area - neckline
```

所有端点必须来自当时可见的结构并冻结。Measured move 是目标候选，不提供入场许可；更近障碍、成本和剩余时间会改变现实 Reward。多个来源相对独立的投射落在相近区域，可以增强 target cluster 的 magnet 和到达后反应意义；同一结构的不同量法仍只属于一个来源族。

目标事件只定义市场结果：价格触及、进入区域、越过并获得接受，或在 Outcome Horizon 内未发生。账户是否实际成交退出属于 Trade Outcome 与 Account Result，不能写入 Opportunity 的市场目标。

## 九、从 Market Read 到 Opportunity Set

结构、位置与当前价格问题明确后，分别扫描现实 Long / Short 路径，不用一个“偏多/偏空”标签代替双方论证。双向扫描完成前不进入 Trade Construction：

```text
Opportunity
- Direction
- Role
- Outcome Horizon
- Objective
- Market Outcome Criterion
- Market Targets
- Support / Already：去重后的已发生价格事实链
- Activation：什么过程事实使机会具备交易表达资格
- Activation Status：MET / PENDING
- Invalidation：引用哪个 Region，什么市场事实真正否定机会
- Counterevidence：尚未由完整对手 Opportunity 表达的最强反方价格事实；没有则 NONE
- Market Probability
- Rule Match
- Opportunity Expiry
```

每一侧先得到一个 Side Scan Result，再只保存该结果需要的内容：

- `OPPORTUNITY`：保存上方完整对象；Activation 可以尚未满足；
- `WATCH`：只保存 Watch Next Event 与 Watch Expiry，不建立 Pending Opportunity；
- `EXCLUDED`：只保存 Exclusion Reason，不展开伪 Opportunity。

一个方向可以引用多张 Opportunity 卡。例如 Up / Correction 与 Up / Reversal，或同方向不同 Outcome Horizon，必须保持独立 Objective、Target、Activation、Invalidation、Probability 与 Expiry；Side Scan Result 只说明本侧是否至少存在一条完整路径。

新 K 线或价格事件不直接生成交易动作，而是先对每条现实路径形成一次 `Path Effect`：

```text
NONE / ACTIVATED
ACTIVE：STRENGTHENED / UNCHANGED / WEAKENED
ACHIEVED / INVALIDATED / EXPIRED / SUPERSEDED / MARKET_SEQUENCE_UNKNOWN
```

`ACTIVATED` 表示此前 Pending 的 Activation 已完成；增强、保持和削弱只适用于仍 `ACTIVE` 的 Opportunity；其余结果进入生命周期终态或替代状态。空仓时 Path Effect 决定是否进入 Trade Construction，持仓时同一结论与竞争 Opportunity 一起决定 Hold、Add、Reduce、Trail 或 Exit。K 线颜色、漂亮外观或单根反向反应不能越过 Current Move / Active Test 直接指定 Path Effect。

Context Control 提供 Permission 和先验，不替代另一方向的扫描。至少一侧为 `OPPORTUNITY` 才进入 Context Permission 与 Candidate 检查；只有 `WATCH` 时向 Decision 提交最早的 Next Event 与 Expiry；两侧均 `EXCLUDED` 时进入 No Trade 判断。

事实不必平均分布。一条机会可以由一条强而连贯的突破链主导，也可以由独立位置、对手失败和新跟随补全。关键是它们分别支持机会的背景、Activation、接受、持续或目标，而不是理由数量。

`Role` 只用来防止混合 objective 和 Outcome Horizon：continuation、correction、reversal、range return 或 balance breakout。趋势或回调中的突破按其外层职责归入 continuation / reversal；`BALANCE_BREAKOUT` 只表示从平衡状态向外建立新路径。例如强空头趋势中，`Up / Correction` 可先到 EMA 或 50%，随后 `Down / Continuation` 再测试旧低；两者可顺序成立。只有该顺序会改变当前选择或管理时才保存一句 `Likely Sequence`。`Up / Reversal` 则要求破坏空头控制并获得新方向接受，不能从短期修正目标直接推出。

Long 与 Short 两列天然互为竞争机会；Counterevidence 只保存尚不足以形成完整对手 Opportunity、但会削弱当前路径的价格事实。`Opportunity Expiry` 只规定当前 Objective 在 Outcome Horizon 内仍有意义的最迟边界；市场事实否定进入 `INVALIDATED`，新 Context 或价格问题取代进入 `SUPERSEDED`。

明显缺少现实目标、时间或空间的方向只保留排除原因，不为形式对称制造伪机会。双向扫描只提交 Side Scan Result、Next Event 或完整 Opportunity；`WAIT / NO_TRADE / EXECUTE` 由 Decision 唯一输出。

常见双向问题可以生成：

| 当前问题 | 一条现实 Opportunity | 对手 Opportunity |
| --- | --- | --- |
| 趋势回调 | 原方向恢复并测试旧极值 | 回调扩大、结构破坏或进入 Range |
| 区间边缘 | 拒绝边缘并返回公平区域 | 外部获得接受并启动突破目标 |
| Breakout pullback | 突破点守住并恢复 | gap 关闭、旧区域重新接受 |
| 通道边界 | 内部反应并继续通道运动 | 外部突破获得接受并重分类 |
| 旧极值、EMA 或量度区域 | 穿越并获得接受 | 拒绝并启动返回路径 |

机会随来源事实改变，不随名称数量改变。新的 Context、价格区域、Current Move 或 Active Test 可以替代旧机会；历史结构只在仍能改变目标、正常回调或管理时留在 Context。不同 objective 或 Outcome Horizon 分别表达，不用一个方向概率覆盖全部结果。

## 十、证据生命周期

```text
出现
→ 在当前周期、窗口和状态内有效
→ 因缺少跟随、重叠增加或关键区域被收回而削弱
→ 因目标路径被新事实否定而失效
→ 因新主导 breakout、成熟 Range、控制切换或周期变化而重置
```

削弱不等于立即失效；重置不否认历史发生，只说明旧事实不再支持当前 Opportunity。Pattern 演化、事后名称和旧概率都不能越过重置继续提供交易许可。

Opportunity 的生命周期与证据强弱分开：

```text
ACTIVE
├─ 目标事件发生             → ACHIEVED
├─ 市场事实实质否定         → INVALIDATED
├─ Outcome Horizon 结束     → EXPIRED
├─ 新 Context、价格问题或机会取代 → SUPERSEDED
└─ 目标与失效顺序无法确认   → MARKET_SEQUENCE_UNKNOWN
```

增强、保持和削弱是 `ACTIVE` 内一次事件的更新结果；Activation 只表示该机会可以进入 Context Permission 与 Candidate 检查，不等于交易许可，也不改变生命周期。是否可交易由当前 Trigger、Entry、Stop、交易结果概率、Reward、成本、时间和账户条件决定。

## 十一、证据追溯

本页的运行关系由以下 Reference 范围支持并接受其冲突边界：

- [课程概念索引](../reference/course/concept_index.md)：课程思想骨架和概念族覆盖；
- [跨讲重复矩阵](../reference/course/repetition_matrix.md)：同源视图、镜像、递进和低增量重复；
- [边界与冲突](../reference/course/boundaries_and_conflicts.md)：概率分母、术语口径、数学和翻译限制；
- [正式来源台账](../reference/official_sources.md)：正式资料身份与来源锚点；
- [逐讲课程材料](../reference/course/README.md)：具体条件、页码和案例证据。

Reference 只提供核验依据；本页负责系统中的形成条件、更新语义和运行职责。
