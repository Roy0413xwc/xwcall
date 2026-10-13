---
title: "ISAC from the Sky: UAV Trajectory Design for Joint Communication and Target Localization"
aliases:
  - ISAC from the Sky
  - MSTD 轨迹设计
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
created: 2026-10-13
source: IEEE Journal on Selected Areas in Communications, 2022
author: Xiaoye Jing, Fan Liu, Christos Masouros, Yong Zeng
year: 2022
journal: IEEE Journal on Selected Areas in Communications

theme: 机载 ISAC 场景下通过无人机轨迹与带宽分配联合设计权衡通信与感知性能
study_area: 通感一体化 / UAV 轨迹设计 / 目标定位
methodology: 加权和归一化优化 + 多阶段轨迹设计（MSTD）+ 迭代算法
core_variable: 总传输数据量（通信）、Cramér-Rao 界（感知）、机载能量
key_finding: 提出 MSTD 与迭代算法获得轨迹局部最优解，揭示 C&S 权衡与能量约束对轨迹的决定作用
relevance: 直接对应 UAV-ISAC 的轨迹—资源联合优化，是本 Vault 该方向的核心参考之一

type: literature-note
zotero_key: "BFPD3VN4"
pdf_key: "ZWFR6M4M"
doi: "10.1109/TWC.2024.3396571"
collection: "UAV"
note_path: "02vault/UAV/ISAC from the Sky UAV Trajectory Design.md"
fulltext_path: "03fulltext/UAV/BFPD3VN4.md"
status:
  - Reading
rating: 五星
---
# ISAC from the Sky: UAV Trajectory Design for Joint Communication and Target Localization

---

# 📌 Basic Information（基本信息）

## Author
Xiaoye Jing, Fan Liu, Christos Masouros, Yong Zeng

## Year
2022

## Source
IEEE Journal on Selected Areas in Communications｜DOI: 10.1109/TWC.2024.3396571

> Zotero 入口：zotero://select/library/items/BFPD3VN4
> PDF 入口：zotero://open-pdf/library/items/ZWFR6M4M
> 全文 Markdown：[[03fulltext/UAV/BFPD3VN4]]

## Research Area

- Integrated Sensing and Communication (ISAC)
- UAV Trajectory Design
- Target Localization
- Nonconvex Optimization

---

# 1. Abstract Summary（一句话总结）

> 该文研究机载 ISAC 场景，让无人机同时充当通信基站与雷达，通过联合设计无人机轨迹与用户带宽分配来同时提升通信与感知性能，并以 Cramér-Rao 界度量感知、以总传输数据量度量通信，提出多阶段轨迹设计（MSTD）与迭代算法求局部最优解。

---

# 2. Research Background（研究背景）

## 背景：

- 下一代无线网络有望超越传统通信服务，提供高精度、鲁棒的感知能力，包括定位、跟踪与导航。
- 在传统无线系统中，通信与感知（C&S）功能通常被当作分离的目标处理，导致资源利用低效。
- 无人机作为空中平台，其可持续性由机载电池决定，因此能量供给必须作为轨迹设计的约束。

> 原文：
> "Next-generation wireless networks are expected to go beyond traditional communication services, offering highly accurate and robust sensing, including localization, tracking and navigation [1], [2]."
>
> 原文：
> "In conventional wireless systems, communication and sensing (C&S) functionalities are typically treated as separated objectives, leading to an inefficient resource utilization."
>
> 原文：
> "Since UAV’s sustainability is determined by its onboard battery, energy supply is considered as a constraint in the trajectory design."

## Motivation（研究动机）

- 现有工作常把 C&S 分离设计，未充分利用 ISAC 的一体化增益。
- UAV 轨迹是同时影响通信链路质量与感知几何的关键自由度，但联合设计问题非凸、难以直接求解。

## Application Scenario（应用场景）

- 无人机同时提供区域通信覆盖与目标探测定位
- 应急场景下临时基站兼感知节点
- UAV-ISAC 系统中的轨迹—资源联合调度
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在机载 ISAC 场景中，如何联合设计无人机轨迹与用户带宽分配，在机载能量约束下实现通信性能与感知性能的灵活权衡？

核心问题：

- 如何在同一目标框架下度量并归一化通信（数据量）与感知（CRB）两个量纲不同的指标？
- 如何在能量约束下求解非凸的轨迹优化问题？
- C&S 权衡权重如何决定最终的无人机轨迹形状？

---

# 4. Related Work（相关工作）

已有方法：

1. **分离式设计**：传统无线系统把通信与感知作为分离目标分别优化，资源利用低效。
2. **单功能无人机场景**：只做通信或只做感知的无人机轨迹设计，可作为对照基线。
3. **无能量约束的 ISAC 轨迹设计**：忽视机载电池对可持续性的限制。

现有不足：

- 缺少把能量供给显式纳入约束的 UAV-ISAC 联合轨迹设计。
- 直接求解加权和轨迹优化问题困难，缺少可实用的求解算法。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 把 UAV 同时视为通信基站与雷达：发送信号服务用户，同时用同一信号定位目标。
- 以归一化后的加权和目标统一度量通信与感知性能，实现灵活权衡。
- 提出多阶段轨迹设计（MSTD）提升轨迹建模精度，并用迭代算法求局部最优解。

> 原文：
> "A tradeoff objective is formulated with normalization. To achieve a flexible tradeoff between C&S, the trajectory design is formulated as a weighted sum optimization problem."
>
> 原文：
> "To improve the formulation accuracy of trajectory design, a multi-stage trajectory design (MSTD) is proposed."

## Model / Framework

系统模型：

- **UAV 角色**：同时作为通信基站（向用户发射信号）与雷达（利用回波定位目标）。
- **优化变量**：UAV 轨迹 + 用户带宽分配。
- **约束**：机载能量供给。
- **通信指标**：总传输数据量（total transmitted data）。
- **感知指标**：Cramér-Rao 界（CRB）。

## Algorithm / Technique

采用：

- 加权和（weighted sum）优化 + 归一化处理
- 多阶段轨迹设计（MSTD）
- 迭代算法求局部最优解（非凸问题）

## Key Steps

1. 建立 UAV-ISAC 系统模型，定义通信指标（总数据量）与感知指标（CRB）。
2. 对两个指标做归一化，构造加权和权衡目标。
3. 加入机载能量供给约束，形成轨迹设计问题。
4. 用多阶段轨迹设计（MSTD）提升轨迹离散化与建模精度。
5. 针对难以直接求解的非凸问题，设计迭代算法获得 UAV 轨迹的局部最优解。

> 原文：
> "While the resultant design problem is difficult to solve directly, an iterative algorithm is developed to obtain a local optimal solution of UA V trajectory."
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **优化目标**：归一化后的通信与感知加权和（flexible tradeoff between C&S）。
- **通信侧**：最大化总传输数据量。
- **感知侧**：最小化目标定位的 Cramér-Rao 界（CRB）。
- **约束**：机载能量供给（onboard battery）。
- **决策变量**：UAV 轨迹、用户带宽分配。

> 说明：论文给出了上述指标的完整闭式表达，具体公式以 [[03fulltext/UAV/BFPD3VN4]] 原文为准；此处不重述未逐项核验的系数推导。PDF 页码未验证。

## Assumptions

假设：

- UAV 可同时承担通信与雷达功能（ISAC 硬件/信号共享）。
- 机载能量是有限且可建模为轨迹函数的关键约束。
- 通信与感知指标可通过归一化放入同一加权和目标比较。

## Optimization Objective

目标：

- 在能量约束下，通过调节加权系数在通信数据量与感知 CRB 之间取得可控权衡。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 数值仿真（numerical results）验证，展示不同 C&S 权衡与能量供给下得到的 UAV 轨迹。

> 原文：
> "Finally, numerical results are presented to show UA V trajectories determined by the tradeoff between C&S and the energy supply."

> 说明：具体仿真参数（用户数、UAV 高度、带宽、能量预算数值）未在当前全文中定位到集中表述，此处不做推测。

## Baseline

比较方法：

- 单功能无人机场景（只通信 / 只感知），用于凸显 ISAC 一体化收益。

> 原文：
> "Benefits of ISAC-based UA V scenario are highlighted by comparing the single-functional UA V scenarios."

## Metrics

评价指标：

- 总传输数据量（通信性能）
- Cramér-Rao 界 CRB（感知性能）
- 机载能量消耗

## Results

主要结果：

- 在**相同能量供给**下，带轨迹设计的 ISAC 方案在 C&S 性能上**优于分离方案**（即两架无人机分别专用于通信或感知的传统方案）。
- 带宽分配带来通信性能改善（速率有明确增量）。
- 能量供给增长会同时改善 C&S 性能，但**当总能量 Etot 较大时，CRB 下降变缓**（存在边际收益递减）。

**仿真设置（原文 V 节）：**

- BS 位置设为 [xB, yB]ᵀ = [0, 0]ᵀ；感知目标（STs）与通信用户（CUs）位置由仿真中的均匀点分布生成。
- ST 坐标估计的 MSE 通过 **100 次蒙特卡洛仿真**评估；仿真参数见原文 Table I（含 N0 = -170 dBm/Hz、Pt = 20 dBm、B = 10 MHz 等）。
- **对照基线**：传统 UAV 方案——同一区域内配置两架无人机，分别专用于通信或感知。

> 原文：
> "The results show that with the same energy supply, the ISAC scheme with the trajectory design outperforms the separate scheme in terms of C&S performances."
>
> 原文：
> "We should notice that even though the growth of energy supply results in a performance improvement in both C&S, the CRB decreases slowly when Etot is large."
>
> 原文（仿真设置）：
> "We set [xB, yB]T = [0, 0]T. The locations of STs and CUs are generated using a uniform point distribution in the simulation. The MSE of a STs coordinate estimate is evaluated through Monte Carlo simulation with 100 runs."
>
> 原文（基线）：
> "We compare C&S performances in ISAC-based UAV scheme with a traditional UAV scheme where the designated area contains two UAVs, which are dedicated to communication or sensing respectively."


> 原文：
> "an iterative algorithm is developed to obtain a local optimal solution of UA V trajectory."
>
> 原文：
> "Benefits of ISAC-based UA V scenario are highlighted by comparing the single-functional UA V scenarios."
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 在机载域研究 ISAC，让 UAV 同时作为通信基站与雷达。
2. 用归一化加权和目标统一度量通信（总传输数据量）与感知（CRB），实现 C&S 灵活权衡。
3. 提出多阶段轨迹设计（MSTD），提升轨迹设计建模精度。
4. 针对难以直接求解的非凸问题，设计迭代算法获得 UAV 轨迹局部最优解。
5. 通过与单功能 UAV 场景对比，凸显 ISAC 一体化收益。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 首次（在该设定下）把能量供给显式纳入 UAV-ISAC 轨迹设计约束。
- MSTD 提升了轨迹离散化建模精度，优于单阶段建模。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 该文是 UAV-ISAC 轨迹设计的奠基性工作之一，与本 Vault 的研究方向高度对口。
- 归一化加权和的建模方式通用，可直接迁移到自己后续的轨迹—波束联合优化。
- 明确指出只能获得局部最优，表述诚实。

---

# 10. Limitation（不足）

论文不足：

1. 迭代算法只能保证局部最优，无全局最优性保证。
2. 验证为数值仿真，无实测或硬件验证。
3. 加权系数需人工设定，论文未给出自适应调参策略。
4. 能量模型为简化约束，未涉及更复杂的能耗动力学。

未来可能改进：

- 引入全局优化或学习式方法改善局部最优问题。
- 扩展到多 UAV 协同 ISAC 场景。
- 联合优化波束赋形与轨迹（本文只做轨迹 + 带宽）。
---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- ISAC 的核心难点之一是通信与感知指标量纲不同，必须归一化后才能放进同一目标比较。
- CRB 是感知性能的标准度量，与通信的数据量指标可直接构成权衡对。
- UAV 的能量约束会实质性改变最优轨迹形状，不能只按几何最优设计。
- 非凸轨迹问题在工程上通常接受局部最优，关键是给出可收敛的迭代算法。

## Connection With My Work

和我的研究/项目关系：

- 该文是 UAV-ISAC 轨迹设计的核心参考，与本 Vault 的 ISAC 方向直接对口。
- 归一化加权和建模可直接用于自己的通信—感知权衡问题。
- MSTD 的多阶段离散化思路可用于提升自己轨迹优化的建模精度。

## Possible Ideas

可能的新想法：

- 把本文的轨迹设计扩展为轨迹 + 波束赋形联合优化。
- 用强化学习替代迭代算法，改善局部最优并提升实时性。
- 研究多 UAV 协同下的 C&S 权衡与能量分配。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|无人机应急通信层次最优控制]] — 同为 UAV 轨迹优化，本文侧重 ISAC 权衡，该文侧重应急通信调度
- [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]] — 提供 UAV 空地信道实测依据，可用于本文信道假设的校验

---

# 13. Summary Card（快速复习）

## Problem

> 机载 ISAC 中通信与感知常被分离设计，且 UAV 轨迹联合优化问题非凸、受机载能量约束，难以直接求解。

## Method

> 归一化加权和统一度量通信数据量与感知 CRB；提出多阶段轨迹设计（MSTD）并用迭代算法求局部最优。

## Result

> 得到由 C&S 权衡与能量供给共同决定的 UAV 轨迹局部最优解，且 ISAC 一体化优于单功能 UAV 场景。

## Importance

> UAV-ISAC 轨迹设计的奠基性工作之一，提供了通信—感知权衡的通用建模范式。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决机载 ISAC 中 UAV 轨迹与带宽分配的联合优化问题，在能量约束下权衡通信数据量与感知 CRB。

Q:
核心方法是什么？

A:
归一化加权和目标 + 多阶段轨迹设计（MSTD）+ 迭代算法求局部最优。

Q:
最大贡献是什么？

A:
把能量约束显式纳入 UAV-ISAC 轨迹设计，并给出可实用的 MSTD 与迭代求解方案。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `BFPD3VN4`，PDF 附件 `ZWFR6M4M`。
- PDF 为开放获取版本（UCL Discovery 机构库），经 pypdf 提取全文。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/BFPD3VN4]]。
- PDF 页码未验证（pypdf 提取不含可靠页码映射）。
- **作者已按 PDF 原文校正**：导入清单记为 Xiao/Zeng，实际为 Jing, Liu, Masouros, Zeng。
- 仿真具体参数与公式闭式表达未在当前全文中定位到集中表述，已在正文如实标注，未做推测。