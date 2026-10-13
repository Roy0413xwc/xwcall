---
title: "Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems"
zotero_key: "9C2VZXD7"
pdf_key: "ZNFJ6BKL"
doi: "10.1109/TVT.2019.2930153"
collection: "其他"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Optimizing Resource Allocation in URLLC for Real-Time Wireless Control Systems — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

8916 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY , VOL. 68, NO. 9, SEPTEMBER 2019
Optimizing Resource Allocation in URLLC for
Real-Time Wireless Control Systems
Bo Chang , Lei Zhang , Liying Li , Guodong Zhao, and Zhi Chen
Abstract—As one of the three main scenarios in the ﬁfth-
generation (5G) cellular networks, ultra-reliable and low-latency
communication (URLLC) can be served as an enabler for real-time
wireless control systems. In such a system, the communication
resource consumption in URLLC and the control subsystem per-
formance are mutually dependent. To optimize the overall system
performance, it is critical to integrate URLLC and control subsys-
tems together by formulating a co-design problem. In this paper,
based on uplink transmission, we study the resource allocation
problem for URLLC in real-time wireless control systems. The
problem is conducted by optimizing bandwidth and transmission
power allocation in URLLC and control convergence rate subject
to the constraints on communication and control. To formulate
and solve the problem, we ﬁrst convert the control convergence
rate requirement into a communication reliability constraint. Then,
the co-design problem can be replaced by a regular wireless re-
source allocation problem. By proving the converted problem is
concave, an iteration algorithm is proposed to ﬁnd the optimal
communication resource allocation. Based on that, the optimal
control convergence rate can be obtained to optimize overall system
performance. Simulation results show remarkable performance
gain in terms of spectral efﬁciency and control cost. Compared
with the scheme of satisfying ﬁxed quality-of-service in traditional
URLLC design, our method can adjust optimal spectrum allocation
to maximize the communication spectral efﬁciency and maintain
the actual control requirement.
Index Terms —URLLC, real-time wireless control, co-design,
optimal resource allocation.
I. I NTRODUCTION
A
S ONE of the most important communication scenarios in
the coming ﬁfth generation (5G) cellular networks, ultra-
reliable and low-latency communication (URLLC) is deﬁned as
a communication scenario to provide high reliability and low la-
tency end-to-end (E2E) services. URLLC has shown its potential
to provide service to real-time wireless control systems, which
can obtain signiﬁcant advantage compared with traditional wired
Manuscript received February 21, 2019; revised June 8, 2019; accepted July
16, 2019. Date of publication July 22, 2019; date of current version September
17, 2019. This work was supported in part by the National Natural Science
Foundation of China under Grants 61631004 and 61601094, and in part by
the National Key R&D Program of China under Grant 2018YFC0807101. The
review of this paper was coordinated by Dr. M. Marchese. (Corresponding
author: Liying Li.)
B. Chang and Z. Chen are with the National Key Laboratory of
Science and Technology on Communications, University of Electronic Sci-
ence and Technology of China (UESTC), Chengdu 611731, China (e-mail:
changb3212@163.com; chenzhi@uestc.edu.cn).
L. Zhang, L. Li, and G. Zhao are with the School of Engineering, University
of Glasgow, Glasgow G12 8QQ, U.K. (e-mail: Lei.Zhang@glasgow.ac.uk;
liyingli0815@gmail.com; guodong.zhao@glasgow.ac.uk).
Digital Object Identiﬁer 10.1109/TVT.2019.2930153
control systems. For instance, the system deployment can be
modiﬁed or upgraded ﬂexibly while maintaining the commuta-
tion quality unaltered. In vehicle technologies, URLLC is one
of the key enablers to in-vehicle wireless control, which can
signiﬁcantly reduce ﬁnancial cost in manufacturing. This further
improves fuel efﬁciency and reduces gas emission to provide
timely, reliable and accurate control and an open architecture
for new applications [1], [2]. Furthermore, URLLC is crucial for
vehicle-to-anything (V2X) communication, which is essential
for the vehicle automatic driving via wireless communications
[3], [4].
There are some research on wireless control systems, but most
of them analyze URLLC (e.g., [5]–[14]) and wireless networked
control (e.g., [15]–[20]) separately. From wireless communica-
tion perspective, the authors in [21] investigated the achievable
channel coding rate for ﬁnite blocklength, which establish one
of the most important foundations of URLLC design in physical
layer. The authors in [22] further discussed the close form ex-
pression of the achievable capacity in URLLC, which provides a
guideline for the URLLC design in different channel cases, e.g.,
additive white gaussian noise (AWGN) channel and Rayleigh
fading channel. Based on the above research, more works focus
on URLLC resource allocation design to maintain the extreme
high quality-of-service (QoS) in URLLC [5]–[12]. For example,
the authors in [5] studied the resource allocation for the uplink
communications and found that a huge amount of frequency and
transmission power are needed to satisfy the extreme high QoS
in URLLC. However, all of the research are targeting a latency or
reliability constrained communication system without bringing
speciﬁc control performance (e.g., control cost, stability, or state
update rate) into consideration.
From wireless control perspective, the communication la-
tency and reliability are set as random variables caused by
communication protocols [15]–[20]. For example, the authors
in [15] studied the effect of communication packet loss on the
control performance caused by transmission control protocol
(TCP) or user datagram protocol (UDP). The authors in [16]
further discussed the effect of both time delay and packet loss
on the control performance caused by carrier sense multiple
access/collision avoidance (CSMA/CA). In [20], the authors
provided a survey on the wireless network design for the control
systems, where the latency and the reliability were discussed
in different communication protocols. The above research indi-
cates that the communication time delay and packet loss results
in control performance loss since they enlarge the sample period
of the control systems [20]. However, no close form expression
0018-9545 © 2019 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.
See http://www.ieee.org/publications_standards/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

CHANG et al.: OPTIMIZING RESOURCE ALLOCA TION IN URLLC FOR REAL-TIME WIRELESS CONTROL SYSTEMS 8917
is obtained to show exactly how the communication latency and
reliability affect the control performance.
The aforementioned work that separately design communi-
cation and control subsystems cannot guarantee optimal overall
system performance. On the one hand, most of the research
on URLLC intend to maintain the extreme high QoS only in
wireless communications. On the other hand, the effect of the
communication latency and reliability on control performance
cannot be obtained exactly. In fact, the co-design of the URLLC
and real-time wireless control is critical for both communication
and control. First, communication resource is extremely limited,
especially to meet the ultra high technical requirements for
URLLC. A tailored design for a wireless control system can
signiﬁcantly reduce the communication resource consumption.
For instance, at some stages when the control performance is
not constrained in an extreme high level, the allocated wireless
resource can be reduced accordingly. Second, the control per-
formance is determined by both the control sample period and
the communication QoS, where the sample period should be
adjusted accordingly to optimize the control performance when
the communication QoS is different [20].
We notice that there are some research on communication-
control co-design [23]–[27]. For instance, in [24], the authors
obtained the optimal control sampling period and communica-
tion time delay and reliability by simulation analysis based on the
existing communication protocols. In [25], we further obtained
that different communication QoSs have different effects on
control performance throughout the control process by simula-
tion analysis, where the control process can be divided into two
stages with different QoS service and the power consumption
can be signiﬁcantly reduced. Furthermore, in [26] and [27], the
authors analyzed the control stability with unreliability commu-
nications in V2X communications. However, without close form
expression indicating the relationship between communication
and control by co-design, a high overall system performance
cannot be obtained.
This paper aims to optimize the communication resource
allocation by joint communication-control design. Taking the
uplink transmission as an example, our goal is to ﬁnd the
optimal communication bandwidth, communication power con-
sumption, and control convergence rate 1 by maximizing the
spectral efﬁciency (SE) while guaranteeing the control require-
ment. However, the idea can be extended into the downlink
transmission scenario straightforwardly. Our problem formula-
tion considers both URLLC QoS and control convergence rate
constraints, while such a co-design is still an open problem to
be explored. To achieve the goal, a key is to ﬁnd a method
to convert the constraints on the control sub-system into the
constraints that the communication sub-system can adopt to
solve the optimization problem. The main contributions of this
paper are summarized as follows.
1The main control variables are state sampling period and the control input
gain, which jointly affect the control convergence rate. Then, the control conver-
gence rate further affects the control performance, e.g., control cost or control
stability. By constraint on control convergence rate, the state sampling period
and the control input gain are constrained. Thus, the control convergence rate is
considered as the control design in this paper.
Fig. 1. Real-time wireless control system model.
r We propose an optimal resource allocation scheme to
maximize the SE by communication and control co-design,
where both URLLC requirements and control convergence
rate requirement are taken into account. The proposed
scheme allows us to use optimal resource to support
URLLC while guaranteeing the required control perfor-
mance level.
r We analyze the relationship between the control conver-
gence rate requirement and communication requirement
on URLLC quality. We ﬁnd that the lower bound of the
communication reliability decreases linearly with the con-
trol convergence rate. Then, the requirement on control can
be treated as a constraint on the communication reliability,
which allows us to convert the co-design problem into a
regular communication optimization problem.
r We prove that the formulated optimization problem is con-
cave based on the conversion. Subsequently, we develop an
iteration method to ﬁnd the optimal bandwidth and power
allocation.
The rest of this paper is organized as follows. In Section II, the
system model is presented. In Section III, the communication-
control co-design method is proposed, where the optimal re-
source allocation problem is formulated with control perfor-
mance constraint. In Section IV, the relationship between the
communication and control subsystems is ﬁrst discussed, then
an iteration method is proposed to obtain the optimal resource
allocation in terms of maximizing the communication SE. In
Section V, simulation results are provided to show the perfor-
mance. Finally, Section VI concludes the paper.
II. S YSTEM MODEL WITH LA TENCY AND
RELIABILITY CONSTRAINTS
In this section, we propose the system model by taking com-
munication latency and reliability into consideration. As shown
in Fig. 1, we consider a typical centralized real-time wireless
communication-control system, where there areM static sensors
transmitting sampling signals of the plant state to the base station
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

8918 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 68, NO. 9, SEPTEMBER 2019
TABLE I
SUMMARY OF NOTA TIONS FORCOMMUNICA TIONSUBSYSTEM
TABLE II
SUMMARY OF NOTA TIONS FORCONTROL SUBSYSTEM
(BS), the remote controller in the BS processing the sampling
signals, and then the BS sending the calculated control command
signals to the M corresponding static plants. With the control
process continuing, the state of each plant will converge to a
preset value. Note that all the notations to be used throughout
the paper for communication subsystem and control subsystem
are summarized in Table I and II, respectively.
A. Wireless Control Model
In this subsection, we present the real-time wireless control
model considering communication time delay and reliability.
Except the inherent control parameters, e.g., the mass and the
speed of the plant, the main coefﬁcients that contribute to control
performance include sampling period at the sensor and commu-
nication QoS [20]. Since we focus on the control convergence
rate requirement and communication QoS, constant sampling
period is adopted. Then, the continuous control function for the
m-th plant is given by a linear differential equation as [24]
dxm(t)= Amxm(t)dt+Bmum(t)dt+dnm(t), (1)
where xm(t) is the state of the m-th plant, um(t) is the control
input, and nm(t) is the disturbance caused by additive white
gaussian noise (AWGN) with zero mean and variance Rm.I n
addition,Am andBm represent the system parameter matrices.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

CHANG et al.: OPTIMIZING RESOURCE ALLOCA TION IN URLLC FOR REAL-TIME WIRELESS CONTROL SYSTEMS 8919
Fig. 2. Wireless control system model for a single plant.
To illustrate the system parameters Am andBm, we consider a
controlled inverted pendulum system as shown in Fig. 2.
Example 1: The m-th controlled inverted pendulum system
consists of an inverted pendulum and a motorized cart. We have
the plant state x(t)=( ct, ˙ct,θt, ˙θt), where ct represents the
cart’s position, ˙ct represents the cart’s velocity,θt represents the
pendulum’s angle, and ˙θt represents the pendulum’s angular ve-
locity. The expression ofAm andBm consists of the pendulum
length 2l, the inertia of the pendulum Ψ, the friction of the cart
r, the gravitational acceleration φ, the mass of the pendulum λ,
and the mass of the cartΓ. By physical-mathematics calculation,
Am andBm can be expressed as follows, respectively,
Am =
⎛
⎜⎜⎜⎜⎜⎜⎜⎜⎜⎝
01 00
0 −(Ψ+ λl2)rΨ(Γ+ λ)+Γ λl2 λ2gl2Ψ(Γ+ λ)+Γ λl2 0
00 01
0 −λlrΨ(Γ+ λ)+Γ λl2 λφl(Γ+ λ)Ψ(Γ+ λ)+Γ λl2 0
⎞
⎟⎟⎟⎟⎟⎟⎟⎟⎟⎠
(2)
and
Bm =
⎛
⎜⎜⎜⎜⎜⎜⎜⎜⎝
0
(Ψ+ λl2)r
Ψ(Γ+ λ)+Γ λl2
0
λl
Ψ(Γ+ λ)+Γ λl2
⎞
⎟⎟⎟⎟⎟⎟⎟⎟⎠. (3)
■
To obtain the discrete time control model, we assume thatsm,n
represents the sample period of the m-th plant at time index n,
which consists of wireless transmission time delay Tm,n and an
idle period ¯sm,n. Their relationship can be expressed as
sm,n =¯sm,n +Tm,n, (4)
where n = 1, 2,...,N represents the sampling time index in
the control process andN is the maximum sampling time index.
Then, the discrete time control model with time delay Tm,n can
be obtained as
xm,n+1 = Ωm,nxm,n +Φm,n0 um,n +Φm,n1 um,n−1 +nm,n,
(5)
whereΩm,n = eAsm,n ,Φm,n0 =( ∫ ¯sm,n0 eAm,ntdt)·Bm,n, and
Φm,n1 =( ∫sm,n¯sm,n eAm,ntdt)·Bm,n. More details about the con-
trol model can be referenced in [20].
Assuming ξm,n =( xTm,n um,n−1)T is the generalized state,
then the control function in (5) can be rewritten as
ξm,n+1 = Ωm,dξm,n +Φm,dum,n + ¯nm,n, (6)
where ¯nm,n =( nTm,n 0)T and Φm,d =( Φm,n0I ). We assume
Ωm,n = Ωm. Then, we have Ωm,d =( Ωm0 Φm,n10 ).
Considering the packet loss, we have Pr{αm,n = 1} = 1−
εm,n ≥ 1−εth and Pr{αm,n = 0} = εm,n <ε th, where ”1”
means that the packet is successfully transmitted and the control
is under closed loop, and ”0” means that the packet is lost and the
control is under open loop. In addition, we assume that the state
estimator is perfect, and then a linear feedbackum,n =Θ mξm,n
is used. Then, we have the closed-loop system in (6) can be
rewritten as
ξm,n+1 =
{
(Ωm,d +Φm,dΘm)ξm,n + ¯nm,n, ifαm,n = 1
Ωm,dξm,n + ¯nm,n, ifαm,n = 0,
(7)
which can be rewritten in a general way as
ξm,n+1 =
{
Ωe1ξm,n + ¯nm,n, ifαm,n = 1
Ωe0ξm,n + ¯nm,n, ifαm,n = 0, (8)
where Ωe1 = Ωm,d +Φm,dΘm is the parameter of the control
system with transmission time delay included inΩm,d when the
data packet is successfully transmitted, and Ωe0 = Ωm,d is the
parameter of the control system with transmission time delay
included in Ωm,d when the data packet is failed. Furthermore,
when there is no transmission time delay, i.e., dm,n = 0, the
expression (5) can be written as
xm,n+1 = Ωm,nxm,n +Φm,n0 um,n +nm,n. (9)
Then, the expression (8) can be written as
xm,n+1 =
{
Ωe1xm,n + ¯nm,n, ifαm,n = 1
Ωe0xm,n + ¯nm,n, ifαm,n = 0, (10)
where Ωe1 = Ωm,n +Φm,n0 Θm is the parameter of the control
system without transmission time delay when the data packet
is successfully transmitted, and Ωe0 = Ωm,n is the parameter
of the control system without transmission time delay when the
data packet is failed. The above discussion indicates that the
proposed presented model in this section can be used regardless
of transmission time delay.
B. Wireless Communication Model
In the rest of this paper, we focus on the uplink from the
sensor to the BS, but the derivations can be extended into the
downlink transmission straightforwardly. For the convenience
of discussion, we assume that the uplink is imperfect that
experiences transmission time delay and packet loss, and the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

8920 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 68, NO. 9, SEPTEMBER 2019
downlink is perfect. The scenario with both uplink and downlink
experiencing imperfect channel will be considered as a future
work. Speciﬁcally, M plants are randomly distributed in the
coverage of the BS with radiusR. In addition, each plant is sam-
pled by a corresponding sensor. To avoid interference, we con-
sider orthogonal frequency division multiple access (OFDMA),
where each sensor is allocated multiple subcarriers within a
given continuous bandwidth, each subcarrier can be allocated
to at most one sensor, and the given bandwidths for different
sensors are not overlapped. Furthermore, we consider ﬂat fading
channel, where the channel gains over different subcarriers for
one sensor are approximately identical and perfectly known for
the sensor. We assume that the number of allocated bandwidth
and transmission duration for the m-th sensor at time index n
are Nm,n and Tm,n, respectively. Then, for the m-th sensor at
time indexn, the received signal-to-noise-ratio (SNR) at the BS
can be expressed as
γm,n = |hm,n|2gmNm,nB0pm,nN0Nm,nB0 = |hm,n|2gm,npm,nN0 , (11)
wherehm,n is the small scale fading for the m-th sensor at time
index n, gm is the path-loss, Nm,n is the number of allocated
bandwidth,pm is the allocated transmission power spectral den-
sity for them-th sensor,B0 is the separation among subcarriers,
andN0 is the single-sided noise spectral density. Then, the allo-
cated bandwidth for them-th sensor isBm,n = B0Nm,n. Based
on the received SNR, the Shannon capacity can be expressed as
Cm,n =l o g(1+γm,n). (12)
In URLLC, with the constraints on utra-reliability and low-
latency, the blocklength is short and small packet size is adopted
[7]. In addition, the size of payload data transmitted by sensor in
control system is usually small (e.g., about 100 bits [20]), which
is suitable to be used in URLLC scenario. In such a scenario,
the impact of decoding error cannot be ignored. We assume that
channel dispersionVm,n is adopted to represent the capacity loss
caused by the transmission error, which can be expressed as [22]
Vm,n =( l o ge)2
(
1− 1(1+γ2m,n)). (13)
When SNR is higher than 5 dB, we haveVm,n ≈ (loge)2, which
is very accurate [7]. When Vm,n < (loge)2, we can obtain a
lower bound of the achievable rate with channel dispersion
by substituting Vm,n =( l o ge)2. Thus, in the following of this
paper, we adopt
Vm,n =( l o ge)2. (14)
For the m-th plant, the available uplink rate with ﬁnite block
length is the uplink capacity eliminating the error bits that are
introduced by channel dispersion, which can be expressed as
Rm,n = Cm,n
−
√
Vm,n
Nm,nTm,nB0
f−1Q (εm,n)+ log(Nm,nTm,nB0)2Nm,nTm,nB0 , (15)
where log(Nm,nTm,nB0 )2Nm,nTm,nB0 is the approximation of the remainder
terms of order log(Nm,nTm,nB0)/(Nm,nTm,nB0), and f−1Q (·)
is the inverse of the Q-function. Then, the packet error probabil-
ity can be expressed as (16), shown at the bottom of this page,
where fQ(·) is the Q-function.
For the above channel model, it consists of path-loss and
small scale fading. According to [28], the path-loss gm can be
expressed as
gm[dB] = −128.1− 37.6lg(lm), (17)
wherelm is the distance between them-th plant and the BS with
unit km and is larger than 0.035 km [28]. The small-scale fading
hm,n follows Rayleigh distribution with mean zero and vari-
ance σ20 = 1. In addition, small-scale fading is constant within
coherence time, which is larger than the maximum end-to-end
(E2E) time delay. Thus, we considerquasi-static fading channel,
which is constant for each uplink subcarrier within a frame [29].
From (12), (14) (16), and (15), we can obtain the SE of the
uplink for them-th plant at time indexn, which can be expressed
as
ηm,n = λmNm,nB0(1−εm,n), (18)
where λm is the desired payload transmitted by the sensor, and
the SE means successful decoding bits at the BS per bit. In this
paper, we intend to obtain the uplink optimal wireless resource
allocation by maximizing SE in (18).
III. C OMMUNICA TION-CONTROL CO-DESIGN
Our goal is to maximize the communication SE and maintain
good overall system performance. Thus, in the following of this
section, we ﬁrst discuss the constraints from the perspectives of
communication and control, respectively. Then, we formulate
the co-design problem based on the constraints.
A. Communication Constraint
The main constraints from communication are the limited
wireless resource and URLLC QoS. We assume that the to-
tal available transmission power and bandwidth without reuse
among sensors for each sensors arepmax andBmax at each time
εm,n = fQ
(
Nm,nTm,nB0Cm,n −Nm,nTm,nB0Rm,n +(log Nm,nTm,nB0)/2√
Nm,nTm,nB0Vm,n
)
= fQ
(
Nm,nTm,nB0Cm,n −Nm,nTm,nB0Rm,n +(log Nm,nTm,nB0)/2
(loge)·
√
Nm,nTm,nB0
) (16)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

CHANG et al.: OPTIMIZING RESOURCE ALLOCA TION IN URLLC FOR REAL-TIME WIRELESS CONTROL SYSTEMS 8921
indexn, respectively, where the constraints can be expressed as
Nm,nB0pm,n ≤ pmax, (19)
and
Bm,n = Nm,nB0 ≤ Bmax. (20)
Based on the constraint of the reliability in URLLC, the
successful transmission probability can be expressed as
Pr{αm,n = 1} = 1−εm,n ≥ 1−εth, (21)
and the failed transmission probability can be expressed as
Pr{αm,n = 0} = εm,n <ε th, (22)
whereεth is the packet error probability bounded by the URLLC
QoS requirement. Furthermore, the communication time delay
should also be bounded by the URLLC QoS requirement. Then,
we have
Tm,n ≤ Tth. (23)
We assume that the sizes of payload λm for each sensor are
identical, which can be rewritten asλ. Then, for givenλ,w eh a v e
Nm,nTm,nB0Rm,n = λ. Then, (16) and (18) can be rewritten
as
εm,n = fQ
(
Nm,nTm,nB0Cm,n−λ+(logNm,nTm,nB0)/2
(loge)·
√
Nm,nTm,nB0
)
,
(24)
and
ηm,n = λNm,nB0(1−εm,n), (25)
B. Control Constraint
In this paper, we consider the control convergence rate ρm as
the constraint from the control aspect, where the sampling period
is ﬁxed and the inherent parameters of the plant are physical
reality and change only when the plants are different. Given
physical control system, the main control variables that can be
optimized are state sampling period sm,n and the control input
gain Θm, which jointly affect the control convergence rate ρm.
Then, the control convergence rate further affects the control
performance, e.g., control cost or stability. By constraint onρm,
the state sampling period sm,n and the control input gain Θm
are directly constrained. In other words, that the relationship be-
tween control convergence rate and wireless resource allocation
indicates the relationship between the main control variables
and wireless resource allocation. Thus, the co-design of this
paper focuses on control convergence rate and wireless resource
allocation.
To obtain the constraint on the control convergence rate, we
consider Lyapunov-like function for each plant, which can be
expressed as [32]
Δm(ξm)= ξTmQmξm, (26)
where Qm is a given positive deﬁnite matrix. The requirement
for the Lyapunov-like function is that these functions should
decrease at given rates ρm < 1 during the control process,
which means that the control process guarantees the plant state
decreasing to the pre-set point. However, affected by the con-
trol perturbation and stochastic communication coefﬁcients, the
Lyapunov-like function is random. Thus, for any possible value
of the current plant states ξm,n, the Lyapunov-like functions
needs to satisfy [32]
E[Δm(ξm,n+1)|ξm,n] ≤ ρmΔm(ξm,n)+ Tr(QmR′m) (27)
where E[·] represents the expectation operator and R′m =
(Rm 0). The control convergence is guaranteed with ρm < 1,
which has been discussed in [32]. We conclude it by the follow-
ing Lemma.
Lemma 1 (Control Convergence Lemma): If (27) holds for
each time stepn = 0, 1, 2,...,N , then by taking the expectation
at both sides and by iterating backwards we can obtain
E[Δm(ξm,N)] ≤ ρmE[Δm(ξm,N−1)]+ Tr(QmR′m)
≤···
≤ ρNmE[Δm(ξm,0)]+
N−1∑
n=0
ρnmTr(QmR′m).
(28)
Since the sum in (28) converges with ρm < 1, the second mo-
ments of the plant states decay exponentially, which is bounded
byTr(QmR′m)/(1−ρm).
■
C. Problem F ormulation
According to the constraints from the communication and
control aspects, we formulate the original communication-
control co-design problem as
max
Nm,n,pm,n,ρm
η =
M∑
m=1
N∑
n=1
ηm,n (29a)
s.t.
εm,n ≤ εth, (29b)
Nmpm,n ≤ pmax, (29c)
Bm,n ≤ Bmax, (29d)
Tm,n ≤ Tth, (29e)
E[Δm,n(ξm,n+1)|ξm,n] ≤ ρmΔm(ξm,n)+ Tr(QmR′m).
(29f)
In this problem, we intend to maximize the communication
SE with optimal wireless resource allocation in URLLC and
control convergence rate. More importantly, we jointly consider
the control constraint on the control convergence rate ρm and
communication constraint on URLLC QoS, which is difﬁcult
to deal with in the proposed communication-control co-design
since the control constraint (29f) seems independent with rest
of the communication constraint terms in (29). However, the
control constraint on the control convergence rate ρm can affect
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

8922 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 68, NO. 9, SEPTEMBER 2019
and is determined by the communication QoS actually. In the
next section, we will deal with the problem in (29) in details.
IV . OPTIMAL RESOURCE ALLOCA TION FOR THE
PROPOSED CO-DESIGN
In this section, we ﬁrst explore the relationship between
control and communication. Then, we discuss the solution for
the problem in (29).
A. Relationship Between Control and Communication
From (8), we can obtain that the plant state ξm,n in (8)
is determined by the control parameters and packet transmis-
sion. Then, the expression E[Δm(ξm,n+1)|ξm,n] depends on the
packet transmission probability. From (8), we can obtain that the
Lyapunov-like function can be expressed as
E[Δm(ξm,n+1)|ξm,n]
=P r{αm,n = 1}ξTm,nΩTe1QmΩe1ξm,n
+P r{αm,n = 0}ξTm,nΩTe0QmΩe0ξm,n
+ Tr(QmR′m), (30)
which indicates that the communication reliability can affect the
control Lyapunov-like function directly. Substituting (30) into
(29f), we can obtain
Pr{αm,n = 1}≥ ξTm,n(ΩTe0QmΩe0 −ρmQm)ξm,nξTm,n(ΩTe0QmΩe0 −ΩTe1QmΩe1)ξm,n, (31)
whereξm,n ⁄= 0.
From (31), we can obtain the relationship between the control
requirement on the control convergence rate ρm and communi-
cation reliability requirement Pr{αm,n = 1}. Here, the lower
bound of the communication reliability decreases monotonically
with ρm. This is reasonable since when ρm is small, the plant
state updates smoothly, which leads to good control performance
[15]. In summary, small ρm means good control performance
and needs high communication reliability to maintain the control
performance. On the contrary, largeρm means the loss in control
performance and does not need high communication reliability
to maintain the control performance. Furthermore, from (10)
and (31), we can obtain that the proposed relationship also
works in the scenario where there is no transmission time delay,
straightforwardly.
Let
cm =s u p
y∈Rn,y⁄=0
yT(ΩTe0QmΩe0 −ρmQm)y
yT(ΩTe0QmΩe0 −ΩTe1QmΩe1)y (32)
represent the supremum of the right-hand term in (31). Accord-
ing to Appendix A, we can obtain the optimal cm.
Based on the above discussion, we can obtain the following
theorem about the relationship between control and communi-
cation.
Theorem 1: In real-time wireless control systems, the com-
munication reliability is actually determined by the control per-
formance constrained by the requirement of control convergence
rate, rather than the suggested reliability in communications, i.e.,
being bounded by εth. Their relationship can be expressed as
Pr{αm,n = 1}≥ c∗m. (33)
■
Based on Theorem 1, we can obtain the following property.
Property 1: According to the relationship between the con-
trol performance constraint c∗m and the reliability requirement
1−εth in URLLC QoS, the actual resource consumption for
URLLC in real-time wireless control system can be divided into
the following three cases.
r Case A:Whenc∗m > 1−εth, the actual resource consump-
tion is higher than the bound in the traditional URLLC
resource allocation.
r Case B:Whenc∗m = 1−εth, the actual resource consump-
tion is equal to the bound in the traditional URLLC resource
allocation.
r Case C:Whenc∗m < 1−εth, the actual resource consump-
tion is lower than the bound in the traditional URLLC
resource allocation.
■
In the following of this section, we solve the optimal problem
in (29). First, we obtain the optimal communication resource
allocation with constraint on control convergence rate. Then,
the optimal control convergence rate can be obtained.
B. Optimal Resource Allocation
In this subsection, we ﬁrst convert the optimal problem into a
solvable problem. Then, we develop an algorithm to obtain the
solution for optimal resource allocation.
1) Problem Conversion: Though the state update of the con-
trol is relevant in different time index n, the wireless resource
allocation to guarantee the control requirement is independent.
In addition, the available resource, i.e., the transmission power
and bandwidth, is independent among different sensors. Thus,
we can drop the time indicesn and decompose Problem (29) into
M subproblems. Furthermore, the constraint on communication
reliability in (29b) should be replaced by the relationship in
Theorem 1. Thus, (29) can be rewritten as
max
Nm,pm
ηm = λNm(1−εm) (34a)
s.t.
εm ≤ 1−c∗m, (34b)
Nmpm ≤ pmax, (34c)
Bm ≤ Bmax, (34d)
Tm ≤ Tth, (34e)
where the control convergence rateρm is omitted in the optimal
variables since the expression (32) and the constraint in (34b)
indicate that ρm can be obtained by εm = 1−c∗m. The optimal
control convergence rate ρm will be discussed later in the next
subsection.
Our goal is to maximize the wireless SE by optimal resource
allocation, and meanwhile cause less resource consumption. To
achieve this goal in solving (34), the time delay should be long
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

CHANG et al.: OPTIMIZING RESOURCE ALLOCA TION IN URLLC FOR REAL-TIME WIRELESS CONTROL SYSTEMS 8923
enough, i.e.,
Tm = Tth, (35)
which is because large time domain resource can reduce other
resource consumption. Then, we have
εm = fQ
(NmTthB0Cm − λ+log(NmTthB0)/2
(loge)√NmTthB0
)
≤ 1−c∗m.
(36)
Then, (34) can be rewritten as
max
Nm,pm
λ
Nm
(1−εm)
s.t.
(34c),(34d),(36). (37a)
This is the ﬁnal expression of the problem formulation. Next,
we focus on the solution to this problem.
2) Problem Solution: In the sequel, we propose an iteration
algorithm to ﬁnd the global optimal solution of problem (37).
Before that, we need the following properties about ηm.
Property 2: Given Nm, ηm decreases monotonically with
p0. ■
Proof: It is easy to obtain thatfQ(·) in (36) decreases mono-
tonically with p0, Then, εm increases monotonically with pm.
Finally,ηm decreases monotonically with pm. ■
Property 3. Given pm, (37a) is a concave function with re-
spect to Nm. ■
Proof: See Appendix B. ■
Based on Property 2 and 3, we propose an iterative algorithm
to ﬁnd the optimal solution for problem (37). Given pm,t h e
optimal values of km that maximizes (37) can be found via
bisection method. By searching km, the optimal and minimum
value of pm can be obtained by (36). Thereby, we can obtain
the optimal resource allocation to maximize the communication
SE in (37). The details of the algorithm are provided in
Algorithm 1.
C. Optimal Control Convergence Rate
Once we obtain the maximum communication SE in (34),
the communication reliability(1−εm) can be obtained accord-
ingly. Then, we can obtain the optimal control convergence rate
ρ∗m to minimize control cost by solving the following equation
Pr{αm,n = 1} = 1−εm = c∗m
= ξTm,n(ΩTe0QmΩe0 −ρmQm)ξm,n
ξTm,n(ΩTe0QmΩe0 −ΩTe1QmΩe1)ξm,n.
(38)
Thereby, we can obtain an optimal overall system performance.
V. S IMULA TIONSRESULTS
In this section, we provide simulation results to demonstrate
the performance of the proposed method, where the system
models are the same as shown in Fig. 1 and Fig. 2. In the follow-
ing of this section, we ﬁrst illustrate the control performance.
Algorithm 1: The Proposed Iterative Algorithm for Optimal
Resource Allocation.
Input: c∗m,B0, Tth, λ,Nlm < 1,Nhm = Bmax/B0, and the
accuracy requirement of the bisection method ν
1: Set pm = pmax
2:Nm = N hm +N lm2
3: whileεm > 1−c∗m or Nmpm >p max do
4: while (|Nhm −Nlm| >ν ) do
5: Nm = N hm +N lm2
6: N∗k = Nk
7: if ∂(−ηm)∂Nm < 0 then
8: Nlm = Nm
9: N∗m = Nm
10: else if ∂(−ηm)∂Nm > 0 then
11: Nhm = Nm
12: else
13: N∗m = Nm
14: break
15: end if
16: end while
17: Obtain pm by solving
1−c∗m = fQ(NmTthB0Cm−λ+log(NmTthB0 )/2(loge)√NmTthB0 ) to
minimize transmission power
18: εm = fQ(NmTthB0Cm−λ+log(NmTthB0 )/2(loge)√NmTthB0 )
19: end while
20:p∗m = pm
Output: Optimal resource allocation N∗m andp∗m.
Then, we discuss the optimal resource allocation to maximize
the communication SE.
A. Control Performance
From the perspective of real-time wireless control, since M
plants are independent in communication-control co-design, we
assume that only two plants, i.e.,M = 2 plants, are considered in
the simulations. For simplicity, we assume that both plants have
the identical dynamics, where assume thatΩe0 = 1.5 andΩe1 =
0.5. We further assume that the given positive deﬁnite weight
matrix isQm = 1, the variance of the disturbance matrixnm(t)
is 1, i.e., Rm = 1, and the sample period is sm,n = 100 ms.
In addition, we adopt the average control cost to evaluate the
control performance [30], which can be expressed as
Jave = 1NΣNn=1x2m,n, (39)
where N = T/sm,n is adopted, and T is the total time of the
control process.
Fig. 3 shows the average control cost Jave with control time
increasing, where we consider three different decreasing rate
ρm, i.e., 0.01, 0.25, and 0.9. From the ﬁgure, all the curves
increase at the initial time. This is because the control process is
performed before the state returns to the pre-set point, where the
plant state update leads to the increasing of Jave . Furthermore,
as the control time increasing, whenρm is small, i.e.,ρm = 0.01,
the curve has a little drop and reaches to a low approximative
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

8924 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 68, NO. 9, SEPTEMBER 2019
Fig. 3. Average control cost with time increasing.
Fig. 4. Optimal c∗m with different control convergence rate ρm.
horizontal line smoothly. However, when ρm is large, i.e.,
ρm = 0.9, the curves have a little drop and reach to a high
approximative horizontal line roughly. This is reasonable since
the plant state update is smaller when the plant turns to stable
than that at the start phase, which leads to the average control cost
Jave has a little drop and reach to an approximative horizontal
line. These phenomenons indicate that small decreasing rate
ρm leads to smooth state updating, where we can obtain small
average control cost Jave updating. When ρm is large, the state
updating is rough, which leads to large average control cost
Jave updating. In addition, when ρm is small, i.e., ρm = 0.01,
the smooth state updating leads to low the average control cost
as the time is large enough, which means that small decreasing
rate has better control performance than large decreasing rate.
Fig. 4 shows the relationship between the optimal c∗m in
(32) when decreasing rate ρm is different. From the ﬁgure,
the curve decreases monotonically with ρm from c∗m = 1t o
c∗m = 0, which means that small ρm results in high constraint
on the communication reliability. This is reasonable since high
reliability can guarantee smooth decrease of the plant state from
control perspective, which leads to small decreasing rateρm and
small average control cost in Fig. 3.
From the above control results, we can obtain that Property 1
can be redescribed based on the different values of control
decreasing rate ρm, where c∗m(ρth)= 1−εth. Then the three
cases in Property 1 can be described as follows.
r Case I.ρm <ρ th: In this case,ρm <ρ th means thatc∗m >
c∗m(ρth)= 1−εth, where the allocated resource in tradi-
tional URLLC is failed in guaranteeing the required control
performance and more wireless resources are needed.
r Case II. ρm = ρth: In this case, ρm = ρth means that
c∗m = c∗m(ρth)= 1−εth, where the allocated resource
in traditional URLLC is just enough in guaranteeing the
required control performance and more wireless resource
are needed.
r Case III. ρm >ρ th: In this case, ρm >ρ th means that
c∗m <c ∗m(ρth)= 1−εth, where the allocated resource in
traditional URLLC is more than that needed in guarantee-
ing the required control performance and wireless resource
waste is presented.
In the following of this section, we discuss the communication
performance of our proposed method. Furthermore, we use
c∗m = 1− 10−9,c∗m = 1− 10−5, andc∗m = 1− 10−3 to discuss
the communication performance in the above three cases, re-
spectively.
B. Communication Performance
From the perspective of wireless communication, we assume
that the bandwidth of each subcarrier is 1 kHz, the single-
sided noise spectral density is −174 dBm/Hz, and the distance
between the base station and the plants is 100 m. For the
URLLC, the maximum packet transmission error probability
is εth = 10−5, the maximum transmission time delay for the
uplink isTth = 0.5 ms, and the maximum number of allocation
subcarrier is 60. In addition, we consider the traditional method
only considering communication aspect in [6] for comparison,
where the authors intended to minimize transmission power.
Fig. 5 demonstrates the wireless resource allocation when
payload information λm is different. Fig. 5(a) shows the total
power allocation. From the ﬁgure, the total resource alloca-
tion (i.e., multiplying transmission power by frequency band-
width) increases with communication reliability increasing from
Case III to Case I. This is reasonable since high reliability needs
more communication resource to support. Fig. 5(b) and Fig. 5(c)
show the allocated transmission power on each subcarrier and
the allocated number of subcarrier for the m-th sensor. From
Fig. 5(a), Fig. 5(b) and Fig. 5(c), both the allocated subcarri-
ers and allocated transmission power of the proposed method
increase monotonically with λm, which means that more pay-
load information needs more resources for transmission. From
Fig. 5(b), the allocated transmission power on each subcarrier of
the proposed method increases with communication reliability
increasing from Case III to Case I. However, from Fig. 5(c),
the allocated subcarriers of the proposed method decrease with
communication reliability increasing from Case III to Case I.
This is reasonable since the proposed method in Algorithm 1
leads to an increasing power allocation from Case III to Case I,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

CHANG et al.: OPTIMIZING RESOURCE ALLOCA TION IN URLLC FOR REAL-TIME WIRELESS CONTROL SYSTEMS 8925
Fig. 5. The optimal resource allocation with different payload information
λm.
which further leads to the subcarrier allocation reducing from
Case III to Case I while maintaining total resource allocation
increasing from Case III to Case I as shown in Fig. 5(a). In
summary, the higher control performance needs more commu-
nication resources. In addition, compared with the traditional
method in [6], the number of the allocated subcarrier of the
proposed method is signiﬁcantly reduced. For instance, the
number of the allocated subcarrier is reduced from 60 to 8 when
the payload information is 50 bits in Fig. 5(c), while the allocated
transmission power on each subcarrier of the proposed method
Fig. 6. The spectral efﬁciency with different payload information λm.
in Fig. 5(b) is increased from −65 dBm to −22 dBm, and the
total allocated transmission power of the proposed method in
Fig. 5(a) is increased from −50 dBm to −20 dBm. This is
reasonable since the traditional method aims to minimize the
transmission power with maximum allocated bandwidth, which
leads to lower total power allocation for the traditional method
as shown in Fig. 5(a).
Fig. 6 shows the spectral efﬁciency when payload information
λm is different. From the ﬁgure, it is easy to obtain that all the
curves increase with the payload information increasing. In addi-
tion, spectral efﬁciency increases with the communication relia-
bility increasing from Case III to Case I. This is reasonable since
the allocated subcarriers decrease with communication reliabil-
ity increasing from Case III to Case I in Fig. 5(c), which leads
to spectral efﬁciency increasing. Furthermore, compared with
traditional method in Case II, the proposed method has larger
spectral efﬁciency, i.e., at most 700% spectral efﬁciency perfor-
mance increasing when payload information is 50 bits. This is
reasonable since our method is optimal in maximizing SE.
VI. C ONCLUSION
In this paper, we proposed an optimal resource allocation
scheme to maximize the communication uplink spectral efﬁ-
ciency in URLLC for real-time wireless control systems. In this
scheme, we considered the URLLC service should satisfy the
requirement on control convergence rate, which is formulated
as a communication-control co-design problem. To solve the
hybrid problem, the control requirement was converted into a
constraint on the wireless communication reliability. Then, the
hybrid optimization problem can be replaced by a regular wire-
less resource allocation problem. We proved that the converted
problem is concave and an iteration algorithm is developed to
obtain the optimal solution. Based on that, the optimal control
convergence rate can be obtained. The simulation results showed
that the proposed method achieves the maximum spectral efﬁ-
ciency while maintaining the control performance. The proposed
co-design approach established a theoretic foundation for the
URLLC serviced real-time wireless control system performance
analysis and algorithm design.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

8926 IEEE TRANSACTIONS ON VEHICULAR TECHNOLOGY, VOL. 68, NO. 9, SEPTEMBER 2019
APPENDIX A
This appendix provides the detailed calculation of the optimal
cm.
Deﬁning Y = yyT , we can rewrite (32) as
cm =s u p
Y≽0
Tr
(
(ΩTe0QmΩe0 −ρmQm)Y)
Tr
(
(ΩTe0QmΩe0 −ΩTe1QmΩe1)Y). (40)
We assume
[Z]n,n = 1/Tr
(
(ΩTe0QmΩe0 −ΩTe1QmΩe1)Y). (41)
Then, (40) can be rewritten as [31]
c′m =s u p
Z∈Rn×n,
Tr
(
(ΩTe0QmΩe0 −ρmQm)Z) (42a)
s.t.
Tr
(
(ΩTe0QmΩe0 −ΩTe1QmΩe1)Z) = 1, (42b)
Z ≽ 0, (42c)
which is a typicalsemideﬁnite programming problem(SDP), and
can be easily solved by available concave optimization [33]–
[35]. Once (34) is solved, we can obtain the optimal Z∗ and
(c′m)∗. Then, the solution for (40) can be obtained by
Y∗ = Z∗ · 1/Tr ((ΩTe0P0Ωe0 −ΩTe1P0Ωe1)Y∗)
= Z∗
[Z∗n,n],
(43)
andc∗m can be obtained accordingly.
APPENDIX B
This appendix provides the proof that (37a) is a concave
function with respect to Nm.
Givenpm,ηm is a function with respect to Nm, whereNm ≥
1. From (36), we have
ηm = λNm
(
1−fQ
(NmTthB0Cm−λ+log(NmTthB0)/2
(loge)√NmTthB0
))
= f1(Nm)·f2(Nm), (44)
wheref1(Nm)= λNm , and
f2(Nm)= 1−fQ
(NmTthB0Cm−λ+log(NmTthB0)/2
(loge)√NmTthB0
)
.
(45)
Property 4: Given pm, f2(Nm) is a concave function with
respect to Nm. ■
Proof: Sincehm is constant during one packet transmission,
we assume |hm|2 = 1 to simplify the proof. Assuming G1 =
TthB0,G2 = G1 ·log(1+ gmpmN0B0 ), andG3 =( l o ge)√G1, then(44) can be rewritten as
f2(Nm)= 1−fQ
(NmG2 − λm +log(NmG1)/2
G3
√Nm
)
. (46)
Let
f3(Nm)= NmG2 − λm +log(NmG1)/2G3√Nm , (47)
then we take derivative with respect toNm in (47) and can obtain
∂f3(Nm)
∂Nm
= G3
2N
1
2
m
·
(
G1 log
(
1+ gmp0
N0B0
)
Nm +( 1+ λm)− log(G1Nm)2 )
= f4(Nm)·f5(Nm), (48)
wheref4(Nm)= G3
2N
1
2m
, and
f5(Nm)= G1 log(1+ gmp0N0B0)Nm+(1+ λm)− log(G1Nm)2 .(49)
In (48), it is obvious that f4(Nm) > 0 for any Nm > 0. In
(49), by taking derivative with respect to Nm, we can obtain
∂f5(Nm)
∂Nm
= G1 log
(
1+ gmpm
N0B0
)
− 12Nm. (50)
Let ∂f5(Nm)∂Nm = 0, then we have
Nm,0 = 12G1 log(1+ gmpmN0B0 ). (51)
Apparently, we have Nm,0 < 1 in (51). In addition, ∂f5(Nm)∂Nm
in (50) increases monotonically with Nm. Thus, ∂f5(Nm)∂Nm > 0when Nm ≥ 1, which means that f5(Nm) increases monoton-
ically with Nm. This leads to f5(Nm) > 0 when Nm ≥ 1.
Thereby, we can obtain ∂f3(Nm)∂Nm > 0 when Nm ≥ 1 in (48),which means that f3(Nm) increases monotonically with Nm.
Furthermore, since fQ(·) decreases monotonically, we can ob-
tain the Q-function in (46) decreases monotonically with re-
spective to Nm. In addition, fQ(·) is a convex function. Thus,
f2(Nm) is a concave function. ■
We have that f(Nm)= f1(Nm)·f2(Nm) is the perspective
function of f2(Nm). Then, f(Nm) is a concave function with
respect to Nm [33].
REFERENCES
[1] X. Li, Y . Y u, G. Sun, and K. Chen, “Connected vehicles’ security from
the perspective of the in-vehicle network,” IEEE Netw. , vol. 32, no. 3,
pp. 58–63, Jun. 2018.
[2] Y . Sadi and S. C. Ergen, “Optimal power control, rate adaptation, and
scheduling for UWB-based intravehicular wireless sensor networks,”
IEEE Trans. V eh. Technol., vol. 62, no. 1, pp. 219–234, Jan. 2013.
[3] P . Wang, B. Di, H. Zhang, K. Bian, and L. Song, “Energy efﬁcient V2X-
enabled communications in cellular networks,”IEEE Trans. V eh. Technol.,
vol. 68, no. 1, pp. 554–564, Jan. 2019.
[4] S. Li, S. Xu, X. Huang, B. Cheng, and H. Peng, “Eco-departure of
connected vehicles with V2X communication at signalized intersections,”
IEEE Trans. V eh. Technol., vol. 64, no. 12, pp. 5439–5449, Dec. 2015.
[5] C. She, C. Y ang, and T. Q. S. Quek, “Uplink transmission design with
massive machine type devices in tactile Internet,” inProc. IEEE Globecom
Workshops, Dec. 2016, pp. 1–6.
[6] C. She, C. Y ang, and T. Quek, “Cross-layer optimization for ultra-reliable
and low-latency radio access networks,” IEEE Trans. Wireless Commun.,
vol. 17, no. 1, pp. 127–141, Jan. 2018.
[7] C. Sun, C. She, C. Y ang, T. Quek, Y . Li, and B. Vucetic, “Optimizing
resource allocation in the short blocklength regime for ultra-reliable and
low-latency communications,” IEEE Trans. Wireless Commun. , vol. 18,
no. 1, pp. 402–415, Jan. 2019.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply. 

CHANG et al.: OPTIMIZING RESOURCE ALLOCA TION IN URLLC FOR REAL-TIME WIRELESS CONTROL SYSTEMS 8927
[ 8 ] V .N .S w a m yet al., “Real-time cooperative communication for automation
over wireless,” IEEE Trans. Wireless Commun., vol. 16, no. 11, pp. 7168–
7183, Nov. 2017.
[9] Y . Y u, H. Chen, Y . Li, Z. Ding, and B. Vucetic, “On the performance of
non-orthogonal multiple access in short-packet communications,” IEEE
Commun. Lett., vol. 22, no. 3, pp. 590–593, Dec. 2017.
[10] H. V . Mendis and F. Li, “Achieving ultra reliable communication in 5G
networks: A dependability perspective availability analysis in the space
domain,” IEEE Commun. Lett., vol. 21, no. 9, pp. 2057–2060, Sep. 2017.
[11] E. Dosti, U. Wijewardhana, H. Alves, and M. Latva-aho, “Ultra reliable
communication via optimum power allocation for type-I ARQ in ﬁnite
block-length,” in Proc. IEEE Inter . Conf. Commun., May 2017, pp. 1–6.
[12] K. Trillingsgaard and P . Popovski, “Downlink transmission of short pack-
ets: Framing and control information revisited,” IEEE Trans. Commun. ,
vol. 65, no. 5, pp. 2048–2061, May 2017.
[13] Y . Chen, L. Cheng, and L. Wang, “Prioritized resource reservation for
reducing random access delay in 5G URLLC,” in Proc. IEEE Annu. Intr .
Symp. Personal, Indoor , Mobile Radio Commun., Oct. 2017, pp. 1–5.
[14] R. Kotaba, C. Manchón, T. Balercia, and P . Popovski, “Uplink transmis-
sions in URLLC systems with shared diversity resources,” IEEE Wireless
Commun. Lett., vol. 7, no. 4, pp. 590–593, Aug. 2018.
[15] L. Schenato, B. Sinopoli, M. Franceschetti, K. Poola, and S. Sastry,
“Foundations of control and estimation over lossy networks,” Proc. IEEE,
vol. 95, no. 1, pp. 163–187, Jan. 2007.
[16] A. Cetinkaya, H. Ishii, and T. Hayakawa, “Networked control under
random and malicious packet losses,”IEEE Trans. Autom. Control, vol. 62,
no. 5, pp. 2434–2449, Sep. 2017.
[17] Y . Feng, X. Chen, and G. Gu, “Output feedback stabilization for discrete-
time systems under limited communication,”IEEE Trans. Autom. Control,
vol. 62, no. 4, pp. 1927–1932, Apr. 2017.
[18] L. Su and G. Chesi, “On the robust stability of uncertain discrete-time
networked control systems over fading channels,” in Proc. Amer . Control
Conf., Jul. 2015, pp. 6010–6015.
[19] L. Shi, Y . Y uan, and J. Chen, “Finite horizon LQR control with limited
controller-system communication,” IEEE Trans. Autom. Control, vol. 62,
no. 7, pp. 1835–1841, Jul. 2013.
[20] P . Park, S. Ergen, C. Fischione, C. Lu, and K. Johansson, “Wireless network
design for control systems: A survey,” IEEE Commun. Surv. Tut. , pp.
978–1013, Secondquarter 2017.
[21] Y . Polyanskiy, H. V . Poor, and S. V erdu, “Channel coding rate in the ﬁnite
blocklength regime,” IEEE Trans. Inf. Theory , vol. 56, no. 5, pp. 2307–
2359, May 2010.
[22] G. Durisi, T. Koch, and P . Popovski, “Toward massive, ultrareliable, and
low-latency wireless communication with short packets,” IEEE Proc. ,
vol. 104, no. 9, pp. 1711–1726, Aug. 2016.
[23] G. Zhao, M. A. Imran, Z. Pang, Z. Chen, and L. Li, “Toward real-time
control in future wireless networks: Communication-control co-design,”
IEEE Commun. Mag., vol. 57, no. 2, pp. 138–144, Feb. 2019.
[24] P . Park, J. Araújo, and K. H. Johansson, “Wireless networked control
system co-design,” in Proc. IEEE Inter . Conf. Netw., Sensing Control ,
2011, pp. 486–491.
[25] B. Chang, G. Zhao, M. Imran, Z. Chen, and L. Li, “Dynamic wireless
QoS analysis for real-time control in URLLC,” in Proc. IEEE Globecom
Workshops, Dec. 2018, pp. 1–5.
[26] T. Zeng, O. Semiari, W. Saad, and M. Bennis, “Integrated communications
and control co-design for wireless vehicular platoon systems,” in Proc.
IEEE Inter . Conf. Commun., May 2018, pp. 1–6.
[27] A. Firooznia, J. Ploeg, N. Wouw, and H. Zwar, “Co-design of controller
and communication topology for vehicular platooning,”IEEE Trans. Intell.
Transp. Syst., vol. 18, no. 10, pp. 2728–2739, Oct. 2017.
[28] 3GPP , “Study on scenarios and requirements for next-generation access
technologies,” Technical Speciﬁcation Group Radio Access Network,
Tech. Rep. 38.913, Release 14, Oct. 2016.
[29] W. Y ang, G. Durisi, T. Koch, and Y . Polyanskiy, “Quasi-static multiplean-
tenna fading channels at ﬁnite blocklength,” IEEE Trans. Inf. Theory ,
vol. 60, no. 7, pp. 4232–4264, Jul. 2014.
[30] J. Sarangapani and H. Xu, Optimal Networked Control Systems With
MATLAB (Automation and Control Engineering) . Boca Raton, FL, USA:
CRC Press, 2015.
[31] C. Chi, W. Li, and C Lin, Convex Optimization F or Signal Processing and
Communications: From Fundamentals to Applications . Boca Raton, FL,
USA: CRC Press, 2017.
[32] K. Gatsis, M. Pajic, A. Ribeiro, and G. J. Pappas, “Opportunistic control
over shared wireless channels,” IEEE Trans. Autom. Control , vol. 60,
no. 12, pp. 3140–3155, Dec. 2015.
[33] S. Boyd and L. V andenberghe, Convex Optimization. Cambridge, U.K.:
Cambridge Univ. Press, 2004.
[34] S. Ruscheweyh and T. Small, Comment. Math. Helv., 1973.
[35] E. Chong and S. ˙Zak, An Introduction to Optimization, 4th ed. Wiley, 2001.
Bo Chang received the bachelor’s and master’s de-
grees from the University of Electronic Science and
Technology of China (UESTC), Chengdu, China,
where he is currently working toward the Ph.D. degree
with the National Key Laboratory of Science and
Technology on Communications. From May 2019 to
May 2020, he is a Visiting Student at the University
of Glasgow, Glasgow, Scotland. His research inter-
ests include cognitive radio, wireless localization,
ultra-reliable and low-latency communications, and
communication and control co-design for Industrial
Internet-of-Things (IIoT).
Lei Zhang received the Ph.D. degree from the Uni-
versity of Shefﬁeld, Shefﬁeld, U.K. He was a Re-
search Engineer with Huawei Communication Tech-
nology Laboratory (CT Lab), and a Research Fellow
in the 5G Innovation Centre (5GIC), Institute of Com-
munications (ICS), University of Surrey, Surrey, U.K.
He is now a Lecturer with the University of Glasgow,
Glasgow, U.K. He has 16 US/UK/EU/China granted
patents on wireless communications. His research
interests broadly lie in the communications and array
signal processing, including radio access network
slicing (RAN slicing), wireless blockchain systems, new air interface design,
Internet of Things (IoT), multi-antenna signal processing, massive MIMO
systems, etc. Dr. Zhang also holds a Visiting Position in 5GIC at the University
of Surrey. He is an Associate Editor of IEEE ACCESS.
Liying Li received the B.E. and Ph.D. degrees from
the University of Electronic Science and Technol-
ogy of China (UESTC), Chengdu, China, in 2005
and 2011, both in electrical engineering. She visited
Georgia Institute of Technology, GA, USA, from
2008–2010 and Lehigh University, PA, USA, in 2016.
Since 2011, she has been with the School of Automa-
tion Engineering, UESTC, where she is currently an
Associate Professor. Her research interests are within
the areas of wireless communications, smart grids,
and data science.
Guodong (Philip) Zhao (SM’16) received the Ph.D.
degree from Beihang University, Beijing, China, in
2011, and the B.E. degree from Xidian University,
Xian, China, in 2005. From 2011–2018, he was
an Associate Professor with the University of Elec-
tronic Science and Technology of China (UESTC),
Chengdu, China. Currently, he is a Lecturer (Assistant
Professor) with the University of Glasgow, Glasgow,
U.K. His current research interests include the areas
of wireless communications and control.
Zhi Chen (SM’16) received the B.Eng, M.Eng.,
and Ph.D. degrees in electrical engineering from the
University of Electronic Science and Technology of
China (UESTC), Chengdu, China, in 1997, 2000,
and 2006, respectively. In 2006, he joined the Na-
tional Key Laboratory of Science and Technology
on Communications, UESTC, where he has been a
Professor since 2013. He was a Visiting Scholar with
the University of California at Riverside, Riverside,
CA, USA, from 2010 to 2011. His current research
interests include 5G mobile communications, tactile
Internet, and terahertz communications. Prof. Chen has served as a Reviewer
for various international journals and conferences, including IEEE T RANS-
ACTIONS ON VEHICULAR TECHNOLOGY and IEEE T RANSACTIONS ON SIGNAL
PROCESSING.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:20:59 UTC from IEEE Xplore.  Restrictions apply.