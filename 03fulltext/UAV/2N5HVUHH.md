---
title: "Radar Probing Optimization for Joint Beamforming and UAV Trajectory Design in UAV-Enabled Integrated Sensing and Communication"
zotero_key: "2N5HVUHH"
pdf_key: "95JQNCGP"
doi: "10.1109/TCOMM.2024.3506917"
collection: "UAV"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Radar Probing Optimization for Joint Beamforming and UAV Trajectory Design in UAV-Enabled Integrated Sensing and Communication — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025 4469
Radar Probing Optimization for Joint Beamforming
and UA V Trajectory Design in UA V-Enabled
Integrated Sensing and Communication
Yaxi Liu
 , Member, IEEE, Wencan Mao
 , Member, IEEE, Boxin He
 , Graduate Student Member, IEEE ,
Wei Huangfu
 , Member, IEEE, Tianyao Huang
 , Member, IEEE, Haijun Zhang
 , Fellow, IEEE,
and Keping Long
 , Senior Member, IEEE
Abstract— Unmanned aerial vehicle (UA V)-enabled massive
multiple-input-multiple-output (MIMO) integrated sensing and
communication (ISAC) is an emerging platform to perform
communication and sensing efficiently and flexibly. However,
the existing works barely consider the radar probing tasks
and neglect the benefits of the dedicated sensing signal. In this
paper, we focus on joint optimizations in radar probing tasks,
and a novel indicator is introduced, namely radar probing
error. Two optimizations in radar probing tasks are established:
i) joint transmit beamforming design for large-scale regional
radar probing and communication task; ii) joint transmit
beamforming and UA V trajectory design for communication
enhancement and radar probing task. For the former task,
we adopt both communication and novel sensing precoders to
further support the MIMO radar. A semidefinite relaxation is
utilized to relax the original non-convex problem, which is proven
to be tight. For the latter task, we adopt block coordinate
descent to alternately optimize the precoders and UA V trajectory
where the fractional programming approach and successive
convex approximation are further adopted. Experiment results
testify the validation of the proposed methods for radar probing
tasks in UA V-enabled MIMO ISAC. Moreover, results show the
fundamental trade-off between the dual functions and reveal the
effectiveness of the introduced sensing precoder.
Received 12 April 2024; revised 21 September 2024; accepted 16 November
2024. Date of publication 27 November 2024; date of current version 18 June
2025. This work is supported by the National Natural Science Foundation
of China (Grant No. 62301028, U21A20456, U22B2003, 62341103); in
part by the Beijing Natural Science Foundation under Grant L212004;
in part by the Fundamental Research Funds for the Central Universities
under Grants FRF-TP-22-002C2; in part by the Xiaomi Fund of Young
Scholar; and in part by the Young Scientists Fund of the National Natural
Science Foundation of China (62306030). The associate editor coordinating
the review of this article and approving it for publication was P. Sharma.
(Corresponding author: Haijun Zhang.)
Yaxi Liu and Wei Huangfu are with Beijing Advanced Innovation Center
for Materials Genome Engineering, Beijing Engineering and Technology
Research Center for Convergence Networks and Ubiquitous Services, School
of Computer and Communication Engineering, and the Shunde Innovation
School, University of Science and Technology Beijing, Beijing 100083, China
(e-mail: yaxi.ustb@gmail.com; huangfuwei@ustb.edu.cn).
Wencan Mao is with the Information Systems Architecture Science Research
Division, National Institute of Informatics, Tokyo 101-8430, Japan (e-mail:
wencan_mao@nii.ac.jp).
Boxin He, Tianyao Huang, Haijun Zhang, and Keping Long are with Beijing
Advanced Innovation Center for Materials Genome Engineering, Beijing
Engineering and Technology Research Center for Convergence Networks and
Ubiquitous Services, School of Computer and Communication Engineering,
University of Science and Technology Beijing, Beijing 100083, China (e-mail:
heboxin@xs.ustb.edu.cn; huangtianyao@ustb.edu.cn; haijunzhang@ieee.org;
longkeping@ustb.edu.cn).
Digital Object Identifier 10.1109/TCOMM.2024.3506917
Index Terms— 6G, UA V-enabled MIMO ISAC, radar probing
task, joint transmit beamforming, UA V trajectory planning.
I. I NTRODUCTION
A. Background
A
S
THE explosive growth of various communication
demands, the integrated sensing and communication
(ISAC) (a.k.a. dual-functional radar communication (DFRC)
[1], joint communication and radar sensing (JCAS) [2]) is
emerging as a key technology in future sixth-generation (6G)
wireless networks [3], [4], [5], [6]. In ISAC, both commu-
nication and radar systems share the physical infrastructure
and spectrum resources, thus it can provide high-throughput
communication with low energy consumption and high spec-
trum utilization. On account of rapid deployment, flexible
mobility, and robust line-of-sight links, the unmanned aerial
vehicle (UA V)-enabled ISAC has recently been recognized
as a promising auxiliary platform to perform communica-
tion and sensing simultaneously, especially for emergency
scenarios [7], [8], [9], [10].
Early works on UA V-enabled ISAC considered a single-
antenna scheme, which fails to sense multiple sensing target
(ST) while communicating with multiple communication user
(CU) with acceptable signal-to-interference-plus-noise ratio
(SINR) if they are not physically co-located. To address this
issue, massive Multiple-Input-Multiple-Output (MIMO) has
been developed for UA V-enable ISAC to synthesize multiple
beams toward multiple CUs and STs simultaneously. Among
various massive MIMO technologies, transmit beamforming
enables both sensing and communication functionality to use
its individual waveform, potentially supporting higher sensing
and communication performance.
However, the benefits of sharing spectrum and equipment
in UA V-enabled ISAC are also accompanied by some chal-
lenges in transmit beamforming design [11]. There exists a
trade-off between communication performance and sensing
performance where the improvement of one would deteriorate
the other [12]. Hence, it is essential to find an appropriate
beamforming matrix (or precoder) to satisfy both the com-
munication and the sensing demands in practical applications.
Furthermore, the scale of solution space is usually huge due
to the large number of optimization variables, making it
0090-6778 © 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4470 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
difficult to obtain a satisfactory solution within a limited time,
especially in massive MIMO systems [13]. Apart from the
transmit beamforming design, the dynamic nature and limited
energy of UA Vs add layers of complexity to the problem.
B. Related Works
From the algorithmic perspective, some mainstream opti-
mization algorithms are not suitable for solving the complex
transmit beamforming problem in UA V-enabled ISAC systems.
For example, the widely used meta-heuristic algorithms, e.g.,
particle swarm optimization [14], genetic algorithm [15] and
simulated annealing algorithms [16] perform poorly when
searching the solution from a huge-scale solution space. Mean-
while, the fast first-order gradient descent algorithms [17], [18]
are prone to fall into local optima and become computationally
expensive when decision variables are massive.
Consequently, the state-of-the-art methods for joint transmit
beamforming design in UA V-enabled ISAC systems are mainly
deep reinforcement learning (DRL) algorithms and convex
optimizations. Although the DRL algorithms can adapt to
dynamic scenarios with large numbers of variables, such meth-
ods heavily depend on the environment parameters and suffer
from low reproducibility [19], [20], [21], [22]. Besides, such
a black-box algorithm lacks interpretability. Other researchers
convert the original complex non-convex ISAC tasks into con-
vex forms, where the global optimal solutions can be obtained
within a limited time by convex optimization solvers [23],
[24], [25]. In this work, we follow the same strategy to increase
the reproducibility and interpretability of the algorithm.
From the practical task perspective, existing works of
UA V-enabled MIMO ISAC systems are dominated by either
communication or sensing performance, ranging from various
tasks. Common communication-dominated tasks [26], [27],
[28], [29], [30] include user quality of service improve-
ment, wide-range communication coverage, etc. Common
sensing-dominated tasks include target estimation, target track-
ing, and location [26], etc. Different tasks have varying
requirements for communication and sensing performance,
which can lead to a variety of optimizations. Specifically,
common indicators for evaluating communication performance
mainly include throughput [26], [29], [30], [31] and achievable
rate [12], [27], [28]; and those for measuring sensing perfor-
mance include Cramér-Rao bound (CRB) [26], and transmit
beam pattern (TBP) gain [27], [28], [29], [30], [31].
Some researchers focus on communication-dominated tasks
where communication metrics are usually the optimization
goal, subject to sensing, energy, and power constraints.
Deng et al. [26] maximized the average system throughput of
both uplink and downlink communications while guaranteeing
that the CRB of all target directions was smaller than a given
threshold. Meng et al. [27] maximized the achievable rate to
obtain the optimal beamforming vector where the TBP gain of
each target was required to be greater than a specific threshold.
Meng et al. [28] proposed a new integrated periodic sensing
and communication mechanism for UA V-enabled ISAC sys-
tems where the objective was to maximize the user achievable
rate, subject to the TBP gain constraints for all targets.
Lyu et al. [29], [30] maximized the average weighted sum-
rate throughput, ensuring that the TBP gain towards each target
location exceeded a specific threshold, while simultaneously
satisfying the requirements of the sensing frequency, sensing
power, and quality of service. They aimed to optimize the
beamforming vector, user association, sensing time selection,
and UA V trajectory.
Other researchers are concerned with sensing-dominated or
energy-dominated tasks. Xu et al. [12] aimed to seek the
trade-off between the computation capacity and the sensing
beam pattern gain. Their objective was to maximize the
weighted achievable offloading rate and the probing signal in
the target direction, and then the Pareto front could be obtained
to balance the performance of the communication and sensing
for specific practical demands. Khalili et al. [31] minimized the
average power consumption of a fixed-altitude UA V , involv-
ing the propulsion power consumption and the aerodynamic
power consumption. The communication constraints required
that the average achievable data rate exceed the minimum
value. The sensing constraints required that the difference
between the desired radar beam pattern and the ideal beam
pattern of all targets would not exceed a predefined threshold.
However, there are still limitations on the existing works
as follows. First, as far as we know, the existing works
barely concern the radar probing tasks. Radar probing tasks
utilize radar technology to detect and scan specific areas. Key
advantages of radar probing tasks include high penetration,
wide-area detection, flexibility, and security, thus they can be
widely used in geological and topographic mapping, agricul-
ture, environmental monitoring, search and rescue operations,
and other practical applications. In radar probing tasks, the
UA V tends to perform large-area radar scans over regions of
interest, and thus the ideal TBP shape should be designed to
define the scanning range. Nevertheless, the existing works
only consider the TBP values of some specific directions of
STs. More practically, it is necessary to consider that the shape
of the TBP closely approximates the predefined ideal shape of
some probing sectors.
In addition, the auxiliary sensing precoder is usually not
considered in the existing works to further enhance the sens-
ing performance. Although some works directly used the
sensing beamforming vector or the sensing covariance in
signal modeling [26], [32], the effect of the dedicated sensing
signal has not yet been adequately analyzed and verified in
experiments.
C. Contributions of This Paper
To tackle the above limitations, we focus on the radar
probing tasks in UA V-enabled ISAC where a novel indicator
is proposed to evaluate the sensing performance, namely
radar probing error. It consists of a weighted sum of two
indicators: i) the mean square error (MSE) of probing sector
matching (PSM) with certain central sector directions and
probing widths and ii) the MSE of the cross-correlation
pattern. In addition, we introduce the sensing precoder to
provide an extra degree of freedom (DoF) for the optimiza-
tion. It improves sensing performance while causing slightly
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4471
additional sensing interference for communication, which may
be canceled by the channel matrix.
However, the introduced sensing indicator and precoder both
bring some new challenges. With regard to the introduced
sensing indicator, the radar probing error is complex and
non-convex with respect to the precoders. In addition, the
benefits of UA V maneuverability also complicate the problem
of joint transmit beamforming and UA V trajectory design,
especially when aiming for dual functions. Moreover, the
location of the UA V is limited by the similarity of user
channels and guided by the communication performance.
Additionally, the limited energy of the UA V also adds a layer
of complexity to the problem. As for the introduced sensing
precoder, it increases the complexity of the problem in two
ways: first, the sensing indicator is related to the additional
sensing covariance; second, the communication indicator has
an additional sensing interference term.
Our contributions mainly lie in three aspects, summarized
as follows.
• We establish two optimizations for radar probing tasks
in UA V-enabled MIMO ISAC. The former optimization
jointly optimizes both the communication and sensing
precoders to minimize the radar probing error while meet-
ing SINR and power constraints for large-scale regional
radar probing and communication tasks. The latter opti-
mization jointly optimizes precoders and UA V trajectory
to minimize the radar probing error while maximizing the
average throughput simultaneously under the constraints
of UA V energy consumption for communication enhance-
ment and radar probing tasks.
• For the former optimization, we relax it into a sequential
quadratic programming (SQP) by using a semidefinite
relaxation (SDR) strategy where the relaxation is proved
to be tight. For the latter optimization, we adopt the block
coordinate descent (BCD) to alternately optimize the
precoders and UA V trajectory, and they are formulated as
two sub-problems. For the sub-problem of beamforming
design, we adopt the SDR and direct fractional program-
ming (FP) approach to solve it. For the sub-problem of
UA V trajectory planning, we adopt the successive convex
approximation (SCA) where the first-order Taylor expan-
sion is conducted and slack variables are introduced.
• Experiment results verify the feasibility and conver-
gence of the proposed methods for the formulated
radar probing tasks in UA V-enabled MIMO ISAC.
In addition, the newly introduced sensing precoder helps
improve the sensing performance at a small sacrifice in
communication performance, thereby improving the inte-
grated performance. Moreover, there exists a fundamental
trade-off between the dual functions by adjusting the
weight parameter in the optimization. Also, other sys-
tem parameters are analyzed, including the user number,
antenna array number, maximum UA V energy consump-
tion, and channel state information (CSI) accuracy.
The rest of this article is organized as follows. Section II
presents the system model. Sections III and IV formulate the
optimization problems for the proposed two radar probing
Fig. 1. Illustration of the DFRC system.
tasks, respectively. Sections V and VI describe their exper-
imental setups and results. Finally, Section VII concludes this
article.
Notations: In this paper, boldface letters represent vectors
(lower case) or matrices (upper case). AT, A∗, AH, rank (A)
and tr (A) represent the transpose, the conjugate, the Her-
mitian conjugate, the rank, and the trace of matrix A,
respectively.∥x∥2 represents the L2 norm of vector x.|a|
and arg (a) denote the magnitude and phase angle of complex
number a.⊗ denotes the Kronecker product operator. [A]i,j
and [x]i denotes the (i, j)-th element of matrix A and the
i-th element of vector x, respectively. [A]i,: and [A]:,j denote
the sub-matrices (or vectors) containing i-th row and j-th
column of matrix A, respectively. E (·) denotes the stochastic
expectation. Re (·) denotes the real part. Let 0m×n and In
denote m× n zero matrix and n-dimensional identity matrix,
respectively. j denotes the imaginary unit. S +n denotes the set
consisting of all n-dimensional complex positive semidefinite
matrices.
II. S YSTEM MODEL
In this section, we introduce the UA V-enabled dual-
functional radar-communication system. Then, we describe the
transmit signal model with both the communication precoder
and sensing precoder. Next, we introduce the design guidelines
for evaluating the performance of the MIMO communication
system and MIMO radar system.
A. DFRC System
As shown in Fig. 1, we consider a UA V-enabled dual-
functional radar-communication system that provides down-
link communication service for I single-antenna CUs, denoted
as C1, C2, . . . , CI, and simultaneously senses J probing sec-
tors of interest, denoted as T1, T2, . . . , TJ. We assume that
there is a rotary-wing UA V U, equipped with a vertically
placed Uniform Linear Array (ULA) with M antennas, shared
by the MIMO communication system and the MIMO radar
system in the service region R.
We divide the whole service period T into N time slots
where the slot length is T Slot = TN . Let the time slot set be
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4472 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
T ={t1, t2, . . . , tN}. In each time slot, the DFRC system
simultaneously provides communication and sensing service.
During the interval between two time slots, the UA V flies
from the location of the previous time slot to that of the next
one, with the flight time not included as part of the service
time. Since the UA V hovers at a specific location to provide
ISAC service, and both the CUs and STs are stationary, we do
not consider the Doppler shift. We adopt a three-dimensional
(3D) Cartesian coordinate system, and the UA V is flying at a
specific altitude zUn. The UA V location in xoy plane at time
slot tn is denoted as qn =

xUn, yUn, T ∈ R2×1. Let dCn,i =
xCn,i, yCn,iT∈ R2×1, i∈{1, 2, . . . , I} denote the location of
ground CU Ui in xoy plane at time slot tn. Regarding target
detection, we tend to probe some sectors of interest for large-
scale searching, and the central direction set of the probing
sectors and their corresponding probing width set are denoted
as{αn,1, αn,2, . . . , αn,J} and{Dn,1, Dn,2, . . . , Dn,J} at tn,
respectively.
B. Transmit Signal Model
The antenna array on the UA V is shared by the communi-
cation system and radar system. We assume that the UA V not
only transmits information-bearing signals for CUs but also
transmits dedicated sensing signals to achieve a higher degree
of freedom for sensing tasks. Thus, the transmit signal of UA V
U at tn is a superimposition of information signals and radar
waveforms, given by
xn = W Cn cn + W Sn sn =
IX
i=1
wCn,icn,i +
MX
m=1
wSn,msn,m,
(1)
where vector cn = [c n,1, cn,2, . . . , cn,I ]T ∈ CI×1 includes I
information signals to be communicated to I users; cn,i repre-
sents the desired information signal from U to Ci at tn; matrix
W Cn ∈ CM×I represents the beamforming/precoding matrix
for information signals; vector sn = [sn,1, sn,2, . . . , sn,M ]T∈
CM×1 includes M individual radar waveforms; matrix W Sn∈
CM×M represents the beamforming matrix for radar wave-
forms; vector wCn,i = W Cn :,i ∈ CM×1 and wSn,m =
W Sn :,m ∈ CM×1 represent the beamforming vectors for
signal cn,i and sn,m, respectively. The information signal cn,i
and dedicated radar waveform sn,m are both temporally-white
and wide-sense stationary stochastic processes with zero mean.
It is assumed that all information signals and dedicated radar
waveforms are uncorrelated from each other. We also assume
that all signals are normalized to have unit power.
Our goal is to jointly design the precoders W Cn and W Sn for
achieving better system performance. Here, in consideration
of the transmit hardware requirements, it is assumed that
the antenna arrays on UA Vs all satisfy per-antenna power
constraints, given by
E

|[xn]m|2

=


 W Cn m,: 

22 + 

 W Sn m,: 

22
= P Max
M , ∀n, m, (2)
where P Max represents the maximum transmit power for all
antennas.
C. Performance on Communication System
Common performance indicators for measuring the Quality
of Service (QoS) of the multiuser broadcast communication
system are the Signal to Interference plus Noise Ratio (SINR)
[33] and throughput [26]. Then, we will introduce how to
calculate these indicators.
The channel output of I CUs at tn is computed as
yn = Hnxn + nAWGNn , (3)
where vector nAWGNn = hnAWGNn,1 , nAWGNn,2 , . . . , nAWGNn,I iT ∈
CI×1 represents the noise set where nAWGNn,i ∼CN  0, σ2 is
the Additive White Gaussian Noise (AWGN) with zero mean
and variance σ2 for Ci at tn; matrix Hn∈ CI×M represents
the instantaneous downlink channel. Let hn,i = [H n]i,: ∈
C1×M denote the downlink channel vector between U and Ci.
Here, we adopt the Rician fading channel [26], [34] to take
both the line-of-sight (LoS) signal path and the line-of-sight
(NLoS) signal paths into account, expressed as hn,i = hn,iH
where
hn,i =
r κ
κ + 1
s
β0
DU→Cn,i 2 hLoSn,i +
r
1
κ + 1
s
β0
DU→Cn,i 2 hNLoSn,i .
(4)
Here, DU→Cn,i =
q

qn− dCn,i

22 + zUn 2; κ denotes the Rician
K-factor, measuring the ratio of the power of the direct path
to the power of the scatter paths; β0 represents channel power
gain at a reference distance d0 = 1 m. Term hNLoSn,i ∼
CN
 
0, σ2h IM  denotes the small-scale Rayleigh fading com-
ponent. Term hLoSn,i denotes the LoS component, expressed as
hLoSn,i = a  qn, dCn,i. Vector a  qn, dCn,i ∈ CM×1 is the
steering vector towards Ci, given by
a
 
qn, dCn,i = h1, e−j2π dλ sin(θ(qn,dCn,i)), . . . ,
e−j2π dλ (M−1) sin(θ(qn,dCn,i))iT, (5)
where d and λ denote antenna separation and carrier
wavelength, respectively; θ
 
qn, dCn,i denotes the angle of
departure corresponding to Ci, calculated by
θ
 
qn, dCn,i = arcsin zUn q

qn− dCn,i

22 + zUn 2 . (6)
It is worth noting that θ
 
qn, dCn,i is the horizontal angle of
the UA V towards the CU.
Then, the received signal of CU Ci at tn can be written as
yn,i = [yn]i = hn,ixn = hn,iwCn,icn,i| {z }
Desired signal
+ nAWGNn,i| {z }
AWGN
+
X
ˆi∈{1,...,I}
ˆi̸=i
hn,iwCn,ˆicn,ˆi
| {z }
Inter-user interference signals
+
MX
m=1
hn,iwSn,msn,m
| {z }
Sensing interference signals
.
(7)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4473
The interference signals for CU Ci include not only the
inter-user interference signals, or more precisely, the commu-
nication interference signals, but also the sensing interference
signals. If we only design the communication precoder W Cn ,
the sensing interference signal is zero and there are only
inter-user interference signals. We not only design the com-
munication precoder but also introduce the sensing precoder,
and thus the dedicated sensing signals, or more precisely, the
dedicated sensing interference, will degrade the communica-
tion ability to a certain extent. Nonetheless, the dedicated
sensing signals provide more degree of freedom to enhance
the sensing performance. Moreover, when the directions of CU
and probing sector relative to UA V are sufficiently distinct, the
beamforming vector W Sn can eliminate the sensing interfer-
ence towards the CU while form highly focused beams towards
the direction of probing sector to support sensing tasks.
Consequently, the SINR of downlink communication for Ui
at tn can be calculated by
γn,i =
hn,iwCn,i2
IP
ˆi=1
ˆi̸=i
hn,iwCn,ˆi2 + MPm=1 hn,iwSn,m2 + σ2 . (8)
Furthermore, when designing the UA V trajectory, the average
throughput can be regarded as the objective that reflects
communication performance, given by
R = 1N I
NX
n=1
IX
i=1
log2 (1 + γn,i) . (9)
D. Performance on Radar System
We consider two common performance indicators for mea-
suring radar systems, say TBP and CCP. The former TBP
means the transmit power at the location of ST, and the latter
CCP indicates the dependence between the baseband signals
of two STs. To better describe the practical detection tasks,
we adopt the following two design guidelines [32], [35] in the
MIMO radar system:
1) Minimize the MSE of the probing sector matching,
or more precisely, minimize the MSE between the
obtained TBP and the ideal TBP.
2) Minimize the MSE of the CCP between every two
central directions of the probing sectors.
To this aim, we first describe the expression of the above
two indicators and then express the design criteria related to
indicators.
Here, the communication signals can also be exploited for
sensing tasks, that is, we use the composite transmit signal
xn to sense targets. In this case, the information signals
for communication are not considered as interference for the
probing directions. The baseband signal in an angular direction
α at tn is ySn (α) = aH (α) xn where
a (α) =
h
1, ej2π dλ sin α, . . . , ej2π dλ (M−1) sinαiT . (10)
Then, the transmit power (or TBP) in direction α at tn can
be computed by
P TBPn  α = a (α)H W Cn W Cn H + W Sn W Sn H  a (α) . (11)
The CCP between directions αj1 and αj2 at tn can be deduced
by
P CCPn (αj1 , αj2 )
= E

ySn (αj2 )H ySn (αj1 )
= a (αj2 )H

W Cn W Cn H + W Sn W Sn H  a (αj1 ) . (12)
In the practical probing task, the ideal TBP In (α) can be
described as a rectangular gate function where the values of
sectors with specific probing widths are defined as probing
power, and the other values are set to zero. If αn,j−Dn,j/2≤
α≤ αn,j + Dn,j/2,∀j, In (α) = P Sen; otherwise, In (α) = 0.
To evaluate the difference between the obtained TBP and the
ideal TBP, we finely sample in a certain angular range and
take the MSE on all sampled angles for all time slots as the
first design guideline, expressed as
G1 = 1N K
NX
n=1
KX
k=1
In (αk)− P TBPn (αk)2 , (13)
where K represents the number of sampled angles, and αk
represents the k-th sampled angle. The MSE of the CCP
between every two central directions αj1 and αj2 for all time
slots, i.e., the second design guideline, can be calculated by
G2 = 2N (J 2−J)
NX
n=1
J−1X
j1=1
JX
j2=j1+1
P CCPn (αn,j1 , αn,j2 )2 .
(14)
III. J OINT TRANSMIT BEAMFORMING DESIGN FOR
LARGE -SCALE REGIONAL RADAR PROBING AND
COMMUNICATION TASK
In this section, we first formulate a problem for large-scale
regional radar probing and communication tasks. Then,
we convert the original complex and non-convex problem to its
relaxation based on a semidefinite relaxation strategy, which
is proved to be tight.
A. Problem Formulation
In the large-scale regional communication and sensing
probing task, the flight plan is to ensure the comprehensive
coverage of a predefined region. The UA V equipped with
an ISAC antenna array automatically flies from a specific
charging station to each predetermined location along the
flight route, hovering at each location to provide ISAC ser-
vice. After completing its flight mission, the UA V returns
to the charging station for recharging. Since the trajec-
tory of the UA V and the time of its hover service are
predesigned, the energy consumption of the UA V is predeter-
mined. Such a task is radar-dominated and aims to minimize
the radar probing error (the MSE of the PSM plus that of
CCP), subject to the communication requirements and power
requirements.
Let W C = W C1 , W C2 , . . . ,W CN 	 and W S =
W S1 , W S2 , . . . ,W SN 	 denote the communication precoder set
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4474 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
and the sensing precoder set, respectively. Then, the optimiza-
tion problem is formulated as
(P1) : min
{WC,WS} O = G1 + ϕG2
= 1N K
NX
n=1
KX
k=1
In (αk)− P TBPn (αk)2 + 2ϕN (J 2−J)·
NX
n=1
J−1X
j1=1
JX
j2=j1+1
P CCPn (αn,j1 , αn,j2 )2 (15a)
s.t. C1: wCn,iwCn,iH∈S +M ,∀n, i, (15b)
C2: wSn,mwSn,mH∈S +M ,∀n, m, (15c)
C3:



WCnm,:


22 + 


WSnm,:


22 = P MaxM ,
∀n, m, (15d)
C4: γn,i≥ THSINR,∀n, i, (15e)
where C1 and C2 requires that the matrices wCn,iwCn,iH and
wSn,mwSn,mH are all complex positive semidefinite; C3 are the
per-antenna power constraints; C4 are the SINR constraints for
all CUs. Parameter ϕ∈ [0, +∞) indicates the importance of
the MSE of the PSM compared with the MSE of CCP.
B. Semidefinite Relaxation Strategy
The optimization problem (P1) with a huge number of
optimization variables is complex and non-convex, and thus it
is quite challenging to solve. To simplify the original problem,
we decompose the problem (P1) into N sub-problems accord-
ing to N independent time slots. Then, each sub-problem at
tn can be described as
(P2) : min
{WCn,WSn} On = Gn,1 + ϕGn,2 (16a)
s.t. C1: wCn,iwCn,iH∈S +M ,∀i, (16b)
C2: wSn,mwSn,mH∈S +M ,∀m, (16c)
C3:



WCnm,:


22 + 


WSnm,:


22 = P MaxM ,∀m,
(16d)
C4: γn,i≥ THSINR,∀i. (16e)
Notice that the sub-problem (P2) is still non-convex, and
we then will introduce an SDR strategy [32] to convert
the non-convex problem to sequential quadratic programming
which can be solved in polynomial time with the convex
optimization toolboxes [23], [24], [25].
First, we define the covariance matrix of precoder as
Rn = WCnWCnH + WSnWSnH
=
IX
i=1
wCn,iwCn,iH +
MX
m=1
wSn,mwSn,mH
=
IX
i=1
Rn,i +
MX
m=1
wSn,mwSn,mH , (17)
where Rn,i = wCn,iwCn,iH. Thereafter, the SINR
constraint (16e) can be rewritten to a linear form with
respect to the rank-one matrices Rn,1, Rn,2, . . . ,Rn,I, given
in (18), as shown at the bottom of the next page.
Meanwhile, the sensing design guidelines in the objective
function (16a) can be converted to
Gn,1 (Rn) = 1K
KX
k=1
In (αk)− a (αk)H Rna (αk)2 , (19)
Gn,2 (Rn) = 2J 2− J
J−1X
j1=1
JX
j2=j1+1
a (αn,j2 )H Rna (αn,j1 )2 . (20)
Then, the optimization problem (P2) can be reformulated as
the following equivalent form:
(P3) : min
{Rn,Rn,1,...,Rn,I}
On (Rn) = Gn,1 (Rn)
+ ϕGn,2 (Rn) (21a)
s.t. C1: Rn∈S +M , (21b)
C2: Rn−
IX
i=1
Rn,i∈S +M , (21c)
C3: Rn,i∈S +M ,∀i, (21d)
C4: [Rn]m,m = P MaxM ,∀m, (21e)
C5:

1 + 1THSINR

hn,iH Rn,ihn,i
≥ hn,iH Rnhn,i + σ2, ∀i, (21f)
C6: rank (Rn,i) = 1,∀i, (21g)
where the SINR constraint (21f) is derived from (18). Notice
that the optimization problem (P3) is still non-convex due to
rank-one constraints. Therefore, we here omit the rank-one
constraints in (21g), and the problem (P3) can be further
relaxed to the following form:
(P4) : min
{Rn,Rn,1,...,Rn,I}
On (Rn) (22a)
s.t. (21b), (21c), (21d), (21e), (21f ). (22b)
C. Sequential Quadratic Programming
Next, we will show that the problem (P4) is a sequential
quadratic programming [35]. Define vec (Rn) as the vectoriza-
tion operation of matrix Rn where Rn∈ RM×M is converted
to a vector vec (Rn)∈ RM 2×1 by stacking the columns of Rn
on top of one another. Thereafter, the TBP and CCP terms in
the objective function are rewritten as
a (αk)H Rna (αk) =vec a (αk)H Rna (αk)
=

a (αk)T⊗ a (αk)H

vec (Rn)
=− AkT vec (Rn) , (23)
a (αj2 )H Rna (αj1 ) =vec a (αj2 )H Rna (αj1 )
=

a (αj1 )T⊗ a (αj2 )H

vec (Rn)
=Cj1,j2
Hvec (Rn) , (24)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4475
where Ak =−a (αk)⊗ a (αk)∗ and Cj1,j2 = a (αj1 )∗⊗
a (αj2 ). Inserting (23) and (24) into the objective function
On (R) yields
On (R)
= 1K
KX
k=1

In (αk) + AkT vec (Rn)2
+ 2ϕJ 2− J
J−1X
j1=1
JX
j2=j1+1
Cj1,j2 Hvec (Rn)2
= 1K
KX
k=1


 In (αk)
P Sen AkT
 

P Sen
vec (Rn)




2
+ 2ϕJ 2− J
J−1X
j1=1
JX
j2=j1+1
h0 Cj1,j2 H i  P Senvec (Rn) 2
= RnT SnRn, (25)
where
Sn
= 1K
KX
k=1


In(αk)
P Sen
Ak


 In (αk)
P Sen AkT

+ Re

 2ϕ
J 2− J
J−1X
j1=1
JX
j2=j1+1


0
Cj1,j2


h
0 Cj1,j2
H
i

 .
(26)
Then, the optimization problem (P4) can be reformulated as
(P5) : min
{Rn,Rn,1,...,Rn,I ,Rn}
RnT SnRn (27a)
s.t. (21b), (21c), (21d), (21e), (21f ), (27b)
C6: Rn =
 P Sen
vec (Rn)

. (27c)
So far, the optimization problem (P5) is convex where the
global optimum can be obtained in polynomial time via
standard convex optimization tools, such as CVX [23]. It is
worth noting that the parameter P Sen can be set artificially by
adding a constraint or directly obtained by the optimizer.
D. Relaxation Tightness
Once we obtain the global optimum
 ˆRn, ˆRn,1, . . . ,ˆRn,I 	
of the problem (P5), we use them to compute another solution
Algorithm 1 Pseudocode of the Joint Transmit Beamforming
Design for Large-Scale Regional Radar Probing and Commu-
nication Task
Input: β0, σ, d, P Max, ϕ, qn, I, J, M, dCn,i,∀n, i, αn,j,
Dn,j,∀n, j, TH SINR
Output: WC, WS
1: for n← 1, . . . , Ndo
2: Calculate intermediate variable Sn.
3: Obtain the global optimum
n
ˆRn, ˆRn,1, . . . ,ˆRn,I
o
by
solving the convex problem (P5) via convex optimization
tools.
4: Rn← ˆRn.
5: wCn,i← ˆRn,ihn,i√hn,i H ˆRn,ihn,i .
6: Rn,i← wCn,iwCn,iH.
7: W
S
nW
S
n
H
← Rn−
IP
i=1
Rn,i.
8: Calculate W
S
n based on the Cholesky decomposition.
9: W
C
n←

wCn,1 wCn,2 . . . wCn,I .
10: end for
11: WC← nWC1 , WC2 , . . . ,WCN o.
12: WS← nWS1, WS2, . . . ,WSN o.

Rn, Rn,1, . . . ,Rn,I
	
, given by
Rn = ˆRn, Rn,i = wCn,iwCn,iH , (28)
wCn,i = ˆRn,ihn,iq
hn,iH ˆRn,ihn,i
. (29)
It is worth noting that the solution

Rn, Rn,1, . . . ,Rn,I
	
is a global optimum to problem (P2), which is proved in
the Appendix. Therefore, the semidefinite relaxation is tight.
The algorithm process of the joint transmit beamforming
for the problem (P1) is shown in Algorithm 1. Notice that
the most time-consuming calculation portion in joint trans-
mit beamforming is the optimization for the problem (P5).
To consider the worst situation, the computation complexity
of the SQP is O
 
I 6.5M 6.5 log   1ϵ  with a given solution
accuracy ϵ based on the primal-dual interior-point algorithm
[32], [36], [37].
γn,i = hn,iH wCn,iwCn,iH hn,iIP
i=1
hn,iH wCn,iwCn,iH hn,i− hn,iH wCn,iwCn,iH hn,i + MP
m=1
hn,iH wSn,mwSn,mH hn,i + σ2
=
hn,iH Rn,ihn,i
hn,iH
 IP
i=1
Rn,i +
MP
m=1
wSn,mwSn,mH

hn,i− hn,iH Rn,ihn,i + σ2
= hn,iH Rn,ihn,i
hn,iH Rnhn,i− hn,iH Rn,ihn,i + σ2≥ THSINR,∀i.
(18)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4476 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
IV. J OINT TRANSMIT BEAMFORMING AND UAV
TRAJECTORY DESIGN FOR COMMUNICATION
ENHANCEMENT AND RADAR PROBING TASK
In this section, we first formulate a problem for the com-
munication enhancement and radar probing task. To solve the
complex non-convex problem, we adopt the BCD to alternately
optimize the precoders and UA V trajectory.
A. Problem Formulation
Due to the limited energy of the UA V , letting the UA Vs
fly through the whole region will lead to unnecessary energy
consumption and reduce the effective service time. Instead,
planning the UA V’s trajectory based on system performance
will contribute to energy conservation. Therefore, except
for optimizing the communication and sensing precoders,
designing an appropriate UA V trajectory is a key issue in
communication enhancement and sensing probing tasks. In this
task, our goal is to both minimize the radar probing error (the
MSE of PSM plus that of CCP) and maximize the average
throughput by jointly designing the dual functional precoders
(communication precoder and sensing precoder) and 2D UA V
trajectory during the flight period, under the per-antenna power
constraints (2) and UA V energy consumption constraints.
At tn, the energy consumption of the UA V is primarily
composed of two key components: ISAC transmit energy and
propulsion energy [9], written as EUA Vn = EISACn + EFlyn . The
former ISAC transmit energy is given by
EISACn = T Slottr W Cn W Cn H + W Sn W Sn H  = T SlotP Max.
(30)
The latter propulsion energy enables the UA V to fly or hover
in the air, calculated as equation (31), shown at the bottom
of the next page, where Vm denotes flying speed of UA V Um,
V T denotes tip speed of the rotor blade, V M denotes mean
rotor induced velocity in hover, RF denotes fuselage drag ratio,
ρ denotes air density, SR denotes rotor solidity, AR denotes
rotor disc area, CDra denotes profile drag coefficient, V Ang
denotes blade angular velocity, RRot denotes rotor radius, F Cor
denotes incremental correction factor to induced power, and
W Air denotes aircraft weight.
Then, the total UA V energy consumption is
EUA V=
NX
n=1
EUA Vn . (32)
Let Q ={q1, q2, . . . ,qN} denote the 2D UA V location set.
Then, the optimization problem is formulated as
(P6) : min
{Q,W C,W S} O = G1 + ϕG2− ψR =
G1 + ϕG2− ψ 1N I
NX
n=1
IX
i=1
log2 (1 + γn,i) (33a)
s.t. (16b), (16c), (16d), (33b)
C4:EUA Vn ≤ THE,∀n, (33c)
C5:∥qn− qn−1∥2≤ ∆Max, n∈{ 2, . . . , N} ,
(33d)
C6:q1 = qI, qN = qF, (33e)
C7:xMin≤ xCn,i≤ xMax,∀n, i, (33f)
C8:yMin≤ yCn,i≤ yMax,∀n, i, (33g)
where C4 are the UA V energy constraints where THE denotes
the maximum threshold of UA V energy consumption; C5 are
the UA V maximum flight distance constraints; C6 are the
initial and final location constraints; C7 and C8 are the UA V
boundary constraints where xMin, yMin and xMax, yMax are the
minimum and maximum 2D range of the UA V , respectively.
Parameter ψ ∈ [0, +∞) indicates the importance of the
communication performance (average throughput) compared
with the sensing performance (radar probing error).
The optimization problem (P6) is complex and non-convex,
and thus it is quite challenging to solve. To simplify the
original problem, we adopt the BCD to optimize the variables
alternately. Then, problem (P6) can be decomposed into two
sub-problems (P7) and (P8). The former sub-problem (P7) is
to optimize the communication and sensing precoders W C
and W S under the fixed UA V trajectoryQ, and the latter sub-
problem (P8) is to optimize Q under the fixed W C and W S.
B. Transmit Beamforming Design for Sub-Problem (P7)
We first formulate the sub-problem (P7) for transmit
beamforming design, where the communication and sensing
precoders are both considered. When the UA V trajectory Q is
fixed, the sub-problem (P7) is formulated as
(P7) : min
{W C,W S} O = G1 + ϕG2− ψR (34a)
s.t. (16b), (16c), (16d). (34b)
Notice that the sub-problem (P7) is non-convex
due to the non-convex objective (34a). Let R =
{R1, R2, . . . ,RN} denote the covariance matrix set;
RCi ={R1,i, R2,i, . . . ,RN,i} denote the covariance matrix
set of Ci. According to equations (17), (19), and (20), the
optimization problem (P7) can be then reformulated as the
following equivalent form:
(P7.1) : min
{R,RC1,...,RCI} O = G1 + ϕG2− ψR (35a)
s.t. (21b), (21c), (21d), (21e), (21g). (35b)
Here, we also omit the rank-one constraint, and such a
relaxation is tight.
Notice that problem (P7.1) is still non-convex due to
the average throughput, and then we adopt the direct FP
approach [38] on the communication performance term. Let
F In,i be hn,iH Rn,ihn,i, F IIn be hn,iH Rnhn,i, and the auxil-
iary variable set be y ={yn,i|∀n, i}. Then, the problem (P7.1)
is equivalent to:
(P7.2) : min
{R,RC1,...,RCI ,y} O = G1 + ϕG2− ψ 1N I
NX
n=1
IX
i=1
log2

1 + 2 yn,i
q
F In,i− yn,i2  F IIn− F In,i + σ2  (36a)
s.t. (21b), (21c), (21d), (21e). (36b)
We optimize the primal variables R, RC1 , . . . ,RCI and the
auxiliary variable y iteratively. When other variables are fixed,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4477
Algorithm 2 Pseudocode of Transmit Beamforming Design
for Sub-Problem (P7)
Input: Q(l−1), W C(l−1), W S(l−1), InP2 =σ, d, P Max, ϕ, I,
J, M, dCn,i,∀n, i, αn,j, Dn,j,∀n, j, TH SINR, κ, σ2h 	
Output: W C, W S
1: W C(s=0)← W C(l−1).
2: W S(s=0)← W S(l−1).
3: R(s=0) = W C(s=0)W C(s=0)H + W S(s=0)W S(s=0)H.
4: Rn,i(s=0) = wCn(s=0)wCn(s=0)H.
5: RCi (s=0) = nRC1,i(s=0), RC2,i(s=0), . . . ,RCN,i (s=0)o.
6: for s←{1, 2, . . . , S} do
7: Fix R(s−1), RC1 (s−1), . . . ,RCI (s−1) and obtain the
optimal y according to (37).
8: yn,i(s)← yn,i∗,∀n, i.
9: Fix y and obtain the optimal R∗, RC1∗, . . . ,RCI∗ by
solving the convex problem (P7.3) via convex optimization
tools.
10: R(s), RC1 (s), . . . ,RCI (s)← R∗, RC1∗, . . . ,RCI∗.
11: if the objective in (P7.3) converges then
12: Break
13: end if
14: end for
the closed form of the auxiliary variable yn,i is
yn,i∗ = qF In,i/  F IIn,i− F In,i + σ2 ,∀n, i. (37)
When the auxiliary variable y is fixed, we optimize the
variables R, RC1 , . . . ,RCI by solving (P7.2).
According to equations (23), (24), (25), and (26), the
optimization problem (P7.2) can be reformulated as
(P7.3) : min
{R,RC1,...,RCI ,y}
NX
n=1
rnT Snrn− ψ 1N I
NX
n=1
IX
i=1
log2

1 + 2 yn,i
q
F In,i− yn,i2  F IIn− F In,i + σ2  (38a)
s.t. (21b), (21c), (21d), (21e), (27c). (38b)
So far, the optimization problem (P7.3) is convex where the
optimum can be obtained in polynomial time via standard
convex optimization tools. The pseudocode of the trans-
mit beamforming design for sub-problem (P7) is shown in
Algorithm 2. Here, l denotes the epoch index in BCD, and s
denotes the iteration index in FP.
C. UAV Trajectory Design for Sub-Problem (P8)
Then, we formulate the sub-problem (P8) for UA V tra-
jectory design. When precoders W C and W S are fixed, the
sub-problem (P8) is formulated as
(P8) : min
{Q}
O = G1 + ϕG2 + ψR (39a)
s.t. (33c), (33d), (33e), (33f ), (33g). (39b)
However, the sub-problem (P8) is difficult to solve due to the
non-convex objective. To simplify this problem, the channel
can be rewritten as
hn,i = 1DU→Cn,i
 r κ
κ + 1
p
β0hLoSn,i +
r
1
κ + 1
p
β0hNLoSn,i
!
= 1DU→Cn,i ehn,i. (40)
Then, the objective is provided in equation (41), as shown at
the bottom of the next page. We adopt the channel matrix
eh(s−1)n,i in its previous iteration to approximate that in this
iteration. Note that the objective (41) are still non-convex.
To solve the problem (P8), we adopt the SCA technique which
approximates the solution to the original non-convex prob-
lem by iteratively solving a series of convex approximation
problems [26]. First, we choose the optimal solution Q(l−1)
obtained from the previous generation in the BCD algorithm
(l denotes the epoch index in BCD) as the starting solution
and set the initial iteration number as s = 0 (s denotes the
iteration index in SCA).
Then, we use first-order Taylor expansion to approximate
the term f In,i in (41) into its convex form, which is also the
global lower bound, given by
f In,i(Tn,i)≥ f In,i(Tn,i(s−1))− ∂f In,i
∂Tn,i(s−1)
 
Tn,i− Tn,i(s−1),
(42)
where Tn,i =


qn− dCn,i

22 + zUn 2, and the expression of the
partial
∂f In,i
∂Tn,i is provided in equation (43), as shown at the
bottom of the next page. Therefore, the terms f In,i,∀n, ican
be converted to their convex forms related to Tn,i based on
their known previous generation value Tn,i(s−1).
Next, we introduce the slack variables pn,i,∀n, ito approx-
imate term f IIn,i, given by
f IIn,i≈ log2  epn,i   IX
ˆi=1
ˆi̸=i
ehn,iwCn,ˆi2 + MX
m=1
ehn,iwSn,m2 + σ2,
(44)
where epn,i satisfies
1
epn,i≤


qn(s−1)− dCn,i

22 + zUn 2 + 2 qn(s−1)− dCn,iH
 
qn− qn(s−1). (45)
EFlyn = hP B 1 + 3Vm2/V T2 + P Ind
rq
1 + V 4m /(4V M2)− V 2m /2· V M2 + 1/2RFρSRARVm3
i∥qk,n− qk,n−1∥2
Vm
+
 
P B + P Ind T Slot, P B = 1/8CDraρSRARV Ang3RRot3, P Ind =  1 + F Cor W Air3/2/p2· ρ· AR. (31)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4478 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
Algorithm 3 Pseudocode of UA V Trajectory Planning for Sub-
Problem (P8)
Input: W C(l−1), W S(l−1), Q(l−1), In P3 = σ, d, I, M,
dCn,i,∀n, i, TH SINR, κ, σ2h , TH E, ∆Max, Vm, V T, V M, RF,
ρ, SR, AR, CDra, V Ang, RRot, F Cor, W Air	
Output: Q
1: Q(s=0)← Q(l−1).
2: for s←{1, 2, . . . , S} do
3: Calculate EUA V according to equations (30), (31),
and (32).
4: Obtain the optimum Q(s) by solving the convex
problem (P8.1) via convex optimization tools based on
Q(s−1).
5: if the objective O in (P8.1) converges then
6: Break
7: end if
8: end for
Let P ={pn,i|∀n, i} denote the slack variable set. There-
fore, the sub-problem (P8) can be reformulated as a convex
form:
(P8.1) : min
{Q,P}
O = G1 + ϕG2 + ψ
NX
n=1
IX
i=1

f In,i(Tn,i(s−1))
− ∂f In,i
∂Tn,i(s−1)
 
Tn,i− Tn,i(s−1)− ψ NX
n=1
IX
i=1
log2

epn,i
 IX
ˆi=1
ˆi̸=i
ehn,iwCn,ˆi2 + MX
m=1
ehn,iwSn,m2 + σ2 (46a)
s.t. (33c), (33d), (33e), (33f ), (33g), (45). (46b)
It can be obtained in polynomial time via standard convex
optimization tools. The pseudocode of UA V trajectory plan-
ning for sub-problem (P8) is shown in Algorithm 3.
Algorithm 4 Pseudocode of Joint Transmit Beamforming and
UA V Trajectory Design for Communication Enhancement and
Radar Probing Task Based on BCD Algorithm
Input: InP2, InP3
Output: W C, W S, Q
1: Initialize W C(0), W S(0) and Q(0).
2: for l←{1, 2, . . . , L} do
3: Fix Q(l−1) and compute optimal W C(l) and W S(l)
based on Algorithm 2. ▷ Beamforming
4: Fix W C(l) and W S(l) and compute optimal Q(l)
based on Algorithm 3. ▷ UA V trajectory
5: if the objective O in (P6) converges then
6: Break
7: end if
8: end for
D. Block Gradient Descent Algorithm for Joint Transmit
Beamforming and UAV Trajectory Design
The BCD algorithm is an iterative optimization algorithm
when the objective function is decomposed into several blocks
of variables. Here, the objective is decomposed into two
blocks, one with the variable precoders W C and W S, and the
other with the variable UA V trajectory Q. In each iteration,
BCD optimizes one block of variables while keeping the others
fixed. The pseudocode of joint transmit beamforming and UA V
trajectory design is shown in Algorithm 4.
V. E XPERIMENT FOR LARGE -SCALE REGIONAL RADAR
PROBING AND COMMUNICATION TASK
In this section, we will discuss four topics: a) Is the joint
transmit beamforming design feasible for large-scale regional
radar probing and communication tasks? b) What is the influ-
ence of different communication requirements? c) Is the newly
introduced sensing precoder effective? d) What is the influence
of various system parameters?
O = G1 + ϕG2 + ψ
NX
n=1
IX
i=1
log2
 
1
 

qn− dCn,i

22 + zUn 2  IX
ˆi=1
ehn,iwCn,ˆi2 + MX
m=1
ehn,iwSn,m2 + σ2!
| {z }
f I=
NP
n=1
IP
i=1
f In,i
−ψ
NX
n=1
IX
i=1
log2
 
1
 

qn− dCn,i

22 + zUn 2  IX
ˆi=1
ˆi̸=i
ehn,iwCn,ˆi2 + MX
m=1
ehn,iwSn,m2 + σ2!
| {z }
f II=
NP
n=1
IP
i=1
f IIn,i
. (41)
∂f I
∂Tn,i
=−
 IX
ˆi=1
ehn,iwCn,ˆi2 + MX
m=1
ehn,iwSn,m2 ln(2)Tn,i2 1Tn,i  IXˆi=1 ehn,iwCn,ˆi2 + MXm=1 ehn,iwSn,m2 + σ2.
(43)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4479
TABLE I
SETTINGS OF SIMULATION PARAMETERS
Fig. 2. The illustrations of the transmit beam patterns and the
cross-correlation patterns in multiple probing sector scenarios. a) The ideal
TBP and the TBP by R, Rc, and Rs in two probing sector scenario. b) The
cross-correlation pattern by R in two probing sector scenario. c) The ideal
TBP and the TBP by R, Rc, and Rs in three probing sector scenario. d) The
cross-correlation pattern by R in three probing sector scenario.
A. Simulation Scenario Modeling
The large-scale regional radar probing and communication
task can be divided into multiple independent time-based
sub-tasks, with the UA V hovering at a specific location
and providing ISAC service during each sub-task. Therefore,
we verify the feasibility of the joint transmit beamforming
design under the sub-task scenarios. We consider two cases
with two and three probing sectors respectively. The central
directions and probing widths in the two-sector case are
[−30◦, 30◦] and [20◦, 20◦], and those in the three-sector case
are [−50◦, 0◦, 50◦] and [20◦, 20◦, 20◦], respectively. We use
the MATLAB CVX toolbox [23] to solve the proposed SQP
problem. The settings of simulation parameters in our simu-
lation experiments are listed in Table I.
B. Algorithm Feasibility and Trade-Offs Between
Dual Functions
Transmit beam pattern: Let Rc = W CW CH and Rs =
W SW SH denote the covariance precoder matrix of commu-
nication and sensing, respectively. The illustrations of the ideal
TBP and the TBP by joint R, only Rc and only Rs in two
and three probing sector scenarios are depicted in Fig. 2(a) and
Fig. 2(c), respectively. We can see from Fig. 2(a) and Fig. 2(c)
that the obtained TBP with joint R can basically accord with
Fig. 3. The illustrations of the transmit beam patterns by joint R under
different SINR thresholds in three probing sector scenario.
the ideal gate-shaped TBP, and they both have two or three
peaks corresponding to the probing sectors. It indicates that
the joint transmit beamforming is valid for probing sector
matching. In addition, the TBP obtained by joint R can better
approximate the ideal TBP in terms of the probing width and
phase compared with that obtained by only Rc. It means
that the newly introduced precoder Ws, or more precisely,
the matrix Rs indeed helps improve the sensing performance.
The utilization of Rs corrects poor sensing performance at
a small sacrifice of communication performance, thus the
sensing interference term can be almost eliminated.
Cross-correlation pattern: The illustrations of the
cross-correlation patterns in two and three probing sector
scenarios are depicted in Fig. 2(b) and Fig. 2(d), respectively.
The optimization tends to minimize the MSE of the CCP,
i.e., the second design guideline for sensing task, and thus
we can see that the value on (30 ◦,−30◦) in Fig. 2(b) and the
values on (50◦, 0◦), (50◦,−50◦) and (0◦,−50◦) in Fig. 2(d)
are all small enough, which is exactly in accord with our
expectation. Besides, the strong correlation is manifested in
the autocorrelation of the directions corresponding to the
peaks in TBP, as shown in (−30 ◦, 30◦) in Fig. 2(b) and
(−50◦, 0◦, 50◦) in Fig. 2(d).
Transmit beam pattern versus SINR threshold : The illustra-
tions of the transmit beam patterns by joint R under different
SINR thresholds in the three probing sector scenario are
depicted in Fig. 3. In the optimization process, we obtain the
optimal P Sen by the optimizer, and the optimal P Sen values are
1.99, 1.99, 1.98, 1.86, and 1.22 under the SINR thresholds
12 dB, 14 dB, 16 dB, 18 dB, and 20 dB, respectively.
We can see from Fig. 3 that as the SINR threshold increases,
the difference between the obtained TBP and the ideal TBP
becomes larger. As the SINR threshold increases, the peaks
of the obtained TBP gradually shift away from the ideal
central directions, and the probing width is also getting smaller
compared to the ideal value. There exists a trade-off between
communication and sensing, once the communication require-
ments are enhanced, the sensing performance deteriorates,
which is exactly in accordance with the experiment results.
MSE of PSM and MSE of CCP versus ϕ: To measure the
trade-off between the two sensing indicators, we depict the
illustrations of the MSE of PSM (sensing indicator G1) and
the MSE of CCP (sensing indicator G2) versus importance
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4480 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
Fig. 4. The illustrations of MSE of PSM and MSE of CCP versus ϕ.
parameter ϕ in Fig. 4. As ϕ increases, the MSE of CCP
decreases until it approaches zero, while that of PSM
increases. Moreover, the rate at which the MSE of CCP
decreases gradually diminishes, making further increases in
ϕ less meaningful. Therefore, we take ϕ = 1 to make
G2 approximately equal to zero in the experiments.
C. Effectiveness of Newly Introduced Sensing Precoder
Radar probing error, SINR values, and throughput versus
SINR threshold : In Fig. 2(a) and Fig. 2(c), the matrix Rs
indeed helps improve the sensing performance. To further
quantitatively analyze the effectiveness of the sensing precoder
W S, we depict the illustrations of the radar probing error, the
MSE of PSM, and the MSE of CCP versus SINR threshold in
three probing sector scenario in Fig. 5(a). Three conclusions
can be derived as follows.
First, the radar probing error, i.e., the objective function,
increases as the SINR threshold increases due to the trade-off
between communication and sensing. It is worth noting that
there exists a sudden increase in the value of the objective
function when the SINR threshold is high. When the SINR
requirements become strict, the TBP deformation is severe,
as depicted in Fig. 3. Then, the error between the obtained TBP
and the ideal one, i.e., the main component of the objective
function, will suddenly increase significantly. Besides, the
increased demands of communication imply a deterioration of
the integrated sensing performance (G 1 + G2), which cannot
account for changes in an individual sensing indicator (G 1 or
G2), such as the trend reversal for the MSE of CCP and the
SINR threshold of 19 dB.
Second, two sensing indicators in the objective, i.e., the
MSE of PSM and the MSE of CCP, by joint R are all
lower than those by only Rc, which manifests that the sensing
precoder contributes to the improvement of the sensing per-
formance. However, such improvement usually comes with a
small sacrifice in communication performance. In Fig.5(b), the
minimal SINR values by joint R and by only Rc both satisfy
their corresponding constraints and are almost identical except
for situation TH SINR = 10 dB. Therefore, with satisfactory
communication performance, the sensing performance can be
adequately enhanced by utilizing the sensing precoder.
Third, although the average SINR obtained by only W C is
significantly higher than that by joint R when THSINR = 10 dB
and THSINR = 14 dB, this increase is uncritical since the SINR
constraints only require that the SINR values of CUs are all
Fig. 5. The illustrations of errors and SINR values versus SINR threshold in
the three probing sector scenario. a) Radar probing error, MSE of PSM, and
MSE of CCP versus SINR threshold. b) The average SINR, minimal SINR,
and average throughput versus the SINR threshold.
higher than a given threshold. Thus, a solution that satisfies the
SINR constraint and has a higher sensing performance will be
a better choice for the designed joint transmit beamforming
proposed in problem (P1). Besides, there exists an overlap
between the curve by joint R and by only Rc. This is because
the optimization tends to just satisfy the constraints. Further-
more, except for SINR, we also consider another typical design
criterion/metric, say the throughput, depicted in Fig. 5(b).
Similar conclusions hold with throughput.
D. Influence of Different System Parameters
Radar probing error versus the number of users: To analyze
the impact of user size on beamforming, we depict the
illustrations of the radar probing error versus SINR threshold
under different numbers of users in the three probing sector
scenario in Fig. 6. It can be seen from Fig. 6 that as the
number of users increases, the radar probing error, i.e., the
MSE of PSM plus CCP, also increases. More number of users
means higher communication demands to be satisfied, which
will take up more power resources in the precoder. Hence, the
higher communication interferences attached to the precoder
will deteriorate the sensing performance. Furthermore, the rate
of deterioration of sensing performance also increases with
the number of CUs, which is reflected in the slopes of the
curves in Fig. 6. An increase in the number of CUs leads
to an increase in the size of the precoder matrices. Since
the total transmit power of each antenna remains constant,
the desired information-bearing signal distributed to each
CU will decrease. Thereafter, a higher degree of sensing
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4481
Fig. 6. The illustrations of the objective functions versus SINR threshold
under different number of users in the three probing sector scenario.
Fig. 7. The illustrations of radar probing error versus SINR threshold under
different antenna array numbers in the three probing sector scenario.
performance needs to be sacrificed to meet the same SINR
requirements.
Radar probing error versus antenna array number : Fur-
thermore, we study the influence of the antenna array number,
and the illustrations of the radar probing error versus SINR
threshold under different antenna array number settings in the
three probing sector scenario are depicted in Fig. 7. Here,
we take I = 3. It can be seen from Fig. 7 that the more the
number of antennas is, the smaller the radar probing error
is, and the higher the sensing performance. Both Rc and
Rs are M× M matrices. When M is larger, the size of
the optimization variables becomes larger, and the degree of
freedom of the optimization problem becomes higher, which
indicates that the optimization results will be more optimal,
but this also leads to an increase in the algorithmic complexity.
Above all, the proposed joint transmit beamforming design
is valid for large-scale regional radar probing and communica-
tion tasks. In addition, the newly introduced sensing precoder
indeed greatly improves the integrated performance.
VI. E XPERIMENT FOR COMMUNICATION ENHANCEMENT
AND RADAR PROBING TASK
In this section, we first testify the feasibility of the joint
transmit beamforming and UA V trajectory design for com-
munication enhancement and radar probing tasks and the
effectiveness of sensing precoder from the aspects of the
convergence, UA V trajectory, and transmit beam pattern. Then,
we explore the trade-offs between communication and sensing
by adjusting the weight parameter ψ. Other system parameters
TABLE II
SETTINGS OF SIMULATION PARAMETERS
TABLE III
SETTINGS OF PARAMETERS WITH RESPECT TO THE UAV
ENERGY CONSUMPTION
are also discussed, including the UA V energy consumption,
CSI accuracy, and antenna array number.
A. Simulation Scenario Modeling and Algorithm Feasibility
In the communication enhancement and radar probing task,
we consider that the UA V takes off from a charging station,
located at qI = (40 m, 0m, 0m), flies along an optimized
trajectory, and hovers at some specific locations to provide
ISAC service. Ultimately, the UA V lands at a charging station,
located at qE = (220m, 0m, 0m). During the whole flight,
the UA V flies at a fixed altitude zUn = 50m, ∀n. For the
radar probing, we consider the three-sector case where the
central direction and probing width are [−50◦, 0◦, 50◦] and
[20◦, 20◦, 20◦], respectively. Part of the parameter settings is
listed in Table II. The other parameter settings are consistent
with those listed in TableI. The parameter settings with respect
to the UA V energy consumption are listed in Table III [9].
Convergence: To testify the algorithm feasibility, the
algorithm convergence under different weight parameter set-
tings is depicted in Fig. 8. Let L, S1l , and S2l denote the
maximum epoch of the BCD, the maximum iteration of
transmit beamforming design in the l-th epoch of BCD, and
that of UA V trajectory design in the l-th epoch of BCD.
In Fig. 8, the vertical axis represents the objective function O
in problem (P6), and the horizontal axis represents the iteration
number PLl=1(S1l + S2l ). Since the algorithm can converge
after a few epochs in BCD (only two epochs under these
settings), to more clearly illustrate the convergence process,
we also show the convergence of sub-problems (P7) and (P8)
in Fig. 8. We can conclude that all curves eventually converge.
Additionally, the larger the ψ, the lower the value it converges
to. This is because the magnitude of the average throughput
is greater than that of the radar probing error. Besides, the
oscillation is due to the transition from the optimization of
precoders to that of the UA V trajectory.
UAV trajectory: The illustrations of the optimal UA V trajec-
tory under different thresholds of UA V energy consumption are
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4482 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
Fig. 8. Algorithm convergence under different weight parameter settings.
Fig. 9. The illustrations of the optimal UA V trajectory under different
thresholds of UA V energy consumption.
depicted in Fig. 9. In Fig. 9, pink hollow circles represent the
CUs, pink hollow square represents the UA V initial location,
and the pink asterisk represents the UA V final location. We can
conclude that as the energy consumption threshold increases,
the UA V tends to fly a longer distance to get closer to CUs,
thereby improving communication performance.
Transmit beam pattern : The illustrations of transmit beam
patterns under different ψ are depicted in Fig. 10. It can
be concluded from Fig. 10 that when ψ is small (or for
pure MIMO radar), sensing is dominant in the optimization,
resulting in a TBP that is closer to the ideal TBP. When
ψ is large, communication is dominant in the optimization,
leading to a TBP that deviates more from the ideal TBP.
In addition, the communication and sensing precoders are
jointly optimized to enhance the matching of the probing
sector. When the communication precoder is insufficient to
achieve a satisfactory TBP, the sensing precoder compen-
sates for the TBP with minimal sacrifice to communication
performance.
B. Trade-Offs Between Dual Functions and Influence of
Different System Parameters
Radar probing error versus average throughput : We can
conclude from Fig. 11 that as the average throughput
increases (communication performance improves), radar prob-
ing error also increases (sensing performance deteriorates),
which reveals a fundamental trade-off between communication
and sensing that has been proved and widely discussed [39],
[40].
Fig. 10. The illustrations of transmit beam patterns of pure MIMO radar
and ISAC. a) Pure MIMO radar. b) ISAC, ψ = 0.01. c) ISAC, ψ = 0.1.
d) ISAC, ψ = 10.
Fig. 11. Radar probing error versus average throughput under different CSI
accuracy settings.
Imperfect Channel State Information: Then, we will discuss
the impact of channel imperfections on the proposed system,
which is one of the key issues in MIMO ISAC [41]. The
estimated channel between U and Ci can be expressed as
ˆhn,i = ξhn,i + p1− ξ2E, (47)
where ξ∈ [0, 1] represents the CSI accuracy; E∼CN (0, I)
represents the estimated error component. Radar probing error
versus average throughput under different CSI accuracy set-
tings is depicted in Fig. 11. We can see from Fig. 11 that
the trade-offs between dual functions always hold regardless
of the value of CSI accuracy. In addition, as the CSI accu-
racy decreases, the performance of both communication and
sensing gradually deviates from the results under the condition
of perfect CSI. However, when ξ = 0.9 (channel estimation
is relatively accurate), the performance of communication and
sensing is relatively close to the actual performance. It is worth
noting that the estimated error component is similar to the
NLoS component in the channel matrix. Hence, exploring the
influence of the error term also reflects that of the NLoS term
on the system performance.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4483
Fig. 12. Objective function values versus antenna array number under
different weight parameter settings. a) Radar probing error. b) Average
throughput.
Radar probing error and average throughput versus antenna
array number : To characterize the influence of the antenna
array number, we depict the radar probing error and average
throughput versus antenna array number under different weight
parameter settings in Fig. 12(a) and Fig. 12(b), respectively.
It can be seen from Fig. 12 that as the number of anten-
nas increases, both sensing and communication performance
improve, which is consistent with the results in Fig. 7.
Moreover, as ψ increases, the importance of communica-
tion performance in the optimization increases, and thus the
sensing performance deteriorates while the communication
performance improves.
Above all, the proposed joint transmit beamforming and
UA V trajectory design are valid for communication enhance-
ment and radar probing tasks. In addition, there exists a
fundamental trade-off between the dual functions by adjusting
the weight parameter in the optimization.
VII. C ONCLUSION
Joint transmit beamforming and UA V trajectory design are
crucial issues in UA V-enabled ISAC systems. Existing works
barely consider radar probing tasks and neglect the benefits
of the newly introduced sensing precoder. In this paper,
we first design both communication and sensing precoders for
large-scale regional radar probing and communication tasks.
Experiments are conducted for an independent time-based
sub-task with a quasi-static UA V , and the results testify the
correctness of the proposed algorithm and the effectiveness
of the newly introduced sensing precoder. Then, we also take
the mobility of the UA V into consideration where the transmit
beamforming and UA V trajectory are jointly designed for com-
munication enhancement and radar probing tasks. Experiment
results demonstrate the proposed algorithm is valid, and there
exists a fundamental trade-off between the dual functions by
adjusting the weight parameters of the two objectives. Also,
other system parameters are analyzed, including the antenna
array number, maximum UA V energy consumption, and CSI
accuracy. For future work, we will analyze the impact of the
Doppler shift on the performance of the UA V-enabled ISAC
system. Besides, we will quantitatively measure the impact
of the NLoS channel components on system performance by
considering the expectation of signal amplitude.
APPENDIX
In this appendix, we will prove that the solution
Rn, Rn,1, . . . ,Rn,I
	
is a global optimum to problem (P2).
First, since Rn = ˆRn, the constraints (21b) and (21e) hold for
Rn. It is clear that the Rn,1, . . . ,Rn,I are positive semidefi-
nite, and thus the constraints (21d) hold for Rn,1, . . . ,Rn,I.
Next, for an arbitrary vector v∈ CM , we have
vH

ˆRn,i− Rn,i

v = vH ˆRn,iv−
vH ˆRn,ihn,i2
hiH ˆRn,ihn,i . (48)
According to the Cauchy-Schwarz inequality, we have

hn,iH ˆRn,ihn,i
 
vH ˆRn,iv≥ vH ˆRn,ihn,i2 . (49)
Hence, for arbitrary v∈ CM , vH

ˆRn,i− Rn,i

v≥ 0 and
ˆRn,i− Rn,i∈S +M will always hold. Thereafter, it holds that
Rn−
IX
i=1
Rn,i = ˆRn−
IX
i=1
ˆRn,i
+
IX
i=1

ˆRn,i− Rn,i

∈S +M . (50)
Thus, the constraints (21c) hold for Rn, Rn,1, . . . ,Rn,I.
Then, we have
hn,iH Rn,ihn,i = hn,iH wCn,iwCn,iH hn,i
= hn,iH ˆRn,ihn,i. (51)
We can conclude that

1 + 1THSINR

hn,iH Rn,ihn,i
=

1 + 1THSINR

hn,iH ˆRn,ihn,i≥
hn,iH ˆRnhn,i + σ2 = hn,iH Rnhn,i + σ2, (52)
and thus the constraints (21f) hold for Rn, Rn,1, . . . ,Rn,I.
Therefore, the solution

Rn, Rn,1, . . . ,Rn,I
	
is a global
optimum of problem (P4).
Furthermore, it can be concluded that Rn,1, . . . ,Rn,I all
satisfy the rank-one constraints (21g), and thus the solution
Rn, Rn,1, . . . ,Rn,I
	
is also the optimal for problem (P3).
It is worth noting that the solution to the relaxed problem (P4)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

4484 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 73, NO. 6, JUNE 2025
also solves the original problem (P3), and hence the relaxation
can be considered tight.
To further obtain the optimal solution of the problem (P2),
we have
W
C
n =

wCn,1 wCn,2 . . . wCn,I  , (53)
W
S
nW
S
n
H
= Rn−
IX
i=1
Rn,i. (54)
The sensing precoder W
S
n can be then calculated based on the
Cholesky decomposition [42]. Above all, solution

W
C
n, W
S
n
	
is an optimal solution to problem (P2).
REFERENCES
[1] A. Bazzi and M. Chafii, “On outage-based beamforming design for
dual-functional radar-communication 6G systems,” IEEE Trans. Wireless
Commun., vol. 22, no. 8, pp. 5598–5612, Aug. 2023.
[2] J. A. Zhang et al., “An overview of signal processing techniques for joint
communication and radar sensing,” IEEE J. Sel. Topics Signal Process.,
vol. 15, no. 6, pp. 1295–1315, Nov. 2021.
[3] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[4] U. Demirhan and A. Alkhateeb, “Integrated sensing and communication
for 6G: Ten key machine learning roles,” IEEE Commun. Mag., vol. 61,
no. 5, pp. 113–119, May 2023.
[5] H. Zhang et al., “Intelligent channel prediction and power adaptation
in LEO constellation for 6G,” IEEE Netw., vol. 37, no. 2, pp. 110–117,
Mar./Apr. 2023.
[6] H. Zhang, L. Feng, X. Liu, K. Long, and G. K. Karagiannidis, “User
scheduling and task offloading in multi-tier computing 6G vehicular
network,” IEEE J. Sel. Areas Commun., vol. 41, no. 2, pp. 446–456,
Feb. 2023.
[7] K. Meng et al., “UA V-enabled integrated sensing and communication:
Opportunities and challenges,” IEEE Wireless Commun., vol. 31, no. 2,
pp. 1–9, Apr. 2023.
[8] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets integrated
sensing and communication: Challenges and future directions,” IEEE
Commun. Mag., vol. 61, no. 5, pp. 62–67, May 2023.
[9] Y . Liu, W. Huangfu, H. Zhou, H. Zhang, J. Liu, and K. Long, “Fair
and energy-efficient coverage optimization for UA V placement prob-
lem in the cellular network,” IEEE Trans. Commun., vol. 70, no. 6,
pp. 4222–4235, Jun. 2022.
[10] H. Zhang, H. Wang, Y . Li, K. Long, and V . C. Leung, “Toward intelligent
resource allocation on task-oriented semantic communication,” IEEE
Wireless Commun., vol. 30, no. 3, pp. 70–77, Jun. 2023.
[11] A. Liu et al., “A survey on fundamental limits of integrated sensing
and communication,” IEEE Commun. Surveys Tuts., vol. 24, no. 2,
pp. 994–1034, 2nd Quart., 2022.
[12] Y . Xu, T. Zhang, Y . Liu, and D. Yang, “UA V-enabled integrated sens-
ing, computing, and communication: A fundamental trade-off,” IEEE
Wireless Commun. Lett., vol. 12, no. 5, pp. 843–847, May 2023.
[13] L. Lu, G. Y . Li, A. L. Swindlehurst, A. Ashikhmin, and R. Zhang,
“An overview of massive MIMO: Benefits and challenges,” IEEE J. Sel.
Topics Signal Process., vol. 8, no. 5, pp. 742–758, Oct. 2014.
[14] F. Marini and B. Walczak, “Particle swarm optimization (PSO). A tuto-
rial,” Chemometric Intell. Lab. Syst., vol. 149, pp. 153–165, Dec. 2015.
[15] S. Katoch, S. S. Chauhan, and V . Kumar, “A review on genetic algorithm:
Past, present, and future,” Multimedia Tools Appl., vol. 80, no. 5,
pp. 8091–8126, Feb. 2021.
[16] R. A. Rutenbar, “Simulated annealing algorithms: An overview,” IEEE
Circuits Devices Mag., vol. 5, no. 1, pp. 19–26, Jan. 1989.
[17] S. Ruder, “An overview of gradient descent optimization algorithms,”
2016, arXiv:1609.04747.
[18] D. R. Fuhrmann and G. San Antonio, “Transmit beamforming for MIMO
radar systems using partial signal correlation,” in Proc. 38th Asilomar
Conf. Signals, Syst. Comput., vol. 1, Pacific Grove, CA, USA, 2004,
pp. 295–299.
[19] K. Arulkumaran, M. P. Deisenroth, M. Brundage, and A. A. Bharath,
“Deep reinforcement learning: A brief survey,” IEEE Signal Process.
Mag., vol. 34, no. 6, pp. 26–38, Nov. 2017.
[20] S. Gong, L. Cui, B. Gu, B. Lyu, D. T. Hoang, and D. Niyato, “Hierar-
chical deep reinforcement learning for age-of-information minimization
in IRS-aided and wireless-powered wireless networks,” IEEE Trans.
Wireless Commun., vol. 22, no. 11, pp. 8114–8127, Mar. 2023.
[21] B. Li, T. Shi, W. Zhao, and N. Wang, “Reinforcement learning-
based intelligent reflecting surface assisted communications against
smart attackers,” IEEE Trans. Commun., vol. 70, no. 7, pp. 4771–4779,
Jul. 2022.
[22] C. Liu et al., “Learning-based predictive beamforming for integrated
sensing and communication in vehicular networks,” IEEE J. Sel. Areas
Commun., vol. 40, no. 8, pp. 2317–2334, Aug. 2022.
[23] S. Diamond and S. Boyd, “CVXPY: A Python-embedded modeling
language for convex optimization,” J. Mach. Learn. Res., vol. 17, no. 1,
pp. 2909–2913, 2016.
[24] L. Vandenberghe and S. Boyd, “Semidefinite programming,” SIAM Rev.,
vol. 38, pp. 49–95, Apr. 1996.
[25] K.-C. Toh, M. J. Todd, and R. H. Tütüncü, “On the implemen-
tation and usage of SDPT3—A MATLAB software package for
semidefinite-quadratic-linear programming, version 4.0,” in Handbook
Semidefinite, Conic Polynomial Optimization. New York, NY , USA:
Springer, Sep. 2011, pp. 715–754.
[26] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun., vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[27] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li, “Throughput
maximization for UA V-enabled integrated periodic sensing and commu-
nication,” IEEE Trans. Wireless Commun., vol. 22, no. 1, pp. 671–687,
Jan. 2023.
[28] K. Meng, Q. Wu, S. Ma, W. Chen, and T. Q. S. Quek, “UA V
trajectory and beamforming optimization for integrated periodic sensing
and communication,” IEEE Wireless Commun. Lett., vol. 11, no. 6,
pp. 1211–1215, Jun. 2022.
[29] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[30] Z. Lyu, G. Zhu, and J. Xu, “Joint trajectory and beamforming design
for UA V-enabled integrated sensing and communication,” inProc. IEEE
Int. Conf. Commun., May 2022, pp. 1593–1598.
[31] A. Khalili, A. Rezaei, D. Xu, and R. Schober, “Energy-aware
resource allocation and trajectory design for UA V-enabled ISAC,” 2023,
arXiv:2302.10124.
[32] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. Eldar,
“Joint transmit beamforming for multiuser MIMO communications and
MIMO radar,” IEEE Trans. Signal Process., vol. 68, pp. 3929–3944,
Jun. 2020.
[33] N. Dutta, H. K. D. Sarma, and Z. Polkowski, “Cluster based routing in
cognitive radio adhoc networks: Reconnoitering SINR and ETT impact
on clustering,” Comput. Commun., vol. 115, pp. 10–20, Jan. 2018.
[34] D. Luo, Z. Ye, B. Si, and J. Zhu, “Secure transmit beamforming for
radar-communication system without eavesdropper CSI,” IEEE Trans.
Veh. Technol., vol. 71, no. 9, pp. 9794–9804, Sep. 2022.
[35] P. Stoica, J. Li, and Y . Xie, “On probing signal design for MIMO
radar,” IEEE Trans. Signal Process., vol. 55, no. 8, pp. 4151–4161,
Aug. 2007.
[36] J.-W. Nie and Y .-X. Yuan, “A predictor–corrector algorithm for QSDP
combining Dikin-type and Newton centering steps,” Annu. Oper. Res.,
vol. 103, pp. 115–133, Mar. 2001.
[37] K.-C. Toh, “An inexact primal–dual path following algorithm for con-
vex quadratic SDP,” Math. Program., vol. 112, no. 1, pp. 221–254,
Jul. 2007.
[38] K. Shen and W. Yu, “Fractional programming for communication
systems—Part I: Power control and beamforming,” IEEE Trans. Signal
Process., vol. 66, no. 10, pp. 2616–2630, May 2018.
[39] F. Liu, Y . Xiong, K. Wan, T. X. Han, and G. Caire, “Deterministic-
random tradeoff of integrated sensing and communications in Gaussian
channels: A rate-distortion perspective,” in Proc. IEEE Int. Symp. Inf.
Theory (ISIT), Jun. 2023, pp. 2326–2331.
[40] Y . Xiong, F. Liu, Y . Cui, W. Yuan, T. X. Han, and G. Caire, “On
the fundamental tradeoff of integrated sensing and communications
under Gaussian channels,” IEEE Trans. Inf. Theory, vol. 69, no. 9,
pp. 5723–5751, Sep. 2023.
[41] Y . Liu, T. Huang, F. Liu, D. Ma, W. Huangfu, and Y . C. Eldar, “Next-
generation multiple access for integrated sensing and communications,”
Proc. IEEE, pp. 1–30, Sep. 2024, doi: 10.1109/JPROC.2024.3449807.
[42] X.-D. Zhang, Matrix analysis and Applications. Cambridge, U.K.:
Cambridge Univ. Press, 2017.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply. 

LIU et al.: RADAR PROBING OPTIMIZATION FOR JOINT BEAMFORMING AND UA V TRAJECTORY DESIGN 4485
Yaxi Liu (Member, IEEE) received the B.S. and
Ph.D. degrees in communication engineering from
the School of Computer and Communication Engi-
neering, University of Science and Technology
Beijing, Beijing, China, in 2016 and 2021, respec-
tively. From 2021 to 2023, she was with the
University of Science and Technology Beijing, as a
Post-Doctoral Researcher. She is currently a Lecturer
with the University of Science and Technology
Beijing. Her research interests include wireless
communications, integrated sensing and communi-
cations, network optimization, and planning. She received the 2018 IEEE
WCSP Best Paper Award.
Wencan Mao (Member, IEEE) received the B.E.
degree in vehicle engineering from Wuhan Univer-
sity of Technology, Wuhan, China, in 2017, the
M.S. degree in mechanical engineering from Aalto
University, Espoo, Finland, in 2019, and the Ph.D.
degree from the Department of Information and
Communications Engineering, Aalto University. She
is currently a Post-Doctoral Researcher with the
National Institute of Informatics, Tokyo, Japan. Her
current research interests include edge computing,
smart and sustainable cities, integrated sensing and
communications, and the Internet of Things.
Boxin He (Graduate Student Member, IEEE) is
currently pursuing the Ph.D. degree in information
and communication engineering with the School of
Computer and Communication Engineering, Univer-
sity of Science and Technology Beijing (USTB).
His current research interests include the inte-
gration of sensing and communication, millimetre
wave communications, and multiple-input–multiple-
output technologies.
Wei Huangfu (Member, IEEE) received the M.S.
and Ph.D. degrees in electronic engineering from
Tsinghua University, Beijing, China, in 1998 and
2001, respectively. He is currently a Professor
with the School of Computer and Communication
Engineering, University of Science and Technology
Beijing (USTB). His main research interests include
statistical signal processing, cooperative communi-
cations, the Internet of Things, and wireless sensor
networks.
Tianyao Huang (Member, IEEE) received the
B.S. degree in telecommunication engineering from
Harbin Institute of Technology, Heilongjiang, China,
in 2009, and the Ph.D. degree in electronics engi-
neering from Tsinghua University, Beijing, China,
in 2014. He is currently a Professor with the School
of Computer and Communication Engineering, Uni-
versity of Science and Technology Beijing, Beijing,
China. From 2017 to 2023, he was with the Intelli-
gence Sensing Laboratory, Department of Electronic
Engineering, Tsinghua University, as an Assistant
Professor. From 2014 to 2017, he was a Radar Researcher with Aviation
Industry Corporation of China (A VIC). His current research interests include
signal processing, compressed sensing, and joint radar communications system
design.
Haijun Zhang (Fellow, IEEE) was a Post-Doctoral
Research Fellow with the Department of Electri-
cal and Computer Engineering, The University of
British Columbia (UBC), Canada. He is currently
a Full Professor with the University of Science
and Technology Beijing, China. He received the
IEEE ComSoc Young Author Best Paper Award
in 2017, IEEE CSIM Technical Committee Best
Journal Paper Award in 2018, and the IEEE ComSoc
Asia-Pacific Best Young Researcher Award in 2019.
He serves/served as the Track Co-Chair for VTC Fall
2022 and WCNC 2020/2021, the Symposium Chair for GLOBECOM’19,
the TPC Co-Chair for INFOCOM 2018 Workshop on Integrating Edge
Computing, Caching, and Offloading in Next Generation Networks, and the
General Co-Chair for GameNets’16. He serves/served as an Editor at Large
for IEEE T RANSACTIONS ON COMMUNICATIONS and an Editor for IEEE
TRANSACTIONS ON WIRELESS COMMUNICATIONS . He is a Distinguished
Lecturer of IEEE.
Keping Long (Senior Member, IEEE) received the
M.S. and Ph.D. degrees from the University of Elec-
tronic Science and Technology of China, Chengdu,
in 1995 and 1998, respectively. From September
1998 to August 2000, he was a Post-Doctoral
Research Fellow with the National Laboratory
of Switching Technology and Telecommunication
Networks, Beijing University of Posts and Telecom-
munications (BUPT), China. From September
2000 to June 2001, he was an Associate Professor
with BUPT. From July 2001 to November 2002,
he was a Research Fellow with the ARC Special Research Centre for Ultra
Broadband Information Networks (CUBIN), The University of Melbourne,
Australia. He is currently a Professor with the School of Computer and
Communication Engineering, University of Science and Technology Beijing.
He has published more than 200 articles, 20 keynote speeches, and invited
talks at international and local conferences. His research interests include
optical internet technology, new generation network technology, wireless
information networks, value-added services, and secure technology of net-
works. He received the National Science Fund for Distinguished Young
Scholars of China in 2007 and was selected as the Chang Jiang Scholars
Program Professor of China in 2008. He is a member of the Editorial
Committees of Science in China Series F and China Communications.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:23 UTC from IEEE Xplore.  Restrictions apply.