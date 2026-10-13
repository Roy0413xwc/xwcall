---
title: "Memory-Enhanced Dynamic Self-Attention Communication Mechanism for Multi-UAV Base Stations Trajectory Planning"
zotero_key: "SW4GRDN9"
pdf_key: "Z9T3IEVU"
collection: "UAV"
source: "User-provided PDF (pypdf extraction)"
page_mapping: unverified
---

# Memory-Enhanced Dynamic Self-Attention Communication Mechanism for Multi-UAV Base Stations Trajectory Planning — Fulltext

> 由用户提供的 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

9758 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Memory-Enhanced Dynamic Self-Attention
Communication Mechanism for Multi-UA V
Base Stations Trajectory Planning
Hanxiao Yuan
 , Yao Shi
 , Member , IEEE, Emad Alsusa
 , Senior Member , IEEE,
Qinyu Zhang
 , Senior Member , IEEE, Yiping Duan
 , Senior Member , IEEE, and Xiaohu You
 , Fellow, IEEE
Abstract—In large-scale temporary event scenarios, Uncrewed
Aerial Vehicle base stations (UA V-BSs) provide ﬂexible, on-
demand wireless coverage to meet rapidly growing user demands.
However, dynamic crowd movements and unpredictable user
behaviors lead to highly uncertain environments. The absence of
prior knowledge on user distribution, interference, and network
load, coupled with UA Vs’ limited sensing capabilities, makes
real-time trajectory planning especially challenging. Although
reinforcement learning has shown potential in these scenarios,
many existing approaches remain limited. They often make
decisions based on instantaneous local observations or rely
on unavailable centralized training information in a practi-
cal environment, limiting their adaptability and scalability. To
address these limitations, we propose Mem-DSACM (Memory-
Enhanced Dynamic Self-Attention Communication Mechanism),
a lightweight reinforcement learning framework that integrates
memory-assisted temporal reasoning with distance-constrained
decentralized communication. In Mem-DSACM, the exchanged
data, including relative distances and communication loads,
is combined with historical observations and processed by a
memory-based temporal reasoning module using a Transformer
decoder. This enables context-aware and predictive decision-
making under decentralized conditions. The simulation results
demonstrate that the proposed method improves the system rate
by 12.8%, the cumulative satisfaction 8.0% and the algorithm
reduces the training time by 6.3% compared to the best baselines
approaches, demonstrating superior performance in dynamic
urban scenarios.
Index Terms—UA V base station, trajectory planning, memory,
Transformer.
Received 8 June 2025; revised 21 October 2025, 20 December
2025, and 7 March 2026; accepted 11 May 2026. Date of publica-
tion 1 June 2026; date of current version 15 June 2026. This work
is supported by National Natural Science Foundation of China (Grant
No. 62531012 and 62201174), Shenzhen Science and Technology Pro-
gram (Grant No. GXWD20231129134340001) and Shenzhen Low-Altitude
Airspace Strategic Program Portfolio (Grant No. Z25306108). The associate
editor coordinating the review of this article and approving it for publication
was N. Mokari. (Corresponding author: Yao Shi.)
Hanxiao Yuan, Yao Shi, and Qinyu Zhang are with Guangdong Provincial
Key Laboratory of Aerospace Communication and Networking Technol-
ogy, Harbin Institute of Technology, Shenzhen 518055, China (e-mail:
shiyao@hit.edu.cn).
Emad Alsusa is with the Department of Electrical and Electronic Engineer-
ing, The University of Manchester, M13 9PL Manchester, U.K.
Yiping Duan is with the Department of Electronic Engineering, Tsinghua
University, Beijing 100084, China.
Xiaohu You is with the National Mobile Communications Research Labo-
ratory, Southeast University, Nanjing 210096, China.
Digital Object Identiﬁer 10.1109/TCOMM.2026.3698915
I. I NTRODUCTION
U
NCREWED aerial vehicle (UA V) technology have
emerged as a versatile technology with transformative
potential across a wide range of applications, including intel-
ligent logistics, trafﬁc monitoring, emergency response, and
environmental sensing [1], [2], [3], [4], [5]. In wireless com-
munications, UA Vs can serve as aerial base stations [6], [7],
user terminals [8], or relay nodes [9], [10], enabling ﬂexible
and rapid deployment in areas with limited infrastructure or
sudden in demand. Among these roles, UA V base stations
(UA V-BSs) have garnered increasing interest due to their
mobility and adaptability, which allow dynamic placement,
reduced signal blockage, and improved coverage in urban
environments.
UA V-BSs can deliver on-demand coverage at large tempo-
rary events, yet trajectory planning is highly challenging due to
rapidly changing demand and limited prior knowledge—such
as user distributions, interference patterns, and network
load. As a result, UA Vs must operate in partially observ-
able and uncertain environments, where relying solely on
instantaneous observations leads to suboptimal decision mak-
ing. In such cases, the ability to retain and utilize past
information—memory—is crucial for making informed and
adaptive trajectory planning decisions.
Traditional UA V trajectory optimization methods, such as
exhaustive search [11], dynamic programming [12], convex
optimization [13], [14], [15], [16], and heuristic methods [17],
[18], have focused on improving coverage, energy efﬁciency,
and service quality. While effective in static settings, these
methods struggle in dynamic, fast-changing environments due
to limited adaptability and high computational costs. Recent
research in deep reinforcement learning (DRL) has signiﬁ-
cantly expanded their applications in UA V trajectory planning.
Many studies have employed advanced architectures, such
as deep Q-networks [19], [20], and sophisticated algorithms
[21], [22], [23] to optimize UA V trajectory and resource
allocation on user behavior jointly. However, single-UA V
systems are inherently limited by their local sensing range and
computational capacity, leading to incomplete environmental
observations and delayed reactions to sudden changes in user
demand.
Multi-Agent Deep Reinforcement Learning (MARL) [24],
[25] has emerged as a promising framework for enabling
0090-6778 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

YUAN et al.: MEMORY-ENHANCED DYNAMIC SELF-ATTENTION COMMUNICATION MECHANISM 9759
distributed decision-making among multiple UA Vs. By allow-
ing UA Vs to coordinate and jointly optimize their trajectories
[26], [27], MARL enhances system-level adaptability in
dynamic environments. Recent studies have highlighted the
importance of UA V trajectory optimization using memory-
enhanced multi-agent reinforcement learning [28], [29].
However, most approaches adopt a centralized training with
decentralized execution (CTDE; training uses a centralized
critic or joint information, whereas execution relies on each
agent’s local observations and its own policy only), which
depends on centralized critics or globally shared knowl-
edge during training. Such assumptions are often impractical
in bandwidth-limited, rapidly changing UA V network envi-
ronments. Moreover, real-world deployments face additional
challenges such as imperfect CSI caused by estimation errors
and feedback delays, noisy sensing of user positions and
environmental features, and constrained inter-UA V communi-
cation. These factors collectively induce partial observability,
making it difﬁcult for each UA V to access globally accurate
and timely network states.
To enhance cooperation under decentralized conditions,
several MARL algorithms have incorporated inter-UA V com-
munication mechanisms, allowing agents to exchange local
observations or learned policies. Early works employed sim-
ple message passing or broadcasting, but these approaches
suffer from rapidly growing communication overhead as
the number of agents increases. Subsequent research intro-
duced Graph Neural Network (GNN)-based methods such
as Deep Graph Network(DGN) [30], Target-driven Multi-
Agent Communication(TarMAC) [31], which allow UA Vs to
exchange local observations or learned policies. However,
these methods typically rely on learned attention weights or
implicit graph construction [28], [32], [33], [34], [35], often
overlooking physical constraints such as spatial proximity
and communication capacity [36]. This can result in dense
or unconstrained communication graphs that are difﬁcult to
realize in practical deployments. When physical communica-
tion ranges are limited, coordination is constrained to local
neighborhoods and the resulting interaction graph may become
sparse or fragmented, reducing the efﬁciency of global infor-
mation propagation. This motivates the need for a design that
(i) enforces physically feasible, distance-aware sparse interac-
tions, (ii) keeps the communication structure controllable and
scalable, and (iii) complements local exchange with temporal
memory.
Meanwhile, Transformer-based architectures [37], [38], [39]
have gained increasing attention in reinforcement learning.
These methods leverage self-attention mechanisms to model
long-range dependencies in sequential data and have demon-
strated strong performance in RL tasks. For instance, MAT
(Multi-Agent Transformer) [40] applies Transformers to multi-
agent trajectory prediction. However, these works are built on
ofﬂine RL datasets and depend on supervised settings rather
than interactive training, which limits their effectiveness in
real-time online decision-making scenarios. Without accurate
and up-to-date environmental information, decision-making
remains reactive and suboptimal. Furthermore, existing works
often focus solely on temporal modeling, neglecting the
crucial synergy between communication and memory in
online settings—speciﬁcally, how selective communication
can acquire critical information while historical memory com-
pensates for incomplete information.
Motivated by these challenges, we propose Mem-DSACM,
a lightweight learning framework that integrates decentralized
communication with memory-enhanced temporal reasoning
to support decision-making in dynamic, partially observable
environments. At the core of this framework lies a Spa-
tially Proximate Communication Embedding (SPaCE) module,
which constructs a physically grounded, distance-aware inter-
action relationship among UA Vs. Rather than relying on
learned attention weights or global broadcasting, SPaCE lever-
ages explicit spatial constraints—based on Euclidean proxim-
ity, to deﬁne sparse, interpretable communication pathways.
This design signiﬁcantly reduces information redundancy
and computational overhead, while enhancing scalability and
deployment readiness in dynamic, partially observable envi-
ronments. Furthermore, a memory-based temporal reasoning
module, which leverages a Transformer decoder, is applied to
model long-term dependencies across historical observations.
This module supports context-aware decision making and
improving predictive accuracy in dynamic and uncertain envi-
ronments. This design allows UA Vs to make more informed
and anticipatory decisions based on accumulated experience,
rather than relying solely on instantaneous feedback. Two
practical considerations are also highlighted. First, SPaCE may
be suboptimal when long-range coordination is required. How-
ever, in the considered UA V-assisted network, the difference
from the optimal performance may be limited. This is because
distant agents are typically weakly coupled to immediate
local decisions, and any missing long-range context can be
compensated over time via the Transformer-based memory and
evolving neighborhoods created by UA V mobility. Second, the
Transformer decoder incurs computation that grows with the
history length; therefore, the history window is selected to
balance performance and efﬁciency.
The remainder of this paper is structured as follows: Sec-
tion II presents the system model and problem formulation.
Section III reformulates the trajectory optimization task as a
Partially Observable Markov Process. Section IV introduces
a Transformer-based algorithm for trajectory planning. Sec-
tion V introduce the time complexity analysis and convergence
analysis. Section VI details the experimental setup and reports
the simulation results. Finally, Section VII summarizes this
work.
II. S YSTEM MODEL AND ASSUMPTION
A. System Model
To support realistic trajectory planning, the communication
system considered UA V base stations, ground base stations
(GBS), and mobile user terminals (UT), as illustrated in
Fig. 1. The indices of UA V-BS and GBS are denoted by
I ={1,...,I },U ={1,...,U }, respectively. The UT index
set is denoted by N ={1,...,N }. The entire duration of
serviceT is evenly discretized into Nt time periods of length
∆t = TNt . Within each period, UA Vs provide continuous
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

9760 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 1. System model.
communication coverage to UTs. Trajectory decisions are
made at period boundaries based on observations collected
during the preceding period, and the updated trajectory is
applied throughout the following period. Decision-making and
coordination between UA V are carried out within each period
and designed to be much smaller than ∆t under the con-
ﬁguration considered. Nevertheless, range-limited information
exchange may affect coordination quality and timeliness.
Each UA V is assumed to lack prior knowledge of UTs’
geographical positions. Each UA V observes only local users,
buildings, base stations, and neighboring UA Vs with its sens-
ing or communication range, and does not access to the
global user distribution, or the full network load. Although
imperfect CSI, sensing errors, and feedback delays are not
explicitly modeled at the physical layer, their decision-level
effect is consistent with the partial observability considered
in this work. Coverage is provided by both aerial and terres-
trial BSs using the Orthogonal Frequency Division Multiple
Access (OFDMA) protocol. The spectral resources are allo-
cated in units of Resource Blocks (RB), each deﬁned as a
cluster of subcarriers in the frequency domain paired with a
ﬁxed time duration. The system operates under the constraint
of the maximum available RBs M. In addition, efﬁcient
resource management and collaboration are enabled through
the exchange of information between UA Vs.
B. Geometric LoS Model (Sampling-Based)
Line-of-sight (LoS) conditions are critical in communi-
cation systems as they signiﬁcantly impact signal quality,
propagation reliability, and overall network performance. To
accurately determine LoS conditions, we use a geometric
LoS model [41] to assess the impact of buildings on the
signal transmission path. Let the UT and UA V positions be
pUT = (xUT,y UT, zUT) and pUA V = (xUA V,y UA V, zUA V),
and let B = ⋃kBk denote the union of known building
volumes. Probe the line segment pUTpUA V at N′ = 100
uniformly spaced points (including endpoints):
p(si) = pUT + iN ′−1(pUA V− pUT), i = 0, 1,...,N ′− 1.
(1)
Then the LoS indicator is deﬁned as
⊮LoS(pUT, pUA V) =
{
1, p(si) /∈B, ∀i,
0, otherwise. (2)
The probe spacing is set to d/(N′− 1) where d =‖pUA V−
pUT‖, providing sufﬁcient granularity for our maps, in which
typical building extents along the link direction are well
represented. This model performs deterministic geometric
LoS/NLoS labeling based on building geometry and does not
account for Fresnel-zone clearance or diffraction.
C. Channel Model
For the ground base station communication link, the path
loss LGBS(d) is given by:
LGBS(d) = 20 log
( 4π
λGBS
)
+ 10α log(d) +χGBS (3)
where LGBS(d) represents the path loss for the link, d is the
distance between the GBS and UT. λGBS is the GBS carrier
wavelength,α denotes the GBS path loss exponent, and χGBS
accounts for GBS log-normal shadowing.
For UA V base stations, the path loss LUA V(d) is modeled
as:
LUA V(d)
=



20 log
( 4π
λUA V
)
+ 10αL log(d) +χL, if LoS,
20 log
( 4π
λUA V
)
+ 10αN log(d) +χN, otherwise.
(4)
where LUA V(d) represents the path loss between UA Vs and
ground users, λUA V is the UA V carrier wavelength, αL and
αN are the path loss exponents for LoS and NLoS conditions,
respectively. The terms χL and χN account for log-normal
shadowing in LoS and NLoS scenarios. This model is tailored
to capture the unique propagation characteristics of commu-
nication for UA V base stations, where LoS availability and
path loss characteristics vary signiﬁcantly with altitude and
movement.
D. Communication Model
When base station k, which includes UA V-BS and GBS,
communicates with user n over RB m in time interval t, the
achievable rate of the user n can be expressed as
Rn[t] =
K∑
k=1
M∑
m=1
xkn,m[t]γkn,m[t]· ∆t (5)
where
γkn,m [t] = B log2

1 + pk[t]gkn,m[t]∑
i=k
pk[t]gin,m[t] +σ2

 (6)
Here,pk[t] represents the transmission power of base stationk,
with both UA V-BSs and GBSs assumed to have ﬁxed transmit
powers.gkn,m[t] denotes the channel gain between base station
k and UT n over RB m. The Doppler shift caused by the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

YUAN et al.: MEMORY-ENHANCED DYNAMIC SELF-ATTENTION COMMUNICATION MECHANISM 9761
UA V’s movement is assumed to be ideally compensated at
the receivers, ensuring stable communication. ∆t is the time
interval length. Furthermore, σ2 = N 0B is the variance of
AWGN, where N 0 refers to the power of noise, and B is the
sub-channel bandwidth. M is the maximum resource block
number. K is the total number of UA V base stations and
ground base stations. A group of binary variables, denoted
as xkn,m[t] is deﬁned, where xkn,m[t] = 1 denotes the user
is served by base station k in time interval t, otherwise,
xkn,m[t] = 0. The satisfaction rate of UTS is deﬁned as:
S[t] = 1N
N∑
n=1
I{Rn[t]≥ρn[t]} (7)
where ρn[t] is the demand rate of user n, and I{·} is the
indicator function.
E. Problem F ormulation
The optimization objective is to maximize a composite
utility that jointly considers the system data rate and user
satisfaction. The goal can be achieved by optimizing the UA V-
UT and GBS-UT association pair H ={xkn,m[t],∀n,m,k,t },
and the UA V trajectory P ={pUA V[i,t ],∀i,t}.
max
H,P
Υ =
T∑
t=0
(
λ1
1
N
N∑
n=1
Rn[t] +λ2S[t]
)
(8a)
s.t.
K∑
k=1
M∑
m=1
xkn,m[t]≤ 1, ∀n,t (8b)
vi[t]∈V, ∀i,t (8c)
ψi[t]∈ Ψ, ∀i,t (8d)
hi[t] =hmax, ∀i,t (8e)
‖pi[t]− pj[t]‖≥ dmax, ∀i⁄=j,t (8f)
The optimization problem is formulated in (8), which
consists of the objective function (8a) and the constraints
(8b)–(8f). Speciﬁcally, (8a) represents a weighted sum of the
system average rate and the user satisfaction rate, whereλ1 and
λ2 are the corresponding weighting factors. Constraint (8b)
restricts a UT to communicate with only one base station using
a ﬁxed number of RBs. Constraint (8c) limits the available
velocity of UA Vs to the set V . Constraint (8d) restricts the
available directions of the UA Vs to the set Ψ. Constraint (8e)
ﬁxes the ﬂight altitude of each UA V athmax for all time steps.
Finally, Constraint (8f) enforces a minimum UA V distance
dmax between UA Vs at every time step, thereby preventing
collisions and maintaining spatial safety.
The UA V-UT and GBS-UT association pair H is dynam-
ically conﬁgured through Channel Quality Indicator (CQI)
[42] reported by UTs. The CQI report contains the Signal-to-
Interference-Plus-Noise Ratio γkn,m [t] for each RB. The base
stations leverage these CQI reports to determine the preferred
RBs for each UT. This study employs a greedy resource
allocation algorithm [43], which is particularly suitable for
scenarios where computational resources are limited and quick
decisions are required. Since trajectory optimization P is a
real-time decision problem, traditional convex optimization
algorithms are ill-suited for solving it. We convert it into a
POMDP and present our solution.
III. P ARTIALLY OBSERVABLE MARKOV
DECISION PROCESS
In real-world scenarios, UA V-BSs cannot acquire complete
state information. Their observations are limited by sensing
range, communication range, and the absence of user mobility
and trafﬁc demand. Therefore, the trajectory planning problem
is naturally modeled as a POMDP, which can be formally
decribed as (S,A,T,R, Ω,O). The UA Vs act as agents and
learn their optimal trajectory policies without access to the full
state. Here,S is the set of environment states, A is the action
set, Ω is the observation space, T (s,a,s′) = P (s′|s,a ) is
the transition model, denoted the probability of transitioning
from state s to state s′ given action a.R :S×A→ R is
the reward function, and O(s′,a,o ) = P (o| s′,a ) is the
observation model with o∈ Ω.
At each time step t, the unobserved state st∈ S evolves
according to T . The UA Vs receive an observation ot ∈ Ω,
takes action at ∈ A, and obtains an immediate reward
rt = R, with the aim of maximize the expected cumu-
lative discounted reward. Due to the environment’s partial
observability, the UA V cannot access the system’s complete
state information. Consequently, it must rely on its history
of observations ot:t+k ={ot,ot+1,...,o t+k−1} and actions
at:t+k ={at,at+1,...,a t+k−1} to make informed decisions.
The speciﬁc information will be detailed in the following
subsections.
A. Observation
In this module, each UA V node i has an observation that
includes its self-state and observations of the surrounding
environment within speciﬁed observation ranges:
oi[t] =
[
oselfi [t],o BSi [t],o Useri [t],o Buildingi [t]] (9)
where each component is deﬁned as follows:
Self: Captures the UA V’s own properties oselfi [t], which
includes position pi[t] = ( xi[t],yi[t], zi[t]), representing the
3D spatial coordinates and current communication load li[t]∈
[0,l max] at time step t, where li[t] denotes the number of
users currently served by UA Vi, normalized by the maximum
allowable load lmax. Thus, oselfi [t] can be expressed as:
oselfi [t] = [xi[t],yi[t], zi[t],li[t]] (10)
Base-Stations: The observation feature for ground base
stations, represented as oBSi [t], encodes information of nearby
base stations b∈U that are within UA Vi’s observation range
RGi at time step t. This feature includes the relative distance
dib[t] = ‖pi[t]−pb[t]‖ between UA Vi and base station b,
and the communication load lb[t] of base station b, where li[t]
denotes the number of users currently served by BS b at time
stept. Thus, the observation features for ground base stations
are:
oBSi [t] ={(dib[t],lb[t])⏐⏐b∈U , dib[t]≤RGi} (11)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

9762 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Users: For ground users, the observation feature oUseri [t]
includes details about users u∈N within the general obser-
vation range RGi . This feature captures the relative distance
diu[t] = ‖pi[t]−pu[t]‖ between UA Vi and user u at time
stept, the data rate requirement Ru[t] of user u. Together, the
observation features for ground users are:
oUseri [t] ={(diu[t],Ru[t],)⏐⏐u∈N ,diu[t]≤RGi } (12)
Buildings: The features oBuildingi [t] represents the charac-
teristics of buildings g ∈ Gthat are within the range RGi ,
whereG is the building set. The features include the relative
distance dig[t] =‖pi[t]−pg[t]‖ between UA Vi and building
g, allowing the UA V to understand the environment. Addi-
tionally, each building has associated structural dimensions
sg = (hg,wg,dg), which are height, width, and depth, giving
the UA V a sense of the building’s physical characteristics and
potential obstacles:
oBuildingi [t] ={(dig[t],sg)⏐⏐g∈G ,dig≤RGi } (13)
These observation features provide a comprehensive represen-
tation of the UA V’s state and its surrounding environment. To
handle variable-length neighbor sets, the observations are ﬁrst
ﬁltered on the basis of a predeﬁned perception radius. The k’
nearest nodes’ information is then selected and, if necessary,
padded to ensure consistent input dimensions. All features
are normalized to maintain dimensional consistency across
different observations, preventing any feature from dominating
due to scale differences. This normalization facilitates effective
aggregation and interpretation of the UA V’s state, allowing
the neural network to learn meaningful patterns and make
informed decisions based on a stable, ﬁxed-size input vector.
B. Action
In the trajectory design task, the action space for each
UA V consists of a combination of ﬂight speed vi[t] and ﬂight
directionψi[t]. The direction includes nine possible movement
options: north, south, west, east, northwest, northeast, south-
west, southeast, and hover. This action space is represented
as
ai[t] ={vi[t],ψi[t]} (14)
C. Reward
After executing the chosen actions, UA Vs will obtain the
reward as
ri[t] = 1I
I∑
i=0
(λ1
(
1
N
∑N
n=1Rn[t]
)
¯Rmax +λ2Sn[t]
−λ3Ci[t]−λ4Pout[t]
)
(15)
Here, ¯Rmax denotes the theoretical maximum transmission
rate; Ci[t] indicates whether UA Vi collides with another UA V
at time t; and P out[t] denotes the probability that UA V i is
outside the service area. The coefﬁcients λ1,λ 2,λ 3,λ 4 are
scalar weights for the reward and penalty terms, reﬂecting
their relative priorities. Higher weights are assigned to the rate
and satisfaction components as primary objectives; the out-of-
bounds penalty steers UA Vs toward user-dense regions; and
the collision term carries a small weight because collisions
are rare in this environment. The reward is shared across all
UA Vs to encourage cooperative behavior.
IV. M EMORY-E NHANCED DYNAMIC SELF -ATTENTION
COMMUNICATION MECHANISM
A. Algorithm Architecture
This section details the proposed Mem-DSACM algorithm.
As shown in Fig. 2, the framework involves multiple UA V
agents that autonomously collect environmental data. These
agents efﬁciently share and exchange temporal information
through an adaptive distance-based communication mecha-
nism, enabling cooperative decision-making. The collected
data are embedded and processed to extract essential features.
The algorithm employs a lightweight Transformer network
(only decoder network) to capture the dynamic patterns in
the time-series data, leveraging its exceptional performance in
temporal analysis to detect complex environmental changes
precisely. Based on the extracted features, a distributed multi-
agent reinforcement learning framework is utilized to make
action decisions and optimize strategies, ensuring scalable
collaboration and adaptive system performance. The details
are as follows.
B. Spatially Constrained Communication Embedding
To support decentralized cooperation, a spatially constrained
communication mechanism is adopted, where each UA V
exchanges information with neighboring agents located within
a predeﬁned communication radius. For a given UA V i, the
set of observable neighbors includes those UA Vs u ∈ I
satisfying diu ≤ RUi , where diu = ‖pi−pu‖ denotes the
Euclidean distance between UA V i and UA Vu. Each valid
neighbor provides two features: the relative distance diu and
its communication load lu. These features form a structured
and physically grounded feature set:
cUA Vi ={(diu,lu)⏐⏐u∈I , diu≤RUi} (16)
To ensure consistency across samples, the feature values are
subsequently normalized. This communication-aware feature
set is then integrated with the UA V’s local observation history
over the most recent k time steps, denoted as oi,t:t+k =
{oi,t,oi,t+1,...,o i,t+k−1}. Then, the combined features are
processed by an observation embeddings module, which
projects them into a uniﬁed ﬁxed-dimensional representation
space via a learnable linear transformation, as in Eq.(17).
Where W′ and b′ are the parameters of the embedding layer,
andσ1 denotes the non-linear activation function (e.g., ReLU).
hi,t:t+k =E(oi,t:t+k) =σ1(W′·oi,t:t+k +b′) (17)
C. Dynamic Self-Attention Network
The Transformer architecture [44], initially designed with
a complete encoder-decoder structure, has gained signiﬁcant
adoption in contemporary implementations through its discrete
encoder/decoder operational paradigms. The key difference
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

YUAN et al.: MEMORY-ENHANCED DYNAMIC SELF-ATTENTION COMMUNICATION MECHANISM 9763
Fig. 2. The proposed algorithm framework.
Fig. 3. Transformer decoder structure.
between the two is that the decoder applies causal masking
in the attention layer, meaning that the ith token cannot
attend to subsequent tokens in the sequence, ensuring the
temporal order of information. Since the Transformer decoder
performs better in generation tasks (such as next-token predic-
tion), this paper chooses the Transformer decoder architecture
to process historical features. The decoder functions as a
Dynamic Self-Attention Network, continuously integrating
sequential embeddings derived from both local observations
and communication-aware inputs. The algorithm structure is
shown in Fig. 3.
1) Position Embedding: Positional encoding is an important
component of the Transformer network, used to introduce
positional information into the sequence [45]. In reinforcement
learning environments, the role of positional encoding depends
on the temporal dependencies of the task features. If the
features in the observation sequence exhibit temporal regulari-
ties, positional encoding can signiﬁcantly improve the model’s
ability to capture time-dependent information. However, if the
changes in the observation features are not strongly related
to time, the introduction of positional information may have
limited signiﬁcance.
This study adopts learnable positional encoding for maxi-
mum ﬂexibility in diverse task environments. This encoding
method allows the agent to adaptively decide how to utilize
positional information based on the task requirements. Specif-
ically, after being embedded and encoded, the features from
multiple time steps are combined with positional encoding
and then fed into the Transformer decoder to further enhance
the capability of modeling temporal sequence features. The
formula for introducing positional encoding is as follows:
E0i =hi,t:t+k + Posi,t:t+k (18)
wherehi,t:t+k represents the features of UA Vi from time step
t tot+k−1, and Posi,t:t+k represents the learnable positional
parameters from time step t to t +k− 1.
2) Masked Multi-Headed Self-Attention: Like the DTQN
(Deep Transformer Q-Network) network architecture [46],
the number of Transformer layers is set to L, and each
Transformer layer consists of two submodules: Masked Multi-
Head Self-Attention and Feed-Forward Network. The masking
mechanism functions by setting the attention weights of
future positions in the input sequence to zero, thereby ensur-
ing that the model focuses only on the current and past
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

9764 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 4. Masked multi-headed self-attention.
information during attention computation. The Multi-Head
Attention mechanism, as shown in Fig 4, focuses on extracting
relationships between observed objects and temporal features
from observation inputs. In the multi-agent reinforcement
learning framework, the agent independently computes the
input feature E0i as the query Qi, key Ki, and value Vi. Sub-
sequently, the Scaled Dot-Product Attention module is used
to compute the attention weights, deﬁned by the following
formula:
Attention(Qi,Ki,Vi) = softmax
(QiK⊤i√dk )Vi (19)
dk denotes the dimensionality of Qi, used to scale the dot-
product result and prevent numerical instability.
The multi-head attention mechanism allows extracting dif-
ferent state representations of agents from different subspaces,
where each attention head processes different input features.
The outputs from all heads are concatenated and transformed
via linear projection to generate the ﬁnal representation. The
formulas are as follows:
MultiHead(Qi,Ki,Vi) = Concat(head1,..., headn)WO
(20)
where
headz = Attention(QiWQiz ,KiWKiz ,ViWViz ) (21)
WQiz , WKiz , and WViz are learnable weight matrices. i repre-
sents the index of the head, and WO denotes the projection
weight matrix applied after concatenation.
3) Residual Connection and Layer Normalization: The
input and output of each submodule are connected using
a combination of residual connections [47] (referred to
as the “Combine” operation, as shown in Fig. 3). Speciﬁcally,
if the input to a given submodule is x, and its output is F (x),
the residual connection computes the output as y =F (x) +x.
This design helps the network maintain gradient ﬂow during
backpropagation and mitigates the vanishing gradient prob-
lem. Subsequently, the network applies Layer Normalization,
improving training stability and convergence speed.
For a UA V , after passing through the ﬁrst submodule of the
Transformer network, the feature representation is computed
as follows:
Eli,1 = LayerNorml−1i,1
(
Combinel−1i,1
[
× MultiHeadli(Ql−1i , Kl−1i , Vl−1i ), El−1i ]) (22)
where LayerNorm l−1i,1 normalizes the output, ensuring the
stability of the feature distribution and thereby providing high-
quality input for subsequent network layers.
4) Feed-F orward Network: Within each Transformer block,
a feed-forward network (FFN) is employed to enhance repre-
sentational depth. It comprises two dense layers with a ReLU
non-linearity in between, enabling the model to capture intri-
cate features. By introducing the ReLU activation function,
the network can learn more complex representations. The
operation can be formulated as:
FFN(x) = max (0, xW1 +b1)W2 +b2 (23)
Here, x is the input vector, W1 and W2 are weight matrices,
and b1 and b2 are the corresponding biases.
After passing through the FFN, the output feature represen-
tation is updated as follows:
Eli,2 = LayerNorm{Combine(FFN(Eli,1), Eli,1)} (24)
D. Multi-Agent Deep Reinforcement Learning
Due to the dynamic changes in the environment and partial
observability, UA Vs must be capable of continuously perceiv-
ing environmental changes and achieving effective interaction.
To address this, this study adopts a decentralized reinforce-
ment learning framework involving multiple agents, leveraging
the beneﬁts of collaborative decision-making. The detailed
procedure is illustrated in Algorithm 1. Within this setup,
UA Vs exchange observation data depending on their relative
positions. These shared features are then processed by L
Transformer decoder layers to extract temporal features and
capture the dynamic changes in the environment. For UA V
i, the processed features will be projected into action spaces.
The Q-value will be obtained as follows:
Q(hi,t:t+k,a ) = FFN(EL) (25)
Here,EL is the output features of the Lth layers Transformer
network. At time t, the action selection formula is given as
follows:
a∗i,t = arg maxa Q(hi,t:t+k,a ) (26)
Here, hi,t:t+k denotes the observed features spanning from
time t to time t +k− 1. The variable a indicates a candidate
choice from the set of all possible actions, whileQ(hi,t:t+k,a )
evaluates the expected return of selecting action a under
the given feature representation. At each time step t, the
agent determines its decision by choosing the option with the
highest Q.
This model optimizes the training strategy to fully utilize
time-series information from all time steps rather than relying
solely on the latest time step as in traditional methods, effec-
tively reducing data wastage. Speciﬁcally, the loss function
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

YUAN et al.: MEMORY-ENHANCED DYNAMIC SELF-ATTENTION COMMUNICATION MECHANISM 9765
Algorithm 1 Mem-DSACM Algorithm
1: Initialize the network parametersθ, target network param-
eters θ′, and replay buffer B.
2: for each training episode do
3: fori∈I do
4: Collect the observation information fi,t:t+k.
5: Get the spatially constrained communication fea-
tures hi,t:t+k.with (17)
6: Encode position encoding E0i with (18).
7: forl = 1,...,L do
8: Compute the output feature of the previous sub-
module El−1i,1 with (22).
9: Compute the output feature of the current sub-
module Eli,2 with (24).
10: end for
11: Evaluate the Q-value with (25).
12: Apply epsilon-greedy strategy to select action ai,t.
13: Store (oi,t,ai,t,ri,t,oi,t+1) inB.
14: end for
15: if Train then
16: fori∈I do
17: Sample a mini-batch from B:
(oi,t:t+k,ai,t:t+k,ri,t:t+k,o′i,t:t+k).
18: Compute the target Q-value Q.
19: Minimize the loss with (28).
20: Update both θ and θ′.
21: end for
22: end if
23: ClearB and proceed to the next training episode.
24: Reupload θ and θ′
25: end for
is deﬁned over a subhistory of length k, as shown in (28),
where t marks the beginning of the segment, and j indexes
the current time step within the sub-history, ranging from 1
to k. The loss at each step t includes the immediate reward
rt+j−1 and the discounted maximum Q-value of the next step
(computed using θ′), while the Q-value is obtained from θ.
Here,γ denotes the discount factor, and ot+j−1,at+j−1 refer
to the observation and action at step t +j− 1, respectively.
The objective function is deﬁned as:
Lj(θ) = E(·)∼D[(rt+j−1 +γ maxa′∈AQ(ot+1:t+j+1,a′;θ′)
−Q(ot:t+j,at+j−1;θ))2] (27)
The formulation trains the network to predict the Q-value at
each step in the sub-history, even for the earlier steps where
little context is available. The variable a′ indicates the action
taken in the next time step.
The loss is obtained at training episodes by summing the
losses across all time steps within the sub-history. The model
parameters are then updated using gradient descent as follows,
θ←θ−η∇θ
k∑
j=1
Lj(θ) (28)
Fig. 5. Urban environment buildings layout.
where η represents the learning rate, k speciﬁes the sequence
length, and ∇θ denotes the gradient with respect to the
parameters θ.
V. T IME COMPLEXITY AND CONVERGENCE ANALYSIS
A. Time Complexity Analysis
In Mem-DSACM algorithm,L denote the number of Trans-
former layers, and d indicates the number of neurons in each
layer. The time complexity is expressed as
O
(
I(·L· (ϖ·d2 +ϖ2d))) (29)
where I is the number of agents, ϖ is the input sequence
length, and d is the hidden dimension. For the MADQN algo-
rithm, the time complexity is O
(
I·L·ϖ·d2). It relies on
feedforward computations without modeling temporal depen-
dencies. By introducing LSTM to model temporal dependen-
cies, the time complexity of MADRQN is O
(
I·L·ϖ·d2).
Adding attention mechanisms to MADRQN, the time com-
plexity of MADARQN is O
(
I(·L·ϖ·d2 +ϖ2d))). For the
QMIX algorithm, a monotonic mixing network is introduced
to combine individual Q-values into a joint action-value func-
tion, leading to a complexity of O
(
I·L· (ϖ·d2)). QPLEX
decomposes the joint value into individual advantages and a
joint advantage term via a bilinear structure, the complexity
is O
(
I·L· (ϖ·d2 +I 2d2))
B. Convergence Analysis
Mem-DSACM is an extension of the Q-learning framework
and inherits its convergence properties. Given the conditions∑∞
t=0αt = ∞ and ∑∞t=0(αt)2 < ∞ and the bounded
rewards|rt(st,at)|, the Q-function will converge to the opti-
mal Q-function as t → ∞[48]. Furthermore, we adopt a
learning rate decay method, starting with a larger learning rate
in the early stages of training and gradually reducing it in the
later stages, ensuring that the algorithm converges to a good
local optimum.
VI. N UMERICAL RESULTS
A. Simulation Setting
This section presents the evaluation results of the Mem-
DSACM algorithm. The simulation environment is designed
using a stochastic mobility model to realistically emulate user
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

9766 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
TABLE I
SIMULATION PARAMETER SETTINGS
position in dynamics conditions, where UA Vs cannot get user
positions in advance and lack global environmental informa-
tion. The distribution layout of the buildings is shown in Fig. 5.
As illustrated, the environment contains 116 buildings with
two types: 14 commercial buildings (26m ×14m×20-25m)
and 102 residential buildings (8m ×6m×40m), resulting in a
4.16% building coverage ratio. The buildings are arranged in
clustered patterns to represent typical urban blocks.
The core settings for the Mem-DSACM framework include
a learning rate of 3· 10−4, a discount factor of 0.99, and
a replay buffer with capacity of 5,000 transitions. During
training, exploration is implemented using an exponentially
decayedϵ-greedy strategy, where ϵ decreases from 1.0 to 0.05
over the ﬁrst 70% of the total training steps and then remains
at 0.05 thereafter. Detailed hyperparameter conﬁgurations are
listed in Table I.
This experiment evaluates the performance of six
approaches, including two multi-agent extensions of classi-
cal deep reinforcement learning models: Memory-Enhanced
Multi-Agent Deep Q-Network (Mem-MADQN [49]) and
Memory-Enhanced Multi-Agent Deep Recurrent Q-Network
(Mem-MADRQN [50]). Additionally, two extended algo-
rithms of state-of-the-art value-based multi-agent methods,
Memory-Enhanced Monotonic Value Factorization Network
(Mem-QMIX [51]) and Memory-Enhanced Joint Advantage
Q-learning (Mem-QPLEX [52]) are included. The fully decen-
tralized communication-based method, Mem-TarMAC [31],
is used for a comprehensive comparison with the proposed
Mem-DSACM. Classical optimization and heuristic meth-
ods are less directly comparable in this setting because
they usually require stronger prior knowledge, or repeated
global re-optimization. The traditional Mem-MADQN algo-
rithm employs a Deep Q-Network structure, where each
Fig. 6. Comparison of training rewards and Training Time across different
algorithms during training epochs (a) Cumulative Reward (b) Training Time.
agent processes history information with an MLP network.
To capture temporal dependencies, MADRQN incorporates
Long Short-Term Memory (LSTM) networks. While LSTM
improves the modeling of temporal dependencies, Mem-
MADRQN can still be inefﬁcient when processing long
observation sequences in highly dynamic environments. Mem-
QMIX and Mem-QPLEX are both advanced methods that
follow a CTDE paradigm. Building on Mem-MADRQN,
Mem-QMIX introduces a monotonic mixing network for
Q-value aggregation, while Mem-QPLEX optimizes the pro-
cess with a bilinear decomposition of the joint advantage func-
tion. These methods were selected to compare our proposed
algorithm with state-of-the-art approaches, demonstrating their
performance in complex tasks. Mem-TarMAC is an attention-
based multi-agent communication method operating under
decentralized execution. It augments the original communi-
cation structure with an additional memory module to store
historical information across timesteps, thereby enhancing
long-term dependency modeling and improving coordination
performance. The proposed Mem-DSACM algorithm lever-
ages a memory-augmented self-attention mechanism within
a Transformer-based architecture. This design captures both
local and long-range dependencies across the entire sequence.
This breakthrough makes Mem-DSACM particularly well-
suited for handling complex interactions and long temporal
dependencies.
B. Results and Analysis
1) Comparison of Algorithms: In the training phase, the
variations in cumulative rewards and training time across
training epochs are examined for the different algorithms
in Fig. 6. In Fig. 6(a), Mem-DSACM achieves the high-
est cumulative reward with steady growth, showcasing its
superior convergence, learning efﬁciency, and stability. Mem-
MADQN, though improving early, suffers from instability later
in training. Mem-QMIX shows relatively low reward values,
indicating that its monotonic value factorization struggles to
adapt to the dynamic environment. Mem-QPLEX performs
well early on but experiences more ﬂuctuations towards the
end. Mem-TarMAC exhibits consistently strong reward growth
and converges to a high reward level, ranking second only to
Mem-DSACM, which demonstrates that communication-based
decentralized coordination can substantially improve learning
effectiveness under partial observability. The suboptimal per-
formance of Mem-QPLEX and Mem-QMIX may stem from
their reliance on local observations for joint decision making,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

YUAN et al.: MEMORY-ENHANCED DYNAMIC SELF-ATTENTION COMMUNICATION MECHANISM 9767
TABLE II
TRAINING PERFORMANCE COMPARISON OF DIFFERENT ALGORITHMS ON
UAV-ASSISTED NETWORK
Fig. 7. Rate distribution and percentile analysis of different algorithms in
testing phase (a) Rate Distribution (b) Percentile Analysis.
Fig. 8. Satisfaction performance analysis of different algorithms in testing
phase (a) cumulative coverage (ever-covered) (b) Coverage distribution by
time segments (c)Instant coverage percentage over time during the testing
process.
Fig. 9. Out-of-bounds frequency analysis of different algorithms in test-
ing process (a)Overall out-of-bounds frequency across different algorithms
(b) Cumulative out-of-bounds rate over time (c) Out-of-bounds frequency
distribution by time segment.
limited by the inability to access global state information, and
the challenges in adapting to complex, dynamic environments.
The corresponding training times in Fig. 6(b) show that
Mem-DSACM is relatively more efﬁcient, requiring less train-
ing time for comparable or superior performance. These results
highlight the efﬁciency and effectiveness of Mem-DSACM in
achieving high rewards with low computational overhead in
complex multi-agent scenarios. In Table II, the performance
of different algorithms is compared. Mem-DSACM achieves
the highest cumulative reward, surpassing the next best-
performing algorithm by 31.8%. Although its training time
is not the shortest, it is still competitive, requiring only 1.95%
higher than the optimal method (Mem-MADQN) and 14.5%
higher than Mem-MADRQN, demonstrating a good balance
between performance and efﬁciency.
In the testing phase, the performance of various algorithms
for UA V-assisted networks is evaluated, focusing on key met-
rics such as rate, satisfaction, and out-of-bounds frequency.
TABLE III
TESTING PERFORMANCE COMPARISON OF DIFFERENT MULTI-AGENT
REINFORCEMENT LEARNING ALGORITHMS ON UAV-ASSISTED
NETWORK . BOLD VALUES INDICATE THE BEST
PERFORMANCE FOR EACH METRIC
The results are summarized in Table III, which provides
detailed data for each metric. The performance of these algo-
rithms is also shown in Figs. 7, 8, and 9, which illustrate the
variations in rate, satisfaction, and out-of-bounds frequency,
respectively.
Rate Performance: As shown in Fig. 7 (a), Mem-DSACM
achieves the highest average rate, outperforming the next
best-performing algorithm, Mem-MADRQN, by 12.5%. Mem-
DSACM also exceeds Mem-TarMAC by 15.8%, Mem-QMIX
by 34% and Mem-QPLEX by 82%. In terms of maximum
rate, Mem-QMIX obtains the best value, while Mem-DSACM
remains highly competitive and is close to both Mem-QMIX
and Mem-TarMAC. Moreover, Mem-DSACM achieves the
best median rate and the best 90th percentile rate (Fig. 7 (b)),
slightly surpassing Mem-MADRQN and Mem-TarMAC, indi-
cating more consistently high-throughput performance across
users.
Satisfaction Rate: Mem-DSACM leads in user satisfaction.
As shown in Fig. 8 (a) and Table III, it achieves a cumulative
satisfaction rate of 62.26%, representing a 7.96% improve-
ment over Mem-MADRQN and an 8.21% improvement over
Mem-TarMAC. Mem-DSACM maintains superior satisfaction
rates throughout all time segments, as shown in Fig. 8 (b),
consistently outperforming the other algorithms.
Out-of-Bounds Frequency: Since the boundary is handled
as a soft constraint via reward penalty, out-of-bounds rate
reﬂects how well an algorithm learns to stay within the
service area while optimizing service reward. Mem-TarMAC
achieves the lowest out-of-bounds rate, while Mem-DSACM
ranks second, demonstrating strong stability. Compared with
Mem-MADRQN, Mem-DSACM reduces the out-of-bounds
frequency by 66.8%, and it also signiﬁcantly outperforms
Mem-QMIX, Mem-QPLEX, and Mem-MADQN. Panels
(b) and (c) further conﬁrm that Mem-DSACM maintains
low cumulative and time-segment out-of-bounds frequency,
ensuring stable performance throughout the test.
Speciﬁcally, we measure the computational overhead of
each algorithm using two metrics: the Average Test Time,
representing the total runtime of an entire evaluation episode,
and, more critically, the Average Test Time per period. The
latter quantiﬁes the online decision latency exclusively for
computational inference, excluding the ﬁxed service time.
Our proposed Mem-DSACM achieves an average decision
time of merely 35.8 ms per period, far below the period
duration ( ∆t = 5 s). This constitutes only 0.72% of the
period budget, leaving over 99% of the time for execution.
Although some baseline methods show slightly lower test
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

9768 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 10. Comparison of UA V trajectories obtained from different algorithms.
times, they suffer from severely degraded performance on
key communication metrics. Mem-DSACM thus provides a
highly favorable performance–efﬁciency trade-off, making it
both effective and practically deployable in latency-sensitive
UA V network.
In conclusion, Figs. 6–8 and Table III show that Mem-
DSACM achieves the best performance across key metrics. In
particular, Mem-DSACM yields the highest average rate and
cumulative satisfaction, while maintaining the lowest out-of-
bounds rate. Critically, it accomplishes this while requiring
only 35.8 ms of pure computation per decision period—a
negligible fraction of the service cycle.
Fig. 10 illustrates the trajectories of UA V-BSs designed
by different algorithms, each color-coded according to the
algorithm. The background shows a user density heatmap,
where areas with higher user density are depicted in brighter
colors, highlighting regions where the algorithms are likely to
encounter more users. The ﬁgure clearly reveals that UA Vs
employing different algorithms exhibit distinct path-planning
strategies. UA Vs using Mem-QPLEX and Mem-MADRQN
frequently deviate from the target zone, struggling to maintain
effective ﬂight paths and leading to suboptimal performance.
Mem-QMIX offers more stability but still often misses
high-density user regions, reducing its ability to optimize
throughput. Mem-TarMAC tends to concentrate its move-
ments within a few local regions and exhibits relatively
stable coverage of medium-density areas, but it is less con-
sistent than Mem-DSACM in persistently tracking the most
prominent high-density hotspots. In contrast, Mem-DSACM
UA Vs navigate efﬁciently through high-density areas. This
trajectory behavior provides an intuitive explanation of the
learned policy: Mem-DSACM uses local communication and
historical observations to guide UA V-BSs toward high-demand
regions more consistently, which contributes to the observed
improvements in rate and satisfaction.
2) SPaCE Module: The ablation study systematically eval-
uates three key design variants:
• Mem-DSACM (Full model) : With SPaCE and memory
• Mem-DSACM-Nocomm: Memory only, no SPaCE (no
spatial neighbor information)
Table IV evaluates the contribution of the SPaCE communi-
cation module by removing inter-UA V spatial communication.
Removing SPaCE (No-SPaCE) results in a 4.2% drop in
average rate. From these results, we conclude that both SPaCE
TABLE IV
ABLATION STUDY: COMMUNICATION MODULE (SPACE)
TABLE V
ABLATION STUDY: M EMORY LENGTH (ω = 1/30/50/60)
TABLE VI
ABLATION STUDY: NETWORK DEPTH (L = 1/2/3/4/6)
and the memory module play crucial roles in improving system
performance, with their combination yielding the best synergy.
3) History Length: Table V presents the performance of
the memory with varying memory lengths, where ω = 1
corresponds to using only the current observation and can
be interpreted as a no-memory setting. Increasing memory
length from 1 to 60 improves average rate and median rate,
with history = 60 achieving the highest performance, notably
a 5.2% increase in average rate compared to the baseline
(history = 50). History = 30 results in a slight degrada-
tion in performance, especially in satisfaction and cumulative
reward. On the other hand, the out-of-bounds rate improves
substantially with longer memory. History = 1 showing the
most signiﬁcant reduction to 0.00%, while history = 60 fur-
ther improves this metric by 85.3%. Training time increases
modestly with larger memory lengths, though the trade-off in
performance improvements remains competitive. As a minor
limitation, the method is mildly sensitive to the chosen history
window (evidenced by the dip at history = 30 ), and the self-
attention module incurs a modest O(ϖ2) cost in the history
length.
4) Network Depth: Table VI investigates the effect of
varying network depth on algorithm performance. Increasing
the number of layers results in a modest improvement in
average rate and median rate, with L = 6 yielding the highest
performance, a 2.7% increase over the baseline (L = 2).
However, deeper networks also introduce longer training time,
with L = 6 requiring 5.1% more time than the baseline. The
out-of-bounds rate improves as network depth increases, with
L = 6 showing a signiﬁcant reduction of 94.1% compared to
L = 2. Overall, deeper networks offer enhanced performance in
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

YUAN et al.: MEMORY-ENHANCED DYNAMIC SELF-ATTENTION COMMUNICATION MECHANISM 9769
TABLE VII
SCALABILITY STUDY OF MEM-DSACM W ITH
DIFFERENT NUMBERS OF UAV-BSS
TABLE VIII
SCALABILITY STUDY OF DTQN U NDER DIFFERENT USER DENSITIES
most metrics but come at the cost of increased computational
time.
5) Scalability:
a) Different numbers of UA Vs: To evaluate scalability,
supplementary experiments were conducted by varying the
number of UA V-BSs with I ∈ {2, 3, 4, 6, 8, 10} under the
same urban environment and evaluation protocol (Table VII).
The results show that increasing the number of UA V-BSs
from a small to a moderate team size improves spatial cov-
erage and service ﬂexibility, leading to higher throughput
and user satisfaction. As the number of UA Vs continues to
increase in the same service area, the performance trend
becomes more dependent on the balance among user demand,
spectrum resources, and local UA V interactions. This observa-
tion is consistent with practical UA V-BS deployments, where
adding UA Vs does not always produce gains once the main
user hotspots have been covered. Meanwhile, Mem-DSACM
remains decentralized for larger UA V teams because each
UA V exchanges information only with nearby agents within
its communication range. As a result, the communication
structure remains locally bounded as I increases, while the
gradual increase in average test time is expected due to the
larger number of UA V agents and local interaction features
involved in each decision step.
b) Different user densities: To evaluate scalability with
respect to trafﬁc load, supplementary experiments were con-
ducted by varying the user density the same urban environment
and evaluation protocol (Table VIII). Overall, throughput
and satisfaction exhibit a non-monotonic trend: performance
improves from low to moderate density, indicating better
resource utilization when sufﬁcient users are available to
exploit spatial and scheduling opportunities; as the density
further increases, performance decreases due to intensiﬁed
contention and limited spectral resources. Meanwhile, the out-
of-bounds rate remains relatively low but ﬂuctuates across
densities, suggesting that constraint satisfaction can become
more challenging under certain load levels. The average
test time increases with user density, mainly because the
environment-side evaluation and resource-allocation proce-
dures require traversing more users and resource blocks under
heavier demand.
VII. C ONCLUSION
In response to the challenges posed by dynamic and uncer-
tain environments in UA V-assisted wireless coverage, this
study develops Mem-DSACM, a lightweight reinforcement
learning framework that combines decentralized communica-
tion with memory-informed policy learning. By adopting a
spatially constrained communication scheme, UA V agents can
selectively share key information with nearby peers, enabling
low-latency and scalable coordination. A temporal reasoning
module further supports long-term decision optimization by
modeling sequential dependencies from partial observations.
Experimental evaluations validate the effectiveness of the
proposed approach Mem-DSACM. Relative to the best non-
DSACM baselines, it increases cumulative reward by 31.8%,
improves average rate by 12.5%, and raises cumulative sat-
isfaction by 8.0%. For complexity, compared against the
best-performing baseline, the training time is 6.3% lower, and
the average testing time is 17.5% lower.
REFERENCES
[1] B. He et al., “Energy-efﬁcient joint beamforming and trajectory opti-
mization for uav-enabled integrated sensing and communication,” IEEE
Trans. Commun., vol. 73, no. 12, pp. 13426–13440, Dec. 2025.
[2] Y . Li, A. S. Madhukumar, T. Z. H. Ernest, G. Zheng, W. Saad, and
A. H. Aghvami, “Energy-efﬁcient UA V-driven multi-access edge com-
puting: A distributed many-agent perspective,” IEEE Trans. Commun. ,
vol. 73, no. 9, pp. 8405–8420, Sep. 2025.
[3] R. Ye, Y . Peng, F. Al-Hazemi, and R. Boutaba, “A robust cooperative
jamming scheme for secure UA V communication via intelligent reﬂect-
ing surface,” IEEE Trans. Commun., vol. 72, no. 2, pp. 1005–1019, Feb.
2024.
[4] H. Zhang, B. Li, Y . Rong, Y . Zeng, and R. Zhang, “Joint optimiza-
tion of transmit power and trajectory for UA V-enabled data collection
with dynamic constraints,” IEEE Trans. Commun. , vol. 73, no. 9,
pp. 8080–8091, Sep. 2025.
[5] Y . Zhang et al., “Robust secure UA V communications with the aid
of jamming beamforming,” IEEE Trans. Commun. , vol. 73, no. 11,
pp. 12205–12220, Nov. 2025.
[6] Y . Liu, K. Liu, J. Han, L. Zhu, Z. Xiao, and X.-G. Xia, “Resource
allocation and 3-D placement for UA V-enabled energy-efﬁcient IoT
communications,” IEEE Internet Things J., vol. 8, no. 3, pp. 1322–1333,
Feb. 2021.
[7] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-UA V
networks,” IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660–2672, Apr.
2021.
[8] M. Mozaffari, A. T. Z. Kasgari, W. Saad, M. Bennis, and M. Debbah,
“Beyond 5G with UA Vs: Foundations of a 3D wireless cellular network,”
IEEE Trans. Wireless Commun. , vol. 18, no. 1, pp. 357–372, Jan. 2019.
[9] B. Jiang, J. Yang, H. Xu, H. Song, and G. Zheng, “Multimedia
data throughput maximization in Internet-of-Things system based on
optimization of cache-enabled UA V ,” IEEE Internet Things J. , vol. 6,
no. 2, pp. 3525–3532, Apr. 2019.
[10] P. G. Sudheesh, M. Mozaffari, M. Magarini, W. Saad, and P. Muthuchi-
dambaranathan, “Sum-rate analysis for high altitude platform (HAP)
drones with tethered balloon relay,” IEEE Commun. Lett. , vol. 22, no. 6,
pp. 1240–1243, Jun. 2018.
[11] L. Wang, B. Hu, and S. Chen, “Energy efﬁcient placement of a drone
base station for minimum required transmit power,” IEEE Wireless
Commun. Lett. , vol. 9, no. 12, pp. 2010–2014, Dec. 2020.
[12] Y . Luo, W. Ding, and B. Zhang, “Optimization of task scheduling
and dynamic service strategy for multi-UA V-enabled mobile-edge com-
puting system,” IEEE Trans. Cognit. Commun. Netw. , vol. 7, no. 3,
pp. 970–984, Sep. 2021.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

9770 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
[13] S. Zhang, W. Liu, and N. Ansari, “Joint wireless charging and data
collection for UA V-enabled Internet of Things network,” IEEE Internet
Things J., vol. 9, no. 23, pp. 23852–23859, Dec. 2022.
[14] Y . Gao, Y . Wu, Z. Cui, W. Yang, G. Hu, and S. Xu, “Robust trajectory
and communication design for angle-constrained multi-UA V communi-
cations in the presence of jammers,” China Commun. , vol. 19, no. 2,
pp. 131–147, Feb. 2022.
[15] Y . Guo, S. Yin, and J. Hao, “Resource allocation and 3-D trajectory
design in wireless networks assisted by rechargeable UA V ,” IEEE
Wireless Commun. Lett. , vol. 8, no. 3, pp. 781–784, Jun. 2019.
[16] J. Liu and H. Zhang, “Outage-aware deployment in multi-AA V-RIS
aided networks with imperfect CSI,” IEEE Trans. Commun. , vol. 73,
no. 11, pp. 11545–11558, Nov. 2025.
[17] M. K. Shehzad, A. Ahmad, S. A. Hassan, and H. Jung, “Backhaul-
aware intelligent positioning of UA Vs and association of terrestrial base
stations for fronthaul connectivity,” IEEE Trans. Netw. Sci. Eng. , vol. 8,
no. 4, pp. 2742–2755, Oct. 2021.
[18] H. Ghazzai, E. Yaacoub, M.-S. Alouini, Z. Dawy, and A. Abu-Dayya,
“Optimized LTE cell planning with varying spatial and temporal user
densities,” IEEE Trans. V eh. Technol. , vol. 65, no. 3, pp. 1575–1589,
Mar. 2016.
[19] C. Wang, D. Deng, L. Xu, and W. Wang, “Resource scheduling based on
deep reinforcement learning in UA V assisted emergency communication
networks,” IEEE Trans. Commun. , vol. 70, no. 6, pp. 3834–3848, Jun.
2022.
[20] K. K. Nguyen, T. Q. Duong, T. Do-Duy, H. Claussen, and L. Hanzo, “3D
UA V trajectory and data collection optimisation via deep reinforcement
learning,” IEEE Trans. Commun. , vol. 70, no. 4, pp. 2358–2371, Apr.
2022.
[21] C. Qiu, Y . Hu, Y . Chen, and B. Zeng, “Deep deterministic policy
gradient (DDPG)-based energy harvesting wireless communications,”
IEEE Internet Things J. , vol. 6, no. 5, pp. 8577–8588, Oct. 2019.
[22] X. Liu, M. Chen, and C. Yin, “Optimized trajectory design in UA V
based cellular networks for 3D users: A double Q-learning approach,”
J. Commun. Inf. Netw. , vol. 4, no. 1, pp. 24–32, Mar. 2019.
[23] J. Ji, K. Zhu, and L. Cai, “Trajectory and communication design for
cache{-} enabled UA Vs in cellular networks: A deep reinforcement
learning approach,” IEEE Trans. Mobile Comput. , vol. 22, no. 10,
pp. 6190–6204, Oct. 2023.
[24] H. Fu, J. Wang, J. Chen, P. Ren, Z. Zhang, and G. Zhao, “Dense
multiagent reinforcement learning aided multi-UA V information cov-
erage for vehicular networks,” IEEE Internet Things J. , vol. 11, no. 12,
pp. 21274–21286, Jun. 2024.
[25] Y . He, Y . Gan, H. Cui, and M. Guizani, “Fairness-based 3-D multi-
UA V trajectory optimization in multi-UA V-assisted MEC system,”IEEE
Internet Things J. , vol. 10, no. 13, pp. 11383–11395, Jul. 2023.
[26] Y . Zhang, Z. Mou, F. Gao, J. Jiang, R. Ding, and Z. Han, “UA V-enabled
secure communications by multi-agent deep reinforcement learning,”
IEEE Trans. V eh. Technol., vol. 69, no. 10, pp. 11599–11611, Oct. 2020.
[27] H. Kang, X. Chang, J. Mi ˇsi´c, and V . B. Mi ˇsi´c, “Cooperative UA V
resource allocation and task ofﬂoading in hierarchical aerial computing
systems: A MAPPO-based approach,” IEEE Internet Things J. , vol. 10,
no. 12, pp. 10497–10509, Jun. 2023.
[28] M. Pourghasemian, M. R. Abedi, S. S. Hosseini, N. Mokari, M. R. Javan,
and E. A. Jorswieck, “AI-based mobility-aware energy efﬁcient resource
allocation and trajectory design for NFV enabled aerial networks,” IEEE
Trans. Green Commun. Netw. , vol. 7, no. 1, pp. 281–297, Mar. 2023.
[29] M. R. Abedi, N. Mokari, M. R. Javan, H. Saeedi, E. A. Jorswieck, and
N. Zorba, “Low complexity and mobility-aware robust radio, storage,
computing, and cost management for cellular vehicular networks,” IEEE
Trans. V eh. Technol., vol. 74, no. 2, pp. 3327–3344, Feb. 2025.
[30] J. Jiang, C. Dun, T. Huang, and Z. Lu, “Graph convolutional rein-
forcement learning,” in Proc. 8th Int. Conf. Learn. Represent. , Addis
Ababa, Ethiopia, 2020. [Online]. Available: https://openreview.net/
forum?id=HkxdQkSYDB
[31] A. Das et al., “TarMAC: Targeted multi-agent communication,”
in Proc. 36th Int. Conf. Mach. Learn. , vol. 97, Jun. 2019,
pp. 1538–1546.
[32] X. Zhang, H. Zhao, J. Wei, C. Yan, J. Xiong, and X. Liu, “Cooperative
trajectory design of multiple UA V base stations with heterogeneous
graph neural networks,” IEEE Trans. Wireless Commun. , vol. 22, no. 3,
pp. 1495–1509, Mar. 2023.
[33] Y . Pan, X. Wang, Z. Xu, N. Cheng, W. Xu, and J.-J. Zhang,
“GNN-empowered effective partial observation MARL method for AoI
management in multi-UA V network,” IEEE Internet Things J. , vol. 11,
no. 21, pp. 34541–34553, Nov. 2024.
[34] Z. Gao, J. Fu, Z. Jing, Y . Dai, and L. Yang, “MOIPC-MAAC:
Communication-assisted multiobjective MARL for trajectory planning
and task ofﬂoading in multi-UA V-assisted MEC,” IEEE Internet Things
J., vol. 11, no. 10, pp. 18483–18502, May 2024.
[35] Z. Xie, Z. Wang, Z. Zhang, J. Wang, Z. Jiang, and Z. Han, “Distributed
UA V swarm for device-free integrated sensing and communication rely-
ing on multi-agent reinforcement learning,” IEEE Trans. V eh. Technol.,
vol. 73, no. 12, pp. 19925–19930, Dec. 2024.
[36] Z. Wu, S. Pan, F. Chen, G. Long, C. Zhang, and P. S. Yu, “A
comprehensive survey on graph neural networks,” IEEE Trans. Neural
Netw. Learn. Syst. , vol. 32, no. 1, pp. 4–24, Jan. 2021.
[37] B. Zhu, E. Bedeer, H. H. Nguyen, R. Barton, and Z. Gao, “UA V
trajectory planning for AoI-minimal data collection in UA V-aided IoT
networks by transformer,” IEEE Trans. Wireless Commun. , vol. 22,
no. 2, pp. 1343–1358, Feb. 2023.
[38] Q. Zheng, A. Zhang, and A. Grover, “Online decision transformer,” in
Proc. Int. Conf. Mach. Learn. , 2022, pp. 27042–27059.
[39] M. Carroll et al., “Towards ﬂexible inference in sequential decision
problems via bidirectional transformers,” 2022, arXiv:2204.13326.
[40] J. Kuba et al., “Multi-agent reinforcement learning is a sequence
modeling problem,” in Proc. Adv. Neural Inf. Process. Syst. 35 . Red
Hook, NY , USA: Curran Associates Inc., 2022, pp. 16509–16521.
[41] W. Khawaja, I. Guvenc, D. W. Matolak, U.-C. Fiebig, and N. Schneck-
enburger, “A survey of air-to-ground propagation channel modeling for
unmanned aerial vehicles,” IEEE Commun. Surveys Tuts., vol. 21, no. 3,
pp. 2361–2391, 3rd Quart., 2019.
[42] N. Kolehmainen, J. Puttonen, P. Kela, T. Ristaniemi, T. Henttonen, and
M. Moisio, “Channel quality indication reporting schemes for UTRAN
long term evolution downlink,” in Proc. IEEE V eh. Technol. Conf. (VTC
Spring), May 2008, pp. 2522–2526.
[43] Y . Kim and J. Kim, “An efﬁcient subcarrier allocation scheme for
capacity enhancement in multiuser OFDM systems,” in Proc. IEEE V eh.
Technol. Conf. (VTC Spring) , May 2008, pp. 1915–1919.
[44] A. Vaswani et al., “Attention is all you need,” in Proc. Adv. Neural Inf.
Process. Syst., vol. 30, 2017, pp. 5998–6008.
[45] P. Dufter, M. Schmitt, and H. Sch ¨utze, “Position information in
transformers: An overview,” Comput. Linguistics , vol. 48, no. 3,
pp. 733–763, Sep. 2022.
[46] K. Esslinger, R. Platt, and C. Amato, “Deep transformer Q-networks for
partially observable reinforcement learning,” 2022, arXiv:2206.01078.
[47] K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for
image recognition,” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit.
(CVPR), Jun. 2016, pp. 770–778.
[48] P. Dayan and C. Watkins, “Q-learning,” Mach. Learn. , vol. 8, no. 3,
pp. 279–292, 1992.
[49] M. A. Ouamri, G. Barb, D. Singh, A. B. M. Adam, M. S. A. Muthanna,
and X. Li, “Nonlinear energy-harvesting for D2D networks underlaying
UA V with SWIPT using MADQN,”IEEE Commun. Lett., vol. 27, no. 7,
pp. 1804–1808, Jul. 2023.
[50] X. Tan et al., “Cooperative multi-agent reinforcement-learning-based
distributed dynamic spectrum access in cognitive radio networks,” IEEE
Internet Things J. , vol. 9, no. 19, pp. 19477–19488, Oct. 2022.
[51] T. Rashid, M. Samvelyan, C. S. De Witt, G. Farquhar, J. Foerster, and
S. Whiteson, “Monotonic value function factorisation for deep multi-
agent reinforcement learning,” J. Mach. Learn. Res. , vol. 21, no. 178,
pp. 1–51, 2020.
[52] J. Wang, Z. Ren, T. Liu, Y . Yu, and C. Zhang, “QPLEX: Duplex dueling
multi-agent Q-learning,” in Proc. 9th Int. Conf. Learn. Represent.
(ICLR), 2021.
Hanxiao Yuan received the master’s degree from
Harbin Institute of Technology, Shenzhen, in 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply. 

YUAN et al.: MEMORY-ENHANCED DYNAMIC SELF-ATTENTION COMMUNICATION MECHANISM 9771
Yao Shi (Member, IEEE) received the Ph.D.
degree in electrical and electronic engineering
from The University of Manchester, U.K. She
joined Harbin Institute of Technology, Shenzhen,
in 2021, and is currently an Associate Professor
with the School of Information Science and Tech-
nology. Her research interests include integrated
satellite–terrestrial networks, UA V communications,
B5G/6G uplink enhancement technologies, and mul-
timodal data fusion.
Emad Alsusa (Senior Member, IEEE) is currently
a Professor of communications and signal process-
ing with The University of Manchester, where he
leads the Communications Research Group. He was
a Post-Doctoral Researcher with The University
of Edinburgh from 2000 to 2003 before joining
Manchester in 2003. He has authored over 300 peer-
reviewed journal and conference publications and
has supervised more than 40 Ph.D. students. His
research focuses on communication systems across
the physical, MAC, and network layers. He serves
as an Editor for IEEE W IRELESS COMMUNICATIONS LETTERS and IEEE
TRANSACTIONS ON VEHICULAR TECHNOLOGY , has held several TPC lead-
ership roles at major IEEE conferences, and has received multiple best paper
awards.
Qinyu Zhang (Senior Member, IEEE) received
the bachelor’s degree in communication engineering
from Harbin Institute of Technology (HIT), Harbin,
China, in 1994, and the Ph.D. degree in biomedical
and electrical engineering from Tokushima Univer-
sity, Tokushima, Japan, in 2003. From 1999 to
2003, he was an Assistant Professor with Tokushima
University. From 2003 to 2005, he was an Associate
Professor with Shenzhen Graduate School, HIT. He
was the Founding Director of the Communication
Engineering Research Center, School of Electronic
and Information Engineering (EIE). Since 2005, he has been a Full Professor
and the Dean of the EIE School, HIT. His research interests include aerospace
communications and networks, wireless communications and networks, cog-
nitive radios, signal processing, and biomedical engineering. He has been a
TPC Member of INFOCOM, IEEE ICC, IEEE GLOBECOM, IEEE Wireless
Communications and Networking Conference, and other ﬂagship conferences
in communications. He was the Associate Chair of the Finance of the Inter-
national Conference on Materials and Manufacturing Technologies in 2012.
He was the TPC Co-Chair of IEEE/CIC ICCC 2015. He was the Symposium
Co-Chair of CHINACOM 2011 and IEEE Vehicular Technology Conference
2016 (Spring). He was the Founding Chair of the IEEE Communications
Society Shenzhen Chapter. He is on the Editorial Board of some academic
journals, such as Journal of Communication , KSII Transactions on Internet
and Information Systems , and Science China Information Sciences .
Yiping Duan (Senior Member, IEEE) received the
B.S. degree from the School of Computer Sci-
ence and Technology, Henan Normal University,
Xinxiang, China, in 2010, and the Ph.D. degree
from the School of Computer Science and Tech-
nology, Xidian University, Xi’an, China, in 2016.
She is currently an Assistant Research Fellow with
the Department of Electronic Engineering, Tsinghua
University, Beijing, China. Her current research
interests include wireless communications, machine
learning, computer vision, and image processing.
Xiaohu You (Fellow, IEEE) has been working
with the National Mobile Communications Research
Laboratory, Southeast University, where he holds
the rank of the Director and a Chief Professor.
Currently, he is also the Director and the Chief
Scientist of Purple Mountain Laboratories and the
Deputy Director of the Peng Cheng Laboratory.
His research interests include broadband wireless
transmission, mobile communication systems, and
advanced signal processing and its applications. He
won the Tan Kah Kee Science Award in 2014 and
the IET Achievement Medal in 2021. He was awarded an Academician of
China Academy of Science in 2023.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on July 28,2026 at 07:36:03 UTC from IEEE Xplore.  Restrictions apply.