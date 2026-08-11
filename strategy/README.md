# 情景策略目录（Strategy）

> **状态：Strategy / Index**
>
> 本页是策略层的入口，说明策略层与 core、reference 的职责边界，以及按情景选择策略的决策链。

## 定位

本目录把 core 的五个 Setup 示例家族组织在四个情景中——趋势延续、突破延续、交易区间 fade、Major Trend Reversal、逆势修正 scalp——实例化为按情景组织的策略命题。Core 明确这些家族是示例、不是穷尽分类，本目录不声称覆盖全部可能的 Setup；每个策略页回答：在什么情景下、交易什么价格行为、怎样触发、什么事实使命题失效、stop 与 target 的锚点类别。

策略层是 **Application 层**：只综合和本地应用 core 已定义的概念，不建立新的最低定义，不生成可直接执行的订单参数。所有概念的完整定义以 core 权威页为准，本目录只保留必要摘要并链接权威页。

## 与 core、reference 的职责边界

| 目录 | 唯一职责 |
| --- | --- |
| [core](../core/README.md) | 解释市场为什么这样运动，以及概念之间怎样关联（权威定义所在） |
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

## 页面类型

| 类型 | 含义 |
| --- | --- |
| Index | 目录与导航，不建立策略命题 |
| Application（策略页） | 可检查的策略原型：回答 premise、触发、失效、stop 锚点、目标与管理 |
| Application（目标构造页） | 目标与结构构造说明，不独立成立入场策略（如 [量度目标构造](breakout/measured_move_breakout.md)） |
| Application（覆盖层页） | 叠加约束（时段、时间风险），不建立新家族（见 [时段覆盖层](session/README.md)） |
| Application（决策协议页） | 把策略页已有概念操作化为可观察的选择条件（版本选择、stop/target/管理绑定）；可收紧候选资格，但不得扩大 premise、重定义概念或增加未经授权的概率/订单执行规则（见 [决策协议](protocols/README.md)） |

## 核验工具

| 工具 | 用途 |
| --- | --- |
| [覆盖矩阵](coverage_matrix.md) | 核验五个已注册家族 × 当前状态与证据词汇不存在未处理组合；行号 R01–R46 + 全局行 G01，21 个实际策略页全部直接链接 |
| [决策流程图](decision_flow.md) | 覆盖矩阵的视觉投影：opening 检查 → 基础状态 → MTR → 晚段形态 → continuation 分支 → PREMISE_SELECT（STRATEGY/WATCH/NO_TRADE 统一裁决，含 G01 空间裁决）→ 时段/时间校验（按所选候选持有期，R28）→ 唯一叶子 |

## 执行清单（从策略页到 Trade Plan）

策略页是原型：它告诉你「看什么、怎样触发、什么使它失效、stop 与 target 锚在哪类结构」，但**不给你具体价格**；[决策协议](protocols/README.md) 绑定选项选择条件。入场前必须逐项写清下列字段，全部写清前不下单：

| 步骤 | 写什么 | 来自策略页哪一节 |
| --- | --- | --- |
| 1. Premise | 一句话：「我在交易什么」（如：强趋势首次浅回调恢复） | 交易命题 |
| 2. 触发 | 具体订单：具体参照事件或 signal bar 的触发位 + 订单类型（stop entry / limit / 收盘市价） | 触发类别 |
| 3. 失效清单 | 会使 premise 失效的可观察事实清单（逐条可核对） | 失效 |
| 4. Active protective stop | 具体价格 + 依据（把 stop 锚点类别落到实际结构价位；signal bar 另一端仅在同时是完整失效边界时可用） | Stop 锚点 |
| 5. Profit target | 具体价格 + 依据（把目标类别落到实际 magnet / 量度价位；非"等它涨"） | 目标 |
| 6. 仓位 | 由 entry → active stop 的风险距离与账户风险上限算出；scale-in 则写全部层总风险 | 目标与管理 + 跨情景基线 |
| 7. 管理 | 入场前选定 scalp 或 swing；写出正常回调容忍、部分退出与 premise 变化退出的分支 | 目标与管理 + 三层退出保护 |
| 8. Trader's Equation | 用同一组 entry / stop / target 检查二结果近似：p(win) × reward − p(loss) × risk − costs > 0；存在部分退出、scratch 等结果时按 core 拆分更多互斥结果 | 跨情景基线 |

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
检查对应策略页的触发类别、失效事实与目标类别
    ↓
Trader's Equation：概率、risk、reward、成本来自同一方案
    ↓
Trade Plan：entry、active protective stop、target、仓位、management
```

模糊状态的逐层 fallback 见 [市场周期](../core/01_market_cycle/00_market_cycle.md)，位置与控制见 [Context](../core/02_context/00_context_location_control.md)，Trader's Equation 见 [概率、风险和回报](../core/00_method/01_probability_risk_reward.md)，完整计划 schema 见 [从 Setup 到交易计划](../core/06_trade_plan_and_management/00_trade_plan.md)。

## 跨情景基线（全部链接 core，不在此重复定义）

| 主题 | 权威位置 | 策略层如何继承 |
| --- | --- | --- |
| Stop entry / protective stop | [两类 Stop](../core/03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md) | 触发用 stop entry，保护用结构 stop，两者用途不同 |
| 二次信号与陷阱 | [二次入场和陷阱](../core/03_acceptance_and_order_logic/03_second_entries_and_traps.md) | second signal / second-entry opportunity / actual fill 三层分开 |
| 接受与失败证据 | [接受、失望与失败证据](../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md) | follow-through、disappointment、premise 变化、trade failure、trapped in/out、Pain Trade（行为模型，不构成独立入场依据） |
| 限价单环境 | [限价单市场](../core/03_acceptance_and_order_logic/02_limit_order_market.md) | buy below / sell above 只在对应环境中使用 |
| Scalp / Swing / TBTL | [Scalp 与 Swing](../core/06_trade_plan_and_management/01_scalp_vs_swing.md) | 入场前定管理方式，不临场切换 |
| 加仓减仓 | [加仓与减仓](../core/06_trade_plan_and_management/02_scaling_in_out.md) | scale-in 总风险在第一笔 entry 前确定 |
| 目标构造 | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md) | magnet、measured move 的构造与投射起点 |
| 心理与纪律 | [风险与心理纪律](../core/06_trade_plan_and_management/03_risk_psychology.md) | OPM/沉没纪律、FOMO 边界、小仓宽 stop 早期参与的前提 |

## 相关来源

- core 框架入口与权威注册表：[core/README.md](../core/README.md)
- Setup 家族：[Setups](../core/05_setups/README.md)
- 术语速查：[核心术语表](../reference/glossary.md)
