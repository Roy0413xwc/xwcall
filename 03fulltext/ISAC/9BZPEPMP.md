---
title: "Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UAV Networks"
zotero_key: "9BZPEPMP"
pdf_key: "CQTI13K1"
doi: "10.1109/gcwkshp64532.2024.11100546"
collection: "ISAC"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# Resource Allocation Based on Optimal Transport Theory in ISAC-Enabled Multi-UAV Networks — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

arXiv:2410.02122v1  [cs.NI]  3 Oct 2024
Resource Allocation Based on Optimal Transport
Theory in ISAC-Enabled Multi-UA V Networks
Y ufeng Zheng∗, Lixin Li ∗, Wensheng Lin ∗, Wei Liang ∗, Qinghe Du † and Zhu Han ‡
∗School of Electronics and Information, Northwestern Polyt echnical University, Xi’an, China, 710129
†School of Information and Communications Engineering, Xi’ an Jiaotong University, Xi’an, China, 710049
‡Department of Electrical and Computer Engineering, Univer sity of Houston, Houston, TX, 77004
Abstract—This paper investigates the resource allocation op-
timization for cooperative communication with non-cooper ative
localization in integrated sensing and communications (IS AC)-
enabled multi-unmanned aerial vehicle (UA V) cooperative n et-
works. Our goal is to maximize the weighted sum of the system’ s
average sum rate and the localization quality of service (Qo S) by
jointly optimizing cell association, communication power alloca-
tion, and sensing power allocation. Since the formulated pr oblem
is a mixed-integer nonconvex problem, we propose the altern ating
iteration algorithm based on optimal transport theory (AIB OT)
to solve the optimization problem more effectively. Simula tion
results demonstrate that the AIBOT can improve the system
sum rate by nearly 12% and reduce the localization Cr ´amer-
Rao bound (CRB) by almost 29% compared to benchmark
algorithms.
Index Terms —Integrated sensing and communication, multi-
unmanned aerial vehicle networks, cooperative communicat ion,
non-cooperative localization, optimal transport theory.
I. I NTRODUCTION
With the rapid development of unmanned aerial vehicle
(UA V) [1]–[4] and artiﬁcial intelligence [5]–[7] in the six th
generation (6G) wireless networks, multi-UA Vs are increas -
ingly used in military and civil applications. Compared wit h
single UA V , cooperative multi-UA Vs have a more robust
distributed architecture and more comprehensive operatio nal
range [8]. Multi-UA V networks can improve the capacity of
UA V communications and enhance the reliability of transmis -
sions. However, 6G has a higher requirement for security [9] .
Due to the increasingly serious security issues caused by th e
“black ﬂight” of UA Vs, incidents harming public property an d
even national security have occurred many times.
Integrated sensing and communications (ISAC), considered
to have a wide range of application prospects, has been
established as one of the critical technologies for 6G. In
6G mobile communication networks, ISAC technology will
provide high-quality wireless connectivity and high-prec ision
sensing capability, which will boost many emerging applica -
tions, such as UA V communication.
Since ISAC can effectively reduce hardware costs and
improve spectrum efﬁciency, researchers have started to ex -
plore the application of ISAC in UA V networks. In ISAC-
enabled UA V networks, designing efﬁcient joint optimizati on
This paper has been accepted for publication in IEEE Globeco m 2024
workshop.
algorithms for adaptive resource allocation has become a
challenge. Liu et al. [10] proposed a periodic pass-sensing
integration mechanism, which jointly optimized transmitt ing
beamforming, user association, sensing time selection, an d
UA V trajectory to maximize the achievable rate. Cao and Y u
[11] investigated a large-scale multiple-input multiple- output
ISAC system that supports cell-free and proposed a joint use r
scheduling and power allocation scheme, where the nonconve x
resource allocation problem is relaxed to a linear programm ing
problem. Liu et al. [12] achieved maximum energy efﬁciency
and minimum user radar mutual information for ISAC-enabled
UA Vs by optimizing user scheduling, transmit power and
UA V trajectories. However, the researches mentioned above
do not consider multi-UA V cooperative communication and
the potential non-cooperative UA V localization problem. I n
addition, the above works deal with mixed integer nonconvex
problems by relaxing the discrete variables into continuou s
variables, which inevitably causes accuracy problems.
Therefore, avoiding collision or interference to the ﬂight
trajectory within UA Vs is necessary by localizing the loca-
tion of non-cooperative UA V . Meanwhile, accurate position
acquisition between UA V cluster nodes is the basis of UA V
cluster cooperative. In addition, 6G also requires the syst em
to have the adaptive capability [13], [14]. How to design
efﬁcient joint optimization algorithms for adaptive resou rce
allocation and deal with the mixed integer nonconvex resour ce
allocation problem more efﬁciently in ISAC-enabled UA V
networks has become an important problem. In this paper,
we study the resource allocation problem for cooperative
communication with non-cooperative localization in the IS AC-
enabled multi-UA V cooperative network. We summarize the
main contributions in the following:
• The relationship between localization quality of service
(QoS) and sum rate is ﬁrst revealed. We formulate an
optimization problem that maximizes the weighted sum
of the system average sum rate and localization QoS by
jointly optimizing the optimal cell association, commu-
nication power and sensing power allocation under the
constraints of the localization QoS of all UA Vs and the
sum rate of cooperative UA Vs.
• Since the formulated problem is a mixed-integer non-
convex problem and optimal transport theory (OT) can
solve mixed-integer nonconvex problems more effectively

/9')2OTQ +INUROTQ 
(RUIQOTMZNK/9')ROTQ 
)UUVKXGZO\K;'< 
)UUVKXGZO\K;'< 4UTIUUVKXGZO\K 
;'< 
:NKIUTZXURIKTZKX 
:NKHGYKYZGZOUT 
Fig. 1. The system model.
by utilizing probability theory to capture the generalized
distribution, the alternating iteration algorithm based o n
optimal transport theory (AIBOT) is proposed to solve
the optimization problem more effectively.
• The simulation results demonstrate that the AIBOT can
improve the system sum rate by nearly 12% and reduce
the localization Cr´ amer-Rao bound (CRB) by almost 29%
compared to benchmark algorithms.
II. S YSTEM MODEL
A. Network Model
We consider a downlink communication system supporting
ISAC. The system consists of M multi-antenna dual-functional
ground base stations, K + 1 UA Vs, and a control centre,
where the UA Vs consist ofK single-antenna cooperative UA V
users and one single-antenna non-cooperative UA V , as shown
in Fig. 1. At the n-th time slot, the coordinates of the k-th
UA V are denoted as ~Uk(n) = (xu,k(n),yu,k(n),zu,k(n)), the
coordinates of the m-th dual-function base station are denoted
as ~Bm(n) = ( xb,k(n),yb,k(n),zb,k(n)). The coordinates of
the non-cooperative UA Vs are denoted as ~A(n).
Each base station is equipped with a uniform planar array
antenna consisting of Nt antenna units, where the position of
the en-th antenna at the m-th base station denotes £m,en.
Let aj,m(n) ∈ { 0, 1},n ∈ { 1, · · ·,N } denote the association
variable between the m-th ground base station and the k-th
UA V . If~Uk ∈ Qm, then aj,m(n) = 1 indicates that the k-th
UA V is provided with ISAC or sensing service by the m-th
base station at the n-th time slot. Otherwise, aj,m(n) = 0 .
The total ﬂight time of the UA V is denoted by T , which is
divided into N time slots having the same time interval δt.
We deﬁne UA Vs’ spatial distribution function f (x,y,z ) to
capture the probability of each UA V appearing around a three -
dimensional location q = ( x,y,z ). Qm denotes the three-
dimensional cell associated with the m-th dual-functional
ground base station, and the average number of UA V inside
Qm can be expressed as
Um =K
∫
Qmf (q)dq, (1)
where the spatial distribution function f (q) = f (x,y,z )
captures the probability of each UA V user appearing around
the three-dimensional location q = (x,y,z ).
The departure angle between the m-th ground base station
and the k-th UA V can be denoted as θk,m = [θazk,m,θelk,m]T ,
where θazk,m and θelk,m indicate the departure angle in azimuth
and elevation angles, respectively. θazk,m and θelk,m can be
expressed by
θazk,m ∆=a tan 2([~Bm]2 − [~Uk]2, [~Bm]2 − [~Uk]1),
θelk,m ∆= arccos
(
[~Bm]3 − [~Uk]3
‖~Bm − ~Uk‖
)
. (2)
B. Communication Model
After completing stages 1 and 2, the base station acquires
estimated channel state information ˆhk,m for the UA V and its
position ˆUk.ˆhck,m(n) by the path loss model can be expressed
as
ˆhck,m(n) = λejϕk,m(n)
4π(ˆdk,m(n) + ∆dk,m(n))ˆαk,m(n), (3)
where ˆαk,m(n) represents the estimated response vector of
the antenna array, which can be calculated based on the
estimated position by (2). ϕk,m(n) represents the phase shift,
∆dk,m(n) = dk,m(n) − ˆdk,m(n) represents the location
sensing error, and dk,m(n) =
‖‖‖~Bm(n) − ~Uk(n)‖‖‖ represents
the actual distance between the base station and the UA V .
The communication signal yk,ms (n) received by the k-th
cooperative UA V from the m-th base station at the n-th time
slot using the receiver beamforming vector ~wk,m(n) can be
expressed as
yk,ms (n) =
√
pk,ms (ˆhck,m + ∆hck,m)H wk,msk,ms (n −τk,m)
+b(n), (4)
whereb(n) denotes additive white Gaussian noise, ∆hck,m(n)
denotes the channel state information error, which can be
expressed as
∆hck,m(n) = λejϕk,mˆαk,m(n)4π∆dk,m(n) = λejϕk,m(n)ˆαk,m(n)4π(dk,m(n) −ˆdk,m(n)).
(5)
The sum rate of all cooperative UA Vs can be expressed as
Rsum =
K∑
k=1
N∑
n=1
bk,m(n)
× log2[1 +ak,m(n)
pk,mc (n)λ2| ˆαHk (n)wk(n)|2
16π2N0( ˆdk,m(n)+∆dk,m(n)) ],(6)
where bk,m(n) denotes the bandwidth allocated to the k-th
UA V by them-th base station in the n-th time slot.

C. Sensing Model
The baseband form yj,ms (n) in which the m-th ground base
station receives the reﬂected echo signal from the k-th UA V
can be expressed as
yj,ms (n) =
√
pj,ms (n)hsHj,m(n)wj,m(n)sj,ms (n −τj,m) +b(n),
(7)
where hsj,m(n) denotes the composite channel between the k-
th UA V and the m-th base station, τj,m = ‖ ~Bm− ~Uj‖c denotes
the delay between the j-th UA V and the m-th base station,
andc denotes the speed of light. hsk,m(n) can be expressed as
hsj,m(n) = ςj,m(n)α(θj,m(n)), (8)
where ςj,m(n) = |ςj,m(n)|ejϕj,m(n) denotes the composite
channel gain, |ςj,m(n)| = λ4π‖ ~Uj (n)− ~Bm(n)‖ ,ϕj,m(n) denotes
the phase shift, α(θj,m(n)) denotes the antenna response
vector, which can be expressed as [15]
α(θj,m(n)) = ejQTk,m(n)κ(θj,m(n)), (9)
where Qk,m(n)
∆
= [ £m,1(n), · · ·, £m,Nt(n)], and
κ(θj,m(n))
∆
= 2πλ [sinθel(n) cosθaz(n), sinθel(n) sinθaz(n),
cosθel(n)], λ denotes the wavelength.
A generalized form to simplify the expression is used to
characterize the estimated CRB for the j-th UA V , which can
be expressed as [16]
CRB (dj (n)) ∝ (pj,ms (n)|ςj (n)|2B2rms,j )−1,
CRB (θj(n)) ∝ (pj,ms (n)|ςj(n)|2WNN )−1, (10)
wherepj,ms (n) denotes the transmit power for localization non-
cooperative UA V ,Brms,j and WNN represent the effective
bandwidth and the null-to-null beam width of the receiving
antennas, respectively.
Localization focuses on target distance and angle of arriva l
estimation, so the localization error is deﬁned as the CRB of
target distance and angle of arrival estimation. By transfo rming
the minimization problem of the CRB into the maximization
problem of its inverse, the target parameters of j-th sensing
target can be expressed as
ρj = ̟1CRB (d) + ̟2CRB (θ)
=̟1
pj,ms (n)|ςj,m(n)|2bj
β1
+̟2
pj,ms (n)|ςj,m(n)|2
β2
, (11)
where β1 and β2 denote the scaling factor, ̟1 and ̟2
denote the normalization factors used to unify the distance
and departure angle units.
D. Problem F ormulation
For simplicity, time slot n will be omitted in the follow-
ing. The cell association variable, the communication and
sensing power allocation variable can be denoted as Q =
{Q∗1, · · ·,Q ∗M }, Pc = {p1,1c , · · ·,pK,Mc ,pK+1,Mc }, Ps =
{p1,1s , · · ·,pK,Ms ,pK+1,ms }. The objective is to maximize the
weighted sum of the system average sum rate and average
localization QoS by jointly optimizing the cell associatio n,
communication power allocation and sensing power allocati on
under non-cooperative UA V localization QoS and cooperativ e
UA V sum rate constraints, which can be formulated as
P1 : max
Q,Pc,Ps
GTOL =ϑ1
Rsum
K + (1 −ϑ1)ϑ2
ρsum
K + 1
s.t. C1 :Um =M
∫
Qmf (q)dq,
C2 : Qr ∩ Qi = ∅, ∀i ⁄=r ∈ {1, · · ·,M },
⋃
m∈M
Qm = q,
C3 :pmin ⩽pk,mc ,pk,ms ⩽pmax, ∀k ∈ {1, · · ·,K },
∀m ∈ {1, · · ·,M },
C4 :
K∑
k=1
pk,m =Ptotal, ∀m ∈ {1, · · ·,M },
C5 :ρk ⩽ρmin,∀k ∈ {1, · · ·,K }
C6 :Rmin ⩽Rk,∀k ∈ {1, · · ·,K } (12)
whereRsum andρsum represent the sum rate of all cooperative
UA Vs and target parameters of all UA Vs, respectively. ϑ1
denotes the weights of sum rate and localization QoS and
ϑ2 denotes the sum rate-localization QoS mapping factor to
ensure that the sum rate and localization QoS are at the same
scale level [16]. C1 denotes the number of cooperative UA V
users in the region Qm. C2 ensures that the three-dimensional
correlation spaces are disjoint and their combination cove rs
the entire space under consideration. C3 denotes the maxi-
mum and minimum transmission communication power and
sensing power constraints. C4 denotes the total power budge t
constraints. C5 denotes the UA V localization QoS constrain ts.
C6 denotes the communication QoS constraints.
III. T HE AIBOT-B ASED JOINT CELL ASSOCIATION AND
POWER ALLOCATION OPTIMIZATION
P1 is a mixed integer nonconvex problem and the objective
function as well as constraints are highly nonconvex, which
is difﬁcult to convert into a convex function. However, OT
can utilize probability theory and statistics to capture th e
generalized distribution of wireless devices. It can provi de a
more in-depth fundamental analysis of network performance .
Therefore, we propose AIBOT to solve the proposed problem.
Since the OT is used to solve the minimization problem, P1
can be transformed into
P2 : min
Q,Pc,Ps
− GTOL
s.t. C 1,C 2,C 3,C 4,C 5,C 6. (13)
A. Cell Association Design
For a given transmit power, let z(Ul) = 1Ul , and the optimalcell association optimization subproblem can be expressed as
P3 : min
Q
M∑
m=1
∫
Qm
1
Um
[GTOLf (x,y,z )]dxdydz
=
M∑
m=1
∫
Qmz(Um)[GTOLf (x,y,z )]dxdydz
s.t. C 1,C 2,C 5,C 6. (14)

P3 can be modeled as a semi-discrete OT problem, where
the base stations are considered to follow discrete distrib utions,
and the UA Vs are considered to follow continuous distri-
butions. The optimal cell association must be obtained by
mapping UA Vs to the base stations at a minimum cost. Next,
we can proceed to solve P3 using the following theorem:
Theorem 1: The optimal 3D cellular association for a dual-
functional ground base station can be expressed as
qM =
{
arg min
i∈{1,···,M }
− 1UiGTOL (q0) + GT OL(q0)UiK
}
. (15)
Proof: The existence of an optimal cell association Qm can
be veriﬁed by the existence of an OT mapping [3]. There exist
two cells Qi and Qr and a point q0 = (x0,y 0,z 0) ∈ Qi. Let
Oχ(q0) be a ball centered at q0 with radius χ> 0. Generate
the following new three-dimensional partition ~Qm, which can
be denoted as
~Qi = Ql/Oχ(q0),
~Qr = Qr ∪ Oχ(q0),
~Qm = Qm,m ⁄=i,r. (16)
The set Qm is the optimal cellular association. Therefore,
the optimal cell association obtained from ~Qm will not be
better than that obtained from Qm. It can be obtained as∫
Qi[z(Ui) −z(Ui −Uχ)]GTOLf (q)dq
+
∫
Oχ(q0)z(Ui −Uχ)GTOLf (q)dq
≤
∫
Qr [z(Ur +Uχ) −z(Ur)]GTOLf (q)dq
+
∫
Oχ(q0)z(Ur +Uχ)GTOLf (q)dq (17)
Multiplying 1Uχ on both sides of (17). Then, we takethe limit when χ → 0, and it can be calculated to obtain
Uχ =K
∫
Qχf (q)dq,z′(Ui) = dz(t)dt ⏐⏐t=Ui = − 1U 2i ,z′(Ur) =dz(t)
dt
⏐⏐t=Ur = − 1U 2r . We can get
− 1UiGTOL (q0) + GTOL (x,y,z )UiK
≤ − 1UrGTOL (q0) + GTOL (x,y,z )UrK . (18)
The optimal cell association for the m-th ground base station
can be expressed as
Q∗m = {(x,y,z )⏐⏐⏐− 1UiGTOL (x,y,z ) + GT OL(x,y,z)UiK
≤ − 1UrGTOL (x,y,z ) + GT OL(x,y,z)UrK , ∀i ⁄=m}.
(19)
which completes the proof of Theorem 1.
Based on the conclusion of Theorem 1, an iterative algo-
rithm based on [17] is proposed, as shown in Algorithm 1,
where ℜ
(t1 )
m (q) denotes the predeﬁned parameters used for cell
partitioning.
Algorithm 1 The iterative algorithm for searching for optimal
cell associations
Input: f (x,y,z ), T1, K, Bm(n)
Output: Q∗m,m ∈M
Initialization: t1 = 1 , generate initial cell associations
Q(t1)m , ℜ(t1 )m (q) = 0, q = (x,y,z ), ∀m ∈ {1, · · ·,M }
1: while t1 <T 1 do
2: Computing
ℜ(t1+1)m (q) =
{
[1 − 1/t1]ℜ(t1)m (q),if (q) ∈ Q(t1)m
1 − [1 − 1/t1][1 − ℜ(t1)m (q)],otherwise
3: Computing Um =
∫
Q(1 − ℜ(t1)m (q))f (x,y,z )dxdydz
4: t →t + 1
5: Updating cell associations by (15)
6: end while
B. Transmitting Power Design
For the given cell association, the transmit power optimiza -
tion subproblem can be expressed as
P4 : min
Pc,Ps
− GTOL
s.t. C 3,C 4,C 5,C 6. (20)
P4 involves ﬁnding the OT scheme with optimal transmit
power. The source distribution is the transmit power alloca ted
by the base station, the destination distribution is the pow er
received by the UA V and the transmission cost is the negative
of the objective function [18].
According to the Monge-Kantorovich problem [16], P4 can
be rewritten as
max
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
log2
(
1+ak,m
pk,mc λ2⏐⏐ˆαHk wk⏐⏐2
16π2N0(ˆdk,m + ∆dk,m)
)
·ϑ1bk,mdPc
+
∫ 1
K + 1
K+1∑
j=1
[(
̟1
bj
β1
+̟2
1
β2
)(
pj,ms |ςj|2
)]
dPs
s.t.ψ(Pc)= 1K
K∑
k=1
log2
(
1+ak,m
pk,mc λ2⏐⏐ˆαHk wk⏐⏐2
16π2N0(ˆdk,m + ∆dk,m)
)
,
Ω(Pc) = 1K
K∑
k=1
ϑ1bk,m,
φ(Ps) = 1K + 1
K+1∑
j=1
(
pj,ms |ςj|2
)
,
℧(Ps) = 1K + 1
K+1∑
j=1
(
̟1
bj
β1
+̟2
1
β2
)
. (21)
To maximize GTOL , ψ and φ must be maximized within
the expected range. Since it is necessary for any Pc ∈ D1
and Ps ∈V1 to satisfy ψ(Pc) +φ(Ps) ≤ −ϑ1 1KRsum − (1 −
ϑ1) 1K+1ϑ2ρsum, after determining ψ,φ can be represented as
φ(Ps) = ψ(Pc) = inf {−GTOL (Pc, Ps)} −ψ(Pc), (22)

where inf represents the inﬁmum of the function.
φ(Ps) can be simpliﬁed as
max
ψ,φ
F (φ) = max
ϕ,φ
∫
ψ(Pc)Ω(Pc)dPc +
∫
φ(Ps)(Ps)dPs,
(23)
where F (φ) is the function name. Solving the optimization
problem of (23) will result in a set of φ, by which the optimal
power allocation scheme Pis can be obtained. Calculating the
ﬁrst-order derivative can solve the optimization problem ( 23)
using the gradient descent method. It can be expressed as
∇F (φ) = ∂F (φ)∂φi
=
∫
Ω(Pc)dPc +
∫
(Ps)dPs
= 1K
K∑
k=1
ϑ1bk,mpk,mc
+ 1K + 1
K+1∑
j=1
(
̟1
bj
β1
+̟2
1
β2
)
pj,ms . (24)
Therefore, the power allocation algorithm based on OT is
shown in Algorithm 2 .
Algorithm 2 The power allocation algorithm based on OT
Input: ϑ1, ϑ2, ψ(Pc),φ (Ps) ∈D, Ω(Pc), (Ps) ∈V
Output: P ∗c = Pt2c , P ∗s = Pt2s
Initialization: t2 = 1, φt
1: while ‖∇F (φt)‖2 ≥ϑ2 do
2: n = 1, m1 = 1
3: Updating φt+1 =φt +m∇F (φt)
4: if ∇F (φt)< ∇F (φt+1) then
5: while ∇F (φt)< ∇F (φt+1) do
6: n →n + 1, mn = 2n−1m1
7: Updating φt+1 =φt +mn∇F (φt)
8: end while
9: else
10: while ∇F (φt)> ∇F (φt+1) do
11: n →n + 1, mn = 2n−1m1
12: Updating φt+1 =φt +mn∇F (φt)
13: end while
14: end if
15: t →t + 1
16: end while
C. The alternating iteration algorithm based on OT
AIBOT alternately solves P3 and P4 by Algorithm 1 and
Algorithm 2 to solve P1, respectively, as shown in Algorithm
3.
IV. N UMERICAL RESULTS
This section analyzes the effectiveness of AIBOT in ISAC-
enabled multi-UA V cooperative scenarios through simulati on.
The parameter settings are shown in Table I [10]–[12]. To
verify the effectiveness of the alternating iteration algo rithm
Algorithm 3 The alternating iteration algorithm based on OT
Input: T3
Output: Q∗ = Qt3, P ∗c = Pt3c , P ∗s = Pt3s
Initialization: t3 = 1
1: while t3 <T 3 do
2: n = 1, m1 = 1
3: Given the transmit power, solve P3 by Algorithm 1
4: Given cell association, solve P4 by Algorithm 2
5: end while
TABLE I
PARAMETERS SETTING
Parameter Value Parameter Value
fc 30 GHz N0 −169 dBm/Hz
pmin, pmax 0, 40 dBm β0 −50 dBW
M 6 K 18
based on the OT, we use the Weighted V oronoi diagram [3] and
the Iterative Water-ﬁlling algorithm as comparison algori thms.
The relationship between the system objective function and
the number of iterations is shown in Fig. 2. As iterations
increase, the objective function rises and stabilizes afte r the
3rd iteration. Compared to the Weighted V oronoi diagram
and Iterative Water-ﬁlling algorithm, AIBOT improves the
objective function by nearly 0.116. This improvement is due to
solving the mixed-integer nonconvex problem without relax ing
discrete variables, thus avoiding accuracy errors. Additi onally,
OT’s advantage lies in handling mixed integer planning prob -
lems by mapping continuous probability density functions t o
discrete measures in semi-discrete OT problems.
The relationship between the non-cooperative UA V local-
ization CRB and the number of iterations is given in Fig. 3.
It can be observed that the non-cooperative UA V localizatio n
CRB gradually decreases with the increase of the number of
iterations and gradually stabilizes after the 3rd iteratio n. It can
be demonstrated that the AIBOT can improve the localization
CRB by almost 29%. Therefore, the proposed algorithm can
achieve high localization QoS for the non-cooperative UA V .
The average sum rate comparison of different algorithms
converging in the ISAC-enabled multi-UA V network with dif-
ferent communication rate threshold requirements is illus trated
Fig. 2. The system objective function versus different numb er of iterations.

Fig. 3. The CRB for non-cooperative UA V localization versusdifferent number
of iterations.
Fig. 4. The localization CRB of UA V versus the threshold of th e communi-
cation sum rate.
in Fig. 4. It can be seen that the average sum rate of the system
continues to decrease as the communication rate threshold
increases. This trend occurs because the total power and
channel resources of the ground dual-functional base stati on
are ﬁnite. When the demand for sensing increases, the ground
dual-functional base station must allocate some of its reso urces
to meet the sensing requirements, consequently reducing th e
resources available for communication and leading to an
increase in the localization CRB of the UA V .
V. C ONCLUSIONS
This paper studies the resource allocation problem for
cooperative communication with non-cooperative localiza tion
in ISAC-enabled multi-UA V cooperative networks. The rela-
tionship between localization QoS and sum rate is revealed.
The objective of maximizing the weighted sum of the system
average sum rate and localization QoS is achieved by jointly
optimizing the cell association, communication power allo ca-
tion and sensing power allocation. We propose the AIBOT
to solve the mixed-integer nonconvex problem. Simulation
results demonstrate that the proposed AIBOT can achieve
high-rate communication and high-accuracy localization i n
ISAC-enabled multi-UA V networks.
REFERENCES
[1] W. Lin, L. Li, J. Y uan, Z. Han, M. Juntti, and T. Matsumoto, “Co-
operative lossy communications in unmanned aerial vehicle networks:
Age-of-information with outage probability,” IEEE Trans. V eh. Technol.,
vol. 70, no. 10, pp. 10 105–10 120, Oct. 2021.
[2] Y . Chen, W. Cheng, and W. Zhang, “Reconﬁgurable intellig ent surface
equipped UA V in emergency wireless communications: A new fa d-
ing–shadowing model and performance analysis,” IEEE Trans. Com-
mun., vol. 72, no. 3, pp. 1821–1834, Nov. 2024.
[3] M. Mozaffari, A. Taleb Zadeh Kasgari, W. Saad, M. Bennis, and
M. Debbah, “Beyond 5G with UA Vs: Foundations of a 3D wireless
cellular network,” IEEE Trans. Wireless Commun. , vol. 18, no. 1, pp.
357–372, 2019.
[4] W. Lin, L. Li, Y . Liu, Y . He, and Y . Liu, “Timeliness optimi zation of
unmanned aerial vehicle lossy communications for Internet -of-Things,”
Chin. J. Aeronaut. , vol. 36, no. 6, pp. 249–255, Jun. 2023.
[5] W. Lin, Y . Y an, L. Li, Z. Han, and T. Matsumoto, “Semantic- forward
relaying: A novel framework toward 6G cooperative communic ations,”
IEEE Commun. Lett. , vol. 28, no. 3, pp. 518–522, Mar. 2024.
[6] Y . Fu, W. Cheng, W. Zhang, and J. Wang, “Scalable extracti on based
semantic communication for 6G wireless networks,” IEEE Commun.
Mag., vol. 62, no. 7, pp. 96–102, 2024.
[7] W. Lin, Y . Y an, L. Li, Z. Han, and T. Matsumoto, “SemantIC: Semantic
interference cancellation toward 6G wireless communicati ons,” IEEE
Commun. Lett. , vol. 28, no. 8, pp. 1810–1814, Aug. 2024.
[8] M. Mozaffari, W. Saad, M. Bennis, Y .-H. Nam, and M. Debbah , “A
tutorial on UA Vs for wireless networks: Applications, chal lenges, and
open problems,” IEEE Commun. Surveys & Tuts. , vol. 21, no. 3, pp.
2334–2360, 2019.
[9] Y . Xiao, Q. Du, W. Cheng, and N. Lu, “Secure communication guar-
antees for diverse extended-reality applications: A uniﬁe d statistical
security model,” IEEE J. Sel. Topics Signal Process. , vol. 17, no. 5,
pp. 1007–1021, 2023.
[10] X. Liu, Y . Liu, Z. Liu, and T. S. Durrani, “Fair integrate d sensing and
communication for multi-UA V-enabled Internet of Things: J oint 3-D
trajectory and resource optimization,” IEEE Internet Things J. , vol. 11,
no. 18, pp. 29 546–29 556, 2024.
[11] Y . Cao and Q.-Y . Y u, “Joint resource allocation for user -centric cell-free
integrated sensing and communication systems,” IEEE Commun. Lett. ,
vol. 27, no. 9, pp. 2338–2342, 2023.
[12] Y . Liu, S. Liu, X. Liu, Z. Liu, and T. S. Durrani, “Sensing fairness-based
energy efﬁciency optimization for UA V enabled integrated s ensing and
communication,” IEEE Wireless Commun. Letters , vol. 12, no. 10, pp.
1702–1706, 2023.
[13] Y . Xiao, Q. Du, W. Cheng, and W. Zhang, “Adaptive samplin g and
transmission for minimizing age of information in metavers e,” IEEE J.
Sel. Areas Commun. , vol. 42, no. 3, pp. 588–602, 2024.
[14] Y . Xiao, Q. Du, Y . Zhang, and C. Lu, “Secure vehicular com munications
with varying QoS and environments: A uniﬁed cross-layer pol icy-
adaptation approach,” IEEE Trans. Intell. Transp. Syst. , vol. 24, no. 11,
pp. 13 462–13 471, Nov. 2023.
[15] J. Sun, S. Ma, R. Y ang, Y . Tingting, and S. Li, “Robust pow er
allocation for UA V-aided ISAC systems with uncertain locat ion sensing
errors,” 2023. [Online]. Available: https://arxiv.org/a bs/2305.04423
[16] F. Dong, F. Liu, Y . Cui, W. Wang, K. Han, and Z. Wang, “Sens ing as
a service in 6G perceptive networks: A uniﬁed framework for I SAC
resource allocation,” IEEE Trans. Wireless Commun. , vol. 22, no. 5, pp.
3522–3536, 2023.
[17] G. Crippa, C. Jimenez, and A. Pratelli, “Optimum and equ ilibrium in a
transport problem with queue penalization effect,” Advances in Calculus
of V ariations, vol. 2, no. 3, pp. 207–246, 2009.
[18] D. Gan, X. Ge, and Q. Li, “An optimal transport-based fed erated
reinforcement learning approach for resource allocation i n cloud–edge
collaborative IoT,” IEEE Internet Things J. , vol. 11, no. 2, pp. 2407–
2419, 2024.