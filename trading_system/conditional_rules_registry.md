# 条件规则台账

> **状态：Trading System / Rule Registry**

本页只保存可匹配的条件概率模板、背景、规则替代顺序和隔离项。模板不是可以直接抄入计划的百分比；市场结构、目标生成和 Pattern 关系由[Market Read 与 Opportunity](market_read_and_opportunities.md)负责，当前实例化和实时决策由[交易系统总流程](overall_flow.md)与[交易决策与计划](decision_and_plan.md)负责。

规则实例化是内部判断边界，不是 scalp 交易者的逐项填表任务。实盘只需快速确认当前目标、周期、Outcome Horizon 和条件与所用规则一致，并检查是否已有更具体的新条件替代它。只有 Rule Match 本身成为关键决定依据、需要复盘或参与样本校准时，才保存必要字段。

## 一、规则模板与当前匹配

台账条目可以使用“旧极值”“当前 Channel”等相对对象保存通用模板。模板只有在当前判断时点完成以下实例化，才能成为 Opportunity 的 Market Probability：

```text
候选规则模板
已经成立的 Market Read 事实
当前可观察的目标事件与到达口径
当前观察周期
当前 Outcome Horizon
判断时点
近似概率或概率语言
增强、削弱、替代和失效条件
与同源证据的合并关系
```

实例化结果称为当前 Rule Match。缺少目标、分母、周期、Outcome Horizon 或判断时点的模板不能进入 Trader's Equation；不同目标或 Outcome Horizon 的模板也不能互相补字段。

## 二、规则状态

| 状态 | 含义 | 能否进入当前路径或方程 |
| --- | --- | --- |
| 候选模板 | 保存相对条件、目标关系和近似概率 | 完成当前实例化后才可以 |
| 可运行匹配 | 当前条件、目标、周期、Outcome Horizon 和时点完整，且未被更具体规则替代 | 可以 |
| 条件更新 | 同一目标在新时点出现更具体条件 | 使用新规则替代旧规则 |
| 背景 | 描述状态频率、语言或长期倾向，不是当前交易结果 | 只进入 Context |
| 隔离 | 分母、目标、数学或来源口径不清 | 不可以 |

下列表格除明确标为背景或隔离的条目外，默认都是候选模板，不是已经完成的 Rule Match。

## 三、规则选择顺序

```text
基础 `Context.Operating State` 先验
→ 更具体的结构条件
→ 当前区域测试结果
→ Breakout / Follow-through / Acceptance 等新事实
→ 当前判断时点的目标先于失败结果估计
```

匹配顺序应用于当前已经实例化的规则。只有目标事件、周期和 Outcome Horizon 相同，更具体条件才替代一般规则。不同目标事件可以同时成立，但不相加、不相乘，也不共同进入一份 Trade Plan。

理由负责更新 Opportunity 支持程度与 Activation；条件规则提供 Market Probability。H2 / Double Bottom / Second Buy Entry 与镜像的 L2 / Double Top / Second Sell Entry 等同源角色不各自提供概率。

Long / Short Opportunity 分别匹配各自目标。双方目标、Outcome Horizon 或判断时点不同时，其概率不要求互补，也不能用 `1 - P(向上目标事件)` 自动生成向下目标概率。系统先独立匹配 Market Probability；Candidate 再根据 Trigger、Entry、Stop、Targets、管理和成本形成 Candidate Outcome Probability 或诚实区间。

## 四、概率语言与交易数学

| 条件或措辞 | 目标事件 | 概率或风险交换 | 限制 |
| --- | --- | --- | --- |
| Brooks 使用 `likely / probably` | 原句明确定义的事件 | 约 `60%+` | 教学语言阈值，不是统一统计模型 |
| Brooks 使用 `unlikely` | 原句明确定义的事件 | 约 `40%-` | 目标事件仍须明确 |
| 普通、没有压倒性证据 | 当前明确 objective | 常在 `40%–60%` | 不制造更精确数字 |
| 当前交易估计约 `40%` | 计划目标先于失败结果 | 常需约 `2R` 作基线 | 只是风险交换，不是固定目标 |
| 当前交易估计约 `60%` | 计划目标先于失败结果 | 约 `1R` 可能成立 | 仍须计成本、实际 Stop 和管理 |

基础结构/阶段频率、结构最终演化、突破方向、目标先于 Stop 和账户盈利不是同一概率对象。

条件规则给出的 Market Probability 只有在 Candidate 的结果事件与原目标事件一致时，才可作为 Trader's Equation 的主要输入。更近 Stop、部分退出、主动管理、执行和成本改变结果事件时，必须另行估计 Candidate Outcome Probability，不能直接复制市场目标概率。

## 五、基础结构与区间

| 已成立条件 | 目标事件 / 时间范围 | 近似概率 | 用途与限制 |
| --- | --- | --- | --- |
| 观察总体市场阶段 | 强 breakout phase 与 channel / range 行为占比 | 约 `10 / 90` | 状态频率，不是交易胜率 |
| 已确认 Trend 中的反转尝试 | 不发展成完整 opposite trend | 约 `80%` | 趋势惯性；不等于任意顺势 Entry 胜率 |
| 已确认 Trading Range 中的 breakout attempt | 不获得持续外部接受 | 约 `80%` | 普通区间尝试；成功接受后立即更新 |
| 成熟中性 Range / Breakout Mode | 最终向上或向下突破方向 | 接近 `50 / 50` | 方向先验，不是具体订单方程 |
| 成熟区间上 / 下三分之一附近 | 先向区间内部移动等距目标 | 约 `60%` | 中部更接近 50/50；仍需实际 Target 与 Stop |
| Endless Pullback 发展到约 20 根 | 原趋势恢复或反向突破 | 接近 `50 / 50` | 用于重分类；根数不是机械阈值 |

普通区间约 80% 的单次突破失败，与成熟 Breakout Mode 最终方向接近 50/50 描述不同事件。区间边界外已经出现强突破和接受后，不能继续使用普通 attempt 的 80% 失败先验。

## 六、Trend、Channel 与当前恢复路径

| 已成立条件 | 目标事件 / 时间范围 | 近似概率 | 用途与限制 |
| --- | --- | --- | --- |
| 已确认 Trend、合理 pullback、结构 Stop | 测试旧极值或对应近端 objective | 典型约 `60%` | 目标必须具体，不属于 H2 名称本身 |
| Tight Channel 第一次逆势尝试 | 先成为 minor reversal、pullback 或测试旧极值 | 约 `70%` | 不是顺势订单胜率 |
| 清楚倾斜的方向 Channel | 最终先反向突破趋势线并通常区间化 | 约 `75%` | 完整 Channel 生命周期 |
| 测试已识别 Channel 边界 | 从边界反应 / 测试另一侧，与持续外部突破 | 约 `70 / 30` | 局部边界路径事件 |
| 清楚倾斜的方向 Channel 沿自身推进方向突破外侧 Channel Line | 在仍清楚承载同一 Channel 的最高相关周期上，约五根内无法保持外部接受并回入 | 约 `75%` | 近水平、主体更像 Range 时不适用；强跟随与外部接受出现后按新 breakout 更新 |
| Trending Trading Range 形成新区间 | 回测并与前一区间重叠 | 约 `60%` | 描述局部公平区域重叠 |

Rising Channel 当前恢复旧高约 60%，与完整生命周期最终向下突破趋势线约 75% 可以同时成立；它们使用不同 Outcome Horizon，不构成当前多空交易概率冲突。

上述外侧 Channel Line 条目的“最高相关周期”是仍能清楚表达同一 Channel 的最高周期，不是无限向上寻找任意周期；约五根从该周期的越界尝试开始观察，也不是第五根自动反向入场。失败描述的是加速突破没有保持，不自动确认 opposite trend 或一笔反向交易；反向 Candidate 仍需自己的 Activation、Stop、Target 和方程。若强实体、持续跟随和外部接受确认少数成功分支，旧失败匹配立即失效；只有来源条件同时匹配时，才进一步调用第二段、TBTL 或 measured-move 路径。

普通 Flag 的统一 40% 说法因 Flag 范围过宽，不进入运行。实际路径按当前 Trend、Channel、Wedge 或 Range 条件匹配。

## 七、Wedge、Breakout 与反转过程

| 已成立条件 | 目标事件 / 时间范围 | 近似概率 | 用途与限制 |
| --- | --- | --- | --- |
| 合格倾斜 Wedge 的三推已经完成，尚无低先验方向突破 | 先向 Wedge 反方向 / 原方向突破 | 约 `75 / 25` | 只描述突破方向先验；宽泛三推不能直接借用 |
| Wedge 已向原先约 25% 的方向突破 | 突破保持接受并到达事前固定的 measured move / 失败并反向返回 | 约 `50 / 50` | 新条件替代旧 75/25；较小第二段是路径预期，不与 measured-move 目标混用 |
| Strong Breakout 并获得跟随 | 至少尝试第二段 | 约 `60%` | 第二段可以短小、横向或失败 |
| 特别强、连续、低重叠的 Breakout | 到达已固定 breakout-height measured move | 约 `60%–70%` | 普通突破不能借用 |
| 趋势结构破坏、旧极值测试失败，尚无强反向跟随 | 完成反向 swing objective | 约 `40%` | 较早风险承担时点 |
| 强反向 Breakout 与 follow-through 已建立控制 | 完成反向 swing objective | 约 `60%` | 新判断时点；重算 Entry、Stop 与 Reward |

“广义反转约 80% 不形成完整 opposite trend”、较早反向 swing 约 40%、强反向确认后约 60% 分别描述状态惯性和两个筛选后的判断时点。不能相乘，也不能用后者概率配合前者 Entry。

## 八、Climax、TBTL 与 Gap 覆盖条件

| 已成立条件 | 目标事件 | 近似概率 | 用途与限制 |
| --- | --- | --- | --- |
| 极端 microchannel / 特定高潮推进 | TBTL 横向至反向修正 / 继续形成新 swing | 约 `70 / 30` | 特定覆盖条件，不适用于普通 microchannel |
| 区间顶部高潮突破、长上影、差跟随 | TBTL 横向至下 / 继续成为 measuring move | 约 `60 / 40` | 只适用该区间顶部组合 |
| 成熟 Channel、重复 climaxes 或末段推进 | correction / Trading Range 与继续原趋势 | 约 `75 / 25` | correction 不等于 opposite trend |
| Moving-Average Gap 背景中的反向路径 | swing reversal / Flag 或 Trading Range | 约 `40 / 60` | 只作背景，不与早期反转概率叠加 |

Candidate measuring gap、potential exhaustion 和 climax bar 在结果出现前不取得事后概率。Gap 关闭只更新分离证据；没有旧区域重新接受和反向跟随，不确认反转。

## 九、Opening 与 Session 背景及覆盖条件

| 已成立条件 | 目标事件 | 近似概率 | 状态与限制 |
| --- | --- | --- | --- |
| 第一根 / 前 7 根 / 第一小时 / 前 90 分钟 | 已形成当日一个极值 | 约 `20 / 50 / 70 / 90%` | 背景；窗口嵌套，不相加 |
| 初始 opening swing 已形成 | 初始 swing 发生反转 | 约 `50%` | 候选模板；仍需定义 swing、Outcome Horizon、结构、目标和 Trigger |
| 前两小时 / 日中 / 最后两小时 | 启动当日 major swing | 约 `90 / 50 / 80%` | 背景；窗口可重叠，不是互斥分布 |
| 约 18 根 opening range 后出现获接受突破 | 对侧极值保持不被测试 | 约 `90%` | 候选模板；仅适用来源市场与周期，普通越界不适用 |
| 开盘前 90 分钟 | 测试事前标出的 support / resistance | 约 `80%` | 候选模板；仅适用来源市场与周期，不得事后挑价位 |
| Exceptional opening breakout | 到达已固定 measured move | 约 `70%` | 候选模板；并入特别强 breakout 的 60%–70% |

标为背景的窗口统计只用于安排观察、约束剩余时间和提供 Session Context，不直接进入 Trader's Equation。候选模板也只有在当前市场、周期、Session 和目标与来源适用边界相容，并完成当前字段实例化时才形成 Rule Match；Exceptional opening breakout 按特别强 breakout 的通用目标规则实例化，不因“opening”标签重复增加概率。

## 十、条件更新示例

| 表面冲突 | 实际关系 | 正确切换 |
| --- | --- | --- |
| 区间 breakout attempt 约 80% 失败；强突破约 60% 有第二段 | 观察时点和突破质量不同 | 普通 attempt → 获接受后切换第二段规则 |
| Channel 最终约 75% 反向突破；当前顺势回调约 60% 测试旧极值 | 长期生命周期与短期内部段不同 | 分别保存 Outcome Horizon |
| Tight Channel 第一次逆势约 70% 只是 minor；Channel 最终约 75% 反向突破 | 第一次信号近期结果与最终寿命不同 | 先按 minor；反向接受后更新结构 |
| Wedge 突破前 75/25；低概率方向已经突破后约 50/50 | 25% 事件已发生，条件分母改变 | 突破后重置旧先验 |
| Channel 边界 70/30；同向外轨突破约 75% 失败 | 局部边界反应与越界后的失败事件不同 | 以当前已经发生的事件选规则 |
| 市场约 10% breakout、90% channel/range；普通交易约 40–60% | 状态频率与目标结果估计不同 | 不把状态占比代入方程 |

## 十一、隔离项

以下说法保留来源问题，但不得进入运行：

| 说法 | 问题 |
| --- | --- |
| “下一次反转约 40% 成为主要反转” | 分母与 major 的结果口径不清 |
| 任意 Protective Stop 被触发后约 50% 是 trap | 范围过宽，缺少结构与窗口 |
| Surprise 后 scale-in 约 80% 回到 breakeven | 未定义最大风险、次数、时间与成本 |
| Scale-in 胜率递进 `60 / 80 / 90` | 材料内部和总风险数学冲突 |
| “80% 胜率且风险 3R 会亏” | 忽略成本时方程并非必然为负 |
| Elite scalper 约 90% 胜率 | 能力修辞，无可复核样本 |
| 约 90% K 线双方都能经管理获利 | 结果与管理分母不可验证 |
| “风险大于回报时约 60% 会亏” | 未定义具体比例与结果事件 |
| 用单笔 Actual Risk / MAE 证明 Entry 概率或 2R | 事后循环推理 |
| “概率永远不超过 60%” | 与多项特定结构事件冲突，只能视为普通交易修辞 |
| 期权对冲可能占卖压约 50% | 缺少数据，且不是价格可直接观察事实 |
| 无明确条件的 TBTL `60 / 70 / 75` | 使用不同结构和分母 |

课程中的 Z-score 解释、十亿交易者连续百胜百负算例、43C 的 60%/80%/90% 数字冲突和其他数学问题也保持隔离。完整证据见[课程边界与冲突](../reference/course/boundaries_and_conflicts.md)。

## 十二、规则维护

新增或修改候选模板、背景或隔离项必须：

1. 回到 [正式来源台账](../reference/official_sources.md)和具体逐讲材料核对原条件；
2. 检查[重复矩阵](../reference/course/repetition_matrix.md)是否只是同源、镜像或低增量重复；
3. 检查[边界与冲突](../reference/course/boundaries_and_conflicts.md)是否存在分母、数学或翻译问题；
4. 明确它替代哪条相同目标、周期和 Outcome Horizon 的旧规则；
5. 若来自内部连续样本，登记样本定义、采集区间和适用市场，不冒充 Brooks 通用规则。

规则修订必须登记生效时间，并说明替代、缩小或隔离了什么条件。单笔实盘结果不能直接改变本台账；条件定义改变时，新旧样本不得静默合并，后来的修订也不能回写历史 Decision Record / Trade Plan 使用的规则。
