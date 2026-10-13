---
title: "Integrated Sensing Communication and Over-the-Air Control of UAV Swarm Dynamics"
zotero_key: "ARDMTZWB"
pdf_key: "EUHD6I29"
collection: "UAV"
source: "Open-access PDF (arXiv, pypdf extraction)"
page_mapping: unverified
---

# Integrated Sensing Communication and Over-the-Air Control of UAV Swarm Dynamics — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
Integrated Sensing, Communication, and
Over-The-Air Control of UA V Swarm Dynamics
Zhuangkun Wei, Wenxiu Hu, Yathreb Bouazizi, Mengbang Zou, Chenguang Liu,
Yunfei Chen, Hongjian Sun, Julie McCann
Abstract—Coordinated controlling a large UA V swarm re-
quires significant spectrum resources due to the need for band-
width allocation per UA V , posing a challenge in resource-limited
environments. Over-the-air (OTA) control has emerged as a
spectrum-efficient approach, leveraging electromagnetic super-
position to form control signals at a base station (BS). However,
existing OTA controllers lack sufficient optimization variables to
meet UA V swarm control objectives and fail to integrate control
with other BS functions like sensing. This work proposes an
integrated sensing and OTA control framework (ISAC-OTA) for
UA V swarm. The BS performs OTA signal construction (uplink)
and dispatch (downlink) while simultaneously sensing objects.
Two uplink post-processing methods are developed: a control-
centric approach generating closed-form control signals via a
feedback-looped OTA control problem, and a sensing-centric
method mitigating transmission-induced interference for accurate
object sensing. For the downlink, a non-convex problem is
formulated and solved to minimize control signal dispatch (trans-
mission) error while maintaining a minimum sensing signal-to-
noise ratio (SNR). Simulation results show that the proposed
ISAC-OTA controller achieves control performance comparable
to the benchmark optimal control algorithm while maintaining
high sensing accuracy, despite OTA transmission interference.
Moreover, it eliminates the need for per-UA V bandwidth allo-
cation, showcasing a spectrum-efficient method for cooperative
control in future wireless systems.
Index Terms —Integrated sensing and communications, over-
the-air, control theory, UA V swarm.
I. I NTRODUCTION
The emergent Internet of Everything (IoE) and intelligent
edge learning systems will encompass vast numbers of devices
that require management and control for critical applications in
a coordinated manner, such as smart-grid synchronization [1],
drone formation flight [2], and platoon driving [3], etc. The
limited availability of spectrum resources, however, presents
a challenge in allocating bandwidth to a large number of
Zhuangkun Wei, Chenguang Liu, Yunfei Chen, and Hongjian Sun are with
the Department of Engineering, Durham University, DH1 3LE, UK. (Email:
zhuangkun.wei/chenguang.liu/yunfei.chen/hongjian.sun@durham.ac.uk)
Yathreb Bouazizi and Julie McCann are with the Department
of Computing, Imperial College London, SW7 2RH, UK.
(Email:y.bouazizi18/j.mccann@imperial.ac.uk)
Mengbang Zou is with the School of Aerospace, Transport, and
Manufacturing, Cranfield University, MK43 0AL, UK. (Email:
m.zou@cranfield.ac.uk)
Wenxiu Hu is with the Optoelectronics Research Centre, Southampton
University, SO17 1BJ, UK. (Email: w.hu@soton.ac.uk) Corresponding
Author: Wenxiu Hu
This work is supported by the Engineering and Physical Sciences Research
Council: Communications Hub For Empowering Distributed ClouD
Computing Applications And Research (CHEDDAR) with grant id:
EP/X040518/1 and EP/Y037421/1.
TABLE I
CONCEPTUAL COMPARISON WITH OTHER ISAC, OTA, AND UAV WORKS
Research
Categories
Number of
required
channels
Feedback-
looped control
objectives
Sensing in
the same
frequency
UA V trajectory opti-
mization
Number of
UA Vs
× ×
ISAC-UA V
trajectory
optimization
Number of
UA Vs
× ✓
OTA-FL 1 × ×
ISAC OTA-FL 1 × ✓
Existing control the-
ory: LQR, MPC, etc
Number of
UA Vs
✓ ×
OTA-Control. 1 Current versions
cannot work for
UA V swarm
×
ISAC-OTA Control.
(proposd)
1 ✓ ✓
networked devices for coordinated management. This issue
becomes particularly severe in cooperative control frameworks
[1], [4] and multi-UA V trajectory optimization scenarios [5],
where each terminal requires dedicated frequency bandwidth
for information exchange including reporting its state to a
coordinate controller and to receive control signals. Actually,
due to this limited spectrum, current UA V swarm displays are
restricted to predefined trajectories for each UA V , rather than
allowing real-time path determination, not to mention UA V
coordination or networking for more complex tasks.
To address the spectrum scarcity challenges, the concept
of over-the-air (OTA) computation has been proposed. OTA
computations allow multiple devices to use the same time and
frequency block to transmit their signals to a server or base-
station (BS), where the signal processing of transmitted signals
can be directly performed by tuning the electromagnetic waves
in the air. In doing so, OTA computation can save the spectrum
resources for a wide range of linear operations in IoE and edge
computing system. One popular example lies in the designs
of OTA federated learning (OTA-FL) [6], where the linear
aggregation of neural network (NN) parameters transmitted
by selected terminal clients are pursued leveraging the linear
superposition of appropriately tuned wireless channels. Sev-
eral techniques have been developed to minimize the mean
squared error (MSE) between channel coefficients and linear
FL aggregation weights (e.g., FedAvg). These include but are
not limited to transmitter precoding and beamforming designs
[7], BS or server beamforming [8], movement and trajectory
optimization of mobile terminals [9], reconfigurable intelli-
arXiv:2502.07467v1  [eess.SP]  11 Feb 2025

2
gent surface (RIS) phase adjustment [10], [11], and recent
advanced fluid antennas [12]. However, the established OTA-
FL schemes cannot be extended to multi-device cooperative
control systems [13]. This is because OTA-FL are not designed
to address the complex feedback-looped objective function
of control signals, which involves the accumulated effects of
future predicted system states based on the feedback from the
current control signals. Moreover, the feedback-looped objec-
tive function creates a control layer state dependency among
different terminals, which differs from the independence or
spatiotemporal correlations typically assumed in FL.
To exploit the OTA concept in control theory, OTA con-
trollers have been proposed in [13], [14]. Compared with
traditional control frameworks, e.g., linear quadratic regulator
(LQR), and model predictive control (MPC), which require the
allocation of bandwidth for different terminals, OTA controller
allows all network nodes to transmit their observed states
on the same time and frequency block. Then, the received
signals at the BS (serving as the coordinate controller) form
the control signals through the linear superposition of com-
pensated wireless channels. In [13], a terminal transmitter
(Tx) power-allocation based OTA controller was proposed,
aiming to find the optimal transmission powers of network
terminals to minimize the H∞ based OTA control objective.
However, as the network state-space and control signal space
scale up, the size of the OTA control operator, defined by the
product of these dimensions, far exceeds the number of Tx-
power optimization variables provided by the antenna-limited
terminals. For instance, consider a cooperative control scenario
of 50 UA Vs, each of which has 6 states i.e., xyz-positions
and velocities, and 3 control variables i.e., xyz-accelerations.
The terminal Tx-power-based OTA controller can only have
62 × 50 = 1800 precoding variables, insufficient to configure
the linear control operator of size (3×50)×(6×50) = 45, 000
that maps a total of 6 × 50 states to 3 × 50 control signals,
leading to significant control errors and slow convergence
(shown later in Fig. 2).
Besides, current OTA controller designs do not integrate the
coordinate controller role with the diverse multi-functionalities
of BS for future wireless systems. The BS is envisioned to
have diverse functionalities, such as communications, compu-
tations and sensing. Thus, the integrated sensing and com-
munication (ISAC) concept has emerged as a promising en-
abler for future 6G and beyond wireless networks [15]–[17].
ISAC enables the cohabitation of communication and sensing
functionalities in the same hardware system. This integra-
tion leverages orthogonal subspace division (loose coupling)
[18], ranging from time frequency and code [19]–[22], to
spatial beamforming designs [23]–[25]. Using different levels
of integration, ISAC offers a great potential to shape the
future of several applications including smart healthcare [26],
smart transportation [27], [28], smart industry and critical
infrastructure monitoring [29].
The performance gains achieved by each of the ISAC and
the OTA computations make their integration appealing. The
instances include the framework designs of the over-the-air in-
tegrated sensing communication and computation (Air-ISCC)
[30], the integrated sensing and OTA computation (ISAA)
[31], and ISAC for OTA-FL (Fed-ISCC) [32]. Motivated by
these designs, a novel framework to integrate sensing and OTA
controller for spectrum efficient networked dynamics control
is necessary for large-scale IoE control scenarios, such as UA V
swarm and smart-grid.
In this work, we propose a novel integrated sensing and
OTA control framework, namely ISAC-OTA controller, for
UA V swarm system. Compared with other related works
in Table. I, the design of ISAC-OTA controller is able to
realize object sensing and coordinate feedback-looped control
of dynamical UA V swarm system in the same frequency. The
main contributions are as follows:
(1) We formulate an ISAC-OTA controller framework,
where BS serves as the coordinate controller of the dynamical
UA V swarm system, as well as performing the object sensing
tasks, within the same time and frequency block. In the UA V-
BS uplink, BS is designed to (i) construct the overall control
signal for UA V swarm from the OTA transmitted UA V states
corrupted by the echoed radar signal interference, and (ii)
perform the sensing task with uplink transmission interference.
In the BS-UA V downlink process, BS is designed to dispatch
its OTA-constructed control signals dedicated to each UA V ,
and maintain the sensing performance that leverages both the
downlink transmission signal and radar sensing signal.
(2) In the uplink process, we design two post-processing
matrices at BS: namely control-centric and sensing-centric
matrices, to avoid the interference between OTA state trans-
mission and echoed radar signal. For UA V coordinate control
purposes, a feedback-lopped control objective function is for-
mulated, incorporating the wireless channels and the control-
centric BS post-processing matrix into the accumulated state
error minimization problem. Then, we convert the complex
feedback-looped objective function to a mini-max eigenvalue
problem, and deduce the optimal closed-form control signal.
For sensing purposes, to mitigate the interference from uplink
state transmission, the sensing-centric post-processing matrix
is derived via the orthogonal subspace to the uplink transmis-
sion channels.
(3) In downlink designs, an optimization problem is formu-
lated to minimize the transmission error of control signals, as
well as maintain the minimum BS sensing signal-to-noise ratio
(SNR). Unlike the download process in OTA-FL (e.g., Fed-
ISCC [32]), where every client receives the same data (i.e.,
global NN parameters), each UA V must be assigned only its
portion of the overall control signals. This requires more com-
plex designs and optimization for the BS precoding dispatch
matrix and the BS sensing beamforming vector. To address
the non-convex issue in the formulated downlink optimization
problem, a successive convex approximation (SCA) based
iterative algorithm is designed to find numerical solutions
of optimal (sub-optimal) BS precoding matrix and sensing
beamforming vector.
(4) We evaluate our proposed ISAC-OTA controller in the
coordinate control scenario with 50 UA Vs. The results show
that the ISAC-OTA controller can (i) achieve comparable con-
trol performance (in terms of error and time convergence) to
the benchmark LQR algorithm, without the need for bandwidth
allocation to each UA V , and (ii) offer remarkable sensing

3
accuracy despite OTA transmission interference.
The rest of this work is structured as follows. The net-
worked dynamical system model of UA V swarm, and the
wireless communication model are described in Section II. The
overall schematics of our ISAC-OTA controller framework is
elaborated in Section III. In Sections IV-V, the uplink and
downlink optimizations for ISAC-OTA controller are detailed.
The simulation results are shown and analyzed in Section VI.
We finally conclude our work in Section VII.
In the following, we use bold lower-case letters for vec-
tors, and bold capital letters for matrices. We use ∥ · ∥2 to
denote the 2-norm, ∥ · ∥F to denote the Frobenius norm, and
diag(·) to diagonalize a vector. | · |represents the absolute
value of a complex value. The matrix transpose, conjugate
transpose, element-wise conjugate, Kronecker product, trace,
and vectorize operators are denoted as (·)T , (·)H, (·)∗, ⊗,
tr(·), and vec (·). λmax(·) represents the largest eigenvalue of a
matrix. IN represents the identity matrix with size N ×N. E(·)
represents the expectation. ℜ{·} denotes to take the real part
of a complex number. CN (µ, σ2) is to represent the complex
Gaussian distribution with mean µ and variance σ2.
II. S YSTEM MODEL
In this work, we consider a cooperative control scenario of
N ∈ N+ UA Vs, where a BS serves as the coordinate controller
for the UA V swarm dynamic system, as well as for the object
sensing, as is shown in Fig. 1(a).
Traditionally, for coordinated control purposes, each UA V
is typically allocated a unique bandwidth as an orthogonal
channel for state transmission and control signal reception.
To save bandwidth resources, we leverage the concept of
an over-the-air controller [13]. The OTA-controller allows all
nodes to transmit their observed state values to the coordinate
controller, through the same frequency over the air (with-
out any digital modulation, and time or frequency division).
These state values are sent via electromagnetic waves that
are superposed with different channel coefficients, which, if
properly tuned, allow the direct obtaining of the cooperative
control signals at the BS. Here, we design a novel ISAC-OTA
controller, which leverages the strong channel compensation
ability of the BS, to integrate OTA control and sensing in the
same time and frequency block to control the UA V swarm.
A. Control Model of UA V Swarm Dynamical System
The networked dynamical system is the coordinated control
scenario of N UA Vs. Each n-th UA V has 6 states (xyz-
positions and velocities), denoted as x(n)k ∈ R6, and are con-
trolled by the motor force induced xyz-accelerations, denoted
as u(n)k ∈ R3, where k ∈ N+ is the controlling time step. The
state-space UA V dynamic model is [33]:
x(n)k+1 =
 I3 ∆tI3
O3×3 I3

| {z }
A
x(n)k +
∆2t /2I3
∆tI3

| {z }
B
u(n)k ,
y(n)k+1 = C · x(n)k+1 + n(n)k+1
(1)
where ∆t is the control interval. Here, the UA V dynamical
system contains only their xyz positions to accelerations that
will be coordinated with each other; the conversion of obtained
xyz-acceleration to roll, pitch, and yaw rates and motor forces
are locally pursued in each UA V [34]. y(n)k+1 represents the
observation of n-th UA V to measure its state at (k + 1)-th
controlling period, with the observation matrix C = I6 and
the observation noise n(n)k+1 ∼ N(0, σ2n).
To coordinately control N UA Vs, we specify the
overall networked dynamical system by stacking states,
control signals, observed states, and noises of each
UA V , i.e., xk = [( x(1)k )T , · · ·, (x(N )k )T ]T , uk =
[(u(1)k )T , · · ·, (u(N )k )T ]T , yk = [( y(1)k )T , · · ·, (y(N )k )T ]T ,
and nk = [( n(1)k )T , · · ·, (n(N )k )T ]T . The overall networked
dynamical state-space model can be then expressed as:
xk+1 = A · xk + B · uk,
yk+1 = C · xk+1 + nk+1
(2)
where A = IN ⊗ A, B = IN ⊗ B, and C = IN ⊗ C.
B. Wireless Channel Model
The implementation of both OTA control of networked
dynamical system and object sensing requires the uplink and
downlink processes. Each UA V is equipped with a single
antenna to transmit its observed state to the BS in the uplink,
and receive the control signal from the BS in the downlink.
The BS is equipped with a half-wavelength spaced uniform
linear array (ULA), which consists of Nr ∈ N+ Rx antennas
to receive uplink OTA constructed control signals and radar
echo signals for sensing, and Nt ∈ N+ Tx antennas to send
downlink integrated control and sensing signals.
The uplink channel from the n-th UA V to BS, denoted as
h(ul)nS ∈ CNr×1, and the downlink channel from BS to the n-
th UA V , denoted as h(dl)Sn ∈ C1×Nt, are formulated via the
narrow-band geometric models, i.e., [35]
h(ul)nS = ρnS,1 · ψ(θnS,1, Nr) +
LX
l=2
ρnS,l·ψ (θnS,l, Nr) ,
h(dl)Sn = ρSn,1 · ψT (θSn,1, Nt) +
LX
l=2
ρSn,l·ψT (θnS,l, Nt)
(3)
In Eq. (3), L is the number of paths including 1 line-of-sight
(LoS) and L−1 non-LoS (NLoS) paths [35]. ρnS,1 = ρSn,1 =q
C0 · d−ηLoSnS are the gains of the LoS paths between UA V n
and BS, and ρnS,l, ρSn,l ∼ CN
 
0, C0 · d−ηNLoSnS /(L − 1) , l=
2, · · ·, L are the l-th NLoS path gains from UA V n to
BS and from BS to UA V n, respectively, with dnS the
distance between UA V n and BS, C0 the path loss at the
reference distance of 1m, and ηLoS and ηNLoS the exponential
LoS and NLoS loss factors. θnS,l, θSn,l ∈ [−π/2, π/2] are
the half-space azimuth angles of the l-th path arriving at
(uplink) and departing from (downlink) BS. ψ(θ, M) ≜
[1, exp(jπ cos θ), · · ·, exp(jπM cos θ)]T defines the spatial
channel vector of BS ULA.
For the BS sensing task, we consider the echoed radar
response model to characterize the radar response matrix of a
target [36], i.e.,
G = β · ψ(αo, Nr) · ψT (αo, Nt) (4)

4
Precoding 
𝐖𝑇
Sense 
signal s
⋮
𝐡𝑛𝑆(ul)ISAC-OTA controller
𝐱𝑘+1 = 𝐀𝐱𝑘 + 𝐁𝐮𝑘
States-space
𝐮𝑘
BS downlink 
ISAC signal 
transmission
OTA uplink 
transmitted 𝐱𝑘 
+
+
OTA control 
gain 𝐖𝑅
Sense. 
beamform v
Sensing 
process 𝐖𝑆
Sensing
𝐡𝑆𝑛(dl)
𝐆
• Coordinate UAV control
• Object sensing
• Uplink: OTA control signal 
construction 𝐮𝑘
• Downlink: OTA dispatch 
control signal 𝐮𝑘
Echoed 
radar 
signalInterfered OTA & radar signal
BS
(a) Overall Schematics (b) Control & Comm. Timeline
𝐱𝑘+1
𝐱𝑘
𝐮𝑘
⋮
𝑘-th 
control 
period 
0.02s
Channel est.
OTA uplink comm.
BS process: 
control & 
sensing
Channel est.
Downlink ISAC
BS precode, 
beamform
Fig. 1. Schematic flow of ISAC-OTA controller.
where β is the complex channel gain that includes both the
round-trip path-loss and the radar cross section (RCS), and αo
is the angle of the sensing object that will be estimated jointly
in this work with the OTA control objective.
III. S CHEMATIC OF ISAC-OTA C ONTROLLER
We consider a total of K ∈ N+ controlling periods. In
each controlling period, BS will (i) generate control signals
from the received UA V states in the uplink, (ii) dispatch the
generated control signal to each UA V , and (iii) perform the
object sensing task.
A. UA V-BS Uplink
The UA V-BS uplink aims to transmit all UA V states through
OTA mode in the same frequency, to BS to generate the overall
control signal uk. Before the k-th controlling period, uplink
channel estimation is conducted at BS when it receives the
pilot sequences transmitted by all UA Vs in the same frequency.
At the start of the k-th controlling period, all UA Vs transmit
their observed 6-state in 6 time division to the BS, i.e., y(n)k =
x(n)k + n(n)k with x(n)k = [ x(n)k,1, x(n)k,2, x(n)k,3, x(n)k,4, x(n)k,5, x(n)k,6]T .
BS then receives r(ul)k [1], r(ul)k [2], r(ul)k [3], r(ul)k [4], r(ul)k [5], and
r(ul)k [6] of 6 successive uplink transmission time-slots, i.e.,
r(ul)k [t] =
NX
n=1
h(ul)nS · γ(ul) · x(n)k,t +G · s[t] + ε(ul)k [t],
t = 1, · · ·, 6,
(5)
where γ(ul) is the predefined uplink scaling factor to constrain
transmission power, i.e., |γ(ul)y(n)k,t| ≤1W, and is known to all
UA Vs and BS. In Eq. (5), G · s[t] represents the received
echoed radar signal s[t] ∈ CN(0, 1) at t time-slot. The
existence of the echoed radar signal in the ISAC uplink is due
to the radar’s continuous operation, as it persistently transmits
signals for sensing purposes. ε(ul)k [t] ∼ CN(0, σ2INr ) is the
noise vector that involves received noise and observation noise,
with variance σ2.
After the BS receives all 6 signals, the BS stacks all of them
as r(ul)k , i.e.,
r(ul)k = vec hr(ul)k [1], r(ul)k [2], r(ul)k [3], r(ul)k [4], r(ul)k [5], r(ul)k [6]i .
(6)
The received signal r(ul)k [t], t = 1 , · · ·, 6 and its stacked
version r(ul)k , will be used to (i) construct the OTA control
signal uk, and (ii) perform object sensing task. The challenge
lies in that the uplink state transmission and radar sensing
signal interfere with each other. The concept of OTA signal
processing applies here, whereby two BS post-processing
matrices WR and WS will be designed in Section IV: WR
is to compensate the uplink channel coefficients to directly
construct control signal uk, and WS is to derive an accurate
sensing signal by projecting to the orthogonal transmission
subspace. The post-processed results, i.e.,
uk = WR · r(ul)k , (7a)
q[t] = WS · r(ul)k [t], t = 1, · · ·, 6 (7b)
are the constructed OTA control signal, and the input of the
MUSIC algorithm for object sensing, respectively.
B. BS-UA V Downlink Procedure
After BS constructs the OTA control signal uk for k-th
controlling period, BS will (i) send UA Vs’ their own control
signal via the OTA mode using the same frequency, as well
as (ii) maintain the object sensing task.
Recall that uk = [( u(1)k )T , · · ·, (u(N )k )T ]T , and each
u(n)k = [ u(n)k,1, u(n)k,2, u(n)k,3]T contains 3 signals. BS therefore
will split and send the whole uk into 3 parts in 3 succes-
sive downlink transmission time-slots, denoted as ˜uk[t] ≜
[(u(1)k,t )T , (u(2)k,t )T , · · ·, (u(N )k,t )T ]T , t = 1 , 2, 3. Then, as is

5
integrated with the radar sensing purposes, The BS downlink
ISAC signal is expressed as:
ζk[t] = WT · ˜uk[t] + v · s[t], t = 1, 2, 3, (8)
where WT is the BS precoding matrix, and v is the sensing
beamforming vector. The designs of WT and v are required to
balance both the control signal transmission accuracy at each
UA V , and the radar sensing performance at BS, which will be
detailed in Section V.
The received signals at n-th UA V of the corresponding
3 successive transmission time-slots are denoted as z(n)k [1]
z(n)k [2] and z(n)k [3], which are expressed as:
z(n)k [t] = h(dl)Sn · ζk[t] + ϵ(n)k [t], t = 1, 2, 3, (9)
where ϵ(n)k [t] ∼ CN(0, σ2) is the received noise. The n-th
UA V then constructs its control signal u(n)k by scaling its
received signals via the scaling factor a, i.e.,
u(n)k = a · hz(n)k [1], z(n)k [2], z(n)k [3]iT . (10)
Here, the scaling factor is optimized in BS and sent in advance
to all UA Vs in an error-free manner [37]. The constructed
control signal u(n)k will be further input to the local controller
of UA V n to compute the row pitch and yaw rates, and the
forces of 4 rotors [34].
For sensing at BS, its received signal is from the continuous
radar signal echoed by the object of the interest, i.e.,
r(dl)k [t] = G · ζk[t] + ε(dl)k [t], t = 1, 2, 3, (11)
where ε(dl)k [t] ∼ CN(0, σ2INr ) is BS received noise vector.
MUSIC algorithm (detailed in Appendix A) will then be
employed for sensing tasks.
IV. U PLINK ISAC-OTA C ONTROL DESIGNS
In this section, we elaborate on the designs of optimizations
for the uplink OTA control signal construction, as well as
maintaining the integrated sensing operation. From Eq. (7), the
optimization in the UA V-BS uplink process contains the BS
post-processing matrices, i.e., (i) WR for OTA construction of
the control signal uk, and (ii) WS for the sensing task with
uplink signal interference.
A. BS Post-processing Matrix for Control Signal Construction
The aim of dynamical system controlling is to make the
system state xk approach the designated reference state. We
first construct the OTA-combined control objective by inte-
grating the wireless channel coefficients into the widely used
quadratic control optimization.
1) OTA-Combined Control Objective: Without the loss of
generality, we consider xk as the state error between the
system state xk and a zero reference [38]. Then, the widely-
studied feedback-looped objective function and the corre-
sponding optimization problem is employed here as [38], [39]:
Jk(xk) ≜ minuk,··· ,uk+K−1
K−1X
i=0
xHk+iQxk+i + uHk+iRuk+i
(12a)
s.t. (2) (12b)
where Q ∈ R6N ×6N and R ∈ R3N ×3N are predefined
positive semi-definite symmetrical matrices.
In linear control cases where the control signal uk is linear
to the system state xk (e.g., the OTA controller from Eq. (7a)),
a quadratic form Jk(xk) = xHk Pkxk can be founded, with Pk
a symmetrical positive semi-definite matrix [39]. As such, Eq.
(12) is reformulated as:
Jk(xk) = xHk Qxk + minuk  uHk Ruk + Jk+1(Axk + Buk)
= min
uk
 
uHk Ruk +(Axk +Buk)H Pk+1(Axk +Buk)+const,
(13)
where const = xHk Qxk is irrelavant with the optimization
variable uk. In practice, we replace Pk+1 with P, the solution
of Riccati function that is obtained by iteratively solving P ←
Q + AH P A− AH PB(R + BH PB)−1BH P A, with initial
P = Q [38], [39].
As we take the OTA design of Eq. (7a) in the control signal
construction, the uplink optimization problem to design post-
processing matrix WR is formed as:
P1 : minuk, WR uTk Ruk +(Axk +Buk)HP (Axk +Buk) ,
(14a)
s.t. (7a). (14b)
2) Closed-F orm Control-centric BS Post-processing Matrix:
In this part, we derive a closed-form solution for problem P1.
First, using Eq. (5) and Eq. (7a), BS constructed control signal
uk can be further expressed as:
uk = WR · ˜H(ul) · xk + WR · Ξ · s + WR · εk, (15)
where ˜H(ul) ≜ H(ul) ⊗ I6 with H(ul) ≜
γ(ul)
h
h(ul)1S , h(ul)2S , · · ·, h(ul)N S
i
, and Ξ ≜ G ⊗ I6.
In Eq. (15), it is noticeable that the sensing signal s is
not related to the UA V control purpose. We hereby make
WRΞ ≡ 0 by representing the range of WHR via the
null-space of ΞH. To do this, we pursue compact singular-
value decomposition (SVD) of Ξ and obtain the compact left
singular matrix, denoted as Γ. Then, the orthogonal matrix of
Γ, denoted as Γ⊥ is used to characterize the rows of WR,
i.e.,
WR = W · Γ⊥, (16)
where W is the coefficient matrix to represent WR. By
combining Eqs. (15)-(16), the BS constructed control signal
uk can be re-written as:
uk = W · Γ⊥ · ˜H(ul) · xk + W · Γ⊥ · εk. (17)
Then, we take the orthogonal design of uk from Eqs. (16)-
(17) back into the objective function of Eq. (14a). To simplify
the expression, we denote Υ ≜ Γ⊥ ˜H(ul). The objective
function of Eq. (14a) is then expressed as:
uHk Ruk +(Axk +Buk)HP (Axk +Buk)
=xHk Π11xk + xHk Π12εk + εHk ΠH12xk + εHk Π22εk, (18)
where
Π11 =ΥH WH (BH PB + R)WΥ + AH PBWΥ
+ ΥH WH BH P A+ AH P A, (19)

6
Π12 =ΥH WH (BH PB + R)WΓ⊥ + AH PBWΓ⊥,
(20)
and
Π22 =ΓH⊥ WH (BH PB + R)WΓ⊥. (21)
As such, the optimization problem P1 in Eq. (14) is converted
to optimize the objective function in Eq. (18) with respect
to the optimization variable W that constitutes the post-
processing matrix WR, i.e.,
P1−1 : minW [xHk εH ]
 Π11 σΠ12
σΠH12 σ2Π22
 xk
ε

(22)
where ε is the normalized version (with variance 1) of εk.
It is noteworthy that in the optimization process of problem
P1−1, BS does not know the system state xk and the noise
vector ε. This is because that BS may not be able to recover all
UA V states, given the low-rank of channel matrix. To address
this, we convert the problem P1−1, and make it irrelevant
to the specific UA V state xk and noise vector. We do this by
minimizing the largest eigenvalue of the matrix that constitutes
the quadratic form of xk, i.e.,
P1−2 : minW λmax
 Π11 σΠ12
σΠH12 σ2Π22

(23)
In Eq. (23), the coefficient matrices can be factorized as:
 Π11 σΠ12
σΠH12 σ2Π22

=
 ΥH WH AH
σΓH⊥ WH 0

·Φ·
WΥ σWΓ⊥
A 0

(24)
with
Φ ≜

BH PB + R B H P
PB P

. (25)
By taking Eqs. (24)-(25) into Eq. (23), we convert the opti-
mization problem P1−2 as:
P1−3 : minW λmax
 ΥH WH AH
σΓH⊥ WH 0

Φ
WΥ σWΓ⊥
A 0

(26)
Given that Φ is hermitian and positive semi-definite, there ex-
ists Φ = ΨH Ψ via Cholesky factorization. Then, the objective
function in P1−3 is converted, given matrix inequalities, as:
λmax
 ΥH WH AH
σΓH⊥ WH 0

Φ
WΥ σWΓ⊥
A 0

=




Ψ · WΥ σWΓ⊥A 0 



22 < 



Ψ · WΥ σWΓ⊥A 0 



2F
(a)
= ∥Ψ1WΥ + Ψ2A∥2F + σ2 ∥Ψ1WΓ⊥∥2F
(b)
=



ΥT ⊗ Ψ1 vec(W) + vec(Ψ2A)


22
+ σ2



ΓT⊥ ⊗ Ψ1 vec(W)


22 . (27)
In Eq. (27), (a) is by rewriting Ψ = [Ψ1 Ψ2], and (b) is due
to ∥ · ∥2F = ∥vec(·)∥22 and Kronecker product computations.
As such, with the help of Eq. (27), the minimization
problem P1−3 in Eq. (26) is further transformed to minimize
its upper-bound, i.e.,
P1−4 : minW (27). (28)
The closed-form solution of P1−4 can be obtained by letting
the derivative of Eq. (27) to vec (W) equal 0, i.e.,
vec(W) = −
h
ΥΥH + σ2Γ⊥ΓH⊥

⊗

ΨH1 Ψ1
i−1
·

ΥT ⊗ Ψ1
H
· vec (Ψ2A) .
(29)
With Eq. (29), the BS post-processing matrix WR = WΓ⊥
can be computed and assigned for BS. The control signal uk is
then obtained after the post-processing of BS’s received signal
r(ul)k according to Eq. (7a).
3) Analysis of Upper-bound Relaxation Gap: It is notewor-
thy that the derivation of this closed-form OTA control solution
is based on the relaxed upper-bound in P1−4 of original OTA
control objective P1 in Eq. (14). We show that minimizing the
relaxed upper-bound in P1−4 does minimize the original OTA
control objective.
It is first seen that P1 and P1−1 is equivalent, as no relax-
ation is made from Eq. (14) to Eq. (22). Then, from P1−1 to
P1−2 and its equivalent P1−3, the largest eigenvalue relaxation
is used and indeed serves as a reachable upper-bound, for any
possible system state xk and normalized noise vector ε that
may be taken in the minimization problem in P1−1. Next, from
P1−3 to the final P1−4, the relaxation in Eq. (27) is from the
norm inequality, i.e., ¯ω · ∥ · ∥2F < ∥ · ∥22 < ∥ · ∥2F for some
¯ω ∈ (0, 1), which therefore leads to ¯ω · (27) < (26) < (27).
As such, by minimizing the objective function Eq. (27) in
P1−4, the optimization problem P1−3 can be minimized and
so does the original OTA control problem in P1.
B. BS Post-processing Matrix for Sensing
The sensing-centric BS post-processing matrix WS is to
separate echoed sensing signal from the transmitted UA V
states. By taking Eq. (5) into Eq. (7b), we rewrite the post-
processed received sensing signal as:
q[t] = WS · G · s[t] + WS ·
NX
n=1
h(ul)nS · γ(ul)x(n)k,t + WS · εk[t].
(30)
We here avoid the interference with the uplink transmitted
signal in the second term, by finding the orthogonal (quasi-
orthogonal) subspace to the uplink UA V-BS channels, i.e.,
WS ·
h
h(ul)1S , h(ul)2S , · · ·, h(ul)N S
i
= WS · H(ul) ≈ 0.
To achieve this, we first pursue complete SVD of H(ul) and
find the d ∈ N+ left singular vectors that correspond to the d
least singular values. We denote matrix D as the obtained d-
least left singular vectors. Then, we assign WS = DH, which
renders WS ·H(ul) = DH ·H(ul) ≈ 0. Next, the sensing process
will be pursued by the MUSIC algorithm, which is detailed
in Appendix A.
C. Overall Uplink Algorithm
The overall uplink algorithm for OTA control signal con-
struction and sensing purposes is provided in Algorithm 1. The
inputs are the dynamical system model parameters A and B,
the control setting matrices Q R and P, the stacked wireless

7
Algorithm 1: Uplink BS post-processing optimization
Input: Dynamical system model parameters A and B,
control parameters Q R and P, and stacked
channel H(ul) = γ(ul)[h(ul)1S , h(ul)2S , · · ·, h(ul)N S],˜H(ul) = H(ul) ⊗ I6 and the stacked echoed
channel Ξ = G ⊗ I6.
1 Compute Γ⊥ as the orthogonal matrix to the compact
left singular matrix of Ξ;
2 Compute Υ = Γ⊥ · ˜H(ul) and Φ via Eq. (25);
3 Compute Ψ via Cholesky factorization, i.e.,
Φ = ΨH Ψ;
4 Construct Ψ1 and Ψ2 via Ψ = [Ψ1 Ψ2];
5 Compute optimal W via Eq. (29);
6 Compute the BS post-processing matrix for OTA
control signal construction WR via Eq. (16);
7 Obtain the BS post-processing matrix for sensing WS
by the least left singular vectors of H(ul), to make
WSH(ul) ≈ 0;
Output: BS post-processing matrices WR and WS.
uplink channels H(ul) and ˜H(ul), and the echoed sensing chan-
nel G. Step 1 is to separate the received UA V statesxk and the
sensing signal by setting control-centric BS post-processing
matrix orthogonal to the sensing channel matrix Ξ. Steps 2-
4 are to compute the intermediate results that will be used
to compute the control-centric post-processing matrix. Steps
5-6 are to compute the optimized control-centric BS post-
processing matrix WR for OTA control signal construction.
The control signal uk can be constructed over the air at the
BS, if the computed control-centric BS post-processing matrix
WR is deployed, as is shown by Eq. (7a). Step 7 is to obtain
the sensing-centric BS post-processing matrix WS for sensing
purposes, and the sensing process will be pursued by the
MUSIC algorithm, detailed in Appendix A.
V. D OWNLINK OTA CONTROL SIGNAL DISPATCH &
SENSING OPTIMIZATIONS
After the uplink OTA construction of control signal uk at
BS, BS will pursue downlink process to balance the control
signal dispatch and its sensing task. In the downlink process,
BS aims to (i) send UA Vs’ their own control signal via OTA
mode using the same frequency, and (ii) maintain the object
sensing task. From Eqs. (8)-(11), we are required to optimize
the BS precoding matrix WT , the BS sensing beamforming
vector v, and the UA V receiver scaling factor a, to balance
the transmission and sensing metrics.
A. Transmission Metrics
In existing OTA-FL frameworks, all clients receive identical
information from the BS via the downlink signal (e.g., global
aggregated parameters in OTA-FL). As a result, the transmis-
sion metric is typically evaluated using statistical metrics such
as receiving SNR or related channel capacity. In contrast, the
downlink process of the OTA-control framework requires each
UA V to receive a specific portion of the overall control signal,
all transmitted by BS over the same frequency.
In this view, we assess the expectation error between UA Vs’
scaled received signals and the BS transmitted constructed
control signal. From Eqs. (8)-(10), we stack all UA Vs’ received
signals of the each of 3 successive downlink time-slots as
zk[t] ≜ [z(1)k [t], z(2)k [t] · · ·, z(N )k [t]]T , t = 1 , 2, 3, which
corresponds to BS transmitted control signals in 3 successive
downlink transmission time-slots, i.e., ˜uk[t] in Eq. (8). The
expected transmission error of t downlink transmission slot is
therefore expressed as:
E∼s,ϵk
h
∥a · zk[t] − ˜uk[t]∥22
i
(a)
=


 aH(dl)WT − INt  ˜uk[t]

22 + E∼s 

a · s[t] · H(dl)v

22
+ E∼ϵk
 
a∥ϵk[t]∥22
(b)
≤


 aH(dl)WT − INt 

2F ∥˜uk[t]∥22 + a2 

H(dl)v

22 + a2N σ2,(31)
where H(dl) ≜ [(h(dl)S1 )T , (h(dl)S2 )T , · · ·, (h(dl)SN )T ]T . In Eq. (31),
(a) is due to that the sensing signal s[t] and the received noise
vector ϵk[t] = [ ϵ(1)k [t], ϵ(2)k [t], · · ·, ϵ(N )k ]T are independent
random variables, with both zero expectations, i.e., E(s[t]) = 0
and E(ϵk[t]) = 0. (b) is because of the norm inequality, with
straightforward computations of the last two terms.
From Eq. (31), the expected transmission error of all 3
transmission time-slots can be expressed as follows:
1
3
X
t=1,2,3
E∼s,ϵk
h
∥a · zk[t] − ˜uk[t]∥22
i
(a)
<


 aH(dl)WT − INt 

2F ∥uk∥223 + a2 

H(dl)v

22 + a2N σ2,(32)
where (a) is due to the fact that the BS transmitted control
signal at 3 time-slots [˜uk[1], ˜uk[2], ˜uk[3]] is a rearrange of its
constructed OTA control signal uk. The expected transmission
error in Eq. (32) is in terms of the BS precoding matrix WT ,
the BS sensing beamforming vector v, and the scaling factor
a of all UA V receivers, which can be treated as an objective
function for ISAC optimization.
B. Minimum Sensing SNR
For sensing purposes in the downlink process, we employ
the minimum SNR of the received echoed radar signals at BS
as the sensing metric. According to Eq. (11), the minimum
sensing SNR corresponding to the 3 successive BS downlink
transmission time-slots are expressed as:
SNR(dl-echo) = min
t=1,2,3
E∼s
 
∥G · (WT · ˜uk[t] + v · s[t])∥22
E∼εk (∥εk[t]∥22)
= min
t=1,2,3
∥GWT ˜uk[t]∥22 + ∥Gv∥22
N · σ2 ,
(33)
given the fact that E(s[t]) = 0.
To ensure the sensing performance, the sensing SNR should
be kept large through the optimization variables WT and
v, which, however, is conflicting when trying to minimize
transmission error in Eq. (32). In the next part, we will design
and solve the corresponding ISAC optimization problem to
balance the sensing and transmission performance.

8
C. ISAC Optimization Problem F ormulation
Combing the transmission error in Eq. (32) and the sensing
SNR in Eq. (33), the ISAC optimization problem is formulated
as follows:
P2 : minWT ,v,a
1
3
X
t=1,2,3
E∼s,ϵk
h
∥a · zk[t] − ˜uk[t]∥22
i
(34a)
s.t. SNR (dl-echo) ≥ γSNR, (34b)
∥[WT ]m,:∥22 + |vm|2 ≤ PBS, 1 ≤ m ≤ Nt, . (34c)
where [WT ]m,: represents the m-th row of the matrix WT ,
and vm denotes m-th element of the vector v. In P2, we
minimize the transmission error of Eq. (34a), as well as
maintaining the sensing SNR in Eq. (34b) larger than a
predefined threshold γSNR. Eq. (34c) is to set BS downlink
transmission power constrain, i.e., PBS for combined precoding
matrix and sensing beamforming vector .
D. SCA-based Solution to ISAC Optimization Problem
To solve the optimization problem P2, we notice that the
objective function in Eq. (34a) is non-convex with respect to
the optimization variables a, WT , and v, as seen from Eq.
(32), it contains quadratic forms as a2WHT WT and a2vH v.
Then, the constraints from Eq. (34b) draws non-convex sets
for WT and v.
We first convert the non-convex objective function by com-
bining the optimization variables, i.e.,
˜WT ≜ a · WT , (35a)
˜v ≜ a · v, (35b)
˜a ≜ a2. (35c)
The original optimization problem P2 in Eq. (34) can be
thereby rewritten by taking ˜WT , ˜vT , and ˜a back into Eqs.
(32)-(33) and Eq. (34c), i.e.,
P2−1: min˜WT ,˜v,˜a



H(dl) ˜WT −INt 


2F ∥uk∥223 +

H(dl) ˜v

22 +˜aN σ2
(36a)
s.t. ∥G ˜WT ˜uk[t]∥22 + ∥G˜v∥22 ≥ ˜aN σ2γSNR, t = 1, 2, 3
(36b)



[ ˜WT ]m,:


22 + |˜vm|2 ≤ ˜a · PBS, 1 ≤ m ≤ Nt.
(36c)
As such, the non-convexity is only from the constraint in Eq.
(36b), which draws a non-convex set for optimization variables
˜WT and ˜v.
Next, to address the non-convex optimization problem P2−1
in Eq. (36), we provide a SCA based method. To be specific,
we assume to obtain an local optimal ˜WT and ˜v at i-th
iteration, denoted as ˜W(i)T and ˜v(i). Then, the first-order
Taylor expansion based lower-bounds of ∥G ˜WT ˜uk[t]∥22 and
∥G˜v∥22 can be computed based on the points ˜W(i)T and ˜v(i).
The non-convex constrain in Eq. (36b) will be further relaxed
by making the lower-bound no less than the right-hand side.
Algorithm 2: SCA based optimization of BS downlink
precoding matrix WT , BS sensing beamforming vector
v, and UA V receiver scaling factor a.
Input: BS constructed control signal uk, channel
H(dl) = [(h(dl)S1 )T , (h(dl)S2 )T , · · ·, (h(dl)SN )T ]T ,
echoed sensing channel G, noise variance σ2,
the minimum BS sensing SNR γSNR, and BS
transmission power PBS.
1 Initialize the optimization variables ˜WT and ˜v at start,
i.e., ˜W(0)T and ˜v(0) for i = 0-th iteration, and assign
the stop condition ι;
2 while ∆ > ιdo
3 Obtain optimal ˜WT , ˜v, and ˜a by solving convex
problem P2−2 in Eq. (40);
4 Assign ˜W(i+1)T = ˜WT , and ˜v(i+1) = ˜v;
5 ∆ = ∥ ˜W(i+1)T − ˜W(i)T ∥F + ∥˜v(i+1) − ˜v(i)∥2;
6 i = i + 1;
7 end
8 Obtain WT = W(i)T /√˜a, v = v(i)/√˜a, and a = √˜a;
Output: Optimized BS downlink precoding matrix
WT , BS sensing beamforming vector v, and
actuator receiver scaling factor a.
Noticing that the both ˜WT and ˜v are complex variables, their
first-order Taylor expansions are:
∥G˜v∥22 ≥ 


G˜v(i)


22 +2ℜ hGT G∗ ˜v(i)∗iT· ˜v − ˜v(i) ,
(37)
and



G ˜WT ˜uk[t]


22 ≥ 


G ˜W(i)T ˜uk[t]


22
+2ℜ
n
vecT
h
GTG∗

˜W(i)T
∗
∥˜uk[t]∥22
i
·
h
vec

˜WT

−vec

˜W(i)T
 i o
,
(38)
where the detailed deduction is provided in Appendix B. With
the help of the linear lower-bounds of the quadratic forms in
Eqs. (37)-(38), we relax the non-convex constraint in Eq. (36b)
of problem P2−1 as:



G˜v(i)


2
2
+



G ˜W(i)T ˜uk[t]


22+ 2ℜ hGTG∗˜v(i)∗iT·˜v− ˜v(i)
+2ℜ
n
vecT
h
GTG∗

˜W(i)T
∗
∥˜uk[t]∥22
i
·
h
vec

˜WT

−vec

˜W(i)T
 i o
≥˜a · N σ2γSNR, t = 1, 2, 3
(39)
which draws affine convex sets to ˜WT , ˜v, and ˜a.
Leveraging the new convex constraint of Eq. (39), the SCA
based optimization problem is formulated as:
P2−2 : min˜WT ,˜v,˜a(36a) (40a)
s.t. (39), (36c). (40b)
which is convex and can be solved by CVX Toolbox.
The overall SCA based algorithm is provided in Algorithm
2. The inputs are the BS constructed control signal uk for
OTA transmission, the dowinlink channel matrix H(dl), the

9
echoed sensing channel matrix G, the noise variance σ2,
and the predefined minimum BS sensing SNR γSNR, and
BS transmission power limit PBS. Step 1 is to initialize the
iterative optimization variables ˜WT and ˜v as ˜W(0)T and ˜v(0)
at the start i = 0 -th iteration, and assign the stop condition
ι. Steps 2-7 are the iterative SCA procedures to obtain the
optimal ˜W(i+1)T , ˜v(i+1), and ˜a of the problem P2−2. Step 7
is to transform the optimized ˜WT , ˜v, and ˜a back to the BS
downlink precoding matrix WT , the BS sensing beamforming
vector v, and the UA V receivers’ scaling factor a, which
serve as the outputs. These optimized outputs, adopted in the
downlink process detailed in Section III-B, ensure that (i) the
each UA V can obtain their own control signals for controlling
purposes, and (ii) sufficient sensing SNR for continuous radar
sensing objective at BS.
VI. S IMULATIONS RESULTS
In this section, we evaluate our proposed ISAC-OTA con-
troller scheme. The performance contains (i) the wireless
communication based OTA controller, and (ii) the sensing
performance with interference of transmitted OTA signals. The
parameter setting is provided in Table II.
A. Metrics Comparison of OTA Controllers
In this part, we evaluate the control performance in terms
of the state controlling errors, with respect to the number of
BS antennas, and the setting of minimum sensing SNR.
1) OTA control error & time convergence: Fig. 2 shows the
errors of the actual states from the referenced states versus
time, provided by our proposed ISAC-OTA controller, the
existing UA V Tx-power allocated OTA controller [13], and
the classic LQR as benchmark [38], [39] that uses N unique
bandwidth to control N UA Vs. It is first observed that our
proposed ISAC-OTA controllers have fewer errors and faster
convergence time, as opposed to the existing UA V Tx-power
based OTA controller [13]. This is because the number of
optimization variables for the existing Tx-power-based OTA
controller is constrained by the number of each terminal user’s
Tx antennas, and is insufficient to tune the wireless channels
for OTA control purposes. To be specific, in our configuration
with N = 50 UA Vs and6 states each, Tx-power-based OTA
controller can only have 62 × 50 = 1800 precoding variables,
which is insufficient to configure the linear control operator
of size (3 × 50) × (6 × 50) = 45 , 000 that maps xk to uk.
Compared to the terminal UA V , the BS can be equipped with
more antennas for OTA control optimization, suggesting its
capability of tuning the wireless channel to better construct
and dispatch control signals.
It is observed that with Nt = Nr > N BS antennas, the
control performance of the proposed ISAC-OTA controller is
comparable to that of the benchmark LQR’s optimal control.
Notably, however, the proposed ISAC-OTA controller achieves
this using only a single frequency bandwidth, unlike the bench-
mark LQR, which requires N unique frequency allocations to
control N UA Vs.
TABLE II
SIMULATION PARAMETERS
Parameters Configurations
Number of UA Vs N = 50
Control interval [2] ∆t = 0.02s
Q in control objective IN ⊗ diag([1, 1, 1, 0.1, 0.1, 0.1])
R in control objective IN ⊗ diag([1, 1, 1])
Initial UA V xyz-positions (m) x(n)1,1 , x(n)1,2 ∈ U(0, 100), x(n)1,3 = 0
Number of antennas per UA V 1
UA V Tx power 0.1W
BS xyz-position (m) (0, 0, 5)
Number of BS antennas Nt = Nr ∈ [10, 60]
Uplink scaling factor γul = 100
BS Tx power PBS = 1W
Number of wave paths [35] L = 10
Path-loss at 1m C0 = 10−3
LoS exponential loss factor ηLoS = 2.5
NLoS exponential loss factor ηNLoS = 3
Azimuth angles of NLoS paths θnS,l, θSn,l ∼ U[−π/2, π/2), l >1
Sensing object xzy-position (m) (10, 10, 1) leads to αo = 0.7854
Echoed sensing gain β = 0.1 · C0d−ηLoSoS
Minimum BS sensing SNR γSNR ∈ [10, 70]dB
Received noise variance σ2 = −110dBW
Fig. 2. Control performance comparison among the proposed ISAC-OTA
controller, the existing Tx-power-OTA controller [13], and the original LQR
as the benchmark.
2) OTA control error versus number of antennas: From Fig.
2, we also notice that with the increase of BS antennas (e.g.,
from Nt = Nr = 30 to Nt = Nr = 60), both the errors and
the convergence time of our proposed ISAC-OTA controllers
decrease. This can be further validated via Fig. 3, which shows
a decreased mean absolute state error with respect to the
increased number of BS antennas. This is because more BS
antennas can provide more uplink and downlink optimization
variables to achieve better performances of uplink OTA control
signal construction, and downlink control signal dispatch.
3) OTA control error versus minimum sensing SNR: We
next provide the control performance of the proposed ISAC-
OTA controller with respect to the different minimum BS
sensing SNR levels set in the downlink process, i.e., γSNR. It is
seen from Fig. 4 that as the setting of γSNR increases, the mean
absolute state errors of the proposed ISAC-OTA controllers

10
10 20 30 40 50 60
Number of BS antennas, Nt = Nr
0.8
0.9
1
1.1
1.2
1.3
1.4Mean absolute state error (m)
ISAC-OTA control
Original LQR (benchmark)
Fig. 3. Mean absolute state controlling error of proposed ISAC-OTA
controller, with respect to different numbers of BS antennas.
10 20 30 40 50 60 70
Minimum BS sensing SNR .SN R (dB)
0.8
1
1.2
1.4
1.6
1.8
2
Mean absolute state error (m)
ISAC-OTA control, 10 BS antennas
ISAC-OTA control, 30 BS antennas
ISAC-OTA control, 60 BS antennas
Original LQR (benchmark)
Fig. 4. Mean absolute state controlling error of proposed ISAC-OTA
controller, with respect to different levels of minimum BS sensing SNR γSNR.
go up. This is due to the fact that both the OTA transmission
and the sensing task are integrated within the common time,
frequency, and spatial resources, rendering the conflict to
maintain both of their performances. Yet, with the help of
our ISAC optimization design in Eq. (34) and the SCA-based
solution in Algorithm 2, the control accuracy of our proposed
ISAC-OTA controller is still remarkable. For instance, when
using 60 BS antennas, the mean absolute state errors are
nearly identical to those of the classic LQR algorithm for
γSNR ≤ 50 dB. As noted in [40], a minimum sensing SNR
of γSNR = 15 dB is sufficient to guarantee successful sensing.
Our proposed ISAC-OTA controller therefore is capable of
effectively balancing both sensing and OTA control objectives.
B. BS Sensing Performance
In this part, we evaluate the BS sensing performance with
the interference from the uplink and downlink OTA transmis-
10 20 30 40 50 60
Number of BS antennas Nt = Nr
0
0.05
0.1
0.15
0.2
0.25
0.3
0.35
0.4
0.45Mean absolute sensing error (rad)
ISAC-OTA control: BS sensing (uplink interference)
Fig. 5. Mean absolute sensing error of proposed ISAC-OTA controller in the
uplink process, with respect to the number of BS antennas.
sions. Here, the sensing accuracy is measured by the mean
absolute error of the object’s angle estimated by the MUSIC
algorithm in Appendix A.
1) BS sensing with uplink interference: Fig. 5 provides
the sensing performance of the proposed ISAC-OTA scheme,
interfered by the uplink OTA transmission signals. It is seen
that with the increase of BS antennas (from 10 to 60), the
sensing error reduces (from 0.45rad to 0.05rad). Recall that
the design of uplink post-processing matrix WS for sensing
purposes (in Section IV-B) requires to find the orthogonal
(quasi-orthogonal) subspace to the uplink UA V-BS channel
matrix H(ul) of size Nr × N. Note that the rank of H(ul)
may approach to N, given the fact that the channels from N
UA Vs to BS are independent. As such, when the number of
BS antennas is less than the number of UA Vs, i.e., Nr < N,
it is less likely to approach WSH(ul) ≈ O, and therefore
leads to more uplink interference to deteriorate the sensing
accuracy (e.g., an angle error of 0.2rad with Nr = 30 < 50).
Then, when the number of BS antennas is larger than that of
UA Vs, i.e.,Nr ≥ N, an orthogonal subspace is existed for BS
to separate the sensing signal and uplink OTA transmission,
which therefore results in small sensing error (e.g., an angle
error below 0.05rad with Nr = 60 > N= 50).
2) BS sensing in downlink process: Fig. 6 illustrates the BS
sensing performance in the downlink process. Here, different
from the uplink process that the uplink UA V-BS transmission
interferes the sensing operation, in the downlink process, BS
can use both of its downlink transmission and the continuous
radar sensing signal for sensing purposes. In this view, we can
first observe an overall lower sensing error as opposed to the
sensing operation in the uplink process (e.g., 0.035 < 0.05).
Then, from Fig. 6, it is also seen that the BS sensing accuracy
in the downlink process is affected by both the number of
antennas used, and the setting of minimum BS sensing SNR
γSNR. The sensing errors of our proposed ISAC-OTA scheme
decrease when larger SNRs or more antennas are allocated.
Combining these results, we demonstrate the our proposed

11
10 20 30 40 50 60 70
Minimum BS sensing SNR .SN R (dB)
0.0366
0.03661
0.03662
0.03663
0.03664
0.03665
0.03666Mean absolute sensing error (rad)
ISAC-OTA BS downlink signal sensing: 10 antennas
ISAC-OTA BS downlink signal sensing: 30 antennas
IISAC-OTA BS downlink signal sensing: 60 antennas
Fig. 6. Mean absolute sensing error of proposed ISAC-OTA controller in
the downlink process, with respect to the different settings of minimum BS
sensing SNR γSNR.
Fig. 7. Illustration of 4 (out of 50) drones referenced paths and actual
positions (only xy-plane are shown with constant heights), controlled by our
proposed ISAC-OTA controller.
ISAC-OTA controller is capable of achieving integrated co-
ordinate UA V swarm control and the sensing tasks within the
same frequency bandwidth.
C. Overall ISAC-OTA Controller Illustration
We finally show one example of integrated UA V swarm
coordinate control and sensing objectives operated by our
proposed ISAC-OTA controller. In this example, we use 60
BS antennas, and the minimum BS sensing SNR is set as
γSNR = 20dB.
In Fig. 7, 4 out of N = 50 UA Vs are randomly selected
for the illustration of the ISAC-OTA controlling performance
to control them follow their predefined reference paths. The
results show that our proposed ISAC-OTA controller can
provide accurate control signals for the swarm of drones to
follow the referenced paths.
Fig. 8. Illustration of MUSIC algorithm estimated object angle, with the
proposed ISAC-OTA scheme generated input signals: x-coordinate is the angle
range in rad, and y-coordinate is the MUSIC output in dB.
Fig. 8 provides an illustration of the MUSIC algorithm
(Appendix A) estimated object angle, with the proposed ISAC-
OTA scheme generated input signals. Here, x-coordinate rep-
resents the angle range from [0, 2π], and y-coordinate is the
MUSIC output provided by the right-hand side of Eq. (44) in
dB. Given that the object of interest is located at (10, 10, 1)
relative to the BS at (0, 0, 5), resulting in an azimuth angle
from the BS ULA of αo = 0.7854, it is evident from Fig. 8
that the proposed ISAC-OTA scheme delivers accurate sensing
performance in both the uplink and downlink processes.
VII. C ONCLUSION
OTA controllers leverage the physical superposition of
nodes’ transmitted signals (states) on the same frequency to
generate control signals over the air, avoiding the need of
extensive spectrum resources allocated for different nodes.
However, existing Tx-power based OTA controllers, operating
at each terminal, have two drawbacks. First, the size of the
OTA control operator, determined by the product of the trans-
mitted state-space and control signal space dimensions, far
exceeds the number of optimization variables in the existing
terminal Tx-power-based OTA controller, causing severe con-
trol error and slow convergence time. Second, how to integrate
the coordinate controller role with the diverse functionalities
of BS (e.g., communication, sensing) is not studied.
In this work, the ISAC-OTA controller is proposed for UA V
swarm system, where BS is designed to facilitate OTA control
signal construction (uplink) and dispatch (downlink), as well
as maintaining the object sensing task. In uplink process, two
BS post-processing matrices are designed. The control-centric
matrix determines a closed-form control signal by solving
a feedback-looped control objective that incorporates uplink
UA V-BS channels. The sensing-centric matrix spans from
the orthogonal subspace of the uplink channels to mitigate
transmission interference, ensuring accurate sensing. For the
downlink process, we formulate a non-convex optimization
problem to minimize transmission error for control signal

12
dispatch while maintaining a minimum sensing SNR. The
optimal (or sub-optimal) BS precoding matrix and sensing
beamforming vector are determined through the design of the
SCA algorithm. The simulation results show (i) comparable
control performance of our ISAC-OTA controller with the
benchmark LQR control algorithm, without the need to al-
locate different bandwidths to each UA V , and (ii) high sensing
accuracy despite OTA transmission interference. This therefore
underscores the potential of utlizing the proposed ISAC-OTA
controller for spectrum-efficient cooperative control in future
wireless systems.
APPENDIX A
MUSIC S ENSING ALGORITHM
MUSIC algorithm is one super-resolution algorithm for
parameter estimation (e.g., angles, time of arrival) of objects
of interests, which exploits the orthogonality of signal sub-
space [41]. For this work, we rewrite BS received signals at
successive transmission time-slot as:
ξ[t] =
(
q[t], t = 1, · · ·, 6 Uplink post-process in (7b)
r(dl)k [t], t = 1, 2, 3 Downlink process in (11) .
(41)
Then, the signal subspace is constructed as:
Σ =
X
t
ξ · ξH = F · Λ · FH| {z }
signal subspace
+ F⊥ · Λ⊥ · FH⊥| {z }
noise subspace
, (42)
where Λ and F are the M largest eigenvalues and the corre-
sponding eigenvector composed matrix, and Λ⊥ and F⊥ are
the other rest eigenvalues and the corresponding eigenvector
composed matrix. In the case of single object sensing, we have
M = 1. As such, we create the spatial vector spanning from
the range of angles of the sensing object, i.e.,
a(α) =
(
WS · ψ(α, Nr) Uplink post-process,
ψ(α, Nr) Downlink process. (43)
Then the estimated object angle, denoted as ˆαo can be obtained
by finding the maximum MUSIC output as follows:
ˆαo = argmax
α∈[0,2π)
1
∥FH⊥ · a(α)∥22 . (44)
We evaluate the BS sensing performance during uplink and
downlink processes in Simulation section.
APPENDIX B
DEDUCTION OF COMPLEX 1-O RDER TAYLOR EXPANSION
We compute the complex first-order Taylor expansion of the
scalar function with the complex matrix input in Eq. (38). The
deduction process of Eq. (37) is similar.
To simplify the expression, we abbreviate ˜uk[t] at t down-
link transmission time-slots of k-th control period as ˜u. It is
seen that the variable of ˜uH ˜WHT GH G ˜WT ˜u, i.e., ˜WT , is
a complex matrix, rendering the different expression of first-
order Taylor expansion, i.e.,
˜uH ˜WHT GH G ˜WT ˜u ≥ ˜uH

˜W(i)T
H
GH G ˜W(i)T ˜u
+
 
∂ ˜uH ˜WHT GH G ˜WT ˜u
∂vec( ˜WT )
 ˜W(i)T !T · vec( ˜WT )−vec  ˜W(i)T  
+
 
∂ ˜uH ˜WHT GH G ˜WT ˜u
∂vec∗( ˜WT )
 ˜W(i)T !T · vec∗( ˜WT )−vec∗ ˜W(i)T  (45)
We then compute the two Wirtinger derivatives of Eq. (45).
By denoting f ( ˜WT ) ≜ ˜uH ˜WHT GH G ˜WT ˜u, the differential
of f ( ˜WT) : CNt×D → R is defined as [42]:
d f( ˜WT )
=
X
m,n

 ∂f ( ˜WT )
∂[ ˜WT ]m,n · d[ ˜WT ]m,n + ∂

f ( ˜WT )

∂[ ˜WT ]∗m,n · d[ ˜WT ]∗m,n


=
 
∂f ( ˜WT )
∂vec( ˜WT )
!T
dvec( ˜WT ) +
 
∂f ( ˜WT )
∂vec∗( ˜WT )
!T
dvec∗( ˜WT )
(46)
On the other hand, the differential can be computed as:
d f( ˜WT )
=˜uH · d ˜WHT · GH G ˜WT ˜u + ˜uH ˜WHT GH G · d ˜WT · ˜u
=tr

d ˜WHT · GH G ˜WT ˜u˜uH

+ tr

˜u˜uH ˜WHT GH G · d ˜WT

=tr

GH G ˜WT ˜u˜uH
T
d ˜W∗T

+tr

GT G∗ ˜W∗T ˜u∗ ˜uT
T
d ˜WT

=vecT

GH G ˜WT ˜u˜uH

· dvec∗( ˜WT )
+ vecT

GT G∗ ˜W∗T ˜u∗ ˜uT

· dvec( ˜WT )
(47)
As such, by matching Eqs. (46)-(47), the two Wirtinger
derivatives in the first-order Taylor expansion of Eq. (45) are
derived, i.e.,
∂ ˜uH ˜WHT GH G ˜WT ˜u
∂vec( ˜WT ) = vec

GT G∗ ˜W∗T ˜u∗ ˜uT

, (48)
∂ ˜uH ˜WHT GH G ˜WT ˜u
∂vec∗( ˜WT ) = vec

GH G ˜WT ˜u˜uH

. (49)
In this view, Eq. (45) can be further expressed as:
˜uH ˜WHT GH G ˜WT ˜u ≥ ˜uH

˜W(i)T
H
GH G ˜W(i)T ˜u
+vecT

GH G ˜WT ˜u˜uH

·
h
vec∗( ˜WT ) − vec∗

˜W(i)T
i
+vecT

GT G∗ ˜W∗T ˜u∗ ˜uT

·
h
vec( ˜WT ) − vec

˜W(i)T
i
,
(50)
which is equivalent to Eq. (38) given the fact that the last two
terms are conjugate with each other.
REFERENCES
[1] P. Park, S. Coleri Ergen, C. Fischione, C. Lu, and K. H. Johansson,
“Wireless network design for control systems: A survey,” IEEE Com-
mun. Surveys Tuts. , vol. 20, no. 2, pp. 978–1013, 2018.

13
[2] Z. Wei and W. Guo, “Control layer security: Exploiting unobservable
cooperative states of autonomous systems for secret key generation,”
IEEE Trans. Mobile Comput. , vol. 23, no. 10, pp. 9989–10 000, 2024.
[3] D. Jia and D. Ngoduy, “Platoon based cooperative driving model with
consideration of realistic inter-vehicle communication,” Transp. Res. C:
Emerg. Technol., vol. 68, pp. 245–264, 2016.
[4] J. Lunze, Control theory of digitally networked dynamic systems . vol.1.
Berlin, Germany: Springer, 2014.
[5] X. Liu, B. Lai, B. Lin, and V . C. M. Leung, “Joint communication
and trajectory optimization for multi-uav enabled mobile internet of
vehicles,” IEEE Transactions on Intelligent Transportation Systems ,
vol. 23, no. 9, pp. 15 354–15 366, 2022.
[6] K. Yang, T. Jiang, Y . Shi, and Z. Ding, “Federated learning via over-
the-air computation,” IEEE Transactions on Wireless Communications ,
vol. 19, no. 3, pp. 2022–2035, 2020.
[7] T. Sery, N. Shlezinger, K. Cohen, and Y . C. Eldar, “Over-the-air
federated learning from heterogeneous data,” IEEE Transactions on
Signal Processing, vol. 69, pp. 3796–3811, 2021.
[8] M. Kim, A. L. Swindlehurst, and D. Park, “Beamforming vector
design and device selection in over-the-air federated learning,” IEEE
Transactions on Wireless Communications , 2023.
[9] K.-C. Hsu, M.-C. Lee, and Y .-W. P. Hong, “Joint trajectory and commu-
nication optimization for uav-assisted over-the-air federated learning,”
in 2023 IEEE International Conference on Communications Workshops
(ICC Workshops), 2023, pp. 1666–1671.
[10] P. Sun, E. Liu, W. Ni, R. Wang, Z. Xing, B. Li, and A. Jamalipour,
“Reconfigurable intelligent surface-assisted wireless federated learning
with imperfect aggregation,” IEEE Trans. Commun. , pp. 1–1, 2024.
[11] J. Zheng, H. Tian, W. Ni, W. Ni, and P. Zhang, “Balancing accuracy
and integrity for reconfigurable intelligent surface-aided over-the-air
federated learning,” IEEE Transactions on Wireless Communications ,
vol. 21, no. 12, pp. 10 964–10 980, 2022.
[12] M. Ahmadzadeh, S. Pakravan, G. A. Hodtani, M. Zeng, and J.-Y .
Chouinard, “Enhancement of over-the-air federated learning by using
ai-based fluid antenna system,” arXiv preprint arXiv:2407.03481 , 2024.
[13] P. Park, P. D. Marco, and C. Fischione, “Optimized over-the-air compu-
tation for wireless control systems,” IEEE Commun. Lett. , vol. 26, no. 2,
pp. 424–428, 2022.
[14] P. Park, P. Di Marco, and C. Fischione, “Wireless for control: Over-the-
air controller,” IEEE Commun. Lett. , vol. 25, no. 10, pp. 3437–3441,
2021.
[15] C.-X. Wang, X. You, X. Gao, X. Zhu, Z. Li, C. Zhang, H. Wang,
Y . Huang, Y . Chen, H. Haas, J. S. Thompson, E. G. Larsson, M. D.
Renzo, W. Tong, P. Zhu, X. Shen, H. V . Poor, and L. Hanzo, “On the
road to 6g: Visions, requirements, key technologies, and testbeds,” IEEE
Communications Surveys & Tutorials , vol. 25, no. 2, pp. 905–974, 2023.
[16] F. Liu, Y . Cui, C. Masouros, J. Xu, T. X. Han, Y . C. Eldar, and S. Buzzi,
“Integrated sensing and communications: Toward dual-functional wire-
less networks for 6g and beyond,” IEEE Journal on Selected Areas in
Communications, vol. 40, no. 6, pp. 1728–1767, 2022.
[17] J. Wang, N. Varshney, C. Gentile, S. Blandino, J. Chuang, and
N. Golmie, “Integrated sensing and communication: Enabling tech-
niques, applications, tools and data sets, standardization, and future
directions,” IEEE Internet of Things Journal , vol. 9, no. 23, pp. 23 416–
23 440, 2022.
[18] A. Liu, Z. Huang, M. Li, Y . Wan, W. Li, T. X. Han, C. Liu, R. Du,
D. K. P. Tan, J. Lu, Y . Shen, F. Colone, and K. Chetty, “A survey
on fundamental limits of integrated sensing and communication,” IEEE
Communications Surveys & Tutorials , vol. 24, no. 2, pp. 994–1034,
2022.
[19] N. Cao, Y . Chen, X. Gu, and W. Feng, “Joint bi-static radar and com-
munications designs for intelligent transportation,” IEEE Transactions
on V ehicular Technology, vol. 69, no. 11, pp. 13 060–13 071, 2020.
[20] T. T. Nguyen, K. Elbassioni, N. C. Luong, D. Niyato, and D. I.
Kim, “Access management in joint sensing and communication systems:
Efficiency versus fairness,” IEEE Transactions on V ehicular Technology,
vol. 71, no. 5, pp. 5128–5142, 2022.
[21] W. Zhou, R. Zhang, G. Chen, and W. Wu, “Integrated sensing and
communication waveform design: A survey,” IEEE Open Journal of the
Communications Society , vol. 3, pp. 1930–1949, 2022.
[22] X. Chen, Z. Feng, Z. Wei, P. Zhang, and X. Yuan, “Code-division
ofdm joint communication and sensing system for 6g machine-type
communication,” IEEE Internet of Things Journal , vol. 8, no. 15, pp.
12 093–12 105, 2021.
[23] J. Du, Y . Tang, X. Wei, J. Xiong, J. Zhu, H. Yin, C. Zhang, and
H. Chen, “An overview of resource allocation in integrated sensing
and communication,” in 2023 IEEE/CIC International Conference on
Communications in China (ICCC Workshops) , 2023, pp. 1–6.
[24] Z. Wang, X. Mu, and Y . Liu, “Near-field integrated sensing and
communications,” IEEE Communications Letters , vol. 27, no. 8, pp.
2048–2052, 2023.
[25] Z. Wei, H. Qu, Y . Wang, X. Yuan, H. Wu, Y . Du, K. Han, N. Zhang,
and Z. Feng, “Integrated sensing and communication signals toward 5g-
a and 6g: A survey,” IEEE Internet of Things Journal , vol. 10, no. 13,
pp. 11 068–11 092, 2023.
[26] J. Liu, Y . Chen, Y . Wang, X. Chen, J. Cheng, and J. Yang, “Monitoring
vital signs and postures during sleep using wifi signals,” IEEE Internet
of Things Journal , vol. 5, no. 3, pp. 2071–2084, 2018.
[27] X. Cheng, D. Duan, S. Gao, and L. Yang, “Integrated sensing and
communications (isac) for vehicular communication networks (vcn),”
IEEE Internet of Things Journal , vol. 9, no. 23, pp. 23 441–23 451,
2022.
[28] X. Jing, F. Liu, C. Masouros, and Y . Zeng, “Isac from the sky: Uav
trajectory design for joint communication and target localization,” IEEE
Transactions on Wireless Communications , pp. 1–1, 2024.
[29] S. K. Rao and R. Prasad, “Impact of 5g technologies on industry
4.0,” Wirel. Pers. Commun. , vol. 100, no. 1, p. 145–159, May 2018.
[Online]. Available: https://doi.org/10.1007/s11277-018-5615-7
[30] X. Li, Y . Gong, K. Huang, and Z. Niu, “Over-the-air integrated sens-
ing, communication, and computation in iot networks,” IEEE Wireless
Communications, vol. 30, no. 1, pp. 32–38, 2023.
[31] X. Li, F. Liu, Z. Zhou, G. Zhu, S. Wang, K. Huang, and Y . Gong,
“Integrated sensing and over-the-air computation: Dual-functional mimo
beamforming design,” in 2022 1st International Conference on 6G
Networking (6GNet) , 2022, pp. 1–8.
[32] M. Du, H. Zheng, M. Gao, X. Feng, J. Hu, and Y . Chen, “Integrated
sensing, communication and computation for over-the-air federated
learning in 6g wireless networks,” IEEE Internet of Things Journal ,
pp. 1–1, 2024.
[33] Z. Tahir, W. Tahir, and S. A. Liaqat, “State space system modelling of
a quad copter uav,” arXiv preprint arXiv:1908.07401 , 2019.
[34] T. Luukkonen, “Modelling and control of quadcopter,” ” Independent
Res. Project Appl. Math. , vol. 22, no. 22, pp. 2–6, 2011.
[35] E. Bj ¨ornson and L. Sanguinetti, “Rayleigh Fading Modeling and Chan-
nel Hardening for Reconfigurable Intelligent Surfaces,” IEEE Wireless
Commun. Lett. , vol. 10, no. 4, pp. 830–834, 2021.
[36] B. Tang and J. Li, “Spectrally constrained mimo radar waveform design
based on mutual information,” IEEE Transactions on Signal Processing ,
vol. 67, no. 3, pp. 821–834, 2019.
[37] Z. Wang, Y . Zhou, Y . Shi, and W. Zhuang, “Interference management
for over-the-air federated learning in multi-cell wireless networks,” IEEE
Journal on Selected Areas in Communications , vol. 40, no. 8, pp. 2361–
2377, 2022.
[38] G. C. Goodwin, S. F. Graebe, M. E. Salgado et al. , Control system
design. vol.240. Prentice Hall Upper Saddle River, 2001.
[39] F. L. Lewis, D. Vrabie, and V . L. Syrmos, Optimal control. John Wiley
& Sons, 2012.
[40] Z. He, W. Xu, H. Shen, D. W. K. Ng, Y . C. Eldar, and X. You,
“Full-duplex communication for isac: Joint beamforming and power
optimization,” IEEE Journal on Selected Areas in Communications ,
vol. 41, no. 9, pp. 2920–2936, 2023.
[41] A. H. Sayed and T. Kailath, “A survey of spectral factorization methods,”
Numerical linear algebra with applications , vol. 8, no. 6-7, pp. 467–496,
2001.
[42] R. Hunger, “An introduction to complex differentials and complex dif-
ferentiability,” URL https://mediatum. ub. tum. de/doc/631019/631019.
pdf, 2007.