---
title: "Deep Unfolding Learning Aided ISAC Transceiver Design"
zotero_key: "ZE5HNQHG"
pdf_key: "KUCPV2UA"
doi: "10.1109/TWC.2025.3568367"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Deep Unfolding Learning Aided ISAC Transceiver Design — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025 8681
Deep Unfolding Learning Aided ISAC
Transceiver Design
Jifa Zhang, Yongxu Zhu
 , Senior Member , IEEE, Nan Zhao
 , Senior Member , IEEE, Shi Jin
 , Fellow, IEEE,
Xianbin Wang
 , Fellow, IEEE, Derrick Wing Kwan Ng
 , Fellow, IEEE, and Naofal Al-Dhahir
 , Fellow, IEEE
Abstract—Integrated sensing and communication (ISAC) can
enhance spectral efﬁciency and facilitate the diverse emerg-
ing applications via sharing the same spectrum and hardware
between communication and sensing. However, effective opera-
tion of ISAC may suffer from high complexity. In this paper,
we develop a low-complexity deep unfolding learning-aided
transceiver design scheme for ISAC in a cluttered environment.
In particular, we optimize the transmit waveform and receive
ﬁltering to minimize the weighted sum of multi-user interference
power and the reciprocal of sensing signal-to-interference-plus-
noise ratio (SINR), while adhering to the constraints of a constant
modulus signal and waveform similarity. An alternating direction
method of multipliers (ADMM)-based iterative algorithm is ﬁrst
developed to address this non-convex optimization problem with
both equality and inequality constraints. To further reduce the
computational complexity, we develop two deep unfolding neural
networks (NNs), termed ADMM-DL-NET and ADMM-PGD-
NET, to handle this problem, which can unfold the underlying
ADMM-based iterative algorithm to a lightweight neural net-
work with learnable parameters and eliminate the need for the
bisection method by adopting the Uzawa’s method and projected
gradient descent, respectively. Simulation results demonstrate
that our proposed deep unfolding NNs can achieve comparable
performance to the ADMM-based iterative algorithm with sig-
niﬁcantly reduced complexity, and outperform the unsupervised
learning benchmarks in performance and number of learnable
parameters.
Index Terms —ADMM, clutter environment, deep unfolding,
ISAC, transceiver design.
Received 14 October 2024; revised 23 February 2025; accepted 5 May
2025. Date of publication 15 May 2025; date of current version 14 October
2025. The work of Nan Zhao was supported in part by the National Natural
Science Foundation of China (NSFC) under Grant U23A20271 and Grant
62271099. The work of Naofal Al-Dhahir was supported by the Erik Jonsson
Distinguished Professorship at The University of Texas at Dallas (UT-Dallas).
An earlier version of this paper was presented in part at the IEEE ICC 2025
[1]. The associate editor coordinating the review of this article and approving
it for publication was Y . Zhang. (Corresponding author: Nan Zhao.)
Jifa Zhang and Nan Zhao are with the School of Information and Com-
munication Engineering, Dalian University of Technology, Dalian, Liaoning
116024, China (e-mail: jifazhang@mail.dlut.edu.cn; zhaonan@dlut.edu.cn).
Yongxu Zhu and Shi Jin are with the National Communications
Research Laboratory, Southeast University, Nanjing 210018, China (e-mail:
yongxu.zhu@seu.edu.cn; jinshi@seu.edu.cn).
Xianbin Wang is with the Department of Electrical and Computer
Engineering, Western University, London, ON N6A 5B9, Canada (e-mail:
xianbin.wang@uwo.ca).
Derrick Wing Kwan Ng is with the School of Electrical Engineering and
Telecommunications, University of New South Wales, Sydney, NSW 2052,
Australia (e-mail: w.k.ng@unsw.edu.au).
Naofal Al-Dhahir is with the Department of Electrical and Computer
Engineering, The University of Texas at Dallas, Richardson, TX 75080 USA
(e-mail: aldhahir@utdallas.edu).
Digital Object Identiﬁer 10.1109/TWC.2025.3568367
I. I NTRODUCTION
N
OW ADAYS, the roll out of numerous emerging applica-
tions in the ﬁfth-generation (5G) mobile networks pose
a heterogeneous service requirements on both communica-
tion rate and sensing accuracy [2]. In addition, the rapid
proliferation of wireless devices has exacerbated spectrum
congestion [3]. Fortunately, integrated sensing and commu-
nication (ISAC) offers an effective paradigm to address these
challenges concurrently by enabling both communication and
sensing functionalities to share the same spectrum and hard-
ware platform [4]. By integrating different functions, ISAC
brings signiﬁcant advantages over separate setups in terms
of hardware size, power consumption, spectral efﬁciency
and interference mitigation, establishing itself be an effective
enabler for 5G [5].
In practice, achieving the effective integration of ISAC
remains challenging owing to the inherent dichotomy between
communication and sensing functionalities [6]. Recently,
researchers have proposed various ISAC schemes on wave-
form sharing, interference mitigation and transceiver design
[7]. For instance, waveform sharing focuses on designing
dual-functional (DF) waveforms for dual services, which can
be categorized into radar-centric, communication-centric, and
joint-design approaches [8]. The ﬁrst two categories adopt the
same principle that integrates the secondary functionality with
the primary one without compromising its performance [9].
Speciﬁcally, the radar-centric category embeds the commu-
nication symbols into the radar waveform exploiting various
signaling strategies, while the communication-centric one
modiﬁes the high-ﬂexibility communication waveform for
enhanced target sensing. However, the radar-centric approach
suffers from the challenges of low achievable rate and the sens-
ing capabilities of the communication-centric approach may be
limited owing to the inherent randomness of the transmit signal
[10]. There is a deterministic-random dichotomy between
communication and sensing waveforms [11]. In contrast, the
joint-design category directly optimizes the DF waveform
from foundational principles rather than modifying existing
communication or radar waveforms, thus enjoying the great
advantages of higher design ﬂexibility [12]. For instance,
Liu et al. in [13] proposed a DF waveform design scheme
to minimize the weighted sum of multi-user interference
(MUI) power, waveform similarity and integrated sidelobe
level (ISL). In addition, in [14], Ding et al. minimized MUI
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

8682 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025
power, taking the transmit power and detection probability
constraints into account through DF waveform optimization.
Furthermore, Yang et al. in [15] developed a DF waveform
to minimize the MUI power while satisfying the constraints
of transmit power, peak average power ratio (PAPR), and
Cram´er-Rao bound (CRB) for angle estimation. In addition,
Wang et al. in [16] investigated joint waveform and phase-shift
optimization for the intelligent reﬂecting surface (IRS)-aided
ISAC networks, where the MUI power was minimized subject
to the constraints of constant modulus and CRB of angle
estimation.
Apart from DF waveform design, several studies have
focused on joint transmit waveform and receive ﬁltering,
i.e., transceiver design, for ISAC. For example, in [17], Wu
et al. investigated transceiver design for ISAC networks in
cluttered environments, and the sensing signal-to-interference-
plus-noise ratio (SINR) was maximized subject to the MUI
power and constant modulus signal constraints. Furthermore,
in [18], Tsinos et al. investigated the trade-off between
these two functionalities from a perspective of transceiver
design, and the weighted sum of MUI power and reciprocal
of sensing SINR was minimized. Moreover, Wen et al. in
[19] proposed an effective ISAC transceiver design scheme,
where the minimum sensing SINR was maximized subject
to constraints of communication SINR, per-antenna power
and PAPR. Besides, Chen et al. in [20] proposed a gen-
eralized transceiver beamforming scheme for ISAC and the
performance trade-off between sensing and communication
was explored. However, these ISAC schemes often involve
high complexity iterative algorithms for handling non-convex
design problems that hinder their practical implementation.
Thanks to its exceptional non-linear ﬁtting and general-
ization capabilities, deep learning (DL) has achieved great
success in computer vision and offers rapid inference speed
suitable for online deployment [21]. Leveraging these unique
capabilities, deep neural networks (DNNs) have emerged as
a low-complexity alternative to traditional optimization algo-
rithms by modeling the mapping from the problem formulation
to the solution space. This advocates a paradigm shift in ISAC
design from model-driven to data-driven approaches [22]. For
instance, Ye et al. in [23] proposed a low-complexity beam-
forming design scheme for IRS-aided ISAC networks, where a
DNN was trained in an unsupervised learning manner to mim-
ick the mapping from wireless channels to the corresponding
active and passive beamforming matrices. Also, in [24], Liu et
al. proposed a DL-based interference management scheme for
ISAC, where each base station (BS) employed a DNN to allo-
cate its transmit power and optimize beamforming. However,
these DNNs lack sufﬁcient interpretability and often involve
an enormous number of learnable parameters to enhance the
ﬁtting capabilities, increasing the risk of overﬁtting, especially
when training data is scarce.
By integrating domain knowledge with DL, deep unfolding
neural networks (NNs) are poised to overcome the afore-
mentioned drawbacks of traditional black-box NNs [25].
Speciﬁcally, it unfolds the underlying iterative algorithm to
an NN with less learnable parameters than its black-box
counterparts, with each layer of the NN corresponding to
approximately one iteration. In addition, the feedforward prop-
agation of deep unfolding NN is equivalent to performing ﬁnite
iterations. Consequently, the deep unfolding NN outperforms
its black-box counterpart in interpretability, reduced network
parameters and training samples, enabling its wide applications
in ISAC systems [26]. Furthermore, in [27], Nguyen et al.
investigated hybrid beamforming design for ISAC, where the
achievable rate was maximized subject to transmit power and
sensing constraints. In addition, a projected gradient ascent
(PGA)-based NN was developed to deal with the formu-
lated optimization problem, achieving a 33.5% achievable rate
improvement over the underlying PGA algorithm and reducing
the running time. Furthermore, Krishnananthalingam et al. in
[28] proposed a PGA-based deep unfolding NN for the DF
constant modulus design, obtaining comparable performance
with signiﬁcantly reduced computational complexity. In addi-
tion, Zhang et al. in [29] developed an alternating direction
method of multipliers (ADMM)-based deep unfolding NN
for the joint transmit waveform and phase-shift optimization
in reconﬁgurable intelligent surface (RIS)-aided ISAC, while
only involving equality constraints. Also, in [30], Jiang et
al. proposed a deep unfolding NN to conduct target sens-
ing and channel reconstruction simultaneously, obtaining a
comparable performance to the benchmarks with sustainable
lower complexity. Moreover, Zhao et al. in [31] minimized
the range-integrated sidelobe level (ISL) via optimizing the
constant modulus waveform and developed an effective deep
unfolding NN based on the Riemannian gradient descent
(RGD) algorithm to deal with it. Nevertheless, deep unfolding
NN is highly dependent on the underlying iterative algorithm,
which directly increases the difﬁculty of deep unfolding due
to the need of case-by-case investigation. Moreover, all the
aforementioned deep unfolding NNs are suitable for the opti-
mization problems with only equality constraints. The deep
unfolding NNs for a more general optimization problem with
both equality and inequality constraints have not been well
investigated. In general, the consideration of the inequality
constraints hinders the design of effective deep unfolding
owing to the complex operations involved in the underlying
iterative algorithm. Furthermore, it may be difﬁcult to ﬁnd
a projection operator to project the optimization variable to
the feasible region of an optimization problem with both
equality and inequality constraints, making the PGA algorithm
infeasible.
To the best of our knowledge, the deep unfolding NN
for a general ISAC transceiver design with both equality
and inequality constraints has not been well investigated,
motivating our work. The comparison between our work and
related publications is presented in Table I. Although [17]
and [18] also investigate the transceiver design for ISAC in
a cluttered environment, our work not only formulates a more
general ISAC transceiver design problem but also develops an
iterative algorithm and its corresponding unfolding NNs with
low computational complexity. Compared with the confer-
ence version [1], this article proposes another deep unfolding
neural network, termed ADMM-DL-NET, and develops a low-
complexity algorithm implementation approach, bypassing the
need for the transform from the complex-number operations
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

ZHANG et al.: DEEP UNFOLDING LEARNING AIDED ISAC TRANSCEIVER DESIGN 8683
TABLE I
COMPARISON BETWEEN THIS WORK AND THE RELATED PUBLICATIONS
to the real-number counterpart. Furthermore, more simulation
results are presented to verify the effectiveness of the propose
algorithms. Our contributions can be summarized as follows.
• This paper focuses on a general ISAC transceiver design
in a cluttered environment. Speciﬁcally, the weighted sum
of MUI power and the reciprocal of sensing SINR is
minimized subject to equality and inequality constraints.
Moreover, one iterative algorithm and its corresponding
deep unfolding NNs are proposed to address the investi-
gated optimization problem.
• We ﬁrst propose an ADMM-based iterative algorithm to
tackle the transceiver optimization problem. In particu-
lar, the fractional objective function is ﬁrst equivalently
transformed into a more tractable one by introducing
several slack variables. Then, to decouple the optimiza-
tion variables, the optimization problem is decomposed
into six subproblems to be optimized alternately and
the (semi) closed-form solution to each subproblem is
derived rather than resorting to the existing optimization
toolbox, enjoying the advantages of low computational
complexity.
• To further reduce computational complexity, we aim to
unfold the proposed iterative algorithm to a lightweight
NN with learnable parameters. Although the (semi)
closed-form solution to each subproblem can be obtained,
the intricate operations involved, such as the bisection
method, hinder the design of effective deep unfolding. To
deal with this issue, we transform the proposed ADMM-
based iterative algorithm into an unfolding-friendly one.
Speciﬁcally, the Uzawa’s method and projected gradient
descent (PGD) are leveraged to circumvent the bisection
method, resulting in the development of two deep unfold-
ing NNs, ADMM-DL-NET and ADMM-PGD-NET. The
step size and penalty coefﬁcients are treated as learn-
able parameters of NNs, which can be ﬁne-tuned in an
TABLE II
SUMMARY OF NOTATIONS
unsupervised learning manner, bypassing the need for
manual labels.
The remainder of this paper is organized as follows. The
system model and problem formulation are introduced in
Section II. Section III and IV present the proposed ADMM-
based iterative algorithm and two deep unfolding NNs for the
transceiver design of ISAC, respectively. Simulation results
are provided in Section V and this paper is concluded in
Section VI. Table II summarizes the notations through this
manuscript.
II. S YSTEM MODEL AND PROBLEM FORMULATION
The typical ISAC system is illustrated in Fig. 1, where
the ISAC-BS with Nt transmit antennas and Nr receive
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

8684 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025
Fig. 1. A typical ISAC network in cluttered environments.
antennas transmits a DF waveform to serve K (K > 1)
single-antenna users and detect a point target in the pres-
ence of clutters. Considering the half-duplex ISAC-BS, the
transmitting and receiving are in time-division approach. In
each pulse, the ISAC-BS transmitter ﬁrst transmits the dual-
functional waveform, and then the ISAC-BS receiver receives
the echo to detect the target. The channels from the ISAC-
BS to the k-th user and from the k-th user to the ISAC-BS
are given by ha,k∈ CNt×1 and ga,k∈ CNr×1, respectively,
k ∈ {1,··· ,K}. Assume that there are J (J > 1) signal-
dependent clutter points around the target of interest, and the
links of ISAC-BS-target, ISAC-BS-clutter- j, target-ISAC-BS
and clutter- j-ISAC-BS can be represented as ha,t∈ CNt×1,
ga,t ∈ CNr×1, ha,j ∈ CNt×1 and ga,j ∈ CNr×1, ∀j ∈
{1,··· ,J}, respectively. We consider transceiver design for
the ISAC network during a coherence time, which can be
evenly divided into L time slots.
A. Sensing Performance Metric
For ISAC-BS, the received baseband digital signal at the
range bin of the target in the 𝓁-th time slot can be formulated
as1
yr,𝓁 =αT ga,thHa,tx𝓁 +
J∑
j=1
αjga,jhHa,jx𝓁
+ nr,𝓁,∀𝓁∈{ 1,··· ,L}, (1)
where αT ∈ C1 and αj∈ C1 denote the complex reﬂection
coefﬁcients of the target and j-th clutter with E(|αT|2) =σ2T
and E(|αj|2) =σ2j ,∀j∈{ 1,··· ,J}. x𝓁∈ CNt×1 stands for
the DF waveform in the 𝓁-th time slot, nr,𝓁∼CN (0,σ 2r I)∈
CNt×1 denotes the additive white Gaussian noise (AWGN)
and σ2r refers to the noise power at each BS receive antenna.
Without loss of generality, the links between the ISAC-BS
and the target of interest and all clutter points are assumed as
line-of-sight (LoS) links [17]. Consequently, ha,t, ha,j, ga,t,
and ga,j are given by
ha,t =
[
1,··· ,eπ(Nt−1) sinϑt
]T
, (2a)
ha,j =
[
1,··· ,eπ(Nt−1) sinϑj
]T
,∀j∈{1,··· ,J}, (2b)
1Without loss of generality, we assume that the communication users and
the target of interest are located at different range bins, and the signal reﬂected
by the communication users are not taken into consideration.
ga,t =
[
1,··· ,eπ(Nr−1) sinϑt
]T
, (2c)
ga,j =
[
1,··· ,eπ(Nr−1) sinϑj
]T
,∀j∈{1,··· ,J}, (2d)
respectively, where ϑt and ϑj denote the angle-of-arrival
(AoA) of the target and the j-th clutter point, respectively,
∀j∈{ 1,··· ,J}.
Let ˜yr ≜ [yTr,1,··· , yTr,L]T ∈ CLNt×1, then the total
received signals at the ISAC-BS during the L time slots can
be represented as
˜yr =αT Aa,t˜x +
J∑
j=1
αjAa,j ˜x + ˜nr, (3)
where ˜x = [ xT1,··· , xTL]T ∈ CLNt×1, ˜nr =
[nTr,1,··· , nTr,L]T ∈ CLNt×1, Aa,t = IL⊗ (ga,thHa,t), and
Aa,j = IL⊗ (ga,jhHa,j),∀j∈{ 1,··· ,J}.
Applying receive ﬁltering, we have
wH ˜yr =αT wH Aa,t˜x +
J∑
j=1
αjwH Aa,j ˜x + wH ˜nr, (4)
where w∈ CLNt×1 denotes the receive ﬁltering coefﬁcients
vector. Consequently, the sensing SINR at the ISAC-BS is
given by
SINRr = σ2T|wH Aa,t˜x|2
wH
(∑J
j=1σ2j Aa,j ˜x˜xH AHa,j +σ2r I) w (5a)
= |wH ˜Aa,t˜x|2
wH
(∑J
j=1 ˜Aa,j ˜x˜xH ˜AHa,j +σ2r I) w, (5b)
where ˜Aa,t =σT Aa,t and ˜Aa,j =σjAa,j,∀j∈{ 1,··· ,J}.
According to [17], the target detection probability Pd can
be written as
Pd = 12 erfc(erfc−1(2Pfa)−√SINRr), (6)
where erfc (x) = 2√π∫∞x e−t2dt is the complementary error
function and Pfa is the probability of false alarm. Pd is a
very complicated function w.r.t. SINR r, making it difﬁcult
to handle. Fortunately, Pd is monotonically increasing w.r.t.
SINRr for the given false alarm probability. 2 Therefore, Pd
can be maximized via maximizing SINR r, which is adopted
as the sensing performance metric in this paper.
In addition, the sensing waveform is expected to exhibit
some critical properties, including strong autocorrelation and
a high peak-to-sidelobe ratio [9]. Nevertheless, it is difﬁcult to
obtain a DF waveform with desirable sensing properties via
direct optimization. As a remedy, existing radar waveforms
can be leveraged as a reference and the waveform similarity
is also taken into consideration, which can be formulated as
‖˜x− ˜x0‖22, (7)
where ˜x0 = vec( ˜X0) denotes the reference sensing waveform.
2Note that the relationship between Pd and SINRr is non-linear, and
the marginal gain from increasing SINR r can vary signiﬁcantly in different
regimes.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

ZHANG et al.: DEEP UNFOLDING LEARNING AIDED ISAC TRANSCEIVER DESIGN 8685
Considering the sensing waveform should have high auto-
correlation in time domain and high directivity in spatial
domain, we design a reference sensing waveform matrix by
precoding the linear frequency modulation waveform as ˜X0 =
ha,txH, where ha,t denotes the precoding vector towards
the target of interest and x represents the linear frequency
modulation waveform as
x(𝓁) =e
2π
(
fc
fs𝓁+ ϱf 2s𝓁2
)
,𝓁∈{ 1,··· ,L}. (8)
B. Communication Performance Metric
The received signal at the K users in the 𝓁-th time slot can
be formulated as
yc,𝓁 = Hcx𝓁 + nc,𝓁,∀𝓁∈{ 1,··· ,L}, (9)
where Hc = [ h∗a,1,··· , h∗a,K]T ∈ CK×Nt refers to the
equivalent channel matrix from the ISAC-BS to the users in
the 𝓁-th time slot, nc,𝓁 ∼ CN(0,σ 2c I), and σ2c denotes the
noise power at each communication user.
Let s𝓁∈ CK×1 refer to the desired communication symbol
vector at the users in the 𝓁-th time slot, then (9) can be
rewritten as
yc,𝓁 = s𝓁 + (Hcx𝓁− s𝓁)| {z }
MUI
+nc,𝓁,∀𝓁∈{ 1,··· ,L}, (10)
where the term (Hc,𝓁x𝓁− s𝓁) denotes the MUI.
According to [13], the sum achievable rate R can be
formulated as
R =
K∑
k=1
log2(1 +γk), (11)
where
γk = E(|s𝓁(k)|2)
E
(⏐⏐hHa,kx𝓁− s𝓁(k)⏐⏐2)| {z }
MUI power
+σ2c
,∀k∈{ 1,··· ,K}, (12)
refers to the communication SINR at the k-th user,
E
(
|hHa,kx𝓁− s𝓁(k)|2) stands for the MUI power, and E(·)
denotes the mathematical expectation. Therefore, for the
desired communication symbol vector with a ﬁxed power,
the sum achievable rate can be maximized via minimizing
the MUI power.
Let ˜yc = [ yTc,1,··· , yTc,L]T ∈ CLK×1, then (10) can be
reformulated as
˜yc = s + ( ˜Hc˜x− s)| {z }
MUI
+˜nc, (13)
where ˜Hc = IL⊗ Hc, ˜nc = [ nTc,1, ··· , nTc,L]T ∈ CLK×1,
s = [ sT1,··· , sTL]T ∈ CLK×1, and ( ˜Hc˜x− s) refers to the
MUI during the L time slots.
C. Problem F ormulation
To achieve a performance trade-off between communication
and sensing, the weighted sum of MUI power and the recip-
rocal of sensing SINR is minimized via jointly optimizing the
transmit waveform and receive ﬁltering, yielding the following
optimization problem 3
min
˜x,w
ρ‖ ˜Hc˜x− s‖22 + (1−ρ) 1SINRr (14a)
s.t. ‖˜x− ˜x0‖22≤γ, (14b)
|˜x(i)| = 1,∀i∈{ 1,··· ,LNt}, (14c)
where ρ∈ [0, 1] stands for the weighting coefﬁcient, γ≥ 0
refers to the similarity threshold, and ˜x0 denotes the reference
waveform. Equations (14b) and (14c) represent the constraints
of waveform similarity and constant modulus, 4 respectively.
Nevertheless, (14) is non-convex owing to the non-convex
constraint and objective function. Moreover, the complicated
fractional objective function poses a huge challenge to han-
dling it.
Fortunately, (14) can be equivalently transformed into
min
˜x,w
ρ‖ ˜Hc˜x− s‖22
+ (1−ρ)wH


J∑
j=1
˜Aa,j ˜x˜xH ˜AHa,j +σ2nI

 w (15a)
s.t. |wH ˜Aa,t˜x|2 = 1, (15b)
(14b), (14c), (15c)
where the objective function is transformed into a more
tractable one. Nevertheless, (15) is still non-convex because
of the coupled variables and non-convex constraints. It can be
seen that the semi-deﬁnite relaxation [33] is not suitable to
address (15) because the objective is not a quadratic form
w.r.t. ˜x. Moreover, the feasible region does not belong to
a manifold, hindering the adoption of manifold optimization
[34]. Thanks to the minimization and constant modulus con-
straint, the direction method of multipliers (ADMM) can be
leveraged to address (15). Consequently, we ﬁrst design an
ADMM-based iterative algorithm to address this challenge in
Section III. Afterwards, two model-driven NNs with lower
computational complexity and comparable performance are
proposed to facilitate the online deployment in Section IV.
III. ADMM-B ASED ITERATIVE ALGORITHM
In this section, we propose an ADMM-based iterative
algorithm to handle (15). In particular, the original problem
is ﬁrst transformed to an equivalent and more tractable one
by introducing some auxiliary variables and then decomposed
into six subproblems to be optimized alternately. Moreover, the
(semi) closed-form solution to each subproblem is derived.
A. Problem Transformation
Via introducing the auxiliary variables θ∈ [0, 2π] and y∈
CNtL×1, (15) can be rewritten as
min
˜x,w,θ,y
ρ‖ ˜Hc˜x− s‖22
3According to the simulation parameters in Section V, the magnitude of
MUI energy is close to that of the reciprocal of sensing SINR, bypassing the
need for normalization. Otherwise, the normalization operation is necessary
to balance two functionalities.
4The constant modulus constraint can guarantee that the ISAC-BS ampliﬁer
often works in a saturation condition, avoiding the waveform distortion [32].
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

8686 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025
+ (1−ρ)wH


J∑
j=1
˜Aa,j ˜x˜xH ˜AHa,j +σ2nI

 w (16a)
s.t. wH ˜Aa,t˜x =eθ, (16b)
˜x =ey, (16c)
(14b), (16d)
whose Lagrangian function can be formulated as (17), as
shown at the bottom of the page,where µ > 0 and µ1 > 0
denote the penalty coefﬁcients, and v∈ C1 and z∈ CNtL×1
refer to the slack variables.
Therefore, the Lagrangian problem of (16) can be formu-
lated as
min
˜x,w,θ,y,v,z
Lµ(˜x, w,θ, y,v, z) (18a)
s.t. (14b). (18b)
The ADMM-based iterative algorithm alternately optimizes
˜x, w, θ, y, v and z, adopting the following iterative steps
˜xn+1 = arg min
˜x
Lµ(˜x, wn,θn, yn,vn, zn), (19a)
s.t. (14b),
wn+1 = arg min
w
Lµ(˜xn+1, w,θn, yn,vn, zn), (19b)
θn+1 =∠(|wn+1,H ˜Aa,t˜xn+1 +vn), (19c)
yn+1 =∠(|˜xn+1 + zn), (19d)
vn+1 =vn + wn+1,H ˜Aa,t˜xn+1−eθn+1, (19e)
zn+1 = zn + ˜xn+1−eyn+1, (19f)
where n refers to the iteration index of the proposed approach.
B. Waveform Optimization
With the given wn,θn, yn,vn, and zn, (19a) can be reduced
into
min
˜x
Lµ(˜x, wn,θn, yn,vn, zn) (20a)
s.t. (14b), (20b)
which is convex. Although existing optimization toolboxes,
such as CVX, can be utilized to deal with (20), they suffer
from the challenges of high computational complexity [35].
In the following, we derive a semi closed-form solution to it
using the Karush-Kuhn-Tucker (KKT) conditions.
The Lagrangian function of (20) is given by
˜Lx(˜x,λ ) =ρ‖ ˜Hc˜x− s‖22 (21a)
+ (1−ρ)wH


J∑
j=1
˜Aa,j ˜x˜xH ˜AHa,j +σ2nI

 w
(21b)
+ µ2(|wn,H ˜Aa,t˜x−eθn +vn|2−|vn|2) (21c)
+ µ1
2
(
‖˜x−eyn + zn‖22−‖ zn‖22) (21d)
+λ(‖˜x− ˜x0‖22−γ), (21e)
where λ≥ 0 refers to the Lagrangian multiplier.
The Lagrangian problem can be written as
min
˜x
˜Lx(˜x,λ ) (22a)
s.t. (14b). (22b)
The Hessian matrix of (21) can be formulated as
∇2 ˜Lx(˜x,λ )
∇˜x2 = 2ρ ˜HHc ˜Hc + 2(1−ρ)
J∑
j=1
˜AHa,jwnwn,H ˜Aa,j
+µ ˜AHa,twnwn,H ˜Aa,t + (µ1 + 2λ)I, (23)
which is positive-deﬁnite, and thus ˜Lx(˜x,λ ) is a convex func-
tion w.r.t. ˜x. Considering the constraint (14b) is a convex set,
the problem (22) is convex. According to the KKT conditions,
the optimal solution ˜xn+1 should satisfy (24), as shown at
the bottom of the page. By solving (24) a semi closed-form
solution of ˜xn+1 is given by (25), as shown at the bottom of
Lµ(˜x, w,θ, y,v, z) =ρ‖ ˜Hc˜x− s‖22 + (1−ρ)wH


J∑
j=1
˜Aa,j ˜x˜xH ˜AHa,j +σ2nI

 w + µ2(|wH ˜Aa,t˜x−eθ +v|2−|v|2)
+ µ1
2
(
‖˜x−ey + z‖22−‖ z‖22). (17)
∂ ˜Lx(˜x,λ )
∂˜x = 2ρ ˜HHc ( ˜Hc˜x− s) + 2(1−ρ)
J∑
j=1
˜AHa,jwnwn,H ˜Aa,j ˜x +µ ˜AHa,twn(wn,H ˜Aa,t˜x−eθn +vn)
+µ1(˜x−eyn + zn) + 2λ(˜x− ˜x0) = 0. (24)
˜xn+1(λ) =

2ρ ˜HHc ˜Hc+2(1−ρ)
J∑
j=1
˜AHa,jwnwn,H ˜Aa,j +µ ˜AHa,twnwn,H ˜Aa,t+(µ1+2λ)I


†
(
2ρ ˜HHc s+µ ˜AHa,twn(eθn−vn)
+µ1(eyn− zn) + 2λ˜x0). (25)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

ZHANG et al.: DEEP UNFOLDING LEARNING AIDED ISAC TRANSCEIVER DESIGN 8687
Algorithm 1 The Heuristic Method for the Choice of Left and
Right End Points
1: Initialize the left end point λmin = 0, right end point λ1
and factor c> 1.
2: while‖˜xn+1(λ1)− ˜x0‖22≥γ do
3: λ1 =cλ1.
4: end while
5: Output: left end point λmin and right end point λ1.
the previous page. In addition, λ should be chosen to make
˜xn+1(λ) satisfy the complementary slackness condition for
(14b) as
λ(‖˜xn+1(λ)− ˜x0‖22−γ) = 0. (26)
If‖˜xn+1(0)− ˜x0‖22≤ γ, ˜xn+1(0) is the optimal solution
to (18). Otherwise, the optimal waveform vector ˜x(λ) should
satisfy
‖˜xn+1(λ)− ˜x0‖22 =γ, (27)
which is a monotonically decreasing function w.r.t. λ, proved
in Lemma 1.
Lemma 1: The function F (λ) ≜ ‖˜xn+1(λ)− ˜x0‖22 is a
monotonically decreasing function w.r.t. λ.
Proof: The Lagrangian dual function of (21) can be given
by
g(λ) = inf
˜x
Lx(˜x,λ ), (28)
and the dual problem is formulated as
max
λ>0
g(λ). (29)
Assume that the two variables λ andλ′ satisfyλ>λ ′, and
˜x(λ) and ˜x(λ′) are the optimal solutions to (28) with λ and
λ′, respectively. We have
Lx(˜x(λ),λ )≤L x(˜x(λ′),λ ), (30a)
Lx(˜x(λ′),λ′)≤L x(˜x(λ),λ′). (30b)
According to (30), we have (λ−λ′)F (λ)≤ (λ−λ′)F (λ′).
Moreover, F (λ) ≥ F (λ′) holds because λ > λ′. Conse-
quently, the proof is completed.■
Therefore, the optimal λ can be obtained via the bisection
method, and the choice of left and right end points is very
important to it. We propose a heuristic method to chose the
left and right points in Algorithm 1.
C. Receive Filtering Optimization
With the given ˜xn+1, θn, yn, vn and zn, (19b) can be
equivalently written as
min
w
(1−ρ)wH


J∑
j=1
˜Aa,j ˜xn+1˜xn+1,H ˜AHa,j +σ2nI

 w
+ µ2⏐⏐⏐wH ˜Aa,t˜xn+1−eθn +vn⏐⏐⏐2, (31)
which is an unconstrained optimization problem. According to
the ﬁrst-order optimality condition (FOOC), the closed-form
solution of wn+1 is given by
wn+1 =−µcn,∗(2Bn +µbbH)−1 b, (32)
Algorithm 2 ADMM-Based Iterative Algorithm for (16)
1: Initialization: Set an initial point (˜x0, w0,θ 0, y0,v 0, z0),
the index of iteration n = 0 and convergence accuracy
ϵ> 0.
2: repeat
3: With given (˜xn, wn,θn, yn,vn, zn), obtain ˜xn+1 from
(25).
4: With given (˜xn+1, wn,θn, yn,vn, zn), obtain wn+1
from (32).
5: With given (˜xn+1, wn+1,θn, yn,vn, zn), obtain θn+1
from (19c).
6: With given (˜xn+1, wn+1,θn+1, yn,vn, zn), obtain
yn+1 from (19d).
7: With given (˜xn+1, wn+1,θn+1, yn+1,vn, zn), obtain
vn+1 from (19e).
8: With given (˜xn+1, wn+1,θn+1, yn+1,vn+1, zn),
obtain zn+1 from (19f).
9: n =n + 1.
10: until
⏐⏐Lµ(˜xn+1, wn+1,θn+1, yn+1,vn+1, zn+1) −
Lµ(˜xn, wn,θn, yn,vn, zn)⏐⏐≤ϵ.
11: Output: (˜xn+1, wn+1,θn+1, yn+1,vn+1, zn+1).
where Bn = (1−ρ)(∑Jj=1 ˜Aa,j ˜xn+1˜xn+1,H ˜AHa,j +σ2nI),
b = ˜Aa,t˜xn+1, andcn =−eθn +vn. Moreover, wn+1 can be
regarded as the whitening operation followed by the matched
ﬁlter.
D. Algorithm Analysis
The proposed ADMM-based iterative algorithm for (16) is
presented in Algorithm 2, which divides the original problem
into six subproblems to be optimized alternately. Furthermore,
the (semi) closed-form solution to each subproblem is derived.
It can be observed that the complexity of Algorithm 2 is
mainly determined by the waveform optimization and receive
ﬁltering optimization subproblems. Speciﬁcally, the approxi-
mate computational complexity of optimizing ˜x and w in each
iteration are given byO(I1L3N3t ) andO(L3N3t ), respectively,
where I1 refers to the number of iterations of the bisection
method.
According to [36], the ADMM-based iterative algorithm
illustrates the satisfactory convergence performance, which
will be veriﬁed via simulation results.
E. Robust Transceiver Design
In this subsection, we extend the proposed scheme to the
case of imperfect clutter angle. Assume the angle of clutter
lies in an angular region Θ, which is evenly discretized into
˜J angles as {ϑ1,··· ,ϑ ˜J} according to the angle resolution.
The worst-case sensing SINR can be formulated as
SINRr = |wH ˜Aa,t˜x|2
wH
(∑ ˜J
j=1 ˜Aa,j ˜x˜xH ˜AHa,j +σ2r I) w, (33)
where Aa,j = IL⊗ (ga,jhHa,j), ˜Aa,j = σjAa,j, ∀j ∈
{1,··· , ˜J}.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

8688 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025
Under the case of imperfect clutter angle, the communica-
tion and sensing trade-off can also be written as (14), which
can be tackled by the proposed scheme and the details are
omitted for brevity.
IV. D EEP UNFOLDING NEURAL NETWORK
Although the proposed ADMM-based iterative algorithm
can handle (16), it faces the challenges of high computational
complexity owing to the iteration and the bisection. Moreover,
the involved complicated operations, such as the bisection
method, hinder the design of effective deep unfolding. In
this section, we modify the proposed ADMM-based iterative
algorithm to make it a unfolding-friendly one and develop two
deep unfolding NNs, named ADMM-DL-NET and ADMM-
PGD-NET, which circumvent the bisection method exploiting
the Uzawa’s method and PGD, respectively. Moreover, the
comparison between the proposed deep unfolding NNs and
their underlying iterative algorithm is presented.
A. ADMM-DL-NET
Although a semi closed-form solution to (20) can be
derived, it is difﬁcult to obtain an unfolding network owing to
the involved bisection method. Since (20) is convex and the
strong duality condition holds, the dual method can be utilized
to tackle it [37]. In particular, the Lagrangian dual function of
(20) is given by
g(ν) = inf
˜x
L(˜x,ν ), (34)
where ν > 0 refers to the dual variable and L(˜x,ν ) is the
Lagrangian function of (20), i.e.,
L(˜x,ν )=Lµ(˜x, wn,θn, yn,vn, zn)+ν(‖˜x−˜x0‖22−γ). (35)
Furthermore, the dual problem is formulated as
max
ν>0
g(ν), (36)
which can be solved via the projection-gradient method
because of its convexity. Therefore, we adopt Uzawa’s method,
which is a gradient-based algorithm with the constant step
size, to obtain the solutions to both primary and dual problems
[37]. More speciﬁcally, to update ˜x andν alternately, Uzawa’s
method follows the iterative steps as
primary update: ˜xm =arg min˜x L(˜x,νm), (37a)
dual update:νm+1 =max(νm +α(‖˜xm− ˜x0‖22−γ), 0),
(37b)
where α> 0 denotes the step-size for the dual update and m
represents the index of iterations. Similar to (32), the closed-
form solution to (37a) can be obtained via the FOOC, which
can be formulated as (38), as shown at the bottom of the page.
Fig. 2. Architecture of the DL-NET.
The step size α plays an important role in the performance
of the Uzawa’s method, which should be carefully chosen
[37]. Nevertheless, it may be difﬁcult to obtain a proper α. To
overcome this issue, the step size α is regarded as a learnable
parameter, which is determined in a data-driven manner rather
than set manually. To further enhance the performance, α
varies with the iterations, and αm > 0 stands for the step
size in the m-th iteration of Uzawa’s method. The number of
iterations of Uzawa’s method is M and all learnable parameters
are formulated as
A ={α1,··· ,αM}. (39)
Consequently, the Uzawa’s method can be unfolded into a M-
layer NN with the learnable parameter setA, i.e., the DL-NET,
whose architecture is illustrated in Fig 2.
Leveraging the DL-NET, the proposed Algorithm 2 can be
unfolded to an NN effectively, which is termed as ADMM-DL-
NET. As illustrated in Fig. 3, the ADMM-DL-NET consists
of Q > 1 layers, with each layer made up of six units,
i.e., ˆx, ˆw, ˆθ, ˆy, ˆv, and ˆz. In addition, ˆx leverages the DL-
NET to deal with the waveform optimization subproblem. The
formulations involved in ˆw, ˆθ, ˆy, ˆv, and ˆz are presented in (32),
(19c), (19d), (19e), and (19f), respectively. Since the penalty
coefﬁcients are essential to the performance of the algorithm,
they are also treated as learnable parameters and vary with
layers. Therefore, all learnable parameters of the ADMM-DL-
NET are included in the set Θ ={Aq}Qq=1∪{µq,µ 1,q}Q−1q=1 ,
whereAq refers to the learnable parameters contained in the
q-th DL-NET, and µq and µ1,q stand for the penalty coefﬁ-
cients in the q-th layer of ADMM-DL-NET. Consequently,
the ADMM-DL-NET follows the basic framework of the
proposed ADMM-based iterative algorithm and ﬁne-tunes the
hyperparameters (step size and plenty coefﬁcients) in a data-
driven manner.
˜xm =

2ρ ˜HHc ˜Hc + 2(1−ρ)
J∑
j=1
˜AHa,jwnwn,H ˜Aa,j +µ ˜AHa,twnwn,H ˜Aa,t + (µ1 + 2νm)I


†
(
2ρ ˜HHc s +µ ˜AHa,twn(eθn−vn) +µ1(eyn− zn) + 2νm˜x0). (38)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

ZHANG et al.: DEEP UNFOLDING LEARNING AIDED ISAC TRANSCEIVER DESIGN 8689
Fig. 3. Architecture of the ADMM-DL-NET.
The non-convexity of (16) makes it difﬁcult to obtain the
globally optimal solution, hindering the application of the
supervised learning method. As a remedy, the unsupervised
learning is utilized to train the ADMM-DL-NET and (17) acts
as the loss function. In addition, the learnable parameters are
updated via the following gradient descent method
Θ← Θ−η∇ΘLµ(˜xQ, wQ,θQ, yQ,vQ, zQ), (40)
where η > 0 refers to the learnable rate and
(˜xQ, wQ,θQ, yQ,vQ, zQ) stands for the output of the
ADMM-DL-NET. The physical meaning of (40) is to update
the learnable parameters along the direction of negative
gradient to decrease the loss.
Algorithm 3 Training Procedure of the ADMM-DL-NET
1: Input: Data set G =
{{
h(i)a,k
}
, h(i)a,t,{h(i)a,j}, S(i)}|G|i=1
with|G| samples, preset the hyperparameters and initial
point.
2: Initialize ADMM-DL-NET parameter Θ(0,0).
3: foro = 1 toF do
4: Randomly splitG intoB batches with⌊|G|B⌋ samples.
5: forb = 1 toB do
6: Lavg = 0.
7: fori = 1 to⌊|G|B⌋ do
8: Feed the i-th sample{{
h(i)a,k
}
, h(i)a,t,{h(i)a,j}, S(i)} into the
ADMM-DL-NET, obtaining the output{˜x(i), w(i),θ (i), y(i),v (i), z(i)}.
9: Calculate the loss
˜Lµ(˜x(i), w(i),θ (i), y(i),v (i), z(i)) from (17).
10: Lavg =Lavg+ ˜Lµ(˜x(i), w(i),θ (i), y(i),v (i), z(i)).
11: end for
12: Optimize the network parameter Θ(o,b) via (40).
13: end for
14: end for
15: Output: Optimized parameter Θ(F,B).
The detailed training procedure of the ADMM-DL-NET is
presented in Algorithm 3. In particular, a data set G with
|G| training samples is utilized for training the ADMM-DL-
NET. The hyperparameters and initial point are ﬁrst given, and
then the ADMM-DL-NET is trained over F > 1 episodes.
In each episode, a ﬁxed number of training samples are fed
into the ADMM-DL-NET to obtain the corresponding output,
and then the loss is calculated according to (17). Finally, the
ADMM-DL-NET updates its learnable parameters from (40)
to minimize the loss. Through multiple episodes of training,
the learnable parameters (hyperparameters of the iterative
algorithm) can be ﬁne-tuned.
B. ADMM-PGD-NET
Apart from the dual method, the PGD algorithm can be also
utilized to handle (20). Different from the Uzawa’s method
that solves (20) via handling its dual problem, PGD deals
with (20) directly. Speciﬁcally, in each iteration of PGD, the
optimization variable is ﬁrst updated via the gradient descent
method, and then projected on the feasible set. For instance,
the m-th iteration of the PGD algorithm for solving (20) is
formulated as
˜xm+1 = ˜xm−βm∇˜xmLµ(˜xm, wn,θn, yn,vn, zn), (41a)
˜xm+1 = ΠΩ(˜xm+1), (41b)
whereβm (βm > 0) denotes the step-size in the m-th iteration
of the PGD algorithm and ΠΩ(˜xm+1) stands for the orthogo-
nal projection of ˜xm+1 on the feasible set Ω ={˜x|‖˜x−˜x0‖22≤
γ}.∇˜xmLµ(˜xm, wn,θn, yn,vn, zn) denotes the gradient of
Lµ(˜xm, wn,θn, yn,vn, zn) w.r.t. ˜xm, which is formulated as
∇˜xmLµ(˜xm, wn,θn, yn,vn, zn)
= 2ρ ˜HHc ( ˜Hc˜xm− s)
+2(1−ρ)
J∑
j=1
˜AHa,jwnwn,H ˜Aa,j ˜xm+µ1(˜xm−eyn +zn)
+µ ˜AHa,twn(wn,H ˜Aa,t˜xm−eθn +vn). (42)
It can be observed that the feasible set Ω is a ball centered
on ˜x0 with radius√γ. Therefore, ΠΩ(˜xm+1) is given by [38]
ΠΩ(˜xm+1) = ˜x0 +
√γ× (˜xm+1− ˜x0)
max(‖˜xm+1− ˜x0‖2,√γ). (43)
The PGD algorithm bypasses the need for adopting bisec-
tion search, making it suitable for an effective deep unfolding.
Moreover, the step-size in each iteration can be viewed as
the learnable parameters to enhance the performance. Conse-
quently, we can develop another NN to solve (20), termed
PGD-NET, whose architecture is illustrated in Fig. 4 and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

8690 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025
Fig. 4. Architecture of the PGD-NET.
βm > 0 refers to the learnable parameter in the m-th itera-
tion. The forward propagation of PGD-NET is equivalent to
conducting M iterations of the PGD algorithm. Based on the
PGD-NET, Algorithm 2 can be unfolded to another NN, which
is referred to ADMM-PGD-NET. The framework of ADMM-
PGD-NET is similar to that of ADMM-DL-NET except that
the network in the unit ˆx, and the details are omitted for
brevity. The loss function and training procedure of ADMM-
PGD-NET are the same as those of the ADMM-DL-NET.
C. Computational Complexity and Parameter Analysis
The approximate computational complexity of both
ADMM-DL-NET and ADMM-PGD-NET are O(Q(M +
1)N3tL3). Compared with the underlying ADMM-based iter-
ative algorithm, our proposed two deep unfolding NNs can
reduce the number of iterations and thus enjoy the advantage
of low complexity, which is also veriﬁed by simulation results.
Furthermore, the number of learnable parameters within both
ADMM-DL-NET and ADMM-PGD-NET is 2(Q− 1) +QM.
D. Comparison Between the Deep Unfolding NNs With the
Underlying Iterative Algorithm
In this subsection, we compare the proposed deep unfolding
NNs with the underlying iterative algorithm across several
aspects.
• Architecture: The architectures of our proposed deep
unfolding NNs are very similar to that of the ADMM-
based iterative algorithm except for the waveform
update. Speciﬁcally, the ADMM-based iterative algorithm
derives the semi closed-form solution to the waveform
optimization subproblem and the optimal Lagrangian
Multiplier is obtained via the bisection method. In con-
trast, our proposed deep unfolding NNs resort to the
unfolding-friendly dual methods to handle the waveform
optimization subproblem.
• Complexity: The proposed ADMM-DL-NET and
ADMM-PGD-NET unfold the underlying iterative
algorithm to a shallow and lightweight NN, reducing the
computational complexity signiﬁcantly.
• Parameters: There are few parameters in the proposed
ADMM-based iterative algorithm, and these parameters
Fig. 5. Convergence curve of the ADMM-based iterative algorithm versus
the number of time slots, with ρ = 0.3.
are set manually. On the contrary, our proposed deep
unfolding NNs contain more parameters, which are deter-
mined in a data-driven manner rather than being set
manually.
• Interpretability: The proposed deep unfolding NNs fol-
low a similar procedure to our proposed ADMM-based
iterative algorithm and treat the step size and penalty
coefﬁcients as the learnable parameters, which can be
ﬁne-tuned via training. Each layer of ADMM-DL-NET
and ADMM-PGD-NET is equivalent to one iteration
and thus the feed forward propagation conducts a ﬁxed
number of iterations. Consequently, our proposed deep
unfolding NNs are superior to the traditional black-box
NN in interpretability and number of learnable parame-
ters.
V. S IMULATION RESULTS
In this section, simulation results are presented to demon-
strate the effectiveness of our proposed deep unfolding NNs.
If not speciﬁed, we set Nt = 6, L = 10, ϑt = 0◦, K = 2,
J = 2 , µ = 5 , µ1 = 0.1, γ = 5 , σ2T = 2 dB, fc = 5 Hz,
ϱ = 0.1, σ2n = 0 dB and ϵ = 10−4. The AoAs of the clutter
points are −7◦ and 7◦, respectively, and σ21 = σ22 = 20 dB
[17]. All communication channels follow the Gaussian distri-
bution with pathloss 5×10−3, and the desired communication
symbols follow the binary phase shift keying modulation with
Ps = 10−2 W. The hyperparameters of the ADMM-DL-NET
and ADMM-PGD-NET are listed in Table III. The results in
Fig. 6 and Fig. 10 –12 are obtained by averaging over 1000
independent Monte Carlo simulations while other results aim
at a speciﬁc simulation. All experiments are conducted on one
Intel CPU I9-12900KF with 64GB RAM, and the proposed
NNs are implemented in Python 3.9.5 with Pytorch 2.0.0. 5
We consider the following four benchmarks for performance
comparison.
5Note that Pytorch 2.0.0 can support the complex tensors, bypassing the
transform from complex-number operations to the real-number counterpart.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

ZHANG et al.: DEEP UNFOLDING LEARNING AIDED ISAC TRANSCEIVER DESIGN 8691
Fig. 6. Achievable rate of different iterative algorithms versus γ, with ρ =
0.3.
Fig. 7. Beampattern comparison among all algorithms, with ρ = 0.3.
TABLE III
HYPERPARAMETERS OF THE ADMM-DL-NET AND ADMM-PGD-NET
• ADMM: The developed ADMM-based algorithm.
• ADMM-PGD: The combination of ADMM and PGD
algorithms, where the PGD is utilized to deal with the
waveform optimization subproblem. Moreover, the step-
size is obtained by the Armijo rule.
• ADMM-DL: The combination of ADMM and Uzawa’s
method, where the bisection method of Algorithm 2 is
replaced by the Uzawa’s method.
Fig. 8. Convergence curves of the proposed NNs versus the learning rate,
with ρ = 0.3. (a) ADMM-PGD-NET, (b) ADMM-DL-NET.
Fig. 9. Convergence curves of the proposed NNs versus ρ, withη = 0.0005.
• USL: The feed-forward neural network (FNN) with
Q hidden layers and 500 neurons per hidden layer.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

8692 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025
Fig. 10. Achievable rate of the proposed NNs and benchmarks versus the
communication SNR, with ρ = 0.3.
Fig. 11. Sensing SNR versus L for the proposed NNs and benchmarks, with
ρ = 0.3.
Consequently, the number of learnable parameters of
FNN is 500×Q, which is much larger than those of the
proposed NNs. The FNN is trained in an unsupervised
learning manner, and the loss function is formulated as
Lusl =ρ‖ ˜Hc˜x− s‖22 + (1−ρ)SINRr +ζ[‖˜x− ˜x0‖22−γ]+,
(44)
where ζ = 2 refers to the penalty coefﬁcient, [x]+ ≜
max(x, 0) and ζ[‖˜x− ˜x0‖22−γ]+ can be regraded as
the penalty term for violating the similarity constraint.
The input of FNN is the collection of the communication
links, sensing links, reference radar waveform and desired
communication symbols. Furthermore, the output of FNN
is made up of the waveform vector and receive ﬁltering
coefﬁcient, and the waveform vector is normalized to
satisfy the constant modulus constraint.
Fig. 5 illustrates the convergence curve of the ADMM-
based iterative algorithm versus the number of time slots,
Fig. 12. The generalization of proposed algorithms under different channel
realizations, with ρ = 0.3.
with ρ = 0 .3. We can see that the proposed ADMM-
based iterative algorithm converges about 10 iterations, and
its convergence speed remains almost unchanged with L.
Consequently, the satisfactory convergence performance of the
proposed ADMM-based iterative algorithm is veriﬁed.
Fig. 6 depicts the achievable rate of different iterative
algorithms versus γ, with ρ = 0.3. For each algorithm, the
achievable rate increases withγ because a largeγ expands the
feasible region of optimization problem. Furthermore, ADMM
is superior to both ADMM-PGD and ADMM-DL, and the
performance gaps increase with γ, verifying the effectiveness
of ADMM algorithm.
The beampattern corresponding to the transmit waveform
and receive ﬁltering towards the angle ϑ can be written as
[17]
P (ϑ) =|wH ˜A(ϑ)˜x|2,∀ϑ∈[−π2,π2], (45)
where ˜A(ϑ) ≜ IL⊗ (a(ϑ,Nr)aH(ϑ,Nt)) and a(ϑ,N ) ≜[1,eπ sinϑ,··· , eπ(N−1) sinϑ]T stand for the corresponding
response matrix and steering vector, repsectively. Fig. 7 com-
pares the beampatterns of all algorithms, with ρ = 0.3. It can
be seen that the beampattern of ADMM forms a high gain
towards the direction of the target and two deep nulls towards
the cluttering directions, thus achieving the satisfactory clutter
suppression performance and high sensing SINR. In addition,
the beampatterns of the proposed two NNs are closer to that
of the ADMM than the USL, verifying the effectiveness of
our proposed NNs.
Table IV compares the CPU running time of the algo-
rithms versus the number of time slots, with (F,γ,|G|) =
(10, 5, 100). From the results, both the CPU training and
testing time of deep unfolding NNs increase with L, while
the running time of USL remains almost unchanged with L
because the dimensions of its hidden layers, which determine
the computational complexity, are independent with L. In
addition, both the CPU training and testing time of ADMM-
DL-NET are larger than those of ADMM-PDG-NET owing to
the more complicated operations. Furthermore, the proposed
deep unfolding NNs can achieve over one hundred times
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

ZHANG et al.: DEEP UNFOLDING LEARNING AIDED ISAC TRANSCEIVER DESIGN 8693
TABLE IV
CPU R UNNING TIME VERSUS THE NUMBER OF TIME SLOTS , W ITH (F,γ, |G|) = (10, 5, 100)
higher running speed than the ADMM in testing period, while
they are inferior to the USL in testing time due to the more
complicated operations.
Fig. 8 depicts the convergence curves of the ADMM-PGD-
NET and ADMM-DL-NET versus the learning rate, with ρ =
0.3. We can see that the ADMM-DL-NET can converge to
a better stationary point than ADMM-PGD-NET counterpart
when η = 0.001 and η = 0.0005. Moreover, the learning rate
plays an important role in the performance of the proposed
deep unfolding networks. On the one hand, a small learning
rate slows down the convergence speed. On the other hand, a
large learning rate exacerbates the oscillation of the loss curve.
Consequently, there is a trade-off between the convergence
speed and stability. Sinceη = 0.0005 can keep a good balance
between the convergence speed and stability, the learning rate
is set as 0.0005 for both the ADMM-PGD-NET and ADMM-
DL-NET.
Fig. 9 depicts the convergence curves of the ADMM-PGD-
NET and ADMM-DL-NET versus ρ, with η = 0.0005. It can
be seen that, under different ρ, both ADMM-PGD-NET and
ADMM-DL-NET can converge within 100 episodes. More-
over, the ADMM-DL-NET can converge to a better stationary
point than ADMM-PGD-NET counterpart at the cost of slower
convergence speed.
Fig. 10 illustrates the achievable rate of the proposed
NNs and benchmarks versus the communication SNR, 6 with
ρ = 0 .3. From Fig. 10, the achievable rate of all algo-
rithms increases with SNR, and the ADMM achieves the
best performance among all algorithms. When SNR is large,
the waveform similarity constraint becomes the performance
bottleneck of all the algorithms, which veriﬁes the dichotomy
between communication and sensing waveform. Moreover, our
proposed two deep unfolding NNs achieve comparable perfor-
mance to the ADMM, and the ADMM-PDG-NET outperforms
the ADMM-DL-NET. The proposed two deep unfolding NNs
are superior to the USL, and the performance gap increases
with SNR.
Fig. 11 shows the sensing SNR versus L for the proposed
NNs and benchmarks, with ρ = 0.3. The sensing SNR of all
algorithms except USL increases with L because the transmit
and receive beamforming gain increase with L. Nevertheless,
the sensing SNR of USL does not monotonically increase with
6The communication SNR is denoted as Psσ2c .
L. Moreover, both the ADMM-PDG-NET and ADMM-DL-
NET achieve the comparable performance to the ADMM, and
the performance gaps are small.
Fig. 12 illustrates the performance of the proposed algo-
rithms under different channel realizations, with ρ = 0.3. It
can be observed that the ADMM serves as an upper bound
of the other three algorithms. Although the NNs are trained
in Channel 1, they can perform well in both Channel 2 and
Channel 3, enjoying satisfactory generalization. Furthermore,
our proposed unfolding NNs demonstrate better performance
over the USL.
VI. C ONCLUSION
We investigated the deep unfolding learning-aided
transceiver design for an ISAC system in a cluttered
environment. Speciﬁcally, the weighted sum of MUI energy
and the reciprocal of sensing SINR was minimized subject to
the constraints of waveform similarity and constant modulus.
An ADMM-based iterative algorithm was ﬁrst proposed
to deal with the non-convex optimization problem, which
decomposed the original problem into six subproblems to
be optimized alternately. Then, we developed two deep
unfolding NNs, named ADMM-DL-NET and ADMM-PGD-
NET, to reduce the computational complexity. In particular,
the ADMM-PGD-NET and ADMM-DL-NET unfolded
the underlying ADMM-based iterative algorithm into the
lightweight NNs with several learnable parameters, and
circumvented the bisection method by the Uzawa’s method
and PGD, respectively. Simulation results illustrated that our
proposed two deep unfolding NNs can achieve comparable
performance with much lower computational complexity than
the underlying iterative algorithm, and outperformed the USL
in performance and number of learnable parameters. In the
future, we will compare the joint-design waveform scheme
with both communication-centric and radar-centric waveform
schemes.
REFERENCES
[1] J. Zhang et al., “Performance-complexity tradeoff for ISAC transceiver
design: A deep unfolding method,” in Proc. IEEE ICC , Jul. 2025,
pp. 1–6.
[2] X. Yu, J. Xu, N. Zhao, X. Wang, and D. Niyato, “Security enhancement
of ISAC via IRS-UA V ,”IEEE Trans. Wireless Commun., vol. 23, no. 10,
pp. 15601–15612, Oct. 2024.
[3] A. Hassanien, M. G. Amin, E. Aboutanios, and B. Himed, “Dual-
function radar communication systems: A solution to the spectrum
congestion problem,” IEEE Signal Process. Mag. , vol. 36, no. 5,
pp. 115–126, Sep. 2019.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

8694 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 10, OCTOBER 2025
[4] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[5] J. A. Zhang et al., “Enabling joint communication and radar sensing
in mobile networks—A survey,” IEEE Commun. Surveys Tuts. , vol. 24,
no. 1, pp. 306–345, 1st Quart., 2022.
[6] A. Liu et al., “A survey on fundamental limits of integrated sensing
and communication,” IEEE Commun. Surveys Tuts. , vol. 24, no. 2,
pp. 994–1034, 2nd Quart., 2022.
[7] A. Hassanien, M. G. Amin, Y . D. Zhang, and F. Ahmad, “Dual-function
radar-communications: Information embedding using sidelobe control
and waveform diversity,” IEEE Trans. Signal Process. , vol. 64, no. 8,
pp. 2168–2181, Apr. 2016.
[8] W. Zhou, R. Zhang, G. Chen, and W. Wu, “Integrated sensing and
communication waveform design: A survey,” IEEE Open J. Commun.
Soc., vol. 3, pp. 1930–1949, 2022.
[9] J. Zhang et al., “Joint design for STAR-RIS aided ISAC: Decou-
pling or learning,” IEEE Trans. Wireless Commun. , vol. 23, no. 10,
pp. 14365–14379, Oct. 2024.
[10] F. Liu et al., “Seventy years of radar and communications: The road
from separation to integration,” IEEE Signal Process. Mag. , vol. 40,
no. 5, pp. 106–121, Jul. 2023.
[11] Y . Xiong, F. Liu, Y . Cui, W. Yuan, T. X. Han, and G. Caire, “On
the fundamental tradeoff of integrated sensing and communications
under Gaussian channels,” IEEE Trans. Inf. Theory , vol. 69, no. 9,
pp. 5723–5751, Sep. 2023.
[12] J. A. Zhang et al., “An overview of signal processing techniques for joint
communication and radar sensing,” IEEE J. Sel. Topics Signal Process. ,
vol. 15, no. 6, pp. 1295–1315, Nov. 2021.
[13] F. Liu, C. Masouros, T. Ratnarajah, and A. Petropulu, “On range sidelobe
reduction for dual-functional radar-communication waveforms,” IEEE
Wireless Commun. Lett. , vol. 9, no. 9, pp. 1572–1576, Sep. 2020.
[14] Y . Ding, S. Yan, X. Zhou, F. Shu, and S. Feng, “Radar-communication
waveform design with detection probability constraints,” IEEE Wireless
Commun. Lett. , vol. 12, no. 1, pp. 168–172, Jan. 2023.
[15] R. Yang, H. Jiang, and L. Qu, “Waveform design for MIMO dual-
functional radar-communication system using MUI energy minimization
with PAPR and CRB constraints,” IEEE Commun. Lett. , vol. 27, no. 5,
pp. 1417–1421, May 2023.
[16] X. Wang, Z. Fei, J. Huang, and H. Yu, “Joint waveform and discrete
phase shift design for RIS-assisted integrated sensing and communi-
cation system under Cramer–Rao bound constraint,” IEEE Trans. V eh.
Technol., vol. 71, no. 1, pp. 1004–1009, Jan. 2022.
[17] W. Wu, B. Tang, and X. Wang, “Constant-modulus waveform design for
dual-function radar-communication systems in the presence of clutter,”
IEEE Trans. Aerosp. Electron. Syst., vol. 59, no. 4, pp. 4005–4017, Aug.
2023.
[18] C. G. Tsinos, A. Arora, S. Chatzinotas, and B. Ottersten, “Joint
transmit waveform and receive ﬁlter design for dual-function radar-
communication systems,” IEEE J. Sel. Topics Signal Process. , vol. 15,
no. 6, pp. 1378–1392, Nov. 2021.
[19] C. Wen, Y . Huang, and T. N. Davidson, “Efﬁcient transceiver design
for MIMO dual-function radar-communication systems,” IEEE Trans.
Signal Process., vol. 71, pp. 1786–1801, 2023.
[20] L. Chen, Z. Wang, Y . Du, Y . Chen, and F. R. Yu, “Generalized
transceiver beamforming for DFRC with MIMO radar and MU-
MIMO communication,” IEEE J. Sel. Areas Commun. , vol. 40, no. 6,
pp. 1795–1808, Jun. 2022.
[21] Y . Wang, C. Yang, S. Lan, L. Zhu, and Y . Zhang, “End-edge-cloud
collaborative computing for deep learning: A comprehensive survey,”
IEEE Commun. Surveys Tuts., vol. 26, no. 4, pp. 2647–2683, 4th Quart.,
2024.
[22] J. Zhang et al., “Intelligent waveform design for integrated sensing and
communication,” IEEE Wireless Commun. , vol. 32, no. 1, pp. 166–173,
Feb. 2025.
[23] J. Ye, L. Huang, Z. Chen, P. Zhang, and M. Rihan, “Unsupervised
learning for joint beamforming design in RIS-aided ISAC systems,”
IEEE Wireless Commun. Lett. , vol. 13, no. 8, pp. 2100–2104, Aug.
2024.
[24] X. Liu, H. Zhang, K. Long, A. Nallanathan, and V . C. M. Leung,
“Distributed unsupervised learning for interference management in
integrated sensing and communication systems,” IEEE Trans. Wireless
Commun., vol. 22, no. 12, pp. 9301–9312, Dec. 2023.
[25] H. He, C.-K. Wen, S. Jin, and G. Y . Li, “Model-driven deep learning for
MIMO detection,” IEEE Trans. Signal Process., vol. 68, pp. 1702–1715,
2020.
[26] H. He, S. Jin, C.-K. Wen, F. Gao, G. Y . Li, and Z. Xu, “Model-
driven deep learning for physical layer communications,” IEEE Wireless
Commun., vol. 26, no. 5, pp. 77–83, Oct. 2019.
[27] N. T. Nguyen, L. V . Nguyen, N. Shlezinger, Y . C. Eldar, A. L. Swindle-
hurst, and M. Juntti, “Joint communications and sensing hybrid
beamforming design via deep unfolding,” IEEE J. Sel. Topics Signal
Process., vol. 18, no. 5, pp. 901–916, Jul. 2024.
[28] P. Krishnananthalingam, N. T. Nguyen, and M. Juntti, “Constant mod-
ulus waveform design for wideband multicarrier joint communications
and sensing via deep unfolding,” in Proc. IEEE Wireless Commun. Netw.
Conf. (WCNC) , Dubai, United Arab Emirates, Apr. 2024, pp. 1–6.
[29] J. Zhang, M. Liu, J. Tang, N. Zhao, D. Niyato, and X. Wang, “Joint
design for RIS-aided ISAC via deep unfolding learning,” IEEE Trans.
Cognit. Commun. Netw. , vol. 11, no. 1, pp. 349–361, Feb. 2025.
[30] W. Jiang, D. Ma, Z. Wei, Z. Feng, P. Zhang, and J. Peng, “ISAC-
NET: Model-driven deep learning for integrated passive sensing and
communication,” IEEE Trans. Commun., vol. 72, no. 8, pp. 4692–4707,
Aug. 2024.
[31] Z. Zhao, J. Hu, K. Zhong, Y . Zuo, H. Li, and B. Zhang, “MIMO radar
waveform design for range-ISL optimization via iterative deep unfolding
network,” IEEE Geosci. Remote Sens. Lett. , vol. 21, pp. 1–5, 2024.
[32] G. Cui, H. Li, and M. Rangaswamy, “MIMO radar waveform design
with constant modulus and similarity constraints,” IEEE Trans. Signal
Process., vol. 62, no. 2, pp. 343–353, Jan. 2014.
[33] Z.-Q. Luo, W.-K. Ma, A. So, Y . Ye, and S. Zhang, “Semideﬁnite
relaxation of quadratic optimization problems,” IEEE Signal Process.
Mag., vol. 27, no. 3, pp. 20–34, May 2010.
[34] J. H. Manton, “Geometry, manifolds, and nonconvex optimization: How
geometry can help optimization,” IEEE Signal Process. Mag. , vol. 37,
no. 5, pp. 109–119, Sep. 2020.
[35] C. Pan et al., “Intelligent reﬂecting surface aided MIMO broadcasting
for simultaneous wireless information and power transfer,” IEEE J. Sel.
Areas Commun., vol. 38, no. 8, pp. 1719–1734, Aug. 2020.
[36] S. Boyd et al., “Distributed optimization and statistical learning via
the alternating direction method of multipliers,” F ound. Trends Mach.
Learn., vol. 3, no. 1, pp. 1–122, 2011.
[37] J. Zhang, C. Masouros, and L. Hanzo, “Joint precoding and CSI
dimensionality reduction: An efﬁcient deep unfolding approach,” IEEE
Trans. Wireless Commun. , vol. 22, no. 12, pp. 9502–9516, Dec. 2023.
[38] M.-T. Nguyen, G. Kaddoum, B. Selim, K. V . Srinivas, and P. F. de
Araujo-Filho, “Deep unfolding network for PAPR reduction in mul-
ticarrier OFDM systems,” IEEE Commun. Lett. , vol. 26, no. 11,
pp. 2616–2620, Nov. 2022.
Jifa Zhang received the M.S. degree from Beihang
University, China, in 2023. He is currently pursuing
the Ph.D. degree with the School of Information
and Communication Engineering, Dalian University
of Technology, China. His current research interests
include artiﬁcial intelligence, optimization theory,
and integrated sensing and communication. He won
the Best Paper Award in WCSP 2024 and the Hon-
orable Mentions Award in IEEE MAPE 2024.
Yongxu Zhu (Senior Member, IEEE) received the
Ph.D. degree in electrical engineering from Univer-
sity College London in 2017. From 2017 to 2019,
she was a Research Associate at Loughborough
University. From 2019 to 2023, she held positions as
a Senior Lecturer at London South Bank University
and an Assistant Professor at the University of
Warwick. She is currently a Professor at Southeast
University. Her research interests include B5G/6G,
edge mobile intelligent networks, cell-free wireless
networks, and non-terrestrial networks. She also
serves as an Editor for IEEE W IRELESS COMMUNICATIONS LETTERS and
IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply. 

ZHANG et al.: DEEP UNFOLDING LEARNING AIDED ISAC TRANSCEIVER DESIGN 8695
Nan Zhao (Senior Member, IEEE) received the
Ph.D. degree in information and communication
engineering from Harbin Institute of Technol-
ogy, Harbin, China, in 2011. He is currently
a Professor at Dalian University of Technology,
China. He is serving on the editorial boards of
IEEE W IRELESS COMMUNICATIONS and IEEE
WIRELESS COMMUNICATIONS LETTERS . He won
the best paper awards in IEEE VTC 2017 Spring,
ICNC 2018, WCSP 2018, and WCSP 2019. He also
received the IEEE Communications Society Asia-
Paciﬁc Board Outstanding Young Researcher Award in 2018.
Shi Jin (Fellow, IEEE) received the B.S. degree in
communications engineering from Guilin University
of Electronic Technology, Guilin, China, in 1996, the
M.S. degree from Nanjing University of Posts and
Telecommunications, Nanjing, China, in 2003, and
the Ph.D. degree in information and communications
engineering from Southeast University, Nanjing, in
2007. From June 2007 to October 2009, he was a
Research Fellow with the Adastral Park Research
Campus, University College London, London, U.K.
He is currently a Faculty Member of the National
Mobile Communications Research Laboratory, Southeast University. His
research interests include wireless communications, random matrix theory, and
information theory. He is serving as an Area Editor for IEEE T RANSACTIONS
ON COMMUNICATIONS and IET Electronics Letters . He was an Associate
Editor of IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE
COMMUNICATIONS LETTERS , and IET Communications . He and his co-
authors have been awarded the 2011 IEEE Communications Society Stephen
O. Rice Prize Paper Award in the ﬁeld of communication theory, the
2024 IEEE Communications Society Marconi Prize Paper Award, the IEEE
Vehicular Technology Society 2023 Jack Neubauer Memorial Award, the 2022
Best Paper Award, and the 2010 Young Author Best Paper Award by the IEEE
Signal Processing Society.
Xianbin Wang (Fellow, IEEE) received the Ph.D.
degree in electrical and computer engineering from
the National University of Singapore, in 2001.
He has been with Western University, Canada,
since 2008, where he is currently a Distinguished
University Professor and the Tier-1 Canada Research
Chair of Trusted Communications and Computing.
Prior to joining Western University, he was with
the Communications Research Centre Canada, as
a Research Scientist and later a Senior Research
Scientist, from 2002 to 2007. From 2001 to 2002,
he was a System Designer at STMicroelectronics. He has over 600 highly
cited journals and conference papers, in addition to over 30 granted and
pending patents and several standard contributions. His current research
interests include 5G/6G technologies, the Internet of Things, machine learning,
communications security, digital twin, and intelligent communications.
Dr. Wang is a fellow of Canadian Academy of Engineering and the
Engineering Institute of Canada. He is currently a member of the Senate,
the Senate Committee on Academic Policy, and the Senate Committee on
University Planning at Western. He has received many prestigious awards
and recognitions, including the IEEE Canada R. A. Fessenden Award,
Canada Research Chair, Engineering Research Excellence Award at Western
University, Canadian Federal Government Public Service Award, Ontario
Early Researcher Award, and ten best paper awards. He also serves on the
NSERC Discovery Grant Review Panel for Computer Science. He has been
involved in many ﬂagship conferences, including IEEE GLOBECOM, ICC,
VTC, PIMRC, WCNC, CCECE, and ICNC, in different roles, such as the
General Chair, the TPC Chair, the Symposium Chair, the Tutorial Instructor,
the Track Chair, the Session Chair, and a Keynote Speaker. He serves/has
served as the editor-in-chief, the associate editor-in-chief, an area editor, and
an editor/associate editor for over ten journals. He was the Chair of the
IEEE ComSoc Signal Processing and Computing for Communications (SPCC)
Technical Committee and is currently serving as the Central Area Chair of
the IEEE Canada.
Derrick Wing Kwan Ng (Fellow, IEEE) received
the bachelor’s (Hons.) and Master of Philoso-
phy degrees in electronic engineering from The
Hong Kong University of Science and Technology
(HKUST), Hong Kong, in 2006 and 2008, respec-
tively, and the Ph.D. degree from The University
of British Columbia, Vancouver, BC, Canada, in
November 2012.
Following his Ph.D., he was a Senior Post-
Doctoral Fellow at the Institute for Digital Commu-
nications, Friedrich-Alexander-University Erlangen-
N¨urnberg (FAU), Germany. He is currently a Scientia Associate Professor with
the University of New South Wales, Sydney, NSW, Australia. His research
interests include global optimization, integrated sensing and communication
(ISAC), physical layer security, IRS-assisted communication, UA V-assisted
communication, wireless information and power transfer, and green (energy-
efﬁcient) wireless communications. He has been recognized as a Highly Cited
Researcher by Clarivate Analytics (Web of Science) since 2018. He was
a recipient of Australian Research Council (ARC) Discovery Early Career
Researcher Award 2017, the IEEE Communications Society Leonard G. Abra-
ham Prize 2023, the IEEE Communications Society Stephen O. Rice Prize
2022, the best paper awards at the WCSP 2020 and 2021, the IEEE TCGCC
Best Journal Paper Award 2018, the INISCOM 2018, the IEEE International
Conference on Communications (ICC) 2018, 2021, 2023, and 2024, the
IEEE International Conference on Computing, Networking and Communi-
cations (ICNC) 2016, the IEEE Wireless Communications and Networking
Conference (WCNC) 2012, the IEEE Global Telecommunication Conference
(Globecom) 2011, 2021, and 2023, and the IEEE Third International Confer-
ence on Communications and Networking in China 2008. From January 2012
to December 2019, he served as an Editorial Assistant to the Editor-in-Chief
for IEEE T RANSACTIONS ON COMMUNICATIONS . He is also an Area Editor
of IEEE T RANSACTIONS ON COMMUNICATIONS , the Associate Editor-in-
Chief of IEEE O PEN JOURNAL OF THE COMMUNICATIONS SOCIETY , and
a member of IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS
Executive Editorial Committee.
Naofal Al-Dhahir (Fellow, IEEE) received the
Ph.D. degree from Stanford University. He was a
Principal Member of Technical Staff at the GE
Research Center and the AT&T Shannon Laboratory
from 1994 to 2003. He is currently an Erik Jons-
son Distinguished Professor and the ECE Associate
Head of UT-Dallas. He is the co-inventor of 43
issued patents, the co-author of over 650 articles, and
a co-recipient of eight IEEE best paper awards. He is
a fellow of the U.S. National Academy of Inventors,
a member of European Academy of Sciences and
Arts, and a Web of Science Clarivate Highly Cited Researcher. He is an AAIA
Fellow and received the 2019 IEEE COMSOC SPCC Technical Recognition
Award, the 2021 Qualcomm Faculty Award, and the 2022 IEEE COMSOC
RCC Technical Recognition Award. He served as the Editor-in-Chief for IEEE
TRANSACTIONS ON COMMUNICATIONS from January 2016 to December
2019.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:25:25 UTC from IEEE Xplore.  Restrictions apply.