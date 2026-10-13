---
title: "Channel Knowledge Map Enabled Low-Altitude ISAC Networks: Joint Air Corridor Planning and Base Station Deployment"
aliases:
  - CKM 低空 ISAC
  - 空中走廊规划
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - 网络规划
created: 2026-10-13
source: IEEE Wireless Communications Letters, 2026
author: Jiaxuan Li, Yilong Chen, Fan Liu, Jie Xu
year: 2026
journal: IEEE Wireless Communications Letters

theme: 用信道知识地图（CKM）支撑低空 ISAC 网络的空中走廊规划与基站部署联合优化
study_area: 通感一体化 / 低空网络 / 网络规划
methodology: 信道知识地图表征 + 分层由粗到细网格分解算法求解大规模非凸整数规划
core_variable: 空中走廊长度、部署基站数量、感知与通信覆盖性能
key_finding: 利用 CKM 在部署前刻画候选站址信道，实现离线规划；分层网格分解算法求解大规模非凸整数规划
relevance: 低空 ISAC 网络规划与本 Vault 的 UAV-ISAC 方向直接对口，CKM 是实用工具

type: literature-note
zotero_key: "JUTU2WE6"
pdf_key: "1A1B49FC"
doi: "10.1109/lwc.2025.3642429"
collection: "ISAC"
note_path: "02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC.md"
fulltext_path: "03fulltext/ISAC/JUTU2WE6.md"
status:
  - Reading
rating: 五星
---

# Channel Knowledge Map Enabled Low-Altitude ISAC Networks: Joint Air Corridor Planning and Base Station Deployment

---

# 📌 Basic Information（基本信息）

## Author
Jiaxuan Li, Yilong Chen, Fan Liu, Jie Xu

## Year
2026

## Source
IEEE Wireless Communications Letters｜DOI: 10.1109/lwc.2025.3642429

> Zotero 入口：zotero://select/library/items/JUTU2WE6
> PDF 入口：zotero://open-pdf/library/items/1A1B49FC
> 全文 Markdown：[[03fulltext/ISAC/JUTU2WE6]]

## Research Area

- Low-Altitude ISAC Networks
- Channel Knowledge Map (CKM)
- Air Corridor Planning
- Base Station Deployment

---

# 1. Abstract Summary（一句话总结）

> 该文研究低空 ISAC 网络中空中走廊规划与基站部署的联合问题：无人机在由立方段构成的走廊内运行，需在候选位置选择性部署多个基站以保障走廊全程的感知与通信覆盖；借助信道知识地图（CKM）在部署前刻画候选站址信道，并以分层由粗到细的网格分解算法求解最小化「走廊长度 + 基站数量」加权成本的大规模非凸整数规划。

---

# 2. Research Background（研究背景）

## 背景：

- 低空 ISAC 网络需要同时保障无人机运行全程的感知与通信覆盖。
- 基站部署位置的选择直接决定覆盖质量与建设成本。

## Motivation（研究动机）

- 联合规划空中走廊与基站部署，构成大规模非凸整数规划问题，难以直接求解。
- 若能在部署前就刻画候选站址的信道特性，可把在线优化转为离线规划，大幅降低复杂度。

> 原文：
> "we leverage the channel knowledge map (CKM) to characterize wireless channels for candidate BS sites prior to deployment, thereby facilitating the offline planning."

## Application Scenario（应用场景）

- 低空经济中的无人机航线（空中走廊）规划
- 低空 ISAC 网络的基站选址
- 需同时保障感知与通信覆盖的专网建设

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在低空 ISAC 网络中联合规划空中走廊与基站部署，在满足全程感知与通信覆盖约束下最小化系统成本？

核心问题：

- 如何用 CKM 在部署前刻画候选站址信道？
- 如何求解大规模非凸整数规划问题？
- 走廊长度与基站数量之间的成本如何权衡？
---

# 4. Related Work（相关工作）

已有方法：

1. **在线/实测驱动的规划**：需在部署后实测信道，难以做离线优化。
2. **分离规划**：先定走廊再布站，忽略二者的耦合。
3. **通用整数规划求解器**：面对大规模问题时计算不可行。

现有不足：

- 缺少在部署前即可刻画信道的工具（CKM 正是为此）。
- 大规模非凸整数规划缺少高效的专用算法。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 把无人机航路建模为**结构化空中走廊**：由相互连接的立方段（connected cubic segments）构成。
- 在候选位置集合中**选择性部署**多个基站，保障走廊全程的感知与通信覆盖。
- 借助**信道知识地图（CKM）**在部署前刻画候选站址的无线信道，从而支持**离线规划**。
- 针对大规模非凸整数规划，提出**分层由粗到细的网格分解算法**（hierarchical coarse-to-fine grid decomposition）。

> 原文：
> "unmanned aerial vehicles (UAVs) operate within a structured air corridor composed of connected cubic segments, and multiple BSs need to be selectively deployed at a set of candidate locations to ensure both sensing and communication coverage throughout the corridor."
>
> 原文：
> "To solve the formulated large-scale nonconvex integer programming problem, we develop a hierarchical coarse-to-fine grid decomposition algorithm."

## Model / Framework

系统模型：

- **空中走廊**：由连接的立方段构成的结构化航路
- **基站**：在候选位置集合中选择性部署
- **覆盖要求**：走廊全程需同时满足感知与通信性能约束
- **信道表征**：CKM（信道知识地图）

## Algorithm / Technique

采用：

- 信道知识地图（Channel Knowledge Map, CKM）
- 分层由粗到细网格分解算法（hierarchical coarse-to-fine grid decomposition）
- 大规模非凸整数规划求解

## Key Steps

1. 建模低空 ISAC 网络：定义结构化空中走廊（立方段连接）与候选基站位置。
2. 用 CKM 刻画各候选站址的无线信道特性，使规划可在部署前离线进行。
3. 构造优化问题：最小化「空中走廊长度 + 部署基站数量」的加权和系统成本。
4. 加入走廊全程的感知与通信性能约束。
5. 用分层由粗到细的网格分解算法求解该大规模非凸整数规划。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标**：最小化系统成本，定义为**空中走廊长度**与**部署基站数量**的加权和。
- **约束**：走廊全程的感知性能约束与通信性能约束。
- **问题性质**：大规模非凸整数规划（large-scale nonconvex integer programming）。

> 说明：走廊的立方段离散化方式、覆盖约束的闭式表达与网格分解的具体步骤见 [[03fulltext/ISAC/JUTU2WE6]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- CKM 可足够准确地刻画候选站址的信道特性（部署前可用）。
- 空中走廊可离散化为立方段的连接。
- 感知与通信覆盖可沿走廊分段评估。

## Optimization Objective

目标：

- 在满足全程感知与通信覆盖的前提下，最小化走廊长度与基站数量的加权成本。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（Simulation results），具体候选站址数量、走廊尺度与信道参数未在当前材料中定位到集中表述。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 空中走廊长度
- 部署基站数量
- 系统成本（上述二者的加权和）
- 感知与通信覆盖满足率

## Results

主要结果：

- 所提联合设计在**保障低空 ISAC 网络覆盖的同时降低了总体部署成本**。

> 原文：
> "Simulation results demonstrate the benefit of the proposed joint design in reducing the overall deployment cost while ensuring the coverage of the low-altitude ISAC networks." 

> 说明：具体的成本节省与覆盖性能数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/JUTU2WE6]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出低空 ISAC 网络中空中走廊规划与基站部署的联合问题。
2. 用结构化空中走廊（连接立方段）建模无人机航路。
3. 借助 CKM 在部署前刻画候选站址信道，实现离线规划。
4. 提出分层由粗到细网格分解算法，求解最小化「走廊长度 + 基站数量」加权成本的大规模非凸整数规划。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- CKM 把「先建后测」转变为「先刻画后规划」，是低空网络规划范式上的实用改进。
- 分层由粗到细的网格分解是应对大规模整数规划的可行工程路径。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 选题（低空 ISAC 网络规划）与本方向高度对口，且是工程上真实存在的问题。
- CKM 的引入有实际价值：把在线问题离线化。
- 但为通信快报（Letter），篇幅有限，算法细节与量化评估需看全文。

---

# 10. Limitation（不足）

论文不足：

1. Letter 篇幅，算法收敛性与最优性分析可能不足。
2. CKM 本身的构建成本与精度依赖未在本文充分讨论。
3. 仿真验证，无实测。
4. 未考虑基站部署后的动态环境变化（如新建遮挡）。

未来可能改进：

- 研究 CKM 构建成本与规划收益的权衡。
- 扩展到动态/时变环境下的在线重规划。
- 在真实低空场景做实测验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- CKM（信道知识地图）是连接「环境先验」与「网络规划」的实用桥梁，可把在线优化转为离线规划。
- 低空网络规划的核心权衡是「走廊长度 vs 基站数量」——航线越绕越省站，越直越费站。
- 大规模整数规划的实用解法常是分层/分解，而非直接求最优。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向直接对口，是低空网络规划的重要参考。
- CKM 思路可用于自己的 UAV 空地信道建模（与 [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]] 的实测数据互补）。
- 分层网格分解可借鉴到自己的大规模选址/规划问题。

## Possible Ideas

可能的新想法：

- 结合实测 UAV 信道数据构建 CKM，检验本文规划方法的实际收益。
- 把走廊规划与 [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] 的实时轨迹优化结合（离线规划 + 在线调整）。
- 研究动态遮挡下的 CKM 更新与重规划频率。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]] — 提供 UAV 空地信道实测依据，可作为 CKM 构建的数据来源
- [[02vault/ISAC/ISAC for Low-Altitude Economy DRL|DeepLSC 低空经济]] — 同属低空 ISAC，该文做实时 DRL 优化，本文做离线网络规划

---

# 13. Summary Card（快速复习）

## Problem

> 低空 ISAC 网络需联合规划空中走廊与基站部署，构成难以直接求解的大规模非凸整数规划。

## Method

> 用 CKM 部署前刻画候选站址信道实现离线规划；用分层由粗到细网格分解算法求解。

## Result

> 最小化「空中走廊长度 + 基站数量」的加权成本，同时满足全程感知与通信覆盖约束。

## Importance

> 把低空 ISAC 网络规划从「先建后测」推进到「先刻画后规划」，工程价值明确。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决低空 ISAC 网络中空中走廊规划与基站部署的联合优化问题。

Q:
核心方法是什么？

A:
用 CKM 在部署前刻画候选站址信道实现离线规划，并用分层由粗到细网格分解算法求解大规模非凸整数规划。

Q:
最大贡献是什么？

A:
提出 CKM 使能的低空 ISAC 网络离线规划框架，并给出可求解的大规模规划算法。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `JUTU2WE6`，PDF 附件 `1A1B49FC`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/JUTU2WE6]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 具体成本节省、覆盖性能数值与仿真参数未在当前材料中定位，已在正文如实标注，未做推测。