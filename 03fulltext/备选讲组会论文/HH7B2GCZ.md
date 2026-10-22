---
type: literature-fulltext
title: "Movable Antenna-Aided Near-Field Integrated Sensing and Communication"
zotero_key: "HH7B2GCZ"
pdf_key: "V97L9DTS"
doi: "10.1109/TWC.2025.3584833"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Movable Antenna-Aided Near-Field Integrated Sensing and Communication.md"
fulltext_path: "03fulltext/备选讲组会论文/HH7B2GCZ.md"
zotero_item: "zotero://select/library/items/HH7B2GCZ"
zotero_pdf: "zotero://open-pdf/library/items/V97L9DTS"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Movable Antenna-Aided Near-Field Integrated Sensing and Communication

> PDF 原文逐页文本抽取；来源文件 SHA-256：`a1b1bd7755ad80b352f3b8b69189f6aa6951d3ab1eadc64f884ae2a18ab9d5b7`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 493
Movable Antenna-Aided Near-Field Integrated
Sensing and Communication
Jingze Ding
 , Graduate Student Member , IEEE , Zijian Zhou
 , Member , IEEE, Xiaodan Shao
 , Member , IEEE,
Bingli Jiao
 , Senior Member , IEEE, and Rui Zhang
 , Fellow, IEEE
Abstract—Integrated sensing and communication (ISAC) is
emerging as a pivotal technology for next-generation wire-
less networks. However, existing ISAC systems are based on
ﬁxed-position antennas (FPAs), which inevitably incur a loss
in performance when balancing the trade-off between sensing
and communication. Movable antenna (MA) technology offers
promising potential to enhance ISAC performance by enabling
ﬂexible antenna movement. Nevertheless, exploiting more spatial
channel variations requires larger antenna moving regions, which
may invalidate the conventional far-ﬁeld assumption for channels
between transceivers. Therefore, this paper utilizes the MA to
enhance sensing and communication capabilities in near-ﬁeld
ISAC systems, where a full-duplex base station (BS) is equipped
with multiple transmit and receive MAs movable in large-size
regions to simultaneously sense multiple targets and serve multi-
ple uplink (UL) and downlink (DL) users for communication. We
aim to maximize the weighted sum of sensing and communication
rates (WSR) by jointly designing the transmit beamformers,
sensing signal covariance matrices, receive beamformers, and
MA positions at the BS, as well as the UL power allocation.
The resulting optimization problem is challenging to solve. Thus,
we propose an efﬁcient two-layer random position (RP) algorithm
to tackle it. In addition, to reduce movement delay and cost, we
design an antenna position matching (APM) algorithm based
Received 26 December 2024; revised 10 April 2025 and 25 June 2025;
accepted 26 June 2025. Date of publication 10 July 2025; date of current
version 22 December 2025. This work was supported in part by the Project
of General Administration of Customs of the People’s Republic of China
under Grant 2024HK290, in part by Guangzhou Municipal Science and
Technology Project under Grant 2023B04J0011 and Grant 2025B04J0038,
in part by Guangdong Provincial Key Laboratory of Big Data Computing,
in part by the National Natural Science Foundation of China under Grant
62331022, in part by the 2022 Stable Research Program of Higher Education
of China under Grant 20220817144726001, and in part by Guangdong Major
Project of Basic and Applied Basic Research under Grant 2023B0303000001.
The associate editor coordinating the review of this article and approving it
for publication was G. Interdonato. (Corresponding authors: Zijian Zhou;
Rui Zhang.)
Jingze Ding is with the School of Electronics, Peking University, Beijing
100871, China (e-mail: djz@stu.pku.edu.cn).
Zijian Zhou is with the School of Science and Engineering, The
Chinese University of Hong Kong, Shenzhen 518172, China (e-mail:
zijianzhou@link.cuhk.edu.cn).
Xiaodan Shao is with the Department of Electrical and Computer Engi-
neering, University of Waterloo, Waterloo, ON N2L 3G1, Canada (e-mail:
x6shao@uwaterloo.ca).
Bingli Jiao is with the School of Computing and Artiﬁcial Intelligence,
Fuyao University of Science and Technology, Fuzhou 350109, China, and
also with the School of Electronics, Peking University, Beijing 100871, China
(e-mail: jiaobl@pku.edu.cn).
Rui Zhang is with the School of Science and Engineering, Shenzhen
Research Institute of Big Data, The Chinese University of Hong Kong,
Shenzhen 518172, China, and also with the Department of Electrical and
Computer Engineering, National University of Singapore, Singapore 117583
(e-mail: rzhang@cuhk.edu.cn).
Digital Object Identiﬁer 10.1109/TWC.2025.3584833
on the greedy strategy to minimize the total MA movement
distance. Extensive simulation results demonstrate the substantial
performance improvement achieved by deploying MAs in near-
ﬁeld ISAC systems. Moreover, the results show the effectiveness of
the proposed APM algorithm in reducing the antenna movement
distance, which is helpful for energy saving and time overhead
reduction for MA-aided near-ﬁeld ISAC systems with large
moving regions.
Index Terms —Near-ﬁeld, integrated sensing and commu-
nication (ISAC), movable antenna (MA), antenna position
optimization.
I. I NTRODUCTION
I
NTEGRATED sensing and communication (ISAC) has
been considered as a promising technology for next-
generation wireless networks because of its unique ability
to efﬁciently reuse time, frequency, power, and hardware
resources for both sensing and communication tasks at the
same time [1], [2]. In addition, the continuous and aggressive
utilization of frequency spectrum, such as millimeter-wave
(mmWave), in wireless communications has resulted in spec-
trum overlap with conventional radar systems, thereby driving
the need for the development of ISAC frameworks [3].
In the ISAC system, one key challenge is to design dual-
functional signals that can achieve both the sensing and
communication tasks. It is worth noting that multiple-input
multiple-output (MIMO) technology provides a viable solu-
tion to this issue by exploiting spatial degrees of freedom
(DoFs) through beamforming design. Speciﬁcally, MIMO-
based ISAC systems, equipped with multiple antennas at both
the transmitter and receiver, can employ beamforming to steer
the sensing/communication signals toward the desired tar-
gets/users, which reduces interference in undesired directions
and enhances the quality of ISAC performance [4]. Moti-
vated by this, substantial works have explored beamforming
design in MIMO-based wireless sensing and communication
systems [5], [6], [7], [8], [9], [10], [11]. However, most
existing ISAC systems focus on either uplink (UL) or down-
link (DL) communication, which cannot simultaneously meet
both communication demands, thus incurring reduced system
throughput. To address this limitation, full-duplex ISAC sys-
tems have been proposed [12], which enable simultaneous
transmission and reception of sensing/communication signals
over the same frequency. The full-duplex operation improves
both sensing and communication capabilities through the efﬁ-
cient reuse of time-frequency resources. In terms of sensing,
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

494 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
the entire frequency bands are available to detect targets so
that an enhanced radar performance is achieved. From the
communication perspective, there is a signiﬁcant improvement
in spectral efﬁciency [12]. Accordingly, full-duplex ISAC sys-
tems have garnered signiﬁcant attention [13], [14], [15]. The
authors in [13] investigated the joint secure transceiver design
for the full-duplex ISAC system, where the base station (BS)
simultaneously performs target tracking and communicates
with the UL and DL users. The authors in [14] studied
the joint optimization of a full-duplex communication-based
ISAC system under the criteria of transmit power minimiza-
tion and sum-rate maximization. The results demonstrated
the performance gains in terms of both the power and the
spectral efﬁciency compared to the conventional half-duplex
ISAC. More comprehensively, the authors in [15] compared
the different advantages of ISAC systems operating in full-
duplex and half-duplex modes.
However, conventional ISAC architectures mentioned above
typically utilize ﬁxed-position antenna (FPA) arrays. The
static antenna placement in FPA systems prevents the full
exploitation of the wireless channel spatial variation in a
given region, due to the lack of local antenna mobility. This
limitation hinders the ability to fully optimize spatial diversity
and multiplexing performance in sensing and communication
tasks, thus constraining the overall potential of ISAC systems
[16]. Fortunately, movable antenna (MA) and six-dimensional
MA (6DMA) technologies have recently been proposed to
address this limitation [17], [18], [19], [20], [21], [22], [23],
[24], [25]. Speciﬁcally, MA technology can adjust antenna
positions with ﬁxed antenna rotation to effectively provide
customized sensing and communication services [17], [18],
[19], [20]. More generally, 6DMA technology can incorporate
the DoFs in the three-dimensional (3D) position and 3D
orientation/rotation of antennas, which can adaptively allocate
antenna resources based on the long-term/statistical user distri-
bution to improve network capacity [21], [22], [23], [24], [25].
The various wireless sensing/ISAC systems applying MA have
been extensively studied [26], [27], [28]. The authors in [26]
analyzed the performance of a new wireless sensing system
equipped with a one-dimensional (1D) or two-dimensional
(2D) array. The authors in [27] minimized the Cram ´er-Rao
bound (CRB) through the joint beamforming design and MA
position optimization. Moreover, the authors in [28] proposed
a 6DMA-aided wireless sensing system and compared it with
MA for both directive and isotropic antenna radiation patterns.
In addition, based on previous studies of MA-aided full-
duplex wireless communication systems [29], [30], [31], [32],
the full-duplex ISAC system aided by MAs has begun to
attract the attention of researchers [33], [34], [35]. The authors
in [33] focused on maximizing the communication rate and
sensing mutual information in a monostatic MA-ISAC system.
The authors in [34] investigated the joint discrete antenna
positioning and beamforming optimization in MA-enabled
full-duplex ISAC networks. The authors in [35] considered
the joint active beamforming and position coefﬁcients design
problem in an MA-aided networked full-duplex ISAC system
that accomplishes radar sensing as well as UL and DL
communication capabilities concurrently.
While the advantages of MA in ISAC systems have been
validated, existing studies mainly focus on far-ﬁeld ISAC
systems. In contrast, the investigation of MA-aided ISAC
systems under near-ﬁeld propagation conditions remains in its
infancy [36], [37], [38]. Generally, to accommodate the free
movement of multiple MAs and maximize spatial DoFs, larger
antenna moving regions are required [39], [40]. Hence, the MA
system usually has a larger aperture size compared to conven-
tional FPA-based systems. Besides, to meet the ever-growing
demands for sensing and communication performance, future
ISAC systems are expected to operate in high-frequency bands
[41]. The above two reasons render the conventional far-
ﬁeld assumption commonly adopted in previous MA-aided
ISAC systems invalid. As a result, it is essential to explore
the potential advantages that MA can offer to ISAC systems
in near-ﬁeld scenarios. It is noteworthy that the additional
distance dimension in near-ﬁeld ISAC compared to far-ﬁeld
ISAC allows the system to provide sensing/communication
services for multiple targets/users through joint resolutions
in both the angle and distance domains [42], [43]. However,
to the best of the authors’ knowledge, there has been no
prior work on designing MA-aided full-duplex ISAC systems
under near-ﬁeld channel conditions. Therefore, in this paper,
we investigate MA-aided near-ﬁeld ISAC systems. The main
contributions of this paper are summarized as follows:
1) We propose an MA-aided ISAC system that employs
the near-ﬁeld spherical wave channel model, where the
dual-functional full-duplex BS is equipped with mul-
tiple transmit and receive MAs movable in large-size
regions to simultaneously sense multiple targets and
serve multiple UL and DL users for communication. To
balance sensing accuracy and communication efﬁciency,
we aim to maximize the weighted sum of sensing and
communication rates (WSR) by jointly designing the
transmit beamformers, sensing signal covariance matri-
ces, receive beamformers, and MA positions at the BS,
as well as the UL power allocation.
2) We propose a two-layer random position (RP) algorithm
to solve the formulated non-convex optimization prob-
lem with highly-coupled variables. In the inner-layer, for
a given MA position, we iteratively update the remaining
optimization variables based on the alternating optimiza-
tion (AO) framework. In the outer-layer, we randomly
assign multiple pairs of transmit and receive MA posi-
tions and select the pair that maximizes the WSR.
Moreover, to reduce the overhead associated with the
real-time movement of multiple MAs within the large-
size moving region, we propose an antenna position
matching (APM) algorithm that effectively minimizes
the total MA movement distance.
3) We conduct extensive simulations to validate the advan-
tages of MA-aided near-ﬁeld ISAC systems and the
effectiveness of the proposed algorithms. The results
demonstrate that the MA-aided ISAC system outper-
forms the ISAC system based on FPAs due to the
additional DoF introduced by antenna position opti-
mization. In addition, a larger moving region for MAs
increases the equivalent array aperture, thus providing an
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

DING et al.: MOV ABLE ANTENNA-AIDED NEAR-FIELD INTEGRATED SENSING AND COMMUNICATION 495
Fig. 1. Illustration of the proposed MA-aided near-ﬁeld ISAC system.
efﬁcient way to enlarge the near-ﬁeld region of ISAC
systems without increasing the number of antennas,
which facilitates multi-location beamfocusing. Further-
more, the proposed APM algorithm effectively reduces
the total MA movement distance, which signiﬁcantly
reduces the energy consumption and time overhead for
antenna movement in practical systems.
The rest of this paper is organized as follows. Section II
introduces the system model and the optimization problem
for the proposed system. In Section III, we propose the
two-layer RP algorithm and APM algorithm to solve the
optimization problem and minimize the total MA movement
distance, respectively. Next, simulation results and discussions
are provided in Section IV. Finally, this paper is concluded in
Section V.
Notation: a/A, a, A, and A denote a scalar, a vector, a
matrix, and a set, respectively. A! represents the factorial of
positive integer A. A ≽ 0 indicates that A is a positive
semideﬁnite matrix. (·)T , (·)H, ‖·‖2, |·|, ‖·‖F , Tr{·}, and
Rank{·} denote the transpose, conjugate transpose, Euclidean
norm, absolute value, Frobenius matrix norm, trace, and rank,
respectively. CM×N and RM×N are the sets for complex and
real matrices of M×N dimensions, respectively. IN is the
identity matrix of order N.CN (0, Λ) represents the circularly
symmetric complex Gaussian (CSCG) distribution with mean
zero and covariance matrix Λ.A\B denotes the subtraction
of setB from setA.
II. S YSTEM MODEL AND PROBLEM FORMULATION
Consider an MA-aided near-ﬁeld ISAC system as shown
in Fig. 1, where a dual-functional full-duplex BS equipped
with two MA arrays transmits the DL ISAC signal and
receives the UL communication signal from J single-FPA half-
duplex UL users, along with the reﬂected ISAC signal from
sensing targets, via the same time-frequency resource. The DL
ISAC signal is transmitted from the N-element MA array to
simultaneously communicate with K single-FPA half-duplex
DL users and detect L point sensing targets. The sensing echo
signal and the UL communication signal are received at the BS
through the receive MA array equipped with M elements. Each
transmit or receive MA can move freely within its designated
transmit or receive region, i.e., Ct orCr, respectively. Without
loss of generality, we assume thatCt andCr are square regions
with the same side length A. Generally, the boundary between
near-ﬁeld and far-ﬁeld can be determined by the Rayleigh
distance [41]. For the considered MA-aided ISAC system, the
Rayleigh distance depends on the size of the moving region
and is deﬁned as 4A2/λ, where λ is the carrier wavelength.
We assume that the targets and users are located within the
BS’s near-ﬁeld region, which implies that their distances from
the BS are less than 4A2/λ.
A. Channel Model
We consider the quasi-static 1 near-ﬁeld spherical wave
channel model [39], [40] for the self-interference (SI) channel,
communication channel, and sensing channel. 2 Since these
channels can be actively reconﬁgured through MA movement,
we establish a global Cartesian coordinate system o−xyz
at the BS to describe the MA positions. The reference point
between the transmit and receive regions is deﬁned as origin
o, where axes x and y are deﬁned as the horizontal and vertical
directions in the MA array plane, respectively, and axis z is
perpendicular to the array plane (see Fig. 1). The coordinates
of N transmit MAs and M receive MAs are described by
t =
[
tT1,..., tTN]T ∈ R3N×1 and r = [rT1,..., rTM]T ∈
R3M×1, where tn = [xtn,y tn, 0]T ∈ Ct (1≤ n≤ N) and
rm = [xrm,y rm, 0]T ∈C r (1≤ m≤ M), respectively. The
coordinates of UL user j (j∈J ={1,...,J }), DL user k
(k∈K ={1,...,K }), and target l (l∈L ={1,...,L })
are denoted as qUj∈ R3×1, qDk∈ R3×1, and qSl∈ R3×1,
respectively.
In full-duplex systems, the SI signal must be signiﬁcantly
suppressed through effective SI cancellation techniques. Typ-
ically, the SI cancellation can be achieved at three stages:
passive antenna suppression, active analog cancellation at
the radio frequency level, and digital SI cancellation at the
baseband level 3 [44]. Therefore, we deﬁne 0 < ρSI ≪ 1
as the SI loss coefﬁcient, which characterizes the overall
effectiveness of the three-stage SI cancellation. Based on
the uniform-power distance, the channel models suitable for
characterizing signal propagation in near-ﬁeld scenarios can
be categorized into the non-uniform spherical wave (NUSW)
model and the uniform spherical wave (USW) model [41]. In
the NUSW model, the propagation distance is shorter than
1In this paper, the proposed MA-aided near-ﬁeld ISAC system is designed
for scenarios with slow-fading propagation. For fast-fading channels, the MA
positions can be optimized using the two-timescale optimization scheme [40]
based on statistical channel state information (CSI) rather than instantaneous
CSI to avoid performance degradation caused by CSI variations during MA
movement.
2In typical near-ﬁeld scenarios, the line-of-sight (LoS) path signiﬁcantly
dominates the non-LoS (NLoS) paths and thus the latter are negligible.
3Since the analog and digital SI cancellations can actively adapt to channel
variations [31], the impact of SI channel ﬂuctuations on their performance is
neglected in this paper.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

496 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
the uniform-power distance. As a result, the variations in
channel gain become non-negligible. In contrast, when the
propagation distance exceeds the uniform-power distance in
the USW model, the channel gains are approximately uniform.
Without loss of generality, we adopt the USW model. Thus,
the SI channel is given by
HSI (t, r)
=ρSI


ej 2πλ‖t1−r1‖2 ... e j 2πλ‖tN−r1‖2
... ... ...
ej 2πλ‖t1−rM‖2 ... e j 2πλ‖tN−rM‖2

∈ CM×N.
(1)
The DL user k’s and UL user j’s communication channels can
be respectively expressed as the functions of the transmit and
receive MAs’ position vectors, i.e.,
hk (t)=ρDk
[
ej 2πλ‖t1−qDk‖2,...,e j 2πλ‖tN−qDk‖2]T∈ CN×1,
(2)
fj (r)=ρUj
[
ej 2πλ‖r1−qUj‖2,...,e j 2πλ‖rM−qUj‖2]T∈ CM×1,
(3)
where ρDk and ρUj represent the corresponding path loss. 4
For the sensing channel of target l, we denote the transmit
near-ﬁeld response vector by
gt,l (t) =
[
ej 2πλ‖t1−qSl‖2,...,e j 2πλ‖tN−qSl‖2]T∈ CN×1,
(4)
and similarly denote by
gr,l (r) =
[
ej 2πλ‖r1−qSl‖2,...,e j 2πλ‖rM−qSl‖2]T∈ CM×1,
(5)
the receive near-ﬁeld response vector. The target l’s sensing
channel is thus given by Gl (t, r) = ρSlgr,l (r) gt,l (t)H ∈
CM×N , where ρSl is the round-trip channel coefﬁcient deter-
mined by the path loss and the radar cross-section of the
target. Following [8], [9], [10], and [14], we assume that
ρSl and qSl are known or previously estimated at the BS
for designing the best suitable sensing waveform to detect
this speciﬁc target of interest, i.e., target l. It is worth noting
that the assumption of known ρSl and qSl is idealized and
mainly serves to reveal the fundamental performance of MA-
aided near-ﬁeld ISAC systems. In practice, such parameters are
usually unavailable a priori and must be estimated via previous
observations [45], [46]. As a future extension, robust designs
that account for the uncertainty of the sensing channel can be
developed. Speciﬁcally, the CSI uncertainty of sensing channel
Gl can be modeled based on a deterministic model [47], i.e.,
Gl = ˆGl + ∆Gl, where ˆGl is the CSI estimate and ∆Gl
represents the unknown channel uncertainty. The continuous
setGl =
{
Gl∈ CM×N :‖∆Gl‖F≤εl} contains all possible
channel uncertainties with bounded magnitude εl. The system
design with ∆Gl∈G l involves inﬁnitely many constraints due
to the continuity of the CSI uncertainty set. To enable efﬁcient
4To provide a performance upper bound for realistic scenarios and robust
designs, this paper assumes that the CSI of HSI, hk, and fj is perfectly
available at the full-duplex BS.
optimization, these constraints can be equivalently transformed
into linear matrix inequality (LMI) constraints using the S-
procedure [48].
B. Signal Model
We ﬁrst focus on the DL ISAC signal used for simultaneous
sensing and DL multi-user communication via N-element MA
array beamforming, which is expressed as
x =
∑
l∈L
sl +
∑
k∈K
wkdDk∈ CN×1, (6)
where wk ∈ CN×1 is the beamformer of DL user k and
dDk is the corresponding DL signal with normalized power,
i.e., E
{
|dDk|2
}
= 1 . sl ∈ CN×1 is the dedicated sens-
ing signal for target l with the covariance matrix Sl =
E
{
slsHl }∈ CN×N . Here, we assume that the signals dDk
and sl are independent of each other. In covariance-based
design approaches for MIMO radar systems, the covariance
matrix of the waveform is considered instead of the entire
waveform [9]. Therefore, we focus on the optimization of Sl
in the subsequent analysis. Once Sl is determined, a dedicated
sensing signal sl with Sl as its covariance matrix can be
synthesized accordingly [49]. It should be noted that the syn-
thesized waveform may not satisfy all practical requirements
of a real-world radar system, such as the constant-modulus
property. The topic of synthesizing practical sensing signals
with a given covariance matrix for MA-aided near-ﬁeld ISAC
systems is left for future research. The received signal at DL
user k is given by
yk = hHk wkdDk
| {z }
Desired signal
+
∑
i∈K\k
hHk widDi
| {z }
Multi−user interference
+
∑
l∈L
hHk sl
| {z }
Sensing signal
+nk,
(7)
where nk∼CN
(
0,σ 2k) represents the additive white Gaus-
sian noise (AWGN) with zero mean and variance σ2k. In (7),
the co-channel interference from UL to DL users is assumed
to be negligible due to the limited transmit power of UL users
and the severe attenuation of high-frequency signals that are
considered in this paper.
As the full-duplex BS transmits the DL ISAC signal, it
simultaneously receives the UL communication signal and the
target reﬂection. Denote the signal from UL user j by dUj ,
which satisﬁes E
{⏐⏐dUj⏐⏐2} = 1 . The received signal at the
full-duplex BS can be expressed as
yBS =
∑
j∈J
fj
√pjdUj
| {z }
Communication signal
+
∑
l∈L
Glx
| {z }
Target reﬂection
+ HSIx|{z}
SI
+nBS,
(8)
where pj is the transmit power of UL user j and nBS ∼
CN
(
0,σ 2BSIM) is the AWGN at the BS with covariance
matrix σ2BSIM .
C. Sensing and Communication Performance Metrics
The BS uses the received signal (8) to sense the target.
To capture the reﬂected signal of target l, the BS applies the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

DING et al.: MOV ABLE ANTENNA-AIDED NEAR-FIELD INTEGRATED SENSING AND COMMUNICATION 497
receive beamformer, ul∈ CM×1, on received signal yBS, and
thus the corresponding signal-to-interference-plus-noise ratio
(SINR) is given by
γSl = uHl GlRGHl ul
uHl
(
∑
j∈J
pjfjfHj + AlRAHl +σ2BSIM
)
ul
, (9)
where R = E
{
xxH} =∑l∈L Sl +∑k∈K wkwHk ∈ CN×N
and Al = ∑i∈L\l Gi + HSI ∈ CM×N . For point target
detection in MIMO radar systems, an effective radar waveform
design strategy is to maximize the output SINR, given that the
probability of target detection generally exhibits a monotonic
increase with SINR [8], [14]. Although the scalar SINR
deﬁned in (9) inevitably reduces the dimension of observations
compared to the full-dimensional data in (8), it provides
a tractable and effective surrogate for sensing performance.
A sensing system may make measurements of a target to
determine its unknown characteristics. To quantify how much
information can be extracted with a given sensing signal, the
sensing rate, also known as the sensing mutual information
per unit time [50], can be adopted. It is deﬁned as the
mutual information between the received signal at the BS
and the target response (or the target parameter), conditioned
on the transmitted signal. Speciﬁcally, after receive beamform-
ing, the output signal is expressed as yBS = uHl yBS. Since the
BS has knowledge of both the receive beamformer ul and the
transmitted ISAC signal x, we can use yBS and (9) together
with the results in [11] and [16] to obtain the conditional
sensing mutual information between the received signal and
the target response (or the sensing rate) as
RSl =I (yBS; Gl| ul, x) = log2 (1 +γSl). (10)
The target response Gl contains the geometric parameters of
the target, such as distance and angle information. It has been
proved in [51] that a high sensing rate indicates that the sens-
ing system can accurately estimate the geometric parameters
of targets embedded in the target response matrix. Therefore,
we can maximize the sensing rate to obtain more informa-
tion about the measured target and reduce the measurement
error, which ﬁnally results in more accurate target parameter
estimation [51]. Different from the communication rate, the
sensing rate has no explicit operational meaning. However,
it has similar mathematical properties and the same unit of
measurement as the communication rate, which facilitates
theoretical analysis and waveform design. The sensing rate
has been widely recognized as an effective metric in previous
studies [11], [16], [33], [43].
Similarly, the BS applies another set of receive beamform-
ers, bj ∈ CM×1, on yBS to decode the data signal of UL
user j. The corresponding UL communication rate is given by
RUj = log2
(
1 +γUj
)
, where γUj is the receive SINR given
by
γUj = pjbHj fjfHj bj
bHj
(
∑
i∈J\j
pififHi + ARAH +σ2BSIM
)
bj
, (11)
where A =∑l∈L Gl + HSI∈ CM×N . For DL communica-
tion, (7) indicates that the SINR of DL user k can be expressed
as
γDk =
⏐⏐hHk wk⏐⏐2
∑
i∈K\k
⏐⏐hHk wi⏐⏐2 +∑
l∈L
hHk Slhk +σ2k
, (12)
and the corresponding DL communication rate is given by
RDk = log2 (1 +γDk).
D. Problem F ormulation
In this paper, we aim to maximize the WSR to balance
sensing accuracy and communication efﬁciency, which can be
expressed as
WSR =
∑
l∈L
ϖSlRSl +
∑
j∈J
ϖUjRUj +
∑
k∈K
ϖDkRDk, (13)
where ϖSl≥ 0, ϖUj ≥ 0, and ϖDk≥ 0 denote predeﬁned
rate weights for target l, UL user j, and DL user k, respectively,
which satisfy∑l∈LϖSl +∑j∈J ϖUj +∑k∈KϖDk = 1 and
can be used to prioritize the targets and users. In particular, we
jointly optimize the receive beamformers, ul and bj, sensing
signal covariance matrices, Sl, transmit beamformers, wk, UL
transmit power, pj, and MA positions, t and r. Accordingly,
the optimization problem is formulated as 5
maximize
ul,bj,Sl,wk,pj,t,r
WSR
s.t. C1 :‖ul‖22 = 1, ∀l∈L,
C2 :‖bj‖22 = 1, ∀j∈J ,
C3 :
∑
l∈L
Tr{Sl} +
∑
k∈K
‖wk‖22≤P maxD ,
C4 : 0≤pj≤P maxU , ∀j∈J ,
C5 : t∈C t, r∈C r,
C6 :‖ta− t˜a‖2≥D, 1≤a⁄= ˜a≤N,
C7 :
‖‖rb− r˜b‖‖2≥D, 1≤b⁄= ˜b≤M. (14)
Here, constraints C1 and C2 normalize the receive beamform-
ers. Constraints C3 and C4 indicate that the total transmit
powers of DL and UL transmissions should not exceed the
maximum limits, P maxD and P maxU , respectively. Constraint
C5 conﬁnes the moving regions of transmit and receive MAs.
Constraints C6 and C7 ensure the minimum inter-MA distance,
D, at the BS for practical implementation. Note that problem
(14) is a non-convex optimization problem with coupled
variables, and thus ﬁnding globally optimal solutions for it in
polynomial time is challenging. Thus, we develop an efﬁcient
two-layer RP algorithm to obtain suboptimal solutions for this
problem in the next section.
III. P ROPOSED SOLUTION
The AO algorithm is commonly used to solve optimization
problems in wireless communication systems. It decomposes
5This paper focuses on maximizing the overall WSR of the proposed MA-
aided near-ﬁeld ISAC system. The quality-of-service (QoS) requirements of
individual users and targets can be addressed in subsequent stages via user
scheduling and resource allocation.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

498 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
the original problem into manageable sub-problems and itera-
tively solves each one while keeping the optimization variables
of other sub-problems ﬁxed. For MA-aided communication
systems, a straightforward approach is to separate the opti-
mization of MA positions and other variables into two
independent problems and then solve them iteratively [18].
However, the conventional AO algorithm may converge to
undesired local optimal solutions because the MA positions
(or other variables) determined in the previous iteration restrict
the optimization space for other variables (or MA positions) in
the current iteration [52]. Therefore, we propose a two-layer
RP algorithm. In the inner-layer, for a given MA position,
we decompose problem (14) into two sub-problems, i.e.,
iteratively updating {ul, bj} with closed-form expressions
and{Sl, wk,pj} based on successive convex approximation
(SCA). In the outer-layer, we randomly assign multiple pairs
of transmit and receive MA positions, {t, r}, and select the
pair that maximizes the objective value (13) as the optimized
MA positions. The initial and optimized MA positions are
then matched one by one via the proposed APM algorithm to
minimize the total MA movement distance. The details of the
proposed algorithms are presented below.
A. Inner-Layer of RP Algorithm
In the inner-layer, since the MA positions,{t, r}, are given,
we only need to optimize {ul, bj, Sl, wk,pj}. Thus, problem
(14) can be restated as the following optimization problem:
maximize
ul,bj,Sl,wk,pj
WSR
s.t. C1− C4. (15)
Based on the AO framework, we decompose problem (15)
into two sub-problems and iteratively optimize {ul, bj} and
{Sl, wk,pj}.
1) Sub-Problem 1 for Optimizing {ul, bj}: Given
{Sl, wk,pj}, the optimizations of ul and bj only affect
the receive SINRs (9) and (11), respectively. Therefore,
maximizing the WSR, i.e., objective value (13), is equivalent
to maximizing SINRs (9) and (11). Hence, we optimize
{ul, bj} via the SINR maximization criteria:
maximize
ul
γSl
s.t. C1, (16)
maximize
bj
γUj
s.t. C2. (17)
Proposition 1: The optimal solutions of problems (16) and
(17) are respectively given by
u∗l =
(
∑
j∈J
˜fj˜fHj + AlRAHl +σ2BSIM
)−1
gl
‖‖‖‖‖‖(∑j∈J ˜fj˜fHj + AlRAHl +σ2BSIM)−1gl‖‖‖‖‖‖
2
, (18)
b∗j =
(
∑
i∈J\j
˜fi˜fHi + ARAH +σ2BSIM
)−1
˜fj
‖‖‖‖‖‖( ∑i∈J\j ˜fi˜fHi + ARAH +σ2BSIM)−1˜fj‖‖‖‖‖‖
2
, (19)
where gl = Gl
(∑
k∈K wk +∑l∈L sl)∈ CM×1 and ˜fj =√pjfj∈ CM×1.
Proof: Please refer to [14, Appendix A].
2) Sub-Problem 2 for Optimizing {Sl, wk,pj}: Given
{ul, bj}, the joint optimization of {Sl, wk,pj} can be for-
mulated as
maximize
Sl,wk,pj
WSR
s.t. C3, C4. (20)
Deﬁning Wk = wkwHk ∈ CN×N , constraint C3 can be
equivalently transformed into the following constraints:
C3a :
∑
l∈L
Tr{Sl} +
∑
k∈K
Tr{Wk}≤ P maxD ,
C3b : Wk≽ 0, ∀k∈K,
C3c : Rank{Wk}≤ 1, ∀k∈K.
As such, problem (20) can be recast as
maximize
Sl,Wk,pj
WSR
s.t. C3a, C3b, C3c, C4. (21)
Problem (21) is non-convex due to the non-concavity of the
objective function and the rank constraint C3c. Therefore, it
is necessary to transform problem (21) into a convex form.
To achieve this goal, we begin by addressing the non-
concavity of the objective function. Based on the rule of the
logarithmic function, the objective function of problem (21)
can be reformulated as
~WSR =α1 +α2 +α3−β1−β2−β3, (22)
where α1, α2, α3, β1, β2, and β3 are the concave functions
with respect to (w.r.t.) optimization variables{Sl, Wk,pj} and
shown in (23)–(28), shown at the bottom of the next page,
respectively. Thus, objective function (22) is a difference-of-
concave function. The SCA algorithm is applied to obtain a
suboptimal solution for problem (21).
Deﬁne the maximum number of iterations for SCA as
C. In the c-th ( 1 ≤ c ≤ C) iteration, given the feasible
point
{
Scl, Wck,pcj}, we construct a global overestimate of
β1 (Sl, Wk,pj) by the ﬁrst-order Taylor expansion, i.e.,
β1 (Sl, Wk,pj)≤ ˆβ1(Sl, Wk,pj⏐⏐Scl, Wck,pcj)
=β1
(
Scl, Wck,pcj)
+
∑
l∈L
Tr
{(
∇Slβ1
(
Scl, Wck,pcj))H (Sl− Scl )}
+
∑
k∈K
Tr
{(
∇Wkβ1
(
Scl, Wck,pcj))H (Wk− Wck)}
+
∑
j∈J
∇pjβ1
(
Scl, Wck,pcj)(pj−pcj), (29)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

DING et al.: MOV ABLE ANTENNA-AIDED NEAR-FIELD INTEGRATED SENSING AND COMMUNICATION 499
where∇Slβ1,∇Wkβ1, and∇pjβ1 are the gradients of func-
tion β1 w.r.t. Sl, Wk, and pj, respectively, and are shown
in (30) and (31), at the bottom of the page. Similarly, given
the feasible point
{
Scl, Wck,pcj}, the global overestimates of
β2 (Sl, Wk,pj) and β3 (Sl, Wk) are respectively given by
β2 (Sl, Wk,pj)≤ ˆβ2(Sl, Wk,pj⏐⏐Scl, Wck,pcj)
=β2
(
Scl, Wck,pcj)
+
∑
l∈L
Tr
{(
∇Slβ2
(
Scl, Wck,pcj))H (Sl− Scl )}
+
∑
k∈K
Tr
{(
∇Wkβ2
(
Scl, Wck,pcj))H (Wk− Wck)}
+
∑
j∈J
∇pjβ2
(
Scl, Wck,pcj)(pj−pcj), (32)
and
β3 (Sl, Wk)≤ ˆβ3 (Sl, Wk|Scl, Wck )
=β3 (Scl, Wck)
+
∑
l∈L
Tr
{
(∇Slβ3 (Scl, Wck))H (Sl− Scl )}
+
∑
k∈K
Tr
{
(∇Wkβ3 (Scl, Wck))H (Wk− Wck)}, (33)
α1 =
∑
l∈L
ϖSllog2

∑
i∈L
Tr
{
RGHi uluHl Gi} + Tr{RHHSIuluHl HSI} +∑
j∈J
pj
⏐⏐uHl fj⏐⏐2 +σ2BS

. (23)
α2 =
∑
j∈J
ϖUjlog2
(∑
l∈L
Tr
{
RGHl bjbHj Gl} + Tr{RHHSIbjbHj HSI} +∑
i∈J
pi
⏐⏐bHj fi⏐⏐2 +σ2BS
)
. (24)
α3 =
∑
k∈K
ϖDklog2
(
Tr
{
RhkhHk} +σ2k). (25)
β1 =
∑
l∈L
ϖSllog2

∑
i∈L\l
Tr
{
RGHi uluHl Gi} + Tr{RHHSIuluHl HSI} +∑
j∈J
pj
⏐⏐uHl fj⏐⏐2 +σ2BS

. (26)
β2 =
∑
j∈J
ϖUjlog2

∑
l∈L
Tr
{
RGHl bjbHj Gl} + Tr{RHHSIbjbHj HSI} + ∑
i∈J\j
pi
⏐⏐bHj fi⏐⏐2 +σ2BS

. (27)
β3 =
∑
k∈K
ϖDklog2

Tr



∑
l∈L
Sl +
∑
i∈K\k
Wi

 hkhHk

 +σ2k

. (28)
∇Slβ1 =∇Wkβ1 =
∑
l∈L
ϖSl
ln 2·
∑
i∈L\l
GHi uluHl Gi + HHSIuluHl HSI
∑
i∈L\l
Tr
{
RGHi uluHl Gi} + Tr{RHHSIuluHl HSI} + ∑
j∈J
pj
⏐⏐uHl fj⏐⏐2 +σ2BS. (30)
∇pjβ1 =
∑
l∈L
ϖSl
ln 2·
⏐⏐uHl fj⏐⏐2
∑
i∈L\l
Tr
{
RGHi uluHl Gi} + Tr{RHHSIuluHl HSI} + ∑
j∈J
pj
⏐⏐uHl fj⏐⏐2 +σ2BS. (31)
∇Slβ2 =∇Wkβ2 =
∑
j∈J
ϖUj
ln 2·
∑
l∈L
GHl bjbHj Gl + HHSIbjbHj HSI
∑
l∈L
Tr
{
RGHl bjbHj Gl} + Tr{RHHSIbjbHj HSI} + ∑
i∈J\j
pi
⏐⏐bHj fi⏐⏐2 +σ2BS. (34)
∇pjβ2 =
∑
t∈J\j
ϖUt
ln 2·
⏐⏐bHt fj⏐⏐2
∑
l∈L
Tr
{
RGHl btbHt Gl} + Tr{RHHSIbtbHt HSI} + ∑
i∈J\t
pi
⏐⏐bHt fi⏐⏐2 +σ2BS. (35)
∇Slβ3 =
∑
k∈K
ϖDk
ln 2· hkhHk
Tr
{(
∑
l∈L
Sl + ∑
i∈K\k
Wi
)
hkhHk
}
+σ2k
. (36)
∇Wkβ3 =
∑
t∈K\k
ϖDt
ln 2· hthHt
Tr
{(
∑
l∈L
Sl + ∑
i∈K\t
Wi
)
hthHt
}
+σ2k
. (37)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

500 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Algorithm 1 SCA Algorithm for Solving Problem (20)
Initialization: Set initial point
{
S0l, W0k,p 0j}, iteration index
c = 0, and error tolerance 0≤ϵ≪ 1.
Output: Sl, wk, and pj.
1: Calculate initial value ˆWSR(S0l, W0k,p 0j);
2: repeat
3: Set c =c + 1;
4: Solve the relaxed version of problem (39) for the
given feasible point
{
Sc−1l , Wc−1k ,pc−1j } and store the
intermediate solution
{
Scl, Wck,pcj} ={Sl, Wk,pj};
5: until Increase of objective value (38) is less than ϵ or
c≥C
6: Perform eigenvalue decomposition on Wck to obtain wk;
7: return: Sl = Scl , wk, and pj =pcj.
Algorithm 2 AO Algorithm for Solving Problem (15)
Initialization: Set initial
{
u0l, b0j, S0l, w0k,p 0j}, iteration index
˜c = 0, and error tolerance 0≤ ˜ϵ≪ 1.
Output: ul, bj, Sl, wk, and pj.
1: Calculate initial value WSR
(
u0l, b0j, S0l, w0k,p 0j);
2: repeat
3: Set ˜c = ˜c + 1;
4: With given S˜c−1l , w˜c−1k , and p˜c−1j , solve sub-problem
1 by (18) and (19), and store the intermediate solutions
u˜cl = ul and b˜cj = bj;
5: With given u˜cl and b˜cj, solve sub-problem 2 by Algo-
rithm 1 and store the intermediate solutions S˜cl = Sl,
w˜ck = wk, and p˜cj = pj;
6: until Increase in objective value (13) is less than ˜ϵ or
˜c≥ ~C
7: return: ul = u˜cl , bj = b˜cj, Sl = S˜cl , wk = w˜ck, and
pj =p˜cj.
where gradients∇Slβ2,∇Wkβ2,∇pjβ2,∇Slβ3, and∇Wkβ3
are shown in (34)–(37) at the bottom of the previous page.
Therefore, in the c-th iteration, given the feasible point{
Scl, Wck,pcj}, a lower bound of objective value (22) can be
determined by
ˆWSR (Sl, Wk,pj) =α1 +α2 +α3
− ˆβ1(Sl, Wk,pj⏐⏐Scl, Wck,pcj)
− ˆβ2(Sl, Wk,pj⏐⏐Scl, Wck,pcj)
− ˆβ3 (Sl, Wk|Scl, Wck ). (38)
Then, problem (21) can be reformulated as
maximize
Sl,Wk,pj
ˆWSR (Sl, Wk,pj)
s.t. C3a, C3b, C3c, C4. (39)
Next, for the rank constraint C3c, we apply semideﬁnite
relaxation (SDR) and remove constraint C3c. The relaxed
version of problem (39) can now be optimally solved using
standard convex solvers such as CVX [48]. Then, we verify
the tightness of SDR in the following proposition.
Algorithm 3 RP Algorithm for Solving Problem (14)
Input: M, N, K, J, L,P maxD ,P maxU , D, Γ,Ct,Cr,ρSI,λ,{ρDk},{
ρUj
}
,{ρSl},
{
qUj
}
,{qDk}, and{qSl}.
Output: ul, bj, Sl, wk, pj, t, and r.
1: Randomly generate {{t, r}i}Γi=1 that satisfy constraints
C5-C7;
2: fori = 1 : 1 : Γ do
3: With given{t, r}i, solve problem (15) by Algorithm 2
to obtain the optimized {ul, bj, Sl, wk,pj};
4: Calculate the corresponding WSR ({t, r}i) by (13);
5: end for
6: Select the optimized MA position {t, r} =
arg max
{t,r}i
{WSR ({t, r}1),...,WSR ({t, r}Γ)}
7: return: ul, bj, Sl, wk, pj, t, and r.
Proposition 2: If P maxD > 0, the optimal beamforming
matrices Wk satisfying Rank{Wk} ≤ 1 can always be
obtained.
Proof: Please refer to [53, Appendix A].
The SCA algorithm for solving problem (20) iteratively is
summarized in Algorithm 1.
3) AO Algorithm for Solving Problem (15): After obtaining
the solutions of sub-problems 1 and 2, the proposed AO algo-
rithm for solving problem (15) is summarized in Algorithm 2.
Speciﬁcally, we ﬁrst obtain the optimized {ul, bj} by closed-
form expressions (18) and (19) (Line 4). Then, we optimize
{Sl, wk,pj} by solving sub-problem 2 based on SCA (Line
5). The AO algorithm iteratively solves the two sub-problems
until the increase in objective value (13) is less than error
tolerance threshold ˜ϵ or the maximum number of iterations
for AO, ~C, is reached.
B. Outer-Layer of RP Algorithm
In the outer-layer, we propose an intuitive antenna position
optimization algorithm, i.e., RP algorithm, to obtain the opti-
mized positions for multiple transmit and receive MAs. It is
well known that the adjustment of MA positions effectively
reconﬁgures the channel [19]. In addition, the optimization
of beamformers, sensing signal covariance matrices, and UL
power allocation relies directly on the channel response.
Therefore, in the antenna position optimization process, the
beamformers, sensing signal covariance matrices, and UL
power allocation need to be optimized for each candidate
MA position to fully exploit the performance potential of the
current MA position. To reduce the computational complexity
of the antenna position optimization algorithm, we provide
an intuitive and feasible RP algorithm, which is summarized
in Algorithm 3. First, the RP algorithm randomly generate Γ
pairs of t and r, i.e., {t, r}i (1≤ i≤ Γ), that satisfy con-
straints C5-C7 (Line 1). For each pair, problem (15) is solved
by Algorithm 2 to obtain the optimized {ul, bj, Sl, wk,pj}
(Line 3). The corresponding WSR is calculated based on (13)
(Line 4). Then, the {t, r} with the largest WSR is selected as
the optimized MA position (Line 6). Finally, the optimized
MA position, along with the corresponding beamformers,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

DING et al.: MOV ABLE ANTENNA-AIDED NEAR-FIELD INTEGRATED SENSING AND COMMUNICATION 501
Fig. 2. An example of APM with ~N = 3.
sensing signal covariance matrices, and UL power allocation,
are obtained.
C. Antenna Position Matching (APM) Algorithm
To reduce the additional overhead caused by antenna move-
ment over large-size regions, we develop the APM algorithm
to minimize the total MA movement distance in this sub-
section.
Deﬁne the initial and optimized antenna positions of ~N
MAs before and after antenna position optimization as vinit˜n ∈
R3×1 and vopt˜n ∈ R3×1 (1 ≤ ˜n ≤ ~N), respectively. Prior
works on MA-aided systems have yet incorporated the MA
movement distance into the objective function or constraints
of the optimization problem, apart from an initial investi-
gation given in [54]. In other words, when moving MA ˜n
from vinit˜n to vopt˜n , they do not consider the additional costs
incurred by antenna movement in practical applications. The
optimized position vopt˜n may be far from the corresponding
initial position vinit˜n but closer to another initial MA position.
Furthermore, this oversight is especially signiﬁcant in near-
ﬁeld ISAC scenarios because the large-size moving regions
are deployed. As such, we propose an APM algorithm based
on the greedy strategy to tackle this issue.
The total MA movement distance minimization problem is
a shortest path search problem in tree graph. Fig. 2 shows an
example for the case when ~N = 3, where
ω
(
vinit˜n , voptˆn ) =‖‖vinit˜n − voptˆn ‖‖2, 1≤ ˆn≤ ~N, (40)
is the path weight determined by the movement distance
from vinit˜n to voptˆn . For each MA, the destination position,
vdest˜n ∈ R3×1, can be selected according to path weights.
Once a speciﬁc optimized position is selected by one MA,
it becomes unavailable for the remaining MAs. Consequently,
there are ~N! APM solutions.
To ﬁnd the optimal APM solution that minimizes the total
MA movement distance, a straightforward approach is to per-
form an exhaustive search over the ~N! solutions. However, this
clearly results in high computational complexity, especially
Algorithm 4 APM Algorithm for Minimizing the Total MA
Movement Distance
Input: M, N, tinit, rinit, topt, and ropt.
Output: tdest and rdest.
1: Initialize the index sets of the transmit and receive MAs as
N 0 ={1,...,N } andM0 ={1,...,M }, respectively;
2: forn = 1 : 1 :N do
3: Calculate path weight ω
(
tinitn , toptˆn ) according to
(40);
4: Select optimized position toptˆn as transmit MA n’s
destination position tdestn according to (41);
5: Update antenna index set Nn according to (42);
6: end for
7: form = 1 : 1 :M do
8: Calculate path weight ω
(
rinitm , roptˆm ) according to
(40);
9: Select the optimized position roptˆm as receive MA
m’s destination position rdestm according to (41);
10: Update antenna index set Mm according to (42);
11: end for
12: return: tdest and rdest.
when ~N is large. As a result, we adopt the greedy strategy to
identify a suboptimal solution. First, we initialize the antenna
index set as ~N 0 ={1,..., ~N}. Next, we sequentially select
destination position vdest˜n for each MA. Speciﬁcally, for MA˜n,
we select the optimized position in updated antenna index set
~N ˜n−1 with the smallest path weight as its destination position,
i.e.,
vdest˜n = arg min
voptˆn
{
ω
(
vinit˜n , voptˆn )⏐⏐⏐ˆn∈ ~N ˜n−1}. (41)
Then, we update the antenna index set by removing the index
of the selected antenna position, i.e.,
~N ˜n = ~N ˜n−1\ˆn. (42)
After the destination positions for all ~N MAs have been
selected, the APM solution vdest˜n for 1≤ ˜n≤ ~N is obtained.
Note that the aforementioned APM algorithm can be widely
applied in MA-aided communication systems. For the pro-
posed system, we need to perform APM separately for the
transmit and receive MAs. In other words, we have ~N = N
or M, vinit˜n = tinitn or rinitm , and vopt˜n = toptn or roptm ,
where tinitn /rinitm is the initial transmit/receive MA position
and toptn /roptm is the optimized transmit/receive MA position
output by Algorithm 3. The corresponding processing steps
are summarized in Algorithm 4. After that, the destination
positions of transmit and receive MAs, tdestn and rdestm , can be
obtained.
In practical applications, the movement of multiple MAs
within a given region can be realized through two typical
methods [55]. The ﬁrst method divides the moving region
into several non-overlapping sub-regions, where each MA is
restricted to move only within its designated sub-region. The
second method is based on dense array antennas. Speciﬁcally,
a large number of antennas are compactly arranged within the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

502 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Algorithm 5 Overall Algorithm for Solving Problem (14) and
Minimizing Total MA Movement Distance
Input: M, N, K, J, L,P maxD ,P maxU , D, Γ,Ct,Cr,ρSI,λ,{ρDk},{
ρUj
}
,{ρSl},
{
qUj
}
,{qDk},{qSl}, tinit, and rinit.
Output: ul, bj, Sl, wk, pj, tdest, and rdest.
1: Solving problem (14) by Algorithm 3 to obtain optimized
ul, bj, Sl, wk, pj, topt, and ropt;
2: Search destination positions for transmit and receive MAs,
tdest and rdest, by Algorithm 4;
3: return: ul, bj, Sl, wk, pj, tdest, and rdest.
transmit/receive region, and each is integrated with a recon-
ﬁgurable device (e.g., a pixel antenna [56]) to enable dynamic
conﬁguration. By adjusting the states of these reconﬁgurable
devices, different sets of antennas can be selectively activated.
This method serves as an efﬁcient alternative to physical MA
movement and is particularly well-suited for scenarios with
limited movement space.
D. Overall Algorithm
The detailed overall algorithm for solving problem (14) and
minimizing the total MA movement distance is summarized
in Algorithm 5. Speciﬁcally, the optimized transmit beam-
formers, wk, sensing signal covariance matrices, Sl, receive
beamformers, ul and bj, UL power allocation, pj, and MA
positions, topt and ropt, are obtained by Algorithm 3 (Line 1).
Subsequently, the destination positions of transmit and receive
MAs, tdest and rdest, are searched by Algorithm 4 to minimize
the total MA movement distance (Line 2).
E. Convergence and Complexity Analysis
As the RP algorithm only executes the selection of candidate
MA positions, its convergence depends on Algorithm 2. The
convergence of Algorithm 2 is guaranteed by the following
inequality:
WSR
(
u˜cl, b˜cj, S˜cl, w˜ck,p ˜cj)
(α1)
≥ WSR
(
u˜cl, b˜cj, S˜c−1l , w˜c−1k ,p ˜c−1j )
(α2)
≥ WSR
(
u˜c−1l , b˜c−1j , S˜c−1l , w˜c−1k ,p ˜c−1j ), (43)
where inequality (α1) holds because
{
S˜cl, w˜ck,p ˜cj} are the
optimized sensing signal covariance matrices, transmit beam-
formers, and UL power allocation via Algorithm 1 under the
current
{
u˜cl, b˜cj}, and inequality (α2) holds because{u˜cl, b˜cj}
are the optimal receive beamformers for maximizing SINRs
(9) and (11) under the current
{
S˜c−1l , w˜c−1k ,p ˜c−1j }. Thus,
the objective value is non-decreasing during the iterations
in Algorithm 2. Meanwhile, the objective value is upper-
bounded due to ﬁnite communication resources. As such,
the convergence of Algorithm 2 is guaranteed. Moreover, the
convergence is veriﬁed by the simulations in Section IV-B.
The main computational complexity of the overall
algorithm, i.e., Algorithm 5, is due to the iteration in
Algorithm 2, the selection in Algorithm 3, and the search in
Algorithm 4. In Algorithm 2, the computational complexity
TABLE I
SIMULATION PARAMETERS
for calculating receive beamformers is O
(
(L +J)M3) due
to the matrix inversion in (18) and (19). The computational
complexity of Algorithm 1 for optimizing transmit
beamformers, sensing signal covariance matrices, and
UL power allocation is O
(
CSCA
(
(L +K)N3.5 +J3.5))
due to solving the SDR problem iteratively, where
CSCA is the number of iterations for SCA. Therefore,
the computational complexity of Algorithm 2 is o1 =
O
(
~CAO((L +J)M3 +CSCA((L +K)N3.5 +J3.5))),
where ~CAO is the number of iterations for AO. In addition,
the computational complexity of Algorithm 4 for matching
antenna positions is o2 =O
( 1
2 (N (N + 1) +M (M + 1))
)
.
As a result, with the number of candidate MA position pairs
Γ, the computational complexity of the overall algorithm is
O (Γo1 +o2).
IV. P ERFORMANCE EVALUATION
In this section, we provide the simulation results to evaluate
the performance of the proposed MA-aided near-ﬁeld ISAC
system. First, the simulation setup is introduced, and then the
numerical results are presented.
A. Simulation Setup
In the simulation, the sensing targets and users are randomly
distributed within a semicircular region on the ground centered
at the BS, with horizontal distances from the BS to the
targets/users ranging from 25 to 30 meters (m). The transmit
and receive MA arrays are horizontally mounted on a full-
duplex BS at a height of 15 meters. The carrier frequency is
set to 30 GHz ( λ = 0.01 m). The pass loss coefﬁcients ρDk
andρUj are determined by the USW model [41]. Without loss
of generality, we assume that the rate weights are equal, i.e.,
ϖSl = ϖUj = ϖDk = 1L+J+K . Unless otherwise speciﬁed,
the default simulation parameters are listed in Table I.
B. Convergence Evaluation of Algorithm 2
We ﬁrst evaluate in Fig. 3 the convergence performance
of the proposed Algorithm 2, under different numbers of
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

DING et al.: MOV ABLE ANTENNA-AIDED NEAR-FIELD INTEGRATED SENSING AND COMMUNICATION 503
Fig. 3. Convergence evaluation of Algorithm 2.
targets/users. As can be observed, the algorithm demonstrates
rapid convergence in all scenarios, with the objective value
stabilizing within 10 iterations. This conﬁrms the previous
discussion regarding the convergence of Algorithm 2 in Sec-
tion III-E. Moreover, the WSR improves as the number of
targets/users increases, since the additional targets/users can
leverage the redundant spatial DoFs to further enhance the
overall system performance.
C. Beamfocusing in MA-Aided Near-Field ISAC
To intuitively demonstrate the advantages of large-size
moving regions in near-ﬁeld ISAC systems, we present the
beampattern corresponding to the optimized geometry of the
transmit MA array with N = 128 in Figs. 4 and 5. The beam-
pattern for the receive MA array can be similarly obtained and
is thus omitted here for brevity. Speciﬁcally, we calculate the
array response vector
a (q) =
[
ej 2πλ‖t1−q‖2,...,e j 2πλ‖tN−q‖2
]T
∈ CN×1, (44)
for all positions q within a deﬁned rectangular region on
the ground. Then, the beamfocusing at B locations, i.e.,
˜qb∈ R3×1, b∈B ={1,...,B }, is achieved by setting the
beamforming vector as the sum of the array response vectors
at these beamfocusing points, i.e.,
wbf =
∑
b∈B
a (˜qb)
=
∑
b∈B
[
ej 2πλ‖t1−˜qb‖2,...,e j 2πλ‖tN−˜qb‖2
]T
∈ CN×1,
(45)
Therefore, the beamforming gain at position q can be calcu-
lated as
G (q) = 1N ⏐⏐wHbfa (q)⏐⏐. (46)
As shown in Fig. 4, when A = 100λ (see Fig. 4(a)), the
beam is precisely focused at the multiple desired locations,
and the main lobes of the beam are extremely narrow. This
indicates that the beam focused on the desired locations causes
minimal interference leakage to other locations, allowing the
near-ﬁeld ISAC system to achieve excellent performance in
multi-target sensing and multi-user communication through
joint resolutions in both the distance and angle domains. As the
size of the moving region decreases ((see Figs. 4(b) and 4(c)),
the beam’s main lobes become wider due to the reduced
maximum aperture achievable by the MA array. This results
in signiﬁcant interference to the targets/users at undesired
locations, thereby degrading the overall system performance.
Notably, when A = 5λ, the beamfocusing points are already
in the far-ﬁeld region, resulting in a loss of resolution in the
distance domain and retaining only angle discrimination. In
other words, when multiple targets and users are located in the
same direction relative to the BS, the far-ﬁeld ISAC system
cannot provide effective sensing and communication services
for them.
In addition, Fig. 5 provides a 3D perspective on the
variations in beampatterns across different distance intervals
between the BS and beamfocusing points. The beamforming
gains in Fig. 5(a) at the beamfocusing points are signiﬁcantly
higher compared to the other locations. As the distance
between the BS and beamfocusing points increases, the inter-
ference leakage from the beam’s main lobes to locations
that are not beamfocusing points becomes more pronounced
because the spherical wave approximates more closely to
the plane wave, leading to a gradual disappearance of near-
ﬁeld beamfocusing characteristics. The beamforming gains in
Fig. 5(c) are nearly uniform in the same direction, which
makes it impossible to distinguish between different beam-
focusing points along that direction.
Overall, the additional distance dimension of near-ﬁeld
ISAC, compared to far-ﬁeld ISAC, allows for beamfocusing
that enhances the performance of multi-target sensing and
multi-user communication. The MA system, which has a larger
aperture size of the antenna array compared to conventional
FPA systems, naturally expands the near-ﬁeld region. As a
result, the MA-aided near-ﬁeld ISAC system can beneﬁt from
the enlarged near-ﬁeld region achieved by the large moving
region.
D. Performance Comparison With Benchmark Schemes
To gain more insight, we compare the performance of the
proposed scheme (labeled as MA) with benchmark schemes.
The considered benchmark schemes for setting antennas’ posi-
tions are listed as follows: 1) FPA with full aperture (FPAF):
The antenna’s positions, t and r, are set according to the
transmit and receive uniform planar arrays (UPAs) with the
largest achievable apertures A×A; and 2) FPA with half-
wavelength antenna spacing (FPAH): The antenna’s positions,
t and r, are set according to the transmit and receive UPAs
with half-wavelength inter-antenna spacing both horizontally
and vertically. To ensure a fair comparison, the FPAF, FPAH,
and MA schemes use the same number of transmit and receive
antennas. For the FPAH scheme, the targets and users are in
the far-ﬁeld region of the BS, which facilitates comparing the
performance differences between far-ﬁeld and near-ﬁeld ISAC
systems.
Fig. 6 compares the WSRs of different schemes versus the
moving region size. As can be seen, the WSRs of the MA and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

504 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 4. Beampattern under different sizes of the moving region.
Fig. 5. Beampattern under different distances between the BS and beamfocusing points.
Fig. 6. Comparison of WSR between the proposed and benchmark schemes
w.r.t. the moving region size.
FPAF schemes continuously increase when the moving region
size is less than 30λ, and stabilize when the size exceeds 30λ.
This is because the increase in the moving region size provides
two advantages: 1) expand the optimization space for the
antenna position optimization; and 2) enlarge the equivalent
array aperture, thereby extending the near-ﬁeld region, within
which the resolution for multiple locations can be achieved.
The MA scheme fully leverages both advantages to improve
system performance. The FPAF scheme beneﬁts only from
advantage 2). The FPAH scheme fails to capitalize on either
of these two advantages due to two main limitations. First,
the static antenna placement prevents the ISAC system from
ﬂexibly optimizing the antenna positions based on varying
channel conditions. Second, the ﬁxed array aperture conﬁnes
the ISAC system to far-ﬁeld propagation conditions, where it
offers resolution only in the angular domain rather than in
the distance domain. As a result, the MA scheme achieves a
13.57% or 19.07% WSR gain over the FPAF scheme when
Γ = 10 or Γ = 100 , respectively. The WSR of the FPAH
scheme, however, remains unchanged. Furthermore, for the
MA scheme, Γ = 100 achieves better system performance
than Γ = 10 due to the availability of more candidate MA
positions, at the cost of increased computational complexity.
In Fig. 7, we compare the WSRs of the proposed and
benchmark schemes w.r.t. the distance between the BS and
targets/users. The distances between the BS and different
targets/users are set within a 5-meter interval, centered around
a speciﬁed distance. We can see that as the distance increases,
the WSRs of all schemes decreases. This is because the
increase in distance weakens system performance in the fol-
lowing two aspects: 1) increased path loss; and 2) the
transition from near-ﬁeld ISAC to far-ﬁeld ISAC, which leads
to the gradual loss of the distance dimension in the ISAC
system. However, in the same communication scenario, the
MA scheme still outperforms the FPAF and FPAH schemes
due to the additional DoFs introduced by antenna position
optimization.
Next, we show the WSRs of the proposed and bench-
mark schemes w.r.t. the maximum DL transmit power under
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

DING et al.: MOV ABLE ANTENNA-AIDED NEAR-FIELD INTEGRATED SENSING AND COMMUNICATION 505
Fig. 7. Comparison of WSR between the proposed and benchmark schemes
w.r.t. the distance between the BS and targets/users.
Fig. 8. Comparison of WSR between the proposed and benchmark schemes
w.r.t. the maximum DL transmit power.
different maximum UL transmit power constraints in Fig. 8.
Overall, the WSRs of all schemes improve as the maximum
DL transmit power increases, since higher DL transmit power
ensures more reliable DL transmission quality. However, the
high DL transmit power can cause strong echo signals from
the sensing targets and SI, which in turn degrade the SINRs of
the UL users. Therefore, as shown in Fig. 8, when P maxD ≥ 40
dBm, both the FPAF and FPAH schemes exhibit a noticeable
slowdown in WSR increase compared to the MA scheme at
low maximum UL transmit power case, i.e., P maxU = 10 dBm.
In addition, compared to FPA-based schemes, the MA scheme
can save the DL transmit power at the same WSR level by
leveraging ﬂexible antenna movement.
In Fig. 9, we analyze the trade-off between sensing and
communication. We set P maxD = 30 dBm, Γ = 10 , and
ϖUj = ϖDk. By adjusting the sensing rate weight ϖSl and
the communication weightsϖUj andϖDk, the trade-off curves
between the sensing rate and the communication rate are plot-
ted. For example, a purely communication-oriented design can
be realized by setting ϖSl = 0. To illustrate the performance
Fig. 9. Trade-off between sensing and communication performance.
improvements enabled by the repositioning capability of MAs
and the incorporation of near-ﬁeld characteristics, we consider
four typical ISAC system conﬁgurations: 1) MA, near-ﬁeld:
The moving region size is set to A = 100λ, and thus the
targets and users are located within the near-ﬁeld region of
the BS; 2) MA, far-ﬁeld: The moving region size is set to
A = 5λ. In this case, the signal propagation between the
targets/users and the BS follows the far-ﬁeld model; 3) FPA,
near-ﬁeld: The antenna placement is determined based on
the FPAF scheme with A = 100λ, and thus the near-ﬁeld
condition consistent with that of 1) is ensured; and 4) FPA,
far-ﬁeld: The antenna placement is determined based on the
FPAH scheme, under which the targets and users are located
within the far-ﬁeld region of the BS. As shown in Fig. 9,
the ISAC system achieves a better sensing-communication
trade-off under near-ﬁeld conditions compared to the far-ﬁeld
case. This improvement is attributed to the spherical-wave
channel model, which enables the BS to distinguish targets
and users at different distances and angles. Moreover, the
MA system can exploit the additional DoF introduced by
the antenna position optimization to ﬂexibly reposition the
antennas, thereby further enlarging the achievable sensing-
communication trade-off region compared to the FPA system
in both far-ﬁeld and near-ﬁeld scenarios.
Finally, Fig. 10 illustrates the total MA movement distance
for schemes with (w/) or without (w/o) APM algorithm w.r.t.
the moving region size under different numbers of MAs. It
can be seen that the total MA movement distance increases
linearly with the size of the moving region, and the APM
algorithm signiﬁcantly reduces this distance. Moreover, as the
number of MAs increases, the gap between the schemes w/ and
w/o APM algorithm widens. Speciﬁcally, when the moving
region size is 120λ, the proposed APM algorithm reduces the
total MA movement distance by 35.79%, 39.50%, 42.46%, and
47.59% forN =M = 6, 8, 10, and 12, respectively. Typically,
in MA-aided near-ﬁeld ISAC systems, the size of moving
region and the number of MAs are large. Therefore, solely
considering antenna position optimization without accounting
for antenna’s position matching with their initial positions
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

506 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 10. Total MA movement distance for schemes with (w/) or without (w/o)
APM algorithm w.r.t. the moving region size.
leads to long MA movement distance, thereby increasing the
time delay and hardware burden.
V. C ONCLUSION
In this paper, we investigated the MA-aided near-ﬁeld ISAC
system. We characterized the near-ﬁeld sensing and commu-
nication channels w.r.t. MA positions using the spherical wave
model and formulated a joint optimization problem to maxi-
mize the system’s WSR achievable for both communications
and sensing. To solve this non-convex optimization problem,
we proposed a two-layer RP algorithm where multiple MA
positions were randomly initialized. For each MA position,
the beamformers, sensing signal covariance matrices, and UL
power allocation were iteratively optimized using the AO algo-
rithm until convergence. The MA position that achieves the
maximum WSR was then selected as the optimized position.
Moreover, considering the large size of moving region in near-
ﬁeld MA systems, we proposed an APM algorithm based
on the greedy strategy to reduce the total MA movement
distance, thereby alleviating the cost of antenna movement.
Simulation results veriﬁed the effectiveness of the proposed
algorithms and the advantages of the considered MA-aided
ISAC scheme compared to conventional FPA-based schemes.
Furthermore, the results showed that equipping the BS with
large regions for free MA movement increases the equivalent
array aperture, thereby signiﬁcantly expanding the near-ﬁeld
region without requiring more antennas or higher frequen-
cies. Compared to the far-ﬁeld ISAC system, the additional
distance dimension introduced by the near-ﬁeld ISAC system
can enhance system performance for multi-target sensing and
multi-user communication through precise beamfocusing. This
can be more efﬁciently exploited by optimally designing the
MAs’ positions matching the ISAC channels.
ACKNOWLEDGMENT
The calculations were supported by the High-Performance
Computing Platform of Peking University.
REFERENCES
[1] Y . Zhuo et al., “Multi-beam integrated sensing and communication:
State-of-the-art, challenges and opportunities,” IEEE Commun. Mag. ,
vol. 62, no. 9, pp. 90–96, Sep. 2024.
[2] X. Shao, C. You, W. Ma, X. Chen, and R. Zhang, “Target sensing
with intelligent reﬂecting surface: Architecture and performance,” IEEE
J. Sel. Areas Commun. , vol. 40, no. 7, pp. 2070–2084, Jul. 2022.
[3] Y . Gong, X. Li, F. Meng, L. Liu, M. Guizani, and Z. Xu, “Toward
green RF chain design for integrated sensing and communications:
Technologies and future directions,” IEEE Commun. Mag. , vol. 62,
no. 9, pp. 36–42, Sep. 2024.
[4] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[5] X. Chen et al., “Joint localization and communication enhance-
ment in uplink integrated sensing and communications system with
clock asynchronism,” IEEE J. Sel. Areas Commun. , vol. 42, no. 10,
pp. 2659–2673, Oct. 2024.
[6] J. Dai, C. Liu, C. Pan, and K. Wang, “Secure downlink transmission
for integrated sensing, energy, and communication systems,” IEEE
Commun. Lett. , vol. 28, no. 9, pp. 1996–2000, Sep. 2024.
[7] X. Wang, Z. Fei, J. A. Zhang, and J. Huang, “Sensing-assisted secure
uplink communications with full-duplex base station,” IEEE Commun.
Lett., vol. 26, no. 2, pp. 249–253, Feb. 2022.
[8] C. G. Tsinos, A. Arora, S. Chatzinotas, and B. Ottersten, “Joint
transmit waveform and receive ﬁlter design for dual-function radar-
communication systems,” IEEE J. Sel. Topics Signal Process. , vol. 15,
no. 6, pp. 1378–1392, Nov. 2021.
[9] C.-Y . Chen and P. P. Vaidyanathan, “MIMO radar waveform optimization
with prior information of the extended target and clutter,” IEEE Trans.
Signal Process., vol. 57, no. 9, pp. 3533–3544, Sep. 2009.
[10] L. Wu, P. Babu, and D. P. Palomar, “Transmit waveform/receive ﬁlter
design for MIMO radar with multiple waveform constraints,” IEEE
Trans. Signal Process. , vol. 66, no. 6, pp. 1526–1540, Mar. 2018.
[11] D. Galappaththige, C. Tellambura, and A. Maaref, “Integrated sensing
and backscatter communication,” IEEE Wireless Commun. Lett., vol. 12,
no. 12, pp. 2043–2047, Dec. 2023.
[12] J. A. Zhang et al., “Enabling joint communication and radar sensing
in mobile networks—A survey,” IEEE Commun. Surveys Tuts. , vol. 24,
no. 1, pp. 306–345, 1st Quart., 2022.
[13] B. He, F. Wang, and J. Cheng, “Joint secure transceiver design for
integrated sensing and communication,” IEEE Trans. Wireless Commun.,
vol. 23, no. 10, pp. 13377–13393, Oct. 2024.
[14] Z. He, W. Xu, H. Shen, D. W. K. Ng, Y . C. Eldar, and
X. You, “Full-duplex communication for ISAC: Joint beamforming
and power optimization,” IEEE J. Sel. Areas Commun. , vol. 41, no. 9,
pp. 2920–2936, Sep. 2023.
[15] Z. Wang, X. Mu, and Y . Liu, “Bidirectional integrated sensing and
communication: Full-duplex or half-duplex?,” IEEE Trans. Wireless
Commun., vol. 23, no. 8, pp. 8184–8199, Aug. 2024.
[16] W. Lyu, S. Yang, Y . Xiu, Z. Zhang, C. Assi, and C. Yuen, “Movable
antenna enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 24, no. 4, pp. 2862–2875, Apr. 2025.
[17] L. Zhu et al., “A tutorial on movable antennas for wireless networks,”
IEEE Commun. Surveys Tuts. , early access, Feb. 27, 2025, doi: 10.1109/
COMST.2025.3546373.
[18] W. Ma, L. Zhu, and R. Zhang, “MIMO capacity characterization for
movable antenna systems,” IEEE Trans. Wireless Commun. , vol. 23,
no. 4, pp. 3392–3407, Apr. 2024.
[19] L. Zhu, W. Ma, and R. Zhang, “Movable antennas for wireless commu-
nication: Opportunities and challenges,” IEEE Commun. Mag. , vol. 62,
no. 6, pp. 114–120, Jun. 2024.
[20] J. Ding, Z. Zhou, L. Zhu, Y . Zhao, B. Jiao, and R. Zhang, “Energy
efﬁciency maximization for movable antenna communication systems,”
2025, arXiv:2506.07129.
[21] X. Shao et al., “A tutorial on six-dimensional movable antenna for
6G networks: Synergizing positionable and rotatable antennas,” 2025,
arXiv:2503.18240.
[22] X. Shao, Q. Jiang, and R. Zhang, “6D movable antenna based on
user distribution: Modeling and optimization,” IEEE Trans. Wireless
Commun., vol. 24, no. 1, pp. 355–370, Jan. 2025.
[23] X. Shao, R. Zhang, Q. Jiang, and R. Schober, “6D movable
antenna enhanced wireless network via discrete position and rotation
optimization,” IEEE J. Sel. Areas Commun., vol. 43, no. 3, pp. 674–687,
Mar. 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

DING et al.: MOV ABLE ANTENNA-AIDED NEAR-FIELD INTEGRATED SENSING AND COMMUNICATION 507
[24] X. Shao and R. Zhang, “6DMA enhanced wireless network with ﬂexible
antenna position and rotation: Opportunities and challenges,” IEEE
Commun. Mag. , vol. 63, no. 4, pp. 121–128, Apr. 2025.
[25] X. Shao, R. Zhang, Q. Jiang, J. Park, T. Q. S. Quek, and R. Schober,
“Distributed channel estimation and optimization for 6D movable
antenna: Unveiling directional sparsity,” IEEE J. Sel. Topics Signal
Process., vol. 19, no. 2, pp. 349–365, Mar. 2025.
[26] W. Ma, L. Zhu, and R. Zhang, “Movable antenna enhanced wireless
sensing via antenna position optimization,” IEEE Trans. Wireless Com-
mun., vol. 23, no. 11, pp. 16575–16589, Nov. 2024.
[27] H. Qin, W. Chen, Q. Wu, Z. Zhang, Z. Li, and N. Cheng, “Cram ´er–Rao
bound minimization for movable antenna-assisted multiuser integrated
sensing and communications,” IEEE Wireless Commun. Lett. , vol. 13,
no. 12, pp. 3404–3408, Dec. 2024.
[28] X. Shao, R. Zhang, and R. Schober, “Exploiting six-dimensional mov-
able antenna for wireless sensing,” IEEE Wireless Commun. Lett. ,
vol. 14, no. 2, pp. 265–269, Feb. 2025.
[29] J. Ding, Z. Zhou, W. Li, C. Wang, L. Lin, and B. Jiao, “Movable antenna-
enabled co-frequency co-time full-duplex wireless communication,”
IEEE Commun. Lett. , vol. 28, no. 10, pp. 2412–2416, Oct. 2024.
[30] J. Ding, Z. Zhou, C. Wang, W. Li, L. Lin, and B. Jiao, “Secure full-
duplex communication via movable antennas,” in Proc. IEEE Global
Commun. Conf. (GLOBECOM) , Cape Town, South Africa, Dec. 2024,
pp. 885–890.
[31] J. Ding, Z. Zhou, and B. Jiao, “Movable antenna-aided secure full-duplex
multi-user communications,” IEEE Trans. Wireless Commun. , vol. 24,
no. 3, pp. 2389–2403, Mar. 2025.
[32] L. Lin, J. Ding, Z. Zhou, and B. Jiao, “Power-efﬁcient full-duplex
satellite communications aided by movable antennas,” IEEE Wireless
Commun. Lett. , vol. 14, no. 3, pp. 656–660, Mar. 2025.
[33] S. Peng et al., “Joint antenna position and beamforming optimiza-
tion with self-interference mitigation in MA-ISAC system,” 2024,
arXiv:2408.00413.
[34] Z. Li et al., “Joint discrete antenna positioning and beamforming
optimization in movable antenna enabled full-duplex ISAC networks,”
2024, arXiv:2411.04419.
[35] Y . Guo et al., “Movable antenna enhanced networked full-duplex inte-
grated sensing and communication system,” 2024, arXiv:2411.09426.
[36] Y . Sun, H. Xu, C. Ouyang, and H. Yang, “Rotatable and mov-
able antenna-enabled near-ﬁeld integrated sensing and communication,”
2025, arXiv:2501.04490.
[37] Y . Wang, W. Mei, X. Wei, B. Ning, and Z. Chen, “Antenna position
optimization for movable antenna-empowered near-ﬁeld sensing,” 2025,
arXiv:2502.03169.
[38] X. Shao et al., “Hybrid near-far ﬁeld 6D movable antenna design exploit-
ing directional sparsity and deep learning,” 2025, arXiv:2506.15808.
[39] J. Ding, L. Zhu, Z. Zhou, B. Jiao, and R. Zhang, “Near-ﬁeld multiuser
communications aided by movable antennas,” IEEE Wireless Commun.
Lett., vol. 14, no. 1, pp. 138–142, Jan. 2025.
[40] L. Zhu, W. Ma, Z. Xiao, and R. Zhang, “Movable antenna
enabled near-ﬁeld communications: Channel modeling and performance
optimization,” IEEE Trans. Commun. , early access, Mar. 4, 2025, doi:
10.1109/TCOMM.2025.3547783.
[41] Y . Liu, Z. Wang, J. Xu, C. Ouyang, X. Mu, and R. Schober, “Near-
ﬁeld communications: A tutorial review,” IEEE Open J. Commun. Soc. ,
vol. 4, pp. 1999–2049, 2023.
[42] Z. Wang, X. Mu, and Y . Liu, “Near-ﬁeld integrated sensing and
communications,” IEEE Commun. Lett. , vol. 27, no. 8, pp. 2048–2052,
Aug. 2023.
[43] D. Galappaththige, S. Zargari, C. Tellambura, and G. Y . Li, “Near-
ﬁeld ISAC: Beamforming for multi-target detection,” IEEE Wireless
Commun. Lett. , vol. 13, no. 7, pp. 1938–1942, Jul. 2024.
[44] M. Duarte, C. Dick, and A. Sabharwal, “Experiment-driven characteri-
zation of full-duplex wireless systems,” IEEE Trans. Wireless Commun.,
vol. 11, no. 12, pp. 4296–4307, Dec. 2012.
[45] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. Eldar, “Joint
transmit beamforming for multiuser MIMO communications and MIMO
radar,” IEEE Trans. Signal Process. , vol. 68, pp. 3929–3944, 2020.
[46] F. Liu, C. Masouros, A. P. Petropulu, H. Grifﬁths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun., vol. 68, no. 6, pp. 3834–3862, Jun.
2020.
[47] J. Wang and D. P. Palomar, “Worst-case robust MIMO transmission with
imperfect channel knowledge,” IEEE Trans. Signal Process. , vol. 57,
no. 8, pp. 3086–3100, Aug. 2009.
[48] S. Boyd and L. Vandenberghe, Convex Optimization. Cambridge, U.K.:
Cambridge Univ. Press, 2004.
[49] P. Stoica, J. Li, and Y . Xie, “On probing signal design for MIMO radar,”
IEEE Trans. Signal Process. , vol. 55, no. 8, pp. 4151–4161, Aug. 2007.
[50] C. Ouyang, Y . Liu, H. Yang, and N. Al-Dhahir, “Integrated sensing
and communications: A mutual information-based framework,” IEEE
Commun. Mag. , vol. 61, no. 5, pp. 26–32, May 2023.
[51] M. R. Bell, “Information theory and radar waveform design,” IEEE
Trans. Inf. Theory , vol. 39, no. 5, pp. 1578–1597, Sep. 1993.
[52] G. Hu et al., “Movable antennas-enabled two-user multicasting: Do we
really need alternating optimization for minimum rate maximization?,”
IEEE Trans. V eh. Technol., vol. 74, no. 3, pp. 5135–5140, Mar. 2025.
[53] D. Xu, X. Yu, Y . Sun, D. W. K. Ng, and R. Schober, “Resource
allocation for IRS-assisted full-duplex cognitive radio systems,” IEEE
Trans. Commun., vol. 68, no. 12, pp. 7376–7394, Dec. 2020.
[54] Q. Li, W. Mei, B. Ning, and R. Zhang, “Minimizing movement delay for
movable antennas via trajectory optimization,” 2024, arXiv:2408.12813.
[55] B. Ning et al., “Movable antenna-enhanced wireless communications:
General architectures and implementation methods,” IEEE Wireless
Commun., early access, May 19, 2025, doi: 10.1109/MWC.013.2400238.
[56] K. Chen, C. Qi, Y . Hong, and C. Yuen, “REMAA: Reconﬁgurable
pixel antenna-based electronic movable-antenna arrays for multiuser
communications,” 2025, arXiv:2504.00787.
Jingze Ding (Graduate Student Member, IEEE)
received the B.E. degree in information engineer-
ing from the University of Electronic Science and
Technology of China (UESTC), Chengdu, China,
in 2022. He is currently pursuing the Ph.D. degree
with the School of Electronics, Peking University,
Beijing, China. His research interests include ﬂexible
antenna and optimization techniques.
Zijian Zhou (Member, IEEE) received the B.Eng.
degree in information engineering from Soochow
University, Suzhou, China, in 2020. He is currently
pursuing the Ph.D. degree with the School of Sci-
ence and Engineering, The Chinese University of
Hong Kong, Shenzhen, China. From 2020 to 2024,
he was a Research Assistant with the School of
Electronics, Peking University, Beijing, China. His
research interests include polarforming for wireless
communications, movable antenna (MA)-enabled
communication systems, and convex optimization.
He was honored as a Chun-Tsung Scholar of Soochow University in 2019.
Xiaodan Shao (Member, IEEE) received the Ph.D.
degree in information and communication engi-
neering from Zhejiang University, China, in 2022.
From 2021 to 2022, she was a Visiting Research
Scholar with the National University of Singapore,
Singapore. From 2022 to 2024, she was a Hum-
boldt Research Fellow with the Institute for Digital
Communications, Friedrich-Alexander-University of
Erlangen-Nuremberg (FAU), Erlangen, Germany.
She is currently a Post-Doctoral Fellow with the
University of Waterloo, Waterloo, ON, Canada. Her
current research interests include six-dimensional movable antenna (6DMA),
integrated sensing and communications (ISAC), massive access, statistical
signal processing, and optimization methods. She was a recipient of the
Best Ph.D. Thesis Award of China Institute of Communications in 2023
and the IEEE International Conference on Wireless Communications and
Signal Processing (WCSP) Best Paper Award in 2020. She serves as a
Guest Editor for Electronics and an Associate Editor for IEEE W IRELESS
COMMUNICATIONS LETTERS .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

508 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Bingli Jiao (Senior Member, IEEE) received the
B.S. and M.S. degrees from Peking University, Bei-
jing, China, in 1983 and 1988, respectively, and the
Ph.D. degree from Saarland University, Saarbrcken,
Germany, in 1995. He became an Associate Profes-
sor in 1995 and a Professor with Peking University
in 2000. He is currently the Director of the Joint
Laboratory for Advanced Communication Research,
Peking University and Geespace. He is a pioneer of
co-frequency and co-time full-duplex as found in his
early patent in 2006. His research interests include
full-duplex communications, information theory, and signal processing.
Rui Zhang (Fellow, IEEE) received the B.Eng.
(Hons.) and M.Eng. degrees from the National
University of Singapore, Singapore, and the Ph.D.
degree from Stanford University, Stanford, CA,
USA, all in electrical engineering.
From 2007 to 2009, he was a Researcher with
the Institute for Infocomm Research, ASTAR, Singa-
pore. In 2010, he joined the Department of Electrical
and Computer Engineering, National University of
Singapore, where he was appointed as a Provost’s
Chair Professor in 2020. He is currently with the
School of Science and Engineering, Shenzhen Research Institute of Big Data,
The Chinese University of Hong Kong, Shenzhen, as a Principal’s Diligence
Chair Professor. He has published over 300 journal articles and over 200
conference papers. He has been listed as a Highly Cited Researcher by
Thomson Reuters/Clarivate Analytics since 2015. His current research inter-
ests include UA V/satellite communications, wireless power transfer, intelligent
reﬂecting surface, reconﬁgurable MIMO, radio mapping, and optimization
methods.
Dr. Zhang is a fellow of the Academy of Engineering Singapore. He
was a recipient of the Sixth IEEE Communications Society Asia–Paciﬁc
Region Best Young Researcher Award in 2011, the Young Researcher Award
of National University of Singapore in 2015, the Wireless Communications
Technical Committee Recognition Award in 2020, the IEEE Signal Processing
and Computing for Communications (SPCC) Technical Recognition Award
in 2021, and the IEEE Communications Society Technical Committee on
Cognitive Networks (TCCN) Recognition Award in 2023. His works received
the 18 IEEE Best Journal Paper Awards, including the IEEE Marconi Prize
Paper Award in Wireless Communications in 2015 and 2020; the IEEE Signal
Processing Society Best Paper Award in 2016; the IEEE Communications
Society Heinrich Hertz Prize Paper Award in 2017, 2020, and 2022; and
the IEEE Communications Society Stephen O. Rice Prize in 2021. He
served for over 30 international conferences as the TPC co-chair and an
organizing committee member. He was an Elected Member of the IEEE
Signal Processing Society SPCOM Technical Committee from 2012 to 2017
and the SAM Technical Committee from 2013 to 2015. He served as
the Vice Chair for the IEEE Communications Society Asia-Paciﬁc Board
Technical Affairs Committee from 2014 to 2015. He served as an Editor
for IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS from 2012
to 2016, IEEE J OURNAL ON SELECTED AREAS IN COMMUNICATIONS :
Green Communications and Networking Series from 2015 to 2016, IEEE
TRANSACTIONS ON SIGNAL PROCESSING from 2013 to 2017, IEEE T RANS -
ACTIONS ON GREEN COMMUNICATIONS AND NETWORKING from 2016 to
2020, and IEEE T RANSACTIONS ON COMMUNICATIONS from 2017 to 2022.
He served as a member for the Steering Committee of IEEE W IRELESS
COMMUNICATIONS LETTERS from 2018 to 2021. He was a Distinguished
Lecturer of the IEEE Signal Processing Society and the IEEE Communications
Society from 2019 to 2020.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:09 UTC from IEEE Xplore.  Restrictions apply.
