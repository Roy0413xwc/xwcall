---
title: ISAC 研究方向及论文图谱
date: 2026-10-16
tags: [ISAC, 文献图谱]
---

# 研究方向图谱

| 方向         | 本地代表                                                            | 共同模型            | 常用指标                | 主要边界                 |
| ---------- | --------------------------------------------------------------- | --------------- | ------------------- | -------------------- |
| UAV 轨迹/部署  | ISAC from the Sky；Radar Probing；Control-Based；Joint Deployment  | 位置/轨迹、波束、功率联合设计 | 速率、CRLB、能耗          | 多为单目标、仿真、短时域         |
| 波束与收发机     | Optimal Beamforming；GNN Beamforming；Deep Unfolding              | 协方差矩阵、波束、接收滤波   | Sum-rate、CRLB、MSE   | 常假设 CSI/目标状态已知       |
| 目标跟踪/定位    | U2U Beam Tracking；Cooperative Detection；AFDM Estimation         | 角度/距离/多普勒或 PCRB | RMSE、CRLB/PCRB、检测概率 | 跟踪误差对下一步资源的反馈不足      |
| 预测控制       | Predictive Control；LLM V2I Beamforming                          | 预测状态/信道，滚动时域    | 累计效用、跟踪误差           | 预测模型失配、控制延迟常未完整建模    |
| 多 UAV 协同   | C-HAPPO；Multi-UAV Dual Objective；AIBOT；Cooperative Low-Altitude | 多智能体位置、关联、功率    | Pareto、覆盖、能效        | 公平性、通信开销和泛化验证不足      |
| 鲁棒/不完美 CSI | U2U Jitter；Near-Field Secure；Situation-Aware                    | 抖动、遮挡、近场、混合感知   | 鲁棒速率、保密率、感知误差       | 不确定性常被简化成固定裕量        |
| 新兴方向       | CKM、6DMA、OTA Control、SeCo4                                      | 知识地图、可动天线、通控算协同 | 规划代价、控制稳定性、能效       | 真实数据和统一 benchmark 缺失 |

跨论文稳定判断：优化分解类有结构解释但通常局部最优；学习类适应高维动态环境但缺少最优性、样本效率和 sim-to-real 证据。22 篇综合来源全部以仿真为主，不能做跨论文数值排名。
