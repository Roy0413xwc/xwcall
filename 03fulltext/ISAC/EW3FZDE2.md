---
title: "Integrated Sensing and Communications in Multi-UAV Networks A Dual-Objective Optimization Perspective"
zotero_key: "EW3FZDE2"
pdf_key: "GCRNXBN0"
collection: "ISAC"
source: "User-provided PDF (pypdf extraction)"
page_mapping: unverified
---

# Integrated Sensing and Communications in Multi-UAV Networks A Dual-Objective Optimization Perspective — Fulltext

> 由用户提供的 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

10066 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Integrated Sensing and Communications in
Multi-UA V Networks: A Dual-Objective
Optimization Perspective
Xu Guo
 , Student Member , IEEE, Jingcheng Shi
 , Graduate Student Member , IEEE ,
Jianjun Wu
 , Member , IEEE, Rongqing Zhang
 , Member , IEEE, and Xiang Cheng
 , Fellow, IEEE
Abstract—Integrated sensing and communications (ISAC) has
become increasingly crucial in next-generation wireless networks.
Leveraging the reliable line-of-sight (LoS) links and mobility
of unmanned aerial vehicles (UA Vs), UA V-assisted ISAC has
attracted signiﬁcant attention. Different from the previous UA V-
ISAC scenarios with single target or overlapping users and
targets, we investigate ISAC in a more general multi-UA V
network with independent multiple communication users and
multiple sensing targets, where the UA Vs provide downlink com-
munications to the users while sensing the targets. Additionally,
we consider the complicated interference management among
the UA Vs to further enhance the network’s practicality. Such
a scenario presents a new challenge for the joint optimization
problem in terms of the UA V trajectories, the user association, the
target association, and the power control. Furthermore, since the
existing single-objective and weighted optimization approaches
may result in potential performance loss and optimization biases,
we propose a dual-objective model to further optimize ISAC,
aiming for a better tradeoff between the communication and
sensing performance. Speciﬁcally, we propose an efﬁcient sens-
ing and communication dual-objective multi-UA V optimization
algorithm (SC-DO-MUOA) to maximize communication rate
and simultaneously minimize sensing Cra ´mer-Rao bound (CRB).
Simulation results demonstrate that our proposed SC-DO-MUOA
outperforms various baselines in both communication and sens-
ing performance.
Index Terms —Dual-objective optimization, multi-UA V ISAC,
resource allocation.
I. I NTRODUCTION
I
NTEGRATED sensing and communications (ISAC) has
become increasingly crucial in next-generation wireless
networks, such as Beyond 5G (B5G) and 6G, driven by
Received 15 April 2025; revised 8 August 2025 and 29 October 2025;
accepted 2 December 2025. Date of publication 15 December 2025; date of
current version 12 January 2026. This work was supported in part by the
National Natural Science Foundation of China under Grant 62271351, Grant
62125101, and Grant 62341101; and in part by the New Cornerstone Science
Foundation through the Xplorer Prize. The associate editor coordinating
the review of this article and approving it for publication was X. Chen.
(Corresponding authors: Rongqing Zhang; Jianjun Wu.)
Xu Guo, Jingcheng Shi, Jianjun Wu, and Xiang Cheng are with
the School of Electronics, Peking University, Beijing 100871, China
(e-mail: guoxu@stu.pku.edu.cn; shijingcheng@stu.pku.edu.cn; just@pku.edu.
cn; xiangcheng@pku.edu.cn).
Rongqing Zhang is with the Intelligent Transportation Thrust, The Hong
Kong University of Science and Technology (Guangzhou), Guangzhou
511453, China (e-mail: rongqing.labs@gmail.com).
Digital Object Identiﬁer 10.1109/TWC.2025.3641375
the stronger demands for advanced sensing capabilities and
the scarcity of spectrum resources [1]. By sharing spectrum
resources and hardware, ISAC is expected to signiﬁcantly
enhance spectrum efﬁciency, reduce equipment costs, and pro-
vide both high-quality communications and accurate sensing
services. Moreover, Zhang et al. have leveraged advanced
artiﬁcial intelligence (AI) techniques, such as Generative
Adversarial Networks (GANs) [2], Deep Reinforcement
Learning (DRL) [3], and Deep Unfolding Learning [4], to
accelerate the development of ISAC systems. These AI-driven
approaches help ISAC show great promise in a wide range of
emerging applications, including vehicle-to-everything, smart
homes, smart manufacturing, and more [5].
One of the most promising applications of ISAC is
unmanned aerial vehicle (UA V)-assisted wireless networks.
With their high mobility and ease of deployment, UA Vs can
serve as aerial base stations or relays, establishing reliable line-
of-sight (LoS) communication links [6] and enhancing sensing
accuracy through ﬂexible positioning [7]. Moreover, UA Vs
can optimize their ﬂight trajectories to mitigate interference
effectively [8]. The integration of UA Vs with ISAC has the
potential to signiﬁcantly improve both communication and
sensing performance, making UA V-ISAC a key focus for 6G
development and a growing area of research.
Several studies have explored ISAC in single-UA V net-
works. To improve the communication rate while meeting
sensing requirements, researchers jointly optimized UA V tra-
jectory, user associations, and resource allocation in systems
with multiple users and targets [9], [10], [11]. Jiang et al. [12]
maintained information freshness at the ground controller
while ensuring high sensing quality for each target. Con-
strained by communication rate, [13] maximized the radar
estimation rate through the joint optimization of UA V task
scheduling, transmit power allocation, and 3D ﬂight param-
eters. Moreover, to achieve a balance between the sensing
and communication performance, Liu et al. [14] proposed
a multi-objective resource optimization framework aimed at
maximizing both energy efﬁciency and minimum radar mutual
information (MI). Jing et al. [15] formulated a weighted sum
optimization problem to balance the total transmitted data
and Cra ´mer-Rao bound (CRB) for ISAC in the single-UA V
network.
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10067
Considering a single UA V’s limited sensing range and
communication capability, some recent works have focused
on deploying multiple UA Vs for cooperative ISAC to enhance
the potential of aerial-to-ground communication and sensing
[16], [17], [18], [19], [20], [21], [22], [23], [24], [25], [26],
[27], [28], [29], [30], [31], [32], [33], [34]. Wang et al. [16]
investigated the UA Vs serving the communication users while
cooperatively sensing a single target, aiming to maximize the
network utility under the localization accuracy constraints. By
planning the trajectories and resource allocation of the UA Vs,
the valid detection and fairness [21] and the Cram ´er-Rao
lower bounds (CRLB) for target location estimation [22] were
improved subject to the communication data rate and quality-
of-service (QoS) constraints, respectively. Beuster et al. [26]
focused on measurement-driven insights for multi-sensor ISAC
networks, which could offer relevant guidelines on real-
istic channel modeling and performance under real-world
constraints. Orikumhi et al. [27] highlighted mobility-aware
resource allocation, reminding us that user or UA V mobility
can considerably affect interference patterns and ﬂight trajec-
tory decisions. Furthermore, to jointly enhance the sensing
and communication performance for ISAC in multi-UA V
networks, [28], [29], [30], [31], [32], [33] all employed the
weighted-based algorithms to optimize the UA V trajectories,
user association, power control, and other network resources.
Li et al. [34] proposed an efﬁcient dual-objective evolutionary
algorithm based on large language models (LLMs) to ﬁnd
the clear trade-off between communication and sensing per-
formance. However, they considered the scenario where the
UA Vs communicated and sensed the same group of users, and
assumed no interference between UA Vs.
Similarly, most existing multi-UA V ISAC works focus on
single-target scenarios or cases where communication users
are also the sensing targets. With the broader application
demands of 6G, it is general and essential for UA Vs to perform
sensing tasks with multiple targets while serving multiple
communication users, independent of the targets. Addition-
ally, in multi-UA V ISAC scenarios, UA Vs receive not only
echo signals from targets but also direct transmissions from
other UA Vs, leading to inevitable interference. Most existing
works assume that such interference can be eliminated through
ﬁltering, which is hard to achieve in practical applications.
Moreover, it is noteworthy that most above ISAC studies
adopt the following two approaches for modeling the optimiza-
tion of communication and sensing performance: 1) optimizing
communication performance with sensing performance as a
constraint, or vice versa; 2) using a weighted approach to
combine communication and sensing performance into a single
optimization objective. The former approach may result in
a loss of potential performance due to restrictive thresholds,
while the latter may introduce optimization biases from sub-
jective weight selection. Therefore, modeling a dual-objective
optimization of both communication and sensing performance
may result in a more optimized ISAC performance, fully
exploiting the potential of both communication and sensing.
Motivated by the above ﬁndings, in this paper, we investi-
gate ISAC in a multi-UA V network, where the UA Vs provide
downlink communication services for multiple ground users
while simultaneously sensing multiple ground targets. Dif-
ferent from the previous works that focus on single-target
scenarios or assume communication users also serve as sensing
targets, we consider a more general and practical network
where the multiple communication users and sensing targets
are independent. Additionally, we consider the interference
management among UA Vs, further enhancing the practical-
ity of our scenario. Notably, in such a multi-UA V network
with multi-user and multi-target, the UA Vs need to not only
coordinate and schedule the communication and sensing tasks
while balancing the resource competition, but also design
efﬁcient ﬂight trajectories to enhance both communication
and sensing performance. Therefore, it leads to a complicated
and challenging joint optimization problem in terms of the
UA V trajectories, the both user and target associations, and
the power control.
Furthermore, in this general multi-UA V network, we aim
to further optimize ISAC to achieve a better tradeoff between
the communication and sensing performance. Considering the
potential performance loss of the existing single-objective
and weighted optimization approaches, we propose a dual-
objective model to jointly enhance the communication and
sensing performance. Here, we select two key metrics, i.e.,
communication rate and sensing CRB [35], as dual objectives
for optimization. Speciﬁcally, we propose an efﬁcient sensing
and communication dual-objective multi-UA V optimization
algorithm (SC-DO-MUOA) to enhance both communication
rate and CRB. Simulation results show that our proposed
SC-DO-MUOA signiﬁcantly outperforms various baselines in
both sensing and communication performance. The major
contributions of this work are summarized as follows:
1) Different from the previous UA V-ISAC scenarios with
a single target or communication users also serving as
sensing targets, we investigate ISAC in a more general
multi-UA V network where the multiple communication
users and multiple sensing targets are independent. The
UA Vs provide downlink communications to the users
while simultaneously sensing the targets. Additionally,
we consider the complicated interference management
among the UA Vs to further enhance the network’s prac-
ticality. Note that in such a scenario, the UA Vs need to
not only coordinate and schedule the communication and
sensing tasks while balancing resource competition, but
also design efﬁcient ﬂight trajectories to enhance both
communication and sensing performance. This results
in a complicated and challenging joint optimization
problem in terms of the UA V trajectories, the both user
and target associations, and the power control.
2) Considering the potential performance loss of existing
single-objective and weighted optimization approaches,
we propose a dual-objective model to further optimize
ISAC, aiming for a better tradeoff between communica-
tion and sensing performance. Speciﬁcally, modeling a
dual-objective optimization for both communication rate
and sensing CRB can overcome the limitations of sub-
jective weights and constraint thresholds on performance
optimization in the traditional approaches. It can also
allow for more balanced resource allocation and lead to
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

10068 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. Multi-UA V ISAC scenario with multiple users and multiple targets.
a more optimized ISAC performance, fully exploiting
the potential of both communication and sensing.
3) The above complicated multi-UA V ISAC optimization
problem with dual objectives is non-convex mixed-
integer nonlinear programming (MINLP) and difﬁcult to
solve. To overcome this problem, we propose an efﬁcient
SC-DO-MUOA to jointly improve the communication
and sensing performance. Speciﬁcally, our algorithm
decomposes the problem into several subproblems and
adopts the hybrid evolutionary operators to generate
and update the promising solutions. Compared with
the traditional multi-objective optimization algorithms,
our SC-DO-MUOA more effectively addresses the chal-
lenges of multiple constraints, large-scale variables, and
mixed-integer variables in our multi-UA V ISAC sce-
nario.
The remainder of this paper is organized as follows.
Section II describes the system model of the multi-UA V
ISAC scenario with multiple users and multiple targets. And
formulate the dual-objective problem of maximizing the com-
munication sum rate and minimizing the CRB. Section III
presents our SC-DO-MUOA with problem decomposition,
new solution generation, and population update to obtain the
solutions. And discuss the complexity of our proposed algo-
rithm. In Section IV, simulation results show the performances
of our proposed algorithm. Section V is the conclusion of this
paper.
II. S YSTEM MODEL AND PROBLEM FORMULATION
We investigate ISAC in a more general multi-UA V network,
as shown in Fig. 1. There are M UA Vs, with the set denoted
byM = {1, 2,...,M }, K users, with the set denoted by
K = {1, 2,...,K }, and J targets, with the set denoted
byJ = {1, 2,...,J }, in the network. The UA Vs leverage
their mobility to provide downlink communications to the
ground users while sensing the ground targets through the
downlink ISAC signals. During their ﬂight, the UA V trajec-
tories, transmission power, and associations between UA Vs
and users, as well as UA Vs and sensing targets, are contin-
uously adjusted to enhance both sensing and communication
services. We suppose the 3D coordinate of each user k is
ﬁxed at uk = [ ux,k,uy,k, 0]T , which can be obtained by
global positioning system (GPS). The coordinate of target j
is denoted by vj = [vx,j,vy,j, 0]T , which can be estimated
based on the sensing tasks of UA Vs. Without loss of generality,
Fig. 2. ISAC frame for the multi-UA V , multi-user, and multi-target scenario.
the UA Vs can sail freely between the lowest altitude Hmin
and the highest altitude Hmax. Additionally, assume that the
whole mission period is T and can be discretized into N time
slots with duration δt = TN , indexed by n = 1, 2,...,N .
And the time slot is sufﬁciently small so that the UA Vs’
locations are considered approximately unchanged within each
time slot. As a result, the trajectory of UA V m can be
denoted by the 3D coordinate at consecutive time slots, i.e.,
qm[n] = [qx,m[n],qy,m[n],q z,m[n]]T,n∈{ 1, 2,...,N }.
Note that we actually assume a centralized ground control
center responsible for the uniﬁed task scheduling and resource
allocation of multiple UA Vs in the scenario. The communi-
cation between the control center and the UA Vs primarily
involves low-rate control commands or non-payload data, such
as task status and sensing results. These transmissions are
characterized by small data volume and low transmission cost,
and are typically implemented via dedicated control channels
or out-of-band links in practical applications [36], [37]. As
they are separated from the core spectrum resources used for
UA V–user communication, they have a limited impact on our
primarily focused resource allocation and ISAC performance.
Therefore, in this work, we do not explicitly model the
communication links or constraints between the control center
and the UA Vs.
A. ISAC Frame
As shown in Fig. 2, we assume that the total ISAC frame
number L = TTL and the index is denoted by l = 1, 2,...,L ,whereTL is the time length of an ISAC frame. And the number
of time slots in each ISAC frame is NL = NL . Following the
assumption in [9], the sensing tasks are not always performed
together with communications due to the different practical
requirements of the sensing and communications. Speciﬁcally,
an ISAC frame consists of two parts, indicated by two different
colors in the ﬁgure: the time slots during which the UA Vs
provide only communication service, and the time slots during
which the UA Vs provide both sensing and communication
services simultaneously.
For communications, denote thatαm,k[n] = 1, which means
UA Vm aims to transmit signals to user k in time slot n.
Otherwise, αm,k[n] = 0 . The UA Vs provide services to the
users with the requirement that each UA V can serve at most
one user, and each user can be served by at most one UA V
per time slot. Therefore, the following conditions hold:
K∑
k=1
αm,k[n]≤ 1,∀m,n, (1)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10069
M∑
m=1
αm,k[n]≤ 1,∀k,n. (2)
For sensing, the UA Vs perform sensing tasks when needed,
requiring that each UA V can sense at most one target per time
slot, and each target must be sensed once within an ISAC
frame. Denote that cm,j[n] = 1 , which means UA V m aims
to sense target j in time slot n. Otherwise, cm,j[n] = 0 .
Therefore, the following requirements are satisﬁed:
lNL∑
n=(l−1)NL+1
M∑
m=1
cm,j[n] = 1,∀l,j, (3)
J∑
j=1
cm,j[n]≤ 1,∀m,n. (4)
In this ﬂexible ISAC framework, multiple UA Vs can cooper-
atively sense targets at different times and locations, leveraging
different perspectives and temporal diversity to improve sens-
ing accuracy. Similarly, for communications, the more suitable
UA Vs can serve the associated users to enhance the system
sum rate. However, the UA V trajectories, power control, user
association, and target association with UA Vs are tightly cou-
pled to determine resource allocation, and there is competition
for the resources between the sensing and communication
functions. Besides, our multi-UA V ISAC frame also brings
interference to affect both sensing and communication per-
formance. These factors make our dual-objective optimization
problem more complicated and challenging.
B. Communication Interference Model
As typically discussed in UA V-ISAC scenarios [9], [16],
[19], [31], [32], the communication links between UA Vs
and ground users are assumed to be dominated by the LoS
component. Therefore, the channel power gain from UA V m
to user k follows the free-space path loss model:
hm,k[n] =βcomd(qm[n], uk)−2 = βcom
‖qm[n]− uk‖2, (5)
where βcom is the channel power at a unit reference distance
withβcom = gcgtλ2(4π)2 according to [13] and [15]. gt is the UA V
transmit antenna gain. gc is the communication user’s receive
antenna gain. λ is the wavelength. And d(qm[n], uk) is the
distance between the UA Vm and the user k in time slot n.
Assume that all the UA Vs share the same frequency band
to communicate with the downlink users. If user k is served
by the UA Vm in time slot n, the received signal at user k
according to the data transmission process is:
ym,k[n] =
√
hm,k[n]pm[n]sm,k[n]
+
M∑
i=1,i⁄=m
√
hi,k[n]pi[n]si,k[n] +nm,k[n], (6)
where pm[n] is the transmit power of UA V m in time
slot n; sm,k[n] is the transmitted signal of UA V m; and
nm,k[n] ∼ CN (0,σ 2k) represents the independent additive
white Gaussian noise (AWGN). Note that the transmissions
of all other UA Vs in time slot n cause the co-channel
interference ∑Mi=1,i⁄=m√hi,k[n]pi[n]si,k[n] [38]. Thus, the
signal-to-interference-plus-noise ratio (SINR) of userk in time
slot n can be expressed as:
γm,k[n] = hm,k[n]pm[n]∑M
i=1,i⁄=mhi,k[n]pi[n] +σ20, (7)
where σ20 = Bσ 2k, and B is the channel bandwidth. The
corresponding achievable rate of user k in time slot n is:
Rm,k[n] =Bαm,k[n] log2(1 +γm,k[n]). (8)
C. Sensing Interference Model
Note that ISAC in the multi-UA V networks introduces
greater complexity in managing interference. The UA V
receives not only the echo signal from the target but also direct
transmissions from other UA Vs. These interference signals
cannot be ignored and are challenging to predict in practice.
Unlike previous multi-UA V ISAC works [16], [21], [22],
[23], which assume the interference signals are known and
can be removed by matched ﬁltering, we explicitly consider
the interference and take it into our model. This consider-
ation increases the complexity of our optimization problem,
particularly in trajectory optimization and CRB calculation,
but it also aligns more closely with real-world scenarios.
Additionally, it is worth noting that, although the direct links
between UA Vs are treated as sources of sensing interference,
they do physically exist. And these links can be readily
leveraged as communication channels in practical scenarios
where information exchange between UA Vs is required.
As for the echo links of the ISAC signal, the channel power
gain from the UA V m to the direction of target j and then
back to the UA V m in time slot n can be denoted as [13],
[15], and [39]:
hm,j,m[n] = grgtϕλ2(4π)3 d(qm[n], vj)−4 =βsend(qm[n], vj)−4,
(9)
where gr denotes the antenna gain of UA V receiver, and ϕ
denotes radar cross-section (RCS) of the target. d(qm[n], vj)
is the distance between the UA V m and the target j in time
slot n. To simplify the expression, let βsen = grgtϕλ2(4π)3 .
Considering the interference among the UA Vs caused by
communications, We denote the channel power gain from UA V
i to UA Vm as:
hi,m[n] = grgtλ2(4π)2 d(qi[n], qm[n])−2 =βintd(qi[n], qm[n])−2,
(10)
whered(qi[n], qm[n]) is the distance between the UA Vi and
the UA Vm in time slot n. To simplify the expression, let
βint = grgtλ2(4π)2 .
Therefore, if targetj is sensed by UA Vm in time slotn, the
received signal at UA Vm including both echo and interference
can be expressed as:
ym,j[n] =
√
hm,j,m[n]pm[n]sm,j[n−τm,j]
+
M∑
i=1,i⁄=m
√
hi,m[n]pi[n]si[n−τi,m] +nm,j[n],
(11)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

10070 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
where τm,j = 2d(qm[n],vj )c is the propagation time of the
signal transmitted from UA V m, reﬂected by target j, and
ﬁnally received by UA V m with the speed of light c. Sim-
ilarly, τi,m = d(qi[n],qm[n])c is the propagation time of the
interference signal from UA V i to UA V m. And nm,j[n]
obeys the Gaussian distribution of CN (0,σ 2j ). Here, the
interference signals can be regarded as the superposition of
Gaussian signals and still obey the Gaussian distribution.
Let Ii = ∑Mi=1,i⁄=m√hi,m[n]pi[n]si[n− τi,m], satisfying
Ii∼ CN
(
0,χ∑Mi=1,i⁄=mhi,m[n]pi[n]). And χ denotes the
suppression gain of the direct interference during the signal
processing [39], [40]. Thus, the SINR of the received echo
signal at UA Vm is given by:
γm,j[n] = hm,j,m[n]pm[n]χ∑Mi=1,i⁄=mhi,m[n]pi[n] +σ2j. (12)
D. Problem F ormulation
Our dual objectives are maximizing the communication
sum rate and improving the sensing accuracy. To evaluate the
estimation performance of sensing, mean square error (MSE)
is a commonly used metric [41]. However, obtaining the
closed form of MSE is hard, and minimizing MSE to improve
sensing performance is almost intractable. Note that the CRB
could provide a lower bound for MSE for the unbiased (or
asymptotically unbiased) parameter estimator. Therefore, we
adopt the CRB to characterize the sensing performance.
We ﬁrst present the observation set yj for target j (j =
1,...,J ) and then derive the CRB from these observations.
Here, yj consists of the signals reﬂected by target j and
received by all UA Vs throughout the entire mission durationT .
Since each target is sensed only once during each ISAC frame,
we can express the observation yj = [yj[1],yj[2],...,y j[L]],
where yj[l] = ∑lNLn=(l−1)NL+1∑Mm=1cm,j[n]ym,j[n]. The m
and n are determined by cm,j[n] for each ISAC frame l. To
simplify the expression, we use l instead of n in the following
to represent the speciﬁc time within this ISAC frame when the
target is sensed. In theory,L≥ 3 should be satisﬁed to achieve
unambiguous localization [31]. For the unknown horizontal
location parameters of target j, vj = [vx,j,vy,j]T , we have
the following inequality:
E
{
( ˆvj− vj)( ˆvj− vj)T}≥ J−1(vj), (13)
and the CRB can be formulated as:
CRBvj = J−1(vj), (14)
where J(vj) is the Fisher information matrix (FIM) of vj
given by:
J(vj) = E
{
∂
∂vj
logf(yj| vj)
( ∂
∂vj
logf(yj| vj)
)T}
,
(15)
where f(yj | vj) is the conditional probability density
function (pdf) of the observation yj. Based on the received
signal in (11) and the Gaussian distribution of the interference
and noise, the conditional pdf f(yj| vj) can be expressed as:
f(yj| vj) = 1
(2π)
L
2
∏L
l=1
(
σ2j +χ∑Mi=1,i⁄=mhi,m[l]pi[l]) 12
×exp
{
−12
L∑
l=1
(yj[l]−
√
hm,j,m[l]pm[l]sm,j[l−τj[l]])2
σ2j +χ∑Mi=1,i⁄=mhi,m[l]pi[l]
}
.
(16)
In most cases, if it is difﬁcult to calculate the FIM of
some parameters, we can calculate the FIM of other related
parameters ﬁrst. We ﬁnd that the pdff(yj| vj) directly relates
to the propagation time τj[l]. And the time-to-location con-
version is mathematically linked through τm,j = 2d(qm[n],vj )c
for each ISAC frame l. Therefore, to obtain the FIM J(vj),
we can ﬁrst calculate the FIM J(tj) with respect to the
propagation time tj. According to the observation yj, we can
get tj = [τj[1],τj[2],...,τ j[L]]T . Then, given by the chain
rules, we can derive the FIM J(vj) with respect to vj as:
J(vj) = QjJ(tj)QjT, (17)
where Qj is the Jacobian matrix of (tj) with respect to vj
shown as:
Qj = ∂tTj∂vj = ∂ [τj[1],τj[2],...,τ j[L]]T∂[vx,j,vy,j]T
= 2c
[qx,m[1]−vx,j
d(qm[1],vj ) ... qx,m[l]−vx,jd(qm[l],vj ) ... qx,m[L]−vx,jd(qm[L],vj )
qy,m[1]−vy,j
d(qm[1],vj ) ... qy,m[l]−vy,jd(qm[l],vj ) ... qy,m[L]−vy,jd(qm[L],vj )
]
. (18)
Then, following [42] and [43], the FIM J(tj) can be derived
by (15) and (16) and is presented in (19), shown at the bottom
of the next page.
Finally, the CRB matrix of vj, being the inverse of J(vj)
can be expressed by substituting (18) and (19) into (17) as:
CRBvj = 1gajgbj− [gcj]2
[gbj gcj
gcj gaj
]
, (20)
where gaj , gbj, and gcj are shown in (21)-(23), shown at the
bottom of the next page. Then, the CRB of the target j’s
coordinates vx,j and vy,j are the diagonal elements and can
be given by the following equations, respectively.
CRBvx,j = gajgajgbj− [gcj]2. (24)
CRBvy,j = gbjgajgbj− [gcj]2. (25)
The metric to evaluate sensing performance for target j thus
becomes:
CRB vj =CRBvx,j +CRBvy,j = gaj +gbjgajgbj− [gcj]2. (26)
Similarly, the CRBs of other target locations can be obtained
through the above process.
Taking maximizing the communication rate and minimizing
the sensing CRB as the dual objectives, we jointly optimize
the 3D trajectories of multiple UA Vs, the user association,
the target association, and the power control at the UA Vs
to improve both sensing and communication performance.
For ease of notation, let P = {pm[n],∀m,n} represent
the vector of the transmit power of the UA Vs; let A =
{αm,k[n],∀m,k,n} represent the user association with the
UA Vs; letC ={cm,j[n],∀m,j,n} represent the target asso-
ciation with the UA Vs; let Q ={qm[n],∀m,n} represent the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10071
3D trajectories of the UA Vs. Therefore, the dual-objectives
for the sensing and communication performance optimization
problem can be formulated as follows:
max
P,A,C,Q
1
N
N∑
n=1
M∑
m=1
K∑
k=1
Rm,k[n]
min
P,A,C,Q
J∑
j=1
CRB vj
s.t. cm,j[n]∈{ 0, 1},αm,k[n]∈{ 0, 1},∀m,k,j,n, (27a)
K∑
k=1
αm,k[n]≤ 1,∀m,n, (27b)
M∑
m=1
αm,k[n]≤ 1,∀k,n, (27c)
J∑
j=1
cm,j[n]≤ 1,∀m,n, (27d)
lNL∑
n=(l−1)NL+1
M∑
m=1
cm,j[n] = 1,∀l,j, (27e)
0≤pm[n]≤Pmax,∀m,n, (27f)
1
NL
lNL∑
n=(l−1)NL+1
M∑
m=1
αm,k[n]Rm,k[n]≥Rthk ,∀k,l,
(27g)
‖qm[n]− qm[n− 1]‖≤ Vmaxδt,∀m,n, (27h)
‖qm[n]− qg[n]‖≥ dmin,∀m,n,m ⁄=g, (27i)
Hmin≤qz,m[n]≤Hmax,∀m,n. (27j)
The constraints (27a)-(27c) ensure that each UA V serves
at most one user per time slot, and each user can be served
by at most one UA V per time slot. The constraints (27a),
(27d), and (27e) ensure that each UA V can sense at most
one target per time slot, and each target must be sensed once
within an ISAC time slot. Constraint (27f) indicates that the
transmit power of all UA Vs cannot exceed certain budgets
Pmax. Additionally, Rthk in constraint (27g) is the minimum
achievable rate requirement in each ISAC frame to ensure
the quality of service. The maximum distance between two
consecutive locations of each UA V is constrained as in (27h),
where Vmax is the maximum UA V speed. And dmin is the
minimum distance between any two UA Vs in the same time
slot to avoid the collision in (27i). Constraint (27j) speciﬁes
that the UA Vs ﬂy at the appropriate altitudes, between the
minimum altitude Hmin and the maximum altitude Hmax.
To the best of our knowledge, this is the ﬁrst attempt
to consider ISAC in the multi-UA V network with multiple
users and multiple targets from a dual-objective optimization
perspective to simultaneously improve the communication rate
and sensing accuracy CRB. We need to point out that such
a multi-UA V ISAC scenario results in a complicated and
challenging joint optimization problem in terms of the UA V
trajectories, the both user and target associations, and the
power control. Furthermore, the dual objectives of sensing and
communications, rather than treating one as the objective and
the other as a constraint, present a new challenge in solving the
joint optimization problem. It is a non-convex MINLP, which
is NP-hard to solve.
III. S ENSING AND COMMUNICATION DUAL-O BJECTIVE
MULTI-UAV OPTIMIZATION ALGORITHM
Different from the single-objective optimization problem,
our dual-objective optimization problem aims to obtain a non-
dominated set of solutions instead of a single optimal solution
shown in Fig. 3. And a non-dominated solution is one where
no other solution is better in all objectives. These solutions are
deﬁned as the Pareto optimal solutions, representing the best
trade-offs among the objectives. Moreover, the set of all the
Pareto optimal solutions is deﬁned as the Pareto set (PS) and
the set of all the Pareto optimal objective functions is regarded
as the Pareto front (PF) [44].
Generally, evolutionary algorithms are well-suited for
addressing multi-objective problems due to their population-
based heuristic search nature, which does not rely on gradient
J(tj) = diag


pm[1]hm,j,m[1]
(
8π2B2 + c2d(qm[1],vj )2
)
σ2j +χ∑Mi=1,i⁄=mhi,m[1]pi[1] ,...,
pm[L]hm,j,m[L]
(
8π2B2 + c2d(qm[L],vj )2
)
σ2j +χ∑Mi=1,i⁄=mhi,m[L]pi[L]

. (19)
gaj =
L∑
l=1
pm[l]βsen
σ2j +χ∑Mi=1,i⁄=mhi,m[l]pi[l]
{32π2B2
c2 × (qx,m[l]−vx,j)2d(qm[l], vj)6 + 4(qx,m[l]−vx,j)2d(qm[l], vj)8 }. (21)
gbj =
L∑
l=1
pm[l]βsen
σ2j +χ∑Mi=1,i⁄=mhi,m[l]pi[l]
{32π2B2
c2 × (qy,m[l]−vy,j)2d(qm[l], vj)6 + 4(qy,m[l]−vy,j)2d(qm[l], vj)8 } (22)
gcj =
L∑
l=1
pm[l]βsen
σ2j +χ∑Mi=1,i⁄=mhi,m[l]pi[l]
{32π2B2
c2 × (qx,m[l]−vx,j)(qy,m[l]−vy,j)d(qm[l], vj)6
}
+
L∑
l=1
pm[l]βsen
σ2j +χ∑Mi=1,i⁄=mhi,m[l]pi[l]
{4(qx,m[l]−vx,j)(qy,m[l]−vy,j)
d(qm[l], vj)8
}
(23)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

10072 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 3. The Pareto front distribution for the dual-objective function.
information. As a result, these algorithms are widely recog-
nized for their ability to approximate the Pareto front (PF).
Among these, MOEA/D has demonstrated superior perfor-
mance over other algorithms [45].
Notice that our focus is on the joint improvement of
communication and sensing performance in a more general
multi-UA V network, where multiple communication users
and sensing targets are independently considered. This sce-
nario signiﬁcantly differs from the traditional dual-objective
optimization problems. In such a multi-UA V network with
multi-user and multi-target, the UA Vs need to not only coor-
dinate and schedule the communication and sensing tasks
while balancing the resource competition, but also design
efﬁcient ﬂight trajectories to manage the interference among
UA Vs and enhance both communication and sensing perfor-
mance. This leads to a large number of mixed-integer decision
variables and numerous stringent and complex constraints.
These high-dimensional, temporally coupled variables and
constraints make the traditional multi-objective algorithms,
such as NSGA-II and MOEA/D, less effective in both solution
quality and computational efﬁciency.
To overcome these challenges, we propose an efﬁcient SC-
DO-MUOA algorithm based on the external archive guided
MOEA/D (EAG-MOEA/D) [46] to solve our dual-objective
ISAC problem. By combining the rapid convergence of Parti-
cle Swarm Optimization (PSO) with the diversity-maintaining
ability of Genetic Algorithms (GA), our hybrid approach
improves search efﬁciency and reduces the likelihood of
getting trapped in local optima. This enables a better bal-
ance between communication and sensing performance in
this complex multi-UA V network. Additionally, we propose
a multi-stage constraint control method that manages different
constraints in different stages, including guided population
generation at the problem decomposition stage, population
correction at the solution generation stage, and selective
updates at the population update stage, to efﬁciently handle
the challenges of multiple constraints posed by our problem.
The key steps of the SC-DO-MUOA algorithm are as
follows: 1) Problem decomposition: The dual-objective opti-
mization problem is divided into a set of scalar subproblems
with corresponding weight vectors, thereby constructing an
approximate search space for the Pareto solution set. 2) Cou-
pling treatment for variables (Solution generation): The UA V
trajectories, power allocation, user association, and target
association variables are jointly encoded as individual chro-
mosomes or particle vectors, generated through our proposed
adaptive hybrid generator to jointly optimize during every
solution generation and update process. 3) Population update:
An external archive mechanism and neighborhood update
strategy are employed to reﬁne and maintain the Pareto
front, improving convergence quality and solution diversity.
4) Convergence guarantee: HV metric tracks the evolution
of the Pareto front. If HV improvement stays below a set
threshold for several generations, the algorithm is considered
to have converged. A maximum iteration limit is also set to
ensure timely termination with stable, high-quality solutions.
The details are as follows.
A. Problem Decomposition
Similarly to other MOEA/D algorithms, we ﬁrst decompose
the dual-objective problem into D single-objective opti-
mization subproblems, indexed by d = 1 , 2,...,D . Each
subproblem d is associated with a weight vector λd ={
λd1,...,λ dm}, where ∑mi=1λdi = 1 and m is the number of
objectives, here, m = 2. Speciﬁcally, each individual weight
can be selected from the set
{
0
D−1, 1D−1,... D−1D−1
}
according
to [45], [46]. The goal is to optimize each subproblem simulta-
neously, which collectively approximates the PF. Furthermore,
considering the numerous constraints in our problem, we
introduce a penalty function into the objective function to
guide population generation. Therefore, the subproblem d can
be expressed as follows:
min
P,A,C,Q
yd(x) =
m∑
i=1
λdifi(x) +γg(x)
s.t. x∈ Ω, (28)
where fi is the normalized objective function, deﬁned as
fi = f ′i−fminifmaxi −fmini . fmaxi and fmini are the maximum andminimum values of the objective function fi in the current
population, respectively. According to our problem, f′1 =
− 1N∑Nn=1∑Mm=1∑Kk=1Rm,k[n] and f′2 = ∑Jj=1CRB vj .
Similarly, let all penalty terms normalize and have the same
penalty weight γ within the range of [1, 10] to ensure the fea-
sibility of the solutions. Then, the penalty g can be expressed
as g =∑3i=1 g′i−gminigmaxi −gmini . According to our constraints, g′1 =∑N
n=1
∑M
m=1 max(0,‖qm[n]− qm[n− 1]‖− Vmaxδt), g′2 =∑N
n=1
∑M
m=1
∑M
g⁄=m max(0,dmin−‖ qm[n]− qg[n]‖), and
g′3 = ∑Kk=1∑Ll=1 max(0,Rthk − 1NL∑lNLn=(l−1)NL+1∑Mm=1
αm,k[n]Rm,k[n]). Besides, variable ranges can be restricted
directly at the time of deﬁnition. And the other constraints
are integer constraints, which we will handle in the algorithm
below. The feasible solution set is Ω.
Additionally, we deﬁne the subproblems which have the Ne
closest weight vectors to λd in terms of Euclidean distance as
the neighbours of subproblem d, donated asBd. According to
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10073
the EAG-MOEA/D algorithm, deﬁne the best solutions to all
the subproblems up to the current iteration as population E
andD solutions selected by NSGA-II [47] (the nondominated
sorting approach and crowding distance assignment) as the
external archive population Z.
B. New Solution Generation
We propose a novel adaptive hybrid generator to generate
new populations. The strategy combines PSO’s fast local
search with GA’s global exploration. When the algorithm
is likely to get stuck in a local optimum, the population
generator automatically switches from PSO to GA to over-
come local convergence issues. Conversely, PSO generator is
used to accelerate exploration. Therefore, the hybrid generator
effectively integrates the fast convergence properties of PSO
and the diversity-preserving capabilities of GA, signiﬁcantly
accelerating overall convergence speed, improving search efﬁ-
ciency, and reducing the probability of getting trapped in a
local optimum. Moreover, we incorporate adaptive parameter
control to further balance convergence and diversity, enhancing
the search performance. The speciﬁc process of generating a
new solution of subproblem d is as follows:
Note that HV is deﬁned as the hypervolume between the
estimated Pareto front and the reference vector, whose changes
can reﬂect whether the population is convergent to a certain
extent. Therefore, we deﬁne ∆k =HV k−HV k−1. When ∆k
is lower than a certain threshold for 5 consecutive iterations,
it may be trapped in the local optimum, and we switch from
PSO operator to genetic operator, and vice versa.
For the genetic operator, we introduce dynamic adjustment
of the selection probability Pselect, crossover probability Pc,
and mutation probability Pm of the current individual d as
follows [48], [49]:
Pselect,d = Fd∑D
d=1Fd
, (29)
Pc,d =



Pmaxc − (Pmaxc −Pminc )(F′d−Favg)Fmax−Favg ,F′d≥Favg,
Pmaxc ,F′d <F avg,
(30)
Pm,d =



Pmaxm − (Pmaxm −Pminm )(Fd−Favg)Fmax−Favg ,Fd≥Favg,
Pmaxm ,Fd <F avg.
(31)
To better match the search-space scales, we adopt simple
linear models of the number of UA Vs M based on our
simulations to enable dynamic initialization adjustment of
the GA/PSO parameters. Speciﬁcally, set the maximum and
minimum crossover probability Pmaxc = 0.8 + 0.002M and
Pminc = 0.5 + 0.002M, respectively. Set the maximum and
minimum mutation probability Pmaxm = 0 .15− 0.001M
and Pminm = 0.09− 0.0008M, respectively. Therefore, for
the smaller UA V scales, slightly lower crossover preserves
good structures and reduces redundant exploration, yielding
faster, more stable convergence and better solutions; for larger
scales, moderately higher values enhance global exploration
and improve ﬁnal results. Fd is the ﬁtness value of the
individual d, while Fmax and Favg are the maximum and
average ﬁtness values of the current population. F′d represents
the higher ﬁtness between the two parents. In multi-objective
optimization, the ﬁtness value can incorporate Pareto rank and
crowding distance to better represent individual superiority
[47]. Here we deﬁne F−1d = rank(d) + 1Distance(d). This
adaptive adjustment of crossover and mutation probabilities
helps to retain favorable genes when ﬁtness is high and
promotes diversity when ﬁtness is low, thereby improving
algorithm efﬁciency. And the simulated binary crossover is
employed. Generate the offspring solutions xdk+1,c with the
parent solutions of kth generation, i.e., xb1k and xb2k, by the
following crossover:
xdk+1,c =((1 +β)xb1k + (1−β)xb2k)/2, (32)
whereβ is the spread factor of the simulated binary crossover,
satisfying β = (2u)
1
ηc +1 if u≤ 0.5, otherwise, β = (2(1−
u))− 1ηc +1 , where u uniformly distributs on the interval [0, 1]
and ηc = 20 [47], [50]. Then, employ polynomial mutation
to further explore the solution space. Obtain the mutated
solutions xdk+1,m by:
xdk+1,m = xdk+1,c +δd(Ub− Lb), (33)
where Lb and Ub are the corresponding lower and upper
bounds of the solutions.δd is the perturbation factor, satisfying
δd =
(
2r + (1− 2r)
(
1− xdk+1,c−LbUb−Lb )ηm+1) 1ηm+1 −
1, if r ≤ 0.5, otherwise, δd = 1 −(
2(1−r) + 2(r− 0.5)
(
1− Ub−xdk+1,cUb−Lb )ηm+1) 1ηm +1 ,
where r uniformly distributs on the interval [0, 1] and
ηm = 20 [47], [50].
For the PSO operator, each particle represents a potential
solution of the corresponding subproblem, and the particle
swarm gradually approaches the optimal solution by continu-
ously updating its position and velocity [51]. Here, deﬁne the
velocity of particle d of kth generation as vdk, the individual
best position of kth generation as edk, where edk∈ E, and
the global best position of kth generation in its neighborhood
as zdk, where ydk ∈ E. Then, we generate new solutions
using the following rules:
vdk+1 =ωvdk +c1r1(edk− xdk) +c2r2(zdk− xdk),
(34)
xdk+1,p = xdk + vdk+1, (35)
where ω is the inertia weight, which controls the inﬂuence
of the particle’s current velocity. c1 and c2 are the cognitive
and social coefﬁcients, respectively. r1 and r2 are the ran-
dom numbers uniformly distributed on the interval [0, 1]. We
employ a linear-varying strategy to adapt the inertia weight
ω and learning coefﬁcients c1 and c2 over iterations. These
parameters are deﬁned as:
ω =ωmax− (ωmax−ωmin)kKmax , (36)
c1 =cmax− (cmax−cmin)kKmax , (37)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

10074 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
c2 =cmin + (cmax−cmin)kKmax , (38)
where k is the current iteration and Kmax is the total
number of iterations. Similar to the dynamic initialization
of parameters in AGA, we set the maximum inertia weight
ωmax = 0 .8 + 0.002M and the minimum inertia weight
ωmin = 0.3 + 0.002M. Given the relatively minor effects
with UA V scale in our experiments, we set cmax = 2 .5,
and cmin = 0.5 according to [52] and [53]. This adaptive
strategy allows for larger step sizes during the early iterations
to enhance global exploration and progressively reduces the
search range to improve convergence in later stages.
Now, we obtain the new solution xdk+1,p or xdk+1,m of
subproblem d through the hybrid operator integrating PSO
and GA. However, the solutions generated by PSO or genetic
operators might not satisfy the constraints, especially for the
binary variables. Therefore, to better satisfy the constraints,
we apply correction factors to obtain the ﬁnal solution xdk+1.
Speciﬁcally, for the zero-one variables, we preserve the gen-
erated solutions as much as possible and adjust only the
infeasible entries. When multiple UA Vs are assigned to the
same user, we retain the assignment with the nearest UA V–user
and set the others to 0. Deﬁne the solution set of all the
subproblems as X.
C. Population Update
To more effectively leverage local search capabilities, accel-
erate convergence, and maintain diversity, we ﬁrst consider
updating the solutions of the neighbour sets. For each solution
xdk+1, we compare it with the solutions of all neighbors. If
xdk+1 performs better than the solution xbk of neighbour
subproblemb,b∈B d, in terms of the neighbour weight vector
λb, replace xbk with xdk+1. Let the updated solutions denote
as X′ and update E with X′. Then, we update the external
archive population Z. Merge X′ with Z to obtain Y = X′∪Z.
Select the best D solutions from the combined population Y
to form new Z by the NSGA-II selection.
Note that when determining if one solution is better than
another, we give more attention to constraint satisfaction. We
calculate the total constraint violation value for each solution
xdk+1 asGk+1d [54]. When there are constraint violations in a
solution (anyGk+1d > 0), we update only if the new solution’s
constraint value is less than or equal to that of the original
solution. This guides our search towards solutions that better
satisfy the constraints.
The procedure of the whole algorithm is given in the
following Algorithm 1.
D. Algorithm Complexity
We discuss the computational complexity of the proposed
SC-DO-MUOA algorithm. Obviously, the major computa-
tional cost is involved in the repetition part. We ﬁrst generate
new solutions by the hybrid operator with the computational
complexity ofO(D). Then, we update the neighbour solutions
for each subproblem and select the best D solutions based on
non-dominated sorting with the computational complexity of
Algorithm 1 SC-DO-MUOA
Input:
1) the dual-objective problem with constraints;
2) a stopping criterion;
3) D: the number of subproblems (population size);
4) λ1,...,λ D: weight vectors set for all subproblems;
5) Ne: the size of the neighbour set for each subproblem.
Initialization:
1) Decompose dual-objective problem into D subprob-
lems associated to λ1,...,λ D with penalty function.
2) Generate an initial population E ={x1k,..., xDk}
satisfying the constraints. Let k = 0.
3) Set Z = E.
4) Select Ne subproblems with the nearest weight vec-
tors to each subproblem d using Euclidean distance,
forming the neighbor set Bd for each subproblem.
Repeat
New solution generation:
for all d∈{ 1,...,D } do
a) if ∆k < ∆min for 5 consecutive iterations
Apply adaptive GA operator to generate new
solution xdk+1,m based on (32) and (33).
else
Apply adaptive PSO operator to generate new
solution xdk+1,p based on (34) and (35).
end if
b) Obtain ﬁnal solution xdk+1 by correction factors.
end for
Population update:
for all d∈{ 1,...,D } do
a) Update neighbour solutions to obtain X′.
For each b ∈ Bd of each subproblem d, set
xbk = xdk+1, if objectives yb(xdk+1 | λb) ≤
yb(xbk | λb) and constraints Gk+1d ≤ Gkb (if
min(Gkb,Gk+1d )> 0).
end for
b) Set the updated Set E = X′, Y = X′∪ Z.
c) Select the best D solutions from Y to form new
Z by NSGA-II. And calculate ∆k of Z.
Update k =k + 1.
Until satisfy the stopping criteria
Output: A set of nondominated solutions Z.
O(DNe) andO(D2), respectively. Thus, the overall complex-
ity of the proposed SC-DO-MUOA algorithm is O(D2) for
each iteration.
IV. S IMULATION RESULTS
In this section, numerical results demonstrate the efﬁciency
of our proposed dual-objective SC-DO-MUOA algorithm in
the general multi-UA V network.
A. Energy Constraints
The UA V primarily consumes energy during both ISAC
transmission and ﬂight, which limits the endurance time of our
scheme. To guarantee that total energy consumption remains
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10075
TABLE I
PARAMETERS OF ENERGY CONSTRAINTS
within the available battery energy, we derive a conservative
mission-time upper bound for optimization.
For each UA V , the power consumption for signal transmis-
sion in time slot n can be denoted by PT [n] [55]:
PT [n] =p[n] +Pconst (39)
which includes the transmit power of the UA V p[n] and
a constant power Pconst, consumed in the circuitry, signal
processing, equipment, etc. Additionally, the propulsion power
of a rotary-wing UA V can be modeled as a function of its speed
v[n] in time slot n [55], [56]:
PF [n] =P0
(
1 + 3v[n]2
U 2tip
)
+ 12d0ρsAv[n]3
+Pi
(√
1 +v[n]4
4v40 − v[n]22v20
)1/2
(40)
with the typical parameter values shown in Table I according
to [55] and [56].
Considering our 3D trajectory optimization, the total energy
consumption model of N slots with duration δt can be
approximately expressed as follows [57]:
Etot =
N∑
n=1
(PT [n] +PF [n])δt + MUAV (v[N]2−v[1]2)2
+MUAVg(qz[N]−qz[1]) (41)
where MUAV is the UA V mass, and g is the gravitational
acceleration. The last two terms capture the net changes of
kinetic and gravitational potential energy between the start and
end of the mission.
To ensure feasibility in real deployment, we enforce the
battery-energy constraint:
Etot≤Ebat (42)
where Ebat is the available battery energy of the UA Vs.
As observed from the function curve in Fig. 2 in [55], the
propulsion powerPF [n] achieves its maximum atv[n] =Vmax
in our scenario, hence PF [n] ≤ PmaxF ∆=PF (Vmax). Using
these worst-case bounds and denoting T = Nδt, we obtain
the upper bound of the total energy consumption:
T (PmaxT +PmaxF ) +MUAVV 2max2
Fig. 4. Comparison of dual objectives: communication sum rate and sensing
CRB against baseline schemes.
Fig. 5. Comparison of 3D UA V trajectories and locations by different schemes
with ηCRB = 15 and ψ = 0.5.
+MUAVg(Hmax−Hmin)≤Ebat (43)
where PmaxT = Pmax + Pconst. And we instantiated the
boundary values withv[N] =Vmax,v[1] = 0,qz[N] =Hmax,
and qz[1] = Hmin. Solving the inequality for T provides the
worst-case feasible mission time:
Tmax≈ 33s (44)
We then set the whole mission period as T = Tmax for
optimization to guarantee feasibility in deployment.
B. Simulation Setups
The ground users and targets are randomly and uniformly
distributed in a 2-dimension area of 2 km ×2 km, as shown
in Fig. 6. Set the number of the users and targets as K = 12
and J = 4 , respectively, which are served by M = 4
UA Vs in the whole mission period T = 33 s. The settings
are the same unless otherwise speciﬁed for the following
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

10076 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 6. Top view of the comparison of the UA V trajectories and locations by
different schemes with ηCRB = 15 and ψ = 0.5.
TABLE II
SIMULATION PARAMETERS
simulations. The major simulation parameters are given in
Table II, which are selected according to [9], [15], [16], [39],
and [40]. Additionally, for all the multi-objective optimization
algorithms, we set the population size D = 50, the neighbor
size Ne = 5 , and the maximum iteration Kmax = 600 for
the small-scale UA V networks (M < 50 UA Vs); and set the
population size D = 100 , the neighbor size Ne = 10 , and
the maximum iteration Kmax = 1200 for the large-scale UA V
networks (M≥ 50 UA Vs). The performance results below are
obtained through Monte Carlo simulations.
C. Simulation Results
To the best of our knowledge, there has been no sim-
ilar work addressing the dual objectives of improving the
communication rate and the sensing CRB for the UA V-ISAC
scenarios, especially in multi-UA V ISAC scenarios. Therefore,
we select the two most relevant works as baselines and extend
them to the same scenario as ours to compare with our pro-
posed SC-DO-MUOA. We also compare with the traditional
multi-objective algorithms NSGA-II and EAG-MOEA/D to
further validate the effectiveness of our algorithm.
1) Weighted dual-objective scheme [15], where a single
UA V serves multiple users while sensing multiple tar-
gets. The objective is to maximize a weighted sum of
the communication rate and the negative of the sensing
CRB. Following the principles proposed in [15], the
UA V trajectory is primarily determined by the successive
convex approximation (SCA) algorithm, and the transmit
power is set according to a maximum power strategy. To
extend this scheme to multi-UA V scenarios, we adopt the
UA V clustering method [16] to group users and targets,
with each cluster served by a dedicated UA V . Addition-
ally, the computational complexity is polynomial over
O(N 3.5 log(1/ϵ)), where ϵ> 0 is a solution accuracy.
2) Constrained single-objective scheme [16], where mul-
tiple UA Vs serve the communication users while
cooperatively sensing a single target. The objective is to
maximize the network utility based on communication
rate, subject to the CRB localization accuracy constraint.
This scheme balances UA V sensing and communica-
tion by optimizing one aspect under constraints on the
other. Speciﬁcally, following the principles proposed in
[16], the UA V locations are determined using spectral
clustering to group users, while the user association
and UA V transmission power control rely mainly on
coalition game theory and SCA algorithms, respectively.
Note that the trajectory and placement optimizations can
be compared based on the average instantaneous sum-
rate objective. According to [16], the total computational
complexity is polynomial over O(KM ).
3) EAG-MOEA/D algorithm [46], an external archive-
guided multi-objective evolutionary algorithm based on
decomposition method. And the computational complex-
ity is polynomial over O(D2).
4) NSGA-II algorithm [47], a widely used multi-objective
genetic algorithm with fast non-dominated sorting and
crowding distance calculation. And the computational
complexity is polynomial over O(D2).
Fig. 4 illustrates the distribution of solutions for the
dual-objective optimization, and each point represents the
performance across two dimensions: communication sum rate
and sensing CRB. We obtained the optimization results of the
weighted dual-objective scheme and the constrained single-
objective scheme under the different CRB thresholds, i.e.,
ηCRB = [9 , 25], and the different weighting factors, i.e.,
ψ = [0.1, 0.9], respectively, as shown by the pentagon and
triangle markers in the ﬁgure.
Note that higher communication rates and lower CRB
values indicate superior performance; thus, points closer to
the bottom-right in the graph represent better solutions. Fig. 4
clearly demonstrates that our proposed SC-DO-MUOA sig-
niﬁcantly outperforms the weighted and constrained schemes
in terms of both the sum rate and the CRB. This is because
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10077
Fig. 7. Sum rate comparison with weighted dual-objective and constrained
single-objective schemes under increasing communication users.
our SC-DO-MUOA simultaneously considers the communi-
cation and sensing objectives, more effectively utilizes the
overall resources, and manages the interference in multi-
UA V ISAC scenarios. Additionally, the dual-objective model
can overcome the rigid priority constraints of single-objective
methods and biases from subjective weighting factors in
weighted dual-objective schemes, fully exploiting the potential
of both communication and sensing. Moreover, our SC-DO-
MUOA achieves a superior Pareto front (PF) compared to the
EAG-MOEA/D and NSGA-II algorithms, further validating
its effectiveness in balancing communication and sensing
performance.
We compare the 3D UA V trajectories and locations
optimized by different schemes in Fig. 5, selecting two high-
performing baseline solutions (with ηCRB = 15 andψ = 0.5)
from Fig. 4 for comparison. In order to show the differences
of the UA V trajectories more clearly, we plot the top view of
these trajectories in Fig. 6. As shown in Fig. 6, the trajectories
of our SC-DO-MUOA are closer to both the communication
users and the sensing targets compared to baseline trajectories.
And the optimized ﬂight trajectories by our SC-DO-MUOA
enable the UA Vs to serve the most suitable users and targets
at optimal times and locations to improve the whole channel
conditions, thus improving the overall system sum rate and
sensing accuracy. Moreover, the UA Vs can make dynamic
altitude adjustment to more ﬂexibly optimize the sensing
perspectives and mitigate interference.
In Fig. 7 and Fig. 8, we compare these UA V-ISAC schemes
under increasing number of communication users by eval-
uating the average performance of PS solutions. It can be
observed that our proposed dual-objective SC-DO-MUOA
consistently achieves the highest communication sum rate and
the best sensing CRB performance among all the UA V-ISAC
schemes. This advantage is primarily due to the dual-objective
optimization employed by SC-DO-MUOA, which enables
more ﬂexible resource allocation and efﬁcient trajectory
Fig. 8. Sensing CRB comparison with weighted dual-objective and con-
strained single-objective schemes under increasing communication users.
planning, effectively balancing communication and sensing
tasks while mitigating interference. Notably, there is an opti-
mal user-serving capacity in Fig. 7 due to the trade-off between
improved resource utilization and increased interference with
additional users. Nevertheless, our proposed SC-DO-MUOA
algorithm still maintains robust and effective performance even
when other schemes experience great performance degrada-
tion. Additionally, the increased number of users competing
for sensing resources results in reduced sensing accuracy and
elevated CRB values in Fig. 8. However, the SC-DO-MUOA
exhibits the slowest rate of increase in CRB among these
schemes due to its effective balancing of resources between
sensing and communications.
With the increasing number of UA Vs, we compare differ-
ent UA V-ISAC schemes in terms of both the sum rate and
the CRB. As shown in Fig. 9 and Fig. 10, our SC-DO-
MUOA algorithm consistently outperforms the weighted and
constrained schemes in both performances. Notably, Fig. 9
shows that the increasing speed of the sum rate begins to
decrease when the number of UA Vs increases to 16. This
is because the increasing UA Vs introduce more signiﬁcant
interference, thereby slowing down the improvement of sum
rate. However, despite this slowdown, the performance gap
between algorithms continues to expand with the increasing
number of UA Vs because of our SC-DO-MUOA’s superior
ability to exploit the growing UA V resources and dynamically
adjust UA V altitudes. Similarly, in Fig. 9, the interference also
slows down the rate of improvement in sensing CRB as the
number of UA Vs increases. In contrast, the CRB even worsens
under the weighted and constrained schemes. These results
clearly demonstrate that our SC-DO-MUOA algorithm not
only scales effectively but also consistently delivers superior
performance as the UA V network expands.
Fig. 11 and Fig. 12 compare the performance of the
proposed SC-DO-MUOA with the baseline schemes as the
maximum UA V power, Pmax, increases. In both sum rate
and CRB, our SC-DO-MUOA consistently outperforms the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

10078 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 9. Sum rate comparison with weighted dual-objective and constrained
single-objective schemes in the increasing number of UA Vs, and users K =
40, targets J = 12.
Fig. 10. Sensing CRB comparison with weighted dual-objective and con-
strained single-objective schemes in the increasing number of UA Vs, and users
K = 40, targets J = 12.
other two schemes. This advantage primarily arises from our
algorithm’s effective power allocation strategy, coupled with
its adaptive optimization of UA V trajectories and user asso-
ciations based on power control, enabling superior resource
utilization. Additionally, as power continues to increase, the
interference also increases, leading to slower improvement in
sum rate and CRB. However, our SC-DO-MUOA’s superior
interference management mitigates this effect, enabling it to
maintain a higher growth (descent for CRB) rate in sum rate
compared to the other schemes.
To further analyze the complexity and scalability of the
SC-DO-MUOA algorithm, particularly in large-scale UA V
networks, we compare its performance with EAG-MOEA/D
and NSGA-II in terms of computational runtime, memory
usage, convergence speed, and HV in different network scales,
Fig. 11. Sum rate comparison with weighted dual-objective and constrained
single-objective schemes under the increasing UA V maximum power Pmax.
Fig. 12. CRB comparison with weighted dual-objective and constrained
single-objective schemes under the increasing UA V maximum power Pmax.
as shown in Table III. Additionally, all the experiments were
conducted on a desktop PC running Windows 10, equipped
with an Intel Core i7-1165G7 CPU @ 2.80GHz, 16GB DDR4
RAM, and MATLAB 2023a. Here, we did not use any parallel
acceleration techniques. In practical applications, leveraging
high-performance computing platforms (such as GPU parallel
computing or edge device optimization) can further reduce the
runtime and enhance the system’s ability to respond to real-
time environments.
The results clearly demonstrate that our SC-DO-MUOA
algorithm outperforms the other algorithms in terms of runtime
efﬁciency and convergence speed, particularly in larger-scale
UA V networks. Moreover, HV is a widely used metric for
evaluating multi-objective optimization algorithms and the
larger HV value implies that our algorithm has a larger size
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10079
TABLE III
PERFORMANCE COMPARISON OF SC-DO-MUOA, EAG-MOEA/D,
AND NSGA-II
Fig. 13. HV comparison with the number of UA Vs M = 50 and reference
point [1.1, 1.1].
of covered space and achieves better performance regarding
both convergence and diversity. Speciﬁcally, Fig. 13 is the HV
comparison with increasing iterations when the network scale
is M = 50 UA Vs. It clearly shows that our algorithm con-
verges faster than EAG-MOEA/D and effectively avoids the
local optima problem encountered by NSGA-II. Therefore, the
experimental results validate the robustness and effectiveness
of our SC-DO-MUOA in large-scale UA V deployments.
D. Discussions
We explicitly discuss the limitations and scalability of the
SC-DO-MUOA algorithm. Because the problem is NP-hard,
approximate strategies (such as objective-space decomposition
we adopted) are required, which may lead to suboptimal solu-
tions or limited convergence speed. Moreover, as the problem
size increases signiﬁcantly, the computational complexity may
grow exponentially. Even so, the results in Table III show
that even with 100 UA Vs, 100 users, and 20 targets, SC-DO-
MUOA still outperforms baselines, reducing the runtime by
half and improving solution quality by 20%, demonstrating
strong scalability. Nevertheless, the exponential growth of the
search space due to the larger problem scale still poses chal-
lenges in terms of the computational burden and performance
for ultra-large-scale and real-time applications. To address
these challenges, we will explore multi-stage optimization,
parallel computing, and distributed processing methods in
future work to further enhance scalability.
V. C ONCLUSION
This paper investigated ISAC in a more general multi-UA V
network, where the UA Vs provided downlink communica-
tions to multiple ground users while sensing the locations
of multiple ground targets. We also consider the complicated
interference management among the UA Vs to make the sce-
nario more practical. Note that in such an ISAC scenario,
the UA Vs need to coordinate and schedule communication
and sensing tasks, balance resource competition, and design
efﬁcient ﬂight trajectories to enhance both communication
and sensing performance. This results in a complicated and
challenging joint optimization problem in terms of the UA V
trajectories, the both user and target associations, and the
power control. Furthermore, to overcome the potential perfor-
mance limitations of existing single-objective and weighted
approaches, we proposed a dual-objective model to further
optimize ISAC, aiming for a better tradeoff between commu-
nication and sensing performance. Speciﬁcally, we proposed
an efﬁcient SC-DO-MUOA to improve both the communi-
cation sum rate and the sensing CRB. Simulation results
demonstrated that our proposed SC-DO-MUOA outperformed
various baselines in terms of both communication and sensing
performance.
REFERENCES
[1] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets integrated
sensing and communication: Challenges and future directions,” IEEE
Commun. Mag. , vol. 61, no. 5, pp. 62–67, May 2023.
[2] J. Zhang, M. Sheng, C. Xing, J. Liu, N. Zhao, and G. K. Karagiannidis,
“Generative-adversarial-network-enhanced DRL for ISAC with double
active RISs,” IEEE Internet Things J., vol. 12, no. 10, pp. 13487–13499,
May 2025, doi: 10.1109/JIOT.2025.3527441.
[3] J. Zhang et al., “Intelligent waveform design for integrated sensing and
communication,” IEEE Wireless Commun. , vol. 32, no. 1, pp. 166–173,
Feb. 2025.
[4] J. Zhang, M. Liu, J. Tang, N. Zhao, D. Niyato, and X. Wang, “Joint
design for RIS-aided ISAC via deep unfolding learning,” IEEE Trans.
Cognit. Commun. Netw. , vol. 11, no. 1, pp. 349–361, Feb. 2025.
[5] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[6] Y . Shen, B. Li, R. Zhang, X. Cheng, and L. Yang, “A ﬂexible load bal-
ancing scheme in multi-UA V-enabled wireless networks,” IEEE Trans.
V eh. Technol., vol. 73, no. 6, pp. 9205–9210, Jun. 2024.
[7] L. Zhou, W. Pu, Y . Jiang, M.-Y . You, R. Zhang, and Q. Shi, “Joint
optimization of UA V deployment and directional antenna orientation
for multi-UA V cooperative sensing system,” IEEE Trans. Wireless
Commun., vol. 23, no. 10, pp. 14052–14065, Oct. 2024.
[8] K. Meng et al., “UA V-enabled integrated sensing and communication:
Opportunities and challenges,” IEEE Wireless Commun. , vol. 31, no. 2,
pp. 97–104, Apr. 2024.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

10080 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[9] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li,
“Throughput maximization for UA V-enabled integrated periodic sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 1,
pp. 671–687, Jan. 2023.
[10] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[11] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[12] W. Jiang, B. Ai, C. Shen, M. Li, and X. Shen, “Age-of-information
minimization for UA V-based multi-view sensing and communication,”
IEEE Trans. V eh. Technol., vol. 73, no. 1, pp. 1100–1114, Jan. 2024.
[13] Z. Liu, X. Liu, Y . Liu, V . C. M. Leung, and T. S. Durrani, “UA V assisted
integrated sensing and communications for Internet of Things: 3D
trajectory optimization and resource allocation,” IEEE Trans. Wireless
Commun., vol. 23, no. 8, pp. 8654–8667, Aug. 2024, doi: 10.1109/
TWC.2024.3352985.
[14] Y . Liu, S. Liu, X. Liu, Z. Liu, and T. S. Durrani, “Sensing fairness-
based energy efﬁciency optimization for UA V enabled integrated sensing
and communication,” IEEE Wireless Commun. Lett. , vol. 12, no. 10,
pp. 1702–1706, Oct. 2023.
[15] X. Jing, F. Liu, C. Masouros, and Y . Zeng, “ISAC from the sky: UA V
trajectory design for joint communication and target localization,” IEEE
Trans. Wireless Commun., vol. 23, no. 10, pp. 12857–12872, Oct. 2024,
doi: 10.1109/TWC.2024.3396571.
[16] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-UA V
networks,” IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660–2672, Apr.
2021.
[17] X. Liu, Y . Liu, Z. Liu, and T. S. Durrani, “Fair integrated sensing and
communication for multi-UA V-enabled Internet of Things: Joint 3-D
trajectory and resource optimization,” IEEE Internet Things J. , vol. 11,
no. 18, pp. 29546–29556, Sep. 2024.
[18] I. Orikumhi, H. Lee, J. Bae, and S. Kim, “ISAC-enable mobility-aware
multi-UA V placement for ultra-dense networks,” ICT Exp. , vol. 10,
no. 4, pp. 831–835, Aug. 2024.
[19] L. Zhou, S. Leng, Q. Wang, and Q. Liu, “Integrated sensing and commu-
nication in UA V swarms for cooperative multiple targets tracking,”IEEE
Trans. Mobile Comput. , vol. 22, no. 11, pp. 6526–6542, Nov. 2023.
[20] R. A. Khalil and N. Saeed, “Convex hull optimization for robust
localization in ISAC systems,” IEEE Sensors Lett. , vol. 7, no. 12,
pp. 1–4, Dec. 2023.
[21] T. Zhang, K. Zhu, S. Zheng, D. Niyato, and N. C. Luong, “Trajectory
design and power control for joint radar and communication enabled
multi-UA V cooperative detection systems,” IEEE Trans. Commun. ,
vol. 71, no. 1, pp. 158–172, Jan. 2023.
[22] Y . Pan et al., “Cooperative trajectory planning and resource allocation
for UA V-enabled integrated sensing and communication systems,”IEEE
Trans. V eh. Technol., vol. 73, no. 5, pp. 6502–6516, May 2024.
[23] W. Ding et al., “Multi-UA V-enabled integrated sensing and commu-
nications: Joint UA V placement and power control,” in Proc. IEEE
Globecom Workshops (GC Wkshps) , Kuala Lumpur, Malaysia, Dec.
2023, pp. 842–847.
[24] Y . Liu et al., “Secure rate maximization for ISAC-UA V assisted
communication amidst multiple eavesdroppers,” IEEE Trans. V eh.
Technol., vol. 73, no. 10, pp. 15843–15847, Oct. 2024, doi: 10.1109/
TVT.2024.3412805.
[25] Y . Cui, Z. Feng, Q. Zhang, Z. Wei, C. Xu, and P. Zhang, “Toward trusted
and swift UA V communication: ISAC-enabled dual identity mapping,”
IEEE Wireless Commun. , vol. 30, no. 1, pp. 58–66, Feb. 2023.
[26] J. Beuster et al., “Sounding-based evaluation of multi-sensor
ISAC networks for drone applications: Measurement and simulation
perspectives,” in Proc. IEEE 4th Int. Symp. Joint Commun. Sens. , Mar.
2024, pp. 1–6.
[27] I. Orikumhi, J. Bae, and S. Kim, “Mobility-aware resource allocation
in UA V-assisted ISAC networks,” inProc. 14th Int. Conf. Inf. Commun.
Technol. Converg. (ICTC), Oct. 2023, pp. 1042–1044.
[28] Y . Zheng, L. Li, W. Lin, W. Liang, Q. Du, and Z. Han, “Resource
allocation based on optimal transport theory in ISAC-enabled multi-
UA V networks,” 2024, arXiv:2410.02122.
[29] R. M. Azadur, C. J. Pawase, and K. Chang, “Multi-UA V path planning
utilizing the PGA algorithm for terrestrial IoT sensor network under
ISAC framework,” Trans. Emerg. Telecommun. Technol., vol. 35, no. 1,
p. 4916, Jan. 2024.
[30] X. Xu, R. Tao, S. Li, and Y . Chen, “Collaborative UA V deployment
and task allocation for environment sensing in multi-UA V networks,” in
Proc. IEEE Int. Conf. Unmanned Syst. (ICUS) , Oct. 2022, pp. 738–743.
[31] J. Wu, W. Yuan, and L. Bai, “On the interplay between sensing and
communications for UA V trajectory design,” IEEE Internet Things J. ,
vol. 10, no. 23, pp. 20383–20395, Dec. 2023.
[32] Y . Qin, Z. Zhang, X. Li, W. Huangfu, and H. Zhang, “Deep rein-
forcement learning based resource allocation and trajectory planning
in integrated sensing and communications UA V network,” IEEE Trans.
Wireless Commun., vol. 22, no. 11, pp. 8158–8169, Nov. 2023.
[33] M. Wang, P. Chen, Z. Cao, and Y . Chen, “Reinforcement learning-based
UA Vs resource allocation for integrated sensing and communication
(ISAC) system,” Electronics, vol. 11, no. 3, p. 441, Feb. 2022.
[34] H. Li, M. Xiao, K. Wang, D. I. Kim, and M. Debbah, “Large language
model based multi-objective optimization for integrated sensing and
communications in UA V networks,” IEEE Wireless Commun. Lett. ,
vol. 14, no. 4, pp. 979–983, Apr. 2025.
[35] Y . Xiong, F. Liu, Y . Cui, W. Yuan, T. X. Han, and G. Caire, “On
the fundamental tradeoff of integrated sensing and communications
under Gaussian channels,” IEEE Trans. Inf. Theory , vol. 69, no. 9,
pp. 5723–5751, Sep. 2023.
[36] M. A. Jasim, H. Shakhatreh, N. Siasi, A. H. Sawalmeh, A. Aldalbahi,
and A. Al-Fuqaha, “A survey on spectrum management for unmanned
aerial vehicles (UA Vs),”IEEE Access, vol. 10, pp. 11443–11499, 2022.
[37] H. Koumaras et al., “5G-enabled UA Vs with command and control soft-
ware component at the edge for supporting energy efﬁcient opportunistic
networks,” Energies, vol. 14, no. 5, p. 1480, Mar. 2021.
[38] Q. Wu, Y . Zeng, and R. Zhang, “Joint trajectory and communication
design for multi-UA V enabled wireless networks,”IEEE Trans. Wireless
Commun., vol. 17, no. 3, pp. 2109–2121, Mar. 2018.
[39] X. Wang, Z. Fei, J. Huang, J. A. Zhang, and J. Yuan, “Joint resource
allocation and power control for radar interference mitigation in multi-
UA V networks,”Sci. China Inf. Sci. , vol. 64, no. 8, Aug. 2021, Art. no.
182307.
[40] J. Zhang, Z. Fei, X. Wang, P. Liu, J. Huang, and Z. Zheng, “Joint
resource allocation and user association for multi-cell integrated sensing
and communication systems,” EURASIP J. Wireless Commun. Netw. ,
vol. 2023, no. 1, pp. 1–19, Jul. 2023.
[41] S. M. Kay, Fundamentals of Statistical Signal Processing: Estimation
Theory. Upper Saddle River, NJ, USA: Prentice-Hall, 1993, pp. 15–67.
[42] H. Godrich, A. P. Petropulu, and H. V . Poor, “Power allocation strategies
for target localization in distributed multiple-radar architectures,” IEEE
Trans. Signal Process. , vol. 59, no. 7, pp. 3226–3240, Jul. 2011.
[43] H. Godrich, A. M. Haimovich, and R. S. Blum, “Target localization
accuracy gain in MIMO radar-based systems,” IEEE Trans. Inf. Theory ,
vol. 56, no. 6, pp. 2783–2803, Jun. 2010.
[44] J. Li, H. Kang, G. Sun, S. Liang, Y . Liu, and Y . Zhang, “Physical
layer secure communications based on collaborative beamforming for
UA V networks: A multi-objective optimization approach,” inProc. IEEE
INFOCOM - IEEE Conf. Comput. Commun. , Vancouver, BC, Canada,
May 2021, pp. 1–10.
[45] Q. Zhang and H. Li, “MOEA/D: A multiobjective evolutionary algorithm
based on decomposition,” IEEE Trans. Evol. Comput. , vol. 11, no. 6,
pp. 712–731, Dec. 2007.
[46] X. Cai, Y . Li, Z. Fan, and Q. Zhang, “An external archive guided
multiobjective evolutionary algorithm based on decomposition for com-
binatorial optimization,” IEEE Trans. Evol. Comput. , vol. 19, no. 4,
pp. 508–523, Aug. 2015.
[47] K. Deb, A. Pratap, S. Agarwal, and T. Meyarivan, “A fast and elitist
multiobjective genetic algorithm: NSGA-II,” IEEE Trans. Evol. Com-
put., vol. 6, no. 2, pp. 182–197, Apr. 2002.
[48] C. Zhang, X. Wen, C. Li, W. Zheng, L. Yu, and Z. Lu, “Dynamic
rapid scheduling algorithm for vehicle time sensitive communication
based on CILP and AGA,” IEEE Trans. V eh. Technol., vol. 72, no. 11,
pp. 15014–15027, Nov. 2023.
[49] W. Jiangxiong, L. Qiankuan, J. Liandian, T. Benke, and T. Junyang,
“Research on intelligent substation secondary circuit fault location based
on AGA-PSO algorithm,” in Proc. 6th Asia Energy Electr . Eng. Symp.
(AEEES), Mar. 2024, pp. 1075–1081.
[50] Y . Tian, W. Zhu, X. Zhang, and Y . Jin, “A practical tutorial on solv-
ing optimization problems via PlatEMO,” Neurocomputing, vol. 518,
pp. 190–205, Jan. 2023.
[51] S. Z. Mart ´ınez and C. A. C. Coello, “A multi-objective particle swarm
optimizer based on decomposition,” in Proc. 13th Annu. Conf. Genetic
Evol. Comput. , Jul. 2011, pp. 69–76.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply. 

GUO et al.: ISAC IN MULTI-UA V NETWORKS: A DUAL-OBJECTIVE OPTIMIZATION PERSPECTIVE 10081
[52] S. Liu, “An improved particle swarm algorithm for UA V path planning,”
in Proc. IEEE Int. Conf. Image Process. Comput. Appl. (ICIPCA) , Aug.
2023, pp. 949–953.
[53] A. Ratnaweera, S. K. Halgamuge, and H. C. Watson, “Self-organizing
hierarchical particle swarm optimizer with time-varying acceleration
coefﬁcients,” IEEE Trans. Evol. Comput. , vol. 8, no. 3, pp. 240–255,
Jun. 2004.
[54] H. Jain and K. Deb, “An evolutionary many-objective optimization
algorithm using reference-point based nondominated sorting approach,
part II: Handling constraints and extending to an adaptive approach,”
IEEE Trans. Evol. Comput. , vol. 18, no. 4, pp. 602–622, Aug. 2014.
[55] M. B. Yilmaz, L. Xiang, and A. Klein, “Joint beamforming and trajec-
tory optimization for UA V-enabled ISAC under a ﬁnite energy budget,”
in Proc. IEEE Int. Conf. Commun. Workshops (ICC Workshops) , Jun.
2024, pp. 1876–1881.
[56] Y . Zeng, J. Xu, and R. Zhang, “Energy minimization for wireless
communication with rotary-wing UA V ,”IEEE Trans. Wireless Commun.,
vol. 18, no. 4, pp. 2329–2345, Apr. 2019.
[57] H. Pan, Y . Liu, G. Sun, J. Fan, S. Liang, and C. Yuen, “Joint power
and 3D trajectory optimization for UA V-enabled wireless powered com-
munication networks with obstacles,” IEEE Trans. Commun. , vol. 71,
no. 4, pp. 2364–2380, Apr. 2023.
Xu Guo (Student Member, IEEE) received the
B.E. degree in network engineering from Southwest
Jiaotong University, Chengdu, China, in 2021. She
is currently pursuing the Ph.D. degree with the
School of Electronics, Peking University, Beijing,
China. Her current research interests include UA V
communications, wireless resource allocation, and
integrated sensing and communication networks.
Jingcheng Shi (Graduate Student Member, IEEE)
received the B.E. degree in communication engineer-
ing from Dalian Maritime University, Dalian, China,
in 2022. He is currently pursuing the Ph.D. degree
with the School of Electronics, Peking University,
Beijing, China. His current research interests include
integrated sensing and communications, signal pro-
cessing, and wireless resource allocation.
Jianjun Wu (Member, IEEE) received the B.S.,
M.S., and Ph.D. degrees from Peking University,
Beijing, China, in 1989, 1992, and 2006, respec-
tively. Since 1992, he has been joined the School
of Electronics Engineering and Computer Science,
Peking University. He was a Professor with Peking
University in 2014. His research interests include the
areas of satellite communications, wireless commu-
nications, and communications signal processing.
Rongqing Zhang (Member, IEEE) received the B.S.
and Ph.D. degrees (Hons.) from Peking University,
Beijing, China, in 2009 and 2014, respectively.
He is currently an Associate Professor with The
Hong Kong University of Science and Technology
(Guangzhou), Guangzhou, China. Before joining
HKUST(GZ), he held faculty positions at Tongji
University and Colorado State University. His
research interests include vehicular communications
and networking, low-altitude vehicular networks,
and connected intelligence. He has authored and
co-authored three monographs and over 200 papers in top journals and
conferences, with three Best Paper Awards at the IEEE ICC 2016, GLOBE-
COM 2018, and ICC 2019. He also received the 2017 First-Class Prize in
Natural Science of Ministry of Education of China, the 2023 First-Class
Prize in Natural Science of Chinese Association of Automation, and the 2023
First-Class Prize in Natural Science of China Institute of Communications.
Currently, he is the Secretary General of the Connected Intelligence Commit-
tee of Chinese Association of Automation, the Vice-Chair of the Information
Services Committee of IEEE ComSoc Asian–Paciﬁc Board, and an Associate
Editor of IEEE T RANSACTIONS ON VEHICULAR TECHNOLOGY and IET
Communications.
Xiang Cheng (Fellow, IEEE) received the joint
Ph.D. degree from Heriot-Watt University and The
University of Edinburgh, Edinburgh, U.K., in 2009.
He is currently a Boya Distinguished Professor
with Peking University. His research focuses on
the in-depth integration of communication networks
and artiﬁcial intelligence, including intelligent com-
munication networks and connected intelligence,
the subject on which he has published more than
280 journals and conference papers, 11 books, and
holds 32 patents. He was a recipient of the IEEE
Asia–Paciﬁc Outstanding Young Researcher Award in 2015 and the Xplorer
Prize in 2023. He was a co-recipient of the 2016 IEEE Journal on Selected
Areas in Communications Best Paper Award: the Leonard G. Abraham Prize
and the 2021 IET Communications Best Paper Award: Premium Award. He
has also received the Best Paper Awards from IEEE ITST’12, ICCC’13,
ITSC’14, ICC’16, ICNC’17, GLOBECOM’18, ICCS’18, and ICC’19. He has
been a Highly Cited Chinese Researcher since 2020. In 2021 and 2023, he was
selected into two world scientist lists, including the World’s Top 2% Scientists
released by Stanford University and top computer science scientists released
by Guide2Research. He has served as the symposium lead chair, the co-chair,
and a member of the technical program committee for several international
conferences. He led the establishment of four Chinese standards (including
industry standards and group standards) and participated in the formulation
of ten 3GPP international standards and two Chinese industry standards. He
is currently a Subject Editor of IET Communications ; an Associate Editor of
IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE T RANS -
ACTIONS ON INTELLIGENT TRANSPORTATION SYSTEMS , IEEE Wireless
Communications Letters , and Journal of Communications and Information
Networks. He was a Distinguished Lecturer of the IEEE Vehicular Technology
Society.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on April 17,2026 at 06:49:58 UTC from IEEE Xplore.  Restrictions apply.