---
title: "Joint Beamforming and UAV Deployment Optimization for ISAC-Enhanced UAV-Assisted VEC"
zotero_key: "WRMKPUJZ"
pdf_key: "5Y3YEDPN"
doi: "10.1109/TWC.2026.3694912"
collection: "UAV"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Joint Beamforming and UAV Deployment Optimization for ISAC-Enhanced UAV-Assisted VEC — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

17666 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Joint Beamforming and UA V Deployment
Optimization for ISAC-Enhanced
UA V-Assisted VEC
Chunlin Li
 , Wenhao Wu, Zhihao Zhang
 , Student Member , IEEE, Tianbing Ma
 ,
and Shaohua Wan
 , Senior Member , IEEE
Abstract—In urban temporary congestion or hotspot scenarios,
ﬁxed roadside units (RSUs) often fail to provide reliable and
efﬁcient communication services due to their static deployment.
Unmanned Aerial Vehicles (UA Vs) can be rapidly deployed to
provide ﬂexible and on-demand communication and sensing sup-
port, effectively complementing ground infrastructure. However,
UA Vs are faced with challenges such as limited coverage, high
deployment complexity, and unbalanced communication-sensing
performance. These challenges give rise to increased energy
consumption and reduced communication efﬁciency. To address
these issues, we propose a UA V energy-efﬁcient deployment
method based on Integrated Sensing and Communication (ISAC),
which balances performance and energy consumption. Specif-
ically, under UA V energy constraints, we jointly optimize UA V
deployment positions and beamforming to maximize communica-
tion capacity. We decompose the problem into two subproblems:
UA V deployment and beamforming strategy optimization. During
the iteration process, the subproblems are respectively solved by
using the sparrow search algorithm based on refraction-based
learning and successive convex approximation-based iterative
algorithm and the ﬁrst order Taylor expansion method. Sim-
ulation results show that the proposed method outperforms
the benchmark schemes, achieving approximately a 10.51%
improvement in average coverage rate and a 19.83% reduction in
UA V energy consumption, while maintaining an effective trade-
off between communication coverage and energy efﬁciency.
Received 8 January 2026; revised 5 May 2026; accepted 12 May
2026. Date of current version 28 May 2026. This work was supported
in part by the Open Fund of State Key Laboratory of Digital Intelligent
Technology for Unmanned Coal Mining under Grant SZQZ2025-2-024,
in part by the National Natural Science Foundation of China (NSFC)
under Grant 62372344 and Grant 62171330, in part by the National Key
Research and Development Program of China under Grant 2023YFB3308701,
in part by the Natural Science Foundation of Guangdong Province of
China under Grant 2024A1515011155, and in part by Shenzhen Sci-
ence and Technology Program under Grant JCYJ20240813114223031. The
associate editor coordinating the review of this article and approving
it for publication was D. Niyato. (Corresponding authors: Chunlin Li;
Tianbing Ma.)
Chunlin Li is with the State Key Laboratory of Digital Intelligent Tech-
nology for Unmanned Coal Mining, Huainan 232001, China, and also
with Wuhan University of Technology, Wuhan 430063, China (e-mail:
chunlinli2020@163.com).
Wenhao Wu and Zhihao Zhang are with Wuhan University of Technology,
Wuhan 430063, China.
Tianbing Ma is with the State Key Laboratory of Digital Intelligent
Technology for Unmanned Coal Mining, Anhui University of Science and
Technology, Huainan 232001, China (e-mail: dfmtb@163.com).
Shaohua Wan is with Shenzhen Institute for Advanced Study, University
of Electronic Science and Technology of China, Shenzhen 518110, China.
Digital Object Identiﬁer 10.1109/TWC.2026.3694912
Index Terms —Unmanned aerial vehicles (UA Vs), vehicular
edge computing (VEC), integrated sensing and communication
(ISAC), UA V deployment, beamforming optimization, block coor-
dinate descent, sparrow search algorithm.
I. I NTRODUCTION
A. Background
W
ITH the rapid advancement of intelligent transportation
systems, unmanned aerial vehicle (UA V) technology
has emerged as a critical solution for enhancing communica-
tion efﬁciency in vehicular edge computing (VEC), leveraging
its advantages of ﬂexible deployment and high-altitude per-
spective [1]. In urban scenarios, especially during temporary
trafﬁc congestion or hotspot events, ﬁxed roadside units
(RSUs) often fail to provide reliable and low-latency com-
munication services due to dynamic trafﬁc conditions and
severe interference [2]. Traditional solutions are costly, time-
consuming, and inﬂexible in adapting to dynamic trafﬁc
conditions. With continuous advances in UA V technologies,
UA Vs have emerged as promising ofﬂoading platforms and
merit further investigation.
In UA V-assisted VEC, previous UA V deployment studies
primarily use separate communication and sensing devices to
improve vehicular connectivity and perception [3]. However,
such approaches fail to meet the strict requirements for ultra-
low latency and high reliability in transmitting broadband
sensing data. Moreover, deploying an excessive number of
UA Vs requires complex spectrum management and coordina-
tion mechanisms [4], [5]. To overcome these limitations, we
propose the Integrated Sensing and Communication (ISAC)
technology into UA V-assisted VEC systems. By unifying
traditional wireless communication and sensing functions,
ISAC enables vehicles to obtain comprehensive environmental
awareness while simultaneously improving both communica-
tion and perception performance [6].
ISAC is a technique that combines sensing and com-
munication functions into a uniﬁed framework. Traditional
UA V-assisted VEC systems struggle to achieve balanced time
slot allocation and energy efﬁciency under vehicle mobility
constraints. In existing ISAC frameworks, dual-functional sig-
nals necessitate the allocation of communication resources
within extremely short time slots, while UA V mobility exac-
erbates beam alignment errors. The UA V deployment position
directly affects the path loss and interference level of beam-
forming, while the beamforming strategy restricts the coverage
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT BEAMFORMING AND UA V DEPLOYMENT OPTIMIZATION 17667
efﬁciency of UA V deployment. The two are tightly coupled,
and separate optimization cannot simultaneously address the
coverage limitations [4]. Therefore, we focus on the critical
challenge of UA V deployment:
• How can communication, sensing and timeslot allocation
be jointly optimized in ISAC-enhanced UA V-assisted
VEC to minimize system energy consumption and max-
imize ISAC efﬁciency?
• How to jointly optimize the UA V deployment and beam-
forming in ISAC-Enhanced UA V-Assisted VEC scenario
to maximize UA Vs communication capacity?
B. Motivations
Therefore, the following limitations still exist in current
ISAC-Enabled UA V-Assisted VEC studies:
1) Existing ISAC-Enabled UA V-Assisted VEC schemes
have yet to fully exploit the joint capabilities of com-
munication and sensing: In UA V-assisted VEC systems,
the integration of ISAC introduces an inherent trade-
off between communication and sensing performance,
such that improving one generally degrades the other,
which complicates the overall system design. However,
existing works [7], [8], [9], [10], [11], [12] do not
explicitly characterize this trade-off between sensing
and communication, nor do they jointly consider the
associated coupled factors. In addition, existing studies
[13], [14] mainly focus on UA V trajectory or deployment
optimization, without jointly considering communica-
tion beamforming and sensing performance, which leads
to suboptimal system design. To address these limita-
tions, we formulate a joint optimization problem that
explicitly captures the communication-sensing trade-off
while incorporating UA V deployment and beamforming,
ensuring an efﬁcient and balanced system design.
2) High Complexity of Joint UA V Deployment and
Beamforming in ISAC-Enhanced UA V-Assisted VEC:
The solution space grows rapidly when UA V deploy-
ment and beamforming are jointly optimized, making
it difﬁcult to obtain high-quality solutions within a
limited computational budget. However, current works
[15], [16], [17], [18] typically adopt suboptimal solu-
tion methods based on convex/non-convex optimization
techniques, such as iterative decomposition, alternat-
ing optimization, successive convex approximation, and
semi-deﬁnite relaxation, which still lack efﬁciency in
handling the resulting non-convex joint optimization
problem. To tackle this challenge, we propose a novel
hybrid algorithm that integrates block coordinate descent
and heuristic-convex optimization, speciﬁcally designed
to efﬁciently solve the non-convex optimization problem
for UA V deployment and beamforming.
C. Contributions
This paper optimizes UA V placement and beamforming
to reduce energy consumption and expand coverage, aiming
to maximize communication capacity. In summary, the main
contributions of this paper are as follows:
1) A joint optimization problem for beamforming and
UA V deployment in ISAC-Enabled UA V-Assisted VEC
to maximize communication rate with ensuring sens-
ing performance: We jointly consider communication,
sensing, and energy in an integrated optimization formu-
lation. Speciﬁcally, we formulate a joint optimization
problem that capturing the coupling between commu-
nication and sensing by incorporating communication
capacity and CRB-based sensing metrics, which is fur-
ther modeled as a non-convex optimization problem.
Based on these metrics, we introduce an ISAC sensing-
communication effectiveness function to quantify and
balance the trade-off between communication and sens-
ing performance. To evaluate the proposed method, we
employed the Veins simulation platform, and simulation
results demonstrate improvements in both communica-
tion latency and energy consumption.
2) Joint Block Coordinate Descent and Heuristic-Convex
Optimization for UA V Deployment and Beamform-
ing: We propose a joint optimization scheme for
UA V deployment and beamforming. Under speciﬁc
constraints, we decompose the coupled optimization
problem into tractable subproblems and iteratively opti-
mize UA V deployment and beamforming using a hybrid
algorithm that combines block coordinate descent and
heuristic-convex optimization. Simulations show the
method boosts average coverage rate by 10.51% and
reduces UA V energy consumption by 19.83% compared
with the baseline algorithms.
The remainder of the paper is structured as follows.
Section II reviews related work. Section III introduces the
system model and problem formulation. Section IV describes
the proposed solution and algorithm. Section V presents the
simulationresults, while Section VI provides conclusions and
outlines potential future work.
II. R ELATED WORK
In this section, we review related studies on UA V deploy-
ment, including beamforming, multidimensional deployment,
and ISAC mechanisms.
A. UA V Deployment Optimization in UA V-Assisted VEC
Dai et al. [7] addressed the computational overload of
RSUs in dense urban VEC scenarios by deploying a UA V
as an aerial edge server to ofﬂoad tasks from overloaded
RSUs. Chen et al. [8] devised a two-layer particle swarm
optimization–genetic algorithm–greedy algorithm that jointly
optimizes UA V deployment and computation ofﬂoading to
minimize average task response time in multi-UA V MEC
systems. Hao et al. [9] studied the task ofﬂoading problem in a
multi-UA V-assisted MEC system, focusing on task priority and
binary ofﬂoading decisions. Deng et al. [10] proposed a joint
beamforming and trajectory optimization framework for UA Vs
to maximize the communication performance. Deng et al. [11]
proposed an adaptable integrated sensing and communication
mechanism in UA V-enabled systems that jointly optimizes
beamforming and trajectory via alternating optimization to
maximize system throughput. Zhang et al. [12] proposed a
joint beamforming design for an active STAR-RIS-assisted
full-duplex ISAC system. Jiang et al. [13] proposed an ISAC-
based UA V safe-ﬂight strategy that improves target accuracy
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

17668 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. Dynamic multi-UA V deployment in ISAC-enhanced UA V-assisted
VEC.
and reduces communication delay. Chen et al. [14] optimized
full-duplex self-interference cancellation to improve radar
signal-to-noise ratio.
B. UA V Deployment Optimization in ISAC-Enhanced
UA V-Assisted VEC
Lyu et al. [15] optimized UA V trajectory and beamforming
to maximize ISAC-enabled device performance. Liu et al. [16]
proposed a UA V-assisted ISAC system for IoT, where the UA V
simultaneously provides sensing and communication services
for ground IoT nodes. Cheng et al. [17] developed a networked
ISAC framework to improve communication and detection
through coordinated beamforming and UA V trajectory design.
In summary, above strategies provide effective solutions for
enhancing the efﬁciency of UA Vs. However, studies [12], [19]
do not explicitly consider the coupling between communica-
tion and sensing in ISAC-enabled systems. Studies [13], [14],
[15], [16], [17] mainly focus on speciﬁc aspects such as UA V
deployment or resource allocation, without jointly considering
communication beamforming and sensing performance. In
contrast to the previous studies, this paper formulates the joint
design of UA V positioning optimization and beamforming
strategy as a non-convex optimization problem. Aiming to
maximize the communication capacity, we decompose the
original problem via the Block Coordinate Descent (BCD)
method, thereby achieving a balanced optimization between
energy consumption and communication performance.
III. S YSTEM MODEL AND PROBLEM FORMULATION
In this section, we ﬁrst describe the ISAC-enhanced
UA V-assisted VEC, and then gradually analyze the system’s
communication model, sensing model and energy consumption
model.
A. System Overview
The ISAC-enhanced UA V-assisted VEC framework is illus-
trated in Fig. 1. It comprises an in-vehicle terminal layer and
an edge layer. The system workﬂow is as follows: (1) Vehicles
ﬁrst upload complex tasks to the edge computing station.
(2) The edge base station and UA Vs exchange multisource
Fig. 2. Schematic diagram of time slot frame allocation for integrated sensing
assisted by UA V .
information. (3) We adopt the BCD method to alter-
nately optimize UA V deployment positions and beamforming.
(4) Determine the optimal UA V deployment positions to
maximize communication capacity and coverage.
B. Time Slot Division Model
The system consists of N vehicles and U UA V edge nodes.
The vehicle movement process is divided into T time slots,
with each time slot length set to τ(τ > 0). The system
is assumed to be quasi-static, meaning that the states of
vehicles and UA Vs remain unchanged within a short time
slot but can vary in different time slots [20], τ is chosen
to be sufﬁciently small so that the UA V’s location remains
approximately unchanged in a time slot [21]. We use xu,n(t)
to represent perceptual scheduling, where xu,n(t)∈ {0, 1}.
When xu,n(t) = 1 , UA Vu serves vehicle n in time slot t.
Each UA V can serve at most one vehicle in each time slot,
i.e.,∑Nn=1xu,n(t)≤ 1.
Fig. 2 illustrates the time-division frame structure for ISAC,
which is based on the dual-period frame format in the 5G
NR Time Division Duplex (TDD) mode [22]. For each pair
of UA V-vehicle, the transmission period includes a downlink
slot, a ﬂexible slot, and an uplink slot. The downlink slot
is divided into sensing (S) and communication (D) with
adjustable symbol positions, since sensing is realized through
downlink transmission, while the uplink is used only for com-
munication. This TDD design provides time-domain isolation
between sensing and communication, thus avoiding mutual
interference.
We use Tdownu,n to indicate the time when the nth vehicle
user downloaded data from the UA Vu in time slot t, and use
Tflexu,n to represent ﬂexible time slots, and use Tupu,n to indicate
the time when the nth vehicle user uploaded data to the UA V
u in time slot t. The time resource constraints in this article
are shown:
xtu,n(Tdownu,n (t) +Tflexu,n (t) +Tupu,n(t)) =τ. (1)
The vehicle model employs the Krauss vehicle-following
model, used to simulate the behavior of trafﬁc ﬂow and prevent
vehicle collisions [23]. To compensate for the continuous
movement of vehicles during the time required for the UA V
to ﬂy to a new position, we do not directly use the real-time
position of the vehicle at timet in distance calculation. Instead,
we ﬁrst predict its estimated position at the arrival time based
on its linear velocity, with the formula as follows:
ˆxn(t) =xn(t) +vn,x(t)∆t, ˆyn(t) =yn(t) +vn,y(t)∆t,
(2)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT BEAMFORMING AND UA V DEPLOYMENT OPTIMIZATION 17669
wherevn,x(t) andvn,y(t) represent the instantaneous velocity
components of the vehicle along the horizontal directions. The
estimated ﬂight delay for the UA V to ﬂy from its current
position to the target deployment point are given:
∆t = du,m
Vxy,max
, (3)
where, Vxy,max represents the maximum horizontal speed of
the UA V . The horizontal distance the UA V needs to move are
given:
du,m =
√
(xu,target−xu,current)2 + (yu,target−yu,current)2. (4)
C. Communication and Sensing Model
This section uses Frequency-Division Multiple Access
(FDMA) technology for UA V-to-vehicle communication. TDD
provides time-domain separation among downlink sensing,
downlink communication, and uplink communication, whereas
FDMA allocates orthogonal frequency resources to UA V-to-
vehicle links, thereby mitigating co-channel interference in the
baseline model. The terrestrial channel follows the free space
path loss model. Assume that UA Vs and vehicles are equipped
withMU andMN antennas, respectively. The LoS and NLoS
communication channels between UA V u and vehicle n are
given:
HcLos =
√
K
K+1α0ejϕc0√MNMUa(MU,θu,0)a(MN,θn,0)H
(5)
HcNLos =
√
1
K + 1
P∑
p=1
αpejϕcp√MNMU√
P
a(MU,θu,p)a(MN,θn,p)H (6)
When the UA V is deployed above road intersections and
higher than surrounding buildings, a larger elevation angle
between the UA V and vehicles increases the LoS probability
[24]. Hence, the UA V-vehicle channel matrixHc∈CMU×MN
can be decomposed into LoS and NLoS components as
Hc =HcLos +HcNLos, (7)
where K is the fading factor. For the p-th path, θn,p and
θu,p(0 ≤ p ≤ P ) denote the departure and arrival angles,
respectively, whileαp∈R+ and ϕcp represent the small-scale
fading factor and phase shift, respectively.a(M,θ ) denotes the
antenna steering vector for the M-element array with respect
to azimuth angle θ. Considering a uniform linear array with
half-wavelength spacing, the antenna steering vector is
a(M,θ ) = 1√
M
[1e−jπcosθ··· e−(M−1)jπcosθ ]T. (8)
For the sensing channel model, the departure angle of the
sensing path is the same as that of the communication path.
In addition, since the UA V antenna is set up near the vehicle
antenna, the arrival angle of the path is approximately equal
to the departure angle. Therefore, the sensing channel is
Hs =
P∑
p=0
βpejϕsp√MNMU√
P
a(MU,θu,p)a(MN,θn,p)H, (9)
whereβp∈R+ andϕsp(0≤p≤P ) are the small-scale fading
factor and phase shift of the sensing channel, respectively.
It is assumed that both UA Vs and vehicles use beamforming
technology to compensate for path loss. The communication
signal from UA Vu to vehicle n can be expressed as
ycn =ωu,nHcu,nsu,n +
N∑
j,j⁄=n
ωu,jHcu,nsu,j + (σcn)2, (10)
where ω∈CMU is the beamforming vector at the UA V , and
(σcn)2 represents Gaussian white noise. In addition, constraint
(26e) prevents multiple UA Vs from serving the same vehicle
simultaneously in the same time slot.
Under ideal orthogonal resource allocation among different
UA Vs, inter-UA V co-channel interference is neglected [25].
Our primary scenario is not a dense multi-UA V network,
but an urban temporary trafﬁc-congestion scenario in which
a limited number of UA Vs are rapidly deployed at urban
crossing roads as on-demand supplements to the existing RSU
infrastructure [7], where the UA Vs are typically assigned to
different crossing roads that are spatially separated by a certain
distance, the resulting Signal-to-Interference-plus-Noise Ratio
(SINR) can be expressed as follows:
SINR =
‖‖ωu,nHcu,nsu,n‖‖2
(σcn)2 . (11)
The communication capacity is given:
Cn =
T∑
t=1
xu,n(t) log2(1 + SINR). (12)
Over the entire ﬂight period T , the total communication
capacity of the system is given by
Csum =
N∑
n=1
Cn. (13)
The radar sensing received signal in the ISAC equipment
carried by the vehicle is represented as shown:
ys =Hsfsss +ns, (14)
where fs ∈ CMU is the sensing beam carrying the signal
ss∈ C, and ns is Gaussian white noise, including thermal
noise and residual self-interference, with a value range of
CN (0, (σsn)2). Typically, sensing and communication beams
differ in direction for sensing needs. Independent sequences
for both offer higher correlation gain to differentiate signals.
This paper uses the Cramer-Rao Bound (CRB) to evaluate the
radar’s estimation capability, as shown:
CRBsΘ =diag([I(Θ)]−1), (15)
where I(Θ) is the Fisher information matrix regarding the
channel parameter Θ, represented as (16), shown at the bottom
of the next page, where ysk is the k-th ys, This paper uses
CRBloc to represent the CRB of position estimation. Typi-
cally, the position estimation is decomposed into angle φ and
distanced estimation. Therefore, the CRB is also decomposed
as shown:
CRBloc =d2CRBφ +CRBd, (17)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

17670 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
where c is the speed of light. The sensing beam scans the
target to detect and estimate its position, with the sensing beam
covering the target represented as fs = a(MN,φs), and the
received power shown:
As =
√
(1−γ)ε√MNMUβ√
P + 1 |aH(MN,φ )a(MN,φs)|, (18)
where γ is the ISAC power allocation coefﬁcient, γε and
(1− γ)ε are the power of the communication beam and
the sensing beam, respectively, and β is the fading factor
determined by the path loss and radar cross-section of the
vehicle target. According to radar ranging theory [26], the
CRB of the distance is expressed as:
CRBd = c24 (σsn)2(P + 1)(1−γ)εMN(MU)2β2(B′)2·W 2, (19)
where W represents the bandwidth. The expression for B′ is
given:
B′ = sin
(MN
2 (cosφ−cosφs)
)
sin
( 1
2(cosφ−cosφs)
) . (20)
where B′ denotes a Dirichlet-kernel-type form with respect
to the angular mismatch term cosφ− cosφs. This structure
characterizes the angular selectivity of the received signal and
directly facilitates the subsequent derivation of the CRB for
angle estimation [27]. The equation (20) directly facilitates the
derivation of the CRB of the angle φ, as shown:
CRBφ = 6(σsn)2(P + 1)(1−γ)εMN(MU)2((MU)2− 1)β2(B′)2π2 sin2φ.(21)
Since both angle and distance estimations are inversely
proportional to (1−γ), an increase in γ reduces the accuracy
of position estimation.
D. ISAC Model
Using the ISAC efﬁciency as a metric, this indicator aims to
characterize the maximum achievable communication capacity
under unit sensing error. It is deﬁned as the ratio of commu-
nication capacity to parameter estimation error, as shown:
GISAC = Cκ +CRBloc, (22)
where C represents the communication capacity, CRBloc
represents the CRB of parameter estimation, and κ is a preset
constant to limit the maximum value of GISAC .
According to its deﬁnition, GISAC increases with commu-
nication capacity and decreases with the CRB. Thus, GISAC
characterizes the overall ISAC efﬁciency, and a larger value
indicates better joint communication–sensing performance. In
this paper, GISAC is adopted as the ISAC utility, and max-
imizing it balances communication throughput and sensing
precision.
E. Energy Consumption Model
1) Deploy and Sensing Energy Consumption: The energy
consumption of the UA V consists of two main parts: sens-
ing and communication energy consumption and propulsion
energy consumption. The total sensing and communication
energy consumption of the UA V at time slot t in shown as
follows:
EuISAC (t) =τ·
U∑
u=1
N∑
n=1
xu,n(t)· (||wu(t)||2 +||ru(t)||2),
(23)
where wu(t) and ru(t) are the transmission beamforming
vectors for UA V communication and sensing, respectively. The
propulsion energy consumption of a UA V at time slot t can
be modeled as
EuFly (t) =[P0
(
1 + 3(Vxy(t))2
U2tip
)
+P1
(√
1 + (Vxy(t))4
4V 40 − (Vxy(t))22V 20
) 12
+C0(Vxy(t))3 +G0Vz(t)]τ, (24)
whereP0,P1 andC0 are constant parameters related to ﬂight
dynamics,Utip andV0 are the tip speed and mean speed of the
rotor, respectively, and G0 is the weight of the UA V .Vxy(t)
and Vz(t) are the horizontal and vertical ﬂight speeds of the
UA V at time slott, respectively, and are constant within each
time period. By substituting Vxy(t) = 0 and Vz(t) = 0 into
(24), we obtain the power consumption for hovering status
as EuFly(t) = (P0 +P1)τ, which is a ﬁnite value depending
on the aircraft weight, air density, and rotor disc area, etc.
Since the UA V maneuvering duration accounts for only a
small portion of the total operation time, the additional/reduced
energy consumption caused by UA V acceleration/deceleration
can be ignored [28]. Since the UA V’s own power is limited, the
total energy consumption of the UA V should satisfy equation
T∑
t=1
(EuISAC (t) +EuFly (t))≤Emax. (25)
F . Problem F ormulation
1) Problem Description of UA V Deployment Optimization:
In this section, we jointly optimize the UA V deployment
position and UA V beamforming with the aim of maximizing
the communication capacity under the energy consumption
constraints of the UA V , and the problem can be expressed
as:
P1 : Max
x,y,h,Gisac
Csum (26a)
Tdownu,n (t)≥xu,n(t)·Tmin,T flexu,n ≥xu,n(t)·Tmin
Tupu,n(t)≥xu,n(t)·Tmin,∀t∈T,u ∈U,n∈N (26b)
Rdownu,n (t)≤xu,n(t)·Rmax,Rupu,n(t)≤xu,n(t)·Rmax
(26c)
I(Θ) = 2(σsm)2
MU−1∑
k=0
(∂Re(ysk)
∂Θ
∂Re(ysk)
∂Θ′ + ∂Im(ysk)∂Θ ∂Im(ysk)∂Θ′ ) Θ, (16)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT BEAMFORMING AND UA V DEPLOYMENT OPTIMIZATION 17671
N∑
n=1
Bupn +
U∑
u=1
Bdownu ≤B (26d)
N∑
n=1
xu,n(t)≤ 1,∀u∈U,n∈N,t∈T (26e)
Cn(t)≥Cmin,∀t∈T,u ∈U (26f)
CRBud≤CRBud,min,CRB uφ≤CRBuφ,min (26g)
T∑
t=1
(EuISAC (t) +EuFly (t))≤Emax (26h)
du,n(t) =
√
((yu(t)− ˆyn(t))2 + (xu(t)− ˆxn(t))2)≤Rcov
(26i)
du,min(t) =
√
((yu(t + 1)−yu(t))2+(xu(t + 1)−xu(t))2)
≤Vxy,max·τ,∀u∈U,t∈T (26j)√
((hu(t + 1)−hu(t))2≤Vz,max·τ,∀t∈T,u ∈U (26k)
Hmin≤hu(t)≤Hmax,∀t∈T,u ∈U (26l)
vn,min≤vn(t)≤vn,max,∀t∈T (26m)
The constraints (26b) ensure the rational allocation of
time resources in each time slot. Constraint (26c) ensures
that the uplink and downlink communication rates between
the UA V and vehicles must be less than or equal to the
maximum achievable communication rate Rmax. Constraint
(26d) indicates that the total spectrum resources do not exceed
the maximum value B. Constraint (26e) ensures that vehicle
users can ofﬂoad tasks to at most one UA V in each time
slot. Constraint (26f) ensures that the UA V’s communication
capacity is not less than a minimum value Cmin. Constraint
(26g) indicates that the CRB of angle and distance must be
less than the minimum tolerable sensing accuracy. Constraint
(26h) ensures that the sum of the UA V’s energy consumption
does not exceed the maximum value of the UA V’s battery
capacity. Constraint (26i) ensures that the horizontal distance
between the vehicle and the UA V does not exceed the UA V’s
signal coverage radius. Constraints (26j) and (26k) ensures that
the distance the UA V ﬂies within a time slot is not less than
a minimum value du,min and does not exceed the maximum
valueVxy,max·τ. Constraint (26l) ensures the UA V’s minimum
and maximum ﬂight heights. Constraint (26m) ensures that the
vehicle’s driving speed is within a certain range.
IV. P ROBLEM SOLUTION AND ALGORITHM DESCRIPTION
A. Outline of Proposed Solution
In problem P1, the objective function involves the coupling
of four optimization variables, namely the UA V position and
the beamforming vector, denoted as ( x, y, h, w). To tackle
problem P1, we exploit the BCD method to maximize the
objective function by alternately optimizing different groups
of variables while keeping the others ﬁxed [29]. To better
reveal the block-wise structure of problem P1, we deﬁne
z1 = {x,y,h}, z2 = {w}. Then, problem P1 can be
rewritten as max
z1,z2
Csum(z1, z2), where z1 = {x,y,h} and
z2 = {w} denote the corresponding optimization variable
sets. Speciﬁcally, this paper obtains the optimal solution of
the original problem P1 by solving the following two sub-
problems. Optimize x, y, h under the given feasible w,
optimize w under the given feasible x, y, h.
B. The Optimization Method for UA V Deployment
Given the UA V beamforming scheme, the UA V deployment
location subproblem is addressed. The ﬁrst optimization sub-
problem of problem P1 can be expressed:
P2 : Max
x,y,h
Csum (27a)
s.t. (26e)− (26f), (26i)− (26m). (27b)
To address the NP-hard UA V deployment problem, this
paper employs a hybrid SSA integrated with refracted
Opposition-Based Learning (OBL) and SCA for multi-UA V
deployment. Refracted Opposition-Based Learning improves
population initialization, while SCA enhances local search
performance.
1) Three-Dimensional Initialization of UA V Positions via
Refracted OBL: In this study, each candidate position of UA V
u is represented by a sparrow in a three-dimensional space,
and OBL combined with the refraction principle is introduced
to improve population initialization and enhance diversity and
global search capability.
(xu,yu,hu)∗ =(xmax +xmin2 + xmax +xmin2rϱ − xurϱ,
ymax +ymin
2 + ymax +ymin2rϱ − yurϱ,
hmax +hmin
2 + hmax +hmin2rϱ − hurϱ), (28)
where ϱ and r are the scaling factor and refractive index,
respectively, which help enhance population diversity and
global search capability.
2) Adaptive Global Search for Discoverers With Weighted
Position Updates: This paper introduces an adaptive weighting
factor λ to balance global and local searches. The position
update formulas for discoverers are shown:
(xt+1u ,yt+1u ,ht+1u )
=
{
λ· (xtu,ytu,htu)·exp( −tαssa×itermax),R 2 <ST
(1−λ)· (xtu,ytu,htu),R 2≥ST
(29)
λ = e− 1
0.2 +e− 1itermax ·cos
( π·t
2·itermax
)
, (30)
whereR2 <ST indicates a safe search state, while R2≥ST
indicates danger and triggers movement to a new safe area.
assa is a positive control parameter for the discoverer update.
3) F ollowers’ Position Update Optimization Using SCSA:
To reduce the risk of local optima and preserve population
diversity, the Sine-Cosine Search Algorithm (SCSA) is intro-
duced to optimize the followers’ update formulas. The position
update formula for followers can be derived as:
(xt+1u ,yt+1u ,ht+1u ) = AS,
AS =
{
ωS(0xtu,ytu,htu) + BS− (xtu,ytu,htu)|,r 4 < 0.5
ωS(xtu,ytu,htu) + CS− (xtu,ytu,htu)|,r 4≥ 0.5
BS =r1sin(r2)|r3(xtbest,u,ytbest,u,htbest,u),
CS =r1cos(r2)|r3(xtbest,u,ytbest,u,htbest,u), (31)
where (xtbest,u,ytbest,u,htbest,u) represents the current global
best position. The parameters r1, r2, r3, and r4 control the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

17672 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
step amplitude, movement distance, inﬂuence of the best indi-
vidual, and switching between sine and cosine components,
respectively.r1 is deﬁned as:
r1 =
(
1−
( t
itermax
)χ
ssa
) 1χssa
, (32)
whereχssa is an adjustment factor with χssa > 1. In addition,
ωS is a nonlinear weighting factor given by:
ωS = e
t
itermax− 1
e− 1 , (33)
where e denotes the natural constant.
4) Vigilant Escape Strategy to Avoid Local Optima: To
avoid local optima, some individuals are selected as vigilant
individuals and quickly move to safe areas. The position
update for vigilant individuals is given by:
(xt+1u ,yt+1u ,ht+1u )
=
{
(xtbest,u,ytbest,u,htbest,u) +ASSA,fu⁄=fb
(xtu,ytu,htu) +BSSA,fu =fb
ASSA =|(xtu,ytu,htu)− (xtbest,u,ytbest,u,htbest,u)|,
BSSA =
(|(xtu,ytu,htu)− (xtworst,u,ytworst,u,htworst,u)|
|fu−fw|
)
.
(34)
The numbers of discoverers and vigilant individuals are
denoted by PD and SD, respectively. To reduce the impact
of UA V ﬂight time on service continuity, the single movement
distance of each UA V is limited so that position adjustment
can be completed within one time slot.
C. Beamforming Optimization
Given the UA V deployment location scenario, solve the
UA V beamforming subproblem. The second optimization sub-
problem of problem P1 can be expressed:
P3 : Max
ω
Csum (35a)
s.t. (26f), (26h) (35b)
Since Cn in the constraint is non-convex with respect to
ω, the SCA technique is employed to solve this subproblem
P3. First, by applying Taylor series expansion to Cn, Cn is
converted into the difference of two logarithmic functions,
speciﬁcally:
Cn =
N∑
n=1
T∑
t=1
xu,n(t)log2
(
1 +
‖‖ωu,nHcu,nsu,n‖‖2
(σcm)2
)
=C1u,n−C2u,n, (36)
where
C1u,n =log2
( U∑
u=1
‖‖ωu,nHcu,nsu,n‖‖2 + (σcm)2
)
,
C2u,n = (σcm)2. (37)
Since C2u,n is a concave function with respect to‖‖ωu,jHcu,nsu,j‖‖2 and the ﬁrst order Taylor expansion of a
concave function at any point is its global upper bound, the
global upper bound of C2u,n at the kth iteration is
Ck2u,n = (σcm)2 +
∑N
j,j⁄=n
‖‖Hcu,n(ωu,jsu,j−ωu,nsu,n)‖‖2
ln2((σcm)2) .(38)
Algorithm 1 Multi-UA V Deployment Algorithm Based on
Improved SSA
Input: Sparrow setu ={1, 2,··· ,U}, Number of discoverers
PD , Number of vigilantes SD, Maximum number of itera-
tions itermax, Current number of iterations t, Beamforming
strategies for UA VΩ
Output: Current global best position Q, Global optimal
individual ﬁtness value fb
1: Initialize the initial positions of n ground users
2: Initialize UA V positions. Calculate the initial ﬂight delay
∆t0 based on Equation (3)
3: Predict the position of the vehicle at t + ∆t0
4: Generate refractive reverse UA V position (xtu,ytu,htu)
5: while t<iter max do
6: for each vehicle n do
7: Update the velocity in real-time (vn,x(t),vn,y(t))
8: Calculate the intended moving distance of the UA V
as du,m =‖(xu(t + 1)−xu(t),yu(t + 1)−yu(t))‖
9: Calculate the new ﬂight delay as ∆tnew =
du,m/Vxy,max
10: Predict the position of the vehicle at time t+∆tnew
based on Equation (2)
11: end for
12: Calculate and rank the ﬁtness values of all UA Vs in
the current population
13: Selection of the optimal individual with the highest
ﬁtness value and the worst individual with the lowest
ﬁtness value
14: fori = 1 :PD do
15: Updated discoverers position based on
Equation (29)
16: end for
17: fori =PD + 1 :U do
18: Updated followers position based on Equation (31)
19: end for
20: fori = 1 :SD do
21: Updated vigilantes position based on Equation (34)
22: end for
23: Get the current position and maximum ﬁtness value
24: if Current position > previous position then
25: Update the optimal position
26: end if
27: t =t + 1
28: end while
29: returnQ, fb
For a given arbitraryωu,n, it is constant thatCku,n =C1u,n−
Ck2u,n≤C1u,n−C2u,n, so subproblem P3 can be transformed
into subproblem P3.1
P3.1 : Max
ω
Csum (39a)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT BEAMFORMING AND UA V DEPLOYMENT OPTIMIZATION 17673
Algorithm 2 Beamforming Optimization Algorithm
Input: UA V locationQ, Maximum number of iterations Imax
Output: Beamforming strategies for UA V Ω
1: Initialize the number of iterations i = 0
2: fori≤Imax do
3: The CVX method is utilized to solve subproblem P3.1
to obtain ωiu,n
4: i =i + 1
5: end for
6: Updating the UA V beamforming strategies Ω
7: return Ω
s.t. C1u,n(t)−Ck2u,n(t)≥Cmin,∀u∈U,t∈T
(39b)
(26h) (39c)
subproblem P3.1 is a convex optimization problem that can
be solved directly using the CVX Convex Optimization tool
in MATLAB. Algorithm 2 shows the pseudo-code ﬂow.
Algorithm 3 Joint Optimization Algorithm for UA V Deploy-
ment and Beamforming Based on BCD
Input: UA V set u = {1, 2,··· ,U}, user vehicle n =
{1, 2,··· ,N}, Maximum number of iterations KBCDmax , Con-
vergence accuracy δconv, Range of UA V deployment X×
Y×H, UA V ground service range radiusRcov, slot length τ,
timeslot set T ,
Output: The optimal Csum
1: Initialize system state, the number of iterations k = 0 ,
Ω0, Q0
2: while
⏐⏐Ck+1sum−Cksum⏐⏐≥δconv and k≤KBCDmax do
3: Given Ωk, calculate the deployment position Qk+1 of
the UA V .
4: Given Qk+1, calculate the beamforming strategy Ωk+1
for the UA V .
5: Calculate Ck+1sum based on{Qk+1, Ωk+1}
6: k =k + 1
7: end while
8: returnCsum
D. Block Coordinate Descent Method
The BCD algorithm is widely used for solving multi-
variable block optimization problems. In each iteration, it
optimizes one variable block while ﬁxing the others, thereby
decomposing the original non-convex problem into more
tractable subproblems. Speciﬁcally, according to Algorithm 1,
given the beamforming strategy Ω, it outputs the UA V deploy-
ment positions Q and the global optimal individual ﬁtness
valuefb. Then, based on Algorithm 2, given the UA V deploy-
ment positions Q, it outputs the beamforming strategy Ω.
Finally, Algorithm 3 iteratively updates Q and Ω until con-
vergence, and calculates the optimal communication capacity
Csum based on these two variables.
E. Convergence Analysis and Algorithm Complexity
Assume that C0sum =obj(Q0, Ω0) is the objective value of
the initial solution in Algorithm 3, and thatCsum =obj(Q, Ω)
is the objective value of the solution returned after KBCDmax
iterations.
Theorem 1: Algorithm 3 creates a sequence of feasible
solutions with a non-decreasing objective value over iterations.
As a result, the objective value sequence converges to a ﬁnite
limit.
Proof: According to the pseudo-code of Algorithm 3, based
on the given UA V deployment scheme{Qk}, the beamforming
scheme {Ωk+1} is obtained, then the following inequality
holds
obj(Qk, Ωk)≤obj(Qk, Ωk+1), (40)
based on the given beamforming scheme {Ωk+1}, the UA V
deployment scheme {Qk+1} is obtained, then the following
inequality holds
obj(Qk, Ωk+1)≤obj(Qk+1, Ωk+1), (41)
based on the above analysis, it can be obtained that
obj(Qk, Ωk)≤obj(Qk+1, Ωk+1). (42)
Therefore, (40)–(42) imply that the objective value gener-
ated by Algorithm 3 is non-decreasing over the iterations.
Meanwhile, the objective value is upper-bounded because
the transmit power, bandwidth, number of UA Vs, number of
vehicles, and number of time slots are ﬁnite, while the UA V
deployment region is also bounded and the noise power is
positive. Hence, the achievable communication capacity of
each UA V–vehicle link is ﬁnite, and the sum communication
capacity Csum is upper-bounded by a ﬁnite value.
Thus, the objective value sequence generated by
Algorithm 3 is non-decreasing and upper-bounded. According
to the convergence theorem, it converges to a ﬁnite limit.
The block coordinate descent algorithm proposed in this
paper consists of three algorithms. The UA V deployment
algorithm uses RS-SSA, and the time complexity depends on
the dimensionality of the problem, the size of the population,
the number of iterations, etc. In this paper, since each sparrow
represents a candidate deployment position for a UA V , the
overall size of the population is exactly equal to the total
number of UA Vs, denoted as U, the maximum number of
iterations is itermax, and the dimension is 3. Then the time
complexity of the proposed SSA based on the refractive
backward learning and sine cosine algorithms can be expressed
asO(3×U×itermax). The time complexity of beamforming
optimization algorithm isO
(
Imax (UNMU)3
)
. Therefore the
time complexity of theblock coordinate descent algorithm is
O
(
KBCDmax (3×U×itermax +Imax(UNMU)3)).
V. S IMULATION RESULTS
A. Outline of The Experiment
We design a simulation experiment framework. Speciﬁcally,
Python 3.9.7 is used with Veins to construct the simulation
environment, where the performance of the proposed UA V
deployment algorithm is veriﬁed and compared. In detail,
we select the trafﬁc conditions around Wuhan University of
Technology within a spatial scope of 1000m×1000m×100m
[10]. The UA V-assisted VEC simulation scenario designed
is an air-ground cooperative scenario, with the simulation
environment built using Python in conjunction with Veins,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

17674 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE I
LIST OF MAIN NOTATIONS
OMNeT++, and SUMO [1], [30]. Due to the limitations of
civilian routers in reproducing the radio frequency characteris-
tics and performance required for UA V monitoring, numerical
simulation is employed to verify key detection parameters
and channel characteristics. To comprehensively assess the
effectiveness and robustness of the proposed UA V deployment
algorithm, we conduct three types of experiments: iterative
experiments, scalability experiments, and ablation studies.
B. Simulation Environment Design
We ﬁrst obtain an OSM ﬁle from OpenStreetMap, which
provides a map of a real-world urban area. Using SUMO
tools, we then process this OSM ﬁle to generate SUMO
simulation ﬁles. In the simulation environment, SUMO com-
municates with Veins via Traci to generate simulation data,
while Python is used to process and analyze these data.
This environment serves to generate vehicle movement tra-
jectories and provide dynamic data inputs consistent with
real-world trafﬁc environments.Since most existing studies on
ISAC are based on numerical simulations, our simulation
design similarly adopts a simulation-based approach as in [10],
[11], and [15]. The speciﬁc design parameters are shown in
Table II.
C. Baseline Algorithms and Adaptation for Fair Comparison
In order to analyze the performance of the proposed
multi-UA V deployment algorithm in the ISAC-enhanced UA V-
assisted VEC environment, we compare it with the trajectory
planning and passive beamforming-based (TPaPBA) UA V
deployment algorithm [4], the DDPG algorithm [34], and the
TABLE II
SIMULATION PARAMETER TABLE
PSO algorithm [35]. To ensure a fair comparison, the baseline
algorithms are adapted as follows:
• TPaPBA-based UA V deployment algorithm:The UA V
energy consumption model in (24) is adopted, where the
total energy includes both communication and sensing
components, and the sensing energy is incorporated into
the optimization objective as a constraint.
• DDPG-based UA V deployment algorithm: The state
space is extended to include UA V positions and sensing-
related variables, the action space is redesigned to jointly
optimize deployment and beamforming, and the reward
function is modiﬁed to incorporate sensing energy for
consistency with the ISAC model.
• PSO-based UA V deployment algorithm: The particle
representation is deﬁned by UA V deployment and beam-
forming variables, and the ﬁtness function is modiﬁed
to align with the proposed objective, including both
communication and sensing energy consumption.
D. Performance Metrics
This paper investigates the impact of the number of vehicles,
the number of iterations and the number of UA V on four
metrics: average communication capacity, average coverage,
Radar Mutual Information (RMI) and average UA V energy
consumption in UA V deployment algorithms.
• Average communication capacity :
C = Csum
T (43)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT BEAMFORMING AND UA V DEPLOYMENT OPTIMIZATION 17675
TABLE III
BENCHMARK TEST FUNCTIONS
• Average coverage: Average coverage refers to the propor-
tion of vehicles that a UA V can effectively cover within
a certain area, as shown in
¯Ncov = 1T
T∑
t=1
(∑U
u=1
∑N
n=1xu,n(t)
N
)
. (44)
• Average UA V energy consumption: This factor reﬂects the
performance of the proposed algorithm, as shown in
EUA V= 1U·T
U∑
u=1
T∑
t=1
(
EuISAC(t) +EuFly(t)) (45)
• Average Radar Mutual Information :Average RMI is
deﬁned as the average of the mutual information about
targets among all UA Vs within each time slot. From an
information-theoretic perspective, the radar mutual infor-
mation quantiﬁes the amount of target-related information
contained within the radar return signals [36], as shown
in
Rs = 1T·U
T∑
t=1
U∑
u=1
ηu(t)·Wsu(t)·ln (1 +γsu(t)), (46)
where ηu(t) denotes the ISAC time-splitting ratio of
UA Vu at time slot t, determining the temporal resource
allocation between sensing and communication tasks;
Wsu(t) represents the sensing bandwidth, which governs
the frequency-domain capacity for radar detection; and
γsu(t) stands for the sensing signal-to-interference-plus-
noise ratio, accounting for both the target’s channel power
gain and the mutual interference inherently present.
E. Simulation Results
1) Iteration and Location Simulation: First, four bench-
mark test functions are used to conduct iterative tests and
compare convergence values between the UA V deployment
algorithm based on ISAC proposed in this paper and the
traditional SSA. Table III provides the formulas and search
ranges for the four benchmark test functions, which have been
widely used to test the feasibility, effectiveness, and stability
of algorithms.
Fig. 3 shows the convergence curves for the four test
functions, F1–F4. From the ﬁgure, the proposed algorithm
not only converges more quickly and smoothly across all
functions but also consistently reaches the theoretical optimal
value of 0, whereas SSA fails to do so in any case. This
performance boost is mainly attributed to the introduction
of refracted OBL, which enhances exploration and prevents
premature convergence.
Fig. 3. Convergence curves under different test functions.
Fig. 4. UA V deployment diagram.
As shown in Fig. 4(a), during a speciﬁc time slot, 50
vehicle users are randomly distributed within a 1000m×
1000m× 100m ground area, with ﬁve UA Vs deployed in
the three-dimensional space. Blue represents the vehicles, and
red represents the UA Vs. To better visualize and analyze
the coverage optimization strategy without overcomplicating
the trajectory visualization, Fig. 4(b) focuses on the ﬂight
path of a randomly selected UA V within a speciﬁc time
period, as well as its compliance with deployment con-
straints, so as to ensure that its trajectory characteristics
can fully reﬂect the overall operational behavior of all ﬁve
UA Vs.
The number of iterations is set from 100 to 500, with
performance metrics recorded every 100 iterations while
other variables are kept constant. As shown in Fig. 5, the
average communication capacity, coverage rate, and radar
mutual information gradually converge as the number of
iterations increases. The proposed algorithm converges within
300–400 iterations, whereas the three baseline algorithms
require 400–500 iterations, indicating faster convergence and
better performance. This result is mainly attributed to the
proposed algorithm, which effectively addresses the strong
coupling among variables through the joint optimization of
UA V deployment and beamforming.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

17676 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 5. The inﬂuence of iteration times on simulation results.
Fig. 6. Parameter Sensitivity Analysis: (a) The impact of weight γ, (b) The
impact of weight γε.
2) Parameter Sensitivity Analysis: Fig. 6(a) illustrates the
sensitivity of average communication capacity and ISAC
utility to the power split factor γ. Communication capacity
increases monotonically with γ, while ISAC utility exhibits
a non-monotonic behavior with a peak at an intermediate
γ. Smaller γ favors sensing, whereas larger γ prioritizes
communication. This result mainly arises from the proposed
joint optimization algorithm, which gives higher priority to the
communication utility during iterative resource allocation. The
selected operating point lies on the communication-oriented
side of this trade-off. The selected operating point lies on
the communication-oriented side of this trade-off. Fig. 6(b)
shows the effect of beam powerγε on energy consumption and
radar mutual information. Energy consumption increases with
γε, while radar mutual information improves with diminishing
returns. The chosen operating point achieves a balance where
further power increases provide limited sensing gains at a
signiﬁcantly higher energy cost, reﬂecting an effective trade-
off between sensing performance and energy efﬁciency.
3) Scalability: In this environment, variations in the num-
ber of vehicles can impact the average communication
capacity, average coverage rate, and average UA V energy
consumption. In Fig. 7, the average communication capacity
decreases as the number of vehicles increases: with more
vehicles sharing the same UA V resources, per-link bandwidth
and power allocations shrink, lowering per-vehicle rates. The
result mainly arises from the proposed joint optimization
algorithm, which it adaptively updates UA V deployment and
Fig. 7. The inﬂuence of vehicle quantity on simulationresults.
Fig. 8. The inﬂuence of UA V quantity on simulation results.
beamforming under dense vehicular trafﬁc, the increasingly
limited communication and sensing resources still cause per-
formance degradation and higher UA V energy consumption.
The average coverage rate declines with vehicle density.
Between 10 and 20 vehicles there may be slight ﬂuctuations
due to uneven vehicle clustering, but beyond 20 the coverage
drops more steadily. At 30 vehicles, our method provides a
9.6%, 20.1% and 4.4% higher coverage rate than DDPG, PSO
and TPaPBA, respectively.
In Fig. 8, the average communication capacity and coverage
rate both increase with the number of UA Vs, since additional
UA Vs reduce the communication load per UA V and expand
the service region. When the number of UA Vs increases from
3 to 5, the coverage gains of the four algorithms are 6.1%,
6.1%, 7.2%, and 5.2%, respectively. This performance gain
is primarily driven by the reduction in average propagation
distance and the increased probability of establishing LoS
links, which effectively mitigates path loss and enhances the
SINR for vehicular users. Across different deployment scales,
the proposed algorithm improves the average coverage rate by
10.51% over the baseline algorithms. Overall, the proposed
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT BEAMFORMING AND UA V DEPLOYMENT OPTIMIZATION 17677
Fig. 9. Purpose of the ablation study: To investigate the performance of joint
optimization and the contribution of the ISAC module.
Fig. 10. Impact of the number of UA Vs under inter-UA V interference.
algorithm achieves an average 19.83% reduction in UA V
energy consumption compared with the baseline algorithms.
4) Ablation Study: We design ablation experiments under
two scenarios. The ﬁrst adopts a ﬁxed optimization sequence
instead of alternating joint optimization, while the second
replaces ISAC with the conventional separated communication
and sensing scheme. In Fig. 9(a), removing the alternat-
ing joint optimization reduces the communication capability
and RMI by 2.8% and 10%, respectively, indicating that
ﬁxed-sequence optimization weakens the synergy among cou-
pled variables. Removing the sensing module may slightly
improve communication performance, whereas ﬁxing the
sensing–communication allocation ratio at 0.5 degrades com-
munication capability and increases system cost.
5) The Impact of Interference Among UA Vs: In dense multi-
UA V environments, we further consider interference among
UA Vs, which is characterized by:
Iinteru,n =
U∑
u′⁄=u
xu′,n(t)‖‖ωu′,nHcu′,nsu′,n‖‖2. (47)
where Iinteru,n denotes the aggregated residual interference
among UA Vs power received by vehicle n when it is served
by UA Vu, and u′⁄= u is the index of an interfering UA V .
The SINR is given by:
SINR′ =
‖‖ωu,nHcu,nsu,n‖‖2
(σcn)2 +Iinteru,n . (48)
In Fig. 10, we conduct a simulation in which interference
among UA Vs is considered. Different from Fig. 8(a), the aver-
age communication capacity ﬁrst increases and then begins
to decay after reaching the optimal point. This is because
adding UA Vs initially reduces the service load of each UA V ,
thereby improving the communication service capability for
UA Vs. However, when the number of UA Vs reaches a certain
level, the interference from other UA Vs also becomes stronger,
which overwhelms the desired communication gain and thus
degrades the average communication capacity.
Fig. 11. The impact of Rician fading factor.
6) The Impact of Rician Fading Factor: In Fig. 11, we
investigate communication capacity under different Rician
fading factors. K = 0 dB indicates that the LoS component
and NLoS paths have comparable power, under which the
received signal envelope distribution is modeled as Rician
fading for a less LoS condition. The average communication
capacity underK = 0 dB is lower than that underK = 15 dB,
because this scenario leads to a lower effective channel gain.
VI. C ONCLUSION AND FUTURE WORK
In this article, we investigate the joint optimization of
UA V deployment and beamforming in an ISAC-enhanced
UA V-assisted VEC system. We formulate the problem as
a non-convex optimization framework aiming to maxi-
mize communication capacity under UA V energy constraints.
The proposed approach effectively captures the coupling
between deployment and beamforming decisions and achieves
signiﬁcant performance gains. Future work could explore
collaborative optimization among UA Vs and vehicles to further
improve service quality and resource utilization efﬁciency.
REFERENCES
[1] Z. Lv, D. Chen, and Q. Wang, “Diversiﬁed technologies in Internet of
Vehicles under intelligent edge computing,” IEEE Trans. Intell. Transp.
Syst., vol. 22, no. 4, pp. 2048–2059, Apr. 2021.
[2] J. Karedal, N. Czink, A. Paier, F. Tufvesson, and A. F. Molisch, “Path
loss modelling for vehicle-to-vehicle communications,” IEEE Trans.
V eh. Technol., vol. 60, no. 1, pp. 323–328, Jan. 2011.
[3] Q. Zhang, X. Wang, Z. Li, and Z. Wei, “Design and performance
evaluation of joint sensing and communication integrated system for 5G
mmWave enabled CA Vs,”IEEE J. Sel. Topics Signal Process. , vol. 15,
no. 6, pp. 1500–1514, Nov. 2021.
[4] M. Asim, M. ELAffendi, and A. A. A. El-Latif, “Multi-IRS and multi-
UA V-assisted MEC system for 5G/6G networks: Efﬁcient joint trajectory
optimization and passive beamforming framework,” IEEE Trans. Intell.
Transp. Syst., vol. 24, no. 4, pp. 4553–4564, Apr. 2023.
[5] R. Zeng, C. Jiang, X. Wang, and B. Li, “A joint secure mechanism of
multi-task learning for a UA V team under FDI attacks,” IEEE Trans.
Mobile Comput. , vol. 24, no. 8, pp. 7345–7359, Aug. 2025.
[6] Y . Zhuo and Z. Wang, “Performance analysis of ISAC system under
correlated communication-sensing channel,” IEEE Trans. V eh. Technol.,
vol. 72, no. 12, pp. 16823–16827, Dec. 2023.
[7] X. Dai, Z. Xiao, H. Jiang, and J. C. S. Lui, “UA V-assisted task ofﬂoading
in vehicular edge computing networks,” IEEE Trans. Mobile Comput. ,
vol. 23, no. 4, pp. 2520–2534, Apr. 2024.
[8] Z. Chen, H. Zheng, J. Zhang, X. Zheng, and C. Rong, “Joint computation
ofﬂoading and deployment optimization in multi-UA V-enabled MEC
systems,” Peer Peer Netw. Appl., vol. 15, no. 1, pp. 194–205, Jan. 2022.
[9] H. Hao, C. Xu, W. Zhang, S. Yang, and G. Muntean, “Joint task
ofﬂoading, resource allocation, and trajectory design for multi-UA V
cooperative edge computing with task priority,” IEEE Trans. Mobile
Comput., vol. 23, no. 9, pp. 8649–8663, Sep. 2024.
[10] D. Deng, W. Zhou, X. Li, D. B. da Costa, D. W. K. Ng, and
A. Nallanathan, “Joint beamforming and UA V trajectory optimization
for covert communications in ISAC networks,” IEEE Trans. Wireless
Commun., vol. 24, no. 2, pp. 1016–1030, Feb. 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply. 

17678 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[11] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[12] S. Zhang et al., “Joint beamforming optimization for active STAR-RIS-
assisted ISAC systems,” IEEE Trans. Wireless Commun., vol. 23, no. 11,
pp. 15888–15902, Nov. 2024.
[13] W. Jiang et al., “Improve sensing and communication performance of
UA V via integrated sensing and communication,” in Proc. IEEE 21st
Int. Conf. Commun. Technol. (ICCT) , Oct. 2021, pp. 644–648.
[14] L. Chen, Z. Wang, J. Jiang, Y . Chen, and F. R. Yu, “Full-duplex SIC
design and power allocation for dual-functional radar-communication
systems,” IEEE Wireless Commun. Lett. , vol. 12, no. 2, pp. 252–256,
Feb. 2023.
[15] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[16] Z. Liu, X. Liu, Y . Liu, V . C. M. Leung, and T. S. Durrani, “UA V assisted
integrated sensing and communications for Internet of Things: 3D
trajectory optimization and resource allocation,” IEEE Trans. Wireless
Commun., vol. 23, no. 8, pp. 8654–8667, Aug. 2024.
[17] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for
low-altitude economy: Coordinated transmit beamforming and UA V tra-
jectory design,” IEEE Trans. Commun. , vol. 73, no. 8, pp. 5832–5847,
Aug. 2025.
[18] Z. Wang, L. Xu, L. Hou, R. Li, and L. Wang, “UA V-assisted emergency
integrated sensing and communication networks: A CNN-based rapid
deployment approach,” 2024, arXiv:2401.07001.
[19] T. Kimura and M. Ogura, “Distributed collaborative 3D-deployment of
UA V base stations for on-demand coverage,” in Proc. IEEE INFOCOM
Conf. Comput. Commun. , Jul. 2020, pp. 1748–1757.
[20] Q. Wu, Y . Zeng, and R. Zhang, “Joint trajectory and communication
design for UA V-enabled multiple access,” in Proc. IEEE Global Com-
mun. Conf. , Dec. 2017, pp. 1–6.
[21] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li,
“Throughput maximization for UA V-enabled integrated periodic sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 1,
pp. 671–687, Jan. 2023.
[22] K. Boutiba, M. Bagaa, and A. Ksentini, “Multi-agent deep reinforcement
learning to enable dynamic TDD in a multi-cell environment,” IEEE
Trans. Mobile Comput. , vol. 23, no. 5, pp. 6163–6177, May 2024.
[23] S. Krauss, “Microscopic modeling of trafﬁc ﬂow: Investigation of
collision free vehicle dynamics,” DLR Deutsches Zentrum Fuer Luft-
und Raumfahrt e.V ., Koeln, Germany, Tech. Rep. DLR-FB-98-08, Apr.
1998.
[24] Y . Zeng, Q. Wu, and R. Zhang, “Accessing from the sky: A tutorial
on UA V communications for 5G and beyond,” Proc. IEEE , vol. 107,
no. 12, pp. 2327–2375, Dec. 2019.
[25] L. Zhang, A. Celik, S. Dang, and B. Shihada, “Energy-efﬁcient trajectory
optimization for UA V-assisted IoT networks,” IEEE Trans. Mobile
Comput., vol. 21, no. 12, pp. 4323–4337, Dec. 2022.
[26] S. M. Kay, Fundamentals of Statistical Signal Processing: Estimation
Theory, vol. 1. Englewood Cliffs, NJ, USA: Prentice-Hall, 1993.
[27] S. Mandelli, M. Henninger, and J. Du, “Sampling and reconstructing
angular domains with uniform arrays,” IEEE Trans. Wireless Commun. ,
vol. 22, no. 6, pp. 3628–3642, Jun. 2023.
[28] Y . Zeng, J. Xu, and R. Zhang, “Energy minimization for wireless
communication with rotary-wing UA V ,”IEEE Trans. Wireless Commun.,
vol. 18, no. 4, pp. 2329–2345, Apr. 2019.
[29] N. Zhao et al., “Joint trajectory and precoding optimization for UA V-
assisted NOMA networks,” IEEE Trans. Commun. , vol. 67, no. 5,
pp. 3723–3735, May 2019.
[30] L. Wei, J. Cui, Y . Xu, J. Cheng, and H. Zhong, “Secure and lightweight
conditional privacy-preserving authentication for securing trafﬁc emer-
gency messages in V ANETs,” IEEE Trans. Inf. F orensics Security ,
vol. 16, pp. 1681–1695, 2021.
[31] Y . Liu, K. Xiong, Y . Lu, Q. Ni, P. Fan, and K. B. Letaief, “UA V-aided
wireless power transfer and data collection in Rician fading,” IEEE
J. Sel. Areas Commun. , vol. 39, no. 10, pp. 3097–3113, Oct. 2021.
[32] A. Gupta, A. Trivedi, and B. Prasad, “B-GWO based multi-UA V
deployment and power allocation in NOMA assisted wireless networks,”
Wireless Netw., vol. 28, no. 7, pp. 3199–3211, Oct. 2022.
[33] J. Xue and B. Shen, “A novel swarm intelligence optimization approach:
Sparrow search algorithm,” Syst. Sci. Control Eng. , vol. 8, no. 1,
pp. 22–34, Jan. 2020.
[34] A. S. Abdalla and V . Marojevic, “Multi-agent learning for secure wire-
less access from UA Vs with limited energy resources,” IEEE Internet
Things J., vol. 10, no. 24, pp. 22356–22370, 2023.
[35] Z. Yuheng, Z. Liyan, and L. Chunpeng, “3-D deployment optimization
of UA Vs based on particle swarm algorithm,” in Proc. IEEE 19th Int.
Conf. Commun. Technol. (ICCT) , Oct. 2019, pp. 954–957.
[36] X. Liu, W. Yang, L. Li, Z. Liu, Y . Liu, and F. Li, “UA V assisted
integrated sensing and communication for mobile vehicles,” IEEE Trans.
Intell. Transp. Syst. , vol. 26, no. 11, pp. 21335–21339, Nov. 2025.
Chunlin Li received the B.S. and M.Sc. degrees
in computer science from Wuhan University of
Technology (WUT), China, in 1996 and 2000,
respectively, and the Ph.D. degree in computer soft-
ware and theory from the Huazhong University of
Science and Technology (HUST), Wuhan, China, in
2003. She is currently a Professor and the Ph.D.
Tutor of computer science at WUT. She has pub-
lished more than 60 technical articles. Her research
interests include high-performance computing, UA V
communications, and the Internet of Things (IoT).
Wenhao Wu is currently pursuing the M.E. degree
with the School of Computer Science and Technol-
ogy, Wuhan University of Technology. His research
interests include cloud computing, edge computing,
and artiﬁcial intelligence.
Zhihao Zhang (Student Member, IEEE) received
the M.S. degree from Tianjin University of Tech-
nology (TUT) in 2024. He is currently pursuing
the Ph.D. degree with the School of Computer
Science and Technology, Wuhan University of Tech-
nology (WUT). His research interests include UA V
communications, the Internet of Things (IoT), deep
reinforcement learning (DRL), and mobile edge
computing (MEC).
Tianbing Ma received the M.S. degree from Anhui
University of Science and Technology, Huainan,
China, in 2005, and the Ph.D. degree from
Nanjing University of Aeronautics and Astronautics,
Nanjing, China, in 2014. Since 2016, he has been
a Professor at Anhui University of Science and
Technology. His research areas include autonomous
energy sensing, fault diagnosis, and digital twins.
Shaohua Wan (Senior Member, IEEE) received the
Ph.D. degree from the School of Computer, Wuhan
University, Wuhan, China, in 2010. He is currently
a Full Professor with the Shenzhen Institute for
Advanced Study, University of Electronic Science
and Technology of China, Shenzhen, China. From
2016 to 2017, he was a Visiting Professor with the
Department of Electrical and Computer Engineering,
Technical University of Munich, Munich, Germany.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:08:18 UTC from IEEE Xplore.  Restrictions apply.