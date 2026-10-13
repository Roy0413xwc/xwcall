---
title: "Situation-Aware Hybrid Sensing and Position Control for UAV-Assisted ISAC Systems"
aliases:
  - 情境感知混合感知
  - 按需感知
tags:
  - literature-note
  - reading-note
  - UAV
  - ISAC
  - 位置控制
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2026
author: Ling Lyu, Qirui Luo, Yanpeng Dai, Nan Cheng, Cailian Chen, Xinping Guan, Xuemin Shen
year: 2026
journal: IEEE Transactions on Wireless Communications

theme: 用情境感知的混合感知模式降低感知能耗与对通信的干扰，同时完成位置感知与数据传输
study_area: 通感一体化 / UAV 位置控制 / 按需感知
methodology: 基于信道状态的按需感知激活 + UAV 位置控制
core_variable: 能量消耗、感知对通信的干扰、信道状态（受 UAV 位置影响）、位置感知精度
key_finding: 感知功能按信道状态按需激活，可降低能耗与感知对通信的干扰；配合 UAV 位置控制保障链路质量
relevance: 与本 Vault 的 UAV-ISAC 方向对口，且触及「感知开销」这一常被忽略的工程问题

type: literature-note
zotero_key: "573TSHTV"
pdf_key: "UTIJ8MMX"
doi: "10.1109/TWC.2026.3661956"
collection: "UAV"
note_path: "02vault/UAV/Situation-Aware Hybrid Sensing for UAV-ISAC.md"
fulltext_path: "03fulltext/UAV/573TSHTV.md"
status:
  - Reading
rating: 五星
---

# Situation-Aware Hybrid Sensing and Position Control for UAV-Assisted ISAC Systems

---

# 📌 Basic Information（基本信息）

## Author
Ling Lyu, Qirui Luo, Yanpeng Dai, Nan Cheng, Cailian Chen, Xinping Guan, Xuemin Shen

## Year
2026

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2026.3661956

> Zotero 入口：zotero://select/library/items/573TSHTV
> PDF 入口：zotero://open-pdf/library/items/UTIJ8MMX
> 全文 Markdown：[[03fulltext/UAV/573TSHTV]]

## Research Area

- UAV-Enabled ISAC
- Position Awareness and Data Transmission
- On-Demand / Hybrid Sensing
- UAV Position Control

---

# 1. Abstract Summary（一句话总结）

> 该文利用 UAV 的高灵活性与可控移动性为厂区设备与远程中心建立视距链路，采用 ISAC 在有限无线资源下同时完成位置感知与数据传输；提出情境感知的混合感知模式——感知功能根据受 UAV 位置强烈影响的信道状态按需激活，从而降低能耗与感知对通信的干扰，并配合 UAV 位置控制保障链路。

---

# 2. Research Background（研究背景）

## 背景：

- UAV 的高灵活性与可控移动性使其可在厂区设备与远程中心之间建立视距（LoS）传输链路。
- 但该链路的信道状态**严重依赖于 UAV 的位置**。

> 原文：
> "The high flexibility and controllable mobility of uncrewed aerial vehicles (UAVs) make it possible to construct the line-of-sight transmission link between devices in plant and the remote center, where the channel state condition heavily depends on the position of UAV."

## Motivation（研究动机）

- 需在**有限无线资源**下同时完成位置感知与数据传输。
- 持续感知会带来**不必要的能耗**，且**感知会对通信造成干扰**。

> 原文：
> "integrated sensing and communication (ISAC) is adopted to simultaneously perform position awareness and data transmission with limited radio resources. In particular, a situation-aware hybrid sensing pattern is proposed to reduce energy consumption and the interference of sensing to communication."

## Application Scenario（应用场景）

- 厂区设备与远程控制中心的 UAV 中继链路
- 工业物联网中的位置感知 + 数据传输
- 资源受限、需节省能耗的 UAV-ISAC 部署

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在有限无线资源下，既完成 UAV 的位置感知与数据传输，又降低感知带来的能耗与对通信的干扰？

核心问题：

- 感知功能何时该激活（按需的判据是什么）？
- UAV 位置如何控制以保障信道质量？
- 位置感知与数据传输如何共存于有限资源？

---

# 4. Related Work（相关工作）

已有方法：

1. **持续感知的 ISAC**：感知常开，能耗高且持续干扰通信。
2. **分离的位置感知与通信**：未共享资源，开销更大。
3. **固定位置或不做位置控制的 UAV 中继**：信道质量随位置变化而无法保障。

现有不足：

- 缺少「按需感知」的机制设计。
- 未把 UAV 位置控制与感知调度联合考虑。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 采用 ISAC 在有限无线资源下**同时执行位置感知与数据传输**。
- 提出**情境感知的混合感知模式**（situation-aware hybrid sensing pattern）：
  - 感知功能**按需激活**，判据是**信道状态条件**（而信道状态又受 UAV 位置强烈影响）
  - 以此**降低能耗**并**减少感知对通信的干扰**
- 同时执行 **UAV 位置控制**，以保障链路质量。

> 原文：
> "In this hybrid pattern, the sensing function is activated on demand based on the channel state condition that is heavily affected by the position of UAV. Besides, the position control of UAV is perform"

## Model / Framework

系统模型：

- **链路**：UAV 中继的厂区设备 ↔ 远程中心视距链路
- **双功能**：位置感知 + 数据传输（ISAC）
- **感知调度**：按需激活（由信道状态触发）
- **控制变量**：UAV 位置

## Algorithm / Technique

采用：

- 情境感知（situation-aware）机制
- 混合感知模式（hybrid sensing pattern）
- 按需感知激活（on-demand sensing）
- UAV 位置控制（position control）

## Key Steps

1. 建立 UAV 中继的视距链路模型，明确信道状态对 UAV 位置的依赖。
2. 设计情境感知判据：根据信道状态决定是否激活感知功能。
3. 在需要时激活感知以完成位置感知，其余时间仅做数据传输，从而省电并减少干扰。
4. 同时执行 UAV 位置控制，使信道维持在较好状态。
5. 通过仿真验证能耗降低与干扰抑制效果。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **双任务**：位置感知 + 数据传输，共享有限无线资源。
- **感知调度变量**：感知功能的激活决策（依赖信道状态）。
- **控制变量**：UAV 位置。
- **优化目标**：降低能耗与感知对通信的干扰，同时保障位置感知与传输性能。

> 说明：信道状态的具体度量、按需激活的阈值设计与位置控制的求解方式见 [[03fulltext/UAV/573TSHTV]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- UAV 位置可按需调整（可控移动性）。
- 信道状态可被估计并作为感知激活的判据。
- 感知功能可在需要时快速开关。

## Optimization Objective

目标：

- 在满足位置感知与数据传输需求的前提下，最小化能耗与感知对通信的干扰。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体厂区尺度、UAV 高度、信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 持续感知的 ISAC 方案（作为能耗与干扰的对照）。

## Metrics

评价指标：

- 能量消耗
- 感知对通信的干扰
- 位置感知精度
- 数据传输性能

## Results

主要结果：

- 情境感知的混合感知模式降低了能耗与感知对通信的干扰。
- 配合 UAV 位置控制保障了链路质量。

> 说明：具体的能耗降低比例与干扰抑制数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/573TSHTV]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 指出 UAV 中继的视距链路信道状态严重依赖 UAV 位置。
2. 用 ISAC 在有限资源下同时完成位置感知与数据传输。
3. 提出情境感知的混合感知模式：感知按需激活，判据为信道状态。
4. 借此降低能耗与感知对通信的干扰，并配合 UAV 位置控制保障链路。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 感知不必一直开启——按需感知是降低 ISAC 开销的直接有效手段。
- 信道状态既是感知的触发条件，也是 UAV 位置控制的目标，二者形成闭环。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 「感知开销」是 ISAC 工程落地的真实问题，却常被理论工作忽略，本文正面处理。
- 把信道状态同时用作感知触发与位置控制目标，闭环设计合理。
- 场景（厂区 ↔ 远程中心）具体，工程价值明确。

- 局限：量化收益需查阅仿真章节。

---

# 10. Limitation（不足）

论文不足：

1. 量化收益需查阅仿真章节。
2. 按需感知的判据若估计不准，可能漏掉需要的感知时机。
3. 仿真验证，无实测。
4. 未讨论感知功能开关的时延开销。

未来可能改进：

- 研究信道状态估计误差下的鲁棒按需策略。
- 在真实工业场景验证。
- 分析感知开关的时延与同步开销。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **感知是有开销的**：持续感知既费电又干扰通信，按需感知是务实的工程选择。
- UAV 位置既是通信质量的决定因素，也可作为控制手段——这是 UAV 相对固定基站的独特优势。
- 把「信道状态」同时用作感知触发条件与控制目标，可以形成自洽的闭环设计。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向对口，补充了「感知开销」这一工程维度。
- 按需感知的思路可用于自己的 ISAC 系统设计以节省资源。
- 与 [[02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks|SNN-DRL ISAC V2X]] 形成对照：该文用 SNN 降低计算能耗，本文用按需感知降低感知能耗。

## Possible Ideas

可能的新想法：

- 把按需感知与 [[02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning|Mem-DSACM]] 的记忆机制结合，用历史信道预测感知时机。
- 研究感知开关频率与链路质量保障的权衡。
- 对比按需感知与持续感知在不同业务负载下的能耗差异。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks|SNN-DRL ISAC V2X]] — 同属 ISAC 节能，该文降计算能耗，本文降感知能耗
- [[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]] — 同属 UAV 位置/控制与通信联合设计

---

# 13. Summary Card（快速复习）

## Problem

> UAV 中继链路需在有限资源下同时做位置感知与数据传输，而持续感知带来能耗与对通信的干扰。

## Method

> 情境感知的混合感知模式：按信道状态（受 UAV 位置影响）按需激活感知；同时做 UAV 位置控制。

## Result

> 降低了能耗与感知对通信的干扰（具体数值见全文仿真章节）。

## Importance

> 把「感知开销」作为明确优化对象，提供了 ISAC 工程落地的务实设计。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 UAV 中继链路中持续感知带来能耗与干扰、难以在有限资源下兼顾感知与传输的问题。

Q:
核心方法是什么？

A:
情境感知的混合感知模式：按信道状态按需激活感知，并配合 UAV 位置控制保障链路。

Q:
最大贡献是什么？

A:
提出按需感知机制，把感知开销作为优化对象，降低能耗与感知对通信的干扰。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `573TSHTV`，PDF 附件 `UTIJ8MMX`。
- PDF 经 pypdf 提取全文（88326 字符），原文引用均取自全文 Markdown [[03fulltext/UAV/573TSHTV]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 信道状态度量、按需激活阈值与量化数值未在当前材料中逐项定位，已在正文如实标注，未做推测。