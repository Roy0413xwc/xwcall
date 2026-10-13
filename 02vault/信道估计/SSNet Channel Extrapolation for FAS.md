---
title: "SSNet: Flexible and Robust Channel Extrapolation for Fluid Antenna Systems Enabled by a Self-Supervised Learning Framework"
aliases:
  - SSNet
  - FAS 信道外推
tags:
  - literature-note
  - reading-note
  - 信道估计
  - 自监督学习
created: 2026-10-13
source: IEEE Journal on Selected Areas in Communications, 2025
author: Yuan Gao, Yiming Liu, Runze Yu, Shengli Liu, Yanliang Jin, Shunqing Zhang, Shugong Xu, Xiaoli Chu
year: 2025
journal: IEEE Journal on Selected Areas in Communications

theme: 用自监督学习解决流体天线系统（FAS）的信道状态信息外推问题
study_area: 信道估计 / 流体天线 / 自监督学习
methodology: 把信道外推建模为图像重建任务 + 对比损失与 NMSE 联合损失的自监督网络 SSNet
core_variable: 外推精度、噪声鲁棒性、可变 CSI 输入数量的灵活性、推理时间
key_finding: SSNet 在精度、噪声鲁棒性与输入灵活性上显著优于 AGMAE、LSTM 等基准
relevance: 自监督思路可降低对标注数据的依赖，对信道获取困难的 UAV 场景有借鉴价值

type: literature-note
zotero_key: "8S7LK7TQ"
pdf_key: "QEOR43QA"
doi: "10.1109/jsac.2025.3619472"
collection: "信道估计"
note_path: "02vault/信道估计/SSNet Channel Extrapolation for FAS.md"
fulltext_path: "03fulltext/信道估计/8S7LK7TQ.md"
status:
  - Reading
rating: 四星
---

# SSNet: Flexible and Robust Channel Extrapolation for Fluid Antenna Systems

---

# 📌 Basic Information（基本信息）

## Author
Yuan Gao, Yiming Liu, Runze Yu, Shengli Liu, Yanliang Jin, Shunqing Zhang, Shugong Xu, Xiaoli Chu

## Year
2025

## Source
IEEE Journal on Selected Areas in Communications｜DOI: 10.1109/jsac.2025.3619472

> Zotero 入口：zotero://select/library/items/8S7LK7TQ
> PDF 入口：zotero://open-pdf/library/items/QEOR43QA
> 全文 Markdown：[[03fulltext/信道估计/8S7LK7TQ]]

## Research Area

- Fluid Antenna Systems (FAS)
- Channel Extrapolation
- Self-Supervised Learning
- 6G Channel State Information

---

# 1. Abstract Summary（一句话总结）

> 该文把流体天线系统（FAS）的信道外推建模为图像重建任务，提出自监督学习网络 SSNet，用少量已知端口 CSI 外推未选端口 CSI，在精度、噪声鲁棒性与输入灵活性上显著优于现有方法。

---

# 2. Research Background（研究背景）

## 背景：

- 流体天线系统（FAS）通过提升频谱效率与鲁棒性，成为 6G 通信的重要进展。
- 但 FAS 复杂的物理结构使得获取准确信道状态信息（CSI）面临挑战。

> 原文：
> "Fluid antenna systems (FAS) signify a pivotal advancement in 6G communication by enhancing spectral efficiency and robustness. However, obtaining accurate channel state information (CSI) in FAS poses challenges due to its complex physical structure."

## Motivation（研究动机）

- 传统方法（基于导频的插值、压缩感知）计算密集且缺乏适应性。
- 依赖刚性参数模型的外推技术无法适应 FAS 的动态环境。
- 数据驱动的深度学习方法需要大量训练，且对噪声与硬件缺陷脆弱。

> 原文：
> "Traditional methods, such as pilot-based interpolation and compressive sensing, are not only computationally intensive but also lack adaptability. Current extrapolation techniques relying on rigid parametric models do not accommodate the dynamic environment of FAS, while data-driven deep learning approaches demand extensive training and are vulnerable to noise and hardware imperfections."

## Application Scenario（应用场景）

- 6G 流体天线系统的 CSI 获取
- 端口选择与预编码的联合优化
- FAS 与 ISAC 的结合场景
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在减少对标注数据依赖的同时，实现 FAS 中准确、鲁棒且能适应可变 CSI 输入数量的信道外推？

核心问题：

- 如何把信道外推转化为可自监督求解的任务形式？
- 如何同时提升特征提取能力与噪声鲁棒性？
- 如何处理可变数量的 CSI 输入（端口数变化）？

---

# 4. Related Work（相关工作）

已有方法：

1. **基于导频的插值**：计算密集，缺乏适应性。
2. **压缩感知（CS）**：同样计算密集且适应性不足。
3. **刚性参数模型外推**：无法适应 FAS 的动态环境。
4. **数据驱动深度学习**：需大量训练数据，对噪声与硬件缺陷脆弱。
5. **基准模型**：AGMAE、LSTM 等（本文对比对象）。

现有不足：

- 传统方法计算开销大、适应性差。
- 深度学习方法依赖大量标注且鲁棒性不足。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 把 FAS 的信道外推问题建模为图像重建任务：少量未掩码像素（已选端口的已知 CSI）用于外推被掩码像素（未选端口的 CSI）。
- SSNet 利用 FAS 信道的固有结构，直接从原始 CSI 数据学习广义表示，最大限度减少对大量标注数据集的需求。

> 原文：
> "We formulate the problem of channel extrapolation in FAS as an image reconstruction task. Here, a limited number of unmasked pixels (representing the known CSI of the selected ports) are used to extrapolate the masked pixels (the CSI of unselected ports)."
>
> 原文：
> "Our SSNet leverages the inherent structure of FAS channels to learn generalized representations directly from raw CSI data, thereby minimizing the need for extensive labeled datasets."

## Model / Framework

模型结构：

- **任务形式**：图像重建（掩码/未掩码像素 ↔ 已知/未知端口 CSI）
- **训练方式**：自监督学习（self-supervised learning）
- **损失函数**：对比损失（contrastive loss）+ 信道外推归一化均方误差（NMSE）的联合损失

> 原文：
> "To further improve the feature extraction capability and the noise robustness of the self-supervised learning, we propose to train the SSNet using a joint loss function of contrastive loss and channel extrapolation normalized mean squared error."

## Algorithm / Technique

采用：

- 自监督学习框架（SSNet）
- 掩码建模（类似 MAE 的像素掩码思路）
- 对比学习损失 + NMSE 联合监督
- 从原始 CSI 直接学习，减少对标注的依赖

## Key Steps

1. 把 FAS 信道外推重构为图像重建问题，定义掩码（未知端口）与未掩码（已知端口）。
2. 设计 SSNet 网络，利用 FAS 信道固有结构学习表示。
3. 用对比损失 + 外推 NMSE 的联合损失训练，兼顾特征判别性与重建精度。
4. 在多种信道模型（Clarke 模型、全相关信道模型）下训练与测试，验证泛化。
5. 与 AGMAE、LSTM 等基准对比，评估精度、鲁棒性与推理时间。
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **输入**：已选端口的已知 CSI（未掩码像素）
- **输出**：未选端口的 CSI（被掩码像素）
- **训练目标**：联合最小化对比损失与外推 NMSE

> 说明：网络结构细节、损失函数权重与掩码比例等超参数，以 [[03fulltext/信道估计/8S7LK7TQ]] 原文为准，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- FAS 信道具有可被网络学习的固有结构（端口间的空间相关性）。
- 少量已知端口 CSI 足以推断其余端口（外推可行）。
- 自监督掩码重建任务与真实外推任务在分布上一致。

## Optimization Objective

目标：

- 在减少对标注数据依赖的前提下，最大化外推精度、噪声鲁棒性与对可变输入数量的适应能力。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 训练与测试使用不同信道模型生成的样本：Clarke 模型 [52][53] 与全相关信道模型 [2]。
- 该设置用于检验分布外泛化（out-of-distribution）能力。

> 原文：
> "the proposed SSNet is trained and tested using the channel samples generated using the CLarke’s model [52], [53] and fully correlated channel model [2], respectively."

## Baseline

比较方法：

- AGMAE [29]
- LSTM（长短期记忆网络）
- 其他现有信道外推基准

> 原文：
> "Our detailed simulations demonstrate that SSNet significantly surpasses benchmark models, such as AGMAE [29] and long short-term memory (LSTM) networks"

## Metrics

评价指标：

- 外推精度（NMSE）
- 噪声鲁棒性
- 处理可变 CSI 输入数量的灵活性
- 推理时间

## Results

主要结果：

- SSNet 在精度、噪声鲁棒性与可变 CSI 输入数量的灵活性方面显著优于现有方法。
- 相比 AGMAE 与 LSTM 等基准模型有明显优势。
- 在性能与推理时间之间取得了平衡。

> 原文：
> "Our findings demonstrate that SSNet significantly outperform existing methods in terms of accuracy, robustness to noise, and flexibility in handling variable numbers of CSI inputs."
>
> 原文：
> "balance between the performance and inference time."

> 说明：具体的 NMSE 数值与推理时间对比，未在当前材料中逐项定位，此处不做引述。
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出 SSNet——面向 FAS 信道外推的自监督学习框架。
2. 把信道外推建模为图像重建任务，用少量已知端口 CSI 外推未选端口 CSI。
3. 提出对比损失 + 外推 NMSE 的联合损失，同时提升特征提取能力与噪声鲁棒性。
4. 在精度、噪声鲁棒性与可变输入灵活性上显著优于 AGMAE、LSTM 等基准，并取得性能与推理时间的平衡。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 自监督范式可摆脱对大量标注 CSI 数据集的依赖，这是相对数据驱动方法的关键改进。
- 联合损失（对比 + NMSE）是同时获得判别性表示与重建精度的关键设计。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 把图像掩码重建范式迁移到 FAS 信道外推，是有效的跨域借鉴，工程价值明确。
- 但核心组件（掩码自监督、对比学习）均为已有技术，创新性在于组合与适配。
- 训练/测试用不同信道模型是加分项，说明作者重视泛化验证。

---

# 10. Limitation（不足）

论文不足：

1. 创新性主要在范式迁移与组合，核心学习组件非原创。
2. 性能与推理时间的权衡仍需按实际部署约束再评估。
3. 依赖仿真信道模型（Clarke、全相关），真实 FAS 硬件缺陷建模可能不足。

未来可能改进：

- 在真实 FAS 硬件平台上验证。
- 联合优化端口选择与外推（端到端）。
- 扩展到 FAS-ISAC 联合信道获取。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 自监督掩码重建是把「获取标注难」问题转化为「从数据自身结构学习」的通用解法。
- 联合损失设计（表示学习损失 + 任务损失）是兼顾泛化与精度的常见有效组合。
- 用不同信道模型做训练/测试分离，是检验泛化能力的必要实验设计。

## Connection With My Work

和我的研究/项目关系：

- 自监督思路对 UAV 场景信道获取（标注少、环境多变）有直接借鉴价值。
- 图像重建范式可迁移到 UAV 空地信道的时空外推（用部分观测推断完整信道）。
- 可作为自己后续信道估计模块的候选 baseline。

## Possible Ideas

可能的新想法：

- 把 SSNet 的外推思想用于 UAV 移动场景的信道预测（时间维度外推）。
- 研究外推误差对后续波束成形/端口选择的端到端影响。
- 在 UAV 实测信道数据上检验该自监督方案的泛化性。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/信道估计/Diagonally Reconstructed Channel Estimation for MIMO-AFDM|MIMO-AFDM 信道估计]] — 同为信道获取，该文基于波形结构（解析），本文基于学习（自监督）

---

# 13. Summary Card（快速复习）

## Problem

> FAS 结构复杂导致 CSI 获取困难，传统方法计算密集/适应性差，深度学习方法又依赖大量标注且不鲁棒。

## Method

> 把信道外推建模为图像重建，用 SSNet 自监督学习，以对比损失 + 外推 NMSE 联合训练。

## Result

> 在精度、噪声鲁棒性与可变 CSI 输入数量的灵活性上显著优于 AGMAE、LSTM 等基准。

## Importance

> 以自监督范式摆脱对大量标注 CSI 的依赖，为 FAS 实用化提供了可落地的信道获取方案。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 FAS 中 CSI 获取困难的问题，克服传统方法计算密集、深度学习依赖标注且不鲁棒的限制。

Q:
核心方法是什么？

A:
把信道外推建模为图像重建任务，用 SSNet 自监督学习 + 对比损失与 NMSE 联合损失训练。

Q:
最大贡献是什么？

A:
以自监督方式实现高精度、强鲁棒、可变输入的 FAS 信道外推，显著优于 AGMAE 与 LSTM 基准。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `8S7LK7TQ`，PDF 附件 `QEOR43QA`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/信道估计/8S7LK7TQ]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 具体 NMSE 数值、推理时间与超参数配置未在当前材料中逐项定位，已在正文如实标注，未做推测。