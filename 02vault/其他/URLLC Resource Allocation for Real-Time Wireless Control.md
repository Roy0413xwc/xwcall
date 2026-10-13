---
title: "Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems"
aliases:
  - URLLC 控制协同设计
  - 实时无线控制资源分配
tags:
  - literature-note
  - reading-note
  - URLLC
  - 无线控制
  - 资源分配
created: 2026-10-13
source: IEEE Transactions on Vehicular Technology, 2019
author: Bo Chang, Lei Zhang, Liying Li, Guodong Zhao, Zhi Chen
year: 2019
journal: IEEE Transactions on Vehicular Technology

theme: 把 URLLC 通信资源与控制子系统性能联合建模为协同设计问题
study_area: URLLC / 实时无线控制 / 控制通信协同设计
methodology: 基于上行传输，联合优化 URLLC 的带宽与发射功率分配以及控制收敛速率
core_variable: 通信资源消耗、控制收敛速率、带宽分配、发射功率分配
key_finding: URLLC 的资源消耗与控制子系统性能相互依赖，必须联合建模为协同设计问题
relevance: 与本 Vault 的 UAV 控制方向（如 [[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]]）思路一脉相承

type: literature-note
zotero_key: "9C2VZXD7"
pdf_key: "ZNFJ6BKL"
doi: "10.1109/TVT.2019.2930153"
collection: "其他"
note_path: "02vault/其他/URLLC Resource Allocation for Real-Time Wireless Control.md"
fulltext_path: "03fulltext/其他/9C2VZXD7.md"
status:
  - Reading
rating: 四星
---

# Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems

---

# 📌 Basic Information（基本信息）

## Author
Bo Chang, Lei Zhang, Liying Li, Guodong Zhao, Zhi Chen

## Year
2019

## Source
IEEE Transactions on Vehicular Technology｜DOI: 10.1109/TVT.2019.2930153

> Zotero 入口：zotero://select/library/items/9C2VZXD7
> PDF 入口：zotero://open-pdf/library/items/ZNFJ6BKL
> 全文 Markdown：[[03fulltext/其他/9C2VZXD7]]

## Research Area

- Ultra-Reliable Low-Latency Communication (URLLC)
- Real-Time Wireless Control Systems
- Control-Communication Co-Design
- Resource Allocation

---

# 1. Abstract Summary（一句话总结）

> 该文以 URLLC 作为实时无线控制系统的使能技术，指出 URLLC 的通信资源消耗与控制子系统性能相互依赖，因而必须把二者整合为协同设计问题；基于上行传输，研究通过优化 URLLC 的带宽与发射功率分配以及控制收敛速率来进行资源分配。

---

# 2. Research Background（研究背景）

## 背景：

- URLLC 是 5G 蜂窝网络的三大主要场景之一，可作为**实时无线控制系统**的使能技术。

> 原文：
> "As one of the three main scenarios in the fifth-generation (5G) cellular networks, ultra-reliable and low-latency communication (URLLC) can be served as an enabler for real-time wireless control systems."

## Motivation（研究动机）

- 在实时无线控制系统中，**URLLC 的通信资源消耗**与**控制子系统的性能**是**相互依赖**的。
- 为优化整体系统性能，必须把二者**整合为一个协同设计（co-design）问题**。

> 原文：
> "In such a system, the communication resource consumption in URLLC and the control subsystem performance are mutually dependent. To optimize the overall system performance, it is critical to integrate URLLC and control subsystems together by formulating a co-design problem."

## Application Scenario（应用场景）

- 工业闭环控制（如工厂自动化）
- 需 URLLC 支撑的实时无线控制系统
- 通信资源受限但控制性能要求高的场景

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在上行传输下，如何通过联合优化 URLLC 的带宽与功率分配以及控制收敛速率，实现通信与控制的最优协同？

核心问题：

- 通信资源消耗与控制性能如何相互依赖？
- 协同设计问题如何形式化？
- 带宽与功率如何在控制需求下最优分配？

---

# 4. Related Work（相关工作）

已有方法：

1. **通信为中心的 URLLC 资源分配**：只优化通信指标，忽略控制性能。
2. **控制为中心的设计**：假设通信理想，不考虑资源约束。
3. **分离优化通信与控制**：无法获得协同增益。

现有不足：

- 未把通信与控制作为耦合系统联合优化。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 基于**上行传输**，研究实时无线控制系统中的 URLLC 资源分配问题。
- 通过**优化 URLLC 的带宽与发射功率分配**以及**控制收敛速率（control convergence rate）**来求解该问题。

> 原文：
> "based on uplink transmission, we study the resource allocation problem for URLLC in real-time wireless control systems. The problem is conducted by optimizing bandwidth and transmission power allocation in URLLC and control convergence rate sub"

## Model / Framework

系统模型：

- **链路方向**：上行传输
- **通信侧**：URLLC 的带宽分配、发射功率分配
- **控制侧**：控制收敛速率（反映控制子系统性能）
- **耦合关系**：通信资源消耗 ⇄ 控制性能

## Algorithm / Technique

采用：

- 控制-通信协同设计（co-design）建模
- 带宽与功率分配优化
- 控制收敛速率建模

## Key Steps

1. 建立上行 URLLC 的实时无线控制系统模型。
2. 明确通信资源消耗与控制子系统性能的相互依赖关系。
3. 形式化为协同设计问题。
4. 联合优化带宽分配、发射功率分配与控制收敛速率。
5. 通过仿真验证协同增益。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **优化变量**：URLLC 带宽分配、发射功率分配、控制收敛速率
- **耦合**：通信资源消耗与控制性能之间的相互依赖
- **求解**：协同设计问题的联合优化

> 说明：控制收敛速率的定义、URLLC 的可靠性/时延模型与联合优化的具体求解方法见 [[03fulltext/其他/9C2VZXD7]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 上行链路是控制信息的主要传输方向。
- 控制子系统性能可由收敛速率刻画。
- 通信资源（带宽、功率）有限且需分配。

## Optimization Objective

目标：

- 在资源约束下同时优化通信效率与控制性能，获得系统整体最优。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体控制对象、系统数量、带宽与功率约束未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 控制收敛速率
- 通信资源消耗（带宽、功率）
- 系统整体性能

## Results

主要结果：

- 通过协同设计（联合优化带宽、功率与控制收敛速率）实现了系统整体性能的优化。

> 说明：具体的性能改善数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/其他/9C2VZXD7]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出 URLLC 可作为实时无线控制系统的使能技术。
2. 明确通信资源消耗与控制子系统性能相互依赖这一核心耦合。
3. 主张将二者整合为协同设计问题（而非分离优化）。
4. 基于上行传输，联合优化带宽分配、发射功率分配与控制收敛速率。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 控制与通信不是「先通信达标、再控制设计」的串联关系，而是必须联合优化的耦合关系。
- 控制收敛速率是连接通信质量与控制性能的合适桥梁指标。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 「控制-通信协同设计」的提法清晰，且用收敛速率作为桥梁指标是合理的建模选择。
- 该思路与本 Vault [[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]] 一脉相承（后者也联合优化控制策略与通信资源），可相互印证。
- 本文为 2019 年工作，相对早期，方法细节在当前材料中亦不完整。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅仿真章节。
2. 仿真验证，无实测。
3. 单控制对象/小规模场景的设定，大规模扩展未讨论。

未来可能改进：

- 在真实工业控制系统中验证。
- 扩展到多控制回路协同。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **控制与通信是双向耦合的**：通信质量影响控制性能，而控制需求又决定通信资源该怎么分。
- 控制收敛速率是一个好的「桥梁指标」——它既是控制性能的度量，又能与通信的时延/可靠性挂钩。
- 串联设计（先通信后控制）会损失协同增益，协同设计才有整体最优。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV 控制方向一脉相承：[[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]] 同样联合优化控制策略与通信资源（功率、轨迹）。
- 协同设计的思路可用于自己的 UAV 控制-通信联合问题。

## Possible Ideas

可能的新想法：

- 把控制收敛速率作为 UAV 控制-通信联合优化的桥梁指标。
- 对比本文的 URLLC 协同设计与 [[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]] 的 MPC 协同设计。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]] — 同为控制-通信协同设计，该文用 MPC 并面向低空 UAV
- [[02vault/UAV/Control-Based Beamforming and Trajectory for UAV-ISAC|控制导向 UAV-ISAC]] — 同把控制/动力学纳入通信设计

---

# 13. Summary Card（快速复习）

## Problem

> 实时无线控制系统中，URLLC 通信资源消耗与控制子系统性能相互依赖，分离优化无法获得整体最优。

## Method

> 把二者整合为协同设计问题，基于上行传输联合优化带宽分配、发射功率分配与控制收敛速率。

## Result

> 实现通信与控制的最优协同（具体数值见全文仿真章节）。

## Importance

> 明确了控制-通信的双向耦合关系，为 URLLC 支撑的实时控制系统提供了协同设计范式。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决实时无线控制系统中 URLLC 通信资源与控制性能相互依赖、分离优化无法整体最优的问题。

Q:
核心方法是什么？

A:
协同设计：基于上行传输，联合优化带宽分配、发射功率分配与控制收敛速率。

Q:
最大贡献是什么？

A:
提出把 URLLC 与控制子系统整合为协同设计问题，用控制收敛速率作为桥梁指标。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `9C2VZXD7`，PDF 附件 `ZNFJ6BKL`。
- PDF 经 pypdf 提取全文（57226 字符），原文引用均取自全文 Markdown [[03fulltext/其他/9C2VZXD7]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 控制收敛速率的定义、URLLC 可靠性/时延模型与量化数值未在当前材料中逐项定位，已在正文如实标注，未做推测。