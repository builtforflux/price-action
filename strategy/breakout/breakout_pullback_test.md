# 突破回踩延续（Breakout Pullback / Test）

> **状态：Strategy / Application**
>
> 本文把突破延续命题实例化为"突破获接受后的回调守住"；它不生成具体订单参数。

## 交易命题

回调或回测守住旧边界，原突破方向恢复并延续。Breakout test 更具体地测试原边界、突破价或相关入场区域；测试可能很快发生，也可能延后许多根。

## 两个确认版本

- **版本 A（已接受后的普通 pullback）**：接受证据已由"收盘在外 + 跟进"完成，回调守住旧边界只是额外证据；
- **版本 B（首次回测完成确认）**：突破后首次回调/回测守住旧边界或突破点本身构成"突破点未被快速收回"的接受证据，随后重新触发。

## 情景判定

- 版本 A 要求接受证据已由收盘在外 + 跟进完成；版本 B 由首次回测守住完成接受证据；
- 回调守住旧边界或突破点；
- 旧区域未被重新接受；
- 新区域保留足够目标空间。

定义见 [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md#breakout-pullback-与-breakout-test)。

## 触发类别

回调结束后的重新触发（stop entry 越过回调 signal bar 极值）。这是确认版本的一种：确认增加，但 entry 更差、剩余目标更近，必须与预判版本分开计算。

## 失效与 Stop 锚点

- 价格明确回到旧区域并获得反向跟进；
- Failed breakout 确认：突破尝试缺乏接受并明确回到或重新接受旧区域。

Stop 锚点类别：回踩 swing 外，或足以证明旧区域重新接受的边界外。

## 目标与管理

直接预期是第二腿或清楚结构的 measured move。回踩守住是额外接受证据，**不是突破获接受的必要步骤**。管理：确认版 entry 更差，scalp 或 swing 取决于剩余目标空间；正常回踩允许，旧区域重新接受或跟进消失时按 premise 变化退出。

## 常见误读

- 把单次越界当成新价格已被接受；
- 认为回踩是突破成立的必需条件；
- 把确认版本的概率套给预判版本的 entry。

## 相关来源

- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md)
- [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md)
- [接受、失望与失败证据](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md)
