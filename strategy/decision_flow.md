# 情景决策流程图（Decision Flow）

> **状态：Strategy / Index（覆盖矩阵的候选收集投影）**
>
> 本图是[覆盖矩阵](coverage_matrix.md)的可视化。它不是要求执行者在每个节点只选一条出边的互斥决策树，而是对同一价格快照运行多个候选收集器，再经同家族精度消歧、候选级时段过滤和跨 premise 选择，最终输出唯一叶子。

## 运行规则

固定顺序为：

```text
绑定周期与观察窗口
    ↓
收集 session / opening 覆盖信息（只叠加，不替代基础状态）
    ↓
并行收集全局 Breakout Mode（跨基础状态叠加）
    ↓
判定基础状态与趋势阶段
    ↓
在同一快照上运行适用的候选收集器
    ↓
同家族精度消歧（命名子型优先，通用兜底最后承接）
    ↓
按每个候选自己的持有期执行 R28 时间过滤
    ↓
PREMISE_SELECT（跨 premise 裁决）
    ↓
STRATEGY / WATCH / NO_TRADE
```

候选收集器的输出分为四类：

| 输出 | 含义 | 是否参与最终选择 |
| --- | --- | --- |
| `STRATEGY_CANDIDATE` | 证据完整的策略候选 | 先经同家族精度消歧，再进入 PSEL |
| `WATCH_FLAG` | 某项候选仍缺少什么证据，或需要重新分类 | 无完整 STRATEGY 时可成为 WATCH 终端；不能压过已完整策略 |
| `HARD_NO_TRADE` | 对当前候选或位置生效的硬回避约束 | 先过滤其适用范围内的候选 |
| `CHECKPOINT` | 晚段风险、概率或管理提示 | 只附着于保留下来的策略，不产生独立叶子 |

这些输出可以同时存在。例如趋势线破坏但旧极值测试未完成时，可以收集 `R29 WATCH_FLAG`；若同一快照另有完整的趋势延续候选，R29 只记录“MTR 尚未完成”，不能把整轮提前终止为 WATCH。

## 执行者步骤

1. **绑定观察尺度**：写明交易周期、外层 Context、当前观察窗口和预期持有方式；不同周期各自分类，不能把局部状态覆盖外层状态。
2. **收集覆盖信息**：记录 opening、Opening BOM、Opening Reversal、Trend from the Open 和 late-session 等信息。它们只增加候选来源与时段约束，之后仍须进入基础状态分类。
3. **收集跨层 BOM**：Breakout Mode 可以叠加在任意基础状态上；只有尚无一侧获得足以排除另一侧的持续接受，且双向候选的边界、触发、失效和空间均可声明时，才收集 R26。R45 只增加 opening 约束。
4. **判定基础状态**：先区分 trend / trading range；trend 再区分 spike / tight channel / broad channel。状态不清时以 trading range 作为管理假设并产生 R35 WATCH；这不授权尚未成熟的 range fade，也不得截断已经成立的 R26。
5. **运行适用收集器**：trend 同时检查 MTR、minor reversal、continuation 与状态检查点；成熟 trading range 同时检查 fade、breakout 与硬回避约束。一个行情可以命中多个收集器。
6. **同家族精度消歧**：同一母命题下，命名子型完整成立时移除通用兜底；只有没有更具体子型时才保留 R47、R48 等兜底。这个步骤只选“用哪一页描述同一 premise”，不在不同 premise 之间选方向。
7. **逐候选校验 R28**：每个完整候选先用自己的 entry、stop、target 和持有方式检查剩余时间；拒绝时间不足的 swing，但保留已经独立建立且时间足够的 scalp。
8. **PSEL 跨 premise 裁决**：先应用候选相关硬约束和 G01，再检查每个候选是否至少有两个相互补充、没有重复计票的理由，并记录当前最有力的 opposing evidence 与 update condition；独立理由或必要触发不足时输出 WATCH，premise 已否定时输出 NO_TRADE。其后再检查时间合格候选各自的 Trader's Equation；多个不同 premise 均通过时，必须记录明确选择理由。无法给出不依赖结果的选择理由时输出 WATCH / NO_TRADE。
9. **建立 Trade Plan**：按[策略入口的执行清单](README.md#执行清单从策略页到-trade-plan)实例化 supporting reasons、opposing evidence、update condition、具体 entry、active protective stop、target、仓位和管理。

## 候选收集与裁决图

```mermaid
flowchart TD
    ENTRY["读图开始<br/>绑定交易周期、外层 Context、观察窗口与持有意图"] --> OVERLAY["SESSION_OVERLAY_COLLECT<br/>记录 opening / R27 / R41 / R45 / R46 / late 信息<br/>收集后仍继续基础状态分类"]
    OVERLAY --> SESSIONOUT["SESSION_OUTPUT（仅在各自行条件成立时）<br/>R27 → WATCH_FLAG<br/>R41 → STRATEGY_CANDIDATE<br/>R45 / R46 → OVERLAY_FLAG<br/>late → 送入 R28 候选过滤"]
    OVERLAY --> BASE{"BASE_CLASSIFY<br/>基础状态与当前趋势阶段<br/>Core：Market Cycle"}
    OVERLAY --> BOMC["GLOBAL_BOM_COLLECT<br/>R26 跨层叠加；不依赖 BASE 分类<br/>R45 仅附加 opening 约束"]
    BOMC --> S26G["STRATEGY_CANDIDATE：R26<br/>尚无单侧持续接受；双向边界、两套计划与各自空间均可声明"]

    BASE -->|"状态不清"| W35["WATCH_FLAG：R35<br/>以 trading range 作为管理假设<br/>不授权未成熟 fade；不截断全局 R26"]
    BASE -->|"trend：spike / tight / broad"| TFORK["TREND_COLLECTORS<br/>同一快照并行运行"]
    BASE -->|"成熟 trading range"| RFORK["RANGE_COLLECTORS<br/>同一快照并行运行"]

    subgraph TREND["Trend 候选收集（输出可同时成立）"]
        TFORK --> MTRC["MTR_COLLECT<br/>R29–R31 / R34 / R43–R44"]
        TFORK --> MINORC["MINOR_REVERSAL_COLLECT<br/>R06–R07 / R12 / R32–R33 / R42 / R48"]
        TFORK --> CONTC["CONTINUATION_COLLECT<br/>R01 / R03–R05 / R08 / R14–R15 / R36–R40 / R47"]
        TFORK --> CHECKC["CHECKPOINT_COLLECT<br/>R09–R11"]

        MTRC --> MTRS{"MTR 进度"}
        MTRS -->|"通道破坏，旧极值测试未决"| W29["WATCH_FLAG：R29"]
        MTRS -->|"测试失败，尚无反向触发"| W44["WATCH_FLAG：R44"]
        MTRS -->|"旧极值重新接受 / 原趋势重建控制"| W34["WATCH_FLAG：R34<br/>仅重置 MTR 证据链"]
        MTRS -->|"测试失败 + 早期反向触发"| S30["STRATEGY_CANDIDATE：R30<br/>MTR 早期版"]
        MTRS -->|"测试失败 + 强反向突破和跟进"| S31["STRATEGY_CANDIDATE：R31<br/>MTR 确认版"]
        MTRS -->|"合格 ET + 反向突破、跟进与接受"| S43["STRATEGY_CANDIDATE：R43<br/>Expanding Triangle MTR"]

        MINORC --> MINORS{"逆势结构与接受证据"}
        MINORS -->|"高潮式推进，无反向接受"| W06["WATCH_FLAG：R06"]
        MINORS -->|"高潮后修正"| S07["STRATEGY_CANDIDATE：R07"]
        MINORS -->|"tight channel 合格逆势触发"| S12["STRATEGY_CANDIDATE：R12<br/>命名子型或通用 minor"]
        MINORS -->|"wedge / final flag"| S3233["STRATEGY_CANDIDATE：R32 / R33"]
        MINORS -->|"double top-bottom + neckline 触发；MTR 链未完整"| S42["STRATEGY_CANDIDATE：R42<br/>minor scalp 子型"]
        MINORS -->|"其他重要位置合格触发"| S48["STRATEGY_CANDIDATE：R48<br/>通用 minor 兜底"]

        CONTC --> STAGEC{"当前趋势阶段与结构"}
        STAGEC -->|"spike"| SPIKEC["SPIKE_COLLECT<br/>R01 / R03–R05 / R36–R40 / R47"]
        STAGEC -->|"tight channel"| TIGHTC["TIGHT_COLLECT<br/>R08 / R13 / R37–R39 / R47"]
        STAGEC -->|"broad channel"| BROADC["BROAD_COLLECT<br/>R14–R15 / R47"]

        SPIKEC --> SPIKEOUT["收集 R01 / R03 / R04 / R05 / R36 / R37 / R38 / R39 / R40<br/>无更具体子型时收集 R47"]
        TIGHTC --> TIGHTOUT["收集 R08 / R37 / R38 / R39<br/>endless pullback 产生 R13 WATCH<br/>无更具体子型时收集 R47"]
        BROADC --> BROADOUT["条件成立时独立收集 R14 STRATEGY 与 R15 WATCH<br/>两者可并存；无更具体子型时收集 R47"]

        CHECKC --> CP["CHECKPOINT：R09 / R10 / R11<br/>只附着，不参与叶子优先级"]
    end

    subgraph RANGE["Trading Range 候选收集（输出可同时成立）"]
        RFORK --> FADEC["FADE_COLLECT<br/>R16–R19"]
        RFORK --> BOC["BREAKOUT_COLLECT<br/>R20–R22 / R25 / R40"]
        RFORK --> HARDC["HARD_CONSTRAINT_COLLECT<br/>R23 / R24"]

        FADEC --> FADEOUT["收集 R16 / R17 / R18 / R19<br/>命名子型优先于 R16 通用承接"]
        BOC --> BOOUT["收集 R20 / R21 / R22 / R25 / R40<br/>空间不足仅标记候选相关 G01 输入"]
        HARDC --> HARDOUT["HARD_NO_TRADE：R23 / R24<br/>只过滤区间中部或 barbwire 内候选"]
    end

    SESSIONOUT --> COLLECT
    S26G --> COLLECT
    W35 --> COLLECT
    W29 --> COLLECT
    W44 --> COLLECT
    W34 --> COLLECT
    S30 --> COLLECT
    S31 --> COLLECT
    W06 --> COLLECT
    S07 --> COLLECT
    S12 --> COLLECT
    S3233 --> COLLECT
    S42 --> COLLECT
    S43 --> COLLECT
    S48 --> COLLECT
    SPIKEOUT --> COLLECT
    TIGHTOUT --> COLLECT
    BROADOUT --> COLLECT
    CP --> COLLECT
    FADEOUT --> COLLECT
    BOOUT --> COLLECT
    HARDOUT --> COLLECT

    COLLECT["CANDIDATE_SET<br/>合并 STRATEGY_CANDIDATE / WATCH_FLAG / HARD_NO_TRADE / CHECKPOINT<br/>并叠加 R27 / R41 / R45 / R46 session 信息"] --> SPEC["SPECIFICITY_RESOLVE<br/>同一母命题内：命名子型优先<br/>无具体子型才保留 R16 / R47 / R48 等通用承接"]

    SPEC --> TIMEF["CANDIDATE_TIME_FILTER：R28<br/>逐候选按自己的持有期、目标距离与剩余 session 时间过滤<br/>一个 swing 失败不删除独立合格 scalp"]
    TIMEF --> PSEL{"PREMISE_SELECT<br/>独立理由 + 反方证据 + 更新条件<br/>跨 premise 裁决"}
    PSEL -->|"候选适用的 R23/R24 硬约束过滤后无剩余"| T_NT
    PSEL -->|"所有可识别候选均无现实空间（G01；R02/R22 为例）"| T_NT
    PSEL -->|"完整候选均被 R28 拒绝，且无独立时间合格候选"| T_NT
    PSEL -->|"至少一个时间合格的完整候选方程成立，且明确选定 premise"| T_STRAT
    PSEL -->|"多个时间合格候选方程成立；等待可观察新证据才能消歧"| T_WATCH
    PSEL -->|"多个时间合格候选方程成立；无预写选择标准且等待也不能消歧"| T_NT
    PSEL -->|"时间合格的完整候选均方程不成立"| T_NT
    PSEL -->|"无完整策略，仍有 R05/R06/R13/R15/R27/R29/R34/R35/R44 WATCH"| T_WATCH
    PSEL -->|"均无候选或只有 CHECKPOINT"| T_NT

    subgraph TERMINALS["唯一终端"]
        T_STRAT["STRATEGY<br/>进入所选策略页并建立 Trade Plan"]
        T_WATCH["WATCH<br/>记录所需证据；新数据到来后从入口重新运行"]
        T_NT["NO_TRADE<br/>记录硬约束、空间、时间或方程原因"]
    end
```

## 裁决细则

### 1. 覆盖层不参与基础状态竞争

- Opening BOM（R45）叠加到通用 Breakout Mode（R26）；
- Opening Reversal（R27）只记录早段语境和缺失证据，证据足够后仍路由到 range fade、MTR 或 minor reversal；
- Opening-range breakout（R41）只有在明确边界外获得接受后才成为突破策略候选；
- Trend from the Open（R46）叠加于 R01、R03 或 R47；
- late-session 信息在候选各自绑定持有期后执行 R28；它过滤候选，不提前全局否决，也不等最终选定后才首次检查。

### 2. 同家族精度消歧

同一母命题下只保留最准确的策略页：

| 母命题 | 优先顺序 |
| --- | --- |
| 趋势延续 | R01 / R08 / R14 / R37–R39 等命名子型 → 无子型才用 R47 |
| 逆势修正 | R07 / R32 / R33 / R42 等命名子型 → 无子型才用 R48；tight-channel 路由 R12 仍按具体结构二次判定 |
| 区间 fade | R17 / R18 / R19 等命名进入方式 → 无更具体子型才使用 R16 通用确认 fade |
| 突破延续 | 按实际风险承担时点选择 BTC/STC、breakout pullback、failed failure 或 opening-range breakout；这些是不同版本/事件，不由通用兜底覆盖 |
| MTR | R30 / R31 表示早期/确认风险时点；R43 是合格 ET 子型。双顶/双底只有完整链成立时才作为 R30/R31 的结构证据，不完整时由 R42 按 minor scalp 承接 |

精度消歧不会改变方向、概率或 premise，也不会把一个候选的有利参数借给另一个候选。

### 3. WATCH 不提前截断完整策略

WATCH_FLAG 说明某个候选仍未完成。例如：

- R29 只说明 MTR 尚缺旧极值测试；
- R34 只说明旧 MTR 证据链已经重置；
- R06 只说明高潮后尚无合格逆势触发；
- R15 只说明 broad channel 出现 transition evidence；
- R05 只说明该 breakout attempt 尚未获得接受。

如果同一快照存在另一个完整 STRATEGY_CANDIDATE，PSEL 仍先检查完整策略；只有没有完整策略时，WATCH_FLAG 才输出 WATCH。

### 4. 硬 NO_TRADE 必须限定适用范围

R23 与 R24 过滤发生在区间中部或 barbwire 内的候选，不能自动否决发生在其他位置、其他周期或已明确脱离该结构的候选。G01 只有在当前所有可识别候选各自的现实 target 空间都不足时才成立。

## 可达性与一致性检查

- Mermaid 的主干是 `OVERLAY → SESSION/GLOBAL_BOM + BASE → COLLECTORS → CANDIDATE_SET → SPECIFICITY_RESOLVE → CANDIDATE_TIME_FILTER → PSEL → TERMINAL`；collector 内的分支是候选输出，不表示执行者只能选择一条；
- R01–R48 与 G01 均由 collector、说明表或 PSEL 明确登记；R02、R22 是 G01 示例，不要求独立策略节点；
- R09–R11 永远只作为 CHECKPOINT；
- MTR、minor reversal、continuation 和状态检查点在 trend 中互不截断；
- R26 作为跨层 collector 与 BASE 并行；fade、breakout 和硬约束在成熟 trading range 中并行收集；
- WATCH 是当前快照的终端；新数据到来后从入口重新运行，不在图内保留无限回边。

维护时人工核对矩阵 ID、collector 归属、入口与终端可达性，并用具体行情逐条走查候选能否正确共存和收敛。拓扑完整不等于语义正确；最终判断仍以 Core 定义、Reference 证据和候选自身 Trade Plan 为准。

## 相关来源

- [覆盖矩阵](coverage_matrix.md)（R01–R48、G01）
- [策略目录入口](README.md)
- [Core：市场周期](../core/01_market_cycle/00_market_cycle.md)
- [Core：什么是 Setup](../core/05_setups/00_what_is_a_setup.md)
