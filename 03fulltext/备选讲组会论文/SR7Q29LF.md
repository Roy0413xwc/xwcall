---
type: literature-fulltext
title: "Precise HDV Positioning Through Safety-Aware ISAC in a Value-of-Information-Driven 6G V2X System"
zotero_key: "SR7Q29LF"
pdf_key: "4WE53LT7"
doi: "10.1109/TWC.2026.3678464"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Precise HDV Positioning Through Safety-Aware ISAC in a Value-of-Information-Driven 6G V2X System.md"
fulltext_path: "03fulltext/备选讲组会论文/SR7Q29LF.md"
zotero_item: "zotero://select/library/items/SR7Q29LF"
zotero_pdf: "zotero://open-pdf/library/items/4WE53LT7"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Precise HDV Positioning Through Safety-Aware ISAC in a Value-of-Information-Driven 6G V2X System

> PDF 原文逐页文本抽取；来源文件 SHA-256：`7d8e5e658891fded0964db626c776503470f1ab6d096e6d69ce606964a7207fa`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 14875
Precise HDV Positioning Through Safety-Aware
ISAC in a Value-of-Information-Driven
6G V2X System
Mohammad Reza Abedi
 , Member, IEEE, Zahra Rashidi, Nader Mokari
 , Senior Member, IEEE,
Hamid Saeedi
 , Member, IEEE, and Nizar Zorba
 , Senior Member, IEEE
Abstract—Recent advancements in Integrated Sensing and
Communications (ISAC) have unlocked new potential for
addressing the dual demands of high-resolution positioning
and reliable communication in 6G Vehicle-to-Everything (V2X)
networks. These capabilities are vital for transmitting safety-
critical data from Connected Autonomous Vehicles (CA Vs) to
improve metrics such as Time to Collision (TTC) and reduce the
Collision Risk (CR) ratio. However, limited radio resources and
interference remain major obstacles to achieving both precision
and capacity simultaneously. The challenge intensiﬁes in mixed-
trafﬁc scenarios involving Human-Driven Vehicles (HDVs), which
lack connectivity and cannot share their status or positioning.
Additionally, CA V sensors are limited in range and accuracy,
making detection of HDVs unreliable. ISAC plays a pivotal role
here by enabling the sensing of HDV positions via shared com-
munication infrastructure, improving environmental awareness.
To address these challenges, this paper proposes a novel Value
of Information (VoI) metric that prioritizes the transmission
of safety-critical data. The joint sensing-communication-control
problem is modeled as a two-time-scale sequential decision
process and solved using a Multi-Agent Distributed Deterministic
Policy Gradient (MADDPG) algorithm. By focusing on high-
VoI data, the framework reduces complexity and optimizes
network and trafﬁc resource usage. Simulations show that the
proposed approach signiﬁcantly reduces the CR ratio by at
least 33% and improves the TTC by up to 66%, demon-
strating its effectiveness in enhancing safety and efﬁciency in
mixed-autonomy environments.
Index Terms —Connected automated vehicles, collision avoid-
ance, integrated sensing and communication, vehicle positioning.
I. I NTRODUCTION
A. Motivations and State of the Art
T
HE rapid growth of vehicle automation highlights the
importance of longitudinal control systems like Adaptive
Received 6 September 2025; revised 2 February 2026; accepted 20 March
2026. Date of current version 8 April 2026. This work was supported by
Qatar Research, Development and Innovation (QRDI) Council under Grant
ARG01-0511-230129. The associate editor coordinating the review of this
article and approving it for publication was S. Zhou. (Corresponding author:
Nader Mokari.)
Mohammad Reza Abedi, Zahra Rashidi, and Nader Mokari are
with the Department of Electrical Engineering, Tarbiat Modares Univer-
sity, Tehran 14115-111, Iran (e-mail: Mohammadreza abedi@modares.ac.ir;
zrashi@modares.ac.ir; nader.mokari@modares.ac.ir).
Hamid Saeedi is with the College of Engineering and Technology,
University of Doha for Science and Technology, Doha, Qatar (e-mail:
hamid.saeedi@udst.edu.qa).
Nizar Zorba is with the College of Engineering, Qatar University, Doha,
Qatar (e-mail: nizarz@qu.edu.qa).
Digital Object Identiﬁer 10.1109/TWC.2026.3678464
Cruise Control (ACC). ACC not only improves safety, comfort,
and string stability for individual vehicles but also beneﬁts
large-scale trafﬁc by enhancing ﬂow, reducing congestion,
and minimizing emissions. These impacts demonstrate the
key role of Automated Vehicles (A Vs) in advancing both
driving experiences and overall trafﬁc efﬁciency. Cooperative
Adaptive Cruise Control (CACC) surpasses ACC by uti-
lizing Vehicle-to-Infrastructure (V2I) and Vehicle-to-Vehicle
(V2V) communication to exchange key data (e.g., position,
speed, acceleration), enabling coordinated and efﬁcient driv-
ing. Within the Vehicle-to-Everything (V2X) framework, A Vs
fuse external information with onboard sensor data, thereby
enhancing vehicle guidance and signiﬁcantly improving trafﬁc
safety. Accurate positioning is crucial for A V safety, especially
where GPS is unreliable (e.g., tunnels, parking). Mixed trafﬁc
with human-driven vehicles adds complexity, requiring behav-
ioral understanding. To overcome these issues, emerging 6G
networks integrate sensing and communication for enhanced
positioning and safety.
Integrated Sensing and Communications (ISAC) is a trans-
formative paradigm for vehicular networks that enables object
detection without extra spectrum cost, aligning with 6G’s
IMT-2030 vision [1], [2], [3], [4], [5], [6], [7], [8], [9]. ISAC
improves positioning when GPS is weak or unavailable, sup-
ports localization of GPS-lacking vehicles, and enables V2X
information sharing—enhancing situational awareness, coor-
dination, and road safety. Recent advances such as mmWave
(wide spectrum, high data rates, ﬁne sensing resolution)
and massive Multiple-Input Multiple-Output (mMIMO) (direc-
tional beamforming, spatial multiplexing) mitigate mmWave
path loss while boosting positioning accuracy. Their synergy
makes simultaneous data transmission and sensing feasi-
ble, positioning ISAC as a key enabler of future intelligent
transportation systems.
Although advanced technologies improve vehicular posi-
tioning and communication, practical deployment is limited
by bandwidth constraints and the infeasibility of transmit-
ting all vehicles’ data in dense trafﬁc. To address this, we
introduce the Value of Information (V oI) metric, which priori-
tizes data based on its contribution to safety and situational
awareness, unlike the Age of Information (AoI) that only
considers freshness. This paper investigates which vehicles’
positioning data should be prioritized for radar estimation
and transmission under resource constraints: Which vehicles’
positioning information should be prioritized for radar-based
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

14876 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
estimation and transmission to maximize safety and situational
awareness under constrained radio resources? We propose
a uniﬁed V oI-driven framework that enables selective radar
sensing and V2I transmission of high-value information, while
constructing a compact state space for Deep Reinforcement
Learning (DRL)-based control, ensuring efﬁcient resource
allocation and real-time decision-making. Therefore, we pose
a secondary question: How should transport and radio network
parameters be selected to construct a compact yet informative
state space for DRL-based autonomous vehicle control?
B. Related Works
V2I networks play a crucial role in 6G cellular systems, par-
ticularly with the growing ISAC. Roadside Base Stations (BSs)
are expected to provide both data transmission and vehicle
tracking capabilities. Existing research primarily focuses on
two sensing paradigms—active and passive sensing—within
V2I systems [10]. Considerable efforts have been dedicated
to the development of integrated active sensing and commu-
nication mechanisms, where full-duplex BSs simultaneously
transmit downlink (DL) data and monitor vehicle motion via
echo signals [10], [11], [12]. For instance, [10] proposed a
power allocation scheme to minimize the Cram ´er-Rao Lower
Bound (CRLB) under a sum-rate constraint in multi-vehicle
scenarios. Expanding on this, [12] tackled multi-user interfer-
ence challenges by introducing a Weighted sum Mean Square
Error minimization (WMMSE)-based iterative algorithm for
optimized DL beamforming.
While ISAC-based V2I scenarios have received signiﬁcant
attention, several critical challenges hinder their practical
implementation. A major limitation in prior works is the
predominant focus on single-Roadside Units (RSU) V2I sce-
narios [4], [10], [13]. Given that vehicles are continuously
mobile, ensuring seamless sensing and communication ser-
vices requires a multi-RSU deployment strategy. However,
most existing solutions fail to effectively address the coor-
dination among multiple RSUs, leading to service disruptions.
Some studies have explored multi-RSU V2I scenarios
under conventional radar-sensing architectures. However,
they typically emphasize sensing accuracy while neglect-
ing communication performance [14], [15]. For instance,
[14] proposed a multi-sensor, multi-vehicle positioning and
tracking framework for autonomous driving, showing that
cooperation among RSUs enhances positioning accuracy.
Similarly, [15] developed a multi-RSU collaborative radar
sensing network leveraging signal-level fusion technology
to assist vehicles in perceiving their surroundings. Despite
these advancements, these methods overlook the challenges
of radio resource allocation and efﬁcient beamforming for
real-time communication and tracking in dynamic trafﬁc
environments.
Recent works have proposed innovative ISAC-based frame-
works to overcome some of these challenges. For instance,
[16] introduced a Nonlinear Self-Interference Cancellation
(NSIC) scheme for ISAC-assisted V2X networks, consider-
ing beam tracking. While effective in reconstructing self-
interference using CSI-based path projection, this approach
fails to account for practical issues such as CSI estimation
errors, processing delays, and external interference. Another
study [17] proposed a multi-vehicle tracking and ID asso-
ciation scheme using ISAC signals, where RSUs transmit
multi-beam signals to estimate vehicle positions and velocities
while employing Kullback-Leibler Divergence (KLD) for ID
association. However, this approach assumes an idealized
environment and does not fully address real-world factors such
as environmental noise, sudden vehicle maneuvers, and signal
distortions.
Further, [18] developed a multi-beam object positioning
framework to enhance sensing performance in mmWave
MIMO ISAC systems for connected autonomous vehicles,
optimizing the sensing beampattern gain under SINR, power,
and hardware constraints. However, the scheme primarily
focuses on improving sensing rather than addressing com-
munication and radio resource management. Similarly, [19]
proposed an ISAC-assisted collision avoidance mechanism
that utilizes mmWave MIMO and beamforming for simulta-
neous communication and environmental sensing. However,
its power allocation scheme does not consider the V oI in
prioritizing safety-critical data transmission. Additionally, [20]
introduced ISAC-assisted frame structures for NR-V2X com-
munications, reducing pilot overhead while improving beam
management, yet the work lacks an adaptive mechanism for
dynamically allocating radio resources in real-time scenarios.
Lastly, [21] proposed an ISAC-based beam tracking scheme
for multi-RSU V2I systems, integrating an unscented Kalman
ﬁlter and CoMP-based resource allocation to minimize inter-
region interference. However, its approach does not explicitly
address the optimization of radio resources based on the
importance of transmitted information. The authors in [22]
and [23] study ISAC systems with centralized, model-based
optimization. In [22], a NOMA-aided ISAC system jointly
optimizes beamformers and sensing scheduling to maximize
sensing efﬁciency under per-user data and sensing-quality
constraints. The problem is mixed non-convex and is solved
via layered decomposition: SCA with penalty for beam-
forming, bisection for duration, and cross-entropy learning
for scheduling. By contrast, [23] investigates a STAR-RIS-
assisted downlink ISAC system with energy-splitting protocol,
jointly optimizing active BS beams and passive RIS phases
to maximize sensing SNR while satisfying per-user SINR and
power/energy constraints. It uses alternating optimization with
SDR for BS beams, achieving rank-one BS beam solutions
and showing that dedicated sensing waveforms do not improve
SNR in single-target scenarios. By contrast, in our work we
consider a practical, large-scale, safety-critical V2X scenario
with mixed autonomy (human-driven vehicles and CA Vs)
served by Cell-Free RSUs. Instead of maximizing sensing
efﬁciency or SNR, we optimize safety metrics (TTC/CR)
through Cram ´er–Rao Bound (CRB)-aware beamforming, and
select high-value exogenous states using KL-divergence (V oI)
to reduce V2X signaling and computational complexity. Fur-
thermore, a two-time-scale MA-DDPG framework jointly
adapts long-term vehicle control and short-term beamforming
in an online, distributed manner, enforcing per-vehicle rate
constraints and dynamically handling time-varying CSI.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14877
C. Contributions
A key challenge in mixed trafﬁc control arises from HDVs,
which are typically unconnected and thus cannot report their
real-time positions or velocities to RSUs or CA Vs. To over-
come this, our framework leverages ISAC, enabling RSUs to
estimate HDV positions, velocities, and trajectories through
radar sensing embedded in the communication infrastructure.
These estimated states are then shared with CA Vs in real time,
providing critical exogenous information that would otherwise
be unavailable. Furthermore, the proposed MADDPG-based
policy accounts for sensing uncertainties via the V oI prior-
itization, which reduces the inﬂuence of low-conﬁdence or
delayed measurements on decision-making. The innovations
of the paper, presented in a technical and precise manner, are
as follows:
• ISAC-Assisted Position Estimation for Human-Driven
Vehicles: Unlike conventional vehicle positioning stud-
ies that assume given or cooperative measurements and
focus on temporal state ﬁltering, our work investigates
ISAC-enabled, CRB-aware sensing and beamforming
for non-cooperative human-driven vehicles. By jointly
designing communication and sensing at the physical
layer, the proposed framework actively shapes the infor-
mation content and reliability of position measurements
under practical radio, power, and QoS constraints, thereby
providing an information-optimal measurement founda-
tion upon which tracking can subsequently operate.
• Integration of VoI in ITS Systems : Unlike conventional
methods that treat all transmitted data equally, our work
introduces the concept of V oI in ITSs. By distinguishing
and prioritizing high-value information that enhances
safety, our approach ensures efﬁcient allocation of com-
munication resources, leading to improved reliability and
system performance.
• Radio Resource Management for ISAC-Based V2I Net-
works: Addressing the challenge of limited radio
resources, we propose a novel beamforming and resource
allocation mechanism that prioritizes the transmission
of critical safety information. Unlike existing schemes,
which allocate resources based on sensing accuracy
alone, our method dynamically optimizes beamforming
parameters while ensuring that the most valuable data is
transmitted efﬁciently.
The structure of this paper is as follows: Section II details
the system model, while Section III introduces a framework
for quantifying the value of exogenous information. Section IV
formulates the problem, and Section V presents the MA-
DDPG-based solution methodology. Section VI discusses the
computational complexity, followed by performance evalua-
tion results in Section VII. Finally, Section VIII summarizes
the key ﬁndings.
II. S YSTEM MODEL
In an urban environment, a square region is equipped
with a Cell-Free massive MIMO (CFmMIMO) system, which
consists of R RSUs strategically positioned along both sides
of the road. Each RSU is outﬁtted with a massive Uniform
Linear Array (ULA) consisting of Mt transmit antennas and
Mr receive antennas, where Mt = Mr = M = P× Q,
and MtR ≫ V , where the symbol ≫ denotes that one
quantity is much greater than another. The set of V CA Vs
is denoted by V = {v1,v 2,...,v V}, where |V| = V , and
each vehicle is indexed by v, where the notation|.| represents
the cardinality (size) of set. RSUs are connected to a Central
Processing Unit (CPU) and support a Dual-function Radar
Communication (DFRC) system operating in the millimeter-
Wave (mmWave) band. This system simultaneously performs
sensing and communication tasks, serving V CA Vs, each
equipped with a single antenna. The set of RSUs is denoted
byR ={r1,r 2,...,r R}, with cardinality |R| =R, and each
RSU is indexed by r. A selected subset of these RSUs is used
to serve each CA V via coherent joint transmissions within the
user-centric cluster. The subset of RSUs used to serve vehicle
v is denoted by Rv, where |Rv| = Rv. RSUs are chosen
based on their large-scale fading coefﬁcients, which are the
highest for vehicle v. The set of CA Vs served by RSU r is
deﬁned as Vr, where |Vr| = Vr≤ Mt. The road consists of
L lanes, each with a width of Dl and a center position given
by yl = Dl/2 + (l− 1)Dl. The set of lanes is represented
by L = {l1,l 2,...,l L}, indexed by l, with |L| = L. To
address the different time scales of transportation and radio
network control parameters, a two-time scale control scheme is
adopted to reduce signal processing complexity and overhead.
The time axis is divided into several large-term time slots,
each of duration ∆, indexed by τ. Each large-term time slot
is further divided into T short-term time slots, each with a
duration of δ, indexed by tτ . Based on the studies in [13]
and [24], it is reasonable to assume that the state parameters
of vehicles remain constant over a short time duration. Each
CA Vv has a position qlv,tτ =(xlv,tτ,ylv,tτ), where xlv,tτ and
ylv,tτ represent the longitudinal and lateral positions during
short time slot tτ , respectively. The velocity and acceleration
of CA Vv on lane l at short-term time tτ are denoted by ϑlv,tτ
and zlv,tτ , respectively. The dynamic model of CA Vs, based
on their trajectories, is described as follows:
˙xlv,tτ =ϑlv,tτ cosθlv,tτ, ˙ylv,tτ =ϑlv,tτ sinθlv,tτ, (1)
˙ϑlv,tτ = zlv,tτ, ˙θlv,tτ = tanαlv,τϑlv,tτ/Dv, (2)
˙zlv,tτ = zlv,tτ/ξv +ulv,τ/ξv, (3)
where θlv,tτ ∈ [−π,π ] denotes the heading angle of CA V
v in lane l at short-term time tτ . The variables αlv,τ and
ulv,τ represent the control inputs, including the steering angle
and acceleration (e.g., thrust or braking), respectively, which
are designed at the large-term time scale τ. The parameters
ξv and Dv represent the response time to a given set of
control inputs and the physical length of CA V v, respectively.
It is important to note that the same equations can also be
applied to the preceding vehicle (predecessor) (v− 1) by
substituting the subscriptv with (v−1). To ensure safety—i.e.,
avoiding collisions with surrounding vehicles within a speciﬁc
lane—and to satisfy the physical limitations of the vehicles,
the following boundary constraints are imposed on the control
variables of each CA Vv in lane l over both long-term τ and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

14878 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
short-term tτ time horizons:
∆qlv,tτ≥dlv,tτ,ϑl,min≤ϑlv,tτ cosθlv,tτ≤ϑl,max, (4)
−zmax≤ zlv,tτ cosθlv,tτ≤ zmax,−umax≤ulv,τ≤umax,
(5)
−αmax≤αlv,τ≤αmax, (6)
where ∆qlv,tτ =√(xlv,tτ−xl(v−1),tτ )2 + (ylv,tτ−yl(v−1),tτ )2−
Dv denotes the distance between CA V v and the
preceding CA V (v− 1) at lane l at short-term time tτ ,
dlv,tτ = d0 +Tv(ϑlv,tτ−ϑl(v−1),tτ ) is the desired (safe) gap(i.e., the minimum distance to avoid a collision) between
CA Vv and the preceding CA V (v− 1) at lane l at short-term
time tτ , d0 is a constant standstill distance for each CA V ,Tv
is the time gap for CA V v, ϑl,min (ϑl,max) is the minimum
(maximum) velocity at lane l, and umax and αmax are the
maximum values of the control inputs, including acceleration
and steering angle, respectively. The constraints (4)-(6)
describe the lower limit of the gap between adjacent CA Vs,
the range of distance, velocity, acceleration, and heading
angle of the CA Vs, respectively. The control errors of CA Vv,
including spacing and velocity errors in lane l at short-term
time tτ , are deﬁned as follows:
elv,tτ = ∆qlv,tτ−dlv,tτ, ˜elv,tτ =ϑlv,tτ−ϑl(v−1),tτ. (7)
Minimizing spacing and velocity errors is crucial to ensur-
ing proper safety for all CA Vs. However, it is important to
note that only neighboring CA Vs on the same lane signif-
icantly impact safety and should be considered. Therefore,
we deﬁne a set of neighboring CA Vs for each CA V v on
lane l asVlv,tτ = vlv′ : ∆qlvv′,tτ≤ ∆qth, where ∆qlvv′,tτ =√
(xlv,tτ−xlv′,tτ )2 + (ylv,tτ−ylv′,tτ )2−Dv represents the dis-
tance between CA Vv and CA Vv′ at lane l at short-term time
tτ , and ∆qth is the distance threshold. We only consider the
CA Vs within this neighboring set.
A. Safety Metric
Our CR model is based on the concept of TTC, which is a
widely used metric in time-based safety measures. The TTC
metric is employed to assess on-road safety, where each CA V
continuously monitors its TTC with respect to neighboring
vehicles [25] and [26]. TTC is deﬁned as the time required for
two CA Vs to reach a near-zero distance, which would result in
a collision. Therefore, the TTC for CA V v and the preceding
CA V(v− 1) at lane l at short-term time tτ is computed as
Ξlv,tτ = ∆qlv,tτ/|ϑlv,tτ−ϑl(v−1),tτ|, where ϑlv,tτ−ϑl(v−1),tτ isthe relative velocity between CA V v and the preceding CA V
(v− 1) at lane l at short-term time tτ . Overall, on-road safety
can be measured by counting the number of instances between
each pair of CA Vs in which Ξlv,tτ falls below the threshold
value of Ξth:
CR =
{
1, if Ξlv,tτ < Ξth,
0, otherwise. (8)
A collision occurs when Ξlv,tτ for each pair of CA Vs
exceeds the threshold value of Ξth =δReact+δBreak, whereδReact
Fig. 1. System model.
andδBreak represent the time required to respond to the decision
and to apply the brakes, respectively. In this paper, δReact is
assumed to be equal to 1s. For a CA V with speed ϑlv,tτ and
acceleration zlv,tτ , δBreak is calculated as δBreak = ϑlv,tτ/zlv,tτ
[27], [28]. In order to determine the frequency at which the
TTC exceeds the predetermined TTC threshold, we use the
CR ratio, which serves as a measure of the proportion of
instances that pose a collision risk (CR) to the total number
of instances, both risky and non-risky, for each pair of CA Vs.
When considering the optimization problem objective for each
CA V , the primary goal is to maximizeΞlv,tτ in order to reduce
the CR ratio.
B. Signal Model
Assuming the use of Orthogonal Frequency-Division Multi-
ple Access (OFDMA),1 the total bandwidth Ω in the mmWave
band is divided into K subcarriers, indexed by k, with
K = {k1,k 2,...,k K}, each of bandwidth wk. We further
assume ideal, error-free backhaul links (i.e., low latency and
high reliability) are employed to connect all RSUs to a CPU,
facilitating coherent processing across the system [30]. When
considering the scenario with only one RSU, the primary
challenge is intra-region interference, which arises due to
energy leakage from the side beams [28]. Fortunately, intra-
region interference can be mitigated by assigning orthogonal
bandwidths to different vehicles. However, in a multi-RSU
scenario, both intra-region and inter-region interference must
be addressed. For example, consider CA V v being served by
RSU r, while CA Vv′ (v′⁄= v) is served by the neighboring
RSU r′ (r′⁄=r), as shown in Fig. 1.
At time slot tτ , if both vehicles move to nearby locations
at the edges of different RSU service regions, beam collision
may occur. Furthermore, if the allocated downlink bandwidths
for CA Vsv andv′ overlap, inter-region interference will result.
1) Sensing Signal Model: The transmitted signal vec-
tor by RSU r to its serving CA Vs ∀v ∈ Vr at short
time slot tτ on subcarrier k is denoted by ζkr,tτ =
[ζkr1,tτ,ζkr2,tτ,...,ζ krv,tτ,...,ζ krVr,tτ ]T ∈ CVr×1, where ζkrv,tτ
1OFDMA enhances ISAC by reducing inter-user interference through sub-
carrier separation and improving sensing accuracy via efﬁcient pilot designs
[29].
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14879
TABLE I
NOTATION AND DEFINITION
represents the transmitted ISAC DL signal to vehicle v at time
slottτ on subcarrierk, whose power is assumed to be normal-
ized, where [.]T denotes the transpose of a vector or matrix. Let
Fkr,tτ = [fkr1,tτ, fkr2,tτ,..., fkrv,tτ,..., fkrVr,tτ ]∈ CMt×Vr denote
the transmit beamforming matrix at RSU r at time slot tτ
on subcarrier k, where fkrv,tτ is the beamforming vector for
vehiclev at time slot tτ on subcarrier k and CMt×Vr denotes
the set of all complex-valued matrices with Mt rows and Vr
columns. Subsequently, the transmitted signal at RSUr can be
written as ˜ζkr,tτ = Fkr,tτζkr,tτ =∑v∈Vr fkrv,tτζkrv,tτ∈ CMt×1.In mmWave systems, the communication channel is typ-
ically represented by a Line-of-Sight (LoS) channel model
[31]. Due to the inherent sparsity of the mmWave channel,
the Non-LoS (NLoS) component is signiﬁcantly dimin-
ished, which facilitates more accurate channel modeling
and subsequently enhances both sensing and communication
capabilities. Through beam alignment, the transmitted signal
associated with vehicle v is reﬂected by the vehicle itself.
Subsequently, RSU r will receive Vr reﬂected echoes at a
given time slot tτ on subcarrier k, which can be formulated
as ˆζkr,tτ = α∑v∈Vrϱkrv,tτ bk(θrv,tτ )(ak(θrv,tτ ))H ˜ζkr,tτ (tτ−
τrv,tτ )ej2πτrv,tτνkrv,tτ + nkr, where α = √MtMr is the
antenna array gain factor, nr∈ CMr×1 denotes the complex
Additive White Gaussian Noise (AWGN) vector, ϱkrv,tτ =
ξkrv,tτ (2drv,tτ )−1 is the reﬂection coefﬁcient with a Radar
Cross-Section (RCS) coefﬁcient ξkrv,tτ and distance drv,tτ
[18], [19], [32], τrv,tτ and νkrv,tτ denote the round-trip delay
and the round-trip Doppler spread for vehicle v at time slottτ ,
respectively. Notably, RSUs positioned at different locations
will capture distinct measurement parameters when observing
the same CA V . Here, for RSUr, the azimuth angle, elevation
angle, and distance related to CA V v at short time slot tτ
are denoted as θrv,tτ , φrv,tτ , and drv,tτ , respectively, in the
Cartesian coordinate system.
The terms b(θrv,tτ ) ∈ CMr×1 and a(θrv,tτ ) ∈ CMt×1
denote the receive and transmit steering vectors of RSU r,
respectively, which are given by:
b(θrv,tτ ) =
√
1
Mr
[1,...,e −jπ(Mr−1) cosθrv,tτ ]T, (9)
a(θrv,tτ ) =
√
1
Mt
[1,...,e −jπ(Mt−1) cosθrv,tτ ]T, (10)
respectively, where the assumption of half-wavelength antenna
spacing is adopted.
2) Radar Measurement Model: In the considered V2I sce-
nario enabled by a massive MIMO array, it is important to
note that inter-beam interference between different vehicles
in the uplink echoes can be effectively neglected when suf-
ﬁciently narrow beams are employed. This allows the RSU
to distinguish each vehicle based on the received echoes,
as the steering vectors become asymptotically orthogonal
[33]. By utilizing spatial ﬁltering techniques [34], the echo
corresponding to vehicle v at time slot tτ can be isolated from
the reﬂected signal echoes, which is mathematically expressed
as ˆζkrv,tτ = b(ˆθrv,tτ )ˆζkr,tτ = αϱrv,tτ aH(θrv,tτ )˜ζkr,tτ (tτ −
τrv,tτ )ej2πτrv,tτνrv,tτ + ˆnkrv,tτ , where b(ˆθrv,tτ ) denotes the
receive beamforming vector used for spatial ﬁltering, with
ˆθrv,tτ being an estimate of θrv,tτ obtained through existing
Angle-of-Arrival (AoA) estimation techniques [35] and aH
denotes the Hermitian (conjugate transpose) of the complex
vector a. It is important to note that the vehicle is mod-
eled as a perfectly backscattering point target [40], thereby
neglecting inter-vehicle reﬂections. Additionally, by allocat-
ing orthogonal bandwidths to vehicles within an RSU, the
reﬂected echoes received by vehicles served by other RSUs
can be guaranteed to remain orthogonal. This ensures the
equivalence to mono-static sensing. For simplicity, we assume
that ˆθrv,tτ = θrv,tτ , implying that bH(ˆθrv,tτ )b(θrv,tτ ) =
1 [36]. The term ˆnrv,tτ = bH(ˆθrv,tτ )nr represents the
complex AWGN with zero mean and variance σ2k. Addi-
tionally, the estimated delay ˜τrv,tτ and Doppler shift
˜νrv,tτ are acquired using the classic matched-ﬁltering
approach [13].
{˜τrv,tτ, ˜νrv,tτ}
= arg max
τ,ν
⏐⏐⏐∫ ∆Td
0
ˆζrv,tτζ∗rv,tτ (t−τ)e−j2πνrv,tτtdt⏐⏐⏐2,
(11)
where ∆Td represents the time duration of the received
signals. Using the estimates ˜τrv,tτ and ˜νrv,tτ obtained from
(11), and employing the interference cancellation method,
we can effectively eliminate the multi-user interference. For
simplicity, we assume ideal interference removal in this case.
Consequently, we have ¯ζrv,tτ = αϱrv,tτ aH(θrv,tτ )fkrv,tτ
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

14880 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
ζkr,tτ (tτ−τrv,tτ )ej2πτrv,tτνrv,tτ + ˆnkrv,tτ . Thus, the measure-
ment model for angles θrv,tτ can be derived as
˜ζrv,tτ =
∫ ∆Td
0
¯ζrv,tτζ∗rv,tτ (t− ˜τ)e−j2πνrv,tτtdt
=αϱrv,tτGmaH(θrv,tτ )fkrv,tτ + ˜nkrv,tτ, (12)
where Gm is the matched-ﬁltering gain and ˜nkrv,tτ represents
the noise obeying the distributionCN∼ (0,σ 2m) with variance
σ2m. Based on the observation model, the distance drv,tτ and
radial velocity ¯νrv,tτ are given by:
drv,tτ = ˜τrv,tτc2 = (˜τrv,tτ +ϵrv,tτ )c2 , (13)
¯νrv,tτ = ˜νrv,tτc2 = (˜νrv,tτ +ϵrv,tτ )c2 , (14)
where fc is the carrier frequency and c is the velocity of
signal propagation. The terms ϵrv,tτ ∼ N(0,σ 2rv,tτ ) and
˜ϵrv,tτ ∼N (0, ˜σ2rv,tτ ) represent the estimation errors of the
distance and radial velocity for vehicle v, respectively. In
particular, σ2rv,tτ and ˜σ2rv,tτ typically depend on the Signal-
to-Noise Ratios (SNRs) at the RSU and are given by:
σ2rv,tτ = ρ2σ2kG2m|αϱrv,tτe−j2πνrv,tτt|2|aH(θrv,tτ )fkrv,tτ|2 (15)
˜σ2rv,tτ = ˜ρ2σ2kG2m|αϱrv,tτe−j2πνrv,tτt|2|aH(θrv,tτ )fkrv,tτ|2, (16)
where ρ and ˜ρ are constants determined by the speciﬁc
system parameters. It is evident that the beamforming vector
fkrv,tτ signiﬁcantly inﬂuences the noise variances σ2rv,tτ and
˜σ2rv,tτ . Consequently, a Deep Learning (DL)-based approach is
employed to implicitly predict the state evolution and optimize
the beamforming matrix fkrv,tτ , thereby enhancing estimation
accuracy.
3) Communication Signal Model: The communication sig-
nal received by vehicle v is given by
ˇζkv,tτ
= ˜α
∑
r∈Rv
aH(θrv,tτ )˜ϱkrv,tτ
∑
v∈Vr
fkrv,tτζkrv,tτej2πνrv,tτt
| {z }
Desired signal
= ˜α
∑
v′∈Vr\v
∑
r∈Rv′
aH(θrv,tτ )˜ϱkrv,tτ
∑
v∈Vr
fkrv,tτζkrv,tτej2πνrv,tτt
| {z }
Interference signal
+wv,tτ, (17)
where ˜α2 = Mt represents the antenna gain and ˜ϱrv,tτ rep-
resents the communication channel coefﬁcient. Additionally,
wrv,tτ denotes the noise term at CA V v, which follows a
complex normal distribution CN (0,σ 2c) with an associated
noise variance σ2c . Speciﬁcally, the channel coefﬁcient ˜ϱrv,tτ
can be expressed as ˜ϱrv,tτ = (ˇϱrv,tτ/drv,tτ )ej2π(fc/c)drv,tτ
[28], where, ˇϱrv,tτ represents the channel gain constant at
the reference distance d0 = 1 . Given that ˇϱrv,tτ , fc, and c
are known at the RSU, the channel coefﬁcient ˜ϱrv,tτ can be
determined based on drv,tτ .
Assuming that the transmitted communication signal has
unit power, the received Signal-to-Interference-plus-Noise
Ratio (SINR) for vehicle v at time slot is given by [32]
ψkrv,tτ (hkrv,tτ, Fkr,tτ )
=
∑
r∈Rv|(hkrv,tτ )Hfkrv,tτ|2∑
v′∈Vr\v|∑r∈Rv′(hkrv′,tτ )Hfrv′,tτ|2 +σ2c, (18)
where hkrv,tτ denotes the equivalent channel vector for vehi-
cle v at time slot tτ . Consequently, the achievable rate
Rrv,tτ for vehicle v at time slot tτ can be expressed
as Rkrv,tτ (hrv,tτ, Fr,tτ )) = log 2(1 + ψkrv,tτ (hrv,tτ, Fr,tτ )).
In this context, multi-user interference from other vehi-
cles is considered during the sensing process, speciﬁcally∑
v′⁄=v frv′,tτζkrv,tτ . Similar to the sensing task, the achievable
sum-rate∑vRrv,tτ can be enhanced by adapting the beam-
forming matrix Fr,tτ . The channel capacity of V2I links must
satisfy the following constraints, respectively:
∑
k∈K
ρkrv,tτRkrv,tτ (hrv,tτ, Fr,tτ )≥ ¯Cv,∀v,tτ, (19)
where ¯Cv is the minimum required rate for receiver CA Vv to
receive the requested exogenous information.
Based on the safety requirement, each RSU r utilizes a set
of the binary variables βrvv′,tτ ∈{ 0, 1} to decide to sense
HDV at short-term time tτ and send their sensing information
to CA Vv′ at coverage area or not. This will be established by
setting βrvv′,tτ = 1 and βrvv′,tτ = 0, respectively.
Using the motion model, the relationship between
the estimated parameters (drv,tτ,θrv,tτ ) and the vehicle’s
position (xlv,tτ,ylv,tτ ) can be expressed as drv,tτ =√
(xlv,tτ )2 + (ylv,tτ )2, and θrv,tτ = arctan(ylv,tτ/xlv,tτ). As
shown in [32], the kinematic model characterizes the changes
in distance and angle for CA V v as d2rv,tτ = d2rv,tτ−1 +
∆d2−2d2rv,tτ−1∆d cosθrv,tτ−1, ∆d sinθrv,tτ−1 =dn sin ∆θ,
where ∆d and ∆θ represent the distance and angle variations
over one time slot. The beam tracking process focuses on
monitoring these changes in distances and angles for V
vehicles using the received signals deﬁned in (12).
III. V ALUE OF STATUS AND AUGMENTED -STATE
SEQUENTIAL STOCHASTIC DECISION PROCESS (SSDP)
In an ideal scenario, RSUs could instantly detect HDV posi-
tions and speeds and share them with CA Vs to enhance safety.
In practice, network constraints—such as limited bandwidth,
processing delays, and ﬁnite 5G resource blocks—restrict this
capability. Our research addresses these limitations by prior-
itizing critical safety data, thereby reducing communication
load, minimizing delays, and improving reliability. Although
methods like data compression ease congestion, high vehicle
density still risks transmitting non-essential data at the expense
of vital safety information.
The sensing–communication trade-off arises at the physical
layer, where sensing accuracy (via CRB) and communication
rate share radio resources such as power, bandwidth, and
beamforming: high-gain beams improve sensing but reduce
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14881
spatial multiplexing, whereas rate-oriented beams favor com-
munication at the potential cost of sensing. This trade-off is
explicitly embedded in the optimization (Problems 32–33), as
improving sensing tightens communication feasibility and vice
versa. Our V oI-driven framework manages this trade-off by
prioritizing resources according to vehicles’ V oI, enforcing
high sensing accuracy only for vehicles with critical safety
impact (e.g., low TTC) while allowing relaxed communication
rates for lower-V oI vehicles. Furthermore, the two-time-scale
design separates long-term V oI-based prioritization from short-
term beamforming decisions, stabilizing the trade-off and
preventing oscillations between sensing- and communication-
focused operation.
Each CA V determines its movement and radio channel
actions, denoted by uv and αv, using onboard sensing and
V2X communicationβv. Incorporating exogenous information
from other CA Vs can improve transportation efﬁciency and
network performance but also introduces challenges such as
signaling overhead, network congestion, higher costs, and
computational complexity from the curse of dimensional-
ity. Hence, a balance is required between the beneﬁts and
trade-offs of using such information. Optimizing system per-
formance relies on selecting the most valuable subset of
exogenous information, i.e., the data from CA Vs whose con-
tributions are most beneﬁcial for decision-making.
Each CA V v has local information about movement
at large-term and short-term times, sL,lv,τ = {ulv,τ,αlv,τ}
and sS,lv,tτ = {elv,tτ, ˜elv,tτ,ϑlv,tτ, zlv,tτ,θlv,tτ, qlv,tτ}, respec-
tively. However, in order to improve the performance
of both transportation and communication networks, each
CA V needs to obtain the information of other CA Vs
(i.e., exogenous information), large-term time information
¯sL,lv,τ = {sL,lv′,τ}v′∈V,v′⁄=v = {ulv′,τ,αlv′,τ}v′∈V,v′⁄=v and
short-term time information ¯sS,lv,τ = {sS,lv′,tτ}v′∈V,v′⁄=v =
{elv′,tτ, ˜elv′,tτ,ϑlv′,tτ, zlv′,tτ,θlv′,tτ, qlv′,tτ}v′,v′′∈V,v′⁄=v. In the
next subsection, after introducing SSDP and augmented-state
SSDP formulations, we adopt the KL divergence measure to
select a subset of all available states that can help each CA V
to improve its controlling policy in selecting movement and
radio parameters.
A. SSDP and Augmented-State SSDP Formulation
Deﬁnition 1: A standard SSDP over a ﬁnite time horizon
t∈{tτ,τ} is characterized for each agent k by the elements
{sk,t,ak,t, ¯sk,t,f s,f ¯s,rk,t}. Here, sk,t ∈ S represents the
state of agentk at timet, whereS is the state space. Similarly,
ak,t∈A denotes the action taken at time t, withA being the
action space. The exogenous information at timet, represented
as ¯sk,t ∈ ¯S, lies within the outcome space ¯S and becomes
available after performing action ak,t.
The functions fs and f ¯s deﬁne the state transition and
the evolution of exogenous information, respectively.
The next state is determined by the state transition
function as sk,t+1 = fs(sk,t,ak,t, ¯sk,t), while
the next exogenous information is computed as
¯sk,t+1 = f ¯s({sk,t′}t+1t′=0,{at′}t+1t′=0,{¯sk,t′}tt′=0,ξk,t). Here,
ξk,t accounts for all factors inﬂuencing ¯sk,t+1 aside from the
states, actions, and prior exogenous information up to time
t + 1.
The reward function at time t is denoted as
rk,t(sk,t,ak,t, ¯sk,t), and for each time step, a policy πk
is deﬁned as a set of functions µk,t that maps the current state
to an action, expressed as ak,t = µk(sk,t). Under a given
policyπk, the expected cumulative reward over the ﬁnite time
horizon can be calculated. The objective is to identify the
optimal policy π∗k that maximizes this total expected reward.
In an SSDP, during each time step t, the action ak,t is
determined solely by the current state sk,t, without any prior
information about the exogenous variable ¯sk,t.
Deﬁnition 2: When the exogenous information ¯sk,t is
known prior to taking action ak,t, an augmented-state SSDP
over a ﬁnite time horizon t ∈ T can be represented by
{˜sk,t,ak,t,f ˜s,f ¯s,rk,t}. In this formulation, the augmented
state ˜sk,t = (sk,t, ¯sk,t)∈S is created by incorporating the
exogenous information ¯sk,t into the original state space of the
standard SSDP.
The action ak,t ∈ A and the reward function
rk,t(sk,t,ak,t, ¯sk,t) = rk,t(˜sk,t,ak,t) remain unchanged
from those in the original SSDP. The exogenous
information ¯sk,t at time t is determined as
¯sk,t =
{
{sk,t′}t−1t′=0,{ak,t′}t−1t′=0,{¯sk,t′}t−1t′=0,ξk,t
}
, where
ξk,t encompasses additional parameters inﬂuencing ¯sk,t.
In this case, the state transition function fs is adapted to
reﬂect the augmented state structure.
˜sk,t+1 =f ˜s (sk,t,ak,t, ¯sk,t) =
(sk,t+1
¯sk,t+1
)
=
( fs (sk,t,ak,t, ¯sk,t)
f ¯s({sk,t′}t+1t′=0,{ak,t′}t+1t′=0,{¯sk,t′}tt′=0,ξk,t)
)
.
(20)
Likewise, at each time stept, a policy ˜πk speciﬁes the action
for a given state, such that the action ak,t is chosen according
to ˜µk(˜sk,t).
Remark 1: Deﬁnition 1 outlines the SSDP framework, which
includes the most general form of the exogenous information
transition function f ¯s. However, by placing a restriction on
f ¯s, such that the exogenous information transition is deﬁned as
¯sk,t+1 =f ¯s(sk,t+1,ak,t+1,ξk,t), where ξk,t is an independent
random variable following a predeﬁned distribution, the SSDP
effectively reduces to an MDP.
B. The Value of Exogenous Information Analysis
In this subsection, we focus on determining ˜π∗k(˜sk,t), which
leverages ¯sk,t to achieve better performance compared to
π∗k(sk,t). It is important to highlight that ˜π∗k(˜sk,t) andπ∗k(sk,t)
will yield identical results if ¯sk,t has no inﬂuence on the
reward function or the state transition dynamics of sk,t.
Consequently, the performance of ˜π∗k(˜sk,t) is guaranteed to be
at least as effective as that ofπ∗k(sk,t). The signiﬁcance of ¯sk,t
and its impact on ˜π∗k(˜sk,t) are determined by how ¯sk,t affects
both the reward function and the state transition. Therefore, the
optimal policy ˜π∗k(˜sk,t) for the augmented-state SSDP either
outperforms or matches the original SSDP policy π∗k(sk,t),
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

14882 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
provided that the exogenous information evolves according to
¯sk,t+1 =f ¯s(sk,t, ¯sk,t,ξk,t).
Remark 2: The optimal policy of the augmented-state SSDP,
represented as ˜π∗k(˜sk,t), demonstrates performance that is
either equivalent to or better than the optimal policy of the
original SSDP, π∗k(sk,t), provided that the exogenous infor-
mation adheres to the condition ¯sk,t+1 = f ¯s(sk,t+1,ξk,t). In
this scenario, the exogenous information ¯sk,t+1 is allowed to
depend on the statesk,t+1, but it must not depend on any other
variables aside from ξk,t, which is a random variable with an
independent distribution.
In the following, we model the effect of ¯sk,t on state
transitions as the question: “How much more accurately can
the state sk,t+1 be predicted when ˜sk,t incorporates ¯sk,t?”
To explore this, we transform the transition functions for the
system state and exogenous information, namely fs, f ˜s, and
f ¯s, into their corresponding transition probabilities: Ts =
Pr{sk,t+1|sk,t,ak,t}, T ˜s = Pr{sk,t+1, ¯sk,t+1|sk,t,ak,t, ¯sk,t},
and T ¯s = Pr{¯sk,t+1|¯sk,t,sk,t,ak,t}. The conditional KL
divergence betweenTs⊗T ¯s andT ˜s can then be computed as
follows:
DL(T ˜s‖Ts⊗T ¯s)
=
∫
˜sk,t+1,˜sk,t,ak,t
Pr{˜sk,t+1, ˜sk,t,ak,t}
× log2
( Pr{˜sk,t+1|˜sk,t,ak,t}
Pr{sk,t+1|sk,t,ak,t} Pr{¯sk,t+1|sk,t,ak,t, ¯sk,t}
)
,
(21)
where⊗ represents the Kronecker product. When the transi-
tion of sk,t is independent of ¯sk,t, the KL divergence equals
zero, meaning that ¯sk,t does not contribute to the transition
dynamics ofsk,t, and thus is unnecessary. Conversely, a higher
KL divergence indicates that incorporating ¯sk,t can enhance
the accuracy of predicting the future state. By evaluating the
KL divergence, each CA V can determine which speciﬁc subset
of exogenous information would be most effective for improv-
ing control policies. In the following sections, we explore how
exogenous information contributes to both transportation and
radio network control policies. Given that CA V mechanical
systems tend to operate slower than communication systems, a
two-time-scale DDPG algorithm is employed to reduce signal
processing complexity, minimize system load, and cut down
on signaling overhead, all while preserving performance.
Our method utilizes a two-time-scale framework to reduce
the complexity of signal processing and the overhead of sig-
naling. In this framework, the value of exogenous information
is categorized into two components: long-term (denoted as
L) and short-term (denoted as S). The long-term component
includes information related to the CA V’s control system and
the radio network, which is transmitted over extended periods,
denoted by times τ and tτ , respectively.
1) Value of Exogenous Information for Large-Term Time:
Although the transmission of all large-term time exogenous
information can improve the optimal control policy of CA Vv,
the transmission of this information ¯sL,lv,τ ={sL,l′v′,τ}′∈L,v′∈
V,v′⁄= v ={ul′v′,τ,αl′v′,τ}′,l′′∈L ,v′,v′′∈V ,v′⁄= v can
lead to the performance degradation due to the communication
and computation overheads, and the curse-of-dimensionality.
Therefore, a trade-off between improving the performance of
the optimal policy and reducing the state space dimension
should be considered by transmitting only the high value
components that help better predict the future state at CA V
v. In other words, only a subset of exogenous information
is used for predicting future states in the augmented-state
to get improved DRL-based control policy. To this end,
the value of each exogenous information is quantiﬁed. For
each CA Vv, the augmented-state ˜sL,lv,τ can include its driv-
ing status sL,lv,τ = {ulv,τ,αlv,τ} and exogenous information
¯sL,lv,τ =sLτ\sL,lv,τ transmitted by V2X from other CA Vs, where
sLτ ={sL,lv,τ,{sL,l′v′,τ}l′∈L,v′∈V,v′⁄=v}. If the state ˆsL,lv,τ is a subset
of all exogenous information ¯sL,lv,τ that can be used by CA V
v to predict the future actions of its preceding CA V (v− 1),
the value of this additional information ˆsL,lv,τ for CA Vv can
be analyzed by deriving the KL divergence for including
the additional information as (22), shown at the bottom of
the page, where aL,l(v−1),(τ+1) ={ul(v−1),(τ+1),αl(v−1),(τ+1)}.
As can be seen from (22), this KL divergence depends
on the ratio of Pr{ul(v−1),(τ+1),αl(v−1),(τ+1)|ˆsL,lv,τ} and
Pr{ul(v−1),(τ+1),αl(v−1),(τ+1)|sL,lv (tτ)} and shows how much
better CA Vv can predict the control parameters ul(v−1),(τ+1)
and αl(v−1),(τ+1) of CA V (v− 1) in large-term time τ + 1,
given the additional information from CA V v′. Therefore,
we form ˆsL,lv,τ as ˆsL,lv,τ = {sL,l′v′,τ|DLL,lvv′≥DL thv}, where
DLthv denotes the threshold for determining the high value
information. We deploy Monte Carlo (MC) method to esti-
mate the KL divergence, i.e., the value of (22) numerically,
as the expected value of log2
(
Pr{aL,l(v−1),(τ +1)|sL,l′v′,τ}
Pr{aL,l(v−1),(τ +1)|sL,lv,τ}
)
. By
generating F independent and identically distributed (i.i.d)
samples from Pr{aL,l(v−1),(τ+1),s L,l′v′,τ}, the approach involves
computingDLL,lvv′ = 1F∑Fi=1 log2
(
Pr{aL,l(v−1),(τ +1)|sL,l′v′,τ}
Pr{aL,l(v−1),(τ +1)|sL,lv,τ}
)
.
DLL,lvv′
(
T ˜sL,lv,τ‖TsL,lv,τ⊗TsL,l′v′,τ)
=
∫
˜sL,lv,(τ +1),˜sL,lv,τ,aL,lv,τ
Pr{˜sL,lv,(τ+1), ˜sL,lv,τ,a L,lv,τ} log2
(
Pr{˜sL,lv,(τ+1)|˜sL,lv,τ,a L,lv,τ}
Pr{sL,lv,(τ+1)|sL,lv,τ,a L,lv,τ} Pr{sL,l′v′,(τ+1)|sL,lv,τ,s L,l′v′,τ}
)
=
∫
aL,l(v−1),(τ +1)
Pr{aL,l(v−1),(τ+1),s L,l′v′,τ} log2

Pr{aL,l(v−1),(τ+1)|sL,l′v′,τ}
Pr{aL,l(v−1),(τ+1)|sL,lv,τ}

, (22)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14883
As the number of samples, F , increases, the MC estimation
error decreases. With such an approximation, the estimation
error distribution is normal with zero mean and variance σL,lvv′,
whereσL,lvv′ = 1F E
{[
log2
(
Pr{aL,l(v−1),(τ +1)|sL,l′v′,τ}
Pr{aL,l(v−1),(τ +1)|sL,lv,τ}
)]2}
, where
E{.} the expected value (mathematical expectation).
Based on the KL divergence value, CA Vv decides to request
the state information of CA V v′ in order to better predict the
preceding CA V(v− 1) actions.
2) Value of Exogenous Information for Short-Term Time:
A similar way can be considered for calculating the value of
exogenous information of the radio channel. If the state sS,lv,tτ
is a subset of the exogenous information of channel ¯sS,lv,tτ that
can be used by CA V v to predict the future state of CA V
(v−1), the value of this additional information sS,lv,tτ for CA V
v can be analyzed by deriving the KL divergence for including
the additional information as (23), shown at the bottom of the
page, where aS,lv,tτ ={βrv′v,tτ}. Therefore, we form ˆsS,lv,tτ as
ˆsS,lv,tτ ={sS,l′v′,tτ|DLS,lvv′≥DL thv}. (24)
We take similar steps to deal with the value of (23)
based on MC. Note that each RSU has only the short-
time term state and action that can be determined as
sSr,tτ ={ϑlv,tτ, zlv,tτ,θlv,tτ, qlv,tτ, hkrv,tτ} and aSr,tτ ={fkrv,tτ}.
KL divergence in our framework is used only as an
information-theoretic prioritization metric, quantifying how
much conditioning on a candidate exogenous state alters the
vehicle state transition distribution, i.e., the resulting predictive
gain. The ﬁnal admission of any exogenous state is deter-
mined through a hybrid information–physical decision process
that jointly enforces communication and sensing feasibility,
including SNR/SINR, latency, signaling overhead, available
bandwidth, RSU transmit power, and sensing accuracy, which
is explicitly captured via the CRB. Consequently, a high KL
divergence value does not automatically guarantee selection
if physical constraints render the acquisition or dissemina-
tion of the state unreliable or inefﬁcient; conversely, states
with moderate KL divergence but high safety relevance or
strong physical feasibility may be prioritized. Formally, we
compare the baseline marginal transition model with the
augmented transition model and evaluate the conditional KL
divergence. Only exogenous states whose KL divergence
exceeds a threshold are admitted into the augmented state. This
selection is tightly coupled with the binary request variables,
RSU resource allocation, and beamforming design. As a
result, the proposed two-time-scale DDPG framework exploits
slow-varying, high-value information for control policy learn-
ing and fast-varying, radio-centric information for beam-
forming adaptation, achieving a principled balance among
predictive accuracy, system complexity, signaling overhead,
and safety.
IV. P ROBLEM FORMULATION FOR RADIO RESOURCE
ALLOCATION AND VEHICLE CONTROL
We propose a predictive DL-based beamforming framework
that optimizes sensing while ensuring DL communication
quality, reducing signaling overhead, and improving robust-
ness. Performance is evaluated using CRBs and an associated
optimization problem.
A. Cramer-Rao Bound for Sensing Performance
The CRB is commonly used to assess the accuracy of
parameter estimation. Initially, we compute the Fisher Infor-
mation Matrix (FIM) based on the CRB theorem, as outlined
in [34]
J(okrv,t)= E



[
∂ lnp(˜okrv,t,okrv,t)
∂okrv,t
][
∂ lnp(˜okrv,t,okrv,t)
∂okrv,t
]T
,
(25)
where lnp(˜okrv,t,okrv,t) is the likelihood function of ˜okrv,t =
[˜ζrv,tτ, ˜τrv,tτ, ˜νrv,tτ ]T conditioned on the motion parameter
vector okrv,t = [ θrv,tτ,drv,tτ,ϑv,tτ ]T . In this scenario, the
relationship is expressed as ˜okrv,t =φ(okrv,t)+¯nkrv,t, whereφ(·)
represents the nonlinear function of the observation vector,
and ¯nkrv,t = [˜nk,n,ϵk,n,εk,n] includes the noise components.
Consequently, ˜okrv,t follows a complex Gaussian distribution,
˜okrv,t ∼ CN(φ(okrv,t), Σ), with a covariance matrix Σ =
diag(σ2n1Mr,σ 2τ,σ 2ν). Based on this, the conditional Probabil-
ity Density Function (PDF) can be derived as follows
p(˜okrv,t,okrv,t)
= 1πMr+2 det(Σ)e−(˜okrv,t−φ(okrv,t))HΣ−1(˜okrv,t−φ(okrv,t)). (26)
Once the FIM is obtained, the CRBs for the parameters
θrv,t and drv,t, corresponding to vehicle v at time slot t, can
be expressed as follows:
Φ(dkrv,t,f krv,t) =
[
1
σ2τ
(2
c
)2]−1
, (27)
Φ(θkrv,t,f krv,t) =

 1
σ2τ
(
∂ ˜ζrv,tτ
∂θkrv,t
)2(
∂ ˜ζrv,tτ
∂θkrv,t
)2

−1
. (28)
DLS,lvv′
(
T ˜sS,lv,tτ‖TsS,lv,tτ⊗TsS,l′v′,tτ) =∫
˜sS,lv,(tτ +1),˜sS,lv,tτ,aS,lv,tτ
Pr{˜sS,lv,(tτ+1), ˜sS,lv,tτ,a S,lv,tτ}
× log2
(
Pr{˜sS,lv,(tτ+1)|˜sS,lv,tτ,a S,lv,tτ}
Pr{sS,lv,(tτ+1)|sS,lv,tτ,a S,lv,tτ} Pr{sS,l′v′,(tτ+1)|slv,tτ,s S,l′v′,tτ}
)
=
∫
aS,l(v−1),(tτ +1)
Pr{aS,l(v−1),(tτ+1),s S,l′v′,tτ} log2

Pr{aS,l(v−1),(tτ+1)|sS,l′v′,tτ}
Pr{aS,l(v−1),(tτ+1)|sS,lv,tτ}

. (23)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

14884 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
The Mean Squared Error (MSE) matrix of okrv,t is bounded
below by the CRB, expressed as:
E
[
(˜okrv,tτ−okrv,tτ )(˜okrv,tτ−okrv,tτ )H]≽ J−1(okrv,t). (29)
Speciﬁcally, the lower bounds for the MSE of dkrv,t and
θkrv,t are represented as:
E
[
(˜θkrv,tτ−θkrv,tτ )2
]
≥J11
∆
= Ψ(θkrv,t,f krv,t), (30)
E
[
( ˜dkrv,tτ−dkrv,tτ )2
]
≥J22
∆
= Ψ(dkrv,t,f krv,t), (31)
where Jij represents the (i,j )-th element of the inverse of
J−1(okrv,t).
This paper aims to develop a beamformer design that
minimizes joint CRBs while adhering to constraints on
communication performance and transmit power. To sup-
port diverse joint CRB functions within the proposed neural
network framework, a utility function is crafted to mea-
sure sensing performance, while the achievable sum-rate is
employed as a metric to evaluate communication efﬁciency. As
a result, the optimization problem is reformulated as follows:
min
F
E{Φ(θ, F) + Φ(d, F)} (32a)
s.t. E
{∑
k
∑
r
Rkrv,tτ (hrv,tτ, Fr,tτ )
}
≥Rthv, (32b)
‖Fr‖F≤P maxr , (32c)
where the expectation E(·) is computed over the AWGN in the
transmission process and the stochastic channel realizations.
Furthermore, Rthv and P maxr represent the minimum required
communication sum-rate and the maximum allowable transmit
power, respectively.
Indeed, the CRB terms in (32) that depend on the vehi-
cle state qv,tτ and the instantaneous channel hrv,tτ are
handled explicitly by three coupled steps: (i) online estima-
tion — RSUs form ISAC measurements ~okrv,tτ and produce
MMSE/LS estimates ˆokrv,tτ = [ ˆθ, ˆd, ˆϑ] and ˆhrv,tτ , which
are used to compute the instantaneous, estimate-conditioned
CRB; (ii) predictive surrogate objective — the intractable
clairvoyant objective is replaced by its predictive expec-
tation Eˆo,ˆhΦ(ˆθ,F ) + Φ(ˆd,F ), implemented in training via
Monte-Carlo sampling from the estimator/posterior (the same
sampling used for the rate expectation in (16)), so estima-
tion uncertainty is explicitly integrated into the objective
and constraints; and (iii) robust learning & execution —
a two-time-scale MA-DDPG is trained on these sampled
(noisy/predicted) states so centralized critics learn the mapping
from uncertain estimates to long-term utility and decentralized
actors (taking ˆo, ˆh and uncertainty statistics as inputs) output
beamformers F , V oI requests β and controls ( α,u ) that are
robust to estimator errors. Constraint satisfaction (Eq. (16),
‖Fr‖F≤Pmaxr ) is enforced by penalty terms during training
and a light projection at execution, and the two-time-scale
split (fast beamforming adaptation, slow vehicle/V oI updates)
ensures Falways reacts to the freshest estimates; analytically,
this preserves the true dependence of CRB on beamforming
(e.g. σ2rv ∝ 1/ | aH(θrv)frv |2), because all CRB/rate
evaluations used in learning are computed on the sampled
(ˆθ, ˆd, ˆh)values so critics learn the correct sensitivity of CRB
to F .
Solving problem (32) poses signiﬁcant challenges due to
its variational nature and the non-convexity of the objective
function, particularly for traditional model-driven algorithms.
To tackle this complexity, we introduce a deep learning-based
method designed to efﬁciently determine the parameters and
solve problem (32). CA Vs make distributed decisions with
limited system knowledge. Each CA V can request RSUs to
share useful external information via V2I, aiming to minimize
its collision risk (CR) ratio by selecting an optimal subset of
external data. The optimization for a CA Vv is thus formulated
as:
min
αv,uv,βv,DLthv
1
T
∑
τ
∑
l∈L
E{Ξlv,tτ} (33a)
s.t.βv∈{ 0, 1}, (4)−(6), (19), (33b)
Problems (33) and (32) are tightly coupled: the RSU beam-
former F in (32) controls sensing accuracy (CRB) and the
achievable downlink rates Rkrv,tτ (hrv,tτ, F) (Eq. (19)), while
the CA V control actions (αv,uv) in (33) determine vehicle
positions qv,tτ via the dynamics (Eqs. (4)–(6)) and thus enter
the rate and channel models used by (32). In addition, the
V oI selection variables βrvv′,tτ and threshold DLthv change
the amount of downlink data required by each CA V , which in
turn affects the feasibility of RSU beamforming. Therefore,
the joint problem should be viewed as a dynamic multi-
agent program where F and (α,u,β, DLth) are co-optimized
to simultaneously satisfy CRB, communication, and safety
constraints. To solve this coupled, stochastic, and nonconvex
problem, we employ a two-time-scale MA-DDPG (centralized
training, decentralized execution): centralized critics capture
the coupling (how beamforming affects rates and safety), and
decentralized actors implement beamforming, V oI requests,
and vehicle controls. The two time scales reﬂect physical
dynamics (slow vehicle control, fast radio adaptation) and
guarantee that beamformers adapt rapidly to current state
estimates while long-term control and V oI policies evolve at
the slower vehicle time scale (see Algorithm 1).
V. T HE PROPOSED TWO-T IME SCALE MA-DDPG
FRAMEWORK
The optimization problems in (32) and (33) are highly non-
convex and heavily constrained, and their solution is further
complicated by time-varying CSI; classical static optimization
methods therefore either produce suboptimal outcomes or
require costly per-slot recalibration and cannot scale to multi-
stage setups that span many coherence intervals. To overcome
these limitations, we recast request design and resource allo-
cation as a Multi-Agent Reinforcement Learning problem in
which each CA V and the BS act as autonomous agents that
make decentralized decisions from local observations; this
formulation removes the need for repeated global optimization,
enables online adaptation to evolving radio conditions, and
permits agents to coordinate resource usage while minimizing
collision risk.
A Markov model can be employed to represent the move-
ment parameter control and resource allocation challenges,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14885
Fig. 2. V oI-driven two-time-scale ISAC & MA-DDPG: state estimates and CRB/FIM guide KL-based V oI selection; centralized training updates MADDPG
actors, deployed for distributed execution performing long-term vehicle control and fast beamforming, producing actions and feedback metrics.
with the BS and each CA V serving as distinct agents. Notably,
the optimization problem deﬁned in (33) is addressed for both
short-term and long-term horizons, while the problem in (32)
is resolved exclusively for long-term scenarios. At a given time
t∈{ tτ,τ}, each agent j∈{R ,V} derives a portion of the
global state, referred to as its local observation ˜sj,t. Following
this, the agent selects an actionaj,t, receives a rewardrj,t, and
the environment transitions to the subsequent state ˜sj,(t+1).
A. State Space and Local Observation
The global state, ˜st, includes all the environment compo-
nents, e.g., channel conditions, movement parameters, and the
agent’s behavior. However, only a subset of the global state
can be observed by each agent. The local observation of each
agent j includes channel information such as channel gain as
well as movement parameter obtained by sensors of CA V v.
B. Action Space
The action space for CA V’s agents includes exogenous
information request, and movement parameter determination.
C. Reward Function
Our aim is to maximize the utility functions deﬁned in (34)
for the proposed resource allocation problem. Therefore, the
instant reward function for agent j is deﬁned as
rj,t =



1
T
∑
τ
∑
l∈L
E{Ξlv,tτ}, j =v.
E{Φ(θ, F) + Φ(d, F)}, j =r.
(34)
D. Reinforcement Learning
In the MARL problem, the actions of each agent are selected
under its policy, ˜πj : Λ(Aj) ← S, where Λ denotes a
probability distribution. Moreover, in our resource allocation
problem, the joint policy ˜π is deﬁned as ˜π ={˜πj}j∈{V,R}.
A policy ˜πj = [˜µj,0,..., ˜µj,t,..., ˜µj,T−1] comprises of T
functions ˜µj,t, where aj,t = ˜µj,t(˜sj,t) for each time step t.
The aim is to determine the optimal policy ˜π∗j that maxi-
mizes the expected total reward ˜π∗j = arg max˜πj ˜J˜πj , where
˜J∗ = E˜sj,t{ ˜V∗j,t(˜sj,t)} is the episode expected reward.
The state value function is formulated as ˜Vj,t(˜sj,t) =
E˜πj[Gj,t|˜sj,t = ˜s], where Gj,t =∑∞i γirj,t+i and γ denotes
the discount factor to balance the instant and future rewards.
The value functions satisfy the Bellman equation, and thus can
be expressed as
˜Vj,t(˜sj,t) = E˜πj[rj,t+1 +γ ˜Vj,t+1(˜sj,t+1)|˜sj,t = ˜s]. (35)
Based on the value function in the value based RL problem,
the Q-value that represents the value from state ˜sj,t and action
aj,t over policy πj, is described as
˜Qj,t(˜sj,t,aj,t) =rj,t(˜sj,t,aj,t) +γE˜πj[ ˜Vj,t(˜sj,(t+1))]. (36)
The goal is to ﬁnd the optimal policy ˜π∗j that maximize
the value function. Since our movement parameter control
and resource allocation problem is high dimensional with
continuous action space, we utilize multi-agent deep deter-
ministic policy gradient (MA-DDPG) framework, in which
both the Q-value and policy are modeled as neural net-
works. Although MA-DDPG requires the global information
in the training phase, it can be executed distributively in
the execution phase by each agent, where each agent has
one actor and one critic network. The choice of MAD-
DPG is driven by the intrinsic structure of the proposed
problem rather than by preference. Speciﬁcally, our frame-
work involves (i) continuous and high-dimensional action
spaces (e.g., RSU beamforming vectors and CA V control
actions), which makes value-based MARL methods with dis-
crete actions (e.g., Q-learning) unsuitable; (ii) decentralized
execution under partial observability with strongly coupled
agents, where MADDPG’s centralized-training–decentralized-
execution (CTDE) paradigm provides stable learning while
respecting practical V2X deployment constraints; and (iii)
nonlinear and non-convex reward functions arising from
CRB-based sensing accuracy, SINR-constrained communica-
tion, and collision-risk metrics, for which policy-gradient
actor–critic methods such as MADDPG are well suited.
Moreover, the proposed two-time-scale design (slow V oI-
based state selection and control learning, fast beamforming
adaptation) naturally aligns with MADDPG’s actor–critic
architecture, enabling different update rates and replay buffers
while preserving policy consistency. Compared with alterna-
tive continuous-action MARL methods (e.g., multi-agent PPO
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

14886 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
or SAC), MADDPG offers lower computational overhead and
higher architectural transparency, which is critical for large-
scale, latency-sensitive vehicular systems.
The details of the proposed steps is shown in
Algorithm 1. The MADDPG agent j employs two main
deep neural networks: actor network with θµj parameter
to approximate the deterministic policy µj(sj|θµj ) and a
critic network with θQ parameter to approximate a state-
value function Qj(sj,aj|θQj ). In order to train the main
networks, a random mini-batch consisting of ¯Dj samples
(sij,ai,rij,si+1j )| ¯Dji=1 is selected from the replay buffer¯Dj. Each sample is assigned an index denoted by i. The
parameters θQ and θµ of each critic and actor networks are
updated as
Lj(θQj ) = (1/ ¯Dj)∑
i
(yij−Qj(sij,ai|θQj ))2, (37)
∇θµjJ = (1/ ¯Dj)∑
i
∇ajQj(sij,ai|θQj )∇θµjµj(sij|θµj ),
(38)
whereyij =rij +γQ′j(si+1j ,ai+1|θQ′j ) denotes the target value.
The actor and critic networks are softly updated for the target
parameters θµ′j and θQ′j as follows:
θµ′j ←ςjθµj + (1−ςj)θµ′j , (39)
θQ′j ←ςjθQj + (1−ςj)θQ′j . (40)
where ςj is a constant close to zero.
VI. C OMPUTATIONAL COMPLEXITY ANALYSIS
DDPG mainly includes a replay buffer and four neural
networks. Assuming that the actor network contains ¯L fully
connected layers and the critic network contains ¯K fully
connected layers. Thus the time complexity and space com-
plexity of DDPG can be derived with regard to ﬂoating point
operations per second (FLOPS) [37].
The neural networks for every layer have a vector ¯nActl and
a matrix ¯nActl × ¯nActl+1 for a fully connected layer to perform dot
product. The FLOPS computation is (2¯nActl − 1)× ¯nActl+1, i.e.,
multiply ¯nActl times and add ¯nActl − 1 times. Activation layers
also should be taken into consideration, which is calculated
without dot product. It is only measured by FLOPS, where
addition, subtraction, multiplication, division, exponent, and
square root are counted as a single FLOPS. So the time
complexity can be deﬁned as follows:
2
¯L−1∑
l=0
((2¯nActl − 1)¯nActl+1 +νA¯nActl+1)
+ 2
¯K−1∑
k=0
((2¯nCrik − 1)¯nCrik+1 +νA¯nCrik+1)
=O


¯L−1∑
l=0
¯nActl ¯nActl+1 +
¯K−1∑
k=0
¯nCrik ¯nCrik+1

 =O(n2) (41)
where νA is the corresponding parameter of the activation
layer [37].
Algorithm 1 Two-Time Scale MA-DDPG Framework
1: Initialize: For each agentj ∈ {V, R}:
2: Initialize actorµj, criticQj, and their target networks.
3: Initialize replay buffer ¯Dj and set learning ratesςj.
4: for each episode do
5: Initialize short-term statesS0 and long-term statesL0 .
6: for each long-term stepτ do
7: Each agent observessLj,τ and selects long-term actionaLj,τ .
8: ExecuteaLj,τ (e.g., acceleration, heading) and receiverLj,τ .
9: Store (sLj,τ,aLj,τ,rLj,τ,sLj,τ +1) in ¯Dj.
10: for each short-term steptτ do
11: ObservesSj,tτ and select aSj,tτ usingµj with exploration
noise.
12: Execute action and receive reward rSj,tτ and next state
sSj,tτ +1.
13: Store (sSj,tτ,aSj,tτ,rSj,tτ,sSj,tτ +1) in ¯Dj.
14: if update condition met then
15: Sample mini-batch from ¯Dj.
16: Update criticQj via loss (37).
17: Update actorµj using policy gradient (38).
18: Soft update target networks via (39), (40).
19: end if
20: end for
21: end for
22: if episode mod update interval = 0 then
23: Repeat actor/critic updates using long-term memory ˜Dj.
24: end if
25: end for
To explicitly demonstrate the computational tractability of
the policy improvement step, we derive the actor update
from the reformulated continuous-action MDP. Since each
actor outputs a compact, low-dimensional representation of
beamforming and resource control variables, the gradient com-
putation scales linearly with network parameters and does not
require solving high-dimensional constrained optimization at
each step. The centralized critic provides an efﬁcient approxi-
mation of the global Q-function, further reducing computation
by replacing iterative multi-agent optimization with a single
back propagation pass. Moreover, the two-time-scale decom-
position separates slow-varying environmental statistics from
fast control actions, which limits variance in gradient estimates
and stabilizes learning. Consequently, the policy improvement
reduces to a series of standard gradient-based updates with
complexity proportional to the network size and the number of
agents. This ensures that the proposed learning-based approach
is computationally tractable and feasible for real-time V2X
beamforming and resource allocation tasks.
VII. S IMULATION RESULTS
In this section, we evaluate the performance of our proposed
approach. We consider a transportation system with V = 100
CA Vs and a communication system with one BS. The main
simulation parameters including the technical constraints, the
parameters used for training the actor and critic networks,
and operational parameters are summarized in Table II [38].
We assume that small-scale and large-scale fading parameters
are updated every coherence time, and every 100 coherence
times, respectively. The control environment and MA-DDPG
algorithms are implemented in Python using Tensorﬂow 1.14.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14887
TABLE II
SIMULATION PARAMETERS
In order to evaluate the effectiveness of our proposed
scheme, we compare it with the following existing benchmark
schemes:
• Benchmark 1:
In [22], the authors proposed a sensing scheduling
paradigm for ISAC systems, where the base station
simultaneously serves multiple users via non-orthogonal
multiple access. System performance was evaluated using
sensing estimation mutual information, ensuring that the
base station extracts the required information from sched-
uled sensing targets. To this end, they formulated a joint
optimization of beamforming, transmission duration, and
sensing scheduling, with the objective of maximizing
sensing efﬁciency, deﬁned as the number of selected
sensing targets per transmission duration.
• Benchmark 2 : In [23], the authors investigated a
RIS-empowered ISAC network, where the base station
performs joint sensing and communication by trans-
mitting both information-bearing and dedicated sensing
waveforms across the wireless medium. They formulated
a joint optimization of the base station’s transmit beam-
forming and the RIS reﬂection beamforming, aiming to
maximize the sensing SNR.
A. Training and Convergence Properties
We evaluate the convergence of our algorithm against [22]
and [23] in terms of TTC for CA Vs (Fig. 3(a)) and CRB for
RSUs (Fig. 3(b)), conﬁrming the effectiveness of our approach.
Our algorithm achieves the highest TTC and lowest CRB, as
it explicitly accounts for vehicle Doppler spread. In contrast,
both baselines neglect Doppler effects, leading to degraded
performance. The model in [22] outperforms [23] due to
its use of successive interference cancellation in NOMA,
which supports simultaneous transmissions while mitigating
co-channel interference. Overall, our model improves TTC by
33% and 66%, and reduces CRB by 32% and 75% compared
to [22] and [23], respectively.
Fig. 3(c) shows the CR evolution over time. While [23]
reduces CR rapidly at the beginning but converges poorly, and
[22] achieves lower CR after several iterations, our proposed
model initially exhibits higher risk but progressively adapts
to the dynamic environment, ultimately eliminating collisions.
Overall, it achieves superior long-term CR reduction compared
to both baselines.
Under standard stochastic-approximation assumptions
(ergodic Markov dynamics, bounded rewards, Lipschitz &
differentiable parameterizations, bounded-variance noise) and
with a two-time-scale step-size schedule (critic updates faster
than actor), the proposed two-time-scale MA-DDPG admits
the following Stochastic Approximation (SA) to Ordinary
Differential Equation (ODE) analysis. Based on the critic
parameters by ΘQn ={θQj,n}j∈J and the actor parameters by
Θµn ={θµj,n}j∈J , the stochastic recursions can be written in
the abstract SA form
θQj,n+1 =θQj,n +αn(Hj(ΘQn, Θµn) +MQj,n+1), (42)
θµj,n+1 =θµj,n +βn(Gj(ΘQn, Θµn) +Mµj,n+1), (43)
whereHj(ΘQ, Θµ) is the mean temporal-difference (Bellman-
error) operator for the critic of agent j, Gj(ΘQ, Θµ) is the
mean policy-gradient direction computed using the critic, and
MQj,n+1,M µj,n+1 are martingale-difference noise terms with
uniformly bounded second moments. Assume the step-sizes
satisfy the Robbins–Monro conditions and a two-time-scale
separation ∑nαn = ∞, ∑nα2n < ∞, ∑nβn =
∞, ∑nβ2n <∞, βnαn−−−−→n→∞ 0, so that the critic evolveson the faster time scale and the actor on the slower one.
A practical choice that satisﬁes these conditions is αn =
a
(n+1)ξ, β n = b(n+1)ζ, 12 < ξ < ζ≤ 1, a,b > 0,
which ensures ∑nαn = ∞, ∑nα2n < ∞, ∑nβn =
∞, ∑nβ2n <∞ and βn/αn → 0. By the two-time-scale
(quasi-static) argument, as n→∞ :
• On the fast time scale, the actor parameters Θµn are quasi-
static, and each critic recursion tracks the ODE ˙θQj =
Hj(ΘQ, Θµ), so that θQj,n converges to the Temporal-
Difference (TD) ﬁxed point θQ,⋆j (Θµ).
• On the slow time scale, the critic is (approximately)
at θQ,⋆j (Θµ), and the actor dynamics follow the aver-
aged ODE ˙θµj =Gj({θQ,⋆k (Θµ)}k∈J, Θµ), whose stable
equilibria correspond to stationary points of the long-run
expected return (local optima or saddles).
Standard two-time-scale stochastic approximation results
imply that the joint iterates (ΘQn, Θµn) converge (almost surely
in the linear/compatible case; and to an internally chain-
transitive invariant set more generally) to an invariant set
of the limiting ODE system. Practically, this corresponds to
convergence to a local stationary policy (policy-gradient ﬁxed
point) with the critic accurately tracking the value-estimate.
The same reasoning extends to the CTDE/MADDPG setting:
centralized critics ΘQ, trained on the fast time scale with
access to additional information, track the multi-agent TD
ﬁxed point for the current joint policy, while decentralized
actors Θµ evolve on the slower time scale and converge to
stationary multi-agent policies under the same assumptions.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

14888 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 3. Convergence of the (a) TTC and (b) CRB, (c) CR over time.
Fig. 4. (a) TTC and (b) CRB under different numbers of CA Vs, (c) TTC and (d) CRB under different numbers of HDVs, (e) TTC and (f) CRB with different
numbers of RSUs.
B. Scalability of the Proposed Scheme
In the following, we reveal the inﬂuence of the number of
vehicles and the number of RSUs on performance and show
the result curves in Fig. 4. In Fig. 4(a), it can be seen that
with increase in the number of CA Vs TTC decreases, because
more CA Vs result in less distance between them which reduces
the time to collision. On the other hand, with more CA Vs the
accuracy of parameter estimation by RSUs decreases, so this
is why we see an upward trend for CRB in Fig. 4(b). Our
proposed model shows 22% and 43% increase in TTCs as
well as 6% and 8% decrease in CRBs over [22] and [23],
respectively. Furthermore, Fig. 4(c) and Fig. 4(d) demonstrate
that how HDVs can affect the performance of the system.
Similarly, more HDVs result in fewer TTCs and higher CRBs.
Compared to [22] and [23] respectively, our proposed model
increases TTCs by 33% and 53%, as well as decreases CRBs
by 72% and 83%.
When the number of RSUs increases, each RSU serves
fewer CA Vs, thereby enhancing overall system performance.
As shown in Fig. 4(e) and Fig. 4(f), this leads to an upward
trend in TTC and a downward trend in CRBs. Compared to
[22] and [23], our model achieves 24% and 43% improvement
in TTC, along with 7% and 8% reduction in CRBs, respec-
tively. A similar trend is observed when increasing the number
of antennas per RSU, as depicted in Fig. 5(a) and Fig. 5(b).
This improvement is attributed to the enhanced antenna gain
provided by large-scale antenna arrays. In this case, our model
achieves 26% and 42% improvement in TTC and reduces
CRBs by 6% and 7% relative to [22] and [23], respectively.
Furthermore, Fig. 5(c) and Fig. 5(d) present the perfor-
mance of our model under varying transmit power budgets.
As observed in Fig. 5(c), higher transmit power leads to
an increase in TTC, since the improved received SNR at
the RSU enables transmission of more vehicles’ information.
Similarly, Fig. 5(d) shows that CRBs decrease with increasing
transmit power, as the enhanced SNR yields more accurate
RSU estimations. Overall, our proposed model achieves up to
54% and 80% improvement in TTC, along with 7% and 8%
reduction in CRBs, compared to [22] and [23], respectively.
Fig. 5(e) illustrates the KL divergence across time steps.
It starts at a relatively high value near 0.9 and gradually
decreases, indicating that transmitting the corresponding V2X
information and incorporating it into the state space enhances
next-state prediction. Fig. 5(f) and Fig. 6 present the spacing
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14889
Fig. 5. (a) TTC and (b) CRB with different numbers of antennas, (c) TTC and (d) CRB with different transmit power budget, (e) The KL divergence for
each time step, (f) spacing error over time.
Fig. 6. (a) Velocity error, (b) acceleration, and (c) input acceleration over time.
Fig. 7. (a) CRB and (b) TTC for three CA Vs over time.
error, velocity error, and acceleration for both the proposed
and baseline models. At the beginning of each episode, the
input accelerationulv,τ is maintained at its maximum to rapidly
increase zlv,tτ , thereby promptly reducing the control errors
elv,tτ and ˜elv,tτ . As shown in Fig. 6(c), the input acceleration
ulv,τ in [22] and [23] exhibits larger ﬂuctuations compared to
our proposed model, indicating that vehicles supported by our
framework achieve smoother driving dynamics.
Fig. 7 is included to enhance the clarity of vehicle-speciﬁc
details. Fig. 7(a) depicts the time evolution of the CRB for
the 1st, 10th, and 50th CA Vs. As time increases, the accuracy
of parameter estimation improves; therefore, a decrease in the
CRB is observed. Fig. 7(b) illustrates the corresponding TTC
values for the same set of vehicles. With the progression of
time, vehicle behavior becomes increasingly stable, leading to
an increased TTC. This effect is reﬂected in the increasing
trend observed in Fig. 7(b).
VIII. S UMMARY AND CONCLUSION
This paper introduces a novel V oI-driven framework for
enhancing vehicular safety and positioning accuracy in
6G-enabled V2X networks through ISAC. A safety-aware
mechanism prioritizes transmission of only safety-critical
information, mitigating bandwidth and latency constraints in
ultra-dense trafﬁc. The sensing, communication, and control
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

14890 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
tasks are modeled as a two-time-scale sequential stochastic
decision problem, solved via a MA-DDPG-based multi-agent
reinforcement learning approach. By constructing a compact,
high-impact state representation, the method addresses the
curse of dimensionality and enables efﬁcient control of CA Vs.
Simulation results show signiﬁcant safety gains, with TTC
improved by up to 66% and CR minimized compared to
benchmarks. KL divergence analysis conﬁrms effective selec-
tion of high-value exogenous information, ensuring robust
decision-making in dynamic mixed-trafﬁc environments. The
proposed framework establishes a foundation for future 6G
ITS systems requiring precise positioning, reliable communi-
cation, and real-time safety assurance.
REFERENCES
[1] K. Hou and S. Zhang, “Optimal beamforming for secure integrated
sensing and communication exploiting target location distribution,”
IEEE J. Sel. Areas Commun. , vol. 42, no. 11, pp. 3125–3139, Nov.
2024.
[2] L. Li, J. Zhang, and T.-H. Chang, “Beamforming optimization for robust
sensing and communication in dynamic mmWave MIMO networks,”
IEEE J. Sel. Areas Commun. , vol. 43, no. 4, pp. 1354–1370, Apr. 2025.
[3] X. Gan et al., “Coverage and rate analysis for integrated sensing and
communication networks,” IEEE J. Sel. Areas Commun. , vol. 42, no. 9,
pp. 2213–2227, Sep. 2024.
[4] C. Liu et al., “Learning-based predictive beamforming for integrated
sensing and communication in vehicular networks,” IEEE J. Sel. Areas
Commun., vol. 40, no. 8, pp. 2317–2334, Aug. 2022.
[5] Q. Zhang, H. Sun, X. Gao, X. Wang, and Z. Feng, “Time-division ISAC
enabled connected automated vehicles cooperation algorithm design and
performance evaluation,” IEEE J. Sel. Areas Commun. , vol. 40, no. 7,
pp. 2206–2218, Jul. 2022.
[6] Z. Xiao and Y . Zeng, “Waveform design and performance analysis for
full-duplex integrated sensing and communication,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1823–1837, Jun. 2022.
[7] S. Xu, H. Sun, Y . Xu, T. Guo, C. Li, and L. Yang, “Distributed
compression method for channel calibration in cell-free MIMO ISAC
systems,” IEEE J. Sel. Areas Commun. , vol. 43, no. 7, pp. 2349–2363,
Jul. 2025.
[8] P. Gao, L. Lian, and J. Yu, “Cooperative ISAC with direct local-
ization and rate-splitting multiple access communication: A Pareto
optimization framework,” IEEE J. Sel. Areas Commun. , vol. 41, no. 5,
pp. 1496–1515, May 2023.
[9] Z. He, W. Xu, H. Shen, D. W. K. Ng, Y . C. Eldar, and
X. You, “Full-duplex communication for ISAC: Joint beamforming
and power optimization,” IEEE J. Sel. Areas Commun. , vol. 41, no. 9,
pp. 2920–2936, Sep. 2023.
[10] F. Liu, W. Yuan, C. Masouros, and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: Communication served by sensing,”
IEEE Trans. Wireless Commun. , vol. 19, no. 11, pp. 7704–7719, Nov.
2020.
[11] W. Yuan, F. Liu, C. Masouros, J. Yuan, D. W. K. Ng, and N. Gonz ´alez-
Prelcic, “Bayesian predictive beamforming for vehicular networks:
A low-overhead joint radar-communication approach,” IEEE Trans.
Wireless Commun., vol. 20, no. 3, pp. 1442–1456, Mar. 2021.
[12] L. Chen, Z. Wang, Y . Du, Y . Chen, and F. R. Yu, “Generalized
transceiver beamforming for DFRC with MIMO radar and MU-
MIMO communication,” IEEE J. Sel. Areas Commun. , vol. 40, no. 6,
pp. 1795–1808, Jun. 2022.
[13] X. Meng, F. Liu, C. Masouros, W. Yuan, Q. Zhang, and Z. Feng,
“Vehicular connectivity on complex trajectories: Roadway-geometry
aware ISAC beam-tracking,” IEEE Trans. Wireless Commun. , vol. 22,
no. 11, pp. 7408–7423, Nov. 2023.
[14] P. Yang, D. Duan, C. Chen, X. Cheng, and L. Yang, “Multi-sensor multi-
vehicle (MSMV) localization and mobility tracking for autonomous
driving,” IEEE Trans. Veh. Technol., vol. 69, no. 12, pp. 14355–14364,
Dec. 2020.
[15] W. Jiang, Z. Wei, B. Li, Z. Feng, and Z. Fang, “Improve
radar sensing performance of multiple roadside units cooperation
via space registration,” IEEE Trans. Veh. Technol. , vol. 71, no. 10,
pp. 10975–10990, Oct. 2022.
[16] Y . He, H. Zhao, and S. Shao, “Nonlinear self-interference cancellation in
vehicle networks for full-duplex integrated sensing and communication,”
IEEE Trans. Veh. Technol., vol. 73, no. 9, pp. 13980–13985, Sep. 2024.
[17] Z. Wang, K. Han, J. Jiang, F. Liu, and W. Yuan, “Multi-vehicle
tracking and ID association based on integrated sensing and com-
munication signaling,” IEEE Wireless Commun. Lett. , vol. 11, no. 9,
pp. 1960–1964, Sep. 2022.
[18] J. Singh, A. Gupta, A. K. Jagannatham, and L. Hanzo, “Multi-
beam object-localization for millimeter-wave ISAC-aided connected
autonomous vehicles,” IEEE Trans. Veh. Technol. , vol. 74, no. 1,
pp. 1725–1729, Jan. 2025.
[19] Z. Ye, C. Yu, H. Zhu, Y . He, M. Gao, and G. Yu, “ISAC-assisted
collision avoidance mechanism for vehicle-to-infrastructure systems,”
IEEE Trans. Intell. Vehicles, vol. 9, no. 10, pp. 6242–6257, Oct. 2024.
[20] Y . Li, F. Liu, Z. Du, W. Yuan, Q. Shi, and C. Masouros, “Frame structure
and protocol design for sensing-assisted NR-V2X communications,”
IEEE Trans. Mobile Comput. , vol. 23, no. 12, pp. 11045–11060, Dec.
2024.
[21] Z. Xu, S. Xu, H. Ding, and R. Xu, “An ISAC-based beam track-
ing scheme against inter-region interference for the multi-RSU V2I
scenario,” IEEE Trans. Veh. Technol. , vol. 74, no. 3, pp. 4257–4272,
Mar. 2025.
[22] C. Dou, N. Huang, Y . Wu, L. Qian, and T. Q. S. Quek, “Sensing-efﬁcient
NOMA-aided integrated sensing and communication: A joint sensing
scheduling and beamforming optimization,” IEEE Trans. Veh. Technol.,
vol. 72, no. 10, pp. 13591–13603, Oct. 2023.
[23] Z. Liu, X. Li, H. Ji, H. Zhang, and V . C. M. Leung, “Toward STAR-
RIS-empowered integrated sensing and communications: Joint active
and passive beamforming design,” IEEE Trans. Veh. Technol., vol. 72,
no. 12, pp. 15991–16005, Dec. 2023.
[24] Z. Du et al., “Integrated sensing and communications for V2I networks:
Dynamic predictive beamforming for extended vehicle targets,” IEEE
Trans. Wireless Commun., vol. 22, no. 6, pp. 3612–3627, Jun. 2023.
[25] B. Choudhury, V . K. Shah, A. Dayal, and J. H. Reed, “Experimental
analysis of safety application reliability in V2V networks,” in Proc.
IEEE 91st Veh. Technol. Conf. (VTC-Spring) , Antwerp, Belgium, May
2020, pp. 1–5.
[26] J. Aznar-Poveda, E. Egea-Lopez, A.-J. Garcia-Sanchez, and P. Pavon-
Mari´ao, “Time-to-collision-based awareness and congestion control for
vehicular communications,” IEEE Access , vol. 7, pp. 154192–154208,
2019.
[27] ETSI, ETSI TR 103.300-1: Integrated Satellite Communications; Inter-
faces Between Mobile-Satellite Services and Terrestrial Networks (Part
1), ETSI, Standard TR 103.300-1, 2024.
[28] ETSI TS 101.539-3: Digital Cellular Telecommunications System (Phase
2+); Universal Mobile Telecommunications System (UMTS); Mission-
Critical Services; MC-SUBUIL-T Architecture (Part 3), ETSI, Standard
TS 101.539-3, 2023.
[29] A. S. S ¨umer, E. Memisoglu, and H. Arslan, “A novel pilot allocation
technique for uplink OFDMA in ISAC systems,” IEEE Wireless Com-
mun. Lett., vol. 14, no. 8, pp. 2561–2565, Aug. 2025.
[30] C. M. Yetis, E. Bj ¨ornson, and P. Giselsson, “Joint analog beam selection
and digital beamforming in millimeter wave cell-free massive MIMO
systems,” IEEE Open J. Commun. Soc. , vol. 2, pp. 1647–1662, 2021.
[31] Z. Chen and Q. Liang, “Massive MIMO channel modeling based on
B5G/6G and consumer IoT,” IEEE Trans. Consum. Electron. , vol. 71,
no. 2, pp. 5984–5993, May 2025.
[32] Y . Cui, F. Liu, W. Yuan, J. Mu, X. Jing, and D. W. Kwan Ng, “Optimal
precoding design for monostatic ISAC systems: MSE lower bound
and DoF completion,” in Proc. IEEE Wireless Commun. Netw. Conf.
(WCNC), Dubai, United Arab Emirates, Apr. 2024, pp. 1–6.
[33] B. M. Lee, “Efﬁcient resource management for massive MIMO in high-
density massive IoT networks,” IEEE Trans. Mobile Comput. , vol. 24,
no. 3, pp. 1963–1980, Mar. 2025.
[34] H. Fang, X. Qiao, Y . Zhang, L. Yang, and H. Zhu, “On the performance
of RIS-aided cell-free massive MIMO systems under channel aging,”
IEEE Trans. Veh. Technol., vol. 73, no. 9, pp. 12828–12841, Sep. 2024.
[35] W. Yuan, N. Wu, Q. Guo, X. Huang, Y . Li, and L. Hanzo, “TOA-
based passive localization constructed over factor graphs: A uniﬁed
framework,” IEEE Trans. Commun. , vol. 67, no. 10, pp. 6952–6965,
Oct. 2019.
[36] Z. Yuan, L. Yu, Z. Wang, C. Li, T. Dallmann, and W. Fan, “Experimental
analysis and modeling of monostatic AA V RCS for ISAC channels,”
IEEE Antennas Wireless Propag. Lett. , vol. 24, no. 1, pp. 222–226,
Jan. 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 17 页

ABEDI et al.: PRECISE HDV POSITIONING THROUGH SAFETY-AW ARE ISAC IN A VoI-DRIVEN 6G V2X SYSTEM 14891
[37] C. Qiu, Y . Hu, Y . Chen, and B. Zeng, “Deep deterministic policy
gradient (DDPG)-based energy harvesting wireless communications,”
IEEE Internet Things J. , vol. 6, no. 5, pp. 8577–8588, Oct. 2019.
[38] Y . Cao et al., “Implementation of a cell-free RAN system with dis-
tributed cooperative transceivers under ORAN architecture,”IEEE J. Sel.
Areas Commun., vol. 43, no. 3, pp. 765–779, Mar. 2025.
Mohammad Reza Abedi (Member, IEEE) received
the M.Sc. degree in electrical engineering from the
Amirkabir University of Technology, Tehran, Iran,
and the Ph.D. degree form Tarbiat Modares Univer-
sity, Tehran. He is currently a Post-Doctoral Fellow
with Tarbiat Modares University. His research inter-
ests include multiple access techniques, energy
harvesting and wireless power transfer, coopera-
tive and adaptive wireless communications, wireless
edge caching, mobile edge computing, multibitrate
video transcoding, software deﬁned networking,
wireless network virtualization, and optimization theory.
Zahra Rashidi received the B.S. degree in infor-
mation technology engineering from the Amirkabir
University of Technology, Tehran, Iran, in 2014,
the M.S. degree in information technology engineer-
ing (computer networks) from the Sharif University
of Technology, Tehran, in 2017, and the Ph.D.
degree in computer engineering from Iran Univer-
sity of Science and Technology, Tehran, in 2023.
She is currently a Research Associate with Tarbiat
Modares University, Tehran. Her research interests
include sixth-generation (6G) networks, wireless
edge caching, network slicing, and integrated sensing and communications.
Nader Mokari (Senior Member, IEEE) received
the Ph.D. degree in electrical engineering from
Tarbiat Modares University, Tehran, Iran, in 2014.
Since 2015, he has been with the Department
of Electrical and Computer Engineering, Tarbiat
Modares University, where he is currently an Asso-
ciate Professor. In recent years, his research has
been funded by Mobile Telecommunication Com-
panies, Iran National Science Foundation, German
Research Foundation (DFG), and Qatar Research,
Development and Innovation (QRDI) Council. His
research interests include wireless technologies with a special emphasis on
wireless networks. He serving as a member of the Editorial Board for IEEE
TRANSACTIONS ON COMMUNICATIONS .
Hamid Saeedi (Member, IEEE) received the B.Sc.
and M.Sc. degrees in electrical engineering from the
Sharif University of Technology, Tehran, Iran, in
1999 and 2001, respectively, and the Ph.D. degree
in electrical engineering from Carleton University,
Ottawa, ON, Canada, in 2007. From 2008 to 2009,
he was a Post-Doctoral Fellow with the Department
of Electrical and Computer Engineering, University
of Massachusetts Amherst, Amherst, MA, USA.
He is currently with the College of Engineering,
University of Doha for Science and Technology,
Doha, Qatar, as an Associate Professor. He was a member of the Editorial
Board of IEEE C OMMUNICATIONS LETTERS and IEEE T RANSACTIONS ON
COMMUNICATIONS from 2014 to 2018 and from 2018 to 2020, respectively.
Nizar Zorba (Senior Member, IEEE) received
the B.Sc. degree in electrical engineering from
JUST University, Jordan, in 2002, and the Ph.D.
degree in signal processing for communications
from UPC Barcelona, Spain, in 2007. He is cur-
rently a Professor with the Electrical Engineering
Department, Qatar University, Doha, Qatar. He is an
Associate EiC of IEEE Communications Magazine ,
an Executive Editor of IEEE C OMMUNICATIONS
LETTERS , and an Associate Editor of IEEE T RANS -
ACTIONS ON COGNITIVE COMMUNICATIONS AND
NETWORKING . He served as an IEEE ComSoc Distinguished Lecturer from
2024 to 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:40 UTC from IEEE Xplore.  Restrictions apply.
