---
title: "NOMA Empowered Integrated Sensing and Communication"
zotero_key: "W6BEE4ZE"
pdf_key: "A0DERMHC"
doi: "10.1109/gcwkshps56602.2022.10008704"
collection: "ISAC"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# NOMA Empowered Integrated Sensing and Communication — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

arXiv:2208.04786v4  [cs.IT]  28 Sep 2022
Reconﬁgurable Intelligent Surface Assisted NOMA
Empowered Integrated Sensing and Communication
Jiakuo Zuo ∗ and Y uanwei Liu†
∗ School of Internet of Things, Nanjing University of Posts an d Telecommunications, Nanjing 210003, China.
† School of Electronic Engineering and Computer Science, Que en Mary University of London, London E1 4NS, U.K.
E-mail: zuojiakuo@njupt.edu.cn, yuanwei.liu@qmul.ac.u k.
Abstract—This paper exploits the potential of reconﬁgurable
intelligent surface (RIS) to improve radar sensing in a non-
orthogonal multiple access (NOMA) empowered integrated se ns-
ing and communication (NOMA-ISAC) network. The objective
is to maximize the minimum radar beampattern gain by jointly
optimizing the active beamforming, power allocation coefﬁ cients
and passive beamforming. To tackle the formulated non-conv ex
problem, we propose an efﬁcient joint optimization algorit hm
by invoking alternating optimization, successive convex a pprox-
imation (SCA) and sequential rank-one constraint relaxati on
(SRCR) algorithm. Numerical results show that the proposed RIS
assisted NOMA-ISAC system, with the aid of the proposed sche me,
outperforms the RIS assisted ISAC system without NOMA.
Index Terms —Beamforming optimization, integrated sensing
and communication, non-orthogonal multiple access, recon ﬁg-
urable intelligent surface.
I. I NTRODUCTION
In conventional wireless communication, communication
quality of service (QoS) is the main indicator. However, in t he
upcoming beyond ﬁfth generation (B5G) and sixth generation
(6G) wireless networks, sensing service will play a more
important role than ever before [1]. The goal of future wirel ess
communication is to provide services based on both sensing a nd
communication functionalities. Toward this trend, integr ated
sensing and communication (ISAC) has emerged and attracted
growing attention in both academia and industries.
To boost the communication and sensing capabilities, vario us
key technologies can be exploited in ISAC, such as: millimet er
wave [2], terahertz [3] and massive multiple-input multipl e-
output (MIMO) [4]. However, the communication users will
suffer from severe interference when the system is overload ed,
which is not considered in these works. Non-orthogonal mul-
tiple access (NOMA) is a good solution as it can multi-
plex communication users and mitigate the inter-user inter fer-
ence. The authors in [5] ﬁrst proposed a NOMA empowered
ISAC (NOMA-ISAC) system, where the superimposed NOMA
communication signal was utilized to perform radar sensing .
Considering that the sensing signal can also be information -
bearing, the authors in [6] used multiple beams of the sensin g
signal to deliver extra multicast information and detect ra dar
targets simultaneously. The authors in [7] proposed a novel
NOMA aided joint radar and multicast-unicast communicatio n
system, where the base station (BS) transmits superimposed
This work was supported by Key Laboratory of Universal Wirel ess
Communications (BUPT), Ministry of Education, P .R.China u nder Grant
KFKT-2022105 and China Postdoctoral Science Foundation un der Grant
2021M693699.
multicast and unicast messages to the radar users and com-
munication users, while detecting the radar user targets. S ince
the bandwidth has been occupied by different applications,
the ISAC networks can not utilize all the spectrum for both
radar detection and wireless communication. To overcome th is
difﬁculty, the authors in [8] proposed an uplink NOMA-assis ted
semi-ISAC system, where the total bandwidth was divided int o
ISAC bandwidth and communication-only bandwidth.
In conventional ISAC systems, radar sensing relies on line-
of-sight (LoS) links between the BS and radar targets. How-
ever, in practical scenarios, the radar targets are likely t o be
distributed in the non-LoS (NLoS) region of the BS. As a
remedy, reconﬁgurable intelligent surface (RIS) can be int e-
grated into ISAC systems. RIS comprises a large number of
passive elements and can reconﬁgure the signal propagation by
adjusting the phase shifts. Also, the RIS can provide virtua l
LoS links to the ISAC systems, potentially resulting in bett er
sensing performance [9].
Inspired by the aforementioned discussion, we investigate
the RIS assisted NOMA-ISAC (RIS-NOMA-ISAC) system.
To the best of our knowledge, the joint optimization design
for the considered system has not been studied yet. In this
paper, the communication users and radar targets are assume d
to be at the NLoS areas of the BS. The RIS is deployed to
create reﬂection and virtual LoS links for communication an d
target sensing. A novel alternating algorithm is proposed t o
optimize the active beamforming, power allocation coefﬁci ents
and passive beamforming.
Notations:CM×1 denotes a complex vector of size M, diag(x)
denotes a diagonal matrix whose diagonal elements are the
corresponding elements in vector x. The (m, n)-th element
of matrix X is denoted as [X]m,n. xH and XH denote the
conjugate transpose of vector x and matrix X, respectively.
The notations Tr( X) and rank( X) denote the trace and rank
of matrix X, respectively. CN
(
0, σ2) represents a random
complex variable following the distribution of zero mean an d
σ2 variance.
II. S YSTEM MODEL AND PROBLEM FORMULATION
As shown in Fig. 1, the considered RIS-NOMA-ISAC system
consists of a dual-functional base station (BS) equipped wi th
NT antennas, 2K single-antenna users, an uniform linear
array (ULA)-RIS with M reﬂecting elements and L radar
targets. We assume that the direct links from the BS to the
communication users and radar targets are blocked, which is

Fig. 1: System model of the RIS-NOMA-ISAC system
a typical application scenario when RISs are needed or used.
Therefore, in our system, we assume that all the communicati on
users and radar targets are at the NLoS areas of the BS. We
carefully deploy the RIS to ensure that all the targets are in
LoS areas of the RIS.
To improve the spectral efﬁciency and reduce the system
load, we assume that the 2K users are grouped into K clusters
by employing user clustering techniques. As a result, there
are two types of users in each cluster, namely the RIS-
near user (RNU) and the RIS-far user (RFU). Generally, the
RNUs are much closer to the RIS than the RFUs. In each
cluster, the NOMA protocol is applied during transmission.
The cluster and user sets are denoted by K = {1,··· , K}
and U ={1,··· , 2K}, respectively. Moreover, denote by Uk
the set of users in cluster k, where U =∪k∈Uk, Uk∩ Uk =
⊘ (k, k∈K , k⁄= k). For notation simplicity, we denote the
RNU and RFU in the k-th cluster as user U (k, n) and user
U (k, f ), respectively.
A. Communication Model
The superimposed communication signal transmitted by the
BS is given by
x =
K∑
k=1
wk
(√ak,nsk,n +√ak,f sk,f), (1)
where wk ∈ CNT×1 is the active beamforming vector for
the k-th cluster, sk,i denotes the communication signal to
be sent to user U (k, i) with E
(
sHk,isk,i
)
= 1 , ak,i is the
corresponding power allocation coefﬁcient, i∈{ n, f}, k∈K .
Let G∈C M×NT and gk,i∈C M×1 be the channel coefﬁcients
of the communication links BS → RIS and RIS →U (k, i),
respectively. With the help of RIS, the signal received at us er
U (k, i) can be mathematically expressed as
yk,i =
(
gHk,iΘG) K∑
k=1
wk
(√ak,nsk,n +√ak,f sk,f) + zk,i,
(2)
where Θ = diag (v) is the RIS’s diagonal phase shift matrix,
v =
[
ejθ RIS1 ejθ RIS2 ··· ejθ RISM
]
is the passive beamforming vector
of the RIS with θRISm ∈ [0, 2π) denoting the phase shift of the
m-th reﬂecting element, m∈M , and zk,i∼CN
(
0, σ2) is the
additive white Gaussian noise (AWGN), M ={1, 2,··· , M}
is the reﬂecting elements set.
In the proposed RIS-NOMA-ISAC system, successive inter-
ference cancellation (SIC) is applied for the users to decod e
their signals in the same cluster. We assume a ﬁxed decoding
order in each cluster. Particularly, user U (k, n) ﬁrst decodes
the signal of user U (k, f ) and then subtracts this signal from
its observation to decode its own information. Therefore, t he
achievable rate for user U (k, n) to decode the signal of user
U (k, f ) is given by
Rk,f →n = log 2

1 + ak,f
⏐⏐⏐gHk,nΘGwk⏐⏐⏐2
I inerk,n + I iterk,n + σ2

 , (3)
where I inerk,n = ak,n
⏐⏐⏐gHk,nΘGwk⏐⏐⏐2 and I iterk,n =
∑K
~k⁄=k
⏐⏐⏐gHk,nΘGw~k⏐⏐⏐2.
If the above decoding is successful, then user U (k, n)
removes the signal sk,f from yk,n to further decode its own
signal sk,n. The corresponding individual achievable rate is
given by
Rk,n = log 2

1 + ak,n
⏐⏐⏐gHk,nΘGwk⏐⏐⏐2
I iterk,n + σ2

 . (4)
Accordingly, userU (k, f ) directly decodes its own signal by
treating the signal of user U (k, n) as interference. Therefore,
the achievable rate for user U (k, f ) to decode its own signal
can be expressed as
Rk,f →f = log 2

1 + ak,f
⏐⏐⏐gHk,f ΘGwk⏐⏐⏐2
I inerk,f + I iterk,f + σ2

 , (5)
where I inerk,f = ak,n
⏐⏐⏐gHk,f ΘGwk⏐⏐⏐2 and I iterk,f =
∑K
~k⁄=k
⏐⏐⏐gHk,f ΘGw~k⏐⏐⏐2.
As a result, the individual achievable rate of user U (k, f ) is
given by
Rk,f = min{Rk,f →n, Rk,f →f} . (6)B. Radar Detection Model
Since all the potential targets are in the NLoS ares of the
BS, NLoS links from the BS can be exploited to perform radar
target sensing. However, we can utilize the reﬂection-LoS l inks
created by the RIS to complete the sensing tasks. We consider
using the RIS’s beampattern gain as the sensing performance
metric. The reﬂected signal at the RIS can be expressed as
x = ΘG
( K∑
k=1
wk
(√ak,nsk,n +√ak,f sk,f)
)
. (7)
Therefore, the corresponding covariance matrix is given by
Rx = E
(
xxH) = ΘG
( K∑
k=1
wkwHk
)
GH ΘH . (8)
In our considered system, the communication signal is used
to perform radar target sensing, thus the RIS’s beampattern gain
with respect to the q-th interested angle, i.e, θTgq , is given by
PθTgq (wk, v) = aH(θTgq ) ΘG
( K∑
k=1
wkwHk
)
GH ΘH a(θTgq ) ,
(9)
where a (θ) =
[
1, ej 2πdλ sin(θ),··· , ej 2πdλ (M−1) sin(θ)]T is the
steering vector at the RIS with angle θ, d denotes the an-
tenna spacing, λ denotes the carrier wavelength, q ∈ Q≜
{1, 2,··· , Q}, and Qθ =
{
θTg1 , θTg2 ,··· , θTgQ
}
is the set of
interested sensing angles.

C. Maximize The Minimum Beampattern Gain
The objective of this paper is to maximize the minimum
beampattern gain towards Q interested angles by jointly op-
timizing the active beamforming and power allocation co-
efﬁcients at the BS, and the passive beamforming at the
RIS. Accordingly, the optimization problem is formulated a s
max
ak,wk,v
min
q∈Q
PθTgq (wk, v) , (10a)
s.t. R k,i /greaterorequalslant Rmink,i , (10b)
K∑
k=1
‖wk‖2 ⩽ Pmax, (10c)
ak,n + ak,f = 1, ak,i∈ (0, 1) , (10d)
θRISm ∈ [0, 2π) , (10e)
where Rmink,i is the minimum QoS requirement, Pmax is the
maximum transmit power at the BS, ak = [ ak,nak,f ]T , i∈
{n, f} , k∈K , m∈M .
III. P ROPOSED SOLUTION
In this section, we elaborate on how to solve problem (10).
We ﬁrst transform problem (10) into a more tractable form. To
facilitate the design, we deﬁne Wk = wkwHk , where Wk ≽ 0
and rank (Wk) = 1 , k∈K . Similarly, we deﬁne V = vvH ,
which satisﬁes V ≽ 0 and rank (V) = 1 . Then, the beampattern
gain in (9) can be rewritten as:
PθTgq (Wk, V) = Tr
[
VΥq
( K∑
K=1
Wk
)
ΥHq
]
, (11)
where Υq = diag
{
aH
(
θTgq
)}
G.
Moreover, the quadratic terms
⏐⏐⏐gHk,iΘGwk⏐⏐⏐2 and⏐⏐⏐gHk,iΘGw~k⏐⏐⏐2 in (3), (4) and (5) can be rewritten as:



⏐⏐⏐gHk,iΘGwk⏐⏐⏐2 = Tr(VΓk,iWkΓHk,i) ,⏐⏐⏐gHk,iΘGw~k⏐⏐⏐2 = Tr(VΓk,iW~kΓHk,i) , (12)
where Γk,i = diag
{
gHk,i
}
G, k⁄= ˜k.
By exploiting the above deﬁnitions, constraints in (10b) ca n
be equivalently reformulated as follows:
ak,nTr
(
VΓk,nWkΓHk,n) /greaterorequalslant rmink,n (I iterk,n + σ2) , (13)
ak,f Tr
(
VΓk,nWkΓHk,n) /greaterorequalslant rmink,f (I inerk,n + I iterk,n + σ2) , (14)
ak,f Tr
(
VΓk,f WkΓHk,f) /greaterorequalslant rmink,f (I inerk,f + I iterk,f + σ2) , (15)
where I inerk,n = ak,nTr(VΓk,nWkΓHk,n),
I inerk,f = ak,nTr(VΓk,f WkΓHk,f) and I iterk,i =∑K
~k⁄=k Tr
(
VΓk,iW~kΓHk,i
)
, rmink,i = 2 Rmink,i − 1, i∈{ n, f} ,
k∈K .
Furthermore, we introduce an auxiliary variable χ to trans-
form the nonsmooth objective function in problem (10) into a
smooth one. Finally, the original problem (10) can be recast
equivalently as follows:
max
χ>0,ak,Wk≽0,V≽0
χ, (16a)
s.t. Tr
[
VΥq
( K∑
k=1
Wk
)
ΥHq
]
/greaterorequalslant χ, (16b)
K∑
k=1
Tr (Wk) ⩽ Pmax, (16c)
[V]m,m = 1, (16d)
rank (Wk) = 1 , (16e)
rank (V) = 1 , (16f)
(10d), (13), (14), (15), (16g)
where i∈{ n, f} , k∈K , m∈M , q∈Q .
A. Joint Active Beamforming And Power Allocation Coefﬁ-
cients Optimization
In this subsection, we aim to optimize the active beamform-
ing and power allocation coefﬁcients by solving problem (16 )
with given passive beamforming matrix V. In particular, we can
obtain the optimal {Wk} and{ak} by solving the following
optimization problem:
max
χ>0,ak,Wk≽0
χ, (17a)
s.t. (10d), (13), (14), (15), (16b), (16c), (16e). (17b)
The difﬁculty to solve problem (17) is the nonconvex
constraints (13), (14), (15), and (16e). We ﬁrst handle con-
straint (13) by introducing a new slack variable ηk, then we
have {
ak,nTr (WkHk,n) /greaterorequalslant η2k, (18)
η2k /greaterorequalslant rmink,n (I iterk,n + σ2) , (19)
where Hk,n = ΓHk,nVΓk,n and I iterk,n =∑K~k⁄=k Tr(W~kHk,n).
Then, by applying the Schur complement theory [10], (18)
can be expressed in linear matrix inequality form
[ak,n ηk
ηk Tr (WkHk,n)
]
≽ 0,∃ηk > 0 (20)
Furthermore, by using the successive convex approximation
(SCA) approach based on First-order Taylor approximation,
(19) can be approximated as followed:
~η2k + 2~ηk (ηk− ~ηk) /greaterorequalslant rmink,n (I iterk,n + σ2) , (21)
where~ηk is a ﬁxed point and can be updated by ~η(t1)k = η(t1)k ,
t1 is the iteration index.
Next, we tackle the constraints (14) and (15). Substituting
ak,f = 1− ak,n into (14) and (15), we have:
rmink,f
(
Tr(WkHk,n)
rmink,f − I iterk,n− σ2
)
rmink,f + 1 /greaterorequalslant ak,nTr (WkHk,n) , (22)
rmink,f
(
Tr(WkHk,f )
rmink,f − I iterk,f − σ2
)
rmink,f + 1 /greaterorequalslant ak,nTr (WkHk,f ) , (23)

where Hk,f = ΓHk,f VΓk,f and I iterk,f =∑K~k⁄=k Tr(W~kHk,f).
We note that the functions ak,nTr (WkHk,n) and
ak,nTr (WkHk,f ) in (22) and (23) are nonconvex. To deal
with these non-convexity, we adopt the arithmetic-geometr ic
mean inequality [11]. Speciﬁcally, ak,nTr (WkHk,n) and
ak,nTr (WkHk,f ) can be approximated as
ak,nTr (WkHk,n) ⩽
βk,1a2k,n
2 + (Tr (WkHk,n))22βk,1 ≜Tk,1,
(24)
ak,nTr (WkHk,f ) ⩽
βk,2a2k,n
2 + (Tr (WkHk,f ))22βk,2 ≜Tk,2,
(25)
where βk,1 and βk,2 are ﬁxed points. The equality in (24)
and (25) will always hold if βk,1 = Tr(WkHk,n)ak,n and βk,2 =
Tr(WkHk,f )
ak,n .Based on the aforementioned transformations and approxi-
mations, constraints given in (22) and (23) can be approxima ted
as follows
rmink,f
(
Tr(WkHk,n)
rmink,f − I iterk,n− σ2
)
rmink,f + 1 /greaterorequalslantTk,1, (26)
rmink,f
(
Tr(WkHk,f )
rmink,f − I iterk,f − σ2
)
rmink,f + 1 /greaterorequalslantTk,2, (27)
Finally, let us turn our attention to the rank-one con-
straint (16e). To address this issue, we exploit the semideﬁ nite
relaxation (SDR) technique by removing the rank-one con-
straints from the problem formulation. As a result, the rela xed
problem is give as
max
χ>0,0<ak,n<1,Wk≽0
χ, (28a)
s.t. (16b), (16c), (20), (21), (26), (27). (28b)
In the following theorem, we will verify the tightness of the
SDR problem.
Theorem 1: If the relaxed problem (28) is feasible, then the
solutions{Wk} obtained by solving the problem (28) always
satisfy rank (Wk) ⩽ 1, k∈K .
Proof : Similar proof can be found in [11].
Theorem 1 represents the fact that we can obtain the rank-one
solutions of problem (17) by solving the convex problem (28) .
To facilitate the understanding of the proposed algorithm, we
summarize it in Algorithm 1 .
B. Passive Beamforming Optimization
For any given {Wk} and{ak}, the passive beamforming
optimization problem is given by
max
χ>0,V≽0
χ, (29a)
s.t. (13), (14), (15), (16b), (16d), (16f). (29b)
Now, the remaining non-convexity in problem (29) lies in
the rank-one constraint (16f). According to the sequential rank-
one constraint relaxation (SRCR) algorithm [12], the const raint
rank (V) = 1 can be transformed equivalently as:
eHmax
(
V(t2)
)
V emax
(
V(t2)
)
/greaterorequalslant ε(t2)Tr (V) , (30)
where V(t2) is the obtained solution in the t2-th iteration,
emax
(
V(t2)) is the eigenvector corresponding to the maximum
Algorithm 1 Proposed joint active beamforming and power
allocation coefﬁcients optimization algorithm
1: Initialize β(0)k,1, β(0)k,2,~η(0)k , k∈K , and set t1 = 0.
2: repeat
3: t1 = t1 + 1;
4: update W(t1)k , a(t1)k,n and η(t1)k by solving problem (28)
with given β(t1−1)k,1 , β(t1−1)k,2 ,~η(t1−1)k ;
5: update~η(t1)k = η(t1)k , β(t1)k,1 = Tr
(
W(t1 )k Hk,n )
a(t1 )k,n and β(t1)k,2 =
Tr
(
W(t1 )k Hk,f )
a(t1 )k,n ;
6: until the objective value of problem (28) converge.
7: Output: Wk and ak, k∈K .
eigenvalue of V(t2), ε(t2) ∈ [0, 1] is a relaxation parameter
in the t2-th iteration. We can increase ε(t2) from 0 to 1
sequentially via iterations to gradually approach a rank-o ne
solution. After each iteration, the relaxation parameter c an be
updated as
ε(t2+1)←− min
(
1, λmax
(
V(t2+1))
Tr
(
V(t2+1)) + ρ(t2+1)
)
, (31)
where λmax
(
V(t2)) is the largest eigenvalue of V(t2) and ρ(t2)
denotes the step size.
As a result, in the t2-th iteration, the optimization problem
that needs to be solved is given as follows
max
χ>0,V≽0
χ, (32a)
s.t. (13), (14), (15), (16b), (16d), (30). (32b)
Problem (32) is a semideﬁnite program (SDP) problem and
can be solved by the CVX tool [13]. The procedure for
optimizing passive beamforming is sketched in Algorithm 2 .
Algorithm 2 Proposed passive beamforming optimization al-
gorithm
1: Initialize V(0) and ρ(0). Set ε(t2) = 0 and t2 = 0.
2: repeat
3: Solve problem (32) with
{
ε(t2), V(t2)} to obtain V∗;
4: if problem (32) is solvable
5: Update V(t2+1) = V∗;
6: Update ρ(t2+1) = ρ(0);
7: else
8: Update V(t2+1) = V(t2);
9: update ρ(t2+1) = ρ(t2)2 ;
10: end
11: Update ε(t2+1) via (31);
12: Update t2 = t2 + 1;
13: until
Tr(V(t2))
λmax(V(t2 )) is below a predeﬁned threshold and the
objective value of problem (32) converges.
14: Output: V.
C. Proposed Algorithm, Complexity and Convergence
To facilitate the understanding of the proposed
algorithm for solving problem (16), we summarize it in

Fig. 2: The simulated RIS-NOMA-ISAC system geometry
Algorithm 3 . The convergence of Algorithm 3 is analyzed
as follows. Algorithm 1 and Algorithm 2 converge to a
KKT stationary solution of problem (17) and problem (29),
respectively, which has been proved in [11] and [12]. In
addition, the objective value of problem (16) is non-decrea sing
after each iteration and the radar beampattern gain is upper
bounded. Therefore, the proposed algorithm is guaranteed t o
converge. The complexities of Algorithm 1 and Algorithm 2
are O
(
T max1
(
max{Ncont, NT}4√NT log 1̟1))
and O
(
T max2
(
max{Ncont + 1, M}4√M log 1̟2)),
respectively, where ̟1 and ̟2 are the solution
accuracies, T max1 and T max2 are the number of iterations,
Ncont = 3K + Q + 1. The whole complexity of Algorithm 3 is
O

T max3

 T max1
(
max{Ncont, NT}4√NT log 1̟1) +
T max2
(
max{Ncont, M}4√M log 1̟2)



,
where T max3 is the number of iterations for Algorithm 3 .
Algorithm 3 Proposed joint optimization algorithm
1: Initialize V(0) and set t3 = 0.
2: repeat
3: t3 = t3 + 1;
4: update W(t3)k and a(t3)k by Algorithm 1 with V(t3−1);
5: update V(t3) by Algorithm 2 with W(t3)k and a(t3)k ;
6: until the objective value of problem (16) converges.
7: Output: Wk, ak, and V, k∈K .
IV. S IMULATION RESULTS
In this section, the performances of the proposed algorithm
for RIS-NOMA-ISAC system are evaluated through numerical
simulations. The simulated RIS-NOMA-ISAC system geometry
is shown in Fig. 2. We assume that there are three clusters
and three radar targets. The RIS is located in the origin of th e
coordinate, while the BS is located at (−40, 10) meter (m). In
each cluster, the RNU and the RFU are randomly distributed on
the half circles centered at (0, 0) m with radius of rk,n and rk,f ,
respectively, where rk,n ∈ [20, 25] m and rk,f ∈ [80, 85] m.
Let θk,i denote the angle from the RIS to user U (k, i) and
we further assume that {θ1,i} in cluster 1, {θ2,i} in cluster 2,
and{θ3,i} in cluster 3, are randomly distributed in the angle
ranges (−30o,−20o], (20o, 30o], and (60o, 70o], respectively,
i∈{ n, f}. Without loss of generality, let θk,n = θk,f , k∈K .
The angle from the RIS to the three targets are set to −45o, 0o
-90 -80 -70 -60 -50 -40 -30 -20 -10 0 10 20 30 40 50 60 70 80 90
Angle (degree)
0
0.1
0.2
0.3
0.4
0.5
0.6
0.7
0.8
0.9
1
normalized beampattern gain
 M=30
 M=36
Desired
Fig. 3: Obtained beampattern gain with NT = 9
Fig. 4: Illumination power of the RIS with NT = 9 and
M = 30.
and 45o, and the corresponding radius are set to 90 m, 90 m
and 80 m, respectively. With the angles of sensing targets, the
desired beampattern can be deﬁned as
P (θ) =
{
1, θT− ∆θ2 ⩽ θ ⩽ θT + ∆θ2 , θT∈{− 45o, 0o, 45o} ,
0, otherwise,
(33)
where ∆θ = 6 o is the desired beam width, θ is
the element of angle grid
[
− π2 : π100 : π2], and the in-
terested sensing angle set can be deﬁned as Qθ ={
θ|θT− ∆θ2 ⩽ θ ⩽ θT + ∆θ2 , θT∈{− 45o, 0o, 45o}}.
All the channels follow the Rician fading, which can be
modeled as in [14]. The path loss at a reference distance of
one meter is set to −30 dB, the path loss exponents are set
to 2.2, the Rician factors are set to 3, the noise power is set
to−90 dBm, the normalized spacing between two adjacent
antennas(elements) is set as dλ = 0 .5. The minimum QoS
requirement for RNUs and RFUs are set to Rmink,n = 0 .5
bits/s/Hz and Rmink,f = 0.1 bits/s/Hz, respectively. The maximum
transmit power is set to 35 dBm.
In Fig. 3, we plot the normalized beampattern gain obtained
over one random channel realization. The desired beampatte rn
gain is obtained via (33). As illustrated in Fig. 3, the propo sed
scheme can achieve the dominant peaks of the beampattern
gain in the angles of interest, i.e., −45o, 0o and 45o. Moreover,
at the target directions, the achievable beampattern gains for
M = 36 are always higher than that for M = 30 , which
implies that the performance of the proposed scheme can be
improved by increasing the number of the RIS elements. In
Fig. 4, we show that the normalized illumination power [15]
of the RIS on different angles and locations over one random

24 28 32 36
Number of RIS reflecting elements: M
3
4
5
6
7
8
9
10
11
12Minimum Beampattern gain
10-4
RIS-ISAC
RIS-NOMA-ISAC
RIS-ISAC
RIS-NOMA-ISAC
Overloaded: NT=3
Underloaded: NT=9
Fig. 5: Obtained minimum beampattern gain by different
schemes
channel realization. From Fig. 4, we can see that there are th ree
brightest region towards the target directions. This is int uitive
since the RIS attempts to steer both the active and passive
beamforming towards the targets to maximize the minimum
beampattern.
To evaluate the performance of the proposed RIS-
NOMA-ISAC system, the RIS assisted conventional ISAC
(RIS-ISAC) system without NOMA is considered. The
achievable rate of user k can be obtained by: Rk =
log2
(
1 + |gHk ΘGwk|2∑2K
i⁄=k|gHi ΘGwk|2+σ2
)
, where gk is the channel co-
efﬁcients from the RIS to user k, k∈{ 1, 2,··· , 2K}. The joint
active and passive beamforming optimization problem for RI S-
ISAC system can also be solved by our proposed algorithms.
In Fig. 5, we compare the minimum beampattern gain obtained
by the RIS-NOMA-ISAC and RIS-ISAC systems versus M .
The results are obtained over 100 random channel realizatio ns.
First, it is observed that the achievable minimum beampat-
tern gain monotonically increases with M . This is expected
since more reﬂecting elements can provide higher possible
beamforming gain towards the radar targets, thereby increa sing
beampattern gain. Second, the proposed RIS-NOMA-ISAC
system outperforms the RIS-ISAC system under overloaded
and underloaded cases. This is because the RIS-NOMA-ISAC
system can mitigate the inter-user interference by SIC and
provide more degrees of freedoms. for radar sensing. Howeve r,
the RIS-ISAC system cannot well mitigated the inter-user
interference. Fig. 6 compares the beampattern gain obtaine d by
different systems. We observe that the beampattern gain of a ll
schemes have peaks towards target directions and our propos ed
RIS-NOMA-ISAC system has a stronger peak compared with
the RIS-ISAC system. On the other hand, the proposed scheme
can obtain higher beampattern gains at the worst angles.
V. CONCLUSIONS
We have proposed a novel RIS-NOMA-ISAC system, where
the RIS is deployed to serve the communication users and
assist radar sensing. A joint optimization problem over ac-
tive beamforming, power allocation coefﬁcients, and passi ve
beamforming was formulated with the aim of maximizing the
minimum beampattern gain. Due to the nonconvex nature of
the formulated problem, an alternating optimization based algo-
rithm was proposed to solve the original problem. Simulatio n
-90 -80 -70 -60 -50 -40 -30 -20 -10 0 10 20 30 40 50 60 70 80 90
Angle (degree)
0.2
0.4
0.6
0.8
1
1.2
1.4
1.6
1.8
2
Beampattern gain
10-3
RIS-ISAC: NT=9
RIS-NOMA-ISAC: NT=9
RIS-ISAC: NT=3
RIS-NOMA-ISAC: NT=3
44 45 46
4.5
5
5.5
6
6.5
10-4
Fig. 6: Obtained beampattern gain by different systems with
M = 36
results were presented to demonstrate the superiority of th e
proposed RIS-NOMA-ISAC system.
REFERENCES
[1] J. A. Zhang, M. L. Rahman, K. Wu, X. Huang, Y . J. Guo, S. Chen ,
and J. Y uan, “Enabling joint communication and radar sensin g in mobile
networks—a survey,” IEEE Commun. Surv. Tut. , vol. 24, no. 1, pp. 306–
345, Oct. 2022.
[2] Z. Gao, Z. Wan, D. Zheng, S. Tan, C. Masouros, D. W. K. Ng, an d
S. Chen, “Integrated sensing and communication with mmwave massive
mimo: a compressed sampling perspective,” 2022, [Online]. Available:
https://arxiv.org/abs/2201.05766.
[3] C. Chaccour, W. Saad, O. Semiari, M. Bennis, and P . Popovs ki, “Joint
sensing and communication for situational awareness in wir eless THz
systems,” 2021, [Online]. Available: https://arxiv.org/ abs/2111.14044.
[4] L. Y ou, X.-H. Qiang, C. G. Tsinos, F. Liu, W. Wang, X. Gao, a nd B. E.
Ottersten, “Beam squint-aware integrated sensing and comm unications for
hybrid massive MIMO LEO satellite systems,” 2022, [Online] . Available:
https://arxiv.org/abs/2203.00235.
[5] Z. J. Wang, Y . Liu, X. Mu, Z. Ding, and O. A. Dobre, “NOMA em-
powered integrated sensing and communication,” IEEE Commun. Lett. ”,
vol. 26, no. 3, pp. 677–681, March 2022.
[6] Z. J. Wang, Y . Liu, X. Mu, and Z. Ding, “NOMA inspired inter ference
cancellation for integrated sensing and communication,” 2 021, [Online].
Available: https://arxiv.org/abs/2206.00377.
[7] X. Mu, Y . Liu, L. Guo, J. Lin, and L. H. Hanzo, “NOMA-aided j oint
radar and multicast-unicast communication systems,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1978–1992, June 2022.
[8] C. Zhang, W. Yi, Y . Liu, and L. H. Hanzo, “Semi-integrated -sensing-and-
communication (semi-ISaC): From OMA to NOMA,” 2022, [Onlin e].
Available: https://arxiv.org/abs/2204.11245.
[9] X. Song, D. Zhao, H. Hua, T. X. Han, X. Y ang, and J. Xu, “Join t trans-
mit and reﬂective beamforming for IRS-assisted integrated sensing and
communication,” 2022 IEEE Wireless Communications and Networking
Conference (WCNC), pp. 189–194, 2022.
[10] X. Xie, F. Fang, and Z. Ding, “Joint optimization of beam forming, phase-
shifting and power allocation in a multi-cluster IRS-NOMA n etwork,”
IEEE Trans. V eh. Technol., vol. 70, no. 8, pp. 7705–7717, Aug. 2021.
[11] X. Sun, N. Y ang, S. Y an, Z. Ding, D. W. K. Ng, C. Shen, and Z. Zhong,
“Joint beamforming and power allocation in downlink NOMA mu ltiuser
MIMO networks,” IEEE Trans. Wireless Commun. , vol. 17, no. 8, pp.
5367–5381, Aug. 2018.
[12] P . Cao, J. S. Thompson, and H. V . Poor, “A sequential cons traint relax-
ation algorithm for rank-one constrained problems,” 2017 25th European
Signal Processing Conference (EUSIPCO) , pp. 1060–1064, 2017.
[13] M. Grant and S. Boyd, “CVX: Matlab software for discipli ned convex
programming, version 2.1,” http://cvxr.com/cvx, Mar. 201 4.
[14] Y . Li, M. Jiang, Q. Zhang, and J. Qin, “Joint beamforming design
in multi-cluster MISO NOMA reconﬁgurable intelligent surf ace-aided
downlink communication networks,” IEEE Trans. Commun. , vol. 69,
no. 1, pp. 664–674, Jan. 2021.
[15] R. S. P . Sankar, S. P . Chepuri, and Y . C. Eldar, “Beamform ing in inte-
grated sensing and communication systems with reconﬁgurab le intelligent
surfaces,” 2022, [Online]. https://arxiv.org/abs/2206. 07679.