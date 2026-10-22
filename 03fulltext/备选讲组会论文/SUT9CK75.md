---
type: literature-fulltext
title: "DDRL: A Dual-Phase Deep Reinforcement Learning Approach for UAV-Assisted Content Delivery Across Multiple Base Stations"
zotero_key: "SUT9CK75"
pdf_key: "YCJEXIJ9"
doi: "10.1109/TWC.2026.3677068"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/DDRL- A Dual-Phase Deep Reinforcement Learning Approach for UAV-Assisted Content Delivery Across Multiple Base Stations.md"
fulltext_path: "03fulltext/备选讲组会论文/SUT9CK75.md"
zotero_item: "zotero://select/library/items/SUT9CK75"
zotero_pdf: "zotero://open-pdf/library/items/YCJEXIJ9"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# DDRL: A Dual-Phase Deep Reinforcement Learning Approach for UAV-Assisted Content Delivery Across Multiple Base Stations

> PDF 原文逐页文本抽取；来源文件 SHA-256：`1d89544a294d9fcebe4a54afa32a3b36d45f91034243376516e5791439ffd2bc`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 14367
DDRL: A Dual-Phase Deep Reinforcement
Learning Approach for UA V-Assisted Content
Delivery Across Multiple Base Stations
Xinshuai Hua, Long Chen
 , Xia Zhu, Xiaoping Li
 , Senior Member, IEEE, and Jingjing Li
Abstract—Uncrewed Aerial Vehicles (UA Vs) with caching capa-
bilities present a ﬂexible and scalable approach for efﬁcient
content delivery in wireless communication environments with
high demand. However, the challenges posed by the limited
energy and storage capabilities of UA Vs signiﬁcantly affect
content delivery efﬁciency. In this paper, we consider the problem
of UA V-assisted content delivery across multiple base stations,
with the aim of reducing content acquisition delays by jointly
optimizing UA V trajectory, cache replacement, and transmission
power. A Dual-phase Deep Reinforcement Learning (DDRL)
framework is proposed, integrating real-time decision making
with ofﬂine training to adapt dynamic user demands and multi-
BS conﬁgurations. The Particle Swarm Optimization (PSO)
algorithm is incorporated to improve UA V caching performance.
The simulation results demonstrate that the DDRL framework
achieves up to a 8% reduction in latency and a 5% improvement
in cache hit rate compared to the best baseline algorithm,
showcasing its efﬁciency in UA V-assisted content delivery.
Index Terms—UA V caching, trajectory design, cache replace-
ment, energy constraint, deep reinforcement learning, particle
swarm optimization.
I. I NTRODUCTION
U
NCREWED Aerial Vehicles (UA Vs) are emerged as a
promising solution to improve wireless communication
services, due to their mobility, cost effectiveness, and ability
to provide coverage in areas with limited ground infrastructure
[1]. In contrast to traditional base stations (BSs) or vehicle-
mounted mobile base stations [2], UA Vs offer a ﬂexible and
scalable means to support communication in challenging envi-
ronments, such as disaster-stricken areas or high-trafﬁc regions
Received 10 December 2024; revised 6 June 2025, 11 Octo-
ber 2025, and 14 January 2026; accepted 19 March 2026. Date
of current version 27 March 2026. This work was supported in
part by the Jiangsu Provincial Frontier Technology Development Pro-
gram under Grant BF2025601 and in part by the National Natu-
ral Science Foundation of China under Grant 62302095 and Grant
62363032. The associate editor coordinating the review of this article
and approving it for publication was M. Fiore. (Corresponding author:
Long Chen.)
Xinshuai Hua, Long Chen, and Xia Zhu are with the School of Computer
Science and Engineering, Southeast University, Nanjing 211189, China, and
also with the Key Laboratory of New Generation Artiﬁcial Intelligence
Technology and Its Interdisciplinary Applications, Ministry of Education,
Southeast University, Nanjing 211189, China (e-mail: chen long@seu.
edu.cn).
Xiaoping Li is with the School of Computer Science, Guangdong University
of Technology, Guangzhou 510006, China.
Jingjing Li is with the Bellini College of Artiﬁcial Intelligence, Cyberse-
curity, and Computing, University of South Florida, Tampa, FL 33612 USA.
Digital Object Identiﬁer 10.1109/TWC.2026.3677068
where traditional BSs are either unavailable or congested.
Furthermore, with the rapid increase in mobile devices and
the escalating demand for high-quality content delivery, there
is a pressing need for efﬁcient content delivery strategies [3].
Equipping UA Vs with caching capabilities enables the storage
of popular content closer to end-users, signiﬁcantly reducing
latency and improving Quality of Experience (QoE) [4]. For
example, with the growing popularity of virtual reality (VR)
devices, the requirement for high-quality, low-latency content
has increased signiﬁcantly [5]. As immersive VR experiences
are highly dependent on real-time data streaming and seamless
interaction, any latency or drop in content quality can greatly
detract the user experience [6]. This places additional pressure
on the network infrastructure, as high bandwidth and low
latency are critical to maintain seamless content delivery.
In this paper, we focus on optimizing UA V-assisted content
delivery in multi-base station (multi-BS) environments, partic-
ularly during high-demand periods such as peak hours or urban
hotspots. During these periods, BSs become congested due to
the large number of simultaneous user requests, leading to
delays and degradation in service quality. UA Vs are deployed
to ofﬂoad trafﬁc from congested BSs by providing content
delivery directly to users. The UA Vs can take off and land
at different BSs, which also serve as charging hubs and
content update points. The characteristics of the problem under
consideration include: (1) User demand is highly dynamic and
geographically distributed, with users located in different areas
and requiring varying content in real-time. (2) UA Vs have
limited battery capacity, restricting their operational time and
necessitating periodic returns to BSs for recharging. (3) UA Vs
have limited storage space, which constrains the amount of
content they can cache locally, requiring frequent retrieval or
updates from BSs. The objective is to jointly optimize the
UA V’s trajectory, caching strategy, and transmission power,
improving content delivery efﬁciency, and reducing BS con-
gestion, while maintaining high-quality service for users.
These characteristics present several signiﬁcant challenges
for optimizing UA V-assisted content delivery. (1) Han-
dling dynamic and diverse user demands: Users generate
diverse, geographically dispersed requests with strict real-
time requirements. UA Vs must balance bandwidth, low-latency
transmission, and throughput, while adapting to dynamic con-
ditions, creating a rapidly changing and complex solution
space. Optimal decisions must continuously adapt to real-time
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

14368 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
conditions, increasing the complexity of achieving robust and
efﬁcient solutions. (2) Trajectory optimization with multi-BS
and energy constraints: Limited UA V battery life creates a
fundamental conﬂict between maximizing user coverage and
minimizing energy use. In multi-BS environments, UA Vs must
plan efﬁcient paths to serve users and recharge timely. The
trade-offs between extending operational time, maintaining
low latency, and optimizing throughput result in a highly
constrained and non-linear optimization problem. The con-
stantly changing UA V trajectory decision variables and BS
connectivity further complicate the solution space, making
it dynamic and multi-dimensional. (3) Cache management
with limited storage: Cache management with limited storage:
The ﬁnite storage capacity of UA Vs presents a trade-off
between caching popular content to reduce BS retrievals and
dynamically adapting to real-time user demand. This conﬂict
intensiﬁes as user pReferences evolve unpredictably, requir-
ing UA Vs to manage a continuously shifting cache strategy.
Balancing cache hit rates with storage constraints ampliﬁes
the computational complexity, as the optimal solution space
changes with every user request and content popularity update.
This paper proposes a Dual-phase Deep Reinforcement
Learning (DDRL) framework to tackle the previously men-
tioned challenges. DDRL is combined with Particle Swarm
Optimization (PSO) to optimize UA Vs trajectories, caching
strategies, and power allocation. The main contributions of
this paper are summarized as follows:
• A novel framework is proposed for cache-enabled UA Vs
in multi-BS networks, aimed at improving content deliv-
ery in hotspot areas. Our approach jointly optimizes UA V
trajectory, cache replacement, and transmission power to
minimize the overall content acquisition delay.
• A DDRL framework is outlined to design UA Vs trajec-
tories and power allocation, integrating ofﬂine learning
with online decision-making to boost UA V ﬂexibility in
multi-BS settings with ﬂuctuating user demands. A GRU-
based sequential model is introduced to capture temporal
dependencies in user requests, UA V energy dynamics, and
mobility patterns, enabling more coherent and foresighted
trajectory planning.
• A PSO-optimized cache replacement strategy is inte-
grated into the DRL framework. By using PSO to
ﬁne-tune the cache evaluation function and obtain the
extrinsic reward, DDRL agents learn more effective
caching policies, leading to higher cache hit rate and
improved content delivery performance in UA V-assisted
networks.
The remainder of the paper is organized as follows.
Section II reviews related work on UA V-assisted wireless
networks. In Section III, the system model and problem
formulation are presented. Section IV outlines our proposed
optimization approach for designing joint UA V trajectories and
caching replacements. Section V provides simulation results
and analysis, followed by the conclusion in Section VI.
II. R ELATED WORK
Many research efforts [7], [8] have proposed UA V-assisted
frameworks aimed at improving network efﬁciency in hotsopt
regions. UA V-assisted content delivery focuses on key issues
such as trajectory planning, cache strategy development, and
resource allocation for communication.
Some studies have concentrated on designing an optimal
UA V trajectory to improve coverage and reduce energy usage.
In our previous work [9], a two-stage heuristic (HMUR) has
been proposed for the planning of UA V trajectory in mobile
edge computing with time window constraints. Zeng et al. [10]
optimized UA V trajectories to maximize data throughput in
mobile relaying systems, considering the mobility and energy
constraints of the UA V . Mozaffari et al. [11] developed a
framework for optimizing the trajectory of UA Vs to enhance
energy efﬁciency in IoT communications. Lyu et al. [12]
explored optimal UA V placement and trajectory planning to
serve as mobile base stations, with the objective of maximizing
coverage area while ensuring connectivity. Zhang et al. [13]
investigated strategies for energy-efﬁcient trajectory planning
in UA Vs supporting IoT devices, aiming to optimize both ﬂight
time and energy consumption. Nguyen et al. [14] proposed
a deep reinforcement learning-based technique to optimize
UA V trajectories and resource allocation in UA V-assisted IoT
systems, with the objective of maximizing data collection
efﬁciency while minimizing resource usage and ﬂight time.
Al-Hilo et al. [15] leveraged UA Vs for content delivery in
Internet of Vehicle scenarios by addressing challenges like
dynamic vehicle requests, caching strategies, and energy-
efﬁcient trajectory.
Caching strategy in mobile networks has been explored
for its potential to improve data transmission efﬁciency.
Fan et al. [16] investigated the role of cache-enabled UA Vs in
post-disaster communication networks, providing performance
analysis using stochastic geometry. Zhang et al. [17] focused
on network deployment and resource allocation for cache-
enabled UA V communications, aiming to enhance quality
of service for users. Ji et al. [18] combined UA V trajec-
tory optimization with communication strategies to improve
caching efﬁciency in cellular networks. Zhang et al. [19]
explored the use of intelligent caching strategies for UA Vs
acting as ﬂying base stations to improve content delivery
performance. Wu et al. [20] investigated UA V-aided edge
caching for vehicular networks, formulating a joint caching
and trajectory optimization problem and proposing a deep
supervised learning approach. Su et al. [21] proposed a content
delivery mechanism between UA Vs and the Internet of Con-
nected Vehicles (IoCVs) in heterogeneous networks, with the
objective of minimizing transmission delay and improving user
QoE through a coalition game-based optimization strategy.
Lam et al. [22] proposed a TCP-3DF framework that optimizes
caching, power allocation, and 3D trajectory for UA V-assisted
IoT networks using a modiﬁed Genetic Algorithm (GA) to
achieve efﬁcient multimedia delivery with minimized ﬂight
distance and service time.
Previous work has extensively explored the use of UA Vs
in communication networks, mainly focusing on improving
wireless coverage and ensuring stable communication links.
Zhou et al. [23] addressed the challenges of channel assign-
ment and power allocation in multi-UA V communication,
suggesting optimization techniques to enhance signal quality
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

HUA et al.: DDRL: A DUAL-PHASE DEEP REINFORCEMENT LEARNING APPROACH 14369
Fig. 1. Framework of UA V-assisted content delivery in multi-BS.
and minimize interference. Li et al. [24] concentrated on
the integration of UA V trajectory planning with resource
allocation to enhance the performance of the communication
network. Zhou et al. [25] tackled interference issues in multi-
UA V communication systems by jointly optimizing channel
assignment and power allocation to maximize the minimum
SINR and adapt resource allocation based on mission priority.
Cui et al. [26] examined information security in UA V-ground
communication by jointly optimizing the trajectory and trans-
mission power to maximize the average worst-case secrecy
rate.
Existing research on UA V-assisted content delivery has
primarily focused on isolated aspects such as trajectory opti-
mization or caching strategies, with limited work addressing
their combined optimization alongside resource allocation.
Ji et al. [27] investigated the joint optimization of the UA V
trajectory, cache placement, and power allocation in single
base station wireless networks. Their work did not consider
cache replacement strategies. To the best of our knowledge,
few studies have explored the joint optimization of UA V-
assisted content delivery across multi-BS. This research seeks
to bridge this gap by proposing a integrated approach to UA V
optimization. However, integrating these elements in such
scenarios into a uniﬁed framework signiﬁcantly complicates
the problem but is essential to address real-world challenges.
III. S YSTEM MODEL
As shown in Fig. 1, we consider a wireless communi-
cation system where cache-enabled UA Vs are deployed to
deliver content to ground users distributed within a multi-
BS geographical area. The system is composed of three
main components: (1) Base Stations: Denoted by the set
B = {b | b = 1, 2, 3}, each base station is located at
Lb = [x b,yb]. The BS serves as a central hub, supplying
UA Vs with both power and content. (2) UA Vs: Denoted by
the setU ={u|u = 1, 2,...,U }, each UA V starts its mission
from the BS, serves user requests, and returns to the BS after
completing its task. UA Vs operate within a constant coverage
radius R and ﬂy at a ﬁxed altitude H. Due to limited energy
TABLE I
MAIN NOTATIONS USED IN THIS PAPER
resources, effective trajectory planning for each UA V is crucial
to maximize coverage and minimize energy consumption. (3)
End users: Denoted by the set G = {g|g = 1, 2,...,G },
ground users are located at ﬁxed positions within the service
area. The horizontal coordinates for each user g ∈ G are
speciﬁed as Lg = [xg,yg]. A summary of the main notation
used in the paper is presented in Table I.
In the multi-BS scenario, BSs are strategically deployed
within the service area, and UA Vs collaborate with these BSs
to retrieval content and plan trajectory. Each user is located
within the overlapping coverage area of both BSs and UA Vs.
All entities, including BSs, UA Vs and users, operate within a
ﬁxed area deﬁned by [0,x max]× [0,y max]. UA Vs have limited
cache capacity and can pre-load popular content for delivery to
users upon request. When a requested content is not available
in a UA V’s local cache, the UA V must fetch it from a BS over
a wireless backhaul link, utilizing a cache replacement strategy
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

14370 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
to optimize storage. Users’ content requests are dynamic and
stochastic, exhibiting a Zipf distribution as described in [28],
which is a typical pattern for content popularity. In this paper,
our objective is to jointly optimize UA V trajectory, cache
replacement and transmission power to minimize the total
content acquisition delay.
A. UAV Mobility Model
We assume that all UA Vs operate at a ﬁxed altitudeH above
the ground and move within a two-dimensional plane. The
mission duration T is divided into N uniform time slots with
duration t, such that N ={n|n = 1, 2,...,N }. We assume
that t is sufﬁciently small, allowing the UA Vs’ positions to
be considered static within each time slot. At each time slot
n, UA Vu moves a distance du[n]∈ [0,d max] in a direction
speciﬁed by an angle αu[n]∈ [0, 2π]. Let (xu[n],yu[n]) be
the coordinates of UA Vu at time slot n. The position of UA V
u is updated using:
xu[n + 1] = xu[n] +du[n] cos(αu[n]),
yu[n + 1] = yu[n] +du[n] sin(αu[n]) (1)
Simultaneously, numerous constraints are set on UA V move-
ments to guarantee their safe and effective operation:
(1) UA Vs must remain within the predeﬁned service area,
which is represented as:
0≤xu[n]≤xmax, 0≤yu[n]≤ymax, ∀u∈U ,n∈N
(2)
(2) The distance between any two UA Vs must be at least
dmin to prevent collisions:
‖Lu[n]− Lk[n]‖≥ dmin, u ⁄=k,∀u,k∈U ,∀n∈N (3)
(3) UA V movements are constrained by maximum speed
and energy availability. Each UA V has a limited initial energy
reserve E0. Following [29], the energy consumption of each
UA V during movement is calculated using:
Euseu [n] = e1
(
1 + 3v2uav
v2tip
)
+ 12e3v3uav
+e2
(√
1 + v4uav
4v40− v2uav2v20
)1/2
(4)
The power consumption Euseu [n] consists of three main com-
ponents: blade proﬁle power, induced power and parasite
power. The constants e1, e2, and e3 depend on factors such
as the UA V’s power, rotor characteristics, and air density.
The parameters vtip and v0 refer to the rotor’s tip speed
and the average velocity induced by the rotor, respectively.
This formulation effectively captures the energy dynamics
associated with the UA V’s power requirements during various
ﬂight conditions.
B. Communication and Transmission Model
Given the altitude of the UA V and the complexity of its sur-
rounding environment, the communication channels between
the UA V and user, as well as between the UA V and BS, are
characterized by probabilistic line-of-sight (LoS) and non-line-
of-sight (NLoS) conditions [30]. These factors signiﬁcantly
inﬂuence the dynamics of the wireless channel. In this paper,
the air-to-ground propagation channel is used to determine
communication.
As referenced in [31], the probabilities of establishing a LoS
connection from the UA V to the user and BS are given by:
PrLoS = 11 +α1 exp (−α2 (θ−α1)) (5)
whereα1 andα2 are environment-speciﬁc constants, and θ =
180
π arcsin
(
H
du
)
is the elevation angle from UA V to user and
UA V to BS,du =
{
dnu,g,dnu,b
}
represents the distances from
UA Vu to user g, and UA Vu to BS b in time slot n.
The probability of a NLoS connection is PrNLoS = 1−
PrLoS. The overall path loss ϕt from UA V to user and UA V
to BS is determined as a weighted sum of the LoS and NLoS
path losses:
ϕt =PrLoSPLLoS +PrNLoSPLNLoS (6)
where PLLoS and PLNLoS are the average path losses for
LoS and NLoS links.
For the UA V to BS connection, following [32], PLLoS =
d−χu and PLNLoS =κd−χu . For the UA V to user connection,
the LoS and NLoS are calculated as follows:
PLLoS = 20 log (4πfcdu/vc) +ηLoS,
PLNLoS = 20 log (4πfcdu/vc) +ηNLoS (7)
wherefc is the carrier frequency, and ηLoS andηNLoS are the
shadowing factors for the respective links, κ is the additional
path loss factor of the NLoS link, vc is the velocity of light.
We assume that content transmission from different users
to UA Vs will not interfere with each other, using Orthogonal
Frequency Division Multiple Access (OFDMA) as outlined
in 802.11ax [33]. Although more complex communication
models are available, they are beyond the purview of this
paper. Given a ﬁxed transmission power ϕ and an average
noise power ϕnoise, the received signal-to-noise ratio (SNR)
can be calculated as:
ϕn,snr =ϕ−ϕt−ϕnoise (8)
Following [34], [35], we assume that the received SNR must
exceed a thresholdϕ0. Otherwise, transmission fails. Applying
Shannon’s capacity, the maximum transmission rate between
UA V and user in time slot n is:
Ru,g[n] = Bu log
(
1 +ϕu,gn,snr) (9)
where Bu denotes the bandwidth from UA V to user, ϕu,gt is
the overall path loss ϕu,gt,snr from UA V to user based on Eq. 6.
Similarly, the maximum transmission rate between UA V and
BS in time slot n is:
Ru,b[n] = B0 log
(
1 +ϕu,bn,snr) (10)
whereB0 denotes the bandwidth from UA V to BS,ϕu,bn is the
overall path loss ϕu,gn,snr from UA V to BS based on Eq. 6.
When a user connects to a UA V , the transmission delay con-
sists of two primary components: the downlink transmission
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

HUA et al.: DDRL: A DUAL-PHASE DEEP REINFORCEMENT LEARNING APPROACH 14371
delay from the UA V to the user and the backhaul transmission
delay from the UA V to the BS. At each time slot n, users
request content from the UA V , the downlink transmission delay
from UA V to user and the backhaul transmission delay from
BS to UA V can be calculated by:
Tu,g[n] = SqRu,g[n] (11)
Tu,b[n] = SqRu,b[n] (12)
whereSq represents the bit-size of content q, and Ru,g[n] and
Ru,b[n] denote the data transfer rates for the connection from
UA Vu to user g and from UA V u to BS b at time slot n,
respectively.
C. Cache Distribution Model
In the cache-enabled UA Vs network, UA Vs distribute
request content to the ground users, with each UA V pre-storing
popular content derived from past user demand within the
service zone. When a user asks for content that resides in
the UA V’s local cache, the UA V can directly transmit it to the
user via a downlink wireless link. Conversely, if the content is
absent from the cache, the UA V retrieves it from the nearest
BS through a wireless backhaul and forwards it to the user,
simultaneously running a cache replacement algorithm.
Suppose that the BS possesses all the required contents,
with each content assumed to be of size Sq Mbits and stored
as a single block in the BS. The complete content library
consists of Q blocks, denoted by Q ={q| q = 1, 2,...,Q }.
The content request matrix, expressed as x∈{ 0, 1}NG×Q, is
structured such that xg,q [n] = 1 indicates that user g requests
content q during the time slot n; otherwise, xg,q [n] = 0 .
Due to the limited storage capacit of UA Vs, their caching
capacity is constrained. Let C represents the caching capacity
of the UA V . The total amount of content cached by each UA V
must satisfy the constraint:
Q∑
q=1
βu,qSq≤C (13)
where βu,q∈{0, 1} is a binary variable indicating whether
UA Vu caches content q. If βu,q = 1, the content is cached;
otherwise, βu,q = 0.
Each user’s request pattern is inﬂuenced by content popu-
larity, which follows a Zipf distribution characterized by the
skewness parameter ρ:
Reqq(ρ,i ) =
1
iρ
∑I
i=1
1
iρ
(14)
where ρ is the rank of the content based on popularity.
D. Problem Formulation
The main objective is to minimize the total content acqui-
sition delay for all users while maximizing the cache hit rate
and improving energy efﬁciency.
This encompasses both the downlink transmission delay
from the UA V to the user and the backhaul transmission delay
from the UA V to the BS when a cache miss occurs. The
overall delay experienced is represented mathematically by the
following:
min
∑
g∈G
∑
i∈U∪B
Di,g (15)
where Di,g denotes the delay experienced by user g when
retrieving content from source i.
The source could be a UA V u∈U or a BS b∈B . In the
scenario where i represents the UA V u, the user g retrieves
the cache directly from the UA V . In contrast, if not, the UA V
u serves as an intermediary, ﬁrst obtaining the cache from the
BS b and subsequently delivering it to the user g. The delay
Di,g for user g is calculated as:
Di,g =
∑
n∈N
∑
q∈Q
xg,q [n] (Ti,g[n] + (1−βi,q[n])Ti,b[n])
(16)
IV. D UAL-PHASE DEEP REINFORCEMENT LEARNING
FRAMEWORK
The joint optimization of UA V trajectory, transmission
power and cache replacement presents signiﬁcant challenges
due to the highly non-convex decision space. To solve it, we
adopt the Proximal Policy Optimization (PPO), a model-free,
on-policy, policy-gradient, actor-critic based algorithm known
for its robust convergence and sample efﬁciency [36]. PPO
iteratively updates policies within a trust region to ensure
stable and monotonic improvement. Compared to policy-based
algorithms such as deep deterministic policy gradient (DDPG),
it may not be suitable since it suffers from high variance and
unstable convergence due to its fully off-policy nature. Among
PPO variants, Clip-PPO maintains a balance between explo-
ration and exploitation through its clip function by limiting
the probability ratio within (1−ϵ, 1 + ϵ), which stabilizes
the training process. It is crucial in our cache-enabled UA V-
assisted multi-BS network as excessive trajectory adjustments
can lead to increased energy consumption and latency.
The proposed DDRL mainly includes two phases
(Figure 2): ofﬂine training and online decision-making. The
ofﬂine training phase involves training the actor-critic network
using a deep neural network (DNN) to maximize PPO’s
clipped objective while minimizing the value network’s loss.
The online decision phase leverages a trained CNN-GRU-
based network to process multi-channel inputs and make
real-time decisions for trajectory and caching. Additionally,
PSO is integrated into the environment for efﬁcient cache
replacement. This approach enhances the UA Vs’ ability to
balance trajectory optimization and caching efﬁciency, offering
robust performance in complex, dynamic scenarios.
A. DDRL Framework Design
In the proposed DDRL framework, each UA V operates as
an agent within a dynamic environment. This environment
includes ground users generating content requests, UA Vs with
limited energy and cache capacity, and BSs acting as content
sources. We formulate our problem as a Markov Decision
Process (MDP) which is denoted by a 5-tuple ⟨S,A,P,R,γ⟩
where:
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

14372 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 2. The architecture of the DDRL algorithm.
• Sdenotes the state space which encompasses all possible
states obtained by an observation function. Each state S
captures comprehensive information necessary for each
UA V to make informed decisions. Speciﬁcally, the state
includes: Locations and content request of the users;
positions of all UA Vs on the grid area, their remaining
energy levels and the BSs’ locations at the current time
slot. Mathematically, the state space in time slot n can
be described as:
S =
{
(xu[n],yu[n],Eresu [n])u∈U, (xb[n],yb[n])b∈B,
(xg[n],yg[n],Reqq[n])g∈G
}
(17)
• Ais the action space which deﬁnes all possible actions
UA V agent can take. Each action a ∈ Ais a vector
consisting of UA V moving distancedu[n], directionαu[n]
and power allocation pu[n] for content delivery. Mathe-
matically, the action space in time slotn can be described
as:
A ={du[n],αu[n],pu[n]} (18)
• P is the state transition probability characterizes the
dynamics of the environment by specifying the probabil-
ity of moving from one state to another given a particular
action. Formally,
P(st+1|s,a ) = Pr (st+1|st =s,at =a) (19)
it represents the probability of transitioning to state st+1
from state s when action a is taken.
• Ris the discounted cumulative reward. Once an agent
executes its chosen actions, it will receive an immediate
reward in each time slot. Based on previous analysis,
similar to [18] and [37], the reward for each UA V agent
in time slot n is composed of two parts, mathematically
expressed as:
Rn =RExtru [n] +ϵRIntru [n], ∀u∈U (20)
where RExtru [n] is the extrinsic reward typically aligns
with the system’s primary objective, RIntru [n] is deﬁned
to incorporate the UA V energy consumption and served
user cache requests.
Our goal is to minimize the total cache acquisition delay
and maximum the cache hit rate under the UA V energy
constraints. Hence the extrinsic reward is calculated by
cache hit and delay rewards. According to Eq. 15, the
delay rewards is expressed:
Rdelayu [n] = L−∑
g∈G
∑
i∈U∪B
Di,g[n] (21)
where L is a large constant ensuring the delay reward
remains positive. By reducing content acquisition delay,
the system increases the overall reward, incentivizing
efﬁcient content delivery.
In this system, the reward for cache hits is based on the
number of times the cache has been hit. If UA V u has a
cache hit at time slot n, the reward is proportional to
the number of times that speciﬁc cache has been hit.
Conversely, if there is a cache miss, a ﬁxed penalty is
applied. The cache reward function is deﬁned as:
Rcacheu [n] =
{
Nqu[n], if there is a cache hit
−rmiss, if there is a cache miss (22)
where Nqu[n] represents the number of times the cache
for content q in UA Vu has been hit up to time slot n,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

HUA et al.: DDRL: A DUAL-PHASE DEEP REINFORCEMENT LEARNING APPROACH 14373
rmiss denotes the ﬁxed penalty applied for a cache miss.
To simplify the calculation, the variable βu,q can still be
used to indicate whether there is a cache hit, and the total
number of hits Nqu[n] is updated accordingly. The reward
function can be rewritten as:
Rcacheu [n] = Nqu[n]βu,q−rmiss(1−βu,q) (23)
Therefore, the extrinsic reward can be expressed as:
RExtru [n] = Rdelayu [n] +Rcacheu [n] (24)
Given the UA V’s limited energy, it is essential to incorpo-
rate energy consumption into the reward design. Effective
energy management enables the UA V to complete all
user content requests while retaining enough energy to
return the BS. To enforce this, a large penalty is applied
if a UA V depletes its energy mid-mission. Additionally,
an intrinsic reward is introduced to encourage efﬁcient
energy use, calculated based on the ratio of energy
consumed to the number of users served:
RIntru [n] = NumGu[n]Euesu [n] (25)
where Euseu [n] is denoted UA V u has consumed the
energy in time slot n which calculated by Eq. 4 and
NumGu[n] is denoted the number of users of the UA V u
has completed the user request in time slotn. By this way,
the intrinsic reward function encourages UA Vs to serve
more users using less energy, promoting overall system
energy efﬁciency.
The objective of the learning system is to identify an opti-
mal policy π that maximizes the cumulative discounted
reward over time, deﬁned by:
Rcum =
N∑
n=1
γnRn (26)
• γ is the reward discount factor between 0 and 1 that
determines the importance of future rewards relative to
immediate rewards.
B. Online Decision-Making
In the initial phase of online decision-making, the policy and
value networks, along with the Deep Neural Networks (DNNs)
suggested in [38], start with random initialization. These
DNNs encompass convolutional neural networks (CNN) and
gated recurrent unit (GRU) networks. As training progresses
and more epochs are completed, these networks are gradually
updated, enhancing the UA V’s decision-making ability by
leveraging accumulated experiences.
The details are shown in Algorithm 1. The input consists of
two channels that are used to convey spatial and environmental
details for CNN processing. Channel 1 represents a spatial
map of user locations and users’ speciﬁc content request. This
channel encodes the spatial distribution and user density, pro-
viding critical information on where communication demands
are concentrated. Channel 2 incorporates the positions of each
BS and UA V , along with the current remaining energy levels
of each UA V .
Algorithm 1 Online Decision-Making Procedure
At each time slot, the system gets the current environment
state, processing this through the CNN to extract a feature
representation. Traditional RL algorithms often suffer from
limited exploration capabilities, which can lead to premature
convergence to suboptimal policies. In addition to capturing
spatial features, the CNN module proactively guides UA V
agents towards unexplored or underserved regions, promoting
efﬁcient spatial coverage and reducing redundant movement
to break the performance ceiling. This representation is then
combined with the previous action, the last reward. Next,
this combined feature vector is fed into the GRU to capture
temporal dependencies over sequential time slots. Temporal
information across adjacent time slots is inherently correlated,
and capturing these dependencies enables the agent to pre-
dict spatial mobility patterns and less energy consumption
trajectories. Finally, the GRU outputs the representation for
the Actor-Critic model, the actor network generates an action
distribution, and the critic network estimates the expected
cumulative reward.
Each UA V agent independently performs the sampled
action and receives an immediate reward. A new transition
(st,at,rt,st+1) is stored in the experience bufferD for future
ofﬂine training and policy improvement.
C. Ofﬂine Training
The ofﬂine training phase focuses on improving the policy
and value networks using the experiences collected during the
online phase, the details are shown in Algorithm 2. At the
beginning of this phase, the global policy network parameters
θ and the value network parameters φ are initialized, along
with setting the PPO hyperparameters. For each training itera-
tion, experience dataD is ﬁrst collected from the buffer used to
calculate the advantage estimate using Generalized Advantage
Estimation (GAE). For each transition (st,at,rt,st+1), the
temporal difference (TD) error is computed as:
δt =rt +γVφ(st+1)−Vφ(st) (27)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

14374 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Algorithm 2 Ofﬂine Training Procedure
where γ is the discount factor used in the cumulative dis-
counted reward function (26), δt reﬂects the discrepancy
between the immediate reward plus future value and the
current state value.
The advantage estimate ˆAt is then computed recursively as:
ˆAt =δt +γλ ˆAt+1 (28)
Using the advantage estimates, the target values are com-
puted as:
V targett = ˆAt +Vφ(st) (29)
The policy network is then updated by maximizing the PPO
objective function, which includes a clipped surrogate loss to
prevent large policy changes that could destabilize training.
This objective is expressed as:
LCLIP(θ) = 1|D|∑t∈D min(r(θ) ˆAt, clip (r(θ), 1−ϵ, 1 +ϵ) ˆAt)
(30)
where r(θ) = πθ(at|ht)πθold (at|ht) denotes the probability ratiobetween the old policy and the new policy, πθ represents
the current policy probability, πθold is the previous policy
probability, andϵ is the clipping threshold, constraining policy
updates within a limited range.
The policy parameters θ are updated via gradient ascent:
θ =θ +α∇θLCLIP(θ) (31)
Similarly, the value network parameters φ are updated by
minimizing the value function loss:
LVF(φ) = 1|D|∑t (Vφ(st)−V targett )2 (32)
and adjusted via gradient descent:
φ =φ−α∇φLVF(φ) (33)
Once an iteration concludes, the updated parametersθ andφ
are distributed to each UA V , providing them with reﬁned policy
and value estimates to improve trajectory optimization in
future episodes. This iterative process of gathering experiences
Algorithm 3 Cache Replacement Strategy Based on PSO
and updating the networks builds a robust learning system,
enhancing the adaptability of UA Vs and decision making in
dynamic environments.
D. Cache Replacement Strategy
We propose a caching replacement strategy for cache-
enabled UA Vs that adapts dynamically according to user
requests and environment conditions. Following the initial
caching setup, we introduce an evaluation function [39],
[40] to determine which cached content should be replaced.
Efﬁcient cache management is crucial to optimize the per-
formance of the UA V-assisted content delivery network. To
enhance the cache hit rate and thereby reduce the overall
acquisition delay, we utilize a Particle Swarm Optimization
(PSO)-inspired method to optimize the weight parameters of
the cache evaluation function, which determines the priority of
content items for replacement. By adjusting these weights, the
algorithm seeks to maximize the cache hit rate over time. The
cache evaluation function E(q) assesses the value of caching
a content item q based on multiple factors:
E(q) = γ1Pop(q) +γ2SizeRatio(q) +γ3ReqFre(q) (34)
where γ1, γ2, γ3 are the weight parameters satisfying γ1 +
γ2 +γ3 = 1. Pop(q ) is the popularity for content q which is
modeled using a Zipf distribution, SizeRatio(q ) considers the
impact of a content item’s size relative to the remaining cache
capacity. and C is the capacity of each UA V and ReqFre(q )
is the request frequency for content q within a speciﬁc time
interval.
The PSO algorithm is used to optimize the weight param-
eters γ1, γ2, and γ3 in order to maximize the cache hit rate.
The optimization process is shown in Algorithm 3 which
involves the following steps. Initially, a swarm of particles Z
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

HUA et al.: DDRL: A DUAL-PHASE DEEP REINFORCEMENT LEARNING APPROACH 14375
TABLE II
SIMULATION PARAMETER SETTINGS
is randomly generated with both positions (weight parameters)
and velocities, each representing a potential solution. The
optimization process is carried out iteratively, where each
particle applies its weight parameters to the evaluation function
E(q) and simulates cache operations over the service request
sequence L. During each simulation, caching decisions are
made based on the evaluation function. The replacement
process either adds new content to the cache or swaps out
existing content with lower evaluation values when the cache
reaches capacity. After simulating the cache operations, the
cache hit rate is calculated for each particle, serving as its
ﬁtness value.
Particles update their personal best positions if their current
ﬁtness exceeds their previous best. Similarly, the global best
position is also updated if any particle achieves a ﬁtness
superior to the current global best. Subsequently, the particles
adjust their velocities and positions using the PSO update
equations:
vt+1i =wvti +c1r1(pBesti−γti ) +c2r2(gBest−γti ) (35)
γt+1i =γti +vt+1i (36)
Here, w is the inertia weight, c1 and c2 are cognitive and
social coefﬁcients, and r1 and r2 are random values between
0 and 1. The updated weight parameters are normalized to
ensure they remain within [0, 1] and sum to 1. This iterative
process continues for a predetermined number of iterations or
until convergence criteria are met.
V. P ERFORMANCE EVALUATION
This section presents the results of experiments designed to
evaluate the performance of the proposed DDRL algorithm.
The experiments aim to compare the efﬁciency of the proposed
algorithm with several baseline methods in terms of delay and
cache hit rate.
A. Simulation Setup
We consider a cache-enabled UA V-assisted multi-BS net-
work with a set of users randomly distributed over a square
TABLE III
SUMMARY OF DDRL P ARAMETERS
area of 1.0 km ×1.0 km, similar to the datasets randomly
generated in [18] and [38]. This network consists of three BSs
and a set of UA Vs, collaboratively providing content delivery
services to users within the area. UA Vs begin at BSs and
head back to the closest BS once they have completed their
tasks. UA Vs operate at a ﬂight altitude of H = 100 meters.
To prevent collisions, UA Vs must maintain a minimum safe
separation of dmin = 1 meter, and their maximum speed, vuav,
is capped at 20 m/s. The time slot duration is set to n = 1 s,
and each training episode consists of T = 500 time slots. The
Zipf parameter ρ is ﬁxed to 1.3. Each UA V is equipped with
a caching capacity of C = 100 Mbits. The content size Sq
for each request is assumed to follow a uniform distribution
with a mean of 10 Mbits. Table II provides details on the
communication settings. Table III summarizes the details of
DDRL parameters. Simulations are executed on a server with
an NVIDIA GTX 4090 Ti GPU, utilizing Python 3.8 and
PyTorch to construct the simulation models.
B. Convergence and Scalability Analysis
Initially, we demonstrate that our DDRL model converges.
Fig. 3a indicates the total reward accumulated per episode.
With more iterations, we observe a clear trend in the cumula-
tive reward, which increases and eventually converges. This
stabilization indicates that the algorithm successfully opti-
mizes trajectory and caching decisions, enhancing service
coverage and resource allocation efﬁciency. This consistent
convergence demonstrates that our proposed framework is
effective in addressing dynamic challenges associated with
UA V trajectory and caching management, resulting in an
optimized policy that maximizes performance in terms of
accumulated reward.
Fig. 3b shows the energy consumption ratio across 2500
training episodes. The energy consumption ratio ζ is deﬁned
as the ratio of the total energy consumed by all UA Vs in
transmitting content relative to their initial energy reserves at
the end of time slot n, mathematically, it can be expressed as:
ζ = 1U·E0
N∑
n=1
U∑
u=1
eun (37)
where U represents the number of UA Vs, E0 is the initial
energy per UA V ,N is the total number of time slots, and eun
denotes the energy consumed by UA V u at time slot n. In
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

14376 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 3. Convergence of DDRL: (a) Accumulated reward, (b) Energy consumption ratio, (c) Average entropy loss.
Fig. 4. Comparison of convergence: (a) Accumulated reward, (b) Energy consumption ratio.
Fig. 5. Comparison of Accumulated reward and Energy consumption ratio under different learning rates and discount factors.
the early stages of training, the energy consumption ratio is
notably high, with values peaking around 0.25. This elevated
consumption is indicative of inefﬁcient energy usage, likely
due to the model’s initial exploratory phase, where UA Vs may
not yet have optimized their decisions. However, as training
progresses, the ratio consistently stabilizes with a lower level.
This trend signiﬁes that the DDRL algorithm has learned more
energy-efﬁcient strategy. The convergence energy consumption
ratio reﬂects the efﬁcient energy usage in the UA V-assisted
content delivery networks.
Fig. 3c illustrates the trend in average entropy loss across
training episodes for the DRL. Entropy in reinforcement
learning algorithms is often used as a measure of exploration in
the action space. A higher entropy value encourages the agent
to explore more diverse actions, while a decreasing entropy
indicates that the agent is progressively focusing on more
speciﬁc, optimal actions as it learns. By the end of training,
the entropy loss reaches a low and stable level, implying
that the UA V agents have largely optimized their actions.
The convergence of entropy loss to a lower and stable value
indicates that UA Vs have achieved a well-deﬁned policy.
Fig. 5 compares the convergence of accumulated reward and
energy consumption ratio under different learning rates and
discount factors. The convergence speed of the learning rate
4e4 is slightly faster than 3e4; however, its training process
exhibits larger ﬂuctuations and higher variance across multiple
runs. In contrast, 3e4 achieves optimal performance while
demonstrating stronger convergence stability. Discount factor
γ = 0.99 trades off short-term performance for improved
long-term outcomes, it learns more slowly in the early
stages but eventually achieves a higher and more stable ﬁnal
performance.
Fig. 6 illustrates the cache acquisition delay as the number
of users increases under different numbers of UA Vs. It can
be observed that a single UA V cannot handle large-scale
user requests, leading to unacceptable delay as user growth.
Deploying two UA Vs signiﬁcantly alleviates this bottleneck,
reducing the delay under the same load. Further increasing
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

HUA et al.: DDRL: A DUAL-PHASE DEEP REINFORCEMENT LEARNING APPROACH 14377
Fig. 6. Cache Acquisition Delay versus number of users under different
numbers of UA Vs.
the ﬂeet to three UA Vs continues to improve scalability but
with higher payment. These results highlight the effectiveness
of UA V cooperation, while also revealing diminishing returns
beyond a certain ﬂeet size.
We compare the convergence of DDRL with two primary
baselines: (i) CPPO: a DRL algorithm that integrates CNN
for feature extraction with standard PPO (DDRL without
GRU module); (ii) DCPPO [18]: a Dual-Clip Proximal Policy
Optimization-based (DCPPO) algorithm, when ˆAt < 0, the
new clip function of the DCPPO is expressed as
LDCPPOclip (θ) = 1|D|∑t∈Dmax(min(r(θ) ˆAt,
clip (r(θ), 1−ϵ, 1 +ϵ) ˆAt),c ˆAt) (38)
For fair comparison, we add our proposed PSO-based cache
replacement strategy for the two DRL baselines. The experi-
ments conduct a comparative analysis of CPPO and DCPPO
in terms of both cumulative reward and energy efﬁciency.
Fig. 4a shows the cumulative reward results, which demon-
strate the clear advantage of the proposed DDRL framework
over the baseline methods. DDRL consistently achieves
higher cumulative rewards throughout the training process
and converges more rapidly, typically stabilizing around 1500
episodes. In contrast, CPPO shows a steady improvement
in accumulated reward over time but does not reach the
same level of performance as DDRL, DCPPO underperforms
both DDRL and CPPO, with slower convergence and lower
cumulative reward, suggesting that the lack of spatial and
sequential dependency information limits its ability to adapt to
learn a more energy-efﬁcient scheduling strategy. The results
indicate that the proposed DDRL achieves a signiﬁcantly
higher cumulative reward compared to the baseline algorithms,
underscoring its superior performance by learning a more
optimal strategy that effectively maximizes long-term rewards.
Fig. 4b shows the energy consumption comparison results,
which further demonstrate the beneﬁts of DDRL’s design.
Over the training duration, DDRL maintains a consistently
lower energy consumption ratio compared to CPPO and
DCPPO, with noticeable stability after 1500 episodes. This is a
direct result of the GRU’s ability to model temporal dependen-
cies, which facilitates a more energy-aware scheduling strategy
and reduces redundant UA V movements, extending the overall
mission duration while maintaining service quality. On the
other hand, CPPO and DCPPO show higher energy usage due
to their lack of time-aware decision-making, leading to less
efﬁcient ﬂight paths.
Fig. 7 shows the optimized UA Vs trajectories for scenarios
with 16 users. In these experiments, two UA Vs were deployed
to serve users distributed across a target grid area in collab-
oration with three BSs. The red lines represent the path of
UA V 1, while the blue lines indicate the path of UA V 2.
The BSs locations are at coordinates [500,875], [125,125] and
[875,125]. Black dots indicate the positions of users and blue
triangles represent the positions of the BSs.
In Fig. 7a, we investigate a scenario where two UA Vs
provide content delivery services to 16 users. Each UA V
starts from its designated BS located at [500,875]. The
UA Vs begin their trajectories from the BS and adjust their
movements based on user locations and requests. The result
shows that UA Vs trajectories demonstrate a well-coordinated,
adaptive strategy that optimizes coverage of users which
can continuously to reduce energy consumption ratio and
minimize the total transmission delay. Once the UA Vs have
completed all the users’ requests, they each select the near-
est BS to return, with their ﬁnal locations marked by the
stars.
In Fig. 7b, we consider UA Vs start from the different BSs
in our multi-BS scenario. Speciﬁcally, one UA V starts from
[500, 875] and the other from [125, 125]. This setup reﬂects
a practical deployment strategy in the multi-BS environment
where UA Vs are assigned to different BSs. This experiment
highlights the advantages of a multi-BS deployment in improv-
ing coverage, reducing energy usage and enhancing service
efﬁciency in cache-enabled UA Vs networks.
In Fig. 8, we compare the content acquisition delay by
the CPPO and DCPPO algorithms. The cache acquisition
delay result demonstrates that DDRL maintains signiﬁcantly
lower latency compared to CPPO and DCPPO across varying
user densities. Moreover, the gap in content acquisition delay
between the proposed algorithm and the other two baselines
widens as the number of users increases. By capturing spatial
and time sequential information, DDRL can make a more
efﬁcient policy, achieving signiﬁcant reductions in content
delivery delay compared to baseline methods.
In Fig. 9, we examine how different UA Vs cache capacity
impact content acquisition delay under different users. The
result indicates that as the cache capacity of UA Vs increases,
the content acquisition delay decreases. As the number of users
increases, the total content acquisition delay rises across all
cache capacities due to a higher number of content requests.
At any given user count, a higher cache capacity results
in a lower content acquisition delay. When CU = 100M ,
content acquisition delay is signiﬁcantly lower compared to
when CU = 40M . This reduction is due to the larger cache
capacity, which allows more content to be stored locally on the
UA V . With a larger cache, the algorithm can store and replace
content more effectively, reducing the need to retrieve data
from the BSs, improving cache hit rate and thereby reducing
the average acquisition delay.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

14378 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Optimized UA V trajectory for a two-UA V and 16-user multi-BS system with different start locations.
Fig. 8. Comparison of content acquisition delay by different DRL algorithms.
Fig. 9. Comparison of content acquisition delay by our schemes for a two-
UA V system with different UA V capacity.
Fig. 10 explores the impact of UA V downlink link band-
width on content acquisition delay as the number of users
increases. Downlink link bandwidth is used to calculate the
transmission power through Shannon Capacity. Higher trans-
mission power generally results in lower content acquisition
Fig. 10. Comparison of content acquisition delay by our schemes for a two-
UA V system with different UA V transmission power.
delay, as greater power improves data transmission rates.
This trend highlights that higher transmission power enables
faster and more reliable content delivery, which is particularly
beneﬁcial in scenarios with high user demand. This analysis
underscores the importance of optimizing transmission power
in UA V systems to manage high user demand effectively,
ensuring reduced acquisition delay and improved service
quality.
C. Evaluation and Comparison With Baseline Algorithms
To illustrate the effectiveness of the proposed DDRL algo-
rithm, we evaluate four baseline approaches:
• DDRS [40]: An evaluation function with ﬁxed func-
tion parameters is presented to determine which content
should be cached, according to the evaluation values
for UA V using the DDQN-based Replacement Scheme
(DDRS).
• POP [15]: Content is cached based on its popularity, with
the least popular content being replaced to make space
for new items.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

HUA et al.: DDRL: A DUAL-PHASE DEEP REINFORCEMENT LEARNING APPROACH 14379
Fig. 11. Comparison of cache hit ratio by different schemes for a two-UA V
system.
Fig. 12. Comparison of content acquisition delay by different schemes for a
two-UA V system.
• LRU: A traditional caching replacement strategy where
the least recently accessed content is replaced when the
cache is full.
• RAN: Content is randomly selected for replacement,
with no prioritization based on relevance or frequency
of access.
Fig. 11 illustrates the cache access hit ratio across different
numbers of users ranging from 16 to 128 for ﬁve caching
schemes. Our proposed strategy consistently outperforms the
other methods across all user counts. The cache hit ratio grad-
ually decreases as the user base expands, but the overall trend
indicates that our proposed strategy is effective at maintaining
a high cache hit ratio. The DDRS and POP strategies show
relatively stable performance across all user counts, with cache
hit ratios remaining close to 0.6. The LRU and RAN schemes
show a noticeable drop in cache hit ratios as the number of
users increases.
Fig. 12 presents the cache acquisition delay under ﬁve
different caching schemes. In terms of cache acquisition delay,
our proposed approach outperforms all the baselines across
different user numbers. This is attributed to the optimization
of UA V path planning and caching strategy. Notably, the gap
between our method and the other methods widens as the
number of users increases. The baseline strategies, such as
RAN, show much higher delay, especially for larger user
Fig. 13. Comparison of content acquisition delay by different schemes for a
two-UA V system with different UA V capacity.
Fig. 14. Comparison of content acquisition delay by different schemes for a
two-UA V system with different UA V transmission power.
numbers, emphasizing the need for an intelligent cache place-
ment strategy. The proposed method effectively reduces cache
acquisition delay and enhances the system efﬁciency.
In Fig. 13, we compare content acquisition delay across
different caching schemes with varying cache capacities for
32 users. As UA V cache capacity increases from 40M to
100M, all caching schemes show a reduction in content
acquisition delay. The result indicates our scheme consistently
outperforms other schemes across all capacity levels. This
performance highlights the advantage of our caching strategy
in utilizing UA V storage to minimize delay under constrained
cache capacity. The improvement is especially noticeable
when cache capacity is limited, emphasizing the strategy’s
effectiveness in optimizing cache usage.
In Fig. 14, we analyze the impact of varying UA V downlink
link bandwidth on content acquisition delay for different
caching schemes for 32 users. As bandwidth increases from 8
to 14, content acquisition delay decreases across all schemes
and our proposed scheme demonstrates higher performance.
This improvement is particularly pronounced at lower trans-
mission power levels, where efﬁcient caching signiﬁcantly
reduces the need for additional data retrieval. This suggests
that our proposed method effectively leverages both cache
management and transmission power, providing a robust solu-
tion for minimizing delay under varying power conditions.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

14380 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
VI. C ONCLUSION
In this paper, we present a novel Dual-phase Deep Rein-
forcement Learning (DDRL) framework for UA V-assisted
content delivery in multi-BS networks. By jointly optimizing
UA V trajectories, caching strategies, and transmission power,
the DDRL framework effectively reduces content acquisition
delay, enhances cache hit rate, and conserves UA V energy.
The integration of Particle Swarm Optimization (PSO) further
reﬁnes the caching strategy, enabling adaptive and efﬁcient
content management. Extensive simulation results conﬁrm that
our proposed framework enhances the cache hit rate, reduces
the total content acquisition delay, and conserves UA V energy.
While the current framework achieves promising results
under controlled simulation settings, extending it to real-
world scenarios introduces several challenges. The most
notable one is dynamic user mobility, which can disrupt
pre-optimized UA V trajectories and reduce cache efﬁciency
in both urban (frequent commuting) and rural (randomly
distributed) environments. In addition, real deployments must
address environmental interference and the lack of large-scale,
scenario-speciﬁc datasets. Future work will therefore focus
on integrating realistic mobility models, developing robust
optimization mechanisms, and validating the framework under
diverse real-world conditions.
REFERENCES
[1] R. Amer, W. Saad, and N. Marchetti, “Mobility in the sky: Performance
and mobility analysis for cellular-connected UA Vs,” IEEE Trans. Com-
mun., vol. 68, no. 5, pp. 3229–3246, May 2020.
[2] X. Li, L. Chen, Z. Yuan, and G. Liu, “AIHO: Enhancing task ofﬂoading
and reducing latency in serverless multi-edge-to-cloud systems,” Future
Gener. Comput. Syst., vol. 165, Apr. 2025, Art. no. 107607.
[3] N. Cheng et al., “AI for UA V-assisted IoT applications: A comprehensive
review,” IEEE Internet Things J., vol. 10, no. 16, pp. 14438–14461,
Aug. 2023.
[4] M. Chen, M. Mozaffari, W. Saad, C. Yin, M. Debbah, and C. S. Hong,
“Caching in the sky: Proactive deployment of cache-enabled unmanned
aerial vehicles for optimized quality-of-experience,” IEEE J. Sel. Areas
Commun., vol. 35, no. 5, pp. 1046–1061, May 2017.
[5] L. Zhang and J. Chakareski, “UA V-assisted edge computing and
streaming for wireless virtual reality: Analysis, algorithm design, and
performance guarantees,” IEEE Trans. Veh. Technol., vol. 71, no. 3,
pp. 3267–3275, Mar. 2022.
[6] Y . Li, C. Dou, Y . Wu, W. Jia, and R. Lu, “NOMA assisted two-tier
VR content transmission: A tile-based approach for QoE optimization,”
IEEE Trans. Mobile Comput., vol. 23, no. 5, pp. 3769–3784, May 2024.
[7] J. Lyu, Y . Zeng, and R. Zhang, “UA V-aided ofﬂoading for cellular
hotspot,” IEEE Trans. Wireless Commun., vol. 17, no. 6, pp. 3988–4001,
Jun. 2018.
[8] Z. Liao, Y . Ma, J. Huang, J. Wang, and J. Wang, “HOTSPOT: A UA V-
assisted dynamic mobility-aware ofﬂoading for mobile-edge computing
in 3-D space,” IEEE Internet Things J., vol. 8, no. 13, pp. 10940–10952,
Jul. 2021.
[9] G. Liu, X. Zhu, L. Chen, and X. Li, “HMUR: A two-stage heuristic
for UA V scheduling in mobile edge computing with time window
constraints,” in Proc. IEEE Int. Conf. Web Services (ICWS), Jul. 2024,
pp. 1400–1402.
[10] Y . Zeng, R. Zhang, and T. J. Lim, “Throughput maximization for
UA V-enabled mobile relaying systems,”IEEE Trans. Commun., vol. 64,
no. 12, pp. 4983–4996, Dec. 2016.
[11] M. Mozaffari, W. Saad, M. Bennis, and M. Debbah, “Mobile
unmanned aerial vehicles (UA Vs) for energy-efﬁcient Internet of Things
communications,” IEEE Trans. Wireless Commun., vol. 16, no. 11,
pp. 7574–7589, Nov. 2017.
[12] J. Lyu, Y . Zeng, R. Zhang, and T. J. Lim, “Placement optimization
of UA V-mounted mobile base stations,” IEEE Commun. Lett., vol. 21,
no. 3, pp. 604–607, Mar. 2017.
[13] L. Zhang, A. Celik, S. Dang, and B. Shihada, “Energy-efﬁcient trajectory
optimization for UA V-assisted IoT networks,” IEEE Trans. Mobile
Comput., vol. 21, no. 12, pp. 4323–4337, Dec. 2022.
[14] K. K. Nguyen, T. Q. Duong, T. Do-Duy, H. Claussen, and L. Hanzo, “3D
UA V trajectory and data collection optimisation via deep reinforcement
learning,” IEEE Trans. Commun., vol. 70, no. 4, pp. 2358–2371, Apr.
2022.
[15] A. Al-Hilo, M. Samir, C. Assi, S. Sharafeddine, and D. Ebrahimi,
“UA V-assisted content delivery in intelligent transportation systems-joint
trajectory planning and cache management,” IEEE Trans. Intell. Transp.
Syst., vol. 22, no. 8, pp. 5155–5167, Aug. 2021.
[16] C. Fan, X. Zhou, T. Zhang, W. Yi, and Y . Liu, “Cache-enabled
UA V emergency communication networks: Performance analysis with
stochastic geometry,” IEEE Trans. Veh. Technol., vol. 72, no. 7,
pp. 9308–9321, Jul. 2023.
[17] T. Zhang, Y . Wang, Y . Liu, W. Xu, and A. Nallanathan, “Cache-enabling
UA V communications: Network deployment and resource allocation,”
IEEE Trans. Wireless Commun., vol. 19, no. 11, pp. 7470–7483, Nov.
2020.
[18] J. Ji, K. Zhu, and L. Cai, “Trajectory and communication design for
cache{-} enabled UA Vs in cellular networks: A deep reinforcement
learning approach,” IEEE Trans. Mobile Comput., vol. 22, no. 10,
pp. 6190–6204, Oct. 2023.
[19] M. Zhang, E.-H. Mohammed, and S. X. Ng, “Intelligent caching in UA V-
aided networks,” IEEE Trans. Veh. Technol., vol. 71, no. 1, pp. 739–752,
Jan. 2022.
[20] H. Wu, F. Lyu, C. Zhou, J. Chen, L. Wang, and X. Shen, “Optimal
UA V caching and trajectory in aerial-assisted vehicular networks: A
learning-based approach,” IEEE J. Sel. Areas Commun., vol. 38, no. 12,
pp. 2783–2797, Dec. 2020.
[21] Z. Su, M. Dai, Q. Xu, R. Li, and H. Zhang, “UA V enabled
content distribution for Internet of Connected Vehicles in 5G hetero-
geneous networks,” IEEE Trans. Intell. Transp. Syst., vol. 22, no. 8,
pp. 5091–5102, Aug. 2021.
[22] T. C. Lam, N.-S. V o, M.-P. Bui, C. D. T. Thai, H. Jung, and V .-C. Phan,
“Service time-aware caching, power allocation, and 3D trajectory opti-
mised multimedia content delivery in UA V-assisted IoT networks,”IEEE
Trans. Veh. Technol., vol. 74, no. 4, pp. 6419–6432, Apr. 2025.
[23] L. Zhou, Y . Dong, M. Hong, and Q. Shi, “Joint channel assignment
and power allocation for multi-UA Vs communication systems,” in
Proc. IEEE 21st Int. Workshop Signal Process. Adv. Wireless Commun.
(SPAWC), May 2020, pp. 1–5.
[24] R. Li et al., “Joint trajectory and resource allocation design for UA V
communication systems,” in Proc. IEEE Globecom Workshops (GC
Wkshps), Dec. 2018, pp. 1–6.
[25] L. Zhou, X. Chen, M. Hong, S. Jin, and Q. Shi, “Efﬁcient resource
allocation for multi-UA V communication against adjacent and co-
channel interference,” IEEE Trans. Veh. Technol., vol. 70, no. 10,
pp. 10222–10235, Oct. 2021.
[26] M. Cui, G. Zhang, Q. Wu, and D. W. K. Ng, “Robust trajectory and
transmit power design for secure UA V communications,” IEEE Trans.
Veh. Technol., vol. 67, no. 9, pp. 9042–9046, Sep. 2018.
[27] J. Ji, K. Zhu, D. Niyato, and R. Wang, “Joint cache placement, ﬂight
trajectory, and transmission power optimization for multi-UA V assisted
wireless networks,” IEEE Trans. Wireless Commun., vol. 19, no. 8,
pp. 5389–5403, Aug. 2020.
[28] L. Breslau, P. Cao, L. Fan, G. Phillips, and S. Shenker, “Web caching and
zipf-like distributions: Evidence and implications,” in Proc. 18th Annu.
Joint Conf. IEEE Comput. Commun. Societies. Future Now , vol. 1, Oct.
1999, pp. 126–134.
[29] M. Mozaffari, W. Saad, M. Bennis, Y .-H. Nam, and M. Debbah, “A tuto-
rial on UA Vs for wireless networks: Applications, challenges, and open
problems,” IEEE Commun. Surv. Tut., vol. 21, no. 3, pp. 2334–2360,
3rd Quart., 2019.
[30] Q. Feng, J. McGeehan, E. K. Tameh, and A. R. Nix, “Path loss models
for air-to-ground radio channels in urban environments,” in Proc. IEEE
63rd Veh. Technol. Conf., vol. 6, Jul. 2006, pp. 2901–2905.
[31] M. Mozaffari, W. Saad, M. Bennis, and M. Debbah, “Unmanned
aerial vehicle with underlaid device-to-device communications: Perfor-
mance and tradeoffs,” IEEE Trans. Wireless Commun., vol. 15, no. 6,
pp. 3949–3963, Jun. 2016.
[32] A. Al-Hourani, S. Kandeepan, and A. Jamalipour, “Modeling air-to-
ground path loss for low altitude platforms in urban environments,” in
Proc. IEEE Global Commun. Conf., Dec. 2014, pp. 2898–2904.
[33] B. Bellalta, “IEEE 802.11ax: High-efﬁciency WLANS,” IEEE Wireless
Commun., vol. 23, no. 1, pp. 38–46, Feb. 2016.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

HUA et al.: DDRL: A DUAL-PHASE DEEP REINFORCEMENT LEARNING APPROACH 14381
[34] Y . Zeng, X. Xu, and R. Zhang, “Trajectory design for completion
time minimization in UA V-enabled multicasting,” IEEE Trans. Wireless
Commun., vol. 17, no. 4, pp. 2233–2246, Apr. 2018.
[35] H. Wang, C. H. Liu, H. Yang, G. Wang, and K. K. Leung, “Ensuring
threshold AoI for UA V-assisted mobile crowdsensing by multi-agent
deep reinforcement learning with transformer,” IEEE/ACM Trans. Netw.,
vol. 32, no. 1, pp. 566–581, Feb. 2024.
[36] J. Schulman, F. Wolski, P. Dhariwal, A. Radford, and O. Klimov,
“Proximal policy optimization algorithms,” 2017, arXiv:1707.06347.
[37] T. Zhang et al., “BeBold: Exploration beyond the boundary of explored
regions,” 2020, arXiv:2012.08621.
[38] Z. Dai, C. H. Liu, R. Han, G. Wang, K. K. Leung, and J. Tang, “Delay-
sensitive energy-efﬁcient UA V crowdsensing by deep reinforcement
learning,” IEEE Trans. Mobile Comput., vol. 22, no. 4, pp. 2038–2052,
Apr. 2023.
[39] X. Li, J. Shen, Y . Sun, Z. Wang, and X. Zheng, “A smart content caching
and replacement scheme for UA V-assisted fog computing network,” in
Proc. Int. Conf. Wireless Commun. Signal Process. (WCSP), Oct. 2020,
pp. 1040–1045.
[40] Y . Liu, C. Yang, X. Chen, and F. Wu, “Joint hybrid caching and replace-
ment scheme for UA V-assisted vehicular edge computing networks,”
IEEE Trans. Intell. Vehicles, vol. 9, no. 1, pp. 866–878, Jan. 2024.
Xinshuai Hua is currently pursuing the M.S. degree
with the School of Computer Science and Engineer-
ing, Southeast University, Nanjing, China. His main
research interests include edge computing and UA V
wireless communications.
Long Chen received the B.Sc. and Ph.D. degrees in
computer science and engineering from Southeast
University, Nanjing, China, in 2009 and 2018,
respectively. He is currently with the School of
Computer Science and Engineering, Southeast Uni-
versity. He has published more than 30 papers in
international journals and conferences, such as IEEE
TRANSACTIONS ON SERVICES COMPUTING , IEEE
TRANSACTIONS ON CLOUD COMPUTING , and
IEEE T RANSACTIONS ON AUTOMATION SCIENCE
AND ENGINEERING . His main research interests
include cloud computing, edge computing, and service-oriented computing.
Xia Zhu received the B.Sc., M.Sc., and Ph.D.
degrees from the School of Computer Science and
Engineering, Southeast University, Nanjing, China,
in 2004, 2006, and 2009, respectively. She is cur-
rently an Associate Professor with the School of
Computer Science and Engineering, Southeast Uni-
versity. She is the author or co-author over more
than 30 academic papers, some of which have been
published in international journals and conferences,
such as ICWS, European Journal of Operational
Research, Omega, Integrated Computer-Aided Engi-
neering, Computers & Industrial Engineering , International Journal of
Production Research, International Journal of Computer Integrated Manufac-
turing, Information Sciences, SMC, CASE, and CSCW. Her research interests
include scheduling in cloud computing, service computing, big data, and
machine learning.
Xiaoping Li (Senior Member, IEEE) received the
B.Sc. and M.Sc. degrees in applied computer science
from Harbin University of Science and Technology
in 1993 and 1999, respectively, and the Ph.D. degree
in applied computer Science from Harbin Institute
of Technology in 2002. He was a Distinguished
Professor with the School of Computer Science and
Engineering, Southeast University, Nanjing, China.
He is currently a Full Professor and the Dean of
the School of Computer Science and Technology,
Guangdong University of Technology, Guangzhou,
China. He is the author or co-author over more than 100 academic papers,
some of which have been published in international journals, such as IEEE
TRANSACTIONS ON COMPUTERS , IEEE T RANSACTIONS ON PARALLEL
AND DISTRIBUTED SYSTEMS , IEEE T RANSACTIONS ON SERVICES COM-
PUTING , IEEE T RANSACTIONS ON CYBERNETICS , IEEE T RANSACTIONS
ON AUTOMATION SCIENCE AND ENGINEERING , IEEE T RANSACTIONS
ON CLOUD COMPUTING , IEEE T RANSACTIONS ON SYSTEMS , M AN AND
CYBERNETICS : S YSTEMS , Information Sciences, Omega, European Journal
of Operational Research, International Journal of Production Research,
Expert Systems with Applications, and Journal of Network and Computer
Applications. His research interests include scheduling in cloud computing,
scheduling in cloud manufacturing, service computing, big data, and machine
learning.
Jingjing Li received the M.S. degree from the
College of Engineering, The Pennsylvania State
University, PA, USA, in 2025. She is currently
pursuing the Ph.D. degree with the Bellini College of
Artiﬁcial Intelligence, Cybersecurity, and Comput-
ing, University of South Florida. Her main research
interests include deep reinforcement learning and
human–robot interaction.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:08:35 UTC from IEEE Xplore.  Restrictions apply.
