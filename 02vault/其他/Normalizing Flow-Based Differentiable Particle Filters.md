---
title: "Normalizing Flow-Based Differentiable Particle Filters"
aliases:
  - 归一化流粒子滤波
  - Differentiable PF
tags:
  - literature-note
  - reading-note
  - 状态估计
  - 粒子滤波
created: 2026-10-13
source: IEEE Transactions on Signal Processing, 2025
author: Xiongjie Chen, Yunpeng Li
year: 2025
journal: IEEE Transactions on Signal Processing

theme: 用（条件）归一化流构建可微粒子滤波的动态/提议/测量模型，摆脱预定义分布族限制
study_area: 序贯状态估计 / 粒子滤波 / 归一化流
methodology: 归一化流建模三个模块 + 理论推导（ELBO 等）+  joint 状态估计与模型学习
core_variable: 状态估计精度、密度估计有效性、模型适应性
key_finding: 用归一化流构建动态/提议/测量模型，既保证合法概率密度，又可自适应学习而不受预定义分布族限制
relevance: 非线性非高斯状态估计可迁移到 UAV 目标跟踪/ISAC 感知侧的滤波问题

type: literature-note
zotero_key: "5LH9KB2X"
pdf_key: "1C8YZBM5"
doi: "10.1109/tsp.2024.3521338"
collection: "其他"
note_path: "02vault/其他/Normalizing Flow-Based Differentiable Particle Filters.md"
fulltext_path: "03fulltext/其他/5LH9KB2X.md"
status:
  - Reading
rating: 四星
---

# Normalizing Flow-Based Differentiable Particle Filters

---

# 📌 Basic Information（基本信息）

## Author
Xiongjie Chen, Yunpeng Li

## Year
2025

## Source
IEEE Transactions on Signal Processing｜DOI: 10.1109/tsp.2024.3521338

> Zotero 入口：zotero://select/library/items/5LH9KB2X
> PDF 入口：zotero://open-pdf/library/items/1C8YZBM5
> 全文 Markdown：[[03fulltext/其他/5LH9KB2X]]

## Research Area

- Sequential State Estimation
- Differentiable Particle Filters
- Normalizing Flows
- Non-linear Non-Gaussian State-Space Models

---

# 1. Abstract Summary（一句话总结）

> 该文提出用（条件）归一化流构建可微粒子滤波框架的动态模型、提议分布与测量模型，从而既获得合法的概率密度，又能自适应学习这些模块而不受预定义分布族（如高斯）的限制，并给出相应的理论推导。

---

# 2. Research Background（研究背景）

## 背景：

- 近期出现了把神经网络引入粒子滤波的热潮，即可微粒子滤波（differentiable particle filters）。
- 其目标是在复杂环境下对非线性、非高斯状态空间模型进行**联合序贯状态估计与模型学习**。

> 原文：
> "there has been a surge of interest in incorporating neural networks into particle filters, e.g. differentiable particle filters, to perform joint sequential state estimation and model learning for non-linear non-Gaussian state-space models in complex environments."

## Motivation（研究动机）

- 现有可微粒子滤波多使用普通（vanilla）神经网络构建，不允许密度估计。
- 因此它们要么局限于 bootstrap 粒子滤波框架，要么采用预定义分布族（如高斯分布），限制了在更复杂真实场景中的性能。

> 原文：
> "Existing differentiable particle filters are mostly constructed with vanilla neural networks that do not allow density estimation. As a result, they are either restricted to a bootstrap particle filtering framework or employ predefined distribution families (e.g. Gaussian distributions), limiting their performance in more complex real-world scenarios."

## Application Scenario（应用场景）

- 非线性非高斯系统的序贯状态估计
- 目标跟踪、导航定位、SLAM
- UAV/ISAC 感知侧的滤波与状态估计（潜在迁移）

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在可微粒子滤波中获得合法的概率密度，并使动态模型、提议分布与测量模型都可自适应学习而不受预定义分布族限制？

核心问题：

- 普通神经网络为何不能用于密度估计，如何替代？
- 归一化流如何用于构建滤波的三个模块？
- 该框架的理论保障（如 ELBO）如何建立？
---

# 4. Related Work（相关工作）

已有方法：

1. **Bootstrap 粒子滤波**：提议分布直接取动态模型，灵活性差。
2. **用普通神经网络的可微粒子滤波**：不允许密度估计，需依赖预定义分布族。
3. **预定义分布族（如高斯）方法**：在复杂真实场景（多峰、重尾）下表达能力不足。

现有不足：

- 无法同时获得「合法概率密度」与「灵活的表达能力」。
- 在复杂场景下性能受限。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出一个可微粒子滤波框架，用**（条件）归一化流（conditional normalizing flows）**构建其三个核心模块：
  - **动态模型**（dynamic model）
  - **提议分布**（proposal distribution）
  - **测量模型**（measurement model）
- 这样既能获得**合法的概率密度**（valid probability densities），又能**自适应地学习**这些模块，而不受预定义分布族限制。
- 作者还给出了相应的理论推导。

> 原文：
> "we present a differentiable particle filtering framework that uses (conditional) normalizing flows to build its dynamic model, proposal distribution, and measurement model. This not only enables valid probability densities but also allows the proposed method to adaptively learn these modules in a flexible way, without being restricted to predefined distribution families."
>
> 原文：
> "We derive the theore"

## Model / Framework

模型结构：

- **框架**：可微粒子滤波（differentiable particle filtering）
- **核心组件**：条件归一化流（conditional normalizing flows）
- **三个被建模模块**：动态模型、提议分布、测量模型
- **联合任务**：序贯状态估计 + 模型学习

## Algorithm / Technique

采用：

- （条件）归一化流（conditional normalizing flows）
- 可微粒子滤波（differentiable particle filtering）
- 变分推断视角的理论推导（ELBO 等）

## Key Steps

1. 建立非线性非高斯状态空间模型下的序贯估计问题。
2. 用条件归一化流参数化动态模型、提议分布与测量模型。
3. 保证各模块输出合法的概率密度（归一化流的可逆变换天然满足）。
4. 进行理论推导（如变分下界），为联合学习提供依据。
5. 端到端联合优化：同时完成状态估计与模型学习。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **状态空间模型**：非线性、非高斯，含状态转移（动态模型）与观测（测量模型）。
- **归一化流的优势**：通过可逆变换把简单分布映射为复杂分布，且**密度可精确计算**（雅可比行列式可得）。
- **联合目标**：序贯状态估计 + 模型学习，通常经由变分下界（ELBO）优化。

> 说明：具体的变分推导、归一化流结构设计（如耦合层）与理论定理见 [[03fulltext/其他/5LH9KB2X]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 状态空间模型为非线性非高斯，需数据驱动建模。
- 归一化流具备足够表达能力以刻画动态/提议/测量分布。
- 可微性保证端到端梯度可回传。

## Optimization Objective

目标：

- 联合优化状态估计精度与模型拟合质量，在不依赖预定义分布族的前提下获得合法概率密度。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真与基准任务验证（具体任务与数据集名称未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 基于 vanilla 神经网络的可微粒子滤波
- Bootstrap 粒子滤波 / 预定义分布族方法

> 说明：论文在引言中明确了对照思路，但基线具体名称未在当前材料中逐一定位，此处不做推测。

## Metrics

评价指标：

- 状态估计精度（如 RMSE）
- 密度估计质量（似然）
- 模型适应性（复杂分布下的表现）

## Results

主要结果：

- 所提框架用归一化流构建三个模块，获得合法概率密度。
- 可自适应学习这些模块，不受预定义分布族限制。
- 给出了相应的理论推导。

> 说明：具体的估计精度与似然数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/其他/5LH9KB2X]] 实验章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出既有可微粒子滤波的核心缺陷：用 vanilla 神经网络无法做密度估计，因而受限于 bootstrap 框架或预定义分布族。
2. 提出用（条件）归一化流构建可微粒子滤波的动态模型、提议分布与测量模型。
3. 该设计同时保证合法概率密度与灵活的自适应学习能力。
4. 给出相应的理论推导。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 归一化流的「可逆 + 密度可精确计算」特性恰好补上了 vanilla 神经网络在密度估计上的短板。
- 把三个模块都换成归一化流，使整个滤波器摆脱对预定义分布族的依赖。

## My Evaluation

我的评价：

四星

创新程度：

中高

理由：

- 问题诊断准确（密度估计能力缺失），解法对症（归一化流）。
- 有理论推导支撑，不是纯调参工作。
- 但属方法组合创新：归一化流与粒子滤波均为既有技术，贡献在于结合方式与理论分析。

---

# 10. Limitation（不足）

论文不足：

1. 归一化流的表达能力与计算开销存在权衡（深层流推理慢）。
2. 量化收益需查阅实验章节。
3. 高维状态空间下归一化流的可扩展性需进一步验证。
4. 仿真/基准任务为主，真实复杂场景验证待补充。

未来可能改进：

- 研究更高效的流结构以适配实时滤波。
- 在高维状态空间（如视觉 SLAM）上验证。
- 与 UAV/ISAC 的实际感知任务结合做实测。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 粒子滤波的三个模块（动态、提议、测量）都可学习，但「能否算密度」决定了能否摆脱 bootstrap 框架。
- 归一化流的核心价值是「可逆变换 + 密度可精确计算」，这正是概率建模所需。
- 预定义分布族（如高斯）在多峰/重尾的真实场景下表达能力不足，是实际性能瓶颈。

## Connection With My Work

和我的研究/项目关系：

- 序贯状态估计可迁移到 UAV 目标跟踪与 ISAC 感知侧的滤波问题。
- 与 [[02vault/其他/OptiPMB 3D Multi-Object Tracking|OptiPMB 跟踪]] 形成对照：该文用 RFS/PMB 的模型化方法，本文用归一化流的学习化方法。
- 归一化流建模测量模型的思路可用于自己的非高斯观测建模。

## Possible Ideas

可能的新想法：

- 把该框架用于 UAV-ISAC 的感知状态估计（非高斯、时变观测）。
- 对比归一化流方法与 RFS/PMB 方法在同一跟踪任务上的表现。
- 研究轻量化流结构以满足机载实时性约束。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/其他/OptiPMB 3D Multi-Object Tracking|OptiPMB 跟踪]] — 同属状态估计/跟踪，该文用 RFS/PMB 模型化方法，本文用归一化流学习化方法

---

# 13. Summary Card（快速复习）

## Problem

> 现有可微粒子滤波用 vanilla 神经网络无法做密度估计，因而受限于 bootstrap 框架或预定义分布族。

## Method

> 用（条件）归一化流构建可微粒子滤波的动态模型、提议分布与测量模型，并给出理论推导。

## Result

> 获得合法概率密度，并可自适应学习三个模块而不受预定义分布族限制（具体精度见全文实验章节）。

## Importance

> 补上了可微粒子滤波在密度估计上的短板，使其适配更复杂的真实场景。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决可微粒子滤波因使用普通神经网络而无法做密度估计、受限于预定义分布族的问题。

Q:
核心方法是什么？

A:
用（条件）归一化流构建粒子滤波的动态模型、提议分布与测量模型。

Q:
最大贡献是什么？

A:
同时实现合法概率密度与不受分布族限制的自适应学习，并给出理论推导。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `5LH9KB2X`，PDF 附件 `1C8YZBM5`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/其他/5LH9KB2X]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 理论推导细节、实验任务名称与量化数值未在当前材料中定位，已在正文如实标注，未做推测。