---
title: "Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications via Hierarchical Optimal Control"
aliases:
  - HOC-UADC
  - 无人机应急通信路径规划
tags:
  - literature-note
  - reading-note
  - UAV
  - ISAC
created: 2026-10-13
source: IEEE Transactions on Communications, Vol. 74, 2026
author: Shangpeng Wang, Ling Chen, Xiatong Hou, Xinyue Wang, Chenyuan Zhang, Haoran Yang, Haijun Zhang, Haixin Sun
year: 2026
journal: IEEE Transactions on Communications

theme: 城市应急通信场景下多无人机协同路径与角色协调的实时规划
study_area: UAV 辅助通信 / 轨迹优化 / 层次最优控制
methodology: 双层模型预测控制（战略层 MILP + 轨迹层 NMPC/SCP）
core_variable: mission makespan、数据采集总量、任务成功率、计算耗时
key_finding: 所提 HOC-UADC 框架使任务完成时间减少 8.6%、数据采集量提升 2.4%
relevance: 直接对应 UAV 应急通信与 ISAC 场景下的实时轨迹—资源联合优化问题

type: literature-note
zotero_key: "H8PIYWY4"
pdf_key: "2RVKF9X8"
doi: "10.1109/TCOMM.2026.3698909"
collection: "UAV"
note_path: "02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications.md"
fulltext_path: "03fulltext/UAV/H8PIYWY4.md"
status:
  - Reading
rating: 五星
---
# Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications via Hierarchical Optimal Control

---

# 📌 Basic Information（基本信息）

## Author
Shangpeng Wang, Ling Chen, Xiatong Hou, Xinyue Wang, Chenyuan Zhang, Haoran Yang, Haijun Zhang, Haixin Sun

## Year
2026

## Source
IEEE Transactions on Communications, Vol. 74, 2026｜DOI: 10.1109/TCOMM.2026.3698909

> Zotero 入口：zotero://select/library/items/H8PIYWY4
> PDF 入口：zotero://open-pdf/library/items/2RVKF9X8
> 全文 Markdown：[[03fulltext/UAV/H8PIYWY4]]

## Research Area

- UAV-Assisted Communication
- Path Planning / Trajectory Optimization
- Model Predictive Control
- Emergency Data Collection

---

# 1. Abstract Summary（一句话总结）

> 该文提出 HOC-UADC 层次最优控制框架，把多无人机应急通信中难以实时求解的大规模混合整数非线性规划（MINLP）分解为「战略层 MILP + 轨迹层 NMPC」的双层模型预测控制结构，在仿真中使任务完成时间减少 8.6%、数据采集量提升 2.4%。

---

# 2. Research Background（研究背景）

## 背景：

- 无人机作为移动中继，是城市环境中应急数据采集的关键技术，可克服遮挡造成的通信中断。
- 问题涉及离散决策（任务分配）与连续决策（轨迹）的强耦合，加上严格的数据采集时限与有限机载能量预算，构成大规模 MINLP。
- 该问题具有 NP-hard 性质，求解时间随规模指数增长，本质上不适合应急场景要求的快速实时决策。

> 原文：
> "These intricate interdependencies formulate a large-scale Mixed-Integer Non-Linear Program (MINLP). The NP-hard nature of this problem renders it computationally intractable, as solution times grow exponentially with scale, making it fundamentally unsuitable for the rapid, real-time decision-making required in emergency response [7]."

## Motivation（研究动机）

- 现有方法通常把问题解耦为路径规划与任务调度等子问题，这种分离不可避免地导致次优性能。
- 直接整体求解的整体式求解器在实时部署中计算上不可行。
- 现有模型常忽视无人机动态角色切换的需求，限制了系统功能灵活性与运行适应性。

> 原文：
> "Existing approaches typically simplify the problem by decoupling it into separate sub-problems, such as path planning and task scheduling. However, this separation inevitably leads to suboptimal performance [8], [9]."
>
> 原文：
> "Compounding this, current models often overlook the need for dynamic UAV role-switching, limiting the system’s functional flexibility and operational adaptability."

## Application Scenario（应用场景）

- 城市应急通信网络中的多无人机协同数据采集
- 灾害导致通信中断时的临时中继网络部署
- 有严格时限与能量约束的 IoT 数据收集任务
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在严格时限与机载能量约束下，对多无人机应急通信网络的轨迹、任务调度与多跳数据中继进行联合优化，并使求解规模可支撑实时部署？

核心问题：

- 如何化解 MINLP 的计算不可行性，使其适用于实时决策？
- 如何在统一框架内处理离散的任务分配/角色切换与连续的轨迹优化？
- 如何刻画动态 LoS 遮挡、异构 IoT 数据需求与截止时间之间的相互依赖？

---

# 4. Related Work（相关工作）

已有方法：

1. **基础路径规划**：早期研究聚焦于生成高效飞行路径。
2. **元启发式方法**：遗传算法、粒子群优化等被用于搜索最优路径。
3. **解耦式方法**：把轨迹优化与通信调度分离处理，降低求解难度但导致次优。
4. **整体式求解器**：尝试联合求最优解，但实时部署中计算不可行。

现有不足：

- 解耦方法不可避免地带来次优性能。
- 整体式方法求解时间随规模指数增长，无法满足应急实时性。
- 现有模型普遍忽视无人机的动态角色切换能力。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出 HOC-UADC 层次最优控制框架，将原本难以求解的 MINLP 分解为**双层模型预测控制（MPC）**架构。
- 战略层用线性化的混合整数线性规划（MILP）做长期机队协调；轨迹层用非线性模型预测控制（NMPC）做实时高精度控制与动态角色切换。

> 原文：
> "We introduce a novel two-layer hierarchical optimization framework to solve the intractable MINLP. The strategic layer employs a linearized Mixed-Integer Linear Program (MILP) for efficient long-term fleet coordination, which is then dynamically adjusted through an RHC loop to ensure adaptability."

## Model / Framework

模型结构（双层 MPC）：

- **战略层（Strategic Layer / GMP）**：在滚动时域控制（RHC）回路内对原问题线性化，构建覆盖 [τk, τk + TH] 时域的 MILP，负责长期任务与轨迹规划。
- **轨迹层（Trajectory Layer）**：采用非线性模型预测控制（NMPC），内嵌组合式方案，将离散的角色切换与连续的轨迹优化智能解耦。
- **求解方式**：轨迹层通过序列凸规划（SCP）高效求解，产生物理可行的局部最优实时控制动作。

## Algorithm / Technique

采用：

- Mixed-Integer Linear Program（MILP，战略层）
- Receding Horizon Control / RHC（滚动时域控制）
- Non-linear Model Predictive Control（NMPC，轨迹层）
- Sequential Convex Programming（SCP，序列凸规划）
- 嵌入式组合解耦方案（角色切换 ↔ 轨迹优化）

## Key Steps

算法 1（Global Mission Planner with RHC）主要步骤：

1. 初始化：τk ← 0，任务集 T ← I0，前次计划 Πprev ← ∅。
2. 状态测量：获取当前无人机状态与任务执行状态。
3. 战略重优化：基于当前状态 Sk，在时域 [τk, τk + TH] 上构建 MILP。
4. 在规定时间预算内求解 MILP；若获得可行解，则记录 Π*(τk) ← Πopt(τk)。
5. 轨迹层以该战略计划为指导，用 NMPC + SCP 生成实时轨迹并执行自适应角色切换。

> 原文（Algorithm 1）:
> "Require: Initial state S0 = {pm(0), Erem m (0)}, initial task set I0, control interval TS, prediction horizon TH. Ensure: Sequence of strategic plans {Π∗(τk)}."
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

原问题为大规模 Mixed-Integer Non-Linear Program（MINLP），联合优化无人机轨迹、任务调度与多跳数据中继，并严格计入动态 LoS 遮挡、异构 IoT 数据需求与截止时间。

能量预算约束经线性化重构为线性约束（式 35）：

$$\sum_{t=0}^{T-1}\ \sum_{k_1,k_2 \in W} z_{m,k_1,k_2,t}\ \bar{E}^{P}_{k_1,k_2} + \sum_{t,i,j,n} f_{i,j,n,t}\, P_t\,\Delta t \le E^{\max}_{m}$$

其中角色切换的离散变量 zm,k1,k2,t 由以下约束与任务分配变量绑定（式 32–34）：

$$z_{m,k_1,k_2,t} \le y_{m,k_1,t}$$

$$z_{m,k_1,k_2,t} \le y_{m,k_2,t+1}$$

$$z_{m,k_1,k_2,t} \ge y_{m,k_1,t} + y_{m,k_2,t+1} - 1$$

> 说明：以上公式取自全文 Markdown [[03fulltext/UAV/H8PIYWY4]] 的原文表达（式 32–35），按原文数学含义还原为标准排版，未改动数值与符号。PDF 页码未验证。

## Assumptions

假设：

- 无人机的任务分配、数据采集与能量消耗可在滚动时域内以线性化方式近似。
- 战略层给出的长期计划可作为轨迹层的指导，两层之间通过滚动时域回路动态校正。
- 轨迹层可通过 SCP 在实时约束内收敛到局部最优且物理可行的解。

## Optimization Objective

目标：

- 在满足任务截止时间、机载能量预算与动态 LoS 遮挡约束的前提下，最小化任务完成时间（makespan）并最大化数据采集总量。
- 同时兼顾任务成功率与计算效率之间的权衡。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 在基于真实地图的城市环境中进行大量仿真（realistic, map-based urban environments）。
- 考虑动态 LoS 遮挡、异构 IoT 数据需求与任务截止时间。

> 原文：
> "We validate the proposed framework through extensive simulations in realistic, map-based urban environments."

> 说明：具体的无人机数量、任务点数、地图规模、仿真平台与硬件配置，未在当前全文中定位到可核验的集中表述，此处不做推测。

## Baseline

比较方法：

- 与 state-of-the-art baselines 对比（论文原文表述，未在当前全文中逐一定位到具体基线名称）。

> 原文：
> "The results demonstrate that our approach significantly outperforms state-of-the-art baselines by achieving a superior trade-off between mission success rate, completion time, and computational efficiency."

## Metrics

评价指标：

- Mission makespan（任务完成时间）
- 数据采集总量（total data collected）
- 任务成功率（mission success rate）
- 计算效率 / 求解耗时（computational efficiency）

## Results

主要结果：

| 指标 | 相对基线的改善 |
|---|---|
| Mission makespan | 减少 8.6% |
| Total data collected | 提升 2.4% |

> 原文：
> "Simulation results demonstrate that the proposed framework reduces mission makespan by 8.6% and increases the total data collected by 2.4%, validating its efficiency and robustness."
>
> 原文：
> "Overall, the results demonstrate that the proposed method is robust to ηs variations within a broad and practically relevant range."
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出 HOC-UADC 框架，联合优化无人机轨迹、任务调度与多跳数据中继，并严格计入动态 LoS 遮挡、异构 IoT 数据需求与截止时间。
2. 提出双层层次优化框架：战略层用线性化 MILP + RHC 回路做长期机队协调。
3. 设计基于 NMPC 的实时高保真轨迹层，用嵌入式组合方案智能解耦离散角色切换与连续轨迹优化，经 SCP 高效求解。
4. 仿真表明该方法在任务成功率、完成时间与计算效率之间取得更优权衡，显著优于现有基线。

> 原文：
> "In this paper, we propose HOC-UADC, a hierarchical optimal control framework to address the joint trajectory and communication design problem for multi-UAV emergency networks. Our method successfully tames the computational complexity of the underlying MINLP by decomposing it into a dual-layer MPC architecture."

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 双层分解是使大规模优化问题可实时部署的**关键**（essential），而非单纯的性能优化技巧。
- 战略层 MILP 负责长期协调，轨迹层 NMPC 负责物理感知的实时控制与动态角色切换，二者通过 RHC 闭环衔接。

> 原文：
> "The strategic layer employs an MILP within an RHC loop to manage long-term fleet coordination, while the trajectory layer uses NMPC for realtime, physics-aware control and dynamic role-switching. This hierarchical design proved essential for making the large-scale optimization problem tractable for real-time deployment."

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 抓住了 UAV 应急通信领域的核心矛盾——MINLP 的最优性与实时性不可兼得，并用层次分解给出可落地方案。
- 角色切换与轨迹优化的解耦设计具有通用性，可迁移到其他含离散—连续混合决策的无人机任务。
- 在真实地图城市环境做仿真，比纯 synthetic 场景更有说服力。
---

# 10. Limitation（不足）

论文不足：

1. 验证方式为仿真，未在真实无人机平台上做硬件在环或实地飞行实验。
2. 战略层依赖问题线性化，线性化误差对长期计划最优性的影响未做定量分析。
3. 轨迹层经 SCP 求解只能保证局部最优，全局最优性缺失。
4. 论文未在当前全文中集中给出仿真规模参数（无人机数量、任务点规模）与基线方法的具体名称，可复现性细节不足。

未来可能改进：

- 引入数据驱动的遮挡预测以替代或增强模型化的 LoS 假设。
- 探索分布式/去中心化的层次控制，降低对中心节点计算能力的依赖。
- 扩展到通信—感知一体化（ISAC）场景，联合考虑感知任务与通信任务。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 「解耦导致次优、整体导致不可行」是组合优化在实时系统中的典型两难，层次分解是打破该僵局的通用思路。
- 离散决策与连续决策可以在不同时间尺度上分层处理：慢尺度做离散分配，快尺度做连续控制。
- 滚动时域控制（RHC）是连接长期规划与实时执行的标准机制。
- SCP 是把非线性轨迹优化纳入实时回路的实用工具，代价是只保证局部最优。

## Connection With My Work

和我的研究/项目关系：

- 该文的 MINLP → 双层 MPC 分解思路可直接借鉴到 UAV-ISAC 的轨迹与波束联合设计问题。
- 角色切换（role-switching）概念对应 ISAC 中通信/感知功能的时分或空分切换，是值得对口迁移的建模元素。
- 能量预算约束的线性化重构（式 32–35）可作为自己建模时处理离散—连续耦合的参考范式。

## Possible Ideas

可能的新想法：

- 把该框架的双层结构扩展到 ISAC：战略层分配感知/通信任务，轨迹层联合优化轨迹与波束赋形。
- 用学习式方法（如强化学习）替代或加速战略层 MILP 求解，进一步压缩重规划时间。
- 研究遮挡预测误差对层次分解性能的影响，给出鲁棒性边界。
---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/LLM/Attention Is All You Need|Transformer 开山之作]] — 序列建模基础架构，可作为轨迹序列建模的方法参照

---

# 13. Summary Card（快速复习）

## Problem

> 多无人机应急通信的轨迹—调度联合优化构成 NP-hard 的 MINLP：解耦则次优，整体求解则无法实时部署。

## Method

> 双层 MPC 分解：战略层用线性化 MILP + 滚动时域控制做长期机队协调，轨迹层用 NMPC + 序列凸规划做实时轨迹与动态角色切换。

## Result

> 任务完成时间（makespan）减少 8.6%，数据采集总量提升 2.4%，且在参数 ηs 的宽范围内保持鲁棒。

## Importance

> 证明了层次分解是使大规模 UAV 联合优化问题可实时部署的关键路径，且角色切换与轨迹优化可智能解耦。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决多无人机应急通信中 MINLP 联合优化不可实时求解的问题——现有解耦方法次优、整体求解不可行。

Q:
核心方法是什么？

A:
HOC-UADC 双层模型预测控制：战略层 MILP + RHC 做长期协调，轨迹层 NMPC + SCP 做实时轨迹与角色切换。

Q:
最大贡献是什么？

A:
用层次分解驯服 MINLP 的计算复杂度，使大规模优化可实时部署，并在仿真中取得 makespan 减 8.6%、数据量增 2.4% 的效果。
---

## 证据溯源说明

- 元数据来自 Zotero 条目 `H8PIYWY4`（本地 API 读取），PDF 附件 `2RVKF9X8`。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/H8PIYWY4]]，来源为 Zotero 全文缓存 `F:\XWCos\zotero\storage\2RVKF9X8\.zotero-ft-cache`。
- PDF 页码未验证：全文缓存不含 page mapping，故未标注具体页码；需页码核验时请打开原始 PDF。
- 论文仿真规模参数（无人机数量、任务点规模）与基线方法具体名称，未在当前全文中定位到集中表述，已在正文如实标注，未做推测。
- 结论区每条主要发现均紧邻至少一条真实原文引用；无法定位原句时明确标注，未反向生成英文 quote。