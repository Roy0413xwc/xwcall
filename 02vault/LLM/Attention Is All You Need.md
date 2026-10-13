---
title: "Attention Is All You Need"
aliases:
  - Transformer
  - 注意力机制
tags:
  - literature-note
  - reading-note
  - LLM
  - Transformer
created: 2026-10-13
source: arXiv:1706.03762
author: Vaswani, Shazeer, Parmar, Uszkoreit, Jones, Gomez, Kaiser, Polosukhin
year: 2023
journal: arXiv preprint (cs.CL)

theme: 用纯注意力机制替代循环与卷积，构建可高度并行化的序列转换模型
study_area: 自然语言处理 / 机器翻译 / 序列建模
methodology: 编码器-解码器 + 多头自注意力 + 位置编码
core_variable: BLEU 分数、训练成本（FLOPs）、每步计算复杂度
key_finding: Transformer 在 WMT 2014 EN-DE 达 28.4 BLEU、EN-FR 达 41.8 BLEU，训练成本远低于此前模型
relevance: 后续大语言模型的架构基础，也可用于 UAV/ISAC 场景的时序状态与轨迹序列建模

type: literature-note
zotero_key: "BBHSTSCH"
pdf_key: "3S4LWK5Y"
doi: "10.48550/arXiv.1706.03762"
collection: "LLM"
note_path: "02vault/LLM/Attention Is All You Need.md"
fulltext_path: "03fulltext/LLM/BBHSTSCH.md"
status:
  - Reading
rating: 五星
---
# Attention Is All You Need

---

# 📌 Basic Information（基本信息）

## Author
Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, Illia Polosukhin

## Year
2023（Zotero 记录的 arXiv 版本；原始工作发表于 2017 年）

## Source
arXiv:1706.03762 [cs.CL]｜DOI: 10.48550/arXiv.1706.03762

> Zotero 入口：zotero://select/library/items/BBHSTSCH
> PDF 入口：zotero://open-pdf/library/items/3S4LWK5Y
> 全文 Markdown：[[03fulltext/LLM/BBHSTSCH]]

## Research Area

- Artificial Intelligence
- Natural Language Processing
- Machine Learning
- Sequence Transduction / Machine Translation

---

# 1. Abstract Summary（一句话总结）

> 该文提出完全基于注意力机制、彻底去除循环与卷积的 Transformer 架构，在 WMT 2014 英德与英法两项机器翻译任务上以显著更低的训练成本取得当时最好的翻译质量。

---

# 2. Research Background（研究背景）

## 背景：

- 当时主流的序列转换模型基于复杂的循环或卷积神经网络，采用编码器-解码器结构，性能最好的模型还会用注意力机制连接编码器与解码器。
- 循环模型沿序列位置顺序计算，无法在训练样本内并行化；序列较长时内存限制会制约批大小。
- 已有工作（ByteNet、ConvS2S）用卷积替代循环以并行化，但学习远距离依赖的路径长度仍随距离增长（ConvS2S 线性增长、ByteNet 对数增长）。

> 原文：
> "The dominant sequence transduction models are based on complex recurrent or convolutional neural networks in an encoder-decoder configuration. The best performing models also connect the encoder and decoder through an attention mechanism."
>
> 原文：
> "In the Transformer this is reduced to a constant number of operations, albeit at the cost of reduced effective resolution due to averaging attention-weighted positions, an effect we counteract with Multi-Head Attention as described in section 3.2."

## Motivation（研究动机）

- 循环层的顺序计算本质上阻碍训练并行化，成为长序列场景的性能瓶颈。
- 注意力机制本身可建立任意距离的依赖，但此前只作为循环网络的附属组件使用。
- 作者希望验证：仅靠注意力是否足以支撑完整的序列转换模型。

## Application Scenario（应用场景）

- 机器翻译（论文主要验证场景）
- 英语句法成分分析（用于验证泛化性）
- 后续被扩展到预训练语言模型、语音、视觉、强化学习等序列建模任务
- 对本研究方向：无人机通信场景下的时序状态序列建模、轨迹决策等
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 能否设计一种完全依赖注意力机制、不含循环与卷积的序列转换架构，在提升翻译质量的同时大幅提高可并行性并降低训练成本？

核心问题：

- 如何在没有循环结构的情况下表达序列顺序信息？
- 如何让模型同时关注不同表示子空间、不同位置的信息？
- 自注意力相比循环与卷积，在复杂度与依赖路径长度上有何优势？

---

# 4. Related Work（相关工作）

已有方法：

1. **循环序列模型（RNN / LSTM / GRU）**：沿序列顺序计算，路径长度 O(n)，无法并行；代表工作如 GNMT、Deep-Att + PosUnk。
2. **卷积神经网络（ByteNet、ConvS2S）**：可并行，但远距离依赖路径长度为 O(log_k n) 或 O(n/k)。
3. **带注意力的编码器-解码器（Bahdanau 等）**：注意力用于对齐，但仍依附于循环主干。
4. **自注意力先前工作**：自注意力已在阅读理解、摘要、文本蕴含等任务中使用，但未作为独立主干架构。
5. **循环神经网络文法（RNNG）**：句法分析方向，论文在实验部分与其对比。

现有不足：

- 循环模型无法并行，训练成本高、长序列受限。
- 卷积模型路径长度仍随距离增长，远距离依赖学习困难。
- 已有注意力使用方式未摆脱对循环结构的依赖。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 用多头自注意力完全替代循环层与卷积层，编码器与解码器各由 6 层相同结构的堆叠组成。
- 由于模型不含循环与卷积，需通过位置编码显式注入序列顺序信息。

> 原文：
> "We propose a new simple network architecture, the Transformer, based solely on attention mechanisms, dispensing with recurrence and convolutions entirely."

## Model / Framework

模型结构（编码器-解码器各 6 层）：

- **Encoder**：每层含多头自注意力子层 + 位置-wise 前馈网络子层，每个子层外接残差连接与层归一化。
- **Decoder**：在编码器两子层基础上插入一个对编码器输出做多头注意力的子层；自注意力子层带掩码，保证位置 i 的预测只能依赖 i 之前的已知输出。
- 前馈网络 FFN(x) = max(0, xW1 + b1)W2 + b2，内层维度 d_ff = 2048。
- 输出层：解码器输出经线性变换与 softmax 得到下一 token 概率；两个嵌入层与 pre-softmax 线性变换共享权重矩阵，嵌入层权重乘以 d_model 的平方根。

## Algorithm / Technique

采用：

- Scaled Dot-Product Attention（缩放点积注意力）
- Multi-Head Attention（多头注意力，h = 8 个并行注意力层）
- Positional Encoding（正弦/余弦位置编码）
- Residual Dropout（P_drop = 0.1）
- Label Smoothing（epsilon_ls = 0.1）
- Adam 优化器 + warmup 学习率调度（warmup_steps = 4000）

## Key Steps

1. 输入 token 嵌入后叠加位置编码，送入编码器栈（6 层）。
2. 编码器每层：多头自注意力 → 残差+层归一化 → 前馈网络 → 残差+层归一化。
3. 解码器每层：带掩码的多头自注意力 → 对编码器输出的多头注意力 → 前馈网络，每步同样接残差与层归一化。
4. 解码器输出经线性层与 softmax 预测下一 token。
5. 推理阶段使用 beam search（beam size = 4，长度惩罚 alpha = 0.6）。

> 原文：
> "An attention function can be described as mapping a query and a set of key-value pairs to an output, where the query, keys, values, and output are all vectors. The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key."
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

公式（缩放点积注意力）：

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

多头注意力：

$$\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, \dots, \text{head}_h)W^O$$

$$\text{head}_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)$$

位置编码（正弦/余弦）：

$$PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d_{model}}}\right)$$

$$PE_{(pos, 2i+1)} = \cos\left(\frac{pos}{10000^{2i/d_{model}}}\right)$$

学习率调度：

$$lrate = d_{model}^{-0.5} \cdot \min(step\_num^{-0.5},\ step\_num \cdot warmup\_steps^{-1.5})$$

> 说明：以上公式取自全文 Markdown [[03fulltext/LLM/BBHSTSCH]] 的原文表达。位置编码与学习率公式在缓存中以线性文本形式出现，此处按原文数学含义还原为标准排版，未改动数值与符号。PDF 页码未验证。

## Assumptions

假设：

- 序列顺序信息可通过加性位置编码充分注入，无需循环结构。
- 多个注意力头可分别关注不同表示子空间，缓解单头注意力平均化导致的有效分辨率下降。
- 翻译任务的质量与训练成本可由 BLEU 与训练 FLOPs 估计值衡量。

## Optimization Objective

目标：

- 标准自回归语言建模目标：在给定已生成前缀与源句的条件下最大化下一 token 的概率。
- 使用 label smoothing（epsilon_ls = 0.1），论文指出这会损害困惑度，但提升准确率与 BLEU。

> 原文：
> "This hurts perplexity, as the model learns to be more unsure, but improves accuracy and BLEU score."
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据：

- WMT 2014 English-to-German：约 450 万句对，BPE 编码，共享源-目标词表约 37000 个 token。
- WMT 2014 English-to-French：约 3600 万句对，词表 32000 个 word-piece。
- 句对按近似长度分批，每批约含 25000 个源 token 与 25000 个目标 token。
- 句法分析任务：WSJ 数据集（含 40K 句子的训练子集）。

环境：

- 单机 8 块 NVIDIA P100 GPU。
- base 模型每步约 0.4 秒，训练 10 万步（12 小时）；big 模型每步 1.0 秒，训练 30 万步（3.5 天）。

平台：

- TensorFlow，代码开源于 tensor2tensor。

> 原文：
> "We trained our models on one machine with 8 NVIDIA P100 GPUs. For our base models using the hyperparameters described throughout the paper, each training step took about 0.4 seconds. We trained the base models for a total of 100,000 steps or 12 hours. For our big models,(described on the bottom line of table 3), step time was 1.0 seconds. The big models were trained for 300,000 steps (3.5 days)."

## Baseline

比较方法：

- ByteNet
- Deep-Att + PosUnk（含 Ensemble）
- GNMT + RL（含 Ensemble）
- ConvS2S（含 Ensemble）
- MoE
- 句法分析方向：BerkeleyParser、RNN Grammar

## Metrics

评价指标：

- BLEU（EN-DE、EN-FR）
- 训练成本（以 FLOPs 估计：训练时间 × GPU 数量 × 单卡持续浮点算力估计）
- 每步训练时间、总训练步数

## Results

主要结果（Table 2）：

| Model | EN-DE BLEU | EN-FR BLEU | EN-DE 训练成本 (FLOPs) | EN-FR 训练成本 (FLOPs) |
|---|---|---|---|---|
| ByteNet | 23.75 | — | — | — |
| Deep-Att + PosUnk | — | 39.2 | — | 1.0 · 10^20 |
| GNMT + RL | 24.6 | 39.92 | 2.3 · 10^19 | 1.4 · 10^20 |
| ConvS2S | 25.16 | 40.46 | 9.6 · 10^18 | 1.5 · 10^20 |
| MoE | 26.03 | 40.56 | 2.0 · 10^19 | 1.2 · 10^20 |
| ConvS2S Ensemble | 26.36 | 41.29 | 7.7 · 10^19 | 1.2 · 10^21 |
| **Transformer (base)** | **27.3** | **38.1** | 3.3 · 10^18 | — |
| **Transformer (big)** | **28.4** | **41.8** | 2.3 · 10^19 | — |

- 句法分析：Transformer 在仅用 40K 句 WSJ 训练集时也超过 BerkeleyParser。

> 原文：
> "On the WMT 2014 English-to-German translation task, the big transformer model (Transformer (big) in Table 2) outperforms the best previously reported models (including ensembles) by more than 2.0 BLEU, establishing a new state-of-the-art BLEU score of 28.4."
>
> 原文：
> "On the WMT 2014 English-to-French translation task, our big model achieves a BLEU score of 41.0, outperforming all of the previously published single models, at less than 1/4 the training cost of the previous state-of-the-art model."
>
> 原文：
> "In contrast to RNN sequence-to-sequence models [37], the Transformer outperforms the BerkeleyParser [29] even when training only on the WSJ training set of 40K sentences."

> 注：摘要与 Table 2 中 EN-FR 为 41.8（Transformer big），正文 6.1 节叙述中出现 41.0 的表述，两者在原文中并存，此处如实并列，不做取舍。
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出 Transformer——首个完全基于注意力、不依赖循环与卷积的序列转换模型。
2. 引入 Scaled Dot-Product Attention 与 Multi-Head Attention，在保持常数级依赖路径长度的同时缓解平均化带来的分辨率损失。
3. 在 WMT 2014 EN-DE 与 EN-FR 上取得新的最佳结果，且训练成本显著低于此前所有竞争模型。
4. 证明该架构可泛化到英语句法成分分析任务（大数据与受限数据两种设置）。

> 原文：
> "In this work, we presented the Transformer, the first sequence transduction model based entirely on attention, replacing the recurrent layers most commonly used in encoder-decoder architectures with multi-headed self-attention."

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 首次证明纯注意力架构足以承担完整序列转换任务。
- 自注意力将任意位置间的路径长度压缩为常数级操作（对比循环 O(n)、卷积 O(log_k n)）。
- 多头机制可联合关注不同位置的不同表示子空间。
- 训练成本大幅下降：base 模型的训练成本低于任何竞争模型。

> 原文：
> "For translation tasks, the Transformer can be trained significantly faster than architectures based on recurrent or convolutional layers. On both WMT 2014 English-to-German and WMT 2014 English-to-French translation tasks, we achieve a new state of the art."

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 架构级创新，直接改变了后续 NLP 乃至多模态建模的技术路线。
- 复杂度分析清晰（Table 1 给出每层复杂度、顺序操作数、最大路径长度三项对比），理论与实验闭环完整。
- 工程可复现性强：代码开源，训练成本量化到 FLOPs 量级。
---

# 10. Limitation（不足）

论文不足：

1. 位置编码为固定的正弦/余弦形式，论文未充分讨论其在超出训练长度序列上的外推表现。
2. 自注意力复杂度为 O(n^2 · d)，长序列场景下仍存在二次增长问题（论文 Table 1 已列明）。
3. 论文自述平均化注意力加权位置会降低有效分辨率，仅通过多头机制缓解，未给出彻底解决方案。
4. 实验集中于机器翻译与句法分析，对其他模态与更长上下文的验证有限。

未来可能改进：

- 更高效的长序列注意力机制（稀疏、线性化注意力）。
- 可学习或相对位置编码，改善长度外推。
- 面向低资源、多模态与实时场景的适配。

> 原文（作者自述的后续方向）：
> "We plan to extend the Transformer to problems involving input and output modalities other than text and to investigate local, restricted attention to efficiently handle large inputs and outputs such as images, audio and video. Making generation less sequential is another research goals of ours."

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 并行化与依赖路径长度是衡量序列模型架构的两个独立维度，不能只看其中一个。
- 注意力不只是对齐工具，它本身可以承担完整的表示计算职责。
- 位置信息必须显式注入——去掉循环的同时也去掉了模型对顺序的天然感知。
- 训练成本的量化（FLOPs 估计）比单纯报告准确率更能反映架构的实际价值。

## Connection With My Work

和我的研究/项目关系：

- UAV/ISAC 场景中存在大量时序状态序列与轨迹决策问题，自注意力的常数级依赖路径长度对长时依赖建模有直接参考价值。
- Table 1 的复杂度对比框架（每层复杂度 / 顺序操作数 / 最大路径长度）可迁移用于评估时序模型的实时性约束。
- 若后续涉及无人机通信中的序列预测或资源调度策略学习，Transformer 的编码器结构可作为特征提取底座。

## Possible Ideas

可能的新想法：

- 将多头自注意力用于 UAV 轨迹序列的长期依赖建模，评估相对 LSTM 的推理时延与精度权衡。
- 在受限机上算力场景下考察注意力 O(n^2) 复杂度对实时性的影响，探索局部/稀疏注意力变体。
- 对比位置编码在定长遥测序列与变长文本序列上的表现差异。
---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- 暂无（当前 Vault 中尚未建立其他论文精读笔记）

---

# 13. Summary Card（快速复习）

## Problem

> 循环序列模型无法并行训练，卷积模型远距离依赖路径仍随距离增长，训练成本高。

## Method

> 编码器-解码器各 6 层，用多头自注意力 + 位置编码 + 前馈网络 + 残差层归一化，彻底去掉循环与卷积。

## Result

> WMT 2014 EN-DE 28.4 BLEU、EN-FR 41.8 BLEU（big 模型），训练成本 2.3 · 10^19 FLOPs，低于此前所有竞争模型。

## Importance

> 首个纯注意力序列转换模型，确立了大语言模型时代的主流架构范式。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决循环模型无法并行、卷积模型远距离依赖路径长、训练成本高的问题，提出纯注意力的 Transformer 架构。

Q:
核心方法是什么？

A:
多头缩放点积自注意力 + 正弦/余弦位置编码 + 编码器-解码器各 6 层堆叠，外接残差连接与层归一化。

Q:
最大贡献是什么？

A:
证明纯注意力架构足以独立完成序列转换，在两项机器翻译任务上以更低训练成本取得当时最佳结果，并成为后续预训练模型的架构基础。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `BBHSTSCH`（本地 API 读取），PDF 附件 `3S4LWK5Y`。
- 原文引用均取自全文 Markdown [[03fulltext/LLM/BBHSTSCH]]，来源为 Zotero 全文缓存 `F:\XWCos\zotero\storage\3S4LWK5Y\.zotero-ft-cache`。
- 该条目在 Zotero 中无批注（批注数为 0），故未纳入批注语料。
- PDF 页码未验证：全文缓存不含 page mapping，故未标注具体页码；需页码核验时请打开原始 PDF。
- Zotero 中记录的日期为 2023（arXiv 版本）；原始 NeurIPS 2017 版本信息未在当前材料中定位到可核验字段。
- 结论区的每条主要发现均紧邻至少一条真实原文引用；无法定位原句时已明确标注，未反向生成英文 quote。