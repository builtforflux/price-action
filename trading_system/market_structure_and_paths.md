# 市场结构与结果路径

> **状态：Trading System / Market Model**

本页规定价格事实怎样生成活动结构、目标事件和 Market Path。概念名称只压缩已经观察到的关系；系统不按 Pattern 或 Setup 名称切换运行逻辑。

## 一、统一价格命题

市场不断在旧公平区域与可能的新公平区域之间测试：

```text
方向运动创造分离
→ 回调或反向尝试检验分离
→ 新区域获得接受：控制保持或建立，价格寻找下一目标
→ 分离被关闭：控制减弱，价格返回旧区域或进入双边状态
→ 反方在另一侧获得接受：旧路径失效，结构重新分类
```

Trend、Trading Range、Gap、Breakout、Failed Breakout、H2、Double Bottom、Wedge、Flag 和 MTR 都是这条测试链在不同周期、次序、空间或 Context 中的描述。

## 二、概念的形成契约

系统中的概念必须能够回答：

```text
来源事实是什么？
在什么周期与观察窗口形成？
它在当前流程中承担什么职责？
什么新事实会增强、削弱、失效或重置它？
它不能单独推出什么？
```

不能从价格事实给出形成条件、更新条件和流程职责的名称，不进入运行系统。包含最终结果的名称必须区分实时候选和事后确认。

概念之间只使用五种关系：

| 关系 | 含义 | 示例 |
| --- | --- | --- |
| 本质归属 | A 是 B 的一种 | Channel 是当前周期 Trend 的阶段 |
| 同源视图 | 同一事件从不同维度命名 | H2 与 Double Bottom 可以描述同一第二次测试 |
| Context 角色 | 局部结构在外层路径中的作用 | Rising Channel 同时保留长期 Bear-Flag 视角 |
| 条件演化 | 新事实改变当前解释 | Breakout Attempt → Acceptance → Breakout Phase |
| 周期展开 | 同一价格在不同尺度呈现不同结构 | 高周期 Breakout Bar 在低周期展开为 Channel / Range |

同源视图只产生一份证据。Context 角色可以同时成立，但必须分别保存周期、目标事件与 horizon。

## 三、原始价格事实

### 外部信息的边界

价格运动的任何表示都属于价格行为。Volume、DOM、新闻、NYSE TICK 等辅助指标和日程事件可以作为背景、流动性、时机或尾部风险输入，却不能独立保证方向；运行证据仍是这些信息怎样反映在突破、跟随、回调、接受或失败上。产品报价、pip、tick、保证金、rollover 和平台机制属于外部产品事实，只通过成本、仓位、订单和风险边界进入系统。数据中断、基础设施异常和已知事件风险进入运行边界与 Trade Plan，不因系统以价格反应为主而被忽略。

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

`H = L` 时记录为零波幅 K 线，不计算比例。还要记录：

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

第二腿是条件路径倾向：第一腿足够强并使参与者期待延续时，市场常再尝试一次。第二腿可以很短、横向、未创新极值或很快失败；它不保证 `Leg 1 = Leg 2`，也不同于 second signal、second entry 或第二次实际成交。

### 参照区域

系统把以下对象记录为区域而非精确屏障：

- 前高低、swing high / low、日周月已经形成的 OHLC；
- 区间边界、中部和内部公平区域；
- 突破点、旧结构起点和可见入场区域；
- 趋势线、通道线、EMA、大整数位；
- gap 边界和已固定结构生成的 measured-move 区域。

Support 位于当前价格下方，Resistance 位于当前价格上方；穿越后可以交换角色。位置本身不保证反转或突破。

多个来源相对独立的区域在同一价格附近相遇，可以称为 confluence / Dueling Lines。若两条线由同一组 swing 推导，或旧高、区间上沿和 double-top 只是同一位置的不同名称，它们仍是一份位置证据。汇合只增强 Location，不替代 reaction、目标空间和条件概率。

## 四、测试与接受的共同事件链

所有边界互动按同一顺序记录：

```text
Approach
→ Touch / Overshoot
→ Reaction 或 Breakout Attempt
→ Follow-through / No Follow-through
→ Acceptance / Failure / Still Pending
```

- `Approach`：正在接近区域，尚未触及。
- `Touch / Overshoot`：触及或短暂越过，只确认测试事件发生。
- `Reaction`：停顿、拒绝、反向或加速，结果仍可能缺少延续。
- `Breakout event / attempt`：高低点越过重要边界；此时新区域是否被接受仍未知。
- `Follow-through`：初始运动后，后续一根或多根继续延伸。
- `Acceptance`：边界外收盘、跟随、保持在外或回踩守住等证据支持新价格；它是证据状态，不直接许可交易。
- `Failure`：原目标路径未获得接受并被新价格实质否定；必须写明失败的是哪个 move 或 objective。

没有立即 follow-through 会削弱路径，但普通回调不自动确认失败。Failed breakout 要求旧区域被重新接受；若反向尝试随后失败、原突破方向重新获得接受，则形成 failed failure / breakout-pullback 路径。

## 五、分离、重叠、压力与控制

### Separation / Gap

Gap 的最低职责是描述两个价格对象之间是否保持分离。记录时必须写明比较对象和边界：

- 完整范围 gap；
- body gap；
- micro gap；
- breakout point 与回调之间的开放、negative 或 overlap gap；
- 整根 K 线未触及 EMA 的 moving-average gap bar；
- session opening gap 或单根 `open` 相对前 `close` 的 Gap Open Bar。

这些名称不能互换。完整、实体、微型、EMA 分离和突破接受若来自同一次运动，只属于一个分离证据簇。

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

Buying / Selling Pressure 汇总一段窗口中的可观察事实：

- 顺势 K 线、实体和强收盘的数量与连续性；
- 反向影线和失败尝试；
- breakout、gap、follow-through 与是否快速收回；
- pullback 深度、持续时间和恢复速度；
- 反方能否获得 scalp 或持续路径。

同一根 K 线的“大实体、强收盘、顺势 K 线”不能算成三个独立理由。Pressure 是事实簇的方向汇总；一侧明显占优才支持 Control，控制足够强时才支持 Always In。Always In 不是必须持仓，也不能替代位置、目标和交易方程。

通常需要足够强的反向运动和跟进改变 Always In。单根异常强反转只有在方向、相对强度、重要位置和对旧控制的否定同时清楚时，才可能直接完成切换；普通反色 K 线不够。

## 六、活动结构的连续演化

基础状态只分为 Trend 与 Trading Range。若为 Trend，再判断当前主要阶段：

```text
Breakout Phase / Spike
→ Tight Channel
→ Broad Channel
→ Trading Range
```

判断维度为：

- 回调深度和持续时间；
- 重叠是否增加；
- gap 或近似 gap 是否保持；
- 双边能否获利；
- 新旧公平区域是否仍在方向迁移。

Breakout Mode、climactic move、transition evidence、Limit Order Market 和 Session Context 是叠加信息，不是第三种基础状态。

### Trend 与 Channel

Trend 表示市场持续寻找更高或更低价格，一侧控制明显、反方尝试经常失败。Breakout Phase 是接受证据已经建立方向控制且几乎没有回调的阶段；第一次可识别回调使当前阶段进入 Channel，但不结束整个 Trend。

Channel 是 Trend 的方向结构：

- Tight Channel 回调浅、重叠少、分离保持，第一次逆势尝试通常先按 minor 处理；
- Microchannel 是没有明显回调、每根顺势极值持续推进的局部 tight-channel 表现；Small Pullback Trend 则持续以浅回调、保留 gap 或反方难以获利维持控制。两者只增强当前延续路径，不保证任意位置都值得入场；
- Broad Channel 回调更深、更久、常穿回突破点，双边逐渐都能获利；
- Staircase 表示相邻突破与回调开始重叠；shrinking stairs 表示连续延伸缩小，区间化证据增加；
- Trending Trading Range 强调“局部区间—短突破—新区间”的公平区域迁移。

Broad Channel 与 Trending Trading Range 可以是同一行情的两个观察视图：前者强调方向 swing 和深回调，后者强调局部平衡区迁移，只形成一份结构证据。

回调接近先前 leg 的一半可作为几何参照，但 `50%` 不是独立支撑或固定反转阈值。回调持续扩大为 endless pullback、反向 channel 或双边都能获利的区域时，应更新活动结构，而不是继续沿用“浅回调”名称。

Rising Channel 在当前周期属于 Bull Trend；同时保留其完整生命周期中向下突破趋势线并通常区间化的 Bear-Flag 视角。若它位于外层 Bear Trend，本身直接承担外层 Bear Flag 角色。短期恢复旧高与长期向下突破属于不同 horizon，不能放进同一交易方程；Falling Channel 完全镜像。

趋势线或通道线只是候选区域。轻微 overshoot / undershoot 不使结构自动失效；强越界、边界外收盘、follow-through 或旧线长期不再组织价格，才支持重画或重新分类。

### Trading Range

Trading Range 表示市场围绕公平区域反复双向测试，双方都能获利而没有一侧持续控制：

- Tight Trading Range / barbwire 重叠多、空间小，通常缺少扣除成本后的目标空间；
- Broad Trading Range 边缘可能生成路径，中部通常缺少优势；
- 强区间腿可能只是 vacuum test 或边缘第二腿陷阱，不因运动强就取得趋势突破后的延续概率；
- 边界越过先记 breakout attempt，只有外部接受和控制形成后才更新为 Trend。

Limit Order Market 是可观察的双边交易行为环境，常见于区间、宽通道和弱趋势，不是新的市场状态。价格 touch / cross limit price 也不证明账户成交。

### Breakout Mode、Climax 与 Transition

Breakout Mode 表示任一方向突破都有可能获得跟进，可以叠加在区间或其他当前状态上。Triangle、ii、ioi、oo 和压缩都可能承担该角色；它不预测方向，也不保证首次突破成功。

Climactic move / climax bar 是进行时的过快过远或异常强运动；严格的已确认 climax 需要后续已经停止延续并进入区间或反向结构。Final Trend Bar、Final Flag、Give-up Bar 同样包含事后角色，实时只能记录候选并观察 follow-through、剩余空间和反向接受。

回调加深、双边交易增加、趋势线突破、旧极值测试失败和顺势突破缺少跟随构成 transition evidence；单项线索通常不足以确认 opposite trend。

### 状态不清时的局部 fallback

- Trend 与 Trading Range 分不清：先按 Trading Range 处理；
- 已确认 Trend，但 Breakout Phase 与 Channel 分不清：先按 Breakout Phase 处理；
- 已确认 Channel，但 Tight 与 Broad 分不清：先按 Tight Channel 处理；
- Broad Channel 与 Trading Range 分不清：先按 Trading Range 处理。

Fallback 只处理当前未决层级，是保守运行假设，不是永久标签。

## 七、结构视图，而不是交易分类

### H/L、Double Test 与 Wedge

H1 / H2 / H3 记录同一牛向恢复逻辑中的第一、第二、第三次向上尝试；L1 / L2 / L3 镜像记录熊向恢复。计数必须绑定周期、当前 pullback / test 和重置条件。

```text
第二次向上恢复尝试
├─ 次序视图：H2
├─ 若两次下探测试近似区域：Double Bottom
├─ 若外层牛趋势仍有效：Bull Flag 角色
└─ 若旧空头结构已受破坏：MTR 测试组件
```

Double Bottom 只要求两次测试近似低位；成为 H2 还要求同一逻辑中的第二次向上尝试。严格 second entry 还要求第一次 chart entry opportunity 已经触发。三者可以描述同一事件，却不是无条件同义词。

Wedge 描述三次可区分的推动或测试；H3/L3 是尝试计数视图。Wedge 可以是趋势回调中的 Flag、成熟通道末端的 reversal candidate，或 Trading Range 中没有优势的局部结构。编号增加不等于概率增加；H4/H6 等高阶计数首先提示检查结构是否已经变成区间、endless pullback 或新趋势。

Parabolic Wedge 是 Tight Channel 中至少三次 surge 构成的高潮式三推。它描述推进紧迫性，不要求每一推机械变陡；没有反向接受时仍可能继续原趋势，第一笔反向运动通常先按 minor correction 或 Range 路径处理。

新的强 breakout 获得接受、成熟区间切断旧运动、主要结构被替换或观察周期改变时，旧 H/L 与腿数重置。局部重计和全局累计都必须写明尺度，不能在结果出现后选择更漂亮的计数。

### Flag

Flag 只说明 pullback、channel、局部 range 或其他暂停在外层趋势路径中的角色。它没有统一概率，不产生 Entry、Stop 或 Target：

- Double Bottom 可以是 Bull Flag，也可以是区间底部测试或 MTR 组件；
- Rising Channel 可以是当前 Bull Trend，并同时是外层或长期 Bear-Flag 视角；
- 普通 pullback 可以拖长成 endless pullback、反向 channel 或 Trading Range。

Final Flag 只能在顺势恢复失败和后续结果出现后得到更多确认；实时仍同时保留普通 continuation flag 路径。

### Triangle、ii、ioi 与 oo

Triangle 是成熟 Trading Range 与 Breakout Mode 的结构视图。来源对“五次反转”和“一侧三推且总体至少五腿”存在不同计数口径；运行中必须声明采用的观察尺度，不能建立机械换算。

- `ii / iii`：连续 inside bars，表示压缩；
- `ioi`：inside–outside–inside；
- `oo`：连续 outside bars，表示双边扩张；
- Expanding Triangle：两侧极值逐步扩张且多次反转，没有建立持续控制。

统一处理都是：压缩或双边状态 → 实际突破 → follow-through → 守住或重新进入。形态名称不提供方向。

### Reversal 与 MTR 过程

第一次逆势尝试默认是 Minor Reversal，常见目标是两腿修正或 Trading Range，不自动形成 opposite trend。

MTR 描述一条过程，而不是另一套交易方法：

```text
成熟趋势
→ 趋势线或主要结构被破坏
→ 原趋势测试旧极值
→ 测试失败或形成 HL / LH
→ 反方触发并尝试建立 swing
→ 强反向 breakout 与 follow-through 进一步确认控制转移
```

约五根强反向 K 线，或约十根普通 / 较弱反向 K 线，是课程用于比较反向压力强度与持续时间的启发式，不是达到根数就确认 MTR；一两根足够强的 surprise 也可能更快改变控制。

Wedge、Double Top/Bottom、Head and Shoulders、rounding top/bottom、Final Flag 或 Climax 可以描述其中组件，不能替代完整过程。Head and Shoulders 通常可拆回结构破坏、旧极值测试和反向路径；rounding top/bottom 常可拆回 Broad Channel、Endless Pullback 或 Trading Range。强反向 breakout 获得接受后，它同时是旧趋势失控和新方向 breakout continuation 的事实链，不需要在两种“策略”间选择。

旧趋势以新的强 breakout 和紧密趋势腿重新建立控制时，旧趋势线破坏、旧极值测试和 H/L 证据重置，不能永久借给后来的反转候选。

## 八、多周期与时间范围

每个结构、测试、目标和概率都绑定周期与观察窗口。同一价格在高周期可能是一根 breakout bar，在交易周期是 Tight Channel，在更低周期又展开成 Broad Channel 或 Range。

至少分别保存：

```text
外层 Context
- 主要状态、重要区域和长期目标

交易周期
- 当前结构、目标事件、Entry、Invalidation 与管理
```

较小周期可以提前触发，但必须在承担风险前定义；成交后不能因盈亏情绪临时切换到更小噪声周期。小周期 Entry 若追求大周期目标，Stop、仓位和持有时间必须容纳大周期正常波动。

Session 只通过剩余时间、波动、流动性、目标可达性和是否允许跨 Session 进入路径。盘中只能描述实时 session state，最终 day type 不能回填当时判断。Opening、first swing、Opening Breakout Mode、first-18 heuristic 和内部固定 opening window 不是同一对象，使用时必须声明边界来源。

## 九、结构生成目标

目标来自已经固定的结构或可见参照区域：

| 来源结构 | 候选目标事件 |
| --- | --- |
| Trend / Channel 内恢复 | 测试旧极值、通道边界或下一现实 magnet |
| Trading Range 边缘反应 | 返回内部公平区域、中部或另一侧 |
| Range / Pattern 突破并接受 | 测试按固定高度投射的 measured-move 区域 |
| 强 Breakout 与回调 | 尝试第二腿、旧极值或 Leg 1 = Leg 2 |
| Failed Breakout | 返回旧结构、内部目标、中部或另一侧 |
| 通道反向突破并接受 | 通道起点或更大 Trading Range |
| MTR 路径 | 反向两腿、旧公平区域或其他实际 swing magnet |

常见投射：

```text
Leg 1 = Leg 2：第一腿 A → B，第二腿起点 C，目标 = C + (B - A)
Range height：H = upper boundary - lower boundary
  向上目标 = upper boundary + H
  向下目标 = lower boundary - H
Double-bottom height = neckline - bottom area
Double-top height    = top area - neckline
```

所有端点必须来自当时可见的同一结构并冻结。Measured move 是目标候选，不提供入场许可；更近障碍、成本和剩余时间会改变现实 Reward。多个投射落在相近区域可以增强 magnet，但同一结构的不同量法不能重复增加方向概率。

## 十、从目标到 Market Path

结构明确后，不先寻找 Entry，而是为每个现实目标建立路径：

```text
来源结构
→ 目标区域
→ 目标事件与到达口径
→ 到达所需的价格序列
→ 增强、削弱和失效事实
→ 周期与时间范围
→ 条件概率
```

典型测试可以生成：

| 当前测试 | 一条目标路径 | 实质反路径 |
| --- | --- | --- |
| 趋势回调 | 原方向恢复并测试旧极值 | 回调扩大、结构破坏或进入 Range |
| 区间边缘 | 拒绝边缘并返回公平区域 | 外部获得接受并启动突破目标 |
| Breakout pullback | 突破点守住并恢复 | gap 关闭、旧区域重新接受 |
| 通道边界 | 内部反应并继续通道运动 | 外部突破获得接受并重分类 |
| 第二腿到旧结构边缘 | 外部接受并延续 | 第二腿陷阱并返回旧结构 |
| 旧极值、EMA 或量度区域 | 穿越并获得接受 | 拒绝并启动返回路径 |

路径状态随来源事实改变，不随名称数量改变。新的更具体结构可以替代旧路径；历史结构仍可保留为 Context，但必须服从证据生命周期。

## 十一、证据生命周期

```text
出现
→ 在当前周期、窗口和状态内有效
→ 因缺少跟随、重叠增加或关键区域被收回而削弱
→ 因目标路径被新事实否定而失效
→ 因新主导 breakout、成熟 Range、控制切换或周期变化而重置
```

削弱不等于立即失效；重置不否认历史发生，只说明旧事实不再支持当前路径。Pattern 演化、事后名称和旧概率都不能越过重置继续提供交易许可。

## 十二、证据追溯

本页的运行关系由以下 Reference 范围支持并接受其冲突边界：

- [课程概念索引](../reference/course/concept_index.md)：课程思想骨架和概念族覆盖；
- [跨讲重复矩阵](../reference/course/repetition_matrix.md)：同源视图、镜像、递进和低增量重复；
- [边界与冲突](../reference/course/boundaries_and_conflicts.md)：概率分母、术语口径、数学和翻译限制；
- [正式来源台账](../reference/official_sources.md)：正式资料身份与来源锚点；
- [逐讲课程材料](../reference/course/README.md)：具体条件、页码和案例证据。

Reference 只提供核验依据；本页负责系统中的形成条件、更新语义和运行职责。
