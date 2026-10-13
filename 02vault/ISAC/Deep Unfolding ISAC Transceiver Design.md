---
title: "Deep Unfolding Learning Aided ISAC Transceiver Design"
aliases:
  - 深度展开 ISAC 收发机
  - Deep Unfolding
tags:
  - literature-note
  - reading-note
  - ISAC
  - 深度展开
  - 波形设计
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2025
author: Jifa Zhang, Yongxu Zhu, Nan Zhao, Shi Jin, Xianbin Wang, Derrick Wing Kwan Ng, Naofal Al-Dhahir
year: 2025
journal: IEEE Transactions on Wireless Communications

theme: 用深度展开学习降低杂波环境下 ISAC 收发机设计的复杂度
study_area: 通感一体化 / 波形设计 / 深度展开
methodology: ADMM 迭代算法 → 深度展开为网络层；联合优化发射波形与接收滤波
core_variable: 多用户干扰功率、感知 SINR 的倒数、恒模约束、波形相似度约束、计算复杂度
key_finding: 先构造 ADMM 迭代算法，再深度展开为低复杂度网络，在恒模与波形相似度约束下优化波形与接收滤波
relevance: 与本 Vault 的 ISAC 方向对口，且是「优化算法 → 学习化加速」的典型范式

type: literature-note
zotero_key: "ZE5HNQHG"
pdf_key: "KUCPV2UA"
doi: "10.1109/TWC.2025.3568367"
collection: "ISAC"
note_path: "02vault/ISAC/Deep Unfolding ISAC Transceiver Design.md"
fulltext_path: "03fulltext/ISAC/ZE5HNQHG.md"
status:
  - Reading
rating: 五星
---

# Deep Unfolding Learning Aided ISAC Transceiver Design

---

# 📌 Basic Information（基本信息）

## Author
Jifa Zhang, Yongxu Zhu, Nan Zhao, Shi Jin, Xianbin Wang, Derrick Wing Kwan Ng, Naofal Al-Dhahir

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2025.3568367

> Zotero 入口：zotero://select/library/items/ZE5HNQHG
> PDF 入口：zotero://open-pdf/library/items/KUCPV2UA
> 全文 Markdown：[[03fulltext/ISAC/ZE5HNQHG]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- Deep Unfolding / Algorithm Unrolling
- Transmit Waveform and Receive Filtering Design
- ADMM Optimization

---

# 1. Abstract Summary（一句话总结）

> 该文针对 ISAC 有效运行可能面临的高复杂度问题，提出低复杂度的深度展开学习辅助收发机设计方案：联合优化发射波形与接收滤波，最小化多用户干扰功率与感知 SINR 倒数之和，并满足恒模信号与波形相似度约束；先构造基于 ADMM 的迭代算法，再将其深度展开为网络以实现低复杂度。

---

# 2. Research Background（研究背景）

## 背景：

- ISAC 通过在通信与感知之间共享频谱与硬件，可提升频谱效率并支撑多样化的新兴应用。

> 原文：
> "Integrated sensing and communication (ISAC) can enhance spectral efficiency and facilitate the diverse emerging applications via sharing the same spectrum and hardware between communication and sensing."

## Motivation（研究动机）

- ISAC 的有效运行**可能受制于高复杂度**。
- 波形设计与接收滤波的联合优化本身非凸，迭代算法（如 ADMM）虽可解但开销大，难以实时。

> 原文：
> "However, effective operation of ISAC may suffer from high complexity."

## Application Scenario（应用场景）

- 杂波环境（cluttered environment）下的 ISAC 系统
- 需低复杂度实时实现的收发机
- 对波形有恒模与相似度约束的雷达通信一体化系统

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在杂波环境下低复杂度地联合设计 ISAC 的发射波形与接收滤波，同时满足恒模与波形相似度约束？

核心问题：

- 波形与接收滤波的联合优化目标如何设定？
- 恒模与波形相似度约束如何处理？
- 如何把迭代算法转化为低复杂度的学习模型？

---

# 4. Related Work（相关工作）

已有方法：

1. **纯迭代优化（如 ADMM）**：可求解但复杂度高，难实时部署。
2. **纯数据驱动的黑箱网络**：复杂度低但可解释性差、约束难保证。
3. **分离设计波形与滤波**：忽略二者耦合。

现有不足：

- 缺少兼顾低复杂度、可解释性与约束满足的方案。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 为杂波环境下的 ISAC 开发**低复杂度的深度展开学习辅助收发机设计方案**。
- **优化目标**：联合优化**发射波形**与**接收滤波**，最小化**多用户干扰功率**与**感知 SINR 倒数**的加权和。
- **约束**：恒模信号（constant modulus）与波形相似度（waveform similarity）。
- **求解路径**：先构造基于 **ADMM** 的迭代算法处理非凸问题，再将其**深度展开（deep unfolding）**为网络层，从而实现低复杂度。

> 原文：
> "we develop a low-complexity deep unfolding learning-aided transceiver design scheme for ISAC in a cluttered environment. In particular, we optimize the transmit waveform and receive filtering to minimize the weighted sum of multi-user interference power and the reciprocal of sensing signal-to-interference-plus-noise ratio (SINR), while adhering to the constraints of a constant modulus signal and waveform similarity."
>
> 原文：
> "An alternating direction method of multipliers (ADMM)-based iterative algorithm is first developed to address this non-convex optim"

## Model / Framework

系统模型：

- **环境**：杂波环境（存在 clutter）
- **优化变量**：发射波形、接收滤波
- **目标项**：多用户干扰功率 + 感知 SINR 的倒数（加权和）
- **约束**：恒模信号、波形相似度
- **两阶段求解**：ADMM 迭代算法 → 深度展开网络

## Algorithm / Technique

采用：

- 交替方向乘子法（ADMM）迭代算法
- 深度展开 / 算法展开（deep unfolding）
- 恒模约束处理
- 波形相似度约束

## Key Steps

1. 建立杂波环境下的 ISAC 收发模型，定义干扰功率与感知 SINR。
2. 构造加权和目标：多用户干扰功率 + 感知 SINR 的倒数。
3. 加入恒模信号与波形相似度约束。
4. 用 ADMM 设计迭代算法求解该非凸问题。
5. 把 ADMM 的迭代步骤深度展开为网络层，得到低复杂度的学习化实现。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标函数**：加权和 = 多用户干扰功率 + 感知 SINR 的倒数（1/SINR）
- **优化变量**：发射波形、接收滤波
- **约束**：恒模（constant modulus）、波形相似度（waveform similarity）
- **求解**：ADMM → 深度展开

> 说明：目标函数与约束的闭式表达、ADMM 的迭代格式与展开为网络层的具体方式见 [[03fulltext/ISAC/ZE5HNQHG]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 杂波可建模并体现在感知 SINR 中。
- 发射波形需满足恒模（利于功放效率）与与参考波形的相似度（利于保留雷达特性）。
- ADMM 的迭代结构可被展开为可学习的网络层。

## Optimization Objective

目标：

- 在恒模与波形相似度约束下，同时压低多用户干扰、提升感知 SINR，并以低复杂度实现。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体天线数、用户数、杂波强度与信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- ADMM 迭代算法（作为复杂度与性能的对照）。

## Metrics

评价指标：

- 多用户干扰功率
- 感知 SINR
- 计算复杂度 / 运行时间
- 约束满足情况（恒模、相似度）

## Results

主要结果：

- 深度展开方案在保持性能的同时显著降低了复杂度（相对 ADMM 迭代）。

> 说明：具体的复杂度降低倍数与性能数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/ZE5HNQHG]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出 ISAC 有效运行受高复杂度制约。
2. 联合优化发射波形与接收滤波，目标为「多用户干扰功率 + 感知 SINR 倒数」的加权和。
3. 满足恒模信号与波形相似度两类实际约束。
4. 先构造 ADMM 迭代算法，再深度展开为低复杂度网络。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 深度展开兼具优化的可解释性与学习的低复杂度，是二者的折中之道。
- 把感知 SINR 的**倒数**放入目标，等价于直接压低感知性能的劣化（而非最大化 SINR 本身）。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 深度展开是「算法学习化」的成熟范式，本文应用得当且问题设定完整（含恒模与相似度约束）。
- 与 [[02vault/ISAC/Learning to Beamform for ISAC (GNN)|GNN 波束成形]] 形成有趣对照：该文用 GNN+隐式层保证可行性，本文用算法展开保证可解释与约束。
- 但创新性主要在应用而非方法本身。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅仿真章节。
2. 展开层数需权衡（层数少则性能差，多则复杂度回升）。
3. 仿真验证，无实测。
4. 训练后的网络在分布外场景的泛化需验证。

未来可能改进：

- 研究展开层数与性能的帕累托关系。
- 在真实 ISAC 平台上验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **深度展开 = 把迭代算法变成网络层**：既保留优化的结构与可解释性，又获得推理速度。
- 恒模约束不只是数学要求，它关系到功放效率（雷达/通信发射机的实际约束）。
- 波形相似度约束用于保留参考波形（如雷达优选波形）的良好特性，是ISAC 波形设计的重要约束。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 ISAC 方向对口，提供了「优化算法学习化加速」的范式参考。
- 恒模 + 相似度约束可作为自己波形设计的约束模板。
- 与 [[02vault/ISAC/Learning to Beamform for ISAC (GNN)|GNN 波束成形]] 对照：两条不同的学习化路径（算法展开 vs 图网络+隐式层）。

## Possible Ideas

可能的新想法：

- 对比深度展开与 GNN 方案在同一 ISAC 波形问题上的复杂度与性能。
- 把恒模/相似度约束引入自己的 UAV-ISAC 波形设计。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/ISAC/Learning to Beamform for ISAC (GNN)|GNN 波束成形]] — 同为 ISAC 学习化方法，该文用 GNN+隐式层，本文用算法展开
- [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] — 同属 ISAC 信号处理，该文做参数估计，本文做收发机设计

---

# 13. Summary Card（快速复习）

## Problem

> ISAC 收发机联合设计（波形+接收滤波）非凸且复杂度高，难以实时运行。

## Method

> 以「多用户干扰功率 + 感知 SINR 倒数」加权和为目标，在恒模与波形相似度约束下，先构造 ADMM 迭代算法再深度展开为网络。

## Result

> 在保持性能的同时显著降低复杂度（具体数值见全文仿真章节）。

## Importance

> 用深度展开打通「优化可解释性」与「学习低复杂度」，为 ISAC 实时化提供路径。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 ISAC 收发机联合设计非凸、复杂度高、难以实时运行的问题。

Q:
核心方法是什么？

A:
以干扰功率+感知 SINR 倒数为目标，在恒模与相似度约束下，先构造 ADMM 再深度展开为网络。

Q:
最大贡献是什么？

A:
用深度展开把 ADMM 迭代算法学习化，在保持性能的同时大幅降低复杂度。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `ZE5HNQHG`，PDF 附件 `KUCPV2UA`。
- PDF 经 pypdf 提取全文（70774 字符），原文引用均取自全文 Markdown [[03fulltext/ISAC/ZE5HNQHG]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 目标函数闭式表达、ADMM 迭代格式、展开层级设计与量化数值未在当前材料中逐项定位，已在正文如实标注，未做推测。