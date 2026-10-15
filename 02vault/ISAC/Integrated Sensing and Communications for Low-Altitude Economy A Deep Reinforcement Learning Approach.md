---
title: "Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement Learning Approach"
tags:
  - joint_beamforming_and_trajector_design
  - Low-altitude_economy
  - ISAC
  - UAV
  - DRL
author: Xiaowen Ye, Yuyi Mao, Xianghao Yu, Shu Sun, Liqun Fu, Jie Xu
year: 2025
journal: IEEE Transactions on Wireless Communications
theme: 面向低空经济的 ISAC 系统，用深度强化学习联合优化波束成形与无人机轨迹
methodology: 建模为 episode task 型 MDP + 深度强化学习方案 DeepLSC
core_variable: 给定时段内的期望通信和速率、感知平均 SNR、飞行任务与避撞约束
key_finding: 把序贯决策问题转化为 episode task MDP，提出 DeepLSC 联合优化 GBS 波束成形与 UAV 轨迹
relevance: 低空经济 + ISAC + DRL，与本 Vault 的 UAV-ISAC 方向高度对口
zotero_key: 4ZKUQ3NN
pdf_key: ZMNWZNSB
doi: 10.1109/twc.2025.3583950
collection: ISAC
note_path: 02vault/ISAC/ISAC for Low-Altitude Economy DRL.md
fulltext_path: 03fulltext/ISAC/4ZKUQ3NN.md
---
- **[《Integrated Sensing and Communications for Low-Altitude Economy A Deep Reinforcement Learning Approach》](zotero://select/library/items/4ZKUQ3NN)**
<span style="color: #E63946; font-weight: bold;">作者</span>: <span style="color: #1D3557;">Ye, Mao, Yu, Sun, Fu, Xu</span>
<span style="color: #FFC107; font-weight: bold;">发表年份</span>: <span style="color: #2A9D8F;">2025</span>
<span style="color: #8E44AD; font-weight: bold;">期刊名称</span>: <span style="color: #264653;">IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS</span>

# Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement Learning Approach

---

# 📌 Basic Information（基本信息）

## Author
Xiaowen Ye, Yuyi Mao, Xianghao Yu, Shu Sun, Liqun Fu, Jie Xu

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/twc.2025.3583950

> Zotero 入口：zotero://select/library/items/4ZKUQ3NN
> PDF 入口：zotero://open-pdf/library/items/ZMNWZNSB
> 全文 Markdown：[[03fulltext/ISAC/4ZKUQ3NN]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- Low-Altitude Economy (LAE)
- Deep Reinforcement Learning
- UAV Trajectory and Beamforming Design

---

# 1. Abstract Summary（一句话总结）

> 该文研究面向低空经济（LAE）的 ISAC 系统：地面基站为授权无人机提供通信与导航服务，同时感知低空空域监视==非授权移动目标==；把该序贯决策问题转化为 episode task 型马尔可夫决策过程，并提出深度强化学习方案 DeepLSC，联合优化 GBS 波束成形与无人机轨迹，以最大化给定时段内的期望通信和速率。

---

# 2. Research Background（研究背景）

## 背景：

- 低空经济（LAE）场景下，地面基站（GBS）需同时为授权无人机（UAV）提供通信与导航服务。
- 与此同时，GBS 还需感知低空空域，监视非授权移动目标（unauthorized mobile target）。

> 原文：
> "a ground base station (GBS) provides communication and navigation services for authorized unmanned aerial vehicles (UAVs), while sensing the low-altitude airspace to monitor the unauthorized mobile target."

## Motivation（研究动机）

- 在给定飞行任务下，该问题是序贯决策问题，传统优化方法难以高效处理时变与不确定性。
- 波束成形与 UAV 轨迹存在强耦合，联合优化是提升性能的关键。

## Application Scenario（应用场景）

- 低空经济中的 UAV 通信与导航服务
- 低空空域监视与非法目标探测
- UAV 物流、巡检等场景的通信—感知一体化保障

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在低空经济场景中，如何联合优化地面基站==波束成形与无人机轨迹，在感知 SNR、飞行任务、避撞与发射功率约束==下最大化给定时段内的期望通信和速率？

核心问题：

- 如何把带飞行任务的序贯决策问题形式化为可求解的 MDP？
- 如何设计 DRL 方案处理波束成形与轨迹的联合优化？
- 如何同时满足感知平均 SNR 要求与飞行/避撞约束？
---

# 4. Related Work（相关工作）

已有方法：

1. **传统优化方法**：难以高效处理带飞行任务的序贯决策与时变性。
2. **分离设计**：分别优化通信波束与 UAV 轨迹，忽略二者耦合。
3. **通用 DRL 方法**：未针对「episode task」这一带终止条件的飞行任务结构设计。

现有不足：

- 缺少把「给定飞行任务」显式建模为 MDP episode 的工作。
- 波束成形与轨迹联合优化在时变环境下的高效求解方案不足。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 把带飞行任务的序贯决策问题转化为一类特定的马尔可夫决策过程模型，称为 **episode task**。
- 基于该建模，提出面向低空经济的 ISAC 方案 **Deep LAE-ISAC（DeepLSC）**，借助深度强化学习求解。

> 原文：
> "Typically, this is a sequential decision-making problem with the given flight mission. Thus, we transform it to a specific Markov decision process (MDP) model called episode task."
>
> 原文：
> "Based on this modeling, we propose a novel LAE-oriented ISAC scheme, referred to as Deep LAE-ISAC (DeepLSC), by leveraging the deep reinforcement"

## Model / Framework

系统模型：

- **GBS**：为授权 UAV 提供通信与导航服务，并感知低空空域。
- **授权 UAV**：执行给定飞行任务。
- **非授权移动目标**：需被感知/监视的对象。
- **优化变量**：GBS 波束成形 + UAV 轨迹

## Algorithm / Technique

采用：

- 马尔可夫决策过程（MDP）建模，具体为 episode task 形式
- 深度强化学习（DRL）
- 波束成形与 UAV 轨迹联合优化
![[Pasted image 20261014175528.png|700]]
## Key Steps

1. 建立 LAE-ISAC 系统模型：GBS 同时服务授权 UAV 并监视非授权目标。
2. 定义优化目标：最大化给定飞行时段内的期望通信和速率。
3. 列出约束：感知平均 SNR 要求、UAV 飞行任务与避撞、GBS 最大发射功率。
4. 把该序贯决策问题转化为 episode task 型 MDP（状态/动作/奖励/终止条件）。
5. 设计 DeepLSC（DRL 方案）求解波束成形与 UAV 轨迹的联合优化。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **目标**：最大化给定飞行时段（given flight period）内的期望通信和速率（expected communication sum-rate）。
- **优化变量**：GBS 波束成形、UAV 轨迹。
- **约束**：
  - 感知的平均 SNR 要求（average SNR requirement for sensing）
  - UAV 飞行任务与避撞（flight mission and collision avoidance）
  - GBS 最大发射功率（maximum transmit power）

> 原文：
> "The expected communication sum-rate over a given flight period is maximized by jointly optimizing the beamforming at the GBS and UAVs’ trajectories, subject to the constraints on the average signal-to-noise ratio requirement for sensing, the flight mission and collision avoidance of UAVs, as well as the maximum transmit power at the GBS."

> 说明：MDP 的状态/动作/奖励具体定义与 DeepLSC 的网络结构见 [[03fulltext/ISAC/4ZKUQ3NN]] 原文，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- UAV 的飞行任务预先给定（given flight mission），因此决策过程有明确终止（episode）。
- GBS 可同时执行通信波束与感知波束（ISAC 一体化）。
- 非授权目标的存在需通过感知平均 SNR 约束加以保障。

## Optimization Objective

目标：

- 在满足感知 SNR、飞行任务、避撞与功率约束下，最大化给定时段内的期望通信和速率。
---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 仿真验证（具体 UAV 数量、空域尺寸、信道参数未在当前材料中定位到集中表述）。

## Baseline

比较方法：

- 论文未在当前提取的摘要部分具名列出基线，此处不做推测。

## Metrics

评价指标：

- 给定时段内的期望通信和速率
- 感知平均 SNR
- 飞行任务完成度与避撞满足情况

## Results

主要结果：

- 所提 DeepLSC 方案通过把问题转化为 episode task MDP，实现了 GBS 波束成形与 UAV 轨迹的联合优化。

> 说明：具体的和速率增益与感知 SNR 数值未在当前材料中定位到可核验的集中表述，此处不做引述。建议查阅 [[03fulltext/ISAC/4ZKUQ3NN]] 的仿真章节。

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出面向低空经济（LAE）的 ISAC 系统模型：GBS 同时服务授权 UAV 并监视非授权目标。
2. 把带飞行任务的序贯决策问题转化为 episode task 型 MDP。
3. 提出 DeepLSC——面向 LAE 的 ISAC 深度强化学习方案，联合优化波束成形与 UAV 轨迹。
4. 在感知 SNR、飞行任务、避撞与功率约束下最大化期望通信和速率。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- ==「给定飞行任务」使决策有明确终止==，构成 episode task——这一结构性洞察是套用 DRL 的关键。
- 把通信服务与空域监视统一在同一 ISAC 框架下，是低空经济场景的实质需求。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 场景选择（低空经济 + 空域监视）切中当前热点，且是真实需求。
- episode task 的建模洞察使 DRL 应用具备结构合理性，而非简单套用。
- 约束完整（感知 SNR + 飞行任务 + 避撞 + 功率），工程可信度高。

- 局限：本文量化结果需查阅仿真章节才能评估。

---

# 10. Limitation（不足）

论文不足：

1. DRL 方案的训练样本效率与收敛性依赖环境设计。
2. 仿真验证，无实测或硬件在环。
3. 未考虑 UAV 间通信干扰或更大规模集群场景。
4. 具体量化增益需查阅仿真章节。

未来可能改进：

- 扩展到多 UAV、多 GBS 协同场景。
- ==考虑 UAV 能耗与续航约束==。
- 在真实低空场景做实测验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 「任务有明确终止」这一结构特性决定了该用 episode task 而非 continuing task 的 MDP 建模。
- 低空经济的核心需求之一是「服务 + 监管」并存（服务授权 UAV、监视非授权目标），ISAC 天然适配。
- 波束成形与轨迹联合优化是 UAV-ISAC 的标准难题，DRL 是处理其时变性的主流工具。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV-ISAC 方向直接对口，是低空经济场景的重要参考。
- episode task 建模可直接借鉴到自己的 UAV 任务型决策问题。
- 感知 SNR + 避撞 + 功率的约束组合可作为自己问题建模的模板。

## Possible Ideas

可能的新想法：

- 在 DeepLSC 基础上加入 UAV 能耗约束，研究续航与性能的权衡。
- 扩展到多 GBS 协同，研究切换与协作感知。
- 对比 DRL 与 [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] 的优化方法在同一场景下的性能与实时性。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同为 UAV-ISAC 轨迹优化，该文用优化方法，本文用 DRL
- [[02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks|SNN-DRL ISAC V2X]] — 同为 DRL 驱动的 ISAC，该文面向 V2X 且关注能耗，本文面向低空经济

---

# 13. Summary Card（快速复习）

## Problem

> 低空经济中 GBS 需同时服务授权 UAV 与监视非授权目标，波束成形与轨迹的联合优化是带飞行任务的序贯决策难题。

## Method

> 把问题转化为 episode task 型 MDP，提出 DeepLSC（DRL 方案）联合优化 GBS 波束成形与 UAV 轨迹。

## Result

> 在感知 SNR、飞行任务、避撞与功率约束下最大化给定时段的期望通信和速率（具体数值见全文仿真章节）。

## Importance

> 面向低空经济这一新兴场景，给出了「服务 + 监管」一体化的 ISAC-DRL 解决方案。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决低空经济中 GBS 同时服务授权 UAV 与监视非授权目标时，波束成形与 UAV 轨迹的联合优化问题。

Q:
核心方法是什么？

A:
把带飞行任务的序贯决策转化为 episode task 型 MDP，用 DRL 方案 DeepLSC 联合优化波束成形与 UAV 轨迹。

Q:
最大贡献是什么？

A:
提出面向低空经济的 ISAC-DRL 方案 DeepLSC，并给出 episode task 这一适配飞行任务的 MDP 建模方式。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `4ZKUQ3NN`，PDF 附件 `ZMNWZNSB`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/4ZKUQ3NN]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 具体的和速率增益、感知 SNR 数值与仿真参数未在当前材料中定位到集中表述，已在正文如实标注，未做推测。