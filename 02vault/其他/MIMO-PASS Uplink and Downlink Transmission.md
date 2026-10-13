---
title: "MIMO-PASS: Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems"
aliases:
  - MIMO-PASS
  - Pinching Antenna
tags:
  - literature-note
  - reading-note
  - 可重构天线
  - MIMO
created: 2026-10-13
source: IEEE Transactions on Communications, 2026
author: (原文首页未在当前全文提取中定位到完整作者行)
year: 2026
journal: IEEE Transactions on Communications

theme: 把可捏合天线系统（PASS）引入多用户 MIMO，研究上下行传输的混合波束成形与检测
study_area: 可重构天线 / Pinching Antenna / MIMO 传输
methodology: 分式规划（FP）+ Gauss-Seidel 迭代优化数字预编码与捏合单元位置
core_variable: 加权和速率、吞吐量、算法收敛性与精度
key_finding: PASS 使上下行吞吐量相比大规模 MIMO 与经典混合模数设计显著提升
relevance: 新型可重构天线技术，可作为 UAV 通信中轻量可调天线的候选方案

type: literature-note
zotero_key: "GP5BSSKT"
pdf_key: "NUDLOEU2"
doi: "10.1109/tcomm.2026.3668156"
collection: "其他"
note_path: "02vault/其他/MIMO-PASS Uplink and Downlink Transmission.md"
fulltext_path: "03fulltext/其他/GP5BSSKT.md"
status:
  - Reading
rating: 四星
---

# MIMO-PASS: Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems

---

# 📌 Basic Information（基本信息）

## Author
未在当前全文提取中定位到完整作者行（PDF 首页作者信息提取失败），建议以 Zotero 条目或 PDF 首页为准

## Year
2026

## Source
IEEE Transactions on Communications｜DOI: 10.1109/tcomm.2026.3668156

> Zotero 入口：zotero://select/library/items/GP5BSSKT
> PDF 入口：zotero://open-pdf/library/items/NUDLOEU2
> 全文 Markdown：[[03fulltext/其他/GP5BSSKT]]

## Research Area

- Pinching-Antenna Systems (PASS)
- Reconfigurable Antennas
- Multiuser MIMO
- Hybrid Beamforming / Multiuser Detection

---

# 1. Abstract Summary（一句话总结）

> 该文把可捏合天线系统（PASS）引入多用户 MIMO，对下行联合优化接入点数字预编码与波导上捏合单元位置以最大化加权和速率（用分式规划与 Gauss-Seidel 求解），并针对上行设计迭代方案解决混合多用户检测问题，仿真显示上下行吞吐量相比大规模 MIMO 与经典混合设计显著提升。

---

# 2. Research Background（研究背景）

## 背景：

- 可捏合天线系统（PASS）是近期的柔性天线技术，通过在介质波导上附加「捏合元件」实现。
- PASS 具备可重构特性，是下一代无线系统的候选技术之一。
- 但把 PASS 部署到多用户 MIMO 场景的上下行传输问题尚未被充分研究。

> 原文：
> "Pinching-antenna systems (PASSs) are a recent flexible-antenna technology that is realized by attaching simple components, referred to as pinching elements, to dielectric waveguides."

## Motivation（研究动机）

- 下行需联合优化数字预编码与捏合单元激活位置，是混合波束成形问题。
- 上行存在混合多用户检测问题，需专门设计迭代方案。
- 需要验证 PASS 相比既有 MIMO 架构（大规模 MIMO、经典混合模数设计）的实际增益量级。

## Application Scenario（应用场景）

- 下一代无线系统的可重构天线部署
- 室内/热点区域的高吞吐覆盖
- UAV 平台上的轻量化可调天线
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在多用户 MIMO 场景中部署 PASS，分别设计下行的混合波束成形与上行的多用户检测方案，并量化其相对既有 MIMO 架构的吞吐增益？

核心问题：

- 下行如何联合优化数字预编码与捏合单元位置以最大化加权和速率？
- 上行的混合多用户检测问题如何迭代求解？
- PASS 相比大规模 MIMO 与经典混合模数设计的增益量级如何？

---

# 4. Related Work（相关工作）

已有方法：

1. **大规模 MIMO（massive MIMO）**：基线架构之一。
2. **经典混合模数设计（classical hybrid analog-digital designs）**：基线架构之一。
3. **既有柔性/可重构天线技术**：PASS 的技术背景。

现有不足：

- 既有 MIMO 架构的天线位置固定，缺少 PASS 提供的空间自由度。
- PASS 在多用户 MIMO 上下行传输中的联合优化问题未被系统研究。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- **下行**：把问题建模为最优混合波束成形——联合优化接入点（AP）的数字预编码矩阵与波导上捏合单元的激活位置，最大化可达加权和速率。
- **求解工具**：借助分式规划（fractional programming）与 Gauss-Seidel 方法，提出两种低复杂度算法迭代更新预编码矩阵与捏合单元激活位置。
- **上行**：研究 PASS 辅助的上行传输，设计迭代方案解决底层的混合多用户检测问题。

> 原文：
> "For downlink PASS-aided communication, we formulate the optimal hybrid beamforming, in which the digital precoding matrix at the access point and the location of pinching elements on the waveguides are jointly optimized to maximize the achievable weighted sum-rate."
>
> 原文：
> "Invoking fractional programming and Gauss-Seidel approach, we propose two low-complexity algorithms to iteratively update the precoding matrix and activated locations of the pinching elements."
>
> 原文：
> "We further study uplink transmission aided by a PASS, where an iterative scheme is designed to address the underlying hybrid multiuser detection problem."

## Model / Framework

系统模型：

- **下行**：AP 数字预编码矩阵 + 波导上捏合单元位置（联合优化）
- **上行**：混合多用户检测（hybrid multiuser detection）
- **捏合单元位置**：可通过网格搜索高效确定

## Algorithm / Technique

采用：

- 分式规划（Fractional Programming, FP）
- Gauss-Seidel 迭代方法
- 网格搜索（确定捏合单元位置）
- 迭代式混合多用户检测

## Key Steps

1. 建立 PASS 辅助的多用户 MIMO 上下行系统模型。
2. 下行：构造加权和速率最大化问题，用 FP 将分式目标转化。
3. 用 Gauss-Seidel 思路交替更新数字预编码矩阵与捏合单元激活位置（两种低复杂度算法）。
4. 捏合单元位置可通过网格搜索高效确定。
5. 上行：设计迭代方案求解混合多用户检测问题。
6. 通过大量数值实验验证收敛性、精度与相对基线的增益。
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **下行目标**：最大化可达加权和速率（weighted sum-rate）。
- **优化变量**：AP 数字预编码矩阵、波导上捏合单元的激活位置。
- **求解思路**：分式规划处理分式目标 + Gauss-Seidel 交替更新。

上行可达速率表达式（原文式 74，第 k 个用户）：

$$R_{ul}(m_k, L) = \log\det\left(I_M + g_k(L)g_k^H(L)\left(\sum_{j\neq k} g_j(L)g_j^H(L) + \frac{\varsigma^2}{P_u}I_M\right)^{-1}\right)$$

> 说明：其中 g_k(L) 为第 k 个用户在捏合单元位置 L 下的等效信道，P_u 为上行发射功率，varsigma² 为噪声功率。完整推导与其余公式见 [[03fulltext/其他/GP5BSSKT]] 原文。PDF 页码未验证。

## Assumptions

假设：

- 捏合单元可沿介质波导移动并激活在任意位置。
- 信道为 PASS 辅助的等效信道，可由捏合单元位置参数化。
- 位置优化可用网格搜索在可接受复杂度内完成。

## Optimization Objective

目标：

- 下行最大化加权和速率；上行解决混合多用户检测，提升上行吞吐量。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 大量数值实验（extensive numerical experiments），从两方面评估：
  1. 所提算法的收敛性与精度；
  2. 在相同仿真环境下与经典 MIMO 基线对比，评估该技术带来的增益量级。

> 原文：
> "we evaluate the convergence and precision of the proposed algorithms. (ii) We compare MIMO-PASSs against classical MIMO baselines in the same simulated environment to assess the order of gain achieved by this technology."

## Baseline

比较方法：

- 大规模 MIMO（massive MIMO）
- 经典混合模数设计（classical hybrid analog-digital designs）

## Metrics

评价指标：

- 加权和速率（下行）
- 吞吐量（上行/下行）
- 算法收敛性与精度

## Results

主要结果：

- 使用 PASS 后，上行与下行吞吐量相比基线 MIMO 架构均显著提升。
- 所提两种低复杂度算法具备可用的收敛性与精度。
- 凸显了 PASS 作为下一代可重构天线技术的巨大潜力。

> 原文：
> "The results demonstrate that using a PASS, the throughput in both uplink and downlink is boosted significantly as compared with baseline MIMO architectures, such as massive MIMO and classical hybrid analog-digital designs. This highlights the great potential of PASSs, making it a promising reconfigurable antenna technology for next-generation wireless systems."

> 说明：具体的吞吐量增益数值与收敛曲线数据未在当前材料中逐项定位，此处不做引述。
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 首次系统研究 PASS 在多用户 MIMO 上下行传输中的部署。
2. 下行：建模为最优混合波束成形，联合优化数字预编码与捏合单元位置以最大化加权和速率。
3. 提出两种基于 FP 与 Gauss-Seidel 的低复杂度算法，迭代更新预编码矩阵与激活位置。
4. 上行：设计迭代方案解决混合多用户检测问题。
5. 仿真验证：上下行吞吐量相比大规模 MIMO 与经典混合设计显著提升。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- PASS 的捏合单元位置是新引入的空间自由度，可与数字预编码联合优化。
- FP + Gauss-Seidel 的组合可在低复杂度下处理该混合优化问题。

## My Evaluation

我的评价：

四星

创新程度：

中高

理由：

- 把新兴 PASS 技术推进到多用户 MIMO 场景，选题前沿且工程问题定义清晰。
- 上下行都给出方案，完整性好。
- 但核心优化工具（FP、Gauss-Seidel、网格搜索）均为成熟方法，创新性主要在问题建模与场景适配。

---

# 10. Limitation（不足）

论文不足：

1. 捏合单元位置用网格搜索，精度与复杂度受网格粒度制约。
2. 纯仿真验证，无硬件平台实测。
3. 未考虑捏合单元移动的物理时延与机械约束。
4. 本文作者行在 PDF 文本提取中未能定位，元数据完整性有缺口。

未来可能改进：

- 用连续优化或学习式方法替代网格搜索。
- 在真实 PASS 硬件上验证吞吐增益。
- 研究移动/时变场景下的位置自适应策略。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 「天线位置」本身可以成为优化变量，这是可重构天线相对固定阵列的本质优势。
- FP 是处理分式目标（如速率、SINR）的通用工具，Gauss-Seidel 是交替更新的简洁框架。
- 新兴天线技术的价值需要在相同仿真环境下与既有架构做定量对比才能说服人。

## Connection With My Work

和我的研究/项目关系：

- PASS 的轻量化、可重构特性对 UAV 载荷受限场景有吸引力。
- 位置优化的建模思路可迁移到 UAV 载天线阵列的位置/朝向优化。
- FP + 交替优化的框架可用于自己的资源分配问题。

## Possible Ideas

可能的新想法：

- 研究 UAV 平台上 PASS 的部署（振动、姿态变化对位置精度的影响）。
- 把 PASS 与 ISAC 结合，探索位置自由度对感知性能的增益。
- 用连续优化替代网格搜索以降低位置优化复杂度。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]] — 同属可重构天线增强 ISAC，该文用 IRS 的 6D 参数，本文用捏合单元位置

---

# 13. Summary Card（快速复习）

## Problem

> PASS 在多用户 MIMO 上下行传输中的部署问题未被系统研究，缺少混合波束成形与多用户检测方案。

## Method

> 下行用 FP + Gauss-Seidel 交替优化数字预编码与捏合单元位置；上行设计迭代式混合多用户检测。

## Result

> 上下行吞吐量相比大规模 MIMO 与经典混合模数设计显著提升。

## Importance

> 论证了 PASS 作为下一代可重构天线技术的潜力，把该技术推进到多用户 MIMO 场景。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 PASS 在多用户 MIMO 场景中的部署问题，包括下行混合波束成形与上行多用户检测。

Q:
核心方法是什么？

A:
下行用分式规划 + Gauss-Seidel 交替优化预编码矩阵与捏合单元位置；上行用迭代式混合检测。

Q:
最大贡献是什么？

A:
系统给出 PASS 在多用户 MIMO 上下行的方案，并量化证明其相比大规模 MIMO 与经典混合设计的吞吐增益。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `GP5BSSKT`，PDF 附件 `NUDLOEU2`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/其他/GP5BSSKT]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- **作者行缺失**：PDF 首页作者信息在文本提取中未能定位，已如实标注，未做推测。
- 具体吞吐量增益数值与收敛数据未在当前材料中逐项定位，已在正文标注。