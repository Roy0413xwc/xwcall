---
onenote-id: 5a6a9cd3-3ec1-49ed-a3c5-cb3fb772d303:1
---
2026/5/31

# ﷟HYPERLINK "https://zhuanlan.zhihu.com/p/537067898"(4 封私信 / 80 条消息) 通信感知一体化（ISAC）：从入门到入坑 - 知乎

RCSS：频谱共享的大背景

RCC：两个系统共存，重点是干扰管理

DFRC：一个系统同时做雷达和通信

ISAC：通信 + 更广义的感知

ISAC 不是简单地把雷达和通信放在一起，而是希望通过统一的硬件、频谱、波形和信号处理设计，让无线网络同时具备通信能力和感知物理世界的能力。

集成增益：省资源

协作增益：互相帮

论文里常见通信指标有：

SINR：信干噪比

Rate：通信速率

BER：误码率

Throughput：吞吐量

论文里常见感知指标有：

CRB：参数估计误差下界

MSE：均方误差

Detection probability：检测概率

Beampattern：波束图

Angle / range / velocity estimation：角度、距离、速度估计

雷达探测性能主要分两类：

Radar performance criteria

│

├── Detection：检测.    检测性能常用三个概率描述：

Pd：正确检测概率，真的有目标，并且系统判断有目标

Pfa：虚警概率，明明没有目标，但系统误判为有目标

Pm：漏检概率，明明有目标，但系统没检测出来

│

└── Estimation：估计.    判断目标参数是多少

MSE：实际估计误差指标

CRLB：理论最优误差下界

CRB 越小 → 理论估计精度越高

MSE 越小 → 实际估计误差越小

# ﷟HYPERLINK "https://mp.weixin.qq.com/s/vaofUxurFaxSBInlvc_6Rw"雷达学术入门--脉冲雷达信号处理概述

[雷达原理【83集】(魏青：西安电子科技大学)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Rt411p7EQ/?spm_id_from=333.337.search-card.all.click&vd_source=b3f35d3b56b0c8b4462f62e309cf04d6)参考视频

我们就从这篇 **“****==🟡雷达学术入门--脉冲雷达信号处理概述==****”** 开始，而且先不急着看复杂公式。

**第 1 站：脉冲雷达的基本工作流程**

雷达发射一个短脉冲，等目标反射回来，再根据回波的信息判断目标的位置、速度、角度等。

过程：发射脉冲 → 信号传播到目标 → 目标反射 → 雷达接收回波 → 处理回波

脉冲雷达：一下一下发射信号，然后接收目标回波

PRI：两个脉冲之间的时间间隔,PRF：一秒发多少个脉冲

τ = 2d / c：双程时延,d = cτ / 2：由时延估计距离

![[Gpt知乎入门isac image.png]]

目标朝雷达靠近或远离 → 有明显多普勒

目标绕着雷达横向运动，距离几乎不变 → 多普勒可能很小

e^{j2πf_D t}表示一个随时间旋转的相位。

你可以理解成：因为目标在运动，回波相位不是固定的，而是在持续旋转；旋转速度就是多普勒频率 f_D。

如果目标朝雷达靠近：距离 d(t) 变小,回波频率通常变高.多普勒频移为正或负，取决于论文的符号约定

目标方向

↘

天线1   天线2   天线3   天线4

信号到不同天线的路程不一样。路程差会导致 **相位差**。核心关系是：路程差 → 时间差 → 相位差

[(8 封私信 / 80 条消息) 阵列导向矢量(Steering vector)详细推导 - 知乎](https://zhuanlan.zhihu.com/p/1931011171479171685)

![[Gpt知乎入门isac image 1.png]]

路程差 d sinθ↓占波长的比例 d sinθ / λ↓乘上一整圈相位 2π↓相位差 2πd sinθ / λ

![[Gpt知乎入门isac image 2.png]]

**第** **2** **站：目标检测问题 Detection**

![[Gpt知乎入门isac image 3.png]]

H0：没有目标，只有噪声。H1：有目标，回波 + 噪声

T(y)：检测统计量，表示 y 像不像目标。γ：检测门限

PD：有目标时正确检测出来

PFA：没目标时误判有目标

Pm：有目标时漏掉目标

Neyman-Pearson：控制虚警，最大化检测概率

**第** **3** **站：参数估计问题 Estimation**

距离估计 → 快时间 Fast-Time → 看一个脉冲内部的时延

速度估计 → 慢时间 Slow-Time → 看多个脉冲之间的相位变化

角度估计 → 空间维度 Spatial → 看多天线之间的相位差。**MUSIC** 和 **ESPRIT** 都是经典的角度估计算法

Detection：判断有没有目标

Estimation：估计目标参数是多少

距离 d：来自时延 τ。匹配滤波做的事情就是：把 y(t) 和不同延迟版本的 s(t) 做相关，哪个延迟位置相关峰值最大，哪个延迟就是目标时延 τ。脉冲压缩：实际雷达常常希望发射较长脉冲来增加能量，但又希望距离分辨率像短脉冲一样好

[(8 封私信 / 80 条消息) 雷达笔记 - 4 匹配滤波/脉冲压缩 - 知乎](https://zhuanlan.zhihu.com/p/616973836)

速度 v：来自多普勒 fD

角度 θ：来自阵列相位差

MSE：实际估计误差

CRLB：理论误差下界。如果 CRLB 很小，说明这个系统从理论上具备较好的估计能力。如果 CRLB 很大，说明不管你用什么估计算法，都很难估得特别准。

[雷达原理【83集】(魏青：西安电子科技大学)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Rt411p7EQ/?spm_id_from=333.337.search-card.all.click&vd_source=b3f35d3b56b0c8b4462f62e309cf04d6)参考视频

2026/6/1开始看，笔记如下

[**雷达原理在good note**](%E9%9B%B7%E8%BE%BE%E5%8E%9F%E7%90%86%E5%9C%A8good%20note)

一些经典的检测器[<sup>\[1\]</sup>](https://zhuanlan.zhihu.com/p/537067898#ref_1)、CRLB[<sup>\[2\]</sup>](https://zhuanlan.zhihu.com/p/537067898#ref_2)的推导可以参考这2篇paper：

\[1\] Fishler E, Haimovich A, Blum R S, et al. Spatial diversity in radars—Models and detection performance\[J\]. IEEE Transactions on signal processing, 2006, 54(3): 823-838. \[2\] Bekkerman I, Tabrikian J. Target detection and localization using MIMO radars and sonars\[J\]. IEEE Transactions on Signal Processing, 2006, 54(10): 3873-3883.

来自 \<https://zhuanlan.zhihu.com/p/537067898>