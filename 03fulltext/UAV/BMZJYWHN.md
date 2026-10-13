---
title: "ISAC Enabled Anti-UAV Joint Beamforming and Trajectory Design for Multi-UAVs"
zotero_key: "BMZJYWHN"
pdf_key: "YR2IGAYU"
collection: "UAV"
source: "User-provided PDF (pypdf extraction)"
page_mapping: unverified
---

# ISAC Enabled Anti-UAV Joint Beamforming and Trajectory Design for Multi-UAVs — Fulltext

> 由用户提供的 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 19611
ISAC Enabled Anti-UA V: Joint Beamforming and
Trajectory Design for Multi-UA Vs
Xiaojie Wang
 , Senior Member, IEEE, Lingfei Li
 , Graduate Student Member, IEEE ,
Zhaolong Ning
 , Senior Member, IEEE, Xiaoming Tao, Senior Member, IEEE, Tie Qiu
 , Senior Member, IEEE,
Lei Guo
 , and Yan Zhang
 , Fellow, IEEE
Abstract—The rapid proliferation of Uncrewed Aerial Vehicles
(UA Vs) introduces signiﬁcant challenges to low-altitude airspace
security, particularly from unauthorized intrusions. To address
these vulnerabilities, Integrated Sensing and Communication
(ISAC) has emerged as a key enabler for anti-UA V systems.
However, existing studies focusing on cellular networks with ﬁxed
base stations are ill-suited for the continuous movement of target
UA Vs, thus failing to meet the dual demands of ﬂexible sensing
and reliable positioning. To address this, we propose an ISAC-
enabled anti-UA V scheme solely based on cooperative UA Vs.
Speciﬁcally, we ﬁrst derive the optimal transmit power under the
constraint of space-air transmission outage probability tolerance.
Subsequently, we deduce the sensing Fisher information matrix
and Cram ´er-Rao Bound (CRB) by incorporating the position
uncertainty of the target UA V . Then, we formulate a long-
term CRB minimization problem to enhance cooperative sensing
performance. To tackle this NP-hard problem, we design a robust
optimization algorithm that jointly optimizes transmit-receive
beamforming, association scheduling, and UA V trajectory, by
transforming the structurally complex CRB matrix into a set
of semi-deﬁnite constraints, and resolving the inherent position
uncertainty. Numerical results demonstrate that our proposed
algorithm outperforms representative algorithms in terms of
sensing accuracy and robustness.
Index Terms —Integrated sensing and communication, anti-
UA V , beamforming design, Cram´er-Rao bound.
I. I NTRODUCTION
Received 8 January 2026; revised 19 April 2026; accepted 22 June 2026.
Date of publication 3 July 2026; date of current version 8 July 2026. This work
was supported in part by the National Natural Science Foundation of China
under Grant 62272075 and Grant 62221005; and in part by the Natural Science
Foundation of Chongqing under Grant CSTB2025NSCQ-LZX0050, Grant
CSTB2024NSCQ-JQX0013, and Grant CSTB2024NSCQ-QCXMX0058. The
associate editor coordinating the review of this article and approving it for
publication was S. Ikki. (Corresponding author: Zhaolong Ning.)
Xiaojie Wang and Lingfei Li are with the School of Communications
and Information Engineering, Chongqing University of Posts and Telecom-
munications, Chongqing 400065, China (e-mail: xiaojie.kara.wang@ieee.org;
s240101011@stu.cqupt.edu.cn).
Zhaolong Ning is with the School of Communications and Informa-
tion Engineering, Chongqing University of Posts and Telecommunications,
Chongqing 400065, China, and also with the School of Intelligence Science
and Engineering, Qinghai Minzu University, Xining 810007, China (e-mail:
z.ning@ieee.org).
Xiaoming Tao is with the School of Computer Science and Technology,
Xinjiang University, ¨Ur¨umqi 830046, China (e-mail: taoxm@xju.edu.cn).
Tie Qiu and Lei Guo are with the School of Computer Science and Engi-
neering, Northeastern University, Shenyang 110819, China (e-mail: qiutie@
ieee.org; guolei@cse.neu.edu.cn).
Yan Zhang is with the School of Information and Communication Engi-
neering, University of Electronic Science and Technology of China, Chengdu
611731, China (e-mail: yanzhang@ieee.org).
Digital Object Identiﬁer 10.1109/TWC.2026.3707705
T
HE rapid growth of the low-altitude economy has driven
the widespread adoption of Uncrewed Aerial Vehicles
(UA Vs) across sectors, boosting efﬁciency in military oper-
ations, security surveillance, and urban management [1].
However, malicious activities such as unauthorized ﬂight have
become increasingly frequent, posing severe threats to public
security and privacy. Against this backdrop, there is an urgent
need for anti-UA V systems capable of continuous sensing
and precise tracking. Integrated Sensing and Communication
(ISAC) technology is an emerging paradigm that represents
a synergistic integration of communication and radar func-
tionalities. This integrated approach effectively mitigates the
limitations of standalone sensor systems in addressing UA Vs’
high-speed maneuverability, low-altitude ﬂight, and active
evasion behaviors [2]. Speciﬁcally, ISAC-enabled anti-UA V
systems overcome the constraints of traditional monitoring and
signiﬁcantly enhance target recognition accuracy and tracking
stability, thus serving as a key technical pillar for building
efﬁcient, low-cost, and low-altitude security systems.
Existing research mainly focused on target sensing with
Base Stations (BSs) or cellular networks as the carrier. Authors
in [3] proposed an ISAC-enabled dual-function monostatic
system, aiming at sensing aerial targets while providing stable
service for Communication Users (CUs). Building on this,
a massive multiple-input multiple-output ISAC system was
designed in [4], where the BS precisely steered the probing
signal’s transmission angle toward the target for efﬁcient
sensing-communication coordination. Authors in [5] presented
a multi-cell anti-UA V system and quantitatively character-
ized the sensing signal-to-clutter-noise ratio by considering
inter-cell and mutual interference. Further, a coordinated
beamforming scheme for multi-cell systems was designed in
[6], aiming to maximize the downlink detection probability.
Building on this, authors in [7] accounted for the impact
of imperfect Channel State Information (CSI), and adopted
distributed dual-function base stations by jointly optimizing
two-stage duration and transmit beam.
Despite this, the aforementioned studies suffer from terrain-
induced signal blockage, and challenges in cross-regional
sensing, while UA V-assisted ISAC emerges as a highly com-
petitive solution. Authors in [8] provided a cellular-connected
UA V system, where the BS and connected UA V perform
cooperative sensing tasks for multiple targets. Furthermore,
a set of networked BSs with the authorized UA V was con-
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19612 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE I
COMPARISON BETWEEN THIS WORK AND THE RELATED ONES
sidered in [9], which cooperatively transmit ISAC signals to
sense unauthorized objects within the region of interest. To
balance communication and sensing, authors in [10] proposed
a joint optimization framework for ISAC beams, while satis-
fying sensing frequency and beam pattern gain constraints.
Considering practical channel uncertainty, authors in [11]
broke through the ideal channel assumption and proposed
a robust downlink transmit beamforming design. Regarding
trajectory and resource allocation, a multi-stage trajectory
design by jointly optimizing UA V trajectory and allocating
user’s bandwidth was proposed in [12]. For multi-user and
multi-target scenarios, authors in [13] investigated the joint
resource allocation and trajectory design with limited BS-UA V
link capacity. Recently, considering UA V ﬂight characteris-
tics, authors in [14] considered different degree-of-freedom
dynamic models of UA V , aiming to maximize the average
weighted communication rate while maintaining dynamic and
sensing constraints.
However, the aforementioned ISAC schemes still face
critical drawbacks: they suffer from inﬂexibility due to
single-UA V operation and centralized control, while being
hampered by the static nature of BSs and limited UA V agility,
collectively leading to incomplete coverage and severely
degraded sensing performance. In contrast, multi-UA V coop-
erative sensing emerges as a critical solution to achieve
high-efﬁciency and high-reliability perception in complex
and dynamic scenarios [15]. Considering the complicated
interference management among UA Vs, research [16] jointly
optimized UA V trajectories, association, and power control.
The network utility maximization problem in a dual-functional
radar-communication multi-UA V network was investigated
[17]. Authors in [18] considered navigating multiple UA Vs
in a distributed way by jointly optimizing the collected data
volume, geographical fairness and limited energy reserve. In
[19], the placement optimization for multi-UA V localization
networks was explored, with a robust placement strategy
proposed. Regarding multi-UA V cooperative detection, authors
in [20] considered a typical scenario where UA Vs simulta-
neously detect targets and forward sensed data to a fusion
center. To maximize the minimum weighted spectral efﬁciency
across UA Vs, literature [21] formulated the joint sensing
and communication performance optimization as a sequential
decision-making problem, and jointly optimized user associa-
tion, UA V trajectory planning, and power allocation.
Another critical limitation of existing studies on UA V-
assisted ISAC networks is their presumption of the statically
located and perfectly known unauthorized UA V . However,
this assumption neglects the dynamic nature and position
uncertainty caused by the continuous movement of practical
aerial targets, which fundamentally hinders high-sensitivity,
anti-interference, and efﬁcient tracking of them in complex
scenarios. Consequently, their proposed strategies may offer
diminished returns in environments with mobile targets or
time-varying network topologies.
To address the above challenges, we propose an ISAC
enabled anti-UA V framework with multiple authorized UA Vs,
CUs and one unauthorized UA V (the target UA V), while
considering the position uncertainty induced by its mobility.
The comparison between our work and the related work is
presented in Table I, and the key contributions of this paper
are summarized as follows:
• An ISAC Enabled Anti-UA V Framework: To the
best of our knowledge, this is the ﬁrst study on an
ISAC enabled anti-UAV framework while accounting
for position uncertainty induced by the mobility of the
target UAV .To achieve efﬁcient cooperative sensing and
resource scheduling, we design an innovative time allo-
cation model among multi-UA Vs by adopting spatially
separated transmit-receive beamforming.
• Cooperative Cram ´er-Rao Bound (CRB) Derivation:
By analyzing sensing echo signals received by authorized
UA Vs while satisfying the tolerable outage probability
of space-air transmission, we derive the Fisher Infor-
mation Matrix (FIM) for target UA V sensing under
position uncertainty. Accordingly, to obtain the theoret-
ical lower bound on position estimation accuracy, we
further derive the corresponding CRB matrix, considering
sensing parameters including position vector and complex
Radar Cross Section (RCS).
• Robust Alternative Optimization: We formulate a
long-term CRB minimization problem under position
uncertainty of the target UA V , and design a robust
alternating optimization algorithm for ISAC-enabled
anti-UA V , named AIEA. Speciﬁcally, by developing
Schur complement based generalized Petersen’s sign-
deﬁniteness lemma, we transform the CRB matrix into
a set of semi-deﬁnite constraints. Then, the transmit-
receive ISAC beamforming is decoupled via Lagrangian
relaxation, and the tightness of Semi-Deﬁnite Relaxation
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19613
Fig. 1. The ISAC enabled multi-UA V assisted anti-UA V scenario.
(SDR) is rigorously proved. We design a penalty-based
Successive Convex Approximation (SCA) algorithm to
address the coupled UA V scheduling and CU association,
and prove the effectiveness of AIEA from the perspective
of convergence.
• Performance Validation: We evaluate the performance
of AIEA on Manhattan map and compare it with several
representative algorithms. Evaluation results show that
AIEA achieves effective cooperative sensing of the con-
tinuously moving target UA V , signiﬁcantly outperforming
existing schemes in robustness and sensing accuracy.
The rest of this paper is organized as follows. In Section II,
we present the system model. In Section III, we detail metric
deﬁnitions and formulate the CRB minimization problem. In
Section IV, we design an alternative optimization algorithm to
achieve robust sensing performance. In Section V, we provide
the evaluation of the proposed method. Finally, we conclude
this work in Section VI.
Notations: x, x, X andX denote scalar, vector, matrix and
set, respectively. Operations(·)T and (·)H denote the transpose
and conjugate transpose, respectively. Operations Tr (·) and
vec (·) denote the trace and the vectorization of a matrix,
respectively. Operation ⊗ denotes the Kronecker product of
two matrices. Symbols RM and CM×N denote the set of
M× 1 real-valued vector and M×N complex-valued matrix,
respectively. Expression X≽ 0 denotes that X is a positive
semideﬁnite matrix. Variable a∼CN (µ, Σ) denotes that a
is a complex-valued circularly symmetric Gaussian random
variable with mean µ and covariance matrix Σ.
II. S YSTEM MODEL
In this section, we ﬁrst introduce an ISAC enabled anti-
UA V network model. Following this, channel model, transmit
and received signal model, and power consumption model are
elaborated, respectively.
A. Network Model
As shown in Fig. 1, we consider an ISAC-enabled anti-
UA V system consisting of multiple authorized UA Vs, multiple
mobile CUs, and one target UA V (an unreported “black ﬂight”
UA V). Similar to [11] and [22], by maintaining a connection to
a single low earth orbit satellite through space-air links, coor-
dinated control, scheduling, and clock synchronization within
the UA V group can be facilitated without requiring satellite
handover. Under this coordination, UA Vs are thus capable
Fig. 2. The proposed time slot allocation scheme.
of dual functions: cooperatively positioning a moving target
and providing communication services for single-antenna CUs
by sharing CSI, obtained sensing samples, and basic status
information.
Each UA V is equipped with a transmit Uniform Planar
Array (UPA) of sizeQT =QxT×QyT and a receive UPA of size
QR = QxR× QyR, where QT = QR, and QxT,QyT , QxR,QyR
denote the number of transmit and receive antennas along
the x-axis and y-axis, respectively. To adapt to target UA V’s
characteristics (e.g., small size and low RCS), two-dimensional
beamforming is implemented based on the vertical and hor-
izontal Angle of Departure (AoD), enabling high-precision
positioning and tracking of aerial moving targets. We deﬁne
M ≜{1,··· ,m,··· ,M} andK ≜{1,··· ,k,··· ,K} as
the set of UA Vs and CUs, respectively. The total ﬂight period
T is discretized into N time slots with length δ = T/N ,
which is indexed by N ≜ {1,··· ,n,··· ,N}. Given that
δ is sufﬁciently small, the position of UA Vs and CUs can
be regarded as invariant within a time slot, which facilitates
the design of trajectory and beamforming. We adopt a Three-
Dimensional (3D) Cartesian coordinate system, where the
position of UA V m in time slot n is denoted as pm[n] =
(pxm[n],pym[n],p zm[n]), with (pxm[n],pym[n]) and pzm[n] repre-
sent its horizontal coordinates and ﬂight altitude, respectively.
Similarly, the coordinates of CU k and the target UA V are
denoted as pk[n] = ( pxk[n],pyk[n], 0) and pL[n] = ( pxL[n],
pyL[n],p zL[n]), respectively.
By considering the existence of sensing errors and the
continuous movement, the target UA V exhibits signiﬁcant
position uncertainty at the start of each time slot. Mean-
while, simultaneous transmission-reception design leads to
severe self-interference, and cross-link echoes among UA Vs
also introduce interference, which increases the difﬁculty of
processing sensing echoes for aerial moving target. To address
this, we propose a separated transmitter-receiver design to
improve the accuracy of cooperative sensing and positioning
for the target UA V . As shown in Fig. 2, we divide authorized
UA Vs into two types, i.e., type-1 and type-2 in each time
slot: type-1 UA Vs transmit sensing signals to the target UA V ,
while type-2 UA Vs receive sensing echoes reﬂected by the
target UA V from all type-1 UA Vs. Note that both types of
UA Vs can simultaneously provide communication services for
multiple CUs. Thus, in time slotn, the association relationship
between UA Vs and CUs, and the role of UA Vs are determined
by binary variables αm[n] and βmk[n], respectively. Variable
αmk[n] = 1 indicates that UA V m provides communication
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19614 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
services for CU k, and vice versa. If βm[n] = 1 , UA Vm is
type-1; otherwise, it is type-2.
B. Channel Model
1) Space-Air Channel Model: Similar to [23], the space-
air channel in time slot n is modeled as Rician fading channel
and can be expressed as:
hms[n]=
√ρms
dms [n]
(√ κ
κ + 1hLoSms[n]+
√
1
κ + 1hNLoSms [n]
)
,
(1)
whereρms =G0(ςms/4π)2 withG0 denoting the ﬁxed power
gain, andςms representing the wavelength of the space-air car-
rier frequency; variable dms[n] denotes the distance between
UA Vm and the selected satellite in time slot n; variable κ
denotes the corresponding Rician factor; variable hLoSms [n]∈
CQT is the Line-of-Sight (LoS) component with each element
being a unit complex vector, and hNLoSms [n] ∼ CN(0, IQT )
is the Non-Line-of-Sight (NLoS) component which is a zero-
mean complex Gaussian random vector with a unit covariance
matrix.
2) Air-Ground Channel Model: We assume the communi-
cation channel follows a probabilistic LoS channel model, and
the LoS probability between UA Vm and CU k is given by:
P LoSmk [n] = 11 +ν1 exp (−ν2 (ϕmk [n]−ν1)), (2)
where ν1 and ν2 are constant parameters dependent on the
propagation environment, and variable ϕmk [n] denotes the
dual-angle joint factor between UA V m and CU k, which
is given by equation (7). The NLoS probability is expressed
as P NLoSmk [n] = 1 − P LoSmk [n], and the path losses under
LoS and NLoS conditions can be modeled as ν0dmk [n]−2
andεν0dmk [n]−2, respectively, where ν0 denotes the channel
power gain at reference distance d0 = 1m; variabledmk [n]=
‖pm[n]− pk[n]‖ represents their corresponding distance; and
ε< 1 is an additional attenuation factor caused by the NLoS
condition. Therefore, similar to [24], the air-ground channel
between UA Vm and CU k can be expressed as:
hmk [n] =
√
P LoSmk [n](ν0dmk [n]−2)hLoSmk [n]
+
√
P NLoSmk [n](εν0dmk [n]−2)hNLoSmk [n], (3)
where hLoSmk [n] = aT (θmk [n],ωmk [n]) denotes the LoS
channel component, and hNLoSmk [n] ∼ CN(0, IQT ) denotes
the NLoS component. The transmit steering vector of UA V
m relative to CU k is aT (θmk [n],ωmk [n])∈ CQT , which
is given by equation (4), shown at the bottom of the page.
Variablesς1 andς2 denote the antenna spacing and the carrier
wavelength, respectively. The vertical and horizontal AoD of
UA Vm relative to CU k in time slot n can be expressed as:
θmk [n] = arcsin
( pzm [n]−pzk [n]
||pm [n]− pk [n]||
)
, (5)
ωmk[n] = arccos

 pym [n]−pyk [n]√
(pxm[n]−pxk[n])2+(pym[n]−pyk[n])2

,
(6)
respectively. Then, similar to [25], we deﬁne the dual-angle
joint factor as follows:
ϕmk [n] =θmk [n] (1 +ζ cos (ωmk [n]−ω0)), (7)
where ζ and ω0 denote the horizontal angle weight coefﬁ-
cient and unobstructed horizontal reference angle, respectively,
which are determined by the distribution of obstacles (e.g.,
ω0 = 0 when UA Vm is directly above CU k in the horizontal
direction).
3) Sensing Channel Model: Similar to [26], when UA Vm
serves as a type-2 UA V receiving sensing signals transmitted
by type-1 UA Vm′ and reﬂected by the target UA V , the sensing
channel in time slot n can be modeled as:
Gm′,L,m [n] =ϱm′,L,m [n] Hm′,L,m [n], (8)
aT (θmk [n],ωmk [n]) =
[
1,··· ,e−j2π ς1ς2 sinθmk[n] cosωmk[n],··· ,e−j2π (QxT−1)ς1ς2 sinθmk[n] cosωmk[n]]T
⊗
[
1,··· ,e−j2π ς1ς2 sinθmk[n] sinωmk[n],··· ,e−j2π (QyT−1)ς1ς2 sinθmk[n] sinωmk[n]]T (4)
bT (θm′L [n],ωm′L [n]) =
[
1,··· ,e−j2π ς1ς2 sinθm′ L[n] cosωm′ L[n],··· ,e−j2π (QxT−1)ς1ς2 sinθm′ L[n] cosωm′ L[n]]T
⊗
[
1,··· ,e−j2π ς1ς2 sinθm′ L[n] sinωm′ L[n],··· ,e−j2π (QyT−1)ς1ς2 sinθm′ L[n] sinωm′ L[n]]T (9)
bR (θmL [n],ωmL [n]) =
[
1,··· ,e−j2π ς1ς2 sinθmL[n] cosωmL[n],··· ,e−j2π (QxR−1)ς1ς2 sinθmL[n] cosωmL[n]]T
⊗
[
1,··· ,e−j2π ς1ς2 sinθmL[n] sinωmL[n],··· ,e−j2π (QyR−1)ς1ς2 sinθmL[n] sinωmL[n]]T (10)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19615
where ϱm′,L,m [n] denotes the composite radar path gain that
incorporates the target RCS and two-way path loss, which
is given by ϱm′,L,m [n] = C1‖dm′,L‖−1‖dL,m‖−1 with C1
representing the path loss at the reference distance. The corre-
sponding reﬂection matrix of the target UA V isHm′,L,m [n] =
bR (θmL[n],ωmL[n]) bHT (θm′L[n],ωm′L[n]) ∈ CQR×QT ,
where bT (θm′L[n],ωm′L[n]) ∈ CQT denotes the transmit
steering vector from type-1 UA V m′ to the target UA V , and
bR (θmL[n],ωmL[n]) ∈ CQR denotes the receive steering
vector from type-2 UA Vm to the target UA V , which are given
by equations (9) and (10), shown at the bottom of the previous
page, respectively. The vertical and horizontal Angle of Arrival
(AoA) are given by θm′L [n] and ωm′L [n]; the vertical and
horizontal AoD of UA Vm relative to the target UA V in time
slot n are given by θmL [n] and ωmL [n], respectively, which
can be computed by:
θmL [n] = arcsin
( pzm [n]−pzL [n]
||pm [n]− pL [n]||
)
, (11)
ωmL[n]=arccos

 pym [n]−pyL [n]√
(pxm[n]−pxL[n])2+(pym[n]−pyL[n])2

.
(12)
C. Transmit and Receive Signal Model
Communication and sensing impose distinct performance
requirements on waveforms: communication demands a con-
stant envelope and high data rate, while sensing requires
excellent correlation characteristics. To address this, dedi-
cated waveforms are adopted for each function. To achieve
simultaneous sensing and communication, the transmitted
ISAC signal of UA V m in time slot n can be expressed
as:
xm[n]=
∑
kϵK
αmk[n]wmk[n]sCommk [n]+βm[n]rm[n]sSensm [n],
(13)
where sCommk [n]∼CN (0, 1) denotes the communication signal
transmitted from UA Vm to CU k in time slot n, and variable
wmk [n] ∈ CQT represents the corresponding communication
transmit beamforming vector; sSensm [n] denotes the sensing
signal transmitted from UA V m to the target UA V , with
elements in
{
sSensm [n],∀m} being mutually independent and
each having zero mean and unit variance, and variablerm[n]∈
CQT represents the corresponding sensing transmit beam-
forming vector. The covariance matrix of xm[n] is expressed
as:
Sm[n]=
∑
kϵK
αmk[n]wmk[n]wHmk[n]+βm[n]rm[n]rHm[n]. (14)
Due to the simultaneous transmission of communication
and sensing signals, CUs still suffer from self-interference
and mutual interference from other UA Vs. Thus, the signal
received by CU k in time slot n can be expressed as:
yk [n]
=
∑
mϵM
hHmk [n]αmk[n]wmk [n]sCommk [n]
+
∑
m∈M
∑
k′∈K\{k}
hHmk [n]αmk′ [n] wmk′ [n]sCommk′ [n]
+
∑
m∈M
hHmk [n]βm [n] rm [n]sSensm [n] +vk [n], (15)
where vk[n] ∼ CN(0,σ 2k) is the Additive White Gaussian
Noise (AWGN) at CU k.
Communication signals may interfere with reﬂected echoes.
To improve sensing performance, we extract the sensing
signal by removing the component of the known communi-
cation waveform from the received signal. Existing methods
can eliminate such self-interference, but mutual interference
caused by communication signals transmitted from type-1
UA Vm′ still persists [27]. Thus, we consider the joint design
of separated transmitter-receiver beamforming, and the sensing
echoes received by type-2 UA V m in time slot n can be
expressed as:
ym[n] = uHm[n]( ∑
m′∈M\{m}
Gm′,L,m[n]βm′[n]rm′[n]sSensm′ [n]
+
∑
m′∈M\{m}
∑
k∈K
Gm′,L,m[n]αm′k[n]
wm′k[n]sComm′k[n] + vm[n]), (16)
where variable um [n] ∈ CQR denotes the corresponding
receive beamforming vector and vm [n]∼CN (0,σ 2mIQR) is
the AWGN at type-2 UA Vm.
D. Power Consumption Model
The power consumption of UA V can be decomposed as:
space-air transmission power consumption P SATm [n], which is
given by the proof of Theorem 1 in subsection III-A, air-
ground transmission power consumption P ISACm [n], and ﬂight
power consumption P FLYm [n].
The transmission power consumption of UA Vm in time slot
n (including communication and sensing power consumption)
can be expressed as:
P ISACm [n] =∑
k∈K
αmk[n]‖wmk[n]‖2 +βm[n]‖rm[n]‖2. (17)
Similar to [28], the propulsion power consumption of UA Vm
in time slot n can be expressed as:
P FLYm [n] =P0
(
1 + 3 (Vxym [n])2
U2tip
)
+C0 (Vxym [n])3
+P1


√
1 + (Vxym [n])4
4V 40 − (Vxym [n])22V 20


1
2
+G0V zm [n], (18)
where P0,P 1,Utip,V 0 and C0 denote aerodynamic constants,
and G0 is the weight of the UA V . Horizontal and verti-
cal velocities of UA V m in time slot n are deﬁned as
Vxym [n] = ‖(pxm [n + 1],pym [n + 1])− (pxm [n],pym [n])‖/δ
andV zm [n] =|pzm [n + 1]−pzm [n]|/δ, respectively, which are
assumed to remain constant within each time slot.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19616 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Note that satellites are infrastructure nodes with sufﬁcient
computing and energy resources, whose overhead does not
limit UA V-side cooperation performance or system feasibility.
Therefore, we neglect computing and power consumption of
the satellite in our feasibility analysis.
III. M ETRIC DEFINITION AND PROBLEM FORMULATION
In this section, we introduce metric deﬁnitions of space-air
transmission, air-ground transmission, and sensing. Then, we
formulate a long-term CRB matrix trace minimization problem
in the ISAC enabled anti-UA V system.
A. Metric Deﬁnition
For space-air transmission, we ﬁrst derive the probability of
transmission outage event, and then prove that there exists an
optimal transmit power for a given tolerable transmission out-
age probability. For air-ground transmission, SINR is adopted
as the communication performance metric. For multi-UA V
cooperative sensing, we derive the FIM of the target UA V
and employ CRB as the sensing performance metric.
1) Space-Air Transmission Metric: Similar to [11], since
space-air transmission and air-ground transmission operate
in the Ka-band and V-band, respectively, such inter-layer
interference can be reasonably neglected, allowing us to focus
on multi-UA V cooperative sensing. The Signal-to-Noise Ratio
(SNR) of the space-air transmission between the satellite and
UA Vm is given by:
γm [n] = P SATm [n]‖hms [n]‖2σ2m [n] , (19)
where P SATm [n] is the transmit power from UA V m to the
satellite in time slot n, and σ2m [n] is the power of the AWGN
at UA Vm. To ensure reliable decoding of information at the
selected satellite, the SNR of the space-air transmission in time
slot n should exceed predeﬁned threshold Γreqm .
Theorem 1: Due to the uncertainty of the NLoS component
in space-air channel hms [n], transmission outage events occur
with a non-zero probability, which is given by:
Pr{γm [n]≤ Γreqm}
= Pr
{
‖hms [n]‖2≤ Γreqmσ2m [n]P SATm [n] }
= 1−MQT
(
√
2κQT,
√
2Γreqmσ2m [n]d2ms [n] (κ + 1)
ρmsP SATm [n]
)
.
(20)
The proof of Theorem 1 is provided in Appendix A.
Corollary 1: For a given tolerable transmission outage
probability ϵm[n] of UA V m in time slot n, there exists
a unique optimal transmit power P SATm [n] for the space-air
link of UA V m, which minimizes the transmit power while
satisfying Pr
{
γm[n]≤ Γreqm}≤ϵm[n].
The proof of Corollary 1 is provided in Appendix B.
2) Air-Ground Transmission Metric: Similar to [5] and [8],
the SINR of CU k in time slot n is given by:
γk[n] = P Ck [n]P Uk [n] +P Sk [n] +σ2k[n], (21)
where variable P Ck [n] = ∑m∈Mαmk[n]⏐⏐hmk[n]Hwmk[n]⏐⏐2
is the power of the desired communication signal; variable
P Uk [n] = ∑m∈M∑k′∈K\{k}αmk′[n]⏐⏐hmk[n]Hwmk′[n]⏐⏐2
is the multi-user interference; and variable P Sk [n] =∑
m∈Mβml[n]
⏐⏐hmk[n]Hrml[n]⏐⏐2 is the interference from
sensing signals.
3) Sensing Metric: We restructure sensing signals received
by type-2 UA Vm in time slot n to facilitate the derivation of
CRB for multi-UA V cooperative sensing by rewriting equation
(16) as:
ym[n]= uHm[n]

 ∑
m′∈M\{m}
Gm′,L,m[n]xm′[n]+vm[n]

, (22)
where xm′ [n] = ∑k∈Kαm′k [n] wm′k [n]sComm′k [n] +
βm′ [n] rm′ [n]sSensm′ [n] denotes the signal transmitted by
type-1 UA Vm′, and its covariance matrix is given by:
Sm′[n] =
∑
m′∈M\{m}
αm′k[n]wm′k[n]wHm′k[n]
+βm′[n]rm′[n]rHm′[n]. (23)
Due to the continuous mobility of the target UA V and errors
in sensing-based estimation, accurate position coordinates of
the target UA V cannot be consistently obtained, giving rise to
inevitable position uncertainty. Thus, similar to [29], we adopt
a bounded uncertainty model with deterministic constraints,
which can be expressed as:
pL [n] = pL [n] + ∆pL [n], (24)
where vector pL[n] ≜ [pxL[n],pyL[n],pzL[n]]T denotes the
estimated position of the target UA V in time slot n, and
vector ∆pL[n] ≜ [∆pxL[n], ∆pyL[n], ∆pzL[n]]T represents the
positioning error, while |∆pxL[n]|≤ λxL[n],|∆pyL[n]|≤ λyL[n]
and |∆pzL[n]| ≤ λzL[n]. Thus, for i ∈ {x,y, z}, position
uncertainty region of the target UA V can be expressed as:
ΩL[n] ≜
{
(∆pxL[n], ∆pyL[n], ∆pzL[n])||∆piL[n]|≤λiL[n]}.
(25)
The sensing parameter vector to be estimated for the target
UA V in time slotn can be expressed as:
S [n] =
[
pTL[n],ϱTm[n]]T, (26)
where ϱm[n]∈ C2M represents the complex reﬂection coef-
ﬁcient vector related to the target UA V extracted from the
sensing echoes received by type-2 UA V m, which is given
by:
ϱm [n] = [ℜ{ϱ1,L,m [n]},ℑ{ϱ1,L,m [n]},···
ℜ{ϱM,L,m [n]},ℑ{ϱM,L,m [n]}]T, (27)
where ℜ{ϱ1,L,m[n]} denotes the real part of the complex
reﬂection coefﬁcient extracted from the sensing signal trans-
mitted by type-1 UA V 1, reﬂected by the target UA V , and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19617
received by type-2 UA V m, while ℑ{ϱ1,L,m[n]} denotes its
corresponding imaginary part.
Theorem 2: We deﬁne matrix Fm [n]∈ C(2M+3)×(2M+3)
as the FIM for target UA V sensing parameter S[n]. If UA Vm
serves as a type-2 UA V to receive all sensing echoes reﬂected
by the target UA V , element(i,j ) of Fm [n] is given by:
F (i,j)m [n] = 2σ2mℜ{vec(BHm[n])ψ(i,j)m [n]}, (28)
where beamforming association matrix Bm[n] =
uHm[n]um[n]Sm′[n]∈ CMQ T×MQ T , and sensing association
vectorψ(i,j)m [n] = vec( ˙G(j)HL,m [n] ˙G(i)L,m[n])∈ CM2Q2T .
The proof of Theorem 2 is provided in Appendix C.
Then, similar to [30], we partition Fm [n] into:
Fm [n] =

 F(m)pLpL [n] F(m)pLϱm [n][
F(m)pLϱm [n]]T F(m)ϱmϱm [n]

, (29)
where matrix F(m)pLpL [n]∈ R3×3 is the sub-block of Fm [n]
related to pL [n], and the corresponding CRB matrix based on
the observation sample ~ym [n] is given by:
CRBm(pL[n])
=
[
F(m)pLpL[n]− F(m)pLϱm[n]F(m)−1ϱmϱm[n]F(m)TpLϱm[n]]−1. (30)
Following this, the CRB for estimating the position of the
target UA V in time slotn is given by:
CRBm(piL[n]) =(CRBm(pL[n]))(j,j), j∈{ 1, 2, 3},
(31)
where diagonal elements of matrix CRBm(pL[n]) represent
the variances of parameters corresponding to position coordi-
nates
{
piL[n],i∈{x,y, z}} of the target UA V .
B. Problem Formulation
To achieve robust cooperative sensing performance of the
proposed anti-UA V system while accounting for the position
uncertainty of the target UA V (i.e., ∆pL[n] ∈ ΩL[n]), our
objective is to minimize the time-averaged trace of CRB
by jointly optimizing communication beamforming wmk[n],
sensing beamforming rm[n], receive beamforming um[n],
CU association αmk[n], UA V scheduling βm[n], and ﬂight
trajectory pm[n]. By deﬁningWmk ={wmk[n]}n∈N ,Rm =
{rm[n]}n∈N ,Um = {um[n]}n∈N ,Amk = {αmk[n]}n∈N ,
Bm ={βm[n]}n∈N ,Pm ={pm[n]}n∈N , the corresponding
long-term optimization problem is formulated as:
P 1 : minimize
Wmk,Rm,Um,
Amk,Bm,Pm
max
∆pL[n]∈ΩL[n]
1
N
∑
n∈N
Tr
(
CRB(pL[n])
)
,
(32)
s.t. P ISACm [n]≤P tx,∀n∈N , (32a)
P SATm [n] +P ISACm [n] +P FLYm [n]≤P max, (32b)
γk [n]≥ Γreqk ,∀k∈K,n∈N , (32c)
αmk [n]∈{ 0, 1},∀m∈M,k∈K,n∈N ,
(32d)∑
m∈M
αmk [n]≤ 1,∀k∈K,n∈N , (32e)
βm [n]∈{ 0, 1},∀m∈M,n∈N , (32f)∑
m∈M
(1−βm [n])≥ 1,∀n∈N , (32g)
‖(pxm[n+1],pym[n+1])−(pxm[n],pym[n])‖
δ
≤V maxxy , (32h)
|pzm [n + 1]−pzm [n]|
δ ≤V maxz ,∀n∈N , (32i)
hmin≤pzm [n]≤hmax,∀n∈N , (32j)
where Tr (CRB (pL [n])) denotes the trace of the CRB matrix
for multi-UA V cooperative sensing in time slot n, given by:
Tr(CRB(pL[n]))=
∑
m∈M
(1−βm[n]) Tr(CRBm(pL[n])).
(33)
Speciﬁcally, in time slot n, constraints (32a) and (32b)
denote P tx as the transmit power limit and P max as the
total power consumption budget of UA V m, respectively;
constraint (32c) guarantees the SINR requirement of CU
k; constraints (32d) and (32e) ensure the validity of the
association relationship between UA Vs and CUs, where each
CU can communicate with at most one UA V; constraints
(32f) and (32g) regulate the role of UA Vs, requiring that at
least one type-2 UA V is assigned to receive sensing echoes;
constraints (32h), (32i), and (32j) impose constraints on UA V
ﬂight trajectories.
Theorem 3: ProblemP 1 is a Mixed-Integer Nonlinear Non-
convex Programming (MINNP) that is NP-hard.
The proof of Theorem 3 is provided in Appendix D.
IV. P ROPOSED SOLUTION
Since ProblemP 1 is NP-hard and involves multiple strongly
coupled variables, which are deeply coupled with the nonlinear
characteristics of time-varying probabilistic LoS channels,
existing algorithms cannot directly yield effective solutions.
To address this challenge, we ﬁrst leverage Schur complement
to transform the high-dimensional, structurally complex CRB
matrix into a set of semi-deﬁnite constraints. Then we resolve
the position uncertainty of the target UA V by applying gen-
eralized Petersen’s sign-deﬁniteness lemma. Subsequently, we
decompose the resulting SDP problem into three subproblems:
joint transmit-receive beamforming design, joint user associa-
tion and UA V scheduling design, and UA V trajectory design.
To solve these subproblems efﬁciently, we adopt Lagrangian
relaxation, SDR, and penalty-based SCA, respectively. Finally,
an alternating iterative strategy is employed to coordinate the
solution of these subproblems, and the effectiveness of the pro-
posed algorithm is theoretically proven from the perspective
of convergence.
A. Problem Reformulation and Uncertainty Resolution
First, we address the complex form of the CRB matrix in
the optimization objective. Since function Tr
(
X−1) decreases
over the space of positive semi-deﬁnite matrices [31], we
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19618 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
introduce auxiliary optimization variables Jm [n]∈ C3×3≽ 0
andQ ={Θ[n]≥ 0}n∈N , and reformulate Problem P 1 as:
P 1′ : minimize
Wmk,Rm,Um,
Amk,Bm,Pm,Q
1
N
∑
n∈N
Θ [n], (34)
s.t. Jm [n]≽ 0, (34a)∑
m∈M
(1−βm [n])Tr
(
J−1m [n])≤ Θ [n], (34b)
Constraints (32a)− (32j), (34c),
where constraint (34c), shown at the bottom of the page.
Due to the product of submatrices and the position uncer-
tainty of the target UA V , constraint (34c) remains non-convex.
Therefore, we apply Schur complement [32] to transform it
equivalently into the following form:

F(m)pLpL[n]−Jm[n] F(m)pLϱm[n][
F(m)pLϱm[n]]T F(m)ϱmϱm[n]

≽0, ∆pL[n]∈ΩL[n].
(35)
Next, we address the uncertainty in constraint (35). Observ-
ing equation (28), we can ﬁnd that uncertainty stems from
sensing association vector ψ(i,j)m [n], which is nonlinear with
respect to ∆pL [n]. Therefore, we approximate ψ(i,j)m [n] by
the ﬁrst-order Taylor expansion, which is given by:
ψ(i,j)m [n] =ψ(i,j)m [n] + ˙ψ(i,j)m,Lx [n] ∆pxL [n]
+ ˙ψ(i,j)m,Ly [n] ∆pyL [n] + ˙ψ(i,j)m,Lz [n] ∆pzL [n],
(36)
where ψ
(i,j)
m [n] refers to the estimated value of ψ(i,j)m [n] at
position pL[n], while ˙ψ(i,j)m,Lx [n], ˙ψ(i,j)m,Ly [n], and ˙ψ(i,j)m,Lz [n]
represent the derivatives of ψ(i,j)m [n] with respect to pxL [n],
pyL [n], and pzL [n], respectively.
Then, based on the linear term of the Taylor expansion,
we deﬁne vector ∆ψ(i,j)m [n] and its upper bound, which
is given by equation (37) and (38), shown at the bot-
tom of the page, respectively, where ξ(i,j)m [n] is deﬁned
as the error bound induced by the position uncertainty
in time slot n. Then, we decompose the variation of
sensing association matrix ∆ψ(i,j)m into real-valued vector
∆~ψ(i,j)m [n] in its standard form by deﬁning ∆~ψ(i,j)m [n] =[
ℜ
{
∆ψ(i,j)m [n]}T,ℑ{∆ψ(i,j)m [n]}T]T ∈ R6M2Q2T . Sim-
ilarly, we deﬁne ~Bm [n] ≜ vec (Bm [n]) ∈ RM2Q2T ,
Bm [n] ≜ [1, 1, 1]T ⊗ ~Bm [n] ∈ R3M2Q2T , and Bm [n] ≜{
ℜ
{
Bm [n]
}T
, ℑ
{
Bm [n]
}T}T
∈ R6M2Q2T to transform
beamforming association matrix Bm [n].
Thus, we can rewrite the elements of the FIM in equation
(28) as:
F (i,j)m = 2σ2m(ℜ{~BHm[n]ψ(i,j)m [n]} +ℜ{BHm[n]ψ(i,j)m [n]})
= 2σ2m(ℜ{~BHm[n]ψ(i,j)m [n]} +ℜ{BHm[n]~ψ(i,j)m [n]}).
(39)
Next, we substitute equation (39) into constraint (35) to obtain:
(
Fm[n]−
[
Jm[n]0
0 0
])
≽−∆Fm[n], ∆pL[n]∈ΩL[n], (40)
where element (i,j ) of matrices Fm[n] and ∆Fm[n] are
2
σ2mℜ
{
~BHm[n]ψ(i,j)m [n]} and 2σ2mℜ{BHm[n]~ψ(i,j)m [n]}, respec-tively. Subsequently, we leverage the following lemma [33] to
handle the uncertainty contained in elements of FIM.
Lemma 1: (Generalized Petersen’s Sign-deﬁniteness
Lemma) For given matrices D and {Mi, Zi}Ni=1, semi-
inﬁnite linear matrix inequality:
D≽
N∑
i=1
(
MHi PiZi + ZHi PHi Mi
)
, ∀i, Pi :‖Pi‖≤ℵ i,
(41)
is valid if and only if there exists non-negative real numbers
ϵ1,...,ϵ N satisfying:

D−∑Ni=1ϵiZHi Zi−ℵ1MH1 ... −ℵNMHN
−ℵ1M1 ϵ1I ... 0
... ... ... ...
−ℵNMN 0 ... ϵ NI

≽0. (42)
Based on Lemma 1, term −∆Fm [n] in equation (40) is
reformulated as equation (43), shown at the bottom of the
next page, where matrix M(i,j) [n]∈ R6M2Q2T×(2M+3), and
column i of M(i,j) [n] is Bm [n], while all other column
elements are 0; vector z(i,j) [n]∈ R1×(2M+3), and if i = j,
element i of z(i,j) [n] is −1/2; otherwise, element i of
z(i,j) [n] is−1, while all other elements of z(i,j) [n] are 0.
Then, we introduce auxiliary variable Em =
{
ϵ(i,j)m [n] ≥
0
}
n∈N, (i,j ) ∈ { (i,j )|i,j ∈M,j ≥i}, and applyLemma 1 into equation (40) to obtain:
[
D [n]− Z [n] MH [n]
M [n] T [n]
]
≽ 0, (44)
(
F(m)pLpL [n]− F(m)pLϱm [n][F(m)ϱmϱm [n]]−1[F(m)pLϱm [n]]T− Jm [n])≽ 0, ∀m∈M,n∈N , ∆pL [n]∈ ΩL [n] (34c)
∆ψ(i,j)m =[[ ˙ψ(i,j)m,Lx [n]]T ∆pxL [n],[ ˙ψ(i,j)m,Ly [n]]T ∆pyL [n],[ ˙ψ(i,j)m,Lz [n]]T ∆pzL [n]]T∈ R3M2Q2T (37)
‖∆ψ(i,j)m [n]‖ =(‖ ˙ψ(i,j)m,Lx [n]‖2(∆pxL [n])2 +‖ ˙ψ(i,j)m,Ly [n]‖2(∆pyL [n])2 +‖ ˙ψ(i,j)m,Lz [n]‖2(∆pzL [n])2) 12
≤
(
‖ ˙ψ(i,j)m,Lx [n]‖2(λxL [n])2 +‖ ˙ψ(i,j)m,Ly [n]‖2(λyL [n])2 +‖ ˙ψ(i,j)m,Lz [n]‖2(λzL [n])2) 12 ≜ξ(i,j)m [n] (38)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19619
where D [n]− Z [n] = Fm [n]−
[Jm [n] 0
0 0
]
, and matrices
Z [n], M [n], and T [n] are given by equations (45)–(47),
shown at the bottom of the page.
Z [n] =
∑
i,j
ϵ(i,j)m [n][z(i,j) [n]]H z(i,j) [n]. (45)
Finally, we can reformulate Problem P 1′ as follows:
P 1′′ : minimize
Wmk,Rm,Um,
Amk,Bm,Pm,Q,Em
1
N
∑
n∈N
Θ [n], (48)
s.t. Constraints (32a)−(32j), (34a), (34b), (44).
However, ProblemP 1′′ still involves multiple strongly coupled
variables: beamforming vectors Wmk,Rm, and Um, binary
variables Amk and Bm, as well as UA V trajectory Pm.
In addition, various non-convex constraints (including power
budget and SINR requirements) are also deeply coupled with
nonlinear time-varying channels, rendering direct joint opti-
mization nearly infeasible. Therefore, we decompose Problem
P 1′′ into the following three subproblems and solve them
iteratively.
B. Joint Transmit-Receive Beamforming Design
We optimize beamforming vectors Wmk,Rm, andUm for
given CU associationAmk, UA V schedulingBm and trajectory
Pm by formulating the following problem:
P 2 : minimize
Wmk,Rm,Um,
Q,Em
1
N
∑
n∈N
Θ [n], (49)
s.t. Constraints (32a)−(32c), (34a), (34b), (44).
However, the joint optimization of Wmk, Rm, and Um
involves complex interdependencies. In addition, power con-
straints (32a) and (32b), as well as SINR requirement (32c),
further exacerbate non-convexity and solution complexity. To
address this, we decompose Problem P 2 into subproblems:
ProblemP 2.1 for solving transmit beamforming vectorsWmk
andRm, and Problem P 2.2 for solving receive beamforming
vector Um. By adopting Lagrangian relaxation and SDR,
we gradually transform Problem P 2 into a tractable convex
problem and approach the optimal solution through multiple
alternating iterations.
1) Transmit Beamforming Optimization: We deﬁne com-
munication transmit beamforming, sensing transmit beam-
forming, and communication channel matrices as Wmk [n] ≜
wmk [n] wHmk [n], Rm [n] ≜ rm [n] rHm [n], and Hmk [n] ≜
hmk [n] hHmk [n]. Thus, equation (14) can be rewritten as:
Sm′ [n] =
∑
kϵK
αm′k [n] Wmk [n] +βm′ [n] Rm′ [n]. (50)
Similarly, constraints (32a), (32b), and (32c) can be rewritten
as (51a), (51b), and (51c), respectively. We substitute equation
(50) into constraint (44) to transform the latter into a convex
form with respect toWmk andRm. Then we optimize transmit
beamforming by formulating the following problem:
P 2.1 : minimize
Wmk,Rm,Q,Em
1
N
∑
n∈N
Θ [n], (51)
s.t. P ISACm (Wmk [n], Rm [n])≤P tx, (51a)
P SATm [n] +P ISACm (Wmk[n], Rm[n])
+P FLYm [n]≤P max, (51b)
γk (Wmk [n], Rm [n])≥ Γreqk , (51c)
Rank (Wmk [n]) = Rank (Rm [n]) = 1,
(51d)
Constraints (34a), (34b), (44),
where rank-one constraint (51d) ensures that Wmk[n] and
Rm[n] can equivalently recover wmk[n] and rm[n]. Then,
we adopt Lagrangian relaxation to decouple constrains
(51a)–(51c) by introducing multipliers υIm[n]≥ 0,υIIm[n]≥ 0,
and υk[n]≥ 0. Thus, we can reformulate Problem P 2.1 as:
P 2.1′ : minimize
Wmk,Rm,Q,Em
1
N
∑
n∈N
Θ[n]+L[n], (52)
s.t. Constraints (34a), (34b), (44), (51d),
where Lagrangian function termL[n] =L1[n]+L2[n]+L3[n],
elements of which are given by equations (53)–(55), shown
at the bottom of the next page. Note that multipliers can be
updated by a dual ascent method.
Despite this, Problem P 2.1′ is still non-convex due to
constraint (51d). Thus, we relax and transform it into convex
Problem P 2.1′′ by leveraging SDR technique, which can be
efﬁciently solved by convex optimization solvers. We prove
the tightness of the rank relaxation by the following theorem.
Theorem 4: Based on obtained solutionsW∗mk,R∗m,Q∗, and
E∗m to convex Problem P 2.1′′, there exist equivalent solutions~W∗mk, ~R∗m, ~Q∗, and ~E∗m that achieve the same objective value
of Problem P 2.1′ and satisfy constraint (51d).
−∆Fm[n]=
∑
i,j
([
M(i,j)[n]]H ∆~ψ(i,j)m [n]z(i,j)[n]+[z(i,j)[n]]H[∆~ψ(i,j)m [n]]HM(i,j)[n]),i,j ∈{ 1,..., 2M + 3} (43)
M [n] =
[
−ξ(1,1)m [n][M(1,1) [n]]H,..., −ξ(i,j)m [n][M(i,j) [n]]H,..., −ξ(2M+3,2M+3)m [n][M(2M+3,2M+3) [n]]H]T (46)
T [n] = diag
{[
ϵ(1,1)m [n],...,ϵ (i,j)m [n],...ϵ (2M+3,2M+3)m [n]]}⊗ I6M2Q2T (47)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19620 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
The proof of Theorem 4 is provided in Appendix E.
2) Receive Beamforming Optimization: It can be observed
that power constraints (32a) and (32b), and SINR requirement
(32c) depend only on transmit beamforming vectors Wmk
and Rm. Consequently, we can optimize Um by solving
Problem P 1 without constraints (32a)–(32c). Similarly, we
deﬁne receive beamforming matrix Um[n] ≜ um[n]uHm[n] and
substitute it into constraint (44) to transform it into a convex
form. Then we optimize receive beamforming by formulating
the following problem:
P 2.2 : minimize
Um
1
N
∑
n∈N
Θ [n], (56)
s.t. Rank (Um [n]) = 1, (56a)
Constraints (34a), (34b), (44),
where rank-one constraint (56a) ensures that Um[n] obtained
by Problem P 2.2 can equivalently recover um[n].
However, Problem P 2.2 remains non-convex due to the
existence of constraint (56a). To address this, we relax
and transform it into convex Problem P 2.2′ by leveraging
SDR technique, which can be efﬁciently solved via convex
optimization solvers. Similarly, the existence of a rank-one
solution to convex Problem P 2.2′ can be proven following
the steps outlined in Theorem 4.
C. Joint CU Association and UAV Scheduling Design
Given beamforming vectors Wmk,Rm, and Um obtained
from Problem P 2, and ﬁxed UA V trajectoryPm, we optimize
CU association variable Amk and UA V scheduling variable
Bm by formulating the following problem:
P 3 : minimize
Amk,Bm
1
N
∑
n∈N
Θ [n], (57)
s.t. Constraints (32a)− (32g), (34a), (34b), (44).
However, Problem P 3 is non-convex and intractable due
to binary integer variables Amk andBm. To address this, we
relax discrete variables into continuous ones by reconstructing
binary constraints (32d) and (32f) as:
∑
m∈M
∑
k∈K
(
αmk[n]−α2mk[n])≤ 0, 0≤αmk[n]≤ 1, (58)
∑
m∈M
(
βm[n]−β2m[n])≤ 0, 0≤βm[n]≤ 1. (59)
However, constraints (58) and (59) remain non-convex. Thus,
we employ a penalty function to incorporate them into the
objective function of Problem P 3 and reformulate it as:
P 3′ : minimize
Amk,Bm
1
N
∑
n∈N
Θ [n] +F [n], (60)
s.t. Constraints (32a)− (32c),
(32e), (32g), (34a), (34b), (44),
and the penalty function term is given by:
F [n] =µα [n]
∑
m∈M
∑
k∈K
(
αmk[n]−α2mk[n])
+µβ [n]
∑
m∈M
(
βm[n]−β2m[n]), (61)
whereµα[n] andµβ[n] denote penalty factors corresponding to
constraints (58) and (59), respectively. Then, we can obtain the
relationship between Problem P 3 and Problem P 3′ according
to the following theorem:
Theorem 5: If the optimal solutions of Problem P 3′ are CU
association variable A(t)mk and UA V scheduling variableB(t)m
when penalty factors areµα =µ(t)α andµβ =µ(t)β , limit points
Amk andBml of sequences
{
µ(t)α } and{µ(t)β } are the optimal
solution of Problem P 3 when µα→∞ and µβ→∞ .
Please refer to Appendix G for the proof of Theorem 5.
According to Theorem 5, we merely need to obtain the
optimal solution of Problem P 3′. We apply successive con-
vex approximation technique to handle the non-convexity in
penalty terms of Problem P 3′. Given the solution obtained in
iteration t− 1, the optimization problem in iteration t is:
P 3′′ : minimize
Amk,Bm
1
N
∑
n∈N
Θ [n] +F(t) [n], (62)
s.t. Constraints (32a)− (32c),
(32e), (32g), (34a), (34b), (44),
where the penalty function term in iteration t is given by:
F(t)[n]
=µβ[n]
∑
m∈M
(
1− 2β(t−1)m [n])βm[n] +(β(t−1)m [n])2
+µα[n]
∑
m∈M
∑
k∈K
((
1−2α(t−1)mk [n])αmk[n] +(α(t−1)mk [n])2).
(63)
L1 [n] =
∑
m∈M
υIm [n]
(∑
k∈K
αmk [n] Tr (Wmk [n]) +βm [n] Tr (Rm [n])−P tx
)
(53)
L2 [n] =
∑
m∈M
υIIm [n]
(
P SATm [n] +∑
k∈K
αmk [n] Tr (Wmk [n]) +βm [n] Tr (Rm [n]) +P FLYm [n]−P max
)
(54)
L3[n]=
∑
k∈K
vk[n]
[∑
m∈M
( ∑
k′∈K\{k}
αmk′[n]Tr(Hmk[n]Wmk′[n])
+βm[n]Tr(Hmk[n]Rm[n])−αmk[n]Γreqk Tr(Hmk[n]Wmk[n]))+σ2k] (55)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19621
Consequently, ProblemP 3′′ exhibits convexity with regard to
binary variablesAmk andBm, which can be addressed via a
standard convex optimization solver.
D. UAV Trajectory Design
Given beamforming vectors Wmk,Rm, and Um obtained
from Problem P 2, association scheduling variables Amk and
Bm obtained from Problem P 3, we optimize UA V trajectory
Pm by formulating the following problem:
P 4 : minimize
Pm
1
N
∑
n∈N
Θ [n], (64)
s.t. Constraints (32b), (32c), (32h)− (32j),
(34a), (34b), (44).
However, due to the probabilistic LoS channel model, transmit
steering vector amk [n] is complex and nonlinear with respect
to UA V trajectoryPm, rendering Problem P 4 intractable to
solve directly. Besides, strong coupling exists among ﬂight
power consumption terms and non-convex constraints (32b),
(32c), and (44).
To mitigate this complexity, we approximate transmit steer-
ing vectors in iteration t + 1 using UA V trajectories from
iteration t. Therefore, approximated communication channel
~hmk [n] and channel matrix ~Hmk [n] can be expressed as:
~hmk[n] =d−1mk[n](√(P LoSmk [n])(t)ν0(hLoSmk[n])(t)
+
√(
P NLoSmk [n])(t)εν0hNLoSmk [n]) =d−1mk[n]h′mk[n],
(65)
~Hmk [n] =𝓁−1mk [n]H′mk [n], (66)
respectively, where the squared corresponding distance
𝓁mk[n] = ( pxm[n]−pxk[n])2 + ( pym[n]−pyk[n])2 +
(pzm[n]−pzk[n])2. Next, we substitute equation (66) into
constraint (32c) and rewrite it as:
− Γreqk
( ∑
m∈M
∑
k′∈K\{k}
αmk′ [n] Tr (H′mk [n] Wmk′ [n])
+
∑
m∈M
βm [n] Tr (H′mk [n] Rm [n])−𝓁mk [n]σ2k
)
+
∑
m∈M
αmk [n] Tr (H′mk [n] Wmk [n])≥ 0. (67)
Similarly, we resolve the non-convex terms related to the
trajectory in constraint (44) by deﬁning the approximated
sensing channel matrix and rewrite sensing association vector
deﬁned in equation (28) as:
~ψ(i,j)m [n] =𝓁−1m′,L,m [n]ψ(i,j)m [n], (68)
where 𝓁m′,L,m[n] = d2m′,L[n]d2L,m[n]. However, d2L,m[n] is a
quadratic function of trajectory pm [n] of type-2 UA Vm, ren-
dering 𝓁−1m′,L,m[n] a non-convex function. To address this, we
introduce slack variable Xm =
{
χm[n]≈ 𝓁−1m′,L,m[n]}n∈N ,
and perform a ﬁrst-order Taylor expansion on 𝓁−1m′,L,m[n] at
p(t)m [n] by the following constraint:
χm[n]≤ 1𝓁(t)m′,L,m[n] + 2d2m′,L[n](𝓁(t)m′,L,m[n])2
×
∑
k=x,y,z
(
pkt [n]−(pkm)(t) [n])(pkm[n]−(pkm)(t) [n]). (69)
Following this, we can rewrite constraint (44) as:
[~D [n]− Z [n] MH [n]
M [n] T [n]
]
≻0, (70)
where element (i,j ) of ~Fm [n] is 2σ2mℜ{~BHm [n]~ψ(i,j)m [n]}.To handle the non-convexity term in constraint (32b), we
introduce slack variable Vm =
{
ϑm [n]≥ 0
}
n∈N , and deﬁne
ϑ2m [n] =
√
1 + (V xym [n])44V 40 − (V xym [n])22V 20 , which is equivalent to
1
ϑ2m[n] = ϑ2m [n] + (V xym [n])2V 20 , where fraction 1ϑ2m[n] is convex
with respect to ϑm [n], and ϑ2m [n] + (V xym [n])22V 20 is jointlyconvex with respect to {pxm [n],pym [n],ϑm [n]}. Therefore,
givenpxm(t) [n],pym(t) [n] and ϑ(t)m [n], we have:
1
ϑ2m[n]≤ 2 (Vxym )(t) [n]V 20 (Vxym [n]−(Vxym )(t) [n])+(ϑ(t)m [n])2
+ 2ϑ(t)m [n](ϑm[n]−ϑ(t)m [n]) +
(
(Vxym )(t) [n])2
2V 20 .
(71)
Then, we substitute P1
(√
1 + (V xym [n])44V 40 − (V xym [n])22V 20 ) 12 in
constraint (32b) by P1ϑm [n], and rewrite it as:
P SATm [n] +P0
(
1 + 3 (Vxym [n])2
U2tip
)
+P1ϑm [n]
+C0 (Vxym [n])3 +G0V zm [n] +P ISACm [n]≤P max. (72)
Finally, Problem P 4 is transformed into a convex problem
regarding trajectoryPm as follows:
P 4′ : minimize
Pm,Xm,Vm
1
N
∑
n∈N
Θ [n], (73)
s.t. Constraints (32h)− (32j),
(34a), (34b), (67), (69)− (72),
which is solvable via a standard convex optimization solver.
Then, we perform the theoretical analysis of the computational
complexity and convergence of our designed algorithm. In
AIEA, we leverage the interior point method to solve all sub-
problems (Problems P 2-P 4), and the computational complex-
ity of each problem is given by O
(
(MKN )2Q3T log(1/ε)),
O
(
(MKN )3 log(1/ε)), and O((MN )3 log(1/ε)), respec-
tively, where ε denotes the convergence tolerance. Conse-
quently, the total complexity of AIEA can be expressed as
O
((
(MKN )2Q3T + (MKN )3 + (MN )3) log(1/ε)).
Theorem 6: The convergence of AIEA can be guaranteed.
The proof of Theorem 6 is provided in Appendix G.
V. P ERFORMANCE EVALUATION
As illustrated in Fig. 3(a), the performance of AIEA is
validated on the Manhattan map with an area of 500 m×700 m
indicated by red line. We consider an ISAC enabled anti-UA V
system supported by 4 authorized UA Vs, 5 CUs and one target
UA V , where CUs are randomly distributed at the beginning of
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19622 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE II
SIMULATION PARAMETERS
each time slot and move along roads based on the Manhattan
mobility model [34]. Each authorized UA V is equipped with 2
UPA featuring 4 antennas. Unless otherwise stated, the settings
of simulated parameters are based on [27] and [35], which can
be found in Table II. Furthermore, we assess AIEA against ﬁve
representative solutions:
• Multi-BS cooperative Sensing (MBS) [5]: Multiple BSs
collaboratively perform sensing tasks for one target UA V .
Without robust design accounting for position uncertainty,
this algorithm focuses on maximizing sensing perfor-
mance at the received BS by jointly optimizing both
transmit and receive beamforming vectors.
• Connected UA V assisted Sensing (CUS) [8]: One BS with
a connected UA V is employed to perform cooperative
sensing tasks for multiple targets. Without association
scheduling, this algorithm jointly optimizes transmit
beamforming vectors and trajectory of the connected
UA V , aiming to maximize the communication data rate.
• Zero-Forcing beamforming (ZF) [36]: This algorithm uti-
lizes a conventional zero-forcing beamforming scheme to
suppress interference among CUs. It focuses on eliminat-
ing inter-user interference with a ﬁxed linear strategy and
does not consider robustness against location uncertainty.
• Random Association (RA): This baseline establishes
associations with CUs in a random manner, while both
the beamforming scheme and UA V scheduling follow the
same design as our proposed method.
• Random Scheduling (RS): This baseline randomly adopts
type-1 and type-2 scheduling, while keeping the joint
optimization of beamforming, association, and trajecto-
ries consistent with our algorithm.
Fig. 3(b) depicts the 3D optimized trajectories of UA Vs via
AIEA. Speciﬁcally, UA V3 ﬁrst targets CU3, with a directional
communication beam covering the user. Then, it serves CU4
and CU5 by leveraging its high-altitude advantage. Along the
trajectory near the target UA V , it transmits signals via sensing
Fig. 3. Performance of trajectories: (a) The city map of Manhattan and
(b) 3D Optimized trajectories via AIEA.
Fig. 4. Sensing performance with varying parameters: (a) Number of iterations
and (b) Initial position uncertainty of the target UA V .
beamforming while maintaining continuous communication
service. UA V2 adopts a low altitude and ﬂies near the target
UA V while ensuring communication with CU1. Through short
reciprocating maneuvers, it captures reﬂected echoes efﬁ-
ciently with a high-gain receive beam. Based on the trajectory
planning, UA Vs achieve precise beamforming-task matching,
balancing the accuracy of sensing beams, echo capture of
receiving beams, and user coverage of communication beams
to enable efﬁcient execution of ISAC-based anti-UA V tasks.
Fig. 4(a) illustrates the convergence characteristics of the
trace of CRB versus the number of iterations under differ-
ent SINR requirements and initial position uncertainties. A
comparison of the three curves shows that stringent com-
munication requirements degrade the positioning accuracy. A
smaller initial position uncertainty leads to faster algorithm
convergence and a higher ﬁnal positioning accuracy. Overall,
the iterative process progressively enhances the positioning
accuracy. Notably, all curves converge and stabilize within 5
iterations, demonstrating the fast convergence speed and high
computational efﬁciency of the proposed AIEA.
In Fig. 4(b), as the initial position uncertainty of the
target UA V increases from 4 m to 10 m, the CRB trace of
AIEA remains stable at the lowest level, demonstrating strong
robustness. In contrast, the trace of RA increases moderately
from 1.5 to 2.5, and its positioning accuracy declines slightly
due to the lack of targeted optimization in random association.
RS features low random scheduling efﬁciency and limited
error offset capability. CUS prioritizes communication rates,
leading to insufﬁcient sensing resources and high sensitivity to
position uncertainty. ZF shows a steady rise with its ignorance
of position uncertainty, revealing its vulnerability to location
errors. MBS relies solely on position information without
uncertainty optimization, resulting in the most signiﬁcant drop.
In Fig. 5(a), the sensing performance of all algorithms
degrades as the number of CUs increases. In contrast,
AIEA achieves stable positioning performance by dynami-
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19623
Fig. 5. Sensing performance with varying parameters of CU: (a) Number of CUs; (b) Noise power of CU; and (c) SINR requirement of CU.
Fig. 6. Sensing performance with varying parameters of UA V: (a) Number of UA Vs; (b) Maximum horizontal ﬂight speed; and (c) Maximum transmit power.
cally balancing sensing robustness, communication quality,
and association scheduling. For MBS, all sensing resources
are allocated to strengthen the link between the target and
BSs, without considering the spatial correlation and mutual
interference introduced by the growing number of CUs. This
leads to a steeply rising CRB trace, fully exposing its fragility
in complex and high-interference environments. ZF lacks
robustness mechanisms against target position errors. When
the mismatch between the ideal channel state assumption and
actual position uncertainty deteriorates sharply, it fails to adapt
to the dynamic spatial distribution of users, resulting in the
highest CRB value among all baseline schemes.
In Fig. 5(b), we evaluate the impact of CU noise power
on the trace of CRB under different SINR requirements. As
the CU noise power increases from−115 dBm to−100 dBm,
the CRB traces of both algorithms exhibit a consistent upward
trend, indicating that elevated noise levels degrade the overall
positioning accuracy. By dynamically optimizing the trajecto-
ries and resource allocation to safeguard sensing performance,
AIEA maintains a relatively low CRB trace even under the
stringent SINR requirement of 10 dB. However, ZF prioritizes
enforcing zero inter-user interference at the expense of sensing
robustness. This rigid design fails to adjust beam directions to
mitigate the ampliﬁed noise, leading to a rapid degradation
in echo signal quality and a corresponding sharp surge in the
CRB trace.
In Fig. 5(c), AIEA achieves the best sensing performance.
Its optimized resource scheduling and association strategy
effectively balances communication SINR requirements and
sensing resource reservation. Without trajectory design, MBS
focuses on the sensing performance of the receiving BS,
leading to squeezed sensing resources as communication
requirements increase. CUS prioritizes maximizing com-
munication rates and resources are heavily tilted toward
communication under high SINR requirements. RA lacks
targeted design in random association, leading to lower sensing
resource allocation efﬁciency than that of AIEA. RS has
low resource utilization efﬁciency due to random sensing
scheduling. With ﬁxed zero-forcing beamforming, ZF shows
the steepest CRB rise as SINR requirements increase, failing
to balance communication and sensing.
In Fig. 6(a), at low SINRs, AIEA decreases rapidly with
an increasing number of UA Vs by fully leveraging multi-UA V
sensing collaboration. RA remains low and stable with random
user association, and additional UA Vs barely improve posi-
tioning accuracy. For RS, low random scheduling efﬁciency
limits the effectiveness of multi-UA V sensing. At high SINRs,
AIEA still declines with more UA Vs deployed, and multi-UA V
collaboration effectively mitigates the occupation of sensing
resources by communication tasks. The CRB of RA remains
low, while RS maintains a relatively high value, with additional
UA Vs bringing negligible improvement in sensing accuracy.
In Fig. 6(b), lower SINRs generally lead to lower CRB
traces, indicating that low SINRs release more sensing
resources. At the same SINR, the trace of AIEA is signiﬁcantly
lower than those of RA and RS, and AIEA achieves optimal
sensing performance at 8 dB. This demonstrates that AIEA
enables optimal resource allocation under both high and low
communication requirements. All curves remain stable as UA V
ﬂight speed increases, highlighting AIEA’s adaptability to
dynamic scenarios. While RA and RS also maintain stable
performance, their sensing accuracy is consistently inferior to
AIEA.
In Fig. 6(c), all algorithms show improved sensing per-
formance as transmit power increases, but power utilization
efﬁciency varies signiﬁcantly. AIEA remains the lowest as
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19624 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Beamforming performance: (a) Beampattern of type-1 UA V and
(b) Beampattern of type-2 UA V .
its optimized scheduling and association strategy efﬁciently
allocates increased power to sensing tasks. RA shows weak
power gain-to-sensing conversion, owing to the lack of service
allocation in random association. CUS prioritizes maximizing
communication rates, so additional power is mostly allocated
to communication, leading to slow improvement in sensing
performance. MBS and RS exhibit weak capability: the former
does not optimize power allocation for sensing, while the latter
suffers from low random scheduling efﬁciency. ZF maintains
the highest CRB and slowest descent across all transmit power
levels, revealing its poor efﬁciency in converting extra power
into sensing accuracy.
Fig. 7(a) demonstrates the beam pattern of type-1 UA V1,
including the radiation patterns of communication and sensing
beams. The communication beam peak points accurately to
the angle of CU3, while the sensing beam peak matches the
target angle, achieving angular alignment of beamforming with
the user and the target UA V , respectively. Meanwhile, the two
beams alternately form main lobes and suppress side lobes in
different angular intervals. This ensures communication signal
gain for users, achieves sensing signal focusing on the target,
and avoids mutual interference between the two beams.
Fig. 7(b) illustrates the beam pattern of type-2 UA V2,
covering two beams: communication transmission beam and
receiving beam. The communication beam main lobe peak
aligns precisely with CU2, ensuring directional communi-
cation signal gain for the user. The receiving beam main
lobe peak matches the target angle, capturing sensing echo
signals in this direction. Meanwhile, when the communication
beam main lobe covers the user, the receiving beam main
lobe focuses on the target. This design avoids interference
between communication transmission and sensing reception,
and ensures communication link stability and sensing echo
reception accuracy.
VI. C ONCLUSION
To overcome the limitations in achieving both ﬂexible
sensing and reliable positioning, this paper proposed an ISAC-
enabled anti-UA V algorithm considering the mobility-induced
position uncertainty of the target UA V . First, we derived the
corresponding CRB matrix for target UA V sensing under posi-
tion uncertainty and established the theoretical lower bound
on position estimation accuracy. Then, we formulated the
long-term CRB minimization problem and designed a robust
optimization algorithm by jointly optimizing transmit-receive
beamforming, association scheduling, and trajectories of
multi-UA Vs. Speciﬁcally, by developing a Schur complement-
based generalized Petersen’s sign-deﬁniteness lemma, we
converted the CRB matrix into a set of semideﬁnite con-
straints. Lagrangian relaxation was then adopted to decouple
transmit-receive ISAC beamforming, with the tightness of
SDR rigorously proven. We further proposed a penalty-based
SCA algorithm to tackle the coupled UA V scheduling and
CU association, and veriﬁed the convergence and effective-
ness of AIEA. Numerical results validated the performance
improvements of our proposed algorithm in cooperative sens-
ing accuracy. For future research, we will extend the proposed
framework to multi-target UA V scenarios to enable large-scale
anti-UA V operations.
APPENDIX A
PROOF OF THEOREM 1
According to equation (1), space-air channel hms [n] con-
sists of a deterministic LoS component and a random NLoS
component. Thus, ‖hms [n]‖2 follows a non-central chi-
squared distribution, which is a typical statistical model for
Rician fading. The general form of the probability density
function of the non-central chi-squared distribution is:
PX (x) = 12e− x+Φ2 (xΦ) QT−12 IQT−1(2√Φx), (A.1)
where Φ = 2κρmsQT/ (κ + 1)d2ms [n] quantiﬁes the contri-
bution of the LoS component to the statistical characteristics
of the squared channel norm, and In (x) denotes the modiﬁed
Bessel function of the ﬁrst kind of order n, expressed as:
In (x) = 1π∫ π0 ex cosθ cos (nθ)dθ. (A.2)
Thus, the corresponding cumulative distribution function is:
CX(x)
= Pr{X≤x} =
∫ x
−∞
PX(t)dt
=



1−MQT
(
√
2κQT,dms[n]
√
2x(κ + 1)
ρms
)
, x≥0,
0, otherwise,
(A.3)
where MQT (a,b ) is the Marcum Q-function, deﬁned as:
MQT (a,b ) ≜ 1aQT−1
∫ ∞
b
xQT−1e− x2+a22 IQT−1 (ax)dx.
(A.4)
APPENDIX B
PROOF OF COROLLARY 1
Since MQT (a,b ) is strictly increasing as b decreases for
ﬁxed QT and a, and b =
√
C/P SATm [n] is strictly decreas-
ing in P SATm [n], the outage probability is strictly increasing
in P SATm [n]. By considering feasible transmit power range
(0,P max], where Pmax is the maximum transmit power con-
straint, the outage probability approaches 1 as P SATm [n]→ 0+
and reaches a minimum at P SATm [n] =Pmax. Therefore, there
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19625
exists a uniqueP SATm [n] satisfying Pr{γm[n]≤ Γreqm} =ϵm[n]
that minimizes the transmit power while meeting the con-
straint, which can be efﬁciently obtained via binary search and
is treated as a predeﬁned parameter in subsequent analysis.
APPENDIX C
PROOF OF THEOREM 2
First, we deﬁne the overall sensing channel matrix of as
GL,m[n]=
[
ϱ1,L,m[n]H1,L,m[n],...,ϱ M,L,m[n]HM,L,m[n]
]
∈
CQR×MQ T , and the transmit signal vector ~x[n] =[
x1[n]T,..., xM[n]T]T∈ CMQ T . Then we can obtain:
~ym [n] = uHm [n] GL,m [n]~x [n] + uHm [n] vm [n], (C.1)
with receive beamforming vector um[n] ∈ CQR and noise
vector vm[n]∈ CQR. Consequently, element (i,j ) of Fm [n]
is given by:
F (i,j)m = 2σ2m ℜ{∂~ym[n]∂Si[n]∂~ym[n]∂Sj[n]}, (C.2)
where ∂~ym[n]/∂Si[n] = uHm[n] ˙G(i)L,m[n]~x[n]. Variable Si[n]
denotes element i of the parameter vector to be estimated,
and ˙G(i)L,m[n] represents the derivative of GL,m[n] with
respect to Si[n]. Speciﬁcally, if i ∈ {1, 2, 3}, ˙GL,m[n] =[
ϱ1,L,m[n] ˙H1,L,m[n],...,ϱ M,L,m[n] ˙HM,L,m[n]], where vari-
able ˙H(i)1,L,m[n] denotes the derivative of H1,L,m[n] with
respect to Si[n]. If i = 4 , and term i of Si[n] is
ϱm′,L,m[n], then ˙G(i)L,m[n] = [0,··· , ˙H(i)m′,L,m[n],··· , 0]. If
i = 5 , and term i of Si[n] is ϱm′,L,m[n], then ˙G(i)L,m[n] =[
0,··· ,j ˙H(i)m′,L,m[n],··· , 0]. The same rule applies for i =
6... 2M + 3. Thus, we can obtain the following:
F (i,j)m [n]
= 2σ2mℜ{(uHm[n] ˙G(i)L,m[n]~x[n])(uHm[n] ˙G(j)L,m[n]~x[n])T}
= 2σ2mℜ{Tr(uHm[n]um[n] ˙G(i)L,m[n]Sm′[n][ ˙G(j)L,m[n]]H)}
= 2σ2mℜ{vec(BHm[n])ψ(i,j)m [n]}. (C.3)
where beamforming association matrix Bm[n] =
uHm[n]um[n]Sm′[n]∈ CMQ T×MQ T , and sensing association
vectorψ(i,j)m [n] = vec( ˙G(j)HL,m [n] ˙G(i)L,m[n])∈ CM2Q2T .
APPENDIX D
PROOF OF THEOREM 3
The objective function of Problem P 1 is nonconvex with
respect to beamforming vectors ( Wmk,Rm,Um), association
scheduling (Amk,Bm), and UA V trajectory Pm, which are
highly coupled with each other. Besides, due to binary vari-
ables and nonconvex constraints, Problem P 1 is an MINNP
problem. In fact, even if UA V trajectory and beamforming
vectors are ﬁxed, the problem reduces to ﬁnding an optimal
solution for association scheduling to minimize the CRB
trace, which belongs to the classical Knapsack problem. Thus,
Problem P 1 exhibits NP-hard complexity.
APPENDIX E
PROOF OF THEOREM 4
We deﬁne A∗ ≜ {W∗mk,R∗m,Q∗,E∗m} as the optimal
solution set of the convex Problem P 2.1′′, and construct a
new solution set ~A∗ ≜{~W∗mk, ~R∗m, ~Q∗,~E∗m} satisfying:
~W∗mk =W∗mkhmkhHmkW∗mkhHmkW∗mkhmk , (E.1)
~R∗m =∑
k∈K
~W∗mk +R∗m−∑
k∈K
W∗mk, (E.2)
~Q∗ =Q∗, ~E∗m =E∗m. (E.3)
From equation (E.1), ~W∗mk is an outer product of vec-
torW∗mkhmk/
√
hHmkW∗mkhmk and its Hermitian transpose,
which yields Rank (~W∗mk) = 1 . By direct calculation,
we have Tr
(~W∗mk) = Tr(W∗mk), and Tr(Hmk~W∗mk) =
Tr
(
HmkW∗mk), where matrix Hmk = hmkhHmk. From equa-
tion (E.2), it follows that
∑
k∈K
~W∗mk + ~R∗m =∑
k∈K
W∗mk +R∗m, (E.4)
which implies Tr
(~R∗m) = Tr (R∗m), and Tr(Hmk~R∗m) =
Tr (HmkR∗m). Thus, ~A∗ satisﬁes all constraints of Problem
P 2.1′′.
LetL be the Lagrangian function of Problem P 2.1′′ with
optimal dual variables{υI∗m,υ II∗m,υ∗k}. Since the objective and
constraints are linear in trace terms, the gradients of L at ~A∗
are identical to those at A∗, which yields
∇ ~WmkL
⏐⏐~A∗ = 0, ∇ ~RmL⏐⏐~A∗ = 0. (E.5)
The optimal dual variables are nonnegative, satisfying dual
feasibility. As all constraint values are preserved under the
above construction, the complementary slackness conditions
hold for ~A∗. Given that Problem P 2.1′′ is convex and ~A∗
satisﬁes all KKT optimality conditions, ~A∗ is also optimal
with Rank (~W∗mk) = 1 . By the same argument, Problem
P 2.2′ admits a rank-one optimal solution ~U∗m such that Rank
(~U∗m) = 1.
APPENDIX F
PROOF OF THEOREM 5
First, we deﬁne ~J as the objective function of Problem
P 3 and (A∗mk,B∗m) as its optimal solution. For any feasible
solution (Amk,Bm) to Problem P 3, we have ~J (A∗mk,B∗m)≤~J (Amk,Bm). Next, we deﬁne ~F1 = ~J + µαCα(Amk) +
µβCβ(Bm) as the objective function of Problem P 3′ and
(A(t)mk,B(t)m ) as its optimal solution corresponding to penalty
factors (µ(t)α ,µ (t)β ) as t → ∞. We obtain the following
inequality:
~J (A(t)mk,B(t)m )+µ(t)α Cα(A(t)mk)+µ(t)β Cβ(B(t)m )
≤ ~J (A∗mk,B∗m). (F.1)
By rearranging equation (F.1), we obtain:
µ(t)α Cα(A(t)mk)+µ(t)β Cβ(B(t)m )
≤ ~J (A∗mk,B∗m)−~J (A(t)mk,B(t)m ). (F.2)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

19626 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Next, we deﬁne (Amk,Bm) as the limit point, and denote
T as an inﬁnite subsequence such that
lim
t∈T,t→∞
(A(t)mk,B(t)m ) = (Amk,Bm). (F.3)
Since µ(t)α →∞ , µ(t)β →∞ , and Cα(α)≤ 0, Cβ(β)≤ 0
for all feasible α,β , the left-hand side of equation (F.2) is
bounded above only if Cα(A(t)mk)→ 0 and Cβ(B(t)m )→ 0.
This impliesAmk∈{ 0, 1} andBm∈{ 0, 1} for all m,k , and
thus (Amk,Bm) is feasible for Problem P 3.
Finally, taking the limit of equation (F.1), we obtain
~J (Amk,Bm)≤ ~J (A∗mk,B∗m). Since (Amk,Bm) is feasible
for Problem P 3 and (A∗mk,B∗m) is optimal, it follows that~J (Amk,Bm) = ~J (A∗mk,B∗m). Thus, (Amk,Bm) is an opti-
mal solution of Problem P 3.
APPENDIX G
PROOF OF THEOREM 6
We deﬁne variable sets W(t)mk,R(t)m ,U(t)m ,A(t)mk,B(t)m and
P(t)m as the solution of iteration t of the formulated CRB min-
imization problem. Then, the corresponding objective function
can be deﬁned as S
(
W(t)mk,R(t)m,U(t)m ,A(t)mk,B(t)m,P(t)m). Vari-
ablesW(t+1)mk ,R(t+1)m , and U(t+1)m can be obtained for given
A(t)mk, B(t)m and P(t)m by solving Problem P 2. Thus, the
following inequality holds:
S
(
W(t)mk,R(t)m,U(t)m ,A(t)mk,B(t)m,P(t)m)≥
S
(
W(t+1)mk ,R(t+1)m ,U(t+1)m ,A(t)mk,B(t)m,P(t)m). (G.1)
Similarly,A(t)mk,B(t)m andP(t)m can be obtained by solving
Problems P 3 and P 4, and the following inequalities hold:
S
(
W(t+1)mk ,R(t+1)m ,U(t+1)m ,A(t)mk,B(t)m,P(t)m)≥
S
(
W(t+1)mk ,R(t+1)m ,U(t+1)m ,A(t+1)mk ,B(t+1)m ,P(t)m). (G.2)
S
(
W(t+1)mk ,R(t+1)m ,U(t+1)m ,A(t+1)mk ,B(t+1)m ,P(t)m)≥
S
(
W(t+1)mk ,R(t+1)m ,U(t+1)m ,A(t+1)mk ,B(t+1)m ,P(t+1)m ). (G.3)
Based on inequalities (G.1)–(G.3), we can obtain:
S
(
W(t)mk,R(t)m,U(t)m ,A(t)mk,B(t)m,P(t)m)≥
S
(
W(t+1)mk ,R(t+1)m ,U(t+1)m ,A(t+1)mk ,B(t+1)m ,P(t+1)m ). (G.4)
From constraint (34a), the positive semi-deﬁniteness of Jm
yields a positive lower bound for the sum of CRB traces.
Together with the non-increasing monotonicity of the objective
under alternating optimization, the convergence of AIEA is
rigorously guaranteed.
REFERENCES
[1] X. Wang, Q. Liu, Z. Ning, T. Qiu, L. Guo, and Y . Zhang, “Energy-
efﬁcient secure aerial communications for low-altitude economy: Joint
UA V scheduling and trajectory optimization,” IEEE Trans. Wireless
Commun., vol. 25, pp. 14828–14844, 2026.
[2] X. Luo, Q. Lin, R. Zhang, H.-H. Chen, X. Wang, and M. Huang,
“ISAC—A survey on its layered architecture, technologies, standardiza-
tions, prototypes, and testbeds,” IEEE Commun. Surveys Tuts. , vol. 28,
pp. 485–526, 2026.
[3] R. Liu, M. Li, and A. Lee Swindlehurst, “Joint array partitioning and
beamforming designs in ISAC systems: A Bayesian CRB perspective,”
IEEE J. Sel. Areas Commun. , vol. 44, pp. 150–164, 2026.
[4] H. T. Nguyen et al., “Energy efﬁciency for massive MIMO integrated
sensing and communication systems,” IEEE J. Sel. Areas Commun. ,
vol. 44, pp. 165–180, 2026.
[5] Y . Zhang, H. Shan, Y . Zhou, Z. Shi, L. Sheng, and Y . Liu, “Cooperative
beamforming design for anti-UA V ISAC systems,”IEEE Trans. Wireless
Commun., vol. 24, no. 3, pp. 2249–2264, Mar. 2025.
[6] X. Liu and C. Fischione, “Coordinated beamforming for multi-cell ISAC
using graph neural networks,” IEEE Trans. Wireless Commun., vol. 25,
pp. 5876–5889, 2026.
[7] S. Zhang et al., “Two-stage transmission framework and resource
allocation for mmWave-ISAC systems,”IEEE Trans. Wireless Commun.,
vol. 25, pp. 5797–5810, 2026.
[8] Y . Wang et al., “ISAC enabled cooperative detection for cellular-
connected UA V network,” IEEE Trans. Wireless Commun. , vol. 24,
no. 2, pp. 1541–1554, Feb. 2025.
[9] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for
low-altitude economy: Coordinated transmit beamforming and UA V tra-
jectory design,” IEEE Trans. Commun. , vol. 73, no. 8, pp. 5832–5847,
Aug. 2025.
[10] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li,
“Throughput maximization for UA V-enabled integrated periodic sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 1,
pp. 671–687, Jan. 2023.
[11] W. Mao, Y . Lu, G. Pan, and B. Ai, “UA V-assisted communications in
SAGIN-ISAC: Mobile user tracking and robust beamforming,” IEEE
J. Sel. Areas Commun. , vol. 43, no. 1, pp. 186–200, Jan. 2025.
[12] X. Jing, F. Liu, C. Masouros, and Y . Zeng, “ISAC from the sky: UA V
trajectory design for joint communication and target localization,” IEEE
Trans. Wireless Commun., vol. 23, no. 10, pp. 12857–12872, Oct. 2024.
[13] A. Khalili, A. Rezaei, D. Xu, F. Dressler, and R. Schober, “Efﬁcient
UA V hovering, resource allocation, and trajectory design for ISAC with
limited backhaul capacity,” IEEE Trans. Wireless Commun. , vol. 23,
no. 11, pp. 17635–17650, Nov. 2024.
[14] B. Li, H. Zhang, Y . Rong, and Z. Han, “A control-based design of
beamforming and trajectory for UA V-enabled ISAC system,” IEEE
Trans. Wireless Commun., vol. 25, pp. 3469–3484, 2026.
[15] K. Meng et al., “UA V-enabled integrated sensing and communication:
Opportunities and challenges,” IEEE Wireless Commun., vol. 31, no. 2,
pp. 97–104, Apr. 2024.
[16] X. Guo, J. Shi, J. Wu, R. Zhang, and X. Cheng, “Integrated sensing and
communications in multi-UA V networks: A dual-objective optimization
perspective,” IEEE Trans. Wireless Commun., vol. 25, pp. 10066–10081,
2026.
[17] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-UA V
networks,” IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660–2672, Apr.
2021.
[18] H. He et al., “Energy-efﬁcient multi-UA V navigation for cooperative
data sensing and transmission,” IEEE Trans. Mobile Comput. , vol. 25,
no. 3, pp. 3119–3136, Mar. 2026.
[19] L. Zhou, X. Ning, M.-Y . You, R. Zhang, and Q. Shi, “Robust multi-UA V
placement optimization for AOA-based cooperative localization,” IEEE
Trans. Intell. Vehicles, vol. 9, no. 10, pp. 6122–6136, Oct. 2024.
[20] T. Zhang, K. Zhu, S. Zheng, D. Niyato, and N. C. Luong, “Trajectory
design and power control for joint radar and communication enabled
multi-UA V cooperative detection systems,” IEEE Trans. Commun. ,
vol. 71, no. 1, pp. 158–172, Jan. 2023.
[21] Y . Qin, Z. Zhang, X. Li, W. Huangfu, and H. Zhang, “Deep rein-
forcement learning based resource allocation and trajectory planning
in integrated sensing and communications UA V network,” IEEE Trans.
Wireless Commun., vol. 22, no. 11, pp. 8158–8169, Nov. 2023.
[22] B. Yin, X. Fang, and X. Wang, “Robust group target awareness
inference in multi-UA V-enabled ISCC networks based on split deep rein-
forcement learning,” IEEE Trans. Wireless Commun. , vol. 24, no. 11,
pp. 9478–9492, Nov. 2025.
[23] C. You and R. Zhang, “3D trajectory optimization in Rician fading for
UA V-enabled data harvesting,”IEEE Trans. Wireless Commun., vol. 18,
no. 6, pp. 3192–3207, Jun. 2019.
[24] B. Li, Q. Li, Y . Zeng, Y . Rong, and R. Zhang, “3D trajec-
tory optimization for energy-efﬁcient UA V communication: A control
design perspective,” IEEE Trans. Wireless Commun. , vol. 21, no. 6,
pp. 4579–4593, Jun. 2022.
[25] M. Gapeyenko, D. Moltchanov, S. Andreev, and R. W. Heath, “Line-of-
sight probability for mmWave-based UA V communications in 3D urban
grid deployments,” IEEE Trans. Wireless Commun. , vol. 20, no. 10,
pp. 6566–6579, Oct. 2021.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED ANTI-UA V: JOINT BEAMFORMING AND TRAJECTORY DESIGN FOR MULTI-UA Vs 19627
[26] W. Mao et al., “Cram ´er–Rao bound optimization for bistatic ISAC:
Transceiver design and attention-based ISACNet,” IEEE J. Sel. Areas
Commun., vol. 44, pp. 181–195, 2026.
[27] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[28] B. Liu, Y . Wan, F. Zhou, Q. Wu, and R. Q. Hu, “Resource allocation
and trajectory design for MISO UA V-assisted MEC networks,” IEEE
Trans. Veh. Technol., vol. 71, no. 5, pp. 4933–4948, May 2022.
[29] B. Lyu et al., “Robust transmission design for reconﬁgurable intelligent
surface and movable antenna enabled symbiotic radio communications,”
IEEE Trans. Wireless Commun. , vol. 25, pp. 1702–1716, 2025.
[30] P. Stoica and A. Nehorai, “MUSIC, maximum likelihood, and Cram ´er-
Rao bound,” IEEE Trans. Acoust., Speech, Signal Process. , vol. 37,
no. 5, pp. 720–741, May 1989.
[31] Y . Xu, D. Xu, and S. Song, “Sensing-assisted robust SWIPT for mobile
energy harvesting receivers in networked ISAC systems,” IEEE Trans.
Wireless Commun., vol. 24, no. 3, pp. 2094–2109, Mar. 2025.
[32] C. Siriteanu, A. Takemura, S. Kuriki, D. St. P. Richards, and H. Shin,
“Schur complement based analysis of MIMO zero-forcing for Rician
fading,” IEEE Trans. Wireless Commun., vol. 14, no. 4, pp. 1757–1771,
Apr. 2015.
[33] S. Li, C. Gao, M. Wei, J. Zhao, P. Shao, and J. Xu, “CSI-impaired secure
resource allocation for SWIPT-enabled full-duplex consumer Internet of
Things networks in smart healthcare,” IEEE Trans. Consum. Electron. ,
vol. 69, no. 4, pp. 685–696, Nov. 2023.
[34] X. Wang, J. Li, Z. Ning, Q. Song, L. Guo, and A. Jamalipour, “Wireless
powered metaverse: Joint task scheduling and trajectory design for multi-
devices and multi-UA Vs,”IEEE J. Sel. Areas Commun. , vol. 42, no. 3,
pp. 552–569, Mar. 2023.
[35] Z. Ning, Y . Zhang, X. Wang, L. Guo, D. Niyato, and Y . Zhang,
“Joint trajectory and beamforming optimization for UA V-ISAC
secure communications,” IEEE Trans. Wireless Commun. , vol. 25,
pp. 15216–15231, 2026.
[36] Y . Wang, M. Tao, and S. Sun, “Cram ´er–Rao bound analysis and
beamforming design for integrated sensing and communication with
extended targets,” IEEE Trans. Wireless Commun. , vol. 23, no. 11,
pp. 15987–16000, Nov. 2024.
Xiaojie Wang (Senior Member, IEEE) received the
Ph.D. degree from Dalian University of Technology,
Dalian, China, in 2019. Currently, she is a Full
Professor with the School of Communications and
Information Engineering, Chongqing University of
Posts and Telecommunications, Chongqing, China.
She has published over 90 scientiﬁc papers in
international journals and conferences. Her research
interests are uncrewed aerial vehicle communica-
tions, mobile edge computing, and machine learning.
She is also a Highly Cited Researcher (Clarivate) in
2023 and 2024.
Lingfei Li (Graduate Student Member, IEEE)
received the bachelor’s degree from the School
of Communications and Information Engineering,
Chongqing University of Posts and Telecommuni-
cations, Chongqing, China, in 2024, where he is
currently pursuing the master’s degree. His research
interests include uncrewed aerial vehicle communi-
cations, integrated sensing and communication, and
convex optimization.
Zhaolong Ning (Senior Member, IEEE) received
the Ph.D. degree from Northeastern University,
China, in 2014. He is currently a Full Professor
with the School of Communications and Informa-
tion Engineering, Chongqing University of Posts
and Telecommunications, Chongqing, China. He
has published more than 150 scientiﬁc papers in
international journals and conferences. His research
interests include 6G networks, uncrewed aerial vehi-
cle communications, and edge intelligence. He has
been a Highly Cited Researcher (Clarivate) since
2020, an IEEE VTS Distinguished Lecturer, and an IET Fellow. He serves as
an Associate Editor for IEEE T RANSACTIONS ON VEHICULAR TECHNOL -
OGY and IEEE T RANSACTIONS ON CLOUD COMPUTING .
Xiaoming Tao (Senior Member, IEEE) received
the Ph.D. degree in information and communica-
tion systems from Tsinghua University, Beijing,
China, in 2008. She is currently a Professor with
the Department of Electronic Engineering, Tsinghua
University, and Dean of the School of Computer
Science and Technology, Xinjiang University. She
was a recipient of the National Science Foundation
for Outstanding Youth for the term (2017–2019)
and many national awards, such as the 2017 China
Young Women Scientists Award, the 2017 Top Ten
Outstanding Scientists and Technologists from China Institute of Electronics,
the 2017 First Prize of Wu Wen Jun AI Science and Technology Award,
the 2016 National Award for Technological Invention Progress, and the 2015
Science and Technology Award of China Institute of Communications. She
served as the Workshop General Co-Chair for IEEE INFOCOM 2015 and the
V olunteer Leadership for IEEE ICIP 2017. She has been an Editor of Journal
of Communications and Information Networks and China Communications
since 2016.
Tie Qiu (Senior Member, IEEE) held an Assis-
tant Professor and an Associate Professor with the
School of Software, Dalian University of Technol-
ogy, from 2008 to 2013. He was a Visiting Professor
with the Department of Electrical and Computer
Engineering, Iowa State University, Ames, IA, USA,
from 2014 to 2015. He is currently a Full Professor
with the School of Computer Science and Engi-
neering, Northeastern University, Shenyang, China.
He has authored/co-authored ten books, more than
200 scientiﬁc papers in international journals and
conference proceedings. He is also a Distinguished Member of China Com-
puter Federation (CCF) and a Senior Member of ACM. He serves as an
Associate Editor for IEEE/ACM T RANSACTIONS ON NETWORKING , IEEE
TRANSACTIONS ON NETWORK SCIENCE AND ENGINEERING , and IEEE
TRANSACTIONS ON SYSTEMS , M AN, AND CYBERNETICS : S YSTEMS ; and
an Area Editor for Ad Hoc Networks (Elsevier).
Lei Guo received the Ph.D. degree from the Univer-
sity of Electronic Science and Technology of China,
Chengdu, China, in 2006. He is currently a Full
Professor with Northeastern University, Shenyang,
China. He has authored or co-authored more than
200 technical papers in international journals and
conferences. His current research interests include
communication networks, optical communications,
and wireless communications. He is an editor of
several international journals.
Yan Zhang (Fellow, IEEE) received the Ph.D.
degree from the School of Electrical and Electron-
ics Engineering, Nanyang Technological University,
Singapore. He is currently a Full Professor with
the University of Electronic Science and Technol-
ogy of China. His research interests include next
generation wireless networks leading to 6G and
green and secure cyber-physical systems. He is
the Co-Editor-in-Chief of IEEE T RANSACTIONS
ON INDUSTRIAL INFORMATICS , an Area Editor of
IEEE T RANSACTIONS ON GREEN COMMUNICA -
TIONS AND NETWORKING , a Senior Editor of IEEE S YSTEMS JOURNAL ,
and an Associate Editor of several IEEE T RANSACTIONS /magazine. Since
2018, he has been a recipient of the global Clarivate Analytics “Highly Cited
Researcher” Award (Web of Science top 1% most cited worldwide). He is a
fellow of IET, an elected member of Academia Europaea (MAE), an elected
member of the Royal Norwegian Society of Sciences and Letters (DKNVS),
and an elected member of Norwegian Academy of Technological Sciences
(NTV A).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on August 13,2026 at 05:40:35 UTC from IEEE Xplore.  Restrictions apply.