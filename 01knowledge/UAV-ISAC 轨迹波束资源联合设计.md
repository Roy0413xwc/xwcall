
---
type: "knowledge-theme"
title: "无人机通感一体化（UAV-ISAC）的轨迹、波束与资源联合设计"
aliases:
  - UAV-ISAC
  - 无人机通感一体化
status: "developing"
evidence_count: 22
source_notes:
  - "[[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]]"
  - "[[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|无人机应急通信层次最优控制]]"
  - "[[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]]"
  - "[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO 协同 ISAC]]"
  - "[[02vault/UAV/ISAC-OTA UAV Swarm Dynamics|ISAC-OTA 机群控制]]"
  - "[[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]]"
  - "[[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]]"
  - "[[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 空地信道实测]]"
  - "[[02vault/ISAC/Optimal ISAC Beamforming Structure|ISAC 波束成形最优结构]]"
  - "[[02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks|SNN-DRL ISAC V2X]]"
  - "[[02vault/ISAC/ISAC for Low-Altitude Economy DRL|DeepLSC 低空经济]]"
  - "[[02vault/ISAC/NOMA Empowered ISAC with RIS|NOMA-ISAC RIS]]"
  - "[[02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV|AIBOT 资源分配]]"
  - "[[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]]"
  - "[[02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC|CKM 低空规划]]"
  - "[[02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)|ISAC 综述]]"
- "[[02vault/UAV/ISAC Enabled Anti-UAV|ISAC 反无人机]]"
  - "[[02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning|Mem-DSACM]]"
  - "[[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization|双目标 ISAC]]"
  - "[[02vault/ISAC/ISAC-Enabled Beam Tracking for U2U|U2U 波束跟踪]]"
  - "[[02vault/信道估计/HMIMO Graph-Based Wavenumber-Domain Channel Estimation|HMIMO 信道估计]]"
  - "[[02vault/信道估计/Under-Determined DOA Estimation|欠定 DOA]]"
related: []
last_updated: "2026-10-13"
evidence_status: "mixed"
---
为什么是红的，是不是要修复一下
# 无人机通感一体化（UAV-ISAC）的轨迹、波束与资源联合设计

> [!summary] 30 秒综合判断
> **研究对象：** 以无人机为空中平台的通感一体化（ISAC）系统，联合设计轨迹、波束成形与通信/感知资源分配。
> **核心问题：** 通信性能（速率/可靠性）与感知性能（CRB/PCRB/SNR）在同一平台上相互竞争，且联合优化问题多为非凸甚至 NP-hard，难以实时求解。
> **当前最稳健结论：** 层次/交替分解 + 凸近似（SCA）是处理该类非凸问题的通用工程路径；把 UAV 的机动性（位置、朝向）作为新增自由度，可显著扩展系统可控空间。
> **最重要的条件边界：** 现有结论绝大多数来自仿真；能量/续航约束、实测信道、硬件非理想性在多数工作中被简化或忽略。
> **当前最大证据缺口：** 缺少实测验证与跨论文统一基准（不同工作的场景、信道模型、指标差异大，难以横向定量比较）。
> [!important] 准入检查
> 本页对应明确研究问题：UAV 平台下通信与感知性能的权衡机制，以及联合设计问题（轨迹/波束/资源）的求解路径与性能边界。非关键词集合。

## 1. 主题范围

### 纳入范围

- 以无人机（UAV）为空中平台或参与节点的 ISAC 系统
- 联合设计问题：轨迹优化、波束成形、资源（功率/带宽/关联）分配
- 感知性能度量：CRB、PCRB、雷达波束方向图增益、定位精度
- 通信性能度量：和速率、最小速率、SNR/SINR、中断概率
- 求解方法：优化分解（SCA/交替优化/MPC）、学习方法（DRL/MARL）、结构化方法（张量/最优传输）

### 不纳入范围

- 纯地面 ISAC（不含 UAV 参与）
- 纯通信系统或纯雷达系统（无一体化设计）
- 与本方向无关联的深度学习理论、LLM 部署等（归入其他主题）

### 核心分析层级

- **空间尺度：** 低空（数十至数百米高度）、城市/开阔场地为主
- **时间尺度：** 秒级至分钟级的飞行任务时域；决策为序贯/滚动时域
- **结果变量：** 感知精度（CRB/PCRB）、通信速率、任务完成时间、能耗
- **主要解释变量：** UAV 轨迹与朝向、波束成形、功率/带宽分配、天线/IRS 配置

> [!warning] 边界提示
> 本页综合结论仅适用于上述范围。不同频段、不同空域环境（城市峡谷 vs 开阔场）、不同 UAV 平台能力下的结果不得自动外推。
---

## 2. 当前综合判断

本 Vault 现有 16 篇相关精读笔记，覆盖了 UAV-ISAC 的主要问题分支。综合来看：

**第一，通信与感知的权衡是结构性的，而非参数可调的表面冲突。** ISAC 综述（[[02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)|ISAC 综述]]）指出该权衡存在于三个层次：信息论极限、物理层性能、跨层设计。具体到 UAV 场景，多数工作（如 [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]]、[[02vault/ISAC/Optimal ISAC Beamforming Structure|Optimal ISAC Beamforming Structure]]）都采用「归一化加权和」或「约束一侧、优化另一侧」的建模方式，这本身印证了二者不可兼得的本质。

**第二，UAV 的机动性是被普遍利用的新增自由度，但其刻画深度不一。** 从早期的 3D 轨迹优化（[[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]]），到把朝向也纳入优化的六维可动天线（[[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|UAV 6DMA ISAC]]），UAV 的可控维度在扩展。值得注意的是，多数工作只优化位置，把「朝向/姿态」作为优化变量的工作仍属少数。

**第三，求解路径已从纯优化扩展到学习，但各有代价。** 优化类方法（SCA、交替优化、MPC）能保证局部最优且有收敛性分析，但难以实时（如 [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|无人机应急通信层次最优控制]] 需层次分解）；学习类方法（[[02vault/ISAC/ISAC for Low-Altitude Economy DRL|DeepLSC]]、[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO]]）可应对时变与高维，但缺少最优性保证且训练成本高。二者尚未出现压倒性的统一方案。

**第四，感知指标的选取反映问题层次：CRB 用于静态估计，PCRB 用于动态跟踪。** [[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO]] 明确采用 PCRB 而非 CRB，因为跟踪场景需利用目标运动模型与先验。这是一个值得注意的方法论区分。

---

## 3. 核心证据地图

| 子议题 | 当前结论 | 证据角色 | 主要尺度 / 情境 | 核验状态 | 代表来源 |
|---|---|---|---|---|---|
| 轨迹—波束联合优化的可行性 | 可行且有效，但多为局部最优 | direct | 低空、单/多 UAV | note_supported | [[02vault/UAV/ISAC from the Sky UAV Trajectory Design\|ISAC from the Sky]] |
| 波束成形的最优结构 | 存在可降维的结构性结论（Ns=3M 足够） | mechanism | 多用户多目标、单站 | note_supported | [[02vault/ISAC/Optimal ISAC Beamforming Structure\|波束最优结构]] |
| UAV 机动性作为自由度 | 位置已普遍利用；朝向/6D 仍属前沿 | direct | UAV 载 IRS/天线 | note_supported | [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC\|6DMA]] |
| 学习类方法的适用性 | 可处理时变与高维，代价是无最优性保证 | direct | 低空经济、多智能体 | note_supported | [[02vault/ISAC/ISAC for Low-Altitude Economy DRL\|DeepLSC]]、[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC\|C-HAPPO]] |
| 频谱受限下的机群控制 | OTA 空中计算可绕开逐机带宽分配 | mechanism | 大规模 UAV 群 | note_supported | [[02vault/UAV/ISAC-OTA UAV Swarm Dynamics\|ISAC-OTA]] |
| 信道先验用于网络规划 | CKM 可把在线优化转为离线规划 | contextual | 低空走廊 | note_supported | [[02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC\|CKM 规划]] |
| 实测信道依据 | 空地 UWB 信道有实测数据与解析路径损耗模型 | contextual | 开阔场地、3.1–4.8 GHz | note_supported | [[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area\|UWB 实测]] |
---

## 4. 已较稳定的认识

### 4.1 通信与感知不可同时最优，必须显式建模权衡

**判断：** UAV-ISAC 中通信与感知性能存在结构性竞争，需通过加权和、约束法或 Pareto 刻画显式处理；不存在同时最大化二者的通用方案。

**证据基础：**

- [[02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)|ISAC 综述]] — 系统分析了信息论、物理层、跨层三个层次的 S&C 权衡
- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 用归一化加权和统一度量通信数据量与感知 CRB
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|波束最优结构]] — 在 sum rate 与 CRLB 之间做平衡设计

**适用边界：**

- 上述结论针对共享频谱与硬件的一体化系统；若通信与感知使用分离资源，则权衡减弱甚至消失。

### 4.2 非凸/NP-hard 问题的实用解法是分解与凸近似

**判断：** 面对联合优化的 NP-hard 特性，层次分解、交替优化与 SCA 是被反复验证有效的工程路径。

**证据基础：**

- [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|层次最优控制]] — 双层 MPC：战略层 MILP + 轨迹层 NMPC/SCP
- [[02vault/ISAC/Optimal ISAC Beamforming Structure|波束最优结构]] — SCA 序列凸近似保证收敛到局部最优
- [[02vault/ISAC/NOMA Empowered ISAC with RIS|NOMA-ISAC RIS]] — 交替优化 + SCA + SRCR
- [[02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC|6DMA]] — 两阶段法：先优化 6D 参数，再闭式求波束成形

**适用边界：**

- 这些方法只保证局部最优；问题规模增大时收敛速度与解的质量需重新评估。

### 4.3 学习类方法用于时变与高维，但牺牲最优性保证

**判断：** 当时变性、不确定性或多智能体维度使传统优化难以奏效时，DRL/MARL 是可行替代，代价是无最优性保证与较高的训练成本。

**证据基础：**

- [[02vault/ISAC/ISAC for Low-Altitude Economy DRL|DeepLSC]] — 把带飞行任务的问题建模为 episode task MDP
- [[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO]] — 异构多智能体 + 课程学习 + 降维
- [[02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks|SNN-DRL]] — 用 SNN 降低 DRL 能耗

**适用边界：**

- 性能高度依赖训练环境与奖励设计；sim-to-real 差距未在这些工作中被充分处理。
---

## 5. 条件性与异质性

### 空间尺度

- 低空（LAE/LAWN）场景与常规蜂窝的场景假设不同：空地链路以 LOS 为主，仰角对天线增益影响显著（[[02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area|UWB 实测]]）。
- 大规模天线下近场（NF）与远场（FF）目标可能共存，使参数估计问题复杂化（[[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]]）。

### 场景类型

- **应急通信**强调时限与覆盖公平性（max-min rate），见 [[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|层次最优控制]]、[[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]]。
- **低空经济**强调服务与监管并存（服务授权 UAV、监视非授权目标），见 [[02vault/ISAC/ISAC for Low-Altitude Economy DRL|DeepLSC]]。
- **时延敏感控制**强调 FBL 可靠性与控制闭环耦合，见 [[02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks|低空预测控制]]。

### 指标定义

- **CRB vs PCRB**：静态参数估计用 CRB；动态跟踪应选用 PCRB（[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO]]）。这是本 Vault 中明确体现的方法论区分。
- **波束方向图增益**：部分工作用「最小波束方向图增益」体现感知鲁棒性（[[02vault/ISAC/NOMA Empowered ISAC with RIS|NOMA-ISAC RIS]]），而非峰值。

### 模型与识别策略

- 优化类与学习类是两条并行路线，目前没有跨论文的定量对比基准。
- 部分工作给出与上界解的偏差（如 [[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]] 的 ε≈0.67%），这是较少见且可贵的严谨做法。

### 非线性 / 阈值

- 雷达流数存在饱和点：[[02vault/ISAC/Optimal ISAC Beamforming Structure|波束最优结构]] 证明 Ns=3M 已足够用尽感知自由度，超出无收益。
- 通信—感知权衡系数需人工设定，多数工作未给出自适应调参策略。

> [!important] 不应被压平的差异
> 1. **CRB 与 PCRB 不可混用**——前者对应静态估计，后者对应动态跟踪，选错会导致性能评估偏差。
> 2. **单 UAV 与多 UAV 协同的问题结构不同**——多智能体引入异构性与维度灾难，不能把单 UAV 结论直接外推。
> 3. **仿真结论不等于实测表现**——本主题几乎所有结论来自仿真，实测信道、硬件非理想性与能量约束会显著改变结果。
---

## 6. 涉及概念与方法

### 核心概念

- 暂无独立概念页（当前 Vault 未建立 knowledge-concept 页面）

### 关键方法

- SCA（序列凸近似）：[[02vault/ISAC/Optimal ISAC Beamforming Structure|波束最优结构]]、[[02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory|UAV 5G 移动感知]]
- 层次/双层 MPC：[[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|层次最优控制]]
- DRL / 异构 MARL：[[02vault/ISAC/ISAC for Low-Altitude Economy DRL|DeepLSC]]、[[02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC|C-HAPPO]]
- 张量 CP 分解：[[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]]
- 最优传输理论：[[02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV|AIBOT]]
- OTA 空中计算：[[02vault/UAV/ISAC-OTA UAV Swarm Dynamics|ISAC-OTA]]
- 信道知识地图（CKM）：[[02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC|CKM 规划]]

### 关键关系

- 暂无独立关系页（可后续基于本页结论建立）

### 相关争议

- 优化类 vs 学习类方法的优劣：本 Vault 尚无跨论文定量对比证据，属于未决问题。

---

## 7. 当前研究空白

按「缺什么证据」而非「很少有人研究」来写。

### Gap A — 实测验证缺口

- **缺失：** 本 Vault 全部 16 篇相关工作的结论均来自仿真，无一包含实测或硬件在环验证。
- **为什么重要：** UAV 空地信道、硬件非理想性（相移量化、姿态抖动）会显著影响实际性能，仿真增益未必可复现。
- **需要什么研究设计：** 在真实 UAV 平台上做小规模实测，与仿真结果对照，标定仿真模型的偏差。

### Gap B — 跨论文定量基准缺口

- **缺失：** 各工作的场景、信道模型、UAV 数量、性能指标差异大，无法横向定量比较（例如无法判断 DeepLSC 与 ISAC from the Sky 谁更优）。
- **现有证据局限：** 每篇只在自己的设定下与自己的基线对比。
- **需要补充：** 建立一个统一的仿真基准（场景参数、信道模型、指标定义），在该基准上复现主要算法。

### Gap C — 能量与续航约束缺口

- **缺失：** 多数工作把能量作为简化约束或完全忽略，少有把 UAV 续航作为核心优化目标。
- **当前只能说明：** 在给定能量约束下的轨迹/资源分配可行。
- **尚不能说明：** 能量约束如何改变通信—感知权衡的最优工作点。

---

## 8. 对本研究的启示

### 可直接继承

- 归一化加权和的通信—感知权衡建模（多个工作验证有效）
- 层次分解 + SCA 的求解范式
- CRB/PCRB 的指标选取原则（静态 vs 动态）
- 低空场景的信道实测数据与解析路径损耗模型（用于仿真标定）

### 需要重新验证

- 各工作报告的增益（12%、16%、29% 等）在统一基准下是否仍成立
- 学习类方法在不同奖励设计与环境扰动下的稳定性
- 近场/远场混合在实际低空场景中的发生条件与占比

### 可形成研究问题

- RQ1：在统一基准下，优化类与学习类 UAV-ISAC 方法的性能—实时性权衡如何？
- RQ2：把 UAV 续航作为核心约束时，通信—感知的最优工作点如何移动？
- RQ3：实测信道与硬件非理想性会削减多少仿真所报告的 ISAC 增益？

---

## 9. 来源与追踪

### Note supported（本页结论主要来自笔记层）

- 全部 16 篇来源笔记见 frontmatter 的 source_notes。

### 待核验

- 各工作的具体量化数值（12%、16%、29%、0.67% 等）在生成笔记时多标注为「未在当前材料中逐项定位」，需回到全文仿真章节逐项核验后才能升级为 fulltext_verified。