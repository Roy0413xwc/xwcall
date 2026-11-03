# 车联网 ISAC 开题方向深度筛选报告

本次核心结论：我更建议你以方向二为主线，以方向一中的异步双基地感知作为关键技术储备，而不是直接把两个完整课题拼在一起。

理由是：你的就业目标是 AI 技术与通信交叉，而不仅仅是传统通信信号处理。多 RSU 协同 ISAC 更容易形成一套完整的 AI-RAN 技术能力，包括多节点协同、无线资源调度、目标跟踪、预测决策、强化学习和边缘智能。

但方向二也有一个必须正视的问题：2025—2026 年已经出现多基站 ISAC 资源分配、分布式目标航迹交接、动态遮挡下的多基站跟踪等研究。不能再把「多 RSU + 强化学习 + 资源分配」本身作为创新点。

下面我按文献查新、创新空间、数学模型、AI 技术路线、仿真实现和就业价值六个方面进行比较。

推荐研究主线

多 RSU 协同 ISAC + 不确定性感知的联合切换决策。

## 一、文献查新：两个方向目前发展到什么程度？

先明确一个原则：已有论文不意味着不能开题，关键是你的研究问题、数学模型、优化目标和解决方法是否有明确区别。

本次查新以 IEEE TWC、TCom、TVT、TMC、JSAC、IEEE WCL、GLOBECOM、ICC，以及 2025—2026 年相关预印本为重点。检索截止日期为 2026 年 11 月 2 日。

### 1. 方向一：异步双基地 ISAC

这个方向的核心不是简单的双基地感知，而是：

如何在发射端和接收端不同步、发射车辆自身移动、车辆位置存在误差的情况下，准确感知其他车辆和行人？

这是一个真实的信号处理问题。

#### 关键文献

|文献|发表时间及期刊|主要研究内容|对你的启发|
|---|---|---|---|
|Sensing in Bistatic ISAC Systems With Clock Asynchronism|IEEE SPM, 2024|系统梳理双基地时钟不同步问题|异步双基地理论基础|
|Bistatic Doppler Frequency Estimation With Asynchronous Moving Devices|IEEE WCL, 2024|研究收发设备移动且时钟不同步时的多普勒估计|已经解决了部分设备运动与时钟耦合问题|
|User Equipment Assisted Localization for 6G ISAC|arXiv, 2023|利用 UE 辅助定位，考虑 GPS 位置误差和同步误差|与车辆自报状态作为先验有较大关联|
|Time-Varying Offset Estimation for Clock-Asynchronous Bistatic ISAC Systems|arXiv, 2025|通过 LoS 几何特征和 EKF 联合估计 TO、CFO|不能简单把时钟估计作为全新的创新点|
|Multistatic Sensing for Target Localization in ISAC Systems with Dynamic and Unknown-Location Transmitters|IEEE TVT, 2026|联合跟踪移动目标和未知位置的动态发射端|与移动车辆作为发射锚点的研究存在交叉|
|ISAC for Vehicles: Bistatic Radar With 5G-NR Signals|IEEE TVT, 2025|使用 5G NR 信号进行车辆双基地雷达感知|提供车辆场景的信号模型和基线|

文献来源：

IEEE Signal Processing Society+5

其中有三篇尤其值得精读：

第一篇：Wu 等，IEEE Signal Processing Magazine，2024。

这篇文章是异步双基地 ISAC 的重要综述，应该作为方向一的第一篇入门文献。它把不同步引起的随机相位、时延偏差和频偏问题进行了系统梳理。

第二篇：Ventura 等，IEEE WCL，2024。

这篇论文考虑了移动设备和异步时钟同时存在的情况，利用多径分量之间的相位不变性和双基地几何关系估计目标多普勒。

这意味着你的研究不能只说：

> 我考虑了车辆移动引起的多普勒和时钟偏差。

因为这部分已经有研究。

第三篇：Zhuge 等，IEEE TVT，2026。

这篇论文已经研究动态、未知位置发射端条件下的多基地目标定位，同时估计移动目标和发射端位置。

因此，方向一真正需要区分的是：车辆周期广播的状态信息是否能够成为一种有时间戳、有误差、有延迟的随机先验，并与无线测量共同完成状态和时钟估计。

#### 方向一还剩下什么创新空间？

我认为存在一个值得深入研究的切入点：

利用 V2X 自报运动状态辅助异步双基地感知。

这里有一个很好的标准基础：ETSI CAM 消息可以携带车辆位置、运动状态和时间信息，车辆 CAM 生成间隔可以在 100 ms 到 1000 ms 之间动态变化，而且标准规定了时间戳和部分数据的置信度信息。

ETSI+1

这给出了一个非常具体的问题：

- 无线 SRS 测量可以在毫秒级更新。
    
- CAM/BSM 提供的是低频车辆运动状态。
    
- 两种信息的时间尺度不同。
    
- CAM 可能存在 GNSS 偏差和传输延迟。
    
- 无线测量又受到时钟偏差和多普勒影响。
    

目前这次定向检索没有发现与以下完整方案完全相同的研究：

将 CAM/BSM 作为带时间戳、延迟和不确定性的侧信息，放入异步双基地 ISAC 的发射车状态、时钟参数和被动目标状态联合估计框架。

这不是证明全球没有相关论文，而是一个值得继续查新的具体候选空白。

方向一的创新潜力

它的主要优势是理论问题明确，能够推导可辨识条件、贝叶斯 CRB/PCRB，并设计多速率鲁棒状态估计算法。

但它有一个明显缺点：AI 不是这个问题天然的核心工具。

如果想突出 AI，需要进一步研究学习辅助的鲁棒滤波、噪声统计估计或可微分因子图。这些是可以做的，但不能为了使用深度学习而强行增加神经网络。

### 2. 方向二：多 RSU 协同 ISAC

这个方向的研究范围更广，核心问题是：

如何让多个 RSU 协同完成车辆通信、目标感知和连续跟踪，并利用 AI 决定不同 RSU 在不同时间应该承担什么任务？

这里有一个重要发现：你之前设想的多 RSU 方案中，部分创新点已经被 2025—2026 年的新论文覆盖。

#### 关键文献查新

文献 1：An ISAC-Based Beam Tracking Scheme Against Inter-Region Interference for the Multi-RSU V2I Scenario

与你们课题组研究基础直接相关

IEEE Transactions on Vehicular Technology, 2025, DOI: 10.1109/TVT.2024.3488089

[Radar-Assisted Multiple Base Station Cooperative mmWave Beam Tracking](https://images.openai.com/static-rsc-4/HCwWu3GthG8Hvcduv8LxtDWPf73Sr4E99y82EJyzaM21NoCHAnem1gigRJyctKXtayYkJSCu_YY3xtRjuT1bKA1N_wfnbtbpBAz2R16G6GW85i614BDDaCw2VHNPkZ6RwkbF2WuZyyyknsR7ZImK-YXJ5JjRRUlK_UBtUFKBJOA?purpose=inline)

主要内容：

- 多 RSU 协同服务车辆。
    
- 使用 UKF 预测车辆状态。
    
- 根据预测车辆集合进行资源分配。
    
- 以 PCRB 为指标优化跟踪精度。
    
- 采用 CoMP 缓解区域间干扰。
    

对你的影响： 不能再将「多 RSU + UKF + PCRB + 联合资源分配」作为主要创新点。

Request PDF+1

文献 2：A Rate-Splitting Multiple Access Enabled Cooperative ISAC Tracking System for Complex V2I Scenarios

尤其需要阅读

IEEE Transactions on Vehicular Technology, 2026, Vol. 75, No. 3, pp. 4032–4048

这是徐少毅等团队的相关工作。

主要内容：

- 多基站协同 ISAC 跟踪。
    
- IMM-UKF 与加权最小二乘。
    
- 单载波和多载波 RSMA 协同传输。
    
- 基于图论的车辆分组。
    
- 根据预测状态进行动态功率分配。
    

对你的影响： 复杂车辆轨迹、多基站协同跟踪、RSMA 和预测状态辅助资源分配已经有较好的研究基础。你的开题应该从新的网络决策问题切入，而不是重新搭建一套相似的跟踪与资源优化系统。

ResearchGate+1

文献 3：Look Before Switch: Sensing-Assisted Handover in 5G NR V2I Networks

IEEE Transactions on Mobile Computing, DOI: 10.1109/TMC.2025.3647295

主要内容：

- 利用 ISAC 感知结果辅助通信切换。
    
- 使用车辆位置和 IMM-EKF 预测机动行为。
    
- 提出距离触发和概率触发两种切换方法。
    
- 仿真中平均切换中断时间降低超过 50%。
    

对你的影响： 感知辅助通信切换本身已经有比较成熟的研究。

UCL Discovery

文献 4：Target Handover in Distributed Integrated Sensing and Communication

IEEE ICC, 2025

主要内容：

- 多基站之间进行目标航迹交接。
    
- 使用 TPMBM 多目标跟踪。
    
- 研究何时、向哪个基站以及传递哪些航迹信息。
    

对你的影响： 感知航迹交接也已经成为独立研究方向。

IEEE Xplore

文献 5：Belief Propagation-based Target Handover in Distributed ISAC

IEEE GLOBECOM, 2025

主要内容：

- 利用因子图表达多目标跟踪。
    
- 通过置信传播实现分布式航迹交接。
    
- 在保持跟踪精度的同时减少基站之间的数据交换。
    

2026 年 9 月，相关团队又发布了 Scalable Extended-Target Handover in DISAC，进一步研究事件触发的扩展目标航迹交接和可扩展性。

对你的影响： 单纯把 BP、航迹交接或事件触发交接作为创新点，已经不够。

research.chalmers.se+1

文献 6：Cooperative Base Station Assignment and Resource Allocation for 6G ISAC Network

arXiv, 2025；后续发表于 IEEE TVT, 2026

主要内容：

- 多基站联合分配。
    
- 通信速率与 PCRB 联合优化。
    
- 联合考虑功率和带宽。
    
- 使用交替优化求解非凸问题。
    

对你的影响： 基站选择、功率分配、带宽分配与通感性能权衡也不是空白。

arXiv+1

文献 7：Game-Theoretic Multi-BS Tracking Under Blockage in V2I ISAC Networks

2026 年非常新的相关工作

IEEE/CIC ICCC, 2026

主要内容：

- 多基站联合跟踪和多用户通信。
    
- 考虑 LoS 到 Blockage 的变化。
    
- 利用 UKF、PCRB 和合作博弈分配多基站资源。
    
- 使用 Shapley Value 和加权图博弈确定基站贡献。
    

对你的影响： 不能仅以动态遮挡下的多 RSU 资源分配作为创新点。

IEEE Xplore+1

文献 8：Graph Learning for Cooperative Cell-Free ISAC Systems: From Optimization to Estimation

AI 方向的重要查新文献

IEEE Transactions on Wireless Communications, 2026, Vol. 25, pp. 13992–14008

主要内容：

- 将 Cell-Free ISAC 网络表示为异构图。
    
- 利用动态图学习和 GAT。
    
- 联合优化 AP 模式选择、用户关联、预编码和回波处理。
    
- 同时估计多目标位置与速度。
    

对你的影响： GNN + 多节点 ISAC 已经有 TWC 论文，不能把使用 GNN 本身当作创新。

IEEE Xplore

#### 方向二真正值得研究的空白

把以上论文放在一起，可以发现一个很有意思的现象：

|已有研究|已经解决的问题|
|---|---|
|Look Before Switch|感知辅助通信切换|
|Target Handover|感知航迹交接|
|Multi-RSU Beam Tracking|多 RSU 波束跟踪|
|Cooperative BS Assignment|多基站资源分配|
|Game-Theoretic Multi-BS Tracking|遮挡条件下的多基站协同|
|Graph Learning for Cell-Free ISAC|图学习辅助多节点 ISAC 优化|

还有一篇 Ribeiro 等人 2025 年的 Mobility Management in ISAC Networks，已经从概念层面提出了感知和通信移动性管理，以及单基地、双基地感知模式切换。

arXiv

因此，我建议不要声称「首次提出通信和感知双切换」。

真正值得深入研究的是：

在车辆高速移动、动态遮挡和状态预测不确定的条件下，如何将通信服务节点切换和感知航迹所有权交接作为一个联合决策问题，并利用图强化学习优化长期网络收益？

这与现有研究的区别在于：

1. 不是单独优化通信切换。
    
2. 不是单独优化感知航迹交接。
    
3. 不只是给每个 RSU 分配功率。
    
4. 而是研究两种切换之间的相互影响，以及预测误差对长期决策的影响。
    

这里需要特别强调：这是根据当前检索形成的候选创新切入点，还需要进一步阅读上述论文全文，尤其是它们的系统模型和优化变量，才能完成正式的创新性论证。

## 二、两个方向的创新性比较

结合目前的文献情况，我给出以下评价。

|比较项目|方向一：异步双基地|方向二：多 RSU 协同|
|---|---|---|
|原始问题的新颖程度|4.5/5|3.5/5|
|理论创新空间|4.5/5|4/5|
|AI 融合自然程度|3/5|4.5/5|
|强化学习应用空间|2.5/5|4.5/5|
|数学建模深度|4.5/5|4.5/5|
|与现有课题组研究衔接|4/5|5/5|
|AI+通信就业匹配度|3.5/5|5/5|

以上是选题决策评分，不是论文质量或录用概率的统计结果。

我的判断：

- 如果你未来想做无线信号处理、雷达感知、定位算法，方向一更有优势。
    
- 如果你未来想做 AI-RAN、无线网络智能优化、边缘智能、通信算法工程师，方向二更合适。
    
- 如果你想做通信理论与 AI 算法结合，方向二更容易形成完整的算法研发项目。
    

## 三、推荐方向的数学建模

我建议将方向二缩小为一个核心问题：

通信服务节点与感知跟踪节点的联合切换。

不要一开始就同时研究 RSMA、波束成形、功率分配、前传压缩、多目标检测和世界模型。这样容易变成几个已有方向的简单堆叠。

### 1. 系统场景

[Traffic Signals & ITS | Town of Cary](https://images.openai.com/static-rsc-4/5kOoP5_9Ca_BfnMb-fK4gYXfO1mIM2kgjKRu7SdjrClk1DfKkj9nVKwRaeVY4gnbJFw3yjwqz8peqhe5lp0kgMC3TJ0Mn84r59AuyV89OBJUldradhQQbnp2hWZkZ4IlF-3BcNv-QxKj-ajllABFpO-OwYaBZL4XqKJi9I8zph8?purpose=inline)

[carync.gov](https://www.carync.gov/services-publications/traffic/traffic-signals?utm_source=chatgpt.com)

建立一个城市十字路口场景：

- 部署 \(K=4\) 个 RSU，分别位于路口四个方向。
    
- 存在多辆网联车辆和非网联车辆。
    
- 车辆在行驶过程中可能被建筑物、大型货车和公交车遮挡。
    
- 每个 RSU 具备通信和 ISAC 感知能力。
    
- RSU 之间通过前传连接到边缘控制中心。
    

系统需要同时维护两种关系：

|类型|变量|物理意义|
|---|---|---|
|通信关联|\(a_{i,k}(t)\)|车辆 \(i\) 当前由哪个 RSU 提供通信服务|
|感知关联|\(s_{j,k}(t)\)|目标 \(j\) 当前由哪个 RSU 负责主要跟踪|

其中：

\[ a_{i,k}(t),s_{j,k}(t)\in\{0,1\} \]

对于单个通信用户和单个目标，采用简化的单主节点模型：

\[ \sum_{k=1}^{K}a_{i,k}(t)=1 \]

\[ \sum_{k=1}^{K}s_{j,k}(t)=1 \]

后续可以扩展为多个 RSU 协同跟踪，但初期不需要。

### 2. 车辆运动与状态估计模型

车辆状态定义为：

\[ \mathbf{x}_j(t)= [x_j,y_j,v_{x,j},v_{y,j}]^{T} \]

采用恒速（CV）和协调转弯（CT）模型：

\[ \mathbf{x}_j(t+1) = \mathbf F_{m_j(t)}\mathbf{x}_j(t) +\mathbf w_j(t) \]

其中：

- \(\mathbf F\)：车辆运动状态转移矩阵。
    
- \(m_j(t)\)：车辆运动模式。
    
- \(\mathbf w_j(t)\)：运动噪声。
    

采用 IMM-UKF 获得：

\[ \hat{\mathbf x}_j(t),\quad \mathbf P_j(t) \]

这里有一个非常重要的设计：

不能直接把仿真环境中的真实车辆位置交给强化学习智能体。

智能体只能获得状态估计、协方差、通信质量等可观测信息。

这样才是真正的不完美感知条件下的网络决策。

### 3. 动态遮挡概率模型

这是我认为可以重点挖掘的创新点。

假设 RSU \(k\) 到车辆 \(j\) 的视线可能受到其他车辆遮挡。

定义：

\[ \nu_{k,j}(t) = P(\mathrm{LoS}_{k,j}(t)=1) \]

其中：

\[ 0\leq \nu_{k,j}(t)\leq 1 \]

可以利用车辆位置、尺寸、速度和协方差预测未来的遮挡概率。

例如：

- 预测 RSU A 在未来 200 ms 内被大型车辆遮挡的概率为 0.85。
    
- RSU B 的可见概率为 0.92。
    
- RSU C 的可见概率为 0.35。
    

那么系统不应该等到 RSU A 完全失去感知能力才切换，而应该提前评估 RSU B 是否适合接管。

初期可以使用几何遮挡模型和蒙特卡洛采样，不必一开始训练复杂的遮挡预测网络。

### 4. 感知性能模型

对于 RSU \(k\) 对目标 \(j\) 的感知测量：

\[ \mathbf z_{k,j}(t) = \mathbf h_{k,j}(\mathbf x_j(t)) + \mathbf n_{k,j}(t) \]

其中：

- \(\mathbf h\)：距离、角度、多普勒等测量函数。
    
- \(\mathbf n\)：感知测量噪声。
    

假设预测协方差为 \(\mathbf P^-_j(t)\)，则可采用信息矩阵形式近似表示后验精度：

\[ \begin{aligned} \mathbf J_j(t) =& \left(\mathbf F\mathbf P_j(t-1) \mathbf F^T+\mathbf Q\right)^{-1}\\ &+ \sum_{k=1}^{K} s_{j,k}(t)\nu_{k,j}(t) \mathbf H_{k,j}^{T} \mathbf R_{k,j}^{-1} \mathbf H_{k,j} \end{aligned} \]

进而：

\[ \mathbf P_j^+(t)\approx \mathbf J_j^{-1}(t) \]

这可以作为后续跟踪性能的 PCRB 近似指标。

它把三个因素联系起来：

1. 车辆自身运动的不确定性。
    
2. RSU 的感知几何与测量质量。
    
3. 动态遮挡造成的观测可靠性变化。
    

这比单纯使用 SNR 选择 RSU 更有研究价值。

### 5. 通信性能模型

通信侧采用常见 SINR 和 Shannon 速率模型：

\[ \gamma_{i,k}(t) = \frac{p_i |\mathbf h_{i,k}^{H}(t)\mathbf w_{i,k}|^2} {I_{i,k}(t)+\sigma^2} \]

\[ R_{i,k}(t) = B_{i,k}\log_2(1+\gamma_{i,k}(t)) \]

其中：

- \(p_i\)：发射功率。
    
- \(\mathbf h_{i,k}\)：通信信道。
    
- \(\mathbf w_{i,k}\)：波束赋形向量。
    
- \(B_{i,k}\)：分配带宽。
    
- \(I_{i,k}\)：干扰。
    

初期可以固定波束码本和功率配置，重点研究 RSU 关联与切换，不要同时优化所有物理层参数。

### 6. 最终优化目标

我建议将问题构建为一个长期序贯决策问题。

定义：

- \(H_c(t)\)：通信切换次数。
    
- \(H_s(t)\)：感知航迹交接次数。
    
- \(L(t)\)：切换中断或航迹丢失造成的损失。
    

构造长期奖励：

\[ \boxed{ r_t= \alpha\sum_i R_i(t) -\beta\sum_j\omega_j \operatorname{tr}(\mathbf P_j^+(t)) -\lambda_1H_c(t) -\lambda_2H_s(t) -\lambda_3L(t) } \]

优化目标：

\[ \max_{\pi} \mathbb E_{\pi} \left[ \sum_{t=0}^{T} \gamma^t r_t \right] \]

约束包括：

\[ R_i(t)\geq R_i^{\min} \]

\[ \sum_i p_i(t)\leq P_{\max} \]

以及 RSU 的通信和感知处理能力限制。

这里的核心不是让某一时刻的吞吐量最高，而是让整个车辆行驶过程中：

- 通信不中断。
    
- 感知航迹不断裂。
    
- 切换次数合理。
    
- 不因为短期预测误差反复切换。
    

这就形成了一个有明确通信物理意义的优化问题。

## 四、AI 技术路线：如何真正体现 AI + 通信？

这是决定你未来就业竞争力的重要部分。

我不建议你直接使用一个普通 DQN 或 PPO，然后把通信系统的几个指标塞进奖励函数。

因为 2026 年已经有不少 DRL 用于 ISAC 功率分配和资源优化的研究；GNN 也已经被用于 Cell-Free ISAC 的 AP 选择和联合优化。

Korea University Pure+2

我建议采用：

推荐技术路线

IMM-UKF + 动态遮挡预测 + 时空图神经网络 + PPO

### 1. 第一层：物理模型和状态估计

[3 - Non-linear models: unscented Kalman filter — Stone Soup 0.1b6 documentation](https://images.openai.com/static-rsc-4/zt_x62Cg0n1Bn0DfExW5_IClU1-A39REChw9YbB1s8gtwyMwYHUG0_-UhXGMC04v5NkCe2zFoh00B44RppNEzDkBIyzzAwOSIXlT_3HPaLa4cmU1DgN-1x0HIVAyWiUCMZMA06GxcAkVkYFKSvz14uXEKh6tEs2n1f4t0ZuFYpw?purpose=inline)

[stonesoup.readthedocs.io](https://stonesoup.readthedocs.io/en/v0.1b6/auto_tutorials/03_UnscentedKalmanFilterTutorial.html?utm_source=chatgpt.com)

先使用 IMM-UKF：

- 估计车辆位置、速度和航向。
    
- 获取状态协方差。
    
- 预测短期运动轨迹。
    
- 计算不同 RSU 的未来可见概率。
    

对于网联车辆，可以增加 CAM/BSM 作为辅助状态观测。

注意：这里将方向一的成果作为辅助技术，不直接承担完整的异步 TO/CFO 联合估计任务。

ETSI CAM 的时间戳、位置、运动状态和置信度字段能够为这种多速率融合提供标准依据。

ETSI

### 2. 第二层：构建 RSU-车辆异构图

[Dynamic Allocation of C-V2X Communication Resources Based on Graph Attention Network and Deep Reinforcement Learning](https://images.openai.com/static-rsc-4/pkhvPPFW1iUmq5TNFiznyxdfsiMQlvO4KsCjTrbFVDGBJUsYPK8jxQcWUrgk6Z6Y961PPjmk0-lR-Ea4HeOnasA7aKsm6FCeHHbtDVHz1mo_UjjwkcF3Mlyh8WRTCBZhU-uWt_S9T_MT4z7982vq2h9AiQC1vJRPeKxHZljONiw?purpose=inline)

[mdpi.com](https://www.mdpi.com/1424-8220/25/16/5209?utm_source=chatgpt.com)

把整个网络抽象为图：

\[ G_t=(V_t,E_t) \]

节点包括：

- RSU 节点。
    
- 网联车辆节点。
    
- 被感知目标节点。
    

边表示 RSU 与车辆或目标之间的关系。

每条边包含：

|特征|含义|
|---|---|
|预测 SINR|通信质量|
|距离|RSU 与目标距离|
|可见概率|LoS/NLoS 状态|
|PCRB 信息增益|感知价值|
|状态协方差|预测不确定性|
|切换代价|切换时延和信令开销|

使用 GNN 或 Graph Attention Network 提取网络拓扑关系。

这样，当车辆数量从 5 辆增加到 20 辆，或者 RSU 从 2 个增加到 4 个时，模型不必完全依赖固定长度的状态向量。

### 3. 第三层：PPO 联合决策

[PPO (Proximal Policy Optimization)](https://images.openai.com/static-rsc-4/JirfRtrB18aovgvZzm8jNYmPfn01yiKQsAEXQpVP_Rv4yLgZYI6K4um8uc77sTMQGty1Qj_hZLj9fILyiYwtB8Guge0yTRL1twTPfLprf6VLWbOIlCMDEzEXl658Gz9WrNY3HRS71UQhyVWmGQXQRzYcTcLprMFFYfaBbVJnm0A?purpose=inline)

[hoonhub.dev](https://hoonhub.dev/background/ai/ppo-proximal-policy-optimization/?utm_source=chatgpt.com)

使用 PPO 作为主要强化学习算法。

输入：

\[ s_t=\operatorname{GNN}(G_t) \]

输出动作：

\[ a_t= \left( a_{i,k}(t),s_{j,k}(t) \right) \]

即：

- 是否切换通信服务 RSU。
    
- 是否交接感知航迹。
    
- 选择哪个 RSU 作为新的服务节点。
    
- 选择哪个 RSU 作为新的主要感知节点。
    

采用动作掩码限制不可行决策，并通过约束惩罚保证通信 QoS。

我更建议先采用边缘控制中心统一决策的 GNN-PPO，而不是一开始就使用 MAPPO。

原因是：

- 统一决策容易协调通信和感知。
    
- 更容易控制动作空间。
    
- 更容易与传统优化算法比较。
    
- 训练过程相对容易复现。
    

### 4. 完整技术路线

SUMO 交通流与城市交叉口场景

车辆运动、交通密度、建筑和动态遮挡物

多 RSU 通信与 ISAC 感知模型

SINR、时延、多普勒、感知测量、可见概率

IMM-UKF 状态估计与短期预测

位置、速度、协方差、动态遮挡概率

异构图构建 + GNN 特征提取

RSU、车辆、目标和网络状态

PPO 联合决策

通信关联、感知航迹交接、切换时机

性能评估与在线反馈

吞吐量、PCRB、航迹连续性、切换中断、信令开销

这条路线有一个重要特点：

前半部分使用通信和感知理论提供可靠的物理状态，后半部分使用 AI 决定网络应该如何行动。

这比单纯让神经网络预测信道或直接输出波束索引更有系统性。

## 五、如果选择方向一，数学模型和 AI 技术应该怎么做？

为了避免只分析方向二，我也给方向一设计一条可以真正落地的路线。

### 1. 系统状态

考虑一辆网联车辆作为移动发射端，一个 RSU 作为接收端，另外有一个或多个被动目标。

定义联合状态：

\[ \mathbf x(t)= [ \mathbf p_u,\mathbf v_u, \mathbf p_s,\mathbf v_s, \delta_\tau,\delta_f, \mathbf b_{\mathrm{GNSS}} ]^T \]

其中：

- \(\mathbf p_u,\mathbf v_u\)：发射车辆的位置和速度。
    
- \(\mathbf p_s,\mathbf v_s\)：被动目标的位置和速度。
    
- \(\delta_\tau\)：时钟定时偏差。
    
- \(\delta_f\)：载波频率偏差。
    
- \(\mathbf b_{\mathrm{GNSS}}\)：GNSS 慢变定位偏差。
    

### 2. 双基地观测模型

定义路径总长度：

\[ L_\ell(t)= \|\mathbf p_u-\mathbf p_s\| + \|\mathbf p_s-\mathbf p_R\| \]

则可以建立：

\[ \hat\tau_\ell(t) = \frac{L_\ell(t)}{c} +\delta_\tau(t)+n_\tau \]

\[ \hat f_\ell(t) = -\frac{1}{\lambda}\dot L_\ell(t) +\delta_f(t)+n_f \]

这两个式子说明：

- 位置影响双基地传播距离。
    
- 速度影响双基地多普勒。
    
- 时钟误差影响时延和频率估计。
    
- 目标运动与发射端运动会共同影响测量。
    

### 3. CAM 辅助观测

车辆广播状态：

\[ \mathbf z_{\mathrm{CAM}}(t_k)= \begin{bmatrix} \mathbf p_u(t_k-\Delta_k)+\mathbf b_{\mathrm{GNSS}}\\ \mathbf v_u(t_k-\Delta_k) \end{bmatrix} +\mathbf n_{\mathrm{CAM}} \]

这里最关键的是：

CAM 不能被视为真实位置，而应该是带有时间延迟和误差协方差的观测。

### 4. AI 技术路线

建议采用：

- 因子图或 EKF/UKF：完成物理状态估计。
    
- PyTorch：构建学习辅助的测量噪声估计网络。
    
- Robust Neural Filtering：学习 GNSS 异常误差和测量可靠性。
    
- PCRB：评估估计性能极限。
    

可以构建一个网络，学习不同条件下的测量可靠性权重：

\[ w_t=f_\theta( \mathrm{SNR}, \sigma_{\mathrm{CAM}}, \Delta_t, \mathrm{NLoS} ) \]

然后把这个权重融入鲁棒滤波器。

不过，方向一的主贡献仍然应该是估计理论和物理建模，不能把它变成一个纯粹的神经网络定位项目。

### 5. 方向一的毕业可行性

|研究阶段|工作内容|难度|
|---|---|---|
|第一阶段|单车、单 RSU、单目标异步双基地模型|中|
|第二阶段|TO/CFO 和运动状态联合估计|高|
|第三阶段|CAM 多速率、延迟和鲁棒融合|高|
|第四阶段|多车、多目标扩展|很高|

我认为方向一可以独立形成一篇质量不错的硕士论文，但如果把多车、多 RSU、恶意消息检测和完整时钟同步都放进去，就会明显超出合理工作量。

## 六、硕士毕业可行性：如何控制工作量？

我认为方向二最重要的不是把模型做得多复杂，而是要有一个能够逐步完成、随时可以形成论文成果的研究计划。

### 1. 建议分成三个研究内容

研究内容一：多 RSU 协同 ISAC 系统建模与状态预测

基础工作

主要任务：

- 建立城市交叉口多 RSU 系统模型。
    
- 建立车辆运动、通信和感知模型。
    
- 使用 IMM-UKF 预测车辆状态。
    
- 建立动态遮挡概率模型。
    

预期成果：一个可复现的车联网多 RSU ISAC 仿真平台。

研究内容二：通信与感知联合切换机制

核心创新

主要任务：

- 研究通信切换与感知航迹交接的耦合关系。
    
- 设计考虑预测协方差的联合切换触发条件。
    
- 设计航迹状态及其协方差的交接机制。
    
- 分析切换时延、信令开销和跟踪连续性。
    

预期成果：一套具有数学依据的联合切换算法。

研究内容三：不确定性感知图强化学习决策

AI 创新

主要任务：

- 构建 RSU-车辆异构图。
    
- 设计 GNN-PPO 决策模型。
    
- 优化通信关联和感知航迹交接。
    
- 研究不同交通密度、遮挡和 RSU 数量下的泛化能力。
    

预期成果：一个能够在动态无线环境中做长期决策的 AI 模型。

### 2. 仿真工具选择

我建议使用以下工具，不需要一开始就搭建真实硬件平台。

|工具|具体用途|优先级|
|---|---|---|
|SUMO|车辆轨迹、交通流、交叉口|必须|
|Python|系统建模和算法实现|必须|
|PyTorch|GNN、PPO、深度学习|必须|
|PyTorch Geometric|异构图神经网络|推荐|
|Stable-Baselines3|PPO 算法实现|推荐|
|MATLAB 5G Toolbox|5G NR 和 ISAC 信号验证|推荐|
|Sionna|无线信道、射线追踪|后期|

建议初期采用 Python + SUMO + 几何遮挡模型，先把系统跑通，再引入 3GPP 信道模型和更高保真的射线追踪。

3GPP 的 TR 38.765 已经进入 Release 20 的 ISAC NR 研究体系，且处于变更控制状态，可以作为标准背景和系统模型的重要参考。

3GPP Portal

### 3. 必须设计的对比基线

这部分决定你的论文能不能证明创新。

|基线|方法|用途|
|---|---|---|
|Baseline 1|RSRP + A3 切换|传统通信切换|
|Baseline 2|IMM-EKF 感知辅助通信切换|对比已有 V2I 感知切换|
|Baseline 3|BP 目标航迹交接|对比分布式感知交接|
|Baseline 4|两种切换分别独立运行|验证联合设计的价值|
|Baseline 5|最近 RSU / 最大 SINR 贪心选择|简单决策基线|
|Baseline 6|PPO-MLP|验证图结构是否有帮助|
|Proposed|不确定性感知 GNN-PPO|你的方法|

还应该在小规模场景下使用穷举搜索或混合整数优化获得近似最优上界，避免只和较弱的强化学习基线比较。

### 4. 评价指标

不要只看奖励函数。

|类别|指标|
|---|---|
|通信|平均吞吐量、5% 分位吞吐量、通信中断率|
|切换|切换次数、切换失败率、乒乓切换率、中断时间|
|感知|定位 RMSE、速度 RMSE、PCRB|
|跟踪|航迹丢失率、航迹连续性、ID 切换次数|
|系统|信令开销、推理时间、RSU 负载|
|AI|收敛速度、跨场景泛化能力、计算复杂度|

其中我最建议重点突出三个结果：

1. 联合切换是否比两种独立切换更好？
    
2. 考虑预测不确定性是否能减少乒乓切换？
    
3. GNN-PPO 能否在不同 RSU 数量和车辆密度下保持性能？
    

### 5. 时间安排

|阶段|主要任务|
|---|---|
|第 1–3 个月|文献精读、复现 IMM-UKF 和传统切换算法|
|第 4–6 个月|建立 SUMO 和多 RSU 仿真平台|
|第 7–10 个月|完成联合切换数学模型和传统优化基线|
|第 11–15 个月|实现 GNN-PPO，完成主要对比实验|
|第 16–20 个月|动态遮挡、泛化和鲁棒性实验，准备论文|
|第 21–24 个月|扩展研究、整理学位论文|
|第 25–30 个月|修改、送审和答辩|

这是按约 2.5 年研究周期制定的建议计划，具体需要结合学院开题和毕业时间调整。

最重要的是：研究内容一完成后，就应该已经有可以运行的系统；研究内容二完成后，就应该有一套独立的算法。不能等到 GNN-PPO 全部训练完才有成果。

## 七、从就业角度分析：哪个方向更值得投入？

这是我最终倾向方向二的主要原因。

目前通信与 AI 的交叉就业，不仅包括传统的基带算法，还包括 AI-RAN、无线网络智能优化、边缘智能和网络自动化等岗位。

例如 AI-RAN 研究已经关注：

- 基于 AI 的无线资源分配。
    
- 强化学习辅助 RAN 优化。
    
- GNN 拓扑感知网络优化。
    
- Near-RT RIC 的 xApp 和 Non-RT RIC 的 rApp。
    
- 网络移动性管理与智能控制。
    

相关研究也开始讨论 AI 与 RAN 在同一基础设施上运行，以及计算和无线资源的协同调度。

IEEE Communications Society+2

### 两个方向对应的就业能力

[MIMO Radar System Testing Tools and Techniques | Tektronix](https://images.openai.com/static-rsc-4/3QGAO9-DG5LEREjbEuwlKCjr9CtsC96fJsLfpEYR9Y01FNj2_mHHgYLSPidBYJ8TPeuT3xVEBsG4vYEv65e1oM-SobH99BHpQcVW3gokzQwrxFh7UAjPd-fdOVd0JhZQor88sjd8SjrL66wq1Ppk-0jvO8nK_Q5rBoZZVDa4Wng?purpose=inline)

方向一：信号处理与无线感知算法

重点积累：

- OFDM、MIMO、SRS 信号处理。
    
- 时钟同步、CFO 估计。
    
- 雷达参数估计和目标定位。
    
- EKF、UKF、因子图。
    
- 鲁棒估计和传感器融合。
    

适合无线物理层算法、雷达算法、定位感知、通信基带研发等岗位。

[什么是 AI-RAN？架构、技术逻辑、部署挑战与 6G 展望-贝克电信](https://images.openai.com/static-rsc-4/v3OiML9iTCeV-BpA7MtySAT1Y1W5WWJtck0K6NJB31fXtxVlGdnZ8kDSZoqrAXWo0lArtOoXAQPjk7w7WDZUqif9trBCKxOF0hUUexZ42dng_Jmxee4PFqY4hPMG2I4SixJzMGwAYgPo1rrWRT0e4I0Ehmiaddm-UBDfkXIk360?purpose=inline)

方向二：AI-RAN 与智能无线网络算法

重点积累：

- Python、PyTorch。
    
- GNN、PPO、强化学习。
    
- 无线资源分配和移动性管理。
    
- 通信系统建模与优化。
    
- 边缘智能、网络控制和推理部署。
    

适合 AI-RAN、无线网络算法、通信智能优化、边缘智能、网络自动化等岗位。

我尤其建议你在硕士期间形成一个可以展示的工程作品：

基于 GNN-PPO 的多 RSU 智能切换仿真系统。

它不只是一个论文算法，而是可以向面试官展示的项目：

1. 能够搭建车联网通信环境。
    
2. 能够建立无线信道和感知模型。
    
3. 能够使用 PyTorch 训练强化学习模型。
    
4. 能够进行算法对比和消融实验。
    
5. 能够分析模型的推理延迟和泛化能力。
    

这比只在简历上写「熟悉强化学习，研究 ISAC」更有说服力。

## 八、最终推荐：正式硕士论文开题题目

综合文献查新、理论深度、AI 技术结合、课题组基础和就业目标，我建议你最终选择：

最终推荐题目

# 基于不确定性感知图强化学习的多 RSU 协同 ISAC 通信—感知联合切换研究

英文：Uncertainty-Aware Graph Reinforcement Learning for Joint Communication and Sensing Handover in Multi-RSU Cooperative ISAC Networks

研究场景

城市交叉口动态遮挡车联网。

核心研究问题

通信服务节点与感知跟踪节点的联合切换。

理论基础

IMM-UKF、PCRB、SINR、动态遮挡概率、无线移动性管理。

AI 方法

时空图神经网络 + PPO。

优化目标

在保证通信 QoS 的同时，降低感知误差、航迹丢失、切换中断和信令开销。

主要预期创新

1. 建立通信关联与感知航迹交接的联合决策模型。
    
2. 将目标状态预测不确定性和动态遮挡概率引入联合切换机制。
    
3. 设计不确定性感知的图强化学习策略，实现动态多 RSU 网络的长期决策。
    

### 为什么不是直接选择方向一？

方向一的理论创新空间确实很好，但它的核心研究能力偏向无线信号处理和参数估计。

方向二则可以同时积累：

- 通信理论。
    
- 无线网络优化。
    
- 目标跟踪。
    
- 图神经网络。
    
- 强化学习。
    
- 边缘智能。
    

这几项能力组合起来，更贴近你希望进入的 AI + 通信交叉岗位。

### 方向一怎么保留？

我建议不要完全放弃方向一，而是采用以下安排：

|研究位置|内容|
|---|---|
|主线|多 RSU 协同 ISAC 联合切换|
|辅助技术|CAM/BSM 辅助车辆状态预测|
|后续扩展|异步双基地测量与时钟偏差鲁棒估计|

这样既保留了方向一的特色，又不会让整个硕士论文同时承担两套复杂的物理层系统模型。

## 九、正式开题前还需要做的三件事

我建议暂时不要急着写完整开题报告，而是先完成三个验证。

第一：精读四篇最重要的论文。

1. Xu 等：An ISAC-Based Beam Tracking Scheme Against Inter-Region Interference for the Multi-RSU V2I Scenario。
    
2. Xu 等：A Rate-Splitting Multiple Access Enabled Cooperative ISAC Tracking System for Complex V2I Scenarios。
    
3. Li 等：Look Before Switch。
    
4. Bai 等：Belief Propagation-based Target Handover。
    

尤其需要对比你们课题组已有的两篇 TVT 工作，避免研究内容重叠。

第二：先做一个最小可行仿真。

仅使用两个 RSU、一辆车辆、一个动态遮挡物，验证：

- 传统 RSRP 切换。
    
- 感知辅助通信切换。
    
- 独立通信切换与航迹交接。
    
- 联合切换。
    

如果联合切换在这种简化场景中都无法体现优势，就需要调整数学模型，而不是急着上强化学习。

第三：确认 AI 的必要性。

如果 GNN-PPO 不能在长期收益、复杂度或跨场景泛化方面优于规则算法和传统优化，就不能仅凭使用了 GNN-PPO 宣称创新。

## 十、我建议你接下来先做这个任务

我建议下一步不是直接写开题报告，而是进行一次更严格的论文级创新性对照：

- 逐篇拆解上述四篇核心论文的系统模型、优化变量和算法。
    
- 特别分析徐少毅老师团队 2025、2026 年两篇相关工作。
    
- 找出至少两个现有工作没有同时解决的具体问题。
    
- 判断联合切换究竟能不能形成独立的论文贡献。
    

这样可以避免开题后才发现和已有论文重复。

我更愿意让你先花一周把研究问题确定准确，再花几个月做算法，而不是现在就把 GNN、PPO、世界模型和多 RSU 全部堆在一起。