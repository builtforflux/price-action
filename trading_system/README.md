# Trading System

本目录是可脱离 `reference/` 独立运行的交易系统。它把 Brooks 价格行为理念组织成一条决策链，而不是形态或 Setup 目录。

```text
Safety Check
→ Market Read：继承 Context → Price Map → Current Move → Active Test → 确认或重构 Context
→ Opportunity Set：现实的多空机会与可能先后顺序
→ Trade Construction：当前允许表达机会的 Trigger / Entry Method / Planned Stop / Targets / Size
→ Trade Gate：Execute / Wait / No Trade
→ Order / Position / Protection
→ Event Update / Exit / Review
```

## 文件职责

1. [总流程](overall_flow.md)：盘中入口、运行顺序、状态路由、检查清单与最小记录。
2. [市场结构与机会](market_read_and_opportunities.md)：定义 Market Read、连续价格事实、Context、Price Map、Current Move、Active Test 和双向 Opportunity Set。
3. [交易决策与计划](decision_and_plan.md)：应用 Context Permission，把具备当前表达资格的 Opportunity 变成 Candidate，构造判断时点、Entry Method、Planned Stop、Targets、仓位与管理，再由 Trade Gate 比较方程并冻结所选 Trade Plan。
4. [执行、管理与复盘](execution_management_and_review.md)：订单、成交、保护、持仓更新、退出和复盘。
5. [条件规则台账](conditional_rules_registry.md)：保存可审计的条件概率与适用边界，不是另一套路由。
6. [完整示例](worked_examples.md)：用复合多空场景走完整流程。

每个事实只在承担唯一职责的文件定义；其他文档引用结论。`overall_flow.md` 决定现在看什么和下一步做什么，下级文档负责需要时展开知识。

## 三层使用方式

- **系统知识与内部模型**：完整保存事实、对象、概率和状态语义，供学习、实现和复盘使用。
- **实盘检查**：快速扫图或心中确认；普通 K 线没有改变 Context、机会、风险或动作时，不产生记录。
- **必要记录**：只在形成或改变计划、订单、仓位、保护、关键等待条件、异常或交易结束时保存最小增量。

“必须检查”不等于“必须书面记录”。空仓扫描和持仓更新以数秒为目标；只有新建计划、改变风险、发生执行事件或交易结束时，才进入较完整记录。

## 运行不变量

- 先读市场，再构造多空机会；先确定目标，再设计 Entry。
- 多空理由分别组织，不按名称数量投票；同一价格链的多个标签只算一次。
- 独立汇合可以增强机会，但必须说明它增强的是 Activation、接受、延续、到达目标，还是目标区反应。
- 不同方向、角色、目标或 horizon 分成不同 Opportunity；可以表达“先修正、后顺势”的序列。
- Price Map 唯一登记区域；Opportunity 为区域分配 Support / Resistance、Entry Area、Obstacle、Magnet、Target 与 Invalidation Reference 角色。
- Opportunity 拥有 Objective、Market Targets、Activation、Invalidation 和 Market Probability；Candidate 拥有 Trigger、Entry Method、Planned Protective Stop、选定 Targets 与 Candidate Outcome Probability。
- 只为当前可表达的少数 Opportunity 计算 Candidate；只把被选 Candidate 冻结成 Trade Plan。
- `Wait` 保存下一事实和过期条件，不藏一份尚未重新计算的可执行计划。
- 订单意图、经纪商确认、实际成交、敞口和保护状态始终分开。
- 持仓中同时更新所选 Opportunity 与现实竞争 Opportunity；竞争路径获得接受先触发原仓位处理，反向风险仍需新 Candidate。
- Trailing / Breakeven 只使用已经形成、能容纳管理周期正常波动并降低开放风险的新保护锚点。
