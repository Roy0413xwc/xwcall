---
title: 最小可行仿真实验方案
date: 2026-10-16
tags: [仿真, PCRB, MPC]
---
# 选题一最小仿真
离散状态：$x_t=[r_x,r_y,v_x,v_y]^T$，$x_{t+1}=Fx_t+Gu_t+w_t$；UAV 位置 $q_{t+1}=q_t+v_t\Delta t$，$\|v_t\|\le v_{max}$、$\|u_t\|\le a_{max}$。观测为 $z_t=h(x_t,q_t,a_t)+v_t$，信道用自由空间/LoS+阴影衰落，感知 Fisher 信息由距离和波束方向决定。
目标：$\min\sum[-R_k+\lambda\operatorname{tr}(P_k)+\mu E_k+\rho\mathrm{CVaR}_\alpha(L_k)]$。约束包括动力学、功率、最低速率、禁飞区和 $\operatorname{tr}(P_k)\le P_{max}$。
MDP 仅在完整状态和噪声分布已知时适用；遮挡、未知目标运动或仅有观测时应称 POMDP，策略输入为观测历史/滤波后验 $(\hat x_t,P_t)$。
基线：悬停/预设圆轨迹、瞬时速率/CRLB 贪心或 SCA、无后验风险项 MPC、可选 PPO/SAC。消融：去掉 $P_t$、主动感知、动力学约束，改变噪声/延迟/速度分布。指标：累计速率、平均/95% PCRB、失锁率、能耗、约束违例率、推理时延、跨噪声泛化。参数来源与自行假设需分开标注。未运行实验，不含性能结果。
