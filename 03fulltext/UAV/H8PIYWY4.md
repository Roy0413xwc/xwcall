---
title: "Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications via Hierarchical Optimal Control"
zotero_key: "H8PIYWY4"
pdf_key: "2RVKF9X8"
doi: "10.1109/TCOMM.2026.3698909"
collection: "UAV"
note_path: "02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications.md"
source: "Zotero PDF full-text cache"
page_mapping: unknown
---

# Real-Time UAV Path and Role-Coordinated Planning Method ... — Fulltext

> 本文件由 Zotero PDF 全文缓存归档生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（缓存无 page mapping）。原始 PDF：
> `F:\XWCos\zotero\storage\2RVKF9X8\Wang 等 - 2026 - Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications via Hierarchica.pdf`

---

9484 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Real-Time UAV Path and Role-Coordinated
Planning Method for Emergency Communications
via Hierarchical Optimal Control
Shangpeng Wang , Ling Chen, Xiatong Hou, Xinyue Wang , Chenyuan Zhang, Haoran Yang , Haijun Zhang , Senior Member, IEEE, and Haixin Sun , Senior Member, IEEE
Abstract—Cooperative path planning for UAVs using hierarchical optimal control is a critical technology for urban emergency communication networks. Existing methods typically decouple trajectory optimization from communication scheduling, which inherently leads to suboptimal performance. Attempting to solve the problem monolithically creates a largescale Mixed-Integer Non-Linear Program that is computationally intractable for real-time deployment. Compounding this, current models often overlook the need for dynamic UAV role-switching, limiting the system’s functional flexibility and operational adaptability. We propose a hierarchical control framework that decomposes the problem into a dual-layer model predictive control architecture. Specifically, we linearize the original problem within a receding horizon control loop for long-term task and trajectory planning in the strategic layer. Guided by this, the lower trajectory layer employs non-linear model predictive control, solved via sequential convex programming, to generate realtime trajectories and perform adaptive role switching. Simulation results demonstrate that the proposed framework reduces mission makespan by 8.6% and increases the total data collected by 2.4%, validating its efficiency and robustness.
Index Terms—UAV-assisted communication, path planning, hierarchical optimal control, model predictive control, emergency data collection, trajectory optimization.
I. INTRODUCTION
U
AVS have emerged as a pivotal technology for emergency data collection in urban environments [1], [2]. Acting as mobile relays, they are critical for overcoming communication blackouts caused by obstructions, thereby ensuring
Received 19 October 2025; revised 12 February 2026 and 5 April 2026; accepted 10 May 2026. Date of publication 1 June 2026; date of current version 10 June 2026. This work was supported in part by the National Natural Science Foundation of China under Grant No. 61972398. The associate editor coordinating the review of this article and approving it for publication was P. Sarigiannidis. (Corresponding author: Haoran Yang.)
Shangpeng Wang is with the School of Informatics, Xiamen University, Xiamen 361005, China, and also with the School of Computer Science and Engineering, Central South University, Changsha 410083, China (e-mail: Dr.Wang cse@csu.edu.cn). Ling Chen, Xiatong Hou, and Haixin Sun are with the School of Informatics, Xiamen University, Xiamen 361005, China (e-mail: clynn1@stu.xmu.edu.cn; xxxhhh@stu.xmu.edu.cn; hxsun@xmu.edu.cn). Xinyue Wang and Chenyuan Zhang are with the School of Computer Science and Engineering, Central South University, Changsha 410083, China (e-mail: xinyue wang@csu.edu.cn; zhangchenyuan@csu.edu.cn). Haoran Yang is with the Big Data Institute, Central South University, Changsha 410083, China (e-mail: haoran.yang@csu.edu.cn). Haijun Zhang is with the School of Computer Science and Technology, Harbin Institute of Technology, Shenzhen 518055, China (e-mail: hjzhang@hit.edu.cn). Digital Object Identifier 10.1109/TCOMM.2026.3698909
connectivity in disaster-stricken areas [3], [4]. The effective deployment of a multi-UAV fleet in such scenarios, however, requires sophisticated coordination to achieve mission objectives. UAV operations are characterized by a tightly coupled nature, where continuous decisions related to trajectory planning and discrete decisions regarding task allocation are deeply intertwined. These interdependencies lead to a combinatorial explosion of possible solutions, making the problem computationally intractable. Additionally, real-time constraints and dynamic environmental factors, such as varying communication links and battery limitations, further complicate the decision-making process [5]. Discrete decisions, such as assigning specific tasks to individual UAVs, must adhere strictly to pressing data collection deadlines and finite onboard energy budgets [6]. These intricate interdependencies formulate a large-scale Mixed-Integer Non-Linear Program (MINLP). The NP-hard nature of this problem renders it computationally intractable, as solution times grow exponentially with scale, making it fundamentally unsuitable for the rapid, real-time decision-making required in emergency response [7]. Existing approaches typically simplify the problem by decoupling it into separate sub-problems, such as path planning and task scheduling. However, this separation inevitably leads to suboptimal performance [8], [9]. Conversely, monolithic solvers that attempt to find a joint optimal solution are generally too slow for dynamic, real-world scenarios [7]. These shortcomings are often compounded by oversimplified models that neglect crucial operational realities, such as dynamic tasking and on-the-fly role-switching for UAVs [10], [11]. While data-driven techniques like reinforcement learning have shown promise, they often lack the formal performance guarantees necessary for critical applications [12], [13], [14]. To overcome these limitations, we propose a Hierarchical Optimal Control for UAV-assisted Data Collection (HOCUADC) framework. Our approach addresses the computational intractability of the global MINLP by decomposing it into two distinct but coupled sub-problems that operate on different time scales. The system employs a high-level strategic layer for long-term planning and a low-level trajectory layer for finegrained, real-time control. This hierarchical structure, guided by a Receding Horizon Control (RHC) mechanism, allows
0090-6778 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artificial intelligence and similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission. See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9485
our system to approach global optimality while maintaining responsiveness to dynamic changes. Our principal contributions are as follows:
• We formulate a MINLP for UAV-assisted emergency communication. Our model jointly optimizes UAV trajectories, task scheduling, and multi-hop data relaying while rigorously accounting for dynamic LoS blockages, heterogeneous IoT data requirements, and deadlines. • We introduce a novel two-layer hierarchical optimization framework to solve the intractable MINLP. The strategic layer employs a linearized Mixed-Integer Linear Program (MILP) for efficient long-term fleet coordination, which is then dynamically adjusted through an RHC loop to ensure adaptability. • We design a real-time, high-fidelity trajectory layer based on Non-linear Model Predictive Control (NMPC). This layer features an innovative embedded combinatorial scheme to decouple discrete role-switching from continuous trajectory optimization intelligently. Solved efficiently via Sequential Convex Programming (SCP), it generates physically feasible, locally optimal control actions in real-time. • We validate the proposed framework through extensive simulations in realistic, map-based urban environments. The results demonstrate that our approach significantly outperforms state-of-the-art baselines by achieving a superior trade-off between mission success rate, completion time, and computational efficiency.
II. RELATED WORK
The core challenge in UAV-assisted emergency communications is to complete data collection tasks efficiently and robustly under strict deadlines, particularly in urban environments with complex blockages.
A. Path Planning and Trajectory Optimization
Early research focused on the fundamental problem of generating efficient flight paths[15], [16]. In parallel, metaheuristic approaches like genetic algorithms [17] and particle swarm optimization [18] were applied to search for optimal paths. These methods provide a valuable foundation for UAV mobility modelling and can generate feasible flight plans in predictable scenarios. However, their primary limitation is the decoupling of path planning from communication tasks. They typically operate with a static communication objective, ignoring the dynamics and resource requirements of the tasks themselves [19]. Consequently, these methods suffer from poor adaptability in dynamic emergency scenarios. To improve system performance, it became necessary to incorporate tasklevel decision-making.
B. Task Scheduling and Resource Allocation
To better align UAV mobility with mission objectives, researchers began integrating task scheduling and resource allocation into the optimization. Pioneering this direction, Quirynen et al. [20] used mixed-integer programming to
optimize trajectories and task assignments jointly. This decomposition-based approach became a standard paradigm. For instance, the MinTime-TCO algorithm employed Block Coordinate Descent (BCD) to iteratively optimize a UAV’s hovering positions and charging energies to minimize mission time [21]. Similarly, the AoI-EaTO algorithm decomposed the problem into UAV speed and path subproblems, solving them with successive convex approximation (SCA) and genetic algorithms to minimize completion time under AoI and energy constraints [22]. Metaheuristic methods were also adapted for this integrated purpose. For example, the MACONOTM algorithm utilized a modified ant colony optimization (MACO) to solve the NP-hard trajectory subproblem while jointly minimizing the number of UAVs and their operation time [23]. This work shifted the focus from mere mobility efficiency to broader task-centric metrics like latency, energy, and quality of service. Subsequent work refined this approach with bandwidth-aware scheduling [24], NOMA-based schemes for uplink concurrency [25], [26], and energy-aware planning with wireless power transfer or recharging opportunities [27], [28]. Despite these advances, most of these frameworks rely on centralized scheduling architectures [11] that assume simplified UAV mobility. In large-scale, dynamic scenarios, this centralization creates significant signalling overhead and decision latency, forming a new performance bottleneck.
C. Distributed Multi-UAV Cooperation Method
To overcome the scalability and latency issues associated with centralized control, researchers developed distributed mechanisms. Early distributed methods included task graph decomposition [29], though its assumption of sub-task independence is often invalid in complex urban settings. More sophisticated approaches based on game theory [30], [31], [32] and auction mechanisms [33] enabled local resource negotiation but suffered from high complexity or slow convergence. Recently, data-driven methods like Multi-Agent Reinforcement Learning (MARL) have gained prominence for learning decentralized policies [34]. While these adaptive methods excel in complex environments without explicit modelling, they introduce their own challenges, including a combinatorial explosion of the state-action space, poor generalization to unforeseen events, and a lack of formal performance guarantees, all of which are critical concerns for safety-critical missions. Underlying these technical hurdles is a more fundamental problem: most distributed approaches treat high-level strategic decision-making and low-level physical execution as separate challenges. A strategically optimal task allocation derived from a game-theoretic or MARL model might be physically infeasible or energetically unsustainable when the complexities of 3D flight and real-world communication links are considered. Although hierarchical control and MPC were applied to UAV navigation in previous studies [35], [36], these works often focused purely on mobility and collision avoidance, neglecting the tightly coupled communication constraints. They simplified communication to a basic connectivity requirement rather than optimizing for data rates, latency, and multi-hop relaying under blockage. This paper proposes an
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

9486 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
MPC-based hierarchical framework tailored explicitly for the joint communication and control problem. We bridge the gap between abstract coordination and concrete physical implementation by ensuring that high-level strategic decisions are directly informed by and translated into low-level, dynamically feasible trajectories that explicitly optimize communication performance. Our integrated approach ensures cooperative strategies are not only logically sound but also physically and energetically feasible, enhancing both mission speed and network resilience in urban emergencies.
III. SCENARIO DESCRIPTION AND SYSTEM MODEL
We model a UAV-assisted wireless system comprising agile UAVs and fixed IoT devices under LoS blockage and coverage limitations. The system operates under mobility, connectivity, and energy constraints, which form the basis for the subsequent cross-layer optimization problem.
A. System Model
We consider a UAV-assisted data collection system deployed in dense urban environments, where stationary IoT devices I = {i1, i2, . . ., iN } monitor critical events, each IoT device in ∈ I is located at (xn, yn, 0), and generates a data packet of size Sn at time τn, which must be uploaded before a deadline δn. During emergencies, these devices must upload timesensitive data to a remote server in a timely manner. However, due to cellular dead zones and LoS blockages caused by highrise buildings, direct transmission to ground infrastructure is often infeasible. To address the problem of blocked direct transmission, a fleet of UAVs U = {u1, u2, . . ., uM } is deployed as mobile relays. Each UAV um ∈ U dynamically adjusts its 3D position pm(t) = (xm(t), ym(t), hm(t)), where altitude is bounded by:
hmin ≤ hm(t) ≤ hmax, ∀m, t (1)
To ensure physically realistic and energy-aware motion, we discretize the operation into equal-length time slots of duration ∆t, indexed by t = 0, 1, . . ., T . UAV trajectories are subject to the following mobility constraint:
(xm(t+1) − xm(t))2 + (ym(t+1) − ym(t))2
+ (hm(t+1) − hm(t))2 ≤ (vmax∆t)2 (2)
with additional altitude variation limit:
|hm(t+1) − hm(t)| ≤ vmax
h ∆t (3)
where vmax and vmax
h are the UAV’s maximum 3D and vertical velocities, respectively. At each time slot t, each UAV um can perform at most one primary action: collecting data from an IoT device, relaying data, which involves both receiving and transmitting, typically in different time slots, or uploading data to the server (a transmitting task). We assume all UAVs operate in a half-duplex mode, meaning they cannot transmit and receive simultaneously in the same frequency band. The roles are denoted by binary variables ρc
m(t) (collection), ρr,rx
m (t)
(relay-receive), and ρtx
m(t) (transmit). The transmission role
Fig. 1. UAV-assisted data collection in urban environments. Data from device i2 is directly uploaded to the remote server via UAV u4. Data from device i1 is relayed through UAVs u1 and u2 sequentially to bypass LoS blockages caused by urban structures B. UAV u3 remains on standby.
accommodates both relay-transmit and direct uploading. These roles are mutually exclusive, satisfying:
ρc
m(t) + ρr,rx
m (t) + ρtx
m(t) ≤ 1, ∀m, t (4)
where setting a variable to 1 indicates the active role. If all are 0, the UAV is in a passive (flying or hovering) state. The specific transmission content (relayed data or final upload) will be determined by data flow and scheduling constraints. The scenario of UAV-assisted data collection is shown in Fig. 1.
B. Communication Model
We adopt an urban Air-to-Ground (A2G) [37] and Air-toAir (A2A) [38], [39] channel model dependent on geometric parameters. The Euclidean distance dn,m(t) and elevation angle θn,m(t) are:
dn,m(t) =
√
(xm(t) − xn)2 + (ym(t) − yn)2 + hm(t)2 (5)
θn,m(t) = tan−1
(
hm(t)
√
(xm(t) − xn)2 + (ym(t) − yn)2
)
(6)
We assume a scenario where a known 3D map of the primary obstacles represented as B = {b1, . . ., bK } is available. Consequently, the LoS or Non-Line-of-Sight (NLoS) status of a link is determined by the UAV’s instantaneous position. We define a binary indicator variable χn,m(t) to represent the LoS status of the link between IoT device in and UAV um at time slot t. The link is considered LoS if the straight line segment connecting the device and the UAV, denoted by `n,m(t), does not intersect with any obstacle region Rbk corresponding to bk ∈ B:
χn,m(t) =
{
1, if `n,m(t) ∩
(⋃
bk∈B Rbk
)
=∅
0, otherwise (7)
where χn,m(t) = 1 signifies an LoS link and χn,m(t) = 0 signifies an NLoS link. Channel quality is characterized by the path loss, which is state-dependent on the LoS condition. For an A2G link
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9487
between device in and UAV um, the path loss Ln,m(t) in dB is modelled as:
Ln,m(t) = 20 log10
( 4πfcdn,m(t) c
)
+ ηn,m(t), (8)
where fc is the carrier frequency, c is the speed of light. The excess path loss ηn,m(t) is:
ηn,m(t) = (1 − χn,m(t))ηNLoS + χn,m(t)ηLoS, (9)
where ηLoS and ηNLoS are additional attenuation values for LoS and NLoS links, respectively. The channel power gain
is then hn,m(t) = 10
−Ln,m (t)
10 . The instantaneous data rate Rn,m(t) is determined by the Signal-to-Interference-plusNoise Ratio:
Rn,m(t) = BA2G log2
(
1 + PIoTGt,IoTGr,UAVhn,m(t)
σ2 + InA,2mG(t)
)
,
(10)
where BA2G is the channel bandwidth, PIoT is the transmit power of IoT devices, Gt,IoT and Gr,UAV are the antenna gains of the IoT device and UAV, respectively, and σ2 is the thermal noise power. The term IA2G
n,m(t) represents the aggregate interference. Let the binary scheduling variable an,m(t) indicate if UAV um serves device in at time t. We require each UAV to serve at most one device per time slot:
∑
n∈I an,m(t) ≤ 1, ∀m, t. To ensure fairness, each IoT device can be served by at most one UAV at any given time:
∑
m∈U an,m(t) ≤ 1, ∀n, t. A service action is only possible if the UAV is in a receiving role:
an,m(t) ≤ ρc
m(t) + ρr,rx
m (t), ∀n, m, t (11)
Based on these scheduling and role definitions, the aggregate interference IA2G
n,m(t) experienced by the receiving UAV um can be formulated as:
I A2G
n,m(t) =
∑
n′ ∈I ,m′ ∈U (n′ ,m′ )6=(n,m)
an′,m′ (t)PIoTGt,IoTGr,UAVdn′,m(t)−α
+
∑
m′ ∈U
ρtx
m′ (t)PtGt,UAVGr,UAVdm′,m(t)−αA2A ,
(12)
where Pt denotes the UAV transmit power, Gt,UAV and Gr,UAV represent the UAV transmission and reception antenna gains, respectively. α and αA2A are the path loss exponents for A2G and A2A links. To manage concurrent access among multiple UAVs the system employs Orthogonal Frequency Division Multiple Access and dynamically allocates a set of Nc available orthogonal channels to the active air to ground collection links at each control step. When the number of concurrent collection links is less than or equal to Nc channels are assigned orthogonally to completely avert cochannel interference. Conversely when the concurrent links exceed Nc the channels are iteratively reused via a cyclic modulo operation. Any resulting unavoidable cochannel interference from this dynamic frequency reuse along with the transmission interference from UAVs in the transmitting role is explicitly incorporated into the aggregate
interference term IA2G
n,m(t) to precisely calculate the practical data rate. Remark 1: A simplified power-law path loss model is used for the interference term in(12). This is a deliberate simplification to maintain the tractability of the optimization problem, particularly for the upper-level MILP formulation after linearization. Incorporating the more detailed LoS/NLoSdependent path loss model from(10)into the aggregate interference term would introduce significant non-convexity, making a real-time solution infeasible. Next, to characterize the backhaul performance, the Air-toAir (A2A) path loss between UAV um and um′ is modelled using the FSPL model:
Lm,m′ (t) = 20 log10
( 4πfcdm,m′ (t) c
)
. (13)
The achievable data rate Rm,m′ (t) on the A2A link is:
Rm,m′ (t)
= BA2A log2

1 + PtGt,UAVGr,UAV10
−Lm,m′ (t) 10
σ2 + IA2A
m,m′ (t)

 , (14)
where BA2A is the A2A channel bandwidth, and IA2A
m,m′ (t) is the aggregate interference experienced at the receiving UAV um′ .
C. Energy Model
The total power consumption of UAV um at time slot t, Pm(t), consists of propulsion and communication power. The
propulsion power P prop
m (t) = Ph + P move
m (t), where Ph is the
constant hovering power and P move
m (t) is the movement-related power, for which we adopt a tractable quadratic approximation: P move
m (t) ≈ cm‖vm(t)‖2, with cm representing the propulsion power coefficient.The communication power is primarily consumed during transmission: P comm
m (t) = ρtx
m(t)Pt. The cumulative energy must not exceed the battery capacity:
T −1
∑
t=0
(
Ph + cm
‖pm(t+1) − pm(t)‖2
(∆t)2 + ρtx
m(t)Pt
)
∆t
≤ Emax
m (15)
D. Cooperative Relay and Data Flow Model
Let S denote the ground server, which acts as the final data sink. Let cn,m,m′ (t) ∈ {0, 1} be a binary scheduling variable, where cn,m,m′ (t) = 1 if UAV um transmits data originating from device in to UAV um′ . Let cn,m,S(t) = 1 denote the final upload from UAV um to the server S. The A2A link between um and um′ must be LoS:
cn,m,m′ (t) ≤ χm,m′ (t), ∀n, m, m′, t (16)
where χm,m′ (t) is the A2A LoS indicator. To model the data flow, we introduce Dn,m(t) as the amount of data from device in stored at UAV um at the beginning of slot t. The data conservation principle dictates:
Dn,m(t + 1) = Dn,m(t) + ∆t an,m(t)Rn,m(t)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

9488 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
+ ∆t
∑
m′ 6=m
cn,m′,m(t)Rm′,m(t) − ∆t cn,m,S (t)Rm,S (t)
− ∆t
∑
m′′ 6=m
cn,m,m′′ (t)Rm,m′′ (t) (17)
The cumulative data uploaded must satisfy:
T
∑
t=0
∑
m∈U
cn,m,S(t)Rm,S(t)∆t ≥ Sn, ∀n ∈ I (18)
where the completion time for device in, denoted χn, is the first time slot t by which (18) is satisfied for that device, and it must be before the deadline δn.
E. Problem Formulation
Our primary objective is to minimize the mission completion time, equivalent to minimizing the maximum data completion time among all IoT devices.
min Tmax
s.t. χn ≤ Tmax, ∀n ∈ I. (19)
We denote P = {pm(t)}, A = {an,m(t)}, C = {cn,m,m′ (t), cn,m,S (t)}, and R = {ρ·
m(t)} be the sets of optimization variables. The overall optimization problem is:
(P1): min
P ,A,C ,R,Tmax
Tmax
s.t. χn ≤ δn, ∀n ∈ I (20a)
χn ≤ Tmax, ∀n ∈ I (20b)
an,m(t) ≤ χn,m(t), ∀n, m, t (20c)
cn,m,m′ (t) ≤ χm,m′ (t), ∀n, m, m′, t
(1)−(4), (10)−(11), (15)−(18) (20d)
IV. THE PROPOSED HOC-UADC METHOD
We decouple the problem into two main components operating on different timescales and levels of abstraction. The high-level component, the Global Mission Planner (GMP), confronts the combinatorial complexity of multi-UAV task allocation and coarse routing. The purpose of solving a tractable MILP approximation is to ensure long-term, fleetwide strategic effectiveness. Guided by the GMP, the low-level component, the Local Trajectory Optimizer (LTO), addresses the non-linear dynamics and continuous control for each UAV. It generates physically feasible and locally optimal trajectories by solving an NMPC problem, ensuring safe and precise execution in the immediate environment.
A. Cooperative Task Allocation and Relay Path Planning
To address this, we use GMP to transform (P1) into a tractable MILP approximation. This MILP captures the essential strategic trade-offs and is embedded within RHC framework for adaptive, closed-loop decision-making. The following details the key linearization techniques and the resulting MILP formulation. To handle the non-convex communication rate models, we approximate the continuous rate-distance relationship with a piecewise linear function. We define i, j ∈ K as general nodes
in the abstracted communication network (K = I ∪ U ∪ {S}). The continuous distance between these nodes, denoted dij(t), is approximated by mapping it to a set of predefined distance intervals. A set of binary variables λij,k(t) selects one of K predefined rate segments Rˆk, yielding a linear rate expression:
R ̄ij(t) =
K
∑
k=1
λij,k(t)Rˆk (21)
A uniqueness constraint ensures that at most one rate segment is active for any link at any time:
K
∑
k=1
λij,k(t) ≤ 1, ∀i, j, t (22)
We use standard Big-M formulation in (23) and (24), then links the selection of rate segment k to a corresponding permissible distance range [Dmin
k , Dmax
k ] between pre-defined waypoints.
dij (t) ≥ Dmin
k − M(1 − λij,k(t)), ∀i, j, k, t (23)
dij (t) ≤ Dmax
k + M(1 − λij,k(t)), ∀i, j, k, t (24)
where M is a sufficiently large positive constant. Proposition 1 (Upper-bound of Linearization Error): The piecewise linear approximation of the logarithmic rate function R = log2(1 + x) in (21) introduces a truncation error. For each segment [xk, xk+1], the maximum absolute error max is bounded by:
max = max
x∈[xk ,xk+1 ]
|log2(1 + x) − (akx + bk)|
≤ (xk+1 − xk)2
8 ln 2(1 + xk)2 . (25)
Proof: Since f (x) = log2(1 + x) is strictly concave, the linear interpolation L(x) over [xk, xk+1] lies below f (x). According to the second-order Taylor residual formula, the error e(x) is bounded by 1
8 (xk+1 − xk)2 max |f ′′(x)|. Substi
tuting f ′′(x) = −1
ln 2(1+x)2 , the maximum error occurs at the segment’s lower bound xk, yielding the result. By increasing the number of segments K, this error can be made arbitrarily small. Furthermore, within the RHC framework, these local approximation inaccuracies are effectively compensated by the continuous closed-loop feedback mechanism, ensuring the long-term feasibility of the generated trajectories. Similarly, the non-convex cumulative energy constraint from (15), which contains a quadratic propulsion power term, is addressed by replacing the instantaneous power with a linearized, aggregate propulsion energy cost, denoted E ̄P
ab,
for traversing between waypoints[40]. Following established models, we approximate this energy as a linear function of travel distance and time:
E ̄ P
ab = cpdab + chtab (26)
where cp and ch are coefficients for distance- and timedependent propulsion energy, respectively. By systematically applying these linearization techniques, the strategic planning problem is formulated as a tractable
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9489
MILP defined over decision variables that transform the complex continuous and discrete choices of (P1) into a unified strategic model. First, the binary variable xn,m ∈ {0, 1} governs the highlevel assignment of task n to a primary UAV um. Second, the spatio-temporal state of the fleet is discretized using ym,k,t ∈ {0, 1}, which indicates if UAV um is located at waypoint k ∈ W at time step t. Third, a unified binary flow variable, fi,j,n,t ∈ {0, 1}, represents multi-hop routing decisions by indicating if data for task n is relayed from node i to node j at time step t. This variable effectively abstracts the detailed scheduling decisions an,m(t), cn,m,m′ (t) into a cohesive network flow framework, where nodes i, j can represent IoT devices, UAVs, or the server. Finally, the continuous variable χn tracks the completion time for each task n. Consistent with (19), the MILP aims to minimize the mission makespan Tmax, which is defined as the maximum time required for task completion. The MILP is governed by the following key constraints, which are the linearized and discretized counterparts of those in (P1):
1) Task Assignment and Timing Constraints: These constraints ensure that each task is assigned to exactly one primary UAV (27), and that all task completion times respect the predefined deadlines (28) and data release times (29).
M
∑
m=1
xn,m = 1, ∀n ∈ I (27)
χn ≤ δn, ∀n ∈ I (28)
fi,j,n,t = 0, ∀i, j, n, if t · ∆t < τn (29)
2) Data Flow and Collection Constraints: Let K = I ∪ U ∪{S} denote the set of all network nodes. The flow variable fi,j,n,t is used to enforce data conservation at each relay node (UAV), mirroring (17). Furthermore, the total data transmitted from each source device, weighted by the linearized link rates, must meet the task’s requirement Sn from (18).
∑
i∈K,i6=um
fi,m,n,t =
∑
j∈K,j6=um
fm,j,n,t, ∀m, n, t (30)
T
∑
t=0
∑
j∈U
(
fin,j,n,t · R ̄in,j (t) · ∆t
)
≥ Sn, ∀n ∈ I (31)
3) UAV Mobility and Energy Constraints: The waypoint variables ym,k,t must form valid trajectories, ensuring that each UAV occupies at most one waypoint per time step and that transitions between waypoints are physically feasible. The linearized energy constraint contains a quadratic term ym,k1,tym,k2,t+1 due to the product of two binary variables. To maintain the linearity of the MILP, we introduce an auxiliary binary variable zm,k1,k2,t = ym,k1,t · ym,k2,t+1, which is 1 if and only if the UAV m transitions from waypoint k1 at time t to waypoint k2 at time t + 1. The following set of linear constraints enforces this relationship:
zm,k1,k2,t ≤ ym,k1,t (32)
zm,k1,k2,t ≤ ym,k2,t+1 (33)
zm,k1,k2,t ≥ ym,k1,t + ym,k2,t+1 − 1 (34)
The total energy budget constraint is then reformulated as a linear constraint:
T −1
∑
t=0
∑
k1 ,k2 ∈W
zm,k1 ,k2 ,t E ̄ P
k1,k2 +
∑
t,i,j,n
fi,j,n,tPt∆t ≤ Emax
m.
(35)
Algorithm 1 Global Mission Planner (GMP) With Receding Horizon Control Require: Initial state S0 = {pm(0), Erem
m (0)}, initial task set I0, control interval TS, prediction horizon TH . Ensure: Sequence of strategic plans {Π∗(τk)}. 1: Initialize: τk ← 0, T ← I0, Πprev ← ∅. 2: while mission is not complete do 3: State Measurement:
4: Obtain current UAV states and task execution status. 5: Strategic Re-Optimization:
6: Formulate the MILP over horizon [τk, τk + TH ] based on state Sk. 7: Solve the MILP under a prescribed time budget. 8: if a feasible solution is obtained then 9: Π∗(τk) ← Πopt(τk) 10: Πprev ← Π∗(τk) 11: else
12: Π∗(τk) ← Πprev 13: end if 14: Plan Dispatch:
15: Dispatch the first segment of Π∗(τk) for interval [τk, τk + TS]. 16: τk ← τk + TS . 17: end while 18: return {Π∗(τk)}.
To instill robustness, the GMP is implemented within an RHC scheme. At each control interval TS, the GMP re-solves the MILP with updated system states, generating a new optimal plan Π∗ for a prediction horizon TH . The process is detailed in Algorithm 1. Each plan Π∗ contains the optimal task assignments (xn,m), waypoint sequence (ym,k,t), and data flow routes (fi,j,n,t) for the horizon. Remark 2: The feasibility of the proposed HOC-UADC framework under these restricted conditions is supported by two primary factors. First, the control signaling required for the GMP (status vectors and tactical indices) is several orders of magnitude smaller than the actual mission data traffic. This disparity ensures that the strategic layer remains resilient even when operating on bandwidth-limited control channels. Second, the RHC mechanism provides inherent robustness. If a periodic strategic update is missed due to transient link failure, UAVs can continue executing the previously optimized trajectories from their plan buffers. This temporal buffering ensures operational continuity until the next successful synchronization epoch restores global coordination.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

9490 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
B. Real-Time Trajectory Generation and Role Control
GMP provides long-term, strategic directives to the LTO of each individual UAV. In this part, we use LTO to translate the coarse strategic plan into a dynamically feasible and locally optimal continuous trajectory, ensuring precise execution and real-time responsiveness to immediate physical constraints and dynamic link qualities. To achieve this, the LTO for each UAV um utilizes a secondorder kinematic model. The state vector is defined as xm(k) = [pm(k)T , vm(k)T ]T ∈ R6, comprising the 3D position and velocity. The control input is the 3D acceleration, um(k) = am(k) ∈ R3. The dynamics are governed by:
xm(k + 1) = Axm(k) + Bum(k) (36)
where A =
[I ∆tlI 0I
]
and B =
[
(∆tl )2
2I ∆tlI
]
, with I being
the 3 × 3 identity matrix and ∆tl the local control interval. Then the LTO solves the following NMPC problem for each UAV um over its local prediction horizon, which is discretized into Kp steps. Based on the conceptions, we can formualte:
min
{xm (k),um (k)}Kp −1
k=0
Kp −1
∑
k=0
(
‖pm(k) − p∗
m‖2
Q
−wRRm(pm(k)) + ‖um(k)‖2
R
)
+ ‖pm(Kp) − p∗
m‖2
Qf
s.t. xm(k + 1)=f (xm(k), um(k)), ∀k ∈ Kp (37a)
xm(0) = xms
m (37b)
hmin ≤ hm(k) ≤ hmax, ∀k ∈ K+
p (37c)
‖vm(k)‖ ≤ vmax, ‖um(k)‖ ≤ amax, ∀k ∈ Kp (37d)
Kp −1
∑
k=0
Pm(·)∆tl ≤ Erem
m (τk) (37e)
pm(k) ∈/
⋃
b∈B
Interior(b), ∀k ∈ K+
p (37f)
where Jm is the cost function, wR is a weighting coefficient that balances the communication rate reward and waypoint p∗
m is derived from the GMP’s strategic plan and serves as the long-term abstract goal for the UAV. Rm(·) is the position-dependent link rate function, which is conditionally set by the current active role s∗ as determined by the role coordination scheme in (40). Q, R, and Qf are positive semidefinite weighting matrices. The constraints in (37) define the local, real-time nature of the LTO’s task. Specifically, the trajectory is anchored to the UAV’s currently measured state xms
m (37b) and must evolve according to the physical dynamics (37a). The plan must adhere to all physical safety limits, including altitude (37c), velocity/acceleration (37d), and collision avoidance with known obstacles (37f). Local energy constraint (37e) ensures the planned short-term maneuver is feasible given the UAV’s currently remaining energy
E rem
m (τk). These physics-based constraints replace the global logistical constraints which the GMP handles. To solve this non-convex NMPC problem in real-time, we employ SCP [41]. At each SCP iteration, non-convex terms are convexified around the solution from the previous iteration. Specifically,
the communication rate term is linearized via a first-order Taylor expansion:
Rˆ(j)
m (pm(k)) = ∇pRm(p ̃(j−1)
m (k))T (pm(k) − p ̃(j−1)
m (k))
+ Rm(p ̃(j−1)
m (k)) (38)
The non-convex obstacle avoidance constraint (37f) is convexified into a linear half-space constraint:
(p ̃ (j −1)
m (k) − oc)T (pm(k) − p ̃(j−1)
m (k)) ≥ 0 (39)
where oc denotes the center coordinates of the obstacle involved in the constraint. By providing a more favorable strategic waypoint sequence, the GMP can reshape the reference p∗
m before the UAV is driven deeply into a geometrically unfavorable region, thereby reducing the risk that the SCP-based LTO stagnates near obstacle boundaries under purely local half-space convexification. Finally, we transform NMPC into a sequence of efficiently solvable convex Quadratically Constrained Quadratic Programs [42] (QCQPs) within a trust region ∆u.
Lemma 1 Convergence of Sequential Convex Programming: Consider the non-convex NMPC optimization problem defined in (37). Assume the objective and constraint functions are continuously differentiable and their gradients are Lipschitz continuous. If the fixed trust region radius ∆u is chosen to be sufficiently small, the sequence of solutions {x(j)} generated by the SCP algorithm monotonically decreases the objective function value and converges to a Karush-Kuhn-Tucker (KKT) point of the original problem. Proof: Let the original NMPC problem be denoted as minx J(x) subject to gi(x) ≤ 0, ∀i. At iteration j, the SCP algorithm constructs a convex subproblem by replacing nonconvex terms with their first-order Taylor expansions around the previous point x(j−1). By definition, the resulting convex approximations, denoted J ̃(j) and g ̃(j)
i , satisfy first-order
consistency at the expansion point: J ̃(j)(x(j−1)) = J (x(j−1)) and ∇J ̃(j)(x(j−1)) = ∇J (x(j−1)), with analogous equalities holding for the constraint functions. The algorithm then minimizes J ̃(j)(x) within a trust region ‖x − x(j−1)‖ ≤ ∆u. Since the previous iterate x(j−1) is a feasible solution to this subproblem with zero displacement, the optimal solution x(j) yields J ̃(j)(x(j)) ≤ J ̃(j)(x(j−1)). Provided the fixed trust region radius ∆u is sufficiently small relative to the Lipschitz constant of the gradients, the reduction in the convex approximation dominates the second-order Taylor remainder. Consequently, the actual cost decreases monotonically, i.e., J (x(j)) < J (x(j−1)), unless
x(j) = x(j−1).
Since the feasible set is compact and the objective is bounded below, the sequence of objective values must converge. Let x∗ be the limit point of the sequence {x(j)}. At convergence, x∗ is the optimal solution to the convex subproblem centered at itself. Due to the first-order consistency established above, the gradients of the approximation match the gradients of the original functions at x∗. Therefore, the KKT multipliers that satisfy the stationarity conditions for the subproblem also satisfy the stationarity, primal feasibility, and complementary slackness conditions for the original problem. Thus, x∗ is a KKT point of the original NMPC problem.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9491
From Lemma1, we can directly infer the quality of the solution obtained by the LTO’s solver for the NMPC subproblem. Corollary 1: [Local Optimality of LTO Solution] The trajectory {x∗
m} obtained by the SCP solver (Algorithm 2) upon convergence is a locally optimal solution to the non-convex NMPC problem defined in (37), provided that the problem satisfies standard second-order sufficiency conditions at the point of convergence. Proof: Let x∗ be the point of convergence. From Lemma 1, x∗ is a KKT point of the NMPC problem (37). Let L(x, λ, μ) be the Lagrangian of the problem. By definition, the KKT conditions are satisfied at x∗, meaning there exist multipliers λ∗ ≥ 0 and μ∗ such that ∇xL(x∗, λ∗, μ∗) = 0, all constraints are met, and dual feasibility as well as complementary slackness hold. These are the first-order necessary conditions for local optimality. If, in addition, the second-order sufficiency condition holds at x∗, then x∗ is guaranteed to be a strict local minimum.
Algorithm 2 Sequential Convex Programming (SCP) Solver Require: NMPC problem PNMPC, initial guess ̃x0, tolerance SCP, max iterations J mx, trust region radius ∆u. Ensure: Optimal trajectory {x∗
m}, controls {u∗
m}, cost J ∗.
1: Initialize: iteration j ← 0, nominal trajectory ( ̃x(0)
m , u ̃(0)
m ). 2: repeat
3: j ← j + 1. 4: Convexify: Linearize non-convex terms(38),(39) around (x ̃(j−1)
m , u ̃(j−1)
m ) to form a QCQP subproblem. 5: Solve the subproblem to find candidate (x(j)
m , u(j)
m ). 6: Update the nominal trajectory (x ̃(j)
m , u ̃(j)
m ) based on cost improvement and trust region logic. 7: until convergence criterion met or j > Jmx 8: return Converged trajectory {x∗
m} ← x ̃(j)
m , controls {u∗
m} ← u ̃(j)
m , and cost J ∗ ← J (j).
Corollary1provides a formal guarantee on the quality of the high-fidelity trajectory generated by each LTO at every control step. The detailed workflow of the SCP solver is presented in Algorithm2. The LTO must determine not only the UAV’s physical trajectory but also its functional role, as constrained by (4). This creates a hybrid discrete-continuous optimization problem. To solve this tractably, we propose an embedded combinatorial scheme that decouples the discrete role selection from the continuous trajectory optimization. At each decision step, the LTO first identifies a small set of feasible candidate roles, Sm, based on the strategic directive from the GMP. For each candidate role s ∈ Sm, it solves the whole NMPC problem using SCP, yielding a corresponding optimal trajectory cost, Js,∗
m . To ensure system stability, a switching penalty ηs > 0 is introduced to quantify the operational overhead of mode transitions, such as control reconfiguration latency. Theoretically, this penalty serves as a regularization term that induces hysteresis to prevent high-frequency oscillations between roles. The final decision is therefore made by selecting the role that minimizes an augmented cost, which is the sum of the trajectory cost and
Algorithm 3 Local Trajectory Optimizer (LTO) for UAV um
Require: Current state xm(τk), strategic directive Dm(τk), local horizon Tp, local time step ∆tl, SCP tolerance SCP, max iterations Jmx. Ensure: Optimal control input u∗
m(τk) and role s∗.
1: Initialize: optimal cost J∗ ← ∞, s∗ ← null. 2: Identify candidate roles Sm based on directive Dm(τk). 3: for each candidate role s ∈ Sm do 4: Formulate the NMPC problem in (37) for role s. 5: Solve NMPC using SCP: 6: [{xs,∗
m }, {us,∗
m }, J s,∗
m ] ← Algorithm 2.
7: Calculate augmented cost ζs using (40). 8: if ζs < J ∗ then
9: J ∗ ← ζs, s∗ ← s, u∗
m(τk) ← us,∗
m (0). 10: end if 11: end for 12: return u∗
m(τk), s∗.
the switching penalty. This selection criterion is formalized as:
s∗ = arg min
s∈Sm
(
J s,∗
m + ηs · I(s 6= s−
m)
)
(40)
where s∗ is the optimal role to be executed, s−
m is the UAV’s active role from the previous time step, and I(·) is the indicator function, which is 1 if the condition inside is true, and 0 otherwise. This LTO process is summarized in Algorithm 3.
C. Overall Algorithm and Complexity Analysis
The complete operational flow of HOC-UADC is summarized in Algorithm 4, which orchestrates the GMP and the LTOs through a continuous receding horizon mechanism. Upon completion, the algorithm returns the optimized trajectory set P and role schedule R, alongside the recorded control inputs Uctrl required for precise energy consumption evaluation. To theoretically justify the real-time performance of the proposed framework, we analyze the computational complexity of its hierarchical components: the strategic GMP, the local LTO, and the underlying SCP solver. The computational load of the strategic layer is determined by the GMP, which solves a MILP at each interval TS. The scale of this problem is primarily governed by the number of binary decision variables, which is on the order of O(M N + M |W|TH ), where M , N , |W|, and TH denote the number of UAVs, tasks, waypoints, and the prediction horizon, respectively. Although general MILP problems are NP-hard, the specific formulation in our framework exhibits a sparse network-flow structure. Consequently, modern branch-and-bound solvers can typically leverage this sparsity to achieve an average-case polynomial time complexity with respect to the task number N , ensuring that high-quality strategic plans are generated within the allotted time budget TS. At the trajectory level, the computational burden is distributed across parallel LTO instances for each UAV. Each LTO solves a local NMPC subproblem using the SCP algorithm. The complexity of a single SCP iteration, solved via interiorpoint methods, is approximately O(V 3.5
L ), where VL represents
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

9492 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Algorithm 4 Hierarchical Optimal Control for UAV-Assisted Data Collection (HOC-UADC) Require: Initial system state S0, total mission time T , strategic interval TS, local interval ∆tl. Ensure: Trajectory set P, role schedule R, and control inputs
Uctrl.
1: Initialize: τ ← 0, P ← ∅, R ← ∅, Uctrl ← ∅, Iτ ← I. 2: while τ < T do 3: GMP Execution (every TS): 4: if τ (mod TS) == 0 then
5: Observe fleet state Sτ ← {pm(τ ), Erem
m (τ )}∀m. 6: Pending:
7: Task set Iτ ← {n ∈ I | task n is incomplete}. 8: Call Algorithm 1 with Sτ , Iτ to compute strategic plan Π∗(τ ). 9: Generate directives Dm(τ ) from Π∗(τ ). 10: end if 11: LTO Execution (every ∆tl):
12: for each UAV um ∈ U in parallel do 13: Measure local state xm(τ ). 14: Call Algorithm 3 with xm(τ ) and Dm(τ ). 15: Obtain optimal control u∗
m(τ ) and role s∗
m(τ ).
16: Apply control u∗
m(τ ) to UAV dynamics. 17: Record:
18: P ← P ∪ {pm(τ )} 19: R ← R ∪ {s∗
m(τ )}
20: Uctrl ← Uctrl ∪ {u∗
m(τ )} 21: end for
22: τ ← τ + ∆tl. 23: end while 24: return P, R, Uctrl.
the number of local decision variables. Crucially, VL depends solely on the local horizon and is strictly independent of the global task count N . Furthermore, the receding horizon implementation enables efficient warm-starting, which constrains the SCP solver to converge within a bounded number of iterations J. This ensures that the total complexity per control step, O(M ·J ·V 3.5
L ), remains low and deterministic, satisfying the rigorous requirements for real-time deployment. Synthesizing these analyses, the total time complexity of the HOC-UADC framework is characterized by the superposition of the strategic and trajectory layers. Since the parallel LTOs operate with complexity independent of task scale, and the GMP exhibits average-case polynomial scaling, the overall system complexity is theoretically polynomial with respect to N (O(poly(N ))).
V. EXPERIMENTAL RESULTS
In this section, we conduct extensive simulations to evaluate the performance of our proposed HOC-UADC method.
A. Simulation Settings and Datasets Details
The experiments are conducted in a custom-built Python simulator that models a 3D urban environment with buildings as obstacles. To ensure a high-fidelity performance evaluation,
the simulator implements the building-aware channel model defined in Section III to assess the strategic and trajectory plans generated by the optimization layers. To rigorously test the adaptability and performance of the algorithms, we designed two distinct scenarios based on real-world map data. 1) Geographic Scenarios: The building layouts for both scenarios are generated using the OSMnx library from realworld OpenStreetMap data.1 The area of both scenarios is kept identical to ensure a fair comparison of density effects. We designed two distinct scenarios to rigorously test the algorithms’ adaptability. The Dense Urban Scenario is modeled after a real-world 0.55 × 0.55 km2 area of downtown Palo Alto, CA, USA. The simulation includes 296 buildings, whose heights are programmatically generated following a uniform distribution between 20 m and 80 m to represent a typical city center with significant LoS blockage challenges. In contrast, the Sparse Suburban Scenario is based on a same-sized area in the suburban foothills west of Palo Alto. This area contains 19 buildings, with heights uniformly distributed between 2 m and 8 m, representing a rural setting with minimal LoS obstructions. This scenario primarily tests the algorithms’ efficiency in large-scale path planning and fleet coordination. 2) Task and UAV Datasets: To analyze the scalability of the competing algorithms, the number of IoT tasks N is systematically varied from 15 to 80 for each scenario. The tasks in the set I are sequentially selected from a pre-generated primary dataset where locations are randomly distributed on the ground within the operational area. Each task n ∈ I is characterized by a unique data packet size Sn, which ranges from approximately 25 to 35 Mbits, and must be collected before a hard deadline δn. All tasks are available for service from the mission start time, i.e., t = 0. Similarly, the initial positions pm[0] for the UAVs in the fleet U are fixed by sequentially loading from a configuration file containing randomly initialized coordinates. Table I summarizes the key system models and simulation parameters used in our experiments. The UAV propulsion energy model is adapted from a standard multi-rotor model [43], communication channel parameters are selected based on a widely-used A2G path loss model [44], noise power is set to a typical value for urban macro-cell scenarios with 3GPP TR 36.814,2 respectively.
B. Selected Baseline Algorithms
To benchmark the performance of our proposed method, we implement and compare against five baseline algorithms, categorized by their underlying methodology, and include four ablation variants of our own method to analyze its components. 1) Decomposition-Based Optimization Algorithms: These algorithms address the joint optimization problem by decomposing it into more manageable subproblems that are solved iteratively. a) AoI-EaTO [22]: The AoI-and-Energy-aware Trajectory Optimization algorithm is formulated to minimize the
1https://www.openstreetmap.org 2https://portal.3gpp.org/desktopmodules/Specifications/ SpecificationDetails.aspx?specificationId=2493
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9493
TABLE I
UAV, COMMUNICATION, AND ALGORITHM PARAMETERS
UAV’s mission completion time by jointly optimizing flying speeds, hovering positions, and the visiting sequence. Its computational complexity is approximately O(L4((L1(2N + 2)3.5 + L3(5N )3.5) · log(1/ ) + M N + lmax(2M N + 3M ))).
b) MinTime-TCO[21]: The Minimum Completion Time Trajectory and Charging Optimization algorithm is proposed for a laser-powered data-gathering UAV, with the objective of minimizing the total task completion time. The complexity of its core component is O((8J)3 ln(1/ )).
2) Metaheuristic Algorithms: Including population-based and neighborhood-search algorithms that are effective for complex, large-scale optimization problems.
a) MACO-NOTM [23]: The Modified Ant Colony Optimization for Number and Operation Time Minimization algorithm aims to jointly minimize the number and total operation time of UAVs. It decomposes the problem and uses a modified ant colony optimization algorithm to solve the trajectory subproblem, with a complexity of roughly O(log(1/ )M 2).
b) GA [17]: A Genetic Algorithm evolves a population of candidate solutions using selection, crossover, and mutation.
Its time complexity is pseudo-polynomial, typically O(Iga · Npop · L).
c) PSO [18]: Particle Swarm Optimization iteratively improves a population of candidate solutions based on the swarm’s best-known positions. Its computational complexity is typically O(Ipso · Np · D).
3) Learning-Based Algorithms:
a) MA-HPPO [45]: The Multi-Agent Hybrid Proximal Policy Optimization algorithm is proposed for multi-UAV data collection in wireless sensor networks, aiming to maximize the total collected data while minimizing the overall energy consumption by learning cooperative trajectory control and task execution policies.
4) Ablation Study Variants: To isolate and quantify the contribution of each key component of our framework, we evaluate the following four degraded variants: a) HOC-UADC w/o GMP: This variant replaces the high-level MILP-based strategic planner with a simple greedy heuristic [46] that assigns the closest available UAV to the next unassigned task. It is designed to demonstrate the value of strategic foresight. b) HOC-UADC w/o NMPC: In this version, the real-time trajectory optimizer is replaced by a simple waypointfollowing controller that flies in a straight line between waypoints. This variant tests the importance of physics-aware, real-time trajectory generation. c) HOC-UADC w/o RHC: This variant executes the initial GMP plan in an open-loop fashion, without the RHC mechanism for periodic re-planning. It highlights the role of RHC in adapting to dynamic changes and accumulated errors.
d) HOC-UADC w/o Role-Switching: UAVs are assigned fixed roles at the start of the mission and cannot change them. This tests the benefit of dynamic functional flexibility.
C. Performance Evaluation Metrics
To quantitatively evaluate the performance of the proposed framework, we define two key evaluation metrics.
1) Data Delivery Success Ratio (Rs): This metric evaluates the reliability of the algorithm, quantifying the fraction of tasks successfully completed within their respective deadlines δn. A higher ratio indicates greater robustness in meeting QoS requirements.
Rs = 1
N
∑
n∈I
I [χn ≤ δn] (41)
2) computation Time (Tc): A lower computation time signifies a more efficient algorithm, better suited for dynamic environments that may require rapid re-planning.
D. Performance Comparison With Baselines
In this section, we present a series of simulations designed to validate the effectiveness of HOC-UADC in Dense Urban Scenario and Sparse Urban Scenario. We account for the stochastic nature of metaheuristic algorithms, MinTime-TCO, and learning-based methods by executing each of them five times per scenario and reporting
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

9494 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 2. Performance comparison in the dense urban scenario for M = 8 (top row) and M = 10 (bottom row) UAVs.
the average performance. Shaded areas in our plots represent the standard deviation across these runs. In contrast, deterministic baseline algorithms require only a single execution per scenario. As systematically illustrated in Fig. 2 across varying task scales (N = 15 to 80), HOC-UADC consistently achieves the lowest or near-lowest mission completion time Tmax. While the learning-based MA-HPPO also delivers competitive completion times, this speed comes at the cost of the task success rate, resulting in higher performance variance and suboptimal routing due to the lack of hard constraint enforcement. HOC-UADC’s superiority is particularly evident in the dense urban scenario, a problem characteristic defined by numerous obstacles that severely constrain the trajectory solution space. By effectively decoupling high-level task allocation from low-level trajectory optimization, HOCUADC enables globally aware decisions that mitigate the high combinatorial complexity that overwhelms metaheuristic approaches like GA and PSO as N increases. Similarly, this hierarchical structure helps avoid the suboptimal local minima that decomposition-based methods are prone to in such nonconvex environments. It is noteworthy that the Tmax curves exhibit minor fluctuations rather than strict monotonicity with respect to N . We clarify that this behavior stems from the topological heterogeneity of the randomized task instances, where specific spatial clusterings in larger datasets occasionally enable more efficient routing than dispersed smaller sets. This performance advantage remains robust as the fleet size scales from 8 to 10 UAVs (as shown in Fig. 2(d)) and extends to sparse scenarios (Fig. 3), demonstrating the framework’s
scalability in handling both obstacle-constrained and longrange planning challenges. Next, we assess the operational reliability of each algorithm via the task success rate Rs. For time-critical missions, a high success rate is paramount. HOC-UADC exhibits exceptional robustness, consistently maintaining an Rs exceeding 0.98 across all task scales. This reliability is guaranteed by a synergy of strategic and tactical safeguards. The strategic layer performs feasibility-aware task allocation to rigorously prevent energy-infeasible assignments, while the trajectory layer enforces hard geometric constraints to ensure collisionfree flight. This dual mechanism effectively eliminates both planning dead-ends and execution failures. In contrast, learning-based methods like MA-HPPO lack this global validation, optimizing for expected rewards rather than guaranteed feasibility, which leads to occasional failures in complex scenarios. While metaheuristic approaches also show high reliability, their exhaustive search mechanism is computationally expensive. The limitations of several decomposition-based methods become apparent under increased load, especially when the environment characteristics are considered. In dense scenarios, the high obstacle density makes finding feasible collision-free paths difficult, which leads to a decline in Rs for AoI-EaTO and MinTime-TCO as the problem scales. However, in the less constrained sparse scenarios, the success rate for MinTime-TCO shows an upward trend. This suggests that with more tasks, the BCD-based optimizer has a larger solution space, making it easier to find trajectories that satisfy the strict energy causality constraints by breaking long-distance flights into shorter, more energy-feasible segments.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9495
Fig. 3. Performance comparison in the sparse urban scenario for M = 8 (top row) and M = 10 (bottom row) UAVs.
Fig. 4. Visualization of the optimized UAV trajectories generated by HOC-UADC in a dense urban scenario with N = 50 and M = 8.
Finally, we examine the computational time Tc as a function of the task scale N to address practical viability for largescale deployment. The results distinguish the algorithms into three scalability tiers. First, metaheuristic algorithms like GA and PSO suffer from exponential growth in Tc inherent to their population-based search. Their execution time surges from roughly 400 s for 15 tasks to over 2200 s for 80 tasks as shown in Fig.2(c), rendering them computationally prohibitive for real-time applications. Second, decompositionbased methods and MA-HPPO demonstrate exceptional speed due to problem simplification and rapid neural inference respectively, yet this efficiency compromises solution quality
and reliability. Third, HOC-UADC exhibits polynomial scalability consistent with the complexity analysis in SectionIV-C. Its computational cost grows in a controlled and near-linear manner, increasing from approximately 26 s for 15 tasks to 237 s for 80 tasks in the dense scenario. This confirms that our hierarchical decomposition successfully overcomes the curse of dimensionality by delivering high-quality and reliable solutions with an efficiency that remains tractable for large-scale real-world deployments. To offer a qualitative perspective on the solution’s structure, Fig. 4 visualizes the optimized trajectories for UAVs in dense scenario with 50 IoT devices.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

9496 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 5. Ablation for a dense scenario with N = 50 tasks and M = 8.
E. Ablation Study
To validate the contribution of each key component in our framework, we conducted an ablation study in a demanding dense urban scenario, featuring 50 IoT devices and 8 UAVs, the results of which are shown in Fig.5. The study highlights the indispensability of each module. The foremost requirement for any viable strategy is a high mission success rate. Our results show that core adaptive capabilities are non-negotiable. Both the HOC-UADC w/o Role-Switching and HOC-UADC w/o RHC variants experienced catastrophic failures, with success rates plummeting to 36%. Their low makespan values are artifacts of premature mission termination and are therefore not indicative of performance. It is also noteworthy that the HOC-UADC w/o Role-Switching variant incurred a very high computation time of 285.4s, suggesting the solver struggled to find feasible solutions without functional flexibility. Similarly, the HOCUADC w/o GMP variant, while faster, proved unreliable with a success rate of only 82%. For the variants that achieved a perfect 100% success rate, we perform a direct comparison of makespan. The full HOC-UADC completed the mission in 88.2s, whereas the HOC-UADC w/o NMPC variant required 90.9s. This comparison demonstrates that the NMPC-based trajectory optimization directly contributes to minimizing the mission completion time. In terms of computational cost, the full framework required 127.8s, outperforming the 136.0s needed by the variant without NMPC. This efficiency gain stems from the high-quality, dynamically feasible trajectories generated by NMPC, which streamline the problem for the upperlevel strategic planner. By providing locally optimal solutions, NMPC reduces the complexity of the global optimization, leading to faster overall convergence for the hierarchical system. In summary, for minimizing makespan, the full HOCUADC configuration is superior to all other reliable alternatives. While components like role-switching, RHC, and GMP are foundational for achieving a high success rate, the NMPC is the decisive element that reduces the final mission time while also improving the framework’s overall computational efficiency.
Fig. 6. Gantt chart illustrating the task allocation and execution timeline for each UAV generated by HOC-UADC in a dense scenario with N = 50 and M = 8.
Fig. 7. Sensitivity analysis of makespan with respect to strategic prediction horizon and control interval in a dense scenario with N = 50 and M = 8.
F. Qualitative Analysis
To provide a more intuitive understanding of our algorithm’s operational dynamics, Fig. 6 presents a Gantt chart visualizing the task schedule generated by HOC-UADC for a representative scenario. The chart illustrates how tasks are allocated to different UAVs over time. It clearly shows a high degree of concurrency, with multiple UAVs executing data collection tasks in parallel. The minimal white space in the timelines indicates low idle time for each UAV. Furthermore, the chart implicitly showcases the efficiency of the strategic planner, which effectively deconflicts routes and staggers task execution to maximize system throughput, leading to the short makespans observed in our quantitative results.
G. Parameter Sensitivity Analysis
1) Strategic and Local Control Time Scales: The strategic control interval (TS) and local control interval (∆tl) present a critical trade-off between mission performance and computational load, as shown in Fig. 7. A large TS or ∆tl reduces computational cost but degrades system responsiveness and control precision, respectively. Conversely, small intervals improve performance at the cost of frequent re-planning and computation. Our chosen parameters, TS = 12.15s and ∆tl = 0.9s, prioritize mission effectiveness by balancing strategic adaptability with fine-grained control, accepting a manageable computational load to minimize the overall makespan.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9497
Fig. 8. Sensitivity of NMPC numerical behavior to the trust-region radius ∆u in a dense scenario with N = 50 and M = 8.
Fig. 9. Evolution of the NMPC objective JNMPC over internal IPOPT iterations for five representative NMPC subproblems under ∆u = 5 (N = 50, M = 8).
2) Trust-Region Radius in the NMPC/LTO Layer: The local trajectory optimization is solved in a receding-horizon fashion using a warm-start control sequence shifted from the previous solution, with the control update regulated by the trust-region radius ∆u. Fig.8reports the NMPC numerical behavior under different ∆u, aggregated over five randomized problem instances and all NMPC subproblems, where the left vertical axis shows the solver success rate, and the right vertical axis shows the mean IPOPT iteration count and the 90th percentile of the normalized feasibility-based KKT error. As shown in Fig.8, increasing ∆u rapidly drives the solver success rate to unity, while both the iteration count and the KKT error exhibit a stable plateau over a moderate range of ∆u. The combination of near-unity success rate, bounded iteration count, and stable KKT error indicates that the NMPC subproblems consistently converge to near-KKT points in practice. Within this plateau, ∆u = 5 achieves a favorable balance between numerical robustness and computational efficiency. Accordingly, ∆u = 5 is adopted in the NMPC/LTO layer throughout the paper. Fig.9plots the NMPC objective JNMPC versus IPOPT iterations for five representative subproblems under ∆u = 5. The rapid stabilization of JNMPC is
Fig. 10. Sensitivity of makespan Tmax and task completion ratio Rs with respect to the number of rate segments K in a dense scenario with N = 50 and M = 8.
TABLE II
IMPACT OF ROLE SWITCHING PENALTY MAGNITUDE ηs ON SYSTEM PERFORMANCE
consistent with the high success rate and small KKT residuals, indicating reliable convergence in practice.
3) Rate-Segmentation Granularity: Fig.10shows the
resulting maximum completion time Tmax and the task completion ratio Rs as functions of the number of rate segments K. As K increases, Tmax generally exhibits a downward trend and reaches its global minimum of 96.30 s at K = 9, reflecting the benefit of finer rate approximation. The task success rate Rs remains robust across all cases, consistently staying above 0.98. However, a slight rebound in Tmax at K = 10 indicates that the performance gain saturates beyond K = 9. Consequently, we set K = 9 as the optimal granularity, as it minimizes mission time while achieving full task completion. 4) Sensitivity to Role Switching Penalty: We examine the sensitivity of the proposed framework to the role switching penalty ηs, which acts as a secondary regularization term relative to the dominant energy component of the objective. Table II shows that for ηs ≤ 200, the task completion rate remains at 1.00 and the number of role switches stays stable at around 60, indicating that switching decisions are mainly driven by energy efficiency. When ηs increases to 300, a sharp behavioral change occurs: role switching is strongly suppressed, reducing the number of switches to 4 and causing the task completion rate to drop to 52%. This behavior persists for larger ηs, demonstrating that excessive penalty values hinder adaptive role coordination. Overall, the results demonstrate that the proposed method is robust to ηs variations within a broad and practically relevant range.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

9498 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
VI. CONCLUSION
In this paper, we propose HOC-UADC, a hierarchical optimal control framework to address the joint trajectory and communication design problem for multi-UAV emergency networks. Our method successfully tames the computational complexity of the underlying MINLP by decomposing it into a dual-layer MPC architecture. The strategic layer employs an MILP within an RHC loop to manage long-term fleet coordination, while the trajectory layer uses NMPC for realtime, physics-aware control and dynamic role-switching. This hierarchical design proved essential for making the large-scale optimization problem tractable for real-time deployment. We will explore decentralizing the strategic planning layer, which we anticipate could enhance both system scalability and its robustness to single points of failure. To further bridge the gap between simulation and real-world deployment, we will integrate more sophisticated stochastic models for communication channels and environmental dynamics, improving performance in unpredictable conditions.
REFERENCES
[1] H. Xu et al., “A survey on UAV applications in smart city management: Challenges, advances, and opportunities,” IEEE J. Sel. Topics Appl. Earth Observ. Remote Sens., vol. 16, pp. 8982–9010, 2023. [2] M. H. Bashir, M. Ahmad, D. R. Rizvi, and A. A. A. El-Latif, “Efficient CNN-based disaster events classification using UAV-aided images for emergency response application,” Neural Comput. Appl., vol. 36, no. 18, pp. 10599–10612, Jun. 2024. [3] M. Adil et al., “UAV-assisted IoT applications, QoS requirements and challenges with future research directions,” ACM Comput. Surveys, vol. 56, no. 10, pp. 1–35, May 2024. [4] X. Gu and G. Zhang, “A survey on UAV-assisted wireless communications: Recent advances and future trends,” Comput. Commun., vol. 208, pp. 44–78, Aug. 2023. [5] J. Chen, U. Mitra, and D. Gesbert, “3D urban UAV relay placement: Linear complexity algorithm and analysis,” IEEE Trans. Wireless Commun., vol. 20, no. 8, pp. 5243–5257, Aug. 2021. [6] J. Liu and H. Zhang, “Height-fixed UAV enabled energy-efficient data collection in RIS-aided wireless sensor networks,” IEEE Trans. Wireless Commun., vol. 22, no. 11, pp. 7452–7463, Nov. 2023. [7] S. Peng, B. Li, L. Liu, Z. Fei, and D. Niyato, “Trajectory design and resource allocation for multi-UAV-assisted sensing, communication, and edge computing integration,” IEEE Trans. Commun., vol. 73, no. 4, pp. 2847–2861, Apr. 2025. [8] B. Li and J. Chen, “Large timescale optimization for communications over aerial ad hoc networks with predetermined trajectories,” IEEE Trans. Commun., vol. 72, no. 10, pp. 6371–6385, Oct. 2024. [9] J. Xue, J. Xu, X. Guan, H. Zhang, and Y. Gan, “Secure and energyefficient transmission in UAV-assisted intelligent reflecting surface networks,” Sci. Rep., vol. 15, no. 1, p. 34538, Oct. 2025. [10] H. Sun, Y. Zhou, H. Zhang, L. Ale, H. Dai, and N. Zhang, “Joint optimization of caching, computing, and trajectory planning in aerial mobile edge computing networks: An MADDPG approach,” IEEE Internet Things J., vol. 11, no. 24, pp. 40996–41007, Dec. 2024. [11] S. Wu, S. Li, H. Zhu, T. Wang, and L. Zhang, “Group multirole assignment with general conflict,” IEEE Trans. Syst., Man, Cybern., Syst., vol. 55, no. 6, pp. 4188–4201, Jun. 2025. [12] M. N. Tariq, J. Wang, S. Raza, M. Siraj, M. Altamimi, and S. Memon, “Toward optimal resource allocation: A multi-agent DRL based task offloading approach in multi-UAV-assisted MEC networks,” IEEE Access, vol. 12, pp. 81428–81440, 2024. [13] H. Wang, C. H. Liu, H. Yang, G. Wang, and K. K. Leung, “Ensuring threshold AoI for UAV-assisted mobile crowdsensing by multi-agent deep reinforcement learning with transformer,” IEEE/ACM Trans. Netw., vol. 32, no. 1, pp. 566–581, Feb. 2024. [14] S. Liu et al., “UAV-enabled collaborative beamforming via multi-agent deep reinforcement learning,” IEEE Trans. Mobile Comput., vol. 23, no. 12, pp. 13015–13032, Dec. 2024.
[15] N. Bashir, S. Boudjit, and G. Dauphin, “A connectivity aware path planning for a fleet of UAVs in an urban environment,” IEEE Trans. Intell. Transp. Syst., vol. 24, no. 10, pp. 10537–10552, Oct. 2023. [16] Z. Shen, G. Zhou, H. Huang, C. Huang, Y. Wang, and F.-Y. Wang, “Convex optimization-based trajectory planning for quadrotors landing on aerial vehicle carriers,” IEEE Trans. Intell. Vehicles, vol. 9, no. 1, pp. 138–150, Jan. 2024. [17] K. S. Tang, K. F. Man, S. Kwong, and Q. He, “Genetic algorithms and their applications,” Springer Handbook Eng. Statist., vol. 13, no. 6, pp. 22–37, 1996. [18] D. Wang, D. Tan, and L. Liu, “Particle swarm optimization algorithm: An overview,” Soft Comput., vol. 22, no. 2, pp. 387–408, Jan. 2018. [19] C. Kim, H.-H. Choi, and K. Lee, “Joint optimization of trajectory and resource allocation for multi-UAV-enabled wireless-powered communication networks,” IEEE Trans. Commun., vol. 72, no. 9, pp. 5752–5764, Sep. 2024. [20] R. Quirynen, S. Safaoui, and S. Di Cairano, “Real-time mixedinteger quadratic programming for vehicle decision-making and motion planning,” IEEE Trans. Control Syst. Technol., vol. 33, no. 1, pp. 77–91, Jan. 2025. [21] Y.-S. Liau, Y. W. P. Hong, and J. Sheu, “Laser-powered UAV trajectory and charging optimization for sustainable data-gathering in the Internet of Things,” IEEE Trans. Mobile Comput., vol. 24, no. 5, pp. 4278–4295, May 2024. [22] K. Liu and J. Zheng, “UAV trajectory optimization for time-constrained data collection in UAV-enabled environmental monitoring systems,” IEEE Internet Things J., vol. 9, no. 23, pp. 24300–24314, Dec. 2022. [23] S. Shen, K. Yang, K. Wang, G. Zhang, and H. Mei, “Number and operation time minimization for multi-UAV-enabled data collection system with time windows,” IEEE Internet Things J., vol. 9, no. 12, pp. 10149–10161, Jun. 2022. [24] A. Chapnevis and E. Bulut, “Delay optimal UAV trajectory planning for secure data collection from mobile IoT networks,” in Proc. IEEE Int. Conf. Ind. Technol. (ICIT), Apr. 2023, pp. 1–4.
[25] J. Tang and J. Chen, “Throughput maximization for UAV-assisted data collection with hybrid NOMA,” IEEE Trans. Wireless Commun., vol. 23, no. 10, pp. 13068–13081, Oct. 2024. [26] R. Liu et al., “Resource allocation for NOMA-enabled cognitive satellite–UAV–terrestrial networks with imperfect CSI,” IEEE Trans. Cognit. Commun. Netw., vol. 9, no. 4, pp. 963–976, Aug. 2023. [27] Y. He, K. Xiang, X. Cao, and M. Guizani, “Task scheduling and trajectory optimization based on fairness and communication security for multi-UAV-MEC system,” IEEE Internet Things J., vol. 11, no. 19, pp. 30510–30523, Oct. 2024. [28] Z. Yu, Z. Zhang, S. Zeadally, B. Shen, and X. Pei, “Energy-efficient computing offloading with trajectory optimization and resource allocation in UAVs aided industrial IoT,” IEEE Internet Things J., vol. 12, no. 17, pp. 34780–34792, Sep. 2025. [29] J. Fang, C. Zhu, P. Zhang, H. Yu, and J. Xue, “Heterogeneous trajectory forecasting via risk and scene graph learning,” IEEE Trans. Intell. Transp. Syst., vol. 24, no. 11, pp. 12078–12091, Nov. 2023. [30] Z. Zhang, J. Jiang, X. Haiyan, and W.-A. Zhang, “Distributed dynamic task allocation for unmanned aerial vehicle swarm systems: A networked evolutionary game-theoretic approach,” Chin. J. Aeronaut., vol. 37, no. 6, pp. 182–204, Jun. 2024. [31] N. T. Thanh Van, N. C. Luong, S. Feng, V.-D. Nguyen, and D. I. Kim, “Evolutionary games for dynamic network resource selection in RSMAenabled 6G networks,” IEEE J. Sel. Areas Commun., vol. 41, no. 5, pp. 1320–1335, May 2023. [32] Z. Cui, T. Yang, X. Wu, H. Feng, and B. Hu, “The data value based asynchronous federated learning for UAV swarm under unstable communication scenarios,” IEEE Trans. Mobile Comput., vol. 23, no. 6, pp. 7165–7179, Jun. 2024. [33] X. Tong, X. Li, and Y. Liu, “An auction-based distributed network slicing scheme for resource allocation in satellite-UAV integrated networks,” Comput. Commun., vol. 210, pp. 58–68, Oct. 2023. [34] M. Chen, A. Guo, and C. Song, “Multi-agent deep reinforcement learning for collaborative task offloading in mobile edge computing networks,” Digit. Signal Process., vol. 140, Aug. 2023, Art. no. 104127. [35] S. Huang, H. Zhang, and Z. Huang, “E 2 CoPre: Energy efficient and cooperative collision avoidance for UAV swarms with trajectory prediction,” IEEE Trans. Intell. Transp. Syst., vol. 25, no. 7, pp. 6951–6963, Jul. 2024. [36] H. Lei, Y. Yan, J. Liu, Q. Han, and Z. Li, “Hierarchical multi-UAV path planning for urban low altitude environments,” IEEE Access, vol. 12, pp. 162109–162121, 2024.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.

WANG et al.: REAL-TIME UAV PATH AND ROLE-COORDINATED PLANNING METHOD 9499
[37] S. Jie Seah et al., “Empirical channel models for UAV communication: A comparative study,” IEEE Access, vol. 12, pp. 96740–96756, 2024. [38] M. M. Z. Shaheen, H. H. Amer, and N. A. Ali, “Robust air-to-air channel model for swarms of drones in search and rescue missions,” IEEE Access, vol. 11, pp. 68890–68896, 2023. [39] B. Hua et al., “AAV air-to-air channel: Statistical properties and experimental verification,” IEEE Internet Things J., vol. 12, no. 13, pp. 25790–25803, Jul. 2025. [40] T. Liang, T. Zhang, B. Cao, and Q. Zhang, “Sensing, communication, and control co-design for energy-efficient UAV-aided data collection,” IEEE Wireless Commun. Lett., vol. 13, no. 10, pp. 2852–2856, Oct. 2024. [41] Y. Mao, B. Acikmese, P.-L. Garoche, and A. Chapoutot, “Successive convexification for optimal control with signal temporal logic specifications,” in Proc. 25th ACM Int. Conf. Hybrid Syst., Comput. Control, May 2022, pp. 1–7. [42] S. P. Boyd and L. Vandenberghe, Convex Optimization. Cambridge, U.K.: Cambridge Univ. Press, 2004. [43] J. K. Stolaroff, C. Samaras, E. R. O’Neill, A. Lubers, A. S. Mitchell, and D. Ceperley, “Energy use and life cycle greenhouse gas emissions of drones for commercial package delivery,” Nature Commun., vol. 9, no. 1, p. 409, Feb. 2018. [44] A. Al-Hourani, S. Kandeepan, and S. Lardner, “Optimal LAP altitude for maximum coverage,” IEEE Wireless Commun. Lett., vol. 3, no. 6, pp. 569–572, Dec. 2014. [45] Z. Bai, J. Shi, Z. Li, M. Li, and X. Liao, “An MA-HPPO approach for multi-UAV data collection,” IEEE Trans. Wireless Commun., vol. 23, no. 12, pp. 17974–17986, Dec. 2024. [46] B. P. Gerkey and M. J. Matari ́c, “A formal analysis and taxonomy of task allocation in multi-robot systems,” Int. J. Robot. Res., vol. 23, no. 9, pp. 939–954, Sep. 2004.
Shangpeng Wang received the Ph.D. degree from the School of Computer Science and Engineering, Central South University, Changsha, China, in 2025. His research focuses on spatial information network architecture, network resource management, intelligent systems, and collaborative computing.
Ling Chen is currently pursuing the B.S. degree in computer science and technology with the School of Informatics, Xiamen University, Xiamen, China. Her research interests including mission planning, route selection and planning, network flow optimization, and distributed computing.
Xiatong Hou is currently pursuing the B.S. degree in computer science and technology with the School of Informatics, Xiamen University, Xiamen, China. Her research interests including mission planning, network flow optimization, route selection and planning, and distributed computing.
Xinyue Wang is currently pursuing the B.S. degree in data science and big data technology with the School of Computer Science and Engineering, Central South University, Changsha, China. Her research interests including mission planning, network flow optimization, route selection and planning, and distributed computing.
Chenyuan Zhang is currently pursuing the bachelor’s degree with the School of Computer Science and Engineering, Central South University, Changsha, China. His research interests include spatial information network architecture, mobile edge computing, and the coordinated scheduling of space-based network resources.
Haoran Yang received the M.Eng. degree in artificial intelligence from the School of Artificial Intelligence, Henan University, Zhengzhou, China, in 2024. He is currently pursuing the Ph.D. degree in computer science and technology with the Big Data Institute, Central South University, Changsha, China. His research interests include multi-agent collaboration and intelligent computing systems.
Haijun Zhang (Senior Member, IEEE) received the Ph.D. degree from the Department of Electronic Engineering, City University of Hong Kong in 2010. He was a Post-Doctoral Research Fellow with the Department of Electrical and Computer Engineering, University of Windsor, Windsor, ON, Canada, from 2010 to 2011. He is currently a Professor of computer science with Shenzhen Graduate School, Harbin Institute of Technology, China. His current research interests include multimedia data mining, computational advertising, and service computing. He is currently an Associate Editor of Neurocomputing and Pattern Analysis and Applications.
Haixin Sun (Senior Member, IEEE) received the Ph.D. degree in communication engineering from the Institute of Acoustic, Chinese Academy of Sciences, Shanghai, China, in 2006. He visited the Department of Electrical and Computer Engineering, University of Connecticut, Storrs, USA, from March 2012 to April 2013. He is currently a Professor and a Doctoral Advisor with the School of Information Science and Engineering, Xiamen University.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 07,2026 at 03:11:43 UTC from IEEE Xplore. Restrictions apply.