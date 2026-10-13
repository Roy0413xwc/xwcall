---
title: "A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System"
aliases:
  - 控制导向 UAV-ISAC
  - 3-DoF / 6-DoF 动力学
tags:
  - literature-note
  - reading-note
  - UAV
  - ISAC
  - 控制理论
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2026
author: Bin Li, Hongyun Zhang, Yue Rong, Zhu Han
year: 2026
journal: IEEE Transactions on Wireless Communications

theme: 把 UAV 动力学模型（3-DoF 与 6-DoF）纳入波束成形与轨迹设计，实现控制感知的一体化设计
study_area: 通感一体化 / UAV 动力学建模 / 波束成形与轨迹联合优化
methodology: 含动力学约束的 3-DoF 与 6-DoF 两类优化问题 + 分解为波束成形与轨迹子问题
core_variable: 平均加权通信速率、动力学约束、感知服务需求、UAV 轨迹与波束成形向量
key_finding: 显式纳入常被既有设计忽视的 UAV 动力学模型，在动力学与感知约束下最大化平均加权通信速率
relevance: 与本 Vault 的 UAV-ISAC 方向对口，且补充了「动力学可行性」这一工程约束维度

type: literature-note
zotero_key: "HWHQDBSP"
pdf_key: "6PFB9AYV"
doi: "10.1109/TWC.2025.3604344"
collection: "UAV"
note_path: "02vault/UAV/Control-Based Beamforming and Trajectory for UAV-ISAC.md"
fulltext_path: "03fulltext/UAV/HWHQDBSP.md"
status:
  - Reading
rating: 五星
---

# A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System

---

# 📌 Basic Information（基本信息）

## Author
Bin Li, Hongyun Zhang, Yue Rong, Zhu Han

## Year
2026

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2025.3604344

> Zotero 入口：zotero://select/library/items/HWHQDBSP
> PDF 入口：zotero://open-pdf/library/items/6PFB9AYV
> 全文 Markdown：[[03fulltext/UAV/HWHQDBSP]]

## Research Area

- UAV-Enabled ISAC
- Control-Based Design / Dynamic Models
- Beamforming and Trajectory Joint Optimization
- Multi-Target Sensing + Multi-User Communication

---

# 1. Abstract Summary（一句话总结）

> 该文研究控制导向的波束成形与轨迹设计：多天线 UAV 在特定区域对多个目标做雷达感知、同时与多个地面用户通信，显式纳入常被既有设计忽视的 UAV 动力学模型（3-DoF 与 6-DoF），在动力学约束与感知服务需求下最大化平均加权通信速率，并把原问题分解为通信/感知波束成形与轨迹两个子问题求解。

---

# 2. Research Background（研究背景）

## 背景：

- 多天线 UAV 可在特定区域同时执行多目标雷达感知与多地面用户通信。

## Motivation（研究动机）

- 既有设计**普遍忽视 UAV 的动力学模型**——即 UAV 实际的运动能力约束（3 自由度与 6 自由度动力学）。
- 忽略动力学会导致设计的轨迹在物理上不可行。

> 原文：
> "Two optimization problems are formulated for the three-degree-of-freedom (3-DoF) and six-degree-of-freedom (6-DoF) dynamic models of UAV, which are often overlooked in existing designs."

## Application Scenario（应用场景）

- 多天线 UAV 的区域多目标探测 + 多用户通信
- 需保证轨迹动力学可行性的 UAV-ISAC 任务
- 对机动性有明确约束的实际 UAV 平台

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在 UAV 动力学约束与感知服务需求下，设计波束成形与轨迹以最大化平均加权通信速率？

核心问题：

- 3-DoF 与 6-DoF 动力学模型如何分别建模？
- 动力学约束如何与波束成形、感知需求耦合？
- 耦合问题如何分解求解？
---

# 4. Related Work（相关工作）

已有方法：

1. **忽略动力学的 UAV-ISAC 设计**：假设 UAV 可任意移动，轨迹物理上未必可行。
2. **仅考虑运动学（位置/速度）的工作**：未建模姿态与角动力学。
3. **分离设计波束成形与轨迹**：忽略二者的耦合。

现有不足：

- UAV 动力学模型（3-DoF / 6-DoF）在既有设计中被普遍忽视。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 研究**控制导向（control-based）**的波束成形与轨迹设计，把 UAV 动态模型纳入设计。
- 针对 UAV 的 **3-DoF** 与 **6-DoF** 动力学模型，分别建立两个优化问题。
- 目标：在维持**动力学约束**与**感知服务需求**的前提下，最大化**平均加权通信速率**。
- 为应对动力学约束带来的挑战，把原问题**分解为两个子问题**：通信与感知波束成形、UAV 轨迹。

> 原文：
> "Two optimization problems are formulated for the three-degree-of-freedom (3-DoF) and six-degree-of-freedom (6-DoF) dynamic models of UAV, which are often overlooked in existing designs. These problems aim to maximize the average weighted communication rate while maintaining the dynamic constraints and the sensing service requirements by designing the UAV trajectory and the communication and sensing beamforming vectors."
>
> 原文：
> "To deal with the challenges posed by the UAV dynamic constraints, we decompose the original problem into two subproblems: the communication and sensing beamforming"

## Model / Framework

系统模型：

- **平台**：多天线 UAV
- **任务**：对特定区域内的多个目标做雷达感知 + 与多个地面用户通信
- **动力学模型**：3-DoF（三自由度）与 6-DoF（六自由度）两套，分别建模
- **优化变量**：UAV 轨迹、通信波束成形向量、感知波束成形向量

## Algorithm / Technique

采用：

- 控制导向设计（control-based design）
- 3-DoF / 6-DoF 动力学建模
- 问题分解（波束成形子问题 + 轨迹子问题）
- 平均加权通信速率最大化

## Key Steps

1. 建立多天线 UAV 同时执行多目标感知与多用户通信的系统模型。
2. 分别建立 UAV 的 3-DoF 与 6-DoF 动力学模型，形成两个优化问题。
3. 设定目标为最大化平均加权通信速率，约束含动力学可行性与感知服务需求。
4. 把原问题分解为通信/感知波束成形子问题与 UAV 轨迹子问题。
5. 交替/迭代求解两个子问题至收敛。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标函数**：平均加权通信速率（average weighted communication rate）
- **约束**：
  - UAV 动力学约束（3-DoF 或 6-DoF 动态模型）
  - 感知服务需求（sensing service requirements）
- **优化变量**：UAV 轨迹、通信波束成形向量、感知波束成形向量
- **分解**：原问题 → 波束成形子问题 + 轨迹子问题

> 说明：3-DoF 与 6-DoF 动力学方程的具体形式、感知服务需求的量化方式与子问题求解细节见 [[03fulltext/UAV/HWHQDBSP]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- UAV 动力学可由 3-DoF（如仅平动）或 6-DoF（平动+转动）模型刻画。
- 目标位于特定区域内，感知需求可量化为约束。
- 波束成形与轨迹可通过分解交替求解。

## Optimization Objective

目标：

- 在满足动力学可行性与感知需求的前提下，最大化平均加权通信速率。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体天线数、目标/用户数、区域尺度与动力学参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 平均加权通信速率
- 动力学约束满足情况（轨迹物理可行性）
- 感知服务需求满足情况

## Results

主要结果：

- 通过纳入 3-DoF 与 6-DoF 动力学模型，所得轨迹具备动力学可行性。
- 在动力学与感知约束下实现了平均加权通信速率的最大化。

> 说明：具体的速率数值与对比增益未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/HWHQDBSP]] 仿真章节。