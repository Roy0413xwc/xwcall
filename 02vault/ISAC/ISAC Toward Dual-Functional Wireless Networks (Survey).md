---
title: "Integrated Sensing and Communications: Toward Dual-Functional Wireless Networks for 6G and Beyond"
aliases:
  - ISAC 综述
  - Dual-functional 6G
tags:
  - literature-note
  - reading-note
  - ISAC
  - 综述
created: 2026-10-13
source: IEEE Journal on Selected Areas in Communications, 2022
author: Fan Liu, Yuanhao Cui, Christos Masouros, Jie Xu, Tony Xiao Han, Yonina C. Eldar, Stefano Buzzi
year: 2022
journal: IEEE Journal on Selected Areas in Communications

theme: ISAC 领域的奠基性综述——背景、应用、S&C 权衡、信号处理与未来愿景
study_area: 通感一体化 / 6G / 波形设计与接收处理
methodology: 综述（历史脉络 + 信息论极限 + 物理层权衡 + 跨层设计 + 信号处理）
core_variable: S&C 性能权衡、信息论极限、波形设计、接收信号处理
key_finding: 系统梳理 ISAC 的背景、关键应用与 SOTA 方法，分析从信息论极限到物理层、跨层的多重权衡，并给出波形与接收处理的技术图景
relevance: ISAC 领域的入门与纲领性文献，是本 Vault ISAC 方向的必读基石

type: literature-note
zotero_key: "M92ZFKEN"
pdf_key: "4FBXFUUM"
doi: "10.1109/jsac.2022.3156632"
collection: "ISAC"
note_path: "02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey).md"
fulltext_path: "03fulltext/ISAC/M92ZFKEN.md"
status:
  - Reading
rating: 五星
---

# Integrated Sensing and Communications: Toward Dual-Functional Wireless Networks for 6G and Beyond

---

# 📌 Basic Information（基本信息）

## Author
Fan Liu, Yuanhao Cui, Christos Masouros, Jie Xu, Tony Xiao Han, Yonina C. Eldar, Stefano Buzzi

## Year
2022

## Source
IEEE Journal on Selected Areas in Communications｜DOI: 10.1109/jsac.2022.3156632

> Zotero 入口：zotero://select/library/items/M92ZFKEN
> PDF 入口：zotero://open-pdf/library/items/4FBXFUUM
> 全文 Markdown：[[03fulltext/ISAC/M92ZFKEN]]

## Research Area

- Integrated Sensing and Communications (ISAC)
- 6G Radio Access Network
- Perceptive Networks
- ISAC Waveform and Receiver Design

---

# 1. Abstract Summary（一句话总结）

> 该文是 ISAC 领域的奠基性综述：从历史视角梳理感知与通信的交织关系，全面覆盖 ISAC 的背景、关键应用与前沿方法，分析从信息论极限、物理层性能到跨层设计的多重 S&C 权衡，并讨论波形设计与接收信号处理，最后给出深度融合的未来愿景。

---

# 2. Research Background（研究背景）

## 背景：

- 在 5G 标准逐步固化之际，研究者开始展望 6G。
- 集成感知功能正成为 6G 无线接入网（RAN）的关键特征，使得利用 5G 密集小区基础设施构建「感知网络（perceptive network）」成为可能。

> 原文：
> "As the standardization of 5G is being solidified, researchers are speculating what 6G will be. Integrating sensing functionality is emerging as a key feature of the 6G Radio Access Network (RAN), allowing to exploit the dense cell infrastructure of 5G for constructing a perceptive network."

## Motivation（研究动机）

- ISAC 涉及面广（背景、应用、方法、权衡、标准化），缺少一篇系统性的纲领文献。
- 工业界与标准化活动需要统一的术语与问题框架。

## Application Scenario（应用场景）

- 6G 感知网络（perceptive network）
- 利用蜂窝基础设施实现的广域感知
- 车联网、低空经济、工业互联网中的通感一体服务

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何系统梳理 ISAC 的全景——背景与历史脉络、关键应用与 SOTA 方法、从信息论到跨层的多重权衡、波形与接收处理技术，并指明未来方向？

核心问题：

- 感知与通信的关系在历史上如何演变？
- S&C 之间存在哪些层次的性能权衡？
- ISAC 的波形设计与接收信号处理有哪些技术路径？
---

# 4. Related Work（相关工作）

本文为综述，覆盖的相关方向包括：

1. **感知与通信的历史交织**：从历史视角讨论 S&C 的相互影响。
2. **ISAC 的应用场景**：在研与潜在用例。
3. **产业进展与标准化活动**：与 ISAC 相关的工业与标准动态。
4. **性能权衡研究**：信息论极限、物理层性能、跨层设计三个层面。
5. **信号处理**：ISAC 波形设计与接收信号处理。

> 原文：
> "We commence by discussing the interplay between sensing and communications (S&C) from a historical point of view, and then consider multiple facets of ISAC and its performance gains."
>
> 原文：
> "We analyze a number of performance tradeoffs between S&C, spanning from information theoretical limits, tradeoffs in physical layer performance, to the tradeoff in cross-layer designs."

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想（综述的组织逻辑）：

- **历史脉络**：先讨论感知与通信的交织关系。
- **多面刻画**：进而考虑 ISAC 的多个侧面及其性能增益。
- **应用与标准化**：通过引入在研与潜在用例，阐明产业进展与标准化活动。
- **权衡分析**：分析从信息论极限到物理层、再到跨层的 S&C 性能权衡。
- **信号处理**：讨论 ISAC 波形设计与接收信号处理。
- **未来愿景**：进一步给出对深度融合的展望。

> 原文：
> "Next, we discuss signal processing aspects of ISAC, namely ISAC waveform design and receive signal processing. As a step further, we provide our vision on the deepe"

## Model / Framework

综述框架：

- **层次一：历史与背景**——S&C 的交织演进
- **层次二：应用与标准化**——用例、产业进展、标准活动
- **层次三：性能权衡**——信息论极限 / 物理层 / 跨层
- **层次四：信号处理**——波形设计 / 接收处理
- **层次五：愿景**——深度融合的未来方向

## Key Steps

作为综述，本文的阅读路径建议：

1. 先读历史脉络部分，建立 S&C 关系的认知框架。
2. 再看应用场景与标准化现状，了解落地进展。
3. 重点研读三个层次的权衡分析（信息论 / 物理层 / 跨层）。
4. 按需查阅波形设计与接收处理的技术细节。
5. 结合未来愿景部分思考自己的研究方向定位。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- 综述涉及的理论要素包括：
  - **信息论极限**：S&C 在信息论层面的基本界限
  - **物理层性能权衡**：如速率 vs 估计精度（CRB）
  - **跨层设计权衡**：物理层之上的资源调度与网络层考量

> 说明：本文为综述，具体的定理、闭式表达与推导分散在各章节，以 [[03fulltext/ISAC/M92ZFKEN]] 原文为准，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设（综述的视角前提）：

- 6G RAN 将把感知作为原生特性。
- 5G 的密集小区基础设施可被复用于感知。
- S&C 可共享频谱与硬件，并通过一体化设计获得增益。

## Optimization Objective

目标（综述意义下）：

- 为 ISAC 领域建立统一的问题框架、术语体系与研究路线图。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 本文为综述，不含独立实验；其「验证」体现在对既有工作与标准化进展的系统梳理。

## Baseline

比较方法：

- 综述覆盖的各类 SOTA 方法（波形设计、接收处理等的已有方案），具体对比见原文各章节。

## Metrics

评价指标：

- 综述涉及的 S&C 性能指标（如通信速率、感知精度/CRB、频谱与能量效率）

## Results

主要贡献性结论：

- 系统梳理了 ISAC 的背景、关键应用与 SOTA 方法。
- 揭示了从信息论极限到物理层、跨层设计的多重 S&C 权衡。
- 给出 ISAC 波形设计与接收信号处理的技术图景。
- 提出对 S&C 深度融合的未来愿景。

> 原文：
> "In this paper, we provide a comprehensive overview on the background, range of key applications and state-of-the-art approaches of Integrated Sensing and Communications (ISAC)."

> 说明：综述中的具体数值对比需查阅各章节原文，此处不做引述。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 从历史视角梳理感知与通信的交织关系，为 ISAC 建立认知框架。
2. 全面覆盖 ISAC 的背景、关键应用范围与 SOTA 方法。
3. 通过引入在研与潜在用例，阐明产业进展与标准化活动。
4. 分析三个层面的 S&C 性能权衡：信息论极限、物理层性能、跨层设计。
5. 讨论 ISAC 信号处理（波形设计 + 接收处理），并给出深度融合的未来愿景。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 把感知作为 6G RAN 的原生特性，并利用 5G 密集小区基础设施构建感知网络，是 ISAC 的核心机遇。
- 三重权衡（信息论 / 物理层 / 跨层）是理解 ISAC 设计空间的骨架。

## My Evaluation

我的评价：

五星

创新程度：

高（纲领性贡献）

理由：

- 本文是 ISAC 领域被引用最广的奠基性综述之一，作者阵容权威（含 Eldar、Buzzi 等）。
- 三重权衡的分析框架（信息论 / 物理层 / 跨层）至今仍是理解 ISAC 的标准视角。
- 对本 Vault 而言，是建立 ISAC 整体认知的必读文献。

---

# 10. Limitation（不足）

论文不足：

1. 作为 2022 年的综述，未覆盖此后（2023+）的快速进展（如近场 ISAC、AI 原生 ISAC）。
2. 综述性质决定了技术细节的深度有限，具体实现需查原始文献。
3. 对标准化活动的描述随标准演进而变化。

未来可能改进：

- 结合 2023 年后的新进展（近场通信、可重构天线、AI 驱动 ISAC）做补充阅读。
- 按自己的研究方向（如 UAV-ISAC）深入查阅对应章节引用的原始工作。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- ISAC 的机遇本质：复用已密集部署的蜂窝基础设施来做感知，边际成本低。
- S&C 权衡存在于三个层次——信息论极限（能不能）、物理层（好不好）、跨层（用不用得起），缺一不可。
- 波形设计与接收处理是 ISAC 落地的两大技术抓手。
- 感知与通信并非 2020 年后才交汇，历史上二者长期交织演进。

## Connection With My Work

和我的研究/项目关系：

- 是本 Vault ISAC 方向的纲领性文献，可作为整体认知的入口。
- 三重权衡框架可用于定位自己工作处于哪个层次的问题。
- 与 [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] 等具体工作形成「总—分」关系。

## Possible Ideas

可能的新想法：

- 按本文的三重权衡框架，梳理本 Vault 已有 ISAC 笔记各自解决的是哪个层次的权衡。
- 针对 UAV-ISAC 场景，补充本文未覆盖的近场/移动性议题。
- 以本文为纲，建立本 Vault 的 ISAC 知识页（theme）。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文（本文可作为这些工作的纲领）：

- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]]
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]]
- [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]]
- [[02vault/ISAC/ISAC for Low-Altitude Economy DRL|DeepLSC 低空经济]]

---

# 13. Summary Card（快速复习）

## Problem

> ISAC 涉及面广但缺少系统性纲领文献，术语与研究框架尚未统一。

## Method

> 综述：历史脉络 → 应用与标准化 → 三重权衡（信息论/物理层/跨层）→ 信号处理 → 未来愿景。

## Result

> 建立了 ISAC 的统一认知框架与路线图，成为该领域被广泛引用的奠基性文献。

## Importance

> 确立「把感知作为 6G RAN 原生特性」的定位，并以三重权衡骨架刻画了 ISAC 的设计空间。

## Flash Card

Q:
这篇论文解决什么问题？

A:
为快速发展的 ISAC 领域提供系统性的综述与统一框架（背景、应用、权衡、信号处理、愿景）。

Q:
核心内容是什么？

A:
历史脉络 + 应用与标准化 + 三重权衡（信息论极限 / 物理层 / 跨层）+ 波形与接收处理。

Q:
最大贡献是什么？

A:
确立 ISAC 作为 6G RAN 原生特性的定位，并以三重权衡框架刻画其设计空间。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `M92ZFKEN`，PDF 附件 `4FBXFUUM`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文（215627 字符，篇幅完整）。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/M92ZFKEN]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 本文为综述，具体数值对比与定理见原文各章节，此处未逐项引述。