---
title: "Under-Determined DOA Estimation: A Method Based on Higher-Order Statistics and Non-Uniform Arrays"
aliases:
  - 欠定 DOA 估计
  - 高阶统计量
tags:
  - literature-note
  - reading-note
  - DOA 估计
  - 阵列信号处理
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2024
author: Wei Peng, Peng Li, Xinyi Wu, Kai Luo, Gan Zheng, Dong Li
year: 2024
journal: IEEE Transactions on Wireless Communications

theme: 用高阶统计量与非均匀阵列解决路径数超过阵元数的欠定 DOA 估计问题
study_area: DOA 估计 / 阵列信号处理 / 高阶统计量
methodology: 高阶统计量（扩展阵列孔径 + 抑制高斯噪声）+ 非均匀阵列结构
core_variable: 可估计 DOA 数量、自由度、噪声鲁棒性、估计精度
key_finding: 高阶统计量可扩展阵列孔径并抑制加性高斯噪声；与非均匀阵列结合可解决欠定问题
relevance: DOA 估计是 ISAC 感知侧的基础技术，与本 Vault 的感知方向相关

type: literature-note
zotero_key: "74WGPALB"
pdf_key: "MD4SYGJS"
doi: "10.1109/twc.2024.3434981"
collection: "信道估计"
note_path: "02vault/信道估计/Under-Determined DOA Estimation.md"
fulltext_path: "03fulltext/信道估计/74WGPALB.md"
status:
  - Reading
rating: 四星
---

# Under-Determined DOA Estimation: A Method Based on Higher-Order Statistics and Non-Uniform Arrays

---

# 📌 Basic Information（基本信息）

## Author
Wei Peng, Peng Li, Xinyi Wu, Kai Luo, Gan Zheng, Dong Li

## Year
2024

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/twc.2024.3434981

> Zotero 入口：zotero://select/library/items/74WGPALB
> PDF 入口：zotero://open-pdf/library/items/MD4SYGJS
> 全文 Markdown：[[03fulltext/信道估计/74WGPALB]]

## Research Area

- Direction of Arrival (DOA) Estimation
- Higher-Order Statistics (HOS)
- Non-Uniform Arrays
- Under-determined Estimation

---

# 1. Abstract Summary（一句话总结）

> 该文针对路径数超过天线阵元数的欠定 DOA 估计问题，提出基于高阶统计量与非均匀阵列结构的方法：高阶统计量既能扩展阵列孔径又能抑制加性高斯噪声，与非均匀阵列结合后克服了二阶统计量 + 均匀线阵在可估计 DOA 数量与噪声敏感性上的限制。

---

# 2. Research Background（研究背景）

## 背景：

- DOA 估计在众多应用中被广泛使用。
- 传统 DOA 估计通常採用**二阶统计量**与**均匀线阵（ULA）**结构。

> 原文：
> "Traditional DOA estimation generally adopts the second-order statistics and the uniform linear array (ULA) structure."

## Motivation（研究动机）

- 二阶统计量与均匀阵列结构**限制了可准确估计的 DOA 数量**。
- 基于二阶统计量的方法**对噪声敏感**。
- 5G 时代无线环境日益复杂，传播信道可能由大量路径构成；**当路径数超过天线阵列规模时，DOA 估计成为欠定问题**，传统二阶统计量方法无法处理。

> 原文：
> "the second-order statistics and the uniform array structure restrict the number of DOAs that can be accurately estimated. In addition, the performance of the second-order statistics-based methods is sensitive to noise."
>
> 原文：
> "When the number of paths exceeds the size of the antenna array, DOA estimation becomes an under-determined problem, which the second-order statistics-based traditional methods fail to deal with."

## Application Scenario（应用场景）

- 多径丰富的 5G/6G 环境中的 DOA 估计
- 阵元数受限但路径数众多的小型阵列
- ISAC 中的目标角度估计（潜在迁移）

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 当路径数超过阵元数时，如何突破二阶统计量 + 均匀线阵的限制，实现欠定条件下的 DOA 估计并提升噪声鲁棒性？

核心问题：

- 高阶统计量如何扩展阵列孔径并抑制高斯噪声？
- 为何高阶统计量需与非均匀阵列（而非均匀阵列）结合？
- 该方法能处理多少超额路径？
---

# 4. Related Work（相关工作）

已有方法：

1. **二阶统计量 + 均匀线阵（ULA）**：限制了可准确估计的 DOA 数量，且对噪声敏感。
2. **传统欠定 DOA 方法**：无法处理路径数超过阵元数的情形。

现有不足：

- 可估计 DOA 数量受阵元数硬限制。
- 噪声敏感性高。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 采用**高阶统计量（HOS）**替代二阶统计量：高阶统计量**既能扩展阵列孔径，又能抑制加性高斯噪声**。
- 采用**非均匀阵列结构**替代均匀阵列：若高阶统计量与均匀阵列结合，**扩展后的自由度（DoF）会受到限制**；因此需与非均匀阵列配合。

> 原文：
> "Higher-order statistics-based methods can not only expand the array aperture, but also suppress the additive Gaussian noise. However, if combined with a uniform array structure, the degrees of freedom of the exp"

## Model / Framework

系统设定：

- **问题**：欠定 DOA 估计（路径数 > 阵元数）
- **统计量**：高阶统计量（higher-order statistics）
- **阵列结构**：非均匀阵列（non-uniform array）
- **目标**：扩展有效孔径与自由度，抑制高斯噪声

## Algorithm / Technique

采用：

- 高阶统计量（HOS）处理
- 非均匀阵列（non-uniform array）结构设计
- 阵列孔径扩展
- 高斯噪声抑制

## Key Steps

1. 建立欠定 DOA 估计问题模型（路径数 > 阵元数）。
2. 用高阶统计量替代二阶统计量处理接收数据，扩展等效阵列孔径。
3. 利用高阶统计量对加性高斯噪声的抑制能力，提升噪声鲁棒性。
4. 设计非均匀阵列结构，避免均匀阵列对高阶统计量自由度的限制。
5. 在扩展后的孔径与自由度下完成 DOA 估计。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **欠定条件**：路径数（number of paths）> 天线阵列规模（size of the antenna array）。
- **高阶统计量作用**：扩展阵列孔径（array aperture）+ 抑制加性高斯噪声（additive Gaussian noise）。
- **非均匀阵列作用**：避免均匀结构对高阶统计量所扩展自由度（DoF）的限制。

> 说明：高阶统计量的具体阶数、非均匀阵列的排布方式（如嵌套阵/互质阵）与 DOA 估计算法的闭式表达见 [[03fulltext/信道估计/74WGPALB]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 噪声主要为加性高斯噪声（高阶统计量可对其抑制）。
- 非均匀阵列的排布可按需设计（不受均匀间距约束）。
- 信号源之间具备足够的统计独立性以供高阶统计量利用。

## Optimization Objective

目标：

- 在欠定条件下准确估计超过阵元数量的 DOA，并提升噪声鲁棒性。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体阵元数、路径数、SNR 范围未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 基于二阶统计量的传统方法
- 均匀线阵（ULA）方案

## Metrics

评价指标：

- 可准确估计的 DOA 数量（欠定能力）
- 估计精度（RMSE）
- 噪声鲁棒性
- 有效阵列孔径 / 自由度

## Results

主要结果：

- 所提基于高阶统计量与非均匀阵列的方法可处理**路径数超过阵元数**的欠定 DOA 估计。
- 高阶统计量扩展了阵列孔径并抑制了加性高斯噪声，提升了噪声鲁棒性。

> 说明：具体的可估计 DOA 数量上限与 RMSE 数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/信道估计/74WGPALB]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出二阶统计量 + 均匀线阵的两大限制：可估计 DOA 数量受限、对噪声敏感。
2. 明确「路径数超过阵元数」使 DOA 估计成为欠定问题，传统方法失效。
3. 提出用高阶统计量扩展阵列孔径并抑制加性高斯噪声。
4. 指出高阶统计量若与均匀阵列结合会限制扩展后的自由度，因而采用非均匀阵列结构。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 高阶统计量是突破「阵元数硬限制」的关键：它从统计结构上产生额外的等效孔径。
- 非均匀阵列是释放高阶统计量自由度潜力的必要条件——这是一个容易被忽略的配套设计。

## My Evaluation

我的评价：

四星

创新程度：

中

理由：

- 高阶统计量与非均匀阵列都是既有技术，本文的贡献在于指出二者的**配套必要性**并用于欠定场景。
- 「高阶统计量 + 均匀阵列会限制自由度」这一洞察有实际指导价值。
- 与本 Vault 主线（UAV/ISAC）的相关性中等：DOA 是感知基础技术，但本文未涉及 UAV 场景。

---

# 10. Limitation（不足）

论文不足：

1. 高阶统计量计算复杂度高于二阶统计量。
2. 仿真验证，无实测。
3. 非均匀阵列的硬件实现（互耦、校准）比均匀阵列复杂。
4. 量化能力上限需查阅仿真章节。

未来可能改进：

- 降低高阶统计量的计算复杂度。
- 研究非均匀阵列在互耦下的校准方法。
- 在 UAV/ISAC 的实际感知场景中验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **欠定（under-determined）是路径数 > 阵元数**的情形，传统子空间类方法（如 MUSIC）在此失效。
- 高阶统计量的两个独特价值：扩展等效孔径 + 抑制高斯噪声（后者是二阶统计量做不到的）。
- 阵列几何与统计量类型是**配套设计**：换统计量就得换阵列结构，否则自由度仍受限。

## Connection With My Work

和我的研究/项目关系：

- DOA 估计是 ISAC 感知侧的基础技术，可作为自己感知算法的备选方案。
- 与 [[02vault/信道估计/HMIMO Graph-Based Wavenumber-Domain Channel Estimation|HMIMO 信道估计]] 形成对照：该文处理大规模阵列的信道估计，本文处理小规模阵列的欠定 DOA。
- 与 [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] 形成对照：该文用张量 CP 分解做角度估计，本文用高阶统计量。

## Possible Ideas

可能的新想法：

- 把高阶统计量方法用于 UAV-ISAC 的小阵列角度估计。
- 对比本文方法与 [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 张量方法]] 在同一欠定场景下的表现。
- 研究 UAV 平台振动对非均匀阵列校准的影响。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] — 同为角度估计，该文用张量 CP 分解，本文用高阶统计量 + 非均匀阵列
- [[02vault/信道估计/HMIMO Graph-Based Wavenumber-Domain Channel Estimation|HMIMO 信道估计]] — 同属阵列信号处理，该文面向大规模阵列信道估计，本文面向小阵列欠定 DOA

---

# 13. Summary Card（快速复习）

## Problem

> 当路径数超过阵元数时 DOA 估计成为欠定问题；二阶统计量 + 均匀线阵在可估计数量与噪声敏感性上均受限。

## Method

> 用高阶统计量扩展阵列孔径并抑制加性高斯噪声，并配合非均匀阵列结构以释放扩展后的自由度。

## Result

> 可处理路径数超过阵元数的欠定 DOA 估计，并提升噪声鲁棒性（具体上限与精度见全文仿真章节）。

## Importance

> 指出高阶统计量与非均匀阵列的配套必要性，为小阵列下的欠定 DOA 估计提供了可行路径。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决路径数超过阵元数时的欠定 DOA 估计问题，突破二阶统计量与均匀线阵的限制。

Q:
核心方法是什么？

A:
高阶统计量（扩展孔径 + 抑制高斯噪声）配合非均匀阵列结构（释放自由度）。

Q:
最大贡献是什么？

A:
指出高阶统计量需与非均匀阵列配套使用，并据此实现欠定条件下的 DOA 估计。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `74WGPALB`，PDF 附件 `MD4SYGJS`。
- PDF 由用户提供（本地 Downloads 目录），经 pypdf 提取全文（55983 字符）。
- 原文引用均取自全文 Markdown [[03fulltext/信道估计/74WGPALB]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 高阶统计量阶数、非均匀阵列排布与量化仿真数值未在当前材料中定位，已在正文如实标注，未做推测。