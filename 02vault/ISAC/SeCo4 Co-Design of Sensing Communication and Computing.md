---
title: "SeCo4: Co-Design of Sensing, Communication, and Computing for Intelligent Control in Industrial Cyber-Physical Systems"
aliases:
  - SeCo4
  - 通感算协同设计
tags:
  - literature-note
  - reading-note
  - ISAC
  - 工业物联网
  - 云雾自动化
created: 2026-10-13
source: IEEE Journal on Selected Areas in Communications, 2025
author: Qinqin Tang, Yutian Yang, Jiayi Cui, Renchao Xie, Tao Huang, Tianjiao Chen, Ran Zhang, Zehui Xiong
year: 2025
journal: IEEE Journal on Selected Areas in Communications

theme: 面向工业信息物理系统的感知、通信与计算协同设计
study_area: 通感算一体化 / 工业 CPS / 云雾自动化
methodology: SeCo4 协同设计框架（应对刚性采样、通信配置僵化、云雾协同不足、感通算割裂四类挑战）
core_variable: 传感器采样灵活度、通信配置、云雾资源协同、感通算集成度
key_finding: 针对云雾自动化（CFA）的四类挑战提出 SeCo4 感知-通信-计算协同设计框架
relevance: 与本 Vault 的 ISAC 方向相关，且把「计算」纳入一体化——是 ISAC 向通感算演进的代表

type: literature-note
zotero_key: "RFIP7ECI"
pdf_key: "4DDGZBQW"
doi: "10.1109/JSAC.2025.3574623"
collection: "ISAC"
note_path: "02vault/ISAC/SeCo4 Co-Design of Sensing Communication and Computing.md"
fulltext_path: "03fulltext/ISAC/RFIP7ECI.md"
status:
  - Reading
rating: 四星
---

# SeCo4: Co-Design of Sensing, Communication, and Computing for Intelligent Control in Industrial Cyber-Physical Systems

---

# 📌 Basic Information（基本信息）

## Author
Qinqin Tang, Yutian Yang, Jiayi Cui, Renchao Xie, Tao Huang, Tianjiao Chen, Ran Zhang, Zehui Xiong

## Year
2025

## Source
IEEE Journal on Selected Areas in Communications｜DOI: 10.1109/JSAC.2025.3574623

> Zotero 入口：zotero://select/library/items/RFIP7ECI
> PDF 入口：zotero://open-pdf/library/items/4DDGZBQW
> 全文 Markdown：[[03fulltext/ISAC/RFIP7ECI]]

## Research Area

- Industrial Cyber-Physical Systems (CPS)
- Cloud-Fog Automation (CFA)
- Sensing-Communication-Computing Co-Design
- Integrated Sensing and Communication (ISAC)

---

# 1. Abstract Summary（一句话总结）

> 该文面向工业信息物理系统（CPS）与云雾自动化（CFA），指出四类挑战——刚性传感器采样、通信配置不灵活、云与雾资源协同不足、感知/通信/计算缺乏集成，并提出 SeCo4 感知-通信-计算协同设计框架。

---

# 2. Research Background（研究背景）

## 背景：

- 工业信息物理系统（CPS）近年来取得显著进展，推动制造业未来发展。

> 原文：
> "Industrial Cyber-Physical Systems (CPS) have made significant strides in recent years, driving the future of manufacturing."

## Motivation（研究动机）

- 为推进云雾自动化（CFA），仍需解决四类挑战：
  1. **刚性的传感器采样**（rigid sensor sampling）
  2. **不灵活的通信配置**（inflexible communication configurations）
  3. **云与雾资源协同不足**（insufficient coordination between cloud and fog resources）
  4. **感知、通信与计算缺乏集成**（lack of integration between sensing, communication, and computing）

> 原文：
> "However, for further advancement in Cloud-Fog Automation (CFA), several challenges remain: rigid sensor sampling, inflexible communication configurations, insufficient coordination between cloud and fog resources, and a lack of integration between sensing, communicatio"

## Application Scenario（应用场景）

- 工业 CPS / 智能制造
- 云雾协同的自动化系统
- 需感通算一体化的工业物联网

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何通过感知、通信与计算的协同设计，克服工业 CPS 中采样刚性、通信僵化、云雾协同不足与感通算割裂四类挑战？

核心问题：

- 四类挑战如何逐一被协同设计化解？
- 感知、通信、计算三者如何统一建模？

---

# 4. Related Work（相关工作）

已有方法：

1. **固定周期采样的传感系统**：采样刚性，无法按任务/信道自适应。
2. **静态配置的工业通信**：通信参数不随业务变化。
3. **云中心或雾中心各自为政的架构**：云与雾缺乏协同。
4. **感知与通信分离设计**：计算更是独立规划。

现有不足：

- 感知、通信、计算三者被分别优化，难以获得一体化增益。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出 **SeCo4**——**感知、通信与计算的协同设计**（Co-Design of Sensing, Communication, and Computing）。
- 针对前述四类挑战逐一应对：灵活采样、可配置通信、云雾协同、感通算集成。

## Model / Framework

框架要素：

- **感知侧**：可自适应的传感器采样
- **通信侧**：灵活可配置的通信
- **计算侧**：云与雾资源的协同调度
- **一体化**：三者联合设计与优化

## Algorithm / Technique

采用：

- 感知-通信-计算协同设计（Co-Design）
- 自适应采样机制
- 灵活通信配置
- 云雾资源协同

## Key Steps

1. 分析工业 CPS / CFA 的现状与四类挑战。
2. 提出 SeCo4 协同设计框架，把感知、通信、计算纳入统一设计空间。
3. 针对每类挑战设计对应机制。
4. 通过系统集成与评估验证一体化收益。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **一体化对象**：感知（采样）、通信（配置与传输）、计算（云/雾资源）
- **优化目标**：在满足工业业务需求的约束下，联合优化三者以获得整体增益。

> 说明：SeCo4 的具体系统架构、各模块的优化模型与联合求解方式见 [[03fulltext/ISAC/RFIP7ECI]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 传感器采样率/时机可按需调整（非固定周期）。
- 通信参数（如调度、带宽）可动态配置。
- 云与雾的计算/存储资源可统一编排。

## Optimization Objective

目标：

- 克服四类挑战，实现工业 CPS 中感知、通信与计算的整体最优协同。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 论文包含系统评估（具体平台、规模与参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 采样灵活性与感知质量
- 通信配置效率
- 云雾资源协同程度
- 感通算一体化收益

## Results

主要结果：

- 所提 SeCo4 框架针对四类挑战提供了协同设计路径。

> 说明：具体的性能改善数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/RFIP7ECI]] 评估章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 系统指出推进云雾自动化（CFA）面临的四类挑战。
2. 提出 SeCo4 感知-通信-计算协同设计框架。
3. 把「计算」与感知、通信并列纳入一体化设计，扩展了传统 ISAC 的边界。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 仅做感知与通信的一体化（ISAC）不足以支撑工业 CPS，必须把计算也纳入统一设计。
- 采样、通信配置、云雾协同是工业场景特有的三个瓶颈。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 把 ISAC 扩展到「通感算一体化」是有价值的视野拓展，契合工业场景的真实需求。
- 四类挑战梳理清晰，有工程指导意义。
- 但与本 Vault 主线（UAV/ISAC 的波形、波束、轨迹设计）距离较远——本文偏系统架构与工业自动化。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅评估章节。
2. 框架层面的工作，具体算法细节需看全文。
3. 与 UAV/移动通信场景的关联较弱。

未来可能改进：

- 给出可复现的量化评估与对比。
- 探索该框架在 UAV 辅助工业物联网中的适用性。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **ISAC 的自然演进是「通感算一体化」**：工业场景中计算资源的编排与感知、通信同等重要。
- 采样刚性是工业传感的固有痛点——固定周期采样既浪费资源又可能错过关键事件。
- 云与雾的协同不足是分层架构的典型问题，需在编排层解决。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 ISAC 方向相关，但偏工业自动化，与 UAV 主线距离较远。
- 「通感算一体化」的视角可提醒自己：若涉及边缘计算场景，需把计算资源纳入权衡。
- 与 [[02vault/UAV/Joint Beamforming and UAV Deployment for ISAC-VEC|UAV 部署与波束成形]] 形成对照：该文面向车载边缘计算（VEC），本文面向工业云雾自动化（CFA）。

## Possible Ideas

可能的新想法：

- 探索 UAV 辅助工业物联网中「感知-通信-计算」的三方权衡。
- 把 UAV 机动性作为 SeCo4 框架中的新增自由度。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Joint Beamforming and UAV Deployment for ISAC-VEC|UAV 部署与波束成形]] — 同涉边缘计算，该文面向 VEC，本文面向工业 CFA

---

# 13. Summary Card（快速复习）

## Problem

> 工业 CPS 推进云雾自动化面临四类挑战：采样刚性、通信僵化、云雾协同不足、感通算割裂。

## Method

> 提出 SeCo4 感知-通信-计算协同设计框架，逐一应对四类挑战。

## Result

> 提供了感通算一体化的设计路径（具体收益见全文评估章节）。

## Importance

> 把 ISAC 的边界从「通感」扩展到「通感算」，契合工业自动化的真实需求。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决工业 CPS 中采样刚性、通信僵化、云雾协同不足、感通算割裂四类挑战。

Q:
核心方法是什么？

A:
SeCo4 感知-通信-计算协同设计框架。

Q:
最大贡献是什么？

A:
把计算纳入一体化设计，把 ISAC 扩展为通感算协同设计。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `RFIP7ECI`，PDF 附件 `4DDGZBQW`。
- PDF 经 pypdf 提取全文（87154 字符），原文引用均取自全文 Markdown [[03fulltext/ISAC/RFIP7ECI]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- SeCo4 架构细节、各模块优化模型与量化数值未在当前材料中逐项定位，已在正文如实标注，未做推测。