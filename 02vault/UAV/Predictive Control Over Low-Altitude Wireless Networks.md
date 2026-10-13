---
title: "Predictive Control Over Low-Altitude Wireless Networks: Joint Trajectory Design and Resource Allocation"
aliases:
  - LAWN 预测控制
  - MPC FBL 联合设计
tags:
  - literature-note
  - reading-note
  - UAV
  - 预测控制
  - URLLC
created: 2026-10-13
source: IEEE Transactions on Mobile Computing, 2026
author: Haijia Jin, Jun Wu, Weijie Yuan, Ruizhi Ruan, Jiacheng Wang, Dusit Niyato, Dong In Kim, Abbas Jamalipour
year: 2026
journal: IEEE Transactions on Mobile Computing

theme: 低空无线网络中面向时延敏感控制的无人机轨迹与资源联合预测控制
study_area: 低空网络 / 模型预测控制 / 有限块长传输
methodology: MPC 轨迹跟踪 + FBL 中断概率闭式表达 + 重构为二次规划（QP）
core_variable: 轨迹跟踪精度、中断概率、发射功率分配、最大行驶距离与控制输入约束
key_finding: 推导 FBL 下中断概率闭式表达，把原非凸问题重构为 QP，联合确定控制策略、功率分配与无人机轨迹
relevance: 低空网络时延敏感控制与本 Vault 的 UAV 方向对口，FBL 分析对 URLLC 设计有参考价值

type: literature-note
zotero_key: "IE53M953"
pdf_key: "6FXSCPUU"
doi: "10.1109/tmc.2026.3668854"
collection: "UAV"
note_path: "02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks.md"
fulltext_path: "03fulltext/UAV/IE53M953.md"
status:
  - Reading
rating: 五星
---

# Predictive Control Over Low-Altitude Wireless Networks: Joint Trajectory Design and Resource Allocation

---

# 📌 Basic Information（基本信息）

## Author
Haijia Jin, Jun Wu, Weijie Yuan, Ruizhi Ruan, Jiacheng Wang, Dusit Niyato, Dong In Kim, Abbas Jamalipour

## Year
2026

## Source
IEEE Transactions on Mobile Computing｜DOI: 10.1109/tmc.2026.3668854

> Zotero 入口：zotero://select/library/items/IE53M953
> PDF 入口：zotero://open-pdf/library/items/6FXSCPUU
> 全文 Markdown：[[03fulltext/UAV/IE53M953]]

## Research Area

- Low-Altitude Wireless Networks (LAWNs)
- Model Predictive Control (MPC)
- Finite Blocklength (FBL) Transmission
- Joint Trajectory and Resource Allocation

---

# 1. Abstract Summary（一句话总结）

> 该文研究低空无线网络中的实时无线控制：无人机通过有限块长（FBL）传输服务多台移动自动导引车（AGV），用 MPC 保证轨迹跟踪精度，并以中断概率分析通信可靠性；联合确定控制策略、发射功率分配与无人机轨迹，通过推导 FBL 下中断概率闭式表达把非凸问题重构为二次规划（QP）求解。

---

# 2. Research Background（研究背景）

## 背景：

- 低空无线网络（LAWNs）被视为在物联网系统中支撑时延敏感控制应用的灵活、变革性平台。
- 无人机可服务多台移动自动导引车（AGV），但需在有限块长（FBL）传输下保证可靠性。

> 原文：
> "Low-altitude wireless networks (LAWNs) have been envisioned as flexible and transformative platforms for enabling delay-sensitive control applications in Internet of Things (IoT) systems."

## Motivation（研究动机）

- 时延敏感控制要求通信与控制协同设计，单独优化任一侧都无法保证闭环性能。
- FBL 传输下中断概率的分析与优化是非凸问题，需专门处理。

## Application Scenario（应用场景）

- 低空网络支撑的工业物联网实时控制
- 无人机服务多台移动 AGV 的协同作业
- 时延敏感型无线控制系统（URLLC 场景）

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在低空无线网络中，如何在有限块长传输下联合确定控制策略、发射功率分配与无人机轨迹，以同时保证轨迹跟踪精度与通信可靠性？

核心问题：

- FBL 传输下的中断概率如何解析表征？
- 如何把含控制、功率、轨迹的联合非凸问题转化为可求解形式？
- 如何在最大行驶距离与控制输入约束下完成联合优化？
---

# 4. Related Work（相关工作）

已有方法：

1. **控制与通信分离设计**：先保证通信可靠性再设计控制，忽略闭环耦合。
2. **无限块长假设下的分析**：不适用短包、低时延的 URLLC 场景。
3. **固定轨迹的 UAV 辅助控制**：未把轨迹作为优化变量。

现有不足：

- FBL 场景下缺少中断概率的闭式表达，导致优化困难。
- 缺少控制—功率—轨迹三者的联合优化框架。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 采用**模型预测控制（MPC）**保证 AGV 的准确轨迹跟踪。
- 用**中断概率（outage probability）**分析通信可靠性。
- 构造联合优化问题，同时确定**控制策略、发射功率分配与无人机轨迹**，并计入最大行驶距离与控制输入约束。
- 针对非凸性：**先推导 FBL 传输下中断概率的闭式表达**，再据此把原问题**重构为二次规划（QP）**问题。

> 原文：
> "we adopt the model predictive control (MPC) to ensure accurate trajectory tracking, while we analyze the communication reliability using the outage probability."
>
> 原文：
> "we formulate an optimization problem to jointly determine control policy, transmit power allocation, and drone trajectory by accounting for the maximum travel distance and control input constraints."
>
> 原文：
> "To address the resultant non-convex optimization problem, we first derive the closed-form expression of the outage probability under FBL transmission. Based on this, we reformulate the original problem as a quadratic programming (QP) problem"

## Model / Framework

系统模型：

- **平台**：低空无线网络（LAWN），由无人机（drone）服务多台移动 AGV
- **传输**：有限块长（FBL）传输
- **控制**：MPC（模型预测控制）
- **可靠性度量**：中断概率（outage probability）

## Algorithm / Technique

采用：

- 模型预测控制（MPC）
- 有限块长（FBL）传输分析
- 中断概率闭式表达推导
- 二次规划（QP）重构与求解

## Key Steps

1. 建立低空无线网络模型：无人机通过 FBL 传输服务多台移动 AGV。
2. 用 MPC 设计控制策略以保证轨迹跟踪精度。
3. 分析 FBL 传输下的通信可靠性，推导中断概率的闭式表达。
4. 构造联合优化问题：控制策略 + 发射功率分配 + 无人机轨迹，含最大行驶距离与控制输入约束。
5. 基于闭式中断概率把原非凸问题重构为 QP 问题并求解。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **控制侧**：MPC 保证 AGV 轨迹跟踪精度。
- **通信侧**：FBL 传输下的中断概率（outage probability）作为可靠性度量。
- **优化变量**：控制策略、发射功率分配、无人机轨迹。
- **约束**：最大行驶距离（maximum travel distance）、控制输入约束（control input constraints）。
- **重构**：基于中断概率闭式表达，原非凸问题被重构为**二次规划（QP）**。

> 说明：中断概率的闭式表达、QP 重构的具体推导与约束的闭式形式见 [[03fulltext/UAV/IE53M953]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- FBL 传输的中断概率可解析求出闭式表达。
- MPC 可在给定通信可靠性下保证轨迹跟踪。
- AGV 的移动受最大行驶距离与控制输入约束限制。

## Optimization Objective

目标：

- 在满足行驶距离与控制输入约束下，联合优化控制、功率与轨迹，兼顾轨迹跟踪精度与通信可靠性。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

仿真设置（原文 Simulation Results 节）：

| 参数 | 取值 |
|---|---|
| 仿真总时长 | 60 s，划分为 120 个离散时隙 |
| AGV 数量 | 4 台，在 200 × 200 m² 矩形区域内移动 |
| 无人机 | 同区域内飞行，固定高度 50 m，初始位置 q[1] = [0, 100]ᵀ m |
| Nakagami 形状参数 | m = 2 |
| 参考信道增益 | β₀ = -50 dB |
| 子信道带宽 | B = 1 MHz |
| 噪声功率 | σ²ₖ = -100 dBm |
| BLER | ε = 10⁻⁶ |
| 控制权重矩阵 | Q₁ 与 Q₂ 均设为单位矩阵 |

> 原文：
> "The total simulation duration is set to 60 s, divided into 120 discrete time slots. Four AGVs are assumed to move within a predefined rectangular area of size 200 × 200 m². The drone flies within the same area at a fixed altitude of 50 m. The initial drone position is set as q[1] = [0, 100]ᵀ m. Regarding the communication parameters, the Nakagami shape parameter is set to m = 2. The reference channel gain is set to β₀ = -50 dB and the sub-channel bandwidth B is set to 1 MHz. The noise power is configured as σ²ₖ = -100 dBm and BLER is set to ε = 10⁻⁶." 

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 轨迹跟踪精度
- 中断概率（通信可靠性）
- 发射功率消耗

## Results

主要结果：

- 推导出 FBL 传输下中断概率的闭式表达，使原非凸问题可重构为 QP 并求解。
- 实现了控制策略、功率分配与无人机轨迹的联合确定。

> 说明：具体的跟踪误差、中断概率与功率节省数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/IE53M953]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 研究低空无线网络中面向时延敏感控制的实时无线控制问题。
2. 用 MPC 保证移动 AGV 的准确轨迹跟踪。
3. 推导 FBL 传输下中断概率的闭式表达，解决可靠性分析难题。
4. 基于该闭式表达把非凸问题重构为 QP，实现控制策略、功率分配与无人机轨迹的联合优化。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- FBL 场景下中断概率的闭式表达是把控制—通信联合问题变得可解的关键一步。
- 把非凸问题重构为 QP，既降低了求解难度，也便于工程实现。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 控制—通信联合设计（co-design）是低时延场景的正确范式，本文落地完整。
- 闭式中断概率 + QP 重构是实打实的技术贡献，不只是仿真调参。
- 期刊（TMC）长文，完整度较好。

- 局限：量化收益需查阅仿真章节。

---

# 10. Limitation（不足）

论文不足：

1. 仿真验证，无实测或硬件在环。
2. MPC 的计算负担在大规模 AGV 场景下需进一步评估。
3. 未考虑无人机自身能耗与续航约束。
4. 量化性能需查阅仿真章节。

未来可能改进：

- 在真实 AGV + 无人机平台上验证。
- 纳入无人机能耗与续航约束。
- 研究多无人机协同服务更大范围 AGV 的扩展。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 时延敏感控制必须做控制—通信联合设计：通信可靠性直接决定控制闭环能否稳定。
- FBL（有限块长）是 URLLC 的正确建模层次，香农容量公式在此不再适用。
- 「推导闭式表达 → 问题重构为 QP」是解决非凸工程问题的经典而有效的路径。
- 把无人机轨迹作为优化变量，是低空网络相对地面网络的独有自由度。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV 方向对口，是低空网络控制场景的重要参考。
- FBL 中断概率分析可用于自己的 UAV 链路可靠性建模。
- 控制—通信联合设计的框架可迁移到 UAV-ISAC 的感知—控制协同。

## Possible Ideas

可能的新想法：

- 把 FBL 分析引入 UAV-ISAC，研究感知性能与通信可靠性的联合约束。
- 纳入无人机能耗，研究续航与控制性能的权衡。
- 与 [[02vault/UAV/ISAC-OTA UAV Swarm Dynamics|ISAC-OTA 机群控制]] 对比：OTA 提升频谱效率，本文用 FBL 保证可靠性，二者可互补。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC-OTA UAV Swarm Dynamics|ISAC-OTA 机群控制]] — 同属 UAV 协同控制，该文用 OTA 提升频谱效率，本文用 FBL 保证可靠性
- [[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]] — 同为 UAV 轨迹优化，该文面向通信覆盖，本文面向时延敏感控制

---

# 13. Summary Card（快速复习）

## Problem

> 低空网络中时延敏感控制需联合设计控制与通信，FBL 下的中断概率分析使问题非凸难解。

## Method

> MPC 保证轨迹跟踪；推导 FBL 中断概率闭式表达；据此把非凸问题重构为 QP，联合优化控制策略、功率分配与无人机轨迹。

## Result

> 实现了控制—功率—轨迹的联合确定（具体跟踪精度与可靠性数值见全文仿真章节）。

## Importance

> 为低空网络的时延敏感控制提供了完整的控制—通信联合设计范式与可求解路径。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决低空无线网络中时延敏感控制下，FBL 传输可靠性与控制性能的联合优化问题。

Q:
核心方法是什么？

A:
MPC 轨迹跟踪 + 推导 FBL 中断概率闭式表达 + 重构为 QP 联合优化控制、功率与无人机轨迹。

Q:
最大贡献是什么？

A:
给出 FBL 下中断概率的闭式表达并把问题重构为 QP，使控制—通信联合设计可高效求解。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `IE53M953`，PDF 附件 `6FXSCPUU`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/IE53M953]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 中断概率闭式表达与 QP 重构的具体推导、量化仿真数值未在当前材料中定位，已在正文如实标注，未做推测。