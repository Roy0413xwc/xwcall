---
title: "Radar Probing Optimization for Joint Beamforming and UAV Trajectory Design in UAV-Enabled Integrated Sensing and Communication"
aliases:
  - UAV 大规模 MIMO ISAC
  - 雷达探测误差
tags:
  - literature-note
  - reading-note
  - UAV
  - ISAC
  - massive-MIMO
created: 2026-10-13
source: IEEE Transactions on Communications, 2025
author: Yaxi Liu, Wencan Mao, Boxin He, Wei Huangfu, Tianyao Huang, Haijun Zhang, Keping Long
year: 2025
journal: IEEE Transactions on Communications

theme: 在无人机大规模 MIMO ISAC 中引入雷达探测误差指标，联合优化发射波束成形与 UAV 轨迹
study_area: 通感一体化 / 大规模 MIMO / 雷达探测
methodology: 雷达探测误差指标（PSM 的 MSE + CCP）+ 半正定松弛 + 通信/感知预编码器联合设计
core_variable: 雷达探测误差、通信 SINR 门限、用户数、UAV 轨迹
key_finding: 引入专用感知信号可带来收益；用户数增加会挤占功率资源、恶化感知性能
relevance: 与本 Vault 的 UAV-ISAC 方向对口，补充了「大规模 MIMO + 专用感知信号」这一细分设定

type: literature-note
zotero_key: "2N5HVUHH"
pdf_key: "95JQNCGP"
doi: "10.1109/TCOMM.2024.3506917"
collection: "UAV"
note_path: "02vault/UAV/Radar Probing Optimization for Joint Beamforming a.md"
fulltext_path: "03fulltext/UAV/2N5HVUHH.md"
status:
  - Reading
rating: 五星
---

# Radar Probing Optimization for Joint Beamforming and UAV Trajectory Design in UAV-Enabled Integrated Sensing and Communication

---

# 📌 Basic Information（基本信息）

## Author
Yaxi Liu, Wencan Mao, Boxin He, Wei Huangfu, Tianyao Huang, Haijun Zhang, Keping Long

## Year
2025

## Source
IEEE Transactions on Communications｜DOI: 10.1109/TCOMM.2024.3506917

> Zotero 入口：zotero://select/library/items/2N5HVUHH
> PDF 入口：zotero://open-pdf/library/items/95JQNCGP
> 全文 Markdown：[[03fulltext/UAV/2N5HVUHH]]

## Research Area

- UAV-Enabled Massive MIMO ISAC
- Radar Probing / Sensing Signal Design
- Transmit Beamforming and Trajectory Joint Design
- Semidefinite Relaxation

---

# 1. Abstract Summary（一句话总结）

> 该文针对无人机大规模 MIMO ISAC 中雷达探测任务被忽视的问题，引入「雷达探测误差」这一新指标，分别建立两类优化：一是面向大范围区域雷达探测与通信的发射波束成形设计（同时采用通信与专用感知预编码器），二是面向通信增强与雷达探测的波束成形与 UAV 轨迹联合设计。

---

# 2. Research Background（研究背景）

## 背景：

- 无人机使能的大规模多输入多输出（massive MIMO）ISAC 是一种新兴平台，可高效、灵活地同时执行通信与感知。

> 原文：
> "Unmanned aerial vehicle (UAV)-enabled massive multiple-input-multiple-output (MIMO) integrated sensing and communication (ISAC) is an emerging platform to perform communication and sensing efficiently and flexibly."

## Motivation（研究动机）

- 现有工作**很少考虑雷达探测任务**，且**忽视了专用感知信号带来的收益**。

> 原文：
> "the existing works barely consider the radar probing tasks and neglect the benefits of the dedicated sensing signal."

## Application Scenario（应用场景）

- 无人机载大规模 MIMO 的区域雷达探测 + 通信
- 需要专用感知信号支撑的高精度探测任务
- UAV 机动性辅助的通信增强与探测联合任务

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在 UAV 大规模 MIMO ISAC 中刻画并优化雷达探测任务的性能，同时兼顾通信需求？

核心问题：

- 如何度量雷达探测性能（新指标）？
- 专用感知信号能带来多少收益？
- 波束成形与 UAV 轨迹如何联合设计？
---

# 4. Related Work（相关工作）

已有方法：

1. **仅用通信信号做感知的 ISAC**：未设计专用感知预编码器，探测性能受限。
2. **忽略雷达探测任务的 UAV-ISAC 工作**：只优化通信或粗粒度感知指标。
3. **固定轨迹的波束成形设计**：未利用 UAV 机动性。

现有不足：

- 缺少面向雷达探测的专门性能指标。
- 未利用专用感知信号带来的探测增益。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 引入新指标——**雷达探测误差**（radar probing error），用于刻画雷达探测任务的精度。
- 建立两类优化问题：
  - **任务一**：面向大范围区域雷达探测 + 通信的**发射波束成形设计**
  - **任务二**：面向通信增强 + 雷达探测的**发射波束成形与 UAV 轨迹联合设计**

> 原文：
> "Two optimizations in radar probing tasks are established: i) joint transmit beamforming design for large-scale regional radar probing and communication task; ii) joint transmit beamforming and UAV trajectory design for communication enhancement and radar probing task."

## Model / Framework

系统模型：

- **平台**：UAV 载大规模 MIMO（massive MIMO）
- **指标**：雷达探测误差 = PSM 的 MSE + CCP（两项之和）
- **任务一方案**：同时采用**通信预编码器**与**专用感知预编码器**以支持 MIMO 雷达
- **任务二方案**：发射波束成形 + UAV 轨迹联合设计

## Algorithm / Technique

采用：

- 雷达探测误差指标（radar probing error）
- 通信与感知双预编码器设计
- 半正定松弛（semidefinite relaxation, SDR）
- 发射波束成形与 UAV 轨迹联合优化

## Key Steps

1. 建立 UAV 大规模 MIMO ISAC 系统模型，明确雷达探测任务。
2. 定义雷达探测误差指标（PSM 的 MSE 与 CCP 之和）。
3. 任务一：设计通信 + 专用感知双预编码器，支持 MIMO 雷达探测。
4. 用半正定松弛处理非凸的波束成形问题。
5. 任务二：进一步把 UAV 轨迹纳入，做波束成形与轨迹的联合优化。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **雷达探测误差**：由 PSM 的均方误差（MSE）与 CCP 两部分构成，作为探测精度的度量。
- **任务一变量**：通信预编码器 + 感知预编码器
- **任务二变量**：发射波束成形 + UAV 轨迹
- **求解**：半正定松弛（SDR）

> 说明：PSM 与 CCP 的具体定义、预编码器结构与 SDR 的推导细节见 [[03fulltext/UAV/2N5HVUHH]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- UAV 搭载大规模 MIMO 阵列，可同时形成通信与感知波束。
- 雷达探测误差可由 PSM 的 MSE 与 CCP 合理刻画。
- 专用感知信号可与通信信号共存（功率共享）。

## Optimization Objective

目标：

- 在满足通信需求（SINR 门限）的同时最小化雷达探测误差（任务一）；或同时优化通信增强与探测（任务二）。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证，考察三探测扇区场景下不同用户数、不同 SINR 门限下的雷达探测误差。
- 具体阵列规模与信道参数未在当前材料中定位到集中表述。

## Baseline

比较方法：

- 未采用专用感知信号的方案（论文指出这类工作忽视了该收益）。

## Metrics

评价指标：

- 雷达探测误差（PSM 的 MSE + CCP）
- 通信 SINR / 吞吐量
- 用户数对感知性能的影响

## Results

主要结果：

- **用户数增加会恶化感知性能**：用户越多，通信需求占用更多功率资源，附加在预编码器上的通信干扰会恶化感知；且恶化速率随用户数增加而上升。

> 原文：
> "as the number of users increases, the radar probing error, i.e., the MSE of PSM plus CCP, also increases. More number of users means higher communication demands to be satisfied, which will take up more power resources in the precoder. Hence, the higher communication interferences attached to the precoder will deteriorate the sensing performance. Furthermore, the rate of deterioration of sensing performance also increases with the number of CUs"

> 说明：具体的误差数值与对比增益未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/2N5HVUHH]] 仿真章节。