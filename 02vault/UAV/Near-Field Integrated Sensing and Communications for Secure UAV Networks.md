---
title: "Near-Field Integrated Sensing and Communications for Secure UAV Networks"
aliases:
  - 近场安全 UAV ISAC
  - Near-Field Secure UAV
tags:
  - literature-note
  - reading-note
  - ISAC
  - UAV
  - near-field
  - physical-layer-security
created: 2026-10-13
source: IEEE Journal on Selected Areas in Communications, 2025
author: Jingjing Zhao, Songtao Xue, Kaiquan Cai, Xidong Mu, Yuanwei Liu, Yanbo Zhu
year: 2025
journal: IEEE JSAC

theme: 用近场感知实时定位窃听无人机（E-UAV），并把人工噪声同时用于干扰与感知，联合设计波束与轨迹最大化保密速率
study_area: 通感一体化 / 近场通信 / 无人机安全通信 / 物理层安全
methodology: 近场 3D 速度感知（ML）+ EKF 轨迹跟踪 + AO 交替优化（SCA + DC 罚函数）联合波束成形与 C-UAV 轨迹
key_finding: 所提跟踪方案使保密速率几乎逼近"E-UAV 轨迹完全已知"的理想上界，且明显优于 C-UAV 静止方案
relevance: 近场 + ISAC + 安全是近年的热点组合，其"AN 一物两用"与"感知精度—保密速率折衷"结论对本方向有价值

type: literature-note
zotero_key: "SFHWJXB7"
pdf_key: "UGBKAK29"
doi: "10.1109/JSAC.2025.3608737"
collection: "UAV"
note_path: "02vault/UAV/Near-Field Integrated Sensing and Communications for Secure UAV Networks.md"
fulltext_path: "03fulltext/UAV/SFHWJXB7.md"
status:
  - Reading
rating: 五星
---

# Near-Field Integrated Sensing and Communications for Secure UAV Networks

---

# 📌 Basic Information（基本信息）

## Author
Jingjing Zhao, Songtao Xue, Kaiquan Cai, Xidong Mu, Yuanwei Liu, Yanbo Zhu

## Year
2025

## Source
IEEE Journal on Selected Areas in Communications｜DOI: 10.1109/JSAC.2025.3608737

> Zotero 入口：zotero://select/library/items/SFHWJXB7
> PDF 入口：zotero://open-pdf/library/items/UGBKAK29
> 全文 Markdown：[[03fulltext/UAV/SFHWJXB7]]

## Research Area

- Near-Field Integrated Sensing and Communications (ISAC)
- UAV Networks / Low-Altitude Security
- Physical Layer Security
- Extended Kalman Filter (EKF) Tracking

---

# 1. Abstract Summary（一句话总结）

> 该文提出面向安全 UAV 网络的**近场 ISAC 框架**：地面基站（GBS，大孔径）与通信无人机（C-UAV）通信，同时存在窃听无人机（E-UAV）；**人工噪声（AN）一物两用**——既干扰 E-UAV 又用于感知；先利用近场空间域变化的多普勒观测估计 E-UAV 三维速度并用 EKF 融合校正轨迹，再联合设计 GBS 波束成形与 C-UAV 轨迹以最大化瞬时保密速率。

---

# 2. Research Background（研究背景）

## 背景：

- UAV 网络在 5G/6G 中应用广泛，但空—地链路的视距主导特性使其**易被窃听**。
- 物理层安全（人工噪声 AN）是经典对策，但 AN 的设计依赖窃听者的位置信息。

## Motivation（研究动机）

- E-UAV 是**非协作节点**，GBS 无法先验获知其位置与运动模型。
- 传统做法要么假设窃听者位置已知（不现实），要么把感知与通信分开设计（频谱/能量低效）。
- 近场（大孔径阵列）带来新机遇：多普勒频移在**空间域上是变化的**，这提供了远场所没有的观测维度。

> 原文（Remark 1）：
> "Different from the far-field scenario, due to the different azimuth and elevation angles observed at each GBS antenna, the Doppler frequency shift varies in the spatial domain for the near-field propagation."

## Application Scenario（应用场景）

- 存在窃听 UAV 的低空安全通信
- 大孔径地面基站（近场条件成立）服务 UAV 的场景
- 需要兼顾通信保密性与目标跟踪精度的双功能系统

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 在 E-UAV 位置与运动模型均未知的条件下，如何实时获得其位置，并据此联合设计 GBS 波束与 C-UAV 轨迹，在**保证感知精度**的前提下最大化瞬时保密速率？

核心问题：

- 如何从近场回波中估计非协作 E-UAV 的 **3D 速度**？
- 如何校正定位预测误差，实现实时轨迹跟踪？
- 感知精度约束与保密速率之间如何折衷，如何求解该非凸问题？

---

# 4. Related Work（相关工作）

已有方法：

1. **传统 AN 物理层安全**：假设窃听者 CSI 或位置已知。
2. **远场 ISAC 安全设计**：多普勒在远场不随空间变化，无法据此提取 3D 速度。
3. **分离的感知与保密通信**：两套资源、两套波形，频谱与能量效率低。

现有不足：

- E-UAV 非协作 → 位置未知 → 传统 AN 设计失效。
- 远场模型缺乏空间变化的多普勒观测，难以从回波直接解 3D 速度。
- 未见把 AN 同时用作干扰源与感知信号的一体化设计。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- **AN 一物两用**：`xl,i(n) = wc,l,i * sl(n) + we,l,i * al(n)`，即发射信号 = 信息波束（承载 `sl(n)`）+ AN 波束（承载 `al(n)`）。AN 既干扰 E-UAV，又作为感知信号被 GBS 接收回波。
- **两阶段方案**：
  - **Stage 1（感知）**：从回波中用匹配滤波估计 `{rel, θel, ϕel}`，再利用近场空间变化多普勒估计 3D 速度，用 **EKF** 融合预测与测量以校正轨迹。
  - **Stage 2（优化）**：基于预测的 E-UAV 位置，联合设计 GBS 波束成形与 C-UAV 轨迹，最大化瞬时保密速率并保证感知精度。

## Model / Framework

- 场景：大孔径 GBS（UPA，M 天线）与 1 个 C-UAV 通信，存在 1 个 E-UAV。
- 近场回波模型（式 6）：

> 原文：
> "y_bl(n) = β/(rel)² * A(rel, θel, ϕel) ⊙ D_{l,n}(f_Dl) * xl(n) + z_bl(n)"

- 阵列响应向量按**逐天线距离**构造（式 3），体现近场球面波特性：
  `α(rel, θel, ϕel) = [e^{−j2π/λ * r̄el,1}, ..., e^{−j2π/λ * r̄el,M}]ᵀ`
- 时变相位—多普勒向量（式 5）：`dl,n(f_Dl) = [e^{−j2πf_Dl,1 nTs}, ..., e^{−j2πf_Dl,M nTs}]ᵀ`
- 通信速率（式 9）与泄露速率（式 10），保密速率（式 12）：`Rs_l = [Rc_l − Re_l]⁺`

## Algorithm / Technique

采用：

- **3D 速度感知**：把 N 个时隙回波聚为矩阵 `Ybl = β Xl(f_Dl) + Zbl`，利用多普勒与 3D 速度的投影关系（式 15-16）：
  `f_Dl,m = (1/λ)(vre,l,m + vθe,l,m + vϕe,l,m)`
  其中各分量是径向/方位/俯仰速度沿"E-UAV—第 m 天线"连线的投影，用 **ML（最大似然）** 求解。
- **EKF 轨迹跟踪**：融合预测状态与测量状态，及时校正定位误差。
- **AO（交替优化）求解非凸问题（34）**：
  - 子问题 1（GBS 波束成形）：引入半正定松弛 `Wc,l = wc,l wc,lᴴ`、`We,l = we,l we,lᴴ`；引入指数辅助变量 `τ, ε, δ, ϵ` 把分式目标转为 `τ − ε − δ + ϵ`；对非凸约束做一阶泰勒展开（SCA）；用 **Schur 补**处理感知精度约束；对秩一约束用 **DC（difference of convex）表示** `ψi,l = ‖Wi,l‖* − ‖Wi,l‖₂ = 0` 加罚函数法（`ω` 由小逐步增大）。
  - 子问题 2（C-UAV 轨迹）：固定波束后优化 `qc,l`，同样用 SCA 处理。

## Key Steps

1. 在每个 CPI（相干处理间隔）内，GBS 发射信息信号 + AN。
2. 接收 E-UAV 回波，用匹配滤波（式 13）估计 `{r̂el, θ̂el, ϕ̂el}`。
3. 用近场空间变化多普勒 + ML 估计 E-UAV 的 3D 速度 `{vre,l, vθe,l, vϕe,l}`。
4. 用 EKF 融合预测状态与测量状态，输出 E-UAV 实时位置估计。
5. 以预测位置 `q̂e,l|l−1` 计算 E-UAV 信道 `Ĥbel|l−1`，构造并求解保密速率最大化问题（AO + SCA）。
6. 迭代至收敛，输出 GBS 波束 `wc,l, we,l` 与 C-UAV 位置 `qc,l`。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- 优化问题（式 34）：最大化瞬时保密速率 `R̂sl`，约束包括总发射功率 `tr(Wc,l) + tr(We,l) ≤ Pmax`、半正定、秩一，以及**感知精度约束**——E-UAV 状态估计的 MSE 不超过阈值 `Γ`。
- 波束子问题（式 35 → 37）：目标化为 `max τ − ε − δ + ϵ`，其中（式 36）：

> 原文：
> "R̂sl = [ log₂(1 + tr(H_bcl Wc,l)/(tr(H_bcl We,l) + σ²c)) − log₂(1 + tr(Ĥ_bel|l−1 Wc,l)/(tr(Ĥ_bel|l−1 We,l) + σ²e)) ]⁺"

- 感知精度约束的转换：引入辅助变量 `um ≥ 0` 上界化 `Cl` 的对角元，`[Cl]m,m ≤ um` 且 `Σ_{i=1}^{6} um ≤ Γ`；再用 Schur 补（式 42）化为 LMI 形式。
- 秩一约束的 DC 表示（式 43）：`ψi,l ≜ ‖Wi,l‖* − ‖Wi,l‖₂ = 0`，该式恒成立且**等号成立当且仅当 `Wi,l` 秩一**。

## Assumptions

假设：

- 信息信号与 AN **互不相关**：`(1/N) Σ_{n=1}^{N} sl(n) a*_l(n) ≈ 0`。
- 在一个 CPI 内，E-UAV 位置对大尺度衰落参数（信道增益）视为恒定，但**时变时延被保留**以利于多普勒估计。
- C-UAV 的 CSI `hbcl` 在 GBS 处已知（通过近场信道估计方法获得）。
- E-UAV 为**非协作节点**，其运动模型 GBS 未知。
- 单 C-UAV、单 E-UAV。

## Optimization Objective

目标：

- 最大化瞬时保密速率 `R̂sl`，同时满足：
  - 总发射功率约束
  - 感知精度约束（E-UAV 状态估计 MSE ≤ Γ）

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据：数值仿真（80 个 CPI）。

- GBS 为大孔径 UPA；C-UAV 与 E-UAV 各一架
- 基线中 C-UAV 静止方案（CSS）固定位置为 `(12.0, 3.0, 10.0)` 米
- 最大发射功率扫描范围约 22–30 dBm
- 最大 E-UAV 跟踪 MSE `Γ` 扫描范围约 0.02–0.1

## Baseline

比较方法：

- **PKS（Perfect knowledge scheme）**：假设 E-UAV 轨迹完全已知的上界方案（用 Algorithm 4 + 精确位置）
- **CSS（C-UAV static scheme）**：C-UAV 位置固定，仅用 Algorithm 2 设计波束
- **所提方案（Proposed）**：EKF 跟踪 + AO 联合波束与轨迹

## Metrics

评价指标：

- **瞬时保密速率**与**平均保密速率**（bps/Hz）
- E-UAV 跟踪 MSE（定位精度）
-  secrecy rate 随发射功率、随 `Γ` 的变化

## Results

主要结果：

- **图 10（平均保密速率 vs 最大发射功率）**：所提方案性能**几乎逼近 PKS**（理想上界），并明显优于 CSS。说明所提 E-UAV 轨迹跟踪方案有效，且用 Algorithm 4 设计 C-UAV 轨迹能提升安全性能。
- **图 11（平均保密速率 vs 最大跟踪 MSE Γ）**：所提方案与 PKS 的差距**可忽略**；与 CSS 的差距在 `Γ` 较小时**更为显著**——因为感知精度要求越严格，GBS 需给 AN 分配更多功率，而 CSS 中 GBS 与 C-UAV 距离大、分给信息信号的功率更少，保密速率退化更明显。
- **图 9（保密速率 vs CPI 索引，不同 Γ）**：揭示了**感知精度与保密通信性能的折衷**——`Γ` 越小（要求越严），AN 需分得更多功率以保感知精度，导致信息信号功率下降、保密速率降低；CPI > 50 后 E-UAV 远离 GBS 而 C-UAV 已基本静态，该退化更严重。
- 结论：为获得高保密速率，**感知精度阈值 `Γ` 应取恰当值**，而非越严越好。

> 原文：
> "the performance of the proposed scheme nearly approaches to that of the 'PKS', which confirms the effectiveness of the proposed E-UAV trajectory tracking scheme."
>
> 原文：
> "These observations highlight the trade-off between the E-UAV tracking accuracy and the secure communication performance."

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 提出近场 3D 感知辅助的安全 UAV 通信框架，**AN 同时用于干扰与感知**，提升时间与频谱效率。
2. 利用**近场多普勒的空间域变化性**（远场所无）从回波中直接估计 E-UAV 的 **3D 速度**，并用 EKF 融合校正轨迹。
3. 基于预测位置联合设计 GBS 波束成形与 C-UAV 轨迹，用 **AO + SCA + DC 罚函数**求解含秩一约束与感知精度约束的非凸问题。
4. 仿真验证：保密速率几乎逼近"轨迹完全已知"的上界，且优于 C-UAV 静止方案；并定量揭示了**感知精度—保密速率的折衷**。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 近场不只是"距离维度"，更提供了**空间变化的多普勒**，这是能被算法利用的额外观测自由度（Remark 1 是全文的物理支点）。
- AN 不必是纯浪费的功率——让它同时承担感知照明与干扰，是 ISAC 思路在安全场景的自然延伸。
- 感知精度不是一个"越严越好"的指标，而是需要与保密速率共同权衡的设计变量（`Γ` 的作用）。

## My Evaluation

我的评价：

五星

创新程度：

高

理由：

- 近场"空间变化多普勒 → 3D 速度"这一步把近场的物理特性真正转化成了算法能力，而不是停留在"近场信道模型更精确"的层面。
- AN 一物两用的设计干净且实用，直接解决了"感知要发功率、干扰也要发功率"的资源冲突。
- 图 9–11 给出了清晰可解释的折衷结论（`Γ` 应取恰当值），有工程指导意义。

- 局限：单 C-UAV、单 E-UAV，多窃听/多用户场景未涉及；E-UAV 的 RCS 假设已知（`β` 中含 `σRCS`）；全仿真。

---

# 10. Limitation（不足）

论文不足：

1. **单 C-UAV、单 E-UAV**：多用户、多窃听者场景下的波束与轨迹设计未讨论，可扩展性未知。
2. **E-UAV RCS 假设已知**：反射系数 `β` 中含雷达截面积 `σRCS`，实际中非协作无人机的 RCS 起伏未知。
3. **全仿真无实测**：近场大孔径阵列的校准误差、互耦、近场信道估计误差均未建模。
4. **AN 与信息信号不相关的假设**：`(1/N)Σ sl(n)a*_l(n) ≈ 0` 在有限块长下是近似，短包场景可能不成立。
5. **C-UAV CSI 假设已知**：近场信道估计本身的开销与误差未计入。
6. 感知精度阈值 `Γ` 由人工给定，论文指出应"取恰当值"但未给出自适应选取方法。

未来可能改进：

- 扩展到多 C-UAV / 多 E-UAV 场景，研究波束与多轨迹的联合设计。
- 研究 RCS 未知或起伏下的鲁棒跟踪与波束设计。
- 把近场信道估计误差与阵列校准误差纳入鲁棒优化。
- 设计 `Γ` 的自适应选取策略（按实时保密速率需求动态调整）。
- 在真实大孔径阵列平台上做近场实测验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- **近场的价值不止于"多一个距离维度"**：多普勒在天线间是变化的，这等于给速度估计增加了空间采样。远场下所有天线看到同一个多普勒，3D 速度不可解——这个对比很能说明近场的算法意义。
- **AN 的双用途设计**是 ISAC 在安全场景的漂亮落地：传统物理层安全把 AN 视为纯代价，这里把它变成"照明弹"，一举两得。
- **感知精度不是越高越好**：图 9/图 11 说明严格感知约束会挤占信息信号功率，反而降低保密速率。这与本 Vault 中 ISAC 的"C&S 权衡是结构性的"判断一致。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 UAV + ISAC 主线高度对口，特别是 [[02vault/UAV/ISAC Enabled Anti-UAV|ISAC 反无人机]] 同属对抗 UAV 场景。
- 近场 + 安全的组合可与 [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] 的近/远场混合场景对照：本文是纯近场，该文处理混合场。
- "AN 一物两用"的思路可迁移到自己的波形设计：让原本纯开销的信号承担感知功能。
- 与 [[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization|双目标 ISAC]] 批评的"加权和偏置"呼应：本文用感知精度约束（而非加权和目标）建模折衷，是更诚实的建模方式。

## Possible Ideas

可能的新想法：

- 研究 `Γ` 的自适应调度：按 E-UAV 距离、剩余功率动态放宽/收紧感知约束。
- 把本文的单 E-UAV 扩展到多 E-UAV，研究感知资源在多目标间的分配。
- 结合近场信道估计误差做鲁棒版本，分析误差对保密速率的定量影响。
- 把 AN 的双用途设计推广到远场（用其他感知观测量替代空间变化多普勒）。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/ISAC Enabled Anti-UAV|ISAC 反无人机]] — 同属对抗 UAV 场景，该文做波束与多 UAV 轨迹联合设计
- [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] — 同涉近场，该文处理近/远场混合的角度-时延-多普勒估计
- [[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization|双目标 ISAC]] — 批评加权和偏置，本文用感知约束建模折衷，可对照
- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同为 UAV-ISAC 轨迹设计，但用加权和且非安全场景

---

# 13. Summary Card（快速复习）

## Problem

> E-UAV 为非协作节点、位置与运动模型未知，传统依赖窃听者位置的 AN 设计失效；且远场缺乏空间变化多普勒，无法从回波解 3D 速度。

## Method

> AN 一物两用（干扰 + 感知照明）；利用近场多普勒的空间域变化性用 ML 估计 E-UAV 3D 速度，EKF 融合校正轨迹；再联合设计 GBS 波束与 C-UAV 轨迹，用 AO + SCA + DC 罚函数求解含秩一与感知精度约束的非凸保密速率最大化问题。

## Result

> 平均保密速率几乎逼近"E-UAV 轨迹完全已知"的 PKS 上界，明显优于 C-UAV 静止方案；并揭示感知精度阈值 Γ 与保密速率的折衷——Γ 过严会挤占信息信号功率，反而降低保密速率。

## Importance

> 把近场的物理特性（空间变化多普勒）转化为算法能力，并用 AN 双用途设计解决感知与干扰的资源冲突，是近场 ISAC + 物理层安全的代表性工作。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决非协作窃听无人机位置未知导致传统 AN 物理层安全设计失效的问题，并需兼顾感知精度与保密速率。

Q:
核心方法是什么？

A:
AN 同时用于干扰与感知；利用近场多普勒的空间变化性用 ML 估计 E-UAV 3D 速度，EKF 跟踪轨迹；再 AO + SCA + DC 罚函数联合设计 GBS 波束与 C-UAV 轨迹，最大化保密速率并保证感知 MSE ≤ Γ。

Q:
最大贡献是什么？

A:
保密速率几乎逼近"轨迹完全已知"的理想上界，证明近场 3D 感知可支撑安全通信；并定量揭示感知精度与保密速率的折衷。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `SFHWJXB7`，PDF 附件 `UGBKAK29`（已挂载至 `F:\XWCos\zotero\storage\UGBKAK29`）。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/SFHWJXB7]]，由 Zotero 附件 PDF 经 pypdf 提取。
- PDF 页码未验证（pypdf 提取不含可靠页码映射），故未标注页码。
- 仿真数值（图 9/10/11 趋势与结论）直接引自原文；具体数值点未在提取文本中完整给出，故以趋势与相对关系表述，未做推测。
- 式 34 的完整约束列表未在本次提取中全部定位，正文按已定位内容（功率、秩一、感知 MSE ≤ Γ）如实描述。
