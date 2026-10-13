---
title: "Integrated Sensing and Communications for Low-Altitude Economy A Deep Reinforcement Learning Approach"
zotero_key: "4ZKUQ3NN"
pdf_key: "ZMNWZNSB"
doi: "10.1109/twc.2025.3583950"
collection: "ISAC"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# Integrated Sensing and Communications for Low-Altitude Economy A Deep Reinforcement Learning Approach — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

arXiv:2412.04074v3  [cs.NI]  2 Jan 2025
1
Integrated Sensing and Communications for
Low-Altitude Economy: A Deep Reinforcement
Learning Approach
Xiaowen Y e, Y uyi Mao, Senior Member , IEEE, Xianghao Y u, Senior Member , IEEE, Shu Sun, Member , IEEE,
Liqun Fu, Senior Member , IEEE, and Jie Xu, Fellow, IEEE
Abstract—This paper studies an integrated sensing and com-
munications (ISAC) system for low-altitude economy (LAE),
where a ground base station (GBS) provides communication
and navigation services for authorized unmanned aerial veh icles
(UA Vs), while sensing the low-altitude airspace to monitor the
unauthorized mobile target. The expected communication su m-
rate over a given ﬂight period is maximized by jointly optimi zing
the beamforming at the GBS and UA Vs’ trajectories, subject t o
the constraints on the average signal-to-noise ratio requi rement
for sensing, the ﬂight mission and collision avoidance of UA Vs,
as well as the maximum transmit power at the GBS. Typically,
this is a sequential decision-making problem with the given
ﬂight mission. Thus, we transform it to a speciﬁc Markov
decision process (MDP) model called episode task. Based on
this modeling, we propose a novel LAE-oriented ISAC scheme,
referred to as Deep LAE-ISAC (DeepLSC), by leveraging the
deep reinforcement learning (DRL) technique. In DeepLSC,
a reward function and a new action selection policy termed
constrained noise-exploration policy are judiciously des igned to
fulﬁll various constraints. To enable efﬁcient learning in episode
tasks, we develop a hierarchical experience replay mechani sm,
where the gist is to employ all experiences generated within each
episode to jointly train the neural network. Besides, to enh ance
the convergence speed of DeepLSC, a symmetric experience
augmentation mechanism, which simultaneously permutes th e
indexes of all variables to enrich available experience set s, is
proposed. Simulation results demonstrate that compared wi th
benchmarks, DeepLSC yields a higher sum-rate while meeting
the preset constraints, achieves faster convergence, and i s more
robust against different settings.
Index Terms—Low-altitude economy (LAE), integrated sensing
and communications (ISAC), joint beamforming and trajecto ry
design, deep reinforcement learning (DRL).
I. I NTRODUCTION
L
OW-altitude economy (LAE), composed of various low-
altitude ﬂight activities involving unmanned and manned
Xiaowen Y e and Xianghao Y u are with the Department of Electri cal
Engineering, City University of Hong Kong, Hong Kong, China . (E-mail: xi-
aowen.ye@cityu.edu.hk, alex.yu@cityu.edu.hk). ( Corresponding author: Xi-
anghao Yu.)
Y uyi Mao is with the Department of Electrical and Electronic Engineering,
The Hong Kong Polytechnic University, Hong Kong, China. (E- mail: yuyi-
eie.mao@polyu.edu.hk).
Shu Sun is with the Department of Electronic Engineering and the Coop-
erative Medianet Innovation Center, Shanghai Jiao Tong Uni versity, Shanghai
200240, China. (E-mail: shusun@sjtu.edu.cn).
Liqun Fu is with the School of Informatics, Xiamen Universit y, Xiamen,
China. (E-mail: liqun@xmu.edu.cn).
Jie Xu is with the School of Science and Engineering(SSE), th e Shenzhen
Future Network of Intelligence Institute (FNii-Shenzhen) , and the Guangdong
Provincial Key Laboratory of Future Networks of Intelligen ce, The Chinese
University of Hong Kong, Shenzhen, China. (E-mail: xujie@c uhk.edu.cn).
aircraft, such as unmanned aerial vehicles (UA Vs) and elect ric
vertical take-off and landing (eVTOL), has gained widespre ad
attention from academia and industry [1]. It is expected tha t
LAE could support a wide variety of important applications,
including but not limited to transportation, environmenta l mon-
itoring, tourism, and agriculture [2]. However, the succes sful
implementation of LAE requires the strictly safe operation
(e.g., collision-free) of all aircraft, especially in the p resence of
massive aircraft and unauthorized targets [3]. Therefore, it is
imperative to provide seamless communication and navigati on
for authorized aircraft, as well as ubiquitous surveillanc e of
unauthorized targets in the low-altitude airspace.
One possible solution that could facilitate the implemen-
tation of LAE is to jointly adopt wireless communications
and radar sensing technologies. Conventionally, these two
technologies are designed and implemented independently.
This, however, results in low spectrum utilization and expe n-
sive hardware overhead. Fortunately, integrated sensing a nd
communications (ISAC), a key technique for next-generatio n
wireless networks, is capable of simultaneously performin g
wireless communications and radar sensing based on the com-
mon spectrum resource and hardware infrastructures [4]. Wi th
ISAC, the ground base station (GBS) provides communication
and navigation services for authorized aircraft, while sen sing
the low-altitude airspace to monitor unauthorized targets .
A. Related W ork
Currently, there have been substantial bodies of works
studying the integration of aircraft (speciﬁcally UA Vs) an d
ISAC systems, which can be divided into two main paradigms
according to the role that UA Vs play [5]–[35]. The ﬁrst
paradigm is referred to as UA V -assisted ISAC services, wher e
each UA V operates as a new aerial platform (e.g., aerial base
station or relay) to serve ground users. For example, toward s
the goal of minimizing the age of information of sensed
data, a joint extremum principles and dynamic programming
scheme was proposed in [5] to optimize the UA V power and
trajectory, whereas in [6], a successive convex approximat ion
(SCA) iterative method was used to reﬁne the UA V trajectory
and time allocation for both communication and sensing.
These two works, however, were merely concerned about
the communication performance, while ignoring the sensing
requirement. By contrast, the works [7]–[11] considered bo th
simultaneously. Speciﬁcally, in [7], Wang et al. investigated
a dual-function multi-UA V wireless network, in which the

2
sum-rate was maximized by jointly optimizing the UA V loca-
tion, transmit power, and user association under the Cram´ e r-
Rao bound constraint. In [8], Chang et al. proposed a joint
scheduling strategy for control, communication, and sensi ng in
millimeter-wave UA V networks, such that the communication
and sensing requirements can be met while maintaining good
control performance. By jointly employing the alternating
optimization and SCA method, the authors of [9] proposed a
joint UA V deployment and power control scheme to maximize
the minimum detection probability, whilst the authors of
[10] optimized the deployment and joint communication and
sensing precoder to balance communication rate and sensing
accuracy. Besides, the potential of UA Vs for physical layer
security provisioning in ISAC systems was explored in [11].
The aforementioned research, however, mainly focused on
the ISAC in quasi-static UA V scenarios, without exploiting
the controllable mobility over the three-dimensional (3D)
space. To explore the advantages of UA V mobility, literatur e
[12]–[24] studied the UA V trajectory optimization for ISAC
applications. To be speciﬁc, by optimizing the UA V trajecto ry,
the real-time secrecy rate was maximized in [12], while
the UA V propulsion consumption was minimized in [13].
Furthermore, in [14]–[24], other variables are jointly opt imized
with the UA V trajectory, e.g., UA V transmit power and user
scheduling [14]–[17], bandwidth allocation for users [18] ,
UA V -user association [19], UA V transmit beamforming [20]–
[23], and ofﬂoading task size [24]. These above works were
dedicated to the case with a single UA V and thus exempted
from the UA V collision-avoidance constraint. On the contra ry,
investigations [25] and [26] focused on a multi-UA V -assist ed
ISAC network, where the trajectory of individual UA Vs and
their association with users are jointly optimized subject to the
minimum collision avoidance distance. In addition, to circ um-
vent the high computational complexity and poor adaptabili ty
of conventional optimization methods, several intelligen t UA V -
aided ISAC schemes were developed in [27]–[33].
The inherent limitation of the ﬁrst paradigm is that it is not
applicable to terrestrial ISAC oriented towards LAE, where au-
thorized UA Vs (as communication users) with missions (e.g. ,
cargo deliver) and unauthorized targets (as sensing target s) are
located at low altitudes in the 3D space. Instead, the second
paradigm, which focuses on the use of GBS to provide aircraft
with ISAC services, aligns better with LAE-oriented ISAC.
Currently, there are few studies on this paradigm [34], [35] .
In particular, the authors of [34] considered a system with
one GBS and multiple UA Vs, where a novel dual identity
association-based ISAC approach was designed to enable fas t
and accurate beamforming towards different UA Vs. Unlike
[34], the authors of [35] studied a networked ISAC system,
where multiple GBSs cooperatively transmit uniﬁed ISAC
signals to communicate with multiple authorized UA Vs and
concurrently detect unauthorized targets. In prior works, the
unauthorized target is presumed to be static, and the iterat ive
alternating algorithm that focuses on one instantaneous op ti-
mization problem is adopted to optimize different variable s in
a separate manner. In practical LAE-oriented ISAC systems,
however, (i) the locations of unauthorized targets are high ly
dynamic; (ii) the channel state information (CSI) is time-
correlated since the next locations of the target and UA Vs
depend on their current locations; and (iii) the beamformin g
and trajectory are jointly optimized subject to UA Vs’ ﬂight
missions that last for a long period. As a result, the LAE-
oriented ISAC problem is a typical long-term optimization
problem, in which all variables should be jointly optimized
with respect to the average system performance during the
ﬂight mission.
Such a problem can be transformed and solved under the
Markov decision process (MDP) model, in which an agent
continuously optimizes its decisions towards the given lon g-
term objective. Generally, an efﬁcient solution for MDP can
be derived through a simple dynamic programming algorithm,
if the accurate state transition (e.g., the CSI transition) of the
system is available [36]. However, in practical LAE-orient ed
ISAC systems, the mobility model of the target is difﬁcult to
obtain, in the sense that the state transition of the system i s
unknown. Fortunately, model-free deep reinforcement lear ning
(DRL) excels at ﬁnding an efﬁcient strategy for MDP in
unknown environments, through a large number of trial-and-
error interactions and reward-decision iterations [37]. I n this
regard, DRL is a promising candidate for solving the long-term
optimization problem in LAE oriented-ISAC systems . So far,
DRL has shown its powerful capability in solving a wide range
of sequential decision-making problems, e.g., robot contr ol,
game playing, and wireless communications [38]. To the best
of our knowledge, DRL has not been explored yet in existing
works to design the LAE-oriented ISAC scheme.
B. Contributions
In this paper, we investigate an LAE-oriented ISAC system
with the objective of maximizing the expected communication
sum-rate of all UA Vs over a given ﬂight period, by jointly
optimizing the GBS’s beamforming and authorized UA Vs’
trajectories. In addition, the constraints, including the average
sensing signal-to-noise ratio (SNR) requirement for monit or-
ing the mobile target, the UA Vs’ ﬂight missions, the UA V
collision avoidance, and the GBS’s maximum transmit power,
are considered. Overall, the main contributions of this pap er
are summarized below:
1) A problem is formulated as a speciﬁc MDP model termed
episode task [36] to jointly optimize the GBS’s beamforming
and UA Vs’ trajectories, where each ﬂight period is consider ed
as an episode and the ﬂight mission corresponds to the
episode task. To ﬁnd an efﬁcient solution, we propose an
ISAC scheme capable of supporting LAE, referred to as Deep
LAE-ISAC (DeepLSC), by exploiting the DRL technique.
The underpinning algorithm in DeepLSC is deep deterministi c
policy gradient (DDPG) [39], since the formulated problem
involves continuous control variables. The salient advant ages
of DeepLSC are that it (i) does not require the prior mobility
information of the target and (ii) well caters the long-term
optimization objective of the LAE-oriented ISAC system.
2) A new action selection policy, termed constrained noise-
exploration policy, is developed for DeepLSC to guarantee t he
ﬂight mission and maximum power constraints. The gist is to
(i) introduce a scaling factor to reﬁne the beamforming from
the conventional noise-exploration policy [39] and (ii) de cide

3
whether to follow the trajectory decision of the convention al
noise-exploration policy or choose straight ﬂight based on the
real-time locations of UA Vs. In addition, we judiciously design
a reward function for action evaluation, which incorporate s the
communication sum-rate, average sensing SNR requirement,
and collision avoidance into the learning process.
3) A new hierarchical experience replay mechanism is pro-
posed for DeepLSC to train the deep neural network (DNN).
Speciﬁcally, in the traditional experience replay mechani sm
[40], since different experiences generated within a speci ﬁc
episode are collected and utilized in a separate manner,
they cannot be guaranteed to appear together during trainin g.
DeepLSC, however, is tailored for episode tasks. To efﬁcien tly
learn from the episode task, the hierarchical experience re play
mechanism employs the experience sets, each containing all
experiences within an episode, to jointly train the DNN.
4) We devise a symmetric experience augmentation mech-
anism to promote the convergence speed of DeepLSC. To be
speciﬁc, DeepLSC is an online learning scheme, in the sense
that the agent (i.e., the GBS) needs a lot of trial and error wi th
the environment to generate sufﬁcient experiences for trai ning.
Consequently, an efﬁcient joint beamforming and trajector y
policy takes a long time to learn. To circumvent this issue,
the symmetric experience replay mechanism generates more
new experience sets by simultaneously permuting the indexe s
of all variables, based on a prior experience set.
5) Extensive experimental results show that DeepLSC out-
performs various schemes including the DeepLSC-CNE (i.e.,
DeepLSC with the conventional noise-exploration policy [3 9]),
DeepLSC-CER (i.e., DeepLSC with the conventional experi-
ence replay mechanism [40]), and AC2 (i.e., the actor-criti c
algorithm [36] with the constrained noise-exploration pol icy),
in terms of both communication and sensing performance.
Compared with DeepLSC-w (i.e., DeepLSC without sym-
metric experience augmentation), DeepLSC converges faste r.
Furthermore, under different simulation setups, DeepLSC i s
more robust than these baselines.
C. Organization and Notations
Organization: The remainder of this paper is below. Section
II describes the system model. Section III presents the prob lem
formulation and transformation. The DeepLSC scheme is
detailed in Section IV, and numerical results are discussed
in Section V. Finally, Section VI concludes this paper.
Notations: V ectors (matrices) are denoted by boldface lower
(upper) case letters, CN ×M represents the space of N×M
complex matrices,|·| represents the absolute value, ||·|| 2 rep-
resents the 2-norm, E[·] represents the statistical expectation,
while Tr (·), (·)T , and (·)H represent the trace, transpose, and
conjugate transpose, respectively.
II. S YSTEM MODEL
Consider an LAE-oriented ISAC system shown in Fig. 1,
where one GBS equipped with N transmit/receive-antennas
servesM single-antenna authorized UA Vs for downlink com-
munications and simultaneously detects a low-altitude tar get
(e.g., unauthorized UA V). The location of the GBS is repre-
sented by the 3D Cartesian coordinate (b, 0) with b = [ˆx, ˆy]
GBS 
: ۶ୱ
UA V ͳ
Target 
UA V ͳ
UA V ݉
UA V ݉
: Trajectory 
: ܐ௠
Fig. 1. LAE-oriented ISAC systems.
denoting the horizontal coordinate, and the location of the
target is (g,H Tar), wherein g = [˜x, ˜y] andHTar> 0 denote the
horizontal and vertical coordinates, respectively. The UAVs are
indexed by m∈M ={1, 2,··· , M}, and each UA Vm ﬂies
at a pre-assigned altitude Hm with the mission of transporting
cargo from a source to a destination within a given time
duration of ∆T. In other words, the initial and ﬁnal locations
of UA Vm are predetermined as (uIm,Hm) and (uFm,Hm),
respectively, wherein uIm = [xIm,y Im] and uFm = [xFm,y Fm].
A. UA V/T arget Trajectory Model
We discretize the duration ∆T into T time slots, indexed
by t∈T ={1, 2,··· , T}. The slot duration ∆t = ∆ T/T
is sufﬁciently small, such that the locations of the target a nd
UA Vs can be assumed as unchanged within each time slot.
1) UA V Flight Model: Within a speciﬁc time period ∆T,
the trajectory of UA V m is a (T + 1)-length sequence, i.e.,
{(uIm,Hm), (um(t),Hm)|t = 1 , 2,··· , T} with um(t) ≜
[xm(t), ym(t)]. We assume that UA V m ﬂies at a constant
speedvm. Thus, its ﬂight distance in one time slot is given as
vm∆t, leading to the following constraint:
‖um(t + 1)− um(t)‖2 =vm∆t,∀m∈M, t∈T . (1)
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
2) T arget Mobility Model: For simplify, we assume that the
target moves at a constant speed vTar and its ﬂight distance

4
within one time slot is vTar∆t. To better model the mobility
of a realistic target, a Gauss-Markov process is introduced to
capture the temporal correlation of the movement direction
[41]. Let φ(t) and ϕ(t) denote the azimuth and elevation
angles at which the target moves at time slot t, respectively.
They are modeled as
{
φ(t) = µaφ(t− 1) + (1−µa)ξa +
√
1−µa2 ˆφ(t),
ϕ(t) = µeϕ(t− 1) + (1−µe)ξe +
√
1−µe2 ˆϕ(t), (5)
where µa∈ [0, 1] and µe∈ [0, 1] are the time correlation coef-
ﬁcients, modulating the degree of temporal dependency. For
example, µa = 0 indicates that the target moves at a fully
random azimuth angle, while µa = 1 indicates that the hori-
zontal movement direction is unchanged. Parameters ξa andξe
are asymptotic means of φ(t) andϕ(t), respectively, as t→∞.
Parameters ˆφ(t) and ˆϕ(t) are independent, uncorrelated, and
stationary Gaussian processes with N (0,σ 2φ) andN (0,σ 2ϕ),
respectively, whereinσφ andσϕ correspond to the asymptotic
standard deviations.
Hence, given φ(t) and ϕ(t), the location of the target at
time slot t + 1 can be obtained as
{
g(t + 1) = g(t) +vTar∆tcos (ϕ(t)) [cos (φ(t)), sin (φ(t))],
HTar(t + 1) = HTar(t) +vTar∆tsin (ϕ(t)).
(6)
B. Channel Model
Denote hs(t)∈ CN ×1 by the channel vector between the
GBS and the target at time slot t. The bidirectional channel
matrix that the signal experiences from forward transmissi on to
echo can be represented as Hs(t) = hs(t)hTs (t)∈ CN ×N . Fur-
thermore, let Hc(t) = [ h1(t), h2(t),··· , hM (t)]∈ CN ×M
denote the channel matrix between the GBS and all UA Vs
at time slot t, wherein hm(t)∈ CN ×1 is the channel vector
between the GBS and UA V m.
Due to the relatively high altitude of the target and UA Vs,
there generally exists a strong line-of-light (LoS) link be tween
the GBS and them. As such, the air-ground communica-
tion links are dominated by the LoS channel. For example,
hm(t),∀m∈M is represented as
hm(t) =
√
ωm(t)c (ψm(t)), (7)
where
ωm(t) = L0
D0
(‖b− um(t)‖22 +H 2m)ςm
is the path loss with L0 as the path loss constant at reference
distance D0, and ςm as the path loss exponent. Furthermore,
c (ψm(t)) = [1 ,e2π dλ cosψm(t),··· ,e2π dλ (N −1) cosψm(t)]T is
the steering vector with ψm(t) being the angle of departure
(AoD) at the GBS, given by
ψm(t) = arccos Hm√
‖b− um(t)‖22 +H 2m
. (8)
A similar channel model is adopted for hs(t).
C. Signal Model
In each time slot t, the transmit signal of the GBS is a
weighted sum of communication symbols and radar probing
signals [4], which is expressed as
x(t) = Wc(t)vc(t) + Ws(t)vs(t), (9)
where vc(t)∈ CM×1 is the communication symbol with
E{vc(t)vHc (t)} = IM , vs(t)∈ CN ×1 is the radar probing
signal with E{vs(t)vHs (t)} = IN , Wc(t)∈ CN ×M is the
communication precoding matrix, and Ws(t)∈ CN ×N is the
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
hTm(t)x(t) +nm(t), where nm(t)∼CN (0,σ 2m) is the additive
white Gaussian noise (AWGN), and σ2m is the noise power. As
a result, the communication signal-to-interference-and- noise
ratio (SINR) at UA V m is given by
SINRm(t) =
⏐⏐hTm(t)wm(t)⏐⏐2
N +M∑
k=1,k ⁄=m
|hTm(t)wk(t)|2 +σ2m
, (11)
where wm is the m-th column of W. Accordingly, the sum-
rate of all UA Vs can be calculated by
Rtotal(t) =
M∑
m=1
log2 (1 + SINRm(t)). (12)
2) Sensing Model: As shown in Fig. 1, the radar probing
signal is reﬂected by the target to GBS via the direct and
reﬂected/refracted links. Thus, the echo signal from the ta rget
to GBS is expressed as ys(t) = Hs(t)x(t) + nB(t), wherein
nB(t)∼CN (0N, σ2b IN ) is the AWGN, and σ2b is the noise
power. Furthermore, the sensing SNR of the target is given by
SNRTar(t) =
E
{
|Hs(t)W(t)v(t)|2
}
σ2b
= Tr
(
WH (t)HHs (t)Hs(t)W(t))
σ2b . (13)
III. P ROBLEM FORMULATION AND TRANSFORMATION
This section formulates the joint beamforming and trajec-
tory optimization problem as a constrained sequential deci sion
problem. Then, it is transformed to an unconstrained proble m
with a judiciously designed reward function.
A. Problem F ormulation
Our objective is to maximize the expected sum-rate of all
UA Vs over T time slots while satisfying the sensing SNR
requirement, ﬂight mission, collision avoidance, and maxi mum
transmit power constraints. The communication beamformin g
Wc(t), sensing beamforming Ws(t), and trajectory um(t) of

5
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
with the expectation in (14a) taken over varying target mo-
bility, which is unknown to the GBS. Besides, constraint
(14b) speciﬁes the ﬂight constraints of the target and UA Vs;
constraint (14c) guarantees the average SNR requirement Γmin
for sensing the target [3]; and constraint (14d) limits the
transmit power of the GBS to Pmax.
Typically, problem (14) is a sequential decision-making
problem, which can be transformed and solved under the
MDP model [36]. This corresponds to one particular MDP
form, referred to as episode task [36], where the task ends
in a terminal status (i.e., the ﬁnal location of the UA V)
that separates the agent-environment interactions into ep isodes
with each containing T time slots. Different episodes are
independent of each other, and a new episode will start from
the starting status (i.e., the initial location of the UA V) a fter
each episode ends. Besides, within each episode, the agent h as
to satisfy the preset constraints (14b)–(14d). Thus, probl em
(14) is actually a constrained episode task . Generally, an
efﬁcient solution that can handle this problem is hard to der ive
[36], which therefore motivates us to transform problem (14 )
into an unconstrained MDP problem.
B. Unconstrained MDP Transformation
We deﬁne the basic MDP elements, including agent, en-
vironment, action, state, transition probability, and rew ard
function, as follows.
1) Agent and Environment O: The GBS is considered as
the agent, while the target, UA Vs, and wireless channels are
treated as the environment. In each time slot, the GBS ﬁrst
decides an efﬁcient joint beamforming and trajectory strat egy.
Afterward, it performs the communication beamforming to
provide data transmission and navigation for all UA Vs, whil e
monitoring the mobile target via the sensing beamforming.
2) Action Space A: The action space A is composed of
all possible actions that could be potentially executed by
the agent. In the light of (14), the agent needs to decide
three types of sub-actions, including the communication be am-
forming Wc(t), the sensing beamforming Ws(t), and all
UA Vs’ movement directions au(t), in each time slot. Specif-
ically, the sub-action au(t) is represented as [au,1(t), au,2(t),
··· , au,M (t)], where au,m(t) is the movement direction of
UA Vm at time slot t. With au,m(t), the horizontal location of
UA Vm at time slot t + 1 becomes um(t + 1) = [ xm(t)+
vm∆t cos(au,m(t)), ym(t) + vm∆t sin(au,m(t))]. In Wc(t),
Ws(t), and au(t), each element is a continuous variable to
be optimized by the agent. Overall, the action of the agent at
time slot t can be denoted by A(t) = ( Wc(t), Ws(t), au(t)).
3) State Space S: The state space S is a set of all possible
states, each of which contains enough useful information fo r
decision-making. To be speciﬁc, at time slot t, the observable
state S(t) is determined by the communication CSI Hc(t),
the sensing CSI Hs(t), and all UA Vs’ locations U(t) =
[u1(t), u2(t),··· , uM (t)], which can be represented as
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
reward function, we address constraints (3), (4), and (14c) ,
apart from the optimization objective (14a). In Section IV - B,
we will detail how to guarantee constraints (2) and (14d) fro m
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
to satisfy the preset sensing SNR requirement Γmin.
In this regard, if the average sensing SNR over the
whole ﬂight period (i.e., episode) 1 is less than Γmin, a
penalty−δ2(Γmin−∑Tt=1SNRTar(t)/T ) should be added
to r(t + 1) , wherein δ2 > 0 is the penalty coefﬁcient
corresponding to the sensing SNR requirement constraint.
As such, the agent can be encouraged to optimize its
strategy, so as to meet the average SNR requirement for
sensing the target in subsequent episodes.
Overall, the reward function of the agent is designed as
(16). Note that since ∑Tt=1SNRTar(t)/T is not revealed until
the end of each episode, the rewards {r(t + 1)|t = 1, 2,··· ,
T} are only available at the agent in time slot t =T .
Thus far, we have reformulated problem (14) as an uncon-
strained MDP problem. At each time slot, given the system
state S(t), the agent makes an decision A(t) to interact
with the environment by trial-and-error according to a poli cy
π(A(t)|S(t)). Afterward, the environment feeds back a reward
r(t + 1) to the agent, and enters a new state S(t + 1) with
probability p (S′|S, A). Over the lifetime, the agent aims to
1This paper uses the terms “ﬂight period” and “episode” inter changeably.

6
r(t + 1) =



−δ1−δ2
(
Γmin− 1T T∑t=1SNRTar(t)), if (3) or (4) is not met and (14c) is not met ,
−δ1, if (3) or (4) is not met but (14c) is met ,
Rtotal(t)−δ2
(
Γmin− 1T T∑t=1SNRTar(t)), if (3) and (4) are met but (14c) is not met ,
Rtotal(t), if (3), (4), and (14c) are all met .
(16)
search for an optimal policy π∗ (i.e., the optimal joint GBS’s
beamforming and UA Vs’ trajectories policy) to maximize the
cumulative reward G(t) = ∑Tl=tr(l + 1) [36]. Furthermore,
the action-value that reﬂects the expected cumulative rewa rd
at state S(t) given A(t) is chosen can be deﬁned as
Qπ (S(t), A(t)) = Eπ [G(t)|S(t), A(t)]. (17)
In the above MDP problem, if the channel model is ac-
curately known, the state transition probability p (S′|S, A)
is easy to obtain. At this time, this MDP problem can be
well tackled by dynamic programming. However, the mobility
model of the target is unavailable at the GBS, which motivate s
the use of model-free DRL techniques.
IV. D EEP LSC S CHEME
In this section, we present DeepLSC, a DRL-enabled ISAC
scheme, to solve the formulated MDP problem. The under-
pinning algorithm in DeepLSC is DDPG [39], and the major
reasons why we favor DDPG are as follows: (i) Problem
(14) involves continuous control variables, whereas value -
based DRL methods, e.g., deep Q-network (DQN) [37], are
limited to discrete control problems. (ii) Conventional po licy-
based approaches, e.g., policy gradient [42], are capable o f
solving continuous control issues, but they suffer from uns table
learning and slow convergence. DDPG, which integrates the
advantages of value-based and policy-based methods, can
effectively circumvent the above challenges. Fig. 2 shows t he
DeepLSC framework, and the details are elaborated below.
A. Actor-Critic Architecture
There are two types of DNNs in DeepLSC, referred to as
actor and critic. Each of them consists of two DNNs with the
same structure but different parameters, i.e., the eval-ac tor with
parameter Θa, the target-actor with parameter Θ−a , the eval-
critic with parameter Θc, and the target-critic with parameter
Θ−c . As shown in Fig. 2, all DNNs share the same structure,
i.e., one input layer, one gated recurrent unit (GRU) layer,
one fully connected (FC) layer, and one output layer, but the ir
roles are different.
1) Eval-Actor: At each time slot, the eval-actor makes
the temporary joint beamforming and trajectory decision
πa (S(t); Θa) based on the state S(t). Speciﬁcally, since the
DNN cannot process complex numbers, we divide Hc(t) and
Hs(t) into the corresponding real and imaginary parts, and
concatenate them together with U(t). After obtaining the
preprocessed state S(t), the input layer delivers it into the
GRU layer. Afterward, the GRU layer extracts the underlying
temporal correlation from the input sequence and imports it
into the FC layer for analysis. 2 Since DNNs cannot generate
complex numbers, it is not feasible to directly get a matrix w ith
sizeN×M as Wc(t) and a matrix with size N×N as Ws(t).
Thus, after receiving the processed information from the FC
layer, the output layer generates πa (S(t); Θa) containing three
vectors, wherein the ﬁrst vector with size 2NM is related to
the temporary communication beamforming, the second vecto r
with size 2N 2 is related to the temporary sensing beamform-
ing, and the last vector with size M is the temporary trajectory
decision. In particular, with the ﬁrst vector in πa (S(t); Θa), the
temporary communication beamforming can be generated via
element-wise concatenation, i.e., the ﬁrst NM elements are
treated as the real parts of individual elements in the tempo rary
communication beamforming and the remaining elements are
the corresponding imaginary parts. The temporary sensing
beamforming can also be generated in a similar way. On this
basis, we design a new action selection policy to determine
the real joint beamforming and trajectory decision A(t), which
will be detailed in Section IV -B.
2) Eval-Critic: The eval-critic is responsible for evaluating
the action-value Q(S(t), A(t); Θc) of the pair (S(t), A(t)).
In particular, after acquiring the action A(t) from the eval-
actor, the agent feeds it together with S(t) to the eval-critic
for action-value evaluation. To cater to the input of the DNN ,
the eval-critic preprocesses each element in both S(t) and
A(t) in a similar way as the eval-actor. Then, the evaluated
action-value will be used to compute the action gradient,
i.e.,∇A(t)Q
(
S(t), A(t); Θc
)
, so as to train the eval-actor as
detailed in Section IV -C.
3) T arget-Actor and T arget-Critic: The role of both the
target-actor and the target-critic is to compute the target value
ofQ(S(t), A(t); Θc) when the eval-critic is trained. To further
enhance the stability of the algorithm, the parameters of th e
eval-actor and the eval-critic are fully updated, whereas t he
parameters of the target-actor and the target-critic are pa rtially
updated via the soft-update approach in Section IV -E.
B. Constrained Noise-Exploration Policy
Given the optimization objective (14), the eval-actor aims to
ﬁnd the optimal policy of joint beamforming and trajectory π∗a .
Recall that in Section III-B, constraints (3), (4), and (14c ) have
been considered from the perspective of reward design. We
now illustrate how to guarantee the maximum power constrain t
(14d) and the ﬂight mission constraint (2) from the perspect ive
of action selection. Speciﬁcally, according to constraint s (14d)
and (2), the signal power used for communication and sensing
2Our previous work [38] has demonstrated the efﬁciency of GRU in ad-
dressing the problem with complex temporal correlations in wireless networks.

7
݁ሺͳሻ
݁ሺʹሻ
ڮ
݁ሺܶሻ
݁ሺͳሻ
݁ሺʹሻ
ڮ
݁ሺܶሻ
ڮ
ڮ
ڮ
ڮ
ڮ
ڮ
ڮ
ڮ
Experience sets 
Experience augmentation 
Target-actor 
Eval-actor 
Eval-critic 
Target-critic 
Output layer 
Experience buffer 
Sample 
Train 
DeepLSC
Refine 
Mini-batch B
Environment 
Input layer GRU layer FC layer Output layer 
Input layer GRU layer FC layer 
ڮ
ڮ
ڮ
ڮ
Input layer GRU layer FC layer Output layer 
Input layer GRU layer FC layer 
ߨୟି ܁ݐ ൅ ͳ Ǣ દ ୟି
Action-value 
Reward ݎሺݐ ൅ ͳሻ
Output layer Constrained noise-
exploration policy 
Soft-update 
Soft-update 
ۯሺݐሻߨୟ ܁ݐ Ǣ દ ୟ
State ܁ሺݐሻ
Action 
ۯሺݐሻ
Target-value 
Train 
Refine 
GBS's beamforming 
܅ୡሺݐሻ and ܅ୱሺݐሻ
UA Vs' trajectories 
ࢇ୳ሺݐሻ
Fig. 2. DeepLSC framework, including the execution phase an d the training phase. During the execution phase, based on S(t), the eval-actor outputs the
temporary joint beamforming and trajectory decision πa(S(t), Θa), which is reﬁned by the constrained noise-exploration poli cy. During the training phase,
some experience sets sampled from the experience buffer are augmented to form the mini-batch for training the actor-cri tic architecture.
cannot exceed the preset maximum value Pmax, and the trajec-
tory should ensure all UA Vs to complete their ﬂight missions
within each episode. Given the temporary joint beamforming
and trajectory decision πa (S(t); Θa) from the eval-actor based
on S(t), the conventional noise-exploration policy in DDPG
[39] generates a reﬁned decision by adding randomness, i.e. ,
(ac(t), as(t), au(t)) = πa (S(t); Θa) + (dc(t), ds(t), du(t)),
(18)
where ac(t) and as(t) are vectors with size 2NM and 2N 2,
respectively. V ectordi(t),∀i∈{c, s, u}, has the same size as
ai(t), each element of which is Gaussian distributed with zero
mean and variance σ2i (t). By doing so, the agent is encouraged
to explore random actions for better solutions. Generally, too
much exploration is unnecessary once an efﬁcient solution
is learned. Hence, we introduce a decay factor κ∈ (0, 1) to
reduce σ2i (t) over time. Denote the initial variances by σ2i,init,
then σ2i (t) at time slot t can be represented as σ2i,initκt.
The conventional noise-exploration policy, however, only
improves the exploration capability of the agent, while ig-
noring constraints (14d) and (2). To cope with this issue,
we develop a new action selection policy for DeepLSC,
referred to as constrained noise-exploration policy . The gist
is to (i) introduce a scaling factor to reﬁne the beamforming
decided by the conventional noise-exploration policy, so a s
to meet constraint (14d), and (ii) decide whether to use the
conventional noise-exploration policy based on the real-t ime
location of each UA V , so as to satisfy constraint (2). The details
are elaborated below.
1) Decision-Making of Communication and Sensing Beam-
forming: As a ﬁrst step, with ac(t) and as(t), two matrices
Ac(t)∈ CN ×M and As(t)∈ CN ×N can be generated via
element-wise concatenation, i.e., the ﬁrst NM (N 2) elements
of ac(t) (as(t)) are treated as the real parts of individual
elements in Ac(t) (As(t)) and the remaining elements are
the corresponding imaginary parts. Thereafter, to obtain t he
communication beamforming Wc(t) and the sensing beam-
forming Ws(t) that satisfy the preset power constraint (14d),
a scaling factor, deﬁned as ǫ = Pmax/
(
Tr
(
AHc (t)Ac(t)) +
Tr
(
AHs (t)As(t)), is introduced to reﬁne Ac(t) and As(t) as
follows:
Wc(t) =√ǫAc(t), Ws(t) =√ǫAs(t). (19)
2) Decision-Making of UA Vs’ Trajectories: Within each
episode, all UA Vs’ trajectories{au(t) = [au,1(t), au,2(t),··· ,
au,M (t)]|t∈T} decided by the agent should fulﬁll the pre-
set ﬂight mission. For this purpose, the constrained noise-
exploration policy that decides au,m(t) limits the movement
directions of UA Vm in the last T−t−1 time slots within each
episode: at time slot t, if the minimum required number of time
slots from the current location to reach the desired locatio n is
not less than T−t− 13, UA V m has to ﬂy in a straight
line toward the desired location uFm, i.e., au,m(t) = “straight
ﬂight”. Within other time slots, the movement decision au,m(t)
can be directly determined through the conventional noise-
exploration policy, in the sense that the agent is not subjec t to
constraint (2) and thus can derive more efﬁcient movement
directions for UA Vs towards other optimization objectives .
Overall, the movement decision of UA V m at time slot t is
given as follows:
au,m(t) =
{
au,m(t), if⌈ ‖um(t)−uFm‖2vm∆t ⌉<T −t− 1,
straight ﬂight, otherwise,
(20)
where⌈x⌉ represents the smallest integer not less than x.
3Intuitively, to complete the ﬂight mission, UA V m only needs to ﬂy in a
straight line towards the desired location uFm when the number of its available
time slots is equal to the minimum required number of time slo ts. However,
there are some special cases. For example, the movement dist ance of UA V m
in each time slot is 1 m, the number of time slots available to U A Vm at time
slot t is 11, and at least 10 time slots are required to reach the desi red location
uFu,m. If UA V m moves in the opposite direction of the desired location at
time slot t, the number of time slots available to UA V m at time slot t + 1
will be 10 but at this time at least 11 time slots will be requir ed to reach the
desired location. Consequently, UA Vm will never complete the ﬂight mission
in the subsequent time slots. Therefore, in (20), we relax T − t to T − t − 1.

8
C. Hierarchical Experience Replay
Since DeepLSC is developed for episode tasks, all expe-
riences from different time slots within each episode shoul d
be jointly used to train both the eval-actor and the eval-cri tic.
However, in the conventional experience replay mechanism o f
DDPG [40], the experiences generated in different time slot s
are separately gathered and utilized. In other words, durin g
training, the experiences from different time slots within a
speciﬁc episode cannot be guaranteed to appear in full. Cons e-
quently, the agent fails to learn an efﬁcient joint beamform ing
and trajectory strategy in LAE-oriented ISAC systems. To ﬁl l
this gap, a new hierarchical experience replay mechanism is
designed for DeepLSC, which makes use of experience sets
each containing all experiences generated within each epis ode
to train the eval-actor and the eval-critic.
As a ﬁrst step, to store and reuse historical experiences, a
ﬁrst-input-ﬁrst-output (FIFO) experience bufferD with size D
is used. As mentioned in Section III-B, within each episode,
the rewards {r(t + 1)|t = 1 , 2,··· ,T} are not available
until time slot T . Thus, in time slot T of each episode, after
calculating the reward r(t + 1) via (16), the agent collects the
experiencee(t) in the form of (S(t), A(t),r (t + 1), S(t + 1)),
where A(t) = [ Wc(t), Ws(t), au(t)]. With all experiences
generated over the whole episode, a experience set E =
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
S(t + 1),π −a (S(t + 1);
Θ−a); Θ−c) is the target value related to the eval-actor, and π−a
is the policy of the target-actor. Furthermore, by performi ng
the stochastic gradient descent (SGD) algorithm [36], the
parameter Θc is updated as follows:
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
environment. Consequently, an efﬁcient joint beamforming and
trajectory strategy usually takes a long time to derive. If t he ex-
perience set{(S(t), A(t),r (t+1), S(t+1))|t = 1, 2,··· , T}
can be generated based on existing experience sets, the expe -
rience buffer D will effectuate experience augmentation and
greatly boost the convergence speed. Actually, in problem ( 14),
the index of each UA V is artiﬁcially speciﬁed. Thus, in terms
of the system performance, if the indices of different UA Vs
are permuted, the new optimization problem is equivalent to
the original problem [43]. For example, when M = 2 and
N = 2, the communication CSI is given as
Hc(t) =
[ h1,1(t) h1,2(t)
h2,1(t) h2,2(t)
]
. (24)
where hn,m is the channel component of antenna n to UA V
m. If we permute the indexes of UA V 1 and UA V 2, the
communication CSI will be transformed into
Hc(t) =
[
h1,2(t) h1,1(t)
h2,2(t) h2,1(t)
]
. (25)
At this time, if the indexes of UA V 1 and UA V 2 in the com-
munication beamforming Wc(t), the sensing beamforming
Ws(t), the UA Vs’ movement decisions au(t), and the sensing
CSI Hs(t) are synchronously permuted, the new optimization
problem will be equivalent to the original problem.
Inspired by this, we propose the symmetric experi-
ence augmentation mechanism , and the main idea is to
simultaneously exchange the indexes of all variables to
generate more new experience sets. Speciﬁcally, denote
Υ = {{υ1, υ2, υ3,··· , υM}, {υ2, υ1, υ3,··· , υM},··· ,
{υM, υM−1, υM−2,··· , υ1}} by the symmetric group of
ﬁnite integer set F = {υ1, υ2,··· , υM}, where group
elements are bijection of F to itself. Let Ωυi denote the
permutation ofυi. Then the permutation of individual elements
inF can be represented as
Ω =
(
υ1 υ2 ··· υM
Ωυ1 Ωυ2 ··· ΩυM
)
, (26)
where the ﬁrst row is the elements of F , and the second
row is the corresponding permutation under Ω. In the above
example, the permutation is given as Ω =
(
1 2
2 1
)
. Consider
a system with M UA Vs. Under all possible permutations Ω,
there will be a total of M ! group elements in Υ. Besides, to
distinguish the variables before and after the permutation , we
superscript the permuted communication beamforming, sens -
ing beamforming, UA Vs’ movement decisions, communication
CSI, and sensing CSI by Ω as WΩc (t), WΩs (t), aΩu (t), HΩc (t),
and HΩs (t), respectively.
Therefore, the experience sets used for DeepLSC train-
ing can be signiﬁcantly enriched through various permuta-
tions. In particular, given a prior experience set
{
e(i) =
(S(i), A(i),r (i + 1), S(i + 1))|i = 1 , 2,··· , T
}
that is
acquired via the agent-and-environment interaction, M !− 1
new experience sets, i.e.,
{{
eΩ(i)|i = 1, 2,··· , T}|Ω∈ Υ},
can be generated based on the symmetric group Υ. In each
experience set eΩ(i), the elements are given as



SΩ(i) = [ HΩc (i), HΩs (i), UΩ(i)]
AΩ(i) = [ WΩc (i), WΩs (i), aΩu (i)],
rΩ(i + 1) = r(i + 1),
SΩ(i + 1) = [ HΩc (i + 1), HΩs (i + 1), UΩ(i + 1)].
(27)

9
The symmetric mapping, despite increasing the number
of available experience sets, may lead to strong correlatio n
among experience sets [36]. The consequence is that DeepLSC
will fall into overﬁtting and converge to a sub-optimal join t
beamforming and trajectory strategy. Actually, at the beginning
of training, it is difﬁcult to get enough experience sets. In
this case, it is beneﬁcial to augment existing experience se ts
based on the symmetric group Υ. However, as the number
of episodes increases, the experience sets from agent-and-
environment interactions become miscellaneous. As a resul t,
it is no longer necessary to use the symmetric mapping to
enrich the available experience sets. Hence, we introduce a
dynamic augmentation factor ζ∈ (0, 1) to adjust the number
of augmented experience sets as follows:
Λ(ω) =⌊(M !− 1)ζω⌋, (28)
where ⌊x⌋ represents the largest integer less than x, and
ω is the number of training times. During each training,
Ne experience sets, i.e.,
{{
e(i,j )|i = 1 , 2,··· , T
}
|j =
1, 2,··· , Ne
}
, are sampled from D in random, and each of
which is augmented based on Λ(ω) random group elements
(i.e., permutations Ω) of the symmetric group Υ. Thereafter,
all augmented experience sets are merged with Ne original
experience sets to form the mini-batch B for training the eval-
actor and eval-critic.
E. Soft-Update for T arget-Actor and T arget-Critic
The parameters Θ−a and Θ−c of the target-actor and the
target-critic are updated based on the parameters Θa and Θc
of the eval-actor and the eval-critic. A simple approach is t o
update the parameters of the target-actor and the target-cr itic
by Θ−a←Θa and Θ−c←Θc. However, this approach is not
suitable for the continuous control task, since it may lead t o
large prediction errors of the target-actor and the target- critic
[39]. To circumvent this issue, the soft-update approach wa s
proposed in [36], which updates both Θ−a and Θ−c as follows:
Θ−a ←χaΘa+(1−χa)Θ−a , Θ−c ←χcΘc+(1−χc)Θ−c , (29)
where χa∈ [0, 1] and χc∈ [0, 1] are the update factors of the
target-actor and the target-critic, respectively. To be sp eciﬁc,
the soft-update enables the target-actor and the target-cr itic to
maintain a certain continuity during the update process, so as
to better adapt to the continuous control task.
F . Detailed Operations of DeepLSC
Thus far, we have presented the main elements of the
DeepLSC scheme, and Algorithm 1 provides the correspond-
ing pseudocode. Overall, the operations of DeepLSC include :
(i) decide the temporary joint beamforming and trajectory
decisionπa (S(t); Θa) via the eval-actor with the current state
S(t) (lines 7∼8); (ii) decide ac(t), as(t), and au(t) via (18)
(lines 9∼10); (iii) determine the communication beamforming
Wc(t) and the sensing beamforming Ws(t) via (19), and
the movement directions au(t) via (20) (lines 11 ∼13); (iv)
obtain the next state S(t + 1) according to (15) (line 14); (v)
calculate the reward {r(t + 1)|t = 1, 2,··· , T} via (16) at
Algorithm 1 DeepLSC Scheme
1: InitializeN ,M ,T , b, uIm, uFm,{Hm|m∈M} ,vm, vTar.
2: Initialize g(0), HTar(0), Γmin, δ1, δ2, ǫ, κ, αa, αc, Υ, Ω.
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
the end of each episode (line 16); (vi) form the experience se t
{e(t) = ( S(t), a(t), r(t + 1), S(t + 1))|t = 1, 2,··· , T} and
store it in the experience buffer D (line 17); (vii) randomly
sampleNe experience sets from D and augment each of them
with Λ(ω) via (27) (lines 18∼20); (viii) integrate the sampled
and augmented experience sets to form the mini-batch B for
training the eval-actor and the eval-critic via (22) and (23 ),
respectively (lines 21∼23); and (ix) update the parameters of
both the target-actor and the target-critic via (29) (line 1 4).
V. P ERFORMANCE EVALUATION
This section evaluates the performance of DeepLSC based
on Python 3.6 simulation platform, where the Keras library
[44] builds all DNN models.
A. Parameter Settings
1) System Setups: We consider a scenario with one GBS,
one target, and M = 4 UA Vs, unless stated otherwise. The
GBS is located at (0, 0, 0) m, the initial location of the target is
(−60, 100, 70) m, the initial locations of UA Vs are uniformly
chosen from the area [−150,−80] m× [60, 150] m× 80 m,
and the ﬁnal locations of UA Vs are uniformly chosen from
the area [90, 160] m× [50, 160] m× 80 m. The movement
speed of the target and UA Vs are 10 m per time slot, and
the number of time slots within an episode i.e., T , is 40 time
slots, by default. The movement azimuth and elevation of the
target are initialized to 30◦, the time correlation coefﬁcients µa
andµe for the target movement are 0.9, and the corresponding
asymptotic means and standard deviations, i.e., ξa,ξe,σφ, and
σϕ, are 10◦. The number of antennas and the transmit power

10
TABLE I: Algorithm hyper-parameters.
Hyper-parameter Value Hyper-parameter Value
Learning rate ( αa) 1e-4 Reward coefﬁcient ( δ1/δ2) 20/10
Learning rate ( αc) 2e-4 Update coefﬁcient ( χa) 0.0001
Buffer size ( D) 2000 Update coefﬁcient ( χc) 0.0001
Mini-batch size ( Ne) 64 Initial exploration ( ǫinit) 0.9
Decaying rate ( ζ) 0.999 Decaying rate ( κ) 0.999
areN = 6 andPmax = 40 dBm, respectively. The noise power
σ2b and σ2m are−80 dBm, The path loss exponent is 3.2, the
reference distance D0 is 1 m, and the path loss L0 for D0 is
−30 dB. The sensing SNR requirement Γmin is set to 1 dB.
2) Algorithm Setups: The GRU and FC layers of DeepLSC
contain 128 neurons, and TABLE I summarizes the detailed
hyper-parameters. In the simulation, the following scheme s are
considered:
• DeepLSC: This is our designed DRL-based ISAC scheme
for supporting LAE.
• DeepLSC-CNE: This scheme replaces the constrained
noise-exploration policy with the conventional noise-
exploration policy [39]. To meet the signal power con-
straint for communication and sensing, the scaling factor
ǫ is retained in the conventional noise-exploration policy.
• DeepLSC-CER: This scheme replaces the proposed hier-
archical experience replay mechanism with the conven-
tional experience replay mechanism [40].
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
which contains T time slots in which all UA Vs fulﬁll the
preset ﬂight missions. The performance metrics include the
communication sum-rate, the sensing SNR, and whether the
ﬂight missions of all UA Vs are met. Speciﬁcally, the communi-
cation sum-rate at each episode is a short-term average, whi ch
is calculated by averaging ∑Tt=1 Rtotal(t) over the previous
200 episodes; and the short-term average sensing SNR at each
episode is calculated by averaging∑Tt=1 SNRTar(t)/T over the
previous 200 episodes. To ensure the reliability of experim ents,
all simulations run 20 times to obtain the average result.
B. Learning Curves
Fig. 3 and TABLE II provide the communication sum-
rate and average sensing SNR achieved by various schemes,
respectively. As can be seen from Fig. 3, due to the random
mobility of the target, all the curves are in ﬂuctuation. In
other words, in different episodes, the joint beamforming a nd
trajectory strategies derived from the same scheme may be
different. Fig. 4 depicts the ﬂight trajectory of a speciﬁc U A V
under various schemes in the last simulation episode.
Fig. 3. Communication sum-rate achieved by various schemes .
TABLE II: Average sensing SNR [dB] of various schemes.
Scheme A verage sensing SNR Target sensing SNR
DeepLSC 1.12 1.00
DeepLSC-CNE 1.24 1.00
DeepLSC-CER 1.03 1.00
DeepLSC-w 1.12 1.00
AC2 0.86 1.00
1) DeepLSC V ersus DeepLSC-CNE: As presented in Fig. 3,
among all the schemes, DeepLSC-CNE achieves the highest
communication sum-rate while guaranteeing the given sensi ng
SNR constraint. To be speciﬁc, compared with DeepLSC, the
communication sum-rate gain of DeepLSC-CNE is around
11.14%. This is because DeepLSC-CNE is designed to max-
imize the communication sum-rate and satisfy the average
sensing SNR requirement, while ignoring the ﬂight mission
constraint. As a result, under DeepLSC-CNE, UA Vs tend to
stay in a speciﬁc area instead of ﬂying from initial location s to
desired locations within each episode, as shown in Fig. 4. On
the contrary, owing to the constrained noise-exploration p olicy,
DeepLSC can well guide UA Vs to reach their desired locations
within an episode, although sacriﬁcing both communication
and sensing performance to some certain. This result demon-
strates the effectiveness of the proposed constrained nois e-
exploration policy in fulﬁlling the ﬂight mission.
2) DeepLSC V ersus AC2: Similar to DeepLSC, AC2 em-
ploys the constrained noise-exploration policy to decide t he
movement directions of UA Vs. It, however, not only fails
to satisfy the given average sensing SNR requirement, but
also achieves a much lower communication sum-rate than
DeepLSC. In particular, compared with DeepLSC, the sum-
rate reduction of AC2 is more than 22.73%. The underlying
reasons are as follows. First, before executing the constra ined
noise-exploration policy, DeepLSC derives a deterministi c
joint beamforming and trajectory decision, whereas AC2 usu -
ally generates a probability distribution corresponding t o all
possible actions and randomly samples an action from this
distribution, resulting in inefﬁcient decisions. Second, during
DNN training, DeepLSC makes full use of random historical
experience sets, but AC2 relies on a single instantaneous

11
Fig. 4. Flight trajectory of a speciﬁc UA V under various sche mes.
experience set. As a consequence, the parameters of the DNN
are strongly correlated before and after the update, which
reduces the efﬁciency of the decision-making [36]. Besides , in
DeepLSC, the target-actor and target-critic are utilized t o assist
in training eval-actor and eval-critic, which further boos ts the
stability of the algorithm, whilst AC2 lacks this considera tion.
3) DeepLSC V ersus DeepLSC-CER: Unlike AC2, the under-
pinning algorithm in DeepLSC-CER is DDPG [37], which cir-
cumvents the above issues well. Thus, in comparison to AC2,
while meeting the preset average sensing SNR requirement,
DeepLSC-CER yields a signiﬁcant communication sum-rate
gain of about 15.88%. DeepLSC-CER, however, does not cater
well to the formulated optimization problem. Speciﬁcally, the
formulated optimization problem is an episode task, in the
sense that all experiences generated within an episode shou ld
be jointly used to train the DNN. Unfortunately, the DNN
training mechanism adopted in DeepLSC-CER, i.e., conven-
tional experience replay [40], separately collects and uti lizes
the experiences from different time slots. The consequence
is that all experiences generated within an episode cannot
be guaranteed to appear in full during training. By contrast ,
beneﬁting from the hierarchical experience replay mechani sm,
DeepLSC is able to take advantage of experience sets, each
composed of all experiences generated within an episode.
Thus, DeepLSC can well handle the formulated problem and
further improve the sum-rate of LAE-oriented ISAC systems:
compared with DeepLSC-CER, the improvement attained by
DeepLSC is about 11.68%.
4) DeepLSC V ersus DeepLSC-w: From Fig. 3, it can
also be found that DeepLSC-w experiences more episodes
before convergence compared to DeepLSC, DeepLSC-CNE,
and DeepLSC-CER, although they are all online learning
schemes. In particular, compared with the other three schem es,
DeepLSC-w consumes over 130.60% more episodes to con-
verge. The main reasons are illustrated below. In DeepLSC-w ,
the experience sets can only be obtained through interactio ns
with the environment. In general, to efﬁciently train the DN N,
a sufﬁcient number of experience sets are essential. As a res ult,
the learning process of the agent is slow. Unlike DeepLSC-
Fig. 5. Sum-rate of various schemes under different numbers of UA Vs.
w, based on the limited existing experience sets, DeepLSC,
DeepLSC-CNE, and DeepLSC-CER schemes exploit the sym-
metric experience augmentation mechanism to enrich the
available experience sets. Therefore, these three schemes can
acquire massive experience sets in a short time, thereby
signiﬁcantly accelerating the convergence speed. On the ot her
hand, in terms of communication and sensing performance,
DeepLSC-w is the same as DeepLSC after convergence; and
the UA V trajectories generated by the two are also similar,
as provided in Fig. 4. This is because the proposed symmetric
experience augmentation mechanism will not impair algorit hm
performance despite achieving faster convergence.
C. Robustness to Different Numbers of UA Vs
This subsection evaluates the robustness of various scheme s
against different numbers of UA Vs, in whichM increases from
2 to 5 with a step size of 1. Fig. 5 and TABLE III present the
communication sum-rate and constraint satisfactory of var ious
schemes, respectively.
It can be observed that as M increases, the communication
sum-rate achieved by all schemes are gradually improved. Th is
is because when M increases, the GBS can support more
parallel transmissions. At this time, under a reasonable be am-
forming design, spatial multiplexing can be further improv ed,
thereby increasing the communication sum-rate. In additio n,
with the increase of M , the sum-rate gap between DeepLSC
and DeepLSC-CER/AC2 increases. For example, when M
increases from 2 to 5, the sum-rate gain of DeepLSC increases
from 14.43 bps/Hz to 21.42 bps/Hz compared with DeepLSC-
CER. On the other hand, as summarized in TABLE III, due
to the inefﬁcient DNN training mechanism, both DeepLSC-
CER and AC2 cannot always meet the average sensing SNR
requirement under different values of M , whereas DeepLSC-
CNE fails to fulﬁll the ﬂight mission since it lacks the guid-
ance of the constrained noise-exploration policy. Thus, am ong
all the schemes, only DeepLSC and DeepLSC-w satisfy all
constraints under various settings. DeepLSC-w, however, c on-
verges much slower than DeepLSC, as elaborated in Section
V -B. Overall, the above observations exemplify that compar ed

12
TABLE III: Performance of various schemes in satisfying the
average sensing SNR and ﬂight mission constraints under
different numbers of UA Vs.
A verage sensing SNR constraint
M = 2 M = 3 M = 4 M = 5
DeepLSC ✓ ✓ ✓ ✓
DeepLSC-CNE ✓ ✓ ✓ ✓
DeepLSC-CER ✓ ✓ ✓ ×
DeepLSC-w ✓ ✓ ✓ ✓
AC2 ✓ ✓ × ×
Flight mission constraint
M = 2 M = 3 M = 4 M = 5
DeepLSC ✓ ✓ ✓ ✓
DeepLSC-CNE × × × ×
DeepLSC-CER ✓ ✓ ✓ ✓
DeepLSC-w ✓ ✓ ✓ ✓
AC2 ✓ ✓ ✓ ✓
with other schemes, DeepLSC is more robust against differen t
numbers of UA Vs in LAE-oriented ISAC systems.
D. Robustness to Different Numbers of Time Slots Within a
Flight Period
This simulation evaluates the robustness of various scheme s
to different numbers of time slots within a ﬂight period, in
which T increases from 40 to 70 with a step size of 10. The
communication sum-rate and constraint satisfactory of var ious
schemes are shown in Fig. 6 and TABLE IV, respectively.
As expected, the communication sum-rate attained by vari-
ous schemes improves monotonically as T increases. The main
reasons are below. As T increases, the number of time slots
during which all UA Vs can ﬂy freely without the ﬂight mission
constraint increases. In this regard, all schemes possess m ore
time degrees of freedom to optimize the joint beamforming
and trajectory strategy, so as to maximize the communi-
cation sum-rate while satisfying the average sensing SNR
requirement. Besides, under different T , DeepLSC, DeepLSC-
CER, and DeepLSC-w schemes can always satisfy all preset
constraints, whilst both DeepLSC-CNE and AC2 fail. Thanks
to a more intelligent and efﬁcient strategy, DeepLSC achiev es
a higher communication sum-rate than DeepLSC-CER. To be
speciﬁc, compared with DeepLSC-CER, DeepLSC yields a
more than 11.68% sum-rate gain for all simulation setups.
More importantly, as T increases, the communication sum-
rate gap between DeepLSC and DeepLSC-CNE keeps almost
unchanged, whereas that between DeepLSC and DeepLSC-
CER/AC2 increases. In particular, when M increases from
40 to 70, the sum-rate improvement of DeepLSC increases (i)
from 18.42 bps/Hz to 39.56 bps/Hz compared with DeepLSC-
CER and (ii) from 40.03 bps/Hz to 76.63 bps/Hz compared
with AC2. The above results show that under different number s
of time slots within a ﬂight period, DeepLSC is more robust
than other schemes.
VI. C ONCLUSION
This paper put forth a new ISAC scheme for LAE, termed
DeepLSC, based on the DRL technique. By jointly optimizing
GBS’s beamforming and UA Vs’ trajectories, DeepLSC aims to
maximize the expected communication sum-rate over the ﬂigh t
Fig. 6. Sum-rate of various schemes under different numbers of time slots
within a ﬂight period.
TABLE IV: Performance of various schemes in satisfying
the average sensing SNR and ﬂight mission constraints under
different numbers of time slots within a ﬂight period.
A verage sensing SNR constraint
T = 40 T = 50 T = 60 T = 70
DeepLSC ✓ ✓ ✓ ✓
DeepLSC-CNE ✓ ✓ ✓ ✓
DeepLSC-CER ✓ ✓ ✓ ✓
DeepLSC-w ✓ ✓ ✓ ✓
AC2 × × × ×
Flight mission constraint
T = 40 T = 50 T = 60 T = 70
DeepLSC ✓ ✓ ✓ ✓
DeepLSC-CNE × × × ×
DeepLSC-CER ✓ ✓ ✓ ✓
DeepLSC-w ✓ ✓ ✓ ✓
AC2 ✓ ✓ ✓ ✓
period, subject to the average sensing SNR requirement, ﬂig ht
mission, collision avoidance, and maximum transmit power
constraints. DeepLSC, on the one hand, is model-free since
it does not require prior mobility information of the target ;
on the other hand, it is capable of episode tasks thanks to an
appropriate structural design. First, to meet various cons traints,
a constrained noise-exploration policy and a reward functi on
were judiciously designed in DeepLSC for action selection
and action evaluation, respectively. Thereafter, we devel oped
a hierarchical experience replay mechanism for DNN trainin g,
where all experiences within an episode are jointly utilize d
to enable DeepLSC to efﬁciently learn from episode tasks.
Besides, to promote the convergence speed of DeepLSC, a
symmetric experience augmentation mechanism was further
proposed. Simulation results demonstrated compared with
other schemes, DeepLSC (i) yields a much higher commu-
nication sum-rate while meeting all constraints, (ii) conv erges
faster, and (iii) is more robust against different settings .
REFERENCES
[1] Y . Jiang, X. Li, G. Zhu, H. Li, J. Deng, and Q. Shi, “6G non-t errestrial
networks enabled low-altitude economy: Opportunities and challenges,”
arXiv preprint arXiv:2311.09047 , 2023.

13
[2] China Telecom, Ericsson, Nokia, Huawei, ZTE, CICT
Mobile, OPPO, Xiaomi, vivo, Lenovo, Qualcomm, Mediatek,
UNISOC, “The low-altitude network by integrated sensing
and communication,” White Paper, Feb. 2024. [Online]. Avai lable:
https://www.zte.com.cn/content/dam/zte-site/res-www-zte-com-cn/mediares/zte/%E6%97%A0%E7%BA%BF%E6%8E%A 5%E5%85%A5/%E7%99%BD%E7%9A%AE%E4%B9% 
[3] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets inte grated
sensing and communication: Challenges and future directio ns,” IEEE
Commun. Mag. , vol. 61, no. 5, pp. 62–67, Jan. 2023.
[4] F. Liu, Y . Cui, C. Masouros, J. Xu, T. X. Han, Y . C. Eldar, an d S. Buzzi,
“Integrated sensing and communications: Toward dual-func tional wire-
less networks for 6G and beyond,” IEEE J. Sel. Areas in Commun. ,
vol. 40, no. 6, pp. 1728–1767, Mar. 2022.
[5] K. Zhang and C. Shen, “UA V aided integrated sensing and co mmuni-
cations,” in Proc. IEEE VTC , Norman, OK, USA, Sept. 2021, pp. 1–6.
[6] S. Zhang, H. Zhang, Z. Han, H. V . Poor, and L. Song, “Age of
information in a cellular internet of UA Vs: Sensing and comm unication
trade-off design,” IEEE Trans. Wireless Commun. , vol. 19, no. 10, pp.
6578–6592, Jun. 2020.
[7] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Y uan, “Constr ained
utility maximization in dual-functional radar-communica tion multi-UA V
networks,” IEEE Trans. Commun. , vol. 69, no. 4, pp. 2660–2672, Dec.
2020.
[8] B. Chang, W. Tang, X. Y an, X. Tong, and Z. Chen, “Integrate d
scheduling of sensing, communication, and control for mmWa ve/THz
communications in cellular connected UA V networks,” IEEE J. Sel.
Areas in Commun. , vol. 40, no. 7, pp. 2103–2113, Mar. 2022.
[9] W. Ding, C. Chen, Y . Fang, L. Qiu, X. Li, X. Wang, and J. Xu,
“Multi-UA V-enabled integrated sensing and communications: Joint UA V
placement and power control,” in Proc. IEEE Globecom W orkshops ,
Kuala Lumpur, Malaysia, Dec. 2023, pp. 842–847.
[10] G. A. Bayessa, R. Chai, C. Liang, D. K. Jain, and Q. Chen, “ Joint
UA V deployment and precoder optimization for multicasting and target
sensing in UA V-assisted ISAC networks,” IEEE Internet Things J. ,
vol. 11, no. 20, pp. 33 392–33 405, Jul. 2024.
[11] X. Y u, J. Xu, N. Zhao, X. Wang, and D. Niyato, “Security en hancement
of ISAC via IRS-UA V,”IEEE Trans. Wireless Commun., vol. 23, no. 10,
pp. 15 601–15 612, Jul. 2024.
[12] J. Wu, W. Y uan, and L. Hanzo, “When UA Vs meet ISAC: Real-
time trajectory design for secure communications,” IEEE Trans. V eh.
Technol., vol. 72, no. 12, pp. 16 766–16 771, Dec. 2023.
[13] S. Hu, X. Y uan, W. Ni, and X. Wang, “Trajectory planning o f cellular-
connected UA V for communication-assisted radar sensing,” IEEE Trans.
Commun., vol. 70, no. 9, pp. 6385–6396, Aug. 2022.
[14] Y . Liu, S. Liu, X. Liu, Z. Liu, and T. S. Durrani, “Sensing fairness-based
energy efﬁciency optimization for UA V enabled integrated s ensing and
communication,” IEEE Wireless Commun. Lett. , vol. 12, no. 10, pp.
1702–1706, Jun. 2023.
[15] Z. Liu, X. Liu, Y . Liu, V . C. Leung, and T. S. Durrani, “UA V assisted in-
tegrated sensing and communications for internet of things : 3D trajectory
optimization and resource allocation,” IEEE Trans. Wireless Commun. ,
vol. 23, no. 8, pp. 8654–8667, Jan. 2024.
[16] Y . Liu, X. Liu, Z. Liu, Y . Y u, M. Jia, Z. Na, and T. S. Durran i, “Secure
rate maximization for isac-uav assisted communication ami dst multiple
eavesdroppers,” IEEE Trans. V eh. Technol., vol. 73, no. 10, pp. 15 843–
15 847, Jun. 2024.
[17] J. Zhang, J. Xu, W. Lu, N. Zhao, X. Wang, and D. Niyato, “Se cure
transmission for IRS-aided UA V -ISAC networks,”IEEE Trans. Wireless
Commun., vol. 23, no. 9, pp. 12 256–12 269, Apr. 2024.
[18] X. Jing, F. Liu, C. Masouros, and Y . Zeng, “ISAC from the s ky: UA V
trajectory design for joint communication and target local ization,” IEEE
Trans. Wireless Commun., vol. 23, no. 10, pp. 12 857–12 872, May 2024.
[19] K. Meng, Q. Wu, S. Ma, W. Chen, K. Wang, and J. Li, “Through put
maximization for UA V-enabled integrated periodic sensing and commu-
nication,” IEEE Trans. Wireless Commun. , vol. 22, no. 1, pp. 671–687,
Aug. 2022.
[20] K. Meng, Q. Wu, S. Ma, W. Chen, and T. Q. Quek, “UA V traject ory
and beamforming optimization for integrated periodic sens ing and
communication,” IEEE Wireless Commun. Lett., vol. 11, no. 6, pp. 1211–
1215, Mar. 2022.
[21] Z. Lyu, G. Zhu, and J. Xu, “Joint maneuver and beamformin g design
for UA V-enabled integrated sensing and communication,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2424–2440, Oct. 2022.
[22] Z. Wu, X. Li, Y . Cai, and W. Y uan, “Joint trajectory and re source
allocation design for RIS-assisted UA V-enabled ISAC syste ms,” IEEE
Wireless Commun. Lett. , vol. 13, no. 5, pp. 1384–1388, Feb. 2024.
[23] C. Deng, X. Fang, and X. Wang, “Beamforming design and tr ajectory
optimization for UA V-empowered adaptable integrated sens ing and
communication,” IEEE Trans. Wireless Commun. , vol. 22, no. 11, pp.
8512–8526, Apr. 2023.
[24] T. V an Chien, M. D. Cong, N. C. Luong, T. N. Do, D. I. Kim, an d
S. Chatzinotas, “Joint computation ofﬂoading and target tr acking in
integrated sensing and communication enabled UA V networks ,” IEEE
Commun. Lett. , vol. 28, no. 6, pp. 1327–1331, Apr. 2024.
[25] J. Wu, W. Y uan, and L. Bai, “On the interplay between sens ing and
communications for UA V trajectory design,” IEEE Internet Things J. ,
vol. 10, no. 23, pp. 20 383–20 395, Jun. 2023.
[26] R. Zhang, Y . Zhang, R. Tang, H. Zhao, Q. Xiao, and C. Wang, “A joint
UA V trajectory, user association, and beamforming design s trategy for
multi-UA V assisted ISAC systems,” IEEE Internet Things J. , vol. 11,
no. 8, pp. 29 360–29 374, Jul. 2024.
[27] T. Zhang, K. Zhu, S. Zheng, D. Niyato, and N. C. Luong, “Tr ajectory de-
sign and power control for joint radar and communication ena bled multi-
UA V cooperative detection systems,” IEEE Trans. Commun. , vol. 71,
no. 1, pp. 158–172, Nov. 2022.
[28] Z. Xie, Z. Wang, Z. Zhang, J. Wang, Z. Jiang, and Z. Han, “D istributed
UA V swarm for device-free integrated sensing and communica tion rely-
ing on multi-agent reinforcement learning,” IEEE Trans. V eh. Technol.,
Aug. 2024, early access, doi: 10.1109/TVT.2024.3438854.
[29] X. Chen, X. Cao, L. Xie, and Y . He, “DRL-based joint traje ctory
planning and beamforming optimization in aerial RIS-assis ted ISAC
system,” in Proc. IEEE iWRF&AT, Shenzhen, China, Jul. 2024, pp. 510–
515.
[30] H. Cho, S. Y oo, B. C. Jung, and J. Kang, “Enhancing battle ﬁeld
awareness: An aerial RIS-assisted ISAC system with deep rei nforcement
learning,” arXiv preprint arXiv:2405.20168 , 2024.
[31] G. Fontanesi, A. Guerra, F. Guidi, J. A. V´ asquez-Peral vo, N. Shlezinger,
A. Zanella, E. Lagunas, S. Chatzinotas, D. Dardari, and P . M. Djuri´ c, “A
deep-NN beamforming approach for dual function radar-comm unication
THz UA V,”arXiv preprint arXiv:2405.17015 , 2024.
[32] Y . Qin, Z. Zhang, X. Li, W. Huangfu, and H. Zhang, “Deep re in-
forcement learning based resource allocation and trajecto ry planning
in integrated sensing and communications UA V network,” IEEE Trans.
Wireless Commun., vol. 22, no. 11, pp. 8158–8169, Mar. 2023.
[33] C. Dai, T. Wu, G. Sun, Y . Zuo, Z. Guo, and F. Xiao, “Joint UA V
trajectory and beamforming design for ris-aided integrate d sensing
and communication system,” in Proc. IEEE INFOCOM W orkshops ,
V ancouver, BC, Canada, May 2024, pp. 1–6.
[34] Y . Cui, Q. Zhang, Z. Feng, F. Liu, C. Shi, J. Fan, and P . Zha ng,
“Speciﬁc beamforming for multi-UA V networks: A dual identi ty-based
ISAC approach,” in Proc. IEEE ICC , Rome, Italy, May 2023, pp. 4979–
4985.
[35] G. Cheng, X. Song, Z. Lyu, and J. Xu, “Networked ISAC for l ow-
altitude economy: Coordinated transmit beamforming and UA V trajec-
tory design,” arXiv preprint arXiv:2406.16946 , 2024.
[36] R. S. Sutton and A. G. Barto, Reinforcement learning: An introduction .
Cambridge, MA, USA:MIT press, 2018.
[37] V . Mnih, K. Kavukcuoglu, D. Silver, A. A. Rusu, J. V eness , M. G.
Bellemare, A. Graves, M. Riedmiller, A. K. Fidjeland, G. Ost rovski
et al. , “Human-level control through deep reinforcement learnin g,”
nature, vol. 518, no. 7540, pp. 529–533, Feb. 2015.
[38] X. Y e, Y . Y u, and L. Fu, “Multi-channel opportunistic ac cess for
heterogeneous networks based on deep reinforcement learni ng,” IEEE
Trans. Wireless Commun. , vol. 21, no. 2, pp. 794–807, Feb. 2022.
[39] T. Lillicrap, J. Hunt, A. Pritzel, N. Heess, T. Erez, Y . T assa, D. Silver,
and D. Wierstra, “Continuous control with deep reinforceme nt learning,”
in Proc. Int. Conf. Learn. Represent. , San Juan, Puerto Rico, May 2016,
pp. 1–14.
[40] L.-J. Lin, “Self-improving reactive agents based on re inforcement learn-
ing, planning and teaching,” Mach. Learn. , vol. 8, pp. 293–321, May
1992.
[41] H. Tabassum, M. Salehi, and E. Hossain, “Fundamentals o f mobility-
aware performance characterization of cellular networks: A tutorial,”
IEEE Commun. Surveys Tuts. , vol. 21, no. 3, pp. 2288–2308, Mar. 2019.
[42] R. S. Sutton, D. McAllester, S. Singh, and Y . Mansour, “P olicy gradient
methods for reinforcement learning with function approxim ation,” in
Proc. Adv. Neural Inf. Process. Syst. , Denver, USA, Nov. 1999, pp.
1057–1063.
[43] ´A. Seress, Permutation group algorithms. Cambridge University Press,
2003, no. 152.
[44] F. Chollet, Keras: The python deep learning library , Jun. 2018.
[Online]. Available: https://keras.io.