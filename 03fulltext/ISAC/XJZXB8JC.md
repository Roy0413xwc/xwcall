---
title: "Environment Sensing Considering the Occlusion Effect: A Multi-View Approach"
zotero_key: "XJZXB8JC"
pdf_key: "XFIS8EIB"
doi: "10.1109/TSP.2022.3185892"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Environment Sensing Considering the Occlusion Effect: A Multi-View Approach — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

3598 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
Environment Sensing Considering the Occlusion
Effect: A Multi-View Approach
Xin Tong , Student Member , IEEE, Zhaoyang Zhang , Senior Member , IEEE,
Yihan Zhang, Student Member , IEEE, Zhaohui Y ang, Member , IEEE, Chongwen Huang , Member , IEEE,
Kai-Kit Wong , Fellow, IEEE, and Mérouane Debbah , Fellow, IEEE
Abstract—In this paper, we consider the problem of sensing the
environment within a wireless cellular framework. Speciﬁcally,
multiple user equipments (UEs) send sounding signals to one or
multiple base stations (BSs) and then a centralized processor re-
trieves the environmental information from all the channel infor-
mation obtained at the BS(s). Taking into account the occlusion
effect that is common in the wireless context, we make full use of
the different views of the environment from different users and/or
BS(s), and propose an effective sensing algorithm called GAMP-
MVSVR (generalized-approximate-message-passing-based multi-
view sparse vector reconstruction). In the proposed algorithm,
a multi-layer factor graph is constructed to iteratively estimate
the scattering coefﬁcients of the cloud points and their occlusion
relationship. In each iteration, the occlusion relationship between
the cloud points of the sparse environment is recalculated according
to a simple occlusion detection rule, and in turn, used to estimate the
scattering coefﬁcients of the cloud points. Our proposed algorithm
can achieve improved sensing performance with multi-BS collabo-
ration in addition to the multi-views from the UEs. The simulation
results verify its convergence and effectiveness.
Manuscript received 17 December 2021; revised 15 April 2022 and 11 June
2022; accepted 13 June 2022. Date of publication 24 June 2022; date of current
version 19 July 2022. The associate editor coordinating the review of this
manuscript and approving it for publication was Dr. Michael B Wakin. This
work was supported in part by the National Natural Science Foundation of
China under Grants U20A20158 and 61725104 and in part by the National Key
R&D Program of China under Grants 2020YFB1807101 and 2018YFB1801104.
(Corresponding author: Zhaoyang Zhang.)
Xin Tong, Zhaoyang Zhang, Yihan Zhang, and Chongwen Huang are with
the College of Information Science and Electronic Engineering, Zhejiang Uni-
versity, Hangzhou 310027, China, with the Key Laboratory of Information
Processing, Communication and Networking of Zhejiang Province, Zhejiang
University, Hangzhou 310027, China, with the Key Laboratory of Collabo-
rative Sensing and Autonomous Unmanned Systems of Zhejiang Province,
Zhejiang University, Hangzhou 310015, China, and also with the Interna-
tional Joint Innovation Center, Zhejiang University, Haining 314400, China
(e-mail: tongx@zju.edu.cn; ning_ming@zju.edu.cn; zhangyihan@zju.edu.cn;
chongwenhuang@zju.edu.cn).
Zhaohui Y ang is with the College of Information Science and Electronic
Engineering, Zhejiang University, Hangzhou 310027, China, with the Key
Laboratory of Information Processing, Communication and Networking of
Zhejiang Province, Zhejiang University, Hangzhou 310027, China, with the
Key Laboratory of Collaborative Sensing and Autonomous Unmanned Sys-
tems of Zhejiang Province, Zhejiang University, Hangzhou 310015, China,
with the International Joint Innovation Center, Zhejiang University, Haining
314400, China, and also with Zhejiang Lab, Hangzhou 311121, China (e-mail:
yang_zhaohui@zju.edu.cn).
Kai-Kit Wong is with the Department of Electronic and Electrical En-
gineering, University College London, London WC1E 6BT, U.K. (e-mail:
kai-kit.wong@ucl.ac.uk).
Mérouane Debbah is with the Technology Innovation Institute, Masdar City
9639, Abu Dhabi, UAE, and also with the CentraleSupelec, University Paris-
Saclay, 91192 Gif-sur-Yvette, France (e-mail: merouane.debbah@tii.ae).
Digital Object Identiﬁer 10.1109/TSP .2022.3185892
Index Terms —Environment sensing, integrated sensing and
communication (ISAC), multi-view sensing, occlusion effect.
I. I NTRODUCTION
A. Motivation
T
HE emergence of innovative wireless communication tech-
nologies, such as ultra-massive multiple input multiple
output (MIMO) technology, intelligent reﬂective surface (IRS),
and wireless artiﬁcial intelligence (AI) [1]–[3], etc., provides
more possibilities for the development of future wireless com-
munication systems design. In the foreseeable future wireless
communication application scenarios, autonomous driving [4],
intelligent robot localization [5], and unmanned aerial vehicle
(UA V) control [6] require not only wireless broadband connec-
tions, but also accurate environmental information, including
the location, shape, and electromagnetic (EM) characteristics,
etc. of objects in the environment. Therefore, integrated sensing
and communication (ISAC), as a research hotspot for the next
generation wireless communication system, aims to use the
wireless communication equipment and infrastructure to achieve
environment sensing.
Such kind of environment sensing has long been accom-
plished by traditional radar technology and its later evolution
of joint radar and communication [7]. The latter usually aims
to achieve the sharing of software and hardware equipment
and time-frequency resources between radar equipment and
communication equipment. Compared with traditional radar or
early joint radar and communication systems, efﬁcient use of
communication signals in the existing communication systems
for environment sensing, and efﬁcient exploitation of the en-
vironment sensing results to enhance communication, are two
major design goals of the ISAC systems. For the former goal, one
straightforward realization is to fully exploit the environmental
information embedded in the received communication data, due
to the simple fact that the distribution of environmental scatterers
dramatically affects the wireless multipath channels. For the lat-
ter, direct channel prediction (reconstruction) can be conducted
based on the sensed distribution and characteristics of scatterers
within the environment thus to enhance the performance of com-
munication [8]–[10]. In this paper, we mainly focus on the ﬁrst
part and study how to perform efﬁcient and accurate environment
sensing based on the uplink data received from multiple users,
in a way compatible with existing communication systems thus
to achieve a smooth integration of communication and sensing.
One major challenge to do this is the large number of unknown
variables embedded in the generally complicated environment,
1053-587X © 2022 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3599
including the unknown location and EM characteristics of the
environmental scatterers themselves, and the very common
occlusion effect within and between scatterers, which blocks the
propagation of EM waves and makes portions of some scatterers
or even all of them invisible to the receivers. In such a case, it
is hard for a single user or base station (BS) to fully sense the
entire environment and the different views of the environment
from different users and/or BS(s) should be exploited. However,
a challenge still remains since in each separate sensing (transmit-
ting and receiving), we generally cannot know which scatterers
or which part of them participates in the ﬁnal generation of the
received signal in an environment yet to know, and it differs
from user to user and BS to BS. This motivates us to develop a
practical and efﬁcient multi-view sensing algorithm to deal with
the above problem.
B. Related Works
So far, the design of ISAC system has raised extensive re-
search effort. In [11], the author comprehensively discussed the
novel applications, key performance requirements, challenges,
and future research directions of ISAC system designs. In [12],
the author compared the difference between the radar sensing
scheme and the ISAC scheme. The author showcased that a
common signal wave should be jointly designed to realize the
integration of sensing and communication, and the advantages
and disadvantages of various design methodologies are also
discussed.
Rapid progresses have been witnessed in the practical ISAC
system and algorithm design recently. [13] designed an ISAC
system based on the wireless cellular networks. The author
jointly designed signal waveforms suitable for sensing and
communication based on 5G NR (New Radio) and its frame
structure. Also under the 5G framework, [14] proposed a multi-
beam based sensing and communication scheme. In addition
to the beams used for communication, some other ones are
used to sense the environment around the BS. Based on the
4G and 5G frameworks, [15] studied the processing princi-
ples, implementation challenges, and performance of orthog-
onal frequency division multiplexing (OFDM)-based radars,
and achieved excellent sensing performance by using high
channel bandwidth and conﬁgurable sub-carriers. In a Wi-Fi
communication context, based on the Doppler frequency shift
embedded in the channel state information (CSI), [16] achieved
the sensing of human body posture. In the regime of internet
of vehicles, [17] designed a fast beam alignment and track-
ing algorithm based on a hardware test platform to achieve
vehicle tracking while performing millimeter wave communi-
cation with low latency and high data rate. As the research
interest on ISAC keeps on increasing, more and more potential
technologies are also introduced into this ﬁeld, such as chan-
nel modeling [18], joint beam optimization [19] and machine
learning [20], etc.
As for the environment sensing system design, some works
have made full use of the sparsity of environmental information
and achieved better and lower-complexity solutions based on
the compressed sensing (CS) [21], [22] framework. In the ﬁeld
of microwave computational imaging, the utilization of the
intrinsic sparsity of scatterers within the environment is key to
their effective detection. This type of algorithm usually treats the
scatterer as a sparsely distributed point cloud, thereby convert
the imaging problem into a CS reconstruction problem, which is
solved by orthogonal matching pursuit (OMP) [23], approximate
message passing (AMP) [24], generalized approximate message
passing (GAMP) [25] and other widely used methods.
Recently, in [26] and [27], the authors innovatively used BS to
sense actively, and based on the block sparse Bayesian learning
(BSBL) algorithm, proposed an IRS-assisted microwave com-
puting imaging method. Although the above-mentioned meth-
ods effectively exploit the sparsity of the environment but ignore
the occlusion effect caused by the scatterers. They ideally believe
that EM signals can be freely transmitted to any location in the
environment, and there still lacks sufﬁcient consideration of the
occlusion effect in the ISAC system design.
C. Main Ideas and Contributions
In this paper, based on the existing wireless communication
framework, we design a multi-view environment sensing scheme
taking into full consideration the occlusion effect in an outdoor
scenario.
Different from the above-mentioned application scenarios, we
have achieved ISAC by noninvasively making use of the multi-
user uplink communication data. At the same time, we have
designed an effective sensing algorithm called GAMP-MVSVR
which refers to the generalized-approximate-message-passing-
based multi-view sparse vector reconstruction. In the uplink
communication scenario, we consider an environment sensing
scenario with single or multiple BSs, where users and BSs
perform multi-view and collaborative sensing, and a centralized
processor retrieving the environmental information from all the
channel information obtained at the BSs. As a special case of
the multi-BS scheme, a single BS itself can also complete all
the sensing tasks, and we compare the performance differences
between the two schemes.
Our design is depicted as follows. In one or more time slots,
the BS estimates the multi-user uplink channel after detecting
user pilot symbols (sounding signals). We propose an occlusion
detection model based on the geometric location of the cloud
points and convert the environment sensing problem into a
CS reconstruction problem with the occlusion effect. Then we
propose a probabilistic reasoning model based on the factor
graph by analyzing the relationship among multipath channels,
environmental information, and occlusion effects. Based on
the well-known AMP method, the proposed GAMP-MVSVR
algorithm achieves environment sensing by iteratively estimat-
ing the scattering coefﬁcients of the cloud points and their
occlusion relationship. In each iteration, the occlusion rela-
tionship between the cloud points of the sparse environment
is recalculated according to the proposed occlusion detection
rule, and in turn, used to estimate the scattering coefﬁcients of
the cloud points. Our proposed algorithm achieves improved
sensing performance with multi-BS collaboration in addition to
the multi-views from the users. To the best of our knowledge,
there has been little work on the design of such an ISAC system
in the literature.
The main contributions of this paper are summarized as
follows:r We propose an ISAC scheme, which makes full use of
the different views of the environment from different users
and/or BS(s) to achieve improved sensing performance
with multi-BS collaboration in addition to the multi-views
from the UEs.r We propose an effective environment sensing algorithm
called GAMP-MVSVR that considers the occlusion ef-
fect, where a multi-layer factor graph is constructed to
iteratively estimate the scattering coefﬁcients of the cloud
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3600 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
Fig. 1. The environment sensing scenario with the occlusion effect.
points and derive their occlusion relationship based on a
simple occlusion detection rule.r We analyze the impact of the multi-view schemes on envi-
ronment sensing range and system performance. Extensive
simulation results verify the convergence and effectiveness
of the proposed algorithm.
The rest of this paper is organized as follows. Section II
presents the environment setting and system model in the uplink
communication scenario. Section III proposes the environment
sensing problem formulation. Section IV proposes the GAMP-
MVSVR algorithm under the occlusion effect. In Section V, we
analyze the impact of the multi-view schemes on environment
sensing range and system performance. Finally, Section VI
presents the numerical results, and Section VII concludes the
paper.
Notations: Fontsa, a and A represent scalars, vectors and ma-
trices, respectively. Notations AT and ‖A‖F denote transpose
and Frobenius norm of A, respectively. Ai,: and A:,j represent
the i-th row and j-th column of matrix A, respectively. ⊙
represents the Hadamard product between two matrices. Finally,
notation diag(a) represents a diagonal matrix with the entries
of a on its main diagonal, and δ(·) is the Dirac delta function.
II. E NVIRONMENT SETTING AND SYSTEM MODEL
A. Environment Setting
As shown in Fig. 1, we consider that in the outdoor wireless
communication scenario, multiple BSs are deployed and there
are multiple active user equipments (UEs). There are some
buildings (target objects, serve as scatterers) in the outdoor
environment that affect the wireless communication channel.
We assume w.l.o.g. that the channel is a quasi-static channel
where one block of transmission timeTb is much shorter than the
channel coherence time Tc,Tb << Tc, and the UE is stationary
within the coherence time of the multipath channel estimation
by UE pilots. In the uplink communication scenario, multiple
single-antenna UEs send uplink communication data to multi-
antenna BSs. The transmitted signal is scattered by the scatterer,
and received by BSs through multipath channel. Therefore, the
received signal of the BS contains environmental information.
We consider two schemes: a single-BS scheme and a multi-BS
joint scheme to achieve multi-view environment sensing. The
speciﬁc analysis is as follows.r As shown in Fig. 1, the single-BS environment sensing
scheme is treated as a special case of the multi-BS joint
scheme. When multiple UEs send uplink data to BS 1,
the uplink communication channel is affected by the target
scatterer. In the scenario, due to the occlusion effect, the
multipath channel of UE 1 is only affected by the scattering
of target scatterers 4 and 5, and the multipath channel of
UE 2 is only affected by the scattering of target scatterers 5.
Therefore, not all scatterers in the environment will affect
the multipath channel of the same user, and the occlusion
effect makes it hard for a single user to fully sensed the
entire environment. The different views of the environment
from different users should be exploited to deal with the
occlusion effect.r Fig. 1 shows the scenario where multiple BSs are used
for joint environment sensing, where the multi-BS scheme
is performed. Sensing by multiple BSs will effectively
expand the sensing range. In addition to the same user
multi-view method as in the single-BS scheme, the dif-
ferent views of the environment from different BSs should
be exploited. For example, in Fig. 1, BS 2 cannot receive
the scattered signal from the target scatterer 3, and BS 1 and
3 also have scatterers that cannot be observed. Therefore,
a multi-BS joint scheme should be designed to achieve the
sensing of the entire environment.
B. System Model
For the receiving antennas deployed on the BS, the single-BS
scheme and the multi-BS joint scheme have the same system
model. Let the number of users in the environment beNu, and the
total number of receiving antennas of all BSs isNR. In the uplink
communication scenario, the channel from the user to the BS is
mainly composed of two parts: the line-of-sight channel HLOS
from the user to the BS, and the multipath channel HS caused
by the scatterer. We discretize environmental information and
treat the environmental information in the entire environment
as point clouds. Each point in the point cloud represents the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3601
Fig. 2. The discretized targeted environment object.
environmental information of the small cube with length ls,
width ws, and height hs around it, and these small cubes are
called pixels. The inside of each pixel may be empty, or there may
be scatterers. The length, width and height of the environment
to be sensed are Ls, Ws and Hs respectively, then the number
of point clouds is Ns =( Ls/ls)×(Ws/ws)×(Hs/hs).F i g .2
shows the method of discretizing environmental information into
point clouds. We use the scattering coefﬁcient xns to represent
the scattering coefﬁcient of the small cube where the ns-th
cloud point is located. If the small cube is empty, then xns =0 .
Otherwise, xns > 0. Therefore, the environmental information
to be sensed is expressed as x =[ x1,x 2,...,x Ns]T.
Multiple users in the space share time-frequency resources.
On a single subcarrier, the antennas of all BSs are analyzed in-
dependently. The signal received at thenR-th receiving antenna
can be expressed as
Y(nR)= S
(
HS (nR)+ HLOS (nR))+ W, (1)
where S ∈ CNT×Nu represents codewords with the length of
NT sent by Nu users, Y(nR) ∈ CNT×1 represents the received
signal of the nR-th BS antenna, and W represents noise. The
term HLOS(nR) ∈ CNu×1 represents the channel coefﬁcient of
the line-of-sight path from the user to the receiving antenna,
where the free space channel is decomposed into amplitude
attenuation and phase shift, hLOSnu (nR)= αLOS ·ejϕLOS , αLOS
is the line-of-sight channel amplitude attenuation, and ϕLOS is
the line-of-sight channel phase shift. The line-of-sight channel
occlusion can be detected through beam scanning, received
power, etc. The term HS(nR) ∈ CNu×1 represents the channel
coefﬁcient of the multipath channel from the user to the receiving
antenna.
As mentioned in Section I-B, we consider that in ISAC system
design, the utilization of the intrinsic sparsity of objects or
scatterers within an environment is key to the effective detection.
We separate the free space channel (microwave background
ﬁeld) and scatterers in the multipath channel model to obtain
sparse environmental information. In this way, the occlusion
relationship between the scatterer and the antenna can be mod-
eled by the existence of the free space channel between them.
The multipath channel from the user to the receiving antenna
HS(nR) is expressed as
HS (nR)= ˜H(nR) x (2a)
=[ H(nR)⊙ V(nR)] x (2b)
=
(
HU→s ⊙ VU→s)diag(Hs→B (nR)⊙ Vs→B (nR)) x,
(2c)
where the free space channel coefﬁcient ˜H(nR) with occlu-
sion is expressed as the Hadamard product of the free space
channel coefﬁcient H(nR) ∈ CNu×Ns and the occlusion matrix
V(nR) ∈{ 0,1}Nu×Ns . The element 0 in the occlusion matrix
V(nR) indicates that the path fromnu-th user tonR-th receiving
antenna is blocked, and the element 1 indicates that the path from
nu-th user to nR-th receiving antenna is not blocked. HU→s ∈
CNu×Ns represents the channel coefﬁcient from the user to
the point cloud position, where hU→snu,ns = αU→s ·ejϕU→s , αU→s
represents the channel amplitude attenuation from the user to the
point cloud position, ϕU→s represents the channel phase shift
from the user to the point cloud position. Hs→B(nR) ∈ CNs×1
represents the channel coefﬁcient from the point cloud position
to the BS receiving antenna, wherehs→Bns (nR)= αs→B ·ejϕs→B ,
αs→B represents the channel amplitude attenuation from the
point cloud position to the BS receiving antenna, ϕs→B rep-
resents the channel phase shift from the point cloud position to
the BS receiving antenna, H(nR)= HU→sdiag(Hs→B(nR)).
VU→s ∈{ 0,1}Nu×Ns represents the occlusion matrix from the
user to the point cloud position, and its distribution reﬂects
the different views from different users. When VU→s con-
tains an all-zero column, it means that all users cannot sense
the corresponding pixel, and the corresponding pixel is out
of the sensing range. Vs→B(nR) ∈{ 0,1}Ns×1 represents the
occlusion matrix from the point cloud position to the receiving
antenna, and its distribution reﬂects the different views from
different BSs. When Vs→B(nR) contains a zero element, it
means that the receiving antenna cannot sense the corresponding
pixel, and the corresponding pixel is also out of the sensing
range, V(nR)= VU→sdiag(Vs→B(nR)).
In (2), the model is derived as follows. First, in (2a), we
decompose the multipath channel HS(nR) in (1) into free space
channel with occlusion ˜H(nR) and environmental information
x. Then, in (2b), we decompose free space channel with occlu-
sion ˜H(nR) into free space channelH(nR) and occlusion matrix
V(nR). Finally, in (2c), we further decompose the free space
channel with occlusion ˜H(nR) into the channels from the user,
the base station to the point cloud position HU→s, Hs→B(nR)
and their corresponding occlusion matrices VU→s, Vs→B(nR).
III. P ROBLEM FORMULA TION
In this section, we analyze the detection method of the occlu-
sion effect in environment sensing, and based on this, we convert
the environment sensing problem into a CS reconstruction prob-
lem with occlusion effect.
A. Occlusion Detection Model
We detect the occlusion effect between scatterers based on the
geometric positions between pixels. As shown in Fig. 3, there is
a pixel C with a scattering coefﬁcient greater than the threshold
η between pixels A and B. We believe that pixel C will cause
an occlusion effect. Let the position of pixel A be the origin
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3602 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
Fig. 3. An illustration of the environmental scatterer occlusion detection.
of coordinates, then the position vectors of pixel B and C are
expressed as b and c respectively. According to the following
conditions, it is considered that pixel C blocks the line-of-sight
path between pixels A and B.r The distance d between pixel C and the line-of-sight path
between pixels A and B is less than the threshold l,
d = |c× b||b| <l , (3)
where the detection threshold l should be selected accord-
ing to the side length or diagonal length of the small cube,
that is, l ∈ [min{ls,w s,h s},(l2s +w2s +h2s)1/2].r The angle between vector b and vector c is an acute angle,
which means that pixel C is located in the same direction
of the line-of-sight path from pixel A to pixel B, but not
pixel A is located between the pixel B and the pixel C. It
is expressed as
b· c > 0. (4)
r Pixel C is located between pixel A and pixel B, which is
expressed as
|c· b| < |b|2 . (5)
According to the above occlusion detection method, we de-
sign the environment sensing algorithm. However, the proposed
occlusion detection method is not the only method, and the
proposed environment sensing algorithm does not depend on
the uniqueness of the occlusion detection method.
B. Environment Compressed Sensing Model
As mentioned in Section I, since the distribution of scatterers
in the environment is sparse, according to the CS theory, the
optimization problem of solving environmental information is
expressed as
ˆx =a r gm i n
x
‖x‖1 s.t.
‖‖Y − S(HS + HLOS)‖‖2 ≤ ε, (6)
whereε is a slack variable. In the system model of Section II-B,
We can calculate the free space channel coefﬁcients HLOS(nR)
and H(nR) through the basic free space path propagation model.
In addition, some empirical models, simpliﬁed models, or inter-
polation methods are also suitable, and the appropriate model
needs to be selected according to the practical environment.
The BS estimates the multipath channel HS(nR) by detecting
the UE pilot and calculating the relationship with the received
signal Y(nR). Therefore, in general, in order to achieve accurate
channel estimation (e.g. least-squares channel estimation), the
pilot length should be greater than the number of users, that is,
NT >N u. The proposed algorithm does not rely much on the
method of channel estimation. Note that the channel estimation
is only the ﬁrst step of the overall integrated sensing and commu-
nication process. The subsequent environment sensing problem
studied here is always an underdetermined CS problem with
given channel matrix. Due to the large propagation range of
wireless signals, according to different precision requirements,
the number of pixelsNs will be greater thanNuNR.A tt h es a m e
time, based on the sparsity of the environmental information x,
the optimization problem (6) is expressed as the CS reconstruc-
tion problem equation
⎡
⎢⎢⎢⎢⎢⎣
HS(1)
...
HS (nR)
...
HS (NR)
⎤
⎥⎥⎥⎥⎥⎦
NuNR×1
=
⎡
⎢⎢⎢⎢⎢⎣
˜H(1)
...˜H(nR)
...˜H(NR)
⎤
⎥⎥⎥⎥⎥⎦
NuNR×Ns
[x]Ns×1,
⇒ HS = ˜Hx, (7)
where ˜H is formed by splicing the multipath channel matrix
˜H(nR) between NR receiving antennas and Nu users. In the
multi-BS joint environment sensing scheme, NR receiving an-
tennas include the number of all antennas on multiple BSs.
IV . ENVIRONMENT SENSING ALGORITHM UNDER THE
OCCLUSION EFFECT
In this section, we propose an environment sensing algorithm
called GAMP-MVSVR under the occlusion effect to solve the
environment information x in the (7). According to (2), (7) is
expressed as
HS = ˜Hx =( H⊙ V) x, (8)
where channel matrix H is formed by splicing channel matrix
H(nR) of NR receiving antennas, and occlusion matrix V is
formed by splicing occlusion matrix V(nR) of NR receiving
antennas.
A. Overview of the Proposed GAMP-MVSVR Algorithm
Different from the traditional CS reconstruction problem,
solving the environment sensing problem with occlusion effect
requires not only solving the environment informationx but also
needs to consider the unknown occlusion matrix V. Traditional
CS reconstruction algorithms, such as GAMP algorithm [25],
can solve environmental information in an ideal (ignoring oc-
clusion, ˜H = H) situation. In this way, since the accurate
measurement matrix ˜H cannot be obtained, the environmental
information x cannot be accurately solved. Compared with the
GAMP algorithm, the Bilinear GAMP algorithm [28] can solve
the bilinear problem, that is, simultaneously solve the occlusion
matrix V and the environmental informationx. However, it does
not consider the relationship between the occlusion effect and
the environmental information, the Bilinear GAMP algorithm
cannot constrain the uniqueness and accuracy of the occlusion
matrix V and the environmental information x.
Fig. 4 shows a sketch of the proposed GAMP-MVSVR algo-
rithm. In Section IV -B, we propose a factor graph based on the
decomposition result of the joint posterior probability. Based on
the sum-product algorithm (SPA) algorithm, we calculate the
message passed in the factor graph, and deﬁne the prior proba-
bility and likelihood function. In Section IV -C, we approximate
the message from factor node to variable node. Through the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3603
Fig. 4. A sketch of the proposed GAMP-MVSVR algorithm.
approximate process, we use the result in the previous iteration
to calculate its corresponding multipath channel. We compare
it with the channel ˆHS estimated by the pilot and calculate the
residual to guide this iteration. In Section IV -D, we approxi-
mate the message from variable node to factor node. Through
the approximate process, according to the occlusion effect, we
estimate ˜H and x based on the residual. In Section IV -E, We
update the intermediate variables in Section IV -C and IV -D,
and achieve the iterative execution of the estimation methods
in Section IV -C and IV -D.
B. Factor Graph and Passed Messages
As mentioned in Section III-B, let ˆHS be the multipath
channel estimated by the pilot, then ˆHS = HS + We, where
We represents the estimation error. The estimation error We
is caused by two main reasons, including the multipath channel
estimation error caused by pilot estimation and the free space
channel estimation error caused by modeling estimation. In
order to simplify the analysis, we assume that the noise We
obeys a Gaussian distribution. The joint posterior distribution
of the occluded multipath channel ˜H and the environmental
information x is expressed as
px, ˜H| ˆHS
(
x, ˜H| ˆHS
)
= p ˆHS|x, ˜H
(
ˆHS|x, ˜H)px (x)p ˜H|x( ˜H|x)/p ˆHS ( ˆHS)
∝ p ˆHS| ˜Hx
(
ˆHS| ˜Hx)px (x)p ˜H|x( ˜H|x)
= p ˆHS|HS
(
ˆHS|HS
)
px (x)p ˜H|x
(
˜H|x
)
, (9)
where pHS(HS) is a constant. To simplify the expression, let
NH = NuNR denote the length of the multipath channel vector
ˆHS. As shown in Fig. 5, according to the (9), the posterior
distribution is expressed in the form of a factor graph.
As shown in Fig. 5, the circles represent the variable nodes ˜H
and x, the squares represent the factor node p ˆHS|HS( ˆHS|HS),
px(x) and p ˜H|x( ˜H|x). The lines between the nodes represent
that the variables are included in the function of the factor nodes.
Speciﬁcally, the environmental information prior probability
functionpx(x) contains the environmental information variable
x. The relationship between the environmental information
Fig. 5. The factor graph of joint posterior distribution.
variable x and the channel with occlusion ˜H conforms to the
occlusion detection model function p ˜H|x( ˜H|x). The multipath
channel observation function p ˆHS|HS( ˆHS|HS) contains the en-
vironmental information variable x and the free space channel
˜H. The speciﬁc function is expressed as follows: ˆHS can be
considered as the observation of HS under the interference of
additive white Gaussian noise, i.e.,
pˆhSnH|hSnH
(
ˆhSnH|hSnH
)
= N
(
ˆhSnH;hSnH,σ w
)
, (10)
where σw is the variance of Gaussian white noise. Due to the
sparseness of environmental information x, we assume that the
x obeys a Bernoulli-Gaussian distribution,
px (x)=( 1 −λ)δ(x)+ λN (x;θx,σ x), (11)
whereλ is the sparsity of the environment, θx andσx represent
the mean and variance of the scattering coefﬁcient of the envi-
ronmental scatterer. p ˜H|x( ˜H|x) represents the occlusion effect
of environmental information x on the channel, i.e.,
p˜hnH,ns|x
(
˜hnH,ns|x
)
=
⎧
⎨
⎩
δ
(
˜hnH,ns −hnH,ns
)
vnH,ns = focc (x)=1
δ
(
˜hnH,ns
)
vnH,ns = focc (x)=0
, (12)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3604 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
where focc(·) represents the occlusion detection function, the
speciﬁc method is as described in the Section III-A, and the
occlusion detection threshold is set to η = θx/4.
Based on the sparse prior information and occlusion rela-
tionship of environmental information, we aim to obtain the
minimum mean square error (MMSE) estimate of environmental
information
ˆxMMSEns =a r gm i nˆxns Ex
[
(xns − ˆxns)2
]
. (13)
According to the loopy belief propagation (LBP) theory [29],
based on the factor graph model, we calculate the MMSE
estimated value of the environment information through the
SPA [30]. As explained in Appendix A, the method of SPA mes-
sage passing is as follows. As shown in Fig. 5, the output message
of the variable node along the edge (solid line) is obtained by
calculating the product of all its input messages. The output
message of the factor node is calculated by multiplying and
integrating the function of the factor node and its input message.
The marginal distribution of the variable is calculated from the
product of all messages input to the node. Since it is difﬁcult
to accurately calculate the passed message, we approximate the
message in the following sections.
C. Approximated Factor-to-V ariable Messages
In this section, we approximate the message from the factor
node to the variable node according to the central limit the-
orem (CLT) and Gaussian approximation based on the idea
of approximate message passing [24], [25], [28]. Based on
CLT, whenNs →∞ , NH/Ns remains constant, we drop some
high-order inﬁnitesimal terms. In the t iteration, the sparsity
λ in the prior distribution of environmental information px(x)
remains constant. As mentioned in Section III-A and Section V,
the number of zero elements in the occlusion matrix V in the
variable ˜H remains ﬁxed, and the position of the zero elements
is determined byˆxns . Therefore, we consider that variableˆxns is
independent of variableˆhnH,ns in thet-th iteration. As explained
in Appendix B, the passed message in (62) is approximated as
μˆhSnH→xns (t,xns)=l o g
∫
hSnH
pˆhSnH|hSnH
(
ˆhSnH
⏐⏐hSnH)
×N
(
hSnH;¯hnHns,nH(t)xns +¯pns,nH(t),
σhnHns,nH(t)x2ns +σpns,nH(t))+c
= FnH
(¯hnHns,nH(t)xns +¯pns,nH(t),
σhnHns,nH(t)x2ns +σpns,nH(t);ˆhSnH
)
+c,
(14)
where
FnH
(
¯p,σ p;ˆhS
)
=l o g
∫
hS
pˆhS|hS
(
ˆhS|hS
)
N
(
ˆhS;¯p,σ p
)
.
(15)
Adding the ns- t ht e r mt ot h es u m m a t i o ni n¯pns,nH(t) in (71),
then ¯pnH(t) and σpnH(t) are considered as an estimate of hSnH ,i.e.,
¯pnH(t)=
Ns∑
k=1
¯hnHk,nH(t)¯xk,nH(t), (16)
σpnH(t)=
Ns∑
k=1
(¯h2nHk,nH(t)σxk,nH(t)
+σhnHk,nH(t)¯x2k,nH(t)+ σhnHk,nH(t)σxk,nH(t)).
(17)
We deﬁne a residual variable whose mean value is,
¯snH(t)= F′nH,1
(
¯pnH(t),σ pnH(t);ˆhSnH
)
, (18)
due to the Gaussian property ofFnH , the variance of the residual
is expressed as,
σsnH(t)= −F′′nH,1
(
¯pnH(t),σ pnH(t);ˆhSnH
)
. (19)
whereF′nH,1 andF′′nH,1 represent the ﬁrst and second derivatives
of the ﬁrst argument of FnH , and F′nH,2 represents the ﬁrstderivative of the second argument of FnH .
As explained in Appendix C, we get the ﬁnal approximation
result of the passed message μˆhSnH→xns (t,xns) in (62)
μˆhSnH→xns (t,xns)
≈
[
¯snH(t)¯hnHns,nH(t)+ σsnH(t)ˆh2nH,ns(t)ˆxns(t)]xns
− 12[σsnH(t)ˆh2nH,ns(t)−σhnH,ns(t)
×
(
¯s2nH(t)−σsnH(t))]x2ns +c, (20)
According to (16), ¯pnH is considered to be an estimate of HS,
we can express the posterior probability of HS as the product of
the prior probabilityN(hSnH;¯pnH(t),σ pnH(t)) and the likelihood
pˆhSnH|hSnH (ˆhSnH|hSnH) as follows
phSnH|pnH
(
hSnH|¯pnH(t);σpnH(t))
= 1CpˆhSnH|hSnH
(
ˆhSnH|hSnH
)
N
(
hSnH;¯pnH(t),σ pnH(t)), (21)
where C =
∫
hS phSnH|pnH (hS|¯p(t);σp(t)) is a normalizationconstant. Then the mean and variance of (21) are the mean and
variance of calculated HS as follows
¯hSnH(t)= E{hSnH|¯pnH(t);σpnH(t)}, (22)
σHsnH(t)= D{hSnH|¯pnH(t);σpnH(t)}, (23)
where E(X)=
∫
xf(x)dx represents the mean of x and
D(X)=
∫
[x− E(X)]2f(x)dx represents the variance of x.
Pluging (21), (22), and (23) into (18) and (19). Based on the
likelihood in (10), according to the derivation in [25], [28], the
mean and variance of the residual are expressed as
¯snH(t)=
ˆhSnH − ¯pnH(t)
σpnH(t)+ σw , (24)
σsnH(t)= 1σpnH(t)+ σw . (25)
As mentioned in this section, in the t-th iteration, we con-
sider that variable x is independent of variable ˜H,s ot h e
same as the derivation of (20), we approximate the message
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3605
μˆhSnH→˜hnH ,ns (t,˜hnH,ns) in (64) as
μˆhSnH→˜hnH,ns
(
t,˜hnH,ns
)
≈
[
¯snH(t)¯xns,nH(t)+ σsnH(t)ˆx2ns(t)ˆhnH,ns(t)]˜hnH,ns
− 12[σsnH(t)ˆx2ns(t)−σxns(t)
×
(
¯s2nH(t)−σsnH(t))]˜h2nH,ns +c. (26)
In summary, in this section we approximate the message from
factor node to variable node as follows. We calculate ¯pnH(t) (as
shown in (16)) to obtain the calculated channel¯hSnH(t) (as shown
in (22)). Then we calculate the residual ¯snH(t) according to¯hSnH(t) and the channel estimation value using the pilot ˆhSnH (asshown in (24)). Finally, we use the residual and the approximate
mean and variance of the passed message to represent the
message from the factor node to the variable node (as shown
in (20) and (26)).
D. Approximated V ariable-to-Factor Messages
In this section, we approximate the message from the factor
node to the variable node. We plug (20) in (63), the mes-
sage μxr→ˆhSnH (t+1,xr) from variable node x to factor node
p ˆHS|HS( ˆHS|HS) is approximated as
μxns→ˆhSnH (t+1,xns)
=l o gpx (xns)− 12σrns,nH(t)(xns − ¯rns,nH(t))2 +c
=l o g
(
px (xns)N
(
xns;¯rns,nH(t),σ rns,nH(t)))+c, (27)
where
¯rnH,ns(t)
=ˆxns(t)
⎛
⎝1+ σrns,nH(t)∑
k⁄=nH
σhk,ns(t)[¯s2k(t)−σsk(t)]
⎞
⎠
+σrns,nH(t)∑
k⁄=nH
ˆhk,ns(t)¯sk(t), (28)
σrns,nH(t)
=
⎛
⎝∑
k⁄=nH
ˆhk,ns(t)σsk(t)−σhk,ns(t)(¯s2k(t)−σsk(t))
⎞
⎠
−1
.
(29)
Then the mean ¯xns,nH(t+1) and variance σxns,nH(t+1) ofthe passed message in (27) are expressed as,
¯xns,nH (t+1)
= 1C∫xns xnspx (xns)N(xns;¯rnH,ns(t),σ rnH,ns(t))
= Gx
(
¯rnH,ns(t),σ rnH,ns(t)), (30)
σxns,nH (t+1)= σrnH,ns(t)G′x(¯rnH,ns(t),σ rnH,ns(t)), (31)
whereC =
∫
xns px(xns)N(xns;¯rnH,ns(t),σ rnH,ns(t)) is a nor-
malization constant, and G′x represents the ﬁrst derivative of
the ﬁrst argument of the Gx. The speciﬁc derivation of the
relationship between (30) and (31) was shown in [25].
Adding the nH-th term to the summation in ¯rnH,ns(t), then
¯rns(t) andσrns(t) are expressed as
¯rns(t)=ˆxns(t)
(
1+ σrns(t)
NH∑
k=1
σhk,ns(t)[¯s2k(t)−σsk(t)]
)
+σrns(t)
NH∑
k=1
ˆhk,ns(t)¯sk(t), (32)
σrns(t)=
(NH∑
k=1
ˆhk,ns(t)σsk(t)−σhk,ns(t)(¯s2k(t)−σsk(t))
)−1
,
(33)
Based on AMP [24], [25], [28], ¯rns(t) andσrns(t) are consid-ered as an estimate of xns as follows
ˆxns (t+1)= Gx
(
¯rns(t),σ rns(t)), (34)
σxns (t+1)= σrns(t) G′x(¯rns(t),σ rns(t)), (35)
where G′x represent the ﬁrst derivative of the ﬁrst argument of
Gx. Finally, we calculate the relationship between the mean of
the passed message ¯xns,nH(t+1) and the mean of the marginal
distribution ˆxns(t+1) as follows
¯xns,nH (t+1)
≈ Gx
(
¯rns(t)−σrns(t)ˆhnH,ns(t)¯snH(t),σ rns(t))
≈ Gx
(
¯rns(t),σ rns(t))
−σrns(t)ˆhnH,ns(t)¯snH(t)G′x(¯rns(t),σ rns(t))
=ˆxns (t+1) −ˆhnH,ns(t)¯snH(t)σxn (t+1) , (36)
in which we drop inﬁnitesimal terms such asσrns,nH(t)−σrns(t)in the second step of approximation, and we perform Taylor
series expansion on the ﬁrst argument of the function at point
¯rns(t) and drop the inﬁnitesimal term in the second step of
approximation.
In the t-th iteration, we consider that variable x is indepen-
dent of variable ˜H and recalculate the relationship between
variables ˜H and x after each iteration. Therefore, we approxi-
mate the passed message from variable node ˜H to factor node
p ˆHS|HS( ˆHS|HS) the same way as (27), and calculate the mean
ˆhnH,ns(t+1) and the variance σhnH,ns(t+1) of the marginal
distribution of variable ˜H the same way as (34) and (35), i.e.,
ˆhnH,ns (t+1)= GH(¯qnH,ns(t),σ qnH,ns(t)), (37)
σhnH,ns (t+1)= σqnH,ns(t)G′H(¯qnH,ns(t),σ qnH,ns(t)), (38)
GH
(
¯qnH,ns(t),σ qnH,ns(t)) = 1C∫˜h ˜hnH,nsp˜hnH ,ns|x
(
˜hnH,ns|x
)
×N
(
˜hnH,ns;¯qnH,ns(t),σ qnH,ns(t)), (39)
where C =
∫
˜h p˜h|x(˜h|x)N(˜h;¯q(t),σ q(t)) is a normalization
constant, G′H represent the ﬁrst derivative of the ﬁrst argument
ofGH, ¯qnH,ns(t) andσqnH,ns(t) are considered as an estimate of
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3606 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
˜hnH,ns as follows
¯qnH,ns(t)= ˆhnH,ns(t)(1+ σqnH,ns(t)σxns(t)(
¯s2nH(t)−σsnH(t))+σqnH,ns(t)¯xns,nH (t)¯snH (t)), (40)
σqnH,ns(t)= (ˆx2ns(t)σsnH(t)−σxns(t)(¯s2nH(t)−σsnH(t)))−1.
(41)
Similar to the approximation process of (36), we calcu-
late the relationship between the mean of the passed message
¯hnHns,nH(t+1) and the mean of the marginal distribution
ˆhnH,ns(t+1) as follows
¯hnHns,nH (t+1)= ˆhnH,ns (t+1) − ˆxns(t)¯snH(t)σhnH,ns(t).(42)
Since the environmental information x is an unknown vari-
able, in the t+1 -th iteration, we use ˆx(t) instead of x for
occlusion detection, (39) is expressed as
GH
(
¯qnH,ns(t),σ qnH,ns(t)) = 1C∫˜h ˜hnH,ns
p˜hnH,ns|ˆx(t)
(
˜hnH,ns|ˆx(t)
)
N
(
˜hnH,ns;¯qnH,ns(t),σ qnH,ns(t)).
(43)
In summary, in this section we approximate the message from
variable node to factor node as follows. Firstly, we calculate
¯rns(t) and ¯qnH,ns(t) based on the residual ¯snH (t) (as shown in
(32) and (40)), and calculate the new estimated valuesˆxns(t+1)
and ˆhnH,ns(t+1) (as shown in (34) and (37)). Secondly, since
the message from the variable node to the factor node is similar
to the posterior probability, we approximate the relationship
between the estimated value ˆxns(t+1) , ˆhnH,ns(t+1) and the
passed message ¯xns,nH(t+1) , ¯hnHns,nH(t+1) (as shown in
(36) and (42)).
E. Algorithm Iterative Execution
In Section IV -C and Section IV -D, we have obtained the esti-
mation methods for variables ˆxns(t+1) andˆhnH,ns(t+1) ,b u t
the intermediate variables ¯pnH(t), ¯rns(t), and ¯qnH,ns(t) contain
the passed messages ¯xns,nH(t+1) and ¯hnHns,nH(t+1) .W e
need to replace the passed message with the current estimated
variable ˆxns(t+1) and ˆhnH,ns(t+1) to calculate these inter-
mediate variables again to achieve the iteration of the algorithm.
Pluging (36) and (42) into (16), we can get
¯pnH(t) ≈
Ns∑
k=1
ˆhnH,k(t)ˆxk(t)− ¯snH (t−1)
×
Ns∑
k=1
(
σhnH,k(t)ˆx2k(t)+ ˆh2nH,k(t)σxk(t)), (44)
where we replace ˆxk(t)ˆxk(t−1) with ˆx2k(t), replaceˆhnH,k(t)ˆhnH,k(t−1) with ˆh2nH,k(t), and drop the inﬁnitesimal
term under the CLT condition. In most AMP algorithms [25],
[28], (44) can be interpreted as the Onsager correction to
ˆhnH,k(t)ˆxk(t), and (17) is expressed as
σpnH(t) ≈
Ns∑
k=1
(
σhnH,k(t)ˆx2k(t)
+ˆh2nH,k(t)σxk(t)+ σhnH,k(t)σxk(t)). (45)
Algorithm 1: Proposed GAMP-MVSVR Algorithm.
Input: Given the free space channel coefﬁcient H and the
estimated value of the uplink multipath channel ˆHS.
1: Initialization: For each nH andns, set the prior
probabilitypx(x) of environmental information x in
(11), and choose ˆxns(1) andσxns(1). Set the likelihood
pˆhSnH|hSnH (ˆhSnH|hSnH) in (10). Set ¯snH(0) = 0.
2: For each nH andns,p l u gˆxns(1) into (12), calculate
the free space channel coefﬁcient distribution
p˜hnH ,ns|x(1)(˜hnH,ns|x(1)) with occlusion, and chooseˆhnH,ns(t) and σhnH,ns(t).3: fort =1 ,2,...,T max do
4: For each nH,p l u gˆxns(t), σxns(t), ˆhnH,ns(t), and
σhnH,ns(t) into (44) and (45) to obtain ¯pnH(t) and
σpnH(t).
5: For each nH,p l u g¯pnH(t), σpnH(t), and
pˆhSnH|hSnH (ˆhSnH|hSnH) into (22) and (23) to obtain¯hSnH(t) andσHsnH(t).
6: For each nH,p l u gˆhSnH , ¯pnH(t), and σpnH(t) into (24)
and (25) to obtain ¯snH(t) and σsnH(t).
7: For each ns,p l u gˆxns(t), σxns(t), ˆhnH,ns(t),
σhnH,ns(t), ¯snH(t), and σsnH(t) into (46) and (47) to
obtain ¯rns(t) andσrns(t).
8: For each nH and ns,p l u gˆxns(t), σxns(t), ˆhnH,ns(t),
σhnH,ns(t), ¯snH(t), and σsnH(t) into (48) and (49) to
obtain ¯qnH,ns(t) andσqnH,ns(t).
9: For each ns,p l u g¯rns(t) andσrns(t) into (34) and
(35) to obtain ˆxns(t+1) andσxns(t+1) .
10: For each nH and ns,p l u g¯qnH,ns(t), σqnH,ns(t), and
p˜hnH ,ns|x(t)(˜hnH,ns|x(t)) into (37) and (38) to
obtain ˆhnH,ns(t+1) andσhnH,ns(t+1) .
11: For each nH and ns,p l u gˆxns(t+1) into (12) to
obtain the free space channel coefﬁcient distribution
with occlusion p˜hnH ,ns|ˆx(t+1)(˜hnH,ns|ˆx(t+1)) .
12: If ∑nH |ˆhSnH −¯hSnH(t)| >ε t, where εt is a givenerror tolerance value, stop the iteration.
13: end for
Output: Estimated sparse vector ˆxns(t) andσxns(t).
Similar to the approximate method in the (44), pluging (36)
and (42) into (32) and (33), it yields
¯rns(t) ≈ ˆxns(t)
(
1−σrns(t)
NH∑
k=1
σhk,ns(t)σsk(t)
)
+σrns(t)
NH∑
k=1
(
ˆhk,ns(t)¯sk(t)
)
, (46)
σrns(t) ≈
(NH∑
k=1
ˆh2k,ns(t)σsns(t)
)−1
. (47)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3607
And similar to the approximate method in the (44), pluging
(36) and (42) into (40) and (41), it yields
¯qnH,ns(t) ≈ ˆhnH,ns(t)(1−σqnH,ns(t)σxns(t)σsnH(t))
+σqnH,ns(t)ˆxns(t)¯snH(t), (48)
σqnH,ns(t) ≈(ˆx2ns(t)σsnH(t))−1. (49)
We summarize the proposed GAMP-MVSVR algorithm in
Algorithm 1. During the execution process of the GAMP-
MVSVR algorithm, the approximate message passing and the
occlusion detection method execute repeatedly and converge to
the estimated value of environmental information. The com-
putational complexity of the GAMP-MVSVR algorithm con-
sists of two parts: approximate message passing and occlusion
detection method. The computational complexity is expressed
as O(NHNs +NHNs‖x‖0), where ‖x‖0 is the number of the
environmental scatterers, the number of pixels Ns has a major
inﬂuence on the computational complexity. The setting of Tmax
is to stop the iteration in time when the system performance
is poor. Due to the small order of magnitude of iterations, the
number of algorithm iterations will hardly reach Tmax, and
we omit the term Tmax when calculating the computational
complexity.
V. S YSTEM PERFORMANCE ANAL YSIS
In this section, we compare the performance of the single-BS
environment sensing scheme and the multi-BS joint environment
sensing scheme from two aspects: environment sensing range
and environment sensing accuracy.
A. Environment Sensing Range
In this section, we analyze the impact of the CS measurement
matrix ˜H on the system performance. According to the CS
reconstruction model in Section III-B, the environment sens-
ing range is determined by the CS measurement matrix ˜H.
Speciﬁcally, the number of 0 elements in the occlusion matrix
V, VU→s, and Vs→B is calculated to obtain the environment
sensing range.
As mentioned in Section II-B, the number of pixels isNs, and
the position of ns-th pixel is asns =[ xsns,y sns,z sns]. The numberof users in the environment is Nu, and the position of nu-th
user is aunu =[ xunu,y unu,z unu]. In the multi-BS joint environmentsensing scheme, the number of BSs in the environment is NB,
and the position of nB-th BS is aBnB =[ xBnB,y BnB,z BnB]. Under
these deﬁnitions, the analysis of the occlusion matrix VU→s and
Vs→B is summarized in the following theorem.
Theorem 1: The probability that the element in the occlusion
matrix VU→s is 0 can be expressed as
p
(
VU→snu,ns =0) =1 −
‖‖VU→s‖‖1
Nu ×Ns
=
∫
aunu,asns
pu
(
aunu
)
λl2‖‖aunu − asns‖‖2
(LsWsHs)2 ,
(50)
where pu(aunu) is the distribution function of nu-th user in theenvironment. For the receiving antenna deployed on the nB-
th BS, the probability that the element in the occlusion matrix
Vs→B(nR) is 0 can be expressed as
p
(
Vs→Bns (nR)=0 ) =1 −
‖‖Vs→B‖‖1
Ns
=
∫
aBnB,asns
pB
(
aBnB
)
λl2‖‖aBnB − asns‖‖2
(LsWsHs)2 ,
(51)
where pB(aBnB) is the distribution function of nB- t hB Si nt h eenvironment.
Proof: According to the occlusion detection model in
Section III-A, when there is a scatterer in the space of size
l2‖aunu − asns‖2 between the nu-th user and the ns-th pixel,the EM propagation path is blocked. The location distribution
function pu(aunu) of each user is independent, and the divisionof pixels is uniform. Therefore, in the space of size LsWsHs,
the probability of a scatterer between the nu-th user and the
ns-th pixel is denoted as (50). In the occlusion detection model,
the analysis methods of the BS and the user are the same.
Therefore, according to (50), replacing pu(aunu) with pB(aBnB)
and replacing asns with aBnB , we obtain (51). ■
The occlusion matrix VU→s reﬂects the different views from
different users. In the single-BS environment sensing scheme
and the multi-BS joint environment sensing scheme, the multi-
views from users are the same. As mentioned in Section II-B,
when VU→s contains an all-zero column, it means that all users
cannot sense the corresponding pixel, and the pixel is out of the
user sensing range. According to Theorem 1, when the number
of users isNu, the probability that the pixels in the environment
are outside the user sensing range is
p
(
VU→s:,ns = 0) = pNu (VU→snu,ns =0). (52)
Let Vs→B =[ Vs→B(1), Vs→B(2), ..., Vs→B(NR)] ∈
{0,1}Ns×NR and the occlusion matrix Vs→B reﬂects the dif-
ferent views from different BSs. In the single-BS environment
sensing scheme, since the receiving antennas are deployed close
to each other, they have almost the same views to the scatterers
in the environment. Therefore, the probability that a pixel is
outside the sensing range of a single BS is p(Vs→Bns (nR)=0 ).
In the multi-BS joint environment sensing scheme, when Vs→B
contains an all-zero row, it means that all BSs cannot sense
the corresponding pixel, and the pixel is out of the BS sensing
range. According to Theorem 1, since the location distribution
probability of each BS is independent, the probability that a
pixel in the environment is outside the sensing range of the
BS is
p
(
Vs→Bns,: = 0) = pNB (Vs→Bns (nR)=0 ). (53)
According to (50), (51), (52), and (53), we calculate the mean
value ¯Ncon of the number of pixels that cannot be sensed in the
single-BS environment sensing scheme and the mean value ¯Ndis
of the number of pixels that cannot be sensed in the multi-BS
joint environment sensing scheme as
¯Ncon = Ns(pNu (VU→snu,ns =0)+p(Vs→Bns (nR)=0 )
−pNu (VU→snu,ns =0)p(Vs→Bns (nR)=0 )), (54)
¯Ndis = Ns(pNu (VU→snu,ns =0)+pNB (Vs→Bns (nR)=0 )
− pNu (VU→snu,ns =0)pNB (Vs→Bns (nR)=0 )). (55)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3608 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
The multi-BS joint environment sensing has a larger sensing
range than single-BS environment sensing. In practical appli-
cations, a multi-BS scheme should be implemented according
to the BS location. When the multi-BS scheme is difﬁcult to
implement, e.g., when the BSs are far away and users cannot
communicate with each BS, a single-BS scheme should be used.
In addition, if there is a failure of environment sensing for some
pixels, a larger number of base stations and users or users after
moving locations should be used for joint sensing.
B. Environment Sensing Accuracy
In this section, we analyze the impact of environmental infor-
mation x on system performance. The mean square error (MSE)
between the estimated environmental information ˆx and the real
environmental information x is used to describe the accuracy of
environment sensing, i.e.,
MSE = 1Ns ‖x− ˆx‖22 . (56)
According to the CS reconstruction model in Section III-B
(6), the reconstruction problem in (7) is expressed as
ˆx =a r gm i n
x
‖x‖1 s.t.
‖‖‖HS − ˜Hx‖‖‖
2
≤ ε, (57)
whereε is a slack variable. We consider that the performance of
environment sensing methods for solving the occlusion problem
should be as close as possible to the upper limit in Theorem 2.
Theorem 2: The upper bound of the environment sensing
error when the CS measurement matrix ˜H = H under the ideal
(no occlusion, the occlusion detection is completely correct)
situation is
MSE ≤ m·R2 ·logNs
Ns ·Nu ·NR
, (58)
wherem is a normalized constant, and
R =
⎧
⎪⎨
⎪⎩
Rcon = ‖xcon‖1 = λθx(Ns − ¯Ncon),for single-BS scheme,
Rdis = ‖xdis‖1 = λθx(Ns − ¯Ndis),for multi-BS scheme. (59)
Proof: According to the CS theory [21],
‖x− ˆx‖2 ≤ m·R·(NH/logNs)1/2−1/ps , (60)
where, ‖x‖ps ≤ R. Pluging (56) and (57) into (60), we obtain
(58). According to (57), let ps =1 , we get the values of Rcon
andRdis. ■
Remark 1: When the number of BS antennas or the number of
users increases, the upper bound of environment sensing error
MSE decreases. When the environment sparsity λ and other
system parameters remain constant, the number of pixels Ns
increases (this means a wider sensing range or higher sensing
resolution), the upper bound of environment sensing error MSE
increases. Therefore, wider and more accurate sensing results
require more resource costs.
According to (54) and (55), under the condition that the num-
ber of users is the same and the total number of antennas of all
BSs is the same, the number of environmental scatterers sensed
by multiple BSs is more than that of a single BS, Rdis >R con.
Therefore, according to (58), for the scatterers in the sensing
range, the upper bound of MSE of multi-BS joint environment
sensing is higher than that of the single-BS scheme. However,
in practical applications, the total number of antennas deployed
by multiple BSs is usually more than that of a single BS. The
increase in the number of antennasNR will signiﬁcantly improve
system performance.
We analyze the probability distribution of the occlusion matrix
caused by the environmental scatterers as shown in Corollary 1.
Corollary 1: The elements in the occlusion matrixV conform
to the Bernoulli distribution. The probability that the element in
the occlusion matrix Vnu,ns(NR) is 0 can be expressed as
p(Vnu,ns (NR)=0 )
= p
(
VU→snu,ns =0)+p(Vs→Bns (nR)=0 )
− p
(
VU→snu,ns =0)p(Vs→Bns (nR)=0 )
Ns
(61)
Proof: According to V(nR)= VU→sdiag(Vs→B(nR)),a s
shown in Theorem 1, the probability that the element in the
occlusion matrix Vnu,ns(NR) is 0 can be calculated by VU→s
and Vs→B(nR). ■
Therefore, the unknown occlusion matrix V is equivalent to
causing a multiplicative Bernoulli perturbation to the known
free space channel matrix H as shown in (8). At present,
some works [31], [32] have analyzed the compressed sensing
reconstruction performance under the condition that there is a
speciﬁc perturbation in the compressed sensing measurement
matrix. In this paper, the proposed algorithm iteratively elim-
inates the perturbation to the measurement matrix caused by
the occlusion effect according to the results of each iteration
and obtains accurate imaging results. The system performance
analysis of this iterative detection process will be future work,
and extensive simulation results have veriﬁed the effectiveness
and convergence of the proposed algorithm.
VI. N UMERICAL RESULTS
In this section, we simulate the performance of the algorithm.
In order to reduce the computational cost and reﬂect the envi-
ronment sensing accuracy, we set up a small-scale simulation
sensing region, the environmental scatterers are distributed in
the sensing region of 5 m × 5m × 5 m, and the sensing region
is evenly divided into 10×10×10 pixels. Multiple BSs and
users are randomly distributed in or around the sensing region.
The carrier frequency of the uplink signal is set to 30 GHz. The
positions of scatterers distributed in sensing region are random,
and the scattering coefﬁcient is set to xns ∈ [0,1].A ss h o w ni n
the Figs. 6 and 7, small cubes are used to represent the position
and scattering coefﬁcient of pixels. The lower the transparency
of the small cubes, the higher the scattering coefﬁcient of the
pixel.
In this section, as mentioned in Section IV -A, we choose
GAMP and Bilinear GAMP algorithm as the baseline algorithms
to solve the environment sensing problem under the occlusion
effect. Compared with the two baseline algorithms, in this paper,
the proposed GAMP-MVSVR algorithm based on the occlu-
sion effect signiﬁcantly improves the accuracy of environment
sensing.
Fig. 6 shows the results of the single-BS environment sensing,
where the gray cubes represent scatterers that are out of the
sensing range due to the occlusion effect. The system parameters
are set to the number of users Nu =2 0, a single BS is deployed
with a 5×5 array antenna, and the signal-to-noise ratio (SNR)
Eb/N0 = 20dB. Compared with the baseline algorithms, it
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3609
Fig. 6. The original environment scatterer distribution and single-BS environment sensing results.
can be seen that the proposed algorithm clearly and accurately
obtains the shape of the original target.
Fig. 7 shows the results of the multi-BS joint environment
sensing. In order to make the total number of antennas deployed
in the environment the same, we reduce the number of antennas
on each BS. The system parameters are set to the number of users
Nu =2 0, 5 BSs are deployed with5×1 array antennas, and the
SNR Eb/N0 = 20 dB. Compared with the single-BS scheme,
as analyzed in (54) and (55), multi-BS joint environment sensing
scheme effectively increases the environment sensing range.
In Fig. 7, there is no scatterer that cannot be sensed even
though the occlusion effect is exist. It can be seen that the
sensing results of baseline algorithms are more blurred than the
results of the single-BS scheme. This is because, as analyzed in
Section V -B, when the total number of receiving antennas is
the same, multi-BS joint environment sensing has a larger en-
vironment sensing range, which causes a small decrease in the
accuracy of environment sensing within the sensing range.
Figs. 8 and 9 show the relationship between the single-BS
environment sensing performance, the multi-BS joint environ-
ment sensing performance and the number of users Nu, respec-
tively. The MSE between the environmental information within
the sensing range and the environmental information estimated
by the algorithm reﬂects the accuracy of environment sensing
within the sensing range. The system parameters are set as
follows: the single BS in the scenario in Fig. 8 is deployed with
a 5×5 array antenna, and 5 BSs in the scenario in Fig. 9 are
deployed with 5×1 array antennas, and the SNR Eb/N0 =
20 dB.
Remark 2: As analyzed in (58), as the number of users
increases or the number of environmental scatterers decreases,
the accuracy of environment sensing increases. Both the pro-
posed algorithm and the baseline algorithm perform poorly
when the number of users is small. But as the number of users
increases, the performance of the proposed algorithm improves
signiﬁcantly.
Fig. 10 shows the relationship between the number of users
and the MSE within the full range of two sensing schemes.
The MSE between the environmental information within the
full range and the environmental information estimated by the
algorithm reﬂects the size of the environment sensing range.
The system parameter settings of the two environment sensing
schemes are the same as those in Figs. 8 and 9, respectively.
Remark 3: As analyzed in (58), as the number of users
increases or the number of environmental scatterers decreases,
the accuracy of environment sensing increases. At the same time,
as analyzed in (54) and (55), for the full range of the environment,
the multi-BS scheme has a lower sensing error, so it effectively
increases the environment sensing range.
Figs. 11 and 12 show the relationship between the single-
BS environment sensing performance, the multi-BS joint
environment sensing performance and the SNREb/N0, respec-
tively. The system parameters are set as follows: the single BS in
the scenario in Fig. 11 is deployed with a 5×5 array antenna,
and 5 BSs in the scenario in Fig. 12 are deployed with 5×1
array antennas, and the number of users Nu =1 0.
Remark 4: As the SNR increases, the estimated value ˆHS
of the multipath channel is more accurate, and the accuracy
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3610 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
Fig. 7. The original environment scatterer distribution and multi-BS joint environment sensing results.
Fig. 8. The relationship between the number of users and the MSE within the
sensing range of the single-BS scheme.
of environment sensing increases. At the same time, the less
sparse the environmental scatterer distribution, the closer the
performance of the proposed algorithm and the baseline algo-
rithm are. This is because the more environmental scatterers
cause more occlusion, which reduces the performance of all
algorithms at the same time.
Fig. 13 shows the relationship between the SNR and the
MSE within the full range of two sensing schemes. The system
parameter settings of the two environment sensing schemes are
the same as those in Figs. 11 and 12, respectively.
Fig. 9. The relationship between the number of users and the MSE within the
sensing range of the multi-BS scheme.
Remark 5: As the SNR increases, the accuracy of environ-
ment sensing increases. At the same time, as analyzed in (54)
and (55), for the full range of the environment, the multi-BS
scheme has a lower sensing error, so it effectively increases the
environment sensing range.
As shown in Fig. 14, we provide performance curves under
various parameter settings to verify the convergence of the pro-
posed algorithm. The antenna settings of the multi-base station
scheme are the same as above.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3611
Fig. 10. The relationship between the number of users and the MSE within
the full range of two sensing schemes.
Fig. 11. The relationship between the SNR and the MSE within the sensing
range of the single-BS scheme.
Remark 6: As the number of iterations increases, the sensing
error MSE gradually decreases and converges. The sparser the
environmental information, the faster the algorithm converges
and the better the system performs. Meanwhile, the increase
in the number of users and the signal-to-noise ratio accelerates
algorithm convergence and improves system performance.
VII. C ONCLUSION
In this paper, we have designed a multi-view environment
sensing scheme taking into full consideration the occlusion
effect in an outdoor scenario. Based on the occlusion effect, we
have proposed a probabilistic reasoning model based on the fac-
tor graph. According to the AMP theory, the GAMP-MVSVR al-
gorithm is proposed to achieve multi-view environment sensing.
The proposed GAMP-MVSVR algorithm achieves environment
sensing by iteratively estimating the scattering coefﬁcients of the
cloud points and their occlusion relationship. In each iteration,
the occlusion relationship between the cloud points of the sparse
environment is recalculated according to the proposed occlusion
detection rule, and in turn, used to estimate the scattering coef-
ﬁcients of the cloud points. Our proposed algorithm achieves
improved sensing performance with multi-BS collaboration in
Fig. 12. The relationship between the SNR and the MSE within the sensing
range of the multi-BS scheme.
Fig. 13. The relationship between the SNR and the MSE within the full range
of two sensing schemes.
Fig. 14. The convergence performance of proposed algorithm.
addition to the multi-views from the users, which will provide
ideas for future ISAC system design.
APPENDIX A
According to the factor graph shown in Fig. 5, the logarithmic
form of the passed message is calculated as follows. In the t-th
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3612 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
iteration, the message μˆhSnH→xns (t,xns) passed from the factor
node p ˆHS|HS( ˆHS|HS) to the variable node x is
μˆhSnH→xns (t,xns)
=l o g
∫
{˜hnH ,k}Nsk=1,{xr}r⁄=ns
pˆhSnH|hSnH
(
ˆhSnH
⏐⏐⏐⏐⏐Ns∑k=1 ˜hnH,kxk)
×
∏
r⁄=ns
exp
(
μxr→ˆhSnH (t,xr)
)
×
Ns∏
k=1
exp
(
μ˜hnH ,k→ˆhSnH
(
t,˜hnH,k
))
+c, (62)
where the passed message μ is expressed in logarithmic form. c
is a normalization constant, so that the integral of the exponential
passed message exp(μˆhSnH→xns ) is 1. In the subsequent passedmessage and marginal distribution in this section, the constant
c has the same meaning. In the (t+1) -th iteration, the message
μxr→ˆhSnH (t+1,xr) passed from the variable node x to the
factor node p ˆHS|HS( ˆHS|HS) is
μxns→ˆhSnH (t+1,xns)
=l o gpx (xns)+
∑
k⁄=nH
μˆhSk→xns (t,xns)+ c. (63)
Let the mean and variance of the exponential form of the mes-
sage passed in (63) be ¯xns,nH(t+1) andσxns,nH(t+1) , respec-
tively. In thet-th iteration, the messageμˆhSnH→˜hnH,ns (t,˜hnH,ns)
passed from the factor node p ˆHS|HS( ˆHS|HS) to the variable
node ˜H is expressed as
μˆhSnH→˜hnH,ns
(
t,˜hnH,ns
)
=l o g
∫
{˜hnH ,r}r⁄=ns,{xk}Nsk=1
pˆhSnH|hSnH
(
ˆhSnH
⏐⏐⏐⏐⏐Ns∑k=1 ˜hnH,kxk)
×
Ns∏
k=1
exp
(
μxk→ˆhSnH (t,xk)
)
×
∏
r⁄=ns
exp
(
μ˜hnH ,r→ˆhSnH
(
t,˜hnH,r
))
+c. (64)
In the (t+1) -th iteration, similar to (63), the message
μ˜hnH ,ns→ˆhSnH (t+1,˜hnH,ns) passed from the variable node ˜H
to the factor node p ˆHS|HS( ˆHS|HS) is expressed as
μ˜hnH ,ns→ˆhSnH
(
t+1,˜hnH,ns
)
=l o gp˜hnH ,ns|x
(
˜hnH,ns|x
)
+
∑
k⁄=nH
μˆhSk→˜hnH ,ns
(
t,˜hnH,ns
)
+c. (65)
Let the mean and variance of the exponential form of the mes-
sage passed in (65) be ¯hnHns,nH(t+1) and σhnHns,nH(t+1) ,
respectively.
According to the factor graph in Fig. 5, the logarithmic
marginal distribution of the variable ˜H and x are calcu-
lated as follows. With the iteration of the algorithm, the
marginal distributions of variables gradually converge to their
MMSE estimates. The marginal distribution of the variable
x is
μxns (t+1,xns)
=l o gpx (xns)+
NH∑
k=1
μˆhSk→xns (t,xns)+ c. (66)
Let the mean and variance of the exponential form of the
marginal distribution in (66) be ˆxns(t+1) and σxns(t+1) ,
respectively. The marginal distribution of the variable ˜H is
μ˜hnH ,ns
(
t+1,˜hnH,ns
)
=l o gp˜hnH ,ns|x
(
˜hnH,ns|x
)
+
NH∑
k=1
μˆhSk→˜hnH ,ns
(
t,˜hnH,ns
)
+c. (67)
Let the mean and variance of the exponential form
of the marginal distribution in (67) be ˆhnH,ns(t+1) and
σhnH,ns(t+1) , respectively.
APPENDIX B
Here we derive the approximate result (14). The Roman font is
used to represent the elementshSnH ,˜hnH,ns , andxns in the matrix
HS, ˜H, and x in the case of CLT. Let ΔhnHns,nH = ˜hnH,ns −¯hnHns,nH(t) andΔxns,nH =x ns − ¯xns,nH(t), then the mean is
0, and the variance is σhnHns,nH(t) andσxns(t).
In thet iteration, the sparsity λ in the prior distribution of en-
vironmental informationpx(x) remains constant. As mentioned
in Section IV -C, we consider that variable x is independent of
variable ˜H in the t-th iteration. Therefore, the mean ˆhnH,ns and
the variance σhnH,ns of variable ˜H are independent of variable
x. HS is expressed as
hSnH =
N∑
k=1
˜hnH,nsxns
=
(
ΔˆhnHns,nH +¯hnHns,nH(t)
)
xns
+
∑
k⁄=ns
(¯hnHk,nH(t)¯xk,nH(t)+ ¯hnHk,nH(t)Δxk,nH
+Δ hnHk,nH ¯xk,nH(t)+Δ hnHk,nHΔxk,nH). (68)
Based on the CLT condition, xns = xns , the mean and vari-
ance of hSnH in (68) is written as
E
{
hSnH} = ¯hnHns,nH(t)xns +¯pns,nH(t), (69)
D
{
hSnH} = σhnHns,nH(t)x2ns +σpns,nH(t), (70)
where
¯pns,nH(t)=
∑
k⁄=ns
¯hnHk,nH(t)¯xk,nH(t), (71)
σpns,nH(t)= ∑
k⁄=ns
(¯h2nHk,nH(t)σxk,nH(t)
+σhnHk,nH(t)¯x2k,nH(t)+ σhnHk,nH(t)σxk,nH(t)).
(72)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3613
Under CLT conditions, we approximate the last two product
terms of message μˆhSnH→xns (t,xns) in (62) to the marginal
distribution of variable hSnH in (68). Therefore, according to the
conditional Gaussian approximation, we obtain (14).
APPENDIX C
Here we derive the approximate result (20). Pluging (16) and
(17) into (14) we obtain
FnH
(¯hnHns,nH(t)xns +¯pns,nH(t),
σhnHns,nH(t)x2ns +σpns,nH(t);ˆhSnH
)
+c
≈ FnH
(¯hnHns,nH(t)(xns − ˆxns(t))+ ¯pnH(t),
σhnHns,nH(t)(x2ns − ˆx2ns(t))+σpnH(t);ˆhSnH)+c, (73)
where, since Ns →∞ , we drop inﬁnitesimal terms such as¯hnHns,nH(t)(ˆxns(t)− ¯xns,nH(t)) and so on.
As with most AMP algorithms [24], [25], [28], we make
the same derivation. We perform Taylor series expansion of
variablexns in (73) at point ˆxns(t), the passed message in (14)
is approximated as
μˆhSnH→xns (t,xns) ≈ c+FnH
(
¯pnH(t),σ pnH(t);ˆhSnH
)
+¯hnHns,nH(t)(xns − ˆxns(t))
×F′nH,1
(
¯pnH(t),σ pnH(t);ˆhSnH
)
+2σhnHns,nH(t)ˆxns(t)(xns − ˆxns(t))
×F′nH,2
(
¯pnH(t),σ pnH(t);ˆhSnH
)
+ 12¯h2nHns,nH(t)(xns − ˆxns(t))2
×F′′nH,1
(
¯pnH(t),σ pnH(t);ˆhSnH
)
+σhnHns,nH(t)(xns − ˆxns(t))2
×F′nH,2
(
¯pnH(t),σ pnH(t);ˆhSnH
)
. (74)
whereF′nH,1 andF′′nH,1 represent the ﬁrst and second derivatives
of the ﬁrst argument of FnH , and F′nH,2 represents the ﬁrst
derivative of the second argument ofFnH . We drop inﬁnitesimal
terms such as the second derivative term of the second argument
of FnH .
According to the derivation in Appendix D that
F′nH,2 = 12[(F′nH,1)2 +F′′nH,1]. (75)
We plug (18), (19) and (75) into (74), and absorb the con-
stant term into the constant c, we obtain (20), where under the
CLT condition, we use ˆh2nH,ns(t) instead of ¯h2nHns,nH(t), and
σhns,nH(t) instead of σhnHns,nH(t).
APPENDIX D
Here we derive the equation (75). According to (15), we know
the following
∂exp(FnH)
∂σp = F′nH,2 exp(FnH), (76)
∂2 exp(FnH)
∂p2 =
[(
F′nH,1)2 +F′′nH,1]exp(FnH). (77)
According to (15), we obtain
∂exp(FnH)
∂σp
=
∫
hS
pˆhS|hS
(
ˆhS|hS
) 1√
2π
[
−12(σp)−3/2
−(σp)−5/2
(
hS −p)2
2
]
exp
((
hS −p)2
2σp
)
= 12∂2 exp(FnH)∂p2 . (78)
Plugging (76) and (77) into (78), we obtain (75).
REFERENCES
[1] F. Liu et al. , “Integrated sensing and communications: Towards dual-
functional wireless networks for 6G and beyond,” 2021. [Online]. Avail-
able: https://arxiv.org/abs/2108.07165
[2] W. Saad, M. Bennis, and M. Chen, “A vision of 6G wireless systems:
Applications, trends, technologies, and open research problems,” IEEE
Netw., vol. 34, no. 3, pp. 134–142, May/Jun. 2020.
[3] T. S. Rappaport et al., “Wireless communications and applications above
100 GHz: Opportunities and challenges for 6G and beyond,”IEEE Access,
vol. 7, pp. 78729–78757, 2019.
[4] L. Kong, M. K. Khan, F. Wu, G. Chen, and P . Zeng, “Millimeter-wave
wireless communications for IoT-cloud supported autonomous vehicles:
Overview, design, and challenges,” IEEE Commun. Mag. , vol. 55, no. 1,
pp. 62–68, Jan. 2017.
[5] G. Han, J. Jiang, C. Zhang, T. Q. Duong, M. Guizani, and G. K. Karagian-
nidis, “A survey on mobile anchor node assisted localization in wireless
sensor networks,”IEEE Commun. Surv. Tut., vol. 18, no. 3, pp. 2220–2243,
Jul.–Sep. 2016.
[6] H. Menouar, I. Guvenc, K. Akkaya, A. S. Uluagac, A. Kadri, and A.
Tuncer, “UA V -enabled intelligent transportation systems for the smart
city: Applications and challenges,” IEEE Commun. Mag. , vol. 55, no. 3,
pp. 22–28, Mar. 2017.
[7] F. Liu, C. Masouros, A. P . Petropulu, H. Grifﬁths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun. , vol. 68, no. 6, pp. 3834–3862,
Jun. 2020.
[8] C. Jiao, Z. Zhang, C. Zhong, and Z. Feng, “An indoor mmWave joint radar
and communication system with active channel perception,” inProc. IEEE
Int. Conf. Commun., 2018, pp. 1–6.
[9] C. Jiao, Z. Zhang, C. Zhong, X. Chen, and Z. Feng, “Millimeter wave
communication with active ambient perception,” IEEE Trans. Wireless
Commun., vol. 18, no. 5, pp. 2751–2764, May 2019.
[10] X. Tong, Z. Zhang, J. Wang, C. Huang, and M. Debbah, “Joint multi-user
communication and sensing exploiting both signal and environment spar-
sity,” IEEE J. Sel. Topics Signal Process. , vol. 15, no. 6, pp. 1409–1422,
Nov. 2021.
[11] D. K. P . Tan et al. , “Integrated sensing and communication in 6G:
Motivations, use cases, requirements, challenges and future directions,”
in Proc. 1st IEEE Int. Online Symp. Joint Commun. Sens. , 2021,
pp. 1–6.
[12] J. A. Zhang et al. , “Enabling joint communication and radar sensing in
mobile networks — A survey,” IEEE Commun. Surv. Tut., vol. 24, no. 1,
pp. 306–345, Jan.–Mar. 2022, [Online]. Available: https://arxiv.org/abs/
2006.07559v3
[13] T. Wild, V . Braun, and H. Viswanathan, “Joint design of communica-
tion and sensing for beyond 5G and 6G systems,” IEEE Access ,v o l .9 ,
pp. 30845–30857, 2021.
[14] C. B. Barneto, S. D. Liyanaarachchi, T. Riihonen, L. Anttila, and M.
V alkama, “Multibeam design for joint communication and sensing in 5G
new radio networks,” in Proc. IEEE Int. Conf. Commun. , 2020, pp. 1–6.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

3614 IEEE TRANSACTIONS ON SIGNAL PROCESSING, VOL. 70, 2022
[15] C. B. Barneto et al. , “Full-duplex OFDM radar with LTE and 5G NR
waveforms: Challenges, solutions, and measurements,” IEEE Trans. Mi-
crow. Theory Techn., vol. 67, no. 10, pp. 4042–4054, Oct. 2019.
[16] B. Tan, Q. Chen, K. Chetty, K. Woodbridge, W. Li, and R. Piechocki,
“Exploiting WiFi channel state information for residential health-
care informatics,” IEEE Commun. Mag. , vol. 56, no. 5, pp. 130–137,
May 2018.
[17] Q. Zhang, H. Sun, Z. Wei, and Z. Feng, “Sensing and communication
integrated system for autonomous driving vehicles,” in Proc. IEEE Conf.
Comput. Commun. Workshops, 2020, pp. 1278–1279.
[18] P . Almers et al., “Survey of channel and radio propagation models for wire-
less MIMO systems,” EURASIP J. Wireless Commun. Netw. , vol. 2007,
Feb. 2007, Art. no. 019070.
[19] L. Chen, F. Liu, W. Wang, and C. Masouros, “Joint radar-communication
transmission: A generalized pareto optimization framework,”IEEE Trans.
Signal Process., vol. 69, pp. 2752–2765, 2021.
[20] G. K. Papageorgiou, M. Sellathurai, and Y . C. Eldar, “Deep networks for
direction-of-arrival estimation in low SNR,” IEEE Trans. Signal Process.,
vol. 69, pp. 3714–3729, 2021.
[21] D. L. Donoho, “Compressed sensing,” IEEE Trans. Inf. Theory , vol. 52,
no. 4, pp. 1289–1306, Apr. 2006.
[22] E. J. Candes and T. Tao, “Near-optimal signal recovery from random
projections: Universal encoding strategies?,” IEEE Trans. Inf. Theory ,
vol. 52, no. 12, pp. 5406–5425, Dec. 2006.
[23] T. T. Cai and L. Wang, “Orthogonal matching pursuit for sparse signal re-
covery with noise,”IEEE Trans. Inf. Theory, vol. 57, no. 7, pp. 4680–4688,
Jul. 2011.
[24] D. L. Donoho, A. Maleki, and A. Montanari, “Message passing algorithms
for compressed sensing: I motivation and construction,” inProc. IEEE Inf.
Theory Workshop Inf. Theory, 2010, pp. 1–5.
[25] S. Rangan, “Generalized approximate message passing for estimation with
random linear mixing,” in Proc. IEEE Int. Symp. Inf. Theory Proc. , 2011,
pp. 2168–2172.
[26] J. Y ao, Z. Zhang, X. Shao, C. Huang, C. Zhong, and X. Chen, “Concen-
trative intelligent reﬂecting surface aided computational imaging via fast
block sparse Bayesian learning,” in Proc. IEEE 93rd V eh. Technol. Conf.,
2021, pp. 1–6.
[27] Y . Tao and Z. Zhang, “Distributed computational imaging with reconﬁg-
urable intelligent surface,” in Proc. Int. Conf. Wireless Commun. Signal
Process., 2020, pp. 448–454.
[28] J. T. Parker, P . Schniter, and V . Cevher, “Bilinear generalized approxi-
mate message passing—Part I: Derivation,” IEEE Trans. Signal Process.,
vol. 62, no. 22, pp. 5839–5853, Nov. 2014.
[29] B. J. Frey and D. J. C. MacKay, “A revolution: Belief propagation in graphs
with cycles,” in Proc. Adv. Neural Inf. Process. Syst., 1998, pp. 479–485.
[30] F. R. Kschischang, B. J. Frey, and H. A. Loeliger, “Factor graphs and
the sum-product algorithm,” IEEE Trans. Inf. Theory , vol. 47, no. 2,
pp. 498–519, Feb. 2001.
[31] A. Lavrenko, F. Römer, G. Del Galdo, and R. S. Thomä, “Sensing matrix
sensitivity to random Gaussian perturbations in compressed sensing,” in
Proc. 26th Eur . Signal Process. Conf., 2018, pp. 583–587.
[32] Z. Y ang, C. Zhang, and L. Xie, “Stable signal recovery in compressed
sensing with a structured matrix perturbation,” in Proc. IEEE Int. Conf.
Acoust., Speech, Signal Process., 2012, pp. 2737–2740.
Xin Tong (Student Member, IEEE) received the B.S.
degree in communication engineering from Ningbo
University, Ningbo, China, in 2020. He is currently
working toward the Ph.D. degree in information and
communication engineering with Zhejiang Univer-
sity, Hangzhou, China, under the supervision of Prof.
Zhaoyang Zhang. His research interests include joint
communication and sensing, signal processing, and
massive MIMO.
Zhaoyang Zhang (Senior Member, IEEE) re-
ceived the Ph.D. degree from Zhejiang University,
Hangzhou, China, in 1998. He is currently a Qiushi
Distinguished Professor with Zhejiang University. He
has coauthored more than 300 peer-reviewed inter-
national journal and conference papers. His research
interests include the fundamental aspects of wireless
communications and networking, such as information
theory and coding theory, network signal processing
and distributed learning, AI-empowered communi-
cations and networking, and synergetic sensing, and
computing and communication. He was the recipient of eight conference best
papers awarded by IEEE ICC 2019 and IEEE GlobeCom 2020. He was awarded
the National Natural Science Fund for Distinguished Y oung Scholars by NSFC
in 2017.
Dr. Zhang is/was the Editor of IEEE T RANSACTIONS ON WIRELESS COMMU-
NICA TIONS, IEEE T RANSACTIONS ON COMMUNICA TIONSand IET Communica-
tions, and the General Chair, TPC Co-Chair or Symposium Co-Chair for PIMRC
2021 Workshop on Native AI Empowered Wireless Networks, VTC-Spring
2017 Workshop on HMWC, WCSP 2013 / 2018, and Globecom 2014 Wireless
Communications Symposium. He was also a keynote speaker for APCC 2018
and VTC-Fall 2017 Workshop NOMA.
Yihan Zhang (Student Member, IEEE) received the
B.S. degree in information engineering from Zhejiang
University, Hangzhou, China, in 2020, where he is
currently working toward the M.S. degree in infor-
mation and communication engineering, under the
supervision of Prof. Zhaoyang Zhang. His research
interests include signal processing, integrated sensing
and communication, and computational imaging.
Zhaohui Yang (Member, IEEE) received the B.S.
degree in information science and engineering from
Chien-Shiung Wu Honors College, Southeast Uni-
versity, Nanjing, China, in June 2014, and the Ph.D.
degree in communication and information system
with the National Mobile Communications Research
Laboratory, Southeast University, Nanjing, China, in
May 2018. From 2018 to 2020, he was a Postdoctoral
Research Associate with the Center for Telecom-
munications Research, Department of Informatics,
King’s College London, UK. From 2020 to 2022,
he was a Research Fellow with the Department of Electronic and Electrical
Engineering, University College London, UK. He is currently a ZJU young Pro-
fessor with College of Information Science and Electronic Engineering Zhejiang
Key Lab of Information Processing Communication and Networking, Zhejiang
University, and also a Research Scientist with Zhejiang Lab. He is an Associate
Editor for the IEEE C OMMUNICA TIONS LETTERS, IET Communications and
EURASIP Journal on Wireless Communications and Networking . He has guest
edited a feature topic/special issue of IEEE C OMMUNICA TIONS MAGAZINE,
IEEE WIRELESS COMMUNICA TIONS, and IEEE J OURNAL ON SELECTED AREAS
IN COMMUNICA TIONS. He was a Co-Chair for international workshops with
more than 10 times including ICC, GLOBECOM, WCNC, PIMRC, INFOCOM.
His research interests include joint communication, sensing, and computation,
federated learning, reconﬁgurable intelligent surface, UA V , and NOMA. He
was a TPC member of IEEE ICC during 2015–2022 and GLOBECOM during
2017-2022. He was an exemplary Reviewer for IEEE T RANSACTIONS ON COM-
MUNICA TIONSin 2019 and 2020.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply. 

TONG et al.: ENVIRONMENT SENSING CONSIDERING THE OCCLUSION EFFECT: A MULTI-VIEW APPROACH 3615
Chongwen Huang (Member, IEEE) received the
B.Sc. degree from Nankai University, Tianjin, China,
in 2010, the M.Sc degree from the University of Elec-
tronic Science and Technology of China, Chengdu,
China, in 2013, and the Ph.D. degree from the Singa-
pore University of Technology and Design (SUTD),
Singapore, in 2019. From October 2019 to September
2020, he was a Postdoc in SUTD. Since Septem-
ber 2020, he has been with Zhejiang University,
Hangzhou, China, as a tenure-track young Profes-
sor. His main research interests include holographic
MIMO surface/reconﬁgurable intelligent surface, B5G/6G wireless commu-
nication, mmWave/THz communications, and deep learning technologies for
wireless communications. Dr. Huang was the recipient of the IEEE Marconi
Prize Paper Award in Wireless Communications, and IEEE ComSoc Asia-Paciﬁc
Outstanding Y oung Researcher Award in 2021. He was the Editor of IEEE
COMMUNICA TIONSLETTER, Elsevier Signal Processing , EURASIP Journal on
Wireless Communications and Networking,a n dPhysical Communication since
2021.
Kai-Kit Wong (Fellow, IEEE) received the B.Eng.,
M.Phil., and Ph.D. degrees in electrical and electronic
engineering from the Hong Kong University of Sci-
ence and Technology, Hong Kong, in 1996, 1998,
and 2001, respectively. After graduation, he took up
academic and research positions with The Univer-
sity of Hong Kong, Hong Kong, Lucent Technolo-
gies, Bell-Labs, Holmdel, Smart Antennas Research
Group of Stanford University, Stanford, CA, USA,
and University of Hull, Hull, U.K. He is the Chair
in wireless communications with the Department of
Electronic and Electrical Engineering, University College London, London,
U.K. His research centers around 5G and beyond mobile communications. He
was the recipient of the 2013 IEEE Signal Processing Letters Best Paper Award
and the 2000 IEEE VTS Japan Chapter Award at the IEEE V ehicular Technology
Conference in Japan in 2000, and a few other international best paper awards.
He is a Fellow of IET and is also on the editorial board of several international
journals. He is also the Editor-in-Chief for IEEE W IRELESS COMMUNICA TIONS
LETTERS since 2020.
Mérouane Debbah (Fellow, IEEE) received the
M.Sc. and Ph.D. degrees from the Ecole Normale
Supérieure Paris-Saclay, Cachan, France. He was
with Motorola Labs, Saclay, France, from 1999 to
2002, and also with the Vienna Research Center
for Telecommunications, Vienna, Austria, until 2003.
From 2003 to 2007, he was an Assistant Professor
with the Mobile Communications Department, Insti-
tut Eurecom, Sophia Antipolis, France. In 2007, he
was appointed as a Full Professor with CentraleSup-
elec, Gif-sur-Yvette, France. From 2007 to 2014, he
was the Director of the Alcatel-Lucent Chair on Flexible Radio. From 2014 to
2021, he was the Vice-President of the Huawei France Research Center. He was
jointly the Director of the Mathematical and Algorithmic Sciences Lab and the
Director of the Lagrange Mathematical and Computing Research Center. Since
2021, he has been a Chief Research Ofﬁcer with Technology Innovation Institute
in Abu Dhabi. He leads jointly the AI and Telecommunication centers. He has
managed eight EU Projects and more than 24 national and international projects.
His research interests include fundamental mathematics, algorithms, statistics,
information, and communication sciences research. He is a WWRF Fellow, a
Eurasip Fellow, an Institut Louis Bachelier Fellow, and a Membre émérite SEE.
He was the recipient of the ERC Grant MORE (Advanced Mathematical Tools
for Complex Network Engineering) from 2012 to 2017, Mario Boella Award in
2005, IEEE Glavieux Prize Award in 2011, Qualcomm Innovation Prize Award
in 2012, 2019 IEEE Radio Communications Committee Technical Recognition
Award, 2020 SEE Blondel Medal. He was also the recipient of more than 20 best
paper awards, among which the 2007 IEEE GLOBECOM Best Paper Award,
Wi-Opt 2009 Best Paper Award, 2010 Newcom++ Best Paper Award, WUN
CogCom Best Paper 2012 and 2013 Award, 2014 WCNC Best Paper Award,
2015 ICC Best Paper Award, 2015 IEEE Communications Society Leonard G.
Abraham Prize, 2015 IEEE Communications Society Fred W. Ellersick Prize,
2016 IEEE Communications Society Best Tutorial Paper Award, 2016 European
Wireless Best Paper Award, 2017 Eurasip Best Paper Award, 2018 IEEE Marconi
Prize Paper Award, 2019 IEEE Communications Society Y oung Author Best
Paper Award, 2021 Eurasip Best Paper Award, 2021 IEEE Marconi Prize Paper
Award, and V aluetools 2007, V aluetools 2008, CrownCom 2009, V aluetools
2012, SAM 2014, and 2017 IEEE Sweden VT-COM-IT Joint Chapter best
student paper awards. He is an Associate Editor-in-Chief for thejournal Random
Matrix: Theory and Applications . He was an Associate Area Editor and the
Senior Area Editor of the IEEE T RANSACTIONS ON SIGNAL PROCESSING from
2011 to 2013 and from 2013 to 2014, respectively. From 2021 to 2022, he was
an IEEE Signal Processing Society Distinguished Industry Speaker.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 04:27:34 UTC from IEEE Xplore.  Restrictions apply.