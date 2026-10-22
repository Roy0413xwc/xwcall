---
type: literature-fulltext
title: "Joint Trajectory and Power Design With Cooperative Jamming UAV Assistance Based on Reinforcement Learning"
zotero_key: "7MZRDAU9"
pdf_key: "IQU9TML9"
doi: "10.1109/TWC.2025.3590170"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Joint Trajectory and Power Design With Cooperative Jamming UAV Assistance Based on Reinforcement Learning.md"
fulltext_path: "03fulltext/备选讲组会论文/7MZRDAU9.md"
zotero_item: "zotero://select/library/items/7MZRDAU9"
zotero_pdf: "zotero://open-pdf/library/items/IQU9TML9"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Joint Trajectory and Power Design With Cooperative Jamming UAV Assistance Based on Reinforcement Learning

> PDF 原文逐页文本抽取；来源文件 SHA-256：`1d8bddd042aa3e9f4ba3ed2405852b973c94b1115854b12a707bcd934c631f8b`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

1258 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Joint Trajectory and Power Design With
Cooperative Jamming UA V Assistance
Based on Reinforcement Learning
Yingkun Wen
 , Member , IEEE, Fengshuan Wang
 , Hui-Ming Wang
 , Senior Member , IEEE,
Junhuai Li
 , Senior Member , IEEE, Jin Qian
 , Kan Wang
 , Senior Member , IEEE, and Huaijun Wang
Abstract—We examine a secure wireless communication sys-
tem that is enabled by uncrewed aerial vehicles (UA Vs) in
this research. In the wireless communication system with an
eavesdropping UA V , we deploy a relay UA V to facilitate the trans-
mission of conﬁdential signals from the source station (denoted
as S) to ground users. Additionally, we select an idle relay UA V to
act as a cooperative jamming UA V , sending interference signals to
the eavesdropping UA V . It is quite feasible that the eavesdropping
UA V will leverage its mobility to improve the quality of its eaves-
dropping, making its trajectory unpredictable. First, to address
the worst-case scenario for the ground user’s security perfor-
mance, we assume the eavesdropping UA V approaches at the
closest distance. We aim to maximize the worst secrecy rate under
perfect CSI via designing the ﬂight trajectory and transmission
power of both the relay UA V and the jamming UA V . Second,
we investigated the performance of the system’s secrecy outage
probability under imperfect CSI. The presence of eavesdropping
UA Vs and the unpredictable nature of their environment makes
traditional convex optimization methods mathematically complex
for solving the trajectory optimization problem of the relay and
jamming UA Vs. To address this, we propose the Multi-Agent
joint design trajectory and power (MAJDTP) algorithm based on
the Multi-Agent Deep Deterministic Policy Gradient (MADDPG)
algorithm to optimize the ﬂight trajectory and transmission
power of both UA Vs. During the design and training process,
the relay and jamming UA Vs are treated as agents to derive
their optimal ﬂight paths and transmission energy. Finally, our
approach surpasses the benchmark algorithm, as demonstrated
by the simulation results.
Index Terms —Physical layer security, cooperative jamming,
cooperative relay, UA V trajectory design, reinforcement learning.
Received 14 November 2024; revised 7 April 2025; accepted 14 July 2025.
Date of publication 24 July 2025; date of current version 22 December 2025.
This work was supported in part by the National Natural Science Foundation
of China under Grant 62402381, Grant 62171364, and Grant U2468206; in
part by the Natural Science Basic Research Program of Shaanxi Province
under Grant 2025JC-OYCX-053; and in part by the Natural Science Basic
Research Plan in Shaanxi Province of China under Grant 2025JC-YBMS-650.
The associate editor coordinating the review of this article and approving it
for publication was H. Zhang. (Corresponding author: Hui-Ming Wang.)
Yingkun Wen, Fengshuan Wang, Junhuai Li, Kan Wang, and
Huaijun Wang are with the School of Computer Science and
Engineering, Xi’an University of Technology, Xi’an 710048, China
(e-mail: ykwen@xaut.edu.cn; fswang@xaut.edu.cn; lijunhuai@xaut.edu.cn;
wangkan@xaut.edu.cn; wanghuaijun@xaut.edu.cn).
Hui-Ming Wang is with the School of Information and Commu-
nication Engineering, Xi’an Jiaotong University, Xi’an 710049, China
(e-mail: xjbswhm@gmail.com).
Jin Qian is with the College of Information Engineering, Taizhou University,
Taizhou 225300, China (e-mail: qianjin@tzu.edu.cn).
Digital Object Identiﬁer 10.1109/TWC.2025.3590170
I. I NTRODUCTION
U
NMANNED aerial vehicles (UA Vs), which can be
ﬂexibly deployed as aerial relays to assist the signal
transmission between terrestrial base stations and users, are
seen as a promising technology to support mobile wireless
communication due to their mobility, ﬂexibility, and high
probability of line-of-sight (LoS) propagation [1]. However,
the spread of UA Vs by LoS presents a two-sided issue,
its broadcast characteristics expose these aerial communica-
tions to malevolent intruders and make them vulnerable to
wiretapping [2].
Drones are increasingly used in the ﬁeld of wireless com-
munications with their advantages of high mobility and ease
of deployment [3], [4], [5]. At the same time, with the
development of physical layer security technology, UA Vs can
be used as airborne mobile relays to assist in the imple-
mentation of wireless communications, or as airborne mobile
jammers to secure wireless communications [6]. However,
eavesdroppers can still take advantage of the ﬂexibility of
UA Vs to conduct more effective eavesdropping attacks on
relay UA Vs, threatening the realization of UA V wireless secure
communications [7].
Conventional encryption techniques involve substantial
computational complexity, resulting in considerable energy
consumption that may be impractical for UA V systems [8].
Physical layer security is a computationally effective solution
that uses the inherent unpredictability of wireless networks to
prevent wiretapping [9]. In order to improve communication
performance, UA Vs are designed to employ trajectory opti-
mization to ﬂy as close to ground users as possible while
avoiding eavesdroppers as much as possible [10]. Additionally,
UA Vs can function as beneﬁcial jammers to protect authorized
users by actively creating artiﬁcial noise (AN) to prevent
wiretapping eavesdroppers [11], [12], [13], [14].
Recent years have seen a signiﬁcant increase in research
interest in the PLS of UA V-assisted wireless communica-
tion systems. Xiang et al explored the concept of physical
layer security within cognitive radio-based non-orthogonal
networks featuring various primary and secondary users [15].
The cooperative jamming method is a widely used physical
layer security solution for enhancing communication security.
In [16], an undercover interference strategy targeting an
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

WEN et al.: JOINT TRAJECTORY AND POWER DESIGN WITH COOPERATIVE JAMMING UA V ASSISTANCE 1259
intelligent Eve was implemented to enhance PLS in col-
laborative CRNS. In UA V-assisted wireless communication
networks, terrestrial and aerial eavesdroppers were investigated
[17], [18], [19], [20]. Secrecy rate optimization in UA V-
assisted wireless communication networks with malicious
eavesdroppers is a signiﬁcant area of research that has been
documented in the literature [21].
Moreover, given the energy limitations of UA Vs, energy
efﬁciency is also an important research direction [22]. Zhang
et al explore a scenario involving secure communication with
a UA V , in which the UA V’s transmitter acts as the base station,
aiding ground users against eavesdroppers and UA V jammers
by collaboratively emitting artiﬁcial noise to safeguard the
UA V tra. nsmitter’s data connections via eavesdroppers [17].
Zhou et al explore a security framework within UA V-supported
networks, involving ground-based IRs and Eves, the use of a
UA V-B for sending secret messages to IRs, and the creation
of AN by a UA V-J to disrupt Eves. inhibit their access to
secret communications [18]. Wen et al explore a feasible
secure communication system enabled by UA Vs, in which the
UA V’s interceptor leverages its mobility for enhanced eaves-
dropping efﬁciency without pre-determining its path, leading
to the development of an optimizations issue [19]. Zhou et al
suggest a UA V-powered MEC system featuring ground users, a
single authentic UA V , and non-colluding eavesdropping UA Vs,
enabling non-ofﬂoading users to send interference signals to
disrupt eavesdropping UA Vs [20].
The eavesdropping UA V will actually utilize all of its
mobility to enhance the quality of its eavesdropping. In
reality, the UA V is able to instantly modify its position by
detecting its surroundings or channel conditions that are not
predictable beforehand [23]. As a result, using conventional
algorithms to predesign UA V’s path and power allocation
designs is challenging. With multiple UA Vs and GUs in
the network, the approach may not perform well and drop
into a local minimum, in spite of it could be addressed
via the convex approximation through the binary variables
relaxation [24].
Because deep reinforcement learning (DRL) has signiﬁcant
nonlinear approximation capabilities and can train neural
networks to handle complicated, model-free issues, it has
become a popular tool for UA V trajectory optimization in
uncertain situations [25], [26], [27], [28]. Liu et al suggest
an innovative UA V-RIS structure to achieve the enduring
advantages of the network that manages the RIS and to
plan the UA V’s path in wireless networks enhanced by RIS,
incorporating a diminishing learning rate deep Q an algorithm
depending on the D-DQN is employed to address the issue
of combined trajectory and phase shift design [25]. Shao et
al proposes a wireless relay communication network with
mobility nodes and a jammer powered by UA Vs to address this
unique optimization issue using DRL. given the complexity
involved in handling non-convex optimization under various
constraints, conventional convex optimization techniques fall
short [26]. Heo et al introduce an innovative structure that
merges optimization and deep learning methodologies to create
a collaborative strategy for UA Vs in secure communications
[27]. Abdalla et al developed a system for optimizing UA V
trajectories to efﬁciently cater to users and reduce eavesdrop-
per efﬁciency using the DDPG algorithm [28].
This paper examines the case when a smart UA V eaves-
dropper is present and a source station multicasts conﬁdential
information to M legitimate UA Vs. From the perspective
of ground users, we examine the problem of maximizing
the worst-case secrecy rate, assuming that the eavesdropping
UA V approaches the ground users at the shortest distance.
We optimize the trajectories and transmission energy of relay
cooperative jamming UA Vs using the MADDPG algorithm to
maximize the minimum secrecy rate.
To our knowledge, the scenario of a cooperative jamming
UA V assisting a secure communication network in the pres-
ence of an eavesdropping UA V has not been studied in the
literature. We propose the Multi-Agent joint design trajectory
and power (MAJDTP) algorithm based on the Multi-Agent
Deep Deterministic Policy Gradient (MADDPG) algorithm to
optimize the ﬂight trajectories and transmission energy of relay
and cooperative jamming UA Vs. The main contributions of this
paper are summarized as follows:
• We examine a realistic UA V-enabled secure communi-
cation network in which the eavesdropping UA V cannot
be predicted in advance and will utilize its full range of
motion for more efﬁcient eavesdropping. To ensure that
the network is communicating securely, we select a relay
UA V closest to the eavesdropper UA V and switch it to a
cooperative jamming UA V . In particular, by modifying the
relay and jamming UA V’s ﬂight paths and transmission
power, the network’s secrecy performance is enhanced.
• Due to the presence of eavesdropping UA Vs and dynamic
environment caused by its uncontrollable mobility, it is
challenging to predesign the trajectories and resource
allocations for the relay and jamming UA Vs. Thus, we
propose the MAJDTP algorithm based on the MADDPG
algorithm to optimize the ﬂight trajectory and transmis-
sion power of relay and jamming UA Vs.
• The simulation results indicate that when the eavesdrop-
ping UA V approaches the ground user, the relay UA V
adjusts its ﬂight path to minimize the eavesdropping
UA V’s signal reception. Simultaneously, the cooperative
jamming UA V alters its trajectory to further reduce
the eavesdropping UA V’s ability to intercept signals by
transmitting interference, thereby improving the system’s
security performance. Additionally, simulation results
conﬁrm that the suggested method performs better than
the benchmark algorithm in terms of secrecy rate.
II. R ELATED WORKS
Due to the wide application of UA Vs, UA V-assisted secure
communication has been deeply studied [29], [30], [31], [32].
Physical layer security (PLS) has been thoroughly investigated
as a supplement for traditional cryptographic methods in
safeguarding wireless communication [1], [33], [34], [35]. The
cooperative jamming method is a widely used physical layer
security solution for enhancing communication security [36],
[37], [38], [39]. Reinforcement learning has been developed
in communication systems as a way to solve optimization
problems [40], [41], [42], [43].
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

1260 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
The UA V has a signiﬁcant part in the procedure of assisting
the networks to communicate safely [29], [30], [31], [32].
In [29], a unique role switching mechanism was suggested
to ensure safe communication through several UA Vs work-
ing together. Jiang et al concentrated on the problems with
UA V-aided wireless networks’ secretive communication [30].
For mobile UA V assisted secure communication in Internet
of Things, Tian et al talked about the maximum secrecy
capacity problem [31]. In the face of numerous eavesdroppers,
Liu et al suggested an ISAC-UA V assisted secure communi-
cation solution [32].
In collaborative jamming drone-assisted wireless communi-
cation networks, the physical layer security of the network can
be enhanced by transmitting jamming signals to interfere with
potential eavesdroppers [44], [45], [46]. In [44], the authors
consider a scenario involving two drones that inherently
interfere with each other while transmitting their respective
private information, thereby enhancing the network’s physi-
cal layer security through collaborative interference. In [45],
the authors propose a UA V swarm framework that supports
simultaneous relay forwarding and collaborative jamming by
leveraging wireless energy harvesting. The performance of
this framework is evaluated based on the secrecy outage
probability. In [46], the authors consider a scenario where
secure communication between an information UA V and a
legitimate user is enhanced through collaborative jamming by
another UA V , with the assistance of a intelligent reﬂecting
surface.
Recent years have seen a large amount of research on
physical layer security [1], [33], [34], [35]. In [33], the
article describes the function of physical layer security in
6G wireless environment awareness security. In [34], an in-
depth examination of various features and methods applicable
in the PLA was furnished. Wang et al offered a summary of
the latest studies focusing on secure communications involving
UA Vs at the physical layer [1]. Wen et al investigated the
amalgamation of jamming and secondary signals in cognitive
radio networks (CRNs) for hidden communications, with the
goal of boosting secrecy through the use of jamming and
secondary signals in a collaborative overlay CRN [35].
Cooperative jamming technology brings a new direction to
improve system security performance [36], [37], [38], [39].
In [36], a reliable and amiable jammer selection system featur-
ing honesty is suggested for wireless cooperative systems. Xu
and Zhu conducted research on authentic eavesdropping and
protected communication within a network of multiple carriers
of interference [37]. Zheng et al investigate secret messages
exchanged between two authentic transmitter-receiver pairs
and a vigilant warden across gradually diminishing channels
[38]. Gao et al conducted research on secret communications
through collaborative jamming and choosing relays in a wire-
less relay network [39].
Recent developments in deep reinforcement learning (DRL)
algorithms may be able to help with a few secure com-
munication system issues [40], [41], [42], [43]. Guo et al
explored a contentious situation involving a genuine eaves-
dropper and a dubious pair of communicators [40]. Yang et al
researched a smart, reﬂective surface (IRS)-supported wireless
Fig. 1. System model.
secure communication system, in which an IRS is utilized
to modify its reﬂective components, ensuring the safety of
communication among several legitimate users amidst multiple
users enthusiasts of eavesdropping [41]. Yang et al explored
employing an intelligent reﬂecting surface to improve com-
munication efﬁciency against jamming and reduce interference
by modifying the reﬂective elements on the IRS surface [42].
In [43], an innovative DRL algorithm aimed at enhancing the
average weighted sum-AoI approach was suggested.
III. S YSTEM MODEL
A. System Model
As shown in Fig. 1, in a high-security-demand network
scenario, we consider a relay UA Vs assisted wireless com-
munication system, where a malicious eavesdropping UA V
(Eve) is present in the system. It is anticipated that there
is a signiﬁcant blockage between the relay UA Vs and the
source station (denoted as S). Relay UA Vs (denoted as mr)
are deployed to facilitate communication between the S and
ground users. To guarantee the security of communications
within the system, we select the mr that is nearest to the
eavesdropping UA V and repurpose it as a jamming UA V
(denoted as mj), which transmits jamming signals aimed at
the eavesdropper.
In the UA V-assisted wireless communication system we
studied, the presence of an eavesdropping UA V eavesdropping
on the transmission process of the relay UA V while the relay
UA V is transmitting private information poses a potential
threat to the wireless communication system. In order to
safeguard the security of the UA V wireless communication
system, the control center monitors the position of the eaves-
dropping drone through radar and other technologies and
gives a role switching command to the nearest relay drone,
ordering the relay drone to convert into a jamming drone,
which performs a follow-jamming task on the eavesdropping
drone, thus safeguarding the security of the UA V wireless
secure communication system.
LetM ={1, 2,..., M},N ={1, 2,..., N} indicate the legit-
imate UA Vs and ground users sets. Binary matrixes pmr[t] =
{pmr[t]}∈ ZN×1 and wmj[t] ={wmj[t]}∈ ZE×1 indicate
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

WEN et al.: JOINT TRAJECTORY AND POWER DESIGN WITH COOPERATIVE JAMMING UA V ASSISTANCE 1261
the mth UA V’s function within the designated time window,
which pmr[t]∈{ 0, 1}, wmj[t]∈{ 0, 1}. When pmr[t] = 1 ,
the mth UA V serve as a relay to facilitate communication
between the ground user and S, denoted by mthr . Similarly,
when wmj[t] = 1 , the mth UA V function as a jammer to
prevent malicious UA V from wiretapping, denoted bymthj . For
each user, there is at most one UA V to assist communication
at the tth time interval. Additionally, each UA V is limited
to serving a single ground user within a single time interval.
There are certain constraints that must be considered:
pmr,n[t]∈{ 0, 1}, (C1)
0≤
M∑
m=1
pmr,n[t]≤ 1, ∀n∈N , (C2)
0≤
N∑
n=1
pmr,n[t]≤ 1, ∀m∈M. (C3)
Likewise, a cooperative jamming UA V can prevent only a
single Eve during the tth time slot:
wmj,e[t]∈{ 0, 1}, (C4)
0≤
M∑
m=1
wmj,e[t]≤ 1, m ∈M. (C5)
It is important to note that, in an effort to facilitate the
solution of the problem, we only research a single ground
user nth in this paper. Correspondingly, we only need a set
of relay UA V and cooperative jammer UA V , denoted byma,
a∈{r,j}.
B. Movement Model
The limited ﬂight duration T0 of the UA Vs can be par-
titioned into T = T0/∆t time intervals, where ∆t must be
sufﬁciently small to ensure that the UA Vs’ position can be
considered stationary within each time slot. For the sake of
notational convenience, we deﬁneT ={0, 1,...,T} to denote
the set of time intervals.
For mathematical clarity, the three-dimensional (3D)
Cartesian coordinate system is adopted, where qma[t] =
[xma(t),yma(t)]T and qe[t] = [xe(t),ye(t)]T represents the
horizontal position of ma and Eve at the tth time interval,
respectively [47]. Consequently, the velocity and acceleration
ofma at the tth time interval can be represented as vma(t) =
˙qma(t) and ama(t) = ¨qma(t).
The velocity of a UA V is the rate of change of position
per unit of time, which indicates the speed and direction
of the UA V’s motion in three-dimensional space, and is
mathematically expressed as:
vma = dqma
dt
, (1)
where qma denotes the positional coordinates of qma.
The acceleration is the rate of change of speed per unit of
time and indicates how the speed of the UA V changes over
time. The mathematical expression is:
ama = dvma
dt
. (2)
Utilizing Taylor expansion, the relationships among the
UA V’s position, velocity, and acceleration can be expressed
as follows [48]:
qma[t + 1] = qma[t] + vma[t]∆t + 12 ama[t](∆t)2, (3)
vma[t + 1] = vma[t] + ama[t]∆t. (4)
Similarly, the velocity and acceleration of the Eve UA V at
the tth time interval can be denoted as ve(t) = ˙qe(t) and
ae(t) = ¨qe(t).
The maximum speed of the UA Vs is constrained by vmax,
which establishes that the maximum distance they can travel
in each time interval is given by dmax = vmax∆t. Because
UA Vs are required to return to a designated docking station for
energy refueling, their initial position qIma and ﬁnal position
qFma must be predetermined [49].
Typically, S and the ground users move at a pace signiﬁ-
cantly slower than that of the UA Vs, allowing their positions
to be treated as static, represented by qs = [xs,ys]T and
qn = [xn,yn]T , respectively. Particularly, we suppose that
both legitimate and malicious UA Vs can monitor each other’s
positions instantaneously through technologies like ground
radar or cameras [50].
To summarize, the kinematic constraints for UA Vs are
expressed as follows, with dmin indicating the minimum
safe distance between UA Vs to prevent collisions, and
‖·‖ representing the Euclidean distance.
qma[0] = qIma, (C6)
qma[T ] = qFma, (C7)
‖qma[t + 1]− qma[t]‖2≤ (dmax)2, (C8)
‖qma[t]− qma ′[t]‖2≥ (dmin)2,
∀ma,m′a∈M,ma⁄=m′a. (C9)
C. Communication Model
In the wireless communication process, channel state infor-
mation is mainly used to measure the quality of the wireless
channel, which is crucial for optimizing the performance of the
wireless communication system [51], [52], [53]. In this paper,
we investigate the cases where the channel state information
is fully known and incompletely known. In the case where the
channel state information is completely known, the channels of
legitimate and eavesdropping users are estimated by the guide
signal [54]. In the case where the channel state information
is not completely known and the eavesdropping channel is
assumed to satisfy the Rayleigh distribution property, the
channel state information of the legitimate user is obtained
through the guide signal, and the eavesdropping channel satis-
ﬁes the Rayleigh fading, which implies that the eavesdropping
user’s channel is randomly varying and obeys the Rayleigh
distribution [55]. In this case, the communication system
cannot accurately obtain the CSI of the eavesdropping user,
and we estimate it based on statistical information.
In the UA V-assisted wireless communication system that we
studied, the UA V ﬂies at high altitude to perform its mission
with fewer obstacles and weaker scattering effects, so the
line-of-sight link dominates. In the case of line of sight link
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

1262 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
dominance, the channel matrix of the multi-antenna system
can be approximated as a matrix of rank 1, and thus we
simplify the communication between the ground source point
and the UA V as a single antenna communication. In addition,
the single-antenna model simpliﬁes the channel modeling
and system analysis, which facilitates theoretical studies and
simulations.
We suppose that the legitimate UA Vma and the Eve UA V
operate at constant altitudes of Hma > 0 and He > 0,
correspondingly [56]. To achieve optimal communication
performance, legitimate UA Vs and the malicious UA V will
operate at the minimum permissible ﬂight altitude H > 0,
such that Hma = He = H. Consequently, the time-varying
coordinate of mth UA V and Eve UA V are represented as
[xma(t),yma(t),H ]T and [xe(t),ye(t),H ]T , respectively. The
corresponding horizontal positions are given by qm(t) =
[xma(t),yma(t)] and qe(t) = [xe(t),ye(t)]. Consequently, the
distances from S to the relay and jammer UA Vs, as well
as the distance between S and the Eve UA V , are deﬁned as
follows:
ds,mr[t] =
√
‖qmr[t]− qs‖2 +H 2, (5)
ds,mj[t] =
√
‖qmj[t]− qs‖2 +H 2, (6)
ds,e[t] =
√
‖qe[t]− qs‖2 +H 2. (7)
Similarly, during the tth time interval, the distances from
relay and jammer UA Vs to thenth ground user, as well as the
distances from relay and jammer UA Vs to the Eve UA V can
expressed as:
dmr,n[t] =
√
‖qmr[t]− qn‖2 +H 2, (8)
dmj,n[t] =
√
‖qmj[t]− qn‖2 +H 2, (9)
dmr,e[t] =
√
‖qmr[t]− qe[t]‖2, (10)
dmj,e[t] =
√
‖qmj[t]− qe[t]‖2, (11)
moreover, the distance from relay UA V to cooperative jam-
ming UA V can be represented as
dmr,mj[t] =
√
‖qmr[t]− qmj[t]‖2. (12)
In this paper, we employ the LoS communication model
for the UA V-to-GU and GU-to-UA V links. Consequently,
the channel power gain from S to both the relay and jam-
mer UA Vs, as well as to the Eve UA V , is derived from
the free space path loss model, which can be expressed
as:
hs,mr[t] =β0d−2s,mr[t] = β0‖qmr[t]− qs‖2 +H 2, ∀t, (13)
hs,mj[t] =β0d−2s,mj[t] = β0‖qmj[t]− qs‖2 +H 2, ∀t, (14)
hs,e[t] =β0d−2s,e[t] = β0‖qe[t]− qs‖2 +H 2, ∀t, (15)
where β0 indicates the channel power gain at a reference
distance of d0 = 1 meter. Likewise, the channel power gains
from ma to nth User can be represented as:
hmr,n[t] =β0d−2mr,n[t] = β0‖qmr[t]− qn‖2 +H 2, ∀t,
(16)
hmj,n[t] =β0d−2mj,n[t] = β0‖qmj[t]− qn‖2 +H 2, ∀t,
(17)
since thema and Eve UA V are in the same horizontal location,
the channel power gains can be formulated as:
hmr,e[t] =β0d−2mr,e[t] = β0‖qmr[t]− qe[t]‖2, ∀t, (18)
hmj,e[t] =β0d−2mj,e[t] = β0‖qmj[t]− qe[t]‖2, ∀t, (19)
hmr,mj[t] =β0d−2mr,e[t] = β0‖qmr[t]− qmj[t]‖2, ∀t. (20)
D. Role Switching of UA Vs and Energy Consumption
A UA Vma is able to perform one function at a time due to
the half-duplex process; by dynamic role transferring, it can
act as a jammer or a relay.
0≤
N∑
n=1
pma,n[t] +wma,e[t]≤ 1, ∀ma∈M,n∈N .
(C10)
To enhance the conﬁdentiality performance of the system,
we choose mr that is closest to the eavesdropping UA V and
convert it into a jamming UA V (denoted by mj) to broadcast
interference signals targeting the eavesdropper [57].
Given that the energy consumption of the UA V for com-
munication tasks, such as signal processing, is typically much
lower than that for propulsion, we will disregard it in this
research [58]. Consequently, the energy consumption of the
UA Vs comprises only propulsion energy and jamming energy.
As indicated in [59], the effective upper bound for the
propulsion energy consumption of a ﬁxed-wing ma UA V , with
velocity vma[t] and acceleration ama[t] at time slot t, can be
formulated as follows:
Epushma [t]
=
[
c1‖vma[t]‖3 + c2‖vma[t]‖(1 +‖ama‖2g2 )] + ∆k, (21)
where c1 and c1 are two constant parameters associated with
aerodynamics, and g denotes the gravitational acceleration.
Additionally, ∆k = 12G(‖vFm‖2−‖ vIm‖2) represents the
change in kinetic energy of the UA V , which depends solely
on the UA V’s mass G and its initial and ﬁnal speeds.
The jamming energy consumption of the mj UA V at time
slot t can be expressed as follows:
Ejammj [t] =wmj,e[t]pmj[t]. (22)
Consequently, the overall energy consumption of the ma
UA V can be formulated as
Etotalmr [t] =Epushmr [t], (23)
Etotalmj [t] =Epushmj [t] +Ejammj [t]. (24)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

WEN et al.: JOINT TRAJECTORY AND POWER DESIGN WITH COOPERATIVE JAMMING UA V ASSISTANCE 1263
IV. M ULTIAGENT OPTIMIZATION WITH PERFECT CSI
In this section, we assume the availability of channel state
information for hs,e, hmr,e, hmj,e is perfect. Therefore, we
explore the secrecy rate of a cooperative jamming UA V
assisted UA V-enabled system.
A. Problem Statement and F ormulation
The transmission power ps[t] of S and the transmission
power pmj[t] of ma are constrained by both their average
and peak values, resulting in the following limitations:
1
T
T∑
t=1
ps[t]≤P aves , (C11)
0≤ps[t]≤P maxs , ∀t. (C12)
1
T
T∑
t=1
pma[t]≤P aveUA V, (C13)
0≤pma[t]≤P maxUA V, ∀t. (C14)
At the tth time slot, the secrecy rates attainable from S to
mr and Eve UA V can be formulated as follows:
Rs,mr[t] = log2
(
1 + ps[t]hs,mr[t]σ2r +pmj[t]hmr,mj[t]), (25)
Rs,e[t] = log2
(
1 + ps[t]hs,e[t]σ2e +pmj[t]hmj,e[t]), (26)
where σ2r and σ2e are the white Gaussian noise power at the
mth UA V and Eve UA V . Similarly, the secrecy rates attainable
frommr tonth ground user and Eve UA V can be formulated
as follows:
Rmr,n[t] = log2
(
1 +ps[t]hs,mr[t]hmr,n[t]σ2n +pmj[t]hmj,n[t]), (27)
Rmr,e[t] = log2
(
1 +ps[t]hs,mr[t]hmr,e[t]σ2e +pmj[t]hmj,e[t]), (28)
where σ2n is the white Gaussian noise power at the ground
user.
Then, the secrecy throughput from S to mr during the tth
time interval can be formulated as follows:
Rsecs,mr[t] = [Rs,mr[t]−Rs,e[t]]+, (29)
where [x]+ = max(x, 0). The achievable transmission rate
from mr to nth ground user during the tth time interval can
be represented as follow:
Rsecmr,n[t] = [Rmr,n[t]−Rmr,e[t]]+. (30)
This paper focuses on the worst-case maximum secrecy rate
problem in system. To evaluate the worst security performance
from the ground user’s perspective, we suppose that the mj
approaches the ground user at the closest distance. We aim to
maximize the minimum secrecy rate by improving the ﬂight
paths and transmission power of both relay and the jamming
UA Vs. This issue can be mathematically formulated as:
P1 : max
qmr,qmj,pmr,pmj
Rsecmr,n
s.t. (C1)− (C14), (31)
where (C1)–(C5) and (C10) represent the guidelines for the
distinction of UA V role allocation, (C6)–(C9) denote the
kinetic constraints on the trajectories of UA V movements,
(C11)–(C14) establish the mean and maximal transmission
power limitations for both the S and UA Vs.
V. M ULTIAGENT OPTIMIZATION WITH IMPERFECT CSI
In this section, we consider the scenario in which the
source station, ground users, and ma Uncrewed Aerial Vehi-
cles (UA Vs) possess instantaneous channel state information
regarding authorized entities, speciﬁcally including hs,mr,
hmr,mj , hmr,n, and hmj,n. It is assumed that the instanta-
neous channel state information hs,e, hmr,e, and hmj,e for
legitimate links is imperfect. Furthermore, we assume that the
wiretap channels exhibit Rayleigh fading characteristics [60].
In particular, the channel from the S to Eve is modeled as
hs,e ∼ CN(0, 1), while the channels from mr and mj to
Eve are deﬁned as hmr,e∼CN (0, 1) and hmj,e∼CN (0, 1),
respectively.
A. Problem Statement and F ormulation
The source station broadcasts conﬁdential signals to ground
user using relay UA V . The signals received by both the ground
user and the eavesdropper can be represented as follows:
yn(l) = (hs,n +hs,mrhmr,n)pss(l) +hmj,npjj(l) +σ2n(l),
(32)
ye(l) = (hs,e +hs,mrhmr,e)pss(l) +hmj,epjj(l) +σ2e(l),
(33)
the terms (hs,n +hs,mrhmr,n) and (hs,e +hs,mrhmr,e) are
designated as the main channel and wiretap channel, respec-
tively; the variableshmj,n andhmj,e are identiﬁed as jamming
channels. Additionally, σ2n and σ2e represent the additive
white Gaussian noise (AWGN), characterized by distributions
CN (0,σ 2n) andCN (0,σ 2e), respectively. The term s(l) denotes
the conﬁdential signal, while j(l) signiﬁes the jamming signal.
The secrecy rate is a widely used metric for quantify-
ing security in physical layer communications, deﬁned as
follows [61]:
Cs = (Cn−Ce)+. (34)
In this context, Cn and Ce denote the secrecy capacity for
the ground user and the wiretap capacity for Eve, respectively,
deﬁned as follows:
Cn = log2
(
1 + pshs,mrhmr,n
σ2n +pmjhmj,n
)
, (35)
Ce = log2
(
1 + pshs,mrhmr,e
σ2e +pmjhmj,e
)
. (36)
However, given thaths,e,hmr,e, and hmj,e are unknown, it
becomes challenging to ascertain whether the instantaneous
secrecy rate is non-negative. In such cases, we typically
employ the secrecy outage probability as a criterion for
assessing the security performance of a system [62]. The
risk of a secrecy outage refers to the likelihood that the
desired physical layer security (PLS) coding rate Rs exceeds
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

1264 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
the secrecy rate Cs. The formulation of the secrecy outage
probability is provided as follows [63]:
Pout =P (Cs≤Rs|Transmission)
=P (Ce≥Cn−Rs). (37)
Clearly, the probability of a secrecy outage is conditional
and relies on the proper transmission of the main channels
[64]. As a result, the ground user can accurately decode the
transmitted codewords at a rate of up toCm. Assuming that the
S possesses complete knowledge of the instantaneous channel
state information (CSI) for hs,mr, hmr,mj , hmr,n, and hmj,n
within the coherence time, Alice is capable of utilizing a
variable rate of transmitted codewords up to Cn.
The secrecy outage probability concerning Rs, denoted as
Pout, can be expressed as follows:
Pout = 1−FZ(θ1), (38)
where θ1 = 2Cn−Rs− 1, with Cn deﬁned in Eq. (35) and
FZ(z) deﬁned in Eq. (39), shown at the bottom of the page.
The equation (39) represents the cumulative distribution
function of FZ(z) in the formula for the probability of
secrecy outage in a multi-objective optimization problem in the
scenario with incompletely known channel state information.
Supposing that the unknown CSI of wiretap channel follows a
complex Gaussian distribution, according to the knowledge of
probability theory, the mode of a variable obeying the complex
Gaussian distribution is described by the Rayleigh distribution.
Therefore, we can derive the formula for the cumulative
distribution function ofFZ(z) in the secrecy outage probability
in the multi-objective optimization problem, i.e., equation (39).
Equation (40), shown at the bottom of the page, represents
the probability distribution function of FZ(z) in the security
outage probability in the multi-objective optimization problem,
and equation (40) is derived by differentiating equation (39).
VI. M ULTIOBJECTIVE OPTIMIZATION ALGORITHM BASED
ON MULTIAGENT REINFORCEMENT LEARNING
A. Multiobjective Optimization Problem Based on Markov
Game
In this section, we construct a Markov game for multi-
objective optimization function. First, the trajectory and power
optimization problem is expressed by a ﬁve-tuple Markov
game as ={I,S,A,T,R}, in this context,I represents ﬁnite
set of agents,S denotes ﬁnite set of states, A indicates action
set,T is state transition probability, and R represents reward
function. Considering the overall performance of UA V-assisted
system, the UA V-assisted system is viewed as the environment,
and relay UA V , jammer UA V and Eve UA V are abstracted as
agents. The details are following:
Fig. 2. MAJDTP algorithm ﬂow chart.
1) State space: The state space for both the relay and
jammer UA Vs are deﬁned as sr(t) = {svr(t),
sqr(t), spr(t)}, sj(t) = {svj(t), sqj(t), spj(t)},
respectively. svi(t), sqi(t) and spk(t),i ∈ {m,j}
describe speed, position and transmission power of
UA Vs. We assume that mr as well as mj UA V and
Eve UA V can observe each other’s positions.
2) Action space: Regarding mr and mj UA Vs, the action
space ak(t) contains the speed vk(t) and the transmis-
sion powerpk(t). Meanwhile, the action spaceae(t) for
the Eve UA V consists of speed ve(t).
3) State Transition Probability: The likelihood of tran-
sition from state st to the next state st+1 at the time
slot t when action a is selected. For all st∈S ,at∈A ,
the following constraints are satisﬁed:
T (st+1|st,at)> 0, (41)∑
st+1∈S
T (st+1|st,at) = 1. (42)
4) Reward: In UA V-assisted system, the goal of the opti-
mization issue P1 is to maximize the worst secrecy rate.
The objective of training the agents is to maximize the
sustained cumulative reward. Thus, immediate reward
formula for agent at the time slot t can be expressed as:
rr(t) =Rmr,n[t], (43)
rj(t) =Rmr,n[t], (44)
re(t) =Rmr,e[t]. (45)
The Fig. 2 is MAJDTP algorithm ﬂow chart. First, the
algorithm initializes the actor and critic networks of each
FZ(z) =
∫ ∞
0
(∫ zx
0
y
pshs,rhr,n
exp
{
− y2
2 (pshs,rhr,n)
}
dy
) x
hj,nps
exp
{
− x2
2hj,nps
}
dx. (39)
fZ(z) =
∫ ∞
0
x xzhr,nps exp{− (xz)22hr,nps} xhj,nps exp{− x22hj,nps}dx. (40)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

WEN et al.: JOINT TRAJECTORY AND POWER DESIGN WITH COOPERATIVE JAMMING UA V ASSISTANCE 1265
agent, which are used for deciding actions and estimating
Q values, respectively. In addition, a target network is set up to
stabilize the training process and an experience replay buffer
is initialized to store historical experience. Subsequently, the
agents interact in the environment, where each agent generates
actions based on the current strategy and performs joint
actions with other agents to obtain new environment states
and corresponding rewards. These experience data are stored
in the experience buffer for subsequent training.
B. Trajectory and Jamming Power Optimization Algorithm
Based on MADDPG
We study the problem of maximizing the security rate of the
network by optimizing the ﬂight trajectories of the relay UA V
and the jamming UA V as well as the transmission power under
the condition that the channel state information is known, and
the problem of minimizing the probability of network security
outage by optimizing the ﬂight trajectories of the relay UA V
and the jamming UA V as well as the transmission power
under the condition that the channel state information is not
fully known. In the process of optimizing the ﬂight trajectory
and transmission power of relay UA Vs and jamming UA Vs,
we implement it by means of a multi-intelligent body deep
deterministic algorithm.
First, the algorithm initializes each agent’s strategy network
(actor) for action selection and value network (critic) for Q-
value estimation. To ensure training stability, a target network
is also established, along with an experience replay buffer to
store historical experiences. The agents then interact within
the environment, where each agent generates actions based
on its current strategy, collaborates through joint actions,
and receives updated environment states and corresponding
rewards. These experiences are stored in the replay buffer for
future training iterations.
During training, a random batch of data is sampled from
the experience buffer to compute the target Q-value, which
is derived from a weighted sum of the reward and discount
factors. The optimal next move is determined using the target
actor network. Next, the loss function of the critic network is
calculated using the mean squared error, and its parameters
are updated via gradient descent. The actor network is then
reﬁned using the policy gradient method to maximize the Q-
value by selecting optimal actions in given states. Additionally,
the target network undergoes a soft update, gradually aligning
with the current network to enhance training stability. This
process is iterated continuously, allowing agents to optimize
their strategies until convergence or the desired performance
level is achieved.
The core steps of MADDPG algorithm follow the
“centralized training, decentralized execution (CTDE)” frame-
work, enabling multiple agents to collaboratively optimize
their policies. During training, agents share observations and
rewards in a centralized manner, allowing for better coordi-
nation and global optimization. However, during execution,
each agent operates independently based only on its local
observations, ensuring adaptability and scalability in real-
world environments.
TABLE I
NEURAL NETWORK PARAMETERS
We introduce a multiagent reinforcement learning algorithm
derived from MADDPG to address the multiobjective opti-
mization issue P1. The MADDPG algorithm is an enhanced
version of the actor-critic and deep deterministic policy gra-
dient (DDPG) algorithms. It adopts a centralized training and
distributed execution operation. Each agent includes an actor
network µi(sit), a critic network Qi(st,at), an actor target
networkµ′i(sit+1), and a critic target network Q′i(st+1,aa+1).
For the MADDPG algorithm, the actor network can operate
with only local information, the critic network is improved
using global information, and each agent to make decisions
will consider the inﬂuence of other agents.
We determine πi as the MAJDTP algorithm’s policy for
agent i. By modifying the evaluation network’s parameters θµi
and θQi , the optimum policy can be achieved. The evaluation
network parametersθµi andθQi are modiﬁed in continuous time
during this operation. To be particular, the operation experi-
ence (st,at,rt,st+1) is retained in the experience replay buffer
D after being acquired via the agent-environment interaction.
The evaluation network’s parameters are updated during train-
ing by extracting mini-batch samples ϵ over the experience
replay bufferD. Through loss function minimization, the critic
network modiﬁes the evaluation network parameters θQi . The
loss function’s formula can be represented as follows:
L(θQi ) = E[(Qi(st,ait,a−it |θQi )− yit)2], (46)
yit =rit +γQ ′i(st+1,ait+1,a−it+1|θQi ), (47)
where Q′i(·) represents the target network’s state-action value
function. The policy objective function is maximized in order
to modify the network parametersθµi for an actor network. The
expression for the policy objective function can be represented
as follows:
J (θµi ) = E[(Qi(sit,ai|ai) =µi(sit))], (48)
where µi(·) is the actor evaluation network function that
reﬂects actions regarding the deterministic policy πi. Rather
than transferring the parametersµ′i andQ′i straight to the target
network, we adjust them gradually as the evaluation network
parameters θµi and θQi are modiﬁed, as following:
θµ′i =λxθµi + (1−λx)θµ′i , (49)
θQ′i =λzθQi + (1−λz)θQ′i , (50)
where λx≪ 1, λz≪ 1.
The above training procedure based MADDPG to solve
MAJDTP is shown in Algorithm 1. The training parameters
about MAJDTP algorithm in Trajectory and Jamming Power
Optimization Algorithm Based on MADDPG section as shown
in Table I.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

1266 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE II
SIMULATION PARAMETERS
Algorithm 1 MAJDTP Algorithm
1: Initialize the actor network and critic network evaluation
parameters as θµi and θQi .
2: Initialize the experience replay buffer D, with mini-batch
samples ϵ, ϵ ≪ D. Initialize the maximum number of
training epochsE, the maximum number of training steps
M, the action noise H.
3: for epochs = 1 to E do
4: Initialize a random state process sit.
5: for step t = 1 to M do
6: Each agent selects actions ait =µi(sit) +Ht based on the
current policy
7: Execute action ait and receive the corresponding reward
rit
8: sit←sit+1
9: Store state process,the next state process, action process,
and the corresponding reward (sit,ait,rit,sit+1) in the expe-
rience replay buffer D
10: for each agent do
11: Randomly sample a mini-batch ε (sit,ait,rit,sit+1) from
the experience replay buffer D
12: Set yit =rit +γQ ′i(st+1,ait+1,a−it+1|θQi )
13: Update the critic network by minimizing the loss function
L(θQi ) = E[(Qi(st,ait,a−it |θQi )− yit)2]
14: Update the actor network by maximizing the policy objec-
tive functionJ (θµi ) = E[(Qi(sit,ai|ai) =µi(sit))]
15: end for
16: Update target network parameters for each agent i: θµ′i =
λaθµi + (1−λa)θµ′i ,θQ′i =λcθQi + (1−λc)θQ′i .
17: end for
18: end for
VII. S IMULATION RESULTS
In this section, we present experimental results to val-
idate the effectiveness of our proposed MADDPG-based
UA V trajectory and interference power optimization algorithm.
We investigate the impact of the maximum relay UA V transmit
power PmR on the network security rate, security outage
probability, and the energy consumption performance of both
relay and jamming UA Vs under different iteration conditions.
Furthermore, by comparing our proposed MAJDTP algorithm
with the reference DDPG algorithm, we demonstrate that
our method outperforms in terms of security performance,
energy consumption, and convergence speed. All simulation
Fig. 3. UA V’s trajectory with different iteration.
experiments were conducted using MATLAB (version 2022a)
with a reliable pseudo-random number generator (PRNG)
to emulate the actual channel environment. We utilize the
MATLAB Reinforcement Learning Toolbox to design the
reinforcement learning environment for UA V trajectory and
interference power optimization. In the trajectory and jam-
ming power optimization algorithm, network parameters were
represented as mathematical variables, transforming the sim-
ulation into a mathematical problem. Numerical simulations
were then performed using MATLAB to verify the network’s
performance. The more simulation parameters are listed
in Table II.
Fig. 3 illustrates the trajectory routes of relay UA V and
cooperative jamming UA V in each iteration under the scenario
that eavesdropping UA V approach ground users with the
shortest route to eavesdrop. Fig. 3 shows that during the
signal transmission to the ground user, the relay UA V will
ﬁrst depart from the ground user because of presence of the
eavesdropping UA V , and then move closer to the ground user
because of signal transmission. After the end of the informa-
tion transmission process, the relay UA V will move away from
the ground user and then return to the set termination point.
In the process of transmitting jamming signals, the jamming
UA V ﬁrst ﬂies in the direction of the ground user to interfere
with the eavesdropping UA V . When the distance is relatively
close, to lessen interference with the ground user signal, it will
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

WEN et al.: JOINT TRAJECTORY AND POWER DESIGN WITH COOPERATIVE JAMMING UA V ASSISTANCE 1267
Fig. 4. Secrecy rate performance versus P mR achieved by differen iteration.
Fig. 5. Secrecy outage performance versus P mR achieved by differen iteration.
stay away from the ground user and then ﬂy back to the set
termination point.
Fig. 4 demonstrates security performance of the putted
forward scheme which selects a cooperative UA V as relay,
in terms of secrecy rate compared to the maximal transport
power PmR across different iteration. First, we observe that
as the relay UA V’s maximal transmission power increases,
the secrecy rate tends to rise. This is because a higher trans-
mission power enhances the signal strength, which improves
the reception quality for the ground user, ultimately increas-
ing the secrecy rate. Additionally, with the increase of the
number of iterations of reinforcement learning algorithm, the
secrecy rate also shows a rising trend, because with the
continuous training of data, the obtained solution is getting
better and better. As shown in Fig. 4, the improvement
in security performance is more pronounced in the initial
iteration, while the gains from subsequent iterations gradually
diminish.
The Fig. 5 illustrates the relationship between the secrecy
outage probability and the maximum transmission power PmR
of relay UA V at different iterations of deep reinforcement
learning. Firstly, it is evident from the Fig. 5 that as the
Fig. 6. Cumulative moving distance with differen iteration.
maximum transmission powerPmR of the relay UA V increases,
the secrecy outage probability shows a decreasing trend. This
occurs because higher transmission power leads to stronger
signal strength at ground user, enabling more reliable signal
transmission and reducing the secrecy outage probability. Sec-
ondly, at a constant maximum transmission power PmR of the
relay UA V , the secrecy outage probability also decreases as the
number of iterations increases. This is attributed to the further
optimization of the ﬂight trajectories of both the relay UA V
and cooperative jamming UA V with more iterations of deep
reinforcement learning, which lowers the system’s secrecy
outage probability and enhances its safety performance.
The Fig. 6 shows the statistical results of cumulative moving
distance (CMD) of relay UA V and cooperative jamming UA V
under different iterations. As shown in Fig. 6, the cumulative
moving distance of the relay UA V and cooperative jamming
UA V gradually decreases as the number of iterations rises.
This implies that, with more iterations, the cumulative distance
traveled by both UA Vs becomes shorter, allowing them to get
closer to the ground user while transmitting the relay and
jamming signals. Reducing the cumulative travel distance of
relay UA V and cooperative jamming UA V can improve energy
effectiveness of UA Vs.
The energy usage of relay and cooperative jamming UA Vs
with different iteration under perfect channel state information
is assessed in Fig. 7. It is noticeable that with an increasing
number of iterations, energy consumption of relay UA V and
cooperative jamming UA V is in a downward trend. This is
because with the iterative training of data by reinforcement
learning algorithm, the ﬂight trajectory of relay UA V and
cooperative jamming UA V is moving closer and closer to the
ground user, thus reducing the cumulative moving distance of
relay UA V and cooperative jamming UA V , and thus reducing
the energy consumption during ﬂight. In addition, cooperative
jamming UA V is required to transmit interference signals to
eavesdropping UA V . Thus, the energy usage of the cooperative
jamming UA V is considerably higher than relay UA V .
The Fig. 8 illustrates the energy consumption simulation
of relay UA V and cooperative jamming UA V under imper-
fect channel state information across different iterations of
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

1268 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Energy consumption of relay UA V and cooperative jamming UA V
with different iteration under perfect CSI.
Fig. 8. Energy consumption of relay UA V and cooperative jamming UA V
with different iteration under imperfect CSI.
reinforcement learning. Firstly, we observe that as the number
of reinforcement learning iterations increases, the energy con-
sumption of both relay UA V and cooperative jamming UA V
shows a downward trend. This is attributed to the further
optimization of ﬂight trajectories and transmission power for
both types of drones with the increase in iterations, leading to
reduced transmission power and consequently lower energy
consumption. Secondly, it is evident that compared to the
scenario with perfect channel state information, the energy
consumption of relay UA V and cooperative jamming UA V
is higher. This is because perfect channel state information
enables better adjustment of the ﬂight trajectories and trans-
mission power for both types of drones, thereby reducing
energy consumption.
Fig. 9 demonstrates describes the variation curve of jam-
ming power of cooperative jamming UA V in the process
of jamming eavesdropping UA V under different iterations.
As illustrated in Fig. 9, during jamming operation of the
cooperative jamming UA V , the jamming power ﬁrst presents an
upward trend, then gradually decreases to the minimum value,
Fig. 9. Cooperative jammer power versus T with different iteration.
Fig. 10. Achievable secrecy rate and mean convergence episodes for com-
parison between MAJDTP and DDPG.
then continues to increase, and ﬁnally decreases to the initial
value. This is because in the process of transmitting jamming
signals, at the beginning, the UA V is closer and closer to the
ground user, to minimize interference to the ground user, the
interference power is reduced, and then the interference power
is increased when it is far away from the ground user. In
addition, as the growing number of iterations, the ﬂight path
of collaborative jamming UA V is continuously reﬁned, and
the distance from ground user is getting closer and closer,
therefore the jamming power correspondingly decreases.
The Fig. 10 demonstrates the outstanding performance of
the algorithm we putted forward. In Fig. 10, we provide a
comparison of the mean secrecy and convergence rate for our
proposed MAJDTP algorithm versus the deep deterministic
policy gradient (DDPG) algorithm, which has a learning rate
of 0.001 and a γ value of 0.95. DDPG is a form of deep
reinforcement learning (DRL) algorithm that operates within
the actor-critic framework, where the agent trained with DDPG
exclusively gathers its own observations during training. The
simulation results indicate that our proposed MAJDTP algo-
rithm demonstrates superior security performance and faster
convergence speed than benchmark algorithm.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

WEN et al.: JOINT TRAJECTORY AND POWER DESIGN WITH COOPERATIVE JAMMING UA V ASSISTANCE 1269
Fig. 11. Total energy consumption for algorithms MAJDTP and DDPG under
different iteration scenarios.
The Fig. 11 illustrates the total energy consumption
performance of the MAJATP algorithm and the DDPG algo-
rithm under varying iteration scenarios. Firstly, it can be
observed that the total energy consumption for both algo-
rithms decreases as the number of iterations increases. This
trend can be attributed to the progressive optimization of
the trajectories and transmit power of the relay UA Vs and
the cooperative jamming UA Vs, resulting in reduced overall
energy consumption. Secondly, we can observe that the total
energy consumption of algorithms MAJDTP is consistently
lower than that of algorithm DDPG across different iterations,
indicating its superior energy-saving performance. This can
be attributed to the fact that algorithm MAJDTP optimizes
the trajectory and power of multiple intelligences, resulting in
a better design of both the trajectory and power compared to
algorithm DDPG, which ultimately reduces the system’s total
energy consumption.
VIII. C ONCLUSION
In this paper, we investigate the issue of secure wireless
communication in system with an eavesdropping UA V present.
From the perspective of ground users, we examine the problem
of maximizing the worst-case secrecy rate, assuming that
the eavesdropping UA V approaches the ground users at the
shortest distance. Moreover, we investigated the performance
of the system’s secrecy outage probability under imperfect
channel state information. We enhance the system’s security
performance by optimizing the ﬂight trajectories and trans-
mission power of the relay UA V and the cooperative jamming
UA V . Due to the ﬂexibility and complexity of UA V ﬂight paths,
we employ the MAJDTP algorithm to design and train the
ﬂight trajectories and transmission energy of the relay and
cooperative jamming UA Vs, thereby addressing the issue of
secure wireless communication in the system. The simulation
results demonstrate that our proposed algorithm achieves better
performance compared to the reference algorithm.
REFERENCES
[1] H.-M. Wang, X. Zhang, and J.-C. Jiang, “UA V-involved wire-
less physical-layer secure communications: Overview and research
directions,” IEEE Wireless Commun. , vol. 26, no. 5, pp. 32–39, Oct.
2019.
[2] N. Wang, P. Wang, A. Alipour-Fanid, L. Jiao, and K. Zeng, “Physical-
layer security of 5G wireless networks for IoT: Challenges and
opportunities,” IEEE Internet Things J. , vol. 6, no. 5, pp. 8169–8181,
Oct. 2019.
[3] M. Mozaffari, W. Saad, M. Bennis, Y .-H. Nam, and M. Debbah,
“A tutorial on UA Vs for wireless networks: Applications, challenges,
and open problems,” IEEE Commun. Surveys Tuts. , vol. 21, no. 3,
pp. 2334–2360, 3rd Quart., 2019.
[4] Y . Zeng, J. Xu, and R. Zhang, “Energy minimization for wireless
communication with rotary-wing UA V ,”IEEE Trans. Wireless Commun.,
vol. 18, no. 4, pp. 2329–2345, Apr. 2019.
[5] S. Yan, S. V . Hanly, and I. B. Collings, “Optimal transmit power and
ﬂying location for UA V covert wireless communications,” IEEE J. Sel.
Areas Commun., vol. 39, no. 11, pp. 3321–3333, Nov. 2021.
[6] D.-H. Tran, V .-D. Nguyen, S. Chatzinotas, T. X. Vu, and B. Otter-
sten, “UA V relay-assisted emergency communications in IoT networks:
Resource allocation and trajectory optimization,” IEEE Trans. Wireless
Commun., vol. 21, no. 3, pp. 1621–1637, Mar. 2022.
[7] H. Wu, M. Li, Q. Gao, Z. Wei, N. Zhang, and X. Tao, “Eavesdropping
and anti-eavesdropping game in UA V wiretap system: A differential
game approach,” IEEE Trans. Wireless Commun. , vol. 21, no. 11,
pp. 9906–9920, Nov. 2022.
[8] M. K. Hasan et al., “Lightweight encryption technique to enhance
medical image security on Internet of Medical Things applications,”
IEEE Access , vol. 9, pp. 47731–47742, 2021.
[9] H.-M. Wang, M. Luo, Q. Yin, and X.-G. Xia, “Hybrid cooperative
beamforming and jamming for physical-layer security of two-way
relay networks,” IEEE Trans. Inf. F orensics Security , vol. 8, no. 12,
pp. 2007–2020, Dec. 2013.
[10] G. Zhang, Q. Wu, M. Cui, and R. Zhang, “Securing UA V communi-
cations via joint trajectory and power control,” IEEE Trans. Wireless
Commun., vol. 18, no. 2, pp. 1376–1389, Feb. 2019.
[11] A. Li, Q. Wu, and R. Zhang, “UA V-enabled cooperative jamming for
improving secrecy of ground wiretap channel,” IEEE Wireless Commun.
Lett., vol. 8, no. 1, pp. 181–184, Feb. 2019.
[12] W. Wang et al., “Energy-constrained UA V-assisted secure communica-
tions with position optimization and cooperative jamming,” IEEE Trans.
Commun., vol. 68, no. 7, pp. 4476–4489, Jul. 2020.
[13] R. Zhang, X. Chen, M. Liu, N. Zhao, X. Wang, and A. Nallanathan,
“UA V relay assisted cooperative jamming for covert communica-
tions over Rician fading,” IEEE Trans. V eh. Technol. , vol. 71, no. 7,
pp. 7936–7941, Jul. 2022.
[14] Y . Wen, Y . Huo, L. Ma, T. Jing, and Q. Gao, “A scheme for trustworthy
friendly jammer selection in cooperative cognitive radio networks,”
IEEE Trans. V eh. Technol., vol. 68, no. 4, pp. 3500–3512, Apr. 2019.
[15] Z. Xiang, W. Yang, G. Pan, Y . Cai, and Y . Song, “Physical layer security
in cognitive radio inspired NOMA network,” IEEE J. Sel. Topics Signal
Process., vol. 13, no. 3, pp. 700–714, Jun. 2019.
[16] Y . Wen et al., “A covert jamming scheme against an intelligent eaves-
dropper in cooperative cognitive radio networks,” IEEE Trans. V eh.
Technol., vol. 72, no. 10, pp. 13243–13254, May 2023.
[17] Y . Zhang, Z. Mou, F. Gao, J. Jiang, R. Ding, and Z. Han, “UA V-enabled
secure communications by multi-agent deep reinforcement learning,”
IEEE Trans. V eh. Technol., vol. 69, no. 10, pp. 11599–11611, Oct. 2020.
[18] X. Zhou, Q. Wu, S. Yan, F. Shu, and J. Li, “UA V-enabled secure
communications: Joint trajectory and transmit power optimization,”
IEEE Trans. V eh. Technol., vol. 68, no. 4, pp. 4069–4073, Apr. 2019.
[19] C. Wen, Y . Fang, and L. Qiu, “Securing UA V communication based on
multi-agent deep reinforcement learning in the presence of smart UA V
eavesdropper,” in Proc. IEEE Wireless Commun. Netw. Conf. (WCNC) ,
Apr. 2022, pp. 1164–1169.
[20] Y . Zhou et al., “Secure communications for UA V-enabled mobile
edge computing systems,” IEEE Trans. Commun. , vol. 68, no. 1,
pp. 376–388, Jan. 2020.
[21] H.-M. Wang, M. Luo, X.-G. Xia, and Q. Yin, “Joint cooperative
beamforming and jamming to secure AF relay systems with individual
power constraint and no Eavesdropper’s CSI,” IEEE Signal Process.
Lett., vol. 20, no. 1, pp. 39–42, Jan. 2013.
[22] C. Wang, H.-M. Wang, and X.-G. Xia, “Hybrid opportunistic relaying
and jamming with power allocation for secure cooperative networks,”
IEEE Trans. Wireless Commun., vol. 14, no. 2, pp. 589–605, Feb. 2015.
[23] A. Fotouhi et al., “Survey on UA V cellular communications: Prac-
tical aspects, standardization advancements, regulation, and secu-
rity challenges,” IEEE Commun. Surveys Tuts. , vol. 21, no. 4,
pp. 3417–3442, 4th Quart., 2019.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

1270 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[24] N. Cheng et al., “AI for UA V-assisted IoT applications: A comprehensive
review,” IEEE Internet Things J. , vol. 10, no. 16, pp. 14438–14461,
May 2023.
[25] X. Liu, Y . Liu, and Y . Chen, “Machine learning empowered trajectory
and passive beamforming design in UA V-RIS wireless networks,” IEEE
J. Sel. Areas Commun. , vol. 39, no. 7, pp. 2042–2055, Jul. 2021.
[26] M. Shao, J. Yan, and X. Zhao, “Secrecy rate maximization by coopera-
tive jamming for UA V-enabled relay system with mobile nodes,” IEEE
Internet Things J. , vol. 10, no. 15, pp. 13168–13180, Mar. 2023.
[27] K. Heo, W. Lee, and K. Lee, “UA V-assisted wireless-powered secure
communications: Integration of optimization and deep learning,” IEEE
Trans. Wireless Commun. , vol. 23, no. 9, pp. 10530–10545, Sep. 2024.
[28] A. S. Abdalla and V . Marojevic, “Multiagent learning for secure wireless
access from UA Vs with limited energy resources,”IEEE Internet Things
J., vol. 10, no. 24, pp. 22356–22370, Dec. 2023.
[29] A. Gao, Q. Wang, Y . Hu, W. Liang, and J. Zhang, “Dynamic role
switching scheme with joint trajectory and power control for multi-UA V
cooperative secure communication,” IEEE Trans. Wireless Commun. ,
vol. 23, no. 2, pp. 1260–1275, Jun. 2023.
[30] X. Jiang et al., “Covert communication in UA V-assisted air-ground
networks,” IEEE Wireless Commun. , vol. 28, no. 4, pp. 190–197, Aug.
2021.
[31] W. Tian, X. Ding, G. Liu, Y . Dai, and Z. Han, “A UA V-assisted
secure communication system by jointly optimizing transmit power and
trajectory in the Internet of Things,” IEEE Trans. Green Commun. Netw.,
vol. 7, no. 4, pp. 2025–2037, Jan. 2023.
[32] Y . Liu et al., “Secure rate maximization for ISAC-UA V assisted com-
munication amidst multiple eavesdroppers,” IEEE Trans. V eh. Technol.,
vol. 73, no. 10, pp. 15843–15847, Oct. 2024.
[33] A. Chorti et al., “Context-aware security for 6G wireless: The role of
physical layer security,” IEEE Commun. Standards Mag. , vol. 6, no. 1,
pp. 102–108, Mar. 2022.
[34] N. Xie, Z. Li, and H. Tan, “A survey of physical-layer authentication in
wireless communications,” IEEE Commun. Surveys Tuts. , vol. 23, no. 1,
pp. 282–310, 1st Quart., 2020.
[35] Y . Wen et al., “Covert communications aided by cooperative jamming in
overlay cognitive radio networks,” IEEE Trans. Mobile Comput., vol. 23,
no. 12, pp. 12878–12891, Dec. 2024.
[36] Y . Wen, T. Jing, and Q. Gao, “Trustworthy jammer selection with truth-
telling for wireless cooperative systems,” Wireless Commun. Mobile
Comput., vol. 2021, no. 1, Jan. 2021, Art. no. 6626355.
[37] D. Xu and H. Zhu, “Jamming-assisted legitimate eavesdropping and
secure communication in multicarrier interference networks,” IEEE Syst.
J., vol. 16, no. 1, pp. 954–965, Mar. 2022.
[38] T.-X. Zheng, Z. Yang, C. Wang, Z. Li, J. Yuan, and X. Guan, “Wireless
covert communications aided by distributed cooperative jamming over
slow fading channels,” IEEE Trans. Wireless Commun. , vol. 20, no. 11,
pp. 7026–7039, Nov. 2021.
[39] C. Gao, B. Yang, D. Zheng, X. Jiang, and T. Taleb, “Cooperative
jamming and relay selection for covert communications in wireless relay
systems,” IEEE Trans. Commun. , vol. 72, no. 2, pp. 1020–1032, Feb.
2024.
[40] D. Guo, H. Ding, L. Tang, X. Zhang, L. Yang, and Y .-C. Liang, “A
proactive eavesdropping game in MIMO systems based on multiagent
deep reinforcement learning,” IEEE Trans. Wireless Commun. , vol. 21,
no. 11, pp. 8889–8904, Nov. 2022.
[41] H. Yang, Z. Xiong, J. Zhao, D. Niyato, L. Xiao, and Q. Wu, “Deep
reinforcement learning-based intelligent reﬂecting surface for secure
wireless communications,” IEEE Trans. Wireless Commun. , vol. 20,
no. 1, pp. 375–388, Jan. 2021.
[42] H. Yang et al., “Intelligent reﬂecting surface assisted anti-jamming
communications: A fast reinforcement learning approach,” IEEE Trans.
Wireless Commun., vol. 20, no. 3, pp. 1963–1974, Mar. 2021.
[43] Z. Ni and S. Paul, “A multistage game in smart grid security: A
reinforcement learning solution,” IEEE Trans. Neural Netw. Learn. Syst.,
vol. 30, no. 9, pp. 2684–2695, Sep. 2019.
[44] Y . Li, R. Zhang, J. Zhang, and L. Yang, “Cooperative jamming via
spectrum sharing for secure UA V communications,” IEEE Wireless
Commun. Lett. , vol. 9, no. 3, pp. 326–330, Mar. 2020.
[45] H. Dang-Ngoc et al., “Secure swarm UA V-assisted communications with
cooperative friendly jamming,” IEEE Internet Things J. , vol. 9, no. 24,
pp. 25596–25611, Dec. 2022.
[46] R. Ye, Y . Peng, F. Al-Hazemi, and R. Boutaba, “A robust cooperative
jamming scheme for secure UA V communication via intelligent reﬂect-
ing surface,” IEEE Trans. Commun., vol. 72, no. 2, pp. 1005–1019, Feb.
2024.
[47] P. Luong, F. Gagnon, L.-N. Tran, and F. Labeau, “Deep reinforce-
ment learning-based resource allocation in cooperative UA V-assisted
wireless networks,” IEEE Trans. Wireless Commun. , vol. 20, no. 11,
pp. 7610–7625, Nov. 2021.
[48] A. Prosperetti, Advanced Mathematics for Applications . Cambridge,
U.K.: Cambridge Univ. Press, 2011.
[49] L. Zhang et al., “A survey on 5G millimeter wave communi-
cations for UA V-assisted wireless networks,” IEEE Access , vol. 7,
pp. 117460–117504, 2019.
[50] X. Gu and G. Zhang, “A survey on UA V-assisted wireless communica-
tions: Recent advances and future trends,” Comput. Commun., vol. 208,
pp. 44–78, Aug. 2023.
[51] H. Du, Y . Deng, J. Xue, D. Meng, Q. Zhao, and Z. Xu, “Robust
online CSI estimation in a complex environment,” IEEE Trans. Wireless
Commun., vol. 21, no. 10, pp. 8322–8336, Oct. 2022.
[52] L. Wei, C. Huang, G. C. Alexandropoulos, C. Yuen, Z. Zhang,
and M. Debbah, “Channel estimation for RIS-empowered multi-user
MISO wireless communications,” IEEE Trans. Commun., vol. 69, no. 6,
pp. 4144–4157, Jun. 2021.
[53] B. Zheng, C. You, W. Mei, and R. Zhang, “A survey on channel estima-
tion and practical passive beamforming design for intelligent reﬂecting
surface aided wireless communications,” IEEE Commun. Surveys Tuts. ,
vol. 24, no. 2, pp. 1035–1071, 2nd Quart., 2022.
[54] Y . Liu, J. Zhao, M. Li, and Q. Wu, “Intelligent reﬂecting surface
aided MISO uplink communication network: Feasibility and power
minimization for perfect and imperfect CSI,” IEEE Trans. Commun. ,
vol. 69, no. 3, pp. 1975–1989, Mar. 2021.
[55] J. Guo, C.-K. Wen, S. Jin, and G. Y . Li, “Overview of deep learning-
based CSI feedback in massive MIMO systems,” IEEE Trans. Commun.,
vol. 70, no. 12, pp. 8017–8045, Dec. 2022.
[56] H. Li, J. Li, M. Liu, and F. Gong, “UA V-assisted secure communication
for coordinated satellite-terrestrial networks,” IEEE Commun. Lett. ,
vol. 27, no. 7, pp. 1709–1713, Jul. 2023.
[57] H.-M. Wang, Y . Zhang, X. Zhang, and Z. Li, “Secrecy and covert
communications against UA V surveillance via multi-hop networks,”
IEEE Trans. Commun. , vol. 68, no. 1, pp. 389–401, Jan. 2020.
[58] Y . Wen, Y . Huo, T. Jing, and Q. Gao, “A reputation framework with
multiple-threshold energy detection in wireless cooperative systems,” in
Proc. IEEE Int. Conf. Commun. (ICC) , Jun. 2020, pp. 1–6.
[59] L. Xiao, Y . Xu, D. Yang, and Y . Zeng, “Secrecy energy efﬁciency
maximization for UA V-enabled mobile relaying,” IEEE Trans. Green
Commun. Netw., vol. 4, no. 1, pp. 180–193, Mar. 2020.
[60] V . K. Rohatgi and A. M. E. Saleh, An Introduction to Probability and
Statistics. Hoboken, NJ, USA: Wiley, 2015.
[61] F. Jameel, S. Wyne, G. Kaddoum, and T. Q. Duong, “A comprehensive
survey on cooperative relaying and jamming strategies for physical layer
security,” IEEE Commun. Surveys Tuts. , vol. 21, no. 3, pp. 2734–2771,
3rd Quart., 2019.
[62] B. Li, Y . Zou, J. Zhou, F. Wang, W. Cao, and Y .-D. Yao, “Secrecy
outage probability analysis of friendly jammer selection aided multiuser
scheduling for wireless networks,” IEEE Trans. Commun. , vol. 67,
no. 5, pp. 3482–3495, May 2019.
[63] Y . Liu, Z. Su, C. Zhang, and H.-H. Chen, “Minimization of secrecy out-
age probability in reconﬁgurable intelligent surface-assisted MIMOME
system,” IEEE Trans. Wireless Commun., vol. 22, no. 2, pp. 1374–1387,
Feb. 2023.
[64] J. Zheng and Q. Zhang, “Secrecy outage probability of multiple-
input–multiple-output secure Internet of Things communication
systems,” IEEE Internet Things J. , vol. 11, no. 6, pp. 9843–9853, Mar.
2023.
Yingkun Wen (Member, IEEE) received the B.S.
degree from North China Electric Power Uni-
versity, Baoding, China, in 2015, and the Ph.D.
degree from Beijing Jiaotong University, Beijing,
China, in 2021. He is currently an Instructor with
the School of Computer Science and Engineering,
Xi’an University of Technology, Xi’an, China. His
research interests include physical layer security,
covert communication, cognitive radio networks, and
cooperative communication.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

WEN et al.: JOINT TRAJECTORY AND POWER DESIGN WITH COOPERATIVE JAMMING UA V ASSISTANCE 1271
Fengshuan Wang received the B.E. degree from
Henan Polytechnic University, Jiaozuo, China, in
2019. He is currently pursuing the M.E. degree
with the School of Computer Science and Engineer-
ing, Xi’an University of Technology, Xi’an, China.
His current research interests include physical layer
security, symbiotic radio networks, uncrewed aerial
vehicle (UA V) aided networks, and cooperative com-
munication.
Hui-Ming Wang (Senior Member, IEEE) received
the B.S. and Ph.D. degrees in electrical engineering
from Xi’an Jiaotong University, Xi’an, China, in
2004 and 2010, respectively. From 2007 to 2008 and
from 2009 to 2010, he was a Visiting Scholar with
the Department of Electrical and Computer Engi-
neering, University of Delaware, Newark, DE, USA.
Since 2015, he has been a Full Professor with Xi’an
Jiaotong University. He has co-authored the book
Physical Layer Security in Random Cellular Net-
works (Springer, 2016) and authored or co-authored
more than 180 IEEE journals and conference papers. His research interests
include 6G communications and networks, intelligent communications, wire-
less physical-layer security, and covert communications. He received the IEEE
ComSoc Asia–Paciﬁc Best Young Researcher Award in 2018 and the National
Excellent Doctoral Dissertation Award in China in 2012. From 2017 to 2022,
he was an Associate Editor of IEEE T RANSACTIONS ON COMMUNICATIONS .
He was the Clarivate Highly Cited Researcher in 2019 and the Elsevier Highly
Cited Researcher from 2020 to 2024.
Junhuai Li (Senior Member, IEEE) received the
B.S. degree in electrical automation from Shaanxi
Institute of Mechanical Engineering, Xi’an, China,
in 1992, the M.S. degree in computer application
technology from Xi’an University of Technology,
Xi’an, in 1999, and the Ph.D. degree in computer
software and theory from Northwest University,
Xi’an, in 2002. He is currently a Professor with
the School of Computer Science and Engineering,
Xi’an University of Technology. His research inter-
ests include the Internet of Things technology and
network computing.
Jin Qian received the Ph.D. degree in communica-
tion and information system from Beijing Jiaotong
University, Beijing, China, in 2017. He is currently a
Lecturer with the College of Information Engineer-
ing, Taizhou University. His major research interests
include wireless communication theory, vehicular ad
hoc networks, physical layer security, and network
security.
Kan Wang (Senior Member, IEEE) received the
Ph.D. degree in military communications from the
State Key Laboratory of Integrated Services Net-
works, Xidian University, Xi’an, China, in 2016.
Since March 2017, he has been with the School
of Computer Science and Engineering, Xi’an Uni-
versity of Technology, Xi’an. His current research
interests include wireless resource allocation, net-
work slicing, convex optimization, and machine
learning.
Huaijun Wang received the B.Sc. and M.Sc.
degrees in computer science from Xi’an University
of Technology in 2005 and 2010, respectively, and
the Ph.D. degree in computer software and theory
from the Northwest University of China, Xi’an, in
2014. He is currently an Associate Professor with
the School of Computer Science and Engineering,
Xi’an University of Technology. His research inter-
ests include the Internet of Things technology and
edge computing.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:04:52 UTC from IEEE Xplore.  Restrictions apply.
