---
type: literature-fulltext
title: "Intelligent Predictive Beamforming for Integrated Sensing, Communication and Power Transfer for Low-Altitude Economy"
zotero_key: "FUQQ4XB5"
pdf_key: "YX9RQ8FY"
doi: "10.1109/TWC.2026.3693103"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Intelligent Predictive Beamforming for Integrated Sensing, Communication and Power Transfer for Low-Altitude Economy.md"
fulltext_path: "03fulltext/备选讲组会论文/FUQQ4XB5.md"
zotero_item: "zotero://select/library/items/FUQQ4XB5"
zotero_pdf: "zotero://open-pdf/library/items/YX9RQ8FY"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Intelligent Predictive Beamforming for Integrated Sensing, Communication and Power Transfer for Low-Altitude Economy

> PDF 原文逐页文本抽取；来源文件 SHA-256：`be37447aa875be49c8fae7fda72a6ac02fb4951d5d4edfff45d19169363215a2`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 17165
Intelligent Predictive Beamforming for Integrated
Sensing, Communication and Power Transfer
for Low-Altitude Economy
Junkai Zhang
 , Member , IEEE, Faheem A. Khan
 , Member , IEEE, Zhiqiang Wei
 , Member , IEEE,
Jiang Xue
 , Senior Member , IEEE, Christos Masouros
 , Fellow, IEEE, Dusit Niyato
 , Fellow, IEEE,
and Zongben Xu
Abstract—This paper investigates intelligent predictive beam-
forming design for simultaneous wireless information and power
transfer-integrated sensing and communication (SWIPT-ISAC)
systems for low-altitude economy wireless networks. Considering
the downlink scenario where the base station aims to localize
the moving targets/communication users and also transfer power
to them, we formulate a weighted sum optimization problem to
balance the trade-off between achievable communication rate and
harvested energy, subject to sensing accuracy constraints deﬁned
by the Cram ´er–Rao lower bound. To address the non-convexity
of the problem, we propose the Time-Spatial Fusion Network
(TSFusionNet), an unsupervised deep learning (DL) framework
that leverages multi-step historical channel state information
for predictive beamforming design. TSFusionNet integrates con-
volutional and recurrent layers with a differential attention
mechanism to capture spatial-temporal dependencies and mit-
igate non-stationary channel dynamics. We introduce a dynamic
penalty-based loss function to enforce sensing constraints during
training. Simulation results show that by adjusting the weight
Received 20 November 2025; revised 22 February 2026; accepted 10 May
2026. Date of current version 20 May 2026. The work of Jiang Xue was
supported in part by the National Key Research and Development Program
of China under Grant 2020YFA0713900, in part by the Fundamental and
Interdisciplinary Disciplines Breakthrough Plan of the Ministry of Education
of China under Grant JYB2025XDXM101, and in part by the National Natural
Science Foundation of China under Grant 62471377. The work of Zhiqiang
Wei was supported in part by the National Key Research and Development
Program of China under Grant 2023YFA1008600 and in part by the Qin
Chuang Yuan High-Level Innovation and Entrepreneurship Talent Program
under Grant QCYRCXM-2023-094. The work of Junkai Zhang was supported
in part by the Fundamental Research Funds for the Central Universities
under Grant xzy012025075. The work of Christos Masouros was supported
in part by the Smart Networks and Services Joint Undertaking Project 6G-
MUSICAL under Grant 101139176 and in part by the Engineering and
Physical Sciences Research Council UK-India Project ICON under Grant
UKRI859. The associate editor coordinating the review of this article and
approving it for publication was G. Zhu. (Corresponding author: Jiang Xue.)
Junkai Zhang and Zongben Xu are with the School of Mathematics
and Statistics, Xi’an Jiaotong University, Xi’an 710049, China (e-mail:
jk.zhang@xjtu.edu.cn; zbxu@xjtu.edu.cn).
Faheem A. Khan is with the School of Computing and Engineer-
ing, University of Huddersﬁeld, HD1 3DH Huddersﬁeld, U.K. (e-mail:
F.Khan@hud.ac.uk).
Zhiqiang Wei and Jiang Xue are with the School of Mathematics and
Statistics, Xi’an Jiaotong University, Xi’an 710049, China, also with the Peng
Cheng Laboratory, Shenzhen 518055, China, and also with Pazhou Labora-
tory, Huangpu, Guangzhou 510555, China (e-mail: zhiqiang.wei@xjtu.edu.cn;
x.jiang@xjtu.edu.cn).
Christos Masouros is with the Department of Electronic and Electrical
Engineering, University College London, WC1E 7JE London, U.K. (e-mail:
c.masouros@ucl.ac.uk).
Dusit Niyato is with the College of Computing and Data Science, Nanyang
Technological University, Singapore 639798 (e-mail: dniyato@ntu.edu.sg).
Digital Object Identiﬁer 10.1109/TWC.2026.3693103
factor, the proposed method achieves a trade-off between rate and
energy while meeting sensing accuracy requirements. Moreover, it
signiﬁcantly reduces computational complexity by up to approx-
imately 96.8% in parameters and 81.5% in FLOPs, compared
to existing DL frameworks.
Index Terms —Deep neural network, low-altitude economy,
predictive beamforming, simultaneous wireless information and
power transfer, integrated sensing and communication.
I. I NTRODUCTION
T
HE low-altitude economy (LAE) represents an emerging
and comprehensive economic ecosystem built around
diverse low altitude aviation activities, including operations
of uncrewed aerial vehicles (UA Vs) and electric vertical take
off and landing aircraft [1], [2]. As a key enabler of next-
generation aerial services, the LAE supports a wide range
of applications such as logistics, environmental monitoring,
entertainment, precision agriculture, and public safety, driving
substantial economic and societal beneﬁts and stimulating
rapid global research interest. The successful realization of
the LAE depends on the safe and efﬁcient operation of a
large number of aircraft in low-altitude airspace (typically
within 1000 meters above ground). This requirement neces-
sitates seamless wireless connectivity, accurate environmental
awareness, and reliable energy support for battery-constrained
aerial platforms. The convergence of communication, sensing,
and energy transfer is therefore envisioned as a cornerstone of
future LAE networks, enabling pervasive connectivity and sus-
tainable operation of Internet of Things devices [3]. To meet
these needs, integrated sensing and communication (ISAC)
and simultaneous wireless information and power transfer
(SWIPT) have emerged as key enabler technologies [4], [5],
[6], [7].
ISAC systems allow the reuse of radio resources for both
data transmission and environmental sensing, while SWIPT
facilitates energy harvesting from radio frequency (RF) signals
to prolong device lifetime. Combining these paradigms into
a uniﬁed SWIPT-ISAC framework promises signiﬁcant
gains in spectral and energy efﬁciency, but introduces new
design challenges [8]. This integration introduces conﬂicting
trade-offs among communication, energy transfer, and sensing
accuracy, which are quantiﬁed in terms of achievable rate,
harvested energy, and Cram ´er-Rao lower bounds (CRLBs),
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

17166 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
respectively. The problem becomes more complex in dynamic
air-ground scenarios, where non-stationary channel state
information (CSI) caused by target/communication user (CU)
mobility demands a high-quality beamforming design to
maintain performance. Conventional optimization-based [9]
or channel-prediction-driven [10] approaches often suffer
from high computational complexity, latency, and sensitivity
to modeling errors, making them unsuitable for real-time
applications.
In sensing-assisted wireless networks, predictive beamform-
ing emerges as a key technique that eliminates reliance on
channel feedback by harnessing information from reﬂected
echoes, thus reducing signaling overhead. Previous studies
have explored predictive beamforming designs for ISAC
and SWIPT-ISAC independently. For instance, the authors
of [11] investigated two radar-assisted predictive beamform-
ing schemes for an extended target model in vehicle-to-
infrastructure communications. In their work, one scheme
dynamically adjusts the beamwidth for robust coverage, while
an upgraded alternant-beam scheme allocates time between
sensing and dedicated communication, achieving signiﬁcant
gains in the achievable rate. Concurrently, to address the
challenge of beam alignment for cellular-connected UA Vs,
a study in [12] proposed a novel predictive beamforming
framework that integrates real-time sensor data with massive
multiple-input-multiple-output (MIMO) communications. By
employing an extended Kalman ﬁlter (EKF) for data fusion,
their developed beamformer enhances tracking accuracy and
delivers superior spectral efﬁciency. However, designing pre-
dictive beamforming strategies for SWIPT-ISAC systems is
particularly challenging because conventional approaches for
MIMO communication, radar sensing, and wireless power
transfer often rely on fundamentally different principles. For
instance, eigenmode transmission with water-ﬁlling is opti-
mal for maximizing communication capacity, while isotropic
transmission enhances radar sensing diversity, and strong
directional beams favor energy harvesting [13]. This inherent
conﬂict is evidenced by research efforts that must navigate
these competing demands. For example, the authors in [14]
proposed an online algorithm to maximize wireless power
transfer efﬁciency while meeting quality-of-service require-
ments for communication and sensing. Their approach, which
relies on EKF to track mobile users, underscores the com-
plexity of balancing these divergent objectives in a dynamic
environment.
Thanks to advances in intelligent wireless networks, deep
learning (DL)-based predictive beamforming methods have
become popular for their fast inference times and strong
ability to solve non-convex optimization problems. In [15],
an ISAC-assisted anti-eavesdropping communication system
was investigated, where DL-based predictive beamforming
was implemented to ensure secure communications with mul-
tiple ground users. A novel Transformer-based deep neural
network (DNN), termed the ISACformer, was developed for
constructing predictive beamformers via exploiting previously
estimated CSI in an unsupervised manner. The work in [16]
investigated ISAC-enabled end-to-end predictive beamforming
to obtain the beamforming vector directly from the reﬂected
signal samples using DL. The proposed approach did not
require an intermediate state parameter estimation step. An
attention-based long short-term memory (LSTM) network was
developed to capture the temporal correlation in the reﬂected
signal samples and derive the beamformer. Further, the authors
of [17] integrated a parallel convolutional neural network
(CNN), LSTM, and a self-attention mechanism to extract
features from historical CSI. This framework directly predicts
the secure beamforming matrix for the subsequent time slot,
aiming to maximize the sum secrecy rate of an intelligent
reﬂecting surface-assisted ISAC system. In particular, the
conﬂicting requirements in SWIPT-ISAC systems, coupled
with dynamic target/CU mobility and non-stationary channels,
motivate the development of intelligent predictive beamform-
ing solutions that can adaptively balance these objectives in
real time. Unfortunately, predictive beamforming solutions
based on DL for such systems remain largely unexplored in
the literature.
Based on the above, this study proposed a DL framework
to design predictive beamforming in SWIPT-ISAC systems
for LAE wireless networks that can efﬁciently balance com-
munication rate and harvested energy, such that the sensing
accuracy and transmit power constraints are satisﬁed. We
consider the downlink scenario with a multi-antenna base
station (BS) that performs integrated sensing, communication,
and power transfer. The BS has the triple objective of deliv-
ering high-rate data to mobile targets/CUs, powering them
wirelessly, and estimating their motion parameters from radar
echoes. The main contributions of this paper are summarized
as follows:
• We propose a DNN, termed Time-Spatial Fusion Network
(TSFusionNet) to achieve predictive beamforming for
the SWIPT-ISAC system in an unsupervised learning
manner. By fusing the spatial and temporal information
of multi-step historical CSI, we map the relationship
between historical CSIs and predictive beamforming,
which eliminates the need for channel prediction and
thereby reallocating the time and memory resources that
would otherwise be consumed by it directly to data
transmission.
• To address the non-stationary temporal dynamics of CSI
induced by moving targets/CUs and to refocus on the
most informative variations, we introduce a differencing
attention module following the time-spatial fusion in
TSFusionNet. This module ﬁrst applies a differencing
operation to stabilize variations between adjacent CSI
samples. It then employs a temporal attention mechanism
to weight different time steps based on their signiﬁcance.
• To balance the communication rate against the harvested
energy, we formulate an optimization problem to maxi-
mize the weighted sum of their respective averages. This
objective is constrained by maintaining the averaged sum
of motion parameter CRLBs below predeﬁned thresholds,
while ensuring the predictive beamforming adheres to the
transmit power constraint.
• To solve the constrained optimization problem, we
employ a penalty method to transform it into an
unconstrained objective, acting as the loss function for
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

ZHANG et al.: INTELLIGENT PREDICTIVE BEAMFORMING FOR LAE 17167
training TSFusionNet. Unlike methods that rely on a
manually-tuned or greedily-searched ﬁxed penalty factor,
we propose an adaptive update strategy that dynamically
adjusts it throughout training. This approach eliminating
the need for expensive hyperparameter search.
Simulation results demonstrate that, by adjusting the weight
factor, TSFusionNet effectively regulates the rate-energy trade-
off while satisfying the sensing CRLB constraint. The ablation
study further indicates that removing the differencing atten-
tion module leads to noticeable performance degradation,
underscoring its importance in mitigating non-stationary CSI
dynamics. Moreover, the adaptive penalty-based loss enables
over 90% of realizations to satisfy the CRLB threshold without
manual hyperparameter tuning, conﬁrming the reliability of
the proposed training strategy. In addition, compared with
existing DL-based methods, TSFusionNet reduces the number
of parameters by 96.8% and FLOPs by 81.5%, while requiring
only 0.7 ms inference time per sample, thereby supporting
the real-time applicability of the proposed framework in LAE
scenarios.
The remainder of this paper is organized as follows. Sec-
tion II introduces the SWIPT-ISAC system model, including
the transmission and reception of SWIPT-ISAC signals, as well
as the signal model for energy harvesting. This section also
presents the BS measurement and target/CU motion parameter
models. In Section III, the weighted sum optimization problem
for predictive beamforming design is formulated, taking into
account the rate-energy trade-off. Section IV investigates the
application of TSFusionNet for unsupervised predictive beam-
forming design. Finally, simulation results and conclusions are
provided in Sections V and VI, respectively.
Notations: B, b,b represent a matrix, a vector, and a scalar,
respectively. BH, BT , and B−1 are the Hermitian, transpose,
and inverse of B, respectively. ‖B‖F and det|B| are the
Frobenius norm and determinant of B.‖b‖ and|b| are the
norm of b andb, respectively. diag[b1b2] is the diagonal matrix
formed by b1 and b2. [b]m denotes the m-th element of b.
[B]m,n denotes the (m,n )-th entry of B.⊗ and⊙ denote the
Kronecker product and Hadamard product. (·)∗ is the complex
conjugate. IK is the K×K identity matrix. Re{·} and Im{·}
are the real part and the imaginary part of the complex number,
respectively.U[a,b ] represents uniformly distribution between
a and b.
II. S YSTEM MODEL
We consider an SWIPT-ISAC system for potential deploy-
ment in the LAE wireless network. This system features a
mono-static BS with NT transmit antennas and NR receive
antennas, which operates in full-duplex (FD) mode. To cancel
the self-interference (SI) from FD transmission, we assume
the use of separated transmit and receive antennas along
with efﬁcient antenna isolation. As veriﬁed by [18] and [19],
this method is sufﬁcient for SI mitigation in ISAC systems.
Furthermore, the BS is located on the open ground or the top
roof of a building, allowing it to communicate and transmit
power to K moving targets/CUs, i.e., UA Vs, while receiving
their reﬂected echoes for predictive beamforming design with
its radar function. The designated beamforming is used for
Fig. 1. Illustration of an SWIPT-ISAC system.
sending data as well as beaming power to the target/CU. A
simple system model is shown in Fig. 1
As for targets/CUs, we assume that each of them has Nr
receive antennas receiving one data stream from the BS and
moves at constant speeds relative to the BS. While it is
feasible for targets/CUs to receive multiple data streams, this
would necessitate additional receive beamforming design. To
preserve the scope of this work, we reserve the investigation of
this scenario for future work. Furthermore, these targets/CUs
are equipped with both information decoding (ID) and energy
harvesting (EH) 1 capabilities. To avoid straying from the
main focus of this paper, we assume targets/CUs have perfect
CSI from the BS, thus optimal receive beamforming can be
achieved. This study focuses on the downlink scenario with
the point target model [20]. Similar to that in [16] and [21],
due to the locations of the BS and targets/CUs, we assume a
high probability of line-of-sight (LoS) transmission. Although
we acknowledge the importance of non-line-of-sight (NLoS)
transmission, it would generally reduce sensing accuracy due
to weaker echoes and potential ghost targets, while for commu-
nication and energy harvesting, it could introduce both fading
and scattering diversity. This creates a more complex trade-
off than in the LoS scenario. Therefore, the consideration of
NLoS transmission is left for future work. Once a target/CU
enters the radar coverage, it can be detected accurately using
conventional methods such as radar signal processing or beam
training [10]. Moreover, we consider that all targets/CUs
are equipped with uniform planar arrays (UPAs) and, for
simplicity, move parallel to the UPA of the BS, resulting
in the same angle of arrival (AoA) and angle of departure
(AoD) [10].
Remark 1: If the UPAs of the targets/CUs are not parallel
to the UPA of the BS, tracking errors may occur in the motion
parameters of the targets/CUs, as well as resulting in different
AoA and AoD for the communication link. An offset known
1Although the harvested power is negligible compared to navigation needs,
it is treated in our model as a supplement rather than a primary source. Thus,
it serves to slightly extend operational lifetime, power low-energy sensors, or
enable trickle-charging, thereby improving overall system efﬁciency.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

17168 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
at the BS can be added to the tracked motion parameters to
correct for these errors [10].
A. Transmit Signal Model
The total time period T is partitioned into small time slots,
each of duration ∆T , where the channel is assumed to be
stable within this small time duration. The SWIPT-ISAC signal
transmitted by the BS to the K targets/CUs in a continuous
time t ∈ [0,T ] that falls within the n-th time slot can be
expressed as
xn(t) = Fnsn(t), forn = 0, 1, 2,..., (1)
where Fn = [fn,1, fn,2,..., fn,K]∈ CNT×K is the transmit
beamforming matrix of BS with fn,k ∈ CNT×1, ∀k ∈
{1, 2,...,K }, representing the transmit beamforming vec-
tor for communicating with the k-th target/CU. sn(t) =
[sn,1(t),sn,2(t),...,s n,K(t)] ∈ CK×1 is the uncorrelated
transmit data stream, i.e., E{sn(t)sHn (t)} = IK, with sn,k(t)
denoting the data stream transmitted to the k-th target/CU.
B. Target/CU Signal Model
The RF signal received at the k-th target/CU during the
n-th time slot, considering the multi-target/CU interference, is
therefore expressed as
yn,k(t) = Hn,kfn,ksn,k(t)| {z }
desired signal
+
K∑
i=1,
i⁄=k
Hn,kfn,isn,i(t)
| {z }
multi-target/CU interference
+zn,k(t),
(2)
where Hn,k =
√
βn,kNrNTaNr(θn,k,φn,k)aHNT(θn,k,φn,k) ∈
CNr×NT is the channel between the BS and k-th target/CU.
βn,k = βd−ϖn,k is the channel fading coefﬁcient [10] with β
and ϖ being the path loss at 1 m distance and path loss
exponent; dn,k is the propagation distance between the BS
and the k-th target/CU. λ = cfc is the wavelength; c is thespeed of light; fc is the carrier frequency. aNT(θn,k,φn,k)
and aNr(θn,k,φn,k) are the transmit and received steering
vectors with θn,k and φn,k being the azimuth and elevation
AoA/AoD, respectively. For UPA with M antenna elements,
the steering vector can be expressed by
aM(θ,φ ) = 1√M [1,a 1(θ,φ ),...,a M−1(θ,φ )]T, (3)
where am(θ,φ ) = e−j 2πλ uTm[cosθ cosφ,sinθ cosφ,sinφ]T ; um =
[xm,ym, zm]T is the Cartesian coordinate of the m-th antenna
element; zm ≈ 0 since it represents the antenna height
measured from the UPA plane. zn,k(t) ∈ CNr×1 is the
additive white Gaussian noise (AWGN) vector with zero mean
and covariance matrix of σ2cINr. Note that the delay and
Doppler shift can be compensated by exploiting existing time-
frequency synchronization approaches [22], which are omitted
in the signal model above.
After receiving the RF signal, the target/CU splits the
received signal into two parts with a power splitter: one part
goes for ID, while the remaining for EH. The signal for
ID at the k-th target/CU after combining with the received
beamformer wn,k∈ CNr×1, is given by
yIDn,k(t) = wHn,k(√αyn,k(t) +~zn,k(t)), (4)
where α∈ [0, 1] is the power splitting ratio for ID. ~zn,k(t)∈
CN r×1 is a composite noise term encompassing the effects
of non-ideal splitters, RF-baseband conversion imperfections,
and thermal noise, which is modeled as zero-mean complex
Gaussian distribution with covariance matrix of δ2INs [23],
[24]. According to [15] and [25], the optimal combiner for
maximizing the communication rate at the k-th target/CU is
given as
wn,k = aNr(θn,k,φn,k). (5)
As for the EH process, the received signal used for harvest-
ing energy is approximated as
yEHn,k(t)≈√1−α~yn,k(t), (6)
where ~yn,k(t) is the received signal by omitting the AWGN
vector in (2). In addition, the noise introduced by the power
splitter is also omitted from the above equation. The reason for
this simpliﬁcation is that these noise terms harvest negligible
energy compared to others [24].
C. BS Measurement Model
During the n-th time slot, the echoes reﬂected by K tar-
gets/CUs are received by the BS for sensing, and the received
echo is written as
rn(t) =
K∑
k=1
Gn,kxn(t−τn,k)ej2πγn,kt + un(t), (7)
where Gn,k =ςn,k
√NRNTaNR(θn,k,φn,k)aHNT(θn,k,φn,k) ∈
CNR×NT. ςn,k = ε2dn,k represents the reﬂection coefﬁcient;ε is the radar cross-section factor [26]. τn,k and γn,k
are the round-trip delay and Doppler shift, respectively.
un(t)∈ CNR×1 is the AWGN vector.
To identify the echo from the k-th target/CU, we
exploit the orthogonality of the steering vectors, i.e.,
aHM(θ1,φ 1)aM(θ2,φ 2)≈ 0 for θ1⁄= θ2 or φ1⁄= φ2, which
holds in massive MIMO systems [27, Corollary 2]. Thanks
to this property, the inter-beam interference can be mitigated
by spatial ﬁltering techniques [28]. Consequently, the received
echo from the k-th target/CU after spatial ﬁltering is given by
rn,k(t) = ~wHn,k
( K∑
k=1
Gn,kxn(t−τn,k)ej2πγn,kt + un(t)
)
= gTn,kxn(t−τn,k)ej2πγn,kt +~un,k(t), (8)
where gTn,k = ςn,k√NRNTaHNT(θn,k,φn,k). ~wn,k =
aNR(ˆθn,k, ˆφn,k) acts as the spatial ﬁlter with ˆθn,k and ˆφn,k
being the estimated AoAs with conventional AoA estimation
methods, which we assume ˆθn,k ≈ θn,k and ˆφn,k ≈ φn,k
[21].~un,k(t) represents the AWGN noise with zero mean and
variance of σ2.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

ZHANG et al.: INTELLIGENT PREDICTIVE BEAMFORMING FOR LAE 17169
Then we apply matched ﬁltering to (8) to obtain estimation
of round-trip delay ˆτn,k and Doppler shift ˆγn,k [10], respec-
tively, which is
{ˆτn,k, ˆγn,k} = arg maxτ,γ
‖‖‖‖‖∫ Ts0 rn,k(t)e−j2πγts∗n,k(t−τ)dt‖‖‖‖‖2,
(9)
where Ts ≪ ∆T is the time length of the signal. After
getting these estimates, the multi-target/CU interference in (8)
can be mitigated with the existing interference cancellation
technique proposed in [29]. To maintain the focus of this
work, we assume the multi-target/CU interference has been
well canceled. Therefore, the measurement model for azimuth
angle θn,k and elevation angle φn,k is given by
ˆrn,k = gTn,kfn,k
∫ Ts
0
sn,k(t−τn,k)s∗n,k(t− ˆτn,k)
×ej2π(γn,k−ˆγn,k)tdt +ur,n,k (10)
≜ gTn,kfn,k +ur,n,k, (11)
where ur,n,k is the measurement noise normalized by the
matched ﬁlter gain κ [30], which is a zero-mean complex
Gaussian distributed random vector with variance of σ2r . The
value of σ2r is deﬁned as ξrσ2/κ, where ξr is related to the
system characteristics and estimation algorithms [10], [28].
Subsequently, the measurement model for the propagation
distancedn,k and the radial velocity to the BS νn,k of thek-th
target/CU is modeled as
ˆτn,k = 2dn,kc +uτ,n,k, (12)
ˆγn,k =−2νn,kλ +uγ,n,k, (13)
where uτ,n,k and uγ,n,k are zero-mean Gaussian distributed
measurement noise with variance of σ2τ and σ2γ, respectively.
The value of σ2τ and σ2γ is deﬁned by ξiσ2/(κ||gTn,kfn,k||2)
for i = τ,γ , where ξi is related to the system characteristics
and estimation algorithms [10], [28].
D. Target/CU Motion Parameter Model
By extending the model proposed in [21] from
2-dimensional (2D) to 3-dimensional (3D), we express
the motion parameter model for this work as follows.
Assume that all targets/CUs move along the y-axis of a 3D
Cartesian coordinate, where the UPA of the BS is located at the
origin. For thek-th target/CU, we denote its position asdn,k =
[dxn,k,dyn,k,d zn,k]T , velocity as νn,k = [ νxn,k,νyn,k,ν zn,k]T .
Given that the kinematic state of targets/CUs can be affected
by wind or system control error, we introduce pn,k =
[pxn,k,pyn,k,p zn,k]T as a perturbation acceleration to reﬂect the
real-world inﬂuence.
Therefore, the position and velocity of the k-th target/CU at
then-th time slot can be updated by its values of the (n−1)-th
time slot, which gives the following models
dn,k = dn−1,k + ∆T νn−1,k + 12∆T 2pn−1,k, (14a)
νn,k = νn−1,k + ∆Tpn−1,k. (14b)
Based on the above, the motion parameter model for the k-th
target/CU at the n-th time slot can be written as
dn,k =‖dn,k‖ +ud, (15a)
θn,k = arctan2
(
dxn,k,dyn,k
)
+uθ, (15b)
φn,k = arcsin
dzn,k
dn,k
+uφ, (15c)
νn,k =
νTn,kdn,k
dn,k
+uν, (15d)
where arctan2 (·,·) is the four-quadrant inverse tangent. ud,
uθ,uφ, and uν are measurement noises introduced by estima-
tion and systematic errors. These are modeled as zero-mean
Gaussian random variables with variances σ2d,σ2θ,σ2φ, and σ2ν,
respectively.
III. P ROBLEM FORMULATION
In this section, we will derive key performance indicators
for ID, EH, and sensing. Then, we formulate the optimization
problem for predictive beamforming design that can balance
the averaged achievable rate and the averaged harvested
energy. Unlike the protocol in [31], beam training is only
required during the initial time slot for our protocol. Moreover,
compared to the two-step beam prediction approach introduced
in [10], our method eliminates the need for explicit channel
prediction. Therefore, signaling overhead can be signiﬁcantly
reduced.
A. Information Decoding Performance
In this work, we evaluate the ID performance by the
averaged achievable rate. Given the received signal for ID in
(4), the signal-to-interference-plus-noise ratio (SINR) for the
k-th target/CU at the n-th time slot is cast as
SINRn,k =
α
⏐⏐⏐wHn,kHn,kfn,k⏐⏐⏐2
K∑
i=1,i⁄=k
α
⏐⏐⏐wHn,kHn,kfn,i⏐⏐⏐2 +ασ2c +δ2. (16)
Therefore, the averaged achievable rate at the n-th time slot
is written as
Rn = 1K
K∑
k=1
log2 (1 + SINRn,k). (17)
B. Energy Harvesting Performance
Owing to the non-linear nature of circuit components within
the EH unit, a non-linear saturation model proposed in [32] is
used to capture the harvested energy by the k-th target/CU at
the n-th time slot, which is cast as
En,k = Ψn,k−QΞ1− Ξ (18)
with
Ξ = 11 +eιϱ, (19a)
Ψn,k = Q
1 +e−ι(‖yEHn,k(t)‖2−ϱ), (19b)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

17170 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
‖yEHn,k(t)‖2 = (1−α)‖Hn,kFn‖2F, (19c)
where Q is the maximum harvested energy under EH circuit
saturation. The coefﬁcientsι andϱ represent the characteristics
of the speciﬁc EH hardware, incorporating the effects of its
internal resistance, capacitance, and diode turn-on voltage.
Therefore, the averaged harvested energy at the n-th time slot
is given by
En = 1K
K∑
k=1
En,k (20)
C. Sensing Performance
Since the sensing function is used for tracking the tar-
gets/CUs, its performance is measured by the estimation error
of the motion parameters. A general way to evaluate the
estimation error is the CRLB, which is the lower bound of
the mean squared error for any unbiased estimator [30].
The CRLBs for motion parameters of the k-th target/CU at
the n-th time slot are obtained by inverting the Fisher infor-
mation matrix (FIM) Jn,k and taking its diagonal elements,
which are
C (dn,k) =
[
J−1n,k
]
1,1
, (21a)
C (θn,k) =
[
J−1n,k
]
2,2
, (21b)
C (φn,k) =
[
J−1n,k
]
3,3
, (21c)
C (νn,k) =
[
J−1n,k
]
4,4
. (21d)
The details for deriving FIM can be found in Appendix.
D. Optimization Problem F ormulation
In this work, we formulate an optimization problem aimed
at designing predictive beamforming that maximizes the
weighted sum of the averaged achievable rate and the averaged
harvested energy, under the constraints that the averaged sum
of CRLBs for the motion parameter estimates remains below
predeﬁned thresholds and the precoder satisﬁes the transmit
power constraint. The corresponding optimization problem is
given as
max
Fn
ρE{Rn} + (1−ρ)E{En} (22a)
s.t. 1K
K∑
k=1
E{C (dn,k) +C (θn,k)
+C (φn,k) +C (νn,k)}≤ ζ, (22b)
‖Fn‖2F≤Pt, (22c)
where 0 ≤ ρ ≤ 1 is the weight factor controlling the
preferred objective. ζ presents the threshold of the averaged
sum of CRLBs. 2 Pt is the total transmit power constraint;
2Following the C-R-E (CRLB-rate-energy) Pareto framework proposed in
[5], the value of ζ is not selected arbitrarily. Speciﬁcally, the minimum
achievable averaged sum of CRLBs, denoted by ζmin, is derived under the
same transmit power constraint to guarantee the feasibility of (22). Then,
by removing the CRLB constraint in (22), we obtain ζ0. Consequently, any
ζ ≥ ζmin ensures feasibility of (22), while any value of ζ ∈ [ζmin,ζ 0]
corresponds to different points along the C-R-E Pareto boundary.
The expectation E{·} denotes the ensemble average over all
randomness from both the noises and the channel fading
realizations.
This problem formulation prioritizes sensing accuracy as a
constraint, which is motivated by the safety-critical nature of
LAE applications, where reliable environmental awareness is
a rigid prerequisite for safe operation. Accordingly, commu-
nication and energy harvesting are optimized only after the
sensing constraint is met. This prioritization is essential for
robust LAE networks, distinguishing our work from traditional
communication-ﬁrst paradigms.
However, the optimization problem in (22) is intractable due
to the highly non-convex nature of both the objective function
and the constraints. Conventional solvers may struggle to
address such problems efﬁciently, often resulting in high
computational complexity or becoming unsolvable. Motivated
by this, we propose a DL approach to derive the desired beam-
former matrix in an unsupervised manner, using historical CSI
of the communication link as input. The proposed network
architecture will be presented in the following section.
Note that although deep reinforcement learning (DRL) has
been investigated for predictive beamforming design [33],
[34], it relies on trial-and-error interactions, which can lead
to training instability and are complex for real-world systems.
Moreover, DRL is tailored for sequential decision-making
problems, whereas our task is a single-step predictive opti-
mization. Since a differentiable loss function is available in
this work, the unsupervised DL approach allows the model to
be optimized efﬁciently via backpropagation, yielding more
stable and faster convergence while avoiding the sample inef-
ﬁciency and high-variance reward estimates inherent in the
DRL approach.
IV. TSF USION NET FOR PREDICTIVE BEAMFORMING
DESIGN
In this section, we ﬁrst formulate the loss function used
to train the DL network according to the penalty method,
where the penalty factor can be adaptively updated. This is
followed by a detailed introduction of our proposed TSFusion-
Net architecture for designing predictive beamforming using
ω-step historical CSIs of the communication links. 3
Note that for the “current” time slot, the ISAC signal is
transmitted by the BS through the beamformer designed in the
previous time slot. The BS then receives the reﬂected echoes
and uses them to ﬁrst estimate the states of the targets/CUs
before predicting the transmit beamformer for the upcoming
time slot. In this work, we assume the state estimation stage
has been completed and focus only on the prediction of the
transmit beamformer.
A. Loss Function
Due to the highly non-convex nature of the optimization
problem in (22), we employ the penalty method to transform
3The proposed TSFusionNet, with its ability to learn from historical CSIs,
could be a promising starting point for handling NLoS scenarios, as it may
learn to infer spatial information from diffuse reﬂections [35].
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

ZHANG et al.: INTELLIGENT PREDICTIVE BEAMFORMING FOR LAE 17171
the constrained optimization into an unconstrained loss func-
tion for our proposed TSFusionNet. This approach replaces
the original constraints with penalty terms in the loss func-
tion, providing a tractable framework for network training.
Moreover, in contrast to existing works [15], [21], [28] that
use a ﬁxed penalty factor, we dynamically update it during
training based on criteria introduced later to balance constraint
satisfaction with objective optimization, thus eliminating the
need for expensive hyperparameter search.
The optimization problem in (22) can be transferred to a
penalty loss function in the following way, that is
L(Fn,µ ) =−(ρE{Rn} + (1−ρ)E{En})
+µ max (0,vn(Fn)) (23)
with
vn(Fn) = 1K
K∑
k=1
E{C (dn,k) +C (θn,k)
+ C (φn,k) +C (νn,k)}− ζ, (24)
where µ≥ 0 is the penalty factor. It is noted that rather than
incorporating the power constraint (22c) into the loss function
above, it is enforced as a hard constraint by a normalization
layer in the TSFusionNet before its output.
To dynamically enforce the tightness of the constraint, based
on the performance on the validation set, the penalty factor is
adaptively increased until either the constraint is satisﬁed or
the factor reaches a predeﬁned maximum. The core principle
is to monitor the constraint violation during validation and
update the penalty factor only when the improvement stagnates
over consecutive epochs. The update process is mathematically
described as
µ(i+1) =
{
min(lµ(i),µ max) for n′ =N
µ(i) otherwise, (25)
where i = 1, 2,... denotes the training epoch index, l > 1
is the growth factor, and µmax is the maximum penalty
factor. Note that n′ increases by 1 when the improvement
ratio of violation, deﬁned as V (i+1)/V (i), is greater than a
predeﬁned threshold v. Conversely, n′ is decremented by 1
but is constrained to remain non-negative. Furthermore, n′ is
reset to 0 when the constraint is satisﬁed or a new penalty
factor is triggered. The update mechanism for the penalty
factor incorporates the following two stopping criteria:
• The update is terminated if the constraints are satisﬁed
for N′ consecutive epochs;
• Alternatively, the update stops when µ(i) reaches µmax.
This approach ensures a balance between timely updates to
enforce constraints and avoiding unnecessary increases in the
penalty factor once the solution is feasible.
B. TSFusionNet Architecture
TSFusionNet is designed to formulate predictive beamform-
ing by treating the ω-step historical CSI of communication
links as a time series. The DNN comprises three specialized
modules: 1) a Fusion Module that integrates temporal and
spatial features from the historical CSI, employing CNNs
to extract spatial features from ω-step CSI sequence of
each target/CU, followed by LSTM layer to model tem-
poral dependencies; 2) a Differencing Attention Module
that handles non-stationary temporal dynamics and calibrates
the signiﬁcance of different time steps to strengthen the
representation capability; and 3) a Prediction Module that
utilizes a 1-dimensional (1D) CNN layer, a linear layer, and a
normalization layer to generate the beamforming predictions
for the subsequent time slot. The detailed structure of each
module will be introduced in the following. The TSFusionNet
architecture is depicted in Fig. 2.
1) Data Preprocessing: Before being fed into the TSFu-
sionNet, the input data undergoes a preprocessing step. The
input for each CNN module corresponds to the CSI from a
speciﬁc historical time slot t′ across all K targets/CUs. These
CSIs are concatenated along the dimension of the number of
targets/CUs through an operation M{·} to form a 3D tensor
Ht′∈ CK×Nr×NT, given as
Ht′ =M{Ht′,1, Ht′,2,..., Ht′,K}, (26)
where t′ = n− 1,n − 2,...,n − ω. Note that to ensure
stable training and to focus the model on learning the spatial-
temporal structure of channels rather than their large-scale
gains, the channel matrix of each user Ht′,k is ﬁrst normalized
by its Frobenius norm before concatenation [36].
We then decompose the complex data into its real and
imaginary components to construct the input for the fusion
module as follows, which is
˜Ht′ =R{ Re{Ht′}, Im{Ht′}}, (27)
whereR{·} : RK×Nr×NT×2 ↦→ R2K×Nr×NT represents a
reshaping function.
2) Fusion Module: Given the pretreated data, they are ﬁrst
sent to the fusion module to combine and explore the temporal
and spatial features. For each input ˜Ht′, a CNN module is
utilized to extract its spatial characteristics. As illustrated in
Fig 3, this module comprises two 2D convolutional layers,
each followed by a 2D batch normalization layer and a
Rectiﬁed Linear Unit (ReLU) activation function. Both CNN
layers employ a 3× 3 kernel with a stride of 1 and padding
of 1, progressively transforming the channel dimension from
2K to 16 and then to 2. A 2D average pooling layer is
subsequently applied to halve the spatial dimensions of the
feature maps, thereby reducing computational complexity and
mitigating potential overﬁtting. The kernel size of the pooling
layer is set as 5× 5 with a stride and padding both of 2. To
this end, a ﬂattening layer is applied to render the features
compatible with the subsequent LSTM layer.
The spatial features corresponding to all ω time steps
are then integrated by a one-layer LSTM to explore their
temporal dependencies, for which the hidden size is designated
as 64. Finally, the hidden states for all ω LSTM cells are
concatenated to be the input of the differencing attention
module, which is represented as
¯Hn = [h1n, h2n,..., hωn]T, (28)
where hin∈ R64×1 is the hidden state of the i-th LSTM cell.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

17172 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 2. Network architecture of the proposed TSFusionNet.
Fig. 3. Network architecture of the CNN module.
From the perspective of wireless communications, as
explored in prior studies [37], [38], [39], the objective of this
fusion module can be treated as implicitly predicting the CSI
for the upcoming time slot by leveraging the proven capabil-
ities of CNN in extracting spatial correlation and LSTM in
capturing temporal dependency. This implicit channel predic-
tion process removes the need for computationally expensive
explicit prediction in beamforming design.
3) Differencing Attention Module: To mitigate the impact
of non-stationary temporal dynamics in CSIs for moving
targets/CUs and refocus on the most informative temporal
variations, we design this differencing attention module, which
enhances network representation. This module consists of a
ﬁrst-order4 differencing layer and a temporal attention layer.
The differencing layer aims to reduce the non-stationary effect
[40]. However, to avoid disrupting the information ﬂow, the
differencing layer is applied to the output of the fusion module,
rather than the original input. Consequently, the output of the
differencing layer is written as
Dn = [h2n− h1n, h3n− h2n,..., hωn− hω−1n ]T. (29)
4High-order differencing should be applied carefully in severe non-
stationary scenarios, since over-differencing can damage the correlations
among time series, which in turn can impair the network representation
capability [38].
Fig. 4. Network architecture of the temporal attention.
After differencing, the outputs from the fusion module and
difference layers are concatenated along the dimension of time
steps to calculate the weight cn∈ R(ω−1)×1 for Dn through a
temporal attention layer, which recalibrate Dn by emphasizing
time steps with signiﬁcant dynamic patterns. The concatenated
input is ﬁrst transferred to a 1D adaptive average pooling layer
and a 1D adaptive max pooling layer, respectively, to reduce
the length of the sequence to one. Then, these two outputs are
processed by a shared multi-layer perceptron (MLP), which
has two linear layers and a ReLU activation function between
them. The number of neurons for these two linear layers is set
as⌊(2ω− 1)/2⌋ andω− 1, respectively. The outputs of these
MLPs are added together and a sigmoid function is used to
scale the weight to [0, 1]. The structure of the proposed channel
attention layer is shown in Fig. 4. The output of the channel
attention layer is given as
¯Dn = cn⊙ Dn. (30)
Finally, by concatenating ¯Hn and ¯Dn along the dimension
of time steps, we have the output of the differencing attention
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

ZHANG et al.: INTELLIGENT PREDICTIVE BEAMFORMING FOR LAE 17173
TABLE I
SYSTEM PARAMETERS AND DEFAULT VALUES
module, which is
˜Dn =
[
¯HTn, ¯DTn]T. (31)
4) Prediction Module: The prediction module is designed
to map the relationship between the output of the differencing
attention module and the beamforming matrix for then-th time
slot. Its architecture consists of a single channel 1D CNN layer
(with a kernel size of 3, a stride of 1, and a padding of 1),
a ReLU activation, and a linear layer (with 2NTK neurons).
After applying a mapping functionF(·) : R2NTK↦→ CNT×K,
we obtain a matrix ˜Fn with complex entries. Finally, we per-
form normalization on ˜Fn to produce the desired beamforming
matrix for the n-th time slot that satisﬁes the power constraint
[41], [42], which is
Fn =
√
Pt
˜Fn
‖˜Fn‖F. (32)
V. S IMULATION RESULTS
In this section, we evaluate the performance of our proposed
TSFusionNet-based SWIPT-ISAC scheme. Unless otherwise
speciﬁed, system parameters are listed in Table I. The mean
value of the initial distance for all targets/CUs are d0,1 =
[10, 15, 5]T , d0,2 = [15, 25, 15]T , d0,3 = [10,−10, 10]T , and
d0,4 = [15,−20, 20]T . The mean value of the initial velocity
for all targets/CUs are ν0,1 = [0,−10, 0]T , ν0,2 = [0,−9, 0]T ,
ν0,3 = [0, 8, 0]T , and ν0,4 = [0, 7, 0]T . A uniformly dis-
tributed random variable is added to each axis of the initial
states to add randomness, i.e., U[−1, 1] for distance and
U[−0.5, 0.5] for velocity. The perturbation acceleration is set
as [0.03,−0.1, 0.02]T for all targets/CUs and remains constant
duringT for simplicity. The initial value of the penalty factor
µ is set to 1. We perform training and testing of TSFusionNet
on PyTorch 3.8 with NVIDIA RTX 3090 graphics processing
units. The size of the training, validation, and test sets is set
to 7000, 2000, and 1000, respectively. The batch size is 100
with a learning rate of 10−3. We train the model for 300
epochs with the Adam optimizer. To stabilize the training
process, we apply min-max normalization to the ID and EH
metrics in the loss function using the statistics obtained from
each mini-batch, thereby ensuring they share the same scale.
Additionally, only the model that satisﬁes the constraint on the
validation set with the lowest validation loss will be saved as
the ﬁnal model.
A. Performance Evaluation Complexity Analysis
To assess the proposed TSFusionNet, we compare its ID
and EH performance and computational complexity against
the following baselines:
• TSFusionNet (perfect): This baseline constitutes a sim-
pliﬁed version of our TSFusionNet, which deliberately
disregards multi-target/CU interference in the rate cal-
culation and omits the CRLB constraint from the loss
function. This setup allows for a direct comparison to a
“perfect” situation.
• ISACformer: This model is a modiﬁed version of the
Transformer proposed in [15] for the predictive beam-
forming design, where multi-head attention in the decoder
of the conventional Transformer architecture is replaced
by a CNN module, due to the lack of CSI for the next
time slot.
• EPDNet: This model is an encoder-prediction-decoder
DNN for predictive beamforming proposed in [21]. A
CNN-based encoder extracts spatial information from the
CSI of each target/CU at each time slot. These spatial
features are then processed by an LSTM for prediction.
Finally, the MLP-based decoder is designed to generate
the beamforming matrix.
• E2E-PB: The DNN introduced in [16] comprises an
LSTM layer, an attention module, and a fully-connected
layer, which collectively serve the purpose of temporal
feature extraction.
• Alternating Direction Method of Multipliers (ADMM): As
a conventional method baseline, we employ the ADMM
[45] to directly solve the non-convex problem in (22).
ADMM decomposes the original problem into a sequence
of more manageable sub-problems, which are solved
iteratively. The number of iterations is set to 500 with
a step size of 10−3.
• Zero-F orcing (ZF):ZF is a classic linear precoding tech-
nique in MIMO communications [13]. Its core principle
is to project the transmit signal onto the null space of the
interference channel, thereby canceling multi-target/CU
interference.
• Maximum Ratio Transmission (MRT): As a classical
beamforming strategy, MRT [13] maximizes the array
gain by aligning the beamforming vector with the chan-
nel direction of the targets/CUs, thereby enhancing the
received signal power. This property makes it particularly
suitable for maximizing the harvested energy.
Fig. 5(a) compares the ID performance of the proposed
“TSFusionNet” with various baseline algorithms across the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

17174 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 5. Performance comparisons in terms of Pt = [0 , 30] dBm (a) ID
performance; (b) EH performance.
transmit power range of Pt = [0 , 30] dBm. As observed,
all algorithms except for “TSFusionNet (perfect)” and “ZF”
exhibit signiﬁcant rate degradation in the high-power region,
which is attributable to strong multi-target/CU interference.
Despite this, our “TSFusionNet” maintains the highest com-
munication rate among all DL-based approaches. In the
low-power region, our method achieves a performance compa-
rable to “ZF”, which serves as an upper bound for conventional
beamforming techniques. Notably, “TSFusionNet (perfect)”
represents an ID performance upper bound, as it is evaluated
under idealized conditions without multi-target/CU interfer-
ence and sensing constraints.
In terms of EH performance shown in Fig. 5(b), the upper
bound is achieved by “MRT” owing to its principle of max-
imizing the signal power. Conversely, this design principle,
which does not suppress multi-target/CU interference, results
in its lowest communication rate. “TSFusionNet (perfect)”
outperforms the standard “TSFusionNet” in EH because it
is optimized without the need for interference cancellation,
thereby reserving more power for energy harvesting. Notably,
our proposed “TSFusionNet” harvests the most energy among
all other practical algorithms that must manage interference.
These results collectively demonstrate that “TSFusionNet”
successfully strikes a balance between communication rate and
energy harvesting in the considered scenario.
TABLE II
COMPLEXITY ANALYSIS OF DIFFERENT ALGORITHMS
Moreover, a comprehensive complexity analysis is provided
in Table II. We assess network parameters, ﬂoating point
operations (FLOPs), and inference time for DL models, while
reporting only the execution time for conventional methods.
Our proposed “TSFusionNet” ranks as the most efﬁcient
learning-based algorithm. Notably, it achieves reductions of
96.8% in parameters, 81.5% in FLOPs, and a 31.4% speed-up
in inference time compared to the most complex DL bench-
mark. The conventional “MRT”, while fast, is fundamentally
limited in its ability to manage the rate-energy trade-off. Mean-
while, the iterative “ADMM” solver exhibits excessively high
latency per sample, making it susceptible to data being out-
dated in dynamic channels. These results collectively conﬁrm
that “TSFusionNet” successfully combines high performance
with low computational cost. Crucially, the inference time of
our proposed “TSFusionNet” is only a small fraction of ∆T
(10 ms), leaving ample time for data transmission and other
baseband processing within the slot, thereby validating the
real-time feasibility of our framework.
B. Effectiveness of the Adaptive Penalty Factor
To evaluate the effectiveness of the proposed adaptive loss
function, Fig. 6 compares the performance of models trained
with a ﬁxed penalty factor against those trained with the
adaptive penalty factor. The cumulative distribution functions
(CDFs) of the communication rate, energy harvesting per-
formance, and sensing accuracy are evaluated at transmit
power levels of Pt = 10 , 20, 30 dBm. To ensure a fair
comparison, the ﬁxed penalty factor µ is set to the maximum
value obtained from the adaptive scheme during training, i.e.,
µ = 3120, 125, 5, respectively.
The results pertaining to the primary optimization objective,
i.e., the ID and EH performance, reveal that these two loss
functions yield nearly identical performance distributions. This
is evidenced by the close alignment of their CDF curves,
as well as their mean values and key percentiles (50-th and
90-th) across all transmit power levels, indicating a comparable
performance level for communication and energy harvesting.
Regarding sensing performance, although a minor mismatch
exists in the distributions, the differences in mean values and
key percentiles remain within an acceptable margin. Further-
more, it is evident that over 90% of the CRLB values fall
below the predeﬁned threshold, i.e., ζ = 10−3, conﬁrming the
effectiveness of the proposed algorithm in meeting the sensing
requirement.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

ZHANG et al.: INTELLIGENT PREDICTIVE BEAMFORMING FOR LAE 17175
Fig. 6. CDF of ﬁxed and adaptive penalty factors for (a) ID performance; (b) EH performance; (c) sensing performance in terms of Pt = 10, 20, 30 dBm.
Fig. 7. Ablation study in terms of different values of transmit power.
Overall, Fig. 6 demonstrates that the proposed adaptive loss
function achieves satisfactory effectiveness while offering the
signiﬁcant advantage of eliminating expensive hyperparame-
ter tuning. More importantly, it attains performance on par
with its ﬁnely-tuned ﬁxed-penalty counterpart, but does so
autonomously, thereby greatly enhancing the practicality and
efﬁciency of the SWIPT-ISAC system optimization.
C. Ablation Study
We conduct an ablation study to evaluate the efﬁcacy of
the differencing attention module for varying transmit power
from 0 dBm to 30 dBm, as illustrated in Fig. 7. The baseline
model is deﬁned as our TSFusionNet without the differencing
attention module, where the hidden states from all LSTM cells
are directly concatenated as the input to the prediction module.
Simulation results indicate that removing the differencing
attention module leads to substantial performance degradation
across all evaluation metrics. This ﬁnding conﬁrms that the
non-stationary temporal dynamics introduced by the moving
target/CU exert a signiﬁcant adverse effect on predictive
beamforming design. Consequently, the differencing attention
module is crucial for mitigating these dynamics and enhancing
the integrated performance in communication, energy harvest-
ing, and sensing.
D. Effect of Number of Time Steps
Table III presents the ID, EH, and sensing performance
achieved by TSFusionNet under different historical window
TABLE III
PERFORMANCE EVALUATION VERSUS THE NUMBER OF TIME STEPS
UNDER DIFFERENT ANTENNA CONFIGURATIONS
lengths (ω∈{ 2, 3, 4, 5}) and antenna conﬁgurations ( NT =
NR∈{ 4× 4, 6× 6, 8× 8}) at Pt = 30 dBm. For the 4× 4
and 6×6 arrays, the ID and EH performance remains within a
narrow range asω varies, while CRLB shows moderate ﬂuctu-
ations. This observation indicates that the proposed temporal
fusion framework can capture the dominant channel evolution
patterns even with a short CSI history (e.g.,ω = 3). Increasing
ω mainly leads to limited performance reﬁnement, and the
overall system performance remains stable, demonstrating the
robustness of the temporal fusion and differencing attention
mechanism.
For the 8× 8 antenna conﬁguration, a clear odd-even
pattern can be observed. Speciﬁcally, odd time steps provide
consistently higher ID and EH performance together with
lower CRLB, whereas even time steps result in noticeable
degradation across all three metrics. This behavior can be
attributed to the interaction between temporal differencing
and the increased spatial degrees of freedom. With larger
antenna arrays, the beamforming design relies more heavily
on accurately capturing ﬁne-grained temporal variations of the
CSI, making it more sensitive to the quality of the temporal
representation. Consequently, an inappropriate differencing
depth may either weaken useful inter-slot correlations or
amplify noise components, thereby affecting both communi-
cation efﬁciency and sensing accuracy.
Overall, the results conﬁrm that the adopted setting ω = 5
achieves a stable and well-balanced performance across dif-
ferent antenna conﬁgurations and evaluation metrics.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

17176 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 8. Effect of different values of weight factor in terms of Pt =
10, 20, 30 dBm (a) ID/EH performance versus ρ; (b) rate-energy trade-off
visualization.
E. Effect of Weight Factor
In Fig. 8, we investigate the trade-off between the averaged
achievable rate and the averaged harvested energy by adjusting
the weight factor ρ in the loss function proposed in (23).
Comparative analyses are conducted under three different
transmit power values, i.e.,Pt = 10, 20, 30 dBm. As expected,
a higher value of ρ prioritizes communication performance,
leading to an increased communication rate at the expense of
harvested energy. Conversely, a lowerρ shifts the system focus
toward energy harvesting, which in turn causes a degradation
in communication performance. Notably, while increasing Pt
enhances the achievable performance for both communication
and energy harvesting across all values of ρ, the fundamen-
tal trade-off between rate and energy remains consistently
governed by the weight factor. A comprehensive visualiza-
tion of this trade-off under different Pt values is provided
in Fig. 8(b).
However, we observe that when ρ = 0 , the averaged
achievable rate remains consistently low and shows minimal
sensitivity to increases in Pt. This is because the predictive
beamforming design focuses solely on maximizing the total
harvested energy for all targets/CUs, neglecting the criti-
cal aspect of multi-target/CU interference management. The
resulting beams fail to spatially separate the data streams for
Fig. 9. Effect of different numbers of targets/CUs in terms of ρ =
0.2, 0.5, 0.8, at Pt = 30 dBm.
different targets/CUs, causing severe interference that degrades
communication performance, even as Pt increases.
F . Effect of Number of Targets/CUs
The impact of the number of targets/CUs on the SWIPT-
ISAC system is evaluated in Fig. 9 under different weight
factors, i.e., ρ = 0 .2, 0.5, 0.8, at Pt = 30 dBm. It is
observed that, regardless of the number of targets/CUs, both
ID and EH performance follow the trend identiﬁed in the
previous subsection. Speciﬁcally, a larger weight factorρ leads
to improved communication rate at the expense of reduced
harvested energy, which aligns with the fundamental trade-off
between communication and energy harvesting in the proposed
system.
Notably, as the number of targets/CUs increases, both the
ID and EH performance exhibit degradation. This phenomenon
can be attributed to the fundamental trade-off between com-
munication and energy harvesting, which is aggravated in
multi-target/CU scenarios. From a communication perspective,
the predictive beamforming strategy is designed to generate
strong, focused beams towards each target/CU to minimize
multi-target/CU interference, thereby maintaining a high com-
munication rate. Conversely, for energy harvesting, the same
multi-target/CU interference represents a potential source of
harvestable energy. As the number of targets/CUs increases,
the beamforming design must satisfy a more complex set of
constraints. To maintain sensing accuracy while maximizing
the weighted sum of the average achievable rate and harvested
energy, the beamformer needs to distribute its ﬁnite spatial
gain across an increasing number of directions. This nec-
essary distribution of spatial resources inherently diminishes
the achievable gain for any single objective. Consequently,
the solution space for the optimization problem becomes
more constrained, leading to a lower maximum value for the
weighted sum objective, thereby explaining the decreasing
trend in both ID and EH performance with an increasing
number of targets/CUs.
VI. C ONCLUSION
In this paper, we have presented an intelligent predictive
beamforming framework for SWIPT-ISAC systems in the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

ZHANG et al.: INTELLIGENT PREDICTIVE BEAMFORMING FOR LAE 17177
LAE wireless networks, addressing the fundamental trade-
off between achievable communication rate and harvested
energy under stringent sensing accuracy constraints. By lever-
aging historical CSI through the proposed TSFusionNet, our
approach eliminates the need for explicit channel predic-
tion and achieves real-time adaptability to non-stationary
channel dynamics. The integration of convolutional and recur-
rent layers with a differencing attention mechanism enables
robust spatial-temporal feature extraction, while the adaptive
penalty-based loss function ensures compliance with sensing
requirements without costly hyperparameter tuning. Simula-
tion results have demonstrated that TSFusionNet signiﬁcantly
outperforms conventional optimization and existing DL base-
lines in terms of rate-energy balance, sensing accuracy, and
computational efﬁciency. These results have validated the fea-
sibility of deploying predictive beamforming in LAE wireless
networks to support integrated communication, sensing, and
power transfer. Future research will explore extensions to
multi-cell scenarios, NLoS environments, and joint optimiza-
tion with resource allocation strategies to further enhance
system scalability and robustness.
APPENDIX
DERIVING FIM
In order to derive the CRLBs for motion parameters of the
k-th target/CU at the n-th time slot, we ﬁrst deﬁne
qn,k =f(mn,k) + un,k, (33)
where qn,k = [ˆrn,k, ˆτn,k, ˆγn,k]T , mn,k = [ dn,k,θn,k,
φn,k,νn,k]T , un,k = [ur,n,k,uτ,n,k,uγ,n,k]T , and f(·) is a set
of non-linear mapping deﬁned in (11)-(13). It is clear that qn,k
is a complex Gaussian distributed random vector with mean
f(mn,k) and covariance matrix Σn,k = diag[σ2r,σ 2τ,σ 2γ], and
therefore, we can have the following conditional probability
density function, that is
p(qn,k|mn,k) = 1π(Ns+2) det(Σn,k) (34)
×e−(qn,k−f (mn,k))
H
Σ−1n,k(qn,k−f (mn,k)).
Then, the FIM is given by the Jacobian as follows:
Jn,k = E



∂ lnp(qn,k|mn,k)
∂m∗n,k
(
∂ lnp(qn,k|mn,k)
∂m∗n,k
)H

=
(∂f (mn,k)
∂mn,k
)H
Σ−1n,k∂f (mn,k)∂mn,k , (35)
where
∂f (mn,k)
∂mn,k
=


0 ∂ ˆrn,k∂θn,k ∂ ˆrn,k∂φn,k 02
c 0 0 0
0 0 0 − 2λ

, (36)
and the details for calculating ∂ ˆrn,k∂θn,k and ∂ ˆrn,k∂φn,k can be foundas follows.
Given that
aNT(θn,k,φn,k) = aNT,x(θn,k,φn,k)⊗ aNT,y(θn,k,φn,k),
(37)
where [aNT,x(θn,k,φn,k)]l = e−jπl cosθn,k cosφn,k/√NT,x,
for l = 0, 1,..., (NT,x− 1), with NT,x being the number of
antenna elements on the x-axis of UPA; aNT,y(θn,k,φn,k) =
e−jπm sinθn,k cosφn,q/√NT,y, for m = 0, 1,..., (NT,y− 1)
with NT,y denoting the number of antenna elements on the
y-axis of UPA, we have
∂ˆrn,k
∂θn,k
=ςn,k
√
NRNT
×
(∂aNT,x (θn,k,φn,k)
∂θn,k ⊗ aNT,y(θn,k,φn,k)
+aNT,x(θn,k,φn,k)⊗
∂aNT,y (θn,k,φn,k)
∂θn,k
)H
fn,k,
(38)
∂ˆrn,k
∂φn,k
=ςn,k
√
NRNT
×
(∂aNT,x (θn,k,φn,k)
∂φn,k ⊗ aNT,y(θn,k,φn,k)
+aNT,x(θn,k,φn,k)⊗
∂aNT,y (θn,k,φn,k)
∂φn,k
)H
fn,k,
(39)
where
[∂aNT,x (θ,φ)
∂θ
]
l
= jπl sinθ cosφe−jπl cosθ cosφ√NT,x , (40a)
[∂aNT,y (θ,φ)
∂θ
]
m
=−jπm cosθ cosφe−jπm sinθ cosφ√NT,y , (40b)
[∂aNT,x (θ,φ)
∂φ
]
l
= jπl cosθ sinφe−jπl cosθ cosφ√NT,x , (40c)
[∂aNT,y (θ,φ)
∂φ
]
m
= jπm sinθ sinφe−jπm sinθ cosφ√NT,y . (40d)
REFERENCES
[1] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for
low-altitude economy: Coordinated transmit beamforming and UA V tra-
jectory design,” IEEE Trans. Commun. , vol. 73, no. 8, pp. 5832–5847,
Aug. 2025.
[2] X. Ye, Y . Mao, X. Yu, S. Sun, L. Fu, and J. Xu, “Integrated sensing and
communications for low-altitude economy: A deep reinforcement learn-
ing approach,” IEEE Trans. Wireless Commun. , vol. 25, pp. 351–367,
2026.
[3] Y . Wang et al., “Toward realization of low-altitude economy networks:
Core architecture, integrated technologies, and future directions,” IEEE
Trans. Cognit. Commun. Netw. , vol. 11, no. 5, pp. 2788–2820, Oct.
2025.
[4] R. Ma et al., “Simultaneous wireless information and power trans-
fer in IoT-based scenarios: Architectures, challenges, and prototype
validation,” IEEE Wireless Commun. , vol. 31, no. 5, pp. 272–278, Oct.
2024.
[5] Y . Chen, H. Hua, J. Xu, and D. W. K. Ng, “ISAC meets SWIPT:
Multi-functional wireless systems integrating sensing, communica-
tion, and powering,” IEEE Trans. Wireless Commun. , vol. 23, no. 8,
pp. 8264–8280, Aug. 2024.
[6] J. Wang et al., “Optimizing 6G integrated sensing and communica-
tions via expert networks,” IEEE Wireless Commun. , vol. 32, no. 5,
pp. 142–150, Oct. 2025.
[7] Y . Cui, F. Liu, X. Jing, and J. Mu, “Integrating sensing and communi-
cations for ubiquitous IoT: Applications, trends, and challenges,” IEEE
Netw., vol. 35, no. 5, pp. 158–167, Sep. 2021.
[8] X. Li et al., “Integrating sensing, communication, and power trans-
fer: From theory to practice,” IEEE Commun. Mag. , vol. 62, no. 9,
pp. 122–127, Sep. 2024.
[9] Y . Xu, D. Xu, and S. Song, “Sensing-assisted robust SWIPT for mobile
energy harvesting receivers in networked ISAC systems,” IEEE Trans.
Wireless Commun., vol. 24, no. 3, pp. 2094–2109, Mar. 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

17178 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[10] F. Liu, W. Yuan, C. Masouros, and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: Communication served by sensing,”
IEEE Trans. Wireless Commun. , vol. 19, no. 11, pp. 7704–7719, Nov.
2020.
[11] Z. Du et al., “Integrated sensing and communications for V2I
networks: Dynamic predictive beamforming for extended vehicle
targets,” IEEE Trans. Wireless Commun., vol. 22, no. 6, pp. 3612–3627,
Jun. 2023.
[12] B. Lee, A. C. Marcum, D. J. Love, and J. V . Krogmeier, “Fusing channel
and sensor measurements for enhancing predictive beamforming in UA V-
assisted massive MIMO communications,” IEEE Wireless Commun.
Lett., vol. 13, no. 3, pp. 869–873, Mar. 2024.
[13] D. Tse and P. Viswanath, Fundamentals of Wireless Communication .
Cambridge, MA, USA: Cambridge Univ. Press, 2005.
[14] J. Fan, Y . Wei, J. Tang, T. Liu, and K.-K. Wong, “Mobility-aware
predictive beamforming design in sensing-assisted SWIPT systems,”
IEEE Wireless Commun. Lett., vol. 14, no. 5, pp. 1476–1480, May 2025.
[15] J. Zhang et al., “Deep learning-empowered secure predictive beam-
forming design for integrated sensing and communications systems,”
IEEE Trans. Wireless Commun. , vol. 24, no. 10, pp. 8565–8580,
Oct. 2025.
[16] Z. Wang and V . W. S. Wong, “Deep learning for ISAC-enabled end-to-
end predictive beamforming in vehicular networks,” in Proc. IEEE Int.
Conf. Commun. , May 2023, pp. 5713–5718.
[17] X. Yu et al., “Learning-based predictive beamforming for secure ISAC
via IRS,” IEEE Trans. Commun. , vol. 73, no. 12, pp. 14304–14315,
Dec. 2025.
[18] C. B. Barneto, S. D. Liyanaarachchi, M. Heino, T. Riihonen, and
M. Valkama, “Full duplex Radio/Radar technology: The enabler for
advanced joint communication and sensing,” IEEE Wireless Commun. ,
vol. 28, no. 1, pp. 82–88, Feb. 2021.
[19] J. Mu, Y . Gong, F. Zhang, Y . Cui, F. Zheng, and X. Jing, “Integrated
sensing and communication-enabled predictive beamforming with deep
learning in vehicular networks,” IEEE Commun. Lett. , vol. 25, no. 10,
pp. 3301–3304, Oct. 2021.
[20] J. Li and P. Stoica, “MIMO radar with colocated antennas,” IEEE Signal
Process. Mag., vol. 24, no. 5, pp. 106–114, Sep. 2007.
[21] X. Zhang, W. Yuan, C. Liu, J. Wu, and D. W. K. Ng, “Predictive
beamforming for vehicles with complex behaviors in ISAC systems: A
deep learning approach,” IEEE J. Sel. Topics Signal Process. , vol. 18,
no. 5, pp. 828–841, Jul. 2024.
[22] T. Tang, P. Wang, C. Jie, P. Zhao, Z. Ren, and H. Zeng, “A time-
frequency synchronization method using dual-channel processing for
GNSS-based passive radar moving target detection,” in Proc. IEEE
IGARSS, Jul. 2024, pp. 6368–6371.
[23] Z. Zong, H. Feng, F. R. Yu, N. Zhao, T. Yang, and B. Hu,
“Optimal transceiver design for SWIPT in K-user MIMO interference
channels,” IEEE Trans. Wireless Commun., vol. 15, no. 1, pp. 430–445,
Jan. 2016.
[24] N. Garg, J. Zhang, and T. Ratnarajah, “Rate-energy balanced precoding
design for SWIPT based two-way relay systems,” IEEE J. Sel. Topics
Signal Process., vol. 15, no. 5, pp. 1228–1241, Aug. 2021.
[25] E. Telatar, “Capacity of multi-antenna Gaussian channels,” Eur . Trans.
Telecommun., vol. 10, no. 6, pp. 585–595, Nov. 1999.
[26] M. A. Richards, Fundamentals of Radar Signal Processing . New York,
NY , USA: McGraw-Hill, 2022.
[27] O. E. Ayach, R. W. Heath, S. Abu-Surra, S. Rajagopal, and Z. Pi,
“The capacity optimality of beam steering in large millimeter wave
MIMO systems,” in Proc. IEEE 13th Int. Workshop Signal Process.
Adv. Wireless Commun. (SPA WC), Jun. 2012, pp. 100–104.
[28] C. Liu et al., “Learning-based predictive beamforming for integrated
sensing and communication in vehicular networks,” IEEE J. Sel. Areas
Commun., vol. 40, no. 8, pp. 2317–2334, Aug. 2022.
[29] J. Bechter, M. Rameez, and C. Waldschmidt, “Analytical and experimen-
tal investigations on mitigation of interference in a DBF MIMO radar,”
IEEE Trans. Microw. Theory Techn., vol. 65, no. 5, pp. 1727–1734, May
2017.
[30] S. M. Kay, Fundamentals of Statistical Signal Processing: Estimation
Theory, vol. 1. Englewood Cliffs, NJ, USA: Prentice-Hall, 1998.
[31] D. Zhang, A. Li, M. Shirvanimoghaddam, P. Cheng, Y . Li, and
B. Vucetic, “Codebook-based training beam sequence design for
millimeter-wave tracking systems,” IEEE Trans. Wireless Commun. ,
vol. 18, no. 11, pp. 5333–5349, Nov. 2019.
[32] E. Boshkovska, D. W. K. Ng, N. Zlatanov, and R. Schober, “Practical
non-linear energy harvesting model and resource allocation for SWIPT
systems,” IEEE Commun. Lett. , vol. 19, no. 12, pp. 2082–2085, Dec.
2015.
[33] I. Rasheed and H. Mostafa, “DeepBeam: A multi-agent deep reinforce-
ment learning framework for predictive mmWave beam management in
dynamic V2X networks,” IEEE Trans. V eh. Technol. , vol. 74, no. 11,
pp. 17854–17864, Nov. 2025.
[34] Y . Liu, S. Zhang, X. Li, Y . Huang, Y . Fang, and H. Cao, “Deep reinforce-
ment learning-based beamforming design in ISAC-assisted vehicular
networks,” in Proc. IEEE Wireless Commun. Netw. Conf. (WCNC) , Apr.
2024, pp. 1–6.
[35] J. Du, H. Ma, Z. Yu, X. Li, S. Mumtaz, and C. Yuen, “DL-based
ISAC via tensor analysis in massive MIMO-OFDM systems with spatial-
frequency wideband effects,” IEEE Internet Things J. , vol. 12, no. 5,
pp. 5093–5108, Mar. 2024.
[36] Z. Qiao, J. Xue, J. Zhang, F. A. Khan, and J. S. Thompson,
“Implicit layer-empowered deep learning networks for 6G adaptive
channel estimation,” IEEE Trans. Commun. , vol. 74, pp. 2190–2204,
Jan. 2026.
[37] B. De Filippo, C. Amatetti, and A. Vanelli-Coralli, “Uplink OFDM chan-
nel prediction with hybrid CNN-LSTM for 6G non-terrestrial networks,”
in Proc. Joint Eur . Conf. Netw. Commun. 6G Summit (EuCNC/6G
Summit), Jun. 2025, pp. 7–12.
[38] G. Liu, Z. Hu, L. Wang, J. Xue, H. Yin, and D. Gesbert,
“Spatio-temporal neural network for channel prediction in massive
MIMO-OFDM systems,” IEEE Trans. Commun. , vol. 70, no. 12,
pp. 8003–8016, Dec. 2022.
[39] Y . Sang, K. Ma, Z. Wang, and S. Chen, “Dual-band super-resolution
channel prediction in high-mobility MIMO systems,” IEEE Trans.
Commun., vol. 73, no. 6, pp. 4409–4424, Jun. 2025.
[40] G. Liu, Z. Hu, L. Wang, H. Zhang, J. Xue, and M. Matthaiou,
“A hypernetwork based framework for non-stationary channel
prediction,” IEEE Trans. V eh. Technol., vol. 73, no. 6, pp. 8338–8351,
Jun. 2024.
[41] W. Jin, J. Zhang, C.-K. Wen, and S. Jin, “Model-driven deep learning for
hybrid precoding in millimeter wave MU-MIMO system,” IEEE Trans.
Commun., vol. 71, no. 10, pp. 5862–5876, Oct. 2023.
[42] M. Zhu, T.-H. Chang, and M. Hong, “Learning to beamform in het-
erogeneous massive MIMO networks,” IEEE Trans. Wireless Commun. ,
vol. 22, no. 7, pp. 4901–4915, Jul. 2023.
[43] H. Zheng, W. Li, L. Tian, C. Xu, F. Huang, and J. Zhang, “Path loss
models for urban macro cell scenario at 3.35, 4.9 and 5.4 GHz,” Proc.
IEEE PIMRC , pp. 2229–2233, Aug. 2015.
[44] E. Boshkovska, D. W. K. Ng, N. Zlatanov, A. Koelpin, and R. Schober,
“Robust resource allocation for MIMO wireless powered communication
networks based on a non-linear EH model,” IEEE Trans. Commun. ,
vol. 65, no. 5, pp. 1984–1999, May 2017.
[45] S. Boyd, N. Parikh, E. Chu, B. Peleato, and J. Eckstein, “Distributed
optimization and statistical learning via the alternating direction method
of multipliers,” F ound. Trends Mach. Learn. , vol. 3, no. 1, pp. 1–122,
Jul. 2011.
Junkai Zhang (Member, IEEE) received the
B.Eng. degree in communication engineering from
Shenyang Ligong University, Shenyang, China, in
2018, the M.Sc. degree (Distinction) in signal pro-
cessing and communications from The University of
Edinburgh, Edinburgh, U.K., in 2019, and the Ph.D.
degree in engineering (wireless communications)
from the Institute for Imaging, Data and Commu-
nications, The University of Edinburgh, in 2023. He
is currently with the School of Mathematics and
Statistics, Xi’an Jiaotong University, Xi’an, China,
as an Assistant Professor. His research interests include 6G AI-based wireless
communications, full-duplex radio, and integrated sensing and communica-
tions (ISAC).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

ZHANG et al.: INTELLIGENT PREDICTIVE BEAMFORMING FOR LAE 17179
Faheem A. Khan (Member, IEEE) received the
bachelor’s degree in electronics engineering from
Aligarh Muslim University, the master’s degree
in communication and radar engineering from
Indian Institute of Technology Delhi, and the Ph.D.
degree in electrical and electronic engineering from
Queen’s University Belfast in 2012. He is currently a
Reader of electronic engineering with the School of
Computing and Engineering, University of Hudders-
ﬁeld. Before joining the University of Huddersﬁeld,
as a Lecturer, in 2016, he was a Research Associate
of wireless communications and signal processing with the Institute for
Imaging, Data and Communications, The University of Edinburgh. During
this time, he contributed signiﬁcantly to several EU and EPSRC-funded
research projects, both in technical development and project management.
His current research interests include spectrum sharing and management
for beyond 5G and 6G wireless networks, AI/deep learning applications
in wireless communications, integrated sensing and communication (ISAC),
reconﬁgurable intelligent surfaces (RIS) for 6G communications, and the
Internet of Things (IoT) networks. He is a fellow of the Higher Education
Academy (FHEA).
Zhiqiang Wei (Member, IEEE) received the B.E.
degree in information engineering from Northwest-
ern Polytechnical University (NPU), Xi’an, China, in
2012, and the Ph.D. degree in electrical engineering
and telecommunications from the University of New
South Wales (UNSW), Sydney, Australia, in 2019.
From 2019 to 2020, he was a Post-Doctoral Research
Fellow with UNSW. From 2021 to 2022, he was
a Humboldt Post-Doctoral Research Fellow with
the Institute for Digital Communications, Friedrich-
Alexander University Erlangen-Nuremberg (FAU),
Erlangen, Germany. He is currently a Professor with the School of Math-
ematics and Statistics, Xi’an Jiaotong University, Xi’an. He also co-authored
the IEEE ComSoc Best Readings on OTFS and Delay Doppler Signal
Processing. His research interests include delay-Doppler communications,
resource allocation optimization, and statistical and array signal processing.
He received the Best Paper Award at the IEEE ICC 2018 and IEEE WCNC
2023. He was the Organizer/Chair for several workshops and tutorials on
related topics of orthogonal time frequency space (OTFS) in IEEE ﬂagship
conferences, including IEEE ICC, IEEE WCNC, IEEE VTC, and IEEE ICCC.
He is the Founding Co-Chair (publications) of the IEEE ComSoc Special
Interest Group on OTFS (OTFS-SIG). He has been listed in the World’s
Top 2% Scientists by Stanford University for citation impact, since 2021.
He is currently an editor for IEEE T RANSACTIONS ON COMMUNICATIONS ,
IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS , and IEEE O PEN
JOURNAL OF THE COMMUNICATIONS SOCIETY .
Jiang Xue (Senior Member, IEEE) received the B.S.
degree in information and computing science from
Xi’an Jiaotong University, Xi’an, China, in 2005, the
M.S. degree in applied mathematics from Lanzhou
University, China, in 2008, and the M.S. degree from
Uppsala University, Sweden, in 2009, and the Ph.D.
degree in electrical and electronic engineering from
ECIT, Queen’s University of Belfast, U.K., in 2012.
From 2013 to 2017, he was a Research Fellow with
The University of Edinburgh, U.K. Since 2017, he
has been with the National Engineering Laboratory
for Big Data Analytics, Xi’an International Academy for Mathematics and
Mathematical Technology, School of Mathematics and Statistics, Xi’an Jiao-
tong University. He is supported by the Zhongying Young Scholars Project.
His research interests include the interdisciplinary areas of machine learning,
signal processing, wireless communications and their applications.
Christos Masouros (Fellow, IEEE) received the
Diploma degree in electrical and computer engi-
neering from the University of Patras, Greece, in
2004, and the M.Sc. (by research) and Ph.D. degrees
in electrical and electronic engineering from The
University of Manchester, U.K., in 2006 and 2009,
respectively. In 2008, he was a Research Intern
with Philips Research Laboratories, U.K. From 2009
to 2010, he was a Research Associate with The
University of Manchester. From 2010 to 2012, he
was also a Research Fellow with Queen’s University
Belfast. In 2012, he joined University College London, as a Lecturer.
He has held a Royal Academy of Engineering Research Fellowship from
2011 to 2016. He is currently a Full Professor with the Information and
Communications Engineering Research Group, Department of Electrical and
Electronic Engineering, University College London. His research interests
include wireless communications and signal processing, with a particular
focus on green communications, large scale antenna systems, cognitive
radio, interference mitigation techniques for MIMO, and multicarrier com-
munications. He is currently an Elected Member of the EURASIP SAT
Committee on Signal Processing for Communications and Networking. He
was a recipient of the Best Paper Award at the IEEE GlobeCom 2015 and
IEEE WCNC 2019 conferences. He has been recognized as an Exemplary
Editor of IEEE C OMMUNICATIONS LETTERS and as an Exemplary Reviewer
of IEEE T RANSACTIONS ON COMMUNICATIONS . He is an Editor of IEEE
TRANSACTIONS ON COMMUNICATIONS and IEEE T RANSACTIONS ON
WIRELESS COMMUNICATIONS . He has been an Associate Editor of IEEE
COMMUNICATIONS LETTERS and a Guest Editor of IEEE J OURNAL ON
SELECTED TOPICS IN SIGNAL PROCESSING issues “Exploiting Interference
Toward Energy Efﬁcient and Secure Wireless Communications” and “Hybrid
Analog/Digital Signal Processing for Hardware-Efﬁcient Large Scale Antenna
Arrays”.
Dusit Niyato (Fellow, IEEE) received the B.Eng.
degree from the King Mongkut’s Institute of Tech-
nology Ladkrabang (KMITL), Thailand, and the
Ph.D. degree in electrical and computer engineering
from the University of Manitoba, Canada. He is
currently a Professor with the College of Computing
and Data Science, Nanyang Technological Univer-
sity, Singapore. His research interests include mobile
generative AI, edge general intelligence, quantum
computing and networking, and incentive mecha-
nism design.
Zongben Xu received the Ph.D. degree in math-
ematics from Xi’an Jiaotong University, China, in
1987. He was the Vice President of Xi’an Jiaotong
University from 2003 to 2014. He is currently the
Chief Scientist of National Basic Research Program
of China (973 Project) and the Director of the
Institute for Information and System Sciences of
the university. He delivered a 45 minute talk on the
International Congress of Mathematicians 2010. His
current research interests include intelligent infor-
mation processing and applied mathematics. He was
elected as a member of Chinese Academy of Science in 2011. He is the
Owner of the Tan Kan Kee Science Award in Science Technology in 2018,
the National Natural Science Award of China in 2007, the National Award
on Scientiﬁc and Technological Advances of China in 2011, the CSIAM
Su Buchin Applied Mathematics Prize in 2008, and ITIQAM Richard Price
Award.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:06:23 UTC from IEEE Xplore.  Restrictions apply.
