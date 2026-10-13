---
title: "Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using Meta Deep Reinforcement Learning"
aliases:
  - STAR-IRS SCMA ISAC
  - 元深度强化学习资源分配
tags:
  - literature-note
  - reading-note
  - ISAC
  - STAR-IRS
  - 太赫兹
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2025
author: Armin Farhadi, Ali Olfat, Christos Masouros
year: 2025
journal: IEEE Transactions on Wireless Communications

theme: 太赫兹频段下 STAR-IRS 辅助 SCMA 的 ISAC 系统波束成形与资源分配联合优化
study_area: 通感一体化 / STAR-IRS / SCMA / 太赫兹
methodology: 元深度强化学习（MDRL）求解 NP-hard 联合优化问题，并具备适应不同情境的能力
core_variable: 波束成形、资源分配、QoS 约束、STAR-IRS 约束、感知与通信性能
key_finding: 所提联合优化为 NP-hard，采用 MDRL 求解并使解具备跨情境适应能力
relevance: 与本 Vault 的 ISAC 方向相关，补充了「STAR-IRS + 非正交多址 + 太赫兹」这一组合场景

type: literature-note
zotero_key: "M4EVSKTU"
pdf_key: "P6HRFKYQ"
doi: "10.1109/TWC.2025.3580347"
collection: "ISAC"
note_path: "02vault/ISAC/STAR-IRS SCMA ISAC Beamforming (THz).md"
fulltext_path: "03fulltext/ISAC/M4EVSKTU.md"
status:
  - Reading
rating: 四星
---

# Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using Meta Deep Reinforcement Learning

---

# 📌 Basic Information（基本信息）

## Author
Armin Farhadi, Ali Olfat, Christos Masouros

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2025.3580347

> Zotero 入口：zotero://select/library/items/M4EVSKTU
> PDF 入口：zotero://open-pdf/library/items/P6HRFKYQ
> 全文 Markdown：[[03fulltext/ISAC/M4EVSKTU]]

## Research Area

- Simultaneously Transmitting and Reflecting IRS (STAR-IRS)
- Sparse Code Multiple Access (SCMA)
- Integrated Sensing and Communication (ISAC)
- Terahertz (THz) Band

---

# 1. Abstract Summary（一句话总结）

> 该文研究太赫兹频段下 STAR-IRS 辅助 SCMA 的 ISAC 系统波束成形与资源分配联合优化问题（OP），同时考虑 ISAC、SCMA、波束成形、QoS 与 STAR-IRS 五类约束；该 OP 为 NP-hard，常规方法无法求解且解需具备跨情境适应能力，故采用元深度强化学习（MDRL）高效求解。

---

# 2. Research Background（研究背景）

## 背景：

- 为应对未来无线网络应用对**感知与通信性能**的双重需求，三项技术被引入：
  - **STAR-IRS**（同时透射与反射的智能反射面）
  - **SCMA**（稀疏码多址接入）
  - **ISAC**（通感一体化）

> 原文：
> "In response to growing demands for both sensing and communication performance from future applications of wireless networks, simultaneous transmitting and reflecting intelligent reflecting surface (STAR-IRS), sparse code multiple access (SCMA), and integrated sensing and communication (ISAC) have been introduced."

## Motivation（研究动机）

- 所研究的联合优化问题是 **NP-hard**，常规方法无法求解。
- 且可行解必须**具备适应不同情境的能力**（动态环境）。

> 原文：
> "The investigated OP is a type of NP-hard OP that cannot be solved by conventional methods. Moreover, the possible solution must have the ability to adapt to different situations."

## Application Scenario（应用场景）

- 太赫兹频段的 STAR-IRS 辅助 ISAC 系统
- 采用 SCMA 的多用户接入场景
- 需跨情境自适应的资源配置

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在太赫兹频段下，如何在 ISAC、SCMA、波束成形、QoS 与 STAR-IRS 五类约束下求解 NP-hard 的波束成形与资源分配联合优化问题，并使解具备跨情境适应能力？

核心问题：

- 五类约束如何统一建模？
- NP-hard 问题如何高效求解？
- 如何让解适应不同情境（泛化能力）？

---

# 4. Related Work（相关工作）

已有方法：

1. **常规优化方法**：面对 NP-hard 问题无法求解或复杂度过高。
2. **普通深度强化学习**：可解但跨情境泛化能力不足。
3. **仅反射式 IRS 的方案**：无法同时服务两侧用户。

现有不足：

- 缺少同时处理五类约束且具备跨情境适应能力的求解方案。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 研究 STAR-IRS 辅助 SCMA 的 ISAC 系统的**波束成形与资源分配联合优化问题（OP）**。
- 同时考虑五类约束：**ISAC、SCMA、波束成形、QoS、STAR-IRS**，且工作在**太赫兹（THz）频段**。
- 为高效求解该 NP-hard 问题，采用**元深度强化学习（MDRL）**。

> 原文：
> "we investigate the joint beamforming and resource allocation optimization problem (OP) for STAR-IRS-Aided SCMA for an ISAC System by considering ISAC, SCMA, beamforming, quality of service (QoS), and STAR-IRS constraints in the THz band."
>
> 原文：
> "Then to solve this problem efficiently, we employ a new meta deep reinforcement learning (MDRL"

## Model / Framework

系统模型：

- **频段**：太赫兹（THz）
- **关键技术**：STAR-IRS + SCMA + ISAC
- **优化变量**：波束成形、资源分配
- **约束**：ISAC、SCMA、波束成形、QoS、STAR-IRS
- **求解**：元深度强化学习（MDRL）

## Algorithm / Technique

采用：

- 元深度强化学习（Meta Deep Reinforcement Learning, MDRL）
- STAR-IRS 透射/反射联合设计
- SCMA 资源分配
- 波束成形优化

## Key Steps

1. 建立太赫兹频段 STAR-IRS 辅助 SCMA-ISAC 系统模型。
2. 列出五类约束（ISAC、SCMA、波束成形、QoS、STAR-IRS）。
3. 形式化为波束成形与资源分配的联合优化问题，确认为 NP-hard。
4. 采用 MDRL 求解，以获得高效且能适应不同情境的解。
5. 通过仿真验证。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **优化变量**：波束成形、资源分配
- **约束类别**：ISAC、SCMA、波束成形、QoS、STAR-IRS
- **频段**：THz
- **问题性质**：NP-hard

> 说明：各约束的具体数学形式、THz 信道模型与 MDRL 的网络/训练细节见 [[03fulltext/ISAC/M4EVSKTU]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- STAR-IRS 可同时透射与反射，服务两侧用户。
- SCMA 的码本分配可作为资源分配的优化变量。
- MDRL 能通过元学习获得跨情境的快速适应能力。

## Optimization Objective

目标：

- 在五类约束下优化 ISAC 系统的感知与通信性能，并使解可适应不同情境。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体 IRS 单元数、用户数、THz 载频与信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 感知性能
- 通信性能（含 QoS 满足）
- 求解效率
- 跨情境适应能力

## Results

主要结果：

- MDRL 能高效求解该 NP-hard 问题并适应不同情境。

> 说明：具体的性能数值与对比增益未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/M4EVSKTU]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 把 STAR-IRS、SCMA 与 ISAC 三项技术组合，并置于 THz 频段研究。
2. 同时考虑五类约束的波束成形与资源分配联合优化。
3. 确认该问题为 NP-hard 且需具备跨情境适应能力。
4. 采用 MDRL 求解。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- STAR-IRS + SCMA + ISAC + THz 的组合面向未来高容量感知通信需求，是前瞻性的场景设定。
- 元学习（meta-learning）解决了普通 DRL 跨情境泛化不足的问题。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 技术组合完整且有前瞻性（THz + STAR-IRS + SCMA + ISAC）。
- 但方法层面是既有技术的组合应用（MDRL 求解 NP-hard），且与本 Vault 主线（UAV/ISAC 的波形与轨迹）距离较远。
- 与 [[02vault/ISAC/Learning to Beamform for ISAC (GNN)|GNN 波束成形]] 形成对照：该文用 GNN，本文用 MDRL。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅仿真章节。
2. 仿真验证，无实测。
3. THz 频段的实际信道损伤（如分子吸收）需更细致建模。

未来可能改进：

- 在真实 THz 平台上验证。
- 细化 THz 信道模型。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- STAR-IRS 相对传统反射式 IRS 的优势：可同时服务两侧（透射+反射），覆盖更完整。
- 多技术组合（IRS + 多址 + ISAC）是 6G 研究的典型形态，但组合越多、优化越难（NP-hard 常见）。
- 元学习用于解决 DRL 的跨情境泛化问题是合理的思路。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 ISAC 方向相关，但偏 IRS/多址，与 UAV 主线距离较远。
- 与 [[02vault/ISAC/Learning to Beamform for ISAC (GNN)|GNN 波束成形]] 可对比不同学习方法在 ISAC 资源分配上的表现。

## Possible Ideas

可能的新想法：

- 对比 MDRL 与 GNN 在 ISAC 资源分配上的样本效率与适应性。
- 探索 STAR-IRS 在 UAV 场景中的应用（UAV 载 STAR-IRS）。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/ISAC/Learning to Beamform for ISAC (GNN)|GNN 波束成形]] — 同属 ISAC 学习化资源分配，该文用 GNN，本文用 MDRL
- [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]] — 同涉 IRS/反射面，该文面向 UAV 低空

---

# 13. Summary Card（快速复习）

## Problem

> THz 频段下 STAR-IRS 辅助 SCMA 的 ISAC 系统联合优化含五类约束，为 NP-hard 且需跨情境适应。

## Method

> 形式化波束成形与资源分配联合优化问题，采用元深度强化学习（MDRL）求解。

## Result

> 高效求解并获得可适应不同情境的解（具体数值见全文仿真章节）。

## Importance

> 提供了 THz + STAR-IRS + SCMA + ISAC 组合场景下的可行求解路径。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 THz 频段 STAR-IRS 辅助 SCMA-ISAC 系统中五类约束下 NP-hard 的联合优化问题。

Q:
核心方法是什么？

A:
形式化为波束成形与资源分配联合优化问题，用元深度强化学习（MDRL）求解。

Q:
最大贡献是什么？

A:
在 THz + STAR-IRS + SCMA + ISAC 组合场景下给出 NP-hard 问题的 MDRL 求解方案。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `M4EVSKTU`，PDF 附件 `P6HRFKYQ`。
- PDF 经 pypdf 提取全文（90514 字符），原文引用均取自全文 Markdown [[03fulltext/ISAC/M4EVSKTU]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 五类约束的数学形式、THz 信道模型与 MDRL 细节未在当前材料中逐项定位，已在正文如实标注，未做推测。