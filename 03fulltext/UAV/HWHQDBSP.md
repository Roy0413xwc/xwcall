---
title: "A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System"
zotero_key: "HWHQDBSP"
pdf_key: "6PFB9AYV"
doi: "10.1109/TWC.2025.3604344"
collection: "UAV"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 3469
A Control-Based Design of Beamforming and
Trajectory for UA V-Enabled ISAC System
Bin Li
 , Senior Member , IEEE, Hongyun Zhang
 , Yue Rong
 , Senior Member , IEEE,
and Zhu Han
 , Fellow, IEEE
Abstract—We study a control-based design of beamforming
and trajectory that incorporates the dynamic model, focusing
on a scenario where a multi-antenna unmanned aerial vehicle
(UA V) simultaneously performs radar sensing of multiple targets
in a speciﬁc region and communication with multiple ground
users. Two optimization problems are formulated for the three-
degree-of-freedom (3-DoF) and six-degree-of-freedom (6-DoF)
dynamic models of UA V , which are often overlooked in existing
designs. These problems aim to maximize the average weighted
communication rate while maintaining the dynamic constraints
and the sensing service requirements by designing the UA V
trajectory and the communication and sensing beamforming
vectors. To deal with the challenges posed by the UA V dynamic
constraints, we decompose the original problem into two
subproblems: the communication and sensing beamforming
design subproblem, and the UA V trajectory optimization
subproblem. Given the UA V trajectory, we employ the sequential
convex approximation (SCA) and semi-deﬁnite relaxation (SDR)
methods to transform the beamforming design subproblem
into a convex problem. Given the communication and sensing
beamforming vectors, we propose a control-based approach with
piecewise parameterization and exact penalty function strategies
to transform the UA V trajectory optimization subproblem into
a static nonlinear program, which can be efﬁciently solved by
sequential quadratic programming (SQP). Numerical simulations
indicate that the proposed scheme is more feasible in terms of
the UA V control than the existing scheme in practical systems,
with less performance loss or even no performance degradation.
Index Terms —UA V-enabled ISAC system, trajectory
optimization, beamforming design, alternating optimization,
control parametrization.
I. I NTRODUCTION
W
ITH the mobile communication gradually moving
towards the era of intelligent connection of everything,
Received 18 December 2024; revised 28 April 2025; accepted 22 August
2025. Date of publication 8 September 2025; date of current version
22 December 2025. This work was supported in part by the National
Natural Science Foundation of China under Grant U24B20156; in part by the
National Defense Basic Scientiﬁc Research Program of China under Grant
JCKY2021204B051; in part by NSF under Grant ECCS-2302469 and Grant
CMMI-2222810; and in part by Toyota, Amazon, and Japan Science and
Technology Agency (JST) Adopting Sustainable Partnerships for Innovative
Research Ecosystem (ASPIRE) under Grant JPMJAP2326. The associate
editor coordinating the review of this article and approving it for publication
was Z. Fadlullah. (Corresponding author: Hongyun Zhang.)
Bin Li and Hongyun Zhang are with the School of Aeronautics and
Astronautics, Sichuan University, Chengdu, Sichuan 610065, China (e-mail:
bin.li@scu.edu.cn; zhanghongyun1@stu.scu.edu.cn).
Yue Rong is with the School of Electrical Engineering, Computing and
Mathematical Sciences, Curtin University, Perth, W A 6845, Australia (e-mail:
y.rong@curtin.edu.au).
Zhu Han is with the Department of Electrical and Computer Engineer-
ing, University of Houston, Houston, TX 77004 USA, and also with the
Department of Computer Science and Engineering, Kyung Hee University,
Seoul 446-701, South Korea (e-mail: zhan2@uh.edu).
Digital Object Identiﬁer 10.1109/TWC.2025.3604344
the future mobile communication system should not only
achieve high communication performance such as ultra-fast
speed, ultra-low latency, and ultra-high dependability, but
also have the sensing ability of millimeter-level accuracy
[1] to support various intelligent applications, such as auto-
matic driving [2], [3], trafﬁc monitoring [4], human activity
recognition, and smart home [5]. Toward this end, integrated
sensing and communication (ISAC) has garnered tremendous
attention from both academia and industry [6], [7], [8], [9],
[10], [11], [12], [13], [14], [15], [16], [17], [18], and is one
of the six international telecommunication union (ITU) use
scenarios for 6G. In contrast to conventional fully separated
independent systems, ISAC has signiﬁcant potential to reduce
both hardware and signaling costs, while enhancing spectral
and energy utilization efﬁciencies by sharing wireless devices
and spectrum resources.
Due to the additional spatial information provided by
multiple-input-multiple-output (MIMO) systems, they can
signiﬁcantly enhance sensing performance and effectively
increase system throughput compared to the information
embedding method [19] and the waveform combination
scheme [20]. The high-quality service of multiple users and
high-precision sensing of multiple targets can be ensured
through beamforming techniques by focusing signals simul-
taneously in multiple speciﬁc directions. However, the MIMO
ISAC with transmit beamforming in terrestrial networks
suffers from severe performance degradation due to non-line-
of-sight (NLoS) signal paths or clutter caused by obstacles
and scatterers in the surrounding environment, especially for
sensing.
Given the altitude advantage of unmanned aerial vehicles
(UA Vs), they are expected to serve as a promising new type
of aerial ISAC platform to overcome existing limitations.
Hence, the UA V-enabled ISAC with transmit beamforming
has attracted signiﬁcant attention from both industry and
academia. For instance, [15] investigates UA V performing
sensing tasks in target areas while simultaneously serving
multiple users for communication tasks, for the purpose
of maximizing the weighted average communication rate
under sensing performance requirements. To achieve this, the
optimization of UA Vs’ two-dimensional (2D) trajectory and
transmit beamforming vectors is conducted. A novel adaptable
ISAC mechanism in UA V-assisted systems is designed in [16]
to avoid excessive sensing, where the duration of sensing does
not need to align with the duration of communication and
can be ﬂexibly conﬁgured based on application requirements.
In [17], two joint optimization schemes under different UA V
states are discussed. On the one hand, a joint design approach
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3470 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
for communication precoding and UA V ﬂight trajectory is
proposed to address the minimum user rate maximization
problem. On the other hand, a joint optimization method for
UA V sensing position, communication, and sensing precoding
is proposed to tackle the minimum target detection probabil-
ity maximization problem. Paper [18] studies a multi-UA V
assisted ISAC scenario where the UA Vs detect a target and
simultaneously transmit the corresponding data to users. A
joint design scheme for the UA Vs trajectory, user association,
and beamforming is proposed to maximize the sum weighted
bit rate of all ground users while ensuring the minimum service
requirement of radar sensing.
The authors in [15], [16], [17], and [18] address the tra-
jectory optimization problem of UA Vs under discrete speed
constraints by modeling the UA V as a mass point in the ISAC
scenarios with transmit beamforming. They obtain a series
of segmented trajectories using time discretization techniques.
However, this model only focuses on the position and speed
of the UA V while neglecting its rotational motion, internal
forces, and torques. This means the complex dynamic char-
acteristics of the UA V as a rigid body are ignored, which
can lead to inaccuracies in both trajectory optimization and
control strategies. In other words, the UA V controller might
struggle to accurately follow the planned trajectory in prac-
tical applications. Any mismatch between the planned and
actual trajectories can result in increased communication link
delays, acquisition errors, and a decrease in the environmental
modeling and target recognition capabilities of the sensing
system, ultimately degrading communication and sensing
performance.
Motivated by the aforementioned discussions, we propose
a joint design of beamforming and trajectory control to
maximize the average weighted communication rate while
guaranteeing the service requirement for radar sensing. In
particular, we consider the three-degree-of-freedom (3-DoF)
model with translational UA V motion and the six-degree-
of-freedom (6-DoF) dynamic model with both translational
and rotational UA V motion. These two UA V models provide
performance-complexity tradeoffs. We investigate the scenario
where a multi-antenna UA V senses targets within a speciﬁc
region while simultaneously providing communication ser-
vices to multiple users, with potential applications in border
surveillance and environmental monitoring. To address the
challenges posed by the dynamic constraints on the UA V , we
decompose the original optimization problem into two distinct
subproblems: one that focuses on beamforming optimization,
and the other on designing the UA V’s trajectory, solving
them iteratively in an alternating manner. Different from the
trajectory discretization in existing methods [15], [16], [17],
[18], the proposed approach parameterizes control variables
based on a state-space model and describes the UA V state
variables (such as position and velocity) as functions of control
parameters to achieve a continuous and smooth ﬂight path.
Additionally, this method effectively reduces vibrations and
abrupt changes during ﬂight, enhancing stability and tracka-
bility.
The primary contributions of this paper can be summarized
below.
• We propose a control-based joint design of beamforming
and trajectory that incorporates either the 3-DoF model
or the 6-DoF model. Compared with the segmented
piecewise trajectories commonly obtained in [15], [16],
[17], and [18], the proposed scheme achieves continuous
and smooth ﬂight trajectories.
• We leverage an iterative method to solve the joint beam-
forming and trajectory optimization problem, combining
the UA V dynamics model. The original problem is
decomposed into two subproblems: communication and
sensing beamforming optimization, and UA V trajectory
optimization. Given the UA V trajectory, the communica-
tion and sensing beamforming optimization subproblem
is reformulated as a convex problem adopting sequential
convex approximation (SCA) and semi-deﬁnite relaxation
(SDR) methods, which can be addressed with the CVX
toolbox. Based on the obtained communication and sens-
ing beamforming vectors, we apply a piecewise-based
parameterization method and an exact penalty function
method to transform the UA V trajectory optimiza-
tion subproblem into a static nonlinear program which
can be solvable via sequential quadratic programming
(SQP).
• We evaluate the performance of the proposed schemes
and verify the effectiveness of the proposed algorithms
through numerical simulations. The results indicate that
the two proposed schemes are more feasible in terms of
the UA V control than the benchmark scheme [15] in prac-
tical UA V-enabled ISAC systems, with less performance
loss or even no performance degradation. Furthermore,
the proposed scheme with the 3-DoF model strikes an
effective compromise between computational complexity
and performance compared to both the benchmark model-
free scheme and the proposed scheme with the 6-DoF
model.
The rest of the paper is structured as follows. In Sec-
tion II, the UA V dynamic models and the communication and
sensing channel models are described. The joint problem of
beamforming design and UA V ﬂight trajectory planning is
solved in Section III. In Section IV, the assessment of the
proposed methods is conducted. Finally, we conclude the paper
in Section V.
II. S YSTEM MODEL AND PROBLEM FORMULATION
We study a downlink UA V-enabled ISAC system designed
to perform radar sensing on potential targets while providing
downlink communication services for multiple single-antenna
users,1 as shown in Fig. 1. The quad-rotor UA V travels from a
1The system we consider can be applied to various scenarios, includ-
ing large-scale public events, emergency responses and rescues, and trafﬁc
monitoring. To illustrate its functionality, we focus on the trafﬁc monitoring
scenario. In the event of a trafﬁc accident, or during major public events
such as marathons, the UA V provides high-quality downlink communication
services for trafﬁc management departments, drivers, and pedestrians by
broadcasting real-time road condition information. Simultaneously, the UA V
utilizes radar to scan the monitored area, track vehicle ﬂow, and precisely
locate accident locations. By delivering real-time and precise data, the
UA V enables trafﬁc management departments to optimize trafﬁc control and
enhance emergency response efﬁciency.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: CONTROL-BASED DESIGN OF BEAMFORMING AND TRAJECTORY FOR UA V-ENABLED ISAC SYSTEM 3471
Fig. 1. Description of the UA V-aided downlink ISAC scenario.
predetermined initial location to a ﬁnal location within a ﬁnite
time horizon, i.e., T
∆
= [0,T ]. Let p(t) = [x(t),y (t), z(t)]⊤
represent the position vector of the UA V , where[·]⊤ stands for
the matrix transpose. For simplicity, it is assumed that the UA V
operates at a ﬁxed altitude denoted by zu.2 A uniform linear
array (ULA) with N antennas and d =λ/2 adjacent-element
spacing is installed at the UA V , whereλ represents the carrier
wavelength. Similarly to [21], the ULA is placed vertically
to the horizontal plane at the UA V to facilitate the technical
derivation. The set of sensing targets in the area of interest
is represented byJ ≜{1,...,J }, with each target’s location
given by oj = [ox,j,oy,j, 0]⊤, j∈J . The position of targets
is assumed to be known by the UA V . We also assume there
are M users, with each user m∈M ≜{1,...,M } having
a position denoted by pm = [px,m,py,m, 0]⊤. The position
of users can be acquired either through the global positioning
system (GPS) or estimated from uplink signals [22]. For ease
of reading, the notations for the primary variables are provided
in Table I.
A. Communication and Sensing Model
We consider that the UA V sends the information signal
cm(t) to user m∈ Mwith transmit beamforming at time
t∈T .3 Although it is feasible to reuse communication signals
for sensing, the DoF of sensing may be limited [25]. Thus, we
design a dedicated radar signal c0∈ CN×1 to further enhance
communication and sensing performance [12], [15], [26]. We
assume that the information signals{cm}Mm=1 are independent,
i.e.,cm(t)∼CN (0, 1), while the dedicated radar signalc0 has
zero mean and covariance matrix Gd = E
[
c0cH0]≽ 0N×N ,
where (·)H stands for the matrix conjugate transpose and
≽ denotes positive semi-deﬁnite. Moreover, the information
signals are uncorrelated with the dedicated radar signal, i.e.,
2The algorithms proposed in this paper can be easily extended to systems
with varying UA V altitude.
3The prerequisite for UA V to successfully provide users with data transmis-
sion services is to ensure the synchronization of downlink. If synchronization
is not guaranteed, the system performance will degrade due to inter-symbol
interference and inter-carrier interference. Thus, this paper assumes that
synchronization can be achieved through synchronization signal blocks similar
to those used in 5G systems [23], [24].
TABLE I
SYMBOL NOTATIONS
E(c0cm) = 0N×1,∀m∈ M. Let wm ∈ CN×1 represent
the transmit beamforming vector for m-th user. Therefore, the
transmitted signal by the UA V is given by
c(t) =
M∑
m=1
wm(t)cm(t) +c0(t),∀t∈T . (1)
Hence, the sum transmit power of UA V is expressed as
E
(
‖c(t)‖2
)
= E


‖‖‖‖‖ M∑m=1wm(t)cm(t) +c0(t)‖‖‖‖‖2
=
M∑
m=1
‖wm(t)‖2 + tr (Gd(t)), (2)
where‖·‖ stands for the vector Frobenius norm and tr(·)
denotes matrix trace. Then the power constraint is expressed
as
M∑
m=1
‖wm(t)‖2 + tr(Gd(t))≤Pmax,∀t∈T , (3)
where Pmax is shown on Table I.
To quantitatively characterize the propagation channel,
many studies [27], [28], [29], [30] have conducted a
series of air-to-ground channel measurements in various
typical environments, including near-urban, suburban, and
hilly/mountainous areas. The air-to-ground channel model
is consistent with the LoS channel model when the UA V
altitude is above 50 meters [27], [28]. Therefore, the LoS
channel link between the UA V and ground users has also been
widely adopted in previous works [31], [32], [33], [34] for
gaining essential insights on the placement/trajectory design.
Furthermore, the Doppler effect resulting from UA V mobility
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3472 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
is assumed to be adequately compensated at both users [35],
[36] and targets [37]. Hence, the air-to-ground channel is
considered to follow the free-space path loss model. The
channel power gain from the UA V to them-th user is speciﬁed
as
βm(p(t),pm) = β0d(p(t),pm)α, (4)
where β0 and α are shown on Table I, with α characterizing
the rate at which the signal strength diminishes with distance.
d(p(t),pm) =
√
(x(t)−px,m)2 + (y(t)−py,m)2 + z2u
denotes the Euclidean distance between the UA V’s position
p(t) and the m-th user’s position pm. The transmit array
response vector of the UA V in the direction of the m-th user
is written as
b(p(t),pm)
=
[
1, ei2πdλ cosφ(p(t),pm),..., ei2πdλ (N−1) cosφ(p(t),pm)]⊤,
(5)
where φ(p(t),pm) is the angle of departure (AoD) of the
signal from the UA V to the m-th user with
φ(p(t),pm) = arccos zud(p(t),pm). (6)
Therefore, the channel vector from the UA V to the m-th user
is expressed as
gm(p(t)) =
√
βm(p(t),pm)b(p(t),pm). (7)
Then, the received signal at the m-th user is written as
sm(t) =gHm(p(t−td))c(t−td) +nm(t)
=
M∑
i=1
gHm(p(t−td))wi(t−td)ci(t−td)
+gHm(p(t−td))c0(t−td) +nm(t), (8)
where td is the time delay from when a signal is trans-
mitted by the UA V until it is received by the user, and
nm(t)∼CN (0,σ 2m) represents the additive white Gaussian
noise (AWGN) at the m-th user. The received signal power of
the m-th user is given by
E
(⏐⏐gHm(p(t−td))wm(t−td)cm(t−td)⏐⏐2)
=
⏐⏐gHm(p(t−td))wm(t−td)⏐⏐2.
Since the transmission of the communication signals and
the dedicated radar signal share the same frequency spec-
trum, the received signal of one user is interfered by the
communication signals of other users and the dedicated radar
signal.4 Speciﬁcally, for the m-th user, the average power of
the interference caused by other users’ transmissions can be
computed as
E


⏐⏐⏐⏐⏐⏐⏐⏐ M∑i=1,i⁄=mgHm(p(t−td))wi(t−td)ci(t−td)⏐⏐⏐⏐⏐⏐⏐⏐2
=
M∑
i=1,
i⁄=m
⏐⏐gHm(p(t−td))wi(t−td)⏐⏐2.
The average power of the interference at the m-th user caused
by the dedicated radar signal is given by
E
(⏐⏐gHm(p(t−td))c0(t−td)⏐⏐2)
=gHm(p(t−td))Gd(t−td)gm(p(t−td)).
The signal-to-interference-plus-noise ratio (SINR) of the
m-th user is expressed as in (9), shown at the
bottom of the page. Since the time delay td is
only a few microseconds, which is sufﬁciently short
that it does not cause signiﬁcant changes, the term
E
(⏐⏐gHm(p(t−td))wm(t−td)cm(t−td)⏐⏐2) can be
approximated as E
(⏐⏐gHm(p(t))wm(t)cm(t)⏐⏐2), and similarly
for other terms. Therefore, φm(p(t − td),{wi(t−td)},
Gd(t− td)) is approximated by φm(p(t),{wi(t)},Gd(t)),
which is written as (10), as shown at the bottom of the page.
As a result, the achievable spectral efﬁciency (data rate per
unit bandwidth) of the m-th user in bits-per-second-per-Hertz
(bps/Hz) is written as
Rm(t) = log2(1 +φm(p(t),{wi(t)}Mi=1,Gd(t))). (11)
Next, we consider the radar sensing services provided by
UA V . To enhance the sensing performance, communication
signals for the users can also be exploited for estimating target
parameter [12], [34]. Generally, the power of the sensing signal
4In fact, the other interference suppression strategies [38], [39], [40], [41]
can also be considered in our proposed framework.
φm(p(t−td),{wi(t−td)},Gd(t−td)) =
⏐⏐gHm(p(t−td))wm(t−td)⏐⏐2
M∑
i=1,
i⁄=m
|gHm(p(t−td))wi(t−td)|2 +gHm(p(t−td))Gd(t−td)gm(p(t−td)) +σ2m
.
(9)
φm(p(t),{wi(t)},Gd(t)) =
⏐⏐gHm(p(t))wm(t)⏐⏐2
M∑
i=1,
i⁄=m
|gHm(p(t))wi(t)|2 +gHm(p(t))Gd(t)gm(p(t)) +σ2m
. (10)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: CONTROL-BASED DESIGN OF BEAMFORMING AND TRAJECTORY FOR UA V-ENABLED ISAC SYSTEM 3473
Fig. 2. Force analysis of quad-rotor UA V .
directed towards target j∈J is referred to as the transmit
beam pattern gain [12], [34], [42], which is written as
Θt,j(p(t),{wm(t)},Gd(t))
= E
(⏐⏐⏐bH(p(t),oj)c(t)⏐⏐⏐2)
=bH(p(t),oj)
( M∑
m=1
wm(t)wHm(t) +Gd(t)
)
b(p(t),oj),
where b(p(t),oj) is deﬁned in (5). Due to path loss, the
received beam pattern gain at the UA V depends ond(p(t),oj),
which is adopted as the sensing performance evaluation and
is indicated by
Θr,j(p(t),{wm(t)},Gd(t)) = Θt,j (p(t),{wm(t)},Gd(t))d (p(t),oj)α .
(12)
B. Dynamic Model of Quad-Rotor UA V
1) The 3-DoF Dynamic Model: In this model, the UA V
is treated as a mass point and is characterized by the earth
frame I{x,y, z} as depicted in Fig. 2. We consider that the
gravity force mag, the drag force FD, and the lift force
FL are applied to the UA V in the earth frame I. Since the
UA V maintains a constant altitude during ﬂight, the lift force
can be derived as FL = mag/ cosχ(t), where χ(t) is the
angle between the direction of FL and the z-axis as shown in
Fig. 2.
According to the deﬁnition of the drag force FD(t) =
KdV 2(t) [43], [44], whereKd is shown on Table I andV (t) is
the velocity of the UA V , the 3-DoF model in horizontal ﬂight
is expressed as [45]
[ma¨x(t)
ma¨y(t)
]
=
[FLx(t)−FDx(t)
FLy(t)−FDy(t)
]
=
[mag tanχ(t) cosδ(t)−Kd| ˙x(t)| ˙x(t)
mag tanχ(t) sinδ(t)−Kd| ˙y(t)| ˙y(t)
]
,
(13)
where ˙x(t), ˙y(t), ¨x(t), ¨y(t), FLx(t), FLy(t), FDx(t) and
FDy(t) are the velocities, accelerations, lift forces, and drag
forces along the x and y axis, respectively.
2) The 6-DoF Dynamic Model: In this model, the UA V
is considered as a rigid body and is characterized by the
Fig. 3. Schematic view of quad-rotor UA V .
ﬁxed-body frame B{xb,yb, zb} and the earth frame I{x,y, z}.
For simplicity, Fig. 3 illustrates a UA V equipped with four
rotors.5 The UA V is operated by controlling the speed of its
propellers. For example, the vertical motion is achieved by
concurrently increasing or decreasing the speed of four pro-
pellers. The orientation vector of the UA V can be represented
by Φ(t) = [ζ(t),η (t),γ (t)]⊤.
The translational dynamics based on the Lagrange-Euler
equation and the rotational dynamics based on the Newton-
Euler equation together form a 6-DoF model [43], [45], [46],
thus the dynamic equations of a quad-rotor UA V are written
as{
ma¨p(t) =fL(t)−fD(t)−fg(t),
J ˙ω(t) =−ω(t)×Jω (t) +ϕf(t) +ϕg(t)−ϕa(t),
(14)
where fL(t) and fD(t) denote respectively the lift forces
produced via four propellers and the drag force along x, y,
and z axis [43], as shown below,
fL(t) =


cosζ(t) cosγ(t) sinη(t) + sinζ(t) sinγ(t)
cosζ(t) sinη(t) sinγ(t)− sinζ(t) cosγ(t)
cosζ(t) cosη(t)


·
4∑
i=1
Li(t), (15)
fD(t) =


Kdx 0 0
0 Kdy 0
0 0 Kdz

 ˙p(t), (16)
and fg(t) = [0 , 0,mag]⊤. In (15), Li(t) denotes the lift
force generated by the i-th propeller. Since the lift force is
proportional to the square of the propeller speed [44], it is
expressed as Li(t) =Kpξ2i (t), where Kp is shown on Table I
andξi(t) denotes the speed of the i-th propeller. In (16), Kdx,
Kdy and Kdz are shown on Table I.
In the second equation of (14), symbol ‘ ×’ denotes the
cross-product of vectors.J∈ R3×3 is the inertia matrix, which
5The algorithms developed later are applicable to UA Vs with other number
of rotors, as they are unaffected by differences in dynamic models.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3474 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
is expressed as
J =


Ixx 0 0
0 Iyy 0
0 0 Izz

.
ω(t) represents the rotational angular velocity of the quad-
rotor UA V . Under small disturbances, the rate of change of the
Euler angles is approximately equal to the body’s rotational
angular velocity, i.e., ω(t) = [ ˙ζ(t), ˙η(t), ˙γ(t)]⊤. Additionally,
ϕf(t), ϕg(t), and ϕa(t) indicate the torque generated by
the propellers, the gyroscopic torques, and the aerodynamic
friction torques, respectively [43], as shown below,
ϕf(t) =


l(L2(t)−L4(t))
l(L3(t)−L1(t))
Km(ξ21(t) +ξ23(t)−ξ22(t)−ξ24(t))

, (17)
ϕg(t) = [ImΛ(t) ˙η(t),−ImΛ(t) ˙ζ(t), 0]⊤, (18)
ϕa(t) = [Kdmx ˙ζ2(t),Kdmy ˙η2(t),Kdmz ˙γ2(t)]⊤, (19)
where l, Km, Im, Kdmx, Kdmy and Kdmz are shown on
Table I, Λ(t) =−ξ1(t) +ξ2(t)−ξ3(t) +ξ4(t).
Since the UA V ﬂies horizontally, we can deduce the total
lift force acting upon it to be [45]
4∑
i=1
Li(t) =Kp
4∑
i=1
ξ2i (t) = magcosζ(t) cosη(t). (20)
As a result, the 6-DoF model for horizontal ﬂight can be
described as in (21), shown at the bottom of the page, located
at the top of this page, where sign(b) denotes the sign of b.
C. Problem F ormulation
In this paper, the average weighted sum-rate (per Hz) of
communication is maximized by optimizing the UA V tra-
jectory, the transmit information and sensing beamforming
vectors, subjecting to the UA V dynamics model, the sensing
requirements, and the transmit power constraints. We consider
problems with the 3-DoF model and the 6-DoF model, respec-
tively.
First, we consider the problem with the 3-DoF model (13),
which is formulated as
(P1) : max
{wm(t)},
Gd(t)≽0,p(t)
Rave(p(t),{wm(t)},Gd(t))
s.t. Θr,j(p(t),{wm(t)},Gd(t))≥ Θthj ,
∀j∈J ,∀t∈T , (22a)√
˙x(t)2 + ˙y(t)2≤Vmax,∀t∈T , (22b)
p(0) =pI, (22c)
p(T ) =pF,
(3), (13). (22d)
In problem (P1), our objective is to maximize the aver-
age weighted sum-rate Rave(p(t),{wm(t)},Gd(t)) =
1
T
∫T
0
M∑
m=1
ρmRm(t)dt, where ρm denotes the weight of the
m-th user and Rm(t) is given in (11). The received beam
pattern gain constraint of UA V is shown by (22a), where Θthj
represents the beam pattern gain threshold of j-th target. The
maximum ﬂight speed constraint is given by (22b), where
Vmax is shown on Table I. In addition, (22c) and (22d) denote
the initial and ﬁnal location constraints with pI = [xI,y I, zu]⊤
andpF = [xF,y F, zu]⊤.
Next, we consider the joint design problem with the 6-
DoF model (21). This optimization problem is formulated
as
(P2) : max
{wm(t)},
Gd(t)≽0,p(t)
Rave(p(t),{wm(t)},Gd(t))
s.t. (3), (21), (22a), (22b), (22c), (22d).
Notice that the main difference between problem
(P1) and problem (P2) is the dynamic models (13)
and (21).
Solving the problems of (P1) and (P2) is highly challeng-
ing due to their nature of inﬁnite-dimensional optimization
problems. Additionally, the UA V trajectories are embedded in
the exponential part of the transmit array response vector in
an extremely complex manner, as described in (5). Moreover,
the strong coupling between the optimization variables, as
indicated in (10), and (12), further increases the difﬁculty of
computation. Problem (P2) with the 6-DoF model is particu-
larly more complicated to handle compared to problem (P1)
with the 3-DoF model, due to its involvement of more complex
dynamic characteristics, higher control complexity, and greater
computational burden. As such, we will deal with problem
(P2) in Section III, problem (P1) can be solved in a similar
manner.
III. P ROPOSED OPTIMIZATION METHOD
We address problem (P2) by adopting the alternating opti-
mization strategy in this section, due to the strong coupling
relationship between the UA V trajectory point and beam-
forming vectors. Speciﬁcally, we ﬁrst ﬁx the UA V trajectory
p(t) and design {wm(t)} and Gd(t) based on the convex
optimization technique in Section III-A. Subsequently, we
optimize the UA V trajectory p(t) with updated {wm(t)}
and Gd(t) by solving a dynamic optimization problem in
Section III-B.
A. Communication and Sensing Beamforming Optimization
For given UA V trajectoryp(t), the optimization subproblem
of communication beamforming vectors{wm(t)} and sensing


ma¨x(t)
ma¨y(t)
Ixx ¨ζ(t)
Iyy ¨η(t)
Izz¨γ(t)

 =


mag [tanη(t) cosγ(t) + cscη(t) tanζ(t) sinγ(t)]− sign( ˙x(t))Kdx ˙x2(t)
mag [tanη(t) sinγ(t)− cscη(t) tanζ(t) cosγ(t)]− sign( ˙y(t))Kdy ˙y2(t)
lKp
[
ξ22(t)−ξ24(t)] + (Iyy−Izz) ˙η(t) ˙γ(t) +ImΛ(t) ˙η(t)− sign( ˙ζ(t))Kdmx ˙ζ2(t)
lKp
[
ξ23(t)−ξ21(t)] + (Izz−Ixx) ˙ζ(t) ˙γ(t)−ImΛ(t) ˙ζ(t)− sign( ˙η(t))Kdmy ˙η2(t)
Km
[
ξ21(t) +ξ23(t)−ξ22(t)−ξ24(t)] + (Ixx−Iyy) ˙ζ(t) ˙η(t)− sign( ˙γ(t))Kdmz ˙γ2(t)

 (21)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: CONTROL-BASED DESIGN OF BEAMFORMING AND TRAJECTORY FOR UA V-ENABLED ISAC SYSTEM 3475
covariance matrix Gd(t) is expressed as
(P2.1) : max
{wm(t)},
Gd(t)≽0
1
T
∫ T
0
M∑
m=1
ρmRm({wm(t)},Gd(t))dt
s.t. (3), (22a).
To transform the above subproblem into a tractable form,
we discretize the time intervalT into P equal subintervals and
P + 1 time slots, indexed by {τn, n = 0, 1,...,P }, and
0 =τ0 <τ 1 <τ 2 <...<τ P−1 <τ P =T.
Therefore, we obtain the following discrete optimization
problem
(P2.2) : max
{wm[τn]},
Gd[τn]≽0
1
P
P∑
n=1
M∑
m=1
ρmRm({wm[τn]},Gd[τn])
s.t.
M∑
m=1
‖wm[τn]‖2 + tr(Gd[τn])≤Pmax,∀n,
(23a)
Θr,j({wm[τn]},Gd[τn])≥ Θthj ,∀n,∀j. (23b)
Since the optimization variables {wm[τn]} and Gd[τn] at
different time slots are independent, as indicated in (23a) and
(23b), we can decouple them over different time slots. This
means that problem (P2.2) can be equivalently decomposed
into P subproblems. We refer to problem (P2.2) at time slot
τn as problem (P 2.2n). As a result, the values of {wm[τn]}
and Gd[τn] at time slot τn can be obtained by solving
(P2.2n). In particular, the optimization problem at time slot
τn is written as
(P2.2n) : max
{wm[τn]},
Gd[τn]≽0
M∑
m=1
ρmRm({wm[τn]},Gd[τn])
s.t.
M∑
m=1
‖wm[τn]‖2 + tr(Gd[τn])≤Pmax, (24a)
Θr,j({wm[τn]},Gd[τn])≥ Θthj ,∀j. (24b)
By utilizing the SCA and SDR techniques, we can obtain
a high-quality solution to problem (P 2.2n). We ﬁrst deﬁne
Wm[τn] = wm[τn]wHm[τn], then rank(Wm[τn]) ≤ 1 and
Wm[τn]≽ 0. Further, (P 2.2n) is reformulated as
(P2.3) : max
{Wm[τn]≽0},
Gd[τn]≽0
M∑
m=1
ρmRm({Wm[τn]},Gd[τn])
s.t.
M∑
m=1
tr(Wm[τn]) + tr(Gd[τn])≤Pmax,
(25a)
Θr,j({Wm[τn]},Gd[τn])≥ Θthj , ∀j, (25b)
rank(Wm[τn])≤ 1, (25c)
where Rm({Wm[τn]},Gd[τn]) is represented as in (26),
shown at the bottom of the page, according to the proper-
ties of trace functions. Note that solving problem (P2.3) is
non-trivial due to the non-concavity of the objective func-
tion and the highly non-convexity of the rank constraint
given in (25c).
In the sequel, based on the facts that the ﬁrst-order Taylor
expansion of a convex function is its global under-estimator
and that of a concave function is its global over-estimator,
we approximate the objective function in (26) as a concave
function via the SCA technique in an iterative manner. Here,
we rewrite Rm({Wm[τn]},Gd[τn]) as in (27), shown at
the bottom of the page, based on the properties of the log
function. In particular, the second term in (27) is converted
into a linear function by adopting the ﬁrst-order Taylor expan-
sion, (28) as shown at the bottom of the next page, where
C(k)m = log 2(E(k)m ), D(k)m = gm(p[τn])gHm(p[τn])ln2(E(k)m ) , and E(k)m isgiven by
E(k)m =
M∑
i=1,
i⁄=m
tr
(
gm(p[τn])gHm(p[τn])W (k)i [τn])
+ tr
(
gm(p[τn])gHm(p[τn])G(k)d [τn]) +σ2m. (29)
In fact,
{
W (k)m [τn]} and G(k)d [τn] denote the local points of
{Wm[τn]} andGd[τn] at the k-th iteration. Consequently, by
Rm({Wm[τn]},Gd[τn]) = log2

1 + tr(gm(p[τn])gHm(p[τn])Wm[τn])M∑
i=1,
i⁄=m
tr
(
gm(p[τn])gHm(p[τn])Wi[τn]) + tr(gm(p[τn])gHm(p[τn])Gd[τn]) +σ2m

.
(26)
log2
( M∑
i=1
tr
(
gm(p[τn])gHm(p[τn])Wi[τn]) + tr(gm(p[τn])gHm(p[τn])Gd[τn]) +σ2m
)
− log2

 M∑
i=1,
i⁄=m
tr
(
gm(p[τn])gHm(p[τn])Wi[τn]) + tr(gm(p[τn])gHm(p[τn])Gd[τn]) +σ2m

 (27)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3476 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
replacing the objective function in problem (P2.3) with (28),
the problem at the k-th iteration is represented as
(P2.4)(k) : max
{Wm[τn]≽0},
Gd[τn]≽0
M∑
m=1
ρm ˜R(k)m ({Wm[τn]},Gd[τn])
s.t. (25a), (25b), (25c).
Next, we adopt the SDR method to tackle the non-convex
rank constraint (25c). The rank constraint can be relaxed, and
the new problem is formulated as
(P2.5)(k) : max
{Wm[τn]≽0},
Gd[τn]≽0
M∑
m=1
ρm ˜R(k)m ({Wm[τn]},Gd[τn])
s.t. (25a), (25b).
It is obvious that problem (P2.5)(k) is convex and can be
efﬁciently tackled by CVX. However, the feasible solution of
problem (P2.5)(k) may not satisfy the rank constraint (25c).
To address this issue, we can leverage Gaussian randomization
to construct the solution that meets the rank constraint. Fortu-
nately, we can provide the following proposition to guarantee
that a rank-one solution to problem (P2.4)(k) always exists.
Proposition 1: Let {W∗m[τn]}Mm=1 and G∗d[τn] be the
optimal solution of problem (P2.5)(k). We can reconstruct
equivalent solutions to problem (P2.4)(k) as ˜W∗m[τn] and˜G∗d[τn], given by
˜w∗m[τn] =(gHm(p[τn])W∗m[τn]gm(p[τn]))−1/2
·W∗m[τn]gm(p[τn]), (30)
˜W∗m[τn] = ˜w∗m[τn]( ˜w∗m[τn])H, (31)
˜G∗d[τn] =
M∑
m=1
W∗m[τn] +G∗d[τn]−
M∑
m=1
˜W∗m[τn], (32)
which satisfy the rank constraints and are feasible for problem
(P2.4)(k). The equivalent solutions ({ ˜W∗m[τn]}Mm=1, ˜G∗d[τn])
achieve the same objective value for (P2.4)(k) as the opti-
mal value achieved by
(
{W∗m[τn]}Mm=1,G∗d[τn]). Therefore,
{ ˜W∗m[τn]}Mm=1 and ˜G∗d[τn] are optimal for (P2.4)(k).
Proof: See Appendix A.
The above proposition allows us to obtain the optimal solu-
tion of problem (P2.4)(k) by solving problem (P2.5)(k). As a
result, the reconstructed solution
(
{ ˜W∗m[τn]}Mm=1, ˜G∗d[τn]) is
guaranteed to be a feasible solution of problem (P2.3). We can
provide the following proposition to guarantee the convergence
for the solution to problem (P2.3) [47].
Proposition 2: If the approximate function
˜R(k)m ({Wm[τn]},Gd[τn]) satisﬁes the conditions
(A1)− (A4), as shown at the bottom of the next page,
where symbol ‘ ∇’ denotes the differential operation. Then
each limit point of the iterations generated by the problem
(P2.4)(k) is a stationary point of the original problem (P2.3).
Proof: See Appendix B.
Consequently, we can achieve the optimal {Wm[τn]}
and Gd[τn] of problem (P2.3) by iteratively solving
problem (P2.4)(k). Speciﬁcally, in the k-th iteration, we
get the optimal
{
W (k,∗)m [τn]} and G(k,∗)d [τn] by solving
problem (P2.4)(k). Then, in the (k + 1)-th iteration, we use{
W (k,∗)m [τn]} andG(k,∗)d [τn] as the local points for computing
˜R(k+1)m ({Wm[τn]},Gd[τn]). This process continues until
convergence.
B. UA V Trajectory Optimization
For given communication beamforming vectors {wm(t)}
and the sensing covariance matrix Gd(t), the optimization
subproblem of the UA V trajectoryp(t) is represented as
(P2.6) : max
p(t)
1
T
∫ T
0
M∑
m=1
ρmRm(p(t))dt
s.t. (21), (22a), (22b), (22c), (22d).
To obtain a suboptimal but high-quality solution, we
ﬁrst reformulate the problem (P2.6) as an optimal control
problem based on the state-space model. Then, the introduced
continuous-time control vector is discretized using a control
parameterization approach. Furthermore, an exact penalty
function method is adopted to address the continuous state
inequality constraints. Based on the above techniques, we
design an efﬁcient gradient-based algorithm to optimize the
UA V trajectory.
1) State-Space Based Problem Transformation: By consid-
ering the meaning of variables in the 6-DoF model (21), the
state vector is deﬁned as [48]
x(t) = [x1(t),x 2(t),...,x 10(t)]⊤
=
[
x(t),y (t), ˙x(t), ˙y(t),ζ (t),η (t),γ (t), ˙ζ(t), ˙η(t), ˙γ(t)
]⊤
.
(33)
The control variables are deﬁned as [43], [46], [49]
u1(t) =ξ22(t)−ξ24(t),
u2(t) =ξ23(t)−ξ21(t),
u3(t) =ξ21(t) +ξ23(t)−ξ22(t)−ξ24(t), (34)
≥ log2
( M∑
i=1
tr
(
gm(p[τn])gHm(p[τn])Wi[τn]) + tr(gm(p[τn])gHm(p[τn])Gd[τn]) +σ2m
)
−

C(k)m [τn] + M∑
i=1,
i⁄=m
tr
(
D(k)m (Wi[τn]−W (k)i [τn])) + tr(D(k)m (Gd[τn]−G(k)d [τn]))

 ≜ ˜R(k)m ({Wm[τn]},Gd[τn]).
(28)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: CONTROL-BASED DESIGN OF BEAMFORMING AND TRAJECTORY FOR UA V-ENABLED ISAC SYSTEM 3477
thus the control vector is described as
u(t) = [u1(t),u 2(t),u 3(t)]⊤. (35)
Based on (33) and (35), the state-space model of (21) is written
as in (36), shown at the bottom of the page. We obtain from
(36) that the UA V trajectory can be optimized by adjusting
the control variables u1(t),u2(t), and u3(t), where lKpu1(t),
lKpu2(t), and Kmu3(t) denote the torques produced along
the x, y, and z axis, respectively.
For brevity, (36) can be abbreviated as
˙x(t) =h(x(t),u(t)). (37)
Thus, the problem (P2.6) is written as the optimal control
problem in the following form
(P2.7) : max
x(t),u(t)
1
T
∫ T
0
M∑
m=1
ρmRm (x(t|u)) dt
s.t. (37),
|ui(t)|≤ Umaxi ,i = 1, 2, 3, ∀t, (38a)
Θr,j (x(t|u),oj)≥ Θthj , ∀j, ∀t, (38b)√
x3(t)2 +x4(t)2≤Vmax, ∀t, (38c)
x(0) = ˆx0, (38d)
x1(T ) =xF,x 2(T ) =yF, (38e)
where ˆx0 =
[
x0,y 0, ˙x0, ˙y0,ζ 0,η 0,γ 0, ˙ζ0, ˙η0, ˙γ0
]⊤
. For practi-
cal reasons, (38a) is introduced to constrain the maneuvering
capability of the UA V . Additionally, (38d) provides the initial
state vector essential for solving the differential equations in
(37). The remaining constraints are derived by reformulating
the constraints from problem (P2) in terms of x(t) andu(t).
Remark 1: The optimal control problem (P2.7) is extremely
difﬁcult to solve optimally due to the fact that the control vari-
ables are multi-dimensional continuous-time function (38a) as
well as there are inﬁnite state constraints in (38b) and (38c). To
address these issues, a control parametrization technique and
an exact penalty function method are adopted to transform
problem (P2.7) into a solvable form.
Fig. 4. The process of control parametrization.
2) Control Parametrization: In this paper, we adopt a piece-
wise constant function to parameterize the control variables
[50]. As shown in Fig. 4, the parametrization function of
control variable ui(t),i = 1, 2, 3 is expressed as
ui(t) =
P∑
n=1
ϑniϖ[τn−1,τn)(t), ∀t∈T , (39)
where ϖ[τn−1,τn) is deﬁned as follows
ϖ[τn−1,τn)(t) =
{
1, t ∈ [τn−1,τn)
0, t /∈ [τn−1,τn),
and τn,n = 1, 2,...,P are ﬁxed times that remain the same
as those in subproblem 1.
By letting ϑn = [ ϑn1,ϑn2,ϑn3 ]⊤,n = 1 , 2,...,P , and
ϑ =
[
(ϑ1)⊤, (ϑ2)⊤,..., (ϑP )⊤
]⊤
, we rewrite the dynamic
system (37) as
˙x(t) =h(x(t),ϑn), ∀t∈P n, n = 1, 2,...,P, (40)
wherePn = TP× [n− 1,n ). By replacing u(t) with ϑ, the
constraints (38a) and (38b) are rewritten as
|ϑni|≤ Umaxi , i = 1, 2, 3, ∀n, (41)
Θr,j (x(t|ϑn ),oj)≥ Θthj , ∀t∈P n, ∀j. (42)
3) Exact Penalty Function Method: To deal with the count-
less state inequality constraints given in (38b) and (38c), we
employ an exact penalty function method to incorporate these
(A1) ˜R(k)m
({
W (k)m [τn]},G(k)d [τn]) =Rm({W (k)m [τn]},G(k)d [τn]).
(A2) ˜R(k)m ({Wm[τn]},Gd[τn])≤Rm({Wm[τn]},Gd[τn]).
(A3)∇ ˜R(k)m
⏐⏐⏐⏐({W (k)m [τn]},G(k)d [τn]) =∇Rm⏐⏐⏐⏐({W (k)m [τn]},G(k)d [τn]) .
(A4) ˜R(k)m ({Wm[τn]},Gd[τn]) is continuous in ({Wm[τn]},Gd[τn]).



˙x1(t) =x3(t), ˙x2(t) =x4(t),
˙x3(t) =g (tanx6(t) cosx7(t) + cscx6(t) tanx5(t) sinx7(t))− sign (x3(t))Kdxx23(t)/ma,
˙x4(t) =g (tanx6(t) sinx7(t)− cscx6(t) tanx5(t) cosx7(t))− sign (x4(t))Kdyx24(t)/ma,
˙x5(t) =x8(t), ˙x6(t) =x9(t), ˙x7(t) =x10(t),
˙x8(t) =
[
lKpu1(t) + (Iyy−Izz)x9(t)x10(t) +ImΛ(t)x9(t)− sign (x8(t))Kdmxx28(t)]/Ixx,
˙x9(t) =
[
lKpu2(t) + (Izz−Ixx)x8(t)x10(t)−ImΛ(t)x8(t)− sign (x9(t))Kdmyx29(t)]/Iyy,
˙x10(t) =
[
Kmu3(t) + (Ixx−Iyy)x8(t)x9(t)− sign (x10(t))Kdmzx210(t)]/Izz.
(36)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3478 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
constraints into the objective function, thereby transform-
ing the constrained nonlinear programming problem into an
unconstrained optimization problem. We redeﬁne the objective
function by utilizing the exact penalty function method, as in
(43), shown at the bottom of the page [48], where Q(x(t|ϑ))
is the original objective function and is represented by
Q(x(t|ϑ))=− 1T
P∑
n=1
∫
Pn
M∑
m=1
ρmlog2(1+φm(x(t|ϑn ) ) )dt,
φm(x(t|ϑn )) =
⏐⏐gHm(x(t|ϑn ))wm[τn]⏐⏐2
M∑
i= 1,
i⁄=m
|gHmwi[τn]|2+gHmGd[τn]gm+σ2m
.
Γ (x(t|ϑ),ς ) in (43) is the constraint violation term, which is
expressed as
Γ (x(t|ϑ),ς )
=
P∑
n=1
∫
Pn
[ J∑
j=1
max
{
0, Θthj − Θr,j(x(t|ϑn ), oj)−ςϵO}2
+ max
{
0,
√
x3(t)2 +x4(t)2−Vmax−ςϵO}2] dt. (44)
Ω(x(T|ϑ)) in (43) is the terminal state constraint violation function,
which is given as follows
Ω(x(T|ϑ)) = (x1(T )−xF)2 + (x2(T )−yF)2. (45)
In (43), µ > 0 denotes the penalty parameter, and κ, θ, ϵ, O are
given constants satisfying κ> 0, θ> 2, ϵ> 0, O∈ (0, 1).
Based on the above discussion, problem (P2.7) can be translated
into the following form
(P2.7)ϑ,ς : minϑ,ς Qµ(x(t|ϑ),ς )
s.t. ς∈ [0,ς max],
(38d), (40), (41), (46)
where
Qµ(x(t|ϑ),ς ) =F(x(T|ϑ),ς ) +
P∑
n=1
∫
Pn
H(t, x(t|ϑn ),ς )dt,
(47)
F(x(T|ϑ),ς ) =µςθ +ς−κΩ(x(T|ϑ)), (48)
and
H(t, x(t|ϑn ),ς )
=− 1T
M∑
m=1
ρmlog2(1 +φm(x(t|ϑn )))
+ς−κ
[ J∑
j=1
max
{
0, Θthj − Θr,j(x(t|ϑn ), oj)−ςϵO}2
+ max
{
0,
√
x3(t)2 +x4(t)2−Vmax−ςϵO}2]. (49)
Note that given the system (38d) and (40), problem (P2.7)ϑ,ς
is a static nonlinear programming problem, subjecting to only box
constraints (41) and (46). Once the gradients of the objective function
Qµ(x(t|ϑ),ς ) with respect to ϑ and ς are obtained, the problem
(P2.7)ϑ,ς can be solved. As such, the calculation of gradients is
crucial to the solution of the problem. The steps of calculating the
gradients are shown in Appendix C. Note that Theorems 9.3.2, 9.3.3,
and 9.3.4 in [48] show that the solution of problem (P2.7) converges
to a local optimum by solving a series of problems (P2.7)ϑ,ς.
Algorithm 1 Solving Problem (P2)
Input:{wm},Gd,p,ϑ.
Output:{w∗m},G∗d,p∗,ϑ∗.
Initialization: υ = 1 , Γth = 0 .5, {w(υ)m} = {wm},
G(υ)d =Gd,p(υ) =p,ϑ(υ) =ϑ, R(1)ave = 1, R(0)ave = 0.
1: While R(υ)ave−R(υ−1)ave ≥ Γth do
2: Solve problem (P2.2) under {w(υ)m},G(υ)d ,p(υ) to obtain
{w(υ,∗)m },G(υ,∗)d .
3: Solve problem (P2.7) under {w(υ,∗)m },G(υ,∗)d ,ϑ(υ) to
obtainp(υ,∗),ϑ(υ,∗), as shown in Algorithm 2.
4: Let υ =υ + 1,{w(υ)m} ={w(υ−1,∗)m },G(υ)d =G(υ−1,∗)d ,
p(υ) =p(υ−1,∗),ϑ(υ) =ϑ(υ−1,∗).
5: End while.
6: Output{w∗m} ={w(υ)m},G∗d =G(υ)d ,p∗ =p(υ),ϑ∗ =
ϑ(υ).
C. The Overall Algorithm
Based on the analysis in the previous two subsections,
the design of beamforming vectors in Section III-A and
the optimization of the UA V trajectory in Section III-B, we
propose an efﬁcient iterative algorithm for solving problem
(P2) via the alternating optimization strategy, as presented
in Algorithm 1. Speciﬁcally, we partition all optimization
variables into two blocks. Given the other block of variables,
we alternately optimize the beamforming vectors by solving
problem (P2.2) and the UA V trajectory by solving problem
(P2.7), respectively. Furthermore, the obtained solution in each
outer iteration υ≥ 1 is used as the input of the next iteration.
Finally, we obtain an efﬁcient solution until the increase
of the average weighted sum-rate Rave is below a ﬁxed
threshold Γth.
In Algorithm 1, the main computational complexity arises
from Steps 2 and 3. In Step 2, the beamforming{wm[τn]} and
Gd[τn] are obtained by the semidenite programming method.
Thus, the number of iterations required to reduce the duality
gap to a threshold is bounded above by O
(√
Nc∑
n=1
Dn
)
,
where Nc and Dn denote the number of constraints and
the dimension of the n-th constraint, respectively. In problem
(P2.5)(k),
Nc∑
n=1
Dn = (MN +N +J + 1). According to [51],
the computational complexity of solving problem (P2.5)(k)
is expressed as O(
√
MN +N +J + 1(MN 2 + N2)2
Qµ (x(t|ϑ),ς ) =



Q (x(t|ϑ)) ς = 0, Γ (x(t|ϑ),ς ) = 0,
Q(x(t|ϑ)) +ς−κ (Γ (x(t|ϑ),ς ) + Ω(x(T|ϑ))) +µςθ ς >0,
∞ otherwise.
(43)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: CONTROL-BASED DESIGN OF BEAMFORMING AND TRAJECTORY FOR UA V-ENABLED ISAC SYSTEM 3479
(M2N2 +N2 +J + 1)), where (MN 2 +N2) is the number
of variables. In Step 3, we adopt the SQP approach to
compute the UA V trajectoryp(t), resulting in a computational
complexity ofO((NuP +1)2) [45], [52] whereNu denotes the
number of control variables. Therefore, the total complexity
of Algorithm 1 is expressed as in (50), shown at the bottom
of the page, where Ib and Iu are the iterations required for
solving (P2.2) and (P2.7), respectively.
We would like to note that problem (P1) can be solved
similar to problem (P2) by executing the steps in Algorithm
1 and replacing the 6-DoF model (21) with the 3-DoF model
(13). Since the number of control variables in (P1) is less
than that of the control variables in (P2), the computational
complexity of (P1) is less than that of (P2). However, the
planned trajectories of (P1) cannot be accurately followed
which results in performance degradation in contrast to (P2).
Therefore, problem (P1) with the 3-DoF model achieves a
balance between computational complexity and performance.
Algorithm 2 Solving Problem (P2.7)
Input:ϑ0.
Output:ϑ∗.
Initialization: o = 0, µ(0) = 10, ς(0) = 0.1, ϑ(0) =ϑ0,
ςmin = 10−9, µmax = 108, θ> 2.
1: Problem (P2.7)ϑ,ς under (ϑ(o),ς (o)) is solved as shown
in Algorithm 3, and (ϑ(o,∗),ς (o,∗)) is the optimal solution
obtained. Then, x(o,∗) is calculated by (40).
2: While ς(o,∗) >ς min, µ(o) <µ max do
3: Let µ(o+1) = 10µ(o), ς(o+1) = ς(o,∗), ϑ(o+1) = ϑ(o,∗),
o =o + 1, then go to Step 1.
4: End while
5: Let ς(o,∗) =ςmin.
6: Ifx(o),∗ is feasible do
7: Exit.
8: Else
9: Adjust the parameters κ, θ, and ϵ. Let µ(o+1) = 10µ(o),
ς(o+1) = 0.1ς(o), o =o + 1, then go to Step 1.
10: End if
11: Outputϑ∗ =ϑ(o,∗).
Algorithm 3 Solving Problem (P2.7)ϑ,ς
Input:ϑ(o) and ς(o).
Output:ϑ(o+1) and ς(o+1).
1: The control vectoru(o)(t) is calculated byϑ(o) according
to (39).
2: The state vector x(o)(t) is obtained by solving the differ-
ential equations (40) with u(o)(t).
3: The gradients of the objective function Qµ concerning
ϑ(o) and ς(o) are calculated.
4: Input the values obtained in the ﬁrst three steps into the
nonlinear program solver.
5: Outputϑ(o+1) and ς(o+1).
TABLE II
PARAMETERS FOR SIMULATIONS
Remark 2: In Step 3 and Step 9 of Algorithm 2, the penalty
parameter µ is increased. This is because with the increase
of µ, ςθ will be reduced to minimize Qµ (x(t|ϑ),ς ) given
in (43). Since θ is constant, ς will be reduced which leads
to an increase of ς−κ. Hence, the value of Γ (x(t|ϑ),ς ) and
Ω(x(T|ϑ)) must diminish to meet the sensing requirement
(38b), the velocity constraint (38c) and the terminal constraint
(38e).
IV. N UMERICAL EXAMPLE
To validate the effectiveness of our proposed schemes, we
compare our proposed schemes to the benchmark scheme
with the model-free approach [15] (which is referred to as
P0). Unless speciﬁed differently, the system parameters can
be found in Table II [53]. In the simulation, we consider
that the UA V starts at pI = [450m, 525m]⊤ and ends at
pF = [550m, 525m]⊤. Meanwhile, M = 8 ground users
are located at p1 = [370m, 400m], p2 = [380m, 345m],
p3 = [420m , 300m], p4 = [470m , 275m], p5 =
[530m, 275m], p6 = [580m, 300m], p7 = [620m, 345m],
p8 = [630m, 400m]. Furthermore, a matrix sensing region
is considered, with a midpoint at [500m, 600m], a length
of 80 meters and a width of 20 meters, with a total of
J = 18 sensing points. The beam pattern gain threshold
Θthj = 1e−7 W (−40 dBm) , ∀j ∈ J. The UA V initial
conditions for P1 and P2 are set as [p⊤I ,−12,−27.4955]⊤
and [p⊤I ,−1,−15, 0.67638,−0.001,−0.26295, 0, 0, 0]⊤,
respectively.
The planned trajectories of P0, P1 and P2 are plotted in
Fig. 5. As depicted in Fig. 5, the planned trajectories of
the three schemes look similar. During the ﬂight, the UA V
continually strives to approach users for more communication
throughput. However, the UA V cannot reach the user position,
as it needs to maintain a suitable sensing distance from the
sensing area to satisfy the requirement of sensing beam pattern
gain.
The actual trajectories of P0 and P1 are plotted in Fig. 6,
which are obtained by designing the proportional-integral-
derivative (PID) controller with (21) to track the planned
trajectories. The process of obtaining the actual trajectory is
shown in Fig. 7. It is evident from Fig. 6 that the actual
O
(
IbP
√
MN +N +J + 1(MN 2 +N2)2(M2N2 +N2 +J + 1) +Iu(NuP + 1)2
)
. (50)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3480 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 5. The planned trajectories of P0, P1 and P2.
trajectory of P0 cannot reach the destination, while that of P1
can. This phenomenon occurs because the planned trajectory
of P0 does not take into account the UA V dynamics, giving rise
to the control inputs required for the planned trajectory beyond
the execution capabilities of the UA V system. Therefore, the
UA V fails to track the planned trajectory of P0. Although
the actual trajectory of P1 can complete the main task as
required, it cannot exactly follow the planned trajectory due
to the absence of the 6-DoF model. This underscores the
importance of incorporating the 6-DoF model in the trajec-
tory planning process, while also exposing the fact that the
planned trajectory of P2 is the actual ﬂight trajectory of the
UA V .
The received beam pattern gain of UA V versus time at
sensing point [500m, 600m] is plotted in Fig. 8. As depicted
in Fig. 8, the received beam pattern gain of the UA V ﬁrst
decreases and then increases for all trajectories. This trend
arises because as the UA V approaches the users, the sensing
distance between the UA V and the sensing position gradually
increases, leading to a gradual decline in sensing performance.
Subsequently, as the UA V ﬂies away towards its destina-
tion, the sensing distance gradually decreases, resulting in an
improvement in sensing performance. Additionally, we can
observe that although the beam pattern gain of the planned
trajectory of P0, P1 and P2 is always greater than the prede-
termined threshold Θth, there are moments where that of the
actual trajectory of P0 and P1 is less than Θth. This indicates
that the sensing performance constraint is violated at these
moments. The violation occurs because the actual trajectory
of the UA V deviates from the pre-planned trajectory, and the
actual trajectory points fail to meet the sensing performance
constraints. Compared with the proposed scheme P1, there is a
longer duration of constraint violation in the actual trajectory
of P0 due to the larger deviation between its actual and planned
trajectories.
The average rate versus the received beam pattern gain
threshold Θth under different trajectories is plotted in Fig. 9.
As depicted in Fig. 9, with the increase of Θth, the average
rate of each scheme decreases. This is attributed to the fact
that the UA V needs to spend more transmit power to meet
higher sensing requirements, thereby leaving less transmit
power for communication. Additionally, it is observed that
the communication performance of the planned trajectory of
P0 and P1 outperforms that of the planned trajectory of
P2. However, the communication performance of the actual
trajectories for P0 and P1 is not only inferior to their respec-
tive planned trajectories, but also falls below that of the
planned trajectory for P2. The performance degradation of
P0 and P1 occurs primarily due to the absence of the UA V
complex 6-DoF dynamics. Although the proposed scheme P2
achieves a signiﬁcant performance improvement in real-ﬂight,
the P2 scheme has a higher complexity than the P1 and P0
schemes. Consequently, the proposed scheme provides useful
complexity-performance trade-offs which can be exploited in
practical UA V-enabled ISAC system design.
V. C ONCLUSION
This paper considers a control-based novel UA V-enabled
ISAC system with dynamic model, where a UA V equipped
with multiple antennas provides users with downlink commu-
nication service while simultaneously sensing areas of interest.
A control-based alternating optimization algorithm for jointly
designing communication and sensing beamforming vectors
as well as UA V trajectories is developed. The methods from
SCA and SDR are adopted to transform the beamforming opti-
mization subproblem into a convex problem. The techniques of
control parametrization and exact penalty function are utilized
to convert the dynamic trajectory optimization subproblem
into a form that can be efﬁciently tackled as a nonlinear
program. Simulation results demonstrate that, in comparison
to the existing scheme, the proposed scheme can markedly
reduce the degradation of communication performance and
the violation of sensing constraints. Moreover, the design
scheme incorporating the 3-DoF model achieves a good trade-
off between the complexity and performance.
APPENDIX A
PROOF OF PROPOSITION 1
For the simplicity of notation, we omit the notations (k)
and [τn] in the following. We show that { ˜W∗m}Mm=1 and ˜G∗d
are the optimal solution of problem (P2.4)(k). In view of (30)
and (31), it is not difﬁcult to see that { ˜W∗m}Mm=1 are positive
semi-deﬁnite and meet the rank constraint in (25c). Likewise,
substituting (31) and (32) into (25a) and (25b), it can be shown
that the sensing requirements in (25b) and the transmit power
constraints in (25a) are satisﬁed.
Then, we need to show that ˜G∗d is positive semi-deﬁnite.
For any y∈ CN×1, m∈M , it follows that
yH(W∗m− ˜W∗m)y
=yHW∗my−yH ˜w∗m( ˜w∗m)Hy
=yHW∗my−(gHm(p)W∗mgm(p))−1⏐⏐yHW∗mgm(p)⏐⏐2.
Using the Cauchy-Schwarz inequality, it is evident that
⏐⏐yHW∗mgm(p)⏐⏐2 =⏐⏐yHw∗m(w∗m)Hgm(p)⏐⏐2
≤
⏐⏐yHw∗m⏐⏐2⏐⏐gHm(p)w∗m⏐⏐2
= (yHW∗my)(gHm(p)W∗mgm(p)). (51)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: CONTROL-BASED DESIGN OF BEAMFORMING AND TRAJECTORY FOR UA V-ENABLED ISAC SYSTEM 3481
Fig. 6. A comparison between the existing scheme and the proposed scheme.
Fig. 7. The process of obtaining the actual trajectory.
Fig. 8. The received beam pattern gain versus time.
Fig. 9. The average sum rate versus Θth.
Therefore, we can obtain
yH(W∗m− ˜W∗m)y≥ 0, (52)
which means that W∗m− ˜W∗m≽ 0. Due to G∗d≽ 0, this
further implies that ˜G∗d≽ 0 based on (32).
Following that, we also need to show that the
value of the objective function (28) with the new
solution
(
{ ˜W∗m}Mm=1, ˜G∗d) is consistent with that of(
{W∗m}Mm=1,G∗d). According to (31), we can get that
gHm(p) ˜W∗mgm(p) =gHm(p)W∗mgm(p). (53)
Substituting (32) and (53) into (28), for ∀m∈M , we can
obtain that
M∑
i=1
tr
(
gm(p)gHm(p) ˜W∗i) + tr(gm(p)gHm(p) ˜G∗d)
=
M∑
i=1
tr
(
gm(p)gHm(p)W∗i) + tr(gm(p)gHm(p)G∗d), (54)
Cm +
M∑
i=1,
i⁄=m
tr
(
Dm( ˜W∗i−W∗i )) + tr(Dm( ˜G∗d−Gd))
=Cm +
M∑
i=1,
i⁄=m
tr
(
Dm(W∗i−Wi)) + tr(Dm(G∗d−Gd)).
(55)
Thus, it follows from (54) and (55) that the objective
value achieved by
(
{ ˜W∗m}Mm=1, ˜G∗d) is identical to that of(
{W∗m}Mm=1,G∗d). Based on the above discussion, we show
that
(
{ ˜W∗m}Mm=1, ˜G∗d) is the optimal solution of problem
(P2.5)(k), and { ˜W∗m}Mm=1 also meet the rank constraint in
(25c). Thus,
(
{ ˜W∗m}Mm=1, ˜G∗d) is also the optimal solution of
(P2.4)(k).
APPENDIX B
PROOF OF PROPOSITION 2
For the simplicity of notation, we omit the notation [τn] in
the following. Since the nonconvex functionRm({Wm},Gd)
is approximated as the concave function ˜R(k)m ({Wm},Gd) by
adopting the ﬁrst-order Taylor expansion, as shown in (28), it
is not difﬁcult to see that conditions ( A1)-(A4) are satisﬁed.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3482 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Furthermore, the ﬁrst-order Taylor expansion of
log2


M∑
i=1,i⁄=m
tr
(
gm(p)gHm(p)Wi)+tr(gm(p)gHm(p)Gd)+σ2m


is its global over-estimator. As such, problem (P2.4)(k)
maximizes a lower bound of the objective function
Rm({Wm},Gd) of problem (P2.3), and the lower bound
and the objective function of (P2.3) are equal only at the
local point
({
W (k)m },G(k)d ); thus, the objective value
of problem (P2.3) with the solution obtained by solving
problem (P2.4)(k) is no smaller than that with the local point({
W (k)m },G(k)d ). This means that the sequence of objective
function values is not decreasing. Moreover, the objective
function has an upper bound since the channel capacity is
limited. Combining with the monotone bounded theorem
[54], we can obtain that the sequence of objective function
values obtained by solving a series of problems (P2.4)(k)
converges.
Assume that there exists a subsequence
({
W (kj)m },G(kj)d )
converging to a limit point
({
W∗m},G∗d). According to (A4),
the gradient of the approximation function is consistent with
that of the original function at the local point
({
W∗m},G∗d).
Combined with the fact that each iteration solution is the
extreme point of the approximation problem, this implies that({
W∗m},G∗d) is a stationary point of the original problem
(P2.3).
APPENDIX C
THE DERIVATION OF GRADIENT
According to the derivative rule, the gradient of the objective
function Qµ(x(t|ϑ),ς ) with respect to ϑni, i = 1, 2, 3, n =
1, 2,...,P is denoted as follows
∂Qµ(x(t|ϑ),ς )
∂ϑni
= ∂F(x(T|ϑ),ς )∂ϑni
+
∫ T
0
[∂H(t,x(t|ϑ),ς )
∂ϑni + ∂H(t,x(t|ϑ),ς )∂x ∂x(t)∂ϑni
]
dt
+ ∂F(x(T|ϑ),ς )∂x ∂x(T|ϑ)∂ϑni . (56)
There is implicit relationship between x(t|ϑ) andϑni , thus∂x(t|ϑ )
∂ϑni needs to be computed with certain skills. For ∀t∈T ,x(t|ϑ) can be represented by
x(t|ϑ) =x(0) +
∫ t
0
h(x(τ|ϑ),ϑ)dτ. (57)
Hence, the gradient of x(t|ϑ) with respect to ϑni is denoted
as
∂x(t|ϑ)
∂ϑni = ∂x(0)∂ϑni
+
∫ t
0
[∂h(x(τ|ϑ),ϑ)
∂x
∂x(τ|ϑ)
∂ϑni + ∂h(x(τ|ϑ),ϑ)∂ϑni
]
dτ.
(58)
With t = 0 , (58) is equivalent to ∂x(0|ϑ )∂ϑni = ∂x(0)∂ϑni . Byconsidering the derivative of both sides of (58) concerning
t, we can get
d
dt
(∂x(t|ϑ)
∂ϑni
)
= ∂h(x(τ|ϑ),ϑ)∂x ∂x(t|ϑ)∂ϑni
+ ∂h(x(τ|ϑ),ϑ)∂ϑni . (59)
Deﬁne ∂x(t|ϑ)
∂ϑni =ρni (t), ∀t∈T , (60)
henceρni (t) satisﬁes the following auxiliary dynamic system


ρni (0) = ∂x(0)∂ϑni ,dρni (t)
dt = ∂h(x(t|ϑ),ϑ)∂x ρni (t) +∂h(x(t|ϑ),ϑ)∂ϑni . (61)
It follows fromx(0) is independent ofϑni thatρni (0) = 010×1.
In addition, deﬁne
∂F(x(T|ϑ),ς )
∂ϑni =ιni,∂F(x(T|ϑ),ς )∂x = ˙Ψ, (62)
∂H(t,x(t|ϑ),ς )
∂ϑni =εni,∂H(t,x(t|ϑ),ς )∂x = ˜Ψ. (63)
Thus, by substituting (60), (62), and (63) into (56), we can
get
∂Qµ(x(t|ϑ),ϑ,ς )
∂ϑni
=ιni + ˙Ψ⊤ρni (T|ϑ) +∫ T
0
(
εni + ˜Ψ⊤ρni (t|ϑ))dt. (64)
Similarly, the gradient of the objective function
Qµ(x(t|ϑ),ς ) with respect to ς is expressed as follows,
∂Qµ(x(t|ϑ),ς )
∂ς
= ∂F(x(T|ϑ),ς )∂ς +∫ T0 ∂H(t,x(t|ϑ),ς )∂ς dt, (65)
where
∂F(x(T|ϑ),ς )
∂ς =µθςθ−1 + (−κ)ς−κ−1Ω(x(T|ϑ)), (66)
∂H(t,x(t|ϑ),ς )
∂ς
=f1


J∑
j=1
max
{
0, Θthj − Θr(x(t|ϑ),pj)−ςϵO}2
+ max
{
0,
√
x3(t)2 +x4(t)2−Vmax−ςϵO}2]
+f2


J∑
j=1
max
{
0, Θthj − Θr(x(t|ϑ),pj)−ςϵO}
+ max
{
0,
√
x3(t)2 +x4(t)2−Vmax−ςϵO}]. (67)
In (67), f1 =−κς−κ−1, f2 =−2Oϵςϵ−κ−1. We substitute
(66) and (67) into (65), this thus completes the gradient
calculation.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: CONTROL-BASED DESIGN OF BEAMFORMING AND TRAJECTORY FOR UA V-ENABLED ISAC SYSTEM 3483
REFERENCES
[1] J. A. Zhang et al., “Enabling joint communication and radar sensing
in mobile networks—A survey,” IEEE Commun. Surveys Tuts. , vol. 24,
no. 1, pp. 306–345, 1st Quart., 2022.
[2] V . Petrov et al., “On uniﬁed vehicular communications and radar sensing
in millimeter-wave and low terahertz bands,” IEEE Wireless Commun. ,
vol. 26, no. 3, pp. 146–153, Jun. 2019.
[3] J. A. Zhang, X. Huang, Y . J. Guo, J. Yuan, and R. W. Heath Jr.,
“Multibeam for joint communication and radar sensing using steerable
analog antenna arrays,” IEEE Trans. V eh. Technol. , vol. 68, no. 1,
pp. 671–685, Jan. 2019.
[4] J. Liu, H. Liu, Y . Chen, Y . Wang, and C. Wang, “Wireless sensing for
human activity: A survey,” IEEE Commun. Surveys Tuts. , vol. 22, no. 3,
pp. 1629–1645, 3rd Quart., 2020.
[5] F. Liu, C. Masouros, A. P. Petropulu, H. Grifﬁths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun., vol. 68, no. 6, pp. 3834–3862, Jun.
2020.
[6] Z. Xiao, S. Chen, and Y . Zeng, “Simultaneous multi-beam sweeping for
mmWave massive MIMO integrated sensing and communication,” IEEE
Trans. V eh. Technol., vol. 73, no. 6, pp. 8141–8152, Jun. 2024.
[7] W. Yuan, Z. Wei, S. Li, J. Yuan, and D. W. K. Ng, “Integrated sensing
and communication-assisted orthogonal time frequency space transmis-
sion for vehicular networks,” IEEE J. Sel. Topics Signal Process. ,
vol. 15, no. 6, pp. 1515–1528, Nov. 2021.
[8] J. A. Zhang et al., “An overview of signal processing techniques for joint
communication and radar sensing,” IEEE J. Sel. Topics Signal Process. ,
vol. 15, no. 6, pp. 1295–1315, Nov. 2021.
[9] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[10] X. Zhao, H. Liu, S. Gong, X. Ju, C. Xing, and N. Zhao, “Dual-functional
MIMO beamforming optimization for RIS-aided integrated sensing and
communication,” IEEE Trans. Commun., vol. 72, no. 9, pp. 5411–5427,
Sep. 2024.
[11] X. Zhao and Y .-J. A. Zhang, “Joint beamforming and scheduling for
integrated sensing and communication systems in URLLC: A POMDP
approach,” IEEE Trans. Commun., vol. 72, no. 10, pp. 6145–6161, Oct.
2024.
[12] H. Hua, J. Xu, and T. X. Han, “Optimal transmit beamforming for
integrated sensing and communication,” IEEE Trans. V eh. Technol. ,
vol. 72, no. 8, pp. 10588–10603, Aug. 2023.
[13] G. Cheng, Y . Fang, J. Xu, and D. W. K. Ng, “Optimal coordi-
nated transmit beamforming for networked integrated sensing and
communications,” IEEE Trans. Wireless Commun. , vol. 23, no. 8,
pp. 8200–8214, Aug. 2024.
[14] R. Li, Z. Xiao, and Y . Zeng, “Toward seamless sensing coverage for
cellular multi-static integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 23, no. 6, pp. 5363–5376, Jun. 2024.
[15] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[16] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[17] R. Chai, X. Cui, R. Sun, D. Zhao, and Q. Chen, “Precoding and
trajectory design for UA V-assisted integrated communication and sensing
systems,” IEEE Trans. V eh. Technol., vol. 73, no. 9, pp. 13151–13163,
Sep. 2024.
[18] R. Zhang, Y . Zhang, R. Tang, H. Zhao, Q. Xiao, and C. Wang, “A joint
UA V trajectory, user association, and beamforming design strategy for
multi-UA V-assisted ISAC systems,” IEEE Internet Things J. , vol. 11,
no. 18, pp. 29360–29374, Sep. 2024.
[19] A. Hassanien, M. G. Amin, Y . D. Zhang, and F. Ahmad, “Dual-function
radar-communications: Information embedding using sidelobe control
and waveform diversity,” IEEE Trans. Signal Process. , vol. 64, no. 8,
pp. 2168–2181, Apr. 2016.
[20] Q. Li, K. Dai, Y . Zhang, and H. Zhang, “Integrated waveform for a
joint radar-communication system with high-speed transmission,” IEEE
Wireless Commun. Lett. , vol. 8, no. 4, pp. 1208–1211, Aug. 2019.
[21] X. Yuan, Y . Hu, and A. Schmeink, “Joint design of UA V trajectory
and directional antenna orientation in UA V-enabled wireless power
transfer networks,” IEEE J. Sel. Areas Commun. , vol. 39, no. 10,
pp. 3081–3096, Oct. 2021.
[22] N. Garcia, H. Wymeersch, E. G. Larsson, A. M. Haimovich, and
M. Coulon, “Direct localization for massive MIMO,” IEEE Trans. Signal
Process., vol. 65, no. 10, pp. 2475–2487, May 2017.
[23] NR; Physical Channels and Modulation , Standard
38.211, 3rd Generation Partnership Project (3GPP), Nov.
2017. [Online]. Available: https://www.etsi.org/deliver/
etsi ts/138200 138299/138211/15.02.00 60/ts 138211v150200p.pdf
[24] C. Johnson, 5G New Radio in Bullets . Farnham, U.K.: Independently
published, 2019.
[25] F. Liu, C. Masouros, A. Li, H. Sun, and L. Hanzo, “MU-MIMO
communications with MIMO radar: From co-existence to joint
transmission,” IEEE Trans. Wireless Commun. , vol. 17, no. 4,
pp. 2755–2770, Apr. 2018.
[26] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. Eldar, “Joint
transmit beamforming for multiuser MIMO communications and MIMO
radar,” IEEE Trans. Signal Process. , vol. 68, pp. 3929–3944, 2020.
[27] R. Amorim, H. Nguyen, P. Mogensen, I. Z. Kov ´acs, J. Wigard, and
T. B. Sørensen, “Radio channel modeling for UA V communication
over cellular networks,” IEEE Wireless Commun. Lett. , vol. 6, no. 4,
pp. 514–517, Aug. 2017.
[28] S. D. Muruganathan et al., “An overview of 3GPP release-15 study
on enhanced LTE support for connected drones,” IEEE Commun.
Standards Mag., vol. 5, no. 4, pp. 140–146, Dec. 2021.
[29] D. W. Matolak and R. Sun, “Air–ground channel characterization
for unmanned aircraft systems—Part III: The suburban and near-
urban environments,” IEEE Trans. V eh. Technol. , vol. 66, no. 8,
pp. 6607–6618, Aug. 2017.
[30] K. Mao et al., “A survey on channel sounding technologies and
measurements for UA V-assisted communications,” IEEE Trans.
Instrum. Meas. , vol. 73, pp. 1–24, 2024.
[31] Q. Wu, Y . Zeng, and R. Zhang, “Joint trajectory and communication
design for multi-UA V enabled wireless networks,”IEEE Trans. Wireless
Commun., vol. 17, no. 3, pp. 2109–2121, Mar. 2018.
[32] Y . Zeng, J. Xu, and R. Zhang, “Energy minimization for wireless
communication with rotary-wing UA V ,”IEEE Trans. Wireless Commun.,
vol. 18, no. 4, pp. 2329–2345, Apr. 2019.
[33] Q. Wu, J. Xu, and R. Zhang, “Capacity characterization of UA V-enabled
two-user broadcast channel,” IEEE J. Sel. Areas Commun. , vol. 36,
no. 9, pp. 1955–1971, Sep. 2018.
[34] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li, “Throughput
maximization for UA V-enabled integrated periodic sensing and
communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 1,
pp. 671–687, Jan. 2023.
[35] Q. Wu, L. Liu, and R. Zhang, “Fundamental trade-offs in communication
and trajectory design for UA V-enabled wireless network,”IEEE Wireless
Commun., vol. 26, no. 1, pp. 36–44, Feb. 2019.
[36] E. S. Kang, H. Hwang, and D. S. Han, “A ﬁne carrier recovery
algorithm robustto Doppler shift for OFDM systems,” IEEE Trans.
Consum. Electron., vol. 56, no. 3, pp. 1218–1222, Aug. 2010.
[37] M. Xing, X. Jiang, R. Wu, F. Zhou, and Z. Bao, “Motion compensation
for UA V SAR based on raw radar data,” IEEE Trans. Geosci. Remote
Sens., vol. 47, no. 8, pp. 2870–2883, Aug. 2009.
[38] L. Liu, S. Zhang, and R. Zhang, “Multi-beam UA V communication
in cellular uplink: Cooperative interference cancellation and sum-rate
maximization,” IEEE Trans. Wireless Commun. , vol. 18, no. 10,
pp. 4679–4691, Oct. 2019.
[39] W. Miao, C. Luo, G. Min, Y . Mi, and Z. Yu, “Location-based robust
beamforming design for cellular-enabled UA V communications,” IEEE
Internet Things J. , vol. 8, no. 12, pp. 9934–9944, Jun. 2021.
[40] Y . Kawamoto et al., “HAPS-based interference suppression through
null broadening with directivity control in space-air-ground
integrated networks,” IEEE Trans. V eh. Technol. , vol. 72, no. 12,
pp. 16098–16107, Dec. 2023.
[41] Y . Kawamoto et al., “Interference suppression in HAPS-based space-air-
ground integrated networks using a codebook-based approach,” IEEE
Trans. V eh. Technol., vol. 73, no. 12, pp. 19252–19262, Dec. 2024.
[42] P. Stoica, J. Li, and Y . Xie, “On probing signal design for MIMO radar,”
IEEE Trans. Signal Process. , vol. 55, no. 8, pp. 4151–4161, Aug. 2007.
[43] O. Moﬁd and S. Mobayen, “Adaptive sliding mode control for ﬁnite-
time stability of quad-rotor UA Vs with parametric uncertainties,” ISA
Trans., vol. 72, pp. 1–14, Jan. 2018.
[44] R. Mahony, V . Kumar, and P. Corke, “Multirotor aerial vehicles:
Modeling, estimation, and control of quadrotor,” IEEE Robot. Autom.
Mag., vol. 19, no. 3, pp. 20–32, Sep. 2012.
[45] B. Li, Q. Li, Y . Zeng, Y . Rong, and R. Zhang, “3D trajectory
optimization for energy-efﬁcient UA V communication: A control
design perspective,” IEEE Trans. Wireless Commun. , vol. 21, no. 6,
pp. 4579–4593, Jun. 2022.
[46] M. Labbadi and M. Cherkaoui, “Robust adaptive nonsingular fast
terminal sliding-mode tracking control for an uncertain quadrotor UA V
subjected to disturbances,” ISA Trans., vol. 99, pp. 290–304, Apr. 2020.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply. 

3484 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[47] M. Razaviyayn, M. Hong, and Z.-Q. Luo, “A uniﬁed convergence
analysis of block successive minimization methods for nonsmooth
optimization,” SIAM J. Optim., vol. 23, no. 2, pp. 1126–1153, Jan. 2013.
[48] K. Teo, B. Li, C. Yu, and V . Rehbock, Applied and Computational
Optimal Control: A Control Parametrization Approach . Cham,
Switzerland: Springer, 2021.
[49] O. Moﬁd, S. Mobayen, C. Zhang, and B. Esakki, “Desired tracking of
delayed quadrotor UA V under model uncertainty and wind disturbance
using adaptive super-twisting terminal sliding mode control,” ISA
Trans., vol. 123, no. 7, pp. 455–471, Apr. 2022.
[50] C. Liu, Z. Gong, K. L. Teo, J. Sun, and L. Caccetta, “Robust multi-
objective optimal switching control arising in 1,3-propanediol microbial
fed-batch process,” Nonlinear Anal., Hybrid Syst. , vol. 25, pp. 1–20,
Aug. 2017.
[51] M. S. Lobo, L. Vandenberghe, S. Boyd, and H. Lebret, “Applications
of second-order cone programming,” Linear Algebra Appl. , vol. 284,
no. 1, pp. 193–228, Nov. 1998.
[52] Q. Li, B. Li, Z.-Q. He, Y . Rong, and Z. Han, “Joint design of
communication sensing and control with a UA V platform,” IEEE Trans.
Wireless Commun., vol. 23, no. 12, pp. 19231–19244, Dec. 2024.
[53] Data of the UA V . Accessed: 2021. [Online]. Available: https://
ﬂyeval.com/
[54] W. Rudin, Principles of Mathematical Analysis , 3rd ed., New York,
NY , USA: McGraw-Hill, 1976.
Bin Li (Senior Member, IEEE) received the
bachelor’s degree in automation and the master’s
degree in control science and engineering from
Harbin Institute of Technology, China, in 2005
and 2008, respectively, and the Ph.D. degree in
mathematics and statistics from Curtin University,
Australia, in 2011. From 2012 to 2014, he was a
Research Associate with the School of Electrical,
Electronic and Computer Engineering, University of
Western Australia, Australia. From 2014 to 2017,
he was a Research Fellow with the Department of
Mathematics and Statistics, Curtin University. Currently, he is a Professor with
the School of Aeronautics and Astronautics, Sichuan University, China. His
research interests include stochastic model predictive control, optimal control,
optimization, signal processing, and wireless communications.
Hongyun Zhang received the Master of Science
degree in operations research and cybernetics from
Dalian University of Technology, China, in 2022.
She is currently pursuing the Ph.D. degree in
information and communication engineering with
Sichuan University, China. Her research interests
include sensing, communication and control co-
design, and trajectory optimization.
Yue Rong (Senior Member, IEEE) received the
Ph.D. degree (summa cum laude) in electrical engi-
neering from Darmstadt University of Technology,
Darmstadt, Germany, in 2005.
He was a Post-Doctoral Researcher with the
Department of Electrical Engineering, University of
California at Riverside, Riverside, CA, USA, from
February 2006 to November 2007. Since December
2007, he has been with Curtin University, Bentley,
W A, Australia, where he is currently a Professor.
His research interests include signal processing for
communications, underwater acoustic communications, underwater optical
wireless communications, machine learning, speech recognition, and biomed-
ical engineering. He has published over 200 journal and conference papers in
these areas.
Prof. Rong was a Senior Area Editor of IEEE T RANSACTIONS ON SIGNAL
PROCESSING from 2020 to 2024. He was an Editor of IEEE W IRELESS
COMMUNICATIONS LETTERS from 2012 to 2014 and a Guest Editor of
IEEE J OURNAL ON SELECTED AREAS IN COMMUNICATIONS Special Issue
on Theories and Methods for Advanced Wireless Relays. He was an Associate
Editor of IEEE T RANSACTIONS ON SIGNAL PROCESSING from 2014 to
2018.
Zhu Han (Fellow, IEEE) received the B.S. degree
in electronic engineering from Tsinghua University
in 1997 and the M.S. and Ph.D. degrees in electrical
and computer engineering from the University of
Maryland, College Park, MD, USA, in 1999 and
2003, respectively.
From 2000 to 2002, he was a Research and Devel-
opment Engineer with JDSU, Germantown, MD.
From 2003 to 2006, he was a Research Associate at
the University of Maryland. From 2006 to 2008, he
was an Assistant Professor at Boise State University,
ID, USA. Currently, he is a John and Rebecca Moores Professor with the
Electrical and Computer Engineering Department as well as the Computer
Science Department, University of Houston, TX, USA. His main research
targets on the novel game-theory related concepts critical to enabling efﬁcient
and distributive use of wireless networks with limited resources. His other
research interests include wireless resource allocation and management, wire-
less communications and networking, quantum computing, data science, smart
grid, carbon neutralization, and security and privacy. He has been an AAAS
Fellow since 2019 and an ACM Fellow since 2024. He has been a 1% Highly
Cited Researcher according to Web of Science since 2017. He is the winner of
the 2021 IEEE Kiyo Tomiyasu Award (an IEEE Field Award), for outstanding
early to mid-career contributions to technologies holding the promise of
innovative applications, with the following citation: “for contributions to game
theory and distributed management of autonomous communication networks.”
He received the NSF Career Award in 2010, the Fred W. Ellersick Prize of
the IEEE Communication Society in 2011, the EURASIP Best Paper Award
for EURASIP Journal on Advances in Signal Processing in 2015, the IEEE
Leonard G. Abraham Prize in the ﬁeld of communications systems (Best Paper
Award in IEEE J OURNAL ON SELECTED AREAS IN COMMUNICATIONS ) in
2016, the IEEE Vehicular Technology Society 2022 Best Land Transportation
Paper Award, and several best paper awards in IEEE conferences. He was
an IEEE Communications Society Distinguished Lecturer from 2015 to 2018
and an ACM Distinguished Speaker from 2022 to 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:23:28 UTC from IEEE Xplore.  Restrictions apply.