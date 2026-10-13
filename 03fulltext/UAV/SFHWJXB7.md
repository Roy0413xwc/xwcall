---
title: "Near-Field Integrated Sensing and Communications for Secure UAV Networks"
zotero_key: "SFHWJXB7"
pdf_key: "UGBKAK29"
doi: "10.1109/JSAC.2025.3608737"
collection: "UAV"
source: "Zotero imported PDF (pypdf extraction)"
page_mapping: "unknown"
source_sha256: "73e7eccdba4b28449dcef31ecd4b82454a07928b412769b798a95dc3488c5e59"
pdf_pages: 14
---

# Near-Field Integrated Sensing and Communications for Secure UAV Networks — Fulltext

> 由 Zotero 附件 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证。

---


<!-- extraction_page_index: 1 -->

1
Near-Field Integrated Sensing and Communications
for Secure UA V Networks
Jingjing Zhao, Songtao Xue, Kaiquan Cai, Xidong Mu, Yuanwei Liu, Fellow, IEEE, and Yanbo Zhu
Abstract—A novel near-field integrated sensing and communi-
cations framework for secure unmanned aerial vehicle (UA V)
networks with high time efficiency is proposed. A ground
base station (GBS) with large aperture size communicates with
one communication UA V (C-UA V) under the existence of one
eavesdropping UA V (E-UA V), where the artificial noise (AN) is
employed for both jamming and sensing purpose. Given that
the E-UA V’s motion model is unknown at the GBS, we first
propose a near-field localization and trajectory tracking scheme.
Specifically, exploiting the variant Doppler shift observations
over the spatial domain in the near field, the E-UA V’s three-
dimensional (3D) velocities are estimated from echo signals. To
provide the timely correction of location prediction errors, the
extended Kalman filter (EKF) is adopted to fuse the predicted
states and the measured ones. Subsequently, based on the real-
time predicated location of the E-UA V , we further propose a
joint GBS beamforming and C-UA V trajectory design scheme for
maximizing the instantaneous secrecy rate, while guaranteeing
the sensing accuracy constraint. To solve the resultant non-convex
problem, an alternating optimization approach is developed,
where the near-field GBS beamforming and the C-UA V trajectory
design subproblems are iteratively solved by exploiting the succes-
sive convex approximation method. Finally, our numerical results
unveil that: 1) the E-UA V’s 3D velocities and location can be
accurately estimated in real time with our proposed framework
by exploiting the near-field spherical wave propagation; and 2)
the proposed framework achieves superior secrecy rate compared
to benchmark schemes and closely approaches the performance
when the E-UA V trajectory is perfectly known.
Index Terms—Integrated sensing and communications (ISAC),
secure communications, near field, unmanned aerial vehicle
(UA V), 3D velocities sensing
I. I NTRODUCTION
With the fast development of the low-altitude economy,
unmanned aerial vehicles (UA Vs) have received significant
attention for potential usage in military, civilian, and com-
mercial applications [1]. Particularly, benefiting from the high
mobility and the low operation cost, UA Vs are anticipated
to play significant roles in future wireless networks [2]. In
contrast to the terrestrial communications, the ground-to-air
communications have higher probability to be dominated by
the line-of-sight (LoS) links [3], [4], which is beneficial for
improving the communication quality. Moreover, the UA V’s
locations can be flexibly adjusted to adapt to the time-varying
J. Zhao, S. Xue, K. Cai, and Y . Zhu are with the School of Electronics and
Information Engineering, Beihang University, Beijing, China, and also with
the State Key Laboratory of CNS/ATM, Beijing, China. (e-mail:{jingjingzhao,
xuesongtao, caikq, zhuyanbo }@buaa.edu.cn).
X. Mu is with the Centre for Wireless Innovation (CWI), Queen’s University
Belfast, Belfast, BT3 9DT, U.K. (e-mail: x.mu@qub.ac.uk).
Y . Liu is with the Department of Electrical and Electronic Engineering, the
University of Hong Kong, Hong Kong, China (e-mail: yuanwei@hku.hk).
communications environment, which helps to construct prefer-
able channel conditions in real time.
Despite the above advantages, one prominent challenge for
facilitating UA V communications is the potential eavesdrop-
ping risk posed by the inherent broadcast nature of the LoS-
dominated channels [5]. As such, it is critical to develop
physical layer security (PLS) technologies to provide flexi-
ble security services for safeguarding UA V communications.
Thanks to the capability of the multiple-input multiple-output
(MIMO) technique for steering the signals toward the desired
directions, the secrecy rate at the receivers can be enhanced
via effective beamforming [6], [7]. However, since the eaves-
droppers are usually non-cooperative nodes, it is impractical
to obtain the wiretap channel state information (CSI) with the
conventional pilot-based estimation approach [8]. In addition,
due to the high mobility of the UA V , the CSI tracking is a
tough task to guarantee stable communication performance
while meeting the strict latency requirement. Recently, the
concept of sensing-aided communication, which leverages the
integrated sensing and communications (ISAC) techniques [9],
[10], has emerged for obtaining the communication/wiretap
CSI and thereby assisting the subsequent beamforming de-
sign [11], [12]. This approach eliminates the requirement for
transmitting pilot signals, and instead estimating the CSI based
on the distance and direction parameters obtained from echo
signals reflected by legitimate users/eavesdroppers [13].
With the increment of the array aperture size and the carrier
frequencies, the Rayleigh distance in the next-generation com-
munications system can span up to several tens to hundreds of
meters [14], [15]. Therefore, the UA Vs that move in the low-
altitude space are more likely to communicate with the ground
base station (GBS) in the near-field region. Unlike the planar
wave approximation in the far-field channel model, the more
complex spherical wave front brings in new opportunities for
the sensing and secure communication design. As a result, the
sensing-aided secure UA V communications in the near field
deserves further investigation.
A. Related Works
1) Secure UAV Communications: Extensive research works
have been devoted to secure UA V communications. In [16],
the UA V navigation problem was investigated for securing the
ground-to-air communications in the presence of collaborative
eavesdroppers. The authors of [17] investigated the average
secrecy rate maximization problem via jointly optimizing
the robust trajectory and the UA V transmit power, assuming
imperfect knowledge of the eavesdropper locations. In [18],
arXiv:2502.01003v2  [eess.SP]  15 Aug 2025

<!-- extraction_page_index: 2 -->

2
the PLS of UA V relaying communication system was studied,
where the UA V forwarded the information from the GBS to the
ground nodes in the presence of an eavesdropper. The authors
of [19] discussed the security and reliability performance of a
ground communication system, where a UA V was deployed to
send jamming signals to protect against an eavesdropper. Con-
sidering the multi-UA Vs scenario with multiple eavesdroppers,
the authors of [20] leveraged the cooperation among UA Vs for
simultaneously sending information signals to the legitimate
nodes and jamming signals to the eavesdroppers. In [21], the
reconfigurable intelligent surface (RIS) was applied to enhance
the average secrecy rate of the UA V communications under the
assumption of the imperfect wiretap CSI. Furthermore, the
joint UA V transmit power, trajectory, and RIS beamforming
were jointly optimized in [22], with the aim of maximizing
the average secrecy rate in the RIS-aided multi-UA V commu-
nications scenario. The aforementioned works all assumed that
the eavesdroppers were static and the wiretap CSI was fully
or at least partially known, while the wiretap CSI is not easy
to be obtained in practice as the eavesdropper is normally a
non-cooperative node.
2) Sensing-Aided Communications: To reap the benefits of
the ISAC technique, the sensing-aided communications have
attracted some research contributions recently, especially in the
far-field scenario. For instance, the authors of [23] proposed
to jointly design the transmit beamformers of communication
and radar systems to minimize the maximum eavesdropping
signal-to-interference-plus-noise ratio (SINR). In [24], the
authors proposed a beamforming optimization method for
downlink secure ISAC systems, where the communication
secrecy and target sensing performance were well balanced
under imperfect eavesdropper CSI. To further enhance the
communications security, the authors of [25] employed a com-
bined Capon and approximate maximum likelihood (CAML)
technique to search for the potential eavesdroppers’ directions
and formulated a weighted optimization problem to enhance
the secrecy rate while minimizing the eavesdroppers’ Cram ´er-
Rao Bound (CRB). In addition, the sensing-assisted predictive
beamforming has been investigated for high-dynamic scenar-
ios [26], [27]. The authors of [26] proposed a sensing-aided
beamforming prediction algorithm based on the extended
Kalman filter (EKF), where the ISAC echo signals reflected
by vehicles were employed to predict the CSI for time-varying
channels. Furthermore, the authors of [27] developed a two-
stage beamforming scheme, where the CSI was estimated
from echo signals and predicted via a neural network, which
was followed by the joint active and passive beamforming.
In [28], an ISAC framework was proposed for safeguarding the
UA V communications against a mobile eavesdropper, where
the artificial noise (AN) was used for estimating the wiretap
channel so as to assist the online UA V navigation and resource
allocation design.
Recently, some works have also started to explore the near-
field target sensing to assist the reliable communications.
For example, the authors of [29] investigated the maximum
likelihood (ML) approach to enhance the near-field localiza-
tion performance in the presence of noise. To ensure reliable
communication performance, the authors of [30] investigated
the beam training and tracking schemes for the extremely
large-scale MIMO systems with partially-connected combiner
structures, where the kinematic model was adopted to charac-
terize the near-field channel variations. In [31], the authors
proposed a near-field beamforming optimization algorithm
that utilized environmental sensing information to minimize
BS transmit power while realizing precise multi-target de-
tection. Considering high-dynamic scenarios on the ground,
the authors of [32] proposed a motion tracking method that
leveraged the characteristics of spherical waves to sense the
two-dimensional (2D) velocity of the target, for assisting the
predictive beamforming.
B. Motivations and Contributions
The existing works on sensing-aided UA V secure commu-
nications only focus on the far-field region, while there is
a paucity of investigations on the near field. Compared to
the far field, the shift on near-field propagation characteristics
introduces new opportunities for the time-sensitive secure UA V
communications design as follows.
• For sensing, the variant Doppler observations over differ-
ent antennas opens up the possibility for simultaneously
estimating the three-dimensional (3D) velocities of the
mobile eavesdropper, which facilitates the eavesdropper
location prediction without the prior knowledge of the
motion model. This is of vital importance for UA V secure
communications to localize high-mobility eavesdropping
UA Vs.
• For communications, near-field propagation enables the
unique beamfocusing capability, i.e., targeting the signal
on a specific location in the near field instead of a
specific direction in the far field. This provides enhanced
flexibility to prevent legitimate information leakage and
thus improve anti-eavesdropping performance, which is
beneficial for secure UA V communications.
Despite the above attractive benefits, the spherical wave-
based near-field propagation causes the sensing and com-
munications design quite complicated. The sensing and anti-
eavesdropping beamforming schemes have to be re-designed
to unlock the great potential of near field for secure UA V
communications. To the best of the authors’ knowledge, the
design of near-field secure UA V communications with the aid
of 3D sensing technologies has not been well studied yet,
which motivates us to contribute this work.
Against the above background, this paper investigates
the near-field sensing-assisted secure UA V communications
framework, to guarantee PLS for the communication link from
the ground base station (GBS) to a communication UA V (C-
UA V) in the presence of an eavesdropping UA V (E-UA V).
Benefiting from the ISAC technique, the C-UA V trajectory and
the GBS beamforming are designed online with low latency
based on the sensing results obtained with the echo signals.
For the sake of brevity, the main contributions of this paper
are summarized as follows.
• We consider the secure UA V communication scenario,
where the GBS transmits information signals toward the
C-UA V and also sends artificial noise (AN) signal toward
the E-UA V for both sensing and jamming purpose. To

<!-- extraction_page_index: 3 -->

3
realize the online PLS design without the prior knowledge
of the E-UA Vs’s motion model, we propose a sensing-
aided secure communication framework, which consists
of two schemes, namely the E-UAV trajectory tracking
scheme and the joint GBS beamforming and C-UAV
trajectory design scheme .
• For the E-UA V trajectory tracking, we first propose
a ML method to estimate the E-UA V’s 3D velocities
by exploiting the spatial variation of Doppler shifts in
the near field. Furthermore, we employ the EKF-based
method to fuse the location predicted with the sensed
3D velocities and that estimated with the echoes, for
improving the E-UA V trajectory tracking accuracy.
• For the joint GBS beamforming and C-UA V trajectory
design, we formulate an instantaneous secrecy rate maxi-
mization problem with the constraint on the GBS transmit
power and the E-UA V tracking accuracy. To solve the
resultant non-convex problem, an alternating optimization
(AO) algorithm is developed to decouple the optimization
variables, where the GBS beamforming and the C-UA V
trajectory design subproblems are alternately solved by
employing the successive convex approximation (SCA)
method.
• Our numerical results unveil that 1) the proposed E-
UA V trajectory tracking scheme achieves high-accuracy
localization of the E-UA V’s flight route in real time; and
2) the achievable secrecy rate of the proposed sensing-
aided secure UA V communications framework closely
approaches to that of the case where the E-UA V trajectory
is perfectly known.
C. Organization and Notations
The remainder of this paper is organized as follows. Section
II introduces the near-field sensing-aided secure UA V com-
munication system model. Section III proposes the E-UA V
3D trajectory tracking scheme, which is followed by the AO-
based joint GBS beamforming and C-UA V trajectory design
in Section IV . Section V presents the simulation results, and
Section V concludes the paper.
Notations: Vectors and matrices are denoted by boldface
lowercase and boldface capital letters, respectively. CM ×N
denotes the space of all M × N matrices with complex
entries. A∗, AT and AH denote the conjugate, transpose,
and conjugate transpose of the matrix A, respectively. Ai,j
returns the entry in the i-th row and j-th column of matrix A.
tr(A) and rank(A) denote the trace and the rank of matrix
A. ⊙ is the Hadamard product. ∥ · ∥denotes the norm of
the vector. ∥ · ∥F denotes the Frobenius norm of a matrix.
CN (u, v) denotes a Gaussian distribution with mean m and
variance v. | · |denotes the absolute value of a complex scalar.
IM denotes the M ×M identity matrix. 0M denotes the M ×M
zero matrix. [x]+ stands for max{x, 0}.
II. S YSTEM MODEL AND PROBLEM FORMULATION
As shown in Fig. 1, we consider a near-field 1 UA V commu-
nication system that consists of one ISAC GBS, one C-UA V
1We assume that both the C-UA V and E-UA V are in the near-field region
during the whole flight.
receiving signals from the GBS, and one E-UA V wiretapping
the GBS information. Thanks to few scatterers in the air-
to-ground communication environment, we assume the LoS-
dominant case for channels from the GBS to the C-UA V and
the E-UA V [17], [22]. The GBS is deployed with a rectangular
uniform planar array (UPA) that consists of M = Mx × My
antennas with the spacing d, while the C-UA V and the E-
UA V are both equipped with a single antenna. The index of
the m-th GBS antenna is given by m = aMy + b, where
a = 0 , . . . , Mx − 1 and b = 1 , . . . , My. We assume that
the GBS operates in the full-duplex mode, which allows it
to transmit and receive signals simultaneously. With the aid
of advanced self-interference mitigation techniques [33], we
assume that the full-duplex GBS can realize perfect self-
interference mitigation. The bandwidth of the system, denoted
by B, is related to the symbol duration Ts = 1B . Let N
denote the number of symbol durations in a single coherent
processing interval (CPI) with the duration of ∆t for the near-
field sensing, during which the UA Vs’ location and velocity
are assumed to be unchanged. We set a Cartesian coordinate
system for which the origin is chosen as the center of the
GBS UPA and the x and y axes are aligned with the column
and row of the UPA, respectively, while the z axis points up
to complete a right handed coordinate frame. As such, the
coordinate of the UPA center is given by qb = [0, 0, 0]T , while
that of the m-th antenna is denoted by qm = [ xm, ym, 0]T .
In the l ∈ {1, ..., L}-th CPI, the position and the velocity
of the E-UA V are denoted by qe,l = [ xel , yel , zel ]T and
ve,l = [ vxe,l, vye,l, vze,l]T , respectively, and the position of the
C-UA V is represented by qc,l = [xcl , ycl , zcl ]T . Given that the
E-UA V trajectory is unknown at the GBS, the GBS sends
artificial noise (AN) signals to the E-UA V for both sensing
and jamming purpose. Then, the transmitted signal xl(n) of
the GBS in the time slot n of the l-th CPI is given by
xl(n) = wcl sl(n) + wel al(n), (1)
where sl(n) ∼ CN(0, 1) and al(n) ∼ CN(0, 1) represent the
information and AN signals, respectively, and wcl ∈ CM ×1
and wel ∈ CM ×1 denote the precoding vectors for the
information and AN signals in the l-th CPI, respectively. Note
that, considering the tradeoff between the system performance
and the computational complexity, the same beamformers are
utilized within each CPI.
A. Near-Field Sensing Signal Model
In practice, the signal transmitted by the GBS is partially
received by the E-UA V and partially reflected back to the
GBS. Note that the signals reflected by the C-UA V and other
scatterers in the environment are assumed to be effectively
suppressed at the GBS by exploiting existing clutter suppres-
sion techniques [34]. In the n-th time slot of the l-th CPI, the
echo signal received by the m-th GBS antenna is given by
ybl,m(n) =
MX
i=1
β
(rel )2 e−j 2πλ (rel,m(nTs)+rel,i(nTs))xl,i(n)
+ zbl,m(n), (2)

<!-- extraction_page_index: 4 -->

4
Fig. 1: Illustration of the near-field UA V communication scenario
with the presence of an eavesdropper.
where rel,m(t) = ¯ rel,m + vel,mt represents the time-variant
distance from the m-th antenna to the E-UA V ,¯rel,m denotes the
distance from the m-th antenna to the E-UA V at the beginning
of the l-th CPI, vel,m denotes the E-UA V’s radial velocity
component w.r.t. the m-th antenna in the l-th CPI. Note here
that, although we assume the E-UA V’s location is constant
within one CPI for large-scale fading parameters discussions,
such as the channel gain, we take the time-variant delay into
consideration in one CPI for facilitating the Doppler estimation
as discussed later. Still referring to (2), β is a constant factor
given by β = β0
p σRCS
4π , with β0 and σRCS representing
the channel gain at the reference distance of 1 m and the
radar cross-section of the E-UA V , respectively. Furthermore,
xl,i(n) = wcl,isl(n) +wel,ial(n) denotes the transmitted signal
of the i-th antenna, wcl,i and wel,i represent the i-th element of
wcl and wel , respectively, and zbl,m(n) ∼ CN 0, σ2b  denotes
the additive white Gaussian noise (AWGN) at then-th antenna.
Denote the array response vector at the GBS for the E-UA V
at the beginning of the l-th CPI as α(rel , θel , ϕel ), where rel , θel
and ϕel represent the distance, azimuthal angle, and elevation
angle between the E-UA V and the GBS UPA center in thel-th
CPI, respectively. Specifically, α(rel , θel , ϕel ) is given by
α(rel ,θel , ϕel ) = he−j 2πλ ¯rel,1 , ..., e−j 2πλ ¯rel,M iT . (3)
Based on the geometric relationship, the expression of ¯rel,m
with respect to (w.r.t.) rel , θel and ϕel is given in (4), where
Sθel = sin θel , Cθel = cos θel and Cϕel = cos ϕel . Further, denote
the Doppler frequency shift over the m-th antenna in the l-th
CPI by f Dl,m. Then, we define the time-variant phase-Doppler
vector as dl,n
 
f Dl , with f Dl = hf Dl,1, ..., fDl,M i, in the n-th
time slot of the l-th CPI as
dl,n
 
f Dl  = he−j2πf Dl,1nTs , . . . , e−j2πf Dl,M nTs iT . (5)
Based on (2)-(5), the received echo signals over all the GBS
antennas in the n-th time slot of the l-th CPI, i.e., ybl (n) =h
ybl,1 (n) , . . . , ybl,M (n)iT ∈ CM ×1, can be expressed as
ybl (n) = β(rel )2 A (rel , θel , ϕel ) ⊙ Dl,n  f Dl  xl(n) + zbl (n),
(6)
where A (rel , θel , ϕel ) = α (rel , θel , ϕel ) × αT (rel , θel , ϕel ),
Dl,n
 
f Dl  = dl,n  f Dl  × dTl,n  f Dl , xl(n) =
[xl,1(n), · · ·, xl,m(n)]T ∈ CM ×1, and zbl (n) =
[zbl,1(n), · · ·, zbl,m(n)]T ∈ CM ×1, respectively.
Remark 1. Different from the far-field scenario, due to the
different azimuth and elevation angles observed at each GBS
antenna, the Doppler frequency shift varies in the spatial
domain for the near-field propagation.
B. Near-Field Communication Signal Model
The received signal at the C-UA V in time slot n of the l-th
CPI is given by
ycl (n) =  hbcl H xl(n) + zcl (n), (7)
where hbcl and zcl (n) ∼ CN  0, σ2c  denote the channel
between the GBS and the C-UA V , and the AWGN at the C-
UA V , respectively. Specifically,hbcl is expressed as
hbcl = β0rcl α(rcl , θcl , ϕcl ), (8)
where rcl , θcl , ϕcl represent the distance, azimuthal angle, and
elevation angle between the C-UA V and the GBS UPA center
in the l-th CPI, respectively. We assume that the C-UA V CSI,
i.e., hbcl , is known at the GBS by employing the near-field
channel estimation methods [35]. Accordingly, the achievable
data rate at the C-UA V in the l-th CPI is given by
Rcl = log2

1 +
 hbcl H wcl 2
 hbcl H wel 2 + σ2c

. (9)
Similarly, the leakage information rate at the E-UA V in the
l-th CPI is given by
Rel = log2

1 +
 hbel H wcl 2
 hbel H wel 2 + σ2e

 , (10)
where hbel and σ2e denote the channel between the GBS and
the E-UA V , and the AWGN power at the E-UA V , respectively.
Specifically, hbel is expressed as
hbel = β0rel α(rel , θel , ϕel ). (11)
Based on (9) and (10), the secrecy rate in the l-th CPI can be
expressed as follows:
Rsl = [Rcl − Rel ]+ . (12)
The secrecy rate given in (12) highly depends on the
real-time channel (location) of the E-UA V , as shown in (3).
However, the E-UA V’s location is generally unknown at the
GBS as it is a non-cooperative node. As such, we first propose
an E-UA V trajectory tracking scheme in Section III. Then, with
the aim of maximizing the secrecy rate, we advocate a joint
GBS beamforming and C-UA V trajectory design scheme in
Section IV , which is based on the estimated E-UA V’s real-
time locations in Section III.

<!-- extraction_page_index: 5 -->

5
¯rel,m =
r
(rel )2 +  a − Mx−12 2 d2 + b − My+12 2 d2 − 2rel  a − Mx−12  dSθel Cϕel − 2rel b − My+12  dCθel Cϕel . (4)
III. E-UAV 3D T RAJECTORY TRACKING SCHEME
In this section, we propose a near-field E-UA V’s 3D ve-
locities sensing and trajectory tracking scheme. Specifically, a
ML-based 3D velocities sensing approach is first proposed,
which exploits the variant Doppler shift observations over
different antennas. Then, an EKF-based state tracking method
is proposed to fuse the predicted states and the estimated ones
of the E-UA V for improving the tracking accuracy.
A. 3D Velocities Sensing and Localization
Based on the echo signal model in (6), the unknown
parameters {rel , θel , ϕel } can be estimated by the matched-
filtering principle as follows [36]:
n
ˆrel , ˆθel , ˆϕel
o
= arg max
rel ,θel ,ϕel
1
N
NX
n=1
αH (rel , θel , ϕel ) ybl (n)a∗l (n), (13)
where ˆrel , ˆθel , and ˆϕel denote the estimated distance, azimuth
angle, and elevation angle from the GBS to the E-UA V ,
respectively. Note that we assume the AN and the information
signals are uncorrelated i.e., 1N PNn=1 sl(n)a∗l (n) ≈ 0.
To capture the complete motion of the E-UA V , the
real-time velocity sensing is essential. Aggregating
ybl (n) , n ∈ { 1, ..., N} into the matrix form as
Ybl = ybl (1) , ybl (2) , . . . ,ybl (N ), we can obtain
Ybl = βXl  f Dl  + Zbl , (14)
where Xl
 
f Dl  = [ Gl(1)xl(1), . . . ,Gl(N )xl(N )], Gl(n) =
A(rel , θel , ϕel ) ⊙ Dl,n(f Dl ), and Zbl = [zl(1), zl(2), . . . ,zl(N )].
As shown in Fig. 2, to facilitate the 3D velocities derivation,
we denote the E-UA V’s velocity in the spherical coordinate
system that is centered at the GBS UPA center, as ˜ve,l =h
vre,l, vθe,l, vϕe,l
i
, where vre,l, vθe,l, and vϕe,l represent the radial
velocity, the azimuthal velocity, and the elevation velocity,
respectively. Notably, compared to the 2D velocity sensing, the
3D velocity sensing involves more variables, and thus leads
to higher complexity. As shown in Fig. 3, the mathematical
relationship between f Dl and ˜ve,l is expressed as
f Dl,m = 1λ vre,l,m + vθe,l,m + vϕe,l,m . (15)
In Eq. (15), vre,l,m, vθe,l,m, and vϕe,l,m denote the projection of
the E-UA V’s radial velocity, azimuthal velocity, and elevation
velocity along the line connecting the E-UA V and the m-th
GBS antenna, respectively. Thus, we have
vre,l,m = cos αr,mvre,l, (16a)
vθe,l,m = cos αθ,mvθe,l, (16b)
vϕe,l,m = cos αϕ,mvϕe,l, (16c)
where αr,m, αθ,m and αϕ,m represent the included angles
between the line connecting the m-th GBS antenna and the
E-UA V , and the E-UA V’s radial, azimuthal, and elevation
velocities, respectively. These angles are illustrated in Fig. 3.
(a) The E-UA V’s radial and ele-
vation velocities.
 (b) The E-UA V’s azimuthal velocity.
Fig. 2: Illustration of the E-UA V ’s 3D velocities.
Thanks to the various values of f Dl,m, ∀m, the ML
method [32] can be utilized for the estimation of ˜ve,l based
on the relationship between f Dl and ˜ve,l as shown in Eq. (15).
Specifically, the ML optimization problem is formulated as
follows:

ˆβ, ˆve,l

= arg min
β, ˜ve,l
Ybl − βXl (˜ve,l)2F , (17)
where ˆβ and ˆve,l denote the estimated values of β and ˜ve,l,
respectively. For given ˜ve,l, the optimal ˆβ is given by
ˆβ = tr
 
Ybl XHl (˜ve,l)
∥Xl (˜ve,l) ∥2F . (18)
Substituting the estimated ˆβ into the original problem (17),
we obtain the following optimization subproblem for solving
˜ve,l:
ˆve,l = arg max˜ve,l g (˜ve,l) =
tr  Ybl XHl (˜ve,l)2
∥Xl (˜ve,l) ∥2F . (19)
Since problem (19) is highly non-convex w.r.t. ˜ve,l, the
gradient descent algorithm can be utilized to find the sub-
optimal solution [32]. Specifically, according to the chain rule,
the gradient of g (˜ve,l) w.r.t. vie,l, ∀i ∈ {r, θ, ϕ} is given by
∂g (˜ve,l)
∂v ie,l = 2Re
(
tr
 
∂g (˜ve,l)
∂XTl (˜ve,l)
∂Xl (˜ve,l)
∂v ie,l
!)
, (20)
where
∂g (˜ve,l)
∂XTl (˜ve,l) = tr
 
Ybl XHl (˜ve,l)  Ybl H
∥Xl (˜ve,l) ∥2F
−
tr  Ybl XHl (˜ve,l)2 XHl (˜ve,l)
∥Xl (˜ve,l) ∥4F . (21)
Then, the next step is to calculate the following partial
derivations:

<!-- extraction_page_index: 6 -->

6
(a)
 (b)
 (c)
Fig. 3: Illustration of the geometrical relationship between ˜ve,l and vel,m.
∂Xl (˜ve,l)
∂v ie,l =
"
∂Gl (1)
∂v ie,l xl(1), . . . ,∂Gl (N )∂v ie,l xl(N )
#
,
(22a)
∂Gl (n)
∂v ie,l = 2A(rel , θel , ϕel ) ⊙
 
∂dl,n (˜ve,l)
∂v ie,l dTl,n (˜ve,l)
!
,
(22b)
∂dl,n (˜ve,l)
∂v ie,l = −j 2πλ nTs
×
"
dl,n,1 (˜ve,l) ∂ve,l,1∂v ie,l , . . . , dl,n,M (˜ve,l) ∂ve,l,M∂v ie,l
#T
,
(22c)
where dl,n,m (˜ve,l) denotes the m-th element of dl,n (˜ve,l).
According to (16), the partial derivation ∂ve,l,m∂v ie,l in (22c) canbe easily obtained, for which the details is omitted here.
Finally, based on the partial derivations ∂g(˜ve,l)∂v ie,l , ∀i ∈
{r, θ, ϕ}, ˜ve,l is updated through the following gradient-
descent steps:
˜v(t+1)e,l = ˜v(t)e,l + η(t) ∂g (˜ve,l)∂ ˜ve,l

˜ve,l=˜v(t)e,l
, (23)
where ˜v(t)e,l and η(t) denote the updated value of ˜ve,l and the
step size in the t-th iteration. The details of the gradient-
descent algorithm is shown in Algorithm 1. In Algorithm 1,
the complexity for calculating ∂g (˜ve,l) /∂v ie,l is given by
O
 
M 2N . Denote Igrad as the number of iterations for the
gradient descent convergence. Then, the overall computational
complexity of Algorithm 1 is O
 
IgradM 2N .
B. EKF-Based E-UAV State Tracking
To address inevitable errors of the sensed E-UA V’s states,
i.e., locations and velocities, obtained with the echo signals as
described in Section III-A, we propose an EKF-based method
to fuse the predicted states and the measured ones [28] for
improving the E-UA V trajectory tracking accuracy. In the
following, we first construct the state measurement error model
and the state prediction model, and then introduce the EKF-
based data fusion approach.
Algorithm 1 Proposed Algorithm for Optimizing ˜ve,l
1: Initialize feasible point ˜v(0)e,l and step size η(0).
2: Set iteration index t = 0.
3: repeat
4: Solve problem (23) to obtain ˜v(t)e,l;
5: Update ˜ve,l = ˜v(t)e,l;
6: t = t + 1;
7: until the fractional increment of ˜ve,l is less than the
threshold µ1.
1) State Measurement Error Model: In the l-th CPI, denote
the sensing errors for rel , θel , ϕel , vre,l, vθe,l, and vϕe,l as
Gaussian random variables zrel , zθel , zϕel , zvre,l, zvθe,l and zvϕe,l,
respectively, each with zero mean and variances σ2rel , σ2θel , σ2ϕel ,
σ2vre,l, σ2vθe,l and σ2vϕe,l, respectively. Then, the measured statescan be expressed as
ˆrel = ∥qe,l∥ + zrel , (24a)
ˆθel = arcsin xelq
|xel |2 + |yel |2
+ zθel , (24b)
ˆϕel = arcsin zel∥qe,l∥ + zϕel , (24c)
ˆvre,l = vxe,lxel + vye,lyel + vze,lzel∥qe,l∥ + zvre,l , (24d)
ˆvθe,l = vxe,lyel − vye,lxelq
|xel |2 + |yel |2
+ zvθe,l , (24e)
ˆvϕe,l = vze,l
q
|xel |2 + |yel |2
∥qe,l∥
+
vxe,lxel + vye,lyelq
|xel |2 + |yel |2
× zel
∥qe,l∥ + zvϕe,l .
(24f)
Assuming that the measurement errors for each state are
uncorrelated, we can construct the measurement error covari-
ance matrix as Pl = diag{σ2rel , σ2θel , σ2ϕel , σ2vre,l , σ2vθe,l , σ2vϕe,l }. It

<!-- extraction_page_index: 7 -->

7
has been demonstrated in [37] that the measurement errors are
inversely proportional to the signal-to-noise ratio (SNR) of the
echo signals. Therefore, we have σ2rel = crSNRl , σ2θel = cθSNRl ,
σ2ϕel = cϕSNRl , σ2vr,l = cvrSNRl , σ2vθ = cvθSNRl and σ2vϕ,l = cvϕSNRl ,where cr, cθ, cϕ, cvr,cvθ and cvϕ are the scaling factors [38],
while SNRl is given by
SNRl = σRCSβ02M N|α(rel , θel , ϕel )wel |2
4πσ 2b (rel )4 . (25)
Denote the E-UA V’s ground-truth state vector
under the Cartesian coordinate system and the
measured state vector under the spherical coordinate
system as sel = hxel , yel , zel , vxe,l, vye,l, vze,liT and
ˆul =
h
ˆrel , ˆθel , ˆϕel , ˆvre,l, ˆvθe,l, ˆvϕe,l
iT
, respectively. Then, (24) can
be rewritten as
ˆul = χl(sel ) + zl, (26)
where zl = [zrel , zθel , zϕel , zvre,l , zvθe,l , zvϕe,l ]T denotes the noise
vector, and the function χ(·) can be derived based on (24) .
2) State Prediction Model: To accurately characterize the
temporal motion of the E-UA V , it is essential to establish
a state prediction model. Specifically, the state prediction
equation can be expressed as
sel = Fsel−1 + ζl, (27)
where ζl =
h
ζxel , ζyel , ζzel , ζvxe,l , ζvye,l , ζvze,l
iT
,
ζxel , ζyel , ζzel , ζvxe,l , ζvye,l, and ζvze,l denote the prediction
errors for xel , yel , zel , vxe,l, vye,l, and vze,l respectively, with
ζxel ∼ N(0, σ2xel ), ζyel ∼ N(0, σ2yel ), ζzel ∼ N(0, σ2zel ), ζvxe,l ∼
N (0, σ2vxe,l ), ζvye,l ∼ N(0, σ2vye,l ) and ζvze,l ∼ N(0, σ2vze,l ),respectively. Again, assuming mutually independent
state prediction errors, we have ζl ∼ N (0, Qs) with
Qs = diag {σ2xel , σ2yel , σ2zel , σ2vxe,l , σ2vye,l , σ2vze,l }. Moreover,
F ∈ R6×6 is the state transition matrix. In the prediction
model, we make the assumption of constant-velocity
movement between adjacent CPIs and express the state
transition matrix accordingly as
F =

I3 ∆tI3
03 I3

. (28)
3) EKF-Based Data Fusion: Due to the nonlinearity
of (24), we adopt the EKF for fusing the E-UA V’s measured
states and the predicted ones [39]. In the l-th CPI, we assume
that the GBS has the E-UA V’s state estimation ˆsel−1 from
the (l − 1)-th CPI, along with the corresponding covariance
matrix Cl−1 of the estimation errors. Then, the state prediction
equation and the corresponding prediction error covariance
matrix are respectively given by
ˆsel|l−1 = Fˆsel−1, (29)
Cl|l−1 = FCl−1FT + Qs, (30)
where ˆsel|l−1 denotes the predicted state of the E-UA V in the
l-th CPI. With the predicted state ˆsel|l−1 and the measured one
ˆul, the E-UA V’s state in the l-th CPI is updated by
ˆsel = ˆ sel|l−1 + Kl(ul − h(ˆ sel|l−1)), (31)
Fig. 4: The overall E-UA V trajectory tracking workflow.
where Kl denotes the Kalman gain that is given by
Kl = Cl|l−1ΣlT

ΣlCl|l−1ΣTl + Pl
−1
. (32)
The covariance matrix of the estimation error, i.e., ˆsel − sel , is
given by [28]
Cl =

C−1l|l−1 + ΣHl P−1l Σl
−1
, (33)
where Σl = ∂χl∂sel |sel =ˆsel|l−1 denotes the Jacobian matrix ofh(·) w.r.t. sel . It is worth noting that Cl is the key variable
to evaluate the E-UA V trajectory tracking accuracy, which
highly depends on the SNR of the echo signals received at
the GBS due to Pl. Therefore, the value of Cl will be taken
into consideration for the joint GBS beamforming and C-
UA V trajectory design in the next section. The overall E-UA V
trajectory tracking workflow is shown in Fig. 4.
IV. O NLINE JOINT GBS B EAMFORMING AND C-UAV
TRAJECTORY DESIGN SCHEME
With the E-UA V trajectory tracking scheme proposed in
Section III, the GBS can obtain the real-time E-UA V’s loca-
tions, and thus facilitates the online GBS beamforming and
C-UA V trajectory design. On this basis, we formulate the
optimization problem with the aim of maximizing the secrecy
rate for the l-th CPI as follows:
max
qc,l,wcl ,wel
ˆRsl , (34a)
s.t. ∥qc,l − qc,l−1∥ ≤Vmax∆t, (34b)
qmin ≤ qc,l ≤ qmax, (34c)
||qc,l − ˆqe,l|l−1||2 ≥ d2min, (34d)
∥wcl ∥2 + ∥wel ∥2 ≤ Pmax, (34e)
tr(Cl) ≤ Γ. (34f)
In (34), ˆRsl denotes the secrecy rate calculated with the pre-
dicted E-UA V’s locationˆqe,l|l−1, for which the full expression
will be provided later. (34b) restricts that the C-UA V’s maxi-
mum speed does not exceed Vmax. (34c) confines the C-UA V’s
flight within the 3D space [qmin, qmax]. (34d) is the collision
avoidance constraint, where dmin is the minimum safe distance
between the C-UA V and the E-UA V . (34e) guarantees that
the GBS transmit power does not exceed Pmax. (34f) ensures

<!-- extraction_page_index: 8 -->

8
that the mean squared error (MSE) of the E-UA V’s state
estimation is not larger than the threshold Γ. The optimization
problem (34) is intractable to solve as it is non-convex w.r.t.
qc,l, wcl , wel , and the involved variables are highly coupled.
Therefore, we propose to invoke the AO algorithm to decouple
the original problem into the GBS beamforming and the C-
UA V trajectory design subproblems, where each subproblem
is iteratively optimized while keeping the other one fixed.
A. GBS Beamforming Optimization
To start with, we first define Wc,l = wcl (wcl )H and We,l =
wel (wel )H. Then, the GBS beamforming subproblem can be
formulated as
max
Wc,l,We,l
ˆRsl (35a)
s.t. tr(Wc,l) + tr(We,l) ≤ Pmax, (35b)
Wc,l ⪰ 0, We,l ⪰ 0, (35c)
Rank (Wc,l) = 1, Rank (We,l) = 1, (35d)
(34f). (35e)
In (37a), ˆRsl is given by
ˆRsl =

log2

1 + tr(Hbcl Wc,l)tr(Hbcl We,l) + σ2c 
− log2
 
1 +
tr( ˆHbel|l−1Wc,l)
tr( ˆHbel|l−1We,l) + σ2e
!#+
, (36)
where Hbcl = hbcl  hbcl H and ˆHbel|l−1 = ˆhbel|l−1 ˆhbel|l−1H
with ˆhbel|l−1 denoting the channel between the GBS and the
E-UA V calculated by the predicted E-UA V’s locationˆqe,l|l−1.
To facilitate the design, we introduce the auxiliary exponential
variables τ, ε, δ, and ϵ, and transform problem (35) as
max
Wc,l,We,l,τ,ε,δ,ϵ
τ − ε − δ + ϵ (37a)
eτ ≤ trHbcl We,l + trHbcl Wc,l + σ2c , (37b)
eε ≥ tr Hbcl We,l + σ2c , (37c)
eδ ≥ tr ˆHbel|l−1Wc,l + tr ˆHbel|l−1We,l + σ2e , (37d)
eϵ ≤ tr ˆHbel|l−1We,l + σ2e , (37e)
(35b) − (35d), (34f). (37f)
Problem (37) is still non-convex due to constraints (37c),
(37d), (35d), and (35e). For (37c) and (37d), we apply the first-
order Taylor expansion to obtain the following two relaxed
constraints:
tr
 
Hbcl We,l + σ2c ≤ eε(j) (ε − ε(j) + 1), (38)
tr
  ˆHbel|l−1Wc,l+tr  ˆHbel|l−1We,l + σ2e
≤ eδ(j) (δ − δ(j) + 1), (39)
where ε(j) and δ(j) are the given local points of ε and δ in
the j-th iteration of the SCA, respectively. Moreover, to deal
with the non-convexity of the covariance matrix in (34f), we
introduce auxiliary variables um ≥ 0, ∀m ∈ {1, ...,6} to upper
bound the diagonal elements in Cl, and transform constraint
(34f) to the following two constraints:
[Cl]m,m ≤ um, ∀m, (40)
6X
i=1
um ≤ Γ, ∀m, (41)
where [Cl]m,m denotes the m-th diagonal element of Cl.
To further simplify the non-convex form of (40), we utilize
the Schur complement [40] to obtain the following equivalent
constraint: 
C−1l em
eTm um

⪰ 0, ∀m, (42)
where em ∈ R6×1 denotes a vector whose m-th element is 1
and other elements are 0.
Now, the only non-convexity left in problem (37) is the
rank-one constraint (35d). To deal with this issue, we provide
an equivalent difference of convex (DC) representation as
ψi,l ≜ ∥Wi,l∥∗ − ∥Wi,l∥2 = 0, i∈ {c, e}, (43)
where ∥Wi,l∥∗ and ∥Wi,l∥2 denote the nuclear norm and the
largest spectral norm of Wi,l, respectively. Note that for any
Wi,l, the inequality ∥Wi,l∥∗−∥Wi,l∥2 ≥ 0 always hold, with
equality occurring if and only if Wi,l is a rank-one matrix.
Hence, the constraint (35d) is satisfied exclusively when Wi,l
is rank-one. Next, we apply the penalty-based method [41]
to tackle the constraint (43). Specifically, by adding (43) into
the objective function as a penalty term, problem (37) can be
converted to:
min
Wc,l,We,l
−(τ − ε − δ + ϵ) + ω
X
i∈{c,e}
ψi,l, (44a)
s.t. (35b), (35c), (37b), (37e), (38) − (39), (41), (42), (44b)
where ω > 0 denotes the penalty factor. As ω → +∞ (or
becomes sufficiently large), the solution Wi,l of problem (44)
will comply with the equality constraint (43). However, if
ω is initially set too large, the penalty term will dominate
the objective function (44a), diminishing the influence of the
desired maximum secrecy rate on the optimization result. To
prevent this, we start by setting ω to a relatively small value
to determine an appropriate initial point, after which ω is
gradually increased until the rank-one constraint is satisfied.
To deal with the non-convexity of the penalty term in (44a),
we utilize the first-order Taylor expansion to obtain the convex
upper bound in the j-th iteartion of the SCA as follows:
∥Wi,l∥∗ − ∥Wi,l∥2 ≤ tr (Wi,l) − ¯W(j)i,l ≜ ψ(j)i,l , (45)
where ¯W(j)i,l ≜ ∥W(j)i,l ∥2 + trξ(W(j)i,l )ξ(W(j)i,l )H (Wi,l −
W(j)i,l ) and ξ(W(j)i,l ) is the eigenvector of Wi,l corresponding
to the largest singular value σ1(Wi,l). Subsequently, problem
(37) can be equivalently addressed by solving the following
problem:
min
Wc,l,We,l,τ,ε,δ,ϵ
−(τ − ε − δ + ϵ) + ω
X
t∈{c,e}
ψ(j)i,l , (46a)

<!-- extraction_page_index: 9 -->

9
Algorithm 2 Proposed Algorithm for Optimizing Wc,l, We,l
1: Initialize feasible points
n
W(0)c,l , W(0)e,l
o
, and the penalty
factor ω.
2: repeat
3: Set iteration index j = 0;
4: repeat
5: Solve problem (46) to obtain W(j)c,l and W(j)e,l ;
6: Update Wc,l = W(j)c,l , and Wc,l = W(j)e,l ;
7: j = j + 1;
8: until the fractional decrement of the ˆRsl is less than the
threshold µ2;
9: Update ω = cω;
10: until the rank-one constraint violation is below a prede-
fined threshold µ3.
s.t. (35b), (35c), (37b), (37e), (38) − (39), (41), (42). (46b)
The relaxed problem (46), structured as a standard convex
semi-definite program (SDP), can be effectively addressed by
using optimization tools like CVX [42]. The specific details of
the proposed algorithm for solving the original problem (35)
are outlined in Algorithm 2. Note that Algorithm 2 consists
of two loops. In the inner loop, the variable Wc,l, We,l are
optimized by solving the relaxed convex form (46) iteratively.
In the outer loop, the penalty factor ω is updated with the
scaling factor c >1 until the rank-one constraint is satisfied.
B. C-UAV Trajectory Optimization
With the fixed GBS beamforming vectors wc,l and we,l, the
C-UA V trajectory design subproblem can be formulated as
max
qc,l
ˆRsl (47a)
s.t. (34b) − (34d). (47b)
As the leakage information rate is irrelevant to the C-UA V
trajectory qc,l, we can rewrite problem (47) as
max
qc,l
Rcl (48a)
s.t. (34b) − (34d). (48b)
Since the steering vector α(rcl , θcl , ϕcl ) is highly complex w.r.t.
qc,l, we propose to adopt the value of qc,l in the (k−1)-th iter-
ation of the SCA, i.e., q(k−1)c,l , for approximating α(rcl , θcl , ϕcl )
in the k-th iteration [43]. As such, the communication channel
hcl in the k-th iteration of the SCA is approximated by
hc,(k)l = β0rcl α rc,(k−1)l , θc,(k−1)l , ϕc,(k−1)l  = ˜hc,(k−1)l rcl ,(49)
where ˜hc,(k−1)l ≜ β0α rc,(k−1)l , θc,(k−1)l , ϕc,(k−1)l ,
rc,(k−1)l , θc,(k−1)l , and ϕc,(k−1)l denote the distance, azimuthal
angle, and elevation angle between the C-UA V and the GBS
based on q(k−1)c,l . Accordingly, in the k-th iteration, the
objective function Rc,(k)l is given by
Rc,(k)l =
log2
 
1 + tr( ˜Hbc,(k−1)l Wc,l)
tr( ˜Hbc,(k−1)l We,l) + ∥qc,l − qb∥2σ2c
!
,
(50)
Algorithm 3 Proposed Algorithm for Optimizing qc,l
1: Initialize feasible point q(0)c,l .
2: Set iteration index k = 0.
3: repeat
4: Solve problem (53) to obtain q(k)c,l ;
5: Update qc,l = q(k)c,l ;
6: k = k + 1;
7: until the fractional increment of (53) is less than the
threshold µ2.
where ˜Hbc,(k−1)l = ˜hc,(k−1)l

˜hc,(k−1)l
H
. Due to the non-
convexity of (50), we adopt the first-order Taylor expansion
to obtain the globally lower bound as follows:
Rc,(k)l ≥ log2
 
1 + Ac,(k−1)l
Bc,(k−1)l + γ(k)
!
− 1ln 2
×
σ2c Ac,(k−1)l (∥qc,l − qb∥2 − ∥q(k)c,l − qb∥2)
(Bc,(k−1)l, + γ(k))2 + Ac,(k−1)l (Bc,(k−1)l + γ(k))
≜ ¯Rc,(k)l ,
(51)
where Ac,(k−1)l = tr( ˜Hbc,(k−1)l Wc,l), Bc,(k−1)l =
tr( ˜Hbc,(k−1)l We,l), γ(k) = ∥q(k)c,l − qb∥2σ2c , and q(k)c,l denotes
the given local point at the k-th iteration. Similarly, the non-
convex constraint (34d) can be relaxed to the convex form by
applying the first-order Taylor expansion as follows:
d2min ≤ ∥q(k)c,l − ˆqe,l|l−1∥2
+ 2(q(k)c,l − ˆqe,l|l−1)T (qc,l − q(k)c,l ). (52)
Subsequently, in the k-th iteration of the SCA, problem (48)
can be relaxed to the following convex form:
max
qc,l
¯Rc,(k)l (53a)
s.t. (34b), (34c), (52). (53b)
Problem (53) can be readily solved by standard convex solvers,
such as CVX [44]. For clarity, the algorithm developed for
solving the C-UA V trajectory optimization problem is outlined
in Algorithm 3.
C. Overall Algorithm
With the solutions obtained for problems (35) and (47),
we now finalize the overall algorithm design for solving
the original problem (34), which is given in details in Al-
gorithm 4 . Specifically, Algorithm 2 and Algorithm 3 are
iteratively executed until the increment of the secrecy rate is
below the predefined convergence threshold µ4. Since ˆRsl is
non-decreasing during the process in alternatively optimizing
Wc,l, We,l, and qc,l, Algorithm 4 is guaranteed to converge
to a solution of problem (34) that is at least locally optimal.
We now analyze the computational complexity of Algo-
rithm 4. For solving Wc,l and We,l, the main computational
complexity of Algorithm 2 relies on applying CVX to solve
the SDP problem. If the interior point method is employed, the
complexity is given by O(2M 3.5). Thus the total complexity
is IinIout
 
2M 3.5, where Iin and Iout represent the required

<!-- extraction_page_index: 10 -->

10
TABLE I: Simulation parameters
Parameter Description Value Parameter Description Value
B Signal bandwidth 10 kHz Γ Maximum E-UA V tracking MSE 0.2
N Number of symbols in one CPI 500 qmin Flight area lower bound [−30, −30, 25]T
L Total number of CPIs 80 qmax Flight area upper bound [30, 30, 40]T
∆t CPI duration 0.05 s Vmax Maximum velocity of C-UA V 5 m/s
β0 Channel power gain at 1 meter −30 dB dmin Minimum safe distance 7 m
Pmax GBS maximum transmit power 30 dBm σ2c ,σ2e C-UA V and E-UA V noise power −80 dBm
σRCS Radar cross-section of the E-UA V 0.03 m2 σ2b GBS noise power −50 dBm
cr,cθ,cϕ Scaling factors for locationmeasurement errors 1,10−2,10−2 cvr , cvθ , cvϕ Scaling factors for velocitymeasurement errors 1,1,1
Algorithm 4 Proposed AO-based algorithm for solving prob-
lem (34)
1: Initialize q(0)c,l , W(0)c,l , W(0)e,l .
2: Set iteration index q = 0.
3: repeat
4: Update Wc,l = W(q)c,l and We,l = W(q)e,l via Algo-
rithm 2 with given qc,l;
5: Update qc,l = q(q)c,l via Algorithm 3 with given Wc,l
and We,l;
6: q = q + 1;
7: until the increment of ˆRsl is below the threshold µ4.
number of inner and outer iterations for convergence, respec-
tively. Similarly, for solving qc,l, Algorithm 3 exhibits the
complexity of O(I33.5), where I denotes the number of SCA
iterations. Therefore, the overall complexity of Algorithm 4
can be expressed as O(IAO(IinIout
 
2M 3.5 + I33.5)), where
IAO denotes the number of iterations required for the conver-
gence of the AO algorithm.
V. S IMULATION RESULTS
In this section, numerical results are provided to validate
the feasibility and effectiveness of the proposed near-field
3D sensing-aided secure UA V communication framework. We
assume that the GBS is equipped with M = 16 × 16 antennas,
the system operates at the frequency of fc = 1 .5 GHz ,
and the spacing between the antenna elements is set as half
of the operating wavelength. As a result, the corresponding
Rayleigh distance is 52 m . Referring to the x-o-y plane in
Fig. 1, we assume that the E-UA V performs the circular motion
centered at (4.6, 8.0, 28.5) meters with the radius of 3.2 m.
Unless otherwise specified, the adopted system parameters are
presented in Table I.
A. Convergence of Algorithm 4
In Fig. 5, we investigate the convergence behavior of
the proposed AO algorithm for the joint GBS beamforming
and C-UA V trajectory design under different GBS maximum
transmit power Pmax. The demonstrated results were acquired
by running Algorithm 4 in the 18-th CPI. Note that the secrecy
rate is obtained based on (12), where qcl , wcl , wel are the output
of Algorithm 4 given the estimated E-UA V trajectory, while
hbel in (12) is calculated based on the E-UA V’s ground-truth
trajectory. It is shown that the secrecy rate increases rapidly
at the beginning of the iterations and converges within around
5 iterations. This fast convergence speed implies the possible
application of the proposed AO algorithm in practice. It is
1 2 3 4 5 6 7 8 9 10
Number of iterations
15
15.5
16
16.5
17
17.5
18
18.5
19
Secrecy Rate (bps/Hz)
Pmax=22 dBm
Pmax=24 dBm
Pmax=26 dBm
Fig. 5: Convergence behavior of the proposed algorithm at one CPI.
also observed that the secrecy rate increases with higher GBS
maximum transmit powe, which is expected given the higher
power gain for the information signal transmitted to the C-
UA V and the enhanced AN signal strength at the E-UA V .
B. E-UAV Trajectory Tracking and C-UAV Trajectory Design
Performance
In Fig. 6, we depict the estimated E-UA V trajectory obtained
with the trajectory tracking scheme designed in Section III as
well as the C-UA V trajectory obtained withAlgorithm 4 given
different initial locations. Specifically, we set three different
C-UA V’s initial locations, given by [10, 2, 30]T , [14, 6, 30]T ,
[12, 16, 30]T , and label the corresponding trajectory as “C-
UA V trajectory 1”, “C-UA V trajectory 2”, and “C-UA V tra-
jectory 3”, respectively. The E-UA V’s ground-truth trajectory
is also plotted for comparison. One can first observe that
estimated trajectory perfectly aligns with the ground-truth
trajectory of the E-UA V , which underscores the high accuracy
for tracking the E-UA V trajectory with the proposed near-
field 3D sensing method. Observing the C-UA V’s trajectories,
one can find that the C-UA V’s flight tends to approach the
GBS, which is expected as the secrecy rate can be improved
when the path loss between the GBS and C-UA V is reduced.
Moreover, it is also seen that the C-UA V keeps adjusting its
flight during the given time period rather than adopting the
straight-line trajectory. The is because, due to the presence
of the E-UA V , the C-UA V trajectory should be designed to
guarantee the minimum safe distance, as well as to reduce
the channel correlations with the E-UA V so as to improve the

<!-- extraction_page_index: 11 -->

11
(a) 2D-space demonstration.
(b) 3D-space demonstration.
Fig. 6: Demonstration of the E-UA V’s estimated trajectory and the
C-UA V’s designed trajectory.
secrecy rate. From the 3D trajectory plot given in Fig. 6(b),
we also see that the C-UA V initially descends rapidly along
the z-axis until reaches to the predetermined minimum flight
altitude, after which the height is not changed anymore. This
is quite intuitive as the C-UA V tends to be get close to the
GBS to improve the achievable rate.
In Fig. 7, we plot the instantaneous normalized E-UA V’s
state estimation error (NSEE) during the whole flight duration
of 80 CPIs. The NSEE is defined as log10( |sel −ˆsel |2ρ ), with the
normalization factor ρ set to 10. It is evident to see that the
NSEE increases with the increment of the maximum E-UA V
tracking MSE Γ. Specifically, define the average NSEE over L
CPIs as 1L PLl=1 log10( |sel −ˆsel |2ρ ). We obtain the average NSEE
over the 80 CPIs as −1.09 dB, −1.98 dB, −2.18 dB, and
−2.58 dB for Γ given by 0.2, 0.05, 0.04, and 0.02, respec-
tively. This is expected, as the instantaneous E-UA V’s state
estimation error gets smaller when the estimation accuracy
requirement becomes more strict. We also observe that the
instantaneous NSEE provided in Fig. 7 does not monotonically
decrease over time, which is due to the E-UA V’s varying
0 10 20 30 40 50 60 70 80
CPI index
-4.5
-4
-3.5
-3
-2.5
-2
-1.5
-1
-0.5
0
NSEE (dB)
=0.2
=0.05
=0.04
=0.02
Fig. 7: Instantaneous normalized E-UA V’s state estimation error
versus the maximum tracking MSE.
0 10 20 30 40 50 60 70 80
CPI index
15
16
17
18
19
20
21Secrecy Rate (bps/Hz) Pmax = 30 dBm
Pmax = 28 dBm
Pmax = 26 dBm
Pmax = 24 dBm
Pmax = 22 dBm
Fig. 8: Secrecy rate versus GBS maximum transmit power.
locations during the whole time period.
C. Secure UAV Communications Performance
We choose the “C-UA V trajectory 1” in Fig. 6 for demon-
strating the secure UA V communication performance in this
subsection. In Fig. 8, we depict the instantaneous secrecy rate
with different GBS maximum transmit power Pmax. One can
observe that the secrecy rate increases rapidly at the beginning
of the flight, which is due to the fact that the C-UA V quickly
descends and gets closer to the GBS. Subsequently, the C-UA V
adjusts its flight direction to maintain a safe distance from the
E-UA V , resulting in a slower increment of the secrecy rate.
Once the C-UA V reaches to the position that is directly above
the GBS, the secrecy rate remains approximately constant.
In Fig. 9, we present the instantaneous secrecy rate with
different maximum E-UA V tracking MSE Γ. It is interesting
to find that, the secrecy rate does not change much when Γ
is relatively large. However, a significant decrement of the
secrecy rate is observed when Γ drops below 0.04, which can
be explained as follows. When Γ gets smaller, the GBS needs
to allocate more power to the AN signals, which results in

<!-- extraction_page_index: 12 -->

12
0 10 20 30 40 50 60 70 80
CPI index
18.8
19
19.2
19.4
19.6
19.8
20
20.2
20.4Secrecy Rate (bps/Hz)
 = 0.2
 = 0.1
 = 0.05
 = 0.04
 = 0.02
Fig. 9: Secrecy rate versus maximum E-UA V tracking MSE.
22 23 24 25 26 27 28 29 30
Maximum transmit power (dBm)
16.5
17
17.5
18
18.5
19
19.5
20
20.5Average secrecy rate (bps/Hz)
Perfect knowledge scheme
Proposed scheme
C-UAV static scheme
26 27 28
18.6
18.8
19
19.2
 
Fig. 10: Average secrecy rate versus maximum transmit power.
lower power allocation to the information signal given that
the GBS total transmit power is limited. This performance
degradation gets more severe when l is larger than 50. This
is because, after 50 CPIs, the E-UA V moves farther from the
GBS while the C-UA V’s location keeps almost static as it has
reached to the location above the GBS. Thus, the GBS needs to
allocate more power to the AN signals to guarantee the sensing
accuracy, which leads to the decrement of secrecy rate as the
power allocated to the C-UA V gets lower. These observations
highlight the trade-off between the E-UA V tracking accuracy
and the secure communication performance. In other words,
to achieve high secrecy rate, the sensing accuracy threshold
should be given a proper value.
D. Comparison with Baseline Schemes
To further evaluate the effectiveness of the proposed near-
field sensing-aided secure UA V communication framework, we
compare with the following two baseline schemes:
• Perfect knowledge scheme (denoted as “ PKS”): In this
case, the E-UA V trajectory is assumed to be perfectly
known at the GBS. Therefore, the resulting joint GBS
beamforming and C-UA V trajectory design problem can
0.02 0.03 0.04 0.05 0.06 0.07 0.08 0.09 0.1
Maximum E-UAV tracking MSE
18.6
18.8
19
19.2
19.4
19.6
19.8
20
20.2Average secrecy rate (bps/Hz)
Perfect knowledge scheme
Proposed scheme
C-UAV static scheme
0.06 0.07 0.08
20.02
20.04
20.06
20.08  
Fig. 11: Average secrecy rate versus maximum E-UA V tracking MSE.
be solved by applying Algorithm 4 with the precise E-
UA V’s real-time locations.
• C-UA V static scheme (denoted as “ CSS”): In this case,
the location of the C-UA V is assume to be fixed at the
point (12.0, 3.0, 10.0) meters, while the GBS beamform-
ing is designed by applying Algorithm 2.
In Fig. 10, we compare the average secrecy rate over 80
CPIs achieved by different schemes versus the GBS maximum
transmit power. As can be observed, the performance of the
proposed scheme nearly approaches to that of the “PKS”,
which confirms the effectiveness of the proposed E-UA V
trajectory tracking scheme. Moreover, the proposed scheme is
shown to outperform the “CSS”, which implies that the secure
communication performance can be improved by properly
designing the C-UA V trajectory with Algorithm 4.
In Fig. 11, we further provide the performance comparison
between the proposed scheme and the baselines versus the
maximum E-UA V tracking MSE Γ. It is shown that the
performance gap between the proposed scheme and the “PKS”
is negligible. Moreover, we can observe that the performance
gap between the proposed scheme and the “CSS” is much
significant when Γ is small. This is because, the GBS needs
to allocate more power to the AN signals when the sensing
accuracy requirement is strict. As the distance between the
GBS and the C-UA V is large for “CSS”, the secrecy rate
degradation is more pronounced when less power is allocated
to the information signal.
VI. C ONCLUSION
In this paper, a novel near-field 3D sensing-aided secure
UA V communication framework with high time efficiency was
proposed, where the GBS sent the AN signals for both the
sensing and jamming purpose to the E-UA V . To obtain the
unknown E-UA V’s locations in real time, an E-UA V trajectory
tracking scheme was first introduced. Specifically, the 3D
velocities were estimated with the echo signals by exploiting
the variant Doppler shift observations over the spatial domain
in the near field. An EKF-based data fusion method was
further designed to timely correct the E-UA V localization
errors. Based on the E-UA V’s predicted location with the

<!-- extraction_page_index: 13 -->

13
measured 3D velocities, a joint GBS beamforming and C-
UA V trajectory design scheme was proposed for maximizing
the instantaneous secrecy rate, while guaranteeing the sensing
accuracy. An AO algorithm was developed for solving the
resulting non-convex problem, where the subproblems were
iteratively solved with the SCA method. Extensive simulation
results were provided to verify the superiority of the proposed
scheme. It was shown that the proposed E-UA V trajectory
tracking scheme can achieve accurate localization of the E-
UA V in real time. Moreover, the secrecy rate achieved by the
proposed scheme was demonstrated to closely approaches to
that obtained by the case where the E-UA V trajectory was
perfectly known.
REFERENCES
[1] Y . Zeng, Q. Wu, and R. Zhang, “Accessing from the sky: A tutorial on
UA V communications for 5G and beyond,”Proc.IEEE, vol. 107, no. 12,
pp. 2327–2375, Dec. 2019.
[2] R. Zhang, H. Du, D. Niyato, J. Kang, Z. Xiong, A. Jamalipour, P. Zhang,
and D. I. Kim, “Generative AI for space-air-ground integrated networks,”
IEEE Wireless Commun., vol. 31, no. 6, pp. 10–20, Dec. 2024.
[3] J. Zhao, Q. Xu, X. Mu, Y . Liu, and Y . Zhu, “Aerial active STAR-RIS-
aided IoT NOMA networks,” IEEE Internet Things J. , vol. 12, no. 8,
pp. 9525–9538, Apr. 2025.
[4] R. Zhang, H. Du, Y . Liu, D. Niyato, J. Kang, Z. Xiong, A. Jamalipour,
and D. In Kim, “Generative AI agents with large language model for
satellite networks via a mixture of experts transmission,” IEEE J. Sel.
Areas Commun., vol. 42, no. 12, pp. 3581–3596, Dec. 2024.
[5] B. Duo, Q. Wu, X. Yuan, and R. Zhang, “Anti-jamming 3D trajectory
design for UA V-enabled wireless sensor networks under probabilistic
LoS channel,” IEEE Trans. Veh. Technol., vol. 69, no. 12, pp. 16 288–
16 293, Dec. 2020.
[6] J. Zhao, J. Su, K. Cai, Y . Zhu, Y . Liu, and N. Al-Dhahir,
“Interference-robust broadband rapidly-varying MIMO communica-
tions: A knowledge-data dual driven framework,” IEEE Trans.
Wireless Commun. , pp. 1–17, Mar. 2025, early access, doi:
10.1109/TWC.2025.3548618.
[7] M. Jiang, Y . Li, Q. Zhang, Q. Li, and J. Qin, “Secure beamforming in
downlink MIMO nonorthogonal multiple access networks,” IEEE Signal
Process. Lett., vol. 24, no. 12, pp. 1852–1856, Dec. 2017.
[8] W. Ma, C. Qi, and G. Y . Li, “High-resolution channel estimation for
frequency-selective mmwave massive MIMO systems,” IEEE Trans.
Commun. Technol., vol. 19, no. 5, pp. 3517–3529, May 2020.
[9] F. Liu, Y . Cui, C. Masouros, J. Xu, T. X. Han, Y . C. Eldar, and S. Buzzi,
“Integrated sensing and communications: Toward dual-functional wire-
less networks for 6G and beyond,” IEEE J. Sel. Areas Commun., vol. 40,
no. 6, pp. 1728–1767, June 2022.
[10] T. Mao, J. Chen, Q. Wang, C. Han, Z. Wang, and G. K. Karagiannidis,
“Waveform design for joint sensing and communications in Millimeter-
Wave and low Terahertz bands,” IEEE Trans. Commun., vol. 70, no. 10,
pp. 7023–7039, Oct. 2022.
[11] Z. Wei, H. Qu, Y . Wang, X. Yuan, H. Wu, Y . Du, K. Han, N. Zhang, and
Z. Feng, “Integrated sensing and communication signals toward 5G-A
and 6G: A survey,” IEEE Internet Things J., vol. 10, no. 13, pp. 11 068–
11 092, Jul. 2023.
[12] J. Wang, N. Varshney, C. Gentile, S. Blandino, J. Chuang, and
N. Golmie, “Integrated sensing and communication: Enabling tech-
niques, applications, tools and data sets, standardization, and future
directions,” IEEE Internet Things J. , vol. 9, no. 23, pp. 23 416–23 440,
Dec. 2022.
[13] S. Lu, F. Liu, Y . Li, K. Zhang, H. Huang, J. Zou, X. Li, Y . Dong,
F. Dong, J. Zhu, Y . Xiong, W. Yuan, Y . Cui, and L. Hanzo, “Integrated
sensing and communications: Recent advances and ten open challenges,”
IEEE Internet Things J. , vol. 11, no. 11, pp. 19 094–19 120, Jun. 2024.
[14] H. Lu, Y . Zeng, C. You, Y . Han, J. Zhang, Z. Wang, Z. Dong, S. Jin,
C.-X. Wang, T. Jiang, X. You, and R. Zhang, “A tutorial on near-field
XL-MIMO communications toward 6G,” IEEE Commun. Surveys Tuts.,
vol. 26, no. 4, pp. 2213–2257, early access, Apr. 12, 2024.
[15] X. Mu, J. Xu, Y . Liu, and L. Hanzo, “Reconfigurable intelligent surface-
aided near-field communications for 6G: Opportunities and challenges,”
IEEE Veh. Technol. Mag., vol. 19, no. 1, pp. 65–74, Mar. 2024.
[16] A. V . Savkin, H. Huang, and W. Ni, “Securing UA V communication
in the presence of stationary or mobile eavesdroppers via online 3D
trajectory planning,” IEEE Wireless Commun. Lett. , vol. 9, no. 8, pp.
1211–1215, Aug. 2020.
[17] M. Cui, G. Zhang, Q. Wu, and D. W. K. Ng, “Robust trajectory and
transmit power design for secure UA V communications,” IEEE Trans.
Veh. Technol., vol. 67, no. 9, pp. 9042–9046, Sep. 2018.
[18] Z. Na, C. Ji, B. Lin, and N. Zhang, “Joint optimization of trajectory and
resource allocation in secure UA V relaying communications for Internet
of things,” IEEE Internet Things J. , vol. 9, no. 17, pp. 16 284–16 296,
Sep. 2022.
[19] Y . Zhou, P. L. Yeoh, C. Pan, K. Wang, Z. Ma, B. Vucetic, and Y . Li,
“Caching and UA V friendly jamming for secure communications with
active eavesdropping attacks,”IEEE Trans. Veh. Technol., vol. 71, no. 10,
pp. 11 251–11 256, Oct. 2022.
[20] R. Li, Z. Wei, L. Yang, D. W. K. Ng, J. Yuan, and J. An, “Resource
allocation for secure multi-UA V communication systems with multi-
eavesdropper,” IEEE Trans. Commun. , vol. 68, no. 7, pp. 4490–4506,
Jul. 2020.
[21] S. Li, B. Duo, M. D. Renzo, M. Tao, and X. Yuan, “Robust secure UA V
communications with the aid of reconfigurable intelligent surfaces,”
IEEE Wireless Commun. Lett. , vol. 20, no. 10, pp. 6402–6417, Oct.
2021.
[22] R. Ye, Y . Peng, F. Al-Hazemi, and R. Boutaba, “A robust cooperative
jamming scheme for secure UA V communication via intelligent reflect-
ing surface,” IEEE Trans. Commun., vol. 72, no. 2, pp. 1005–1019, Feb.
2024.
[23] J. Chu, R. Liu, M. Li, Y . Liu, and Q. Liu, “Joint secure transmit beam-
forming designs for integrated sensing and communication systems,”
IEEE Trans. Veh. Technol., vol. 72, no. 4, pp. 4778–4791, Apr. 2023.
[24] Z. Ren, L. Qiu, J. Xu, and D. W. K. Ng, “Robust transmit beamforming
for secure integrated sensing and communication,” IEEE Trans. Com-
mun., vol. 71, no. 9, pp. 5549–5564, Sep. 2023.
[25] N. Su, F. Liu, and C. Masouros, “Sensing-assisted eavesdropper esti-
mation: An ISAC breakthrough in physical layer security,” IEEE Trans.
Wireless Commun., vol. 23, no. 4, pp. 3162–3174, Apr. 2024.
[26] X. Meng, F. Liu, C. Masouros, W. Yuan, Q. Zhang, and Z. Feng,
“Vehicular connectivity on complex trajectories: Roadway-geometry
aware ISAC beam-tracking,” IEEE Trans. Wireless Commun. , vol. 22,
no. 11, pp. 7408–7423, Mar. 2023.
[27] F. Xia, Z. Fei, J. Huang, X. Wang, R. Wang, W. Yuan, and D. W. K. Ng,
“Sensing-enabled predictive beamforming design for RIS-assisted V2I
systems: A deep learning approach,” IEEE Trans. Wireless Commun. ,
vol. 23, no. 6, pp. 5571–5586, Jun. 2024.
[28] Z. Wei, F. Liu, C. Liu, Z. Yang, D. W. K. Ng, and R. Schober, “Integrated
sensing, navigation, and communication for secure UA V networks with
a mobile eavesdropper,” IEEE Trans. Wireless Commun., vol. 23, no. 7,
pp. 7060–7078, Jul. 2024.
[29] X. Cao, A. Chen, H. Yin, and L. Chen, “A low-complexity near-field
localization method based on electric field model,” IEEE Commun. Lett.,
vol. 28, no. 2, pp. 288–292, Dec. 2024.
[30] K. Chen, C. Qi, C.-X. Wang, and G. Y . Li, “Beam training and tracking
for extremely large-scale MIMO communications,”IEEE Trans. Wireless
Commun., vol. 23, no. 5, pp. 5048–5062, May 2024.
[31] D. Galappaththige, S. Zargari, C. Tellambura, and G. Y . Li, “Near-
field ISAC: Beamforming for multi-target detection,” IEEE Wireless
Commun. Lett., vol. 13, no. 7, pp. 1938–1942, Jul. 2024.
[32] Z. Wang, X. Mu, and Y . Liu, “Near-field velocity sensing and predictive
beamforming,” IEEE Trans. Veh. Technol., vol. 74, no. 1, pp. 1806–1810,
Jan. 2025.
[33] A. Sabharwal, P. Schniter, D. Guo, D. W. Bliss, S. Rangarajan, and
R. Wichman, “In-band full-duplex wireless: Challenges and opportuni-
ties,” IEEE J. Sel. Areas Commun. , vol. 32, no. 9, pp. 1637–1652, Sep.
2014.
[34] M. I. Skolnik, Introduction to RADAR systems. Introduction to RADAR
systems, 1990.
[35] Y . Lu and L. Dai, “Near-field channel estimation in mixed LoS/NLoS
environments for extremely large-scale MIMO systems,” IEEE Trans.
Commun., vol. 71, no. 6, pp. 3694–3707, June 2023.
[36] S. K. Sengijpta, “Fundamentals of statistical signal processing: Estima-
tion theory,” Control Engineering Practice, vol. 37, no. 4, pp. 465–466,
1994.
[37] C. Richmond, “Mean-squared error and threshold SNR prediction of
maximum-likelihood signal parameter estimation with estimated colored
noise covariances,” IEEE Trans. Inf. Theory , vol. 52, no. 5, pp. 2146–
2164, May 2006.

<!-- extraction_page_index: 14 -->

14
[38] F. Liu, W. Yuan, C. Masouros, and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: Communication served by sensing,”
IEEE Trans. Wireless Commun. , vol. 19, no. 11, pp. 7704–7719, Nov.
2020.
[39] B. D. O. Anderson, J. B. Moore, and M. Eslami, Optimal Filtering .
Courier Corporation, 2012.
[40] F. Z. Zhang, The Schur Complement and Its Applications . Springer
US, 2005.
[41] A. Ben-Tal and M. Zibulevsky, “Penalty/barrier multiplier methods for
convex programming problems,” SIAM Journal on Optimization ,
vol. 7, no. 2, pp. 347–366, 1997. [Online]. Available:
https://doi.org/10.1137/S1052623493259215
[42] S. Boyd and L. Vandenberghe, Convex optimization. Cambridge, U.K.:
Cambridge Univ. Press, 2004.
[43] S. Li, B. Duo, M. D. Renzo, M. Tao, and X. Yuan, “Robust secure
uav communications with the aid of reconfigurable intelligent surfaces,”
IEEE Trans. Wireless Commun. , vol. 20, no. 10, pp. 6402–6417, Oct.
2021.
[44] M. Grant and S. Boyd, “CVX: Matlab software for disciplined convex
programming, version 2.1,” https://cvxr.com/cvx, Mar. 2014.
