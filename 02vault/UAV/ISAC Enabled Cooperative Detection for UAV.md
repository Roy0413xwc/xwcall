---
title: "ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network"
aliases:
  - ISAC 协同探测
  - 电子围栏
  - 黑飞检测
tags:
  - literature-note
  - reading-note
  - UAV
  - ISAC
  - 低空安全
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2025
author: Yi Wang, Keke Zu, Luping Xiang, Qixun Zhang, Zhiyong Feng, Jie Hu, Kun Yang
year: 2025
journal: IEEE Transactions on Wireless Communications

theme: 用基站 ISAC 能力实现蜂窝连接无人机的协同探测与低空监管
study_area: 通感一体化 / 低空安全 / 电子围栏
methodology: 基站 ISAC 能力 + 电子围栏区域划定 + 利用 UAV 高机动性与强视距链路的协同检测
core_variable: 非法入侵检测概率、通信服务质量、低空安全
key_finding: 借助基站 ISAC 划定电子围栏区域，可实现对非法入侵 UAV 的自动检测，保障低空经济下的低空安全
relevance: 与本 Vault 的 UAV 方向对口，与 [[02vault/UAV/ISAC Enabled Anti-UAV|ISAC 反无人机]] 主题直接相邻

type: literature-note
zotero_key: "E6FEI3MH"
pdf_key: "B36G57S8"
doi: "10.1109/TWC.2024.3509978"
collection: "UAV"
note_path: "02vault/UAV/ISAC Enabled Cooperative Detection for UAV.md"
fulltext_path: "03fulltext/UAV/E6FEI3MH.md"
status:
  - Reading
rating: 五星
---

# ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network

---

# 📌 Basic Information（基本信息）

## Author
Yi Wang, Keke Zu, Luping Xiang, Qixun Zhang, Zhiyong Feng, Jie Hu, Kun Yang

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/TWC.2024.3509978

> Zotero 入口：zotero://select/library/items/E6FEI3MH
> PDF 入口：zotero://open-pdf/library/items/B36G57S8
> 全文 Markdown：[[03fulltext/UAV/E6FEI3MH]]

## Research Area

- Cellular-Connected UAV
- Integrated Sensing and Communication (ISAC)
- Cooperative Detection / Electronic Fence
- Low-Altitude Safety

---

# 1. Abstract Summary（一句话总结）

> 该文面向低空无人机「黑飞」带来的民航安全与隐私风险，利用基站的 ISAC 能力对低空无人机实施通信与监管：通过划定电子围栏区域，ISAC 基站可自动检测 UAV 的非法入侵，从而在低空经济背景下保障低空安全。

---

# 2. Research Background（研究背景）

## 背景：

- 低空无人机作为新型交通方式快速发展，为市场注入新动力。
- 但未上报的「黑飞」无人机在民航安全、公民隐私保护等社会安全领域带来新风险。

> 原文：
> "The rapid development of low altitude Unmanned Aerial Vehicles (UAVs) as a new mode of transportation has injected a new driving force into the market development, but at the same time, unreported 'black flight' UAVs have also created new risks in civil aviation safety, citizen privacy protection and other social security areas."

## Motivation（研究动机）

- 低空经济背景下，对低空 UAV 的**通信服务与监管**需同时实现。
- 传统监管手段难以自动、实时地发现非法入侵。

## Application Scenario（应用场景）

- 低空经济下的 UAV 通信与监管一体化
- 电子围栏区域的非法入侵自动检测
- 民航安全与隐私保护场景

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何利用基站的 ISAC 能力，在提供低空 UAV 通信服务的同时实现对其的有效监管与非法入侵自动检测？

核心问题：

- 电子围栏区域如何划定与检测？
- 如何利用 UAV 的高机动性与强视距链路？
- 通信与监管如何在同一系统中协同？
---

# 4. Related Work（相关工作）

已有方法：

1. **传统低空监管手段**：依赖上报与人工监管，难以自动、实时发现黑飞。
2. **纯通信的蜂窝连接 UAV**：只提供通信服务，无感知/监管能力。
3. **独立雷达监测系统**：需额外部署，成本高且难以与通信网融合。

现有不足：

- 缺少通信与监管一体化的手段。
- 非法入侵检测缺乏自动化机制。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 利用基站（BS）的 **ISAC 能力**，为低空 UAV 提供**通信与监管的有效手段**。
- 通过**划定电子围栏区域**（electronic fence area），ISAC 基站可**自动检测 UAV 的非法入侵**。
- 借助 UAV 的**高机动性**与**强视距（LoS）链路**特性实现协同检测。

> 原文：
> "the Integrated Sensing And Communication (ISAC) capability of Base Station (BS) can provide an effective means of communication and supervision of low-altitude UAVs. For example, by demarcating the electronic fence area, the ISAC BS can realize automatic detection of illegal invasion of UAVs, effectively guaranteeing low-altitude safety in the context of low-altitude economy."
>
> 原文：
> "By leveraging the high mobility of UAVs and their strong ai"

## Model / Framework

系统模型：

- **基础设施**：具备 ISAC 能力的基站（BS）
- **对象**：低空 UAV（含合法的与未上报的「黑飞」UAV）
- **机制**：电子围栏区域划定 + 非法入侵自动检测
- **协同**：利用 UAV 高机动性与强视距链路

## Algorithm / Technique

采用：

- 基站 ISAC 能力（通信 + 感知）
- 电子围栏（electronic fence）区域划定
- 非法入侵自动检测
- 利用 UAV 高机动性与强视距链路的协同检测

## Key Steps

1. 建立低空 UAV 通信与监管的场景模型，明确黑飞风险。
2. 划定电子围栏区域，作为监管的空间边界。
3. 基站以 ISAC 方式同时提供通信服务并对区域进行感知。
4. 当检测到 UAV 非法进入围栏区域时触发自动告警/处置。
5. 利用 UAV 的高机动性与强视距链路提升检测可靠性。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **监管机制**：电子围栏区域划定 + 入侵检测
- **双功能**：通信服务 + 感知监管（ISAC）
- **可利用特性**：UAV 高机动性、强视距链路

> 说明：电子围栏的几何建模、检测概率的闭式表达与协同检测的具体算法见 [[03fulltext/UAV/E6FEI3MH]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- 基站具备 ISAC 能力，可同时通信与感知低空目标。
- 低空 UAV 与基站间以视距链路为主。
- 电子围栏区域可事先划定并作为检测依据。

## Optimization Objective

目标：

- 在保障合法 UAV 通信服务的同时，自动、可靠地检测非法入侵 UAV。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体基站数、围栏尺度、UAV 速度等参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取材料中对基线做具名列示，此处不做推测。

## Metrics

评价指标：

- 非法入侵检测概率
- 通信服务质量
- 低空安全保障能力

## Results

主要结果：

- 通过划定电子围栏区域，ISAC 基站可自动检测 UAV 的非法入侵。
- 在低空经济背景下有效保障了低空安全。

> 说明：具体的检测概率与对比数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/UAV/E6FEI3MH]] 仿真章节。