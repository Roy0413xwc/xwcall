---
type: knowledge-synthesis
title: UAV-ISAC 联合设计的求解路径与性能边界：基于 22 篇笔记的跨论文综合
aliases:
  - UAV-ISAC 综合
status: developing
agreement: mixed
evidence_count: 22
source_notes:
  - "[[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]]"
  - "[[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|层次最优控制]]"
  - "[[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]]"
  - "[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO 协同 ISAC]]"
  - "[[02vault/UAV/ISAC-OTA UAV Swarm Dynamics|ISAC-OTA 机群控制]]"
  - "[[02vault/UAV/ISAC Enabled Anti-UAV|ISAC 反无人机]]"
  - "[[02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning|Mem-DSACM]]"
  - "[[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]]"
  - "[[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]]"
  - "[[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]]"
  - "[[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]]"
  - "[[Integrated Sensing and Communications for Low-Altitude Economy A Deep Reinforcement Learning Approach|DeepLSC 低空经济]]"
  - "[[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization|双目标 ISAC]]"
  - "[[02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV|AIBOT 资源分配]]"
  - "[[02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC|CKM 低空规划]]"
  - "[[02vault/ISAC/ISAC-Enabled Beam Tracking for U2U|U2U 波束跟踪]]"
  - "[[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]]"
  - "[[02vault/ISAC/NOMA Empowered ISAC with RIS|NOMA-ISAC RIS]]"
  - "[[02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks|SNN-DRL ISAC V2X]]"
  - "[[02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)|ISAC 综述]]"
  - "[[02vault/信道估计/HMIMO Graph-Based Wavenumber-Domain Channel Estimation|HMIMO 信道估计]]"
  - "[[02vault/信道估计/Under-Determined DOA Estimation|欠定 DOA]]"
related:
  - "[[UAV-ISAC 轨迹波束资源联合设计|UAV-ISAC 主题页]]"
  - "[[UAV 机动自由度与 ISAC 权衡边界|机动自由度关系页]]"
last_updated: 2026-10-13
evidence_status: note_only
---

# UAV-ISAC 联合设计的求解路径与性能边界

> [!summary] 综合判断
> **综合问题：** 在 UAV 平台上联合设计通信与感知时，问题的固有困难是什么？现有工作如何应对？这些应对方案的共同边界在哪里？
> **当前最稳健判断：** UAV-ISAC 的困难是**结构性的**（通信与感知不可兼得 + 联合问题 NP-hard），而非参数调优不足。现有工作分化为**优化分解**与**学习近似**两条路径，各有代价，尚无统一方案。
> **关键条件或机制：** 优化类依赖问题可分解/可凸近似的结构；学习类依赖环境可模拟且训练成本可接受。UAV 的机动性是两条路径共同依赖的额外自由度。
> **最大证据边界：** 22 篇来源**全部为仿真**，无实测验证；且各工作场景参数差异大，**缺少统一基准**，任何跨论文的定量比较都不成立。

## 1. 综合范围与纳入规则

- **主题范围：** 以 UAV 为平台或参与节点的 ISAC 系统的联合设计问题（轨迹、波束、资源分配）及其求解方法
- **来源范围：** 本 Vault 中 22 篇相关精读笔记（UAV 10、ISAC 10、信道估计 2）
- **纳入条件：** 明确涉及通信与感知的一体化设计，或为该方向提供基础技术（信道估计、DOA、综述）
- **排除条件：** 纯通信或纯感知系统；与本方向无关的深度学习理论、LLM 部署

## 2. 跨论文综合判断

### 相对稳定的发现

**发现一：通信与感知的权衡是结构性的，建模方式决定了结论的诚实程度。**

22 篇工作中，凡涉及权衡的，无一篇声称可同时最大化通信与感知。建模方式有三类，其「诚实度」递增：

| 建模方式 | 代表 | 问题 |
|---|---|---|
| 约束一侧、优化另一侧 | [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC\|UAV 6DMA]]、[[02vault/ISAC/ISAC-Enabled Beam Tracking for U2U\|U2U 跟踪]] | 需人为设定约束阈值 |
| 归一化加权和 | [[02vault/UAV/ISAC from the Sky UAV Trajectory Design\|ISAC from the Sky]] | 权重决定解在 Pareto 前沿的位置，缺乏依据（[[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization\|双目标 ISAC]] 明确批评此为「优化偏置」） |
| 双目标/多目标模型 | [[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization\|双目标 ISAC]] | 更诚实，但最终仍需标量化或求 Pareto 解 |

**发现二：求解路径分化为两支，代价互补。**

| 维度 | 优化分解类 | 学习近似类 |
|---|---|---|
| 代表 | [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications\|层次 MPC]]、[[02vault/ISAC/Optimal ISAC Beamforming Structure\|SCA 结构]] | [[Integrated Sensing and Communications for Low-Altitude Economy A Deep Reinforcement Learning Approach\|DeepLSC]]、[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC\|C-HAPPO]] |
| 优势 | 有收敛性分析、可得结构性洞察（如 Ns=3M） | 处理时变、高维、多智能体 |
| 代价 | 仅局部最优；实时性差 | 无最优性保证；训练成本高；sim-to-real 未解决 |

**发现三：感知指标的选择反映问题层次——CRB 用于静态估计，PCRB 用于动态跟踪。**

[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO]] 采用 PCRB 而非 CRB，因跟踪场景需利用目标运动模型与先验。这是一个明确的方法论区分，但本 Vault 中仅此一篇明确实践，多数工作仍用 CRB。
### 存在分歧或未决的问题

**未决一：优化类与学习类，谁更优？** 本 Vault 无跨论文定量对比。[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO]] 报告感知提升 >30%，[[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]] 报告与上界偏差仅 0.67%——但二者场景、指标完全不同，无法比较。

**未决二：加权和的「优化偏置」实际有多大？** [[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization|双目标 ISAC]] 批评加权和会造成性能损失与偏置，但本 Vault 无定量证据表明该损失的实际量级。

**未决三：实测会削减多少仿真增益？** 全部 22 篇为仿真。[[02vault/ISAC/ISAC-Enabled Beam Tracking for U2U|U2U 波束跟踪]] 指出抖动会破坏波束对齐——这类实际损伤在其他工作中被忽略，意味着仿真增益可能被系统性高估。

## 3. 关键机制与条件

### 机制一：可行域扩大 ⇒ 权衡边界弱改善

扩展 UAV 机动自由度（位置 → 位置+朝向 → 载 IRS）扩大可行域，理论上使 Pareto 前沿不劣化。详见 [[UAV 机动自由度与 ISAC 权衡边界|机动自由度关系页]]。

**条件：** 需算法能有效利用新增自由度；若求解器只得局部最优，理论改善未必兑现。

### 机制二：分解使 NP-hard 问题可解

层次分解（[[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|双层 MPC]]）、两阶段法（[[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|6DMA]]）、交替优化（[[02vault/ISAC/NOMA Empowered ISAC with RIS|NOMA-ISAC]]）把难解问题拆为可解子问题。

**条件：** 子问题间耦合需可控；分解带来的次优性需可接受。

### 机制三：结构洞察可降低维度

[[02vault/ISAC/Optimal ISAC Beamforming Structure|波束最优结构]] 证明 Ns=3M 已足够用尽感知自由度，据此把变量数降至 K²+9M²+6MK。这是「先找结构再优化」的范例。

**条件：** 结构结论依赖具体的信道与阵列模型假设。

## 4. 证据边界（本综合的最大限制）

| 边界 | 说明 |
|---|---|
| **零实测** | 22 篇全部为仿真。[[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area\|UWB 空地信道实测]] 是唯一含实测数据的工作，但它只做信道表征，未验证 ISAC 增益 |
| **无统一基准** | 场景参数（UAV 数、用户/目标数、频段、区域尺度）差异大，跨论文定量比较不成立 |
| **量化值未逐项核验** | 多数笔记中的具体数值（12%、16%、29%、>30%、2.58× 等）标注为「未逐项核验」，需回全文仿真章节确认 |
| **能量约束缺失** | 多数工作忽略 UAV 能耗/续航，可能高估机动性与算法收益 |

## 5. 对本研究的启示

### 可直接继承

- 权衡建模的诚实度阶梯：优先用双目标/多目标，而非任意加权和
- 「先找结构再优化」的降维范式（Ns=3M 范例）
- CRB/PCRB 的选取原则（静态估计 vs 动态跟踪）
- 分解 + 凸近似的工程路径

### 最值得投入的三个问题

1. **建立统一仿真基准**，在该基准上复现优化类与学习类方法——这是本 Vault 当前最有价值也最缺失的工作
2. **量化实测损伤**（抖动、互耦、信道估计误差）对 ISAC 增益的削减
3. **把能量/续航纳入核心约束**，研究其对最优工作点的影响

---

## 6. 来源与追踪

### Note supported

- 全部 22 篇来源笔记见 frontmatter。

### 关联的 Claim 记录

- `REL-UAVMOBILITY-ISACTRADEOFF-01`（机动自由度 → 权衡边界，note_supported）
- `REL-UAVMOBILITY-ENERGYGAP-02`（能量约束缺失，interpretation）
- `REL-LOCALOPT-NONCONVEX-03`（分解+凸近似为有效路径，note_supported）

### 待核验

- 升级为 fulltext_verified 需回各全文仿真章节逐项核验量化数值。