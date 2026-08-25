# 价格行为交易运行模型

> **状态：Strategy / Index**

本目录保存价格行为交易的统一运行流程与条件规则。交易机会从活动结构、当前测试、结果路径、条件概率和目标路径产生。

## 文件

1. [价格行为交易总流程](overall_flow.md)：唯一运行入口；定义市场事实怎样更新活动结构与当前测试，怎样选择结果路径并形成交易计划、订单和持仓管理。
2. [规则、条件关系与冲突台账](rules_and_conflicts.md)：集中保存条件概率、概念关系、适用范围、表面冲突和隔离规则。

## 边界

- `core/` 继续负责概念最低定义。
- `reference/` 继续负责来源、课程材料和原始冲突记录。
- `strategy/overall_flow.md` 负责编排统一运行闭环。
- Pattern、Gap、H/L、Wedge、Double Test、Flag、Measured Move、Stop 和 Management 都作为闭环中的结构、证据、目标或状态字段使用。
