---
title: "Integrated Sensing and Communications in Multi-UAV Networks: A Dual-Objective Optimization Perspective"
aliases:
  - 多无人机双目标优化
  - Multi-UAV ISAC
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - 双目标优化
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2026
author: (PDF 首页作者行未在当前全文提取中定位)
year: 2026
journal: IEEE Transactions on Wireless Communications

theme: 在独立多用户多目标的通用多无人机网络中，用双目标模型优化 ISAC 以避免性能损失与优化偏置
study_area: 通感一体化 / 多无人机网络 / 多目标优化
methodology: 双目标建模 + 无人机间干扰管理 + 轨迹/用户关联/目标关联/功率控制联合优化
core_variable: 通信性能、感知性能、无人机间干扰、轨迹与关联、功率控制
key_finding: 单目标与加权优化会造成性能损失与优化偏置，双目标模型可获得更好的 ISAC 权衡
relevance: 多 UAV ISAC 的双目标建模，与本 Vault 方向对口，对「如何权衡」这一核心问题有方法论价值

type: literature-note
zotero_key: "EW3FZDE2"
pdf_key: "GCRNXBN0"
doi: "10.1109/twc.2025.3641375"
collection: "ISAC"
note_path: "02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization.md"
fulltext_path: "03fulltext/ISAC/EW3FZDE2.md"
status:
  - Reading
rating: 五星
---

# Integrated Sensing and Communications in Multi-UAV Networks: A Dual-Objective Optimization Perspective

---

# 📌 Basic Information（基本信息）

## Author
PDF 首页作者行未在当前全文提取中定位，建议以 Zotero 条目或 PDF 首页为准

## Year
2026

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/twc.2025.3641375

> Zotero 入口：zotero://select/library/items/EW3FZDE2
> PDF 入口：zotero://open-pdf/library/items/GCRNXBN0
> 全文 Markdown：[[03fulltext/ISAC/EW3FZDE2]]

## Research Area

- Integrated Sensing and Communications (ISAC)
- Multi-UAV Networks
- Dual-Objective Optimization
- Interference Management

---

# 1. Abstract Summary（一句话总结）

> 该文研究更通用的多无人机 ISAC 网络：存在相互独立的多个通信用户与多个感知目标，无人机为用户提供下行通信同时感知目标；考虑无人机间复杂的干扰管理，并指出单目标与加权优化可能导致性能损失与优化偏置，因而提出双目标模型以获得更好的 ISAC 权衡。

---

# 2. Research Background（研究背景）

## 背景：

- ISAC 在下一代无线网络中日益重要。
- 借助无人机可靠的视距（LoS）链路与机动性，UAV 辅助 ISAC 受到广泛关注。

> 原文：
> "Integrated sensing and communications (ISAC) has become increasingly crucial in next-generation wireless networks. Leveraging the reliable line-of-sight (LoS) links and mobility of unmanned aerial vehicles (UAVs), UAV-assisted ISAC has attracted significant attention."

## Motivation（研究动机）

- 既有 UAV-ISAC 场景多为「单目标」或「用户与目标重叠」，未覆盖**用户与目标相互独立**的通用情形。
- 无人机间的干扰管理未被充分考虑，影响网络实用性。
- **单目标与加权优化方法可能造成性能损失与优化偏置**。

> 原文：
> "Different from the previous UAV-ISAC scenarios with single target or overlapping users and targets, we investigate ISAC in a more general multi-UAV network with independent multiple communication users and multiple sensing targets"
>
> 原文：
> "since the existing single-objective and weighted optimization approaches may result in potential performance loss and optimization biases, we propose a dual-objective model to further optimize ISAC, aiming for a better trade"

## Application Scenario（应用场景）

- 多无人机协同的 ISAC 网络
- 通信用户与感知目标分离的业务场景
- 需管理机间干扰的密集无人机部署

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在用户与目标相互独立、且存在机间干扰的通用多无人机网络中，如何通过双目标优化获得更好的 ISAC 权衡，同时联合确定轨迹、用户关联、目标关联与功率控制？

核心问题：

- 单目标/加权优化的「优化偏置」具体如何产生、如何避免？
- 无人机间干扰如何建模与管理？
- 轨迹、双重关联与功率的联合问题如何求解？
---

# 4. Related Work（相关工作）

已有方法：

1. **单目标 UAV-ISAC**：把通信或感知之一作为目标、另一作为约束，存在偏置。
2. **加权和优化 UAV-ISAC**：权重需人工设定，可能带来性能损失。
3. **单目标或用户/目标重叠的场景设定**：未覆盖用户与目标独立的通用情形。
4. **忽略机间干扰的工作**：实用性受限。

现有不足：

- 单目标与加权优化会导致潜在的性能损失与优化偏置。
- 缺少对独立多用户/多目标与机间干扰的联合考虑。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 在更通用的多无人机网络中研究 ISAC：**多个独立通信用户 + 多个独立感知目标**。
- 无人机为下行用户提供通信，同时感知目标；并考虑无人机之间复杂的干扰管理以提升实用性。
- 针对单目标/加权优化的偏置问题，提出**双目标（dual-objective）模型**来进一步优化 ISAC，以获得更好的权衡。
- 联合优化：无人机轨迹、用户关联、目标关联、功率控制。

> 原文：
> "the UAVs provide downlink communications to the users while sensing the targets. Additionally, we consider the complicated interference management among the UAVs to further enhance the network’s practicality. Such a scenario presents a new challenge for the joint optimization problem in terms of the UAV trajectories, the user association, the target association, and the power control."

## Model / Framework

系统模型：

- **网络**：多无人机（multi-UAV）
- **用户**：多个**独立**通信用户（下行）
- **目标**：多个**独立**感知目标
- **干扰**：无人机之间存在复杂干扰，需管理
- **优化变量**：无人机轨迹、用户关联、目标关联、功率控制

## Algorithm / Technique

采用：

- 双目标优化模型（dual-objective model）
- 无人机间干扰管理
- 联合优化（轨迹 + 用户关联 + 目标关联 + 功率控制）

## Key Steps

1. 建立独立多用户 + 独立多目标的多无人机 ISAC 网络模型。
2. 建模无人机间的干扰，将其纳入网络实用性考量。
3. 指出单目标与加权优化可能导致的性能损失与优化偏置。
4. 构造双目标优化模型以同时刻画通信与感知目标。
5. 联合求解无人机轨迹、用户关联、目标关联与功率控制。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **双目标模型**：同时以通信性能与感知性能为目标（而非把一侧降为约束或做加权求和）。
- **优化变量**：无人机轨迹、用户关联、目标关联、功率控制。
- **干扰项**：无人机间干扰被显式建模。

> 说明：双目标模型的具体形式（如 Pareto 前沿求解、标量化方法）与干扰项的闭式表达见 [[03fulltext/ISAC/EW3FZDE2]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 通信用户与感知目标相互独立（不重叠）。
- 无人机间干扰可建模并可通过对关联与功率的控制加以管理。
- 双目标模型能得到比加权和更均衡的权衡解。

## Optimization Objective

目标：

- 在管理机间干扰的同时，获得通信与感知性能之间更好的权衡。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体无人机数量、用户与目标数量、场景尺度未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 单目标优化方法
- 加权和优化方法

> 说明：论文明确指出与单目标/加权优化对照，但基线具体名称未在当前材料中逐一定位，此处不做推测。

## Metrics

评价指标：

- 通信性能（用户速率等）
- 感知性能（目标估计精度等）
- 权衡质量（是否避免偏置）
- 干扰管理水平

## Results

主要结果：

- 所提算法（SC-DO-MUOA）在**通信与感知两方面均优于多种基线方法**。

> 原文：
> "Simulation results demonstrate that our proposed SC-DO-MUOA outperforms various baselines in both communication and sensing performance." 

> 说明：具体的性能改善数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/EW3FZDE2]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 研究更通用的多无人机 ISAC 场景：多个独立通信用户 + 多个独立感知目标。
2. 考虑无人机间复杂的干扰管理，提升网络实用性。
3. 指出单目标与加权优化可能导致性能损失与优化偏置。
4. 提出双目标模型以进一步优化 ISAC，获得更好的权衡。
5. 联合优化无人机轨迹、用户关联、目标关联与功率控制。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 「用户与目标独立」是比「单目标/重叠」更通用也更真实的设定。
- 加权和的本质缺陷是权重人为设定会引入偏置，双目标模型可避免这一点。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 对「加权和偏置」的批评切中了 ISAC 建模的普遍问题，双目标建模是有价值的方法论改进。
- 场景设定（独立多用户多目标 + 机间干扰）比多数工作更完整。
- 但需注意：双目标最终仍需标量化或求 Pareto 解，是否真正优于精心调参的加权和，需看仿真证据。

---

# 10. Limitation（不足）

论文不足：

1. 论文作者行未在当前文本提取中定位，元数据完整性有缺口。
2. 仿真验证，无实测。
3. 双目标模型的求解复杂度需评估（尤其大规模网络）。
4. 量化收益需查阅仿真章节。

未来可能改进：

- 给出双目标求解的计算复杂度分析。
- 与精心调参的加权和方法做公平对比。
- 扩展到时变场景与在线求解。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **加权和的偏置问题是真实的**：权重决定了解落在 Pareto 前沿的哪个位置，而这个选择往往缺乏依据。
- 双目标/多目标建模把「选择权」显式化，是更诚实也更灵活的建模方式。
- 无人机间干扰在多机部署中不可忽视，直接影响网络实用性。
- 「用户与目标是否重叠」是一个容易被忽略但影响问题结构的设定差异。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向对口，双目标视角对「如何权衡」有直接方法论价值。
- 可与采用加权和的 [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] 做对比研究：检验双目标是否真的更优。
- 干扰管理可纳入自己的多 UAV ISAC 设计。

## Possible Ideas

可能的新想法：

- 复现本文双目标方法与加权和方法，定量检验「优化偏置」的实际大小。
- 把双目标建模引入 UAV-ISAC 的轨迹—波束联合设计。
- 研究时变场景下的在线双目标求解。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同属 UAV-ISAC 权衡，该文用归一化加权和，本文批评该方法并改用双目标
- [[02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)|ISAC 综述]] — 本方向的纲领性综述

---

# 13. Summary Card（快速复习）

## Problem

> 既有 UAV-ISAC 多为单目标或用户/目标重叠设定；单目标与加权优化会造成性能损失与优化偏置。

## Method

> 在独立多用户 + 独立多目标的通用多无人机网络中，引入机间干扰管理，并用双目标模型联合优化轨迹、双重关联与功率控制。

## Result

> 双目标模型获得比单目标/加权优化更好的 ISAC 权衡（具体数值见全文仿真章节）。

## Importance

> 指出并试图修正 ISAC 建模中普遍存在的「加权和偏置」问题，具有方法论价值。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决通用多无人机 ISAC 网络（独立多用户多目标 + 机间干扰）中，单目标/加权优化导致性能损失与偏置的问题。

Q:
核心方法是什么？

A:
双目标优化模型 + 无人机间干扰管理 + 联合优化轨迹、用户关联、目标关联与功率控制。

Q:
最大贡献是什么？

A:
指出加权和方法的偏置缺陷，并用双目标模型在更通用的多 UAV 场景中获得更好的 ISAC 权衡。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `EW3FZDE2`，PDF 附件 `GCRNXBN0`。
- PDF 由用户提供（本地 Downloads 目录），经 pypdf 提取全文（83348 字符）。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/EW3FZDE2]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- **作者行缺失**：PDF 首页作者信息未在当前文本提取中定位，已如实标注。
- 双目标模型的具体形式与量化仿真数值未在当前材料中定位，已在正文如实标注，未做推测。