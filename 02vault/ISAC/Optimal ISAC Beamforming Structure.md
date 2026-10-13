---
title: "Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Balancing"
aliases:
  - ISAC 波束成形最优结构
  - OBS
tags:
  - literature-note
  - reading-note
  - ISAC
  - 波束成形
created: 2026-10-13
source: IEEE Transactions on Signal Processing, 2026
author: Tianyu Fang, Mengyuan Ma, Markku Juntti, Nir Shlezinger, A. Lee Swindlehurst, Nhan Thanh Nguyen
year: 2026
journal: IEEE Transactions on Signal Processing

theme: 揭示 ISAC 波束成形的最优结构并用低维重构降低求解复杂度
study_area: 通感一体化 / 波束成形 / 非凸优化
methodology: SCA 序列凸近似 + 拉格朗日对偶推导最优波束结构（OBS）+ 低维重构
core_variable: 和速率（SR）、Cramér-Rao 下界（CRLB）、雷达流数、变量维度
key_finding: 证明雷达流数超过 3M 无必要（Ns=3M 足够用尽感知自由度），并给出 CRLB 优化的 OBS 使问题可低维求解
relevance: ISAC 波束成形是 UAV-ISAC 的核心模块，该文的 OBS 结论可直接用于降低设计复杂度

type: literature-note
zotero_key: "4IPDFAZ4"
pdf_key: "U2MIQPK8"
doi: "10.1109/tsp.2026.3694198"
collection: "ISAC"
note_path: "02vault/ISAC/Optimal ISAC Beamforming Structure.md"
fulltext_path: "03fulltext/ISAC/4IPDFAZ4.md"
status:
  - Reading
rating: 五星
---

# Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Balancing

---

# 📌 Basic Information（基本信息）

## Author
Tianyu Fang, Mengyuan Ma, Markku Juntti, Nir Shlezinger, A. Lee Swindlehurst, Nhan Thanh Nguyen

## Year
2026

## Source
IEEE Transactions on Signal Processing｜DOI: 10.1109/tsp.2026.3694198

> Zotero 入口：zotero://select/library/items/4IPDFAZ4
> PDF 入口：zotero://open-pdf/library/items/U2MIQPK8
> 全文 Markdown：[[03fulltext/ISAC/4IPDFAZ4]]

## Research Area

- Integrated Sensing and Communications (ISAC)
- Dual-Purpose Beamforming
- Cramér-Rao Lower Bound (CRLB)
- Successive Convex Approximation (SCA)

---

# 1. Abstract Summary（一句话总结）

> 该文针对 ISAC 双功能波束成形中通信和速率与感知 CRLB 高度非凸的难题，提出基于序列凸近似（SCA）的低复杂度结构化算法保证收敛到局部最优，并利用拉格朗日对偶推导出 CRLB 优化的最优波束成形结构（OBS），刻化了可使用的雷达流数上界。

---

# 2. Research Background（研究背景）

## 背景：

- ISAC 已成为统一无线通信与雷达感知的有前景范式，可提升频谱与硬件利用效率。
- 实现 ISAC 增益的核心挑战来自双功能波束成形设计：通信的和速率（sum rate）与感知的 Cramér-Rao 下界（CRLB）都是高度非凸的性能指标。

> 原文：
> "Integrated sensing and communications (ISAC) has emerged as a promising paradigm to unify wireless communications and radar sensing, enabling efficient spectrum and hardware utilization."
>
> 原文：
> "A core challenge with realizing the gains of ISAC stems from the unique challenges of dual purpose beamforming design due to the highly non-convex nature of key performance metrics such as sum rate for communications and the Cramér–Rao lower bound (CRLB) for sensing."

## Motivation（研究动机）

- 现有数值方法（含深度学习与深度展开）虽能提供有效解，但无法给出最优波束成形器结构的根本性洞察。
- 缺乏结构洞察导致在大规模网络中面临计算复杂度挑战。

> 原文：
> "While the above approaches provide effective numerical solutions to joint ISAC beamforming designs, they fail to offer fundamental insights into the structure of the optimal beamformers. As a result, they face challenges in computational complexity, especially in large-scale networks."

## Application Scenario（应用场景）

- 多用户通信 + 多目标探测的 ISAC 基站
- 大规模天线阵列下的低复杂度波束设计
- UAV-ISAC 的波束成形模块
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在 ISAC 双功能波束成形中，既保证收敛到局部最优，又揭示最优波束成形器的结构以降低大规模场景下的计算复杂度？

核心问题：

- 如何把高度非凸的 SR-CRLB 权衡问题转化为可求解的凸子问题序列？
- CRLB 优化下的最优波束成形结构（OBS）是什么？
- 雷达流数需要多少才能用尽感知自由度？

---

# 4. Related Work（相关工作）

已有方法：

1. **纯数值优化方法**：能给出有效数值解，但缺乏对最优波束结构的结构性洞察。
2. **深度学习 / 深度展开（deep unfolding）**：可支持迭代受限的 ISAC 波束成形优化，但同样缺少结构洞察。
3. **多用户纯通信系统 OBS**：已有工作证明 MMSE 滤波器是最优结构，为本文提供了参照。

现有不足：

- 缺少对 ISAC 最优波束结构（OBS）的理论刻画。
- 大规模网络下计算复杂度高。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出低复杂度的结构化 ISAC 波束成形优化方法，同时提升频谱效率与估计精度。
- 用序列凸近似（SCA）把原非凸问题转化为一系列凸子问题，保证收敛到局部最优解。
- 借助 SCA 框架与拉格朗日对偶，推导 ISAC 系统中 CRLB 优化的最优波束成形结构（OBS）。

> 原文：
> "we develop a successive convex approximation (SCA) based algorithm which transforms the original non-convex problem into a sequence of convex subproblems ensuring convergence to a locally optimal solution."
>
> 原文：
> "Furthermore, leveraging the proposed SCA framework and the Lagrange duality, we derive the optimal beamforming structure for CRLB optimization in ISAC systems."

## Model / Framework

系统模型：

- **场景**：单站（monostatic）ISAC 系统，同时服务多用户通信与多目标探测。
- **感知度量**：通用 CRLB 指标，可估计目标相对基站的方位角、俯仰角以及复雷达截面积。
- **通信度量**：和速率（sum rate, SR）。
- **优化变量**：波束成形矩阵（含通信与感知流）。

## Algorithm / Technique

采用：

- 序列凸近似（SCA）
- 拉格朗日对偶（Lagrange duality）
- 最优波束成形结构（OBS）推导
- 低维波束成形重构

## Key Steps

1. 建立支持多用户通信与多目标探测的通用单站 ISAC 系统模型。
2. 推导可估计方位角/俯仰角/复 RCS 的通用 CRLB 感知度量。
3. 基于 CRLB 与 SR 构造高度非凸的优化问题。
4. 用 SCA 将问题转为凸子问题序列，迭代至局部最优。
5. 结合拉格朗日对偶推导 CRLB 优化的 OBS，并据此做低维重构降低变量维度。
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **感知指标**：通用 CRLB，可估计目标相对基站的方位角、俯仰角与复雷达截面积；已有单目标或有限参数 CRLB 度量是其特例。
- **通信指标**：多用户和速率 SR。
- **优化变量**：波束成形矩阵 W。
- **秩结论（Lemma 5）**：最优解的秩不超过 3M，即 rank(W) ≤ 3M。
- **低维重构（Proposition 5）**：原问题可重构为 W = NP 的形式，其中 N = [H, A, Ȧθ, Ȧφ]，P 为辅助变量，维度 (K+3M)×(K+3M)。

> 原文（Lemma 5 含义）：
> "Lemma 5 indicates that Ns = 3M is sufficient to fully exploit the available DoFs for sensing, and setting Ns > 3M is unnecessary."
>
> 说明：完整闭式表达与证明见 [[03fulltext/ISAC/4IPDFAZ4]] 原文附录，此处仅重述结论性不等式。PDF 页码未验证。

## Assumptions

假设：

- 单站 ISAC 配置（收发同址）。
- 目标参数可由方位角、俯仰角与复 RCS 刻画。
- SCA 的凸子问题序列可收敛到原问题的局部最优。

## Optimization Objective

目标：

- 在和速率与 CRLB 之间取得平衡（sum rate 与 CRLB balancing），同时通过 OBS 降低求解复杂度。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 数值仿真验证（Section V），具体包括对 Ns = 3M 结论的验证（Section V-B）。

## Baseline

比较方法：

- 纯数值优化方法
- 深度学习 / 深度展开方法

> 说明：论文指出上述方法缺少结构洞察因而复杂度高，但具体基线名称未在当前材料中逐一定位，此处不做推测。

## Metrics

评价指标：

- 和速率（SR）
- CRLB（估计精度）
- 优化变量维度 / 计算复杂度
- 雷达流数 Ns 的充分性

## Results

主要结果：

- SCA 算法可保证收敛到局部最优解。
- 推导出 CRLB 优化的 OBS，提供灵活且低复杂度的 CRLB 优化方案。
- Lemma 5：Ns = 3M 足以用尽感知可用自由度，Ns > 3M 无必要（仿真在 Section V-B 验证）。
- 基于 OBS 的低维重构把变量数降至 K² + 9M² + 6MK 量级，显著降低维度。

> 原文：
> "Lemma 5 indicates that Ns = 3M is sufficient to fully exploit the available DoFs for sensing, and setting Ns > 3M is unnecessary. Our subsequent simulation results verify this in Section V-B."
>
> 原文：
> "The above finding reveals that the dimensions of the optimization variable can be further reduced without compromising the performance."

> 说明：具体的 SR/CRLB 数值与复杂度量级对比，未在当前材料中逐项定位，此处不做引述。
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 建立支持多用户通信与多目标探测的通用单站 ISAC 系统模型。
2. 推导可估计方位角、俯仰角与复 RCS 的通用 CRLB 感知度量，涵盖已有单目标/有限参数度量作为特例。
3. 提出基于 SCA 的算法，把非凸问题转为凸子问题序列并保证收敛到局部最优。
4. 借助 SCA 与拉格朗日对偶推导 CRLB 优化的最优波束结构（OBS）。
5. 刻画了雷达流数上界：Ns = 3M 即足以用尽感知自由度，并据此实现低维重构。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 识别并利用问题的最优波束结构（OBS），是降低大规模 ISAC 网络复杂度的有前景路径。
- 本文方案能识别 CRLB 波束成形优化的 OBS，因此可为 ISAC 系统中的 CRLB 优化提供灵活且低复杂度的解法。

> 原文：
> "our proposed approach identifies the OBS of CRLB-based beamforming optimization and is thus able to provide a flexible and low-complexity solution for CRLB-based optimization in ISAC systems."

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 不仅有算法（SCA），还给出结构性理论结论（OBS、Ns=3M 上界），这是相对纯数值工作的实质性推进。
- 低维重构直接把变量维度降到可工程实现的量级，实用价值明确。
- 通用 CRLB 度量涵盖已有特例，理论完整性强。

---

# 10. Limitation（不足）

论文不足：

1. SCA 只能保证局部最优，无全局最优性保证。
2. 单站（monostatic）配置，未覆盖双站/多站 ISAC。
3. 仿真验证为主，无硬件实测。
4. 结构结论依赖具体的信道与阵列模型假设。

未来可能改进：

- 推广到双站/多站与分布式 ISAC 架构。
- 结合学习式初始化改善 SCA 的局部最优问题。
- 在 UAV 等移动平台上验证（含移动性带来的时变信道）。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 「先找结构再优化」是降低非凸问题复杂度的有效路径：OBS 一旦确定，变量维度可大幅压缩。
- 雷达流数并非越多越好，存在饱和点（本文为 3M），超出后不带来额外自由度收益。
- SCA 是处理非凸波束优化的标准工程工具，代价是局部最优。
- 通用 CRLB 度量把单目标/有限参数情形统一为特例，这种「普适化」写法值得学习。

## Connection With My Work

和我的研究/项目关系：

- 该文的 OBS 与低维重构可直接用于 UAV-ISAC 波束设计，缓解机载算力约束。
- Ns = 3M 的结论可用于自己的感知流数配置，避免无效维度浪费。
- 通用 CRLB 推导可作为自己感知性能度量的模板（方位角 + 俯仰角 + RCS）。

## Possible Ideas

可能的新想法：

- 把 OBS 结论推广到 UAV 移动场景（时变信道下的结构是否保持）。
- 联合优化 UAV 轨迹与本文的低维波束结构。
- 研究双站 UAV-ISAC 下的 OBS 形式。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同属 ISAC 权衡，该文做轨迹设计，本文做波束成形结构
- [[02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks|SNN-DRL ISAC V2X]] — 同为 ISAC 波束优化，该文用学习方法，本文用结构化优化方法

---

# 13. Summary Card（快速复习）

## Problem

> ISAC 双功能波束成形中 SR 与 CRLB 高度非凸，现有数值/学习方法缺乏结构洞察，大规模场景复杂度高。

## Method

> SCA 序列凸近似保证局部最优；结合拉格朗日对偶推导 CRLB 优化的 OBS，并做低维重构。

## Result

> 证明 Ns = 3M 足以用尽感知自由度；基于 OBS 的低维重构在不损失性能的前提下降维。

## Importance

> 为 ISAC 波束成形提供了结构性理论洞察与可工程落地的低复杂度解法。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 ISAC 波束成形中 SR-CRLB 高度非凸、现有方法缺结构洞察且大规模复杂度高的问题。

Q:
核心方法是什么？

A:
SCA 序列凸近似 + 拉格朗日对偶推导 CRLB 优化的最优波束结构（OBS）+ 低维重构。

Q:
最大贡献是什么？

A:
给出 ISAC 波束成形的结构性结论（OBS 与 Ns=3M 上界），并据此实现可落地的低复杂度设计。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `4IPDFAZ4`，PDF 附件 `U2MIQPK8`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/4IPDFAZ4]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- Lemma 5 与 Proposition 5 的完整证明见原文附录，此处仅重述结论性不等式；具体 SR/CRLB 数值未逐项定位，已在正文标注。