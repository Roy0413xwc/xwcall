---
title: "LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in Near-Field ISAC Systems"
aliases:
  - LLM 近场预测波束成形
  - LNN 波束预测
tags:
  - literature-note
  - reading-note
  - ISAC
  - 近场通信
  - LLM
created: 2026-10-13
source: IEEE Journal on Selected Areas in Communications, 2026
author: Hongjia Huang, Weijie Yuan, Chang Liu, Liang Liu, Fan Liu, Wei Xiang, Derrick Wing Kwan Ng
year: 2026
journal: IEEE Journal on Selected Areas in Communications

theme: 用大语言模型神经网络（LNN）利用历史 CSI 实现近场 V2I 系统的预测波束成形
study_area: 通感一体化 / 近场通信 / 预测波束成形
methodology: 基于 LLM 的神经网络（LNN）+ 历史 CSI 序列预测 + 角度与距离 CRB 及可达和速率分析
core_variable: 角度与距离估计的 CRB、可达和速率、预测波束精度、车辆跟踪性能
key_finding: 近场波形设计需联合考虑距离与角度两个维度；用 LNN 挖掘历史 CSI 可做出准确的未来波束决策
relevance: 与本 Vault 的 ISAC 方向对口，且是 LLM 方法进入物理层波束预测的代表工作

type: literature-note
zotero_key: "YLGH28E2"
pdf_key: "3HTHUFEE"
doi: "10.1109/JSAC.2025.3643394"
collection: "ISAC"
note_path: "02vault/ISAC/LLM in V2I Predictive Beamforming.md"
fulltext_path: "03fulltext/ISAC/YLGH28E2.md"
status:
  - Reading
rating: 五星
---

# LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in Near-Field ISAC Systems

---

# 📌 Basic Information（基本信息）

## Author
Hongjia Huang, Weijie Yuan, Chang Liu, Liang Liu, Fan Liu, Wei Xiang, Derrick Wing Kwan Ng

## Year
2026

## Source
IEEE Journal on Selected Areas in Communications｜DOI: 10.1109/JSAC.2025.3643394

> Zotero 入口：zotero://select/library/items/YLGH28E2
> PDF 入口：zotero://open-pdf/library/items/3HTHUFEE
> 全文 Markdown：[[03fulltext/ISAC/YLGH28E2]]

## Research Area

- Near-Field ISAC
- Vehicle-to-Infrastructure (V2I)
- Predictive Beamforming
- Large Language Model-based Neural Network (LNN)

---

# 1. Abstract Summary（一句话总结）

> 该文研究近场 ISAC 车联网（V2I）系统中车辆跟踪的预测波束成形设计：近场场景下波形设计需联合考虑距离与角度两个维度，给传统波束成形与跟踪带来新挑战；为此提出基于大语言模型神经网络（LNN）的预测波束成形框架，利用历史 CSI 做出准确的未来波束决策，并分析角度与距离估计的 CRB 及可达和速率。

---

# 2. Research Background（研究背景）

## 背景：

- 在基于 ISAC 的**近场**车联网（V2I）系统中，对车辆进行跟踪需要设计**预测波束成形**（predictive beamforming）。

## Motivation（研究动机）

- 近场场景下的波形设计要求**联合考虑距离（range）与角度（angle）两个维度**，这对传统的波束成形与跟踪策略提出了新挑战。

> 原文：
> "The waveform design in near-field scenarios requires the joint consideration of both range and angle dimensions, posing new challenges to conventional beamforming and tracking strategies."

## Application Scenario（应用场景）

- 近场 ISAC 车联网（V2I）的车辆跟踪
- 需利用历史 CSI 做前瞻性波束决策的高移动场景
- 大规模天线/高频段下的近场通信感知

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在近场 V2I 系统中，如何利用历史 CSI 设计预测波束成形，以在同时考虑距离与角度维度的条件下准确跟踪车辆？

核心问题：

- 近场下距离维度为何不能忽略（与远场的区别）？
- 如何从历史 CSI 中预测未来波束？
- 预测波束的性能界（CRB、和速率）如何刻画？

---

# 4. Related Work（相关工作）

已有方法：

1. **远场假设下的波束跟踪**：只考虑角度维度，近场下失效。
2. **基于模型的预测（如卡尔曼滤波）**：依赖精确的运动模型假设。
3. **常规 DNN 预测方法**：时序建模能力有限，难以充分挖掘历史 CSI 的长程依赖。

现有不足：

- 未联合考虑近场的距离与角度双维度。
- 历史 CSI 的时序价值未被充分挖掘。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出**基于大语言模型（LLM）的神经网络（LNN）**的预测波束成形框架。
- 利用**历史信道状态信息（CSI）**来促成准确的**未来波束成形决策**。

> 原文：
> "we propose a predictive beamforming framework leveraging a large language model (LLM)-based neural network (LNN), which exploits historical channel state information (CSI) to facilitate accurate future beamforming decisions."

## Model / Framework

系统模型：

- **场景**：近场 ISAC 车联网（V2I），基站跟踪车辆
- **双维度**：距离（range）+ 角度（angle），需联合设计波形
- **输入**：历史 CSI 序列
- **输出**：未来的波束成形决策
- **网络**：LLM 基础的神经网络（LNN）

## Algorithm / Technique

采用：

- 基于 LLM 的神经网络（LNN）
- 历史 CSI 序列建模
- 预测波束成形（predictive beamforming）
- 角度与距离估计的 CRB 分析
- 可达和速率分析

## Key Steps

1. 建立近场 ISAC-V2I 的车辆跟踪模型，明确距离与角度双维度需求。
2. 收集并利用历史 CSI 作为预测依据。
3. 设计 LNN 网络，从历史 CSI 学习时序规律并预测未来波束。
4. 推导角度与距离估计的 Cramér-Rao 界（CRB）作为性能界。
5. 分析可达和速率，评估通信性能。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **近场特性**：波前为球面（而非远场的平面波），故需同时估计目标的**距离与角度**。
- **性能界**：分别推导**角度估计 CRB**与**距离估计 CRB**
- **通信性能**：可达和速率（achievable sum-rate）
- **预测目标**：由历史 CSI 序列预测未来时刻的波束成形向量

> 说明：近场信道模型、CRB 的推导过程与 LNN 的具体结构见 [[03fulltext/ISAC/YLGH28E2]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 车辆运动具有可被历史 CSI 反映的规律性（可预测性）。
- 近场效应显著，距离维度不可忽略（大规模天线/高频段）。
- LNN 能有效建模 CSI 序列的长程时序依赖。

## Optimization Objective

目标：

- 在近场双维度约束下实现准确的车辆跟踪与波束预测，同时维持良好的通信和速率。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体载频、天线数、车辆速度与信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 角度估计 CRB
- 距离估计 CRB
- 可达和速率
- 车辆跟踪精度

## Results

主要结果：

- 所提 LNN 框架可利用历史 CSI 做出准确的未来波束决策。
- 给出了角度与距离估计的 CRB 及可达和速率的理论刻画。

> 说明：具体的 CRB 数值、和速率与对比增益未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/YLGH28E2]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出近场 ISAC-V2I 波形设计需联合考虑距离与角度双维度，这对传统方法构成新挑战。
2. 提出基于 LLM 的神经网络（LNN）的预测波束成形框架。
3. 利用历史 CSI 实现准确的未来波束决策。
4. 给出角度与距离估计的 CRB 及可达和速率的分析。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 近场的距离维度是相对远场的本质区别，必须纳入波形与波束设计。
- LLM 类网络的时序建模能力适合挖掘历史 CSI 的长程依赖，是预测波束的天然选择。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 把 LLM 引入物理层波束预测是有前瞻性的尝试，且与 [[02vault/LLM/Attention Is All You Need|Transformer]] 的时序建模能力一脉相承。
- 近场双维度（距离+角度）的强调符合当前大规模天线/高频段的技术趋势。
- 但 LLM 的计算开销在实时物理层部署中是个现实问题，论文未充分讨论。

---

# 10. Limitation（不足）

论文不足：

1. LLM 类网络的推理开销较大，实时性需评估（物理层对时延敏感）。
2. 量化收益需查阅仿真章节。
3. 仿真验证，无实测数据。
4. 历史 CSI 的长度与预测视野的权衡未详细说明。

未来可能改进：

- 研究轻量化 LNN 以满足物理层时延约束。
- 在真实 V2I 场景验证。
- 分析历史窗口长度与预测精度的关系。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **近场 vs 远场的本质区别**：近场波前是球面，目标位置由「距离+角度」共同决定，远场只需角度——这改变了波形设计的自由度结构。
- 预测波束成形的核心是把「估计-跟踪-波束」串成时序问题，历史 CSI 是宝贵的信息源。
- LLM/Transformer 类网络的时序建模能力可迁移到物理层信号处理，但需权衡计算开销。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 ISAC 方向对口。
- 与 [[02vault/LLM/Attention Is All You Need|Transformer 开山之作]] 形成呼应：自注意力机制从 NLP 走向物理层波束预测。
- 与 [[02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning|Mem-DSACM]] 思路相近：都用电网络的时序记忆做预测性决策。

## Possible Ideas

可能的新想法：

- 把 LNN 预测波束用于 UAV 空地链路（高移动性 + 可能近场）。
- 对比 LNN 与传统卡尔曼/扩展卡尔曼预测的精度与开销。
- 研究轻量化方案使 LLM 类方法满足物理层时延约束。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/LLM/Attention Is All You Need|Transformer 开山之作]] — 自注意力的本源，本文将其时序建模能力用于物理层波束预测
- [[02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning|Mem-DSACM]] — 同样用记忆/时序建模做预测性决策，该文面向 UAV 轨迹

---

# 13. Summary Card（快速复习）

## Problem

> 近场 ISAC-V2I 中波形设计需联合考虑距离与角度双维度，传统波束跟踪策略失效。

## Method

> 提出基于 LLM 的神经网络（LNN）预测波束成形框架，利用历史 CSI 做未来波束决策，并分析角度/距离 CRB 与可达和速率。

## Result

> 实现准确的未来波束决策（具体 CRB 与和速率数值见全文仿真章节）。

## Importance

> 把 LLM 的时序建模能力引入近场 ISAC 物理层波束预测，是跨学科方法迁移的代表。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决近场 ISAC-V2I 中需联合考虑距离与角度双维度、传统波束跟踪失效的问题。

Q:
核心方法是什么？

A:
基于 LLM 的神经网络（LNN）预测波束成形框架，利用历史 CSI 做未来波束决策。

Q:
最大贡献是什么？

A:
把 LLM 引入近场 ISAC 波束预测，并给出角度与距离 CRB 及和速率的理论刻画。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `YLGH28E2`，PDF 附件 `3HTHUFEE`。
- PDF 经 pypdf 提取全文（94198 字符），原文引用均取自全文 Markdown [[03fulltext/ISAC/YLGH28E2]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 近场信道模型、CRB 推导与 LNN 结构细节未在当前材料中逐项定位，已在正文如实标注，未做推测。