# 情景策略目录（Strategy）

> **状态：Strategy / Index**
>
> 本页是策略层的入口，说明策略层与 core、reference 的职责边界，以及按情景选择策略的决策链。

## 定位

本目录把 core 的五个 Setup 示例家族组织在四个情景中——趋势延续、突破延续、交易区间 fade、Major Trend Reversal、逆势修正 scalp——实例化为按情景组织的策略命题。Core 明确这些家族是示例、不是穷尽分类，本目录不声称覆盖全部可能的 Setup；每个策略页回答：在什么情景下、交易什么价格行为、怎样触发、什么事实使命题失效、stop 与 target 的锚点类别。

策略层是 **Application 层**：只综合和本地应用 core 已定义的概念，不建立新的最低定义，不生成可直接执行的订单参数。所有概念的完整定义以 core 权威页为准，本目录只保留必要摘要并链接权威页。

Core 的候选结果 `TRADE / WAIT / REJECT` 在策略层分别映射为 `STRATEGY / WATCH / NO_TRADE`：前者表达通用 Setup 资格，后者表达覆盖矩阵和决策流程的具体叶子。名称不同不表示存在两套判断体系。

## 与 core、reference 的职责边界

| 目录 | 唯一职责 |
| --- | --- |
| [core](../core/README.md) | 解释怎样描述、判断和更新市场行为，以及概念之间怎样关联（权威定义所在） |
| [strategy](README.md) | 把核心命题实例化为按情景组织的可检查策略原型 |
| [reference](../reference/README.md) | 保存派生术语速查、正式来源、课程映射与内容边界 |

维护原则：

- 策略页不重复定义概念；需要术语边界时链接 core 对应 Definition 页。
- 策略页只写触发类别、stop 锚点类别、目标类别，不固定具体价格、根数窗口或订单寿命；core 或课程给出的经验数字只标注语境，不写成跨市场硬规则或胜率。
- 同一段行情可以同时满足多个命题；策略页描述命题，不替代交易者当前实际选择的 premise。

## 四大情景

| 情景 | 核心命题 | 目录 | 权威 Setup 页 |
| --- | --- | --- | --- |
| 趋势 | 既有方向控制，回调未破坏主要结构，原方向恢复 | [趋势](trend/README.md) | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) |
| 突破 | 市场接受旧边界外的新价格，延续或形成第二腿 | [突破](breakout/README.md) | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) |
| 交易区间 | 边缘突破未被接受，价格回到区间内部轮动 | [交易区间](range/README.md) | [交易区间 Fade Setup](../core/05_setups/03_trading_range_fade.md) |
| 反转 | 原趋势失去控制（MTR 家族，swing）与逆势修正（minor scalp 家族，短线） | [反转](reversal/README.md) | [主要趋势反转](../core/05_setups/04_major_trend_reversal.md)、[逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) |

Breakout mode、climactic move 与 transition evidence 是叠加在基础状态上的跨层信息，不是第五个情景，也不与上述四类并列。

时段覆盖层加在四类情景之上，只增加候选起点、最晚入场、目标可达性与强制退出约束，不建立新家族，见 [时段覆盖层](session/README.md)。

## 覆盖层级：母命题、通用兜底与命名子型

策略目录不按“一个 Core 术语一页策略”组织，而按会改变 premise、触发、失效或直接预期的交易命题组织。每个家族先保证母命题有通用承接，再用命名子型收紧特定结构：

| 母命题 | 通用承接 | 命名子型 |
| --- | --- | --- |
| 趋势延续 | [普通趋势回调延续](trend/pullback_continuation.md) | 第一次小回调、H2/L2、wedge pullback、double flag、MAG、宽通道参与区 |
| 突破延续 | 已接受且无回踩由 BTC/STC 承接；双向未决由 [Breakout Mode](breakout/breakout_mode.md) 承接 | 突破回踩、failed failure、opening-range breakout |
| 交易区间 fade | [边缘确认 fade](range/edge_fade_confirmed.md) | limit probe/scale-in、边缘第二信号、失败突破回归 |
| MTR | [MTR 早期与确认两版本](reversal/mtr_early_and_confirmed.md) | 扩张三角形 MTR 候选；完整链中的双顶/双底作为结构证据，不单独降低 MTR 门槛 |
| 逆势修正 scalp | [通用逆势修正](reversal/minor_reversal_scalp.md) | 双顶双底反转尝试、wedge、final flag、climax 后修正 |

使用顺序是：先确认母命题成立；若命名子型成立，使用更具体页面及其更具体失效边界；只有母命题完整但没有更准确子型时才使用通用兜底。兜底页不能降低证据要求，也不能绕开状态更新。

K 线角色、Pattern、Context、接受/失败、Trader's Equation、stop、target、scale-in/out 和风险纪律属于证据输入或跨策略约束，不因为没有各自独立策略页就构成覆盖缺口。特别是 scale-in/out 改变同一 premise 的数量与管理，不建立新的入场 premise。

## 页面类型

| 类型 | 含义 |
| --- | --- |
| Index | 目录与导航，不建立策略命题 |
| Application（策略页） | 可检查的策略原型：回答 premise、触发、失效、stop 锚点、目标与管理 |
| Application（目标构造页） | 目标与结构构造说明，不独立成立入场策略（如 [量度目标构造](breakout/measured_move_breakout.md)） |
| Application（覆盖层页） | 叠加约束（时段、时间风险），不建立新家族（见 [时段覆盖层](session/README.md)） |
| Application（决策协议页） | 把策略页已有概念操作化为可观察的选择条件（版本选择、stop/target/管理绑定）；可收紧候选资格，但不得扩大 premise、重定义概念或增加未经授权的概率/订单执行规则（见 [决策协议](protocols/README.md)） |

## 实际策略页统一模板

`trend/`、`breakout/`、`range/` 与 `reversal/` 下的实际策略页统一使用以下语义结构。固定章节必须存在并保持顺序；可选章节只在确有策略特有信息时加入，不能替代固定章节。

| 顺序 | 章节 | 职责 | 是否固定 |
| --- | --- | --- | --- |
| 1 | 交易命题 | 说明交易什么价格行为、方向与所属 Setup 家族 | 固定 |
| 2 | 适用情景与路由 | 写明 market cycle、阶段、位置、控制、成立事实，以及何时路由到相邻策略 | 固定 |
| 3 | 版本或结构子型 | 区分早期/确认版、结构口径、边界来源等，不改变母命题 | 可选，可使用更准确标题 |
| 4 | 触发类别 | 描述抽象订单角色或可观察触发，不生成具体价格 | 固定 |
| 5 | Premise 失效 | 只写哪些新事实否定原交易理由；不与普通波动、candidate rejection 或 stop price 混用 | 固定 |
| 6 | Protective Stop 锚点 | 说明保护单应位于哪类结构外及为何容许正常波动 | 固定 |
| 7 | 直接预期与目标 | 写 Setup 直接期待的路径、现实 magnet 与允许加入 measured move 的条件 | 固定 |
| 8 | 管理边界 | 写 scalp/swing、正常回调、部分退出、转策略与数量管理边界 | 固定 |
| 9 | 语境数字与先验 | 只保留来源与分母清楚、绑定具体事件的经验数字 | 可选 |
| 10 | 常见误读 | 记录本策略最容易发生的越界和相邻策略混淆 | 固定 |
| 11 | 相关来源 | 链接 Setup 家族、直接使用的 Definition 页与必要相邻策略 | 固定 |

固定因果顺序为：`Premise → Eligibility / Routing → Trigger → Invalidation → Stop → Expected Path / Target → Management`。其中 Premise 失效不等于 protective stop，直接预期不等于最终 target，target 构造也不等于成交后管理。

维护时人工复核四个情景目录下的实际策略页是否保留固定章节和因果顺序；可选章节只能补充策略特有信息，不能替代 premise、触发、失效、stop、目标或管理。结构一致只是可读性基线，不证明内容正确。

## 核验工具

| 工具 | 用途 |
| --- | --- |
| [Core → Strategy 思想覆盖表](core_coverage.md) | 登记全部 Core Definition 与 Application，并用 Reference 复核高风险命题边界及其策略层落点 |
| [覆盖矩阵](coverage_matrix.md) | 核验五个已注册家族 × 当前状态与证据词汇不存在未处理组合；行号 R01–R48 + 全局行 G01，23 个实际策略页全部直接链接 |
| [决策流程图](decision_flow.md) | 覆盖矩阵的候选收集投影：session 覆盖收集 + 全局 BOM → 基础状态 → trend/range 并行 collectors → 同家族精度消歧 → 按各候选持有期过滤 R28 → PREMISE_SELECT（含硬约束与 G01）→ 唯一叶子 |

维护这些文档时使用以下人工检查顺序：先从 Core 权威页确认命题，再用 Reference 核对来源与边界，然后检查策略页、覆盖矩阵和决策流程是否表达同一语义。主题有链接、章节齐全或 R 编号完整都不自动证明思想覆盖和内容正确。

## 执行清单（从策略页到 Trade Plan）

策略页是原型：它告诉你「看什么、怎样触发、什么使它失效、stop 与 target 锚在哪类结构」，但**不给你具体价格**；[决策协议](protocols/README.md) 绑定选项选择条件。入场前必须逐项写清下列字段，全部写清前不下单：

| 步骤 | 写什么 | 来自策略页哪一节 |
| --- | --- | --- |
| 1. Premise | 一句话：「我在交易什么」（如：强趋势首次浅回调恢复） | 交易命题 |
| 2. Supporting reasons | 至少两个相互补充的理由，注明所属维度并排除同义标签重复计票 | 适用情景与路由 + 触发类别 |
| 3. Opposing evidence / Update | 反方当前最有力事实，以及会增强、削弱或否定本判断的新证据 | 适用情景与路由 + Premise 失效 |
| 4. 触发 | 具体订单：具体参照事件或 signal bar 的触发位 + 订单类型（stop entry / limit / 收盘市价） | 触发类别 |
| 5. 失效清单 | 会使 premise 失效的可观察事实清单（逐条可核对） | 失效 |
| 6. Active protective stop | 具体价格 + 依据（把 stop 锚点类别落到实际结构价位；signal bar 另一端仅在同时是完整失效边界时可用） | Stop 锚点 |
| 7. Profit target | 具体价格 + 依据（把目标类别落到实际 magnet / 量度价位；非"等它涨"） | 目标 |
| 8. 仓位 | 由 entry → active stop 的风险距离与账户风险上限算出；scale-in 则写全部层总风险 | 目标与管理 + 跨情景基线 |
| 9. 管理 | 入场前选定 scalp 或 swing；写出正常回调容忍、部分退出与 premise 变化退出的分支 | 目标与管理 + 三层退出保护 |
| 10. Trader's Equation | 用同一组 entry / stop / target 检查二结果近似：p(win) × reward − p(loss) × risk − costs > 0；存在部分退出、scratch 等结果时按 core 拆分更多互斥结果 | 跨情景基线 |

执行时仍遵守：证据不足 → WATCH（等待新数据重新运行）；空间或时间不足 → NO_TRADE。计划版本规则：**承担风险前**，stop / target / management 的实质变化需要新版本；**成交后**按预写管理分支调整并记录状态（不覆盖 original_target），不自动新建整份计划；退出后重新入场必须建立新 Trade Plan（core [从 Setup 到交易计划](../core/06_trade_plan_and_management/00_trade_plan.md)）。

## 选择链

每个策略页都不独立于以下判断链使用：

```text
Market Cycle 判定（trend / trading range，模糊时按 core fallback）
    ↓
趋势阶段与跨层信息（breakout phase / channel / breakout mode / climax / transition）
    ↓
Context：位置、控制权、Always In、支撑阻力与目标空间
    ↓
选定当前主导的命题（当前覆盖的家族之一：趋势延续、突破延续、区间 fade、MTR、逆势修正；可同时多个，core 不排除其他家族）
    ↓
检查至少两个相互补充的支持理由、反方证据和更新条件
    ↓
检查对应策略页的触发类别、失效事实与目标类别；不足则 WATCH / NO_TRADE
    ↓
Trader's Equation：概率、risk、reward、成本来自同一方案
    ↓
Trade Plan：entry、planned / active protective stop lifecycle、target、仓位、management
```

模糊状态的逐层 fallback 见 [市场周期](../core/01_market_cycle/00_market_cycle.md)，位置与控制见 [Context](../core/02_context/00_context_location_control.md)，Trader's Equation 见 [概率、风险和回报](../core/00_method/01_probability_risk_reward.md)，完整计划 schema 见 [从 Setup 到交易计划](../core/06_trade_plan_and_management/00_trade_plan.md)。

## 跨情景基线（全部链接 core，不在此重复定义）

| 主题 | 权威位置 | 策略层如何继承 |
| --- | --- | --- |
| Stop entry / protective stop | [两类 Stop](../core/03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md) | 触发用 stop entry，保护用结构 stop，两者用途不同 |
| 二次信号与陷阱 | [二次入场和陷阱](../core/03_acceptance_and_order_logic/03_second_entries_and_traps.md) | second signal / second-entry opportunity / actual fill 三层分开 |
| 接受与失败证据 | [接受、失望与失败证据](../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md) | follow-through、disappointment、premise 变化、Brooks success / failure 与适用 objective、trapped in/out、Pain Trade（行为模型，不构成独立入场依据） |
| 限价单环境 | [限价单市场](../core/03_acceptance_and_order_logic/02_limit_order_market.md) | buy below / sell above 只在对应环境中使用 |
| Scalp / Swing / TBTL | [Scalp 与 Swing](../core/06_trade_plan_and_management/01_scalp_vs_swing.md) | 入场前定管理方式，不临场切换 |
| 加仓减仓 | [加仓与减仓](../core/06_trade_plan_and_management/02_scaling_in_out.md) | scale-in 总风险在第一笔 entry 前确定 |
| 目标构造 | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md) | magnet、measured move 的构造与投射起点 |
| Test / confluence | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md#test-与-confluence) | 触及后继续看 reaction / follow-through；汇合可增加位置理由，同源对象不重复计票 |
| Two Reasons / 候选结果 | [什么是 Setup](../core/05_setups/00_what_is_a_setup.md#two-reasons-与证据汇合) | 独立理由不足输出 WATCH；premise 或方程已否定输出 NO_TRADE |
| 心理与纪律 | [风险与心理纪律](../core/06_trade_plan_and_management/03_risk_psychology.md) | OPM/沉没纪律、FOMO 边界、小仓宽 stop 早期参与的前提 |

## 相关来源

- core 框架入口与权威注册表：[core/README.md](../core/README.md)
- Setup 家族：[Setups](../core/05_setups/README.md)
- 术语速查：[核心术语表](../reference/glossary.md)
