# 方案5：交叉口多RSU协同ISAC——通信/感知“双切换”与遮挡感知的动态角色分配

> 一句话概括：在城市交叉口部署多个具备 ISAC 能力的 RSU，让它们根据预测到的遮挡情况和前传容量，动态决定“谁照射、谁接收、谁服务通信”。对网联车，同时完成**通信链路切换**和**感知航迹交接**这两件事；对行人等非网联目标，保证航迹连续不断。

---

## 1. 为什么值得做

### 1.1 单个 RSU 在交叉口不够用

- 交叉口是遮挡最严重的地方：建筑物拐角、大货车、公交车都会挡住视线。单个 RSU 的单基地感知，一旦目标被挡住就会丢失航迹。
- 行人、骑行者等弱势道路使用者（VRU）约占全球城市交通死亡人数的一半，其中交叉口占比尤其高（见参考文献 25），而且他们通常**不会主动发送 V2X 消息**，只能靠网络“看见”。欧洲 6G-DISAC 项目的架构论文就把“智能交叉口的 VRU 保护”作为分布式 ISAC 的两个代表用例之一（arXiv:2504.12765）。
- 3GPP Rel-20 的车辆感知评估场景包括 Urban Grid（城市网格），本身就以路口为主要几何结构（RAN1#125 主持人总结草案）。

### 1.2 多节点协同已有基础，但各条线是分开做的

- **通信切换（用感知辅助）：** 让空闲 RSU 提前感知车辆状态，做到近乎“无感切换”。这一思路在 Liu 等的 ISAC 综述（arXiv:2108.07165）中已有讨论，后续 Li 等给出了与 5G NR 兼容的完整方案。
- **感知航迹交接：** 分布式 ISAC 中，目标从一个基站的视野走到另一个基站的视野，航迹需要交接，这是 Wymeersch 团队近两年的工作重点。
- **网络化跟踪与资源分配：** 用后验 CRB（PCRB）作为指标，优化多基站波束和目标-基站关联（Liang Liu 团队，2026）。
- **前传受限：** 多节点感知要把数据汇聚到中心单元，而前传容量有限，需要压缩和量化设计。

问题在于：**这几条线基本是各做各的**。而在交叉口，一辆网联车既是通信用户又是感知目标，两种“切换”是耦合的；遮挡变化又同时影响通信和感知。把它们放在同一个框架里统一设计，正是本方案的切入点。

---

## 2. 相关工作梳理

| 方向 | 代表工作 | 做了什么 | 局限 / 与本方案的关系 |
|---|---|---|---|
| 感知辅助的**通信切换** | Y. Li, F. Liu, …, C. Masouros, *Look Before Switch*, IEEE TMC, 2025 | 两种切换触发算法：基于估计位置的距离触发，以及基于 IMM-EKF 机动预测的概率触发；给出与 5G NR 兼容的帧结构和协议；无需上行反馈和波束扫描 | 只关注通信链路切换；单目标视角；未考虑感知航迹的交接 |
| 同上（会议版） | Y. Li, F. Liu, C. Masouros, *Beyond RSRP* | 在十字路口射线追踪场景中，切换中断时间降低约 76% | 同上 |
| **感知航迹交接** | Y. Ge, …, H. Wymeersch, *Target Handover in DISAC*, arXiv:2411.01871 | 用 TPMBM 滤波器做多目标跟踪，研究何时、向谁、分享什么航迹信息 | 只做感知，不涉及通信切换；各基站单基地 |
| 同上 | L. Bai, Y. Ge, H. Wymeersch, BP-based Target Handover, Globecom 2025 | 基于置信传播的航迹交接，性能接近集中处理，同时显著减少数据交换 | 同上 |
| ISAC 移动性管理 | Mobility Management in ISAC Networks, arXiv:2501.08159 | 提出“感知切换”的概念框架，包括在单基地和双基地之间切换感知模式 | 概念层面，缺少具体优化 |
| **网络化跟踪 + PCRB** | Y. Hu, …, L. Liu, *Networked Tracking of Multiple Moving Targets in 6G*, arXiv:2604.19709 | 设计网络化卡尔曼滤波器，推导 PCRB，以 PCRB 最小化为目标优化各基站波束，实现目标到基站的动态关联 | 未考虑遮挡的突变、通信切换和前传限制 |
| 多基站 ISAC 资源分配 | Cooperative BS Assignment and Resource Allocation, arXiv:2509.10240 | 用 PCRB 和可达速率做基站分配及功率带宽分配 | 无遮挡建模 |
| 基站选择 | Y. Xu et al. (HKUST), Joint BS Selection, User Association, and Beamforming, arXiv:2305.05265 | 联合优化哪些基站做感知接收、用户关联和波束；被选作感知接收的基站不能再服务通信用户 | 静态场景，未考虑跟踪 |
| **前传受限的协同感知** | Joint Transmission and Compression for Networked Sensing, arXiv:2408.03174 | 以 PCRB 为指标，联合优化发射策略和前传压缩策略 | 未结合车辆场景和遮挡 |
| 同上 | Cooperative Sensing With Limited Backhaul, arXiv:2404.03440 | 用 KLT + Lloyd 量化，只回传估计时延附近的少量采样 | 同上 |
| 同上 | C. Eckrich, A. M. Zoubir, V. Jamali, Fronthaul-Constrained Distributed Radar Sensing, Globecom WS 2024 | 联合前传压缩和时间分配，最小化 CRB | 纯雷达网络 |
| 多 RSU 波束跟踪 | An ISAC-Based Beam Tracking Scheme Against Inter-Region Interference for Multi-RSU V2I, IEEE TVT, 2024 | 多 RSU 场景下的区域间干扰处理 | 侧重通信波束 |
| 交叉口分布式 ISAC | W. Liu, Y. Deng, Goal-Oriented Semantic Communication for Distributed ISAC-Enabled Vehicle Coordination, arXiv:2607.15111 | 无信号灯交叉口，4 个 RSU 通过光纤连到中心基站，做感知融合和车辆协同控制，实现无碰撞通行 | 关注控制和语义通信，不涉及切换和遮挡 |
| 目标-用户关联 | Predictive Target-to-User Association via Hybrid-Field ISAC, arXiv:2501.10676 | 用 IMM + CT 模型处理复杂道路几何和车辆机动下的“哪个回波是哪个用户” | 单 RSU |
| 分布式 V2V ISAC | Q. Li et al., Distributed ISAC Resource Allocation for V2V Detection and Tracking, IEEE TVT, 2026 | 车辆层面分布式功率带宽分配，兼顾非网联车检测和网联车 PCRB 跟踪 | V2V 视角，可作为扩展参考 |
| 动态遮挡预测 | WM4ISAC, arXiv:2610.08267 | 用世界模型从回波中学习环境动态，预测遮挡和 LoS/NLoS 切换 | 单基站，指出多基站切换仍待研究 |

**查新结论（截至 2026 年 11 月初）：** 在我们的检索范围内，以下问题尚无系统性研究：
1. **通信切换和感知航迹交接的联合设计**。现有工作要么只做通信切换（Li et al.），要么只做航迹交接（Ge/Bai et al.）。
2. **以“网络自身感知到的遮挡物”来预测遮挡，并据此提前分配 RSU 角色**。
3. **在前传受限条件下，为每个目标自适应选择融合层级**（只传航迹 / 传测量 / 传压缩后的原始采样）。

---

## 3. 核心思路

### 3.1 “双切换”：通信链路和感知航迹一起交接

对一辆网联车 $j$，交叉口网络同时维护两样东西：
- **通信服务节点** $s_j(t)$：当前由哪个 RSU 为它传数据；
- **感知航迹** $\mathcal T_j(t)$：它的状态估计（均值 + 协方差），以及由哪些 RSU 负责观测。

现有做法是两件事各自触发、各自交接，可能出现“通信已经切到 RSU B，但航迹还在 RSU A，B 只能盲扫”的情况。本方案的做法是：**通信切换以航迹为依据，航迹交接随通信切换同步完成**。

- 切换触发：不再只看 RSRP，而是基于航迹预测出的未来 $T$ 秒内的“通信 SNR 预测值 + 感知信息增益（PCRB 下降量）”。
- 交接内容：传递航迹置信状态（均值和协方差，可压缩），新服务节点直接用它对准波束，省去初始接入时的波束扫描。

对于非网联目标（行人、未装 V2X 的车），只有感知航迹，交接问题退化为纯航迹交接，可以复用同一套机制。

### 3.2 用感知到的遮挡物预测遮挡

大货车、公交车本身就是网络在跟踪的目标。既然知道了它们的位置、尺寸和速度，就能预测未来一段时间内，哪些 RSU 到哪些目标的视线会被挡住。这是 ISAC 独有的“自举”能力：**感知结果不仅服务于被感知的对象，还用来预测其他目标的可见性**。

可见性的建模思路：
- 静态遮挡：来自路口数字地图（建筑轮廓），预先算好每个 RSU 的视域。
- 动态遮挡：把已跟踪的大车建模为二维矩形或三维长方体，用其预测轨迹计算视线是否相交。由于大车位置本身有不确定性，得到的是**可见概率** $\nu_{k,j}(t) \in [0,1]$，而非确定的 0/1。

### 3.3 动态角色分配

每个时隙，每个 RSU $k$ 被分配一个角色：

$$
r_k(t) \in \{\text{单基地 ISAC},\ \text{双基地发射},\ \text{双基地接收},\ \text{仅通信}\}.
$$

选择依据是：可见概率、几何构型（双基地角对定位精度的影响）、通信负载和前传容量。HKUST 的工作已经指出，被选作感知接收的基站不能同时服务通信用户，这种耦合在路口多 RSU 场景下同样存在。

### 3.4 前传感知的融合层级选择

对每个目标，RSU 可以向中心单元上报三种层级的信息：
1. **航迹级**：只报状态估计，数据量最小，但融合增益有限；
2. **测量级**：报时延、角度、多普勒等参数估计；
3. **信号级**：报目标附近的压缩原始采样（参考 arXiv:2404.03440 的 KLT + Lloyd 量化思路），融合增益最大，但最占前传。

几何好、SNR 高的目标，航迹级就够了；几何差或者刚从遮挡中出现的目标，值得花前传资源传信号级数据。

---

## 4. 研究问题

**Q1 双切换机制：** 如何定义联合触发准则？交接时传递哪些信息、如何压缩？对齐 NR 的切换流程需要哪些信令改动？

**Q2 遮挡感知的角色分配：** 如何把可见概率纳入 PCRB？如何建立“角色 + 波束 + 功率 + 前传”的联合优化问题，并在交叉口实时求解（每 10–100 ms 一次）？

**Q3 融合层级选择：** 在总前传容量约束下，为每个目标选择融合层级，问题本质是带约束的混合整数规划，需要设计低复杂度算法。

**Q4 优先级与公平性：** VRU 的跟踪精度应该优先保障。可以在目标函数中对不同类别目标加权，或者对 VRU 设置硬约束。

**Q5（扩展）网联车作为接收节点：** 把车载 UE 也纳入感知接收端（UE-TRP 或 TRP-UE 双基地），与方案3衔接。

---

## 5. 系统模型（建议写法）

**场景：** 四路交叉口，$K$ 个 RSU（例如每个路口角一个），通过容量为 $C_k$ 的前传连到边缘中心单元（CU）。网联车集合 $\mathcal J_c$，非网联目标集合 $\mathcal J_n$（含 VRU）。

**目标运动模型：** $\mathbf x_j(t+1) = \mathbf F \mathbf x_j(t) + \mathbf w_j(t)$，直行用 CV 模型，转弯用 CT 模型，也可以用 IMM 混合。

**测量模型：** RSU $k$ 对目标 $j$ 的测量
$$
\mathbf z_{k,j}(t) = \nu_{k,j}(t)\, \mathbf h_{k,j}\big(\mathbf x_j(t); r_k, r_{k'}\big) + \mathbf n_{k,j}(t), \quad \mathbf n_{k,j} \sim \mathcal N\big(\mathbf 0, \mathbf R_{k,j}(\mathbf w_k, p_k, C_k)\big),
$$
其中 $\mathbf h$ 取决于单基地还是双基地（双基地时与配对的 $k'$ 有关），$\nu_{k,j}$ 是可见性，测量噪声协方差 $\mathbf R$ 由波束 $\mathbf w_k$、功率 $p_k$ 和前传量化失真共同决定。

**PCRB 递推（以期望可见性近似）：**
$$
\mathbf J_j(t) = \big(\mathbf F \mathbf J_j(t-1)^{-1} \mathbf F^{\mathsf T} + \mathbf Q\big)^{-1} + \sum_{k} \bar\nu_{k,j}(t)\, \mathbf H_{k,j}^{\mathsf T} \mathbf R_{k,j}^{-1} \mathbf H_{k,j},
$$
$\mathbf H_{k,j}$ 为测量函数的雅可比矩阵，$\bar\nu$ 为可见概率。PCRB 为 $\mathbf J_j(t)^{-1}$。

**优化问题（示意）：**
$$
\min_{\{r_k\}, \{\mathbf w_k\}, \{p_k\}, \{\ell_{k,j}\}} \ \sum_{j} \omega_j \, \mathrm{tr}\big(\mathbf J_j(t)^{-1}\big)
\quad \text{s.t.}\quad R_i \ge \bar R_i\ (i \in \mathcal J_c),\ \ \sum_j B(\ell_{k,j}) \le C_k,\ \ \|\mathbf w_k\|^2 \le P_k,
$$
其中 $\ell_{k,j}$ 是融合层级，$B(\cdot)$ 是对应的前传开销，$\omega_j$ 对 VRU 取更大值。

> 求解建议：先固定角色（离散变量），对波束和功率用 SCA/SDR 求解；离散部分用贪心或分支定界。若追求实时性，可以训练 GNN 学习离散决策，这也是论文的一个可选亮点。

---

## 6. 分阶段研究计划

### 第一篇：交叉口的通信/感知双切换

- 场景：2–4 个 RSU，网联车转弯穿越路口，存在静态建筑遮挡。
- 内容：联合触发准则 + 航迹置信状态交接；与 NR 切换流程对齐的信令设计。
- 对比基线：
  - RSRP 切换 + 独立跟踪；
  - Li et al.（TMC 2025）的感知辅助通信切换 + Ge et al. 的航迹交接，**两者分开运行**；
  - 集中式全信息上界。
- 指标：切换中断时间、切换失败率、吞吐、航迹 ID 切换次数、航迹丢失率。
- 目标：IEEE TVT（短文或长文）/ Globecom / VTC。

### 第二篇：遮挡感知的动态角色分配 + PCRB 优化

- 引入动态遮挡（被跟踪的大车）和可见概率；联合优化角色、波束、功率。
- 对比基线：静态角色、就近 RSU、Hu et al. 的 PCRB 波束设计（不考虑遮挡）。
- 目标：IEEE TWC / TVT。

### 第三篇（可选）：前传受限下的融合层级自适应

- 每个目标在航迹级、测量级、信号级之间自适应选择；与 arXiv:2408.03174 的压缩方案对比。
- 目标：IEEE TCOM / JSAC 特刊。

---

## 7. 仿真方案

### 7.1 工具链

| 用途 | 工具 |
|---|---|
| 交通流与路口几何 | SUMO（可以导入真实路口的 OpenStreetMap） |
| 遮挡与信道 | Sionna RT 或 MATLAB 射线追踪；也可以用 3GPP TR 38.901 ISAC 信道模型加上自定义遮挡判断 |
| 多目标跟踪 | 先用 EKF/IMM + GNN 数据关联起步；进阶可用 PMBM/TPMBM（参考 Ge et al.） |
| 优化 | CVX / MOSEK（SDR、SCA），PyTorch Geometric（GNN 调度，可选） |

### 7.2 建议参数

| 参数 | 取值 |
|---|---|
| 载频 / 带宽 | 28–30 GHz / 200–400 MHz（对齐 3GPP Urban Grid 30 GHz） |
| RSU 数量 / 天线 | 4 个 / 每个 32–64 元 UPA |
| 前传容量 | 0.1–10 Gbps 扫描 |
| 目标 | 10–30 辆车（其中 10–20% 为大车）+ 5–10 个行人 |
| 时隙 | 10–50 ms 做一次角色决策 |

### 7.3 评价指标

- **感知：** 每类目标的 RMSE 和 PCRB、GOSPA、航迹丢失率、航迹 ID 切换次数，以及 VRU 从走出遮挡到被首次检测的时延
- **通信：** 吞吐量、切换中断时间、切换失败率
- **系统：** 前传占用、优化求解时间

---

## 8. 风险与应对

| 风险 | 应对 |
|---|---|
| 问题太大，难以在硕士期间做完 | 第一篇只做双切换（2 个 RSU、静态遮挡），已经足够成文；后两篇按进度取舍 |
| 射线追踪计算量大 | 先用几何遮挡判断（线段与矩形求交）代替，射线追踪只用于最终验证 |
| 可见性为随机变量，PCRB 不好处理 | 用期望 FIM 近似（如第 5 节），或改写为机会约束；在论文中说明近似条件 |
| 与 Hu et al.、Ge et al. 重叠 | 明确定位为“通信 + 感知联合”和“遮挡预测驱动”，在相关工作部分逐条对比 |

---

## 9. 时间规划（以硕士约 2.5 年计）

| 时间 | 任务 |
|---|---|
| 第 1–3 个月 | 精读核心文献；搭建 SUMO + 几何遮挡 + 单 RSU EKF 跟踪的仿真框架 |
| 第 4–8 个月 | 第一篇：双切换机制，投会议 |
| 第 9–16 个月 | 第二篇：动态遮挡 + 角色分配 + PCRB 优化，投期刊 |
| 第 17–24 个月 | 第三篇（前传融合层级），或把第一篇扩展为期刊长文 |
| 第 25–30 个月 | 学位论文撰写 |

---

## 10. 目标期刊与会议

- **期刊：** IEEE TVT、IEEE TWC、IEEE TMC（偏协议和系统时）、IEEE TCOM、IEEE TITS（偏交通应用时）
- **会议：** IEEE ICC、Globecom、VTC、WCNC、INFOCOM（偏网络时）

---

## 11. 参考文献与链接

**切换与航迹交接**
1. Y. Li, F. Liu, H. Xiong, Z. Wang, Narengerile, C. Masouros, Look Before Switch: Sensing-Assisted Handover in 5G NR V2I Networks, IEEE TMC, 2025：https://discovery.ucl.ac.uk/id/eprint/10219848/
2. Y. Li, F. Liu, C. Masouros, Beyond RSRP: A Sensing-Assisted Handover Framework in V2I Networks：https://discovery.ucl.ac.uk/10219238/1/a701-li%20paper.pdf
3. Y. Ge et al., Target Handover in Distributed Integrated Sensing and Communication, arXiv:2411.01871：https://export.arxiv.org/abs/2411.01871
4. L. Bai, Y. Ge, H. Wymeersch, Belief Propagation-based Target Handover in DISAC, IEEE Globecom, 2025：https://research.chalmers.se/publication/551819/file/551819_Fulltext.pdf
5. Mobility Management in Integrated Sensing and Communications Networks, arXiv:2501.08159：https://arxiv.org/pdf/2501.08159
6. Distributed Intelligent Sensing and Communications for 6G: Architecture and Use Cases, arXiv:2504.12765：https://arxiv.org/pdf/2504.12765
7. F. Liu et al., Integrated Sensing and Communications: Towards Dual-functional Wireless Networks for 6G and Beyond, arXiv:2108.07165：https://arxiv.org/pdf/2108.07165

**网络化跟踪与资源分配**
8. Y. Hu, W. Zhu, C. Wu, S. Zhang, J. A. Zhang, L. Liu, Networked Tracking of Multiple Moving Targets in 6G Network, arXiv:2604.19709：https://arxiv.org/html/2604.19709v1
9. Cooperative Base Station Assignment and Resource Allocation for 6G ISAC Network, arXiv:2509.10240：https://arxiv.org/html/2509.10240v2
10. Y. Xu, D. Xu, L. Xie, S. Song, Joint BS Selection, User Association, and Beamforming Design for Network ISAC, arXiv:2305.05265：https://ar5iv.labs.arxiv.org/html/2305.05265
11. L. Wang, L. F. Abanto-Leon, Resource Allocation for ISAC Networks with Application to Target Tracking, arXiv:2412.20314：https://arxiv.org/pdf/2412.20314
12. Q. Li et al., Distributed ISAC Resource Allocation for V2V Detection and Tracking, IEEE TVT, 2026：https://eprints.gla.ac.uk/387620/
13. Y. Guo et al., Predictive Beam Tracking and Power Allocation With Cooperative Sensing for V2I, IEEE OJCOMS, 2024：https://doaj.org/article/fbee78486313456eade3653f9d27be96

**前传受限的协同感知**
14. Joint Transmission and Compression Optimization for Networked Sensing with Limited-Capacity Fronthaul Links, arXiv:2408.03174：https://arxiv.org/html/2408.03174v3
15. Design and Optimization of Cooperative Sensing With Limited Backhaul Capacity, arXiv:2404.03440：https://arxiv.org/pdf/2404.03440
16. C. Eckrich, A. M. Zoubir, V. Jamali, Fronthaul-Constrained Distributed Radar Sensing, IEEE Globecom Workshops, 2024：https://arxiv.org/pdf/2409.17753
17. Networked ISAC with Fronthaul Compression, arXiv:2408.08057：https://www.arxiv.org/pdf/2408.08057

**多 RSU、交叉口与遮挡**
18. An ISAC-Based Beam Tracking Scheme Against Inter-Region Interference for the Multi-RSU V2I Scenario, IEEE TVT, 2024, DOI: 10.1109/TVT.2024.3488089
19. W. Liu, Y. Deng, Goal-Oriented Semantic Communication for Distributed ISAC-Enabled Vehicle Coordination, arXiv:2607.15111：https://arxiv.org/pdf/2607.15111
20. Predictive Target-to-User Association in Complex Scenarios via Hybrid-Field ISAC Signaling, arXiv:2501.10676：https://arxiv.org/html/2501.10676v2
21. Z. Xiao, L. Wu, B. Shankar M. R., WM4ISAC: World Model for Proactive ISAC Under Dynamic Blockage, arXiv:2610.08267：https://arxiv.org/pdf/2610.08267
22. Cell-Free ISAC: Principles, Advances, and Future Directions, arXiv:2502.20345：https://arxiv.org/html/2502.20345v2
23. T. Yang, S. Li, Y. Song, K. Zhi, G. Caire, Cooperative Multistatic Target Detection in Cell-Free Communication Networks, arXiv:2410.16140：https://arxiv.org/html/2410.16140v1

**标准与背景**
24. 3GPP RAN1#125 ISAC 评估主持人总结草案（2026 年 5 月）：https://www.3gpp.org/ftp/meetings_3gpp_sync/RAN1/Inbox/drafts/10.8(ISAC)/10.8.1%20Evaluations/
25. P. Anowar, An Integrated Roadside Sensing and Communication Framework for VRU Safety at Signalized Intersections, arXiv:2606.07016：https://arxiv.org/pdf/2606.07016
