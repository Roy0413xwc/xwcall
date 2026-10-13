---
title: "Learning to Beamform for Integrated Sensing and Communication: A Graph Neural Network With Implicit Projection Approach"
aliases:
  - GNN 波束成形
  - 学习式 ISAC 资源分配
tags:
  - literature-note
  - reading-note
  - ISAC
  - 图神经网络
  - 波束成形
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2025
author: Yifei Zhao, Yong Zhou, Zixin Wang, Yuanming Shi, Nan Cheng, Haibo Zhou
year: 2025
journal: IEEE Transactions on Wireless Communications

theme: 用图神经网络（GNN）求解多用户多目标 ISAC 的高维非凸波束成形问题
study_area: 通感一体化 / 图神经网络 / 波束成形
methodology: 带隐式层的图神经网络（GNN），在通信性能约束下优化雷达发射波束方向图
core_variable: 雷达发射波束方向图、通信性能约束、计算复杂度、解的可行性、可扩展性
key_finding: 相比优化类算法（复杂度高）与传统学习类算法（返回不可行解），所提 GNN 兼顾高效、可扩展与可行性
relevance: 与本 Vault 的 ISAC 方向对口，且直接针对「优化太慢 / 学习不可行」这一两难

type: literature-note
zotero_key: "I6IKDDQA"
pdf_key: "ACEMP65W"
doi: "10.1109/TWC.2025.3550315"
collection: "ISAC"
note_path: "02vault/ISAC/Learning to Beamform for ISAC (GNN).md"
fulltext_path: "03fulltext/ISAC/I6IKDDQA.md"
status:
  - Reading
rating: 五星
---

# Learning to Beamform for Integrated Sensing and Communication: A Graph Neural Network With Implicit Projection Approach

---

# 📌 Basic Information（基本信息）

## Author
Yifei Zhao, Yong Zhou, Zixin Wang, Yuanming Shi, Nan Cheng, Haibo Zhou

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2025.3550315

> Zotero 入口：zotero://select/library/items/I6IKDDQA
> PDF 入口：zotero://open-pdf/library/items/ACEMP65W
> 全文 Markdown：[[03fulltext/ISAC/I6IKDDQA]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- Graph Neural Networks (GNN)
- Transmit Beampattern Optimization
- Resource Allocation

---

# 1. Abstract Summary（一句话总结）

> 该文针对多通信用户、多感知目标的 ISAC 场景，指出资源分配问题高维非凸导致优化类算法复杂度高、传统学习类算法返回不可行解的两难，提出带隐式层的图神经网络（GNN），在通信性能约束下高效、可扩展地优化雷达发射波束方向图。

---

# 2. Research Background（研究背景）

## 背景：

- ISAC 是 6G 的重要使用场景，能通过共享频谱与硬件实现感知与通信的无缝融合与互利。

> 原文：
> "Integrated sensing and communication (ISAC), as an important usage scenario of 6G, is capable of seamlessly integrating wireless sensing and communication for their mutual benefit."

## Motivation（研究动机）

- 充分发挥 ISAC 优势高度依赖有效求解资源分配问题，但这些问题通常**高维且非凸**，导致：
  - **基于优化的算法**：计算复杂度高
  - **传统基于学习的算法**：返回**不可行解**

> 原文：
> "Taking full advantage of ISAC heavily relies on effectively solving resource allocation problems, which, however, are generally high-dimensional and non-convex, resulting in the optimization-based algorithms exhibiting high computation complexity and the traditional learning-based algorithms returning infeasible solutions."

## Application Scenario（应用场景）

- 多通信用户 + 多感知目标的 ISAC 系统
- 需低时延求解的实时波束成形
- 规模可变、需算法具备可扩展性的网络

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在通信性能约束下，设计出既高效、可扩展、又能保证解的可行性的 ISAC 波束成形算法？

核心问题：

- 如何避免优化类算法的高复杂度？
- 如何避免传统学习类算法的不可行解？
- 如何让算法随网络规模扩展（可扩展性）？

---

# 4. Related Work（相关工作）

已有方法：

1. **基于优化的算法**：能得可行解，但高维非凸下计算复杂度高，难实时。
2. **传统基于学习的算法**：推理快，但常返回**不可行解**（不满足约束）。
3. **固定规模设计的网络**：难以适应不同数量的用户/目标。

现有不足：

- 效率与可行性不可兼得；可扩展性不足。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 面向**多通信用户 + 多感知目标**的 ISAC 场景，开发高效、可扩展的算法。
- 目标：在**通信性能约束**下优化**雷达发射波束方向图**（radar transmit beampattern）。
- 提出带**隐式层（implicit layer）**的**图神经网络（GNN）**。

> 原文：
> "we consider an ISAC scenario featured by multiple communication users and multiple sensing targets, aiming to develop an efficient and scalable algorithm that optimizes the radar transmit beampattern under the communication performance constraint. To this end, we propose a graph neural network (GNN) with implici"

## Model / Framework

方法框架：

- **图建模**：把 ISAC 网络建模为图（节点为用户/目标/天线等，边为信道或干扰关系），使 GNN 可处理规模变化
- **网络结构**：GNN + 隐式层（用于保证约束/可行性）
- **优化目标**：雷达发射波束方向图
- **约束**：通信性能

## Algorithm / Technique

采用：

- 图神经网络（Graph Neural Network, GNN）
- 隐式层（implicit layer）
- 雷达发射波束方向图优化
- 通信性能约束处理

## Key Steps

1. 建立多用户多目标 ISAC 系统模型，定义波束方向图与通信约束。
2. 把系统建模为图结构，使模型可随规模扩展。
3. 设计带隐式层的 GNN，隐式层用于保证输出满足约束（可行性）。
4. 训练该网络以在通信约束下优化雷达波束方向图。
5. 验证效率、可行性与可扩展性。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **优化目标**：雷达发射波束方向图（radar transmit beampattern）
- **约束**：通信性能（communication performance constraint）
- **问题性质**：高维、非凸
- **求解**：GNN + 隐式层

> 说明：图的构建方式、隐式层的具体形式与约束满足的机制见 [[03fulltext/ISAC/I6IKDDQA]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- ISAC 系统可建模为图，且图结构能反映关键的干扰/信道关系。
- 隐式层可将约束可行性嵌入网络前向计算。
- 训练数据可覆盖目标场景的分布。

## Optimization Objective

目标：

- 在满足通信性能约束的前提下优化雷达波束方向图，同时保证算法高效、可行、可扩展。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体用户/目标数、天线数与信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 优化类算法（复杂度对照）
- 传统学习类算法（可行性对照）

## Metrics

评价指标：

- 雷达波束方向图质量
- 通信性能约束满足情况（可行性）
- 计算复杂度 / 推理时间
- 可扩展性（不同规模下的表现）

## Results

主要结果：

- 所提 GNN 在效率、可行性与可扩展性上优于两类对照方法（优化类复杂度高、传统学习类返回不可行解）。

> 说明：具体的复杂度与性能数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/I6IKDDQA]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 明确指出 ISAC 资源分配的两难：优化类复杂度高、传统学习类返回不可行解。
2. 面向多用户多目标 ISAC 场景，在通信性能约束下优化雷达发射波束方向图。
3. 提出带隐式层的 GNN，兼顾高效、可行与可扩展。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 隐式层是把「可行性」嵌入学习型方法的关键——这是传统学习类算法的主要短板。
- 图建模使算法天然具备处理规模变化的能力（可扩展性）。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 诊断精准：「优化慢 vs 学习不可行」是 ISAC 算法落地的真实两难。
- 用隐式层保证可行性是有针对性的设计，不是简单套用 GNN。
- 与本 Vault [[02vault/UAV/ISAC-Enabled Beam Tracking for U2U|U2U 波束跟踪]] 等工程工作形成方法层面的对照。

- 局限：量化收益需查阅仿真章节。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅仿真章节。
2. GNN 需训练数据，跨场景泛化能力需验证。
3. 隐式层会带来额外的前向计算开销。
4. 仿真验证，无实测。

未来可能改进：

- 验证跨场景泛化与在线自适应。
- 分析隐式层的计算开销与收益权衡。
- 在真实 ISAC 平台上验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **「学习类算法返回不可行解」是 ISAC 特有的痛点**——因为通信性能是硬约束，纯回归式网络容易违反。
- 隐式层是把约束嵌入网络前向计算的有效手段，值得借鉴到其他带约束的学习问题。
- 图建模的价值在于可扩展性：节点数变化不影响网络参数，这是相对全连接网络的关键优势。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 ISAC 方向对口，且提供了「优化 vs 学习」之外的第三条路径。
- 隐式层保证可行性的思路可用于自己的约束型学习问题。
- 与 [[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO 协同 ISAC]] 形成对照：该文用 MARL，本文用 GNN + 隐式层。

## Possible Ideas

可能的新想法：

- 把隐式层思路引入 UAV-ISAC 的轨迹优化，保证动力学约束可行。
- 对比 GNN 与 MARL 在多目标 ISAC 上的样本效率与可扩展性。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO 协同 ISAC]] — 同属 ISAC 学习类方法，该文用 MARL，本文用 GNN + 隐式层
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]] — 同属波束成形，该文用优化+结构洞察，本文用学习

---

# 13. Summary Card（快速复习）

## Problem

> ISAC 资源分配高维非凸：优化类算法复杂度高，传统学习类算法返回不可行解。

## Method

> 带隐式层的图神经网络（GNN），在通信性能约束下优化雷达发射波束方向图。

## Result

> 兼顾高效、可行与可扩展（具体数值见全文仿真章节）。

## Importance

> 用隐式层解决「学习类算法不可行」这一关键短板，为 ISAC 提供可行的学习式方案。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 ISAC 资源分配中优化类算法复杂度高、传统学习类算法返回不可行解的两难。

Q:
核心方法是什么？

A:
带隐式层的图神经网络（GNN），在通信性能约束下优化雷达发射波束方向图。

Q:
最大贡献是什么？

A:
用隐式层保证学习类算法输出的可行性，同时用图建模获得可扩展性。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `I6IKDDQA`，PDF 附件 `ACEMP65W`。
- PDF 经 pypdf 提取全文（71768 字符），原文引用均取自全文 Markdown [[03fulltext/ISAC/I6IKDDQA]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 图构建方式、隐式层形式与量化数值未在当前材料中逐项定位，已在正文如实标注，未做推测。