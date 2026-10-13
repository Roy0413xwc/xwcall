---
title: "A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Near-Field and Far-Field Scenarios"
aliases:
  - AFDM-ISAC
  - CP 分解估计
tags:
  - literature-note
  - reading-note
  - ISAC
  - AFDM
  - 参数估计
created: 2026-10-13
source: IEEE Internet of Things Journal, 2025
author: Yirui Luo, Yong Liang Guan, Yao Ge, David González G., Chau Yuen
year: 2025
journal: IEEE Internet of Things Journal

theme: 在近场/远场混合场景下用张量 CP 分解实现 AFDM-ISAC 的角度-时延-多普勒联合估计
study_area: 通感一体化 / AFDM 波形 / 参数估计
methodology: 三阶张量建模 + 结构化 CP 分解 + 空间平滑 + 低复杂度估计
core_variable: 角度、时延、多普勒估计精度；唯一性条件；计算复杂度
key_finding: 利用因子矩阵 Vandermonde 特性与空间平滑，提出保证唯一性的结构化 CP 分解与低复杂度估计方案
relevance: AFDM-ISAC 参数估计，对高移动性 UAV 场景的感知算法设计有参考价值

type: literature-note
zotero_key: "2UM9X5FB"
pdf_key: "G9CX5BUU"
doi: "10.1109/jiot.2025.3559924"
collection: "ISAC"
note_path: "02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation.md"
fulltext_path: "03fulltext/ISAC/2UM9X5FB.md"
status:
  - Reading
rating: 五星
---

# A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Near-Field and Far-Field Scenarios

---

# 📌 Basic Information（基本信息）

## Author
Yirui Luo, Yong Liang Guan, Yao Ge, David González G., Chau Yuen

## Year
2025

## Source
IEEE Internet of Things Journal｜DOI: 10.1109/jiot.2025.3559924

> Zotero 入口：zotero://select/library/items/2UM9X5FB
> PDF 入口：zotero://open-pdf/library/items/G9CX5BUU
> 全文 Markdown：[[03fulltext/ISAC/2UM9X5FB]]

## Research Area

- Affine Frequency Division Multiplexing (AFDM)
- Integrated Sensing and Communication (ISAC)
- Tensor CP Decomposition
- Near-Field / Far-Field Sensing

---

# 1. Abstract Summary（一句话总结）

> 该文面向近场与远场目标共存的大规模天线 AFDM-ISAC 系统，把接收信号建模为三阶张量并利用其低秩 CP 结构，借助因子矩阵的 Vandermonde 特性与空间平滑技术，提出保证唯一性的结构化 CP 分解方法与低复杂度的角度-时延-多普勒参数估计方案。

---

# 2. Research Background（研究背景）

## 背景：

- 新近提出的多啁啾波形 AFDM（仿射频分复用）被认为是 ISAC 的潜在候选波形。
- 但在大规模天线系统中，近场（NF）与远场（FF）目标共存，加上分数时延与多普勒偏移，使准确获取目标感知参数变得困难。

> 原文：
> "The recently proposed multi-chirp waveform, affine frequency division multiplexing (AFDM), is considered as a potential candidate for integrated sensing and communication (ISAC)."
>
> 原文：
> "acquiring accurate target sensing parameter information becomes challenging due to fractional delay and Doppler shift occurrence, as well as effects introduced by the coexistence of near-field (NF) and far-field (FF) targets associated with large-scale antenna systems."

## Motivation（研究动机）

- 分数时延/多普勒与 NF/FF 混合共存，使传统估计算法失效或精度下降。
- 需要在保证估计唯一性的前提下降低计算复杂度。

## Application Scenario（应用场景）

- 大规模天线 AFDM-ISAC 系统
- 高移动性目标的角度-时延-多普勒联合估计
- UAV/车辆等近远场混合感知场景

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在近场与远场目标共存且存在分数时延/多普勒的 AFDM-ISAC 系统中，如何实现保证唯一性且低复杂度的角度-时延-多普勒联合估计？

核心问题：

- 如何把接收信号构造成可利用低秩结构的张量模型？
- 如何保证 CP 分解的唯一性？
- 如何在保证精度的同时降低复杂度？
---

# 4. Related Work（相关工作）

已有方法：

1. **传统 AFDM 感知参数估计**：未同时处理 NF/FF 混合与分数参数。
2. **通用张量 CP 分解**：缺少对因子矩阵 Vandermonde 结构的利用。
3. **OTFS 类波形的感知算法**：AFDM 的多啁啾结构与之不同。

现有不足：

- 分数时延/多普勒与 NF/FF 混合共存时精度下降。
- 通用 CP 分解未利用结构信息，唯一性难以保证且复杂度高。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 把接收的 ISAC 信号建模为**三阶张量**，该张量具有低秩 CANDECOMP/PARAFAC（CP）格式。
- 利用因子矩阵的 **Vandermonde 特性**与**空间平滑技术**，开发保证唯一性条件的结构化 CP 分解方法。
- 进一步提出低复杂度估计方案获取目标感知参数。

> 原文：
> "we model the received ISAC signals as a third-order tensor that admits a low-rank CANDECOMP/PARAFAC (CP) format. By employing the Vandermonde nature of the factor matrix and the spatial smoothing technique, we develop a structured CP decomposition method that guarantees the condition for uniqueness."
>
> 原文：
> "We further propose a low-complexity estimation scheme to acquire target sensing parameters"

## Model / Framework

信号模型：

- **波形**：AFDM（多啁啾，仿射频分复用）
- **张量模型**：三阶张量，具有低秩 CP 格式
- **目标场景**：近场（NF）与远场（FF）混合共存
- **待估参数**：角度（angle）、时延（delay）、多普勒（Doppler）

## Algorithm / Technique

采用：

- 三阶张量建模（third-order tensor）
- CANDECOMP/PARAFAC（CP）低秩分解
- Vandermonde 结构利用
- 空间平滑（spatial smoothing）
- 低复杂度参数估计方案

## Key Steps

1. 建立混合 NF/FF 场景下的 AFDM-ISAC 接收信号模型。
2. 把接收信号构造为三阶张量并验证其低秩 CP 结构。
3. 利用因子矩阵的 Vandermonde 特性，结合空间平滑技术构造结构化 CP 分解。
4. 给出并证明分解唯一性条件。
5. 设计低复杂度方案从分解结果中提取角度、时延与多普勒参数。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **接收信号模型**：三阶张量 X，可表示为低秩 CP 格式：

$$\mathcal{X} \approx \sum_{r=1}^{R} a_r \circ b_r \circ c_r$$

其中 R 为张量秩（对应目标数），a_r、b_r、c_r 分别对应角度、时延、多普勒维度的因子向量。

- **关键结构性质**：因子矩阵具有 Vandermonde 特性，可利用以保唯一性。

> 说明：张量构造方式、空间平滑的具体处理与唯一性条件的严格表述见 [[03fulltext/ISAC/2UM9X5FB]] 原文，此处不重述未逐项核验的推导。PDF 页码未验证。

## Assumptions

假设：

- 接收信号可被组织为具有低秩 CP 结构的三阶张量。
- 因子矩阵具备 Vandermonde 结构（由阵列几何与啁啾参数决定）。
- 空间平滑可有效处理相干信号（如相干多径）。

## Optimization Objective

目标：

- 在保证分解唯一性的前提下，以低复杂度准确估计目标的角度、时延与多普勒参数。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体阵元数、载频、目标数等参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 角度、时延、多普勒的估计精度（如 RMSE）
- CP 分解唯一性满足情况
- 计算复杂度

## Results

主要结果：

- 所提结构化 CP 分解方法可保证分解的唯一性条件。
- 所提低复杂度方案可有效获取目标感知参数（角度/时延/多普勒）。

> 说明：具体的估计精度数值、复杂度量级与参数配置未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/2UM9X5FB]] 的仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 面向混合 NF/FF 场景的 AFDM-ISAC 系统提出新的角度-时延-多普勒估计方案。
2. 把接收 ISAC 信号建模为具有低秩 CP 格式的三阶张量。
3. 利用因子矩阵 Vandermonde 特性与空间平滑技术，提出保证唯一性的结构化 CP 分解方法。
4. 进一步提出低复杂度的目标感知参数估计方案。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 利用 CP 因子矩阵的 Vandermonde 结构是把「结构信息」转化为「唯一性保证」的关键。
- 空间平滑可解决相干信号导致的分解退化问题。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 抓住 AFDM-ISAC 中「NF/FF 混合 + 分数参数」这一真实且困难的设定。
- 张量建模 + 结构化 CP 分解是有理论深度的做法，且明确处理唯一性这一核心问题。
- 同时给出低复杂度方案，兼顾理论与实用。

- 局限：本文量化结果需查阅仿真章节才能评估。

---

# 10. Limitation（不足）

论文不足：

1. 量化性能需查阅仿真章节，摘要未给具体数值。
2. 仿真验证，无实测数据。
3. 张量构造与空间平滑会牺牲部分孔径/孔径效率。
4. 未与 OTFS 等同类波形在同一设定下做充分对比。

未来可能改进：

- 在实测或半实物平台上验证。
- 与 OTFS-ISAC 在同一 NF/FF 混合设定下对比。
- 研究更低复杂度的在线实现（面向实时感知）。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 多维参数估计（角度/时延/多普勒）天然适合张量建模，CP 分解可直接对应三个维度。
- 「唯一性」是 CP 分解用于参数估计的核心理论问题，利用 Vandermonde 结构是关键突破口。
- 空间平滑不只是阵列信号处理技巧，在张量分解中同样用于处理相干性。
- NF/FF 混合是大规模天线下的真实问题（近场边界随孔径增大而扩展）。

## Connection With My Work

和我的研究/项目关系：

- AFDM 适合 UAV 高移动性场景，该文的参数估计方案可作为 UAV-ISAC 感知算法候选。
- 张量建模思路可迁移到自己的多维参数联合估计问题。
- 与 [[02vault/信道估计/Diagonally Reconstructed Channel Estimation for MIMO-AFDM|MIMO-AFDM 信道估计]] 形成互补：该文解决通信侧信道估计，本文解决感知侧参数估计。

## Possible Ideas

可能的新想法：

- 把该估计方案与 UAV 轨迹优化结合，用感知结果驱动轨迹调整。
- 研究 NF/FF 混合在 UAV 空地场景下的实际发生条件与占比。
- 对比该结构化 CP 方法与基于压缩感知/深度学习的估计方案。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/信道估计/Diagonally Reconstructed Channel Estimation for MIMO-AFDM|MIMO-AFDM 信道估计]] — 同为 AFDM 系统，该文解决通信侧信道估计，本文解决感知侧参数估计
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]] — 同属 ISAC，该文关注波束设计，本文关注接收端参数估计

---

# 13. Summary Card（快速复习）

## Problem

> 大规模天线 AFDM-ISAC 中，NF/FF 目标共存与分数时延/多普勒使目标感知参数难以准确获取。

## Method

> 把接收信号建模为三阶低秩 CP 张量，利用因子矩阵 Vandermonde 特性与空间平滑，提出保证唯一性的结构化 CP 分解与低复杂度估计方案。

## Result

> 保证了 CP 分解唯一性，并有效获取角度/时延/多普勒参数（具体精度见全文仿真章节）。

## Importance

> 为混合近远场场景下的 AFDM-ISAC 感知提供了有理论保证（唯一性）且可实现的估计方案。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 AFDM-ISAC 在近场/远场混合与分数时延/多普勒条件下目标参数难以准确估计的问题。

Q:
核心方法是什么？

A:
三阶张量低秩 CP 建模 + 利用 Vandermonde 结构与空间平滑的结构化 CP 分解 + 低复杂度参数提取。

Q:
最大贡献是什么？

A:
提出保证唯一性的结构化 CP 分解方法，使混合 NF/FF 场景下的角度-时延-多普勒联合估计具备理论保证。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `2UM9X5FB`，PDF 附件 `G9CX5BUU`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/2UM9X5FB]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 张量构造、唯一性条件的严格表述与仿真数值未在当前材料中逐项定位，已在正文如实标注，未做推测。