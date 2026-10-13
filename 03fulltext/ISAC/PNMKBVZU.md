---
title: "Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinching-Antenna Systems With Motion Power Consumption"
zotero_key: "PNMKBVZU"
pdf_key: "PRRHI94A"
doi: "10.1109/TWC.2025.3633833"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Joint Radiation Power, Antenna Position, and Beamforming Optimization for Pinching-Antenna Systems With Motion Power Consumption — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 7825
Joint Radiation Power, Antenna Position, and
Beamforming Optimization for Pinching-Antenna
Systems With Motion Power Consumption
Yiming Xu
 , Graduate Student Member, IEEE , Dongfang Xu
 , Member, IEEE,
Xianghao Yu
 , Senior Member, IEEE, Shenghui Song
 , Senior Member, IEEE, Zhiguo Ding
 , Fellow, IEEE,
and Robert Schober
 , Fellow, IEEE
Abstract—Pinching-antenna systems (PASS) have been recently
proposed to improve the performance of wireless networks by
reconﬁguring both the large-scale and small-scale channel condi-
tions. However, existing studies ignore the physical constraints of
antenna placement and assume ﬁxed antenna radiation power.
To overcome this limitation, this paper investigates the design
of PASS, taking into account the motion power consumption of
pinching antennas (PAs) and the impact of adjustable antenna
radiation power. To that end, we minimize the average power
consumption for a given quality-of-service (QoS) requirement by
jointly optimizing the antenna positions, antenna radiation power
ratios, and transmit beamforming. To the best of the authors’
knowledge, this is the ﬁrst work to consider radiation power
optimization in PASS, which provides an additional degree of
freedom (DoF) for system design. The cases with both continuous
and discrete antenna placement are considered, where the main
challenge lies in the fact that the antenna positions affect both the
magnitude and phase of the channel coefﬁcients of PASS, making
system optimization very challenging. To tackle the resulting
unique obstacles, an alternating direction method of multipliers
(ADMM)-based framework is proposed to solve the problem
Received 1 July 2025; revised 19 October 2025; accepted 9 November 2025.
Date of publication 25 November 2025; date of current version 22 December
2025. This work was supported in part by the General Research Fund
from Hong Kong Research Grants Council under Project 16209524. The
work of Robert Schober was supported in part by the Federal Ministry for
Research, Technology and Space (BMFTR) in Germany in the Program of
“Souver¨an. Digital. Vernetzt.” Joint Project xG-RIC under Project 16KIS2432;
and in part by the Deutsche Forschungsgemeinschaft (DFG, German Research
Foundation) under Project SFB 1483 (Project-ID 442419336, EmpkinS). The
associate editor coordinating the review of this article and approving it for
publication was D. Niyato. (Corresponding author: Dongfang Xu.)
Yiming Xu is with the Department of Electronic and Computer Engineering,
The Hong Kong University of Science and Technology, Hong Kong, China
(e-mail: yxuds@connect.ust.hk).
Dongfang Xu is with the Division of Integrative Systems and Design, The
Hong Kong University of Science and Technology, Hong Kong, China (e-mail:
eedxu@ust.hk).
Xianghao Yu is with the Department of Electrical Engineering, City
University of Hong Kong, Hong Kong, China (e-mail: alex.yu@cityu.edu.hk).
Shenghui Song is with the Department of Electronic and Computer Engi-
neering and the Division of Integrative Systems and Design, The Hong
Kong University of Science and Technology, Hong Kong, China (e-mail:
eeshsong@ust.hk).
Zhiguo Ding is with the Department of Computer and Informa-
tion Engineering, Khalifa University, Abu Dhabi, United Arab Emirates,
and also with the Department of Electrical and Electronic Engineer-
ing, The University of Manchester, M13 9PL Manchester, U.K. (e-mail:
zhiguo.ding@manchester.ac.uk).
Robert Schober is with the Institute for Digital Communications, Friedrich-
Alexander-Universit¨at Erlangen-N¨urnberg, 91054 Erlangen, Germany (e-mail:
robert.schober@fau.de).
Digital Object Identiﬁer 10.1109/TWC.2025.3633833
for continuous antenna movement, while its discrete counter-
part is formulated as a mixed integer nonlinear programming
(MINLP) problem and solved by the block coordinate descent
(BCD) method. Simulation results validate the performance
enhancement achieved by incorporating PA movement power
consumption and adjustable radiation power into the PASS
design, while also demonstrating the efﬁciency of the proposed
optimization framework. The beneﬁts of PASS over conventional
multiple-input multiple-output (MIMO) systems in mitigating the
large-scale path loss and inter-user interference are also revealed.
Index Terms —Beamforming, antenna placement and acti-
vation, motion power consumption, antenna radiation power,
pinching-antenna system (PASS), alternating direction method
of multipliers (ADMM).
I. I NTRODUCTION
O
VER the past few decades, multiple-input multiple-
output (MIMO) has evolved as an effective technique for
enhancing the throughput, spectral efﬁciency, and reliability of
wireless communication systems [1]. However, in traditional
MIMO systems, the antennas are deployed in ﬁxed locations,
limiting the channel capacity. To break through this limitation,
ﬂexible-antenna techniques, such as reconﬁgurable intelligent
surfaces (RISs) [2], movable antennas [3], and ﬂuid antennas
[4], have been developed. Speciﬁcally, an RIS consists of a
large number of low-cost electromagnetic reﬂecting elements
that can intelligently reconﬁgure the wireless channels. The
movable and ﬂuid antenna systems enhance the channel quality
by optimizing the antenna positions and orientations. Despite
their proven effectiveness, existing ﬂexible-antenna techniques
face practical limitations when it comes to reducing large-scale
path loss and maintaining line-of-sight (LoS) links, which are
particularly critical for future millimeter-wave (mmWave) and
Terahertz (THz) communications. For instance, although an
RIS is able to construct a virtual LoS link, RIS-aided systems
suffer from high path loss due to the double-fading effect [2].
On the other hand, movable and ﬂuid antennas typically move
within the range of a few wavelengths, and thus are unable to
mitigate LoS blockage. To this end, pinching-antenna systems
(PASS) have recently emerged as a revolutionary ﬂexible-
antenna technology promising to overcome the aforementioned
obstacles [5], [6]. PASS was initially proposed and demon-
strated by NTT DOCOMO in 2022 [7]. Speciﬁcally, PASS
employs dielectric waveguides made of PTFE (Polytetraﬂu-
oroethylene) as transmission medium, spanning from a few
meters to tens of meters, along which multiple radiation points
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7826 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
can be activated by applying small and cost-effective dielectric
particles. These dielectric particles, which can be realized,
e.g., via clothespins, are referred to as pinching antennas
(PAs), through which the signals in the waveguide are emitted
into free space. The low cost of PASS allows for large-scale
deployment.
Compared with conventional MIMO systems and other
ﬂexible-antenna technologies, PASS offer several unique
advantages: 1) Path loss mitigation : Since the PAs can be
moved over a wide range on the waveguide, PASS can activate
the PAs near the users to signiﬁcantly reduce the path loss.
2) LoS link establishment : By dynamically adjusting the
positions of PAs to bypass a blockage, PASS can construct and
robustly maintain a LoS link. 3) Scalable system deployment:
The low-cost PAs can be easily reconﬁgured by pinching or
releasing operations, making the deployment of PASS very
scalable. 4) Efﬁcient pinching beamforming : PASS facilitate
a novel beamforming paradigm, pinching beamforming, which
simultaneously adjusts both the path loss and the phases expe-
rienced by the radiated signals. Beneﬁting from the pinching
beamforming, PASS achieve efﬁcient signal enhancement and
interference mitigation, even with a limited number of PAs [8].
Inspired by the aforementioned advantages, a signiﬁcant
amount of research has been conducted regarding the per-
formance analysis and system design of PASS. In [5], the
authors analyzed the ergodic sum rate achieved by PASS,
revealing the superior gain of PAs over conventional antennas.
Furthermore, a performance upper bound on the multi-input
single-output (MISO) interference channel with two users was
derived. In [9], the authors proposed a two-stage algorithm
to optimize the antenna positions. Speciﬁcally, the antenna
positions were ﬁrst optimized to minimize the path loss and
then reﬁned to maximize the receive signal strength. The
authors of [10] formulated the antenna position optimization
problem for PASS with one waveguide as a one-sided one-to-
one matching problem based on matching theory.
Besides antenna placement, the antenna radiation power
also plays an important role in PASS. The ﬁrst physical
radiation model for PASS was proposed in [11], unveiling
the relation between radiation power and antenna deployment.
The authors of [12] proposed a physical model to conﬁgure
antenna radiation power ratios by tuning the spacing between
PAs and waveguides. A closed-form expression for the spacing
between PAs and waveguides was derived to achieve equal
radiation power for all antennas. Based on that, a global
optimal algorithm was developed for the minimization of the
transmit power of PASS with discrete PAs movement.
Despite these recent advancements, there are still many
challenges that need to be tackled to fully unleash the potential
of PASS. First, the physical constraints of antenna move-
ment were ignored by existing works when designing the
PA positions. On the one hand, the power consumption of
PA movement, controlled mechanically or electronically, has
not been considered in the literature. On the other hand, in
practice, the movement distance of PAs within a given time
is limited, but this constraint has not been fully considered in
existing works.
Another issue that has not been well investigated is antenna
radiation power control. In particular, most of the existing
works assumed equal antenna radiation power [10], [13], [14],
hindering the PASS from reaching its full potential. Although
the authors of [11] and [12] have made initial contributions
in modeling the antenna radiation power, the radiation power
optimization in PASS has not been addressed in the literature,
so far.
To bridge the above research gaps, this paper investi-
gates the design of PASS, taking the physical movement
constraints on PAs and the adjustable radiation power into
consideration. Speciﬁcally, we consider a downlink multi-user
MIMO PASS, where the antenna movement, antenna radiation
power, and transmit beamforming are jointly optimized to
minimize the average power consumption, while guaranteeing
the users’ quality-of-service (QoS) requirements. Furthermore,
cases with both continuous and discrete antenna movement are
investigated.
The challenge in solving the formulated optimization
problem for continuous antenna movement stems from two
aspects. First, the challenging spherical-wave channel model
needs to be used in PASS, instead of the simpliﬁed far-
ﬁeld beam-steering model commonly used for conventional
ﬂexible-antenna system design. For example, while the
antenna positions affect only the phase of the channel coef-
ﬁcients for movable and ﬂuid antenna systems, the antenna
positions in PASS also impact the magnitude of the channel
coefﬁcients, causing challenges for optimization. In addi-
tion, the optimization variables for transmit beamforming,
antenna radiation power, and channel coefﬁcients, which are
complicated functions of the antenna positions, are severely
coupled. To this end, an optimization framework based on the
alternating direction method of multipliers (ADMM) is devel-
oped to solve the problem for continuous antenna movement.
The problem for discrete antenna movement is treated as a
PA position selection problem, resulting in a mixed integer
nonlinear program (MINLP). The main difﬁculties in solving
the problem for discrete antenna movement are caused by the
non-convex binary constraint and variable coupling, where a
block coordinate descent (BCD)-based framework is proposed
to tackle the problem.
The main contributions of this paper can be summarized as
follows.
• We investigate PASS accounting for the physical con-
straints on PA movement and adjustable radiation power.
A novel comprehensive framework for joint antenna
movement, antenna radiation power, and transmit beam-
forming design is proposed for the minimization of the
average power consumption, including both information
transmission power and antenna movement power, while
meeting the users’ signal-to-interference-plus-noise ratio
(SINR) requirements.
• To tackle the unique challenges arising in optimizing
the PASS, an ADMM-based framework is developed to
solve the problem for continuous antenna movement.
Speciﬁcally, we adopt the variable splitting method to
decompose the complex impact of the antenna posi-
tions on the channel coefﬁcients, resulting in several
equality constraints. Then, we adopt ADMM to handle
these equality constraints and the variable coupling issue
by alternatingly minimizing the augmented Lagrangian
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7827
function. By exploiting a series of transformations,
fractional programming, and successive convex approxi-
mation (SCA), the resulting sub-problems are effectively
solved.
• To handle the discrete antenna movement case, we for-
mulate the problem as a binary selection task for each
PA among multiple discrete position choices, leading to
an MINLP problem. Then, a BCD-based algorithm is
developed to solve the problem. Speciﬁcally, the bilin-
ear transformation is exploited to decouple the binary
variables and the transmit beamforming. Further, we use
the penalty method and SCA to obtain a low-complexity
design for handling the binary constraint.
• Numerical results are presented to validate the effec-
tiveness of incorporating the physical constraints on PA
movement and the adjustable radiation power into PASS
design, and to evaluate the efﬁciency of the proposed
optimization framework. Our results demonstrate that
1) it is essential to strike a balance between the pow-
ers consumed for information transmission and antenna
movement, respectively; 2) adjusting the antenna radia-
tion power ratios further improves the performance of
PASS; 3) compared with conventional MIMO, PASS
are superior in terms of both path loss reduction and
interference management.
Notations:Vectors and matrices are denoted by boldface
lowercase and boldface capital letters, respectively. (·)T and
(·)H stand for the transpose and the conjugate transpose
operator, respectively.ℜ{·} andℑ{·} represent the real and
imaginary parts of a complex number, respectively. Vectoriza-
tion of matrix A is denoted by vec(A), and A⊗ B represents
the Kronecker product of two matrices A and B. ∠(a) denotes
the phase angle of the complex scalar a.
II. S YSTEM MODEL AND PROBLEM FORMULATION
In this paper, we consider a PA-enabled downlink MIMO
system, as shown in Fig. 1. The channel between the PAs and
users is dominated by a strong LoS link, which is dependent
on the user’s position [11]. We adopt a two-phase protocol
for conﬁguring the PASS as shown in Fig. 2 [15]. 1 In the
ﬁrst phase, the PAs move to the desired position identiﬁed
by optimization. Then, the information transmission with
optimized transmit beamforming is implemented in the second
phase. We use T1 and T2 to denote the durations of the
two phases, respectively. In an ideal case, the antennas can
be precisely moved to any location, leading to a continuous
antenna movement design. However, in practice, due to limited
precision, the motion control of electromechanical drivers is
conﬁned to discrete movement [18]. For a comprehensive
investigation of antenna movement control, we consider both
continuous and discrete antenna movement. As shown in
1In this paper, we assume the channel state information (CSI) is perfectly
known. However, mobility of users and CSI acquisition delay induced by
users’ position estimation will cause channel variation. These variances can be
captured using a channel uncertainty model [16]. Then, a robust optimization
framework can be used to ensure the QoS requirements of the users for all
possible CSI states within the channel uncertainty set [17]. In this work,
we assume that the users’ positions remain unchanged within each frame to
focus on optimizing the key parameters of a typical PASS system. Robust
optimization of PASS is an interesting topic for future work.
Fig. 1. Illustration of a PASS-enabled downlink multi-user MIMO commu-
nication system.
Fig. 2. Illustration of the proposed two-phase protocol for antenna movement
and information transmission.
Fig. 1, the PAs are preinstalled on waveguides and then moved
to the designated position. For the discrete antenna movement
case, the positions that the PAs can reach are quantized.
The BS is equipped with M waveguides, each of which
is fed by an RF chain and comprises N PAs. Without loss
of generality, the waveguides are assumed to be deployed
parallel to the x-axis at a height of h, as shown in Fig. 1. The
y-axis coordinate of them-th waveguide is denoted byym. The
m-th waveguide spans from its feed point pm,0 = [0,ym,h ]T
to [D,ym,h ]T with a length of D. The coordinate of the n-th
PA on them-th waveguide is given by pm,n = [xm,n,ym,h ]T ,
where xm,n denotes the x-axis coordinate of the n-th PA on
the m-th waveguide. We assume xm,1 <x m,2 <··· <x m,N
without loss of generality. The coordinate of the n-th PA on
them-th waveguide at the beginning of a frame is denoted by
p′m,n = [x′m,n,ym,h ]T .2 The PASS serve K ground users,
and the coordinate of the k-th ground user is denoted by
pk = [xk,yk, 0]T . For notational simplicity, we deﬁne sets
M ={1,...,M },N ={1,...,N }, and K ={1,...,K }
to collect the indices of the waveguides, PAs, and users,
respectively. Besides, we use the tuple (m,n ) to index the
n-th PA on the m-th waveguide.
A. Signal Model
Denote the vector collecting the information symbols
intended for the K users by s = [s1,...,s K]T∈ CK×1 with
E[ssH] = IK and the transmit beamformer for the k-th user
by wk = [w1,k,...,w M,k]T∈ CM×1. The feed signal at the
m-th waveguide is given by
cm =
∑
k∈K
wm,ksk. (1)
2The overhead and errors caused by estimation of the users’ positions
and imperfect antenna movement control are not modeled in this paper.
Nevertheless, such errors can impair performance, and developing concepts
for their mitigation is an important direction for future research.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7828 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
We assume lossless in-waveguide propagation because the in-
waveguide attenuation has been shown to be insigniﬁcant [10].
After the in-waveguide propagation, the signal transmitted
from the N PAs on the m-th waveguide is given by gmcm,
where gm∈ CN×1 denotes the in-waveguide channel vector
given by
gm
∆
=
[
αm,1e
−2jπ
λg ‖pm,1−pm,0‖,...,α m,Ne−2jπλg ‖pm,N−pm,0‖]T.
(2)
Here, αm,n denotes the radiation power ratio at the (m,n )-th
PA, satisfying ∑
n∈N
α2m,n≤ 1,∀m∈M , where, αm,n = 0
indicates that the (m,n )-th antenna is deactivated. Constant
λg = λcneff represents the waveguide wavelength, with λc
denoting the free-space wavelength and neff representing the
effective refractive index of the waveguide [19].
Remark 1: The existing works in PASS design assume ﬁxed
radiation powers, which limits the PASS in fully exploiting
its capabilities. In this work, we consider PASS design with
adjustable radiation power, providing a new degree of freedom
(DoF) for system optimization and allowing a more ﬂexible
power allocation.
For the ease of presentation, gm is reformulated as
gm = Gmαm, (3)
where Gm ∈ CN×N and αm ∈ RN×1 are given by,
respectively,
Gm = diag
([
e−j 2πλg‖pm,1−pm,0‖,...,e −j 2πλg‖pm,N−pm,0‖]),
(4)
αm = [αm,1,...,α m,N]T. (5)
The received signal at the k-th user is given by
yk =
∑
m∈M
hHm,kgmcm +nk, (6)
where hm,k∈ CN×1 is the free-space channel vector between
the antennas of the m-th waveguide and the k-th user, and is
given by3
hm,k =
[
βe−j 2πλc‖pm,1−pk‖
‖pm,1− pk‖ ,..., βe−j 2πλc‖pm,N−pk‖‖pm,N− pk‖ ]H.
(7)
Here, β = λc4π is a constant and nk∼CN (0,σ 2k) denotes the
additive white Gaussian noise (AWGN) at the k-th user. By
deﬁning
hk ≜
[
hH1,k,..., hHM,k]H∈ CMN×1, (8)
G ≜ diag [G1,..., GM]∈ CMN×MN, (9)
A ≜ diag [α1,..., αM]∈ RMN×M, (10)
c ≜ [c1,...,c M]T∈ CM×1, (11)
the received signal yk can be rewritten compactly as
yk = hHk GAc +nk
3For PASS operating in mmWave frequency bands, where PAs are deployed
close to the users, the channel is dominated by the LoS component. In this
paper, we assume that the non-line-of-sight (NLoS) components are negligible.
= hHk GAwksk| {z }
Desired signal
+
∑
k′∈K\{k}
hHk GAwk′sk′
| {z }
Multi-user interference
+nk. (12)
As a result, the SINR at the k-th user is given by
γk =
⏐⏐hHk GAwk⏐⏐2
∑
k′∈K\{k}
⏐⏐hHk GAwk′⏐⏐2 +σ2k. (13)
B. Pinching-Antenna Movement Model
The movement of the PAs is driven by electric motors, such
as stepper motors [18]. Denote the power consumption of the
employed motor by P and the speed of the PAs by v. Then,
the maximum movement distance of one PA during each frame
is given by vT1, resulting in the following constraint on PA
movement ‖‖pm,n− p′m,n‖‖≤vT1. (14)
As a result, the energy consumption of the (m,n )-th PA for
moving from p′m,n to pm,n is obtained as follows [20]
Em,n =P
‖‖pm,n− p′m,n‖‖
v . (15)
Remark 2: The existing literature on PASS mostly relies on
antenna activation, which leads to suboptimal performance,
since the PAs have to be preinstalled and their positions may
not be optimal. A more general approach is to ﬁrst activate
the antenna closest to the optimal position and then move it
to that position on a small scale. Such a PASS still adheres to
the constraints on maximum movement distance and motion
power consumption and is covered by the considered system
model.
C. Problem Formulation for Continuous Antenna Movement
In this paper, we aim to minimize the average power
consumption while guaranteeing the communication QoS
requirements of the users by jointly optimizing the radiation
power ratios, antenna movement, and transmit beamforming.
The resulting optimization problem for continuous antenna
movement is formulated as follows
minimize
wk,αm,X
f1
∆
= T2
T1 +T2
∑
k∈K
‖wk‖22 + 1T1 +T2 ∑m,nEm,n
subject to C1:γk≥ Γk,∀k,
C2:‖αm‖22≤ 1,∀m,
C3:xm,n−xm,n−1≥∆min,∀ 2≤n≤N, ∀m,
C4: 0≤xm,n≤D,∀n,∀m,
C5:|xm,n−x′m,n|≤ vT1,∀n,∀m. (16)
Here, we deﬁne matrix X∈ RM×N to collect the locations of
all PAs, where its (m,n )-th element is xm,n. Constraint C1
ensures that the SINR of the k-th user is larger than the pre-
deﬁned threshold Γk. Constraint C2 indicates that the radiated
power of each waveguide does not exceed the power of the
feed signal. To avoid mutual coupling among antennas, we
restrict the minimum distance between adjacent antennas to
be larger than the pre-deﬁned threshold ∆min, as speciﬁed in
constraint C3 [5]. Constraint C4 ensures that the PAs move
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7829
on the waveguide within the waveguide length. Constraint C5
guarantees that the movement distance of PAs is smaller than
the maximum possible movement distance. We note that the
optimization of the radiation power coefﬁcients, i.e., αm, has
not yet been studied for PASS design.
Remark 3: The optimization problem in (16) is highly non-
convex. In particular, the transmit beamforming vector wk,
antenna radiation power coefﬁcient αm, and antenna position
matrix X are coupled. Different from movable antenna and
ﬂuid antenna systems, where the antenna positions only affect
the phase of channel coefﬁcients [21], [22], the positions
of PAs also impact the path loss, making the optimization
problem more challenging.
III. J OINT POWER AND ANTENNA CONTROL FOR
CONTINUOUS ANTENNA MOVEMENT
In this section, an optimization framework based on ADMM
is proposed to solve the formulated problem for continuous
antenna movement.
Remark 4: ADMM is well-suited for solving optimization
problems with equality constraints and coupled variables, ren-
dering it effective in dealing with the structure of the speciﬁc
problem obtained for PASS design. Speciﬁcally, decomposing
the channel coefﬁcients, which are a complicated expression of
the antenna positions, into multiple simpler expressions using
the variable splitting method inherently introduces equality
constraints, i.e., C6 and C7 speciﬁed below. Following the
principle of augmented Lagrangian methods, ADMM can
effectively handle these equality constraints by combining the
Lagrangian term with quadratic penalty terms, as formulated in
(29) and elaborated on below [23]. In addition, ADMM parti-
tions the initial problem into simpler sub-problems by splitting
the variables and alternatingly solving these sub-problems
to update the variables, enabling ADMM to overcome the
variable coupling issue.
A. ADMM-Based Transformation
In the following, we use the variable splitting method to
transform the equivalent channel vector GH hk of user k into
a more tractable form [24]. Speciﬁcally, the ((m−1)N +n)-th
element of GH hk∈ CMN×1 is given by
[GH hk]((m−1)N +n) = βej 2πλc (rk,m,n+neffxm,n)rk,m,n , (17)
where rk,m,n denotes the distance between the (m,n )-th PA
and the k-th user, which is given by
rk,m,n =
√
(xm,n−xk)2 + (ym−yk)2 +h2. (18)
To handle the exponential term in (17), we deﬁne an auxiliary
variableθ∈ RKMN×1 and introduce the following equality
constraint
C6:θk,m,n = 2πλc (rk,m,n +neffxm,n),∀k,∀m,∀n, (19)
whereθk,m,n is the ((k−1)MN +(m−1)N +n)-th element of
θ. For ease of presentation, we deﬁne vector φ∈ RKMN×1,
whose ((k− 1)MN + (m− 1)N +n)-th element is φk,m,n
∆
=
2π
λc (rk,m,n +neffxm,n), and rewrite constraint C6 compactlyas
C6:θ =φ. (20)
Furthermore, we introduce auxiliary variables tk∈ CMN×1 to
replace the equivalent channel vector, leading to the following
equality constraint
C7: tk = GH hk,∀k∈K. (21)
The element-wise expression of constraint C7 is given by
tk,m,n = βejθk,m,n
rk,m,n
,∀k∈K,∀m∈M,∀n∈N , (22)
where tk,m,n is the ((m− 1)N +n)-th element of tk. Then,
we can rewrite (22) as follows
rk,m,ntk,m,n =βejθk,m,n,∀k∈K,∀m∈M,∀n∈N ,
(23)
A compact version of (23) is
C7: Rktk = uk,∀k∈K, (24)
where Rk∈ CMN×MN is a diagonal matrix, whose ((m−
1)N +n)-th main diagonal element is rk,m,n. uk∈ CMN×1
is a vector whose ((m− 1)N +n)-th element is βejθk,m,n.
Based on (21), constraint C1 can be reformulated equiva-
lently as follows
C1:
⏐⏐tHk Awk⏐⏐2
∑
k′∈K\{k}
⏐⏐tHk Awk′⏐⏐2 +σ2k≥ Γk,∀k∈K. (25)
Then, problem (16) is recast as
minimize
wk,αm,X,
θ,tk
f1 + IF(wk,αm, X, tk)
subject to C6:θ =φ,
C7: Rktk = uk,∀k∈K, (26)
where IF(wk,αm, X, tk) is an indicator function deﬁned as
IF(wk,αm, X, tk)
∆
=
{
0 : ( wk,αm, X, tk)∈F ,
∞ : otherwise, , (27)
whereF is the feasible set deﬁned by constraints C1, C2, C3,
C4, and C5 and is given by
F
∆
=
{
(wk,αm, X, tk)| C1, C2-C5
}
. (28)
Then, to handle the equality constraints C6 and C7 and
variable coupling, we apply the principle of ADMM to opti-
mization problem (26). In particular, a canonical form of the
augmented Lagrangian function of problem (26) is given by
L(wk,αm, X,θ, tk,µ,λk)
=ρ2
2
∑
k∈K
‖‖‖‖Rktk−uk+λkρ2‖‖‖‖22−ρ12 ‖‖‖‖µρ1‖‖‖‖22−ρ22 ∑k∈K‖‖‖‖λkρ2‖‖‖‖22
+f1 + IF(wk,αm, X, tk) +ρ12 ‖‖‖‖θ−φ + µρ1‖‖‖‖22, (29)
whereµ∈ RKMN×1 andλk∈ CMN×1 are the dual variables
with respect to equality constraints C6 and C7, respectively.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7830 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Constants ρ1, ρ2 > 0 are penalty parameters. The primal
variables can be obtained by alternatingly minimizing the
augmented Lagrangian function L(wk,αm, X,θ, tk,µ,λk)
with respect to wk, αm, X, θ, and tk. Given the updated
primal variables in the i-th iteration of ADMM, the dual
variables are updated as
µ(i) =µ(i−1) +ρ1
(
θ(i)−φ(i)
)
, (30)
λ(i)k =λ(i−1)k +ρ2
(
R(i)k t(i)k − u(i)k
)
. (31)
So far, we have established the basic framework of ADMM.
Next, we minimize L(wk,αm, X,θ, tk,µ,λk) by alternat-
ingly updating the primal variables wk,αm, X,θ, and tk.
B. Sub-Problem for Updating wk
By ﬁxing the other optimization variables, the transmit
beamforming vector wk is updated by solving
minimizewk
T2
T1 +T2
∑
k∈K
‖wk‖22 + IF(wk,αm, X, tk), (32)
which is equivalent to
minimizewk
T2
T1 +T2
∑
k∈K
‖wk‖22
subject to C1:γk≥ Γk,∀k∈K. (33)
Note that any phase rotated version of wk satisﬁes con-
straint C1 while the value of the objective function remains
unchanged. Hence, the term tHk Awk can be chosen to be
real-valued without loss of generality. As a result, the above
optimization problem can be equivalently transformed as fol-
lows
minimizewk,a a
subject to C1a:
‖‖‖‖ WH AH tkσk ‖‖‖‖≤√1 + 1Γkℜ{tHk Awk},
∀k∈K,
C1b:ℑ
{
tHk Awk} = 0,∀k∈K,
C8:‖W‖22≤ (T1 +T2)aT2 , (34)
where W
∆
= [ w1,..., wK]. It can be veriﬁed that problem
(34) is a standard second-order cone programming (SOCP)
problem, which can be efﬁciently solved by standard convex
optimization solvers such as CVX [25], [26].
C. Sub-Problem for Updating tk
By ﬁxing the other optimization variables, the auxiliary
variable tk is updated by solving
minimize
tk
ρ2
2
∑
k∈K
‖‖‖‖Rktk−uk+λkρ2‖‖‖‖22 + IF(wk,αm, X, tk),
(35)
which can be equivalently rewritten as follows
minimize
tk
ρ2
2
∑
k∈K
‖‖‖‖Rktk− uk +λkρ2‖‖‖‖22
subject to C1:γk≥ Γk,∀k∈K. (36)
Different from the problem with respect to wk in (33), a phase
rotation of tk has an impact on the objective function value.
As a result, the transformation used in (34) cannot be applied
to problem (36). Instead, we ﬁrst rewrite C1 equivalently as
C1: Γk
∑
k′∈K\{k}
⏐⏐tHk Awk′⏐⏐2−⏐⏐tHk Awk⏐⏐2 +σ2kΓk≤ 0,∀k,
(37)
where the left-hand side of the inequality is a difference
of convex (d.c.) functions with respect to tk which can
be effectively tackled by SCA. Speciﬁcally, we construct
an upper-bound on the non-convex term −
⏐⏐tHk Awk⏐⏐2 by
employing its ﬁrst-order Taylor expansion. Constraint C1 is
transformed into
C1: Γk
∑
k′∈K\{k}
⏐⏐tHk Awk′⏐⏐2−2ℜ{(t(i−1)k )H AwkwHk AH tk}
+
⏐⏐⏐⏐(t(i−1)k )H Awk⏐⏐⏐⏐2 +σ2kΓk≤ 0,∀k∈K, (38)
where t(i−1)k denotes the solution of tk obtained in the
previous iteration. As a result, problem (36) is replaced by
the following approximated optimization problem
minimize
tk
ρ2
2
∑
k∈K
‖‖‖‖Rktk− uk +λkρ2‖‖‖‖22
subject to C1, (39)
which is convex and can be solved efﬁciently.
D. Sub-Problem for Updating αm
By ﬁxing the other optimization variables, the antenna
radiation power ratios αm are updated by solving
minimizeαm IF(wk,αm, X, tk), (40)
which is equivalent to the following feasibility check problem
Find αm
subject to C1, C2. (41)
To accelerate the convergence and to provide more DoFs for
energy minimization in other sub-problems, we update αm by
maximizing the SINR among users [27], which leads to the
following problem
maximizeαm
∑
k∈K
⏐⏐tHk Awk⏐⏐2
∑
k′∈K\{k}
⏐⏐tHk Awk′⏐⏐2 +σ2k
subject to C2:‖αm‖22≤ 1,∀m∈M, (42)
where the non-convexity is caused by the fractional expression.
To deal with this issue, fractional programming is exploited.
By introducing auxiliary variable q = [q1,...,q K]T∈ RK×1,
problem (42) is then equivalently transformed into [28]
maximizeαm,q f2
∆
=
∑
k∈K
(
2 qk
⏐⏐tHk Awk⏐⏐
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7831
−q2k

 ∑
k′∈K\{k}
⏐⏐tHk Awk′⏐⏐2 +σ2k


)
subject to C2:‖αm‖22≤ 1,∀m∈M. (43)
For given αm, the optimal q is obtained from ∂f2∂qk = 0,∀k∈K, given by
qk =
⏐⏐tHk Awk⏐⏐∑
k′∈K\{k}
⏐⏐tHk Awk′⏐⏐2 +σ2k,∀k∈K. (44)
Next, we solve problem (43) for given q. To begin with,
we introduce auxiliary variable ψ ∈ RK×1 whose the k-th
element is ψk and the following constraint
C9:
⏐⏐tHk Awk⏐⏐≥ψk,∀k∈K. (45)
The resulting objective function is then expressed as
f 2
∆
=
∑
k∈K

2 qkψk−q2k

 ∑
k′∈K\{k}
⏐⏐tHk Awk′⏐⏐2 +σ2k



.
(46)
Note that constraint C9 is non-convex with respect to αm. To
handle this, we ﬁrst equivalently transform C9 into
C9: tHk AwkwHk AT tk≥ψ2k,∀k∈K. (47)
By constructing a lower bound on the term tHk AwkwHk AT tk,
constraint C9 can be rewritten as
C9: Tr
((
TkA(i−1)Wk + TTk A(i−1)WTk
)T
A
)
− Tr
(
TkA(i−1)Wk
(
A(i−1)
)T)
−ψ2k≥ 0,∀k∈K, (48)
where Tk
∆
= tktHk , Wk ∆= wkwHk . A(i−1) is the solution
obtained in the previous iteration. With q obtained from (44),
optimization problem (43) for solving αm is transformed into
maximize
αm,ψ
f 2
subject to C2, C9, (49)
which is convex and can be solved efﬁciently.
E. Sub-Problem for Updating θ
The auxiliary variable θ is updated by solving
minimize
θ
f3
∆
= ρ1
2
‖‖‖‖θ−φ+µρ1‖‖‖‖22+ρ22∑k∈K‖‖‖‖Rktk−uk+λkρ2‖‖‖‖22.
(50)
Here, the non-convexity comes from the second term, which
can be explicitly expressed as ρ22 ∑k,m,nvk,m,n(θk,m,n), where
vk,m,n(θk,m,n) is deﬁned as
vk,m,n(θk,m,n)
∆
=
⏐⏐⏐⏐rk,m,ntk,m,n−βejθk,m,n +λk,m,nρ2 ⏐⏐⏐⏐2.(51)
The variable λk,m,n is the ((m− 1)N +n)-th element of λk.
We note that the variable θk,m,n is involved in the exponential
term, which is neither convex nor concave. To handle this
challenge, we construct an upper-bound on vk,m,n(θk,m,n)
based on the following lemma [8], [29].
Lemma 1 (Descent Lemma [30]): Let f : Rn → R
be a continuously differentiable function with a Lipschitz
continuous gradient on X ∈Rn with Lipschitz constant L.
Then, for all x, y∈X , we have
f(x)≤f(y) +∇f(y)T (x− y) +L2‖x− y‖22. (52)
Proposition 1: vk,m,n(θk,m,n) has a Lipschitz continuous
gradient on R with the Lipschitz constant Lk,m,n given by
Lk,m,n = 2β
⏐⏐⏐⏐rk,m,ntk,m,n + λk,m,nρ2 ⏐⏐⏐⏐. (53)
Proof: Please refer to Appendix.
Based on Proposition 1, an upper-bound on vk,m,n(θk,m,n)
is constructed as follows
vk,m,n(θk,m,n)
≤vk,m,n
(
θ(i−1)k,m,n
)
+∇θvk,m,n
(
θ(i−1)k,m,n
)(
θk,m,n−θ(i−1)k,m,n
)
+ Lk,m,n
2
(
θk,m,n−θ(i−1)k,m,n
)2
∆
=~vk,m,n(θk,m,n), (54)
where
∇θvk,m,n
(
θ(i−1)k,m,n
)
= 2β
⏐⏐⏐⏐rk,m,ntk,m,n + λk,m,nρ2 ⏐⏐⏐⏐
× sin
(
θ(i−1)k,m,n− ∠
(
rk,m,ntk,m,n + λk,m,nρ2
))
. (55)
Here, θ(i−1)k,m,n denotes the solution of θk,m,n obtained in the
previous iteration. As a result, the second-order surrogate
function of objective function f3 in (50) is given by
f3≤
∑
k,m,n
(
ρ1
2
(
θk,m,n−φk,m,n+µk,m,nρ1
)2
+ρ2
2~vk,m,n(θk,m,n)
)
∆
= ~f3, (56)
where µk,m,n denotes the ((k− 1)MN + (m− 1)N +n)-th
element of µ. Problem (50) is transformed into
minimize
θ
~f3, (57)
which has the closed-form solution given by (58), shown at
the bottom of the next page.
F . Sub-Problem for Updating X
The antenna positions X are updated by solving
minimize
X
1
T1 +T2
∑
m,n
Em,n + IF(wk,αm, X, tk)
+ ρ1
2
‖‖‖‖θ−φ + µρ1‖‖‖‖22 + ρ22 ∑k∈K‖‖‖‖Rktk− uk +λkρ2‖‖‖‖22,
(59)
which is equivalent to
minimize
X
f4
∆
= 1T1 +T2∑m,nEm,n + ρ12 ‖‖‖‖θ−φ + µρ1‖‖‖‖22
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7832 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
+ ρ2
2
∑
k∈K
‖‖‖‖Rktk− uk +λkρ2‖‖‖‖22
subject to C3-C5. (60)
By substituting the locations of the antennas and users, the
objective function is formulated as
f4 = P(T1 +T2)v∑m,n|xm,n−x′m,n| + ρ12 ∑k,m,n
(
θk,m,n− 2πλc (rk,m,n +neffxm,n) +µk,m,nρ1
)2
+ ρ2
2
∑
k,m,n
⏐⏐⏐⏐rk,m,ntk,m,n−βejθk,m,n + λk,m,nρ2 ⏐⏐⏐⏐2.
(61)
Here, the non-convexity of the objective function comes
from the last two terms. To deal with the second term, we
introduce auxiliary variables ξk,m,n≥ 0,∀k,∀m,∀n, and the
following constraint
C10:
⏐⏐⏐⏐θk,m,n− 2πλc (rk,m,n +neffxm,n) +µk,m,nρ1 ⏐⏐⏐⏐≤ξk,m,n,
∀k,∀m,∀n, (62)
which is equivalent to
C10a:θk,m,n− 2πλc (rk,m,n +neffxm,n) +µk,m,nρ1 ≥−ξk,m,n,
∀k∈K,∀m∈M,∀n∈N , (63)
C10b:θk,m,n− 2πλc (rk,m,n +neffxm,n) +µk,m,nρ1 ≤ξk,m,n,
∀k∈K,∀m∈M,∀n∈N , (64)
where constraint C10a is convex but constraint C10b is non-
convex due to the term rk,m,n. To tackle this issue, we
construct a lower bound with respect to rk,m,n, which is given
by [31]
rk,m,n≥r(i−1)k,m,n + x(i−1)m,n −xk
r(i−1)k,m,n
(
xm,n−x(i−1)m,n
)
∆
=~rk,m,n, (65)
where r(i−1)k,m,n denotes the value of rk,m,n evaluated using
x(i−1)m,n obtained in the previous iteration. Constraint C10b is
then transformed into
C10b: 2πλc (~rk,m,n +neffxm,n) +ξk,m,n≥θk,m,n + µk,m,nρ1 ,
∀k,∀m,∀n. (66)
Next, we handle the term ρ22 ∑k∈K‖‖‖Rktk− uk + λkρ2‖‖‖22 in
objective function f4 in (60). To begin with, we deﬁne
ηk,m,n(xm,n)
∆
=
⏐⏐⏐rk,m,ntk,m,n−βejθk,m,n + λk,m,nρ2 ⏐⏐⏐2, which
can be expanded as
ηk,m,n =|tk,m,n|2r2k,m,n +
⏐⏐⏐⏐λk,m,nρ2 −βejθk,m,n⏐⏐⏐⏐2
+ 2
⏐⏐⏐⏐λk,m,nρ2 −βejθk,m,n⏐⏐⏐⏐|tk,m,n| cos (ϑk,m,n)rk,m,n,
(67)
where ϑk,m,n
∆
= ∠tk,m,n− ∠
(
λk,m,n
ρ2 −βejθk,m,n
)
. The
convexity of ηk,m,n depends on the value of cos (ϑk,m,n).
Speciﬁcally,ηk,m,n is convex if cos (ϑk,m,n)≥ 0. Otherwise,
ηk,m,n is non-convex and is in the form of a d.c. function. For
handling the non-convex case of ϑk,m,n, we linearize rk,m,n
by ~rk,m,n as in (65), leading to a convex upper bound on
ηk,m,n, denoted by ~ηk,m,n. As a result, the surrogate function
of the term
⏐⏐⏐rk,m,ntk,m,n−βejθk,m,n + λk,m,nρ2 ⏐⏐⏐2 is obtainedas
ηk,m,n =
{
ηk,m,n, cos (ϑk,m,n)≥ 0,
~ηk,m,n, otherwise. (68)
We note that the term ϑk,m,n is a constant when optimizing
X, hence the expression for ηk,m,n is known before solving
problem (60). The objective function is now formulated as
follows
f 4 = P(T1 +T2)v∑m,n|xm,n−x′m,n|+∑k,m,nρ1ξ2k,m,n +ρ2ηk,m,n2 .
(69)
Thus, optimization problem (60) is transformed into
minimize
X,ξ
f 4
subject to C3-C5, C10a, C10b, (70)
which is a convex optimization problem and can be solved
efﬁciently.
The ADMM-based algorithm for solving problem (16) for
continuous antenna movement is summarized in Algorithm 1,
where we set the scaling factor ϵ> 1 to gradually enlarge the
penalty parameters to speed up the elimination of constraint
violations and force the equality constraints to be satisﬁed.
f (i)1 denotes the value of f1 obtained in the i-th iteration. The
workﬂow of Algorithm 1 is shown in Fig. 3. The convergence
and computational complexity of Algorithm 1 are discussed
in the following.
The objective function values of problems (39), (57), (70)
serve as upper bounds on the objective function values of
problems (35), (50), (59), respectively. For any ﬁxed penalty
parameters, these upper bounds are monotonically tightened
by alternatingly solving (39), (57), and (70) for updating tk,
θ, and X, respectively. Together by alternatingly solving (34)
and (49) for updating wk andαm, the augmented Lagrangian
functionL(wk,αm, X,θ, tk,µ,λk) is non-increasing and the
θk,m,n =
2ρ1
(
φk,m,n− µk,m,nρ1
)
+ρ2Lk,m,nθ(i−1)k,m,n−ρ2∇θvk,m,n
(
θ(i−1)k,m,n
)
2ρ1 +ρ2Lk,m,n
. (58)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7833
Algorithm 1 ADMM-Based Algorithm for Solving Problem
(16) for Continuous Antenna Movement
1: Set iteration index i = 1 , scaling factor for the penalty
parameters ϵ > 1, error tolerances ς1 and ς2. Initialize
X(1) within the maximum movement distance; initialize
θ(1) and t(1) according to (20) and (21), respectively;
initialize α(1)m,n = 1√N
2: repeat
3: Update wk by solving problem (34)
4: Update tk by solving problem (39)
5: Updateαm by solving problem (49)
6: Updateθ by (58)
7: Check the sign of cos (ϑk,m,n) and determine ηk,m,n
according to (68)
8: Update X by solving problem (70)
9: Update dual variables µ andλ by (30) and (31)
10: Update penalty parameters ρ1←ϵρ1, ρ2←ϵρ2
11: Set i←i + 1
12: until ‖θ−φ‖22 + ∑
k∈K
‖Rktk− uk‖22 ≤ ς1 and
⏐⏐⏐f (i)1 −f (i−1)1 ⏐⏐⏐
f (i−1)1 ≤ς2
corresponding solution is guaranteed to converge to a station-
ary point of problem (16) [23].4 The computational complexity
of Algorithm 1 is dominated by updating variables tk, αm,
and X. Updating tk involves solving a quadratic constrained
quadratic programming(QCQP) problem (39) with complexity
given by B1 =O(M 3N 3K 3.5 +MNK 4.5) [33]. Updating
αm requires solving the QCQP (49) with complexity given
by B2 = O((K + M)0.5M 3N 3 + ((K + M)0.5MNK )).
Updating X requires solving SOCP problem (70) with com-
plexity given by B3 =O(K 0.5M 3.5N 3.5 +K 1.5M 2.5N 2.5).
As a result, the overall complexity of Algorithm 1 is given by
B1 +B2 +B3.
IV. J OINT POWER AND ANTENNA CONTROL FOR
DISCRETE ANTENNA MOVEMENT
In this section, we consider PASS with discrete antenna
movement. Different from the case with continuous antenna
movement, the possible positions of the PAs with discrete
movement are discretized, leading to the joint power and
antenna control problem becoming an MINLP. To handle
this issue, we recast the optimization problem as an antenna
position selection problem. An algorithm exploiting the BCD
method and bilinear transformation is developed to tackle the
formulated optimization problem.
A. Problem Reformulation for Discrete Antenna Movement
The discrete antenna movement problem can be seen as
an antenna position selection problem. Speciﬁcally, each PA
should be assigned one particular position to move toward.
Assume there are ~N available discrete positions within the
maximum movement distance of each PA and we deﬁne
4Algorithm 1 solves the sub-problems within the ADMM iteration using
SCA and fractional programming. ADMM with both SCA and fractional
programming is guaranteed to converge [27], [32].
the set ~N ∆= {1,..., ~N} to collect the indices of the
available antenna positions. The location of the ~n-th available
antenna position with respect to the (m,n )-th PA is denoted
by ~pm,n,~n = [ ~xm,n,~n,ym,h ]T , where ~xm,n,~n denotes the
corresponding x-axis coordinate. To accommodate the prob-
lem in the discrete antenna movement case, we ﬁrst expand
the equivalent channel between the PAs and the k-th user
hHk G∈ C1×MN as follows
hHk G = [hHk,1,..., hHk,M ], (71)
where hk,m ∈ CN×1 denotes the effective channel vector
between them-th waveguide and thek-th user. By considering
the problem as a discrete antenna position selection problem,
we express hk,m as
h
H
k,m =
[
~hHk,m,1zm,1,..., ~hHk,m,N zm,N
]
,
=~hHk,mZm, (72)
where~hk,m and Zm are deﬁned as
~hk,m∆=[~hHk,m,1,..., ~hHk,m,N]H∈ CN~N×1, (73)
Zm
∆
= diag [zm,1,..., zm,N]∈ CN~N×N, (74)
Here, ~hHk,m,n ∆= [~hk,m,n,1,..., ~hk,m,n,~N] denotes the channel
vector from all available antenna positions of the (m,n )-th PA
to the k-th user, with the elements given by
~hk,m,n,~n = βe−j 2πλc (‖~pm,n,~n−pk‖+neff‖~pm,n,~n−pm,0‖)‖~pm,n,~n− pk‖ . (75)
We deﬁne vector zm,n
∆
= [ zm,n,1,..., zm,n,~N]T ∈ R~N×1 to
indicate the antenna position selection for the (m,n )-th PA.
Speciﬁcally, zm,n,~n = 1 indicates that the (m,n )-th PA will
be moved to the available antenna position ~pm,n,~n, otherwise,
zm,n,~n = 0 . One PA occupies only one position, leading to
the following constraint
C11: 1T~N zm,n = 1,∀m∈M,∀n∈N , (76)
where 1~N∈ R~N×1 is a vector with all elements being equal to
1. By substituting (72) into (71), the effective channel vector
hHk G can be expressed as
hHk G =~hHk Z, (77)
where
~hk = [~hHk,1,..., ~hHk,M ]H∈ CMN ~N×1, (78)
Z = diag [Z1,..., ZM]∈ CMN ~N×MN. (79)
As a result, the SINR at the k-th user can be rewritten
equivalently as
~γk =
⏐⏐⏐~hHk ZAwk⏐⏐⏐2
∑
k′∈K\{k}
⏐⏐⏐~hHk ZAwk′⏐⏐⏐2 +σ2k. (80)
Then, we deﬁne ~xm,n = [~xm,n,1,..., ~xm,n,~N]T to collect
all available locations of the (m,n )-th PA along the x-axis,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7834 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
leading to xm,n = ~xTm,nzm,n. Furthermore, we deﬁne the
displacement vector of the (m,n )-th PA as
~dm,n =
[⏐⏐~xm,n,1−x′m,n⏐⏐,..., ⏐⏐⏐~xm,n,~N−x′m,n⏐⏐⏐]T, (81)
which results in |xm,n−x′m,n| =~dTm,nzm,n.
Based on the above transformations, the optimization prob-
lem for discrete antenna movement is given by
minimize
wk,αm,Z
f5
∆
= T2
T1 +T2
∑
k∈K
‖wk‖22+ P(T1 +T2)v∑m,n~dTm,nzm,n
subject to ~C1:~γk≥ Γk,∀k∈K,
C2:‖αm‖22≤ 1,∀m,
~C3:~xTmzm,n−~xTmzm,n−1≥ ∆min,
∀2≤n≤N, ∀m,
~C4: 0≤~xTmzm,n≤D,∀n,∀m,
~C5:~dTm,nzm,n≤vT1,∀n,∀m,
C11: 1T~N zm,n = 1,∀n,∀m,
C12: zm,n,~n∈{ 0, 1},∀~n,∀n,∀m. (82)
Compared to problem (16) for continuous antenna movement,
problem (71) has an additional binary constraint C12 for the
antenna position selection variable, leading to a challenging
MINLP problem.
B. Solution for Discrete Antenna Movement
In this subsection, we develop a BCD-based algorithm to
solve problem (82). The optimization variables are divided into
two blocks, and the associated sub-problems are handled by
capitalizing on bilinear transformation, penalty method, and
SCA. A corresponding analysis of convergence and complex-
ity is also provided.
Remark 5: For continuous antenna movement, the channel
coefﬁcients depend on optimization variable X in problem
(16) in a complicated manner, motivating ﬁrst the use of
the variable splitting method and then ADMM to handle
the resulting equality constraints. However, problem (71) for
discrete antenna movement is formulated as an antenna posi-
tion selection problem. The channel coefﬁcients are a linear
combination of the binary antenna position selection variables
and the known channel coefﬁcients of all possible antenna
positions. In this case, the non-convexity comes from the
binary constraint and variable coupling. The binary constraint
can be resolved by using the penalty method and SCA. Since
there are no equality constraints, BCD is adopted to overcome
the variable coupling issue, making BCD suitable for handling
the problem.
According to the principle of BCD, the variables of problem
(82) are divided into two blocks, i.e.,{wk, Z} and{αm}. The
sub-problems associated with the two blocks are solved in an
alternating manner [34].
1) Update of {wk, Z}: The sub-problem associated with
block{wk, Z} is given by
minimize
wk,Z
f5
subject to ~C1,~C3-~C5, C11, C12, (83)
which is non-convex due to constraint ~C1, the coupling
between wk and Z, and binary constraint C12. In the fol-
lowing, we ﬁrst transform ~C1 into a more tractable form.
We note that, similar to the transformation for (33), a phase
shift applied to wk does not impact constraint ~C1 nor the
objective function value of problem (83). Hence, ~C1 can be
equivalently expressed as
~C1a:
‖‖‖‖ WH AH ZH~hkσk ‖‖‖‖≤√1 + 1Γkℜ{~hHk ZAwk},∀k,
(84)
~C1b:ℑ
{
~hHk ZAwk
}
= 0,∀k. (85)
Next, we exploit the following bilinear transformation lemma
to handle the variable coupling between W and Z.
Lemma 2 (Bilinear Transformation [35]) The matrix equal-
ity B = CD, where C∈ CM×N , D∈ CN×P , holds if and
only if there exist E≽ 0, F≽ 0 such that the following two
matrix inequalities hold


E B C
BH F DH
CH D I N

≽ 0, (86)
Tr
(
E− CCH)≤ 0. (87)
Lemma 2 decouples the two coupled optimization variables
using one convex constraint (86) and one constraint (87),
which is in the form of a d.c. function. Later, we will show that
(87) is actually convex by exploiting the special structure of
binary selection variables. Speciﬁcally, we introduce auxiliary
variables Q∈ CMN ~N×K with the k-th column being qk, and
the following constraint
C13: Q = ZA W. (88)
Based on Lemma 2, constraint C13 is equivalently transformed
into the following two constraints
C13a:


P Q Z
QH S W H AH
ZH A W I MN

≽ 0, (89)
C13b: Tr(P− ZZH)≤ 0, (90)
where P ∈ CMN ~N ≽ 0 and S ∈ CK ≽ 0 are auxiliary
variables. Moreover, we have
Tr
(
ZZH) = ∑
m∈M
Tr
(
ZmZHm)
=
∑
m∈M
∑
n∈N
zHm,nzm,n
=MN, (91)
where the last equality is obtained from constraints C11
and C12. As a result, constraint C13b can be equivalently
expressed as
~C13b: Tr(P)≤MN. (92)
Accordingly, constraints ~C1a and ~C1b are rewritten as
~~C1a:
‖‖‖‖ QH~hkσk ‖‖‖‖≤√1 + 1Γkℜ{~hHk qk},∀k∈K, (93)
~~C1b:ℑ{~hHk qk} = 0,∀k∈K. (94)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7835
Optimization problem (83) is now transformed into
minimize
wk,Z,Q,P,S
f5
subject to ~~C1a, ~~C1b, ~C3-~C5,
C11, C12, C13a, ~C13b, (95)
where the remaining non-convexity originates from binary
constraint C12. To tackle this obstacle, we ﬁrst transform
constraint C12 equivalently into the following two constraints
C12a: 0≤ zm,n,~n≤ 1,∀~n,∀n,∀m, (96)
C12b:
∑
m,n,~n
(
−z2m,n,~n + zm,n,~n)≤ 0, (97)
where constraint C12b is a non-convex d.c. function. To deal
with this issue, we ﬁrst penalize it in the objective function
by applying the penalty method, resulting in the following
problem
minimize
wk,Z,Q,P,S
f 5
∆
=f5 +ζ
∑
m,n,~n
(
−z2m,n,~n + zm,n,~n)
subject to ~~C1a, ~~C1b, ~C3-~C5,
C11, C12a, C13a, ~C13b, (98)
whereζ >0 is the penalty parameter to enforce that constraint
C12b is satisﬁed after optimization. An upper-bound on f 5 is
established as follows
f 5≤f5 +ζ
∑
m,n,~n
((
1− 2
(
z(i−1)m,n,~n
))
zm,n,~n +
(
z(i−1)m,n,~n
)2)
∆
= ~f5, (99)
where the value of z(i−1)m,n,~n is obtained in the previous iteration.
Optimization problem (98) is now transformed into
minimize
wk,Z,
Q,P,S
~f5
subject to ~~C1a, ~~C1b, ~C3-~C5,
C11, C12a, C13a, ~C13b, (100)
which is a convex optimization problem and can be solved
efﬁciently.
2) Update of {αm}: The sub-problem associated with
{αm} is a feasibility checking problem which is given by
Find αm
subject to ~C1, C2. (101)
Similar to the steps for addressing problem (41), we update
αm by solving the following optimization problem
maximizeαm
∑
k∈K
⏐⏐⏐~hHk ZAwk⏐⏐⏐2
∑
k′∈K\{k}
⏐⏐⏐~hHk ZAwk′⏐⏐⏐2 +σ2k
subject to C2:‖αm‖22≤ 1,∀m∈M. (102)
Then, we recast optimization problem (102) as follows
maximize
αm,~ψ
f6
subject to C2, C14, (103)
where ~ψ∈ RK×1 is an auxiliary variable whose k-th element
is ~ψk, and objective function f6 is given by
f6
∆
=
∑
k∈K

2~qk~ψk−~q2k

 ∑
k′∈K\{k}
⏐⏐⏐~hHk ZAwk′⏐⏐⏐2 +σ2k



.
(104)
Furthermore, constraint C14 in (103) is given by
C14: Tr
((
~TkA(i−1)Wk +~TTk A(i−1)WTk
)T
A
)
− Tr
(
~TkA(i−1)Wk
(
A(i−1)
)T)
− ~ψ2k≥ 0,∀k,
(105)
where ~Tk∆= ZH~hk~hHk Z. Variable~qk is updated according to
~qk =
⏐⏐⏐~hHk ZAwk⏐⏐⏐
∑
k′∈K\{k}
⏐⏐⏐~hHk ZAwk′⏐⏐⏐2 +σ2k,∀k∈K. (106)
Algorithm 2 BCD-Based Algorithm for Solving Problem (82)
for Discrete Antenna Movement
1: Set iteration index i = 1, penalty parameter ζ >0, error
tolerance~ς. Initialize α(1)m,n = 1√N and z(1)m,n,~n = 0
2: repeat
3: Update wk, Z by solving problem (100)
4: Updateαm by solving problem (103)
5: Set i←i + 1
6: until
⏐⏐⏐~f (i)5 −~f (i−1)5 ⏐⏐⏐
~f (i−1)5 ≤~ς
The BCD-based algorithm for solving problem (82) for dis-
crete antenna movement is summarized in Algorithm 2 . The
objective function value of problem (100) is an upper-bound
on the objective function value of problem (98). This upper-
bound is gradually tightened by iteratively solving problem
(100). Recall that solving (103) does not directly inﬂuence
the objective function value of (82). Hence, by iteratively
solving problems (100) and (103), the objective function
value of problem (82) is monotonically non-increasing. Thus,
according to [36], the proposed algorithm is guaranteed to
converge to a stationary point of problem (82) within poly-
nomial time. 5 The computational complexity of Algorithm 2
is dominated by solving problem (100) whose complexity is
given byO(M 3N 3~N 3K 3.5 +MN ~NK 4.5).
Remark 6: The proposed Algorithm 2 for discrete antenna
movement can also be applied to handle the antenna acti-
vation problem, which amounts essentially to the problem
of selecting locations for antennas. The differences between
both cases include that for the antenna activation problem, the
PAs do not need to be restricted to a maximum movement
range. Additionally, the power consumption and time delay
associated with antenna movement can be omitted. Thus, the
5Algorithm 2 solves the sub-problems within the BCD iterations using SCA
and the penalty method. The BCD method with both SCA and penalty method
is guaranteed to converge [17], [37].
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7836 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
proposed methods can be straightforwardly applied to solve
the antenna activation problem.
Some discussions of the number of iterations, sensitivity to
initialization, and potential oscillations due to penalty scaling
of Algorithm 1 and Algorithm 2 are in order:
• Number of iterations : The required iteration count is
primarily governed by three key factors. First, the penalty
scaling strategy plays a signiﬁcant role for convergence:
Rapidly increasing the penalty factor can destabilize the
process, requiring additional iterations for adjustment,
while a slower increase delays constraint satisfaction
and prolongs convergence. Second, the SCA approxima-
tion accuracy critically affects performance: Performing
fewer SCA iterations results in less accurate sub-problem
solutions, necessitating more outer iterations, whereas
solving sub-problems to full convergence reduces the
required number of outer iterations but incurs higher
computational costs per iteration. Third, the stopping tol-
erances are crucial for balancing efﬁciency and accuracy:
Tighter tolerances improve solution quality and reduce
the required number of outer iterations but increase
the computational cost per iteration. Conversely, looser
tolerances can lead to suboptimal solutions, oscillatory
behavior, and a higher overall iteration count.
• Sensitivity to initialization : In the SCA method, the
starting point determines the convergence path, and poor
initialization can lead to suboptimal solutions. This is
addressed by sequentially solving the sub-problems and
initializing variables based on prior solutions. The initial
penalty factor also plays a critical role. An exceedingly
small initial penalty factor underweights constraint satis-
faction, while an extremely large one makes subproblems
ill-conditioned and forces premature convergence.
• Potential oscillations in penalty-scaling phases : As the
penalty factor increases, the structure of the objective
function changes. A sudden increase of the penalty factor
forces variables to adjust abruptly to stricter constraint
satisfaction, often leading to oscillations. The inner SCA
iterations further inﬂuence these oscillations. An SCA
approximation valid for the previous penalty factor can
become invalid after a large penalty factor update, requir-
ing multiple SCA iterations to recalibrate. During this
recalibration, the primal and dual variables in the outer
iterations may experience oscillatory behavior. To mit-
igate such oscillations, the penalty factor is increased
gradually instead of abruptly. One can also use an adap-
tive increase based on the rate of change of the constraint
violation [38].
• Selection of ζ to balance the trade-off between con-
vergence speed and solution quality : For small ζ, the
objective function is relatively smooth, leading to a larger
step size and quicker convergence, but the solution may
not satisfy the penalized constraint. For large ζ, the
objective function becomes steeper, and each iteration
progresses more slowly due to the resulting smaller step
size. The algorithm places a strong emphasis on satisfying
the constraints. This ensures that the ﬁnal solution sat-
isﬁes the constraints rigorously. However, the algorithm
may over-emphasize feasibility at the expense of the
TABLE I
SYSTEM SIMULATION PARAMETERS
original objective function’s optimality. In this paper,ζ is
selected experimentally to balance the trade-off between
convergence speed and solution quality.
V. S IMULATION RESULTS
In this subsection, we validate the effectiveness of the pro-
posed design of PASS via numerical simulations. We consider
a square-shaped service area with side length of D = 40
m. In particular, the PASS consists of M = 3 waveguides
deployed at a height of h = 5 m, where each waveguide
comprisesN = 4 PAs, andK = 3 users are served. They-axis
coordinates of the three waveguides are {−15 m, 0 m, 15 m}.
The pinching antennas are preinstalled with the x-coordinate
given by {8 m, 16 m, 24 m, 32 m} for each waveguide. The
default number of discrete antenna positions available on each
waveguide is 800. Unless otherwise speciﬁed, we adopt the
parameters provided in Table I.
For the purpose of performance comparison, we consider
the following three baseline schemes.
• Baseline scheme 1: This baseline scheme corresponds
to the traditional MIMO design with the same number of
RF chains as the considered PASS. Speciﬁcally, a MIMO
BS equipped with M = 3 antennas is deployed at the
origin.6 The transmit power is minimized by optimizing
the transmit beamforming while guaranteeing the SINR
requirement of the users. The corresponding optimization
problem can be equivalently transformed into a convex
optimization problem and can be solved efﬁciently and
optimally. The details are omitted here due to space
limitations.
• Baseline scheme 2: This baseline scheme follows the
existing PASS design without antenna radiation power
control. In particular, the power is equally distributed
among all the PAs of each waveguide, i.e., αm,n =
√
1
N .
The resulting optimization problem can be solved by
employing the proposed ADMM framework.
• Baseline scheme 3: This baseline scheme exploits the
existing PASS design that focuses on minimizing the
information transmit power, i.e., T2T1+T2 ∑k∈K‖wk‖22. The
6Although there are a total of MN PAs for PASS, the required number of
RF chains is M, i.e., one RF chain per waveguide [11]. The cost of adding
one PA is relatively low compared to adding one antenna in a traditional
MIMO BS, where a corresponding RF chain, baseband processing unit, and
antenna feed lines are required.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7837
Fig. 3. Workﬂow of Algorithm 1.
Fig. 4. Workﬂow of Algorithm 2.
Fig. 5. Convergence behavior of the proposed algorithms for continuous and
discrete antenna movement.
actual system performance is evaluated by the average
power consumption, including the power consumption
associated with antenna movement.
• Baseline scheme 4: This baseline scheme adopts ﬁxed
PA positions in the PASS, which is the same as the initial
positions of the PAs of the proposed schemes.
For simplicity, in the following description, we refer to
the proposed algorithms for continuous and discrete antenna
movement as “continuous design” and “discrete design”,
respectively.
A. Algorithm Convergence
Fig. 5 presents the convergence behavior of the proposed
algorithms. As can be observed, the average power consump-
tion of Algorithm 1 for continuous antenna movement ﬁrst
decreases and then slightly increases, and ﬁnally decreases
until convergence. This phenomenon is caused by the change
of the penalty parameters. For the ﬁrst several iterations,
the penalty parameters are small, allowing large constraint
violations and broadening the feasible set. Hence, the objective
Fig. 6. Average power consumption (dBm) versus SINR requirement Γk.
function value dramatically decreases, however, the solutions
obtained during these initial iterations may not be feasible.
As the penalty parameters increase, the constraint violations
reduce gradually and the equality constraints are enforced,
leading to a smaller feasible region and a larger objective
function value. Once the equality constraints are satisﬁed,
the objective function value decreases until convergence. As
for Algorithm 2 for discrete antenna movement, the objective
function value monotonically decreases until convergence.
Furthermore, it can be observed that the algorithms require
a few more iterations to converge as the number of antennas
and users, i.e., M and K, increases.
B. Impact of SINR Requirement
We investigate the impact of the SINR requirements in
Fig. 6. It can be observed from the ﬁgure that the aver-
age transmit power increases with the SINR requirement.
Compared with baseline scheme 1, the proposed designs
achieve signiﬁcant performance improvement, which comes
from the signiﬁcantly reduced path loss in PASS. Compared
with baseline scheme 2, the proposed design consumes less
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7838 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Average power consumption (dBm) versus antenna motion power P
(W).
power because of the antenna radiation power optimization.
This is because the ﬂexible antenna radiation power facilitates
more efﬁcient energy utilization. In other words, the optimized
antenna radiation power provides extra DoFs for system design
and enlarges the feasible region of the optimization problem,
leading to better system performance. The performance gap
between the proposed scheme and baseline scheme 3 reveals
that minimizing the information transmission power consump-
tion alone cannot minimize the total power consumption in
practice, thus verifying the necessity of also considering the
power consumed for antenna movement. The performance gap
between the proposed scheme and baseline scheme 4 demon-
strates that PASS signiﬁcantly beneﬁts from the additional DoF
provided by conﬁgurable antenna positions. Baseline scheme 4
performs worse than baseline schemes 2 and baseline scheme
3, indicating that antenna movement has a greater impact on
PASS performance than adjustable power radiation and the
consideration of antenna movement power consumption. In
addition, the superiority of baseline scheme 4 over baseline
scheme 1 arises from the reduced large-scale path loss caused
by the antenna being positioned closer to the user.
C. Impact of Antenna Motion Power
We study the impact of antenna motion power in Fig. 7.
As can be observed, the average power consumption of PASS
increases with the motion power consumption. The continuous
design yields the lowest power consumption among all con-
sidered schemes. As the antenna motion power increases from
0.04 W to 0.14 W, the continuous design also causes a smaller
power consumption increment (56.6%), compared to baseline
scheme 3 (89.1%). This is because, by taking the inﬂuence of
the antenna motion power into account, the proposed scheme
can strike a balance between the antenna motion power and
information transmission power, thus reducing the average
power consumption.
D. Impact of Density of Available Discrete Antenna Positions
Fig. 8 illustrates the impact of the density of the available
discrete antenna positions. We can observe that the average
power consumption decreases with the number of available
Fig. 8. Average power consumption (dBm) versus antenna spacing of discrete
antenna positions.
Fig. 9. Average power consumption (dBm) versus antenna movement speed
v (m/s).
discrete antenna positions on each waveguide. This is because
more available antenna positions support a ﬁner-grained
antenna movement control and hence improve performance.
Furthermore, it can be observed that the discrete design
approaches the continuous design when the number of avail-
able discrete antenna positions reaches 1000, which veriﬁes
the optimality of the discrete design for the case of a large
number of antennas. We note that 1000 antenna positions is a
large number and results in a high computational complexity
of the discrete design. On the other hand, although the
discrete antenna movement case allows for easier hardware
deployment, it suffers from a performance loss compared to
the continuous design for a small number of antenna positions.
As a result, the trade-off between system performance, com-
putational complexity, and simplicity of hardware deployment
of PASS with discrete antenna movement should be carefully
considered for practical design.
E. Impact of Antenna Movement Speed
The impact of the antenna movement speed is investigated
in Fig. 9. As can be seen, the average power consumption
decreases with the antenna movement speed. Here, we note
that the relationship between the power consumption and
antenna movement speed depends on the speciﬁc motion
model for driving the antennas. In this work, we adopt a
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7839
Fig. 10. Average power consumption (dBm) versus service area size.
uniform motion model to capture the antenna movement. With
the adopted motion model, a larger speed expands the location
range of the antennas, providing more feasible antenna posi-
tions for system design and enlarging the feasible region. In
addition, a larger movement speed directly reduces the value
of motion power consumption in the objective function. Fur-
thermore, it can be seen from the ﬁgure that the performance
gap between the discrete and continuous designs decreases
with increasing antenna movement speed, as a higher speed
reduces the impact of antenna motion power consumption
in the objective function. A more realistic antenna motion
model should involve acceleration at the beginning, followed
by uniform motion, and then deceleration at the end, which
leads to more challenging design problems and constitutes a
key area for future research.
F . Beneﬁt of PASS in Path Loss Mitigation
In Fig. 10, we investigate the performance advantage of
PASS compared to conventional MIMO systems for varying
service area sizes. In particular, we ﬁrst deﬁne the scale size
of the service area as D′D , where D′ is the variable length of
the square service area. As can be seen from the ﬁgure, the
average power consumption increases with the service area
size. Baseline scheme 1 consumes signiﬁcantly more power
as the service area increases, while the PASS is less sensitive
to changes in the service area size. This is due to the fact
that the PASS can alleviate the long-distance path loss via
in-waveguide propagation. In addition, the PAs move to the
preferred positions, facilitating short-range LoS communica-
tion. Fig. 10 demonstrates the signiﬁcant path loss reduction
and the efﬁcient pinching beamforming achieved by PASS.
VI. C ONCLUSION
This paper studied the design of PASS, where physical
constraints on PA movement and the adjustable antenna
radiation power were accounted for. The antenna positions,
radiation power, and transmit beamforming were jointly opti-
mized to minimize the average power consumption for both
continuous and discrete antenna movement. An ADMM-based
framework was developed to tackle the unique challenges
of PASS for continuous antenna movement by exploiting
the unique ability of ADMM to address variable coupling
and equality constraints. The problem for discrete antenna
movement was recast as an MINLP and solved by the BCD
method. Simulation results showed that PASS offer signiﬁcant
beneﬁts over conventional MIMO systems by greatly reducing
path loss and alleviating user interference via subtle pinching
beamforming. The system models proposed in this work, along
with the derived optimization framework, represent an initial
step toward fully harnessing the potential of PASS.
The proposed algorithm can be further extended to handle
a hybrid antenna movement pattern, where the antenna is
ﬁrst activated near the designated position and then moved
to that position. This hybrid antenna movement combines the
ﬂexibility of continuous movement with the energy efﬁciency
of discrete movement, which constitutes a key area for future
research.
APPENDIX A
PROOF OF PROPOSITION 1
For simplicity, we omit subscriptsk,m, andn in the deriva-
tion. We note that∇θv(θ) is continuous and differentiable on
R. Then, according to the mean value theorem, for all θ1,
θ2∈ R, we have
|∇θv(θ1)−∇θv(θ2)|≤
⏐⏐⏐⏐ maxθ∈[θ1,θ2]∇2θv(θ)⏐⏐⏐⏐|θ1−θ2|, (107)
where the second-order gradient ∇2θv(θ) is given by
∇2θv(θ) = 2β
⏐⏐⏐⏐rt + λρ2⏐⏐⏐⏐ cos(θ− ∠(rt + λρ2)), (108)
which is upper bounded by 2β
⏐⏐⏐rt + λρ2⏐⏐⏐. Hence, ∇θv(θ) is
Lipschitz continuous with the Lipschitz constant given by L =
2β
⏐⏐⏐rt + λρ2⏐⏐⏐.
REFERENCES
[1] L. Lu, G. Y . Li, A. L. Swindlehurst, A. Ashikhmin, and R. Zhang, “An
overview of massive MIMO: Beneﬁts and challenges,” IEEE J. Sel.
Topics Signal Process., vol. 8, no. 5, pp. 742–758, Oct. 2014.
[2] X. Yu, V . Jamali, D. Xu, D. W. K. Ng, and R. Schober, “Smart and
reconﬁgurable wireless communications: From IRS modeling to algo-
rithm design,” IEEE Wireless Commun. , vol. 28, no. 6, pp. 118–125,
Dec. 2021.
[3] L. Zhu et al., “A tutorial on movable antennas for wireless networks,”
IEEE Commun. Surveys Tuts., early access, Feb. 27, 2025, doi: 10.1109/
COMST.2025.3546373.
[4] K.-K. Wong, A. Shojaeifard, K.-F. Tong, and Y . Zhang, “Fluid
antenna systems,” IEEE Trans. Wireless Commun. , vol. 20, no. 3,
pp. 1950–1962, Mar. 2021.
[5] Z. Ding, R. Schober, and H. Vincent Poor, “Flexible-antenna systems: A
pinching-antenna perspective,” IEEE Trans. Commun. , vol. 73, no. 10,
pp. 9236–9253, Oct. 2025.
[6] Y . Liu, Z. Wang, X. Mu, C. Ouyang, X. Xu, and Z. Ding, “Pinching-
antenna systems (PASS): Architecture designs, opportunities, and
outlook,” 2025, arXiv:2501.18409.
[7] H. O. Y . Suzuki and K. Kawai, “Pinching antenna: Using a dielectric
waveguide as an antenna,” NTT DOCOMO Tech. J. , vol. 23, no. 3,
pp. 5–12, 2022.
[8] X. Xu, X. Mu, Y . Liu, and A. Nallanathan, “Joint transmit and pinching
beamforming for pinching antenna systems (PASS): Optimization-based
or learning-based?,” 2025, arXiv:2502.08637.
[9] Y . Xu, Z. Ding, and G. K. Karagiannidis, “Rate maximization for
downlink pinching-antenna systems,” IEEE Wireless Commun. Lett. ,
vol. 14, no. 5, pp. 1431–1435, May 2025.
[10] K. Wang, Z. Ding, and R. Schober, “Antenna activation for NOMA
assisted pinching-antenna systems,” IEEE Wireless Commun. Lett. ,
vol. 14, no. 5, pp. 1526–1530, May 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

7840 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[11] Z. Wang, C. Ouyang, X. Mu, Y . Liu, and Z. Ding, “Modeling
and beamforming optimization for pinching-antenna systems,” 2025,
arXiv:2502.05917.
[12] X. Xu, X. Mu, Z. Wang, Y . Liu, and A. Nallanathan, “Pinching-antenna
systems (PASS): Power radiation model and optimal beamforming
design,” 2025, arXiv:2505.00218.
[13] Y . Qin, Y . Fu, and H. Zhang, “Joint antenna position and transmit
power optimization for pinching antenna-assisted ISAC systems,” 2025,
arXiv:2503.12872.
[14] G. Zhu, X. Mu, L. Guo, S. Xu, Y . Liu, and N. Al-Dhahir, “Pinching-
antenna systems (PASS)-enabled secure wireless communications,”
2025, arXiv:2504.13670.
[15] X. Wei, W. Mei, X. Huang, Z. Chen, and B. Ning, “Mechanical power
modeling and energy efﬁciency maximization for movable antenna
systems,” 2025, arXiv:2505.05914.
[16] J. Wang and D. P. Palomar, “Worst-case robust MIMO transmission with
imperfect channel knowledge,” IEEE Trans. Signal Process. , vol. 57,
no. 8, pp. 3086–3100, Aug. 2009.
[17] X. Yu, D. Xu, Y . Sun, D. W. K. Ng, and R. Schober, “Robust and secure
wireless communications via intelligent reﬂecting surfaces,” IEEE J. Sel.
Areas Commun., vol. 38, no. 11, pp. 2637–2652, Nov. 2020.
[18] S. Basbug, “Design and synthesis of antenna array with movable
elements along semicircular paths,” IEEE Antennas Wireless Propag.
Lett., vol. 16, pp. 3059–3062, 2017.
[19] D. M. Pozar, Microwave Engineering , 4th ed., Hoboken, NJ, USA:
Wiley, 2012, pp. 26–30.
[20] Y . Wu, D. Xu, D. Wing Kwan Ng, W. Gerstacker, and R. Schober,
“Globally optimal movable antenna-enabled multiuser communication:
Discrete antenna positioning, power consumption, and imperfect CSI,”
IEEE Trans. Commun. , vol. 73, no. 10, pp. 9903–9923, Oct. 2025.
[21] L. Zhu, W. Ma, B. Ning, and R. Zhang, “Movable-antenna enhanced
multiuser communication via antenna position optimization,” IEEE
Trans. Wireless Commun., vol. 23, no. 7, pp. 7214–7229, Jul. 2024.
[22] W. K. New et al., “A tutorial on ﬂuid antenna system for 6G
networks: Encompassing communication theory, optimization methods
and hardware designs,” IEEE Commun. Surveys Tuts. , vol. 27, no. 4,
pp. 2325–2377, 4th Quart., 2025.
[23] S. Boyd, “Distributed optimization and statistical learning via the alter-
nating direction method of multipliers,” Found. Trends Mach. Learn. ,
vol. 3, no. 1, pp. 1–122, 2010.
[24] J. M. Bioucas-Dias and M. A. T. Figueiredo, “Multiplicative noise
removal using variable splitting and constrained optimization,” IEEE
Trans. Image Process., vol. 19, no. 7, pp. 1720–1730, Jul. 2010.
[25] S. Boyd and L. Vandenberghe, Convex Optimization. Cambridge, U.K.:
Cambridge Univ. Press, 2004.
[26] M. Grant and S. Boyd. CVX: MATLAB Software for Disciplined Convex
Programming Version 2.2. [Online]. Available: http://cvxr.com/cvx/
[27] R. Liu, M. Li, Q. Liu, and A. Lee Swindlehurst, “SNR/CRB-constrained
joint beamforming and reﬂection designs for RIS-ISAC systems,” IEEE
Trans. Wireless Commun., vol. 23, no. 7, pp. 7456–7470, Jul. 2024.
[28] K. Shen and W. Yu, “Fractional programming for communication
systems—Part I: Power control and beamforming,” IEEE Trans. Signal
Process., vol. 66, no. 10, pp. 2616–2630, Oct. 2018.
[29] Y . Sun, P. Babu, and D. P. Palomar, “Majorization-minimization algo-
rithms in signal processing, communications, and machine learning,”
IEEE Trans. Signal Process. , vol. 65, no. 3, pp. 794–816, Feb. 2017.
[30] D. P. Bertsekas, “Nonlinear programming,” J. Oper. Res. Soc. , vol. 48,
no. 3, p. 334, 1997.
[31] D. Xu, X. Yu, D. W. K. Ng, A. Schmeink, and R. Schober, “Robust
and secure resource allocation for ISAC systems: A novel optimiza-
tion framework for variable-length snapshots,” IEEE Trans. Commun. ,
vol. 70, no. 12, pp. 8196–8214, Dec. 2022.
[32] X. Xu, Y . Liu, X. Mu, Q. Chen, and Z. Ding, “Cluster-free NOMA
communications toward next generation multiple access,” IEEE Trans.
Commun., vol. 71, no. 4, pp. 2184–2200, Apr. 2023.
[33] A. Ben-Tal and A. Nemirovski, Lectures on Modern Convex Optimiza-
tion: Analysis, Algorithms, and Engineering Applications . Philadelphia,
PA, USA: SIAM, 2001.
[34] Y . Xu, D. Xu, Z. Xie, Z. Jiang, S. Song, and D. W. K. Ng, “Resolution-
aware beam scanning for joint detection and communication in ISAC
systems,” Sci. China Inf. Sci., vol. 68, no. 5, May 2025, Art. no. 150305.
[35] U. Rashid, H. D. Tuan, H. H. Kha, and H. H. Nguyen, “Joint optimiza-
tion of source precoding and relay beamforming in wireless MIMO
relay networks,” IEEE Trans. Commun. , vol. 62, no. 2, pp. 488–499,
Feb. 2014.
[36] M. Razaviyayn, M. Hong, and Z.-Q. Luo, “A uniﬁed convergence
analysis of block successive minimization methods for nonsmooth
optimization,” SIAM J. Optim., vol. 23, no. 2, pp. 1126–1153, Jan. 2013.
[37] M. Yuan, D. He, W. Yuan, H. Yin, and H. Wang, “Near-ﬁeld integrated
sensing and communication: SPEB analysis and hybrid beamforming
design,” IEEE Trans. Cognit. Commun. Netw. , early access, Aug. 26,
2025, doi: 10.1109/TCCN.2025.3602802.
[38] C. Song, S. Yoon, and V . Pavlovic, “Fast ADMM algorithm for dis-
tributed optimization with adaptive penalty,” in Proc. AAAI Conf. Artif.
Intell., vol. 30, no. 1, 2016, pp. 753–759.
[39] X. Mu, G. Zhu, and Y . Liu, “Pinching-antenna system (PASS)-enabled
multicast communications,” 2025, arXiv:2502.16624.
[40] Z. Wei, F. Liu, C. Liu, Z. Yang, D. W. K. Ng, and R. Schober, “Integrated
sensing, navigation, and communication for secure UA V networks with
a mobile eavesdropper,” IEEE Trans. Wireless Commun., vol. 23, no. 7,
pp. 7060–7078, Jul. 2024.
[41] The BLM Series Integrated (Brushless) Motor . Accessed: Sep. 2025.
[Online]. Available: https://www.nimotion.cn/product/detail/17
Yiming Xu (Graduate Student Member, IEEE)
received the B.S. degree from the University of Elec-
tronic Science and Technology of China (UESTC),
Chengdu, China, in 2021. He is currently pursuing
the Ph.D. degree with the Department of Electronic
and Computer Engineering (ECE), The Hong Kong
University of Science and Technology (HKUST).
His research interests include integrated sens-
ing and communications, pinching antenna systems,
generative AI, and mathematical optimization. He
was recognized as an Exemplary Reviewer of the
IEEE C OMMUNICATIONS LETTERS in 2024.
Dongfang Xu (Member, IEEE) received the B.Eng.
degree in communication engineering from Shan-
dong University, Jinan, China, in July 2014, and the
M.Sc. degree (Hons.) in communications and mul-
timedia engineering and the Ph.D. degree (Hons.)
in electrical engineering from Friedrich-Alexander-
Universit¨at Erlangen-N ¨urnberg (FAU), Erlangen,
Germany, in September 2017 and December 2022,
respectively.
He is currently a Research Assistant Professor
with The Hong Kong University of Science and
Technology (HKUST). He was a co-recipient of the IEEE Communications
Society Leonard G. Abraham Prize 2023, the IEEE Communications Society
Stephen O. Rice Prize 2022, and the IEEE Global Communications Con-
ference (GLOBECOM) 2019 Best Paper Award. He was also recognized as
an Exemplary Reviewer of IEEE T RANSACTIONS ON COMMUNICATIONS
in 2022, 2021, and 2020; and the IEEE C OMMUNICATIONS LETTERS in
2023. He also serves as an Editor for IEEE T RANSACTIONS ON MOBILE
COMPUTING , IEEE T RANSACTIONS ON COMMUNICATIONS , and the IEEE
COMMUNICATIONS LETTERS .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply. 

XU et al.: JOINT RADIATION POWER, ANTENNA POSITION, AND BEAMFORMING OPTIMIZATION 7841
Xianghao Yu (Senior Member, IEEE) received
the B.Eng. degree in information engineering from
Southeast University, Nanjing, China, in 2014, and
the Ph.D. degree in electronic and computer engi-
neering from The Hong Kong University of Science
and Technology (HKUST), Hong Kong, China, in
2018.
From 2018 to 2020, he was a Humboldt
Post-Doctoral Research Fellow with the Institute
for Digital Communications, Friedrich-Alexander-
Universit¨at Erlangen-N ¨urnberg (FAU), Erlangen,
Germany. He is currently an Assistant Professor with the Department of
Electrical Engineering, City University of Hong Kong (CityU), Hong Kong,
China. Before joining CityU, he was a Research Assistant Professor with the
Department of Electronic and Computer Engineering, HKUST. He has co-
authored the book Stochastic Geometry Analysis of Multi-Antenna Wireless
Networks (Springer, 2019). His research interests include intelligent reﬂecting
surface-assisted communications, integrated sensing and communications,
near-ﬁeld communications, and wireless artiﬁcial intelligence.
Dr. Yu was listed as the World’s Top 2% Scientist by Stanford University
from 2021 to 2025. He received the IEEE Global Communications Conference
(GLOBECOM) 2017 Best Paper Award, the 2018 IEEE Signal Processing
Society Young Author Best Paper Award, the IEEE GLOBECOM 2019
Best Paper Award, the 2023 IEEE Communications Society Leonard G.
Abraham Prize, and the 2024 IEEE ComSoc Asia–Paciﬁc Outstanding Young
Researcher Award. He was also recognized as an Exemplary Reviewer of
IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS in 2017 and 2018
and IEEE T RANSACTIONS ON COMMUNICATIONS in 2021 and 2022. He is
the Symposium Co-Chair of the IEEE ICC 2026 Wireless Communications
Symposium and serves as the Secretary for the IEEE Communications
Society Wireless Communications Technical Committee (WTC). He is an
Editor of IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE
TRANSACTIONS ON MOBILE COMPUTING , and IEEE C OMMUNICATIONS
LETTERS .
Shenghui Song (Senior Member, IEEE) is currently
an Associate Professor with the Division of Integra-
tive Systems and Design (ISD) and the Department
of Electronic and Computer Engineering (ECE), The
Hong Kong University of Science and Technology
(HKUST). His research interests include wireless
communications and machine learning, with current
focus on information theory, integrated sensing and
communication, distributed intelligence, semantic
communications, and machine learning for commu-
nications.
Dr. Song is an Editorial Board Member of Entropy. He was named an
Exemplary Reviewer of IEEE C OMMUNICATIONS LETTERS . He has won
several teaching awards at HKUST, including the Michael G. Gale Medal
for Distinguished Teaching in 2018, the Best Ten Lecturers in 2013, 2015,
and 2017, the School of Engineering Distinguished Teaching Award in
2012, the Teachers I Like Award in 2013, 2015, 2016, and 2017, and the
M.Sc. (Telecom) Teaching Excellent Appreciation Award for 2020–2021 and
2022–2023. He was one of the honorees of the Third Faculty Recognition
at HKUST in 2021. He served as the Tutorial Program Co-Chair for the
2022 IEEE International Mediterranean Conference on Communications and
Networking. He is also interested in the research on engineering education and
served as an Associate Editor for IEEE T RANSACTIONS ON EDUCATION .
Zhiguo Ding (Fellow, IEEE) received the B.Eng.
degree from Beijing University of Posts and
Telecommunications in 2000 and the Ph.D. degree
from Imperial College London in 2005.
He is currently a Professor of communications
at The University of Manchester, and he has been
with Khalifa University and Princeton University.
His research interests include 6G networks, multiple
access, energy harvesting networks, and statistical
signal processing. He received the EU Marie Curie
Fellowship 2012–2014, the Top IEEE TVT Editor
2017, the IEEE Heinrich Hertz Award 2018, the IEEE Jack Neubauer
Memorial Award 2018, the IEEE Best Signal Processing Letter Award 2018,
the Friedrich Wilhelm Bessel Research Award 2020, the IEEE SPCC Technical
Recognition Award 2021, and the IEEE VTS Best Magazine Paper Award
2023. He is a Web of Science Highly Cited Researcher in two categories
in 2024. He is serving as a (Senior) Area Editor for IEEE T RANSAC -
TIONS ON WIRELESS COMMUNICATIONS and IEEE O PEN JOURNAL OF
SIGNAL PROCESSING , an Editor for IEEE T RANSACTIONS ON VEHICULAR
TECHNOLOGY , and was an Area Editor for IEEE T RANSACTIONS ON
COMMUNICATIONS and IEEE O PEN JOURNAL OF THE COMMUNICATIONS
SOCIETY .
Robert Schober (Fellow, IEEE) received the
Diploma and Ph.D. degrees in electrical engineer-
ing from Friedrich-Alexander-Universit ¨at Erlangen-
N¨urnberg (FAU), Germany, in 1997 and 2000,
respectively.
From 2002 to 2011, he was a Professor and the
Canada Research Chair of The University of British
Columbia, Vancouver, BC, Canada. Since January
2012, he has been an Alexander von Humboldt
Professor and the Chair for Digital Communication
with FAU. His research interests include communi-
cation theory, wireless and molecular communications, and statistical signal
processing.
Prof. Schober is a fellow of Canadian Academy of Engineering and the
Engineering Institute of Canada and a member of European Academy of
Sciences and Arts, the Academia Europaea, German National Academy
of Science and Engineering (acatech), and German National Academy of
Science Leopoldina. He received several awards for his work, including
the 2002 Heinz Maier Leibnitz Award of German Science Foundation, the
2004 Innovations Award of the V odafone Foundation for Research in Mobile
Communications, the 2006 UBC Killam Research Prize, the 2007 Wilhelm
Friedrich Bessel Research Award of the Alexander von Humboldt Foundation,
the 2008 Charles McDowell Award for Excellence in Research from UBC,
the 2011 Alexander von Humboldt Professorship, the 2012 NSERC E.W.R.
Stacie Fellowship, the 2017 Wireless Communications Recognition Award
by the IEEE Wireless Communications Technical Committee, and the 2022
IEEE Vehicular Technology Society Stuart F. Meyer Memorial Award; and
a Honorary Doctorate from Aristotle University of Thessaloniki, Greece, in
2024. Furthermore, he received numerous best paper awards for his work,
including the 2022 ComSoc Stephen O. Rice Prize and the 2023 ComSoc
Leonard G. Abraham Prize. Since 2017, he has been listed as a Highly
Cited Researcher by the Web of Science. He served as the Editor-in-Chief
for IEEE T RANSACTIONS ON COMMUNICATIONS , the VP Publications for
the IEEE Communication Society (ComSoc), a ComSoc Member at Large,
and a ComSoc Treasurer. He also serves as a Senior Editor for P ROCEEDINGS
OF THE IEEE and the ComSoc President.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:09:36 UTC from IEEE Xplore.  Restrictions apply.