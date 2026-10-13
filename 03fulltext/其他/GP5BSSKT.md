---
title: "MIMO-PASS Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems"
zotero_key: "GP5BSSKT"
pdf_key: "NUDLOEU2"
doi: "10.1109/tcomm.2026.3668156"
collection: "其他"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# MIMO-PASS Uplink and Downlink Transmission via MIMO Pinching-Antenna Systems — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

arXiv:2503.03117v1  [cs.IT]  5 Mar 2025
1
MIMO-PASS: Uplink and Downlink Transmission
via MIMO Pinching-Antenna Systems
Ali Bereyhi, Member , IEEE, Chongjun Ouyang, Member , IEEE, Saba Asaad, Member , IEEE,
Zhiguo Ding, Fellow, IEEE, and H. Vincent Poor, Life Fellow, IEEE
Abstract—Pinching-antenna systems (PASSs) are a recent
ﬂexible-antenna technology that is realized by attaching s imple
components, referred to as pinching elements, to dielectric waveg-
uides. This work explores the potential of deploying PASS fo r
uplink and downlink transmission in multiuser MIMO setting s.
For downlink PASS-aided communication, we formulate the op ti-
mal hybrid beamforming, in which the digital precoding matr ix
at the access point and the location of pinching elements on
the waveguides are jointly optimized to maximize the achiev able
weighted sum-rate. Invoking fractional programming and Ga uss-
Seidel approach, we propose two low-complexity algorithms to
iteratively update the precoding matrix and activated loca tions
of the pinching elements. We further study uplink transmiss ion
aided by a PASS, where an iterative scheme is designed to addr ess
the underlying hybrid multiuser detection problem. We vali date
the proposed schemes through extensive numerical experime nts.
The results demonstrate that using a PASS, the throughput in
both uplink and downlink is boosted signiﬁcantly as compare d
with baseline MIMO architectures, such as massive MIMO and
classical hybrid analog-digital designs. This highlights the great
potential of PASSs, making it a promising reconﬁgurable ant enna
technology for next-generation wireless systems.
Index Terms —Reconﬁgurable antennas, downlink beamform-
ing, multiuser detection, weighted sum-rate maximization .
I. I NTRODUCTION
S
HANNON’S coding theorem characterizes the maximum
data rate achievable for a given transmission model, i.e.,
for a given channel [1]. In the context of wireless communica -
tions, the transmission model is traditionally considered to be
speciﬁed by environmental factors such as path loss, diffra c-
tion, and scattering that are beyond human control and ma-
nipulation. This assumption has shaped the evolution of con -
ventional wireless multiple-input multiple-output (MIMO ) de-
signs, including fully digital and hybrid analog-digital M IMO
systems, where the primary focus has been on optimizing
transceiver architectures to maximize throughput [2], [3] .
As wireless systems move to higher frequency band, such as
millimeter or terahertz waves, the impact of severe path los s
becomes more pronounced [4], [5]. The high attenuation at
these frequencies imposes signiﬁcant challenges in mainta in-
ing reliable links over moderate to long distances. The depl oy-
ment of massive MIMO has emerged as an effective solution
in this respect, as large arrays can form highly directional
A. Bereyhi is with Department of Electrical and Computer Eng ineering at
University of Toronto; email: ali.bereyhi@utoronto.ca.
Chongjun Ouyang is with School of Electronic Engineering an d Computer
Science at Queen Mary University of London; email: c.ouyang@qmul.ac.uk.
Saba Asaad is with Department of Electrical Engineering and Computer
Science at Y ork University; email: asaads@yorku.ca.
Zhiguo Ding is with School of Electrical and Electronic Engi neering at
University of Manchester; email: zhiguo.ding@manchester .ac.uk.
H. Vincent Poor is with Department of Electrical and Compute r Engineering
at Princeton University; email: poor@princeton.edu.
beams that compensate for the detrimental effects of path-
loss. This empirical observation, combined with theoretic al
advances such as channel hardening [6], [7], has challenged
this conventional assumption that the data transmission mo del
in wireless systems is inherently uncontrollable, suggest ing a
paradigm shift toward emerging technologies that can activ ely
reconﬁgure the channel [8].
Although channel reconﬁguration has recently gained in-
creased attention, it has been an active research area for a
considerable time [9]–[12]. Primary studies considered ba sic
approach such as antenna selection , in which the channel
is modiﬁed by dynamically choosing a subset of available
antennas [13]–[15]. Inspired by this idea, several lines of work
suggest reconﬁgurable transceiver architectures which ca n
modify the communication link between the transmitter and
receiver [12]. The results of these early studies demonstra te the
potential beneﬁts of spatial adaptability in wireless syst ems.
Recent advancements in channel reconﬁguration have led to
the development of more sophisticated technologies, such a s
reconﬁgurable intelligent surfaces (IRSs) [16], ﬂuid ante nnas
[17], and movable antenna systems [18]. In this work, we in-
vestigate a recently-proposed reconﬁgurable technology c alled
pinching-antenna s ystems (PASSs) to understand its potentials
for efﬁcient channel modiﬁcation in wireless systems.
A. Reconﬁgurable Antenna T echnologies
Advances in antenna technology have led to several break-
throughs in the design of intelligent components for dynami c
environment reconﬁguration [19]–[22]. IRS technology is a n
example, which can apply controllable phase-shifts to the i n-
cident electromagnetic waves [8], [23]. Through these tuna ble
phase-shifts, IRSs can reconﬁgure the end-to-end effectiv e
channel. An IRS can be seen as a component that realizes
programmable propagation environments. By properly placing
IRSs in a network, various favorable propagation propertie s,
such as bypassing obstruction, improving coverage, channe l
hardening, and reducing multi-user interference can be rea lized
in a real-time and cost-efﬁcient manner [19], [24]–[26].
Fluid antennas represent another technology that provides a
means for intelligent reconﬁguration of the wireless mediu m
[17], [27]–[30]. Fluid antennas deploy conductive liquids ,
such as mercury or galinstan, encapsulated within a dielect ric
holder to form an adaptive illumination. By controlling the
displacement, shape, and volume of the liquid conductor, ﬂu id
antennas can adjust their electrical and radiation propert ies in
real time. This ﬂexibility enables dynamic beam-steering a nd
enhanced spatial diversity, making ﬂuid antennas advantag eous
for compact devices with limited physical space [17]. Despi te
this, these components face challenges with respect to scal -

2
ability, due to physical limitation in the implementation a nd
control of liquid-based illuminating elements on large sca les
[31]. To address this issue, the movable antenna technology
has been introduced, which realizes the reconﬁgurable prop -
erties of ﬂuid antennas by mechanical means [18].
In movable antennas, the location of the antenna elements
can be dynamically tuned within a designated region of the
transceiver array. Through this tuning, these antenna arra ys
can reconﬁgure the propagation environment [18], [32]. Unl ike
ﬂuid antennas, the movement is controlled mechanically in
this technology, enabling it to be scaled more efﬁciently [3 3].
From an abstract viewpoint, the movement of antennas in thes e
arrays can be seen as antenna selection with a large virtual
array of passive antennas, whose elements are located at the
possible positions on moving antennas [34], [35]. The large
array in this case is however realized implicitly via mechan ical
displacements. This allows for efﬁcient implementation by
bypassing the signiﬁcant loss introduced by switching in th e
direct implementation of antenna selection [36].
B. Pinching-Antenna Systems
Despite the gains reported for the above-mentioned recon-
ﬁgurable technologies, the integration of these technolog ies
remains challenging due to the need for real-time control,
high implementation cost and complexity, and limited abili ty
to address large-scale path loss . To address these challenges,
several lines of research have focused on developing altern a-
tive efﬁcient reconﬁgurable technologies for wireless sys tems.
P ASS is one of the most recent advancements in this direction
proposed in [37], [38]. This proposal is motivated by the
demonstration given by Fukuda et al. in DOCOMO 2022 [39],
which showcases that a array beam pattern can be constructed
by attaching low-cost dielectric materials (referred to as pinch-
ing elements , such as plastic clothespins, at arbitrary points
along a dielectric waveguide. Inspired by this demonstrati on,
P ASS technology suggests to realize large-scale reconﬁgurable
arrays via long dielectric waveguides, in which the propaga tion
pattern is tuned by the location of the pinching elements.
P ASSs offer ﬂexibility in establishing or strengthening li ne-
of-sight (LoS) links by adding or removing pinches to waveg-
uides [37]. Unlike the earlier proposals for reconﬁgurable
arrays, this modiﬁcation can be easily implemented via sign if-
icantly low-cost pinching elements. This has attracted sev eral
lines of recent research in the literature. The ergodic rate
achieved by a P ASS is analyzed [37] using stochastic geometry
tools. The array-gain achieved by a P ASS is examined in [40].
Low-complexity algorithms for optimizing the locations of
pinching elements along a single waveguide are proposed in
[41]–[43]. These studies collectively highlight the super iority
of P ASSs over conventional ﬁxed-location antenna systems i n
enhancing communication performance.
C. Contributions
The initial study in [37] has investigated the potential of
P ASSs for MIMO communication, considering basic multi-
user scenarios. The scope of this study is further extended i n
recent lines of work, such as [41], [43]. Motivated by these,
this work aims to study the potential of P ASSs for multiuser
MIMO communication; a gap that has not been explored
in the literature. In this respect, we study the problem of
multiuser detection and beamforming in the uplink and down-
link of a multiuser MIMO system whose access point (AP)
employs a P ASS-aided transceiver technology. The main line s
of contribution in this study are as follows: ( i) we consider
a generic multi-antenna P ASS, in which the AP is equipped
with an array of waveguides each being equipped with multipl e
reconﬁgurable pinching elements. For this setting, we form u-
late the uplink and downlink transmission and characterize
the effective vector multiple access and broadcast channel s
between the P ASS-aided AP and users. ( ii) Using the analytic
characterization of the uplink and downlink channels, we
develop hybrid multi-user detection and beamforming designs,
in which the location of the pinching elements on the waveg-
uides and the digital units are designed jointly, such that t he
weighted achievable sum-rate is maximized. ( iii) Invoking
fractional programming (FP), block coordinate descent (BC D)
algorithm, and Gauss-Seidel approach, we develop several
iterative algorithms for multi-user detection task in upli nk and
the beamforming task in downlink. The proposed algorithms
simultaneously optimize the digital units, i.e., precodin g ma-
trix and linear receiver, at the AP and adjust the locations o f
the pinching elements. ( iv) We investigate the efﬁciency of
the proposed designs in both uplink and downlink scenarios
through extensive numerical experiments, where we compare
different variation of our proposed P ASS-aided transmissi on
with baseline MIMO schemes; namely, conventional MIMO,
massive MIMO and hybrid analog-digital architectures. Nu-
merical results demonstrate that the proposed P ASS-aided
transceiver can achieve signiﬁcantly higher throughput, a s
compared with conventional ﬁxed-location antenna systems .
This highlights great potentials of this technology to addr ess
the targets considered for next generations of wireless sys tems.
The remainder of this paper is organized as follows: Sec-
tion II formulates the problem and characterizes the uplink
and downlink channels in a P ASS. Hybrid beamforming is
studied in Section III, and iterative algorithms are develo ped
in Section IV. Section V develops algorithmic approaches
for multiuser detection. Numerical results are presented i n
Section VI. Finally, the paper is concluded in Section VII.
Notation V ectors, and matrices are shown by bold lower-
case and bold upper-case letters, respectively. The transp ose,
conjugate and conjugate-transpose of H are denoted by HT,
H∗ and HH, respectively. The N ×N identity matrix is shown
by IN , and R and C denote the real axis and complex plane,
respectively. For set {1, . . . , N}, we use shortened notation
[N ]. We denote expectation by /BX {.} , and CN
(
η, σ2) is the
complex Gaussian distribution with mean η and variance σ2.
When the summation range is clear from the context, we omit
it and denote only the index, e.g., ∑k.
II. S YSTEM MODEL
Consider M dielectric waveguides, each equipped with N
pinching elements that can freely move across the waveguide .1
The elements on each waveguide act as an isotropic illuminat or
1In practice, each element can be realized via multiple eleme nts, each
covering one part of the waveguide.

3
Pinching Antenna 
Access 
Point 
Fig. 1: Schematic of MIMO-PASS setting: each waveguide is pi nched
with multiple elements.
whose signals are the phase-shifted version of the signal fe d to
the waveguide. We assume that waveguides are extended over
the x-axis at the altitude a in an array formed on the y-axis
with each two waveguides being distanced d. The location of
the pinching element n on the waveguide m ∈ [M ] in the
Cartesian coordinate is given by vm,n = [ ℓm,n, (m − 1)d, a],
where 0 ≤ ℓm,n ≤ Lm is the position of the element on the
waveguide m with length Lm, assuming that the signal is fed
to the wave guide at ℓm,0 = 0; see Fig. 1. Note that ℓm,n for
m ∈ [M ] and n ∈ [N ] are the design parameters that we tune
to optimize the system throughput.
The radiating waveguides are fed by an AP that aims to
serve K single-antenna users. The users are distributed within
a known two-dimensional area, e.g., a rectangular region. W e
denote the location of user k by uk = [ xk, yk, 0], assuming
that the users are located in the xy-plane.
A. Characterizing Downlink Channel
We start with downlink transmission, in which each waveg-
uide transmits a separate signal to the users. Let zm denote
the signal fed to waveguide m. The pinching elements on this
waveguide radiate phase-shifted versions of zm. The radiated
signal from the pinching elements can hence be represented
as tm = zmem, where the radiation vector em ∈ CN reads as
em = [pm,1 exp {−jθm,1} , . . . , pm,N exp {−jθm,N }]T (1)
with pm,n and θm,n being the attenuation factor and phase-
shift at pinching element n on waveguide m. Note that θm,n is
determined by the location of the element n. Recalling that the
signal on the waveguide m is fed at ℓm,0 = 0 , and denoting
the carrier frequency with f , we can write θm,n = κirefℓm,n,
where κ = 2π/λ is the wave number with λ = c/f denoting
the wavelength and c being the speed of light. The coefﬁcient
iref is further the refractive index of the waveguides.
By neglecting the minor propagation loss in the dielectric,
each waveguide m can be modeled as a passive power dis-
tribution component whose radiated power does not exceed
or drop from the one fed to it by zm. This means that we
have ∑n |pm,n|2 = 1. Neglecting the propagation loss further
implies that the power radiated from each element is the same .
We can hence conclude that in this case pm,n =
√
1/N for
all n ∈ [N ]. The radiation vector em is hence simpliﬁed as
em = 1√N [exp {−jθm,1} , . . . ,exp {−jθm,N }]T . (2)
We consider classical indoor scenarios. It is hence practic al
to assume that users are in the LoS of the waveguides, and
that the signals received from the non-LoS paths are negligi ble
in amplitude and separable in delay, as compared with those
received over the LoS. Let yk denote the signal received by
user k. Considering LoS channels, we can write yk as
yk =
∑
m
hTk,mtm + εk (3)
where εk ∈ C is complex-valued additive white Gaussian
noise with mean zero and variance σ2, i.e., εk ∼ CN (0, σ2),
and hk,m ∈ CN denotes the vector of channel coefﬁcients
from pinching elements on waveguide m to user k. The entry
n of the channel vector hk,m can be explicitly expressed in
terms of the location of the user and the pinching element as
hk,m,n = ξαk
exp {−jκDk,m (ℓm,n)}
Dk,m (ℓm,n) (4)
where ξ = λ/4π is the coefﬁcient proportional to the effective
surface of the pinching elements, 2 Dk,m (ℓ) is a function
computing the distance between the location ℓ on the m-th
waveguide and user k, i.e.,
D2k,m (ℓ) = ( ℓ − xk)2 + (md − d − yk)2 + a2, (5)
and αk captures the shadowing experienced by user k.
Remark 1: We assume that shadowing is invariant in n. In
limited areas, e.g., moderate-size indoor environments, t his is a
practical approximation [37]. Nevertheless, in a setting w here
shadowing varies from an element to another, the shadowing
coefﬁcients depend on both m and n, i.e., αk,m,n.
The end-to-end channel between the waveguide array and
the user k depends on the element locations. Deﬁning location
vector of the waveguide m as lm = [ ℓm,1, . . . , ℓm,N ]T, this
means that the channel between waveguide m and user k
is a function of lm. Considering the radiation vector of
waveguide m, we can write the end-to-end channel between
the waveguide array and the user k as
yk =
∑
m
gk,m (lm) zm + εk = gTk (L) z + εk (6)
where z = [ z1, . . . , zM ]T denotes the transmitted beam, and
gk (L) = [ gk,1 (l1) , . . . , gk,M (lM )]T with L = [l1, . . . ,lM ] ∈
RN ×M collecting locations of elements and gk,m (lm) ∈ C
being the effective channel between the waveguide m and the
user k given by
gk,m (lm) = hTk,mem (7a)
= ξαk
∑
n
exp {−jκ (Dk,m (ℓm,n) + irefℓm,n)}√
N Dk,m (ℓm,n)
. (7b)
The vector downlink channel is hence given by
y = GT (L) z + ε, (8)
where G(L) ∈ CM×K is the downlink channel deﬁned as
G (L) = [ g1 (L) · · · gK (L)] , (9)
and ε ∈ CK is Gaussian noise. This describes a standard
vector Gaussian broadcast channel whose channel matrix is
tunable by the activated locations of the pinching elements .
B. Characterizing Uplink Channel
We now consider uplink transmission in which the array of
waveguides receives the user signals. Let us denote the upli nk
signal transmitted by user k via xk. Assuming that the system
2We assume that pinching elements behave as isotropic antenn as.

4
operates in the time-domain duplexing (TDD), the received
signal by pinching element n on waveguide m is given by
rem,n = ∑
k
hk,m,nxk + νem,n (10)
where hk,m,n is the channel coefﬁcient between user k and
pinching element n on waveguide m given in (4), and νem,n
is Gaussian noise with variance ς 2, i.e., νem,n ∼ CN (0, ς2).
Following our assumption on passiveness of the waveguides,
we can write the superimposed signal received through waveg -
uide m at the AP as
˜rm =
∑
n
exp {−jκℓm,n} rem,n (11a)
=
∑
k
∑
n
hk,m,n exp {−jκℓm,n} xk + ˜νm, (11b)
where ˜νm is aggregated noise process, i.e., ˜νm = ∑n νem,n.
The independence of νem,n implies that ˜νm is zero-mean
Gaussian with variance N ς2. Considering (7a), we can write∑
n
hk,m,n exp {−jκℓm,n} =
√
N gk,m (lm) . (12)
Hence, the signal received by the AP can be written as
˜rm =
√
N
K∑
k=1
gk,m (lm) xk + ˜νm =
√
N ˜gTm (lm) x + ˜νm, (13)
where ˜gm (lm) = [ g1,m (lm) · · · gK,m (lm)]T is the m-th row
of G (L) deﬁned in (9), and x = [ x1 · · · xK] represents the
vector of uplink signals. Noting that scaling at the receive d
side does not impact transmission quality, we can compactly
represent the effective uplink channel as
r = G (L) x + ν, (14)
where r = [r1 · · · rM ]T with rm = ˜rm/√N representing the
effective received signal, and ν = [ ν1 · · · νM ]T with νm =
˜νm/
√
N being effective zero-mean noise with variance ς 2.
As a dual case to downlink transmission, the end-to-end
uplink channel describes a Gaussian multiple access channe l.
The channel matrix in this case is the transpose of the down-
link channel, which is the direct result of channel reciprocity
in the TDD mode. Similar to downlink case, the key advantage
in this system is the reconﬁgurability of the channel matrix by
the locations of the pinching elements.
III. H YBRID BEAMFORMING IN A DOWNLINK PASS
Considering the equivalent end-to-end channel for the P ASS
system, we can achieve multiplexing gain via digital pre-
coding. The design of precoding however describes a hybrid
beamforming problem, in which both the digital precoder and
locations of the pinching elements are to be optimized jointly.
A. Joint Digital Precoding and Location Tuning
Let s = [s1, . . . , sK]T denote the signals the AP intends to
send, with sk ∈ C being the encoded information signal of
user k. We assume that the information signals are zero-mean
unit-variance stationary processes satisfying
/BX
{
ssH} = I. (15)
The AP sets the signal fed to each waveguide to be a linear
superposition of these signals, i.e., it sets zm = ˜wTms, for
some vector of coefﬁcients ˜wm ∈ CK speciﬁed for waveguide
m. The transmit signal by the waveguide array can hence
be represented as z = Ws, where W = [ ˜w1, . . . , ˜wM ]T is
the precoding matrix. We further impose a power constraint
restricting the average transmit power to be bounded by a
positive downlink power Pd, i.e., /BX
{
‖z‖2
}
≤ Pd. Using (15),
this reduces to tr
{
WWH} ≤ Pd.
The signal received by user k is written as
yk = gTk (L) Ws + εk (16)
which depends on W and L. It is worth mentioning that while
W represents a digital beamforming, the tuning of matrix L
describes beam-design in the analog domain. The joint design
of W and L can hence be interpreted as hybrid beamforming.
B. Downlink W eighted Sum-Rate
To proceed with the beamforming design, let us ﬁrst rewrite
the received signal at user k as
yk =
∑
j
gTk (L) wjsj + εk (17)
with wj denoting the j-th column vector of W collecting the
j-th entries of ˜wm for m ∈ [M ]. We refer to wj as the digital
beamforming vector of user j. The achievable downlink rate
for user k in this case can be written as
Rdk (W, L) = log (1 + SINRdk (W, L)) , (18)
where SINRdk (W, L) denotes the signal to interference and
noise ratio (SINR) at user k deﬁned as
SINRdk (W, L) =
⏐⏐gTk (L) wk⏐⏐2∑
j⁄=k
⏐⏐gTk (L) wj⏐⏐2 + σ2 . (19)
The achievable weighted sum-rate in the downlink vector
channel can hence be written as
Rd (W, L) = ∑
k
λkRdk (W, L) , (20)
for some non-negative weights λk that are proportional to the
expected quality of service for user k.
C. Optimal Beamforming Design
The ultimate goal is to maximize the achievable weighted
sum-rate for a given power budget Pd and physical limitations.
We hence formulate optimal hybrid beamforming as
max
W,L
Rd (W, L) s.t. tr {WHW} ≤ Pd and C1, C2 (21)
where we deﬁne C1 and C2 as
C1 : 0 ≤ ℓm,n ≤ Lm (22a)
C2 : ∆ℓ + ℓm,n ≤ ℓm,n+1, (22b)
for n ∈ [N ] and m ∈ [M ] recalling that Lm denotes the length
of the waveguide m.
In addition to restricting the location of pinching element s
with the length of waveguides, i.e., C1, C2 guarantees that the
element n is located behind element n + 1 with a distance
that exceeds ∆ℓ. This is physically the case when pinching
elements are tuned by sliding tracks on waveguides. The
parameter ∆ℓ > 0 is the minimum spacing required to prevent
mutual coupling between two neighboring elements.
Although the formulation in (21) matches the physical limi-
tations of the P ASS, one can observe that the second constrai nt

5
in (22b), i.e., ∆ℓ + ℓm,n ≤ ℓm,n+1, can be further simpliﬁed.
This is intuitive, as exchanging two pinching elements on a
waveguide in this case does not change signal propagation. I n
other words, the throughput is invariant to permutation of
pinching elements. This is shown in the following lemma.
Lemma 1: Consider L ∈ RN ×M . Let ˜L ∈ RN ×M be
another location matrix whose columns are a permutation of
the columns of L. Then, for any W ∈ CM×K we have
Rd (W, L) = Rd(W, ˜L). (23)
Proof: From (7a), we see that by replacing lm with a per-
mutation ˜lm, the sum does not change implying gk,m (lm) =
gk,m(˜lm). Noting that Rd (W, L) depends on the locations
only through the channels, the proof is completed.
Using this permutation invariance, the optimal hybrid pre-
coding scheme simpliﬁes to
max
W,L
Rd (W, L) (24a)
s.t. tr
{
WHW} ≤ Pd and lm ∈ Lm, (24b)
where lm denotes the m-th column of L, and we deﬁne the
feasible set Lm for m ∈ [M ] as
Lm =
{
l ∈ RN : 0 ≤ ℓn ≤ Lm and
|ℓn − ℓn′ | ≥ ∆ℓ for n, n′ ∈ [N ]} (25)
with ℓn in (25) denoting the n-th entry of l.
Remark 2: It is worth mentioning that the permutation
invariance is implied by the invariance of the shadowing acr oss
the pinching elements. In fact, when the shadowing varies, i .e.,
we have path-loss coefﬁcients of the form αk,m,n that vary
with n, one needs to solve the original problem in (21) for
optimal hybrid beamforming. See Remark 1 for more details.
IV. E FFICIENT ALGORITHM FOR HYBRID BEAMFORMING
The optimization in (24a) is non-convex, and its global so-
lution is not computed in polynomial time. In this section,
we develop an efﬁcient suboptimal algorithm. The derivatio n
follows three major steps: ( i) we ﬁrst rewrite (24a) in a
variational form with no power constraint. ( ii) Using FP, we
transform the variational problem into a dual optimization with
quadratic objective. ( iii) Using BCD [44] and Gauss-Seidel
[45] methods, a two-tier iterative solver is developed.
A. V ariational Design Problem
We start with transforming the problem (24a) into a vari-
ational form without the power constraint, whose dual form
exhibits a smoother objective function. The variational op ti-
mization is derived using the following lemmas.
Lemma 2 (Equality power constraint): The optimal solution
to(24a) satisﬁes the power constraint with equality, i.e.,
tr
{
WH⋆ W⋆} = Pd, (26)
for any W⋆ that is a solution to (24a).
Proof: The proof is concluded by contradiction: let the
precoding matrix ˆW = [ ˆw1, . . . , ˆwK] be a solution to problem
(24a) that satisﬁes the constraint with inequality, i.e.,
ˆP ≜ tr
{
ˆWH ˆW} = ∑
j
‖ ˆwj‖2 < P d. (27)
We now deﬁne ρ = Pd/ ˆP and a scaled solution ¯wj = √ρ ˆwj.
Note that the scaled matrix ¯W = [ ¯w1, . . . , ¯wK] satisﬁes
the power constraint with equality, i.e., tr
{ ¯WH ¯W} = Pd.
Replacing into the deﬁnition (19), it is readily shown that
SINRdk ( ¯W, L) > SINRdk( ˆW, L), (28)
for any L. This means that using ¯W, the AP can achieve a
strictly larger weighted sum-rate. This contradicts the in itial
assumption and completes the proof.
Using Lemma 2, we can rewrite the optimization in (24a)
in an unconstrained form whose solution determines explici tly
the solution of (24a). This is shown in the following lemma.
Lemma 3 (Unconstrained Equivalent Problem): For a given
L, let ¯W = [ ¯w1, . . . , ¯wK] denote a solution to the following
unconstrained weighted sum-rate maximization
max
W
∑
k
λk log(1 + SINR
d
k (W, L)), (29)
where SINR
d
k (W, L) for W = [w1, . . . ,wK] is deﬁned as
SINR
d
k (W, L) =
⏐⏐gTk (L) wk⏐⏐2
∑
j⁄=k
⏐⏐gTk (L) wj⏐⏐2 + σ2Pd ∑j ‖wj‖2 . (30)
Then, a solution to (24a) is determined from ¯W as
˘W =
√
Pd
tr
{ ¯WH ¯W} ¯W. (31)
Proof: It is readily shown that the solution in (31) satisﬁes
the power constraint with equality and that
SINR
d
k
(
˘W, L
)
= SINR dk
(
˘W, L
)
, (32)
for any L. This implies that the objective function in (24a)
attains the same value as the one in (29). Noting that ¯W is the
optimal solution to (29), we can conclude that ˘W maximizes
the objective in (24a) among all beamforming matrices that
satisfy the power constraint with equality. Lemma 2 further
indicates that no solution with inequality constraint exis ts.
This implies that ˘W maximizes the objective in (24a). This
completes the proof.
Using Lemma 3, the optimal hybrid beamforming is equiv-
alently represented by the following variational optimiza tion
max
W,l
¯Rd (W, L) s.t. lm ∈ Lm (33a)
where ¯Rd (W, L) is given by
¯Rd (W, l) = ∑
j
λk log
(
1 + SINR
d
k (W, L)
)
(34)
with SINR
d
k (W, L) being deﬁned in (30). It is worth noting
that the power limit in the variational form is incorporated
through SINR
d
k (W, L) and the optimal precoding matrix is
computed from the solution by the scaling given in (31).
B. Solution via Fractional Programming
The variational problem in (33a) describes a classical prob -
lem of maximizing sum of log ratios, whose solution can be
efﬁciently approximated via FP as outlined in this sub-sect ion.
We start our derivations by deﬁning the feasible set S for the
variational problem as
S = CM×K × L1 × · · · × LM , (35)
and denoting S = (W, L) for brevity.

6
The FP approach suggests converting the sum-of-log-ratios
problem, i.e., the variational problem (33a), into a quadra tic
form by means of the Lagrange and quadratic dual transforms
[46], [47]. Although the resulting dual problem is yet non-
convex, it describes a smooth objective landscape, whose op -
timal point can be efﬁciently approximated by BCD algorithm
[44]. For a quick introduction to FP, see [48, Section IV]. In
the sequel, we follow this approach: we start with determini ng
the Lagrange dual objective for (33a), which is given by (36)
given at the top of the next page for some ωn ≥ 0. The key
property of this dual objective is the Lagrange duality, whi ch
implies that Smax for the dual problem
(Smax, ωmax) = argmax
S∈S,ω∈RK+
Ld (S, ω) (37)
recovers the solution of the optimization (33a), and that th e
optimal values of the objectives in both problems are identi cal
[46], [47]. Note that the Lagrange dual problem is not convex .
Nonetheless, its solution can be efﬁciently approximated v ia
the BCD algorithm: we initiate some S = (W, L) and iterate
between the following two marginal optimization problems.
1) For ﬁxed S, solve the marginal optimization
ω⋆ = argmax
ω∈RK+
Ld (S, ω) . (38)
This problem describes a standard convex optimization
whose solution is given by
ω⋆k = SINRdk (W, L) . (39)
2) Set ωk = ω⋆k, i.e., the solution of ﬁrst marginal problem,
and update S with the marginal solution S⋆ given by
S⋆ = argmax
S∈S
Ld (S, ω⋆) (40)
The second marginal optimization reduces to
S⋆ = argmax
S∈S
∑
k
λk (1 + ω⋆k) ⏐⏐gTk (L) wk⏐⏐2
∑
j
⏐⏐gTk (L) wj⏐⏐2 + σ2Pd ∑j ‖wj‖2 , (41)
which describes the problem of maximizing sum of fractional
functions. This can be transformed into a quadratic form usi ng
the quadratic transform [46], [47], as outlined in the sequel.
To solve the optimization in (41), we determine its quadrati c
dual objective, which is given by (42) at the top of the next
page for some complex auxiliary variables qk ∈ C [46],
[47]. The quadratic duality implies that the solution of (41 )
is recovered by solving the dual problem [46], [47]
max
S∈S,q∈CK
Qd (S, q) . (43)
This dual form has a quadratic objective which describes a
smoother landscape, and hence its solution can be approx-
imated more efﬁciently. Note that the dual optimization is
again non-convex through q, multiplicative expressions, and
the functional form of gk (L). Similar to the Lagrange dual
problem, we approximate the dual solution via BCD: starting
with S, the algorithm iterates between the following two steps.
1) Fix S and ﬁnd q⋆ by solving (42) marginally for q.
2) Update S by solving (42) marginally for S, i.e.,
S⋆ = argmax
S∈S
Qd (S, q⋆) (44)
The solution to the ﬁrst marginal problem is given by
q⋆k = Pd
√1 + ω⋆kgTk (L) wk
σ2tr {WWH} + Pdtr {WWHg∗k (L) gTk (L)} . (45)
The second marginal problem can be further written as
S⋆ = argmax
(W,L)∈S
Fd (W, L) , (46)
where the objective Fd (W, L) is given by
Fd (W, L) = 2 ℜ
{
tr
{
THGT (L) W}} (47)
− tr
{
GT (L) WWHG∗ (L) U} − σ2tr {U}Pd tr {WWH}
for T = QAΛ and U = QΛQH with Λ, A and Q being
Λ = diag {λ1, . . . , λK} (48a)
A = diag
{√
1 + ω⋆1, . . . ,√1 + ω⋆K} (48b)
Q = diag {q⋆1, . . . , q⋆K} . (48c)
The ﬁnal step is to approximate the solution of the marginal
problem in (46). This is challenging due to two facts: ( i) it is
non-convex, and ( ii) it shows too many local minima, due to
its oscillating form. We address these challenges by develo ping
an iterative solver via the BCD and Gauss-Seidel schemes.
C. Two-tier Iterative Algorithm
To solve the optimization in (46), we ﬁrst note that the
problem is marginally convex in both W. This suggests that a
BCD-based outer loop can efﬁciently approximate the optima l
digital precoding matrix: the outer loop iterates between t he
following two steps.
1) Fix L, and ﬁnd W⋆ as the marginal solution to (46).
2) Set W = W⋆ and solve (46) marginally for L.
The ﬁrst marginal problem describes a standard regularized
linear inverse problem whose solution is given by
W⋆ = (G∗ (L) UGT (L) + γdIM )−1 G∗ (L) T. (49)
with γd = σ2tr {U}/Pd.
Remark 3: The digital precoder (49) can be seen as regular-
ized zero-forcing (RZF) precoding with an effective channe l
given in terms of G (L), T, and U whose regularizer is set
to σ2tr {U}/Pd. This is intuitive, as for a ﬁxed channel,
i.e., ﬁxed location L, the optimal linear precoder is readily
computed by an optimally-tuned RZF.
The second marginal problem in the outer loop deals with
an objective whose dependency on L is given in terms of
exponential sums. The global optimum of this problem is not
feasibly found. We hence develop an inner-loop algorithm to
iteratively approximate its solution. The classical appro ach
to tackle these problems is to invoke greedy approaches,
e.g., stepwise regression. In the sequel, we develop a greed y
approach based on the Gauss-Seidel scheme to efﬁciently
approximate the solution of this marginal problem.
D. Greedy Algorithm for Location Optimization
The inner loop solves the following optimization
max
L
2ℜ
{
tr
{
EGT (L)}} − tr {FG∗ (L) UGT (L)} (50a)
s.t. lm ∈ Lm for m ∈ [M ], (50b)
where we deﬁne E = WTH and F = WWH.

7
Ld (S, ω) = ∑
k
λk

log (1 + ωk) − ωk + (1 + ωk) ⏐⏐gTk (L) wk⏐⏐2∑
j
⏐⏐gTk (L) wj⏐⏐2 + σ2P ∑j ‖wj‖2

 (36)
Qd (S, q) = ∑
k
λk

2√1 + ω⋆kℜ {q∗kgTk (L) wk} − |qk|2 ∑
j
⏐⏐gTk (L) wj⏐⏐2 − σ2Pd |qk|2 ∑j ‖wj‖2

 (42)
To tackle the problem in (50), we invoke the Gauss-Seidel
approach, which suggests to sequentially update the locati ons
[45]. In this approach, each location is updated individual ly by
treating other locations as constants. This way, each locat ion is
optimized to reﬁne analog beamforming optimized in previous
iterations. To this end, let us consider the element n on
waveguide m and ﬁx ℓm′,n′ for (m′, n′) ⁄= (m, n). The scalar
problem for this element is given by
max
ℓ
2ℜ
{
tr
{
E ˜GTm,n (ℓ)}} − tr {F ˜G∗m,n (ℓ) U ˜GTm,n (ℓ)}
s.t. 0 ≤ ℓ ≤ Lm and ∆ℓ ≤ |ℓm,i − ℓ| for i ⁄= n, (51)
where ˜Gm,n (ℓ) represents matrix G (L), when all locations
but ℓm,n = ℓ are set to their ﬁxed values, i.e.,
˜Gm,n (ℓ) = [ ˜g1, . . . ,˜gm−1, ˜gnm (ℓ) , ˜gm+1, . . . ,˜gM ]T, (52)
where ˜gm′ for m′ ⁄= m represents the m′-th rows of G (L),
when all entries of L except ℓm,n are set to their ﬁxed values,
and ˜gnm (ℓ) is the m-th row as a function of ℓm,n = ℓ.3 Note
that the scalar objective of (51) depends on the optimizatio n
variable only through ˜gm (ℓ) whose k-th entry is given by
[˜gnm (ℓ)]k = Π k,m (ℓ) + ∑
n′⁄=n
Πk,m (ℓm,n′) (53)
where we deﬁne the function Πk,m (ℓ) as
Πk,m (ℓ) = ξαk
exp {−jκ (Dk,m (ℓ) + iref ℓ)}√
N Dk,m (ℓ)
. (54)
By simple lines of derivation, (51) is rewritten as
max
ℓ
2ℜ
{
bTm˜gnm (ℓ)} − [F]m,m˜gnHm (ℓ) U˜gnm (ℓ) (55)
s.t. 0 ≤ ℓ ≤ Lm and ∆ℓ ≤ |ℓm,i − ℓ| for i ⁄= n, (56)
where bm ∈ CK is deﬁned as
bm = am −
∑
m′⁄=m
[F]m,m′ UT˜g∗m′, (57)
with aTm being the m-th row of E. Using (53) and treating
ℓm′,n′ for (m′, n′) ⁄= (m, n) as ﬁxed, we can simplify (77) to
max
ℓ
fm(ℓ) (58a)
s.t. 0 ≤ ℓ ≤ Lm and ∆ℓ ≤ |ℓm,i − ℓ| for i ⁄= n, (58b)
where fm(ℓ) is deﬁned as
fm(ℓ) =
∑
k
2ℜ {ζk,mΠk,m (ℓ)} − ϑk,m |Πk,m (ℓ)|2 . (59)
for scalars ζk,m = [ bm]k and ϑk,m = [ F]m,m[U]k,k. This is
3Noting that ℓm′,n for m′ ⁄= m is treated as ﬁxed, the argument ℓm′,n in
˜gm′ for m′ ⁄= m is dropped. We also use superscript n in ˜gnm (ℓ) to indicate
that that ℓ is the location of the n-th element.
a classical scalar optimization problem within a ﬁxed inter val,
which can be effectively solved via grid search. Using an L-
point grid for interval [0, Lm], i.e.,
ˆLm ≜
{
0, Lm
L − 1 , 2LmL − 1 , . . . , Lm
}
a nearly-optimal ℓm,n is computed as
ℓ⋆m,n = argmax
ℓm∈ˆLm\˘Lm,n
fm(ℓm,n), (60)
where the set ˘Lm,n includes all grid points that violate the
minimum distance criteria, i.e.,
˘Lm,n = ˆLm∩ {ℓ : 0 ≤ ℓ ≤ Lm and (61)
∆ℓ ≥ |ℓm,i − ℓ| for i ⁄= n} .
Consequently, the optimal locations in L are computed by
looping this grid reach over all entries of L.
Remark 4: Note that classical gradient-based methods can-
not solving the scalar problem in (58a) efﬁciently. This is
due to the fact taht the objective fm(·) contains numerous
stationary points caused by oscillations of the cosine term .
E. Final Algorithm: Convergence and Complexity
Using the Gauss-Seidel approach, we can complete the
inner-loop of the two-tier solver: in Step 2 of the BCD loop in
Section IV -C, we update the L by solving (60) with W being
set to W⋆ is given by (49). This concludes the derivation
of the algorithm. The overall FP-BCD algorithm for solving
problem (24a) is summarized in Algorithm 1.
Convergence It is straightforward to show that the proposed
algorithm converges to a stationary point. To show this, we ﬁ rst
note that the objective in each step of the BCD algorithm, i.e .,
the marginal objectives in the outer loop, is a non-decreasi ng
function of the underlying variables. This guarantees that in
each iteration, the objective is increasing. On the other ha nd,
the downlink power constraint guarantees that the achievab le
weighted sum-rate is bounded from above, and therefore the
iterative increments of the objective in the algorithm are
limited by this upper bound. This implies that Algorithm 1
always converges to a stationary point. Noting that this poi nt
is a combination of marginal maximizers, we can further
conclude that this stationary point is a local maximizer.
Complexity The computational complexity of Algorithm 1
is dominated by (49) which is the classical operation for lin ear
RZF. To see this point, we ﬁrst note that ﬁnding the optimal
dual variables, i.e., ωk and qk, imposes computational com-
plexity of the order O(K 2M ). The inner loop, i.e., algorithm

8
Algorithm 1 FP-BCD Hybrid Beamforming
Require: Weights λk for k ∈ [K]
1: Initialize ǫ, feasible W and L, and resolution L
2: repeat
3: Update dual variables ωk and qk via (39) and (45) for
k ∈ [K]
4: Computed T and U from the dual variables via (48)
5: Update W via (49)
6: for m = 1 : M do
7: Compute fm(ℓ) via (59)
8: for n = 1 : N do
9: Update ℓn,m via (60)
10: end for
11: end for
12: until fractional increase of objective falls below ǫ
13: Scale W as W =
√
Pd/tr {WHW}W
14: return Precoding matrix W and location matrix L
A, further is linear in all dimensions and performs a grid
search over a set of L grid points in each iteration. Its com-
putational complexity is hence O(N M LK). The computation
of W deals with matrix inversion and imposes the computa-
tional complexity of the order O(KM 2 + M 3). Comparing
these operations, we observe that the latter is the one which
dominates the order of complexity in the overall algorithm.
Noting that (49) is a classical linear precoding operation,
one can conclude that the proposed algorithm imposes the
same order of complexity as in classical linear precoding.
More precisely, Algorithm 1 scales with system dimensions
as O(2K 2M I + KM 2I + M 3I + M N LKI) with I being
the number of iterations in the outer loop. Our numerical
investigations depict that the required number of iteratio ns
is rather small implying that the complexity of the proposed
algorithm is comparable to that of classical linear precodi ng.
F . Alternative Algorithm via Zero-F orcing
Algorithm 1 maintains reasonable complexity for moderate-
size P ASSs. However, its computational burdens might be
relatively high for large P ASSs. In this subsection, we pres ent
an alternative scheme based on zero-forcing (ZF) precoding
which optimizes the location matrix for optimal effective Z F.
This bypasses the need for solving the dual problem, i.e., th e
outer loop, allowing for optimization in a single loop.
Let us assume that M > K . In this case, we can zero-force
the effective downlink channel for a given L as [49]
W =
√
Pd
tr {Γ (L)} G∗ (L) Γ (L) , (62)
with Γ (L) =
(
GT (L) G∗ (L))−1. Using (62), the achievable
downlink weighted sum-rate is given by
Rd (W, L) =
K∑
k=1
λk log
(
1 + Pd
σ2
1
tr {Γ (L)}
)
. (63)
The joint design of L and W in this case reduces to
maximizing the objective in (63) against L. Noting that the
logarithm function is strictly increasing, one can alterna tively
Algorithm 2 Single-Loop Hybrid Beamforming
Require: Weights λk for k ∈ [K]
1: Initialize ǫ, feasible W and L, and resolution L
2: repeat
3: for m ∈ [M ] and n ∈ [N ] do
4: Solve problem (68) using grid search
5: end for
6: until fractional decrease of objective falls below ǫ
7: Calculate the ZF digital detector W using (62)
8: return Precoding matrix W and location matrix L
ﬁnd the optimal L via the following optimization
min
L
tr {Γ (L)} s.t. lm ∈ Lm for m ∈ [M ]. (64)
Note that this optimization directly optimizes the ZF preco ding
matrix, and hence no BCD loop, i.e., the outer loop in
Algorithm 1, is needed in this case.
Similar to the FP-BCD scheme, this problem can also
be solved via the Gauss-Seidel approach and grid search.
Nonetheless, calculating the matrix inversion in Γ (L) at each
search point is computationally intensive. To mitigate thi s
burden, we invoke the Sherman-Morrison lemma to develop
a rank- 1 decomposition for this trace term, in the case of
M > K . To this end, let us focus on the scalar optimization
when we set ℓm,n = ℓ and remaining locations in L ﬁxed: in
this case, we have
tr {Γ (L)} = tr
{(
˜GTm,n (ℓ) ˜G∗m,n (ℓ))−1} (65a)
= tr
{(
˜gnm (ℓ) ˜gnHm (ℓ) + ˘GTm ˘G∗m
)−1}
, (65b)
where ˜Gm,n (ℓ) is deﬁned in (52), and we deﬁne ˘Gm as G (L)
missing the m-th column, i.e.,
˘Gm = [ ˜g1, . . . ,˜gm−1, ˜gm+1, . . . ,˜gM ]T. (66)
Using the Sherman-Morrison lemma, we can write(
˜gnm (ℓ) ˜gnHm (ℓ) + ˘GTm ˘G∗m
)−1
= Γm − Γm˜gnm (ℓ) ˜gnHm (ℓ) Γm1 + ˜gnHm (ℓ) Γm ˜gnm (ℓ) , (67)
where Γm =
(
˘GTm ˘G∗m
)−1
exists due to M > K . The scalar
problem is hence written as
max
ℓ
˜gnHm (ℓ) Γ2m ˜gnm (ℓ)
1 + ˜gnHm (ℓ) Γm˜gnm (ℓ) (68a)
s.t. 0 ≤ ℓ ≤ Lm and ∆ℓ ≤ |ℓm,i − ℓ| for i ⁄= n, (68b)
which can be solved using a grid search similar to (60).
The algorithm is given in Algorithm 2. The non-decreasing
shape of the objective in each iteration and its boundedness
implies that this algorithm converges to a local minimum.
V. M ULTIUSER DETECTION IN AN UPLINK PASS
We now consider uplink transmission in the P ASS, where users
transmit signals to the AP over the Gaussian multiple access
channel. In this case, the key task is to design a multiuser
receiver, which jointly determines the receiver matrix and
activated locations of pinching elements, such that the upl ink

9
throughput is optimized. Similar to downlink beamforming,
this describes a hybrid design. However, unlike the downlin k
case, the optimal digital detector in the uplink case can be
directly characterized via the well-known minimum mean
squared error (MMSE) detector. This allows for more efﬁcien t
algorithmic developments in this case.
A. Hybrid Design for Multiuser Detection
Let sk ∈ C denote the encoded information signal at user k.
We assume that the signals of different users are independen t,
zero-mean, and unit-variance. User k scales its signal as xk =√Pusk, where Pu > 0 denotes the uplink power. The effective
received signal at the AP is given by
r = G (L) x + ν =
√
Pu
∑
k
skgk (L) + ν. (69)
To estimate the transmitted signals, i.e., s1, . . . , sK, the AP
employs a bank of K linear ﬁlters in the digital domain. Let
mk ∈ CM denote the receiver that estimates the signal of user
k. Using this linear receiver, the signal of user k is estimated
as ˆsk = mTk r, which depends on both digital receiver mk
and the analog receive beam speciﬁed by L. This implies that
the detection task is a hybrid problem in which the digital
components, i.e., mk for k ∈ [K], and analog degrees of
freedom, i.e., L, are to be designed jointly.
B. Uplink W eighted Sum-Rate
To quantify the quality of estimates at the AP, various
metrics can be used, e.g., mean squared error (MSE) or achiev -
able rates. To be consistent with the downlink performance
metric, we adopt the uplink achievable weighted sum-rate.
Considering the signal model, the achievable rate for user k
over the uplink channel is given by
Ruk (mk, L) = log (1 + SINR uk (mk, L)) , (70)
where SINRuk (mk, L) represents the uplink SINR at the AP
for user k, deﬁned as
SINRuk (mk, L) =
⏐⏐mTk gk (L)⏐⏐2
∑
j⁄=k
⏐⏐mTk gj (L)⏐⏐2 + ς 2Pu ‖mk‖2 . (71)
The uplink weighted sum-rate is then given by
Ru (M, L) = ∑
k
βkRuk (mk, L) , (72)
computed for some non-negative weights βk. In this notation,
the matrix M ∈ CM×K is the digital receiver matrix deﬁned
as M = [m1 · · ·mK]. The goal is to design M and L, such
that the achievable uplink weighted sum-rate is maximized.
C. Optimal Hybrid Design for Uplink
The per-user SINR given in (71) features a generalized
Rayleigh quotient. This is maximized when we set mk to
be the MMSE detector [49]. As a result, the optimal digital
detector for a given L is readily given by the corresponding
MMSE matrix, i.e., [50]
M = G∗ (L)
(
GT (L) G∗ (L) + ς 2
Pu
IK
)−1
. (73)
Substituting (73) into (72), we can represent Ruk (mk, L) as
given in (74) at the top of the next page.
Algorithm 3 Greedy Hybrid Receiver
Require: Weights βk for k ∈ [K]
1: Initialize ǫ, feasible W and L, and resolution L
2: repeat
3: for m ∈ [M ] and n ∈ [N ] do
4: Solve problem (77) using the grid search
5: end for
6: until fractional increase of objective in (76) falls below ǫ
7: Determine optimal digital detector M using (73)
8: return Receiver matrix M and location matrix L
Using Sylvester’s determinant identity, the weighted sum-
rate can be rewritten as
Ru (M, L) = β∑ log det
(
IK + Puς 2 GH (L) G (L))
−
K∑
k=1
βk log det
(
IK−1 + Puς 2 GHk (L) Gk (L)) , (75)
where β∑ = ∑k βk, and Gk (L) ∈ CM×K−1 is a reduced
form of G (L) with its k-th column missing. Noting that the
resulting weighted sum-rate only depends on L, we can write
the throughput optimization problem as
max
L
Ru (L) s.t. lm ∈ Lm for m ∈ [M ], (76)
with Lm deﬁned in (25), where we drop M for compactness.
Similar to Algorithms 1 and 2, we can tackle the problem in
(76) via the Gauss-Seidel approach. Due to the similarity, w e
skip the detailed derivation for this case. By omitting term s
irrelevant with ℓm,n, we equivalently simplify to the following:
max
ℓ
β∑ log
(
1 + Pu
ς 2 ˜gnTm (ℓ) ˜Γm˜gn∗m (ℓ)
)
−
∑
k
βk log
(
1 + Pu
ς 2 ˜gnTm\k (ℓ)˜Γm\k ˜g∗m\k (ℓ)
)
(77a)
s.t. 0 ≤ ℓ ≤ Lm and ∆ℓ ≤ |ℓm,i − ℓ| for i ⁄= n, (77b)
where we deﬁne
˜Γm =
(
IK + Puς 2 ˘GHm ˘Gm
)−1
˜Γm\k =
(
IK + Puς 2 ˘GHm\k ˘Gm\k
)−1
with ˘Gm deﬁned in (66) and ˘Gm\k being its reduced version
whose k-th column is dropped. Similarly, ˜gnm\k (ℓ) denotes
˜gnm (ℓ) whose k-th entry is dropped. As in Algorithms 1 and
2, this problem can be solved efﬁciently by grid search. The
ﬁnal algorithm is presented in Algorithm 3.
VI. N UMERICAL INVESTIGATIONS
We now validate the proposed algorithms through numerical
experiments. Through the numerical simulations, we invest i-
gate P ASSs and the proposed algorithms in two major aspects:
(i) we evaluate the convergence and precision of the proposed
algorithms. ( ii) We compare MIMO-P ASSs against classical
MIMO baselines in the same simulated environment to assess
the order of gain achieved by this technology.

10
Ruk (mk, L) = log

det

IM + gk (L) gHk (L)

∑
j⁄=k
gj (L) gHj (L) + ς 2Pu IM


−1


 (74)
1 2 3 4 5 6 7 8
Number of Iterations
0
1
2
3
4
5
6
7Weighted Sum-Rate [bps/Hz]
ZF, Pd = -20 dBm
FP-BCD, Pd = -20 dBm
ZF, Pd = -10 dBm
FP-BCD, Pd = -10 dBm
ZF, Pd = 0 dBm
FP-BCD, Pd = 0 dBm
(a) Downlink
1 2 3 4 5 6 7 8
Number of Iterations
0
3
6
9Weighted Sum-Rate [bps/Hz]
Pu = -20 dBm
Pu = -10 dBm
Pu = 0 dBm
(b) Uplink
Fig. 2: Convergence of the proposed iterative algorithms fo r MIMO-PASS uplink and downlink transmission.
A. Experimental Setting
Consider a rectangular region with side lengths Dx and
Dy along the x- and y-axes, respectively, centered at
[Dx/2, Dy/2, 0]. Within this region, K single-antenna users
are randomly and uniformly distributed. A schematic illust ra-
tion of this setup is provided in Fig. 1. The M waveguides are
assumed to be positioned at a height of a = 5 m and cover the
entire area. These waveguides are spaced uniformly along th e
y-axis with a separation distance of d = Dy/(M − 1). Each
waveguide has a length of Dx, i.e., Lm = Dx for m ∈ [M ],
and the antenna elements are spaced at least half a wavelengt h
apart, i.e., ∆ℓ = λ/2. For the simulations, the following
parameters are adopted unless otherwise speciﬁed: we consi der
M = 5 waveguides, each equipped with N = 6 pinching
elements and fed by a dedicated RF chain, serving K = 4
users. The side lengths of the rectangular region are set to
Dx = 50 m and Dy = 6 m. The noise variance in both uplink
and downlink is σ2 = ς 2 = −90 dBm. The carrier frequency
is f = 28 GHz, and the refractive index is iref = 1.44 [37]. We
use uniform weights, i.e., λk = βk = 1/K, in both uplink and
downlink. Furthermore, the path-loss is computed via the fr ee-
space propagation model, i.e., αk = 1 for k ∈ [K]. Numerical
results are obtained by averaging 500 random seeds.
For implementation of the proposed algorithms, i.e., Algo-
rithms 1, 2, and 3, the predeﬁned threshold is set to ǫ = 10 −3.
For the one-dimensional grid search, the grid resolution is set
to L = 10 5, unless stated otherwise. Since the performance of
the FP-BCD algorithms may depend on the initial parameters,
the digital precoding matrix and location matrix in Algorit hm 1
are initialized using the results obtained from the ZF-base d
algorithm, i.e., Algorithm 2. For the ZF-based beamforming
and MMSE-based detection designs, the locations of the
pinching elements are initialized randomly.
B. Baseline Architectures
We compare a MIMO-P ASS with M waveguides each hav-
ing N pinching elements against three benchmark technolo-
gies: conventional MIMO , massive MIMO (mMIMO) , and
hybrid beamforming-based MIMO (hMIMO) . To ensure a fair
comparison, the following conﬁgurations are considered fo r
the baselines: (1) The conventional MIMO system is equipped
with M antennas, each connected to a dedicated RF chain,
and employs fully digital signal processing. Speciﬁcally, FP-
based digital precoding is used in the downlink, and MMSE-
based digital detection is applied in the uplink. From an
implementation perspective, this setup incurs approximat ely
the same RF cost as the proposed P ASS, as it utilizes the
same number of RF chains at the AP . (2) The mMIMO
system features an array of M N antennas, each with its own
RF chain, and employs fully digital signal processing for
both uplink and downlink. The beamforming for downlink
and uplink is designed using FP-based and MMSE-based
methods, respectively. Due to its large number of RF chains,
this baseline represents a signiﬁcantly more expensive des ign
compared to both conventional MIMO and the proposed P ASS.
(3) The hMIMO system utilizes a hybrid transceiver with
M RF chains, each connected to N antenna elements via a
network of tunable phase shifters. It employs hybrid analog -
digital signal processing for both uplink and downlink, whi ch
is designed using the algorithms in [51]. While this setup
imposes the same RF cost as the proposed P ASS, it may suffer
from poor power efﬁciency due to high power splitting losses .
In simulations, all baselines are based on a half-wavelengt h
spaced uniform linear array centered within the square regi on
at [Dx/2, Dy/2, a], and aligned along the y-axis.
C. Numerical Results
Convergence. Fig. 2 illustrates the convergence behavior of
the proposed algorithms for different values of transmitte d
power. Speciﬁcally, Fig. 2(a) shows the downlink weighted
sum-rate achieved by the FP-BCD and ZF-based methods
as a function of the number of iterations. As observed, the
weighted sum-rate gradually increases with the number of
iterations and eventually converges to a stable value for al l

11
102 104 106
Grid Search Resolution
2  
2.5
3  
3.5
4  
4.5
5  
5.5
6  
6.5Weighted Sum-Rate [bps/Hz]
Conventional MIMO
Conventional mMIMO
Conventional hMIMO
Pinching antenna (FP-BCD)
Pinching antenna (ZF)
35%
67%
203%
(a) Downlink. Pd = 0 dBm
102 104 106
Grid Search Resolution
1.5
2.5
3.5
4.5
5.5
6.5
7.5
8.5Weighted Sum-Rate [bps/Hz]
Conventional MIMO
Conventional mMIMO
Conventional hMIMO
Pinching antenna
38%
82%
338%
(b) Uplink. Pu = 0 dBm
Fig. 3: Weighted sum-rate vs the grid search resolution. Arr ows indicate the gain achieved by MIMO-PASS over the baselin es.
considered values of Pd, which conﬁrms the effectiveness of
the proposed algorithms. Furthermore, increasing the tran smit
power improves the system throughput, i.e., the weighted su m-
rate. Notably, the weighted sum-rate at the initial point of the
FP-BCD method is the same as that at the converged point
of the ZF-based method, as the FP-BCD method is initialized
using the optimized results from the ZF-based method. Fig.
2(b) demonstrates the convergence behavior of the MMSE-
based algorithm for optimizing the uplink weighted sum-rat e.
Under the considered setup, the proposed algorithms conver ge
within 5 iterations, verifying their fast convergence.
Grid Search Resolution. As the one-dimensional grid search
is utilized in Algorithms 1, 2, and 3, the achievable uplink
and downlink throughput is inﬂuenced by the grid resolution ,
i.e., the number of discrete points along the waveguide, L.
To illustrate this impact, Fig. 3(a) and Fig. 3(b) plot the
downlink and uplink weighted sum-rates achieved by the
proposed algorithms as a function of the grid search resolut ion
L, respectively. As shown in these graphs, the weighted sum-
rates for both downlink and uplink increase monotonically
with the grid search resolution. Additionally, we observe t hat
the achieved sum-rates saturate when L reaches approximately
105. This suggests that setting the grid resolution to 105 nearly
attains the performance upper bound of the P ASS.
For a thorough study, we also compare the weighted sum-
rate achieved by the MIMO-P ASS with those achieved by the
baseline ﬁxed-location antenna systems, i.e., MIMO, mMIMO,
and hMIMO. As seen in both Fig. 3(a) and Fig. 3(b), the
MIMO-P ASS achieves signiﬁcantly better weighted sum-rate
performance compared to these baselines. Notably, even whe n
compared to a fully digital massive MIMO system with the
same number of antennas as the P ASS, the P ASS achieves a
gain of more than 30%. This gain further increases to over
200% when compared to small-scale fully digital MIMO sys-
tems. Such promising improvements are primarily attribute d
to the capability of P ASSs to ﬂexibly tune pinching location s
on waveguides, enabling collaborative establishment of st rong
and stable LoS paths, i.e., a nearly-wired transmission link.
Downlink W eighted Sum-Rate. Fig. 4(a) shows the downlink
weighted sum-rate as a function of the maximum total transmi t
power Pd, which compares performance of the MIMO-P ASS
with the conventional ﬁxed-location antenna systems. The
results indicate that the sum-rate increases with Pd for all
schemes. Notably, the P ASS achieves signiﬁcantly higher
throughput than the conventional systems, particularly in the
medium- and high-power regimes. From the graph, we observe
that increasing the grid search resolution, L, improves the
weighted sum-rate achieved by the P ASS, which is consistent
with the what we observed in Fig. 3(a). Another important
observation is that in the medium- and high-power regimes,
the ZF-based method achieves nearly the same performance
as the FP-BCD method. However, in the low-power regime,
the FP-BCD method enables the P ASS to achieve a higher
sum-rate than the ZF-based method. This is expected, as ZF
beamforming is asymptotically optimal in the high signal to
noise ratio (SNR) regime [49], [50]. This also explains the
behavior observed in Fig. 2(a) and Fig. 3(a), where the ZF-
based method achieves nearly the same performance as the
FP-BCD method.
Fig. 4(b) illustrates the sum-rate as a function of the side
length of the square region along the x-axis, Dx, while Dy is
ﬁxed. As the side length increases, the performance gain of t he
P ASS over the conventional baseline improves signiﬁcantly .
This is because a larger side length increases the average
distance between users and the center of the region, resulti ng
in higher path loss for the conventional systems. In contras t,
the P ASS can ﬂexibly position its radiating elements closer to
the users, which effectively enhances the system throughpu t.
Furthermore, as shown in the graph, as Dx increases, the
FP-BCD method outperforms the ZF-based method. This is
because a larger side length leads to more severe path loss,
which creates a low-SNR scenario where ZF performs poorly.
Fig. 4(c) further depicts the weighted sum-rate as a functio n
of the number of pinching elements along each waveguide, N .
As shown in the graph, the sum-rates achieved by both the
MIMO-P ASS setting and the baseline mMIMO and hMIMO
schemes increase monotonically with the number of pinching
elements. This is due to the increased spatial DoFs and array
gains provided by adding more antennas. The graph also high-
lights the weighted sum-rate performance gain of the P ASS
over the baseline systems. Speciﬁcally, tuning the locatio ns
of the pinching elements introduces sum-rate improvements
of 27% and 76% compared to the mMIMO and hMIMO
schemes, respectively. These results, along those in Fig. 4 (a)

12
-30 -20 -10 0 10
Transmit Power [dBm]
0
2
4
6
8
10Weighted Sum-Rate [bps/Hz]
Conventional MIMO
Conventional mMIMO
Conventional hMIMO
Pinching antenna (FP-BCD)
Pinching antenna (ZF)
-25 -20
0.5
1  
L = 500
L = 1E5
(a) Transmit power Pd
20 30 40 50 60 70 80
Side Length [m]
1
2
3
4
5
6
7Weighted Sum-Rate [bps/Hz]
Conventional MIMO
Conventional mMIMO
Conventional hMIMO
Pinching antenna (FP-BCD)
Pinching antenna (ZF)
(b) Side length Dx. Pd = 0 dBm
2 4 6 8 10
Number of Pinching Antennas
2
3
4
5
6
7Weighted Sum-Rate [bps/Hz]
Conventional MIMO
Conventional mMIMO
Conventional hMIMO
Pinching antenna (FP-BCD)
Pinching antenna (ZF)
27%
76%
(c) Number of PAs N . Pd = 0 dBm
Fig. 4: Achievable downlink weighted sum-rate: arrows indi cate the gain achieved by MIMO-PASS over the baselines.
and Fig. 4(b), validate the effectiveness of the MIMO-P ASS
in enhancing the throughput in downlink transmission.
Uplink W eighted Sum-Rate. Fig. 5(a) depicts the achiev-
able uplink weighted sum-rate as a function of the per-user
transmit power Pu. It is observed that, across the consid-
ered range of transmit powers, the proposed MMSE-based
method effectively optimizes the locations of the pinching
elements, enabling the P ASS to achieve higher throughput than
conventional ﬁxed-location antenna systems. Additionall y, we
observe that increasing the grid search resolution L improves
the weighted sum-rate achieved by the MIMO-P ASS. This is
consistent with the earlier results in Fig. 3(b).
Fig. 5(b) further depicts the weighted sum-rate as a functio n
of the number of users, K. The sum-rates achieved by both the
MIMO-P ASS and the baseline systems decrease monotonically
as the number of users increases, primarily due to the rise
in inter-user interference. As shown in the graph, when the
number of users does not exceed the number of waveguides or
RF chains, i.e., K ≤ M = 5, the P ASS achieves a higher sum-
rate than the baseline schemes. However, once K > M , the
sum-rate achieved by the P ASS decays rapidly. This is becaus e
the P ASS is essentially a hybrid beamforming system. When
the number of users exceeds the number of RF chains, the
system cannot provide sufﬁcient DoFs to effectively mitiga te
inter-user interference. This explains why the fully digit al
mMIMO system outperforms the MIMO-P ASS when M = 8.
Nevertheless, compared to ﬁxed-location antenna systems w ith
the same number of RF chains, i.e., conventional MIMO and
hMIMO, the MIMO-P ASS still can signiﬁcantly enhance the
throughput due to its ability to ﬂexibly tune the locations o f
antennas and establish a strong LoS link.
VII. C ONCLUSION
We have studied uplink and downlink transmission in a
multiuser MIMO-P ASS system, in which the AP deploys
an array of pinched waveguides at its front-end. Invoking
the FP framework, BCD scheme and Gauss-Seidel approach,
several low-complexity algorithms for hybrid beamforming
in downlink and detection in uplink were developed. These
algorithms solve a hybrid problem, where the digital units, i.e.,
precoding or receiver matrix, is optimized jointly with the ac-
tivated locations of the pinching elements on the waveguide s.
The effectiveness of the proposed algorithms was validated
through several numerical experiments. The results of this
study showcase the signiﬁcant superiority of MIMO-P ASS
over conventional ﬁxed-location designs including both ma s-
sive MIMO and the benchmark hybrid analog-digital archi-
tectures. Our results highlight the potential of P ASSs as a k ey
reconﬁgurable antenna system technology for next-generat ion
wireless systems urging for further research in this direct ion.
REFERENCES
[1] C. E. Shannon, “A mathematical theory of communication, ” Bell Syst.
Tech. J., vol. 27, no. 3, pp. 379–423, Jul. 1948.
[2] E. G. Larsson, O. Edfors, F. Tufvesson, and T. L. Marzetta , “Massive
MIMO for next generation wireless systems,” IEEE Commun. Mag. ,
vol. 52, no. 2, pp. 186–195, Feb. 2014.
[3] F. Sohrabi and W. Y u, “Hybrid analog and digital beamform ing for
mmwave OFDM large-scale antenna arrays,” IEEE J. Sel Areas Com-
mun., vol. 35, no. 7, pp. 1432–1443, Jul. 2017.
[4] T. S. Rappaport, S. Sun, R. Mayzus, H. Zhao, Y . Azar, K. Wan g, G. N.
Wong, J. K. Schulz, M. Samimi, and F. Gutierrez, “Millimeter wave
mobile communications for 5G cellular: It will work!” IEEE Access ,
vol. 1, pp. 335–349, 2013.
[5] I. F. Akyildiz, C. Han, Z. Hu, S. Nie, and J. M. Jornet, “Ter ahertz band
communication: An old problem revisited and research direc tions for
the next decade,” IEEE Trans. Commun. , vol. 70, no. 6, pp. 4250–4285,
Jun. 2022.
[6] B. M. Hochwald, T. L. Marzetta, and V . Tarokh, “Multiple- antenna
channel hardening and its implications for rate feedback an d scheduling,”
IEEE Trans. Inf. Theory , vol. 50, no. 9, pp. 1893–1909, Sep. 2004.
[7] Z. Chen and E. Bj¨ ornson, “Channel hardening and favorab le propagation
in cell-free massive MIMO with stochastic geometry,” IEEE Trans.
Commun., vol. 66, no. 11, pp. 5205–5219, Nov. 2018.
[8] S. Gong, X. Lu, D. T. Hoang, D. Niyato, L. Shu, D. I. Kim, and Y .-C.
Liang, “Toward smart wireless communications via intellig ent reﬂecting
surfaces: A contemporary survey,” IEEE Commun. Surveys Tuts., vol. 22,
no. 4, pp. 2283–2314, 4th Quart., 2020.
[9] B. A. Cetiner, E. Akay, E. Sengul, and E. Ayanoglu, “A MIMO system
with multifunctional reconﬁgurable antennas,” IEEE Antennas Wirel.
Propag. Lett., vol. 5, pp. 463–466, 2006.
[10] A. M. Sayeed and V . Raghavan, “Maximizing MIMO capacity in sparse
multipath with reconﬁgurable antenna arrays,” IEEE J. Sel. Topics Signal
Proc., vol. 1, no. 1, pp. 156–166, Jun. 2007.
[11] Z. Xu, X. Dong, and J. Bornemann, “Design of a reconﬁgura ble MIMO
system for THz communications based on graphene antennas,” IEEE
Trans. Terahertz Sci. Tech. , vol. 4, no. 5, pp. 609–617, Sep. 2014.
[12] S. Asaad, A. Bereyhi, M. A. Sedaghat, R. Mueller, and A. M . Rabiei,
“Asymptotic performance analysis of spatially reconﬁgura ble antenna
arrays,” in Proc. Int. ITG W orkshop Smart Antennas (WSA) . VDE,
Mar. 2017, pp. 1–8.
[13] A. F. Molisch and M. Z. Win, “MIMO systems with antenna se lection,”
IEEE Microw. Mag. , vol. 5, no. 1, pp. 46–56, Mar. 2004.
[14] H. Li, L. Song, and M. Debbah, “Energy efﬁciency of large -scale
multiple antenna systems with transmit antenna selection, ” IEEE Trans.
Commun., vol. 62, no. 2, pp. 638–647, Feb. 2014.
[15] S. Asaad, A. M. Rabiei, and R. R. M¨ uller, “Massive MIMO w ith antenna
selection: Fundamental limits and applications,” IEEE Trans. Wireless
Commun., vol. 17, no. 12, pp. 8502–8516, Dec. 2018.

13
-30 -20 -10 0 10
Transmit Power [dBm]
0
2
4
6
8
10
12Weighted Sum-Rate [bps/Hz]
Conventional MIMO
Conventional mMIMO
Conventional hMIMO
Pinching antenna (L = 1E5)
Pinching antenna (L = 500)
-25 -20
0.5
1  
1.5
(a) Transmit power Pu
2 3 4 5 6 7 8
Number of Users
2
4
6
8
10Weighted Sum-Rate [bps/Hz]
Conventional MIMO
Conventional mMIMO
Conventional hMIMO
Pinching antenna
(b) Number of users K. Pu = 0 dBm
Fig. 5: Weighted uplink sum-rate achieved by MIMO-PASS agai nst the uplink transmit power and number of users.
[16] Q. Wu and R. Zhang, “Towards smart and reconﬁgurable env ironment:
Intelligent reﬂecting surface aided wireless network,” IEEE Commun.
Mag., vol. 58, no. 1, pp. 106–112, Jan. 2020.
[17] K.-K. Wong, A. Shojaeifard, K.-F. Tong, and Y . Zhang, “F luid antenna
systems,” IEEE Trans. Wireless Commun., vol. 20, no. 3, pp. 1950–1962,
Mar. 2021.
[18] L. Zhu, W. Ma, and R. Zhang, “Movable antennas for wirele ss commu-
nication: Opportunities and challenges,” IEEE Commun. Mag. , vol. 62,
no. 6, pp. 114–120, Jun. 2024.
[19] G. C. Alexandropoulos, G. Lerosey, M. Debbah, and M. Fin k, “Recon-
ﬁgurable intelligent surfaces and metamaterials: The pote ntial of wave
propagation control for 6G wireless communications,” IEEE ComSoc
TCCN Newslett., vol. 6, no. 1, pp. 25–37, Jun. 2020.
[20] ¨O. ¨Ozdogan, E. Bj¨ ornson, and E. G. Larsson, “Intelligent reﬂe cting
surfaces: Physics, propagation, and pathloss modeling,” IEEE Wireless
Commun. Lett. , vol. 9, no. 5, pp. 581–585, May 2020.
[21] M. Konca and P . A. Warr, “A frequency-reconﬁgurable ant enna archi-
tecture using dielectric ﬂuids,” IEEE Trans. Antennas Propag. , vol. 63,
no. 12, pp. 5280–5286, Dec. 2015.
[22] J. M. Jornet and I. F. Akyildiz, “Graphene-based plasmo nic nano-
antenna for terahertz band communication in nanonetworks, ” IEEE J.
Sel. Areas Commun. , vol. 31, no. 12, pp. 685–694, Dec. 2013.
[23] Q. Wu, S. Zhang, B. Zheng, C. Y ou, and R. Zhang, “Intellig ent
reﬂecting surface-aided wireless communications: A tutor ial,” IEEE
Trans. Commun., vol. 69, no. 5, pp. 3313–3351, May 2021.
[24] Q. Wu and R. Zhang, “Intelligent reﬂecting surface enha nced wireless
network via joint active and passive beamforming,” IEEE Trans. Wireless
Commun., vol. 18, no. 11, pp. 5394–5409, Nov. 2019.
[25] A. Bereyhi, S. Asaad, C. Ouyang, R. R. M¨ uller, R. F. Scha efer, and
H. V . Poor, “Channel hardening of irs-aided multi-antenna systems: How
should IRSs scale?” IEEE J. Sel Areas Commun. , vol. 41, no. 8, pp.
2321–2335, Aug. 2023.
[26] B. Zheng, C. Y ou, and R. Zhang, “Double-IRS assisted mul ti-user
MIMO: Cooperative passive beamforming design,” IEEE Trans. Wireless
Commun., vol. 20, no. 7, pp. 4513–4526, Jul. 2021.
[27] W. K. New, K.-K. Wong, H. Xu, C. Wang, F. R. Ghadi, J. Zhang , J. Rao,
R. Murch, P . Ram´ ırez-Espinosa, D. Morales-Jimenez et al. , “A tutorial
on ﬂuid antenna system for 6G networks: Encompassing commun ication
theory, optimization methods and hardware designs,” IEEE Commun.
Surveys Tuts., Early Access, 2024.
[28] K.-K. Wong, W. K. New, X. Hao, K.-F. Tong, and C.-B. Chae, “Fluid
antenna system—part I: Preliminaries,” IEEE Commun. Lett. , vol. 27,
no. 8, pp. 1919–1923, Aug. 2023.
[29] K.-K. Wong, K.-F. Tong, and C.-B. Chae, “Fluid antenna s ystem—part
II: Research opportunities,” IEEE Commun. Lett. , vol. 27, no. 8, pp.
1924–1928, Aug. 2023.
[30] ——, “Fluid antenna system—part III: A new paradigm of di stributed
artiﬁcial scattering surfaces for massive connectivity,” IEEE Commun.
Lett., vol. 27, no. 8, pp. 1929–1933, Aug. 2023.
[31] K. K. Wong, A. Shojaeifard, K.-F. Tong, and Y . Zhang, “Pe rformance
limits of ﬂuid antenna systems,” IEEE Commun. Lett. , vol. 24, no. 11,
pp. 2469–2472, Nov. 2020.
[32] L. Zhu, W. Ma, B. Ning, and R. Zhang, “Movable-antenna en hanced
multiuser communication via antenna position optimizatio n,” IEEE
Trans. Wireless Commun. , vol. 23, no. 7, pp. 7214–7229, Jul. 2024.
[33] L. Zhu, W. Ma, W. Mei, Y . Zeng, Q. Wu, B. Ning, Z. Xiao, X. Sh ao,
J. Zhang, and R. Zhang, “A tutorial on movable antennas for wi reless
networks,” IEEE Commun. Surveys Tuts. , pp. 1–1, Early Access, 2025.
[34] L. Zhu, W. Ma, and R. Zhang, “Modeling and performance an alysis
for movable antenna enabled wireless communications,” IEEE Trans.
Wireless Commun., vol. 23, no. 6, pp. 6234–6250, Jun. 2024.
[35] W. Ma, L. Zhu, and R. Zhang, “MIMO capacity characteriza tion for
movable antenna systems,” IEEE Trans. Wireless Commun. , vol. 23,
no. 4, pp. 3392–3407, Apr. 2024.
[36] W. Mei, X. Wei, B. Ning, Z. Chen, and R. Zhang, “Movable-a ntenna po-
sition optimization: A graph-based approach,” IEEE Wireless Commun.
Lett., vol. 13, no. 7, pp. 1853–1857, Jul. 2024.
[37] Z. Ding, R. Schober, and H. V . Poor, “Flexible-antenna s ystems: A
pinching-antenna perspective,” 2024, arXiv preprint arXi v:2412.02376.
[38] Z. Y ang, N. Wang, Y . Sun, Z. Ding, R. Schober, G. K. Karagi annidis,
V . W. Wong, and O. A. Dobre, “Pinching antennas: Principles, applica-
tions and challenges,” 2025, arXiv preprint arXiv:2501.10 753.
[39] A. Fukuda, H. Y amamoto, H. Okazaki, Y . Suzuki, and K. Kaw ai,
“Pinching antenna: Using a dielectric waveguide as an anten na,” NTT
DOCOMO Technical J. , vol. 23, no. 3, pp. 5–12, Jan. 2022.
[40] C. Ouyang, Z. Wang, Y . Liu, and Z. Ding, “Array gain for pi nching-
antenna systems (PASS),” 2025, arXiv preprint arXiv:2501. 05657.
[41] Y . Xu, Z. Ding, and G. K. Karagiannidis, “Rate maximizat ion for
downlink pinching-antenna systems,” IEEE Wireless Commun. Lett. ,
Early Access, 2025.
[42] K. Wang, Z. Ding, and R. Schober, “Antenna activation fo r NOMA
assisted pinching-antenna systems,” 2024, arXiv:2412.13 969.
[43] S. A. Tegos, V . K. Papanikolaou, Z. Ding, and G. K. Karagi annidis,
“Minimum data rate maximization for uplink pinching-anten na systems,”
2024, arXiv:2412.13892.
[44] P . Tseng, “Convergence of a block coordinate descent me thod for
nondifferentiable minimization,” J. Optim. Theory Appl. , vol. 109, no. 3,
pp. 475–494, 2001.
[45] T. Sauer, Numerical Analysis. Upper Saddle River, NJ: Pearson Educ.,
2006.
[46] K. Shen and W. Y u, “Fractional programming for communic ation
systems—Part I: Power control and beamforming,” IEEE Trans. Signal
Process., vol. 66, no. 10, pp. 2616–2630, May 2018.
[47] ——, “Fractional programming for communication system s—Part II:
Uplink scheduling via matching,” IEEE Trans. Signal Process. , vol. 66,
no. 10, pp. 2631–2644, May 2018.
[48] S. Asaad, Y . Wu, A. Bereyhi, R. R. Mueller, R. F. Schaefer , and H. V .
Poor, “Secure active and passive beamforming in IRS-aided M IMO
systems,” IEEE Trans. Inf. F orensics Security , vol. 17, pp. 1300–1315,
2022.
[49] R. W. Heath Jr and A. Lozano, F oundations of MIMO Communication.
Cambridge, U.K.: Cambridge Univ. Press, 2018.
[50] E. Bj¨ ornson, M. Bengtsson, and B. Ottersten, “Optimal multiuser trans-
mit beamforming: A difﬁcult problem with a simple solution s tructure
[lecture notes],” IEEE Signal Process. Mag. , vol. 31, no. 4, pp. 142–148,
Jul. 2014.
[51] X. Y u, J.-C. Shen, J. Zhang, and K. B. Letaief, “Alternat ing minimization
algorithms for hybrid precoding in millimeter wave MIMO sys tems,”
IEEE J. Sel. Topics Signal Process. , vol. 10, no. 3, pp. 485–500, Apr.
2016.