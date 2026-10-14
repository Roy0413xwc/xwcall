---
type: "thesis-prep"
title: "ISAC 知识图谱（一级 + 二级分类）"
aliases: ["ISAC 知识图谱", "ISAC 分类地图"]
created: "2026-10-14"
last_updated: "2026-10-14"
evidence_status: "note_only"
---

# ISAC 知识图谱

> [!summary] 构建口径
> **一级分类**按你指定的 10 个方向。**二级分类**每个方向下给出三项：① 已阅读论文（指向真实 `02vault` 精读笔记）；② 缺失方向（基于 52 篇笔记的覆盖诊断）；③ 推荐补充论文（**均已通过 Crossref 逐条核验 DOI、标题、年份与期刊**，可直接用 Zotero「按标识符添加」入库）。
> 已读论文的「已读」判定依据：`02vault/` 中存在对应 Analytical Note（精读笔记），而非仅 Zotero 条目。

## 覆盖热力图

| 一级分类 | 已读篇数 | 覆盖强度 | 缺口严重度 |
|---|---|---|---|
| 1. ISAC 基础理论 | 7 | 中 | 中 |
| 2. 波形设计 | 4 | 弱 | **高** |
| 3. 波束成形 | 8 | 中 | 中 |
| 4. MIMO ISAC | 8 | 中 | 中 |
| 5. RIS 辅助 ISAC | 3 | 弱 | **高** |
| 6. UAV / 车联网 ISAC | 26 | 强 | 低 |
| 7. 高移动场景 ISAC | 5 | 中 | 中 |
| 8. AI 辅助 ISAC | 14 | 强 | 低 |
| 9. 资源分配 | 11 | 强 | 低 |
| 10. 目标检测与跟踪 | 9 | 中 | 中 |

> 注：单篇论文可同时归属多个方向（如 `4IPDFAZ4` 同时属于基础理论、波束成形、MIMO ISAC），故合计大于 52 篇。

## 1. ISAC 基础理论

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2022 | Integrated Sensing and Communications: Toward Dual-Functional Wireless Networks for … | IEEE Journal on Selected Areas in Communicat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)\|笔记]] |
| 2026 | Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Ba… | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Optimal ISAC Beamforming Structure\|笔记]] |
| 2022 | Environment Sensing Considering the Occlusion Effect: A Multi-View Approach | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Environment Sensing with Occlusion Effect\|笔记]] |
| 2024 | Under-Determined DOA Estimation: A Method Based on Higher-Order Statistics and Non-U… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Under-Determined DOA Estimation\|笔记]] |
| 2025 | OptiPMB: Enhancing 3D Multi-Object Tracking With Optimized Poisson Multi-Bernoulli F… | IEEE Transactions on Intelligent Transportat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/OptiPMB 3D Multi-Object Tracking\|笔记]] |
| 2025 | Normalizing Flow-Based Differentiable Particle Filters | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Normalizing Flow-Based Differentiable Particle Filters\|笔记]] |
| 2025 | Overparameterized ReLU Neural Networks Learn the Simplest Model: Neural Isometry and… | IEEE Transactions on Information Theory | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Overparameterized ReLU Neural Networks\|笔记]] |

### 二级分类 B：缺失方向

**结构性缺口（最严重）**：现有笔记中**没有任何一篇**讨论 ISAC 的信息论极限、容量—失真/率—CRB 的可达界或自由度分析。你读的 ISAC 理论类文献几乎全部是「优化求解」型，缺少「性能上界」型。开题报告中「研究意义与理论依据」一节会因此缺乏支撑。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2025 | Rethinking the Fundamental Performance Limits of Integrated Sensing and Communication | IEEE TWC | `10.1109/twc.2025.3572678` |
| 2025 | Fundamental Limits of Multiple-Access Integrated Sensing and Communication Systems | IEEE TIT | `10.1109/tit.2025.3553111` |
| 2025 | Information-Theoretic Limits of Bistatic Integrated Sensing and Communication | IEEE TIT | `10.1109/tit.2025.3621465` |
| 2023 | On the Fundamental Tradeoff of Integrated Sensing and Communications Under Gaussian Channels | IEEE TIT | `10.1109/tit.2023.3284449` |
| 2024 | Fundamental CRB-Rate Tradeoff in Multi-Antenna ISAC Systems With Information Multicasting | IEEE TWC | `10.1109/twc.2023.3312723` |
| 2024 | MIMO Integrated Sensing and Communication: CRB-Rate Tradeoff | IEEE TWC | `10.1109/twc.2023.3303326` |
| 2025 | Fundamental CRB-Rate Trade-Off in ISAC Systems Under Correlated Communication-Sensing | IEEE TCOM | `10.1109/tcomm.2025.3588613` |
| 2026 | From Cramér-Rao To Barankin: Fundamental Trade-Off in OFDM ISAC | IEEE JSAC | `10.1109/jsac.2025.3612931` |
| 2023 | Fundamental Detection Probability vs. Achievable Rate Tradeoff in ISAC | IEEE TWC | `10.1109/twc.2023.3273850` |
| 2014 | Cooperative Radar and Communications Signaling: The Estimation and Information Theory Odd Couple | IEEE Radar Conf | `10.1109/radar.2014.6875553` |

---

## 2. 波形设计

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2022 | An AFDM-Based Integrated Sensing and Communications | ISWCS 2022 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/An AFDM-Based Integrated Sensing and Communications\|笔记]] |
| 2025 | A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Near-Fie… | IEEE Internet of Things Journal | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation\|笔记]] |
| 2024 | Diagonally Reconstructed Channel Estimation for MIMO-AFDM With Inter-Doppler Interfe… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Diagonally Reconstructed Channel Estimation for MIMO-AFDM\|笔记]] |
| 2025 | Deep Unfolding Learning Aided ISAC Transceiver Design | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Deep Unfolding ISAC Transceiver Design\|笔记]] |

### 二级分类 B：缺失方向

**缺口 1**：只有 AFDM 一条波形线（3 篇），**缺少 OFDM/OTFS 这两条最主流波形的经典与前沿**，导致无法论证「为什么选 AFDM」。**缺口 2**：缺少**波形相似度/恒模约束、PAPR、频谱兼容**等工程约束类文献。**缺口 3**：缺少**波形设计的信息论/优化理论根基**（经典 DFRC 最优波形）。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2011 | Waveform Design and Signal Processing Aspects for Fusion of Wireless Communications and Radar Sensing | Proc. IEEE | `10.1109/jproc.2011.2131110` |
| 2018 | Toward Dual-functional Radar-Communication Systems: Optimal Waveform Design | IEEE TSP | `10.1109/tsp.2018.2847648` |
| 2021 | Dual-Functional Radar-Communication Waveform Design: A Symbol-Level Precoding Approach | IEEE JSTSP | `10.1109/jstsp.2021.3111438` |
| 2009 | An OFDM System Concept for Joint Radar and Communications Operations | IEEE VTC | `10.1109/vetecs.2009.5073387` |
| 2009 | A Novel Approach to OFDM Radar Processing | IEEE Radar Conf | `10.1109/radar.2009.4977002` |
| 2017 | Orthogonal Time Frequency Space Modulation | IEEE WCNC | `10.1109/wcnc.2017.7925924` |
| 2025 | A Novel OTFS-Chirp Waveform for Low-Complexity Multiuser Joint Sensing and Communication | IEEE IoTJ | `10.1109/jiot.2024.3509922` |
| 2023 | Waveform Design with Constellation Extension for OFDM Dual-Functional Radar-Communication | IEEE TVT | `10.1109/tvt.2023.3281130` |
| 2024 | Index Modulation for Integrated Sensing and Communications: A Signal Processing Perspective | IEEE SPM | `10.1109/msp.2024.3444195` |
| 2020 | Joint Radar-Communication With Cyclic Prefixed Single Carrier Waveforms | IEEE TVT | `10.1109/tvt.2020.2975243` |
| 2026 | A Tutorial on MIMO-OFDM ISAC: From Far-Field to Near-Field | IEEE COMST | `10.1109/comst.2025.3650568` |

---

## 3. 波束成形

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2026 | Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Ba… | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Optimal ISAC Beamforming Structure\|笔记]] |
| 2025 | Learning to Beamform for Integrated Sensing and Communication: A Graph Neural Networ… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Learning to Beamform for ISAC (GNN)\|笔记]] |
| 2022 | NOMA Empowered Integrated Sensing and Communication (RIS-Assisted) | IEEE GLOBECOM Workshops | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/NOMA Empowered ISAC with RIS\|笔记]] |
| 2025 | Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/STAR-IRS SCMA ISAC Beamforming (THz)\|笔记]] |
| 2026 | LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in N… | IEEE Journal on Selected Areas in Communicat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/LLM in V2I Predictive Beamforming\|笔记]] |
| 2026 | ISAC-Enabled Beam Tracking for U2U Communication Systems Under Jittering Effects | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC-Enabled Beam Tracking for U2U\|笔记]] |
| 2026 | Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinching-A… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/PASS Joint Radiation Power Antenna Position Beamforming\|笔记]] |
| 2026 | MIMO-PASS: Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/MIMO-PASS Uplink and Downlink Transmission\|笔记]] |

### 二级分类 B：缺失方向

**缺口 1**：缺少**经典 CRB 波束成形**（Liu/Zhang 的 CRB 优化与多用户 MIMO+雷达联合发射波束成形），这是你现有「最优结构」论文的理论前置。**缺口 2**：缺少**混合波束成形（模拟/数字）与宽带/波束斜视**，而你的 UAV/THz 场景必然涉及。**缺口 3**：缺少**多波束与干扰管理**综述。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2022 | Cramér-Rao Bound Optimization for Joint Radar-Communication Beamforming | IEEE TSP | `10.1109/tsp.2021.3135692` |
| 2020 | Joint Transmit Beamforming for Multiuser MIMO Communications and MIMO Radar | IEEE TSP | `10.1109/tsp.2020.3004739` |
| 2024 | Multi-Beam Integrated Sensing and Communication: State-of-the-Art, Challenges and Opportunities | IEEE CommMag | `10.1109/mcom.001.2300634` |
| 2026 | Wideband Hybrid Beamforming for Integrated Sensing and Communication Systems | IEEE TWC | `10.1109/twc.2026.3651469` |
| 2026 | Joint Array Partitioning and Beamforming Designs in ISAC Systems: A Bayesian CRB Perspective | IEEE JSAC | `10.1109/jsac.2025.3608773` |
| 2019 | Dual-Function MIMO Radar Communications System Design Via Sparse Array Optimization | IEEE TAES | `10.1109/taes.2018.2866038` |
| 2023 | Transmit Sparse Array Beamformer Design for Dual-Function Radar Communication Systems | IEEE Radar Conf | `10.1109/radar54928.2023.10371099` |
| 2020 | Waveform Design for Dual-function MIMO Radar-communication Systems | IEEE SAM | `10.1109/sam48682.2020.9104378` |
| 2026 | Coordinated Beamforming for Multi-Cell ISAC Using Graph Neural Networks | IEEE TWC | `10.1109/twc.2025.3621437` |
| 2024 | Interference Mitigation for Network-Level ISAC: An Optimization Perspective | IEEE CommMag | `10.1109/mcom.001.2300674` |

---

## 4. MIMO ISAC

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2026 | Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Ba… | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Optimal ISAC Beamforming Structure\|笔记]] |
| 2025 | Deep Unfolding Learning Aided ISAC Transceiver Design | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Deep Unfolding ISAC Transceiver Design\|笔记]] |
| 2024 | Under-Determined DOA Estimation: A Method Based on Higher-Order Statistics and Non-U… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Under-Determined DOA Estimation\|笔记]] |
| 2025 | Fast and Robust Channel Estimation for HMIMO: A Graph-Based Wavenumber-Domain Approa… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/HMIMO Graph-Based Wavenumber-Domain Channel Estimation\|笔记]] |
| 2025 | SSNet: Flexible and Robust Channel Extrapolation for Fluid Antenna Systems Enabled b… | IEEE Journal on Selected Areas in Communicat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/SSNet Channel Extrapolation for FAS\|笔记]] |
| 2025 | UAV-Enabled Passive 6D Movable Antenna for ISAC: Joint Location, Orientation, and Re… | IEEE Wireless Communications Letters | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC\|笔记]] |
| 2026 | MIMO-PASS: Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/MIMO-PASS Uplink and Downlink Transmission\|笔记]] |
| 2026 | Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinching-A… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/PASS Joint Radiation Power Antenna Position Beamforming\|笔记]] |

### 二级分类 B：缺失方向

**缺口 1**：**完全缺失无小区（Cell-Free）/分布式 MIMO ISAC**，这是 2025–2026 最热的方向之一，也是你 UAV 集群场景的天然延伸。**缺口 2**：缺少**超大阵列/全息 MIMO/近场**的 MIMO 视角文献。**缺口 3**：缺少**阵列划分（Array Partitioning）与天线选择**类文献。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2018 | MU-MIMO Communications With MIMO Radar: From Co-Existence to Joint Transmission | IEEE TWC | `10.1109/twc.2018.2803045` |
| 2025 | Cell-Free ISAC MIMO Systems: Joint Sensing and Communication Beamforming | IEEE TCOM | `10.1109/tcomm.2024.3490740` |
| 2026 | Joint Beamforming Optimization for ISAC in Cell-Free Massive MIMO Systems | IEEE TWC | `10.1109/twc.2026.3727657` |
| 2026 | Energy Efficiency for Massive MIMO Integrated Sensing and Communication Systems | IEEE JSAC | `10.1109/jsac.2025.3610821` |
| 2025 | Performance Analysis and Power Allocation for Massive MIMO ISAC Systems | IEEE TSP | `10.1109/tsp.2025.3554012` |
| 2026 | Cooperative ISAC for Joint Localization and Velocity Estimation in Cell-Free MIMO Systems | IEEE JSAC | `10.1109/jsac.2025.3613283` |
| 2025 | Integrated Location Sensing and Communication for Ultra-Massive MIMO With Hybrid-Field Beam-Squint | IEEE JSAC | `10.1109/jsac.2025.3531551` |
| 2025 | Performance Analysis of Holographic MIMO Based Integrated Sensing and Communications | IEEE TCOM | `10.1109/tcomm.2025.3529209` |
| 2026 | A Survey on Reconfigurable and Movable Antennas for Wireless Communications and Sensing | IEEE COMST | `10.1109/comst.2026.3663021` |
| 2025 | Movable Antenna Enabled Integrated Sensing and Communication | IEEE TWC | `10.1109/twc.2025.3525631` |

---

## 5. RIS 辅助 ISAC

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2022 | NOMA Empowered Integrated Sensing and Communication (RIS-Assisted) | IEEE GLOBECOM Workshops | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/NOMA Empowered ISAC with RIS\|笔记]] |
| 2025 | Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/STAR-IRS SCMA ISAC Beamforming (THz)\|笔记]] |
| 2025 | Near-Field Integrated Sensing and Communications for Secure UAV Networks | IEEE JSAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Near-Field Integrated Sensing and Communications for Secure UAV Networks\|笔记]] |

### 二级分类 B：缺失方向

**缺口 1**：只有 3 篇，且 **2 篇为会议短文**，缺**期刊级系统研究**。**缺口 2**：缺少 **STAR-RIS / 主动 RIS / 可动天线** 三类新型 RIS 变体（你的 STAR-IRS 笔记是 THz+SCMA 组合，未覆盖 RIS 本身的设计权衡）。**缺口 3**：缺少 **RIS 相移离散化、信道估计误差、双站/多站 RIS** 的鲁棒性分析。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2025 | The Emergence of Multi-Functional and Hybrid Reconfigurable Intelligent Surfaces for ISAC | IEEE COMST | `10.1109/comst.2024.3519785` |
| 2025 | A Survey on Integrated Sensing and Communication With Intelligent Metasurfaces: Trends, Challenges | IEEE OJCOMS | `10.1109/ojcoms.2025.3594049` |
| 2024 | STAR-RIS Aided Integrated Sensing and Communication Over High Mobility Scenario | IEEE TCOM | `10.1109/tcomm.2024.3381725` |
| 2026 | Cramér-Rao Bound Optimization for Active RIS Aided Device-Based ISAC System | IEEE TWC | `10.1109/twc.2026.3656644` |
| 2026 | STAR-RIS Enabled Air-Ground Near-Field ISAC | IEEE TWC | `10.1109/twc.2025.3602989` |
| 2026 | Robust Beamforming for Active STAR-RIS-Aided Integrated Sensing and Communication | IEEE WCL | `10.1109/lwc.2026.3671417` |
| 2026 | Partitioned Sensing-Communication Trade-off for Dual STAR-RIS-Aided ISAC Systems | IEEE IoTJ | `10.1109/jiot.2026.3731215` |
| 2026 | Beam Training for RIS-Aided ISAC Systems | IEEE TWC | `10.1109/twc.2026.3717972` |
| 2026 | Shifting the Sensing Versus Data-Security Tradeoff in ISAC Systems With Active RIS | IEEE TCOM | `10.1109/tcomm.2026.3725034` |
| 2023 | Simultaneous Beam Training and Target Sensing for RIS-Aided ISAC | IEEE ICC | `10.1109/icc45041.2023.10279742` |

---

## 6. UAV / 车联网 ISAC

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2022 | ISAC from the Sky: UAV Trajectory Design for Joint Communication and Target Localiza… | IEEE Journal on Selected Areas in Communicat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC from the Sky UAV Trajectory Design\|笔记]] |
| 2025 | Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC for Low-Altitude Economy DRL\|笔记]] |
| 2026 | ISAC-Enabled Beam Tracking for U2U Communication Systems Under Jittering Effects | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC-Enabled Beam Tracking for U2U\|笔记]] |
| 2025 | Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative I… | IEEE Transactions on Vehicular Technology | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Joint Target Assignment and Resource Allocation (Fairness)\|笔记]] |
| 2026 | LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in N… | IEEE Journal on Selected Areas in Communicat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/LLM in V2I Predictive Beamforming\|笔记]] |
| 2026 | Integrated Sensing and Communications in Multi-UAV Networks: A Dual-Objective Optimi… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization\|笔记]] |
| 2024 | Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UAV Netw… | IEEE GLOBECOM Workshops | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV\|笔记]] |
| 2026 | A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Control-Based Beamforming and Trajectory for UAV-ISAC\|笔记]] |
| 2025 | Cooperative ISAC-Empowered Low-Altitude Economy | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Cooperative ISAC-Empowered Low-Altitude Economy\|笔记]] |
| 2026 | Curriculum-Guided Heterogeneous Multi-Agent Intelligence for Multi-UAV Cooperative I… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC\|笔记]] |
| 2026 | ISAC Enabled Anti-UAV: Joint Beamforming and Trajectory Design for Multi-UAVs | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Anti-UAV\|笔记]] |
| 2025 | ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Cooperative Detection for UAV\|笔记]] |
| 2025 | Integrated Sensing, Communication, and Over-The-Air Control of UAV Swarm Dynamics | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC-OTA UAV Swarm Dynamics\|笔记]] |
| 2026 | Joint Beamforming and UAV Deployment Optimization for ISAC-Enhanced UAV-Assisted VEC | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Joint Beamforming and UAV Deployment for ISAC-VEC\|笔记]] |
| 2026 | Memory-Enhanced Dynamic Self-Attention Communication Mechanism for Multi-UAV Base St… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning\|笔记]] |
| 2025 | Near-Field Integrated Sensing and Communications for Secure UAV Networks | IEEE JSAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Near-Field Integrated Sensing and Communications for Secure UAV Networks\|笔记]] |
| 2026 | Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource Alloca… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Optimal Transport Framework for Low-Altitude ISAC\|笔记]] |
| 2026 | Predictive Control Over Low-Altitude Wireless Networks: Joint Trajectory Design and … | IEEE Transactions on Mobile Computing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks\|笔记]] |
| 2025 | Radar Probing Optimization for Joint Beamforming and UAV Trajectory Design in UAV-En… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Radar Probing Optimization for Joint Beamforming and UAV Trajectory\|笔记]] |
| 2026 | Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications\|笔记]] |
| 2026 | Situation-Aware Hybrid Sensing and Position Control for UAV-Assisted ISAC Systems | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Situation-Aware Hybrid Sensing for UAV-ISAC\|笔记]] |
| 2025 | UAV-Assisted 5G Networks: Mobility-Aware 3D Trajectory Optimization and Resource All… | IEEE VTC2025-Fall | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory\|笔记]] |
| 2025 | UAV-Enabled Passive 6D Movable Antenna for ISAC: Joint Location, Orientation, and Re… | IEEE Wireless Communications Letters | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC\|笔记]] |
| 2026 | Channel Knowledge Map Enabled Low-Altitude ISAC Networks: Joint Air Corridor Plannin… | IEEE Wireless Communications Letters | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC\|笔记]] |
| 2020 | Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area | IEEE Transactions on Aerospace and Electroni | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area\|笔记]] |
| 2025 | Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-D… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks\|笔记]] |

### 二级分类 B：缺失方向

**这是你最强的一类（26 篇）**，但仍有三个缺口：**缺口 1**：缺少**低空经济的综述/杂志级纲领文献**，开题时无法一句话说清「低空 ISAC 为什么重要」。**缺口 2**：缺少**空地信道测量与建模**的期刊级文献（只有 1 篇 2020 年 UWB 实测），而你的轨迹/波束设计全部依赖信道模型假设。**缺口 3**：缺少**多 UAV 协同的组网/干扰协调**与**续航能量约束**的专门研究。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2025 | An Overview of Cellular ISAC for Low-Altitude UAV: New Opportunities and Challenges | IEEE CommMag | `10.1109/mcom.002.2400742` |
| 2025 | Networked ISAC for Low-Altitude Economy: Coordinated Transmit Beamforming and UAV Trajectory Design | IEEE TCOM | `10.1109/tcomm.2025.3541027` |
| 2026 | Integrated Sensing, Communication, and Computing for Low-Altitude Economy: UAV Placement and Resource | IEEE TCOM | `10.1109/tcomm.2026.3704147` |
| 2026 | A Novel Integrated Sensing and Communication Scheme in UAVs-Enabled Vehicular Networks With MARL | IEEE TMC | `10.1109/tmc.2025.3591259` |
| 2026 | Movable Antenna-Enabled Integrated Sensing and Communication in Low-Altitude UAV Networks | IEEE IoTJ | `10.1109/jiot.2026.3695058` |
| 2026 | CKM-Enabled Joint Spatial-Doppler Domain Clutter Suppression for Low-Altitude UAV ISAC | IEEE IoTJ | `10.1109/jiot.2026.3689485` |
| 2026 | Ray Antenna Array Achieves Uniform Angular Resolution for Low-Altitude UAV Swarm ISAC | IEEE TWC | `10.1109/twc.2025.3643458` |
| 2026 | Air-Ground Collaborative ISAC for LAE: UAV Swarms as Virtual Aerial Arrays | IEEE CommMag | `10.1109/mcom.001.2600190` |
| 2026 | Joint Beamforming and Trajectory Design for Multi-UAV-Assisted ISCC | IEEE JSAC | `10.1109/jsac.2026.3707817` |
| 2026 | Integrated Sensing and Communications for Vehicular Networks: A Survey | J. Adv. Signal Process. | `10.1186/s13634-026-01332-0` |
| 2026 | A Survey on Detection, Classification, and Tracking of AAVs Using Radar and Communications | IEEE COMST | `10.1109/comst.2025.3554613` |
| 2025 | Integrated Radar Sensing, Communication and Computation UAV Networks: A Survey | TechRxiv 预印本 | `10.36227/techrxiv.172866072.21185086/v2` |

---

## 7. 高移动场景 ISAC

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2026 | ISAC-Enabled Beam Tracking for U2U Communication Systems Under Jittering Effects | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC-Enabled Beam Tracking for U2U\|笔记]] |
| 2022 | An AFDM-Based Integrated Sensing and Communications | ISWCS 2022 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/An AFDM-Based Integrated Sensing and Communications\|笔记]] |
| 2025 | A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Near-Fie… | IEEE Internet of Things Journal | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation\|笔记]] |
| 2024 | Diagonally Reconstructed Channel Estimation for MIMO-AFDM With Inter-Doppler Interfe… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Diagonally Reconstructed Channel Estimation for MIMO-AFDM\|笔记]] |
| 2025 | Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-D… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks\|笔记]] |

### 二级分类 B：缺失方向

**缺口 1（关键）**：**完全没有多普勒/时变信道的专门理论文献**——你的 AFDM 笔记提到了多普勒，但没有一篇讲**高移动下的信道建模、时延-多普勒域信号处理、OTFS 的感知机理**。**缺口 2**：缺少 **OTFS/ODDM 波形在 ISAC 中的前沿**（2025–2026 JSAC 有专刊）。**缺口 3**：缺少**双站/异步时钟**这一高移动感知的实际难点。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2026 | Integrated Sensing and Communication for Symbiotic Radio over High-Mobility Channels | IEEE TVT | `10.1109/tvt.2026.3717756` |
| 2024 | From Orthogonal Time-Frequency Space to Affine Frequency-Division Multiplexing: A Comparative Study | IEEE SPM | `10.1109/msp.2024.3422653` |
| 2026 | ISAC MIMO Systems With OTFS Waveforms and Virtual Arrays | IEEE JSAC | `10.1109/jsac.2025.3608761` |
| 2026 | Customized OTFS Pulse Compression and Waveform Optimization for Enhancing Target Sensing | IEEE JSAC | `10.1109/jsac.2025.3611394` |
| 2026 | Hybrid Beamforming With Orthogonal Delay-Doppler Division Multiplexing Modulation for THz Sensing | IEEE JSAC | `10.1109/jsac.2025.3610799` |
| 2024 | Sensing in Bistatic ISAC Systems With Clock Asynchronism: A Signal Processing Perspective | IEEE SPM | `10.1109/msp.2024.3418725` |
| 2023 | Exploiting Double Timescales for Integrated Sensing and Communication with Delay-Doppler Alignment | IEEE ICC | `10.1109/icc45041.2023.10279599` |
| 2025 | Interference Mitigation via Doppler Filtering in Integrated Sensing and Communication Networks | IEEE ICC | `10.1109/icc52391.2025.11161142` |
| 2024 | Enhancing Doppler Resilience for Integrated Sensing and Communication Systems | IEEE ICCT | `10.1109/icct62411.2024.10946432` |
| 2026 | Evaluating AFDM-Based Integrated Sensing and Communication in Vehicular Scenarios | IEEE ICC | `10.1109/icc59461.2026.11586892` |

---

## 8. AI 辅助 ISAC

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2025 | Learning to Beamform for Integrated Sensing and Communication: A Graph Neural Networ… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Learning to Beamform for ISAC (GNN)\|笔记]] |
| 2025 | Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC for Low-Altitude Economy DRL\|笔记]] |
| 2025 | Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-D… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks\|笔记]] |
| 2026 | Curriculum-Guided Heterogeneous Multi-Agent Intelligence for Multi-UAV Cooperative I… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC\|笔记]] |
| 2025 | Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/STAR-IRS SCMA ISAC Beamforming (THz)\|笔记]] |
| 2026 | LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in N… | IEEE Journal on Selected Areas in Communicat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/LLM in V2I Predictive Beamforming\|笔记]] |
| 2025 | Deep Unfolding Learning Aided ISAC Transceiver Design | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Deep Unfolding ISAC Transceiver Design\|笔记]] |
| 2025 | Learning to Optimize Resource Allocation in Dynamic Wireless Environments: Embracing… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Learning to Optimize Resource Allocation in Dynamic Wireless\|笔记]] |
| 2026 | Memory-Enhanced Dynamic Self-Attention Communication Mechanism for Multi-UAV Base St… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning\|笔记]] |
| 2025 | WDMoE: Wireless Distributed Mixture of Experts for Large Language Models | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/WDMoE Wireless Distributed Mixture of Experts\|笔记]] |
| 2023 | Attention Is All You Need | arXiv preprint (cs.CL) | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/LLM/Attention Is All You Need\|笔记]] |
| 2025 | Normalizing Flow-Based Differentiable Particle Filters | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Normalizing Flow-Based Differentiable Particle Filters\|笔记]] |
| 2025 | OptiPMB: Enhancing 3D Multi-Object Tracking With Optimized Poisson Multi-Bernoulli F… | IEEE Transactions on Intelligent Transportat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/OptiPMB 3D Multi-Object Tracking\|笔记]] |
| 2025 | Overparameterized ReLU Neural Networks Learn the Simplest Model: Neural Isometry and… | IEEE Transactions on Information Theory | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Overparameterized ReLU Neural Networks\|笔记]] |

### 二级分类 B：缺失方向

**数量最多（14 篇）但结构失衡**：**缺口 1**：缺少**学习方法在 ISAC 中的系统性综述**（无法论证「为什么用学习」而非「为什么用这个网络」）。**缺口 2**：缺少**可解释性、泛化性（sim-to-real）、训练开销**的批判性文献——你自己笔记里反复写「仿真验证、无实测」，这正是开题可以立论的点。**缺口 3**：缺少**扩散模型/大模型/语义通信**等 2026 新范式。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2026 | A Tutorial on AI-Empowered Integrated Sensing and Communications | IEEE COMST | `10.1109/comst.2026.3665143` |
| 2026 | Advanced Learning Algorithms for Integrated Sensing and Communication (ISAC) Systems in 6G | IEEE COMST | `10.1109/comst.2025.3584333` |
| 2026 | Integrated Radio Sensing Capabilities for 6G Networks: AI/ML Perspective | IEEE COMST | `10.1109/comst.2026.3668458` |
| 2024 | A Survey on Machine Learning Enhanced Integrated Sensing and Communication Systems | IEEE Access | `10.1109/access.2024.3501363` |
| 2023 | Graph Neural Networks for Joint Communication and Sensing Optimization in Vehicular Networks | IEEE JSAC | `10.1109/jsac.2023.3322761` |
| 2024 | Deep Learning-Based Joint Transmit Beamforming for Dual-Functional Radar-Communication | IEEE TWC | `10.1109/twc.2024.3427368` |
| 2023 | Reinforcement Learning Based Dual-Functional Massive MIMO Systems for Multi-Target Detection | IEEE TSP | `10.1109/tsp.2023.3252885` |
| 2026 | Deep Learning-Based Predictive Bidirectional Beamforming in ISAC-Enabled UAV Networks | IEEE TWC | `10.1109/twc.2026.3664980` |
| 2025 | Joint Deep Reinforcement Learning and Unfolding for Sensing and Communication Function Selection | IEEE TVT | `10.1109/tvt.2024.3495536` |
| 2026 | Deep Unfolding for RIS Enabled Backscatter Integrated Sensing and Communication | IEEE TVT | `10.1109/tvt.2026.3697040` |

---

## 9. 资源分配

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2024 | Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UAV Netw… | IEEE GLOBECOM Workshops | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV\|笔记]] |
| 2025 | Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative I… | IEEE Transactions on Vehicular Technology | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Joint Target Assignment and Resource Allocation (Fairness)\|笔记]] |
| 2026 | Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource Alloca… | IEEE Transactions on Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Optimal Transport Framework for Low-Altitude ISAC\|笔记]] |
| 2025 | Learning to Optimize Resource Allocation in Dynamic Wireless Environments: Embracing… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Learning to Optimize Resource Allocation in Dynamic Wireless\|笔记]] |
| 2025 | Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/STAR-IRS SCMA ISAC Beamforming (THz)\|笔记]] |
| 2025 | Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC for Low-Altitude Economy DRL\|笔记]] |
| 2026 | Channel Knowledge Map Enabled Low-Altitude ISAC Networks: Joint Air Corridor Plannin… | IEEE Wireless Communications Letters | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC\|笔记]] |
| 2025 | Communication-Control Codesign for Large-Scale Wireless Networked Control Systems | IEEE JSAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Communication-Control Codesign for Large-Scale Wireless Networked Control Systems\|笔记]] |
| 2025 | SeCo4: Co-Design of Sensing, Communication, and Computing for Intelligent Control in… | IEEE Journal on Selected Areas in Communicat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/SeCo4 Co-Design of Sensing Communication and Computing\|笔记]] |
| 2019 | Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems | IEEE Transactions on Vehicular Technology | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/URLLC Resource Allocation for Real-Time Wireless Control\|笔记]] |
| 2025 | Random Access Control in NB-IoT With Model-Based Reinforcement Learning | IEEE Internet of Things Journal, 12(7), 8135 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Random Access Control in NB-IoT With Model-Based Reinforcement Learning\|笔记]] |

### 二级分类 B：缺失方向

**缺口 1**：缺少**资源分配的公平性理论**（α-fairness、max-min 与效率和公平的权衡）——你只有 1 篇 max-min 会议/期刊文。**缺口 2**：缺少**感知-通信-计算一体化（ISCC）的资源分配综述**。**缺口 3**：缺少**能量效率**作为独立优化目标的系统研究。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2024 | Maximizing the Value of Service Provisioning in Multi-User ISAC Systems Through Fairness | IEEE JSAC | `10.1109/jsac.2024.3413973` |
| 2024 | Channel Sharing Aided Integrated Sensing and Communication: An Energy-Efficient Sensing Scheduling | IEEE TWC | `10.1109/twc.2023.3322680` |
| 2023 | Sensing Fairness-Based Energy Efficiency Optimization for UAV Enabled ISAC | IEEE WCL | `10.1109/lwc.2023.3288529` |
| 2023 | Energy-Efficient Integrated Sensing and Communication: A Multi-Access Edge Computing Design | IEEE WCL | `10.1109/lwc.2023.3306433` |
| 2026 | Joint Optimization of Sensing, Communication, and Computing for Collaborative Multi-UAV Edge | IEEE TWC | `10.1109/twc.2025.3590253` |
| 2025 | Joint Task Scheduling and Resource Allocation for UAV-Assisted Air-Ground Collaborative ISAC | IEEE TCOM | `10.1109/tcomm.2025.3591748` |
| 2025 | A Survey on Integrated Sensing, Communication, and Computation | IEEE COMST | `10.1109/comst.2024.3521498` |
| 2025 | Interference Management for Integrated Sensing and Communication Systems: A Survey | IEEE IoTJ | `10.1109/jiot.2024.3506162` |
| 2025 | Integrated Sensing and Communication Channel Modeling: A Survey | IEEE IoTJ | `10.1109/jiot.2024.3449377` |
| 2025 | Integrated Sensing, Communication, and Computing With Max-Min Fairness | IEEE TWC | `10.1109/twc.2025.3631338` |

---

## 10. 目标检测与跟踪

### 二级分类 A：已阅读论文

| 年份 | 标题 | 期刊/会议 | 笔记 |
|---|---|---|---|
| 2025 | ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Cooperative Detection for UAV\|笔记]] |
| 2026 | ISAC Enabled Anti-UAV: Joint Beamforming and Trajectory Design for Multi-UAVs | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Anti-UAV\|笔记]] |
| 2025 | Cooperative ISAC-Empowered Low-Altitude Economy | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Cooperative ISAC-Empowered Low-Altitude Economy\|笔记]] |
| 2025 | OptiPMB: Enhancing 3D Multi-Object Tracking With Optimized Poisson Multi-Bernoulli F… | IEEE Transactions on Intelligent Transportat | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/OptiPMB 3D Multi-Object Tracking\|笔记]] |
| 2025 | Normalizing Flow-Based Differentiable Particle Filters | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Normalizing Flow-Based Differentiable Particle Filters\|笔记]] |
| 2025 | Passive Human Tracking With WiFi Point Clouds | IEEE Internet of Things Journal | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Passive Human Tracking With WiFi Point Clouds\|笔记]] |
| 2022 | Environment Sensing Considering the Occlusion Effect: A Multi-View Approach | IEEE Transactions on Signal Processing | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Environment Sensing with Occlusion Effect\|笔记]] |
| 2024 | Under-Determined DOA Estimation: A Method Based on Higher-Order Statistics and Non-U… | IEEE Transactions on Wireless Communications | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Under-Determined DOA Estimation\|笔记]] |
| 2025 | Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative I… | IEEE Transactions on Vehicular Technology | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Joint Target Assignment and Resource Allocation (Fairness)\|笔记]] |

### 二级分类 B：缺失方向

**缺口 1（关键）**：你的跟踪类笔记（OptiPMB、粒子滤波、WiFi 跟踪）来自**雷达/视觉/无线感知社区**，**没有一篇是 ISAC 框架下的目标跟踪**——即「用通信信号做跟踪」与「跟踪算法本身」之间是断开的。**缺口 2**：缺少**检测性能理论**（检测概率、虚警率与速率的关系）。**缺口 3**：缺少**扩展目标/多目标分辨**与**实测验证**。

### 二级分类 C：推荐补充论文

| 年份 | 论文 | 期刊/会议 | DOI |
|---|---|---|---|
| 2026 | Scalable Integrated Sensing and Communications for Multi-Target Detection and Tracking in Cell-Free | IEEE TCOM | `10.1109/tcomm.2025.3642717` |
| 2025 | Joint Angle and Velocity-Estimation for Target Localization in Bistatic mmWave MIMO Radar | IEEE TCOM | `10.1109/tcomm.2025.3581046` |
| 2026 | A Closed-Form Single-Array Integrated Localization and Sensing Solution Using Hybrid Arrays | IEEE TSP | `10.1109/tsp.2026.3733157` |
| 2026 | Radar and Camera Fusion for Object Detection and Tracking: A Comprehensive Survey | IEEE COMST | `10.1109/comst.2025.3599596` |
| 2025 | Signal Accumulation and Parameter Estimation for Target Detection on Dual-Function Radar | IEEE IoTJ | `10.1109/jiot.2025.3530874` |
| 2023 | Multiuser Beam Tracking and Target Detection in Integrated Sensing and Communication | IEEE ICC | `10.1109/icc45041.2023.10279142` |
| 2026 | 3D Cooperative User Tracking for Distributed Integrated Sensing and Communication | IEEE ICC | `10.1109/icc59461.2026.11587979` |
| 2026 | Experimental Demonstration of Multi-Target Tracking in Integrated Sensing and Communication | EuCNC/6G Summit | `10.1109/eucnc/6gsummit68295.2026.11577419` |
| 2023 | A Unified Channel Model for Both Communication and Sensing in Integrated Sensing and Communication | IEEE VTC-Fall | `10.1109/vtc2023-fall60731.2023.10333766` |
| 2024 | Simultaneous Multi-Beam Sweeping for mmWave Massive MIMO Integrated Sensing and Communication | IEEE TVT | `10.1109/tvt.2024.3350714` |

---
