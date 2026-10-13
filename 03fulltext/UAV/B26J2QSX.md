---
title: "UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory Optimization and Resource Allocation for Dynamic Environments"
zotero_key: "B26J2QSX"
pdf_key: "WGXCO23E"
doi: "10.1109/vtc2025-fall65116.2025.11309902"
collection: "UAV"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# UAV-Assisted 5G Networks Mobility-Aware 3D Trajectory Optimization and Resource Allocation for Dynamic Environments — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

arXiv:2504.02613v2  [eess.SP]  11 Jun 2025
IEEE VTC2025-FALL 1
UA V -Assisted 5G Networks: Mobility-Aware 3D Trajectory Optimization
and Resource Allocation for Dynamic Environments
Asad Mahmood, Thang X. Vu, Wali Ullah Khan, Symeon Chatzinot as, Björn Ottersten
Interdisciplinary Centre for Security, Reliability and Tr ust (SnT), University of Luxembourg
{asad.mahmood, thang.vu,waliullah.khan, symeon.chatzi notas, bjorn.ottersten}@uni.lu
Abstract—This work proposes a framework for the robust
design of UA V-assisted wireless networks that combine 3D tr a-
jectory optimization with user mobility prediction to addr ess
dynamic resource allocation challenges. We proposed a spar se
second-order prediction model for real-time user tracking cou-
pled with heuristic user clustering to balance service qual ity
and computational complexity. The joint optimization prob lem
is formulated to maximize the minimum rate. It is then decom-
posed into user association, 3D trajectory design, and reso urce
allocation subproblems, which are solved iteratively via s uccessive
convex approximation (SCA). Extensive simulations demons trate:
(1) near-optimal performance with ǫ ≈ 0.67% deviation from
upper-bound solutions, (2) 16% higher minimum rates for distant
users compared to non-predictive 3D designs, and (3) 10 − 30%
faster outage mitigation than time-division benchmarks. T he
framework’s adaptive speed control enables precise mobile user
tracking while maintaining energy efﬁciency under constra ined
ﬂight time. Results demonstrate superior robustness in edg e-
coverage scenarios, making it particularly suitable for 5G/6G
networks.
Index Terms—UA V-assisted communication, 3D trajectory op-
timization, User mobility prediction, Successive Convex A pprox-
imation (SCA), Dynamic resource allocation
I. I NTRODUCTION
Recent advancements in 6G communication systems enable
applications that demand massive connectivity, ultra-rel iable
low-latency communication, and high data rates [1]. Howeve r,
terrestrial base stations (BS) remain vulnerable to disrup tions
from natural disasters or network congestion [2]. An attrac tive
alternative, unmanned aerial vehicles (UA Vs) have emerged as
a ﬂexible alternative, leveraging mobility and reliable li ne-of-
sight (LoS) links to act as ﬂying base stations (BS), mobile
relays, or data collectors [3]. Besides these advantages, U A Vs
face challenges, including ﬁnite battery life [4] that limi ts
ﬂight time by 16% [5], security risks, regulatory barriers, and
communication resources. Moreover, in practical scenario s,
UA Vs lack real-time user location [6], further bottlenecks in
resource allocation and trajectory planning, particularl y for
mobile users requiring seamless connectivity. Additional ly,
higher UA V altitudes improve LoS but increase path loss, thu s
reducing communication efﬁciency [7]. To address these cha l-
lenges, ongoing research focuses on UA V trajectory/placement
optimization, real-time user mobility prediction, and dyn amic
resource allocation, ensuring seamless connectivity and e n-
hanced QoS in next-generation networks.
Recent work on UA V -assisted networks focuses on 2D [2],
[4], [8] and 3D deployment [7] to improve system resource
usage. Static deployment, however, fails to adapt to dynami c
environments. Researchers now emphasize trajectory desig n,
allowing UA Vs to adjust positions dynamically for greater
efﬁciency. Early studies optimized 2D trajectories at ﬁxed
altitudes [3], [9], whereas recent works focus on 3D design [ 1],
[10], [11] which exploit altitude variations for performan ce en-
hancement. For example, [1] uses deep reinforcement learni ng
to optimize multi-UA V coverage and energy efﬁciency under
known user distributions. In [10] authors balances energy
harvesting and data collection in solar-powered UA Vs via
max-min fair 3D trajectory design, while [11] models 3D
energy consumption under stochastic wind, proposing adapt ive
trajectories for energy-efﬁcient communications. Critic ally,
these studies assume static users—an unrealistic premise i n
dynamic environments where user mobility directly impacts
network performance and UA V path planning.
To address this, several studies have been conducted on
mobile users, where the user mobility model follows the
Reference Point Group Mobility (RPGM) model [6], [12],
the Gauss-Markov Mobility (GMM) model [13], [14] or
real-world mobility data collected from Twitter through th e
Twitter API [15]. These models have been applied to both 2D
trajectory design [6], [12], [14], [16] and 3D trajectory de sign
[13], [15] under various assumptions and objectives. Moreo ver,
the studies [6], [12]–[14], [16] assume that UA Vs have acces s
to users’ locations at each time step through Global Posi-
tioning System (GPS), wireless sensing, or feedback, among
other methods. In contrast, continuous tracking through fe ed-
back/signaling results in computational overhead, accele rating
battery depletion and reducing UA V ﬂight duration. Similar ly,
the authors of [6], [12], [13], [16] consider a simpliﬁed LoS
model and do not explicitly account for NLoS components.
Moreover, the authors [13], [14] optimize the trajectory de sign
under the assumption of ﬁxed communication resources, whic h
limits the system’s ﬂexibility. The approach in [15] uses
an Echo State Network (ESN) to predict user locations but
neglects practical constraints like maximum speed, accele r-
ation, and user connectivity time. Optimizing connectivit y
and ﬂying time is crucial for improving UA V efﬁciency and
system performance. This work overcomes prior limitations by
implementing a dynamic 3D trajectory design with a predicti ve
model for user location estimation. It optimizes ﬂight time
and adapts service time allocation while dynamically adjus ting
resources to enhance efﬁciency and responsiveness. The main
contributions of this work are listed below:
A. Contribution
We propose a 3D UA V trajectory design framework inte-
grated with a Markov chain-based user mobility predictor,

IEEE VTC2025-FALL 2
user association, and dynamic resource allocation to maxim ize
the minimum rate in congested/disaster scenarios. The NP-
hard joint optimization problem is decomposed via Block
Coordinate Descent (BCD) into two subproblems: (i) user
association and 3D trajectory optimization and (ii) commu-
nication resource allocation, solved iteratively using pr edicted
user locations. To reduce complexity, a heuristic clusteri ng
method groups users by location, demand, and ergodic ca-
pacity, enabling tractable trajectory and resource alloca tion
via Successive Convex Approximation (SCA) with guaranteed
(theoretical) convergence and polynomial-time complexit y.
Simulations demonstrate near-optimal performance (0.67%
deviation), 15.51% higher rates for edge users versus non-
predictive 3D designs, and 10–30% faster outage mitigation
than time-division benchmarks, with adaptive speed contro l
ensuring energy-efﬁcient tracking in dynamic environment s.
II. S YSTEM MODEL
We consider a UA V -assisted downlink wireless network for
intermittent coverage to N mobile users, indexed by n∈N =
{1,...,N } within a speciﬁed area. A UA V , acting as a ﬂying
base station (BS) with M antennas, operates for up to T time
slots and serves users using orthogonal frequency bands per
time slot. Given the UA V’s limited prior knowledge of user
positions, a Gauss-Markov mobility model [13], [14] genera tes
synthetic (historical) data to train a prediction model at t he
Central Control Unit (CCU). The CCU estimates user location s
based on the historical data and transmits this information to
the UA V via a dedicated control link before ﬂight. To ensure
efﬁcient service, the UA V clusters users into L groups [7],
each containing Nl users (Nl ⊂ N). The service duration
for cluster l is Tl, where Tl < T and ∑l∈LTl≤ T . Each
Tl is further divided into discrete time slots of δ seconds,
assuming stationary users within a slot [3]. At time slot
tl ∈ Tl, the estimated position of user n in cluster l is
Qln[tl] = [ xln[tl] + ∆xln,y ln[tl] + ∆yln]T , where xln[tl] and
yln[tl] are actual positions, and ∆xln, ∆yln denote prediction
errors. The UA V’s 3D position is W [tl] = [ wT [tl],H [tl]]T ,
where w[tl] = [ x[tl],y [tl]]T represents horizontal coordi-
nates and H[tl] the ﬂight altitude. The UA V’s trajectory is
constrained by maximum speeds for horizontal ( Vxymax) and
vertical (VHmax ) movements.
xmin≤x[tl]≤xmax, ∀l,t l, (1)
ymin≤y[tl]≤ymax, ∀l,t l, (2)
Hmin≤H[tl]≤Hmax, ∀l,t l, (3)
|w[tl + 1]−w[tl]|2≤S2xymax, ∀l,t l, (4)
|H[tl + 1]−H[tl]|2≤S2Hmax, ∀l,t l. (5)
Here, (.)min and (.)max denote the bounds for the UA V co-
ordinates, and S(.)max = V (.)maxδ represents the maximum
distance the UA V can travel in each time frame. Due to
limited communication resources (e.g., bandwidth and powe r),
the UA V serves up to Cmax users per time slot tl [7].
To model user connections, we deﬁne a binary variable
J [tl] = [ J ln[tl]]N×L, where J ln[tl] = 1 if user n is connected to
the UA V attl, and J ln[tl] = 0 otherwise. Similarly, to maintain
QoS (rlon), users must remain connected for at least τn slots.
This setup imposes the following constraints:
∑
tl∈Tl
J ln[tl]≥τn, ∀l,n, (6)
∑
n∈Nl
J ln[tl]≤Cmax, ∀l,t l, (7)
∑
l∈L
J ln[tl]≤ 1, ∀n,t l. (8)
A. Transmission and Channel Modeling
This work adopts a probabilistic channel model ac-
counting for LoS and NLoS components. LoS prob-
ability ( PLoS) is a function of user-UA V 3D posi-
tions and the surrounding environment [5], given by
PLoSln[tl] = (1 + b1 exp(−b2(θln[tl]−b1)))−1, where b1 and
b2 represent environmental conditions. The elevation angle
θln[tl] is θln[tl] = sin −1
(
H[tl]
dln[tl]
)
, where the distance dln[tl] is
dln[tl]=
√
‖w[tl]−Qln[tl]‖2 +H 2[tl]. Based on PLoS ln[tl], the
path loss PL ln[tl] is PL ln[tl] = η(.)
(
4πfcdln[tl]
c
)2
, where fc is
the carrier frequency and c the speed of light. The attenuation
factor η(.), determined by PLoS ln[tl], inﬂuences PL ln[tl] with
ηLoS for PLoS ln[tl] ≥ φ (threshold) and ηNLoS otherwise.
Using this, the effective channel gain with maximum ratio
transmission precoding is gln[tl] = |hln[tl](hln[tl])H |P Lln[tl] , where
hln[tl]∈ C1×M represents small-scale fading. Based on gln[tl],
the SNR for the n-th user associated with l-th cluster can be
expressed as: γln[tl] = pln[tl]gln[tl]/σ2. Whereσ2 =Bln[tl]No,
with Bln[tl] as n-th user bandwidth, No the noise spectral
density, and pln[tl] the transmitted power in cluster l at time
slot tl. The achievable data rate for user n is:
Rln = 1/Tl∑tl∈TlBln[tl]log2(1 +γln[tl]). (9)
B. Problem F ormulation
This work aims to enhance the communication system by
maximizing the minimum user data rate, a key performance
metric that ensures fairness among users. To achieve this,
we jointly optimize UA V trajectory, user association, clus -
tering, time slot allocation, ﬂight time, transmit power, a nd
bandwidth. For shorthand, we deﬁne B[tl] = [ Bln[tl]]N ×L,
P [tl] = [ pln[tl]]N ×L, and τ = [τ ]N ×1. The resulting joint
optimization problem is formulated as follows:
max
J [tl],W [tl],B[tl],
P [tl],Tl,τ ,L
min
∀n
∑L
l=1
Rln, (10a)
s.t.Equations (1) to (8) .
Rlnτn≥J lnrlon,∀n,l (10b)
Bln[tl]≤J ln[tl]Bmax,∀n,l,t l (10c)
pln[tl]≤J ln[tl]P max,∀n,l,t l (10d)∑
n∈Nl
pln[tl]≤P maxt ,∀l,t l, (10e)
∑
n∈Nl
Bln[tl]≤Bmax,∀l,t l, (10f)
∑
l∈L
Tl≤T, (10g)
W [0] =W [T ]. (10h)

IEEE VTC2025-FALL 3
where J ln = ∑tl∈TlJ ln[tl]. Constraint (10b) ensures service
quality, requiring usern to receive at least rlon bits. Constraints
(10c) and (10d) allocate bandwidth and power only for users
associated with the UA V . To enforce resource limits, (10e)
and (10f) constrain the maximum transmit power P maxt and
bandwidthBmax. Additionally, (10g) restricts the UA V’s ﬂight
duration, while (10h) ensures it returns to its initial posi tion
at time T .
III. F RAMEWORK FOR UAV TRAJECTORY , U SER
ASSOCIATION AND RESOURCE ALLOCATION
The optimization problem (10) is an NP-hard and mixed
integer nonlinear program (MINLP) due to the integral natur e
of the user association variable J ln[tl], non-linear because of
logarithmic rate function, and nonconvex because variable cou-
pling. Moreover, integrating user mobility with physical l ayer
resource allocation further complicates joint UA V traject ory
and resource optimization. To enhance tractability and efﬁ -
ciency, we apply the block coordinate descent (BCD) method
to decouple the problem into two subproblems: UA V trajectory
and user association (Section III-B) and joint bandwidth an d
power allocation (Section III-C), following the user mobil ity
prediction model in Section III-A.
A. User Mobility Prediction Model:
This section presents a Markov chain-based mobility predic -
tion model [17] deployed on a UA V , predicting user locations
based on prior information from the CCU. We deﬁne a set of
K possible states,S ={s1,s 2,...,s K}, including the current
statesc, forward/backward states sf,s b, left/right states sl,s r,
and other directions{si|i/∈c,f,b,l,r} for each user n. The state
transitions follow a second-order Markov model, represent ed
by a three-dimensional transition matrix Ω = [Ω ijk ]K×K×K,
where Ωijk denotes the probability of transitioning from state
sk to sj, given si and computed by normalizing the observed
transition frequencies ρijk :
Ωijk = ρijk∑
l∈Sρijl
,
∑
k∈S
Ωijk = 1,∀i,j∈S , (11)
where ∑l∈Sρijl represents total transitions from si tosj and
subsequently to any statesl, ensuring probabilistic consistency.
The initial state distribution πn[0] deﬁnes the probability of
user n occupying each state at t = 0:
πn[0] = [π1,n[0],π 2,n[0],...,π K,n[0]], (12)
whereπi,n[0]=1 ifi =c and 0 otherwise. The state distribution
evolves as:
πn[tl] =πn[tl−1]· Ωprev,curr,:. (13)
Computing (13) requires O(K 3) operations per transition and
is computationally expensive for large K. To mitigate this,
we exploit the sparsity of Ω, reducing complexity to O(Nz),
where Nz is the nonzero count:
πn[tl] =πn[tl−1]· sparse(Ωprev,curr,:). (14)
Using (14), the most probable user state at tl determined via
Maximum A Posteriori (MAP) estimation [18]:
sn[tl] = arg maxk∈S πk,n[tl]. (15)
Each state corresponds to a movement vector that updates the
user’s position as:
Qn[tl] =Qn[tl−1] + ∆Qn[tl]. (16)
By leveraging sparsity, the prediction model reduces the pe r-
step complexity from O(K 3) toO(Nz). The total complexity
includes state initialization O(NlK), and O(NlTlNz) for both
state updates and MAP estimation, where steps are detailed i n
Algorithm 1.
Algorithm 1: Mobility Prediction Algorithm
Input: Initial state πn[0], transition matrix Ω, time
slots Tl, users Nl, statesS
Output: Predicted locations Qn[tl]
1 for each user n do
2 for each time slot tl do
3 Update state distribution:
πn[tl]←πn[tl− 1]· sparse(Ω);
4 Predict location: Qn[tl]← arg maxk∈Sπk,n[tl];
5 end
6 end
B. UA V Trajectory and User Association:
Given the users’ locations at time slot tl and ﬁxed radio
resources (B[tl],P [tl]), the subproblem for UA V trajectory
and user association is formulated as follows:
max
J[tl],W [tl],Tl,τ ,L
min
∀n
∑L
l=1
Rln, (17a)
s.t.Equations (1) to (8), (10b), (10c), (10g) and (10h) .
Moreover, joint optimization of UA V trajectory (W [tl]), user
association (J [tl]), clustering (L), serving time (Tl), and user
connectivity (τ ) is still computationally challenging due to
their mutual coupling and high dimensionality. To tackle th is,
we propose a heuristic approach to efﬁciently determine the
number of clusters, serving time, and user connectivity. Th e
L clusters are determined using Shannon’s capacity bound,
which estimates the average spectral efﬁciency:
Λ = E
[
log2
(
1 + P maxt
fcσ2
(⏐⏐hHh⏐⏐2
P L
))]
. (18)
Assuming LoS with PLoS ≈ 1, the (18) provides an upper
bound on the achievable data rate: Rmax = B× Λ. To
satisfy the minimum required data rate ron in constraint (10b),
the user connectivity time is given by: τ =
⌈ ron
Rmax
⌉
. From
this, the UA V’s maximum user capacity per time slot is:
Cmax = ⌊ τ ×Rmaxron ⌋. Using Cmax as an estimate of cluster
size, users are grouped into L =
⌈ N
C max
⌉
clusters via K-
means. With clusters and connectivity times established, t he
next step is to optimize the UA V’s trajectory and serving
schedule. The problem remains nonlinear and non-convex due
to the fractional term Tl in (17a) and the dynamic nature of
user mobility. To overcome this, we adopt an iterative strat egy
where the UA V ﬁrst selects the nearest cluster:
lmin = arg minl∈{1,...,L}‖W [tl]−Ql[tl]‖. (19)

IEEE VTC2025-FALL 4
DuringTl, the UA V tracks and serves users in the l-th cluster,
reducing computational complexity since Nl ≪ N . The
serving time for each cluster is: Tl = f (Nl,D l), Where Nl
is the number of users in the cluster, and Dl is the UA V’s
travel distance to its centroid, ensuring clusters with hig her
user densities receive more service time. Once Tl elapses, the
UA V updates its position, gathers user locations, and dynam -
ically re-clusters the remaining users into L′ ≤ L groups.
This process iterates until all users are served, balancing
user association, trajectory optimization, and computati onal
efﬁciency. To enhance tractability, we introduce the auxil iary
variable: Γ = min Rln, ∀n,, which allows us to decouple
user association and trajectory optimization into separat e sub-
problems. This structured approach simpliﬁes problem-sol ving
and enhances resource utilization and operational efﬁcien cy in
UA V -assisted networks.
1) Optimizing User Association: Given theW [tl], the user
association subproblem can be formulated as:
max
J[tl],Γ
Γ, s.t.Rln≥ Γ, Γτn≥rlon,∀n∈N l (20a)
Equations (6) to (8) and (10c) .
The optimization problem (20) is an integer linear and conve x
problem. This can be solved using standard methods like
integer linear programming (ILP).
2) UA V Trajectory Optimization: Following that, under
the given user association matrix, the subproblem for UA V
trajectory optimization can be expressed as:
max
W [tl],Γ
Γ, (21a)
Rln≥ Γ,∀n∈N l (21b)
s.t.Equations (1) to (5), (10h) and (20a) .
The objective function (21a) in (21) is convex, but the term
Rln deﬁned in (9) remains non-convex due to the log(·)
function. To simplify and enhance tractability, we deﬁne
PL o= 1η(.)( 4πfcc )2σ2 and rewrite (9) as:
Rln = ∑
tl∈Tl
Bln[tl]
Tl
f ln(w[tl],H [tl]); (22)
f ln(w[tl],H[tl])= log2
(
1+ pln[tl]PL o
‖w[tl]−Qln[tl]‖2+H 2[tl]
)
. (23)
To simplify the non-convex problem, we apply a ﬁrst-order
Taylor expansion around the point (w0,H 0). For the shorthand
notation, we introduce:Cl1,n[tl] =‖w0[tl]−Qln[tl]‖2 +H 20 [tl],
Cl2,n[tl] = pln[tl]PL o,C3 = ln(2) and expressed the Taylor
expression as:
f (‖w[tl]‖2,H 2[tl])≈f (‖w0[tl]‖2,H 20 [tl])
+ ∂f∂‖w‖2
⏐⏐⏐⏐
(‖w0[tl]‖2,H20 [tl])
(‖w[tl]‖2−‖w0[tl]‖2)
+ ∂f∂H 2
⏐⏐⏐⏐
(‖w0[tl]‖2,H20 [tl])
(H 2[tl]−H 20 [tl]). (24)
The partial derivatives of (23) with respect to ‖w‖2 and H 2
are given by:
∂f
∂||w||2
⏐⏐⏐⏐
(·)
= ∂f∂H 2
⏐⏐⏐⏐
(·)
=− Cl2,n[tl]C3Cl1,n[tl](Cl1,n[tl] + Cl1,n[tl]) = ∇f ln[tl]. (25)
where (·) = ( ||w0[tl]||2,H 20 [tl]). Substituting (25) into the
(24) gives the ﬁrst-order approximation of (23) as shown (26 ).
Following that, by substituting (26) into the (22), we obtai n
the lower bound (Rlbln) for Rln as:
Rln≈Rlbln≥ ∑
tl∈Tl
Bln[tl]
Tl
[
f ln(‖w[tl]‖2,H 2[tl])] (27)
This lower bound simpliﬁes the (21), enabling tractable opt i-
mization. The joint problem is then formulated as:
max
W [tl],Γ
Γ, s.t.Rlbln≥ Γ,∀n∈N l (28a)
s.t.Equations (1) to (5), (10h) and (20a) .
The optimization problem (28) is convex, enabling a (sub-
optimal) solution for (20) using CVX. To bridge the gap
between optimal and suboptimal solutions, the UA V’s initia l
trajectory is set according to [3] for Nl users in the l-
th cluster, while adhering to horizontal ( Vxymax) and vertical
(VHmax ) speed constraints in (4) and (5). The UA V follows
a circular trajectory in 3D space at a constant speed V =√
V 2xy +V 2H . The trajectory’s center and radius are deﬁned as
ctrj = [xtrj,y trj,z trj]T andρtrj, respectively, where 2πρtrj =VT l
for any period Tl. The geometric center of users in cluster l is:
cg =
∑Nl
n=1 Qn[tl]
Nl . The radius ρu represents the farthest userfrom cg, given by: ρu = max n∈Nl|Qn[tl]− cg|. Using a circle
packing scheme (CP), the trajectory’s center ctrj and radius ρcp
are determined. To ensure feasibility, the trajectory radi us is
capped by: ρtrj = min(ρmax, ρcp2 ), where ρmax = VmaxTl2π .
Thus, the initial trajectory at time slot tl is:
ˆW[tl] =


xtrj +ρtrj cosθtl
ytrj +ρtrj sinθtl
ztrj

,θ tl ≜ 2π (tl− 1)Tl− 1 . (29)
This ensures the UA V trajectory adheres to coverage and speed
constraints, as outlined in Algorithm 2
Algorithm 2: Joint UA V Trajectory and Association
Input: Qn[tl],B,P
Output: OptimizedW [tl],J [tl]
1 Solve user association: J ∗i← solve(20);
2 Optimize UA V trajectory:W ∗i← solve (28);
C. Joint Bandwidth and Power Allocation
Under the given trajectory and user association matrix, the
joint optimization problem for bandwidth and power allocat ion
is as follows:
max
B[tl],P [tl],Γ
Γ, (30a)
s.t. 1Tl ∑tl∈TlBln[tl] log2(1 +γln[tl])≥ Γ,∀n∈N l (30b)

IEEE VTC2025-FALL 5
f ln(‖w[tl]‖2,H 2[tl])≈f (‖w0[tl]‖2,H 20 [tl])+∇f ln[tl](‖w0[tl]‖2,H 20 [tl])·(‖w[tl]‖2−‖w0[tl]‖2+H 2[tl]−H 20 [tl]) (26)
Γτn≥J lnrlon,∀n∈N l (30c)
Equations (10c), (10e) and (10f) .
whereγln[tl] = pln[tl]gln[tl]Bln[tl]No , the problem (30) remains nonconvexdue to constraint (30b). We introduce auxiliary variables
Ψ[tl] = [Ψ ln[tl]]N ×L and rewrite (30) as:
max
B[tl],P [tl],Γ
Γ, (31a)
s.t. 1Tl∑tl∈TlBln[tl] log2(1 + Ψln[tl])≥Γ,∀n∈N l (31b)
pln[tl]gln[tl]
Bln[tl]No ≥ Ψln[tl],∀n∈N l,t l∈T l, (31c)
Equations (10c), (10e), (10f) and (30c) .
The problem (31) is equivalent to (30). Demonstrate this
equivalence by showing that the inequalities in constraint s
(31b) and (31c) are satisﬁed. The challenge lies in solving
(31b) and (31c). To address this, we introduce the slack
variableψ[tl] = [ψln[tl]]N ×L and reformulate constraint (31b)
as:
log2(1 + Ψln[tl])≥ψln[tl],∀n∈N l,t l∈T l. (32)
1
Tl
∑
tl∈Tl
Bln[tl]ψln[tl]≥ Γ,∀n∈N l. (33)
The constraint (32) is convex in nature. To deal with constra int
(33), we ﬁrst reformulate it into a difference-of-convex pr e-
sentation and then apply the ﬁrst-order approximation [19] .
Given the feasible solution ( ˆBln[tl], ˆψln[tl]) from the current
iteration, constraint (33) is approximated in the next iter ation
as:
∑
tl∈Tl
2( ˆBln[tl] + ˆψln[tl])(Bln[tl] +ψln[tl]) (34)
−
∑
tl∈Tl
( ˆBln[tl]+ ˆψln[tl])2≥∑
tl∈Tl
(Bln[tl]2 +ψln[tl]2)+2TlΓ.
To address constraint (31c), we rewrite it as:
pln[tl]gln[tl]N −1o ≥ Ψln[tl]Bln[tl]. (35)
Since the left side of (35) is linear and convex, while the rig ht
side is neither, we apply a ﬁrst-order approximation to the
nonconvex side. Given the feasible solution ( ˆBln[tl], ˆΨln[tl]),
approximate constraint (31c) as:
Ψln[tl]Bln[tl]≈ ˆBln[tl]Ψln[tl] + ˆΨln[tl]Bln[tl]. (36)
gln[tl]pln[tl]
No
≥ ˆBln[tl]Ψln[tl] + ˆΨln[tl]Bln[tl]. (37)
Using (37) and (34), the inner approximations of (35) and
(33), respectively, we approximate the (30) as:
max
B[tl],P [tl],Γ,ψ[tl],Ψ[tl]
Γ, (38a)
Equations (10c), (10e), (10f), (30c), (32), (34) and (37) .
We observe that problem (38) is convex and can be efﬁ-
ciently solved using convex optimization tools such as CVX.
Since its solution satisﬁes Equations (10c), (10e), (10f), (30b)
and (30c), it provides a (sub)optimal solution for (30). The
performance gap between this (sub)optimal solution and the
global optimum of (30) primarily depends on the initializat ion
of ˆΨ, ˆψ, ˆB, and ˆP . To address this, we propose an iterative
method that reﬁnes the solution through a series of convex
subproblems, as detailed in Algorithm 3.
2 4 6 8 10 12 14
Iterations
0.5
1
1.5
2
Min Rate (bps)
108
With Res. Allo. -  Average
With Res. Allo. - Cluster 1
With Res. Allo. - Cluster 2
With Res. Allo. - Cluster 3
With Res. Allo. - Cluster 4
Without Res. Allo. - Average
Without Res. Allo. - Cluster 1
Without Res. Allo. - Cluster 2
Without Res. Allo. - Cluster 3
Without Res. Allo. - Cluster 4
11
2.1
2.15
2.2
108
Fig. 1: Convergence Analysis
Algorithm 3: Joint Resource Allocation
Input: V ariables ˆΨ, ˆψ, ˆB, ˆP ,Qn,W ,J ,∀tl∈T ,
∀n∈N ,Fprev← 0, P maxt , Bmaxt , rlon,
maximum iterations Imax, tolerance ǫ.
Output:B,P,∀tl∈T ,∀n∈N l
1 [B∗i,P ∗i, Γ∗i,ψ∗i, Ψ∗i ]← solve (38) using CVX;
2 Update: [ ˆΨ, ˆψ, ˆB, ˆP ]← [Ψ∗i,ψ∗i,B∗i,P ∗i ].
D. Joint Algorithm Design and Complexity Analysis
The iterative algorithm solves (10) to obtain a (sub)optima l
solution by determining the minimum user connectivity time
τ , UA V ﬂight time Tl, number of clusters L, and user
partitioning. User locations Qn[tl] are ﬁrst predicted us-
ing a mobility model. Then, Algorithm 2 jointly optimizes
user association and UA V trajectory with complexity C1 =
O(2Nl +Z 3.5 log(1/ǫ)), where Z is the number of decision
variables. Algorithm 3 allocates bandwidth and power by
solving the convex problem (38) via the interior point metho d,
with complexity C2 = O((4NlTl + 1) 3). The joint solution
at iteration i is Π∗i [tl] = [ B∗i,P ∗i,Q∗i,W ∗i,J ∗i ], and the
objective is Fcurrent = min ∀nRn(Π∗i [tl],∀tl ∈ Tl). The
solution is reﬁned until |Fprev−F current| < ǫ. Since each
subproblem’s feasible region is a subset of the original joi nt
problem, and each iteration yields non-decreasing objecti ve
values [19, Sec. III-A], convergence is guaranteed. The ove rall

IEEE VTC2025-FALL 6
(a) 3D UA V ﬂight trajectory.
0 10 20 30 40 50 60 70
Time Slots
0
5
10
15
20
25UAV Speed (m/s)
UAV-Cluster 1
UAV-Cluster 2
UAV-Cluster 3
UAV-Cluster 4
Users Speed
Hovering
Start
End
(b) UA V speed variations.
10 20 30
Time Slots
0
0.2
0.4
0.6
0.8
1
Outage (0 = No, 1 = Yes)
(a)
Proposed Scheme ( =4)
Time Divided Scheme( =4)
Proposed Scheme ( =8)
Time Divided Scheme( =8)
10 20 30
Time Slots
0
0.5
1
1.5
2
Min Rate (bps)
108 (b)
Proposed Scheme ( =4)
Time Divided Scheme ( =4)
Proposed Scheme ( =8)
Time Divided Scheme ( =8)
(c) Proposed vs.Time Dividend [16].
Fig. 2: UA V trajectories and user associations with optimal resource allocation.
10 15 20 25 30
Power (dBm)
1
1.5
2
2.5
3
3.5
4
Min Rate (bps)
108
Upper Bound Solution-C1 Upper Bound Solution-C4
Proposed Scheme-C1 Proposed Scheme-C4
2D Traj. With Prediction-C1 2D Traj. With Prediction-C4
3D Traj. Without Prediction-C1 3D Traj. Without Prediction-C4
2D Traj. Without Prediction-C1 2D Traj. Without Prediction-C4
15
2.48
2.5
2.52
2.54
108
2.4
2.5
2.6
108
Fig. 3: Performance Across Different Schemes. Legend abbre viations: C1
Cluster 1, C4 Cluster 4.
complexity isO(LImax(C1+C2)), where Imax is the number
of iterations per cluster.
IV. N UMERICAL RESULTS
This section presents numerical results from MA TLAB
simulations over independent channel realizations. 10 mobile
users are uniformly distributed across a 100× 100m area, with
constant movement simulated to mimic real-world mobility.
The UA V operates under a dynamic 3D trajectory, clustering
users and serving them sequentially based on predicted loca -
tions. Key simulation parameters include a total ﬂight time of
210 s, a transmit power of 10 dBm, a maximum bandwidth
of 20MHz, a frequency of 900 MHz, a noise power spectral
density of−168 dBm/Hz, and altitude constraints of 21− 100
meters. The UA V’s vertical and horizontal movement is limited
to 15 m and 30 m, respectively. Performance is compared
against ﬁve benchmarks: (i) an Upper Bound Solution with
optimal 3D trajectory/resource allocation using perfect u ser
location knowledge [13],(ii) the Proposed Scheme without
prediction (using current locations only), (iii) the Propo sed
Scheme with ﬁxed communication resources [13], [14], (iv)
the Time Dividend Approach allocating one user per slot with
equal resources [16], and (v)2D Trajectory designs with and
without prediction.
Fig. 1 compares the convergence of the proposed scheme
with/without resource optimization. Both cases converge
within 10 iterations (one curve per cluster). The optimized
scheme achieves convergence by iteration 8 with minimal
deviation (0.67%), whereas the non-optimized scheme con-
verges faster (iteration 4) but exhibits signiﬁcantly high er
deviation (20%). The dashed average line underscores resou rce
optimization’s role in ensuring uniformity, highlighting its
necessity alongside trajectory design.
Fig. 2 illustrates the UA V’s 3D trajectory and user asso-
ciation, optimizing ﬂight time and resource allocation. Ti me
slots are dynamically assigned ( Cmax = 3 , τ = 4 ) to limit
cluster size while ensuring users are served for τ slots. The
UA V adapts its trajectory Fig. 2a, re-clustering users afte r
each service session, and adjusts speed as per users Fig.2b
for seamless tracking. Simulations with constrained ﬂight time
(Tl,s < Nl× τ ) evaluate outage probability Fig. 2ca and
minimum rate Fig. 2cb. For τ = 4 and 8, our scheme achieves
zero outages 10% and 30% faster, respectively, than the Time
Dividend Approach, demonstrating the importance of dynami c
UA V -user association and trajectory design.
Fig. 3 compares minimum rates across benchmark schemes
under transmit powers ranging from 10 dBm to 30 dBm.
The proposed scheme with sparse second-order prediction
achieves near-upper-bound performance ( ǫ ≈ upper-bound)
for both clusters C1 (nearest users) and C4 (farthest users) .
Notably, the 3D trajectory design without prediction matches
proposed scheme performance for C1 but lags by 15.51% for
C4, underscoring the prediction model’s critical role for d istant
users. Crucially, the 3D non-prediction design still outpe rforms
2D-with-prediction trajectories, while 2D designs gain si gnif-
icant improvement from prediction integration. These resu lts
demonstrate that 3D trajectory optimization with predicti on
ensures robust performance across user distributions, par tic-
ularly for edge-of-coverage scenarios where conventional 2D
designs falter.
V. C ONCLUSION
This work presents a UA V communication framework that
combines 3D trajectory optimization with user mobility pre -
diction to improve QoS in dynamic networks. The results
show that the sparse second-order prediction model deliver s
near-optimal performance ( ǫ ≈ 0.67%) and increases rates
for distant users by 16% compared to the non-predictive
3D designs. Furthermore, 3D trajectory optimization con-

IEEE VTC2025-FALL 7
sistently outperforms 2D designs, even without prediction .
The integration of adaptive UA V speed control and heuristic
clustering ( Cmax = 3 ,τ = 4 ) leads to a 10–30% faster
reduction in outages compared to time-division benchmarks .
Moreover, simulations conducted under constrained ﬂight t ime
(Tl,s<N l×τ ) demonstrate the robustness of the framework,
making it particularly suitable for edge-of-coverage scen arios.
ACKNOWLEDGMENT
This research was funded by the Luxembourg
National Research Fund (FNR) under grant
INTER/MOBILITY/2023/IS/18014377/MCR and project
RUTINE (ref. C22/IS/17220888).
REFERENCES
[1] H. He et al. , “Deep reinforcement learning-based distributed 3d UA V
trajectory design,” IEEE Trans. Commun., vol. 72, pp. 3736–3751, 2024.
[2] Z. Y ang et al. , “Deployment Optimization of Dual-Functional UA Vs
for Integrated Localization and Communication,” IEEE Trans. Wireless
Commun., vol. 22, no. 12, pp. 9672–9687, 2023.
[3] Q. Wu et al. , “Joint Trajectory and Communication Design for Multi-
UA V Enabled Wireless Networks,” IEEE Trans. Wireless Commun. ,
vol. 17, no. 3, pp. 2109–2121, 2018.
[4] L. Wang et al. , “Deployment and association of multiple UA Vs in
UA V-assisted cellular networks with the knowledge of stati stical user
position,” IEEE Trans. Wireless Commun., vol. 21, pp. 6553–6567, 2022.
[5] M. Alzenad et al. , “3-d placement of an unmanned aerial vehicle base
station (UA V-bs) for energy-efﬁcient maximal coverage,” IEEE Wireless
Commun. Lett. , vol. 6, no. 4, pp. 434–437, 2017.
[6] J. Wang et al. , “Joint trajectory design and power allocation for UA V
assisted network with user mobility,” IEEE Trans. V eh. Technol., vol. 72,
no. 10, pp. 13 173–13 189, 2023.
[7] A. Mahmood et al. , “Joint Optimization of 3D Placement and Radio
Resource Allocation for Per-UA V Sum Rate Maximization,”IEEE Trans.
V eh. Technol., vol. 72, pp. 13 094–13 105, 2023.
[8] H. Hydher et al. , “UA V deployment for data collection in energy
constrained wsn system,” in IEEE INFOCOM 2022 - IEEE Conf.
Comput. Commun. W orkshops, 2022, pp. 1–6.
[9] X. Jing et al. , “ISAC From the Sky: UA V Trajectory Design for
Joint Communication and Target Localization,” IEEE Trans. Wireless
Commun., vol. 23, no. 10, pp. 12 857–12 872, 2024.
[10] C. Sun et al. , “Max–min fair 3d trajectory design and transmission
scheduling for solar-powered ﬁxed-wing UA V-assisted data collection,”
IEEE Trans. Wireless Commun. , vol. 22, no. 12, pp. 8650–8665, 2023.
[11] X. Dai et al. , “Energy-efﬁcient UA V communications in the presence
of wind: 3d modeling and trajectory design,” IEEE Trans. Wireless
Commun., vol. 23, no. 3, pp. 1840–1854, 2024.
[12] X. Y an et al. , “Joint optimization of resource allocation and trajector y
control for mobile group users in ﬁxed-wing UA V-enabled wir eless
network,” IEEE Trans. Wireless Commun. , vol. 23, no. 2, pp. 1608–
1621, 2024.
[13] B. Omoniwa et al. , “Optimizing energy efﬁciency in UA V-assisted
networks using deep reinforcement learning,” IEEE Wireless Commun.
Lett., vol. 11, no. 8, pp. 1590–1594, 2022.
[14] Z. Y ang et al. , “Dynamic trajectory and ofﬂoading control of UA V-
enabled mec under user mobility,” in 2021 IEEE ICC W orkshops, 2021,
pp. 1–6.
[15] X. Liu et al. , “Trajectory design and power control for multi-UA V
assisted wireless networks: A machine learning approach,” IEEE Trans.
V eh. Technol., vol. 68, no. 8, pp. 7957–7969, 2019.
[16] X. Liu, B. Lai, B. Lin, and V . C. M. Leung, “Joint communic ation
and trajectory optimization for multi-UA V enabled mobile i nternet of
vehicles,” IIEEE Trans. Intell. Transp. Syst. , vol. 23, no. 9, pp. 15 354–
15 366, 2022.
[17] Y . Jiang, M. Saito, and K. C. Sinha, Bridge performance prediction
model using the Markov chain , 1988, no. 1180.
[18] J.-L. Gauvain et al. , “Maximum a posteriori estimation for multivariate
gaussian mixture observations of markov chains,” IEEE Trans. on spe.
and aud. proces. , vol. 2, pp. 291–298, 1994.
[19] T. X. Vu et al. , “Dynamic bandwidth allocation and precoding design
for highly-loaded multiuser miso in beyond 5g networks,” IEEE Trans.
Wireless Commun., vol. 21, pp. 1794–1805, 2021.