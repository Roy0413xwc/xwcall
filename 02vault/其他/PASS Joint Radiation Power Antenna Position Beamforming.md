---
title: "Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinching-Antenna Systems With Motion Power Consumption"
aliases:
  - PASS 可捏合天线
  - 天线位置与辐射功率优化
tags:
  - literature-note
  - reading-note
  - 可重构天线
  - PASS
  - 能效优化
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2026
author: Yiming Xu, Dongfang Xu, Xianghao Yu, Shenghui Song, Zhiguo Ding, Robert Schober
year: 2026
journal: IEEE Transactions on Wireless Communications

theme: 计入可捏合天线（PA）移动功耗与可调辐射功率的 PASS 系统节能设计
study_area: 可重构天线 / Pinching-Antenna Systems / 能效优化
methodology: 联合优化天线位置、天线辐射功率比与发射波束成形以最小化平均功耗
core_variable: 平均功耗、QoS 要求、天线位置、天线辐射功率比、发射波束成形
key_finding: 首次把 PA 移动功耗与可调辐射功率纳入 PASS 设计（既有研究忽略物理放置约束、假设固定辐射功率）
relevance: 与本 Vault 的可重构天线方向相关，且明确纳入功耗——与 [[02vault/其他/MIMO-PASS Uplink and Downlink Transmission|MIMO-PASS]] 互补

type: literature-note
zotero_key: "PNMKBVZU"
pdf_key: "PRRHI94A"
doi: "10.1109/TWC.2025.3633833"
collection: "其他"
note_path: "02vault/其他/PASS Joint Radiation Power Antenna Position Beamforming.md"
fulltext_path: "03fulltext/ISAC/PNMKBVZU.md"
status:
  - Reading
rating: 四星
---

# Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinching-Antenna Systems With Motion Power Consumption

---

# 📌 Basic Information（基本信息）

## Author
Yiming Xu, Dongfang Xu, Xianghao Yu, Shenghui Song, Zhiguo Ding, Robert Schober

## Year
2026

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2025.3633833

> Zotero 入口：zotero://select/library/items/PNMKBVZU
> PDF 入口：zotero://open-pdf/library/items/PRRHI94A
> 全文 Markdown：[[03fulltext/ISAC/PNMKBVZU.md]]

## Research Area

- Pinching-Antenna Systems (PASS)
- Reconfigurable Antennas
- Energy-Efficient Beamforming
- Antenna Position Optimization

---

# 1. Abstract Summary（一句话总结）

> 该文针对既有 PASS 研究忽略天线放置物理约束、假设固定辐射功率的局限，把可捏合天线（PA）的移动功耗与可调辐射功率纳入设计：在给定 QoS 要求下，通过联合优化天线位置、天线辐射功率比与发射波束成形来最小化平均功耗。

---

# 2. Research Background（研究背景）

## 背景：

- 可捏合天线系统（PASS）是近期提出的新型灵活天线技术，通过**同时重构大尺度与小尺度信道条件**来改善无线网络性能。

> 原文：
> "Pinching-antenna systems (PASS) have been recently proposed to improve the performance of wireless networks by reconfiguring both the large-scale and small-scale channel conditions."

## Motivation（研究动机）

- 既有研究存在两点局限：
  1. **忽略天线放置的物理约束**
  2. **假设天线辐射功率固定**

> 原文：
> "However, existing studies ignore the physical constraints of antenna placement and assume fixed antenna radiation power."

## Application Scenario（应用场景）

- 可捏合天线系统的实际部署与节能设计
- 需考虑天线移动能耗的场景
- 有 QoS 要求且需最小化功耗的无线系统

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在考虑 PA 移动功耗与可调辐射功率的条件下，如何在给定 QoS 要求下最小化 PASS 系统的平均功耗？

核心问题：

- 天线位置的物理约束如何建模？
- 天线辐射功率可调带来多少节能空间？
- 位置、辐射功率、波束成形三者如何联合优化？

---

# 4. Related Work（相关工作）

已有方法：

1. **忽略放置约束的 PASS 设计**：天线可任意放置，不实际。
2. **固定辐射功率的 PASS 设计**：未利用功率调节的自由度。
3. **不计天线移动能耗的工作**：低估了重构的代价。

现有不足：

- 未同时考虑物理放置约束、可调辐射功率与移动功耗。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 研究 PASS 的设计，**计入可捏合天线（PAs）的移动功耗**与**可调天线辐射功率的影响**。
- 目标：在给定 **QoS 要求**下**最小化平均功耗**。
- 手段：**联合优化**天线位置、天线辐射功率比、发射波束成形。

> 原文：
> "this paper investigates the design of PASS, taking into account the motion power consumption of pinching antennas (PAs) and the impact of adjustable antenna radiation power. To that end, we minimize the average power consumption for a given quality-of-service (QoS) requirement by jointly optimizing the antenna positions, antenna radiation power ratios, and transmit beamforming."

## Model / Framework

系统模型：

- **技术**：PASS（可捏合天线系统）
- **优化变量**：天线位置、天线辐射功率比、发射波束成形
- **约束**：QoS 要求、天线放置的物理约束
- **能耗项**：PA 移动功耗 + 辐射功率 + 发射功耗

## Algorithm / Technique

采用：

- 天线位置优化（含物理约束）
- 天线辐射功率比优化
- 发射波束成形优化
- 平均功耗最小化

## Key Steps

1. 建立 PASS 系统模型，明确大尺度与小尺度信道均可被重构。
2. 建模 PA 的移动功耗与可调辐射功率。
3. 加入天线放置的物理约束与 QoS 要求。
4. 联合优化天线位置、辐射功率比与发射波束成形以最小化平均功耗。
5. 通过仿真验证节能效果。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标函数**：平均功耗（含 PA 移动功耗、辐射功率、发射功耗）
- **约束**：QoS 要求、天线放置的物理约束
- **优化变量**：天线位置、天线辐射功率比、发射波束成形

> 说明：移动功耗模型、辐射功率比的约束形式与联合优化的具体求解方法见 [[03fulltext/ISAC/PNMKBVZU.md]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 可捏合天线可沿波导移动，移动会消耗能量。
- 天线辐射功率可在一定范围内调节。
- QoS 要求可量化为约束（如 SINR 或速率门限）。

## Optimization Objective

目标：

- 在满足 QoS 与物理约束的前提下最小化系统平均功耗。

---

# 7. Experiment / Evaluation（实验与验证）

数据与环境：

- 仿真验证（具体波导数、天线数、QoS 门限与信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 忽略放置约束或固定辐射功率的既有 PASS 设计。

## Metrics

评价指标：

- 平均功耗
- QoS 满足情况
- 天线位置与辐射功率的优化结果

## Results

主要结果：

- 通过联合优化位置、辐射功率与波束成形，在给定 QoS 下降低了平均功耗。

> 说明：具体的功耗降低比例未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/PNMKBVZU.md]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出既有 PASS 研究的两点局限：忽略放置物理约束、假设固定辐射功率。
2. 把 PA 的移动功耗纳入系统能耗模型。
3. 引入可调天线辐射功率作为新的优化自由度。
4. 在 QoS 约束下联合优化位置、辐射功率比与波束成形以最小化平均功耗。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 天线重构不是免费的——移动 PA 需要消耗能量，这是此前被忽略的实际代价。
- 辐射功率可调是继「位置可调」之后的第二个自由度，二者联合才有完整的设计空间。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 把移动功耗与可调辐射功率纳入设计是务实的补充，使 PASS 研究更贴近部署现实。
- 但与本 Vault 主线（UAV/ISAC）距离较远，属于可重构天线这一支线。
- 与 [[02vault/其他/MIMO-PASS Uplink and Downlink Transmission|MIMO-PASS]] 互补：该文研究上下行传输，本文研究能效与放置约束。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅仿真章节。
2. 仿真验证，无实测。
3. PA 移动速度/时延对动态业务的影响未讨论。

未来可能改进：

- 研究 PA 移动时延对业务连续性的影响。
- 在真实 PASS 平台上验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **重构天线是有代价的**：移动天线消耗能量，频繁重构可能得不偿失。
- 「位置可调」与「辐射功率可调」是两个独立自由度，联合优化才能发挥完整潜力。
- 物理放置约束（如最小间距、可达范围）是理论工作常忽略但部署时必须考虑的。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的可重构天线支线相关，与 UAV/ISAC 主线距离较远。
- 「移动代价」的思路可类比到 UAV：UAV 机动同样有能耗代价，与 [[02vault/UAV/Joint Beamforming and UAV Deployment for ISAC-VEC|UAV 部署与波束成形]] 的能耗关注点一致。

## Possible Ideas

可能的新想法：

- 把 PASS 的位置可调与 UAV 的机动性结合（UAV 载可捏合天线）。
- 研究重构频率与业务时延的权衡。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/其他/MIMO-PASS Uplink and Downlink Transmission|MIMO-PASS]] — 同属 PASS 技术，该文研究上下行传输，本文研究能效与放置约束

---

# 13. Summary Card（快速复习）

## Problem

> 既有 PASS 研究忽略天线放置的物理约束、假设固定辐射功率，且未计天线移动能耗。

## Method

> 计入 PA 移动功耗与可调辐射功率，在 QoS 约束下联合优化天线位置、辐射功率比与发射波束成形以最小化平均功耗。

## Result

> 在给定 QoS 下降低了平均功耗（具体数值见全文仿真章节）。

## Importance

> 使 PASS 设计从「理想重构」走向「考虑物理约束与移动代价」，更贴近部署现实。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决既有 PASS 研究忽略放置物理约束、假设固定辐射功率、未计移动能耗的问题。

Q:
核心方法是什么？

A:
计入 PA 移动功耗与可调辐射功率，联合优化天线位置、辐射功率比与波束成形以最小化平均功耗。

Q:
最大贡献是什么？

A:
把物理放置约束、可调辐射功率与移动功耗同时纳入 PASS 设计。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `PNMKBVZU`，PDF 附件 `PRRHI94A`。
- PDF 经 pypdf 提取全文（85731 字符），原文引用均取自全文 Markdown [[03fulltext/ISAC/PNMKBVZU.md]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 移动功耗模型、辐射功率比约束与量化数值未在当前材料中逐项定位，已在正文如实标注，未做推测。