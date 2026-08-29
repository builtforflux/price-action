# Al Brooks 价格行为交易方法

本仓库把 Al Brooks 价格行为材料分成两个互相引用、但不互相越权的部分：

| 入口 | 回答的问题 |
| --- | --- |
| [Trading System](trading_system/README.md) | 怎样从位置、路径与双向机会运行到交易、账户闭环与复盘？ |
| [Reference](reference/README.md) | 知识来自哪里、条件是什么、怎样核验、有哪些冲突？ |

建议先读[统一运行流程](trading_system/overall_flow.md)，需要核对来源时再进入 Reference。

## 权威边界

Reference 保存来源主张、原始锚点、重复、冲突、核验状态和待研究启发式；它不定义运行方法，也不直接决定交易。Trading System 决定知识怎样进入位置、测试、市场结构、双向机会、交易表达与复盘。

数值知识只有在当前目标、条件、周期、期限、判断时点和具体交易表达完全匹配时，才能进入交易者方程。当前仓库没有生产级校准概率；没有匹配数值时使用定性判断，不伪造期望证明，也不自动禁止人工交易。详见[概率与证据边界](trading_system/probability_and_evidence_boundaries.md)。

## 不可违反的原则

- 市场事实与账户事实分别建立，只在交易决策和持仓管理时互相约束。
- 位置、到达路径、当前测试、状态与机会按因果顺序更新。
- Pattern、H/L、Wedge、Double Test、Flag、Triangle、MTR 等是可重合视图，不拥有专用交易流程，也不按名称重复计权。
- 市场机会、交易表达、计划、订单、成交、仓位、保护和结果各有唯一职责。
- 初次入场、加仓、runner 延伸和管理边界改变，都按当前市场与整仓风险重新判断。
- 仓位归零后仍须结清所有可能改变仓位的订单并核对成交与费用，才能稳定关闭。
- 市场、交易、账户与流程结果分开结算。

课程知识与当前方法的关系见[课程知识与方法关系](reference/course/course_to_method_map.md)；数字、数学和来源限制见[边界与冲突](reference/course/boundaries_and_conflicts.md)。
