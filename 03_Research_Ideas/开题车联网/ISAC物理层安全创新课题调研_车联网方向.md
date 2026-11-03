# ISAC 物理层安全：创新课题深度调研（面向车联网）

> 调研时间：2026 年 11 月初
> 范围：IEEE 期刊/会议、arXiv 预印本、部分安全领域会议（ACM WiSec、ACSAC 等）
> 说明：本文档**不重复**“方案6：轨迹级感知隐私”的内容，聚焦其他物理层安全方向。

---

## 0. 结论速览

| 方向 | 一句话 | 新颖度 | 难度 | 硕士适配 | 与方案3/5的衔接 |
|---|---|---|---|---|---|
| **A. 感知完整性：抗重放/欺骗** | 攻击已被实测，防御滞后；可借鉴安全测距（ED/LC）理论 | ★★★★★ | 中 | 很好 | 方案5（多RSU几何校验） |
| **B. 恶意 RIS 攻击与物理检测** | 现有检测准确率约 74%，物理指纹类检测几乎空白 | ★★★★ | 中 | 好 | 可与 A 统一为“人为多普勒检测” |
| **C. 身份–物理一致性认证 / 女巫检测** | ISAC 回波能独立证明“这里真的有车” | ★★★★ | 中低 | 很好 | 方案3（CAM 真实性校验） |
| D. 感知辅助物理层密钥生成 | 车联网 LoS 几何下，附近窃听者的泄露尚未量化 | ★★★ | 中高 | 一般 | — |
| E. 隐蔽感知 | 让“正在感知”本身不被发现，刚起步但增长快 | ★★★ | 中 | 一般 | — |
| F. 小方向（硬件不对称、AI 对抗攻击） | 适合一篇快报 | ★★★ | 中 | 视基础而定 | — |

**最推荐的组合：** A + B + C，可以串成一篇以“车联网 ISAC 感知完整性”为主题的毕业论文（见第 8 节）。

---

## 1. 领域全景：ISAC 物理层安全的三类问题

ISAC 安全大体可以分为三类：

1. **通信保密**：防止 ISAC 信号承载的数据被窃听。这是研究最多的部分。
2. **感知隐私**：防止未授权方利用 ISAC 信号感知目标。近两年快速升温，方案6 已覆盖。
3. **感知完整性**：防止攻击者篡改感知结果，例如注入假目标、隐藏真目标、伪造位置。**这是目前最薄弱、也最贴近车联网安全需求的部分。**

几个可以佐证的事实：

- 一篇面向交通场景的 6G ISAC 多域安全综述（arXiv:2511.16316）指出，ISAC 的物理层面临伪造 CSI、协同干扰、注入虚假反射制造幽灵目标等主动攻击。而且由于感知和通信共用波形，跨层耦合更紧：欺骗感知会改变波束选择，进而拖累链路质量。
- Matsumine 等人的 ISAC 物理层安全综述（IEEE OJCOMS 2025）认为，通信安全已经被研究得比较透彻，而感知安全研究得还很少。
- IEEE JSAC 有一期“Secure Communication, Sensing, and Computation”特刊（2026 年第二季度出版），征稿主题包括感知与定位系统的安全隐私、RIS 辅助反探测、近场安全、密钥生成等。
- VTC2026-Fall（波士顿）开设了 ISAC 安全隐私专题讲座（T12），重点就是干扰、欺骗、幽灵目标注入等操纵感知结果的物理层威胁，以及协同缓解策略。

**拥挤区（建议避开）：**
- “CRB 约束下最大化保密速率 + 人工噪声/RIS/无人机 + 交替优化”
- “隐蔽通信 + ISAC 波束设计”，包括对抗多个（共谋）监测者的版本

---

## 2. 方向 A：感知完整性——抗重放/欺骗攻击（★ 首推）

### 2.1 攻击已经被实测，而且门槛不高

| 工作 | 攻击方式 | 关键结论 |
|---|---|---|
| G. Chrysanidis, Y. Liu, A. Argyriou, *A Replay Attack Against ISAC Based on OFDM*, IEEE Access, 2024 | 截获 OFDM 帧后重发，在各子载波和各符号上施加不同相移 | 车联网仿真中，ISAC 系统无法区分假目标和真目标，攻击者即便功率很低也能奏效 |
| *Practical Blind Full-Frame Replay Attacks on OFDM-Based ISAC Systems*, IEEE JSAC，2026 年 3 月录用 | **盲**全帧重放：施加受控时延和频移后整帧重发，不需要解析帧结构、不需要同步、不需要知道信号内容 | 可以移动真实目标的表观位置、完全遮蔽目标或注入假目标；用商用 SDR 在真实 5G gNB–UE 双基地系统上验证了可行性 |
| H. C. Yildirim et al., *OFDM-based JCAS under Attack*, IEEE IoT-J, 2025 | WLAN 感知中的目标欺骗和欺骗式干扰 | 最高可造成 92% 的假目标注入或关键目标漏检 |
| T. Shui, W. Saad et al.（见方向 B） | 恶意 RIS 无源欺骗 | 生成时空一致的完整假轨迹 |

### 2.2 防御现状：很少，而且大多是“单点检测”

- S. Iqbal, …, H. Arslan, *Dual Correlation-Based Sensing Spoofer Detection in ISAC*, IEEE WCL, 2026：针对感知辅助通信场景，通过给感知信号和通信信号分配不同功率来检测欺骗。在 30 dB SNR、感知功率和欺骗增益都较高时，漏检概率约为 10⁻³。
- K. Qian, P. Pathak（UVA/GMU），*Toward Spoofing-Resilient and Communication-Integrated mmWave Radar Sensing*：在 77 GHz FMCW 雷达上，利用“真实多普勒与载频成正比、人为调制频移不随频率变化”的差异来检测欺骗（下文 2.4 节的课题 A2 会用到这个思路）。

### 2.3 可借鉴的两个“外部领域”

**(1) 多基地雷达的抗欺骗干扰（ECCM）**

雷达领域早就研究过多站系统如何识别假目标：
- 欺骗速度检验：真实目标在各接收站测到的径向速度相互一致，假目标则不一致（Li et al., Remote Sensing, 2024）。
- 同源定位检验：各站对同一目标的定位结果应当重合（Huang et al., 2019）。
- 宽带 HRRP 相关性：真实目标的高分辨距离像随观测角度变化而去相关，而同一干扰源产生的假目标在各站的距离像高度一致（IEEE Sensors Journal, 2025）。

但需要注意一个**关键差异**：多基地雷达抗欺骗的前提之一，是接收站静默工作、位置不易被攻击者获知。Zefi 等（SPIE 2024）也证明，如果干扰机知道各接收机的位置，就能为每个接收机分别计算时延，让假目标在所有双基地图像中出现在同一位置。**而 ISAC 的 RSU 和基站是公开部署的基础设施，位置很容易被获知。** 这正是 ISAC 版本需要重新研究的地方（见课题 A3）。

**(2) 安全测距（Secure Ranging）：ED/LC 攻击**

- 测距安全领域的核心结论是：要防御“距离缩短攻击”，测距信号必须不可预测，否则攻击者可以提前注入信号。
- 早检测/晚提交（ED/LC）攻击：攻击者只观察符号的前一小段就猜出符号值，然后提前发射伪造信号，等确定后再“提交”正确的值。
- **对 ISAC 特别重要的结论：** Leu 等人在 ACSAC 2021 的研究表明，基于 OFDM 的测距（如 IEEE 802.11az）**无论帧长和子载波数多少**，都容易受到 ED/LC 攻击。原因是 OFDM 符号较长，给了攻击者足够的观察和反应时间（详见 Leu 的 ETH 博士论文）。

**由此引出的修正：** 直觉上，重放攻击者必须先收到信号再转发，必然带来额外时延，所以只能把目标“推远”，而 ISAC 承载随机数据，看起来天然难以预测。但 ED/LC 说明，**OFDM 符号内部的可预测性**仍然可能让攻击者把目标“拉近”。这对车联网尤其危险，因为把障碍物“拉近”会触发紧急制动，“推远”或“隐藏”则可能导致碰撞。

### 2.4 具体课题

**A1. ISAC 感知中的距离拉近攻击：可行性分析与对策**
- 研究问题：在 OFDM-ISAC 中（QAM 数据 + 循环前缀 + 导频），攻击者用 ED/LC 能把假目标提前多少？答案取决于符号长度、调制阶数、子载波间隔、攻击者的 SNR 等。
- 查新：安全测距领域研究的是两个合作设备之间的飞行时间测距；**在我们检索范围内，尚未看到把 ED/LC 框架用于 ISAC 雷达式感知（被动目标、攻击者在目标侧）的工作。**
- 对策思路：符号内一致性检验（比较符号前段和后段的估计结果）、在符号内部引入随机相位、比较循环前缀与符号尾部的一致性。
- 适合投：IEEE TIFS / TVT，或安全类会议 ACM WiSec。

**A2. “人为多普勒”的物理检验：统一应对重放和恶意 RIS**

这是一个具体、有物理依据、能写出漂亮推导的点子。

真实运动目标在第 $k$ 个子载波上的多普勒与该子载波频率成正比：
$$
f_{D,k} = \frac{2 v_r}{c}\,\big(f_c + k\Delta f\big),
$$
而重放攻击者在时域施加的频移 $f_a$，以及恶意 RIS 通过相位斜坡制造的频移，**对所有子载波都相同**。

以 28 GHz、400 MHz 带宽、车速 20 m/s 为例：多普勒约 3.7 kHz，带宽两端的多普勒相差约 $B/f_c \approx 1.4\%$，即约 53 Hz。单个 CPI 可能分辨不出来，但结合高 SNR 下的参数估计和多 CPI 跟踪是可以检测的。

研究内容：
- 推导“多普勒频率正比性”的 GLRT 检验统计量和检测性能，给出所需带宽、CPI、SNR 的条件；
- 补充一个“距离-多普勒耦合”检验：真实目标的多普勒必须与距离随时间的变化率一致；
- 讨论攻击者的反制：要伪造正比于频率的多普勒，攻击者需要对信号做时间尺度变换（重采样），这对低时延硬件要求很高，而无源 RIS 基本做不到。

一个检测器同时覆盖方向 A 和方向 B，论文的故事性很强。

**A3. 公开部署条件下的多 RSU 几何一致性：接收端随机化**
- 背景：多基地抗欺骗依赖“攻击者不知道接收站位置”，但 ISAC 基础设施的位置是公开的（见 2.3 节）。
- 思路：每一帧随机选择由哪些 RSU（或哪些网联车 UE）充当感知接收端，即“移动目标防御”。攻击者无法预知哪个接收端在听，就很难让假目标在所有视角下都几何自洽。
- 研究问题：给出“攻击者需要伪造的视角数”与“检测概率”的关系；在接收端随机化带来的感知性能损失和安全增益之间做权衡。
- 与方案5（交叉口多 RSU 动态角色分配）可以直接合并：角色分配时把安全性也作为一个维度。

### 2.5 仿真与实验

- **仿真：** MATLAB 5G Toolbox（PDSCH/DM-RS 感知流程）+ 攻击者模型（时延 + 频移 + 子载波相位）；多 RSU 用几何模型即可起步。
- **实验（加分）：** JSAC 那篇论文证明了用商用 SDR 就能实施攻击。实验室如果有 2–3 台 USRP，可以复现“发射端 + 攻击者 + 接收端”，在真实信号上验证 A2 的检测器。

---

## 3. 方向 B：恶意 RIS 对感知的攻击与物理检测

### 3.1 现状

| 工作 | 内容 | 结果 |
|---|---|---|
| T. Shui, W. Saad, M. Chen, *Sensing Safety Analysis for Vehicular Networks with ISAC*, arXiv:2505.01688 | 首个研究恶意 RIS 破坏 ISAC 车联网感知的工作；攻击者通过时变相位欺骗 RSU 对车辆时延、多普勒、出发角的估计 | 真实速度 10 m/s 时，测速结果可被欺骗到 0.1–14.9 m/s；仅 5° 波束失配就能造成最高 65° 的出发角误差 |
| T. Shui, P.-H. Chou, W. Saad, M. Chen, *Analysis and Detection of RIS-based Spoofing in ISAC*, arXiv:2508.18100 | 推导攻击所需的相位设计和单元数；用 MDP 优化 RIS 相位，生成时空一致的完整假轨迹；提出基于信号时序逻辑（STL）的神经符号检测框架 | 3.1° 波束失配下，测速可偏移到 −9.9 至 50 m/s，出发角偏差最高 11°，用户速率下降 28%；检测准确率 74.17%，比深度聚类基线高 53.34% |
| G. Stamatelis et al., *On the Detection of Non-Cooperative RISs*, arXiv:2411.03237 | 宽带信道模型中刻画了 RIS 相位切换时间的影响；用深度 SVDD + scan B 检验做在线变点检测 | 能检测 RIS 是否存在，但不针对感知欺骗 |
| RIS 安全隐私综述, arXiv:2512.15754 | 汇总了对抗恶意 RIS 的方法 | 指出多维感知交叉验证（AoA/ToA/Doppler）比单一指标更能抵抗隐蔽攻击；红外热成像只对有源 RIS 有效 |
| 非互易 BD-RIS 攻击（NSF PAR 10598706） | 用非对称的超对角相位矩阵破坏 TDD 信道互易性，从而破坏物理层密钥一致性 | 攻击不需要发射能量和同步，难以检测（与方向 D 相关） |

### 3.2 研究空白与课题

现有检测基于“轨迹是否合理”，属于数据层面；而 Saad 团队的攻击者已经专门优化了时空一致性。因此需要**从信号物理层面找 RIS 留下的痕迹**：

**B1. 频率正比性检验**（与 A2 共享同一套理论）：RIS 相位斜坡产生的频移不随子载波变化，而真实多普勒随子载波频率成正比。

**B2. RIS 硬件指纹：**
- 相位切换时间：RIS 只能在离散时刻改变相位，会在 CPI 内留下不连续点（Stamatelis 等的模型已刻画了这一效应，可以借用）；
- 相位响应的频率选择性：实际 RIS 单元的相位响应随频率变化，宽带下会留下特征。

**B3. 主动探测（挑战-应答）：** 合法 RSU 随机扰动波束方向或子载波功率，观察回波变化是否符合真实散射体的物理规律。RIS 攻击者如果不能实时感知并跟上这些扰动，就会露出破绽。

**适合投：** IEEE TIFS / TWC / TVT。注意 Saad 团队已经占了先机，论文中要正面对比其 STL 检测器。

---

## 4. 方向 C：身份–物理一致性认证 / 女巫检测（★ 推荐，与方案3衔接）

### 4.1 问题背景

- **女巫攻击（Sybil）：** 一个物理实体冒充多辆车，广播多个身份的 BSM/CAM，可以伪造拥堵、干扰协同驾驶。
- 密码学认证无法防御“持有合法证书的内鬼”。一篇 2026 年 10 月的 V2X 误报检测预印本（TRUST-V）明确指出：签名正确但内容恶意的消息，密码学认证挡不住。

### 4.2 已有物理层方法及其局限

| 工作 | 方法 | 局限 |
|---|---|---|
| S. So, J. Petit, D. Starobinski, ACM WiSec 2019 | 基于 BSM 的 RSSI 做物理层合理性检查 | 最佳检测率 83.73%、精确率 95.91%；RSSI 粗糙 |
| *Sybil Attack Detection Based on Signal Clustering in Vehicular Networks* | 用 CSI 的时空变化聚类，实测 DSRC 数据 | 检测率超过 98%，但本质是“把同一信道的消息聚在一起” |
| *Physical Signal-Driven Fusion for V2X Misbehavior Detection* | 利用车载多阵列天线的接收信号验证 V2X 消息中声称的 GPS 位置 | 不需要大量专用锚点 |
| V2X 平台安全综述, arXiv:2003.07191 | 汇总各类女巫检测 | 指出基于 RSSI 关联的方法在 GPS 有误差时不可行，攻击者使用多部电台时也可能失效 |
| *Toward Trusted and Swift UAV Communication: ISAC-Enabled Dual Identity Mapping*, arXiv:2306.17350 | 无人机网络中，用 ISAC 感知到的物理特征与通信身份做双重映射 | 检测精确率比基于移动性的方案平均高 31.55%；场景是无人机 |
| *ISAC for Low-Altitude Security*, arXiv:2601.13810 | ISAC 动态可信认证：独立获取发射端位置、轨迹、速度，并检查是否与其广播的 GNSS 位置一致 | 低空场景，偏框架性 |
| H. Amin et al., *Hybrid PLS-ML Authentication for V2I*, 2023 | 以发射车位置为指纹做物理层认证 | 缺少 ISAC 回波 |

### 4.3 ISAC 能带来什么新东西

现有物理层方法（RSSI、CSI、AoA）证明的都是**“这条消息来自哪个信道”**。攻击者如果用多部电台或多波束，就能制造出看起来不同的信道。

ISAC 多了一个独立证据：**雷达回波可以证明“声称的位置上是否真的有一个物理目标”**，而且这个证据不依赖被验证方是否配合。多电台女巫攻击者可以伪造多个信道，却无法凭空在多个位置变出车辆的雷达回波。

### 4.4 具体课题

**C1. 基于检测理论的身份–目标关联与女巫检测**
- 把问题建模为“$N$ 个声称身份 ↔ $M$ 个感知到的物理目标”的关联问题，并考虑 GNSS 误差和感知不确定性。
- 攻击模型分三类：多身份同实体（Sybil）、幽灵车（声称的位置上什么都没有）、位置偏移。
- 推导检测概率和虚警概率随 SNR、GNSS 误差、目标密度的变化，与 RSSI、CSI 方法对比。

**C2. 波束定向的“位置挑战-应答”**
- RSU 把一个随机数（nonce）**只通过窄波束**发往声称的位置，只有真正在那里的设备才能正确解码并回应。
- 这相当于把安全测距中的距离边界思想推广到“角度 + 距离”的位置边界。需要分析波束宽度、旁瓣泄露和攻击者位置之间的安全性关系。

**C3. 与方案3合并**
- 方案3 中“用感知结果反向校验 CAM 真实性”就是 C1 的特例，两者可以写成一章。

**数据集：** IEEE DataPort 上的 V2X-PAD（基于 ns-3 仿真，含约 83 万条 BSM，10 Hz，包括 False-BSM、DoS、Sybil、协同攻击、重放、身份克隆六类）。它只有消息层数据，没有物理层信号，**需要自己叠加 ISAC 感知仿真**，但可以作为攻击场景的标准来源，方便和其他方法对比。

---

## 5. 方向 D：感知辅助的物理层密钥生成

### 5.1 现状

- **问题背景：** 传统基于信道互易的密钥生成需要双向探测，协议开销大；高速移动时信道相干时间太短，来不及完成探测。
- **ISAC 新思路：** X. Li, …, H. Boche（TUM），*Variational Secret Common Randomness Extraction*，arXiv:2510.02048。Alice 发送 5G NR PDSCH，Alice（感知自己的回波）和 Bob（感知 Alice）各自得到距离-角度图，作为相关随机源；用变分学习结合对抗训练抑制泄露，并做了实验验证。他们还发现，散射丰富的实验室环境有时比微波暗室更能抵抗窃听。
- **优化角度：** K. Liu, K. Huang et al., *Secure ISAC Using Physical Layer Key Generation*, IEEE TVT, 2026。在感知精度约束下，联合优化通信和感知波束以最大化总密钥速率（PPO 强化学习求解）。
- **理论基础：** *Secret Key Generation via Localization and Mobility*（arXiv:1112.2793）把两节点间的距离当作公共随机源，给出了密钥速率的理论极限。结论之一是：如果窃听者拿不到到达角观测，密钥速率随观测噪声减小而无界增长；而窃听者若有策略地移动位置，可以显著降低密钥速率。
- **已知风险：** 在 LoS 条件下，窃听者如果位于 Alice 的 LoS 波束内，可能获得高度相关的观测（arXiv:1701.03904）。

### 5.2 研究空白与课题

车联网的感知随机性主要来自 LoS 几何（距离、角度、相对速度），**附近的车辆同样能观测到这些几何量**。

- **D1. 泄露量化：** 在车联网几何下，窃听者的位置、天线数和感知能力，如何影响基于感知的密钥容量？给出“安全区域”。
- **D2. 只用窃听者看不到的特征：** 例如 Alice–Bob 双基地特有的微多普勒、只在双方之间波束内可见的散射体。
- **D3. 主动攻击下的密钥一致性：** 结合方向 A/B，攻击者伪造回波来操纵公共随机源，或用非互易 RIS 破坏一致性。

难度偏高，需要信息论基础。

---

## 6. 方向 E：隐蔽感知

### 6.1 现状

- **隐蔽通信 + ISAC 已经很拥挤**，例如对抗共谋监测者的 ICC 2025 论文（Wu, …, Zhao, Wong, Karagiannidis）、双无人机 ISAC 隐蔽通信（IEEE IoT-J 2026）、近场多目标隐蔽通信（Hu, …, Yan, 2026），以及大量鲁棒波束设计论文。
- **隐蔽感知（让“正在感知”本身不被发现）刚起步：**
  - SNF-PRP（arXiv:2606.03960）：把伪随机探测信号压到噪声底以下，合法接收端用种子做相干累积；声称是首个针对感知波形隐蔽性的工作，但只考虑能量检测型监测者。
  - Q. Shi, …, P. Fan（西南交大），*Waveform Design for MIMO Covert Sensing and Communications*：用全向发射方向图隐藏真实的感知意图（例如正在跟踪哪个目标），并定义了“隐蔽感知距离”。
  - 布鲁内尔大学团队提出“双重隐蔽性”和联合截获概率（JIP）指标，同时考虑雷达信号和通信信号被截获的概率。

### 6.2 课题

- **E1. 更强的监测者：** 多天线、循环平稳特征检测、基于深度学习的检测器。
- **E2. 跟踪过程中的隐蔽性衰减：** 多帧累积后，监测者的检测能力上升，如何自适应调整功率和波形。
- **E3. 意图隐藏：** 车联网中，特定车辆（如执法车）跟踪目标时不暴露正在跟踪谁。

---

## 7. 方向 F：两个小方向（适合快报）

**F1. 硬件非理想作为安全资源**
- 已有工作（arXiv:2608.13270）发现，合法单基地与非法双基地在本振相位噪声上的不对称，可以扩大感知隐私差距。
- 可扩展：功放非线性、IQ 不平衡、阵列互耦，是否也能形成“合法端可补偿、窃听端不可补偿”的不对称。

**F2. 针对 AI-ISAC 的对抗攻击**
- B. Kim, Y. E. Sagduyu, T. Erpek, S. Ulukus（arXiv:2103.13989）展示了通过空口发射对抗扰动来欺骗深度学习波束预测，效果远超普通高斯噪声干扰。
- 视觉辅助波束预测也已被证明可以被黑盒“空间代理攻击”攻破（arXiv:2504.05222）；防御方面有对抗训练和防御性蒸馏等。
- **空白：** 基于大模型的波束预测器（如 BeamLLM、M2BeamLLM）以及多模态融合模型的对抗鲁棒性，在我们的检索中尚未见到系统研究（这一点未专门查新，开题前需要确认）。

---

## 8. 毕业论文主线建议：车联网 ISAC 感知完整性

### 8.1 推荐结构（3 章 / 3 篇论文）

| 章节 | 内容 | 对应方向 | 目标期刊/会议 |
|---|---|---|---|
| 第 1 章 | **人为多普勒的物理检验**：统一检测重放攻击和恶意 RIS 欺骗（频率正比性 + 距离-多普勒耦合） | A2 + B1 | IEEE WCL / TVT（先快报后期刊） |
| 第 2 章 | **ISAC 感知中的距离拉近攻击**：ED/LC 可行性分析与符号内一致性对策 | A1 | IEEE TIFS / ACM WiSec |
| 第 3 章 | **网络级完整性验证**：接收端随机化的多 RSU 几何校验 + 身份–物理一致性的女巫检测 | A3 + C1 | IEEE TVT / TWC |

### 8.2 为什么推荐这条线

1. **攻击已被实测、防御空白明显**，审稿人容易认可问题的重要性。
2. 每一章都有**清晰的物理洞察**（频率正比性、符号内可预测性、公开部署下的几何校验），而不是套优化框架。
3. 与方案3（CAM 校验）、方案5（多 RSU）可以共享仿真平台。
4. 如果有 SDR，第 1、2 章都能做小规模实测，这在安全方向非常加分。

### 8.3 时间规划（约 2.5 年）

| 时间 | 任务 |
|---|---|
| 第 1–3 个月 | 精读 2.1、3.1、4.2 节核心文献；在 MATLAB 中复现 OFDM-ISAC 感知 + 重放攻击 |
| 第 4–8 个月 | 第 1 章：频率正比性 GLRT 推导与仿真，投快报 |
| 第 9–15 个月 | 第 2 章：ED/LC 分析与对策；可选 SDR 实验 |
| 第 16–24 个月 | 第 3 章：多 RSU 随机化校验 + 女巫检测 |
| 第 25–30 个月 | 学位论文撰写 |

---

## 9. 工具与数据

| 用途 | 推荐 |
|---|---|
| OFDM-ISAC 仿真 | MATLAB 5G Toolbox（含 TR 38.901 ISAC 信道和 PDSCH 感知示例） |
| 多 RSU / 交通场景 | SUMO + 几何遮挡；Sionna RT（可选） |
| SDR 实验 | USRP（发射端、攻击者、接收端各一台），GNU Radio |
| V2X 攻击数据 | V2X-PAD（IEEE DataPort） |
| 双基地实测数据 | POWDER 户外双基地 5G ISAC 数据集（Zenodo，2026） |

---

## 10. 目标期刊与会议

- **安全类：** IEEE TIFS（首选）、IEEE TDSC、ACM WiSec、IEEE CNS；有扎实实测时可以冲 NDSS / USENIX Security
- **通信类：** IEEE JSAC（关注安全相关特刊）、TWC、TVT、TCOM、WCL
- **会议：** ICC、Globecom、VTC、WCNC、ICASSP

---

## 11. 参考文献与链接

### 综述与全景
1. Multi-Domain Security for 6G ISAC: Challenges and Opportunities in Transportation, arXiv:2511.16316：https://arxiv.org/pdf/2511.16316
2. T. Matsumine, H. Ochiai, J. Shikata, Physical Layer Security for ISAC: A Survey, IEEE OJCOMS, 2025：https://arxiv.org/pdf/2504.18097
3. T. Welling, O. Günlü, A. Yener, Secure ISAC: Information Theory Offers Insights, IACR ePrint 2026/842：https://eprint.iacr.org/2026/842
4. IEEE JSAC Special Issue on Secure Communication, Sensing, and Computation in Future Intelligent Wireless Networks（CFP）：https://www.scholat.com/vpost.html?pid=269931
5. VTC2026-Fall Tutorial T12: Security and Privacy in ISAC：https://events.vtsociety.org/vtc2026-fall/conference-sessions/tutorials-currently-available/t12-security-and-privacy-in-integrated-sensing-and-communication-from-physical-layer-threats-to-experimental-validation/
6. Security in the Era of Perceptive Networks: A Taxonomic Framework for ISAC Security（评述）：https://www.themoonlight.io/review/security-in-the-era-of-perceptive-networks-a-comprehensive-taxonomic-framework-for-integrated-sensing-and-communication-security

### 方向 A：重放/欺骗攻击与防御
7. G. Chrysanidis, Y. Liu, A. Argyriou, A Replay Attack Against ISAC Based on OFDM, IEEE Access, 2024：https://ieeexplore.ieee.org/document/10416823
8. Practical Blind Full-Frame Replay Attacks on OFDM-Based ISAC Systems, IEEE JSAC, 2026：https://art.torvergata.it/retrieve/677a067f-fa6f-472e-9ebb-22c1c57beff1/main-final.pdf
9. H. C. Yildirim et al., OFDM-based JCAS under Attack: The Dual Threat of Spoofing and Jamming in WLAN Sensing, IEEE IoT-J, 2025：https://research.chalmers.se/en/publication/544773
10. S. Iqbal et al., Dual Correlation-Based Sensing Spoofer Detection in ISAC Systems, IEEE WCL, 2026：https://avesis.medipol.edu.tr/yayin/dd2eccf6-ffc6-4011-88ae-e7dec60105be/dual-correlation-based-sensing-spoofer-detection-in-isac-systems
11. K. Qian, P. Pathak, Toward Spoofing-Resilient and Communication-Integrated mmWave Radar Sensing：https://par.nsf.gov//servlets/purl/10632728
12. Q. Li et al., Deception Velocity-Based Method to Discriminate Physical Targets and Active False Targets in a Multistatic Radar System, Remote Sensing, 2024：https://doaj.org/article/a6bbb8a5e3a44c85a7fbd68c130156e0
13. D. Huang et al., A Suppression Method Against Range Deception Jamming Based on Homologous Localisation Test, 2019：https://doaj.org/article/68bfe45610264312a62828ddc416f128
14. Complex HRRP-Based Discrimination Method for Active Deception Targets Within Multistatic Radar, IEEE Sensors Journal, 2025, DOI: 10.1109/JSEN.2025.3559565
15. G. Zefi et al., A Deceptive Jamming Technique Against Bistatic SAR, SPIE, 2024：https://strathprints.strath.ac.uk/90834
16. P. Leu, Secure Ranging: Physical-Layer Attacks and Countermeasures, ETH 博士论文, 2023：https://research-collection.ethz.ch/bitstream/handle/20.500.11850/609178/1/thesis_leu.pdf
17. OFDM 测距的 ED/LC 安全性分析（ACSAC 2021）：https://acsac.org/2021/program/final/s212.html
18. Distance-Decreasing Attacks Against Correlation-Based Ranging（Bluetooth CS）, arXiv:2605.10632：https://arxiv.org/html/2605.10632v1
19. W. Gou, C. Yu, G. Wu, Random Time-hopping Secure Ranging Against Distance-Reduction Attacks in UWB, arXiv:2406.06252：https://www.arxiv.org/pdf/2406.06252

### 方向 B：恶意 RIS
20. T. Shui, W. Saad, M. Chen, Sensing Safety Analysis for Vehicular Networks with ISAC, arXiv:2505.01688：https://arxiv.org/abs/2505.01688
21. T. Shui, P.-H. Chou, W. Saad, M. Chen, Analysis and Detection of RIS-based Spoofing in ISAC, arXiv:2508.18100：https://arxiv.org/pdf/2508.18100
22. G. Stamatelis et al., On the Detection of Non-Cooperative RISs: Scan B-Testing via Deep SVDD, arXiv:2411.03237：https://arxiv.org/pdf/2411.03237
23. A Survey on RIS in Practical Systems: Security and Privacy Perspectives, arXiv:2512.15754：https://arxiv.org/pdf/2512.15754
24. 非互易 BD-RIS 破坏密钥生成互易性的攻击：https://par.nsf.gov/biblio/10598706

### 方向 C：身份–物理一致性 / 女巫检测
25. S. So, J. Petit, D. Starobinski, Physical Layer Plausibility Checks for Misbehavior Detection in V2X Networks, ACM WiSec, 2019：https://people.bu.edu/staro/WiSec2019_RSSI_MisbehaviorDetection_CameraReady.pdf
26. Sybil Attack Detection Based on Signal Clustering in Vehicular Networks：https://www.researchgate.net/publication/381204582
27. Physical Signal-Driven Fusion for V2X Misbehavior Detection：https://www.researchgate.net/publication/340623909
28. Securing V2X Communication Platforms（综述）, arXiv:2003.07191：https://arxiv.org/pdf/2003.07191
29. Toward Trusted and Swift UAV Communication: ISAC-Enabled Dual Identity Mapping, arXiv:2306.17350：https://arxiv.org/pdf/2306.17350
30. Integrated Sensing and Communication for Low-Altitude Security, arXiv:2601.13810：https://arxiv.org/pdf/2601.13810
31. H. Amin et al., Hybrid PLS-ML Authentication Scheme for V2I Communication Networks, 2023：https://arxiv.org/abs/2308.14693
32. TRUST-V: Cross-Layer Misbehavior Detection in Vehicular Safety Communications（预印本, 2026.10）：https://www.preprints.org/manuscript/202610.2376
33. V2X-PAD: A Physical-Aware Spatio-Temporal Dataset for V2X Misbehavior Detection：https://ieee-dataport.org/documents/v2x-pad-physical-aware-spatio-temporal-dataset-v2x-misbehavior-detection

### 方向 D：密钥生成
34. X. Li, V. C. Andrei, P. J. Gu, Y. Chen, U. J. Mönich, H. Boche, Variational Secret Common Randomness Extraction, arXiv:2510.02048：https://www.arxiv.org/abs/2510.02048
35. K. Liu, K. Huang et al., Secure Integrated Communications and Sensing Using Physical Layer Key Generation, IEEE TVT, 2026：https://research.nottingham.edu.cn/en/publications/secure-integrated-communications-and-sensing-using-physical-layer/
36. Secret Key Generation via Localization and Mobility, arXiv:1112.2793：https://arxiv.org/pdf/1112.2793
37. The Passive Eavesdropper Affects my Channel: Secret-Key Rates under Real-World Conditions, arXiv:1701.03904：https://arxiv.org/pdf/1701.03904
38. M. Bottarelli et al., Adaptive and Optimum Secret Key Establishment for Secure Vehicular Communications, IEEE TVT, 2021：https://wrap.warwick.ac.uk/id/eprint/147758

### 方向 E：隐蔽感知与隐蔽通信
39. SNF-PRP: A Covert ISAC Framework, arXiv:2606.03960：https://arxiv.org/html/2606.03960v2
40. Q. Shi et al., Waveform Design for MIMO Covert Sensing and Communications：https://bura.brunel.ac.uk/bitstream/2438/33136/1/FullText.pdf
41. Double-Covertness in ISAC（联合截获概率 JIP）：https://bura.brunel.ac.uk/bitstream/2438/32969/3/FullText.pdf
42. Y. Wu et al., Covert ISAC: Towards Collusive Detection, ICC 2025：https://discovery.ucl.ac.uk/id/eprint/10215962
43. H. Lei et al., Covert Communication in Dual-UAV-aided ISAC Systems with Collusive Wardens, IEEE IoT-J, 2026：https://pure.bit.edu.cn/en/publications/covert-communication-in-dual-uav-aided-isac-systems-with-collusiv/
44. J. Hu et al., Near-Field Integrated Sensing and Covert Communications with Multiple Targets as Wardens, 2026：https://ro.ecu.edu.au/ecuworks2022-2026/7681

### 方向 F：硬件与 AI
45. Exploiting Phase Noise for Sensing Privacy in ISAC Systems, arXiv:2608.13270：https://arxiv.org/pdf/2608.13270
46. B. Kim, Y. E. Sagduyu, T. Erpek, S. Ulukus, Adversarial Attacks on Deep Learning Based mmWave Beam Prediction in 5G and Beyond, arXiv:2103.13989：https://arxiv.org/abs/2103.13989
47. Security Risks in Vision-Based Beam Prediction: From Spatial Proxy Attacks to Feature Refinement, arXiv:2504.05222：https://arxiv.org/pdf/2504.05222
48. Adversarial Security Mitigations of mmWave Beamforming Prediction Models (NTNU, 2022)：https://ntnuopen.ntnu.no/ntnu-xmlui/handle/11250/3112802
