---
title: "Joint Beamforming and UAV Deployment Optimization for ISAC-Enhanced UAV-Assisted VEC"
aliases:
  - UAV 部署与波束成形
  - ISAC 增强 VEC
tags:
  - literature-note
  - reading-note
  - UAV
  - ISAC
  - 边缘计算
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2026
author: Chunlin Li, Wenhao Wu, Zhihao Zhang, Tianbing Ma, Shaohua Wan
year: 2026
journal: IEEE Transactions on Wireless Communications

theme: 在能量约束下联合优化无人机部署位置与波束成形，平衡 ISAC 性能与能耗
study_area: 通感一体化 / UAV 部署 / 车载边缘计算（VEC）
methodology: 能量约束下的 UAV 部署位置与波束成形联合优化（ISAC 使能的节能部署方法）
core_variable: UAV 能量消耗、通信效率、通信与感知性能平衡、部署位置
key_finding: 提出 UAV 节能部署方法，在能量约束下平衡通信与感知性能、降低能耗并提升通信效率
relevance: 与本 Vault 的 UAV-ISAC 方向对口，且明确纳入能量约束——这正是本 Vault 主题页指出的普遍缺口

type: literature-note
zotero_key: "WRMKPUJZ"
pdf_key: "5Y3YEDPN"
doi: "10.1109/TWC.2026.3694912"
collection: "UAV"
note_path: "02vault/UAV/Joint Beamforming and UAV Deployment for ISAC-VEC.md"
fulltext_path: "03fulltext/UAV/WRMKPUJZ.md"
status:
  - Reading
rating: 五星
---

# Joint Beamforming and UAV Deployment Optimization for ISAC-Enhanced UAV-Assisted VEC

---

# 📌 Basic Information（基本信息）

## Author
Chunlin Li, Wenhao Wu, Zhihao Zhang, Tianbing Ma, Shaohua Wan

## Year
2026

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2026.3694912

> Zotero 入口：zotero://select/library/items/WRMKPUJZ
> PDF 入口：zotero://open-pdf/library/items/5Y3YEDPN
> 全文 Markdown：[[03fulltext/UAV/WRMKPUJZ]]

## Research Area

- UAV-Assisted Vehicular Edge Computing (VEC)
- Integrated Sensing and Communication (ISAC)
- UAV Deployment and Beamforming Optimization
- Energy-Efficient Design

---

# 1. Abstract Summary（一句话总结）

> 该文针对城市临时拥塞或热点场景中固定路侧单元（RSU）难以提供可靠服务的问题，提出基于 ISAC 的无人机节能部署方法：在 UAV 能量约束下联合优化部署位置与波束成形，以平衡通信与感知性能、降低能耗并提升通信效率。

---

# 2. Research Background（研究背景）

## 背景：

- 在城市临时拥塞或热点场景中，固定部署的路侧单元（RSU）往往无法提供可靠、高效的通信服务。
- 无人机可被快速部署，提供灵活的按需通信与感知支持，有效补充地面基础设施。

> 原文：
> "In urban temporary congestion or hotspot scenarios, fixed roadside units (RSUs) often fail to provide reliable and efficient communication services due to their static deployment. Unmanned Aerial Vehicles (UAVs) can be rapidly deployed to provide flexible and on-demand communication and sensing support, effectively complementing ground infrastructure."

## Motivation（研究动机）

- UAV 面临三重挑战：**覆盖范围有限、部署复杂度高、通信与感知性能不均衡**。
- 这些挑战导致能耗上升、通信效率下降。

> 原文：
> "UAVs are faced with challenges such as limited coverage, high deployment complexity, and unbalanced communication-sensing performance. These challenges give rise to increased energy consumption and reduced communication efficiency."

## Application Scenario（应用场景）

- 城市临时拥塞/热点区域的应急通信补盲
- UAV 辅助的车载边缘计算（VEC）任务卸载
- 需兼顾通信、感知与能耗的 UAV 部署规划

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在 UAV 能量约束下联合优化部署位置与波束成形，使 ISAC 系统在通信与感知性能之间取得平衡，同时降低能耗？

核心问题：

- 能量约束如何进入部署与波束成形的联合优化？
- 如何缓解通信与感知性能的不均衡？
- 如何降低部署复杂度？
---

# 4. Related Work（相关工作）

已有方法（论文 II 节综述）：

1. **UAV 作为空中边缘服务器进行任务卸载**：如 Dai 等用 UAV 卸载过载 RSU 的计算任务。
2. **两层 PSO-遗传-贪心算法**：如 Chen 等联合优化 UAV 部署与计算卸载以最小化平均任务响应时间。
3. **任务优先级与二元卸载决策**：如 Hao 等研究多 UAV 辅助 MEC 的任务卸载。
4. **波束成形与轨迹联合优化**：如 Deng 等最大化通信性能，或提出自适应的 ISAC 机制。

现有不足：

- 多数工作未把**能量约束**作为部署优化的核心约束。
- 通信与感知性能的**不均衡**问题缺乏专门处理。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出基于 ISAC 的 **UAV 节能部署方法**，在性能与能耗之间取得平衡。
- 在 **UAV 能量约束**下，联合优化 **UAV 部署位置**与**波束成形**，以最大化（或平衡）通信与感知性能。

> 原文：
> "we propose a UAV energy-efficient deployment method based on Integrated Sensing and Communication (ISAC), which balances performance and energy consumption. Specifically, under UAV energy constraints, we jointly optimize UAV deployment positions and beamforming"

## Model / Framework

系统模型：

- **场景**：城市临时拥塞 / 热点区域，固定 RSU 服务不足
- **平台**：UAV（可快速部署，提供通信 + 感知）
- **上层业务**：车载边缘计算（VEC）的任务卸载
- **优化变量**：UAV 部署位置、波束成形
- **约束**：UAV 能量约束

## Algorithm / Technique

采用：

- ISAC 使能的节能部署建模
- 部署位置与波束成形联合优化
- 能量约束处理
- 通信-感知性能平衡机制

## Key Steps

1. 建立 UAV 辅助 VEC 的 ISAC 系统模型，明确 RSU 不足与 UAV 补盲的需求。
2. 把 UAV 能量作为核心约束引入优化问题。
3. 联合优化 UAV 部署位置与波束成形。
4. 设计通信-感知性能平衡机制，缓解二者不均衡。
5. 通过仿真验证能耗降低与通信效率提升。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **优化变量**：UAV 部署位置、波束成形。
- **约束**：UAV 能量约束（energy constraints）。
- **目标**：最大化/平衡通信与感知性能，同时最小化能耗。

> 说明：能量模型、部署位置的连续/离散化方式与波束成形优化的具体形式见 [[03fulltext/UAV/WRMKPUJZ]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- UAV 能量有限且可建模为部署位置与波束成形的函数。
- 部署位置与波束成形可联合优化（而非分步）。
- 通信与感知性能可通过加权或约束方式实现平衡。

## Optimization Objective

目标：

- 在能量约束下同时改善通信效率、降低能耗，并缓解通信-感知性能的不均衡。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体 UAV 数量、覆盖范围、信道与能耗参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- UAV 能量消耗
- 通信效率
- 通信与感知性能的均衡程度

## Results

主要结果：

- 所提方法在 UAV 能量约束下实现了部署位置与波束成形的联合优化。
- 达到了性能与能耗的平衡，降低了能耗并提升了通信效率。

> 说明：具体的能耗降低比例与效率提升数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/WRMKPUJZ]] 仿真章节。