---
title: "LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in Near-Field ISAC Systems"
zotero_key: "YLGH28E2"
pdf_key: "3HTHUFEE"
doi: "10.1109/JSAC.2025.3643394"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# LLM in V2I: A Data-Driven Predictive Beamforming Framework for Vehicle Tracking in Near-Field ISAC Systems — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

2510 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
LLM in V2I: A Data-Driven Predictive
Beamforming Framework for Vehicle
Tracking in Near-Field ISAC Systems
Hongjia Huang
 , Graduate Student Member , IEEE , Weijie Yuan
 , Senior Member , IEEE,
Chang Liu
 , Member , IEEE, Liang Liu
 , Senior Member , IEEE, Fan Liu
 , Senior Member , IEEE,
Wei Xiang
 , Senior Member , IEEE, and Derrick Wing Kwan Ng
 , Fellow, IEEE
Abstract—In this paper, we investigate the problem of predic-
tive beamforming design for tracking vehicles in an integrated
sensing and communication (ISAC)-based near-ﬁeld vehicle-to-
infrastructure (V2I) system. The waveform design in near-ﬁeld
scenarios requires the joint consideration of both range and angle
dimensions, posing new challenges to conventional beamforming
and tracking strategies. To address this issue, we propose a
predictive beamforming framework leveraging a large language
model (LLM)-based neural network (LNN), which exploits histor-
ical channel state information (CSI) to facilitate accurate future
beamforming decisions. Cram ´er–Rao bounds (CRBs) for angle
and distance estimation, along with the achievable sum-rate, are
applied as key metrics to evaluate the sensing and communication
performance of the V2I system, respectively. Capitalizing on
the derived performance metrics, we formulate the optimization
problems aiming either to maximize the sum-rate subject to CRB
constraints or to minimize the CRB while ensuring a required
communication rate, thereby accommodating different design
Received 13 May 2025; revised 13 October 2025; accepted 4 December
2025. Date of publication 12 December 2025; date of current version
20 February 2026. This work was supported in part by the National Natural
Science Foundation of China under Grant 62471208, in part by Guang-
dong Provincial Natural Science Foundation under Grant 2024A151510098,
in part by Shenzhen Science and Technology Program under Grant
JCYJ20240813094627037 and Grant QNXMB20250701095411015, in part
by ZTE Industry-University-Institute Cooperation Funds under Grant
IA20240610003, in part by the La Trobe University Start-Up Package
under Grant 325011150, and in part by the La Trobe University Research
Project–School of Computing, Engineering and Mathematical Sciences
(SCMES) CaRE and Beyond Scheme under Grant 401310405. (Correspond-
ing author: Weijie Yuan.)
Hongjia Huang is with the Guangdong Provincial Key Laboratory of Fully
Actuated System Control Theory and Technology, School of Automation and
Intelligent Manufacturing, Southern University of Science and Technology,
Shenzhen 518055, China, and also with the Department of Electrical and
Electronic Engineering, The Hong Kong Polytechnic University, Hong Kong,
SAR, China (e-mail: hongj.huang@connect.polyu.hk).
Weijie Yuan is with the Guangdong Provincial Key Laboratory of Fully
Actuated System Control Theory and Technology, School of Automation and
Intelligent Manufacturing, Southern University of Science and Technology,
Shenzhen 518055, China (e-mail: yuanwj@sustech.edu.cn).
Chang Liu and Wei Xiang are with the Department of Computer Science
and Information Technology, La Trobe University, Melbourne, VIC 3086,
Australia (e-mail: C.Liu6@latrobe.edu.au; w.xiang@latrobe.edu.au).
Liang Liu is with the Department of Electrical and Electronic Engineering,
The Hong Kong Polytechnic University, Hong Kong, SAR, China (e-mail:
liang-eie.liu@polyu.edu.hk).
Fan Liu is with the National Mobile Communications Research Laboratory,
Southeast University, Nanjing 210096, China (e-mail: f.liu@ieee.org).
Derrick Wing Kwan Ng is with the School of Electrical Engineering and
Telecommunications, University of New South Wales, Sydney, NSW 2052,
Australia (e-mail: w.k.ng@unsw.edu.au).
Digital Object Identiﬁer 10.1109/JSAC.2025.3643394
requirements. Moreover, to effectively capture the stochastic
nature of vehicle driving behavior, the performance metrics are
further expressed in expectation form over the distribution of
possible driving states. Consequently, a data-driven optimization
approach based on the LNN is adopted to handle the resulting
intractable analytical expressions, and the underlying LNN is
trained with task-speciﬁc loss functions. During the training
process, low-rank adaptation (LoRA) is incorporated to ﬁne-tune
the pre-trained LLM, which signiﬁcantly reduces the number
of trainable parameters. Simulation results demonstrate that the
proposed framework accurately predicts future vehicle kinematic
parameters and effectively optimizes the power allocation across
transmit links. As a result, it achieves superior and robust per-
formance in both communication and sensing tasks, highlighting
its potential as a vital solution for next-generation near-ﬁeld V2I
systems.
Index Terms—Near-ﬁeld communication, mobile vehicle track-
ing, integrated sensing and communication (ISAC), deep learning
(DL), large language model (LLM).
I. I NTRODUCTION
A. Motivation
W
ITH the evolution toward beyond ﬁfth-generation
(B5G) systems, characterized by extremely large-scale
antenna arrays and the operation of high-frequency bands (e.g.,
millimeter-wave and terahertz), future sensing and commu-
nication systems are anticipated to increasingly function in
the near-ﬁeld region [1], [2]. In contrast to conventional far-
ﬁeld regimes where planar wavefront assumptions dominate,
near-ﬁeld propagation is governed by spherical wavefronts,
resulting in channel responses that jointly depend on both
range and angular domains. Such dependency introduces new
challenges to beamforming design and channel estimation
[3], fundamentally reshaping traditional communication and
sensing paradigms. Nevertheless, the incorporation of the
range dimension also unlocks new degrees of freedom for
enhancing spatial discrimination capabilities [1], [4]. In partic-
ular, near-ﬁeld beamforming enables energy focusing toward
speciﬁc spatial locations, which are inherently unattainable
under far-ﬁeld conditions that are limited to angular-domain
beam control. These unique challenges and properties have
sparked growing research interest in the exploration of near-
ﬁeld integrated sensing and communication (ISAC) systems
[5], [6], [7], [8], [9].
1558-0008 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2511
Alongside the development of large-scale antenna arrays,
emerging paradigms such as ﬂuid antenna systems (FAS)
are being explored to introduce new degrees of freedom by
dynamically optimizing antenna positions for superior spatial
diversity [10]. The synergy of combining FAS with ISAC is
also gaining considerable attention, as intelligent antenna posi-
tioning can potentially enhance both communication quality
and sensing accuracy simultaneously [11], [12]. The seamless
integration of sensing and communication functionalities pro-
vides a promising foundation for enabling intelligent trafﬁc
management in vehicle-to-infrastructure (V2I) networks [13],
[14]. However, regardless of the underlying antenna technol-
ogy, maintaining stable communication links and ensuring
accurate localization in high-mobility scenarios requires revis-
iting conventional beamforming and tracking strategies to
accommodate the unique characteristics introduced by near-
ﬁeld propagation [15]. In particular, the joint range-angle
dependency, coupled with rapidly time-varying channels typi-
cally in V2I environments, introduces signiﬁcant challenges
to predictive beamforming techniques. Motivated by these
observations, we propose a large language model (LLM)-based
predictive beamforming framework that leverages historical
channel state information (CSI) to predict future beamform-
ing directions. By simultaneously modeling temporal channel
evolution and its spatial patterns, the proposed framework
aims to jointly enhance communication robustness and sensing
accuracy in near-ﬁeld V2I systems.
B. Prior Work
Several works have investigated the beamforming design
problem in near-ﬁeld scenarios [16], [17], [18]. For instance,
in [16], the unique characteristics of near-ﬁeld channels were
explicitly exploited to develop beamforming strategies tailored
for multi-user MIMO systems, demonstrating enhanced inter-
ference mitigation ability through enhanced spatial focusing.
Furthermore, in [17], the authors jointly designed the wave-
form for communication users and the transmit covariance
matrix for target estimation, with the objective of mini-
mizing the Cram ´er–Rao bound (CRB) under user-speciﬁc
rate constraints. In addition, [18] analyzed the performance
degradation caused by applying far-ﬁeld steering vectors to
near-ﬁeld signal modeling, and accordingly proposed beam-
forming designs to minimize transmit power while maintaining
satisfactory system performance.
While these studies offer valuable insights, they often
assume static user or target positions, limiting their direct
applicability to highly dynamic vehicular scenarios. In the
far-ﬁeld regime, predictive beamforming under high-mobility
conditions has been extensively studied. For example, the con-
ventional extended Kalman ﬁlter (EKF) was applied in [13] to
predict vehicular kinematic parameters, with a similar method
employed in [19] to track extended targets. Furthermore,
[20] investigated predictive transmit beamforming in vehicular
networks based on orthogonal time frequency space (OTFS)
waveforms, leveraging the slow time-varying properties of
delay-Doppler (DD) channels to accurately predict future
angles and motion trajectories. However, these methods are
primarily developed under far-ﬁeld assumptions and therefore
do not account for the critical range–angle coupling character-
istics inherent to near-ﬁeld propagation. As a result, their direct
application to near-ﬁeld scenarios may lead to degraded beam-
forming performance. Recent advancements in [21] and [22]
focus on near-ﬁeld mobile target scenarios, where estimation
problems are formulated and their solutions are subsequently
used for beamforming vector design. While pioneering, this
approach requires iterative optimization at each time step,
resulting in substantial computational overhead for real-time
V2I deployment. Therefore, there is an urgent need to develop
more efﬁcient predictive beamforming networks for near-ﬁeld
environments.
In response, deep learning-based approaches have gained
traction for beam prediction and tracking in vehicular net-
works, offering improved efﬁciency and faster inference
compared to traditional iterative methods [23], [24], [25], [26],
[27], [28]. Speciﬁcally, a deep feedforward neural network
(NN) was employed in [29] to predict angle information
in subsequent time slots, which was subsequently exploited
for beamforming design in ISAC-enabled V2I systems. To
better capture temporal correlations, [30] proposed a long
short-term memory (LSTM)-based model, demonstrating sat-
isfactory performance in both communication and sensing
metrics. Furthermore, an attention-augmented LSTM architec-
ture was introduced in [31] to enhance prediction accuracy
by selectively attending to relevant historical states. Despite
their effectiveness in far-ﬁeld scenarios, their generalization
to near-ﬁeld applications remains limited due to the increased
channel complexity and nonlinear spatio-temporal dependen-
cies introduced by spherical propagation wavefronts. As a
result, more expressive architectures are required to better
model such complexity in the near-ﬁeld scenario. Recently,
LLMs have emerged as a promising paradigm for physical-
layer optimization tasks [32], [33], [34]. It has been proven in
[35] that LLM-based approaches can outperform conventional
NNs in terms of beam prediction accuracy. Motivated by this,
an LLM-based network is introduced to perform predictive
beamforming in this work.
C. Contribution
From the aforementioned prior works, it can be observed
that existing beamforming investigations in near-ﬁeld scenar-
ios either assume static users or rely on computationally inten-
sive optimization procedures. These limitations signiﬁcantly
hinder their scalability to dynamic near-ﬁeld V2I systems,
thereby motivating the need for an efﬁcient and expres-
sive predictive beamforming approach. Moreover, although
[35] investigates the beam prediction problem, it focuses on
the conventional far-ﬁeld scenario and evaluates performance
solely based on the normalized beamforming gain. To over-
come these limitations, this work develops a novel data-driven
vehicle tracking framework that leverages a pre-trained LLM
to enable predictive beamforming in near-ﬁeld environments.
The proposed beamforming design explicitly accounts for both
sensing and communication objectives, providing a more com-
prehensive and balanced performance evaluation. The main
contributions are summarized as follows:
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2512 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
• We propose a predictive beamforming framework tai-
lored for ISAC-based near-ﬁeld V2I systems, where
an LLM-based neural network (LNN) is developed to
effectively extract temporally correlated spatial features
from historical CSI, facilitating accurate generation of
the beamforming matrix for the subsequent time slot. To
evaluate the sensing capability, we derive the CRBs for
estimating the kinematic parameters of the vehicles, while
the achievable communication rate is adopted as a metric
to assess the communication performance.
• Based on the derived performance metrics, we formu-
late optimization problems that either aim to maximize
overall communication rate subject to CRB constraints
or minimize the estimation error bounds while ensur-
ing satisfactory communication rates. These optimization
problems, characterized by different objectives, are inves-
tigated to adapt various performance priorities between
sensing and communication. Moreover, we incorporate
expectation operations into the performance metrics to
explicitly model uncertainties arising from the random
driving behavior of vehicles, thereby enhancing the
robustness of the resulting beamforming strategy.
• To address the intractable expressions arising from the
expectation operations in the formulated optimization
problem, the proposed LNN enables an end-to-end map-
ping from historical channel observations directly to the
future beamforming matrix, thereby bypassing explicit
intermediate parameter prediction. A transformer-based
encoder is employed to convert raw CSI into a sequence
of high-dimensional embeddings, allowing the subse-
quent LLM module to exploit its pattern-recognition
capability for effective temporal sequence modeling.
Furthermore, to enhance training efﬁciency, low-rank
adaptation (LoRA) is applied for ﬁne-tuning, updating
only a small subset of parameters while keeping the base
model weights frozen [36]. Simulation results demon-
strate that the proposed LNN effectively handles the
optimization problems and outperforms the baselines in
both communication and sensing performance.
The remainder of this paper is structured as follows.
Section II introduces the system model of the considered
near-ﬁeld ISAC-based V2I network. Section III derives the
CRBs for vehicle state estimation and formulates the corre-
sponding beamforming optimization problems. In Section IV,
we present the proposed predictive beamforming framework,
including the network architecture of the LNN, training
methodology, and loss function design. Simulation results
are provided in Section V to validate the effectiveness of
the proposed framework under various evaluation metrics
and baseline comparisons. Finally, conclusions are drawn in
Section VI.
Notations: Throughout this paper, bold uppercase letters
(e.g.,A), bold lowercase letters (e.g., a), and non-bold letters
(e.g., a) are used to denote matrices, vectors, and scalars,
respectively. The sets of complex and real numbers are denoted
by C and R. Superscripts T , *, and H represent the trans-
pose, complex conjugate, and Hermitian (conjugate transpose)
operations, respectively. The circularly symmetric complex
Fig. 1. Illustration of the considered near-ﬁeld V2I system, where the RSU
aims to continuously track the vehicles.
Gaussian distribution with mean vector µ and covariance
matrix Σ is denoted by CN (µ, Σ), while N (µ, Σ) denotes
the real-valued Gaussian distribution. The uniform distribu-
tion over the interval [a,b ] is represented by U(a,b ). The
N-dimensional identity matrix is denoted by IN . The sta-
tistical expectation operator is written as E[·]. The Euclidean
norm of a vector is denoted by ‖·‖ , and |·| indicates the
magnitude of a complex number. Finally, diag(x) denotes a
diagonal matrix formed from vector x.
II. S YSTEM MODEL
In this paper, we investigate an ISAC-based near-ﬁeld V2I
network, where the roadside unit (RSU) aims to serve P
single-antenna vehicles, as shown in Fig. 1. The RSU is
equipped with a uniform linear array (ULA) consisting of
¯M = 2M + 1 transmit antennas and ¯N = 2N + 1 receive
antennas. Accordingly, the index sets of the transmit and
receive antennas are deﬁned as M = {−M,...,M } and
N ={−N,...,N }, respectively. Without loss of generality,
the central antennas of each array (i.e., the 0-th elements) are
selected as reference antennas. To mitigate mutual coupling
effects, the antenna spacing is conﬁgured as ϵ = λ/2, where
λ denotes the signal carrier wavelength. Furthermore, we
assume that both the transmit and receive antenna arrays are
sufﬁciently isolated, ensuring negligible interference between
transmitted and received signals [20].
A. Tracking Protocol
To continuously serve the vehicles with reduced signaling
overhead, the RSU operates under a predictive tracking pro-
tocol that leverages historical channel state information (CSI)
to anticipate future system states. Speciﬁcally, the tracking
process begins with an initialization phase, during which the
RSU functions as a monostatic radar to acquire the initial
kinematic states of all vehicles, establishing the foundation for
subsequent predictions. At each time slot l, the RSU transmits
an ISAC signal that simultaneously delivers communication
data and captures echoes reﬂected by vehicles for sensing
purposes, as shown in Fig. 2. The downlink waveform is
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2513
Fig. 2. The operation ﬂow of tracking protocol at each time slot.
adaptively designed based on the historical CSI. In parallel, the
RSU processes the received echoes to obtain updated sensing
information for reﬁning vehicle-state estimates, from which it
reconstructs the CSI corresponding to the current time slot.
The newly estimated channel matrix is then appended to the
set of historical observations and subsequently used to design
the beamforming matrix for the next (l + 1)-th time slot. By
maintaining a continuous prediction–measurement cycle, the
RSU dynamically adapts its beamforming strategy to serve the
vehicles. To ensure reliable performance in both communica-
tion and sensing, the beamforming matrix is jointly designed to
enhance communication quality-of-service (QoS) while main-
taining sufﬁcient estimation accuracy. Such a uniﬁed design
enables the near-ﬁeld ISAC system to operate robustly under
dynamic vehicular conditions without compromising either
functionality.
Moreover, the proposed protocol establishes an end-to-end
mapping from historical channel observations directly to the
subsequent beamforming matrix, thereby eliminating the need
for explicit beam training or separate motion-parameter and
channel prediction. Consequently, it avoids the substantial
time and radio-resource overhead associated with sweeping-
based beam training, as well as the additional computa-
tional complexity and potential model mismatch inherent in
model-driven prediction approaches [37], [38].
B. Sensing Model
Let sl(t) = [ s1,l(t),...,s P,l(t)]T ∈ CP×1 denote the
transmit signal vector intended for all P vehicles during
the l-th time slot, where sp,l(t)∼ CN(0, 1) represents the
modulated data symbol for vehicle p ∈ {1,...,P }. After
applying beamforming, the transmit signal of the RSU at the
l-th time slot is given by
xl(t) =Wlsl(t),∀l, (1)
where Wl ∈ C ¯N×P is the beamforming matrix designed
based on the channel state information (CSI) of the previous
time slots. The signal xl(t) is leveraged for both commu-
nication and sensing, i.e., each vehicle decodes its intended
data symbol from xl(t), while the RSU captures the signal
reﬂections to enable target sensing [30].
We ﬁrst characterize the adopted sensing model of the
considered near-ﬁeld V2I system. Deﬁne φp,l and θp,l as the
angle of departure (AoD) and angle of arrival (AoA) for
vehicle p during the l-th time slot, respectively. Under the
Fresnel approximation [18], [39], the corresponding transmit
and receive steering vectors can be expressed as
a (φp,l,dp,l) =
√
1
¯M
[
e
j2π
λ
(
−Mϵ cosφp,l−M 2ϵ22dp,l sin2φp,l),
...,e
j2π
λ
(
Mϵ cosφp,l−M 2ϵ22dp,l sin2φp,l)],∀p,l,
(2)
b (θp,l,rp,l) =
√
1
¯N
[
e
j2π
λ
(
−Nϵ cosθp,l−N 2ϵ22rp,l sin2θp,l),
...,e
j2π
λ
(
Nϵ cosθp,l−N 2ϵ22rp,l sin2θp,l)],∀p,l,
(3)
where dp,l and rp,l are the distances between the p-th vehicle
and the reference transmit and receive antennas, respectively.
Based on the steering vectors deﬁned above, the aggregated
echo signal received at the RSU from all vehicles at the l-th
time slot can be expressed as [22]
yl(t) =γ
P∑
p=1
αp,lVp,l(t)b(θp,l,rp,l)
×aH(φp,l,dp,l)Up,l(t)xl(t) +zl(t), ∀l, (4)
where γ =
√ ¯M ¯N denotes the array gain, αp,l represents
the propagation attenuation for the p-th vehicle, zl(t) ∼
CN (0,δ 2I ¯N) is the additive white Gaussian noise (AWGN),
and δ2 is the noise power per receive antenna. Moreover,
Up,l(t)∈ C ¯M× ¯M andVp,l(t)∈ C ¯N× ¯N are diagonal matrices
that contain the Doppler shift terms, which can be given by
Up,l(t) = diag
(
e
j2π
λ u−M,p,lt,...,e j2πλ uM,p,lt), ∀p,l, (5)
Vp,l(t) = diag
(
e
j2π
λ v−N,p,lt,...,e j2πλ vN,p,lt), ∀p,l, (6)
whereum,p,l andvn,p,l denote the radial velocity of vehicle p
relative to m-th transmit and n-th receive antenna at l-th time
slot. In equation (4), we assume that the propagation coefﬁ-
cients across all transmit–receive antenna pairs associated with
the same vehicle are approximately equal. This assumption
generally holds under the Fresnel approximation and is widely
applied in near-ﬁeld ISAC system modeling [40].
In the considered near-ﬁeld scenario, a vehicle may exhibit
slightly different radial velocities with respect to each transmit
or receive antenna, as demonstrated in equation (4) [21],
[22]. Nevertheless, when the signal duration T is sufﬁciently
short such that
⏐⏐⏐um,p,l−u0,p,lλ ⏐⏐⏐t ≪ 1, the induced phase
shifts across antennas become approximately equal, 1 i.e.,
e
j2π
λ um,p,lt≈ej2πλ u0,p,lt,∀m, and similarly for the receive side
[41]. Accordingly, the Doppler shift matrices can be simpliﬁed
as
˜Up,l =e
j2π
λ up,ltI ¯M, ˜Vp,l =ej2πλ vp,ltI ¯N, ∀p,l, (7)
1For example, assume that the maximum relative radial velocity across the
array aperture is less than 0.25 m/s. Given a wavelength of λ = 0.03 m and
a coherent processing interval of T = 2 ms, the term on the left-hand side of
the inequality is on the order of 10−2, which is much smaller than 1. Then,
this T can be regarded as a sufﬁciently short coherent interval.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2514 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
where up,l = u0,p,l and vp,l = v0,p,l denote the radial
velocity relative to the reference transmit and receive antennas,
respectively. Based on (7), the received echo signal model (4)
reduces to
˜yl(t) =γ
P∑
p=1
αp,lb(θp,l,rp,l)aH(φp,l,dp,l)
×xl(t)e
j2π
λ µp,lt +zl(t), ∀l, (8)
whereµp,l =up,l+vp,l is the sum radial velocity. Note that the
near-ﬁeld steering vectors preserve asymptotic orthogonality
[42], which can be mathematically given by
lim
¯N→∞
|bH(θ,r )b(θ′,r′)| = 0, ∀θ⁄=θ′or r⁄=r′. (9)
By exploiting the above property and applying appropriate
interference suppression techniques [43], the RSU can isolate
the echo from the p-th vehicle as
˜yp,l(t) =γαp,lb(θp,l,rp,l)aH(φp,l,dp,l)
×wp,lsp,l(t)e
j2π
λ µp,lt + ˜zp,l(t), ∀p,l, (10)
wherewp,l is thep-th column of the beamforming matrixWl,
and ˜zp,l(t)∼CN (0, ˜δ2I ¯N) with ˜δ2 be the noise power. The
RSU can then utilize ˜yp,l(t) to estimate the kinematic states
of each vehicle.
C. Measurement Model
Although the signal model presented in (10) contains a
substantial number of unknowns, these can be estimated
individually and their geometric relationships can be leveraged
to simplify the estimation procedure. The estimation of the
velocity parameterµp,l can be achieved exploiting the conven-
tional matched ﬁlter [13], which is mathematically expressed
as
ˆµp,l = arg maxµ
⏐⏐⏐⏐⏐∫ Ts0 ˜yp,l(t)s∗p,l(t)e−j2πλ µtdt⏐⏐⏐⏐⏐2, ∀p,l,
(11)
where Ts is the duration of the echo received at the RSU.
Once the velocity estimate ˆµp,l is obtained, the observation
model for the angle and distance parameters can be written as
¯yp,l =
∫ Ts
0
˜yp,l(t)s∗p,l(t)e−j2πλ ˆµp,ltdt
=γαp,lb(θp,l,rp,l)aH(φp,l,dp,l)wp,l
×
∫ Ts
0
sp,l(t)s∗p,l(t)ej2πλ (µp,l−ˆµp,l)tdt
+
∫ Ts
0
zp,l(t)s∗p,l(t)e−j2πλ ˆµp,ltdt
=γαp,lωp,lb(θp,l,rp,l)aH(φp,l,dp,l)wp,l + ¯zp,l, ∀p,l,
(12)
where ωp,l =
∫Ts
0 sp,l(t)s∗p,l(t)ej2πλ (µp,l−ˆµp,l)tdt is the
matched-ﬁlter gain, ¯zp,l ∼ CN(0, ¯δ2I ¯N) represents the
AWGN, and ¯δ2 is the noise power. Moreover, the measurement
model for the velocity µp,l is expressed as
¯µp,l =µp,l + zp,l, ∀p,l, (13)
where zp,l∼N (0, ˙δ2p,l) with ˙δ2p,l being the noise power. Note
that ˙δ2p,l is related to the signal-to-noise ratio (SNR) of the
receive signal model given in (10), which can be given by
˙δ2p,l = ϱκp,l (wp,l), ∀p,l, (14)
where ϱ is the scaling factor depending on the system set-up
and the speciﬁc estimation algorithm, and κp,l (wp,l) is the
SNR deﬁned as
κp,l (wp,l)=
E
[⏐⏐γαp,lb(θp,l,rp,l)aH(φp,l,dp,l)wp,lsp,l(t)⏐⏐2]
E
[
|˜zp,l(t)|2
]
=|γαp,l|2|aH(φp,l,dp,l)wp,l|2˜δ2 , ∀p,l. (15)
Consequently, from the derivation process given above, it is
evident that the estimation accuracy for kinematic state param-
eters of vehicles signiﬁcantly relies on the beamforming matrix
Wl. A well-designed Wl can substantially reduce estimation
errors by increasing the SNR, thereby improving the overall
sensing performance. Furthermore, as observed from (12)
and (15), near-ﬁeld beamforming design inherently involves
both range and angular dimensions, which increases the
design complexity and limits the applicability of conventional
far-ﬁeld strategies that rely solely on angular information.
D. Communication Model
Let ˜γ =
√ ¯M denote the array gain at the RSU. Then, the
received signal at vehicle p during the l-th time slot can be
written as
y(c)p,l = ˜γ ˜αp,laH(φp,l,dp,l)xl(t)ej2πλ up,lt + z(c)p,l
= ˜γhHp,lej2πλ up,lt P∑
p′=1
wp′,lsp′,l(t) + z(c)p,l, ∀p,l, (16)
where ˜αp,l is the path loss coefﬁcient, hHp,l =
˜αp,laH(φp,l,dp,l) is the equivalent downlink channel
vector, and z∼CN (0,σ 2p) is the AWGN with σ2p be the noise
power. Following the assumption made in the sensing model,
the Doppler shifts across all transmit antennas are assumed
to be identical for each vehicle.
Based on equation (16), the achievable communication rate
of vehicle p at l-th time slot is given by
Rp,l (Wl) = log2 (1 + ˜κp,l (Wl)), ∀p,l, (17)
where ˜κp,l (Wl) is the signal-to-interference-plus-noise ratio
(SINR) expressed as
˜κp,l (Wl) =
⏐⏐⏐˜γhHp,lwp,l⏐⏐⏐2
⏐⏐⏐⏐⏐˜γ P∑p′⁄=phHp′,lwp′,l⏐⏐⏐⏐⏐2 +σ2p, ∀p,l. (18)
Note that the achievable communication rate for each vehicle
is directly determined by its SINR, which in turn depends
on the beamforming design as shown in (18). Therefore,
analogous to the sensing case, optimizing the beamforming
matrix Wl is also critical in the communication domain, as
it enables effective suppression of inter-user interference and
enhancement of the desired signal strength.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2515
Fig. 3. The geometric relationships between angle and distance parameters.
III. P ROBLEM FORMULATION
In this paper, we focus on designing the beamforming
matrixWl to jointly optimize the sensing and communication
performance of the considered V2I system. To evaluate the
sensing performance, the CRB of the kinematic state esti-
mation error [30], [44] is adopted as a lower bound for the
estimation variance. Speciﬁcally, we ﬁrst derive the expression
of the CRB and an optimization problem is then formulated
to optimize the beamforming matrix at each time slot.
A. Derivation of the Cram ´er-Rao Bound
From the measurement model in (12), it is evident that
several unknown parameters are involved, including the AoA
θp,l, AoD φp,l, and the distance-related terms rp,l and dp,l.
However, the number of unknowns involved in the estima-
tion can be effectively reduced by exploiting the geometric
relationships among these parameters. As illustrated in Fig. 3,
bothφp,l anddp,l can be expressed as deterministic functions
of θp,l and rp,l, which can be given by
φp,l = arccos
(rp,l cosθp,l +a
dp,l
)
, (19)
dp,l =
√
r2p,l + 2arp,l cosθp,l +a2, ∀p,l. (20)
where a denotes the distance between the reference transmit
and receive antennas. Consequently, with equation (19) and
(20), the number of independent parameters can be reduced,
as both φp,l and dp,l become functions of θp,l and rp,l.
Consequently, the remaining unknowns to be estimated can
be collected into the vector ζp,l = [θp,l,rp,l,µp,l]T .
To derive the fundamental limits for the estimation error of
ζp,l, we begin by constructing the joint likelihood function
of the observations. For notation convenience, the subscripts
p and l are omitted in the following derivation without loss
of generality. Based on the measurement models in (12) and
(13), the joint conditional probability density function (PDF)
of ¯y and ¯µ givenζ is expressed as [45] and [46]
f(¯y, ¯µ|ζ)∝ exp
{
− 1¯δ2⏐⏐¯y−γαωb(θ,r )aH(φ,d )w⏐⏐2}
× exp
{
− 1˙δ2|¯µ−µ|2
}
. (21)
Based on this PDF, the Fisher information matrix (FIM)
associated with the unknown parameter vector ζ can be
derived to quantify the amount of information provided by
the observations. The corresponding CRB for the estimation
error of ζ is then obtained by taking the inverse of the FIM.
Let ˆζ = [ˆθ, ˆr, ˆµ]T be the unbiased estimation of ζ. The CRB
has the following form [45]:
Eζ
[
(ˆζ−ζ)(ˆζ−ζ)T
]
≽J−1ζ (w), (22)
where the FIM Jζ(w) is deﬁned as
Jζ(w) =−E¯y,¯µ|ζ
[∂2 lnf(¯y, ¯µ|ζ)
∂ζ∂ζT
]
. (23)
By substituting (21) into equation (23), we can obtain the
explicit form of the FIM, as summarized in the following
proposition.
Proposition 1: The FIM for ζ can be given by
[Jζ(w)]i,i′ =



2γ2|α|2|ω|2
¯δ2 Re
{
wHAi,jw}, i,i ′≤ 2,
2
˙δ2, i,i ′ = 3,
0, otherwise,
(24)
whereAi,i′∈ C ¯M× ¯M represents the partial derivative matri-
ces of the steering vectors b(θ,r ) and a(φ,d ) with respect
to ζ. The detailed expression of matrix Ai,i′ is given in
equation (50)
Proof: See Appendix A. ■
With Proposition 1, we proceed to characterize the detailed
expression of the CRB. Note that the FIM can be organized
into the block matrix form as
Jζ(w) =
[[Jζ(w)]2×2 ι
ιT 2˙δ2
]
, (25)
where ι = [0 , 0]T as shown in (24). By exploiting the
block structure in (25), the equivalent FIM (EFIM) for the
location-related parameters θ and r can be written as
Je(w) = [Jζ(w)]2×2−
( 2
˙δ2
)−1
ιιT = [Jζ(w)]2×2, (26)
while the EFIM for µ is expressed as
Jµ = 2˙δ2−ιT{[Jζ(w)]2×2}−1ι = 2˙δ2. (27)
Accordingly, the lower bounds for the estimation of the AoA
θ, the distance r, and the radial velocity µ are respectively
given by
Eθ
[
(ˆθ−θ)2
]
≥
[
J−1e (w)]1,1, (28)
Er
[
(ˆr−r)2]≥[J−1e (w)]2,2, (29)
Eµ
[
(ˆµ−µ)2]≥ ˙δ2
2 . (30)
By introducing the concept of EFIM, the CRB expressions
for the spatial and velocity parameters can be signiﬁcantly
simpliﬁed, clearly highlighting their explicit dependence on
the beamforming vector w. However, it is found that the
CRB remains a non-convex function of w due to the matrix
inversion operation. To address this challenge, we adopt a data-
driven approach to optimize the beamforming design, which
will be detailed in the subsequent section.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2516 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Remark 1: Although the parameters to be estimated are
identical in both far-ﬁeld and near-ﬁeld scenarios, the resulting
CRBs differ due to the distinct structures of the respective
observation models. In the far-ﬁeld case, angle and distance
parameters can be estimated independently, leading to a diag-
onal FIM and facilitating tractable CRB derivations [14],
[30]. In contrast, in the near-ﬁeld regime, angle and distance
are intrinsically coupled, resulting in non-diagonal FIMs and
more complex CRB formulations. This increased complexity
prevents the direct application of conventional beamforming
strategies developed under far-ﬁeld assumptions.
B. Problem F ormulation
In the previous section, we derived the expressions for the
achievable communication rate and the CRB, which serve as
performance metrics for evaluating the communication and
sensing capabilities of the considered V2I system. In practice,
vehicle states often exhibit random ﬂuctuations caused by
unpredictable driving behaviors, such as spontaneous accelera-
tion, deceleration, and minor trajectory deviations. To robustly
capture these stochastic variations, we formulate a beamform-
ing optimization problem that incorporates expectations over
the performance metrics, thereby enhancing system reliability
under uncertainty. Speciﬁcally, the expectation is taken over
the conditional probability distribution of future vehicle states
given their historical observations. To maintain generality, no
explicit analytical form is assumed for these distributions. At
time slot l, the beamforming design problem is formulated as
Pa : max{wp,l} EHl|Hl
{ P∑
p=1
Rp,l (Wl)
}
(31a)
s.t. Eθl|Θl
{
1
P
P∑
p=1
[
J−1e (wp,l)]1,1
}
≤ηθ,
(31b)
Erl|Rl
{
1
P
P∑
p=1
[
J−1e (wp,l)]2,2
}
≤ηr,
(31c)
P∑
p=1
||wp,l||2≤Q, (31d)
where Hl = [ h1,l,..., hP,l] denotes the complex down-
link channel matrix at the l-th time slot, and Hl ={
ˆHl−K,..., ˆHl−1
}
represents the set of estimated channel
states from the preceding K time slots, with ˆHl being
the estimations of Hl. Similarly, θl = [θ1,l,...,θ P,l]T and
rl = [r1,l,...,r P,l]T denote the true AoA and distance vectors
for all vehicles at time slot l. Θl =
{
ˆθl−K,..., ˆθl−1
}
and
Rl ={ˆrl−K,..., ˆrl−1} collect the past K estimated values
of AoA and distance, with ˆθl and ˆrl being the estimations of
θl andrl, respectively. Moreover, ηθ and ηr are the required
CRB for AoA and distance estimations. Q denotes the total
transmit power budget at the RSU.
The optimization problem Pa focuses on maximizing the
expected sum communication rate, subject to the constraints
in (31b) and (31c), which ensure sufﬁcient sensing ﬁdelity
for continuous vehicle tracking. Moreover, constraint (31d)
imposes a transmit power budget at the RSU. While Pa
primarily targets the enhancement of communication perfor-
mance in the V2I system, this formulation can be readily
extended to emphasize sensing performance by modifying the
objective function, leading to the following problem:
Pb : min{wp,l} Eθl|Θl
{
1
P
P∑
p=1
[
J−1e (wp,l)]1,1
}
(32a)
s.t. EHl|Hl
{ P∑
p=1
Rp,l (Wl)
}
≥ηs, (32b)
(31c) and (31d), (32c)
where ηs is the required sum-rate for all the vehicles. The
objective of Pb is to minimize the average CRB associated
with the AoA estimation errors. Alternatively, if the design
goal shifts toward distance estimation, the same framework
allows for direct substitution of the corresponding CRB metric
in the objective. By appropriately interchanging the roles
of the objectives and constraints, the proposed V2I system
can be ﬂexibly tailored to accommodate diverse performance
requirements, thereby enabling a uniﬁed framework for joint
communication and sensing optimization.
Remark 2: Note that the channel information from the
preceding K time slots is utilized as prior information when
designing the beamforming matrix. Indeed, introducing the
expectation operation allows the optimization to robustly
accommodate potential state variations in a probabilistic
manner. However, this expectation operation will result in
intractable closed-form expressions for the objective function
and constraints. In addition, the matrix inversion involved
in the CRB expressions introduces non-convexity into the
feasible set. To address these issues, we resort to a data-driven
optimization approach [47], which will be elaborated in the
subsequent section.
IV. F RAMEWORK FOR PREDICTIVE
BEAMFORMING DESIGN
In this section, we present a predictive beamforming frame-
work in the considered near-ﬁeld V2I system. The proposed
framework leverages historical channel information to design
beamforming matrices that enhance system performance, with
the LLM serving as a key enabler. Although LLMs are typ-
ically applied to the natural language domain, their powerful
pattern-recognition capability can be readily generalized to
other sequential data, such as the historical CSI considered
in this paper [35]. Speciﬁcally, the time-varying channel
states are represented as sequential inputs, where a dedicated
transformer-based encoder converts the raw channel data at
each time step into high-dimensional tokens. These tokens
are then processed by the LLM, which learns the temporal
dynamics of the channel in a manner analogous to how it
captures grammatical and contextual dependencies in language
sequences. To further improve efﬁciency, the LoRA technique
is employed for parameter-efﬁcient ﬁne-tuning, thereby reduc-
ing the overall training complexity while maintaining model
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2517
Fig. 4. The architecture of the proposed LNN. “FC” and “LN” denote the fully connected layer and layer normalization, respectively.
Fig. 5. The internal structure of the transformer encoder.
expressiveness. The detailed network architecture is provided
in the following.
A. Network Architecture
As shown in Fig. 4, the proposed LNN comprises an
encoder module, a LoRA-enhanced LLM module, and a
prediction head. The functionality and architectural details of
each module are presented in the following.
1) Encoder Module: The encoder module aims to extract
spatially informative features from the complex-valued near-
ﬁeld channel responses. To effectively capture spatial char-
acteristics across multiple vehicles and historical time steps,
we employ P×K identical transformer-based encoders, as
illustrated in Fig. 5. For each encoder, the input complex-
valued channel vector ˆhp,l−k will be separated into real and
imaginary parts to form the input matrix, which can be deﬁned
as
¯hp,l−k =
[
Re
(
ˆhp,l−k
)
, Im
(
ˆhp,l−k
)]
∈ R
¯M×2, (33)
where ˆhp,l−k is the estimated downlink channel of vehicle p
at the (l−k)-th time slot. To prepare this input for transformer
processing, a linear embedding layer maps the input from
R ¯M×2 to a higher-dimensional latent space of RNhid×2, where
Nhid = 1024 denotes the hidden dimension of the transformer.
The embedding layer projects the input to a token-based
representation, where each of the two input features (real and
imaginary) is treated as a token of length Nhid. The resulting
token sequences are then passed through a transformer encoder
layer, which consists of a multi-head self-attention (MHSA)
with Na = 4 attention heads, a feedforward network (FFN)
with a hidden dimension of Nf = 128, two residual connec-
tions, and two normalization layers. The MHSA can capture
global spatial dependencies across antenna elements, while the
residual connections and layer normalization are applied after
both the MHSA and FFN blocks to facilitate gradient ﬂow and
stabilize training. After the transformer layer, the token outputs
are ﬂattened into a vector of dimension 2Nhid, representing the
spatial feature embedding of user p at time slot (l−k).
Finally, the embeddings of all P users at time step (l−k)
are concatenated into a single token, which serves as the
k-th element in the sequence input to the downstream LLM.
Repeating the process across all K historical time steps results
in a token sequence of length K, enabling the LLM to
model temporal dynamics while leveraging the spatial features
extracted by the transformer-based encoders.
2) LLM Module: Following the transformer-based encoder,
we employ an LLM to effectively capture the temporal depen-
dencies across the encoded spatial features from multiple
historical channel observations. As shown in Fig. 4, the LLM
receives a sequence of K tokens, where each token encodes
the aggregated spatial representation corresponding to one
of the K previous time slots. We adopt the standard GPT-
2 architecture as the backbone of the LLM, consisting of
Nlayer = 12 transformer decoder layers with Nattn = 12
attention heads and a hidden dimension of Nemb = 768.
To enable efﬁcient task-speciﬁc adaptation, we integrate the
LoRA technique into the LLM module. LoRA is a parameter-
efﬁcient ﬁne-tuning strategy that introduces trainable low-rank
matrices into pre-trained models while keeping the original
model parameters frozen. The core idea of LoRA is illustrated
in Fig. 6. Deﬁne F∈ Rq×¯q as the weight matrix of a linear
transformation. Then, any input Xin to the transformation
yields an output
Yout =FX in. (34)
In standard training, the NN updates the entire weight matrix
F to obtain the desired output, which incurs signiﬁcant train-
ing cost when F is high-dimensional and full-rank. Instead,
LoRA introduces a trainable low-rank update ∆F = AB,
where B∈ R¯r×¯q projects the input to a lower-dimensional
subspace, and A ∈ Rq×¯r maps it back to the original
dimension, with ¯r≪ min(q, ¯q) being the rank of ∆F . The
resulting modiﬁed transformation becomes
Y′out = (F + ∆F )Xin =FX in +ABX in (35)
During ﬁne-tuning, the original weight matrix F is frozen,
and only the low rank matrices A and B are trained. As a
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2518 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 6. Illustration of LoRA integration in a GPT-2 transformer block.
LoRA is applied to the query, key, and value projections, the attention output
projection, and the feedforward layers, while pre-trained weights remain
frozen and only low-rank adapters are trained.
result, the number of trainable parameters is reduced from
q× ¯q to ¯r(q + ¯q), leading to a substantial reduction in training
complexity with a small rank ¯r [36]. To quantify this reduction,
consider a linear layer in our GPT-2 backbone with a hidden
dimension of Nemb = 768 . A full ﬁne-tuning of this layer
would require updating 768× 768 = 589824 parameters. By
applying LoRA with a rank of ¯r = 16, the number of trainable
parameters is reduced to only 16× (768 + 768) = 24576 ,
corresponding to a reduction of over 95%. Fig. 6 illustrates
the integration of LoRA within the GPT-2 transformer block.
In our implementation, LoRA is applied to the query, key, and
value projections in the attention module, the attention output
projection, and the feedforward layers. During training, only
the LoRA parameters are updated, and all base GPT-2 weights
remain frozen. By employing LoRA into these components,
the model retains its pre-trained knowledge while gaining task-
speciﬁc adaptability.
After processing the K-token input sequence with self-
attention, the LLM produces hidden feature representations
for each token. These representations are then averaged across
the temporal dimension to form a pooled feature vector,
which is fed into a lightweight prediction head to generate
the ﬁnal outputs. The integration of LoRA with the LLM
allows the model to leverage both the long-range temporal
modeling capabilities of transformer-based language models
and the parameter efﬁciency of low-rank adaptation, resulting
in a training-efﬁcient and high-performance NN for predictive
beamforming in near-ﬁeld V2I systems.
3) Prediction Head: Finally, we incorporate a lightweight
prediction head to generate the predicted beamforming vectors
for all vehicles. The prediction head is designed to transform
the temporally pooled representation produced by the LLM
into task-speciﬁc outputs required for beamforming design.
Speciﬁcally, the prediction head comprises a feedforward
neural network with a GELU activation function and layer
normalization operation, followed by a ﬁnal linear projection
to output the predicted beamforming matrix. By integrating
the task-aligned prediction head, the proposed LNN trans-
lates the temporally aware LLM representations into spatially
actionable beamforming decisions.
To summarize, the proposed LNN follows a modular
design. First, the encoder module extracts spatial features from
historical complex-valued channel observations, transforming
them into a sequence of input tokens. These tokens are
then processed by a LoRA-enhanced LLM, which captures
the temporal dependencies across time slots while maintain-
ing parameter efﬁciency. Finally, a prediction head converts
the LLM output into the actionable beamforming matrix.
The proposed LNN enables joint spatial-temporal modeling
of dynamic vehicular environments, offering a solution for
predictive beamforming in near-ﬁeld ISAC systems.
B. Model Training
We ﬁrst provide a detailed rationale for employing historical
channel responses as input to the applied LNN. Note that the
estimated downlink channel for vehicle p at the (l−k)-th time
slot can be modeled as
ˆhp,l−k =
√ α0
ˆd−βp,l−ka(ˆφp,l−k, ˆdp,l−k), ∀k, (36)
where α0 denotes the reference path loss at distance d0, β is
the path loss exponent, and ˆφp,l−k and ˆdp,l−k are the estimated
AoD and distance of vehiclep at time slot (l−k), respectively.
With (36), the estimatedk-th historical channel information for
all the vehicles can then be deﬁned as
ˆHl−k =
[
ˆh1,l−k,..., ˆhP,l−k
]
, ∀k. (37)
The setHl =
{
ˆHl−K,..., ˆHl−1
}
will then be separated into
its real and imaginary components and served as the input to
the network. In (37), it is observed that Hl inherently contains
both the angular and range-related features of the vehicles
across time. By leveraging the temporally correlated spatial
information, the proposed LNN can effectively learn spatial
dynamics of the vehicles, thereby enabling accurate predictive
beamforming.
Next, we demonstrate the design of the loss function for
training the proposed LNN. Conventional regression-based
objectives, such as the mean squared error (MSE), are not
applicable in this context since ground-truth beamforming
matrices are unavailable during training. Instead, we construct
a task-aligned loss function directly derived from the opti-
mization problem Pa andPb, which can be optimized in a
data-driven manner. As deﬁned in (31a)–(31d), Pa aims to
maximize the achievable sum-rate subject to constraints on
sensing accuracy and total transmit power. To incorporate both
the objective and constraints, we formulate the loss function
as
L(χ) =−EHl|Hl
{ P∑
p=1
Rp,l (Wl(χ))
}
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2519
+κ1
(
Eθl|Θl
{
1
P
P∑
p=1
[
J−1e (wp,l(χ))]1,1
}
−ηθ
)
+κ2
(
Erl|Rl
{
1
P
P∑
p=1
[
J−1e (wp,l(χ))]2,2
}
−ηr
)
+κ3
( P∑
p=1
||wp,l(χ)||2−Q
)
, (38)
where χ denotes the learnable parameters of the LNN, and
κi > 0,i = 1, 2, 3 are the penalty parameters related to the
CRB and power constraints. Note that equation (38) cannot
be directly evaluated in closed form due to the expectation
operators. To address this issue, we adopt a data-driven
approach that approximates the expectations using a ﬁnite set
of Ns training samples. Speciﬁcally, the expected achievable
sum-rate can be approximated as
EHl|Hl
{ P∑
p=1
Rp,l (Wl(χ))
}
≈ 1Ns
Ns∑
ns=1
P∑
p=1
R(ns)p,l
(
W (ns)l (χ)), (39)
whereR(ns)p,l
(
W (ns)l (χ)) is the communication rate at thens-
th training example, andW (ns)l (χ) denotes the corresponding
beamforming matrix. Similarly, the expectation operation in
the sensing and power constraints can be approximated via
empirical averages. Then, the loss function given in equation
(38) is reduced to
¯L(χ)
≈−
Ns∑
ns=1
P∑
p=1
R(ns)p,l
(
W (ns)l (χ))
+κ1ReLU
(
1
NsP
Ns∑
ns=1
P∑
p=1
[
J−1e (w(ns)p,l (χ))](ns)1,1 −ηθ
)
+κ2ReLU
(
1
NsP
Ns∑
ns=1
P∑
p=1
[
J−1e (w(ns)p,l (χ))](ns)2,2 −ηr
)
+κ3
1
Ns
Ns∑
ns=1
ReLU
( P∑
p=1
||w(ns)p,l (χ)||2−Q
)
, (40)
where
[
J−1e (w(ns)p,l (χ))](ns)1,1 and [J−1e (w(ns)p,l (χ))](ns)2,2 are
the CRBs for the estimation errors of AoA and distance param-
eters at the ns-th training example, ReLU (x) = max(0,x ) is
the rectiﬁed linear unit function. Similarly, the loss function
forPb is given as
˜L(χ)
≈ 1NsP
Ns∑
ns=1
P∑
p=1
[
J−1e (w(ns)p,l (χ))](ns)1,1
+κ0ReLU
(
−
Ns∑
ns=1
P∑
p=1
R(ns)p,l
(
W (ns)l (χ)) +ηs
)
+κ2ReLU
(
1
NsP
Ns∑
ns=1
P∑
p=1
[
J−1e (w(ns)p,l (χ))](ns)2,2 −ηr
)
+κ3
1
Ns
Ns∑
ns=1
ReLU
( P∑
p=1
||w(ns)p,l (χ)||2−Q
)
, (41)
where κ0 > 0 is the penalty parameter for the sum-rate
constraint. The resulting sample-based empirical loss function
¯L(χ) and ˜L(χ) are fully differentiable and can be optimized
using standard backpropagation. The optimal network param-
eters for solving Pa andPb are then obtained by solving
χ∗1 = arg minχ ¯L(χ), χ∗2 = arg minχ ˜L(χ). (42)
Finally, the predicted beamforming matrix at time slot l
provided by the proposed LNN is given as
ˆWl =Fχ∗(Hl), ∀l, (43)
whereFχ∗(·) denotes the LLM-based mapping from historical
channel observations to beamforming decisions, parameterized
by the optimized network weights χ∗, and χ∗ is the optimal
network parameters.
Remark 3: Although the proposed data-driven method also
relies on a large number of samples, its objective is fundamen-
tally different from that of Monte Carlo simulation. The Monte
Carlo approach solves the deterministic version of the problem
for each individual sample, whereas our method leverages the
empirical average over samples in the loss function to train a
robust LNN that performs well on average across the entire
distribution of possible vehicle states [14].
C. Computational Complexity Analysis
In this subsection, we analyze the computational complexity
of the proposed LNN during the forward inference phase. The
network is composed of three main components: a transformer-
based encoder module, a LoRA-integrated LLM module based
on pre-trained GPT-2, and a lightweight prediction head.
1) Encoder Module: The encoder module consists of KP
identical transformer-based encoders. For each encoder, the
computational cost is dominated by the input projection and
the transformer encoder layer. Given an input of shape R ¯M×2,
the input projection requires O(2 ¯MN hid) operations. The
transformer encoder includes a MHSA mechanism and a FFN,
with a total complexity ofO(N2hid+NaN2hid+NhidNf) per layer.
Consequently, the overall complexity of the encoder module
scales as O(KPN 2hid).
2) LLM Module: The LLM module receives an input
sequence of K embedded feature tokens, each of dimension
Nemb, and processes them through a GPT-2 backbone com-
posed ofNlayer transformer decoder blocks. The computational
cost per block arises mainly from the MHSA and FFN layers.
Although the LoRA technique introduces additional trainable
parameters by inserting low-rank matrices of rank r into
selected linear transformations, its contribution to inference
cost is minor, adding O(rNemb) per layer. Since the original
GPT-2 weights are frozen, training updates are applied solely
to the LoRA components, leading to a signiﬁcant reduction
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2520 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 7. The considered T-shape junction with one RSU and P = 3 vehicles.
The nominal 2-D coordinates of the vehicles are [x1,y 1] = [ −29.8, 18.1] m,
[x2,y 2] = [ −4.5, 48.2] m, [x3,y 3] = [5.9, 25.2] m, respectively.
in parameter overhead. Nonetheless, the inference complex-
ity remains equivalent to standard GPT-2 and is given by
O
(
Nlayer
(
K2Nemb +KN 2emb)).
3) Prediction Head: The prediction head contains two
linear layers and normalization layers, leading to a total
complexity of O(NembNnode +Nnode ¯MP ), where Nnode is the
hidden dimension. As these layers are shallow and linear, their
contribution to the overall complexity is negligible compared
to the encoder and LLM modules.
In summary, the total complexity of a single forward pass is
dominated by the encoder and LLM module, particularly the
MHSA and FFN operations across multiple layers. The total
computational complexity is then given by
O
(
KPN 2hid +Nlayer(K2Nemb +KN 2emb)). (44)
V. E XPERIMENTAL RESULTS
The simulation results are presented in this section to verify
the effectiveness of the proposed predictive beamforming
framework. The RSU is equipped with ¯M = 129 transmit
antennas (M = 64) and ¯N = 129 receive antennas (N = 64),
arranged with an inter-element spacing ofϵ =λ/2 = 0.015 m,
where λ = 0.03 m denotes the carrier wavelength. The noise
power spectral density at both the RSU and the vehicles is
set to−150 dBm/Hz. The path loss model adopts a reference
path loss of α0 =−70 dB at a distance d0 = 1 m, with a path
loss exponent of 2.55 [48].
In terms of the geometric parameters, we consider a T-
shape junction comprising one RSU and P = 3 vehicles,
as shown in Fig. 7. The initial positions of the vehi-
cles are modeled as [xp + ∆x,yp + ∆y], ∀p, where xp
and yp denote the nominal two-dimensional coordinates of
vehicle p, and ∆x, ∆y ∼ CN(0, 1) represent the Gaus-
sian uncertainties. Speciﬁcally, the nominal coordinates of
the vehicles are set as [x1,x 2,x 3] = [ −29.8,−4.5, 5.9]
m and [y1,y 2,y 3] = [18 .1, 48.2, 25.2] m. The reference
transmit and receive antenna elements are positioned at
[−0.975, 0] m and [0.975, 0] m, respectively. Let v(x)p and
v(y)p denote the velocity components of vehicle p along the
x- and y-axes, respectively. The velocity components of the
vehicles are modeled as −v(x)1 ,v (y)2 ,−v(y)3 ∼U (10, 12) m/s,
while the remaining components are set to zero, i.e., v(y)1 =
v(x)2 =v(x)3 = 0 m/s. Here,U(adown,b up) denotes the uniform
distribution within the range of [adown,b up]. Finally, we use
K = 4 historical channel observations as input to the network.
For the training of the proposed LNN, we utilized the Adam
optimizer. The initial learning rate is set to 6× 10−4 and
is reduced by a factor of 0.9 if the validation loss does not
improve for 4 consecutive epochs. The network is trained for
a total of 100 epochs with a batch size of 64. A total of Ne =
1.5× 104 training samples are employed, and the network is
evaluated on 5× 103 test samples.
A. Performance Limit
The performance limits of the proposed LNN are evaluated
in this subsection. We compare its average achievable sum-
rate and minimum CRBs with several benchmarks to verify
its effectiveness in the considered near-ﬁeld V2I system.
1) Communication Performance: To isolate communication
performance, the sensing-related penalty terms in the loss
function ¯L(χ) are deactivated by setting κ1 =κ2 = 0, while
κ3 = 102 enforces the total power constraint. For comparison,
we include the upper bound and the results obtained by the
conventional far-ﬁeld beamforming strategy. The performance
upper bound is obtained by solving Pa without the CRB
constraints (31b) and (31c), under the assumption of perfect
CSI. This upper bound can also serve as an upper bound
for model-driven predictive approaches such as the EKF, as
these methods unavoidably suffer from prediction errors. On
the other hand, the conventional far-ﬁeld beamforming vector
is deﬁned as [44]
wfarp,l =
√ρp,l
¯M
[
e
j2π
λ (−M)ϵ cosφp,l,...,e j2πλ Mϵ cosφp,l]T,
(45)
where ρp,l is the power allocated to vehicle p at the l-th
time slot. To evaluate the performance of the far-ﬁeld scheme,
we assume that the beamforming vector follows the structure
in (45). The corresponding power allocation {ρp,l} is then
optimized by substituting (45) into the objective function (31a)
and solving problem Pa without the CRB constraints.
As illustrated in Fig. 8, the proposed LNN achieves an
average sum-rate that closely approaches the upper bound
across all the transmit power constraints. The results indicate
that the network can effectively infer the spatial characteristics
of vehicles based solely on historical channel observations.
The extracted features are then leveraged to construct the
beamforming matrix, resulting in a performance that nearly
matches that of the upper bound, which assumes perfect
channel knowledge. In contrast, the far-ﬁeld beamforming
scheme yields consistently lower sum-rates under all power
constraints. The performance gap is attributed to the omission
of range-domain information in far-ﬁeld beamforming design,
which becomes non-negligible in near-ﬁeld environments.
These results conﬁrm that, in near-ﬁeld ISAC systems, beam-
forming strategies require joint consideration in both angular
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2521
Fig. 8. Comparison of achievable sum-rate across different beamforming
schemes.
Fig. 9. Comparison of achievable sum-rate among different networks.
and distance-domain characteristics to fully exploit spatial
diversity and achieve optimal communication performance.
To further validate the effectiveness of the proposed LLM-
based architecture, we compare its performance with several
conventional NNs, including the LSTM, recurrent neural net-
work (RNN), and convolutional neural network (CNN). In
these baselines, the LLM module is replaced by the corre-
sponding alternative, while the encoder and prediction head
remain unchanged. The comparison results are presented in
Fig. 9. It can be observed that the LSTM and RNN achieve
comparable sum-rates across all transmit power constraints,
both outperforming the CNN baseline. The performance gain
primarily stems from the ability of LSTM and RNN to capture
temporal dependencies in sequential input, thereby enhancing
their predictive capability. Notably, the proposed LNN consis-
tently outperforms all baseline models under varying transmit
power levels, which is mainly attributed to the strong temporal
modeling and feature extraction capabilities inherent to the
transformer-based LLM. By freezing the pre-trained weights
of GPT-2 and ﬁne-tuning only a small number of LoRA
parameters, the network retains rich linguistic and structural
priors learned during large-scale pretraining. Consequently,
Fig. 10. Comparison of achievable sum-rate under different antenna array
conﬁgurations.
Fig. 11. Comparison of achievable sum-rate under different numbers of
vehicles.
it exhibits a signiﬁcantly enhanced ability to identify and
generalize temporal patterns across historical channel tokens,
resulting in signiﬁcantly improved beamforming performance
compared to conventional sequence modeling approaches.
The communication performance of the proposed LNN
under various system conﬁgurations is also investigated.
Speciﬁcally, we consider three representative antenna array
settings with ¯N = ¯M = ¯Ma ∈ {97, 129, 161}. The
corresponding average achievable sum-rates are depicted in
Fig. 10, along with the theoretical upper bounds computed
under perfect channel knowledge. As shown in the ﬁg-
ure, the proposed network achieves performance that closely
approaches the upper bound across all antenna conﬁgurations
and transmit power levels. Such alignment demonstrates the
capability of the network in leveraging the historical CSI
to construct effective beamforming strategies in different
system setups. Moreover, it is observed that increasing the
number of antennas leads to only a modest improvement
in communication rate. While larger arrays enable higher
spatial multiplexing gains through multi-stream transmission,
the ﬁxed total transmit power reduces the SNR at each sub-
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2522 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 12. CRBs for AoA estimations achieved by different methods.
channel, thus limiting the growth in achievable sum-rate.
In addition, Fig. 11 presents the achievable sum-rate under
varying numbers of vehicles, with the total transmit power
ﬁxed at P = 10 dBm. As expected, increasing the number
of vehicles leads to improved average sum-rate performance
across all schemes, owing to the multi-user diversity gain.
Notably, the proposed LNN consistently achieves average
sum-rates close to the upper bound under all user numbers,
while the far-ﬁeld beamforming scheme lags behind due to its
neglect of range-dependent channel variations inherent in the
near-ﬁeld region.
2) Sensing Performance: Following the analysis of com-
munication performance, we proceed to evaluate the sensing
performance of the considered V2I system enabled by the
proposed LNN. To obtain the minimum CRB for the AoA
estimation error, the penalty coefﬁcients κ0 and κ2 in the
loss function ˜L(χ) are set to zero. Similarly, to minimize the
CRB associated with distance estimation, the corresponding
CRB term is used as the objective, while the AoA and
sum-rate constraints are deactivated. The CRBs achieved by
conventional far-ﬁeld and near-ﬁeld beamforming schemes are
also provided for comparison. In the far-ﬁeld beamforming
scheme, the beamforming vector is constructed as in (45), and
the CRBs are computed by substituting (45) into (28) and (29).
Each vehicle is assigned an equal transmit power ρp,l = Q3 .
For the near-ﬁeld beamforming strategy, the beamforming
vector is constructed as
wnearp,l =
√ρp,l
¯M
[
e
j2π
λ
(
−Mϵ cosφp,l−M 2ϵ22dp,l sin2φp,l),
...,e
j2π
λ
(
Mϵ cosφp,l−M 2ϵ22dp,l sin2φp,l)], ∀p,l, (46)
andρp,l follow the equal power allocation strategy. The above
scheme also corresponds to the performance limit of model-
driven predictive approaches with equal power allocation.
The results, shown in Figs. 12 and 13, reveal that near-ﬁeld
beamforming achieves lower CRBs than far-ﬁeld beamforming
across all transmit power levels, highlighting the advantage
of exploiting both angular and range-domain information in
near-ﬁeld ISAC systems. Furthermore, the proposed LNN
Fig. 13. CRBs for distance estimations achieved by different methods.
achieves even lower CRBs compared to the near-ﬁeld baseline.
Note that the near-ﬁeld baseline assumes perfect vehicle state
information, whereas the proposed network operates based on
predicted historical observations. The performance advantage
indicates that the LNN not only effectively predicts the vehicle
kinematic parameters but also optimizes the power allocation
across vehicles to further minimize the estimation error.
In addition, Figs. 12 and 13 also present a comparison of
the CRBs achieved by several baseline networks, including
LSTM, RNN, and CNN. Consistent with the communication
performance trends, the LSTM and RNN achieve comparable
CRBs, both outperforming the CNN baseline. Nevertheless, all
baseline methods exhibit higher CRBs than the analytical near-
ﬁeld and far-ﬁeld beamforming schemes, highlighting their
limited effectiveness in accurately predicting vehicle kinematic
parameters under dynamic conditions. The performance gap
arises because the analytical schemes are evaluated using
perfect, instantaneous state information, whereas the DL-based
schemes perform a challenging prediction task based on imper-
fect historical observations. The resulting prediction errors
cause beam misalignment, thereby degrading sensing perfor-
mance.In contrast, the proposed LNN consistently achieves the
lowest CRBs across all transmit power settings, demonstrating
its ability to extract spatio-temporal features and optimize
beamforming strategies for improved sensing accuracy.
Finally, we evaluate the impact of user density and antenna
conﬁguration on sensing performance. Fig. 14 shows the
CRBs for both AoA and distance estimation as the number
of vehicles increases while keeping the total transmit power
ﬁxed. The results indicate that the estimation error bounds
of all schemes increase with user density, since the available
transmit power will be shared among more vehicles, reducing
the SNR of the corresponding echo signals. The proposed
LNN consistently achieves the lowest CRBs compared with
the far-ﬁeld and near-ﬁeld baselines, conﬁrming its capability
of resource allocation in multi-vehicle tracking. Moreover,
Figs. 15 and 16 present the CRBs achieved by the proposed
LNN and the near-ﬁeld beamforming baseline under various
antenna conﬁgurations. The LNN again outperforms the base-
line across all settings. As the number of antennas increases,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2523
Fig. 14. CRBs for AoA and distance estimations under different numbers of
vehicles.
Fig. 15. CRBs for AoA estimations with different array conﬁgurations.
Fig. 16. CRBs for distance estimations with different array conﬁgurations.
the CRBs exhibit a considerable reduction due to the improved
spatial resolution. The observation is also consistent with the
theoretical expressions of the CRBs, where the estimation error
decreases inversely with the number of transmit and receive
antennas.
Fig. 17. Achievable sum-rate versus different required CRB thresholds ηθ
for AoA estimation.
Fig. 18. Achievable sum-rate versus different required CRB thresholds ηr
for distance estimation.
B. Sensing & Communication Trade-off
The trade-off between sensing and communication perfor-
mance can be characterized by solving Pa while simultane-
ously activating both CRB and power constraints. Speciﬁcally,
to explore the trade-off between the CRB of AoA estimation
and the average achievable sum-rate, the penalty parameters
are set as κ1 = 10 2, κ2 = 0 , and κ3 = 10 2. Similarly,
to investigate the trade-off between the CRB of distance
estimation and the sum-rate, we set κ1 = 0, κ2 = 10 2, and
κ3 = 10 2. By varying the required CRB thresholds ηθ and
ηr in problem Pa, the trade-off between sensing and com-
munication curves can be obtained, as illustrated in Figs. 17
and 18. It is observed that as the required CRB increases, the
average achievable sum-rate improves accordingly, which is
consistent with theoretical expectations. Moreover, an increase
in the total transmit power budget Q leads to a simultaneous
improvement in both sensing accuracy and communication
rate, as the additional power resources enhance the SNR at
both the communication receivers and sensing targets, thereby
beneﬁting both functionalities concurrently.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2524 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
From the variation trend of the curve given in Figs. 17
and 18, we can also perceive that a favorable trade-off can
be obtained with an appropriate beamforming design. For
example, with a transmit power constraint of Q = 8 dBm,
when the CRB for AoA estimation decreases from 0.58 deg 2
to 0.30 deg 2, the achievable sum-rate decreases slightly from
1.57 bit/Hz to 1.44 bit/Hz. The resulting trade-off indicates that
a minor reduction in communication performance (approxi-
mately 8%) can lead to a signiﬁcant improvement in sensing
accuracy (approximately 48%). However, pursuing the extreme
optimization of either sensing or communication performance
comes at a signiﬁcant cost to the other subsystem, as evident
from the sharper slopes near the edges of the trade-off curves.
Therefore, in practical system design, it is desirable to avoid
over-optimizing a single functionality, as an appropriate com-
promise will ensure balanced performance for both sensing
and communication tasks in near-ﬁeld ISAC networks.
VI. C ONCLUSION
In this paper, we investigate a predictive beamforming
problem for ISAC-based near-ﬁeld V2I systems. The com-
munication and sensing performance of the considered system
are evaluated by the achievable sum-rates and the CRBs for
AoA and distance parameter estimations, respectively. The
optimization problems are subsequently formulated based on
these performance metrics to design the beamforming matrix.
To characterize the random motion behavior of vehicles,
expectation operations are incorporated into the performance
metrics, resulting in intractable closed-form expressions for
both the objective function and the associated constraints. To
address this challenge, an LNN is proposed, which leverages
historical channel information to perform predictive beam-
forming for optimizing system performance. Moreover, the
LoRA technique is integrated into the proposed network to
enhance training efﬁciency by reducing the number of train-
able parameters. Simulation results validate that the proposed
LNN consistently outperforms baselines in terms of both
communication and sensing performance. As the proposed
LNN can effectively exploit historical CSI for predictive
beamforming, it serves as a promising solution for future V2I
systems under near-ﬁeld ISAC scenarios.
APPENDIX A
PROOF OF PROPOSITION 1
In this appendix, we present the detailed derivation of the
FIM. For notation convenience, let ζi denote the i-th entry of
the unknown parameter vector ζ = [θ,r,µ ]T . Based on the
joint conditional PDF given in equation (21), the ﬁrst-order
derivative of lnf(¯y, ¯µ|ζ) with respect to ζi is obtained as
∂ lnf(¯y, ¯µ|ζ)
∂ζi
=



− 1¯δ2
(
−γαω ˜fH(θ,r )∂b(θ,r )aH(φ,d )ζi w
−γα∗ω∗wH∂a(φ,d )bH(θ,r )ζi ˜f(θ,r )), i = 1, 2,2
˙δ2 (¯µ−µ), i =3,
(47)
where
˜f(θ,r ) = ¯y−γαωb(θ,r )aH(φ,d )w. (48)
With equation (47), the second-order derivative of lnf(¯y, ¯µ|ζ)
with respect to ζ can be derived and is expressed as
−E
[∂2 lnf(¯y, ¯µ|ζ)
∂ζi∂ζi′
]
=



2γ2|α|2|ω|2
¯δ2 Re
{
wHAi,i′w}, i,i ′≤ 2,
2
˙δ2, i,i ′ = 3,
0, otherwise,
(49)
where
Ai,i′ = ∂a(φ,d )bH(θ,r )ζi ∂b(θ,r )aH(φ,d )ζi′ . (50)
The detailed expressions for the partial derivatives of the
steering vectors with respect to ζ are given by
∂a(φ,d )bH(θ,r )
ζi
= ∂a(φ,d )∂ζi bH(θ,r ) +a(φ,d )∂bH(θ,r )∂ζi ,
(51)
∂b(θ,r )aH(φ,d )
ζi′
= ∂b(θ,r )∂ζi′ aH(φ,d ) +b(θ,r )∂aH(φ,d )∂ζi′ ,
(52)
∂am(φ,d )
∂θ =
(
−mϵ sinφ∂φ∂θ−(m2ϵ2d sinφ cosφ∂φ∂θ
− m2ϵ2
2d2 sin2φ∂d∂θ))e(mϵ cosφ−m2ϵ22d sin2φ), (53)
∂am(φ,d )
∂r =
(
−mϵ sinφ∂φ∂r−(m2ϵ2d sinφ cosφ∂φ∂r
− m2ϵ2
2d2 sin2φ∂d∂r))e(mϵ cosφ−m2ϵ22d sin2φ), (54)
∂bn(θ,r )
∂θ =
(
−nϵ sinθ
− n2ϵ2
r sinθ cosθ
)
×e
(
nϵ cosθ−n2ϵ22r sin2θ), (55)
∂bn(θ,r )
∂r = n2ϵ22r2 sin2θe(nϵ cosθ−n2ϵ22r sin2θ), (56)
∂φ
∂θ = 1− (r cosθ +a)ad2 , ∂d∂θ =−ad sinφr , (57)
∂φ
∂d = (r +a cosθ)(r cosθ +a)−d2 cosθd2r sinθ , (58)
∂d
∂r = r +a cosθd , (59)
where am(φ,d ) and bn(θ,r ) denote the m-th and n-th ele-
ments of the transmit and receive steering vectors a(φ,d ) and
b(θ,r ), respectively. By applying equations (49) to (59), all
entries of the FIM Jζ(w) can be explicitly determined, thus
completing the proof.
REFERENCES
[1] H. Zhang, N. Shlezinger, F. Guidi, D. Dardari, and Y . C. Eldar, “6G
wireless communications: From far-ﬁeld beam steering to near-ﬁeld
beam focusing,” IEEE Commun. Mag. , vol. 61, no. 4, pp. 72–77, Apr.
2023.
[2] Y . Liu, C. Ouyang, Z. Wang, J. Xu, X. Mu, and A. L. Swindlehurst,
“Near-ﬁeld communications: A comprehensive survey,” IEEE Commun.
Surveys Tuts., vol. 27, no. 3, pp. 1687–1728, 4th Quart., 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2525
[3] X. Wei and L. Dai, “Channel estimation for extremely large-scale
massive MIMO: Far-ﬁeld, near-ﬁeld, or hybrid-ﬁeld?,” IEEE Commun.
Lett., vol. 26, no. 1, pp. 177–181, Jan. 2022.
[4] M. Cui and L. Dai, “Near-ﬁeld wideband beamforming for extremely
large antenna arrays,” IEEE Trans. Wireless Commun. , vol. 23, no. 10,
pp. 13110–13124, Oct. 2024.
[5] Z. Wang, X. Mu, and Y . Liu, “Near-ﬁeld integrated sensing and
communications,” IEEE Commun. Lett. , vol. 27, no. 8, pp. 2048–2052,
Aug. 2023.
[6] H. Lu et al., “A tutorial on near-ﬁeld XL-MIMO communications toward
6G,” IEEE Commun. Surveys Tuts. , vol. 26, no. 4, pp. 2213–2257, 4th
Quart., 2024.
[7] Z. Wang et al., “A tutorial on extremely large-scale MIMO for 6G:
Fundamentals, signal processing, and applications,” IEEE Commun.
Surveys Tuts., vol. 26, no. 3, pp. 1560–1605, 3rd Quart., 2024.
[8] Y . Liu, Z. Wang, J. Xu, C. Ouyang, X. Mu, and R. Schober, “Near-
ﬁeld communications: A tutorial review,” IEEE Open J. Commun. Soc. ,
vol. 4, pp. 1999–2049, 2023.
[9] W. Zhu, J. Gao, S. Zhang, and L. Liu, “Reconﬁgurable intelligent
surface-assisted multiuser tracking and signal detection in ISAC,” 2025,
arXiv:2509.13940.
[10] T. Wu et al., “Fluid antenna systems enabling 6G: Principles, applica-
tions, and research directions,” 2024, arXiv:2412.03839.
[11] L. Zhou, J. Yao, M. Jin, T. Wu, and K.-K. Wong, “Fluid antenna-
assisted ISAC systems,” IEEE Wireless Commun. Lett. , vol. 13, no. 12,
pp. 3533–3537, Dec. 2024.
[12] S. Yang et al., “Toward intelligent antenna positioning: Leveraging DRL
for FAS-aided ISAC systems,” IEEE Internet Things J. , vol. 12, no. 16,
pp. 34615–34618, Aug. 2025.
[13] F. Liu, W. Yuan, C. Masouros, and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: Communication served by sensing,”
IEEE Trans. Wireless Commun. , vol. 19, no. 11, pp. 7704–7719, Nov.
2020.
[14] X. Zhang, W. Yuan, C. Liu, J. Wu, and D. W. K. Ng, “Predictive
beamforming for vehicles with complex behaviors in ISAC systems: A
deep learning approach,” IEEE J. Sel. Topics Signal Process. , vol. 18,
no. 5, pp. 828–841, Jul. 2024.
[15] A. Guerra, F. Guidi, D. Dardari, and P. M. Djuric, “Near-ﬁeld tracking
with large antenna arrays: Fundamental limits and practical algorithms,”
IEEE Trans. Signal Process. , vol. 69, pp. 5723–5738, 2021.
[16] H. Zhang, N. Shlezinger, F. Guidi, D. Dardari, M. F. Imani,
and Y . C. Eldar, “Beam focusing for near-ﬁeld multiuser MIMO
communications,” IEEE Trans. Wireless Commun. , vol. 21, no. 9,
pp. 7476–7490, Sep. 2022.
[17] H. Li, Z. Wang, X. Mu, P. Zhiwen, and Y . Liu, “Near-ﬁeld inte-
grated sensing, positioning, and communication: A downlink and
uplink framework,” IEEE J. Sel. Areas Commun. , vol. 42, no. 9,
pp. 2196–2212, Sep. 2024.
[18] K. Qu, S. Guo, N. Saeed, and J. Ye, “Near-ﬁeld integrated sensing and
communication: Performance analysis and beamforming design,” IEEE
Open J. Commun. Soc. , vol. 5, pp. 6353–6366, 2024.
[19] Z. Du et al., “Integrated sensing and communications for V2I networks:
Dynamic predictive beamforming for extended vehicle targets,” IEEE
Trans. Wireless Commun., vol. 21, no. 12, pp. 10345–10359, Dec. 2021.
[20] W. Yuan, Z. Wei, S. Li, J. Yuan, and D. W. K. Ng, “Integrated sensing
and communication-assisted orthogonal time frequency space transmis-
sion for vehicular networks,” IEEE J. Sel. Topics Signal Process. ,
vol. 15, no. 6, pp. 1515–1528, Nov. 2021.
[21] H. Jiang, Z. Wang, and Y . Liu, “Near-ﬁeld sensing enabled predictive
beamforming: From estimation to tracking,” 2024, arXiv:2408.02027.
[22] Z. Wang, X. Mu, and Y . Liu, “Near-ﬁeld velocity sensing and
predictive beamforming,” IEEE Trans. V eh. Technol. , vol. 74, no. 1,
pp. 1806–1810, Jan. 2025.
[23] X. Zhang, C. Liu, W. Yuan, J. A. Zhang, and D. W. K. Ng, “Sparse
prior-guided deep learning for OTFS channel estimation,” IEEE Trans.
V eh. Technol., vol. 73, no. 12, pp. 19913–19918, Dec. 2024.
[24] C. Liu, X. Liu, D. W. K. Ng, and J. Yuan, “Deep residual learning
for channel estimation in intelligent reﬂecting surface-assisted multi-
user communications,” IEEE Trans. Wireless Commun. , vol. 21, no. 2,
pp. 898–912, Feb. 2022.
[25] T. Wu et al., “Exploit high-dimensional RIS information to localization:
What is the impact of faulty element?,” IEEE J. Sel. Areas Commun. ,
vol. 42, no. 10, pp. 2803–2819, Oct. 2024.
[26] J. Wang et al., “Generative AI for integrated sensing and communication:
Insights from the physical layer perspective,” IEEE Wireless Commun. ,
vol. 31, no. 5, pp. 246–255, Oct. 2024.
[27] J. Wang et al., “Generative AI based secure wireless sensing for ISAC
networks,” IEEE Trans. Inf. F orensics Security, vol. 20, pp. 5195–5210,
2025.
[28] W. Zhu, M. Tao, X. Yuan, and Y . Guan, “Deep-learned approx-
imate message passing for asynchronous massive connectivity,”
IEEE Trans. Wireless Commun. , vol. 20, no. 8, pp. 5434–5448,
Aug. 2021.
[29] J. Mu, Y . Gong, F. Zhang, Y . Cui, F. Zheng, and X. Jing, “Integrated
sensing and communication-enabled predictive beamforming with deep
learning in vehicular networks,” IEEE Commun. Lett. , vol. 25, no. 10,
pp. 3301–3304, Oct. 2021.
[30] C. Liu et al., “Learning-based predictive beamforming for integrated
sensing and communication in vehicular networks,” IEEE J. Sel. Areas
Commun., vol. 40, no. 8, pp. 2317–2334, Aug. 2022.
[31] J. Zhang, G. Zheng, Y . Zhang, I. Krikidis, and K.-K. Wong, “Deep learn-
ing based predictive beamforming design,” IEEE Trans. V eh. Technol.,
vol. 72, no. 6, pp. 8122–8127, Jun. 2023.
[32] F. Jiang et al., “Large language model enhanced multi-agent systems
for 6G communications,” IEEE Wireless Commun. , vol. 31, no. 6,
pp. 48–55, Dec. 2024.
[33] F. Jiang et al., “Large AI model-based semantic communications,” IEEE
Wireless Commun., vol. 31, no. 3, pp. 68–75, Jun. 2024.
[34] F. Jiang et al., “Large AI model empowered multimodal semantic
communications,” IEEE Commun. Mag. , vol. 63, no. 1, pp. 76–82, Jan.
2025.
[35] Y . Sheng, K. Huang, L. Liang, P. Liu, S. Jin, and G. Y . Li, “Beam
prediction based on large language models,” IEEE Wireless Commun.
Lett., vol. 14, no. 5, pp. 1406–1410, May 2025.
[36] J. E. Hu et al., “LoRA: Low-rank adaptation of large lan-
guage models,” in Proc. 10th Int. Conf. Learn. Represent. (ICLR) ,
May 2021, pp. 1–13.
[37] D. Zhang, A. Li, M. Shirvanimoghaddam, P. Cheng, Y . Li, and
B. Vucetic, “Codebook-based training beam sequence design for
millimeter-wave tracking systems,” IEEE Trans. Wireless Commun. ,
vol. 18, no. 11, pp. 5333–5349, Nov. 2019.
[38] W. Yuan, F. Liu, C. Masouros, J. Yuan, D. W. K. Ng, and
N. Gonzalez-Prelcic, “Bayesian predictive beamforming for vehicu-
lar networks: A low-overhead joint radar-communication approach,”
IEEE Trans. Wireless Commun. , vol. 20, no. 3, pp. 1442–1456,
Mar. 2021.
[39] Z. Wu and L. Dai, “Multiple access for near-ﬁeld communications:
SDMA or LDMA?,” IEEE J. Sel. Areas Commun. , vol. 41, no. 6,
pp. 1918–1935, Jun. 2023.
[40] H. Luo, F. Gao, W. Yuan, and S. Zhang, “Beam squint assisted user local-
ization in near-ﬁeld integrated sensing and communications systems,”
IEEE Trans. Wireless Commun. , vol. 23, no. 5, pp. 4504–4517, May
2024.
[41] Y . Li, X. Wang, and Z. Ding, “Multi-target position and velocity esti-
mation using OFDM communication signals,” IEEE Trans. Commun. ,
vol. 68, no. 2, pp. 1160–1174, Feb. 2020.
[42] H. Q. Ngo, Massive MIMO: Fundamentals and System Designs ,
vol. 1642. Link ¨oping, Sweden: Link ¨oping University Electronic Press,
2015.
[43] J. Bechter, M. Rameez, and C. Waldschmidt, “Analytical and experimen-
tal investigations on mitigation of interference in a DBF MIMO radar,”
IEEE Trans. Microw. Theory Techn., vol. 65, no. 5, pp. 1727–1734, May
2017.
[44] F. Liu, Y .-F. Liu, A. Li, C. Masouros, and Y . C. Eldar, “Cram ´er–Rao
bound optimization for joint radar-communication beamforming,” IEEE
Trans. Signal Process. , vol. 70, pp. 240–253, 2022.
[45] Y . Shen and M. Z. Win, “Fundamental limits of wideband
localization—Part I: A general framework,” IEEE Trans. Inf. Theory ,
vol. 56, no. 10, pp. 4956–4980, Oct. 2010.
[46] Y . Qi, H. Kobayashi, and H. Suda, “Analysis of wireless geolocation in a
non-line-of-sight environment,” IEEE Trans. Wireless Commun. , vol. 5,
no. 3, pp. 672–681, Mar. 2006.
[47] J. Yang, W. Zhu, M. Tao, and S. Sun, “Hierarchical beam alignment for
millimeter-wave communication systems: A deep learning approach,”
IEEE Trans. Wireless Commun. , vol. 23, no. 4, pp. 3541–3556, Apr.
2024.
[48] Y . Niu, Y . Li, D. Jin, L. Su, and A. V . Vasilakos, “A survey
of millimeter wave communications (mmWave) for 5G: Opportuni-
ties and challenges,” Wireless Netw. , vol. 21, no. 8, pp. 2657–2676,
Nov. 2015.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

2526 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Hongjia Huang (Graduate Student Member, IEEE)
received the B.Eng. and M.Eng. degrees in electronic
science and technology from Shenzhen University,
Shenzhen, China, in 2018 and 2021, respectively.
He is currently pursuing the Ph.D. degree with the
Department of Electrical and Electronic Engineer-
ing, The Hong Kong Polytechnic University, Hong
Kong. His research interests include integrated sens-
ing and communication, near-ﬁeld communication,
and deep learning-enabled integrated sensing and
communications (ISAC) systems.
Weijie Yuan (Senior Member, IEEE) is currently
an Assistant Professor with the Southern University
of Science and Technology. His research inter-
ests include integrated sensing and communications
(ISAC), orthogonal time frequency space (OTFS),
and the low-altitude wireless networks (LAWN). He
was listed among the World’s Top 2% Scientists by
Stanford University for Citation Impact from 2021 to
2024 and among the Elsevier Highly-Cited Chinese
Researchers. He was a recipient of the Best Editor
from IEEE CommL; the Best Paper Awards from
IEEE ICC 2023, IEEE/CIC ICCC 2023, and IEEE GlobeCom 2024; and the
2025 IEEE Communications Society and Information Theory Society Joint
Paper Award. He is the Founding Chair of the IEEE ComSoc Special Interest
Group (SIG) on LAWN as well as the SIG on OTFS. He serves as an Editor
for IEEE T RANSACTIONS ON COMMUNICATIONS , IEEE T RANSACTIONS
ON WIRELESS COMMUNICATIONS , IEEE T RANSACTIONS ON MOBILE
COMPUTING , IEEE Communications Magazine , IEEE C OMMUNICATIONS
LETTERS , and IEEE O PEN JOURNAL OF THE COMMUNICATIONS SOCIETY ;
and a Guest Editor for IEEE T RANSACTIONS ON VEHICULAR TECHNOL -
OGY, IEEE T RANSACTIONS ON NETWORK SCIENCE AND ENGINEERING ,
and IEEE I NTERNET OF THINGS JOURNAL .
Chang Liu (Member, IEEE) received the Ph.D.
degree from Dalian University of Technology, China,
in 2017. In 2015, he was a joint Ph.D. Scholar with
the University of Tennessee, Knoxville, TN, USA.
From 2017 to 2023, he held research appointments
at several leading international institutions, including
Post-Doctoral Research Fellow positions with the
University of Electronic Science and Technology
of China and the University of New South Wales,
Sydney, Australia; an Alexander von Humboldt
Research Fellowship with Friedrich Alexander Uni-
versity Erlangen-Nuremberg, Germany; and a Research Assistant Professor
position with The Hong Kong Polytechnic University. He is currently a
Lecturer (an Assistant Professor in U.S. system) with the Department of
Computer Science and Information Technology, La Trobe University, Mel-
bourne, Australia. To date, he has published more than 70 papers in leading
international journals and conferences. His research interests include machine
learning in communication and sensing systems, with a focus on the Internet
of Things (IoT), vehicular-to-everything (V2X) networks, and low-altitude
wireless networks (LAWN), supported by enabling technologies including
integrated sensing and communication (ISAC), intelligent reﬂecting surface
(IRS), OTFS, and other emerging next-generation wireless techniques. He
was awarded the prestigious Alexander von Humboldt Research Fellowship
and has been consistently recognized among the World’s Top 2% Scientists by
Stanford University since 2022. His papers have received multiple distinctions,
including the IEEE Best Paper Awards, the ESI Hot Papers, and the ESI
and SciVal Highly Cited Papers. Several of his works have been featured
in IEEE Best Readings, IEEE Selected Ideas in Communications, and IEEE
Popular Articles lists. He is also the EDAS Chair of IEEE PIMRC 2026, the
Publication Chair of IEEE ISWCS 2026, a Founding Member of the IEEE
ComSoc Special Interest Group on orthogonal time frequency space (OTFS),
and the Session Chair at IEEE ICC 2017. He serves as an Editor for IEEE
TRANSACTIONS ON COMMUNICATIONS .
Liang Liu (Senior Member, IEEE) received the
B.Eng. degree from Tianjin University, China, in
2010, and the Ph.D. degree from the National
University of Singapore, Singapore, in 2014. He
was a Post-Doctoral Fellow with the Department
of Electrical and Computer Engineering, University
of Toronto, from 2015 to 2017; a Research Fellow
with the Department of Electrical and Computer
Engineering, National University of Singapore, from
2017 to 2019; and an Assistant Professor with the
Department of Electrical and Electronic Engineer-
ing, The Hong Kong Polytechnic University, from 2019 to 2024. He is
currently an Associate Professor with the Department of Electrical and
Electronic Engineering, The Hong Kong Polytechnic University. He is a Co-
Author of the book Next Generation Multiple Access (Wiley-IEEE Press).
His research interests include the next generation cellular technologies, such
as machine-type communications for the Internet of Things and integrated
sensing and communication. He is an IEEE ComSoc Distinguished Lecturer
for the class of 2025–2026. He was a recipient of the 2021 IEEE Signal
Processing Society Best Paper Award; the 2017 IEEE Signal Processing
Society Young Author Best Paper Award; the Best Student Award of 2022
IEEE International Conference on Acoustics, Speech, and Signal Processing
(ICASSP); and the Best Paper Award of the 2011 International Conference
on Wireless Communications and Signal Processing. He was recognized by
Clarivate Analytics as a Highly Cited Researcher in 2018. He is an Editor of
IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS and an Associate
Editor of IEEE T RANSACTIONS ON SIGNAL PROCESSING . He was a Leading
Guest Editor for the Special Issue on Massive Machine-Type Communications
for the IoT of IEEE W IRELESS COMMUNICATIONS .
Fan Liu (Senior Member, IEEE) received the
B.Eng. and Ph.D. degrees from Beijing Institute
of Technology (BIT), Beijing, China, in 2013 and
2018, respectively.
He is currently a Professor with the National
Mobile Communications Research Laboratory,
School of Information Science and Engineering,
Southeast University, Nanjing, China. Prior to that,
he was an Assistant Professor with the Southern
University of Science and Technology, Shenzhen,
China, from 2020 to 2024. Previously, he has held
academic positions with University College London (UCL), London, U.K.,
as a Visiting Researcher from 2016 to 2018, and a Marie Curie Research
Fellow from 2018 to 2020. His research interests include the general area
of signal processing and wireless communications, and in particular in the
area of integrated sensing and communications (ISAC). He is a member of
the IMT-2030 (6G) ISAC Task Group. He was listed among the World’s
Top 2% Scientists by Stanford University for Citation Impact from 2021 to
2024 and among the Elsevier Highly-Cited Chinese Researchers from 2023
to 2024. He was a recipient of several Best Paper Awards, including the
2025 IEEE Communications Society and Information Theory Society Joint
Paper Award, the 2024 IEEE Signal Processing Society Best Paper Award,
the 2024 IEEE Signal Processing Society Donald G. Fink Overview Paper
Award, the 2024 IEEE Communications Society Asia–Paciﬁc Outstanding
Paper Award, the 2023 IEEE Communications Society Stephan O. Rice
Prize, and the 2021 IEEE Signal Processing Society Young Author Best
Paper Award. He was the TPC Co-Chair of the Second to Fourth IEEE
Joint Communication and Sensing (JC&S) Symposium, the Symposium
Co-Chair of IEEE ICC 2026 and IEEE GLOBECOM 2023, and the Track
Co-Chair for IEEE WCNC 2024. He is the Founding Academic Chair of
the IEEE ComSoc ISAC Emerging Technology Initiative (ISAC-ETI), the
Vice Chair and a Founding Member of the IEEE SPS ISAC Technical
Working Group (ISAC-TWG), and an Elected Member of the IEEE SPS
Sensor Array and Multichannel Technical Committee (SAM-TC). He is an
Associate Editor of IEEE T RANSACTIONS ON COMMUNICATIONS , IEEE
TRANSACTIONS ON MOBILE COMPUTING , and IEEE O PEN JOURNAL OF
SIGNAL PROCESSING ; and a Guest Editor of IEEE J OURNAL ON SELECTED
AREAS IN COMMUNICATIONS , IEEE W IRELESS COMMUNICATIONS , and
IEEE V ehicular Technology Magazine.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply. 

HUANG et al.: LLM IN V2I: A DATA-DRIVEN PREDICTIVE BEAMFORMING FRAMEWORK 2527
Wei Xiang (Senior Member, IEEE) received the
B.Eng. and M.Eng. degrees in electronic engineering
from the University of Electronic Science and Tech-
nology of China, Chengdu, China, in 1997 and 2000,
respectively, and the Ph.D. degree in telecommu-
nications engineering from the University of South
Australia, Adelaide, SA, Australia, in 2004.
He was the Foundation Chair and the Head of the
Discipline of the IoT Engineering, James Cook Uni-
versity, Cairns, QLD, Australia. He is currently a La
Trobe Distinguished Professor, the Cisco Research
Chair of AI and the IoT, and the Director of the Cisco-La Trobe Centre for
AI and IoT, La Trobe University, Melbourne, VIC, Australia. He has authored
or co-authored more than 450 peer-reviewed articles, including three books
and 350 journal articles. His research interests include the Internet of Things,
wireless communications, machine learning for the IoT data analytics, and
computer vision.
Dr. Xiang has served in a large number of international conferences in the
capacity of the general co-chair, the TPC co-chair, and the symposium chair.
Derrick Wing Kwan Ng (Fellow, IEEE) received
the bachelor’s (Hons.) and Master of Philoso-
phy degrees in electronic engineering from The
Hong Kong University of Science and Technology
(HKUST), Hong Kong, in 2006 and 2008, respec-
tively, and the Ph.D. degree from The University
of British Columbia, Vancouver, BC, Canada, in
November 2012.
Following the Ph.D. degree, he was a Senior
Post-Doctoral Fellow with the Institute for Digi-
tal Communications, Friedrich-Alexander-University
Erlangen-N¨urnberg (FAU), Germany. He is currently a Scientia Associate
Professor with the University of New South Wales, Sydney, NSW, Australia.
His research interests include global optimization, integrated sensing and
communication (ISAC), physical layer security, IRS-assisted communication,
UA V-assisted communication, wireless information and power transfer, and
green (energy-efﬁcient) wireless communications. He has been recognized as
a Highly Cited Researcher by Clarivate Analytics (Web of Science) since
2018. He was a recipient of Australian Research Council (ARC) Discovery
Early Career Researcher Award in 2017; the IEEE Communications Society
Leonard G. Abraham Prize in 2023; the IEEE Communications Society
Stephen O. Rice Prize in 2022; the Best Paper Awards at the WCSP in
2020 and 2021; the IEEE TCGCC Best Journal Paper Award in 2018;
INISCOM 2018; the IEEE International Conference on Communications
(ICC) in 2018, 2021, 2023, and 2024; the IEEE International Conference
on Computing, Networking and Communications (ICNC) in 2016; the IEEE
Wireless Communications and Networking Conference (WCNC) in 2012; the
IEEE Global Telecommunication Conference (Globecom) in 2011, 2021, and
2023; and the IEEE Third International Conference on Communications and
Networking, China, in 2008. From January 2012 to December 2019, he served
as an Editorial Assistant to the Editor-in-Chief for IEEE T RANSACTIONS
ON COMMUNICATIONS . He is also an Editor of IEEE T RANSACTIONS
ON COMMUNICATIONS and an Associate Editor-in-Chief of IEEE O PEN
JOURNAL OF THE COMMUNICATIONS SOCIETY .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:06:17 UTC from IEEE Xplore.  Restrictions apply.