---
type: literature-fulltext
title: "Wireless Communication for Low-Altitude Economy With UAV Swarm Enabled Two-Level Movable Antenna System"
zotero_key: "LIN2N6PE"
pdf_key: "PESLRHSR"
doi: "10.1109/TWC.2026.3689048"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Wireless Communication for Low-Altitude Economy With UAV Swarm Enabled Two-Level Movable Antenna System.md"
fulltext_path: "03fulltext/备选讲组会论文/LIN2N6PE.md"
zotero_item: "zotero://select/library/items/LIN2N6PE"
zotero_pdf: "zotero://open-pdf/library/items/PESLRHSR"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Wireless Communication for Low-Altitude Economy With UAV Swarm Enabled Two-Level Movable Antenna System

> PDF 原文逐页文本抽取；来源文件 SHA-256：`9b22cf8684ff46dbf413f9573d80bed2d390d70e21b6cd5f6f9665a2e0d340cb`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 16463
Wireless Communication for Low-Altitude
Economy With UA V Swarm Enabled
Two-Level Movable Antenna System
Haiquan Lu
 , Member , IEEE, Yong Zeng
 , Fellow, IEEE, Shaodan Ma
 , Senior Member , IEEE,
Bin Li
 , Senior Member , IEEE, Shi Jin
 , Fellow, IEEE, and Rui Zhang
 , Fellow, IEEE
Abstract—Unmanned aerial vehicle (UA V) is regarded as a key
enabling platform for low-altitude economy, due to its advantages
such as three-dimensional (3D) maneuverability, ﬂexible deploy-
ment, and line-of-sight (LoS) air-to-air/ground communication
links. In particular, the intrinsic high mobility renders UA V
especially suitable for operating as a movable antenna (MA) from
the sky. In this paper, by exploiting the ﬂexible mobility of UA V
swarm and antenna position adjustment of MA, we propose a
novel UA V swarm enabled two-level MA system, where UA Vs not
only individually deploy a local MA array, but also form a larger-
scale MA system with their individual MA arrays via swarm
coordination. We formulate a general optimization problem to
maximize the minimum achievable rate over all ground user
equipments (UEs), by jointly optimizing the 3D UA V swarm
placement positions, their individual MAs’ positions (or local
positions), and receive beamforming for different UEs. To gain
useful insights, we ﬁrst consider the special case where each UA V
has only one antenna, under different scenarios of one single
Received 24 May 2025; revised 19 September 2025 and 14 February
2026; accepted 24 April 2026. Date of current version 6 May 2026. The
work of Yong Zeng was supported in part by the National Natural Science
Foundation of China under Grant 62571116 and in part by the Mobile
Information Networks-National Science and Technology Major Project under
Grant 2025ZD1304500. The work of Shaodan Ma was supported in part
by the Science and Technology Development Fund, Macau, under Grant
0114/2025/AMJ, Grant 0020/2025/RIB1, Grant 001/2024/SKL, and Grant
0002/2025/EQP; and in part by the Research Committee of University
of Macau under Grant MYRG-GRG2025-00143-IOTSC. The work of Rui
Zhang was supported in part by the National University of Singapore under
Grant A-8003646-00-00 and Grant A-8003676-00-00, in part by the National
Natural Science Foundation of China under Grant 62331022, and in part
by Guangdong Major Project of Basic and Applied Basic Research under
Grant 2023B0303000001. An earlier version of this paper was presented in
part at the 2025 IEEE ICCC Workshop, Shanghai, China, in August 2025
[DOI: 10.1109/ICCCWorkshops67136.2025.11148194]. The associate editor
coordinating the review of this article and approving it for publication was
M. Kaneko. (Corresponding author: Yong Zeng.)
Haiquan Lu is with the School of Electronic and Optical Engineering,
Nanjing University of Science and Technology, Nanjing 210094, China
(e-mail: haiquanlu@njust.edu.cn).
Yong Zeng is with the National Mobile Communications Research
Laboratory, Southeast University, Nanjing 210096, China, and also
with Purple Mountain Laboratories, Nanjing 211111, China (e-mail:
yong zeng@seu.edu.cn).
Shaodan Ma is with the State Key Laboratory of Internet of Things for
Smart City and the Department of Electrical and Computer Engineering,
University of Macau, Macau, China (e-mail: shaodanma@um.edu.mo).
Bin Li is with the School of Aeronautics and Astronautics, Sichuan
University, Chengdu, Sichuan 610065, China (e-mail: bin.li@scu.edu.cn).
Shi Jin is with the School of Information Science and Engineering,
Southeast University, Nanjing 210096, China (e-mail: jinshi@seu.edu.cn).
Rui Zhang is with the Department of Electrical and Computer Engi-
neering, National University of Singapore, Singapore 117583 (e-mail:
elezhang@nus.edu.sg).
Digital Object Identiﬁer 10.1109/TWC.2026.3689048
UE, two UEs, and arbitrary number of UEs. In particular, for
the two-UE case, we derive the optimal UA V swarm placement
positions in closed-form that achieves inter-UE interference (IUI)-
free communication when the uniform plane wave (UPW) model
holds, where the UA V swarm forms a uniform sparse array
(USA) satisfying minimum safe distance constraint. While for
the general case with arbitrary number of UEs, we propose
an efﬁcient alternating optimization algorithm to solve the
formulated non-convex optimization problem. Then, we extend
the results to the case where each UA V is equipped with multiple
antennas. Numerical results verify that the proposed low-altitude
UA V swarm enabled MA system signiﬁcantly outperforms various
benchmark schemes, thanks to the exploitation of two-level
mobility to create more favorable channel conditions for multi-
UE communications.
Index Terms—Low-altitude economy, UA V swarm, movable
antenna (MA), multi-user communication, array geometry, place-
ment optimization.
I. I NTRODUCTION
L
OW-ALTITUDE economy has emerged as a new inte-
grated economic form, involving assorted low-altitude
activities within sub-1,000-meter airspace domains [2], [3].
By leveraging manned/unmanned aerial vehicles (UA Vs),
and electric vertical take-off and landing (eVTOL) air-
crafts, low-altitude economic ecosystems begin to ﬂourish,
which encompass a wide range of applications like logistics
and delivery, agricultural plant protection, cultural tourism,
environmental monitoring, and so on. In particular, bene-
ﬁting from the advantages such as three-dimensional (3D)
maneuverability, ﬂexible deployment, and line-of-sight (LoS)
air-to-air/ground communication links, UA V is regarded as
an indispensable part of the low-altitude economy, which
has driven various applications in wireless communication
and sensing [4], [5], [6]. Speciﬁcally, from the perspective
of wireless communication, there exist two paradigms, i.e.,
UA V-assisted wireless communication and cellular-connected
UA V communication [7]. For example, UA V equipped with
a base station (BS) or relay can be deployed on demand to
assist in the conventional cellular wireless networks, so as to
satisfy the ubiquitous connectivity required by the future sixth-
generation (6G) wireless network. Extensive research efforts
have been devoted to this direction, including UA V channel
and energy consumption modeling, performance analysis, and
placement/trajectory design [4], [5]. On the other hand, the
role of UA V can be shifted from the aerial BS/relay to aerial
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

16464 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
user equipments (UEs), thus enabling a new paradigm where
both the ground and aerial UEs coexist in future wireless
networks [4], [7], [8]. Moreover, as integrated sensing and
communication (ISAC) has been identiﬁed as one of the six
major usage scenarios for 6G [9], research on ISAC with
UA V has gained a surge of interest recently [10], [11], [12].
Similarly, UA V can act as an aerial anchor for providing the
ISAC service from the sky, or an aerial target to be sensed [6].
However, UA Vs are subject to various practical constraints
in terms of size, weight, dynamics, and power, rendering a
single UA V challenging to execute sophisticated communica-
tion or sensing missions [4], [13], [14], [15], [16]. To tackle
this issue, UA V swarm, i.e., a group of coordinated UA Vs,
can cooperatively accomplish sophisticated tasks, e.g., large-
scale data collection and environment monitoring. Compared
to single UA V , UA V swarm is able to signiﬁcantly improve
the overall payload capability and expand the communication
and sensing coverage area. Moreover, the cooperative mecha-
nism helps to reduce the task completion time and offers an
enhanced robustness against anomalies or failures than single
UA V , since the task of any malfunctioning UA V can be trans-
ferred to its neighboring functioning UA Vs [17]. Given the
above promising advantages, extensive research endeavours
have been devoted to UA V swarm assisted communication and
sensing. For example, in [18], an efﬁcient channel estimation
and self-positioning approach was proposed for UA V swarm
communication with unknown displacements among UA Vs.
The authors in [19] proposed a 3D irregular terrain area
coverage scheme with UA V swarm, and the results show that
the proposed scheme can cover the area with little redundancy.
Besides UA V swarm assisted communication, recent research
works have studied the integration of ISAC with UA V swarm,
since the LoS-dominating channel is particularly favorable
for sensing [6]. Research on UA V swarm ISAC involves
various performance metrics, including signal-to-interference-
plus-noise ratio (SINR) and achievable rate for communication
[3], [12], radar mutual information [20] and Cram ´er-Rao
lower bound (CRLB) for sensing [11], [12], [21]. Despite
the promising advantages, UA V swarm also involves several
issues, such as the latency caused by information exchange
among UA Vs, complex collision avoidance planning, and high-
precision localization and sensing for UA V swarm regulation
[13], [22]. In particular, to tackle the challenge of accurately
localizing and sensing the densely located swarm UA Vs,
a super-resolution communication and sensing method was
proposed for UA V swarm in [22].
It is worth mentioning that the inherent ﬂexible mobility
of UA V renders it particularly suitable for operating as a
movable antenna (MA) [23], [24], [25], [26], [27], [28], [29],
[30], [31], [32] or ﬂuid antenna system (FAS) [33], [34]
from the sky. For example, each UA V may be equipped
with a single or multiple antennas, and a ﬂexible antenna
array architecture can be enabled via adjusting the UA V
swarm topology. In contrast to conventional ﬁxed-position
antenna (FPA) where inter-antenna spacing is usually ﬁxed
as half wavelength, MA dynamically adjusts the antenna
position via mechanical and/or electrical control, so as to
pursue a favorable channel condition and circumvent the
deep fading scenario [23], [33]. This thus achieves perfor-
mance improvement with optimized antenna positions, which
may be a complement to extremely large-scale multiple-input
multiple-output (MIMO) technique whereby the spectral efﬁ-
ciency and spatial resolution are signiﬁcantly enhanced via
the orders-of-magnitude scaling of antennas [35], [36]. Sub-
sequently, antenna mobility is extended to a more general
concept, where both the antenna position and rotation can
be ﬂexibly adjusted, i.e., six-dimensional movable antenna
(6DMA) [29], [30], [31], [32]. Driven by such new design
degrees of freedom (DoFs), a large body of literature focuses
on this technology and demonstrates its performance gain in
communication outage probability, spectral efﬁciency and net-
work capacity, as well as sensing accuracy (see [26], [32], [34]
and references therein). Besides active MA, the authors in [37]
further proposed a new ﬂexible passive reﬂector architecture,
enabling the ﬂexible beamforming direction adjustment via
reﬂector placement and rotation angle optimization.
Note that compared to MAs, UA Vs possess even more
ﬂexible and wider-range movement, and thus an interesting
new idea is to utilize UA V swarm to form MA array. Moreover,
different from existing research on MA that only optimizes
antenna positions, UA V swarm enabled MA can fully unlock
its mobility advantage, where the array geometry is able to
be dynamically reconﬁgured via trajectory optimization, thus
yielding a varying array geometry. Preliminary efforts have
been devoted to the single UA V-mounted MA[38], [39], [40],
[41]. Speciﬁcally, a directional MA was mounted on a UA V
to minimize the total data collection time in a backscatter
sensor network in [38]. In [39] and [40], the authors utilized
the single UA V-mounted MA array to facilitate the minimum
beamforming gain for secondary users (SUs) and enhance the
sum rate of all UEs, respectively. In [41], the 6DMA was
deployed at the single UA V to mitigate the interference caused
by the co-channel terrestrial transmissions. Besides the active
antenna, the authors in [42] utilized the single UA V-mounted
passive 6DMA, i.e., by carrying an intelligent reﬂecting sur-
face (IRS) on a UA V[43], to maximize the minimum received
signal-to-noise ratio (SNR) among all UEs. Nevertheless, these
works neither take into account the UA V swarm scenario, nor
explore the capability of MA system enabled by UA V swarm.
Meanwhile, it is also worth pointing out that the UA V swarm
enabled MA system may face several practical challenges,
such as the limited endurance of UA V swarm due to the ﬁnite
onboard battery, positional inaccuracy, array misalignment,
orientation jitter, and synchronization issues, which deserve
further investigations.
In this paper, motivated by the inherent mobility of UA V
swarm and antenna position adjustment of MA, we propose a
novel UA V swarm enabled two-level MA system. Speciﬁcally,
by individually deploying a local MA array on each UA V ,
all the spatially distributed UA Vs cooperatively construct a
larger-scale MA system according to their topology. Compared
to existing MA systems, UA V swarm enabled MA system
involves the dual-scale antenna spatial movement, i.e., the
small-scale antenna movement within each local MA array,
e.g., at wavelength level, and the large-scale UA V movement,
so as to better harness the spatial variations of wireless chan-
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16465
nels in different scales. In particular, the UA V swarm enabled
MA system can be deployed on demand, which is appealing
for assorted application scenarios, such as information dis-
semination and data collection, data ofﬂoading in hotspot
areas, and rapid communication restoration after infrastructure
failure [4]. Moreover, beneﬁting from the desired LoS air-to-
air/ground links, UA V swarm enabled MA system can provide
the ISAC service efﬁciently, so as to support low-altitude
economy applications such as logistics and delivery as well
as environmental monitoring. In this paper, by considering
low-altitude UA V swarm enabled uplink multi-UE commu-
nication, we aim to maximize the minimum achievable rate
over all ground UEs. The main contributions of this paper are
summarized as follows.
• First, we propose a novel low-altitude UA V swarm
enabled two-level MA system, where each UE channel
depends on both UA V swarm placement positions and
their mounted MA array positions. Subject to the min-
imum safe distance constraint for UA Vs [4], as well as
mutual coupling avoidance constraint for UA V-mounted
MA array, we formulate an optimization problem to
maximize the minimum achievable rate over all ground
UEs, by jointly optimizing the 3D UA V swarm placement
positions, their individual MAs’ positions, and receive
beamforming for all UEs.
• Second, to gain useful insights, we consider the special
case of single-antenna UA V . It is shown that for the single
UE communication, the resulting SNR after applying the
optimal maximal-ratio combining (MRC) beamforming
only depends on the number of UA Vs, irrespective of their
array geometry. Then, for the two-UE communication,
we derive the optimal UA V swarm placement positions
that achieves the maximum communication rate without
suffering any inter-UE interference (IUI) when the uni-
form plane wave (UPW) model holds. The result shows
that under the minimum safe distance constraint, UA V
swarm forms a uniform sparse array (USA) [44] for the
IUI-free communication. Moreover, for arbitrary number
of UEs, we propose an efﬁcient alternating optimization
algorithm to solve the highly non-convex problem, where
the optimal receive beamforming is derived in closed-
form for given UA V swarm placement positions, and for
given receive beamforming, the UA V swarm placement
optimization problem can be solved via the successive
convex approximation (SCA) technique [4].
• Last, we consider the general case of multi-antenna UA V ,
where each antenna can move independently within the
speciﬁed region at its mounted UA V . For the single and
two-UE communications, similar results can be obtained
as in the scenario of single-antenna UA V . In particular,
we also consider the special case where all the UA Vs
adopt the USA [45], the IUI-free communication can
be achieved in the two-UE case via joint UA V place-
ment positions and sparsity level adjustment. Next, the
alternating optimization method is applied to solve the
problem with arbitrary number of UEs. Subsequently, we
extend the analysis to the practical case by considering
synchronization and position errors, where a channel
Fig. 1. Wireless communication with a low-altitude UA V swarm enabled
two-level MA system.
estimation-based error compensation scheme is proposed.
Numerical results are presented to validate the superior
performance of the proposed UA V swarm enabled MA
system over various benchmarks, thanks to the two-level
mobility to create more favorable channel conditions.
The remainder of the paper is organized as follows. Sec-
tion II presents the system model of a low-altitude UA V swarm
enabled MA system and formulates the problem to maxi-
mize the minimum achievable rate among UEs. Section III
considers the special case of single-antenna UA V , and the
result is extended to the general case of multi-antenna UA V in
Section IV. Section V presents the numerical results to validate
the performance of UA V swarm enabled MA systems. Finally,
we conclude the paper in Section VI.
Notations: Scalars are denoted by italic letters. Vectors
and matrices are denoted by bold-face lower- and upper-case
letters, respectively. The spaces of M×N complex-valued
matrices are denoted as CM×N . For a vector x,‖x‖ denotes
its Euclidean norm. For an arbitrary-size matrix A, its complex
conjugate, transpose, and Hermitian transpose are denoted by
A∗, AT , AH, respectively. The spectral norm and Frobenius
norm of A are denoted as ‖A‖2 and ‖A‖F , respectively.
The distribution of a circularly symmetric complex Gaussian
random vector with mean x and covariance matrix Σ is
denoted asCN (x, Σ), and∼ stands for “distributed as”. For
a complex-valued number x, Re{x} represents its real part.
mod(a,b) represents the integer modulo operation, which
returns the remainder after division of a by b. The symbol j
denotes the imaginary unit of complex numbers, with j2 =−1.
O (·) denotes the standard big-O notation.
II. S YSTEM MODEL AND PROBLEM FORMULATION
As illustrated in Fig. 1, we consider a low-altitude UA V
swarm enabled wireless communication system, where L
UA Vs cooperatively serveK single-antenna ground UEs. Each
UA V is equipped with a linear MA array with M antenna
elements, while a ﬂexible two-level MA system is formed
by dynamically moving each UA V and the positions of its
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

16466 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
individual MAs. Without loss of generality, we consider a 3D
Cartesian coordinate system, where the location of UE k is
denoted as wk = [xk,yk, 0]T , k∈K , with K≜ [1,··· ,K ].
Let the ﬁrst antenna be the reference point for each UA V ,
with the coordinate of UA V l denoted as ¯ ql = [¯xl, ¯yl,¯zl]T ,
1≤l≤L. Moreover, the coordinate of antenna m for UA Vl
is ¯ ql,m = ¯ ql+bl,m, where bl,m≜ [bl,m, 0, 0]T and we assume
bl,1 = 0,∀l, without loss of generality. As such, the position
of antenna m can be dynamically changed by adjusting bl,m
for UA Vl. This thus enables a two-level MA system, realized
by the joint control of UA Vs’ movement and their individual
antennas’ movement.
Let qr = [x r,yr, zr]T denote the reference location
for the L UA Vs. Let κk = [Φ k, Ψk, Θk]T denote
the wave propagation direction from UE k to qr, with
Φk ≜ sinθk cosφk, Ψk ≜ sinθk sinφk, and Θk ≜ cosθk,
respectively, where θk and φk denote the elevation and
azimuth angles of arrival (AoAs), respectively, as illustrated
in Fig. 1. Moreover, let ql = [xl,yl, zl]T denote the position
of UA Vl relative to the reference point qr, and it follows
that ¯ ql = qr + ql. Similarly, we have ¯ ql,m = qr + ql,m, with
ql,m = ql + bl,m denoting the position of antenna m for
UA Vl relative to the reference point qr. We assume that each
UA V knows its relative position to the reference point, which
can be obtained via satellite-based localization systems, e.g.,
global positioning system (GPS) or Beidou.
In practice, the minimum safe distance constraints need to
be satisﬁed by UA Vs, which is given by [4]
‖ql− ql′‖≥ dmin, ∀l,l′⁄=l, (1)
where dmin denotes the minimum distance to guarantee the
safe operation between UA Vs. Besides, to avoid the mutual
coupling between adjacent MA elements at each UA V , the
minimum distance ˜dmin is required, which yields the following
constraints,
‖‖ql,m− ql,m′‖‖ =|bl,m−bl,m′|≥ ˜dmin,∀l,m,m′⁄=m,
(2)
where ˜dmin is in practice much smaller than dmin.
Note that the communication links between UA Vs and
ground UEs are of high probability to be over LoS chan-
nels in practice. We consider the general near-ﬁeld spherical
wavefront model for the channels between UA Vs and ground
UEs, which includes the far-ﬁeld UPW model as a special
case. Meanwhile, the signals from UE to the local MA array
of each UA V can be well approximated as UPW, since the
movable region of the local MA array is much smaller than
the link distance. Let κk,l = [Φk,l, Ψk,l, Θk,l]T denote the
wave propagation direction from UE k to ¯ ql, where Φk,l =
sinθk,l cosφk,l, Ψk,l = sinθk,l sinφk,l, and Θk,l = cosθk,l,
with θk,l and φk,l being the elevation and azimuth AoAs,
respectively. For UA V l, the difference of the wavefront
propagation distance between ¯ ql and ¯ ql,m for UE k is
ϕk
(
¯ ql,m
)
=κTk,l(¯ ql,m− ¯ ql) =κTk,lbl,m = Φk,lbl,m, (3)
which is the projection length of the vector
(
¯ ql,m− ¯ ql
)
onto
the wave propagation direction vector κk,l. Then, the receive
array response vector of UA Vl for UE k is given by [36]
ak,l
({
¯ ql,m,∀m
})
=e−j 2πλ rk,l×
[
e−j 2πλ ϕk(¯ ql,1),··· ,e−j 2πλ ϕk(¯ ql,M)]T, (4)
whererk,l =‖¯ ql− wk‖ denotes the link distance between ¯ ql
and wk. By applying the second-order Taylor approximation,
we have
rk,l≈rsecondk,l ≜rk +xlΦk +ylΨk + zlΘk+
x2l +y2l + z2l− (xlΦk +ylΨk + zlΘk)2
2rk
, (5)
where rk =‖wk− qr‖ denotes the distance between qr and
wk.
Moreover, the L UA Vs cooperate to form an LM-element
distributed antenna array, and thus the channel from UE k to
the UA V swarm enabled MA system is 1
hk
({
¯ ql,m,∀l,m
})
=αkak
({
¯ ql,m,∀l,m
})
, (6)
where αk =√β0/rk, with β0 being the channel power at the
reference distance ofd0 = 1 m. Besides, ak
({
¯ ql,m,∀l,m
})
∈
CLM×1 denotes the receive array response vector of UE k,
given by
ak
({
¯ ql,m,∀l,m
})
=
[
aTk,1({¯ q1,m,∀m}),··· ,
aTk,L({¯ qL,m,∀m})]T. (7)
In the following, for brevity, we use the notations hk, ak and
ak,l to replace hk
({
¯ ql,m,∀l,m
})
, ak
({
¯ ql,m,∀l,m
})
and
ak,l
({
¯ ql,m,∀m
})
, respectively.
Denote by sk the independent and identically distributed
(i.i.d.) information-bearing symbol of UEk, with E[|sk|2] = 1.
To detect its symbol, the receive beamformingvk∈ CLM×1 is
applied at the UA V swarm enabled MA system, with ‖vk‖ =
1. Thus, the resulting signal of UE k after applying the receive
beamforming is
yk = vHk hk√Pksk + vHk K∑
i=1,i⁄=k
hi
√
Pisi + vHk z, (8)
where Pi, i = 1, ··· ,K , denotes the transmit power of
UE i, z∼CN
(
0,σ 2ILM), with each element denoting the
i.i.d. additive white Gaussian noise (AWGN) with zero mean
and power σ2. To reveal the fundamental performance limit,
synchronization is assumed for the UA V swarm system, which
can be achieved via a synchronization protocol as in [46].
The resulting SINR for UE k is
γk =
¯Pk
⏐⏐vHk hk⏐⏐2
K∑
i=1,i⁄=k
¯Pi
⏐⏐vHk hi⏐⏐2 + 1 =
¯PkvHk hkhHk vk
vHk Ckvk , (9)
where Ck ≜ ILM + ∑Ki=1,i⁄=k ¯PihihHi denotes the
interference-plus-noise covariance matrix with respect to
(w.r.t.) UE k, and ¯Pi ≜ Pi/σ2. The achievable rate of UE
k is
Rk = log2 (1 +γk). (10)
1The LoS channel can be further generalized to the multi-path channel.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16467
Our objective is to maximize the minimum achievable rate
over K UEs, by jointly optimizing the 3D UA V swarm
(relative) placement positions Q ={ql,∀l}, the local posi-
tions of MAs at all UA Vs B = {bl,m,∀l,m = 2,··· ,M},
and receive beamforming for all UEs V = {vk,∀k}. Let
ρ (Q, B, V) = min
k∈K
Rk, which is a function of Q, B, and V.
The optimization problem can be formulated as
(P1) max
Q,B,V,ρ
ρ (11)
s.t. Rk≥ρ, ∀k, (11a)
qr + ql∈C , ∀l, (11b)
‖ql− ql′‖2≥d2min, ∀l,l′⁄=l, (11c)
bl,m∈ ˜C, ∀l,m, (11d)
|bl,m−bl,m′|2≥ ˜d2min, ∀l,m,m′⁄=m, (11e)
‖vk‖ = 1, ∀k, (11f)
whereC denotes the movable region of UA Vs, ˜C denotes the
(local) movable region of MAs at each UA V , and the minimum
safe distance constraint and mutual coupling avoidance con-
straint in (1) and (2) have been replaced by their equivalent
quadratic forms, i.e., (11c) and (11e), respectively. Problem
(P1) is challenging to be directly solved due to the non-
concave objective function and (some) non-convex constraints.
Besides, the optimization variables Q, B and V are intricately
coupled in the objective function, which makes their joint
optimization a challenging task.
III. S PECIAL CASE OF SINGLE -ANTENNA UAV
In this section, to gain useful insights, we ﬁrst consider the
special case of single-antenna UA V , i.e.,M = 1, where (P1)
is reduced to
max
Q,V,ρ
ρ
s.t. Rk≥ρ, ∀k,
qr + ql∈C , ∀l,
‖ql− ql′‖2≥d2min, ∀l,l′⁄=l,
‖vk‖ = 1, ∀k. (12)
In the following, the cases of one single UE, two UEs and
arbitrary number of UEs are studied, respectively.
A. Single UE and Two UEs
For the single UE communication, the receive signal in (8)
reduces to
y = vHh√Ps + vHz, (13)
where the UE index is omitted for brevity. By applying the
optimal MRC beamforming, i.e., v = h/‖h‖, the resulting
SNR is given by
γ = ¯P‖h‖2 = ¯P|α|2L, (14)
which only depends on the number of UA VsL, irrespective of
the geometry formed by the UA V swarm enabled MA system.
As a result, any UA V swarm placement within the movable
region while satisfying the minimum safe distance constraint
can achieve the maximum achievable rate.
Next, we consider the classic MRC, zero-forcing (ZF) and
minimum mean-square error (MMSE) beamforming schemes
for the case of two UEs. Denote by ξk,k′≜ |hHk hk′|2‖hk‖2‖hk′‖2 thechannel’s squared-correlation coefﬁcient between UEs k and
k′, where k,k′ = 1, 2 and k⁄=k′. Besides, we have ‖hk‖2 =
|αk|2L. The resulting SINR/SNR of UE k after applying
the three beamforming schemes are respectively given by
[35], [36]
γMRC,k = ¯Pk|αk|2L
(
1−
¯Pk′|αk′|2Lξk,k′
¯Pk′|αk′|2Lξk,k′ + 1
)
, (15)
γZF,k = ¯Pk|αk|2L (1−ξk,k′), (16)
γMMSE,k = ¯Pk|αk|2L
(
1−
¯Pk′|αk′|2Lξk,k′
¯Pk′|αk′|2L + 1
)
. (17)
It is observed from (15)-(17) that the SINRs of MRC, ZF, and
MMSE beamforming depend on the coefﬁcient ξk,k′, and a
larger SINR can be achieved as ξk,k′ decreases. Moreover, the
terms
¯Pk′|αk′|2Lξk,k′
¯Pk′|αk′|2Lξk,k′+1, ξk,k′, and
¯Pk′|αk′|2Lξk,k′
¯Pk′|αk′|2L+1 in (15)-(17)account for the SNR loss factors for UE k due to applying the
MRC, ZF, and MMSE beamforming schemes, respectively. By
substituting (6) into ξk,k′, we have
ξk,k′ = 1L2⏐⏐aHk ak′⏐⏐2. (18)
Based on the above observation, for the case of two UEs, we
aim to minimize the channels’ squared-correlation coefﬁcient,
which can be formulated as
min
Q
1
L2
⏐⏐aHk ak′⏐⏐2
s.t. qr + ql∈C , ∀l,
‖ql− ql′‖2≥d2min, ∀l,l′⁄=l. (19)
To tackle problem (19), we ﬁrst study the property of the
objective function. Note that when the movable region size is
much smaller than the link distance, the UPW model gives
a valid approximation of spherical wavefront for channels
between UA Vs and ground UEs[36], which may correspond to
the cases of small movable region and/or high UA V operation
altitude. In this case, the receive response vector in (7)
reduces to ak = e−j 2πλ rk
[
e−j 2πλκTk q1,··· ,e−j 2πλκTk qL
]T
. By
substituting it into the objective function, we have
1
L2
⏐⏐aHk ak′⏐⏐2 = 1L2
⏐⏐⏐⏐⏐ L∑l=1ej 2πλ (κk−κk′)T ql⏐⏐⏐⏐⏐2. (20)
By letting νmin =⌈Ldmin‖κk−κk′‖/λ− 1⌉, we obtain
the following theorem for UA V position without drift. In
particular, high-accuracy positioning technologies, such as
real-time kinematic (RTK) global navigation satellite system
(GNSS), multi-sensor fusion, and robust ﬂight control algo-
rithms help to mitigate the issue of UA V position drift [47].
Theorem 1: An optimal solution to (19) that achieves zero
objective value is
ql = q1 + (l− 1) (ς⋆ + 1/L)λ‖κk−κk′‖2 (κk−κk′), (21)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

16468 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
where q1 can be any vector to guarantee qr +ql∈C ,∀l, and
ς⋆ is given by
ς⋆ =
{
νmin
L , if mod (ν min + 1,L)⁄= 0,
νmin+1
L , otherwise. (22)
Proof: Please refer to Appendix A. ■
Note that Theorem 1 extends the 1D result in [24] to the
general 3D placement, and the derived closed-form solution
ς⋆ can be a fraction, which removes the requirement of
being an integer imposed in [24]. Moreover, a sufﬁcient
condition for qr + ql ∈ C, ∀l, is that C contains a line
segment parallel to (κk−κk′) with length no smaller than
‖qL− q1‖ = (L−1)(ς⋆+1/L)λ‖κk−κk′‖ .With (21) and (22), we have ξk,k′ = 0 , and γMRC,k =
γZF,k = γMMSE,k = ¯Pk‖hk‖2 = ¯Pk|αk|2L, i.e., they are
identical to the single UE SNR without IUI. Thus, an IUI-free
communication can be achieved with the UA V swarm enabled
MA system, by setting the UA Vs’ static positions according
to Theorem 1. It is worth noting that the adjacent inter-UA V
distance is |ς⋆+1/L|λ‖κk−κk′‖ ≥ dmin, where the minimum distancedmin is in general much larger than half wavelength. Thus, the
UA V swarm forms a USA for the IUI-free communication.
In particular, compared to the classic compact array where
antenna spacing is separated by half wavelength, USA can
achieve a larger array aperture, and thus a narrower beamwidth
of the main lobe is enabled.
Moreover, the objective function in (P1) is given by
min
k∈K
log2
(
1 + ¯Pk|αk|2L). (23)
It can be observed that the UA V swarm enabled MA system
not only completely eliminates the IUI, but also achieves the
full beamforming gain at each UE, in terms of the number of
UA VsL in (23), without suffering from any performance loss
as in the traditional FPA system [35].
B. Arbitrary Number of UEs
In this subsection, for arbitrary number of UEs, we propose
an alternating optimization algorithm to solve problem (12)
sub-optimally, where the receive beamforming and each UA V
placement position are optimized alternately in an iterative
manner.
1) Optimization of V With Given Q: For given UA V swarm
placement positions Q, the receive beamforming optimization
problem in (12) is expressed as
max
V,ρ
ρ
s.t. Rk≥ρ, ∀k,
‖vk‖ = 1, ∀k. (24)
A closer look at (9) shows that the receive beamforming
vk only impacts the SINR for UE k, and (9) is a generalized
Rayleigh quotient w.r.t. vk, the optimal vk to (24) is given by
the classical MMSE beamforming [48]:
v⋆k = C−1k hk‖‖C−1k hk‖‖, ∀k. (25)
2) Optimization of ql With Given V and{ql′,∀l′⁄=l}:
For given V and{ql′,∀l′⁄=l}, the sub-problem of (12) for
optimizing the placement position of UA Vl can be expressed
as
max
ql,ρ
ρ (26)
s.t. Rk≥ρ, ∀k∈K, (26a)
qr + ql∈C , (26b)
‖ql− ql′‖2≥d2min, ∀l′⁄=l. (26c)
Moreover, to tackle the non-convexity of the constraint
(26a), the slack variables{ηk,µk,∀k} are introduced such that
eηk = 1 +
K∑
i=1
¯Pi
⏐⏐vHk hi⏐⏐2, (27)
eµk = 1 +
K∑
i=1,i⁄=k
¯Pi
⏐⏐vHk hi⏐⏐2. (28)
Thus, problem (26) is transformed into
max
ql,ρ,{ηk,µk}Kk=1
ρ (29)
s.t. ln (eηk−µk)ln 2 ≥ρ, ∀k∈K, (29a)
σ2 +
K∑
i=1
Pi
⏐⏐vHk hi⏐⏐2≥σ2eηk, ∀k∈K, (29b)
σ2 +
K∑
i=1,i⁄=k
Pi
⏐⏐vHk hi⏐⏐2≤σ2eµk, ∀k∈K,
(29c)
qr + ql∈C , (29d)
‖ql− ql′‖2≥d2min, l′⁄=l. (29e)
Note that problem (29) is still challenging to be solved
since the constraints (29b), (29c) and (29e) are non-convex.
To tackle this issue, the SCA technique [4] is applied in
the following, which is an efﬁcient iterative optimization
technique that successively updates the optimization variables
by solving the approximated convex problem at each iteration.
Let ¯hi,l ∈ C(L−1)×1 denote the resulting channel after
removing hi,l from hi, and ¯ vk,l ∈ C(L−1)×1 denote the
resulting beamforming vector after removing vk,l from vk,
where hi,l and vk,l denote the l-th element of hi and vk,
respectively. Then, fk,i≜
⏐⏐vHk hi⏐⏐2 can be expressed as
fk,i = hHi vkvHk hi =
L∑
l′=1,l′⁄=l
2Re
{
h∗i,lVk,l,l′hi,l′}
| {z }
gk,i,l
+|αi|2Vk,l,l + ¯hHi,l ¯Vk,l,l¯hi,l| {z }
¯gk,i,l
, (30)
where Vk,l,l′≜ vk,lv∗k,l′, ¯Vk,l,l∈ C(L−1)×(L−1)≜ ¯ vk,l¯ vHk,l,
and ¯gk,i,l is independent of ql. By substituting hi,l =
αie−j 2πλ ri,l into gk,i,l, we have
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16469
gk,i,l =
L∑
l′=1,l′⁄=l
2|αi|2Re{Vk,l,l′ej 2πλ (ri,l−ri,l′)}
=
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′| cos
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)
.
(31)
It is observed that (31) is neither convex nor concave
w.r.t. ql. To this end, two quadratic surrogate functions are
respectively constructed to serve as the lower and upper
bounds for gk,i,l, shown in the following lemma.
Lemma 1: The lower and upper bounds of gk,i,l are respec-
tively given by
gk,i,l≥ [gk,i,l]lb =gk,i,l
(
q(j)l
)
+∇gk,i,l
(
q(j)l
)T(
ql− q(j)l
)
− δk,i,l
2
(
ql− q(j)l
)T(
ql− q(j)l
)
, (32)
gk,i,l≤ [gk,i,l]ub =gk,i,l
(
q(j)l
)
+∇gk,i,l
(
q(j)l
)T(
ql− q(j)l
)
+ δk,i,l
2
(
ql− q(j)l
)T(
ql− q(j)l
)
, (33)
where δk,i,l = 2πλ L∑l′=1,l′⁄=l 2|αi|2|Vk,l,l′|√
2
r2i +
( 2π
λ
)2(1 + Cmaxr2i )2, q(j)l denotes the resulting
placement position of UA V l in the j-th iteration, and
∇gk,i,l(q(j)l ) denotes the gradient of gk,i,l over q(j)l .
Proof: Please refer to Appendix B. ■
With Lemma 1, the lower and upper bounds of the function
fk,i are
fk,i≥ [fk,i]lb≜ [gk,i,l]lb + ¯gk,i,l, (34)
fk,i≤ [fk,i]ub≜ [gk,i,l]ub + ¯gk,i,l, (35)
which are concave and convex w.r.t. ql, respectively.
Moreover, to tackle the non-convexity of eµk on the right-
hand-side (RHS) of (29c), letµ(j)k denote the resulting variable
in the j-th iteration; then the convex function eµk is lower-
bounded by
eµk≥ [eµk]lb≜µkeµ(j)k +(1−µ(j)k )eµ(j)k . (36)
Similarly, for given q(j)l , the convex function ‖ql− ql′‖2
on the left-hand-side (LHS) of (29e) is lower-bounded by [4]
‖ql− ql′‖2≥[‖ql− ql′‖2]lb
≜ 2
(
q(j)l − ql′
)T(
ql− q(j)l
)
+
‖‖‖q(j)l − ql′‖‖‖2. (37)
As a result, problem (29) is lower-bounded by the following
problem for given {q(j)l ,µ (j)k }.
max
ql,ρ,{ηk,µk}Kk=1
ρ
s.t. ηk−µk≥ρ ln 2,∀k∈K,
σ2 +
K∑
i=1
Pi[fki]lb≥σ2eηk, ∀k∈K,
σ2 +
K∑
i=1,i⁄=k
Pi[fki]ub≤σ2[eµk]lb, ∀k∈K,
qr + ql∈C ,[
‖ql− ql′‖2
]
lb
≥d2min, ∀l′⁄=l, (38)
which is a convex optimization problem and can be solved via
the standard convex optimization tools, such as CVX.
Algorithm 1 Proposed Alternating Optimization for Solving
Problem (12)
1: Initialize Q(0) and{v(0)k } randomly, and let j = 0.
2: repeat
3: For given Q(j), obtain the optimal solution to (24)
based on (25), denoted as {v(j+1)k }.
4: forl = 1 :L do
5: Obtain{q(j+1)l } by solving problem (38), given
{q(j+1)1 ,··· , q(j+1)l−1 , q(j)l ,··· , q(j)L} and{v(j+1)k }.
6: end for
7: Update j =j + 1.
8: until the fractional increase in the objective function value
is below a given threshold ϵ> 0.
The overall algorithm is summarized in Algorithm 1, and
its convergence proof is given as follows.
Proposition 1: The objective value of problem (12) obtained
by Algorithm 1 is guaranteed to converge.
Proof: Please refer to Appendix C. ■
It is worth mentioning that the objective value at each
iteration is non-decreasing, thus guaranteeing the convergence
of Algorithm 1. Moreover, the computational complexity is
analyzed as follows. In step 3, the complexity for obtaining
the receive beamforming is O(KL3). The complexity from
step 4 to step 6 is approximately O(I1L(2K)3), where I1
denotes the maximum number of iterations required by SCA
for convergence. Thus, the total computational complexity of
Algorithm 1 isO(I2KL3 +I1I2L(2K)3), where I2 denotes
the number of iterations required by the alternating optimiza-
tion for convergence.
IV. M ULTI-ANTENNA UAV
In this section, we consider the general case of multi-
antenna UA V , where each UA V deploys an MA array and all
the UA Vs simultaneously forms a larger-scale MA system with
their individual MA arrays.
A. Single UE and Two UEs
For the single UE communication, similar to (14), the
resulting SNR is
γ = ¯P‖h‖2 = ¯P|α|2LM. (39)
For the scenario with two UEs, the resulting SINR/SNR of
UE k with the MRC, ZF, and MMSE beamforming can be
similarly obtained by substituting L with LM in (15)-(17),
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

16470 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
respectively. Besides, when UPW model holds, the channel’s
squared-correlation coefﬁcient between UEs k and k′ is
ξk,k′ = 1L2M2
⏐⏐⏐⏐⏐ L∑l=1 aHk,lak′,l⏐⏐⏐⏐⏐2
= 1L2M2
⏐⏐⏐⏐⏐ L∑l=1ej 2πλ (κTk−κTk′)ql M∑m=1ej 2πλ bl,m∆Φk,k′⏐⏐⏐⏐⏐2,
(40)
where ∆Φk,k′≜ Φk−Φk′. It is observed from (40) that when∑M
m=1ej 2πλ bl,m∆Φk,k′ = 0,∀l, we have ξk,k′ = 0.
Similar to Theorem 1, an optimal solution of{bl,m} to (40)
that achieves zero objective value is
bl,m = (m− 1) (ζ⋆l + 1/M)λ|∆Φk,k′| , (41)
where the common coefﬁcient ζ⋆l is derived to satisfy the
mutual coupling avoidance constraint between adjacent MA
elements for each UA V , given by
ζ⋆l =



˜νmin
M , if mod (˜νmin + 1,M )⁄= 0,˜νmin + 1
M , otherwise,
(42)
with ˜νmin =
⌈
M ˜dmin|∆Φk,k′|/λ− 1
⌉
common to all UA Vs.
Moreover, MA position bl,m ∈ ˜C, ∀l,m , can be satisﬁed
when|bl,M−bl,1| = (M− 1) (ζ⋆l +1/M)λ|∆Φk,k′| is no greater than
the maximum distance between any two points in ˜C.
Note that the MAs’ positions given in (41)-(42) enable
an IUI-free communication via MAs’ positions adjustment,
irrespective of UA V swarm placement positions. The objective
function in (P1) is thus given by
min
k∈K
log2
(
1 + ¯Pk|αk|2LM). (43)
In fact, the results in (41)-(42) correspond to the case where
all MA arrays have the identical architecture. To gain further
insights, we express bl,m as bl,m = bm = [bm, 0, 0]T ,∀l, the
channels’ squared-correlation coefﬁcient in (40) is reduced to
ξk,k′ = 1L2
⏐⏐⏐⏐⏐ L∑l=1ej 2πλ (κTk−κTk′)ql⏐⏐⏐⏐⏐2 1M2⏐⏐⏐⏐⏐ M∑m=1ej 2πλ bm∆Φk,k′⏐⏐⏐⏐⏐2| {z }
≤1
.
(44)
It is observed that (44) differs from (20) in the term
1
M 2|∑Mm=1ej 2πλ bm∆Φk,k′|2≤ 1, which characterizes the capa-
bility of the MA array mounted on each UA V to distinguish UE
k andk′ in the spatial domain. Thus, the IUI can be mitigated
by adjusting not only the UA V swarm placement positions,
but also the local positions of MAs at all UA Vs.
In particular, when the USA is adopted, i.e., bm =
(m− 1) Γd = (m − 1) Γλ/2, where Γ ≥ 1 denotes the
sparsity level [27], [45], (44) reduces to
Fig. 2. The channels’ squared-correlation coefﬁcient ξ1,2 versusς and Γ.
ξk,k′ = 1L2
⏐⏐⏐⏐⏐ L∑l=1ej 2πλ (κTk−κTk′)ql⏐⏐⏐⏐⏐2
× 1M2
⏐⏐⏐⏐⏐⏐sin(πMΓ∆Φk,k′2 )sin(πΓ∆Φk,k′2 ) ⏐⏐⏐⏐⏐⏐2. (45)
Then, the coefﬁcient ξk,k′ is equal to zero when sparsity
level satisﬁes
Γ∈
{ 2ε
M∆Φk,k′
⏐⏐⏐⏐ε∈ Z, 2εM∆Φk,k′≥ 1, mod (ε,M )⁄= 0}.
(46)
Fig. 2 shows the channels’ squared-correlation coefﬁcient
ξ1,2 versus ς and Γ for the two-UE communication, by
considering the placement positions given in (21) and (22).
The UE directions are (θ1,φ 1) = (30◦, 60◦) and (θ2,φ 2) =
(0◦, 0◦), respectively. The number of UA Vs is L = 4,
and each UA V is equipped with a USA with M = 4
antennas. For convenience of presentation, the coefﬁcient ξ1,2
below−200 dB is truncated to −200 dB. It is observed that
when ς satisﬁes (59) in Appendix A, the coefﬁcient ξ1,2 is
equal to zero, i.e., the channel of UE 1 is orthogonal to that
of UE 2, and an IUI-free communication can be obtained.
It is also observed that the coefﬁcient ξ1,2 can be reduced by
adjusting the sparsity level Γ, and thus providing an extra DoF
for IUI mitigation as compared to the single-antenna UA V .
B. Arbitrary Number of UEs
Furthermore, for arbitrary number of UEs, an alternating
optimization algorithm similar to Algorithm 1 is proposed,
where the receive beamforming, UA V swarm placement posi-
tions, and local positions of MAs are alternately optimized in
an iterative manner.
1) Optimization of V With Given Q and B: The optimiza-
tion of receive beamforming is the same as (25), which are
omitted for brevity.
2) Optimization of ql With Given V, {ql′,∀l′⁄=l}, and
B: Let ˜hi,l∈ C(L−1)M×1 denote the resulting channel after
removing hi,l∈ CM×1 =αiai,l from hi, ˜ vk,l∈ C(L−1)M×1
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16471
denote the resulting beamforming after removing vk,l ∈
CM×1 from vk, where hi,l and vk,l denote the l-th block of
hi and vk, respectively. For the case of multi-antenna UA V ,
after some manipulations, fk,i =
⏐⏐vHk hi⏐⏐2 can be expressed
as
fk,i =
L∑
l′=1,l′⁄=l
2|αi|2Re{ej 2πλ (ri,l−ri,l′)dHi,lVk,l,l′di,l′}
| {z }
˜gk,i,l
+|αi|2dHi,lVk,l,ldi,l + ˜hHi,l ˜Vk,l,l˜hi,l| {z }
ˆgk,i,l
, (47)
where di,l =
[
e−j 2πλκTi,lbl,1,··· ,e−j 2πλκTi,lbl,M
]T
, Vk,l,l′ ∈
CM×M ≜ vk,lvHk,l′, and ˜Vk,l,l ∈ C(L−1)M×(L−1)M ≜
˜ vk,l˜ vHk,l. Moreover, we adopt the quasi-static local AoA
approximation, ˆgk,i,l is a constant term, and ˜gk,i,l can be
expressed in terms of ql as
˜gk,i,l =
L∑
l′=1,l′⁄=l
2|αi|2
⏐⏐⏐dHi,lVk,l,l′di,l′⏐⏐⏐×
cos
(2π
λ (ri,l−ri,l′) +∠dHi,lVk,l,l′di,l′
)
. (48)
A closer look at (48) shows that it has a similar form to
(31), and its lower and upper bounds can be correspondingly
obtained. As a result, the optimization of ql for the multi-
antenna UA V can follow the similar procedure as in (38).
3) Optimization of bl,m With Given V, Q, and
{bl′,m′,∀l′⁄=l,m′⁄=m}: The sub-problem of (P1) for
optimizing bl,m is
max
bl,m,ρ
ρ
s.t. Rk≥ρ, ∀k,
bl,m∈ ˜C,
|bl,m−bl,m′|2≥ ˜d2min, ∀m′⁄=m. (49)
By following the similar procedure as in Section III-B2,
problem (49) can be transformed to
max
bl,m,ρ,{ηk,µk}Kk=1
ρ
s.t. ηk−µk≥ρ ln 2,∀k∈K,
σ2 +
K∑
i=1
Pi
⏐⏐vHk hi⏐⏐2≥σ2eηk, ∀k∈K,
σ2 +
K∑
i=1,i⁄=k
Pi
⏐⏐vHk hi⏐⏐2≤σ2eµk, ∀k∈K,
bl,m∈ ˜C,
|bl,m−bl,m′|2≥ ˜d2min, ∀m′⁄=m. (50)
Let ˜hi,l,m∈ C(LM−1)×1 and ˜ vk,l,m∈ C(LM−1)×1 denote
the resulting channel and beamforming vector after removing
hi,l,m andvi,l,m, respectively, where hi,l,m andvk,l,m are the
((l− 1)M +m)-th elements of hi and vk, respectively. The
term fk,i =
⏐⏐vHk hi⏐⏐2 can be further expressed as
fk,i = 2|ck,i,l,m| Re
{
e−j( 2πλ Φi,lbl,m−∠ck,i,l,m)}
| {z }
gk,i,l,m
+
|αi|2|vk,l,m|2 + ˜hHi,l,m˜ vk,l,m˜ vHk,l,m˜hi,l,m| {z }
¯gk,i,l,m
, (51)
where ck,i,l,m≜ ˜hHi,l,m˜ vk,l,mv∗k,l,mαie−j 2πλ ri,l, and ¯gk,i,l,m is
independent ofbl,m. Thus, problem (50) can be solved similar
to (29).
Algorithm 2 Proposed Alternating Optimization for Solving
Problem (P1)
1: Initialize Q(0), B(0), and{v(0)k } randomly, and let j = 0.
2: repeat
3: For given Q(j) and B(j), obtain the optimal beamform-
ing{v(j+1)k }.
4: forl = 1 :L do
5: Obtain{q(j+1)l } similar to problem (38), given
{q(j+1)1 ,··· , q(j+1)l−1 , q(j)l ,··· , q(j)L}, B(j),
and{v(j+1)k }.
6: end for
7: forl = 1 :L do
8: form = 2 :M do
9: Obtain b(j+1)l,m given Q(j+1),{b(j+1)1,2 ,··· ,
b(j+1)l,m−1,b (j)l,m,··· b(j)L,M}, and{v(j+1)k }.
10: end for
11: end for
12: Update j =j + 1.
13: until the fractional increase in the objective function value
is below a given threshold ϵ> 0.
The main procedures for solving problem (P1) are
summarized in Algorithm 2. The complexity for obtaining
the receive beamforming in step 3 is O(K(LM)3).
From step 4 to step 6, the complexity is approximately
O(I1L(2K)3), where I1 denotes the maximum number
of iterations required by SCA for convergence. The
complexity from step 7 to step 11 is approximately given
byO(I2L(M− 1)(2K)3), where I2 denotes the maximum
number of iterations to converge required by step 9. As a
result, the total computational complexity of Algorithm 2
is O(I3K(LM)3 +I1I3L(2K)3 +I2I3L(M− 1)(2K)3),
where I3 denotes the number of iterations required by the
alternating optimization for convergence.
Last, we consider the practical case in the presence of
synchronization and position errors. Speciﬁcally, let τl denote
the synchronization error between the local clock of UA V l
and the reference clock, which follows a Gaussian distribution
[49], [50]. With slight abuse of notations, let ¯ ql denote the
nominal position of UA Vl, and ¯ qtruel = ¯ ql + ∆ql denote its
true position, with ∆ql∼N (0,σ 2pI) being the position error
of UA Vl. By taking into account both the synchronization
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

16472 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
and position errors, the receive array response vector of UA V
for UE k is given by
aek,l =e−j 2πλ rtruek,l [e−j 2πλ ϕk(¯ qtruel,1 ),··· ,e−j 2πλ ϕk(¯ qtruel,M )]Tεsynl ,
(52)
whereεsynl =e−j2πfcτl denotes the phase shift induced by the
synchronization error, with fc being the carrier frequency, and
rtruek,l =‖¯ qtruel − wk‖. Since the position error is in general
much smaller than the link distance, and with the second-
order Taylor approximation tortruek,l , the receive array response
vector in (52) is approximated as
aek,l
≈e−j 2πλ rsecondk,l [e−j 2πλ ϕk(¯ ql,1),··· ,e−j 2πλ ϕk(¯ ql,M)]Tεsynl εposk,l,
(53)
where εposk,l = e−j 2πλκTk,l∆ql denotes the phase shift induced
by the position error of UA V l for UE k. Thus, the channel
from UE k to the UA V swarm enabled MA system with
synchronization and position errors is
hek =αk
[(
aek,1)T,··· ,(aek,L)T]T. (54)
Furthermore, we propose a channel estimation-based error
compensation scheme to effectively mitigate the adverse
effects of synchronization and position errors. It is worth men-
tioning that both the synchronization and position errors can
be regarded as the non-ideal factors of channels from UEs to
the UA V swarm enabled MA system. To mitigate the practical
issues, when the UA V swarm arrives at the optimized place-
ment positions based on the ideal channel, channel estimation
is performed. Speciﬁcally, let S∈ CTp×K = [s 1,··· , sK],
where sk∈ CTp×1 denotes the pilot sequence of length Tp
for UE k, with SHS =TpIK. The received signal of the UA V
swarm enabled MA system can be expressed as
Y =√ptrHST + Z, (55)
where ptr denotes the training power, H ∈ CLM×K =
[he1,··· , heK], Z ∈ CLM×Tp denotes the AWGN matrix.
By applying the least-square (LS) estimation, the estimated
channel of UE k can be expressed as
ˆhk = 1√ptrTp Ys∗k. (56)
Based on the estimated channels of UEs, the receive beam-
forming for UE k is updated to ˆ vk =
ˆC−1k ˆhk‖‖‖ˆC−1k ˆhk‖‖‖,∀k, where
ˆCk≜ ILM +∑Ki=1,i⁄=k ¯PiˆhiˆhHi . Then, the achievable rate of
the channel estimation-based error compensation scheme for
UE k is given by
ˆRk = log2 (1 + ˆγk) = log2
(
1 +
¯Pkˆ vHk hek(hek)Hˆ vk
ˆ vHk Cekˆ vk
)
,
(57)
where Cek≜ ILM +∑Ki=1,i⁄=k ¯Pihei(hei)H. Accordingly, the
minimum achievable rate among K UEs can be obtained.
Fig. 3. Convergence behaviour of Algorithm 1.
V. N UMERICAL RESULTS
In this section, numerical results are provided to verify the
performance of the proposed low-altitude UA V swarm enabled
MA system. The channel power at the reference distance
of d0 = 1 m is β0 = −61.4 dB, and the noise power is
σ2 =−94 dBm. The minimum distance to avoid the collision
among UA Vs isdmin = 1 m. Moreover, the minimum distance
to avoid mutual coupling between adjacent MA elements is
˜dmin =λ/2. The (local) movable region of MAs at each UA V
is [0,D ], with D = 20λ. Unless otherwise stated, K = 3 UEs
are uniformly distributed in a circular area with the center
and radius being [0, 0, 0]T m and Rc = 600 m, respectively.
The transmit power of each UE is Pk = 20 dBm. The
movable region of UA Vs is speciﬁed by ¯xl ∈ [xmin,x max]
m, ¯yl ∈ [ymin,y max] m, and ¯zl ∈ [H,H + zmax] m, with
xmin =ymin =−50 m, xmax =ymax = 50 m, zmax = 40 m,
and H = 500 m.
A. Single-Antenna UA V
First, we consider the case of single-antenna UA Vs, with
L = 4. Fig. 3 shows the convergence behaviour of Algo-
rithm 1. The upper bound of IUI-free communication is also
provided for comparison, i.e., the result given in (23). It is
observed that Algorithm 1 yields a non-decreasing minimum
achievable rate, and ﬁnally approaches the converged solution
that is close to the IUI-free upper bound.
Fig. 4 shows the minimum achievable rate versus the
transmit power of each UE for the two-UE communication,
by considering the UE directions (θ1,φ 1) = (30◦, 60◦) and
(θ2,φ 2) = (0◦, 0◦), respectively. The movable region of UA Vs
is speciﬁed by ¯xl ∈ [xmin,x max] m, ¯yl ∈ [ymin,y max] m,
and ¯zl ∈ [H,H + zmax] m, with xmin = ymin = −20 m,
xmax = ymax = 20 m, zmax = 10 m, and H = 1000 m. For
comparison, the benchmark scheme of circular array geometry
is considered, i.e., the UA V swarm cooperatively forms a
circular array, with their placement positions given by
¯ ql
= qr +
[
R cos
(2π
L (l− 1)
)
,R sin
(2π
L (l− 1)
)
, 0
]T
, ∀l,
(58)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16473
Fig. 4. The minimum achievable rate versus the transmit power of each UE
for the two-UE communication in the single-antenna UA V case.
Fig. 5. The SNR loss factor versus the transmit power for the two-UE
communication in the single-antenna UA V case.
where R denotes the radius of circular array geometry and is
set as R = (xmax−xmin)/2 = (y max−ymin)/2. With the
circular array geometry, the MMSE, ZF and MRC beamform-
ing schemes are respectively considered. It is observed that the
proposed UA V swarm enabled MA system achieves an IUI-
free communication, thanks to the ﬂexible placement position
optimization. Besides, the proposed scheme outperforms the
benchmark schemes of circular array geometry with MMSE,
ZF, and MRC beamforming. This is expected since the pro-
posed scheme is able to completely orthogonalize the channels
of two UEs, while achieving the full beamforming gain at each
UE. Speciﬁcally, Fig. 5 shows the SNR loss factor versus the
transmit power for UE 1. It is observed that the proposed
scheme always enjoys a zero SNR loss factor. By contrast, the
circular array geometry with MMSE and MRC beamforming
schemes experience increased SNR loss factors as the transmit
power increases, as a result of suffering from more severe IUI,
especially for the MRC beamforming scheme.
For further comparison, Fig. 6 shows the minimum achiev-
able rate versus the transmit power of each UE for K = 3
UEs. Since MMSE beamforming achieves the balance
Fig. 6. The minimum achievable rate versus the transmit power of each UE
for three UEs in the single-antenna UA V case.
between reducing the interference and noise enhancement,
the benchmark scheme of circular array geometry with
MMSE beamforming is considered in the following. Moreover,
the benchmark scheme of distributed MIMO is considered
[51], where four single-antenna access points (APs) coop-
eratively serve the UEs, and their locations are given by
[Rc/2,Rc/2, 0]T , [−Rc/2,Rc/2, 0]T , [−Rc/2,−Rc/2, 0]T ,
[Rc/2,−Rc/2, 0]T , respectively, with Rc = 1000 m. It is
ﬁrstly observed that the minimum achievable rate of both the
proposed and benchmark schemes increase as the transmit
power increases, as expected. Besides, similar to the case of
two UEs, the proposed UA V swarm enabled MA system yields
a comparable performance to the IUI-free upper bound, and
is signiﬁcantly superior to the benchmark scheme of circular
array geometry with MMSE beamforming. This is expected
since the proposed scheme can strike a good balance between
the beamforming gain improvement and IUI mitigation via
the ﬂexible UA V placement position adjustment. It is also
observed that the proposed scheme outperforms the benchmark
scheme of distributed MIMO as the transmit power increases.
This is expected since although the distributed MIMO deploys
the geographically separated APs, their ﬁxed-position antennas
cannot exploit the channel variation in the spatial domain for
mitigating the IUI.
Fig. 7 shows the minimum achievable rate versus the
number of UEs, K. It is observed that the performance of
both schemes decrease as the number of UEs increases. This
is because more UEs will cause a severer IUI issue, especially
when the number of UA Vs/antennas is smaller than that of
UEs, e.g., K > 4. It is also observed that the minimum
achievable rate of the proposed UA V swarm enabled MA
system always surpasses the benchmark scheme of circular
array geometry, thanks to the ﬂexible UA V placement position
adjustment to signiﬁcantly reduce the channel correlation and
thus the IUI among UEs.
B. Multi-Antenna UA V
Next, we consider the case of multi-antenna UA Vs, where
the numbers of UA Vs and MAs per UA V are L = 2 and
M = 4, respectively. For comparison, the following two
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

16474 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. The minimum achievable rate versus the number of UEs in the single-
antenna UA V case.
Fig. 8. The minimum achievable rate versus the transmit power of each UE
in the multi-antenna UA V case.
benchmark schemes are considered: 1) Circular array geome-
try with FPA: each UA V is equipped with an FPA array (linear)
and UA V swarm adopts the circular geometry given in (58);
2) Placement optimization with FPA: each UA V is equipped
with the FPA array as above and UA V swarm placement is
optimized similar to Section IV-B. Fig. 8 shows the minimum
achievable rate versus the transmit power of each UE for the
case with K = 3 UEs. It is observed that the performance of
UA V swarm enabled MA system is very close to that of the
IUI-free communication, and its performance gains over the
other two benchmark schemes become even more signiﬁcant
as the transmit power increases. This is due to the two-level
mobility brought by UA V swarm enabled MA system, i.e.,
the intrinsic mobility of UA V swarm and additional antenna
position adjustment of MA. Speciﬁcally, it can be observed
that the scheme of placement optimization with FPA yields a
better performance than that of circular UA V geometry with
FPA, which demonstrates the importance of UA V swarm place-
ment optimization for performance improvement. Moreover,
compared to the scheme of placement optimization with FPA,
considerable performance gain is achieved for UA V swarm
Fig. 9. The minimum achievable rate versus the normalized movable region
size in the multi-antenna UA V case.
enabled MA system, thanks to the additional antenna position
adjustment of MA. The above results verify the advantages
of two-level mobility brought by UA V swarm enabled MA
system, i.e., it can fully exploit channel variation for balancing
the beamforming gain improvement and IUI reduction.
Fig. 9 studies the impact of the normalized movable region
size D/λ on the minimum achievable rate. For K = 2, the
transmit power of each UE isPk = 35 dBm, the UE directions
remain consistent with those in Fig. 4, and the following
three schemes are considered: 1) Placement optimization with
USA: each UA V is equipped with a USA and UA V swarm
adopts the placement given in (21) and (22); 2) Circular array
geometry with USA: each UA V is equipped with a USA
and UA V swarm adopts the circular geometry given in (58);
3) Circular array geometry with FPA: Similar to 2), but using
FPA instead USA. For USA, the sparsity level can be dynam-
ically adjusted. It is ﬁrstly observed from Fig. 9(a) that the
scheme of placement optimization with USA directly achieves
the IUI-free communication. This is because the placement
given in (21) and (22) orthogonalizes the channels of two UEs.
On the other hand, as the normalized movable region size
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16475
Fig. 10. Comparison of the minimum achievable rate for the cases with and
without synchronization and position errors.
increases, the scheme of circular array geometry with USA
also achieves the IUI-free communication, thanks to the extra
DoF of sparsity level adjustment for completely eliminating
the IUI. Moreover, for K = 3, it is observed from Fig. 9(b)
that the performance of two FPA schemes remain unchanged
as the normalized movable region size increases, as expected.
By contrast, the performance of the proposed UA V swarm
enabled MA system ﬁrst increases and ultimately converges as
the normalized movable region size increases. This is mainly
attributed to the fact that with an enlarged movable region
size, MA array has a larger spatial DoF to create favorable
channels for performance improvement. However, this does
not mean that the performance gain of UA V swarm enabled
MA system over other benchmark schemes will continuously
increase, since it is upper-bounded by the performance under
IUI-free communication.
Last, Fig. 10 compares the minimum achievable rate for
the cases with and without synchronization and position
errors, where for the former, the proposed channel estimation-
based error compensation scheme is considered. The standard
deviations of synchronization and position errors are 31.6µs,
and σp = λ, respectively. The length of pilot sequence is
Tp = 60, and the training power is ptr = P . It is observed
that the proposed channel estimation-based error compensation
scheme yields a comparable performance to the case without
errors, which demonstrates the effectiveness of the proposed
scheme in compensating for synchronization and position
uncertainties.
VI. C ONCLUSION
This paper proposed a novel UA V swarm enabled two-level
MA system to support low-altitude economy, by exploiting the
controllable mobility of UA V and antenna position adjustment
of MA. An optimization problem was formulated to maximize
the minimum achievable rate over all ground UEs, by jointly
optimizing 3D UA V swarm placement positions, their indi-
vidual MAs’ positions, and receive beamforming for UEs. To
gain useful insights, we ﬁrst considered the special case of
single-antenna UA V . It was shown that the resulting SNR of
single UE communication is independent of UA V swarm array
geometry, and the optimal UA V swarm placement positions
were derived in closed-form for two-UE communication. For
arbitrary number of UEs, an alternating optimization algorithm
was proposed to efﬁciently solve the formulated non-convex
problem. Moreover, the results of single-antenna UA V were
extended to the general case with multi-antenna UA V . Numeri-
cal results demonstrated that signiﬁcant performance gains can
be achieved for the proposed UA V swarm enabled MA system
over various benchmarks, thanks to the two-level antenna
mobility to create more favorable channels.
In addition, there are many important research directions
that could be pursued in the future. For instance, the channel
modeling incorporating the array misalignment and orientation
jitter issues, as well as the extension to multi-path channels,
are worthwhile to investigate. Besides achievable rate, energy
consumption and latency are the important performance met-
rics for UA V swarm enabled MA system, while designing
the energy-efﬁcient and low-latency UA V system needs more
in-depth studies. Moreover, the ﬂight control mechanisms of
UA V swarm to guarantee the safety and mission execution are
important to investigate in the future. Last, how to integrate
IRS into UA V swarm enabled MA systems is an interesting
direction that deserves further investigation.
APPENDIX A
PROOF OF THEOREM 1
By substituting ql = q1 + (l− 1)× (ς+1/L)λ‖κk−κk′‖2 (κk−κk′)into (20), where ς is a common coefﬁcient to all the UA Vs,
given by
ς∈
{ν
L
⏐⏐⏐ν∈ Z, mod (ν + 1,L)⁄= 0}, (59)
it can be veriﬁed that the objective value of (20) is equal to
zero. Moreover, the distance between UA V l and l′ is given
by
‖ql− ql′‖ =
‖‖‖‖‖(l−l′) (ς + 1/L)λ (κk−κk′)‖κk−κk′‖2‖‖‖‖‖
≥
‖‖‖‖‖(ς + 1/L)λ (κk−κk′)‖κk−κk′‖2‖‖‖‖‖ = λ|ς + 1/L|‖κk−κk′‖. (60)
To satisfy the minimum safe distance constraint for UA Vs, a
feasible solution of ς is thus given by (22). This completes
the proof of Theorem 1.
APPENDIX B
PROOF OF LEMMA 1
With gk,i,l given in (31), its lower and upper bounds can
be constructed based on the second-order Taylor expansion
[25], [52], [53]. Speciﬁcally, the gradient of gk,i,l over ql is
∇gk,i,l =
[
∂gk,i,l
∂xl , ∂gk,i,l∂yl , ∂gk,i,l∂zl
]T
, where
∂gk,i,l
∂xl
=−2πλ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|∂ri,l∂xl
× sin
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)
, (61)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

16476 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
∂gk,i,l
∂yl
=−2πλ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|∂ri,l∂yl
× sin
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)
, (62)
∂gk,i,l
∂zl
=−2πλ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|∂ri,l∂zl
× sin
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)
, (63)
where ∂ri,l∂xl = Φ i + xl−(xlΦi+ylΨi+zlΘi)Φiri ,∂ri,l
∂yl = Ψ i + yl−(xlΦi+ylΨi+zlΘi)Ψiri , and ∂ri,l∂zl =
Θi + zl−(xlΦi+ylΨi+zlΘi)Θiri , respectively.Besides, the Hessian matrix of gk,i,l over ql is
∇2gk,i,l=


∂2gk,i,l
∂xl∂xl
∂2gk,i,l
∂xl∂yl
∂2gk,i,l
∂xl∂zl
∂2gk,i,l
∂yl∂xl
∂2gk,i,l
∂yl∂yl
∂2gk,i,l
∂yl∂zl
∂2gk,i,l
∂zl∂xl
∂2gk,i,l
∂zl∂yl
∂2gk,i,l
∂zl∂zl

, (64)
where
∂2gk,i,l
∂xl∂xl
=−2πλ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|×
[1− Φ2i
ri
sin
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)
+
2π
λ
(∂ri,l
∂xl
)2
cos
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)]
, (65)
∂2gk,i,l
∂xl∂yl
=−2πλ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|×
[−ΦiΨi
ri
sin
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)
+
2π
λ
∂ri,l
∂xl
∂ri,l
∂yl
cos
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)]
, (66)
∂2gk,i,l
∂xl∂zl
=−2πλ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|×
[−ΦiΘi
ri
sin
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)
+
2π
λ
∂ri,l
∂xl
∂ri,l
∂zl
cos
(2π
λ (ri,l−ri,l′) +∠Vk,l,l′
)]
, (67)
and other elements can be similarly obtained based on (61)-
(63), which are omitted for brevity.
Moreover, with (64), we have (68), shown at the bottom of
the page.
Let Cmax≜ maxql x2l +y2l + z2l , it follows that
‖‖∇2gk,i,l‖‖2F≤

2π
λ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|


2
×
[
2
r2i +
(2π
λ
)2(
1 +Cmax
r2i
)2]
. (69)
With∇2gk,i,l ≼ ‖‖∇2gk,i,l‖‖2I, and by choosing δk,i,l =
2π
λ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|
√
2
r2i +
( 2π
λ
)2(1 + Cmaxr2i )2, we have
∇2gk,i,l≼δk,i,lI. Thus, the lower and upper bounds of gk,i,l
in (32) and (33) can be obtained with the Taylor’s theorem
[52]. The proof of Lemma 1 is thus completed.
APPENDIX C
PROOF OF PROPOSITION 1
Denote by {q(j)l } and{v(j)k } the corresponding optimiza-
tion variables in the j-th iteration. Let ρtrajlb ({q(j)l },{v(j)k })
denote the corresponding objective value of problem (38). In
thej-th iteration, since the optimal solution to (24) is obtained
for given{q(j)l } in step 3, it follows that
ρ
({
q(j)l
}
,
{
v(j)k
})
≤ρ
({
q(j)l
}
,
{
v(j+1)k
})
. (70)
Besides, regarding UA Vl in step 5, for given {v(j+1)k } and
{q(j+1)1 ,··· , q(j+1)l−1 , q(j)l ,··· , q(j)L}, we have
ρ
({
q(j+1)1 ,··· , q(j+1)l−1 , q(j)l ,··· , q(j)L
}
,
{
v(j+1)k
})
‖‖∇2gk,i,l‖‖22≤‖‖∇2gk,i,l‖‖2F =(∂2gk,i,l∂xl∂xl)2 +··· +(∂2gk,i,l∂zl∂zl )2≤2πλ L∑l′=1,l′⁄=l 2|αi|2|Vk,l,l′|2×

(1− Φ2i
ri
)2
+
(
2π
λ
(∂ri,l
∂xl
)2)2
+
(ΦiΨi
ri
)2
+
(2π
λ
∂ri,l
∂xl
∂ri,l
∂yl
)2
+
(ΦiΘi
ri
)2
+
(2π
λ
∂ri,l
∂xl
∂ri,l
∂zl
)2
+
(ΨiΦi
ri
)2
+
(2π
λ
∂ri,l
∂yl
∂ri,l
∂xl
)2
+
(1− Ψ2i
ri
)2
+
(
2π
λ
(∂ri,l
∂yl
)2)2
+
(ΨiΘi
ri
)2
+
(2π
λ
∂ri,l
∂yl
∂ri,l
∂zl
)2
+
(ΘiΦi
ri
)2
+
(2π
λ
∂ri,l
∂zl
∂ri,l
∂xl
)2
+
(ΘiΨi
ri
)2
+
(2π
λ
∂ri,l
∂zl
∂ri,l
∂yl
)2
+
(1− Θ2i
ri
)2
+
(
2π
λ
(∂ri,l
∂zl
)2)2

=

2π
λ
L∑
l′=1,l′⁄=l
2|αi|2|Vk,l,l′|


2
 2
r2i +
(2π
λ
)2(
1 +x2l +y2l + z2l− (xlΦi +ylΨi + zlΘi)2
r2i
)2
. (68)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16477
(a)
=ρtrajlb
({
q(j+1)1 ,··· , q(j+1)l−1 , q(j)l ,··· , q(j)L
}
,
{
v(j+1)k
})
(b)
≤ρtrajlb
({
q(j+1)1 ,··· , q(j+1)l−1 , q(j+1)l ,··· , q(j)L
}
,
{
v(j+1)k
})
(c)
≤ρ
({
q(j+1)1 ,··· , q(j+1)l−1 , q(j+1)l ,··· , q(j)L
}
,
{
v(j+1)k
})
,
(71)
where (a) holds because the Taylor expansions are tight at the
given local point q(j)l ; the inequality (b) holds because prob-
lem (38) is solved via SCA, which ensures a non-decreasing
objective value; the inequality (c) holds because the objective
value of (26) is lower-bounded by that of (38) at q(j+1)l . Based
on (70) and (71), we have
ρ
({
q(j)l
}
,
{
v(j)k
})
≤ρ
({
q(j+1)l
}
,
{
v(j+1)k
})
. (72)
The result shows that the objective value of problem (12)
is non-decreasing over iterations, and thus, Algorithm 1 is
guaranteed to converge. This thus completes the proof of
Proposition 1.
REFERENCES
[1] H. Lu, Y . Zeng, S. Ma, B. Li, S. Jin, and R. Zhang, “Enabling aerial
movable antenna system with UA V swarm for low-altitude economy,”
in Proc. IEEE/CIC Int. Conf. Commun. China (ICCC Workshops), Aug.
2025, pp. 1–6.
[2] Y . Jiang et al., “6G non-terrestrial networks enabled low-altitude econ-
omy: Opportunities and challenges,” 2023, arXiv:2311.09047.
[3] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for
low-altitude economy: Coordinated transmit beamforming and UA V tra-
jectory design,” IEEE Trans. Commun., vol. 73, no. 8, pp. 5832–5847,
Aug. 2025.
[4] Y . Zeng, Q. Wu, and R. Zhang, “Accessing from the sky: A tutorial
on UA V communications for 5G and beyond,” Proc. IEEE, vol. 107,
no. 12, pp. 2327–2375, Dec. 2019.
[5] M. Mozaffari, W. Saad, M. Bennis, Y .-H. Nam, and M. Debbah,
“A tutorial on UA Vs for wireless networks: Applications, challenges,
and open problems,” IEEE Commun. Surveys Tuts., vol. 21, no. 3,
pp. 2334–2360, 3rd Quart., 2019.
[6] Y . Song et al., “An overview of cellular ISAC for low-altitude UA V: New
opportunities and challenges,” IEEE Commun. Mag., vol. 63, no. 12,
pp. 88–95, Dec. 2025.
[7] Y . Zeng, J. Lyu, and R. Zhang, “Cellular-connected UA V: Potential, chal-
lenges, and promising technologies,” IEEE Wireless Commun., vol. 26,
no. 1, pp. 120–127, Feb. 2019.
[8] S. Zhang, Y . Zeng, and R. Zhang, “Cellular-enabled UA V communi-
cation: A connectivity-constrained trajectory optimization perspective,”
IEEE Trans. Commun., vol. 67, no. 3, pp. 2580–2604, Mar. 2019.
[9] Framework and Overall Objectives of the Future Development of IMT
for 2030 and Beyond, ITU-R M.2160-0, Jun. 2023. [Online]. Available:
https://www.itu.int/rec/R-REC-M.2160/en
[10] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets integrated
sensing and communication: Challenges and future directions,” IEEE
Commun. Mag., vol. 61, no. 5, pp. 62–67, May 2023.
[11] Y . Pan et al., “Cooperative trajectory planning and resource allocation
for UA V-enabled integrated sensing and communication systems,”IEEE
Trans. V eh. Technol., vol. 73, no. 5, pp. 6502–6516, May 2024.
[12] X. Jing, F. Liu, C. Masouros, and Y . Zeng, “ISAC from the sky: UA V
trajectory design for joint communication and target localization,” IEEE
Trans. Wireless Commun., vol. 23, no. 10, pp. 12857–12872, Oct. 2024.
[13] S. Javed et al., “State-of-the-art and future research challenges in UA V
swarms,” IEEE Internet Things J., vol. 11, no. 11, pp. 19023–19045,
Jun. 2024.
[14] B. Li, Q. Li, Y . Zeng, Y . Rong, and R. Zhang, “3D trajec-
tory optimization for energy-efﬁcient UA V communication: A control
design perspective,” IEEE Trans. Wireless Commun., vol. 21, no. 6,
pp. 4579–4593, Jun. 2022.
[15] Q. Li, B. Li, Z.-Q. He, Y . Rong, and Z. Han, “Joint design of
communication sensing and control with a UA V platform,” IEEE Trans.
Wireless Commun., vol. 23, no. 12, pp. 19231–19244, Dec. 2024.
[16] H. Zhang, B. Li, Y . Rong, Y . Zeng, and R. Zhang, “Joint optimiza-
tion of transmit power and trajectory for UA V-enabled data collection
with dynamic constraints,” IEEE Trans. Commun., vol. 73, no. 9,
pp. 8080–8091, Sep. 2025.
[17] S. Javaid et al., “Communication and control in collaborative UA Vs:
Recent advances and future trends,” IEEE Trans. Intell. Transp. Syst.,
vol. 24, no. 6, pp. 5719–5739, Jun. 2023.
[18] D. Fan et al., “Channel estimation and self-positioning for UA V swarm,”
IEEE Trans. Commun., vol. 67, no. 11, pp. 7994–8007, Nov. 2019.
[19] Z. Mou, Y . Zhang, F. Gao, H. Wang, T. Zhang, and Z. Han, “Deep
reinforcement learning based three-dimensional area coverage with UA V
swarm,” IEEE J. Sel. Areas Commun., vol. 39, no. 10, pp. 3160–3176,
Oct. 2021.
[20] X. Liu, Y . Liu, Z. Liu, and T. S. Durrani, “Fair integrated sensing and
communication for multi-UA V-enabled Internet of Things: Joint 3-D
trajectory and resource optimization,” IEEE Internet Things J., vol. 11,
no. 18, pp. 29546–29556, Sep. 2024.
[21] C. Wang, Z. Wei, W. Jiang, H. Jiang, and Z. Feng, “Cooperative sensing
enhanced UA V path-following and obstacle avoidance with variable
formation,” IEEE Trans. V eh. Technol., vol. 73, no. 6, pp. 7501–7516,
Jun. 2024.
[22] J. Xu, H. Min, and Y . Zeng, “Integrated super-resolution sensing and
symbiotic communication with 3D sparse MIMO for low-altitude UA V
swarm,” IEEE Trans. Commun., vol. 74, pp. 2812–2826, 2026.
[23] L. Zhu, W. Ma, and R. Zhang, “Movable antennas for wireless commu-
nication: Opportunities and challenges,” IEEE Commun. Mag., vol. 62,
no. 6, pp. 114–120, Jun. 2024.
[24] L. Zhu, W. Ma, and R. Zhang, “Movable-antenna array enhanced
beamforming: Achieving full array gain with null steering,” IEEE
Commun. Lett., vol. 27, no. 12, pp. 3340–3344, Dec. 2023.
[25] W. Ma, L. Zhu, and R. Zhang, “MIMO capacity characterization for
movable antenna systems,” IEEE Trans. Wireless Commun., vol. 23,
no. 4, pp. 3392–3407, Apr. 2024.
[26] L. Zhu et al., “A tutorial on movable antennas for wireless networks,”
IEEE Commun. Surveys Tuts., vol. 28, pp. 3002–3054, 2026.
[27] H. Lu, Y . Zeng, S. Jin, and R. Zhang, “Group movable antenna with
ﬂexible sparsity: Joint array position and sparsity optimization,” IEEE
Wireless Commun. Lett., vol. 13, no. 12, pp. 3573–3577, Dec. 2024.
[28] Z. Dong et al., “Movable antenna for wireless communications: Pro-
totyping and experimental results,” IEEE Trans. Wireless Commun.,
vol. 25, pp. 6586–6599, 2026.
[29] X. Shao, Q. Jiang, and R. Zhang, “6D movable antenna based on
user distribution: Modeling and optimization,” IEEE Trans. Wireless
Commun., vol. 24, no. 1, pp. 355–370, Jan. 2025.
[30] X. Shao, R. Zhang, Q. Jiang, and R. Schober, “6D movable
antenna enhanced wireless network via discrete position and rotation
optimization,” IEEE J. Sel. Areas Commun., vol. 43, no. 3, pp. 674–687,
Mar. 2025.
[31] X. Shao, R. Zhang, Q. Jiang, J. Park, T. Q. S. Quek, and R. Schober,
“Distributed channel estimation and optimization for 6D movable
antenna: Unveiling directional sparsity,” IEEE J. Sel. Topics Signal
Process., vol. 19, no. 2, pp. 349–365, Mar. 2025.
[32] X. Shao et al., “A tutorial on six-dimensional movable antenna for
6G networks: Synergizing positionable and rotatable antennas,” IEEE
Commun. Surveys Tuts., vol. 28, pp. 3666–3709, 2026.
[33] K.-K. Wong, A. Shojaeifard, K.-F. Tong, and Y . Zhang, “Fluid
antenna systems,” IEEE Trans. Wireless Commun., vol. 20, no. 3,
pp. 1950–1962, Mar. 2021.
[34] W. K. New et al., “A tutorial on ﬂuid antenna system for 6G
networks: Encompassing communication theory, optimization methods
and hardware designs,” IEEE Commun. Surveys Tuts., vol. 27, no. 4,
pp. 2325–2377, Aug. 2025.
[35] H. Lu and Y . Zeng, “Near-ﬁeld modeling and performance analysis
for multi-user extremely large-scale MIMO communication,” IEEE
Commun. Lett., vol. 26, no. 2, pp. 277–281, Feb. 2022.
[36] H. Lu et al., “A tutorial on near-ﬁeld XL-MIMO communica-
tions towards 6G,” IEEE Commun. Surveys Tuts., vol. 26, no. 4,
pp. 2213–2257, 4th Quart., Apr. 2024.
[37] H. Lu, Z. Yu, Y . Zeng, S. Ma, S. Jin, and R. Zhang, “Wireless communi-
cation with ﬂexible reﬂector: Joint placement and rotation optimization
for coverage enhancement,” IEEE Trans. Wireless Commun., vol. 24,
no. 10, pp. 8252–8266, Oct. 2025.
[38] Y . Bai, B. Xie, R. Zhu, Z. Chang, and R. J ¨antti, “Movable antenna-
equipped UA V for data collection in backscatter sensor networks: A
deep reinforcement learning-based approach,” in Proc. IEEE Int. Conf.
Commun., Jun. 2025, pp. 6560–6565.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

16478 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[39] X.-W. Tang, Y . Shi, Y . Huang, and Q. Wu, “UA V-mounted mov-
able antenna: Joint optimization of UA V placement and antenna
conﬁguration,” 2024, arXiv:2409.02469.
[40] W. Liu, X. Zhang, H. Xing, J. Ren, Y . Shen, and S. Cui, “UA V-enabled
wireless networks with movable-antenna array: Flexible beamforming
and trajectory design,” IEEE Wireless Commun. Lett., vol. 14, no. 3,
pp. 566–570, Mar. 2025.
[41] T. Ren, X. Zhang, L. Zhu, W. Ma, X. Gao, and R. Zhang, “6-D
movable antenna enhanced interference mitigation for cellular-connected
UA V communications,” IEEE Wireless Commun. Lett., vol. 14, no. 6,
pp. 1618–1622, Jun. 2025.
[42] C. Liu, W. Mei, P. Wang, Y . Meng, Z. Chen, and B. Ning, “UA V-enabled
passive 6D movable antennas: Joint deployment and beamforming
optimization,” IEEE Trans. Wireless Commun., vol. 25, pp. 9765–9781,
2026.
[43] H. Lu, Y . Zeng, S. Jin, and R. Zhang, “Aerial intelligent reﬂect-
ing surface: Joint placement and passive beamforming design with
3D beam ﬂattening,” IEEE Trans. Wireless Commun., vol. 20, no. 7,
pp. 4128–4143, Jul. 2021.
[44] X. Li et al., “Sparse MIMO for ISAC: New opportunities and
challenges,” IEEE Wireless Commun., vol. 32, no. 4, pp. 170–178, Aug.
2025.
[45] H. Wang et al., “Enhancing spatial multiplexing and interference sup-
pression for near- and far-ﬁeld communications with sparse MIMO,”
IEEE Trans. Commun., vol. 74, pp. 5765–5782, 2026.
[46] S. Mohanti et al., “AirBeam: Experimental demonstration of distributed
beamforming by a swarm of UA Vs,” in Proc. IEEE 16th Int. Conf.
Mobile Ad Hoc Sensor Syst. (MASS), Nov. 2019, pp. 162–170.
[47] Z. Zuo, C. Liu, Q.-L. Han, and J. Song, “Unmanned aerial vehicles:
Control methods and future challenges,” IEEE/CAA J. Autom. Sinica,
vol. 9, no. 4, pp. 601–614, Apr. 2022.
[48] Z. Wang, J. Zhang, E. Bj ¨ornson, D. Niyato, and B. Ai, “Optimal bilinear
equalizer for cell-free massive MIMO systems over correlated Rician
channels,” IEEE Trans. Signal Process., vol. 73, pp. 1501–1517, 2025.
[49] F. Quitin, A. T. Irish, and U. Madhow, “A scalable architec-
ture for distributed receive beamforming: Analysis and experimen-
tal demonstration,” IEEE Trans. Wireless Commun., vol. 15, no. 3,
pp. 2039–2053, Mar. 2016.
[50] J. Li, G. Sun, L. Duan, and Q. Wu, “Multi-objective optimization for
UA V swarm-assisted IoT with virtual antenna arrays,” IEEE Trans.
Mobile Comput., vol. 23, no. 5, pp. 4890–4907, May 2024.
[51] H. A. Ammar, R. Adve, S. Shahbazpanahi, G. Boudreau, and K. V . Srini-
vas, “User-centric cell-free massive MIMO networks: A survey of
opportunities, challenges and solutions,” IEEE Commun. Surveys Tuts.,
vol. 24, no. 1, pp. 611–652, 1st Quart., 2022.
[52] Y . Sun, P. Babu, and D. P. Palomar, “Majorization-minimization algo-
rithms in signal processing, communications, and machine learning,”
IEEE Trans. Signal Process., vol. 65, no. 3, pp. 794–816, Feb. 2017.
[53] H. Wang et al., “Throughput maximization for movable antenna systems
with movement delay consideration,” IEEE Trans. Wireless Commun.,
vol. 25, pp. 883–899, 2026.
Haiquan Lu (Member, IEEE) received the
B.S. degree in communication engineering from
Yangzhou University, Yangzhou, China, in 2016, the
M.S. degree in signal and information processing
from Nanjing University of Posts and Telecommu-
nications, Nanjing, China, in 2019, and the Ph.D.
degree in information and communication engineer-
ing from Southeast University, Nanjing, in 2024.
From January 2025 to September 2025, he was a
Post-Doctoral Fellow with the State Key Laboratory
of Internet of Things for Smart City, University
of Macau, Macau, China. Since October 2025, he has been an Associate
Professor with the School of Electronic and Optical Engineering, Nanjing Uni-
versity of Science and Technology. His research interests include extremely
large-scale multiple-input multiple-output (XL-MIMO) communication and
reconﬁgurable MIMO. He was a recipient of the Best Paper Award from
IEEE International Conference on Communications (ICC) in 2021.
Yong Zeng (Fellow, IEEE) received the Bachelor
of Engineering (Hons.) and Ph.D. degrees from
Nanyang Technological University, Singapore.
He is a Chief Young Professor with the
National Mobile Communications Research Labo-
ratory, Southeast University, China, and also with
Purple Mountain Laboratories, Nanjing, China.
From 2013 to 2018, he was a Research Fellow
and a Senior Research Fellow with the Department
of Electrical and Computer Engineering, National
University of Singapore. From 2018 to 2019, he
was a Lecturer with the School of Electrical and Information Engineering,
The University of Sydney, Australia. He proposed the concept of channel
knowledge map (CKM) and the transmission method of delay-Doppler
alignment modulation (DDAM). He has published more than 200 papers,
which have been cited by more than 37 000 times based on Google Scholar.
He was elevated to IEEE Fellow “for contributions to unmanned aerial
vehicle communications and wireless power transfer.” He was listed as
Highly Cited Researcher by Clarivate Analytics for seven consecutive years
(2019–2025). He was a recipient of the Australia Research Council (ARC)
Discovery Early Career Researcher Award (DECRA), the IEEE Marconi
Prize Paper Award in Wireless Communications in 2020 and 2024, the
IEEE Communications Society Asia–Paciﬁc Outstanding Young Researcher
Award in 2018, the IEEE Communications Society Heinrich Hertz Prize
Paper Award in 2020 and 2017, the IEEE ICC Best Paper Award in 2021,
and the China Communications Best Paper Award in 2021. He was the
Symposium Chair of IEEE Globecom 2021 Track on Aerial Communications,
the Workshop Co-Chair of ICC 2018–2023 Workshop on UA V communi-
cations, and the Tutorial Speaker of Globecom 2018/2019 and ICC 2019
tutorials on UA V communications. He serves/served as an Associate Editor for
IEEE T RANSACTIONS ON COMMUNICATIONS , IEEE T RANSACTIONS ON
MOBILE COMPUTING , IEEE C OMMUNICATIONS LETTERS , and IEEE O PEN
JOURNAL OF VEHICULAR TECHNOLOGY ; a Leading Guest Editor for IEEE
WIRELESS COMMUNICATIONS on “Integrating UA Vs Into 5G and Beyond”
and China Communications on “Network-Connected UA V Communications.”
Shaodan Ma (Senior Member, IEEE) received the
double bachelor’s degree in science and economics
and the M.Eng. degree in electronic engineering
from Nankai University, Tianjin, China, in 1999 and
2002, respectively, and the Ph.D. degree in electrical
and electronic engineering from The University of
Hong Kong, Hong Kong, in 2006.
From 2006 to 2011, she was a Post-Doctoral
Fellow with The University of Hong Kong. Since
August 2011, she has been with the University of
Macau, where she is currently a Professor. Her
research interests include array signal processing, transceiver design, localiza-
tion, integrated sensing and communication, mmWave/THz communications,
massive MIMO, and machine learning for communications. She is an
Executive Co-Chair of IEEE GLOBECOM 2026. She was the Sympo-
sium Co-Chair of various conferences, including IEEE VTC2024-Spring,
IEEE ICC 2021, 2019, and 2016, IEEE GLOBECOM 2016, and IEEE/CIC
ICCC 2019. She has served as an Editor for IEEE T RANSACTIONS ON
COGNITIVE COMMUNICATIONS AND NETWORKING (since 2025), IEEE
WIRELESS COMMUNICATIONS (since 2024), IEEE C OMMUNICATIONS
LETTERS (2023), Journal of Communications and Information Networks
(since 2021), IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS
(2018–2023), IEEE T RANSACTIONS ON COMMUNICATIONS (2018–2023),
and IEEE W IRELESS COMMUNICATIONS LETTERS (2017–2022). She was
an IEEE ComSoc Distinguished Lecturer from 2024 to 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 17 页

LU et al.: WIRELESS COMMUNICATION FOR LOW-ALTITUDE ECONOMY 16479
Bin Li (Senior Member, IEEE) received the
bachelor’s degree in automation and the master’s
degree in control science and engineering from
Harbin Institute of Technology, in 2005 and 2008,
respectively, and the Ph.D. degree in mathematics
and statistics from Curtin University in 2011. From
2012 to 2017, he visited the University of Western
Australia and Curtin University. He is currently a
Professor with the School of Aeronautics and Astro-
nautics, Sichuan University, Chengdu, China. His
research interests include signal processing, wireless
communications, optimization, and optimal control.
Shi Jin (Fellow, IEEE) received the B.S. degree in
communications engineering from Guilin University
of Electronic Technology, Guilin, China, in 1996, the
M.S. degree from Nanjing University of Posts and
Telecommunications, Nanjing, China, in 2003, and
the Ph.D. degree in information and communications
engineering from Southeast University, Nanjing, in
2007. From June 2007 to October 2009, he was
a Research Fellow with University College Lon-
don, Adastral Park Research Campus, London, U.K.
He is currently with the faculty of the National
Mobile Communications Research Laboratory, Southeast University. His
research interests include wireless communications, random matrix theory,
and information theory. He and his co-authors have received the 2011 IEEE
Communications Society Stephen O. Rice Prize Paper Award in the ﬁeld of
communication theory, the 2024 IEEE Communications Society Marconi Prize
Paper Award, the IEEE Vehicular Technology Society 2023 Jack Neubauer
Memorial Award, the 2022 Best Paper Award, and the 2010 Young Author
Best Paper Award by the IEEE Signal Processing Society. He is serving as
an Area Editor for IEEE T RANSACTIONS ON COMMUNICATIONS and IET
Electronics Letters. He was an Associate Editor of IEEE T RANSACTIONS
ON WIRELESS COMMUNICATIONS , IEEE C OMMUNICATIONS LETTERS , and
IET Communications.
Rui Zhang (Fellow, IEEE) received the B.Eng.
(Hons.) and M.Eng. degrees from the National
University of Singapore, Singapore, and the Ph.D.
degree from Stanford University, Stanford, CA,
USA, all in electrical engineering.
From 2007 to 2009, he was a Research Scientist
with the Institute for Infocomm Research, A*STAR,
Singapore. In 2010, he joined the Department
of Electrical and Computer Engineering, National
University of Singapore, where he is currently a
Provost’s Chair Professor. He is also an Adjunct
Professor with the School of Science and Engineering, The Chinese University
of Hong Kong, Shenzhen, China. He has published over 600 papers, all in the
ﬁeld of wireless communications and networks. He has been listed as a Highly
Cited Researcher by Thomson Reuters/Clarivate Analytics since 2015. His
current research interests include intelligent surfaces, reconﬁgurable antennas,
radio mapping, non-terrestrial communications, wireless power transfer, and
AI and optimization methods.
Dr. Zhang is a fellow of the Academy of Engineering Singapore. He
was a recipient of the Sixth IEEE Communications Society Asia–Paciﬁc
Region Best Young Researcher Award in 2011, the Young Researcher Award
of National University of Singapore in 2015, the Wireless Communications
Technical Committee Recognition Award in 2020, the IEEE Signal Processing
and Computing for Communications (SPCC) Technical Recognition Award in
2021, the IEEE Communications Society Technical Committee on Cognitive
Networks (TCCN) Recognition Award in 2023, and the IEEE James Evans
Avant Garde Award in 2025. His works received 18 IEEE Best Journal
Paper Awards, including the IEEE Marconi Prize Paper Award in Wireless
Communications in 2015 and 2020; the IEEE Signal Processing Society Best
Paper Award in 2016; the IEEE Communications Society Heinrich Hertz Prize
Paper Award in 2017, 2020, and 2022; and the IEEE Communications Society
Stephen O. Rice Prize in 2021. He served as the TPC co-chair or an organizing
committee member for over 30 international conferences. He was an elected
member of the IEEE Signal Processing Society SPCOM Technical Committee
from 2012 to 2017 and SAM Technical Committee from 2013 to 2015. He
is the Chair of the IEEE Communications Society Wireless Communications
Technical Committee (WTC) Award Committee. He served as the Vice Chair
for the IEEE Communications Society Asia–Paciﬁc Board Technical Affairs
Committee from 2014 to 2015 and a member of the Steering Committee of
IEEE W IRELESS COMMUNICATIONS LETTERS from 2018 to 2021 and the
IEEE Communications Society Wireless Communications Technical Commit-
tee (WTC) Award Committee from 2023 to 2025. He served as an Editor
for several IEEE journals, including IEEE T RANSACTIONS ON WIRELESS
COMMUNICATIONS from 2012 to 2016, IEEE J OURNAL ON SELECTED
AREAS IN COMMUNICATIONS : Green Communications and Networking
Series from 2015 to 2016, IEEE T RANSACTIONS ON SIGNAL PROCESSING
from 2013 to 2017, IEEE T RANSACTIONS ON GREEN COMMUNICATIONS
AND NETWORKING from 2016 to 2020, and IEEE T RANSACTIONS ON
COMMUNICATIONS from 2017 to 2022. He serves as an Editorial Board
Member for npj Wireless Technology. He was a Distinguished Lecturer of
IEEE Signal Processing Society and IEEE Communications Society from
2019 to 2020.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:05:40 UTC from IEEE Xplore.  Restrictions apply.
