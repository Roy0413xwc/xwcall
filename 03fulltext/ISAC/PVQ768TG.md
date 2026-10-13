---
title: "Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative ISAC in AAV Detection"
zotero_key: "PVQ768TG"
pdf_key: "EN5GSRVN"
doi: "10.1109/TVT.2025.3525980"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Joint Target Assignment and Resource Allocation for Multi-Base Station Cooperative ISAC in AAV Detection — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

7700 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY , VOL. 74, NO. 5, MA Y 2025
Joint Target Assignment and Resource Allocation for
Multi-Base Station Cooperative ISAC
in AA V Detection
Ruotong Li , Qixun Zhang , Member , IEEE, Dingyou Ma ,K a nY u , Member , IEEE, and Y uzhen Huang
Abstract—Integrated sensing and communication (ISAC) is a
foundational technology for sixth-generation (6 G) networks, with
networked ISAC enabling multiple distributed sensing nodes to
collaborate in target detection. This paper addresses the criti-
cal challenge of managing dynamic interference in cooperative
ISAC systems, focusing on fast-moving autonomous aerial vehicles
(AA Vs) operating in complex propagation environments. Rapid
AA V motion induces signiﬁcant Doppler shifts and ﬂuctuating in-
terference, leading to uneven signal quality and degraded detection
performance, particularly in high-interference zones. To tackle
this, we propose a fairness-based resource allocation framework
that prioritizes the weakest links by maximizing the minimum
radar sensing signal-to-interference-plus-noise ratio (SINR). We
formulate a joint optimization problem for ISAC beamforming and
target allocation, ensuring communication quality of service (QoS)
and base station (BS) power constraints. Although the problem
is non-convex, we develop an alternating optimization approach.
Optimal receive beamforming is derived using the generalized
Rayleigh quotient, while transmit beamforming and target assign-
ment are solved via Dinkelbach’s method, exploiting strong duality.
Numerical results demonstrate the proposed algorithm’s superi-
ority over benchmarks, achieving robust and equitable sensing
performance across AA Vs, even in dynamic, high-mobility scenar-
ios. These results highlight the potential of cooperative ISAC with
multiple BSs for reliable target detection and communication under
challenging conditions.
Index Terms—Integrated sensing and communication (ISAC),
network ISAC, beamforming optimization, target allocation.
I. I NTRODUCTION
T
HE emergence of sixth-generation (6 G) wireless networks
is being shaped by advances in smart technology and the
growing need for high-performance connectivity in autonomous
driving, digital manufacturing, and virtual environments [1].
These applications demand ultra-reliable, low-latency commu-
nication and high-precision sensing [2], positioning Integrated
Received 12 September 2024; revised 1 December 2024; accepted 6 December
2024. Date of publication 6 January 2025; date of current version 20 May 2025.
The review of this article was coordinated by Dr. Wee Kiat New.(Corresponding
author: Yuzhen Huang.)
Ruotong Li, Qixun Zhang, Dingyou Ma, and Kan Y u are with the Key Lab-
oratory of Universal Wireless Communications, Ministry of Education, Beijing
University of Posts and Telecommunications, Beijing 100876, China (e-mail:
liruotong@bupt.edu.cn; zhangqixun@bupt.edu.cn; dingyouma@bupt.edu.cn;
kanyu1108@126.com).
Y uzhen Huang is with the Academy of Military Sciences of PLA, Beijing
10091, China (e-mail: yzh_huang@sina.com).
Digital Object Identiﬁer 10.1109/TVT.2025.3525980
Sensing and Communications (ISAC) as a key technology in
the 6 G roadmap for IMT-2030. One of the key areas where
ISAC demonstrates potential is addressing challenges posed
by autonomous aerial vehicles (AA Vs). They are transforming
sectors like urban planning, entertainment, and logistics, offer-
ing advantages such as exceptional maneuverability, ﬂexibility,
intelligence, and broad coverage. However, their increasing
presence, particularly in sensitive or restricted areas, raises sig-
niﬁcant security and privacy concerns that need to be addressed.
Given the extensive coverage of existing mobile communication
infrastructures, ISAC presents signiﬁcant potential for effective
AA V detection. By facilitating the simultaneous transmission of
data and environmental sensing, ISAC enhances spectrum ef-
ﬁciency while enabling real-time, large-scale AA V monitoring.
This capability is crucial for strengthening situational awareness
and improving security, offering critical solutions for a wide
range of applications.
To achieve complete ISAC, research has been conducted from
various aspects, such as the basic theory of ISAC [3], waveform
design [4], signal processing [5] and transmit beamforming
optimization [6].I n [6], authors considered a full-duplex (FD)
capability for ISAC, an effective algorithm was developed to
optimize the base stations (BSs) transmit beamforming and the
user transmit power. The authors in[7] studied a secure downlink
ISAC beamforming problem, the BS combines the transmit con-
ﬁdential information signals with additional dedicated sensing
signals, which play a role of artiﬁcial noise (AN) for degrading
the qualities of eavesdropping channels. In [8], authors studied
the transmit beamforming in a downlink ISAC system, where a
single BS performs downlink communication and target sensing
at the same time. In [9], authors studied an ISAC system with
downlink communication and multi-static sensing for single
target detection in a cloud radio access network architecture,
a maximum a posteriori ratio test detector is derived to detect
the target using the reﬂected signal. In vehicle-to-infrastructure
(V2I) ISAC network, beamforming is highly depended on the
availability of accurate channel tracking which requiring large
training overhead and computational complexity, authors in[10]
considered a deep learning (DL) approach based beamforming
problem, the features of historical channels were utilized to pre-
dict the beamforming matrix. To improve resource utilization,
authors in [11] investigated the energy-efﬁcient channel sharing
aided ISAC with transmit and receive beamforming design.
0018-9545 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and similar technologi es.
Personal use is permitted, but republication/redistribution requires IEEE permission. See https://www.ieee.org/publications/rights/index. html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT TARGET ASSIGNMENT AND RESOURCE ALLOCA TION FOR MULTI-BASE STA TION COOPERA TIVE ISAC IN AA V DETECTION 7701
The above works take into account the case where there are
signiﬁcant line-of-sight (LoS) links between the sensing targets
and the BSs. However, ISAC signal may suffer from various
practical limitations, such as uncontrollable propagation. There-
fore, some prior works tried to exploit reconﬁgurable intelligent
surface (RIS) aided ISAC, to create a directional path to reﬂect
the source signals towards the destinations by designing the
phase shifts of passive reﬂecting elements [12], [13], [14].
Works above focus on ISAC in a single BS scenario where an
ISAC transceiver performs wireless communication and radar
sensing [8], [12]. While this approach provides high sensing ac-
curacy, it is limited in long-range or blind-area detection, making
it less effective for tracking dynamic AA Vs across multiple BSs.
In contrast, bistatic sensing enables cooperative ISAC by allow-
ing one BS to transmit signals while neighboring BSs receive
reﬂections. This cooperative framework leverages spatial diver-
sity, improving detection range and accuracy through multi-BS
collaboration. By combining monostatic and bistatic sensing,
cooperative ISAC emerges as a promising solution for seamless
AA V detection over wide areas, enhancing performance with
multi-angle and multi-path signal integration.
Cooperative ISAC with multiple BSs is expected to bring
various advantages in terms of larger sensing coverage, richer
sensing information, and better sensing performance[15]. More-
over, it signiﬁcantly reduces the searching space for channel
estimation, helping to improve predictive beam tracking for
fast-moving targets [16]. Despite the various beneﬁts from co-
operative ISAC with multiple BSs, there are also challenges
in coordinated beamforming optimization, resource allocation,
and interference management to trade off between cooperative
sensing and communication performance [17]. Recent studies
have explored such challenges. For instance, the work in [18]
developed a fairness-aware multi-device ISAC framework to op-
timize beamforming and time allocation across devices, ensur-
ing sensing quality and communication fairness. In[19],aA A V -
enabled ISAC system was proposed with joint optimization of
AA V trajectories and resource allocation to enhance localization
accuracy and communication efﬁciency. Another study [20]
focused on multi-static ISAC networks in a cloud-RAN setting,
proposing a joint beamforming and ﬁltering design to maximize
radar SINR while satisfying communication requirements. Ad-
ditionally, authors in[21] considered the joint design of transmit
and receive beamforming vectors for ISAC systems between two
BSs, highlighting the SINR trade-off between target detection
and user communication. In [22], a cooperative ISAC system
was studied to characterize and optimize the performance trade-
off between communication and direct localization, showing
the beneﬁts of networked ISAC. In [23], coordinated power
control among ISAC transmitters was examined to minimize
total transmit power under sensing and communication con-
straints. In [24], a two-phase sensing framework was proposed
to localize targets by separately estimating their ranges and
positions. In [25], a multi-antenna networked ISAC system was
developed with optimized coordinated transmit beamforming,
addressing both synchronized and unsynchronized BS scenarios.
These works advanced interference analysis in coopera-
tive ISAC systems by studying its impact on multiple BS
performance, focusing on trade-offs between communication
and sensing through optimized beamforming, time allocation,
and power control. However, current cooperative ISAC research
typically assumes static or slow-moving targets, relying on sta-
ble signal paths. This simpliﬁes interference management and
resource allocation but falls short in scenarios involving fast-
moving AA Vs. The rapid movement of AA Vs induces signiﬁcant
Doppler shifts, leading to frequency offsets and changes in the
propagation paths. This results in ﬂuctuating interference levels
and uneven signal quality across AA Vs, with some AA Vs in
high-interference zones suffering from degraded performance.
In such dynamic environments, it becomes critical to ensure
that all AA Vs, especially those in areas with high interference,
maintain a certain minimum level of SINR. However, current
research primarily focuses on optimizing overall system perfor-
mance, often prioritizing aggregate sensing and communication
efﬁciency. This emphasis on total system metrics tends to over-
look the performance of individual AA Vs in high-interference
zones, leaving their sensing capabilities insufﬁciently addressed.
To achieve this, a fairness-based optimization approach, such as
max-min SINR optimization, is necessary to provide equitable
SINR to all AA Vs by prioritizing the weakest links, ensuring
that even those in the most challenging interference conditions
receive adequate resources.
Therefore, our research focuses on managing interference
for detecting multiple fast-moving AA Vs in cooperative ISAC
systems, accounting for complex direct and scattered signal
paths due to AA V movement. To address the challenges of
dynamic interference, we propose a fairness-based framework
that integrates monostatic and bistatic sensing modes across
multiple BSs, prioritizing the sensing needs of individual AA Vs,
especially those in high-interference zones. This integration
takes advantage of the channel information between multiple
BSs and the targets, enabling dynamic adaptation to varying
propagation environments. Our contributions are summarized
as follows.
r We propose a cooperative ISAC framework where multiple
BSs simultaneously perform sensing and communication
for multiple fast-moving AA Vs, accounting for the com-
plex and dynamic channel conditions induced by AA V mo-
bility. The reﬂected radar sensing signal is formulated using
the downlink communication signal for sensing, while
linear receive beamforming is employed to derive the SINR
for AA V sensing. A joint optimization problem is then
formulated, incorporating AA V assignment, BS transmit
beamforming, and receive beamforming for each sensing
AA V , with the objective of maximizing the minimum radar
sensing SINR under these challenging conditions.
r To tackle the formulated mixed-integer programming prob-
lem, the original problem is decomposed into three sub-
problems: receive beamforming, transmit beamforming,
and AA V assignment. The closed-form optimal solution
for the receive beamforming subproblem can be derived
from the generalized Rayleigh quotient, given the trans-
mit beamforming and AA V assignment. Once the receive
beamforming is determined, Dinkelbach’s method is ap-
plied to handle the fractional objective function. Utilizing
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

7702 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 74, NO. 5, MA Y 2025
Fig. 1. System model for integrated sensing and communication.
this approach, the Lagrange duality method is employed to
derive the optimal solutions for transmit beamforming and
AA V assignment. Finally, an efﬁcient algorithm is designed
to iteratively solve these three subproblems, leading to the
solution of the original joint optimization problem.
r We evaluate the proposed algorithm by comparing its
performance with benchmarks in simulations based on
a revised channel model that considers complex inter-
ference from fast-moving AA Vs. The cooperative ISAC
scheme outperforms in multi-AA V sensing, ensuring even
the lowest-SINR AA V meets a minimum threshold. This
framework improves SINR fairness and sensing quality,
effectively handling interference from AA V movement and
ensuring reliable sensing in dynamic conditions.
The rest of the paper is organized as follows. In Section II,w e
review the related works. In Section III, we present the system
model and formulate the optimization problem. The proposed
cooperative multi-BSs scheduling algorithm is introduced in
Section IV. Section V evaluates the performance of the proposed
algorithm by numerical simulations. Finally, we conclude the
paper in Section VI.
Notations: Boldface lower-case and upper-case letters indi-
cate column vectors and matrices, respectively. (·)H and (·)−1
denote the transpose-conjugate and inverse operations, respec-
tively. C denotes the sets of complex numbers. |·| denotes
the absolute value of a scalar. E denotes expectation operation.
A ≻ 0 implies that A is positive semideﬁnite. A ⊁ 0 denotes
thatA is a semideﬁnite and singular matrix.
II. S YSTEM MODEL
In our scenario, the AA Vs represent unauthorized or uncoop-
erative aerial vehicles, that may pose a security threat or require
surveillance in an area. The goal is to leverage the BSs to detect
these AA Vs using reﬂected signals. As shown in Fig.1, the con-
sidered ISAC scenario consists ofJ synchronized BSs,K Com-
munication users (CUs) and I AA V sensing targets, denoted by
J = {1, 2,...,J},K= {1, 2,...,K} andI= {1, 2,...,I}. Each BS
equips with a uniform planar arrays (UPAs), Mt = Mtx ×Mty
transmit antennas and Mr = Mrx ×Mry receive antennas. To
TABLE I
SUMMARY OF NOT A TIONS
enable ISAC, each BS can communicate with multiple CUs and
sense multiple AA Vs at the same time. Besides, it is assumed that
each CU is pre-allocated to the associated BS. LetKj = {1, 2,...,
Kj } denotes the set of CUs associating with BS j, andkj refers
to thekth CU which associates with BSj. AA Vs move within the
coverage area of these multiple BSs, making continuous detec-
tion and tracking challenging due to their dynamic positions as
they traverse different areas of coverage. Given that our primary
focus is on AA V detection rather than the estimation of target
state parameters (such as velocity or trajectory), we consider
these two aspects as sequential processes in time. The target
position, therefore, can be treated as a known condition with
slight inaccuracies during the detection phase, based on either
the position information obtained from the previous parameter
estimation or predictions derived from historical data.
In our framework, it is crucial to allocate resources efﬁciently
for accurate AA V detection. Rather than all BSs contributing
resources to sense each AA V uniformly, which would lead to
inefﬁcient use of resources, we assign each AA V to a speciﬁc BS
for receiving the sensing signals. The assigned BS is responsible
for receiving both the monostatic signals (direct reﬂections) and
the bistatic signals (indirect reﬂections from neighboring BSs)
related to the AA V and using these signals to perform target
detection. This approach ensures that the BS most capable of
delivering high SINR is primarily responsible for sensing the tar-
get, optimizing the detection process by concentrating resources
on the most relevant BSs while leveraging the additional bistatic
signals from nearby BSs. To implement this, we introduce the
AA V -BS assignment variableaj,i, which determines the speciﬁc
BS responsible for receiving and processing the sensing signals
for each AA V . Speciﬁcally,aj,i ∈{ 0, 1} is a binary variable that
indicates whether BSj is assigned to receive the sensing signals
for AA Vi.I f aj,i = 1, it indicates that BS j is selected to sense
AA Vi by receiving both the monostatic and bistatic signals. If
aj,i = 0, BS j is not involved in the reception and detection of
AA Vi.
A. Signal Model
First, we focus on the downlink signal model. The transmit
signal of BS j′ can be expressed as:
xj′ = Wj′sj′, (1)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT TARGET ASSIGNMENT AND RESOURCE ALLOCA TION FOR MULTI-BASE STA TION COOPERA TIVE ISAC IN AA V DETECTION 7703
where Wj′ =[ wj′,1,wj′,2,..., wj′,Kj′ ] ∈ CMt×Kj′ denotes
transmit beamforming of BS j′ for CUs, and sj′ =
[sj′,1,...,s j′,Kj′ ]T ∈ CKj′×1 denotes communication symbol
vectors. Without loss of generality, we make the assumption
that the communication symbols from different CUs are un-
correlated, namely E[|sj′,kj′ |2]= 1 and E[sj′,kj′ sj′, ˆkj′ ]= 0f o r
ˆkj′ ∈K and ˆkj′ ⁄= kj′ .
B. Communication Model
The received signal at CU kj′ that attached to BS j′ is
expressed as:
ykj′ = hHj′,kj′ wj′,kj′ sj′,kj′ +
Kj′∑
ˆkj′⁄=kj′
hHj′,kj′ wj′, ˆkj′ sj′, ˆkj′
+
J∑
l⁄=j′
Kl∑
kl=1
hHl,kj′ wl,klsl,kl +nk, (2)
wherehj′,kj′ ∈ CMt×1 andhl,kj′ ∈ CMt×1 denote the commu-
nication channel from BS to CU kj′ respectively. The ﬁrst part
of (2) is the desired communication signal from BSj′ to CUkj′ ,
the second part is the intracell interference from other CUs and
third part is intercell interference signal from other BSs. The last
parts is additive white Gaussian noise (AWGN) at the CU kj′ ,
wherenk ∼CN (0,σ 2n).
Correspondingly, the SINR at CU kj′ attached to BS j′ can
be expressed as:
γkj′ =
|hHj′,kj′ wj′,kj′ |2
Ij′, ˆkj′ +Il,kl +σ2n, (3)
whereIj′, ˆkj′ ,Il,kl are intracell inteference and intercell intefer-
ence, which can be expressed as
Ij′, ˆkj′ =
Kj′∑
ˆkj′⁄=kj′
|hHj′,kj′ wj′, ˆkj′ |2, (4)
Il,kl =
J∑
l⁄=j′
Kl∑
kl=1
|hHl,klwl,kl|2. (5)
C. Sensing Model
According to [26] and [27], the exact target direction can be
previously estimated for designing the transmit signal to detect
the target. The received reﬂected signal at BSj can be expressed
as
yj =
J∑
j′=1
I∑
i=1
βj′,j,iar(φj,i,θj,i)aHt (ϕj′,i,ϑj′,i)xj′
+
J∑
j′=1
GHj′,jxj′ +nr, (6)
where nr[l] is the receiver noise at receiving BS j, nr[l] ∼
CN(0,σ 2n). Gj′,j ∈ CMt×Mr denotes the direct channel from
BS j′ to j.
The reﬂection coefﬁcient βj′,j,i for the path from the trans-
mitting BSj′ to the receiving BSj via the AA V , which includes
the round-trip path loss and the Radar Cross Section (RCS)σrcs ,
is derived from the radar range equation [28] as:
βj′,j,i =
√
λ2σrcs
(4π)3d21d22, (7)
where λ represents wavelength, d1, d2 represent the distance
from transmitting BS to AA V and from AA V to receiving BS.
Assuming the antennas at the BSs are half-wavelength-spaced,
the antenna array response vector for the azimuth angle and
elevation angle, denoted by
ar(φj,i,θj,i)=[ 1,...,e j2πsinθj,i(mtx cosφj,i+mty sinφj,i),
...,e j2πsinθj,i(Mtx cosφj,i+Mty sinφj,i)]H, (8)
at(ϕj′,i,ϑj′,i)=[ 1,...,e j2πsinϑj′,i(mtx cosϕj′,i+mty sinϕj′,i),
...,e j2πsinϑj′,i(Mtx cosϕj′,i+Mty sinϕj′,i)]H,
(9)
wheremtx ∈ [1,Mtx] andmty ∈ [1,Mty] are antenna index.
In the cooperative ISAC scenario, BS j receives reﬂected
sensing signal from multiple BSs via multiple AA Vs. Therefore,
to capture the desired signal of a AA Vi, a receive beamforming
ﬁlter uj,i ∈ CMr×1 is applied on the received sensing signal
y [28]. Consider the premise of sensing is that the reﬂected
signal can be detected, sensing signal strength usually has a
positive correlation effect on the sensing accuracy and detection
probability [29]. Therefore, we adopt SINR of the received
sensing signal as the sensing performance. Then, based on (6),
the radar output signal SINR for targeti at BSj can be expressed
as
γj,i =
aj,iE{| ∑Jj′=1 βj′,j,iuHj,iAj′,j,ixj′|2}
Γj,i
, (10)
where Aj′,j,i = ar(φj,i,θj,i)aHt (ϕj′,i,ϑj′,i).I n (10), Γj,i de-
notes the total interference for sensing AA Vi at BSj, and it can
be expressed as
Γj,i = E
⎧
⎨
⎩|
J∑
j′=1
uHj,iGHj′,jxj′|2
⎫
⎬
⎭
/bracehtipupleft /bracehtipdownright/bracehtipdownleft /bracehtipupright
direct channel interference from other BSs
+E{|uHj,inr|2}/bracehtipupleft /bracehtipdownright/bracehtipdownleft /bracehtipupright
noise
+E
⎧
⎨
⎩|
I∑
i′⁄=i
J∑
j′=1
βj′,j,i′uHj,iAj′,j,i′xj′|2
⎫
⎬
⎭
/bracehtipupleft /bracehtipdownright/bracehtipdownleft /bracehtipupright
interference from other AA Vs’
. (11)
D. Problem F ormulation
In this section, we address the challenge of multi-AA V sensing
by focusing on maximizing the minimum received sensing signal
SINR at the receiving BS, while adhering to constraints on
communication SINRs at CUs and the power budget of BSs.
In multi-AA V sensing scenarios, it is essential to ensure that
all AA Vs meet a baseline level of performance, as failing to
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

7704 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 74, NO. 5, MA Y 2025
detect even a single AA V could compromise the overall system’s
reliability.
To meet this requirement, we adopt the max-min fairness
criterion. This approach ensures that even the weakest sensing
link achieves a sufﬁcient SINR level, which is particularly
important when reliable detection across all AA Vs is critical. By
maximizing the minimum SINR, we aim to maintain adequate
detection performance for every AA V , thereby increasing the
likelihood of reliable multi-AA V detection. Moreover, the max-
min criterion strengthens the system’s robustness. In practical
deployments, factors such as environmental variations, target
mobility, or interference can signiﬁcantly affect channel condi-
tions. By prioritizing the performance of the weakest link, the
system becomes more resilient to these ﬂuctuations, ensuring
stable and reliable performance under varying conditions.
The problem is formulated as a joint optimization of
AA V assignment variables aj,i, the BS transmit beamform-
ing {wj′,kj′ }j′∈J,kj′∈Kj′ and the receive beamforming vectors
{uj,i}j∈J,i∈I , which is given by
P1 :m a x
aj,i,wj′,kj′ ,uj,i
min
i∈I
γj,i (12a)
s.t. γkj′ ≥ γmin,∀j′ ∈J ,kj′ ∈K j′, (12b)
Kj′∑
kj′=1
‖wj′,kj′ ‖2 ≤ P0,∀j′ ∈J ,kj′ ∈K j′, (12c)
aj,i ∈{ 0, 1},
J∑
j=1
aj,i = 1,∀j ∈J ,i ∈I , (12d)
where γmin is the minimum required SINR threshold for CUs
andP0 is the maximum transmit power per BS.
III. S OLUTION OF THE OPTIMIZA TIONPROBLEM
The optimization problem is a non-convex mixed-integer
program due to the multiplication of the beamforming matrix
with AA V assignment matrix in objective. Besides, the fractional
structure of the objective function also leads to a non-convex
optimization problem, which is difﬁcult to solve. Therefore, a
transformation of the original problem is necessary. The trans-
formation of the original problem is composed of the following
steps:
1) Receive beamforming optimization subproblem: In this
subproblem, the transmit beamforming matrix and AA V
assignment matrix are given. Then, the original problem
is only depends on uj,i, and the transformed problem can
be solved by the generalized Rayleigh quotient.
2) Transmit beamforming optimization subproblem: In this
subproblem, we ﬁrst utilize the Dinkelbach’s method to
transform the fractional structure of the original problem,
then the Lagrange duality method is leveraged to obtain
the optimal transmit beamforming matrix.
3) AA V assignment optimization subproblem: Based on the
optimized transmit and receive beamforming variables,
the AA V assignment variable is optimized according to
the highest SINR.
A. Receive Beamforming Optimization Subproblem
Given transmit beamforming matrix and AA V assignment
matrix, the receive beamforming matrix only depends on the
objective. As a result, we optimize the receive beamforming
matrix through the following optimization criterion:
P2 :max
uj,i
min
i∈I
uHj,i
(∑J
j′=1 β2j′,j,iAj′,j,iQAHj′,j,i
)
uj,i
uHj,iBuj,i , (13)
where B denotes the interference from other AA Vs and direct
channel interference from other BSs, Q denotes the covariance
matrix of the downlink ISAC signal, which can be expressed as
B =
I∑
i′⁄=i
J∑
j′=1
β2j′,j,i′Aj′,j,i′QAHj′,j,i′ +
J∑
j′=1
GHj′,jQGj′,j
+σ2nIMr, (14)
Q = E
{
|xj′xHj′ |} =
Kj′∑
kj′=1
wj′,kj′ wHj′,kj′ . (15)
The objective (13) is to maximize the SINR of the received
signal, which is typically expressed as a ratio of quadratic
forms: one representing the desired signal power and the other
representing the interference and noise power:
γj,i = uHj,iRsig,iuj,i
uHj,iRint,iuj,i , (16)
whereRsig,i andRint,i denote the covariance matrices associated
with the desired signal and interference-plus-noise, respectively.
This form precisely matches the classical deﬁnition of a
generalized Rayleigh quotient, whose optimization can be re-
formulated as an eigenvalue problem:
u∗j,i =a r gm a xuj,i uHj,iRsig,iuj,iuHj,iRint,iuj,i . (17)
The optimal solution to this problem is the eigenvector cor-
responding to the largest eigenvalue of the matrix R−1int,iRsig,i,
providing a closed-form solution that avoids complex iterative
algorithms. This approach is computationally efﬁcient and guar-
antees maximum SINR under interference and noise conditions,
thus optimizing sensing performance. Additionally, the gener-
alized Rayleigh quotient formulation reduces the complexity of
the original non-convex problem, transforming it into a more
tractable form. This makes it particularly effective for coop-
erative sensing and communication environments, where both
signal and interference structures are complex.
Therefore, given the transmit beamforming matrix and AA V
assignment matrix, we have the following proposition.
Proposition 1: The optimal solution to the receive beamform-
ing optimization problem (13) can be given by
u∗j,i = Vmax
⎛
⎝B−1
⎛
⎝
J∑
j′=1
β2j′,j,iAj′,j,iQAHj′,j,i
⎞
⎠
⎞
⎠, (18)
where Vmax(H) denotes the eigenvector corresponding to the
maximum eigenvalue of the matrix H.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT TARGET ASSIGNMENT AND RESOURCE ALLOCA TION FOR MULTI-BASE STA TION COOPERA TIVE ISAC IN AA V DETECTION 7705
Proof: See Appendix A.
B. Transmit Beamforming Optimization Subproblem
Because aj,i is a 0-1 integer variable, we ﬁrst relax aj,i as
a continuous variable aj,i ∈ [0, 1]. Given the optimal receive
beamforming matrix and AA V assignment variable, the transmit
beamforming subproblem can be expressed as
P3 :m a x
wj′,kj′
min
i∈I
aj,i
∑J
j′=1
∑Kj′
kj′=1 β2j′,j,iwHj′,kj′ Cj,iwj′,kj′
∑J
j′=1
∑Kj′
kj′=1 wHj′,kj′ Dj,iwj′,kj +Ej,i
(19a)
s.t.γkj′ ≥ γmin,∀j′ ∈J ,kj′ ∈K j′, (19b)
Kj′∑
kj′=1
‖wj′,kj′ ‖2 ≤ P0,∀j′ ∈J ,kj′ ∈K j′, (19c)
whereCj,i, Dj,i,Ej,i can be expresses as
Cj,i = AHj′,j,iuj,iuHj,iAj′,j,i, (20)
Dj,i = Gj′,jujiuHjiGHj′,j + ∑
i′⁄=i
β2j′,j,i′AHj′,j,i′uj,iuHj,iAj′,j,i′,
(21)
Ej,i = uHj,iσ2nIMruj,i. (22)
In AA V sensing scenarios, AA Vs have high mobility, re-
quiring the system to quickly adapt to frequently changing
environments. This necessitates not only rapid computation
of beamforming strategies but also providing real-time opti-
mization results under limited computational resources. Our
optimization problem P3 aims to maximize the SINR, with
the objective function typically represented as a fractional form
of signal power over interference-plus-noise power, which is
generally non-convex and complex to solve directly [30], [31].
Additionally, the constraints of the optimization problem are
nonlinear functions, further complicating the problem.
To overcome these challenges, we employ the Dinkelbach
method [32], which is well-suited for solving this type of op-
timization problem. The Dinkelbach algorithm iteratively ap-
proximates the optimal solution, progressively moving closer
to the global optimum with each iteration, making it highly
efﬁcient for resource allocation in cooperative sensing systems.
Additionally, the Dinkelbach method can handle nonlinear con-
straints without requiring linearization of the objective function,
offering greater ﬂexibility and accuracy in addressing nonlinear
optimization problems. Its efﬁcient solution capability allows for
rapid optimization even under limited computational resources,
thereby meeting the real-time requirements of AA V sensing.
Motivated by Dinkelbach’s method, the non-convexity of the
subproblem P3 can be transformed into a tractable problem,
which is given in Lemma 1.
Lemma 1: The optimal solution of subproblem P3 can be
obtained if and only if the following equation holds:
max
wj′,kj′
min
i∈I
aj,i(fN(wj′,kj′ )−η⋆fD(wj′,kj′ ))
=m i n
i∈I
aj,i(fN(w∗j′,kj′ )−η⋆fD(w∗j′,kj′ )) =0, (23)
where η⋆ is the optimal non-negative parameter. To represent
the objective function in P3, the numerator and denominator
are denoted by fN(aj,i,wj′,kj′ ) and fD(wj′,kj′ ), respectively.
The numerator fN(aj,i,wj′,kj′ ) is expressed as:
fN(aj,i,wj′,kj′ )=
J∑
j′=1
Kj′∑
kj′=1
β2j′,j,iwHj′,kj′ Cj,iwj′,kj′ , (24)
while the denominator fD(wj′,kj′ ) is given by:
fD(wj′,kj′ )=
J∑
j′=1
Kj′∑
kj′=1
wHj′,kj′ Dj,iwj′,kj +Ej,i. (25)
These equations deﬁne the objective function, with the nu-
merator focusing on the weight vector wj′,kj′ and the channel
characteristics, and the denominator accounting for interference
and noise terms. The proof of Lemma 1 can be obtained from
the generalized fractional programming theory [33].
Based on Lemma 1, problem P3 can be transformed into the
following problem:
P4 :m a x
wj′,kj′
min
i∈I
aj,i(fN(wj′,kj′ )−ηfD(wj′,kj′ ))
s.t. (19b)− (19c). (26)
By introducing an auxiliary variable Υ, problem P4 can be
transformed as
P5 :m i n
wj′,kj′ ,Υ
−Υ (27a)
s.t.aj,i(fN(wj′,kj′ )−ηfD(wj′,kj′ )) ≥ Υ,∀i ∈I ,j ∈J
(19b)–(19d). (27b)
Although P5 is more tractable, it is still a non-convex
quadratic problem. Thus, in order to get an optimal solution,
we leverage Lagrangian dual method to analyze the optimal
solution of problem P5 with some strong duality conditions.
The Lagrangian function of P5 can be expressed as (28) shown
at the bottom of the next page, where δ = {δj,i}j∈J,i∈I , α =
{αj′,kj′ }j′∈J,kj′∈Kj and ζ = {ζj′}j′∈J are dual variables. Π is
given by
Π =
−
J∑
j=1
I∑
i=1
δj,iaj,iβ2j′,j,iCj,i +
J∑
m=1
Km∑
km=1
αm,kmhj′,kmhHj′,km
+
J∑
j=1
I∑
i=1
δj,iaj,iηDj,i −αj′,kj′
(
1+ 1γmin
)
hj′,kj′ hHj′,kj′
+ζj′IMr. (29)
Therefore, the dual function is then given by
g(δ,α,ζ)= i n f
wj′,kj′
L(Υ,wj′,kj′ ,δ,α,ζ). (30)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

7706 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 74, NO. 5, MA Y 2025
To guarantee the Lagrangian dual function (28) is not un-
bounded to inﬁnity, it is clear thatΠ ≽ 0 and ∑Jj=1 ∑Ii=1 δj,i −
1 ≽ 0 should be satisﬁed. Consequently, the dual problem can
be expressed as
P6 :
max
δ,α,ζ
J∑
j′=1
Kj′∑
kj′=1
αj′,kj′ σ2n +
J∑
j=1
I∑
i=1
δj,iaj,iηuHj,iσ2nIMruj,i
−
J∑
j′=1
ζj′P0 (31a)
s.t. Π ≽ 0,∀j′ ∈ J,∀kj′ ∈ Kj′, (31b)
J∑
j=1
I∑
i=1
δj,i − 1 ≽ 0. (31c)
Strong duality always holds for convex optimization prob-
lem with Slater’s condition, but it is difﬁcult for non-convex
optimization problem. However, the strong duality can also be
obtained for non-convex problem under some conditions [34].
To analyze the strong duality, the following theorems clarify the
relationship between the existence of a saddle point and strong
duality.
The saddle point (Υ⋆,w⋆j′,kj′ ,δ⋆,α⋆,ζ⋆) for the Lagrangian
functionL(Υ,wj′,kj′ ,δ,α,ζ) can be deﬁned to satisfy follow-
ing condition
L(Υ⋆,w⋆j′,kj′ ,δ,α,ζ) ≤L (Υ⋆,w⋆j′,kj′ ,δ⋆,α⋆,ζ⋆)
≤L (Υ,wj′,kj′ ,δ⋆,α⋆,ζ⋆). (32)
Theorem 1: [34] Denote p⋆, d⋆ the optimal value of the
non-convex quadratic problem and the dual problem re-
spectively, if (Υ⋆,w⋆j′,kj′ ,δ⋆,α⋆,ζ⋆) is a saddle point for
the function L(Υ,wj′,kj′ ,δ,α,ζ), then strong duality d⋆ =
p⋆ holds. Conversely, if d⋆ is ﬁnite with (δ⋆,α⋆,ζ⋆)=
argmax δ,α,ζ≥0 g(δ,α,ζ), and the original problem has an
optimal solution at (Υ⋆,w⋆j′,kj′ ), then (Υ⋆,w⋆j′,kj′ ,δ⋆,α⋆,ζ⋆)
is a saddle point of L(Υ,wj′,kj′ ,δ,α,ζ).
Theorem 2: [35] The existence of a saddle point of
L(Υ,wj′,kj′ ,δ,α,ζ) is equivalent to the following con-
dition: there exists (δ⋆,α⋆,ζ⋆) such that the function
L(Υ,wj′,kj′ ,δ⋆,α⋆,ζ⋆) is convex and has a minimizer
(Υ⋆,w⋆j′,kj′ ) satisfying
δ⋆j,i(Υ−aj,i(fN(w⋆j′,kj′ )−ηfD(w⋆j′,kj′ )) =0, (33)
Υ−aj,i(fN(w⋆j′,kj′ )−ηfD(w⋆j′,kj′ ) ≤ 0, (34)
α⋆j′,kj′ (γmin −γkj′ (w⋆j′,kj′ )) =0, (35)
γmin −γkj′ (w⋆j′,kj′ ) ≤ 0, (36)
ζ⋆j′
⎛
⎝
Kj′∑
kj′=1
‖w⋆j′,kj′ ‖2 −P0
⎞
⎠ = 0, (37)
‖w⋆j′,kj′ ‖2 −P0 ≤ 0. (38)
The proof of the theorem can be easily extended from the
deduction of [35] with multiple constraints.
Therefore, to prove the strong duality for a non-convex
quadratic optimization problem and obtain the optimal solution
from dual method, we need to ﬁnd a saddle point satisfying
Theorem 2.
Since the dual problem P6 is convex with respect
to Lagrangian multipliers, its optimal solution (δ⋆,α⋆,ζ⋆)
can be obtained from standard convex optimization tech-
nique or the interior point method. Consider Π deﬁned
in (29) is positive semi-deﬁnite to guarantee the ﬁnite
of the dual function (28), the Lagrangian function in
(27) is proved to be convex in {wj′,kj′ }j′∈J,kj′∈Kj′ and
Υ. Therefore, it is left to ﬁnd Υ,{wj′,kj′ }j′∈J,kj′∈Kj′ ∈
argminΥ,wj′,kj′ L(Υ,wj′,kj′ ,δ⋆,α⋆,ζ⋆).
If Π ≻ 0, it means Π is full rank and the eigenvalues of it
are all positive, therefore the null space of Π will be a zero
L(Υ,wj′,kj′ ,δ,α,ζ)=
J∑
j=1
I∑
i=1
δj,i
⎛
⎝Υ−aj,i
J∑
j′=1
Kj′∑
kj′=1
β2j′,j,iwHj′,kj′ Cj,iwj′,kj′ +ηaj,i
⎛
⎝
J∑
j′=1
Kj′∑
kj′=1
wHj′,kj′ Dj,iwj′,kj
+uHj,iσ2nIMruj,i
⎞
⎠
⎞
⎠+
J∑
j′=1
Kj′∑
kj′=1
αj′,kj′
⎛
⎜⎜⎜⎝σ2n + J∑m=1 Km∑km=1
(m,km)⁄=(j′,kj′)
wHm,kmhm,kj′ hHm,kj′ wm,km − wHj′,kj′ hj′,kj′ hHj′,kj′ wj′,kj′γmin
⎞
⎟⎟⎟⎠
+
J∑
j′=1
ζj′
⎛
⎝
Kj′∑
kj′=1
wHj′,kj′ wj′,kj′ −P0
⎞
⎠−Υ
=
J∑
j′=1
Kj′∑
kj′=1
wHj′,kj′ Πwj′,kj′ +
⎛
⎝
J∑
j=1
I∑
i=1
δj,i − 1
⎞
⎠Υ+
J∑
j′=1
Kj′∑
kj′=1
αj′,kj′ σ2n −
J∑
j′=1
ζj′P0 +
J∑
j=1
I∑
i=1
δj,iaj,iηuHj,iσ2nIMruj,i.
(28)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT TARGET ASSIGNMENT AND RESOURCE ALLOCA TION FOR MULTI-BASE STA TION COOPERA TIVE ISAC IN AA V DETECTION 7707
vector,wj′,kj′ = 0 should be designed to minimize (28).I fΠ ⊁
0, there is an eigenvalue to be 0. Thus, Π is not full rank and
has a non-zero null space. From this deduction, the null space
of Π spans the unit-norm eigenvector uΠ with the eigenvalue
0, (i.e. ΠuΠ = 0). Thus, w⋆j′,kj′ = √P0uΠ can be selected to
minimize (28), which is obtained from (37).
Based on it, Υ⋆ can also be obtained from the condition (33),
such that
δ⋆j,i
⎛
⎝Υ−aj,i
J∑
j′=1
Kj′∑
kj′=1
β2j′,j,iw⋆Hj′,kj′ Cj,iw⋆j′,kj′
+ η
⎛
⎝
J∑
j′=1
Kj′∑
kj′=1
w⋆Hj′,kj′ Dj,iw⋆j′,kj +uHj,iσ2nIMruj,i
⎞
⎠
⎞
⎠ = 0,
(39)
which is equivalent to
Υ⋆ =m i n
∀i∈I
aj,i
J∑
j′=1
Kj′∑
kj′=1
β2j′,j,iw⋆Hj′,kj′ Cj,iw⋆j′,kj′
−η
⎛
⎝
J∑
j′=1
Kj′∑
kj′=1
w⋆Hj′,kj′ Dj,iw⋆j′,kj +uHj,iσ2nIMruj,i
⎞
⎠. (40)
C. AA V Assignment Optimization Subproblem
Observe the Lagrangian (28), aj,i is only relevant to the
ﬁrst term. Therefore, given the proved strong duality from last
section, the Lagrangian function can be decoupled into multiple
individual functions and solved independently:
Lj,i = δj,i
⎛
⎝Υ−aj,i
J∑
j′=1
Kj′∑
kj′=1
β2j′,j,iwHj′,kj′ Cj,iwj′,kj′
+ ηaj,i
⎛
⎝
J∑
j′=1
Kj′∑
kj′=1
wHj′,kj′ Dj,iwj′,kj +uHj,iσ2nIMruj,i
⎞
⎠
⎞
⎠.
(41)
Thus, the individual subproblem can be given by
min
aj,i
Lj,i(aj,i). (42)
To minimize eachLj,i(aj,i), the optimal aj,i can be obtained
as
aj,i =
{
1,j = j⋆ =a r gm i n
j
Lj,i(aj,i),
0, otherwise.
(43)
The assignment decision for each AA Vaj,i is independent of
others, allowing the AA V assignment problem to be decoupled
into individual decisions for each AA V . This simpliﬁes the pro-
cess, enabling each AA V to be scheduled independently based
on the highest achievable SINR, which aligns with the max-min
fairness criterion and ensures that even the weakest link receives
sufﬁcient resources.
As discussed in prior part, each AA V is assigned to a single
BS, which is responsible for receiving all sensing signals (both
Algorithm 1: Solve problem P1 to obtaain optimal
{wj′,kj′ }j′∈J,kj′∈Kj′ ,{uj,i}j∈J,i∈I andaj,i.
1: Initialize:w(0),a(0),u(0). Set the threshold Δ1,Δ2.
2:ηn = η0 satisfying fN(wj′,kj′ )−η0fD(wj′,kj⋆ ) > 0,
and iteration index n.
3: for n=1:N do
4: initialize iteration index t= 1.
5: while 1 do
6: Given w(t−1),a(t−1), solve receive beamforming
optimization: update u(t) by (18).
7: Calculate Lagrangian multipliers (δ⋆,α⋆,ζ⋆) from
problemP6 and obtain w⋆j′,kj′ = √P0uΠ.
8: Calculate Υ⋆ according to (40).
9: Update AA V assignment variables a(t).
10: t = t+ 1.
11: if|Υ⋆,nj −Υ⋆,nj−1|≤ Δ1 then
12: break.
13: end if
14: end while
15: if|Υ⋆,nj −ηn|≤ Δ2 then
16: the maximum Υ⋆,nj is obtained.
17: break.
18: else
19: n = n+ 1 and ηn =Υ ⋆,nj .
20: end if
21: end for
22: Output: Optimal solution {w⋆j′,kj′ }j′∈J,kj′∈Kj′ ,
{u⋆j,i}j∈J,i∈I anda⋆j,i
monostatic and bistatic) related to the AA V and performing
detection. This method ensures that resources are focused on
the BS best suited for the task, optimizing system performance
without overburdening other BSs.
Thus, the optimization of aj,i becomes a straightforward
selection process. For each AA V i,t h eB S j with the highest
SINR is selected, setting aj,i = 1 for that BS and aj,i = 0f o r
others. The independence of each AA V’s assignment decision
and the deterministic nature of SINR values guarantee a unique
optimal solution, enhancing both resource efﬁciency and overall
sensing accuracy in multi-target detection scenarios.
According to IV -A, IV -B and IV -C, the detailed algorithm is
summarized in Algorithm 1.
D. Convergence and Complexity Analysis
The convergence of the algorithm can be guaranteed as fol-
lows. First, the receiving beamforming subproblem is trans-
formed into a standard generalized Rayleigh quotient problem,
the optimal solution of which can be obtained by closed-form
solution. For transmit beamforming subproblem, P3 is a gen-
eralized fractional programming problem which is solved by
Dinkelbach’s method. It means the algorithm can converge
when iteratively updating η, and this also indicates Υ in P5
is nondecreasing [33]. The strong duality also guarantees the
optimal solution ofw⋆j′,kj′ . The optimization of AA V assignment
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

7708 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 74, NO. 5, MA Y 2025
variables is a discrete optimization problem, which is based on
maximizing the SINR of each AA V , therefore it is a greedy
algorithm that guarantees to raise or maintain the minimum
SINR in each iteration. In AA V assignment subproblem, there
is only one optimal solution of aj,i. The convergence of this
algorithm is proved in Appendix B.
The algorithm includes an outer iteration loop, executed N
times. In each outer iteration, the Dinkelbach algorithm has T
iterations. In each Dinkelbach iteration, the algorithm performs
receive beamforming optimization, Lagrangian multiplier com-
putation, and AA V assignment updates. The receive beamform-
ing optimization involves eigenvalue decomposition, which has
a complexity ofO(M 3r), whereMr is the number of receive an-
tennas. Since each BSj needs to perform this operation for each
AA V , the total complexity isO(JIM 3r). Next, the Lagrangian
multiplier computation involves solving fractional programming
problems using the Dinkelbach algorithm. The Dinkelbach algo-
rithm transforms the original fractional programming problem
into a series of convex subproblems, typically solved using the
interior-point method. The number of optimization variables in
the interior-point method is n = J(I +K + 1), each iteration
has a computational complexity of O(n3), and usually requires
O(√n) iterations to converge, resulting in a total complexity
of O(n3.5). Assuming the Dinkelbach algorithm performs T
iterations, the total complexity of transmit beamforming opti-
mization is O(Tn 3.5). Finally, the AA V assignment complexity
isO(JI), as each AA Vi must be matched to the best scheduling
option among all BSs J. Since AA V assignment is performed
in each Dinkelbach iteration, the total complexity isO(NTJI ).
Combining all the above, the total complexity of the algorithm
can be expressed as O(NT(J(I +K + 1))3.5 +NTJIM 3r +
NTJI ).
Given the structure of the receive beamforming optimiza-
tion and AA V assignment problems, it is evident that the op-
erations for one BS and one AA V are independent of those
for other AA Vs, they can be separately processed in parallel.
Therefore, the complexity of the receive beamforming opti-
mization can be reduced from O(JIM 3r) to O(JIM 3rP ) and the
complexity of AA V assignment can be reduced from O(JI)
to O(JIP ), where P is the number of parallel processing
units. As a result, the overall complexity after parallelization
becomes: O(NT(JIM 3rP +(J(I +K + 1))3.5)+ NTJIP ).T h i s
parallelized complexity highlights the efﬁciency improvements
achieved in the receive beamforming and AA V assignment
components through parallel processing.
Similarly, the space complexity for the receive beamforming
matrices and AA V assignment can also be reduced through
parallelization. Since the computations for one BS and one AA V
are independent of those for other AA Vs, the data storage can
be distributed across multiple processing units. As a result, the
space complexity for storing the receive beamforming matrices
is reduced from O(J ×I ×Mr) to O(J×I×MrP ). The space
complexity for storing the transmit beamforming matrices is
similarly reduced from O(J ×I ×Mt) to O(J×I×MtP ).T h e
space complexity for AA V assignment is reduced from O(J ×
I) to O(J×IP ). The space complexity for storing optimization
Fig. 2. Simulation scenario with 7 BSs, 5 AA V targets and 30 CUs.
variables, which is O(J ×(I +K + 1)), remains unchanged
as this step is not parallelizable.
IV . NUMERICAL RESULTS
In this section, we evaluate the performance of the proposed
transmit and receive beamforming problem. Simulation scenario
is constructed in Fig. 2 In particular, we consider 7 BSs are
arranged in cellular network, and the spacing between each BS
is 500 meters, operating at a frequency of 3.5 GHz and total
transmit power budget P0 = 46 dBm. The AA Vs and CUs are
uniformly distributed throughout the entire area, with AA Vs
moving at a speed of 20 m/s. For communication channels,
the distance-dependent large-scale path loss can be modeled
asPL(dB) = 28+ 22log10(d)+ 20log10(fc), where d denotes
the distance from BS to CUs, and fc represent the carrier
frequency [36]. The signals consist of uncoded, independent
and identically distributed (i.i.d.) zero-mean, unit-energy QPSK
symbols. When constructing the sensing channel model, the
Clustered Delay Line (CDL) model can be extended and adjusted
accordingly. First, speciﬁc clusters are selected from the CDL
model to represent sensing target-related clusters. These clusters
depict the paths taken by the sensing signal as it propagates
through the sensing target and the surrounding environmental
scatters, eventually reaching the sensing receiver after multiple
hops. Due to the movement of the sensing target, these related
clusters introduce Doppler shift effects, thereby inﬂuencing the
signal characteristics. In addition to the sensing target clusters
and sensing target-related clusters, other clusters can be mod-
eled as environmental interference sources. These interference
clusters simulate other inﬂuencing factors in the environment.
The speciﬁc channel model conﬁguration is detailed as fol-
lows. Each sensing target’s channel is inﬂuenced by both the
direct sensing channel component and the environmental chan-
nel component. The overall sensing channel coefﬁcient for a
speciﬁc AA V i∈I between the transmitter j′ and the receiver
j is expressed as the sum of these components:
Hij,j′(τ,t)= Hi,sensj,j′ (τ,t)+ Hi,envj,j′ (τ,t). (44)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT TARGET ASSIGNMENT AND RESOURCE ALLOCA TION FOR MULTI-BASE STA TION COOPERA TIVE ISAC IN AA V DETECTION 7709
The sensing channel component Hi,sensj,j′ (τ,t) captures the
direct interaction between the sensing transmitterj′, the speciﬁc
AA Vi, and the sensing receiver j. This component is deﬁned
as:
Hi,sensj,j′ (τ,t)= SLi ·PLi ·
(√
1
KR + 1Hi,NLOSj,j′ (τ,t)
+
√
KR
KR + 1Hi,LOSj,j′,1 (t)δ(τ −τ1 −d3D/c)
)
,
(45)
where SLi represents the shadow fading for the i-th AA V ,
accounting for attenuation due to obstacles or environmental
factors speciﬁc to that AA V .PLi denotes the path loss for thei-th
AA V , which can be either LOS or NLOS path loss, depending on
the environment.KR is the Rice factor, representing the relative
weight between the LOS and NLOS paths.δ(·) is the Dirac delta
function, indicating the speciﬁc time delay corresponding to the
LOS path.
The sensing channel coefﬁcient consists of a LOS echo path
from the sensing transmitter to the sensing AA V and then to
the sensing receiver, along with multiple NLOS echo paths.
The LOS and NLOS echo paths are combined using the Rician
factor to form the overall sensing channel. Hi,NLOSj,j′ (τ,t) and
Hi,LOSj,j′,1 (t) can be generated from[36], formula 7.5-27 and 7.5-29
respectively.
The environmental channel componentHi,envj,j′ (τ,t) considers
the inﬂuence of the broader environment on the signal for
AA Vi, including both LOS and NLOS contributions from the
environment. It is expressed as:
Hi,envj,j′ (τ,t)= SLe ·PLe ·
(√
1
KR + 1Hi,NLOSe,j,j′ (τ,t)
+
√
KR
KR + 1Hi,LOSe,j,j′,1(t)δ(τ −τ1 −de3D/c)
)
,
(46)
where SLe and PLe are the shadow fading and path loss
speciﬁc to the environment, affecting the signal’s propagation as
it relates to the environment surrounding AA V i. Hi,LOSe,j,j′,1(τ,t)
and Hi,NLOSe,j,j′ (τ,t) are the LOS and NLOS components of the
environmental channel for the i-th AA V , respectively.de3D is
the three-dimensional distance between the transmitter j′ and
the receiver j. The NLOS component can be expressed as:
Hi,NLOSe,j,j′ (τ,t)=
N∑
n=3
HNLOSj,j′,n(t)δ(τ −τn −de3D/c)
+
2∑
n=1
3∑
u=1
∑
m∈Ru
HNLOSj,j′,n,m(t)δ(τ −τn,u−de3D/c).
(47)
The ﬁrst summation accounts for the main clusters of NLOS
paths associated with AA V i, each contributing to the overall
TABLE II
SYSTEM PARAMETERS
NLOS delay spread, where HNLOSj,j′,n(t) andHNLOSj,j′,n,m(t) are gen-
erated according to [36], formula 7.5-22 and 7.5-28 respectively.
The second summation represents additional independent NLOS
paths that do not belong to the main clusters, further capturing
the scattering effects in the environment. The LOS component of
the channel coefﬁcientHi,LOSe,j,j′,1(t) is generated according to[36],
formula 7.5-29.
Path loss is calculated from three part, the path loss from the
sensing transmitter to the sensing AA V ,PL(d1), the path loss
from the sensing AA V to the sensing receiver, PL(d2) and the
inﬂuence of the AA V’s RCS[36]. It is given by
PLs(d1,d 2)= PL(d1)+ PL(d2)
+ 10log10
( 4π
λ2
)
− 10log10 (σrcs). (48)
The environmental path loss can be calculated directly based
on the distance between the transmitter and the receiver, assum-
ing that the signal propagates directly from the transmitter to the
receiver without considering intermediate reﬂection or scatter-
ing paths. Shadow fading is usually assumed to follow a log-
normal distribution, i.e., SLk ∼N (0,σ 2), SLe ∼N (0,σ 2).
Typically, the Radar Cross Section (RCS) is a complex function
of angle, frequency, and polarization. Even for simple targets,
the observed RCS can vary signiﬁcantly with changes in the
radar operating frequency and the target’s aspect angle. In this
paper, the AA V is assumed to be a point target, with the RCS
considered constant regardless of the direction of incidence or
reﬂection. Therefore, a speciﬁc RCS value is used.
The remaining system parameters are given in Table II.
In order to evaluate the performance of the proposed algo-
rithm, we compare it with traditional Zero-Forcing (ZF) beam-
forming method and single BS sensing method. ZF algorithm is
a popular linear beamforming technique that optimizes the per-
formance of communication links by minimizing the inﬂuence
of interfering signals. Speciﬁcally, ZF method directly processes
the inverse of channel matrix through inverse matrix operation,
so as to eliminate the interference in the received signal. The
method assumes perfect channel state information and is able to
point the beam at a single or multiple CUs to maximize the SINR.
In this study, ZF is used as a benchmark algorithm to demonstrate
its beamforming effect when only communication performance
optimization is considered, without considering sensing AA Vs.
Then, sensing SINR is obtained based on the calculated beam
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

7710 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 74, NO. 5, MA Y 2025
Fig. 3. Algorithm convergence with different number of AA V targets.
Fig. 4. Minimum sensing SINR versus minimum communication SINR.
pattern. For single BS sensing method, each AA V is sensed by
its nearest BS, and therefore the sensing signals from other BSs
is recognized as interference.
Fig. 3 shows the convergence behavior of an algorithm with
respect to the sensing SINR as the number of iterations increases.
There are three lines in the graph, each representing a different
number of AA Vs: 5 AA Vs, 7 AA Vs, and 9 AA Vs. As the number
of iterations increases, the sensing SINR for each case increases
rapidly at ﬁrst and then plateaus, indicating that the algorithm is
reaching convergence.
Fig. 4 shows the relationship between the minimum sens-
ing SINR and the minimum communication SINR for a given
network topology. It can be observed from the ﬁgure that com-
pared with the traditional ZF algorithm, the proposed algorithm
provides a higher sensing SINR under different BS numbers.
In particular, the proposed algorithm achieves a higher sens-
ing SINR while maintaining the same communication SINR
level, which demonstrates the effectiveness of the algorithm in
comprehensive communication and sensing performance opti-
mization. In addition, the proposed algorithm considers the joint
optimization of communication and sensing transmission and re-
ceive beamforming, while the ZF algorithm is mainly concerned
Fig. 5. Minimum sensing SINR versus transmit power P0 .
with optimizing the communication capability. Therefore, when
sensing performance is equally important, the proposed algo-
rithm can better balance the performance trade-off between
communication and sensing, which is very critical in a coop-
erative ISAC systems. The advantage of the proposed algorithm
is that it can maximize the sensing capability while ensuring
communication quality service (QoS), so that the system can
support both wireless communication and sensing functions
more effectively. As for single BS sensing method, its sensing
SINR is much smaller than any other two methods. Because
single BS sensing method only receives the reﬂected signal from
its own as effective sensing signal, reﬂected sensing signal from
other BSs is recognized as interference.
Fig. 5 shows the trend of minimum sensing SINR as a function
of total transmit power, and compares the performance of the
proposed algorithm with that of the ZF algorithm and single BS
sensing method under different number of CUs. As can be seen
from the ﬁgure, the proposed algorithm outperforms the ZF algo-
rithm at all power levels and the number of users, proving its su-
periority in resource allocation and beamforming. In particular,
as the transmission power increases, the proposed algorithm can
effectively convert the additional power into improved sensing
performance, while the ZF algorithm has a smaller gain, which
indicates that the proposed algorithm can make better use of the
available power. In addition, when the number of CU increases,
the performance of these two methods declines to improve
communication SNR. The proposed algorithm optimizes both
communication and sensing in a combined manner, rather than
optimizing only the communication capability as the ZF method
does. Therefore, the proposed algorithm is a more ideal choice
for a cooperative ISAC systems that need to make a trade-off
between communication and sensing. The sensing SINR of
single sensing method increases slowly and keeps much smaller
than the previous two methods due to severe interference.
The box plot in Fig. 6 shows the SINR distribution of the
proposed algorithm and ZF algorithm for rounds of simulation. It
reveals that the proposed algorithm exhibits greater variability in
sensing SINR than the ZF algorithm, suggesting a broader range
of performance outcomes to allocate resources for different
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT TARGET ASSIGNMENT AND RESOURCE ALLOCA TION FOR MULTI-BASE STA TION COOPERA TIVE ISAC IN AA V DETECTION 7711
Fig. 6. Sensing SINR data distribution comparison.
Fig. 7. Minimum sensing SINR versus number of CUs.
AA Vs under speciﬁc distributions. The median SINR of the
proposed algorithm is higher, indicating a capacity for achieving
higher SINR. Moreover, the interquartile range (IQR) of the
proposed algorithm is wider, implying greater variability around
the median SINR. In contrast, the ZF algorithm’s IQR is nar-
rower and lower, denoting less variability and generally inferior
performance. In essence, the proposed algorithm demonstrates
a clear advantage in reaching higher SINR for sensing tasks
compared to the ZF algorithm. This advantage is attributed to
the algorithm’s design, which jointly optimizes transmit and
receive beamforming with an emphasis on both communication
and sensing capabilities. The ZF algorithm, optimized solely
for communication, may not perform as well in sensing appli-
cations.
Fig. 7 depicts the minimum sensing SINR as a function
of the number of CUs for three different conﬁgurations of
BSs: 7 BSs, 4 BSs, and 3 BSs. The curve representing 7 BSs
starts at the highest SINR and shows a gradual decline as the
number of CUs increases. Despite this decrease, it maintains
the highest minimum sensing SINR throughout the range of
CU numbers. This indicates a robust sensing capability due to
the large number of BSs, which can cooperate effectively to
provide a strong sensing performance even as the demand for
communication resources rises. The 4 BSs curve begins lower
than the 7 BSs curve and shows a steeper decline with the
increasing number of CUs. This suggests that with fewer BSs,
the system’s ability to allocate sufﬁcient resources for sensing
diminishes more rapidly as the communication load increases.
This results in a more pronounced drop in sensing performance,
highlighting the impact of reduced cooperation among BSs on
the network’s overall sensing capability. The curve for 3 BSs
starts with the lowest minimum sensing SINR and exhibits the
steepest downward trend as the number of CUs grows. This
steep decline reﬂects the limited cooperative sensing capacity
and resource availability in the network with the fewest BSs.
As the communication demands escalate, the competition for
resources signiﬁcantly impacts the sensing performance, leading
to a substantial reduction in the minimum sensing SINR.
V. C ONCLUSION
In this paper, we addressed the joint transmit and receive
beamforming optimization problem for ISAC systems with mul-
tiple BSs, focusing on the challenging scenario of fast-moving
AA V detection. We formulated an optimization problem to
balance communication and sensing tasks, aiming to maximize
the minimum radar SINR while effectively managing the in-
terference complexities introduced by rapid AA V movement,
such as Doppler shifts and dynamic multipath effects. Using an
alternating optimization approach, we tackled the non-convexity
of the problem, reﬁning the solution iteratively with the gen-
eralized Rayleigh quotient and Dinkelbach’s method. Numer-
ical simulations demonstrated the algorithm’s superiority over
benchmark strategies, particularly highlighting the beneﬁts of
cooperative ISAC with multiple BSs in handling high-mobility
AA Vs. The proposed algorithm signiﬁcantly improved fairness
in sensing SINR, ensuring a minimum performance threshold
across multiple AA Vs and enhancing overall sensing accuracy
in dynamic environments.
APPENDIX A
PROOF OF PROPOSITION 1
From the expression in (13), the subproblem maximizes the
minimum sensing SINR among the AA Vs to obtain the optimal
receive beamforming solution. With ﬁxed transmit beamforming
and AA V assignment, the optimization ofuj,i for detecting AA V
i has no effect on the performance of other AA Vs. Therefore, the
optimization of uj,i for each AA V can be conducted separately.
Based on it, the max-min optimization problem(13) is equivalent
to the following problem [37]
max
uj,i
uHj,i(∑Jj′=1 β2j′,j,iAj′,j,iQAHj′,j,i)uj,i
uHj,iBuj,i ∀i ∈I . (49)
The transformed problem (13) is a generalized Rayleigh
quotient, and the optimal solution of u∗j,i can be obtained in
(18).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

7712 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 74, NO. 5, MA Y 2025
APPENDIX B
To prove the convergence of a max-min optimization algo-
rithm, we need to show that in each iteration, when the variable
sets W,u,a are updated, the objective function value γ(n)obj is
non-decreasing. Speciﬁcally, we need to prove that in each iter-
ation, the optimized objective function value is always greater
than or equal to the value from the previous iteration.
Assume that after then− 1th iteration, the objective function
value is γ(n−1)obj .I nt h e nth iteration, the update process of the
objective function can be represented by the following sequence
of inequalities:
γ(n−1)obj = γ(n−1)
(
u(n−1),W(n−1),a(n−1)
)
(I)
≤ γ(n)
(
u(n),W(n−1),a(n−1)
)
(II)
≤ γ(n)
(
u(n),W(n),a(n−1)
)
(III)
≤ γ(n)
(
u(n),W(n),a(n)
)
(IV)
= γ(n)obj . (50)
Assume that after the n− 1th iteration, the value of
the objective function is γ(n−1)obj =m i ni∈I γ(n−1)j,i (u(n−1),
W(n−1),a(n−1)). Next, we will sequentially optimize each
variable and show how the objective function value gradually
increases or remains unchanged.
In thenth iteration, we ﬁrst optimize the receive beamforming
vectoru, while keeping the other variablesW anda unchanged.
At this stage, we use the Generalized Rayleigh Quotient opti-
mization method, which allows us to ﬁnd the optimal receive
beamforming vector by maximizing the eigenvalue of the Gen-
eralized Rayleigh Quotient.
Given the other variables W(n−1) and a(n−1), the optimized
objective function value should satisfy the following inequality:
γ(n)obj
(
u(n),W(n−1),a(n−1)
)
≥ γ(n−1)obj , (51)
which is equivalent to
min
i∈I
γ(n)j,i
(
u(n),W(n−1),a(n−1)
)
≥ min
i∈I
γ(n−1)j,i
(
u(n−1),W(n−1),a(n−1)
)
. (52)
The reason this inequality holds is that u(n) is the optimal
solution to the receive beamforming problem given the other
variables W(n−1) and a(n−1), so the minimum objective func-
tion value will not decrease.
Next, keeping the receive beamforming vectoru and the AA V
assignment variable a unchanged, we optimize the transmit
beamforming vector W. At this stage, we use the Dinkelbach
method to handle the fractional programming problem, which
transforms the non-convex problem into a series of easily solv-
able problems.
The optimized objective function value satisﬁes the following
inequality:
γ(n)obj
(
u(n),W(n),a(n−1)
)
≥ γ(n)obj
(
u(n),W(n−1),a(n−1)
)
, (53)
which is equivalent to
min
i∈I
γ(n)j,i
(
u(n),W(n),a(n−1)
)
≥ min
i∈I
γ(n)j,i
(
u(n),W(n−1),a(n−1)
)
. (54)
Here,W(n) is the optimal transmit beamforming vector in the
nth iteration, given the receive beamforming vectoru(n) and the
AA V assignment variablea(n−1), so the objective function value
continues to increase or remain unchanged.
Finally, keeping the receive beamforming vector u and the
transmit beamforming vector W unchanged, we optimize the
AA V assignment variable a. At this stage, greedy algorithm
is used to select the optimal AA V assignment that maximizes
SINR.
The optimized objective function value satisﬁes the following
inequality:
γ(n)obj
(
u(n),W(n),a(n)
)
≥ γ(n)obj
(
u(n),W(n),a(n−1)
)
, (55)
which is equivalent to
min
i∈I
γ(n)j,i
(
u(n),W(n),a(n)
)
≥ min
i∈I
γ(n)j,i
(
u(n),W(n),a(n−1)
)
. (56)
Here, a(n) is the optimal AA V assignment variable in the nth
iteration, given the receive beamforming vector u(n) and the
transmit beamforming vector W(n), so the objective function
value will not decrease.
By sequentially optimizing each variable, we obtain the fol-
lowing inequality chain:
γ(n−1)obj =m i ni∈I γ(n−1)j,i
(
u(n−1),W(n−1),a(n−1)
)
≤ γ(n)obj =m i ni∈I γ(n)j,i
(
u(n),W(n),a(n)
)
. (57)
Since the objective function value γobj is upper-bounded
(e.g., due to physical power constraints, the objective function
value cannot exceed a certain maximum value), this inequality
chain shows that the objective function value either increases
or remains unchanged during the iterative process, eventually
converging to a stable value. This proves the convergence of the
algorithm.
By sequentially optimizing each variable and using the in-
equality chain to prove the monotonic increase of the objective
function, we can ensure that the algorithm progresses towards
convergence in each iteration. Ultimately, this process ensures
the overall convergence of the max-min optimization problem.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

LI et al.: JOINT TARGET ASSIGNMENT AND RESOURCE ALLOCA TION FOR MULTI-BASE STA TION COOPERA TIVE ISAC IN AA V DETECTION 7713
REFERENCES
[1] D. C. Nguyen et al., “6G Internet of Things: A comprehensive survey,”
IEEE Internet Things J. , vol. 9, no. 1, pp. 359–383, Jan. 2022.
[2] Z. M. Fadlullah and N. Kato, “On smart IoT remote sensing over integrated
terrestrial-aerial-space networks: An asynchronous federated learning ap-
proach,” IEEE Netw., vol. 35, no. 5, pp. 129–135, Sep./Oct. 2021.
[3] Y . Xiong, F. Liu, Y . Cui, W. Y uan, T. X. Han, and G. Caire, “On the fun-
damental tradeoff of integrated sensing and communications under Gaus-
sian channels,” IEEE Trans. Inf. Theory , vol. 69, no. 9, pp. 5723–5751,
Sep. 2023.
[4] X. Wang, Z. Fei, J. Huang, and H. Y u, “Joint waveform and discrete phase
shift design for RIS-assisted integrated sensing and communication system
under Cramer-Rao bound constraint,” IEEE Trans. V eh. Technol., vol. 71,
no. 1, pp. 1004–1009, Jan. 2022.
[5] J. A. Zhang et al., “An overview of signal processing techniques for joint
communication and radar sensing,” IEEE J. Sel. Topics Signal Process. ,
vol. 15, no. 6, pp. 1295–1315, Nov. 2021.
[6] Z. He, W. Xu, H. Shen, D. W. K. Ng, Y . C. Eldar, and X. Y ou, “Full-
duplex communication for ISAC: Joint beamforming and power opti-
mization,” IEEE J. Sel. Areas Commun. , vol. 41, no. 9, pp. 2920–2936,
Sep. 2023.
[ 7 ] Z .R e n ,L .Q i u ,J .X u ,a n dD .W .K .N g ,“ R o b u s tt r a n s m i tb e a m f o r m i n g
for secure integrated sensing and communication,”IEEE Trans. Commun.,
vol. 71, no. 9, pp. 5549–5564, Sep. 2023.
[8] H. Hua, J. Xu, and T. X. Han, “Optimal transmit beamforming for inte-
grated sensing and communication,” IEEE Trans. V eh. Technol., vol. 72,
no. 8, pp. 10588–10603, Aug. 2023.
[9] Z. Behdad, Ö. T. Demir, K. W. Sung, E. Björnson, and C. Cavdar,
“Power allocation for joint communication and sensing in cell-free massive
MIMO,” inProc. 2022 IEEE Glob. Commun. Conf., Rio de Janeiro, Brazil,
2022, pp. 4081–4086.
[10] C. Liu et al., “Learning-based predictive beamforming for integrated
sensing and communication in vehicular networks,” IEEE J. Sel. Areas
Commun., vol. 40, no. 8, pp. 2317–2334, Aug. 2022.
[11] C. Dou, N. Huang, Y . Wu, L. Qian, and T. Q. S. Quek, “Channel sharing
aided integrated sensing and communication: An energy-efﬁcient sensing
scheduling approach,” IEEE Trans. Wireless Commun. , vol. 23, no. 5,
pp. 4802–4814, May 2024.
[12] K. Chen, C. Qi, O. A. Dobre, and G. Y . Li, “Simultaneous beam training and
target sensing in ISAC systems with RIS,”IEEE Trans. Wireless Commun.,
vol. 23, no. 4, pp. 2696–2710, Apr. 2024.
[13] M. Luan, B. Wang, Z. Chang, T. Hämäläinen, and F. Hu, “Robust beam-
forming design for RIS-Aided integrated sensing and communication
system,” IEEE Trans. Intell. Transp. Syst. , vol. 24, no. 6, pp. 6227–6243,
Jun. 2023.
[14] J. Zuo, Y . Liu, C. Zhu, Y . Zou, D. Zhang, and N. Al-Dhahir, “Exploiting
NOMA and RIS in integrated sensing and communication,” IEEE Trans.
V eh. Technol., vol. 72, no. 10, pp. 12941–12955, Oct. 2023.
[15] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[16] L. Xie, S. Song, Y . C. Eldar, and K. B. Letaief, “Collaborative sensing in
perceptive mobile networks: Opportunities and challenges,”IEEE Wireless
Commun., vol. 30, no. 1, pp. 16–23, Feb. 2023.
[17] J. An, H. Li, D. W. K. Ng, and C. Y uen, “Fundamental detection probability
vs Achievable rate tradeoff in integrated sensing and communication
systems,” IEEE Trans. Wireless Commun., vol. 22, no. 12, pp. 9835–9853,
Dec. 2023.
[18] C. Dou, N. Huang, Y . Wu, L. Qian, Z. Shi, and T. Q. S. Quek, “Integrated
sensing and communication enabled multidevice multitarget cooperative
sensing: A fairness-aware design,”IEEE Internet Things J., vol. 11, no. 17,
pp. 29190–29201, Sep. 2024.
[19] Y . Pan et al., “Cooperative trajectory planning and resource allocation
for UA V -Enabled integrated sensing and communication systems,”IEEE
Trans. V eh. Technol., vol. 73, no. 5, pp. 6502–6516, May 2024.
[20] S. Liu, M. Li, R. Liu, W. Wang, and Q. Liu, “Joint transmit beamforming
and receive ﬁlter design for cooperative multi-static ISAC networks,”IEEE
Wireless Commun. Lett., vol. 13, no. 6, pp. 1700–1704, Jun. 2024.
[21] N. Zhao, Y . Wang, Z. Zhang, Q. Chang, and Y . Shen, “Joint transmit and
receive beamforming design for integrated sensing and communication,”
IEEE Commun. Lett., vol. 26, no. 3, pp. 662–666, Mar. 2022.
[22] P . Gao, L. Lian, and J. Y u, “Cooperative ISAC with direct localization
and rate-splitting multiple access communication: A Pareto optimization
framework,” IEEE J. Sel. Areas Commun. , vol. 41, no. 5, pp. 1496–1515,
May 2023.
[23] Y . Huang, Y . Fang, X. Li, and J. Xu, “Coordinated power control for net-
work integrated sensing and communication,” IEEE Trans. V eh. Technol.,
vol. 71, no. 12, pp. 13361–13365, Dec. 2022.
[24] Q. Shi, L. Liu, S. Zhang, and S. Cui, “Device-free sensing in OFDM cellu-
lar network,” IEEE J. Sel. Areas Commun., vol. 40, no. 6, pp. 1838–1853,
Jun. 2022.
[25] G. Cheng, Y . Fang, J. Xu, and D. W. K. Ng, “Optimal coordinated transmit
beamforming for networked integrated sensing and communications,”
IEEE Trans. Wireless Commun., vol. 23, no. 8, pp. 8200–8214, Aug. 2024.
[26] L. Chen, Z. Wang, Y . Du, Y . Chen, and F. Richard Y u, “General-
ized transceiver beamforming for DFRC with MIMO radar and MU-
MIMO communication,” IEEE J. Sel. Areas Commun. , vol. 40, no. 6,
pp. 1795–1808, Jun. 2022.
[27] C. G. Tsinos, A. Arora, S. Chatzinotas, and B. Ottersten, “Joint
transmit waveform and receive ﬁlter design for dual-function radar-
communication systems,” IEEE J. Sel. Topics Signal Process. , vol. 15,
no. 6, pp. 1378–1392, Nov. 2021.
[28] Z. Liu, S. Aditya, H. Li, and B. Clerckx, “Joint transmit and receive beam-
forming design in full-duplex integrated sensing and communications,”
IEEE J. Sel. Areas Commun. , vol. 41, no. 9, pp. 2907–2919, Sep. 2023.
[29] Y . Du, Y . Liu, K. Han, J. Jiang, W. Wang, and L. Chen, “Multi-user and
multi-target dual-function radar-communication waveform design: Multi-
fold performance tradeoffs,” IEEE Trans. Green Commun. Netw. ,v o l .7 ,
no. 1, pp. 483–496, Mar. 2023.
[30] S. Bi, L. Huang, H. Wang, and Y . -J. A. Zhang, “Lyapunov-guided
deep reinforcement learning for stable online computation ofﬂoading
in mobile-edge computing networks,” IEEE Trans. Wireless Commun. ,
vol. 20, no. 11, pp. 7519–7537, Nov. 2021.
[31] J. Gao, Z. Kuang, J. Gao, and L. Zhao, “Joint ofﬂoading scheduling and
resource allocation in vehicular edge computing: A two layer solution,”
IEEE Trans. V eh. Technol., vol. 72, no. 3, pp. 3999–4009, Mar. 2023.
[32] F. Zhou and R. Q. Hu, “Computation efﬁciency maximization in wireless-
powered mobile edge computing networks,” IEEE Trans. Wireless Com-
mun., vol. 19, no. 5, pp. 3170–3184, May 2020.
[33] G. M. N. Guerekata and R. U. V erma, Generalized Fractional Program-
ming. Hauppauge, NY , USA: Nova Science Publishers, 2017.
[34] S. Boyd and L. V andenberghe, Convex Optimization. Cambridge, U.K.:
Cambridge Univ. Press, 2004.
[35] H. Tuy and H. Tuan, “Generalized s-lemma and strong duality in
nonconvex quadratic programming,” J. Glob. Optim. , vol. 56, no. 3,
pp. 1045–1072, 2013.
[36] 3GPP, “Study on channel model for frequencies from 0.5 to 100 GHz,”
3GPP , Tech. Speiciﬁcation TS38.901, 2022.
[37] Y . Jiang, F. C. M. Lau, I. W.-H. Ho, H. Chen, and Y . Huang, “Max–
Min weighted downlink SINR with uplink SINR constraints for full-
duplex MIMO systems,” IEEE Trans. Signal Process. , vol. 65, no. 12,
pp. 3277–3292, Jun. 2017.
Ruotong Li received the B.S. degree in electronic
information engineering from the Hunan University
of Science and Technology, Xiangtan, China, in 2019,
and the M.S. degree in 2022 from the Beijing Uni-
versity of Posts and Telecommunications (BUPT),
Beijing, China, where he is currently working to-
ward the Ph.D. degree. His research interests include
mobile edge computing, artiﬁcial intelligence, joint
communication, and sensing system.
Qixun Zhang (Member, IEEE) received the B.Eng.
degree in communication engineering and the Ph.D.
degree in circuit and system from the Beijing Uni-
versity of Posts and Telecommunications (BUPT),
Beijing, China, in 2006 and 2011, respectively. His
research interests include B5G/6G mobile commu-
nication system, spectrum-sharing access, joint com-
munication, and sensing system.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply. 

7714 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 74, NO. 5, MA Y 2025
Dingyou Ma received the B.Sc. degree in aerospace
science and technology from Xidian University,
Xi’an, China, in 2016, and the Ph.D. degree in elec-
tronics engineering from Tsinghua University, Bei-
jing, China, in 2022. Since July 2022, he has been with
the Key Laboratory of Universal Wireless Communi-
cations, Ministry of Education, School of Information
and Communication Engineering, Beijing University
of Posts and Telecommunications, Beijing, as a Lec-
turer. His research interests include communications
signal processing, radar signal processing, and dual-
function radar-communications system.
Kan Yu (Member, IEEE) received the M.S. degree
in 2016 from the School of Information Science and
Engineering, Qufu Normal University, Qufu, China,
and the Ph.D. degree in 2019 from the College of
Computer Science and Engineering, Shandong Uni-
versity of Science and Technology, Qingdao, China.
He is currently a Postdoctor with the Key Laboratory
of Universal Wireless Communications, Ministry of
Education, Beijing University of Posts and Telecom-
munications, Beijing, China. His research interests
mainly include wireless networks, IoT security, and
distributed algorithm design and analysis. He is also a member of China
Computer Federation (CCF).
Yuzhen Huangreceived the B.S. degree in communi-
cations engineering and the Ph.D. degree in commu-
nications and information systems from the College
of Communications Engineering, PLA University of
Science and Technology, Nanjing, China, in 2008
and 2013, respectively. He is with the Academy of
Military Sciences of PLA, Beijing, China, where he
is currently a Professor. His research interests include
MIMO communications systems, machine learning,
UA V communications, and cognitive radio systems.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:10:34 UTC from IEEE Xplore.  Restrictions apply.