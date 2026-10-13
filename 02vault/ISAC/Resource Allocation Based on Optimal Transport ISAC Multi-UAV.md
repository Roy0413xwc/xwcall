---
title: "Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UAV Networks"
aliases:
  - AIBOT
  - 最优传输资源分配
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
created: 2026-10-13
source: IEEE GLOBECOM Workshops, 2024
author: (PDF 首页作者行未在当前全文提取中定位)
year: 2024
journal: IEEE GLOBECOM Workshops

theme: 用最优传输理论求解多无人机 ISAC 网络中的协作通信与非协作定位资源分配
study_area: 通感一体化 / 多无人机协同 / 资源分配
methodology: 基于最优传输理论的交替迭代算法（AIBOT）
core_variable: 系统平均和速率、定位 CRB、小区关联、通信/感知功率分配
key_finding: AIBOT 相比基准算法使系统和速率提升近 12%，定位 CRB 降低近 29%
relevance: 多 UAV 协同 ISAC 的资源分配，给出可量化的通信—感知权衡收益

type: literature-note
zotero_key: "9BZPEPMP"
pdf_key: "CQTI13K1"
doi: "10.1109/gcwkshp64532.2024.11100546"
collection: "ISAC"
note_path: "02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV.md"
fulltext_path: "03fulltext/ISAC/9BZPEPMP.md"
status:
  - Reading
rating: 四星
---

# Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UAV Networks

---

# 📌 Basic Information（基本信息）

## Author
PDF 首页作者行未在当前全文提取中定位，建议以 Zotero 条目或 PDF 首页为准

## Year
2024

## Source
IEEE GLOBECOM Workshops｜DOI: 10.1109/gcwkshp64532.2024.11100546

> Zotero 入口：zotero://select/library/items/9BZPEPMP
> PDF 入口：zotero://open-pdf/library/items/CQTI13K1
> 全文 Markdown：[[03fulltext/ISAC/9BZPEPMP]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- Multi-UAV Cooperative Networks
- Resource Allocation / Optimal Transport
- Non-Cooperative Localization

---

# 1. Abstract Summary（一句话总结）

> 该文研究多无人机 ISAC 协同网络中「协作通信 + 非协作定位」的资源分配优化，以最大化系统平均和速率与定位 QoS 的加权和为目标，联合优化小区关联、通信功率与感知功率分配，提出基于最优传输理论的交替迭代算法 AIBOT，使系统和速率提升近 12%、定位 CRB 降低近 29%。

---

# 2. Research Background（研究背景）

## 背景：

- ISAC 使能的多无人机协同网络中，通信与感知需共享有限的功率与关联资源。
- 协作通信（cooperative communication）与非协作定位（non-cooperative localization）并存，使资源分配问题更复杂。

## Motivation（研究动机）

- 联合优化小区关联、通信功率分配与感知功率分配，构成混合整数非凸问题，传统方法难以高效求解。
- 需要能同时改善通信速率与定位精度的资源分配算法。

> 原文：
> "Since the formulated problem is a mixed-integer nonconvex problem, we propose the alternating iteration algorithm based on optimal transport theory (AIBOT) to solve the optimization problem more effectively."

## Application Scenario（应用场景）

- 多无人机协同 ISAC 网络
- 需同时保障通信速率与目标定位精度的低空应用
- UAV 集群的资源调度
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在多无人机 ISAC 协同网络中，如何联合优化小区关联、通信功率与感知功率分配，以最大化系统平均和速率与定位 QoS 的加权和？

核心问题：

- 混合整数非凸的资源分配问题如何高效求解？
- 如何同时改善通信和速率与定位精度（CRB）？

---

# 4. Related Work（相关工作）

已有方法：

1. **传统交替优化**：可处理多变量耦合，但对混合整数非凸结构效率有限。
2. **基准算法（benchmark algorithms）**：本文的对比对象（具体名称未在摘要中定位）。

现有不足：

- 混合整数非凸结构使传统方法求解效率与解的质量受限。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 把资源分配问题中的小区关联部分借助**最优传输理论（optimal transport theory）**处理，从而更高效地求解混合整数非凸问题。
- 提出基于最优传输理论的交替迭代算法 AIBOT。

> 原文：
> "we propose the alternating iteration algorithm based on optimal transport theory (AIBOT) to solve the optimization problem more effectively."

## Model / Framework

系统模型：

- **网络**：ISAC 使能的多无人机（multi-UAV）协同网络
- **通信侧**：协作通信（cooperative communication）
- **感知侧**：非协作定位（non-cooperative localization）
- **优化变量**：小区关联（cell association）、通信功率分配、感知功率分配

## Algorithm / Technique

采用：

- 最优传输理论（Optimal Transport Theory）
- 交替迭代（Alternating Iteration）框架
- 混合整数非凸问题求解

## Key Steps

1. 建立多 UAV ISAC 网络模型，定义系统平均和速率与定位 QoS。
2. 构造加权和目标，联合优化小区关联、通信功率与感知功率分配。
3. 识别问题的混合整数非凸结构。
4. 用最优传输理论处理关联子问题，设计交替迭代算法 AIBOT。
5. 通过仿真与基准算法对比验证。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标**：最大化系统平均和速率与定位 QoS（localization quality of service）的加权和。
- **优化变量**：小区关联、通信功率分配、感知功率分配。
- **问题性质**：混合整数非凸（mixed-integer nonconvex）。

> 说明：具体的目标函数闭式表达、约束条件与 AIBOT 的迭代步骤见 [[03fulltext/ISAC/9BZPEPMP]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 多 UAV 可进行协作通信。
- 定位为非协作方式（目标不主动配合）。
- 小区关联问题可用最优传输框架近似/求解。

## Optimization Objective

目标：

- 在资源约束下同时最大化通信和速率与定位质量（以 CRB 度量）。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（Simulation results），具体网络规模与信道参数未在当前材料中定位到集中表述。

## Baseline

比较方法：

- benchmark algorithms（基准算法）

> 说明：论文摘要指出与基准算法对比，但基准具体名称未在当前材料中定位，此处不做推测。

## Metrics

评价指标：

- 系统平均和速率（system sum rate / average sum rate）
- 定位 Cramér-Rao 界（CRB）

## Results

主要结果（摘要明确给出的量化结论）：

| 指标 | 相对基准的改善 |
|---|---|
| 系统 sum rate | 提升近 12% |
| 定位 CRB | 降低近 29% |

> 原文：
> "Simulation results demonstrate that the AIBOT can improve the system sum rate by nearly 12% and reduce the localization Cramér-Rao bound (CRB) by almost 29% compared to benchmark algorithms."

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 研究 ISAC 使能多 UAV 协同网络中协作通信与非协作定位的资源分配优化。
2. 以系统平均和速率与定位 QoS 的加权和为目标，联合优化小区关联、通信功率与感知功率分配。
3. 提出基于最优传输理论的交替迭代算法 AIBOT，有效求解混合整数非凸问题。
4. 量化收益：系统 sum rate 提升近 12%，定位 CRB 降低近 29%。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 把最优传输理论引入 ISAC 资源分配中的关联子问题，是求解混合整数非凸结构的有效路径。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 给出了明确的量化收益（12% / 29%），工程参考价值直接。
- 但为会议短文（GLOBECOM Workshop），篇幅有限，方法细节与实验完备度不如期刊长文。
- 最优传输用于关联问题是有效的跨域借鉴。

---

# 10. Limitation（不足）

论文不足：

1. 会议短文，方法收敛性与复杂度分析可能不够充分。
2. 基准算法未具名，对比的公平性难以评估。
3. 仿真验证，无实测。
4. 论文作者行与部分实验参数未在当前材料中提取到。

未来可能改进：

- 扩展为期刊长文，补充收敛性与复杂度分析。
- 与具名 SOTA 算法做更充分对比。
- 在真实 UAV 平台上验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 最优传输理论可用于处理通信中的「关联/匹配」类离散子问题，是组合优化的有效工具。
- ISAC 资源分配中「协作通信 + 非协作定位」的组合是常见设定，两者对资源的竞争是核心矛盾。
- 同时报告通信增益（%）与感知增益（%）是 ISAC 论文的标准写法。

## Connection With My Work

和我的研究/项目关系：

- 多 UAV 协同 ISAC 与本 Vault 方向直接对口。
- AIBOT 的关联子问题处理思路可用于自己的 UAV-用户关联设计。
- 12%/29% 的量化结果可作为自己方案的对比参照。

## Possible Ideas

可能的新想法：

- 把最优传输框架扩展到 UAV 轨迹与关联联合优化。
- 研究非协作定位下目标机动性对 CRB 与资源分配的影响。
- 与 [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] 的轨迹设计结合，做轨迹—关联—功率三重优化。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同属 UAV-ISAC，该文优化轨迹，本文优化资源分配
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]] — 同属 ISAC 资源优化，该文关注波束结构，本文关注功率与关联

---

# 13. Summary Card（快速复习）

## Problem

> 多 UAV ISAC 网络中，小区关联与通信/感知功率的联合分配构成混合整数非凸问题，难以高效求解。

## Method

> 提出基于最优传输理论的交替迭代算法 AIBOT，联合优化小区关联、通信功率与感知功率分配。

## Result

> 系统 sum rate 提升近 12%，定位 CRB 降低近 29%。

## Importance

> 为多 UAV ISAC 网络的资源分配提供了可量化的通信—感知双赢方案。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决多 UAV ISAC 网络中小区关联与通信/感知功率联合分配的混合整数非凸优化问题。

Q:
核心方法是什么？

A:
基于最优传输理论的交替迭代算法 AIBOT。

Q:
最大贡献是什么？

A:
以 AIBOT 同时改善通信与感知：sum rate 提升近 12%，定位 CRB 降低近 29%。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `9BZPEPMP`，PDF 附件 `CQTI13K1`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/9BZPEPMP]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- **作者行缺失**：PDF 首页作者信息未在当前文本提取中定位，已如实标注。
- 基准算法名称与仿真参数未在当前材料中定位，已在正文标注，未做推测。