---
title: "Integrated Sensing, Communication, and Over-The-Air Control of UAV Swarm Dynamics"
aliases:
  - ISAC-OTA
  - 空中计算控制
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - Over-the-Air
created: 2026-10-13
source: IEEE Transactions on Communications, 2025
author: Zhuangkun Wei, Wenxiu Hu, Yathreb Bouazizi, Chenguang Liu, Yunfei Chen, Hongjian Sun, Julie McCann
year: 2025
journal: IEEE Transactions on Communications

theme: 把空中计算（OTA）控制与感知融合，解决无人机群协同控制的频谱资源瓶颈
study_area: 通感一体化 / 空中计算 / 无人机群控制
methodology: 上行 OTA 信号构建 + 两种后处理方法（控制中心 / 感知中心）+ 下行非凸问题求解
core_variable: 频谱资源效率、控制精度、目标感知精度、传输引入干扰
key_finding: 提出 ISAC-OTA 框架，基站在构建/下发 OTA 控制信号的同时感知目标；两种上行后处理方法分别面向控制与感知
relevance: OTA + ISAC 是频谱受限下无人机群控制的高效路径，与本方向对口

type: literature-note
zotero_key: "ARDMTZWB"
pdf_key: "EUHD6I29"
doi: "10.1109/tcomm.2025.3649354"
collection: "UAV"
note_path: "02vault/UAV/ISAC-OTA UAV Swarm Dynamics.md"
fulltext_path: "03fulltext/UAV/ARDMTZWB.md"
status:
  - Reading
rating: 五星
---

# Integrated Sensing, Communication, and Over-The-Air Control of UAV Swarm Dynamics

---

# 📌 Basic Information（基本信息）

## Author
Zhuangkun Wei, Wenxiu Hu, Yathreb Bouazizi, Chenguang Liu, Yunfei Chen, Hongjian Sun, Julie McCann

## Year
2025

## Source
IEEE Transactions on Communications｜DOI: 10.1109/tcomm.2025.3649354

> Zotero 入口：zotero://select/library/items/ARDMTZWB
> PDF 入口：zotero://open-pdf/library/items/EUHD6I29
> 全文 Markdown：[[03fulltext/UAV/ARDMTZWB]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- Over-the-Air (OTA) Computation/Control
- UAV Swarm Coordination
- Spectrum-Efficient Control

---

# 1. Abstract Summary（一句话总结）

> 该文提出面向无人机群的感知—空中计算控制一体化框架（ISAC-OTA）：基站利用电磁叠加在空中直接构建（上行）与下发（下行）控制信号，同时感知目标；并针对上行提出两种后处理方法——控制中心的闭式控制信号生成，与感知中心的干扰抑制以提升目标感知精度。

---

# 2. Research Background（研究背景）

## 背景：

- 协同控制大规模无人机群需要大量频谱资源，因为每架无人机都需分配带宽。
- 在资源受限环境中，这构成严重挑战。
- 空中计算（OTA）利用电磁叠加在基站侧直接形成控制信号，是一种频谱高效的方法。

> 原文：
> "Coordinated controlling a large UAV swarm requires significant spectrum resources due to the need for bandwidth allocation per UAV, posing a challenge in resource-limited environments."
>
> 原文：
> "Over-the-air (OTA) control has emerged as a spectrum-efficient approach, leveraging electromagnetic superposition to form control signals at a base station (BS)."

## Motivation（研究动机）

- 现有 OTA 控制器缺少足够的优化变量以满足无人机群控制目标。
- 现有方案未能把控制与基站的其他功能（如感知）融合。

> 原文：
> "existing OTA controllers lack sufficient optimization variables to meet UAV swarm control objectives and fail to integrate control with other BS functions like sensing."

## Application Scenario（应用场景）

- 频谱受限环境下的大规模无人机群协同控制
- 基站兼具控制与感知功能的场景
- 无人机集群表演、协同搜救、编队运输

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在同一基站上把空中计算（OTA）控制与感知功能融合，既解决无人机群控制的频谱开销问题，又实现对目标的准确感知？

核心问题：

- 现有 OTA 控制器优化变量不足，如何扩展以满足机群控制目标？
- 如何在 OTA 信号构建的同时完成目标感知？
- 传输引入的干扰如何抑制以保证感知精度？
---

# 4. Related Work（相关工作）

已有方法：

1. **传统逐机带宽分配控制**：每架 UAV 单独分配带宽，频谱开销大。
2. **既有 OTA 控制器**：频谱高效，但优化变量不足且未与感知融合。
3. **分离的控制与感知系统**：未共享同一信号与硬件资源。

现有不足：

- OTA 控制的优化自由度不足以支撑机群级控制目标。
- 控制功能与感知功能未在同一框架内协同设计。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出面向无人机群的**感知与 OTA 控制一体化框架（ISAC-OTA）**。
- 基站执行 OTA 信号的**上行构建**（uplink signal construction）与**下行下发**（downlink dispatch），同时感知目标物体。
- 上行提出**两种后处理方法**：
  - **控制中心方法（control-centric）**：通过带反馈回路的 OTA 控制问题生成**闭式**控制信号。
  - **感知中心方法（sensing-centric）**：抑制传输引入的干扰，以实现准确的目标感知。
- 下行则处理一个非凸问题。

> 原文：
> "This work proposes an integrated sensing and OTA control framework (ISAC-OTA) for UAV swarm. The BS performs OTA signal construction (uplink) and dispatch (downlink) while simultaneously sensing objects."
>
> 原文：
> "Two uplink post-processing methods are developed: a control-centric approach generating closed-form control signals via a feedback-looped OTA control problem, and a sensing-centric method mitigating transmission-induced interference for accurate object sensing."

## Model / Framework

系统模型：

- **基站**：同时承担 OTA 控制信号的构建/下发与目标感知
- **上行**：利用电磁叠加在空中形成控制信号（OTA computation）
- **下行**：向无人机群下发控制信号（非凸优化问题）
- **对象**：无人机群（受控对象）+ 需感知的目标物体

## Algorithm / Technique

采用：

- 空中计算 / Over-the-Air（OTA）控制
- 电磁叠加（electromagnetic superposition）
- 反馈回路 OTA 控制问题（求闭式解）
- 传输引入干扰抑制（面向感知）
- 非凸优化（下行）

## Key Steps

1. 建立无人机群 OTA 控制与感知的一体化系统模型。
2. **上行**：利用电磁叠加在基站侧形成控制信号。
3. 上行后处理——控制中心法：构造带反馈回路的 OTA 控制问题，导出闭式控制信号。
4. 上行后处理——感知中心法：抑制传输引入干扰，提升目标感知精度。
5. **下行**：求解非凸的信号下发优化问题。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **上行 OTA 信号构建**：利用电磁叠加在空中合成控制信号，避免逐机带宽分配。
- **控制中心法**：把 OTA 控制表述为带反馈回路的控制问题，求得闭式控制信号。
- **感知中心法**：建模并抑制传输引入的干扰（transmission-induced interference），以提升感知精度。
- **下行**：信号下发问题为非凸。

> 说明：OTA 叠加模型、闭式控制信号的推导与下行非凸问题的具体形式见 [[03fulltext/UAV/ARDMTZWB]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 无线信道的电磁叠加可被利用来直接计算（形成）控制信号。
- 无人机群的控制目标可表述为可求闭式解的优化问题。
- 传输引入干扰可被建模并在后处理阶段抑制。

## Optimization Objective

目标：

- 在极低频谱开销下同时实现无人机群的精确控制与目标感知。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体机群规模、带宽、信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 传统逐机带宽分配控制方案
- 既有 OTA 控制器

> 说明：论文在引言中明确了对照思路，但基线具体名称未在当前材料中逐一定位，此处不做推测。

## Metrics

评价指标：

- 频谱资源效率（所需带宽）
- 控制精度
- 目标感知精度

## Results

主要结果：

- 提出 ISAC-OTA 框架，使基站在 OTA 信号构建/下发的同时完成目标感知。
- 控制中心法可生成闭式控制信号；感知中心法可抑制传输引入干扰以提升感知精度。

> 原文（摘要中的量化结论）：
> "Simulation results show that the proposed ISAC-OTA controller achieves control performance comparable to the benchmark optimal control algorithm while maintaining high sensing accuracy, despite OTA transmission interference. Moreover, it eliminates the need for per-UAV bandwidth allocation, showcasing a spectrum-efficient method for cooperative control in future wireless systems."
>
> 说明：具体的频谱节省百分比与控制误差数值未在当前材料中定位，此处按摘要结论如实引述「控制性能与基准最优控制算法相当」及「消除逐机带宽分配」两项结论。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出大规模无人机群协同控制的频谱瓶颈，并明确既有 OTA 控制器的两点不足（优化变量不足、未与感知融合）。
2. 提出 ISAC-OTA 框架，把 OTA 控制（上行构建 + 下行下发）与目标感知统一在基站侧。
3. 上行提出两种互补的后处理方法：控制中心（闭式控制信号）与感知中心（干扰抑制）。
4. 下行非凸问题给出相应求解方案。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- OTA 的电磁叠加不仅是通信技巧，也可直接用于「在空中计算」出控制信号，从而绕开逐机带宽分配。
- 控制与感知可在同一信号上共存，但需通过后处理区分与权衡（控制中心 vs 感知中心）。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 切中无人机群规模化的真实瓶颈（频谱随数量线性增长）。
- OTA + ISAC 的组合有新意，且明确给出「控制中心 vs 感知中心」的权衡视角。
- 控制中心法给出闭式解，实用性强。

- 局限：量化收益需查阅仿真章节。

---

# 10. Limitation（不足）

论文不足：

1. 控制中心法与感知中心法的切换/联合策略未明确（二者如何自适应权衡）。
2. 仿真验证，无实测或硬件在环。
3. OTA 依赖精确的信道叠加，对同步与信道估计误差敏感。
4. 量化性能需查阅仿真章节。

未来可能改进：

- 研究控制与感知的自适应联合权衡机制。
- 分析同步误差与信道估计误差对 OTA 叠加的鲁棒性影响。
- 在真实无人机群平台上验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 无人机群规模化的核心制约之一是频谱随数量线性增长，OTA 是对症解法。
- 同一信号承载控制与感知时，二者的需求冲突是本质性的，需要显式的后处理权衡。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV + ISAC 方向高度对口，是机群控制场景的重要参考。
- OTA + ISAC 的思路可用于自己的 UAV 集群通信—感知—控制一体化设计。
- 「控制中心 vs 感知中心」的权衡视角可迁移到自己的多目标波形设计。

## Possible Ideas

可能的新想法：

- 研究控制与感知权重的自适应调度（按任务阶段切换）。
- 分析 UAV 移动导致的信道时变对 OTA 叠加精度的破坏及补偿。
- 把 OTA 控制与 [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|无人机应急通信层次最优控制]] 的层次 MPC 结合。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|无人机应急通信层次最优控制]] — 同属 UAV 协同控制，该文用层次 MPC，本文用 OTA 空中计算
- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同属 UAV-ISAC，该文优化轨迹，本文把感知融入控制信号

---

# 13. Summary Card（快速复习）

## Problem

> 大规模无人机群协同控制需逐机分配带宽，频谱开销巨大；既有 OTA 控制器优化变量不足且未融合感知。

## Method

> 提出 ISAC-OTA 框架：基站利用电磁叠加上行构建、下行下发 OTA 控制信号，同时感知目标；上行提供控制中心（闭式）与感知中心（抗干扰）两种后处理。

## Result

> 在统一信号上同时实现无人机群控制与目标感知（具体频谱节省与精度见全文仿真章节）。

## Importance

> 用 OTA 空中计算破解无人机群控制的频谱瓶颈，并把感知功能融合进同一框架。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决大规模无人机群协同控制的频谱开销瓶颈，以及既有 OTA 控制器未融合感知的问题。

Q:
核心方法是什么？

A:
ISAC-OTA 框架：基站用电磁叠加构建/下发 OTA 控制信号并同时感知；上行有控制中心法（闭式解）与感知中心法（干扰抑制）。

Q:
最大贡献是什么？

A:
把空中计算控制与感知融合在同一基站信号上，给出了控制—感知权衡的两种后处理路径。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `ARDMTZWB`，PDF 附件 `EUHD6I29`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/ARDMTZWB]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 下行非凸问题的具体形式、量化频谱节省与精度数值未在当前材料中定位，已在正文如实标注，未做推测。