---
title: "Communication-Control Codesign for Large-Scale Wireless Networked Control Systems"
zotero_key: "CPAWPDHD"
pdf_key: "IGEFR2C5"
doi: "10.1109/JSAC.2025.3574602"
collection: "ISAC"
source: "Zotero imported PDF (pypdf extraction)"
page_mapping: "unknown"
source_sha256: "9cf35e04e8de2c10000ca9adf4eabf23e1bfaa0b129187dea5b7dddb47c22bd7"
pdf_pages: 13
---

# Communication-Control Codesign for Large-Scale Wireless Networked Control Systems — Fulltext

> 由 Zotero 附件 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证。

---


<!-- extraction_page_index: 1 -->

1
Communication-Control Codesign for Large-Scale
Wireless Networked Control Systems
Gaoyang Pang, Wanchun Liu*, Member, IEEE, Dusit Niyato, Fellow, IEEE, Branka Vucetic, Life Fellow, IEEE,
Yonghui Li, Fellow, IEEE
Abstract—Wireless Networked Control Systems (WNCSs) are
essential to Industry 4.0, enabling flexible control in appli-
cations, such as drone swarms and autonomous robots. The
interdependence between communication and control requires
integrated design, but traditional methods treat them sepa-
rately, leading to inefficiencies. Current codesign approaches
often rely on simplified models, focusing on single-loop or
independent multi-loop systems. However, large-scale WNCSs
face unique challenges, including coupled control loops, time-
correlated wireless channels, trade-offs between sensing and
control transmissions, and significant computational complexity.
To address these challenges, we propose a practical WNCS
model that captures correlated dynamics among multiple control
loops with spatially distributed sensors and actuators sharing
limited wireless resources over multi-state Markov block-fading
channels. We formulate the codesign problem as a sequen-
tial decision-making task that jointly optimizes scheduling and
control inputs across estimation, control, and communication
domains. To solve this problem, we develop a Deep Reinforcement
Learning (DRL) algorithm that efficiently handles the hybrid
action space, captures communication-control correlations, and
ensures robust training despite sparse cross-domain variables
and floating control inputs. Extensive simulations show that the
proposed DRL approach outperforms benchmarks and solves
the large-scale WNCS codesign problem, providing a scalable
solution for industrial automation.
Index Terms—Wireless networked control, Industry 4.0, trans-
mission scheduling, and deep reinforcement learning.
I. I NTRODUCTION
Wireless Networked Control Systems (WNCSs) serve as
foundational models for driving the next generation of cutting-
edge technologies in Industry 4.0, enabling advanced applica-
tions such as drone swarms, autonomous vehicles, and mobile
robots [1]–[3]. By eliminating the physical constraints of wired
communication, WNCSs offer unprecedented flexibility and
scalability, supporting distributed sensing and control across
large-scale and complex industrial environments. However, the
transition to wireless communication introduces fundamental
challenges, particularly in maintaining robust control perfor-
mance amidst uncertainties such as delays, packet loss, and
limited wireless resources [4]. These wireless communication
challenges pose a significant threat to system stability and
reliability, necessitating a fundamental rethinking of traditional
control and communication strategies [4].
The work of W. Liu was supported by the Australian Research Council’s
Discovery Early Career Researcher Award (DECRA) Project DE230100016.
(Corresponding author: W. Liu.)
G. Pang, W. Liu, B. Vucetic, and Y . Li are with the School of Electrical and
Computer Engineering, The University of Sydney, Sydney, NSW 2006, Aus-
tralia (e-mail: gaoyang.pang@sydney.edu.au; wanchun.liu@sydney.edu.au;
branka.vucetic@sydney.edu.au; yonghui.li@sydney.edu.au).
D. Niyato is with the College of Computing and Data Science, Nanyang
Technological University, Singapore 639798, (e-mail: dniyato@ntu.edu.sg).
Communication-control codesign in WNCSs addresses
these challenges through a holistic design approach that simul-
taneously optimizes control algorithms and communication
policies. Recognizing the intrinsic interdependence between
control and communication ensures that control algorithms
compensate for uncertainties in wireless communication while
communication strategies adapt to the stringent performance
requirements of control tasks. This correlation is critical, as
control actions directly influence the timing and priority of
data transmission, while the state of the wireless communi-
cation network impacts the effectiveness of control signals
and sensor feedback. Without an integrated codesign approach,
independently optimizing these domains leads to suboptimal
system performance, especially in high-stakes applications
such as drone swarms and robotics, where precise coordination
and timely data exchange are essential for success.
A. Related Work
1) Control-aware communication design for WNCSs: In
this approach, communication policies are optimized under
the assumption that control algorithms are fixed, with the goal
of improving overall control system performance. Significant
research has been dedicated to this design strategy in areas
such as power allocation [5]–[7], transmission scheduling [8]–
[14], and data rate and packet-length adaptation [15]. However,
this method is suboptimal for complex WNCSs because it
neglects to account for the design of the control policy.
In practice, WNCSs often exhibit tightly coupled dynamics
between communication and control, making the two policies
highly interdependent [16]. This interdependence emphasizes
the importance of a codesign approach, where communication
and control are jointly optimized. Such an approach addresses
the limitations of traditional control-aware communication
design and reduces its conservatism [17], [18].
2) Conventional communication-control codesign methods:
Conventional codesign approaches often decompose the prob-
lem into separate subproblems, solving the communication and
control policies independently [19], [20]. In this framework,
the control policy typically takes the form of linear feedback
control (LFC), where the control input is a linear combination
of the estimated plant state, derived based on the statistical
effects of the communication policy. Once an optimal control
policy is determined, the optimal communication schedul-
ing is selected from the policy space to enhance control
performance [21]–[24]. Although communication and control
are optimized iteratively, this step-by-step optimization can
lead to suboptimal performance, as communication decisions
are made without considering their future impact on control
arXiv:2410.11316v1  [eess.SY]  15 Oct 2024

<!-- extraction_page_index: 2 -->

2
performance. Moreover, recalculating the control policy at
each time slot, based on updated communication policies, in-
troduces inefficiencies and instability in dynamic environments
[24]. The failure to fully integrate communication and control
policies results in missing opportunities to leverage their
interdependencies, which limits overall system optimization.
Another class of methods employs model predictive control
(MPC), where the optimization problem is solved iteratively,
producing a finite sequence of communication actions and
control inputs over a prediction horizon [25], [26]. MPC
accounts for the future impact of current decisions and jointly
optimizes both policies. However, finding the best scheduling
policy over long prediction horizons often requires exhaustive
or heuristic searches, which can be computationally intensive
[27]. While recent research has explored approximations and
simplifications to reduce computational complexity and im-
prove the applicability of MPC in WNCSs [28]–[31], these
strategies may compromise the accuracy and effectiveness of
the policies. The computational burden of MPC remains a
significant limitation, particularly for large-scale systems or
those requiring real-time optimization, hindering its scalability
and practical deployment.
3) Codesign approaches with deep reinforcement learning:
To overcome the limitations of conventional codesign methods,
deep reinforcement learning (DRL) has emerged as a promis-
ing alternative for jointly optimizing communication and con-
trol policies [32]. DRL provides a unified framework that
learns optimal policies by interacting with the environment, ef-
fectively capturing the interdependencies between communica-
tion and control systems. Unlike conventional approaches that
focus on short-term gains, DRL leverages cumulative costs,
allowing for decisions that consider the long-term impact of
current actions on future states and control performance. By
employing deep neural networks (DNNs), DRL also addresses
computational inefficiencies in traditional methods, enabling
online execution with reduced computational overhead.
In scenarios with perfect channels, Baumann et al. [33] pro-
posed a DRL algorithm to maximize control performance in
single-loop WNCS with limited transmissions. Funk et al. [34]
enhanced this by introducing a hierarchical DRL framework,
where the algorithm first decides whether to transmit and then
computes control inputs. Kesper et al. [35] and Shibata et al.
[36], [37] extended these techniques to multi-loop WNCS.
Similar DRL methods for single-loop WNCS can be found
in [38]–[40].
For scenarios with imperfect channels , Termehchi et al.
[41] developed a hierarchical DRL algorithm that jointly opti-
mizes actuator scheduling, control policies, channel allocation,
and power allocation in a single-loop WNCS. Zhao et al.
[42] introduced a DRL approach to jointly learn estimation,
communication, and control policies in a single-loop WNCS,
while Lima et al. [43] designed a DRL algorithm that jointly
optimizes power allocation and control in a multi-loop WNCS.
These works demonstrate the effectiveness of DRL in
handling the complexities of WNCSs, where communication
and control systems are tightly coupled. However, significant
challenges remain, especially in scaling these approaches
for large, practical multi-loop WNCSs with limited wireless
Fig. 1. Illustration of multi-loop WNCSs: (a) Network topology of IML and
CML systems. (b) CML WNCSs in warehouse automation.
resources and dynamic environments.
B. Motivations
1) DRL-based codesign for large-scale systems: Existing
DRL methods are largely constrained to small-scale WNCSs
due to oversimplified communication models [33], [34], [38]–
[42]. Scaling these methods to more complex systems presents
significant challenges that limit their effectiveness. One major
issue is the hybrid action space that arises from the need
to handle both discrete communication actions (e.g., chan-
nel allocation) and continuous control inputs (e.g., actuator
commands). As the system grows in size, the hybrid action
space expands exponentially, making it increasingly difficult
for DRL algorithms to explore and learn optimal policies
effectively. This leads to a dramatic increase in computational
complexity and slows down convergence, posing a fundamen-
tal limitation on the scalability of DRL-based solutions.
Furthermore, the complexity is compounded by the pres-
ence of cross-domain variables—where inputs and outputs
from communication, control, and estimation domains interact.
These variables often have widely differing scales, such as
discrete, finite channel assignments versus continuous, poten-
tially infinite control actions. This mismatch in scale can result
in issues such as gradient explosion [44], leading to unstable
training processes and making it harder for DRL models to
converge on effective solutions. The intricate coupling of these
domains further complicates the problem, as decisions made in
one domain (e.g., communication) have cascading effects on
the others (e.g., control and estimation), adding another layer
of complexity to the training process. As a result, current DRL
methods fail to efficiently handle large-scale systems with
hybrid action spaces and cross-domain interactions, severely
limiting their scalability and applicability in real-world, large-
scale WNCSs.
2) Model practicality issues of WNCSs: The practicality
of existing multi-loop WNCS models faces two significant
issues: the lack of coupling effects in plant state dynamics
and oversimplified communication models.
Lack of Coupling Effect in Control. Most existing works
focus on single-loop (SL) systems [19]–[21], [28], [30], [33],
[34], [38]–[42], [45] or independent multi-loop (IML) systems
[22]–[24], [29], [32], [35]–[37], [43]. In WNCSs, a control
loop refers to the closed feedback loop between sensors, con-
trollers, and actuators, where the system state is continuously

<!-- extraction_page_index: 3 -->

3
monitored by sensors, decisions are made by controllers, and
corrective actions are taken by actuators. In IML systems (see
Fig. 1(a)), control loops operate independently, and controllers
are designed separately for each loop, focusing solely on local
performance in each loop only. In this case, plants (physical
systems being controlled) are independent, meaning the state
of one plant does not directly influence the state or control
strategy of another plant. Each control loop is concerned with
optimizing its own system’s performance without considering
interactions or dependencies with other control loops.
In contrast, coupled multi-loop (CML) systems (see
Fig. 1(a)) involve interdependent control loops, where the
states of different plants are correlated. Sensor measurements
from one plant may be influenced by the states of others, and
control actions taken for one plant can affect the dynamics of
others. For instance, an actuator’s action may alter the behavior
of other plants due to shared environments or constraints. An
example is shown in Fig. 1(b), where robots navigate different
sections to retrieve and deliver goods in a warehouse. The edge
controller coordinates robot actions by receiving sensor data
(e.g., position and load) via uplink transmissions and sending
control commands (e.g., speed and braking) via downlink.
These control loops are interdependent; for example, if one
robot slows down to avoid a collision, it may delay others
reliant on timely item handovers. Such interdependencies are
critical for coordinated and efficient control in CML systems,
which are rarely considered in the literature.
Lack of Coupling Effect in Communications. Existing
works on multi-loop WNCSs rarely consider joint uplink
(sensor-to-controller) and downlink (controller-to-actuator)
communication scheduling with shared wireless resources. In
most studies, communication scheduling is treated separately
for uplink and downlink transmissions, often focusing on a
specific type of communication while neglecting the resource
contention between the two.
However, in practical WNCSs, both uplink and downlink
communications compete for the same limited wireless re-
sources, making joint scheduling essential. The state estima-
tion accuracy relies on timely sensor data (uplink), while con-
trol performance depends on the delivery of control commands
(downlink). Failing to jointly schedule these transmissions
can lead to inefficiencies, such as over-allocating resources to
sensor updates when control commands are more urgent, or
vice versa. For example, in a warehouse with multiple robots,
allocating too many resources for sensors to collect position
data might delay critical control commands needed to prevent
a collision. Thus, in CML WNCSs, the communication and
control processes are deeply intertwined, and joint uplink-
downlink scheduling is crucial to balance resource allocation
and ensure optimal system performance.
C. Contributions
In this work, we tackle the above challenges. The novel
contributions are summarized below.
1) Practical model of WNCSs : We propose a practical
model for CML WNCSs that addresses the real-world com-
plexities of distributed sensing and actuation, with sensors and
actuators sharing limited wireless resources for both uplink
and downlink transmissions. Unlike existing models that often
rely on oversimplified assumptions, our approach captures the
interdependencies between plant dynamics and communica-
tion, recognizing that the overall system performance hinges
on both communication and control policies. By incorporating
short-packet communications and modeling wireless channels
using multi-state block Markov fading [46], the model reflects
the time-correlated nature of wireless channels prevalent in
industrial settings. Additionally, to account for the limited
wireless resources and varying channel quality, we introduce
state estimation strategies that estimate the overall system state
based on partially observed sensor data when not all sensor
packets are successfully transmitted. This comprehensive and
practical model offers a robust framework for solving the
communication-control codesign problem, enabling its appli-
cation in large-scale WNCS environments where real-world
constraints are crucial.
2) Novel problem formulation : We establish a novel
Markov Decision Process (MDP) formulation for the
communication-control codesign problem of the WNCS. The
MDP integrates a comprehensive state representation that
includes estimated plant states, estimation quality states, chan-
nel quality states, and control quality states. This enriched
state space uniquely captures the complex interdependencies
between the control system and the wireless network, enabling
more context-aware decision-making. The action space in-
cludes both the dynamic allocation of frequency channels and
the generation of control inputs, addressing communication
and control tasks simultaneously under resource constraints.
By unifying these elements within the MDP framework, our
approach advances communication-control codesign strategies,
improving control performance in practical CML WNCS en-
vironments. The codesign MDP introduces several complex
challenges: the management of a large and hybrid action
space (both discrete and continuous), the need to capture
the correlation between communication and control policies,
and handling cross-domain variables, all while maintaining
training efficiency.
3) Advanced DRL algorithm : We propose an innovative
Graph-enhanced Cascaded Actor DRL (GCA-DRL) algorithm
to address the challenges of communication-control codesign.
The dual-branch architecture encodes scheduling and con-
trol policies separately. The scheduling branch generates a
continuous weight matrix for device-to-channel assignment,
mapped to discrete actions using a graph-based embedding
that leverages domain-specific communication knowledge for
efficient exploration. This output is cascaded into the control
branch, allowing real-time adaptation of control decisions
based on communication resource allocation and effectively
capturing the interdependencies between policies. To manage
cross-domain variables, layer normalization is applied after
each hidden layer, stabilizing training and balancing learning
across different variable scales. A partial policy gradient up-
date mechanism further enhances efficiency by focusing only
on gradients from effective control inputs, filtering out noise
from unscheduled actuators. These innovations improve train-
ing stability, convergence, and performance, with extensive

<!-- extraction_page_index: 4 -->

4
numerical results demonstrating that the proposed algorithm
outperforms all benchmark policies, making it highly effective
for optimizing communication-control codesign in large-scale
WNCSs.
Outlines. The rest of this article is organized as follows.
The proposed system model of the WNCS is described in
Section II. The codesign problem formulation is presented in
Section III. The advanced DRL algorithm to solve the codesign
problem is detailed in Section IV. Numerical simulation is
demonstrated and discussed in Section V, followed by a
conclusion in Section VI.
Notations. Matrices and vectors are denoted by capital and
lowercase upright bold letters, e.g., A and a, respectively. |v|
is the Euclidean norm of vector v. E [·] is the expectation
operator. [A]i,j denotes the element at i-th row and j-th
column of a matrix A. ρk (A) represents the k-th eigenvalues
of the matrix A. (·)⊤ is the vector or matrix transpose operator.
Tr(·) is the matrix trace operator. Pr[·] is the probability
operator. R denotes the set of real numbers.
II. P ROPOSED MULTI-LOOP WNCS M ODEL
We consider a multi-loop WNCS consisting of an intel-
ligent edge controller, M spatially distributed sensors, and
N actuators within a large integrated plant, as shown in
Fig. 2. The large integrated plant is modeled as a collection of
interdependent control tasks spanning multiple plants. Sensors
transmit state measurements to the edge controller, while
actuators execute the control commands received from the
edge controller. All devices are equipped with a single antenna
for communication. Communication links for all devices are
established over L wireless frequency channels (i.e., subcar-
riers), where 1 ≤ L ≤ N + M. The index sets of channels,
sensors, and actuators are denoted as L≜{1, 2, . . . , L}, M≜
{1, 2, . . . , M}, and N ≜ {1, 2, . . . , N}. The edge controller
implements an estimator to track the plant states and employs
a dynamic policy for joint channel allocation and control.
A. Plant Dynamics
The plant dynamics is modeled as a linear discrete-time
system with a sampling time period of Ts:
x(t + 1) = Ax(t) + Burx(t) + w(t), (1a)
ytx(t) = Cx(t) + v(t), (1b)
urx(t) = Λ(t)utx(t), (1c)
yrx(t) = Ψ(t)ytx(t), (1d)
where A∈RK×K, B∈RK×N , C∈RK×M are system matrices.
Markov plant state dynamics (1a). The plant state is
modeled as a multi-dimensional vector x(t) ∈ RK, where
K represents the number of state dimensions. The evolution
of the plant state over time is influenced by two factors:
the control input urx(t) received by the plant and a process
noise vector w(t) ∈ RK. The noise vector w(t) is assumed
to be an independent and identically distributed (i.i.d.) zero-
mean Gaussian process with a covariance matrix W. The next
state x(t + 1) depends on the current state x(t), the control
input urx(t), and the plant noise w(t). The set of all state
Fig. 2. Illustration of the core components a CML WNCS.
dimensions is denoted as K ≜ {1, 2, . . . , K}. We assume that
each state dimension is unstable, i.e., ρk(A) > 1, ∀k ∈ K,
meaning that without control inputs, the state vector x(t) will
grow unbounded over time, i.e., urx(t) = 0, ∀t.
Transmitted and received sensor measurements (1b) and
(1d). The plant’s sensor measurements are given by ytx(t),
where C ∈ RM ×K is the measurement matrix that maps the
true plant state x(t) to the observed sensor outputs. Since
sensors may only capture part of the full system state, C
reflects this partial observability. The noise vector v(t) ∈ RM ,
modeled as an i.i.d. zero-mean Gaussian process with covari-
ance matrix V, further distorts the accuracy of the measure-
ments. Each measurement corresponds to an individual sensor.
Due to potential packet loss and limited wireless resources,
the edge controller may not receive all sensor measurements.
The received measurements at the controller are denoted
as yrx(t) ∈ RM , where Ψ(t) ∈ 0, 1M ×M is a binary
diagonal matrix that indicates successful packet transmissions.
Specifically, ϕm(t) ≜ [Ψ(t)]m,m = 1 means that the m-th
sensor’s measurement has been successfully received by the
edge controller.
Transmitted and received control inputs (1c). The plant
control input urx(t) ∈ RN consists of N dimensions, with
each dimension corresponding to a control signal for one of
the N actuators. The control signals transmitted from the edge
controller are represented as utx(t) ∈ RN . Due to unreliable
wireless communication, not all control signals are success-
fully received by the actuators. This is captured by the binary
matrix Λ(t) ∈ {0, 1}N ×N , where λn(t) ≜ [Λ(t)]n,n = 1
indicates successful transmission to the n-th actuator. If a
control signal is not received (i.e., λn(t) = 0 ), the actuator
follows a zero-input policy.
This assumption, where each sensor measures a single
dimension and each actuator is associated with one control
signal, is commonly used in industrial automation [13], [15],
[27]. It simplifies the system by avoiding redundant measure-
ments and overlapping feedback, ensuring more precise con-
trol. Although multi-dimensional sensors and actuators exist,
focusing on single-dimensional devices makes the codesign
problem more tractable without sacrificing generality.
B. Wireless Communications
Communication channels are commonly time-correlated and
are quantized to finite discrete states to reflect dynamic
channel properties of complex industrial indoor environments

<!-- extraction_page_index: 5 -->

5
with many mobile machines, vehicles, and robots. Thus, we
consider finite-state time-homogeneous Markov block-fading
channels [46]. The channel states remain constant during a
time slot of Ts and changes slot-by-slot. The edge controller
has the knowledge of channel state information achieved by
standard channel estimation and feedback techniques.
Let gsm(t) ≜ (gsm,1(t), gsm,2(t), . . . , gsm,L)⊤, ∀m ∈ M
and gcn(t) ≜ (gcn,1(t), gcn,2(t), . . . , gcn,L)⊤, ∀n ∈ Nrepresent
the channel power gain of sensor m and actuator n at L
channels, respectively. Each channel power gain has H states,
i.e., G ≜ {h1, h2, . . . , hH } and is modelled as a multi-state
Markov chain. Since devices are dislocated and have different
radio propagation environments, we assume that the Markov
channel states are independent. The transition matrices of
channel power gain for sensors and actuators at L channels
are denoted as Msm,l ∈ RH×H , ∀m ∈ M and Mcn,l ∈
RH×H , ∀n ∈ N, respectively. The overall channel state infor-
mation (CSI) is G(t) ≜ [gs1(t), . . . ,gsM (t), gc1, . . . ,gcN (t)] ∈
GL×(M +N ) ≜ { ˜G1, ˜G2, . . . ,˜GL×(M +N )}. Let M ∈
RH L×(M +N )×H L×(M +N ) denote the overall channel state tran-
sition matrix
[M]i,j ≜ phi,j = Pr hG(t + 1) = ˜Gj | G(t) = ˜Gii , (2)
which can be calculated by the Kronecker product of {Msm,l}
and {Mcn,l}. We note that the channel state transition matrix
is unknown to the edge controller because the estimation of
a multi-dimensional Markov chain model is computationally
intensive [47].
We adopt the short-packet communications for uplink and
downlink transmissions [48]. In short-packet communications,
the decoding failure probability of a packet depends on the
packet length, the data bits, and the signal-to-noise ratio
(SNR). Thus, the decoding failure probability of a packet can
be approximated as [48]
ε (γ) ≈ Q

 C (γ) − blq
V(γ)
l

 , (3)
where Q(x) = 1√2π R ∞x e− t22 dt is the Gaussian Q-function;l is the sensor packet length in symbols; b is the number of
data bits; γ is the SNR of a packet; C(γ) = log 2 (1 + γ) is
the Shannon capacity; V(γn) = (1 − (1 + γ)−2)(log2 e)2 is
the channel dispersion.
Each device (either a sensor or an actuator) takes at most
one channel for transmission, and each channel is allocated
to a single device. In this regard, sensing and control are
performed in an off-band full-duplex mode, where a sensing
packet and a control packet can be scheduled at different
frequency channels at the same time slot. We denote the
channel allocation for sensor m at actuator n at the L channels
as binary vectors dsm(t) ≜ (dsm,1(t), . . . , dsm,L(t))⊤ ∈ {0, 1}L
and dcn(t) ≜ (dcn,1(t), . . . , dcn,L(t))⊤ ∈ {0, 1}L, respectively.
dsm,l(t) = 1 or dcn,l(t) = 1 denotes that channel l is allocated
to sensor m or actuator n, respectively. Thus, the overall
channel allocation for all devices is D(t) ≜ [Ds(t), Dc(t)] =
[ds1(t), . . . ,dsM (t), dc1(t), . . . ,dcN (t)] with the constraint
MX
m=1
dsm,l(t) +
NX
n=1
dcn,l(t) ≤ 1, ∀l ∈ L. (4)
Each device uses full power for transmission. Given the
transmission power budget Pmax and the receiving noise power
σ2, the receiving SNR of sensor m and actuator n is
γsm(t) =dsm(t)⊤gsm(t)Pmaxσ2 , γcn(t) =dcn(t)⊤gcn(t)Pmaxσ2 . (5)
Taking (5) into (3), the decoding error probability of a packet
of sensor m and actuator n can be expressed as
εsm(t) ≜ ε(γsm(t)), εcn(t) ≜ ε(γcn(t)). (6)
Then we have Pr[ϕm(t) = 1] = 1 − εsm(t) and Pr[λn(t) =
1] = 1 − εcn(t).
C. State Estimation
Due to the presence of noise, represented by v(t) and w(t),
and the partial observability introduced by the matrix C, along
with imperfect communication (such as decoding errors and
limited channel access) of sensing packets, the true plant state
x(t) is not directly observable by the edge controller. Instead,
the controller must rely on an estimated state, ˆx(t). Therefore,
a state estimator is implemented on the controller side.
We assume that the edge controller has complete knowledge
of the constant system matrices A, B, C, W, and V, and
can detect whether received sensing packets are successfully
decoded through cyclic redundancy check (CRC), indicated
by Ψ(t). Additionally, we assume that the controller receives
perfect feedback from the actuators regarding the success of
control packet transmissions, captured by Λ(t). This ensures
that the controller knows both the received control inputs
urx(t) and sensor measurements yrx(t). Given this informa-
tion, the controller performs optimal state estimation using a
modified Kalman filter (mKF) with partially observed sensing
measurements [27], formulated as follows:
ˆx−est(t)≜Aˆxest(t − 1) + Burx(t − 1), (7a)
P−est(t)=APest(t − 1)A⊤ + W, (7b)
Kest(t)=P−est(t)C⊤Ψ(t)⊤ Ψ(t)CP−est(t)C⊤Ψ(t)⊤+V−1,(7c)
ˆxest(t)≜ˆx−est(t) + Kest(t)  yrx(t) − Ψ(t)Cˆx−est(t), (7d)
Pest(t)=(I − Kest(t)Ψ(t)C) P−est(t), (7e)
where I is the M × M identity matrix; ˆx−est(t) is the prior
state estimate; ˆxest(t) is the posterior state estimate of x(t)
at time t, i.e., the pre-filtered measurement of yrx(t); Kest(t)
is the time-varying Kalman gain; The matrices P−est(t) and
Pest(t) represent the prior and posterior error covariance at
the sensor at time t, respectively. (7a) and (7b) present the
prediction steps while (7c), (7d), and (7e) correspond to the
updating steps.
At the beginning of each time slot, the controller generates
control commands based on the current plant state estimation
and transmits them within the same time slot. However, due to
a one-step transmission delay, the sensing packets measuring
the current plant state are only received at the end of the time

<!-- extraction_page_index: 6 -->

6
slot. As a result, the controller must rely on the state estimation
from the mKF obtained in the previous time slot. Therefore,
to estimate the current plant state, the controller updates the
current estimation by
ˆx(t) ≜ Aˆxest(t−1)+ Burx(t−1). (8)
The corresponding estimation error covariance matrix P(t) is
P(t) ≜ E
h
(ˆx(t) − x(t)) (ˆx(t) − x(t))⊤
i
,
= APest(t−1)A⊤+W. (9)
D. Performance Metrics
We focus on the discounted control cost of (1) defined as
J = lim
T →∞
E
"T −1X
t=0
βt x(t)⊤Qx(t)+ urx(t)⊤Rurx(t)
#
, (10)
where β ∈ (0, 1] is a discount factor, and Q and R are
positive semi-definite weighting matrices for the state and
control input, respectively. The discount factor introduces a
time-weighting mechanism, allowing flexibility in controlling
the trade-off between short-term responsiveness and long-term
performance. The control cost in (10) reflects the deviation of
the plant state x(t) from desired states (assumed to be zero for
simplicity) and the energy required for control inputs urx(t).
Our goal is to minimize these deviations and do so efficiently
by reducing the overall control cost.
By leveraging the state estimation ˆx(t) in (8) and the
estimation error covariance matrix P(t) in (9), we have the
following equality
E[x(t)⊤Qx(t)] = ˆx(t)⊤Qˆx(t) + Tr(QP(t)). (11)
By substituting (11) into (10), it becomes clear that minimizing
the control cost inherently requires reducing the estimation
error P(t). Thus, the objective of minimizing the control cost
translates into finding an optimal codesign policy that keeps
the system close to its desired state while efficiently managing
the estimation error caused by noise and uncertainties in
wireless communications. This control cost framework aligns
with the goals of the codesign problem because it addresses
two critical factors: 1) balancing communication resources
between sensing and control to maintain system observability
and control accuracy, and 2) generating intelligent control
inputs that efficiently regulate the system state.
E. Codesign Policies
The edge controller implements a codesign policy that
dynamically schedules system devices and generates con-
trol commands based on the available information from the
WNCS. This codesign policy maps the system state (i.e., the
available information) to an action, which can be expressed
as:
(D(t), utx(t)) = π(s(t)), (12)
where π(·) is the codesign policy that generates the overall
channel allocation D(t) for all devices and the control inputs
utx(t) for all actuators; s(t) is the system state and will be
discussed in the next section.
In the WNCS, uplink (sensor measurements) and down-
link (control signals) transmissions share limited wireless
resources. The control cost depends on both the accuracy
of state estimation (influenced by uplink transmissions) and
the effectiveness of control actions (dependent on downlink
transmissions). As a result, decisions in communication and
control are interdependent. For example, the control policy
requires timely, accurate sensor data, while the communication
policy must prioritize transmissions based on the system’s con-
trol demands. Optimizing communication without considering
control requirements can lead to inefficiencies, such as over-
allocating resources to sensor updates when control actions
are more critical. Unlike traditional approaches that treat
communication and control separately, the codesign policy
in (12) jointly optimizes both, acknowledging their interde-
pendencies. It ensures communication scheduling supports
control needs, and control decisions are made inherently with
communication limitations. In the next section, we formally
define the codesign problem for the WNCS.
III. C ODESIGN PROBLEM FORMULATION
We aim to find a deterministic and stationary codesign
policy in (12) that generates actions at each time slot to
minimize the discounted control cost (10). This involves
jointly optimizing the objectives across estimation, control,
and communication domains. The problem can be formulated
as an MDP, as it is inherently a sequential decision-making
task. The Markovian property holds clearly due to the Markov
channel modeling in (2) and (6) as well as the updating rule
in (1) and (8). In the sequel, we present the MDP formulation
for the codesign problem.
A. MDP Formulation
1) States: Given the estimated plant state ˆx(t) ∈ RK, the
estimation quality state P(t) ∈ RK×K, the control quality
state urx(t − 1) ∈ RN , and the CSI state G(t) ∈ GL×(M +N ),
the MDP state set is defined as s(t) ≜ {ˆx(t), P(t), urx(t −
1), G(t)} ∈RK × RK×K × RN × GL×(M +N ). Integrating
the estimated plant state and the estimation quality state
enables the policy to be aware of the sensing and control
performance. The inclusion of a control quality state helps
agents make smart control decisions by making full use of the
effective control efforts in the last time slot. This can justify
the effectiveness of the previously generated control inputs,
evaluate their impacts on the control system, and estimate the
control availability, making better-informed control decisions.
The CSI state determines the channel quality and affects the
updating of the estimation quality state, the control quality
state, and the estimated plant state, thereby impacting the
control cost.
2) Actions: Given the generated control input utx(t) ∈ RN
and the channel allocation D(t) ∈ {0, 1}(N +M )×L under
constraint (4), the MDP action set is defined as a(t) ≜
{D(t), utx(t)} ∈ {0, 1}(N +M )×L × RN . In the codesign
problem, the action allocates L frequency channels to (M +N )
devices and decides the continuous control inputs for N
actuators. The discrete action space is defined by the number

<!-- extraction_page_index: 7 -->

7
of all possible allocations, which is denoted as Ad with the
cardinality of |Ad| = PLl=1 L!l!(L−l)! (M +N )!(M +N −l)!. The continuous
action space for control is defined as Ac ≜ RN . Thus, the
hybrid actions space is denoted as A ≜ Ad × Ac.
3) Transitions: Let s+(t) ≜ {ˆx(t), P(t), urx(t − 1)} rep-
resent the state set excluding the CSI. s+(t) and G(t) are
independent. Hence, the state-transition probability from s(t)
to s(t + 1) under a particular action a(t) is
Pr[s(t + 1) | s(t), a(t)]
= Pr[G(t + 1) | G(t)] Pr[s+(t + 1) | s(t), a(t)], (13)
where Pr[G(t + 1)|G(t)] is the transition probability of the
channel state and can be directly obtained from the channel
state transmission matrices [M]i,j in (2). Pr[s+(t+ 1)|s(t), a(t)]
in (13) is related to the transition probability of the estimated
plant state, the estimation quality state, and the control quality
state, which can be obtained directly from the decoding failure
probability in (6) and the updating rule in (1) and (8).
4) Costs: By substituting (11) into (10), (10) can be rewrit-
ten as
J ∗=min
π(·)
lim
T →∞
E
"T −1X
t=0
βtc(t)
#
, (14)
where c(t) =ˆx(t)⊤Qˆx(t)+Tr(QP(t))+urx(t)⊤Rurx(t) is one-
step cost. The one-step cost c(t) penalizes the error of the
estimated plant state, the state estimation error, and control
efforts at each time slot, respectively. The MDP solution aims
to find a codesign policy for minimizing the total cost J ∗
in (14) accumulating one-step costs c(t) over time with a
discount factor β. The edge controller fully observes the MDP
state by the assumptions presented in Section II and can
calculate the one-step cost at each time slot.
B. Challenges for DRL-based Codesign
The formulated MDP problem motivates the utilization of
DRL. On one hand, closed-form expressions between the
cost function (14) and system state s(t) are analytically
intractable. On the other hand, the formulated MDP problem is
mixed-integer, nonlinear programming, and NP-hard, making
it impossible to solve efficiently with traditional methods for
solving MDPs, such as value iteration, policy iteration, and
linear programming. These challenges necessitate the devel-
opment of advanced DRL approaches to address the codesign
MDP problem. However, the following characteristics of the
codesign MDP pose challenges to DRL-based solutions.
1) Large and hybrid action space: The formulated MDP
presents a large and hybrid action space A, which poses
a significant challenge for conventional single-agent DRL
approaches, typically designed to handle either discrete or
continuous action spaces, but not both simultaneously. A
common approach is to decouple the hybrid action space using
two separate DRL agents, one responsible for discrete actions
and the other for continuous actions, forming a hierarchical
or dual-agent DRL framework [34], [35], [42]. However,
this introduces a non-stationary environment, making learning
unstable and convergence difficult, as the interaction between
agents destabilizes the training process [41]. Moreover, this
approach suffers from the curse of dimensionality as the
system scales, especially in the discrete action space, even with
modest numbers of devices and channels. For example, when
M = N = L = 5, the MDP has 63,590 discrete actions for
channel assignment and 5 continuous actions for control. For
M = N = L = 10, the number of discrete actions increases to
approximately 15 × 1011, with 10 continuous control actions.
This explosion in action space makes training a DRL
agent extremely challenging, requiring DNNs with large stor-
age and high computational complexity. As a result, current
communication-control codesign methods are limited to small
system scales. For instance, prior works [34], [35], [42] only
consider two discrete actions, i.e., whether or not to communi-
cate. One potential solution is to approximate the large discrete
action space with continuous values, allowing a single DRL
agent to handle both discrete and continuous actions. This
is feasible for actions with some continuity, such as discrete
time intervals [38]–[40], but not for channel assignment, where
“continuity” lacks physical meaning. Alternative approaches,
such as threshold triggers [36], [37] or priority mechanisms
[33], [49], introduce a mapping between continuous outputs
and discrete actions, but they often lead to unstable training
and suboptimal policies due to the non-smooth nature of the
mapping.
2) Correlated communication and control policies: In
DRL-based codesign, a significant challenge lies in effectively
capturing the correlation between the communication policy
and the control policy. Although the one-step cost function in
the codesign problem accounts for the joint effects of both
policies, a basic DRL algorithm may struggle to learn the
complex interactions between them. This is because the cost
function reflects the outcome of the chosen actions, but it does
not explicitly model the underlying dependencies between
communication and control. As a result, the DRL agent might
only indirectly learn the relationship between the two policies
through the scalar cost, which can lead to suboptimal policy
learning. Without a mechanism to directly integrate these
interdependencies, the DRL agent may fail to fully optimize
the system performance.
One approach to address the correlation between commu-
nication and control policies is to use two separate actors or
dual agents, with each agent specializing in one policy [34],
[35], [42]. However, this design lacks a direct mechanism for
sharing information between scheduling and control decisions,
limiting the ability to fully capture their interdependencies.
Alternatively, a single-branch actor that encodes both poli-
cies with a shared representation [33], [36]–[40] improves
coordination but weakens the ability to handle the specific
needs of each policy domain—communication and control.
The main challenge is to create a mechanism that allows
efficient information sharing between the two policies while
ensuring that their unique roles—managing communication
and control—are effectively optimized together.
3) Cross-domain variables and floating control inputs:
In the MDP state space, we encounter variables from dif-
ferent domains: the estimated plant state ˆx(t) from control,
the estimation quality state P(t) from estimation, and the
channel quality state G(t) from communication. Similarly, the

<!-- extraction_page_index: 8 -->

8
action space includes continuous control inputs and discrete
channel allocation decisions, spanning these different domains.
This heterogeneity in cross-domain input and output variables
presents significant challenges for DRL due to their differing
scales, units, and coupled dynamics.
DNNs, which are employed in DRL, assume input variables
are on similar scales and distributions. The varying scales of
cross-domain variables can disrupt training, as certain vari-
ables may dominate the learning process, leading to skewed
gradient updates during backpropagation. This imbalance hin-
ders the DNN’s ability to learn an effective policy across all
domains. Additionally, the interdependencies between control,
estimation, and communication mean that a change in one
domain can propagate and affect others, further complicating
the learning process. For large-scale WNCSs with numerous
variables, it is crucial that the DRL model accurately cap-
tures these interactions while maintaining balanced sensitivity
across all domains in both the state and action spaces.
Another issue arises with floating control inputs, where the
DRL may output control signals for actuators that have not
been scheduled during training. These floating actions are in-
effective because they do not influence the system’s behavior,
as the corresponding actuators are inactive. However, they still
introduce noise and irrelevant data into the training process.
The presence of these unused actions can mislead the learning
algorithm by adding unnecessary complexity, making it harder
for the DRL model to identify meaningful patterns between
actions and their actual effects on the system. This noise can
distort the gradients during backpropagation, slowing down
convergence and reducing the effectiveness of policy updates.
In particular, it complicates the learning process by increasing
the variance in the training data, making it more challenging
to learn a robust and efficient policy. These challenges have
not been adequately addressed in existing works [32]–[42].
IV. DRL A LGORITHM FOR THE CODESIGN PROBLEM
To address the challenges outlined in Section III-B, we
introduce the novel GCA-DRL algorithm, as illustrated in
Fig. 3. GCA-DRL is a deterministic DRL algorithm that builds
upon the Twin Delayed Deep Deterministic Policy Gradient
(TD3) algorithm [50]. TD3 is an actor-critic method known
for mitigating overestimation bias and improving learning
stability—two key issues in dynamic, high-variance environ-
ments. Compared to other DRL methods, TD3’s twin critic
architecture and delayed policy updates make it more robust
against the overestimation and instability that can arise in
complex decision-making problems, including the codesign
problem. These advantages enable TD3 to handle intricate in-
terdependencies between communication and control policies
more effectively than alternatives, such as Deep Deterministic
Policy Gradient (DDPG) or Proximal Policy Optimization
(PPO), which may struggle with biased learning and unsta-
ble convergence in such environments. In this section, we
first present the fundamentals of the vanilla TD3 algorithm,
followed by our specific innovations tailored to address the
unique challenges of the codesign problem.
A. Vanilla TD3 Algorithm
1) Basic Architecture: The TD3 algorithm consists of two
actor networks and two critic networks. The main actor
network, πa(s(t); θ), maps the current state s(t) to an action
µ(t), where θ represents the network parameters. To encourage
exploration during training, Gaussian noise ϵ(t) ∼ N(0, σ2a) is
added to the action, resulting in ˜a(t) =µ(t) +ϵ(t). The objective
is to minimize the long-term cumulative cost, defined in (14),
by selecting actions that reduce the overall cost over time.
The two critic networks, Q1(s(t), ˜a(t); φ1) and
Q2(s(t), ˜a(t); φ2), estimate the expected cumulative cost
for each state-action pair and provide feedback to the main
actor. These networks use different sets of parameters,
φ1 and φ2, to prevent overestimation bias—a common
problem in single-critic architectures, where the critic tends
to overestimate the value of certain actions. By using two
critics, TD3 mitigates this bias by taking the minimum of the
two Q-values, ensuring more conservative and stable updates.
This helps guide the actor to select actions that consistently
minimize long-term costs. The Q-value for each critic is:
Qk(s(t), ˜a(t); φk) ≈ E
" ∞X
i=0
−βic(t+i)
s(t), ˜a(t), φk#.
TD3 also employs a target actor network, ˆπ(s(t); ˆθ), and
two target critic networks, ˆQ1 and ˆQ2, to improve stability
during training. The target networks are slow-moving copies of
the main networks, and they help stabilize learning by provid-
ing more consistent target values during updates, reducing the
likelihood of sudden shifts in policy. The target actor generates
actions ˆa(t) by adding clipped noise, and the critics compute
Q-values. Critic updates are performed using the minimum of
the two Q-values from the target critics, which helps reduce
overestimation bias and ensures conservative updates.
Both the actor and critic networks are fully connected,
feedforward structures with multiple hidden layers and ReLU
activations. The main and target networks share similar archi-
tectures but are initialized with different parameters to reduce
bias and ensure robustness during learning.
2) Training Algorithm: The training process of TD3 al-
ternates between experience generation and policy updates.
Below, we outline the key steps and high-level concepts of
TD3. Using the actor network πa(·; θ), the TD3 agent contin-
uously interacts with the environment, sampling transitions in
the form of (s(t), ˜a(t), c(t), s(t + 1)), which are stored in a
replay buffer. The TD3 agent then randomly samples a mini-
batch of B transitions from the replay buffer, represented as
< si, ˜ai, ci, s
′
i >, for each i ∈ {1, 2, . . . , B}. We define the
temporal-difference (TD) error for each transition as:
TDki ≜ yi − Qk(si, ˜ai; φk), ∀k ∈ {1, 2}, (15)
where the TD target yi is
yi ≜ −ci + β mink∈{1,2} ˆQk(s′i, ˆπa(s′i; θt) + ϵ′; ˆφk). (16)
The TD3 agent updates the parameters of the critic networks
by minimizing the following loss function across all sampled

<!-- extraction_page_index: 9 -->

9
Fig. 3. Illustration of GCA-DRL: (a) Learning structure. TD denotes temporal
difference. (b) Dual-branch actor and action embedding scheme.
transitions:
Lk(φk) = 1B
BX
i=1
TDki 2, ∀k ∈ {1, 2}, (17)
where TDki is defined in (15).
Next, the actor network is updated by using the following
policy gradient to minimize the expected cumulative cost:
∇θLa(θ) = 1B
BX
i=1
Gai Gπi ,
Gai ≜ ∇˜ai mink∈{1,2} Qk(si, ˜ai; φk),
Gπi ≜ ∇θπa(si; θ),
where Gai is the gradient of the minimum critic output with
respect to the action ˜ai, and Gπi is the gradient of the actor’s
output with respect to the actor parameters. Both gradients are
evaluated for each state si.
Finally, the TD3 agent periodically updates the target net-
works’ parameters, ˆθ and ˆφk, with the latest parameters θ and
φk from the main networks, respectively.
B. Proposed GCA-DRL
1) Cascaded dual-branch actor network for joint communi-
cation and control optimization: To address the challenges of
correlated communication and control policies and the cross-
domain variables in the codesign problem, we propose the
GCA-DRL, designed with a dual-branch actor network that
simultaneously tackles scheduling (communication) and con-
trol. The architecture outputs two types of decisions, µ(t) =
(acom(t), actrl(t)), where acom(t) represents the channel al-
location (scheduling) and actrl(t) provides the control signals
for the actuators. This structure allows for joint optimization
by sharing critical information between the scheduling and
control branches.
The scheduling branch outputs channel allocation decisions
using a sigmoid activation function to produce acom(t) ∈
[0, 1](M +N )×L, which ensures that the channel assignment is
continuous, facilitating smooth learning. The control branch
outputs continuous control signals actrl(t) ∈ RN .
The novelty lies in the cascaded connection between the
two branches: the scheduling output is passed into the control
branch to inform control decisions based on the real-time
availability of communication resources. This ensures that the
control actions are fully aware of communication constraints,
leading to joint optimization of communication and control
policies. Without this cascading, control commands may fail to
consider the actual communication state, leading to inefficien-
cies or even failed actions. By feeding the scheduling decisions
into the control branch, GCA-DRL directly addresses the
challenge of correlated communication and control policies,
allowing both policies to align dynamically and enhance
overall system performance.
Furthermore, the actor network adopts layer normalization
(LN) across all fully connected layers to handle the challenge
of cross-domain variables. Cross-domain inputs, including
communication quality, control states, and estimation states,
often have differing scales. Let’s assume the output of the fully
connected layer is denoted by a vector z = (z1, . . . , zd) ∈ Rd.
We have the mean µz = 1d Pdi=1 zi and variance σ2z =
1
d
Pd
i=1(zi − µz)2 of the elements in z. Each element of z
is then normalized by
ˆzi = αi
zi − µzp
σ2z + ϵz + δi, ∀i ∈ {1, 2, . . . , d} (18)
where αi is a learnable scale parameter; δi is a learnable shift
parameter; ϵz is a small constant added for numerical stability.
LN ensures that each input to the network is normalized,
preventing certain variables from dominating the learning
process and enabling more effective training across domains.
This is essential for large-scale WNCSs, where maintaining
the balance between communication and control domains is
crucial for learning an effective policy.
2) Knowledge-assisted graph-based action embedding for
effective communications: To address the challenge of large
hybrid action spaces, GCA-DRL leverages max-weight bipar-
tite graph matching (MBGM) theory to transform the discrete
channel allocation decisions into a continuous representation
[51]. This helps reduce the complexity of the action space in
DRL training, enabling more efficient learning.
In MBGM, we model the devices (sensors and actuators)
and communication channels as two distinct sets of nodes in
a bipartite graph. The edges between these nodes are assigned
weights that represent the utility of assigning a particular
device to a particular channel. The goal of MBGM is to
find a one-to-one matching between devices and channels that
maximizes the total utility, which is calculated based on these
edge weights. This matching problem inherently incorporates
the constraint (4) and can be solved using a well-established

<!-- extraction_page_index: 10 -->

10
algorithm as described in [51].
To map the discrete channel allocation decisions D(t)
into continuous values, the actor network generates a weight
matrix acom(t) through the scheduling branch, which is passed
through a sigmoid activation function to ensure the values lie
between 0 and 1. These weights represent the likelihood or
importance of assigning a device to a channel.
By representing the channel allocation decisions as continu-
ous values, we reduce the burden of exploring a large discrete
action space during DRL training. Instead of the DRL agent
needing to evaluate a vast number of discrete possibilities, it
can explore continuous weight values incrementally, allowing
for smoother exploration and faster convergence. This method
avoids abrupt shifts in decision-making, which are common
when directly handling discrete actions, and instead enables
incremental adjustments during training.
A key innovation in GCA-DRL is the incorporation of
domain-specific knowledge into the MBGM process. Specif-
ically, the actor network adjusts the weights in MBGM us-
ing CSI to make the scheduling decisions adaptive to real-
time communication conditions. This is achieved by taking
the element-wise product of the output from the scheduling
branch and the CSI, i.e., acom(t) ⊙ G(t). By multiplying the
scheduling weights with CSI, the resulting weights become
context-aware, ensuring that devices are assigned to channels
with favorable conditions. For instance, if a channel has poor
quality (low CSI), its weight is reduced, lowering the chance of
selection. This helps the DRL agent prioritize better channels,
improving communication reliability. By focusing on channels
with good conditions, the action space is pruned, avoiding poor
performance options.
By using real-time CSI in the MBGM process, GCA-DRL
improves training efficiency and decision quality. It reduces the
exploration of irrelevant options, allowing the agent to focus
on more promising actions, making learning faster and more
effective by exploiting known CSI.
3) Training with partial policy gradients update for effec-
tive control: To address the challenge of floating control in-
puts—control signals generated for unscheduled actuators that
introduce noise during training—GCA-DRL employs a partial
policy gradient update mechanism. This mechanism focuses
solely on the effective control inputs, i.e., those associated with
scheduled actuators, thereby eliminating irrelevant signals and
improving the stability of the training process.
The effective control inputs are defined as ai,effctrl , which
filters the raw control inputs aictrl through the actuator schedul-
ing matrix Dic. This filtering removes control inputs for
unscheduled actuators, reducing irrelevant data that can disrupt
learning. The valid action set for the actor parameters update
is ˜aiv = (aicom, ai,effctrl ).
The actor parameters are then updated using the partial
gradient of the minimum critic output with respect to the
effective actions, ensuring that only valid actions are used in
the optimization process:
∇θLa(θ) = 1B
BX
i=1
∇˜aiv mink∈{1,2} Qk(si, ˜ai; φk)Gπi . (19)
Algorithm 1 GCA-DRL for communications-control codesign of a
CML WNCS
Input: Episode number E, maximum steps per episode T , discount
factor β, target smoothing factor τ, mini-batch size B, the
policy update frequency D1, the target update frequency D2,
the standard deviation of Gaussian noise, σa.
Output: Well-trained actor π∗a(·).
1: Initialize the actor πa(·) with random parameter θ and initialize
the target actor with the same random parameter ˆθ = θ. Initialize
each critic Qk(·) and each target critic ˆQk(·) with random
parameter φk and ˆφk, respectively.
2: for episode = 1,. . . ,E do
3: Initialize the plant state x(0) =0, the received control input
utx(0) =0, and randomly initialize the CSI, G(0).
4: for t = 0,. . . ,T do
5: For the current observation s(t), select action ˜a(t) =
πa(s(t); θ) +ϵ(t). Pass the action ˜a(t) to the action embedding
scheme to obtain the MDP action a(t).
6: Execute the MDP action a(t) into the CML WNCS
defined in (1) with the estimator defined in (8).
7: Observe the cost c(t) and the next observation s(t + 1).
8: Store the experience < s(t), ˜a(t), c(t), s(t + 1)> in the
replay buffer.
9: Sample a random mini-batch of B experiences <
si, ˜ai, ci, s
′
i >, ∀i ∈ {1, 2, . . . , B} from the replay buffer.
10: Set the value function target yi according to (16).
11: Update each critic parameter φk by minimizing the loss
function Lk(φk) in (17).
12: Every D1 steps, update the actor parameters θ by using
the policy gradient ∇θLa(θ) in (19).
13: Every D2 steps, update the target parameters using the
smoothing factor τ, i.e., ˆφk = τ φk + (1− τ ) ˆφk and ˆθ = τ θ+
(1 − τ )ˆθ.
14: end for
15: end for
By focusing on effective control inputs, GCA-DRL eliminates
the disruptive noise caused by floating control signals, leading
to more stable training and faster convergence. It ensures that
only valid control actions contribute to the policy updates. The
training algorithm of GCA-DRL is shown in Algorithm 1.
V. N UMERICAL SIMULATION
Our numerical experiments are implemented using MAT-
LAB 2024a based on the computing platform with Intel i7-
13700k CPU @ 3.40 GHz and 32 GB RAM. GPU is not
required. The details of the WNCS parameters and the GCA-
DRL parameters are summarized in Table I. The dynamic
system matrices A, B, and C are randomly generated by
leveraging the method presented in [52].
A. Benchmark Policies
1) Control policies: We present two benchmark control
algorithms of the linear quadratic regulator (LQR), which are
widely adopted in the existing literature [53].
Standard LQR controller is designed with perfect com-
munication to minimize the control cost (10). The generated
control input at t is given as
utx(t) ≜ Kstd ˆx(t) =−β B⊤Sstd∞ B+R−1B⊤Sstd∞ Aˆx(t),
where the matrix Sstd∞ can be computed recursively as follows:
Sstdk ≜ βA⊤Sstdk+ 1A+Q
−β2A⊤Sstdk+ 1B B⊤Sstdk+ 1B+R−1B⊤Sstdk+ 1A,

<!-- extraction_page_index: 11 -->

11
TABLE I
SUMMARY OF EXPERIMENTAL SETUP
Items Value
The WNCS parameters
System matrices, A, B, C Randomly generated
Eigenvalues of A matrix, ρk(A) ρk(A) ∈ (1.0, 1.1)
Noise covariance matrices, W, V Identity matrix
Penalty matrices in control cost, Q, R Identity matrix
Initial plant state, x(0) x(0) =0⊤
Plant saturation state |xi(t)| ≤100, i∈ K, ∀t >0
Transmit power budget [dBm], Pmax 23
Background noise power [dBm], σ2 −60
Code rate [bps], b/l 2
Block length [symbols], l 200
Channel states, G {10−10, 10−9, . . . ,10−1}
CSI transition matrix, {Msm,l}, {Mcn,l}, Randomly generated
Training parameters of GCA-DRL
Episode number, E 3000
Maximum time slots per episode, T 100
Hidden layer size 300, 200, 100
Learning rate of actor and critic 0.001
Optimizer during learning Adam
Threshold value of the learning gradient 1
Experience buffer length 100000
Target smoothing factor, τ 0.005
Mini-batch size, B 64
Discount factor, β 0.99
Policy and target update frequency, D1, D2 2
Standard deviation of actor action noise, σa
√
0.1
with initial value Sstd0 = Q.
Modified LQR controller is designed with imperfect com-
munication to minimize control cost (10). Let E ∈ [0, 1]N ×N
denote the diagonal matrix of control packet loss rates, where
[E]n,n ≜ ¯εcn, ∀n ∈ Nis the average control packet loss rate
of the actuator n. The generated control input at t is given as
utx(t) ≜ Kmod ˆx(t) =−β B⊤Smod∞ B+R−1B⊤Smod∞ Aˆx(t),
where Smod∞ can be computed recursively as follows:
Smodk ≜ βA⊤Smodk+ 1A+Q
−β2(I−E)A⊤Smodk+ 1B B⊤Smodk+ 1B+R−1B⊤Smodk+ 1A,
with initial value Smod0 = Q.
2) Scheduling policies: We present some benchmark
scheduling algorithms that are commonly used in WNCSs.
Round-robin policy guarantees that no device is starved of
channel access. All devices are numbered in a list. Channels
are assigned to consecutive L devices in the device list, shifting
by one device each time slot. After reaching the last device,
the allocation process wraps around to the start. Persistent
policy ensures that a device retains exclusive access to a
frequency channel until its communication is successfully
completed. Channels are initially assigned to L devices that are
randomly selected from all devices. Upon successful packet
delivery of the scheduled device, the channel is then randomly
reallocated to one of the unscheduled devices in the subsequent
time slots. Greedy policy on age of information (AoI)
ensures timely data updates [52]. AoI of a device is defined
as the time elapsed since the last successful reception of
the packet by that device. At each time slot, devices select
the remaining available channels based on their descend AoI
ranking, choosing the channel with the best channel condition,
until all channels are allocated. Greedy policy on CSI uses
the MBGM theory, where devices and channels are treated
as two distinct sets of nodes. The edges between them have
weights represented by the CSI between a particular device
to a particular channel. The policy is to find a one-to-one
matching that maximizes the total CSI at each time slot.
Random policy ensures that all devices have a statistically
equal chance of accessing any of the channels over time. At
each time slot, L out of M + N devices are randomly selected
and each selected device is randomly allocated to one of the
L frequency channels.
We also compare our GCA-DRL with some codesign meth-
ods using DRL in the existing literature, which have been
discussed in Section III-B.
B. Performance Evaluation
In Table II, we compare the control performance measured
by the average sum of one-step costs, i.e., the control cost,
among the proposed GCA-DRL algorithm and the benchmark
approaches, when K = M = N = L = 5 . There are 10
devices sharing 5 channels. Control costs in Table II are cal-
culated by averaging 100 episodes with 100 steps per episode.
Notably, the developed GCA-DRL method demonstrates a
significant advantage across all metrics compared to traditional
designs and codesign benchmarks. Specifically, GCA-DRL
achieves the lowest overall control cost of 858.65, which is a
significant improvement over all other approaches. Compared
to the best benchmark (1201.36), GCA-DRL reduces 28.5%
control cost. These results highlight the effectiveness of GCA-
DRL in simultaneously optimizing communication and control
policies, leading to better overall system performance as
measured by the control cost.
Fig. 4 presents the training performance of five different
codesign methods, including GCA-DRL, in terms of the
control cost J over 3000 training episodes. The GCA-DRL
method demonstrates a clear advantage in both convergence
speed and final performance. It not only converges faster but
also achieves a significantly lower steady-state control cost
compared to the other methods. By episode 500, GCA-DRL
already exhibits a stable downward trend, whereas methods
like dual-TD3 and the rounded-off method continue to show
fluctuations and higher costs throughout the training period.
The dual-TD3 method, in particular, shows the most variability
and fails to converge to a similarly low control cost, with per-
sistent oscillations around much higher values. The threshold-
based and priority-based methods initially show relatively
rapid convergence but plateau at higher control costs than
GCA-DRL. These results highlight the superiority of GCA-
DRL in terms of achieving both faster convergence and a
lower overall control cost. This is attributed to the adaptive
cascaded dual-branch actor architecture and the knowledge-
assisted graph action embedding, which enable more effective
codesign of communication and control policies.
Table III presents the comparison among the proposed
GCA-DRL algorithm and several benchmark approaches in
terms of the control cost across various system scales. The
system scales are represented by different combinations of
L, N, and M, which correspond to the number of wireless
channels, actuators, and sensors, respectively. The GCA-DRL

<!-- extraction_page_index: 12 -->

12
TABLE II
COMPARISON OF THE GCA-DRL AND BENCHMARKS IN THE CONTROL COST J WITH K = M = N = L = 5.
Design approach Scheduler Controller State estimationcost, E[Tr(QP(t))] Control cost,E[urx(t)⊤Rurx(t)] Estimated state cost,E[ˆx(t)⊤Qˆx(t)] Overallcost, J
Traditional design Random policy Modified LQR 108.33 1897136202 6173988263 8071124573
Traditional design Random policy Standard LQR 108.33 8157.11 43777.50 52042.96
Traditional design Random policy Vanilla TD3 108.41 58.61 2337.41 2504.43
Traditional design Round-robin policy Modified LQR 134.69 7451458.74 32602309.72 40053903.15
Traditional design Round-robin policy Standard LQR 134.69 16212.59 85268.12 101615.40
Traditional design Round-robin policy Vanilla TD3 138.04 81.81 2902.85 3122.71
Traditional design Persistent policy Modified LQR 99.41 16635697.50 43613727.11 60249524.02
Traditional design Persistent policy Standard LQR 99.41 3671.22 21092.08 24862.72
Traditional design Persistent policy Vanilla TD3 98.18 64.78 1961.32 2124.28
Traditional design CSI-based greedy policy Modified LQR 61.57 15003542.91 34940948.69 49944553.17
Traditional design CSI-based greedy policy Standard LQR 61.57 5723.14 27333.63 33118.35
Traditional design CSI-based greedy policy Vanilla TD3 61.26 49.36 1570.45 1681.06
Traditional design AoI-based greedy policy Modified LQR 60.77 33229.38 145388.50 178678.67
Traditional design AoI-based greedy policy Standard LQR 60.77 442.66 2016.48 2519.92
Traditional design AoI-based greedy policy Vanilla TD3 60.75 80.18 1060.44 1201.36
Traditional design TD3 (priority-based mapping) Standard LQR 76.15 171.13 1554.48 1801.76
Codesign TD3 (priority-based mapping) Modified LQR not converge not converge not converge not converge
Codesign TD3 (priority-based mapping) Vanilla TD3 67.23 52.31 1071.68 1203.14
Codesign Single TD3 (rounded-off mapping and control) 222.08 130.36 5598.62 5598.62
Codesign Single TD3 (threshold-based mapping and control) 116.73 58.77 1880.19 2055.68
Codesign Single TD3 (priority-based mapping and control) 66.99 58.02 1130.82 1255.82
Codesign GCA-DRL (This work) 52.21 46.34 760.10 858.65
TABLE III
COMPARISON OF THE GCA-DRL AND BENCHMARKS IN THE CONTROL COST J WITH DIFFERENT SYSTEM SCALES (L, N, M) AND K = N .
Design approach Scheduler Controller (4, 5, 6) (5 , 5, 5) (8 , 10, 12) (10, 10, 10) (12, 15, 18) (15, 15, 15) (20, 20, 20)
Traditional design AoI-based greedy policy Standard LQR 1867237 2519.92 64589.39 8975058 641046.04 27256173 2422586.57
Traditional design AoI-based greedy policy Vanilla TD3 9504.11 1201.36 3003.25 5479.01 5340.31 10083.39 36124.73
Traditional design TD3 (priority-based mapping) Standard LQR 26211.48 1801.76 2928.08 24025.68 19567.30 20406.11 114926.68
Codesign TD3 (priority-based mapping) Vanilla TD3 15898.98 1203.14 4604.62 25321.05 43510.40 31898.73 122493.84
Codesign Single TD3 (priority-based mapping and control) 9995.56 1255.82 3509.47 19077.32 55938.53 33965.72 96412.94
Codesign GCA-DRL (This work) 8973.17 858.65 2214.60 3418.03 5049.50 6239.07 26274.48
Fig. 4. Control cost of five codesign methods using DRL during training.
consistently achieves the lowest costs across all tested scales.
All methods using DRL in Table III employ LN in (18).
Without LN, we can only train DRL with 10 devices sharing
5 channels. However, after introducing LN, we can train
DRL with up to 40 devices sharing 20 channels. The results
highlight the scalability of the proposed GCA-DRL algorithm
that is effective for larger and more complex WNCSs.
VI. C ONCLUSIONS
We have addressed the key challenges of communication-
control codesign in large-scale WNCSs by developing a
practical model and an advanced DRL approach. Our model
captures real-world complexities, and by formulating the
problem as an MDP, we have jointly optimized scheduling
and control, effectively addressing their interdependencies.
The proposed GCA-DRL algorithm efficiently manages the
high-dimensional hybrid action space and improves training
with layer normalization and partial policy gradient updates.
Extensive simulations demonstrate that our approach signif-
icantly outperforms benchmark policies, proving its effec-
tiveness for optimizing communication-control codesign in
large-scale WNCSs. Future work will focus on extending
this approach to nonlinear control systems and exploring
the potential of distributed algorithm codesign rather than
relying on centralized algorithms. Additionally, we aim to
develop a more comprehensive framework for the codesign
of communications, control, and computing. Another direction
will involve investigating the most advanced integrated sensing
and communications framework in WNCSs to enhance overall
system performance.
REFERENCES
[1] J. Jin, K. Yu, J. Kua, N. Zhang, Z. Pang, and Q.-L. Han, “Cloud-
fog automation: Vision, enabling technologies, and future research
directions,” IEEE Trans. Ind. Inf. , vol. 20, no. 2, pp. 1039–1054, 2023.
[2] H. Lyu, J. Yan, J. Zhang, Z. Pang, G. Yang, and A. J. Isaksson,
“Cloud–fog automation: Heterogenous applications over new-generation
infrastructure of virtualized computing and converged networks,” IEEE
Ind. Elect. Mag. , 2024.
[3] K. Bhimavarapu, Z. Pang, O. Dobrijevic, and P. Wiatr, “Unobtrusive,
accurate, and live measurements of network latency and reliability for
time-critical internet of things,” IEEE Inter. Things Magazine , vol. 5,
no. 3, pp. 38–43, 2022.
[4] G. Zhao, M. A. Imran, Z. Pang, Z. Chen, and L. Li, “Toward real-time
control in future wireless networks: Communication-control co-design,”
IEEE Commun. Mag. , vol. 57, no. 2, pp. 138–144, 2019.

<!-- extraction_page_index: 13 -->

13
[5] K. Gatsis, M. Pajic, A. Ribeiro, and G. J. Pappas, “Opportunistic control
over shared wireless channels,” IEEE Trans. Autom. Control , vol. 60,
no. 12, pp. 3140–3155, 2015.
[6] S. Knorn and S. Dey, “Optimal energy allocation for linear control with
packet loss under energy harvesting constraints,” Automatica, vol. 77,
pp. 259–267, 2017.
[7] B. Chang, L. Zhang, L. Li, G. Zhao, and Z. Chen, “Optimizing resource
allocation in URLLC for real-time wireless control systems,” IEEE
Trans. Veh. Technol., vol. 68, no. 9, pp. 8916–8927, 2019.
[8] J. Lu and D. E. Quevedo, “A jointly optimal design of control and
scheduling in networked systems under denial-of-service attacks,” Au-
tomatica, vol. 148, p. 110774, 2023.
[9] A. S. Leong, D. E. Quevedo, T. Tanaka, S. Dey, and A. Ahl ´en, “Event-
based transmission scheduling and LQG control over a packet dropping
link,” IFAC-PapersOnLine, vol. 50, no. 1, pp. 8945–8950, 2017.
[10] Z. Ji, C. Chen, J. He, S. Zhu, and X. Guan, “Edge sensing and control co-
design for industrial cyber-physical systems: Observability guaranteed
method,” IEEE Trans. Cybern., vol. 52, no. 12, pp. 13 350–13 362, 2022.
[11] ——, “Learning-based edge sensing and control co-design for industrial
cyber–physical system,” IEEE Trans. Autom. Control, vol. 20, no. 1, pp.
59–73, 2023.
[12] V . Tzoumas, L. Carlone, G. J. Pappas, and A. Jadbabaie, “LQG control
and sensing co-design,” IEEE Trans. Autom. Control, vol. 66, no. 4, pp.
1468–1483, 2021.
[13] X. Wang, J. Zhang, C. Chen, J. He, Y . Ma, and X. Guan, “Trust-
AoI-aware codesign of scheduling and control for edge-enabled IIoT
systems,” IEEE Trans. Ind. Inf. , pp. 1–10, 2023.
[14] A. M. Girgis, J. Park, M. Bennis, and M. Debbah, “Predictive control
and communication co-design via two-way Gaussian process regression
and AoI-aware scheduling,” IEEE Trans. Comm. , vol. 69, no. 10, pp.
7077–7093, 2021.
[15] X. Wang, C. Chen, J. He, S. Zhu, and X. Guan, “AoI-aware control
and communication co-design for industrial IoT systems,” IEEE Internet
Things J., vol. 8, no. 10, pp. 8464–8473, 2021.
[16] Z. Ji, C. Chen, S. Zhu, Y . Ma, and X. Guan, “Intelligent edge sensing
and control co-design for industrial cyber-physical system,” IEEE Trans.
Signal Inf. Process. Over Netw. , vol. 9, pp. 175–189, 2023.
[17] H. Lv, Z. Pang, K. Bhimavarapu, and G. Yang, “Impacts of wireless on
robot control: the network hardware-in-the-loop simulation framework
and real-life comparisons,” IEEE Trans. Ind. Inf. , vol. 19, no. 9, pp.
9255–9265, 2022.
[18] H. Lyu, Z. Pang, A. Bengtsson, S. Nilsson, A. J. Isaksson, and G. Yang,
“Latency-aware control for wireless cloud-fog automation: Framework
and case study,” IEEE Trans. Autom. Sci. Eng. , 2024.
[19] B. Demirel, Z. Zou, P. Soldati, and M. Johansson, “Modular design of
jointly optimal controllers and forwarding policies for wireless control,”
IEEE Trans. Autom. Control , vol. 59, no. 12, pp. 3252–3265, 2014.
[20] J. Cao, X. Zhu, S. Sun, P. Popovski, S. Feng, and Y . Jiang, “Age of loop
for wireless networked control system in the finite blocklength regime:
Average, variance and outage probability,”IEEE Trans. Wirel. Commun.,
vol. 22, no. 8, pp. 5306–5320, 2023.
[21] G. Di Girolamo, A. D’Innocenzo, and M. D. Di Benedetto, “Co-design
of controller and routing redundancy over a wireless network,” IFAC-
PapersOnLine, vol. 48, no. 22, pp. 100–105, 2015.
[22] X. Lu, Q. Xu, X. Wang, M. Lin, C. Chen, Z. Shi, and X. Guan, “Full-
loop AoI-based joint design of control and deterministic transmission
for industrial CPS,” IEEE Trans. Ind. Inf. , vol. 19, no. 11, pp. 10 727–
10 738, 2023.
[23] M. Lin, Q. Xu, X. Lu, J. Zhang, and C. Chen, “Control and transmission
co-design for industrial CPS integrated with time-sensitive networking,”
in Proc. IEEE SMC , 2022, pp. 229–234.
[24] C. Chen, L. Lyu, S. Zhu, and X. Guan, “On-demand transmission for
edge-assisted remote control in industrial network systems,” IEEE Trans.
Ind. Inf., vol. 16, no. 7, pp. 4842–4854, 2020.
[25] S. Wildhagen and F. Allg ¨ower, “Scheduling and control over networks
using mpc with time-varying terminal ingredients,” in Proc. IEEE ACC,
2020, pp. 1913–1918.
[26] P. Li, Y .-B. Zhao, and Y . Kang, “Integrated channel-aware scheduling
and packet-based predictive control for wireless cloud control systems,”
IEEE Trans. Cybern. , vol. 52, no. 5, pp. 2735–2749, 2022.
[27] E. G. W. Peters, D. E. Quevedo, and M. Fu, “Controller and scheduler
codesign for feedback control over IEEE 802.15.4 networks,” IEEE
Trans. Control Syst. Technol., vol. 24, no. 6, pp. 2016–2030, 2016.
[28] M. K ¨ogel, D. Quevedo, and R. Findeisen, “Combined control and
communication scheduling for constrained system using robust output
feedback MPC,” in Proc. IEEE ECC , 2019, pp. 1778–1783.
[29] N. Yao, M. Malisoff, and F. Zhang, “Contention-resolving model pre-
dictive control for coupled control systems with a shared resource,”
Automatica, vol. 122, p. 109219, 2020.
[30] D. Cui and H. Li, “Co-design of sampling pattern and control in self-
triggered model predictive control for sampled-data systems,” IFAC-
PapersOnLine, vol. 53, no. 2, pp. 1795–1800, 2020.
[31] M. Bahraini, M. Zanon, A. Colombo, and P. Falcone, “Optimal schedul-
ing and control for constrained multi-agent networked control systems,”
Optim. Control Appl. Methods , vol. 43, no. 1, pp. 23–43, 2022.
[32] A. Redder, A. Ramaswamy, and D. E. Quevedo, “Deep reinforcement
learning for scheduling in large-scale networked control systems,” IFAC-
PapersOnLine, vol. 52, no. 20, pp. 333–338, 2019.
[33] D. Baumann, J.-J. Zhu, G. Martius, and S. Trimpe, “Deep reinforcement
learning for event-triggered control,” in Proc. IEEE CDC , 2018, pp.
943–950.
[34] N. Funk, D. Baumann, V . Berenz, and S. Trimpe, “Learning event-
triggered control from data through joint optimization,” IFAC J. Syst.
Control, vol. 16, p. 100144, 2021.
[35] L. Kesper, S. Trimpe, and D. Baumann, “Toward multi-agent reinforce-
ment learning for distributed event-triggered control,” in Proc. Mach.
Learn. Res., 2023, pp. 1072–1085.
[36] K. Shibata, T. Jimbo, and T. Matsubara, “Deep reinforcement learning of
event-triggered communication and control for multi-agent cooperative
transport,” in Proc. IEEE ICRA , 2021, pp. 8671–8677.
[37] ——, “Deep reinforcement learning of event-triggered communication
and consensus-based control for distributed cooperative transport,” Rob.
Autom. Syst., vol. 159, 2023, Art. no. 104307.
[38] H. Wan, H. R. Karimi, X. Luan, and F. Liu, “Model-free self-triggered
control based on deep reinforcement learning for unknown nonlinear
systems,” Int. J. Robust Nonlinear Control , vol. 33, no. 3, pp. 2238–
2250, 2023.
[39] H. Wan, H. R. Karimi, X. Luan, S. He, and F. Liu, “Integrated
learning self-triggered control for model-free continuous-time systems
with convergence guarantees,” Eng. Appl. Artif. Intell. , vol. 123, 2023,
Art. no. 106462.
[40] R. Wang and K. Kashima, “Deep reinforcement learning for continuous-
time self-triggered control with experimental evaluation,” Adv. Rob. ,
vol. 37, no. 16, pp. 1012–1024, 2023.
[41] A. Termehchi and M. Rasti, “A learning approach for joint design of
event-triggered control and power-efficient resource allocation,” IEEE
Trans. Veh. Technol., vol. 71, no. 6, pp. 6322–6334, 2022.
[42] Z. Zhao, W. Liu, D. E. Quevedo, Y . Li, and B. Vucetic, “Deep learning
for wireless networked systems: A joint estimation-control-scheduling
approach,” IEEE Internet Things J., vol. 11, no. 3, pp. 4535–4550, 2023.
[43] V . Lima, M. Eisen, K. Gatsis, and A. Ribeiro, “Model-free design of
control systems over wireless fading channels,” Signal Process. , vol.
197, p. 108540, 2022.
[44] J. Lei Ba, J. R. Kiros, and G. E. Hinton, “Layer normalization,” ArXiv
e-prints, pp. 1–14, 2016.
[45] Y . Wang, S. Wu, J. Jiao, N. Zhang, and Q. Zhang, “On the performance
of joint resource allocation and control in industrial IoT,” in Proc.
IEEE/CIC ICCC, 2023, pp. 1–6.
[46] P. Sadeghi, R. A. Kennedy, P. B. Rapajic, and R. Shams, “Finite-
state Markov modeling of fading channels - a survey of principles and
applications,” IEEE Signal Process. Mag. , vol. 25, no. 5, pp. 57–80,
2008.
[47] Y . He et al., “Deep-reinforcement-learning-based optimization for cache-
enabled opportunistic interference alignment wireless networks,” IEEE
Trans. Veh. Technol., vol. 66, no. 11, pp. 10 433–10 445, 2017.
[48] W. Liu, G. Nair, Y . Li, D. Nesic, B. Vucetic, and H. V . Poor, “On
the latency, rate, and reliability tradeoff in wireless networked control
systems for IIoT,” IEEE Internet Things J. , vol. 8, no. 2, pp. 723–733,
2021.
[49] G. Pang, W. Liu, Y . Li, and B. Vucetic, “DRL-based resource allocation
in remote state estimation,” IEEE Trans. Wirel. Commun., vol. 22, no. 7,
pp. 4434–4448, 2022.
[50] S. Fujimoto, H. Hoof, and D. Meger, “Addressing function approxima-
tion error in actor-critic methods,” in Proc. ICML, 2018, pp. 1587–1596.
[51] I. S. Duff and J. Koster, “On algorithms for permuting large entries to
the diagonal of a sparse matrix,” SIAM J. Matrix Anal. Appl. , vol. 22,
no. 4, pp. 973–996, 2001.
[52] A. S. Leong, A. Ramaswamy, D. E. Quevedo, H. Karl, and L. Shi, “Deep
reinforcement learning for wireless sensor scheduling in cyber-physical
systems,” Automatica, vol. 113, 2020, Art. no. 108759.
[53] L. Schenato, B. Sinopoli, M. Franceschetti, K. Poolla, and S. S. Sastry,
“Foundations of control and estimation over lossy networks,” Proc.
IEEE, vol. 95, no. 1, pp. 163–187, 2007.
