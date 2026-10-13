---
title: "ISAC-Enabled Beam Tracking for U2U Communication Systems Under Jittering Effects"
aliases:
  - U2U 波束跟踪
  - 抖动补偿
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - 波束跟踪
created: 2026-10-13
source: IEEE Transactions on Communications, 2026
author: Wei Liu, Yuhang Tang, Jinkun Zhu, Peng Yang
year: 2026
journal: IEEE Transactions on Communications

theme: 用 ISAC 使能的抖动鲁棒波束跟踪解决无人机间（U2U）通信的波束对齐问题
study_area: 通感一体化 / U2U 通信 / 波束跟踪
methodology: 感知回波辅助的角度跟踪 + 抖动补偿算法（自适应波束宽度控制 + 波束指向精化）
core_variable: 可达速率、角度预测精度、抖动幅度、波束宽度
key_finding: 用系留无人机基站的感知回波获取运动信息并结合先验运动模型提升角度预测精度，再用自适应波束宽度与波束指向精化补偿抖动
relevance: UAV 间通信的波束管理是本 Vault UAV-ISAC 方向的重要子问题，抖动是实际工程痛点

type: literature-note
zotero_key: "2IA69RXU"
pdf_key: "8FA31D6C"
doi: "10.1109/tcomm.2026.3681647"
collection: "ISAC"
note_path: "02vault/ISAC/ISAC-Enabled Beam Tracking for U2U.md"
fulltext_path: "03fulltext/ISAC/2IA69RXU.md"
status:
  - Reading
rating: 五星
---

# ISAC-Enabled Beam Tracking for U2U Communication Systems Under Jittering Effects

---

# 📌 Basic Information（基本信息）

## Author
Wei Liu, Yuhang Tang, Jinkun Zhu, Peng Yang

## Year
2026

## Source
IEEE Transactions on Communications｜DOI: 10.1109/tcomm.2026.3681647

> Zotero 入口：zotero://select/library/items/2IA69RXU
> PDF 入口：zotero://open-pdf/library/items/8FA31D6C
> 全文 Markdown：[[03fulltext/ISAC/2IA69RXU]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- UAV-to-UAV (U2U) Communications
- Beam Tracking / Beam Alignment
- Jitter Compensation

---

# 1. Abstract Summary（一句话总结）

> 该文提出抖动鲁棒的 ISAC 波束跟踪框架：系留无人机基站利用感知回波获取机动无人机用户的运动信息，结合先验运动模型提升角度预测精度；在此基础上设计抖动补偿算法——基站端用自适应波束宽度控制保证鲁棒覆盖，用户端用波束指向精化优化指向，从而最大化 U2U 系统可达速率。

---

# 2. Research Background（研究背景）

## 背景：

- 无人机间（U2U）通信系统中，系留无人机基站（UAV-B）为机动的无人机用户（UAV-U）提供服务。
- **抖动（jitter）会破坏波束对齐并降低通信速率**。

> 原文：
> "a tethered UAV base station (UAV-B) serves a maneuvering UAV user (UAV-U), where jitter disrupts beam alignment and degrades communication rates."

## Motivation（研究动机）

- 无人机平台天然存在姿态与位置抖动（受风、旋翼振动等影响），使窄波束难以维持对准。
- 传统波束跟踪依赖导频反馈，开销大且在快时变下滞后。
- ISAC 提供了新思路：用感知回波直接获取用户的运动信息。

## Application Scenario（应用场景）

- 无人机间高速数据链路
- 系留无人机基站的区域覆盖
- 存在明显平台抖动的空空通信

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在无人机平台抖动导致波束失准的情况下，利用 ISAC 感知能力提升角度预测精度并补偿抖动，从而最大化 U2U 通信可达速率？

核心问题：

- 如何用感知回波 + 先验运动模型提升角度预测精度？
- 如何在基站端与用户端分别设计补偿机制？
- 波束宽度与指向如何联合优化以兼顾覆盖鲁棒性与指向增益？
---

# 4. Related Work（相关工作）

已有方法：

1. **基于导频反馈的波束跟踪**：开销大，快时变下滞后。
2. **忽略抖动的波束对齐方法**：在无人机平台上实际会失效。
3. **固定波束宽度的方案**：无法兼顾覆盖鲁棒性与指向增益。

现有不足：

- 未利用 ISAC 感知回波所携带的运动信息。
- 缺少针对平台抖动的专门补偿机制。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 提出**抖动鲁棒的 ISAC 波束跟踪框架**，面向 U2U 通信系统。
- 第一阶段——**角度跟踪**：提出 UAV-U 角度跟踪方法，估计 UAV-B 与 UAV-U 之间的相对角度。
  - 系留 UAV-B 利用**感知回波信号**获取 UAV-U 的运动信息
  - 与 UAV-U 的**先验运动模型**融合，提升角度预测精度
  - 同时，通过通信链路，UAV-U 可获知 UAV-B 的方向
- 第二阶段——**抖动补偿**：在所得角度信息基础上，进一步设计抖动补偿算法以最大化可达速率。
  - UAV-B 采用**自适应波束宽度控制（ABC）**：调整波束宽度，保证对 UAV-U 的鲁棒覆盖
  - UAV-U 采用**波束指向精化（BSR）**：优化其指向

> 原文：
> "a UAV-U angle tracking method is first proposed to estimate the relative angles between UAV-B and UAV-U. Specifically, the tethered UAV-B leverages sensing echo signals to obtain motion information of UAV-U, and integrates them with UAV-U’s prior motion models to enhance the accuracy of angle prediction."
>
> 原文：
> "Meanwhile, through the communication link, UAV-U can receive the direction of UAV-B."
>
> 原文：
> "a jitter compensation algorithm is further developed to maximize the achievable rate of the U2U communication systems. In particular, UAV-B employs adaptive beamwidth control (ABC) to adjust its beamwidth and thus ensures robust coverage for UAV-U. Meanwhile, UAV-U employs beam steering refinement (BSR) to optimize the di"

## Model / Framework

系统模型：

- **UAV-B**：系留无人机基站（tethered），具备 ISAC 能力（发射通信信号并用回波感知）
- **UAV-U**：机动无人机用户（maneuvering）
- **损伤因素**：平台抖动（jitter）
- **待估量**：UAV-B 与 UAV-U 之间的相对角度

## Algorithm / Technique

采用：

- ISAC 感知回波获取运动信息
- 先验运动模型融合（角度预测）
- 自适应波束宽度控制（Adaptive Beamwidth Control, ABC）
- 波束指向精化（Beam Steering Refinement, BSR）

## Key Steps

1. 建立 U2U 通信系统模型，明确抖动对波束对齐的破坏机制。
2. UAV-B 发射 ISAC 信号，从感知回波中提取 UAV-U 的运动信息。
3. 把回波所得运动信息与 UAV-U 的先验运动模型融合，预测相对角度。
4. 通过通信链路把 UAV-B 的方向告知 UAV-U。
5. 抖动补偿：UAV-B 用 ABC 调整波束宽度以保证鲁棒覆盖。
6. 抖动补偿：UAV-U 用 BSR 优化其波束指向，最大化可达速率。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **待估量**：UAV-B 与 UAV-U 的相对角度（relative angles）。
- **信息来源**：感知回波（运动信息）+ 先验运动模型 + 通信链路（方向反馈）。
- **优化目标**：最大化 U2U 通信系统的可达速率（achievable rate）。
- **补偿手段**：ABC（波束宽度）+ BSR（波束指向）

> 说明：角度估计的具体算法、抖动模型与可达速率的闭式表达见 [[03fulltext/ISAC/2IA69RXU]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- UAV-B 为系留平台（相对稳定），UAV-U 为机动平台。
- 感知回波可反映 UAV-U 的运动状态。
- UAV-U 的运动可用先验模型部分描述（非完全随机）。
- 抖动可建模为角度/位置上的随机扰动。

## Optimization Objective

目标：

- 在抖动存在下，通过角度预测与波束宽度/指向的联合优化，最大化可达速率。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体载频、天线数、抖动幅度与 UAV 速度等参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 可达速率（achievable rate）
- 角度预测精度
- 波束对齐鲁棒性（抖动下）

## Results

主要结果：

- 所提角度跟踪方法通过融合感知回波与先验运动模型，提升了角度预测精度。
- 抖动补偿算法（ABC + BSR）有效提升了 U2U 系统的可达速率。

> 说明：具体的速率增益与角度预测误差数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/2IA69RXU]] 仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出面向 U2U 通信的抖动鲁棒 ISAC 波束跟踪框架。
2. 提出 UAV-U 角度跟踪方法：用感知回波获取运动信息，并与先验运动模型融合以提升角度预测精度。
3. 利用通信链路使 UAV-U 获得 UAV-B 的方向。
4. 提出抖动补偿算法：UAV-B 端自适应波束宽度控制（ABC）+ UAV-U 端波束指向精化（BSR），最大化可达速率。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 感知回波是「免费」的运动信息来源，无需额外导频开销——这是 ISAC 在波束管理上的直接价值体现。
- 抖动补偿需两端协同：基站调宽度（保证不掉链）、用户调指向（保证增益）。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 抓住无人机平台的实际工程痛点（抖动），而非理想化假设。
- 「感知回波 → 运动信息 → 角度预测 → 波束补偿」的链路完整且闭环。
- 两端分工（ABC / BSR）的设计清晰，工程可实现性高。

- 局限：量化收益需查阅仿真章节。

---

# 10. Limitation（不足）

论文不足：

1. 仿真验证，无实测或硬件在环。
2. 先验运动模型与实际机动的匹配程度会影响预测精度。
3. 未考虑多用户场景下的波束资源竞争。
4. 量化收益需查阅仿真章节。

未来可能改进：

- 在真实无人机平台上验证抖动特性与补偿效果。
- 研究模型失配时的鲁棒/自适应预测。
- 扩展到多 UAV-U 的波束调度。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **抖动是无人机平台的固有损伤**，波束管理必须显式处理，否则窄波束增益无法兑现。
- ISAC 的感知回波可替代部分导频开销来获取运动信息——这是「感知辅助通信」的典型用例。
- 波束宽度与指向是一对权衡：宽度保证鲁棒、指向保证增益，需按抖动强度自适应。
- 两端协同补偿比单端调整更有效。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向对口，是波束管理这一子问题的重要参考。
- 「感知辅助通信」的思路可迁移到 UAV-ISAC 的链路自适应设计。
- 抖动建模可用于自己的 UAV 信道仿真（补充 [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]] 未覆盖的抖动维度）。

## Possible Ideas

可能的新想法：

- 把抖动模型引入 UAV 空地信道仿真，检验对波束成形增益的削减。
- 研究多 UAV-U 场景下 ABC/BSR 的资源竞争与调度。
- 用学习式方法替代先验运动模型，提升模型失配时的鲁棒性。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]] — 提供 UAV 信道实测依据，本文补充了抖动这一动态损伤维度
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]] — 同属 ISAC 波束设计，该文关注最优结构理论，本文关注抖动下的跟踪与补偿

---

# 13. Summary Card（快速复习）

## Problem

> 无人机平台抖动破坏 U2U 通信的波束对齐，降低通信速率；传统导频跟踪开销大且滞后。

## Method

> 用感知回波 + 先验运动模型做角度预测；基站端 ABC 自适应调波束宽度，用户端 BSR 精化波束指向。

## Result

> 提升了角度预测精度与 U2U 可达速率（具体增益见全文仿真章节）。

## Importance

> 给出「感知辅助通信」在无人机波束管理上的完整闭环方案，直面抖动这一实际工程损伤。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决无人机平台抖动破坏 U2U 通信波束对齐、导致速率下降的问题。

Q:
核心方法是什么？

A:
感知回波 + 先验运动模型做角度预测；基站端自适应波束宽度控制（ABC）+ 用户端波束指向精化（BSR）。

Q:
最大贡献是什么？

A:
提出抖动鲁棒的 ISAC 波束跟踪框架，用感知回波免导频地获取运动信息并两端协同补偿抖动。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `2IA69RXU`，PDF 附件 `8FA31D6C`。
- PDF 由用户提供（本地 Downloads 目录），经 pypdf 提取全文（71930 字符）。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/2IA69RXU]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 角度估计算法、抖动模型与速率闭式表达未在当前材料中逐项定位，已在正文如实标注，未做推测。