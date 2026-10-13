---
title: "Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative ISAC in AAV Detection"
aliases:
  - 公平性资源分配
  - 网络化 ISAC 干扰管理
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - 资源分配
created: 2026-10-13
source: IEEE Transactions on Vehicular Technology, 2025
author: Ruotong Li, Qixun Zhang, Dingyou Ma, Kan Yu, Yuzhen Huang
year: 2025
journal: IEEE Transactions on Vehicular Technology

theme: 用公平性准则管理协作 ISAC 网络中的动态干扰，优先保障最弱链路
study_area: 通感一体化 / 网络化 ISAC / 干扰管理
methodology: 最大化最小雷达感知 SINR（max-min fairness）的目标指派与资源分配联合优化
core_variable: 雷达感知 SINR、多普勒频移、动态干扰、目标指派、检测性能
key_finding: 以最弱链路优先的公平性框架应对高速 AAV 引发的多普勒与波动干扰，缓解高干扰区的检测退化
relevance: 与本 Vault 的 UAV-ISAC 方向对口，且触及「干扰管理 + 公平性」这一工程要点

type: literature-note
zotero_key: "PVQ768TG"
pdf_key: "EN5GSRVN"
doi: "10.1109/TVT.2025.3525980"
collection: "ISAC"
note_path: "02vault/ISAC/Joint Target Assignment and Resource Allocation (Fairness).md"
fulltext_path: "03fulltext/ISAC/PVQ768TG.md"
status:
  - Reading
rating: 四星
---

# Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative ISAC in AAV Detection

---

# 📌 Basic Information（基本信息）

## Author
Ruotong Li, Qixun Zhang, Dingyou Ma, Kan Yu, Yuzhen Huang

## Year
2025

## Source
IEEE Transactions on Vehicular Technology｜DOI: 10.1109/TVT.2025.3525980

> Zotero 入口：zotero://select/library/items/PVQ768TG
> PDF 入口：zotero://open-pdf/library/items/EN5GSRVN
> 全文 Markdown：[[03fulltext/ISAC/PVQ768TG]]

## Research Area

- Networked ISAC / Cooperative Sensing
- Dynamic Interference Management
- Autonomous Aerial Vehicles (AAVs)
- Fairness-Based Resource Allocation

---

# 1. Abstract Summary（一句话总结）

> 该文针对协作 ISAC 系统中的动态干扰管理难题（聚焦复杂传播环境中高速移动的自主飞行器 AAV），指出快速运动引发显著多普勒频移与波动干扰、导致信号质量不均与高干扰区检测性能退化，提出以「最大化最小雷达感知 SINR」为准则的公平性资源分配框架，优先保障最弱链路。

---

# 2. Research Background（研究背景）

## 背景：

- ISAC 是 6G 的基础性技术；**网络化 ISAC**使多个分布式感知节点协同进行目标检测。

> 原文：
> "Integrated sensing and communication (ISAC) is a foundational technology for sixth-generation (6G) networks, with networked ISAC enabling multiple distributed sensing nodes to collaborate in target detection."

## Motivation（研究动机）

- 快速移动的 AAV 会引发**显著的多普勒频移**与**波动的干扰**。
- 这导致**信号质量不均**与**检测性能退化**，在**高干扰区域**尤为严重。

> 原文：
> "Rapid AAV motion induces significant Doppler shifts and fluctuating interference, leading to uneven signal quality and degraded detection performance, particularly in high-interference zones."

## Application Scenario（应用场景）

- 网络化 ISAC 的多节点协同目标检测
- 高速 AAV 的感知与通信保障
- 干扰分布不均的复杂传播环境

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在高速 AAV 引发多普勒与波动干扰的协作 ISAC 网络中，如何通过目标指派与资源分配保障各链路的检测性能（尤其最弱链路）？

核心问题：

- 动态干扰如何建模与管理？
- 为何采用公平性（max-min）准则而非总和最大化？
- 目标指派与资源分配如何联合优化？

---

# 4. Related Work（相关工作）

已有方法：

1. **总和性能最大化的资源分配**：可能牺牲最弱链路，导致部分区域检测失效。
2. **静态干扰管理**：未考虑 AAV 快速移动带来的时变多普勒与波动干扰。
3. **分离的目标指派与资源分配**：忽略二者耦合。

现有不足：

- 缺少针对动态干扰的公平性资源分配。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出**基于公平性（fairness-based）的资源分配框架**，**优先保障最弱链路**。
- 具体准则：**最大化最小雷达感知 SINR**（maximizing the minimum radar sensing SINR）——即 max-min fairness。
- 构造**联合优化**问题（目标指派 + 资源分配）。

> 原文：
> "We propose a fairness-based resource allocation framework that prioritizes the weakest links by maximizing the minimum radar sensing signal-to-interference-plus-noise ratio (SINR). We formulate a joint optimi"

## Model / Framework

系统模型：

- **网络**：多个分布式感知节点协作（networked ISAC）
- **目标**：快速移动的自主飞行器（AAVs）
- **损伤**：多普勒频移 + 波动干扰
- **优化变量**：目标指派（target assignment）+ 资源分配
- **准则**：max-min 雷达感知 SINR

## Algorithm / Technique

采用：

- 公平性准则（max-min fairness）
- 目标指派与资源分配联合优化
- 动态干扰建模
- 多普勒效应处理

## Key Steps

1. 建立网络化 ISAC 的多节点协同检测模型。
2. 建模 AAV 快速运动带来的多普勒频移与动态干扰。
3. 以 max-min 雷达感知 SINR 为准则构造公平性目标。
4. 联合优化目标指派与资源分配。
5. 通过仿真验证最弱链路性能的改善。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标函数**：最大化**最小**雷达感知 SINR（max-min），而非 SINR 之和。
- **优化变量**：目标指派、资源分配。
- **约束**：分布式感知节点的资源与干扰条件。

> 说明：SINR 的具体表达、多普勒与干扰的建模方式，以及联合问题的求解方法见 [[03fulltext/ISAC/PVQ768TG]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 各链路的雷达感知 SINR 可计算并作为公平性分配依据。
- 目标指派与资源可联合调度。
- 最弱链路的性能决定了系统整体的检测可靠性（短板效应）。

## Optimization Objective

目标：

- 通过提升最弱链路的 SINR，缓解高干扰区的检测退化，使系统检测性能更均衡。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体节点数、AAV 速度、干扰分布与信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 最小雷达感知 SINR（最弱链路）
- 检测性能
- 信号质量均衡性

## Results

主要结果：

- 所提公平性框架通过优先保障最弱链路，缓解了高干扰区的检测性能退化。

> 说明：具体的 SINR 改善与检测性能数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/PVQ768TG]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出网络化 ISAC 中动态干扰管理的关键挑战。
2. 明确高速 AAV 运动带来多普勒频移与波动干扰，导致信号质量不均与高干扰区检测退化。
3. 提出基于公平性的资源分配框架，以 max-min 雷达感知 SINR 为准则优先保障最弱链路。
4. 联合优化目标指派与资源分配。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 检测可靠性由最弱链路决定（短板效应），故公平性比总和最大化更重要。
- 动态干扰必须与时变性（多普勒）一起建模，静态方案无效。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- max-min fairness 是有意义的准则选择，契合检测任务的短板效应。
- 但该方法在通信领域较为成熟，本文的贡献主要在将其用于网络化 ISAC 的干扰管理场景。
- 与本 Vault [[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]] 的 max-min rate 目标思路一致，可相互印证。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅仿真章节。
2. max-min 准则可能牺牲系统整体吞吐（公平性与效率的经典权衡）。
3. 仿真验证，无实测。

未来可能改进：

- 研究公平性与效率的折中（如 α-fairness）。
- 在真实网络化 ISAC 平台上验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **检测任务适合 max-min 准则**：漏检一个目标的代价远高于某个目标检测得更准，短板效应显著。
- 多普勒频移是高速移动平台的核心损伤，会与干扰叠加放大性能退化。
- 公平性与效率存在经典权衡，选择准则时要明确业务诉求。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向对口。
- 与 [[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]] 思路一致（均用 max-min 类目标），可相互印证该准则在 UAV 场景的适用性。
- 多普勒建模可用于自己的 UAV 信道仿真。

## Possible Ideas

可能的新想法：

- 对比 max-min 与加权和在多目标 ISAC 检测中的实际差异。
- 把多普勒效应纳入本 Vault 其他 UAV-ISAC 工作的信道模型。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]] — 同样采用 max-min 类目标（max-min rate）

---

# 13. Summary Card（快速复习）

## Problem

> 网络化 ISAC 中高速 AAV 引发多普勒与波动干扰，导致信号质量不均、高干扰区检测退化。

## Method

> 基于公平性的资源分配框架：以 max-min 雷达感知 SINR 为准则，联合优化目标指派与资源分配。

## Result

> 优先保障最弱链路，缓解高干扰区检测退化（具体数值见全文仿真章节）。

## Importance

> 把公平性准则引入网络化 ISAC 的干扰管理，契合检测任务的短板效应。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决网络化 ISAC 中高速 AAV 引发多普勒与波动干扰、导致高干扰区检测退化的问题。

Q:
核心方法是什么？

A:
基于公平性的资源分配：以 max-min 雷达感知 SINR 为准则，联合优化目标指派与资源分配。

Q:
最大贡献是什么？

A:
把 max-min 公平性引入网络化 ISAC 干扰管理，优先保障最弱链路的检测性能。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `PVQ768TG`，PDF 附件 `EN5GSRVN`。
- PDF 经 pypdf 提取全文（74670 字符），原文引用均取自全文 Markdown [[03fulltext/ISAC/PVQ768TG]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- SINR 表达、多普勒/干扰建模与量化数值未在当前材料中逐项定位，已在正文如实标注，未做推测。