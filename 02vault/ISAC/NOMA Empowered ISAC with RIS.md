---
title: "NOMA Empowered Integrated Sensing and Communication (RIS-Assisted)"
aliases:
  - NOMA-ISAC
  - RIS NOMA ISAC
tags:
  - literature-note
  - reading-note
  - ISAC
  - NOMA
  - RIS
created: 2026-10-13
source: IEEE GLOBECOM Workshops, 2022
author: Zhaolin Wang, Yuanwei Liu, Xidong Mu, Zhiguo Ding, Octavia A. Dobre
year: 2022
journal: IEEE GLOBECOM Workshops

theme: 用可重构智能表面（RIS）提升 NOMA 赋能 ISAC 网络中的雷达感知性能
study_area: 通感一体化 / NOMA / 智能反射面
methodology: 交替优化 + SCA + 序列秩一约束松弛（SRCR）联合优化主动/被动波束成形与功率分配
core_variable: 最小雷达波束方向图增益、主动波束成形、功率分配系数、被动波束成形
key_finding: 所提 RIS 辅助 NOMA-ISAC 系统优于不含 NOMA 的 RIS 辅助 ISAC 系统
relevance: RIS + NOMA + ISAC 的组合，是提升 UAV-ISAC 感知性能的可选技术路径

type: literature-note
zotero_key: "W6BEE4ZE"
pdf_key: "A0DERMHC"
doi: "10.1109/gcwkshps56602.2022.10008704"
collection: "ISAC"
note_path: "02vault/ISAC/NOMA Empowered ISAC with RIS.md"
fulltext_path: "03fulltext/ISAC/W6BEE4ZE.md"
status:
  - Reading
rating: 四星
---

# NOMA Empowered Integrated Sensing and Communication (RIS-Assisted)

---

# 📌 Basic Information（基本信息）

## Author
Zhaolin Wang, Yuanwei Liu, Xidong Mu, Zhiguo Ding, Octavia A. Dobre

## Year
2022

## Source
IEEE GLOBECOM Workshops｜DOI: 10.1109/gcwkshps56602.2022.10008704

> Zotero 入口：zotero://select/library/items/W6BEE4ZE
> PDF 入口：zotero://open-pdf/library/items/A0DERMHC
> 全文 Markdown：[[03fulltext/ISAC/W6BEE4ZE]]

> 说明：Zotero 中该条目标题为「NOMA Empowered Integrated Sensing and Communication」；根据开放获取 PDF 原文，实际内容涉及 RIS 辅助的 NOMA-ISAC。

## Research Area

- Integrated Sensing and Communication (ISAC)
- Non-Orthogonal Multiple Access (NOMA)
- Reconfigurable Intelligent Surface (RIS)
- Beamforming Optimization

---

# 1. Abstract Summary（一句话总结）

> 该文利用可重构智能表面（RIS）提升 NOMA 赋能 ISAC 网络中的雷达感知性能，以最大化最小雷达波束方向图增益为目标，联合优化主动波束成形、功率分配系数与被动波束成形，并采用交替优化 + SCA + 序列秩一约束松弛（SRCR）求解非凸问题。

---

# 2. Research Background（研究背景）

## 背景：

- 传统无线通信中，通信与感知功能长期分离设计。
- NOMA 通过功率域复用提升频谱效率，可与 ISAC 结合。
- RIS 可通过被动波束成形改善信道条件，为 ISAC 提供额外自由度。

> 原文：
> "This paper exploits the potential of reconfigurable intelligent surface (RIS) to improve radar sensing in a non-orthogonal multiple access (NOMA) empowered integrated sensing and communication (NOMA-ISAC) network."

## Motivation（研究动机）

- NOMA-ISAC 网络中雷达感知性能受限于信道条件与功率分配。
- 联合优化主动波束成形、功率分配系数与被动波束成形构成非凸问题，需专门算法。

## Application Scenario（应用场景）

- RIS 辅助的 NOMA-ISAC 网络
- 需同时服务多用户通信与目标探测的场景
- UAV 载/地面 RIS 辅助的通感一体化（潜在迁移）

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在 RIS 辅助的 NOMA-ISAC 网络中，通过联合优化主动波束成形、功率分配系数与被动波束成形，最大化最小雷达波束方向图增益？

核心问题：

- 三类变量的联合非凸问题如何高效求解？
- RIS 的引入相比无 RIS 的 ISAC 能带来多少感知增益？
- NOMA 的引入相比无 NOMA 的 ISAC 能带来多少增益？
---

# 4. Related Work（相关工作）

已有方法：

1. **无 NOMA 的 RIS 辅助 ISAC**：本文的直接对比基线。
2. **不含 RIS 的 NOMA-ISAC**：缺少被动波束成形自由度。
3. **传统分离设计**：通信与感知分别优化。

现有不足：

- 未同时利用 NOMA 的功率域复用与 RIS 的信道重构能力。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 以**最大化最小雷达波束方向图增益**（minimum radar beampattern gain）为目标。
- 联合优化三类变量：主动波束成形、功率分配系数、被动波束成形。
- 针对非凸性，采用**交替优化 + 序列凸近似（SCA）+ 序列秩一约束松弛（SRCR）**的组合算法。

> 原文：
> "The objective is to maximize the minimum radar beampattern gain by jointly optimizing the active beamforming, power allocation coefficients and passive beamforming."
>
> 原文：
> "To tackle the formulated non-convex problem, we propose an efficient joint optimization algorithm by invoking alternating optimization, successive convex approximation (SCA) and sequential rank-one constraint relaxation (SRCR) algorithm."

## Model / Framework

系统模型：

- **网络**：NOMA 赋能的 ISAC 网络
- **增强手段**：RIS（被动波束成形）
- **优化变量**：
  - 主动波束成形（active beamforming，基站侧）
  - 功率分配系数（power allocation coefficients，NOMA）
  - 被动波束成形（passive beamforming，RIS 相移）

## Algorithm / Technique

采用：

- 交替优化（Alternating Optimization, AO）
- 序列凸近似（Successive Convex Approximation, SCA）
- 序列秩一约束松弛（Sequential Rank-one Constraint Relaxation, SRCR）

## Key Steps

1. 建立 RIS 辅助 NOMA-ISAC 系统模型，定义雷达波束方向图增益。
2. 构造最大化最小波束方向图增益的优化问题（含三类变量）。
3. 用交替优化把问题分解为关于主动波束成形、功率分配、被动波束成形的子问题。
4. 对各子问题分别用 SCA 处理非凸性，用 SRCR 处理秩一约束。
5. 迭代至收敛，并与不含 NOMA 的 RIS-ISAC 对比验证。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标**：最大化最小雷达波束方向图增益（maximize the minimum radar beampattern gain）。
- **优化变量**：主动波束成形、NOMA 功率分配系数、RIS 被动波束成形。
- **非凸来源**：变量耦合 + 被动波束成形的单位模约束 + 秩一约束。

> 说明：波束方向图增益的闭式表达、约束条件与 SRCR 的具体松弛步骤见 [[03fulltext/ISAC/W6BEE4ZE]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- RIS 为无源反射，相移受单位模约束。
- NOMA 用户可按功率域区分并做连续功率分配。
- 雷达波束方向图增益可作为感知性能的合理代理指标。

## Optimization Objective

目标：

- 在满足通信需求（隐含于 NOMA 功率分配）的前提下，最大化最差方向上的雷达波束增益，即提升感知的鲁棒性。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 数值结果验证（Numerical results），具体参数未在当前材料中定位到集中表述。

## Baseline

比较方法：

- 不含 NOMA 的 RIS 辅助 ISAC 系统（RIS assisted ISAC system without NOMA）

## Metrics

评价指标：

- 最小雷达波束方向图增益（minimum radar beampattern gain）

## Results

主要结果：

- 在所提方案辅助下，RIS 辅助 NOMA-ISAC 系统**优于不含 NOMA 的 RIS 辅助 ISAC 系统**。

> 原文：
> "Numerical results show that the proposed RIS assisted NOMA-ISAC system, with the aid of the proposed scheme, outperforms the RIS assisted ISAC system without NOMA."

> 说明：具体的增益数值未在当前材料中定位到可核验的集中表述，此处不做引述。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 利用 RIS 改善 NOMA 赋能 ISAC 网络中的雷达感知性能。
2. 以最大化最小雷达波束方向图增益为目标，联合优化主动波束成形、功率分配系数与被动波束成形。
3. 提出结合交替优化、SCA 与 SRCR 的高效联合优化算法。
4. 证明 RIS 辅助 NOMA-ISAC 优于不含 NOMA 的 RIS-ISAC。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 把 NOMA 的功率域复用引入 ISAC 感知侧，可在不额外占用时频资源的前提下提升雷达波束增益。
- SRCR 是处理被动波束成形秩一约束的有效工程手段。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- RIS + NOMA + ISAC 三者组合有一定新意，且给出了明确对比基线。
- 但属会议短文，算法为成熟工具（AO/SCA/SRCR）的组合，理论贡献有限。
- 感知指标用「最小波束方向图增益」是合理的鲁棒性代理。

---

# 10. Limitation（不足）

论文不足：

1. 会议短文，篇幅有限，收敛性与复杂度分析可能不足。
2. 仿真验证，无实测。
3. 未给出相对于无 RIS 情形的增益，基线对比不够完整。
4. 具体增益数值需查阅全文。

未来可能改进：

- 扩展为期刊长文，补充理论分析与更完整基线。
- 在真实 RIS 硬件上验证。
- 研究离散相移与信道估计误差的影响。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 「最大化最小波束方向图增益」体现了感知的鲁棒性导向：不只追求峰值，而是保证最差方向也有足够增益。
- SRCR（序列秩一约束松弛）是处理被动波束成形秩一约束的常用工程技巧。
- NOMA 的价值不止于通信容量，也可通过功率域设计改善感知波形。

## Connection With My Work

和我的研究/项目关系：

- RIS + ISAC 的组合可迁移到 UAV 载 IRS 场景，与本 Vault 的 [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]] 形成对照。
- 交替优化 + SCA + SRCR 的工具组合可用于自己的被动波束成形设计。
- 最小波束增益的鲁棒性目标可用于 UAV-ISAC 的感知波形设计。

## Possible Ideas

可能的新想法：

- 把 NOMA-ISAC 与 UAV 机动性结合（UAV 载 RIS + NOMA）。
- 对比 RIS 与 UAV 机动性两种自由度对感知增益的贡献占比。
- 研究离散相移与信道估计误差下的鲁棒设计。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]] — 同属 RIS/IRS 增强 ISAC，该文用 UAV 六维机动性，本文用 RIS 被动波束 + NOMA
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]] — 同属 ISAC 波束优化，该文关注结构理论，本文关注 RIS/NOMA 组合

---

# 13. Summary Card（快速复习）

## Problem

> NOMA-ISAC 网络中雷达感知性能受限，且主动/被动波束成形与功率分配的联合优化是非凸问题。

## Method

> 以最大化最小雷达波束方向图增益为目标，用交替优化 + SCA + SRCR 联合优化主动波束成形、功率分配与被动波束成形。

## Result

> RIS 辅助 NOMA-ISAC 优于不含 NOMA 的 RIS 辅助 ISAC。

## Importance

> 证明 NOMA 的功率域设计可改善 ISAC 的感知性能，为 RIS-ISAC 提供了额外增益来源。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 RIS 辅助 NOMA-ISAC 网络中雷达感知性能提升与三类变量联合非凸优化的问题。

Q:
核心方法是什么？

A:
以最大化最小雷达波束方向图增益为目标，用交替优化 + SCA + SRCR 联合优化主动波束成形、功率分配系数与被动波束成形。

Q:
最大贡献是什么？

A:
证明 RIS 辅助的 NOMA-ISAC 优于不含 NOMA 的 RIS-ISAC。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `W6BEE4ZE`，PDF 附件 `A0DERMHC`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/W6BEE4ZE]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- **标题差异说明**：Zotero 条目标题为「NOMA Empowered Integrated Sensing and Communication」，而开放获取 PDF 的实际内容涉及 RIS 辅助的 NOMA-ISAC（原清单的期刊字段为 IEEE Communications Letters，与 PDF 实际内容存在出入），已在正文标注该差异。
- 具体增益数值与仿真参数未在当前材料中定位，已如实标注。