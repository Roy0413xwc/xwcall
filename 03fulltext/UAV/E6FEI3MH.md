---
title: "ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network"
zotero_key: "E6FEI3MH"
pdf_key: "B36G57S8"
doi: "10.1109/TWC.2024.3509978"
collection: "UAV"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# ISAC Enabled Cooperative Detection for Cellular-Connected UAV Network — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025 1541
ISAC Enabled Cooperative Detection for
Cellular-Connected UA V Network
Yi Wang
 , Member , IEEE, Keke Zu
 , Member , IEEE, Luping Xiang, Member , IEEE,
Qixun Zhang
 , Member , IEEE, Zhiyong Feng
 , Senior Member , IEEE, Jie Hu
 , Senior Member , IEEE,
and Kun Yang
 , Fellow, IEEE
Abstract— The rapid development of low altitude Unmanned
Aerial Vehicles (UA Vs) as a new mode of transportation has
injected a new driving force into the market development, but at
the same time, unreported “black flight” UA Vs have also created
new risks in civil aviation safety, citizen privacy protection and
other social security areas. In this regard, the Integrated Sensing
And Communication (ISAC) capability of Base Station (BS) can
provide an effective means of communication and supervision of
low-altitude UA Vs. For example, by demarcating the electronic
fence area, the ISAC BS can realize automatic detection of
illegal invasion of UA Vs, effectively guaranteeing low-altitude
safety in the context of low-altitude economy. By leveraging
the high mobility of UA Vs and their strong air-ground Line-of-
Sight (LoS) channels, UA V-enabled ISAC is anticipated to provide
superior sensing and communication coverage, and enhanced
sensing and communication performance compared to terrestrial
ISAC. However, existing work mainly focus on single BS sensing
with the assistance of communication, which may not fully
activate ISAC’s potential and achieve high-precision long-range
sensing. Given the above considerations, this paper provides a
cellular-connected UA V system, where the BS and connected UA V
Received 30 January 2024; revised 13 August 2024 and 26 November 2024;
accepted 27 November 2024. Date of publication 11 December 2024; date of
current version 13 February 2025. This work was supported in part by the
Municipal Government of Quzhou under Grant 2023D027, Grant 2023D045,
and Grant 2023D005; in part by the Natural Science Foundation of China
under Grant 62132004 and Grant 92267202; and in part by Jiangsu Major
Project on Basic Researches under Grant BK20243059. The associate editor
coordinating the review of this article and approving it for publication was
K. Cohen. (Corresponding author: Yi Wang.)
Yi Wang is with the Yangtze Delta Region Institute (Quzhou), University of
Electronic Science and Technology of China, Quzhou 324003, China, and also
with the School of Information and Communication Engineering, University
of Electronic Science and Technology of China, Chengdu 611731, China
(e-mail: wangyi@csj.uestc.edu.cn).
Keke Zu is with the Yangtze Delta Region Institute (Quzhou), University of
Electronic Science and Technology of China, Quzhou 324003, China (e-mail:
zukeke@csj.uestc.edu.cn).
Luping Xiang is with the State Key Laboratory of Novel Software Tech-
nology, Nanjing University, Nanjing 210008, China, and also with the School
of Intelligent Software, Engineering, Nanjing University, Suzhou Campus,
Suzhou 215163, China (e-mail: luping.xiang@nju.edu.cn).
Qixun Zhang and Zhiyong Feng are with the Key Laboratory of
Universal Wireless Communications, Ministry of Education, Beijing Uni-
versity of Posts and Telecommunications, Beijing 100876, China (e-mail:
zhangqixun@bupt.edu.cn; fengzy@bupt.edu.cn).
Jie Hu is with the School of Information and Communication Engineering,
University of Electronic Science and Technology of China, Chengdu 611731,
China (e-mail: hujie@uestc.edu.cn).
Kun Yang is with the State Key Laboratory of Novel Software Technology,
Nanjing University, Nanjing 210008, China, also with the School of Intelligent
Software and Engineering, Nanjing University, Suzhou Campus, Suzhou
215163, China, and also with the School of Information and Communication
Engineering, University of Electronic Science and Technology of China,
Chengdu 611731, China (e-mail: kyang@ieee.org).
Digital Object Identifier 10.1109/TWC.2024.3509978
are employed to perform cooperative detection tasks for precise
detection. To unleash the potential of ISAC in cellular-connected
UA V systems, on the one hand, we propose an Extended Kalman
Filtering (EKF) based data fusion algorithm to provide precise
environment information and achieve beyond LoS sensing. On the
other hand, according to the fusion results, we optimize the com-
munication rate performance by jointly designing the transmit
beamforming and trajectory subject to the power and practical
fight constraints to combat the effect of mobility, while ensuring
the sensing requirements, which can achieve a positive feedback
loop. Extensive simulation results demonstrate that the proposed
data fusion algorithm improves the estimation accuracy by 67%
and the joint design of beamforming and trajectory algorithm
improves the communication data rate by more than 31%.
Index Terms— Cellular-connected UA V , cooperative detection,
data fusion, ISAC, joint design of the transmit beamforming and
trajectory.
I. I NTRODUCTION
W
ITH high maneuverability, flexibility of flight and
low deployment cost, the widely deployment of
multi-purpose and multi-system Unmanned Aerial Vehicles
(UA Vs) have attracted increasing focus to support a wide range
of commercial and civilian applications (e.g., traffic control,
search and rescue, aerial monitoring), which is expected to
provide better coverage, observation, measurement and control
performance [1], [2]. UA Vs can be exploited to provide an
important starting point for the construction of smart cities [3].
However, Due to their low cost, simple control, and ease
of transport, some UA Vs already possess a significant load
capacity, making them easily accessible to illegal individuals.
This poses a serious threat to social security [4], [5], [6]. Due
to the small Radar Cross-Section (RCS) of target UA Vs and
strong interference in the application environment, detection
and identification of them have been a challenging technical
problem, especially in the complex urban environments.
Wireless communication is a critically important technology
to unleash the maximum potential of UA Vs in numerous
applications, through which the UA Vs can be integrated into
the cellular network, thus exploiting the ubiquitous coverage
and high-speed backhaul characteristic of UA Vs for cellular
network [7]. Owing to the wide deployment of Base Station
(BS), high data rate and stable communication links are
considered to be the most promising candidates for providing
high broadband wireless services as well as long range control
and monitoring for UA V flight and task execution [8], [9].
1536-1276 © 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

1542 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025
Meanwhile, the cellular-connected UA V network is envisioned
to provide not only conventional high communication data rate
services, but also high-precision sensing capabilities, which is
one promising method for the detection of target UA Vs [10],
[11], [12]. Such mission-critical use cases have been driving
the integration of two functions of communication and sensing.
The emerging Integrated Sensing And Communication (ISAC)
technology improves the spectral efficiency, energy efficiency,
and hardware efficiency by using wireless channels to transmit
information while sensing the physical characteristics of the
surrounding environment actively, thus enhancing the com-
munication and sensing functions mutually and improving the
overall network performance [13], [14], [15].
Unlike conventional cellular networks which are fixed on
the ground, UA Vs offer the unique capability to function both
as aerial BSs and as users, thanks to their high mobility,
autonomous operation, and flexible deployment [16], [17],
[18]. Notably, UA Vs present a cost-effective solution for
enhancing ISAC services [19], [20], [21]. With their high
mobility and robust Line-of-Sight (LoS) links, UA V-enabled
ISAC can significantly boost system performance by extending
sensing and communication range, providing high-speed and
reliable communication, and enabling high-precision sensing.
Driven by these advantages, integrating UA Vs into existing
cellular networks emerges as an effective strategy to facili-
tate communication and monitor surrounding “black flight”
activities, thus ensuring low-altitude safety. Reference [22]
described a downlink sensing process where detection infor-
mation is derived from reflected echoes when the transmitted
signal encounters potential targets (e.g., UA Vs, buildings,
or other obstacles). To improve the sensing performance,
[23], [24] proposed a transmit beamforming design scheme
which aims to maximize the sensing beampattern while guar-
anteeing the Signal-to-Interference-plus-Noise Ratio (SINR)
requirement of each user. Besides, wireless communications
can improve sensing data processing through effective sensory
data offloading and edge computing [25], while sensing results
can, in turn, enhance communication system design. Numerous
beam training and tracking method have been proposed where
sensing works can be done with the downlink communication
simultaneously in various ISAC systems, which can reduce
overhead and achieve precise target tracking [26], [27], [28].
Meanwhile, according to the sensing results, the ISAC wave-
form and beamforming scheme, sensing/communication time
duration and real-time trajectories and can be designed prop-
erly to improve the communication (rate, throughput or SINR
performance while guaranteeing the sensing capabilities [29],
[30], [31]. Therefore, ISAC can provides the integration gain
based on measurement results and mutually benefit each
other [32]. However, most of mentioned work are focus on sin-
gle BS or UA V enabled network, the sensing/communication
performance are mainly dependent on the well LoS links
between targets and transceivers. For the cellular-connected
UA V network, BS has high sensing capabilities but limited
by the detection range, while the UA V has high mobility but
limited by the detection capabilities. It’s an essential problem
to utilize the integration gain of ISAC for precise detection.
Unlike terrestrial ISAC systems, the performance of
cellular-connected UA V networks is highly depend on UA V
deployment and trajectory design, as the motion of targets
varies with the UA V’s location. Considerable work have
focused on optimizing the UA V’s location, trajectory, and
beamforming [29], [30], [31], [33], [34], [35]. Reference [36]
introduced a Deep Reinforcement Learning (DRL) strategy
that learns environmental dynamics to make optimal trajectory
decisions while meeting control, energy, and communication
range requirements. Similarly, [37] proposed a solution to
maximize network communication coverage by optimizing
multi-UA V deployment, velocity, and energy usage. DRL has
also been employed for resource management to enhance
network reliability, latency, and energy efficiency [38], [39].
Besides, to minimize the age of information and ensure the
freshness of sensing data, [40] formulated an optimization
problem that jointly considers time duration, UA V trajectory,
and task allocation. Reference [41] optimized the trajectories
of UA Vs and its corresponding unmanned ground vehicle
for mobile charging to complete entire missions. Addition-
ally, [42] proposed a scheme that combines user association,
UA V location, and power allocation to improve UA V cov-
erage. Other studies have optimized trajectory and transmit
power to minimize energy consumption while meeting ISAC
requirements [43], [44]. Reference [45] suggested optimiz-
ing trajectory and Reconfigurable Intelligent Surface (RIS)
assisted jamming cancellation to boost data rates for Internet
of Things (IoT) applications. However, the closely coupled
resources like UA V trajectory and beamforming present a
challenging optimization task, especially given the limited
attention to this specific problem. Effectively designing joint
dynamic UA V trajectory and beamforming is crucial for fully
realizing the potential of ISAC in cellular-connected UA V
networks.
Inspired by the prior art, this paper examines a
cellular-connected UA V system that simultaneously offers
communication and sensing services between the target UA V
and connected UA V or BS. To improve the sensing accuracy,
we propose an ISAC enabled cooperative detection scheme
where the intra-system communication assists the sensing
results fusion taken by BS and connected UA V . Meanwhile, the
sensing fusion results will further improve the communication
data rate performance by designing appropriate beamforming
and trajectory, which can achieve a positive feedback loop.
The communication and sensing complement each other, thus
increasing high integration gain to enable the precise detection
of target UA Vs. The main contributions of this work are
explicitly contrasted in Table I and are summarized as follows.
• We present a cellular-connected UA V system, where the
BS and the connected UA V are employed to perform the
detection task jointly. To improve the detection perfor-
mance of this system, on the one hand, we conduct the
information fusion through communication to improve
the sensing performance. On the other hand, the sensing
data fusion results in turn improves the communication
data rate significantly. The communication and sensing
complement each other.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED COOPERATIVE DETECTION FOR CELLULAR-CONNECTED UA V NETWORK 1543
TABLE I
CONTRASTING THE CONTRIBUTIONS OF THIS WORK TO THE LITERATURE
• We propose an Extended Kalman Filtering (EKF) based
data fusion algorithm to fuse the sensing results obtained
by the BS and the connected UA V . Through fusion, not
only the accurate positioning information of surrounding
UA Vs can be obtained, but also the beyond LoS sensing
can be achieved.
• We design a joint beamforming and trajectory algorithm
to further improve the communication data rate perfor-
mance based on the fusion results, which is a non-convex
problem and difficult to be optimally solved. By decom-
posing it into two subproblems, we proposed a Successive
Convex Approximation (SCA) based algorithm to tackle
this issue in an iterative way.
The rest of this article is laid out as follows. Section II
presents the system model of the cellular-connected UA V
system. Section III provides an EKF based data fusion
algorithm. Section IV illustrates the joint design of beam-
forming and trajectory algorithm. Networking performance
of cellular-connected UA V are investigated and results are
provided in Section V. Finally, section VI concludes this
article.
Notations: Bold uppercase letters denote matrices (e.g.,
A). Bold lowercase letters denote column vectors (e.g., v).
Scalars are denoted by normal font (e.g., x); For an arbitrary
matrix A, rank(A), tr(A), AT , AH, and Ap,q denote its rank,
trace, transpose, conjugate, and the p-th row and q-th column
element, respectively.∥·∥ and|·| denote the Euclidean distance
and the magnitude, respectively.
II. S YSTEM MODEL
A. Scenario
Consider a cellular-connected UA V scenario in which
the UA V and BS conduct cooperative detection operations,
as shown in Fig. 1. A connected rotary-wing UA V is flying
from an initial point to a final point which are given in advance
within a time duration, during which it needs to maintain
reliable communication with the cellular network while mon-
itoring the surrounding K UA Vs in real time. Assume that
the BS is equipped with a Uniform Planar Array (UPA) while
each UA V is equipped with a Uniform Linear Array (ULA)
whose size is M Ut antennas for transmitting and M Ur antennas
for receiving that are placed vertically to the horizontal plane.
Equipped with two spatially separated half-wavelength spacing
analog antenna arrays and self-leakage canceler, the BS can
realize radio sensing towards potential targets while maintain-
ing necessary downlink communication services. Given that
the connected UA V is generally constrained by size and weight
Fig. 1. The cellular-connected UA V cooperative detection scenario.
limitations, the feasible size of the antenna array is affected,
which in turn impacts its beamforming capabilities and overall
sensing performance. For ease of analysis, we consider deploy-
ing a vertically oriented ULA on the UA V . By incorporating a
rotating mechanism into the rotary-wing UA V , it can achieve
360-degree coverage.
The three-dimensional position vectors of the BS is rep-
resented as qb = [ xb, yb, zb]T . Moreover, the connected
UA V is assumed to fly at a fixed altitude of H m which
can extend the coverage of BS and significantly enhance
the ISAC performance. For simplicity, we consider a finite
flying time interval t ∈ [0, T] from the predetermined ini-
tial position qI = [ xI , yI , H] to the final position qF =
[xF , yF , H], which can be discretized into N = T∆t equal
time slots with slot length ∆t. Let n∈ [1, 2,··· N ] denote the
n-th time slot. Here, ∆t is set to be small enough, during
which the position of UA V is assumed to be approximately
unchanged so as to facilitate the subsequent joint trajectory and
beamforming design for ISAC. The UA Vs are assumed to fly
at the time-varying coordinate qu (t) = [ xu (t) , yu (t) , H]T ,
at time interval 0≤ t≤ T . As a result, the trajectory of the
connected UA V , denoted byUA Vc, can be approximated by
the sequence qu,c [n] = [xu,c [n] , yu,c [n] , H]T , 1≤ n≤ N.
B. Singal Model
Due to the UA Vs always fly at a relatively high alti-
tude, the communication links between the connected UA V
and BS/UA V are generally dominated by the LoS compo-
nent. Unlike the existing works that assume the simplified
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

1544 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025
LoS channels, we consider the more practically accurate
altitude-dependent Rician fading channels here. Therefore, the
channel vector between the connected UA V and BS/UA V links
at the n-th slot can be represented as [46] and [47]
hc [n] =
√KR√KR + 1hLoSc [n] + 1√KR + 1hN LoSc [n] , (1)
where
hLoSc [n] = βc,0ej2πfc,0tδ (t− τc,0) a (qu,c [n]) (2)
and
hN LoSc [n] =
LX
l=1
βc,lej2πfc,ltδ (t− τc,l) a (qu,c [n]) (3)
denote the LoS and NLoS components of channel, respec-
tively. KR denotes the Rician K-factor, L denotes the number
of multipath, and βc,l, fc,l, τc,l denote the channel fading
coefficient, Doppler shift and delay of l∈{ 0, 1, 2,··· , L}-th
path, respectively; and a (qu,c [n]) denotes the corresponding
array steering vector at the n-th slot. Specially, the expression
of steering vector a (qu,c [n]) can be written as [48]
a (qu,c [n]) =
h
1, ejπ cos θn ,··· ejπ(M Ut−1) cos θn i . (4)
where θn denote the corresponding departure angle at the n-th
slot.
Consider the n-th particular time slot, the transmitted signal
of the connected UA V can be written as
x [n] =
KsX
i=0
wi [n] si [n], (5)
where si [n] denotes the information signal sent by the con-
nected UA V and wi [n] denotes the corresponding transmit
beamforming vector. The dedicated communication signal
between the connected UA V and BS s0 [n] is with zero mean
and unit variance. Due to the limited energy that UA Vs can
carry, we assume that there is sufficient energy for flying,
taking into account the effects of wind and other physical
factors, and do not discuss in detail how energy consumption
is affected by wind or other physical factors. With the given
maximum transmit power Ptotal, the beamforming vector has
power constraints as
KsX
i=0
∥wi [n]∥2≤ Ptotal. (6)
The received signal at the BS via a received beamforming
vector f0 [n] is thus given by
yc [n] = f H0 [n] hHc [n]w0 [n] s0 [n]
+
KsX
i=1
f H0 [n] hHc [n] wi [n] si [n] + zc [n] , (7)
where zc [n] denotes the Additive White Gaussian Noise
(AWGN) with variance σ2n. Note that the first term of
equation (7) denotes the desired received communication sig-
nal and the second term denotes the cochannel interference.
Therefore, the received SINR at the n-th slot is given as
γB [n] =
f H0 [n] hHc [n]w0 [n]2
KsP
i=1
f H0 [n] hHc [n]wi [n]2 + σ2n
, (8)
The achievable communication rate can be written as
Ccom [n] = log2 (1 + γB [n]).
After receiving the echo signals reflected by surrounding
UA Vs, the connected UA V and BS needs to estimate the
unknown parameters about the targets’ positioning infor-
mation. Assume that the position of potential targets are
predetermined based on the specific sensing tasks, it can
be denoted as qu,j [n] , j∈ {1, 2,··· , Ks}. Ks denotes the
number of surrounding UA Vs detected by the connected UA V .
For simplicity, we select the transmit beampattern as the key
sensing performance metric, for which depicts the transmit
power distribution towards the interesting angles based on
specific sensing tasks [49]. It can be designed properly to
enhance sensing performance (e.g., target sensing, detection,
and recognization) via echo signal processing. In the consid-
ered application scenario, the BS and connected UA V both
act as dual-functional platform to perform downlink commu-
nication and sense potential targets simultaneously. Thus, the
resultant transmit beampattern gain can be written as
Ps,j (qu,c [n]) = aH (qu,c [n])  wj [n] wHj [n] a (qu,c [n]) .
(9)
The targets’ positioning information can be obtained by pro-
cessing the reflected echoes received at the connected UA V and
BS, where the distance and velocity are estimated by employ-
ing a 2D Discrete Fourier Transform (DFT) approach [50].
After performing Inverse Fast Fourier Transform (IFFT) and
Fast Fourier Transform (FFT) operations on the fast and slow-
time domains, the delay bτn and Doppler frequency offset cµn
can be estimated as
bτn = 2∥qu,n− qu,c∥ /c + zτ ,
cµn = 2vTn (qu,n− qu,c) fc/ (c∥qu,n− qu,c∥) + zµ, (10)
where vn denotes the velocity of potential targets, and zτ ,
zµ denotes the corresponding noises with Gaussian distri-
bution, respectively. The Direction of Arrival (DoA) can
be estimated by applying the Mutiple Signal Classification
(MUSIC) algorithm, which decompose the covariance matrix
of the output data of any array to obtain the signal subspace
corresponding to the signal component and the noise subspace
orthogonal to the signal component [51]. Then by traversing
all possible arriving directions, the peak of angle spectrum
corresponding to the estimated DoA.
III. S ENSING DATA FUSION
In order to ensure that the cooperative detection task is
carried out successfully, first, the accuracy of detection needs
to be improved effectively. In rapidly changing environments,
the positioning accuracy of the targets may fall short of the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED COOPERATIVE DETECTION FOR CELLULAR-CONNECTED UA V NETWORK 1545
performance requirements for ISAC due to the limited sensing
capacity of a single UA V , as well as potential interference,
Doppler effects, and overlooked noise factors. To ensure
safe flight and swift task accomplishment in real time, it is
crucial that control commands and sensor data are reliably and
efficiently transmitted from the ground base station (BS) via
wireless communication. Obviously, frequent data collection
brings a lot of data redundancy, which will result in poor
transmission performance. The similar and abnormal data can
be eliminated and fused to improve the accuracy and stability
of the data, and further reduce the frequency and quantity
of data transmission. Therefore, data fusion has great efforts
in improving positioning accuracy and link stability with the
assistance of cellular-connected UA V network.
In this cellular-connected UA V scenario, we employ the
centralized fusion strategy where both the connected UA V
and BS transmit their sensing data to a central controller,
which performs the data fusion task. This central controller
can be a powerful server or a cloud-based service with
significant computational resources. In the fusion process, the
connected UA V use 5G wireless communication protocols
to communicate with BS to share its sensing data before it
reaches the central controller, while BS typically have robust
and high-capacity backhaul connections to central controllers,
such as fiber optics or high-speed wireless links. By following
this approach, this system can effectively utilize both UA V and
BS sensing capabilities while ensuring efficient and accurate
data fusion.
The Kalman filter gives us a way to combine measurements
from different sensors with a mathematical model that predicts
the object location [52]. It updates the trusted weights between
measurements and estimations based on how much we trust
a particular sensor or model to get the best estimate of the
exact location. The EKF based data level fusion can take into
account the real time performance of data and make full use
of positioning information in cellular-connected UA V system,
which are collected by UA V or base station, thus achieving
a high-precision UA V positioning for the precise detection
and high quality [53]. According to the sensing results SU
obtained by UA V and SB obtained by BS, we can not only
distinguish between different targets and other UA Vs, but also
further accurately estimate the trajectory of interested targets.
The sensing results contains two aspects: the positioning
information and the motion state, which can be denoted as
S = ( Ω, V ). The positioning information and motion state
are expressed as Ω = (r sin θ cos φ, rsin θ sin φ, rcos θ)T and
V = (µn), respectively.
First, we set normalized distance measurement to sim-
plify the sensing data fusion process. The positioning
and motion state Euclidean Distance (ED) between two
measurement sets SU and SB are given as ΨPi,j =


ΩUi − ΩBj 


22|i∈[1,2,··· ,s1],j∈[1,2,··· ,s2] and ΨMi,j = 


V Ui −
V Bj



2
2
, respectively. Then, the normalized ED can be con-
structed as
Ψi,j =
ΨPi,j
ΨPmax +
ΨMi,j
ΨMmax , (11)
where ΨPmax and ΨMmax denotes the maximum positioning
and motion state ED, respectively.
According to the ML criterion, the points Ψi,j with the
least ED shall be matched as the same target, which indicates
that SUi and SBj are two independent measurement results of
same target. The operation of EKF algorithm consists of two
parts: prediction and update. In the prediction stage, the filter
uses the estimated results of the previous state to make an
estimate of the current state according to the system dynamic
model. In the update stage, the filter optimizes the estimated
values using measurements of the current state to obtain an
optimal correction of estimation. Then the sensing data fusion
process can be conducted as follows.
The state variables and measured vectors are denoted as
x = ( r, v, ac)T and y = ( τ, µ, θ, φ)T , respectively, where
ac denotes the acceleration of UA V . Besides, we assume the
motion state of UA V remains unchanged in ∆T . The models
of state evolution and measurement are shown as xn = g(xn−1) + zx
yn = h(xn) + zy, (12)
where g (·) = [I3×3, ∆T· I3×3, ∆T 22 · I3×3; 03×3, I3×3,
∆T· I3×3; 03×3, 03×3, I3×3] denotes the state evolution
matrix and h (·) is provided in Section II. The process and
measurement noise vectors zx and zy are modeled as inde-
pendent zero-mean Gaussian distribution with Qx = diag(σ2rx,
σ2ry, σ2rz, σ2vx, σ2vy, σ2vz, σ2acx, σ2acy, σ2acz) and Qy = diag(σ2τ ,
σ2θ, σ2φ) covariance, respectively.
The following Jacobian matrices are given by
Gn−1 = ∂g∂x Hn = ∂h∂x (13)
Then the following EKF processing are implemented as
follows.
1) State Prediction :
xn|n−1 = g(xn−1) + ωn. (14)
2) Calculate Prediction Covariance Matrix :
Mn|n−1 = Gn−1Mn−1GHn−1 + Zs. (15)
3) Calculate Filter Gain :
Kn = Mn|n−1HHn  Qm + HnMn|n−1HHn −1. (16)
4) Update States :
xn = xn|n−1 + Kn
 
yn− h
 
xn|n−1

. (17)
5) Update Prediction Covariance Matrix :
Mn = (I− KnHn) Mn|n−1. (18)
Each time we get the positioning and orientation infor-
mation from the BS and connected UA V , then we fuse the
targets which has the least ED based on EKF algorithm.
After repeating these steps, the accuracy of the positioning
state estimate improves with the error covariance matrix M
constantly updating. The detailed EKF based fusion algorithm
is shown in Algorithm 1.
The data fusion process including two parts, i.e., data
sharing and data processing. On the one hand, it necessitates
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

1546 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025
Algorithm 1 EKF-Based Sensing Data Fusion Algorithm
1: Input: The sensing results SU and SB.
2: Output: The fusion result SF .
3: Initialization: A null set SF .
4: Step 1 : Calculate the normalized Euclidean dis-
tance between two measurement sets by employing
equation (11).
5: Step 2 :
6: for k = 1 to s2 do
7: Find the index corresponding to the least ED.
8: Fuse the i-th point with the j-th point according to
equation (14)-(18).
9: Put the fused results into SF .
10: end for
11: Step 3 : Put the rest of the unmatched ones into SF .
12: Return SF .
the scheduling of communication resources to perform the data
sharing. On the other hand, it requires computation resources
to execute data processing tasks and communication resources
for scheduling of computation resources. The overhead we
consider includes the data volume and the corresponding
communication protocols for scheduling.
First, the data volume can be calculated as Vd = Rd× Fd,
where Rd is the data rate (in bits per second) and Fd is the
transmission frequency. Then we assume the corresponding
communication protocols for scheduling is Vs. Since our focus
is not the protocols, we will not discuss the overhead of
this communication protocol in detail here. Thus, the total
overhead for sensing data fusion is Vf = Vd+Vs. According to
the analysis, the more frequency data is transferred, the greater
the overhead, which significantly degrade the communication
rate performance.
After fusion, both the connected UA V and BS store the
accurate positioning information of surrounding UA Vs, which
improves the sensing performance and achieves the beyond
LoS sensing. Besides, it can be employed to assist the joint
design of beamforming and trajectory to combat the high
mobility of UA V .
IV. J OINT DESIGN OF BEAMFORMING AND TRAJECTORY
To achieve precise target UA Vs positioning and infor-
mation sharing among connected UA V and cellular net-
work, it’s essential to provide two appropriate services for
cellular-connected UA V network, i.e., high-quality sensing
capability and high data rate communication service. However,
it has great challenges to achieve a good tradeoff between
these two potentially conflicting beamforming design objec-
tives in high dynamic environment. Fortunately, the previous
data fusion results provide precise environment information,
which can be exploited to steer the antenna beam to target
the interesting UA Vs and design suitable flight trajectory to
improve the communication data rate, thus mitigating the
effect of mobility to cooperative detection. In this section,
we propose a joint trajectory planning and beamforming
design algorithm to maximize the communication rate under
the sensing beampattern requirement and power budget con-
straints, in which the connected UA V move form one position
to another freely.
Consider a fully mobile UA V application scenario, accord-
ing to the task performed by the connected UA V , its trajectory
from qI to qF needs to be designed properly with maximum
flight speed Vmax. Then the maximum moving distances
between two consecutive slots is Dm = Vmax∆t. Therefore,
the following flight constraints are given as
qu,c [1] = qI , qu,c [N ] = qF
∥qu,c [n + 1]− qu,c [n]∥≤ Dm. (19)
In order to improve the communication data rate, the
connected UA V and BS can cooperate to combine multi-source
sensing data to form a wide-area distribution detection con-
figuration, so as to fully utilize the target detection gain and
improve the ISAC system environment sensing and commu-
nication data rate capability. In general, appropriate transmit
beampattern can be designed according to the communication
and target sensing requirements of application. After knowing
the accurate directions of the targets, the most important thing
need to do is maximize the beampattern gains towards these
interested directions. As a result, we aim to maximize the
communication data rate by jointly optimizing the communi-
cation beamforming as well as UA V’s trajectory, subject to the
power budget over different time slots, while considering the
UA V’s flight constraints. Thus, the corresponding optimization
problem is formulated as
(P 1) : max
w,qu,c
Ccom [n] (20)
s.t. P s,j (qu,c [n])≥ Γs (20a)
∥wc [n]∥2≤ Ptotal
(19) (20b)
where Γs denotes a certain threshold of sensing beam. In (P1),
(20a) represents the sensing beampattern gain should exceed
the threshold Γs. (20b) shows the power constraint. The flight
constraints are given in (19). Notice that problem (P1) is
difficult to solve for it’s non-convex with highly coupled
variables. Therefore, we decompose the original problem into
two subproblems, i.e., beamforming design subproblem and
trajectory design subproblem. For beamforming design sub-
problem, it can be solved by employing the Successive Convex
Approximation (SCA) with SemiDefinite Program (SDP) tech-
nology. For trajectory design subproblem, it can be solved by
employing the SCA technology. The beamforming vector and
trajectory can be alternately optimized in an iterative manner
and finally converge after multiple iterative loops.
A. Beamforming Design
In this subsection, we focus on the beamforming opti-
mization with any given UA V trajectory Q. The optimization
problem (P1) can be transformed into the following subprob-
lem, i.e.,
(P 2.1) : max
w
Ccom [n] (21)
s.t. P s,j (qu,c [n])≥ Γs (21a)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED COOPERATIVE DETECTION FOR CELLULAR-CONNECTED UA V NETWORK 1547
KsX
i=0
∥wi [n]∥2≤ Ptotal. (21b)
It is observed that problem (P2.1) is non-convex due to
the non-convex objective function (21). To deal with this
problem, we approximate the original non-convex objective
function as an equivalent convex one by employing the SCA
technique. For simplicity, we focus solely on the LoS path in
the next section so that the analysis can be simplified while
still capturing the dominant signal component crucial for UA V
communication. Let g1 (w [n]) =
KsP
i=0
f H0 [n] hHc [n]wi [n]2
and g2 (w [n]) =
KsP
i=1
f H0 [n] hHc [n]wi [n]2, the communica-
tion rate (21) can be rewritten as
Ccom [n] = log2

1 + f H0 [n] hHc [n]w0 [n]2KsP
i=1
f H0 [n] hHc [n]wi [n]2 + σ2n


= log2

1 + g1 (w [n])σ2n

− log2

1 + g2 (w [n])σ2n

. (22)
Since any concave function is globally upper-bounded by
its first-order Taylor expansion at any given local point, the
second term of (22) is globally upper-bounded by its first-order
Taylor expansion at any given point. Thus, we get
log2

1 + g2 (w [n])σ2n

≤ log2
 
1 + g2
 
w(m) [n]
σ2n
!
+
KsX
i=1
F0 [n]H [n]log2 (e)
σ2n + g2

w(m)i [n]

wi [n]− w(m)i [n]. (23)
where w(m) [n] is a given local point in the m-th iteration,
F0 [n] = f0 [n] f H0 [n] and H [n] = hc [n]hHc [n]. Therefore,
the lower bound of (22) can be obtained as (24), shown at the
bottom of the next page.
Note that the non-convex objective function (21) is approxi-
mated as a convex one by replacing it as its lower bound (24).
For simplicity, we define Wk = wkwHk , where Wk⪰ 0 and
rank (Wk) ≤ 1. Through this substitution, g1 (w [n]) and
g2 (w [n]) can be rewrote as
g1 (W [n]) =
KsX
i=0
tr (F0 [n]H [n] Wi [n])
g2 (W [n]) =
KsX
i=1
tr (F0 [n]H [n] Wi [n]). (25)
Thus, the optimization problem (P1) can be represented as
(P 2.2) : max
Wk
C lbbcom [n] (26)
s.t. tr
 
aH (qu,c [n]) Wka (qu,c [n])≥ Γs
(26a)
KsX
k=0
Wk≤ Ptotal (26b)
rank (Wk)≤ 1 (26c)
It can be observed that problem (P2.2) is a standard
SemiDefinite Program (SDP) which is convex except the
constraint (26c), then we perform a relaxation and deal with
this non-convex constraint via the SemiDefinite Relaxation
(SDR) technique. Further, problem (P2.2) can be optimally
solved by efficient convex optimization tools such as CVX.
Besides, there always exists a globally optimal solution to
problem (P2) even the rank-one constraint isn’t satisfied. Due
to limited space, there are no more details here, which can
refer to the reference [30] for the detailed proof process.
B. Trajectory Design
Next, for the above given beamforming design W , the
optimization problem of UA V’s trajectory can be transformed
into the following subproblem
(P 3) : max
qu,c
Ccom [n] (27)
s.t. P s,j (qu,c [n])≥ Γc (27a)
(19).
It is observed that the sub-optimization problem (P3) is
neither convex nor concave due to the non-convex objec-
tive function (27) and constraint (27a). Similarly, for the
non-convex object function (27), it can be rewritten as (30),
shown at the bottom of the next page. Given the m-th local
trajectory point q(m)u,c [n], the following inequality holds after
employing the first-order Taylor expansion, i.e.,
C (lbt)com [n] = log2


KsX
j=0
B(m) (Wj [n] , qu,c [n])


− log2


KsX
j=1
B(m) (Wj [n] , qu,c [n])


+ D(m) [n] qu,c [n]− q(m)u,c [n] , (28)
where
D(m) [n] = F0 [n]log2 (e)KsP
j=0
B(m) (Wj [n] , qu,c [n])


KsX
j=0
E(m) [n]


− F0 [n]log2 (e)KsP
j=1
B(m) (Wj [n] , qu,c [n])


KsX
j=1
E(m) [n]

 .
(29)
and the expression of E(m) [n] is (32), shown at the bottom
of the next page.
Next, to deal with the highly non-convex constraint (27a),
it can be reexpressed as (36), shown at the bottom of page 9.
Through adopting the SCA technique, the original function is
approximated by a more tractable function at a given local
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

1548 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025
point in each iteration. Similarly, (36) can be approximated as
its first-order Taylor expansion for handling the non-convexity
with given trajectory q(m)u,c [n] in the m-th iteration, which is
formulated as follows.
Ps,j (qu,c [n])≈P (m)s,j (qu,c [n])
=A(m)j [n] + I (m)j [n] qu,c [n]− q(m)u,c [n],
(33)
where the concrete expression of A(m) [n] and I (m) [n] are
shown in the bottom. Thus, the non-convex objective func-
tion (27) is approximated as a convex one, i.e.,
A(m)j [n] + I (m)j [n] qu,c [n]− q(m)u,c [n]≥ Γs. (34)
To improve the accuracy of approximation, a series of trust
region constraints are set as



q(m+1) [n]− q(m) [n]


≤ r(m), (35)
where r(m) denotes the trust radius in the m-th iteration.
After approximation, the non-convex objective function and
constraint are transformed into a convex one, respectively.
Thus, problem (P3) is transformed into
(P 3.1) : max
qu,c
C (lbt)com [n] (39)
s.t. (34), (35), (19).
Note that problem (P3.1) is a convex optimization problem
that can be efficiently solved by convex optimization solvers
such as CVX.
C. Overall Algorithm
According to the analysis results obtained in the previous
two subsections, we propose an overall iterative algorithm
for problem (P1) by applying the alternating optimization
method shown in Algorithm 2, which decomposes the orig-
inal problem into two sub-problems. Specifically, in order
to solve the original non-convex problem (P1), the entire
optimization variables, i.e., beamforming vectors and UA V’s
Algorithm 2 Joint Design of Beamforming and Trajectory
Algorithm
1: Input: β0, sensing results SF , total power Ptotal, the
number of time slots N, BS position qb, initial position
qI, final position qF , altitude H, threshold Γs.
2: Output: Beamforming Vector Matrix w∗k and Trajectory
Matrix q∗.
3: Initialization: Initialize wk and q, and set m1 = 0.
4: repeat
1) Solve sub-optimization problem P 2.2 under local
point W (m1)k to obtain W (m1)k ∗.
2) Reconstruct

w(m1)k
∗
.
3) repeat
a) Set m2 = 1, q(m2−1) =  q(m1−1)∗.
b) Solve sub-optimization problem P 3.1 under
local point q(m2−1), w(m1)k ∗ to obtain 
q(m2)∗.
c) If the objective value of P 3.1 increases then
q(m2) =  q(m2)∗, m2 = m2 + 1.
d) Else Execute r(m2) = r(m2)/2.
e) End If
4) until convergence.
5) return q(m1) = q(m2), m1 = m1 + 1.
5: until convergence.
6: return w∗k and q∗.
trajectory, are alternately optimized by solving problem (P2)
and (P3) correspondingly while keeping the other variable
fixed with the SCA technique. Besides, the results obtained
in each iteration can be used as the input of next itera-
tion. Finally, the joint optimal design beamforming vectors
and UA V’s trajectory can be obtained when the objective
value of problem (P1) converges after multiple iteration
loops.
C lbbcom [n] = log2

1 + g1 (w [n])σ2n

− log2
 
1 + g2
 
w(m) [n]
σ2n
!
−
KsX
i=1
F0 [n]H [n]log2 (e)
σ2n + g2

w(m)i [n]

wi [n]− w(m)i [n]. (24)
Ccom [n] = log2


KsX
j=0
B (Wj [n], qu,c [n])

− log2


KsX
j=1
B (Wj [n], qu,c [n])

 . (30)
B (Wj [n] , qu,c [n]) =
M UtX
s=1
F0[n]s,s Wj[n]s,s + 2 M UtX
p=1
M UtX
q=p+1
F0[n]p,q Wj[n]p,q cos  π (p− q) Hdc,b [n]  + σ2β0 d2c,b [n] .
(31)
E(m) [n] =
M UtX
p=1
M UtX
q=p+1
4π
F0[n]p,q Wj[n]p,q sin  π (q− p) Hd(m)c,b [n] ! (q− p) H2d(m)c,b [n]3 q(m)u,c [n]− qb . (32)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED COOPERATIVE DETECTION FOR CELLULAR-CONNECTED UA V NETWORK 1549
TABLE II
SIMULATION PARAMETERS [26], [30], [46], [54]
V. S IMULATION RESULTS
In this section, we present numerical results to validate
the performance of our proposed ISAC-enabled cooperative
detection in terms of sensing estimation accuracy and commu-
nication data rate. In order to verify the practicability of our
proposed algorithm, the selection of simulation parameters is
mainly based on the following aspects: the standards provided
by 3GPP, the practical scenario constraint, and findings from
previous related work. For this purpose, we assume that
UA Vs are operating within an area of 600m × 600m with
Ks = 4 target UA Vs located in the interested sensing area.
Moreover, we set the AWGN power at each receiver as σ2n =
−174 dBm/Hz, the total transmit power as Ptotal = 0.1 W, and
the channel power at the reference distance as β0 =−60 dB.
Without loss of generality, the connected UA V is assumed to
fly from the initial position qI = [20 , 20, 100] to the final
position qF = [300 , 300, 100] which keeps fixed altitude of
H = 100 m. Note that the locations and velocities of target
UA Vs are randomly distributed within the predefined range.
The detailed simulation parameters are shown in Table II.
A. Sensing Data Fusion Results
First, we compare our proposed work with four existing
detection methods on the performance of estimation accu-
racy, i.e., full-duplex downlink (FD-DL) [26], full-duplex
uplink (FD-UL) [30], half-duplex downlink (HD-DL) [55], and
half-duplex uplink (HD-UL) [56]. Without loss of generality,
we select the Root Mean Square Error (RMSE) as the key
performance metric of estimation accuracy. The estimation
RMSE of range and velocity are shown in Fig. 2(a) and
Fig. 2(b), respectively. It’s obvious that the FD-DL remains
Fig. 2. (a) Estimation RMSE of range vs. maximum speed. (b) Estimation
RMSE of velocity vs. maximum speed.
unchanged for the assumption the transceivers are a stationary
BS, whose performance is not affected by the mobility of Con-
nected UA V (CUA V). Due to the limited detection capability
of Connected UA V (CUA V) compared to BS, the estimation
RMSE of FD-UL is slightly increase as the speed of CUA V
increases since the high dynamic of wireless environment has
bad effect on the accuracy of estimations, which has a great
tr
 
aH (qc,j [n]) Wja (qc,j [n]) = M UtX
s=1
Wj[n]s,s + 2 M UtX
p=1
M UtX
q=p+1
Wj[n]p,q cos  π (q− p) Hdc,j [n] . (36)
A(m)j [n] =
M UtX
s=1
Wj[n]s,s + 2 M UtX
p=1
M UtX
q=p+1
Wj[n]p,q cos  π (q− p) Hd(m)c,j [n] !. (37)
I (m)j [n] =
M UtX
p=1
M UtX
q=p+1
4π
Wj[n]p,q sin  π (q− p) Hd(m)c,j [n] ! (q− p)H2d(m)c,j [n]3 q(m)u,c [n]− qu,j . (38)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

1550 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025
Fig. 3. Cooperative detection scenario.
need to be improved by designing corresponding algorithms.
Besides, the estimation performance of HD-DL and HD-UL
are not very good due to the sensing is mainly rely on Non-LoS
links whose received power is so small that it may be greatly
affected by noise. After fusion, the estimation RMSE of range
improves about 33% while the estimation RMSE of velocity
improves about 38%, which indicates that the EKF based
data fusion algorithm performs very well in improving the
estimation accuracy.
Fig. 3 describes the cooperative detection scenario in a visu-
alized way. By differentiating the sensing results before and
after data fusion in the figure, it’s obvious that the sensing data
fusion process can not only improve the estimation accuracy,
but also extend the sensing range, which can achieve beyond
LoS sensing to combat the complex sensing environments in
a efficient way.
B. Joint Design of Beamforming and Trajectory Results
Due to the original problem (P1) is equivalently decom-
posed into two subproblems and solved by solving these two
subproblems alternately to find the optimal design scheme.
To guarantee the validity of the proposed algorithm, we first
verify its convergence. Fig 4 shows the convergence behavior
of proposed algorithm. It can be observed from fig 4 that as
the number of iterations increases, the average communication
data rate increases sharply at first and then slowly converges to
a constant value after a few iterations, thus guaranteeing the
convergence and verifying the effectiveness of the proposed
algorithm.
Then Fig. 5 presents the achievable communication data
rate under different sensing beampattern threshold Γs. It is
intuitively observed that as the sensing beampattern thresh-
old increases, the communication data rate slowly decreases
because the total transmit power is limited. Thus, the beam-
forming design needs to achieve a good tradeoff between these
two potentially conflicting functions. Fig. 6 also illustrates
the corresponding UA V trajectory design under varying sens-
ing beampattern thresholds Γs. As the sensing requirements
increase, the threshold becomes higher, and the trajectory of
Fig. 4. The convergency of proposed algorithm.
Fig. 5. The communication data rate vs. the sensing beampattern
threshold Γs.
the CUA V is adjusted to move closer to the target sensing
area while distancing itself from the communication user. This
shift highlights the trade-off between sensing and communi-
cation performance. Our simulation results provide valuable
insights for UA V deployment and trajectory design. If network
dynamics can be anticipated in advance, UA V deployment and
trajectory can be strategically planned to meet the networka ¸´rs
specific requirements.
Fig. 7 shows the trajectory design of CUA V under different
time duration. Assume that the slot length ∆t = 1s, we com-
pare the trajectory design under T = 30s, 35s, 40s, 45s time
duration and the straight flight trajectory. With more flight
time duration, the CUA V prefers to spend more flight time to
move closer to the BS to maximize the communication data
rate performance while ensuing the sensing requirements. The
corresponding communication data rate is shown in Fig. 8,
which indicates that allocating more flight time will improve
the communication performance significantly.
Fig. 9 illustrates the communication data rate perfor-
mance of our proposed approach compared to three existing
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED COOPERATIVE DETECTION FOR CELLULAR-CONNECTED UA V NETWORK 1551
Fig. 6. The trajectory design of CUA V vs. the sensing beampattern
threshold Γs.
Fig. 7. The trajectory design of CUA V vs. flight time duration.
Fig. 8. The communication data rate vs. flight time duration.
algorithms: Hybrid Beamforming (HB) design [23], Intelli-
gent Reflecting Surface (IRS) assisted Joint Trajectory and
Beamforming (IRS-JTB) design [34] and Joint Trajectory
Fig. 9. The communication data rate vs. the sensing beampattern
threshold Γs.
and Beamforming (JTB) design [30]. As sensing require-
ments increase, a decrease in communication data rate is
observed across all four methods, highlighting the inherent
trade-off between sensing and communication performance.
Our proposed method, which leverages a data fusion algorithm
alongside the joint design of beamforming and trajectory,
significantly outperforms the other three approaches. The HB
design, while effective in achieving the target radar beam
pattern, offers limited performance gains due to its lack of
trajectory optimization. The IRS-JTB and JTB methods do
optimize UA V trajectory, transmit beamforming, and IRS
phase shifts to maximize the average achievable rate; however,
their performance is slightly compromised by lower position-
ing accuracy. Simulation results demonstrate that our proposed
joint design method improves the data rate by more than 31%
compared to the existing methods.
VI. C ONCLUSION
In this paper, we consider a cellular-connected UA V network
which utilize the almost ubiquitous accessibility of cellular
network and the flexibility of UA V to provide cooperative
detection task. Specifically, owing to the limited detection
range of BS and limited capacity of UA V , an EKF based sens-
ing data fusion algorithm is proposed to enable precise target
detection and achieve beyond LoS sensing. Besides, consider-
ing the bad estimation performance caused by high dynamic
of connected UA V , we propose a joint design of beamforming
and trajectory algorithm to improve the communication data
rate performance while guaranteeing the sensing requirements
depend on the precise environment information. Numerical
results show that the proposed data fusion algorithm can
improve the estimation accuracy by 38% and the joint design
of beamforming and trajectory algorithm can improve the com-
munication data rate by more than 31%. Since the transmitter
and receiver are co-located, sharing a single set of transmitted
signals and a majority of hardware and network infrastruc-
ture, self-interference is inevitable. Although full-duplex ISAC
design shows great potential, the self-interference cancellation
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

1552 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025
involves severe complexity, requiring sophisticated algorithms
and advanced hardware. Additionally, as the scale of the
network increases, how to analyze and optimize large-scale
UA V-enabled ISAC networks with random target distributions
becomes increasingly important. Implementing advanced algo-
rithms can increase power consumption, which is a critical
consideration for mobile devices and UA Vs. These limitations
highlight the need for continued research and innovation
to address these challenges and make ISAC systems more
practical and accessible for widespread use.
REFERENCES
[1] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets integrated
sensing and communication: Challenges and future directions,” IEEE
Commun. Mag. , vol. 61, no. 5, pp. 62–67, May 2023.
[2] Z. Xiao et al., “A survey on millimeter-wave beamforming enabled UA V
communications and networking,” IEEE Commun. Surveys Tuts., vol. 24,
no. 1, pp. 557–610, 1st Quart., 2022.
[3] R. Liu, A. Liu, Z. Qu, and N. N. Xiong, “An UA V-enabled intel-
ligent connected transportation system with 6G communications for
Internet of Vehicles,” IEEE Trans. Intell. Transp. Syst. , vol. 24, no. 2,
pp. 2045–2059, Feb. 2023, doi: 10.1109/TITS.2021.3122567.
[4] J. Zhao, J. Zhang, D. Li, and D. Wang, “Vision-based anti-UA V
detection and tracking,” IEEE Trans. Intell. Transp. Syst., vol. 23, no. 12,
pp. 25323–25334, Dec. 2022.
[5] C. J. Swinney and J. C. Woods, “A review of security incidents and
defence techniques relating to the malicious use of small unmanned
aerial systems,” IEEE Aerosp. Electron. Syst. Mag. , vol. 37, no. 5,
pp. 14–28, May 2022.
[6] J. Zheng et al., “An efficient strategy for accurate detection and
localization of UA V swarms,” IEEE Internet Things J. , vol. 8, no. 20,
pp. 15372–15381, Oct. 2021, doi: 10.1109/JIOT.2021.3064376.
[7] Q. Wu et al., “A comprehensive overview on 5G-and-beyond networks
with UA Vs: From communications to sensing and intelligence,” IEEE
J. Sel. Areas Commun. , vol. 39, no. 10, pp. 2912–2945, Oct. 2021, doi:
10.1109/JSAC.2021.3088681.
[8] A. V . Savkin, W. Ni, and M. Eskandari, “Effective UA V navigation for
cellular-assisted radio sensing, imaging, and tracking,” IEEE Trans. V eh.
Technol., vol. 72, no. 10, pp. 13729–13733, Oct. 2023.
[9] Y . Liu, Q. Wang, H.-N. Dai, Y . Fu, N. Zhang, and C. C. Lee,
“UA V-assisted wireless backhaul networks: Connectivity analysis of
uplink transmissions,” IEEE Trans. V eh. Technol. , vol. 72, no. 9,
pp. 12195–12207, Sep. 2023.
[10] G. Chen, C. Cheng, X. Xu, and Y . Zeng, “Minimizing the age of
information for data collection by cellular-connected UA V ,”IEEE Trans.
V eh. Technol., vol. 72, no. 7, pp. 9631–9635, Jul. 2023.
[11] P. Li, L. Xie, J. Yao, and J. Xu, “Cellular-connected UA V with
adaptive Air-to-Ground interference cancellation and trajectory opti-
mization,” IEEE Commun. Lett. , vol. 26, no. 6, pp. 1368–1372,
Jun. 2022.
[12] W. Du, T. Wang, H. Zhang, D. Wu, and Y . Li, “Resource allocation for
the backhaul of NOMA-based cellular UA V network,”IEEE Trans. V eh.
Technol., vol. 71, no. 11, pp. 11889–11899, Nov. 2022.
[13] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[14] J. A. Zhang et al., “Enabling joint communication and radar sensing
in mobile Networks—A survey,” IEEE Commun. Surveys Tuts. , vol. 24,
no. 1, pp. 306–345, 1st Quart., 2022.
[15] F. Liu, C. Masouros, A. P. Petropulu, H. Griffiths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun. , vol. 68, no. 6, pp. 3834–3862,
Jun. 2020.
[16] T. Bouzid, N. Chaib, M. L. Bensaad, and O. S. Oubbati, “5G net-
work slicing with unmanned aerial vehicles: Taxonomy, survey, and
future directions,” Trans. Emerg. Telecommun. Technol. , vol. 34, no. 3,
Mar. 2023, Art. no. e4721.
[17] K. Messaoudi, O. S. Oubbati, A. Rachedi, A. Lakas, T. Bendouma, and
N. Chaib, “A survey of UA V-based data collection: Challenges, solutions
and future perspectives,” J. Netw. Comput. Appl. , vol. 216, Jul. 2023,
Art. no. 103670.
[18] B. Chang, W. Tang, X. Yan, X. Tong, and Z. Chen, “Integrated
scheduling of sensing, communication, and control for mmWave/THz
communications in cellular connected UA V networks,” IEEE J. Sel.
Areas Commun., vol. 40, no. 7, pp. 2103–2113, Jul. 2022.
[19] N. Huang, C. Dou, Y . Wu, L. Qian, B. Lin, and H. Zhou, “Unmanned
aerial vehicle aided integrated sensing and computation with mobile edge
computing,” IEEE Internet Things J., vol. 10, no. 19, pp. 16844–168303,
Oct. 2023.
[20] J. Wu, W. Yuan, and L. Hanzo, “When UA Vs meet ISAC: Real-
time trajectory design for secure communications,” IEEE Trans. V eh.
Technol., vol. 72, no. 12, pp. 1–6, Dec. 2023.
[21] H. Sun, L. Zhang, J. Hou, T. Q. S. Quek, X. Wang, and Y . Zhang, “CoMP
transmission in downlink NOMA-based cellular-connected UA V net-
works,” IEEE Trans. Wireless Commun. , vol. 23, no. 7, pp. 7392–7407,
Jul. 2024.
[22] K. Meng et al., “UA V-enabled integrated sensing and communication:
Opportunities and challenges,” IEEE Wireless Commun. , early access,
Jun. 3, 2023, doi: 10.1109/MWC.131.2200442.
[23] C. Qi, W. Ci, J. Zhang, and X. You, “Hybrid beamforming for millimeter
wave MIMO integrated sensing and communications,” IEEE Commun.
Lett., vol. 26, no. 5, pp. 1136–1140, May 2022.
[24] K. Meng et al., “Throughput maximization for UA V-enabled integrated
periodic sensing and communication,” IEEE Trans. Wireless Commun. ,
vol. 22, no. 1, pp. 671–687, Jan. 2023.
[25] G. Zhu, J. Xu, K. Huang, and S. Cui, “Over-the-air computing for
wireless data aggregation in massive IoT,” IEEE Wireless Commun. ,
vol. 28, no. 4, pp. 57–65, Aug. 2021.
[26] Y . Cui et al., “Seeing is not always believing: ISAC-assisted predictive
beam tracking in multipath channels,” IEEE Wireless Commun. Lett. ,
vol. 13, no. 1, pp. 14–18, Jan. 2024, doi: 10.1109/LWC.2023.3303949.
[27] F. Liu, W. Yuan, C. Masouros, and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: Communication served by sensing,”
IEEE Trans. Wireless Commun. , vol. 19, no. 11, pp. 7704–7719,
Nov. 2020.
[28] J. Wu, W. Yuan, F. Liu, Y . Cui, X. Meng, and H. Huang, “UA V-based
target tracking: Integrating sensing into communication signals,” inProc.
IEEE ICC Workshops , Oct. 2022, pp. 309–313.
[29] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[30] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[31] Y . Liu, S. Liu, X. Liu, Z. Liu, and T. S. Durrani, “Sensing fairness-
based energy efficiency optimization for uav enabled integrated sensing
and communication,” IEEE Wireless Commun. Lett. , vol. 12, no. 10,
pp. 1702–1706, Oct. 2023.
[32] Q. Zhang, H. Sun, X. Gao, X. Wang, and Z. Feng, “Time-division ISAC
enabled connected automated vehicles cooperation algorithm design and
performance evaluation,” IEEE J. Sel. Areas Commun. , vol. 40, no. 7,
pp. 2206–2218, Jul. 2022.
[33] B. Liu, Y . Wan, F. Zhou, Q. Wu, and R. Q. Hu, “Resource allocation and
trajectory design for MISO UA V-assisted MEC networks,” IEEE Trans.
V eh. Technol., vol. 71, no. 5, pp. 4933–4948, May 2022.
[34] X. Pang, N. Zhao, J. Tang, C. Wu, D. Niyato, and K. Wong,
“IRS-assisted secure UA V transmission via joint trajectory and beam-
forming design,” IEEE Trans. Commun. , vol. 70, no. 2, pp. 1140–1152,
Feb. 2022.
[35] S. Shen, K. Yang, K. Wang, and G. Zhang, “UA V-aided vehicular short-
packet communication and edge computing system under time-varying
channel,” IEEE Trans. V eh. Technol. , vol. 72, no. 5, pp. 6625–6638,
May 2023.
[36] O. S. Oubbati, H. Badis, A. Rachedi, A. Lakas, and P. Lorenz, “Multi-
UA V assisted network coverage optimization for rescue operations using
reinforcement learning,” in Proc. IEEE Consum. Commun. Netw. Conf.
(CCNC), May 2023, pp. 1003–1008.
[37] H. Fu, J. Wang, J. Chen, P. Ren, Z. Zhang, and G. Zhao, “Dense
multiagent reinforcement learning aided multi-UA V information cov-
erage for vehicular networks,” IEEE Internet Things J. , vol. 11, no. 12,
pp. 21274–21286, Jun. 2024.
[38] Y . Su, H. Zhou, Y . Deng, and M. Dohler, “Energy-efficient cellular-
connected UA V swarm control optimization,” IEEE Trans. Wireless
Commun., vol. 23, no. 5, pp. 4127–4140, May 2024.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: ISAC ENABLED COOPERATIVE DETECTION FOR CELLULAR-CONNECTED UA V NETWORK 1553
[39] Y . Li and A. H. Aghvami, “Radio resource management for cellular-
connected UA V: A learning approach,” IEEE Trans. Commun. , vol. 71,
no. 5, pp. 2784–2800, May 2023.
[40] S. Zhang, H. Zhang, Z. Han, H. Vincent Poor, and L. Song, “Age of
information in a cellular Internet of UA Vs: Sensing and communication
trade-off design,” IEEE Trans. Wireless Commun. , vol. 19, no. 10,
pp. 6578–6592, Oct. 2020.
[41] K. Messaoudi, O. S. Oubbati, A. Rachedi, and T. Bendouma, “UA V-
UGV-based system for AoI minimization in IoT networks,” in Proc.
IEEE Int. Conf. Commun. , Jun. 2023, pp. 4743–4748.
[42] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-UA V
networks,” IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660–2672,
Apr. 2021.
[43] D. Liu, Y . Gao, S. Hu, W. Ni, and X. Wang, “Trajectory design for
integrated sensing and communication enabled by cellular-connected
UA V ,”IEEE Wireless Commun. Lett. , vol. 13, no. 7, pp. 1973–1977,
Jul. 2024.
[44] S. Hu, X. Yuan, W. Ni, and X. Wang, “Trajectory planning of cellular-
connected UA V for communication-assisted radar sensing,”IEEE Trans.
Commun., vol. 70, no. 9, pp. 6385–6396, Sep. 2022.
[45] S. Hu, X. Yuan, W. Ni, X. Wang, and A. Jamalipour, “RIS-assisted
jamming rejection and path planning for UA V-borne IoT platform: A
new deep reinforcement learning framework,” IEEE Internet Things J. ,
vol. 10, no. 22, pp. 20162–20173, Nov. 2023.
[46] Study on Channel Model for Frequencies From 0.5 To 100 GHz, Standard
38.901 V14.3.0, 2017.
[47] S. D. Muruganathan et al., “An overview of 3GPP release-15 study on
enhanced LTE support for connected drones,” IEEE Commun. Standards
Mag., vol. 5, no. 4, pp. 140–146, Dec. 2021.
[48] W. Yi, W. Zhiqing, and F. Zhiyong, “Beam training and tracking in
mmWave communication: A survey,” China Commun. , vol. 21, no. 6,
pp. 1–22, Jun. 2024.
[49] H. Hua, J. Xu, and T. X. Han, “Optimal transmit beamforming for
integrated sensing and communication,” IEEE Trans. V eh. Technol. ,
vol. 72, no. 8, pp. 10588–10603, Aug. 2023.
[50] X. Chen, Z. Feng, Z. Wei, J. A. Zhang, X. Yuan, and P. Zhang,
“Concurrent downlink and uplink joint communication and sensing for
6G networks,” IEEE Trans. V eh. Technol., vol. 72, no. 6, pp. 8175–8180,
Jun. 2023.
[51] R. Xie, D. Hu, K. Luo, and T. Jiang, “Performance analysis of joint
range-velocity estimator with 2D-MUSIC in OFDM radar,” IEEE Trans.
Signal Process., vol. 69, pp. 4787–4800, 2021.
[52] Z. Xing, Y . Xia, L. Yan, K. Lu, and Q. Gong, “Multisensor distributed
weighted Kalman filter fusion with network delays, stochastic uncer-
tainties, autocorrelated, and cross-correlated noises,” IEEE Trans. Syst.
Man, Cybern. Syst. , vol. 48, no. 5, pp. 716–726, May 2018.
[53] M. Mammarella, G. Campa, M. R. Napolitano, M. L. Fravolini, Y . Gu,
and M. G. Perhinschi, “Machine vision/GPS integration using EKF for
the UA V aerial refueling problem,” IEEE Trans. Syst. Man, Cybern.,
Part C, vol. 38, no. 6, pp. 791–801, Nov. 2008.
[54] The State Council and the Central Military Commission, “The pro-
visional regulations on the flight management of unmanned aircraft,”
Jun. 2023. [Online]. Available: https://english.www.gov.cn/policies/
latestreleases/202306/28/content_WS649c3653c6d0868f4e8dd4f8.html
[55] Q. Zhao, A. Tang, X. Wang, J. Liu, Y . Zhou, and F. Gao, “Joint transmit
and receive beamforming for integrated bistatic radar sensing and MU-
MIMO communications,” in Proc. IEEE V eh. Technol. Conf., Apr. 2023,
pp. 1–6.
[56] X. Chen, Z. Feng, J. Andrew Zhang, Z. Wei, X. Yuan, and P. Zhang,
“Sensing-aided uplink channel estimation for joint communication and
sensing,” IEEE Wireless Commun. Lett. , vol. 12, no. 3, pp. 441–445,
Mar. 2023.
Yi Wang (Member, IEEE) received the B.Eng.
degree from Beijing Jiaotong University (BJTU),
Beijing, China, in 2018, and the Ph.D. degree from
Beijing University of Posts and Telecommunica-
tions (BUPT), Beijing, in 2023. He is currently a
Post-Doctoral Researcher with the Yangtze Delta
Region Institute (Quzhou), University of Electronic
Science and Technology of China, and the School
of Information and Communication Engineering,
University of Electronic Science and Technology of
China. His research interests include mmWave com-
munication, integrated sensing and communications, and resource allocation.
Keke Zu (Member, IEEE) received the B.Sc. degree
in communications engineering from Southwest
Jiaotong University, China, in 2006, the M.Sc.
degree in communication and information systems
from Southeast University, China, in 2009, and the
Ph.D. degree from The University of York, U.K.,
in 2013. His research interests include channel esti-
mation, ISAC, and intelligent communication.
Luping Xiang (Member, IEEE) received the B.Eng.
degree (Hons.) from Xiamen University, China,
in 2015, and the Ph.D. degree from the University of
Southampton, in 2020. From 2020 to 2021, he was a
Research Fellow with the Next Generation Wireless
Group, University of Southampton. In November
2021, he joined the University of Electronic Sci-
ence and Technology of China (UESTC) as a
Faculty Member. In September 2024, he joined
Nanjing University as an Assistant Professor. His
research interests include native intelligence at wire-
less communication, end-to-end transmission technology, computer vision,
and integrated sensing and communication transmission.
Qixun Zhang (Member, IEEE) received the B.Eng.
degree in communication engineering and the Ph.D.
degree in circuits and systems from Beijing Uni-
versity of Posts and Telecommunications (BUPT),
Beijing, China, in 2006 and 2011, respectively. From
March 2006 to June 2006, he was a Visiting Scholar
with the University of Maryland, College Park, MD,
USA. From November 2018 to November 2019,
he was a Visiting Scholar with the Department of
Electrical and Computer Engineering, University of
Houston, Houston, TX, USA. He is currently a
Professor with the Key Laboratory of Universal Wireless Communications,
Ministry of Education, School of Information and Communication Engi-
neering, BUPT. His research interests include 5G mobile communication
systems, integrated sensing and communication for autonomous driving vehi-
cle, mmWave communication systems, and unmanned aerial vehicles (UA Vs)
communication. He is active in ITU-R WP5A/5C/5D standards.
Zhiyong Feng (Senior Member, IEEE) received the
B.S., M.S., and Ph.D. degrees from Beijing Uni-
versity of Posts and Telecommunications (BUPT),
Beijing, China. She is currently a Full Professor
with BUPT. She is also the Director of the Key
Laboratory of Universal Wireless Communications,
Ministry of Education. Her research interests include
wireless network architecture design and radio
resource management in 5th-generation mobile net-
works (5G), spectrum sensing and dynamic spectrum
management in cognitive wireless networks, univer-
sal signal detection and identification, and network information theory. She is
a Technical Advisor of NGMN; an Editor of IET Communications and KSII
Transactions on Internet and Information Systems ; and a reviewer of IEEE
TRANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE T RANSACTIONS
ON VEHICULAR TECHNOLOGY , and IEEE J OURNAL ON SELECTED AREAS
IN COMMUNICATIONS . She is active in ITU-R, IEEE, ETSI, and CCSA
standards.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply. 

1554 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 24, NO. 2, FEBRUARY 2025
Jie Hu (Senior Member, IEEE) received the B.Eng.
and M.Sc. degrees from Beijing University of Posts
and Telecommunications, China, in 2008 and 2011,
respectively, and the Ph.D. degree from the School
of Electronics and Computer Science, University of
Southampton, U.K., in 2015. Since March 2016,
he has been working with the School of Infor-
mation and Communication Engineering, University
of Electronic Science and Technology of China
(UESTC). He is currently a Full Professor and the
Ph.D. Supervisor. His current research focuses on
wireless communications and resource management for 6G, wireless infor-
mation and power transfer, and integrated communication, computing and
sensing. He is a Technical Committee Member of the ZTE Technology. He is
the Program Vice-Chair of IEEE TrustCom 2020, the Technical Program
Committee (TPC) chair of IEEE UCET 2021, and the Program Vice-Chair
of UbiSec 2022. He serves as a TPC Member for several prestigious
IEEE conferences, such as IEEE Globecom/ICC/WCSP. He has won the
Outstanding Young Researcher Award of IEEE TCGCC in 2024. He has
also won the Best Paper Award of IEEE SustainCom 2020 and the Best
Paper Award of IEEE MMTC 2021. He is an Editor of IEEE W IRELESS
COMMUNICATIONS LETTERS , IEEE/CIC C HINA COMMUNICATIONS , and
Journal of Communications and Information Networks . He also served as a
Guest Editor for IEEE Communications Magazine .
Kun Yang (Fellow, IEEE) received the Ph.D.
degree from the Department of Electronic and
Electrical Engineering, University College London
(UCL), UK. He is currently the Chair Professor
with the School of Intelligent Software and Engi-
neering, Nanjing University, China. He is also an
Affiliated Professor with the University of Essex,
U.K., and UESTC. He has published more than
500 articles and filed 50 patents. His research
interests include wireless networks and communi-
cations, communication-computing cooperation, and
new artificial intelligence (AI) for wireless. He is a member of Academia
Europaea (MAE), a fellow of IET, and a Distinguished Member of ACM.
He has been a Judge of GSMA GLOMO Award at World Mobile CongressC
Barcelona since 2019. He was a Distinguished Lecturer of IEEE ComSoc
(2020–2021) and a recipient of the 2024 IET Achievement Medals. He serves
on the editorial boards for several IEEE journals (e.g., IEEE W IRELESS
COMMUNICATIONS , IEEE T RANSACTIONS ON VEHICULAR TECHNOLOGY ,
and IEEE T RANSACTIONS ON NANO BIOSCIENCE ). He is the Deputy Editor-
in-Chief of IET Smart Cities journal.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 08:13:00 UTC from IEEE Xplore.  Restrictions apply.