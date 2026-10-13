---
title: "Situation-Aware Hybrid Sensing and Position Control for UAV-Assisted ISAC Systems"
zotero_key: "573TSHTV"
pdf_key: "UTIJ8MMX"
doi: "10.1109/TWC.2026.3661956"
collection: "UAV"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Situation-Aware Hybrid Sensing and Position Control for UAV-Assisted ISAC Systems — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 12197
Situation-Aware Hybrid Sensing and Position
Control for UA V-Assisted ISAC Systems
Ling Lyu
 , Member, IEEE, Qirui Luo, Yanpeng Dai
 , Member, IEEE, Nan Cheng
 , Senior Member, IEEE,
Cailian Chen
 , Senior Member, IEEE, Xinping Guan
 , Fellow, IEEE, and Xuemin Shen
 , Fellow, IEEE
Abstract—The high ﬂexibility and controllable mobility of
uncrewed aerial vehicles (UA Vs) make it possible to construct
the line-of-sight transmission link between devices in plant and
the remote center, where the channel state condition heavily
depends on the position of UA V . In this work, integrated sensing
and communication (ISAC) is adopted to simultaneously perform
position awareness and data transmission with limited radio
resources. In particular, a situation-aware hybrid sensing pattern
is proposed to reduce energy consumption and the interfer-
ence of sensing to communication. In this hybrid pattern, the
sensing function is activated on demand based on the channel
state condition that is heavily affected by the position of UA V .
Besides, the position control of UA V is performed based on the
sensing result to further improve the transmission rate. Then,
a joint optimization problem of beamforming design and power
allocation is formulated to maximize energy efﬁciency. To solve
this mixed integer nonlinear problem, the original problem is
decomposed into subproblems in Phase I and Phase II. Finally,
the golden-section based Dinkelbach algorithm and the penalty
based approximation algorithm are proposed to solve the Phase
I subproblem with the fractional objective function and rank-
one constraints. Moreover, a quadratic transform enabled joint
design of remote center beamforming and UA V transmit power
is proposed to solve the Phase II subproblem. Simulation results
verify that the proposed UA V-assisted integration of sensing,
Received 21 October 2024; revised 15 May 2025, 28 September 2025,
and 1 December 2025; accepted 3 February 2026. Date of publication
16 February 2026; date of current version 19 February 2026. This work
was supported in part by the National Natural Science Foundation of China
under Grant 62573082, Grant 62571081, and Grant 62002042; in part by the
Doctoral Research Startup Funds of Liaoning Province under Grant 2025-BS-
0216; and in part by the Joint Research Program for Science and Technology
Plan of Liaoning Province under Grant 2025-MSLH-055. The associate editor
coordinating the review of this article and approving it for publication was
Z. Liu. (Corresponding author: Yanpeng Dai.)
Ling Lyu and Yanpeng Dai are with the School of Information Science
and Technology, Dalian Maritime University, Dalian 116026, China, and
also with the State Key Laboratory of Integrated Services Networks, Xidian
University, Xi’an, Shaanxi 710071, China (e-mail: linglyu@dlmu.edu.cn;
yanpengdai@dlmu.edu.cn).
Qirui Luo is with the School of Information Science and Technology, Dalian
Maritime University, Dalian 116026, China (e-mail: luoqirui@dlmu.edu.cn).
Nan Cheng is with the State Key Laboratory of Integrated Services Net-
works and the School of Telecommunications Engineering, Xidian University,
Xi’an, Shaanxi 710071, China (e-mail: dr.nan.cheng@ieee.org).
Cailian Chen and Xinping Guan are with the State Key Laboratory of
Submarine Geoscience, the Key Laboratory for System Control and Informa-
tion Processing, Ministry of Education of China, Shanghai Key Laboratory
for Perception and Control in Industrial Network Systems, and the School of
Automation and Intelligent Sensing, Shanghai Jiao Tong University, Shanghai
200240, China (e-mail: cailianchen@sjtu.edu.cn; xpguan@sjtu.edu.cn).
Xuemin Shen is with the Department of Electrical and Computer Engi-
neering, University of Waterloo, Waterloo, ON N2L 3G1, Canada (e-mail:
sshen@uwaterloo.ca).
Digital Object Identiﬁer 10.1109/TWC.2026.3661956
communication, and control approach outperforms compared
approaches regarding data volume and energy efﬁciency.
Index Terms—UA V-assisted ISAC, situation-aware hybrid sens-
ing, beamforming design, position control, antenna-angle control.
I. I NTRODUCTION
P
ROMPTED by the development of information and com-
munication technology, a series of advanced Internet of
Things (IoT) services have been conducted, such as smart
manufacturing, smart cities, digital twins, and so on [1],
[2], and [3]. In these services, tremendous IoT devices are
deployed in plant to collect and deliver environment data to the
server for further fusion and processing [4], [5], [6]. However,
the surrounding obstacles and scatters block the signal propa-
gation, making it hard to guarantee the transmission reliability
and timeless [7], [8]. Fortunately, uncrewed aerial vehicle
(UA V) has been envisioned as a cost-effective aerial platform
to overcome the above limitations, since it has high mobility,
ﬂexibility, and controllability and can provide the strong air-
ground line-of-sight (LoS) channels [9], [10], [11]. For the
UA V-assisted communication system, the accuracy of UA V’s
position is a key index, since it heavily affects the channel
condition and then the data rate and transmission reliability
[12], [13], [14]. Therefore, it is necessary to achieve both the
position sensing and the data transmission with limited radio
resources.
Integrated sensing and communication (ISAC) technology
aims at improving the data sensing and transmission efﬁciency
by well-designing the dual-functional signals to share the
same radio resources and wireless infrastructures [15], [16],
[17]. Meng et al. [18] proposed a periodic ISAC method, in
which the UA V periodically provides communication services
to users while performing target sensing tasks. Ni et al.
[19] proposed a communication-centric waveform optimiza-
tion system, in which the base station detects radar targets
while simultaneously communicates with mobile users. The
aforementioned studies primarily focus on achieving the orig-
inal communication functionality of the system while sensing
additional targets, without fully exploring the integration and
coordination gains of combining the two functions. Moreover,
the mutual assistance between communication and sensing
functions has not been adequately explored. Currently, there
are some works focus on the integrated design approaches
for ISAC. Xiao and Zeng [20] proposed a novel full-duplex
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12198 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
(FD) ISAC scheme that utilizes the waiting time of con-
ventional pulsed radars to transmit communication signals.
Zhang et al. [21] proposed a dynamic frame structure, allowing
users to allocate a time-frequency ratio for dual sensing
and communication functions according to varying demands.
He et al. [22] extended the existing ISAC beamforming
design to a general case by considering the FD capability
for not only sensing but also communication for optimizing
the downlink and uplink transmissions. The above studies on
the integrated design approaches for ISAC primarily focus
on the periodic integration method. However, in practice,
the sensing demand is different and variable. It is necessary
to schedule the sensing functions on demand to reduce the
interference between communication and sensing. An adaptive
ISAC mechanism ﬂexibly conﬁgures the sensing duration
according to the communication demand [23]. The sensing
function adopts an event-triggered approach that senses only
when the communication requirements are not met [24].
Therefore, the on-demand scheduling of sensing functions has
not been adequately explored.
As the advantage of ISAC technology on loss-of-sight
(LoS) links, some recent studies focus on the UA V-assited
ISAC system. The existing research on UA V-assisted ISAC
systems primarily focuses on resource allocation among sens-
ing and communication [25]. UA V beamforming design and
trajectory optimization are the main research interests [26].
The prevailing solution for the joint optimization problem
is leveraging an alternating optimization mechanism [27],
[28], [29], or deep reinforcement learning mechanisms [30],
[31] to strike a balance between sensing and communication
performance. The above researches highlight the signiﬁcance
of UA V positioning, which signiﬁcantly impact sensing and
communication performance. Consequently, trajectory or posi-
tion optimization has emerged as a pivotal domain of ongoing
research. However, most works primarily focus on the inte-
gration of sensing and communication, without considering
how to use the sensing result to improve the communication
performance. Moreover, the communication channel between
UA V and the ground user is mainly dominated by the LoS
link, which will be further determined by the position of UA V
[32]. The motion control of UA V was proposed to precisely
adjust the position of UA V , ensuring optimal beam alignment
and then enhancing the channel state for an improved backhaul
rate [33]. A UA V-assisted periodic communication and sensing
approach was proposed, where the penalty-based algorithm
was utilized to maximize the achievable rate by iteratively
optimizing sensing time, user association, UA V trajectory and
beamforming vector [18]. Moreover, a dual-function multi-
UA V wireless network maximizes the network utility by jointly
optimizing UA V position, UA V transmit power, and user
association subject to the positioning accuracy constraint [34].
Therefore, for UA V-assited ISAC communication systems, it
is essential to design the beamforming and transmit power
integrating with the trajectory planning and position control,
since the transmission rate heavily depends on the position-
aware channel quality. The above studies mainly focus on the
integration of sensing and communication, however, sensing is
generally not the ultimate goal, especially for mobile devices
[35]. It is essential to study how to use the sensing result to
perform the control function to improve the communication
performance. Due to the execution of control function will
cause addition energy consumption, it is essential to investigate
the scheduling of control functions to improve the transmission
rate at low energy consumption based on sensing results [36],
[37], [38].
In this paper, we have investigated a UA V-assisted integra-
tion of sensing, communication, and control, which provides
a new option for data transmission in the industrial IoT. In
the considered system, the automatic guided vehicle (AGV)
transmits data to the remote center (RC) via the UA V , where
the channel state condition heavily depends on the position of
UA V . In order to provide a high-precision position at a low cost
of energy consumption, we investigate the integrated design of
antenna-angle control and position control together with the
situation-aware hybrid sensing pattern. The main contributions
of this paper are summarized as follows.
• The proposed situation-aware hybrid sensing pattern is
proposed to activate sensing and control functions on
demand according to the channel state condition, which
signiﬁcantly reduces the interference of sensing signals
on communication.
• The integrated design of antenna-angle control and posi-
tion control could enhance the energy efﬁciency by only
performing beam alignment at a low energy cost when
the misalignment error is moderate.
• The designed golden-section based Dinkelbach and
the penalty based successive algorithms could ensure
the sensing accuracy and mitigate the sensing-to-
communication interference. Moreover, the designed
quadratic transform based reconstructive rank-one algo-
rithm could address the problem of resource allocation
with low computational complexity.
The remainder of this paper is organized as follows. The
system model is presented in Section II. In Section III,
the UA V-assisted integration of sensing, communication and
control is presented, along with the formulation of the maximal
system energy efﬁciency problem. In Section IV, the problem
decomposition and joint design of beamforming and power
allocation are proposed to address the problem. Section V
presents numerical results to validate the UA V-assisted inte-
gration of sensing, communication and control approach and
algorithms’ performance. Finally, Section VI concludes the
paper. For the sake of clarity, the main parameters of the
notations are listed in Table I.
II. S YSTEM MODEL
We consider a UA V-assisted ISAC system as shown in
Fig. 1, in which AGV with sensors gathers sensory data and
then AGV to RC via UA V . The half-duplex UA V works in the
decode-and-forward mode, thus the transmission process from
AGV to RC compose of two phases within an ISAC frame
period T, as shown in Fig. 2. Horn antennas are deployed
on both AGV and UA V . RC is equipped with a N0-antenna
uniform linear array (ULA) for sensing and an omnidirectional
antenna for communication. Each ISAC frame consists of K
time slots, and the duration of each time slot is ∆.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12199
TABLE I
LIST OF NOTATIONS FOR MAIN PARAMETERS
• Phase I: AGV transmits sensory data to UA V . The chan-
nel state directly affects the transmission rate, which in
turn depends on the position of both AGV and UA V . Since
horn antennas are used by both AGV and UA V , smaller
position distortions would lead to larger misalignment
errors. Thus, RC periodically senses both AGV and UA V ,
and performs the beam alignment and position control
based on the sensing result.
• Phase II: UA V transmits data to RC. Omnidirectional
antenna is deployed at the RC. A large communication
rate can be obtained by UA V when the beams of the two
are aligned within a certain range. Therefore, RC senses
the position of UA V in an event-triggered mode. If the
triggering condition is satisﬁed, RC performs the beam
alignment and position control based on the sensing result
to ensure that the misalignment is in the best situation.
The phased division point for Phase I and Phase II is
denoted by kth. Consequently, a coefﬁcient representing the
ﬁrst and second periods is introduced as
ψk =
{
1, if 0<k ≤kth,
0, if kth <k ≤K. (1)
Fig. 1. UA V-assisted integrated system of sensing, communication, and
position control.
Fig. 2. Two-phase transmission in an ISAC frame.
A. Communication Channel
The alignment of communication beams plays a crucial
role in enhancing the transmission rate. In the subsequent
section, the channel model is presented, with a speciﬁc focus
on misalignment fading. Under this consideration, the wire-
less channel undergoes ﬂat fading (i.e., it is LoS-dominant),
incorporating path loss and misalignment fading, while the
impact of multipath fading is neglected. h1,k and h2,k rep-
resent the AGV-to-UA V channel and the UA V-to-RC channel
respectively, which are given by
h1,k =hp,khm,k, (2)
h2,k =hp,kha,k, (3)
where hp,k is the path loss at the k-th moment, and hm,k
andha,k are the misalignment fading of Phase I and Phase II,
respectively.
1) Path Loss: The path loss could be described with the
free-space propagation model, which is expressed as
hp,k =
√GtGrλ
4πdk
, (4)
where Gt and Gr are the gain of transmission and recep-
tion, respectively. λ = fc is the signal wavelength, where
c is the speed of light, f is the occupied frequency band.
dk =
√
(gx2,k−gx0,k)2 + (gy2,k−gy0,k)2 + (gz2,k−gz0,k)2
is the distance between UA V and RC at the k-th moment,
where gx,k,gy,k,g z,k expresses the x-axis, y-axis, and z-axis
coordinate values at the k-th moment, respectively. Moreover,
gz2,k is the ﬂight altitude of UA V at the k-th moment.
2) Misalignment Fading: It is assumed that the radius of
area covered by AGV and UA V is R and r at distance ds,
respectively. Additionally, lk denotes the misalignment error
between the beam center of AGV (O AGV ) and the beam
center of UA V (O UAV ) at the k-th moment. Fig. 3 shows
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12200 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 3. Misalignment error l and three situations in Phase I.
Fig. 4. Misalignment error and three situations in Phase II.
the three situations of misalignment errors based on lk versus
R. According to the result proposed by [39], the misalignment
fading of Phase I is expressed as
hm,k =P0e
−
2l2k
R2e, (5)
which shows that misalignment fading is the received power at
UA V in the areaS with distanceds.Re is the equivalent beam-
width, andeθ,k is the error of the horn antenna. Therefore, the
misalignment errors in Phase I considers only in the tangent
plane direction of the optimal direction, i.e., lk =ς·tan(eθ,k),
where ς is misalignment error factor. When lk = 0, the
received power is represented by
P0 =erf(ϵ)2, (6)
whereerf(·) is Gauss error function andϵ = (√πr)/(√2Rm)
[40]. Then, Re could be expressed as
R2e =R2m
√πerf (ϵ)
2ϵe−ϵ2 , (7)
whereRm is the maximum radius of the beam at distance ds.
As mentioned before, RC employs an omnidirectional antenna,
thus the alignment of UA V’s horn antenna is determined by
the projected area of UA V’s horn antenna beam onto the
omnidirectional antenna beam of RC [41], as shown in Fig. 4.
The misalignment fading ha,k in Phase II can be expressed as
ha,k = P0SkS0 e−
2L2k
R2e , (8)
whereS0 = 2πr20(1−cos(θ0)) is the projected area in the best
situation, and Sk = 2πr20(1− cos(θ0−eθ,k)) is the projected
area of UA V’s beam on RC’s beam, where r0 =
√
r2 +ds2
is the UA V’s beam radius and θ0 = 2 arctan(r/ds) is the
UA V’s beam angule. Then, the misalignment error Lk at the
k-th moment can be given by
Lk =ς· tan(eθ,k). (9)
Note that the appropriate position for UA V is the position
where the beam is perfectly aligned, in which UA V could be
in the best situations.
B. Sensing Channel
RC senses the position of AGV and UA V by transmitting
sensing signals with ULA. According to [42], the sensing
channel of UA V at thek-th moment is expressed as
hs,k =
√
β
g2z2,k +‖Z2,k− Z0,k‖ a(ϕ2,k), (10)
where β is channel gain at a distance of 1m from RC to
AGV or UA V . The position of RC and UA V at the k-th
moment is respectively expressed as G0,k(Z0,k,g z0,k)
and G2,k(Z2,k,g z2,k), where Z0,k(gx0,k,gy0,k) and
Z2,k(gx2,k,gy2,k).
C. UAV Position Control
The discrete-time control model of UA V is given by
xk+1 = Adxk + Bduk + wok, (11)
where Ad is the state transition matrix, Bd is the control input
matrix, uk is the control input, and wok is the perturbation
caused by additive gaussian white noise with zero mean and
variance W0. The state information of UA V at the controller
can be expressed as
yk =
{
xk, when δk = 1,
∅, when δk = 0, (12)
whereδk = (1−ψk)δ′k +ψk is the sensing activation factor in
an ISAC frame, andδ′k is the sensing activation factor in Phase
II.δk = 1 denotes the activation of sensing, indicating that the
embedded controller knows the sensing information at RC, and
δk = 0 denotes the absence of sensing activation, implying that
the controller lacks knowledge of the current state of UA V .
According to Eq. (11), the controller can calculate the control
input as
uk = Kuyk, (13)
where Ku = R−1c BTd Pk is the control gain, where
Pk can be solved by Ricatti equation BTd Pk + PkAd−
PkBdR−1c BTd Pk +Qk =−Qk−1 and the detail can be found
in [43]. Rc is the control cost of uk. The control gain Ku in
Phase I and II, follows the same rule with different parameters
Rc.
Furthermore, according to [44], for a rotorcraft UA V with
speed Zk = |G1,k−G1,k−1|∆ , where G1,k(Z1,k,g z1,k) is the
position of AGV , where Z1,k(gx1,k,gy1,k). Moreover, the
UA V’s position control introduces additional propulsion power
consumption, which is speciﬁcally modeled as
Pf,k(Zk) =Pb
(
1 + 3Z2k
U2tip
)
+ Pivo
Zk
+ 12doρswoZ3k, (14)
where Utip is the rotor blade tip speed, vo is the average
rotor induced speed, do is the body drag ratio, Pb and Pi
are respectively the blade proﬁle power and induced power, ρ,
s and wo are the air density, rotor solidity and blade angular
velocity, respectively.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12201
Fig. 5. Schematic diagram of the phased communication and sensing tasks in 3D and 2D angles.
D. UAV Antenna-Angle Control
The UA V’s antenna-angle control can be quickly adjusted
to ensure beam alignment with less power consumption. The
direction of the horn antenna on UA V is characterized by
the pitch angle θ and azimuth angle φ. Considering that
the antenna angle of AGV is ﬁxed, UA V moves along the
intersection line between its trajectory and the optimal angle
plane. To simplify the position control model and reduce
complexity, it is assumed that the azimuth angle remains
constant, and horizontal disturbances are neglected. The angle
at which the horn antenna points towards AGV at the k-th
moment can be calculated as θd,k, where
θd,k = tan−1

 gz1,k−gz2,k√
(gx1,k−gx2,k)2 + (gy1,k−gy2,k)2

.
(15)
Then, the error of horn antenna direction at thek-th moment
is
eθ,k =θk−θd,k, (16)
where θk is antenna direction angle of UA V at the k-th
moment, which can be obtained through UA V’s built-in sensor.
The control output at the k-th moment can be expressed as
qk =Kaϑk, (17)
whereKa is the control gain. UA V antenna-angle information
can be expressed as
ϑk =
{
θk, when δk = 1,
∅, when δk = 0. (18)
The discrete-time control model for horn antenna angle of
UA V is
θk+1 =Aaθk +Baqk +wk, (19)
where Aa and Ba are system parameter matrix, wk is distur-
bance.
III. I NTEGRATION OF SENSING , COMMUNICATION , AND
CONTROL
The integration communication, sensing, and position con-
trol of UA V are elaborated in this section. The communication
task in Phase I and Phase II is respectively the data trans-
mission from AGV to UA V and data transmission from UA V
to RC. RC performs the sensing tasks in a hybrid sensing
pattern. In Phase I, RC senses the positions of AGV and
UA V in a period pattern, and in Phase II, RC senses the
position of UA V in an event-triggered pattern, as shown in
Fig. 5. As the remote center is employed on the building at
a certain height, it is assumed that the LoS sensing channels
from the RC to AGV and UA V . The whole process of sensing
and communication include two phases. Firstly, this work
introduces the communication and sensing in Phase I in the
subsection III-A. Secondly, the communication and sensing in
Phase II is introduced in subsection III-B. Finally, the phased
integration problem of sensing, communication, and control is
formulated in subsection.C.
A. Communication and Sensing in Phase I
In this subsection, the received signal of UA V and the
achievable transmission rate are introduced at ﬁrst. Then,
the sensing performance and sensing power consumption are
described.
1) Communication Process in Phase I: In Phase I, AGV
and UA V participate in data transmission. Simultaneously,
the sensing function of RC is activated, and the control link
between RC and UA V is initiated.
For the commuincation in Phase I, the signal received by
UA V at thek-th moment can be expressed as
yu,k =h1,ksa + hHs,kx +ωk, (20)
where sa ∈ C is the communication signal from AGV ,
x∈ CN×1 is the sensing signal from RC,h1,k∈ C is the LoS-
dominant fading wireless channel between AGV and UA V at
thek-th moment, hs,k∈ CN×1 is RC sensing channel between
RC and UA V at the k-th moment, and ωk ∈ C is additive
noise with zero-mean and variance N0, i.e., ωk∼CN (0,N 0).
Moreover, the successive interference cancellation (SIC) tech-
nology is employed to achieve the simultaneous transmission
of sensing signals and communication signals on the same
channel. Then, the achievable transmission rate from AGV to
UA V at thek-th moment in Phase I can be expressed as
RR,k =



log2
(
1 +|h1,k|2Pc,k
N0
)
, if 0<|h1,k|2Pc,k≤Ps,k,
log2
(
1 +|h1,k|2Pc,k
Ps,k +N0
)
, otherwise,
(21)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12202 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 6. Sensing and control period pattern in Phase I.
where Pc,k is the transmit power of communication, Ps,k is
the receive power of sensing. If the SIC condition is satisﬁed,
the interference from the sensing signal to the communication
signal could be eliminated. Otherwise, the sensing signal could
be regarded as an interference for the achievable transmission
rate.
2) Sensing Process in Phase I: For the sensing in Phase I,
RC acquires the position information of UA V and AGV , based
on which the misalignment error l is calculated. As both the
AGV and UA V are mobile, the sensing targets in the ﬁrst stage
are the AGV and UA V , and then the periodic sensing pattern is
considered to ensure the sensing accuracy. Then, the position
control of UA V is performed based on the sensing results. The
activation conditions for the control mode are expressed by
εk =
{
1, if lk >R,
0, if lk≤R. (22)
Subsequently, based on the activation conditions of control
mode, either both the UA V position control and antenna-angle
control is implemented, or only the antenna-angle control is
implemented, as shown in Fig. 6.
The covariance matrix is used to evaluate the sensing perfor-
mance. According to [45], the covariance matrix is expressed
as
Rw,k =
M∑
i=1
wi,kwHi,k, (23)
where wm,k is the transmitting beamformer of the sensing
signal. Then, the transmit power of sensing signal at RC is
Pt,k = Tr(Rw,k). (24)
The sensing beampattern in the direction ϕm,k is given by
H1(ϕm,k) = aH(ϕm,k)Rw,ka(ϕm,k),m∈M, (25)
where a(ϕm,k)=
[
1,ej 2πλ d sin(ϕm,k),...,e j 2πλ d(N−1) sin(ϕm,k)]T
is the steering vector. ϕm,k = arcsin gxm,k√g2xm,k+g2ym,k,m ∈ Mis the horizontal angle relative to RC, which is related to the
positions of AGV and UA V .
In practical scenarios, the design of the desired sensing
beampattern is tailored to meet speciﬁc sensing requirements.
If the sensing system lacks information about the target
and operates in detecting mode, an isotropic beampattern is
preferred, where power is uniformly distributed among all
directions [46]. However, when the sensing system possesses
prior information about targets and operates in tracking mode,
the beampattern is anticipated to exhibit dominant peaks in the
target directions. Due to the acquisition of priori information
about AGV and UA V , RC adopts a tracking mode. Conse-
quently, the power of RC sensing UA V at the k-th moment
can be expressed as
Ps,k =
⏐⏐hHs,kw2,k⏐⏐2 =⏐⏐hHs,kW2,khs,k⏐⏐. (26)
According to [47], the mean square error (MSE) is regarded
as a beampattern approximation index to evaluate the sensing
perference, where the MSE of RC beampattern approximation
is deﬁned as MSE(R) =
M∑
m=1
⏐⏐Pd(ϕm)− aH(ϕm)Ra(ϕm)⏐⏐2,
where Pd is the minimum mean square error compared to
basic beamforming. According to [48], the beampattern in the
target direction can archieve high accuracy sensing when it
meets the MSE requirement with the desired beamforming.
B. Communication and Sensing in Phase II
In this subsection, the received signal at the remote center
and the achievable transmission rate are introduced at ﬁrst.
Then, the event-trigger sensing and UA V’s position control
are described. Finally, the activation conditions of sensing and
control in Phase II are introduced.
1) Communication Process in Phase II: For the communi-
cation in Phase II, UA V would forward the data to RC. The
signal received at RC can be expressed as
ya,k =h2,ksu +δ′khHs,kxe +ωk, (27)
where su ∈ C is the communication signal sent by UA V ,
h2,k∈ C is the LoS-dominant fading wireless channel between
UA V and RC at the k-th moment, xe∈ CN×1 is the echo
signal of the sensing signal sent by RC. In general, the echo
interference from the RC sensing signal is very small and
could be treated as noise [49]. In this case, the achievable
transmission rate from UA V to RC at the k-th moment in
Phase II can be expressed as
RT,k = log2
(
1 +|h2,k|2Pu,k
N0
)
, (28)
where Pu,k is the UA V’s transmit power of communication.
2) Sensing Process in Phase II: For the sensing in Phase II,
RC communication function is consistently active to receive
data from UA V . The scheduling of sensing function is executed
on demand. Thus, the event-triggered sensing pattern is con-
sidered to reduce the sensing cost with the overall performance
guarantee. For the event-triggered sensing pattern, the remote
center (i.e., the receiver) evaluates whether the triggering con-
dition is satisﬁed and decides whether to activate the sensing
function based on the achievable data rate. The data rate serves
as the triggering criterion since it directly indicates the wireless
channel quality. Thus, the trigger event relies on the feedback
from the receiver, which can reduce computational complexity
and enhance situation-awareness ability. In this approach, the
remote center performs the state estimation of UA V’s position.
The estimated state can be expressed as
ˆxk+1|k = Adˆxk|k + Bduk. (29)
The actual state of UA V is sensed by RC when the estimate
in Eq. (29) cannot maintain the control performance and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12203
guarantee the communication requirements. Then the state
estimation at k-th moment is obtained as
ˆxk|k =
{
xk, when δ′k = 1,
ˆxk|k−1, when δ′k = 0. (30)
The covariance matrix in Phase II is given by
Rv,k = vkvHk, (31)
where vk is the transmitting beamformer of sensing signal.
Then, the transmit power of sensing signal in Phase II is
Pv,k = Tr(Rv,k). (32)
The sensing beampattern in the direction ϕ2,k is given by
H2(ϕ2,k) = aH(ϕ2,k)Rv,ka(ϕ2,k). (33)
3) The Activation Conditions of Sensing and Control in
Phase II: For the sake of simplicity, this work assumes that
UA V hovers in the horizontal plane. Combining the actual
control updates in Eq. (11) and the estimated states in Eq.
(29), the error between the actual and state estimates of UA V
on the controller can be given by
ek+1 =xk+1− ˆxk+1|k. (34)
According to [50], similar to signal-to-noise ratio in com-
munication, the work adopts the concept of state to noise
ratio, i.e., γk+1 =|ˆxk+1|k|
2
L2 , and then derives the relationship
between the sensing-control activation threshold ptr and the
state-to-noise ratio threshold, i.e., ptr = exp
(
−
|ˆxk+1|k|2
γthk+1
)
. An
excessively high activation probability will trigger the sensing
functions more frequently, increasing energy consumption.
However, an excessively low probability will fail to ensure
the beam alignment, deteriorating the wireless channel quality
and reducing the transmission rate. Thus, a threshold for the
transmission rate of sensing activation is obtained
Rthk = log2
(
1 +|hp,k|2|hf,k|2Pu,k
N0
·|P 0·e
2 ln(ptr )
R2e |2
)
.
(35)
Then, RC evaluates whether the triggering condition is
satisﬁed and decides whether to activate the sensing function
based on the achievable data rate. The triggering condition of
sensing function is expressed as
δ′k =
{
1, if RT,k <R thk ,
0, if RT,k≥Rthk . (36)
The event-triggered sensing mode is sensitive to both the
achievable transmission rate in Phase II and the activation
threshold. In particular, a larger activation threshold provide a
higher requirement for the wireless data transmission, which
in turn is determined by the UA V’s transmit power. Thus, the
event-triggered sensing will be more sensitive to the design of
UA V’s transmit power when the activation threshold is larger.
Moreover, the event-triggered activation threshold is affected
by the activation probability, which in turn is determined
by the state-to-noise ratio threshold. In this way, it can be
inferred that a higher requirement of sensing quality will
lead to a larger threshold of state-to-noise ratio, and then a
Fig. 7. Sensing and control event-trigger pattern based on the achievable
transmission rate at RC in Phase II.
higher activation probability. Thus, the event-triggered sensing
is sensitive to the required sensing quality.
The control activation approach is judged based on UA V
beam projection area, which is expressed as
εk =
{
1, if Sk = 0,
0, if 0<S k≤S0. (37)
The detailed activation process of sensing and control is
shown as Fig. 7. Firstly, the achievable transmission rate from
UA V to RC at the k-th moment is calculated at RC. Based
on the event-triggered pattern, it is determined whether the
sensing activation or UA V state is estimated by the estimator.
Then, if sensing is activated, based on the activation conditions
of control mode, either both the UA V position control and
antenna-angle control is implemented, or only the antenna-
angle control is implemented.
C. Problem Formulation
This work employs the sensing results to control the antenna
angle and the UA V’s position to enhance the channel state
condition, and then improve the transmission rate of sen-
sory data from AGV to the remote center with low energy
consumption. Therefore, the objective function is formulated
as the ratio of sum data rate to power consumption, which
is generally regarded as the energy efﬁciency and could
balance the performance and cost. Moreover, to prevent the
data transmission volumes of the two phases from causing a
bottleneck in the ﬁnal transmission, a reasonable allocation
between the two phases will directly impact the system’s
communication capacity. The optimization variables of P0
includes the transmit power (Pc,k andPu,k), the beamforming
vector (wm,k and vk), and the phased division point for Phase
I and Phase II (k th). As the achievable data volume between
AGV and AP depends on the minimum of data volumes in
Phase I and Phase II, the value of division point kth affects
the achievable data volume (i.e., the numerator of the objective
function). Moreover, a largerkth will increase the data volume
in Phase I, but decrease the data volume in Phase II. Thus,
it is necessary to optimize the value of the division point kth
to balance the data volumes in Phase I and Phase II. Both
the transmitting beamformer of sensing signal wm,k and the
transmit power of communication signal Pc,k are the essential
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12204 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
parameters in Phase I, which determines the sensing accuracy
and the transmission rate in Phase I, respectively. Similarly,
both the transmitting beamformer of sensing signal vk and the
transmit power of communication signal Pu,k are the essential
parameters in Phase II, which determines the sensing accuracy
and the transmission rate in Phase II, respectively. Based
on the above discussion, the constrained energy efﬁciency
maximization problem is formulated as
P0::maxth,Pc,k,
wm,k,Pu,k,vk
∑K
k=kthRT,k
P tot
s.t.C1 : ψk
M∑
m=1
|Pd(ϕm,k)−H1(ϕm,k)|2≤τ,∀k,
C2 : δ′k|Pd(ϕ2,k)−H2(ϕ2,k)|2≤τ,∀k,
C3 : Tr(Rw,k)≤Pl, Rw,k≽ 0,∀k∈ (0,k th],
C4 : Tr(Rv,k)≤Pl, Rv,k≽ 0,∀k∈ (kth,K ],
C5 : 0 <|h1,k|2Pc,k≤Ps,k,∀k∈ (0,k th],
C6 : 0 <P u,k≤Po,∀k∈ (kth,K ],
C7 :
K∑
k=kth
RT,k≤
kth∑
k=1
RR,k,
C8 : kth∈ Z+,k th∈ (0,K ),
C9 : δ′k,εk,ψk∈{ 0, 1},∀k∈K,
whereP tot =
K∑
k=1
[ψk(Pc,k+Pt,k)+(1−ψk)(Pu,k+δ′kPv,k)+
εkPf,k]. In addition, C1 and C2 denote RC sensing accuracy
constraints corresponding to phase I and phase II. C3 and
C4 denote the maximum transmit power of beamforming
constraint, where Pl denotes the sensing power budget. C5
is the constraint of the SIC conditions in Phase I. C6 is the
constraint of the transmit power of communication in Phase II.
C7 is the upper limit of the data volume transmitted in Phase
II. C8 denotes the integer constraint on the phased division
point. C9 denotes the 0-1 constraint on the sensing and control
activation factors.
Note that P0 is a mixed-integer nonlinear programming
(MINLP) problem, since it includes the integer variable kth
and continuous transmit beamformer of the sensing signal
variable wm,k, vk and the transmit power of AGV and
UA VPc,k,Pu,k. The nonlinear objective function cannot
be expressed explicitly with decision variables. Thus, it is
intractable to solve P0 directly so that the effective decom-
position and iterative methods are employed to solve P0.
IV. J OINT BEAMFORMING AND POWER ALLOCATION VIA
CONVEX APPROXIMATION AND PROBLEM
DECOMPOSITION
In this section, the original problem is decomposed into two
subproblems. One is the beamforming and power allocation
subproblem in Phase I, and the other is phased division point,
beamforming and power allocation subproblem in Phase II.
Then, the Golden-section search-based Dinkelbach algorithm
and Penalty-based SCA algorithm are proposed to solve
the non-convex subproblem in Phase I due to the fractional
objective function and rank-one constraints. Moreover,
based on quadratic transform, joint RC beamforming and
UA V communication power design is proposed to solve the
subproblem in Phase II.
A. Problem Decomposition
The quadratic form of covariance matrix and the fractional
form of objective function make it challenging to solve P0
efﬁciently. Moreover, it can be seen that the beamforming
vectors change with UA V and AGV positions and inﬂuence
communication and sensing power. Therefore, to effectively
solve the non-convex problem, it is decomposed into two
subproblems based on two phases of relay transmission.
Speciﬁcally, at the k-th moment, the beamforming and power
allocation subproblem in Phase I is expressed as
SP 1 : maxPc,k,wm,k
RR,k
Pc,k +Pt,k +εkPf,k
s.t. C1, C3, C5, C9.
Thus, the phased division point, beamforming and power
allocation subproblem in Phase II is expressed as
SP 2 : maxkth,Pu,k,vk
K∑
k=kth
RT,k
P tot
s.t. C2, C4, C6− C9.
B. Solution to Problem SP 1
In this section, we propose the golden-section based Dinkel-
bach algorithm and penalty based SCA algorithm to solve the
fractal non-convex subproblem SP 1. As the numerator is a
concave function on the communication transmit power of
AGV , and the denominator is a convex function on the power.
SP 1 can be converted into a concave maximization problem
by utilizing Dinkelbach method [51], [52]. The transformed
subproblem is given by
SP 1.1 : maxPc,k,wm,kf(ηk) =RR,k−ηk(Pc,k +Pt,k +εkPf,k)
s.t. C1, C3, C5, C9,
where ηk =RR,k/Pc,k +Pt,k +εkPf,k.
Remark 1: According to [51], the optimization problem
SP 1.1 is equivalent to the optimization problem SP 1 if and
only if f(η∗k) = 0 where η∗k is the maximum ηk.
It means that if we ﬁnd η∗k, f(η∗k) = 0. Thus, the solution
to the optimization problem SP 1 can be obtained by solving
its equivalent problemSP 1.1.
Then, let Wm,k = wm,kwHm,k,∀m∈M , where Wm,k≽
0 and rank(Wm,k) = 1. Then,SP 1.1 can be reformulated as
SP 1.2 : maxPc,k,Wm,k f(ηk)
s.t. C1, C3, C5, C9,
C10 :Wm,k≽ 0, Wm,k = WHm,k,
∀m∈M,
C11 :rank(Wm,k) = 1.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12205
For this optimization problem, the primary non-convex con-
straint comes from the rank-one constraint, i.e., C11. A SDR
approach could be used to deal with the rank-one constraint.
Then, the general-rank solution obtained with SDR could be
reconstructed as a rank-one solution by using the eigenvalue
decomposition or Gaussian randomization method. This may
lead to a large performance loss and can not guarantee the
feasibility of reconstructed matrix. To deal with this issue,
we convert the rank one constraint into a penalty term in the
objective function and then solve the reformulated problem
with SCA. According to [53], we introduce an equation
constraint
‖Wm,k‖∗−‖Wm,k‖2 = 0,m∈M, (38)
where‖·‖ ∗ is the nuclear norm that is the sum of singular
values of the matrix, and ‖·‖ 2 is the spectral norm, which is
the largest singular value of the matrix. Thus, Eq. (38) will
hold if Wm,k is a rank-one matrix. Otherwise, the sum of
singular values is larger than the largest singular value, i.e.,
‖Wm,k‖∗−‖ Wm,k‖2 > 0, since Wm,k is semideﬁnite. To
obtain a rank-one matrix, we introduce a penalty term to the
objective function based on Eq. (38), yielding that
SP 1.3 : maxPc,k,Wm,k f(ηk)− 1ξ (‖Wm,k‖∗−‖Wm,k‖2)
s.t. C1, C3, C5, C9, C10,
C11 :Wm,k≽ 0, Wm,k = WHm,k,
∀m∈M,
where ξ is the penalty factor. The rank of Wm,k is closer to
1 when ξ tends to 0, i.e., 1ξ tends to∞. In this case, the main
non-convexity of SP 1.3 comes from the second term of the
penalty term, whichcould be replaced with its upper bound
replacement, i.e., its ﬁrst-order Taylor expansion term at the
Wnm,k point, which is given by
−‖Wm,k‖2≤ ˜Wnm,k ∆=−‖Wnm,k‖2
− Tr
[
ˆ wn∗max,m,k( ˆ wn∗max,m,k)H(Wm,k− Wnm,k)], (39)
where ˆ wnmax,m,k is the eigenvector corresponding to the largest
eigenvalue of Wnm,k. Thus, the problemSP 1.3 can be approx-
imated by
SP 1.4 : maxPc,k,Wm,k f(ηk)− 1ξ(‖Wm,k‖∗ +‖ ˜Wnm,k‖2)
s.t. C1, C3, C5, C9, C10.
The problem SP 1.4 is a quadratic semideﬁnite program
(QSDP), which can be efﬁciently solved by the CVX toolbox
[54] and the MOSEK solver [55]. As mentioned above, the
ξ value can only be closer to the rank-one constraint if the
penalty term is sufﬁciently small. However, a problem will
arise as the value of the objective function tends to be inﬁnity.
It cannot get a value that ﬁts the rule, so a reduction factor ϵ is
proposed. By initialising a large value of ϵ and then gradually
reducing it to a sufﬁciently small value via ξ =ϵξ, 0<ϵ< 1,
the overall suboptimal solution is obtained. When the penalty
term is small enough, i.e., ‖Wm,k‖∗−‖Wm,k‖2≤ε2.
Algorithm 1 Golden-Section Based Dinkelbach Algorithm on
Outer Iterative
1 Input: ηl, ηh, κ, ϕm,M, η, ξ, δk, εk, Pf,k;
2 Output: η∗k, W∗m,k, P∗c,k;
3 Initialization: τ = (
√
5− 1)/2, υl = ηh−τ(ηh−ηl),
υh =ηl +τ(ηh−ηl);
4 repeat
5 SolveSP 1.4 besed on ηl and ηh with Algorithm 2;
6 Calculate f(ηl) and f(ηh);
7 if f(ηl)≤f(ηh) then
8 f(ηl)←−f(ηh), ηl ←−υl, υl ←−υh, υh ←−
ηl +τ(ηh−ηl);
9 else
10 ηh←−υh,υh←−υl,υl←−ηl +(1−τ)(ηh−ηl);
11 end if
12 until|ηh−ηl|≤ κ;
13 η∗k←−(ηh +ηl)/2;
14 Calculate W∗m,k and P∗c,k by solvingSP 1.4 besed on η∗k
with Algorithm 2.
Algorithm 2 Penalty-Based SCA Algorithm on Inner Iterative
1 Input: ϕm,M, η, ξ;
2 Output: Wm,k, Pc,k;
3 Initialization: feasible W0m,k, ϵ, ε1, ε2;
4 repeat
5 n−→0
6 repeat
7 SolveSP 1.4 according to Wnm,k;
8 Update Wn+1m,k based on Wnm,k;
9 n←−n + 1;
10 until ι = |fn−fn−1|fn−1 ≤ε1
11 W0m,k←− Wnm,k;
12 ξ←ϵξ;
13 until‖Wm,k‖∗−‖Wm,k‖2≤ε2.
Moreover, a two-layer iterative algorithm based on
Dinkelbach-penalty-SCA is designed to solve the energy efﬁ-
ciency maximization problem. The overall solution process of
SP 1.4 is summarised in Algorithm 1 and Algorithm 2. The
outer iteration is the golden-section search-based Dinkelbach
algorithm, which aims to ﬁndη∗k from [0,η upk ], whereηupk is an
upper bound onηk. For Algorithm 1, the Dinkelbach algorithm
has capability to obtain the optimal solution of convex prob-
lems. The inner iteration employs a penalty-based successive
convex approximation algorithm, which obtains a sub-optimal
solution by analyzing the convergence of the penalty term and
the objective function value. In this work, the initial values
of Wm,k and Pc,k are set as 0. Moreover, different initial
value selections may affect the algorithm convergence speed,
but will not affect the convergence value. The complexity
of the Algorithm 1 isO(log(ηh/κ) log(f(ηh)/κ)), and the
complexity of Algorithm 2 is O(IoIiM6.5N6.5 log(1/ϵ)),
where Io and Ii are the numbers of iterations in the
outer and inner layers in Algorithm 2. Consequently,
the complexity of the algorithm for solving SP 1.4 is
O(log(ηh/κ) log(f(ηh)/κ)(IoIiM6.5N6.5 log(1/ϵ))).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12206 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
C. Solution to Problem SP 2
InSP 2, the integer variable kth makes it challenging to
solveSP 2 directly. If the length of an ISAC frame is given,
the selections of phased division point are ﬁnite, and a search
algorithm can be employed to ﬁnd out the best one. Therefore,
in solving the SP 2 problem, we ﬁx the value of kth for
the problem. Moreover, in Phase II, the power consumption
for Phase I has already been determined. Consequently, the
formulation of the SP 2 problem can be rewritten as
SP 2.1 : maxPu,k,vk
K∑
k=kth
RT,k
Pu,k +δ′k(Pv,k +εkPf,k)
s.t. C2, C4, C6− C9.
The optimization objective function of SP 2.1 has an
expression of multiple-ratio fractional form, which makes it
intractable. Motivated by the direct fractional form algorithm
[56], the quadratic transform is applied to decouple the objec-
tive function as
g(Pu,k, vk,χk)
= 2χk
√
RT,k−χ2k(Pu,k +δ′k(Pv,k +εkPf,k)), (40)
where χk is introduced as auxiliary variable and given by
χk =
√
RT,k/(Pu,k +δ′k(Pv,k +εkPf,k)). (41)
Then, the original problem SP 2.1 is equivalently trans-
formed as
SP 2.2 : maxPu,k,vk
K∑
k=kth
g(Pu,k, vk,χk)
s.t. C2, C4, C6− C9.
Remark 2: According to [56], the optimization problem
SP 2.2 is equivalent to the optimization problem SP 2.1 if and
only if ∂g(Pu,k, vk,χk)/∂χ∗k = 0 where χ∗k is the maximum
χk.
χ∗k =
√
RT,k
Pu,k +δ′k(Pv,k +εkPf,k). (42)
In Phase II, RC needs to sense UA V only when the sensing
function is activated. Based on this, there is no need to
compute the sensing beamforming when the sensing-control
system is not activated. Therefore, we rewrite the optimization
problem is different cases. The inactivation problem and acti-
vation problem is shown inSP 2.3.1 andSP 2.3.2, respectively.
SP 2.3.1 : maxPu,k 2χk
√
RT,k−χ2kPu,k
s.t. C6− C9.
The problem SP 2.3.1 is a convex program, which can be
efﬁciently solved with the CVX toolbox [54] and the MOSEK
solver [55].
SP 2.3.2 : maxPu,k,vkg(Pu,k, vk,χk)
s.t. C2, C4, C6− C9.
The problemSP 2.3.2 is a non-convex problem, and the main
non-convexity of SP 2.3.2 are RT,k and vk in the objective
function. Then, we deﬁne an auxiliary varaibles Vk = vkvHk ,
where Vk≽ 0 and rank(Vk) = 1.SP 2.3.2 can be reformu-
lated as
SP 2.4 : maxPu,k,Vkg(Pu,k, Vk,χk)
s.t. C2, C4, C6− C9,
C12 :Vk≽ 0, Vk = VHk,
C13 :rank(Vk) = 1.
The main non-convex constraint of SP 2.4 comes from the
rank-one constraint of C13. Compared to Phase I, only the
UA V is the sensing target in Phase, and it is feasible to select
an algorithm with lower complexity. For such problems, a
common solution is to ignore the rank-one constraint to ﬁnd
a matrix that does not satisfy rank one and use eigenvalue
decomposition to recover a suboptimal solution that satisﬁes
the rank-one constraint [57]. However, this will cost some
performance and may result in the new solution not meeting
the original constraints. As stated in Theorem 1, it is indicated
that there always exists an optimal solution with rank-one for
the problemSP 2.4.
Theorem 1: For problemSP 2.4, there always exists a global
optimal solution ˜Vk, with rank( ˜Vk) = 1,∀k∈K .
Proof: Let ˆVk be the optimal solution for problem SP 2.4.
A new solution can be constructed as
˜ vk = (hHs,k ˆVkhs,k)−1/2 ˆVkhs,k, (43)
˜Vk = ˜ vk˜ vHk. (44)
It is evident that ˜Vk is positive semi-deﬁnite, and
rank( ˜Vk) = 1. Moreover, it can be easily proven that
hHs,k ˜Vkhs,k = hHs,k˜ vk˜ vHk hs,k = hHs,k ˆVkhs,k. (45)
For constraint C4, substituting (43) and (44) yields
tr(Rv,k) = tr( ˜Vk) = tr(˜ vk˜ vHk )
= tr((hHs,k ˆVkhs,k)−1 ˆVkhs,khHs,k ˆVHk )
= tr( ˆVk). (46)
Therefore, the newly constructed solution ˜Vk satisﬁes all
the original problem constraints and ensures rank( ˜Vk) = 1,
∀k∈K . ■
Meanwhile,SP 2.4 can be reformulated as
SP 2.5 : maxPu,k,Vkg(Pu,k, Vk,χk)
s.t. C2, C4, C6− C9, C12.
The problemSP 2.5 is a QSDP, which can also be efﬁciently
solved by the CVX toolbox [54] and the MOSEK solver [55].
The detailed solution procedure of SP 2 is shown as Algo-
rithm 3, which guarantees optimality. Speciﬁcally, the update
of the auxiliary variableχ∗k based on the quadratic transforma-
tion is ﬁrstly determined (Step 4-Step 12). Then, the optimal
communication powerPu,k or the optimal beamforming vector
Vk is solved according to the converged auxiliary variable χ∗k
(Step 13-Step 17). The corresponding computational complex-
ity isO(((N +1)3.5 log(1/ϵ)+1)n +(N +1)3.5 log(1/ϵ)+1).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12207
Algorithm 3 Quadratic Transform Enabled Joint Design of
RC Beamforming and UA V Communication Power
1 Input: δ′k, εk, Pf,k, ϕm, ζ;
2 Output: χ∗k, V∗k, P∗u,k;
3 Initialization: χk, Pu,k, Vk;
4 while χk is not conbergent do
5 Update χ∗k by (42);
6 if δ′k = 0 then
7 Update UA V’s transmit power Pu,k by solving
SP 2.3.1;
8 else
9 Update Vk and Pu,k by solvingSP 2.5;
10 Reconstruct the new solution ˜Vk according to (43);
11 end if
12 end while
13 if δ′k = 0 then
14 Calculate UA V’s transmit power P∗u,k by solving
SP 2.3.1 with χ∗k;
15 else
16 Calculate V∗k and P∗u,k by solvingSP 2.5 with χ∗k.
17 end if
TABLE II
LIST OF VALUES FOR MAIN PARAMETERS
Therefore, the proposed algorithms can obtain a sub-optimal
solution ofP0 with low complexity.
V. S IMULATION RESULTS
In this section, numerical results are provided to verify the
feasibility and advantage of the proposed UA V-assisted inte-
gration of communication, sensing, and control in industrial
IoT. The speciﬁc parameter settings are shown in Table II.
Fig. 8. Convergence of the proposed algorithms.
Fig. 9. Convergence of the proposed algorithms.
A. Convergence of the Proposed Convex Approximation
Approach
As shown in Fig. 8(a), the search interval of Algorithm 1
decreases with the growth of the number of iterations. It is
almost to 0, while the number of outer iterations is about 10.
Moreover, the upper bound of the search interval is smaller, the
convergence ratio is faster. As shown in Fig.8(b), the objective
function value of Algorithm 2 converges quickly with different
reduction factors in the penalty term. The smaller the reduction
factor is, the larger the objective function convergence value
is. The corresponding penalty term values all converge to 0,
and the smaller the reduction factor, the faster the convergence
ratio, as shown in Fig. 9(a).
As shown in Fig. 9(b), the objective function values of
Algorithm 3 converge quickly with the growth of the number
of iterations with different initial values. Moreover, when the
initial value of iteration is closer to the objective function
value, the convergence value is larger. This veriﬁes that the
convergence of algorithms is affected by the initial value of
iteration and the reduction factor. It also demonstrates the
feasibility of beamforming and resource allocation in the UA V-
assisted integration of sensing, communication and control
approach for the considered industrial IoT system.
B. Performance Comparison Among Different Approaches
In this section, we perform extensive simulations to evaluate
the performance of proposed approach in terms of data volume
and energy efﬁciency. The data volume is deﬁned as the total
data volume received by RC in one ISAC frame. Energy
efﬁciency is deﬁned as the ratio of the total data volume to
the total power consumption in one ISAC frame. The length of
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12208 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 10. Performance Comparison among different approaches with the
variation of Phase I and Phase II division points.
one ISAC frame is set to 100 time slots in the simulation. It is
assumed that AGV moves at a constant speed on a stationary
route without considering the effect of disturbances.
Four additional approaches are considered for compari-
son. The ﬁrst one is the UA V antenna-angle sensing-control
approach with period N = 5 (PAAC-5). The communi-
cation and sensing model is invariable in the UA V-assisted
integration of sensing, communication and control approach.
The second one is the UA V antenna-angle sensing-control
approach with period N = 10 (PAAC-10). The third one
is an event-triggered UA V position sensing-control approach
(ETMC), where triggering condition is invariable. The fourth
one is a communication approach that does not perform any
sensing-control operations (No control). After analyzing the
performance of sub-problem solving, we will investigate the
performance of relay transmission in a single ISAC frame.
1) Performance Comparison With Different Phased Divi-
sion Points: The data volume comparison among ﬁve
approaches is shown in Fig. 10. When the phased division
point from 30 to 50, the data volume in one ISAC frame
ﬁrst increases and then decreases. Moreover, the proposed
approach exhibits a greater amount of data compared to other
comparing approaches. The maximum data volume is reached
at kth = 39. This is because that in one ISAC frame, the
distance between AGV and UA V is smaller than that between
UA V and RC. When the upper bound of communication power
is ﬁxed, the transmission rate in Phase I will be slightly
higher than that in Phase II, and then the data volume is
determined by Phase II. Therefore, we set the phased division
point between Phase I and Phase II to 39 when the initial
values of the simulation are set as shown in Table II.
2) Performance Comparison Among Different Approaches
With the Variation in Communication Power Limitation:
The performance comparison among the ﬁve compared ones
in terms of data volume and energy efﬁciency is shown in
Fig. 11. As shown in Fig. 11(a), the data volume with ﬁve
approaches in three cases of AGV’s transmit power limitation
increases gradually with the growth of UA V’s transmit power
budget and ﬁnally reaches the maximum value. This is because
the data volume of transmission is determined by the data
capacity that Phase I can transmit and is thus affected by the
communication rate of Phase I, namely the communication
power limition constraint of AGV . It is observed that the
greater transmit power budget of AGV is, the larger the data
Fig. 11. Performance comparison among different approaches with the
variation of UA V communication power limitation.
volume is. It is also observed that the UA V-assisted integration
of sensing, communication and control approach signiﬁcantly
slightly outperforms the compared ones. Moreover, the anoma-
lous data points observed on the yellow lines in Fig. 11(a)
can be attributed to the algorithmic limitations of the no-
control compared approach and the inherent randomness of the
wireless channel. Unlike the proposed approach, the compared
approach does not incorporate any sensing or control mecha-
nisms, and therefore lacks the capability to dynamically adjust
antenna angles or UA V positions in response to changing
channel conditions. Consequently, it fails to adapt to variations
in the wireless environment, leading to occasional anomalies
in the results shown in Fig. 11(a).
Similarly, Fig. 11(b) shows that the energy efﬁciency
increases at ﬁrst and then stabilizes with the increase of UA V’s
transmit power budget. When the UA V’s communication
power is limited, the achievable data volume is constrained
by that in Phase II. Furthermore, the data volume in Phase II
increases signiﬁcantly as the communication power limitation
of the UA V rises, thereby enhancing the overall energy efﬁ-
ciency. As the communication power limitation of the UA V
continues to increase, the data volume in Phase II eventually
exceeds that in Phase I, making Phase I the new bottleneck.
However, the achievable data volume in Phase I does not
depend on the UA V’s communication power. As a result, the
energy efﬁciency initially increases but eventually plateaus
with further increases in the UA V’s transmit power budget.
Moreover, the proposed approach has a certain performance
gain over the periodic antenna-angle control approaches. This
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12209
Fig. 12. Performance comparison among different approaches with the
variation of the distance between AGV and UA V .
is due to the fact that the proposed approach is able to
increase data volume. Moreover, the event-triggered approach
consumes less power because the number of triggers is less
than the periodic antenna-angle control approaches.
3) Performance Comparison Among Different Approaches
With the Variation in the Distance Between AGV and UAV:
The performance comparison in terms of data volume and
energy efﬁciency is shown in Fig. 12, while dAU is the
horizontal distance between AGV and UA V . As shown in
Fig. 12(a), the data volume with ﬁve compared approaches
increases and then decreases gradually with the increase of
horizontal distance between UA V and RC when dAU = 20m
and dAU = 35m. In the scenario where dAU = 20m, the
overall data volume is limited by Phase II performance, since
the wireless channel between AGV and UA V in Phase I is well.
When the UA V is closer to the AP, even a slight deviation in
its position can lead to signiﬁcant misalignment error, thereby
reducing the data volume achieved in Phase II. Within a
certain range, as the UA V-AP distance increases, the data
volume in Phase II also increases. However, once the distance
becomes larger, path loss becomes the dominant factor, and
the data volume begins to decrease with further increases
in horizontal distance. Moreover, the data volume converges
when the horizontal distance between UA V and RC is greater
than 30m. This is because that when AGV and UA V are close,
the antenna angles are greatly affected by position adjustment.
When there is a long distance between them two, the distance
becomes the main factor affecting the transmission rate that
achieved with all approaches tend to be same. Meanwhile,
Fig. 13. Performance comparison among different approaches with the
variation of UA V ﬂight height.
whendAU = 20m, the data volume improvement of the UA V-
assisted integration of sensing, communication and control
approach against others is 15.33%, 17.64%, 34.43%, and
59.48%, respectively. When dAU = 50m, limited by the
transmission volume in Phase I, the data volume remains ﬂat
as the horizontal distance between UA V and RC changes in
Phase II. For the periodic antenna-angle control approaches,
the energy efﬁciency gradually decreases with the increase
of horizontal distance between UA V and RC, and eventually
converge to a stable value, as shown in Fig. 12(b). Moreover,
the larger the period is, the lower the energy efﬁciency is.
4) Performance Comparison Among Different Approaches
With the Variation in the UAV Flight Height: The performance
comparison among ﬁve compared ones in terms of data volume
and energy efﬁciency is shown in Fig. 13. The increase of
the ﬂight height of UA V make the transmission rate in Phase
I and Phase II decrease. Therefore, the data volume that
can be received in one ISAC frame decreases, as shown in
Fig. 13(a). Similarly, the energy efﬁciency in one ISAC frame
gradually decreases with the increase of the UA V height, as
shown in Fig. 13(b). Moreover, both the proposed and ETMC
strategies signiﬁcantly outperform the no-control baseline in
terms of data volume and energy efﬁciency (shown as Fig. 13),
underscoring the critical importance of incorporating sensing
and control functions. As shown in Fig. 13(a), the proposed
approach could achieve a larger data volume than the com-
pared ETMC strategy. This gain is achieved through a dynamic
triggering mechanism that adapts to the current sensing and
control performance. Fig. 13(b) compares the energy efﬁciency
of the different strategies. Although all control strategies
consume propulsion energy to enhance sensing accuracy
and transmission rates, the proposed method outperforms
ETMC due to its dynamic adaptation to system requirements.
The non-adaptive nature of the ETMC strategy prevents it
from translating its energy consumption into proportional
performance gains, leading to lower energy efﬁciency.
C. Performance Comparison With Different Sensing
Beampatterns
Fig. 14 shows the sensing beampatterns comparison with
different angles obtained corresponding to Algorithm 2 and
Algorithm 3. In Phase I, RC simultaneously senses AGV
and UA V , but in Phase II, RC only senses UA V . In Phase
I, the beampattern with algorithm 2 has two main lobes that
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12210 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 14. Performance comparison of beamforming with the variation of the
sensing angles.
Fig. 15. Performance comparison with different state transition matrices Ad.
represent different target’s directions, as shown in Fig. 14(a).
In Phase II, it can also be observed that the beampattern
with algorithm 3 can achieve dominant peaks in the target
directions, as shown in Fig. 14(b). Moreover, the proposed
approach has a signiﬁcant power gain in the target direction
and low power leakage in the undesired directions, which
further veriﬁes the efﬁciency of the proposed approaches.
D. Performance Comparison With Different the Spectral
Radius of the State Transition Matrix
In this work, the purpose of UA V position control is to
correct the UA V’s position to the optimal position when
signiﬁcant deviations occur. As the UA V’s position control
is based on the event trigger framework, the event-triggered
Fig. 16. The impact of sensing error on energy efﬁciency.
condition is a key parameter that is related to the activation
probability. The deﬁnition of activation probability is given by
ptr = exp
(
−
|ˆxk+1|k|2
γthk+1
)
, where|ˆxk+1|k|2 is the misalignment
error, and γk+1 =|ˆxk+1|k|
2
L2 is the state signal-to-noise ratio.
As ˆxk+1|k = Adˆxk|k + Bduk, the parameter matrix of control
system will directly affect the activation probability. As the
number of sensing activation and the propulsion power con-
sumption depends on the activation probability, it is important
to analyze the impact of parameter matrix on the data volume
and energy efﬁciency. In order to highlight the impact of UA V
position control, in this subsection, the misalignment error
coefﬁcient is set to be ς = 200. Moreover, the spectral norm
of the parameter matrix of UA V position control is conﬁgured
as 0.6, 0.83, 1, 1.55 and 2, whose corresponding activation
probability respectively is 0.4, 0.5, 0.6, 0.7 and 0.8, regarding
as Case 1 to Case 5. The performance comparison among
different variables in terms of the number of activation and
energy efﬁciency is shown in Fig. 15.
As shown in Fig. 15(a), with the growth of the activation
probability, the activation frequency of sensing and UA V
antenna-angle control gradually increases, while the activation
frequency of UA V position control gradually decreases. This
is because a smaller activation probability will result in a
lower activation threshold, directly increasing the number of
sensing activation. Fewer number of sensing-control activation
will lead to the accumulation of state estimation errors with
disturbances, resulting in the signiﬁcant position deviation
that requires performing the UA V position control for cor-
rection. As shown in Fig. 15(b), with the growth of activation
probability, the overall energy consumption exhibits a trend
of ﬁrst decreasing and then increasing as the number of
sensing-control activation rises. Correspondingly, the energy
efﬁciency ﬁrst increases and then decreases. This is because,
when the activation probability is low, the increased frequency
of position control raises system energy consumption, while
the reduced sensing frequency fails to ensure high transmis-
sion rates over a long time duration. Conversely, when the
activation probability is high, the excessive sensing opera-
tions signiﬁcantly increase system energy consumption, further
leading to a decline in energy efﬁciency. Moreover, in this
simulation, when the activation probability is 0.6, a better
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12211
balance between energy consumption and transmission rate
could be achieved.
E. Performance Analysis About the Impact of Sensing on
Energy Efﬁciency
The impact of sensing error on energy efﬁciency is shown
as Fig. 16. It can be observed that an increase in the value
of τ leads to improved energy efﬁciency. This relationship
stems from the fact that a higher τ implies a less stringent
requirement on sensing accuracy. As a result, fewer resources
are needed to achieve the prescribed accuracy level, thereby
enhancing overall energy efﬁciency.
VI. C ONCLUSION
In this paper, a UA V-assisted integrated system of sensing,
communication and control in industrial IoT systems was
investigated to improve data transmission performance. Firstly,
the situation-aware hybrid sensing pattern was proposed to
minimize the interference of sensing signals on communi-
cation. Then, the integrated design of antenna-angle control
and position control was proposed to ensure beam alignment
with low energy consumption. Finally, to maximize system’s
energy efﬁciency, the phased fractional transformation and
convex approximation algorithms were designed to improve
beamforming accuracy and resource allocation effectiveness.
Numerical results demonstrated that the situation-aware hybrid
sensing pattern can improve transmission rate with low energy
consumption, which is appropriate for applying it into the area
of smart manufacturing. In future work, we will study data
transmission and path planning for AGVs and UA Vs in ISAC
systems.
REFERENCES
[1] B. Yin, J. Tang, and M. Wen, “Connectivity maximization in non-
orthogonal network slicing enabled industrial Internet-of-Things with
multiple services,” IEEE Trans. Wireless Commun., vol. 22, no. 8,
pp. 5642–5656, Aug. 2023.
[2] Q. Li, J. Chen, M. Cheffena, and X. Shen, “Channel-aware latency tail
taming in industrial IoT,” IEEE Trans. Wireless Commun., vol. 22, no. 9,
pp. 6107–6123, Sep. 2023.
[3] L. Lyu et al., “Adaptive edge sensing for industrial IoT systems:
Estimation task ofﬂoading and sensor scheduling,” IEEE Internet Things
J., vol. 10, no. 1, pp. 391–402, Jan. 2023.
[4] C. Chen, L. Lyu, S. Zhu, and X. Guan, “On-demand transmission for
edge-assisted remote control in industrial network systems,” IEEE Trans.
Ind. Informat., vol. 16, no. 7, pp. 4842–4854, Jul. 2020.
[5] B. Zhu, E. Bedeer, H. H. Nguyen, R. Barton, and Z. Gao, “UA V
trajectory planning for AoI-minimal data collection in UA V-aided IoT
networks by transformer,” IEEE Trans. Wireless Commun., vol. 22,
no. 2, pp. 1343–1358, Feb. 2023.
[6] L. Lyu, X. Guan, N. Cheng, and X. S. Shen, Advanced Wireless Tech-
nologies for Industrial Network Systems. Cham, Switzerland: Springer,
2023.
[7] Y . Zhu, B. Mao, and N. Kato, “IRS-aided high-accuracy positioning for
autonomous driving toward 6G: A tutorial,” IEEE Veh. Technol. Mag.,
vol. 19, no. 1, pp. 85–92, Mar. 2024.
[8] L. Lyu et al., “AGV-assisted adaptive cooperative transmission for state
estimation in industrial IoT systems,” IEEE Trans. Veh. Technol., vol. 74,
no. 2, pp. 2390–2405, Feb. 2025.
[9] Q. Wu et al., “A comprehensive overview on 5G-and-beyond networks
with UA Vs: From communications to sensing and intelligence,” IEEE
J. Sel. Areas Commun., vol. 39, no. 10, pp. 2912–2945, Oct. 2021.
[10] Y . Cao, S. Xu, J. Liu, and N. Kato, “Toward smart and secure V2X
communication in 5G and beyond: A UA V-enabled aerial intelligent
reﬂecting surface solution,” IEEE Veh. Technol. Mag., vol. 17, no. 1,
pp. 66–73, Mar. 2022.
[11] Y . Tan, J. Liu, and N. Kato, “Blockchain-based lightweight authentica-
tion for resilient UA V communications: Architecture, scheme, and future
directions,” IEEE Wireless Commun., vol. 29, no. 3, pp. 24–31, Jun.
2022.
[12] Y . Lin, S. Jin, M. Matthaiou, and X. Yi, “Circular RIS-enabled channel
estimation and localization for multi-user ISAC systems,” IEEE Trans.
Wireless Commun., vol. 23, no. 8, pp. 8730–8743, Aug. 2024.
[13] L. Lyu, Z. Chu, B. Lin, Y . Dai, and N. Cheng, “Fast trajectory
planning for UA V-enabled maritime IoT systems: A Fermat-point based
approach,” IEEE Wireless Commun. Lett., vol. 11, no. 2, pp. 328–332,
Feb. 2022.
[14] I. Behnke and H. Austad, “Real-time performance of industrial IoT com-
munication technologies: A review,” IEEE Internet Things J., vol. 11,
no. 5, pp. 7399–7410, Mar. 2024.
[15] F. Dong, F. Liu, Y . Cui, W. Wang, K. Han, and Z. Wang, “Sensing as
a service in 6G perceptive networks: A uniﬁed framework for ISAC
resource allocation,” IEEE Trans. Wireless Commun., vol. 22, no. 5,
pp. 3522–3536, May 2023.
[16] Y . Xiong, F. Liu, Y . Cui, W. Yuan, T. X. Han, and G. Caire, “On
the fundamental tradeoff of integrated sensing and communications
under Gaussian channels,” IEEE Trans. Inf. Theory, vol. 69, no. 9,
pp. 5723–5751, Sep. 2023.
[17] X. Li et al., “Integrated sensing, communication, and computation over-
the-air: MIMO beamforming design,” IEEE Trans. Wireless Commun.,
vol. 22, no. 8, pp. 5383–5398, Aug. 2023.
[18] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li,
“Throughput maximization for UA V-enabled integrated periodic sensing
and communication,” IEEE Trans. Wireless Commun., vol. 22, no. 1,
pp. 671–687, Jan. 2023.
[19] Z. Ni, J. A. Zhang, K. Yang, X. Huang, and T. A. Tsiftsis, “Multi-
metric waveform optimization for multiple-input single-output joint
communication and radar sensing,” IEEE Trans. Commun., vol. 70,
no. 2, pp. 1276–1289, Feb. 2022.
[20] Z. Xiao and Y . Zeng, “Waveform design and performance analysis for
full-duplex integrated sensing and communication,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1823–1837, Jun. 2022.
[21] Y . Zhang, Y . Liu, G. Sun, J. Li, and A. Wang, “Multi-objective
optimization for joint UA V-AGV collaborative beamforming,” in Proc.
IEEE Int. Conf. Syst., Man, Cybern. (SMC), Oct. 2022, pp. 150–157.
[22] Z. He, W. Xu, H. Shen, D. W. K. Ng, Y . C. Eldar, and
X. You, “Full-duplex communication for ISAC: Joint beamforming
and power optimization,” IEEE J. Sel. Areas Commun., vol. 41, no. 9,
pp. 2920–2936, Sep. 2023.
[23] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun., vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[24] B. Chang, W. Tang, H. Zhang, X. Liao, and Z. Chen, “Communication-
aware motion control scheduling of automatic guided vehicles for THz
beam alignment in IIoT,” in Proc. IEEE Int. Conf. Commun., May 2022,
pp. 4619–4624.
[25] Y . Liu et al., “Secure rate maximization for ISAC-UA V assisted com-
munication amidst multiple eavesdroppers,” IEEE Trans. Veh. Technol.,
vol. 73, no. 10, pp. 15843–15847, Oct. 2024.
[26] Q. Wang, R. Chai, R. Sun, R. Pu, and Q. Chen, “ISAC-enabled multi-
UA V cooperative perception and trajectory optimization,”IEEE Internet
Things J., vol. 11, no. 24, pp. 40982–40995, Dec. 2024.
[27] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[28] A. Khalili, A. Rezaei, D. Xu, F. Dressler, and R. Schober, “Efﬁcient
UA V hovering, resource allocation, and trajectory design for ISAC with
limited backhaul capacity,” IEEE Trans. Wireless Commun., vol. 23,
no. 11, pp. 17635–17650, Nov. 2024.
[29] C. Deng, X. Fang, and X. Wang, “Integrated sensing, communication,
and computation with adaptive DNN splitting in multi-UA V networks,”
IEEE Trans. Wireless Commun., vol. 23, no. 11, pp. 17429–17445, Nov.
2024.
[30] Y . Qin, Z. Zhang, X. Li, W. Huangfu, and H. Zhang, “Deep rein-
forcement learning based resource allocation and trajectory planning
in integrated sensing and communications UA V network,” IEEE Trans.
Wireless Commun., vol. 22, no. 11, pp. 8158–8169, Nov. 2023.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

12212 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[31] T. Zhang, K. Zhu, S. Zheng, D. Niyato, and N. C. Luong, “Trajectory
design and power control for joint radar and communication enabled
multi-UA V cooperative detection systems,” IEEE Trans. Commun.,
vol. 71, no. 1, pp. 158–172, Jan. 2023.
[32] Y . Jiang, Q. Wu, W. Chen, and K. Meng, “UA V-enabled integrated
sensing and communication: Tracking design and optimization,” IEEE
Commun. Lett., vol. 28, no. 5, pp. 1024–1028, May 2024.
[33] B. Chang, W. Tang, X. Yan, X. Tong, and Z. Chen, “Integrated
scheduling of sensing, communication, and control for mmWave/THz
communications in cellular connected UA V networks,” IEEE J. Sel.
Areas Commun., vol. 40, no. 7, pp. 2103–2113, Jul. 2022.
[34] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-UA V
networks,” IEEE Trans. Commun., vol. 69, no. 4, pp. 2660–2672, Apr.
2021.
[35] Q. Huang, W. Wang, W. Lu, N. Zhao, A. Nallanathan, and X. Wang,
“Resource allocation for multi-cluster NOMA-UA V networks,” IEEE
Trans. Commun., vol. 70, no. 12, pp. 8448–8459, Dec. 2022.
[36] M. Nikooroo and Z. Becvar, “Optimal positioning of ﬂying base stations
and transmission power allocation in NOMA networks,” IEEE Trans.
Wireless Commun., vol. 21, no. 2, pp. 1319–1334, Feb. 2022.
[37] M. Katwe, K. Singh, P. K. Sharma, C.-P. Li, and Z. Ding, “Dynamic
user clustering and optimal power allocation in UA V-assisted full-duplex
hybrid NOMA system,” IEEE Trans. Wireless Commun., vol. 21, no. 4,
pp. 2573–2590, Apr. 2022.
[38] J. Li, X. B. Zhai, H. Qian, R. Zhang, and X. Liu, “Joint trajectory design
and power allocation in NOMA-based UA V networks,”IEEE Trans. Veh.
Technol., vol. 73, no. 2, pp. 2345–2357, Feb. 2024.
[39] B. Chang, X. Yan, L. Zhang, Z. Chen, L. Li, and M. A. Imran, “Joint
communication and control for mmWave/THz beam alignment in V2X
networks,” IEEE Internet Things J., vol. 9, no. 13, pp. 11203–11213,
Jul. 2022.
[40] A.-A.-A. Boulogeorgos, E. N. Papasotiriou, and A. Alexiou, “Analytical
performance assessment of THz wireless systems,” IEEE Access, vol. 7,
pp. 11436–11453, 2019.
[41] A. Molisch, Wireless Communications: From Fundamentals To Beyond
5G. Hoboken, NJ, USA: Wiley, 2022.
[42] Q. Wu, J. Xu, and R. Zhang, “Capacity characterization of UA V-enabled
two-user broadcast channel,” IEEE J. Sel. Areas Commun., vol. 36,
no. 9, pp. 1955–1971, Sep. 2018.
[43] A. Cuenca, D. J. Antunes, A. Castillo, P. Garcia, B. A. Khashooei, and
W. P. M. H. Heemels, “Periodic event-triggered sampling and dual-rate
control for a wireless networked control system with applications to
UA Vs,”IEEE Trans. Ind. Electron., vol. 66, no. 4, pp. 3157–3166, Apr.
2019.
[44] Y . Zeng, J. Xu, and R. Zhang, “Energy minimization for wireless
communication with rotary-wing UA V ,”IEEE Trans. Wireless Commun.,
vol. 18, no. 4, pp. 2329–2345, Apr. 2019.
[45] Z. Wang, Y . Liu, X. Mu, Z. Ding, and O. A. Dobre, “NOMA empowered
integrated sensing and communication,” IEEE Commun. Lett., vol. 26,
no. 3, pp. 677–681, Mar. 2022.
[46] Z. Wang, Y . Liu, X. Mu, and Z. Ding, “NOMA inspired interference
cancellation for integrated sensing and communication,” in Proc. IEEE
Int. Conf. Commun., May 2022, pp. 3154–3159.
[47] C. Xu, B. Clerckx, S. Chen, Y . Mao, and J. Zhang, “Rate-splitting
multiple access for multi-antenna joint radar and communications,”
IEEE J. Sel. Topics Signal Process., vol. 15, no. 6, pp. 1332–1347, Nov.
2021.
[48] Y . Li, W. Ni, H. Tian, M. Hua, and S. Fan, “Rate splitting multiple
access for joint communication and sensing systems with unmanned
aerial vehicles,” in Proc. IEEE/CIC Int. Conf. Commun. China (ICCC
Workshops), Jul. 2021, pp. 37–42.
[49] L. Zhao, D. Wu, L. Zhou, and Y . Qian, “Radio resource allocation for
integrated sensing, communication, and computation networks,” IEEE
Trans. Wireless Commun., vol. 21, no. 10, pp. 8675–8687, Oct. 2022.
[50] B. Chang, W. Tang, X. Yan, and Z. Chen, “State-to-noise-ratio-based
transmission scheduling in wireless control systems for IIoT,” IEEE
Internet Things J., vol. 9, no. 7, pp. 4949–4957, Apr. 2022.
[51] W. Dinkelbach, “On nonlinear fractional programming,” Manage. Sci.,
vol. 13, no. 7, pp. 492–498, Mar. 1967.
[52] L. Lyu, C. Chen, S. Zhu, X. Wen, and X. Guan, “Sensing aware
opportunistic transmissions for situation monitoring in industrial net-
work systems,” in Proc. IEEE Global Commun. Conf. (GLOBECOM),
Dec. 2019, pp. 1–6.
[53] Z. Wang, X. Mu, Y . Liu, and R. Schober, “TTD conﬁgurations for near-
ﬁeld beamforming: Parallel, serial, or hybrid?,” in Proc. IEEE Trans.
Commun., vol. 72, Jun. 2024, pp. 3783–3799.
[54] M. Grant and S. Boyd. (Mar. 2014). CVX: MATLAB Software for
Disciplined Convex Programming, Version 2.1. [Online]. Available:
http://cvxr.com/cvx
[55] M. ApS. (2024). The MOSEK Optimization Toolbox for MAT-
LAB Manual. [Online]. Available: https://docs.mosek.com/11.0/toolbox/
index.html
[56] K. Shen and W. Yu, “Fractional programming for communication
systems—Part I: Power control and beamforming,” IEEE Trans. Signal
Process., vol. 66, no. 10, pp. 2616–2630, May 2018.
[57] Z.-Q. Luo, W.-K. Ma, A. So, Y . Ye, and S. Zhang, “Semideﬁnite
relaxation of quadratic optimization problems,” IEEE Signal Process.
Mag., vol. 27, no. 3, pp. 20–34, May 2010.
Ling Lyu (Member, IEEE) received the B.Eng.
degree in telecommunication engineering from Jilin
University, Changchun, China, in 2013, and the
Ph.D. degree in control theory and control engineer-
ing from Shanghai Jiao Tong University, Shanghai,
China, in 2019. She joined Dalian Maritime Uni-
versity, China, in 2019, where she is currently an
Associate Professor with the School of Informa-
tion Science and Technology. She was a Visiting
Student with the University of Waterloo, Canada,
from September 2017 to 2018. Her current research
interests include wireless sensor and actuator network and application in
industrial automation, the joint design of communication and control in
industrial cyber-physical systems, estimation and control over lossy wireless
networks, and control-aware integrated sensing and communication.
Qirui Luo received the B.Eng. degree in elec-
tronic information science and technology from
Henan Agricultural University, Zhengzhou, China,
in 2022, and the M.Eng. degree in information and
communication engineering from Dalian Maritime
University, Dalian, China, in 2025. His master’s
research focused on resource allocation in integrated
sensing and communication.
Yanpeng Dai (Member, IEEE) received the B.Eng.
degree in telecommunication engineering from
Shandong Normal University, Jinan, China, in 2014,
and the Ph.D. degree in communication and informa-
tion systems from Xidian University, Xi’an, China,
in 2020. He is currently an Associate Professor with
the School of Information Science and Technology,
Dalian Maritime University, Dalian, China. He was
a Visiting Student with the University of Water-
loo, Waterloo, ON, Canada. His research interests
include resource management and interference coor-
dination for heterogeneous wireless networks and maritime communication
systems.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply. 

LYU et al.: SITUATION-AW ARE HYBRID SENSING AND POSITION CONTROL FOR UA V-ASSISTED ISAC SYSTEMS 12213
Nan Cheng (Senior Member, IEEE) received the
B.E. and M.S. degrees from the Department of
Electronics and Information Engineering, Tongji
University, Shanghai, China, in 2009 and 2012,
respectively, and the Ph.D. degree from the Depart-
ment of Electrical and Computer Engineering,
University of Waterloo, Waterloo, ON, Canada, in
2016. From 2017 to 2019, he was a Post-Doctoral
Fellow with the Department of Electrical and Com-
puter Engineering, University of Toronto, Toronto,
ON. He is currently a Professor with the State Key
Laboratory of ISN and the School of Telecommunications Engineering, Xidian
University, Xi’an, Shaanxi, China. He has authored or co-authored more
than 90 journal papers in IEEE T RANSACTIONS and other top journals.
His research interests include B5G/6G, AI-driven future networks, and
space–air–ground integrated networks. He is an Associate Editor of IEEE
TRANSACTIONS ON VEHICULAR TECHNOLOGY , IEEE O PEN JOURNAL
OF THE COMMUNICATIONS SOCIETY , and Peer-to-Peer Networking and
Applications. He is/was a guest editor of several journals.
Cailian Chen (Senior Member, IEEE) received the
B.Eng. and M.Eng. degrees in automatic control
from Yanshan University, China, in 2000 and 2002,
respectively, and the Ph.D. degree in control and
systems from the City University of Hong Kong,
Hong Kong, SAR, in 2006.
She has been with the Department of Automa-
tion, Shanghai Jiao Tong University, since 2008.
She is currently a Distinguished Professor. She has
authored three research monographs and over 100
refereed international journal articles. She is the
inventor of more than 30 patents. Her research interests include industrial
wireless networks and computational intelligence and the Internet of Vehicles.
She received the prestigious IEEE T RANSACTIONS ON FUZZY SYSTEMS
Outstanding Paper Award in 2008, the IEEE TCCPS Industrial Technical
Excellence Award in 2022, and ﬁve conference best paper awards. She was
awarded the N2Women Star in Computer Networking and Communications
in 2022. She won the Second Prize of National Natural Science Award from
the State Council of China in 2018; the First Prize of Natural Science Award
from the Ministry of Education of China in 2006 and 2016, respectively; and
the First Prize of Technological Invention of Shanghai Municipal, China, in
2017 and 2023, respectively. She was honored with the “National Outstanding
Young Researcher” by NSF of China in 2020, the “Changjiang Young Scholar”
in 2015, and the prestigious China Young Women Scientists Award in 2024.
She has been actively involved in various professional services. She is a
Distinguished Lecturer of IEEE VTS. She serves as the Deputy Editor for
National Science Open and an Associate Editor for IEEE T RANSACTIONS
ON VEHICULAR TECHNOLOGY and IET Cyber-Physical Systems: Theory and
Applications.
Xinping Guan (Fellow, IEEE) is currently a
Chair Professor with Shanghai Jiao Tong Univer-
sity, Shanghai, China, where he is the Dean of
the School of Electronic, Information and Electrical
Engineering, and the Director of the Key Laboratory
of Systems Control and Information Processing,
Ministry of Education of China. Before that, he was
the Executive Director of the Ofﬁce of Research
Management, Shanghai Jiao Tong University, and a
Full Professor and the Dean of electrical engineering
with Yanshan University, Qinhuangdao, China. He
is the Leader of the prestigious Innovative Research Team of the National
Natural Science Foundation of China (NSFC). He has authored and/or co-
authored ﬁve research monographs, more than 200 articles in peer-reviewed
journals, and numerous conference papers. As a Principal Investigator, he has
ﬁnished/been working on more than 20 national key projects. His current
research interests include industrial network systems, smart manufacturing,
and underwater networks.
Dr. Guan is an Executive Committee Member of Chinese Automation
Association Council and Chinese Artiﬁcial Intelligence Association Council.
He received the Second Prize of the National Natural Science Award of China
in 2008 and 2018; and the First Prize of Natural Science Award from the
Ministry of Education of China and Municipal of Shanghai, China, for four
times. He was a recipient of “IEEE T RANSACTIONS ON FUZZY SYSTEMS
Outstanding Paper Award” in 2008 and the IEEE TCCPS Industrial Technical
Excellence Award in 2022. He was honored with the “National Outstanding
Youth” by NSF of China, the “Changjiang Scholar” by the Ministry of
Education of China, and the “State-Level Scholar” of the “New Century Bai
Qianwan Talent Program” of China.
Xuemin (Sherman) Shen (Fellow, IEEE) received
the Ph.D. degree in electrical engineering from
Rutgers University, New Brunswick, NJ, USA, in
1990. He is currently a University Professor with the
Department of Electrical and Computer Engineering,
University of Waterloo, Canada. His research inter-
ests include network resource management, wireless
network security, the Internet of Things, 5G and
beyond, and vehicular networks.
Dr. Shen is a registered Professional Engineer of
Ontario, Canada, an Engineering Institute of Canada
Fellow, a Canadian Academy of Engineering Fellow, a Royal Society of
Canada Fellow, a Chinese Academy of Engineering Foreign Member, and
an International Fellow of the Engineering Academy of Japan. He received
the “West Lake Friendship Award” from Zhejiang Province in 2023, the
President’s Excellence in Research from the University of Waterloo in 2022,
Canadian Award for Telecommunications Research from Canadian Society of
Information Theory (CSIT) in 2021, the R. A. Fessenden Award from IEEE,
Canada, in 2019, the Award of Merit from the Federation of Chinese Canadian
Professionals (Ontario) in 2019, the James Evans Avant Garde Award from
the IEEE Vehicular Technology Society in 2018, the Joseph LoCicero Award
in 2015 and Education Award in 2017 from the IEEE Communications
Society (ComSoc), and the Technical Recognition Award from the Wireless
Communications Technical Committee in 2019 and the AHSN Technical
Committee in 2013. He has also received the Excellent Graduate Supervision
Award from the University of Waterloo in 2006 and the Premier’s Research
Excellence Award (PREA) from the Province of Ontario, Canada, in 2003.
He serves/served as the General Chair for the 6G Global Conference 2023
and ACM Mobihoc 2015; the Technical Program Committee Chair/Co-Chair
for IEEE Globecom 2024, 2016, and 2007, IEEE Infocom 2014, and IEEE
VTC 2010 Fall; and the Chair for the IEEE ComSoc Technical Committee on
Wireless Communications. He is the Past President of the IEEE ComSoc, the
Vice President for Technical and Educational Activities, the Vice President for
Publications, the Member-at-Large on the Board of Governors, the Chair of
the Distinguished Lecturer Selection Committee, and a member of the IEEE
Fellow Selection Committee of the ComSoc. He served as the Editor-in-Chief
of IEEE I NTERNET OF THINGS JOURNAL , IEEE Network, and PPNA.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 01:35:37 UTC from IEEE Xplore.  Restrictions apply.