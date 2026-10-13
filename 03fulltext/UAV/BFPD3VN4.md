---
title: "ISAC from the Sky UAV Trajectory Design for Joint Communication and Target Localization"
zotero_key: "BFPD3VN4"
pdf_key: "ZWFR6M4M"
doi: "10.1109/twc.2024.3396571"
collection: "UAV"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# ISAC from the Sky UAV Trajectory Design for Joint Communication and Target Localization — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
ISAC from the Sky: UA V Trajectory Design for
Joint Communication and Target Localization
Xiaoye Jing, Graduate Student Member , IEEE, Fan Liu, Senior Member , IEEE, Christos Masouros, Fellow, IEEE,
Yong Zeng, Senior Member , IEEE
Abstract—Integrated sensing and communication (ISAC) is
studied in the airborne domain, where Unmanned Aerial Vehicles
(UA Vs) act as communication base stations and radars simulta-
neously. The UA V transmits signals to users while leveraging
these signals to localize targets. This research focuses on jointly
improving communication and sensing (C&S) performances by
designing the UA V trajectory and allocating user’s bandwidth.
Since UA V’s sustainability is determined by its onboard battery,
energy supply is considered as a constraint in the trajectory
design. Communication performance is evaluated by total trans-
mitted data, while sensing performance is assessed through
Cram´er-Rao bound (CRB). A tradeoff objective is formulated
with normalization. To achieve a flexible tradeoff between C&S,
the trajectory design is formulated as a weighted sum optimiza-
tion problem. To improve the formulation accuracy of trajectory
design, a multi-stage trajectory design (MSTD) is proposed.
While the resultant design problem is difficult to solve directly, an
iterative algorithm is developed to obtain a local optimal solution
of UA V trajectory. Finally, numerical results are presented to
show UA V trajectories determined by the tradeoff between C&S
and the energy supply. Benefits of ISAC-based UA V scenario are
highlighted by comparing the single-functional UA V scenarios.
Index Terms—Unmanned aerial vehicles, Cram ´er-Rao bound,
nonconvex optimization, integrated sensing and communication
I. I NTRODUCTION
A. Background and Motivation
N
EXT-generation wireless networks are expected to go be-
yond traditional communication services, offering highly
accurate and robust sensing, including localization, tracking
and navigation [1], [2]. In conventional wireless systems,
communication and sensing (C&S) functionalities are typi-
cally treated as separated objectives, leading to an inefficient
resource utilization. To resolve such issues, designing C&S
systems in a joint manner enabling the sharing of hardware
This paper has received funding from the European Union’s Horizon 2020
research and innovation programme under the Marie Sklodowska-Curie grant
agreement No 812991. This work was supported by the National Natural
Science Foundation of China under Grant 62071114. This work was supported
in part by the Guangdong Province “Pearl River” Young Talent Support
Program under Grant 2021QN02X128, and in part by the Shenzhen Science
and Technology Program under Grant RCBS20210609103227018 and Grant
20220815100308002. (Corresponding author: Fan Liu.)
X. Jing is with the Department of Electronic and Electrical Engi-
neering, University College London, London WC1E 7JE, U.K. (e-mail:
x.jing@ucl.ac.uk). F. Liu is with the Department of Electronic and Electrical
Engineering, Southern University of Science and Technology, Shenzhen
518055, China (e-mail: liuf6@sustech.edu.cn). C. Masouros is with the
Department of Electronic and Electrical Engineering, University College
London, London WC1E 7JE, U.K. (e-mail: chris.masouros@ieee.org). Y . Zeng
is with the National Mobile Communications Research Laboratory, Southeast
University, Nanjing 210096, China, and also with the Purple Mountain
Laboratories, Nanjing 211111, China (e-mail: yong zeng@seu.edu.cn).
and signals, is a promising solution to reduce the cost and
improve spectral efficiency, leading to the emergence of in-
tegrated sensing and communication (ISAC) technology [1]–
[3]. As a promising technology for future 6G, ISAC has been
extensively investigated across wireless applications, such as
Wi-Fi based indoor localization and cognitive recognition [4],
cooperative C&S in unmanned aerial vehicle (UA V) networks
[5] and joint vehicle tracking and communication [6].
UA V-based networks are vital components of future wireless
systems, providing flexible topology and offering on-demand
connectivity, particularly in emergency scenarios [7]. However,
the separate deployment of C&S systems inevitably incurs
a substantial payload carried by UA Vs, thereby resulting in
performance degradation in terms of UA V maneuverability.
To mitigate these challenges, ISAC is envisaged as an avail-
able solution to minimize UA V payload and reuse hardware
between C&S [8]. Furthermore, a common waveform can be
leveraged for both functionalities, which significantly enhances
spectral/energy efficiency of UA V networks. In the subsequent
sections, we provide a concise overview of ISAC technology
and its applications in UA V-based communication and sensing.
B. ISAC Technology
Recently, there has been a dramatically growing research
interest in ISAC. The initial research effort was on estab-
lishing an appropriate integration framework, from sensing-
communication coexistence, enabling the harmonic cohabita-
tion of two systems in the same frequency band without inter-
ference [1], to dual-functional radar-communication (DFRC)
system, which designs joint systems capable of simultaneously
performing C&S [1], [9]. State-of-the-art DFRC research
has witnessed the development of sophisticated techniques,
including coding [10]–[12], waveform design [13]–[15] and
beamforming [6], etc., to facilitate the utilization of a common
signal for accomplishing dual tasks.
The performance evaluation of ISAC encompasses both
C&S aspects. Communication metrics are derived from infor-
mation theory, e.g., channel capacity and symbol error rate [1],
[9]. For sensing functionalities, estimation-theoretic metrics
like mean-square error (MSE) and Cram ´er-Rao Bound (CRB)
[1], [9] are employed. In some works, C&S performance
metrics could be possibly improved simultaneously. However,
in most cases, there exists fundamental tradeoffs between
C&S due to the shared utilization of wireless and hardware
resources, resulting in conflicting design objectives. Hence, it
is of particular importance to reveal such performance bounds
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

2
and to design bound-achieving strategies for ISAC systems.
One representative approach to beamforming proposed in [16],
focused on minimizing CRB for target sensing while ensuring
Quality of Service (QoS) for downlink communications. This
specific tradeoff of waveform design serves as the foundation
of our trajectory design work.
C. UA V Research on C&S
Unlike conventional cellular networks where base stations
(BSs) are fixed on the ground, UA V offers additional de-
sign flexibility in terms of positioning optimization [17].
By optimizing the UA V position and its flying status, UA V-
based communication/sensing platform provides an additional
degree of freedom to enhance the propagation channel for
communication users (CUs) and sensed targets (STs), resulting
in improvements in communication/sensing services.
UA V position design can be broadly divided into static
deployment and moving trajectory. Static UA V deployment in
communication determines UA V hovering positions in space to
enhance performances. Single-UA V optimizes communication
coverage by determining its altitude [18]–[20]. Multi-UA V
exploits topology and cluster for improving coverage and
energy efficiency [21]–[23]. Static UA V deployment in sensing
typically involves at least three UA Vs, where everyone senses
distances/angles between itself and targets. Based on different
measurements, the target location can be determined [24]. In
contrast to static UA Vs, moving UA Vs can fly closer to points
and link directions can evolve with time, thereby improving
channel diversity and benefiting both C&S. Since UA V flying
time is constrained by its battery capacity, energy-efficient de-
sign has received considerable attentions in communications.
Energy efficiency is considered in designing trajectories while
ensuring satisfactory communications [25]–[27]. In terms of
sensing, trajectory design for single-UA V was investigated
in [28], which included a three-dimensional model with a
closed-form solution of UA V path. Angle-of-arrival (AoA)
measurement was applied to multi-UA V trajectories in [29]
and [30].
Existing research also explores the integration of C&S in
UA V systems. A power allocation was proposed for a static
multi-UA V network to maximize a utility performance for
C&S in [5], where UA V deployment was determined using
a clustering approach. In [31] and [32], a single-UA V senses
multiple targets and transmits data to a ground BS for data
updating. The goal was to minimize the maximum average
peak age of information (PAoI) from targets by jointly opti-
mizing UA V trajectory, task scheduling, time allocation and
power allocation. A periodic ISAC framework was proposed
in [33], where sensing is periodically performed alongside
continuous communication. The authors aimed to maximize
communication performance by optimizing sensing instant,
UA V trajectory and beamforming. Authors in [34] considered
a scenario where one UA V sends communication signals to
multiple users and senses potential targets in specific areas.
The objective was to maximize the throughput by jointly
optimizing moving UA V positions and transmit beamform-
ing, subject to sensing requirements and transmission power
constraints. In the aforementioned works on ISAC in mov-
ing UA Vs, the emphasis was on improving communication
performance while adhering to the sensing beampattern gain
requirements [33], [34]. However, although beampattern gain
is a sensing performance metric, it does not accurately capture
the specific sensing performance, such as the estimation error
of target location. This serves as a catalyst for our study,
where we focus on CRB which directly indicates estimation
performance [5], [35].
D. Contributions
In this paper, we focus on an ISAC-based UA V scenario,
aiming to simultaneously provide C&S functionalities using
the shared platform and signal resource. By utilizing a com-
mon signal, both communication with CUs and sensing for
STs are achieved. The UA V provides downlink transmissions
for ground CUs using the pre-designed signal. To ensure the
data transmitted between UA V and CUs kept secret from STs,
secret key generation scheme can be adopted in the PHY layer
[36], [37]. In the meantime, the UA V transmits the downlink
signal to STs and receives echoes reflected by these STs, based
on which, ST locations are estimated.
We design UA V trajectory, including UA V’s flying way-
points, hovering points (HPs) and flying velocities, and al-
locate bandwidth to CUs. Our objective is to jointly improve
communication capacity for CUs and localization accuracy for
STs. It is worth noting that existing works [33], [34], have
only considered the UA V energy consumption related to sig-
nal transmission, neglecting the significant energy consumed
during UA V’s flying [26], [38]. Therefore, by considering the
UA V onboard battery capacity, we impose an energy constraint
in our ISAC scenario.
The main contributions of this paper are as follows:
• We build a performance optimization problem to jointly
increase the total transmitted data for CUs and decrease
the CRB for STs through UA V trajectory design, band-
width allocation and ST estimations. We consider the
C&S performance tradeoff with a weighting factor and
formulate a weighted sum optimization function. By
tuning the weighting factor, the UA V trajectory design
can flexibly adjust its priority between C&S.
• Since ST locations are initially unknown, to construct an
accurate problem formulation of UA V trajectory design,
we propose a multi-stage trajectory design (MSTD) ap-
proach to obtain more accurate ST locations in a gradual
manner, where the UA V trajectory design can be built
upon more accurate formulations.
• Solving the formulated optimization problem is chal-
lenging due to the nonconvex objective function and
constraint. Therefore, we propose an iterative algorithm
for the formulated problem. Specifically, a gradient based
method is introduced to find the ascent direction of the
joint C&S performance in the objective function, so that
to obtain a local optimal solution of the UA V trajectory
design. Successive convex approximation (SCA) method
is then utilized to find the convex bound for the noncon-
vex part in the constraint.
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

3
Fig. 1: ISAC-based rotary-wing UA V scenario.
The remainder of this paper is organized as follows. Section
II introduces the system model and derives the performance
metrics for C&S. Section III formulates the UA V trajectory
design and bandwidth allocation problem. Section IV proposes
an iterative algorithm to address the formulated problem and
the ST’s coordinate estimation is developed. In Section V ,
the proposed approaches are evaluated with numerical results.
Finally, the paper is concluded in Section VI.
II. S YSTEM MODEL AND PERFORMANCE METRICS
In this section, we firstly describe the ISAC-based UA V
scenario and the proposed MSTD approach. We then elaborate
on performance metrics for C&S respectively.
A. Proposed Scenario, MSTD Approach and UA V Trajectory
Model
As shown in Fig. 1, we consider an ISAC-based UA V
scenario comprising 1) a single rotary-wing UA V equipped
with one transmit antenna and one receive antenna, 2) M
CUs, who receive signals from the UA V , and 3) K STs
localized by the UA V . We consider a rectangular area on the
ground with a dimension Lx by Ly. One charging base is
located at [xB, yB]T ∈ R2 for the UA V to charge its battery
before departure. The UA V is dispatched from [xB, yB]T and
then flies at a constant altitude H. The m-th CU’s location
(m = 1, 2, ..., M) is denoted by a two-dimensional coordinate
[xcm, ycm]T ∈ R2. [xcm, ycm]T (m = 1 , 2, ..., M) are known a
priori via Global Navigation Satellite System. Locations of
STs are unknown, which are estimated by the UA V sensing
function. We denote the k-th ST’s location ( k = 1 , 2, ..., K)
is a two-dimensional coordinate [xtk, ytk]T ∈ R2. We denote it
in a vector as uk = [xtk, ytk]T for later use.
The UA V trajectory design and bandwidth allocation are
determined by the distribution of CUs and STs. Since uk
(k = 1 , 2, ..., K) are initially unknown, trajectory design
should be dependent on estimates of ST locations, which
are denoted by buk = [ bxtk, bytk]T (k = 1 , 2, ..., K). Note that
there may exist a large gap between uk and buk, leading to
a worse solution of UA V trajectory due to the inaccurate
formulation. In order to progressively improve the accuracy of
trajectory design formulation, we propose a MSTD approach.
This approach splits the UA V trajectory design problem and
ST location estimation into several stages, allowing for a
gradual refinement of ST estimates and UA V trajectory.
Next, we elaborate details about the MSTD approach.
Before UA V’s departure, we acquire a coarse estimate of uk
(k = 1 , ..., K), denoted by buk,0 =
h
bxtk,0, bytk,0
iT
, via three
sensing points near [xB, yB]T . Then, the UA V flying process
enters to the 1st stage. The UA V trajectory design for the
1st stage is based on [xcm, ycm]T (m = 1 , ..., M) and buk,0
(k = 1 , ..., K). After the trajectory design, the UA V starts
its flying from [xB, yB]T following the 1st stage’s trajectory
designed above and continuously broadcasts the downlink
signal containing valuable information to CUs. We allocate
bandwidth to ensure that all CUs can receive data without
interference. During the flying, UA V selects some positions in
the trajectory as HPs to pause and perform sensing. Specif-
ically, at one HP, the UA V simultaneously broadcasts the
downlink signal to both CUs and STs. Subsequently, echoes
of this signal are reflected by all STs and received at that HP
by the UA V . STs reflect the signal across the whole band. By
observing the propagation delays between the downlink signal
and its echoes, the distances between that HP and all STs are
measured. At the end of the 1st stage, distance measurements
across all HPs regarding the k-th ST ( k = 1 , ..., K) are
combined via estimation method, e.g., maximum likelihood
estimation (MLE), to update a location estimate denoted as
buk,1 =
h
bxtk,1, bytk,1
iT
.
Now, the UA V flying process updates to the 2nd stage.
Before the UA V continues its flying in the 2nd stage, the
UA V trajectory for the 2nd stage should be designed. The
formulation of UA V trajectory design for the 2nd stage is
based on [xcm, ycm]T (m = 1, ..., M) and buk,1 (k = 1, ..., K).
The UA V starts its 2nd stage flying from the final position of
the 1st stage. The C&S process is same with the 1st stage.
Once the UA V completes its 2nd stage’s flying, all distance
measurements across the first HP in the 1st stage to the final
HP in the 2nd stage regarding the k-th ST ( k = 1, ..., K) are
combined to update an estimate buk,2 =
h
bxtk,2, bytk,2
iT
.
The MSTD approach is repeated by estimating ST locations,
designing UA V trajectory and performing C&S functions.
As shown in Fig. 2, we designate j (where j = 1, 2, ...) as
the stage index. At the end of the j-th stage, the distance
measurements across the first HP in the 1st stage to the final
HP in the j-th stage regarding the k-th ST ( k = 1, ..., K) are
combined to estimate the ST location. The estimation after
the j-th stage’s flying is denoted by buk,j =
h
bxtk,j , bytk,j
iT
.
The multi-stage flying continues until UA V battery capacity,
denoted as Etot, runs out.
Since a UA V trajectory is characterized by geographical
positions together with the flying velocity corresponding to
the UA V path, the UA V trajectory is a continuous-time model.
Consequently, the trajectory design is a continuous-time op-
timization which is difficult to solve directly. Therefore, in
each stage, we seek an approximate solution of the continuous-
time optimization through discretizing the UA V’s flying time
by a sequence of time slots. In the j-th stage, the number
of time slots is N fj . The UA V flying duration in each slot is
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

4
(a) The illustration of MSTD approach
 (b) The UA V multi-stage trajectory
Fig. 2: The proposed MSTD approach for UA V trajectory design.
Tf, which is constant and pre-determined. Subsequently, the
UA V continuous path can be approximated into a sequence
of line segments aligned with time slots. We then employ
N fj waypoints to denote these lines. Specifically, the n-th
waypoint (n = 1, 2, ..., Nfj ), denoted by sn,j ∈ R2, represents
the final position of the n-th line segment. And then, the UA V
flies following the (n + 1)-th line segment with a duration
Tf to the (n + 1)-th waypoint, denoted by sn+1,j ∈ R2.
We concatenate all waypoints in the j-th stage in a matrix
Sj =
h
s1,j, ...,sN fj ,j
i
∈ R2×N fj .
As aforementioned, there are some HPs in each stage for
UA V to hover and perform sensing. Therefore, we select some
points from Sj as the HPs. Specifically, after the UA V flies
over µ line segments ( µ is a given integer), it hovers at the
final position of these line segments with a duration Th to
perform sensing. The number of HPs in the j-th stage is N hj ,
so that N hj = floor

N fj
µ

. We use index {γ, j} to denote the
γ-th HP in the j-th stage as

xhγ,j , yhγ,j T = sµγ,j , γ = 1, 2, ..., Nhj . (1)
HPs in the j-th stage are denoted by vectors xhj =h
xh1,j, ..., xhN hj ,j
iT
and yhj = hyh1,j, ..., yhN hj ,jiT .
We assume that N fj (j = 1 , 2, ...) is pre-determined as a
constant Nstg. Since the energy consumption in one stage is
unknown before designing the trajectory in this stage, the num-
ber of stages is unknown. Similarly, the total flying duration
and distance are undetermined before UA V’s departure. In this
case, before we formulate the trajectory design problem for the
j-th stage, we need to calculate the UA V remaining energy.
The remaining energy is the available energy supporting UA V
trajectory in the j-th stage, denoted as Ej, equalling to Etot
minus total energy consumption from the 1st stage to the
(j − 1)-th stage. If Ej is insufficient to support a flying with
Nstg line segments, we designate the j-th stage as the ending
stage, which is denoted by index J. Then, the UA V calculates
the permissible number of line segments in the J-th stage
based on EJ, and denotes it by Nlst, so that N fJ = Nlst.
Meanwhile, there are N hJ = floor  Nlstµ  HPs in the ending
stage.
The velocity in a line segment is a constant, expressed as
vn,j =



sn,j −sn−1,j
Tf , n = 2, ..., Nfj , j = 1, ..., J,s1,j −sNstg ,j−1
Tf , n = 1, j = 2, ..., J,
s1,1−[xB,yB]T
Tf , n = 1, j = 1,
(2)
Matrix Vj =
h
v1,j, ...,vN fj ,j
i
∈ R2×N fj is used to represent
UA V velocities in the j-th stage.
It is important to note that there may exist reflections
from the ground, causing clutters to echoes. To tackle this
issue, we propose in the following a simple and efficient
echo association approach. Meanwhile, the following proposed
approach can also be used to distinguish echoes reflected by
different STs.
At the γ-th HP in the j-th stage, the UA V receives K echo
signals plus N cltγ,j signals caused by ground clutter. The time
delay measurements from all signals above is denoted by a set
eτ allγ,j = eτ all1,γ,j , ...,eτ alli,γ,j , ...,eτ allI,γ,j 	, comprising I = K + N cltγ,j
measurements. In the j-th stage, we can obtain the estimate of
the k-th ST through former stages, which is buk,j−1 presented
before, thus, given buk,j−1, the time delay of the echo from
the k-th ST at the γ-th HP can be predicted as bτk,γ,j . The
prediction bτk,γ,j can be obtained via prediction approaches
such as the Kalman filter [39]. Therefore, by using the
fact that time delay prediction bτk,γ,j and its corresponding
measurement eτk,γ,j should be “close” to each other, the UA V
can distinguish the echo reflected by the k-th ST from all
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

5
received signals. The index of the k-th ST’s echo in eτ allγ,j is
denoted as itk,γ,j . The UA V calculates the “distance” between
bτk,γ,j and each element in eτ allγ,j , and associates eτ alli,γ,j with the
prediction bτk,γ,j that yields the smallest “distance”, which can
be expressed in the form
itk,γ,j = arg mini=1,...,I 

eτ alli,γ,j − bτk,γ,j 

 , k = 1, 2, ..., K.(3)
By doing so, the UA V can update the location estimates using
the correct measurement with a high probability. Additionally,
by leveraging the strong similarity among the electromagnetic
responses from the ground, separating the ground reflections
from ST reflections equals to basically separating constant
from nonconstant valued signals across different HPs, which
can be accomplished by applying a proper spatial filter [40].
Following the MSTD approach, we will illustrate C&S
performance metrics used in the UA V trajectory design for-
mulation in each stage through the following subsections.
B. Communication Model
We assume that the propagation channel is dominated by the
light-of-sight (LoS) link [26]. The free-space path loss model
is applicable to C&S. Given the limitation in UA V velocity and
with the appropriate choice of Tf, the line segment between
two consecutive waypoints satisfies ∥sn−1,j − sn,j∥ ≪H.
Therefore, the transmission distance between the UA V and a
CU within one line segment remains nearly constant. Thus,
when UA V flies from sn−1,j to sn,j, a CU’s communication
rate is nearly unchanged. In this case, a CU’s communication
rate across the n-th line segment nearly equals to the rate at
the n-th waypoint.
Let dcm,n,j denotes the distance from the UA V at the n-th
waypoint to the m-th CU in the j-th stage as
dcm,n,j =
r
H 2 +



sn,j − [xcm, ycm]T 


2. (4)
Thus, the channel power gain from the UA V to the CU is
hm,n,j = α0dcm,n,j2 , (5)
where α0 = GT·Gc·λ2(4π)2 is the channel power at the reference
distance dcm,n,j = 1m. GT is the UA V transmit antenna gain.
Gc is the CU receive antenna gain and λ is the wavelength.
The signal-to-noise ratio (SNR) from the UA V to the CU can
be expressed as
SN Rcm,n,j = Pthm,n,jσ20 , (6)
where Pt is the transmitting power. σ2 is the noise power at
the receiver.
The m-th CU’s communication rate across the n-th line
segment in the j-th stage is
Rm,n,j = Bm,jlog2

1 + Pthm,n,j
σ20

, (7)
where Bm,j is the channel bandwidth allocated to the m-th
CU in the j-th stage and PMm=1 Bm,j ≤ B. We denote Bj =
[B1,j, ..., BM,j ]T for later use.
We use the sum of the transmitted data, named as total
transmitted data , as the communication performance metric
when formulating UA V trajectory design problem. After the
UA V completes the j-th stage, the total transmitted data for
the m-th CU, can be expressed via Rm,n,j at all waypoints
from the 1st stage to the j-th stage, which is
ψcm (j) =
jX
j′=1
N fj′X
n=1
Tf Rm,n,j′ +
jX
j′=1
N hj′X
γ=1
ThRm,µγ,j ′. (8)
We use j′ to denote stages across the 1st to the j-th stage,
because the current stage is with the index j and we need to
make a difference between them.
To guarantee the fairness among CUs, the UA V communi-
cation in a stage aims to improve the lower bound of total
transmitted data among all CUs, which is
Ψc (j) = min {ψc1 (j) , ..., ψcm (j) , ..., ψcM (j)} , j= 1, ..., J.
(9)
C. Sensing Model
We use dsk,j = hdsk,1,j, ..., dsk,γ,j , ..., dsk,N hj ,jiT to representtrue distances between the k-th ST and all HPs in the j-th
stage, where dsk,γ,j is the distance from the γ-th HP to the
k-th ST as
dsk,γ,j =
r
H 2 +



sµγ,j − [xtk, ytk]T 


2, (10)
which is obtained from
dsk,γ,j = τk,γ,j · c2 , (11)
where c is the speed of light. τk,γ,j is the two-way propagation
delay of the signal from the UA V at sµγ,j to the k-th ST and
reflected by the ST to the UA V . The measurement of dsk,γ,j is
edsk,γ,j = dsk,γ,j + wτk,γ,j , (12)
where wτk,γ,j denotes the Gaussian noise with zero
mean and variance

στk,γ,j
2
. We set a vector edsk,j =h
edsk,1,j, ...edsk,γ,j , ...,edsk,N hj ,j
iT
for convenience.
Note that

στk,γ,j
2
is inversely proportional to the echo
SNR from the k-th ST to the γ-th HP [41], [42]. The SNR is
formulated as
SN Rsk,γ,j = Pt · Gp · gk,γ,jσ20 , (13)
where Gp is the signal processing gain at the UA V receive
side. gk,γ,j is the two-way channel power gain between the
k-th ST and the γ-th HP, which is formed as
gk,γ,j = β0h
dsk,γ,j
i4 . (14)
β0 is the channel power at the reference distance dsk,γ,j = 1m,
which is expressed as
β0 = GT · Gs · σrcs · λ2
(4π)3 , (15)
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

6
where Gs is the ST receive antenna gain and σrcs is the Radar
Cross-Section (RCS).
Finally, we remark

στk,γ,j
2
as
 
στk,γ,j 2 = aσ20Pt · Gp · gk,γ,j . (16)
a is associated with the transmission environment noise.
To assess the performance of an estimator, MSE, where
ϵ2 = E ∥ uk − buk,j ∥2, is a commonly used metric. How-
ever, obtaining the MSE in closed-form is often arduous and
minimizing MSE is almost intractable. In this case, we cannot
directly use the MSE of buk,j (k = 1, ..., Kand j = 1, ..., J)
as the sensing performance metric in the trajectory design
formulation. Instead, for an unbiased parameter estimator,
CRB can provide a lower bound for the MSE [39]. Therefore,
we resort to CRB as the metric.
Now, we formulate the CRB of bxtk,j and the CRB of bytk,j
(k = 1, ..., Kand j = 1, ..., J). According to [39], the CRB
of the p-th element belonging to a vector u corresponds to the
p-th diagonal element of the CRB matrix of u. Therefore, our
first step is to compute the CRB matrix of buk,j, expressed as
CRBukk (j), which can be attained through
CRBukk (j) = [Jukk (j)]−1 ∈ R2×2, (17)
where Jukk (j) ∈ R2×2 is the Fisher information matrix (FIM)
of uk.
In most cases, if computing FIM with respect to some
certain parameters is difficult, we can first compute the FIM
of other related parameters. Then, we can exploit the mathe-
matical relationship between two FIMs to derive the former
FIM. For Jukk (j), we can first construct FIM with respect
to distances between the k-th ST and the UA V , denoted by
Jdsk (j). As aforementioned, after the j-th stage, estimation on
the k-th ST’s location is performed by measurements from the
1st stage to the j-th stage, thereby, Jdsk (j) is a matrix with
size
 
N h1 + ... + N hj  ×  N h1 + ... + N hj . Then Jukk (j) can
be derived by using the chain rule in the form of
Jukk (j) = Qk (j) Jdsk (j) [Qk (j)]T . (18)
Qk (j) ∈ R2×(N h1 +...+N hj ) is a Jacobian matrix shown in (19)
in the next page, where
∂
h
dsk,j ′
iT
∂uk
=


xh1,j′ −xtk
dsk,1,j′ ...
xhγ,j ′ −xtk
dsk,γ,j ′ ...
xhN hj′ ,j′ −xtk
ds
k,N hj′ ,j′
yh1,j′ −ytk
dsk,1,j′ ...
yhγ,j ′ −ytk
dsk,γ,j ′ ...
yhN hj′ ,j′ −ytk
ds
k,N hj′ ,j′

 ,
j′ = 1, 2, ..., j.
(20)
Jdsk (j) can be separated into j FIMs with respect to dsk,j ′
(j′ = 1 , ..., j). The FIM of dsk,j ′ is denoted as Λdsk,j ′ ∈
RN hj′ ×N hj′ . Similarly with the communication performance
metric, we use j′ to denote stages across the 1st to the j-
th stage.
From (12)-(16), we observe that the mean of edsk,γ,j ′ is
dsk,γ,j ′ and the covariance of edsk,γ,j ′ is στk,γ,j ′2, which are
both dependent on dsk,γ,j ′. Thus, edsk,j ′ follows the distribution
as
edsk,j ′ ∼ N dsk,j ′, Csk,j ′ , j′ = 1, 2, ..., j, (21)
where Csk,j ′ is a diagonal matrix as the form of
Csk,j ′ = aσ20P Gpβ0 diag  dsk,1,j′4 , ...,dsk,N hj′ ,j′4! . (22)
For every parameter in a vector, if its measurement’s mean and
covariance both depend on a same argument, we can obtain
the FIM of that vector via eq. 3.31 in [39]. Following [39] (eq.
3.31), we acquire Λdsk,j ′ as (23) at the top of the next page.
In accordance with (23), we observe that Λdsk,j ′ is a diagonal
matrix. So that Jdsk (j) is still a diagonal matrix constructed
by Λdsk,j ′ (j′ = 1, 2, ..., j) as
Jdsk (j) = diag diag Λdsk,1 , diag Λdsk,2 , ...,diag Λdsk,j  .
(24)
Finally, substituting (19) and (24) into (18), the CRB matrix
of buk,j can be expressed as
CRBukk (j) = [Jukk (j)]−1
= 1
Θak (j) Θbk (j) − [Θck (j)]2

Θbk (j) Θ ck (j)
Θck (j) Θ ak (j)

,
(25)
where Θak (j), Θbk (j) and Θck (j) are shown in (26)-(28) of the
next page. The CRB of bxtk,j and the CRB of bytk,j are diagonal
elements of CRBukk (j), which are given by
CRBxk (j) = Θbk (j)Θak (j) Θbk (j) − [Θck (j)]2 , (29)
CRByk (j) = Θak (j)Θak (j) Θbk,j − [Θck (j)]2 . (30)
We adopt the sum of CRB xk (j) and CRByk (j) as the sensing
performance metric, which is
ψsk (j) = Θbk (j) + Θak (j)Θak (j) Θbk (j) − [Θck (j)]2 . (31)
As mentioned above in Subsection A, since xtk and ytk are
unknown, following the MSTD approach, when formulating
the UA V trajectory design problem in the j-th stage, xtk and
ytk in (31) should be substituted by bxtk,j−1 and bytk,j−1.
To guarantee the fairness between STs, the sensing objective
is to minimize the upper bound of the CRB among all STs,
expressed as
Ψs (j) = max {ψs1 (j) , ..., ψsk (j) , ..., ψsK (j)} . (32)
III. T HE FORMULATION FOR UAV TRAJECTORY DESIGN
AND BANDWIDTH ALLOCATION
The UA V power consumption includes power for transmit-
ting signals and for supporting mobility. Transmission power
consumed is usually significantly lower compared to the power
required for propulsion. Therefore, we choose to ignore the
transmission power. The propulsion power consumption can
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

7
Qk (j) =
∂
h
dsk,1, ...,dsk,j ′, ...,dsk,j
iT
∂uk
=

 ∂
h
dsk,1
iT
∂uk
, ...,
∂
h
dsk,j ′
iT
∂uk
, ...,
∂
h
dsk,j
iT
∂uk

 , (19)
h
Λdsk,j ′ip,q = " ∂dsk,j ′∂dsk,p,j ′ #T Csk,j ′−1 " ∂dsk,j ′∂dsk,q,j ′ # + 12 tr Csk,j ′−1 ∂ hCsk,j ′i∂dsk,p,j ′ Csk,j ′−1 ∂ hCsk,j ′i∂dsk,q,j ′  , p, q= 1, ..., Nhj′. (23)
Θak (j) =
jX
j′=1
N hj′X
γ=1



PtGpβ0
aσ20
 
xhγ,j ′ − xtk2
h
dsk,γ,j ′
i6 +
8
 
xhγ,j ′ − xtk2
h
dsk,γ,j ′
i4


 , (26)
Θbk (j) =
jX
j′=1
N hj′X
γ=1



PtGpβ0
aσ20
 
yhγ,j ′ − ytk2
h
dsk,γ,j ′
i6 +
8
 
yhγ,j ′ − ytk2
h
dsk,γ,j ′
i4


 , (27)
Θck (j) =
jX
j′=1
N hj′X
γ=1



PtGpβ0
aσ20
 
xhγ,j ′ − xtk  yhγ,j ′ − ytkh
dsk,γ,j ′
i6 +
8
 
xhγ,j ′ − xtk  yhγ,j ′ − ytkh
dsk,γ,j ′
i4


 . (28)
be modeled as the function of speed V [26], which is shown
as
Puav(V ) =P0

1 + 3V 2
Utip2

+ PI
 s
1 + V 4
4v04

− V 2
2v02
! 12
+ 12 D0ρsAV 3. (33)
To account for the difference in units between total trans-
mitted data and CRB, we introduce performance increment as
the metric. Additionally, we normalize these two performance
increments to ensure a fair comparison between them. The
problem formulation of UA V trajectory design and bandwidth
allocation for the j-th stage is
P (j) : max
{Sj ,Vj ,Bj }
η
Ψs (j − 1) (Ψs (j − 1) − Ψs (j))
+ (1 − η)Ψc (j − 1) (Ψc (j) − Ψc (j − 1))
s.t. (1) and (2) ,
∥vn,j∥ ≤Vmax, n= 1, ..., Nfj , (34a)
0 ≤ sn,j (1) ≤ Lx, 0 ≤ sn,j (2) ≤ Ly, (34b)
n = 1, ..., Nfj ,
Tf
N fjX
n=1
Puav (∥vn,j∥) + ThN hj Puav (0) ≤ Ej,
(34c)
MX
m=1
Bm,j ≤ B. (34d)
We apply a weighting factor η(0 ≤ η ≤ 1) to obtain a
tractable tradeoff between C&S. Larger η indicates that the
UA V trajectory design assigns higher priority on sensing.Vmax
is the maximum UA V flying speed. Constraint (34b) restricts
that the UA V should fly in the designated area. Constraint
(34c) means that the UA V energy consumed in the j-th stage
should be no more than its current remaining energy.
Since (9) and (32) are nondifferentiable, we consider to
use log–sum–exp (LSE) in the objective function of P (j) as
smooth approximations to Ψc (j) and Ψs (j). A lower-bound
of (9) and an upper-bound of (32) are shown respectively as
min {ψc1 (j) , ..., ψcM (j)}
≥ log (exp (−ψc1 (j)) + ... + exp (−ψcM (j)))
≥ min {ψc1 (j) , ..., ψcM (j)} −log (M ), (35)
and
max {ψs1 (j) , ..., ψsK (j)}
≤ log (exp (ψs1 (j)) + ... + exp (ψsK (j)))
≤ max {ψs1 (j) , ..., ψsK (j)} + log (K). (36)
The first inequality is strict unless M (K) = 1 . The second
inequality is strict unless all arguments are equal. In addition,
we can scale (35) and (36) to make bounds tighter, then
min {ψc1 (j) , ..., ψcM (j)}
≥ 1−t log (exp (−tψc1 (j)) + ... + exp (−tψcM (j)))
≥ min {ψc1 (j) , ..., ψcM (j)} −log (M )t , (37)
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

8
and
max {ψs1 (j) , ..., ψsK (j)}
≤ 1t log (exp (tψs1 (j)) + ... + exp (tψsK (j)))
≤ max {ψs1 (j) , ..., ψsK (j)} + log (K)t , (38)
where t > 0. Finally, we can substitute (9) and (32) in the
objective function of P (j) by the middle term of (37) and
(38) respectively, and denote the modified objective function
as f (Sj, Bj). Finally, P (j) is rewritten as
P′ (j) : max
{Sj ,Vj ,Bj }
f (Sj, Bj)
s.t. (1), (2), (34a) − (34d).
IV. P ROPOSED ALGORITHM FOR SOLVING P′ (j) AND
ESTIMATIONS FOR ST LOCATIONS
Due to f (Sj, Bj) and constraint (34c) in P′ (j) are noncon-
vex, we divide P′ (j) into two subproblems, which optimize
{Sj, Vj} and Bj respectively, and address them in order
repeatably. The two subproblems are given by
P′1 (j) : max{Sj ,Vj } f (Sj)
s.t. (1), (2), (34a) − (34c).
P′2 (j) : max Bj f (Bj)
s.t. (34d).
P′2 (j) is a convex problem solved directly via CVX in Matlab.
This section aims to addressing P′1 (j).
A. Proposed Iterative Algorithm for P′1 (j)
Since f (Sj) is nonconvexity, an ascent direction search
method is used to find the local optimal solution of P′1 (j).
Firstly, let us approximate f (Sj) by its first-order Taylor
expansion near S′j = hs′1,j, ...,s′N fj ,ji ∈ R2×N fj to obtain itsascent direction as
f (Sj) ≈f
 
S′j +
N fjX
n=1
∇fsn,j (1)
 
S′j  sn,j(1) − s′n,j(1)
+
N fjX
n=1
∇fsn,j (2)
 
S′j  sn,j(2) − s′n,j(2) , (39)
where ∇fsn,j (1) (·) and ∇fsn,j (2) (·) represent the gradient
of f (·) with respect to sn,j(1) and sn,j(2) respectively. By
maximizing the right-hand-side (RHS) of (39), we can find the
ascent direction of f (Sj). This maximizing process focuses
on the last two terms of the RHS, as the first term is fixed.
The ascent direction search is conducted iteratively, allow-
ing us to gradually approach the local optimal solution for
P′1 (j). We reformulate P′1 (j) to an iterative form as
Q (j) : max
{Sj ,Vj }
g (Sj)
=
N fjX
n=1
∇fsn,j (1)
 
Sl−1j   sn,j(1) − sl−1n,j (1)
+
N fjX
n=1
∇fsn,j (2)
 
Sl−1j   sn,j(2) − sl−1n,j (2)
s.t. (1), (2), (34a) − (34c),
where Sl−1j = hsl−11,j , ...,sl−1N fj ,jiT ∈ R2×N fj is Sj obtained
from the (l − 1)-th iteration. It is evident that g (Sj) ≥ 0,
since g
 
Sl−1j  = 0 . By maximizing g (Sj), we obtain the
optimal solution of Sj in Q (j), denoted as S∗j . Then, we can
determine the ascent direction of f (Sj) as S∗j −Sl−1j [43]. We
then move along S∗j − Sl−1j with a stepsize ωj(0 ≤ ωj ≤ 1)
to explore the point along S∗j − Sl−1j that yields maximum
f (Sj). The resulting Slj is expressed as
Slj = Sl−1j + ω∗j  S∗j − Sl−1j  , (40)
where ω∗j is the stepsize that can obtain the maximum f (Sj).
Due to the nonconvex constraint (34c), we are still unable
to solve Q (j) directly. Since the second term of the RHS of
(33) is nonconvex, we build a convex bound for (34c). We
introduce variables δj = {δ1,j, ..., δn,j, ..., δN fj ,j} as
[δn,j]2 =
vuut 1 + ∥vn,j∥4
4v40
!
− ∥vn,j∥2
2v20 , n= 1, ..., Nfj ,
(41)
δn,j ≥ 0, n= 1, ..., Nfj , (42)
where (41) above is equivalent to
∥vn,j∥2
v20 = 1[δn,j]2 − [δn,j]2 , n= 1, ..., Nfj . (43)
Then, (34c) can be rewritten by (42), (43) and the following
inequality
Ej ≥ Tf
N fjX
n=1
(
P0
 
1 + 3 ∥vn,j∥2
Utip2
!
+ 12 D0ρsA ∥vn,j∥3
)
+ Tf
N fjX
n=1
PIδn,j + Th · N hj · (P0 + PI) . (44)
With the above manipulations, Q (j) can be rewritten as
Q′ (j) : max
{Sj ,Vj ,δj }
g (Sj)
s.t. ∥vn,j∥2
v20 ≥ 1[δn,j]2 − [δn,j]2 , n= 1, ..., Nfj . (45)
(1), (2), (34a), (34b), (42) and (44) .
Note that Q′ (j) is obtained by replacing (43) with an in-
equality constraint (45), which does not affect the availability
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

9
of Q (j). Specifically, once constraints (42), (44) and (45) are
satisfied, constraint (34c) is satisfied. We introduce variables
ξj = {ξ1,j, ..., ξN fj ,j} and rewrite constraint (45) as
∥vn,j∥2
v20 ≥ 1[δn,j]2 − ξn,j, n= 1, ..., Nfj , (46)
[δn,j]2 ≥ ξn,j, n= 1, ..., Nfj , (47)
ξn,j ≥ 0, n= 1, ..., Nfj . (48)
We observe that (47) is established following a similar process
of (43). Once (46)-(48) are satisfied, (45) is satisfied.
Now, constraints (46) and (47) can be handled using the
SCA method. Specifically, by utilizing the property that any
convex expression is globally lower-bounded by its first-order
Taylor expansion at any point [43], and by noting that the
left-hand-side (LHS) of (46) and (47) are both convex, we
can approximate the LHS of (46) and (47) around points
Vl−1j = nvl−11,j , ...,vl−1N fj ,jo and δl−1j = {δl−11,j , ..., δl−1N fj ,j} fromthe previous iteration. The LHS of (46) is approximated as
∥vn,j∥2
v20 ≥


vl−1n,j 

2
v20 + 2v20 vl−1n,j T  vn,j − vl−1n,j  . (49)
Then, we approximate the LHS of (47) as
[δn,j]2 ≥ δl−1n,j 2 + 2δl−1n,j  δn,j − δl−1n,j  . (50)
Thus, we find the lower bounds for the LHS of (46) and
(47). Now, we reformulate Q′ (j) to acquire S∗j as
Q′′ (j) : max
{Sj ,Vj ,δj ,ξj }
g (Sj)
s.t.


vl−1n,j 

2
v20 + 2v20 vl−1n,j T  vn,j − vl−1n,j 
≥ 1
[δn,j]2 − ξn,j, n= 1, ..., Nfj , (51a)
δl−1n,j 2 + 2δl−1n,j  δn,j − δl−1n,j  ≥ ξn,j, (51b)
n = 1, ..., Nfj ,
(1), (2), (34a), (34b), (42), (44) and (48) .
Note that due to the lower bounds in (51a) and (51b)
obtained from SCA, if all constraints in Q′′ (j) are satisfied,
then constraints in Q (j) are guaranteed to be satisfied as well.
We then need to prove that all possible points of {Sj, Vj}
following S∗j −Sl−1j are from the feasible region of constraints
in P′1 (j). The proof is illustrated in Appendix A.
After obtaining UA V flying waypoints and HPs, the band-
width allocated to each CU can be solved directly in P′2 (j).
The iterative process of the ascent direction search method
needs the initial inputs S0j, V0j and δ0j for iteration index l = 1
to start the iterative process. To determine reasonable initial
inputs, we design a hypothetical initial trajectory as follows. To
initialize the ascent direction search method for the j-th stage’s
trajectory design, i.e., P′1 (j), the hypothetical trajectory is
from the final waypoint in the (j − 1)-th stage toward to the
point [Lx, Ly]T straightly with a fixed flying velocity. Based
on the hypothetical trajectory design, the initial inputs can be
calculated. The ascent direction search method for P′1 (j) is
shown in Algorithm 1.
Algorithm 1 The ascent direction search method for P′1 (j).
Initialization: Obtain S0j, V0j and δ0j via the hypothetical
trajectory design; l = 1;
1: repeat
2: Formulate Q′′ (j); Obtain S∗j via CVX in MATLAB;
3: For ωj = 0 : ∆ω : 1
4: Obtain f (Sj), where Sj = ωj
 
S∗j − Sl−1j +Sl−1j ;
5: End
6: Find ωj that maximizes f (Sj) and denote it as ω∗j ;
7: Obtain Slj via (40); calculate Vlj and δlj;
8: Update l = l + 1;
9: until f
 
Sl−1j  < f Sl−2j .
10: Sj = Sl−2j and Vj = Vl−2j .
B. Estimation Method for ST Locations
Now, we illustrate the estimation method for uk,j =
[xtk, ytk]T (k = 1, ..., K), via MLE [39].
As discussed in Section II, the UA V trajectory design
problem is a multi-stage process. At the end of the j-th
stage, the distance measurements of the k-th ST contains
N h1 + ... + N hj elements, which is expressed as eDk (j) =h
edsk,1, ...,edsk,j ′, ...,edsk,j
iT
. The likelihood function of uk,j
with respect to eDk (j) is shown in (52) at the top of the next
page. The MLE of uk,j is expressed as

bxtk,j , bytk,j T = arg
(
max
[xtk,ytk]T
h
log p

eDk (j) ;xtk, ytkT i) .
(53)
Since a closed-form solution is unobtainable for the MLE,
a grid search is applied in function (52) to find buk,j =h
bxtk,j , eytk,j
iT
that maximizes p

eDk (j) ; [xtk, ytk]T

. Finally,
the MSE is assessed through Monte Carlo simulation. The
complete MSTD approach is outlined in Algorithm 2. Emin is
the minimum required energy for a UA V trajectory with Nstg
waypoints.
C. Extension on the Proposed ISAC-based UA V Scenario:
Moving STs and Multiple UA Vs
In this subsection, we consider about sensing moving STs
within the UA V trajectory design problem and explore poten-
tial solutions to extend the ISAC-based UA V scenario to a
multi-UA V case.
Unlike static STs, where the coordinate estimates are
obtained by the distance measurements between HPs and
STs, moving STs necessitate the additional measurement of
Doppler frequency for estimating velocities. Furthermore, due
to the mobility of STs, predicting coordinates of STs in each
stage is essential to formulate the trajectory design problem.
Various approaches, e.g., Kalman filtering [39] and factor
graph based message passing algorithms [44] can be employed
to predict and estimate ST states at each stage.
The ISAC-based UA V scenario with moving STs can be
formulated as follows. There are several UA Vs in the given
area, where one UA V is similar to the UA V considered in
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

10
p

eDk (j) ;xtk, ytkT  = jY
j′=1
N hj′Y
γ=1
1r
2π

στk,γ,j ′
2 exp

 −1
2

στk,γ,j ′
2
 
dsk,γ,j ′ −
r
xhγ,j ′ − xtk
2
+

yhγ,j ′ − ytk
2
+ H 2
!2

 .
(52)
Algorithm 2 The MSTD approach for ISAC-based UA V
trajectory design, bandwidth allocation and ST estimations
Initialize:
h
bxtk,0, bytk,0
iT
(k = 1, ..., K); j = 1; E1 = Etot;
1: repeat
2: N fj = Nstg; Bm,j = BM ; Address P′1 (j);
3: Address P′2 (j);
4: UA V flies followingSj and transmits signals; UA V hov-
ers at

xhj , yhj  in order and obtains edsk,j (k = 1, ..., K);
5: Estimate
h
bxtk,j , bytk,j
iT
(k = 1, ..., K) via MLE;
6: Update j = j + 1; Calculate Ej;
7: until Ej < Emin.
8: Denote j = J;
9: NJ = Nlst; Bm,J = BM ; Address P′1 (J);
10: Address P′2 (J);
11: UA V flies followingSJ and transmits signals; UA V hovers
at

xhJ , yhJ  and obtains edsk,J (k = 1, ..., K);
12: Estimate
h
bxtk,J , bytk,J
iT
(k = 1, ..., K) via MLE.
our scenario, used to broadcast downlink signals, and others
are hovering UA Vs receiving the echoes reflected by all
STs. There are transmission links between UA Vs to share
information and realize synchronization. Since the scenario
involving moving STs applies multiple UA Vs, when using
the proposed MSTD approach, we cancel HPs in the UA V
trajectory and set only one sensing point (SP) in each stage.
The moving UA V broadcasts signals continuously to CUs in
each stage. Subsequently, at the moment when it passes the SP,
the receive antennas of hovering UA Vs receive echoes reflected
by all STs. Then, the echoes reflected by the same ST are used
together to estimate that ST’s state parameters. Since STs are
moving, the time duration in each stage should be shorter to
realize a more frequent state evolution, especially when the
moving speed of STs is high. Meanwhile, the number of stages
will be increased after this adjustment.
The state parameters associated with one ST comprise the
two-dimensional coordinate and the two-dimensional velocity.
Similar to the MSTD approach outlined in the static scenario,
the tracking process for moving STs initiates with a coarse
estimation of state parameters. Through the repetition of 1)
state prediction, 2) UA V trajectory design, 3) C&S performing
and 4) state estimation, the UA V network can simultaneously
track moving STs while communicating with CUs. The spe-
cific process is as follows. By leveraging estimates of state
parameters obtained after the (j − 1)-th stage, the system pre-
dicts the k-th ST’s state parameters (k = 1, 2, ..., K) associated
with the j-th stage. Subsequently, sensing performance metrics
ψsk (j) (k = 1 , 2, ..., K) are derived and the UA V trajectory
design for the j-th stage is formulated using the predicted state
parameters. During the j-th stage, the UA V follows the de-
signed trajectory and broadcasts signals. Meanwhile, hovering
UA Vs receive signals reflected by STs when the moving UA V
passes the SP. Echoes from the same ST are used together to
obtain distance and Doppler frequency measurements, refining
the predicted state parameters of that ST to updated state
estimates. These updated estimates are then served as inputs
for predicting that ST’s state parameters associated with the
(j + 1)-th stage for formulating the trajectory design problem
in that stage.
Since the estimation of state parameters for one ST is based
not only on distance and Doppler frequency measurements but
also includes the state prediction, the CRB applied in P (j)
differs from the one presented in (25). The CRB including
prediction requires to derive both the CRB of measurements
and the CRB of state prediction, leading to a posterior CRB
(PCRB) [41].
In scenarios with multiple UA Vs, the signal transmissions
may cause collisions. To address this issue, UA V clustering is
a commonly employed method, wherein ground STs and CUs
are divided into several clusters, with each UA V is assigned to
serve a specific cluster. After the UA V clustering, each UA V
flies straightly to its corresponding cluster and performs C&S
functions within that cluster.
A crucial problem in UA V clustering is the sustainability
of UA Vs. As each UA V needs to fly a long distance to
arrive its cluster, the energy consumed covering this flying is
considerable which cannot be ignored. The leftover energy of
each UA V constrains the C&S performances in the respective
clusters. In this case, the effective management of UA V clus-
ters is necessary. Energy saving strategies and considerations
of fairness in clustering methods, as discussed in [45] and
[46], are employed for UA V clustering before designing each
UA V’s trajectory in its cluster.
V. N UMERICAL RESULTS
This section provides numerical results to evaluate per-
formances of the MSTD approach in the ISAC-based UA V
scenario. We set [xB, yB]T = [0 , 0]T . The locations of STs
and CUs are generated using a uniform point distribution in
the simulation. The MSE of a ST’s coordinate estimate is
evaluated through Monte Carlo simulation with 100 runs. The
simulation parameters are provided in Table I.
We compare C&S performances in ISAC-based UA V
scheme with a traditional UA V scheme where the designated
area contains two UA Vs, which are dedicated to communica-
tion or sensing respectively. This allows us to assess the energy
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

11
TABLE I: Simulation parameters
parameter value parameter value
P0 80 W PI 88.6 W
Utip 120 m/s v0 4.03 m/s
D0 0.6 s 0.05 m3
ρ 1.225 kg/m3 A 0.503 m2
α0 -50 dB β0 -49 dB
N0 -170 dBm/Hz σ20 N0·bandwidth
Pt 20 dBm B 10 MHz
Gp 0.1B Vmax 30 m/s
H 200 m Th 1.5 s
∆ω 100 µ 5
Lx 1500 m Ly 1500 m
Tf 1 s a 200
efficiency of the ISAC scheme in comparison to this baseline
scheme. We define the following terms used in this section:
1) “ISAC”: The scheme with one ISAC-based UA V , where the
UA V trajectory and HPs are determined by addressing P′1 (j),
and the bandwidth of each CU is set as Bm,j = BM (m =
1, 2, ..., M);
2) “ISAC + BA”: The scheme with one ISAC-based UA V ,
where the UA V trajectory and HPs are determined by address-
ing P′1 (j), and the bandwidth of each CU is determined via
P′2 (j);
3) “Separate”: The baseline scheme. One UA V trajectory is
determined by addressing P′1 (j) with η = 0 , focusing on
transmitting signals to CUs. One UA V trajectory is determined
by addressing P′1 (j) with η = 1, focusing on localizing ST
locations;
Meanwhile, we consider two simple UA V trajectories as
performance bounds to illustrate the enhancements achieved
through the proposed trajectory design approach. Referring to
[47] and [48], we introduce the following two widely used
trajectories in UA V wireless scenarios:
4) “Straight”: The UA V follows a straight path without any
specialized design, which is similar with the initial inputs
applied in Algorithm 2. The UA V flies with a constant speed
of Vmax, traveling directly from [xB, yB]T to [Lx, Ly]T and
retraces the same path until its energy runs out. The UA V
performs C&S functions during its flying.
5) “Circle”: The UA V follows a circular path with the center
located at [0.5Lx, 0.5Ly]T and a radius of 0.25Lx. The UA V
maintains a constant speed of Vmax along the circular path un-
til its energy is exhausted. The UA V performs C&S functions
during its flying.
We begin by studying the convergence behavior of the
iterative algorithm proposed for P′1 (j). In Fig. 3, we show
the convergence of C&S performance metrics for the 1st
stage’s trajectory design in a randomly-generated scenario. It
can be observed that the iterative algorithm exhibits a fast
convergence rate, highlighting the effectiveness of the ascent
direction search method. We notice that the CRB value does
not always decrease with iteration index increase, because a
weighted sum optimization objective is adopted in P (j), and
the communication performance is the dominant metric of
the optimization process in this randomly-generated scenario.
As long as the objective function value of P (j) consistently
increases with the index increase, it is meaningful to employ
0 5 10 15
Iteration index
0.4
0.5
0.6
0.7
0.8Upper bound of CRB of x + CRB of y (m2)
20.5
21
21.5
22
22.5
23
23.5
The objective of P(j)
(a) Sensing performance and the objective function value
of P (j)
0 5 10 15
Iteration index
2.3
2.4
2.5
2.6
2.7Lower bound of total transmitted data (Gbits)
20.5
21
21.5
22
22.5
23
23.5
The objective of P(j)
(b) Communication performance and the objective func-
tion value of P (j)
Fig. 3: Convergence behaviour of the proposed algorithm
solving P′1 (j) (j = 1, Nstg = 60, η = 0.5, K = 2, M = 2
and Etot = 40KJ).
1 2 3 4
Stage index j
100
101
Squared estimation error of x + of y (m2)
CRB+ISAC,ST 1
MSE+ISAC,ST 1
CRB+ISAC,ST 2
MSE+ISAC,ST 2
Fig. 4: Sensing performance based on the MSTD approach
(Nstg = 60, η = 1, K = 2 and Etot = 60KJ).
the proposed algorithm for P′1 (j).
In Fig. 4, we give the sensing performance trend of each
ST following stages in a randomly-generated scenario. The
“MSE+ISAC” means the MSE of ST’s coordinate estimates
via MLE. “CRB+ISAC” is the CRB of ST’s coordinate esti-
mates. It is shown that the sensing performance improves as
the UA V progresses to the next stage. This improvement is
attributed to the accumulation in eDk (j). In Fig. 4, the CRB
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

12
20 30 40 50 60
Energy supply (KJ)
10-1
100
101
102
Upper bound of CRB of x + CRB of y (m2)
separate
ISAC
ISAC+BA
straight
circle
(a) Sensing
20 30 40 50 60
Energy supply (KJ)
0
2
4
6
8
10
Lower bound of total transmitted data (Gbits)
separate
ISAC
ISAC+BA
straight
circle
(b) Communication
Fig. 5: Performances of different schemes versus total energy
supply ( Nstg = 60, η = 0.5, K = 2 and M = 2).
is a loose lower bound for the MSE, which happens because of
the reason as follows. Since the observations are time delays
between the ST and HPs, whereas the estimates are locations,
this results in a nonlinear relationship between measurements
and estimates. In the CRB derivation in (18), a linear approx-
imation is employed to transform the CRB of distance mea-
surements into the CRB of coordinates. Therefore, the MSE of
coordinates can asymptotically achieve the approximated CRB
with large number of random and independent measurements,
as well as the variance of measurements should be enough
low. Subsequently, since HPs in the designed trajectory are
not randomly generated, which are intentionally arranged and
positioned contiguously, as well as the measurement amount
is not large enough, the coordinate measurements cannot
be generated strictly randomly and independently. Given the
inability of UA V paths to generate a random distribution of
HPs in abundance, the CRB performing the loose bound of
MSE cannot be solved. Nevertheless, the trends of CRB and
MSE are similar, which can make the optimization process
being meaningful.
The above reason also explains the necessity of consid-
ering angle diversity concerning sensing points in location
estimation, as coordinate estimation involves utilizing one-
dimensional measurements to acquire a two-dimensional esti-
mate.
0 500 1000 1500
Lx (m)
0
500
1000
1500Ly (m)
STs
CUs
Charging base
Trajectory
HPs
(a) Etot = 40KJ
0 500 1000 1500
Lx (m)
0
500
1000
1500Ly (m)
STs
CUs
Charging base
Trajectory
HPs
(b) Etot = 60KJ
Fig. 6: The ISAC-based UA V trajectories under different Etot
(Nstg = 60 and η = 0.5).
10-1 100 101 102
Upper bound of CRB of x + CRB of y (m2)
20
40
60
80
100
120Required energy (KJ)
separate
ISAC
ISAC+BA
5 Gbits
4 Gbits
3 Gbits
2 Gbits
6 Gbits
7 Gbits
Fig. 7: Required energy supply versus various performance
requirements (Nstg = 60, η = 0.5, K = 2 and M = 2).
A. The C&S Performances of the ISAC Scheme Compared
with Other Schemes
Fig. 5 illustrates the improvement on C&S performances of
the proposed trajectory design, as well as compares the ISAC-
based UA V scheme with the “separate” scheme. To ensure
the fairness between ISAC scheme and “separate” scheme,
we set that in the “separate” scheme, Etot of the UA V for
communication and Etot of the UA V for sensing are both
the half value of x-axis, while for the UA V in the ISAC
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

13
1 2 3 4
K
100
Upper bound of CRB of x + CRB of y (m2)
separate
ISAC
ISAC+BA
(a) Number of STs ( M = 2)
1 2 3 4 5 6
M
0
2
4
6
8
10
12Lower bound of total transmitted data (Gbits)
separate
ISAC
ISAC+BA
(b) Number of CUs ( K = 2)
Fig. 8: The C&S performances versus K and M (Nstg = 60,
η = 0.5 and Etot = 40KJ in ISAC scheme, Etot = 20KJ in
“separate” scheme).
scheme, Etot is equal to the value of x-axis. This ensures that
the energy supply provided for the ISAC-based UA V and for
the scenario with two “separate” UA Vs is same. The results
show that with the same energy supply, the ISAC scheme
with the trajectory design outperforms the “separate” scheme
in terms of C&S performances. Bandwidth allocation results
in a performance improvement on communication, where an
increase of at least 0.5 Gbits transmitted data can be achieved.
We should notice that even though the growth of energy
supply results in a performance improvement in both C&S,
the CRB decreases slowly when Etot is large. This is because
the relationship between CRB and the number of distance
measurements is nonlinear. Once we have enough distance
measurements with adequate spatial diversity, additional mea-
surements become redundant as they are just a repeat of former
ones. Furthermore, it is obvious that, comparing with the UA V
flying without trajectory design, both the C&S performances
from the proposed trajectory are improved. UA V flying with
a circle path is better than the straight path, since the straight
path brings less sensing angle diversity.
Fig. 6 compares the ISAC-based UA V trajectories under
different Etot to illustrate why a larger Etot can achieve
better C&S performances. Specifically, the UA V covers a
longer distance and more HPs with a larger Etot, which
means more distance measurements obtained. This leads to
a decreased CRB. The larger Etot also enables more data
transmission during longer flying duration, thereby increasing
total transmitted data. We can additionally observe that in
Fig. 6 (a), in such a distribution of STs and CUs, because of
the C&S tradeoff, the UA V initially flies approaching to the
upper right area where three points are allocated. However,
with more energy supply in Fig. 6 (b), to maintain fairness
between two STs, the UA V then adjusts its trajectory towards
to the upper left ST and alternates between two areas.
Fig. 7 demonstrates the UA V energy consumption of the
ISAC scheme compared to the “separate” scheme under dif-
ferent C&S requirements. The data values in Fig. 7 indicate
that when the CRB on the x-axis is satisfied, the corresponding
total transmitted data should also be satisfied. Fig. 7 confirms
that under the same C&S requirements, the ISAC scheme
consumes less energy compared to two UA Vs flying for C&S
respectively. This indicates a higher energy efficiency with the
ISAC scheme in UA V scenario. Furthermore, using bandwidth
allocation can contribute to energy savings.
B. The C&S Performances with V arious Numbers of CUs and
STs
Fig. 8 (a) depicts the upper bound of CRB among all STs
with varying numbers of STs. It can be observed that in the
ISAC scheme, CRB increases considerably when the number
of STs increases from 1 to 2. This is because the fairness
between STs definitely influences sensing. In particular, for
example, when two STs are located at a large distance from
each other, the UA V may be unable to fly closely to both
of them. Nonetheless, for the “separate” scheme, the CRB
remains nearly unchanged when the number of STs increases
from 1 to 2. That is because in the ISAC scheme, the UA V
trajectory must consider both STs and CUs in the area.
Consequently, besides the large distance between two STs,
in the ISAC scheme, the distance between STs and CUs
also has an impact on sensing. In contrast, for the “separate”
scheme, Etot = 20KJ is sufficient to support a UA V sensing
for two STs, therefore the large distance between two STs
does not strongly influence the sensing performance. The
degradation of sensing performance becomes less pronounced
in ISAC scheme as the number of STs continues to increase.
This is because when the STs become more concentrated in
their distribution, the UA V can fly closer to two or more
STs simultaneously, to have better distance measurements for
multiple STs. Fig. 8 (b) shows the lower bound of total
transmitted data under various numbers of CUs. As can be
seen, the total transmitted data exhibits a decreasing trend
as the number of CUs increases, resulting from the smaller
bandwidth allocated to each CU. Nevertheless, as the number
of CUs continues to increase, the trend stabilizes. This occurs
because when the CUs are densely distributed, the UA V does
not need to spend excessive energy flying around the region.
Consequently, it can improve the duration for transmission.
C. The Tradeoff between C&S in ISAC-based UA V Trajecto-
ries
Fig. 9 aims to illustrate the performance tradeoff between
C&S by tuning the weighting factor η. It can be seen that there
exists a tradeoff between the total transmitted data and CRB.
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

14
100
Upper bound of CRB of x + CRB of y (m2)
3.5
4
4.5
5
5.5
6
Lower bound of total transmitted data (Gbits)
ISAC
ISAC+BA
=0.9 =0.7
=0.5
=0.3
=0.1
(a) The tradeoff between C&S, Etot = 40KJ
0 500 1000 1500
Lx (m)
0
500
1000
1500
Ly (m)
STs
CUs
Charging base
Trajectory
HPs (b) η = 0 .8, sensing with high priority, Etot =
60KJ
0 500 1000
Lx (m)
0
500
1000
1500
Ly (m)
STs
CUs
Charging base
Trajectory
HPs
(c) η = 0 .2, communication with high priority,
Etot = 60KJ
Fig. 9: Tradeoff between C&S performances ( Nstg = 60, M = 2 and K = 2).
The weighting factor has a more significant impact on sens-
ing compared to communication. Specifically, the CRB with
η = 0.1 is nearly 10 times higher than when η = 0.9, while
the total transmitted data only increases by approximately 0.6
Gbits in both “ISAC” and “ISAC+BA” when η decreases from
0.9 to 0.1. Fig. 9 (b) and (c) present the UA V trajectories with
different η. It can be observed that with a higher η, where the
sensing metric carries more weight in the objective function,
the UA V trajectory is more focused on optimizing sensing.
For example, in Fig. 9 (b) and (c), the UA V flies closer to
STs when η = 0.8, enabling more accurate measurements and
leading to an improved estimation performance.
At the end of the section, we discuss some practical aspects
focusing on the computational complexity of the proposed
MSTD approach. We observe that the complexity is primarily
determined by the number of stages and the number of
variables need to be optimized in each stage. Referring to
Algorithm 1 and 2, it is evident that Nstg impacts both the
total number of stages and the number of variables optimized
in each stage. Additionally, µ impacts the number of variables
optimized in each stage. Increasing Nstg means that energy
consumption in each stage is increased, resulting in fewer
stages, potentially reducing the optimization processing time
on repeating stages, but it simultaneously increases the number
of variables in each stage, potentially increasing the processing
time in each stage. On the other hand, smaller µ increases
the number of variables in each stage, but enhancing sensing
performance because of obtaining more distance measure-
ments. Therefore, it is an obvious tradeoff relationship existed
in 1) the values of parameters, i.e., Nstg and µ, 2) sensing
performance and 3) computational complexity, thus specific
experiments can be made in real scenarios based on different
C&S requirements, to discover the appropriate values for Nstg
and µ, seeking for a higher performance-to-complexity ratio.
VI. C ONCLUSION
In this paper, we have addressed the problem of UA V
trajectory design, bandwidth allocation and ST estimations in
an ISAC-based UA V scenario. Firstly, we proposed a multi-
stage trajectory design approach to assure accurate formulation
for UA V trajectory design. Then, we formulated a weighted
sum optimization problem to achieve a flexible performance
Fig. 10: Constraint (54).
tradeoff between C&S. We further developed an iterative
algorithm to address the formulated optimization problem.
The numerical results have demonstrated that the UA V energy
supply and the performance priority have significant impact on
C&S. Moreover, our ISAC scheme has shown considerable
improvements in C&S performances and energy efficiency
compared to single-functional UA V scenarios.
APPENDIX A
THE PROOF ABOUT THE FEASIBILITY OF {Sj, Vj}
SOLUTIONS AFTER CONSTRAINT (34 C) APPLIES SCA
Since we seek the local optimal solution of {Sj, Vj} in
P′1 (j) by following the ascent direction obtained via Q′′ (j),
it is necessary to prove that all available points belonging to the
ascent direction obtained after SCA can satisfy all constraints
in P′1 (j). We rewrite P′1 (j) as
max
{Sj ,Vj ,δj ,ξj }
f (Sj)
s.t. (1), (2), (34a), (34b), (42), (44) and (48) ,
∥vn,j∥2
v20 ≥ 1[δn,j]2 − ξn,j, n= 1, 2, ..., Nfj ,
[δn,j]2 ≥ ξn,j, n= 1, 2, ..., Nfj .
It is readily observed that the two constraints above need to
use SCA in Q′′ (j). Hence, we aim to demonstrate that in the
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

15
l-th iteration, all possible solutions of {Vj, δj, ξj} following
the ascent direction still fulfill this two constraints.
First of all, we split the first constraint into two sub
constraints as follows
∥vn,j∥2
v20 ≥ An,j, n= 1, 2, ..., Nfj , (54)
An,j ≥ 1[δn,j]2 − ξn,j, n= 1, 2, ..., Nfj . (55)
In Fig. 10, we assume that the region of ∥vn,j∥ satisfying con-
straint (54) in the l-th iteration is Za and Zb. After applying
the first-order Taylor expansion in the LHS of constraint (54),
the available region of ∥vn,j∥ in the l-th iteration is Zc. Since
the ascent direction is a part of Zc, and Zc is encompassed
by Zb, all possible solutions following the ascent direction
satisfies (54). Now we can prove that the first constraint in
P′1 (j) rewritten above can be addressed with SCA. The second
constraint has a similar proof, omitted here for brevity.
REFERENCES
[1] A. Liu, Z. Huang, M. Li, Y . Wan, W. Li, T. Han, et al , “A survey
on fundamental limits of integrated sensing and communication,” IEEE
Commun. Surveys Tuts. , Apr. 2021.
[2] Y . Cui, F. Liu, X. Jing and J. Mu, “Integrating sensing and communi-
cations for ubiquitous IoT: Applications, trends, and challenges,” IEEE
Network, vol. 35, no. 5, pp. 158-167, Oct. 2021.
[3] F. Liu, Y . Cui, C. Masouros, J. Xu, T. Han, Y . Eldar, et al , “Integrated
sensing and communications: Towards dual-functional wireless networks
for 6G and beyond,” IEEE J. Sel. Areas Commun. , vol. 40, no. 6, pp.
1728-1767, June 2022.
[4] O. B. Akan and M. Arik, “Internet of radars: Sensing versus sending
with joint radar-communications,” IEEE Commun. Mag. , vol. 58, no. 9,
pp. 13-19, Sept. 2020.
[5] X. Wang, Z. Fei, J. A. Zhang, J. Huang and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-UA V
networks,” IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660-2672, April
2021.
[6] P. Kumari, N. J. Myers and R. W. Heath, “Adaptive and fast com-
bined waveform-beamforming design for mmWave automotive joint
communication-radar,” IEEE J. Sel. Topics Signal Process. , vol. 15, no.
4, pp. 996-1012, June 2021.
[7] Y . Zeng, Q. Wu, and R. Zhang, “Accessing from the sky: A tutorial on
UA V communications for 5G and beyond,”in Proceedings of the IEEE ,
vol. 107, no. 12, pp. 2327-2375, Dec. 2019.
[8] Q. Wu, J. Xu, Y . Zeng, D. W. K. Ng, N. A. Dhahir, R. Schober, and A. L.
Swindlehurst, “A comprehensive overview on 5G-and-beyond networks
with UA Vs: From communications to sensing and intelligence,” IEEE
J. Sel. Commun. , vol. 39, no. 10, pp. 2912-2945, Oct. 2021.
[9] F. Liu, C. Masouros, A. P. Petropulu, H. Griffiths and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-Art, and the
road ahead,” IEEE Trans. Commun., vol. 68, no. 6, pp. 3834-3862, June
2020.
[10] T. Huang, N. Shlezinger, X. Xu, Y . Liu and Y . C. Eldar, “MAJoRCom:
A dual-function radar communication system using index modulation,”
IEEE Trans. Signal Process. , vol. 68, pp. 3423-3438, May 2020.
[11] M. Jamil, H. Zepernick and M. I. Pettersson, “On integrated radar and
communication systems using Oppermann sequences,” in Proc. IEEE
Mil. Commun. Conf. , Nov. 2008, pp. 1-6.
[12] X. Li, R. Yang, Z. Zhang and W. Cheng, “Research of constructing
method of complete complementary sequence in integrated radar and
communication,” in Proc. IEEE Int. Conf. Signal Process. , Nov. 2012,
pp. 1729-1732.
[13] P. Kumari, S. A. V orobyov and R. W. Heath, “Adaptive virtual waveform
design for millimeter-wave joint communication–radar,” IEEE Trans.
Signal Process., vol. 68, pp. 715-730, Nov. 2020.
[14] Y . Liu, G. Liao, J. Xu, Z. Yang and Y . Zhang, “Adaptive OFDM inte-
grated radar and communications waveform design based on information
theory,” IEEE Commun. Lett. , vol. 21, no. 10, pp. 2174-2177, Oct. 2017.
[15] Z. Xiao and Y . Zeng, “Waveform Design and Performance Analy-
sis for Full-Duplex Integrated Sensing and Communication,” IEEE
J. Sel. Areas Commun. , vol. 40, no. 6, pp. 1823-1837, June 2022.
10.1109/JSAC.2022.3155509.
[16] F. Liu, Y . Liu, A. Li, C. Masouros and Y . C. Eldar, “Cram ´er-Rao bound
optimization for joint radar-communication beamforming,” IEEE Trans.
Signal Process., vol. 70, pp. 240-253, Dec. 2017.
[17] Y . Zeng, R. Zhang, and T. J. Lim, “Wireless communications with un-
manned aerial vehicles: Opportunities and challenges,” IEEE Commun.
Mag.,vol. 54, no. 5, pp. 36-42, May 2016.
[18] A. Al-Hourani, S. Kandeepan, and S. Lardner, “Optimal LAP altitude
for maximum coverage,” IEEE Wireless Commun. Lett. , vol. 3, no. 6,
pp. 569–572, Dec. 2014.
[19] B. Li, C. Chen, R. Zhang, H. Jiang, and X. Guo, “The energy-efficient
UA V-based BS coverage in air-to-ground communications,” in Proc.
IEEE Workshop Sensor Array and Multichannel Signal Process. (SAM
Wkshps), Jul. 2018, pp. 578–581.
[20] H. He, S. Zhang, Y . Zeng, and R. Zhang, “Joint altitude and beamwidth
optimization for UA V-enabled multiuser communications,” IEEE Com-
mun. Lett. , vol. 22, no. 2, pp. 344-347, Feb., 2018.
[21] J. Sun and C. Masouros, “Deployment strategies of multiple aerial BSs
for user coverage and power efficiency maximization,” IEEE Trans.
Commun., vol. 67, no. 4, pp. 2981-2994, Apr. 2019.
[22] J. Sun and C. Masouros, “Drone positioning for user coverage maxi-
mization,” in Proc. IEEE Annu. Int. Symp. Pers., Indoor , Mobile Radio
Commun. (PIMRC) , Sep. 2018, pp. 318–322.
[23] I. Valiulahi, C. Masouros, “Multi-UA V deployment for throughput
maximization in the presence of co-channel interference”, IEEE Internet
Things J., vol. 8, no. 5, pp. 3605-3618, 1 March, 2021.
[24] Y . Ji, C. Dong, X. Zhu and Q. Wu, “Fair-energy trajectory planning for
cooperative UA Vs to locate multiple targets,” in Proc. IEEE Int. Conf.
Commun. (ICC) , May 2019, pp. 1-7.
[25] X. Jing, J. Sun and C. Masouros, “Energy aware trajectory optimization
for aerial base stations,” IEEE Trans. Commun., vol. 69, no. 5, pp. 3352-
3366, May 2021.
[26] Y . Zeng, J. Xu, and R. Zhang, “Energy minimization for wireless
communication with rotary-wing UA V ,”IEEE Trans. Wireless Commun.,
vol. 18, no. 4, pp. 2329 - 2345, Apr. 2019.
[27] M. Hua, Y . Wang, Z. Zhang, C. Li, Y . Huang, and L. Yang, “Power-
efficient communication in UA V-aided wireless sensor networks,” IEEE
Commun. Lett. , vol. 22, no. 6, pp. 1264–1267, Jun. 2018.
[28] L. He, P. Gong, X. Zhang and Z. Wang, “The bearing-only target
localization via the single UA V: Asymptotically unbiased closed-form
solution and path planning,” IEEE Access , vol. 7, pp. 153592-153604,
Nov. 2019.
[29] S. Xu, K. Doganc ¸ay and H. Hmam, “Distributed path optimization of
multiple UA Vs for AOA target localization,” in Proc. IEEE Int. Conf.
Acoust., Speech, Signal Process. (ICASSP) , Mar. 2016, pp. 3141-3145.
[30] K. Do ˘ganc ¸ay, “Single- and multi-platform constrained sensor path
optimization for angle-of-arrival target tracking,” in Proc. Eur . Signal
Process. Conf., Aug. 2010, pp. 835-839.
[31] K. Zhang and C. Shen, “UA V Aided Integrated Sensing and Communi-
cations,” in IEEE V eh. Technol. Conf. (VTC2021-Fall) , Sept. 2021, pp.
1-6.
[32] S. Zhang, H. Zhang, Z. Han, H. V . Poor and L. Song, “Age of
information in a cellular internet of UA Vs: Sensing and communication
trade-off design,” IEEE Trans. Wireless Commun. , vol. 19, no. 10, pp.
6578-6592, Oct. 2020.
[33] K. Meng, Q. Wu, S. Ma, W. Chen and T. Q. S. Quek, “UA V trajectory
and beamforming optimization for integrated periodic sensing and
communication,” IEEE Wireless Commun. Lett., vol. 11, no. 6, pp. 1211-
1215, June 2022.
[34] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming de-
sign for UA V-enabled integrated sensing and communication,” 2021,
arXiv:2110.02857.
[35] X. Jing, F. Liu and C. Masouros, “Path Design for Portable Access
Point in Joint Sensing and Communications under Energy Constraints”,
in Proc. IEEE Int. Conf. Acoust., Speech, Signal Process , Sept. 2022,
pp. 1-5.
[36] M. Letafati, H. Behroozi, B. H. Khalaj and E. A. Jorswieck, “Hardware-
Impaired PHY Secret Key Generation With Man-in-the-Middle Adver-
saries”, IEEE Commun. Lett. , vol. 11, no. 4, pp. 856-860, April 2022.
[37] M. Letafati, H. Behroozi, B. H. Khalaj and E. A. Jorswieck, “Deep
Learning for Hardware-Impaired Wireless Secret Key Generation with
Man-in-the-Middle Attacks”, in Proc. IEEE Global Telecommun. Conf. ,
Dec. 2021, pp. 1-6.
[38] Y . Zeng and R. Zhang, “Energy-Efficient UA V Communication with
Trajectory Optimization,” IEEE Trans. Wireless Commun. , vol. 16, no.
6, pp. 3747-3760, Jun., 2017.
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply. 

16
[39] Steven M. Kay, Fundamentals of statistical signal processing: Estima-
tion theory . Upper Saddle River, U.S.: Prentice Hall, 1993, pp. 15-67.
[40] Y . Yoon and M. Amin, “Spatial Filtering for Wall-Clutter Mitigation in
Through-the-Wall Radar Imaging,” IEEE Trans. Geosci. Remote Sens. ,
vol. 47, no. 9, pp. 3192-3208, Sept. 2009.
[41] F. Liu, W. Yuan, C. Masouros and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: communication served by sensing,”
IEEE Trans. Wireless Commun. , vol. 19, no. 11, pp. 7704-7719, Nov.
2020.
[42] Steven.M.Key, Fundamentals of statistical signal processing, volume II:
Detection theory . Upper Saddle River, U.S.: Prentice Hall PTR, 1993,
pp. 20-36.
[43] S. Boyd and L. Vandenberghe, Convex optimization. Cambridge, U.K.:
Cambridge Univ. Press, 2004.
[44] B. Li, N. Wu, H. Wang, P. Tseng and J. Kuang, “Gaussian message
passing-based cooperative localization on factor graph in wireless net-
works,” Signal Processing, vol. 111, pp. 1-12, June 2015.
[45] X. Zhang and L. Duan, “Energy-Saving Deployment Algorithms of UA V
Swarm for Sustainable Wireless Coverage,” IEEE Trans. V eh. Technol.,
vol. 68, no. 9, pp. 10320-10335, sept. 2020.
[46] K. Wang, X. Zhang, L. Duan and J. Tie, “Multi-UA V Cooperative
Trajectory for Servicing Dynamic Demands and Charging Battery,”
IEEE Trans. Mobile Comput. , vol. 22, no. 3, pp. 1599-1614, March
2023.
[47] X. Liu, Y . Liu, Z. Liu and T. S. Durrani, “Fair Integrated Sensing and
Communication For Multi-UA V Enabled Internet of Things: Joint 3D
Trajectory and Resource Optimization,” IEEE Internet Things J . (Early
access)
[48] B. Li, Q. Li, Y . Zeng, Y . Rong and R. Zhang, “3D Trajectory Opti-
mization for Energy-Efficient UA V Communication: A Control Design
Perspective,” IEEE Trans. Wireless Commun. , vol. 21, no. 6, pp. 4579-
4593, June 2022.
This article has been accepted for publication in IEEE Transactions on Wireless Communications. This is the author's version which has not been fully edited and 
content may change prior to final publication. Citation information: DOI 10.1109/TWC.2024.3396571
© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.

See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: University College London. Downloaded on May 14,2024 at 12:55:22 UTC from IEEE Xplore.  Restrictions apply.