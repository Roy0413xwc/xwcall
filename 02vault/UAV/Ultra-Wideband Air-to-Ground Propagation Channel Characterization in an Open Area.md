---
title: "Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area"
aliases:
  - UWB 空地信道
  - AG propagation
tags:
  - literature-note
  - reading-note
  - UAV
  - channel-model
created: 2026-10-13
source: IEEE Transactions on Aerospace and Electronic Systems, Vol.56, pp.4533-4555
author: Wahab Khawaja, Ozgur Ozdemir, Fatih Erden, Ismail Guvenc, David W. Matolak
year: 2020
journal: IEEE Transactions on Aerospace and Electronic Systems

theme: 开阔区域无人机空地超宽带传播信道的实测表征与统计建模
study_area: 空地信道测量 / UWB / 信道建模
methodology: UWB 实测 + 射线追踪仿真 + Saleh-Valenzuela 统计拟合
core_variable: 路径损耗、RMS 时延扩展、莱斯 K 因子、仰角天线增益
key_finding: Saleh-Valenzuela 模型对功率时延谱拟合良好；接收功率高度依赖仰角面 LOS 天线增益
relevance: 为 UAV 通信链路预算与信道建模提供实测依据，是 UAV-ISAC 信道层的基础参考

type: literature-note
zotero_key: "UCRR3CP7"
pdf_key: "3QMWGJNJ"
doi: "10.1109/TAES.2020.3003104"
collection: "UAV"
note_path: "02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area.md"
fulltext_path: "03fulltext/UAV/UCRR3CP7.md"
status:
  - Reading
rating: 五星
---
# Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area

---

# 📌 Basic Information（基本信息）

## Author
Wahab Khawaja, Ozgur Ozdemir, Fatih Erden, Ismail Guvenc, David W. Matolak

## Year
2020（Vol. 56, pp. 4533-4555）

## Source
IEEE Transactions on Aerospace and Electronic Systems｜DOI: 10.1109/TAES.2020.3003104

> Zotero 入口：zotero://select/library/items/UCRR3CP7
> PDF 入口：zotero://open-pdf/library/items/3QMWGJNJ
> 全文 Markdown：[[03fulltext/UAV/UCRR3CP7]]

## Research Area

- Air-to-Ground (AG) Propagation
- Ultra-Wideband (UWB) Channel
- Channel Measurement and Modeling
- UAV Communications

---

# 1. Abstract Summary（一句话总结）

> 该文通过 3.1–4.8 GHz 的无人机空地超宽带实测，给出 LOS 与遮挡场景下的多径信道统计，发现 Saleh-Valenzuela 模型对功率时延谱拟合良好，并提出了基于仰角面天线增益的解析路径损耗模型。

---

# 2. Research Background（研究背景）

## 背景：

- 民用无人机在视频录制、监视、搜救与热点通信等应用中快速增长。
- 与其他空中平台相比，无人机可在更低高度、更灵活位置部署，但其信道特性与地面蜂窝、卫星信道显著不同。
- UWB 的大带宽使其具备精细时延分辨能力，适合刻画空地信道的多径结构。

> 原文：
> "The use of civilian unmanned-aerial-vehicles (UAVs) for applications such as video recording, surveillance, search and rescue, and hot spot communications has seen a surge in recent years."

## Motivation（研究动机）

- 现有文献对 UAV 空地 UWB 信道的实测表征仍不充分，尤其缺少不同天线朝向、不同高度、不同遮挡条件下的系统测量。
- 需要能为链路预算与系统设计提供可直接使用的解析路径损耗模型与统计信道模型。

## Application Scenario（应用场景）

- UAV 空地通信链路预算与覆盖规划
- UAV 辅助应急通信的物理层设计
- UAV 通信/感知一体化（ISAC）系统的信道建模基础
---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何在开阔区域对无人机空地 UWB 信道进行系统实测，并给出可用于系统设计的统计信道模型与解析路径损耗模型？

核心问题：

- 不同传播场景（悬停无遮挡、植被遮挡、定高圆周运动）下的多径统计有何差异？
- Saleh-Valenzuela 模型是否适用于 UAV 空地 UWB 信道？
- 天线朝向与仰角如何影响接收功率与路径损耗？

---

# 4. Related Work（相关工作）

已有方法：

1. **空地信道实测建模**：已有工作在开阔区与郊区用实测数据建立统计信道模型。
2. **仰角效应研究**：已有工作讨论了不同 UAV 高度与天线朝向下仰角对接收功率的影响，并把全向偶极子天线在仰角面的增益建模为仰角的三角函数。
3. **射线追踪仿真**：本文也对无遮挡悬停场景做了射线追踪仿真，与实测对照。

现有不足：

- 缺少同时覆盖多种遮挡条件、多种天线朝向、多种高度与水平距离的 UWB 实测数据集。
- 缺少把天线增益显式纳入解析形式的路径损耗模型。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 在开阔场地用小型无人机做 UWB 空地传播实测（3.1–4.8 GHz），覆盖三种传播场景与两种天线朝向。
- 由实测数据提取多径信道统计，并对功率时延谱（PDP）做 Saleh-Valenzuela 与单指数模型的拟合比较。
- 提出基于仰角面天线增益的解析路径损耗模型。

> 原文：
> "In addition, analysis of best fits for the power delay profiles (PDPs) based on the Saleh-Valenzuela and single exponential models are provided. We also provide additional channel statistics: the root mean square delay spread (RMS-DS) and Ricean K-factor."

## Model / Framework

测量配置：

- **频段**：3.1–4.8 GHz（UWB）
- **传播场景**：无遮挡悬停、植被遮挡（foliage obstruction）、定高圆周运动
- **几何参数**：3 个 UAV 高度 × 2 个水平距离
- **天线朝向**：UAV 发射端 2 种朝向
- **补充仿真**：对无遮挡悬停场景做射线追踪（ray tracing）仿真

> 原文：
> "Measurements were obtained at three UAV heights and two horizontal distances for two different antenna orientations at the UAV TX."

## Algorithm / Technique

采用：

- UWB 信道实测（频域/时域信道探测）
- Saleh-Valenzuela（SV）统计信道模型拟合
- 单指数（single exponential）PDP 模型对照
- 射线追踪仿真
- RMS 时延扩展（RMS-DS）与莱斯 K 因子估计

## Key Steps

1. 在开阔场地部署 UAV 发射端与地面站（GS）接收端，设定测量频段 3.1–4.8 GHz。
2. 按三种传播场景、三种高度、两种水平距离、两种天线朝向组合采集信道响应。
3. 从实测数据提取 PDP，分别用 SV 模型与单指数模型拟合并比较拟合优度。
4. 计算 RMS-DS 与 Ricean K-factor 等附加统计量。
5. 基于仰角面天线增益，建立无遮挡悬停与圆周运动场景的解析路径损耗模型。
---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

- **统计信道模型**：采用 Saleh-Valenzuela（SV）模型描述功率时延谱（PDP）的簇到达与簇内多径到达结构。
- **对照模型**：单指数（single exponential）衰减 PDP 模型。
- **附加统计量**：RMS 时延扩展（RMS-DS）、莱斯 K 因子（Ricean K-factor）。
- **解析路径损耗模型**：基于天线在仰角面（elevation plane）的增益，针对无遮挡悬停与定高圆周运动场景建立。

> 说明：论文给出了上述模型与统计量的定义与拟合结果，具体闭式表达式以 [[03fulltext/UAV/UCRR3CP7]] 原文为准；此处不重述未在当前材料中明确核验的系数数值。PDF 页码未验证。

## Assumptions

假设：

- 开阔场地（open field）环境，散射体相对稀疏，可用 SV 簇结构刻画多径。
- 天线在仰角面的增益可建模为 UAV 与地面站之间仰角的函数。
- 测量期间信道在采集窗口内近似准静态。

## Optimization Objective

目标：

- 给出能最好拟合实测 PDP 的统计模型（SV vs 单指数）。
- 给出可用于链路预算的解析路径损耗表达式，显式计入天线增益与几何关系。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据与环境：

- 开阔场地（open field）实测，使用小型 UAV。
- 频段 3.1–4.8 GHz，三种传播场景、三种 UAV 高度、两种水平距离、两种天线朝向。

> 原文：
> "we have reported UWB AG propagation channel measurements in an open field using a small UAV in three propagation scenarios: unobstructed UAV hovering, foliage obstruction, and unobstructed UAV moving in a constant-altitude circle."

## Baseline

比较方法：

- 统计模型对照：Saleh-Valenzuela vs 单指数 PDP 模型。
- 仿真对照：无遮挡悬停场景的射线追踪仿真 vs 实测。

## Metrics

评价指标：

- 路径损耗（path loss）
- RMS 时延扩展（RMS-DS）
- 莱斯 K 因子（Ricean K-factor）
- PDP 拟合优度

## Results

主要结果：

- Saleh-Valenzuela 模型对统计信道模型提供了良好拟合。
- 当天线朝向一致（aligned）时，接收功率高度依赖仰角面 LOS 分量的天线增益。
- 实测路径损耗低于射线追踪预测，作者归因于：① 射线追踪未建模但实际存在的额外散射体带来更多多径分量（MPC）；② 真实天线的非理想交叉极化鉴别度使 VH 朝向下路径损耗降低。

> 原文：
> "the Saleh-Valenzuela (SV) model was found to provide a good fit for the statistical channel model."
>
> 原文：
> "We observed that the received power is highly dependent on the antenna gain of the LOS component in the elevation plane when the antennas are aligned (same orientation)."
>
> 原文：
> "the additional scatterers not modeled in ray tracing but present in the actual measurements contribute to additional MPCs. This results in a reduction of path loss. Another reason is the non-ideal cross-polarization discrimination for real-world antennas that results in the reduction of the path loss for VH antenna orientation."
---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 报告了开阔场地 UWB 空地传播信道实测，覆盖无遮挡悬停、植被遮挡、定高圆周运动三类场景。
2. 给出基于仰角面天线增益的解析路径损耗模型，适用于无遮挡悬停与圆周运动场景。
3. 提供 PDP 的 SV 与单指数模型最佳拟合分析，并给出 RMS-DS 与 Ricean K-factor 等统计量的实测值。
4. 用射线追踪仿真与实测对照，解释了实测路径损耗偏低的两个原因。

> 原文：
> "An analytical path loss model based on antenna gains in the elevation plane is provided for unobstructed UAV hovering and moving (in a circular path) propagation scenarios."

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- 首次系统给出同时覆盖三类场景、多种高度/距离/天线朝向的 UWB 空地实测结果。
- 把天线在仰角面的增益显式纳入解析路径损耗模型，比传统仅依赖距离的路径损耗指数模型更贴合 UAV 几何。

## My Evaluation

我的评价：

五星

创新程度：

中高

理由：

- 属于扎实的测量与建模工作，工程参考价值高（可直接用于链路预算）。
- 创新在于测量设计的完备性与天线增益的显式建模，而非提出全新理论。
- 对后续 UAV-ISAC 信道建模是可靠的一手实测依据。

---

# 10. Limitation（不足）

论文不足：

1. 场景限于开阔场地，未覆盖城市、郊区等更复杂散射环境。
2. 频段限于 3.1–4.8 GHz，未涉及更高频段（如毫米波）。
3. 圆周运动场景为定高匀速，未覆盖更激进的机动轨迹。
4. 实测与射线追踪的偏差说明模型对真实散射体的刻画仍不完整。

未来可能改进：

- 扩展到城市/郊区多场景与更高频段测量。
- 引入更丰富的机动轨迹与动态信道追踪。
- 把实测统计模型接入系统级仿真与 ISAC 波形设计。
---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- UAV 空地信道的路径损耗不能只用距离指数刻画，天线在仰角面的增益往往主导 LOS 分量强度。
- SV 模型（簇 + 簇内多径）对 UWB 空地 PDP 的拟合优于简单单指数模型。
- 实测与射线追踪的系统性偏差（实测损耗更低）提示：仿真中遗漏的散射体与非理想天线极化特性会显著影响链路预算精度。

## Connection With My Work

和我的研究/项目关系：

- 为 UAV 通信链路预算提供了带天线增益的解析路径损耗表达，可直接用于自己的覆盖分析。
- RMS-DS 与 K 因子实测值可用于校验自己信道仿真的合理性。
- 该文的测量设计（多高度 × 多距离 × 多天线朝向）可作为自己搭建 UAV-ISAC 信道测量方案的模板。

## Possible Ideas

可能的新想法：

- 把该文解析路径损耗模型扩展到 ISAC 场景，联合考虑感知回波与通信链路的路径损耗差异。
- 研究 vegetation obstruction 场景下的遮挡统计，用于 UAV 应急通信的可用性建模。
- 用该实测数据校验射线追踪仿真参数，提升仿真可信度。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|无人机应急通信层次最优控制]] — 同属 UAV 通信方向，前者侧重信道实测，本文侧重轨迹规划

---

# 13. Summary Card（快速复习）

## Problem

> UAV 空地 UWB 信道缺少覆盖多种场景、高度、距离与天线朝向的系统实测与可工程化模型。

## Method

> 开阔场地 3.1–4.8 GHz 实测（三场景 × 三高度 × 两距离 × 两朝向），PDP 用 SV 与单指数模型拟合，并做射线追踪对照。

## Result

> SV 模型拟合良好；天线朝向一致时接收功率高度依赖仰角面 LOS 天线增益；实测路径损耗低于射线追踪预测。

## Importance

> 提供了可直接用于 UAV 链路预算的解析路径损耗模型与一手实测信道统计量。

## Flash Card

Q:
这篇论文解决什么问题？

A:
补齐 UAV 空地 UWB 信道在多场景、多高度、多天线朝向下系统实测与建模的空白。

Q:
核心方法是什么？

A:
3.1–4.8 GHz 开阔场地实测，SV 与单指数 PDP 拟合，加射线追踪仿真对照，提出基于仰角面天线增益的解析路径损耗模型。

Q:
最大贡献是什么？

A:
给出可直接工程化使用的 UAV 空地 UWB 解析路径损耗模型与完整实测信道统计量（RMS-DS、K 因子）。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `UCRR3CP7`（本地 API 读取），PDF 附件 `3QMWGJNJ`。
- 原文引用均取自全文 Markdown [[03fulltext/UAV/UCRR3CP7]]，来源为 Zotero 全文缓存 `F:\XWCos\zotero\storage\3QMWGJNJ\.zotero-ft-cache`。
- PDF 页码未验证：全文缓存不含 page mapping，故未标注具体页码。
- 论文具体拟合系数与公式闭式表达未在笔记中重述，以全文原文为准，避免转述失真。