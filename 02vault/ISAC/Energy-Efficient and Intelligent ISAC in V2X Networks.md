---
title: "Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-Driven DRL"
aliases:
  - SNN-DRL ISAC
  - V2X 通感一体化
tags:
  - literature-note
  - reading-note
  - ISAC
  - DRL
created: 2026-10-13
source: IEEE Transactions on Wireless Communications, 2025
author: Chen Shang, Jiadong Yu, Dinh Thai Hoang
year: 2025
journal: IEEE Transactions on Wireless Communications

theme: 用脉冲神经网络驱动的深度强化学习实现车联网 ISAC 的节能波束成形
study_area: 通感一体化 / V2X / 深度强化学习
methodology: 马尔可夫决策过程建模 + 脉冲神经网络驱动 DRL（SNN-DRL）+ 波束成形与功率联合优化
core_variable: 感知精度、通信性能、神经网络能耗
key_finding: 用 SNN 降低 DRL 能耗，RSU 可仅依据当前感知信息制定波束方案，免除大量导频与 CSI 获取
relevance: ISAC 与学习方法的结合，可为 UAV-ISAC 的实时决策提供低能耗方案参考

type: literature-note
zotero_key: "LH73Q4RG"
pdf_key: "45ZO0OTD"
doi: "10.1109/twc.2025.3589438"
collection: "ISAC"
note_path: "02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks.md"
fulltext_path: "03fulltext/ISAC/LH73Q4RG.md"
status:
  - Reading
rating: 四星
---
# Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-Driven DRL

---

# 📌 Basic Information（基本信息）

## Author
Chen Shang, Jiadong Yu, Dinh Thai Hoang

## Year
2025

## Source
IEEE Transactions on Wireless Communications｜DOI: 10.1109/twc.2025.3589438

> Zotero 入口：zotero://select/library/items/LH73Q4RG
> PDF 入口：zotero://open-pdf/library/items/45ZO0OTD
> 全文 Markdown：[[03fulltext/ISAC/LH73Q4RG]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- Vehicle-to-Everything (V2X)
- Deep Reinforcement Learning
- Spiking Neural Networks

---

# 1. Abstract Summary（一句话总结）

> 该文面向车联网 ISAC 场景，用马尔可夫决策过程建模动态不确定性，提出脉冲神经网络驱动的深度强化学习算法，联合优化波束成形与功率分配，在降低神经网络能耗的同时免除大量导频与完整 CSI 获取。

---

# 2. Research Background（研究背景）

## 背景：

- ISAC 正成为车联网（V2X）系统的关键使能技术。
- 但在 V2X 动态不确定环境中，设计高效的 ISAC 波束成形方案以实现精确感知并提升通信性能，存在显著挑战。
- 人工智能技术虽提供有前景的方案，但神经网络的能源密集特性给通信基础设施带来沉重负担。

> 原文：
> "However, designing efficient beamforming schemes for ISAC signals to achieve accurate sensing and enhance communication performance in the dynamic and uncertain environments of V2X networks presents significant challenges."
>
> 原文：
> "While artificial intelligence technologies offer promising solutions, the energy-intensive nature of neural networks imposes substantial burdens on communication infrastructures."

## Motivation（研究动机）

- 传统方法依赖大量导频信号与广泛的 CSI 获取，开销大。
- 常规 DRL 能耗高，难以在基础设施侧持续部署。
- 需要一种既智能又节能的 ISAC 波束成形方案。

## Application Scenario（应用场景）

- 车联网路侧单元（RSU）的 ISAC 波束成形
- 需要低能耗智能决策的边缘通信设施
- UAV-ISAC 中受限算力下的实时波束决策

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在降低神经网络能耗的同时，让 RSU 仅凭当前感知信息即可制定 ISAC 波束成形与功率分配方案，摆脱对大量导频与完整 CSI 的依赖？

核心问题：

- 如何建模 V2X 网络的动态与不确定性？
- 如何用低能耗网络（SNN）承载 DRL 决策？
- 波束成形与功率如何联合优化以兼顾感知与通信？
---

# 4. Related Work（相关工作）

已有方法：

1. **传统导频/CSI 方法**：依赖大量导频信号与广泛 CSI 获取，开销高。
2. **常规 DRL 方法**：能处理动态环境，但神经网络能耗密集。
3. **单目标优化**：分别优化感知或通信，未充分联合。

现有不足：

- 导频与 CSI 获取开销制约实时性。
- AI 方案的能耗给通信基础设施带来负担。
- 缺少同时解决智能化与低能耗的方案。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 用马尔可夫决策过程（MDP）框架建模 V2X 网络的动态与不确定性。
- 在该框架下，路侧单元（RSU）仅依据当前感知信息即可制定波束成形方案，免除大量导频与广泛 CSI 获取。
- 引入脉冲神经网络驱动的深度强化学习（SNN-DRL），联合优化波束成形与功率分配。

> 原文：
> "we first leverage a Markov Decision Process framework to model the dynamic and uncertain nature of V2X networks. This framework allows the roadside unit to develop beamforming schemes relying solely on its current sensing information, eliminating the need for numerous pilot signals and extensive CSI acquisition."
>
> 原文：
> "We then introduce an advanced deep reinforcement learning (DRL) algorithm, enabling the joint optimization of beamforming and power"

## Model / Framework

系统模型：

- **决策主体**：路侧单元（RSU）。
- **状态来源**：仅依赖当前感知信息（sensing information），不需完整 CSI。
- **优化变量**：波束成形 + 功率分配（联合优化）。
- **能耗考量**：用脉冲神经网络（SNN）替代常规神经网络以降低能耗。

## Algorithm / Technique

采用：

- 马尔可夫决策过程（MDP）建模
- 脉冲神经网络（SNN）
- 深度强化学习（DRL）
- 波束成形与功率联合优化

## Key Steps

1. 将 V2X 网络的动态与不确定性建模为 MDP。
2. 设计状态空间，使其仅由 RSU 当前感知信息构成。
3. 用 SNN 构建 DRL 网络，降低推理能耗。
4. 训练该 SNN-DRL 智能体，联合输出波束成形与功率分配决策。
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **MDP 建模**：状态由 RSU 当前感知信息构成；动作为波束成形与功率分配；奖励兼顾感知精度与通信性能。
- **优化目标**：联合优化波束成形与功率分配，同时降低网络能耗。

> 说明：MDP 的状态/动作/奖励具体定义与 SNN-DRL 的网络结构细节，以 [[03fulltext/ISAC/LH73Q4RG]] 原文为准，此处不重述未逐项核验的公式。PDF 页码未验证。

## Assumptions

假设：

- RSU 的当前感知信息足以支撑波束决策，无需完整 CSI。
- SNN 的事件驱动特性可显著降低 DRL 推理能耗。
- V2X 环境动态特性可被 MDP 合理刻画。

## Optimization Objective

目标：

- 在保证感知精度与通信性能的前提下，最小化神经网络带来的能耗开销。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- V2X 网络仿真环境（具体参数未在当前全文中定位到集中表述）。

## Baseline

比较方法：

- 依赖导频/CSI 的传统波束成形方案
- 常规（非 SNN）DRL 方案

> 说明：论文摘要中明确了对照思路，但具体基线名称未在当前全文中逐一定位，此处不做推测。

## Metrics

评价指标：

- 感知精度
- 通信性能
- 神经网络能耗
- 导频/CSI 开销

## Results

主要结果：

- RSU 可仅凭当前感知信息制定波束方案，免除大量导频与广泛 CSI 获取。
- **能耗显著降低**：SNN 用累加（AC）替代乘累加（MAC）运算，训练能耗降低约 **2.58 倍**，推理能耗降低约 **6.87–7.125 倍**。
- **收敛与性能**：Spiking-AC 与 PPO 收敛最快、奖励最高；DDPG 表现中等（离策略采样引入次优样本）。
- 在保持性能的同时实现了更低能耗、更优通信性能与更高感知精度。

> 原文（能耗结论）：
> "Extensive simulation results validate the effectiveness of the proposed scheme with lower energy consumption, superior communication performance, and improved sensing accuracy."
>
> 原文（SNN 机理）：
> "to perform training and inference operations (e.g., forward and back-propagation) utilizing simple accumulation (AC) instead of MAC operations, thus significantly reducing computational complexity and energy consumption"
>
> 原文（收敛对比）：
> "Spiking-AC and PPO demonstrate the fastest convergence and achieve the highest rewards, highlighting their ability to effectively balance the dual objectives of maximizing the sum-rate and enhancing sensing accuracy"

> 说明：能耗倍数（2.58× 训练 / 6.87–7.125× 推理）取自原文 Fig. 4 的数值标注；基线为 PPO、DDPG、DQN 等。
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出面向 V2X 的节能智能 ISAC 系统。
2. 用 MDP 框架建模 V2X 网络的动态与不确定性。
3. 使 RSU 仅凭当前感知信息即可制定波束方案，免除大量导频与广泛 CSI 获取。
4. 引入 SNN 驱动的 DRL，联合优化波束成形与功率分配，缓解神经网络能耗负担。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 把 SNN 的低能耗特性引入 ISAC-DRL，是针对「AI 能耗」这一实际部署瓶颈的针对性设计。
- 感知信息直接作为决策状态，绕开 CSI 获取开销，是系统层面的实用化改进。

## My Evaluation

我的评价：

四星

创新程度：

中高

理由：

- 把 SNN 与 ISAC-DRL 结合的切入点务实，回应了边缘设施能耗这一真实约束。
- 但创新性主要在于组合应用而非理论突破；具体能耗收益数值需看全文实验部分才能定量评估。

---

# 10. Limitation（不足）

论文不足：

1. 仅凭当前感知信息决策，牺牲了部分 CSI 精度，在快时变信道下可能性能受限。
2. SNN 训练方法（如 surrogate gradient）本身存在近似误差。
3. 论文仿真验证，缺少真实 V2X 路测。
4. 具体能耗与性能权衡的定量结论需查阅全文实验章节。

未来可能改进：

- 在真实 V2X 平台或硬件在环环境验证 SNN 能耗收益。
- 研究 SNN 与常规 ANN 在不同业务负载下的切换策略。
- 把该低能耗决策框架迁移到 UAV 等 airborne ISAC 平台。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 「AI 方法能耗」是边缘通信设施部署中容易被忽视但很实际的约束，SNN 是针对性解法之一。
- 用感知信息直接替代 CSI 作为决策状态，是降低开销的系统级思路，不只是算法级优化。
- MDP 是建模通信网络动态不确定性的标准框架，适合承载 DRL。

## Connection With My Work

和我的研究/项目关系：

- 该文的低能耗智能决策思路可直接迁移到 UAV-ISAC（机载算力与电池更受限）。
- 免 CSI 的感知驱动决策对 UAV 高移动性场景尤其有吸引力。
- SNN-DRL 可作为自己后续实时波束/轨迹决策的候选方案之一。

## Possible Ideas

可能的新想法：

- 把 SNN-DRL 用于 UAV-ISAC 的联合轨迹与波束优化，评估机载能耗收益。
- 对比 SNN 与量化 ANN 在同等精度下的实际能耗与延迟。
- 研究感知信息不完备时的鲁棒决策策略。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同为 ISAC 权衡设计，该文用优化方法，本文用学习方法

---

# 13. Summary Card（快速复习）

## Problem

> V2X 中 ISAC 波束设计面临动态不确定性挑战，且 AI 方案的神经网络能耗给基础设施带来负担。

## Method

> MDP 建模动态环境，RSU 仅凭感知信息决策；用 SNN 驱动 DRL 联合优化波束成形与功率分配。

## Result

> 免除了大量导频与广泛 CSI 获取需求，并通过 SNN 缓解了神经网络能耗负担。

## Importance

> 把低能耗 SNN 引入 ISAC-DRL，回应了边缘通信设施部署 AI 的真实能耗约束。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 V2X-ISAC 波束设计中的动态不确定性挑战，以及 AI 方案神经网络能耗过高的问题。

Q:
核心方法是什么？

A:
MDP 建模 + 感知信息直接作为状态（免 CSI）+ SNN 驱动的 DRL 联合优化波束与功率。

Q:
最大贡献是什么？

A:
用脉冲神经网络降低 ISAC-DRL 的能耗，同时让 RSU 无需完整 CSI 即可完成波束决策。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `LH73Q4RG`，PDF 附件 `45ZO0OTD`。
- PDF 为开放获取版本（arXiv 预印本），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/LH73Q4RG]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- 能耗倍数与收敛对比已按原文 Fig. 4 与仿真章节补入「7. 实验与验证」。基线为 PPO、DDPG、DQN。