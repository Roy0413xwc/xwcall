# 方案6：车联网ISAC的轨迹级感知隐私——面向“内鬼”车辆的时域保护

> 一句话概括：在车联网 ISAC 中，任何能接收信号的车辆都可能利用 RSU 发出的信号，偷偷感知并跟踪别的车辆或行人。现有的感知隐私工作大多只让“单次估计”变差，但攻击者真正想要的是**连续轨迹**。本方案以攻击者的**后验 CRB（PCRB）** 作为轨迹级隐私指标，研究如何在保证合法感知和通信的同时，让攻击者“跟不住”目标，必要时还可以让它“跟错”。

---

## 1. 为什么值得做

### 1.1 ISAC 带来了一种新的隐私威胁：感知窃听

- 传统通信安全保护的是“数据”，ISAC 还会泄露“目标状态”：位置、速度、尺寸、轨迹。只要拿到 ISAC 信号，未授权的接收端就能做被动雷达感知。
- Zou、Masouros、Liu 等在 TVT 2024 的工作明确指出：网络中**任何一个通信用户**都可能非法利用波形做感知，成为“感知窃听者”（sensing Eve）。
- Han、Meng、Masouros 指出，感知安全比通信安全更难：被动雷达式的 Eve 可以把 ISAC 信号同时当作参考信号和监视信号使用，**根本没有一条数据链路可供加密**。
- 多篇综述都把感知安全列为尚未被充分研究的方向，例如 Matsumine 等在 IEEE OJCOMS 2025 发表的 ISAC 物理层安全综述。

### 1.2 车联网让这个问题更尖锐：“广播悖论”

这一点是本方案在车联网场景下的核心观察（属于我们自己的分析，论文中需要论证）：

- V2X 的安全类消息（CAM/BSM 等）**必须让周围所有车辆都能解码**，否则就失去了安全功能。
- 一旦某辆车能解码 RSU 或其他车辆发出的数据，它就能**重建出完整的发射信号**，进而把它当作参考信号做双基地被动感知。
- Han 等已经指出，对导频加扰的方法可以被这种“解码后重建参考信号”的被动雷达绕过。
- 所以，在车联网中，**仅靠密钥化波形或导频加扰，最多只能保护单播数据和专用感知帧，保护不了广播部分**。威胁模型应当以“内鬼”（本身就是合法通信用户的车辆）为中心，防护手段必须更多依赖**空间域和时间域**，而不能只依赖密码学。

### 1.3 现有工作的盲区：只看“单次快照”，不看“轨迹”

- 现有的感知隐私设计，几乎都以快照指标为目标：Eve 处的 CRB、互信息、SINR、检测概率、KL 散度等。
- 但攻击者在跟踪时，会用卡尔曼滤波、平滑器甚至神经网络，**利用目标运动的时间相关性**。单次估计差，并不代表轨迹估计差。
- 一个直接的反例来自隐私数据共享领域：一篇基于 Fisher 信息密度约束 ISAC 轨迹共享的论文（arXiv:2604.08743）声称其方法能从原理上限制轨迹被重建的精度。但第三方评审指出，经典 CRB 只约束固定参数的无偏估计；轨迹重建是滤波/平滑问题，使用的估计器通常有偏且利用了时间相关性，可能突破逐点 CRB。
- **而 PCRB（Van Trees 不等式意义下的贝叶斯界）在常规正则条件下，对任何估计器（包括有偏估计器）的贝叶斯均方误差都成立，并且天然包含运动模型先验。** 所以，用 Eve 的 PCRB 作为隐私约束，方向恰好是对的：让“Eve 的下界”足够大，就等于保证了 Eve 用任何方法都跟不准（在给定模型假设下）。

---

## 2. 相关工作梳理

### 2.1 感知隐私 / 感知安全

| 代表工作 | 做了什么 | 局限 / 与本方案的关系 |
|---|---|---|
| J. Zou, C. Masouros, F. Liu, S. Sun, *Securing the Sensing Functionality in ISAC Networks: An AN Design*, IEEE TVT, 2024 | 双基地场景，通信用户作为感知 Eve；基于互信息设计波束和人工噪声 | 快照指标；未考虑跟踪 |
| K. Han, K. Meng, C. Masouros, *Sensing-Secure ISAC: AF Engineering*, arXiv:2510.02103 | 通过 OFDM 子载波功率分配，在 Eve 的模糊函数中制造人工峰；合法端用失配滤波抑制，代价是一定的 SNR 损失；无需 Eve 的先验信息 | 快照；人工峰是静态的 |
| B. Du, K. Han, C. Masouros, *KLD-Based AF Shaping*, arXiv:2512.19974 | 面向 OFDM 和 OTFS，以 KL 散度为指标，从目标检测角度防止 Eve 感知 | 快照；检测视角 |
| *Sub-Sampling for Positioning Privacy in ISAC: Deception by Aliasing*, arXiv:2608.07206 | 利用稀疏阵列和稀疏导频造成混叠，欺骗 Eve；合法端可用导频加数据，Eve 只能用导频 | 假设 Eve 无法解码数据，**在车联网广播场景下不一定成立** |
| *Exploiting Phase Noise for Sensing Privacy in ISAC*, arXiv:2608.13270 | 利用合法单基地与 Eve 双基地在本振相位噪声上的不对称，扩大隐私差距 | 硬件视角，可作为补充 |
| Z. Fang et al., *Waveform Randomization for Secure ISAC*, arXiv:2610.07994 | 密钥化的波形随机化，合法节点持有密钥可恢复感知参考，Eve 无法构造正确的相干参考 | 同样面临广播悖论 |
| *Secure OFDM Waveform Design: Artificial Phase-Doppler Shifts*, arXiv:2602.23861 | 引入人工相位和多普勒偏移，制造低截获概率（LPI）波形；有 27 GHz、1 GHz 带宽的实测 | 可作为“时变扰动”思路参考 |
| *Enhancing Sensing Privacy via Joint Signal and AN Beamforming*, arXiv:2608.15506 | Eve 位置未知时的联合信号与人工噪声波束设计 | 快照 |
| *Sensing Security in Near-Field ISAC: Exploiting Scatterers*, arXiv:2510.20140 | 近场下同时保护角度和距离隐私 | 静态 |
| PrivISAC（RIS）, arXiv:2601.04488；AmbSentry（环境 IoT）, arXiv:2608.11799 | 借助 RIS 或环境反向散射设备引入可控扰动 | 需要额外硬件 |

### 2.2 “跟踪”出现在安全文献中，但用途相反

| 代表工作 | 做了什么 | 与本方案的区别 |
|---|---|---|
| J.-H. Hong et al., *Tracking-Assisted Robust Secure Transmission Against a Mobile Eavesdropper in Cell-Free ISAC*, arXiv:2608.06781 | 用多基地感知 + EKF 跟踪**窃听者**，再把位置不确定性映射成信道不确定性，做鲁棒保密波束 | 跟踪是为了保护**通信数据**；本方案是防止**目标被跟踪** |
| P. Liu et al., IEEE TVT, 2023（空中窃听者）；J. Wu, W. Yuan, L. Hanzo（UAV 安全轨迹）；RIS 安全 ISAC 跟踪, arXiv:2609.22307 | 同上，用跟踪辅助通信保密 | 同上 |
| *Balancing Functionality and GDPR-Driven Privacy in ISAC Trajectory Sharing*, arXiv:2604.08743 | 共享轨迹数据时，用 Fisher 信息密度约束来加噪 | 数据层面的后处理，不是物理层；其隐私保证的严格性受到质疑（见 1.3 节） |

### 2.3 AFDM 的物理层安全

| 代表工作 | 做了什么 |
|---|---|
| P. Wang et al., *A Secure AFDM System* (SE-AFDM), arXiv:2510.02023 | 预 chirp 参数由长周期伪随机序列控制的码本动态生成，并给出快速时变信道下的同步框架和硬件原型 |
| *Making AFDM Secure Against Eavesdroppers: A Phase Function Design Approach*, arXiv:2605.14837 | 把第二个 chirp 参数 $c_2$ 设计成通用相位函数，提高 Eve 暴力解调的复杂度；文中也综述了参数跳变、基于互易信道生成 $c_2$ 等已有方法 |
| D. Zhang et al., *Parameter Design for Secure AFDM*, arXiv:2503.19364 | 分析 $c_1, c_2$ 等参数对抗窃听性能的影响，给出设计准则 |
| *AFDM-Enabled ISAC in Dynamic Environments*, arXiv:2609.04876 | 指出安全问题在 AFDM-ISAC 中**仍很少被研究**，尤其是动态环境；chirp 参数可作为物理层安全的额外维度 |

**小结：** AFDM 安全目前主要保护的是**通信数据**的保密性，把 chirp 参数用于**感知隐私**的工作还很少。

**查新结论（截至 2026 年 11 月初）：** 在我们的检索范围内，**没有看到以攻击者 PCRB 为轨迹级隐私指标、在多时隙上联合设计 ISAC 发射的工作**，也没有看到针对车联网“广播悖论”的系统讨论。

---

## 3. 研究目标与创新点

### 3.1 三个层次的研究内容

**D1（核心）：轨迹级感知隐私的指标与发射设计**
- 以 Eve 的 PCRB 为隐私约束，以合法 RSU 的 PCRB 为感知目标，在多个时隙上联合设计波束和人工噪声。
- 关键物理手段：**把人工噪声对准敏感目标方向，同时在所有通信用户（包括内鬼 Eve）的直达信道上置零。** 这样 Eve 的通信不受影响，但它收到的目标回波被噪声污染；合法 RSU 自己知道发出的噪声，可以把它纳入匹配滤波参考，因此几乎不受影响。
- 时域手段：让扰动在时间上有结构地变化，使 Eve 的滤波器出现模型失配。

**D2（进阶）：轨迹一致的欺骗**
- 不是单纯抬高噪声，而是在 Eve 的距离-多普勒图中制造**随时间按物理规律移动的虚假目标**，诱导 Eve 的跟踪器锁定假航迹。
- 基础来自 Han 等的人工峰设计和混叠欺骗，但把“静态人工峰”升级为“动态、运动学一致的假轨迹”。
- 合法端持有密钥，可以用失配滤波去除假目标。

**D3（扩展）：AFDM chirp 参数作为感知隐私密钥**
- 在单播数据和专用感知帧中使用 chirp 参数跳变，分析 Eve 在参数失配时的模糊函数扩散程度。
- 明确讨论广播部分无法用这种方式保护，因此需要与 D1 结合。

### 3.2 可以写进摘要的创新点（候选）

1. 提出车联网 ISAC 的“广播悖论”，论证内鬼车辆可以通过解码广播消息重建参考信号，从而说明仅靠波形加密不足以保护感知隐私。
2. 首次以攻击者的 PCRB 作为轨迹级感知隐私指标，指出它对任何估计器都成立，弥补快照 CRB 指标的不足。
3. 提出“隐私-感知-通信”三方权衡下的多时隙发射设计（滚动优化），在保证内鬼车辆通信服务的同时阻止其跟踪敏感目标。
4. 提出运动学一致的轨迹欺骗方法，使攻击者跟踪器锁定虚假航迹。

---

## 4. 系统模型（建议写法）

**场景：** 一个 RSU（$N_t$ 发射天线、$N_r$ 接收天线，单基地感知）服务 $K$ 辆网联车；其中车辆 $e$ 是内鬼 Eve，配有 $M_e$ 根天线，可以解码广播数据。存在一个敏感目标 $s$（例如特定车辆或行人），其状态为 $\mathbf x_s(t) = [\mathbf p_s, \mathbf v_s]^{\mathsf T}$。

**发射信号：**
$$
\mathbf X(t) = \mathbf W(t)\, \mathbf S(t) + \mathbf A(t), \qquad \mathbf R_X(t) = \mathbf W\mathbf W^{\mathsf H} + \mathbf R_A,
$$
$\mathbf S$ 为通信符号（部分为广播，Eve 可解码），$\mathbf A$ 为人工噪声，协方差为 $\mathbf R_A$。

**合法感知（RSU 单基地）：** RSU 知道完整的 $\mathbf X$，回波为
$$
\mathbf Y_R = \alpha_s\, \mathbf b_R(\theta_s)\mathbf a^{\mathsf H}(\theta_s)\, \mathbf X(t-\tau_s)\, e^{j2\pi f_s t} + \text{杂波} + \mathbf N_R .
$$

**Eve 的双基地感知：** Eve 解码出 $\mathbf S$ 的广播部分，用它作参考，但**不知道** $\mathbf A$ 以及单播部分：
$$
\mathbf Y_E = \underbrace{\mathbf H_{e}\, \mathbf X(t)}_{\text{直达径}} + \beta_{s,e}\, \mathbf b_e(\vartheta_{s,e})\mathbf a^{\mathsf H}(\theta_s)\, \mathbf X(t-\tau_{s,e})\, e^{j2\pi f_{s,e} t} + \mathbf N_E .
$$

**人工噪声的空间约束：** $\mathbf H_k \mathbf R_A \mathbf H_k^{\mathsf H} = \mathbf 0,\ \forall k$（包括 $k=e$），即人工噪声不影响任何用户的直达通信；同时希望 $\mathbf a^{\mathsf H}(\theta_s) \mathbf R_A \mathbf a(\theta_s)$ 足够大。

**PCRB 递推：** 合法端和 Eve 各自的贝叶斯信息矩阵
$$
\mathbf J_L(t) = \big(\mathbf F \mathbf J_L(t-1)^{-1}\mathbf F^{\mathsf T} + \mathbf Q\big)^{-1} + \mathbf G_L\big(\mathbf R_X(t)\big),\qquad
\mathbf J_E(t) = \big(\mathbf F \mathbf J_E(t-1)^{-1}\mathbf F^{\mathsf T} + \mathbf Q\big)^{-1} + \mathbf G_E\big(\mathbf R_X(t)\big),
$$
其中 $\mathbf G_L, \mathbf G_E$ 为单时隙的测量 Fisher 信息，Eve 的那一项中人工噪声表现为干扰。

**多时隙优化（滚动时域，示意）：**
$$
\min_{\{\mathbf W(t), \mathbf R_A(t)\}_{t=t_0}^{t_0+T}} \ \sum_{t} \mathrm{tr}\big(\mathbf J_L(t)^{-1}\big)
\quad\text{s.t.}\quad
\mathrm{tr}\big(\mathbf E\, \mathbf J_E(t)^{-1}\mathbf E^{\mathsf T}\big) \ge \gamma,\ \ \mathrm{SINR}_k(t) \ge \Gamma_k\ (\text{含 } k=e),\ \ \mathrm{tr}\big(\mathbf R_X(t)\big) \le P,
$$
$\mathbf E$ 选出位置分量，$\gamma$ 为 Eve 位置误差下限（例如 5 m 表示“只知道在哪条车道附近”）。PCRB 对 $\mathbf R_X$ 是非凸的，可以用 SCA 或 SDR 加松弛求解；滚动时域意味着每个时隙只执行第一步，然后重新优化。

> **要事先想清楚的假设：** Eve 是否知道 RSU 的设计策略（Kerckhoffs 原则下应假设知道策略但不知道噪声实现）、Eve 的天线数、Eve 用的运动模型是否与真实一致。建议主结果按“强 Eve”（知道策略、模型匹配）给出，再分析弱 Eve 的情况。

---

## 5. 分阶段研究计划

### 第一篇：轨迹级隐私指标与单 RSU 设计（快报 → 期刊）

- 内容：给出广播悖论的论证；定义 Eve PCRB 隐私指标；在单个敏感目标、单个内鬼的场景下做多时隙发射设计。
- 对比基线：
  - 无保护；
  - 快照约束设计（每个时隙约束 Eve 的单次 CRB，代表现有做法）；
  - 白噪声型人工噪声；
  - Zou et al. 的互信息型人工噪声设计。
- **关键实验：** 展示“快照约束看起来安全，但 Eve 用卡尔曼滤波/平滑后误差显著下降”，而 PCRB 约束能保住隐私。这张对比图是整篇论文的卖点。
- 目标：IEEE WCL / SPL → IEEE TVT / TIFS。

### 第二篇：运动学一致的轨迹欺骗

- 内容：在 Han 等人工峰设计的基础上，让人工峰按 CV/CT 模型随时间移动；分析 Eve 跟踪器（GNN/JPDA/PMBM）的航迹混淆率。
- 指标：Eve 的 GOSPA、真实航迹被锁定的比例、假航迹存活时间；合法端的 SNR 损失。
- 目标：IEEE TIFS / TSP / TWC。

### 第三篇（可选）：AFDM 参数跳变用于感知隐私

- 内容：在单播和专用感知帧中做 $c_2$ 跳变，推导 Eve 在参数失配下的模糊函数和 PCRB；与 D1 结合，构成“空间 + 时间 + 波形”三层防护。
- 目标：IEEE TCOM / TVT。

---

## 6. 仿真方案

### 6.1 建议参数

| 参数 | 取值 |
|---|---|
| 场景 | 高速公路或城市主干道；RSU 高 6–10 m |
| 载频 / 带宽 | 28 GHz / 200 MHz（OFDM 起步，第三篇换成 AFDM） |
| RSU 天线 | 发 32–64 元，收 16–32 元 |
| 内鬼 Eve | 车载 4–8 元阵列，与目标距离 20–200 m |
| 敏感目标 | 1–3 个，车速 30–120 km/h |
| 跟踪器 | 合法端：EKF；Eve：EKF、RTS 平滑器、IMM（作为最强攻击者） |
| 帧周期 | 1–10 ms；隐私评估窗口 1–10 s |

### 6.2 评价指标

- **隐私：** Eve 的位置 RMSE 随时间的变化曲线、首次锁定时间（误差首次低于某阈值的时刻）、航迹保持率；对欺骗方案还要看航迹混淆率
- **合法感知：** RSU 的 PCRB 和 RMSE
- **通信：** 各车 SINR 和速率（包括 Eve 作为合法用户的速率）
- **三方权衡曲线：** 隐私门限 $\gamma$ vs 合法感知精度 vs 通信和速率

### 6.3 工具

- MATLAB（Phased Array / 5G Toolbox）或 Python + NumPy，信道可以先用几何 LoS 加点目标模型
- CVX / MOSEK 求解 SDR/SCA 子问题
- 跟踪器可以自己写 EKF/RTS；多目标欺骗部分可以参考 Stone Soup（Python 多目标跟踪框架）

---

## 7. 风险与应对

| 风险 | 应对 |
|---|---|
| 审稿人质疑“内鬼车辆跟踪别人”是否现实 | 用车队跟踪、尾随、商业数据采集等动机说明；引用 S-ISAC、隐私法规（GDPR、个人信息保护法）相关论述 |
| Eve 的能力假设被认为过强或过弱 | 主结果用强 Eve；同时给出天线数、模型失配、是否知道策略等因素的灵敏度分析 |
| PCRB 优化非凸、计算量大 | 先做单目标、短时域（$T$ = 1–3）；证明 $T=1$ 时可以转化为 SDP；长时域用 SCA |
| 与 Zou et al. 的人工噪声设计看起来相似 | 强调三点差异：轨迹级指标、多时隙设计、广播悖论下的内鬼威胁模型 |
| 人工噪声对靠近目标方向的其他用户造成干扰 | 把这一点纳入 SINR 约束；这本身就是权衡分析的一部分 |

---

## 8. 时间规划（以硕士约 2.5 年计）

| 时间 | 任务 |
|---|---|
| 第 1–3 个月 | 精读 2.1 节核心文献；复现 Zou et al. 的人工噪声设计；搭建 EKF 跟踪和 PCRB 计算框架 |
| 第 4–8 个月 | 第一篇快报：广播悖论 + PCRB 隐私指标 + 单时隙到多时隙设计 |
| 第 9–15 个月 | 扩展为期刊长文（加入多目标、强/弱 Eve、鲁棒设计） |
| 第 16–24 个月 | 第二篇：轨迹欺骗；或第三篇：AFDM 参数跳变 |
| 第 25–30 个月 | 学位论文撰写 |

---

## 9. 目标期刊与会议

- **期刊：** IEEE TIFS（安全类首选）、IEEE TVT、IEEE TWC、IEEE TSP、IEEE WCL / SPL（快报）
- **会议：** IEEE ICC、Globecom、VTC、ICASSP、SPAWC、IEEE CNS（偏安全时）

---

## 10. 参考文献与链接

**感知隐私 / 感知安全**
1. J. Zou, C. Masouros, F. Liu, S. Sun, Securing the Sensing Functionality in ISAC Networks: An Artificial Noise Design, IEEE TVT, 2024：https://arxiv.org/pdf/2312.00981
2. K. Han, K. Meng, C. Masouros, Sensing-Secure ISAC: Ambiguity Function Engineering for Impairing Unauthorized Sensing, arXiv:2510.02103：https://arxiv.org/pdf/2510.02103
3. B. Du, K. Han, C. Masouros, Securing the Sensing Functionality in ISAC: KLD-Based Ambiguity Function Shaping, arXiv:2512.19974：https://arxiv.org/pdf/2512.19974
4. Sub-Sampling for Positioning Privacy in ISAC: Deception by Aliasing via Sparse Arrays and Pilots, arXiv:2608.07206：https://arxiv.org/pdf/2608.07206
5. Exploiting Phase Noise for Sensing Privacy in ISAC Systems, arXiv:2608.13270：https://arxiv.org/pdf/2608.13270
6. Z. Fang, B. Han, S. Li, H. D. Schotten, Waveform Randomization for Secure ISAC, arXiv:2610.07994：https://arxiv.org/pdf/2610.07994
7. Secure OFDM Waveform Design for ISAC: Artificial Phase-Doppler Shifts Against Passive Sensing, arXiv:2602.23861：https://arxiv.org/html/2602.23861
8. Enhancing Sensing Privacy in ISAC Through Joint Signal and Artificial Noise Beamforming, arXiv:2608.15506：https://arxiv.org/pdf/2608.15506
9. Sensing Security in Near-Field ISAC: Exploiting Scatterers, arXiv:2510.20140：https://arxiv.org/pdf/2510.20140
10. Invisible Walls: Privacy-Preserving ISAC Empowered by RIS (PrivISAC), arXiv:2601.04488：https://arxiv.org/html/2601.04488v2
11. AmbSentry: Mitigating Sensing Eavesdropping in ISAC by Harnessing Ambient IoT Devices, arXiv:2608.11799：https://arxiv.org/pdf/2608.11799

**综述与观点**
12. T. Matsumine, H. Ochiai, J. Shikata, Physical Layer Security for ISAC: A Survey, IEEE OJCOMS, 2025：https://arxiv.org/pdf/2504.18097
13. Integrating Sensing and Communications in 6G? Not Until It Is Secure to Do So, arXiv:2503.15243：https://arxiv.org/pdf/2503.15243
14. T. Welling, O. Günlü, A. Yener, Secure ISAC: Information Theory Offers Insights, arXiv:2605.08106：https://arxiv.org/pdf/2605.08106
15. T. Guo, H. Li, Secure Integrated Sensing and Communications (S-ISAC) Network：https://par.nsf.gov/servlets/purl/10636653
16. N. Su, F. Liu, C. Masouros, A. Al Hilli, Security and Privacy in ISAC Systems（书章）：https://scholar.hit.edu.cn/en/publications/security-and-privacy-in-isac-systems/

**跟踪与安全（用途不同，用于对比）**
17. J.-H. Hong, C. Son, S.-H. Lee, Tracking-Assisted Robust Secure Transmission Against a Mobile Eavesdropper in Cell-Free ISAC, arXiv:2608.06781：https://arxiv.org/pdf/2608.06781
18. Joint Beamforming Optimization and Dynamic Tracking in RIS-Enabled Secure ISAC, arXiv:2609.22307：https://arxiv.org/pdf/2609.22307
19. P. Liu et al., Securing Multi-User Uplink Communications Against Mobile Aerial Eavesdropper via Sensing, IEEE TVT, 2023：https://unpaywall.org/10.1109%2FTVT.2023.3248063
20. J. Wu, W. Yuan, L. Hanzo, When UAVs Meet ISAC: Real-Time Trajectory Design for Secure Communications：https://arxiv.org/pdf/2306.14140
21. Balancing Functionality and GDPR-Driven Privacy in ISAC Trajectory Sharing, arXiv:2604.08743：https://arxiv.org/html/2604.08743v2
22. 对上文的第三方评审（关于快照 CRB 能否约束轨迹重建）：https://pith.science/paper/2604.08743

**AFDM 安全**
23. P. Wang et al., A Secure Affine Frequency Division Multiplexing System for Next-Generation Wireless Communications, arXiv:2510.02023：https://arxiv.org/abs/2510.02023v2
24. Making AFDM Secure Against Eavesdroppers: A Phase Function Design Approach, arXiv:2605.14837：https://arxiv.org/pdf/2605.14837
25. D. Zhang et al., Parameter Design for Secure Affine Frequency Division Multiplexing Waveform, arXiv:2503.19364：https://export.arxiv.org/pdf/2503.19364
26. AFDM-Enabled ISAC in Dynamic Environments: Fundamentals, Technologies and Opportunities, arXiv:2609.04876：https://arxiv.org/pdf/2609.04876
27. H. Yin et al., From OFDM to AFDM: Enabling Adaptive ISAC in High-Mobility Scenarios, IEEE Wireless Communications, 2026：https://discovery.ucl.ac.uk/id/eprint/10230293/

**车联网安全 ISAC（场景参考）**
28. Waveform Design for Vehicular ISAC Systems Via Secrecy Rate Maximization, IEEE TITS, 27(7)：https://trid.trb.org/View/2735020
29. ISAC-OTFS Enabled Secure Transmission Against Co-Existing Internal and External Eavesdroppers in Vehicular Networks, IEEE ICEICT 2025：https://pure.nwpu.edu.cn/en/publications/isac-otfs-enabled-secure-transmission-against-co-existing-interna/
