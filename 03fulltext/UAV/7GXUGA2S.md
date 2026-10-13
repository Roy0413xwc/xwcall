---
title: "Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource Allocation for Cooperative Communication and Non-Cooperative Localization"
zotero_key: "7GXUGA2S"
pdf_key: "PT5TIB2R"
doi: "10.1109/TCOMM.2025.3642742"
collection: "UAV"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Optimal Transport Framework for ISAC in Low-Altitude Networks: Joint Resource Allocation for Cooperative Communication and Non-Cooperative Localization — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

1984 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Optimal Transport Framework for ISAC in
Low-Altitude Networks: Joint Resource Allocation
for Cooperative Communication and
Non-Cooperative Localization
Yufeng Zheng
 , Student Member, IEEE, Lixin Li
 , Member, IEEE, Wensheng Lin
 , Member, IEEE,
Wei Liang
 , Senior Member, IEEE, Qinghe Du
 , Member, IEEE, and Zhu Han
 , Fellow, IEEE
Abstract—The proliferation of unmanned aerial vehicles
(UA Vs) in low-altitude airspace necessitates sophisticated
resource management supporting both cooperative commu-
nications and unauthorized intrusion detection. This paper
investigates joint optimization of cell association and power
allocation in integrated sensing and communication (ISAC)-
enabled low-altitude networks. We propose a novel dual-function
framework where ground base stations simultaneously provide
communication services to authorized UA Vs and localize non-
cooperative UA Vs for collision avoidance. We establish a channel
model capturing the relationship between communication rate
and sensing accuracy, formulating an optimization problem
that maximizes the weighted sum of system average sum rate
and localization quality of service (QoS). The problem jointly
optimizes cell association, communication power allocation, and
sensing power allocation under UA V localization QoS and
cooperative sum rate constraints. To solve the resulting mixed-
integer non-convex problem, we propose a joint optimization
algorithm based on optimal transport theory (J2OT) that
directly handles discrete variables without relaxation, avoiding
Received 2 July 2025; revised 20 October 2025; accepted 26 November
2025. Date of publication 11 December 2025; date of current version
2 January 2026. This work was supported in part by National Natural Science
Foundation of China under Grants 62571450 and 62101450, in part by Key
Research and Development Program of Shaanxi under Grant 2025CY-YBXM-
043, in part by the Young Elite Scientists Sponsorship Program by the China
Association for Science and Technology under Grant 2022QNRC001, in part
by Aeronautical Science Foundation of China under Grants 2022Z021053001
and 2023Z071053007, in part by the Open Fund of Intelligent Control
Laboratory, in part by the Open Fund of Key Laboratory of Radio Spectrum
Testing Technology (The State Radio monitoring center Testing Center),
Ministry of Industry and Information Technology, in part by NSF ECCS-
2302469, Amazon and Japan Science and Technology Agency (JST) Adopting
Sustainable Partnerships for Innovative Research Ecosystem (ASPIRE) JPM-
JAP2326. An earlier version of this paper was presented at the 2024 IEEE
Globecom Workshops [DOI: 10.1109/GCWkshp64532.2024.11100546]. The
associate editor coordinating the review of this article and approving it for
publication was M. J. Khabbaz. (Corresponding author: Lixin Li.)
Yufeng Zheng, Lixin Li, Wensheng Lin, and Wei Liang are with the
School of Electronics and Information, Northwestern Polytechnical Univer-
sity, Xi’an, Shaanxi 710129, China (e-mail: zhengyufeng@mail.nwpu.edu.cn;
lilixin@nwpu.edu.cn; linwest@nwpu.edu.cn; liangwei@nwpu.edu.cn).
Qinghe Du is with the School of Information and Communications
Engineering, Xi’an Jiaotong University, Xi’an 710049, China (e-mail:
duqinghe@mail.xjtu.edu.cn).
Zhu Han is with the Department of Electrical and Computer Engineering,
University of Houston, Houston, TX 77004 USA, and also with the Depart-
ment of Computer Science and Engineering, Kyung Hee University, Seoul
446-701, South Korea.
Digital Object Identiﬁer 10.1109/TCOMM.2025.3642742
accuracy losses of conventional approximation methods. J2OT
decomposes the problem using optimal transport-based cell
association optimization (OTC) and power allocation optimiza-
tion (OTP). Simulation results demonstrate J2OT’s superiority,
achieving 1.5 bits/s/Hz improvement in system objective and
7.5% reduction in localization Cram ´er-Rao bound compared to
Weighted Voronoi and Iterative Water-ﬁlling baseline methods.
Index Terms —Integrated sensing and communication, low-
altitude networks, cooperative communication, non-cooperative
localization, optimal transport theory.
I. I NTRODUCTION
A. Background and Motivations
T
HE rapid emergence of the low-altitude economy has cre-
ated a vibrant ecosystem leveraging airspace for diverse
services and applications [1], [2]. This transformation has
catalyzed unprecedented growth in unmanned aerial vehicle
(UA V) deployments, with multi-UA V cooperative networks
forming the operational backbone by enhancing mission
efﬁciency, operational reliability, and complementary function-
alities in complex environments [3], [4], [5], [6]. To further
empower this intelligent low-altitude economy ecosystem,
recent research has explored advanced technologies includ-
ing large artiﬁcial intelligence (AI) model deployment for
enhancing UA V network capabilities and optimizing resource
allocation strategies [7].
However, UA V proliferation in low-altitude airspace intro-
duces critical safety and efﬁciency challenges. First, non-
cooperative “black ﬂights” pose signiﬁcant risks to legitimate
operations, threatening property security and airspace integrity.
Detecting and localizing these non-cooperative UA Vs requires
active sensing capabilities, as they do not cooperatively
transmit position information through systems like global
navigation satellite system (GNSS). Second, for cooperative
UA Vs that do share position information, traditional GNSS
positioning faces severe limitations in dynamic low-altitude
environments due to signal obstruction and multipath effects,
necessitating alternative localization methods to ensure accu-
rate positioning.
The integration of sensing and communication (ISAC) tech-
nology emerges as a promising solution to these fundamental
0090-6778 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1985
challenges. Based on inherent similarities between commu-
nication and sensing technologies in frequency bands and
hardware architecture [8], [9], ISAC enables collaborative
enhancement of both functions under shared resources, meet-
ing diverse intelligent application requirements [10], [11].
Recognized by the International Telecommunication Union
(ITU) as a primary sixth-generation (6G) application scenario,
ISAC has been highlighted for its critical importance in future
mobile communication systems.
ISAC application in low-altitude networks offers com-
pelling advantages: reducing hardware costs while improving
spectrum efﬁciency through shared spectrum and hardware
resources, enabling real-time UA V location sensing with min-
imal resource consumption, thereby enhancing ﬂight safety
and multi-UA V cooperation [12], [13]. Furthermore, coopera-
tive UA V position data enables optimized resource allocation
strategies that improve network communication performance.
ISAC provides comprehensive distance measurement, angle
measurement, and localization capabilities, supporting critical
operations including intrusion detection, collision avoidance,
and path tracking for comprehensive UA V monitoring and
control.
B. Related Works
ISAC technology integrates communication and sensing
functions through shared spectrum, hardware, and signal
resources, offering substantial beneﬁts for next-generation
wireless systems. Early foundational research established theo-
retical frameworks for performance analysis and optimization.
Meng et al. [14] developed high-accuracy extended Kalman
ﬁlter beam prediction schemes through interactive multi-
mode transformation. Ren et al. [15] analyzed performance
trade-offs in ISAC systems for simultaneous information mul-
ticasting and multi-target sensing. He et al. [16] investigated
full-duplex ISAC systems, optimizing energy consumption
through joint uplink beamforming and power control. While
these studies provided important theoretical foundations,
they primarily focused on ground-based networks, leaving
ISAC design for three-dimensional aerial environments largely
unexplored.
The unique characteristics of aerial networks—three-
dimensional mobility, dynamic channel conditions, and strin-
gent safety requirements—have motivated ISAC research
speciﬁcally for UA V systems. Ensuring rigorous statis-
tical quality of service (QoS) provisioning in complex
three-dimensional network environments remains a funda-
mental challenge [17], [18]. Recent coordination approaches
have explored various optimization strategies, Luo et al.
[19] employed graph neural networks for resource allo-
cation in digital twin-enhanced radar networks, while
Fei et al. [20] comprehensively reviewed air-ground inte-
grated sensing and communications with UA Vs as relay
nodes. Wang et al. [21] addressed utility maximization in
dual-functional radar-communication networks through joint
optimization approaches. Building on these foundations,
Deng et al. [22] introduced adaptive ISAC mechanisms that
dynamically adjust sensing duration based on application
requirements. Meng et al. [23] investigated joint resource
allocation and trajectory optimization in ISAC-enabled UA V
networks, achieving minimal power consumption. Zhao et al.
[24] proposed channel estimation methods through joint UA V
sensing, data transmission, and control design. However, these
studies focus exclusively on cooperative scenarios without
considering non-cooperative intrusion detection challenges
that our work speciﬁcally targets.
Low-altitude airspace increasingly faces challenges from
non-cooperative UA Vs, including unauthorized “black ﬂights”
that create collision risks and interference threats. While
prior work has addressed secure resource management and
eavesdropping protection in UA V networks [25], [26], existing
UA V-ISAC research inadequately addresses these safety con-
cerns, neither considering collision risks from non-cooperative
intrusions nor leveraging sensed location information to
enhance multi-UA V collaboration through collision avoidance.
This represents a signiﬁcant gap in ensuring safe operations
in congested low-altitude environments where cooperative and
non-cooperative UA Vs coexist.
Joint optimization of adaptive resource allocation in
ISAC-enabled UA V networks presents signiﬁcant challenges,
particularly when simultaneously supporting cooperative com-
munication and non-cooperative localization. Recent efforts
have made progress: Cao et al. [27] transformed noncon-
vex power allocation problems into linear programming
for cell-free ISAC systems. Gong et al. [28] developed
environment-aware ofﬂoading for joint task scheduling.
Qin et al. [29] employed deep reinforcement learning for time-
varying resource allocation, optimizing multiple parameters to
maximize minimum weighted spectral efﬁciency.
However, existing approaches face critical limitations.
They typically substitute discrete variables with continu-
ous approximations in mixed-integer nonconvex problems,
potentially compromising optimality. More importantly, these
methods lack speciﬁc design for systems requiring simulta-
neous cooperative communication among authorized UA Vs
and non-cooperative localization of unauthorized UA Vs.
The resulting optimization problems demand sophisticated
multi-dimensional strategies encompassing cell associa-
tion, sensing power distribution, and communication power
allocation.
C. Contributions
Motivated by identiﬁed research gaps and practical require-
ments, we investigate ISAC-enabled low-altitude networks
where dual-function ground base stations provide ISAC ser-
vices to cooperative UA Vs while simultaneously detecting
non-cooperative UA Vs’ positions. Unlike previous work that
exclusively utilized ISAC sensing for cooperative UA Vs,
we propose a novel cooperative communication and non-
cooperative localization methodology that employs ISAC
signals to locate non-cooperative UA Vs, preventing collisions
and interference with cooperative ﬂight trajectories. We estab-
lish a comprehensive channel model relating communication
rate to sensing accuracy and systematically analyze how loca-
tion sensing errors impact communication performance. We
formulate and solve the weighted sum maximization problem
of system average rate and localization QoS through joint
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

1986 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
optimization of cell association, communication power alloca-
tion, and sensing power allocation. To address this challenging
mixed-integer nonconvex optimization problem, we propose a
joint optimization algorithm based on optimal transport theory
(J2OT) that achieves high-quality solutions.
Building upon our previous work [30], this journal extension
introduces three key enhancements. First, we replace simplistic
line-of-sight assumptions with probability-based LoS models
for improved realism. Second, we extend analysis from single
to multiple non-cooperative UA Vs, revealing critical trade-offs
between communication rate and localization accuracy. Third,
we analyze how location sensing errors affect communication
performance, demonstrating that errors beyond speciﬁc thresh-
olds signiﬁcantly degrade rates. These advancements establish
a robust framework for resource allocation in ISAC-enabled
low-altitude networks that effectively balances cooperative
communication and non-cooperative localization requirements.
The main contributions are summarized as follows:
• We develop a novel ISAC-enabled low-altitude net-
work framework addressing the competitive dual-function
resource allocation problem , where base stations simul-
taneously provide communication services to cooperative
UA Vs and perform localization for non-cooperative
UA Vs—a dual-function scenario not addressed by exist-
ing ISAC formulations focusing exclusively on coop-
erative users. Our framework captures the fundamental
competitive coupling where resources allocated to sensing
directly reduce those available for communication, with
the established channel model quantifying how location
sensing errors degrade communication performance.
• We formulate joint optimization of cell association and
power allocation to maximize the weighted sum of
system average sum rate and localization QoS under
heterogeneous objective spaces—combining information-
theoretic metrics (bits/s/Hz) with estimation-theoretic
metrics (CRB in meters). This mixed-integer nonconvex
problem incorporates tightly coupled constraints (local-
ization QoS, sum rate requirements, total power budget)
and represents a new optimization class requiring novel
theoretical solutions.
• To solve this problem, we propose J2OT with three
theoretical innovations: (i) Theorem 1 extending Monge-
Kantorovich optimal transport theory to dual-function
ISAC, deriving optimal cell association where trans-
port costs depend on both communication quality and
sensing geometry; (ii) Direct discrete optimization via
semi-discrete OT that exactly handles binary vari-
ables without relaxation, avoiding suboptimality gaps;
(iii) Proven convergence (Proposition 1) to stationary
points with monotonic improvement. J2OT decomposes
into OT-based cell association (OTC) and Kantorovich
duality-based power allocation (OTP).
• Simulations validate J2OT’s superiority: 1.5 bits/s/Hz
improvement and 7.5% CRB reduction versus base-
lines. We quantify fundamental trade-offs: doubling
non-cooperative UA Vs (4 → 8) degrades sum rate by
15% ( 145 → 124 bits/s/Hz) and localization accuracy
by 14.6% (CRB: 0.041 → 0.047). Critically, location
Fig. 1. The system model in ISAC-enabled low-altitude network.
sensing errors exceeding speciﬁc thresholds cause up
to 2.5% communication degradation, establishing the
importance of precise localization in dual-function ISAC
systems.
The remainder of this paper is organized as follows.
Section II presents the ISAC-enabled low-altitude network
system model and problem formulation. Section III provides
problem analysis, introduces optimal transport theory funda-
mentals, and proposes our J2OT solution approach. Section IV
validates J2OT’s effectiveness and demonstrates how location
sensing errors beyond speciﬁc thresholds impact system com-
munication rates. Section V concludes the paper.
II. S YSTEM MODEL
In this section, we introduce the network model, com-
munication model, and sensing model for cooperative com-
munication and non-cooperative localization in ISAC-enabled
low-altitude network. Next, we formulate the problem to
maximize the weighted sum of the system’s average sum rate
and localization QoS.
A. Network Model
We consider an ISAC-enabled multi-UA V network where
multiple dual-function ground base stations provide ISAC
services to cooperative UA Vs while simultaneously detecting
the positions of non-cooperative UA Vs. The system comprises
M multi-antenna dual-function ground base stations, K +J
UA Vs, and a control center, where the UA Vs consist of K
single-antenna cooperative UA Vs and J single-antenna non-
cooperative UA Vs, as illustrated in Fig. 1. Notably, Fig. 1
depicts a representative scenario where both cooperative and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1987
non-cooperative UA Vs are positioned within the same beam-
formed signal coverage area (shown as the shaded beam
cone). In this conﬁguration, when the base station trans-
mits ISAC signals toward a cooperative UA V (green solid
arrows), any non-cooperative UA V spatially intersecting this
signal path passively scatters portions of the signal, generating
echo reﬂections (red dashed arrows) that enable position
detection.
The coordinates of the i-th UA V are denoted as ~Ui(n) =
(xu,i(n),yu,i(n), zu,i(n)), the coordinates of the m-th dual-
function ground base station are represented as ~Bm(n) =
(xb,m(n),yb,m(n), zb,m(n)).
Index Conventions: We adopt the following indexing con-
ventions throughout this paper: k ∈ {1, 2,...,K }: index
for cooperative UA Vs, 𝓁 ∈ {K + 1,K + 2, ...,K +J}:
index for non-cooperative UA Vs, i ∈ {1, 2,...,K + J}:
index for all UA Vs (both cooperative and non-cooperative),
m ∈ {1, 2,...,M }: index for dual-function ground base
stations.
We deﬁne cooperative communication as the coor-
dination mechanism among multiple cooperative UA Vs,
while non-cooperative localization refers to the process by
which ground base stations determine non-cooperative UA V
locations.
Furthermore, as depicted in Fig. 2, the system frame is
divided into three distinct phases [31]:
• Phase 1 (Downlink ISAC Transmission, Ts): Dual-
function ground base stations transmit beamformed ISAC
signals toward cooperative UA Vs. Cooperative UA Vs
receive these signals for channel estimation. Simultane-
ously, the transmitted ISAC signals propagate through the
beamformed coverage area. Any non-cooperative UA Vs
spatially intersecting these propagating signals passively
scatter portions of the waveform, characterized by their
radar cross-sections. The scattered echo returns are cap-
tured by the base station, generating preliminary target
signatures for initial detection.
• Phase 2 (Uplink Feedback and Echo Processing,
Tf ): Cooperative UA Vs transmit uplink signals contain-
ing: First, estimated channel state information, second,
current position coordinates, and third, unique iden-
tiﬁcation codes. Base stations process echo signals
collected in Phase 1 and distinguish non-cooperative UA V
echoes from expected cooperative UA V signatures using
position-based prediction.
• Phase 3 (Data Transmission and Precise Sensing, Tc):
Base stations ﬁrst execute precise localization through
monostatic radar operation: transmitting high-resolution
sensing pulses toward detected non-cooperative UA V
positions (downlink dashed line) and receiving the
reﬂected echo returns (uplink dashed line). After col-
lecting and processing echo signals, base stations report
precise non-cooperative UA V locations to the control
center (solid line). The control center then computes
collision avoidance strategies and distributes commands
to base stations (solid line). Finally, base stations
perform dual functions: transmitting data to coopera-
tive UA Vs at their conﬁrmed positions and relaying
collision avoidance information to prevent collisions
(solid line).
The ISAC service cycle has total durationT =Ts+Tf +Tc.
In typical conﬁgurations, time allocations are Ts≈ 0.3T for
sensing signal transmission, Tf ≈ 0.1T for uplink feedback
and processing, and Tc≈ 0.6T for data communication and
high-resolution sensing. Importantly, Phase 2 involves only
uplink transmission and signal processing without downlink
data communication, reducing the effective downlink trans-
mission time to Tc per cycle.
We deﬁne the spatial distribution function f (x,y, z) to
represent the probability of a UA V appearing around three-
dimensional location q = (x,y, z). Given M dual-function
ground base stations, the space is divided into three-
dimensional cells, each representing the area served by a base
station. Qm denotes the cell associated with the m-th base
station, and the average number of cooperative UA Vs within
Qm is [32]
Um =K
∫
Qmf(q)dq, (1)
where the spatial distribution function f(q) = f(x,y, z)
captures the probability of each UA V user appearing around
the three-dimensional location q = (x,y, z).
Let ak,m(n) ∈ {0, 1} denote the scheduling variable
between them-th ground base station and thek-th UA V , where
k∈{ 1,··· ,K}. In this paper, only the ground base station
is scheduled to sense the location information of the non-
cooperative UA V . If~Uk∈Qm,ak,m(n) = 1, which indicates
that the i-th UA V is provided with ISAC or sensing service
by the m-th base station at the n-th time slot. Otherwise,
ak,m(n) = 0.
Each ground base station is equipped with Nt antenna
elements with a uniform planar array. The location of theen-th
antenna at the m-th ground base station is denoted as £m,en.
The departure angles from the m-th ground base station to
thei-th UA V are denoted asθi,m = [θazi,m,θeli,m]T , where θazi,m
andθeli,m represent the azimuth and elevation departure angles,
respectively, measured from the base station’s perspective.
Based on the geometric relationships between the base station
and UA V positions, the departure angles can be calculated as
θazi,m ∆=a tan 2([~Bm]2− [~Ui]2, [~Bm]2− [~Ui]1),
θeli,m ∆= arccos
(
[~Bm]3− [~Ui]3
‖~Bm− ~Ui‖
)
. (2)
B. Communication Model
The distinction between line-of-sight (LoS) and non-line-
of-sight (NLoS) channel gains necessitates the incorporation
of a LoS probability factor to appropriately weight the con-
tributions of each propagation scenario. The LoS probability,
denoted by PLoS, is a function of the geometric relationship
between the UA V and the base station, as well as environment-
speciﬁc parameters. We adopt the following expression for the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

1988 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
LoS probability [33] 1
Pi,mLoS = 11 +b1 exp (−b2|Θi,m−b1|) (3)
where Θi,m denotes the elevation angle between the i-th UA V
and the m-th base station, b1 and b2 are environment-speciﬁc
parameters (rural, urban, dense urban, or others).
The actual channel vector from the m-th base station to the
k-th cooperative UA V can be expressed as
hk,m(n)= λejϕk,m(n)4πdk,m(n)αk,m(n)·( 1PLoSµLoS+PNLoSµNLoS),
(4)
where dk,m(n) =
‖‖‖~Bm(n)− ~Uk(n)‖‖‖ represents the actual
distance between the m-th ground base station and the
k-th UA V ,αk,m(n) is the antenna array response vector based
on the actual departure angles, ϕk,m(n) represents the phase
shift, and µLoS and µNLoS represent the shadowing fading
constants corresponding to LoS and NLoS communication
links, respectively.
After completing phases 1 and 2, the ground base station
acquires estimated channel state information for each UA V
based on the estimated location ˆUk(n). The estimated channel
vector is given by
ˆhk,m(n)= λej ˆϕk,m(n)
4πˆdk,m(n)ˆαk,m(n)·
( 1
PLoSµLoS+PNLoSµNLoS
)
,
(5)
where λ is the wavelength of the carrier signal, ˆαk,m(n)
represents the estimated response vector of the antenna array,
which can be calculated based on the estimated location by
(2), ˆdk,m(n) denotes the estimated distance from thek-th UA V
to them-th base station, and ˆϕk,m(n) represents the estimated
phase shift.
The channel estimation error is deﬁned as the difference
between the actual and estimated channels
∆hk,m(n) =hk,m(n)−ˆhk,m(n). (6)
Under the assumption that localization errors are small
(∆dk,m(n)≪ dk,m(n)) and angle estimation is sufﬁciently
accurate (αk,m ≈ ˆαk,m), we expand the distance-dependent
term using
1
dk,m
− 1ˆdk,m = ˆdk,m−dk,mdk,m ˆdk,m = −∆dk,mdk,m ˆdk,m≈−∆dk,md2k,m , (7)
where ∆dk,m(n) = dk,m(n)− ˆdk,m(n) represents the local-
ization distance error. The approximation holds when dk,m≈
ˆdk,m. Substituting this into the channel error expression yields
∆hk,m≈ λαk,m4πd2k,mejϕk,m (−∆dk,m)
· (µLoSPLoS +µNLoSPNLoS) (8)
1While our probabilistic LoS model is well-suited for low-altitude UA V
scenarios, the framework can be extended to general fading channels (e.g.,
Rayleigh for NLoS, Rician for LoS, or Nakagami- m models) by incorpo-
rating small-scale fading statistics into Eq. (4). However, such extensions
introduce challenges in deriving tractable closed-form CRB expressions
(Eqs. (21)–(22)), as sensing accuracy becomes dependent on instantaneous
fading realizations rather than path loss alone—an important direction for
future research.
The downlink data signal xk,mc (n) sent by the m-th base
station to the k-th cooperative UA V can be represented as
xk,mc (n) =
√
pk,mc (n)fk,m(n)sk,mc (n), (9)
where pk,mc (n) denotes the communication transmit power,
fk,m(n) denotes the transmit beamforming vector at the multi-
antenna base station, and sk,mc (n) denotes the data symbols.
Since each UA V is equipped with a single antenna, the com-
munication signal yk,mc (n) received by the k-th cooperative
UA V from them-th ground base station can be expressed as
yk,mc (n) =
√
pk,mc (n)(ˆhk,m(n) + ∆hk,m(n))H
·fk,m(n)sk,mc (n−τk,m) +b(n), (10)
where τk,m = dk,m(n)/c represents the propagation delay
between the k-th UA V and m-th base station, expressed in
terms of time slots.b(n) denotes additive white Gaussian noise
with zero mean and N0/2 two-sided power spectral density,
τk,m represents the propagation delay, and the beamforming
vector fk,m(n) is designed based on the estimated channel
ˆhk,m(n).
The signal-to-noise ratio (SNR) received by the k-th UA V
is given by
SNRk(n) =ak,m(n)
pk,mc
⏐⏐⏐(ˆhk,m + ∆hk,m)Hfk,m⏐⏐⏐2
∑
i⁄=kpci,m
⏐⏐⏐hHi,mfi,m⏐⏐⏐2 +N0 , (11)
where ak,m(n) denotes the user scheduling variable that
indicates whether the k-th UA V is served by the m-th base
station.
The sum rate of all cooperating UA Vs can be expressed as
Rsum =
K∑
k=1
N∑
n=1
bk,m(n) log2[1 + SNRk,m(n)], (12)
where bk,m(n) denotes the bandwidth allocated to the k-th
UA V by them-th base station during the n-th time slot.
Note that Rsum represents the instantaneous sum rate
achieved during the Phase 3 data transmission period Tc. The
effective system throughput over the complete ISAC service
cycle T is given by Reff = Rsum· (Tc/T ). Since the time
fraction Tc/T is a ﬁxed system parameter rather than an
optimization variable, it acts as a constant multiplicative factor
that scales all rate terms equally in the objective function.
Consequently, it does not affect the optimal resource allocation
solution. Therefore, following standard practice in wireless
resource allocation, we formulate the optimization problem
using the instantaneous rate Rsum, which simpliﬁes the math-
ematical formulation without any loss of optimality.
C. Sensing Model
The system employs monostatic radar sensing where each
base station operates in full-duplex mode to simultaneously
transmit sensing signals and receive echo signals from UA Vs.
Each base station independently detects non-cooperative UA Vs
that spatially intersect its beamformed communication paths,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1989
following a round-trip signal propagation: Base Station →
UA V→ Base Station.
The sensing pilot signal transmitted by the m-th base
station toward the i-th UA V is denoted as xi,ms (n), where
i∈{ 1,··· ,K +J}. This signal can be expressed as
xi,ms (n) =
√
pi,ms (n)fi,m(n)si,ms (n), (13)
where pi,ms (n) denotes the sensing transmit power allocated
to detect the i-th UA V by them-th base station at time slot n,
fi,m(n) represents the Nt× 1 transmit beamforming vector,
and si,ms (n) represents the pilot signal with unit amplitude,
i.e., E[|si,ms (n)|2] = 1.
The baseband echo signal received by the m-th ground base
station from the i-th UA V experiences round-trip propagation
and scattering effects. It can be expressed as
yi,ms (n) =
√
pi,ms (n)√σRCS,iwi,m(n)H
×hi,m(n)hi,m(n)Tfi,m(n)
×si,ms (n− 2τi,m) +b(n), (14)
whereσRCS,i represents the radar cross-section of thei-th UA V ,
accounting for scattering loss and UA V material properties,
hi,m(n) denotes theNt×1 composite channel vector between
the i-th UA V and them-th base station, σRCS,i represents the
radar cross-section of the i-th UA V , accounting for scattering
loss and UA V material properties, wi,m(n) is the Nt× 1
receive beamforming vector at the m-th base station for
sensing purposes, 2τi,m = 2‖ ~Bm− ~Ui‖c denotes the round-
trip propagation delay between the i-th UA V and the m-th
base station, where c denotes the speed of light, ~Ui denotes
the coordinates of the i-th UA V ,b(n) denotes additive noise
including thermal noise and residual self-interference.
Note that the factorhi,m(n)hi,m(n)T represents the round-
trip channel effect, where the signal travels from the base
station to the UA V and back to the base station.
The composite channel hi,m(n) can be expressed as
hi,m(n) =ςi,m(n)αi,m(n), (15)
where ςi,m(n) = |ςi,m(n)|ejϕi,m(n) denotes the composite
channel gain, andαi,m(n) is the antenna array response vector
computed using (2) for the i-th UA V .
The channel gain magnitude|ςi,m| and the antenna response
vectorαi,m(n) can be respectively expressed as
|ςi,m| = λ4πdi,m·( 1PLoSµLoS +PNLoSµNLoS), (16)
αi,m(n) =ejQTi,mκθi,m(n), (17)
where di,m = ‖~Bm− ~Ui‖ is the distance between the
m-th base station and i-th UA V , λ denotes the carrier
wavelength, PLoS and PNLoS are the LoS and NLoS proba-
bilities, respectively, deﬁned in equation (3). µLoS and µNLoS
represent the shadowing fading constants, and Qi,m(n) =
[£m,1(n),··· , £m,Nt(n)] represents the 3× Nt matrix of
antenna element positions at the m-th base station.
The spatial frequency vector κθi,m(n) is expressed as
κθi,m(n) = 2πλ [sinθel(n) cosθaz(n),
sinθel(n) sinθaz(n), cosθel(n)]T, (18)
where θel(n) and θaz(n) represent the elevation and azimuth
departure angles, respectively.
Target localization determines position through distance and
azimuth estimation, with different targets requiring varying
precision levels based on criticality and geometric charac-
teristics. This paper introduces localization quality of service
(QoS) [34]. While mean square error (MSE) commonly evalu-
ates estimator performance, deriving closed-form expressions
proves challenging. Consequently, the CRB serves as a theo-
retical lower bound for MSE. Although CRB expressions vary
with system conﬁguration and signal structure, a generalized
form for sensing the i-th UA V is [34]{
CRB(di(n))∝ (pi,ms |ςi(n)|2B2rms,i(n))−1,
CRB(θi(n))∝ (pi,ms (n)|ςi(n)|2WNN(n))−1, (19)
where pi,ms (n) denotes the transmit power for sensing UA V
signals, Brms,i(n) and WNN(n) represent the effective band-
width and the null-to-null beam width of the receiving antenna,
respectively. The effective bandwidth Brms can be expressed
as [34]
B2rms(n) =
∫
Bf2|X(f)|2df∫
B|X(f)|2df ≈ B(n)2π2Tpulse(n), (20)
where X(f) represents the Fourier transform of the time
domain waveform x(n), B(n) is the signal bandwidth, and
Tpulse(n) is the pulse duration.
Since localization focuses on estimating target distance and
angle of arrival at the base station, the localization error is
deﬁned as the CRB of target distance estimation and angle of
arrival estimation from the UA V to the base station, which is
expressed as
CRB(di(n)) = β1
pi,ms (n)|ςi,m(n)|2bi(n), (21)
CRB(θi(n)) = β2
pi,ms (n)|ςi,m(n)|2, (22)
where β1 and β2 denote the scaling factors, which are con-
stants inﬂuenced by the system conﬁguration, signal design
and beamforming gain, and bi(n) represents the bandwidth
allocated for sensing the i-th UA V .
By transforming the minimization problem of the CRB into
the maximization problem of its inverse, the target localization
quality parameters for the i-th sensing target can be expressed
as
ρi = ϖ1CRB(di(n)) + ϖ2CRB(θi(n))
=ϖ1
pi,ms (n)|ςi,m(n)|2bi(n)
β1
+ϖ2
pi,ms (n)|ςi,m(n)|2
β2
,
(23)
where ϖ1 and ϖ2 denote the normalization factors which
are used to unify the distance and departure angle units,
respectively, and ςi,m(n) represents the sensing channel gain.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

1990 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
The target parameters for all sensing targets can be
expressed as
ρsum =
K+J∑
i=1
ϖ1
pi,ms (n)|ςi,m(n)|2bi(n)
β1
+ϖ2
pi,ms (n)|ςi,m(n)|2
β2
. (24)
D. Problem Formulation
For simplicity, time slot n will be omitted in the follow-
ing. The cell association variable, the communication and
power allocation for sensing variable can be denoted as
Q ={Q∗1,··· ,Q∗M},Pc ={p1,1c ,··· ,··· ,pK,Mc } andPs =
{p1,1s ,··· ,pi,ms ,··· ,pK+J,Ms }, where ∀k ∈ {1,··· ,K},
∀m∈{ 1,··· ,M},∀𝓁∈{ 1,··· ,J} andi∈{ 1,··· ,K +J}.
The objective is to maximize the weighted sum of the system
average sum rate and average localization QoS by jointly
optimizing the cell association, communication and power
allocation for sensing under non-cooperative UA V localization
QoS and cooperative UA V sum rate constraints, and can be
formulated as
P1 : max
Q,Pc,Ps
GTOL =ϑ1
Rsum
K + (1−ϑ1)ϑ2
ρsum
K +J
s.t. C1 :Um =M
∫
Qmf(q)dq,
C2 :Qr∩Qt =∅,∀t⁄=r∈{ 1,··· ,M},⋃
m∈M
Qm =Q,
C3 :pmin≤pk,mc ,pi,ms ≤pmax,∀k∈{ 1,··· ,K},
∀m∈{ 1,··· ,M},∀i∈{ 1,··· ,K +J},
C4:
K∑
k=1
pck,m+
K+J∑
i=1
psi,m≤Ptotal,∀m∈{1,...,M }
C5 :ρi≥ρmin,∀k∈{ 1,··· , K + J},
C6 :Rmin≤Rk,∀k∈{ 1,··· , K}, (25)
where ϑ1 and 1−ϑ1 denote the weights assigned to commu-
nication rate and localization CRB, respectively. ϑ2 denotes
the sum rate-localization CRB mapping factor, ensuring that
the communication rate and localization CRB are on the same
scale level [35]. C1 denotes the number of cooperating UA V
users in the regionQm. C2 ensures that the three-dimensional
correlation spaces are disjoint and together covers the entire
space under consideration. C3 denotes the maximum and
minimum transmitting power constraints. C4 constrains the
total transmit power at each base station during Phase 3.
Since communication power and sensing power are drawn
from the same power ampliﬁer array, their sum cannot exceed
Ptotal. C5 denotes the UA V localization QoS constraints, where
localization QoS is deﬁned by the CRB of the distance and
the angle of arrival. C6 denotes the communication QoS
constraints.
Problem Structure Analysis: Problem P1 represents a fun-
damentally new optimization class due to three distinguishing
characteristics:
(i) Competitive resource coupling: C4 creates zero-sum
competition where communication power ∑Kk=1pk,mc
and sensing power ∑J𝓁=1p𝓁,ms share the same budget
Ptotal. This differs from prior ISAC formulations assum-
ing separate power budgets, and introduces fundamental
trade-offs absent in existing literature.
(ii) Heterogeneous objective spaces: The objective func-
tion combines information-theoretic metric ( Rsum in
bits/s/Hz) with estimation-theoretic metric ( ρsum from
CRB in meters). The normalization factor ϑ2 is essential
to unify incompatible scales—a challenge not addressed
in prior multi-objective ISAC work considering homo-
geneous metrics.
(iii) Coupled discrete-continuous optimization: Binary cell
association variables ak,m ∈ {0, 1} and continuous
power variables (Pc,Ps) are coupled through both
objective function and C3-C6. Standard approaches
using continuous relaxation ak,m ∈ [0, 1] introduce
suboptimality, motivating our novel OT-based direct
optimization approach.
These structural properties distinguish P1 from existing
ISAC optimization problems and necessitate the theoretical
and algorithmic innovations presented in Section III.
III. T HE OT-BASED JOINT CELL ASSOCIATION AND
POWER ALLOCATION OPTIMIZATION
This section introduces J2OT as our solution to problem
P1. We ﬁrst decompose P1 into two optimization subprob-
lems, then present the Monge-Kantorovich optimal transport
(OT) theory fundamentals. Subsequently, we detail our J2OT
approach, which alternately optimizes cell association and
power allocation until convergence.
P1 presents signiﬁcant challenges as a mixed-integer
nonconvex problem with binary and continuous variables
exhibiting complex coupling relationships. The high non-
convexity of both objective function and constraints renders
conventional convex transformation approaches ineffective,
often producing substantial accuracy errors.
Optimal transport theory offers a promising solution by
leveraging probability theory to capture wireless device distri-
bution patterns. OT excels at ﬁnding optimal matches between
continuous or discrete distributions while minimizing match-
ing costs, making it particularly suitable for mixed-integer
nonconvex problems.
Our proposed J2OT approach efﬁciently tackles P1 by
decomposing it into manageable subproblems and alternately
applying optimal transport for cell association (OTC) and
power allocation (OTP). Fig. 3 illustrates the complete J2OT
algorithm ﬂowchart.
Since OT is used to solve the minimization problem, the P1
is transformed into a different minimization problem, which
can be expressed as
P2 : min
Q,Pc,Ps
− GTOL =−ϑ1
Rsum
K − (1−ϑ1)ϑ2
ρsum
K +J
s.t. C1, C2, C3, C4, C5, C6 . (26)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1991
Fig. 2. The frame structure for cooperative communication and non-cooperative localization in ISAC-enabled low-altitude network.
Fig. 3. The algorithm ﬂowchart of J2OT.
A. The Monge-Kantorovich Problem of OT
Optimal transport theory examines minimal-cost resource
allocation between locations. Originating from the Monge
problem and expanded by Kantorovich, this framework seeks
optimal transport plans between probability distributions by
minimizing transportation costs.
The measurable space D ∈ Jn contains probability dis-
tribution µ, while measurable space V ∈ Rn contains
probability distribution o. Both spaces are governed by unit
cost function g(i,j ) and mapped according to the following
criteria:
∐
1
={H :D→V ;µ(H−1(E)) =o(E),∀E⊆V},
I(H) =
∫
g(i,H(i))dµ(i),
I(H0) = minH∈∐1I(H), (27)
where the optimal mapping H0 is designed to minimize the
initial cost function I (H0).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

1992 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
The Monge problem, characterized by its high nonlinearity,
dictates that each point in the source distribution must map
to a single location in the destination distribution. Kan-
torovich addresses this by introducing the Monge-Kantorovich
problem [37].
In the Monge-Kantorovich problem with continuous mea-
sures, given a probability distribution µ and o on the
measurable space D and V , respectively, and with the unit
cost function g(i,j ), the probability measure ω∈∐2 on the
spaceD×V can be formulated as
I(ω0) = minω∈∐2
∫
g(i,j )dω(i,j ), (28)
where ∐2 represents the complete probability measure that
satisﬁes the marginal distributions µ ando. The measure ω0
optimizes the cost functionI(ω0) andg (i,j ) can exhibit semi-
continuity within this context.
The optimal solution can be derived through the duality
theorem [38], and this can be equivalently formulated
I(ω0) = maxψ,φ
{∫
ψ(i)ω(i)di +
∫
φ(j)o(j)dj
ψ(i) +φ(j)≤g(i,j );i∈B,j ∈V}, (29)
where ψ (i) and φ (j) represent the Kantorovich potentials
that deﬁne the optimal mapping.
The Kantorovich pairwise theorem provides a viable
solution. The Monge problem coincides with the Monge-
Kantorovich solution only when both source distribution and
unit cost function are continuous [39]. Applying this theorem,
the Monge problem reformulates as a Monge-Kantorovich
problem, with optimal mapping expressed as
H(i) ={j|ψ∗(i) +φ∗(j) =g(i,j )}. (30)
B. Cell Association Design
For a given transmit power, the optimal cell association
optimization subproblem can be expressed as
P3 : min
Q
M∑
m=1
∫
Qm
1
Um
[−GTOLf(x,y, z)]dxdydz
s.t. C1, C2, C5, C6. (31)
Let z(Ul) = 1Ul and substituting into the (31), we can get
P4 : min
Q
M∑
m=1
∫
Qmz(Um)[−GTOLf(x,y, z)]dxdydz
s.t. C1, C2, C5, C6. (32)
P4 aligns with the OT framework, which determines opti-
mal mapping between probability distributions. In the classic
Monge problem, sand piles must be optimally transported to
pits to minimize overall transportation costs [40], with optimal
movement determined by the cost function.
The cell association subproblem P4 formulates as a semi-
discrete optimal transport problem, where base stations follow
discrete distributions and UA Vs follow continuous distribu-
tions. The objective is achieving optimal cell association by
mapping UA Vs to base stations with minimum cost [41]. We
solve P4 using the following theorem:
Theorem 1: Theorem 1 (Optimal Cell Association for
Dual-Function ISAC): For the competitive dual-function
resource allocation problem P4, the optimal cell association
mapping that minimizes the weighted transport cost under
shared power constraints is characterized by:
qM =
{
arg min
m∈{1,...,M}
[
− 1UmGTOL(q0) +GTOL(q0)UmK ]}
(33)
1) Signiﬁcance: This extends Monge-Kantorovich theory
to systems where: (i) transport costs depend on conﬂicting
objectives (communication vs. sensing); (ii) decisions are
coupled via shared constraint (C4); (iii) destination capacities
Um are mapping-dependent. These properties distinguish our
formulation from classical OT and necessitate the novel proof.
Proof: The existence of an optimal cell association Qm
can be veriﬁed by the existence of an optimal transport
mapping [41]. There exist two cells Qt, Qr and a point
q0 = (x0,y 0, z0) ∈ Qt. Let Oχ(q0) be a sphere centered
atq0 with radius χ> 0. We then generate the following new
three-dimensional partitioning ~Qm, which can be denoted as
~Qt =Ql/Oχ(q0),
~Qr =Qr∪Oχ(q0),
~Qm =Qm,m⁄=i,r. (34)
Since the set Qm is the optimal cell association, any cell
association derived from ~Qm will not surpass the optimality
of that obtained from Qm. Therefore, we can obtain
∫
Qi[z(Ut)− z(Ut−Uχ)]GTOLf(q)dq
+
∫
Oχ(q0)z(Ut−Uχ)GTOLf(q)dq
≤
∫
Qr[z(Ur +Uχ)− z(Ur)]GTOLf(q)dq
+
∫
Oχ(q0)z(Ur +Uχ)GTOLf(q)dq. (35)
We multiply 1Uχ on both sides of (35), and we can obtain
∫
Qi[z(Ut)− z(Ut−Uχ)]GTOLf(q)dq
Uχ
+
∫
Oχ(q0)z(Ut−Uχ)GTOLf(q)dq
Uχ
≤
∫
Qr[z(Ur +Uχ)− z(Ur)]GTOLf(q)dq
Uχ
+
∫
Oχ(q0)z(Ur +Uχ)GTOLf(q)dq
Uχ
. (36)
We take the limit when χ → 0 and let Uχ =
K
∫
Qχf(q)dq. Subsequently, we can get
lim
χ→0
Uχ = 0,
lim
Uχ→0
z(Ut)− [z(Ut)− z(Uχ)]
Uχ
= z′(Ut),
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1993
Algorithm 1 The OT-Based Cell Associations Optimization
Algorithm
Input: f(x,y, z), T1, K,Bm(n)
Output: Q∗m,m∈M
Initialization: t1 = 1 , generate initial cell associations
Q(t1)m , ℜ(t1 )m (q) = 0,q = (x,y, z),∀m∈{ 1,··· ,M}
1: while t1 <T 1 do
2: Computing
ℜ(t1+1)m (q)=
{
[1− 1/t1]ℜ(t1)m (q),if (q)∈Q(t1)m
1− [1− 1/t1][1−ℜ (t1)m (q)],otherwise
3: Computing Um =
∫
Q(1− ℜ(t1)m (q))f(x,y, z)dxdydz
4: t1←t1 + 1
5: Updating cell associations by (33)
6: end while
lim
Uχ→0
[z(Ur) + z(Uχ)]− z(Ur)
Uχ
= z′(Ur), (37)
lim
Uχ→0
∫
Oχ(q0)z(Ut−Uχ)GTOL (x,y, z)f(q)dq
Uχ
= lim
Uχ→0
z(Ui)GTOL (q0)
K , (38)
lim
Uχ→0
∫
Oχ(q0)z(Ur +Uχ)GTOLf(q)dq
Uχ
= z(Ur)GTOL (q0)K . (39)
We can calculate that z′(Ut) = dz(t)dt ⏐⏐t=Ut = − 1U 2i ,
z′(Ur) = dz(t)dt ⏐⏐t=Ur =− 1U 2r . Next, we substitute (37), (38)and (39) into (36). As a result, we obtain
− 1UtGTOL (q0) +GTOL (x,y, z)UtK
≤− 1UrGTOL (q0) +GTOL (x,y, z)UrK . (40)
Therefore, the optimal cell association for the m-th ground
base station can be expressed as
Q∗m =
{
(x,y, z)
⏐⏐⏐⏐− 1UtGTOL (x,y, z) +GTOL(x,y, z)UtK
≤− 1UrGTOL (x,y, z) +GTOL (x,y, z)UrK ,∀i⁄=m},
(41)
which proves the Theorem 1. ■
After the proof, (33) can be obtained from (41).
Using Theorem 1, the optimal cell association can be deter-
mined. However, mutual dependence between Um andQm in
(41) prevents an explicit solution. Therefore, we propose OTC
to solve (41), detailed in Algorithm 1, where ℜ(t1)m (x,y, z)
denotes predeﬁned cell partitioning parameters. The algorithm
converges to the optimal solution within reasonable iterations
[40], with computational complexity scaling linearly with
region size.
The OTC algorithm takes UA V distribution, base station
locations, and iteration limit as inputs, outputting opti-
mal cell association variables. It initializes Q(t1)m and sets
ℜ(t1)m (x,y, z) = 0,∀m∈{ 1,··· ,M}, then iteratively updates
ℜ(t1)m (x,y, z), calculates Um, and updates cell association
using (33) until convergence.
2) Convergence Analysis: The convergence of Algorithm 1
is guaranteed by the monotonic decrease of the transport cost
function in each iteration. Speciﬁcally, at iterationt1, the algo-
rithm updates the cell partitioning parameters ℜ(t1)m (x,y, z)
based on the gradient of the objective function with respect
to the current cell association. This update ensures that the
objective function value is non-increasing, i.e., −GTOL (t1 +
1)≤ −GTOL (t1). Since the objective function is bounded
below (due to physical constraints on communication rates and
sensing accuracy), the sequence of objective values converges
to a local optimum.
3) Computational Complexity: The computational com-
plexity of Algorithm 1 is primarily determined by the
numerical integration in Step 3, which can be efﬁciently imple-
mented using pixel-based methods as detailed in [36]. For a
three-dimensional space discretized into Nx×Ny×Nz grid
points, the complexity per iteration is O(MNxNyNz), where
M is the number of base stations. With typical convergence
occurring within T1 = 5-10 iterations, the overall complexity
remains O(MT1NxNyNz), which scales linearly with the
spatial resolution and is computationally tractable for practical
network dimensions.
C. Transmitting Power Design
For the given cell association, the transmitting power opti-
mization subproblem can be expressed as
P5 : min
Pc,Ps
− GTOL
s.t.C3, C4, C5, C6. (42)
P5 can be viewed as the problem of determining the optimal
transmission scheme with the optimal transmit power between
the user and the UA V . The source distribution is the transmit
power resource to be allocated by the base station, while
the destination distribution is the transmit power resource to
be received by the UA V . The transport cost −GTOL is the
negative of the sum rate. The optimal transport scheme is
the mappings of Pc ={p1,1c ,··· ,pK,Mc ,pK,Mc } and Ps =
{p1,1s ,··· ,pK+J,Ms ,pK,Ms }.
According the Monge-Kantorovich problem, P5 can be
rewritten as
min
Pc,Ps
−ϑ1
1
KRsum− (1−ϑ1)ϑ2
1
K +Jρsum
= min
Pc,Ps
− 1K
K∑
k=1
ϑ1Rk + 1K +J
K+J∑
i=1
(ϑ1− 1)ϑ2ρi
= max
ϕ,φ
∫
ψ(Pc)Ω(Pc)dPc +
∫
φ(Ps)(Ps)dPs
= max
ϕ,φ
∫ 1
K
K∑
k=1
ϑ1bk,mlog2 (1 +ak,m· SNRk)dPc
+
∫ 1
K +J
K+J∑
i=1
(
ϖ1
pj,ms |ςi|2bi
β1
+ϖ2
pi,ms |ςi|2
β2
)
dPs
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

1994 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Algorithm 2 OT-Based Power Allocation Algorithm
Input: ϑ1, ϑ2,ψ(Pc),φ(Ps)∈D, Ω(Pc), (Ps)∈V
Output: P∗c =Pt2c ,P∗s =Pt2s
Initialization: t2 = 1,φt
1: while‖∇F (φt)‖2≥ϑ2 do
2: h = 1, m1 = 1
3: Updatingφt+1 =φt +m∇F (φt)
4: if∇F (φt)<∇F (φt+1) then
5: while∇F (φt)<∇F (φt+1) do
6: h→h + 1, mh = 2h−1m1
7: updatingφt+1 =φt +mh∇F (φt)
8: end while
9: else
10: while∇F (φt)>∇F (φt+1) do
11: h→h + 1, mh = 2h−1m1
12: updatingφt+1 =φt +mh∇F (φt)
13: end while
14: end if
15: t←t + 1
16: end while
= max
ϕ,φ
∫ 1
K
K∑
k=1
ϑ1bk,mlog2 (1 +ak,m· SNRk)dPc
+
∫ 1
K +J
K+J∑
i=1
[(
ϖ1
bi
β1
+ϖ2
1
β2
)(
pi,ms |ςi|2
)]
dPs
s.t. ψ(Pc) = 1K
K∑
k=1
log2 (1 +ak,m· SNRk),
Ω(Pc) = 1K
K∑
k=1
ϑ1bk,m,
φ(Ps) = 1K +J
K+J∑
i=1
(
pi,ms |ςi|2
)
,
℧(Ps) = 1K +J
K+J∑
i=1
(
ϖ1
bi,m
β1
+ϖ2
1
β2
)
. (43)
To maximize (43), ψ andφ must be maximized within the
expected scope. And since it is necessary for any Pc∈D1
andPs∈V 1 to satisfyψ(Pc)+φ(Ps)≤−GTOL (Pc,Ps),
onceψ is determined, φ can be represented as
φ(Ps) =ψ(Pc) = inf{−GTOL (Pc,Ps)}− ψ(Pc), (44)
where inf represents the inﬁmum of the function.
At the same time, φ(Ps) can be simpliﬁed as
max
ψ,φ
F (φ) = max
ϕ,φ
∫
ψ(Pc)Ω(Pc)dPc
+
∫
φ(Ps)℧(Ps)dPs, (45)
where F () is the function name.
φ(Ps) can be transformed into a form that is easy to
calculate, as shown in (45). Solving the (45) will generate a
set of φ and the optimal power allocation scheme (Pc,Ps).
Calculating the ﬁrst-order derivative can solve the (45) using
the gradient descent method. It can be expressed as
∇F (φ) = ∂F (φ)∂φi
=
∫
Ω(Pc)dPc +
∫
(Ps)dPs
= 1K
K∑
k=1
ϑ1bk,mpck,m+ 1K+J
K+J∑
i=1
(
ϖ1
bi
β1
+ϖ2
1
β2
)
psi,m.
(46)
Therefore, OTP is shown in Algorithm 2.
D. The Joint Optimization Algorithm Based on Optimal
Transport Theory
P1 is solved by alternately solving P2 and P5 using OTC
and OTP, as shown in Algorithm 3.
Algorithm Computational Complexity : The complexity
of Algorithm 1 is primarily inﬂuenced by the numerical
integration required in Step 3 of Algorithm 1. One effec-
tive method for performing this integration is pixel-based,
as detailed in [40]. This method is highly practical, as its
computational complexity scales linearly with the size of
the three-dimensional space under consideration. This linear
relationship ensures that the method remains efﬁcient and
manageable even as the problem domain grows larger, making
it well-suited for real-world applications where the spatial
dimensions can vary signiﬁcantly.
The computational complexity of Algorithm 2 is inﬂuenced
byψ(Pc),φ(Ps) and∇F (φ). As a result, the computational
complexity of Algorithm 2 aligns with that of quadratic
programming, which is O (hK).
Convergence Analysis:
We now establish formal convergence guarantees for
Algorithm 3.
Proposition 1 (Convergence of J2OT): Algorithm 3
generates a sequence {GTOL(t3)}∞t3=1 that is monotoni-
cally non-decreasing. The corresponding objective function
sequence {−GTOL(t3)}∞t3=1 of problem P2 is monotoni-
cally non-increasing and converges to a stationary point
(Q∗,P∗c,P∗s ).
Proof:
Step 1 - Monotonicity of cell association update:
At iteration t3, given ﬁxed power allocation
(P (t3−1)c ,P (t3−1)s ), Algorithm 1 (OTC) solves:
Q(t3)∈ arg min
Q∈ΩQ
[
−GTOL
(
Q,P (t3−1)c ,P (t3−1)s
)]
(47)
By optimality of Q(t3):
−GTOL
(
Q(t3),P (t3−1)c ,P (t3−1)s
)
(48)
≤−GTOL
(
Q(t3−1),P (t3−1)c ,P (t3−1)s
)
(49)
Equivalently:
GTOL
(
Q(t3),P (t3−1)c ,P (t3−1)s
)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1995
≥GTOL
(
Q(t3−1),P (t3−1)c ,P (t3−1)s
)
(50)
Step 2 - Monotonicity of power allocation update:
Given updated cell association Q(t3), Algorithm 2 solves:
(P (t3)c ,P (t3)s )∈ arg min(Pc,Ps)∈ΩP
[
−GTOL
(
Q(t3),Pc,Ps
)]
(51)
By optimality of (P (t3)c ,P (t3)s ):
GTOL
(
Q(t3),P (t3)c ,P (t3)s
)
≥GTOL
(
Q(t3),P (t3−1)c ,P (t3−1)s
)
(52)
Combining these inequalities:
GTOL(t3) =GTOL
(
Q(t3),P (t3)c ,P (t3)s
)
≥GTOL
(
Q(t3−1),P (t3−1)c ,P (t3−1)s
)
=GTOL(t3− 1) (53)
This establishes monotonic non-decreasing property:
GTOL(t3)≥GTOL(t3− 1) for all t3≥ 1.
Step 3 - Boundedness:
The feasible set Ω = Ω Q× ΩP is compact: ΩQ is ﬁnite
(ﬁnite number of possible cell partitions), and ΩP is compact
(bounded by C3-C4: pmin ≤ pk,mc ,p𝓁,ms ≤ pmax). Since
GTOL(Q,Pc,Ps) is continuous on the compact set Ω, it is
bounded above:
GTOL(t3)≤GmaxTOL <∞, ∀t3 (54)
Step 4 - Convergence:
By the Monotone Convergence Theorem, a monotonically
non-decreasing sequence bounded above must converge:
lim
t3→∞
GTOL(t3) =G∗TOL (55)
Step 5 - Stationarity:
Any limit point (Q∗,P∗c,P∗s ) of the sequence satisﬁes ﬁrst-
order optimality conditions for both subproblems. By the
theory of alternating minimization [42], these conditions are
necessary for (Q∗,P∗c,P∗s ) to be a stationary point of the
original problem P2. □
Remark 1: The system performance metric GTOL =
ϑ1RsumK + (1− ϑ1)ϑ2ρsumK+J improves monotonically (non-
decreasing), while the minimization objective −GTOL in P2
decreases monotonically (non-increasing). This duality ensures
Algorithm 3 consistently improves system performance.
Remark 2: While global optimality cannot be guaranteed for
NP-hard mixed-integer problems, our direct handling of dis-
crete variables through semi-discrete OT reformulation avoids
the suboptimality gap introduced by continuous relaxation
methods. This structural advantage, combined with proven
convergence to stationary points, explains the 1.5 bits/s/Hz
performance gain observed in Section IV.
Remark 3: The convergence rate depends on problem con-
ditioning and initialization quality. Our simulations (Fig. 4)
demonstrate practical convergence within 6 iterations for real-
istic low-altitude network scenarios.
IV. N UMERICAL RESULTS
In this section, the superiority of J2OT for cooperative
communication and noncooperative localization in ISAC-
enabled low-altitude networks will be analyzed through
Fig. 4. The system objective function versus different number of iterations.
TABLE I
PARAMETERS SETTING [43], [44], [45]
simulation. According to [43], [44], [45], we set parameters
as Table I. In addition, we consider an area of size 2,00
m×1,000 m×1 ,000 m with 6 dual-functional ground base
stations and 16 UA V users. We use the estimation method
of the spatial distribution for UA V users to describe the user
probability density function, which is expressed as [46]
f(x,y, z) = 1K
K∑
i=1
1√
(2π)3hxhyhz
· exp
[
−
(
(x−xi)2
hx
+ (y−yi)2
hy
+ (z−zi)2
hz
)]
(56)
wherehx,hy andhz denote the kernel widths in the x,y and
z dimensions, respectively.
To verify the effectiveness of the J2OT, we compare it with
the Weighted V oronoi algorithm [46] and the iterative Water-
ﬁlling algorithm [47] as comparison algorithms:
• Weighted V oronoi: The method is utilized to achieve the
optimal cell association, and the optimal transmit power
is then determined using J2OT.
• Iterative water-ﬁlling: The iterative Water-ﬁlling algo-
rithm is used to obtain the optimal power, while J2OT
is applied for optimal cell association.
The relationship between the system objective function
and the number of iterations is given in Fig. 4. Iteration 0
represents the initial system state with distance-based cell
association and equal power distribution before optimization
begins. Iterations≥ 1 represent successive optimization steps.
The algorithm exhibits characteristic alternating optimization
behavior, with iterations 2-3 showing a plateau as the cell
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

1996 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Algorithm 3 The Joint Optimization Algorithm Based on
Optimal Transport Theory
Input: T3
Output: Q∗ =Qt3,P∗c =Pt3c ,P∗s =Pt3s , ℘
Initialization: t3 = 1
1: while t3 <T 3 and|GTOL (t3)−GTOL (t3− 1)|>℘ do
2: n = 1, m1 = 1
3: Given the transmit power, solve P3 by Algorithm 1
4: Given cell association, solve P4 by Algorithm 2
5: t3←t3 + 1
6: end while
Fig. 5. The CRB for non-cooperative UA V localization versus different
number of iterations.
association structure undergoes necessary adjustments—a typ-
ical pattern for non-convex mixed-integer problems where
algorithms navigate complex solution landscapes to escape
local optima. J2OT converges within 6 iterations, outperform-
ing baseline methods by approximately 0.37, by avoiding the
suboptimality of continuous relaxation. Speciﬁcally, treating
UA Vs as continuous probability distributions and base stations
as discrete measures, J2OT establishes a semi-discrete opti-
mization framework where Theorem 1 directly yields optimal
cell associations and the decomposition approach achieves
precise power allocation. This enables J2OT to avoid the
suboptimal results of Weighted V oronoi and local optima
limitations of Water-ﬁlling algorithms, effectively balancing
cooperative communication and non-cooperative localization
even with location sensing errors.
The relationship between the non-cooperative UA V localiza-
tion CRB and the number of iterations is given in Fig. 5, where
the localization CRB represents the combined metric (J)/ρsum
from Eq. (24), integrating both distance CRB (Eq. (21))
and angle CRB (Eq. (22)) through weighted summation. The
proposed J2OT algorithm demonstrates superior performance,
rapidly decreasing from 0.065 to stabilize at approximately
0.04 after the 1st iteration. The Weighted voronoi algo-
rithm stabilizes around 0.043, while the Iterative water-ﬁlling
algorithm plateaus at approximately 0.05. J2OT achieves
approximately 7.5% lower localization CRB than the Weighted
voronoi algorithm. This improved performance stems from
its three-phase approach coordinating channel sensing, feed-
back, detection, data transmission, and power allocation. This
Fig. 6. The system sum rate versus different number of antennas.
Fig. 7. The trade-off between system sum rate and localization CRB with
increasing non-cooperative UA Vs.
Fig. 8. The localization QoS and system sum rate versus the threshold of the
communication sum rate.
frame-structured methodology particularly beneﬁts non-
cooperative UA V sensing localization, with its iterative
implementation optimizing the system’s sensing and commu-
nication capabilities.
The relationship between the average sum rate and the
number of antennas is given in Fig. 6. As the number of
antennas increases, the system’s average sum rate steadily
improves across all algorithms. This enhancement results
from utilizing multiple antennas for data transmission, which
effectively exploits spatial diversity and multipath propagation
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1997
Fig. 9. The system sum rate versus the total allocation power: (a) ∆d = 0; (b) ∆d∼N (0.1, (0.375)2); (c) ∆d∼U (−0.1, 0.1).
to boost transmission rates. Notably, J2OT outperforms both
comparison algorithms, delivering approximately 1.5 bits/s/Hz
higher system sum rates than the Weighted V oronoi and
iterative Water-ﬁlling approaches. This performance advantage
becomes increasingly signiﬁcant at higher antenna counts,
where J2OT more effectively leverages the expanded spatial
diversity to jointly optimize cell association and power allo-
cation decisions.
The trade-off between system sum rate and localization
CRB with increasing non-cooperative UA Vs. is given in Fig. 7.
As the number of non-cooperative UA Vs increases from 4
to 8, the system sum rate decreases markedly from 145 to
124 bits/s/Hz, while the average localization CRB generally
rises from 0.041 to 0.047, with a slight ﬂuctuation between 6-7
UA Vs. This inverse relationship demonstrates that accommo-
dating additional non-cooperative UA Vs for sensing purposes
consumes communication resources, resulting in lower data
rates while simultaneously reducing localization accuracy as
sensing resources become distributed across more targets. To
maintain constant sum rate with varying non-cooperative UA V
numbers, the system would require either increased total power
budget, relaxed localization QoS constraints, or prioritized
resource allocation favoring communication—each represent-
ing different trade-offs between safety and communication
performance.
The localization QoS and system sum rate comparison
of different algorithms converging in the ISAC-enabled low-
altitude networks with different communication rate threshold
requirements is illustrated in Fig. 8. The relationship between
communication rate threshold and system performance in
ISAC-enabled networks reveals a fundamental trade-off: as
the rate threshold increases, the system sum rate decreases
from approximately 140 to 130 bits/s/Hz, while the localiza-
tion CRB rises from 11.9 to 13.0. This inverse relationship
stems from the limited power and channel resources avail-
able to ground dual-functional base stations. When higher
communication rate thresholds are imposed, the system must
allocate additional resources to meet these communication
demands, inevitably reducing resources available for sens-
ing operations. This resource reallocation directly impacts
the system’s sensing capabilities, resulting in diminished
localization accuracy as evidenced by the increasing CRB
values.
Fig. 10. The average sum rate versus the total power under different location
sensing error.
The relationship between the system’s average sum rate
and the total power, with a location sensing error of zero,
is depicted in Fig. 9(a). The total system communica-
tion rate continues to increase with additional total power
resources. This is because increasing the power resources
allows more users to access the network simultaneously,
allocating additional power to each UA V user and ensur-
ing sufﬁcient resources for higher data transmission rates.
Figures 9(b) and 9(c) illustrate the relationship between the
system’s average sum rate and the total allocated power for
location sensing errors followed by Gaussian and uniform
distribution, respectively. The system exhibits notably better
performance under Gaussian-distributed errors than uniform-
distributed errors because Gaussian distributions concentrate
errors around the mean, minimizing the probability of extreme
deviations that could signiﬁcantly compromise resource allo-
cation efﬁciency. Although location sensing errors introduce
uncertainty that may render resource allocation strategies
suboptimal, increasing power allocation remains an effective
method for enhancing system performance by accommodating
more simultaneous network users while providing adequate
resources for each UA V .
The average sum rate comparison at the convergence of
different location sensing errors in the ISAC-enabled low-
altitude networks for different total power resources, as shown
in Fig. 10. Notably, the performance gap between differ-
ent error levels becomes more pronounced at higher power
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

1998 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
allocations, as shown in the magniﬁed inset for the 28-32 dBm
range. The ﬁgure conﬁrms that location sensing errors below a
certain threshold have minimal impact on system performance,
while errors exceeding this threshold progressively reduce the
system’s average sum rate by 2.5%. This degradation occurs
because larger location sensing errors affect channel estimation
accuracy, leading to suboptimal resource allocation decisions
that diminish overall system communication performance,
though the relationship is not strictly linear as moderate errors
show performance closer to smaller errors than to larger
ones.
From Fig. 9 and Fig. 10, we observe that location
sensing errors signiﬁcantly impact communication perfor-
mance in our ISAC-enabled low-altitude network frame-
work. These errors affect the system through three primary
mechanisms:
• Channel estimation accuracy: The estimated channel state
information ˆhk,m in (5) directly depends on location
information accuracy. When localization errors occur, the
resulting channel estimation inaccuracies lead to distorted
channel state information, affecting the SNR and conse-
quently reducing achievable data rates.
• Resource allocation efﬁciency: Location sensing errors
compromise the effectiveness of our J2OT algorithm
by affecting both cell association and power allocation
decisions. As errors increase, the optimal transport map-
ping between UA Vs and base stations diverges from the
truly optimal solution, resulting in suboptimal network
resource utilization.
• Error threshold effect: Our analysis reveals that
while small localization errors (when dk,m(n) −
ˆdk,m(n) is relatively small compared to wavelength
λ) have minimal impact, errors exceeding a cer-
tain threshold cause substantial degradation in sys-
tem communication performance, establishing a clear
relationship between sensing accuracy and communica-
tion quality.
V. C ONCLUSION
This paper investigates the joint optimization of cell asso-
ciation and power allocation for cooperative communication
and non-cooperative localization in ISAC-enabled low-altitude
networks. We formulate the problem to maximize the weighted
sum of the system’s average sum rate and localization
QoS by jointly optimizing cell association, communication
power allocation and power allocation for sensing under the
constraints of all UA Vs’ localization QoS and cooperative
UA Vs’ sum rate. Subsequently, we propose J2OT to solve the
formulated problem. Simulation results demonstrate J2OT’s
superiority, improving system objective by nearly 1.5 bits/s/Hz
and reducing localization CRB by almost 7.5% compared to
baseline methods. The research reveals signiﬁcant trade-offs
between communication performance and sensing accuracy
as non-cooperative UA Vs increase, and importantly ﬁnds that
location sensing errors exceeding certain thresholds substan-
tially degrade communication performance by compromising
resource allocation effectiveness.
REFERENCES
[1] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for
low-altitude economy: Coordinated transmit beamforming and UA V tra-
jectory design,” IEEE Trans. Commun. , vol. 73, no. 8, pp. 5832–5847,
Aug. 2025, doi: 10.1109/TCOMM.2025.3541027.
[2] Y . Luo, W. Ding, and B. Zhang, “Optimization of task scheduling
and dynamic service strategy for multi-UA V-enabled mobile-edge com-
puting system,” IEEE Trans. Cognit. Commun. Netw. , vol. 7, no. 3,
pp. 970–984, Sep. 2021.
[3] W. Lin, L. Li, Y . Liu, Y . He, and Y . Liu, “Timeliness opti-
mization of unmanned aerial vehicle lossy communications for
Internet-of-Things,” Chin. J. Aeronaut. , vol. 35, no. 9, pp. 249–255,
Sep. 2022.
[4] R. Tang, R. Zhang, Y . Xu, and C. Yuen, “Deep reinforcement learning-
based resource allocation for multi-UA V-assisted full-duplex wireless-
powered IoT networks,” IEEE Trans. Cognit. Commun. Netw. , vol. 10,
no. 6, pp. 2236–2251, Dec. 2024.
[5] Z. Feng, D. Wu, M. Huang, and C. Yuen, “Event-driven transformer-
based reinforcement learning for trajectory design and channel
assignment in multi-UA V assisted communication,” IEEE Trans.
Cogn. Commun. Netw. , early access, Mar. 10, 2025, doi: 10.1109/
TCCN.2025.3549603.
[6] L. Li, Y . Sun, Q. Cheng, D. Wang, W. Lin, and W. Chen, “Optimal
trajectory and downlink power control for multi-type UA V aerial base
stations,” Chin. J. Aeronaut. , vol. 34, no. 9, pp. 11–23, Sep. 2021.
[7] Z. Lyu et al., “Empowering intelligent low-altitude economy with large
AI model deployment,” 2025, arXiv:2505.22343.
[8] Z. Du et al., “Integrated sensing and communications for V2I networks:
Dynamic predictive beamforming for extended vehicle targets,” IEEE
Trans. Wireless Commun., vol. 22, no. 6, pp. 3612–3627, Jun. 2023.
[9] J. Wu, L. Li, W. Lin, J. Liang, and Z. Han, “ADMM-based waveform
design for PAPR reduction in integrated sensing and commuication
systems,” IEEE Sensor J., vol. 24, no. 11, pp. 18488–18498, Jun. 2024,
doi: 10.1109/JSEN.2024.3392353.
[10] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE Trans. Wireless
Commun., vol. 23, no. 2, pp. 1260–1275, Feb. 2024.
[11] L. Li et al., “Millimeter-wave networking in the sky: A machine
learning and mean ﬁeld game approach for joint beamforming
and beam-steering,” IEEE Trans. Wireless Commun. , vol. 19, no. 10,
pp. 6393–6408, Oct. 2020.
[12] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[13] B. Guo, J. Liang, B. Tang, L. Li, and H. C. So, “Bistatic MIMO DFRC
system waveform design via symbol distance/direction discrimination,”
IEEE Trans. Signal Process. , vol. 71, pp. 3996–4010, 2023.
[14] X. Meng, F. Liu, C. Masouros, W. Yuan, Q. Zhang, and Z. Feng,
“Vehicular connectivity on complex trajectories: Roadway-geometry
aware ISAC beam-tracking,” IEEE Trans. Wireless Commun. , vol. 22,
no. 11, pp. 7408–7423, Nov. 2023.
[15] Z. Ren et al., “Fundamental CRB-rate tradeoff in multi-antenna ISAC
systems with information multicasting and multi-target sensing,” IEEE
Trans. Wireless Commun., vol. 23, no. 4, pp. 3870–3885, Apr. 2024.
[16] Z. He, W. Xu, H. Shen, D. W. K. Ng, Y . C. Eldar, and
X. You, “Full-duplex communication for ISAC: Joint beamforming
and power optimization,” IEEE J. Sel. Areas Commun. , vol. 41, no. 9,
pp. 2920–2936, Sep. 2023.
[17] J. Wang, W. Cheng, and W. Zhang, “Performance boundary analyses
for statistical multi-QoS framework over 6G SAGINs,” IEEE Trans.
Wireless Commun., vol. 24, no. 5, pp. 4329–4343, May 2025.
[18] J. Wang, W. Cheng, and H. V . Poor, “Statistical delay and error-rate
bounded QoS provisioning for AoI-driven 6G satellite{-} terrestrial inte-
grated networks using FBC,” IEEE Trans. Wireless Commun. , vol. 23,
no. 10, pp. 15540–15554, Oct. 2024.
[19] J. Luo, Z. Fei, X. Wang, L. Zhao, B. Li, and Y . Zhou,
“GNN-based resource allocation for digital twin-enhanced multi-
UA V radar networks,” IEEE Wireless Commun. Lett. , vol. 13, no. 11,
pp. 3137–3141, Nov. 2024.
[20] Z. Fei, X. Wang, N. Wu, J. Huang, and J. A. Zhang, “Air-ground
integrated sensing and communications: Opportunities and challenges,”
IEEE Commun. Mag. , vol. 61, no. 5, pp. 55–61, May 2023.
[21] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-UA V
networks,” IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660–2672, Apr.
2021.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

ZHENG et al.: OPTIMAL TRANSPORT FRAMEWORK FOR ISAC IN LOW-ALTITUDE NETWORKS 1999
[22] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE J. Sel. Areas Commun. , vol. 41, no. 9,
pp. 2920–2936, Sep. 2023.
[23] K. Meng, Q. Wu, S. Ma, W. Chen, and T. Q. S. Quek, “UA V
trajectory and beamforming optimization for integrated periodic sensing
and communication,” IEEE Wireless Commun. Lett. , vol. 11, no. 6,
pp. 1211–1215, Jun. 2022.
[24] J. Zhao, F. Gao, W. Jia, W. Yuan, and W. Jin, “Integrated sensing and
communications for UA V communications with jittering effect,” IEEE
Wireless Commun. Lett., vol. 12, no. 4, pp. 758–762, Apr. 2023.
[25] Y . Ding et al., “Online edge learning ofﬂoading and resource man-
agement for UA V-assisted MEC secure communications,” IEEE J. Sel.
Topics Signal Process., vol. 17, no. 1, pp. 54–65, Jan. 2023.
[26] W. Lu et al., “Secure NOMA-based UA V-MEC network towards a ﬂying
eavesdropper,” IEEE Trans. Commun. , vol. 70, no. 5, pp. 3364–3376,
May 2022.
[27] Y . Cao and Q.-Y . Yu, “Joint resource allocation for user-centric cell-free
integrated sensing and communication systems,” IEEE Commun. Lett. ,
vol. 27, no. 9, pp. 2338–2342, Sep. 2023.
[28] Y . Gong, Y . Wei, Z. Feng, F. R. Yu, and Y . Zhang, “Resource
allocation for integrated sensing and communication in digital twin
enabled Internet of Vehicles,” IEEE Trans. Veh. Technol., vol. 72, no. 4,
pp. 4510–4524, Apr. 2023.
[29] Y . Qin, Z. Zhang, X. Li, W. Huangfu, and H. Zhang, “Deep rein-
forcement learning based resource allocation and trajectory planning
in integrated sensing and communications UA V network,” IEEE Trans.
Wireless Commun., vol. 22, no. 11, pp. 8158–8169, Nov. 2023.
[30] Y . Zheng, L. Li, W. Lin, W. Liang, Q. Du, and Z. Han,
“Resource allocation based on optimal transport theory in ISAC-
enabled multi-UA V networks,” in Proc. IEEE Globecom Workshops
(GC Wkshps) , Cape Town, South Africa, 2024, pp. 1–6, doi: 10.1109/
GCWkshp64532.2024.11100546.
[31] J. Sun, S. Ma, R. Yang, Y . Tingting, and S. Li, “Robust power allocation
for UA V-aided ISAC systems with uncertain location sensing errors,”
2023, arXiv:2305.04423.
[32] L. Wang, H. Zhang, S. Guo, and D. Yuan, “Deployment and association
of multiple UA Vs in UA V-assisted cellular networks with the knowledge
of statistical user position,” IEEE Trans. Wireless Commun. , vol. 21,
no. 8, pp. 6553–6567, Aug. 2022.
[33] B. Li, Q. Li, Y . Zeng, Y . Rong, and R. Zhang, “3D trajec-
tory optimization for energy-efﬁcient UA V communication: A control
design perspective,” IEEE Trans. Wireless Commun. , vol. 21, no. 6,
pp. 4579–4593, Jun. 2022.
[34] F. Dong, F. Liu, Y . Cui, W. Wang, K. Han, and Z. Wang, “Sensing as
a service in 6G perceptive networks: A uniﬁed framework for ISAC
resource allocation,” IEEE Trans. Wireless Commun. , vol. 22, no. 5,
pp. 3522–3536, May 2023.
[35] J. Feng, F. R. Yu, Q. Pei, J. Du, and L. Zhu, “Joint optimization of radio
and computational resources allocation in blockchain-enabled mobile
edge computing systems,” IEEE Trans. Wireless Commun. , vol. 19,
no. 6, pp. 4321–4334, Jun. 2020.
[36] M. Mozaffari, W. Saad, M. Bennis, Y .-H. Nam, and M. Debbah,
“A tutorial on UA Vs for wireless networks: Applications, challenges,
and open problems,” IEEE Commun. Surveys Tuts. , vol. 21, no. 3,
pp. 2334–2360, 3rd Quart., 2019.
[37] L. V . Kantorovich, “On the translocation of masses,” J. Math. Sci. ,
vol. 133, no. 4, pp. 1381–1382, Oct. 2006.
[38] G. Peyr ´e and M. Cuturi, “Computational optimal transport,” Cen-
ter Res. Econ. Statist. Work. Papers , vol. 11, no. 5, pp. 355–607,
Dec. 2019.
[39] L. Ambrosio, A. Bressan, D. Helbing, A. Klar, and E. Zuazua, Modelling
and Optimisation of Flows on Networks (Lecture Notes in Mathematics).
Berlin, Germany: Springer, 2012.
[40] M. Mozaffari, W. Saad, M. Bennis, and M. Debbah, “Wireless com-
munication using unmanned aerial vehicles (UA Vs): Optimal transport
theory for hover time optimization,” IEEE Trans. Wireless Commun. ,
vol. 16, no. 12, pp. 8052–8066, Dec. 2017.
[41] G. Crippa, C. Jimenez, and A. Pratelli, “Optimum and equilibrium in a
transport problem with queue penalization effect,” Adv. Calculus Variat.,
vol. 2, no. 3, pp. 207–246, Jan. 2009.
[42] D. P. Bertsekas, Nonlinear Programming, 3rd ed., Belmont, MA, USA:
Athena Scientiﬁc, 2016.
[43] X. Jing, F. Liu, C. Masouros, and Y . Zeng, “ISAC from the sky: UA V
trajectory design for joint communication and target localization,” IEEE
Trans. Wireless Commun., vol. 23, no. 10, pp. 12857–12872, Oct. 2024,
doi: 10.1109/TWC.2024.3396571.
[44] J. Zhang, J. Xu, W. Lu, N. Zhao, X. Wang, and D. Niyato, “Secure
transmission for IRS-aided UA V-ISAC networks,”IEEE Trans. Wireless
Commun., vol. 23, no. 9, pp. 12256–12269, Sep. 2024, doi: 10.1109/
TWC.2024.3390169.
[45] Y . Cui et al., “Speciﬁc beamforming for multi-UA V networks: A dual
identity-based ISAC approach,” in Proc. IEEE Int. Conf. Commun. ,
Rome, Italy, May 2023, pp. 4979–4985.
[46] M. Mozaffari, A. T. Z. Kasgari, W. Saad, M. Bennis, and M. Debbah,
“Beyond 5G with UA Vs: Foundations of a 3D wireless cellular network,”
IEEE Trans. Wireless Commun., vol. 18, no. 1, pp. 357–372, Jan. 2019.
[47] P. He, A. Anpalagan, and W. Ejaz, “Energy-efﬁcient power allocation
maximization for MU-MIMO multiple access channels,” IEEE Trans.
Wireless Commun., vol. 22, no. 5, pp. 3460–3471, May 2023.
Yufeng Zheng (Student Member, IEEE) is cur-
rently pursuing the Ph.D. degree with the School of
Electronics and Information, Northwestern Polytech-
nical University, Xi’an, China, under the supervision
of Prof. Lixin Li. His research interests include
integrated sensing and communication (ISAC), low-
altitude communications, optimal transport theory,
and reinforcement learning.
Lixin Li (Member, IEEE) received the B.S. (Hons.),
M.S. (Hons.), and Ph.D. degrees from Northwestern
Polytechnical University (NPU), China, in 2001,
2004, and 2008, respectively. From 2009 to 2011,
he was a Post-Doctoral Research Fellow with NPU.
In 2011, he joined the School of Electronics and
Information, NPU, where he is currently a Full
Professor and the Chair of the Department of Com-
munication Engineering. In 2017, he held a visiting
scholar position with the University of Houston,
USA. He holds 26 granted patents and has authored
or co-authored ﬁve books and more than 200 peer-reviewed papers in many
prestigious journals and conferences. His research interests include 5G/6G
wireless networks, federated learning, game theory, and machine learning for
wireless communications. He was a recipient of the 2016 NPU Outstanding
Young Teacher Award, which is the highest research and education honors
for young faculties in NPU. He was an exemplary reviewer of IEEE
TRANSACTIONS ON COMMUNICATIONS in 2020.
Wensheng Lin (Member, IEEE) received the
B.Eng. degree in communication engineering and
the M.Eng. degree in electronic and communication
engineering from Northwestern Polytechnical Uni-
versity, Xi’an, China, in 2013 and 2016, respectively,
and the Ph.D. degree in information science from
Japan Advanced Institute of Science and Technology
(JAIST), Ishikawa, Japan, in 2019. His doctoral
study was fully funded by Chinese Government
Scholarship awarded from China Scholarship Coun-
cil (CSC). He is currently an Associate Professor
with the School of Electronics and Information, Northwestern Polytechnical
University. His research interests include network information theory, dis-
tributed source coding, and semantic communications. He was a recipient of
the prestigious 2019 Niwa Yasujiro Outstanding Paper Award and the 2019
IEEE Nagoya Section Conference Presentation Award. He was selected into
the 8th Young Elite Scientists Sponsorship Program by China Association for
Science and Technology (CAST).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply. 

2000 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Wei Liang (Senior Member, IEEE) received the
Ph.D. degree in wireless communication from the
University of Southampton, Southampton, U.K., in
2015. She was a Post-Doctoral Research Fellow
with Lancaster University from 2015 to 2018. She
is currently an Associate Professor with the School
of Electronics and Information, Northwestern Poly-
technical University. Her research interests include
adaptive coded modulation, network coding, match-
ing theory, game theory, non-orthogonal multiple
access, and machine learning.
Qinghe Du (Member, IEEE) received the B.S.
and M.S. degrees in electrical engineering from
Xi’an Jiaotong University, China, in 2001 and 2004,
respectively, and the Ph.D. degree in computer
engineering from Texas A&M University, College
Station, TX, USA, in 2010. He is currently a
Professor with the School of Information and Com-
munications Engineering, Xi’an Jiaotong University.
He has published over 100 technical papers in
refereed technical journals and international aca-
demic conferences. His research interests widely
cover related areas of mobile wireless communications and networking. He
received the Best Paper Award from the international academic conferences,
including IEEE GLOBECOM 2007, IEEE COMCOMAP 2019, IEEE/CIC
ICCC 2021, and IWCMC 2024. He received the Best Paper Award from
China Communications in 2017 and 2020. He served and/or serves as an
Associate Editor for IEEE T RANSACTIONS ON COMMUNICATIONS and
IEEE C OMMUNICATIONS LETTERS , an Area Editor for KSII Transactions
on Internet and Information Systems , and an Editor for Electronics.
Zhu Han (Fellow, IEEE) received the B.S. degree
in electronic engineering from Tsinghua University
in 1997 and the M.S. and Ph.D. degrees in electri-
cal and computer engineering from the University
of Maryland, College Park, in 1999 and 2003,
respectively.
From 2000 to 2002, he was a Research and
Development Engineer with JDSU, Germantown,
Maryland. From 2003 to 2006, he was a Research
Associate with the University of Maryland. From
2006 to 2008, he was an Assistant Professor with
Boise State University, ID. He is currently a John and Rebecca Moores
Professor with the Electrical and Computer Engineering Department and
the Computer Science Department, University of Houston, TX. His main
research targets on the novel game-theory related concepts critical to enabling
efﬁcient and distributive use of wireless networks with limited resources. His
other research interests include wireless resource allocation and management,
wireless communications and networking, quantum computing, data science,
smart grids, carbon neutralization, and security and privacy. He received
the NSF Career Award in 2010, the Fred W. Ellersick Prize of the IEEE
Communication Society in 2011, the EURASIP Best Paper Award for the
EURASIP Journal on Advances in Signal Processing in 2015, the IEEE
Leonard G. Abraham Prize in the ﬁeld of communications systems (Best Paper
Award in IEEE J OURNAL ON SELECTED AREAS IN COMMUNICATIONS
(IEEE JSAC)) in 2016, the IEEE Vehicular Technology Society 2022 Best
Land Transportation Paper Award, and several best paper awards in IEEE
conferences. He was an IEEE Communications Society Distinguished Lecturer
from 2015 to 2018, an ACM Distinguished Speaker from 2022 to 2025,
an AAAS Fellow since 2019, and an ACM Fellow since 2024. He is a
1% highly cited researcher since 2017 according to Web of Science. He is
also the winner of the 2021 IEEE Kiyo Tomiyasu Award (an IEEE Field
Award), for outstanding early to mid-career contributions to technologies
holding the promise of innovative applications, with the following citation:
“for contributions to game theory and distributed management of autonomous
communication networks.”
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:33:29 UTC from IEEE Xplore.  Restrictions apply.