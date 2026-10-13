---
title: "UAV-Enabled Passive 6D Movable Antenna for ISAC Joint Location Orientation and Reflection Optimization"
zotero_key: "CGHQUH7E"
pdf_key: "L42CMIAD"
doi: "10.1109/lwc.2025.3610515"
collection: "UAV"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# UAV-Enabled Passive 6D Movable Antenna for ISAC Joint Location Orientation and Reflection Optimization — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
UA V -Enabled Passive 6D Movable Antenna for
ISAC: Joint Location, Orientation, and Reﬂection
Optimization
Peilan Wang, Y u Xue, Weidong Mei, Jun Fang, and Rui Zhang, Fellow, IEEE
Abstract—Improving the fundamental performance trade-off
in integrated sensing and communication (ISAC) systems has
been deemed as one of the most signiﬁcant challenges. To addr ess
it, we propose, in this letter , a novel ISAC system that lever ages
an unmanned aerial vehicle (UA V)-mounted intelligent reﬂe cting
surface (IRS) and the UA V’s maneuverability in six-dimensi onal
(6D) space, i.e., three-dimensional (3D) location and 3D ro tation,
thus referred to as passive 6D movable antenna (6DMA). We aim
to maximize the signal-to-noise ratio (SNR) for sensing a si ngle
target while ensuring a minimum SNR at a communication user
equipment (UE), by jointly optimizing the transmit beamfor ming
at the ISAC base station (BS), the 3D location and orientatio n
as well as the reﬂection coefﬁcients of the IRS. To solve this
challenging non-convex optimization problem, we propose a two-
stage approach. In the ﬁrst stage, we aim to optimize the IRS’ s
3D location, 3D orientation, and reﬂection coefﬁcients to e nhance
both the channel correlations and power gains for sensing an d
communication. Given their optimized parameters, the opti mal
transmit beamforming at the ISAC BS is derived in closed form .
Simulation results demonstrate that the proposed passive 6 DMA-
enabled ISAC system signiﬁcantly improves the sensing and
communication trade-off by simultaneously enhancing chan nel
correlations and power gains, and outperforms other baseli ne
schemes.
Index Terms—Integrated sensing and communication (ISAC),
six-dimensional movable antenna (6DMA), unmanned aerial
vehicle (UA V), intelligent reﬂecting surface (IRS)
I. I NTRODUCTION
Integrated sensing and communication (ISAC) is a key
technology for next-generation wireless networks. Howeve r,
its performance gain is often limited by the weak cou-
pling between the sensing and communication (S&C) channel
subspaces, which typically experience different propagat ion
conditions (e.g., line-of-sight (LoS) for sensing vs. mult ipath
for communication). This mismatch restricts the overall IS AC
gains [1]–[3]. To address this challenge, intelligent reﬂe cting
surface (IRS) has been proposed as a promising solution [2]–
[4]. An IRS, comprising many passive reﬂecting elements, ca n
reshape the wireless environment in a cost-effective manne r.
In particular, IRS can create LoS paths to both communicatio n
users and sensing targets [5], improving both the channel
coupling and individual channel strengths, and thus boosti ng
the overall ISAC performance [3].
This work was supported in part by the Natural Science Founda tion of
Sichuan Province under Grants 2025ZNSFSC1431.
Peilan Wang, Y u Xue, Weidong Mei, and Jun Fang are with the Na-
tional Key Laboratory of Wireless Communications, Univers ity of Elec-
tronic Science and Technology of China, Chengdu, 611731, Ch ina, (Email:
peilan wangle@uestc.edu.cn, wmei@uestc.edu.cn, JunFang@uestc .edu.cn.)
Rui Zhang is with the Department of Electrical and Computer E n-
gineering, National University of Singapore, Singapore 11 7583 (E-mail:
elezhang@nus.edu.sg).
Most existing studies employ IRSs with ﬁxed locations
and orientations to assist in ISAC systems [2]–[4]. Recentl y,
the concept of six-dimensional movable antenna (6DMA) has
emerged to enhance communication and sensing performance
by exploiting additional degrees of freedom (DoFs) from ad-
justable three-dimensional (3D) locations and orientatio ns [6]–
[9]. By jointly optimizing these parameters, 6DMA-enabled
systems can achieve higher spatial diversity and multiplex -
ing gains compared to conventional ﬁxed-position antennas .
However, existing active (e.g., phased arrays [6], [7]) and
passive (e.g., IRS [9]) 6DMA systems are generally conﬁned
to local movement regions, limiting their ability to adapt t o
large-scale channel variations. To overcome this issue, [1 0] has
proposed mounting IRS on unmanned aerial vehicles (UA Vs),
taking advantage of their high maneuverability in both 3D
positioning and orientation control (e.g., via gimbals [11 ],
[12]). Such a UA V -mounted 6DMA system offers signiﬁcantly
larger movement and rotation ranges, enabling more effecti ve
channel reshaping. Despite these advances, the applicatio n of
UA V -enabled passive 6DMAs for ISAC remains unexplored.
To ﬁll this gap, we consider a UA V -enabled passive 6DMA
for an ISAC system, where a multi-antenna dual-functional
ISAC base station (BS) simultaneously serves a communica-
tion user equipment (UE) and tracks a single target with the a id
of an aerial IRS, as shown in Fig. 1. We aim to maximize the
sensing signal-to-noise ratio (SNR) while guaranteeing a m in-
imum communication SNR at the UE, by jointly optimizing
the transmit beamforming at the BS, the 6D parameters (3D
location and 3D orientation) and the reﬂection coefﬁcients of
the IRS. The inclusion of additional 6D parameters introduc es
signiﬁcant complexity, making the problem highly non-conv ex
and intractable. To tackle this challenge, we propose a two-
stage design approach. First, we optimize the IRS’s 6D param -
eters and reﬂection coefﬁcients to maximize the correlatio n
between the S&C channels and their individual power gains,
which is independent of the transmit beamforming at the
BS. Given their optimized solutions, the optimal transmit
beamforming is derived in closed form. Simulation results
show that the proposed passive 6DMA-enabled ISAC system
signiﬁcantly improves the sensing and communication trade -
off by enhancing S&C channel correlations and power gains
at the same time.
II. S YSTEM MODEL
As shown in Fig. 1, we consider a UA V -mounted passive
6DMA-assisted ISAC system where a multi-antenna dual-
functional ISAC BS serves a single-antenna UE and tracks
a single target simultaneously. The BS is equipped with a
uniform linear array (ULA) with Nt transmit antennas and Nr
arXiv:2505.10220v2  [eess.SP]  23 Sep 2025

2
[ ]   
T
R R,x R, y p p H  p
[ ]   
T
U U,x U, y U,z p p p  p
ISAC BS 
[0 0 0] 
T
B  p
[   ] 
T
T T,x T, y T,z p p p  p
Target 
Sensing 
Channels 
Communication 
Channels 
Passive 6DMA 
Local CCS 
Global CCS ( ) Q J
( ) 
T
Q J
UE 
ULA 
UPA 
M
( ) eT
( ) aT'x
'y
Beam Direction 
'z
'x
'y'z
y x
z
Fig. 1. UA V -mounted passive 6DMA-enabled ISAC system.
receive antennas. For clarity, we establish a global Cartes ian
coordinate system (CCS) in which the bottom element of
the BS array is located at the origin, and the ULA of the
BS is aligned along the z-axis. The global coordinates of
the BS, UE, and the target are denoted by pB = [0 , 0, 0]T ,
pU = [ pU,x pU,y pU,z]T , and pT = [pT,x pT,y pT,z ]T , respec-
tively. Furthermore, a local CCS is established at the IRS,
which lies on the x′-y′ plane, and its bottom-left element
is located at the origin. The surface is equipped with a
uniform planar array (UP A) consisting of N = Nx × Ny
reﬂecting elements, where Nx and Ny denote the numbers
of elements along the x′- and y′-axes, respectively, in the
local CCS. The 3D orientation of the IRS can be described
by γ = [ γx γy γz]T , where γx, γy and γz are Euler angles
representing its degrees of rotation along the x′-, y′-, and
z′-axes, respectively. Therefore, the relationship between the
global and local CCSs can be characterized by a 3 × 3 rotation
matrix Q(γ) ∈ SO(3) ≜ {Q|det (Q) = 1 , QQT = I}.
1 Then, for any given 3D position vector p in the global
CCS, its representation in the local CCS can be expressed
as Lp = QT (γ)(p − pR), where pR = [ pR,x pR,y H]T
denotes the global coordinates of the reference element of t he
surface, and H represents its ﬁxed altitude. It follows that
LpR = [0 0 0] T . In this letter, we denote the adjustable
6D parameters of the IRS as g ≜ [pTR γT ]T ∈ R6, which
determine its 3D location and 3D orientation.
A. Channel Model
Due to the high altitude of the IRS/UA V , we assume that the
BS-IRS, BS-target, IRS-target, and IRS-UE channels consis t
solely of an LoS path under far-ﬁeld propagation conditions
[13]. We assume a block-fading channel model where all
channels remain invariant within each coherence time inter val.
Let pI,J = pJ − pI = [ pI,J,x pI,J,y pI,J,z ]T . Then, the
complex path gain between node I and node J is given by
αI,J =
√
β0d−ηI,JI,J e−j2π dI,Jλ , I, J ∈ X , I ⁄= J, (1)
where dI,J = ‖pI,J ‖2 is the distance between node I and
node J, β0 represents the path loss at a reference distance of
1 meter, ηI,J is the path loss exponent. The set of nodes is
deﬁned as X ≜ {B, U, R, T }, where B, U , R, and T denote
the BS, UE, IRS, and the target, respectively.
1The explicit expression for Q can be found in [13] (Equation (1)) and is
omitted here for brevity.
For the transmitting ULA at the BS, its steering vector
toward node I can be expressed as
aB,I =
[
1 ej 2πdλ cos ϕB,I . . . e j 2πdλ (Nt−1) cos ϕB,I
]T
, (2)
where d is the spacing between adjacent antennas, and ϕB,I =
arccos(pB,I,z /dB,I ) denotes the angle of departure (AoD)
toward node I. For the receiving ULA at the BS, its steering
vector from node J can be similarly expressed as
¯aJ,B =
[
1 ej 2πdλ cos ϕJ,B . . . e j 2πdλ (Nr−1) cos ϕJ,B
]T
, (3)
where ϕJ,B = arccos( pJ,B,z/dJ,B) denotes the angle of
arrival (AoA) from node J.
The steering vector from/to the IRS is modeled by a UP A
and is given by
˜aI,J =
[
1 . . . , ej 2πλ (Nx−1)d sin(θ(e)I,J ) cos(θ(a)I,J )]T
⊗
[
1 . . . , ej 2πλ (Ny−1)d sin(θ(e)I,J ) sin(θ(a)I,J )]T , (4)
where θ(e)I,J and θ(a)I,J denote the elevation and azimuth angles
from node I to J (either I or J is R), respectively. Deﬁne
LpI,J (g) = LpJ − LpI = [ LpI,J,x LpI,J,y LpI,J,z ]T , the
angles (θ(e)I,J , θ(a)I,J ) from node I to node J can be expressed
in terms of the 6D parameters g, i.e.,
θ(e)I,J (g) = arccos LpI,J,zdI,J , θ (a)I,J (g) = arctan LpI,J,yLpI,J,x . (5)
On this basis, we can model the involved channels in terms
of spatial locations and/or orientations.
1) Communication Channels: The overall communication
channel is the superposition of the BS-UE channel and the
BS-IRS-UE channel. Speciﬁcally, the BS-UE channel hB,U ∈
C1×Nt can be modeled as
hB,U = αB,U aTB,U , (6)
where αB,U is the complex gain given in ( 1), aB,U is the
transmit steering vector given in ( 2). The BS-IRS channel
H B,R ∈ CN ×Nt can be modeled as the outer product of
steering vectors at the BS and the IRS:
H B,R(g) = αB,R ˜aB,RaTB,R, (7)
where αB,R is the complex gain deﬁned in ( 1), ˜aB,R is
the steering vector by substituting elevation/azimuth AoA s
(θ(e)B,R(g), θ(a)B,R(g)) in ( 5) into ( 4), and aB,R is the transmit
steering vector deﬁned in ( 2). Similarly, the IRS-UE channel
is given as
hR,U (g) = αR,U ˜aTR,U ∈ C1×N . (8)
Let Φ = diag( ejθ1 ejθ2 . . . ejθN ) denote the phase shift
matrix of the IRS. Due to non-isotropic reﬂection character istic
of IRS elements, the effective aperture gain of each element
depends on the elevation incident angle θ(e)in and reﬂection
angle θ(e)ref , which is characterized by [14]
Fθ(e)in ,θ(e)ref = cos(θ(e)in ) cos(θ(e)ref ). (9)
The overall BS-UE communication channel hc ∈ C1×Nt can
be modeled as
hc(Φ, g) = hB,U +
√
Fθ(e)B,R ,θ(e)R,U hR,U (g)ΦH B,R(g). (10)
2) Sensing Channels: The ISAC BS needs to transmit
signals to sense the target and receive echoes reﬂected by it .
As a result, the sensing channel involves the transmit sensi ng
channels from the BS (transmit array) to the target and the
receive sensing channel from the target to the BS (receive

3
array). Similar to the communication scenario, the transmi t
sensing channel is the superposition of BS-target channel a nd
BS-IRS-target channel. Let hB,T ∈ C1×Nt and hR,T ∈ C1×N
denote the BS-target channel and IRS-target channel, respe c-
tively. Then, the transmit sensing channel hs,t ∈ C1×Nt can
be expressed as
hs,t(Φ, g) = hB,T +
√
Fθ(e)B,R ,θ(e)R,T hR,T (g)ΦH B,R(g), (11)
where hB,T and hR,T (g) can be obtained by following ( 6)
and ( 8), respectively, and θ(e)R,T is the elevation angle from the
IRS to the target. On the other hand, the target-BS channel
¯hT,B ∈ CNr , the target-IRS channel ¯hT,R ∈ CN , and the
IRS-BS channel ¯H R,B ∈ CNr×N can be expressed as
¯hT,B =αT,B ¯aT,B , ¯hT,R (g) = αT,R ˜aT,R , (12)
¯H R,B(g) =αR,B ¯aR,B ˜aTR,B, (13)
where the path gain αI,J is calculated using ( 1), ¯aI,J and ˜aI,J
are deﬁned in ( 3) and ( 4), respectively. The receive sensing
channel is thus given by
hs,r(Φ, g) = ¯hT,B +√Fθ(e)R,B ,θ(e)T ,R ¯H R,B(g)Φ¯hT,R (g). (14)
The overall sensing channel H s is the outer product of hs,r ∈
CNr and hs,t, i.e.,
H s(Φ, g) = hs,r(Φ, g)hs,t(Φ, g). (15)
It is seen that both the communication channel and sensing
channel can be reshaped by adjusting the phase shift matrix
Φ and the 6D parameters g of the IRS, which introduces new
DoF to enhance S&C performance. The channel state infor-
mation (CSI) of all involved links can be obtained using pilo t-
based channel estimation techniques developed for 6DMA/IR S
systems [15], [16] or via maximum-likelihood estimation
methods commonly employed in sensing applications [5], [13 ].
B. Signal Model
In the considered scenario, the UE receives signals from the
BS through the overall communication channel, while the BS
receive array captures echoes for sensing through the overa ll
sensing channel. Thus, the received signal at the UE is given
by
yc(Φ, g) =
√
Pthc(Φ, g)f s + nc, (16)
where Pt denotes the total transmit power at the BS, f ∈ CNt
represents the beamformer at the BS, s ∼ CN (0, 1) is the
transmitted signal, nc ∼ CN (0, σ2c ) denotes the received noise
with zero mean and variance σ2c . The communication SNR is
thus given by
SNRc(Φ, g, f ) = Pt|hc(Φ, g)f |2/σ2c . (17)
On the other hand, the received echo at the BS for sensing is
given by
ys(Φ, g) =
√
PtH s(Φ, g)f s + ns ∈ CNr×1, (18)
where ns ∼ CN (0, σ2s I Nr ) is the received noise at the BS
with zero mean and variance σ2s per antenna. The sensing
SNR is deﬁned as
SNRs(Φ, g, f ) = Pt‖H s(Φ, g)f ‖22/σ2s . (19)
III. P ROBLEM FORMULATION AND SIMPLIFICATION
In this letter, our objective is to maximize the sensing SNR
in ( 19) subject to the constraint on the communication SNR
in ( 17) by jointly optimizing the phase shift matrix Φ, the 6D
parameters g of the IRS, and the transmit beamformer f at
the BS. Notably, sensing SNR has been widely utilized as a
tractable and effective performance metric for sensing [1] , [3].
It should be noted that both the UE and the target must lie in
the reﬂection half-space of the IRS when adjusting its rotat ion
and location to ensure that they can receive signals reﬂecte d
by the IRS. Let C denote the movable region of the IRS. The
normal vector of the IRS is given by [13]
n = QT (γ) × Ln + pR, pR ∈ C , (20)
where Ln = [0 0 − 1]T denotes the normal vector of the IRS
in the local CCS.
The optimization problem can then be formulated as fol-
lows.
(P1) : max
Φ,g,f
SNRs(Φ, g, f ),
s.t. SNR c(Φ, g, f ) ≥ Γ0, (21)
‖f‖2 ≤ 1, (22)
|Φi,i| = 1, ∀i = 1, 2, . . . , N, (23)
pR ∈ C , γi ∈ [0, 2π), ∀i ∈ {x, y, z}, (24)
nT pX,R ≥ 0, X ∈ {B, U, T }, (25)
where Γ0 is a pre-deﬁned threshold for the communication
SNR, Φi,i is the ith diagonal element of Φ, and pX,R =
pR − pX denotes the direction vector from the IRS to node
X. The constraints in ( 25) ensure that both the UE and the
target can receive the signals reﬂected by the IRS.
However, problem (P1) is highly non-convex due to the
coupled optimization variables in the objective function a nd
the non-convex unit-modulus constraints on the phase shift s
of the IRS. To address this problem, we propose a two-stage
approach inspired by the idea that the IRS can enhance S&C
performance through channel subspace rotation and expan-
sion [3]. In the ﬁrst stage, we aim to maximize the correlatio n
and gains of the communication and sensing channels by
jointly optimizing Φ and g. This is equivalent to maximizing
the inner product between the communication and sensing
channels (or the correlation), which can be formulated as
(P2) : min
Φ,g
F (Φ, g) = −
‖‖‖H s(Φ, g)hHc (Φ, g)‖‖‖22 ,
s.t. (22), (23), (24), (25).
Given the obtained solution to (P2), denoted as Φ⋆ and
g⋆, the optimal transmit beamformer can be derived in closed
form [3] (Eq. (9a)-(9b)). In the sequel, we focus on solving
the non-convex problem (P2) to investigate the impact of the
increased DoF introduced by the 6D parameter optimization
on the S&C performance.
IV. P ROPOSED SOLUTION TO (P2)
In this section, we propose an efﬁcient alternating optimiz a-
tion (AO)-based approach to solve the non-convex problem
(P2) sub-optimally. The core idea is to iteratively optimiz e the
phase shift matrix Φ and the 6D parameters g by alternately
ﬁxing one set of variables while optimizing the other.
A. 6D Parameters Optimization
When the phase shifts matrix Φ is ﬁxed as ¯Φ, the subprob-
lem for optimizing g is given by
(P2.1) : min
g
f (g) = F ( ¯Φ, g) = −‖Hs( ¯Φ, g)hHc ( ¯Φ, g)‖22,
s.t. (24), (25).
To address this problem, we propose a particle swarm
optimization (PSO)-based method to optimize g, owing to its
low complexity and competitive performance. The basic idea

4
is to employ a group of “particles” that mimic the behavior
of birds searching for food, where each particle explores th e
solution space to ﬁnd an optimal position [17]. Each particl e
is characterized by a “position” g and a “velocity” µ ∈ R6,
where the position g corresponds to the optimization variables,
and the velocity µ determines the direction and step size of
the particle’s movement. The performance of each particle
is evaluated using a ﬁtness function, which combines the
objective function in (P2.1) with a penalty term to enforce
feasibility:
L(g) = f (g) + τ
∑
X∈{B,U,T }
max
{
0, −
(
nT pX,R)2} , (26)
where τ > 0 is a penalty parameter used to ensure that the
constraint in ( 25) is satisﬁed.
Let g(t)m and µ(t)m denote the position and velocity of the
mth particle at the tth iteration. The position update is given
by
g(t+1)m = G (g(t)m + µ(t)m ) , (27)
where G(·) is an element-wise projection operator that ensures
the updated position g(t+1)m = [(p(t)R )Tm (γ(t))Tm]T lies within
the feasible region deﬁned by ( 24). Let gm,pbest and ggbest
denote the best historical position of the mth particle and
the global best position among all particles, respectively . The
velocity of the mth particle is updated by combining inertia,
local best attraction, and global best attraction as follow s.
µ(t+1)m = ω(t)µ(t)m + c1τ1(gm,pbest − g(t)m ) + c2τ2(ggbest − g(t)m ),
ω(t) = (ωini − ωend)( Tmax − tTmax ) + ωend, (28)
where ω(t) is the inertia weight at the tth iteration, ωini and
ωend denote the initial and ﬁnal inertia weights, respectively,
Tmax is the maximum number of iterations, c1 and c2 are the
cognitive and social learning factors, and τ1, τ2 are random
variables uniformly distributed in the interval [0, 1].
The convergence of the algorithm can be veriﬁed by noting
the non-increasing trend of the ﬁtness function value deﬁne d
in ( 26) over iterations.
B. Passive Beamforming Design
Let v = [v1 . . . v N ]T = [ejθ1 . . . e jθN ]T . The subproblem
for passive beamforming (PBF) reduces to
(P2.2) : min
v
Q(v) = −‖hr‖22 × (hchHt ) × (hthHc ),
s.t. |vi| = 1, ∀i = 1, 2, . . . , N,
where we deﬁne
hc ≜hB,U + vT U c ∈ C1×Nt, hr ≜ ¯hT,B + U rv ∈ CNr ,
ht ≜hB,T + vT U t ∈ C1×Nt,
with
U c =
√
Fθ(e)B,R ,θ(e)R,U diag(hR,U )H B,R,
U r =
√
Fθ(e)R,B ,θ(e)T ,R ¯H R,B diag( ¯hT,R ),
U t =
√
Fθ(e)B,R ,θ(e)R,T diag(hR,T )H B,R.
Problem (P2.2) can be efﬁciently solved using the manifold
optimization method as presented in [3], which is guarantee d
to converge to a critical point.
After the IRS’s phase shifts and 6D parameters are opti-
mized as above, the transmit beamforming at the BS can be
obtained in closed form as detailed in [3].
V. S IMULATION RESULTS
In this section, we provide numerical results to demon-
strate the effectiveness of the proposed method in enhancin g
S&C performance. Unless otherwise speciﬁed, the numbers of
transmit and receive antennas at the BS are set to Nt = 32
and Nr = 32 , respectively. The IRS employs a UP A with
N = Nx × Ny = 4 × 4 elements.The carrier frequency is
set to fc = 3 .6 GHz. To reﬂect the different propagation
characteristics, the path loss exponents for the sensing an d
communication channels are set to 2.2 and 3, respectively.
To balance exploration and convergence speed in the PSO
algorithm, we set c1 = 1 .6, c2 = 2 , ωini = 0 .9, and
ωend = 0 .1, respectively [17]. The global coordinates of the
user and target are pU = [280 0 0] T m and pT = [0 20 0] T
m. The altitude of the IRS is ﬁxed at H = 150 m.2 The
movable region of the UA V is constrained by the product of
its maximum speed and the channel coherence time. A high-
speed UA V in a stable environment can cover a large area,
while in dynamic environments, the movable region is limite d
due to shorter channel coherence time. To evaluate the impac t
of different region sizes, we consider two scenarios, namel y,
Region 1 with {pR,x ∈ [50, 100] m, p R,y ∈ [50, 100] m} and
Region 2 with {pR,x ∈ [0, 100] m, p R,y ∈ [0, 100] m} which
includes Region 1.
The performance is evaluated in terms of the S&C SNRs,
as well as the S&C channel correlation. The S&C channel
correlation coefﬁcient is deﬁned as ρ = |hs,thHc |‖hs,t‖‖hc‖ , where 0 ≤ρ ≤ 1. We compare the proposed method against the following
baselines: (1) 6D + PBF (R1) , which jointly optimizes the 6D
parameters and PBF within Region 1; (2) 6D + PBF (R2) ,
which applies the same joint optimization within the larger
Region 2; (3) 3D Orientation + PBF , where the IRS location
is ﬁxed and only its orientation and reﬂection coefﬁcients a re
optimized; and (4) PBF Only (Traditional ﬁxed IRS) , which
ﬁxes both the location and orientation of the IRS and optimiz es
only the reﬂection coefﬁcients.
Fig. 2 shows the sensing SNR and channel correlation
coefﬁcient ρ as functions of the number of reﬂecting elements
at the IRS. We set Nx = Ny and vary Nx from 4 to 16, with
Γ0 = 10 dB. It is seen that all methods achieve improved
sensing SNR as the number of reﬂecting elements increases.
The proposed method (for both R1 and R2) consistently
outperforms the benchmarks, with the “PBF Only” method
yielding the lowest performance. Furthermore, the case usi ng
the larger deployment region (R2) outperforms its counterp art
using Region 1. The “3D Orientation + PBF” method achieves
approximately a 3 dB improvement over the “PBF Only”
method, while “6D + PBF (R1)” achieves an additional 5 dB
gain due to the extra DoF enabled by location optimization.
These results suggest that location optimization may have a
greater impact than orientation optimization in the propos ed
ISAC systems. Moreover, it is observed that the channel
correlation coefﬁcient ρ for all methods increases rapidly and
approaches 1 when the number of reﬂecting elements exceeds
140. After this point, the sensing SNR improves slowly. This
indicates that for smaller IRS sizes, both of the S&C channel
2In practice, the IRS tends to be positioned at the lowest allo wable height
(subject to LoS availability condition) to minimize path lo ss and enhance the
efﬁcacy of rotation optimization. As such, we consider a ﬁxe d UA V height in
this letter.

5
0 20 40 60 80 100 120 140 160 180 200
Number of reflecting elements
10
15
20
25
30
35
40
45
50
55SNR(dB) of Sensing
0.5
0.6
0.7
0.8
0.9
1
6D + PBF (R1),SNR
6D + PBF (R2),SNR
3D orientation + PBF,SNR
PBF Only,SNR
6D + PBF (R1),
6D + PBF (R2),
3D orientation + PBF,
PBF Only,
Fig. 2. Sensing SNR and channel correlation
coefﬁcient vs. the number of reﬂecting elements.
Fig. 3. Optimized location and orientation of the
IRS.
25 30 35 40
Communication SNR(dB)
10
11
12
13
14
15
16
17
18Sensing SNR(dB)
PBF Only,  = 0.57
3D orientation + PBF,  = 0.58
6D + PBF (R2),  = 0.70
Fig. 4. Sensing SNR vs. communication SNR.
correlation and their individual power gains can be enhance d.
As the size of the IRS is sufﬁciently large, the enhancement
of channel power gains becomes more dominant, as the
improvement in channel correlation has already saturated.
To visualize the impact of the IRS’s 6D parameters opti-
mization, Fig. 3 shows the geometric relationship among the
BS, UE, target, and optimized IRS locations and orientation s
in the global CCS. Regardless of the IRS location being ﬁxed
or movable, its optimized orientation tends to align toward
the BS-target area to maximize the received SNR for sensing.
When the IRS is movable, it is typically positioned closer to
the BS-target region to reduce the multi-hop path loss over
the BS-IRS-target-BS and BS-IRS-target-IRS-BS links. Thi s
explains why location optimization plays a more signiﬁcant
role than orientation adjustment, as observed in Fig. 2.
Fig. 4 shows the trade-off between communication and
sensing SNRs under different values of ρ. In each case, IRS
parameters are ﬁrst optimized and then ﬁxed, followed by
beamformer optimization for varying Γ0 to characterize the
S&C SNR boundary. The “3D Orientation + PBF” method is
observed to outperform “PBF Only” by a remarkable margin,
showing that even a modest increase in channel correlation
by orientation optimization can signiﬁcantly improve perf or-
mance. The “6D + PBF (R2)” scheme is observed to further
enlarge the S&C SNR region by simultaneously increasing
correlation and received signal power through large-scale IRS
positioning.
VI. C ONCLUSION
In this letter, we investigated a new UA V -mounted passive
6DMA-enabled ISAC system by exploiting new 6D DoFs
through the joint optimization of 3D location, 3D orientati on,
and reﬂection coefﬁcients of the IRS. We aimed to maximize
the sensing SNR while satisfying a minimum communication
SNR constraint at the UE. To address this highly non-convex
optimization problem, we proposed a two-stage solution tha t
decouples the optimization of the IRS’s 6D parameters and
reﬂection coefﬁcients from the transmit beamforming at the
BS. Simulation results demonstrated that the proposed 6DMA
scheme achieves signiﬁcantly better S&C SNR trade-offs
compared to baseline schemes without using 6DMAs or with
partially movable 6DMAs. Investigating passive 6DMA for
ISAC systems in dynamic scenarios with customized perfor-
mance metrics is a promising direction for future research.
REFERENCES
[1] F. Liu, L. Zheng, Y . Cui, C. Masouros, A. P . Petropulu, H. G rifﬁths, and
Y . C. Eldar, “Seventy years of radar and communications: The road from
separation to integration,” IEEE Signal Process. Mag. , vol. 40, no. 5,
pp. 106–121, Jul. 2023.
[2] R. Liu, M. Li, H. Luo, Q. Liu, and A. L. Swindlehurst, “Inte grated
sensing and communication with reconﬁgurable intelligent surfaces:
Opportunities, applications, and future directions,” IEEE Wireless Com-
munications, vol. 30, no. 1, pp. 50–57, Feb. 2023.
[3] X. Meng, F. Liu, S. Lu, S. P . Chepuri, and C. Masouros, “RIS -assisted
integrated sensing and communications: A subspace rotatio n approach,”
in Proc. IEEE Radar Conference (RadarConf23) . IEEE, 2023, pp. 1–6.
[4] X. Song, J. Xu, F. Liu, T. X. Han, and Y . C. Eldar, “Intellig ent reﬂecting
surface enabled sensing: Cramer-rao bound optimization,” IEEE Trans.
Signal Process. , vol. 71, pp. 2011–2026, 2023.
[5] X. Shao, C. Y ou, W. Ma, X. Chen, and R. Zhang, “Target sensi ng with
intelligent reﬂecting surface: Architecture and performa nce,” IEEE J.
Sel. Areas Commun. , vol. 40, no. 7, pp. 2070–2084, 2022.
[6] X. Shao, Q. Jiang, and R. Zhang, “6D movable antenna based on
user distribution: Modeling and optimization,” IEEE Trans. Wireless
Commun., vol. 24, no. 1, pp. 355–370, 2025.
[7] X. Shao, R. Zhang, and R. Schober, “Exploiting six-dimen sional mov-
able antenna for wireless sensing,” IEEE Wireless Commun. Lett. ,
vol. 14, no. 2, pp. 265–269, Feb. 2025.
[8] B. Ning, S. Y ang, Y . Wu, P . Wang, W. Mei, C. Y uen, and E. Bjor nson,
“Movable antenna-enhanced wireless communications: Gene ral archi-
tectures and implementation methods,” IEEE Wireless Commun. , Early
Access, May 2025.
[9] H. Wang, X. Shao, B. Zheng, X. Shi, and R. Zhang, “Passive s ix-
dimensional movable antenna (6DMA)-assisted multiuser co mmunica-
tion,” IEEE Wireless Commun. Lett. , vol. 14, pp. 1014–1018, 2025.
[10] C. Liu, W. Mei, P . Wang, Y . Meng, B. Ning, and Z. Chen, “UA V-enabled
passive 6D movable antennas: Joint deployment and beamform ing
optimization.” [Online]. Available: https://arxiv.org/ abs/2412.11150
[11] A. Fotouhi, H. Qiang, M. Ding, M. Hassan, L. G. Giordano, A. Garcia-
Rodriguez, and J. Y uan, “Survey on UA V cellular communicati ons:
Practical aspects, standardization advancements, regula tion, and security
challenges,” IEEE Commun. Surveys Tuts., vol. 21, no. 4, pp. 3417–3442,
2019.
[12] Z. Zuo, C. Liu, Q.-L. Han, and J. Song, “Unmanned aerial v ehicles:
Control methods and future challenges,” IEEE/CAA J. Autom. Sinica ,
vol. 9, no. 4, pp. 601–614, 2022.
[13] P . Wang, W. Mei, J. Fang, and R. Zhang, “Target-mounted i ntelligent
reﬂecting surface for joint location and orientation estim ation,” IEEE J.
Sel. Areas Commun. , vol. 41, no. 12, pp. 3768–3782, 2023.
[14] W. Tang, X. Chen, M. Z. Chen, J. Y . Dai, Y . Han, M. Di Renzo,
S. Jin, Q. Cheng, and T. J. Cui, “Path loss modeling and measur ements
for reconﬁgurable intelligent surfaces in the millimeter- wave frequency
band,” IEEE Trans. Commun , vol. 70, no. 9, pp. 6259–6276, 2022.
[15] X. Shao, R. Zhang, Q. Jiang, J. Park, T. Q. S. Quek, and R. S chober,
“Distributed channel estimation and optimization for 6D mo vable
antenna: Unveiling directional sparsity,” IEEE J. Sel. Topics Signal
Process., vol. 19, no. 2, pp. 349–365, 2025.
[16] X. Guan, Q. Wu, and R. Zhang, “Anchor-assisted channel e stimation
for intelligent reﬂecting surface aided multiuser communi cation,” IEEE
Trans. Wireless Commun. , vol. 21, no. 6, pp. 3764–3778, 2022.
[17] J. Kennedy and R. Eberhart, “Particle swarm optimizati on,” in Proc.
IEEE Int. Conf. Neural Netw. , vol. 4. Perth, W A, Australia: IEEE,
1995, pp. 1942–1948.