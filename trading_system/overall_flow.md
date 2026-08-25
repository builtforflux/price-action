# 价格行为交易系统总流程

> **状态：Trading System / Runtime Contract**

本页是唯一运行入口。盘中只完成四件事：读取市场、构造现实多空机会、比较当前交易表达、按账户事实执行与更新。

```text
Safety Check
→ Market Read：继承 Context → 更新 Price Map / Price Process → 确认或重构 Context
→ Opportunity Set：现实的 Long / Short 机会及可能顺序
→ Context Permission + Trade Candidates：只为当前允许且可表达的少数机会计算
→ Decision：Execute / Wait / No Trade
→ Order / Position / Protection
→ Event Update / Exit / Review
```

## 盘中一屏卡

首先确认实际仓位、工作订单、保护和数据一致；异常时只处理风险。

空仓或 Reframe 时扫过：

```text
Context  周期 / horizon；继承的市场组织、Control 与转换状态
Map      当前区域；上下相关价格带、汇合、距离与空间
Process  From / Now / Role；正在测试什么；下一事实
  Bars        实体、收盘、影线和相对强度
  Continuity  同向连续性和 follow-through
  Separation  gap 保持、缩小或关闭；overlap 是否增加
  Pullback    深度、持续时间以及原方向恢复速度
  Opponent    反方 K 线、跟随和失败尝试是否形成持续压力
  Result      Buying / Selling Pressure；Control 保持、减弱还是转移
Confirm  保持当前 Context，标记 Transition，还是 Reframe
Long     Role / horizon；目标；理由链；Activation / Invalidation
Short    Role / horizon；目标；理由链；Activation / Invalidation
Choose   现在可交易的 Entry / Stop / Target / 方程；执行、等待还是放弃
```

这些是观察顺序，不是盘中填写字段。能直接确认的项目扫过即可；只有最终变化会按必要记录规则保存。

普通新 K 线只问：

1. `Map / Process` 出现了什么新事实？
2. 原 Context 仍成立，还是需要标记 Transition 或 Reframe？
3. 哪条多空机会、Candidate、Trade Plan 或动作因此改变？

都是“否”就结束，不记录。

## 一、四个运行对象

| 对象 | 职责 | 权威文档 |
| --- | --- | --- |
| Market Read | 继承当前有效 Context，更新 Price Map 与连续 Price Process，再保存确认或重构后的 Context；不选交易方向 | [Market Read 与 Opportunity](market_read_and_opportunities.md) |
| Opportunity Set | 表达现实多空市场结果的 objective、理由链、Activation、Invalidation、horizon 与市场目标概率 | [Market Read 与 Opportunity](market_read_and_opportunities.md#十从-market-read-到-opportunity-set) |
| Trade Candidate / Plan | 在 Context 许可下，为当前表达计算 Trigger、Entry、Stop、Target、交易结果概率、Size 与方程；选中后冻结为 Trade Plan | [交易决策与计划](decision_and_plan.md) |
| Execution State | 保存实际订单、成交、敞口和 Active Protective Stop | [执行、持仓与复盘](execution_management_and_review.md) |

Market Read 是方向中性的价格事实；Opportunity 是对一个明确市场结果的可证伪假设；Trade Candidate 是当前价格下承担该假设的方法。方向判断正确不表示当前 Candidate 值得交易。

Pattern 不是运行对象。H2、Double Bottom、Wedge、Flag、MTR 等名称只压缩结构、次序或角色；同一价格链的多个名称不生成多份理由。

## 二、Safety Check

每次承担新风险或处理账户事件前确认：

```text
实际净仓位与可能暴露
→ 全部工作订单与回执
→ Active Protective Stop 是否覆盖实际数量
→ 行情、账户、连接与已知事件风险是否可靠
```

不一致时进入 `SAFETY_EXCEPTION`，允许动作只限于核对、恢复保护、撤单、减仓或退出；恢复前不评价新机会。

## 三、Market Read｜继承背景，用当前事实确认或重构

### 1. Inherited Context｜先取得本次判断的外层边界

连续观察时继承上一次已确认的 Context，不因每根新 K 线从头分类。首次看图或 Reframe 时，只做足以开始读取的暂定分类；证据不足就使用 `Unclear`。只保留会改变目标、正常回调、Stop 或管理的信息：

- Trading Timeframe、相关外层约束、Session 和剩余时间；
- 当前主导价格组织：Breakout / Spike、Tight Channel、Broad Channel、Trending Trading Range、Trading Range 或 Unclear；
- Bull / Bear / Balanced / Unclear Control；
- Breakout Mode、Climactic Move Candidate、Confirmed Climax 或 Transition 等当前会改变判断与动作的附加条件。

暂定输入：`5m 空头通道，先继承 Bear Control；当前宽窄和末段加速是否已经改变状态，等待 Price Process 确认。`

### 2. Price Map｜当前在哪里，两侧有什么

1. 确定 Current / Active Area；
2. 标出当前 horizon 相关的旧高低、区间边界、突破点、gap、50%、EMA / 趋势线 / 通道线、事前固定 MM 和 Session 水平；
3. 同一价格带只保留一份，标出来源是否相对独立；
4. 上方、下方按距离排列，估算到最近相关区域的空间。

Price Map 只登记区域、来源、汇合和距离。同一 50%、EMA 或旧高可能是多头的 Target、空头的 Potential Entry Area，或另一机会的 Invalidation Reference；角色在 Opportunity 中分配。

### 3. Price Process｜价格怎样演化到这里

```text
From    此前是什么方向运动、回调或区域测试
Now     当前是 Up / Down Leg、Pause 还是 Local Balance
Role    当前运动承担 Continuation、Pullback、Range Leg、Reversal Attempt 还是 Unresolved
Change  由 Bars、Continuity、Separation、Pullback 与 Opponent Response 汇总 Pressure 变化
Testing 正在测试哪个区域，Control 是否仍有效
Next    什么事实表示 Activation、接受、拒绝、失败或重构
```

`Change` 的数秒扫描顺序是：

```text
Bars        实体、收盘、影线和相对附近 K 线的强度
Continuity  同向 K 线是否连续；是否有 follow-through
Separation  gap / breakout separation 是否保持；overlap 是否增加
Pullback    深度、持续时间、是否留有 gap，以及原方向恢复速度
Opponent    反方 K 线质量、跟随和失败尝试是否形成持续压力
Result      Buying / Selling Pressure 怎样变化；原 Control 是否仍有效
```

这些观察先组成一条价格事实链，再汇总 Pressure；不能把同一强趋势 K 线的实体、强收盘、gap 和 Control 当成四份理由。

把过程压缩成一句：`强空头腿第三推延伸缩小，反弹后第二次下探卖压更弱；当前测试旧低能否守住，下一步看多头能否建立实际跟随。`

### 4. Confirm / Reframe Context｜过程是否改变外层状态

- 新事实仍符合原 Context 的正常回调、目标与双边获利能力：确认并保持；
- 原方向 Pressure 减弱，但反方尚未建立持续接受：不翻转 Direction；只有正常回调、目标或管理边界已开始改变时才标记 Transition；
- 回调、分离、重叠、双边获利能力或新区域接受跨过状态边界：重构 Context；
- 首次看图时，以本轮确认结果替换暂定分类。

只有完成这一步，才用确认后的 Context 构造 Opportunity 和应用 Context Permission。Pressure 减弱、反方 Pressure 建立与 Control 转移是三个不同结果。

## 四、Opportunity Set｜分别构造现实多空机会

不用“当前偏多/偏空”代替机会构造。对每个仍可能影响当前决策的市场结果，使用同一简表：

```text
Opportunity
- Direction + Role + Horizon
- Objective + Market Outcome Criterion
- Why：来源去重后的价格事实链
- Already → Next：已经成立什么，下一过程事实是什么
- Activation：什么事实使该机会具备交易表达资格
- Invalidation：什么市场事实真正否定该机会
- Price Areas：Potential Entry Area / Obstacles / Targets
- Against：当前最强矛盾或对手机会
- Market Probability / Rule Match
- Expiry：最迟何时仍有意义
```

`Role` 只用来防止混合不同目标：continuation、correction、reversal、range return 或 breakout。一个强空头趋势可以同时存在 `Up / Correction` 和后续 `Down / Continuation`；它们可以顺序实现，不是一次二选一。只有顺序会改变当前选择时，才补一句 `Likely Sequence`。

### 理由怎样汇合

理由不按名称计数。同一突破产生的大实体、gap、buying pressure、bull control 和 acceptance 是一条价格链；同一组低点构成的 H2、Double Bottom 和 Wedge View 也可能是一份事实。

新的二次测试、后续 follow-through、反方尝试失败，或来源独立的价格区域才可能提供增量。各事实还必须说明它支持的是：

```text
机会背景 → Activation → 新价格接受 → 向目标持续 → 目标处反应
```

这防止把“反转会启动”、“启动后会到 MM”和“到 MM 后会反转”混成一个概率。

### 价格区域怎样进入 Opportunity

- 50%、EMA、通道边界等区域本身不生成方向；
- 当前价格处多项独立支撑/阻力汇合，可以增强停顿或反应倾向，但仍需要价格反应；
- 前方多个事前固定目标汇合，可以增强 target cluster 的 magnet 和到达后反应意义；
- Invalidation 必须是可观察的市场条件，不只是一个价格引用；Protective Stop 要等 Entry 确定后才能形成。

### Context Permission｜这种市场允许怎样表达

| Context | 默认允许的 Candidate | 逆势或突破要求 |
| --- | --- | --- |
| Breakout / Spike | 沿 Control 方向 | 目标到达、三推或一根反转棒不构成逆势许可 |
| Tight Channel | 顺势 continuation | 强反向 breakout、follow-through 并获得接受后重评 |
| Broad Channel | 顺势 swing；边缘可选逆势 scalp | 有效边缘、独立测试、实际反向 Pressure 和足够空间 |
| Trending Trading Range | 顺势仍略占优；局部双边机会增加 | 分开短期 range return 与长期 reversal |
| Trading Range | 边缘 range return；中部通常等待 | 外部突破、follow-through 并守住后转 breakout |
| Breakout Mode | 等待实际方向证据 | 突破、跟随、守住或回踩成功后重算 |
| Climax / Transition | 原方向减弱但未自动反转 | 后续停止延续、反向 Pressure 与接受决定新机会 |

Context Permission 不删除市场上可能存在的 Opportunity，只决定它现在能否生成 Candidate，以及逆 Control 需要补充什么证据。

## 五、Trade Candidates｜比较怎样交易，不只比较方向

只有 Objective、Activation、Invalidation、horizon 和市场概率口径完整，且 Context Permission 允许的 Opportunity 才生成 Candidate。尚未 Activation、缺空间或没有当前 Trigger 的机会停在 Wait，不填完整计划。

```text
Trade Candidate
- Opportunity Snapshot / 判断时点
- Trigger / Entry 条件、价格规则和有效期
- 引用 Opportunity Invalidation + Planned Protective Stop
- First Target / Main Target / Outcome Criterion
- Position Size + Cost / Slippage + Time + Management
- Candidate Outcome Probability + Trader's Equation
```

同一 Opportunity 可以在收盘、follow-through、回调或 H1/H2 等不同判断时点形成新 Candidate，但每次都使用当前 Entry、Stop、剩余空间和交易结果概率重算。这些是同一市场机会的不同风险承担时点，不是新 Setup。

比较时依次问：

1. Context Permission 是否允许；逆 Control 的 Activation 是否已经完成？
2. 这条价格链已经完成多少，还依赖多少未发生转换？
3. 当前 Entry 到合理 Stop 的风险是多少？
4. 第一现实目标和主要目标前有多少净空间？
5. 等待下一事实会改善确认，还是只会让 Entry 更差？
6. 哪个 Candidate 的完整风险交换更好？

未选 Candidate 是临时比较，不保存为多份完整计划。选中后才冻结为 Trade Plan，完整数学和字段见[交易决策与计划](decision_and_plan.md)。

## 六、Decision｜当前唯一动作

| 结果 | 动作 | 必须明确 |
| --- | --- | --- |
| 选中 Candidate，Trade Plan 完整，账户可靠执行 | `EXECUTE` | 提交的订单、有效期、成交后保护 |
| 当前问题或 Opportunity 仍值得跟踪，但缺 Activation 或当前表达 | `WAIT` | 下一可观察事件与过期条件 |
| 当前没有现实 Candidate，且没有在 Expiry 前值得跟踪的明确下一事件 | `NO_TRADE` | 排除原因；未来只有新 Reframe 才重评 |

Wait 可以发生在 Market Read 尚未解决、Opportunity 尚未 Activation，或当前 Candidate 不值得三个阶段，但必须存在 Expiry 前明确、现实的下一事件。没有这种事件，或空间、时间、风险已排除当前机会时，结果是 No Trade。Wait 不保留隐藏可执行计划；新事实到来时按新价格重算。已提交并等待成交的 Stop / Limit 属于 Working Order，不是 Wait。

## 七、Event Update｜普通事件只沿变化传播

```text
1. Safety 或账户事实变了吗？
2. Price Map 或 Price Process 变了吗？
3. Context 或当前市场问题需要 Reframe 吗？
4. 哪个 Opportunity 增强、削弱、达到 Activation、完成、失效、过期或被取代？
5. Candidate、Trade Plan 或动作需要变吗？
```

第 2–5 步都没有跨过原边界时，结果是 `NO_CHANGE`：继续观察、继续工作原订单或按计划持仓，不产生人工记录。

以下情况才重做完整 Market Read：

- 交易周期或 horizon 改变；
- 主导市场组织或 Control 跨过边界；
- 当前区域测试已解决，价格进入新问题；
- 原 Opportunity Set 被新突破、成熟区间或周期变化取代。

旧 Opportunity 和 Trade Plan 保留当时事实与结果，不被新 Market Read 回填。

## 八、订单与持仓路由

本页只规定当前账户状态应进入哪条路；完整生命周期由[执行、持仓与复盘](execution_management_and_review.md)拥有。

### Working Order

- 核对订单回执、可能最坏 Exposure、有效期和成交后保护；
- Opportunity 失效、成交范围外方程不再成立或订单过期时撤单并确认；
- 部分成交、撤单中或 OCO 另一侧未确认撤销时，按仍可成交的最坏暴露处理。

### Open Position

每个相关事件先运行 Event Update，再映射到原 Trade Plan：

| 机会与计划变化 | 允许动作 |
| --- | --- |
| 增强或保持 | 按计划持有；新增风险仍需新 Candidate |
| 削弱但未失效 | 持有、停止新增风险，或执行预写减仓/目标收缩 |
| 所选 Opportunity 失效 | 取消剩余新增风险并主动退出；归零前维持保护 |
| 反方机会获得接受 | 先处理原仓位；反向交易重新建 Candidate |
| Target、Active Stop、时间或账户条件发生 | 按 Outcome Criterion 处理并核对实际剩余仓位 |

退出原方向不提供反向交易许可；被困交易者和预期退出压力只解释可观察的失败链，不另加一票。

## 九、必要记录

系统是事件驱动，不逐 K 线记录：

| 事件 | 保存内容 |
| --- | --- |
| 普通观察，机会、风险和动作未变 | 无 |
| 新市场问题或 Opportunity 实质改变下一观察 | 只记变化和下一事实 |
| 形成 Execute，或需要跨事件跟踪的 Wait | 最小 Decision Record |
| 普通扫描得到 No Trade | 无；只有改变观察计划、风险或规则样本时才记原因 |
| 选中 Candidate 或实质修改计划、仓位、保护或风险 | 冻结 Trade Plan 或追加 Delta |
| 成交、拒单、部分成交、撤单确认、异常、减仓或退出 | 平台原始事实加必要差异 |
| Opportunity 或交易结束 | 终结事实；盘后复盘 |

最小 Decision Record：

```text
时点 + 品种 / 周期
决定：Execute / Wait / No Trade
Market Read：Context + 当前区域 / 问题（一短句）
Opportunity：Direction + Role + Objective，或当前问题
边界：Activation / Next / Target / Invalidation / Expiry
如执行：Entry + Stop + Target + Size
```

复杂多层、多目标、跨 Session、OCO 或异常计划才展开完整字段。平台已可靠保存的订单、成交和费用不人工重抄。

## 十、账户状态快速清单

### 准备下单

- 我选的是哪个 Opportunity，它是 continuation、correction 还是 reversal？
- Context Permission 是否允许，Activation 是否已经发生？
- 对手机会怎样才算获得接受？
- Entry、Stop、Target、Size、成本和有效期清楚吗？
- 当前账户可以可靠表达它吗？

### 订单工作中

- 实际 Order State 和最坏 Exposure 是什么？
- Opportunity、成交范围、有效期和方程仍成立吗？
- 如果现在成交，保护会立即覆盖实际数量吗？

### 持仓管理

- 实际数量与 Active Protective Stop 一致吗？
- 原 Opportunity 增强、保持、削弱还是失效？
- 反方只是出现，还是已经获得接受？
- 现在的计划动作是持有、停止新增风险、减仓、移动保护还是退出？

### 异常状态

- 真实净仓位、所有可能成交订单和最坏暴露是什么？
- 保护、数据、连接或回执哪里不一致？
- 当前安全动作是核对、恢复保护、撤单、减仓还是退出？

## 十一、系统不变量

- Market Read 先固定价格事实，再构造多空 Opportunity；不从想做的方向反向挑理由。
- 现实多空机会各自拥有 objective、horizon、事实链、Activation、Invalidation 和市场目标概率；缺少一方理由不自动证明另一方。
- Correction、reversal 和趋势 continuation 可以顺序发生；不同 objective 或 horizon 不放入一个概率或方程。
- 同源 Pattern、Pressure、Control、trapped 解释和目标量法不重复计数；新测试、新反应或独立区域可以提供增量。
- 50%、EMA、旧高低、MM 和通道边界是价格区域；它们的 Potential Entry Area、Target、Obstacle 或 Invalidation Reference 角色只对某个 Opportunity 成立。
- Invalidation 属于 Opportunity；Trigger、Entry 和 Protective Stop 属于 Candidate。Stop 不是方向理由，且必须容纳对应周期的正常波动。
- Opportunity 市场目标概率与 Candidate 交易结果概率分开；只有后者与当前 Entry、Stop、退出和管理共同进入 Trader's Equation。
- 只为当前可表达的少数机会构造 Candidate；只把选中 Candidate 冻结为 Trade Plan。
- 认知变化不自动产生交易动作；新增风险永远重新经过 Candidate、账户风险与执行检查。
- Wait、No Trade、未成交机会、实际交易和规则样本分别闭环；普通未变事件不记录。
