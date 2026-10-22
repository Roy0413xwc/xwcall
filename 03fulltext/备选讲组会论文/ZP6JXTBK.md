---
type: literature-fulltext
title: "Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-Driven DRL"
zotero_key: "ZP6JXTBK"
pdf_key: "3ZQIIP5J"
doi: "10.1109/TWC.2025.3589438"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-Driven DRL.md"
fulltext_path: "03fulltext/备选讲组会论文/ZP6JXTBK.md"
zotero_item: "zotero://select/library/items/ZP6JXTBK"
zotero_pdf: "zotero://open-pdf/library/items/3ZQIIP5J"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Energy-Efficient and Intelligent ISAC in V2X Networks With Spiking Neural Networks-Driven DRL

> PDF 原文逐页文本抽取；来源文件 SHA-256：`1fc6695068f7ac1a12d3c29b536038ab085e97a9d2948d7dfd7a52c2d8703a3e`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

1182 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Energy-Efﬁcient and Intelligent ISAC in V2X
Networks With Spiking Neural
Networks-Driven DRL
Chen Shang
 , Jiadong Yu
 , Member , IEEE, and Dinh Thai Hoang
 , Senior Member , IEEE
Abstract—Integrated sensing and communication (ISAC) is
emerging as a key enabler for vehicle-to-everything (V2X)
systems. However, designing efﬁcient beamforming schemes for
ISAC signals to achieve accurate sensing and enhance communi-
cation performance in the dynamic and uncertain environments
of V2X networks presents signiﬁcant challenges. While artiﬁcial
intelligence technologies offer promising solutions, the energy-
intensive nature of neural networks imposes substantial burdens
on communication infrastructures. To address these challenges,
this work proposes an energy-efﬁcient and intelligent ISAC
system for V2X networks. Speciﬁcally, we ﬁrst leverage a Markov
Decision Process framework to model the dynamic and uncertain
nature of V2X networks. This framework allows the roadside
unit to develop beamforming schemes relying solely on its
current sensing information, eliminating the need for numerous
pilot signals and extensive CSI acquisition. We then introduce
an advanced deep reinforcement learning (DRL) algorithm,
enabling the joint optimization of beamforming and power
allocation to guarantee both communication rate and sensing
accuracy in dynamic and uncertain V2X scenario. To alleviate the
energy demands of neural networks, we integrate spiking neural
networks (SNNs) into the DRL algorithm. The event-driven,
sparse spike-based processing of SNNs signiﬁcantly improves
energy efﬁciency while maintaining strong performance. Exten-
sive simulation results validate the effectiveness of the proposed
scheme with lower energy consumption, superior communication
performance, and improved sensing accuracy.
Index Terms —Integrated sensing and communication, V2X,
energy-efﬁcient, spiking neural network, deep reinforcement
learning.
I. I NTRODUCTION
T
HE rapid advancement of wireless communication
technologies has become the backbone of modern
autonomous vehicles and intelligent transportation systems,
driving unprecedented demands for performance and reliability
[1]. These systems rely on ultra-high data rates to enable
Received 1 January 2025; revised 18 April 2025; accepted 9 July 2025. Date
of publication 23 July 2025; date of current version 22 December 2025. This
work was supported by Guangdong Provincial Key Laboratory of Integrated
Communication, Sensing and Computation for Ubiquitous Internet of Things
under Grant 2023B1212010007. The associate editor coordinating the review
of this article and approving it for publication was L. Yang. (Corresponding
author: Jiadong Yu.)
Chen Shang and Jiadong Yu are with the Internet of Things Thrust,
The Hong Kong University of Science and Technology (Guangzhou),
Guangzhou, Guangdong 511458, China (e-mail: chenshang@hkust-gz.edu.cn;
jiadongyu@hkust-gz.edu.cn).
Dinh Thai Hoang is with the School of Electrical and Data Engineering,
University of Technology Sydney, Ultimo NSW 2007, Australia (e-mail:
hoang.dinh@uts.edu.au).
Digital Object Identiﬁer 10.1109/TWC.2025.3589438
bandwidth-intensive applications like high-deﬁnition mapping,
cooperative driving, and real-time video streaming. At the
same time, they require ultra-low latency for instantaneous
responses in safety-critical scenarios, such as collision avoid-
ance and emergency braking, alongside massive connectivity
to ensure seamless interaction among vehicles, roadside units
(RSUs), and cloud infrastructure, i.e., vehicle-to-everything
(V2X) networks. To meet these escalating demands, massive
multiple-input multiple-output (MIMO) and millimeter-wave
(mmWave) technologies have emerged as transformative solu-
tions [2]. Massive MIMO enhances spectral efﬁciency by
leveraging large antenna arrays to serve multiple users simul-
taneously via spatial multiplexing, making it ideal for dense,
dynamic V2X networks. Meanwhile, mmWave exploits abun-
dant spectrum in millimeter-wave bands to deliver unparalleled
data rates and capacity. Together, these technologies enable
ultra-fast communication rates and reliable performance,
establishing their indispensability in V2X networks [1], [2].
Despite their advantages, deploying these technologies to
enhance V2X networks faces signiﬁcant challenges. First, the
high data rates provided by MIMO heavily depend on beam
training, which involves a multi-step process to achieve precise
beam alignment. For example, the RSU initially transmits pilot
signals to the vehicle, which uses these signals to estimate
the channel state information (CSI) and feeds this information
back to the RSU. During this process, both the RSU and the
vehicle periodically transmit and receive pilot signals across
all potential beam directions to identify the beam pair that
maximizes path gain. Based on this feedback, the RSU dynam-
ically adjusts its beam direction to align with the vehicle’s
position and movement. While this iterative process ensures
optimal signal strength and coverage, it also requires substan-
tial pilot signals for channel estimation and beam alignment.
As a result, it signiﬁcantly increases resource consumption,
reduces spectral efﬁciency, and introduces overhead delays
that are especially critical in the fast-changing environments of
V2X networks [3]. To address this issue, endowing the V2X
system with sensing capabilities through radar deployment
has emerged as a potential solution to reduce beam training
overhead. However, conventional approaches that separately
utilize radar signals for sensing and communication signals
for data transmission further exacerbate spectral resource
inefﬁciency [1]. Therefore, these combined requirements for
robust communication and accurate sensing expose signiﬁcant
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

SHANG et al.: ENERGY-EFFICIENT AND INTELLIGENT ISAC IN V2X NETWORKS WITH SNNs-DRIVEN DRL 1183
limitations of conventional wireless technologies in meeting
the demands of modern V2X networks.
The paradigm shift from 5G to 6G networks intro-
duces transformative advancements in wireless communication
through integrated sensing and communication (ISAC) [4] and
artiﬁcial intelligence (AI) [5]. By utilizing sensing signal to
estimate vehicle’s state information, ISAC reduces reliance
on resource-intensive beam training, enhances beamforming
efﬁciency, and optimizes spectrum utilization [6]. Meanwhile,
AI-driven wireless communication introduces intelligent beam
management, dynamic resource allocation, and adaptive learn-
ing capabilities, enabling real-time adaptation to rapidly
changing V2X environments. Together, ISAC and AI synergize
to enhance beam alignment precision, strengthen communica-
tion robustness, and reduce resource overhead, paving the way
for reliable V2X connectivity, mobility, and security.
A. Related Work
Within ISAC-assisted V2X networks, the primary objective
is to develop efﬁcient beamforming strategies that enhance
sensing accuracy and subsequently optimize communication
performance, i.e., designing beamforming for sensing-assisted
communication. Currently, beamforming schemes can be real-
ized through optimization-based approaches [7], [8], [9], [10]
and AI-driven techniques [11], [12], [13], [14].
In [7], an Extended Kalman Filter (EKF) was employed to
track the motion of vehicles using sensing signals, facilitating
the update of beamforming parameters to ensure consistent
communication performance. A similar method was adopted
in [8], where the EKF was extended to track both vehicle and
unmanned aerial vehicle (UA V) kinematics. This enabled the
UA V to dynamically adjust beam widths and trajectories to
maintain robust sensing and communication in high-mobility
environments. Additionally, [9] introduced a predictive beam
tracking approach that integrated vehicle-sensed data with
sensing information to enhance trajectory prediction accuracy,
mitigate multi-user interference, and improve communication
consistency in nonlinear V2X scenarios. To address inter-
beam and inter-vehicle interference, [10] proposed a dynamic
power allocation strategy that optimized the trade-offs between
sensing and communication.
AI-driven beamforming schemes, on the other hand, lever-
age advanced learning algorithms to optimize beamforming
strategies. In [11], a hybrid neural network framework com-
bining convolutional neural networks (CNNs) and a long
short-term memory (LSTM) network was proposed to predict
the current beamforming matrix based on historical channel
data. This approach eliminated the need for explicit channel
tracking, signiﬁcantly reducing signaling overhead. Besides,
[12] developed three neural networks to independently handle
communication, sensing, and power allocation tasks, achieving
greater system efﬁciency. In addition, [13] utilized deep rein-
forcement learning (DRL) to jointly optimize beamforming
and power allocation in static V2X networks, offering a model-
free approach to complex optimization tasks. Furthermore,
[14] introduced a two-stage predictive beamforming frame-
work employing deep neural networks. The ﬁrst stage acquired
CSI, while the second stage optimized the beamforming matri-
ces to enhance communication performance.
Although the aforementioned methods have signiﬁcantly
enhanced the performance of ISAC systems, unresolved
challenges remain. First, conventional optimization-based
approaches [7], [8], [9] that rely on the EKF to predict vehicle
states and perform beamforming. However, these approaches
can encounter challenges in modeling nonlinear vehicle
dynamics accurately. For instance, the EKF relies on lin-
earization via ﬁrst-order Taylor expansion, which may lead to
approximation errors that accumulate over time, especially in
highly dynamic V2X scenarios. Although advanced techniques
such as the Unscented Kalman Filter (UKF) [15] provide
better handling of nonlinearities, they often assume known
and stationary process and measurement noise statistics. These
assumptions may not hold in practical ISAC-assisted V2X
environments, where sensor uncertainties and communication-
induced delays can be time-varying and difﬁcult to model
precisely.
On the other hand, AI-based schemes [11], [12], [13],
[14] utilized data-driven methods to estimate and predict CSI,
bypassing the need for explicit motion tracking and directly
enabling beamforming design. Although effective in some
cases, these methods face difﬁculties in highly dynamic V2X
environments, where rapid channel variations and interference
undermine CSI reliability.
A critical limitation of AI-driven algorithms are inherently
energy-intensive, posing substantial energy consumption chal-
lenges during training, inference, and model updates. This high
energy demand arises from the computational complexity of
forward and backward propagations in deep neural networks,
particularly in architectures with a large number of parameters
and layers [11], [12], [13], [14], [16]. During training, these
algorithms require iterative optimization over massive datasets,
signiﬁcantly increasing energy usage. For example, training a
large-scale neural network like GPT-3, which contains 175
billion parameters, consumed approximately 1,287 megawatt-
hours (MWh) of electricity-comparable to the energy usage
of 130 U.S. homes over a year [17]. The computational
burden is further ampliﬁed during the practical deployment
of these algorithms, which requires the RSU to continuously
perform real-time, sustainable processing in order to adapt
to ﬂuctuating channel conditions and dynamic vehicle states.
Moreover, maintaining model performance in non-stationary
environments necessitates frequent updates, imposing contin-
uous computational and energy demands. Notably, Google has
reported that 60% of its AI-related energy consumption from
2019 to 2021 was attributed to inference processes [17]. These
challenges collectively place substantial pressure on energy-
limited communication infrastructures, e.g., RSUs. The high
energy consumption associated with training, inference, and
model updates not only limits the scalability of AI-driven
methods but also threatens the feasibility of their deployment
in practical V2X scenarios.
B. Motivation and Contributions
Given the above challenges, this work aims to develop
an intelligent and energy-efﬁcient ISAC system for V2X
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

1184 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
networks. Speciﬁcally, we ﬁrst model the dynamics of V2X
networks using a Markov Decision Process (MDP) frame-
work. This framework allows the RSU to develop a one-step
beamforming scheme based solely on its current sensing data,
signiﬁcantly reducing beamforming overhead compared to
existing methods [7], [9], [11], [12], [14]. Meanwhile, it also
eliminates the need for explicit CSI and reduces reliance on
pilot signals, thereby enhancing the system’s practicality in
dynamic and uncertain scenario. To overcome the limitations
of conventional tracking-based methods such as EKF and
UKF, we introduce a model-free deep reinforcement learning
(DRL) algorithm. This algorithm enables the RSU to learn
adaptive control policies through interaction with the envi-
ronment, allowing it to effectively handle nonlinear vehicle
dynamics, stochastic noise, and partial observability. To further
improve communication performance and sensing accuracy in
dynamic V2X network, we jointly optimize the beamforming
and power allocation problems. This approach ensures that
the optimized policy can adaptively respond to time-varying
channel conditions and changing vehicle states, providing
considerable communication rates and sensing accuracy in
uncertain and dynamic V2X environments. In addition, we
introduce a novel neural network framework, spiking neural
networks (SNNs), and integrate it with the proposed DRL
algorithm. Leveraging their event-driven nature and asyn-
chronous processing capabilities, SNNs excel in managing
spatiotemporal patterns, enhancing real-time decision-making
while signiﬁcantly reducing energy consumption. These fea-
tures enable SNN-driven DRL algorithm well-suited for ISAC
tasks in energy-constrained automotive systems, meeting the
safety-critical and latency-sensitive demands of V2X applica-
tions. Our contributions are summarized as follows:
• We develop a novel stochastic optimization framework
that jointly optimizes beamforming and power allocation
schemes to maximize sum communication rates while
ensuring sensing accuracy in ISAC-assisted V2X net-
works. By reformulating this optimization problem as an
MDP, we then design a one-step beamforming scheme
from the RSU. This scheme executes beamforming based
solely on the RSU’s current sensing data for surrounding
vehicles, signiﬁcantly reducing beamforming overhead.
• We introduce a highly effective learning-based algorithm
that enables the RSU to quickly ﬁnd the optimal policy by
utilizing the capabilities of model-free DRL and the actor-
critic framework with a policy-clipping technique. This
learning-based approach eliminates the need for explicit
model linearization and assumptions about known system
noise statistics, as in [7], [8], and [9], by learning optimal
decision-making strategies directly from environmental
interaction data and observed states (i.e., sensing data),
enabling the RSU to make real-time and adaptive deci-
sions in the dynamic and uncertain V2X environments.
• To alleviate the energy consumption of learning-based
algorithms, we propose an advanced DRL algorithm
enhanced with energy-efﬁcient SNNs. By replacing
traditional neural networks with SNNs, the proposed
SNN-driven DRL algorithm signiﬁcantly reduces the
energy consumption of neural network operations. Fur-
Fig. 1. The AI-based ISAC-assisted V2X networks. By leveraging the discrete
spikes of SNNs for decision-making, the RSU signiﬁcantly reduces energy
consumption.
thermore, leveraging the unique spatiotemporal dynamics
of SNNs, the algorithm achieves enhanced performance
in both convergence speed and decision-making.
• We conduct comprehensive simulations to evaluate the
efﬁciency of the proposed method. The results show that
the SNN-driven DRL algorithm achieves energy savings
of 5.15 times during model training and 7.125 times
during inference compared to conventional approaches.
In addition, the proposed scheme exhibits superior per-
formance in terms of enhanced communication rates and
improved sensing accuracy.
The rest of this paper is organized as follows. Section II
introduces the system model and provides a detailed problem
formulation. Section III explains the MDP framework and the
one-step beamforming scheme. In Section IV, we propose the
intelligent and energy-efﬁcient learning algorithm. Sections V
and VI present comprehensive evaluations and the conclusion
of this work, respectively.
II. S YSTEM MODEL AND PROBLEM FORMULATION
As shown in Fig. 1, we consider an ISAC-assisted V2X
network consisting of an RSU controlled by AI algorithm
and multiple vehicles, where the vehicles are driving along a
straight, single-lane road parallel to the antenna array of RSU
and each vehicle represented byK ={1, 2,...,K }. The RSU
is equipped with massive MIMO uniform linear arrays (ULA)
antennas, comprising NTA transmission antennas and NRA
receive antennas, to transmit and receive ISAC signals contain-
ing both radar (i.e., sensing) and communication components
for the vehicles with single antenna. The operation processes
of this system are as follows: (1) The RSU sends the ISAC
signal through the narrow beam to these vehicles; (2) The echo
signals from sensing signals are reﬂected back to the RSU
by the vehicles; (3) The RSU estimates the vehicles’ posi-
tions and optimizes the beamforming based on the reﬂected
sensing signals; (4) The ISAC signals are transmitted using
the optimized beamforming schemes. Through this itera-
tive process, the RSU provides an efﬁcient beamforming
scheme, ensuring that the communication components of the
ISAC signals are effectively received by the vehicles, thereby
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

SHANG et al.: ENERGY-EFFICIENT AND INTELLIGENT ISAC IN V2X NETWORKS WITH SNNs-DRIVEN DRL 1185
achieving sensing-assisted communication. The speciﬁc sens-
ing and communication models are detailed below.
A. Sensing Model
Let xk,n (t) denote the downlink ISAC signal transmit-
ted to the vehicle- k at time instant t within the n-th time
slot, where n ∈ {1, 2,...,N }, and the ISAC signal vec-
tor for all K vehicles can be expressed as xn (t) =
[x1,n (t),x 2,n (t),...,x K,n (t)]T ∈ CK×1. Therefore, the
transmitted signal through the NTA transmission antennas at
the RSU can be expressed as:
˜xn (t) = Fnxn (t)∈ CNTA×1, (1)
where Fn = [f1,n, f2,n,..., fK,n] is the transmit beamforming
matrix with fk,n∈ CNTA×1 at n-th time slot. After a round-trip,
the reﬂected echo signal received at the RSU is given by:
yn (t) =E
K∑
k=1
√pk,nβk,nej2πµk,ntb (θk,n) aH (θk,n)
× ˜xn (t−τk,n) + z (t), (2)
whereE =√NTANRA andpk,n represent the array gain factor
for sensing signal and the transmit power of the RSU for
beam-k at time slot n, respectively. βk,n = κ/ (2dk,n) is
the reﬂection coefﬁcient of vehicle- k at time slot n, where
κ represents the fading coefﬁcient and dk,n is the distance
between vehicle-k and the RSU at time slot n. Besides, θk,n,
µk,n, and τk,n denote the angle between the vehicle- k and
the RSU, the doppler frequency, and the round-trip time-delay
of echo signal at time slot n, respectively. z (t) ∈ CNRA×1
denotes the complex additive white Gaussian noise with zero
mean and variance of σ2, i.e., z∼CN (0,σ 2). Furthermore,
a (θk,n) and b (θk,n) are transmit and receive steering vectors
of the antenna array of the RSU, respectively, which can be
expressed as follows:
a (θk,n)
=
√
1
NTA
[
1,e−jπ cosθk,n,...,e −jπ(NTA−1) cosθk,n
]T
, (3)
b (θk,n)
=
√
1
NRA
[
1,e−jπ cosθk,n,...,e −jπ(NRA−1) cosθk,n
]T
. (4)
Note that the reﬂected echo signal in (2) consists of multiple
sub-echoes originating from different vehicles, leading to
unavoidable inter-beam interference. To address this issue, we
introduce the following lemma based on the theory of massive
MIMO.
Lemma 1: The steering vectors corresponding to
different angles are asymptotically orthogonal, i.e.,⏐⏐bH (θk,n) b (θk′,n)⏐⏐≈ 0, ∀k⁄=k′.
Proof: Please refer to [7], [18].
Based on Lemma 1, the RSU can distinguish multiple vehi-
cles based on their angle-of-arrival (AoA), enabling effective
spatial separation and suppression of self-interference [19]. To
this end, a spatial ﬁltering operation [20] can be applied, and
the received echo signal at the RSU reﬂected by vehicle- k,
denoted as yk,n (t), can be extracted from (2) and expressed
as:
yk,n (t) = bH(ˆθk,n)yn (t)
=E√pk,nβk,nej2πµk,ntaH (θk,n) ˜xn (t−τk,n)
+ zk,n (t), (5)
where bH(ˆθk,n)yn (t) represents the spatial ﬁltering operation
based on the estimated angle ˆθk,n (ˆθk,n≈θk,n) of the receive
beamforming vector. zk,n(t) = bH(ˆθk,n)z(t) with zk,n (t)∼
CN
(
0,σ 2z) denotes the noise vector.
After extracting the received echo signal for vehicles, the
RSU is able to estimate their states, and subsequently update
the beamforming scheme based on these estimated states
information. Speciﬁcally, matched ﬁltering can be applied to
maximize the signal-to-noise ratio (SNR), thereby enhancing
the detectability of the echo signal [21]. This process can be
expressed as:
{˜τk,n, ˜µk,n}
= arg max
τk,n,µk,n
⏐⏐⏐⏐⏐∫ ∆Tm0 yk,n (t)x∗k,n (t−τ)e−j2πµtdt⏐⏐⏐⏐⏐2, (6)
where ˜µk,n and ˜τk,n denote the measured doppler frequency
and time-delay after matched-ﬁltering operation, ∆Tm is the
duration of the observation window used for sensing, and x∗
is the complex conjugate of x. As a result, the RSU is able
to estimate the states of vehicles based on these measurement
parameters. The mathematical representations of the measured
doppler frequency ˜µk,n, estimated distance ˆdk,n, time-delay
˜τk,n, and the velocity ˆvk,n of vehicles-k are given by:
˜τk,n = 2 ˆdk,nc + zτk,n, ˜µk,n = 2ˆvk,n cosθk,nfcc + zµk,n,
(7)
where zτk,n and zµk,n represent the measurement noise with
zero mean and variance of σ2τk,n and σ2µk,n at time slot
n, respectively, c and fc are the speed of light and the
carrier frequency. Speciﬁcally, σ2τk,n and σ2µk,n are inversely
proportional to the received signal-to-interference-plus-noise
ratio (SINR) of the received echo signal (5) [7], [20], which
can be expressed as:
SINRk,n = E2pk,n|βk,n|2|aH(θk,n)fk,n|2∑K
i⁄=kE2pi,n|βi,n|2|aH(θk,n)fi,n|2 +σ2z . (8)
As a result, the variance of noise terms zτk,n and zµk,n in (7)
can be calculated by [7], [20]:
σ2τk,n = α2τ
(∑K
i⁄=kE2pi,n|βi,n|2⏐⏐aH(θk,n)fi,n⏐⏐2 +σ2z)
E2pk,n|βk,n|2|aH(θk,n)fk,n|2 ,
(9)
σ2µk,n = α2µ
(∑K
i⁄=kE2pi,n|βi,n|2⏐⏐aH(θk,n)fi,n⏐⏐2 +σ2z)
E2pk,n|βk,n|2|aH(θk,n)fk,n|2 ,
(10)
where α2τ and α2µ are the constant related to system conﬁgu-
ration and the signal design.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

1186 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
It is worth noting that the RSU acts as a pure mono-static
radar when there are no vehicles in its coverage area. Once
a vehicle enters its coverage area, the RSU can estimate the
vehicle’s states and quickly perform beam alignment for data
transmission. The communication model is then presented in
the following.
B. Communication Model
The received communication signal for vehicle- k at time
slot n, denoted by Ck,n, can be expressed as:
Ck,n (t) = ¯E√pk,nαk,nej2πµ′k,ntaH (θk,n) K∑
k=1
fk,nxk,n (t)
+ zc (t) , (11)
where ¯E = √NTA denotes the array gain factor for com-
munication signal, αk,n =
√
α0 (dk,n/do)−ϱ represents the
path loss coefﬁcient, where α0 and ϱ denote the path loss at
reference distance d0 and the path loss exponent, respectively.
Additionally, zc (t) ∼ CN
(
0,σ 2c) denotes the noise term.
Note that the path loss coefﬁcient αk,n and doppler frequency
µ′k,n =vk,n cosθk,nfc/c in (11) differs from βk,n in (2) and
˜µk,n in (7), respectively, because the communication signal
only involves a one-way transmission, whereas the sensing
signal undergoes a round-trip propagation.
Therefore, given the beamforming scheme fk,n and the
allocated transmit power pk,n, the communication signal’s
SINR for vehicle- k, denoted by γk,n, is given by:
γk,n (fk,n,pk,n) =
¯E2pk,n⏐⏐αk,naH (θk,n) fk,n⏐⏐2
∑K
i⁄=k ¯E2pi,n|αk,naH (θk,n) fi,n|2 +σ2c,
(12)
and then the achievable transmit sum-rate of all the vehicles
in the ISAC-assisted vehicle network system can be expressed
as:
R =
K∑
k=1
Rk =
K∑
k=1
log2 (1 +γk,n (fk,n,pk,n)). (13)
It can be observed that the achievable sum-rate is highly
dependent on the beamforming and power allocation schemes.
Moreover, the efﬁcacy of beamforming can be enhanced by
accurate sensing, thereby enabling sensing-assisted commu-
nication. However, the RSU is unable to directly evaluate
its sensing performance, i.e., the mean square error (RMSE),
because the true state information of the vehicles is unknown.
To address this challenge, we introduce the Cram´er-Rao Lower
Bound (CRLB) [22] in the following subsection.
C. Cram ´er-Rao Lower Bound and Problem F ormulation
Let xk,n = [θk,n,dk,n,vk,n]T represent the states of the
vehicle-k at time slot n, its state evolution model can be
expressed as [7]:



θk,n =θk,n−1 +d−1k,n−1vn−1∆T sinθk,n−1 +ωθ,
dk,n =dk,n−1−vk,n−1∆T cosθk,n−1 +ωd,
vk,n =vk,n−1 +ωv,
(14)
where ∆T is the time duration of each time slot, which
differs from the sensing observation window ∆Tm deﬁned
in (6) ( ∆Tm ≪ ∆T ) [6], [23], ωθ, ωd, and ωv represent
the noise with zero mean and variances σ2θ, σ2d, and σ2v,
respectively. Note that the RSU is unable to directly collect the
vehicles’ states, i.e., the state evolution model of vihicles is
unknown to the RSU, therefore, it must measure and estimate
these parameters using the sensing signal, as illustrated in
Section II-A.
Let yk,n = [˜yk,n, ˜τk,n, ˜µk,n]T denote the measurement
model of the RSU, which maps the vehicle states xk,n to the
corresponding measurements. Speciﬁcally, ˜τk,n and ˜µk,n are
the measurement parameters derived from the signal ˜yk,n that
experienced a matched ﬁltering operation in (6). To this end,
we ﬁrst rewrite the right-hand term of (6) as:
˜yk,n
=
∫ ∆Tm
0
yk,n (t)x∗k,n (t− ˜τk,n)e−j2π˜µk,ntdt
=E√pk,nβk,naH (θk,n) fk,n
×
∫ ∆Tm
0
xk,n (t− ˜τk,n)x∗k,n (t− ˜τk,n)ej2π(µk,nt−˜µk,nt)dt
+
∫ ∆Tm
0
zk,n (t)x∗k,n (t− ˜τk,n)e−j2π˜µk,ntdt
=E√pk,nβk,nξaH (θk,n) fk,n + ˜zk,n, (15)
where ξ represents the matched-ﬁltering gain, and ˜zk,n ∼
CN
(
0,σ 2yk
)
is the noise with zero mean and σ2yk being the
variance. Then, the mapping function between yk,n and xk,n
is given by:
yk,n = g (xk,n) + uk,n, (16)
where g (·) is deﬁned by (7) and (15), uk,n =
[˜zk,n, zτk,n, zµk,n]T , and yk,n ∼ CN(g (xk,n), Q), where
Q = diag
([
σ2yk,σ 2τk,n,σ 2µk,n]) is the covariance matrix. As
a result, the RSU is able to estimate the states of vehicles
ˆxk,n =
[
ˆθk,n, ˆdk,n, ˆvk,n
]T
from the sensing signal.
As aforementioned, we introduce the CRLB to evaluate
the measurement accuracy due to the unknown real states of
vehicles. The CRLB provides the lower bound for the variance
of unbiased estimators in target estimation performance [24],
i.e., xk,n in this work. Speciﬁcally, the CRLB is deﬁned as the
inverse of the Fisher Information Matrix FIM (xk,n), which
can be expressed as [24]:
FIM (xk,n) = E
[∂2 lnp (yk,n|xk,n )
∂2xk,n
]
= E
[(∂g (xk,n)
∂xk,n
)H
Q−1
(∂g (xk,n)
∂xk,n
)]
,
(17)
where p (yk,n|xk,n ) is the conditional probability density
function (PDF) of yk,n given xk,n [22], [24]. Therefore, the
lower bound on the variance of an unbiased estimator, i.e., the
CRLB, can be expressed as:
E
[
(ˆxk,n− xk,n) (ˆxk,n− xk,n)H
]
≽ FIM−1 (xk,n). (18)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

SHANG et al.: ENERGY-EFFICIENT AND INTELLIGENT ISAC IN V2X NETWORKS WITH SNNs-DRIVEN DRL 1187
Note that the variance is equal to the RMSE due to we only
consider the unbiased estimator. Besides, we have:
∂g (xk,n)
∂xk,n
=


∂˜yk,n
∂θk,n 0 0
0 2c 0
0 0 2fc cosθc

∈ C(NRA+2)×(NRA+2). (19)
According to the CRLB theorem [22], [24], given the
estimated angle ˆθk,n and distance ˆdk,n, their RMSEs are
respectively bounded by:
E
[(
ˆθk,n−θk,n
)2]
> CRLBθ (θk,n, fk,n,pk,n) ≜ FIM−111,
(20)
E
[(
ˆdk,n−dk,n
)2]
> CRLBd (dk,n, fk,n,pk,n) ≜ FIM−122,
(21)
where FIM−1ij denotes the i-th row and the j-th column
element of FIM−1. Furthermore, given the beamforming
matrix fk,n and the allocated transmit power pk,n, the CRLB
of θk,n and dk,n can be respectively expressed as follows:
CRLBθ (θk,n, fk,n,pk,n) =
[
1
σ2yk
(∂˜yk,n
∂θk,n
)H ∂˜yk,n
∂θk,n
]−1
,
(22)
and
CRLBd (dk,n, fk,n,pk,n) =
[
1
σ2τk
(2
c
)2]−1
. (23)
Through introducing the CRLB, we are able to quantify the
lower bound of the variance that any unbiased estimator might
reach when estimating θk,n anddk,n. In other words, it allows
us to directly optimize the beamforming and power allocation
schemes without relying on the estimation accuracy (i.e., the
RMSE).
As illustrated above, this work aims to leverage the sensing
signal to reduce the complexity of beamforming training,
thereby assisting in optimizing the beamforming design, and
ultimately enhancing communication performance. The RSU’s
objective is to maximize the achievable sum-rate across all
vehicles while ensuring sensing performance through optimal
beamforming design and power allocation. Therefore, the
optimization problem can be formulated as follows:
P1:
max
{Fn, pn}Nn=1
E
[
1
N
N∑
n=1
K∑
k=1
log2 (1 +γk,n (fk,n,pk,n))
]
,
(24)
s.t. E
[
1
N
1
K
K∑
k=1
CRLBθ (θk,n, fk,n,pk,n)
]
⩽ϵθ,
(24a)
E
[
1
N
1
K
K∑
k=1
CRLBd (dk,n, fk,n,pk,n)
]
⩽ϵd,
(24b)
K∑
k=1
pk,n ⩽Pmax and pk,n > 0 ∀k, (24c)
where pn = [p1,n,p 2,n,...,p K,n]T ∈ CK×1 is the allocated
power vector, ϵθ and ϵd are the maximum tolerable CRLB
thresholds for reliable sensing, andPmax represents the RSU’s
maximum transmit power. Speciﬁcally, the optimization prob-
lem is designed to enable the RSU to maximize the expected
long-term achievable sum-rate, while simultaneously ensur-
ing that the expected sensing accuracy CRLBθ and CRLB d
remains within acceptable thresholds across all vehicles and
time slots.
Optimizing P1 presents signiﬁcant challenges due to the
highly dynamic and complex nature of the V2X environ-
ment, characterized by time-varying and unknown channels
between vehicles and RSUs, as well as real-time variations in
vehicle positions. These factors make the sum-rate dependent
on multiple variables, such as estimation accuracy, channel
conditions, power allocation, and interference management.
Moreover, the problem is inherently non-convex, further com-
plicating the derivation of optimal solutions. In this situation,
classical ﬁltering methods such as EKF and UKF rely on
ideal assumptions (e.g., known noise statistics, full observ-
ability) and are designed for state estimation rather than joint
optimization. They are unable to coordinate beamforming
and power allocation decisions across multiple vehicles or
adapt to long-term dynamics and partial observability. Sim-
ilarly, codebook-based beamforming schemes are typically
static and optimized for single-user communication scenarios.
As such, they are limited in their ability to accommodate
joint communication and sensing constraints, lack support for
coordinated beamforming across multiple vehicles, and are
generally ineffective in highly dynamic environments due to
their limited adaptability.
To effectively tackle these challenges, we reformulate the
dynamic environment as an MDP and introduce an advanced
model-free DRL algorithm in the next section. This innovative
approach empowers the system to make efﬁcient, data-driven
decisions and adapt dynamically in real-time, ensuring opti-
mal performance even in complex and rapidly changing
environments.
III. P ROPOSED BEAMFORMING SCHEME AND PROBLEM
TRANSFORMATION BASED ON MDP F RAMEWORK
As discussed in Section II-C, the operating environment
for ISAC-assisted V2X networks is inherently unpredictable
and dynamic, posing signiﬁcant challenges for conventional
optimization algorithms. DRL algorithms have emerged as
a powerful solution [25], [26], [27]. By continuously inter-
acting with and adapting to these complex environments,
DRL algorithms effectively manage uncertainty and enhance
decision-making through their integration of randomness and
exploration strategies. Moreover, the proﬁciency of DRL in
capturing and representing complex nonlinear relationships
makes it indispensable for these settings. Speciﬁcally, model-
free DRL algorithms excel by learning optimal strategies
directly via interacting with the surrounding environment,
avoiding the need for a predeﬁned model. This capacity allows
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

1188 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
them to adaptively reﬁne their policies in real-time, providing
a signiﬁcant advantage in managing the intricacies of V2X
networks where dynamics are signiﬁcant complex to model
explicitly. Therefore, we develop a DRL algorithm to address
the challenges of beamforming design and power allocation
presented in the ISAC-assisted vehicle network environment.
To this end, we ﬁrst model the dynamics of the vehicle network
using an MDP framework in Section III-A. We then illustrate
the proposed beamforming scheme based on the MDP frame-
work in Section III-B. Furthermore, we reformulate the P1
into a stochastic optimization problem that can be solved by
the DRL in Section III-C.
A. MDP Framework for the ISAC-Assisted V2X Network
As discussed above, directly optimizing the considered
ISAC-assisted V2X network is challenging due to its high
dynamics and uncertainty. Therefore, we ﬁrst transform it
into an MDP framework, which provides a mathematical
foundation for sequential decision-making under uncertainty.
This framework allows the RSU to adaptively optimize its
beamforming and power allocation schemes as the network
environment evolves.
Let a tuple (S,A,P,r,G ) represent the MDP, whereS and
A are the state and action spaces, respectively, P denotes
the state transition probability distribution, r and G∈ (0, 1)
are the reward function and the discount factor of long-term
reward, respectively. The corresponding elements in MDP are
detailed as follows:
1) State Space: At each time slot n, the state space of the
ISAC-assisted vehicle network is deﬁned by:
S =
{{
ˆθk,n, ˆdk,n, ˆvk,n, ˆγk,n
}
; 1 ⩽k ⩽K
}
. (25)
Note that all variables in the state space are subject to
estimation errors due to the gap between sensing performance
and the actual parameters. In other words, sensing perfor-
mance plays a crucial role in accurately modeling the real
state space and signiﬁcantly affects the MDP framework and
subsequent optimization processes. For instance, the agent
(i.e., the RSU) may not be able to take appropriate actions
if there is a signiﬁcant discrepancy between its estimated
state space and the actual state information. This mismatch
signiﬁcantly hinders the RSU’s ability to retrieve accurate state
information and make optimal decisions, leading to potential
degradation in overall system performance. Additionally, the
continuous nature of the state space further exacerbates this
issue. Fortunately, our proposed advanced DRL algorithm does
not rely on perfect estimation performance and is capable
of tolerating estimation errors. It enables the RSU to obtain
optimal solutions and maintain considerable communication
rates even under imperfect estimations, which is detailed in
Section IV-A.
2) Action Space and Reward Function: At each time slot
n, the RSU designs the beamforming scheme and allocates
transmission power to each vehicle based on its current
observed state space. The action space of the RSU can be
deﬁned as follows:
A ={Fn,pn}. (26)
After taking action an from the action space A at time slot
n, the RSU receives an immediate reward rn(an,sn). Based
on this reward, the RSU can determine and optimize its subse-
quent actions in the following steps. Therefore, the objective
of the RSU is to maximize its long-term reward. As illustrated
in (24), this work aims to maximize the communication rates
while ensuring sensing performance. Consequently, the reward
function, which guides the RSU to improve communication
and sensing performance over all time steps (i.e., long-term
reward), is deﬁned as:
rn (an,sn) = 1(RJ− CRLBθ− CRLBd), (27)
where 1 (·) is an indicator function that equals 1 when
(24a)-(24c) are satisﬁed, and 0 otherwise. R represents the
achievable sum-rate deﬁned in (13), and J is the Jain’s
fairness index [28], which evaluates whether the achievable
rates for all vehicles are distributed equitably and is expressed
as
J (R1,R 2,...,R K) =
2
(∑K
k=1Rk
)2
K×∑Kk=1R2k. (28)
This reward function encourages the RSU to optimize beam-
forming and power allocation schemes efﬁciently, maximizing
achievable rates while ensuring fairness in each vehicle’s
communication rate. Besides, it enables the exploration of
optimal sensing performance, achieving a balance between
communication and sensing objectives.
B. Proposed Beamforming Scheme
Based on the MDP framework, we can design an efﬁcient
beamforming scheme. To this end, we ﬁrst introduce the state-
of-the-art beamforming schemes. We then highlight the key
differences and innovations of our proposed approach.
1) Traditional Beam Training: This scheme involves
transmitting downlink pilot signals in multiple directions,
measuring signal quality at the receiver, and using uplink
feedback to select the beamforming direction. Obviously,
frequent updates of downlink pilot signals and uplink feedback
introduce signiﬁcant overhead and degrade communication
quality [2].
2) Two-Stage Beam Prediction Protocol: This protocol
integrates radar sensing with communication (i.e., sensing-
assisted beamforming), enabling direct adaptation to environ-
mental data without the need for traditional beam training.
However, while it eliminates traditional beam training, this
approach still requires a disjoint two-stage process, i.e., sens-
ing and CSI prediction, followed by beamforming, leading to
signiﬁcant computational overhead [7], [14], [29].
3) Historical Channels-Based Beamforming Protocol: This
protocol leverages a learning-based method to design beams,
relying heavily on historical channel data [11]. Similarly, the
continuous update of historical channel data poses signiﬁcant
challenges for the RSU.
We compare these schemes with our proposed beamforming
scheme in Fig. 2. Speciﬁcally, the ISAC block integrates
both communication (i.e., data transmission) and sensing
operations (i.e., state information estimation). Unlike these
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

SHANG et al.: ENERGY-EFFICIENT AND INTELLIGENT ISAC IN V2X NETWORKS WITH SNNs-DRIVEN DRL 1189
Fig. 2. The comparison of different beamforming methods: (a) Traditional
beam training, (b) two-stage beam prediction protocol, (c) historical channels-
based beamforming protocol, and (d) proposed beamforming scheme. ISAC
block includes both data transmission and sensing operations.
state-of-the-art beamforming schemes above, our proposed
beamforming policy is efﬁcient for the following reasons.
First, we leverage the sensing signal to assist beamforming,
which drastically decreases overhead compared to Tradi-
tional beam training . Additionally, our scheme operates in
a single stage, eliminating the need for multiple stages to
ﬁrst acquire state information, deduce explicit CSI, and then
perform beamforming, as required in the Two-stage beam
prediction protocol . Furthermore, compared to the Histori-
cal channels-based beamforming protocol , our MDP-based
framework eliminates the need for continuous updates of CSI,
reducing complexity and resource consumption. As a result, as
shown in Fig. 2, our proposed beamforming scheme is faster,
more resource-efﬁcient, and better suited for dynamic V2X
environments than existing methods.
C. Problem Reformulation
Leveraging the MDP framework, we reformulate the origi-
nal optimization problem in P1 into a stochastic optimization
problem as follow.
Let π denote a stochastic policy of the RSU (i.e., π :S×
A→ [0, 1]), which is the probability that taking action an
given the state sn, i.e., π = P{an|sn}. Given the discount
of long-term reward G, the expected discounted reward of the
RSU follows policy π is given by:
J (π) = Ean∼π,sn∼P
[∞∑
n=0
Gnrn (sn,an)
]
, (29)
whereP (sn+1|sn,an ) is the state transition probability dis-
tribution that models the dynamics of the environment and is
unknown to the RSU. Therefore, the optimization problem in
P1 can be transformed into ﬁnding the optimal policy π∗ that
maximizes J(π), expressed as:
P2: arg max
π
J(π) (30)
s.t. an∼π(an|sn),sn+1∼P (sn+1|sn,an). (30a)
By transforming P1 into P2, we can apply DRL algorithms
to solve the original optimization problem. However, deploy-
ing conventional DRL algorithms, such as DQN [30] and
DDQN [31], presents signiﬁcant challenges in our scenario.
First, traditional DRL algorithms are designed for discrete
action spaces and struggle with continuous, dynamic environ-
ments like V2X networks. On the other hand, these algorithms
Fig. 3. The illustration of the training process for the proposed SNNs-driven
Actor-Critic PPO algorithm. The discrete spikes enable this framework to be
energy-efﬁcient by dramatically reducing computational complexity.
require substantial computational resources and energy due to
the complexity and frequency of neural network operations.
This high computational demand increases energy consump-
tion, raises operational costs, and slows system response
times, thereby limiting scalability and practicality in real-world
deployment scenarios [32].
Consequently, there is an urgent need to design an advanced
and energy-efﬁcient DRL algorithm to address these chal-
lenges. To this end, we propose an enhanced actor-critic DRL
algorithm driven by energy-efﬁcient SNNs in the following
section. This innovative approach not only excels at solving
complex tasks efﬁciently but also signiﬁcantly reduces energy
consumption, achieving the dual objectives of optimizing
algorithm performance and enhancing energy efﬁciency.
IV. P ROPOSED LEARNING ALGORITHM
In this section, we ﬁrst introduce a model-free and actor-
critic DRL algorithm tailored for the dynamic and uncertain
environments of V2X networks. We then integrate energy-
efﬁcient SNNs with DRL to develop a novel and advanced
DRL algorithm to optimize system performance.
A. Model-Free DRL Based on Actor-Critic Framework
As aforementioned, conventional DRL algorithms struggle
to derive the efﬁcient policy π∗ in the dynamic V2X environ-
ment. To address these challenges, we develop an advanced
model-free, actor-critic DRL algorithm. Speciﬁcally, model-
free DRL is a dynamic programming technique designed to
solve decision-making problems by learning an optimized
policy in dynamic environments [33]. This approach is par-
ticularly well-suited for ISAC-assisted V2I networks as it
enhances adaptability to dynamic environments, enables the
RSU to make efﬁcient real-time decisions, and effectively han-
dles high-dimensional data. Additionally, by employing two
neural networks (i.e., the actor network and critic network),
the actor-critic framework allows DRL algorithm to balance
bias and variance of training parameters, improve sample
efﬁciency, and ensure stable convergence [33].
As shown in the top of Fig. 3, our proposed learning algo-
rithm employs two specialized neural networks to optimize the
RSU’s operations, i.e., an actor network and a critic network.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

1190 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
The actor network utilizes a parameter vector, denoted as ψ
(comprising weights and biases), to generate the policy that
guides the RSU’s beamforming and power allocation strate-
gies. Concurrently, the critic network, denoted as Ω, evaluates
the performance of the implemented policy by estimating the
state-value function. This feedback guides the optimization
of ψ, enhancing decision-making accuracy and efﬁciency.
Therefore, the optimal policy in (30) can be approximated as
π∗←πψ with πψ (an|sn ) = P{an|sn;ψ}. Since we focus
on the behavior-decision for each action, the time slot index
n can be omitted in the following. Note that different from
other actor-critc based DRL algorithms [25], [26], [34], [35],
the two networks are driven by SNNs rather than conventional
neural networks, which are detailed in the Section IV-B.
After obtaining the outputs of the two networks, an advantage
function ˆA (·) is introduced to evaluate the current policy and
guide the policy update of the neural network. Speciﬁcally, the
advantage function measures whether the action taken is better
than the policy’s default behavior, which is deﬁned as [36]:
ˆA (s,a ;ψ) =Q (s,a ;ψ)−V (s; Ω), (31)
where Q (s,a ;ψ) =Ea∼πψ,s∼P
[∑∞
l=0Glr (sl,al)] is the
action-value function, V (s; Ω) = Es∼P
[∑∞
l=0Glr (sl,al)]
denotes the state-value function, and l is the constant related
to time step. Once the value of the advantage function is
obtained, the training objective function of actor network can
be expressed as [26]:
J (ψ) = min
( πψ (a|s)
πψold (a|s)
ˆA,φ
(
ϵ, ˆA
))
, (32)
where πψold denotes the vector of policy parameters before
the update. In particular,φ(ϵ, ˆA) represents the policy-clipping
technique, which constrains the policy update ratio within a
predeﬁned range, ensuring stable gradient updates. By prevent-
ing excessively large policy changes, this method stabilizes the
training process and enhances the algorithm’s performance,
which is deﬁned as:
φ
(
ϵ, ˆA
)
=
{
(1 +ϵ) ˆA, if ˆA > 0,
(1−ϵ) ˆA, if ˆA< 0. (33)
B. Enhanced-DRL Through Spiking Neural Network
As aforementioned, the complexity and frequent compu-
tations of conventional neural networks impose signiﬁcant
energy demands on the RSU. To address these challenges,
we propose an enhanced DRL algorithm driven by SNNs.
Unlike traditional neural networks, which propagate infor-
mation using continuous activation values and typically rely
on multiply-and-accumulate (MAC) operations [37], SNNs
transmit information using discrete spikes of electrical activity.
In other words, computation in SNNs is event-driven, meaning
neurons perform computations only when spikes occur (repre-
sented as binary events, i.e., 0 or 1). This event-driven nature
allows SNNs to perform training and inference operations
(e.g., forward and back-propagation) utilizing simple accu-
mulation (AC) instead of MAC operations, thus signiﬁcantly
reducing computational complexity and energy consumption
[25], [38], [39]. As a result, the SNN-driven DRL framework
enables RSUs to make decisions with reduced energy con-
sumption due to the discrete, spike-based processing. On the
other hand, the temporal nature of spikes allows the RSU to
efﬁciently capture temporal dependencies, thereby improving
the training and inference efﬁciency of the algorithm. The
details of the SNN architecture are as follows.
1) The Framework of SNNs: We utilize the Leaky-
Integrate-and-Fire (LIF) mechanism [40] to model spiking
neurons. In the LIF-based SNNs framework, spiking neuron- j
maintains a time-dependent membrane potential, represented
asUj(˜t). Note that the ˜t is the time step of SNN with ˜t≪n.
The membrane potential evolves over time through two key
processes: the integration of incoming inputs, referred to as
charge, and the gradual decay of the accumulated charge,
referred to as Leaky, which mimics the behavior of biological
neurons [40]. The update of membrane potentialUj(˜t) is given
by:
Uj(˜t + 1) = (1−λ)Uj(˜t) +λ
M∑
i=1
Wi,jIi
(˜t), (34)
where λ is the membrane leakage coefﬁcient that denotes
the rate of charge decay over time, M is the set of neu-
rons connected to neuron j, Wi,j and Ii
(˜t) represent the
synaptic weight and input potential from presynaptic neurons,
respectively. Once the membrane potential Uj
(˜t) exceeds a
ﬁring threshold Uth, the neuron releases a spike, represented
as Ψj. Simultaneously, the membrae potential is reset to
Ur(˜t)(Ur(˜t)<Uth). This dynamic ﬁring mechanism can be
expressed as:{
Ψj = 1 and Uj(˜t + 1) =Ur(˜t) ifUj(˜t)≥U th
Ψj = 0 and Uj(˜t + 1) =Uj(˜t) otherwise . (35)
The details of the LIF neurons in the SNN are illustrated at
the bottom of Fig. 3. In particular, the input is directly encoded
and fed into the SNN. This approach preserves ﬁne-grained
input information and simpliﬁes preprocessing [41]. The LIF
neurons then integrate these inputs over time, enabling the net-
work to capture temporal dependencies through their intrinsic
membrane dynamics. When the membrane potential exceeds
the ﬁring threshold Uth, the neuron generates discrete spike
outputs (0 or 1), which are transmitted to connected neurons
in subsequent layers through synaptic weights W. Speciﬁcally,
we remove the membrane potential threshold in the last layer
of the SNN. This adjustment allows the last layer to maintain
and propagate continuous membrane potentials, enabling the
network to generate actions and V tailored to our continuous
action space environment, while retaining the spiking behavior
in the earlier layers.
2) Training of Enhanced-DRL Algorithm: Neural networks
improve their accuracy by iteratively reﬁning their inter-
nal parameters, e.g., weights and biases. This reﬁnement
process relies on the differentiability of the network’s loss
function, which is essential for effective training through back-
propagation. In particular, the back-propagation process of
SNN-driven DRL can be expressed as:
∂J
∂Wi,j
=
˜T∑
˜t=1
∂J
∂Uj
(˜t)∂Uj
(˜t)
∂Wi,j
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

SHANG et al.: ENERGY-EFFICIENT AND INTELLIGENT ISAC IN V2X NETWORKS WITH SNNs-DRIVEN DRL 1191
=
˜T−1∑
˜t=1
∂J
∂Uj
(˜t)∂Uj
(˜t)
∂Wi,j
+ ∂J
∂Uj( ˜T )
∂Uj( ˜T )
∂Wi,j
=
˜T−1∑
˜t=1
(
∂J
∂Ψj
(˜t)∂Ψj
(˜t)
∂Uj(˜t) + ∂J∂Uj(˜t + 1)∂Uj(˜t + 1)∂Uj(˜t)
)
× ∂Uj(˜t)∂Wi,j + ∂J∂Ψj( ˜T )∂Ψj( ˜T )∂Uj(˜t) ∂Uj(˜t)∂Wi,j , (36)
where ˜T denotes the total number of time steps in the SNNs.
Speciﬁcally, due to the temporal dependencies inherent in
SNNs, it is crucial to compute gradients across time steps
(i.e., ˜T ) to capture the dynamics of spiking activity over
time, thereby enabling effective learning in time-dependent
environments.
It can be found that (36) contains ∂J∂Ψj(˜t) and ∂Ψj(˜t)∂Uj(˜t) . In
particular, the derivative of Ψj is impulse function (i.e., Dirac
Delta function [42]), which is given by:
Ψ′ (x) =
{
+∞,x = 0
0, x⁄= 0. (37)
As observed, this function is non-differentiable, which pre-
vents the neural network from being trained normally. To
address this issue, we introduce an approximate derivative
function as follows [38], [43]:
ϕ (Ψ) = 1π arc tan(πη2 Ψ) + 12, (38)
where ϕ (Ψ) denotes the approximate derivative function that
used to approximate the spike output function Ψ (U−U th)
deﬁned in (35). This approximation ensures that ϕ (U−U th)
is well-deﬁned and has a very close value as Ψ (U−U th) even
when Ψ = 0. Besides, η >0 is the custom parameter. Then,
the derivative of ϕ (Ψ) is given by:
ϕ′ (Ψ) = η2× 11 +(πη2 Ψ)2. (39)
It can be observed that (38) and (39) enable SNNs to obtain
meaningful gradients while executing the gradient descent
algorithm during back-propagation processes. Therefore, Ψ
can be approximated as lim
x→0
Ψ(x)≈ lim
x→0
ϕ(x). Consequently,
the non-differentiable terms ∂J∂Ψj(˜t) and ∂Ψj(˜t)∂Uj(˜t) in (36) can
be replaced with the approximate derivative function ϕ (·),
enabling SNNs to be trained effectively. Note that the approx-
imate derivative function is only used for back-propagation
progress, the forward propagation still follows (34) and (35).
Building on above foundation, we are able to develop
an enhanced DRL algorithm that integrates the advanced
actor-critic framework with energy-efﬁcient and temporal-
dependency SNNs. The details of the training process for the
proposed algorithm are illustrated in Fig. 3 and Algorithm 1.
Speciﬁcally, the parameters of the SNNs are ﬁrst initialized
randomly (lines 2-4 in Algorithm 1). At each training iteration
i, the algorithm collects a set of trajectories Bi by running
the current policy ψ in the considered environment (line
6). After obtaining the cumulative reward ˆRn and advantage
function (lines 7-8), the training objective function and the
critic network’s loss, C(Ω), are calculated using (31) and:
C(Ω) =
(
Vn(sn; Ω)− ˆRn
)2
, (40)
respectively (lines 9-10). With all the obtained objectives and
loss functions, the gradients of the actor network, denoted as
∇J(ψ), and then the gradients of critic network, denoted as
∇C(Ω), are computed (lines 10-13). Finally, the networks’
parameters are iteratively updated with learning rate αa and
αc (lines 14-15), respectively, until the cumulative reward
converges to a stationary value.
Algorithm 1 Proposed Learning Algorithm
V. P ERFORMANCE EVALUATIONS
A. Simulation Settings
1) V2X Network : We consider a scenario with three vehicles
(i.e., K = 3 ), each equipped with a single antenna, driving
along a straight road. The vehicles enter the coverage area of
an RSU withNTA =NRA = 32 antennas, operating at a carrier
frequency fc = 30 GHz [7]. Without loss of generality, the
coordinate of the RSU is set as (0, 0) and the initial positions of
the vehicles are (-5, 10), (-15, 10), and (-25, 10), respectively.
For the state evolution model of the vehicles, we consider that
their average velocities follow v∼ Unif(10 m/s, 14 m/s), i.e.
approximately 36-50.4 km/h. The evolution noise parameters
are set as σθ = 0.02◦, σd = 0.2 m, and σv = 0.5 m/s [29].
The time duration is ∆T = 0.02 s, and the total driving time
instant for the vehicles is N = 100 . Additionally, the κ =
10 + 10j and ξ = 10 [7]. The noise power for both sensing
and communication signals is σ2z =σ2c =−80 dBm. For the
measurement noise parameters, we set ατ = 1× 10−9 and
αµ = 2× 103 [29].
2) Algorithm Parameter Setups : We utilize a three-layer
fully connected neural network to implement the DRL frame-
work, consisting of an input layer, a hidden layer, and an
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

1192 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 4. (a) Comparison of the rewards in training process, (b) Comparison of energy consumption in training process, and (c) Comparison of energy
consumption in inference process.
output layer. This shallow network architecture offers suf-
ﬁcient representational capacity for beamforming task while
enabling lower energy consumption. The number of neurons
in the input and output layers corresponds to the dimensions
of the state and action spaces, respectively, while the hidden
layer contains 128 neurons. The batch size and discount factor
are set to {512, 0.99}. Besides, the policy-clipping factor is
conﬁgured with ϵ = 0.2 [25], [26]. Moreover, the learning
rates for the actor and critic networks are set to 5× 10−5 and
5× 10−4, respectively. For the SNNs, we set the parameters
of the LIF-based neurons as ˜T = 6, η = 3,Uth = 1,Ur = 0,
and λ = 12 [43].
3) Baselines : We conduct performance comparisons
between our proposed method, denoted as Spiking Actor-
Critic (Spiking-AC), and several state-of-the-art algorithms,
including the following: Proximal Policy Optimization (PPO)
[26], Deep Deterministic Policy Gradient (DDPG) [44], DQN
[30], and Random scheme.
B. Simulation Results
1) Convergence Performance and Energy Consumption:
We ﬁrst illustrate the convergence performance of the proposed
algorithm and the baselines in Fig. 4(a). In Fig. 4(a) we can
observe that Spiking-AC and PPO demonstrate the fastest
convergence and achieve the highest rewards, highlighting
their ability to effectively balance the dual objectives of
maximizing the sum-rate and enhancing sensing accuracy in
complex and dynamic V2X scenarios. Conversely, the DDPG
algorithm shows moderate performance, with slower reward
accumulation and reduced optimization efﬁciency, indicating it
is less efﬁcient than Spiking-AC and PPO in optimizing beam-
forming and power allocation schemes in the high-dimensional
and uncertain action and state spaces considered. Speciﬁcally,
DDPG relies on an off-policy learning approach with a replay
memory buffer to store and sample past experiences [44]. This
off-policy learning mechanism occasionally introduces subop-
timal samples that hinder training efﬁciency while consuming
signiﬁcant computational resources [34]. In contrast, the pro-
posed Spiking-AC and PPO algorithms utilize an on-policy
learning approach and employ a policy-clipping technique
as in (33) that enables network parameter updates directly
from interactions with the environment, reducing the need for
large replay memory buffers typically required by off-policy
methods. This design allows Spiking-AC to achieve more
efﬁcient and streamlined learning while signiﬁcantly reducing
computational resource consumption. Additionally, compared
to PPO, Spiking-AC further beneﬁts from its spiking-based
neural network architecture, which not only improves conver-
gence and achievable rewards but also signiﬁcantly reduces
energy consumption during the training and inference pro-
cesses, which is detailed in the following.
Furthermore, the DQN algorithm and the Random scheme
are unable to to ﬁnd improved solutions during the learning
process, with the the Random approach shows the poorest
performance. Interestingly, despite being a learning-based
algorithm, DQN demonstrates the poor performance in the
uncertain and dynamic scenario characterized by continuous
state and action spaces. This is primarily because DQN
is inherently designed for discrete action spaces. Although
discretizing the continuous action space into a ﬁnite set of
representative actions partially addresses this limitation, it sig-
niﬁcantly compromises precision and ﬂexibility. Additionally,
storing these discretized actions in the replay memory buffer
further hinders exploration, severely restricting the algorithm’s
adaptability to dynamic environments. As expected, the Ran-
dom approach shows the poorest performance
We then evaluate the energy consumption during model
training and inference. In particular, the total number of
ﬂoating-point operations (FLOPs) is used to quantify the
computational workload during training and inference. These
operations are then mapped to energy consumption by
assigning hardware-speciﬁc energy coefﬁcients to different
operation types (i.e., MAC or AC) [43], [45]. As discussed in
Section IV-B, the Spiking-AC algorithm leverages binary
events (i.e., spikes) for computation, requiring only AC
operations to execute the dot product without the need
for multipliers. In contrast, baseline algorithms rely on tra-
ditional MAC operations. For a three-layers network, the
FLOPs for Spiking-AC and the baseline algorithms can be
calculated as: FLOPS spiking = ∑2i=1 (Ni×Mi×ςi) and
FLOPS baselines =∑3i=1 (Ni×Mi), respectively, where Ni
and Mi represent the input and output dimensions of the i-
th fully connected layer, ςi denotes the spike ﬁring rate [43],
[45]. Note that the ﬁnal layer of this fully connected network
does not use the LIF model, as the actor and critic networks
require continuous-valued outputs. Accordingly, the energy
consumption of Spiking-AC and the baseline algorithms can
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

SHANG et al.: ENERGY-EFFICIENT AND INTELLIGENT ISAC IN V2X NETWORKS WITH SNNs-DRIVEN DRL 1193
Fig. 5. (a) The achievable average sum-rate at Pmax = 40 dBm and (b) The
achievable sum-rate vs. maximum transmit power.
be expressed as:Espiking =
(
EAC×FLOPS spiking× ˜T
)
+
EMAC×N3×M3 andEbaseline =EMAC×FLOPS baselines,
respectively, where EAC = 0.1pJ and EMAC = 3.2pJ are
the energy consumption per operation for AC and MAC [46],
respectively.
We show the comparison of average energy consumption per
training and inference episode (i.e., the energy consumed by
the RSU for executing a single action using the trained model)
in Fig. 4(b) and Fig. 4(c). Notably, the energy consumption of
the PPO and DDPG algorithms is identical because they share
the same actor-critic framework 1. Additionally, the energy
consumption of PPO and DDPG is approximately twice that
of DQN, as DQN uses only a single network. As shown in
Fig. 4(b) and (c), Spiking-AC demonstrates superior efﬁciency,
consuming 5.15 times less energy than PPO and DDPG
during training and 2.58 times less than DQN. Notably, during
inference, Spiking-AC further reduces energy consumption
due to its spiking-based architecture.
Based on above analysis, we can conclude that Spiking-AC
achieves robust and efﬁcient training and inference perfor-
mance while signiﬁcantly conserving energy. Compared to
conventional methods, it reduces energy consumption by over
50% while delivering superior performance, underscoring its
practicality for energy-constrained V2X networks.
2) Communication Performance: We then present the
achievable communication rates during the vehicles’ driving
progress. As shown in Fig. 5(a), the proposed Spiking-AC
algorithm achieves the highest transmit rate during the ﬁrst
40 time steps, outperforming other algorithms. This highlights
Spiking-AC algorithm’s ability to maintain robust communi-
cation rates even for vehicles at long distances, enabled by its
efﬁcient beamforming and power allocation schemes driven by
the SNNs and policy-clipping technique. By jointly optimizing
beamforming and transmission power, Spiking-AC effectively
mitigates path loss, outperforming other algorithms that unable
to optimize these parameters simultaneously.
The PPO baseline, which employs the same policy-clipping
technique as Spiking-AC, achieves the second-best perfor-
mance during this period. However, Spiking-AC surpasses
PPO by integrating SNNs, which enhance training efﬁciency
and inference robustness. DDPG, however, despite sharing the
1The off-policy algorithms such as DDPG consume more energy than on-
policy algorithms due to the overhead of updating the replay memory buffer.
However, in this work, we focus exclusively on the energy consumption of
the neural network.
Fig. 6. Comparison of sensing performance for angle θ.
actor-critic framework with Spiking-AC and PPO, is unable
to achieve comparable communication rates, primarily due to
the absence of the policy-clipping technique that is crucial
for training stability and inference efﬁciency. Over time,
the communication rates increase as vehicles approach the
RSU, peaking when they are closest (i.e., 40-60 time steps)
and subsequently declining as they move away. Interestingly,
the DQN demonstrates contrasting results. This is because,
as vehicles approach the RSU, the challenges of managing
interference, optimizing resource allocation, and adapting to
the dynamic environment become more pronounced. Due to
its lack of coordination and adaptability, the DQN scheme
becomes increasingly ineffective in these conditions, resulting
in worse performance compared to when vehicles are farther
from the RSU. This underscores the critical importance of
intelligent resource management in multi-vehicle scenarios.
Next, we vary the maximum transmit power at the RSU,
i.e., Pmax, to evaluate the impact of power allocation on
communication performance. As shown in Fig. 5(b), the
proposed Spiking-AC algorithm consistently achieves the
highest sum-rate across all transmit power levels, outper-
forming baseline algorithms such as PPO, DDPG, DQN, and
Random allocation. Notably, at a maximum transmit power
of 40 dBm ( Pmax = 40 dBm), Spiking-AC achieves an
sum-rate of 10.864 bps/Hz, surpassing PPO (9.058 bps/Hz)
and DDPG (6.716 bps/Hz) by 19.96% and 61.7%, respec-
tively. Furthermore, as the maximum transmit power of
the RSU decreases, the performance gap among the algo-
rithms diminishes. However, Spiking-AC retains its superiority
by efﬁciently optimizing beamforming and power allocation
strategies, delivering consistently robust performance even
under stringent power constraints.
3) Sensing Performance: We evaluate the sensing perfor-
mance by analyzing the RMSE values achieved by different
algorithms. It is worth noting that the sensing accuracy exhibits
a trend similar to the communication sum-rate shown in
Fig. 5(a), peaking when the vehicles are closest to the RSU.
To ensure a comprehensive comparison, the RMSE values are
averaged over the entire process.
As shown in Fig. 6, the sensing performance for θ improves
across all algorithms as the transmit power increases. This
is because higher transmit power improves the RSU’s abil-
ity to process the echoes of sensing signals, as deﬁned
in (22), thereby reducing noise impact and enabling more
accurate angle estimation. Among the algorithms, Spiking-AC
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

1194 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Comparison of sensing performance for distance d.
consistently achieves the lowest RMSE across all power levels,
improving from 0.1654 rad at 0 dBm to 0.1588 rad at 40 dBm.
Compared to PPO, Spiking-AC achieves an RMSE reduction
of 1.31% at 10 dBm and 1.46% at 40 dBm, and signiﬁ-
cantly outperforms DDPG (7.53% reduction), DQN (83.35%
reduction), and Random (89.95% reduction) in optimizing
beamforming and power allocation strategies for sensing tasks.
In Fig. 7, the sensing performance for distance generally
improves (i.e., RMSE decreases) with increasing trans-
mit power across most algorithms. Speciﬁcally, Spiking-AC
achieves the best performance, with RMSE decreasing from
0.62175 at 0 dBm to 0.2 at 40 dBm, highlighting its superior
capability to leverage SNN-based policies for optimizing sens-
ing performance under varying power levels. In comparison,
PPO reduces its RMSE from 0.89357 to 0.3, while DDPG
decreases from 1.088 to 0.40358, demonstrating their ability
to adapt to higher transmit power. However, their performance
remains inferior to Spiking-AC. In contrast, DQN and Random
schemes display inconsistent trends, exhibiting non-monotonic
behavior with RMSE worsening to 4.79 and 7.435 at 40 dBm,
respectively. For DQN, this can be attributed to its reliance on
a discrete action space, which lacks the granularity required to
ﬁnely optimize transmit power, resulting in interference and
degraded sensing accuracy at higher power levels. Similarly,
the Random scheme suffers from high inference errors caused
by increased power levels.
At 40 dBm, Spiking-AC outperforms PPO and DDPG
by 33.33% and 50.37%, respectively. Moreover, Spiking-
AC achieves signiﬁcant RMSE reductions of 95.83% and
97.31% compared to DQN and Random, respectively. These
results emphasize Spiking-AC’s ability to effectively minimize
estimation error and maintain superior sensing performance
as transmit power increases. This consistent improvement
is attributed to Spiking-AC’s advanced framework, which
integrates SNNs for processing complex information and
employs policy-clipping techniques to ensure stable training
and efﬁcient inference. By effectively balancing beamforming
and power allocation, Spiking-AC minimizes interference and
path loss, thereby maintaining robust sensing performance.
VI. C ONCLUSION
In this work, we have proposed an energy-efﬁcient and
intelligent ISAC system for V2X networks. In particular, we
have ﬁrst utilized an MDP framework to model the complex
environmental dynamics, enabling the RSU to develop efﬁcient
beamforming schemes based solely on current sensing state
information. To enhance system intelligence, we have then
introduced a DRL algorithm based on the Actor-Critic frame-
work with a policy-clipping technique, facilitating the joint
optimization of beamforming and power allocation strategies
to ensure high communication rates and accurate sensing.
Furthermore, to address the energy demands of neural net-
works, we have integrated SNNs into the DRL algorithm,
leveraging their discrete spikes and temporal characteristics
to signiﬁcantly reduce energy consumption during training
and inference while simultaneously improving system per-
formance. Simulation results have shown that our proposed
scheme outperforms baseline methods in terms of energy con-
sumption, communication rates, and sensing accuracy. These
ﬁndings validate the potential of the proposed system to
enable intelligent, robust, and sustainable V2X connectivity
in dynamic and resource-constrained environments.
REFERENCES
[1] G. Kakkavas et al., “5G perspective of connected autonomous vehicles:
Current landscape and challenges toward 6G,” IEEE Wireless Commun.,
vol. 31, no. 4, pp. 299–306, Aug. 2024.
[2] S. A. Busari, K. M. S. Huq, S. Mumtaz, L. Dai, and J. Rodriguez,
“Millimeter-wave massive MIMO communication for future wireless
systems: A survey,” IEEE Commun. Surveys Tuts. , vol. 20, no. 2,
pp. 836–869, 2nd Quart., 2018.
[3] Y . Heng, Y . Zhang, A. Alkhateeb, and J. G. Andrews, “Site-speciﬁc
beam alignment in 6G via deep learning,” IEEE Commun. Mag., vol. 62,
no. 8, pp. 162–168, Aug. 2024.
[4] C. Dou, N. Huang, Y . Wu, L. Qian, and T. Q. S. Quek, “Channel
sharing aided integrated sensing and communication: An energy-efﬁcient
sensing scheduling approach,” IEEE Trans. Wireless Commun. , vol. 23,
no. 5, pp. 4802–4814, May 2024.
[5] N. Wu et al., “AI-enhanced integrated sensing and communications:
Advancements, challenges, and prospects,” IEEE Commun. Mag. ,
vol. 62, no. 9, pp. 144–150, Sep. 2024.
[6] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[7] F. Liu, W. Yuan, C. Masouros, and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: Communication served by sensing,”
IEEE Trans. Wireless Commun. , vol. 19, no. 11, pp. 7704–7719, Nov.
2020.
[8] X. Pang, S. Guo, J. Tang, N. Zhao, and N. Al-Dhahir, “Dynamic ISAC
beamforming design for UA V-enabled vehicular networks,”IEEE Trans.
Wireless Commun., vol. 23, no. 11, pp. 16852–16864, Nov. 2024.
[9] Y . Guo, W. Qin, Y . Xu, Y . Gu, C. Yin, and B. Xia, “Predictive
beam tracking and power allocation with cooperative sensing for V2I
communication,” IEEE Open J. Commun. Soc. , vol. 5, pp. 6048–6063,
2024.
[10] H. Yang et al., “Dynamic power allocation for integrated sensing
and communication-enabled vehicular networks,” IEEE Trans. Wireless
Commun., vol. 23, no. 9, pp. 12313–12330, Sep. 2024.
[11] C. Liu et al., “Learning-based predictive beamforming for integrated
sensing and communication in vehicular networks,” IEEE J. Sel. Areas
Commun., vol. 40, no. 8, pp. 2317–2334, Aug. 2022.
[12] R. Yang et al., “Deep learning-based joint transmit beamforming for
dual-functional radar-communication system,” IEEE Trans. Wireless
Commun., vol. 23, no. 10, pp. 15198–15211, Oct. 2024.
[13] Y . Liu, S. Zhang, X. Li, Y . Huang, Y . Fang, and H. Cao, “Deep reinforce-
ment learning-based beamforming design in ISAC-assisted vehicular
networks,” in Proc. IEEE Wireless Commun. Netw. Conf. (WCNC) , Apr.
2024, pp. 1–6.
[14] F. Xia et al., “Sensing-enabled predictive beamforming design for RIS-
assisted V2I systems: A deep learning approach,” IEEE Trans. Wireless
Commun., vol. 23, no. 6, pp. 5571–5586, Jun. 2024.
[15] K. Xiong, H. Y . Zhang, and C. W. Chan, “Performance evalua-
tion of UKF-based nonlinear ﬁltering,” Automatica, vol. 42, no. 2,
pp. 261–270, Feb. 2006.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

SHANG et al.: ENERGY-EFFICIENT AND INTELLIGENT ISAC IN V2X NETWORKS WITH SNNs-DRIVEN DRL 1195
[16] P. Li et al., “AnycostFL: Efﬁcient on-demand federated learning over
heterogeneous edge devices,” in IEEE Conf. Comput. Commun. , May
2023, pp. 1–10.
[17] A. de Vries, “The growing energy footprint of artiﬁcial intelligence,”
Joule, vol. 7, no. 10, pp. 2191–2194, Oct. 2023.
[18] T. L. Marzetta, E. G. Larsson, H. Yang, and H. Q. Ngo, Fundamentals
of Massive MIMO . Cambridge, U.K.: Cambridge Univ. Press, 2016.
[19] H. Q. Ngo, Massive MIMO: Fundamentals and System Designs ,
vol. 1642. Link ¨oping, Sweden: Link ¨oping University Electronic Press,
2015.
[20] M. A. Richards, Fundamentals of Radar Signal Processing , vol. 1. New
York, NY , USA: McGraw-Hill, 2005.
[21] H. L. Van Trees, Optimum Array Processing: Part IV of Detection,
Estimation, and Modulation Theory . Hoboken, NJ, USA: Wiley, 2002.
[22] F. Liu, Y .-F. Liu, A. Li, C. Masouros, and Y . C. Eldar, “Cram ´er-rao
bound optimization for joint radar-communication beamforming,” IEEE
Trans. Signal Process. , vol. 70, pp. 240–253, 2022.
[23] A. Liu et al., “A survey on fundamental limits of integrated sensing
and communication,” IEEE Commun. Surveys Tuts. , vol. 24, no. 2,
pp. 994–1034, 2nd Quart., 2022.
[24] S. M. Kay, Fundamentals of Statistical Signal Processing: Estimation
Theory. Englewood Cliffs, NJ, USA: Prentice-Hall, 1993.
[25] C. Shang, D. Thai Hoang, J. Yu, M. Hao, and D. Niyato, “Constructing
the metaverse with a new perspective: UA V FoV-assisted low-latency
imaging,” IEEE Wireless Commun. Lett. , vol. 14, no. 1, pp. 158–162,
Jan. 2025.
[26] J. Schulman, F. Wolski, P. Dhariwal, A. Radford, and O. Klimov,
“Proximal policy optimization algorithms,” 2017, arXiv:1707.06347.
[27] K. Arulkumaran, M. P. Deisenroth, M. Brundage, and A. A. Bharath,
“Deep reinforcement learning: A brief survey,” IEEE Signal Process.
Mag., vol. 34, no. 6, pp. 26–38, Nov. 2017.
[28] A. B. Sediq, R. H. Gohary, R. Schoenen, and H. Yanikomeroglu,
“Optimal tradeoff between sum-rate efﬁciency and Jain’s fairness index
in resource allocation,” IEEE Trans. Wireless Commun. , vol. 12, no. 7,
pp. 3496–3509, Jul. 2013.
[29] W. Yuan, F. Liu, C. Masouros, J. Yuan, D. W. K. Ng, and
N. Gonz ´alez-Prelcic, “Bayesian predictive beamforming for vehicular
networks: A low-overhead joint radar-communication approach,” IEEE
Trans. Wireless Commun. , vol. 20, no. 3, pp. 1442–1456, Mar. 2021.
[30] V . Mnih et al., “Human-level control through deep reinforcement
learning,” Nature, vol. 518, no. 7540, pp. 529–533, Sep. 2015.
[31] Z. Wang, T. Schaul, M. Hessel, H. Hasselt, M. Lanctot, and N. Freitas,
“Dueling network architectures for deep reinforcement learning,” in
Proc. Int. Conf. Mach. Learn. , 2016, pp. 1995–2003.
[32] N. Enami, R. A. Moghadam, K. Dadashtabar, and M. Hoseini,
“Neural network based energy efﬁciency in wireless sensor networks:
A survey,” Int. J. Comput. Sci. Eng. Surv. , vol. 1, no. 1, pp. 39–53,
Aug. 2010.
[33] D. T. Hoang, N. Van Huynh, D. N. Nguyen, E. Hossain, and
D. Niyato, Deep Reinforcement Learning for Wireless Communications
and Networking: Theory, Applications and Implementation . Hoboken,
NJ, USA: Wiley, 2023.
[34] J. Yu, A. Yousef Alhilal, T. Zhou, P. Hui, and D. H. K. Tsang,
“Attention-based QoE-aware digital twin empowered edge computing
for immersive virtual reality,” IEEE Trans. Wireless Commun. , vol. 23,
no. 9, pp. 11276–11290, Sep. 2024.
[35] N. Q. Hieu, D. T. Hoang, D. Niyato, D. N. Nguyen, D. I. Kim, and
A. Jamalipour, “Joint power allocation and rate control for rate splitting
multiple access networks with covert communications,” IEEE Trans.
Commun., vol. 71, no. 4, pp. 2274–2287, Apr. 2023.
[36] J. Schulman, P. Moritz, S. Levine, M. Jordan, and P. Abbeel, “High-
dimensional continuous control using generalized advantage estimation,”
2015, arXiv:1506.02438.
[37] M. Masadeh, O. Hasan, and S. Tahar, “Input-conscious approximate
multiply-accumulate (MAC) unit for energy-efﬁciency,” IEEE Access ,
vol. 7, pp. 147129–147142, 2019.
[38] W. Fang, Z. Yu, Y . Chen, T. Masquelier, T. Huang, and Y . Tian,
“Incorporating learnable membrane time constant to enhance learning
of spiking neural networks,” in Proc. IEEE/CVF Int. Conf. Comput. Vis.
(ICCV), Oct. 2021, pp. 2661–2671.
[39] J. Chen, N. Skatchkovsky, and O. Simeone, “Neuromorphic integrated
sensing and communications,” IEEE Wireless Commun. Lett. , vol. 12,
no. 3, pp. 476–480, Mar. 2023.
[40] X. Yao, F. Li, Z. Mo, and J. Cheng, “GLIF: A uniﬁed gated leaky
Integrate-and-Fire neuron for spiking neural networks,” in Proc. Adv.
Neural Inf. Process. Syst. , Jan. 2022, pp. 32160–32171.
[41] Y . Kim, H. Park, A. Moitra, A. Bhattacharjee, Y . Venkatesha, and
P. Panda, “Rate coding or direct coding: Which one is better for
accurate, robust, and energy-efﬁcient spiking neural networks?,” in Proc.
IEEE Int. Conf. Acoust., Speech Signal Process. (ICASSP) , May 2022,
pp. 71–75.
[42] S. Hassani and S. Hassani, “Dirac delta function,” in Mathematical
Methods: F or Students of Physics and Related Fields . New York, NY ,
USA: Springer, 2009, pp. 139–170.
[43] C. Shang, D. Thai Hoang, M. Hao, D. Niyato, and J. Yu, “Energy-
efﬁcient decentralized federated learning for UA V swarm with spiking
neural networks and leader election mechanism,” IEEE Wireless Com-
mun. Lett. , vol. 13, no. 10, pp. 2742–2746, Oct. 2024.
[44] T. P. Lillicrap et al., “Continuous control with deep reinforcement
learning,” 2015, arXiv:1509.02971.
[45] P. Panda, S. A. Aketi, and K. Roy, “Toward scalable, efﬁcient, and
accurate deep spiking neural networks with backward residual con-
nections, stochastic softmax, and hybridization,” Frontiers Neurosci. ,
vol. 14, p. 653, Jun. 2020.
[46] S. Han, J. Pool, J. Tran, and W. Dally, “Learning both weights and
connections for efﬁcient neural network,” in Proc. Adv. neural Inf.
Process. Syst., vol. 28, 2015, pp. 1–23.
Chen Shang received the M.S. degree from the
College of Big Data and Information Engineering,
Guizhou University, China, in 2023. He was a
Research Assistant with the Pillar of Information
Systems Technology and Design, Singapore Uni-
versity of Technology and Design, Singapore. He
is currently a Research Assistant with the Internet
of Things Thrust, The Hong Kong University of
Science and Technology (Guangzhou), China. His
research interests include deep learning, wireless
communications, and edge intelligence.
Jiadong Yu (Member, IEEE) received the Ph.D.
degree in computer science from the Queen
Mary University of London, U.K., in 2021. Since
November 2021, she has been with the Internet
of Things Thrust, The Hong Kong University of
Science and Technology (Guangzhou), where she
held the position of Post-Doctoral Research Fellow
until 2023 and is currently an Assistant Professor.
Her current research interests include artiﬁcial intel-
ligence for the Internet of Things, digital twin, and
metaverse technologies.
Dinh Thai Hoang (Senior Member, IEEE) received
the Ph.D. degree in computer science and engi-
neering from Nanyang Technological University,
Singapore, in 2016. He is currently a Faculty
Member with the School of Electrical and Data
Engineering, University of Technology Sydney,
Australia. His research interests include emerging
wireless communications and networking topics,
especially machine learning applications in net-
working, edge computing, and cybersecurity. He
has received several precious awards, including the
Australian Research Council Discovery Early Career Researcher Award, IEEE
TCSC Award for Excellence in Scalable Computing for Contributions on
“Intelligent Mobile Edge Computing Systems” (Early Career Researcher),
IEEE Asia-Paciﬁc Board (APB) Outstanding Paper Award in 2022, and
IEEE Communications Society Best Survey Paper Award in 2023. He is cur-
rently an Editor of IEEE T RANSACTIONS ON MOBILE COMPUTING , IEEE
TRANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE T RANSACTIONS
ON COMMUNICATIONS , and IEEE T RANSACTIONS ON NETWORK SCIENCE
AND ENGINEERING .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:20 UTC from IEEE Xplore.  Restrictions apply.
