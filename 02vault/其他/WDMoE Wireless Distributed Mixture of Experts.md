---
title: "WDMoE: Wireless Distributed Mixture of Experts for Large Language Models"
aliases:
  - WDMoE
  - 无线分布式 MoE
tags:
  - literature-note
  - reading-note
  - LLM
  - 边缘智能
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2025
author: Nan Xue, Yaping Sun, Zhiyong Chen, Meixia Tao, Xiaodong Xu, Liang Qian, Shuguang Cui, Ping Zhang
year: 2025
journal: IEEE Transactions on Wireless Communications

theme: 把大语言模型的 MoE 层分布部署到基站边缘服务器与移动设备，实现无线分布式专家混合推理
study_area: 边缘智能 / 大语言模型 / 无线资源分配
methodology: MoE 层拆解部署 + 兼顾模型能力与时延的性能指标 + 专家选择与带宽分配联合优化
core_variable: 推理时延、模型精度（能力）、带宽分配、专家选择
key_finding: 把门控网络置于基站、专家网络分布到设备，利用设备并行推理能力；联合优化专家选择与带宽以在保持精度下最小化时延
relevance: 与本 Vault 的 LLM 分类相关，是无线网络支撑大模型部署的代表工作

type: literature-note
zotero_key: "J4JEDLUD"
pdf_key: "V3A5BBRB"
doi: "10.1109/twc.2025.3585163"
collection: "其他"
note_path: "02vault/其他/WDMoE Wireless Distributed Mixture of Experts.md"
fulltext_path: "03fulltext/其他/J4JEDLUD.md"
status:
  - Reading
rating: 四星
---

# WDMoE: Wireless Distributed Mixture of Experts for Large Language Models

---

# 📌 Basic Information（基本信息）

## Author
Nan Xue, Yaping Sun, Zhiyong Chen, Meixia Tao, Xiaodong Xu, Liang Qian, Shuguang Cui, Ping Zhang

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/twc.2025.3585163

> Zotero 入口：zotero://select/library/items/J4JEDLUD
> PDF 入口：zotero://open-pdf/library/items/V3A5BBRB
> 全文 Markdown：[[03fulltext/其他/J4JEDLUD]]

## Research Area

- Mixture of Experts (MoE)
- Edge Inference / Wireless Distributed Computing
- Joint Expert Selection and Bandwidth Allocation

---

# 1. Abstract Summary（一句话总结）

> 该文提出无线分布式专家混合（WDMoE）架构：把 LLM 的 MoE 层拆解——门控网络与前置层置于基站，专家网络分布到移动设备——利用设备的并行推理能力，并提出兼顾模型能力与时延的性能指标，通过联合优化专家选择与带宽分配在保持精度的同时最小化时延。

---

# 2. Research Background（研究背景）

## 背景：

- 大语言模型（LLM）在各类自然语言处理任务中取得显著成功。
- 但无线网络在支撑 LLM 方面的作用尚未被充分探索。

> 原文：
> "Large Language Models (LLMs) have achieved significant success in various natural language processing tasks, but the role of wireless networks in supporting LLMs has not been thoroughly explored."

## Motivation（研究动机）

- 移动设备的算力与缓存资源有限，难以独立承载大模型推理。
- MoE 架构天然具有「专家并行」特性，适合拆解到边缘设备分布式执行。
- 需要在推理时延与模型能力（精度）之间取得平衡。

## Application Scenario（应用场景）

- 基站边缘服务器 + 移动设备协同的 LLM 推理
- 6G 网络中的边缘智能服务
- UAV/车载等资源受限设备的分布式大模型推理（潜在迁移）

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何把 LLM 的 MoE 层拆解部署到基站与移动设备，并通过联合优化专家选择与带宽分配，在保持模型精度的同时最小化推理时延？

核心问题：

- MoE 层如何拆分（哪些放基站、哪些放设备）？
- 如何定义兼顾「模型能力」与「时延」的性能指标？
- 专家选择与带宽如何联合优化？
---

# 4. Related Work（相关工作）

已有方法：

1. **云端集中推理**：LLM 部署在云端，时延高且依赖回传。
2. **设备端独立推理**：受限于移动设备算力与缓存，难以承载大模型。
3. **通用边缘推理拆分**：未针对 MoE 的专家并行特性做专门设计。

现有不足：

- 无线网络支撑 LLM 的作用未被充分探索。
- 缺少利用 MoE 专家并行性的无线分布式部署方案。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出**无线分布式专家混合（WDMoE）**架构，实现 LLM 在基站边缘服务器与移动设备间的协同部署。
- **拆解 MoE 层**：把门控网络（gating network）与其前置神经网络层放在基站（BS），把专家网络（expert networks）分布到各设备。
- 该部署利用**专家网络在移动设备上的并行推理能力**，有效利用设备有限的计算与缓存资源。
- 提出兼顾**模型能力**与**时延**的性能指标，并据此联合优化**专家选择与带宽分配**。

> 原文：
> "we decompose the MoE layer in LLMs by placing the gating network and the preceding neural network layer at BS, while distributing the expert networks among the devices."
>
> 原文：
> "This deployment leverages the parallel inference capabilities of expert networks on mobile devices, effectively utilizing the limited computing and caching resources of these devices."
>
> 原文：
> "we develop a performance metric for WDMoE-based LLMs, which accounts for both model capability and latency. To minimize the latency while maintaining accuracy, we jointly optimize expert selection and bandwidth allocation"

## Model / Framework

系统模型：

- **基站（BS）**：承载门控网络 + 前置神经网络层
- **移动设备**：分布式承载各专家网络
- **执行流程**：设备上专家并行推理 → 结果回传基站
- **优化变量**：专家选择（哪些专家参与）+ 带宽分配

## Algorithm / Technique

采用：

- MoE（Mixture of Experts）层拆解部署
- 门控网络与专家网络的分离放置
- 兼顾模型能力与时延的性能指标设计
- 专家选择与带宽分配的联合优化

## Key Steps

1. 分析 LLM 的 MoE 结构，确定可拆分的边界（门控网络 vs 专家网络）。
2. 把门控网络与前置层部署在基站，专家网络分布到移动设备。
3. 设计同时刻画模型能力（精度）与推理时延的性能指标。
4. 构造优化问题：在保持精度的约束下最小化时延。
5. 联合优化专家选择与带宽分配。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **性能指标**：同时刻画模型能力（model capability，即精度）与推理时延（latency）。
- **优化变量**：专家选择、带宽分配。
- **目标**：在保持精度（accuracy）的前提下最小化时延。

> 说明：性能指标的闭式定义、时延模型（含计算与传输）与优化问题的具体形式见 [[03fulltext/其他/J4JEDLUD]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- MoE 的专家网络可独立于门控网络执行，且并行推理能带来实际加速。
- 设备具备基本的计算与缓存能力以承载单个/若干专家。
- 模型能力与参与专家数量/选择之间存在可建模的关系。

## Optimization Objective

目标：

- 在维持模型精度的基础上，最小化端到端推理时延。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真/实验验证（具体 LLM 规模、设备数量、带宽条件未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 推理时延（latency）
- 模型准确率 / 能力（accuracy / model capability）
- 带宽利用效率

## Results

主要结果：

- 所提 WDMoE 架构通过把专家网络分布到设备，利用了设备的并行推理能力。
- 通过联合优化专家选择与带宽分配，在保持精度的同时降低了时延。

> 说明：具体的时延降低比例与精度保持数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/其他/J4JEDLUD]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出 WDMoE 架构，实现 LLM 在基站边缘服务器与移动设备间的协同部署。
2. 拆解 MoE 层：门控网络与前置层置于基站，专家网络分布到设备。
3. 利用专家网络在设备上的并行推理能力，有效利用设备有限的计算与缓存资源。
4. 提出兼顾模型能力与时延的性能指标，并联合优化专家选择与带宽分配以在保持精度下最小化时延。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- MoE 的「专家并行」天然契合分布式部署，是 LLM 边缘化的结构性机遇。
- 把门控网络留在基站可保证路由决策的集中性与一致性。

## My Evaluation

我的评价：

四星

创新程度：

中高

理由：

- 切入点好：把 MoE 的结构特性与无线分布式计算结合，是有洞察的跨域设计。
- 性能指标同时考虑模型能力与时延，避免了只优化时延导致精度崩塌。
- 但量化收益需查阅仿真章节才能评估，且方案对设备异构性的鲁棒性未充分讨论。

---

# 10. Limitation（不足）

论文不足：

1. 设备异构性（算力/电量差异）对专家分配的影响需进一步研究。
2. 无线链路波动会导致专家回传时延抖动，鲁棒性待验证。
3. 量化收益需查阅仿真章节。
4. 缓存受限时专家网络的换入换出开销未充分讨论。

未来可能改进：

- 研究设备异构与链路波动下的自适应专家分配。
- 考虑专家缓存与换入换出策略。
- 在真实无线环境做端到端验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- MoE 不只是训练技巧，其「专家并行」结构本身就适合分布式部署。
- 边缘部署 LLM 的核心矛盾是「精度 vs 时延」，必须把模型能力显式纳入目标或约束。
- 门控网络集中、专家分布是一种清晰的职责划分，保证了路由一致性。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 LLM 分类相关，是无线网络支撑大模型部署的代表工作。
- 分布式推理的「计算—通信权衡」思路可迁移到 UAV 边缘计算场景。
- 与 [[02vault/LLM/Attention Is All You Need|Transformer 开山之作]] 形成对照：该文是架构基石，本文是无线部署的工程延伸。

## Possible Ideas

可能的新想法：

- 把 WDMoE 的分布式思路用于 UAV 集群的协同推理（无人机作为边缘节点）。
- 研究 UAV 链路时变下的专家分配自适应策略。
- 对比「专家并行」与「层间拆分（split learning）」在无线环境下的优劣。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/LLM/Attention Is All You Need|Transformer 开山之作]] — 架构基础，本文是其在无线分布式场景的部署延伸

---

# 13. Summary Card（快速复习）

## Problem

> LLM 在移动设备上部署受算力/缓存限制，且无线网络支撑 LLM 的作用未被充分探索。

## Method

> WDMoE 架构：门控网络与前置层放基站、专家网络分布到设备；提出兼顾模型能力与时延的指标，联合优化专家选择与带宽分配。

## Result

> 利用设备并行推理能力，在保持精度的同时降低时延（具体数值见全文仿真章节）。

## Importance

> 把 MoE 的结构特性与无线分布式计算结合，为 LLM 边缘化部署提供了可行架构。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 LLM 在移动设备上部署受算力/缓存限制、且无线网络支撑 LLM 作用未明的问题。

Q:
核心方法是什么？

A:
WDMoE 架构：门控网络放基站、专家网络分布到设备；用兼顾能力与时延的指标联合优化专家选择与带宽。

Q:
最大贡献是什么？

A:
利用 MoE 专家并行特性实现 LLM 的无线分布式部署，并在保持精度下最小化推理时延。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `J4JEDLUD`，PDF 附件 `V3A5BBRB`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/其他/J4JEDLUD]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 性能指标闭式定义、时延模型与量化仿真数值未在当前材料中定位，已在正文如实标注，未做推测。