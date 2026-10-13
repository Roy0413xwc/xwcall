---
title: "Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Balancing"
zotero_key: "4IPDFAZ4"
pdf_key: "U2MIQPK8"
doi: "10.1109/tsp.2026.3694198"
collection: "ISAC"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Balancing — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

arXiv:2503.09489v1  [cs.IT]  12 Mar 2025
1
Optimal ISAC Beamforming Structure and Efﬁcient
Algorithms for Sum Rate and CRLB Balancing
Tianyu Fang, Student Member , IEEE, Mengyuan Ma, Student Member , IEEE, Markku Juntti, Fellow, IEEE, Nir
Shlezinger, Senior Member , IEEE, A. Lee Swindlehurst, Fellow, IEEE, and Nhan Thanh Nguyen, Member , IEEE
Abstract—Integrated sensing and communications (ISAC)
has emerged as a promising paradigm to unify wireless
communications and radar sensing, enabling efﬁcient spect rum
and hardware utilization. A core challenge with realizing t he
gains of ISAC stems from the unique challenges of dual purpos e
beamforming design due to the highly non-convex nature of ke y
performance metrics such as sum rate for communications and
the Cram ´er–Rao lower bound (CRLB) for sensing. In this paper ,
we propose a low-complexity structured approach to ISAC
beamforming optimization to simultaneously enhance spect ral
efﬁciency and estimation accuracy. Speciﬁcally, we develo p a
successive convex approximation (SCA) based algorithm whi ch
transforms the original non-convex problem into a sequence of
convex subproblems ensuring convergence to a locally optim al
solution. Furthermore, leveraging the proposed SCA framew ork
and the Lagrange duality, we derive the optimal beamforming
structure for CRLB optimization in ISAC systems. Our ﬁnding s
characterize the reduction in radar streams one can employ
without affecting performance. This enables a dimensional ity
reduction that enhances computational efﬁciency. Numeric al
simulations validate that our approach achieves comparabl e
or superior performance to the considered benchmarks while
requiring much lower computational costs.
Index Terms —Integrated sensing and communications,
Cram´er-Rao lower bound, successive convex approximation.
I. I NTRODUCTION
Future wireless communications technologies are antici-
pated to meet increasingly demanding objectives to enable
a wide range of innovative applications. These application s,
including autonomous vehicles, extended reality, smart
factories, and advanced healthcare systems, require not on ly
ultra-reliable and low-latency communications but also pr ecise
sensing capabilities for environment perception, localiz ation,
and tracking [ 2]. A major challenge lies in the limited
availability of spectrum, as both communications and sensi ng
traditionally operate in separate frequency bands with iso lated
infrastructures. This separation results in inefﬁcient sp ectrum
utilization and high hardware costs, further compounded by
the need to simultaneously support diverse use cases. Withi n
this landscape, integrated sensing and communications (IS AC)
has emerged as an attractive paradigm that uniﬁes wireless
communications and radar sensing functionalities [ 3].
ISAC offers signiﬁcant advantages over conventional
technologies that treat communications and sensing as
A part of this work has been accepted for presentation at the I EEE Int.
Conf. Acoustics, Speech, and Signal Process. (ICASSP), 202 5 [ 1].
T. Fang, M. Ma, M. Juntti, and N. T. Nguyen are with the Centre
for Wireless Communications, University of Oulu, 90014 Oul u, Finland
(e-mail: {tianyu.fang, mengyuan.ma, markku.juntti, nhan.nguyen }@oulu.ﬁ).
N. Shlezinger is with School of ECE, Ben-Gurion University o f the Negev,
Beer-Sheva 84105, Israel (email: nirshl@bgu.ac.il). A. L. Swindlehurst are
with the Center for Pervasive Communications & Computing, U niversity of
California, Irvine, CA 92697, USA (email: swindle@uci.edu ).
separate systems. By sharing the same radio-frequency
signals, ISAC improves spectrum efﬁciency, reduces hardwa re
and infrastructure costs, and enhances energy efﬁciency [ 4].
Unlike traditional systems where communications and radar
sensing are typically designed and deployed independently ,
ISAC aims to achieve dual functionality with a uniﬁed system
framework through shared spectrum, hardware, and joint
signal processing [ 5]. The need to have both functionalities
co-exist while sharing resources, gives rise to the need for
dedicated beamforming techniques that account for both
functionalities while being complexity-aware [ 6].
A. Related W orks
A substantial body of research has focused on beamforming
optimization to enable attaining the aforementioned beneﬁ ts in
multiuser multi-antenna ISAC systems. Common metrics for
the communications functionality are the achievable (sum) rate
and signal-to-interference-plus-noise ratio (SINR). For sensing
performance, various metrics can be used, such as proximity
to a desired beampattern [ 7]–[11], signal-to-clutter-plus-noise
ratio (SCNR) [ 12]–[16], Cram´ er–Rao lower bound (CRLB)
of the target parameters [ 17]–[21], and mutual information
[22], [ 23]. For communications, the sum rate (SR) is often
preferred, being is a fundamental measure of the overall
multiuser communications network. For sensing, the CRLB is
recognized as a fundamental metric that provides a theoreti cal
limit on parameter estimation accuracy [ 19], [ 21]. While
the SR and CRLB are highly relevant for assessing ISAC
beamforming, utilizing them as objectives for beamformer
optimization poses signicant challenges due to their being
highly non-convex functions of the beamforming vectors.
V arious solutions have been proposed to address CRLB-
based ISAC beamforming optimization problems, ranging
from globally optimal to suboptimal. Liu et al. [17] considered
CRLB minimization subject to communications quality of
service and transmit power constraints, and obtained a
globally optimal solution using semi-deﬁnite relaxation
(SDR). Recently, Tang et al. [24] extended the work of [ 17]
from a single-target to a multi-target scenario, proposed a n
upper bound to approximate the CRLB minimization problem,
and developed an efﬁcient algorithm based on the alternatin g
direction method of multipliers (ADMM) framework to solve
the approximated problem. However, these methods face
inherent challenges when applied to beamforming designs
that involve communications sum rate (SR) optimization. To
tackle such challenges, Chen et al. [25] and Zhu et al. [26]
integrated SDR with techniques such as successive convex
approximation (SCA) or weighted minimum mean square
error (WMMSE). Their approaches aim to achieve a locally

optimal solution to the problem of balancing the SR and
CRLB performance using a weighted objective that is subject
to a transmit power constraint. Recently, a globally optima l
beamforming optimization algorithm employing SDR and
the branch and bound (BB) method was proposed in [ 27] to
optimize the weighted sum of the SR and CRLB. Although
offering superior performance, the use of BB requires a high
complexity that increases exponentially with the number
of communications users. Fractional programming (FP) is
another widely employed technique for CRLB optimization
[26], [ 28]–[30]. For instance, in [ 28], auxiliary variables
are introduced to transform the fractional CRLB into a
polynomial form, enabling a multivariable reformulation o f
the original problem that is solved using the ADMM.
Beyond traditional model-based optimization approaches,
deep learning has emerged as a useful tool beamforming
design. For instance, a convolutional long short-term
memory network leveraging historical channel data has been
developed for predictive beamforming in ISAC-based vehicl e-
to-infrastructure networks in [ 31]. An alternative approach
that combines deep learning with conventional optimizatio n is
deep unfolding [ 32], which was shown to facilitate iteration-
limited optimization of ISAC beamforming [ 6], [ 9], [ 33].
While the above approaches provide effective numerical
solutions to joint ISAC beamforming designs, they fail
to offer fundamental insights into the structure of the
optimal beamformers. As a result, they face challenges in
computational complexity, especially in large-scale netw orks.
To develop an efﬁcient algorithm with lower computational
complexity for ISAC beamforming, one promising approach
is to identify and exploit the optimal beamforming structur e
(OBS) of the original problem. The OBS for multi-user
communications-only systems was established in [ 34], where
the minimum mean square error (MMSE) ﬁlter is proven to be
the optimal choice for both transmit and receive beamformin g
using an SINR-based criterion. For sensing-only systems,
the structure of the transmit beamforming covariance matri x
has been characterized in [ 35] for CRLB-based optimization,
but the exact beamforming structure remains unknown. The
goal of this paper is to address this problem for beamforming
design in CRLB-based ISAC systems.
B. Contributions
We focus on the fundamental problem of maximizing the
SR while minimizing the CRLB in a multi-user, multi-antenna
monostatic ISAC system under a transmit power constraint,
balancing these key communications and sensing metrics.
Most existing CRLB-based optimization works focus on eithe r
single-target scenarios [ 17]–[21], [ 27]–[30] or multi-target
cases with a single parameter [ 24]–[26], typically assuming
a uniform linear array (ULA). In contrast, we establish
a general ISAC system model that supports simultaneous
communications with multiple users and estimation of multi ple
parameters for multiple targets using a uniform planar arra y
(UP A). Unlike traditional MIMO radar [ 36], our model allows
the number of radar signals to differ from the number of array
elements for complexity reduction, allowing to characteri ze
its impact on performance. While the formulated problem is
complex and inherently non-convex, our proposed approach
identiﬁes the OBS of CRLB-based beamforming optimization
and is thus able to provide a ﬂexible and low-complexity
solution for CRLB-based optimization in ISAC systems.
The key contributions of this paper are as follows:
• We establish a generic monostatic ISAC system model
that supports simultaneous communications with multiple
users and detection of multiple targets. We further derive
a general CRLB-based radar sensing metric capable of
estimating the azimuth and elevation angles of targets
relative to the BS, as well as their complex radar cross-
sections. This formulation encompasses existing CRLB
metrics for single-target sensing or limited-parameter
detection as special cases. Based on the derived CRLB
and SR metrics, we formulate a highly challenging
non-convex problem to achieve a tradeoff between
communications and sensing performance.
• We propose a uniﬁed framework based on SCA and
the identiﬁed full power property to handle the non-
convexity arising from both the communications and
sensing objectives. A two-layer SCA method is proposed
to transform the original highly non-convex problem into
a sequence of simple sphere projection problems, whose
optimal solutions are easy to obtain. We further provide
a rigorous proof of convergence for the proposed method
illustrating that the proposed algorithm reaches a locally
optimal solution for the weighted sum of SR and CRLB
maximization problem.
• Leveraging the proposed SCA method and Lagrange du-
ality, we derive the OBS for CRLB-based ISAC systems.
By exploiting the inherent low-dimensional beamforming
structure, we reformulate the original problem into a
lower-dimensional optimization with signiﬁcantly fewer
optimization variables. The reformulation preserves
the structure of the original problem but enables a
highly efﬁcient solution. In doing so, we rigorously
characterize the allowable reduction in radar signal
streams without compromising sensing performance,
making the proposed beamforming design framework
particularly appealing for large-scale ISAC systems.
• We perform extensive simulations to demonstrate that the
proposed algorithms achieve the same or better perfor-
mances compared to benchmark optimization techniques,
including SDR-based and FP-based algorithms, while
signiﬁcantly reducing the computational complexity.
Organization: The rest of this paper is organized as
follows. Section II introduces the system model and problem
formulation. Section III presents the proposed SCA method
along with a thorough analysis of its optimality and
convergence. Section IV derives the main results on the
structure of the optimal beamforming solution. Simulation
results and corresponding discussions are provided in
Section V to demonstrate the effectiveness of the proposed
algorithms. Finally, Section VI concludes the paper and
discusses potential directions for future work.
Notation: V ectors and matrices are represented by
lowercase and uppercase bold letters, respectively. The sp ace
2

Target 
Target 
Transmited Signal 
Echo Signal 
BS 
UE  
UE  
Fig. 1: Illustration of the system model.
of complex- and real-valued numbers is respectively denote d
by C and R, while R++ represents the set of positive real
numbers. The set of positive deﬁnite matrices is represente d
by S++. The expectation of a random variable is denoted as
E{·}. The magnitude of a complex number is written as |·| .
The circularly symmetric complex Gaussian distribution wi th
zero mean and variance σ2 is represented as CN (0, σ2). The
transpose and conjugate transpose operators are denoted by
(·)T and (·)H, respectively, while diag{y} denotes a diagonal
matrix whose main diagonal entries are elements of vector y.
II. P RELIMINARIES
A. Signal Model
We consider a downlink monostatic ISAC system as
shown in Fig. 1, where a base station (BS) is equipped with
Nt transmit antennas and Nr antennas for radar reception,
arranged as separate UP As with half-wavelength spacing. Th e
BS simultaneously transmits data signals to K single-antenna
communications users, indexed by the set K ≜{1, . . . , K},
while also utilizing these signals to estimate the paramete rs
of M point-like targets indexed by the set M ≜{1, . . . , M},
over L time slots, indexed by L ≜{1, . . . , L}.
1) Transmitted Signal Model
Let sc[l] = [ sc1[l], . . . , scK[l]]T ∈ CK×1 represent the
vector of symbols to be transmitted to the K users in the l-th
time slot and let Wc ≜ [wc1, . . . ,wcK]∈ CNt×K denote the
corresponding communications beamforming matrix at the
BS. Similarly, let ss[l]∈ CNs×1 be a vector of Ns signals at
time slot l devoted to radar sensing, which will be multiplied
by the radar beamforming matrix Ws∈ CNt×Ns. While the
common practice in MIMO radar [ 36], also suggested for
ISAC in [ 8], is to set Ns = Nt to exploit all available degrees
of freedom (DoF) for sensing, this increases the complexity of
the ISAC design and interference for communications. We wil l
examine later how the choice of Ns affects the overall system
performance. The complete transmit signal in the l-th time slot
is given by x[l] = Wcsc[l] + Wsss[l],∀l∈L . It is assumed
that the signal streams have unit power and are independent o f
each other, leading to E{sc[l]sHc[l]} = IK, E{ss[l]sHs [l]} = INs,
and E{sc[l]sHs [l]} = 0K×Ns [17].
2) Communications Model
The signal received by communications user k∈K at time
slot l∈L is given by
yk[l] =h
H
kwcksck[l]+
K∑
j⁄=k
h
H
kwjscj[l]+h
H
kWsss[l]+nck[l], (1)
where hk∈ CNt×1 is the channel vector between the BS and
user k, and nck[l]∼CN (0, σ2ck) is additive white Gaussian
noise. The communications channels are assumed to be
perfectly known at the BS and remain invariant throughout
the entire transmission block. Consequently, the achievab le
rate in nats/s/Hz for each user k∈K is given by
Rk = log
(
1+ |hHkwck|2∑K
j⁄=k|hHkwcj|2 +‖hHkWs‖2F + σ2ck
)
, (2)
where‖·‖ F denotes the Frobenius norm. The SR of all the
communications users, given as ∑Kk=1 Rk, is used as the
metric to evaluate the system’s communications performanc e.
3) Radar Model
At time slot l, the received echo signal at the BS is given by
ys[l] =
M∑
m=1
αmb(θm, φm)a
H
(θm, φm)x[l] + ns[l], (3)
where αm refers to the radar cross-section for target m,
ns[l]∼CN (0, σ2s I) is noise at the receiver, b(·) and a(·) are
the receive and transmit array steering vectors for sensing
and communications, respectively, with θm ∈ [−π, π] and
φm ∈ [−π/2, π/2] representing the azimuth and elevation
angles of the target relative to the BS.
We use the CRLB associated with θm and φm as the
sensing performance metric, which is obtained from the
inverse of the Fisher information matrix (FIM). To derive th e
FIM, we begin by rewriting ( 3) as
ys[l] = BUA
H
x[l] + ns[l], (4)
where
B ≜ [b(θ1, φ1), . . . ,b(θM , φM )] (5)
U ≜ diag([α1, . . . , αM ]) (6)
A ≜ [a(θ1, φ1), . . . ,a(θM , φM )]. (7)
Deﬁne θ = [ θ1,··· , θM ]T, φ = [ φ1,··· , φM ]T, and α =
[α1,··· , αM ]T, and let ω = [ θ, φ,ℜ{α},ℑ{α}]T∈ R4M×1
denote the vector of unknown parameters. We can now
characterize the FIM as stated in the following lemma:
Lemma 1 The FIM for estimating the parameters in ω is
given by the block matrix
F = 2Lσ2s


ℜ{F11} ℜ{ F12} ℜ{ F13} −ℑ{ F13}
ℜ{FT12} ℜ{ F22} ℜ{ F23} −ℑ{ F23}
ℜ{FT13} ℜ{ FT23} ℜ{ F33} −ℑ{ F33}
−ℑ{FT13} −ℑ{FT23} −ℑ{FT33} ℜ{ F33}

 ,
(8)
whose block entries are given by (9), shown at the top of the
next page, where Rx = WcWHc + WsWHs ,⊙ denotes the
Hadamard product, and
˙Aθ ≜
[ ∂a(θ1, φ1)
∂θ1
, . . . , ∂a(θM , φM )∂θM
]
,
3

F11 ≜ (UA
H
RxAU
H
)
T
⊙( ˙BHθ ˙Bθ)+( UAHRx ˙AθUH)T⊙(BH ˙Bθ)+( U ˙AHθRxAUH)T⊙( ˙BHθB)+( U ˙AHθRx ˙AθUH)T⊙(BHB)
F12 ≜ (UA
H
RxAU
H
)
T
⊙( ˙BHθ ˙Bφ)+( UAHRx ˙AθUH)T⊙(BH ˙Bφ)+( U ˙AHφRxAUH)T⊙( ˙BHθB)+( U ˙AHφRx ˙AθUH)T⊙(BHB)
F22 ≜ (UA
H
RxAU
H
)
T
⊙( ˙BHφ ˙Bφ)+( UAHRx ˙AφUH)T⊙(BH ˙Bφ)+( U ˙AHφRxAUH)T⊙( ˙BHφB)+( U ˙AHφRx ˙AφUH)T⊙(BHB)
F13 ≜ (A
H
RxAU
H
)
T
⊙ ( ˙BHθB) + (AHRx ˙AθUH)T⊙ (BHB)
F23 ≜ (A
H
RxAU
H
)
T
⊙ (B
H
φB) + (A
H
Rx ˙AφUH)T⊙ (BHB)
F33 ≜ (A
H
RxA)
T
⊙ (B
H
B), (9)
˙Bθ ≜
[ ∂b(θ1, φ1)
∂θ1
, . . . , ∂b(θM , φM )∂θM
]
,
˙Aφ ≜
[ ∂a(θ1, φ1)
∂φ1
, . . . , ∂a(θM , φM )∂φM
]
,
˙Bφ ≜
[ ∂b(θ1, φ1)
∂φ1
, . . . , ∂b(θM , φM )∂φM
]
.
Proof: The lemma follows by expressing the FIM in terms
of the noise-free signal vs[l] = ys[l]− ns[l] = BUAHx[l] as
[37]:
F = 2ℜ
{ L∑
l=1
∂vHs [l]
∂ω R−1ns ∂vs[l]∂ω
}
= 2Lσ2sℜ{ ∂vHs∂ω ∂vs∂ω} ,
(10)
The detailed derivations for obtaining ( 8) from ( 10) are
provided in Appendix A.
B. Problem F ormulation
Deﬁne W = [ Wc, Ws] ∈ CNt×(K+Ns). Our goal is to
optimize the transmit beamforming matrix W to achieve
a favorable tradeoff between communications and sensing
performances. We evaluate communications performance
using the SR, and we adopt tr(F−1) as the sensing
performance metric, following [ 35], as the diagonal entries of
F−1 represent the CRLBs for the elements of ω. Several scalar
mappings of these CRLBs have been explored in prior work
[25]–[27], [ 29], [ 30]. Among these approaches, minimizing
tr(F−1) is the more common choice for the CRLB metric [ 35].
The beamforming design problem can be formulated as:
max
W∈S
δc
K∑
k=1
Rk− δstr(F−1) (11)
whereS ≜{W∈ CNt×(K+Ns)⏐⏐tr(WWH)≤ Pt}, with Pt
representing the transmit power budget. Adjusting the valu es
of the weights δc≥ 0 and δs≥ 0 enables a tradeoff between
the communications and sensing performances.
Problem ( 11) is inherently NP-hard due to the presence of
multiple non-convex fractional SINRs. Solving ( 11) to ﬁnd
the global optimum would involve exponential computationa l
complexity, as indicated in [ 27]. Moreover, the blockwise
matrix variables in F present a signiﬁcant challenge for
optimization. In the face of these challenges, we employ
the SCA framework to develop an efﬁcient approach that
ensures a locally optimal solution for ( 11), as detailed in the
following section.
III. ISAC B EAMFORMING OPTIMIZATION VIA SCA
To deal with the non-convex objective function in ( 11),
we develop a two-layer SCA approach, which allows a more
tractable surrogate objective function and guarantees con ver-
gence. Before delving into the details, we ﬁrst present the f ull
power consumption property in the following proposition.
Proposition 1 Any locally optimal point of problem (11)
must result in the full power consumption, i.e., satisfying
tr(WWH) = Pt. Thus, problem (11) is equivalent to
max
W∈B
δc
K∑
k=1
Rk− δstr(F−1) (12)
whereB ≜{W∈ CNt×(K+Ns)⏐⏐tr(WWH) = Pt}.
Proof: Please see Appendix B.
The full power consumption property for the subproblem
with δs = 0 has been presented in [ 38], [ 39]. In this work, we
extend the property to ISAC systems. Intuitively, Proposit ion 1
suggests that higher transmit power leads to improved
performance. As a result, the transmit beamforming matrix c an
be directly set to utilize the maximum power budget without
incurring any performance loss. We will later employ the ful l
power consumption property to facilitate our algorithm des ign.
A. First-Layer SCA
We ﬁrst recall two lemmas that form the foundation for
approximating the non-convex objective function in ( 11).
Lemma 2 ([ 40]) Function log
(
1 + |z|2d ), z∈ C, d∈ R++ is
lower bounded by its ﬁrst-order T aylor expansion as follows :
log
(
1 +|z|2
d
)
≥ log
(
1 +|z0|2
d0
)
+ 2ℜ{ z∗0
d0
z}
− |z0|2
d0(d0 +|z0|2) (|z|2 + d)−|z0|2d0 . (13)
Equality is achieved at (z, d) = ( z0, d0), where (z0, d0) is a
given point that belongs to the domain.
Lemma 3 ([ 41]) The function −tr(Z−1), Z∈ S++ is upper
bounded by its ﬁrst-order T aylor expansion as follows:
−tr(Z−1)≤ tr(Z−10 ZZ−10 )− 2tr(Z−10 ). (14)
Equality is achieved at Z = Z0, where Z0 is a given point
that belongs to the domain.
Applying Lemma 2 to Rk in ( 2), we construct a surrogate
function at iteration t as follows
r[t]k ≜ log(1 + ξ[t]k ) + 2ℜ{hHkwckη[t]k}− ξ[t]k
− β[t]k


K∑
j=1
|h
H
kw[t]cj|2 +‖hHkW[t]s ‖2F + σ2ck

 , (15)
4

where ξ[t]k , η[t]k , and β[t]k are auxiliary variables given by
ξ[t]k ≜ |hHkw[t]ck|2∑K
j=1,j⁄=k|hHkw[t]cj|2 +‖hHkW[t]s ‖2F + σ2ck , (16a)
η[t]k ≜ ξ[t]k
hHkw[t]ck , (16b)
β[t]k ≜ ξ[t]k∑K
j=1|hHkw[t]cj|2 +‖hHkW[t]s ‖2F + σ2ck . (16c)
Similarly, by applying Lemma 3 to−tr(F−1), we construct
the surrogate tr(FΦ[t])− 2tr(F[t]) at iteration t, where
Φ[t] ≜ F[t]−1F[t]−1. With these surrogate functions and
given a feasible point W[t], problem ( 12) can be expressed as
max
W∈B
δc
K∑
k=1
r[t]k + δs
(
tr(FΦ[t])− 2tr(F[t])) . (17)
Although ( 17) is still non-convex, its objective function
now has a quadratic form with respect to W on the sphere
boundaryB. This problem can be handled efﬁciently via the
SCA method as elaborated next.
Remark 1 W e remark that the ﬁrst term in (17), i.e.,
δc
∑K
k=1 r[t]k , serves as a lower bound for the original function
δc
∑K
k=1 Rk, while the second term, i.e., tr(FΦ[t])−2tr(F[t]),
acts as an upper bound for −tr(F−1). However , their sum is
not a lower bound of the original objective function. Thus, t he
proposed method differs from most existing SCA frameworks,
which ﬁrst construct a lower bound surrogate function for
the original objective function and then solve the surrogat e
subproblem based on that lower bound [ 41]. Nevertheless,
the convergence of the proposed method will be established
in Section III-D.
B. Second-Layer SCA
The blockwise structure of F poses a signiﬁcant challenge
for the SCA-based optimization in ( 17). To address this issue,
we ﬁrst partition Φ into blocks as
Φ =


Φ11 Φ12 Φ13 Φ14
ΦT12 Φ22 Φ23 Φ24
ΦT13 ΦT23 Φ33 Φ34
ΦT14 ΦT24 ΦT34 Φ44

 , (18)
which allows us to recast the objective function of ( 17) in a
more explicit and compact form, as stated in the following
proposition.
Proposition 2 Problem (17) can be recast as
max
W∈B
2δcℜ{tr(WcΣ[t]1 HH)} + δsℜ{tr(WWHQ[t])}
− δctr(WW
H
HΣ[t]2 HH), (19)
where
Σ[t]1 ≜ diag(η[t]1 , . . . , η[t]K ) (20)
H ≜ [h1, . . . ,hK] (21)
Σ[t]2 ≜ diag(β[t]1 , . . . , β[t]K ) (22)
Q[t] ≜ 2Lσ2s (Q[t]11 + Q[t]12 + Q[t]13 + Q[t]22 + Q[t]23 + Q[t]33) , (23)
and Q[t]11, Q[t]12, Q[t]13, Q[t]22, Q[t]23, Q[t]33 are deﬁned in (24).
Proof: Please see Appendix C.
Problem ( 19) is a non-convex quadratically constrained
quadratic problem (QCQP) with respect to W. This stems
from the fact that the matrix δsQ[t]− δcHΣ[t]2 HH is not nec-
essarily negative deﬁnite and the feasible set B is not convex.
To overcome this challenge and enable an efﬁcient solution, we
propose an equivalent but more tractable objective functio n.
Speciﬁcally, considering that tr(WWH) = P t is satisﬁed
at the optimal point, we can add λ (tr(WWH)− Pt) to the
objective function of ( 19), where λ is a predeﬁned constant.
With some algebra, problem ( 19) can be written as
max
W∈B
2ℜ{tr(W
H
C[t]1 )} + tr(WWHC[t]2 ), (25)
with C[t]1 ≜ [δcHΣ[t]H1 , 0Nt×Ns] and C[t]2 ≜
λI + 12 δs(Q[t] + Q[t]H) − δcHΣ[t]2 HH. By setting λ
as the absolute value of the dominant eigenvalue of
δcHΣ[t]2 HH− 12 δs(Q[t] +Q[t]H), then C[t]2 is guaranteed to be a
positive semideﬁnite matrix. With this condition, problem (25)
is in the form of the trust region problem (TRP) [ 42] with
the matrix variable W. TRPs with a vector variable can be
solved via methods such as bisection dual search [ 43], SDR
[44], eigenvalue problem reformulation [ 45], and the ﬁrst-
order conic method [ 42]. However, all of these approaches
developed for vector-based TRPs require the eigenvalue
decomposition, resulting in high computational complexit y.
To efﬁciently solve ( 25), we recall the following Lemma.
Lemma 4 ([ 13]) F or any given positive semideﬁnite
Hermitian matrix C ∈ CNt×Nt and any matrix
W ∈ CNt×(K+Ns), the function tr(WWHC) is lower
bounded by its ﬁrst-order T aylor expansion, given by
tr(WW
H
C)≥ 2ℜ{tr(W0W
H
C)}− tr(W0W
H
0C), (26)
where W0 is a given point that belongs to the domain, and
equality is achieved if and only if W = W0.
With Lemma 4, we can further derive the following linear
approximation for problem ( 25) at iteration t:
max
W∈B
2ℜ{tr(W
H
C[t]1 + WHC[t]2 W[t])}. (27)
Again, using the property tr(WWH) = Pt, problem ( 27) can
be reformulated as the following projection problem
min
W∈B
‖W− (C[t]1 + C[t]2 W[t])‖2F. (28)
The optimal solution to ( 28) is known to be
W[t+1] = ΠB
(
C[t]1 + C[t]2 W[t]
)
, (29)
where ΠB(·) denotes the projection of its argument onto B,
i.e.,
ΠB(X) ≜
√
Pt/tr(XXH)X. (30)
Remark 2 The proposed SCA method can be readily applied
with per-antenna power constraints by replacing the total
power constraint projection ΠB(·) with the per-antenna
power constraint projection ΠP(·), given by
ΠP (X) ≜
√
Pt/Nt(I⊙ (XX
H
))−1X, (31)
5

Q[t]11 ≜ AUH(Φ[t]11⊙( ˙BHθ ˙Bθ))UAH + ˙AθUH(Φ[t]11⊙(BH ˙Bθ))UAH +AUH(Φ[t]11⊙( ˙BHθB))U ˙AHθ + ˙AθUH(Φ[t]11⊙(BHB))U ˙AHθ
Q[t]12 ≜ 2(AUH(Φ[t]12⊙( ˙BHθ ˙Bφ))UAH + ˙AθUH(Φ[t]12⊙(BH ˙Bφ))UAH +AUH(Φ[t]12⊙( ˙BHθB))U ˙AHφ + ˙AθUH(Φ[t]12⊙(BHB))U ˙AHφ)
Q[t]22 ≜ AUH(Φ[t]22⊙( ˙BHφ ˙Bφ))UAH + ˙AφUH(Φ[t]22⊙(BH ˙Bφ))UAH +AUH(Φ[t]22⊙( ˙BHφB))U ˙AHφ + ˙AφUH(Φ[t]22⊙(BHB))U ˙AHφ
Q[t]13 ≜ AUH((2Φ[t]13 + 2jΦ[t]14)⊙ ( ˙BHθB))AH + ˙AθUH((2Φ[t]13 + 2jΦ[t]14)⊙ (BHB))AH
Q[t]23 ≜ AUH((2Φ[t]23 + 2jΦ[t]24)⊙ (BHφB))AH + ˙AφUH((2Φ[t]23 + 2jΦ[t]24)⊙ ( ˙BHB))AH
Q[t]33 ≜ A((Φ[t]33 + Φ[t]44 + 2jΦ[t]34)⊙ (BHB))AH. (24)
whereP ≜{W∈ CNt×(K+Ns)⏐⏐diag(WWH) = Pt1Nt/Nt}.
Here, diag(Y) returns a vector whose elements are the
diagonal entries of Y
C. Overall Optimization Framework for Problem (11)
Combining the proposed ﬁrst- and second-layer SCA
method in Sections III-A and III-B respectively, we summarize
the overall optimization algorithm for solving problem ( 11) in
Algorithm 1. Starting with an initial non-zero feasible point
W[0], the auxiliary variables ξk, ηk, βk,∀k∈K and Φ in the
ﬁrst-layer SCA framework are updated based on ( 16) and ( 8).
Then, the auxiliary variables C1 and C2 are updated based on
their deﬁnitions in ( 25). Finally, W is obtained with ( 29). This
process continues until the objective value in ( 11) converges.
Algorithm 1: The proposed SCA Algorithm
1 Initialize: t← 0, W[0];
2 repeat
3 t← t + 1;
4 Update
ξ[t]k , η[t]k and β[t]k according to ( 16) for ∀k∈K ;
5 Update Φ[t] = F[t]−2 according to ( 8);
6 Update W[t] according to ( 29);
7 until The objective value in (11) converges;
D. Convergence Analysis
In this subsection, we show that the objective value
monotonically increases after each iteration of Algorithm 1,
leading to convergence. The core idea of this convergence
analysis is to map the proposed SCA algorithm into a
projected gradient ascent (PGA) algorithm [ 46]. Speciﬁcally,
we denote the original objective function in problem ( 12) as
f (W) ≜ fc(W) + fs(W) with fc(W) ≜ δc
∑K
k=1 Rk and
fs(W) ≜−δstr(F−1), respectively. Similarly, the objective
function in ( 27) can be expressed as h[t](W) ≜ h[t]c (W) +
h[t]s (W) + λtr(WHW[t]) with h[t]c (W) = ℜ{tr(2WHC[t]1 −
δcWHHΣ[t]2 HHW[t])} and h[t]s (W) = 12 δstr(WH(Q[t] +
Q[t]H)W[t]). Then we have the following proposition.
Proposition 3 The gradient of f (W) with respect to W at
W = W[t] can be expressed as
∇f (W)
⏐⏐
W=W[t]
=∇h[t]c (W)⏐⏐W=W[t] +∇h[t]s (W)⏐⏐W=W[t]
= 2C[t]1 + (δsQ[t] + δsQ[t]H− 2δcHΣ[t]2 HH)W[t]. (32)
Proof: Please see Appendix D.
With Proposition 3, ( 29) can be rewritten as
W[t+1] = ΠB
(
C[t]1 + λW[t] + δs2(Q[t] + Q[t]H)W[t]
− δcHΣ[t]2 HHW[t]
)
= ΠB
(
W[t] + 12λ∇f (W)⏐⏐W=W[t]
)
, (33)
where we have utilized the property ΠB(λX) = ΠB(X)
for any constant λ > 0. Therefore, Algorithm 1 can be
interpreted as a PGA algorithm with step size 12λ . In this
context, constructing the surrogate functions in the ﬁrst- and
second-layer SCA corresponds to computing the gradient
of the original objective function f (W), while choosing
an appropriate value of λ is analogous to determining a
suitable step size. With these observations, we establish t he
convergence of Algorithm 1 as elaborated below.
Proposition 4 Assume that the objective function f (W) is ρ-
weakly convex [ 47]. When the shift parameter satisﬁes λ > ρ2 ,
Algorithm 1 generates a convergent sequence {f (W[t])}.
Proof: Please see Appendix E.
We note that although Proposition 4 is developed for
Algorithm 1, it can be generalized to tackle the optimization
problem with PGA, where both the objective function and
feasible set are non-convex. While Proposition 4 introduces
an additional assumption, requiring f (W) to be ρ-weakly
convex, this requirement is quite reasonable in ISAC system s,
as detailed in the following remark.
Remark 3 Assume the channel gain is ﬁnite for each user ,
i.e., ‖hk‖ < ∞,∀k ∈ K, the radar cross-section αm is
positive and ﬁnite, i.e., 0 < α m <∞,∀m∈ M, and the
noise power satisﬁes σ2c,k > 0,∀k∈K and σ2s > 0. Since
B is closed and compact, the gradient ∇f (W) is bounded
for any point W∈B . Thus there exists a constant C > 0
such that ‖∇f (Z)−∇ f (W)‖F ≤ C‖Z− W‖F, for any
Z, W∈B . This implies that ∇f (W) is a C-smooth function,
which satisﬁes the following inequality [ 48]
f (Z)≥ f (W) +⟨∇f (W), Z− W⟩− C2‖Z− W‖2F, (34)
where⟨·,·⟩ denotes the inner product. Since (34) is both a
sufﬁcient and necessary condition for f (W) to be weakly
convex, we can conclude that f (W) is a ρ-weakly convex
function with ρ = C [49, Lemma 1]. While it is generally
6

challenging to analytically determinate the speciﬁc param eter
ρ, it can be estimated numerically by computing the dominant
eigenvalue of the matrix C[t]2 in each iteration.
E. Computational Complexity Analysis
The complexity of Algorithm 1 is mainly due to the matrix
multiplications and inverses. In each iteration, the compl exity
of calculating the auxiliary variables ξ[t]k , η[t]k , and β[t]k is
O(K 2Nt + KN 2t ). In step 5, the computation of the auxiliary
variable Φ[t] requires a complexity of O(M 3 + M 2Nr +
M 2Nt+NsN 2t ). The complexity of updating the beamforming
matrix isO(M 2Nr + M 2Nt + KN 2t + NsN 2t ). Consequently,
the overall complexity of I iterations of Algorithm 1 is of the
order ofO
(
I·(M 3 +M 2(Nt +Nr)+ K 2Nt +KN 2t +NsN 2t ))
operations.
IV. O PTIMAL BEAMFORMING STRUCTURE
While Section III develops a SCA-based numerical
algorithm for beamforming design, the structural properti es
of both the problem and its solution remain unclear, limitin g
deeper insights. Prior studies on the OBS in communications -
only systems have demonstrated its advantages, including
providing fundamental insights into beamforming directio ns
[34], offering theoretical guarantees for optimal structures in
extreme scenarios [ 34], enabling the design of low-complexity
beamforming algorithms [ 38], [ 39], and serving as a founda-
tion for deep unfolding methods [ 50], [51]. Motivated by these
beneﬁts, we seek to identify and exploit the OBS for problem
(11). To that aim, we ﬁrst derive the OBS and then establish
a low-dimensional beamforming optimization framework.
A. OBS for Problem (11)
The Lagrangian function for problem ( 11) is expressed as
L(W, µ) = δc
K∑
k=1
Rk−δstr(F−1)−µ(tr(WWH)−Pt), (35)
where µ is the Lagrange multiplier associated with the power
constraint. The ﬁrst-order optimal condition implies that
for any stationary point W⋄, there exists a corresponding
Lagrange multiplier µ⋄ that satisﬁes the ﬁrst-order stationary
condition, i.e., ∂L(W, µ)/∂W = 0, which leads to
2C⋄1+(δsQ⋄+δsQ⋄H−2δcHΣ⋄2HH)W⋄−2µ⋄W⋄ = 0, (36)
where the superscript (·)⋄ highlights the values of the
respective variables at the stationary point of problem ( 11).
Note that C⋄1, Q⋄, and Σ⋄2 are functions of W⋄ and their
exact numerical values are not considered here since we are
investigating the structure of the solutions.
By splitting W⋄ into W⋄c and W⋄s , we obtain the optimal
beamforming structure for CRLB optimization in ISAC
systems, as characterized by the following Theorem 1.
Theorem 1 The optimal beamforming structure for the ISAC
system with the given CRLB metric is
W⋄c =
(
µ⋄I + δcHΣ⋄2HH− 12 δs(Q⋄ + Q⋄H))−1δcHΣ⋄H1 ,( 1
2 δs(Q⋄ + Q⋄H)− δcHΣ⋄2HH
)
W⋄s = µ⋄W⋄s . (37)
Proof: By dividing W⋄ into W⋄c and W⋄s , we obtain
the following set of equations based on ( 36):
2δcHΣ⋄H1 + δs(Q⋄ + Q⋄H− 2δcHΣ⋄2HH)W⋄c− 2µ⋄W⋄c = 0,(
δs(Q⋄ + Q⋄H )− 2δcHΣ⋄2HH) W⋄s− 2µ⋄W⋄s = 0,
from which Theorem 1 directly follows.
It can be observed that the communications beamforming
matrix Wc generalizes the existing downlink multiuser
unicast beamforming structure presented in [ 34] to ISAC
systems. Moreover, the columns of the optimal sensing
beamforming matrix are either the eigenvectors of the matri x
1
2 δs(Q + QH)− δcHΣ2HH or the zero vector.
B. Inherent Low-Dimensional Beamforming Structure
Theorem 1 indicates that the optimal beamforming solutions
can be fully determined by a set of parameters with signiﬁ-
cantly reduced dimensions. Speciﬁcally, instead of optimi zing
the original variable W, which comprises Nt× (K + Ns)
complex entries, it sufﬁces to identify one real dual variab le
µ⋄, 2K complex auxiliary variables in Σ⋄1 and Σ⋄2, and 8M 2
real auxiliary variables in the symmetric matrix Φ⋄ on which
Q⋄ depends. This highlights that the dimension of the auxiliar y
variables{µ⋄, Σ⋄1, Σ⋄2, Φ⋄} for obtaining the optimal beam-
forming solution{W⋄c , W⋄s} does not scale with the number
of transmit antennas Nt or the number of sensing streams Ns.
Inspired by this fact, we now explore the inherent low-
dimensional structure of ( 37). First, we provide an upper
bound on the number of sensing streams Ns in the following
lemma.
Lemma 5 With δc = 0 , problem (11) reduces to a CRLB
minimization problem. The rank of its optimal solution is no t
more than 3M , i.e., rank(W⋄s⏐⏐δc=0)≤ 3M .
Proof: Please see Appendix F.
Lemma 5 indicates that Ns = 3 M is sufﬁcient to fully
exploit the available DoFs for sensing, and setting Ns > 3M
is unnecessary. Our subsequent simulation results verify t his
in Section V -B.
C. Low-Dimensional Beamforming Design
The above ﬁnding reveals that the dimensions of the opti-
mization variable can be further reduced without compromis -
ing the performance. This motivates the following proposit ion.
Proposition 5 Problem (11) can be reformulated as
max
P
δc
K∑
k=1
Rk− δstr(F−1) (38a)
s.t. W = NP, (38b)
tr(PP
H
N
H
N)≤ Pt, (38c)
where P = [ Pc, Ps] ∈ C(K+3M)×(K+3M) is an auxiliary
variable and N = [H, A, ˙Aθ, ˙Aφ].
Proof: Please see Appendix G.
The number of variables in ( 38) is K 2 + 9 M 2 + 6 M K,
which is signiﬁcantly lower than that of the original proble m
(11) when Nt ≫ max{K, M}. Furthermore, problem
7

(38) has a structure similar to the original problem ( 11),
enabling an efﬁcient low-complexity solution. Speciﬁcall y,
by deﬁning the effective channel matrix as [~H,~A,~˙Aθ,~˙Aφ] =
NH[H, A, ˙Aθ, ˙Aφ] and substituting the original channel
matrices{H, A, ˙Aθ, ˙Aφ} with their transformed counterparts
{~H,~A,~˙Aθ,~˙Aφ} in problem ( 38), we obtain a reformulated
problem that retains the structure of the original one.
Consequently, the methods used to solve for the original
beamforming matrix W can be similarly applied in computing
P. The key difference is that after the ﬁrst- and second-layer
SCA, the following linear approximation problem is obtaine d
at iteration t
max
P
ℜ
{
tr
(
P
H
(
~C[t]1 +~C[t]2 P[t]
))}
s.t. tr(PP
H
N
H
N) = Pt,
(39)
where ~C[t]1 and ~C[t]2 are auxiliary variables computed in the
same way as C1 and C2 according to {~H,~A,~˙Aθ,~˙Aφ}.
Applying the Lagrangian method, we obtain a closed-form
solution to ( 39), written as
P[t+1] =
√
Pt/tr(L[t]L[t]H (NHN)−1)(NHN)−1L[t], (40)
with L[t] = ~C[t]1 +~C[t]2 P[t]. We refer to the algorithm for solv-
ing the low-dimensional problem ( 38) as the low-dimensional
Algorithm 1. This low-dimensional reformulation is particu-
larly beneﬁcial in extremely large MIMO systems [ 52].
V. S IMULATION RESULTS
In this section, we evaluate the computational complexity,
convergence, and performance of the proposed algorithms. 1
In all simulations, unless otherwise stated, we set Nt = 16 ,
Nr = 20 , Ns = Nt, K = 4 , M = 2 , L = 64 , δs = 1 , and
δc = 0 .25 [17]. The transmit power is set to Pt = 10 dBm
while the noise variances are σ2s = σ2ck = 0 dBm. We adopt
a Rayleigh fading model for the communications channel
[17]. The UP A for downlink communications has a size of
Nth× Ntv, where Nth = 4 and Ntv = 4 are the numbers
of antennas in the horizontal and vertical dimensions, resp ec-
tively. The UP A steering vector a(θ, φ) is modeled as [ 53]
a(θ, φ) = ah(θ, φ)⊗ av(φ),
with
ah(θ, φ) = 1√Nth[1, ejπ sin θ sin φ, . . . , ejπ(Nth−1) sin θ sin φ]T ,
av(φ) = 1√Ntv[1, ejπ cos φ, . . . , ejπ(Ntv−1) cos φ]T ,
where ⊗ represents the Kronecker product. The partial
derivatives of the steering vector a(θ, φ) with respect to θ
and φ are expressed as
∂a(θ, φ)
∂θ = ∂ah(θ, φ)∂θ ⊗ av(φ),
∂a(θ, φ)
∂φ = ∂ah(θ, φ)∂φ ⊗ av(φ) + ah(θ, φ)⊗ ∂av(φ)∂φ ,
1The source code is available online at
https://github.com/Nostalgia2022/OBS-for-CRLB-ISAC.
0 100 200 300 400 500 600 700 800
Number of Iterations
-2
-1.5
-1
-0.5
0
0.5
1
Objective Value
s=1, c=0.05
s=1, c=0.1
s=1, c=0.15
Fig. 2: Convergence behavior of the proposed algorithm with
various weight coefﬁcients.
0 2 4 6 8 10 12 14 16 18 20
Trace of the Inverse of the FIM
0
2
4
6
8
10
12
14Sum Rate (nats/Hz)
WMMSE-SDR
FP-SGDA
Algorithm 1
1.5 2 2.5
3.6
3.8
4
4.2
4.4
Fig. 3: Tradeoff region between communications and sensing .
where
∂ah(θ, φ)
∂θ = jπ cos θ sin φnth⊙ ah(θ, φ),
∂ah(θ, φ)
∂φ = jπ sin θ cos φnth⊙ ah(θ, φ),
∂av(φ)
∂φ =−jπ sin φntv⊙ av(φ),
with nth = [0, 1, . . . , Nth−1]T and ntv = [0, 1, . . . , Ntv−1]T.
The steering vector b(θ, φ) and its partial derivatives are
modeled similarly. Furthermore, the radar cross-section αm
is set as αm = 0 .1× (1 + 0 .2νu)e2jπνu [13], where νu
follows a uniform distribution U(0, 1). The angles θm and
φm are sampled independently from a uniform distribution
U(−2π/3, 2π/3). The convergence tolerance for Algorithm 1
is set to 10−4, and all the presented results are averaged over
100 channel realizations.
A. Convergence and Performance
We ﬁrst evaluate the convergence behavior of Algorithm
1 with different values of the weights δs and δc, as shown
in Fig. 2. We see that Algorithm 1 exhibits a monotonic
increase until convergence for all weight coefﬁcients, whi ch
is consistent with the theoretical analysis presented in
Proposition 4. Although Algorithm 1 requires hundreds of
iterations to converge, its per-iteration complexity is ve ry
8

0 1 2 3 4 5 6 7 8
Number of Sensing Streams
-12
-10
-8
-6
-4
-2
0
Objective Value Algorithm 1, K=1
Algorithm 1, K=2
Algorithm 1, K=3
Algorithm 1, K=0
WMMSE-SDR, K=1
WMMSE-SDR, K=2
WMMSE-SDR, K=3
WMMSE-SDR, K=0
Fig. 4: Objective value versus the number of sensing streams .
low, leading to fast convergence in terms of CPU time.
In Fig. 3, we show the communications–sensing tradeoff
region achieved by the proposed approach compared against
the WMMSE-SDR and FP-SGDA baselines from [ 26]. The
WMMSE-SDR method ensures a locally optimal solution
at the expense of a high computational complexity, while
FP-SGDA offers a lower-complexity alternative with a sligh t
performance loss. The tradeoff regions are generated by ﬁxi ng
δs = 1 and varying δc from 10−7 to 105. Fig. 3 shows that
the proposed algorithm achieves a tradeoff region comparab le
to WMMSE-SDR. However, due to inherent differences in
methodology, the two algorithms do not necessarily reach
the same point on the tradeoff region boundary for identical
weight coefﬁcients.
B. Impact of Number of Radar Signal Streams (Ns)
Fig. 4 illustrates the value of Algorithm 1’s objective
function as Ns increases, with L = 128 and M = 3 . The
results show that the objective increases until Ns reaches a
speciﬁc threshold. For a sensing-only system, the threshol d is
Ns = M = 3, which is signiﬁcantly lower than the theoretical
upper bound 3M presented in Lemma 5. For ISAC systems,
the threshold decreases as the number of communications
users increases. Notably, when Ns = max{0, M− K}, the
performance ceases to improve with further increases of Ns.
This observation reveals that only M− K data streams (rather
than Nt as used in [ 8]) are needed to fully exploit the sensing
DoFs. In particular, when K≥ M , i.e., the number of users
is not less than the number of targets, it is sufﬁcient to use
only information signals sc[l],∀l, to guarantee the sensing
performance. Furthermore, this highlights the ﬂexibility
of Algorithm 1, as it consistently achieves the same or
better performance across all values of Ns. Note that the
beamforming matrix Ws has dimension Nt× Ns, whereas the
SDR-based algorithms lift it to the covariance domain, wher e
Rs = WsWHs has dimension Nt× Nt regardless of Ns. This
fundamental difference makes our algorithm signiﬁcantly
more efﬁcient than the SDR-based approaches. We can also
observe that WMMSE-SDR incurs a signiﬁcant performance
loss when the number of sensing streams is insufﬁcient.
8 16 32 64 128
Number of Transmit Antennas
10-1
100
101
102
103
104
105
Average CPU Time (sec)
WMMSE-SDR, Ns=Nt
FP-SGDA, Ns=Nt
Algorithm 1, Ns=3M
Algorithm 1, Ns=0
LD Algorithm1, Ns=3M
95.53%
Fig. 5: Average CPU Time vs. the number of transmit
antennas.
2 4 6 8 10 12
Number of Communications Users
-5
0
5
10
15
20
25Metric Values
WMMSE-SDR, SR
FP-SGDA, SR
Algorithm 1, SR
Sum Rate
WMMSE-SDR, CRLB
FP-SGDA, CRLB
Algorithm 1, CRLB
CRLB
WMMSE-SDR, OV
FP-SGDA, OV
Algorithm 1, OV
Objective Value
4.9 5 5.1
0.5
1
1.5
Fig. 6: Metric values versus the number of communications
users.
C. Comparison With Existing Locally Optimal Algorithms
Table I presents the communications and sensing
performance of the considered algorithms for different
numbers of transmit antennas. The required average CPU time
is also evaluated and shown in Fig. 5 for the case of Intel(R)
Xeon(R) Gold 6226 CPUs. Due to the exponentially increasing
computational cost of WMMSE-SDR, its results are provided
for only 32 or fewer transmit antennas. Table I demonstrates
that the considered algorithms exhibit comparable perform ance
for the same value of Nt. With more transmit antennas, the
communications performance is better at the cost of sensing
performance. Note that Ns = 0 indicates that the information
signals are used for both communications and sensing withou t
dedicated radar signals. Remarkably, although Algorithm 1
with Ns = 0 requires a shorter run time than with Ns = 3M ,
it provides a slight performance gain due its convergence
to better locally optimal solutions. Furthermore, Algorit hm
1 with Ns = 3 M , which utilizes the low-dimensional (LD)
beamforming structure stated in Proposition 5, achieves
the lowest average CPU time, verifying its efﬁciency and
illustrating its potential for extremely large MIMO system s.
Fig. 6 plots the value of the communications, sensing,
and overall objective function for K = 2 , 4, . . . ,12. All
9

TABLE I: Sum Rate and CRLB Performance comparison for differ ent beamforming algorithms.
Algorithm Number of Transmit Antennas Nt
Nt = 8 Nt = 16 Nt = 32 Nt = 64 Nt = 128
Each entry represents (Sum Rate, CRLB).
WMMSE-SDR (11.02, 2.50) (15.02, 1.12) (18.16, 0.83) N/A N/A
FP-SGDA (10.88, 2.47) (14.97, 1.15) (18.12, 0.87) (20.91, 0 .79) (23.45, 0.82)
Algorithm 1, Ns = 3M (10.95, 2.46) (15.07, 1.13) (18.25, 0.85) (21.04, 0.78) (23 .61, 0.81)
Algorithm 1, Ns = 0 (10.93, 2.46) (15.07, 1.13) (18.27, 0.85) (21.13, 0.77) (23 .78, 0.78)
LD Algorithm 1, Ns = 3M (10.95, 2.46) (15.04, 1.14) (18.12, 0.87) (20.77, 0.79) (23 .38, 0.80)
-5 0 5 10 15 20
Transmit Power (dBm)
-60
-40
-20
0
20
40
60
Metric Values
WMMSE-SDR, SR
FP-SGDA, SR
Algorithm 1, SR
Sum Rate
WMMSE-SDR, CRLB
FP-SGDA, CRLB
Algorithm 1, CRLB
CRLB
WMMSE-SDR, OV
FP-SGDA, OV
Algorithm 1, OV
Objective Value
Fig. 7: Metric values versus the transmit powers.
three algorithms exhibit a similar trend: a signiﬁcantly
improving communications accompanied by a degradation
in the sensing accuracy. This occurs because, as the number
of communications users increases, the SR becomes large
enough to dominate the ISAC beamforming objective
function. The three algorithms show distinct behaviors: th e
WMMSE-SDR achieves the largest SR but the worst sensing
accuracy, FP-SGDA achieves the best sensing accuracy but
the worst SR, while the proposed algorithm offers the best
overall performance in terms of the objective.
Fig. 7 plots the values of the various objective functions’
performances for transmit powers from -5 dBm to 20 dBm.
Unlike the previous case, both communications and sensing
performances improve as the transmit power increases. All
three algorithms exhibit metrics across most regions, exce pt
that FP-SGDA experiences a slight performance degradation
when the transmit power reaches 20 dBm.
VI. C ONCLUSION
We have investigated the fundamental problem of maximiz-
ing the weighted sum of the sum rate and the trace of the FIM
under a total power constraint for ISAC systems. We ﬁrst iden -
tiﬁed the full power consumption property for ISAC systems.
Using this property and leveraging lower bounds as surrogat es
for the intractable objective function, we proposed an efﬁc ient
low-complexity iterative algorithm that solves the optimi zation
with provable convergence. Furthermore, we obtained the
optimal beamforming structure for CRLB-based ISAC
systems, enabling a signiﬁcant reduction in the dimension
of the optimized variables to further enhance computationa l
efﬁciency. Numerical simulations veriﬁed the superiority of
the proposed design over the considered baselines.
The developed algorithms are not restricted to the basic
ISAC systems considered in this study; they can be readily
extended to advanced ISAC scenarios, such as reconﬁgurable
intelligent surface-aided ISAC and ISAC with near-ﬁeld com -
munications. Moreover, the proposed full-power property a nd
low-dimensional beamforming structure may also be beneﬁci al
for cell-free massive MIMO systems and deep unfolding-base d
beamforming designs, which we leave for future work.
APPENDIX
A. Proof of Lemma 1
Recall that F is the FIM associated with the target
parameters ω = [ θ, φ,ℜ{α},ℑ{α}]T, and partition ω as
follows: ω1 = θ, ω2 = φ, ω3 =ℜ{α}, ω4 =ℑ{α}. We can
then express F in ( 10) as a block matrix:
F = 2σ2s


Fθθ Fθφ Fθℜ{α} Fθℑ{α}
FTθφ Fφφ Fφℜ{α} Fφℑ{α}
FTθℜ{α} FTφℜ{α} Fℜ{α}ℜ{α} Fℜ{α}ℑ{α}
FTθℑ{α} FTφℑ{α} FTℜ{α}ℑ{α} Fℑ{α}ℑ{α}

 ,
where each block is deﬁned as
Fωiωj = 2σ2sℜ
{ L∑
l=1
∂vHs [l]
∂ωi
∂vs[l]
∂ωj
}
,∀i, j∈{ 1, 2, 3, 4}.
The partial derivative with respect to θi is given by
∂vs[l]
∂θi
= ˙BθeieTi UAHx[l]+BeieTi U ˙AHθx[l],∀i∈{ 1, . . . , M},
where ei = [0 , . . . ,1, . . . ,0]T denotes a vector with 1 located
at the i-th position and zeroes elsewhere. Then
Fθiθj = 2σ2s
L∑
l=1
ℜ
{
tr
( ∂vs[l]
∂θj
∂vHs [l]
∂θi
)}
= 2Lσ2sℜ{tr(eTjUAHRxAUHeieTi ˙BHθ ˙Bθej
+ e
T
jUA
H
Rx ˙AθUHeieTi BH ˙Bθej
+ e
T
jU ˙AHθRxAUHeieTi ˙BHθBej
+e
T
jU ˙AHθRx ˙AθUHeieiBHBej
)}
= 2Lσ2sℜ{(UAHRxAUH)ji( ˙BHθ ˙Bθ)ij
+ (UA
H
Rx ˙AθUH)ji(BH ˙Bθ)ij
+ (U ˙AHθRxAUH)ji( ˙BHθB)ij
+(U ˙AHθRx ˙AθUH)ji(BHB)ij
}
,
where Xij denotes the (i, j)-th element of X,
Rx ≜ x[l]xH[l] = WWH, and we have used the property
10

tr(XYZ) = tr( YZX). Hence, we have
Fθiθj = 2Lσ2sℜ{[F11]ij} ⇒ Fθθ =ℜ{F11},
with F11 given in ( 9). The remaining terms in the FIM can
be readily calculated in the same way with the following
partial derivatives
∂vs[l]
∂φi
= ˙BφeieTi UAHx[l] + BeieTi U ˙AHφx[l],
∂vs[l]
∂ℜ{αi} = Beie
T
i A
H
x[l], ∂vs[l]∂ℑ{αi} = jBeieTi AHx[l].
B. Proof of Proposition 1
We prove this proposition by contradiction, assuming that
there exists a locally optimal solution W⋄ such that‖W⋄‖2F <
Pt. To simplify the notation, we deﬁne the total received signa l
power at user k as the sum of the desired signal power, interfer-
ence power, and noise power, i.e., Tk = Sk + Dk + σ2ck, where
Tk ≜
K∑
j=1
|h
H
kwck|2 +‖hHkWs‖2F + σ2ck, (B.1)
Dk ≜
K∑
j=1,j⁄=k
|h
H
kwcj|2 +‖hHkWs‖2F. (B.2)
Sk ≜|h
H
kwck|2. (B.3)
Let W◦ ≜ ̟W⋄ with ̟ ≜√Pt/‖W⋄‖F > 1. The corre-
sponding SINR for user k satisﬁes the following inequalities:
Sk(W⋄)
σ2ck < ̟2Sk(W⋄)σ2ck = Sk(W◦)σ2ck , if Dk(W⋄) = 0 ,
Sk(W⋄)
Dk(W⋄) + σ2ck < ̟2Sk(W⋄)̟2Dk(W⋄) + σ2ck = Sk(W◦)Dk(W◦) + σ2ck ,
if Dk(W⋄)⁄= 0,
Since the achievable rate Rk is a monotonically increasing
function with respect to its corresponding SINR, these
inequalities imply the existence of a point W◦ = ̟W⋄s near
W⋄s , with an increased objective value for communications
component. Similarly, for the sensing component, we have
−tr(F−1(W◦s )) =−̟2tr(F−1(W⋄s )) >−tr(F−1(W⋄s )),
which suggests that the sensing objective value also increa ses
at point W◦. The existence of W◦, at which the overall
objective value is strictly larger than that of W⋄, contradicts
the assumption that W⋄ is a locally optimal point of
problem ( 11). Thus, for any locally optimal point W⋄s , the
corresponding power constraint must hold with equality.
C. Proof of Proposition 2
Since ( 17) consists of both communications and sensing
components, the proof is divided into two parts. In the ﬁrst
part, we address the communications component. Speciﬁcall y,
the communications term, δc
∑K
k=1 rk, is equal to
δc
K∑
k=1
(log(1 + ξk)− ξk− βkσ2ck) + 2δcℜ{
K∑
k=1
tr(wckηkh
H
k)}
− δc
K∑
k=1
βk (tr(WcW
H
chkh
H
k) + tr(WsW
H
s hkh
H
k))
= ¯C + 2δcℜ{tr(WcΣ1HH)}− δctr(WcWHcHΣ2HH)
− δctr(WsW
H
s HΣ2H
H
), (C.1)
where ¯C is a constant, Σ1 = diag( η1, . . . , ηK), H =
[h1, . . . ,hK], and Σ2 = diag(β1, . . . , βK).
For the sensing component, given that Φ and F are
symmetric matrices, the sensing term tr(ΦF) is equal to
tr(ΦTF), which can be expressed as
ℜ{tr[Φ
T
11F11 + 2Φ
T
12F12 + 2(Φ
T
13 + jΦ
T
13)F13 + Φ
T
22F22
+ 2(Φ
T
23 + jΦ
T
24)F23 + (Φ
T
33 + Φ
T
44 + 2jΦ
T
34)F33]}.
(C.2)
The ﬁrst term of ( C.2), i.e.,ℜ{tr[ΦT11F11]}, can be expanded
as
ℜ{tr(Φ
T
11[(UA
H
RxAU
H
)
T
⊙ ( ˙BHθ ˙Bθ)
+ (UA
H
Rx ˙AθUH)T⊙ (BH ˙Bθ)
+ (U ˙AHθRxAUH)T⊙ ( ˙BHθB)
+ (U ˙AHθRx ˙AθUH)T⊙ (BHB)]}
=ℜ{tr(Rx[AU
H
(Φ11⊙ ( ˙BHθ ˙Bθ))UAH
+ ˙AθUH(Φ11⊙ (BH ˙Bθ))UAH
+ AU
H
(Φ11⊙ ( ˙BHθB))U ˙AHθ
+ ˙AθUH(Φ11⊙ (BHB))U ˙AHθ]}
≜ℜ{tr(RxQ11)}, (C.3)
where we have utilized the property
ℜ{tr(Φ
T
11[(UA
H
RxAU
H
)
T
⊙ ( ˙BHθ ˙Bθ)])}
=ℜ{tr(Rx[AU
H
(Φ11⊙ ( ˙BHθ ˙Bθ))UAH])}. (C.4)
The remaining terms can be calculated similarly using the co r-
responding parameter matrices deﬁned in ( 9). By combining
(C.1) and ( C.2) and omitting constant terms, we obtain ( 19).
D. Proof of Proposition 3
We prove proposition 3 separately for the communications
and sensing components. To simplify the notation, we deﬁne
Ik = Dk + σ2ck, where Dk is deﬁned in ( B.2). The gradient
of fc(W) is given by
∂fc(W)
∂wck
= ∂Rk
∂wck
+
K∑
i=1,i⁄=k
∂Ri
∂wck
= 2
(
1 + Sk
Ik
)−1 hkhHkwck
Ik
− 2
K∑
i=1,i⁄=k
(
1 + Si
Ii
)−1 Si
I 2i hih
H
i wck
= 2 hkhHkwck
Ik
− 2
K∑
i=1
Si
IiTi
hih
H
i wck
= 2hkη∗k− 2
K∑
i=1
βihih
H
i wck,∀k∈K , (D.1)
∂fc(W)
∂Ws
=−2
K∑
k=1
Sk
IkTk
hkh
H
kWs =−2
K∑
k=1
βkhkh
H
kWs,
(D.2)
where we have used the identities(
1 + Sk
Ik
)−1
= Ik
Tk
= 1− Sk
Tk
, (D.3)
11

ηk = ξkhHkwck = (hHkwck)∗Ik , (D.4)
βk = ξkIk = SkIkTk . (D.5)
Now, we can rewrite ∂fc(W)/∂W in the following compact
form:
∂fc(W)
∂W = 2δc C1− 2HΣ2HHW, (D.6)
which is exactly the same as the gradient of h[t]c (W) by
substituting W = W[t].
For the sensing component, the gradient of fs(W) is given
by
∂fs(W)
∂W =
4∑
m,n=1
M∑
i,j=1
∂fs(W)
∂[Fωmωn ]ij
∂[Fωmωn ]ij
∂W
(a)
=
4∑
m,n=1
M∑
i,j=1
[Φmn]ij
∂[Fωmωn ]ij
∂W
(b)
= 2 QW,
(D.7)
where (a) follows from ∂fs(W)/∂F = F−2 = Φ and (b)
follows from a simpliﬁcation similar to that in the proof of
Appendix C. We take the ﬁrst term m = 1 , n = 1 as an
example to show how to simply ( D.7):
M∑
i,j=1
[Φ11]ij
∂[Fω1ω1]ij
∂W =
M∑
i,j=1
[Φ11]ij
∂Fθiθj
∂W
= 2
M∑
i,j=1
[Φ11]ij[AU
H
(eie
T
i ( ˙BHθ ˙Bθ)ejeTj)UAH
+ ˙AθUH(eieTi (BH ˙Bθ)ejeTj)UAH
+ AU
H
(eie
T
i ( ˙BHθB)ejeTj)U ˙AHθ
+ ˙AθUH(eieTi (BHB)ejeTj)U ˙AHθ]W
= 2[AU
H
(Φ11⊙ ( ˙BHθ ˙Bθ))UAH
+ ˙AθUH(Φ11⊙ (BH ˙Bθ))UAH
+ AU
H
(Φ11⊙ ( ˙BHθB))U ˙AHθ
+ ˙AθUH(Φ11⊙ (BHB))U ˙AHθ]W
= 2Q11W.
The remaining terms can be calculated similarly. Note that
withℜ{tr(X)} = 12 tr(X + XH), we can obtain the following
equivalent form
∂fs(W)
∂W = (Q + Q
H
)W, (D.8)
which is exactly the same as the gradient of h[t]s (W). By
summing δc× ∂fc(W)∂W and δs× ∂fs(W)∂W , we obtain ( 32).
E. Proof of Proposition 4
Recall the deﬁnition of a ρ-weakly convex function as
stated in [ 47]:
Deﬁnition 1 A function f (W) is ρ-weakly convex
if there exists a convex function g(W) such that
g(W) = f (W) + ρ2‖W‖2F.
Under the assumption that f (W) is ρ-weakly convex, we
construct the convex function
g(W) = f (W) + ρ2‖W‖2F.
The full power consumption property, as stated in
Proposition 1, implies that ρ2‖W‖2F is a constant term.
This leads to the following equivalent optimization proble m
max
W∈B
δc
K∑
k=1
Rk− δstr(F−1) + ρ2‖W‖2F. (E.1)
For the new convex objective function, we can derive the
following linear lower bound at iteration t
g(W)≥ g(W[t]) +⟨∇g(W)⏐⏐W=W[t] , W− W[t]⟩
=⟨∇f (W)
⏐⏐
W=W[t] + ρW[t], W⟩ + ˆC, (E.2)
where ˆC is a constant, and ⟨·,·⟩ denotes the inner product in
the complex matrix space CNt×(K+Nt).
By maximizing this linear lower bound and projecting the
solution onto the boundary of the sphere B, we derive the
PGA update rule as
W[t+1] = ΠB(∇f (W)⏐⏐W=W[t] + ρW[t])
= ΠB
(
W[t] + 1ρ∇f (W)⏐⏐W=W[t]
)
,
(E.3)
which is exactly the same as the update formula in ( 33) when
λ = ρ2 . Assuming λ≥ ρ2 , we can establish:
f (W[t+1]) (a)= g(W[t+1])− λ‖W[t+1]‖2F
(b)
≥ f (W[t]) +⟨∇g(W)⏐⏐W=W[t] , W[t+1]− W[t]⟩
(c)
≥ f (W[t]),
where (a) follows from Deﬁnition 1, (b) follows from
the assumption λ ≥ ρ2 and ( E.2), and (c) holds since
⟨∇g(W)
⏐⏐
W=W[t] , W[t+1]− W[t]⟩ ≥ 0 for any convex
function g(W). Since the objective function is bounded
within the closed and compact set B, the sequence {f (W[t]}
is guaranteed to converge. This completes the proof.
F . Proof of Lemma 5
When δc = 0 , the optimal beamforming structure of Ws
simpliﬁes to
1
2 δs
(
Q⋄ + Q⋄H) W⋄s = µ⋄W⋄s , (F.1)
which implies that the columns of W⋄s are eigenvectors of
the matrix Q⋄ + Q⋄H. Therefore, the rank of W⋄s is less than
or equal to the rank of Q⋄ + Q⋄H. Recalling the deﬁnition of
Q given in ( 24), Q + QH can be expressed as the sum of a
set of matrices that can be rearranged as
Q + Q
H
= AX1 + ˙AθX2 + ˙AφX3, (F.2)
where X1 ∈ CM×Nt , X2 ∈ CM×Nt, X3 ∈ CM×Nt
are matrices whose speciﬁc details are omitted. It is
straightforward to verify that
rank(Q + Q
H
)≤ rank(AX1) + rank( ˙AθX2) + rank( ˙AφX3)
≤ 3M,
which completes this proof.
12

G. Proof of Proposition 5
Similar to the proof of Proposition 3, we prove
this proposition for the communications and sensing
separately. For the communications subproblem, the optima l
beamforming structure of Wc reduces to
W⋄c = (µ⋄I + HΣ⋄2HH)−1HΣ⋄H1
= H(µ⋄I + Σ⋄2HHH)−1Σ⋄H1 ≜ HP⋄c , (G.1)
which indicates that the optimal solution of the SR problem
lies in the range space of the channel matrix H. For the
sensing subproblem, the columns of the optimal solution W⋄s
are eigenvectors of the matrix Q⋄ + Q⋄H. Consequently W⋄s
lies in the range space of matrix Q⋄ + Q⋄H, i.e.,
W⋄s =(Q⋄ + Q⋄H)ˆPs
= [A, ˙Aθ, ˙Aφ][X1ˆPs, X1ˆPs, X1ˆPs]T
≜ [A, ˙Aθ, ˙Aφ]P⋄s ,
(G.2)
which implies that W⋄s lies in the range space of matrix
[A, ˙Aθ, ˙Aφ]. By introducing new variables Pc and Ps and
substituting ( G.1) and ( G.2) back into the original problem
(11), we obtain the low-dimensional reformulation ( 38).
REFERENCES
[1] T. Fang, N. T. Nguyen, and M. Juntti, “Low-complexity Cra m´ er-Rao
lower bound and sum rate optimization in ISAC systems,” arXiv
preprint arXiv:2502.03162, 2025.
[2] F. Dong, F. Liu, S. Lu, Y . Xiong, Q. Zhang, Z. Feng, and F. Ga o,
“Communication-assisted sensing in 6G networks,” IEEE J. Sel. Areas
Commun., 2025.
[3] F. Liu, Y . Cui, C. Masouros, J. Xu, T. X. Han, Y . C. Eldar, an d
S. Buzzi, “Integrated sensing and communications: Towards dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, 2022.
[4] D. Ma, N. Shlezinger, T. Huang, Y . Liu, and Y . C. Eldar, “Jo int
radar-communication strategies for autonomous vehicles: Combining
two key automotive technologies,” IEEE Signal Process. Mag. , vol. 37,
no. 4, pp. 85–97, 2020.
[5] J. A. Zhang, F. Liu, C. Masouros, R. W. Heath, Z. Feng, L. Zh eng,
and A. Petropulu, “An overview of signal processing techniq ues for
joint communication and radar sensing,” IEEE J. Sel. Topics Signal
Process., vol. 15, no. 6, pp. 1295–1315, 2021.
[6] J. Zhang, C. Masouros, F. Liu, Y . Huang, and A. L. Swindleh urst, “Low-
complexity joint radar-communication beamforming: From o ptimization
to deep unfolding,” IEEE J. Sel. Topics Signal Process. , 2025.
[7] F. Liu, C. Masouros, A. Li, H. Sun, and L. Hanzo, “MU-MIMO c ommu-
nications with MIMO radar: From co-existence to joint trans mission,”
IEEE Trans. Wireless Commun. , vol. 17, no. 4, pp. 2755–2770, 2018.
[8] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. E ldar, “Joint
transmit beamforming for multiuser MIMO communications an d MIMO
radar,” IEEE Trans. Signal Process. , vol. 68, pp. 3929–3944, 2020.
[9] N. T. Nguyen, L. V . Nguyen, N. Shlezinger, Y . C. Eldar, A. L .
Swindlehurst, and M. Juntti, “Joint communications and sen sing hybrid
beamforming design via deep unfolding,” IEEE J. Sel. Topics Signal
Process., vol. 18, no. 5, pp. 901–916, 2024.
[10] N. T. Nguyen, M. Ma, O. Lavi, N. Shlezinger, Y . C. Eldar, A . L.
Swindlehurst, and M. Juntti, “Deep unfolding hybrid beamfo rming
designs for THz massive MIMO systems,” IEEE Trans. Signal Process. ,
vol. 71, pp. 3788–3804, 2023.
[11] N. T. Nguyen, N. Shlezinger, Y . C. Eldar, and M. Juntti, “ Multiuser
MIMO wideband joint communications and sensing system with
subcarrier allocation,” IEEE Trans. Signal Process. , vol. 71, pp.
2997–3013, 2023.
[12] P . Wang, J. Fang, X. Zeng, Z. Chen, and H. Li, “Low-comple xity joint
transceiver optimization for MmWave/THz MU-MIMO ISAC syst ems,”
IEEE Internet Things J. , 2025.
[13] T. Fang, N. T. Nguyen, and M. Juntti, “Beamforming desig n for max-
min fairness performance balancing in ISAC systems,” in Proc. IEEE Int.
W orkshop Signal Process. Adv. Wireless Commun. (SPAWC), Sep. 2024.
[14] T. Zhang, G. Li, S. Wang, G. Zhu, G. Chen, and R. Wang, “ISA C-
accelerated edge intelligence: Framework, optimization, and analysis,”
IEEE Trans. Green Commun. Networking , vol. 7, no. 1, pp. 455–468,
2023.
[15] Y . Wang, Z. Y ang, J. Cui, P . Xu, G. Chen, T. Q. S. Quek, and
R. Tafazolli, “Optimizing the fairness of STAR-RIS and NOMA
assisted integrated sensing and communication systems,” IEEE Trans.
Wireless Commun., vol. 23, no. 6, pp. 5895–5907, 2024.
[16] M. Ma, T. Fang, N. Shlezinger, A. Swindlehurst, M. Juntt i,
and N. Nguyen, “Model-based machine learning for Max-Min
fairness beamforming design in JCAS systems,” arXiv preprint
arXiv:2409.17644, 2024.
[17] F. Liu, Y .-F. Liu, A. Li, C. Masouros, and Y . C. Eldar, “Cr am´ er-Rao
bound optimization for joint radar-communication beamfor ming,” IEEE
Trans. Signal Process. , vol. 70, pp. 240–253, 2021.
[18] X. Song, J. Xu, F. Liu, T. X. Han, and Y . C. Eldar, “Intelli gent
reﬂecting surface enabled sensing: Cram´ er-Rao bound opti mization,”
IEEE Trans. Signal Process. , vol. 71, pp. 2011–2026, 2023.
[19] Y . Xiong, F. Liu, Y . Cui, W. Y uan, T. X. Han, and G. Caire, “ On
the fundamental tradeoff of integrated sensing and communi cations
under Gaussian channels,” IEEE Trans. Inf. Theory , vol. 69, no. 9, pp.
5723–5751, 2023.
[20] X. Zhou, X. Du, and Y . Mao, “Cram´ er-Rao bound based wave form
optimization for MIMO radar: An efﬁcient linear-proximal m ethod,”
arXiv preprint arXiv:2409.12569 , 2024.
[21] Z. Ren, X. Song, Y . Fang, L. Qiu, and J. Xu, “Fundamental C RB-rate
tradeoff in multi-antenna multicast channel with ISAC,” in Proc. IEEE
Global Commun. Conf. , 2022, pp. 1261–1266.
[22] Y . Peng, S. Y ang, W. Lyu, Y . Li, H. He, Z. Zhang, and C. Assi ,
“Mutual information-based integrated sensing and communi cations: A
WMMSE framework,” IEEE Wireless Commun. Lett. , vol. 13, no. 10,
pp. 2642–2646, 2024.
[23] C. Ouyang, Y . Liu, and H. Y ang, “Performance of downlink and
uplink integrated sensing and communications (ISAC) syste ms,” IEEE
Wireless Commun. Lett. , vol. 11, no. 9, pp. 1850–1854, 2022.
[24] B. Tang, D. Li, W. Wu, A. Saini, P . Babu, and P . Stoica, “Du al-function
beamforming design for multi-target localization and reli able communi-
cations,” IEEE Trans. Signal Process. , vol. 73, pp. 559–573, 2025.
[25] K. Chen and Y . Mao, “Transmitter side beyond-diagonal R IS for
mmwave integrated sensing and communications,” in Proc. IEEE Int.
W orkshop Signal Process. Adv. Wireless Commun. (SPAWC), Sep. 2024.
[26] M. Zhu, L. Li, S. Xia, and T.-H. Chang, “Information and s ensing beam-
forming optimization for multi-user multi-target MIMO ISA C systems,”
EURASIP J. Adv. Signal Process. , vol. 2023, no. 1, pp. 15, 2023.
[27] J. Wu, Z. Wang, Y .-F. Liu, and F. Liu, “Efﬁcient global al gorithms for
transmit beamforming design in ISAC systems,” IEEE Trans. Signal
Process., vol. 72, pp. 4493–4508, 2024.
[28] B. Guo, J. Liang, G. Wang, B. Tang, and H. C. So, “Bistatic MIMO
DFRC system waveform design via fractional programming,” IEEE
Trans. Signal Process. , vol. 71, pp. 1952–1967, 2023.
[29] R. Liu, M. Li, Q. Liu, and A. Lee Swindlehurst, “SNR/CRB- constrained
joint beamforming and reﬂection designs for RIS-ISAC syste ms,” IEEE
Trans. Wireless Commun. , vol. 23, no. 7, pp. 7456–7470, 2024.
[30] Y . Chen, Y . Feng, X. Li, L. Zhao, and K. Shen, “Fast fracti onal
programming for multi-cell integrated sensing and communi cations,”
arXiv preprint arXiv:2406.10910 , 2024.
[31] C. Liu, W. Y uan, S. Li, X. Liu, H. Li, D. W. K. Ng, and Y . Li,
“Learning-based predictive beamforming for integrated se nsing and
communication in vehicular networks,” IEEE J. Sel. Areas Commun. ,
vol. 40, no. 8, pp. 2317–2334, 2022.
[32] N. Shlezinger, Y . C. Eldar, and S. P . Boyd, “Model-based deep learning:
On the intersection of deep learning and optimization,” IEEE Access ,
vol. 10, pp. 115384–115398, 2022.
[33] J. Zhang, M. Liu, J. Tang, N. Zhao, D. Niyato, and X. Wang, “Joint
design for RIS-aided ISAC via deep unfolding learning,” IEEE Trans.
on Cogn. Commun. Netw. , vol. 11, no. 1, pp. 349–361, 2025.
[34] E. Bj¨ ornson, M. Bengtsson, and B. Ottersten, “Optimal multiuser
transmit beamforming: A difﬁcult problem with a simple solu tion
structure [lecture notes],” IEEE Signal Process Mag. , vol. 31, no. 4,
pp. 142–148, 2014.
[35] J. Li, L. Xu, P . Stoica, K. W. Forsythe, and D. W. Bliss, “R ange
compression and waveform optimization for MIMO radar: A
Cram´ er–Rao bound based study,” IEEE Trans. Signal Process. ,
vol. 56, no. 1, pp. 218–232, 2008.
[36] P . Stoica, J. Li, and Y . Xie, “On probing signal design fo r MIMO radar,”
IEEE Trans. Signal Process. , vol. 55, no. 8, pp. 4151–4161, 2007.
13

[37] I. Bekkerman and J. Tabrikian, “Target detection and lo calization using
MIMO radars and sonars,” IEEE Trans. Signal Process. , vol. 54, no.
10, pp. 3873–3883, 2006.
[38] X. Zhao, S. Lu, Q. Shi, and Z.-Q. Luo, “Rethinking WMMSE: Can
its complexity scale linearly with the number of BS antennas ?,” IEEE
Trans. Signal Process. , vol. 71, pp. 433–446, 2023.
[39] T. Fang and Y . Mao, “Rate splitting multiple access: Opt imal
beamforming structure and efﬁcient optimization algorith ms,” IEEE
Trans. Wireless Commun. , vol. 23, no. 10, pp. 15642–15657, 2024.
[40] T. Fang and Y . Mao, “Optimal beamforming structure and e fﬁcient
optimization algorithms for generalized multi-group mult icast
beamforming optimization,” arXiv preprint arXiv:2312.16559 , 2023.
[41] Y . Sun, P . Babu, and D. P . Palomar, “Majorization-minim ization
algorithms in signal processing, communications, and mach ine learning,”
IEEE Trans. Signal Process. , vol. 65, no. 3, pp. 794–816, 2017.
[42] A. Beck and Y . V aisbourd, “Globally solving the trust re gion
subproblem using simple ﬁrst-order methods,” SIAM J. Optim. , vol.
28, no. 3, pp. 1951–1967, 2018.
[43] T. Fang and Y . Mao, “A low-complexity beamforming desig n for
beyond-diagonal RIS aided multi-user networks,” IEEE Commun. Lett. ,
vol. 28, no. 1, pp. 203–207, 2024.
[44] F. Rendl and H. Wolkowicz, “A semideﬁnite framework for trust region
subproblems with applications to large scale minimization ,” Math.
Program., vol. 77, no. 1, pp. 273–299, 1997.
[45] S. Adachi, S. Iwata, Y . Nakatsukasa, and A. Takeda, “Sol ving the
trust-region subproblem by a generalized eigenvalue probl em,” SIAM
J. Optim. , vol. 27, no. 1, pp. 269–291, 2017.
[46] D. Davis and D. Drusvyatskiy, “Stochastic model-based minimization
of weakly convex functions,” SIAM J. Optim. , vol. 29, no. 1, pp.
207–239, 2019.
[47] S. Chen, A. Garcia, and S. Shahrampour, “On distributed nonconvex
optimization: Projected subgradient method for weakly con vex problems
in networks,” IEEE Trans. Autom. Control , vol. 67, no. 2, pp. 662–675,
2022.
[48] Y . Nesterov et al., Lectures on Convex Optimization , vol. 137, Springer,
2018.
[49] K. K. Thekumparampil, P . Jain, P . Netrapalli, and S. Oh, “Efﬁcient
algorithms for smooth minimax optimization,” in Adv. Neural Inf.
Process. Syt. 2019, vol. 32, Curran Associates, Inc.
[50] Y . Wang, Y . Mao, and S. Ji, “RS-BNN: A deep learning frame work
for the optimal beamforming design of rate-splitting multi ple access,”
IEEE Trans. V eh. Technol., vol. 73, no. 11, pp. 17830–17835, 2024.
[51] W. Xia, G. Zheng, Y . Zhu, J. Zhang, J. Wang, and A. P . Petro pulu,
“A deep learning framework for optimization of miso downlin k beam-
forming,” IEEE Trans. Commun. , vol. 68, no. 3, pp. 1866–1880, 2020.
[52] Y . Zhang, X. Wu, and C. Y ou, “Fast near-ﬁeld beam trainin g for
extremely large-scale array,” IEEE Wireless Commun. Lett. , vol. 11,
no. 12, pp. 2625–2629, 2022.
[53] N. T. Nguyen, J. Kokkoniemi, and M. Juntti, “Beam squint effects
in THz communications with UPA and ULA: Comparison and hybri d
beamforming design,” in IEEE Globecom W orkshops (GC Wkshps) ,
2022, pp. 1754–1759.
14