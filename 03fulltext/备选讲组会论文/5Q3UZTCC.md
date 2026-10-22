---
type: literature-fulltext
title: "Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement Learning Approach"
zotero_key: "5Q3UZTCC"
pdf_key: "WVIK3WY3"
doi: "10.1109/TWC.2025.3583950"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Integrated Sensing and Communications for Low-Altitude Economy- A Deep Reinforcement Learning Approach.md"
fulltext_path: "03fulltext/备选讲组会论文/5Q3UZTCC.md"
zotero_item: "zotero://select/library/items/5Q3UZTCC"
zotero_pdf: "zotero://open-pdf/library/items/WVIK3WY3"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Integrated Sensing and Communications for Low-Altitude Economy: A Deep Reinforcement Learning Approach

> PDF 原文逐页文本抽取；来源文件 SHA-256：`e4c5710789446567e1ee85dd62d4f42eb00ba7aeb8b77b040abf72db1013ceb4`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 351
Integrated Sensing and Communications for
Low-Altitude Economy: A Deep Reinforcement
Learning Approach
Xiaowen Ye
 , Yuyi Mao
 , Senior Member , IEEE, Xianghao Yu
 , Senior Member , IEEE,
Shu Sun
 , Senior Member , IEEE, Liqun Fu
 , Senior Member , IEEE, and Jie Xu
 , Fellow, IEEE
Abstract—This paper studies an integrated sensing and com-
munications (ISAC) system for low-altitude economy (LAE),
where a ground base station (GBS) provides communication
and navigation services for authorized unmanned aerial vehicles
(UA Vs), while sensing the low-altitude airspace to monitor the
unauthorized mobile target. The expected communication sum-
rate over a given ﬂight period is maximized by jointly optimizing
the beamforming at the GBS and UA Vs’ trajectories, subject to
the constraints on the average signal-to-noise ratio requirement
for sensing, the ﬂight mission and collision avoidance of UA Vs,
as well as the maximum transmit power at the GBS. Typically,
this is a sequential decision-making problem with the given
ﬂight mission. Thus, we transform it to a speciﬁc Markov
decision process (MDP) model called episode task. Based on
this modeling, we propose a novel LAE-oriented ISAC scheme,
referred to as Deep LAE-ISAC (DeepLSC), by leveraging the
deep reinforcement learning (DRL) technique. In DeepLSC,
a reward function and a new action selection policy termed
constrained noise-exploration policy are judiciously designed to
fulﬁll various constraints. To enable efﬁcient learning in episode
tasks, we develop a hierarchical experience replay mechanism,
where the gist is to employ all experiences generated within each
Received 5 December 2024; revised 27 April 2025; accepted 22 June 2025.
Date of publication 4 July 2025; date of current version 22 December 2025.
The work of Xianghao Yu was supported in part by Hong Kong Research
Grants Council under Grant 16212922. The work of Shu Sun was supported
in part by the National Natural Science Foundation of China (NSFC) under
Grant 62271310. The work of Liqun Fu was supported in part by the
National Natural Science Foundation of China under Grant U23A20281 and
in part by the National Social Science Foundation of China under Grant
24&ZD189. The work of Jie Xu was supported in part by the National Natural
Science Foundation of China under Grant 62471424 and Grant 92267202 and
in part by Guangdong Provincial Key Laboratory of Future Networks of
Intelligence under Grant 2022B1212010001. The associate editor coordinating
the review of this article and approving it for publication was H. Zhang.
(Corresponding author: Xianghao Yu.)
Xiaowen Ye is with the College of Photonic and Electronic
Engineering,Normal University, Fuzhou 350117, China (e-mail:
xiaowenye@fjnu.edu.cn).
Yuyi Mao is with the School of Computer Science and Engineer-
ing, Macau University of Science and Technology, Taipa, Macau (e-mail:
yymao@must.edu.mo).
Xianghao Yu is with the Department of Electrical Engineering, City
University of Hong Kong, Hong Kong, China (e-mail: alex.yu@cityu.edu.hk).
Shu Sun is with the Department of Electronic Engineering and the Coop-
erative Medianet Innovation Center, Shanghai Jiao Tong University, Shanghai
200240, China (e-mail: shusun@sjtu.edu.cn).
Liqun Fu is with the School of Informatics, Xiamen University, Xiamen
361005, China (e-mail: liqun@xmu.edu.cn).
Jie Xu is with the School of Science and Engineering (SSE), Shenzhen
Future Network of Intelligence Institute (FNii-Shenzhen), and Guangdong
Provincial Key Laboratory of Future Networks of Intelligence, The Chinese
University of Hong Kong, Shenzhen, Guangdong 518172, China (e-mail:
xujie@cuhk.edu.cn).
Digital Object Identiﬁer 10.1109/TWC.2025.3583950
episode to jointly train the neural network. Besides, to enhance
the convergence speed of DeepLSC, a symmetric experience
augmentation mechanism, which simultaneously permutes the
indexes of all variables to enrich available experience sets, is
proposed. Simulation results demonstrate that compared with
benchmarks, DeepLSC yields a higher sum-rate while meeting
the preset constraints, achieves faster convergence, and is more
robust against different settings.
Index Terms—Low-altitude economy (LAE), integrated sensing
and communications (ISAC), joint beamforming and trajectory
design, deep reinforcement learning (DRL).
I. I NTRODUCTION
L
OW-ALTITUDE economy (LAE), composed of various
low-altitude ﬂight activities involving unmanned and
manned aircraft, such as unmanned aerial vehicles (UA Vs)
and electric vertical take-off and landing (eVTOL), has gained
widespread attention from academia and industry [1]. It is
expected that LAE could support a wide variety of important
applications, including but not limited to transportation, envi-
ronmental monitoring, tourism, and agriculture [2]. However,
the successful implementation of LAE requires the strictly
safe operation (e.g., collision-free) of all aircraft, especially
in the presence of massive aircraft and unauthorized targets
[3]. Therefore, it is imperative to provide seamless commu-
nication and navigation for authorized aircraft, as well as
ubiquitous surveillance of unauthorized targets in the low-
altitude airspace.
One possible solution that could facilitate the implemen-
tation of LAE is to jointly adopt wireless communications
and radar sensing technologies. Conventionally, these two
technologies are designed and implemented independently.
This, however, results in low spectrum utilization and expen-
sive hardware overhead. Fortunately, integrated sensing and
communications (ISAC), a key technique for next-generation
wireless networks, is capable of simultaneously performing
wireless communications and radar sensing based on the
common spectrum resource and hardware infrastructures [4].
With ISAC, the ground base station (GBS) provides commu-
nication and navigation services for authorized aircraft, while
sensing the low-altitude airspace to monitor unauthorized
targets.
A. Related Work
Currently, there have been substantial bodies of works
studying the integration of aircraft (speciﬁcally UA Vs) and
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

352 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
ISAC systems, which can be divided into two main paradigms
according to the role that UA Vs play [5], [6], [7], [8], [9],
[10], [11], [12], [13], [14], [15], [16], [17], [18], [19], [20],
[21], [22], [23], [24], [25], [26], [27], [28], [29], [30], [31],
[32], [33], [34], [35]. The ﬁrst paradigm is referred to as
UA V-assisted ISAC services, where each UA V operates as a
new aerial platform (e.g., aerial base station or relay) to serve
ground users. For example, towards the goal of minimizing the
age of information of sensed data, a joint extremum principles
and dynamic programming scheme was proposed in [5] to
optimize the UA V power and trajectory, whereas in [6], a
successive convex approximation (SCA) iterative method was
used to reﬁne the UA V trajectory and time allocation for
both communication and sensing. These two works, however,
were merely concerned about the communication performance,
while ignoring the sensing requirement. By contrast, the
works [7], [8], [9], [10], [11] considered both simultaneously.
Speciﬁcally, in [7], Wang et al. investigated a dual-function
multi-UA V wireless network, in which the sum-rate was max-
imized by jointly optimizing the UA V location, transmit power,
and user association under the Cram ´er-Rao bound constraint.
In [8], Chang et al. proposed a joint scheduling strategy for
control, communication, and sensing in millimeter-wave UA V
networks, such that the communication and sensing require-
ments can be met while maintaining good control performance.
By jointly employing the alternating optimization and SCA
method, the authors of [9] proposed a joint UA V deploy-
ment and power control scheme to maximize the minimum
detection probability, whilst the authors of [10] optimized the
deployment and joint communication and sensing precoder to
balance communication rate and sensing accuracy. Besides,
the potential of UA Vs for physical layer security provisioning
in ISAC systems was explored in [11].
The aforementioned research, however, mainly focused on
the ISAC in quasi-static UA V scenarios, without exploiting the
controllable mobility over the three-dimensional (3D) space.
To explore the advantages of UA V mobility, literature [12],
[13], [14], [15], [16], [17], [18], [19], [20], [21], [22], [23],
[24] studied the UA V trajectory optimization for ISAC appli-
cations. To be speciﬁc, by optimizing the UA V trajectory, the
real-time secrecy rate was maximized in [12], while the UA V
propulsion consumption was minimized in [13]. Furthermore,
in [14], [15], [16], [17], [18], [19], [20], [21], [22], [23],
and [24], other variables are jointly optimized with the UA V
trajectory, e.g., UA V transmit power and user scheduling [14],
[15], [16], [17], bandwidth allocation for users [18], UA V-user
association [19], UA V transmit beamforming [20], [21], [22],
[23], and ofﬂoading task size [24]. These above works were
dedicated to the case with a single UA V and thus exempted
from the UA V collision-avoidance constraint. On the contrary,
investigations [25] and [26] focused on a multi-UA V-assisted
ISAC network, where the trajectory of individual UA Vs and
their association with users are jointly optimized subject to the
minimum collision avoidance distance. In addition, to circum-
vent the high computational complexity and poor adaptability
of conventional optimization methods, several intelligent UA V-
aided ISAC schemes were developed in [27], [28], [29], [30],
[31], [32], and [33].
The inherent limitation of the ﬁrst paradigm is not being
applicable to terrestrial ISAC oriented towards LAE, where
authorized UA Vs (as communication users) with missions
(e.g., cargo delivery) and unauthorized targets (as sensing
targets) are located at low altitudes in the 3D space. Instead,
the second paradigm, which focuses on the use of GBS
to provide aircraft with ISAC services, aligns better with
LAE-oriented ISAC. Currently, there are few studies on this
paradigm [34], [35]. In particular, the authors of [34] consid-
ered a system with one GBS and multiple UA Vs, where a novel
dual identity association-based ISAC approach was designed
to enable fast and accurate beamforming towards different
UA Vs. Unlike [34], the authors of [35] studied a networked
ISAC system, where multiple GBSs cooperatively transmit
uniﬁed ISAC signals to communicate with multiple authorized
UA Vs and concurrently detect unauthorized targets. In prior
works, the unauthorized target is presumed to be static, and the
alternating algorithms that focus on instantaneous optimization
problems are adopted to optimize different groups of variables.
In practical LAE-oriented ISAC systems, however, (i) the
locations of unauthorized targets are highly dynamic; (ii) the
channel state information (CSI) is time-correlated since
the next locations of the target and UA Vs depend on their
current locations; and (iii) the beamforming and trajectory
are jointly optimized subject to UA Vs’ ﬂight missions that
last for a long period. As a result, the LAE-oriented ISAC
problem is typically a long-term optimization problem , in
which all variables should be jointly optimized with respect
to the average system performance during the ﬂight mission.
Such a problem can be transformed and solved under
the Markov decision process (MDP) model, in which an
agent continuously optimizes its decisions towards the given
long-term objective. Generally, an efﬁcient solution for MDP
can be derived through dynamic programming algorithms, if
the accurate state transition (e.g., the CSI transition) of the
system is available [36]. However, in practical LAE-oriented
ISAC systems, the mobility model of the target is difﬁcult to
obtain, in the sense that the state transition of the system is
unknown. Fortunately, model-free deep reinforcement learning
(DRL) excels at ﬁnding an efﬁcient strategy for MDP in
unknown environments, through a large number of trial-and-
error interactions and reward-decision iterations [37]. In this
regard, DRL is a promising candidate for solving long-term
optimization problems in LAE oriented-ISAC systems . So far,
DRL has shown its powerful capability in solving a wide range
of sequential decision-making problems, e.g., robot control,
game playing, and wireless communications [38]. To the best
of our knowledge, DRL has not been explored yet in designing
LAE-oriented ISAC schemes.
B. Contributions
In this paper, we investigate an LAE-oriented ISAC system
with the objective of maximizing the expected communication
sum-rate of all UA Vs over a given ﬂight period, by jointly
optimizing the GBS’s beamforming and authorized UA Vs’
trajectories. In addition, the constraints, including the average
sensing signal-to-noise ratio (SNR) requirement for monitor-
ing the mobile target, the UA Vs’ ﬂight missions, the UA V
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 353
collision avoidance, and the GBS’s maximum transmit power,
are considered. Overall, the main contributions of this paper
are summarized below:
1) A problem is formulated as a speciﬁc MDP model
termed episode task [36] to jointly optimize the GBS’s
beamforming and UA Vs’ trajectories, where each ﬂight
period is considered as an episode and the ﬂight mission
corresponds to the episode task. To ﬁnd an efﬁcient solu-
tion, we propose an ISAC scheme capable of supporting
LAE, referred to as Deep LAE-ISAC (DeepLSC), by
exploiting the DRL technique. The underpinning algo-
rithm in DeepLSC is deep deterministic policy gradient
(DDPG) [39], since the formulated problem involves
continuous control variables. The salient advantages of
DeepLSC are that it (i) does not require the prior
mobility information of the target and (ii) well caters the
long-term optimization objective of the LAE-oriented
ISAC system.
2) A new action selection policy, termed constrained
noise-exploration policy, is developed for DeepLSC
to guarantee the ﬂight mission and maximum power
constraints. The gist is to (i) introduce a scaling fac-
tor to reﬁne the beamforming from the conventional
noise-exploration policy [39] and (ii) decide whether to
follow the trajectory decision of the conventional noise-
exploration policy or choose straight ﬂight based on the
real-time locations of UA Vs. In addition, we judiciously
design a reward function for action evaluation, which
incorporates the communication sum-rate, average sens-
ing SNR requirement, and collision avoidance into the
learning process.
3) A new hierarchical experience replay mechanism is
proposed for DeepLSC to train the deep neural network
(DNN). Speciﬁcally, in the traditional experience replay
mechanism [40], since different experiences generated
within a speciﬁc episode are collected and utilized
in a separate manner, they cannot be guaranteed to
appear together during training. DeepLSC, however, is
tailored for episode tasks. To efﬁciently learn from the
episode task, the hierarchical experience replay mech-
anism employs the experience sets, each containing all
experiences within an episode, to jointly train the DNN.
4) We devise a symmetric experience augmentation mech-
anism to promote the convergence speed of DeepLSC.
To be speciﬁc, DeepLSC is an online learning scheme,
in the sense that the agent (i.e., the GBS) needs a lot of
trial and error with the environment to generate sufﬁcient
experiences for training. Consequently, an efﬁcient joint
beamforming and trajectory policy takes a long time to
learn. To circumvent this issue, the symmetric experi-
ence replay mechanism generates more new experience
sets by simultaneously permuting the indexes of all
variables, based on a prior experience set.
5) Extensive experimental results show that DeepLSC out-
performs various schemes including the DeepLSC-CNE
(i.e., DeepLSC with the conventional noise-exploration
policy [39]), DeepLSC-CER (i.e., DeepLSC with the
conventional experience replay mechanism [40]), and
TABLE I
MAIN NOTATIONS OF THIS PAPER
AC2 (i.e., the actor-critic algorithm [36] with the con-
strained noise-exploration policy), in terms of both
communication and sensing performance. Compared
with DeepLSC-w (i.e., DeepLSC without symmet-
ric experience augmentation), DeepLSC converges
faster. Furthermore, under different simulation setups,
DeepLSC is more robust than these baselines.
Notations: Vectors (matrices) are denoted by boldface lower
(upper) case letters, CN×M represents the space of N×M
complex matrices, |·| represents the absolute value, ||·|| 2
represents the 2-norm, E[·] represents the statistical expecta-
tion, while Tr(·), (·)T , and (·)H represent the trace, transpose,
and conjugate transpose, respectively. blueFor reference, we
list the main notations of this paper in TABLE I.
II. S YSTEM MODEL
Consider an LAE-oriented ISAC system shown in Fig. 1,
where one GBS equipped with N transmit/receive-antennas
serves M single-antenna authorized UA Vs for downlink com-
munications and simultaneously detects a low-altitude target
(e.g., unauthorized UA V). The location of the GBS is repre-
sented by the 3D Cartesian coordinate (b, 0) with b = [ˆx, ˆy]
denoting the horizontal coordinate, and the location of the
target is (g,H Tar), wherein g = [˜x, ˜y] andHTar> 0 denote the
horizontal and vertical coordinates, respectively. The UA Vs are
indexed by m∈M ={1, 2,··· , M}, and each UA V m ﬂies
at a pre-assigned altitude Hm with the mission of transporting
cargo from a source to a destination within a given time
duration of ∆T. In other words, the initial and ﬁnal locations
of UA V m are predetermined as (uIm,Hm) and (uFm,Hm),
respectively, wherein uIm = [xIm,y Im] and uFm = [xFm,y Fm].
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

354 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. LAE-oriented ISAC systems.
A. UA V/Target Trajectory Model
We discretize the duration ∆T into T time slots, indexed
by t∈T ={1, 2,··· , T}. The slot duration ∆t = ∆ T/T
is sufﬁciently small, such that the locations of the target and
UA Vs can be assumed as unchanged within each time slot.
1) UA V Flight Model: Within a speciﬁc time period
∆T, the trajectory of UA V m is a (T + 1) -length
sequence, i.e., {(uIm,Hm), (um(t),Hm)|t = 1 , 2,··· , T}
with um(t) ≜ [xm(t), ym(t)]. We assume that UA V m ﬂies
at a constant speed vm. Thus, its ﬂight distance in one time
slot is given as vm∆t, leading to the following constraint:
‖um(t + 1)− um(t)‖2 =vm∆t, ∀m∈M, t∈T . (1)
In addition, the initial and ﬁnal locations of M UA Vs (i.e.,
the ﬂight mission constraints) are given by
um(0) = uIm and um(T ) = uFm,∀m∈M. (2)
To avoid collision among different UA Vs, the following
collision avoidance constraints are enforced:
‖um(t)− ui(t)‖22 + (Hm−Hi)2≥D2min,
∀m,i∈M, m⁄=i, t∈T , (3)
where Dmin denotes the minimum allowed distance between
any two UA Vs. Similarly, each UA V also needs to maintain a
minimum distance from the target to avoid collision, i.e.,
‖um(t)− g(t)‖22 + (Hm−HTar(t))2≥D2min,
∀m∈M, t∈T . (4)
2) Target Mobility Model: For simplify, we assume that the
target moves at a constant speed vTar and its ﬂight distance
within one time slot is vTar∆t. To better model the mobility
of a realistic target, a Gauss-Markov process is introduced to
capture the temporal correlation of the movement direction
[41]. Let φ(t) and ϕ(t) denote the azimuth and elevation
angles at which the target moves at time slot t, respectively.
They are modeled as
{
φ(t) =µaφ(t− 1) + (1−µa)ξa +
√
1−µa2 ˆφ(t),
ϕ(t) =µeϕ(t− 1) + (1−µe)ξe +
√
1−µe2 ˆϕ(t), (5)
where µa∈ [0, 1] and µe∈ [0, 1] are the time correlation coef-
ﬁcients, modulating the degree of temporal dependency. For
example, µa = 0 indicates that the target moves at a fully
random azimuth angle, while µa = 1 indicates that the hori-
zontal movement direction is unchanged. Parameters ξa andξe
are asymptotic means of φ(t) andϕ(t), respectively, ast→∞.
Parameters ˆφ(t) and ˆϕ(t) are independent, uncorrelated, and
stationary Gaussian processes with N (0,σ 2φ) andN (0,σ 2ϕ),
respectively, whereinσφ andσϕ correspond to the asymptotic
standard deviations.
Hence, given φ(t) and ϕ(t), the location of the target at
time slot t + 1 can be obtained as{
g(t + 1) = g(t) +vTar∆tcos (ϕ(t)) [cos (φ(t)), sin (φ(t))],
HTar(t + 1) =HTar(t) +vTar∆tsin (ϕ(t)).
(6)
B. Channel Model
Denote hs(t)∈ CN×1 by the channel vector between the
GBS and the target at time slot t. The bidirectional channel
matrix that the signal experiences from forward transmission to
echo can be represented as Hs(t) = hs(t)hTs (t)∈ CN×N . Fur-
thermore, let Hc(t) = [ h1(t), h2(t),··· , hM(t)]∈ CN×M
denote the channel matrix between the GBS and all UA Vs
at time slot t, wherein hm(t)∈ CN×1 is the channel vector
between the GBS and UA V m.
Due to the relatively high altitude of the target and UA Vs,
there generally exists a strong line-of-light (LoS) link between
the GBS and them. As such, the air-ground communica-
tion links are dominated by the LoS channel. For example,
hm(t),∀m∈M is represented as
hm(t) =
√
ωm(t)c (ψm(t)), (7)
where
ωm(t) =L0
D0
(‖b− um(t)‖22 +H2m)ςm
is the path loss with L0 as the path loss constant at reference
distance D0, and ςm as the path loss exponent. Furthermore,
c (ψm(t)) =
[
1,e2πdλ cosψm(t),··· ,e2πdλ (N−1) cosψm(t)]T is
the steering vector with ψm(t) being the angle of departure
(AoD) at the GBS, given by
ψm(t) = arccos Hm√
‖b− um(t)‖22 +H2m
. (8)
A similar channel model is adopted for hs(t).
C. Signal Model
In each time slot t, the transmit signal of the GBS is a
weighted sum of communication symbols and radar probing
signals [4], which is expressed as
x(t) = Wc(t)vc(t) + Ws(t)vs(t), (9)
where vc(t)∈ CM×1 is the communication symbol with
E{vc(t)vHc (t)} = IM , vs(t)∈ CN×1 is the radar probing
signal with E{vs(t)vHs (t)} = IN , Wc(t)∈ CN×M is the
communication precoding matrix, and Ws(t)∈ CN×N is the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 355
radar precoding matrix. In addition, vc(t) and vs(t) are sta-
tistically independent, leading to E(vc(t)vHs (t)) = 0. Denote
W(t)≜ [Wc(t), Ws(t)] and v(t)≜
[
vTc (t), vTs (t)]T . Thus, we
have x(t) = W(t)v(t), and the power constraint is given by
Tr
(
WHc (t)Wc(t)) + Tr(WHs (t)Ws(t))≤ Pmax,∀t∈T .
(10)
1) Communication Model: With the transmit signal x(t),
the received signal at UA V m is expressed as ym(t) =
hTm(t)x(t)+nm(t), where nm(t)∼CN (0,σ 2m) is the additive
white Gaussian noise (AWGN), and σ2m is the noise power. As
a result, the communication signal-to-interference-and-noise
ratio (SINR) at UA V m is given by
SINRm(t) =
⏐⏐hTm(t)wm(t)⏐⏐2
N+M∑
k=1,k⁄=m
|hTm(t)wk(t)|2 +σ2m
, (11)
where wm is the m-th column of W. Accordingly, the sum-rate
of all UA Vs can be calculated by
Rtotal(t) =
M∑
m=1
log2 (1 + SINRm(t)). (12)
D. Sensing Model
As shown in Fig. 1, the radar probing signal is reﬂected by
the target to GBS via the direct and reﬂected/refracted links.
Thus, the echo signal from the target to GBS is expressed as
ys(t) = Hs(t)x(t) +nB(t), wherein nB(t)∼CN (0N, σ2bIN)
is the AWGN, and σ2b is the noise power. Furthermore, the
sensing SNR of the target is given by
SNRTar(t) =
E
{
|Hs(t)W(t)v(t)|2
}
σ2b
= Tr
(
WH(t)HHs (t)Hs(t)W(t))
σ2b . (13)
III. P ROBLEM FORMULATION AND TRANSFORMATION
This section formulates the joint beamforming and trajec-
tory optimization problem as a constrained sequential decision
problem. Then, it is transformed to an unconstrained problem
with a judiciously designed reward function.
A. Problem F ormulation
Our objective is to maximize the expected sum-rate of all
UA Vs over T time slots while satisfying the sensing SNR
requirement, ﬂight mission, collision avoidance, and maximum
transmit power constraints. The communication beamforming
Wc(t), sensing beamforming Ws(t), and trajectory um(t) of
each UA V are jointly optimized. Mathematically, this opti-
mization problem is formulated as
max
Wc(t), Ws(t), um(t)
E
[ T∑
t=1
Rtotal(t)
]
(14a)
s.t. (1), (2), (3), (4), (6), (14b)
E
[
1
T
T∑
t=1
SNRTar(t)
]
≥ Γmin, (14c)
Tr
(
WHc (t)Wc(t)) + Tr(WHs (t)Ws(t))
≤ Pmax,∀t∈T , (14d)
with the expectation in (14a) taken over varying target mobil-
ity, which is unknown to the GBS. Besides, constraint (14b)
speciﬁes the ﬂight constraints of the target and UA Vs; con-
straint (14c) guarantees the average SNR requirement Γmin for
sensing the target [3]; and constraint (14d) limits the transmit
power of the GBS to Pmax.
Typically, problem (14) is a sequential decision-making
problem, which can be transformed and solved under the
MDP model [36]. This corresponds to one particular MDP
form, referred to as episode task [36], where the task ends
in a terminal status (i.e., the ﬁnal location of the UA V)
that separates the agent-environment interactions into episodes
with each containing T time slots. Different episodes are
independent of each other, and a new episode will start from
the starting status (i.e., the initial location of the UA V) after
each episode ends. Besides, within each episode, the agent has
to satisfy the preset constraints (14b)–(14d). Thus, problem
(14) is actually a constrained episode task . Generally, an
efﬁcient solution that can handle this problem is hard to derive
[36], which therefore motivates us to transform problem (14)
into an unconstrained MDP problem.
B. Unconstrained MDP Transformation
We deﬁne the basic MDP elements, including agent,
environment, action, state, transition probability, and reward
function, as follows.
1) Agent and Environment O: The GBS is considered as
the agent, while the target, UA Vs, and wireless channels are
treated as the environment. In each time slot, the GBS ﬁrst
decides an efﬁcient joint beamforming and trajectory strategy.
Afterward, it performs the communication beamforming to
provide data transmission and navigation for all UA Vs, while
monitoring the mobile target via the sensing beamforming.
2) Action Space A: The action space A is composed
of all possible actions that could be potentially executed
by the agent. In the light of (14), the agent needs to
decide three types of sub-actions, including the communica-
tion beamforming Wc(t), the sensing beamforming Ws(t),
and all UA Vs’ movement directions au(t), in each time
slot. Speciﬁcally, the sub-action au(t) is represented as
[au,1(t), au,2(t), ··· , au,M(t)], where au,m(t) is the move-
ment direction of UA V m at time slot t. With au,m(t), the
horizontal location of UA Vm at time slott+1 becomes um(t+
1) = [xm(t)+vm∆t cos(au,m(t)), ym(t)+vm∆t sin(au,m(t))].
In Wc(t), Ws(t), and au(t), each element is a continuous
variable to be optimized by the agent. Overall, the action
of the agent at time slot t can be denoted by A(t) =
(Wc(t), Ws(t), au(t)).
3) State Space S: The state spaceS is a set of all possible
states, each of which contains enough useful information for
decision-making. To be speciﬁc, at time slot t, the observable
state S(t) is determined by the communication CSI Hc(t),
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

356 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
the sensing CSI Hs(t), and all UA Vs’ locations U(t) =
[u1(t), u2(t),··· , uM(t)], which can be represented as
S(t) =
[
Hc(t), Hs(t), U(t)
]
. (15)
4) Transition Probabilities P: The transition probability,
denoted by p (S(t + 1) = S′|S(t) = S, A(t) = A), describes
the probability that the state transits from S to S′ after action
A is conducted [36]. Since the mobility information of the
target is not available, the transition probability p (S′|S, A) is
unknown. As a result, problem (14) is a partially observable
MDP problem.
5) Reward Function R: The reward function, denoted by
r(t + 1) = R(S(t), A(t)), presents the award or penalty to
evaluate how good A(t) is under S(t). In the design of the
reward function, we address constraints (3), (4), and (14c),
apart from the optimization objective (14a). In Section IV-B,
we will detail how to guarantee constraints (2) and (14d) from
the perspective of action selection.
• First, considering only the optimization objective of max-
imizing the sum-rate of all UA Vs, the reward is given by
r(t + 1) = Rtotal(t).
• Second, the agent needs to be aware of its unwise
decisions, i.e., the collision avoidance constraint (3) or
(4) cannot be met. Thus, when a collision occurs at time
slot t, the corresponding reward r(t + 1) should be a
penalty−δ1, wherein δ1 > 0 is the penalty coefﬁcient
corresponding to the collision avoidance constraint, bal-
ancing the utility and cost [38]. The larger δ1 is, the more
the agent attaches importance to the given constraint.
• Third, according to constraint (14c), the agent needs
to satisfy the preset sensing SNR requirement Γmin. In
this regard, if the average sensing SNR over the whole
ﬂight period (i.e., episode) 1 is less than Γmin, a penalty
−δ2
(
Γmin−∑Tt=1SNRTar(t)/T) should be added to
r(t + 1), wherein δ2 > 0 is the penalty coefﬁcient
corresponding to the sensing SNR requirement constraint.
As such, the agent can be encouraged to optimize its
strategy, so as to meet the average SNR requirement for
sensing the target in subsequent episodes.
Overall, the reward function of the agent is designed as
(16), shown at the bottom of the page. Note that since∑T
t=1SNRTar(t)/T is not revealed until the end of each
episode, the rewards {r(t + 1)|t = 1, 2,··· , T} are only
available at the agent in time slot t =T .
Thus far, we have reformulated problem (14) as an uncon-
strained MDP problem. At each time slot, given the system
1This paper uses the terms “ﬂight period” and “episode” interchangeably.
state S(t), the agent makes an decision A(t) to interact
with the environment by trial-and-error according to a policy
π(A(t)|S(t)). Afterward, the environment feeds back a reward
r(t + 1) to the agent, and enters a new state S(t + 1) with
probability p (S′|S, A). Over the lifetime, the agent aims to
search for an optimal policy π∗ (i.e., the optimal joint GBS’s
beamforming and UA Vs’ trajectories policy) to maximize the
cumulative reward G(t) = ∑Tl=tr(l + 1) [36]. Furthermore,
the action-value that reﬂects the expected cumulative reward
at state S(t) given A(t) is chosen can be deﬁned as
Qπ (S(t), A(t)) = Eπ [G(t)|S(t), A(t)]. (17)
In the above MDP problem, if the channel model is
accurately known, the state transition probability p (S′|S, A)
is easy to obtain. At this time, this MDP problem can be
well tackled by dynamic programming. However, the mobility
model of the target is unavailable at the GBS, which motivates
the use of model-free DRL techniques.
IV. D EEP LSC S CHEME
In this section, we present DeepLSC, a DRL-enabled ISAC
scheme, to solve the formulated MDP problem. The under-
pinning algorithm in DeepLSC is DDPG [39], and the major
reasons why we favor DDPG are as follows: (i) Problem
(14) involves continuous control variables, whereas value-
based DRL methods, e.g., deep Q-network (DQN) [37], are
limited to discrete control problems. (ii) Conventional policy-
based approaches, e.g., policy gradient [42], are capable of
solving continuous control issues, but they suffer from unstable
learning and slow convergence. DDPG, which integrates the
advantages of value-based and policy-based methods, can
effectively circumvent the above challenges. Fig. 2 shows the
DeepLSC framework, and the details are elaborated below.
A. Actor-Critic Architecture
There are two types of DNNs in DeepLSC, referred to as
actor and critic. Each of them consists of two DNNs with the
same structure but different parameters, i.e., the eval-actor with
parameter Θa, the target-actor with parameter Θ−a , the eval-
critic with parameter Θc, and the target-critic with parameter
Θ−c . As shown in Fig. 2, all DNNs share the same structure,
i.e., one input layer, one gated recurrent unit (GRU) layer [43],
one fully connected (FC) layer [44], and one output layer, but
their roles are different.
r(t + 1) =



−δ1−δ2
(
Γmin− 1T
T∑
t=1
SNRTar(t)
)
, if (3) or (4) is not met and (14c) is not met ,
−δ1, if (3) or (4) is not met but (14c) is met ,
Rtotal(t)−δ2
(
Γmin− 1T
T∑
t=1
SNRTar(t)
)
, if (3) and (4) are met but (14c) is not met ,
Rtotal(t), if (3), (4), and (14c) are all met .
(16)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 357
Fig. 2. DeepLSC framework, including the execution phase and the training phase. During the execution phase, based on S(t), the eval-actor outputs the
temporary joint beamforming and trajectory decision πa(S(t), Θa), which is reﬁned by the constrained noise-exploration policy. During the training phase,
some experience sets sampled from the experience buffer are augmented to form the mini-batch for training the actor-critic architecture.
1) Eval-Actor: At each time slot, the eval-actor makes
a temporary joint beamforming and trajectory decision
πa (S(t); Θa) based on the state S(t). Speciﬁcally, since the
DNN cannot process complex numbers, we divide Hc(t) and
Hs(t) into the corresponding real and imaginary parts, and
concatenate them together with U(t). After obtaining the
preprocessed state S(t), the input layer delivers it into the
GRU layer. Afterward, the GRU layer extracts the underlying
temporal correlation from the input sequence and imports it
into the FC layer for analysis. 2 Since DNNs cannot generate
complex numbers, it is not feasible to directly get a matrix with
sizeN×M as Wc(t) and a matrix with size N×N as Ws(t).
Thus, after receiving the processed information from the FC
layer, the output layer generatesπa (S(t); Θa) containing three
vectors, wherein the ﬁrst vector with size 2NM is related
to the temporary communication beamforming, the second
vector with size 2N2 is related to the temporary sensing
beamforming, and the last vector with size M is the tem-
porary trajectory decision. In particular, with the ﬁrst vector
in πa (S(t); Θa), the temporary communication beamforming
can be generated via element-wise concatenation, i.e., the
ﬁrst NM elements are treated as the real parts of individual
elements in the temporary communication beamforming and
the remaining elements are the corresponding imaginary parts.
The temporary sensing beamforming can also be generated in
a similar way. In Section IV-B, a new action selection policy
will be designed to determine the real joint beamforming and
trajectory decision A(t).
2) Eval-Critic: After acquiring the action A(t) from the
eval-actor, the agent feeds it together with S(t) to the eval-
critic for evaluating the action-value Q(S(t), A(t); Θc). To
cater to the input of the DNN, the eval-critic preprocesses
each element in both S(t) and A(t) in a similar way as the
eval-actor. Then, the evaluated action-value will be used to
2Our previous work [38] has demonstrated the efﬁciency of GRU in
addressing the problem with complex temporal correlations in wireless
networks.
compute the action gradient, i.e., ∇A(t)Q
(
S(t), A(t); Θc
)
, so
as to train the eval-actor as detailed in Section IV-C.
3) Target-Actor and Target-Critic: The role of both the
target-actor and the target-critic is to compute the target value
ofQ(S(t), A(t); Θc) when the eval-critic is trained. To further
enhance the stability of the algorithm, the parameters of the
eval-actor and the eval-critic are fully updated, whereas the
parameters of the target-actor and the target-critic are partially
updated via the soft-update approach in Section IV-E.
B. Constrained Noise-Exploration Policy
Given the optimization objective (14), the eval-actor aims to
ﬁnd the optimal policy of joint beamforming and trajectoryπ∗a .
Recall that in Section III-B, constraints (3), (4), and (14c) have
been considered from the perspective of reward design. We
now illustrate how to guarantee the maximum power constraint
(14d) and the ﬂight mission constraint (2) from the perspective
of action selection. Speciﬁcally, according to constraints (14d)
and (2), the signal power used for communication and sensing
cannot exceed the preset maximum valuePmax, and the trajec-
tory should ensure all UA Vs to complete their ﬂight missions
within each episode. Given the temporary joint beamforming
and trajectory decisionπa (S(t); Θa) from the eval-actor based
on S(t), the conventional noise-exploration policy in DDPG
[39] generates a reﬁned decision by adding randomness, i.e.,
(ac(t), as(t), au(t)) =πa (S(t); Θa) + (dc(t), ds(t), du(t)),
(18)
where ac(t) and as(t) are vectors with size 2NM and 2N2,
respectively. Vector di(t),∀i∈{c, s, u}, has the same size as
ai(t), each element of which is Gaussian distributed with zero
mean and varianceσ2i (t). By doing so, the agent is encouraged
to explore random actions for better solutions. Generally, too
much exploration is unnecessary once an efﬁcient solution
is learned. Hence, we introduce a decay factor κ∈ (0, 1) to
reduce σ2i (t) over time. Denote the initial variances by σ2i,init,
then σ2i (t) at time slot t can be represented as σ2i,initκt.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

358 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
The conventional noise-exploration policy, however, only
improves the exploration capability of the agent, while ignor-
ing constraints (14d) and (2). To cope with this issue, we
develop a new action selection policy for DeepLSC, referred
to as constrained noise-exploration policy . The gist is to (i)
introduce a scaling factor to reﬁne the beamforming decided
by the conventional noise-exploration policy, so as to meet
constraint (14d), and (ii) decide whether to use the conven-
tional noise-exploration policy based on the real-time location
of each UA V , so as to satisfy constraint (2). The details are
elaborated below.
1) Decision-Making of Communication and Sensing Beam-
forming: As a ﬁrst step, with ac(t) and as(t), two matrices
Ac(t)∈ CN×M and As(t)∈ CN×N can be generated via
element-wise concatenation, i.e., the ﬁrst NM (N2) elements
of ac(t) (as(t)) are treated as the real parts of individual
elements in Ac(t) (As(t)) and the remaining elements are
the corresponding imaginary parts. Thereafter, to obtain the
communication beamforming Wc(t) and the sensing beam-
forming Ws(t) that satisfy the preset power constraint (14d),
a scaling factor, deﬁned as ϵ = Pmax/
(
Tr
(
AHc (t)Ac(t)) +
Tr
(
AHs (t)As(t)), is introduced to reﬁne Ac(t) and As(t) as
follows:
Wc(t) =√ϵAc(t), Ws(t) =√ϵAs(t). (19)
2) Decision-Making of UA Vs’ Trajectories:
Within each episode, all UA Vs’ trajectories
{au(t) = [ au,1(t), au,2(t),··· , a u,M(t)]|t∈T} decided
by the agent should fulﬁll the preset ﬂight mission. For this
purpose, the constrained noise-exploration policy that decides
au,m(t) limits the movement directions of UA V m in the
last T−t− 1 time slots within each episode: at time slot
t, if the minimum required number of time slots from the
current location to reach the desired location is not less than
T − t− 1 3, UA V m has to ﬂy in a straight line toward
the desired location uFm, i.e., au,m(t) = “straight ﬂight”.
Within other time slots, the movement decision au,m(t)
can be directly determined through the conventional noise-
exploration policy, in the sense that the agent is not subject
to constraint (2) and thus can derive more efﬁcient movement
directions for UA Vs towards other optimization objectives.
Overall, the movement decision of UA V m at time slot t is
given as follows:
au,m(t)
=
{
au,m(t), if⌈‖um(t)−uFm‖2vm∆t ⌉<T −t− 1,
straight ﬂight, otherwise,
(20)
where⌈x⌉ represents the smallest integer not less than x.
3Intuitively, to complete the ﬂight mission, UA V m only needs to ﬂy in a
straight line towards the desired location uFm when the number of its available
time slots is equal to the minimum required number of time slots. However,
there are some special cases. For example, the movement distance of UA V m
in each time slot is 1 m, the number of time slots available to UA V m at time
slot t is 11, and at least 10 time slots are required to reach the desired location
uFu,m. If UA V m moves in the opposite direction of the desired location at
time slot t, the number of time slots available to UA V m at time slot t + 1
will be 10 but at this time at least 11 time slots will be required to reach the
desired location. Consequently, UA Vm will never complete the ﬂight mission
in the subsequent time slots. Therefore, in (20), we relax T −t toT −t − 1.
C. Hierarchical Experience Replay
Since DeepLSC is developed for episode tasks, all expe-
riences from different time slots within each episode should
be jointly used to train both the eval-actor and the eval-critic.
However, in the conventional experience replay mechanism of
DDPG [40], the experiences generated in different time slots
are separately gathered and utilized. In other words, during
training, the experiences from different time slots within a
speciﬁc episode cannot be guaranteed to appear in full. Conse-
quently, the agent fails to learn an efﬁcient joint beamforming
and trajectory strategy in LAE-oriented ISAC systems. To ﬁll
this gap, a new hierarchical experience replay mechanism is
designed for DeepLSC, which makes use of experience sets
each containing all experiences generated within each episode
to train the eval-actor and the eval-critic.
As a ﬁrst step, to store and reuse historical experiences, a
ﬁrst-input-ﬁrst-output (FIFO) experience bufferD with size D
is used. As mentioned in Section III-B, within each episode,
the rewards {r(t + 1)|t = 1 , 2,··· ,T} are not available
until time slot T. Thus, in time slot T of each episode, after
calculating the reward r(t + 1) via (16), the agent collects the
experiencee(t) in the form of (S(t), A(t),r (t + 1), S(t + 1)),
where A(t) = [ Wc(t), Ws(t), au(t)]. With all experiences
generated over the whole episode, an experience set E =
{e(t)|t = 1, 2,··· , T} is formed and stored in D. During
training, Ne experience sets are randomly sampled from D
to form the mini-batch B. Afterward, the loss function for
training the eval-critic is given as
L(Θc) = 1Ne ∑E⊂B
( T∑
t=1
(
z(t + 1)−Q (S(t), A(t); Θc)
)2
)
,
(21)
where z(t + 1) = r(t + 1) + Q
(
S(t + 1),π−a (S(t +
1); Θ−a); Θ−c) is the target value related to the eval-actor,
and π−a is the policy of the target-actor. Furthermore, by
performing the stochastic gradient descent (SGD) algorithm
[36], the parameter Θc is updated as follows:
Θc←Θc−αc∇ΘcL(Θc), (22)
where αc is the learning rate of Θc. On the other hand, the
parameter Θa of the eval-actor can be updated via the sampled
policy gradient algorithm [39], i.e.,
Θa←Θa−αa
1
Ne
∑
E⊂B
( T∑
t=1
(
∇A(t)Q
(
S(t), A(t); Θc
)
×∇Θaπa
(
S(t); Θa
)))
, (23)
with αa being the learning rate of Θa.
D. Symmetric Experience Augmentation
In DeepLSC, to gain enough experiences for DNN training,
the agent needs to perform a lot of trial and error with the
environment. Consequently, an efﬁcient joint beamforming
and trajectory strategy usually takes a long time to derive.
If the experience set {(S(t), A(t),r (t + 1), S(t + 1))|t =
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 359
1, 2,··· , T} can be generated based on existing experience
sets, the experience buffer D will effectuate experience aug-
mentation and greatly boost the convergence speed. Actually,
in problem (14), the index of each UA V is artiﬁcially speciﬁed.
Thus, in terms of the system performance, if the indices of
different UA Vs are permuted, the new optimization problem
is equivalent to the original problem [45]. For example, when
M = 2 and N = 2, the communication CSI is given as
Hc(t) =
[ h1,1(t) h1,2(t)
h2,1(t) h2,2(t)
]
. (24)
where hn,m is the channel component of antenna n to UA Vm.
If we permute the indexes of UA V 1 and UA V 2, the commu-
nication CSI will be transformed into
Hc(t) =
[
h1,2(t) h1,1(t)
h2,2(t) h2,1(t)
]
. (25)
At this time, if the indexes of UA V 1 and UA V 2 in the com-
munication beamforming Wc(t), the sensing beamforming
Ws(t), the UA Vs’ movement decisionsau(t), and the sensing
CSI Hs(t) are synchronously permuted, the new optimization
problem will be equivalent to the original problem.
Inspired by this, we propose the symmetric experi-
ence augmentation mechanism , and the main idea is
to simultaneously exchange the indexes of all vari-
ables to generate more new experience sets. Speciﬁcally,
denote Υ = {{υ1, υ2, υ3,··· , υM}, {υ2, υ1, υ3,··· ,
υM},··· , {υM, υM−1, υM−2,··· , υ1}} by the symmetric
group of ﬁnite integer set F = {υ1, υ2,··· , υM}, where
group elements are bijection ofF to itself. Let Ωυi denote the
permutation ofυi. Then the permutation of individual elements
inF can be represented as
Ω =
( υ1 υ2 ··· υM
Ωυ1 Ωυ2 ··· ΩυM
)
, (26)
where the ﬁrst row is the elements ofF, and the second row is
the corresponding permutation under Ω. In the above example,
the permutation is given as Ω =
(1 2
2 1
)
. Consider a system
with M UA Vs. Under all possible permutationsΩ, there will be
a total of M! group elements in Υ. Besides, to distinguish the
variables before and after the permutation, we superscript the
permuted communication beamforming, sensing beamforming,
UA Vs’ movement decisions, communication CSI, and sensing
CSI by Ω as WΩc (t), WΩs (t), aΩu (t), HΩc (t), and HΩs (t),
respectively.
Therefore, the experience sets used for DeepLSC training
can be signiﬁcantly enriched through various permuta-
tions. In particular, given a prior experience set
{
e(i) =
(S(i), A(i),r (i + 1), S(i + 1))|i = 1 , 2,··· , T
}
that is
acquired via the agent-and-environment interaction, M!− 1
new experience sets, i.e.,
{{
eΩ(i)|i = 1, 2,··· ,T} |Ω∈
Υ}, can be generated based on the symmetric group Υ. In
each experience set eΩ(i), the elements are given as



SΩ(i) = [HΩc (i), HΩs (i), UΩ(i)]
AΩ(i) = [WΩc (i), WΩs (i), aΩu (i)],
rΩ(i + 1) =r(i + 1),
SΩ(i + 1) = [HΩc (i + 1), HΩs (i + 1), UΩ(i + 1)].
(27)
The symmetric mapping, despite increasing the number
of available experience sets, may lead to strong correlation
among experience sets [36]. The consequence is that DeepLSC
will fall into overﬁtting and converge to a sub-optimal joint
beamforming and trajectory strategy. Actually, at the beginning
of training, it is difﬁcult to get enough experience sets. In
this case, it is beneﬁcial to augment existing experience sets
based on the symmetric group Υ. However, as the number
of episodes increases, the experience sets from agent-and-
environment interactions become miscellaneous. As a result,
it is no longer necessary to use the symmetric mapping to
enrich the available experience sets. Hence, we introduce a
dynamic augmentation factor ζ∈ (0, 1) to adjust the number
of augmented experience sets as follows:
Λ(ω) =⌊(M!− 1)ζω⌋, (28)
where⌊x⌋ represents the largest integer less than x, and ω
is the number of training times. During each training, Ne
experience sets, i.e., {{e(i,j ) | i = 1 , 2,··· ,T} |j =
1, 2,··· ,N e},, are sampled from D in random, and each of
which is augmented based on Λ(ω) random group elements
(i.e., permutations Ω) of the symmetric group Υ. Thereafter,
all augmented experience sets are merged with Ne original
experience sets to form the mini-batch B for training the eval-
actor and eval-critic.
E. Soft-Update for Target-Actor and Target-Critic
The parameters Θ−a and Θ−c of the target-actor and the
target-critic are updated based on the parameters Θa and Θc
of the eval-actor and the eval-critic. A simple approach is to
update the parameters of the target-actor and the target-critic
by Θ−a←Θa and Θ−c←Θc. However, this approach is not
suitable for the continuous control task, since it may lead to
large prediction errors of the target-actor and the target-critic
[39]. To circumvent this issue, the soft-update approach was
proposed in [36], which updates both Θ−a and Θ−c as follows:
Θ−a ←χaΘa + (1−χa)Θ−a , Θ−c ←χcΘc + (1−χc)Θ−c ,
(29)
where χa∈ [0, 1] and χc∈ [0, 1] are the update factors of the
target-actor and the target-critic, respectively. To be speciﬁc,
the soft-update enables the target-actor and the target-critic to
maintain a certain continuity during the update process, so as
to better adapt to the continuous control task.
F . Detailed Operations of DeepLSC
Thus far, we have presented the main elements of the
DeepLSC scheme, and Algorithm 1 provides the correspond-
ing pseudocode. Overall, the operations of DeepLSC include:
(i) decide the temporary joint beamforming and trajectory
decisionπa (S(t); Θa) via the eval-actor with the current state
S(t) (lines 7 ∼ 8); (ii) decide ac(t), as(t), and au(t) via
(18) (lines 9∼ 10); (iii) determine the communication beam-
forming Wc(t) and the sensing beamforming Ws(t) via (19),
and the movement directions au(t) via (20) (lines 11∼ 13);
(iv) obtain the next state S(t + 1) according to (15) (line 14);
(v) calculate the reward {r(t + 1)|t = 1, 2,··· , T} via (16)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

360 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Algorithm 1 DeepLSC Scheme
1: Initialize N, M, T, b, uIm, uFm,{Hm|m∈M} , vm, Γmin.
2: Initialize g(0), HTar(0), δ1, δ2, σmin, κ, αa, αc, Υ, Ω.
3: Initialize ω = 0,{σ2i,init|i = c, s, u}, ζ,E, D, Ne, χa, χc.
4: Initialize Θa, Θ−a , Θc, Θ−c .
5: for episode = 1, 2,··· do
6: fort = 1, 2,··· ,T do
7: Input S(t) into the eval-actor;
8: Make the temporary decision πa (S(t); Θa);
9: Generate ac(t), as(t), and au(t) via (18);
10: Update σ2i (t) to σ2i,initκt;
11: Obtain Wc(t) and Ws(t) via (19);
12: Reﬁne au(t) via (20);
13: Take A(t) to interact with the environment;
14: Obtain S(t + 1) via (15).
15: end for
16: Compute{r(t + 1)|t = 1, 2,··· , T} via (16);
17: Form{e(t)|t = 1, 2,··· , T} to store into D;
18: Randomly sample Ne experience sets from D;
19: Augment each experience set with Λ(ω) via (27);
20: Set ω← episode and update Λ(ω);
21: Merge sampled and augmented experiences to form B;
22: Calculate L(Θc) via (21);
23: Train Θa via (22) and Θc via (23);
24: Update Θ−a and Θ−c via (29).
25: end for
at the end of each episode (line 16); (vi) form the experience
set{e(t) = (S(t), a(t), r(t+1), S(t+1))|t = 1, 2,··· , T}
and store it in the experience bufferD (line 17); (vii) randomly
sampleNe experience sets fromD and augment each of them
with Λ(ω) via (27) (lines 18∼ 20); (viii) integrate the sampled
and augmented experience sets to form the mini-batch B for
training the eval-actor and the eval-critic via (22) and (23),
respectively (lines 21∼ 23); and (ix) update the parameters
of both the target-actor and the target-critic via (29) (line 14).
V. C OMPLEXITY AND IMPLEMENTATION ANALYSIS
In this section, we ﬁrst analyze the computational complex-
ity of DeepLSC. Then, detailed implementation procedures in
practical systems are presented.
A. Computational Complexity Analysis
As shown in Fig. 2, the actor-critic architecture serves
as the DNN model of DeepLSC, where both the actor and
the critic comprise one input layer, one GRU layer, one
FC layer, and one output layer. According to [43], (i) the
computational complexity of GRU for forward-propagation is
given as O(K1K22), wherein K1 and K2 are the number of
neurons in the input layer and the GRU layer, respectively; and
(ii) the computational complexity for back-propagation is
given as O(NTrainK1K22), with NTrain being the number of
experiences for training, respectively. Besides, in the light of
[44], (i) the computational complexity of FC for forward-
propagation is given asO(K2K3), wherein K3 is the number
of neurons in the FC layer; and (ii) the computational complex-
ity for back-propagation is given as O(NTrainK3K4), with K4
being the number of neurons in the output layer. On the other
hand, as demonstrated in [44], the computational complexity
of the output layer and the input layer needs to be considered
in the forward and backward propagation stages, respectively;
and their computational complexity is calculated in the same
way as the FC layer. Thus, given the DNN model in Fig. 2, the
total computational complexity for forward-propagation and
back-propagation is calculated asO(K1K22 +K2K3 +K3K4)
andO(NTrain(K1K2 +K1K22 +K3K4)), respectively.
In the following, we analyze the computational complexity
of DeepLSC without the symmetric experience augmenta-
tion mechanism and DeepLSC, respectively. (i) In DeepLSC
without the symmetric experience augmentation mechanism,
the size of the pre-processed input matrix S(t) is 2N(N +
M) + 2M, the total number of all optional sub-actions is
2N(N + M) + M, and the GRU and FC layers share
the same number of neurons, denoted by K. In addition,
the number of experiences used for training (i.e., back-
propagation) isNeT . Thus, the total computational complexity
of DeepLSC without symmetric experience augmentation
for both forward-propagation and back-propagation is calcu-
lated as O
(
NeT (N2 +NM +M)K2). (ii) The symmetric
experience augmentation mechanism, while enriching avail-
able experiences, increases the computational overhead of
DeepLSC during the back-propagation stage. In particular,
with this mechanism, the number of experiences used for
training is NeT Λ(ω). As a result, the total computational
complexity of DeepLSC for both forward-propagation and
back-propagation isO
(
NeT Λ(ω)(N2 +NM +M)K2).
Overall, the proposed symmetric experience augmentation
mechanism, while signiﬁcantly enriching the experiences for
DeepLSC training, introduces additional computational com-
plexity ofO
(
NeT (Λ(ω)− 1)(N2 +NM +M)K2).
B. Practical Implementation
The DeepLSC scheme can be easily implemented in prac-
tical LAE-oriented ISAC systems, where the GBS with
sufﬁcient computational resources serves as the agent to exe-
cute the scheme. In the following, we provide the detailed
procedures for applying DeepLSC in practical scenarios.
1) Training Phase: Similar to previous works [15] and [46],
the agent interacts with a simulation environment built using
mathematical models, rather than relying on prior training
data. The state-of-the-art mathematical models, including the
Gauss-Markov-based target random mobility model, the LoS
channel model, and the UA V ﬂight mission models, are derived
from real-world data to ensure realistic simulations. In this
regard, the DeepLSC scheme trained in this environment can
be effectively applied to real-world scenarios. Through inter-
actions within the simulation environment, the agent collects
data to train the DeepLSC scheme for joint beamforming and
trajectory optimization. Once the DNN model converges, the
trained DeepLSC scheme can be deployed in realistic systems.
2) Deployment Phase: During the deployment phase, the
GBS does not require the real-time sum-rate and average
sensing SNR to calculate the reward. Instead, it employs
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 361
the well-trained DeepLSC scheme to make joint decisions.
Speciﬁcally, the GBS/agent feeds the state generated according
to (15) into the eval-actor to determine joint decisions for data
transmission, UA V control, and target detection.
3) Environmental Changes: When the deployment environ-
ment undergoes signiﬁcant changes (e.g., the number of UA Vs
or the number of time slots within a ﬂight period changes),
the GBS retrains the DeepLSC scheme online accordingly.
At this time, the DNN parameters of the previously trained
DeepLSC scheme can be ﬁne-tuned based on the training
results in the new environment. During this process, some
efﬁcient training techniques, e.g., transfer learning [47] and
the proposed symmetric experience augmentation mechanism,
can be used to improve the convergence of the DNN model.
Likewise, in emergency situations such as UA V failure, the
GBS can update the set of available UA Vs in the simulation
and retrain the DeepLSC scheme accordingly. Since this
process can be done in simulated environments beforehand, the
GBS can pre-train multiple versions of the DeepLSC scheme
with different conﬁgurations (e.g., different numbers and initial
positions of UA Vs). By doing so, real-time adaptation can
be achieved and the performance of the ISAC system can be
maintained without signiﬁcant downtime.
VI. P ERFORMANCE EVALUATION
This section evaluates the performance of DeepLSC based
on Python 3.6 simulation platform, where the Keras library
[48] builds all DNN models.
A. Parameter Settings
1) System Setups: We consider a scenario with one GBS,
one target, and M = 4 UA Vs, unless stated otherwise. The
GBS is located at (0, 0, 0) m, the initial location of the target is
(−60, 100, 70) m, the initial locations of UA Vs are uniformly
chosen from the area [−150,−80] m×[60, 150] m×80 m,
and the ﬁnal locations of UA Vs are uniformly chosen from
the area [90, 160] m×[50, 160] m×80 m. The movement
speed of the target and UA Vs are 10 m per time slot, and the
number of time slots within an episode i.e., T, is 40 time slots,
by default. The movement azimuth and elevation of the target
are initialized to 30◦, the time correlation coefﬁcients µa and
µe for the target movement are 0.9, and the corresponding
asymptotic means and standard deviations, i.e., ξa,ξe,σφ, and
σϕ, are 10◦. The number of antennas and the transmit power
areN = 6 andPmax = 40 dBm, respectively. The noise power
σ2b and σ2m are−80 dBm, The path loss exponent is 3.2, the
reference distance D0 is 1 m, and the path loss L0 for D0 is
−30 dB. The sensing SNR requirement Γmin is set to 1 dB.
2) Algorithm Setups: In DeepLSC, the GRU and FC layers
contain 128 neurons. The underpinning algorithm in DeepLSC
is DDPG, where all hyper-parameters are set according to pre-
vious investigations [39] and [49], combined with ﬁne-tuning.
Speciﬁcally, the work [39] proposed the DDPG algorithm and
provided default hyper-parameters, while the work [49] com-
prehensively analyzed the impact of different hyper-parameters
on the performance of DDPG. TABLE II summarizes
the detailed hyper-parameters used in DeepLSC, and in
TABLE II
ALGORITHM HYPER -PARAMETERS
TABLE III
AVERAGE SENSING SNR [ DB] OF VARIOUS SCHEMES WHEN THE NUMBER
OF UAVS IS 4
Section VI-E, we will further discuss the impact of different
hyper-parameters on the performance of DeepLSC. In the
simulation, the following schemes are considered:
• DeepLSC: This is our designed DRL-based ISAC scheme
for supporting LAE.
• DeepLSC-CNE: This scheme replaces the constrained
noise-exploration policy with the conventional noise-
exploration policy [39]. To meet the signal power
constraint for communication and sensing, the scaling
factor ϵ is retained in the conventional noise-exploration
policy.
• DeepLSC-CER: This scheme replaces the proposed
hierarchical experience replay mechanism with the con-
ventional experience replay mechanism [40].
• DeepLSC-w: This scheme removes the proposed sym-
metric experience augmentation mechanism to evaluate
its effectiveness in DeepLSC.
• AC2: This scheme utilizes the actor-critic algorithm [36]
with the constrained noise-exploration policy to optimize
GBS’s beamforming and UA Vs’ trajectories. Its basic
elements, including state, action, and reward function,
are exactly the same as DeepLSC. Furthermore, AC2
usually uses a single instantaneous experience set to train
its DNN, instead of random historical experience sets.
3) Metric Setups: We consider 5000 episodes, each of
which contains T time slots in which all UA Vs fulﬁll the preset
ﬂight missions. The performance metrics include the commu-
nication sum-rate, the sensing SNR, and whether the ﬂight
missions of all UA Vs are met. Speciﬁcally, the communication
sum-rate at each episode is a short-term average, which is
calculated by averaging ∑Tt=1 Rtotal(t) over the previous 200
episodes; and the short-term average sensing SNR at each
episode is calculated by averaging∑Tt=1 SNRTar(t)/T over the
previous 200 episodes. To ensure the reliability of experiments,
all simulations run 20 times to obtain the average result.
B. Learning Curves
Fig. 3 and TABLE III provide the communication sum-
rate and average sensing SNR achieved by various schemes,
respectively. As can be seen from Fig. 3, due to the random
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

362 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 3. Communication sum-rate achieved by various schemes when the
number of UA Vs is 4.
Fig. 4. Flight trajectory of a speciﬁc UA V under various schemes.
mobility of the target, all the curves are in ﬂuctuation. In
other words, in different episodes, the joint beamforming and
trajectory strategies derived from the same scheme may be
different. Fig. 4 depicts the ﬂight trajectory of a speciﬁc UA V
under various schemes in the last simulation episode.
1) DeepLSC V ersus DeepLSC-CNE: As presented in Fig. 3,
among all the schemes, DeepLSC-CNE achieves the highest
communication sum-rate while guaranteeing the given sensing
SNR constraint. To be speciﬁc, compared with DeepLSC, the
communication sum-rate gain of DeepLSC-CNE is around
11.14%. This is because DeepLSC-CNE is designed to max-
imize the communication sum-rate and satisfy the average
sensing SNR requirement, while ignoring the ﬂight mission
constraint. As a result, under DeepLSC-CNE, UA Vs tend to
stay in a speciﬁc area instead of ﬂying from initial locations
to desired locations within each episode, as shown in Fig. 4.
On the contrary, owing to the constrained noise-exploration
policy, DeepLSC can well guide UA Vs to reach their desired
locations within an episode, although sacriﬁcing both commu-
nication and sensing performance to some certain. This result
demonstrates the effectiveness of the proposed constrained
noise-exploration policy in fulﬁlling the ﬂight mission.
2) DeepLSC V ersus AC2: Similar to DeepLSC, AC2
employs the constrained noise-exploration policy to decide
the movement directions of UA Vs. It, however, not only fails
to satisfy the given average sensing SNR requirement, but
also achieves a much lower communication sum-rate than
DeepLSC. In particular, compared with DeepLSC, the sum-
rate reduction of AC2 is more than 22.73%. The underlying
reasons are as follows. First, before executing the constrained
noise-exploration policy, DeepLSC derives a deterministic
joint beamforming and trajectory decision, whereas AC2 usu-
ally generates a probability distribution corresponding to all
possible actions and randomly samples an action from this
distribution, resulting in inefﬁcient decisions. Second, during
DNN training, DeepLSC makes full use of random historical
experience sets, but AC2 relies on a single instantaneous
experience set. As a consequence, the parameters of the DNN
are strongly correlated before and after the update, which
reduces the efﬁciency of the decision-making [36]. Besides, in
DeepLSC, the target-actor and target-critic are utilized to assist
in training eval-actor and eval-critic, which further boosts the
stability of the algorithm, whilst AC2 lacks this consideration.
3) DeepLSC V ersus DeepLSC-CER: Unlike AC2, the
underpinning algorithm in DeepLSC-CER is DDPG [37],
which circumvents the above issues well. Thus, in com-
parison to AC2, while meeting the preset average sensing
SNR requirement, DeepLSC-CER yields a signiﬁcant com-
munication sum-rate gain of about 15.88%. DeepLSC-CER,
however, does not cater well to the formulated optimization
problem. Speciﬁcally, the formulated optimization problem
is an episode task, in the sense that all experiences gener-
ated within an episode should be jointly used to train the
DNN. Unfortunately, the DNN training mechanism adopted
in DeepLSC-CER, i.e., conventional experience replay [40],
separately collects and utilizes the experiences from different
time slots. The consequence is that all experiences generated
within an episode cannot be guaranteed to appear in full
during training. By contrast, beneﬁting from the hierarchi-
cal experience replay mechanism, DeepLSC is able to take
advantage of experience sets, each composed of all experiences
generated within an episode. Thus, DeepLSC can well handle
the formulated problem and further improve the sum-rate of
LAE-oriented ISAC systems: compared with DeepLSC-CER,
the improvement attained by DeepLSC is about 11.68%.
4) DeepLSC V ersus DeepLSC-w: From Fig. 3, it can
also be found that DeepLSC-w experiences more episodes
before convergence compared to DeepLSC, DeepLSC-CNE,
and DeepLSC-CER, although they are all online learning
schemes. 4 In particular, compared with the other three
schemes, DeepLSC-w consumes over 130.60% more episodes
to converge. The main reasons are below. In DeepLSC-w, the
experience sets can only be obtained through interactions with
the environment. In general, to efﬁciently train the DNN, a
4We adopt the convergence line to clear the convergence process of various
schemes, which is deﬁned as the line along which the algorithm tends to be
stable in the long-term average. In addition, the time slot where the scheme
reaches the convergence line for the ﬁrst time is called the convergence point,
and the number of time slots consumed before reaching the convergence point
is considered to be the number of time slots required to converge.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 363
Fig. 5. Sum-rate of various schemes under different numbers of UA Vs.
TABLE IV
PERFORMANCE OF VARIOUS SCHEMES IN SATISFYING THE AVERAGE
SENSING SNR AND FLIGHT MISSION CONSTRAINTS UNDER DIFFER -
ENT NUMBERS OF UAVS
sufﬁcient number of experience sets are essential. As a result,
the learning process of the agent is slow. Unlike DeepLSC-w,
based on the limited existing experience sets, DeepLSC,
DeepLSC-CNE, and DeepLSC-CER schemes exploit the sym-
metric experience augmentation mechanism to enrich the
available experience sets. Therefore, these three schemes can
acquire massive experience sets in a short time, thereby
signiﬁcantly accelerating the convergence speed. On the other
hand, in terms of communication and sensing performance,
DeepLSC-w is the same as DeepLSC after convergence; and
the UA V trajectories generated by the two are also similar,
as provided in Fig. 4. This is because the proposed symmetric
experience augmentation mechanism will not impair algorithm
performance despite achieving faster convergence.
C. Robustness to Different Numbers of UA Vs
This subsection evaluates the robustness of various schemes
against different numbers of UA Vs, in whichM increases from
2 to 5 with a step size of 1. Fig. 5 and TABLE IV present the
communication sum-rate and constraint satisfactory of various
schemes, respectively.
It can be observed that as M increases, the communication
sum-rate achieved by all schemes are gradually improved.
Fig. 6. Communication sum-rate achieved by various schemes when the
number of UA Vs is 20.
TABLE V
PERFORMANCE OF VARIOUS SCHEMES IN SATISFYING THE AVERAGE
SENSING SNR AND FLIGHT MISSION CONSTRAINTS WHEN THE NUM-
BER OF UAVS IS 20
This is because when M increases, the GBS can support more
parallel transmissions. At this time, under a reasonable beam-
forming design, spatial multiplexing can be further improved,
thereby increasing the communication sum-rate. In addition,
with the increase of M, the sum-rate gap between DeepLSC
and DeepLSC-CER/AC2 increases. For example, when M
increases from 2 to 5, the sum-rate gain of DeepLSC increases
from 14.43 bps/Hz to 21.42 bps/Hz compared with DeepLSC-
CER. On the other hand, as summarized in TABLE IV, due
to the inefﬁcient DNN training mechanism, both DeepLSC-
CER and AC2 cannot always meet the average sensing SNR
requirement under different values of M, whereas DeepLSC-
CNE fails to fulﬁll the ﬂight mission since it lacks the
guidance of the constrained noise-exploration policy. Thus,
among all the schemes, only DeepLSC and DeepLSC-w satisfy
all constraints under various settings. DeepLSC-w, however,
converges much slower than DeepLSC, as elaborated in
Section VI-B. Overall, the above results exemplify that com-
pared with other schemes, DeepLSC is more robust against
different numbers of UA Vs in LAE-oriented ISAC systems.
To further evaluate the scalability of DeepLSC when the
number of UA Vs, i.e.,M, increases signiﬁcantly, we consider a
scenario where the GBS is equipped with 20 antennas to serve
20 UA Vs and sense the randomly moving target. Fig. 6 and
TABLE V show the communication sum-rate and constraint
satisfactory of various schemes, respectively. As can be seen,
although M is quite large, DeepLSC can still achieve much
better overall system performance than other solutions. On the
other hand, as presented in Section V-A, the computational
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

364 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Sum-rate of various schemes under different numbers of time slots
within a ﬂight period.
TABLE VI
PERFORMANCE OF VARIOUS SCHEMES IN SATISFYING THE AVERAGE
SENSING SNR AND FLIGHT MISSION CONSTRAINTS UNDER DIFFER -
ENT NUMBERS OF TIME SLOTS WITHIN A FLIGHT PERIOD
complexity of DeepLSC increases linearly with the increase
of M. In other words, as M increases, DeepLSC can achieve
excellent communication and sensing performance without
incurring too much additional computational overhead. The
scalability of DeepLSC makes it highly favorable for realistic
systems.
D. Robustness to Different Numbers of Time Slots Within a
Flight Period
This simulation evaluates the robustness of various schemes
to different numbers of time slots within a ﬂight period. In the
considered ﬂight area, the maximum possible ﬂight distance
of a UA V is calculated to be
√
(160 + 150)2 + (160− 60)2 =
325.73 m. Since the movement speed of UA Vs is 10 m per
time slot, a UA V needs at most 33 time slots to complete
the maximum distance ﬂight. In this regard, to ensure that the
ﬂight mission can be completed, we initialize T to 40 and
increase it to 70 with a step size of 10. The communication
sum-rate and constraint satisfactory of various schemes are
shown in Fig. 7 and TABLE VI, respectively.
As expected, the communication sum-rate attained by vari-
ous schemes improves monotonically as T increases. The main
reasons are below. As T increases, the number of time slots
during which all UA Vs can ﬂy freely without the ﬂight mission
constraint increases. In this regard, all schemes possess more
time degrees of freedom to optimize the joint beamforming
and trajectory strategy, so as to maximize the communi-
cation sum-rate while satisfying the average sensing SNR
requirement. Besides, under different T, DeepLSC, DeepLSC-
CER, and DeepLSC-w schemes can always satisfy all preset
constraints, whilst both DeepLSC-CNE and AC2 fail. Thanks
to a more intelligent and efﬁcient strategy, DeepLSC achieves
a higher communication sum-rate than DeepLSC-CER. To be
speciﬁc, compared with DeepLSC-CER, DeepLSC yields a
more than 11.68% sum-rate gain for all simulation setups.
More importantly, as T increases, the communication sum-
rate gap between DeepLSC and DeepLSC-CNE keeps almost
unchanged, whereas that between DeepLSC and DeepLSC-
CER/AC2 increases. In particular, when M increases from 40
to 70, the sum-rate improvement of DeepLSC increases (i)
from 18.42 bps/Hz to 39.56 bps/Hz compared with DeepLSC-
CER and (ii) from 40.03 bps/Hz to 76.63 bps/Hz compared
with AC2. The above observations show that under different
numbers of time slots within a ﬂight period, DeepLSC is more
robust than other schemes.
E. Impact of Different Hyper-Parameters
The above simulation results have demonstrated the superi-
ority of DeepLSC compared to other schemes. We now study
the impact of different hyper-parameters on the performance
of DeepLSC. In particular, the following hyper-parameters are
considered: the learning rate of the eval-actor (αa), the learning
rate of the eval-critic (αc), the update coefﬁcient of the target-
actor (χa), the update coefﬁcient of the target-critic ( χc), the
size of the experience buffer ( D), the size of the mini-batch
(Ne), the augmentation factor ( ζ), and the initial exploration
variance and decay factor in the constrained noise-exploration
policy (σinit andκ). Under various simulation setups, DeepLSC
can strictly satisfy the ﬂight mission constraint through the
constrained noise-exploration policy and thus this performance
metric is omitted in this subsection. TABLE VII summarizes
the communication sum-rate and sensing SNR constraint sat-
isfactory of DeepLSC under different hyper-parameters.
It can be seen that among all the hyper-parameters, only
the change of the augmentation factor ζ has no impact on the
performance of DeepLSC. This is because ζ is employed to
adjust the number of augmented experiences in the symmetric
experience augmentation mechanism, which only affects the
convergence of DeepLSC. Besides, the impact of other hyper-
parameters on the performance of DeepLSC is as follows.
• Impact of learning rates αa and αc: According to [49],
to enable the efﬁcient learning of the agent, the learning
rate of the eval-critic should be greater than that of the
eval-actor. In addition, as shown in TABLE VII, when αa
andαc are too small, DeepLCS learns slowly and fails to
ﬁnd an efﬁcient solution. Increasing αa andαc gradually
improves both communication and sensing performance.
However, too large αa and αc result in overly aggressive
learning, leading to sub-optimal policy convergence.
• Impact of update coefﬁcientsχa andχc: As demonstrated
in [49], the update coefﬁcients of the target actor and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 365
TABLE VII
PERFORMANCE OF DEEP LSC IN COMMUNICATION SUM-RATE AND SATIS-
FYING THE AVERAGE SENSING SNR C ONSTRAINT UNDER DIFFERENT
HYPER -PARAMETERS
the target critic are typically set to the same value.
TABLE VII reveals that the performance change trend of
DeepLSC under different update coefﬁcients is the same
as that under different learning rates. Besides, both χa
and χc exhibit a stronger inﬂuence on the performance
of DeepLSC compared to αa and αc.
• Impact of the experience buffer size D: A too small value
of D causes high sample correlation, thus reducing the
training efﬁciency. In this case, the communication sum-
rate decreases and the sensing SNR constraint cannot be
met. Instead, a too large value of D results in too old
experiences used in training, negatively impacting the
agent’s learning.
• Impact of the mini-batch size Ne: When Ne is small,
the experiences used for training lacks diversity, causing
DNN overﬁtting. As Ne increases, the communication
and sensing performance of DeepLSC is improved, but it
incurs high computational overhead.
• Impact of the initial exploration variance σinit: If σinit is
too small, the agent fails to adequately explore different
strategies, thus converging to sub-optimal solutions. On
the contrary, an excessively large σinit causes persistent
exploration, which prevents the agent from efﬁciently
utilizing learned strategies.
• Impact of the exploration decay factor κ: Similar to σinit,
κ balances exploration and exploitation. As shown in
TABLE VII, κ should be close to 1.0 (e.g., 0.999) to
gradually reduce the exploration variance and prevent pre-
mature exploration termination. However, an excessively
large κ hinders the agent from using learned strategies.
Overall, different hyper-parameters affect the performance
of DeepLSC to varying degrees. Among them, the learning
rates (αa and αc), update coefﬁcients (χa and χc), experience
buffer size (D), and mini-batch size (Ne) demonstrate particu-
larly signiﬁcant inﬂuence compared to other hyper-parameters.
VII. C ONCLUSION
This paper put forth a new ISAC scheme for LAE, termed
DeepLSC, based on the DRL technique. By jointly optimizing
GBS’s beamforming and UA Vs’ trajectories, DeepLSC aims to
maximize the expected communication sum-rate over the ﬂight
period, subject to the average sensing SNR requirement, ﬂight
mission, collision avoidance, and maximum transmit power
constraints. DeepLSC, on the one hand, is model-free since
it does not require prior mobility information of the target;
on the other hand, it is capable of episode tasks thanks to an
appropriate structural design. First, to meet various constraints,
a constrained noise-exploration policy and a reward function
were judiciously designed in DeepLSC for action selection
and action evaluation, respectively. Thereafter, we developed
a hierarchical experience replay mechanism for DNN training,
where all experiences within an episode are jointly utilized
to enable DeepLSC to efﬁciently learn from episode tasks.
Besides, to promote the convergence speed of DeepLSC, a
symmetric experience augmentation mechanism was further
proposed. Simulation results demonstrated compared with
other schemes, DeepLSC (i) yields a much higher commu-
nication sum-rate while meeting all constraints, (ii) converges
faster, and (iii) is more robust against different settings.
In the current work, we focused on maximizing the com-
munication sum-rate under the constraints of ﬂight mission,
collision avoidance, and average sensing SNR. However, in
realistic systems, the energy of UA Vs is typically limited.
Therefore, how to minimize the energy consumption of UA Vs
is also a crucial issue in LAE-oriented ISAC systems. Gener-
ally, there is a fundamental trade-off between communication
sum-rate maximization and UA V energy consumption min-
imization. In our future work, a new LAE-oriented ISAC
scheme will be designed to balance these two conﬂicting
objectives.
REFERENCES
[1] Y . Jiang et al., “6G non-terrestrial networks enabled low-altitude econ-
omy: Opportunities and challenges,” 2023, arXiv:2311.09047.
[2] China Telecom, Ericsson, Nokia, Huawei, ZTE, CICT Mobile, OPPO,
Xiaomi, vivo, Lenovo, Qualcomm, Mediatek, UNISOC,. (2024). The
Low-altitude Network By Integrated Sensing and Communication .
[Online]. Available: https://www.zte.com.cn/content/dam/zte-site/
res-www-zte-com-cn/mediares/zte/%E6%97%A0%E7%BA%BF%
E6%8E%A5%E5%85%A5/%E7%99%BD%E7%9A%
AE%E4%B9%A6/Low altitude network by ISAC.pdf
[3] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets integrated
sensing and communication: Challenges and future directions,” IEEE
Commun. Mag. , vol. 61, no. 5, pp. 62–67, May 2023.
[4] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[5] K. Zhang and C. Shen, “UA V aided integrated sensing and
communications,” in Proc. IEEE 94th V eh. Technol. Conf. (VTC-Fall) ,
Sep. 2021, pp. 1–6.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

366 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[6] S. Zhang, H. Zhang, Z. Han, H. V . Poor, and L. Song, “Age of
information in a cellular Internet of UA Vs: Sensing and communication
trade-off design,” IEEE Trans. Wireless Commun. , vol. 19, no. 10,
pp. 6578–6592, Oct. 2020.
[7] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-
UA V networks,”IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660–2672,
Apr. 2021.
[8] B. Chang, W. Tang, X. Yan, X. Tong, and Z. Chen, “Integrated
scheduling of sensing, communication, and control for mmWave/THz
communications in cellular connected UA V networks,” IEEE J. Sel.
Areas Commun., vol. 40, no. 7, pp. 2103–2113, Jul. 2022.
[9] W. Ding et al., “Multi-UA V-Enabled integrated sensing and commu-
nications: Joint UA V placement and power control,” in Proc. IEEE
Globecom Workshops, Dec. 2023, pp. 842–847.
[10] G. Abdissa Bayessa, R. Chai, C. Liang, D. Kumar Jain, and Q. Chen,
“Joint UA V deployment and precoder optimization for multicasting and
target sensing in UA V-assisted ISAC networks,” IEEE Internet Things
J., vol. 11, no. 20, pp. 33392–33405, Oct. 2024.
[11] X. Yu, J. Xu, N. Zhao, X. Wang, and D. Niyato, “Security enhancement
of ISAC via IRS-UA V ,”IEEE Trans. Wireless Commun., vol. 23, no. 10,
pp. 15601–15612, Jul. 2024.
[12] J. Wu, W. Yuan, and L. Hanzo, “When UA Vs meet ISAC: Real-
time trajectory design for secure communications,” IEEE Trans. V eh.
Technol., vol. 71, no. 12, pp. 16766–16771, Dec. 2023.
[13] S. Hu, X. Yuan, W. Ni, and X. Wang, “Trajectory plan-
ning of cellular-connected UA V for communication-assisted radar
sensing,” IEEE Trans. Commun. , vol. 70, no. 9, pp. 6385–6396,
Sep. 2022.
[14] Y . Liu, S. Liu, X. Liu, Z. Liu, and T. S. Durrani, “Sensing fairness-
based energy efﬁciency optimization for uav enabled integrated sensing
and communication,” IEEE Wireless Commun. Lett. , vol. 12, no. 10,
pp. 1702–1706, Oct. 2023.
[15] Z. Liu, X. Liu, Y . Liu, V . C. M. Leung, and T. S. Durrani, “UA V assisted
integrated sensing and communications for Internet of Things: 3D
trajectory optimization and resource allocation,” IEEE Trans. Wireless
Commun., vol. 23, no. 8, pp. 8654–8667, Jan. 2024.
[16] Y . Liu et al., “Secure rate maximization for ISAC-UA V assisted com-
munication amidst multiple eavesdroppers,” IEEE Trans. V eh. Technol.,
vol. 73, no. 10, pp. 15843–15847, Jun. 2024.
[17] J. Zhang, J. Xu, W. Lu, N. Zhao, X. Wang, and D. Niyato, “Secure
transmission for IRS-aided UA V-ISAC networks,”IEEE Trans. Wireless
Commun., vol. 23, no. 9, pp. 12256–12269, Apr. 2024.
[18] X. Jing, F. Liu, C. Masouros, and Y . Zeng, “ISAC from the sky:
UA V trajectory design for joint communication and target localization,”
IEEE Trans. Wireless Commun. , vol. 23, no. 10, pp. 12857–12872,
Oct. 2024.
[19] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li,
“Throughput maximization for UA V-enabled integrated periodic sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 1,
pp. 671–687, Jan. 2023.
[20] K. Meng, Q. Wu, S. Ma, W. Chen, and T. Q. S. Quek, “UA V
trajectory and beamforming optimization for integrated periodic sensing
and communication,” IEEE Wireless Commun. Lett. , vol. 11, no. 6,
pp. 1211–1215, Jun. 2022.
[21] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamforming design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Apr. 2023.
[22] Z. Wu, X. Li, Y . Cai, and W. Yuan, “Joint trajectory and resource
allocation design for RIS-assisted UA V-enabled ISAC systems,” IEEE
Wireless Commun. Lett. , vol. 13, no. 5, pp. 1384–1388, May 2024.
[23] C. Deng, X. Fang, and X. Wang, “Beamforming design and trajec-
tory optimization for UA V-empowered adaptable integrated sensing
and communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 11,
pp. 8512–8526, Nov. 2023.
[24] T. V . Chien, M. D. Cong, N. C. Luong, T. Nhu, D. I. Kim, and
S. Chatzinotas, “Joint computation ofﬂoading and target tracking in
integrated sensing and communication enabled UA V networks,” IEEE
Commun. Lett. , vol. 28, no. 6, pp. 1327–1331, Apr. 2024.
[25] J. Wu, W. Yuan, and L. Bai, “On the interplay between sensing and
communications for UA V trajectory design,” IEEE Internet Things J. ,
vol. 10, no. 23, pp. 20383–20395, Dec. 2023.
[26] R. Zhang, Y . Zhang, R. Tang, H. Zhao, Q. Xiao, and C. Wang, “A joint
UA V trajectory, user association, and beamforming design strategy for
multi-UA V assisted ISAC systems,” IEEE Internet Things J. , vol. 11,
no. 8, pp. 29360–29374, Jul. 2024.
[27] T. Zhang, K. Zhu, S. Zheng, D. Niyato, and N. C. Luong, “Trajectory
design and power control for joint radar and communication enabled
multi-UA V cooperative detection systems,” IEEE Trans. Commun. ,
vol. 71, no. 1, pp. 158–172, Jan. 2023.
[28] Z. Xie, Z. Wang, Z. Zhang, J. Wang, Z. Jiang, and Z. Han,
“Distributed UA V swarm for device-free integrated sensing and
communication relying on multi-agent reinforcement learning,”
IEEE Trans. V eh. Technol. , vol. 73, no. 12, pp. 19925–19930,
Aug. 2024.
[29] X. Chen, X. Cao, L. Xie, and Y . He, “DRL-based joint trajectory
planning and beamforming optimization in aerial RIS-assisted ISAC
system,” in Proc. IEEE Int. Workshop Radio Freq. Antenna Technol.
(iWRF&AT), Shenzhen, China, May 2024, pp. 510–515.
[30] H. Cho, S. Yoo, B. C. Jung, and J. Kang, “Enhancing battleﬁeld
awareness: An aerial RIS-assisted ISAC system with deep reinforcement
learning,” in Proc. IEEE MILCOM , Washington, DC, USA, Dec. 2024,
pp. 469–474.
[31] G. Fontanesi et al., “A deep-NN beamforming approach for dual function
radar-communication THz UA V ,”IEEE Trans. V eh. Technol. , vol. 74,
no. 1, pp. 746–760, Sep. 2024.
[32] Y . Qin, Z. Zhang, X. Li, W. Huangfu, and H. Zhang, “Deep
reinforcement learning based resource allocation and trajectory plan-
ning in integrated sensing and communications UA V network,”
IEEE Trans. Wireless Commun. , vol. 22, no. 11, pp. 8158–8169,
Nov. 2023.
[33] C. Dai, T. Wu, G. Sun, Y . Zuo, Z. Guo, and F. Xiao, “Joint UA V
trajectory and beamforming design for RIS-aided integrated sensing
and communication system,” in Proc. IEEE INFOCOM Workshops ,
Vancouver, BC, Canada, May 2024, pp. 01–06.
[34] Y . Cui et al., “Speciﬁc beamforming for multi-UA V networks: A dual
identity-based ISAC approach,” in Proc. IEEE ICC , Rome, Italy, May
2023, pp. 4979–4985.
[35] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for
low-altitude economy: Coordinated transmit beamforming and UA V
trajectory design,” IEEE Trans. Commun. , early access, Feb. 11, 2025,
doi: 10.1109/TCOMM.2025.3541027.
[36] R. S. Sutton and A. G. Barto, Reinforcement Learning: An Introduction .
Cambridge, MA, USA: MIT Press, 2018.
[37] V . Mnih et al., “Human-level control through deep reinforcement
learning,” Nature, vol. 518, no. 7540, pp. 529–533, Feb. 2015.
[38] X. Ye, Y . Yu, and L. Fu, “Multi-channel opportunistic access for
heterogeneous networks based on deep reinforcement learning,”
IEEE Trans. Wireless Commun. , vol. 21, no. 2, pp. 794–807,
Feb. 2022.
[39] T. Lillicrap et al., “Continuous control with deep reinforcement
learning,” in Proc. Int. Conf. Learn. Represent. , May 2016, pp. 1–14.
[40] L.-J. Lin, “Self-improving reactive agents based on reinforcement learn-
ing, planning and teaching,” Mach. Learn. , vol. 8, no. 3, pp. 293–321,
May 1992.
[41] H. Tabassum, M. Salehi, and E. Hossain, “Fundamentals of mobility-
aware performance characterization of cellular networks: A tutorial,”
IEEE Commun. Surveys Tuts., vol. 21, no. 3, pp. 2288–2308, 3rd Quart.,
2019.
[42] R. S. Sutton, D. McAllester, S. Singh, and Y . Mansour, “Policy gradient
methods for reinforcement learning with function approximation,” in
Proc. Adv. Neural Inf. Process. Syst. , Nov. 1999, pp. 1057–1063.
[43] K. Cho et al., “Learning phrase representations using RNN
encoder–decoder for statistical machine translation,” in Proc. EMNLP ,
Sep. 2014, pp. 1724–1734.
[44] I. Goodfellow, Y . Bengio, and A. Courville, Deep Learning. Cambridge,
MA, USA: MIT Press, 2016.
[45] ´A. Seress, Permutation Group Algorithms. Cambridge, U.K.: Cambridge
Univ. Press, 2003.
[46] P. Wang et al., “Decentralized navigation with heterogeneous feder-
ated reinforcement learning for UA V-enabled mobile edge computing,”
IEEE Trans. Mob. Comput. , vol. 23, no. 12, pp. 13621–13638,
Aug. 2024.
[47] X. Ye, Y . Mao, X. Yu, and L. Fu, “Intelligent omni-surface-
aided integrated sensing and communications based on deep rein-
forcement learning with knowledge transfer,” IEEE Trans. Wireless
Commun., vol. 24, no. 5, pp. 4344–4360, May 2025, doi: 10.1109/
TWC.2025.3542780.
[48] F. Chollet. (2018). Keras: The Python Deep Learning Library . [Online].
Available: https://keras.io
[49] Y . Duan, X. Chen, R. Houthooft, J. Schulman, and P. Abbeel,
“Benchmarking deep reinforcement learning for continuous control,” in
Proc. Int. Conf. Mach. Learn. , Jun. 2016, pp. 1329–1338.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 17 页

YE et al.: ISAC FOR LOW-ALTITUDE ECONOMY: A DRL APPROACH 367
Xiaowen Ye received the Ph.D. degree in com-
munication and information systems from Xiamen
University, Xiamen, China, in 2024. He was a Post-
Doctoral Research Fellow with the Department of
Electrical Engineering, City University of Hong
Kong, from 2024 to 2025. He is an Associate Pro-
fessor with the College of Photonic and Electronic
Engineering, Fujian Normal University, China. His
research interests include deep reinforcement learn-
ing, wireless network optimization, and dynamic
resource allocation.
Yuyi Mao (Senior Member, IEEE) received the
B.Eng. degree in information and communica-
tion engineering from Zhejiang University (ZJU),
Hangzhou, China, in 2013, and the Ph.D. degree
in electronic and computer engineering from The
Hong Kong University of Science and Technology
(HKUST), Hong Kong, in 2017. He was a Lead
Engineer with The Hong Kong Applied Science
and Technology Research Institute Company Ltd.
(ASTRI), Hong Kong, a Senior Researcher with the
Theory Lab, 2012 Labs, Huawei Tech. Investment
Co., Ltd., Hong Kong, and a Research Assistant Professor with the Department
of Electrical and Electronic Engineering, The Hong Kong Polytechnic Uni-
versity (PolyU), Hong Kong. He is currently an Assistant Professor with the
School of Computer Science and Engineering, Macau University of Science
and Technology (MUST), Macau. His research interests include wireless
communications and networking, mobile edge computing and learning, and
wireless artiﬁcial intelligence.
Dr. Mao was a recipient of the 2021 IEEE Communications Society
Best Survey Paper Award and the 2019 IEEE Communications Society and
Information Theory Society Joint Paper Award. He was also recognized as an
Exemplary Reviewer of the IEEE W IRELESS COMMUNICATIONS LETTERS
in 2019 and 2021 and IEEE T RANSACTIONS ON COMMUNICATIONS in 2020.
He is an Editor of the IEEE W IRELESS COMMUNICATIONS LETTERS , an
Associate Editor of IEEE T RANSACTIONS ON MOBILE COMPUTING , the
EURASIP Journal on Wireless Communications and Networking , and the
HKIE Transactions.
Xianghao Yu (Senior Member, IEEE) received
the B.Eng. degree in information engineering from
Southeast University, Nanjing, China, in 2014, and
the Ph.D. degree in electronic and computer engi-
neering from The Hong Kong University of Science
and Technology (HKUST), Hong Kong, China, in
2018.
He is currently an Assistant Professor with the
Department of Electrical Engineering, City Univer-
sity of Hong Kong (CityU), Hong Kong, China.
From 2018 to 2020, he was a Humboldt Post-
Doctoral Research Fellow with the Institute for Digital Communications,
Friedrich-Alexander University of Erlangen-Nuremberg (FAU), Erlangen,
Germany. Before joining CityU, he was a Research Assistant Professor with
the Department of Electronic and Computer Engineering, HKUST. He has co-
authored the book Stochastic Geometry Analysis of Multi-Antenna Wireless
Networks (Springer, 2019). His research interests include intelligent reﬂecting
surface-assisted communications, integrated sensing and communications,
near-ﬁeld communications, and wireless artiﬁcial intelligence.
Dr. Yu received the IEEE Global Communications Conference (GLOBE-
COM) 2017 Best Paper Award, the 2018 IEEE Signal Processing Society
Young Author Best Paper Award, the IEEE GLOBECOM 2019 Best Paper
Award, the 2023 IEEE Communications Society Leonard G. Abraham Prize,
and the 2024 IEEE ComSoc Asia-Paciﬁc Outstanding Young Researcher
Award. He is the Symposium Co-Chair of the IEEE ICC 2026 Wireless Com-
munications Symposium and serves as the Secretary for the IEEE Wireless
Communications Technical Committee (WTC). He was also recognized as an
Exemplary Reviewer of IEEE T RANSACTIONS ON WIRELESS COMMUNICA -
TIONS in 2017 and 2018 and IEEE T RANSACTIONS ON COMMUNICATIONS
in 2021 and 2022. He is an Editor of IEEE T RANSACTIONS ON WIRELESS
COMMUNICATIONS , IEEE T RANSACTIONS ON MOBILE COMPUTING , and
IEEE C OMMUNICATIONS LETTERS . He was listed as the World’s Top 2%
Scientist by Stanford University from 2020 to 2023.
Shu Sun (Senior Member, IEEE) received the B.S.
degree in applied physics from Shanghai Jiao Tong
University (SJTU), China, in 2012, and the Ph.D.
degree in electrical engineering from New York Uni-
versity, USA, in 2018. She held summer internship
positions at Nokia Bell Labs in 2014 and 2015. She
was a Systems Engineer at Intel Corporation. She is
a tenure-track Associate Professor with the School
of Information Science and Electronic Engineering,
SJTU. Her current research interests include channel
modeling, millimeter-wave communications, inte-
grated sensing and communication, and holographic MIMO. She received
multiple international academic awards, including the 2023 and 2017 IEEE
Neil Shepherd Memorial Best Propagation Paper Awards, the 2017 Marconi
Society Young Scholar Award, the IEEE VTC2016-Spring Best Paper Award,
and the 2015 IEEE Donald G. Fink Award. She is an Associate Editor
or Guest Editor of IEEE T RANSACTIONS ON MOBILE COMPUTING , IEEE
Internet of Things Magazine , and IEEE O PEN JOURNAL OF ANTENNAS AND
PROPAGATION . She also served as a Guest Editor for the IEEE J OURNAL
ON SELECTED AREAS IN COMMUNICATIONS .
Liqun Fu (Senior Member, IEEE) received the
Ph.D. degree in information engineering from The
Chinese University of Hong Kong in 2010.
She was a Post-Doctoral Research Fellow with the
Institute of Network Coding, The Chinese University
of Hong Kong, from 2011 to 2013, and the ACCESS
Linnaeus Centre, KTH Royal Institute of Technol-
ogy, from 2013 to 2015. She was with ShanghaiTech
University as an Assistant Professor from 2015 to
2016. She is a Full Professor with the School of
Informatics, Xiamen University, China. Her research
interests are mainly in communication theory, optimization theory, game
theory, and learning theory, with applications in wireless networks. She also
serves as a TPC Member for many leading conferences in communications
and networking, such as the IEEE INFOCOM, ICC, and GLOBECOM. She
served as the Technical Program Co-Chair for IEEE/CIC ICCC 2021 and the
GCCCN Workshop of the IEEE INFOCOM 2014, the Publicity Co-Chair for
the GSNC Workshop of the IEEE INFOCOM 2016, and the Web Chair for the
IEEE WiOpt 2018. She is on the Editorial Board of IEEE T RANSACTIONS
ON MOBILE COMPUTING (TMC), IEEE C OMMUNICATIONS LETTERS , and
the Journal of Communications and Information Networks (JCIN).
Jie Xu (Fellow, IEEE) received the B.E. and Ph.D.
degrees from the University of Science and Tech-
nology of China. He is currently an Associate
Professor (Tenured) with the School of Science and
Engineering, Shenzhen Future Network of Intel-
ligence Institute (FNii-Shenzhen), and Guangdong
Provincial Key Laboratory of Future Networks of
Intelligence, The Chinese University of Hong Kong,
Shenzhen. His research interests include wireless
communications, wireless information and power
transfer, UA V communications, edge computing and
intelligence, and integrated sensing and communication (ISAC). He was a
recipient of the 2017 IEEE Signal Processing Society Young Author Best
Paper Award, the IEEE/CIC ICCC 2019 Best Paper Award, the 2019 IEEE
Communications Society Asia-Paciﬁc Outstanding Young Researcher Award,
and the 2019 Wireless Communications Technical Committee Outstanding
Young Researcher Award. He is the Symposium Co-Chair of the IEEE
GLOBECOM 2019 Wireless Communications Symposium and the IEEE
ICC 2025 Communication Theory Symposium, the workshop co-chair of
several IEEE ICC and GLOBECOM workshops, the Tutorial Co-Chair of the
IEEE/CIC ICCC 2019/2022, the Chair of the IEEE Wireless Communications
Technical Committee (WTC), and the Vice Co-Chair of the IEEE Emerging
Technology Initiative (ETI) on ISAC. He served or is serving as an Associate
Editor-in-Chief for IEEE T RANSACTIONS ON MOBILE COMPUTING ; an
Editor for IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE
TRANSACTIONS ON COMMUNICATIONS , IEEE W IRELESS COMMUNICA -
TIONS LETTERS , and Journal of Communications and Information Networks ;
an Associate Editor for IEEE A CCESS ; and a Guest Editor for the IEEE
WIRELESS COMMUNICATIONS , IEEE J OURNAL ON SELECTED AREAS IN
COMMUNICATIONS , IEEE Internet of Things Magazine , Science China Infor-
mation Sciences, and China Communications. He is a Distinguished Lecturer
of IEEE Communications Society.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:00:46 UTC from IEEE Xplore.  Restrictions apply.
