# 趋势第二次恢复信号（H2/L2）

> **状态：Strategy / Application**
>
> 本文把趋势延续命题实例化为"第一次恢复无延伸后的二次触发"；它不生成具体订单参数。

## 交易命题

第一次恢复尝试缺乏延伸，反方仍未建立控制；同一方向第二次触发（H2/L2）表明第一次回撤只是测试，原趋势恢复。

## 适用情景与路由

- 原趋势控制仍有效（Always In 或累积压力支持趋势方）；
- 回调中第一次上破尝试（H1）或下破尝试（L1）未获跟进；
- 第二次尝试形成 H2 / L2；
- 回调深度、持续时间和重叠仍符合当前 trend / channel，而不是已转成 trading range 或反向突破。

H1/H2/L1/L2 的几何计数见 [H1、H2、L1、L2](../../core/04_patterns/02_h1_h2_l1_l2.md)；"第二次"的三层口径（second signal、second-entry opportunity、actual fill）见 [二次入场和陷阱](../../core/03_acceptance_and_order_logic/03_second_entries_and_traps.md)。

## 触发类别

Buy stop 越过第二次 signal bar 高点（H2），或 sell stop 越过第二次 signal bar 低点（L2）。触发本身不代表成功，entry bar 与后续 follow-through 检验信号质量。

## Premise 失效

- 定义回调的结构被反向有效突破（牛：回调低点或 major higher low 被向下跌破；熊：回调高点或 major lower high 被向上突破）；
- 反向运动获得足以改变 market-cycle 判断的跟进；
- 计数进入 H4/L4 及以上时先检查 pullback 是否已变成 trading range、endless pullback 或反向趋势。

## Protective Stop 锚点

最近 major higher low / lower high、完整回调极值或其他能否定趋势 premise 的结构外。

## 直接预期与目标

直接预期是原趋势恢复并测试旧极值；H2/L2 只组织回调和触发，不单独产生更远目标，也不证明趋势仍在。

## 管理边界

可以按 scalp 管理；强趋势且空间足够时支持 swing。触发后 entry bar 很弱或 follow-through 持续失望时重新检查 premise，不能只因“第二次”名称继续持有。

## 语境数字与先验

- 强趋势中 H2/L2 常有意义（反方第二次失败后趋势方可能恢复）；
- Trading range 中 H2/L2 经常失败，因为顺势跟进不足；区间边缘方向指向区间内部时才更可能有意义（见 [区间第二次信号](../range/edge_second_signal.md)）。

## 常见误读

- 数到二就买或卖；
- 不区分趋势与区间；
- 忽略触发后 entry bar 很弱；
- 忽略 failed H2 / failed L2 的被困交易者。

## 相关来源

- [H1、H2、L1、L2](../../core/04_patterns/02_h1_h2_l1_l2.md)
- [趋势延续 Setup](../../core/05_setups/01_trend_continuation.md)
- [二次入场和陷阱](../../core/03_acceptance_and_order_logic/03_second_entries_and_traps.md)
- [接受、失望与失败证据](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md)
