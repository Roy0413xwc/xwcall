---
title: "Channel Knowledge Map Enabled Low-Altitude ISAC Networks Joint Air Corridor Planning and Base Station Deployment"
zotero_key: "JUTU2WE6"
pdf_key: "1A1B49FC"
collection: "ISAC"
source: "Open-access PDF (arXiv, pypdf extraction)"
page_mapping: unverified
---

# Channel Knowledge Map Enabled Low-Altitude ISAC Networks Joint Air Corridor Planning and Base Station Deployment — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
Channel Knowledge Map Enabled Low-Altitude
ISAC Networks: Joint Air Corridor Planning and
Base Station Deployment
Jiaxuan Li, Yilong Chen, Fan Liu, Senior Member , IEEE, and Jie Xu, Fellow, IEEE
Abstract—This letter addresses the joint air corridor planning
and base station (BS) deployment problem for low-altitude
integrated sensing and communication (ISAC) networks. In t he
considered system, unmanned aerial vehicles (UA Vs) operat e
within a structured air corridor composed of connected cubi c
segments, and multiple BSs need to be selectively deployed a t a set
of candidate locations to ensure both sensing and communica tion
coverage throughout the corridor . In particular , we levera ge the
channel knowledge map (CKM) to characterize wireless chann els
for candidate BS sites prior to deployment, thereby facilit ating
the ofﬂine planning. Under this setup, we minimize the syste m
cost in terms of the weighted sum of the air corridor length
and the number of deployed BSs, subject to the constraints
on both sensing and communication performance across the
corridor . To solve the formulated large-scale nonconvex in teger
programming problem, we develop a hierarchical coarse-to- ﬁne
grid decomposition algorithm. Simulation results demonst rate
the beneﬁt of the proposed joint design in reducing the overa ll
deployment cost while ensuring the coverage of the low-alti tude
ISAC networks.
Index Terms—Low-altitude wireless network, integrated sens-
ing and communication (ISAC), channel knowledge map (CKM),
air corridor planning, base station (BS) deployment.
I. I NTRODUCTION
Low-altitude economy (LAE) leverages unmanned aerial
vehicles (UA Vs) and electric vertical takeoff and landing
(eVTOL) aircraft for urban air mobility and cargo delivery. Air
corridors and integrated sensing and communication (ISAC)
have emerged as two promising techniques to ensure the safe
and reliable operations of UA Vs and eVTOLs. On the one
hand, air corridors provide structured routing to deconﬂic t
trafﬁc and simplify airspace management [1]. On the other
hand, ISAC networks enable simultaneous sensing and com-
munication within air corridors, supporting real-time tra cking,
navigation, and reliable control of UA Vs and eVTOLs [2]. As
such, the integration of air corridors and ISAC is crucial fo r
scalable and safe LAE.
In the literature, there have been various prior works in-
vestigating air corridors [3], [4] and ISAC networks [5]–[7 ]
for LAE separately. First, the authors in [3], [4] studied th e
design of geometric conﬁgurations (e.g., cubic or cylindri cal
segments) of air corridors and the corresponding routing st rate-
gies, with the objective of maximizing the trafﬁc throughpu t
J. Li, Y . Chen, and J. Xu are with the School of Science and En-
gineering (SSE), the Shenzhen Future Network of Intelligen ce Institute
(FNii-Shenzhen), and the Guangdong Provincial Key Laborat ory of Future
Networks of Intelligence, The Chinese University of Hong Ko ng (Shen-
zhen), Guangdong, 518172, China (e-mail: jiaxuanli4@link .cuhk.edu.cn; yi-
longchen@link.cuhk.edu.cn; xujie@cuhk.edu.cn).
F. Liu is with the National Mobile Communications Research L aboratory,
School of Information Science and Engineering, Southeast U niversity, Nanjing
210096, China (e-mail: f.liu@ieee.org).
F. Liu is the corresponding author.
while ensuring collision-free operations. Next, various p rior
works (e.g., [5]–[7]) exploited on-ground ISAC networks to
support low-altitude UA V operations via ground-based cellular
infrastructure. For example, the authors in [7] utilized th e
cooperative transmit beamforming at multiple on-ground ba se
stations (BSs) to support the communication and localizati on
of cooperative UA Vs and monitor the low-altitude airspace t o
prevent the invasion of unauthorized ﬂight objects. Despit e
these advances, the joint optimization of air corridor plan ning
and ISAC network deployment remains an open problem,
which motivates this work.
Speciﬁcally, we study joint design of air corridors and low-
altitude ISAC networks, for providing seamless sensing and
communication coverage throughout air corridors. In this c on-
text, obtaining channel state information (CSI) with poten tial
BS sites is particularly challenging due to the lack of prior
measurements. Channel knowledge map (CKM) has emerged
as a promising solution, which establishes a functional map -
ping from transceiver locations to the corresponding chann el
knowledge. In practice, CKM can be effectively constructed
based on physical environment knowledge and limited channe l
measurements [8]–[10], providing CSI a priori to facilitate
network deployment and operation [11], [12]. However, how t o
exploit CKM to facilitate the joint optimization of air corr idor
planning and BS deployment has not been studied in the
literature yet.
This letter studies the CKM-enabled joint air corridor
planning and BS deployment problem for low-altitude ISAC
networks at the planning stage, providing a stable upper-la yer
infrastructure and corridor layout that can be further adap ted
in operation to dynamic urban environments. To be speciﬁc,
we model the air corridor as a sequence of connected cubes
with a ﬁxed edge length located at a ﬁxed altitude, and we
need to selectively deploy multiple BSs at a set of candidate
locations to provide communication and sensing coverage
across the corridor. For each candidate BS site, we utilize
the CKM to predict the CSI and evaluate the communication
and sensing coverage performance, thereby enabling ofﬂine
optimization. Under this setup, we aim to minimize the syste m
cost in terms of the weighted sum of the air corridor length
and the number of deployed BSs, subject to the sensing and
communication coverage requirements throughout the corri dor.
We propose a hierarchical coarse-to-ﬁne grid decompositio n
algorithm to solve the formulated large-scale nonconvex in te-
ger programming problem. In the coarse layer, we reformulat e
the problem as a linear integer program to obtain a feasible
air corridor and BS deployment solution. In the ﬁne layer,
we use an alternating optimization (AO) procedure to reﬁne
arXiv:2512.02464v2  [eess.SP]  12 Dec 2025

2
the coarse layer solution for further reducing the system co st.
Simulation results demonstrate that the proposed algorith m
achieves shorter air corridor lengths and requires fewer BS s
to fulﬁll the LAE tasks, thereby signiﬁcantly reducing syst em
costs compared with various baseline methods.
II. S YSTEM MODEL AND PROBLEM FORMULATION
Fig. 1. System model.
We consider an ISAC network for LAE as illustrated in Fig.
1, in which potential UA Vs pass through an urban area from
a departure point to a destination point within a dedicated a ir
corridor (to be designed) to fulﬁll various tasks such as urb an
air mobility and cargo delivery. To ensure reliable communi -
cation and real-time sensing for UA Vs, multiple ground BSs
are selectively deployed at a set of candidate locations on t he
ground to support these services throughout the corridor.
A. Air Corridor Model
An air corridor is a three-dimensional (3D) volume of
airspace reserved for UA V and eVTOL operations [3]. In
this work, we consider a corridor at a ﬁxed-altitude H.1 The
vertical takeoff and landing zones are assumed to lie direct ly
beneath the departure and destination points. Under these
conditions, our objective is to design an air corridor that s afely
accommodates ﬂights within the prescribed airspace.
As shown in Fig. 1, we adopt a discretized grid map with
Cartesian coordinates, and the air corridor is modeled as a
sequence of uniformly sized cubes connected face to face to
form a continuous path [3]. The grid consists of an N × N
3D rectangular region at a constant altitude H, indexed by
{Ri,j | i, j ∈ N } , N ≜ {1, 2, . . . , N}, with the origin at
(xO, yO, H). The geographical coverage of each grid cell Ri,j
is deﬁned as
Ri,j =
[
xO + (i − 1) ∆x, x O + i ∆x]
×
[
yO + (j − 1) ∆y, y O + j ∆y] × [H, H + ∆z],
(1)
where ∆x, ∆y, and ∆z denote the grid resolutions along the
x-, y-, and z-axes, respectively.
Furthermore, let A denote an N ×N binary indicator matrix,
with Ai,j = 1 if Ri,j is included in the air corridor, and
Ai,j = 0 otherwise. Without loss of generality, we designate
R1,1 and RN,N as the departure and destination points of the
corridor, respectively. We thus have
A1,1 = 1, A N,N = 1. (2)
Note that in order for the air corridor to be feasible,
a necessary condition is that the corridor should form a
continuous path, meaning that all active cells with Ai,j = 1
1The considered system can also be viewed as one representati ve air
corridor among multiple corridors in a multi-layer air corr idor architecture.
must be connected. This is equivalent to the condition that
each active cell (i, j) with Ai,j = 1 should have at least
two active adjacent grid along the x- or y-axis. Moreover,
to avoid unnecessary branching, each active cell is restric ted
to have at most two active neighbors. To this end, for each
grid (i, j), we deﬁne the set of four neighboring grid cells as
N4(i, j) ≜ {(i′, j′) ∈ N × N : |i′ − i| + |j′ − j| = 1 }.
Accordingly, the connectivity constraints are expressed a s
2Ai,j ≤
∑
(i′,j′)∈N4(i,j) Ai′,j′ ≤ 2. (3)
Additionally, to guarantee reachability, there must exist at
least one active grid in each row and column between the
departure point and the destination point. We have∑N
i=1
Ai,j ≥ 1, ∀j ∈ N ,
∑N
j=1
Ai,j ≥ 1, ∀i ∈ N .
(4)
B. Sensing and Communication Models
Suppose that there are K candidate BS sites with indices
K ≜ {1, · · · , K}. Let qk = ( qk,x, qk,y, qk,z ) denote the
location of site k, k ∈ K . We introduce a binary vector δ =
(δ1, · · · , δK) to indicate the deployment status of candidate
sites, where δk = 1 if a BS is deployed at candidate site k
and δk = 0 otherwise.
To characterize the sensing and communication coverage
throughout the air corridor, we need to acquire CSI from each
candidate BS site to any point within the air corridor. Howev er,
acquiring such measurements at a dense set of locations is
typically impractical, especially when the BS has not been
properly deployed. To address this, we exploit the CKM to
obtain channel power gains. In practice, we can ﬁrst obtain t he
3D environmental model of the considered region, and then
utilize the ray tracing technique to construct the channel g ain
map [13]. 2 It is assumed that for each candidate BS site, we
use the CKM to obtain the mapping from a 3D user location
{p = (qx, qy, qz)} to the corresponding channel power gain at
that BS site. Let hk(p) denote the channel power gain between
BS site k ∈ K and location p, which in general is a discrete
function without a closed-form expression. In particular, for
the rectangular region Ri,j associated with Ai,j , i, j ∈ N , the
set of sampled channel power gains from BS site k, k ∈ K
within Ri,j is
Gk,i,j =
{
hk(p) | p ∈ R i,j
}
. (5)
For communication, by leveraging the CKM, we evaluate
the received signal-to-interference-plus-noise ratio (S INR) at
sample positions p as the communication performance metric.
By considering that the receiver is deployed with a single
antenna, the SINR of the arrival signal at location p from
BS k is given by
γk,i,j (p, δ) = P δ kGhk(p)∑
b∈K\k δb P hb(p) + σ2 , (6)
where P is the transmit power of each BS, G > 1 is a co-
efﬁcient capturing the transmit antenna gain and the potent ial
transmit beamforming gain, and σ2 is the noise power at the
receiver. To ensure the coverage within each grid cell (i, j), we
2The accuracy of ray tracing process highly depends on the acc uracy of the
3D environment model. In order to focus our study on the netwo rk deployment
design, we assume that the CKM is perfectly known a priori and leave the
CKM construction and the analysis of inaccurate CKM for futu re work.

3
take the worst-case SINR over all sampling points within thi s
cell as the communication performance metric. Speciﬁcally ,
for all points within Ri,j, we deﬁne hmink,i,j ≜ min (Gk,i,j ) and
hmaxk,i,j ≜ max (Gk,i,j ) as the minimum and maximum channel
power gains from BS site k, respectively. Accordingly, the
worst-case SINR is given by
γk,i,j (δ) ≜
P Gδkhmink,i,j∑
b∈K\k δbP hmaxb,i,j + σ2 . (7)
In addition, we consider the line-of-sight (LoS) sensing
to localize aircraft within the air corridor for navigation and
surveillance. To this end, at least three LoS paths are neede d,
and the total received echo signal power from LoS paths
should exceed a certain threshold [15]. We deﬁne an indicato r
Lk,i,j , where Lk,i,j = 1 if there exists a LoS link between
BS site k and location p ∈ R i,j , and Lk,i,j = 0 otherwise.
Assuming a monostatic LoS sensing model, we consider the
minimum echo signal power over Ri,j from BS site k as the
sensing performance metric, which is given by [14]
pk,i,j ≜ minp∈Ri,j
Lk,i,j P Gλ2σRCS
(4π)3d4k(p) , (8)
where dk(p) ≜ ‖qk − p‖2 is the distance between BS site k
and location p ∈ Ri,j , λ is the wavelength, and σRCS denotes
the radar cross section of potential UA V .
C. Problem F ormulation
In this work, we aim to minimize the system cost in terms
of the weighted sum of the air corridor length and the number
of deployed BSs, subject to the path connectivity, SINR,
LoS visibility, and sensing power constraints. The problem
is formulated as
(P1) : min
A,δ
α11⊤A1 + α2 ∑Kk=1 δk,
s.t.
∑K
k=1
δkpk,i,j ≥ ǫ1Ai,j, ∀i, j ∈ N , (9a)
∑K
k=1
δkLk,i,j ≥ 3Ai,j, ∀i, j ∈ N , (9b)
maxk∈K γk,i,j (δ) ≥ ǫ2Ai,j , ∀i, j ∈ N , (9c)
δk ∈ {0, 1}, Ai,j ∈ {0, 1}, ∀k ∈ K, i, j ∈ N , (9d)
(2) − (4),
where α1 ≥ 0 and α2 ≥ 0 are weighting coefﬁcients
determined by the economics and policy constraints of the
target low-altitude network with α1 + α2 = 1 , and 1 ∈ RN
denotes the all-ones vector, with 1⊤ being its transpose. For
any corridor cell (i, j) (i.e., Ai,j = 1), the constraints in (9a)
and (9c) ensure received sensing power and communication
SINR no less than the corresponding thresholds ǫ1 and ǫ2, re-
spectively, while the constraint in (9b) guarantees the vis ibility
from at least three LoS BSs.
Problem (P1) is an integer nonconvex program with hard
integrality constraints that is inherently difﬁcult to sol ve using
relaxation-based methods. Note that the decision space con -
sists of N 2 + K binary variables. Consequently, in practical
settings with ﬁne spatial resolution, (P1) becomes a large- scale
problem, signiﬁcantly increasing computational complexi ty.
III. P ROPOSED SOLUTION TO PROBLEM (P1)
In this section, we eliminate the nonconvex constraint in
(9c), yielding a linear integer program. Despite this refor mu-
lation, the problem still remains computationally demandi ng
due to its scale and integrality. To address this, we adopt a
coarse-to-ﬁne hierarchical framework that ﬁrst obtains a j ointly
optimized coarse-resolution path and BS deployment, and th en
reﬁnes the solution at the ﬁne layer to improve spatial cover age
with reduced BS deployment overhead.
A. Joint Optimization over Coarse Grids
At the coarse layer, the original N × N map A is coarsened
to an M × M grid B, with index set M ≜ {1, . . . , M}.
Each coarse cell Ba,b, a, b ∈ M represents a rectangular
region ˜Ra,b with spatial resolutions ˜∆x, ˜∆y, and ∆z. Let δB
denote the associated BS deployment vector. For each (a, b),
we evaluate the cell SINR ˜γk,a,b(δB) according to (7), by
using the minimum and maximum channel power gains ˜hmink,a,b
and ˜hmaxk,a,b based on the sample set ˜Gk,a,b within ˜Ra,b. To
suppress outliers in each coarse cell, we discard the lowest
10% and the highest 10 % of the samples in ˜Gk,a,b and compute
˜hmink,a,b and ˜hmaxk,a,b on the remainder. We also deﬁne ˜Lk,a,b and
˜pk,a,b in this layer, following the same form as in Section II-B.
We address the joint optimization problem (P1) at the
re-partitioned coarse layer, with the newly deﬁned indicat or
matrix B and deployment indicator vector δB. Firstly, to
eliminate the max operator in (9c), we apply a Big- M re-
formulation [16]. Speciﬁcally, we introduce binary auxili ary
variables {zk,a,b ∈ { 0, 1}|a, b ∈ M , k ∈ K} to indicate
whether BS site k satisﬁes the SINR threshold at cell (a, b).
Then, for each coarse cell (a, b), a, b ∈ M , the constraint
maxk∈K ˜γk,a,b(δB) ≥ ǫ2Ba,b is equivalently enforced by
(1 − zk,a,b)ζ ≥ ǫ2 Ba,b(P
∑
k′∈K\kδBk′ ˜hmaxk′,a,b + σ2)
− P G δ Bk ˜hmink,a,b, (10a)
zk,a,b ≤ δBk , (10b)∑K
k=1
zk,a,b ≥ Ba,b, (10c)
zk,a,b ∈ {0, 1}. (10d)
Here, ζ > 0 is a sufﬁciently large constant (chosen larger
than an upper bound on the right-hand side of (10a)) used to
deactivate the SINR constraint in (10a) when zk,a,b = 0 , and
to activate the constraint when zk,a,b = 1 . (10b) prevents the
selection of an undeployed BS, and (10c) ensures that at leas t
one deployed BS satisﬁes the threshold whenever Ba,b = 1.
The constraint (10a) remains nonconvex because it contains
the bilinear products Ba,b δBk′ . Since all these variables are
binary, we introduce auxiliary binaries wk,a,b = Ba,b δBk for
all k ∈ K and a, b ∈ M . We enforce this identity wk,a,b =
Ba,b δBk through the standard McCormick linearization [17]:
wk,a,b ≤ δBk , (11a)
wk,a,b ≤ Ba,b, (11b)
wk,a,b ≥ δBk + Ba,b − 1, (11c)
wk,a,b ∈ {0, 1}. (11d)
This linearization guarantees that wk,a,b = 1 if and only if
both Ba,b = 1 and δBk = 1 , and wk,a,b = 0 otherwise. By
substituting wk′,a,b for Ba,bδBk′ , (10a) is rewritten as
(1 − zk,a,b)ζ ≥ ǫ2(P
∑
k′∈K\k
˜hmaxk′,a,b wk′,a,b + σ2Ba,b)
− P G δ Bk ˜hmink,a,b, ∀ k ∈ K, a, b ∈ M. (12)

4
After that, at coarse layer, problem (P1) is reformulated as
(P2) : min
B,δB
{zk,a,b,∀k∈K,a,b∈M}
{wk,a,b,∀k∈K,a,b∈M}
α11⊤B1 + α2 ∑Kk=1 δBk ,
s.t. 2Ba,b ≤
∑
(a′,b′)∈N4(a,b) Ba′b′ ≤ 2, ∀a, b ∈ M (13a)∑M
a=1
Ba,b ≥ 1, ∀b ∈ M,
∑M
b=1
Ba,b ≥ 1, ∀a ∈ M (13b)
B1,1 = 1, B M,M = 1, (13c)∑K
k=1
δBk ˜pk,a,b ≥ ǫ1Ba,b, ∀a, b ∈ M, (13d)∑K
k=1
δBk ˜Lk,a,b ≥ 3Ba,b, ∀a, b ∈ M, (13e)
δBk ∈ {0, 1}, Ba,b ∈ {0, 1}, ∀k ∈ K, a, b ∈ M (13f)
(10b) − (11d), (12).
The coarse layer formulation (P2) reduces the joint op-
timization problem to a linear integer program with KM 2
variables, compared to KN 2 in a direct ﬁne layer formulation
of (P1), where N ≫ M .
B. Alternative Reﬁnement of Air Corridor and BS Deployment
In the coarse layer, Ba,b = 1 indicates that the air corridor
passes through grid (a, b). Let B =
{
(a, b) | Ba,b = 1
}
denote
the set of selected coarse-grid cells obtained by solving (P 2).
For each (a, b) ∈ B , we deﬁne A(a,b) as the (N/M)×(N/M)
(assuming N is divisible by M ) submatrix of A for the region
covered by Ba,b, where each entry A(a,b)i,j , i, j ∈ N (a,b), pro-
vides the unit-cube resolution for ﬁnal planning. We optimi ze
the path within each A(a,b), (a, b) ∈ B and update the global
BS deployment δ based on A, which is assembled from all
A(a,b) via an AO framework.
First, we initialize the ﬁne layer deployment vector δ as the
coarse layer solution δB. Next, for each A(a,b), (a, b) ∈ B , we
predeﬁne its start and end points based on its adjacent coars e-
grid neighbors. For example, if Ba,b = 1 , B a−1,b = 1 , and
Ba,b+1 = 1 , then cell (a, b) is connected to both its southern
and eastern neighbors. We then set the midpoint of A(a,b)’s
southern edge as the start point A(a,b)sx,sy, and the midpoint of
its eastern edge as the destination point A(a,b)dx,dy. Fixing δ and
these end points, we solve the following subproblem (P3.1)
independently for each A(a,b), (a, b) ∈ B .
(P3.1) : min
A(a,b)
1⊤A(a,b)1,
s.t. 2A(a,b)i,j ≤∑
(i′,j′)∈N4(i,j)∩N (a,b)
A(a,b)i′,j′ ≤ 2, ∀i, j ∈ N (a,b), (14)
dx∑
i=sx
A(a,b)i,j ≥ 1, ∀j ∈ N (a,b),
dy∑
j=sy
A(a,b)i,j ≥ 1, ∀i ∈ N (a,b),
(15)
A(a,b)sx,sy = 1, A (a,b)dx,dy = 1, (16)∑K
k=1
δkp(a,b)k,i,j ≥ ǫ1A(a,b)i,j , ∀i, j ∈ N (a,b), (17)∑K
k=1
δkL(a,b)k,i,j ≥ 3A(a,b)i,j , ∀i, j ∈ N (a,b), (18)
maxk∈K γ(a,b)k,i,j ≥ ǫ2A(a,b)i,j , ∀i, j ∈ N (a,b), (19)
A(a,b)i,j ∈ {0, 1}, ∀i, j ∈ N (a,b), (20)
where p(a,b)k,i,j , L(a,b)k,i,j , and γ(a,b)k,i,j follow the deﬁnitions in Section
II-B and are evaluated within ˜Ra,b at the ﬁne layer resolution.
Fig. 2. The considered area (from the OpenStreetMap databas e) and the spatial
distribution of candidate BS sites.
Note that A(1,1)1,1 and A(M,M )N/M,N/M have only one active adjacent
neighbor.
Once all A(a,b), (a, b) ∈ B have been updated, the global
ﬁne layer map A is reconstructed by assembling the submatri-
ces. Subsequently, we solve problem (P3.2) to update δ based
on the obtained A.
(P3.2) : min
δ
∑K
k=1
δk,
∑K
k=1
δkpk,i,j ≥ ǫ1Ai,j , ∀i, j ∈ N , (21a)
∑K
k=1
δkLk,i,j ≥ 3Ai,j, ∀i, j ∈ N , (21b)
maxk∈K γk,i,j ≥ ǫ2Ai,j , ∀i, j ∈ N , (21c)
δk ∈ {0, 1}, ∀k ∈ K. (21d)
Both (P3.1) and (P3.2) are linear integer programs. Since
each AO step leads to monotonically non-increasing system
cost (i.e., the air corridor length or the number of deployed
BSs), and both objectives are bounded below, the algorithm i s
guaranteed to converge [18].
IV. N UMERICAL RESULTS
This section presents numerical results to evaluate the
performance of our proposed algorithms. We consider a 500
m×500 m area in Futian District, Shenzhen, China, with
K = 30 candidate BSs, as shown in Fig. 2. We use the open-
source library Sionna RT (v0.18.0) to generate CKMs [13].
The carrier frequency is set to be 1 GHz, the noise power at
the UA V receiver is σ2 = −110 dBm, and the transmit power
of each BS is P = 30 dBm. We set the transmit gain of each
BS to G = 12 dB and the radar cross section to σRCS = 1 m2.
The altitude of air corridor is set as H = 150 m, and the BS
height is set as 25 m.
In the coarse layer, the map is divided into 10 × 10 grids,
with each grid measuring 50 m × 50 m. For problem (P2),
we set the weights as α1 = 0.5 and α2 = 0.5, and choose the
Big-M constant ζ = 10 −8. In the ﬁne layer, the map is divided
into 100×100 grids, each with resolution ∆x = ∆ y = ∆z = 5
m, which is consistent with the size of the air corridor cube. 3
The received sensing power threshold is ǫ1 = −75 dBm, and
the SINR threshold is ǫ2 = 3 dB.
We consider the following two benchmark schemes for
comparison:
• A*-based sequential planning : We ﬁrst compute the
shortest path via A* [20] and then, conditioning on this
path, solve problem (P3.2) to obtain the BS deployment
subject to the communication and sensing constraints.
• Random BS deployment : We randomly deploy BSs at
the K candidate sites with the number of deployed BSs
3We target small-UA V corridors (max dimension < 2 m [19]) and adopt a
5 m grid, sufﬁcient for single-UA V operation.

5
increasing from 1 to K, and solve problem (P3.1) with
given δ until a feasible shortest path solution is obtained.
Fig. 3 illustrates the jointly optimized coarse-layer air
corridor, BS deployment, and the received sensing power. It is
observed that the cells traversed by the corridor satisfy bo th
thresholds, and the length is minimized. On a 10 × 10 grid,
our method yields a shortest path traversing 19 cells (50 m
per cell) with 8 deployed BSs. Furthermore, Fig. 4 presents
the ﬁne-layer corridors and BS deployment after iterative
optimizations, with each ﬁne cell according to the SINR. On
a 100 × 100 grid, our method yields a shortest path traversing
199 cells (5 m per cell) with 7 deployed BSs.
Fig. 3. Coarse-layer air corridor over-
laid on the sensing power map.
Fig. 4. Fine-layer air corridor overlaid
on the SINR map.
Fig. 5 shows the number of deployed BSs versus the
minimum received sensing power threshold ǫ1 (with ǫ2 = 3
dB), and Fig. 6 shows the length versus the minimum SINR
threshold ǫ2 (with ǫ1 = −75 dBm) for our method and
two benchmarks. The results for the two benchmarks are
averaged over 100 random realizations. It is observed in Fig .
5 that the number of deployed BSs increases with ǫ1 for all
three schemes, whereas our approach consistently requires the
fewest BSs. It is observed in Fig. 6 that the length of both
our method and the random deployment baseline increases
with ǫ2, whereas that of the A* scheme remains unchanged.
Nevertheless, our approach consistently identiﬁes a feasi ble
path and yields the shortest length among all three schemes.
By contrast, the A* scheme fails to ﬁnd any feasible path once
ǫ2 exceeds 3.2 dB, and the random BS deployment baseline
fails beyond 3.8 dB, since under stringent SINR thresholds
and limited trial budget, these methods rarely identify a pa th
satisfying all constraints.
-80 -79 -78 -77 -76 -75 -74 -73 -72 -71 -70
Minimum sensing power 1 (dBm)
6
8
10
12
14
16
18The number of deployed BSs
Proposed design
Random BS deployment
A* search
Fig. 5. The number of deployed BSs
versus ǫ1.
2 2.2 2.4 2.6 2.8 3 3.2 3.4 3.6 3.8 4
Minimum SINR 2 (dB)
195
200
205
210
215
220
225
230The length of paths
Proposed design
Random BS deployment
A* search
Fig. 6. The length of air corridor
paths versus ǫ2.
V. C ONCLUSION
In this letter, we investigated the joint air corridor plan-
ning and BS deployment for low-altitude ISAC networks,
with the objective of minimizing the network cost under
both communication and sensing constraints. By leveraging
CKMs, we enabled ofﬂine evaluation of each candidate BS’s
performance without the need for real-time measurements. W e
proposed a coarse-to-ﬁne framework with an AO algorithm to
efﬁciently solve the formulated large-scale, nonconvex in teger
program. Simulation results show that the proposed method
signiﬁcantly reduces length and deployment cost compared t o
benchmark schemes, thereby demonstrating its effectivene ss
for cost-efﬁcient planning of low-altitude ISAC networks.
REFERENCES
[1] A. Bauranov and J. Rakas, “Designing airspace for urban a ir mobility:
A review of concepts and approaches,” Prog. Aerosp. Sci. , vol. 125,
p. 100726, 2021.
[2] F. Liu, Y . Cui, C. Masouros, J. Xu, T. X. Han, Y . C. Eldar, an d S. Buzzi,
“Integrated sensing and communications: Toward dual-func tional wire-
less networks for 6G and beyond,” IEEE J. Sel. Areas Commun. , vol. 40,
no. 6, pp. 1728–1767, Jun. 2022.
[3] S. I. Muna, S. Mukherjee, K. Namuduri, M. Compere, M. I. Ak bas,
P . Moln´ ar, and R. Subramanian, “Air corridors: Concept, de sign, simu-
lation, and rules of engagement,” Sensors, vol. 21, no. 22, Art. no. 7536,
2021.
[4] L. Y u, Z. Li, N. Ansari, and X. Sun, “Hybrid transformer ba sed
multi-agent reinforcement learning for multiple unpilote d aerial vehicle
coordination in air corridors,” IEEE Trans. Mobile Comput. , vol. 24,
no. 6, pp. 5482–5495, Jun. 2025.
[5] Y . Song, Y . Zeng, Y . Y ang, Z. Ren, G. Cheng, X. Xu, J. Xu, S. J in, and
R. Zhang, “An overview of cellular ISAC for low-altitude UA V : New
opportunities and challenges,” IEEE Commun. Mag. , pp. 1–8, 2025.
[6] Q. Wu, J. Xu, Y . Zeng, D. W. K. Ng, N. Al-Dhahir, R. Schober, and
A. L. Swindlehurst, “A comprehensive overview on 5G-and-be yond net-
works with UA Vs: From communications to sensing and intelli gence,”
IEEE J. Sel. Areas Commun. , vol. 39, no. 10, pp. 2912–2945, Oct. 2021.
[7] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for lo w-
altitude economy: Coordinated transmit beamforming and UA V trajec-
tory design,” IEEE Trans. Commun., vol. 73, no. 8, pp. 5832–5847, Aug.
2025.
[8] Y . Zeng, J. Chen, J. Xu, D. Wu, X. Xu, S. Jin, X. Gao, D. Gesbe rt, S. Cui,
and R. Zhang, “A tutorial on environment-aware communicati ons via
channel knowledge map for 6G,” IEEE Commun. Surveys Tuts. , vol. 26,
no. 3, pp. 1478–1519, 3rd Quart., 2024.
[9] B. Zhang and J. Chen, “Constructing Radio Maps for UA V Com mu-
nications via Dynamic Resolution Virtual Obstacle Maps,” i n Proc.
2020 IEEE 21st Int. W orkshop Signal Process. Adv. Wireless C ommun.
(SPAWC), Atlanta, GA, USA, May 2020, pp. 1–5.
[10] W. Liu and J. Chen, “UA V -Aided Radio Map Construction Ex ploiting
Environment Semantics,” IEEE Trans. Wireless Commun. , vol. 22, no.
9, pp. 6341-6355, Sep. 2023.
[11] Y . Zeng and X. Xu, “Toward environment-aware 6G communi cations
via channel knowledge map,” IEEE Wireless Commun. , vol. 28, no. 3,
pp. 84–91, Jun. 2021.
[12] H. Li, P . Li, G. Cheng, J. Xu, J. Chen, and Y . Zeng, “Channe l knowledge
map (CKM)-assisted multi-UA V wireless network: CKM constr uction
and UA V placement,” J. Commun. Inf. Netw. , vol. 8, no. 3, pp. 256–
270, Sep. 2023.
[13] J. Hoydis, F. A. Ait Aoudia, S. Cammerer, M. Nimier-Davi d, N. Binder,
G. Marcus, and A. Keller, “Sionna RT: Differentiable Ray Tra cing for
Radio Propagation Modeling,” in Proc. 2023 IEEE Globecom W orkshops
(GC Wkshps) , 2023, pp. 317–321.
[14] M. A. Richards, J. A. Scheer, and W. A. Holm, Principles of Modern
Radar: Basic Principles . Ann Arbor, MI, USA: IET Digital Library,
2010.
[15] S. Motie, H. Zayyani, M. Salman, and M. Bekrani, “Self UA V localiza-
tion using multiple base stations based on TDoA measurement s,” IEEE
Wireless Commun. Lett. , vol. 13, no. 9, pp. 2432–2436, Jun. 2024.
[16] M. S. Bazaraa, J. J. Jarvis, and H. D. Sherali, Linear Programming and
Network Flows . New Y ork, NY: Wiley, 1990.
[17] G. P . McCormick, “Computability of global solutions to factorable
nonconvex programs: Part I—Convex underestimating proble ms,” Math.
Program., vol. 10, no. 1, pp. 147–175, 1976.
[18] S. Boyd and L. V andenberghe, Convex Optimization. Cambridge, U.K.:
Cambridge Univ. Press, 2004.
[19] IEEE Standard for a Framework for Structuring Low-Altitude Airspace
for Unmanned Aerial V ehicle (UA V) Operations, Standard 1939.1-2021,
2021, pp. 1–94.
[20] P . E. Hart, N. J. Nilsson, and B. Raphael, “A Formal Basis for the
Heuristic Determination of Minimum Cost Paths,” IEEE Trans. Syst.
Sci. Cybern. , vol. 4, no. 2, pp. 100–107, 1968.