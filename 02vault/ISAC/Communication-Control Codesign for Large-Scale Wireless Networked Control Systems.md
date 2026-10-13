---
title: "Communication-Control Codesign for Large-Scale Wireless Networked Control Systems"
aliases:
  - WNCS 通控协同设计
  - GCA-DRL
tags:
  - literature-note
  - reading-note
  - ISAC
  - WNCS
  - DRL
created: 2026-10-13
source: IEEE Journal on Selected Areas in Communications, 2025
author: Gaoyang Pang, Wanchun Liu, Dusit Niyato, Branka Vucetic, Yonghui Li
year: 2025
journal: IEEE JSAC

theme: 大规模无线网控系统（WNCS）中通信调度与控制输入的联合设计，用级联双分支 DRL 打破分离设计
study_area: 通感一体化 / 无线网控系统 / 通控协同设计
methodology: 多回路 WNCS 建模 + MDP 形式化 + GCA-DRL（级联双分支 actor + 知识辅助图动作嵌入，基于 TD3）
key_finding: GCA-DRL 控制代价 858.65，比最佳基线（1201.36）降低 28.5%，且收敛更快
relevance: 通—控耦合是 ISAC 的重要延伸方向，其"混合动作空间 + 跨域变量"的处理技巧可迁移

type: literature-note
zotero_key: "CPAWPDHD"
pdf_key: "IGEFR2C5"
doi: "10.1109/JSAC.2025.3574602"
collection: "ISAC"
note_path: "02vault/ISAC/Communication-Control Codesign for Large-Scale Wireless Networked Control Systems.md"
fulltext_path: "03fulltext/ISAC/CPAWPDHD.md"
status:
  - Reading
rating: 五星
---

# Communication-Control Codesign for Large-Scale Wireless Networked Control Systems

---

# 📌 Basic Information（基本信息）

## Author
Gaoyang Pang, Wanchun Liu, Dusit Niyato, Branka Vucetic, Yonghui Li

## Year
2025

## Source
IEEE Journal on Selected Areas in Communications｜DOI: 10.1109/JSAC.2025.3574602

> Zotero 入口：zotero://select/library/items/CPAWPDHD
> PDF 入口：zotero://open-pdf/library/items/IGEFR2C5
> 全文 Markdown：[[03fulltext/ISAC/CPAWPDHD]]

## Research Area

- Wireless Networked Control Systems (WNCS)
- Communication-Control Codesign
- Deep Reinforcement Learning (DRL)
- Industrial IoT / Industry 4.0

---

# 1. Abstract Summary（一句话总结）

> 该文针对大规模无线网控系统（WNCS）提出实用的多回路模型（耦合控制回路、时间相关信道、感知—控制传输折衷），把通控协同设计建模为序贯决策（MDP），并提出 **GCA-DRL** 算法——级联双分支 actor 网络联合输出调度与控制，配合知识辅助的图动作嵌入处理混合动作空间，在控制代价上显著优于所有基线。

---

# 2. Research Background（研究背景）

## 背景：

- WNCS 是工业 4.0 的关键支撑，用于无人机群、自主机器人等需要灵活控制的场景。
- 通信与控制之间存在**相互依赖**，需要一体化设计，但传统方法把二者分开处理，导致低效。

> 原文：
> "Wireless Networked Control Systems (WNCSs) are essential to Industry 4.0, enabling flexible control in applications, such as drone swarms and autonomous robots. The interdependence between communication and control requires integrated design, but traditional methods treat them separately, leading to inefficiencies."

## Motivation（研究动机）

- 现有协同设计方法依赖简化模型，聚焦单回路或相互独立的多回路。
- 大规模 WNCS 面临四个独有的挑战：
  1. **控制回路相互耦合**（coupled control loops）
  2. **无线信道时间相关**（time-correlated wireless channels）
  3. **感知与控制传输之间的折衷**（trade-offs between sensing and control transmissions）
  4. **显著的计算复杂度**

> 原文：
> "large-scale WNCSs face unique challenges, including coupled control loops, time-correlated wireless channels, trade-offs between sensing and control transmissions, and significant computational complexity."

## Application Scenario（应用场景）

- 工业 4.0 大规模集成工厂（多个相互依赖的控制任务）
- 无人机群、自主机器人的无线协同控制
- 空间分布式传感器/执行器共享有限无线资源的场景

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在大规模多回路 WNCS 中，联合优化**信道调度**（哪些设备占用哪些信道）与**控制输入**（发给执行器的连续控制信号），以最小化长期折扣控制代价？

核心问题：

- 如何建模耦合的控制回路与时间相关信道？
- 如何处理"离散调度 + 连续控制"的混合动作空间？
- 如何让控制决策感知通信资源的实时可用性（跨域耦合）？

---

# 4. Related Work（相关工作）

已有方法：

1. **传统分离设计**：先设计通信调度，再用 LQR/MPC 控制，二者不联合优化。
2. **既有协同设计方法**：依赖简化模型，多为单回路或独立多回路。
3. **既有 DRL 协同设计**：在处理混合动作空间与跨域变量时表现不佳（后文作为基线对比：dual-TD3、rounded-off、threshold-based、priority-based）。

现有不足：

- 分离设计忽略了通信与控制的内在耦合：例如控制需要及时准确的感知数据，而通信调度必须按控制需求排优先级。
- 直接在大规模混合动作空间上训练 DRL，探索困难、收敛慢。

> 原文：
> "Optimizing communication without considering control requirements can lead to inefficiencies, such as over-allocating resources to sensor updates when control actions are more critical."

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 建立**实用的多回路 WNCS 模型**：多个相互依赖的控制回路、空间分布的传感器与执行器、多状态马尔可夫块衰落信道、短包通信。
- 把协同设计表述为**序贯决策问题（MDP）**，联合优化估计域、控制域、通信域。
- 提出 **GCA-DRL**（Graph-based Cascaded Actor DRL）求解。

## Model / Framework

系统模型（多回路 WNCS）：

- 组成：一个智能边缘控制器 + `M` 个空间分布传感器 + `N` 个执行器，共享 `L` 个无线频率信道（`1 ≤ L ≤ N + M`）。
- 被控对象为线性离散时间系统：

> 原文（式 1a-d）：
> "x(t+1) = Ax(t) + Bu_rx(t) + w(t)"
> "y_tx(t) = Cx(t) + v(t)"
> "u_rx(t) = Λ(t)u_tx(t)"
> "y_rx(t) = Ψ(t)y_tx(t)"

- **`Λ(t)`、`Ψ(t)` 为二进制对角矩阵**，分别表示控制/感知包的传输成功与否（丢包建模）。
- 每个状态维度**不稳定**（`ρk(A) > 1`），无控制输入时状态无界增长。
- 信道：**有限状态齐次马尔可夫块衰落信道**，`H` 个状态，逐时隙变化；控制器通过标准信道估计获得 CSI，但**转移矩阵未知**（估计多维马尔可夫链计算量过大）。
- 短包通信，译码失败概率：

> 原文（式 3）：
> "ε(γ) ≈ Q((C(γ) − b/l) / sqrt(V(γ)/l))"

- 采用 **off-band full-duplex**：感知包与控制包可在同一时隙的不同频率信道上调度。
- 每个设备最多占一个信道，每个信道只分给一个设备（约束式 4）。

## Algorithm / Technique

采用：

- **MDP 形式化**：
  - 状态 `s(t) = {x̂(t), P(t), u_rx(t−1), G(t)}`（估计状态、估计误差协方差、上一步控制质量、CSI）
  - 动作 `a(t) = {D(t), u_tx(t)}`（离散信道分配 + 连续控制输入）
  - 一步代价 `c(t) = x̂(t)⊤Qx̂(t) + Tr(QP(t)) + u_rx(t)⊤Ru_rx(t)`
- **GCA-DRL**，基于 TD3，两个关键创新：
  1. **级联双分支 actor 网络**：调度分支（sigmoid 输出 `[0,1]^{(M+N)×L}`）与控制分支（连续控制信号）并联，且**调度输出级联送入控制分支**，使控制决策感知实时通信资源可用性。全连接层均用 **Layer Normalization** 处理跨域变量量纲差异。
  2. **知识辅助的图动作嵌入**：用**最大权二分图匹配（MBGM）**把离散信道分配转为连续权重表示，并把调度权重与 CSI 逐元素相乘（`acom(t) ⊙ G(t)`），使匹配权重具备信道上下文感知。

## Key Steps

1. 传感器上报测量，边缘控制器用修正 Kalman 滤波（mKF）估计状态；因上行时延，控制器用上一步估计递推当前状态（式 8-9）。
2. 构造 MDP 状态，GCA-DRL actor 输出调度权重与控制信号。
3. 调度权重与 CSI 逐元素相乘后，用 MBGM 求解一对一匹配，得到实际信道分配 `D(t)`。
4. 依据分配结果与信道增益计算译码失败概率，决定 `Λ(t)`、`Ψ(t)`。
5. 执行器按 zero-input 策略处理未收到的控制信号。
6. 用 TD3 的双 critic（取 min 抑制过估计）与策略梯度更新，周期性软更新目标网络。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- 目标：最小化折扣控制代价（式 10 / 式 14）：

> 原文（式 10）：
> "J = lim_{T→∞} E[ Σ_{t=0}^{T−1} β^t (x(t)⊤Qx(t) + u_rx(t)⊤Ru_rx(t)) ]"

- 关键推导（式 11）：

> 原文：
> "E[x(t)⊤Qx(t)] = x̂(t)⊤Qx̂(t) + Tr(QP(t))"

→ 最小化控制代价**内在地要求降低估计误差 `P(t)`**，这把通信（估计质量）与控制（状态调节）在目标层面统一起来。

## Assumptions

假设：

- 每个传感器测一个维度、每个执行器对应一个控制信号（工业自动化常见假设）。
- 每个状态维度不稳定（`ρk(A) > 1`）。
- 各设备的马尔可夫信道状态**相互独立**。
- 每个设备用满功率发射；控制器知 CSI，但**不知信道转移矩阵**。
- 未收到控制信号时执行器采用 zero-input 策略。

## Optimization Objective

目标：

- 寻找确定性平稳协同策略 `π(·)`，`(D(t), u_tx(t)) = π(s(t))`，最小化折扣控制代价 `J`。
- 同时需满足信道分配约束（式 4）：每个信道至多分配给一个设备。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据：数值仿真，参数见表 I。

- 系统矩阵 `A, B, C` 随机生成；`A` 的特征值 `ρk(A) ∈ (1.0, 1.1)`；噪声协方差 `W, V` 为单位阵；`Q, R` 为单位阵
- 初始状态 `x(0) = 0`；状态饱和限 `|xi(t)| ≤ 100`
- 发射功率 `Pmax = 23 dBm`；背景噪声 `σ² = −60 dBm`
- 码率 `b/l = 2 bps`；块长 `l = 200 symbols`
- 信道状态 `G = {10⁻¹⁰, 10⁻⁹, ..., 10⁻¹}`
- GCA-DRL 训练：3000 episode，每 episode 最多 100 时隙；隐藏层 300/200/100；学习率 0.001；Adam；经验池 100000；batch 64；折扣因子 `β = 0.99`；目标平滑 `τ = 0.005`

## Baseline

比较方法（调度策略 × 控制器）：

- 调度：**Round-robin、Persistent、Greedy-AoI、Greedy-CSI、Random**
- 控制器：**Modified LQR、Standard LQR、Vanilla TD3**
- DRL 协同设计基线：**dual-TD3、rounded-off、threshold-based、priority-based**

## Metrics

评价指标：

- **控制代价 `J`**（一步代价的折扣和），分解为：
  - 状态估计代价 `E[Tr(QP(t))]`
  - 控制代价 `E[u_rx(t)⊤Ru_rx(t)]`
  - 估计状态代价 `E[x̂(t)⊤Qx̂(t)]`
- 训练收敛速度（3000 episode 的 `J` 曲线）

## Results

主要结果（`K = M = N = L = 5`，10 个设备共享 5 个信道，100 episode × 100 步平均）：

- **GCA-DRL 总体控制代价 858.65**，而最佳基线为 **1201.36**，**降低 28.5%**。
- 传统分离设计的代价高出一个数量级甚至更多：例如 Random + Modified LQR 为 8071124573，Round-robin + Modified LQR 为 40053903.15。
- **训练收敛（图 4）**：GCA-DRL 在 episode 500 前已呈现稳定下降趋势；dual-TD3 与 rounded-off 全程波动且代价更高；dual-TD3 振荡最剧烈、无法收敛到相近的低代价；threshold-based 与 priority-based 初期收敛较快，但平台期代价高于 GCA-DRL。
- 表 III 进一步给出不同系统规模（`L, N, M` 组合）下的对比，验证了可扩展性。

> 原文：
> "GCA-DRL achieves the lowest overall control cost of 858.65, which is a significant improvement over all other approaches. Compared to the best benchmark (1201.36), GCA-DRL reduces 28.5% control cost."

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出**实用的大规模多回路 WNCS 模型**，同时刻画耦合控制回路、时间相关马尔可夫信道、感知—控制传输折衷，并用短包译码失败概率把通信质量直接接入控制回路。
2. 把协同设计形式化为 MDP，并证明最小化控制代价内在地包含最小化估计误差（式 11），从而把通信与控制目标统一。
3. 提出 **GCA-DRL**：级联双分支 actor 让控制"看见"通信约束；知识辅助图动作嵌入（MBGM + CSI 逐元素相乘）化解混合动作空间难题；LayerNorm 处理跨域变量。
4. 数值验证：控制代价相对最佳基线降低 28.5%，收敛速度与稳定性均优于既有 DRL 协同设计方法。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 通信与控制策略是**相关的**，必须让二者在网络结构层面显式耦合——这就是"级联"（cascaded）的意义：调度输出直接喂给控制分支。
- 混合动作空间的规模可通过**把离散问题嵌入连续空间（MBGM 权重）**来规避，而不是硬探索。
- 跨域变量（CSI 量级 10⁻¹⁰ 与控制量级相差巨大）必须用 LayerNorm 拉齐，否则训练被单一域主导。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 三个技术点（级联双分支、图动作嵌入、LayerNorm）都针对明确的具体痛点，且各自有消融/对比支撑，不是堆砌。
- 式 11 的推导把"通信质量"与"控制代价"在数学上连起来，是全文的理论支点，让协同设计从"工程直觉"变成"目标函数内的必然"。
- 表 II 的量级差异（分离设计 vs 协同设计）极具说服力。

- 局限：全仿真，系统矩阵随机生成，未验证真实工业场景；信道转移矩阵假设控制器未知，但 CSI 假设已知且准确，这在大规模系统中偏理想。

---

# 10. Limitation（不足）

论文不足：

1. **全仿真无实测**：系统矩阵 `A, B, C` 随机生成，未使用真实工业被控对象模型或实测信道数据。
2. **CSI 假设偏理想**：假设控制器通过标准信道估计获得准确 CSI，但未考虑信道估计误差与反馈开销；大规模下 CSI 获取本身即负担。
3. **可扩展性的上限未探明**：表 III 给出若干规模组合，但当设备数远大于信道数（`M + N >> L`）时的性能退化未定量分析。
4. **MBGM 为一对一匹配**：约束式 4 要求每设备最多一信道、每信道最多一设备，未支持一设备多信道聚合或 NOMA 类共享。
5. 未见与"感知（sensing）"功能的联合——本文的 sensing 指传感器测量上报，与 ISAC 中的雷达感知不是同一概念，跨界读者需注意术语差异。

未来可能改进：

- 在真实工业 WNCS 测试床或硬件在环平台验证。
- 放宽一对一匹配约束，研究多信道聚合与非正交接入下的协同设计。
- 引入信道估计误差与 CSI 反馈开销，分析其对控制代价的影响。
- 把本文的"通信—控制"协同扩展到"通信—感知—控制"三方协同。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **协同设计的正确性可以用一个等式证明**：`E[x⊤Qx] = x̂⊤Qx̂ + Tr(QP)` 说明估计误差直接计入控制代价，因此"为了控制好而多分配感知资源"不是启发式，而是最优性的要求。这个论证方式值得借鉴。
- **离散动作空间不一定非要离散地学**：把组合优化（二分图匹配）作为 DRL 的"可微输出层"，让 agent 学连续权重、由经典算法解码为离散决策，是处理混合动作空间的通用范式。
- **网络结构可以编码领域因果**：控制依赖通信（而非相反），所以级联方向是调度→控制，这个方向性本身就是先验知识。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV 协同控制方向直接相关：[[02vault/UAV/ISAC-OTA UAV Swarm Dynamics|ISAC-OTA 机群控制]] 也处理无人机群的规模化控制，但用 OTA 空中计算绕开带宽分配；本文用 DRL 做信道调度。二者是同一瓶颈的两种解法，可对照。
- "调度输出级联进控制分支"的思路可迁移到自己的波形—轨迹联合设计：先定通信资源，再定轨迹。
- MBGM + DRL 的动作嵌入方法可用于自己的资源分配问题。

## Possible Ideas

可能的新想法：

- 把本文的通信—控制协同扩展为通信—感知—控制三方协同（加雷达感知目标，感知结果同时服务于控制与通信）。
- 研究 GCA-DRL 在 `M + N >> L`（严重资源不足）下的退化规律，给出可服务的设备规模上限。
- 把 MBGM 换成支持一设备多信道的匹配（如 b-matching），看控制代价能否进一步下降。
- 与 OTA 方案（ISAC-OTA）结合：用 OTA 消除逐设备调度维度，再用 DRL 优化控制。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC-OTA UAV Swarm Dynamics|ISAC-OTA 机群控制]] — 同为大规模 UAV 群控制的资源瓶颈问题，该文用 OTA 空中计算绕开带宽分配，本文用 DRL 调度
- [[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]] — 同属通信—控制协同，该文强调 FBL 可靠性与控制闭环耦合
- [[02vault/其他/Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems|URLLC 实时控制资源分配]]（待补）— 同领域早期工作

---

# 13. Summary Card（快速复习）

## Problem

> 大规模多回路 WNCS 中控制回路耦合、信道时间相关、感知与控制传输折衷，传统分离设计（先通信后控制）导致严重低效。

## Method

> 建立多回路 WNCS + 马尔可夫块衰落信道 + 短包通信模型，形式化为 MDP，用 GCA-DRL 求解：级联双分支 actor（调度→控制）联合输出，MBGM 把离散调度嵌入连续权重并与 CSI 相乘，LayerNorm 拉齐跨域变量。

## Result

> 控制代价 858.65，比最佳基线 1201.36 降低 28.5%；分离设计代价高出数个量级；训练收敛速度与稳态性能均优于 dual-TD3、rounded-off、threshold-based、priority-based。

## Importance

> 用 MDP + 结构化 DRL 给出了大规模 WNCS 通信—控制协同的可行解法，其"级联耦合""图动作嵌入""跨域归一化"三个技巧具有跨问题迁移价值。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决大规模多回路无线网控系统中通信调度与控制输入分离设计导致的低效问题，需联合优化二者。

Q:
核心方法是什么？

A:
建模为 MDP，用 GCA-DRL：级联双分支 actor（调度输出喂给控制分支）+ MBGM 图动作嵌入（离散调度转连续权重并与 CSI 相乘）+ LayerNorm。

Q:
最大贡献是什么？

A:
控制代价比最佳基线降低 28.5%（858.65 vs 1201.36），并证明最小化控制代价内在包含最小化估计误差，把通信与控制目标统一。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `CPAWPDHD`，PDF 附件 `IGEFR2C5`（已挂载至 `F:\XWCos\zotero\storage\IGEFR2C5`）。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/CPAWPDHD]]，由 Zotero 附件 PDF 经 pypdf 提取。
- PDF 页码未验证（pypdf 提取不含可靠页码映射），故未标注页码。
- 仿真数值（表 I/表 II、图 4 结论）直接引自原文；表 III 的具体数值未在本次提取中完整定位，故仅描述其结论方向。
- 术语提示：本文的 sensing 指传感器测量上报，与 ISAC 中的雷达感知不同。
