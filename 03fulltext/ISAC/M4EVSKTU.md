---
title: "Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using Meta Deep Reinforcement Learning"
zotero_key: "M4EVSKTU"
pdf_key: "P6HRFKYQ"
doi: "10.1109/TWC.2025.3580347"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Joint Beamforming and Resource Allocation for STAR-IRS-Aided SCMA ISAC Systems Using Meta Deep Reinforcement Learning — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

10534 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
Joint Beamforming and Resource Allocation for
STAR-IRS-Aided SCMA ISAC Systems Using
Meta Deep Reinforcement Learning
Armin Farhadi
 , Ali Olfat
 , Senior Member, IEEE, and Christos Masouros
 , Fellow, IEEE
Abstract—In response to growing demands for both sensing
and communication performance from future applications of
wireless networks, simultaneous transmitting and reﬂecting intel-
ligent reﬂecting surface (STAR-IRS), sparse code multiple access
(SCMA), and integrated sensing and communication (ISAC)
have been introduced. In this paper, we investigate the joint
beamforming and resource allocation optimization problem (OP)
for STAR-IRS-Aided SCMA for an ISAC System by considering
ISAC, SCMA, beamforming, quality of service (QoS), and STAR-
IRS constraints in the THz band. The investigated OP is a type
of NP-hard OP that cannot be solved by conventional methods.
Moreover, the possible solution must have the ability to adapt
to different situations. Then to solve this problem efﬁciently, we
employ a new meta deep reinforcement learning (MDRL). The
simulation results demonstrate the effectiveness of the proposed
solution for the resource allocation problem across different
system model and MDRL parameters, as well as multiple access
methods. Compared to non-orthogonal multiple access (NOMA)
and orthogonal frequency-division multiple access (OFDMA),
the proposed system model improves energy efﬁciency (EE) by
15% and 20%, respectively. The suggested MDRL approach
achieves a 123% enhancement over classic deep deterministic
policy gradient (DDPG). Additionally, a scenario involving a
coupled phase-shift model was conducted for the proposed system
model. To investigate the effect of channel state information (CSI)
estimation on our proposed system model, we considered a sim-
ulation with both imperfect and perfect CSI. Additionally, when
solving the optimization problem using a convex optimization
approach, MDRL shows a 10% improvement.
Index Terms—ISAC, STAR-IRS, SCMA, meta deep reinforce-
ment learning (MDRL), resource allocation.
I. I NTRODUCTION
I
N RECENT years, the demand for new communication
technologies has surged due to factors like the growth of
data-intensive applications and the rise of remote work and
online education. These trends underscore the need for higher
Received 12 July 2024; revised 16 December 2024 and 28 March 2025;
accepted 4 June 2025. Date of publication 24 June 2025; date of current
version 12 December 2025. This work was supported by Information and
Communication Technology (ICT) Research Institute [formerly, Iran Telecom-
munications Research Center (ITRC)] under Grant 12011 dated 15/10/2023.
The associate editor coordinating the review of this article and approving it
for publication was H. Zhou. (Corresponding author: Ali Olfat.)
Armin Farhadi and Ali Olfat are with the School of Electrical and
Computer Engineering, College of Engineering, University of Tehran, Tehran
1417935840, Iran (e-mail: armin.farhadi@ut.ac.ir; aolfat@ut.ac.ir).
Christos Masouros is with the Department of Electronic and Electrical
Engineering, University College London, WC1E 6BT London, U.K. (e-mail:
c.masouros@ucl.ac.uk).
Digital Object Identiﬁer 10.1109/TWC.2025.3580347
data rates, lower latency, and robust infrastructure. Addition-
ally, anticipated advancements toward 6G wireless systems
herald a new era in which high-precision sensing capabilities
will be integral. This presents an opportunity to develop inte-
grated sensing and communication (ISAC) systems, leveraging
advancements in millimeter-wave and massive multiple-input
and multiple-output (MIMO) technologies [1], [2].
ISAC integrates sensing and communication systems,
enhancing data acquisition and real-time data exchange [3].
It promises improved spectrum efﬁciency and reduced hard-
ware costs by harmonizing functionalities within the same
frequency band and hardware [4].
To address challenges in new communication systems, intel-
ligent reﬂecting surfaces (IRSs) have emerged as promising
techniques [5]. IRS systems, equipped with adjustable phase
shifts, enhance transmit beamforming and ISAC performance
[4]. They amplify signals and eliminate the need for dedicated
radio frequency units, leading to energy savings and superior
spectrum efﬁciency.
Recently, a new form of IRS, simultaneously transmit-
ting and reﬂecting IRS (STAR-IRS), has been introduced
[6]. Unlike traditional reﬂecting-only IRS, STAR-IRS offers
360-degree coverage [7]. It expands coverage from half-
space to full-space, enabling smart wireless communication
environments. STAR-IRS splits signals into “reﬂected” and
“transmitted” signals, creating reﬂection and transmission
regions [8].
In contrast to reﬂective-only IRS, STAR-IRS provides com-
prehensive full-space coverage by simultaneously transmitting
and reﬂecting signals [9]. It allows adjustment of transmitting
and reﬂecting coefﬁcients by tuning electromagnetic prop-
erties. Practical protocols for controlling Transmission and
Reﬂection modes in STAR-IRS include energy splitting (ES),
mode selection (MS), and time splitting (TS) [10]. IRS-
assisted wireless communication systems are gaining attention
in academia due to their numerous potential applications [11].
Next-generation wireless access networks must accommo-
date numerous users while enhancing spectral efﬁciency [12],
[13]. Non-orthogonal multiple access (NOMA) has emerged as
a solution, optimizing resource utilization and elevating spec-
tral efﬁciency [14]. Unlike orthogonal multiple access (OMA)
methods like frequency division multiple access (FDMA),
time-division multiple access (TDMA), code-division multiple
access (CDMA), and orthogonal frequency division multiple
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10535
access (OFDMA), which allocate orthogonal resources to
users, NOMA introduces controllable interference to manage
receiver complexity, enhancing spectral efﬁciency [12], [13],
[14].
Sparse code multiple access (SCMA) is a code-domain
NOMA technique to improve spectral efﬁciency in wireless
communication systems [12], [13], [15]. SCMA employs
sparse codewords to enable multi-user detection (MUD) using
the message passing algorithm (MPA) at the receiver, achiev-
ing symbol separation with manageable complexity [12], [13].
Compared to classical NOMA, SCMA enables more efﬁcient
resource utilization, improving spectral efﬁciency and system
capacity. It also offers ﬂexibility and robustness in handling
diverse user requirements and channel conditions. Through
advanced codebook-based techniques, SCMA mitigates inter-
user interference effectively, enhancing system reliability and
performance [12], [13], [16].
A. Related Works
1) ISAC: Relevant research covers topics like
radar-communication spectrum sharing and joint
radar-communication systems, including dual-function
radar-communication (DFRC) systems [3], [17], [18]. The
concept and scope of ISAC have recently been explained
[3], [4], garnering attention from both industry [19] and
academia [18]. ISAC offers dual advantages by facilitating
shared resource utilization and collaboration between sensing
and communication components, resulting in efﬁciency and
coordination gains [4].
[20] investigate a NOMA-ISAC scheme that enables simul-
taneous sensing and communication on shared radio resources.
The authors of [21] explored transmit beamforming design for
massive MIMO-ISAC (mMIMO-ISAC) systems. Authors of
[22] focused on developing robust resource allocation strate-
gies to enhance secure communication within an ISAC system.
[23] explored the problem of power allocation for onboard
ISAC systems in vehicles, addressing vehicle-to-infrastructure
and vehicle-to-vehicle communications, as well as sensing.
2) STAR-IRS & IRS: Optimizing the phase shifts of IRSs,
known as passive or active beamforming, is a signiﬁcant chal-
lenge in IRS-assisted systems. Several works have addressed
this optimization [7], [24], [25], [26], [27], [28]. For instance,
[24] aimed to maximize the total data rate in a STAR-
IRS-assisted NOMA system by jointly optimizing various
parameters. Reference [7] proposed an iterative algorithm
to minimize power consumption, optimizing both active and
passive beamforming. Reference [25] focused on minimizing
total transmit power in an IRS-assisted multiple-input single-
output (MISO) system through joint optimization. Reference
[26] introduced an algorithm based on Dinkelbach’s theory
to maximize energy efﬁciency (EE) by optimizing transmit
power and phase shifts. Reference [27] explored a cooperative
passive beamforming algorithm for a multi-IRS system to
maximize the minimum signal-to-interference-plus-noise ratio
(SINR). Reference [28] investigated an IRS-aided simultane-
ous wireless information and power transfer (SWIPT) system,
optimizing information and energy transmission. The authors
of [29] investigated a STAR-RIS-aided communication system
with a coupled transmission and reﬂection phase-shift model
and proposed an efﬁcient algorithm for optimizing amplitude
and phase-shift coefﬁcients to minimize power consumption
under user rate constraints.
3) SCMA: Recent research has explored resource allo-
cation strategies considering SCMA as an MA technique
[12], [13], [30]. Liu et al. presented an optimization frame-
work for SCMA-enabled multi-cell mobile edge computing
(MEC) networks [31]. Reference [32] proposed an IRS-aided
downlink SCMA system to enhance connectivity in future
machine-type communication networks. The authors of [33]
investigated a IRS-aided uplink SCMA cellular network with
device-to-device (D2D) users. Reference [34] developed a
joint resource allocation approach as a multi-objective (MO)
optimization problem, focusing on maximizing the average
sum rate while ensuring fairness among users. Resource allo-
cation for IRS-assisted uplink SCMA networks was examined
in [11], emphasizing energy and spectral efﬁciency. Reference
[35] proposed an IRS-assisted resource allocation problem for
semi-grant-free NOMA transmission systems to meet channel
coefﬁcient requirements for both grant-based and grant-free
users. Chai et al. addressed transmit power minimization in
perfect and imperfect channel state information (CSI) sce-
narios through joint optimization of codebook assignment,
BS active beamforming, and IRS reﬂection coefﬁcients [36].
Furthermore, the authors of [37] introduced a beamforming
and power allocation algorithm for D2D communications in
cellular networks, incorporating energy harvesting and SWIPT
to assist an SCMA network.
Previous studies introduced optimization-based algorithms
for phase shifts in IRSs, resource allocation in SCMA-aided,
and ISAC-based systems. Additionally, there is no existing
research on the resource allocation for the integrated versions
of SCMA, ISAC, and STAR-IRS (including IRS). To ﬁll
this gap, this paper investigates resource allocation in this
context. Furthermore, most published works have focused
on codebook allocation or subcarrier assignment problems.
As demonstrated in the convex optimization benchmarks, the
presence of multiple constraints signiﬁcantly complicates the
problem, often requiring long computation times to satisfy all
constraints.
These resource management problems often have non-
convex objectives and constraints, leading to high computa-
tional complexity and solutions that may deviate from the
optimal. Also in the next generation of wireless systems,
we will faced with a large number of users and devices
and it makes the problems more complex to solve [12],
[13], [24], [38]. Low latency communication is one of the
expected aspects of new wireless systems. Due to these chal-
lenges, optimization-based approaches may not be effective
for addressing non-convex issues in next-generation wireless
communication systems [39].
In response to these challenges, recent advancements have
introduced deep reinforcement learning (DRL) methods as a
viable alternative for tackling resource management problems
in wireless communication contexts [40]. Among the DRL
techniques, deep deterministic policy gradient (DDPG) is
especially well-suited for addressing OPs featuring continuous
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10536 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
TABLE I
SUMMARY OF RELATED WORKS & O UR WORK
decision variables [40]. DDPG leverages its capability to
generate probability distributions over available actions at each
state, making it a valuable tool in this regard. However, it is
important to acknowledge that DRL models trained via DDPG
may exhibit limited adaptability to new or dynamic environ-
ments. To mitigate this concern, a promising approach involves
integrating meta-learning techniques with conventional DRL
methods. This combined approach empowers DRL models to
adapt effectively to changing network conditions and evolving
environments [41].
The most important aspect of using DRL methods is con-
structing an appropriate strategy for learning. By deﬁning
a suitable learning strategy, the agent can learn how to
choose the right actions to enhance the cumulative reward.
Unfortunately, published papers have mainly studied simple
optimization problems with limited constraints or have deﬁned
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10537
actions in a way that ensures the constraints are always
satisﬁed [42], [43], [44]. Due to the nature of the DDPG
algorithm, previous works have applied it only to problems
with continuous action spaces [42], [43], [44]. Additionally,
Table I provides a summarized comparison of our work with
related studies.
B. Contribution
In this context, we aim to tackle the challenge of maxi-
mizing EE for SCMA-based systems within an ISAC-MISO
system model. Here, a STAR-IRS is employed to enhance
communication quality for multiple users operating in the
THz band. Our objective is to frame this problem as a
resource allocation and beamforming optimization problem
(OP). This entails optimizing various parameters, including the
beamforming vector at the ISAC BS, the subcarrier assignment
for each SCMA codebook, codebook allocation to individual
users, and the phase shifts and amplitude coefﬁcients at the
STAR-IRS. The objective of this OP is to maximize EE while
adhering to constraints such as the beam pattern error of the
ISAC system, SCMA, maximum available power at the ISAC
BS, QoS requirements for each user, and the amplitude and
phase shift constraints of the STAR-IRS. This problem is chal-
lenging due to the joint optimization of transmit beamforming,
SCMA assignment parameters, and the amplitude and phase
shift of STAR-IRS [12], [13], [24], [38]. Additionally, the
proposed problem is NP-hard due to its non-convex objective
function and constraints, as well as the presence of mixed inte-
ger and continuous variables [39]. To address this challenge,
meta-learning is applied in this scenario. The proposed meta-
learning can quickly adapt to different conditions. The main
contributions of this paper are summarized below.
• The STAR-IRS-aided ISAC SCMA-based system in
the THz band: The STAR-IRS is explored to compensate
for the high path loss caused by molecular absorption in
the THz band. We consider an STAR-IRS-aided ISAC
SCMA-based system to support the massive number of
users and communication and sensing capability in the
next generation of wireless system as 6G consisting of
one ISAC BS equipped with several antennas, several
users, and an STAR-IRS. The EE of the proposed ISAC
in an SCMA-based system is optimized through transmit
beamforming, SCMA assignment parameters, and phase-
shift and amplitude coefﬁcient design of the STAR-IRS.
The OP of EE maximization is formulated as a resource
allocation OP with beam pattern error of ISAC system
model, SCMA’s subcarrier assignment and codebook-
user allocation, total transmit power of the ISAC BS, QoS
for each user, and amplitude coefﬁcient and phase shift
of STAR-IRS constraints.
• The meta-learning strategy to solve the investigated
resource allocation OP: As the formulated resource
allocation OP is a non-convex mixed-integer nonlinear
programming (MINLP) by considering objective func-
tion, constraints, and optimization variables [12], [39].
Then, the proposed OP is a type of NP-hard optimization
that cannot be addressed using conventional optimization
techniques [39]. To jointly solve the studied resource
allocation OP, we introduced a Meta-DDPG algorithm
which is a type of meta-DRL, which combines meta-
learning principles with the classic DDPG method [41].
• Addressing Mixed Continuous and Discrete Action
Spaces in proposed MINLP OP: DDPG is utilized for
its continuous action space [45]. Hence, many environ-
ments that require deﬁning continuous action space use
DDPG. In the proposed problem, as mentioned, there
are continuous and discrete variables. Consequently, we
cannot use DDPG and meta-DDPG in their current form.
To address this issue, previous papers have employed
hybrid algorithms, resulting in slower convergence and
poor response. To tackle these problems, we employ a
quantization trick to address the investigated MINLP OP
using the suggested Meta-DDPG algorithm.
• Deﬁning a Hybrid Reward Function: Since the OP has
a variety of constraints, it is crucial to account for these
constraints in the Meta-based solution. To address this,
we introduce a hybrid reward function that incorporates
all constraints while maximizing the objective function.
By deﬁning this reward function we can consider all
constraints and it can improve learning and convergence.
Our work introduces a meta-learning-based approach to
maximize EE in a MISO STAR-IRS-assisted ISAC SCMA
system in the THz band. Unlike previous optimization-based
algorithms [24], [28], our Meta-DDPG algorithm adapts to
dynamic network environments, making it suitable for next-
generation wireless networks. Simulations demonstrated the
effectiveness of our system model and meta-learning approach,
showing that proper hyperparameter selection can improve
convergence speed and response. SCMA achieved the highest
EE, improving by 15% over NOMA. The proposed meta
deep reinforcement learning (MDRL) algorithm showed a
123% improvement over classic DDPG and outperformed
other actor-critic-based and hybrid algorithms. Additionally,
our convex optimization strategy, despite using multi-level
approximations and relaxations, was outperformed by MDRL,
which achieved 10% higher performance with satisfactory
running time. Additionally, we considered a scenario with
imperfect CSI for the channel between STAR-IRS and the
users to investigate the impact of CSI on the simulation
results. This scenario is close to a practical case. As we have
mentioned several times, one of our contributions in this paper
is the inclusion of STAR-IRS in the system model, based
on published studies. To make our model more realistic, we
also explored a coupled phase-shift model scenario for the
proposed system.
C. Paper Structure and Organization
This paper is structured as a continuation. Section II
introduces the system model. In Section III, we outline
the OP concerning transmit beamforming and phase-shift
and amplitude coefﬁcient design by considering SCMA-aided
and ISAC in a MISO system in THz. Section IV presents
the meta reinforcement learning algorithm, demonstrating
its application in jointly optimizing transmit beamforming,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10538 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
Fig. 1. An illustration of proposed system model as an environment of
reinforcement learning.
phase-shift, and amplitude coefﬁcient designing for the STAR-
IRS, codebook allocation, and subcarrier assignment within
the multi-user MISO scenario. The effectiveness of these
algorithms is assessed through simulation results in Section V.
Finally, Section VI provides a conclusion of the paper, high-
lighting its contributions and implications in the research
domain.
II. S YSTEM MODEL
In this study, we investigate a multi-user MISO model
within a STAR-IRS-aided ISAC for an SCMA-based system,
as illustrated in Fig. 1. The system consists of one ISAC
BS equipped with NBS antennas for both transmission and
reception of radar echo, NS STAR-IRS elements that act as
phase shifters, and U users, each having a single antenna. We
represent the sets of BS antennas and served users as NBS =
{1, 2,...,N BS} andU ={1, 2,...,U t,Ut+1,...,U t +Ur},
respectively. Here, Ur represents the number of users in the
STAR-IRS’s reﬂection zone, and Ut represents the number of
users in its transmission zone. In addition to the direct link
between the ISAC BS and users, a STAR-IRS-assisted link is
available to serve users when the direct channel link experi-
ences poor quality, possibly due to obstacles or interference.
Also, we assume that perfect CSI is available for the ﬂat-
fading channel at both the STAR-IRS and the BS. Let xj =
[x1,j,x 2,j,...,x U,j]T∈ CU×1 denote the information-bearing
symbols, and Wj ∈ CNBS×U as the transmit beamforming
matrix. Also, the ISAC BS divides the accessible bandwidthW
into a collection of subcarriers denoted by J ={1,...,J }. In
this system model to accommodate high levels of connectivity,
in the SCMA system, the number of users served exceeds
the number of available subcarriers, speciﬁcally, denoted as
J < U. Each user is allocated a codebook with dimensions
U×S, where S represents the total count of J-dimensional
codewords contained within the codebook. The transmitted
symbol after SCMA encoding Sj∈ CNBS×1 forjth subcarrier
after beamforming is given by Sj = WTj · xj.
A. Communication Signal
We introduce the channel coefﬁcients as follows: GISj ∈
CNS×NBS represents the channel coefﬁcient from the
ISAC BS to the STAR-IRS on jth subcarrier, GIUj ∈
CNBS×U denotes the channel coefﬁcient from the ISAC
BS to user u ∈ {1, 2,...,U t,Ut+1,...,U t + Ur} on
jth subcarrier, and GSUj ∈ CNS×U represents the chan-
nel coefﬁcient from STAR-IRS element NS to user u ∈
{1, 2,...,U t,Ut+1,...,U t +Ur} onjth subcarrier. The com-
munication signal rc∈ CU×1 received by users is given by
rc = ∑Cc=1∑Jj=1(GIUj + (GSUj )H∆λGIS) SjϖcOj,c + zc,
where zc ∈ CU×1 represents an independently and identi-
cally distributed complex Gaussian stochastic process, and the
vector ϖc = [ϖc1,...,ϖ cu,...,ϖ cU]T denotes the codebook
allocation to each user. Speciﬁcally, whenϖcu = 1, it indicates
that cth codebook has been allocated to the user u, and vice
versa. Additionally, Oj,c denotes the subcarrier assignment
for each codebook. If Oj,c = 1, it signiﬁes that subcarrier j
is assigned to the cth codebook. This assignment mechanism
plays a crucial role in effectively utilizing subcarriers within
the communication system. Moreover, C represents the total
number of codebooks.
The effective diagonal phase matrix of STAR-IRS, denoted
as ∆λ, is deﬁned as ∆λ = diag
{
µλ1,µλ2,...,µ λNS
}
, which
µλn = √ψλneiθλn, and θn ∈ [0, 2π] is the phase shift of the
n-th element of the STAR-IRS and i represents the imaginary
unit [45]. Besides, λ∈ Λ = {Rλ, Tλ}, where Rλ and Tλ
respectively stand for reﬂection and transmission zones. Also,
ψλn∈ [0, 1], ∑
λ∈Λ
ψλn = 1,∀n∈{ 1,...,N S} is the reﬂection
amplitude of the n-th component at the STAR-IRS. Moreover,
∆ = ∆Rλ for all users u∈ {1,...,U r}, and ∆ = ∆Tλ
for all users u∈{Ur + 1,...,U r +Ut}. In other words, for
users in the reﬂection zone ( u∈{ 1,...,U r}), ∆ = ∆Rλ is
applied, and for users in the transmission zone ( u∈{ Ur +
1,...,U r +Ut}), ∆ = ∆Tλ is used.
The channel coefﬁcients are modeled as Rician channels.
The mentioned channel coefﬁcients are deﬁned below:
Gx,yj =
√ γ
1 +γ GLOS +
√ 1
1 +γ GNLOS,
∀(x,y )∈{ (IS), (IU ), (SU )} (1)
The symbol γ represents the Rician factor.
The GLOS corresponds to the line-of-sight (LoS)
component, which can be mathematically expressed as
GLOS = κLOS(fc,d )GtGrβr (φAoA)αHt (φAoD), in this
context, βr (φAoA) denotes the receive response vector,
while αt (φAoD) represents the transmit response vector.
Additionally,φAoD and φAoA refer to the angle of departure
(AoD) and the angle of arrival (AoA), respectively.
B. Antenna Conﬁguration
We employ a uniform linear array (ULA) conﬁgura-
tion for the antennas of the ISAC BS, where the steer-
ing vector α(φ) ∈ CNBS×1 is given by α(φ) =√
1
NBS
[
1,e−j 2π𝓁ω cosφ,...,e −j 2π𝓁ω (NBS−1) cosφ]T , where 𝓁
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10539
represents the antenna element spacing, and ω is the wave-
length.
For the STAR-IRS, we consider an N =NS×NS element
uniform planar array (UPA). The corresponding array steering
vector, denoted as δ(φ,θ ) ∈ CN×1, can be expressed as
follows:
δ(φ,θ ) = 1N[1,...,e j 2πω 𝓁(n cosθ cosφ+n sinθ sinφ),...,
ej 2πω 𝓁((√N−1) cosθ cosφ+(√N−1) sinθ sinφ)]T, (2)
The variable n represents the antenna element index, where
0≤n≤ N− 1.
C. Pathloss Model
In the THz band, we consider both the free space
pathloss Lfs and the module pathloss Lη. The LoS pathloss
denoted as |κL(fc,d )|2, is expressed as |κL(fc,d )|2 =
Lfs(fc,d )Lη(fc,d ), where c is the speed of light, fc is the
carrier frequency, and d is the transmission distance.The free
space pathloss Lfs(fc,d ) can be calculated as Lfs(fc,d ) =(
c
4πfcd
)2
.
Similarly, the channel state of the NLoS
component GNLOS is given by GNLOS =∑LNLOS
l=1 κNLOS,l(fc,d )GtGrβr (θAoA,l)αHt (θAoD,l), where Gt
and Gr demonstrate the channel coefﬁcients associated with
the transmit and received antennas, respectively. Additionally,
LNLOS stands for the count of non-line-of-sight (NLoS) rays,
while κ(fc,d ) represents the complex gain of the path.
The expressions for the large-scale channel coefﬁcientsκLOS
and κNLOS are as follows:
κLOS(fc,d ) =Lfs(fc,d )Lab(fc,d ) (3)
=
( c
4πfcd
)2
e−kabsorp(fc)d, (4)
κNLOS(fc,d ) =ϕ2(fc)Lfs(fc,d )Lab(fc,d ) (5)
=
( c
4πfcd
)2
e−kabsorp(fc)d, (6)
The constant representing the speed of light is symbolized as
c = 3 × 108 m/s. Let us denote the transmission distance
in free space as d. The absorption coefﬁcient kabs(fc) can be
ascertained through the examination of molecular-level prop-
erties of the medium [46]. On the other hand, the reﬂecting
coefﬁcientϕ(fc) results from the multiplication of the Fresnel
reﬂection coefﬁcient ν and the Rayleigh roughness factor χ.
It’s important to emphasize that, within the THz band, our
consideration is limited to high reﬂection losses, encompassing
reﬂections up to the second order.
These are composed of both reﬂection and
scattering, allowing us to compute the channel state
for each user u on cth codebook as ru,ccomm =∑J
j=1
(
GIUj,u + (GSUj,u)H∆GISj) SjϖcuOj,c + zu,ccomm [47].
Additionally, the SINR for user u on the cth codebook can
be calculated as (7), shown at the bottom of the next page,
[12], [32].
D. Radar Signal
The radar signal received at the
ISAC receiver is described as rR =∑C
c=1
∑J
j=1
(
(GIS)H∆Π∆HGIS + Ξ) SjϖcOj,c + zR
[48].
It’s assumed that STAR-IRS operates as a mono-static
MIMO radar [49]. Therefore, we designate Ξ∈ CNBS×NBS as
the target response matrix for the ISAC BS, and Π∈ CNS×NS
as the target response matrix derived from the parameters
of the STAR-IRS’s elements within the device-based ISAC
system. The computation of these matrices is outlined as
follows:
Ξ =
U∑
u=1
auαr (φu)αHt (φu), (8)
Π =
U∑
u=1
auδr (vk,θu)δHt (vk,θu). (9)
au represents the complex pathloss, encompassing the
pathloss coefﬁcient, reﬂection factors, and the complex radar
cross-section of the target. The vectors αt(φ) and αr(φ)
denote the array steering vectors for transmit and receive
antennas, respectively.
In the context of radar signals, the proposed system in
[17] considered beam pattern error. The design of MIMO
radar transmit beamforming aims to optimize the transmit
power in speciﬁc directions or generally match a desired beam
pattern. The beam pattern error is quantiﬁed as the mean
square error (MSE) between the obtained beam pattern and
the ideal beam pattern, calculated using the ϵBeam(Rj) =
1
L
∑L
l=1|P (θl)−d (θl)|2 formula, where Rj = WjWHj rep-
resents the covariance matrix for jth subcarrier. The direction
grids{θl}Ll=1 are sampled in the range of −90◦ to 90◦ with a
resolution of 0.1◦. P (θl) =αH(θl)Rα(θl) represents power
emitted in the direction θl, and d(θl) is the desired beam
pattern. Its calculation principle is deﬁned as:
d(θ) =
{
1, θ s− Γ/2≤θ≤θs + Γ/2,s = 1, 2, 3
0, otherwise, (10)
Here, the ideal beam pattern θs consists of three main beams,
each with a width of Γ = 10◦.
The beam pattern error is treated as a constraint, expressed
as ϵBeam(Rj)≤ ϵ0, this constraint signiﬁes that the beam
pattern error must not surpass the threshold ϵ0, which serves
as an indicator of sensing performance accuracy.
E. SCMA Structure
SCMA is predominantly characterized by its sparse code-
books, and the assignment of subcarriers to users within
SCMA can be effectively depicted using a bipartite factor
graph. In this study, we employ a standard factor graph
representation, where each user is assigned dv subcarriers, and
each subcarrier is allocated to df users. As depicted in Fig. 2,
the structure of SCMA codebooks, encoding, the relationship
between users and transmission codewords, and the multiplex-
ing of codewords over shared orthogonal resources are shown
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10540 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
Fig. 2. Illustration of SCMA codebooks, encoding, and multiplexing over
shared orthogonal resource for four subcarriers and six codebooks.
for 4 subcarriers and 6 codebooks. Furthermore, the ﬁgure
illustrates the inherent sparsity of codebooks, aligning with
the fundamental principles of SCMA.
Next, we can employ the Maximum a-posteriori (MAP)
technique to detect the SCMA multi-user codeword X =
[x1, x2,··· , xU], as discussed in [50] and [51]:
ˆX = argmax
xu,∀u∈{1,...,U}
Pro(X| rcomm). (11)
The marginal distribution of equation (11) concerning xu
provides us with the detected symbol for the u-th user.
Subsequently, by applying Bayes’ rule, we can determine the
detected codeword for the u-th user as follows:
ˆxu = argmax
xu,∀u∈{1,...,U}
∑
∼xu
(
Pro(X)
C∏
c=1
f (rccomm| X)
)
,
for u = 1,··· ,U. (12)
In this equation, f (rccomm| X) represents the conditional
probability density function (PDF) of the received value, and
P (X) denotes the joint a-priori probability mass function
(PMF). Solving the problem presented in (12) using a brute-
force approach results in exponential complexity. Fortunately,
this issue can be efﬁciently addressed by employing an
iterative message passing algorithm (MPA) with reduced com-
plexity, as explained in [12], [13], and [50]. The complexity
associated with SCMA multi-user detection using MPA scales
proportionally to Sdf .
III. P ROBLEM FORMULATION
In this section problem formulation for the proposed system
model was introduced. To this end, we study maximizing
EE problem in a STAR-IRS-assisted SCMA in the ISAC
system, where a BS communicates and senses users with the
aid of a STAR-IRS. The total EE is obtained from EE =∑U
u=1
∑C
c=1 log2(1+Υu,c)
PC,sum . In this formula, the overall powerconsumption of the system is denoted as PC,sum. It accounts
for various contributing factors, which are the power used
by the active array components of the STAR-IRS, the ﬁxed
circuit power costs attributed to the electrical components, and
the static power needed to maintain the fundamental circuit
operations of the STAR-IRS. We express this as PC,sum =
1
ℵ
∑U
u=1
∑J
j=1
∑C
c=1‖wj,u‖2ϖcuOj,c + PSTAR-IRS + Pcirc ,
here, ℵ is power ampliﬁer efﬁciency [52]. Pcirc represents
the ﬁxed circuit power costs arising from the power con-
sumption of all electrical components in both the receiver,
denoted asP ucirc, and the transmitter, referred to as P BScirc . Then,
Pcirc =P BScirc +∑Uu=1P ucirc . Additionally,PSTAR-IRS is deﬁned
as PSta +NBSPDina . In this expression, PDina signiﬁes the
dynamic power associated with each reﬂecting component,
while PSta represents the static power required to support the
basic circuit activities of the STAR-IRS.
We formulate the OP problem, which aims at maximizing
EE by jointly optimizing the transmit beamforming Wj =
[wj,1,..., wj,U]∈ CNBS×U at the ISAC BS, ∆ at the STAR-
IRS, codebook allocation ϖcu for each user u on codebook c,
and subcarrier assignment variable Oj,c for codebook c that
uses jth subcarrier. The OP is formally stated as:
P1 : max
{ϖcu},{Oj,c},{Wj},∆EE,
s.t. C1 : ϵBeam(Rj)≤ϵ0, ∀j∈ J, (13a)
C2 :
C∑
c=1
Oj,c≤df, ∀j∈ J, (13b)
C3 :
J∑
j=1
Oj,c≤dv, ∀c∈ C, (13c)
C4 :
C∑
c=1
ϖcu≤D, ∀u∈U , (13d)
C5 :
J∑
j=1
U∑
u=1
‖wj,u‖2≤P max, (13e)
C6 :
C∑
c=1
log2 (1 + Υu,c)≥Rth ∀u∈U ,
(13f)
C7 : ψRλn ,ψRλn ∈ [0, 1],ψRλn +ψTλn = 1,
(13g)
C8 : θRλn ,θTλn ∈ [0, 2π], (13h)
C9 : O j,c∈{ 0, 1} ∀j∈ J,c∈ C,
ϖcu∈{ 0, 1} ∀u∈U ,c∈ C, (13i)
The beam pattern error constraint for each subcarrier is
addressed in (13a), indicating the implication of ISAC on our
system model. Furthermore, constraint (13b) limits the max-
imum number of signals multiplexed on each subcarrier, and
constraint (13c) denotes that each codeword of the codebook
has a maximum of dv non-zero values. Also, (13d) shows
Υu,c =
∑J
j=1
⏐⏐(GIUj,u + (GSUj,u)H∆GISj) wj,u⏐⏐2ϖcuOj,c
∑
l⁄=u
∑J
j=1
⏐⏐⏐(GIUj,l + (GSUj,l)H∆GISj) wj,l⏐⏐⏐2ϖclOj,c +σ2u,c. (7)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10541
the maximum number of codebooks assigned to each user. It
is necessary to mention that the three constraints mentioned
above are related to the SCMA structure. Constraint (13e)
implies that the total transmit power of the ISAC BS should
not exceed the ISAC BS’s maximum power budget. To provide
a minimum rate for each user, the QoS constraint is indicated
in (13f). The constraints for the amplitude coefﬁcients and
phase shift of the STAR-IRS are denoted by (13g) and (13h),
respectively. Finally, (13i) shows the SCMA parameters are
discrete.
Problem (13) is an OP with a non-convex objective func-
tion and constraints and includes nonlinear constraints with
a mix of binary and continuous variables. In other words,
the resource allocation problem is an MINLP problem that
cannot be efﬁciently solved by optimization-based algorithms.
To solve problem (13), we propose a Meta-Learning method
which is explained in the next section.
IV. P ROPOSED META-DRL S OLUTION
In this section, we present the Meta-DDPG approach, which
leverages the Meta-DRL algorithm to address problem (13).
To begin, we start by framing problem (13) as a Markovian
decision process (MDP). Subsequently, we provide a detailed
explanation of the Meta-DDPG technique. To this end, We
explain the key components and mechanisms of Meta-DDPG
by mathematics formula. Moreover, we illustrate how the syn-
ergy of Meta-DDPG enhances the efﬁciency and effectiveness
of addressing complex problems, making it a valuable tool for
solving (13).
The problem within the framework of MDP is characterized
by three fundamental components: the state spaceS, the action
spaceA, and the reward function R. These components are
deﬁned as follows: [40] and [41].
1) State Space S:
The state spaceS encompasses various parameters, includ-
ing channel information, SINR levels, and the EE. It can be
formally represented as follows:
S
={{GISj}j∈J,{GIUj}j∈J,{GSUj }j∈J,{Υu,c}∀u∈U,c∈C,EE}.
(14)
2) Action Space A:
To address problem (13), the action space plays a pivotal
role, encompassing a set of crucial decision variables. These
variables have a signiﬁcant inﬂuence over the system’s opera-
tions and include the beamforming vector, SCMA assignment
parameters, and amplitude coefﬁcients and phase shifts of
STAR-IRS. In problem (13), the action space is meticulously
delineated and is formally characterized as follows:
A ={{ϖcu}∀u∈U,c∈C,{Oj,c}∀j∈J,c∈C,{Wj}j∈J, ∆}. (15)
The DDPG algorithm, which is a type of DRL, generates
action spaces in a continuous format. This is suitable for
solving OPs that involve continuous optimization variables.
However, our proposed problem (13), as mentioned earlier, is
a MINLP problem that includes both discrete and continuous
variables. Therefore, we cannot use this algorithm in its current
format. To address the proposed OP in (13) efﬁciently and
without adding complexity, we employ a quantization tech-
nique to convert continuous actions into discrete optimization
variables.
Thus,A constitutes a set of continuous variables. However,
in OP (13), ϖcu and Oj,c are discrete. Consequently, due to
these reasons, a proper transformation is required to address
this issue. Conversely, the output of the neural network is
determined by the activation function. The hyperbolic tangent
(Tanh) function is utilized as the activation function in the
actor network. Therefore, the output of the actor network
ranges between−1 and 1. Subsequently, we employ clipping
to conﬁne the output between 0 and 1. This entails projecting
negative values to zero in this scenario. Following this, we
apply a quantization trick by considering 0.5 as a threshold.
Any value from the neural network output that is less than 0.5
is projected to zero, and vice versa.
3) Reward Function R:
In the fundamental principles of RL, rewards play a key role
in inﬂuencing the selection of actions [43], [53]. Therefore,
it is necessary to design rewards meticulously to guide the
learning process effectively. In the context of addressing the
optimization objective outlined in problem (13), which aims
to maximize EE while satisfying the constraints deﬁned in
(13a) through (13i), it is vital to ensure that the learning
model complies with these constraints [44]. To achieve this,
we introduce a hybrid penalty mechanism within the reward
system, which penalizes the rewards in cases where the
constraints are not met. This strategy guides MDRL in the
right direction [41], [45]. Consequently, the reward function
is thoughtfully formulated as follows:
r =ξ0EE +ξ1
J∑
j=1
(ϵ0−ϵBeam(Rj))+ξ2
J∑
j=1
(
df−
C∑
c=1
Oj,c
)
+ξ3
C∑
c=1

dv−
J∑
j=1
Oj,c

 +ξ4
U∑
u=1
(
D−
C∑
c=1
ϖcu
)
+
ξ5

P max−
J∑
j=1
U∑
u=1
‖wj,u‖2


+ξ6
U∑
u=1
( C∑
c=1
log2 (1 + Υu,c)−Rth
)
, (16)
R =
{
r, if constraints (13g)-(13i) are satisﬁed ,
−|r|, otherwise, (17)
Constructing a proper reward function is crucial in the learning
process, as previously mentioned. The proposed OP (13)
entails several constraints, all of which should be incorporated
into the reward function. Due to the presence of multiple
constraints, it becomes necessary to deﬁne a hybrid reward
function to ensure that our proposed MDRL satisﬁes these
constraints. In (16), the reward function r is deﬁned as a
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10542 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
weighted summation of the objective function and constraints
(13a)–(13f) of the proposed OP. Additionally, equation (17)
addresses the satisfaction of constraints (13g)–(13i), where if
the mentioned constraints are satisﬁed, the reward equals r,
and vice versa.
Given the disparate units associated with seven components
in (16), normalization procedures become necessary, facil-
itated by the introduction of weighting factors denoted as
ξi ∈ [0, 1], ∀i∈{ 0,... 6}. Importantly, the sum of these
weighting factors is constrained to equal one ( ∑6i=0ξi = 1)
[43].
Moreover, given the presence of continuous optimization
variables within action space A, as deﬁned in equation (15),
DDPG proves to be a suitable choice for addressing problem
(13). However, it’s worth noting that the model learned by
DDPG may exhibit limited adaptability to new environments.
To enhance DDPG’s ability to generalize, we introduce a novel
approach by combining DDPG with meta-learning, resulting
in the proposal of Meta-DDPG as a solution for problem (13).
DDPG utilizes an actor network parameterized
by θa(s| ∆θa) and a critic network represented as
Qc(s,a| ∆Qc) with corresponding parameters denoted by
∆θa and ∆Qc. Additionally, to enhance the stability of
the DDPG algorithm, it incorporates target actor and critic
networks, namely θa′θa′ and Qc′Qc′ , where the parameters
are symbolized as ¯∆θa and ¯∆Qc.
Within the framework of DDPG, the selection of actions at
each state relies on a policy that maps states to a probability
distribution over available actions. In the context of this deter-
ministic target policy, denoted as θa, the state-value function
is referenced in [40].
Qθa (st,at)
= Ert,st+1∼E
[
r (st,at) +νQθa (st+1,θa (st+1))], (18)
Here, the discount factor is denoted asν, and it falls within the
range of values from 0 to 1, excluding 1. The term r (st,at)
represents an immediate reward associated with the state-
action pair at time t.
Furthermore, the objective of the critic network is
to minimize the subsequent loss function L
(
∆Qc) =
E
[(
Q
(
st,at| ∆Qc)−ιt)2], where ιt = r (st,at) +
νQ
(
st+1,θa (st+1)| ∆Qc) [40]. Similarly, the actor network
minimizes the following loss function:
L(∆θa) =E[Qθa(st,at)|a =θa(st; ¯∆θa)]. (19)
Using DDPG, the agent selects an action, at ∈ A, from
a state, st, in the environment, denoted as S. After execut-
ing action at in the environment, the agent transitions to
a new state, st+1, and receives an immediate reward, rt.
These state transitions generate experience tuples of the form
(st,at,st+1,rt), which are stored in a replay buffer, denoted
asD.
This interaction results in a sequence of experiences,
s0,a 0,r 1,s 1,a 1,r 2,... . The policy responsible for mapping
states to actions is represented as π, which can be determin-
istic or stochastic. In the context of high-dimensional state
spaces and continuous action spaces, the DDPG algorithm is
employed. In DDPG, the primary objective is to discover the
optimal policy, denoted as π∗, that maximizes the cumulative
reward function.
By considering the target Q value computed by the critic
target network, the chain rule is applied to (18) to derive the
actor network parameters ∇∆θaL, as shown in (20), shown
at the bottom of the next page. This expression represents
the policy gradient, as introduced in [40]. In this context, β
represents the behavior policy of the agent.
To improve the adaptability of learning models using meta-
learning, a method called Meta-DDPG method was introduced
in [41]. According to [41], meta-learning can be formulated
as a bi-level OP, as follows:
τ = arg min
τ
Lmeta
(
dval ; ∆θa∗),
s.t. ∆θa∗ = arg min
∆θa
(
L
(
dtrn; ∆θa)
+Lmeta-criticτ
(
dtrn; ∆θa)), (21)
At the higher level, meta-critic learning is employed, while the
lower level encompasses classic critic learning. The primary
objective of meta-learning in (21) is to enhance the perfor-
mance of DDPG by introducing an additional loss function
Lmeta-criticτ for updating the actor network’s parameters. Specif-
ically, unlike DDPG, where the actor network’s parameters
are updated solely by minimizing L(∆θa) in (19), in meta-
learning (as in (21)), the actor network is trained using both
L(∆θa) and Lmeta-criticτ through stochastic gradient descent.
Furthermore, dtrn and dval refer to distinct sets of transition
batches randomly sampled from the replay buffer.
In (21), the meta-critic parameter τ is optimized through
meta-learning to expedite the learning progress of the actor
network. The loss function for meta-learning in (21) is deﬁned
as:
Lmeta = tanh
(
L
(
dval; ∆θanew)−L(dval; ∆θaold)) (22)
Here, ∆θaold and ∆θanew are updated as follows:
∆θaold = ∆θa−ϵ∇∆θaL(∆θa), (23)
∆θanew = ∆θaold−ϵ∇∆θaLmeta-criticτ (∆θa). (24)
Furthermore, the parameters of the actor network undergo
updates as follows:
∆θa← ∆θa−ϵ(∇∆θaL(∆θa) +∇∆θaLmeta-criticτ (∆θa)).
(25)
Also, the meta-critic parameters are adjusted by the rule:
τ←τ−ϵ∇τLmeta. (26)
The suggested Meta-DDPG method is described compre-
hensively in Algorithm 1.
A. Time Complexity Analysis of Meta-DDPG: As stated in
[54], the analysis of the time complexity for Meta-DDPG can
be approached by considering the ﬂoating point operations
per second (FLOPS) involved in each hidden layer of the
actor, critic, and actor-critic networks. For instance, within
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10543
Fig. 3. Convergence of Meta-DDPG in terms of (a) reward, (b) energy efﬁciency, (c) total sum rate, and (d) total consumed power with different learning
rates for actor and critic networks.
TABLE II
SIMULATION PARAMETERS
the actor network, each hidden layer incorporates a vector
µa,𝓁 and a matrix of size µa,𝓁×µa,𝓁+1 for conducting dot
product operations. The FLOPS computation in this context
can be represented as (2µa,𝓁− 1)×µa,𝓁+1, which includesµa,𝓁
times multiplications and µa,𝓁− 1times additions. Moreover,
it is essential to consider the time complexity of the activation
layer, encompassing various operations such as addition, sub-
traction, multiplication, division, exponentiation, square root,
and others. Consequently, the time complexity of the actor
network is expressed as:
Ca = 2
S−1∑
𝓁=0
((2µa,𝓁− 1)µa,𝓁+1 +κaµa,𝓁+1) (27)
Here, κa denotes the parameter associated with the
activation layer. Following a similar methodology, we
can derive the corresponding time complexities for
the critic and actor-critic networks. As a result, the
comprehensive time complexity of Meta-DDPG can be
deﬁned as Ct =O
(∑S−1
𝓁=0 µa,𝓁µa,𝓁+1 +∑R−1b=0 µc,bµc,b+1+
1
2
∑Y−1
e=0 µm−c,eµm−c,e+1
)
.
V. S IMULATION RESULTS
In this section, we evaluate the effectiveness of the pro-
posed system model across various system model parameters,
algorithms, and multiple access methods. The simulation
parameters and hyperparameters for Meta-DDPG are provided
in Table II unless otherwise speciﬁed. We utilized PyTorch
version 1.4.0 for the implementation of Meta-DDPG and
DDPG algorithms. MATLAB 2021a was used for the convex
optimization benchmark. These computations were conducted
on a MacBook Air (2020) with speciﬁc CPU and GPU
conﬁgurations.
To demonstrate the effective performance of the proposed
MDRL method across various system model parameters,
algorithms, and MA techniques [12], deterministic channel
coefﬁcients are assumed [42]. Simulations of our STAR-IRS-
Aided SCMA ISAC system model were conducted, varying
MDRL method parameters as shown in Fig. (3). Since our
MDRL is constructed from several neural networks, the learn-
ing rate parameters of the actor and critic networks should be
suitable for this MDRL. Learning rate parameters signiﬁcantly
inﬂuence the performance of neural networks in MDRL; our
simulations indicate optimal performance with a learning rate
of 0.001 for both actor and critic networks (Fig. (3a)). This
learning rate choice also maximizes energy efﬁciency (Fig.
(3b)) and total sum rate (Fig. (3c)), while decreasing total
power consumption over episodes (Fig. (3d)), demonstrating
the effectiveness of our proposed MDRL approach for opti-
mizing overall performance metrics. It should be noted that
setting the learning rate close to 1 in machine learning is
generally not recommended, as it can lead to unstable training
and poor convergence. A high learning rate like this may
cause the model to overshoot optimal values during training
(as illustrated in our simulations). In our simulations, we
tuned the learning rate to 0.001 for our proposed Meta-based
approach. The ﬁgure is intended to illustrate the impact of
hyperparameter tuning on our proposed solution.
In Fig. (4), we simulated our STAR-IRS-Aided SCMA
ISAC system model, considering various multiple access
methods. As depicted in these ﬁgures, SCMA is compared
with NOMA and OFDMA. Since our proposed system model
employs SCMA as the multiple-access method, this ﬁg-
ure compares its performance with other multiple-access
∇∆θaL≈ Est∼ρβ

∇aQ
(
s,a| ∆Qc) st=st
a/∈θa(st)
∇∆θaθa
(
s| ∆θa)
⏐⏐⏐⏐⏐⏐
s=st

, (20)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10544 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
Fig. 4. Convergence of Meta-DDPG in terms of (a) reward, (b) energy efﬁciency, (c) total sum rate, and (d) total consumed power for different MA methods.
Algorithm 1 The Proposed Meta-DDPG Algorithm
Input: Maximum number of episodes E, maximum number
of time steps T , and N.
Initialize replay buffer D
Initialize the critic and actor networks, ∆Qc and ∆θa
Initialize the target critic and the target actor networks
¯∆Qc and ¯∆θa with parameters of ¯∆Qc ← ∆Qc and
¯∆θa← ∆θa
for each episode e = 1, ··· , E
Reset the environment to get the initial state s0
for each time step t = 1, ··· , T
Select action at
Execute action at on the environment and receive reward
rt
The network transits from state st to st+1
Transition (st,at,st+1,rt) is stored in D
for each gradient descent step to solve problem (21)
A random batch is sampled from D.
∆Qc← ∆Qc−ϵ∇L(∆Qc)
∆θaold← ∆θa−ϵ∇L(∆θa)
∆θanew← ∆θaold−ϵ∇Lmeta-criticτ (∆θa)
A random batch is sampled from D.
∆θa← ∆θanew
τ←τ−ϵ∇τ
(
tanh
(
L(∆θanew)−L (∆θaold)))
if mod (t,N ) = 0:
¯∆Qct+1←ρ∆Qct + (1−ρ) ¯∆Qct ,¯∆θat+1←ρ∆θat + (1−ρ) ¯∆θat
techniques. To simulate NOMA and OFDMA, all parameters
for our proposed system model on the STAR-IRS-Aided
SCMA ISAC system are utilized in the NOMA-based
and OFDMA-based STAR-IRS-Aided ISAC system models.
Fig. (4a) presents the smoothed rewards of the deﬁned envi-
ronment in the suggested meta-learning approach. From the
ﬁgure, it can be inferred that SCMA yields better rewards com-
pared to other MA methods. Additionally, in the mentioned
ﬁgure, we observe that due to SCMA’s higher complexity
compared to NOMA and OFDMA, it converges after more
episodes. However, all benchmarks converged in fewer than
1000 episodes. EE versus episodes were plotted in Fig. (4b).
As anticipated from the reward ﬁgure, SCMA exhibits the
best performance and converges to higher EE in contrast to
NOMA and OFDMA. It is worth mentioning that NOMA
achieves better EE compared to OFDMA. In Fig. (4c), the
plot illustrates the progression of the total sum rate over
episodes. As expected from the reward ﬁgure analysis, SCMA
demonstrates superior performance, converging to a higher
total sum rate when compared to NOMA and OFDMA. It’s
noteworthy to point out that, in the comparison between
NOMA and OFDMA, NOMA demonstrates a higher total
sum rate. Finally, in Fig. (4d), we provide a ﬁgure indicating
the learning rate for the total power consumption. In the
ﬁgure, total power consumption decreases as the number
of episodes increases. By considering the objective function
presented in OP (13), EE can be calculated by dividing the
total sum rate by the total consumed power. To enhance the
EE over different episodes, our MDRL learns to improve its
experiences across episodes, aiming to increase the total sum
rate while decreasing total consumed power.
Our system model comprises several parameters that need
to be conﬁgured according to the system’s conditions. One of
the critical parameters in our proposed system model is P max,
as mentioned in Section III. P max represents the maximum
available power at the ISAC BS. To investigate the effect of
P max in our suggested system model, we provide Fig. (5).
The ﬁgures are obtained for P max values of 5, 10, 30, and 50
Watts. For instance, Fig. (5a) illustrates rewards for different
power levels. As shown, increasing the available power at
the ISAC BS improves the reward of the MDRL. In this
plot, P max = 50 Watts exhibits the highest reward compared
to other scenarios. The EE versus episodes are depicted in
Fig. (5b). Furthermore, the mentioned ﬁgure also demonstrates
the convergence of our proposed system model with different
P max levels. The investigation of EE over episodes is shown
in Fig. (5b). The same explanations apply to these ﬁgures as
those mentioned for the reward ﬁgure. As noted for the reward,
P max = 50 Watts exhibits the best EE, while P max = 5
Watts has the lowest. Additionally, Fig. (5c) illustrates the
total sum rate concerning episodes. In contrast to the reward
ﬁgure, in this graph, the smoothed total sum rate for both
P max = 50 Watts and P max = 30 Watts is almost the
same. As we know, when power increases, the total sum
rate enhances, and after a speciﬁc power level, our proposed
system model saturates in data rate, and the total sum rate
stabilizes. Another reason for this behavior is related to the
reward function that we have deﬁned in section IV-.3. As
mentioned, our proposed reward is calculated based on the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10545
Fig. 5. The learning curve of Meta-DDPG is analyzed in terms of (a) reward, (b) energy efﬁciency, (c) total sum rate, and (d) total consumed power for
different P max levels.
Fig. 6. The learning curve of Meta-DDPG is analyzed in terms of (a) reward, (b) energy efﬁciency, (c) total sum rate, and (d) total consumed power for
Meta-DDPG, DDPG, PPO,SAC, TD3, uniform beamforming, random beamforming, and Q-learning.
suggested reward function. Therefore, the suggested MDRL
learns to improve EE by satisfying constraints. Hence, based
on these reasons, we can observe equality in the total sum
rate for the mentioned benchmarks. Furthermore, P max = 5
Watts exhibits the lowest total sum rate. Lastly, Fig. (5d)
illustrates the learning curve for total power consumption. By
employing the mathematical framework outlined in OP (13),
we derive the EE metric by dividing the total sum rate by the
aggregate power consumption. Our MDRL methodology aims
to enhance EE iteratively by improving performance across
multiple trials. The objective is to increase the total sum rate
while simultaneously reducing overall power consumption.
Based on the reasons mentioned in section I for utilizing
MDRL to solve our proposed OP, in this simulation section, we
illustrate the efﬁciency of our suggested algorithm in solving
the resource allocation problem investigated in this paper.
Therefore, in Fig. (6), various algorithms were applied to solve
the OP deﬁned in section III. The comparison is between our
proposed MDRL, PPO, TD3, SAC, DDPG, uniform beam-
forming, random beamforming, and Q-learning for codebook
assignment and user association. It is necessary to mention that
all system model parameters are the same in all scenarios. For
the uniform beamforming benchmark, we only apply uniform
beamforming for the beamforming, while the other parts of
the investigated (13) are solved with MDRL. Similarly, the
same strategy is used for the random beamforming benchmark.
As you know, Q-learning is a discrete RL algorithm typically
used to solve problems with discrete optimization variables
[55]. In other cases, continuous optimization variables should
be discretized before the algorithm can be applied to the OP.
Consequently, by considering this property, we have utilized
Q-learning to solve (13). In this regard, we divided (13)
into subproblems. One subproblem is to ﬁnd proper values
for beamforming, phase shifts, and amplitude coefﬁcients of
STAR-IRS. Another subproblem is codebook allocation and
subcarrier assignment, which can be solved with Q-learning.
In this benchmark, we present a hybrid RL algorithm like [56]
to solve (13), consisting of one step of MDRL and another
step of Q-learning. The proposed hybrid algorithm converges
over episodes. Fig. (6a) indicates the reward over episodes for
different benchmarks. It is clear that our proposed solution has
the best performance and achieves better rewards compared to
other benchmarks. As indicated, MDRL improves PPO, SAC,
TD3, and DDPG algorithms. For instance it improves reward
by 100 percent the DDPG algorithm reward. Additionally,
uniform beamforming achieves more reward compared to
random beamforming. However, the hybrid algorithm that uses
Q-learning for codebook allocation and subcarrier assignment
has the lowest reward. In Fig. (6b), a comparison plot shows
EE in terms of episodes for various benchmarks. Hence, in
this ﬁgure, our proposed MDRL enhances EE by 123 percent
compared to DDPG and uniform beamforming. The proposed
solution improves EE by 90 percent compared to SAC and
by 100 percent compared to TD3. It is noteworthy that PPO
has a stability problem, as indicated in [57]. Additionally, this
algorithm cannot be selected as a solution in this paper due
to its instability and the need for more episodes to achieve
convergence. TD3 performs better compared to PPO and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10546 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
Fig. 7. Comparison of Time Complexity between Meta-DDPG and DDPG.
Fig. 8. MDRL versus convex optimization benchmark for D and numbers of
users.
DDPG, as expected [58]. Due to its meta-learning structure, it
has the ability to “learn to learn,” meaning that our proposed
solution can effectively adapt the DRL-based approach to the
model in the best possible way. Consequently, we observe that
it provides a better response compared to other actor-critic-
based solutions. As illustrated, the DDPG benchmark and
uniform beamforming with MDRL approximately converges to
the same value of EE. On the other hand, random beamforming
and Q-learning for codebook allocation and subcarrier assign-
ment have the worst EE. Fig. (6c) shows the total sum rate
versus episodes. In this plot, we can observe that the total sum
rate for the proposed solution and the uniform beamforming
benchmark are near each other. This behavior can also be
attributed to the reward function outlined in Section IV-.3.
As previously stated, our proposed reward is derived from
this function. Consequently, the suggested MDRL algorithm
is designed to enhance EE by adhering to the mentioned
constraints. Then, converging to an equal rate can be related
to the mentioned reason. Furthermore, in the mentioned plot,
the Q-learning benchmark has the worst performance. Finally,
Fig. (6d) indicates the total consumed power over episodes.
The time complexity analysis is provided in Fig. 7. In this
ﬁgure, the time complexity of the Meta-DDPG and DDPG
algorithms are illustrated for U = 2,C = 6,J = 4,NBS =
5, and NS = 4 . The time complexity of the Meta-DDPG
algorithm is O(484750) and for DDPG is O(464700). By
comparing the calculated complexity for these algorithms, we
can understand that Meta-DDPG has more time complexity
compared to DDPG, as we expected. As presented in Fig. 7,
Meta-DDPG has about 4% more complexity compared to
DDPG. Considering the results obtained in this paper, Meta-
DDPG not only has a better response but also has 4% higher
complexity compared to DDPG. Therefore, we can infer
that Meta-DDPG is better compared to DDPG due to its
performance and its time complexity.
Fig. 9. Comparison of MDRL and convex optimization benchmarks for
numbers of users and D.
Furthermore, the convex analysis is presented in Fig. 8 and
Fig. 9 in comparison with MDRL. As mentioned in section
III, the OP in (13) involves mixed binary and continuous
optimization variables, as well as non-convex, nonlinear con-
straints and objective functions. Such problems fall under the
category of MINLP, a class of NP-hard problems that cannot
be solved using conventional methods. Then we employed
several advanced optimization techniques, including alter-
native optimization (AO), Dinkelbach algorithm, fractional
programming, and the difference of two Concave functions
(DC) approximation, to transform the original OP in (13)
into a convex one. At ﬁrst, to obtain a convex format for
the proposed OP, we divided it into three subproblems [12],
[13], [39], [59]. The ﬁrst subproblem is the joint codebook
allocation and subcarrier assignment. By deﬁning a new
variable for codebook allocation and subcarrier assignment,
we can jointly solve it using Dinkelbach’s Transform and
fractional programming [12], [13], [39], [59]. The second
subproblem is the STAR-IRS parameter OP. As mentioned
earlier, we have two types of variables at this stage. Similar to
the previous subproblem, we converted the OP into a convex
format by jointly optimizing the phase shift and amplitude
parameters of STAR-IRS using the mentioned transformation
and multidimensional fractional programming. The third and
ﬁnal subproblem is the beamforming OP. To transform this OP
into a convex structure, we utilized Dinkelbach’s Transform
and multidimensional fractional programming. Based on these
steps, we converted the complex problem, as explained in
section III, into a convex format. Problem (13) can be solved
by iteratively solving the three subproblems using CVX [12],
[13], [39], [59]. As a result, the MDRL-based algorithm
is expected to be more effective compared to the convex
optimization approach in this problem due to the mentioned
procedure. Because our proposed MDRL solution addresses
the problem jointly by learning how to choose actions for dif-
ferent states to maximize its cumulative rewards. From convex
optimization literature, such as [39], we know that NP-hard
problems can be addressed using approximation and relaxation
techniques, as previously mentioned. Therefore, to solve the
NP-hard optimization problem (OP), we applied relaxation
through decomposition, approximation, and iterative methods,
which ultimately led to sub-optimal solutions. For instance,
in the ﬁrst subproblem—joint codebook allocation and sub-
carrier assignment—we introduce an outer loop to relax the
subproblem using Dinkelbach’s transformation. Additionally,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10547
Fig. 10. Running time analysis of the proposed MDRL and the convex
optimization benchmark.
we incorporate an inner loop to apply fractional programming.
Each of these loops requires a predeﬁned number of iterations
or a convergence condition. Furthermore, the three subprob-
lems must be solved iteratively until overall convergence is
achieved. Due to limited computational resources and time
constraints, we must carefully balance speed, resource utiliza-
tion, and accuracy. In each subproblem, we face the same
iterative trade-off. As highlighted in [39], the complexity of the
optimization problem increases due to its non-convexity, push-
ing the solution further away from optimality. Consequently, in
this scenario, similar results to those obtained through convex
optimization techniques can be expected. On the other hand,
DRL-based methods have demonstrated their effectiveness
in recent years. In the proposed solution, the OP is solved
jointly without requiring any relaxations or approximations.
Also, by deﬁning an effective learning strategy and ﬁne-
tuning learning parameters optimally, we can signiﬁcantly
improve the outcome. Therefore, in this paper, utilizing meta-
DRL leads to better performance compared to the convex
optimization benchmark.
In Fig. 8, we plotted a comparison between the MDRL and
convex optimization benchmark for different values of D and
multiple users. Based on the simulation results, the proposed
MDRL outperforms the convex optimization benchmark. The
OP, when solved with the convex optimization benchmark,
involves several iterative steps. Consequently, the obtained
results are suboptimal due to various levels of approximation.
As we know from convex optimization theory, subdivision
and approximation lead to suboptimal solutions, and iteratively
applying these steps makes the responses progressively worse
[39]. This ﬁgure also illustrates the contrast between different
numbers of users. The ﬁgure was obtained for J = 6 and
C = 15 . To show the effect of the number of users on our
system model and to compare the MDRL with the convex
optimization benchmark, we provided Fig. 9 for various num-
bers of users and different D values for J = 6 and C = 15.
The simulation results indicate that the proposed MDRL con-
sistently outperforms the convex optimization benchmark. The
same analysis applies to this ﬁgure as mentioned for Fig. 8.
The proposed MDRL method outperforms the convex opti-
mization benchmark, completing tasks in 1502.36 seconds
versus 3969.63 seconds, demonstrating its efﬁciency and suit-
ability for real-time and complex applications as shown in
Fig (10). This running times were obtained on same device
for Ut = 1, Ur = 1, C = 6, and J = 4.
To investigate more realistic scenario coupled phase-shift
model is consided in this section. the proposed system model
in section II is for a general case of using STAR-IRS with inde-
pendently adjustment phase-shift coefﬁcients for transmission
and reﬂection. This necessitates that the associated electric and
magnetic impedances can take on arbitrary values. However,
for purely passive STAR-RISs, this condition may not be
feasible, as the realizable electric and magnetic impedances
are restricted to purely imaginary numbers [29]. As a result,
the phase-shift coefﬁcients for transmission and reﬂection
become interdependent. This interdependence not only leads
to performance degradation but also complicates the design
of transmission and reﬂection coefﬁcients/beamforming. Then,
to convert the proposed OP (13) for the coupled phase-shift
scenario, we add
⏐⏐θRλn −θTλn ⏐⏐ = 12πor 32π as a constraint
to our investigated optimization problem. Hence, the new
optimization problem is expressed as follows:
P2 : max
{ϖcu},{Oj,c},{Wj},∆EE,
s.t. C10 :
⏐⏐θRλn −θTλn ⏐⏐ = 12π or 32π, (28a)
(C1) − (C9)
Then, (28) can be solved using the suggested method in
this paper. The simulation results for the coupled phase-
shift scenario are plotted in Fig. 11. Due to the complexity
of the constraint (28a) added to the OP, more episodes are
required for convergence, as illustrated in the ﬁgure. Under
equivalent conditions, we observe that the coupled phase-shift
scenario converges in more episodes. Moreover, the perfor-
mance of the coupled phase-shift STAR-IRS is better than the
conventional STAR-IRS, and their results are very close to
each other. However, as mentioned earlier, the coupled phase-
shift STAR-IRS introduces greater implementation complexity
[29]. Additionally, the learning curves for reward, EE, total
sum rate, and consumed power are provided in Fig. 11. It is
important to note that, based on our deﬁned reward function,
the meta-model learns to select the appropriate action for the
current state. As a result, we can observe the impact of the
chosen actions in each episode by analyzing the learning curve.
In real-world conditions, perfect CSI is generally not avail-
able. Therefore, we consider imperfect CSI for the channel
between the STAR-IRS and the users. This channel can
be modeled using the Gaussian error model to account for
imperfect CSI [33]. In this case, we have:
GSU′j = GSUj + ∆GSUj
where ∆GSUj ∼ CN(0,σ SUj 2) represents the estimation
error. The impact of imperfect CSI and perfect CSI is illus-
trated in Fig. 11 for both the STAR-IRS and conventional
IRS systems. As shown, the performance with imperfect CSI
is lower compared to that with perfect CSI. This is because
imperfect CSI introduces greater channel uncertainty. The
ﬁgure also demonstrates the effect of using STAR-IRS. The
results are consistent with our earlier discussions, particularly
in the introduction section, where we highlighted the unique
capability of STAR-IRS to serve users in both reﬂection and
transmission zones. In contrast, conventional IRS can only
provide service to users in the reﬂection zone. As a result,
users behind the IRS cannot beneﬁt from it to improve their
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10548 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
Fig. 11. The learning curve of Meta-DDPG is analyzed in terms of (a) reward, (b) energy efﬁciency, (c) total sum rate, and (d) total consumed power to
investigate the impact of using perfect and imperfect CSI, as well as comparing STAR-IRS with conventional IRS and coupled phase-shift STAR-IRS.
communication quality. In our proposed system model, the EE
is lower when users are in the transmission zone compared to
the system model that includes STAR-IRS.
VI. C ONCLUSION
In this paper, we investigate joint beamforming and resource
allocation in a STAR-IRS SCMA-based ISAC system using
an MDRL approach in the THz band. Our objective is to
maximize EE by considering ISAC, SCMA, the maximum
available power at the ISAC BS, QoS for each user, and
constraints on the amplitude coefﬁcient and phase shift of
STAR-IRS. The problem formulation falls under the cate-
gory of NP-hard problems, which are challenging to solve
using formal methods. Therefore, we employ a novel MDRL
algorithm to address this problem. Our simulation results
demonstrate the advantages of our proposed system model
over various system parameters, MDRL conﬁgurations, MA
methods, and optimization algorithm benchmarks. We show
that our proposed system model outperforms NOMA and
OFDMA systems, achieving the highest performance and
it enhanced EE by 15 percent in comparison to NOMA.
Furthermore, our MDRL method improves EE by 123 percent
compared to conventional DDPG and PPO algorithms. Also,
the proposed solution shows that it has the capability to
enhance EE 90% in contrast to SAC. Additionally, we investi-
gated solving the OP through a convex optimization approach,
and the results illustrated the superiority of MDRL, showing
a 10% improvement compared to the convex approach. The
impact of imperfect CSI was also investigated in the simulation
results. It was concluded that when CSI is perfect, the system
model achieves a higher reward value. Additionally, the results
indicated that the STAR-IRS outperforms the conventional
IRS. A scenario involving a coupled phase-shift model for
the STAR-IRS was studied, revealing that while the coupled
phase-shift model improves performance, it comes at the cost
of increased complexity.
REFERENCES
[1] C.-X. Wang et al., “On the road to 6G: Visions, requirements, key
technologies and testbeds,” IEEE Commun. Surveys Tuts., vol. 25, no. 2,
pp. 905–974, 2nd Quart., 2023.
[2] K. Meng, C. Masouros, K.-K. Wong, A. P. Petropulu, and L. Hanzo,
“Integrated sensing and communication meets smart propagation engi-
neering: Opportunities and challenges,” 2024, arXiv:2402.18683.
[3] Y . Cui, F. Liu, X. Jing, and J. Mu, “Integrating sensing and communi-
cations for ubiquitous IoT: Applications, trends, and challenges,” IEEE
Netw., vol. 35, no. 5, pp. 158–167, Sep. 2021.
[4] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[5] Y . Zhang, C. You, and B. Zheng, “Multi-active multi-passive (MAMP)-
IRS aided wireless communication: A multi-hop beam routing
design,” IEEE J. Sel. Areas Commun. , vol. 41, no. 8, pp. 2497–2513,
Aug. 2023.
[6] M. Ahmed et al., “A survey on STAR-RIS: Use cases, recent advances,
and future research challenges,” IEEE Internet Things J., vol. 10, no. 16,
pp. 14689–14711, Aug. 2023.
[7] X. Mu, Y . Liu, L. Guo, J. Lin, and R. Schober, “Simultaneously
transmitting and reﬂecting (STAR) RIS aided wireless communications,”
IEEE Trans. Wireless Commun. , vol. 21, no. 5, pp. 3083–3098, May
2021.
[8] W. Abdul et al., “A survey on STAR-RIS: Use cases, recent advances,
and future research challenges,” 2023, arXiv.
[9] J. Xu, Y . Liu, X. Mu, and O. A. Dobre, “STAR-RISs:
Simultaneous transmitting and reﬂecting reconﬁgurable intelligent
surfaces,” IEEE Commun. Lett. , vol. 25, no. 9, pp. 3134–3138,
Sep. 2021.
[10] Y . Liu et al., “STAR: Simultaneous transmission and reﬂection for
360 coverage by intelligent surfaces,” IEEE Wireless Commun., vol. 28,
no. 6, pp. 102–109, Dec. 2021.
[11] S. Sharma, K. Deka, Y . Hong, and D. Dixit, “Intelligent reﬂecting
surface-assisted uplink SCMA system,” IEEE Commun. Lett. , vol. 25,
no. 8, pp. 2728–2732, Aug. 2021.
[12] A. Farhadi Zavleh and H. Bakhshi, “Resource allocation in sparse code
multiple access-based systems for cloud-radio access network in 5G
networks,” Trans. Emerg. Telecommun. Technol., vol. 32, no. 1, p. 4153,
Jan. 2021.
[13] A. F. Zavleh and H. Bakhshi, “Downlink resource allocation to total
system transmit power minimization in SCMA-based systems for cloud-
RAN in 5G networks,” Telecommun. Syst., vol. 81, no. 4, pp. 575–590,
Dec. 2022.
[14] X. Mu, Z. Wang, and Y . Liu, “NOMA for integrating
sensing and communications towards 6G: A multiple access
perspective,” IEEE Wireless Commun. , vol. 31, no. 3, pp. 316–323,
Jun. 2023.
[15] Q. Luo, Z. Liu, G. Chen, P. Xiao, Y . Ma, and A. Maaref, “A design
of low-projection SCMA codebooks for ultra-low decoding complexity
in downlink IoT networks,” IEEE Trans. Wireless Commun. , vol. 22,
no. 10, pp. 6608–6623, Oct. 2023.
[16] H. Wen, W. Yuan, Z. Liu, and S. Li, “OTFS-SCMA: A downlink
NOMA scheme for massive connectivity in high mobility channels,”
IEEE Trans. Wireless Commun. , vol. 22, no. 9, pp. 5770–5784,
Sep. 2023.
[17] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. Eldar,
“Joint transmit beamforming for multiuser MIMO communications and
MIMO radar,” IEEE Trans. Signal Process. , vol. 68, pp. 3929–3944,
Jun. 2020.
[18] N. C. Luong, X. Lu, D. T. Hoang, D. Niyato, and D. I. Kim, “Radio
resource management in joint radar and communication: A comprehen-
sive survey,” IEEE Commun. Surveys Tuts., vol. 23, no. 2, pp. 780–814,
2nd Quart., 2021.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

FARHADI et al.: JOINT BEAMFORMING AND RESOURCE ALLOCATION FOR STAR-IRS-AIDED SCMA ISAC SYSTEMS 10549
[19] O. Li et al., “Integrated sensing and communication in 6G a prototype
of high resolution THz sensing on portable device,” in Proc. Joint
Eur. Conf. Netw. Commun. 6G Summit (EuCNC/6G Summit), Jun. 2021,
pp. 544–549.
[20] L. Sun, Z. Zhao, S. Wang, Z. Ding, and M. Peng, “On the study
of non-orthogonal multiple access (NOMA)-assisted integrated sensing
and communication (ISAC),” IEEE Trans. Commun. , vol. 72, no. 11,
pp. 7278–7293, Nov. 2024.
[21] B. Liao, H. Q. Ngo, M. Matthaiou, and P. J. Smith, “Power allocation
for massive MIMO-ISAC systems,” IEEE Trans. Wireless Commun. ,
vol. 23, no. 10, pp. 14232–14248, Oct. 2024.
[22] D. Xu, X. Yu, D. W. K. Ng, A. Schmeink, and R. Schober, “Robust
and secure resource allocation for ISAC systems: A novel optimiza-
tion framework for variable-length snapshots,” IEEE Trans. Commun. ,
vol. 70, no. 12, pp. 8196–8214, Dec. 2022.
[23] H. Yang et al., “Dynamic power allocation for integrated
sensing and communication-enabled vehicular networks,” IEEE
Trans. Wireless Commun. , vol. 23, no. 9, pp. 12313–12330,
Sep. 2024.
[24] J. Zuo, Y . Liu, Z. Ding, L. Song, and H. V . Poor, “Joint design for
simultaneously transmitting and reﬂecting (STAR) RIS assisted NOMA
systems,” IEEE Trans. Wireless Commun., vol. 22, no. 1, pp. 611–626,
Jan. 2023.
[25] Q. Wu and R. Zhang, “Intelligent reﬂecting surface enhanced
wireless network via joint active and passive beamforming,”
IEEE Trans. Wireless Commun. , vol. 18, no. 11, pp. 5394–5409,
Nov. 2019.
[26] C. Huang, G. C. Alexandropoulos, A. Zappone, M. Debbah, and
C. Yuen, “Energy efﬁcient multi-user MISO communication using
low resolution large intelligent surfaces,” in Proc. IEEE Globecom
Workshops (GC Wkshps), Dec. 2018, pp. 1–6.
[27] B. Zheng, C. You, and R. Zhang, “Double-IRS assisted multi-user
MIMO: Cooperative passive beamforming design,”IEEE Trans. Wireless
Commun., vol. 20, no. 7, pp. 4513–4526, Jul. 2021.
[28] Y . Zhao, B. Clerckx, and Z. Feng, “IRS-aided SWIPT: Joint wave-
form, active and passive beamforming design under nonlinear harvester
model,” IEEE Trans. Commun. , vol. 70, no. 2, pp. 1345–1359, Feb.
2022.
[29] Y . Liu, X. Mu, R. Schober, and H. V . Poor, “Simultaneously transmitting
and reﬂecting (STAR)-RISs: A coupled phase-shift model,” in Proc.
IEEE Int. Conf. Commun. , May 2022, pp. 2840–2845.
[30] B. Zhao, J. Liu, B. Mao, and S. Li, “Optimal resource allocation
for random multiple access oriented SCMA-V2X networks,”
IEEE Trans. Veh. Technol. , vol. 72, no. 8, pp. 10921–10932,
Aug. 2023.
[31] P. Liu et al., “SCMA-enabled multi-cell edge computing networks:
Design and optimization,” IEEE Trans. Veh. Technol. , vol. 72, no. 6,
pp. 7987–8003, Jun. 2023.
[32] S. Chaturvedi, V . A. Bohara, Z. Liu, and A. Srivastava, “Sum-rate
maximization of IRS-aided SCMA system,” IEEE Trans. Veh. Technol.,
vol. 72, no. 8, pp. 10462–10472, Aug. 2023.
[33] Y . Liu, W. Chen, H. Tang, and K. Wang, “Resource allocation in the RIS
assisted SCMA cellular network coexisting with D2D communications,”
IEEE Access, vol. 11, pp. 39978–39989, 2023.
[34] M. Cheraghy, W. Chen, H. Tang, Q. Wu, and J. Li, “Joint rate and
fairness improvement based on adaptive weighted graph matrix for
uplink SCMA with randomly distributed users,” IEEE Trans. Commun.,
vol. 69, no. 5, pp. 3106–3118, May 2021.
[35] J. Chen, L. Guo, J. Jia, J. Shang, and X. Wang, “Resource allo-
cation for IRS assisted SGF NOMA transmission: A MADRL
approach,” IEEE J. Sel. Areas Commun., vol. 40, no. 4, pp. 1302–1316,
Apr. 2022.
[36] L. Chai, L. Bai, T. Bai, J. Choi, and W. Zhang, “RIS-aided SCMA-based
SWIPT systems: Design and optimization,” IEEE Trans. Veh. Technol.,
vol. 72, no. 5, pp. 6238–6252, May 2023.
[37] H. M. Kim, H. V . Nguyen, G.-M. Kang, Y . Shin, and O.-
S. Shin, “SWIPT-aided device-to-device communications for massive
IoT networks: A novel resource allocation with sparse code multiple
access,” IEEE Internet Things J. , vol. 10, no. 22, pp. 19617–19629,
Nov. 2023.
[38] Y . Gong, Y . Wei, Z. Feng, F. R. Yu, and Y . Zhang, “Resource
allocation for integrated sensing and communication in digital twin
enabled Internet of Vehicles,” IEEE Trans. Veh. Technol., vol. 72, no. 4,
pp. 4510–4524, Apr. 2023.
[39] S. P. Boyd and L. Vandenberghe, Convex Optimization . Cambridge,
U.K.: Cambridge Univ. Press, 2004.
[40] Y . Yu, J. Tang, J. Huang, X. Zhang, D. K. C. So, and K.-K. Wong,
“Multi-objective optimization for UA V-assisted wireless powered IoT
networks based on extended DDPG algorithm,” IEEE Trans. Commun.,
vol. 69, no. 9, pp. 6361–6374, Sep. 2021.
[41] A. Farhadi, R. Hatami, M. Robat Mili, C. Masouros, and M. Ben-
nis, “A meta-learning approach for energy-efﬁcient resource allo-
cation and antenna selection in STAR-BD-RIS aided wireless
networks,” IEEE Wireless Commun. Lett., vol. 14, no. 5, pp. 1421–1425,
May 2025.
[42] Z. Ding, R. Schober, and H. V . Poor, “No-pain no-gain:
DRL assisted optimization in energy-constrained CR-NOMA
networks,” IEEE Trans. Commun. , vol. 69, no. 9, pp. 5917–5932,
Sep. 2021.
[43] S. Javadi, A. Farhadi, M. Robat Mili, E. Jorswieck, and N. Al-Dhahir,
“Meta-learning for resource allocation in uplink multi-active STAR-RIS-
aided NOMA system,” IEEE Wireless Commun. Lett. , vol. 14, no. 3,
pp. 781–785, Mar. 2025.
[44] H. Zhang, H. Wang, Y . Li, K. Long, and A. Nallanathan,
“DRL-driven dynamic resource allocation for task-oriented semantic
communication,” IEEE Trans. Commun., vol. 71, no. 7, pp. 3992–4004,
Jul. 2023.
[45] A. Farhadi, M. Moomivand, S. K. Taskou, M. R. Mili, M. Rasti,
and E. Hossain, “A meta-DDPG algorithm for energy and
spectral efﬁciency optimization in STAR-RIS-aided SWIPT,”
IEEE Wireless Commun. Lett. , vol. 13, no. 5, pp. 1473–1477,
May 2024.
[46] J. Du, F. R. Yu, G. Lu, J. Wang, J. Jiang, and X. Chu, “MEC-assisted
immersive VR video streaming over terahertz wireless networks: A
deep reinforcement learning approach,” IEEE Internet Things J. , vol. 7,
no. 10, pp. 9517–9529, Oct. 2020.
[47] W. Lu, B. Deng, Q. Fang, X. Wen, and S. Peng, “Intelligent reﬂecting
surface-enhanced target detection in MIMO radar,” IEEE Sensors Lett. ,
vol. 5, no. 2, pp. 1–4, Feb. 2021.
[48] Z.-M. Jiang et al., “Intelligent reﬂecting surface aided dual-function
radar and communication system,” IEEE Syst. J. , vol. 16, no. 1,
pp. 475–486, Mar. 2022.
[49] A. Liu et al., “A survey on fundamental limits of integrated sensing
and communication,” IEEE Commun. Surveys Tuts. , vol. 24, no. 2,
pp. 994–1034, 2nd Quart., 2022.
[50] R. Hoshyar, F. P. Wathan, and R. Tafazolli, “Novel low-density
signature for synchronous CDMA systems over AWGN channel,”
IEEE Trans. Signal Process. , vol. 56, no. 4, pp. 1616–1626,
Apr. 2008.
[51] S. Chaturvedi, Z. Liu, V . Bohara, A. Srivastawa, and P. Xiao, “A tutorial
on decoding techniques of sparse code multiple access,” IEEE Access,
vol. 10, pp. 58503–58524, 2022.
[52] J. Zou, S. Sun, C. Masouros, and Y . Cui, “Sensing-centric energy-
efﬁcient waveform design for integrated sensing and communications,”
in Proc. IEEE Global Telecommun. Conf. (GLOBECOM) , Dec. 2023,
pp. 3105–3110.
[53] X. Hao, P. L. Yeoh, C. She, B. Vucetic, and Y . Li, “Secure deep
reinforcement learning for dynamic resource allocation in wireless MEC
networks,” IEEE Trans. Commun., vol. 72, no. 3, pp. 1414–1427, Mar.
2024.
[54] Q. Wang, A. Gao, and Y . Hu, “Joint power and QoE optimization scheme
for multi-UA V assisted ofﬂoading in mobile computing,” IEEE Access,
vol. 9, pp. 21206–21217, 2021.
[55] T. Zhang, Z. Wang, Y . Liu, W. Xu, and A. Nallanathan,
“Caching placement and resource allocation for cache-enabling UA V
NOMA networks,” IEEE Trans. Veh. Technol. , vol. 69, no. 11,
pp. 12897–12911, Nov. 2020.
[56] W. Wu, F. Yang, F. Zhou, H. Hu, Q. Wu, and R. Qingyang Hu,
“Intelligent resource allocations for IRS-assisted OFDM communica-
tions: A hybrid MDQN-DDPG approach,” 2022, arXiv:2202.05017.
[57] Y . Liu, K. L. Man, G. Li, T. R. Payne, and Y . Yue, “Evaluating
and selecting deep reinforcement learning models for OptimalDy-
namic pricing: A systematic comparison of PPO, DDPG, and SAC,”
in Proc. 8th Int. Conf. Control Eng. Artif. Intell. , Jan. 2024,
pp. 215–219.
[58] S. Liu, “An evaluation of DDPG, TD3, SAC, and PPO: Deep reinforce-
ment learning algorithms for controlling continuous system,” in Proc.
Int. Conf. Data Sci., Adv. Algorithm Intell. Comput. (DAI) , Jan. 2024,
pp. 15–24.
[59] K. Shen and W. Yu, “Fractional programming for communication
systems—Part I: Power control and beamforming,” IEEE
Trans. Signal Process. , vol. 66, no. 10, pp. 2616–2630,
May 2018.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply. 

10550 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 12, DECEMBER 2025
Armin Farhadi received the B.Sc. degree in elec-
trical and telecommunications engineering from the
University of Qom, Iran, in 2017, and the M.Sc.
degree in electrical engineering-telecommunications
systems from Shahed University, Tehran, Iran, in
2019. He is currently pursuing the Ph.D. degree in
electrical engineering-telecommunications systems
with the University of Tehran. He is a Visiting Ph.D.
Student with UCL. His research interests include
machine learning, neural networks, reinforcement
learning, ISAC, IRS, STAR-IRS, convex optimiza-
tion, resource allocation, 6G networks, C-RAN, NOMA, SCMA, and signal
processing. He also serves as a TPC Member for IEEE ICC’25—SAC-13
ISAC Track, EEE ICC’24—SAC-13 ISAC Track, IEEE ICC’25—SAC-
13 ISAC Track (2025 IEEE International Conference on Communications
(ICC): SAC Integrated Sensing and Communication Track), the 2025 5th
International Conference on Computer Application and Information Security
(ICCAIS 2025), the 2025 IEEE 101st Vehicular Technology Conference:
VTC2025-Spring, and the 2024 IEEE 35th Annual International Symposium
on Personal, Indoor, and Mobile Radio Communications (PIMRC).
Ali Olfat (Senior Member, IEEE) received the Ph.D.
degree in electrical engineering from the University
of Tehran, Iran, in 2004. From 2004 to 2005, he
was a Research Associate with Kings College Lon-
don, U.K. He joined the School of Electrical and
Computer Engineering, University of Tehran, as an
Assistant Professor, in 2006. He became an Asso-
ciate Professor in 2013 and a Professor in 2020. He
has been the Director of the Signal Processing and
Communication Systems Laboratory, since 2008. He
was the Director of the Communication Engineering
Department from 2012 to 2014. His research interests include statistical and
adaptive signal processing, array signal processing, information theory, and
learning algorithms for communication systems.
Christos Masouros (Fellow, IEEE) received the
Diploma degree in electrical and computer engi-
neering from the University of Patras, Greece, in
2004, and the M.Sc. by research and Ph.D. degrees
in electrical and electronic engineering from The
University of Manchester, U.K., in 2006 and 2009,
respectively. In 2008, he was a Research Intern with
Philips Research Labs, U.K., working on the LTE
standards. From 2009 to 2010, he was a Research
Associate with The University of Manchester and
a Research Fellow with Queen’s University Belfast
from 2010 to 2012. In 2012, he joined University College London, as a
Lecturer. He has held a Royal Academy of Engineering Research Fellow-
ship from 2011 to 2016. Since 2019, he has been a Full Professor of
signal processing and wireless communications with the Information and
Communication Engineering Research Group, Department of Electrical and
Electronic Engineering, and afﬁliated with the Institute for Communications
and Connected Systems, University College London. From 2018 to 2022,
he was the Project Coordinator of the
 4.2m EU H2020 ITN Project
PAINLESS, involving 12 EU partner universities and industries, toward
energy-autonomous networks. From 2024 to 2028, he will be the Scientiﬁc
Coordinator of the
 2.7m EU H2020 DN Project ISLANDS, involving 19 EU
partner universities and industries, toward next generation vehicular networks.
His research interests include wireless communications and signal processing
with a particular focus on green communications, large scale antenna systems,
integrated sensing and communications, interference mitigation techniques
for MIMO, and multicarrier communications. He is a fellow of the Institute
of Electronic Engineers (IET), the Artiﬁcial Intelligence Industry Alliance
(AIIA), and Asia–Paciﬁc Artiﬁcial Intelligence Association (AAIA). He is
a Founding Member and the Vice-Chair of the IEEE Emerging Technology
Initiative on Integrated Sensing and Communications (SAC), the Chair of
the IEEE SPS ISAC Technical Working Group, and the Chair of the IEEE
Green Communications and Computing Technical Committee, Special Interest
Group on Green ISAC. He is a member of the IEEE Standards Association
Working Group on ISAC Performance Metrics and a Founding Member of
the ETSI ISG on ISAC. He was a recipient of the 2024 IEEE SPS Best Paper
Award, the 2024 IEEE SPS Donald G. Fink Overview Paper Award, and the
2023 IEEE ComSoc Stephen O. Rice Prize, and a co-recipient of the 2021
IEEE SPS Young Author Best Paper Award and a recipient of the Best Paper
Award in the IEEE GlobeCom 2015 and IEEE WCNC 2019 conferences.
He is an IEEE ComSoc Distinguished Lecturer 2024–2025 and his work on
ISAC has been featured in the World Economic Forum’s report on the top
10 emerging technologies. He has been recognized as an Exemplary Editor
of IEEE C OMMUNICATIONS LETTERS and an Exemplary Reviewer of IEEE
TRANSACTIONS ON COMMUNICATIONS . He is the TPC Chair of the IEEE
ICC 2024 Selected Areas in Communications (SAC) Track on ISAC, the
Chair of the IEEE PIMRC2024 Track 1 on PHY and Fundamentals and the
“Integrated Imaging and Communications” stream in IEEE CISA 2024, and
the TPC Co-Chair of IEEE VTC 2025. He is an Area Editor of IEEE T RANS -
ACTIONS ON WIRELESS COMMUNICATIONS and the Editor-at-Large of IEEE
OPEN JOURNAL OF THE COMMUNICATIONS SOCIETY . He has been an Editor
of IEEE T RANSACTIONS ON COMMUNICATIONS , IEEE T RANSACTIONS
ON WIRELESS COMMUNICATIONS , and IEEE O PEN JOURNAL OF SIGNAL
PROCESSING ; an Associate Editor of IEEE C OMMUNICATIONS LETTERS ;
and a Guest Editor of a number of IEEE J OURNAL ON SELECTED TOPICS
IN SIGNAL PROCESSING issues.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:04:36 UTC from IEEE Xplore.  Restrictions apply.