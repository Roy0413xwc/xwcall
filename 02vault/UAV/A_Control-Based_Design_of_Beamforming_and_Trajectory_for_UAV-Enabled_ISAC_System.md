---
title: A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System
journal: IEEE Transactions on Wireless Communications
authors:
  - Bin Li
  - Hongyun Zhang
  - Yue Rong
  - Zhu Han
tags:
  - ISAC
  - UAV
  - SCA
  - SDR
  - trajectory-optimization
  - alternating-optimization
  - beamforming
  - control-parametrization
  - UAV-enabled-ISAC-system
year: 2026
knowledge:
  - "[[SCA与SDR优化方法基础]]"
  - "[[UAV动力学建模]]"
---

- **[《A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System》](zotero://select/library/items/HWHQDBSP)**
<span style="color: #E63946; font-weight: bold;">作者</span>: <span style="color: #1D3557;">Li, Zhang, Rong, Han</span>
<span style="color: #FFC107; font-weight: bold;">发表年份</span>: <span style="color: #2A9D8F;">2026</span>
<span style="color: #8E44AD; font-weight: bold;">期刊名称</span>: <span style="color: #264653;">IEEE Transactions on Wireless Communications</span>

# A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System

## 📌 Basic Information

## Author

Bin Li, Hongyun Zhang, Yue Rong, Zhu Han

## Year

2026

## Source

IEEE Transactions on Wireless Communications

## Research Area

-   Integrated Sensing and Communication (ISAC)
-   UAV Communication
-   Beamforming Optimization
-   Trajectory Optimization
-   Optimal Control

------------------------------------------------------------------------

# 1. Abstract Summary

本文研究无人机辅助ISAC系统中的波束成形与飞行轨迹联合优化问题。
作者考虑无人机真实动力学模型，通过联合设计通信/感知波束和UAV轨迹，在满足感知约束和动力学约束的情况下最大化通信速率。

核心关键词：

UAV-enabled ISAC + Beamforming + Trajectory Optimization + Control

------------------------------------------------------------------------

# 2. Research Background

## 背景

6G网络不仅要求高速通信，还需要高精度环境感知能力。

ISAC（Integrated Sensing and
Communication）通过共享频谱和硬件，同时完成：

-   通信
-   雷达感知

UAV具有高机动性和良好的空地信道条件，因此成为ISAC的重要平台。

## Motivation

已有UAV-ISAC轨迹优化方法通常：

-   将UAV建模为质点
-   只考虑位置和速度

忽略：

-   <mark style="background:#fff88f">姿态变化</mark>
-   推力
-   转动力矩

导致优化得到的轨迹无法被真实无人机控制系统准确执行。

## Application Scenario

-   交通监控
-   应急通信
-   环境监测

------------------------------------------------------------------------

# 3. Research Question

## 核心问题

如何在考虑无人机真实动力学情况下：

联合优化：

1.  UAV飞行轨迹
2.  通信波束
3.  感知波束

最大化通信性能，同时满足感知要求。

------------------------------------------------------------------------

# 4. Related Work

## 已有方法

### 1. 时间离散轨迹优化

将飞行时间划分为多个slot。

缺点：

产生分段轨迹，不连续。

### 2. Model-free UAV优化

将UAV视为移动点。

缺点：

没有考虑实际飞行控制约束。

### 3. 联合Beamforming和Trajectory设计

不足：

主要关注理论性能，没有考虑实际执行误差。

------------------------------------------------------------------------

# 5. Methodology

## Overall Idea

提出控制驱动(Control-based)的联合优化框架。

整体流程：

固定轨迹 ↓ 优化Beamforming (SCA + SDR)

固定Beamforming ↓ 优化UAV轨迹 (Control Parameterization + SQP)

循环迭代。

------------------------------------------------------------------------

# Model / Framework

系统：

-   多天线UAV
-   多个单天线用户
-   多个感知目标

考虑两种动力学模型：

## 3-DoF模型

只考虑平移运动。

优点：

计算复杂度低。

缺点：

控制精度不足。

## 6-==DoF模型可以用于airan项目==

考虑：

-   x,y,z位置
-   roll
-   pitch
-   yaw

更加接近真实无人机。
![[Pasted image 20261014151640.png]]
------------------------------------------------------------------------

# Algorithm / Technique

## Beamforming Optimization

采用：

### SCA

Sequential Convex Approximation

处理非凸优化问题。

### SDR

Semi-Definite Relaxation

处理rank-one约束。

------------------------------------------------------------------------

## Trajectory Optimization

采用：

### Control Parameterization

将连续控制输入转换为分段常数控制变量。

### Exact Penalty Function

将状态约束加入目标函数。

### SQP

Sequential Quadratic Programming

求解非线性规划。

------------------------------------------------------------------------

# 6. Mathematical Model / Theory

## Communication Model

用户SINR：

$$
\phi_m=
\frac{|g_m^Hw_m|^2}
{\sum_{i\neq m}|g_m^Hw_i|^2+
g_m^HG_dg_m+\sigma_m^2}
$$

通信速率：

$$
R_m=\log_2(1+\phi_m)
$$

------------------------------------------------------------------------

## Optimization Objective

最大化平均加权通信速率：

$$
R_{ave}
=
\frac1T
\int_0^T
\sum_m\rho_mR_m(t)dt
$$

约束：

-   发射功率限制
-   感知波束增益限制
-   UAV速度限制
-   初始终止位置约束
-   UAV动力学约束

------------------------------------------------------------------------

# Assumptions

论文假设：

1.  ==UAV高度固定不优化三维吗==
2.  用户位置已知
3.  感知目标位置已知
4.  空地信道采用LoS模型==感觉简化太多了信道模型==
5.  Doppler影响已补偿

------------------------------------------------------------------------

# 7. Experiment / Evaluation

## Environment

仿真：

-   8个通信用户
-   18个感知目标点

比较：

## P0

传统model-free方法

## P1

3-DoF模型

## P2

6-DoF模型

------------------------------------------------------------------------

# Metrics

评价：

-   Average communication rate
-   Beam pattern gain
-   Trajectory tracking error
-   Constraint violation

------------------------------------------------------------------------

# Results

主要结果：

1.  6-DoF模型轨迹更加符合真实飞行。

2.  传统方法规划轨迹性能较高，但实际执行性能下降。

3.  P2方案降低实际飞行中的性能损失。

4.  P1方案在复杂度和性能之间取得平衡。

------------------------------------------------------------------------

# 8. Key Findings

## Contribution 1

首次将真实无人机动力学模型引入UAV-ISAC联合设计。

## Contribution 2

提出控制参数化轨迹优化方法，实现连续平滑轨迹。

## Contribution 3

提出Beamforming和Trajectory交替优化算法。

------------------------------------------------------------------------

# 9. Innovation Analysis

## Author's Innovation

传统方法：

优化数学轨迹。

本文：

优化可执行控制轨迹。

## My Evaluation

⭐⭐⭐⭐

创新程度：高

原因：

结合：

ISAC + UAV + Control

三个方向。

------------------------------------------------------------------------

# 10. Limitation

## 不足

1.  计算复杂度较高。

2.  假设目标位置已知。

3.  实时在线优化能力有限。

## Future Improvement

-   ==MPC预测控制讲过==
-   强化学习控制
-   目标跟踪联合优化
-   多无人机协同ISAC

------------------------------------------------------------------------

# 11. My Thoughts

## What I Learned

==学习：==

- [x]   ==UAV动力学建模==
-   ==ISAC联合优化==
-   ==Beamforming设计==
- [x]   ==SCA/SDR优化方法==
-   ==最优控制思想==

- ## Connection With My Work

适合作为：

-   UAV-ISAC方向开题参考
-   轨迹优化方向核心论文

## Possible Ideas

1.  MPC + ISAC

利用未来信道预测优化轨迹。

2.  Tracking + ISAC

目标未知情况下联合跟踪和通信。

3.  Learning-based ISAC

利用深度强化学习实现实时控制。

------------------------------------------------------------------------

# 12. Related Notes

## Concepts

-   ISAC
-   UAV Communication
-   Beamforming
-   SCA
-   SDR
-   SQP
-   Optimal Control
-   MPC
-   Kalman Filter

## Related Papers

-   Joint maneuver and beamforming design for UAV-enabled ISAC
-   Beamforming design and trajectory optimization for UAV-empowered
    ISAC
-   Joint design of communication sensing and control with a UAV
    platform

------------------------------------------------------------------------

# 13. Summary Card

## Problem

考虑真实无人机动力学约束下的UAV-ISAC轨迹和波束联合优化。

## Method

SCA + SDR + Control Parameterization + SQP

## Result

6-DoF动力学模型提高实际飞行性能。

## Importance

说明ISAC系统设计不能只优化通信性能，还需要考虑实际控制能力。

------------------------------------------------------------------------

# Flash Card

Q: 这篇论文解决什么问题？

A: 解决UAV-ISAC中考虑真实动力学约束的轨迹和Beamforming联合优化问题。

Q: 核心方法是什么？

A:
交替优化Beamforming和Trajectory，其中Beamforming采用SCA/SDR，轨迹采用控制参数化和SQP。

Q: 最大贡献是什么？

A: 将无人机控制模型融入ISAC优化，使规划轨迹更加符合真实飞行。
