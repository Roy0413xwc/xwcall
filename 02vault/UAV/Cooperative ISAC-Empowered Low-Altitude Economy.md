---
title: "Cooperative ISAC-Empowered Low-Altitude Economy"
aliases:
  - 协作 ISAC 低空经济
  - Cooperative ISAC LAE
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - low-altitude-economy
  - tensor
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2025
author: Jun Tang, Yiming Yu, Cunhua Pan, Hong Ren, Dongming Wang, Jiangzhou Wang, Xiaohu You
year: 2025
journal: IEEE Transactions on Wireless Communications

theme: 多个多天线基站协作感知低空 UAV，用张量分解做单站参数估计、MST 做跨站数据关联、Pareto 最优与残差加权做位置/速度融合
study_area: 通感一体化 / 低空经济 / 协作感知 / 张量分解
methodology: 空间平滑张量分解（利用 Vandermonde 结构）+ 降维 GRQ AoA 估计 + 去虚警 MST 数据关联 + Pareto 最优定位 + 残差加权测速
key_finding: 比穷举排列与 WLS 更优且复杂度更低；退化到单天线单目标时仍优于 Benchmark2（除径向速度略逊），且上传开销更低
relevance: 低空经济是本 Vault 主线之一；本文的"多站协作 + 数据关联"是低空组网感知的核心问题

type: literature-note
zotero_key: "8A5WX5RQ"
pdf_key: "AC6Q6PHJ"
doi: "10.1109/TWC.2025.3542399"
collection: "UAV"
note_path: "02vault/UAV/Cooperative ISAC-Empowered Low-Altitude Economy.md"
fulltext_path: "03fulltext/UAV/8A5WX5RQ.md"
status:
  - Reading
rating: 五星
---

# Cooperative ISAC-Empowered Low-Altitude Economy

---

# 📌 Basic Information（基本信息）

## Author
Jun Tang, Yiming Yu, Cunhua Pan, Hong Ren, Dongming Wang, Jiangzhou Wang, Xiaohu You

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2025.3542399

> Zotero 入口：zotero://select/library/items/8A5WX5RQ
> PDF 入口：zotero://open-pdf/library/items/AC6Q6PHJ
> 全文 Markdown：[[03fulltext/UAV/8A5WX5RQ]]

## Research Area

- Cooperative Integrated Sensing and Communications (ISAC)
- Low-Altitude Economy (LAE) / UAV sensing
- Tensor Decomposition / Parameter Estimation
- Multi-BS Data Association

---

# 1. Abstract Summary（一句话总结）

> 该文提出面向低空感知场景的**协作式 ISAC 方案**，用多个基站（BS）协作估计多个 UAV 的参数以提升感知性能：Stage I 用**张量分解模型**做单站参数估计（利用因子矩阵的 Vandermonde 结构设计空间平滑张量分解，并用基于广义瑞利商的降维 AoA 算法降低复杂度）；Stage II 通过多站**数据融合**确定 UAV 位置与真实速度（去虚警 MST 数据关联 + Pareto 最优定位 + 残差加权测速），并进一步扩展到双极化系统。

---

# 2. Research Background（研究背景）

## 背景：

- 低空经济（LAE）场景下需对低空 UAV 的飞行状态（位置、速度）进行感知，这是监管与服务的前提。
- 协作式 ISAC（多 BS 协作）被认为能显著提升感知性能。

## Motivation（研究动机）

- 既有协作 ISAC 研究**只考虑特殊场景**（单天线或单目标），缺乏向更复杂实际场景推广的通用性：
  - **单站参数估计**：多数算法只考虑单目标；扩展到多目标时，**如何把多维参数匹配到同一个目标**仍未很好解决。
  - **多站协作**：多目标场景下的**跨站数据关联**是关键问题；既有关联方法仅为单天线设计。
- 张量技术因估计精度高、且**天然保证参数自动配对**，近年被用于信道与目标参数估计，但既有张量 ISAC 工作**未揭示多站协作带来的精度收益**。

> 原文：
> "most of the existing studies only considered some special scenarios of the cooperative ISAC networks (such as the single-antenna or the single-target cases), lacking the generality to extend to the more complex and practical scenarios."
>
> 原文：
> "However, [16] did not reveal the benefits of improving the sensing accuracy through the multi-BS cooperation."

## Application Scenario（应用场景）

- 低空经济中的 UAV 监视与飞行状态感知
- 多个多天线基站组网协作感知多 UAV
- 双极化系统（阵列尺寸受限时提升精度）

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在多天线、多目标、多基站的通用场景下，如何完成"单站多维参数估计 → 跨站数据关联 → 多站融合定位测速"的完整协作感知链条？

核心问题：

- 如何在单站用张量模型同时估计 AoA、距离、径向速度与信道系数，并保证参数自动配对？
- 如何在多目标下把各站估计的参数正确关联到同一个 UAV（且抗虚警）？
- 如何用各站的距离/AoA/径向速度估计融合出位置与**真实速度**（而非径向速度）？

---

# 4. Related Work（相关工作）

已有方法：

1. **单站参数估计**：MUSIC 等经典 AoA 估计技术；张量方法（估计精度高、自动配参）。
2. **既有基于张量的 ISAC**（如 [16]）：统一张量方法做信道与目标参数估计，但未研究多站协作的精度收益。
3. **多站协作**：符号级融合（symbol-level fusion）方案。
4. **多站数据关联**：既有若干关联方法，但**仅为单天线设计**。

现有不足：

- 单天线或单目标的特殊场景假设，缺通用性。
- 多目标下多维参数的匹配问题未解决。
- 既有数据关联方法无法用于多天线场景。
- 符号级融合需要上传大量数据，传输开销与同步要求高。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- **两阶段协作感知**：
  - **Stage I（单站）**：把单站参数估计表述为**张量分解模型**，利用因子矩阵的 **Vandermonde 结构**设计**空间平滑张量分解**算法，同时得到 AoA、距离、径向速度、信道系数；再用**降维（RD）GRQ** 算法降低 AoA 估计复杂度。
  - **Stage II（多站）**：在云端融合各站估计，先用**去虚警 MST（最小生成树）数据关联**把各站参数匹配到同一 UAV，再用 **Pareto 最优方法**估计位置、**残差加权方案**估计真实速度。
- 扩展：把方案推广到**双极化系统**，用**四阶张量分解**建模，在阵列尺寸受限时提升精度。

## Model / Framework

- 系统：`J` 个 BS 先从回波估计 UAV 参数，再在**云端融合**以强化感知性能。
- 为避免站间干扰，假设各 BS 工作在**非重叠频带**。
- 张量符号：标量 `y`、向量 `y`、矩阵 `Y`、张量 `𝒴`；运算符 `◦`（外积）、`⊗`（Kronecker）、`⊙`（Khatri-Rao）。

## Algorithm / Technique

采用：

- **空间平滑张量分解**：利用因子矩阵的 Vandermonde 结构恢复因子矩阵，直接得到 AoA、距离、径向速度与信道系数（off-grid，无需网格搜索）。
- **降维（RD）AoA 估计（基于广义瑞利商 GRQ）**：进一步降低复杂度。
- **去虚警 MST 数据关联**：相比穷举排列（exhaustive permutation），既**防止虚警检测结果影响后续数据融合**，又在 UAV 数量大时**有效降低复杂度**。
- **Pareto 最优方法**：从候选格点并集中确定最终位置估计（同时考虑距离损失函数与其他准则）。
- **残差加权（residual weighting）方案**：抑制估计误差，改进真实速度估计（对比 WLS 方法）。

## Key Steps

1. 各 BS 在各自非重叠频带上接收 UAV 回波。
2. 构造张量模型，用空间平滑张量分解 + Vandermonde 结构估计本站的 AoA、距离、径向速度、信道系数；用 RD-GRQ 降低 AoA 估计复杂度。
3. 各 BS 把估计参数上传云端（仅上传参数，非符号级数据）。
4. 云端用去虚警 MST 做跨站数据关联，把不同 BS 的参数匹配到同一 UAV。
5. 用 Pareto 最优方法从候选格点中确定位置；用残差加权方案确定真实速度。
6. （可选）双极化扩展：改用四阶张量分解建模。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- 单站参数估计表述为张量分解模型（式 30 及相应分解形式），目标是恢复因子矩阵以获得 AoA、距离、径向速度与信道系数。
- 位置估计：从**格点并集（lattice points union）**中确定最终估计，最小化距离损失函数（式 78 为退化场景下仅考虑距离损失的形式）。
- 双极化扩展：建模为**四阶张量分解**问题。

## Assumptions

假设：

- 各 BS 工作在**非重叠频带**，避免站间干扰。
- 因子矩阵具有 **Vandermonde 结构**（可被算法利用以恢复因子矩阵）。
- 退化场景（单天线单目标）下：张量模型退化为**二阶**张量分解；UAV 与 BS 位于同一水平面，z 轴速度分量为零。
- 云端融合，各 BS 上传的是**估计参数**（非符号级采样）。

## Optimization Objective

目标：

- 多站协作下的**位置估计**与**真实速度估计**的 RMSE 最小化；性能以 Range / Radial velocity / Position / True velocity 的 RMSE 衡量。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据：数值仿真。

- 多 BS、多天线、多 UAV 场景；考察 RMSE 随**发射功率**、**BS 数量**的变化
- 退化场景（单天线单目标）：`r1 = 100 m, r2 = 125 m`；UAV 与 BS 同水平面，z 轴速度为 0；发射功率扫描 45–65 dBm
- 速度估计中残差加权强度因子 `β2 = 0.5`

## Baseline

比较方法：

- **穷举排列（exhaustive permutation）**方法（数据关联）
- **WLS（加权最小二乘）**方法（速度估计）
- **Benchmark2**：单天线单目标场景下的先进协作感知方案 [14]（符号级多站融合）

## Metrics

评价指标：

- Range RMSE（m）
- Radial velocity RMSE（m/s）
- Position RMSE（m）
- True velocity RMSE（m/s）

## Results

主要结果：

- **图 14（真实速度 RMSE vs BS 数量，`β2 = 0.5`）**：速度估计误差随 BS 数量增加而下降，因为更多 BS 提供更多关于径向速度与 AoA 的信息；**所提残差加权方案优于 WLS**，因其抑制了估计误差。
- **图 15（退化场景，RMSE vs 发射功率）**：
  - **距离与位置估计**：所提方案**显著优于 Benchmark2**，原因是其 **off-grid** 方法直接利用因子矩阵的 Vandermonde 结构得到距离估计。
  - **径向速度估计**：所提方案**略逊于 Benchmark2**，原因是误差累积——径向速度估计受前序距离估计的影响。
  - **真实速度估计**：由于位置估计更优，所提方案仍取得**与 Benchmark2 相当**的性能。
  - **开销优势**：不同于 Benchmark2 的符号级多站融合，所提数据融合方案**每个 BS 只需向云端上传更少的感知参数**，从而降低传输开销与同步要求。

> 原文：
> "the proposed scheme demonstrates significant performance gains in range and position estimation compared to Benchmark2, due to its off-grid approach to directly derive the range estimation relying on the Vandermonde structure of the factor matrix."
>
> 原文：
> "the proposed data fusion scheme requires each BS to upload fewer sensing parameters to the cloud, thereby reducing the transmission overhead and synchronization requirements."

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 面向**通用的多天线多目标**协作 ISAC 场景提出完整方案，突破既有研究单天线/单目标的局限。
2. **Stage I**：用张量分解建模单站参数估计，利用 Vandermonde 结构设计空间平滑张量分解，并用 RD-GRQ 降维 AoA 估计降低复杂度。
3. **Stage II**：提出**去虚警 MST 数据关联**（抗虚警 + 降低复杂度，优于穷举排列）、**Pareto 最优定位**、**残差加权测速**（优于 WLS）。
4. 扩展到**双极化系统**（四阶张量分解），在阵列尺寸受限时提升精度。
5. 仿真验证：距离/位置估计显著优于 Benchmark2；真实速度与之相当；且上传开销与同步要求更低。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 张量分解的**自动参数配对**特性天然适合多维参数估计，而 Vandermonde 结构可被显式利用实现 **off-grid** 估计（避免网格失配）。
- 多站数据关联不应穷举——用 MST 既降复杂度又能剔除虚警，是"图结构 + 感知"的结合。
- 融合层级应选**参数级而非符号级**，以牺牲少量精度换取大幅降低的传输与同步开销（这在真实组网中往往更重要）。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 完整覆盖"估计—关联—融合"三段链条，且每段都有明确的技术创新与对比支撑，工程完整性好。
- 主动做了**退化场景对比**（图 15），并**如实报告径向速度略逊于 Benchmark2**，这种不回避劣势的写法很扎实。
- "参数级融合 vs 符号级融合"的开销讨论有真实工程价值。

- 局限：径向速度受前序距离估计误差累积影响，说明 Stage I 与 Stage II 的误差传递未做联合优化；全仿真；各 BS 非重叠频带的假设在多站密集部署时频谱代价高。

---

# 10. Limitation（不足）

论文不足：

1. **径向速度略逊于 Benchmark2**：因误差累积（径向速度受前序距离估计影响），说明两阶段之间未做联合优化。
2. **非重叠频带假设**：为避免站间干扰，各 BS 使用不重叠频带，这在多站密集部署时频谱效率代价显著，与 ISAC 提升频谱效率的初衷存在张力。
3. **全仿真无实测**：未使用真实低空信道或实测 UAV 回波数据。
4. **双极化扩展仅初步**：文中给出四阶张量建模，但复杂度与收益的定量权衡着墨较少。
5. **云端融合的时延与同步**虽被指出低于符号级方案，但未定量分析其对实时跟踪的影响。
6. 未涉及通信功能的具体设计——本文聚焦感知，ISAC 中的通信侧（如通信速率约束下的感知）未展开。

未来可能改进：

- 联合优化 Stage I 与 Stage II，抑制距离估计误差向径向速度的传递。
- 研究站间干扰下的重叠频带协作方案（如干扰协调波形）。
- 在真实低空环境做实测验证，纳入真实信道与 RCS 起伏。
- 定量分析双极化方案的复杂度—精度权衡。
- 把通信速率约束引入协作感知的资源分配。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **张量分解的两大红利**：估计精度高 + **参数自动配对**。后者在多目标场景下尤其关键——传统方法估完一堆参数后还要解决"哪个距离配哪个角度"的配对难题，张量天然规避了这一点。
- **Off-grid 优于网格搜索**：利用因子矩阵的代数结构（Vandermonde）直接解出参数，避免了网格分辨率与复杂度的两难。
- **融合层级的选择是系统级权衡**：参数级融合精度略低但开销大幅下降，符号级相反。本文明确指出了这一点，值得在自己的组网设计中作为决策变量而非默认选项。
- **误差会沿流水线传递**：径向速度劣于基线是因为吃了距离估计的误差，提醒我在多阶段算法中要检查误差耦合。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的低空经济主线直接相关，可与 [[Integrated Sensing and Communications for Low-Altitude Economy A Deep Reinforcement Learning Approach|DeepLSC 低空经济]] 对照：该文用 DRL 做服务与监管并存的资源分配，本文做底层协作感知参数估计，二者是同一场景的不同层次。
- 与 [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]] 互补：本文全仿真，该文提供实测信道依据。
- 张量方法可与 [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] 对照：该文也用张量 CP 分解做角度-时延-多普勒估计，可比较 Vandermonde 结构的利用方式。

## Possible Ideas

可能的新想法：

- 联合优化两阶段：把距离估计的误差协方差作为径向速度估计的先验权重，抑制误差传递。
- 研究重叠频带下的站间干扰协调，把非重叠假设放宽。
- 把参数级 vs 符号级融合做成自适应选择（按回传链路容量动态切换）。
- 引入通信速率约束，做真正的 ISAC（本文通信侧缺失）。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[Integrated Sensing and Communications for Low-Altitude Economy A Deep Reinforcement Learning Approach|DeepLSC 低空经济]] — 同为低空经济，该文用 DRL 做资源分配，本文做协作感知
- [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] — 同用张量 CP 分解做多维参数估计，可对照 Vandermonde 结构利用
- [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]] — 提供实测空地信道依据，补本文仿真之不足
- [[02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC|CKM 低空规划]] — 同为低空感知/规划，该文用信道知识图谱

---

# 13. Summary Card（快速复习）

## Problem

> 既有协作 ISAC 研究局限于单天线/单目标，多天线多目标下的多维参数配对与跨站数据关联未解决，且符号级融合开销高。

## Method

> 两阶段：Stage I 用空间平滑张量分解（利用 Vandermonde 结构，off-grid）+ RD-GRQ 降维 AoA 做单站参数估计；Stage II 用去虚警 MST 做跨站数据关联，Pareto 最优定位、残差加权测速；并扩展到双极化四阶张量。

## Result

> 距离与位置 RMSE 显著优于 Benchmark2（off-grid 优势）；径向速度略逊（误差累积）；真实速度与 Benchmark2 相当；残差加权优于 WLS；且每站上传参数更少，传输与同步开销更低。

## Importance

> 给出多天线多目标协作 ISAC 的完整"估计—关联—融合"方案，并明确了参数级融合在开销上的系统级优势。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决多天线多目标协作 ISAC 中多维参数配对、跨站数据关联与融合定位测速的问题，突破单天线/单目标局限。

Q:
核心方法是什么？

A:
两阶段：单站用空间平滑张量分解（Vandermonde 结构，off-grid）+ RD-GRQ 估计 AoA/距离/径向速度；多站用去虚警 MST 关联、Pareto 最优定位、残差加权测速。

Q:
最大贡献是什么？

A:
完整覆盖"估计—关联—融合"链条；距离/位置精度显著优于基线，且参数级融合大幅降低上传与同步开销。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `8A5WX5RQ`，PDF 附件 `AC6Q6PHJ`（已挂载至 `F:\XWCos\zotero\storage\AC6Q6PHJ`）。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/8A5WX5RQ]]，由 Zotero 附件 PDF 经 pypdf 提取。
- PDF 页码未验证（pypdf 提取不含可靠页码映射），故未标注页码。
- 仿真结论（图 14、图 15 趋势与相对关系）直接引自原文；具体 RMSE 数值点未在提取文本中完整给出，故以趋势与相对关系表述，未做推测。
- 式 30、式 78 仅按文中描述引用，未在本次提取中完整定位其表达式。
