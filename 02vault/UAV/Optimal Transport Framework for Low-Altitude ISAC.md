---
title: "Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource Allocation for Cooperative Communication and Non-Cooperative Localization"
aliases:
  - 最优传输低空网络
  - 双功能低空 ISAC
tags:
  - literature-note
  - reading-note
  - UAV
  - ISAC
  - 资源分配
created: 2026-10-13
source: IEEE Transactions on Communications, 2026
author: Yufeng Zheng, Lixin Li, Wensheng Lin, Wei Liang, Qinghe Du, Zhu Han
year: 2026
journal: IEEE Transactions on Communications

theme: 低空网络中基站同时服务授权 UAV 并定位非合作 UAV 的双功能资源管理
study_area: 通感一体化 / 低空网络 / 资源分配
methodology: 建立通信速率与感知精度的关系模型 + 小区关联与功率分配联合优化
core_variable: 系统平均和速率、定位服务质量（QoS）、小区关联、功率分配
key_finding: 建立刻画通信速率与感知精度关系的信道模型，最大化二者加权和
relevance: 与本 Vault 的 UAV-ISAC 方向对口，与 [[02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV|AIBOT 资源分配]] 方法相近

type: literature-note
zotero_key: "7GXUGA2S"
pdf_key: "PT5TIB2R"
doi: "10.1109/TCOMM.2025.3642742"
collection: "UAV"
note_path: "02vault/UAV/Optimal Transport Framework for Low-Altitude ISAC.md"
fulltext_path: "03fulltext/UAV/7GXUGA2S.md"
status:
  - Reading
rating: 四星
---

# Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource Allocation for Cooperative Communication and Non-Cooperative Localization

---

# 📌 Basic Information（基本信息）

## Author
Yufeng Zheng, Lixin Li, Wensheng Lin, Wei Liang, Qinghe Du, Zhu Han

## Year
2026

## Source
IEEE Transactions on Communications｜DOI: 10.1109/TCOMM.2025.3642742

> Zotero 入口：zotero://select/library/items/7GXUGA2S
> PDF 入口：zotero://open-pdf/library/items/PT5TIB2R
> 全文 Markdown：[[03fulltext/UAV/7GXUGA2S]]

## Research Area

- ISAC-Enabled Low-Altitude Networks
- Cooperative Communications + Unauthorized Intrusion Detection
- Cell Association and Power Allocation
- Dual-Functional Framework

---

# 1. Abstract Summary（一句话总结）

> 该文研究 ISAC 使能低空网络中的小区关联与功率分配联合优化，提出双功能框架：地面基站同时为授权 UAV 提供通信服务、并定位非合作 UAV 以实现避撞；建立刻画通信速率与感知精度关系的信道模型，最大化系统平均和速率与定位 QoS 的加权和。

---

# 2. Research Background（研究背景）

## 背景：

- 低空空域中无人机数量的增长，需要支持**协作通信**与**未授权入侵检测**的复杂资源管理。

> 原文：
> "The proliferation of unmanned aerial vehicles (UAVs) in low-altitude airspace necessitates sophisticated resource management supporting both cooperative communications and unauthorized intrusion detection."

## Motivation（研究动机）

- 授权 UAV 需要通信服务，非授权 UAV 需要被定位（用于避撞）——两类需求并存。
- 需在有限的无线资源下同时满足，且通信速率与感知精度存在耦合关系。

## Application Scenario（应用场景）

- 低空网络的通信服务 + 入侵检测
- 授权 UAV 与非合作 UAV 共存的空域管理
- 无人机避撞场景

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在低空 ISAC 网络中，如何联合优化小区关联与功率分配，以平衡授权 UAV 的通信服务与非合作 UAV 的定位需求？

核心问题：

- 通信速率与感知精度的关系如何建模？
- 小区关联与功率分配如何联合优化？
- 两类 UAV（合作/非合作）的需求如何权衡？
---

# 4. Related Work（相关工作）

已有方法：

1. **仅服务授权 UAV 的通信网络**：无入侵检测能力。
2. **独立的监测系统**：不共享通信网资源。
3. **分离优化小区关联与功率分配**：忽略二者耦合。

现有不足：

- 缺少同时支持协作通信与入侵检测的统一资源管理框架。
- 未显式建模通信速率与感知精度的关系。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出**双功能框架**：地面基站（GBS）**同时**为授权 UAV 提供通信服务，并定位非合作 UAV 以实现避撞。
- 建立**刻画通信速率与感知精度关系**的信道模型。
- 构造优化问题，最大化**系统平均和速率**与**定位 QoS**的加权和。
- 联合优化**小区关联**与**功率分配**。

> 原文：
> "We propose a novel dual-function framework where ground base stations simultaneously provide communication services to authorized UAVs and localize non-cooperative UAVs for collision avoidance. We establish a channel model capturing the relationship between communication rate and sensing accuracy, formulating an optimization problem that maximizes the weighted sum of system average sum rate and localization quality"

## Model / Framework

系统模型：

- **基础设施**：地面基站（GBS）
- **UAV 类型**：授权 UAV（需通信服务）+ 非合作 UAV（需被定位，用于避撞）
- **优化变量**：小区关联（cell association）、功率分配（power allocation）
- **目标**：系统平均和速率 + 定位 QoS 的加权和

## Algorithm / Technique

采用：

- 双功能框架建模
- 通信速率—感知精度关系建模
- 小区关联与功率分配联合优化
- 加权和标量化

## Key Steps

1. 建立低空 ISAC 网络模型，区分授权与非合作 UAV。
2. 建立刻画通信速率与感知精度关系的信道模型。
3. 构造最大化「平均和速率 + 定位 QoS」加权和的优化问题。
4. 联合优化小区关联与功率分配。
5. 通过仿真验证。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **信道模型**：显式刻画通信速率与感知精度之间的关系（二者通过无线资源耦合）。
- **目标**：最大化系统平均和速率（average sum rate）与定位 QoS（localization quality of service）的加权和。
- **优化变量**：小区关联、功率分配。

> 说明：速率—精度关系的具体表达、定位 QoS 的量化方式与功率约束见 [[03fulltext/UAV/7GXUGA2S]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 授权 UAV 可被关联到基站并分配通信功率。
- 非合作 UAV 不主动配合，但仍可通过回波被定位。
- 通信速率与感知精度之间存在可建模的折中关系。

## Optimization Objective

目标：

- 在资源约束下平衡通信服务与定位需求，最大化二者加权和。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体基站数、UAV 数量、空域尺度未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 系统平均和速率
- 定位 QoS（定位精度）

## Results

主要结果：

- 所提双功能框架可在同一网络中同时提供通信服务与入侵定位。
- 通过联合优化小区关联与功率分配实现了两类需求的平衡。

> 说明：具体的速率与定位精度数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/7GXUGA2S]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出低空空域需同时支持协作通信与未授权入侵检测。
2. 提出双功能框架：GBS 同时服务授权 UAV 并定位非合作 UAV。
3. 建立刻画通信速率与感知精度关系的信道模型。
4. 构造最大化「平均和速率 + 定位 QoS」加权和的优化问题，并联合优化小区关联与功率分配。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 把「服务授权 UAV」与「监管非合作 UAV」统一到同一基站的同一资源池中。
- 显式建模速率—精度关系，使权衡可被优化而非仅被观察。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 场景设定（授权/非合作 UAV 并存）贴近低空管理现实。
- 但方法（加权和 + 联合优化）属常规路径，且本 Vault 已有 [[02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV|AIBOT 资源分配]] 采用相近思路，新颖性相对有限。

---

# 10. Limitation（不足）

论文不足：

1. 加权和的权重设定缺乏依据（同 [[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization|双目标 ISAC]] 所批评）。
2. 仿真验证，无实测。
3. 量化收益需查阅仿真章节。

未来可能改进：

- 改用双目标建模以避免权重偏置。
- 在真实低空场景验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 低空网络中「合作用户」与「非合作目标」并存，是 ISAC 的典型适用场景。
- 把速率与精度的关系显式建模为信道模型的一部分，使权衡可被优化。
- 加权和虽常用，但权重缺乏依据是被批评的软肋——可考虑双目标替代。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向对口。
- 与 [[02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV|AIBOT 资源分配]] 方法相近，可作对比研究。
- 与 [[02vault/UAV/ISAC Enabled Cooperative Detection for UAV|ISAC 协同探测]] 场景相邻：该文重监管机制（电子围栏），本文重资源分配优化。

## Possible Ideas

可能的新想法：

- 把本文的加权和改为双目标，检验是否真能避免偏置。
- 对比本文与 AIBOT 方法在同一低空场景下的表现。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV|AIBOT 资源分配]] — 同属 ISAC 资源分配，方法相近
- [[02vault/UAV/ISAC Enabled Cooperative Detection for UAV|ISAC 协同探测]] — 同为低空监管，该文重机制，本文重优化

---

# 13. Summary Card（快速复习）

## Problem

> 低空空域需同时支持授权 UAV 的协作通信与非合作 UAV 的入侵检测，资源管理复杂。

## Method

> 双功能框架：GBS 同时服务授权 UAV 并定位非合作 UAV；建立速率—精度关系模型；联合优化小区关联与功率分配。

## Result

> 实现通信服务与定位需求的平衡（具体数值见全文仿真章节）。

## Importance

> 把服务与监管统一到同一资源池，为低空网络的双功能资源管理提供了框架。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决低空网络需同时支持授权 UAV 通信与非合作 UAV 入侵检测的资源管理问题。

Q:
核心方法是什么？

A:
双功能框架 + 速率—精度关系建模 + 小区关联与功率分配联合优化（加权和目标）。

Q:
最大贡献是什么？

A:
把服务与监管统一到同一基站资源池，并显式建模通信速率与感知精度的关系。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `7GXUGA2S`，PDF 附件 `PT5TIB2R`。
- PDF 经 pypdf 提取全文（84084 字符），原文引用均取自全文 Markdown [[03fulltext/UAV/7GXUGA2S]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 速率—精度关系表达、定位 QoS 量化与数值结果未在当前材料中逐项定位，已在正文如实标注，未做推测。