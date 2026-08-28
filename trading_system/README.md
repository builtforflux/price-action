# Trading System

本目录是可脱离 `reference/` 独立运行的交易系统。它把 Brooks 价格行为知识组织为一条从市场事实到交易计划、账户执行与复盘的闭环，而不是形态或 Setup 目录。

## 运行入口

从[价格行为交易系统总流程](overall_flow.md)开始：

```text
Safety Guard + Frame
→ Market Read：继承 Context → Price Map → Current Move → Active Test → Context Update
→ Long / Short Opportunity Set
→ Trade Construction：构造当前 Candidates
→ Decision：比较并只选一条，或等待消歧事件，或不交易
→ Execution：Intent → Order → Fill → Exposure → Protection
→ Hold / Add / Reduce / Exit → Review
```

首次看图或 Reframe 运行完整 Checklist；普通新 K 线或相关事件只从最早变化处增量传播；已有订单、仓位或异常时按真实账户状态分派。检查可以是观察、心中确认或工具计算，只有计划、风险、执行或复盘边界改变时才保存必要增量。

## 文件职责

| 层次 | 文件 | 唯一职责 |
| --- | --- | --- |
| Runtime | [总流程](overall_flow.md) | 运行模式、检查顺序、增量传播、账户入口与必要记录 |
| Market Contract | [Market Read 与 Opportunity](market_read_and_opportunities.md) | Price Map、Current Move、Active Test、Context、结构目标与双向 Opportunity |
| Decision Contract | [交易决策与计划](decision_and_plan.md) | Context Permission、Candidate 构造与比较、Decision、Trade Plan 和风险数学 |
| Execution Contract | [执行、持仓与复盘](execution_management_and_review.md) | 订单、成交、Exposure、Protection、持仓动作、退出与复盘 |
| Runtime Navigation | [市场决策事件导航](market_decision_events.md) | 从可观察变化定位最早重开步骤，不定义另一套 Pattern 路由 |
| Rule Registry | [条件规则台账](conditional_rules_registry.md) | 条件概率模板、当前 Rule Match、替代顺序与隔离项 |
| Acceptance Examples | [完整流程场景测试](worked_examples.md) | 验证共同契约怎样处理不同场景，不建立新规则 |

`overall_flow.md` 决定现在看什么和下一步去哪里；三个 Core Contract 唯一定义市场、决策和账户语义；导航、规则与示例只按需展开。

## 知识怎样融入共同链路

- 底层事实只登记一次；价格组织、过程、几何、次序、外层功能与行为路径分别保留不可替代的职责，但同源名称不重复增加概率（如 H/L、Double Test、Wedge、Flag、Triangle、MTR）。
- 结构产生的 Region、Neckline、Channel / Range 边界和 measured-move 目标进入 Price Map；当前运动与测试进入 Current Move / Active Test；方向路径进入 Opportunity；Entry、Stop 与交易目标由 Candidate 选择。
- 不同目标、周期、Outcome Horizon 或判断时点必须分开。条件概率只有完成目标、周期、horizon、时点和适用条件匹配后才能进入当前路径或 Trader's Equation。
- 图表事实、订单事实和账户事实始终分开；Chart Trigger 不表示账户成交，交易计划也不表示实际 Protection 已生效。

每类价格行为知识都必须说明 Formation、Role / Owner、Derivation、Lifecycle 和 Boundary / Dedup：从哪些事实形成，改变哪个 Market Read 对象，如何更新和避免同源重复，以及通过共同链可能影响哪些下游对象；Candidate、风险与执行动作仍由各自 Contract 唯一定义。

## 权威边界

`trading_system/` 定义完整运行语义；[`reference/`](../reference/README.md)保存正式来源、逐讲证据、重复、分母、冲突和翻译边界，不直接许可交易。新增知识只有在改变事实、结构、目标、路径、概率、计划、执行或复盘时才进入本目录；数学、分母、来源或翻译不清的内容保持隔离。
