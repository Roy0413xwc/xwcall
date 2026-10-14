---
type: "thesis-prep"
title: "ISAC 已读论文结构化提取（52 篇）"
aliases: ["已读论文提取", "ISAC 文献清单"]
created: "2026-10-14"
last_updated: "2026-10-14"
source: "02vault 精读笔记（Analytical Notes）"
evidence_status: "note_only"
---

# ISAC 已读论文结构化提取（52 篇）

> [!summary] 说明
> 本表由 `02vault/` 全部中文精读笔记的 frontmatter 与正文自动提取，**证据等级为 note_only**（未逐篇回原文核验）。
> 字段口径：研究问题取自笔记第 3 节；方法取自 `methodology` 字段；使用模型取自第 5 节 Model/Framework；优点取自第 9 节作者创新；不足与未来方向取自第 10 节。
> 笔记中原为空的字段在表中以「笔记未记录」标注，不做推测填补。

## 统计总览

- 已读论文总数：**52 篇**（UAV 18、ISAC 18、信道估计 4、其他 11、LLM 1）
- 年份分布：2026 年 16 篇、2025 年 25 篇、2024 年 3 篇、2023 年 1 篇、2022 年 5 篇、2020 年 1 篇、2019 年 1 篇
- 2025–2026 年论文占比：**41/52**（说明文献库高度集中于近两年热点）

## 一、总表（速查）

| # | 标题 | 作者 | 年份 | 期刊/会议 | 分类 | 笔记 |
|---|---|---|---|---|---|---|
| 1 | A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC Syst… | Bin Li, Hongyun Zhang, Yue Rong, Zhu Han | 2026 | IEEE Transactions on Wireless Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Control-Based Beamforming and Trajectory for UAV-ISAC\|笔记]] |
| 2 | Curriculum-Guided Heterogeneous Multi-Agent Intelligence for Multi-UAV Coopera… | Kang Yan, Luping Xiang, Kang Zheng, Jienan Chen, Jun… | 2026 | IEEE Transactions on Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC\|笔记]] |
| 3 | ISAC Enabled Anti-UAV: Joint Beamforming and Trajectory Design for Multi-UAVs | Xiaojie Wang, Lingfei Li, Zhaolong Ning, Xiaoming Ta… | 2026 | IEEE Transactions on Wireless Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Anti-UAV\|笔记]] |
| 4 | Joint Beamforming and UAV Deployment Optimization for ISAC-Enhanced UAV-Assist… | Chunlin Li, Wenhao Wu, Zhihao Zhang, Tianbing Ma, Sh… | 2026 | IEEE Transactions on Wireless Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Joint Beamforming and UAV Deployment for ISAC-VEC\|笔记]] |
| 5 | Memory-Enhanced Dynamic Self-Attention Communication Mechanism for Multi-UAV B… | Hanxiao Yuan, Yao Shi, Emad Alsusa, Qinyu Zhang, Yip… | 2026 | IEEE Transactions on Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning\|笔记]] |
| 6 | Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource … | Yufeng Zheng, Lixin Li, Wensheng Lin, Wei Liang, Qin… | 2026 | IEEE Transactions on Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Optimal Transport Framework for Low-Altitude ISAC\|笔记]] |
| 7 | Predictive Control Over Low-Altitude Wireless Networks: Joint Trajectory Desig… | Haijia Jin, Jun Wu, Weijie Yuan, Ruizhi Ruan, Jiache… | 2026 | IEEE Transactions on Mobile Computing | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks\|笔记]] |
| 8 | Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communic… | Shangpeng Wang, Ling Chen, Xiatong Hou, Xinyue Wang,… | 2026 | IEEE Transactions on Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications\|笔记]] |
| 9 | Situation-Aware Hybrid Sensing and Position Control for UAV-Assisted ISAC Syst… | Ling Lyu, Qirui Luo, Yanpeng Dai, Nan Cheng, Cailian… | 2026 | IEEE Transactions on Wireless Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Situation-Aware Hybrid Sensing for UAV-ISAC\|笔记]] |
| 10 | Cooperative ISAC-Empowered Low-Altitude Economy | Jun Tang, Yiming Yu, Cunhua Pan, Hong Ren, Dongming … | 2025 | IEEE Transactions on Wireless Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Cooperative ISAC-Empowered Low-Altitude Economy\|笔记]] |
| 11 | ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network | Yi Wang, Keke Zu, Luping Xiang, Qixun Zhang, Zhiyong… | 2025 | IEEE Transactions on Wireless Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Cooperative Detection for UAV\|笔记]] |
| 12 | Integrated Sensing, Communication, and Over-The-Air Control of UAV Swarm Dynam… | Zhuangkun Wei, Wenxiu Hu, Yathreb Bouazizi, Chenguan… | 2025 | IEEE Transactions on Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC-OTA UAV Swarm Dynamics\|笔记]] |
| 13 | Near-Field Integrated Sensing and Communications for Secure UAV Networks | Jingjing Zhao, Songtao Xue, Kaiquan Cai, Xidong Mu, … | 2025 | IEEE JSAC | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Near-Field Integrated Sensing and Communications for Secure UAV Networks\|笔记]] |
| 14 | Radar Probing Optimization for Joint Beamforming and UAV Trajectory Design in … | Yaxi Liu, Wencan Mao, Boxin He, Wei Huangfu, Tianyao… | 2025 | IEEE Transactions on Communications | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Radar Probing Optimization for Joint Beamforming and UAV Trajectory\|笔记]] |
| 15 | UAV-Assisted 5G Networks: Mobility-Aware 3D Trajectory Optimization and Resour… | Asad Mahmood, Thang X. Vu, Wali Ullah Khan, Symeon C… | 2025 | IEEE VTC2025-Fall | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory\|笔记]] |
| 16 | UAV-Enabled Passive 6D Movable Antenna for ISAC: Joint Location, Orientation, … | Peilan Wang, Yu Xue, Weidong Mei, Jun Fang, Rui Zhan… | 2025 | IEEE Wireless Communications Letters | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC\|笔记]] |
| 17 | ISAC from the Sky: UAV Trajectory Design for Joint Communication and Target Lo… | Xiaoye Jing, Fan Liu, Christos Masouros, Yong Zeng | 2022 | IEEE Journal on Selected Areas in Communicatio | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC from the Sky UAV Trajectory Design\|笔记]] |
| 18 | Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open A… | Wahab Khawaja, Ozgur Ozdemir, Fatih Erden, Ismail Gu… | 2020 | IEEE Transactions on Aerospace and Electronic  | UAV | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area\|笔记]] |
| 19 | Channel Knowledge Map Enabled Low-Altitude ISAC Networks: Joint Air Corridor P… | Jiaxuan Li, Yilong Chen, Fan Liu, Jie Xu | 2026 | IEEE Wireless Communications Letters | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC\|笔记]] |
| 20 | ISAC-Enabled Beam Tracking for U2U Communication Systems Under Jittering Effec… | Wei Liu, Yuhang Tang, Jinkun Zhu, Peng Yang | 2026 | IEEE Transactions on Communications | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC-Enabled Beam Tracking for U2U\|笔记]] |
| 21 | LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Trackin… | Hongjia Huang, Weijie Yuan, Chang Liu, Liang Liu, Fa… | 2026 | IEEE Journal on Selected Areas in Communicatio | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/LLM in V2I Predictive Beamforming\|笔记]] |
| 22 | Integrated Sensing and Communications in Multi-UAV Networks: A Dual-Objective … | (PDF 首页作者行未在当前全文提取中定位) | 2026 | IEEE Transactions on Wireless Communications | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization\|笔记]] |
| 23 | Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and C… | Tianyu Fang, Mengyuan Ma, Markku Juntti, Nir Shlezin… | 2026 | IEEE Transactions on Signal Processing | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Optimal ISAC Beamforming Structure\|笔记]] |
| 24 | A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Ne… | Yirui Luo, Yong Liang Guan, Yao Ge, David González G… | 2025 | IEEE Internet of Things Journal | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation\|笔记]] |
| 25 | Communication-Control Codesign for Large-Scale Wireless Networked Control Syst… | Gaoyang Pang, Wanchun Liu, Dusit Niyato, Branka Vuce… | 2025 | IEEE JSAC | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Communication-Control Codesign for Large-Scale Wireless Networked Control Systems\|笔记]] |
| 26 | Deep Unfolding Learning Aided ISAC Transceiver Design | Jifa Zhang, Yongxu Zhu, Nan Zhao, Shi Jin, Xianbin W… | 2025 | IEEE Transactions on Wireless Communications | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Deep Unfolding ISAC Transceiver Design\|笔记]] |
| 27 | Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Netw… | Chen Shang, Jiadong Yu, Dinh Thai Hoang | 2025 | IEEE Transactions on Wireless Communications | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks\|笔记]] |
| 28 | Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinfor… | Xiaowen Ye, Yuyi Mao, Xianghao Yu, Shu Sun, Liqun Fu… | 2025 | IEEE Transactions on Wireless Communications | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC for Low-Altitude Economy DRL\|笔记]] |
| 29 | Joint Target Assignment and Resource Allocation for Multi-Base Station Coopera… | Ruotong Li, Qixun Zhang, Dingyou Ma, Kan Yu, Yuzhen … | 2025 | IEEE Transactions on Vehicular Technology | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Joint Target Assignment and Resource Allocation (Fairness)\|笔记]] |
| 30 | Learning to Beamform for Integrated Sensing and Communication: A Graph Neural … | Yifei Zhao, Yong Zhou, Zixin Wang, Yuanming Shi, Nan… | 2025 | IEEE Transactions on Wireless Communications | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Learning to Beamform for ISAC (GNN)\|笔记]] |
| 31 | SeCo4: Co-Design of Sensing, Communication, and Computing for Intelligent Cont… | Qinqin Tang, Yutian Yang, Jiayi Cui, Renchao Xie, Ta… | 2025 | IEEE Journal on Selected Areas in Communicatio | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/SeCo4 Co-Design of Sensing Communication and Computing\|笔记]] |
| 32 | Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems… | Armin Farhadi, Ali Olfat, Christos Masouros | 2025 | IEEE Transactions on Wireless Communications | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/STAR-IRS SCMA ISAC Beamforming (THz)\|笔记]] |
| 33 | Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UA… | (PDF 首页作者行未在当前全文提取中定位) | 2024 | IEEE GLOBECOM Workshops | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV\|笔记]] |
| 34 | An AFDM-Based Integrated Sensing and Communications | Yuanhan Ni, Zulin Wang, Peng Yuan, Qin Huang | 2022 | ISWCS 2022 | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/An AFDM-Based Integrated Sensing and Communications\|笔记]] |
| 35 | Integrated Sensing and Communications: Toward Dual-Functional Wireless Network… | Fan Liu, Yuanhao Cui, Christos Masouros, Jie Xu, Ton… | 2022 | IEEE Journal on Selected Areas in Communicatio | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)\|笔记]] |
| 36 | NOMA Empowered Integrated Sensing and Communication (RIS-Assisted) | Zhaolin Wang, Yuanwei Liu, Xidong Mu, Zhiguo Ding, O… | 2022 | IEEE GLOBECOM Workshops | ISAC | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/NOMA Empowered ISAC with RIS\|笔记]] |
| 37 | Fast and Robust Channel Estimation for HMIMO: A Graph-Based Wavenumber-Domain … | Xufeng Guo, Yuanbin Chen, Ying Wang, Zhaocheng Wang,… | 2025 | IEEE Transactions on Wireless Communications | 信道估计 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/HMIMO Graph-Based Wavenumber-Domain Channel Estimation\|笔记]] |
| 38 | SSNet: Flexible and Robust Channel Extrapolation for Fluid Antenna Systems Ena… | Yuan Gao, Yiming Liu, Runze Yu, Shengli Liu, Yanlian… | 2025 | IEEE Journal on Selected Areas in Communicatio | 信道估计 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/SSNet Channel Extrapolation for FAS\|笔记]] |
| 39 | Diagonally Reconstructed Channel Estimation for MIMO-AFDM With Inter-Doppler I… | Haoran Yin, Xizhang Wei, Yanqun Tang, Kai Yang | 2024 | IEEE Transactions on Wireless Communications | 信道估计 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Diagonally Reconstructed Channel Estimation for MIMO-AFDM\|笔记]] |
| 40 | Under-Determined DOA Estimation: A Method Based on Higher-Order Statistics and… | Wei Peng, Peng Li, Xinyi Wu, Kai Luo, Gan Zheng, Don… | 2024 | IEEE Transactions on Wireless Communications | 信道估计 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Under-Determined DOA Estimation\|笔记]] |
| 41 | MIMO-PASS: Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems | (原文首页未在当前全文提取中定位到完整作者行) | 2026 | IEEE Transactions on Communications | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/MIMO-PASS Uplink and Downlink Transmission\|笔记]] |
| 42 | Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinc… | Yiming Xu, Dongfang Xu, Xianghao Yu, Shenghui Song, … | 2026 | IEEE Transactions on Wireless Communications | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/PASS Joint Radiation Power Antenna Position Beamforming\|笔记]] |
| 43 | Learning to Optimize Resource Allocation in Dynamic Wireless Environments: Emb… | Zhenrong Liu, Yang Li, Yik-Chung Wu, Yi Gong | 2025 | IEEE Transactions on Wireless Communications | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Learning to Optimize Resource Allocation in Dynamic Wireless\|笔记]] |
| 44 | Normalizing Flow-Based Differentiable Particle Filters | Xiongjie Chen, Yunpeng Li | 2025 | IEEE Transactions on Signal Processing | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Normalizing Flow-Based Differentiable Particle Filters\|笔记]] |
| 45 | OptiPMB: Enhancing 3D Multi-Object Tracking With Optimized Poisson Multi-Berno… | Guanhua Ding, Yuxuan Xia, Runwei Guan, Qinchen Wu, T… | 2025 | IEEE Transactions on Intelligent Transportatio | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/OptiPMB 3D Multi-Object Tracking\|笔记]] |
| 46 | Overparameterized ReLU Neural Networks Learn the Simplest Model: Neural Isomet… | Yifei Wang, Yixuan Hua, Emmanuel J. Candès, Mert Pil… | 2025 | IEEE Transactions on Information Theory | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Overparameterized ReLU Neural Networks\|笔记]] |
| 47 | Passive Human Tracking With WiFi Point Clouds | Zhongqin Wang, J. Andrew Zhang, Haimin Zhang, Min Xu… | 2025 | IEEE Internet of Things Journal | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Passive Human Tracking With WiFi Point Clouds\|笔记]] |
| 48 | Random Access Control in NB-IoT With Model-Based Reinforcement Learning | Juan J. Alcaraz; Juan-Carlos Sanchez-Aarnoutse; Alej… | 2025 | IEEE Internet of Things Journal, 12(7), 8135–8 | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Random Access Control in NB-IoT With Model-Based Reinforcement Learning\|笔记]] |
| 49 | WDMoE: Wireless Distributed Mixture of Experts for Large Language Models | Nan Xue, Yaping Sun, Zhiyong Chen, Meixia Tao, Xiaod… | 2025 | IEEE Transactions on Wireless Communications | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/WDMoE Wireless Distributed Mixture of Experts\|笔记]] |
| 50 | Environment Sensing Considering the Occlusion Effect: A Multi-View Approach | Xin Tong, Zhaoyang Zhang, Yihan Zhang, Zhaohui Yang,… | 2022 | IEEE Transactions on Signal Processing | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Environment Sensing with Occlusion Effect\|笔记]] |
| 51 | Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems | Bo Chang, Lei Zhang, Liying Li, Guodong Zhao, Zhi Ch… | 2019 | IEEE Transactions on Vehicular Technology | 其他 | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/URLLC Resource Allocation for Real-Time Wireless Control\|笔记]] |
| 52 | Attention Is All You Need | Vaswani, Shazeer, Parmar, Uszkoreit, Jones, Gomez, K… | 2023 | arXiv preprint (cs.CL) | LLM | [[F:/XWCos/obisidian/xwcall/xwcall/02vault/LLM/Attention Is All You Need\|笔记]] |

## 二、逐篇结构化提取

### 1. A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System

- **作者**：Bin Li, Hongyun Zhang, Yue Rong, Zhu Han
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`HWHQDBSP`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Control-Based Beamforming and Trajectory for UAV-ISAC]]

**研究问题**：如何在 UAV 动力学约束与感知服务需求下，设计波束成形与轨迹以最大化平均加权通信速率？

**方法**：含动力学约束的 3-DoF 与 6-DoF 两类优化问题 + 分解为波束成形与轨迹子问题

**使用模型**：平台：多天线 UAV；任务：对特定区域内的多个目标做雷达感知 + 与多个地面用户通信；动力学模型：3-DoF（三自由度）与 6-DoF（六自由度）两套，分别建模；优化变量：UAV 轨迹、通信波束成形向量、感知波束成形向量

**优点**：笔记未记录

**不足**：笔记未记录

**未来研究方向**：笔记未记录

---

### 2. Curriculum-Guided Heterogeneous Multi-Agent Intelligence for Multi-UAV Cooperative ISAC

- **作者**：Kang Yan, Luping Xiang, Kang Zheng, Jienan Chen, Jun Liu, Qiang Liu, Kun Yang
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`D9Q98G7S`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Curriculum-Guided Heterogeneous Multi-Agent ISAC]]

**研究问题**：如何实现多架无人机与地面基站的异构智能体协同，在通信性能约束下通过联合轨迹—波束成形优化最小化感知的 PCRB？

**方法**：后验克拉美罗界（PCRB）最小化建模 + 课程学习的异构智能体 PPO（C-HAPPO）+ Kronecker/QR 分解降维

**使用模型**：智能体：多架 UAV + 地面基站（BS），构成异构智能体系统；任务：联合目标感知、跟踪与通信；优化目标：最小化 PCRB（后验克拉美罗界，感知性能的贝叶斯下界）；约束：通信性能要求

**优点**：「异构」是关键：UAV 与地面 BS 在能力、观测与动作上本质不同，需专门的多智能体算法。；课程学习 + 矩阵分解降维，是让 MARL 在高维 NP-hard 问题上可用的两个实用杠杆。

**不足**：MARL 的训练样本效率与仿真—现实差距（sim-to-real）未充分讨论。；仿真验证，无实测或硬件在环。；未考虑 UAV 能耗与续航约束。；量化收益需查阅仿真章节。

**未来研究方向**：研究 sim-to-real 迁移与在线自适应。；纳入 UAV 能耗与通信开销约束。；在真实多 UAV 平台上验证。

---

### 3. ISAC Enabled Anti-UAV: Joint Beamforming and Trajectory Design for Multi-UAVs

- **作者**：Xiaojie Wang, Lingfei Li, Zhaolong Ning, Xiaoming Tao, Tie Qiu, Lei Guo, Yan Zhang
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`BMZJYWHN`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Anti-UAV]]

**研究问题**：如何在不依赖地面固定基站的情况下，仅用协同无人机群对持续移动的目标无人机实现灵活感知与可靠定位？

**方法**：空—空传输中断概率约束下推导最优发射功率 + 感知 FIM/CRB 推导 + 长期 CRB 最小化的鲁棒优化

**使用模型**：感知方：协同无人机群（cooperative UAVs），无地面固定基站；目标：非合作/未授权的目标 UAV，位置具有不确定性；链路：空—空（space-air）传输，存在中断概率；优化变量：发射功率、收发波束成形、关联（association）等

**优点**：用「协同无人机」替代「固定基站」是适配移动目标的关键架构选择。；把目标位置不确定性显式纳入 CRB 推导，是相对理想化 CRB 分析的实质改进。

**不足**：仿真验证，无实测或硬件在环。；未考虑无人机自身能耗对长期任务的约束。；目标机动模型较简单时，位置不确定性的建模优势可能被高估。；量化收益需查阅仿真章节。

**未来研究方向**：纳入能耗与续航约束做长期任务规划。；在真实反无人机场景中验证。；研究更强机动目标下的自适应跟踪策略。

---

### 4. Joint Beamforming and UAV Deployment Optimization for ISAC-Enhanced UAV-Assisted VEC

- **作者**：Chunlin Li, Wenhao Wu, Zhihao Zhang, Tianbing Ma, Shaohua Wan
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`WRMKPUJZ`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Joint Beamforming and UAV Deployment for ISAC-VEC]]

**研究问题**：如何在 UAV 能量约束下联合优化部署位置与波束成形，使 ISAC 系统在通信与感知性能之间取得平衡，同时降低能耗？

**方法**：能量约束下的 UAV 部署位置与波束成形联合优化（ISAC 使能的节能部署方法）

**使用模型**：场景：城市临时拥塞 / 热点区域，固定 RSU 服务不足；平台：UAV（可快速部署，提供通信 + 感知）；上层业务：车载边缘计算（VEC）的任务卸载；优化变量：UAV 部署位置、波束成形

**优点**：笔记未记录

**不足**：笔记未记录

**未来研究方向**：笔记未记录

---

### 5. Memory-Enhanced Dynamic Self-Attention Communication Mechanism for Multi-UAV Base Stations Trajectory Planning

- **作者**：Hanxiao Yuan, Yao Shi, Emad Alsusa, Qinyu Zhang, Yiping Duan, Xiaohu You
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`SW4GRDN9`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Memory-Enhanced Dynamic Self-Attention Trajectory Planning]]

**研究问题**：在缺乏先验、感知受限且无法获得集中式训练信息的实际约束下，如何实现多无人机基站的实时、可扩展轨迹规划？

**方法**：Mem-DSACM 轻量 RL 框架（记忆辅助时序推理 + 距离约束去中心化通信 + 动态自注意力）

**使用模型**：主体：多无人机基站（UAV-BSs）；场景：大型临时活动，用户分布动态变化；决策范式：去中心化强化学习；核心组件：

**优点**：「记忆」解决时序信息缺失，「距离约束通信」解决集中式信息不可得——两者结合才有实用价值。；轻量级设计是面向真实机载部署的必要约束，而非可选优化。

**不足**：仿真验证，无实测或真实活动场景验证。；记忆模块的容量与遗忘策略对性能的影响未充分讨论。；未考虑 UAV 能耗与续航对长时间覆盖任务的约束。；量化收益需查阅仿真章节。

**未来研究方向**：在真实大型活动中验证。；研究记忆容量/遗忘机制的自适应设计。；纳入能耗约束做长时间任务规划。

---

### 6. Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource Allocation for Cooperative Communication and Non-Cooperative Localization

- **作者**：Yufeng Zheng, Lixin Li, Wensheng Lin, Wei Liang, Qinghe Du, Zhu Han
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`7GXUGA2S`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Optimal Transport Framework for Low-Altitude ISAC]]

**研究问题**：在低空 ISAC 网络中，如何联合优化小区关联与功率分配，以平衡授权 UAV 的通信服务与非合作 UAV 的定位需求？

**方法**：建立通信速率与感知精度的关系模型 + 小区关联与功率分配联合优化

**使用模型**：基础设施：地面基站（GBS）；UAV 类型：授权 UAV（需通信服务）+ 非合作 UAV（需被定位，用于避撞）；优化变量：小区关联（cell association）、功率分配（power allocation）；目标：系统平均和速率 + 定位 QoS 的加权和

**优点**：把「服务授权 UAV」与「监管非合作 UAV」统一到同一基站的同一资源池中。；显式建模速率—精度关系，使权衡可被优化而非仅被观察。

**不足**：加权和的权重设定缺乏依据（同 [[02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization/双目标 ISAC]] 所批评）。；仿真验证，无实测。；量化收益需查阅仿真章节。

**未来研究方向**：改用双目标建模以避免权重偏置。；在真实低空场景验证。

---

### 7. Predictive Control Over Low-Altitude Wireless Networks: Joint Trajectory Design and Resource Allocation

- **作者**：Haijia Jin, Jun Wu, Weijie Yuan, Ruizhi Ruan, Jiacheng Wang, Dusit Niyato, Dong In Kim, Abbas Jamalipour
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Mobile Computing
- **Zotero Key**：`IE53M953`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Predictive Control Over Low-Altitude Wireless Networks]]

**研究问题**：在低空无线网络中，如何在有限块长传输下联合确定控制策略、发射功率分配与无人机轨迹，以同时保证轨迹跟踪精度与通信可靠性？

**方法**：MPC 轨迹跟踪 + FBL 中断概率闭式表达 + 重构为二次规划（QP）

**使用模型**：平台：低空无线网络（LAWN），由无人机（drone）服务多台移动 AGV；传输：有限块长（FBL）传输；控制：MPC（模型预测控制）；可靠性度量：中断概率（outage probability）

**优点**：FBL 场景下中断概率的闭式表达是把控制—通信联合问题变得可解的关键一步。；把非凸问题重构为 QP，既降低了求解难度，也便于工程实现。

**不足**：仿真验证，无实测或硬件在环。；MPC 的计算负担在大规模 AGV 场景下需进一步评估。；未考虑无人机自身能耗与续航约束。；量化性能需查阅仿真章节。

**未来研究方向**：在真实 AGV + 无人机平台上验证。；纳入无人机能耗与续航约束。；研究多无人机协同服务更大范围 AGV 的扩展。

---

### 8. Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications via Hierarchical Optimal Control

- **作者**：Shangpeng Wang, Ling Chen, Xiatong Hou, Xinyue Wang, Chenyuan Zhang, Haoran Yang, Haijun Zhang, Haixin Sun
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`H8PIYWY4`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications]]

**研究问题**：如何在严格时限与机载能量约束下，对多无人机应急通信网络的轨迹、任务调度与多跳数据中继进行联合优化，并使求解规模可支撑实时部署？

**方法**：双层模型预测控制（战略层 MILP + 轨迹层 NMPC/SCP）

**使用模型**：战略层（Strategic Layer / GMP）：在滚动时域控制（RHC）回路内对原问题线性化，构建覆盖 [τk, τk + TH] 时域的 MILP，负责长期任务与轨迹规划。；轨迹层（Trajectory Layer）：采用非线性模型预测控制（NMPC），内嵌组合式方案，将离散的角色切换与连续的轨迹优化智能解耦。；求解方式：轨迹层通过序列凸规划（SCP）高效求解，产生物理可行的局部最优实时控制动作。

**优点**：双层分解是使大规模优化问题可实时部署的关键（essential），而非单纯的性能优化技巧。；战略层 MILP 负责长期协调，轨迹层 NMPC 负责物理感知的实时控制与动态角色切换，二者通过 RHC 闭环衔接。

**不足**：验证方式为仿真，未在真实无人机平台上做硬件在环或实地飞行实验。；战略层依赖问题线性化，线性化误差对长期计划最优性的影响未做定量分析。；轨迹层经 SCP 求解只能保证局部最优，全局最优性缺失。；论文未在当前全文中集中给出仿真规模参数（无人机数量、任务点规模）与基线方法的具体名称，可复现性细节不足。

**未来研究方向**：引入数据驱动的遮挡预测以替代或增强模型化的 LoS 假设。；探索分布式/去中心化的层次控制，降低对中心节点计算能力的依赖。；扩展到通信—感知一体化（ISAC）场景，联合考虑感知任务与通信任务。

---

### 9. Situation-Aware Hybrid Sensing and Position Control for UAV-Assisted ISAC Systems

- **作者**：Ling Lyu, Qirui Luo, Yanpeng Dai, Nan Cheng, Cailian Chen, Xinping Guan, Xuemin Shen
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`573TSHTV`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Situation-Aware Hybrid Sensing for UAV-ISAC]]

**研究问题**：如何在有限无线资源下，既完成 UAV 的位置感知与数据传输，又降低感知带来的能耗与对通信的干扰？

**方法**：基于信道状态的按需感知激活 + UAV 位置控制

**使用模型**：链路：UAV 中继的厂区设备 ↔ 远程中心视距链路；双功能：位置感知 + 数据传输（ISAC）；感知调度：按需激活（由信道状态触发）；控制变量：UAV 位置

**优点**：感知不必一直开启——按需感知是降低 ISAC 开销的直接有效手段。；信道状态既是感知的触发条件，也是 UAV 位置控制的目标，二者形成闭环。

**不足**：量化收益需查阅仿真章节。；按需感知的判据若估计不准，可能漏掉需要的感知时机。；仿真验证，无实测。；未讨论感知功能开关的时延开销。

**未来研究方向**：研究信道状态估计误差下的鲁棒按需策略。；在真实工业场景验证。；分析感知开关的时延与同步开销。

---

### 10. Cooperative ISAC-Empowered Low-Altitude Economy

- **作者**：Jun Tang, Yiming Yu, Cunhua Pan, Hong Ren, Dongming Wang, Jiangzhou Wang, Xiaohu You
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`8A5WX5RQ`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Cooperative ISAC-Empowered Low-Altitude Economy]]

**研究问题**：在多天线、多目标、多基站的通用场景下，如何完成"单站多维参数估计 → 跨站数据关联 → 多站融合定位测速"的完整协作感知链条？

**方法**：空间平滑张量分解（利用 Vandermonde 结构）+ 降维 GRQ AoA 估计 + 去虚警 MST 数据关联 + Pareto 最优定位 + 残差加权测速

**使用模型**：系统：`J` 个 BS 先从回波估计 UAV 参数，再在云端融合以强化感知性能。；为避免站间干扰，假设各 BS 工作在非重叠频带。；张量符号：标量 `y`、向量 `y`、矩阵 `Y`、张量 `𝒴`；运算符 `◦`（外积）、`⊗`（Kronecker）、`⊙`（Khatri-Rao）。

**优点**：张量分解的自动参数配对特性天然适合多维参数估计，而 Vandermonde 结构可被显式利用实现 off-grid 估计（避免网格失配）。；多站数据关联不应穷举——用 MST 既降复杂度又能剔除虚警，是"图结构 + 感知"的结合。；融合层级应选参数级而非符号级，以牺牲少量精度换取大幅降低的传输与同步开销（这在真实组网中往往更重要）。

**不足**：径向速度略逊于 Benchmark2：因误差累积（径向速度受前序距离估计影响），说明两阶段之间未做联合优化。；非重叠频带假设：为避免站间干扰，各 BS 使用不重叠频带，这在多站密集部署时频谱效率代价显著，与 ISAC 提升频谱效率的初衷存在张力。；全仿真无实测：未使用真实低空信道或实测 UAV 回波数据。；双极化扩展仅初步：文中给出四阶张量建模，但复杂度与收益的定量权衡着墨较少。；云端融合的时延与同步虽被指出低于符号级方案，但未定量分析其对实时跟踪的影响。

**未来研究方向**：联合优化 Stage I 与 Stage II，抑制距离估计误差向径向速度的传递。；研究站间干扰下的重叠频带协作方案（如干扰协调波形）。；在真实低空环境做实测验证，纳入真实信道与 RCS 起伏。；定量分析双极化方案的复杂度—精度权衡。；把通信速率约束引入协作感知的资源分配。

---

### 11. ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network

- **作者**：Yi Wang, Keke Zu, Luping Xiang, Qixun Zhang, Zhiyong Feng, Jie Hu, Kun Yang
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`E6FEI3MH`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC Enabled Cooperative Detection for UAV]]

**研究问题**：如何利用基站的 ISAC 能力，在提供低空 UAV 通信服务的同时实现对其的有效监管与非法入侵自动检测？

**方法**：基站 ISAC 能力 + 电子围栏区域划定 + 利用 UAV 高机动性与强视距链路的协同检测

**使用模型**：基础设施：具备 ISAC 能力的基站（BS）；对象：低空 UAV（含合法的与未上报的「黑飞」UAV）；机制：电子围栏区域划定 + 非法入侵自动检测；协同：利用 UAV 高机动性与强视距链路

**优点**：笔记未记录

**不足**：笔记未记录

**未来研究方向**：笔记未记录

---

### 12. Integrated Sensing, Communication, and Over-The-Air Control of UAV Swarm Dynamics

- **作者**：Zhuangkun Wei, Wenxiu Hu, Yathreb Bouazizi, Chenguang Liu, Yunfei Chen, Hongjian Sun, Julie McCann
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`ARDMTZWB`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC-OTA UAV Swarm Dynamics]]

**研究问题**：如何在同一基站上把空中计算（OTA）控制与感知功能融合，既解决无人机群控制的频谱开销问题，又实现对目标的准确感知？

**方法**：上行 OTA 信号构建 + 两种后处理方法（控制中心 / 感知中心）+ 下行非凸问题求解

**使用模型**：基站：同时承担 OTA 控制信号的构建/下发与目标感知；上行：利用电磁叠加在空中形成控制信号（OTA computation）；下行：向无人机群下发控制信号（非凸优化问题）；对象：无人机群（受控对象）+ 需感知的目标物体

**优点**：OTA 的电磁叠加不仅是通信技巧，也可直接用于「在空中计算」出控制信号，从而绕开逐机带宽分配。；控制与感知可在同一信号上共存，但需通过后处理区分与权衡（控制中心 vs 感知中心）。

**不足**：控制中心法与感知中心法的切换/联合策略未明确（二者如何自适应权衡）。；仿真验证，无实测或硬件在环。；OTA 依赖精确的信道叠加，对同步与信道估计误差敏感。；量化性能需查阅仿真章节。

**未来研究方向**：研究控制与感知的自适应联合权衡机制。；分析同步误差与信道估计误差对 OTA 叠加的鲁棒性影响。；在真实无人机群平台上验证。

---

### 13. Near-Field Integrated Sensing and Communications for Secure UAV Networks

- **作者**：Jingjing Zhao, Songtao Xue, Kaiquan Cai, Xidong Mu, Yuanwei Liu, Yanbo Zhu
- **年份**：2025
- **期刊/会议**：IEEE JSAC
- **Zotero Key**：`SFHWJXB7`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Near-Field Integrated Sensing and Communications for Secure UAV Networks]]

**研究问题**：在 E-UAV 位置与运动模型均未知的条件下，如何实时获得其位置，并据此联合设计 GBS 波束与 C-UAV 轨迹，在保证感知精度的前提下最大化瞬时保密速率？

**方法**：近场 3D 速度感知（ML）+ EKF 轨迹跟踪 + AO 交替优化（SCA + DC 罚函数）联合波束成形与 C-UAV 轨迹

**使用模型**：场景：大孔径 GBS（UPA，M 天线）与 1 个 C-UAV 通信，存在 1 个 E-UAV。；近场回波模型（式 6）：；阵列响应向量按逐天线距离构造（式 3），体现近场球面波特性：；时变相位—多普勒向量（式 5）：`dl,n(f_Dl) = [e^{−j2πf_Dl,1 nTs}, ..., e^{−j2πf_Dl,M nTs}]ᵀ`

**优点**：近场不只是"距离维度"，更提供了空间变化的多普勒，这是能被算法利用的额外观测自由度（Remark 1 是全文的物理支点）。；AN 不必是纯浪费的功率——让它同时承担感知照明与干扰，是 ISAC 思路在安全场景的自然延伸。；感知精度不是一个"越严越好"的指标，而是需要与保密速率共同权衡的设计变量（`Γ` 的作用）。

**不足**：单 C-UAV、单 E-UAV：多用户、多窃听者场景下的波束与轨迹设计未讨论，可扩展性未知。；E-UAV RCS 假设已知：反射系数 `β` 中含雷达截面积 `σRCS`，实际中非协作无人机的 RCS 起伏未知。；全仿真无实测：近场大孔径阵列的校准误差、互耦、近场信道估计误差均未建模。；AN 与信息信号不相关的假设：`(1/N)Σ sl(n)a*_l(n) ≈ 0` 在有限块长下是近似，短包场景可能不成立。；C-UAV CSI 假设已知：近场信道估计本身的开销与误差未计入。

**未来研究方向**：扩展到多 C-UAV / 多 E-UAV 场景，研究波束与多轨迹的联合设计。；研究 RCS 未知或起伏下的鲁棒跟踪与波束设计。；把近场信道估计误差与阵列校准误差纳入鲁棒优化。；设计 `Γ` 的自适应选取策略（按实时保密速率需求动态调整）。；在真实大孔径阵列平台上做近场实测验证。

---

### 14. Radar Probing Optimization for Joint Beamforming and UAV Trajectory Design in UAV-Enabled Integrated Sensing and Communication

- **作者**：Yaxi Liu, Wencan Mao, Boxin He, Wei Huangfu, Tianyao Huang, Haijun Zhang, Keping Long
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`2N5HVUHH`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Radar Probing Optimization for Joint Beamforming and UAV Trajectory]]

**研究问题**：如何在 UAV 大规模 MIMO ISAC 中刻画并优化雷达探测任务的性能，同时兼顾通信需求？

**方法**：雷达探测误差指标（PSM 的 MSE + CCP）+ 半正定松弛 + 通信/感知预编码器联合设计

**使用模型**：平台：UAV 载大规模 MIMO（massive MIMO）；指标：雷达探测误差 = PSM 的 MSE + CCP（两项之和）；任务一方案：同时采用通信预编码器与专用感知预编码器以支持 MIMO 雷达；任务二方案：发射波束成形 + UAV 轨迹联合设计

**优点**：笔记未记录

**不足**：笔记未记录

**未来研究方向**：笔记未记录

---

### 15. UAV-Assisted 5G Networks: Mobility-Aware 3D Trajectory Optimization and Resource Allocation for Dynamic Environments

- **作者**：Asad Mahmood, Thang X. Vu, Wali Ullah Khan, Symeon Chatzinotas, Björn Ottersten
- **年份**：2025
- **期刊/会议**：IEEE VTC2025-Fall
- **Zotero Key**：`B26J2QSX`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory]]

**研究问题**：在用户移动的 UAV 辅助无线网络中，如何结合 3D 轨迹优化与移动性预测，在保证计算可承受的前提下最大化最小用户速率？

**方法**：稀疏二阶预测模型 + 启发式用户分簇 + SCA 迭代求解分解后的子问题

**使用模型**：UAV：可优化 3D 轨迹的空中基站；用户：具有移动性，需实时跟踪预测；优化变量：用户关联、3D 轨迹、资源分配；目标：max-min rate（最大化最小速率）

**优点**：稀疏二阶预测 + 启发式分簇是在预测精度与计算开销之间的务实折中。；三子问题分解 + SCA 使原本难以实时求解的联合问题具备可实施性。

**不足**：二阶预测模型对用户突变运动（急转、加减速）适应性有限。；启发式分簇缺乏理论最优性保证。；SCA 只保证局部最优。；仿真验证，无实测；会议论文篇幅有限。

**未来研究方向**：引入学习式运动预测提升突变场景适应性。；给出分簇策略的理论性能界。；在真实 UAV 平台上验证。

---

### 16. UAV-Enabled Passive 6D Movable Antenna for ISAC: Joint Location, Orientation, and Reflection Optimization

- **作者**：Peilan Wang, Yu Xue, Weidong Mei, Jun Fang, Rui Zhang
- **年份**：2025
- **期刊/会议**：IEEE Wireless Communications Letters
- **Zotero Key**：`CGHQUH7E`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/UAV-Enabled Passive 6D Movable Antenna for ISAC]]

**研究问题**：如何利用无人机载 IRS 的六维机动性，联合优化基站发射波束成形、IRS 的 3D 位置/朝向/反射系数，在保障通信 SNR 下限的同时最大化感知 SNR？

**方法**：两阶段方法（先优化 IRS 的 6D 参数与反射系数以增强信道相关性，再闭式求解发射波束成形）

**使用模型**：ISAC 基站（BS）：发射双功能信号。；UAV 载 IRS：具备 3D 位置、3D 朝向与反射系数三类可调参数。；感知目标：单个目标，最大化其回波 SNR。；通信用户（UE）：保证最低 SNR 约束。

**优点**：把 IRS 的调控维度从「反射系数」扩展到「3D 位置 + 3D 朝向 + 反射系数」的六维空间，是突破固定 IRS 自由度瓶颈的关键。；信道子空间旋转与扩展是 IRS 同时增强 S&C 性能的机理所在。

**不足**：仅考虑单目标感知，未覆盖多目标。；仿真验证，无实测或硬件平台验证。；UAV 的能量消耗与飞行约束（续航、禁飞区）未纳入优化。；IRS 相移的离散量化误差、UAV 抖动对朝向的影响未建模。

**未来研究方向**：扩展到多目标感知与多用户通信。；纳入 UAV 能耗与轨迹约束做联合优化。；考虑 IRS 离散相移与 UAV 姿态抖动的实际工程约束。

---

### 17. ISAC from the Sky: UAV Trajectory Design for Joint Communication and Target Localization

- **作者**：Xiaoye Jing, Fan Liu, Christos Masouros, Yong Zeng
- **年份**：2022
- **期刊/会议**：IEEE Journal on Selected Areas in Communications
- **Zotero Key**：`BFPD3VN4`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/ISAC from the Sky UAV Trajectory Design]]

**研究问题**：在机载 ISAC 场景中，如何联合设计无人机轨迹与用户带宽分配，在机载能量约束下实现通信性能与感知性能的灵活权衡？

**方法**：加权和归一化优化 + 多阶段轨迹设计（MSTD）+ 迭代算法

**使用模型**：UAV 角色：同时作为通信基站（向用户发射信号）与雷达（利用回波定位目标）。；优化变量：UAV 轨迹 + 用户带宽分配。；约束：机载能量供给。；通信指标：总传输数据量（total transmitted data）。

**优点**：首次（在该设定下）把能量供给显式纳入 UAV-ISAC 轨迹设计约束。；MSTD 提升了轨迹离散化建模精度，优于单阶段建模。

**不足**：迭代算法只能保证局部最优，无全局最优性保证。；验证为数值仿真，无实测或硬件验证。；加权系数需人工设定，论文未给出自适应调参策略。；能量模型为简化约束，未涉及更复杂的能耗动力学。

**未来研究方向**：引入全局优化或学习式方法改善局部最优问题。；扩展到多 UAV 协同 ISAC 场景。；联合优化波束赋形与轨迹（本文只做轨迹 + 带宽）。

---

### 18. Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area

- **作者**：Wahab Khawaja, Ozgur Ozdemir, Fatih Erden, Ismail Guvenc, David W. Matolak
- **年份**：2020
- **期刊/会议**：IEEE Transactions on Aerospace and Electronic Systems
- **Zotero Key**：`UCRR3CP7`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area]]

**研究问题**：如何在开阔区域对无人机空地 UWB 信道进行系统实测，并给出可用于系统设计的统计信道模型与解析路径损耗模型？

**方法**：UWB 实测 + 射线追踪仿真 + Saleh-Valenzuela 统计拟合

**使用模型**：频段：3.1–4.8 GHz（UWB）；传播场景：无遮挡悬停、植被遮挡（foliage obstruction）、定高圆周运动；几何参数：3 个 UAV 高度 × 2 个水平距离；天线朝向：UAV 发射端 2 种朝向

**优点**：首次系统给出同时覆盖三类场景、多种高度/距离/天线朝向的 UWB 空地实测结果。；把天线在仰角面的增益显式纳入解析路径损耗模型，比传统仅依赖距离的路径损耗指数模型更贴合 UAV 几何。

**不足**：场景限于开阔场地，未覆盖城市、郊区等更复杂散射环境。；频段限于 3.1–4.8 GHz，未涉及更高频段（如毫米波）。；圆周运动场景为定高匀速，未覆盖更激进的机动轨迹。；实测与射线追踪的偏差说明模型对真实散射体的刻画仍不完整。

**未来研究方向**：扩展到城市/郊区多场景与更高频段测量。；引入更丰富的机动轨迹与动态信道追踪。；把实测统计模型接入系统级仿真与 ISAC 波形设计。

---

### 19. Channel Knowledge Map Enabled Low-Altitude ISAC Networks: Joint Air Corridor Planning and Base Station Deployment

- **作者**：Jiaxuan Li, Yilong Chen, Fan Liu, Jie Xu
- **年份**：2026
- **期刊/会议**：IEEE Wireless Communications Letters
- **Zotero Key**：`JUTU2WE6`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Channel Knowledge Map Low-Altitude ISAC]]

**研究问题**：如何在低空 ISAC 网络中联合规划空中走廊与基站部署，在满足全程感知与通信覆盖约束下最小化系统成本？

**方法**：信道知识地图表征 + 分层由粗到细网格分解算法求解大规模非凸整数规划

**使用模型**：空中走廊：由连接的立方段构成的结构化航路；基站：在候选位置集合中选择性部署；覆盖要求：走廊全程需同时满足感知与通信性能约束；信道表征：CKM（信道知识地图）

**优点**：CKM 把「先建后测」转变为「先刻画后规划」，是低空网络规划范式上的实用改进。；分层由粗到细的网格分解是应对大规模整数规划的可行工程路径。

**不足**：Letter 篇幅，算法收敛性与最优性分析可能不足。；CKM 本身的构建成本与精度依赖未在本文充分讨论。；仿真验证，无实测。；未考虑基站部署后的动态环境变化（如新建遮挡）。

**未来研究方向**：研究 CKM 构建成本与规划收益的权衡。；扩展到动态/时变环境下的在线重规划。；在真实低空场景做实测验证。

---

### 20. ISAC-Enabled Beam Tracking for U2U Communication Systems Under Jittering Effects

- **作者**：Wei Liu, Yuhang Tang, Jinkun Zhu, Peng Yang
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`2IA69RXU`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC-Enabled Beam Tracking for U2U]]

**研究问题**：如何在无人机平台抖动导致波束失准的情况下，利用 ISAC 感知能力提升角度预测精度并补偿抖动，从而最大化 U2U 通信可达速率？

**方法**：感知回波辅助的角度跟踪 + 抖动补偿算法（自适应波束宽度控制 + 波束指向精化）

**使用模型**：UAV-B：系留无人机基站（tethered），具备 ISAC 能力（发射通信信号并用回波感知）；UAV-U：机动无人机用户（maneuvering）；损伤因素：平台抖动（jitter）；待估量：UAV-B 与 UAV-U 之间的相对角度

**优点**：感知回波是「免费」的运动信息来源，无需额外导频开销——这是 ISAC 在波束管理上的直接价值体现。；抖动补偿需两端协同：基站调宽度（保证不掉链）、用户调指向（保证增益）。

**不足**：仿真验证，无实测或硬件在环。；先验运动模型与实际机动的匹配程度会影响预测精度。；未考虑多用户场景下的波束资源竞争。；量化收益需查阅仿真章节。

**未来研究方向**：在真实无人机平台上验证抖动特性与补偿效果。；研究模型失配时的鲁棒/自适应预测。；扩展到多 UAV-U 的波束调度。

---

### 21. LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in Near-Field ISAC Systems

- **作者**：Hongjia Huang, Weijie Yuan, Chang Liu, Liang Liu, Fan Liu, Wei Xiang, Derrick Wing Kwan Ng
- **年份**：2026
- **期刊/会议**：IEEE Journal on Selected Areas in Communications
- **Zotero Key**：`YLGH28E2`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/LLM in V2I Predictive Beamforming]]

**研究问题**：在近场 V2I 系统中，如何利用历史 CSI 设计预测波束成形，以在同时考虑距离与角度维度的条件下准确跟踪车辆？

**方法**：基于 LLM 的神经网络（LNN）+ 历史 CSI 序列预测 + 角度与距离 CRB 及可达和速率分析

**使用模型**：场景：近场 ISAC 车联网（V2I），基站跟踪车辆；双维度：距离（range）+ 角度（angle），需联合设计波形；输入：历史 CSI 序列；输出：未来的波束成形决策

**优点**：近场的距离维度是相对远场的本质区别，必须纳入波形与波束设计。；LLM 类网络的时序建模能力适合挖掘历史 CSI 的长程依赖，是预测波束的天然选择。

**不足**：LLM 类网络的推理开销较大，实时性需评估（物理层对时延敏感）。；量化收益需查阅仿真章节。；仿真验证，无实测数据。；历史 CSI 的长度与预测视野的权衡未详细说明。

**未来研究方向**：研究轻量化 LNN 以满足物理层时延约束。；在真实 V2I 场景验证。；分析历史窗口长度与预测精度的关系。

---

### 22. Integrated Sensing and Communications in Multi-UAV Networks: A Dual-Objective Optimization Perspective

- **作者**：(PDF 首页作者行未在当前全文提取中定位)
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`EW3FZDE2`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Multi-UAV ISAC Dual-Objective Optimization]]

**研究问题**：在用户与目标相互独立、且存在机间干扰的通用多无人机网络中，如何通过双目标优化获得更好的 ISAC 权衡，同时联合确定轨迹、用户关联、目标关联与功率控制？

**方法**：双目标建模 + 无人机间干扰管理 + 轨迹/用户关联/目标关联/功率控制联合优化

**使用模型**：网络：多无人机（multi-UAV）；用户：多个独立通信用户（下行）；目标：多个独立感知目标；干扰：无人机之间存在复杂干扰，需管理

**优点**：「用户与目标独立」是比「单目标/重叠」更通用也更真实的设定。；加权和的本质缺陷是权重人为设定会引入偏置，双目标模型可避免这一点。

**不足**：论文作者行未在当前文本提取中定位，元数据完整性有缺口。；仿真验证，无实测。；双目标模型的求解复杂度需评估（尤其大规模网络）。；量化收益需查阅仿真章节。

**未来研究方向**：给出双目标求解的计算复杂度分析。；与精心调参的加权和方法做公平对比。；扩展到时变场景与在线求解。

---

### 23. Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Balancing

- **作者**：Tianyu Fang, Mengyuan Ma, Markku Juntti, Nir Shlezinger, A. Lee Swindlehurst, Nhan Thanh Nguyen
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Signal Processing
- **Zotero Key**：`4IPDFAZ4`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Optimal ISAC Beamforming Structure]]

**研究问题**：如何在 ISAC 双功能波束成形中，既保证收敛到局部最优，又揭示最优波束成形器的结构以降低大规模场景下的计算复杂度？

**方法**：SCA 序列凸近似 + 拉格朗日对偶推导最优波束结构（OBS）+ 低维重构

**使用模型**：场景：单站（monostatic）ISAC 系统，同时服务多用户通信与多目标探测。；感知度量：通用 CRLB 指标，可估计目标相对基站的方位角、俯仰角以及复雷达截面积。；通信度量：和速率（sum rate, SR）。；优化变量：波束成形矩阵（含通信与感知流）。

**优点**：识别并利用问题的最优波束结构（OBS），是降低大规模 ISAC 网络复杂度的有前景路径。；本文方案能识别 CRLB 波束成形优化的 OBS，因此可为 ISAC 系统中的 CRLB 优化提供灵活且低复杂度的解法。

**不足**：SCA 只能保证局部最优，无全局最优性保证。；单站（monostatic）配置，未覆盖双站/多站 ISAC。；仿真验证为主，无硬件实测。；结构结论依赖具体的信道与阵列模型假设。

**未来研究方向**：推广到双站/多站与分布式 ISAC 架构。；结合学习式初始化改善 SCA 的局部最优问题。；在 UAV 等移动平台上验证（含移动性带来的时变信道）。

---

### 24. A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Near-Field and Far-Field Scenarios

- **作者**：Yirui Luo, Yong Liang Guan, Yao Ge, David González G., Chau Yuen
- **年份**：2025
- **期刊/会议**：IEEE Internet of Things Journal
- **Zotero Key**：`2UM9X5FB`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation]]

**研究问题**：在近场与远场目标共存且存在分数时延/多普勒的 AFDM-ISAC 系统中，如何实现保证唯一性且低复杂度的角度-时延-多普勒联合估计？

**方法**：三阶张量建模 + 结构化 CP 分解 + 空间平滑 + 低复杂度估计

**使用模型**：波形：AFDM（多啁啾，仿射频分复用）；张量模型：三阶张量，具有低秩 CP 格式；目标场景：近场（NF）与远场（FF）混合共存；待估参数：角度（angle）、时延（delay）、多普勒（Doppler）

**优点**：利用 CP 因子矩阵的 Vandermonde 结构是把「结构信息」转化为「唯一性保证」的关键。；空间平滑可解决相干信号导致的分解退化问题。

**不足**：量化性能需查阅仿真章节，摘要未给具体数值。；仿真验证，无实测数据。；张量构造与空间平滑会牺牲部分孔径/孔径效率。；未与 OTFS 等同类波形在同一设定下做充分对比。

**未来研究方向**：在实测或半实物平台上验证。；与 OTFS-ISAC 在同一 NF/FF 混合设定下对比。；研究更低复杂度的在线实现（面向实时感知）。

---

### 25. Communication-Control Codesign for Large-Scale Wireless Networked Control Systems

- **作者**：Gaoyang Pang, Wanchun Liu, Dusit Niyato, Branka Vucetic, Yonghui Li
- **年份**：2025
- **期刊/会议**：IEEE JSAC
- **Zotero Key**：`CPAWPDHD`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Communication-Control Codesign for Large-Scale Wireless Networked Control Systems]]

**研究问题**：如何在大规模多回路 WNCS 中，联合优化信道调度（哪些设备占用哪些信道）与控制输入（发给执行器的连续控制信号），以最小化长期折扣控制代价？

**方法**：多回路 WNCS 建模 + MDP 形式化 + GCA-DRL（级联双分支 actor + 知识辅助图动作嵌入，基于 TD3）

**使用模型**：组成：一个智能边缘控制器 + `M` 个空间分布传感器 + `N` 个执行器，共享 `L` 个无线频率信道（`1 ≤ L ≤ N + M`）。；被控对象为线性离散时间系统：；`Λ(t)`、`Ψ(t)` 为二进制对角矩阵，分别表示控制/感知包的传输成功与否（丢包建模）。；每个状态维度不稳定（`ρk(A) > 1`），无控制输入时状态无界增长。

**优点**：通信与控制策略是相关的，必须让二者在网络结构层面显式耦合——这就是"级联"（cascaded）的意义：调度输出直接喂给控制分支。；混合动作空间的规模可通过把离散问题嵌入连续空间（MBGM 权重）来规避，而不是硬探索。；跨域变量（CSI 量级 10⁻¹⁰ 与控制量级相差巨大）必须用 LayerNorm 拉齐，否则训练被单一域主导。

**不足**：全仿真无实测：系统矩阵 `A, B, C` 随机生成，未使用真实工业被控对象模型或实测信道数据。；CSI 假设偏理想：假设控制器通过标准信道估计获得准确 CSI，但未考虑信道估计误差与反馈开销；大规模下 CSI 获取本身即负担。；可扩展性的上限未探明：表 III 给出若干规模组合，但当设备数远大于信道数（`M + N >> L`）时的性能退化未定量分析。；MBGM 为一对一匹配：约束式 4 要求每设备最多一信道、每信道最多一设备，未支持一设备多信道聚合或 NOMA 类共享。；未见与"感知（sensing）"功能的联合——本文的 sensing 指传感器测量上报，与 ISAC 中的雷达感知不是同一概念，跨界读者需注意术语差异。

**未来研究方向**：在真实工业 WNCS 测试床或硬件在环平台验证。；放宽一对一匹配约束，研究多信道聚合与非正交接入下的协同设计。；引入信道估计误差与 CSI 反馈开销，分析其对控制代价的影响。；把本文的"通信—控制"协同扩展到"通信—感知—控制"三方协同。

---

### 26. Deep Unfolding Learning Aided ISAC Transceiver Design

- **作者**：Jifa Zhang, Yongxu Zhu, Nan Zhao, Shi Jin, Xianbin Wang, Derrick Wing Kwan Ng, Naofal Al-Dhahir
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`ZE5HNQHG`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Deep Unfolding ISAC Transceiver Design]]

**研究问题**：如何在杂波环境下低复杂度地联合设计 ISAC 的发射波形与接收滤波，同时满足恒模与波形相似度约束？

**方法**：ADMM 迭代算法 → 深度展开为网络层；联合优化发射波形与接收滤波

**使用模型**：环境：杂波环境（存在 clutter）；优化变量：发射波形、接收滤波；目标项：多用户干扰功率 + 感知 SINR 的倒数（加权和）；约束：恒模信号、波形相似度

**优点**：深度展开兼具优化的可解释性与学习的低复杂度，是二者的折中之道。；把感知 SINR 的倒数放入目标，等价于直接压低感知性能的劣化（而非最大化 SINR 本身）。

**不足**：量化收益需查阅仿真章节。；展开层数需权衡（层数少则性能差，多则复杂度回升）。；仿真验证，无实测。；训练后的网络在分布外场景的泛化需验证。

**未来研究方向**：研究展开层数与性能的帕累托关系。；在真实 ISAC 平台上验证。

---

### 27. Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-Driven DRL

- **作者**：Chen Shang, Jiadong Yu, Dinh Thai Hoang
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`LH73Q4RG`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Energy-Efficient and Intelligent ISAC in V2X Networks]]

**研究问题**：如何在降低神经网络能耗的同时，让 RSU 仅凭当前感知信息即可制定 ISAC 波束成形与功率分配方案，摆脱对大量导频与完整 CSI 的依赖？

**方法**：马尔可夫决策过程建模 + 脉冲神经网络驱动 DRL（SNN-DRL）+ 波束成形与功率联合优化

**使用模型**：决策主体：路侧单元（RSU）。；状态来源：仅依赖当前感知信息（sensing information），不需完整 CSI。；优化变量：波束成形 + 功率分配（联合优化）。；能耗考量：用脉冲神经网络（SNN）替代常规神经网络以降低能耗。

**优点**：把 SNN 的低能耗特性引入 ISAC-DRL，是针对「AI 能耗」这一实际部署瓶颈的针对性设计。；感知信息直接作为决策状态，绕开 CSI 获取开销，是系统层面的实用化改进。

**不足**：仅凭当前感知信息决策，牺牲了部分 CSI 精度，在快时变信道下可能性能受限。；SNN 训练方法（如 surrogate gradient）本身存在近似误差。；论文仿真验证，缺少真实 V2X 路测。；具体能耗与性能权衡的定量结论需查阅全文实验章节。

**未来研究方向**：在真实 V2X 平台或硬件在环环境验证 SNN 能耗收益。；研究 SNN 与常规 ANN 在不同业务负载下的切换策略。；把该低能耗决策框架迁移到 UAV 等 airborne ISAC 平台。

---

### 28. Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement Learning Approach

- **作者**：Xiaowen Ye, Yuyi Mao, Xianghao Yu, Shu Sun, Liqun Fu, Jie Xu
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`4ZKUQ3NN`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC for Low-Altitude Economy DRL]]

**研究问题**：在低空经济场景中，如何联合优化地面基站波束成形与无人机轨迹，在感知 SNR、飞行任务、避撞与发射功率约束下最大化给定时段内的期望通信和速率？

**方法**：建模为 episode task 型 MDP + 深度强化学习方案 DeepLSC

**使用模型**：GBS：为授权 UAV 提供通信与导航服务，并感知低空空域。；授权 UAV：执行给定飞行任务。；非授权移动目标：需被感知/监视的对象。；优化变量：GBS 波束成形 + UAV 轨迹

**优点**：「给定飞行任务」使决策有明确终止，构成 episode task——这一结构性洞察是套用 DRL 的关键。；把通信服务与空域监视统一在同一 ISAC 框架下，是低空经济场景的实质需求。

**不足**：DRL 方案的训练样本效率与收敛性依赖环境设计。；仿真验证，无实测或硬件在环。；未考虑 UAV 间通信干扰或更大规模集群场景。；具体量化增益需查阅仿真章节。

**未来研究方向**：扩展到多 UAV、多 GBS 协同场景。；考虑 UAV 能耗与续航约束。；在真实低空场景做实测验证。

---

### 29. Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative ISAC in AAV Detection

- **作者**：Ruotong Li, Qixun Zhang, Dingyou Ma, Kan Yu, Yuzhen Huang
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Vehicular Technology
- **Zotero Key**：`PVQ768TG`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Joint Target Assignment and Resource Allocation (Fairness)]]

**研究问题**：在高速 AAV 引发多普勒与波动干扰的协作 ISAC 网络中，如何通过目标指派与资源分配保障各链路的检测性能（尤其最弱链路）？

**方法**：最大化最小雷达感知 SINR（max-min fairness）的目标指派与资源分配联合优化

**使用模型**：网络：多个分布式感知节点协作（networked ISAC）；目标：快速移动的自主飞行器（AAVs）；损伤：多普勒频移 + 波动干扰；优化变量：目标指派（target assignment）+ 资源分配

**优点**：检测可靠性由最弱链路决定（短板效应），故公平性比总和最大化更重要。；动态干扰必须与时变性（多普勒）一起建模，静态方案无效。

**不足**：量化收益需查阅仿真章节。；max-min 准则可能牺牲系统整体吞吐（公平性与效率的经典权衡）。；仿真验证，无实测。

**未来研究方向**：研究公平性与效率的折中（如 α-fairness）。；在真实网络化 ISAC 平台上验证。

---

### 30. Learning to Beamform for Integrated Sensing and Communication: A Graph Neural Network With Implicit Projection Approach

- **作者**：Yifei Zhao, Yong Zhou, Zixin Wang, Yuanming Shi, Nan Cheng, Haibo Zhou
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`I6IKDDQA`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Learning to Beamform for ISAC (GNN)]]

**研究问题**：如何在通信性能约束下，设计出既高效、可扩展、又能保证解的可行性的 ISAC 波束成形算法？

**方法**：带隐式层的图神经网络（GNN），在通信性能约束下优化雷达发射波束方向图

**使用模型**：图建模：把 ISAC 网络建模为图（节点为用户/目标/天线等，边为信道或干扰关系），使 GNN 可处理规模变化；网络结构：GNN + 隐式层（用于保证约束/可行性）；优化目标：雷达发射波束方向图；约束：通信性能

**优点**：隐式层是把「可行性」嵌入学习型方法的关键——这是传统学习类算法的主要短板。；图建模使算法天然具备处理规模变化的能力（可扩展性）。

**不足**：量化收益需查阅仿真章节。；GNN 需训练数据，跨场景泛化能力需验证。；隐式层会带来额外的前向计算开销。；仿真验证，无实测。

**未来研究方向**：验证跨场景泛化与在线自适应。；分析隐式层的计算开销与收益权衡。；在真实 ISAC 平台上验证。

---

### 31. SeCo4: Co-Design of Sensing, Communication, and Computing for Intelligent Control in Industrial Cyber-Physical Systems

- **作者**：Qinqin Tang, Yutian Yang, Jiayi Cui, Renchao Xie, Tao Huang, Tianjiao Chen, Ran Zhang, Zehui Xiong
- **年份**：2025
- **期刊/会议**：IEEE Journal on Selected Areas in Communications
- **Zotero Key**：`RFIP7ECI`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/SeCo4 Co-Design of Sensing Communication and Computing]]

**研究问题**：如何通过感知、通信与计算的协同设计，克服工业 CPS 中采样刚性、通信僵化、云雾协同不足与感通算割裂四类挑战？

**方法**：SeCo4 协同设计框架（应对刚性采样、通信配置僵化、云雾协同不足、感通算割裂四类挑战）

**使用模型**：感知侧：可自适应的传感器采样；通信侧：灵活可配置的通信；计算侧：云与雾资源的协同调度；一体化：三者联合设计与优化

**优点**：仅做感知与通信的一体化（ISAC）不足以支撑工业 CPS，必须把计算也纳入统一设计。；采样、通信配置、云雾协同是工业场景特有的三个瓶颈。

**不足**：量化收益需查阅评估章节。；框架层面的工作，具体算法细节需看全文。；与 UAV/移动通信场景的关联较弱。

**未来研究方向**：给出可复现的量化评估与对比。；探索该框架在 UAV 辅助工业物联网中的适用性。

---

### 32. Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using Meta Deep Reinforcement Learning

- **作者**：Armin Farhadi, Ali Olfat, Christos Masouros
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`M4EVSKTU`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/STAR-IRS SCMA ISAC Beamforming (THz)]]

**研究问题**：在太赫兹频段下，如何在 ISAC、SCMA、波束成形、QoS 与 STAR-IRS 五类约束下求解 NP-hard 的波束成形与资源分配联合优化问题，并使解具备跨情境适应能力？

**方法**：元深度强化学习（MDRL）求解 NP-hard 联合优化问题，并具备适应不同情境的能力

**使用模型**：频段：太赫兹（THz）；关键技术：STAR-IRS + SCMA + ISAC；优化变量：波束成形、资源分配；约束：ISAC、SCMA、波束成形、QoS、STAR-IRS

**优点**：STAR-IRS + SCMA + ISAC + THz 的组合面向未来高容量感知通信需求，是前瞻性的场景设定。；元学习（meta-learning）解决了普通 DRL 跨情境泛化不足的问题。

**不足**：量化收益需查阅仿真章节。；仿真验证，无实测。；THz 频段的实际信道损伤（如分子吸收）需更细致建模。

**未来研究方向**：在真实 THz 平台上验证。；细化 THz 信道模型。

---

### 33. Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UAV Networks

- **作者**：(PDF 首页作者行未在当前全文提取中定位)
- **年份**：2024
- **期刊/会议**：IEEE GLOBECOM Workshops
- **Zotero Key**：`9BZPEPMP`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/Resource Allocation Based on Optimal Transport ISAC Multi-UAV]]

**研究问题**：在多无人机 ISAC 协同网络中，如何联合优化小区关联、通信功率与感知功率分配，以最大化系统平均和速率与定位 QoS 的加权和？

**方法**：基于最优传输理论的交替迭代算法（AIBOT）

**使用模型**：网络：ISAC 使能的多无人机（multi-UAV）协同网络；通信侧：协作通信（cooperative communication）；感知侧：非协作定位（non-cooperative localization）；优化变量：小区关联（cell association）、通信功率分配、感知功率分配

**优点**：把最优传输理论引入 ISAC 资源分配中的关联子问题，是求解混合整数非凸结构的有效路径。

**不足**：会议短文，方法收敛性与复杂度分析可能不够充分。；基准算法未具名，对比的公平性难以评估。；仿真验证，无实测。；论文作者行与部分实验参数未在当前材料中提取到。

**未来研究方向**：扩展为期刊长文，补充收敛性与复杂度分析。；与具名 SOTA 算法做更充分对比。；在真实 UAV 平台上验证。

---

### 34. An AFDM-Based Integrated Sensing and Communications

- **作者**：Yuanhan Ni, Zulin Wang, Peng Yuan, Qin Huang
- **年份**：2022
- **期刊/会议**：ISWCS 2022
- **Zotero Key**：`IVFQQXLZ`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/An AFDM-Based Integrated Sensing and Communications]]

**研究问题**：如何让一体化波形在大 Doppler 频移下仍能可靠估计目标的距离与速度，同时不牺牲通信功能？

**方法**：AFDM 波形 + 两种参数估计（时域 FCCR / DAFT 域）+ 整数与分数多普勒合并

**使用模型**：单站感知：接收目标回波，目标 i 的散射系数、距离、相对速度、时延、多普勒频率分别记为 `hi, Ri, v_rel,i, τi = 2Ri/c, fd,i = 2*v_rel,i*fc/c`。；时域回波：；对每列做 N 点 DAFT 得到 DAFT 域样本矩阵 `Yr`，并写成矩阵形式输入-输出关系：；整数归一化多普勒（`a_i = 0`）时，`H_i` 每行仅一个非零元素，位于 `q = (p + loc_i)_N`，其中 `loc_i = (2Nc1*l_i − α_i)_N`；分数多普勒时每行有 `2k_v+1` 个非零元素，峰值位

**优点**：AFDM 在 DAFT 域复用符号，天然具备在双选择性信道中获得全分集的能力，这使其优于 OFDM 与 OCDM。；把"整数+分数多普勒分离估计再合并"作为扩展无模糊范围的手段，是本方法的关键技巧。

**不足**：低多普勒高 SNR 区优势不明显：图 4 显示 `fd = 0.1Δf` 时符号除法在高 SNR 区反而输出更高图像 SNR，本文两种方法在 ~10 dB 后出现饱和。；通信与感知未联合优化：论文聚焦感知参数估计，通信侧直接沿用既有 AFDM 信道估计/均衡方法，未分析感知占空比对通信速率的实际影响。；全仿真，无实测：所有结论基于蒙特卡洛仿真与点目标模型。；分数多普勒为近似处理：DAFT 域方法由整数多普勒情形推导，分数情形仅靠数值验证，无理论误差界。；会议短文，系统模型为单站单天线，未涉及多天线/多目标分辨极限。

**未来研究方向**：在低多普勒区设计方法切换/融合策略，兼顾两种场景。；给出分数多普勒下的估计误差理论界。；联合通信速率与感知精度的波形参数优化。；扩展到多天线 AFDM-ISAC 与实测验证。

---

### 35. Integrated Sensing and Communications: Toward Dual-Functional Wireless Networks for 6G and Beyond

- **作者**：Fan Liu, Yuanhao Cui, Christos Masouros, Jie Xu, Tony Xiao Han, Yonina C. Eldar, Stefano Buzzi
- **年份**：2022
- **期刊/会议**：IEEE Journal on Selected Areas in Communications
- **Zotero Key**：`M92ZFKEN`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)]]

**研究问题**：如何系统梳理 ISAC 的全景——背景与历史脉络、关键应用与 SOTA 方法、从信息论到跨层的多重权衡、波形与接收处理技术，并指明未来方向？

**方法**：综述（历史脉络 + 信息论极限 + 物理层权衡 + 跨层设计 + 信号处理）

**使用模型**：层次一：历史与背景——S&C 的交织演进；层次二：应用与标准化——用例、产业进展、标准活动；层次三：性能权衡——信息论极限 / 物理层 / 跨层；层次四：信号处理——波形设计 / 接收处理

**优点**：把感知作为 6G RAN 的原生特性，并利用 5G 密集小区基础设施构建感知网络，是 ISAC 的核心机遇。；三重权衡（信息论 / 物理层 / 跨层）是理解 ISAC 设计空间的骨架。

**不足**：作为 2022 年的综述，未覆盖此后（2023+）的快速进展（如近场 ISAC、AI 原生 ISAC）。；综述性质决定了技术细节的深度有限，具体实现需查原始文献。；对标准化活动的描述随标准演进而变化。

**未来研究方向**：结合 2023 年后的新进展（近场通信、可重构天线、AI 驱动 ISAC）做补充阅读。；按自己的研究方向（如 UAV-ISAC）深入查阅对应章节引用的原始工作。

---

### 36. NOMA Empowered Integrated Sensing and Communication (RIS-Assisted)

- **作者**：Zhaolin Wang, Yuanwei Liu, Xidong Mu, Zhiguo Ding, Octavia A. Dobre
- **年份**：2022
- **期刊/会议**：IEEE GLOBECOM Workshops
- **Zotero Key**：`W6BEE4ZE`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/ISAC/NOMA Empowered ISAC with RIS]]

**研究问题**：如何在 RIS 辅助的 NOMA-ISAC 网络中，通过联合优化主动波束成形、功率分配系数与被动波束成形，最大化最小雷达波束方向图增益？

**方法**：交替优化 + SCA + 序列秩一约束松弛（SRCR）联合优化主动/被动波束成形与功率分配

**使用模型**：网络：NOMA 赋能的 ISAC 网络；增强手段：RIS（被动波束成形）；优化变量：；主动波束成形（active beamforming，基站侧）

**优点**：把 NOMA 的功率域复用引入 ISAC 感知侧，可在不额外占用时频资源的前提下提升雷达波束增益。；SRCR 是处理被动波束成形秩一约束的有效工程手段。

**不足**：会议短文，篇幅有限，收敛性与复杂度分析可能不足。；仿真验证，无实测。；未给出相对于无 RIS 情形的增益，基线对比不够完整。；具体增益数值需查阅全文。

**未来研究方向**：扩展为期刊长文，补充理论分析与更完整基线。；在真实 RIS 硬件上验证。；研究离散相移与信道估计误差的影响。

---

### 37. Fast and Robust Channel Estimation for HMIMO: A Graph-Based Wavenumber-Domain Approach

- **作者**：Xufeng Guo, Yuanbin Chen, Ying Wang, Zhaocheng Wang, Zhu Han
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`LJ675F7Y`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/HMIMO Graph-Based Wavenumber-Domain Channel Estimation]]

**研究问题**：如何为 HMIMO 信道估计构建不依赖天线密度的表示基，并在该基下实现鲁棒且快速的稀疏恢复？

**方法**：傅里叶谐波正交基构建波数域 + 椭圆马尔可夫随机场建模簇稀疏 + 图割交换扩张（GCSE）算法

**使用模型**：表示基：波数域基（正交傅里叶谐波 FHs），与天线密度无关；问题重构：信道估计 → 稀疏恢复；结构先验：簇稀疏，用椭圆马尔可夫随机场（EMRF）建模；求解算法：图割交换扩张（GCSE），图论优化

**优点**：波数域（而非角度域）是 HMIMO 更合适的表示域，因为它不依赖天线密度。；把图论优化（graph-cut）引入稀疏恢复求解，是降低复杂度的有效路径。

**不足**：仿真验证，无实测数据。；EMRF 的椭圆假设在复杂散射环境下可能不成立。；GCSE 的收敛性证明与复杂度阶数需查阅全文。；与最新深度学习方法的对比未涉及。

**未来研究方向**：在实测 HMIMO 平台上验证。；研究非椭圆簇结构的建模。；与数据驱动方法做对比。

---

### 38. SSNet: Flexible and Robust Channel Extrapolation for Fluid Antenna Systems Enabled by a Self-Supervised Learning Framework

- **作者**：Yuan Gao, Yiming Liu, Runze Yu, Shengli Liu, Yanliang Jin, Shunqing Zhang, Shugong Xu, Xiaoli Chu
- **年份**：2025
- **期刊/会议**：IEEE Journal on Selected Areas in Communications
- **Zotero Key**：`8S7LK7TQ`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/SSNet Channel Extrapolation for FAS]]

**研究问题**：如何在减少对标注数据依赖的同时，实现 FAS 中准确、鲁棒且能适应可变 CSI 输入数量的信道外推？

**方法**：把信道外推建模为图像重建任务 + 对比损失与 NMSE 联合损失的自监督网络 SSNet

**使用模型**：任务形式：图像重建（掩码/未掩码像素 ↔ 已知/未知端口 CSI）；训练方式：自监督学习（self-supervised learning）；损失函数：对比损失（contrastive loss）+ 信道外推归一化均方误差（NMSE）的联合损失

**优点**：自监督范式可摆脱对大量标注 CSI 数据集的依赖，这是相对数据驱动方法的关键改进。；联合损失（对比 + NMSE）是同时获得判别性表示与重建精度的关键设计。

**不足**：创新性主要在范式迁移与组合，核心学习组件非原创。；性能与推理时间的权衡仍需按实际部署约束再评估。；依赖仿真信道模型（Clarke、全相关），真实 FAS 硬件缺陷建模可能不足。

**未来研究方向**：在真实 FAS 硬件平台上验证。；联合优化端口选择与外推（端到端）。；扩展到 FAS-ISAC 联合信道获取。

---

### 39. Diagonally Reconstructed Channel Estimation for MIMO-AFDM With Inter-Doppler Interference in Doubly Selective Channels

- **作者**：Haoran Yin, Xizhang Wei, Yanqun Tang, Kai Yang
- **年份**：2024
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`KAZLUQJK`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Diagonally Reconstructed Channel Estimation for MIMO-AFDM]]

**研究问题**：在分数多普勒的双选信道下，如何在 MIMO-AFDM 系统中避免逐径估计带来的径间多普勒干扰（IDoI），获得接收处理所需的有效信道矩阵？

**方法**：向量化输入输出建模 + 对角可重构性分析 + 低复杂度 EPA-DR 方案

**使用模型**：系统：MIMO-AFDM（多输入多输出 + 仿射频分复用）；信道条件：分数多普勒（fractional Doppler）的双选信道；估计方式：嵌入式导频辅助（embedded pilot-aided, EPA）；关键量：AFDM 有效信道矩阵（接收处理必需）

**优点**：有效信道矩阵是 MIMO-AFDM 接收处理的必需量，本文方案是「把 AFDM 推向实用通信系统的重要一步」。；不估计三参数而直接重构对角，是从问题结构上消除 IDoI，而非事后抑制。

**不足**：主要为仿真验证，无实测信道数据。；对角可重构性依赖 AFDM 子信道矩阵的结构假设，在更一般信道下的适用性需进一步检验。；论文聚焦信道估计，未与完整的检测/译码链路做端到端联合评估。

**未来研究方向**：在实测高移动性信道下验证 EPA-DR。；与 AFDM 检测算法联合优化。；推广到 AFDM-ISAC 一体化波形设计。

---

### 40. Under-Determined DOA Estimation: A Method Based on Higher-Order Statistics and Non-Uniform Arrays

- **作者**：Wei Peng, Peng Li, Xinyi Wu, Kai Luo, Gan Zheng, Dong Li
- **年份**：2024
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`74WGPALB`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/信道估计/Under-Determined DOA Estimation]]

**研究问题**：当路径数超过阵元数时，如何突破二阶统计量 + 均匀线阵的限制，实现欠定条件下的 DOA 估计并提升噪声鲁棒性？

**方法**：高阶统计量（扩展阵列孔径 + 抑制高斯噪声）+ 非均匀阵列结构

**使用模型**：问题：欠定 DOA 估计（路径数 > 阵元数）；统计量：高阶统计量（higher-order statistics）；阵列结构：非均匀阵列（non-uniform array）；目标：扩展有效孔径与自由度，抑制高斯噪声

**优点**：高阶统计量是突破「阵元数硬限制」的关键：它从统计结构上产生额外的等效孔径。；非均匀阵列是释放高阶统计量自由度潜力的必要条件——这是一个容易被忽略的配套设计。

**不足**：高阶统计量计算复杂度高于二阶统计量。；仿真验证，无实测。；非均匀阵列的硬件实现（互耦、校准）比均匀阵列复杂。；量化能力上限需查阅仿真章节。

**未来研究方向**：降低高阶统计量的计算复杂度。；研究非均匀阵列在互耦下的校准方法。；在 UAV/ISAC 的实际感知场景中验证。

---

### 41. MIMO-PASS: Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems

- **作者**：(原文首页未在当前全文提取中定位到完整作者行)
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Communications
- **Zotero Key**：`GP5BSSKT`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/MIMO-PASS Uplink and Downlink Transmission]]

**研究问题**：如何在多用户 MIMO 场景中部署 PASS，分别设计下行的混合波束成形与上行的多用户检测方案，并量化其相对既有 MIMO 架构的吞吐增益？

**方法**：分式规划（FP）+ Gauss-Seidel 迭代优化数字预编码与捏合单元位置

**使用模型**：下行：AP 数字预编码矩阵 + 波导上捏合单元位置（联合优化）；上行：混合多用户检测（hybrid multiuser detection）；捏合单元位置：可通过网格搜索高效确定

**优点**：PASS 的捏合单元位置是新引入的空间自由度，可与数字预编码联合优化。；FP + Gauss-Seidel 的组合可在低复杂度下处理该混合优化问题。

**不足**：捏合单元位置用网格搜索，精度与复杂度受网格粒度制约。；纯仿真验证，无硬件平台实测。；未考虑捏合单元移动的物理时延与机械约束。；本文作者行在 PDF 文本提取中未能定位，元数据完整性有缺口。

**未来研究方向**：用连续优化或学习式方法替代网格搜索。；在真实 PASS 硬件上验证吞吐增益。；研究移动/时变场景下的位置自适应策略。

---

### 42. Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinching-Antenna Systems With Motion Power Consumption

- **作者**：Yiming Xu, Dongfang Xu, Xianghao Yu, Shenghui Song, Zhiguo Ding, Robert Schober
- **年份**：2026
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`PNMKBVZU`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/PASS Joint Radiation Power Antenna Position Beamforming]]

**研究问题**：在考虑 PA 移动功耗与可调辐射功率的条件下，如何在给定 QoS 要求下最小化 PASS 系统的平均功耗？

**方法**：联合优化天线位置、天线辐射功率比与发射波束成形以最小化平均功耗

**使用模型**：技术：PASS（可捏合天线系统）；优化变量：天线位置、天线辐射功率比、发射波束成形；约束：QoS 要求、天线放置的物理约束；能耗项：PA 移动功耗 + 辐射功率 + 发射功耗

**优点**：天线重构不是免费的——移动 PA 需要消耗能量，这是此前被忽略的实际代价。；辐射功率可调是继「位置可调」之后的第二个自由度，二者联合才有完整的设计空间。

**不足**：量化收益需查阅仿真章节。；仿真验证，无实测。；PA 移动速度/时延对动态业务的影响未讨论。

**未来研究方向**：研究 PA 移动时延对业务连续性的影响。；在真实 PASS 平台上验证。

---

### 43. Learning to Optimize Resource Allocation in Dynamic Wireless Environments: Embracing the New While Engaging the Old

- **作者**：Zhenrong Liu, Yang Li, Yik-Chung Wu, Yi Gong
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`C8A262UH`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Learning to Optimize Resource Allocation in Dynamic Wireless]]

**研究问题**：如何让 DNN 资源分配器在适应新（变化的）无线环境的同时，保留先前学到的知识？

**方法**：在低秩协方差的零空间（null space）中更新 DNN 参数以适配新环境且保留旧知识

**使用模型**：基础模型：用于资源分配的 DNN；问题：信道分布随时间变化（分布偏移）；更新机制：在低秩协方差的零空间内更新参数；效果：新环境适应 + 旧知识保留（抗灾难性遗忘）

**优点**：分布偏移是无线学习方法的常态而非例外，算法设计必须正面应对。；零空间投影是持续学习中优雅且有效的机制：在「不干扰旧知识」的方向上学习新知识。

**不足**：量化收益需查阅仿真章节。；仿真验证，无实测。；低秩假设在剧烈变化的环境下可能不成立。；零空间维度随任务增多而收缩，长期持续学习的可扩展性需评估。

**未来研究方向**：研究长期多环境下的零空间耗尽问题。；在真实动态信道下验证。

---

### 44. Normalizing Flow-Based Differentiable Particle Filters

- **作者**：Xiongjie Chen, Yunpeng Li
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Signal Processing
- **Zotero Key**：`5LH9KB2X`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Normalizing Flow-Based Differentiable Particle Filters]]

**研究问题**：如何在可微粒子滤波中获得合法的概率密度，并使动态模型、提议分布与测量模型都可自适应学习而不受预定义分布族限制？

**方法**：归一化流建模三个模块 + 理论推导（ELBO 等）+  joint 状态估计与模型学习

**使用模型**：框架：可微粒子滤波（differentiable particle filtering）；核心组件：条件归一化流（conditional normalizing flows）；三个被建模模块：动态模型、提议分布、测量模型；联合任务：序贯状态估计 + 模型学习

**优点**：归一化流的「可逆 + 密度可精确计算」特性恰好补上了 vanilla 神经网络在密度估计上的短板。；把三个模块都换成归一化流，使整个滤波器摆脱对预定义分布族的依赖。

**不足**：归一化流的表达能力与计算开销存在权衡（深层流推理慢）。；量化收益需查阅实验章节。；高维状态空间下归一化流的可扩展性需进一步验证。；仿真/基准任务为主，真实复杂场景验证待补充。

**未来研究方向**：研究更高效的流结构以适配实时滤波。；在高维状态空间（如视觉 SLAM）上验证。；与 UAV/ISAC 的实际感知任务结合做实测。

---

### 45. OptiPMB: Enhancing 3D Multi-Object Tracking With Optimized Poisson Multi-Bernoulli Filtering

- **作者**：Guanhua Ding, Yuxuan Xia, Runwei Guan, Qinchen Wu, Tao Huang, Weiping Ding, Jinping Sun, Guoqiang Mao
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Intelligent Transportation Systems
- **Zotero Key**：`7BGSJSQ3`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/OptiPMB 3D Multi-Object Tracking]]

**研究问题**：如何在 TBD 框架下优化基于 RFS 的 3D 多目标跟踪，使其跟踪精度与航迹 ID 保持能力超越既有 RFS 跟踪器？

**方法**：RFS 贝叶斯滤波 + 测量驱动混合自适应新生模型 + 自适应检测概率 + 密度剪枝与航迹提取优化

**使用模型**：框架：Tracking-by-Detection（TBD）；滤波器：泊松多伯努利（PMB）滤波器；理论基底：随机有限集（RFS）贝叶斯滤波，统一处理目标新生、存活与消亡

**优点**：RFS 框架相比 RV 方法的关键优势在于以理论严谨的方式处理目标新生/存活/消亡，便于解释与调参。；三项自适应设计（新生、检测概率、剪枝/提取）是把通用 PMB 滤波器推向自动驾驶实用场景的关键。

**不足**：属增量式改进，核心 RFS/PMB 理论非本文原创。；依赖外部检测器（CenterPoint），检测质量直接制约跟踪上限。；面向自动驾驶场景，向 UAV 空基视角迁移需重新调参与验证。；具体 AMOTA/HOTA 数值需查阅全文才能定量评估。

**未来研究方向**：把自适应设计迁移到空基/无人机视角的 3D MOT。；与检测器联合训练/优化（端到端）。；在遮挡更严重的场景（密集人群、城市峡谷）下验证。

---

### 46. Overparameterized ReLU Neural Networks Learn the Simplest Model: Neural Isometry and Phase Transitions

- **作者**：Yifei Wang, Yixuan Hua, Emmanuel J. Candès, Mert Pilanci
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Information Theory
- **Zotero Key**：`IZAZ7ZJW`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Overparameterized ReLU Neural Networks]]

**研究问题**：如何从理论上解释过参数化 ReLU 网络仍能良好泛化？其学到的模型具有什么结构特性？

**方法**：凸优化与稀疏恢复分析 + 等距条件（isometry）+ 相变分析

**使用模型**：网络：两层 ReLU 网络；正则化：标准权重衰减（weight decay）；变体：含 skip connections 或 normalization layers 的 ReLU 网络变体；分析工具：凸优化、稀疏恢复、等距条件（isometry conditions）

**优点**：深度学习泛化之谜可在凸优化—稀疏恢复的统一框架下得到解释。；「神经等距（neural isometry）」是连接网络训练与稀疏恢复的关键结构条件。

**不足**：结论依赖数据的正则性假设，实际数据未必满足。；分析对象限于两层 ReLU 网络，向深层/其他激活函数的推广需额外工作。；与工程应用（如 UAV/通信）的直接联系未在文中建立。

**未来研究方向**：推广到深层网络与其他激活函数。；放宽数据正则性假设。；与具体应用（如通信中的学习模块）建立联系。

---

### 47. Passive Human Tracking With WiFi Point Clouds

- **作者**：Zhongqin Wang, J. Andrew Zhang, Haimin Zhang, Min Xu, Jay Guo
- **年份**：2025
- **期刊/会议**：IEEE Internet of Things Journal
- **Zotero Key**：`P6EQSBL9`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Passive Human Tracking With WiFi Point Clouds]]

**研究问题**：在商用 WiFi 硬件限制（带宽/天线/时钟异步）与人体非刚体、多径多普勒差异的条件下，如何实现准确的实时被动人体跟踪？

**方法**：WiDFS2.0 增强型实时跟踪方案（超越单一主 DFS 提取）

**使用模型**：硬件：商用 WiFi 设备（带宽有限、天线少、双站时钟异步）；目标：移动的人（非刚体，多部位产生不同 DFS）；信道特性：多径环境下不同子载波呈现不同多普勒特性；输出：实时人体跟踪

**优点**：人体非刚体性使 DFS 呈现分布而非单一值——这是 WiFi 人体感知的固有特性。；多径下不同子载波的差异不是纯干扰，而是可利用的信息。

**不足**：量化收益需查阅实验章节。；商用设备的异构性可能影响泛化。；多目标/密集人群场景的适用性未在当前材料中说明。

**未来研究方向**：在更多商用设备与场景上验证。；研究多人同时跟踪的扩展。

---

### 48. Random Access Control in NB-IoT With Model-Based Reinforcement Learning

- **作者**：Juan J. Alcaraz; Juan-Carlos Sanchez-Aarnoutse; Alejandro-Santos Martinez-Sala; Francisco-Javier Gonzalez-Castaño
- **年份**：2025
- **期刊/会议**：IEEE Internet of Things Journal, 12(7), 8135–8149
- **Zotero Key**：`FHVKJ6WF`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Random Access Control in NB-IoT With Model-Based Reinforcement Learning]]

**研究问题**：笔记未记录

**方法**：排队与组合分析模型、最大似然流量估计和强化学习参数调节

**使用模型**：笔记未记录

**优点**：笔记未记录

**不足**：笔记未记录

**未来研究方向**：笔记未记录

---

### 49. WDMoE: Wireless Distributed Mixture of Experts for Large Language Models

- **作者**：Nan Xue, Yaping Sun, Zhiyong Chen, Meixia Tao, Xiaodong Xu, Liang Qian, Shuguang Cui, Ping Zhang
- **年份**：2025
- **期刊/会议**：IEEE Transactions on Wireless Communications
- **Zotero Key**：`J4JEDLUD`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/WDMoE Wireless Distributed Mixture of Experts]]

**研究问题**：如何把 LLM 的 MoE 层拆解部署到基站与移动设备，并通过联合优化专家选择与带宽分配，在保持模型精度的同时最小化推理时延？

**方法**：MoE 层拆解部署 + 兼顾模型能力与时延的性能指标 + 专家选择与带宽分配联合优化

**使用模型**：基站（BS）：承载门控网络 + 前置神经网络层；移动设备：分布式承载各专家网络；执行流程：设备上专家并行推理 → 结果回传基站；优化变量：专家选择（哪些专家参与）+ 带宽分配

**优点**：MoE 的「专家并行」天然契合分布式部署，是 LLM 边缘化的结构性机遇。；把门控网络留在基站可保证路由决策的集中性与一致性。

**不足**：设备异构性（算力/电量差异）对专家分配的影响需进一步研究。；无线链路波动会导致专家回传时延抖动，鲁棒性待验证。；量化收益需查阅仿真章节。；缓存受限时专家网络的换入换出开销未充分讨论。

**未来研究方向**：研究设备异构与链路波动下的自适应专家分配。；考虑专家缓存与换入换出策略。；在真实无线环境做端到端验证。

---

### 50. Environment Sensing Considering the Occlusion Effect: A Multi-View Approach

- **作者**：Xin Tong, Zhaoyang Zhang, Yihan Zhang, Zhaohui Yang, Chongwen Huang, Kai-Kit Wong, Mérouane Debbah
- **年份**：2022
- **期刊/会议**：IEEE Transactions on Signal Processing
- **Zotero Key**：`XJZXB8JC`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/Environment Sensing with Occlusion Effect]]

**研究问题**：在存在遮挡效应的无线场景中，如何融合多用户/多基站的不同视角以实现准确的环境感知？

**方法**：GAMP-MVSVR 算法（广义近似消息传递 + 多视角稀疏向量重建）+ 多层因子图

**使用模型**：信号流：多 UE 发送探测信号 → 一个或多个 BS 接收 → 中心处理器汇总信道信息；环境表示：稀疏向量（环境的稀疏表示）；挑战：遮挡效应使某些视角的观测不完整；结构：多层因子图（刻画多视角与稀疏结构的关系）

**优点**：遮挡不是单纯的噪声，而是结构性的信息缺失——必须用多视角互补来克服。；GAMP 提供了在因子图上做高效近似推断的工具，适合大规模稀疏重建。

**不足**：量化收益需查阅仿真章节。；仿真验证，无实测。；多层因子图的构造复杂度需评估。

**未来研究方向**：在真实蜂窝环境中验证。；研究视角选择的优化（并非越多越好）。

---

### 51. Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems

- **作者**：Bo Chang, Lei Zhang, Liying Li, Guodong Zhao, Zhi Chen
- **年份**：2019
- **期刊/会议**：IEEE Transactions on Vehicular Technology
- **Zotero Key**：`9C2VZXD7`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/其他/URLLC Resource Allocation for Real-Time Wireless Control]]

**研究问题**：在上行传输下，如何通过联合优化 URLLC 的带宽与功率分配以及控制收敛速率，实现通信与控制的最优协同？

**方法**：基于上行传输，联合优化 URLLC 的带宽与发射功率分配以及控制收敛速率

**使用模型**：链路方向：上行传输；通信侧：URLLC 的带宽分配、发射功率分配；控制侧：控制收敛速率（反映控制子系统性能）；耦合关系：通信资源消耗 ⇄ 控制性能

**优点**：控制与通信不是「先通信达标、再控制设计」的串联关系，而是必须联合优化的耦合关系。；控制收敛速率是连接通信质量与控制性能的合适桥梁指标。

**不足**：量化收益需查阅仿真章节。；仿真验证，无实测。；单控制对象/小规模场景的设定，大规模扩展未讨论。

**未来研究方向**：在真实工业控制系统中验证。；扩展到多控制回路协同。

---

### 52. Attention Is All You Need

- **作者**：Vaswani, Shazeer, Parmar, Uszkoreit, Jones, Gomez, Kaiser, Polosukhin
- **年份**：2023
- **期刊/会议**：arXiv preprint (cs.CL)
- **Zotero Key**：`BBHSTSCH`
- **笔记**：[[F:/XWCos/obisidian/xwcall/xwcall/02vault/LLM/Attention Is All You Need]]

**研究问题**：能否设计一种完全依赖注意力机制、不含循环与卷积的序列转换架构，在提升翻译质量的同时大幅提高可并行性并降低训练成本？

**方法**：编码器-解码器 + 多头自注意力 + 位置编码

**使用模型**：Encoder：每层含多头自注意力子层 + 位置-wise 前馈网络子层，每个子层外接残差连接与层归一化。；Decoder：在编码器两子层基础上插入一个对编码器输出做多头注意力的子层；自注意力子层带掩码，保证位置 i 的预测只能依赖 i 之前的已知输出。；前馈网络 FFN(x) = max(0, xW1 + b1)W2 + b2，内层维度 d_ff = 2048。；输出层：解码器输出经线性变换与 softmax 得到下一 token 概率；两个嵌入层与 pre-softmax 线性变换共享权重矩阵，嵌入层权重乘以 d_model 的平方根。

**优点**：首次证明纯注意力架构足以承担完整序列转换任务。；自注意力将任意位置间的路径长度压缩为常数级操作（对比循环 O(n)、卷积 O(log_k n)）。；多头机制可联合关注不同位置的不同表示子空间。；训练成本大幅下降：base 模型的训练成本低于任何竞争模型。

**不足**：位置编码为固定的正弦/余弦形式，论文未充分讨论其在超出训练长度序列上的外推表现。；自注意力复杂度为 O(n^2 · d)，长序列场景下仍存在二次增长问题（论文 Table 1 已列明）。；论文自述平均化注意力加权位置会降低有效分辨率，仅通过多头机制缓解，未给出彻底解决方案。；实验集中于机器翻译与句法分析，对其他模态与更长上下文的验证有限。

**未来研究方向**：更高效的长序列注意力机制（稀疏、线性化注意力）。；可学习或相对位置编码，改善长度外推。；面向低资源、多模态与实时场景的适配。

---
