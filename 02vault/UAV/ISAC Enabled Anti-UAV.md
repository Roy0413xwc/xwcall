---
title: "ISAC Enabled Anti-UAV: Joint Beamforming and Trajectory Design for Multi-UAVs"
aliases:
  - ISAC 反无人机
  - Anti-UAV
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - 低空安全
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2026
author: Xiaojie Wang, Lingfei Li, Zhaolong Ning, Xiaoming Tao, Tie Qiu, Lei Guo, Yan Zhang
year: 2026
journal: IEEE Transactions on Wireless Communications

theme: 用协同无人机群的 ISAC 能力实现反无人机（anti-UAV）的持续感知与可靠定位
study_area: 通感一体化 / 低空安全 / 反无人机
methodology: 空—空传输中断概率约束下推导最优发射功率 + 感知 FIM/CRB 推导 + 长期 CRB 最小化的鲁棒优化
core_variable: 长期 CRB、发射功率、收发波束成形、关联、目标位置不确定性、中断概率
key_finding: 仅依靠协同无人机（无地面固定基站）实现反无人机，在目标位置不确定性下推导 CRB 并做长期最小化
relevance: 低空安全 + UAV-ISAC 协同，与本 Vault 方向对口，且覆盖「非 cooperative 目标」这一新设定

type: literature-note
zotero_key: "BMZJYWHN"
pdf_key: "YR2IGAYU"
doi: "10.1109/twc.2026.3707705"
collection: "UAV"
note_path: "02vault/UAV/ISAC Enabled Anti-UAV.md"
fulltext_path: "03fulltext/UAV/BMZJYWHN.md"
status:
  - Reading
rating: 五星
---

# ISAC Enabled Anti-UAV: Joint Beamforming and Trajectory Design for Multi-UAVs

---

# 📌 Basic Information（基本信息）

## Author
Xiaojie Wang, Lingfei Li, Zhaolong Ning, Xiaoming Tao, Tie Qiu, Lei Guo, Yan Zhang

## Year
2026

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/twc.2026.3707705

> Zotero 入口：zotero://select/library/items/BMZJYWHN
> PDF 入口：zotero://open-pdf/library/items/YR2IGAYU
> 全文 Markdown：[[03fulltext/UAV/BMZJYWHN]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- Anti-UAV / Low-Altitude Airspace Security
- Cooperative Multi-UAV Sensing
- Robust Beamforming and Trajectory Optimization

---

# 1. Abstract Summary（一句话总结）

> 该文提出仅依靠协同无人机的 ISAC 反无人机方案：先在空—空传输中断概率容限约束下推导最优发射功率，再计入目标无人机的位置不确定性推导感知 Fisher 信息矩阵与 CRB，进而构造长期 CRB 最小化问题，并设计鲁棒算法联合优化收发波束成形与关联等变量。

---

# 2. Research Background（研究背景）

## 背景：

- 无人机（UAV）的快速普及给低空空域安全带来重大挑战，尤其是未经授权的入侵。
- ISAC 已成为反无人机系统的关键使能技术。

> 原文：
> "The rapid proliferation of Uncrewed Aerial Vehicles (UAVs) introduces significant challenges to low-altitude airspace security, particularly from unauthorized intrusions. To address these vulnerabilities, Integrated Sensing and Communication (ISAC) has emerged as a key enabler for anti-UAV systems."

## Motivation（研究动机）

- 现有研究聚焦于**固定基站**的蜂窝网络，不适用于目标无人机的持续移动，因而无法满足「灵活感知 + 可靠定位」的双重需求。
- 目标位置存在不确定性，使感知性能的刻画与优化更为复杂。

> 原文：
> "existing studies focusing on cellular networks with fixed base stations are ill-suited for the continuous movement of target UAVs, thus failing to meet the dual demands of flexible sensing and reliable positioning."

## Application Scenario（应用场景）

- 低空空域安全与反入侵监测
- 协同无人机群对非合作目标的持续跟踪定位
- 无地面基础设施依赖的快速部署安防

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在不依赖地面固定基站的情况下，仅用协同无人机群对持续移动的目标无人机实现灵活感知与可靠定位？

核心问题：

- 空—空链路的中断概率如何约束发射功率设计？
- 目标位置不确定性如何进入感知 FIM 与 CRB 的推导？
- 长期（多时刻）CRB 最小化的 NP-hard 问题如何求解？

---

# 4. Related Work（相关工作）

已有方法：

1. **固定基站的蜂窝 ISAC 反无人机**：位置固定，无法跟随移动目标。
2. **单目标或用户/目标重叠的 UAV-ISAC 场景**：设定较简单，未覆盖多目标独立情形。
3. **未考虑位置不确定性的感知优化**：CRB 推导过于理想。

现有不足：

- 固定基站不适于目标持续移动。
- 缺少对目标位置不确定性的显式建模。
- 缺少长期（而非单时刻）的感知性能优化。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出**仅基于协同无人机**的 ISAC 反无人机方案（不依赖地面固定基站）。
- 三步推进：先在中断概率约束下求最优功率 → 再推导含位置不确定性的感知 FIM 与 CRB → 最后做长期 CRB 最小化的鲁棒联合优化。

> 原文：
> "we propose an ISAC-enabled anti-UAV scheme solely based on cooperative UAVs. Specifically, we first derive the optimal transmit power under the constraint of space-air transmission outage probability tolerance. Subsequently, we deduce the sensing Fisher information matrix and Cramér-Rao Bound (CRB) by incorporating the position uncertainty of the target UAV."

## Model / Framework

系统模型：

- **感知方**：协同无人机群（cooperative UAVs），无地面固定基站
- **目标**：非合作/未授权的目标 UAV，位置具有不确定性
- **链路**：空—空（space-air）传输，存在中断概率
- **优化变量**：发射功率、收发波束成形、关联（association）等

## Algorithm / Technique

采用：

- 空—空传输中断概率建模与最优发射功率推导
- 感知 Fisher 信息矩阵（FIM）与 CRB 推导（含目标位置不确定性）
- 长期 CRB 最小化问题建模
- 鲁棒优化算法（联合优化收发波束成形与关联等）

## Key Steps

1. 建立协同无人机反无人机 ISAC 系统模型。
2. 在空—空传输中断概率容限约束下，推导最优发射功率。
3. 把目标 UAV 的位置不确定性纳入，推导感知 FIM 与 CRB。
4. 构造长期（long-term）CRB 最小化问题以增强协同感知性能。
5. 针对该 NP-hard 问题，设计鲁棒优化算法联合优化收发波束成形与关联等变量。

> 原文：
> "Then, we formulate a long-term CRB minimization problem to enhance cooperative sensing performance. To tackle this NP-hard problem, we design a robust optimization algorithm that jointly optimizes transmit-receive beamforming, associ"
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **功率约束**：空—空传输的中断概率（outage probability）需低于容限，据此推导最优发射功率。
- **感知度量**：Fisher 信息矩阵（FIM）与 Cramér-Rao 界（CRB），且**显式计入目标 UAV 的位置不确定性**。
- **优化目标**：长期（long-term）CRB 最小化，而非单时刻优化。
- **优化变量**：收发波束成形、关联（association）等。
- **问题性质**：NP-hard。

> 说明：中断概率的闭式表达、含位置不确定性的 FIM/CRB 推导与鲁棒算法的具体步骤见 [[03fulltext/UAV/BMZJYWHN]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 协同无人机之间可共享感知信息与通信链路。
- 目标 UAV 的位置可建模为带有不确定性的随机变量。
- 空—空链路的中断概率可解析表征并作为功率约束。

## Optimization Objective

目标：

- 在功率与中断约束下，通过长期 CRB 最小化提升对移动目标 UAV 的协同感知与定位性能。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体无人机数量、场景尺度与信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 长期 CRB（感知/定位精度）
- 空—空传输中断概率
- 发射功率效率

## Results

主要结果：

- 推导了中断概率容限下的最优发射功率。
- 推导了含目标位置不确定性的感知 FIM 与 CRB。
- 设计了鲁棒算法求解长期 CRB 最小化的 NP-hard 问题。

> 说明：具体的 CRB 改善幅度与对比数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/BMZJYWHN]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出固定基站方案不适用于持续移动的目标 UAV，提出仅基于协同无人机的 ISAC 反无人机方案。
2. 在空—空传输中断概率容限约束下推导最优发射功率。
3. 把目标 UAV 的位置不确定性纳入感知 FIM 与 CRB 的推导，使感知度量更贴近实际。
4. 构造长期 CRB 最小化问题并设计鲁棒算法联合优化收发波束成形与关联。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 用「协同无人机」替代「固定基站」是适配移动目标的关键架构选择。
- 把目标位置不确定性显式纳入 CRB 推导，是相对理想化 CRB 分析的实质改进。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 问题设定（非合作移动目标 + 无地面设施）贴近低空安防的真实需求。
- 「长期 CRB 最小化」比单时刻优化更符合跟踪任务的本质。
- 位置不确定性进入 CRB 推导，是方法论上的严谨之处。

- 局限：量化收益需查阅仿真章节。

---

# 10. Limitation（不足）

论文不足：

1. 仿真验证，无实测或硬件在环。
2. 未考虑无人机自身能耗对长期任务的约束。
3. 目标机动模型较简单时，位置不确定性的建模优势可能被高估。
4. 量化收益需查阅仿真章节。

未来可能改进：

- 纳入能耗与续航约束做长期任务规划。
- 在真实反无人机场景中验证。
- 研究更强机动目标下的自适应跟踪策略。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 反无人机场景的核心约束是「目标会跑」——固定基站天然不适应，移动平台（协同无人机）是对症架构。
- 感知性能评估不能假设目标位置已知；把位置不确定性纳入 FIM/CRB 才贴近实际。
- 「长期 CRB」而非瞬时 CRB，是跟踪类问题应选的优化目标。
- 空—空链路的中断概率可作为功率分配的有效约束。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向对口，补充了「非合作目标 + 无地面设施」这一新设定。
- 长期 CRB 最小化的建模思路可迁移到自己的 UAV 目标跟踪问题。
- 与 [[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO 协同 ISAC]] 形成对照：该文用 MARL，本文用鲁棒优化。

## Possible Ideas

可能的新想法：

- 对比本文的鲁棒优化与 C-HAPPO 的 MARL 在同一反无人机场景下的表现。
- 把能耗约束加入长期 CRB 最小化，研究任务时长与精度的权衡。
- 研究目标采用对抗性机动（规避感知）时的跟踪策略。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO 协同 ISAC]] — 同属多 UAV 协同 ISAC，该文用 MARL，本文用鲁棒优化
- [[02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)|ISAC 综述]] — 本方向的纲领性综述

---

# 13. Summary Card（快速复习）

## Problem

> 固定基站 ISAC 反无人机方案不适用于持续移动的目标 UAV，且目标位置不确定性使感知优化复杂化。

## Method

> 仅用协同无人机：中断概率约束下推最优功率 → 含位置不确定性的 FIM/CRB 推导 → 长期 CRB 最小化的鲁棒联合优化。

## Result

> 实现了面向移动目标 UAV 的协同感知与定位（具体 CRB 改善见全文仿真章节）。

## Importance

> 把反无人机 ISAC 从「固定基站」推进到「协同移动平台」，并把位置不确定性纳入感知度量。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决固定基站 ISAC 反无人机方案无法跟随移动目标、且目标位置不确定性难以刻画的问题。

Q:
核心方法是什么？

A:
仅用协同无人机：中断概率约束下的最优功率 + 含位置不确定性的 FIM/CRB + 长期 CRB 最小化鲁棒优化。

Q:
最大贡献是什么？

A:
提出无地面设施依赖的协同无人机反无人机 ISAC 方案，并把目标位置不确定性显式纳入感知 CRB 推导。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `BMZJYWHN`，PDF 附件 `YR2IGAYU`。
- PDF 由用户提供（本地 Downloads 目录），经 pypdf 提取全文（86624 字符）。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/BMZJYWHN]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 中断概率闭式表达、FIM/CRB 推导细节与量化仿真数值未在当前材料中逐项定位，已在正文如实标注，未做推测。