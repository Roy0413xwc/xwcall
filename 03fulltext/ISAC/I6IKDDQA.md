---
title: "Learning to Beamform for Integrated Sensing and Communication: A Graph Neural Network With Implicit Projection Approach"
zotero_key: "I6IKDDQA"
pdf_key: "ACEMP65W"
doi: "10.1109/TWC.2025.3550315"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Learning to Beamform for Integrated Sensing and Communication: A Graph Neural Network With Implicit Projection Approach — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025 5931
Learning to Beamform for Integrated Sensing and
Communication: A Graph Neural Network With
Implicit Projection Approach
Yifei Zhao, Yong Zhou
 , Senior Member, IEEE, Zixin Wang
 , Member, IEEE,
Yuanming Shi
 , Senior Member, IEEE, Nan Cheng
 , Senior Member, IEEE,
and Haibo Zhou
 , Senior Member, IEEE
Abstract— Integrated sensing and communication (ISAC),
as an important usage scenario of 6G, is capable of seam-
lessly integrating wireless sensing and communication for their
mutual benefit. Taking full advantage of ISAC heavily relies
on effectively solving resource allocation problems, which, how-
ever, are generally high-dimensional and non-convex, resulting
in the optimization-based algorithms exhibiting high computa-
tion complexity and the traditional learning-based algorithms
returning infeasible solutions. In this paper, we consider an
ISAC scenario featured by multiple communication users and
multiple sensing targets, aiming to develop an efficient and
scalable algorithm that optimizes the radar transmit beampattern
under the communication performance constraint. To this end,
we propose a graph neural network (GNN) with implicit projec-
tion framework, where GNN captures the intricate interactions
between communication users and sensing targets and meanwhile
enables the joint optimization of communication and sensing
beamforming matrices, and the projection module is applied
to ensure the feasibility of the beamforming matrices design.
Via capturing the permutation equivalence for communication
matrices and the permutation invariance for the sensing matrix,
the scalability of the proposed algorithm is guaranteed. Sim-
ulation results show that the proposed algorithm significantly
reduces the computation complexity compared to the baselines,
and achieves excellent algorithmic scalability and constraint
satisfaction.
Index Terms— Integrated sensing and communication, graph
neural network, implicit projection.
Received 8 May 2024; revised 1 September 2024 and 2 January 2025;
accepted 3 March 2025. Date of publication 20 March 2025; date of current
version 14 July 2025. The work of Yong Zhou was supported by the
Natural Science Foundation of Shanghai under Grant 23ZR1442800. The
work of Yuanming Shi was supported in part by the National Natural Science
Foundation of China under Grant 62271318 and in part by Shanghai Rising-
Star Program under Grant 22QA1406100. The associate editor coordinating
the review of this article and approving it for publication was M. Giordani.
(Corresponding author: Yong Zhou.)
Yifei Zhao, Yong Zhou, and Yuanming Shi are with the School
of Information Science and Technology, ShanghaiTech University,
Shanghai 201210, China (e-mail: zhaoyf@shanghaitech.edu.cn; zhouyong@
shanghaitech; shiym@shanghaitech.edu.cn).
Zixin Wang is with the Department of Electronic and Computer Engineer-
ing, The Hong Kong University of Science and Technology, Hong Kong
(e-mail: eewangzx@ust.hk).
Nan Cheng is with the State Key Laboratory of ISN and the School of
Telecommunications Engineering, Xidian University, Xi’an 710071, China
(e-mail: dr.nan.cheng@ieee.org).
Haibo Zhou is with the School of Electronic Science and Engineering,
Nanjing University, Nanjing 210023, China (e-mail: haibozhou@nju.edu.cn).
Digital Object Identifier 10.1109/TWC.2025.3550315
I. I NTRODUCTION
R
ECOGNIZED
by International Telecommunication
Union (ITU) as an important usage scenario of 6G,
integrated sensing and communication (ISAC) aims to achieve
seamless integration of wireless sensing and communication
functions while pursuing mutual gains in their performance.
Compared to the separate design of communication and
sensing processes, ISAC has the advantages of achieving
higher spectrum, power, and hardware utilization via jointly
optimizing the communication and sensing waveforms and
resources [1]. With these advantages, ISAC has a wide range
of applications in the fields of autonomous driving, smart
city, remote sensing, and environmental monitoring [2], [3].
Waveform design is an essential aspect for unleashing
the full potential of ISAC, which can be divided into
sensing-centric design (SCD), communication-centric design
(CCD), and joint design (JD) [1], [4]. SCD aims at integrating
communication functions into existing sensing waveforms,
where the radar signal remains unchanged and the primary
focus is on the sensing function. For example, the authors
in [5] and [6] propose to embed the communication signals
into the chirp signals to generate the ISAC waveform, while
the authors in [7] implement the communication function-
ality by shuffling the waveforms across multiple transmit
antennas. Different from SCD, CCD achieves the sensing
function through the existing communication waveforms while
prioritizing the communication performance. For instance, the
authors in [8] and [9] employ orthogonal frequency division
multiplexing (OFDM) waveforms for radar sensing, aiming to
optimally implement the radar sensing function while mini-
mizing its impact on communication performance. Moreover,
the authors in [10], [11], [12], and [13] use the JD approach
to balance the performance tradeoff between sensing and
communication. As the resource allocation problem for ISAC
is generally high-dimensional and non-convex, the traditional
optimization-based methods typically require high computa-
tion complexity without being able to obtain optimal solutions.
Machine learning (ML) has the potential to achieve
low-complexity resource allocation after being well-trained,
given its unique feature of achieving nonlinear map-
ping [14], [15], [16], making it suitable for efficiently solving
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artificial intelligence
and similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

5932 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025
high-dimensional non-convex optimization problems [17],
[18], [19], [20]. As a result, the paradigm of learning-to-
optimize has been increasingly explored in ISAC. In particular,
the authors in [21] develop a long short-term memory (LSTM)
network for predictive beamforming in ISAC-based vehicle-to-
infrastructure (V2I) networks. This method does not require
an explicit channel tracking process and significantly reduces
the signaling overhead. While in [22], the authors propose
an end-to-end approach that directly maps the pilot signals
to the beamforming matrices to perform ISAC. In addition,
the authors in [23] propose unsupervised learning methods
for interference management, while avoiding high computation
complexity incurred by optimization-based methods.
Although promising, the ML-based algorithm still
encounters the following challenges. First, conventional
fully-connected neural networks (FCNNs) are unable to
effectively utilize the spatial interaction between sensing
and communication devices in ISAC systems. Fortunately,
such spatial interaction can be captured and leveraged by
graph neural network (GNN) to enhance the performance
of ISAC. Additionally, GNN possesses unique features of
permutation invariance and permutation equivalence [24],
[25], [26], which set it apart from FCNNs and enable
excellent algorithmic scalability. In particular, the authors
in [26] consider a communication system involving intelligent
reflective surface (IRS) and develop a GNN containing user
nodes and IRS nodes to learn mapping from the received
pilots to an optimized system configuration. Nevertheless, the
GNN in [26] cannot be directly applied to ISAC scenarios
due to the absence of sensing node design as well as complex
communication or sensing constraints.. Second, the solutions
returned by conventional data-driven learning algorithms are
not guaranteed to satisfy the stringent non-convex constraints.
Although normalization and Newton’s method can be applied
to tackle simple constraints (e.g., the maximum transmit
power constraint), the constraints of resource allocation
problems in ISAC scenarios are often associated with
sensing and/or communication performance and take on a
nonlinear and non-convex form of high complexity. Under
this circumstance, the penalty-based approach widely used in
the learning algorithm, which converts constraints into penalty
terms in the loss function, has a high probability of producing
infeasible solutions for stringent performance constraints,
owing to the lack of strict constraint enforcement. Designing
an effective learning framework that comprehensively tackles
the aforementioned challenges while considering the unique
features of ISAC is crucial but has not been investigated yet,
and this serves as the primary motivation behind our work.
In this paper, we consider an ISAC system, where the
base station (BS) simultaneously performs sensing of mul-
tiple targets and communicates with multiple communication
users. Our objective is to develop an efficient and scalable
algorithm that optimizes the radar transmit beampattern under
the constraint of communication performance. To achieve this
objective, we propose a novel GNN with implicit projec-
tion (GNN-IP) algorithm to achieve scalable and feasible
beamforming design. To summarize, this paper presents the
following contributions:
1) For an ISAC model involving multiple communication
users and sensing targets, we design a GNN module to
construct a mapping from the communication and sensing
channel state information (CSI) to the transmit beamforming
matrices. Our proposed GNN architecture captures the intri-
cate interactions between communication users and sensing
targets, enabling the joint optimization of communication and
sensing transmit waveforms. Meanwhile, the GNN’s permuta-
tion equivalence for communication matrices and permutation
invariance for the sensing matrix ensure its scalability with
respect to the number of communication users.
2) To ensure the feasibility of the beamforming matrices
design, we introduce a differentiable projection module. When
the solution returned by the GNN module does not satisfy the
constraints, the proposed projection module projects the output
of the GNN to the feasible set defined by the communication
performance and transmit power constraints. Therefore, the
proposed GNN-IP algorithm is capable of ensuring the fea-
sibility of stringent communication performance constraints,
while achieving excellent sensing performance.
3) The simulation results show that the proposed
GNN-IP algorithm exhibits significantly reduced computa-
tion complexity compared to the conventional optimization-
based algorithms, while still approaching similar sensing
mean-squared error (MSE) performance. Additionally, our
proposed algorithm demonstrates substantial enhancements in
both sensing performance and constraint satisfaction when
compared to the conventional FCNNs.
The rest of the paper is organized as follows. In Section
II, we present the system model and problem formulation
of ISAC systems under consideration. Section III describes
the proposed GNN-IP architecture. Section IV presents the
simulation results. Finally, Section V concludes this paper.
Notations: In this paper, (·)T and (·)H denote transpose and
Hermitian, respectively. Vectors are represented by bold lower
class letters, and matrices are represented by bold upper class
letters. We denote 0m×n as the m× n zero matrix. E denotes
the stochastic expectation. Tr(·) and rank(·) denote the trace
and rank for the matrix, respectively.
II. S YSTEM MODEL AND PROBLEM FORMULATION
In this section, we present the system model of ISAC,
including the sensing and communication models, and con-
struct a resource allocation problem for minimizing the
sensing MSE.
A. System Model
Consider an ISAC system, where a BS equipped with a
uniform linear array (ULA) consisting of M half-wavelength
spaced antennas simultaneously communicates with L down-
link users (L ≤ M) indexed by L = {1, . . . , L} and
meanwhile detects K radar targets (K ≤ M) indexed by
K ={1, . . . , K}, as shown in Fig. 1.
We denote the L parallel data streams from the BS to
the users as d = [ d1, d2, . . . , dL]T and the corresponding
communication beamforming matrix at the BS as C =
[c1, c2, . . . ,cL] ∈ CM×L. Meanwhile, to maximize the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

ZHAO et al.: LEARNING TO BEAMFORM FOR INTEGRATED SENSING AND COMMUNICATION 5933
Fig. 1. An illustration of ISAC system with K radar targets and L commu-
nication users.
degrees of freedom (DoF) of the sensing waveform, we denote
the individual sensing symbols and the corresponding sensing
beamforming matrix as w = [ w1, w2,··· , wM ]T and S =
[s1, s2,··· , sM ]∈ CM×M , respectively. Hence, the transmit
signal for joint sensing and communication at the BS can be
expressed as
x = Cd + Sw. (1)
Without loss of generality, we assume that the data streams
of different users are independent of each other and indepen-
dent from the radar symbols as in [27], [28], and [29], i.e.,
E
 
dwH = 0L×M , (2)
and the communication and sensing symbols have unit
power, i.e.,
E

ddH

= E
 
wwH = I. (3)
Given the maximum transmit power budget P0 at the BS,
we have
E
 
∥x∥2 = Tr (R) = TrCC H + SS H≤ P0, (4)
where R = CC H + SS H is the covariance matrix of the
transmit signal.
In the following, we shall elaborate the radar sensing model
and communication model.
1) Radar Sensing Model: We consider a radar probing
scenario [30], [31], [32], [33] where the main objective is to
direct the transmit beam toward specific given directions to
obtain more information about the illuminated target. These
directions are typically known to the transmitter. For instance,
the beam direction is given by the center of the angular sector
of interest in searching mode and determined by the observed
directions of previous targets in tracking mode.
Following [34] and [35], we consider that both the commu-
nication and sensing signals are utilized in target sensing. The
signal at angular position θ can be expressed as
z(θ) = aH(θ)x, (5)
where a(θ) is the array response vector. By denoting ∆ as the
normalized antenna interval, a(θ) can be written as a(θ) =
[1, . . . , e−j2π(M−1)∆ sinθ]T.
We aim to maximize the energy of sensing signal towards
the designated direction via aligning the transmitted signal
with the desired beampattern. Specifically, the beampattern at
a given angular position θ can be represented as
P (θ; R) = E(|z(θ)|2) = aH(θ)Ra(θ). (6)
As in [32] and [33], we evaluate the sensing performance
by measuring the MSE between the desired and obtained
beampatterns, which can be expressed as
L(R) = 1N
NX
n=1
|βb(θn)− P (θn; R)|2, (7)
where b(θ) is the desired beampattern for angle θ, β is the
power normalization parameter,{θn}Nn=1 denote the fine grid
of points that cover the entire location sector of the sensing
targets, and N is the total number of sample grids.
2) Communication Model: We assume that the channel
state information between the BS and the communication user
is available and can be obtained by various state-of-the-art
channel estimation algorithms. By denoting the channel vector
from the BS to user l as hl, the received signal at user l is
rl = hHl x + nl
= hHl

cldl +
LX
j=1,j̸=l
cjdj +
MX
i=1
siwm

 + nl, (8)
where nl is the additive white Gaussian noise (AWGN)
with zero mean and variance σ2. In particular, cldl is the
intended signal received by the l-th user, PLj=1,j̸=l cjdj is the
interference from multi-user communication, and PMi=1 siwm
is the interference caused by sensing signals. Therefore, the
signal-to-interference-plus-noise ratio (SINR) of the l-th user,
denoted as Γl, can be expressed as
Γl =
hHl cl2
PL
j=1,j̸=l
hHl cj2 + PMi=1 hHl si2 + σ2
= hHl clcHl hl
hHl
PL
j=1,j̸=l cjcHj + SS H

hl + σ2
= hHl C lhl
hHl (R− C l) hl + σ2 , (9)
where C l = clcHl .
To ensure the communication performance for each user,
a minimum SINR threshold, denoted as Γ0, for each commu-
nication user should be satisfied, i.e.,
Γl≥ Γ0,∀ l∈L . (10)
B. Problem Formulation
We aim to develop a computation-efficient algorithm that
minimizes L(R) while ensuring the communication SINR for
each user. The designed transmit waveform should maximize
the main lobes energy towards the sensing targets as well as the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

5934 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025
communication users, while suppressing the side lobes energy.
The joint optimization problem can be formulated as
minimize
C1,...,CL,S
L(R) (11a)
subject to R =
LX
l=1
C l + SS H⪰ 0, (11b)
Tr(R) = P0, (11c)
rank(C l) = 1,∀ l∈L , (11d)
Γl≥ Γ0,∀ l∈L , (11e)
where (11c) represents the transmit power constraint and (11e)
represents the communication SINR constraint. Note that we
employ an equational power constraint in constraint (11c) to
ensure that the maximum transmit power of the BS is utilized
to maximize the radar performance [36]. Problem (11) is a
high-dimensional non-convex optimization problem. Although
conventional optimization-based methods (e.g., semidefinite
relaxation (SDR) [37], [38]) can be utilized to solve prob-
lem (11), they usually encounter the issue of excessively high
computation complexity, particularly when the numbers of
sample angle grids and communication users are large, thereby
lacking of algorithmic scalability.
In contrast to the optimization-based algorithms, data-driven
learning algorithms can be utilized to obtain the desired
beamforming matrix through direct mapping, which signif-
icantly reduces the computation complexity. However, the
learning algorithm frequently encounters the critical challenge
of returning infeasible solutions, especially for the commu-
nication SINR constraint (11e). Therefore, it is imperative
to develop an efficient algorithm that exhibits minimal com-
putation complexity while achieving excellent algorithmic
performance in terms of scalability and constraint satisfaction.
To this end, we propose a GNN-IP algorithm, where the GNN
module is utilized to ensure the algorithmic scalability, and
a projection module is employed to map the GNN module’s
output onto the feasible domain, ensuring the feasibility of the
resulting beamforming matrices.
III. GNN-IP F RAMEWORK
In this section, we develop a novel GNN-IP framework
to maximize the sensing performance under stringent com-
munication performance constraint. The GNN structure, loss
function design, projection process, and computation complex-
ity are elaborated in the following.
Our key idea is to learn a direct mapping from CSI and
array responses to desired beamforming design, taking into
account the computational efficiency and the robustness of the
data-driven model training. Specifically, the general form of
the mapping can be expressed as
{ eC, eS} =M({hl, a(θk)}), (12)
where M(·) denotes the mapping function and θk is the
angular position for the k-th sensing target. Therefore, solving
problem (11) is equivalent to acquiring the optimal mapping
functionM(·). In this paper, we approximate M(·) with the
GNN-IP framework, which includes a GNN module and an
implicit projection module. Since the BS knows the topology
of the ISAC system, we model a graph that integrates the
connectivity between BS and communication users as well
as sensing targets, and construct the GNN module accord-
ingly [39], [40], [41]. Specifically, the graph consists of
L + 1 nodes and L(L+1)2 edges, where the nodes includes
L user nodes, each associated with a communication vector,
and one radar node associated with a combined sensing
matrix. Moreover, the edges between the user nodes con-
tain information about the interference interaction among the
communication users. The edges between the radar node
and the user nodes contain two types of information. The
first comprises the interference of the sensing beamforming
matrix design S for communication. The second comprises
the involvement of the communication beamforming matrices
C for sensing. We design a unified sensing matrix instead of
K individual sensing vectors due to the following two reasons.
First, for power maximization towards these sensing targets,
we do not need to capture the interaction among these targets,
such as interference and cross-correlation. Second, the dimen-
sion of the sensing matrix S does not align with the number
of sensing targets K. On the other hand, the proposed projec-
tion module employs an optimization algorithm to minimize
the distance between the infeasible results generated by the
GNN module and the feasible domain, ensuring the stringent
constraint of problem (11). In summary, the proposed GNN-IP
framework initially inputs the CSI and array responses into the
GNN module, subsequently evaluating the feasibility of the
GNN module output. If the output is infeasible, the projection
module then maps it into the feasible domain. The overall
workflow of the proposed GNN-IP framework is illustrated
in Fig. 2.
A. GNN Module
The GNN module of the proposed framework consists of
an initialization layer, T updating layers, and a normalization
layer. Specifically, in the initialization layer, the communica-
tion channel and sensing array responses are converted into
representation vectors of user nodes{z(1)l }l∈L and radar node
z(1)L+1, which are then updated via the message-passing mech-
anism through T updating layers, referred to as {z(T +1)l }l∈L
and z(T +1)L+1 , respectively. Finally, the normalization layer maps
the representation vectors to the beamforming matrices C
and S.
1) Initialization Layer: As shown in Fig. 3, the initialization
layer separately converts the CSI of the communication users
and the array responses of the sensing targets into representa-
tion vectors, facilitating message passing for the subsequent
updating layers. Note that in the proposed ISAC system,
it is essential that the sequence of communication beam-
forming designs must align with the order of communication
users, while the sensing beamforming design should remains
unchanged. These properties are referred to as permutation
equivalence for user nodes and permutation invariance for the
radar node. To realize the above two permutation properties,
we separately initialize the representation vectors as follows.
Specifically, the output representation vector of the l-th user
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

ZHAO et al.: LEARNING TO BEAMFORM FOR INTEGRATED SENSING AND COMMUNICATION 5935
Fig. 2. Workflow of the proposed GNN-IP algorithm.
Fig. 3. Initialization layer for the user nodes and the radar node.
node z(1)l can be represented as
z(1)l = f (0)ct
 
f (0)c

[(ℜ{hl})T , (ℑ{hl})T]T
+ 1K
KX
k=1
f (0)s

[
 
ℜ{a(θk)}T ,  ℑ{a(θk)}T]T
!
,
(13)
where f (0)ct (·), f (0)c (·) and f (0)s (·) denote the FCNN-based
encoders with different sizes. Note that we consider
the decomposition of the real and imaginary parts to
circumvent the poor support of existing deep learning
toolkits for complex numbers. Besides, as the communi-
cation beamforming matrices also participate in sensing,
we incorporate the local CSI and all array responses
into the initialization of representation vectors of each
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

5936 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025
Fig. 4. Aggregation and combining operations of the t-th layer for the user nodes and the radar node.
user node, which preserves the permutation equivalence as
well.
On the other hand, we adopt a FCNN-based encoder
f (0)st (·) to initialize the representation vector of the radar
node. Considering the sensing beamforming matrix as inter-
ference in communication SINR calculations, the generation
for representation vector of the radar node should account for
the communication CSI. Therefore, the output representation
vector of the radar node can be expressed as
z(1)L+1 = f (0)st
 
1
L
LX
l=1
f (0)c

[(ℜ{hl})T , (ℑ{hl})T]T
+ 1K
KX
k=1
f (0)s

[
 
ℜ{a(θk)}T,  ℑ{a(θk)}T]T
!
,
(14)
Through the average operation, we can ensure that all the
communication and sensing information are passed to the radar
node, thereby ensuring the permutation invariance. In (13)
and (14), we use the same encoders f (0)c and f (0)s , thereby
reducing the training complexity and ensuring the permuta-
tion properties. Besides, different encoders f (0)ct and f (0)st are
adopted to ensure different encoding for the user and radar
nodes.
2) Updating Layers: Each updating layer consists of
L + 1 nodes, each of which aggregates the representation
vectors from neighboring nodes and then combines them with
its own representation vector. Specifically, following the design
in [40], [42], [43], and [44], a general form of update for the
representation vector at node i in the t-th updating layer can
be represented as
v(t+1)i = f (t)Comb(v(t)i , f(t)Agg({v(t)j }j∈N (i))), (15)
whereN (i) denotes the collection of neighboring nodes of
node i, and f (t)Comb(·) and f (t)Agg(·) denote the combining
function and the aggregation function, respectively. Note that
the permutation properties of the user nodes and the radar node
are distinct. Consequently, the aggregation and combining
operations for the user nodes and the radar node need to be
designed independently.
As shown in Fig. 4(a), each user node l∈L aggregates the
information from all other user nodes and then combines the
representation vectors of local node and the radar node with
the aggregated representation vectors. Specifically, the update
equation for the l-th user node can be expressed as
z(t+1)l = f (t)Comb,1

z(t)l , f(t)2 (z(t)L+1), z(t+1)Agg,l

, (16)
where
z(t+1)Agg,l = ψ1

{f (t)1 (z(t)j )}j∈L\{l}

, (17)
f (t)1 (·) and f (t)2 (·) are FCNN-based encoders with different
sizes. f (t)Comb,1(·) denotes the combining function and is param-
eterized by a FCNN based encoder. In particular, due to the
lack of theoretical guidance, we set ψ1(·) as the element-wise
max-pooling function, which empirically performs well, as in
[26], [39], and [40]. Furthermore, this choice preserves the
permutation equivalence.
On the other hand, as shown in Fig. 4(b), recall that in (7)
the sensing performance is jointly determined by the sensing
and communication matrices, the radar node aggregates the
information from all the user nodes and then combines the
representation vector of local node with the aggregated rep-
resentation vectors. In particular, the update equation for the
radar node is represented by
z(t+1)L+1 = f (t)Comb,2

f (t)2 (z(t)L+1), z(t+1)Agg,L+1

, (18)
where
z(t+1)Agg,L+1 = ψ0

{f (t)1 (z(t)l )}l∈L

, (19)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

ZHAO et al.: LEARNING TO BEAMFORM FOR INTEGRATED SENSING AND COMMUNICATION 5937
f (t)Comb,2(·) denotes the combining function and is parame-
terized by a FCNN based encoder. Besides, we adopt the
element-wise mean function as ψ0(·) to facilitate the inte-
gration of CSI from all users and guarantee the permutation
invariance. After multiple updates, each node has access to
sufficient information to coordinate between the user and radar
nodes.
3) Normalization Layer: The normalization layer maps the
up-to-date representation vectors to normalized beamforming
matrices C and S. For the representation vector z(T +1)l of
the l-th user node, we first encode it through a FCNN-based
encoder f (T +1)c (·) with the output dimension of 2M, which
can be expressed as
z(T +2)l = f (T +1)c (z(T +1)l )∈ R2M ,∀ l∈L . (20)
Then, we obtain the communication matrix as ˙C =
[ ˙c1, . . . ,˙cL], where ˙cl = z(T +2)l (1 : M ) + jz(T +2)l (M +
1 : 2M ),∀l ∈ L, with z(T +2)l (i : j) being the subvector
of z(T +2)l and consisting of elements i to j of z(T +2)l .
Similarly, for the representation vector of radar node z(T +1)L+1 ,
we employ the FCNN-based encoder f (T +1)s (·) with the output
dimension of 2M 2, and subsequently reshape it to dimension
of 2M× M, i.e.,
Z s =R

f (T +1)s (z(T +1)L+1 )∈ R2M×M , (21)
whereR(·) denote the reshape function. Then, we obtain the
sensing matrix as follows
˙S = Z s(1 : M, :) + jZ s(M + 1 : 2M, :), (22)
where Z s(i : j, :) denotes the submatrix of Z s and consists
of rows i to j of Z s. It is evident that the network output
matrix inherently satisfies constraints (11b) and (11d), i.e.,
the positive definite and rank one conditions. Note that the
randomness of neural networks may result in the violation
of the transmit power constraint (11c). We propose to apply
the normalization operation over the output communication
matrix ˙C and sensing matrix ˙S to address this issue:
C =
√P0
Tr( ˙C ˙C H + ˙S ˙SH)× ˙C,
S =
√P0
Tr( ˙C ˙C H + ˙S ˙SH)× ˙S. (23)
Note that the normalization operation is a one-to-one mapping
from the representation vectors to the beamforming matrices,
thus ensuring the permutation properties of the GNN module
and the satisfaction of constraint (11c).
B. Loss Function Construction
With the aforementioned design, we can transform prob-
lem (11) into an unconstrained Lagrangian problem
minimize
{C1,...,CL,S}
L(R) + λ
LX
l=1
(Γ0− Γl), (24)
where C l = clclH and R = PLl=1 C l + SS H, and λ is
the Lagrangian dual variable. Inspired by the objective plus
penalty structure in (24), we propose to design the loss
function as follows
loss = L(R)| {z }
t1
+µ
LX
l=1
K (Γ0− Γl)
| {z }
t2
, (25)
whereK(·) denotes the barrier function and µ is a hyperparam-
eter associated with constraint (11c). In this paper, we adopt
the ReLU function as the barrier function due to its low
computation complexity and ease of optimization. The barrier
function enables the loss function to prioritize sensing perfor-
mance while incorporating communication SINR constraint.
The proposed GNN module has the following advantages.
First, our proposed GNN module is capable of preserving
permutation invariance and permutation equivalence of
problem (11). The GNN module consistently generates the
same permutation order for communication beamforming
vectors cl and the invariant sensing beamforming matrix S
when the communication users in the system are permuted.
Specifically, permutation equivalence means that when we
arrange the communication users in the system, the GNN
module produces the communication beam forming vectors
cl with the same order of arrangement, whereas permutation
invariance means that the arrangement of the communication
users does not change the sensing beam forming matrix S as
well as the covariance matrix R = PLl=1 C l + SS H. The per-
mutation properties can improve the scalability of the learning
framework. Second, compared to the conventional FCNNs,
the GNN module leverages the network topology to capture
the interaction between communication users and sensing
targets. This not only helps mitigate co-channel interference
for communication users, but also significantly enhances the
sensing performance. Third, the user nodes of the proposed
GNN module share the same design of encoder and decoder.
This design allows us to directly and easily copy or delete user
nodes without retraining when the number of communication
users changes, which reduces the computation time and
enhances the scalability of the algorithm. Additionally,
benefiting from data-driven training and sufficient exploration
over the graph for the considered ISAC system, the learned
GNN module can capture the general representation of the
ISAC system with respect to channel state information and
array responses, and is robust to the randomness of fading
channel and location changes of sensing targets, thereby
reducing the number of retraining. In summary, the proposed
GNN module exhibits the characteristics of low complexity,
high training efficiency, and high algorithmic scalability.
The proposed GNN module effectively reduces computation
complexity while enhancing the sensing performance and
mitigating the communication constraints violation. Neverthe-
less, the stringent transmit power and communication SINR
constraints may not always be satisfied. To ensure robustness,
we propose a projection module to post-process the output of
the GNN module in the following subsection.
C. Implicit Projection Module
After the pre-processing via the GNN module, we post-
process the outputs of the GNN module that violate
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

5938 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025
Fig. 5. Illustration of the proposed projection module, where the round point
represents the output of the GNN module and is projected into the feasible
domain, denoted as the square point, via the projection module.
constraint (11c) by developing an implicit projection module.
By denoting the projection function as Proj(·), the desired
communication beamforming and sensing beamforming matri-
ces can be expressed as
{ eC, eS} = Proj ({C, S}) . (26)
As illustrated in Fig. 5, we adopt the implicit projection
method to project beamforming matrices {C, S} generated
by the GNN module into the feasible domain [45], [46].
Specifically, we formulate the following projection optimiza-
tion problem
minimize
ˆC1,..., ˆCL, ˆR
D

{ ˆC 1, . . . ,ˆC L, ˆR},{C 1, . . . ,C L, R}

(27a)
subject to ˆR⪰ 0, (27b)
ˆR−
 LX
l=1
ˆC l
!
⪰ 0, (27c)
Tr( ˆR) = P0, (27d)
Γl≥ Γ0,∀ l∈L , (27e)
whereD(·) denotes the function that measures the distance
between the output beamforming designs of the GNN module
and the desired designs in the feasible domain. By settingD(·)
as the Frobenius norm, problem (27) can be rewritten as
minimize
ˆC1,..., ˆCL, ˆR
LX
l=1
∥ ˆC l− C l∥2F +∥ ˆR− R∥2F (28a)
subject to ˆR⪰ 0, (28b)
ˆR−
 LX
l=1
ˆC l
!
⪰ 0, (28c)
Tr( ˆR) = P0, (28d)
Γl≥ Γ0,∀ l∈L . (28e)
Based on (9), we reformulate (28e) and obtain the following
convex optimization problem
minimize
ˆC1,..., ˆCL, ˆR
LX
l=1
∥ ˆC l− C l∥2F +∥ ˆR− R∥2F (29a)
subject to ˆR⪰ 0, (29b)
ˆR−
 LX
l=1
ˆC l
!
⪰ 0, (29c)
Tr( ˆR) = P0, (29d)
(1 + Γ−10 )hHl ˆC lhl≥ hHl ˆRhl + σ2,∀ l∈L .
(29e)
Note that the constraints of problems (29) and (11) are equiv-
alent except for the rank-one constraint (11d). To satisfy the
rank-one constraint, the communication beamforming vectors
{ec1, . . . ,ecL} can be explicitly expressed as
ecl =
ˆC lhlq
hHl ˆC lhl
,∀ l∈L , (30)
and the explicit expression of sensing beamforming matrix eS
can be obtained after applying the Cholesky decomposition as
follows
eS eSH = ˆR−
 LX
l=1
eC l
!
, (31)
where eC l = eclecHl . Then, we need to prove that set
{ec1, . . . ,ecL, eS} complies with the constraints in problem (29)
to validate its feasibility as a solution set for problem (11).
Proposition 1: The set {ec1, . . . ,ecL, eS} obtained by (30)
and (31) satisfies the constraints in problem (29).
Proof: With (30) and (31), as hHl eC lhl = hHl ˆC lhl,
the obtained eC l satisfies the communication SINR con-
straint (29e). Since ˆR−
PL
l=1 ˆC l

⪰ 0, we can apply the
Cauchy-Schwartz inequality, for any u and∀ l∈L , leading
to
uH( ˆC l− eC l)u = uH ˆC lu− (hH eC lhl)−1
uH eC lhl2≥ 0,
(32)
which means that ˆC l− eC l⪰ 0,∀ l∈L . Therefore, we obtain
ˆR−
 LX
l=1
eC l
!
= ˆR−
 LX
l=1
ˆC l
!
+
LX
l=1
( ˆC l− eC l)⪰ 0.
(33)
With the derivation above, it is verified that { eC l}l∈L along
with eS constitute a feasible solution to problem (29).
The entire process of the proposed GNN-IP algorithm is
summarized in Algorithm 1. The proposed algorithm has
the following advantages. First, the computation complexity of
problem (11) depends on the sample grid number N, whereas
that of problem (29) is independent of N. Consequently, for
a large value of N, the projection module requires a lower
computation complexity than problem (11). Besides, as shown
in (23) and (25), the proposed GNN module incorporates
constraints in the normalization layer and loss function design.
Consequently, only a few infeasible samples enter the pro-
jection module, thereby significantly reducing the algorithmic
complexity. Second, the proposed GNN-IP framework guar-
antees permutation equivalence/invariance, while ensuring that
the generated solutions are feasible.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

ZHAO et al.: LEARNING TO BEAMFORM FOR INTEGRATED SENSING AND COMMUNICATION 5939
Algorithm 1 Joint Transmit Beamforming via GNN-IP
Algorithm
Input:
BS transmit power P0;
SINR threshold Γ0.
Training dataset
D ={{hl, a(θk)}(1), . . . ,{hl, a(θk)}(Dtrain)};
Test dataset
T ={{hl, a(θk)}(1), . . . ,{hl, a(θk)}(Dtest)};
Initial GNN model G.
Output:
Transmit beamforming matrices {ec1, . . . ,ecL, eS}.
Steps:
T raining:
while Training do
for i = 0 to Dtrain do
Sample{hl, a(θk)}(i) fromD;
for l = 0 to L do
Obtain representation vector z(0)l based on (13);
end for
Obtain representation vector z(0)L+1 based on (14);
for t = 0 to T do
for l = 0 to L do
Update representation vector z(t)l based on (17);
end for
Update representation vector z(t)L+1 based on (18);
end for
Obtain network output matrices C and R based on
(23);
Calculate loss based on (25);
Update GNNG model with gradient backward;
end for
end while
Inf erence:
for i = 0 to Dtest do
Sample{hl, a(θk)}(i) fromT ;
Obtain transmit beamforming matrices {C, R} through
the GNN inference;
if C, R is infeasible then
Project the solution to the feasible domain based
on (29);
Compute{ec1, . . . ,ecL, eS} based on (30) and (31).
else
Output{ec1, . . . ,ecL, eS} based on{C, R}.
end if
end for
D. Computation Complexity
1) Complexity of GNN-IP Algorithm: As the proposed
GNN-IP framework consists of the GNN module and the
projection module, we analyze the complexity of these two
modules separately.
a) Complexity of GNN module: Since the encoders share
the same structure in different layers, we assume that the
encoders of the user and the radar node have the same network
structure with different weights, and denote the computation
complexity of them asO(C). For the initialization layer, since
each node takes into account the CSI of L communication
users and the array responses of K sensing targets when gen-
erating the representation vector, the computation complexity
isO(CL(K + 1) +C(L + K)) =O(C(LK + 2L + K). For
the updating layer, each node performs the aggregation and
combining operations. For the user node, according to (17),
the computation complexity of encoding and max pooling in
aggregation operations isO(CL +L−1). For the sensing node,
according to (18), the computation complexity of encoding
and mean function in aggregation operations is O(CL + L).
Since the combining functions share the same structure in
all nodes, we assume that the combining operation takes
the same amount of time for all nodes, denoted as O(C).
Therefore, the computation complexity of T updating layers
is O(T L(CL+ L + C)). For the normalization layer, the
computation complexity is O(C(L + 1)). As a result, the
overall computation complexity of the GNN module in the
inference stage isO(C(LK + 2L+ K) +T L(CL+ L + C) +
C(L + 1))≈O (C(T L2 + T L+ KL + L + K)).
b) Computation complexity of projection module:
Solving problem (29) is the most time-consuming pro-
cedure of the projection module. Specifically, the CVX
toolbox transforms problem (29) into a second-order cone
programming (SOCP) problem during the solving stage,
where (29a) is transformed into L constraints [47]. Hence
the worst-case computation complexity to solve problem (29)
isO(max(L, LM)4(LM )0.5 log( 1ϵ )) = O((LM )4.5 log( 1ϵ )),
given a solution accuracy ϵ [38].
We assume that the ratio of the number of samples that
satisfy the constraints to the total number of samples after
the inference of the GNN module is ρ. The computation
complexity of the whole GNN-IP algorithm is O(ρ(C(T L2 +
T L+ KL + L + K)) + (1− ρ)((LM )4.5 log( 1ϵ ))). Hence,
the primary factors influencing the computation complexity
include the ratio of constraint satisfaction, the number of
communication users and sensing targets, and the number of
antennas.
2) Computation Complexity of SDR Algorithm: According
to [33], we first transform problem (11) into a semi-definite
programming (SDP) problem, which is then transformed into
a SOCP problem during the solving stage, where (11a) is
transformed into N constraints. Given a solution accuracy
ϵ, the worst-case computation complexity to solve (11) using
the SDR algorithm isO(max(N, LM)4(LM )0.5 log( 1ϵ )) [38].
Hence, the computation complexity of the SDR algorithm is
always greater than or equal to that of the developed projection
module. In particular, to enhance the sensing performance, the
value of N should be large. When N > LM, the projection
module results in lower computation complexity than the SDR
algorithm. By further considering that the projection model is
infrequently used, the worst-case computation complexity of
the proposed algorithm is much smaller than that of the SDR
algorithm.
IV. S IMULATION RESULTS
In this section, we evaluate the performance of our proposed
GNN-IP algorithm for ISAC through extensive simulations.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

5940 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025
TABLE I
NETWORK PARAMETERS OF THE PROPOSED GNN M ODULE
A. System Settings
In the simulations, the BS is equipped with M = 10 anten-
nas, and located at (x, y, z) = (0 ,−100, 20) meters. The BS
simultaneously serves three radar targets and two communica-
tion users, i.e., K = 3 and L = 2. The transmit power of the
BS is normalized to P0 = 1. The communication users are
independent and identically distributed within a rectangular
region of ([5, 35], [−35, 35], 0) meters. The channel between
the BS and user l is modeled as Rayleigh fading, i.e., hl =√αlh∗l , where h∗l ∼CN (0, I). The factor αl, representing
the large-scale fading, is modeled as αl = 10−3d−2.67l , where
dl represents the distance between the BS and user l. The
width of each sensing beam is ∆ = 10◦, and thus the desired
beampattern b(θ) is set as
b(θ) =



1, ˆθp− ∆2 ≤ θ≤ ˆθp + ∆2 , p= 1, 2, 3,
0, otherwise.
(34)
For (7), we uniformly sample the direction grids {θn}Nn=1
within the range of −90◦ to 90◦ with a resolution of 1◦, i.e.,
N = 180. Unless specified otherwise, we set σ2 = 10−10 and
Γ0 = 8 dB.
B. Network Parameters and Benchmarks
We consider a 2-layer GNN and the specific param-
eters of the FCNN in each graph layer are shown in
Table I. For the power normalization parameter β in (7),
we obtain its value by solving the linear equation problem
βb = p, where b = [b(θ 1), b(θ2), . . . , b(θN )]T and p =
[P (θ1; R), P(θ2; R), . . . , P(θN ; R)]T.
Our proposed neural network is implemented by the
PyTorch deep learning library [48]. We employ the Adam
optimizer [49] with a learning rate of 7×10−3 for the network
training. We consider a total of 500 training epochs, and
perform validation and test after every 10 training epochs. The
model with the best performance on the validation set is saved.
The sizes of the training, validation, and test sets are fixed as
10000, 1000, and 1000, respectively. In each simulation, once
the number of communication users and SINR constraints of
the system are fixed, the proposed GNN-IP algorithm directly
Fig. 6. Transmit beampattern of MIMO radar when ˆθ1 = −40◦, ˆθ2 = 0◦,
and ˆθ3 = 40◦.
inference on the changing communication channel and array
responses without retraining.
We consider the following benchmarks:
• Benchmark 1 is the SDR based optimization algorithm
proposed in [33].
• Benchmark 2 is the zero-forcing (ZF) beamforming based
optimization algorithm proposed in [33]. ZF-beamforming is
utilized to reduce inter-user interference and radar interference,
which in turn accelerates the algorithm convergence to obtain
a sub-optimal solution.
• Benchmark 3 is the deep neural network (DNN) based
algorithm. We design a conventional FCNN for compar-
ison. Specifically, we employ a DNN comprising four
fully-connected layers, with each hidden layer comprising
512 neurons. We employ the sigmoid function as the acti-
vation function. The proposed network is implemented using
PyTorch, and we utilize the Adam optimizer with a learning
rate of 10−3 for neural network training. The sizes of the
training, validation, and test sets are the same as that of the
proposed GNN module. We consider a total of 500 training
epochs, and perform validation and test after every 10 training
epochs. The model with the best performance on the validation
set is saved. We employ the normalization operation described
in (23) and use (25) as the loss function for network training.
We implement the optimization-based benchmark algo-
rithms via the MATLAB CVX toolbox [47], [50] with the
SDPT3 solver [51]. The results are obtained by averaging
over 1000 Monte Carlo tests.
C. Performance Comparison
1) Beampattern: We depict the beampattern P (θ; R) in
Fig. 6 and Fig. 7, where we set the number of communication
users L = 2 . We train and compute the beampatterns for
two scenarios with directions { ˆθ1, ˆθ2, ˆθ3} as {−40 ◦, 0◦,
40◦} and {−40 ◦, 15◦, 30◦}. We observe that the proposed
GNN-IP algorithm maintains accurate angle sensing of the
target direction. Our algorithm demonstrates superior beampat-
tern performance at the target angle compared to ZF and DNN,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

ZHAO et al.: LEARNING TO BEAMFORM FOR INTEGRATED SENSING AND COMMUNICATION 5941
Fig. 7. Transmit beampattern of MIMO radar when ˆθ1 = −40◦, ˆθ2 = 15◦,
and ˆθ3 = 30◦.
Fig. 8. Beampattern MSE versus SINR threshold Γ0 in a dynamic scenario.
closely approaching the performance of SDR. Meanwhile,
the proposed algorithm has excellent sensing performance
even when the sensing targets are close in directions. More-
over, due to the full rank sensing beamforming design S,
we successfully sense every target even though the number
of communication users is smaller than the number of sensing
targets.
2) MSE: We then evaluate the sensing MSE performance
of different algorithms versus the communication SINR con-
straint Γ0 in Fig. 8, and versus the number of communication
users L in Fig. 9. In Fig. 8, we evaluate the sensing
MSE performance of the proposed algorithm and the baseline
algorithms in a dynamic scenario. Specifically, after each time
slot, every communication user randomly moves within [−1, 1]
meter along the x-axis and [−2, 2] meters along the y-axis from
its current position. In each time slot, the proposed algorithm
as well as the baseline algorithms are executed to optimize the
resource allocation. Fig. 8 shows that the proposed GNN-IP
algorithm achieves better sensing performance than the DNN
algorithm and ZF optimization algorithm. Meanwhile, the
performance gap between the GNN-IP algorithm and the SDR
algorithm is small when Γ0≤ 8 dB. As Γ0 increases to 9 dB,
the GNN-IP algorithm needs to leverage the projection module
to ensure the solution feasibility, leading to a degradation of its
Fig. 9. Beampattern MSE versus number of communication users.
sensing performance and a relatively large performance loss
compared to the SDR algorithm. This illustrates the feasibility
of the proposed algorithm in dynamic scenarios.
Fig. 9 also indicates that the proposed GNN-IP algorithm
can achieve a satisfactory performance under different values
of L. To illustrate the scalability of the proposed algorithm,
we train a GNN module on the dataset with L = 2, and
then directly apply it to a multi-user scenario. Benefiting from
the shared encoder and decoder design of the user nodes, the
proposed algorithm adapts to different user number scenarios
by directly copying the network weight information of the
encoders of the user nodes of the GNN module without
retraining. From Fig. 9, we find that the performance of the
scaled GNN-IP algorithm is close to that of the GNN-IP
algorithm that performs retraining until the number of users
reaches 4. This illustrates the scalability of the proposed GNN
algorithm.
3) Computation Complexity: Despite achieving a little
higher MSE than the SDR algorithm, the proposed GNN-IP
algorithm has much lower computation complexity. To verify
this, Table II and Table III compare the average computation
time and the sensing MSE of our proposed algorithm with
that of the SDR algorithm and the ZF algorithm under different
number of sample grids N and different communication SINR
constraints, respectively.
From Table II, we observe that the computation time of the
conventional optimization algorithm rapidly increases with the
increase of N. However, with any value of N, the computa-
tion time of the proposed GNN-IP algorithm remains almost
unchanged and is much smaller than that of the traditional
optimization-based algorithms. This is due to the fact that
the network mapping of the GNN module and the compu-
tation complexity of the projection module are independent
of N. This demonstrates the low computation complexity
of our proposed GNN-IP algorithm compared to traditional
optimization-based algorithms. Meanwhile, it can be observed
that the sensing MSE for all algorithms increases rapidly as N
decreases. It is evident that under limited computation time,
our proposed GNN-IP algorithm is able to use a larger N
than the conventional optimization-based methods, to achieve
desired sensing performance.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

5942 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025
TABLE II
A C OMPARISON OF OUR PROPOSED GNN-IP A LGORITHM , ZF A LGORITHM AND SDR A LGORITHM IN TERMS
OF AVERAGE COMPUTATION TIME AND SENSING MSE W ITH DIFFERENT NUMBER OF SAMPLE GRIDS N
TABLE III
A C OMPARISON OF OUR PROPOSED GNN-IP A LGORITHM , ZF A LGORITHM AND SDR A LGORITHM IN TERMS OF AVERAGE
COMPUTATION TIME AND SENSING MSE W ITH DIFFERENT COMMUNICATION SINR C ONSTRAINTS Γ0
Table III also shows the average ratio of the projection
module being used and the corresponding average computation
time during the inference stage. From Table III, it can be
clearly observed that our proposed GNN-IP algorithm enjoys
a significantly lower inference computation complexity than
the SDR and ZF algorithms under various SINR constraints.
We also find that the computation time of the GNN-IP
algorithm increases as the communication SINR constraint
increases. This arises from the inclusion of the projection mod-
ule in the GNN-IP algorithm to meet stringent communication
performance requirements. Nevertheless, it can be observed
that when the communication SINR threshold Γ0 ≤ 8, the
projection module is not used, and the computation time of
the projection module is 0. When Γ0 ≥ 9, the output of
the GNN module may not always be feasible, and hence the
projection module is employed to ensure that the constraints
are satisfied. However, the projection module is not frequently
used and the computation time of our proposed algorithm is
still much smaller than that of the SDR algorithm. We also
observe that the proposed GNN-IP algorithm outperforms the
ZF algorithm in terms of both the algorithmic performance
and the computational complexity. It is worth noting that
when the communication SINR constraints change, the pro-
posed GNN-IP algorithm needs to be retrained. However, the
system settings do not change as frequently as the commu-
nication channel state information. The proposed GNN-IP
algorithm exhibits low computation complexity and can be
applied in many practical scenarios, such as smart agriculture,
video streaming, environment monitoring, and remote control
automation [52].
Fig. 10. Satisfaction ratio versus SINR threshold Γ0.
4) Constraint Satisfaction Ratio: In Fig. 10 and Fig. 11,
we investigate the satisfaction ratio of different algorithms
under different communication SINR constraints and differ-
ent number of communication users, where the GNN only
algorithm denotes our proposed GNN-IP algorithm without
the projection module. We denote the satisfaction ratio as the
ratio of the number of samples where the solution feasibility
holds to the total number of samples. We can conclude from
Fig. 10 that the satisfaction ratios of the GNN only algorithm
and the DNN algorithm decrease as the communication SINR
constraint becomes more stringent. Although some efforts,
including adding normalization layer and introducing penalty
terms in the loss function, have been put forward, neither
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

ZHAO et al.: LEARNING TO BEAMFORM FOR INTEGRATED SENSING AND COMMUNICATION 5943
Fig. 11. Satisfaction ratio versus number of communication users.
the GNN only algorithm nor the DNN algorithm guarantees
the feasibility of solutions when the communication perfor-
mance is highly demanding. Besides, the GNN only algorithm
exhibits a slower decline in satisfaction ratio compared to the
DNN algorithm, which demonstrates the superiority of the
graph structure design of our proposed GNN only algorithm.
In contrast, the satisfaction ratio of the GNN-IP algorithm
remains 100% for all values of Γ0 in Fig. 10, since the projec-
tion module in the GNN-IP algorithm can strictly guarantee the
solution feasibility. When the communication SINR constraint
Γ0 increases to 9 dB, the satisfaction ratio achieved by the
GNN only algorithm starts to decline, signifying the activation
of the projection module in the proposed GNN-IP algorithm.
This coincides with the observation that the algorithmic per-
formance and the computation time of the proposed GNN-IP
algorithm deteriorate at Γ0 = 9 dB, as shown in Fig. 8 and
Table III. From Fig. 11, we also observe that the satisfaction
ratios of both the GNN only algorithm and the DNN algorithm
decrease with the increase of the user number. In contrast, the
proposed GNN-IP algorithm consistently maintains a 100%
satisfaction ratio, indicating its effective constraint satisfaction.
V. C ONCLUSION
In this paper, we investigate the joint design of communi-
cation and sensing beamforming matrices in ISAC systems,
where an optimization problem that maximizes the sensing
performance under communication performance constraints is
formulated. To this end, we propose a GNN-IP algorithm
to solve the formulated MSE minimization problem, while
reducing the computation complexity and guaranteeing the
solution feasibility. Simulation results show that the proposed
GNN-IP algorithm approaches the sensing MSE performance
to the SDR algorithm while achieving much less computation
complexity. The results also demonstrate the superiority of
our proposed algorithm in guaranteeing the feasibility of the
solution with respect to the DNN algorithm and the GNN only
algorithm.
REFERENCES
[1] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[2] A. Liu et al., “A survey on fundamental limits of integrated sensing
and communication,” IEEE Commun. Surveys Tuts. , vol. 24, no. 2,
pp. 994–1034, 2nd Quart., 2022.
[3] D. Wen, X. Li, Y . Zhou, Y . Shi, S. Wu, and C. Jiang, “Integrated
sensing-communication-computation for edge artificial intelligence,”
IEEE Internet Things Mag., vol. 7, no. 4, pp. 14–20, Jul. 2024.
[4] J. A. Zhang et al., “An overview of signal processing techniques for joint
communication and radar sensing,” IEEE J. Sel. Topics Signal Process.,
vol. 15, no. 6, pp. 1295–1315, Nov. 2021.
[5] M. Roberton and E. R. Brown, “Integrated radar and communications
based on chirped spread-spectrum techniques,” in IEEE MTT-S Int.
Microw. Symp. Dig., vol. 1, Aug. 2003, pp. 611–614.
[6] G. N. Saddik, R. S. Singh, and E. R. Brown, “Ultra-wideband multi-
functional communications/radar system,” IEEE Trans. Microw. Theory
Techn., vol. 55, no. 7, pp. 1431–1437, Jul. 2007.
[7] E. BouDaher, A. Hassanien, E. Aboutanios, and M. G. Amin, “Towards
a dual-function MIMO radar-communication system,” in Proc. IEEE
Radar Conf., May 2016, pp. 1–6.
[8] M. F. Keskin, H. Wymeersch, and V . Koivunen, “MIMO-OFDM joint
radar-communications: Is ICI friend or foe?” IEEE J. Sel. Topics Signal
Process., vol. 15, no. 6, pp. 1393–1408, Nov. 2021.
[9] J. Johnston, L. Venturino, E. Grossi, M. Lops, and X. Wang, “MIMO
OFDM dual-function radar-communication under error rate and beam-
pattern constraints,” IEEE J. Sel. Areas Commun., vol. 40, no. 6,
pp. 1951–1964, Jun. 2022.
[10] F. Liu, C. Masouros, A. Li, H. Sun, and L. Hanzo, “MU-MIMO
communications with MIMO radar: From co-existence to joint transmis-
sion,” IEEE Trans. Wireless Commun., vol. 17, no. 4, pp. 2755–2770,
Apr. 2018.
[11] L. Chen, F. Liu, W. Wang, and C. Masouros, “Joint radar-communication
transmission: A generalized Pareto optimization framework,” IEEE
Trans. Signal Process., vol. 69, pp. 2752–2765, May 2021.
[12] N. Huang et al., “Mobile edge computing aided integrated sensing and
communication with short-packet transmissions,” IEEE Trans. Wireless
Commun., vol. 23, no. 7, pp. 7759–7774, Jul. 2024.
[13] D. Wen et al., “Task-oriented sensing, computation, and communication
integration for multi-device edge AI,” IEEE Trans. Wireless Commun.,
vol. 23, no. 3, pp. 2486–2502, Mar. 2024.
[14] Y . LeCun, Y . Bengio, and G. Hinton, “Deep learning,” Nature, vol. 521,
no. 7553, pp. 436–444, 2015.
[15] Y . Shi et al., “Machine learning for large-scale optimization in 6G
wireless networks,” IEEE Commun. Surveys Tuts., vol. 25, no. 4,
pp. 2088–2132, 4th Quart., 2023.
[16] N. Cheng et al., “Big data driven vehicular networks,” IEEE Netw.,
vol. 32, no. 6, pp. 160–167, Nov. 2018.
[17] Y . Shi, Y . Zhou, D. Wen, Y . Wu, C. Jiang, and K. B. Letaief, “Task-
oriented communications for 6G: Vision, principles, and technologies,”
IEEE Wireless Commun., vol. 30, no. 3, pp. 78–85, Jun. 2023.
[18] Y . Xu, B. Qian, K. Yu, T. Ma, L. Zhao, and H. Zhou, “Federated
learning over fully-decoupled RAN architecture for two-tier computing
acceleration,” IEEE J. Sel. Areas Commun., vol. 41, no. 3, pp. 789–801,
Mar. 2023.
[19] Y . Zhou, Y . Shi, H. Zhou, J. Wang, L. Fu, and Y . Yang, “Toward scalable
wireless federated learning: Challenges and solutions,” IEEE Internet
Things Mag., vol. 6, no. 4, pp. 10–16, Dec. 2023.
[20] M. Tao et al., “Federated edge learning for 6G: Foundations, method-
ologies, and applications,” Proc. IEEE, early access, Dec. 13, 2024, doi:
10.1109/JPROC.2024.3509739.
[21] C. Liu et al., “Learning-based predictive beamforming for integrated
sensing and communication in vehicular networks,” IEEE J. Sel. Areas
Commun., vol. 40, no. 8, pp. 2317–2334, Aug. 2022.
[22] Y . Zhao, Z. Wang, Z. Wang, X. Chen, and Y . Zhou, “Learning to
beamform for dual-functional MIMO radar-communication systems,” in
Proc. IEEE Int. Conf. Commun., May 2023, pp. 3572–3577.
[23] X. Liu, H. Zhang, K. Long, A. Nallanathan, and V . C. M. Leung, “Dis-
tributed unsupervised learning for interference management in integrated
sensing and communication systems,” IEEE Trans. Wireless Commun.,
vol. 22, no. 12, pp. 9301–9312, Dec. 2023.
[24] Y . Shen, Y . Shi, J. Zhang, and K. B. Letaief, “Graph neural networks for
scalable radio resource management: Architecture design and theoretical
analysis,” IEEE J. Sel. Areas Commun., vol. 39, no. 1, pp. 101–115,
Jan. 2021.
[25] M. Eisen and A. Ribeiro, “Optimal wireless resource allocation with
random edge graph neural networks,” IEEE Trans. Signal Process.,
vol. 68, pp. 2977–2991, 2020.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

5944 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 7, JULY 2025
[26] T. Jiang, H. V . Cheng, and W. Yu, “Learning to reflect and to beamform
for intelligent reflecting surface with implicit channel estimation,” IEEE
J. Sel. Areas Commun., vol. 39, no. 7, pp. 1931–1945, Jul. 2021.
[27] S. W. Golomb and G. Gong, Signal Design for Good Correlation for
Wireless Communication, Cryptography, and Radar. Cambridge, U.K.:
Cambridge Univ. Press, 2005.
[28] D. Sarwate and M. Pursley, “Crosscorrelation properties of pseudoran-
dom and related sequences,” Proc. IEEE, vol. 68, no. 5, pp. 593–619,
May 1980.
[29] E. H. Kim and K. H. Kim, “Random phase code for automotive MIMO
radars using combined frequency shift keying-linear FMCW waveform,”
IET Radar, Sonar Navigat., vol. 12, no. 10, pp. 1090–1095, Oct. 2018.
[30] C. Liao, F. Wang, and V . K. N. Lau, “Optimized design for IRS-assisted
integrated sensing and communication systems in clutter environments,”
IEEE Trans. Commun., vol. 71, no. 8, pp. 4721–4734, Aug. 2023.
[31] X. Shao, C. You, W. Ma, X. Chen, and R. Zhang, “Target sensing
with intelligent reflecting surface: Architecture and performance,” IEEE
J. Sel. Areas Commun., vol. 40, no. 7, pp. 2070–2084, Jul. 2022.
[32] P. Stoica, J. Li, and Y . Xie, “On probing signal design for MIMO radar,”
IEEE Trans. Signal Process., vol. 55, no. 8, pp. 4151–4161, Aug. 2007.
[33] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. Eldar, “Joint
transmit beamforming for multiuser MIMO communications and MIMO
radar,” IEEE Trans. Signal Process., vol. 68, pp. 3929–3944, Jun. 2020.
[34] F. Liu, Y .-F. Liu, A. Li, C. Masouros, and Y . C. Eldar, “Cramér-Rao
bound optimization for joint radar-communication beamforming,” IEEE
Trans. Signal Process., vol. 70, pp. 240–253, 2022.
[35] H. Luo, R. Liu, M. Li, Y . Liu, and Q. Liu, “Joint beamforming design
for RIS-assisted integrated sensing and communication systems,” IEEE
Trans. Veh. Technol., vol. 71, no. 12, pp. 13393–13397, Dec. 2022.
[36] J. Li and P. Stoica, “MIMO radar with colocated antennas,” IEEE Signal
Process. Mag., vol. 24, no. 5, pp. 106–114, Sep. 2007.
[37] D. P. Palomar and Y . C. Eldar,Convex Optimization in Signal Processing
and Communications. Cambridge, U.K.: Cambridge Univ. Press, 2010.
[38] Z.-Q. Luo, W.-K. Ma, A. So, Y . Ye, and S. Zhang, “Semidefinite
relaxation of quadratic optimization problems,” IEEE Signal Process.
Mag., vol. 27, no. 3, pp. 20–34, May 2010.
[39] X. Zhang, H. Zhao, J. Xiong, X. Liu, L. Zhou, and J. Wei, “Scalable
power control/beamforming in heterogeneous wireless networks with
graph neural networks,” in Proc. IEEE Global Commun. Conf. (GLOBE-
COM), May 2021, pp. 1–6.
[40] Z. Wang, Y . Zhou, Y . Zou, Q. An, Y . Shi, and M. Bennis, “A graph neural
network learning approach to optimize RIS-assisted federated learn-
ing,” IEEE Trans. Wireless Commun., vol. 22, no. 9, pp. 6092–6106,
Sep. 2023.
[41] S. Wan, Z. Wang, and Y . Zhou, “Scalable hybrid beamforming for multi-
user MISO systems: A graph neural network approach,” IEEE Trans.
Wireless Commun., vol. 23, no. 10, pp. 13694–13706, Oct. 2024.
[42] K. Xu, W. Hu, J. Leskovec, and S. Jegelka, “How powerful are graph
neural networks?” 2018, arXiv:1810.00826.
[43] Z. Wu, S. Pan, F. Chen, G. Long, C. Zhang, and P. S. Yu,
“A comprehensive survey on graph neural networks,” IEEE Trans.
Neural Netw. Learn. Syst., vol. 32, no. 1, pp. 4–24, Jan. 2021.
[44] K. Xu, C. Li, Y . Tian, T. Sonobe, K.-I. Kawarabayashi, and S. Jegelka,
“Representation learning on graphs with jumping knowledge net-
works,” in Proc. 35th Int. Conf. Mach. Learn., vol. 80, J. Dy
and A. Krause, Eds., 2018, pp. 5453–5462. [Online]. Available:
https://proceedings.mlr.press/v80/xu18c.html
[45] A. Agrawal, B. Amos, S. Barratt, S. Boyd, S. Diamond, and Z. Kolter,
“Differentiable convex optimization layers,” in Proc. Adv. Neural Inf.
Process. Syst., vol. 32, 2019, pp. 9562–9574.
[46] B. Amos and J. Z. Kolter, “OptNet: Differentiable optimization as a
layer in neural networks,” in Proc. Int. Conf. Mach. Learn., vol. 70,
D. Precup and Y . W. Teh, Eds., 2017, pp. 136–145.
[47] M. Grant and S. Boyd. (2014). CVX: MATLAB Software for
Disciplined Convex Programming, Version 2.1. [Online]. Available:
http://cvxr.com/cvx
[48] A. Paszke et al., “PyTorch: An imperative style, high-performance deep
learning library,” in Proc. Adv. Neural Inf. Process. Syst., vol. 32. Red
Hook, NY , USA: Curran Associates, Inc., 2019, pp. 8024–8035.
[49] D. P. Kingma and J. Ba, “Adam: A method for stochastic optimization,”
2014, arXiv:1412.6980.
[50] M. C. Grant and S. P. Boyd, “Graph implementations for nonsmooth
convex programs,” in Recent Advances in Learning and Control,
V . D. Blondel, S. P. Boyd, and H. Kimura, Eds., London, U.K.: Springer,
2008, pp. 95–110.
[51] R. H. Tütüncü, K. C. Toh, and M. J. Todd, “Solving semidefinite-
quadratic-linear programs using SDPT3,” Math. Program., vol. 95, no. 2,
pp. 189–217, 2003.
[52] B. S. Khan, S. Jangsher, A. Ahmed, and A. Al-Dweik, “URLLC and
eMBB in 5G industrial IoT: A survey,” IEEE Open J. Commun. Soc.,
vol. 3, pp. 1134–1163, 2022.
Yifei Zhao received the B.S. degree from the School
of Information Science and Technology, Shang-
haiTech University, Shanghai, China, in 2021, where
he is currently pursuing the Ph.D. degree with the
School of Information Science and Technology. His
research interests include machine learning and inte-
grated sensing and communication.
Yong Zhou (Senior Member, IEEE) received the
B.Sc. and M.Eng. degrees from Shandong Univer-
sity, Jinan, China, in 2008 and 2011, respectively,
and the Ph.D. degree from the University of Water-
loo, ON, Canada, in 2015. From November 2015 to
January 2018, he was a Post-Doctoral Research Fel-
low with the Department of Electrical and Computer
Engineering, The University of British Columbia,
Vancouver, Canada. Since March 2018, he has been
with the School of Information Science and Tech-
nology, ShanghaiTech University, Shanghai, China,
where he is currently a Tenured Associate Professor. His research inter-
ests include 6G communications, edge intelligence, and the Internet of
Things. He was the Track Co-Chair of IEEE VTC 2020 Fall and IEEE
VTC 2023 Spring and the Co-Chair of IEEE ICC 2022 workshop on
edge artificial intelligence for 6G and IEEE Globecom 2024 workshop on
space computing power networks. He serves as an Associate Editor for
IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS and IEEE O PEN
JOURNAL OF THE COMMUNICATIONS SOCIETY .
Zixin Wang (Member, IEEE) received the B.S.
degree from Wuhan University of Technology,
Wuhan, China, in 2018, and the Ph.D. degree from
the University of Chinese Academy of Sciences,
Shanghai, China, in 2024. Since March 2024, he has
been as a Post-Doctoral Fellow with The Hong Kong
University of Science and Technology (HKUST),
Clear Water Bay, Hong Kong, SAR. He visited the
University of Oulu, Oulu, Finland, from November
2022 to December 2023. His research interests
include optimization, machine learning, wireless
communications, and their applications to 6G and edge AI.
Yuanming Shi (Senior Member, IEEE) received the
B.S. degree in electronic engineering from Tsinghua
University, Beijing, China, in 2011, and the Ph.D.
degree in electronic and computer engineering from
The Hong Kong University of Science and Tech-
nology (HKUST) in 2015. Since September 2015,
he has been with the School of Information Science
and Technology, ShanghaiTech University, where he
is a Full Professor. He visited the University of
California at Berkeley, Berkeley, CA, USA, from
October 2016 to February 2017. His research areas
include edge artificial intelligence and large-scale optimization. He is an
IET Fellow. He was a recipient of the IEEE Marconi Prize Paper Award in
Wireless Communications in 2016, the Young Author Best Paper Award by
the IEEE Signal Processing Society in 2016, the IEEE ComSoc Asia-Pacific
Outstanding Young Researcher Award in 2021, the Chinese Institute of
Electronics First Prize in Natural Science in 2022, and the China Institute
of Communications First Prize in Natural Science in 2024. He is an Editor of
IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE J OURNAL
ON SELECTED AREAS IN COMMUNICATIONS , Journal of Communications
and Information Networks, and Space Habitation.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply. 

ZHAO et al.: LEARNING TO BEAMFORM FOR INTEGRATED SENSING AND COMMUNICATION 5945
Nan Cheng (Senior Member, IEEE) received the
B.E. and M.S. degrees in information and telecom-
munications engineering from Tongji University,
in 2009 and 2012, respectively, and the Ph.D.
degree in electrical and computer engineering from
the University of Waterloo in 2016. He was a
Post-Doctoral Fellow with the Department of Elec-
trical and Computer Engineering, University of
Toronto, from 2017 to 2019. He is currently a
Professor with State Key Laboratory of ISN and the
School of Telecommunications Engineering, Xidian
University, Shaanxi, China. He has published over 110 journal articles
in IEEE T RANSACTIONS and other top journals. His current research
focuses on B5G/6G, AI-driven future networks, and space-air-ground inte-
grated networks. He serves as a Steering Committee Member for IEEE
JOURNAL ON MINIATURIZATION FOR AIR AND SPACE SYSTEMS ; and an
Associate Editor for IEEE I NTERNET OF THINGS JOURNAL , IEEE T RANS -
ACTIONS ON VEHICULAR TECHNOLOGY , IEEE O PEN JOURNAL OF THE
VEHICULAR TECHNOLOGY , and Peer-to-Peer Networking and Applications.
He serves/served as a guest editor for several journals.
Haibo Zhou (Senior Member, IEEE) received the
Ph.D. degree in information and communication
engineering from Shanghai Jiao Tong University,
Shanghai, China, in 2014. From 2014 to 2017,
he was a Post-Doctoral Fellow with the Broad-
band Communications Research Group, Department
of Electrical and Computer Engineering, Univer-
sity of Waterloo. He is currently a Full Professor
with the School of Electronic Science and Engi-
neering, Nanjing University, Nanjing, China. His
research interests include resource management and
protocol design in B5G/6G networks, vehicular ad hoc networks, and space-
air-ground integrated networks. He was a recipient of the 2019 IEEE
ComSoc Asia–Pacific Outstanding Young Researcher Award. He served as
the Track/Symposium Co-Chair for IEEE/CIC ICCC 2019, IEEE VTC-Fall
2020, IEEE VTC-Fall 2021, and IEEE GLOBECOM 2022. He is currently
an Associate Editor of IEEE T RANSACTIONS ON WIRELESS COMMUNICA -
TIONS , IEEE I NTERNET OF THINGS JOURNAL , IEEE Network Magazine,
and IEEE W IRELESS COMMUNICATIONS LETTER .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:17:33 UTC from IEEE Xplore.  Restrictions apply.