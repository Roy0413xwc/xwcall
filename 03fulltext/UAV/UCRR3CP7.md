---
title: "Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area"
zotero_key: "UCRR3CP7"
pdf_key: "3QMWGJNJ"
doi: "10.1109/TAES.2020.3003104"
collection: "UAV"
note_path: "02vault/UAV/Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area.md"
source: "Zotero PDF full-text cache"
page_mapping: unknown
---

# Ultra-Wideband Air-to-Ground Propagation Channel Characterization — Fulltext

> 由 Zotero PDF 全文缓存归档生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（缓存无 page mapping）。原始 PDF：
> `F:\XWCos\zotero\storage\3QMWGJNJ\Khawaja 等 - 2020 - Ultra-Wideband Air-to-Ground Propagation Channel Characterization in an Open Area.pdf`

---

1
Ultra-Wideband Air-to-Ground Propagation
Channel Characterization in an Open Area
Wahab Khawaja∗, Ozgur Ozdemir∗, Fatih Erden∗, Ismail Guvenc∗, David W. Matolak†
∗Department of Electrical and Computer Engineering, North Carolina State University, Raleigh, NC
†Department of Electrical Engineering, University of South Carolina, Columbia, SC
Email: {wkhawaj, oozdemi, ferden, iguvenc}@ncsu.edu, matolak@cec.sc.edu,
Abstract
This paper studies the air-to-ground (AG) ultra-wideband (UWB) propagation channel through measurements
between 3.1 GHz to 4.8 GHz using unmanned-aerial-vehicles (UAVs). Different line-of-sight (LOS) and obstructed
LOS scenarios and two antenna orientations were used in the experiments. Channel statistics for different propagation
scenarios were obtained, and the Saleh-Valenzuela (SV) model was found to provide a good fit for the statistical
channel model. An analytical path loss model based on antenna gains in the elevation plane is provided for unobstructed
UAV hovering and moving (in a circular path) propagation scenarios.
Index Terms
Air-to-ground (AG), channel model, drone, ultra-wideband (UWB), unmanned-aerial-vehicle (UAV).
I. INTRODUCTION
The use of civilian unmanned-aerial-vehicles (UAVs) for applications such as video recording, surveillance, search
and rescue, and hot spot communications has seen a surge in recent years. Compared to other aerial platforms,
highly mobile UAVs have several advantages, including ease in take-off/landing and operability, multiple varieties
of simple flight controls, small size, and affordable prices. These features make them excellent candidates for
numerous current and future applications. One promising applications is in the field of wireless communications,
e.g., providing on-demand access to hot spot or disaster-hit areas [2], [3]. A recent example was seen in Puerto
Rico, after Hurricane Maria, where a large portion of the cellular infrastructure was damaged. UAVs were used
there by AT&T as base stations to provide cellular coverage [4].
This work has been supported in part by NASA under the Federal Award ID number NNX17AJ94A and by National Science Foundation (NSF)
under the grant number CNS-1453678. Wahab Khawaja has also been supported via a Fulbright scholarship. We also thank Jianlin Chen from
NCSU, for his help in the air-to-ground propagation measurements. This work was presented in part in the IEEE Aerospace Conference, Big
Sky, MT, USA, March 2019 [1].
arXiv:1906.04013v1 [eess.SP] 6 Jun 2019

2
Transmitter
Receiver
Trees Buildings
Tree 30 m
Fig. 1: Channel measurement area from Google Earth.
There are limited studies available on air-to-ground (AG) propagation channel characterization in the literature [2],
[5]; here we cite a few examples. Narrowband AG propagation channel measurements using UAVs in an urban
environment [6] consider a Loo model (Rice and lognormal) for signal amplitude variations. A two-ray path loss
model in an urban environment was observed to fit narrowband measurements carried out in an urban environment
in [7]. Wideband AG propagation channel measurement campaigns in the L-band and C-band were performed for
over water, mountains and hilly area, suburban, and near-urban environments in [8]–[10]. Large scale and small
scale propagation channel statistics and quasi-deterministic channel models were provided. Due to the difficulty of
flying UAVs over populated and high-rise building areas, ray tracing simulations provide an alternative approach for
channel characterization in these settings [11]–[13]. Even with the literature in this area growing, there are limited
AG propagation studies with UAVs in comparison to terrestrial, especially studies that specifically focus on the
antenna radiation pattern effects [11], [14]–[16].
To the best of our knowledge, there are also very few ultra-wideband (UWB) AG propagation channel mea
surements in the literature, except for our previous studies [1], [14], [17]. In these studies, UWB AG propagation
channel measurements and analyses were performed in different propagation environments. This present paper is a
major extension of our previous work in [1]. Here, our new contributions include a new analytical path loss model
for the unobstructed UAV hovering and moving (in a circular path) propagation scenarios. Ray tracing simulations
were also conducted for the unobstructed UAV hovering scenario. In addition, analysis of best fits for the power
delay profiles (PDPs) based on the Saleh-Valenzuela and single exponential models are provided. We also provide
additional channel statistics: the root mean square delay spread (RMS-DS) and Ricean K-factor.
In [17], UWB AG propagation channel characteristics using UAVs were studied in an open area and suburban area
for different propagation scenarios. The empirical data was used to develop a statistical channel model. In [14], the
effect of elevation angle for the received power at different UAV altitudes and antenna orientations were discussed
for UWB propagation in an open area. The gain of the omni-directional dipole antenna in the elevation plane was
modeled as a trigonometric function of elevation angle between the UAV and the ground station (GS). Overall,
the large bandwidth of UWB radio signals allows high temporal resolution of multipath components (MPCs) that

3
can provide detailed impulse response information for a given propagation environment. Studying these MPC
characteristics can help in understanding the AG propagation channel for future broadband communications [2].
In this paper, we report on comprehensive channel measurements in an open area for three conditions: (1)
unobstructed line-of-sight (LOS) path (no foliage) when the UAV is hovering; (2) obstructed line-of-sight (OLOS)
path due to foliage within the link while the UAV is hovering; and, (3) unobstructed LOS path while the UAV is
moving in a circular trajectory. A snapshot of the measurement area from Google Maps is shown in Fig. 1. The
measurements were conducted using different horizontal and vertical distances of the transmitter (TX) on the UAV
to the receivers (RXs) on the ground. Two different antenna orientations, vertical and horizontal (also corresponding
to the linear polarization), were used at the TX, whereas the orientation of the RX antennas was always vertical.
The channel measurements were obtained using Time Domain P440 UWB radios operating in the frequency range
3.1 GHz - 4.8 GHz. All antennas are omni-directional in azimuth.
The main contributions of this AG measurement study can be summarized as follows:
• The received power for the co-polarized antennas is mainly dependent on the antenna gain of the LOS
component in the elevation plane for unobstructed UAV hovering scenario. For this scenario, we provide
an analytical path loss model based on the antenna gain in the elevation plane, and we compare path loss
measurements for this scenario with ray tracing simulation results.
• Antenna orientation mismatch results in higher path loss and RMS-DS, a larger number of weak multipath
components (MPCs), and smaller Ricean K-factor than the co-polarized case. Moreover, the OLOS scenario
introduces additional attenuation and MPCs due to foliage, resulting in further reduction in the K-factor.
• The motion of the UAV in an unobstructed circular path provides mitigation against antenna polarization
mismatch effects in comparison to the unobstructed UAV hovering scenario. These include smaller path loss
and RMS-DS for the unobstructed UAV moving scenario compared to the unobstructed UAV hovering scenario
for the cross-polarized case.
• The Saleh Valenzuela (SV) model is found to provide a better fit for the power delay profile (PDP) than the
single exponential model.
The organization of this paper is as follows. Section II explains the channel measurement setup and experiment
scenarios. Using the data obtained from these experiments, Section III describes channel impulse response (CIR)
characterization, PDP model fitting, and small scale channel statistics. In Section IV, antenna radiation pattern
modeling, received power and path loss modeling are provided. This includes empirical path loss results as well as
results from ray tracing simulations. Finally, Section V concludes the paper.
II. CHANNEL MEASUREMENT SETUP AND EXPERIMENT SCENARIOS
In this section, we describe the channel measurements conducted using Time Domain P440 radios and a DJI
Phantom 4 UAV. The measurements were carried out in an open field close to North Carolina State University’s
Centennial campus. A Google map image of the measurement area is shown in Fig. 1. The three different
measurement scenarios are shown in Fig. 2.

4
RX1 RX2
1.5 m
x={15 m, 30 m}
Horizontal antenna orientation at TX UAV Vertical antenna orientation (downward) at TX UAV
Vertical antenna orientation at GS RXs
Antenna phase center
P440 radios
h={10 m, 20 m, 30 m}
Ground level
(a)
Tree foliage
2m x={15 m, 30 m}
h={10 m, 20 m, 30 m}
Horizontal antenna orientation at TX UAV Vertical antenna Orientation (downward) at TX UAV
Vertical antenna orientation at GS RXs RX1 RX2 Ground level
(b)
RX1 RX2
1.5 m
x={15 m, 30 m}
Horizontal antenna orientation at TX UAV
Vertical antenna orientation (downward) at TX UAV
Vertical antenna orientation at GS RXs
h={10 m, 20 m, 30 m}
Ground level
RXs at the center of the circular UAV trajectory
UAV circular trajectory
(c)
Fig. 2: AG propagation scenarios in an open area for (a) unobstructed UAV hovering, (b) UAV hovering with tree
foliage obstruction, (c) unobstructed UAV moving in a circular trajectory. Radiation patterns of the UWB antennas
are also shown for different antenna orientations.
A. Channel Sounding with Time Domain P440 UWB Radios
Channel sounding equipment is generally very bulky and often requires wired synchronization. This puts a
constraint on the AG propagation channel measurements with conventional channel sounders using UAVs. Therefore,
we used Time Domain P440 radios for UWB channel sounding since they provide easy to set up bi-static channel
measurements. Additionally, no physical connection is required for synchronizing the TX and the RX. A central
synchronizing clock signal is sent from the TX to the RX through packets. A very narrow pulse with approximately
a Gaussian shape in the time domain is used. The duration of each pulse is 1 ns and the repetition interval of the
pulse is 100 MHz, resulting in a scan duration of 100 ns. The pulses are integrated into custom sized packets. The
UAV used for the measurements was a DJI Phantom 4. Using the GS auto-pilot application [18], the UAV flew
exactly at the designated flight coordinates. A snapshot of the measurement environment is shown in Fig. 3.
Due to the coherent operation of TX and RX, the signal to noise ratio (SNR) can be adjusted by changing
the integration duration, i.e., the number of pulses per packet. By increasing the pulse integration period, we can
achieve longer ranges due to higher SNR. This can help in overcoming the power emission limitations by FCC
[19]. However, a larger pulse integration period yields lower data rates, resulting in fewer channel scans captured

5
Receiver at 1.5 m
Receiver on ground
RX2
RX1
Fig. 3: Channel measurements using DJI Phantom UAV and UWB P440 radios at two RX positions (snapshot from
the UAV).
TABLE I: Specifications of channel sounding measurements.
Parameter Parameter value
Operating frequency band 3.1 GHz - 4.8 GHz
Center frequency 3.95 GHz
Pulse duration 1 ns
Dynamic range 48 dB
Pulse repetition rate 10 MHz
Noise figure at RX 4.8 dB
RX sensitivity −104 dBm
RX time bin resolution 1.9073 ps
RX waveform measurements at 32 time bin interval
Communication link Packet communication
Antenna type at TX and RX Planar elliptical dipole
Polarization Vertical
Antenna pattern Omni-directional in
azimuth plane (±1.5 dB)
Voltage standing wave ratio 1.75 : 1
Antenna phase response Linear
in a given timing window. It also requires our channel to be time invariant for a longer period. In our experiment,
we have used a pulse integration of 1024 pulses per packet. This value ensures that we capture channel scans in a
timing window without significant change of the propagation channel and at a reasonable link distance.
In addition to emission requirements by the FCC for UWB, there are two main factors affecting the SNR of the
received signal. These factors limit the extraction of the CIR using the CLEAN algorithm [20], which requires a
given threshold of SNR. First is the preference to use omni-directional antennas instead of directional antennas for
AG communications, and the second is the measurement noise. Omni-directional antennas with small antenna gain

6
0 10 20 30 40 60 70 80 90
50
Delay (ns)
-0.4
-0.8
0
0.4
0.8
Normalized amplitude
Raw received pulses Reconstructed pulses
0 10 20 30 40 50 60 70 80 (b) Time (ns)
-0.33
0
0.33
0.67
1
Normalized CIR
CIR Threshold
90
(a)
0 10 20 30 40 50 60 70 80 90 (a) Time (ns)
-0.4
-0.8
0
0.4
Normalized amp
Raw received pulses Reconstructed pulses
0 10 20 30 40 50 60 70 80 Delay (ns)
-0.33
0
0.33
0.67
1
Normalized CIR
CIR Threshold
90
(b)
Fig. 4: (a) Raw received and reconstructed pulses at the RX, (b) Channel impulse response with respect to delay
obtained from raw received pulses at the RX.
will be affected more by variations in the surrounding environment than will directional antennas. These variations
may also be larger for aerial platforms than for terrestrial. Second, we observed high measurement noise from the
equipment on-board the UAVs themselves in comparison to that observed at the GSs. This is mainly due to noise
generated from the motors and propellers, vibrations on-board the UAV, and possibly other ambient effects, e.g.,
high temperatures experienced on-board the UAV, especially at higher UAV heights during a sunny day. These
factors increase the RX noise, causing more frequent loss of transmitted packets, hence requiring larger coherent
pulse aggregation per packet.
The UWB radios used in the experiment operate in the bi-static mode with a single transmit and receive antenna.
In this mode, the TX continuously sends packets at an inter-packet delay of 10 ms. A rake RX is used with a
delay bin resolution of 1.9073 ps. A standard 32 bin duration is maintained between two measurements i.e., each
measurement sample is processed after 61 ps. The operating frequency range is 3.1 GHz - 4.8 GHz with an effective
bandwidth of 1.7 GHz [21].
The received raw pulses are shown in Fig. 4(a) in blue, whereas the reconstructed pulses shown in red are
obtained by convolving the CIR shown in Fig. 4(b) with the template waveform. The CIR in Fig. 4(b) is obtained
by deconvolving the received pulses with the template waveform. The blue horizontal lines indicate the amplitude
threshold of the MPCs selected at 20% of the peak amplitude. The channel sounding parameters are provided in
Table I.
B. Propagation Scenarios for Measurements
The experiments were designed to explore the UWB AG propagation channel characteristics in a typical open
area. The three propagation scenarios are illustrated in Fig. 2. For the first scenario, there is no obstruction between
the TX and the RX direct path while the UAV is hovering. For the second OLOS scenario, the TX and RXs are
placed such that there is a medium-sized tree of height approximately 8 m between them, as shown in Fig. 2(b). The
branches and leaves of the tree partially obstruct, scatter and diffract the transmitted energy. In the third scenario,
measurements were taken while the UAV was moving in a circle at constant altitude, with RXs at the center. The
velocity of the UAV was set at 6.1 m/s and the TX orientation with respect to the UAV is kept constant (i.e., we

7
do not use any gimbal at the UAV to vary antenna direction). The motion in a circle ensures that distance remains
constant between the TX and the RXs.
In all three propagation scenarios, two antenna orientations were used for the TX on the UAV (vertical and
horizontal, corresponding to the polarization). The antennas at the RXs were always vertically oriented as shown in
Fig. 2. For the first antenna orientation, the TX antenna was aligned vertically such that the antenna boresight (with
phase center in the middle) was facing the boresight of the RX antenna, when Tx and Rx were at the same
height. This co-polarized antenna orientation at the RX and TX is called vertical-vertical and denoted VV. For the
cross-polarized antenna orientation, the TX antenna was rotated 90◦ for a vertical-horizontal (VH) orientation. The
VH antenna orientation was chosen in order to study the effects of the antenna orientation change on the channel
characteristics for highly maneuverable UAVs. For both VV and VH antenna orientation, three UAV heights of
10 m, 20 m, and 30 m at two horizontal distances of x = 15 m and x = 30 m were used. Two RXs, RX1 and
RX2, were placed close to each other at heights of 10 cm and 1.5 m, respectively, from the ground.
III. MODELING THE CHANNEL IMPULSE RESPONSE
In this section, the channel impulse response (CIR) is analyzed. We develop model fits for PDPs and analyze
multipath (small scale) channel statistics, using the measurement data that has been collected as described in
Section II.
A. Channel Impulse Response Model
A generic model for the CIR of a time-varying wireless channel can be written as:
H(n) =
M −1
∑
m=0
αm(n) exp
(
jφm(n)
)
δ
(
n − τm(n)
)
, (1)
where M is the total number of MPCs, αm(n), φm(n) and τm(n) are the amplitude, phase and time of arrival (TOA)
or delay, respectively, of the mth MPC at time instant n. For the UWB propagation channel, we observed clustering
of the MPCs in the time domain due to resolvable reflections from individual scatterers. Therefore, considering
NC clusters and assuming the SV model [22], the CIR expression in (1) can be modified to capture the clustering
behavior as follows: An example CIR is provided in Fig. 4, where we can observe clustered received power as a
function of delay that supports the SV claim.
H(n) =
NC −1
∑
l=0
Ml −1
∑
m=0
αl,m(n) exp
(
jφl,m(n)
)
δ
(
n − Tl(n) − τl,m(n)
)
, (2)
where NC is the total number of clusters, Ml is the total number of MPCs within the lth cluster, αl,m(n), φl,m(n)
and τl,m(n) are the amplitude, phase and arrival times, respectively, of the mth MPC of the lth cluster at time instant
n, and Tl(n) is the arrival time of the lth cluster. For our specific measurements, the channel can be considered
time-invariant since all local scattering objects were motionless, and when the UAV is moving, the velocity is very
small at 6.1 m/s. Therefore, the CIR expression (2) can be simplified as follows:
H(n) =
NC −1
∑
l=0
Ml −1
∑
m=0
αl,m exp
(
jφl,m
)
δ
(
n − Tl − τl,m
)
. (3)

8
The mean square value of the mth MPC of the lth cluster is given in terms of the first MPC as:
α2
l,m = |α0,0|2 exp(−Tlη) exp(−τl,mγl), (4)
where |α0,0|2 is a mean power gain of the first path of the first cluster, and η and γl are the cluster and MPC power
decay constants, respectively. Comparing (1) and (2), the SV model converges to single exponential if γl = 0.
The arrival of the clusters and MPCs within each cluster can be modeled by Poisson processes [22]–[24], with
respective arrival rates, χ and ς observed during the excess delay window. The inter-arrival times of clusters and
MPCs are independent and can be fitted with an exponential distribution function [22] as:
p(Tl|Tl−1) =χ exp
[
− χ(Tl − Tl−1)
]
, (5)
p(τm|τm−1) =ς exp
[
− ς(τm − τm−1)
]
. (6)
B. Analysis of Channel Impulse Response Measurements
In this section, we consider the SV CIR model described in Section III-A for characterizing our AG UWB
channel measurements. The channel model parameters were obtained from the empirical results with the SV
models characterized through (3)–(6) [23]. The statistical propagation channel model parameters obtained from
these equations are provided in Table II, III, and IV for the three scenarios in Fig. 2. It can be observed that the
cluster arrival rate χ captured in (5) is the highest for the unobstructed UAV hovering scenario, followed by foliage
obstructed and unobstructed UAV moving scenarios. Similarly, χ is larger for the VV antenna orientation than for
the VH antenna orientation for all three scenarios at both RXs.
RX1 (VV) RX2 (VV) RX1 (VH) RX2 (VH)
Param. x = 15 m x = 30 m x = 15 m x = 30 m x = 15 m x = 30 m x = 15 m x = 30 m
NC 3.33 4 2.66 2 1.66 2.66 1.66 1.33
χ(1
ns ) .033 .04 .027 .02 .017 .027 .017 .013
η .23 .186 .24 .16 .215 .16 .177 .171
ς(1
ns ) .1 .06 .11 .06 .25 .15 .26 .2
γ 8.7 8.66 5.5 4.3 2.7 5.92 2.8 1.88
TABLE II: UWB UAV channel model parameters averaged over UAV heights for an open area while the UAV is
hovering without obstruction.
The arrival rate of MPCs ς in (6) is the largest for the foliage obstructed scenario. This is attributable to the
multiple reflections from the tree (branches, leaves, and trunk). Similarly, ς is larger for the VH than the VV antenna
orientation at both RX1 and RX2. This is mainly due to a larger number of small powered MPCs for VH antenna
orientation compared to VV antenna orientation.
The average of the cluster power decay constant η from (4) is approximately the same for all the propagation
cases of the three scenarios. The value of η is dependent on the peak power values of the individual clusters. For
example, for the unobstructed UAV hovering scenario, we observe a larger number of peaks contributing to the
overall η due to a larger number of individual clusters. However, for the other two scenarios, we have a single or

9
RX1 (VV) RX2 (VV) RX1 (VH) RX2 (VH)
Param. x = 15 m x = 30 m x = 15 m x = 30 m x = 15 m x = 30 m x = 15 m x = 30 m
NC 2 2 2 1.66 2 1.33 1.66 1.33
χ(1
ns ) .02 .02 .02 .017 .02 .013 .017 .013
η .212 .21 .24 .23 .214 .16 .198 .2
ς(1
ns ) .14 .175 .27 .21 .34 .34 .3 .34
γ 1.3 1.11 .985 1.34 .77 .811 1.4 .74
TABLE III: UWB UAV channel model parameters averaged over UAV heights for open area obstructed by foliage
while the UAV is hovering.
RX1 (VV) RX2 (VV) RX1 (VH) RX2 (VH)
Param. x = 15 m x = 30 m x = 15 m x = 30 m x = 15 m x = 30 m x = 15 m x = 30 m
NC 2 1.66 1.66 1.33 2 1 1.66 1
χ(1
ns ) .02 .017 .017 .013 .02 .01 .017 .01
η .14 .143 .2 .18 .15 .12 .205 .171
ς(1
ns ) .1 .082 .084 .084 .14 .11 .16 .16
γ 1.87 1.87 3.6 5.2 1.76 2 2.04 1.31
TABLE IV: UWB UAV channel model parameters averaged over UAV heights for an open area while the UAV is
moving.
two clusters at maximum, where the peak contribution is mainly from the first cluster. Moreover, we observe higher
η for the VV antenna orientation than for the VH antenna orientation at both RX1 and RX2. This is mainly due
to faster power decay for the VV antenna orientation compared to the VH antenna orientation, where the power
decay is relatively slower. In addition, for the unobstructed UAV moving scenario, we observe the smallest overall
η, showing more uniform received power distribution compared to the other two scenarios.
Interesting observations can be made from the MPC power decay constant, γ of (4), in three different scenarios.
The value of γ is the highest for the unobstructed UAV hovering scenario. The clusters observed in this case are of
short duration with sharp power decay (see Section III-D). In the case of foliage, we observe only a few clusters.
The power from the large duration foliage clusters decays slowly, resulting in overall smaller γ . The value of γ for
the unobstructed UAV moving scenario is in between the other two scenarios. As with the cluster decay constant, γ
is larger for the VV antenna orientation than for the VH antenna orientation for both RXs as there is no dominant
cross-polarized component.
C. Saleh-Valenzuela versus Single Exponential Model PDP Fitting
The PDP is obtained from the CIR as E(|H(n)|2) from [25], where E is the expectation operator. A total of 50
CIRs are collected for each scenario during a fixed time interval of 20 s. In this subsection, we analyze the best

10
0 20 40 60 80 100 Delay (ns)
-70
-60
-50
-40
-30
-20
-10
0
PDP (dB)
(a)
0 20 40 60 80 100 Delay (ns)
-70
-60
-50
-40
-30
-20
-10
0
PDP (dB)
|,0,0|2
e-=l,m.l
e-Tl2
T1 T2
1/@
(b)
Fig. 5: (a) Normalized and averaged empirical PDP, and (b) smoothed version. UAV is hovering at a height of 10 m
and horizontal distance x = 30 m from RX1 with VV antenna orientation. There is no foliage.
fit for the empirical PDPs. The PDP for one of the measurement scenarios1 is shown in Fig. 5. It can be observed
that we have at least three distinct clusters. The cluster identification is performed by visually inspecting the PDP
and make sure each cluster is at least 2.5 ns long (for our 1 ns resolution) and there is an 8 dB change from the
peak of the cluster before the next cluster. These lower bounds ensure distinct classification of the clusters for our
empirical data. The clusters detected using this approach are shown in Fig 5(b). The 2.5 ns duration and 8 dB
decay were chosen to enable identification of distinct clusters and avoid transient effects.
When the power is plotted in dB scale as in Fig. 5, the exponential power decay in the absolute scale becomes
a linear decay. Therefore, the PDP can be fit by a single linear fit (logarithm of the exponential) function or by
the SV model [22], where individual linear fits are assigned for each cluster. Let τl,i and Pl,i (in dB) represent the
delay and power value obtained empirically at the ith data point2 of the lth cluster given as
Pl,i = 10 log10
(
|α0,0|2 exp(−Tlη) exp(−τl,iγl)
)
(7)
for i = 0, 1, 2, . . . , Nl − 1, where Nl is the total number of data points in the lth cluster. Let f (l)(τl,i, β0, β1)
represent the linear fit function for the lth cluster given as
f (l)(τl,i, β0, β1) = β0 + β1τl,i, (8)
where β0 and β1 are the y-intercept and slope of f (l)(·), respectively. Then, the LS error Rl for the lth individual
cluster can be written as follows:
Rl(β0, β1) =
Nl −1
∑
i=0
[
f (l)(τl,i, β0, β1) − Pl,i
]2
, (9)
1For this case the UAV is hovering at a height of 10 m. The horizontal distance between the TX and the RX is x = 30 m and the antenna
orientation is VV.
2Individual data points are not necessarily the MPCs. These data points must be above the given threshold set to be a valid MPC.

11
0 5 10 15 20 Delay (ns)
-60
-50
-40
-30
-20
-10
0
PDP (dB)
Empirical data Single linear fit Saleh Valenzuela fit
(a)
5 10 15 20 Delay (ns)
-80
-70
-60
-50
-40
-30
-20
-10
0
Residual (dB)
Single linear fit Saleh Valenzuela fit
(b)
Fig. 6: (a) Normalized and averaged empirical PDP, linear least square fitted with corresponding Saleh Valenzuela
and single exponential. UAV is hovering at a height of 10 m and horizontal distance x = 30 m from RX1. There is
no foliage and antenna orientation is VV, (b) the absolute value of residuals for single linear and Saleh Valenzuela
fit.
which is the sum of the squared residuals between the linear fit f (l)(τl,i, β0, β1) and corresponding empirical data
point values Pl,i for the lth cluster. Subsequently, the model parameters, (β0, β1) can be extracted by jointly solving
the following equations ∂Rl(β0,β1)
∂β0 = 0 and ∂Rl(β0,β1)
∂β1 = 0.
On the other hand, for the single cluster linear fitting, we have a single linear fit function for all the empirical
data points in the PDP given as f (τi, β′
0, β′
1) = β′
0 + β′
1τi, where β′
0 and β′
1 are the y-intercept and slope of f (·),
respectively, for i = 0, 1, 2, ..., N , where N is the total number of data points in the PDP. For this case, the empirical
data is given as Pi = |αi(τi)|2 and the LS fit is obtained over the N data points. The cluster-based individual linear
fits (based on the SV model) and the single linear fit to the empirical data for one of the propagation scenarios
are shown in Fig. 6(a). The absolute value of the residuals of the two fits is shown in Fig. 6(b). The mean of the
absolute residual for the single linear fit is −23.58 dB, whereas, for the SV model fit it is −24.23 dB. The smaller
mean residual value for the SV model compared to the single linear fit suggests that the SV model provides a better
fit to the empirical PDP than the single linear fit. Similar fittings can be obtained for other propagation scenarios.
D. Multipath Channel Analysis: Power Clusters
A common phenomenon to observe during UWB propagation is the clustered reception of power [26]. In our
outdoor open area environment with few obstacles and modest excess delay, we observe a small number of clusters
in the PDP, as shown in Fig. 5. The clusters are identified by visual inspection, using the distinct boundaries of
power decay and rise discussed in Section III-C. The mean cluster count NC captured in (3), is provided in Tables II,

12
RX1, VV RX2, VV RX1, VH RX2, VH (a) No foliage
10
15
20
25
30
Number of significant MPCs
RX1, VV RX2, VV RX1, VH RX2, VH (b) Foliage
10
15
20
25
30
Number of significant MPCs
RX1, VV RX2, VV RX1, VH RX2, VH (c) Moving
10
15
20
25
30
Number of significant MPCs
Fig. 7: Average number of significant MPCs over multiple channel scans with 95% confidence intervals for (a)
unobstructed UAV hovering, (b) with foliage obstruction, and (c) unobstructed UAV moving on a circle. The
average number of significant MPCs are obtained by averaging over UAV heights at respective horizontal distances
for receiver positions RX1 and RX2 with VV and VH antenna orientations.
III, and IV. The unobstructed UAV hovering scenario has the largest mean cluster count followed by the foliage
obstructed scenario and unobstructed UAV moving scenarios.
In the case of unobstructed UAV hovering without obstruction scenario shown in Fig. 2(a), we observe essentially
independent reflections from small scatterers near the RX, yielding several distinct clusters. However, in the case of
UAV hovering with link obstructed by foliage as shown in Fig. 2(b), usually only 2 clusters are observed: one due
to OLOS (through the foliage) and the second mainly from the tree body (diffraction around the tree crown and
trunk). In addition, in case of foliage, the second cluster time delay is large compared to that in the other scenarios
from the multiple reflections from foliage. In the unobstructed UAV moving scenario shown in Fig. 2(c), we have
a small number of clusters. The UAV moving scenario exhibits fewer clusters, likely due to spatial averaging.
We observe larger mean cluster count for the VV antenna orientation than the VH antenna orientation for all
propagation scenarios: the received power in the VH antenna orientation contains fewer strong reflected components,
and this produces a more uniform distribution in delay than in the VV antenna orientation, hence the smaller VH
cluster count. We also observe larger mean cluster count at RX1 than at RX2, likely due to reflections from the
tripod body. The tripod body provides additional reflections and at the same time may help guide the energy towards
the RX on the ground shown in Fig. 3.

13
RX1,VV RX1,VV RX2,VV RX2,VV (a) No foliage
0
5
10
15
20
25
30
35
40
45
50
55
K-factor (dB)
RX1,VV RX1,VV RX2,VV RX2,VV (b) Foliage
0
5
10
15
20
25
30
35
40
45
50
55
K-factor (dB)
RX1,VV RX1,VV RX2,VV RX2,VV (c) Moving
0
5
10
15
20
25
30
35
40
45
50
55
K-factor (dB)
x=15 m
x=30 m
x=15 m
x=30 m x=15 m x=30 m
x=15 m
x=15 m x=30 m
x=30 m
x=15 m x=30 m
Fig. 8: A box plot of Ricean K-factor for VV antenna orientation. Each box (bounded between the 25th and 75th
percentile and median in the center) represents the K-factor variation at all three UAV heights for (i) unobstructed
UAV hovering, (ii) with foliage obstruction, and (iii) unobstructed UAV moving on a circle. The outliers are indicated
by red + sign.
E. Multipath Channel Analysis: Number of Significant MPCs
We obtained the number of significant MPCs by retaining only the MPCs that were above the threshold of
20% of the maximum MPC amplitude for a given CIR. These significant MPCs are counted for every scan of a
given scenario. Then, they are averaged over the three UAV heights and two horizontal distances of x = 15 m
and x = 30 m of a given scenario. The plot of the average number of significant MPCs with 95% confidence
intervals for the three flight conditions is shown in Fig. 7. It can be observed that we have a larger number of
significant MPCs for VH antenna orientation than for the VV antenna orientation. This is because the low powered
cross-polarized components are relatively larger when there is no LOS component than the longer-delayed MPCs
in the presence of a dominant co-polarized LOS component.
We observe the largest number of significant MPCs for the foliage obstructed scenario. On the other hand, we
have the smallest number of significant MPCs for the unobstructed UAV moving and hovering scenarios with VV
antenna orientation. This is because the presence of the dominant LOS component means that only a small number
of large power MPCs exceed our threshold. We also observe a larger number of MPCs for RX2 than for RX1
because of RX2’s better ground clearance. The potential scatterers near the RXs that provided the MPCs are the
tripod, measuring equipment, two humans, and nearby chairs.
F. Multipath Channel Analysis: K-factor
The Ricean K-factor is obtained using the well-known equation, K = 10 log10
A2
2σ2 , where A2 is the power of
the LOS component. The LOS component is obtained as the first arriving component of the received waveform
with highest power. The σ2 term represents the power of the remaining MPCs, whose distribution is assumed

14
Rayleigh. The Ricean K-factor at RX1 and RX2 for VV antenna orientations and different propagation scenarios
is shown in Fig. 8. Each box (bounded between the 25th and 75th percentile with median in the center) represents
the K-factor variation at all three UAV heights. The K-factor is not evaluated for VH antenna orientation due to
weaker or absent LOS component in the channel scans. It can be observed that we have smaller mean K-factor
for the foliage obstructed scenario than for the unobstructed scenarios, due to a weaker LOS component and larger
number of MPCs for the foliage obstructed scenario. Moreover, for the UAV moving scenario, the K-factor has
higher mean than the other two scenarios and the K-factor varies less than in the to other scenarios. The larger
value of K-factor for the moving scenario is likely attributable to some of the spatial averaging of the MPCs during
the circular motion around the fixed receiver position.
G. Multipath Channel Analysis: Temporal Dispersion
Temporal dispersion of the propagation channel is quantified using the RMS-DS represented as τrms. The RMS
DS is computed using the PDP as follows [17]:
τrms =
√ √ √ √
∑
∀n(nTs)2∣
∣H (n)
∣ ∣
2
∑
∀n
∣
∣H (n)
∣ ∣
2−
(∑
∀n nTs
∣
∣H (n)
∣ ∣
2
∑
∀n
∣
∣H (n)
∣ ∣
2
)2
, (10)
where the second term represents the square of the mean delay and Ts is the sampling duration (0.06 ns). The plot
of RMS-DS averaged over the channel scans is shown in Fig. 9. A general trend observed is that the RMS-DS
increases with the height of the UAV (increases with link distance). Overall, we observe a slightly larger mean
RMS-DS at RX1 on the ground than RX2 at 1.5 m height, for all three propagation scenarios for both VV and
VH antenna orientations. Also, larger RMS-DS is observed for the VH antenna orientation than the VV antenna
orientation at both receiver locations and all three propagation scenarios. As noted, this can be attributed to a weaker
dominant component in the VH case as observed in Section III-E.
Overall, for the VV antenna orientation at RX1 and RX2, we observe larger RMS-DS for the unobstructed UAV
moving scenario than for the unobstructed UAV hovering scenario shown in Fig. 9(c) and (a), respectively. This is
likely due to a larger number of MPCs at larger delays arising from different parts of the nearby scatterers during
motion. Similarly, for the foliage obstructed scenario shown in Fig. 9(b), we observe the highest mean RMS-DS–as
noted, likely due to additional MPCs from the foliage. Contrary to the other two scenarios, we observe a larger
mean RMS-DS for the foliage obstructed scenario at RX2 than at RX1, likely because a larger number of MPCs
are captured from the foliage with the better ground clearance position (see Section III-E).
A comparison of the VH antenna orientation with VV antenna orientation reveals that we have a smaller effect of
the antenna orientation change on the RMS-DS for foliage obstructed and unobstructed UAV moving scenarios (as
observed in Section IV-F also). Moreover, similar to the VV antenna orientation, we observe a larger difference
in RMS-DS between x = 15 m and x = 30 m for RX2 than for RX1 for the unobstructed UAV hovering and
unobstructed UAV moving scenarios due to the better ground clearance. In addition, for the VH antenna orientation,
we observe larger mean RMS-DS for the unobstructed UAV hovering scenario than the unobstructed UAV moving
scenario at both RX1 and RX2. This can be attributed to spatial averaging of small powered diffuse MPCs during

15
10 20 30 UAV height (m)
0
5
10
15
20
25
RMS-DS (ns)
x = 15 m, VV x = 30 m, VV x = 15 m, VH x = 30 m, VH
10 20 30 UAV height (m)
0
5
10
15
20
25
RMS-DS (ns)
x = 15 m, VV x = 30 m, VV x = 15 m, VH x = 30 m, VH
RX1 RX2
VH
VV
VH
VV
(a) Unobstructed UAV hovering.
10 20 30 UAV height (m)
0
5
10
15
20
25
RMS-DS (ns)
x = 15 m, VV x = 30 m, VV x = 15 m, VH x = 30 m, VH
10 20 30 UAV height (m)
0
5
10
15
20
25
RMS-DS (ns)
x = 15 m, VV x = 30 m, VV x = 15 m, VH x = 30 m, VH
RX1 RX2
VV
VH
VV
VH
(b) Foliage obstructed UAV hovering.
10 20 30 UAV height (m)
0
5
10
15
20
25
RMS-DS (ns)
x = 15 m, VV x = 30 m, VV x = 15 m, VH x = 30 m, VH
10 20 30 UAV height (m)
0
5
10
15
20
25
RMS-DS (ns)
x = 15 m, VV x = 30 m, VV x = 15 m, VH x = 30 m, VH
RX1 RX2
VV
VH
VH
VV
(c) Unobstructed UAV moving.
Fig. 9: RMS-DS obtained from measurements at RX1 placed on ground (left) and RX2 at 1.5 m above the
ground (right) for (a) unobstructed UAV hovering scenario, (b) foliage obstructed UAV hovering scenario, (c)
unobstructed UAV moving scenario.

16
Azimuth plane
Elevation plane
(a) (b)
Fig. 10: Antenna radiation pattern at 4 GHz [21], (a) in the azimuth and elevation planes with directional vector
at a given elevation angle, (b) in the elevation plane for the transmitter on the UAV and receiver on the ground
station.
the motion for VH antenna orientation. This averaging may yield a smaller number of MPCs at respective delays
compared to the unobstructed UAV hovering scenario for VH antenna orientation.
IV. MODELING RECEIVED POWER AND PROPAGATION PATH LOSS
In this section, we model the antenna gain in the elevation plane, analyze the polarization mismatch losses, and
provide an analytical model for the received power and path loss for the unobstructed UAV hovering and moving
scenarios. Empirical and analytical path loss results are provided. We also describe our ray tracing simulation setup
and simulated path loss results for the unobstructed UAV hovering scenario.
A. Antenna Gain Modeling and Polarization Mismatch Losses
BroadSpec UWB antennas from Time Domain Inc. [21] were used in the experiments at both the TX and the
RX. These antennas are planar elliptical dipoles with omni-directional pattern in the azimuth plane and a typical
doughnut pattern in the vertical plane, shown in Fig. 10(a). The parameters of the antennas are provided in Table I.
The vector ~r in Fig. 10(a) represents the direction of the link in the elevation plane at a given elevation angle θ
given by, θ = tan−1
(x h
)
, where x represents the horizontal distance between the RX and the TX, and h represents
the height of the UAV.
In AG propagation, it is important to consider the antenna radiation pattern in three dimensions [2]. The antenna
radiation pattern in the elevation plane plays a key role in determining the received power, especially at higher
elevation angles. The elevation angle is defined between the horizontal and a direct line connecting TX to RX (along
the LOS component, if present). The link in Fig. 10(b) represents the LOS component from the phase center of

17
0 50 100 150 200 250 300 350 Angle (deg.)
-30
-25
-20
-15
-10
-5
0
Normalized gain (dB)
Elevation plane gain Absolute sine function
Fig. 11: Comparison of normalized antenna gain at 4 GHz in the elevation plane with the absolute sine function.
the TX antenna to the RX antenna. This LOS component makes an angle θ with the vertical axis. The antenna
radiation pattern is approximately symmetrical around the vertical axis as shown by the red circles in Fig. 10(b).
Therefore, the antenna gain for the LOS component in the elevation plane can be approximated by an absolute
sine trigonometric function, i.e., sin θ. Comparison of the antenna gain at 4 GHz in the elevation plane from
manufacturer’s specification [21] with the absolute sine function sin θ over an angular span of [0 180◦] is provided
in Fig. 11. From Fig. 11, we can observe that a sine function with larger exponent value can even provide a better fit.
However, as the operating frequency covers a large band, the pattern of the antenna radiation at different frequencies
is not the same (see [14]). Therefore, sin θ with larger exponent value does not always provide a good fit. Instead,
sin θ provides an overall better fit for antenna gain in the elevation plane over the whole frequency range. For
the VV antenna orientation, the overall antenna gain for the LOS component can be approximated as sin θ over
the elevation angle range of 0◦ to 180◦. Hence, as θ decreases (an increase of elevation), the LOS component is
attenuated accordingly.
Similarly, for the ground reflected component (GRC), the gain of the antenna in the elevation plane is given
by sin Ω and sin Ω′ at the RX and TX respectively, from Fig. 12. Therefore, the combined TX/RX antenna gain
of the GRC for the VV antenna orientation is given by
√
sin Ω sin Ω′. On the other hand, for the VH antenna
orientation, we have a weak (or absent) LOS component and most of the propagation is non-line-of-sight (NLOS),
due to reflections from surrounding objects.
In order to quantify the polarization mismatch, let ρρρ(TX) and ρρρ(RX) represent the unit vectors for the electric fields
at the TX and RX antennas, respectively. At the RX antenna, we have ρρρ(TX) · ρρρ(RX), where (·) represents the dot
product between the two unit vectors. If the direction of the electric field planes (for incident and receiver) are similar,
there is no polarization mismatch and the dot product is 1. However, for the VH antenna orientation, the incident
and received electric field planes will be orthogonal [27], [28]. In an ideal case, the VH antenna orientation should
yield no reception for the linearly polarized antennas. However, due to non-ideal cross-polarization discrimination

18
h
hRX
TX
RX2
d0’
d11
d12
d1 = d11 + d12
x
hRX hRX
Ψ + 90o
d12
LOS
GRC
θ’
θ’ = 90 - tan-1((h-hRX)/x)
= tan-1((h+hRX)/x)
Ψ
Ω=
Ψ
Ω’
Ω’ = 90- Ψ
Ground
Fig. 12: Received signal components of line-of-sight and ground-reflected component at RX2.
and due to reflections from scatterers in the environment, cross-polarized components appear. These components
enable reception for the VH antenna orientation.
B. Received Power Modeling using LOS and GRC Paths
If S(n) is the transmitted signal, then the received signal is given by R(n) = S(n) ~ H(n), where ~ is the
convolution operation and H(n) is as defined in (3). If there are M paths in the propagation channel, then the
received signal consists of M MPCs, and each MPC can be represented as Rm(n) given by [25], [29]:
Rm(n) =
[ λΓm(φm, θm) 4πdm
√
GT
(
φ(TX)
m , θ(TX)
m
)
GR
(
φ(RX)
m , θ(RX)
m
)
s(n − τm) exp
( −j2πdm λ
)∣ ∣
∣ρρρ(TX)
m · ρρρ(RX)
m
∣ ∣ ∣
]
,
(11)
where m = 0, 1, 2, . . . , M with m = 0 representing the LOS component, λ is the wavelength of the transmitted
signal, Γm(φm, θm) is the reflection coefficient of the mth component with φm and θm being the azimuth and
elevation angles of the received components with respect to the scatterers (considering first order reflections),
GT(φ(TX)
m , θ(TX)
m ) is the gain of the antenna at the TX at respective azimuth and elevation angles of departures,
GR(φ(RX)
m , θ(RX)
m ) is the gain of the antenna at the RX at respective azimuth and elevation angles of arrivals,
∣ ∣
∣ρρρ(TX)
m · ρρρ(RX)
m
∣ ∣
∣ is the polarization mismatch loss factor for the mth MPC [28], and finally τm and dm are the delay
and distance of the mth component, respectively. We use the terms reflection and scattering mostly interchangeably
here, understanding that these represent distinct physical propagation mechanisms; their aggregate effect is captured
by Γ in our formulation.
For the LOS component Γ0(φ0, θ0) = 1, and the distance of the path between the TX and RX will be d0, shown
in Fig. 10(b). Similarly, τ0 = 0 for the LOS component in our case. As noted the gain of the antenna for the

19
LOS component can be approximated by the trigonometric function described in Section IV-A. Therefore, the LOS
received component can be represented as follows:
R0(n) =
[λ
4πd0
sin θs(n) exp
( −j2πd0 λ
)∣ ∣
∣ρρρ(TX)
0 · ρρρ(RX)
0
∣ ∣ ∣
]
. (12)
Similarly, the GRC can be represented as,
R1(n) =
[ λΓ1(φ1, θ1) 4πd1
√
sin Ω sin Ω′s(n − τ1) exp
( −j2πd1 λ
)∣ ∣
∣ρρρ(TX)
1 · ρρρ(RX)
1
∣ ∣ ∣
]
. (13)
If E represents the average over time, the total received power PR, as the sum of the powers of all the received
MPCs is given as:
PR = E
[
∣
∣R0(n)
∣ ∣
2
]
+E
[ M−1
∑
m=1
∣
∣Rm(n)
∣ ∣
2
]
, (14)
where m = 1 refers to the GRC.
C. Path Loss Modeling for Unobstructed UAV Hovering Scenario, VV
The path loss is obtained by comparing the received power at a given distance with the received power at the
reference distance. First, the received power is obtained at 1 m distance when the antennas are aligned boresight
to each other and at the same height of 1 m above the ground. Then, the received power at different distances is
compared with that at the reference distance. Let us first consider the unobstructed UAV hovering scenario with
VV antenna orientation at RX1 and RX2 shown in Fig. 2(a). For RX1, we consider that the received power is
mainly from the dominant LOS component for different UAV distances as discussed in Section IV-B. Moreover,
for simplicity, we consider the polarization mismatch loss factor from (12) equal to 1 for the LOS component.
Therefore, from (12) and (14), the received power for the LOS components P (LOS)
R,d0 at different UAV distances can
be written as,
P (LOS)
R,d0 = PT sin2 θλ2
(
4πd0
)2 , (15)
whereas the received power P (LOS)
R,dref at a reference distance dref = 1 m, can be written as:
P (LOS)
R,dref = PTλ2
(
4π
)2 , (16)
where PT = E
[
|s(n)|2]
is the transmitted power, θ = tan−1 ( x
h
)
, and distance d0 =
√
x2 + h2 is from Fig. 10(b).
Additionally, the antenna gains at the TX and RX sides at a reference distance of 1 m are approximated as 1 (0 dB)
which is the maximum antenna gain in the far field at the boresight alignment of the antennas. Using the close-in
free space path loss model [30], the path loss (in dB) can be represented as:
L(d) [dB] = 10 log10 L(dref ) + 10 log10
PR,dref
PR,d
, (17)

20
where 10 log10 L(dref ) is the free space path loss (in dB) at the reference distance, L(dref ) = ( 4πdref
λ )2 [30], and λ
corresponds to the wavelength at the center of the UWB signal spectrum. Therefore, at RX1, the path loss for VV
antenna orientation can be approximated based on the LOS component only (15) as follows:
L(VV)(d0) [dB] = 10 log10 L(dref ) + 10 log10
d2
0
sin2 θ
= 10 log10 L(dref ) + 10 log10
x2 + h2
[
sin
(
tan−1 ( x
h
)
)
]2 . (18)
The path loss at RX2 is calculated in a similar way. However, at RX2, in addition to the LOS component, we
have a dominant GRC due to the height of the RX above the ground as shown in Fig. 12. Due to the large temporal
resolution of the transmitted signal, the GRC and the LOS component can be resolved. Therefore, from (12) and
(13), the overall received power can be approximated as:
PR =P (LOS)
R + P (GRC)
R
PR = PTG(LOS)
T (φ(TX)
0 , θ(TX)
0 )G(LOS)
R (φ(RX)
0 , θ(RX)
0 )λ2 (4πd′
0)2 +
PTG(GRC)
T (φ(TX)
1 , θ(TX)
1 )G(GRC)
R (φ(RX)
1 , θ(RX)
1 )λ2|Γ1(φ1, θ1)|2 (4πd1)2
∣ ∣
∣ρρρ(TX)
1 · ρρρ(RX)
1
∣ ∣ ∣
2
,
(19)
where from Fig. 12, we have d′
0=
√
(h − hRX)2 + x2, d1 =
√
(h + hRX)2 + x2, and Γ1(φ1, θ1) = Γ1(Ψ). The
elevation angle of the GRC at the TX and RX is represented as Ω′ and Ω, respectively. The angle of the LOS
component is also modified as θ′ due to the height of the receiver above the ground. Moreover, the value of
∣ ∣
∣ρρρ(TX)
1 · ρρρ(RX)
1
∣ ∣ ∣
2
is approximated as 1, similar to the LOS component. Therefore, considering only the LOS and
GRC paths, the path loss for RX2 from (17) is given as follows:
L(VV)(d′
0, d1) [dB] =10 log10 L(dref ) + 10 log10
(d′
0d1)2 (d1 sin θ′)2 + (d′2
0 sin Ω sin Ω′)|Γ1(Ψ)|2 . (20)
These analytical path loss results at RX1 and RX2 will be compared with measurements in Section IV-F.
D. Path Loss Modeling for Unobstructed UAV Moving Scenario, VV
The path loss for the unobstructed UAV moving scenario with VV antenna orientation can be modeled in a
similar way as for the unobstructed UAV hovering scenario. However, the effect of the antenna gain is different at
the TX and the RX. At the TX, mounted on the UAV, the antenna’s boresight during motion is fixed with respect to
the RXs on the ground. Therefore, the TX antenna gain can be modeled with sin θ, same as for the UAV hovering
scenario. On the other hand, the gain of the RX antennas on the ground is not fixed during the UAV motion. This is
because the gain of the antenna is not the same at a given elevation point in space around the antenna. However, due
to circular motion around the RX, the overall RX antenna gain can be approximated with a mean value represented
as, G(c)
R . Therefore, the received power for the LOS component at RX1 for UAV moving scenario is given as:
P (LOS)
R,d0 = PT sin θG(c)
R λ2
(
4πd0
)2 . (21)

21
The path loss at RX1 when the UAV is moving can therefore be represented as:
L(VV)(d0) [dB] = 10 log10 L(dref ) + 10 log10
d2
0
sin
(
tan−1 ( x
h
)
)
G(c)
R
. (22)
Similar to RX1, the path loss at RX2 when the UAV is moving can be represented as
L(VV)(d′
0, d1) [dB] =
10 log10 L(dref ) + 10 log10
(d′
0d1)2
d2
1 sin θ′G(c)
R + d′2
0 sin Ω′G(c)
R |Γ1(Ψ)|2 .
(23)
These analytical results will be compared with measurements in Section IV-F.
The path loss for the foliage scenario remains essentially constant for different UAV heights and horizontal
distances as the LOS path is blocked by the foliage. There are small variations of the received power (due to weak
MPCs) versus link distances, however, the logarithm smooths these variations resulting in an approximately constant
path loss. The reason for this constant value is due to the limitation of the equipment to measure the minimum
received power during obstruction, i.e., a limited dynamic range.
E. Path Loss Modeling for Unobstructed UAV Hovering and Moving Scenarios, VH
The polarization mismatch loss for the VH antenna orientation can be estimated empirically. In order to obtain
this estimate, the received power measurements with VH antenna orientation are compared with the respective
measurements with VV antenna orientation. Since the channel is assumed to be stationary and the received power
is mainly dependent on the dominant LOS component, from (12) and (14), the only variable quantity for VH
antenna orientation compared to VV antenna orientation is (ρρρ(TX)
0 · ρρρ(RX)
0 ). The polarization mismatch loss factor
ratio cpol between the VH and VV antenna orientation scenarios can be represented as:
cpol = |ρρρ(TX,VH)
0 · ρρρ(RX,VH)
0 |2
|ρρρ(TX,VV)
0 · ρρρ(RX,VV)
0 |2 , (24)
where ρρρ(TX,VH)
0 , ρρρ(TX,VV)
0 , ρρρ(RX,VH)
0 , ρρρ(RX,VV)
0 are the polarization unit vectors for VH and VV antenna orien
tations at the TX and the RX, respectively. Note that we have already approximated |ρρρ(TX,VV)
0 · ρρρ(RX,VV)
0 |2 = 1,
meaning that there is no polarization mismatch for the LOS component. Therefore, we can write (24) as, cpol =
|ρρρ(TX,VH)
0 · ρρρ(RX,VH)
0 |2 and this provides an estimate of the overall reduction in the received power (or increase in
the path loss) when the orientation of the antennas is changed from VV to VH.
Using (24), we can find the analytical path loss for the UAV hovering and moving scenarios with VH antenna
orientation. If cpol represents the polarization mismatch loss for a given VH antenna orientation scenario, then the
corresponding path loss is given as
L(VH)(d0) [dB] = L(VV)(d0) [dB] + 10 log10(cpol). (25)
The path loss at RX2 is obtained in a similar way. These results will be compared with measurements in Section IV-F.

22
10 20 30 UAV height (m)
66
68
70
72
74
76
78
80
82
84
Path loss (dB)
x=15 m, free space x=30 m, free space x=15 m, VV, measurement x=30 m, VV, measurement x=15 m, VV, analytical x=30 m, VV, analytical
10 20 30 UAV height (m)
66
68
70
72
74
76
78
80
82
84
Path loss (dB)
x=15 m, free space x=30 m, free space x=15 m, VV, measurement x=30 m, VV, measurement x=15 m, VV, analytical x=30 m, VV, analytical
RX1 RX2
(a) Unobstructed UAV hovering.
10 20 30 UAV height (m)
66
68
70
72
74
76
78
80
82
84
Path loss (dB)
x=15 m, VV, measurement x=30 m, VV, measurement
10 20 30 UAV height (m)
66
68
70
72
74
76
78
80
82
84
Path loss (dB)
x=15 m, VV, measurement x=30 m, VV, measurement
RX1 RX2
(b) Foliage obstructed UAV hovering.
10 20 30 UAV height (m)
66
68
70
72
74
76
78
80
82
84
Path loss (dB)
x=15 m, free space x=30 m, free space x=15 m, VV, measurement x=30 m, VV, measurement x=15 m, VV, analytical x=30 m, VV, analytical
10 20 30 UAV height (m)
66
68
70
72
74
76
78
80
82
84
Path loss (dB)
x=15 m, free space x=30 m, free space x=15 m, VV, measurement x=30 m, VV, measurement x=15 m, VV, analytical x=30 m, VV, analytical
RX1 RX2
(c) Unobstructed UAV moving.
Fig. 13: Path loss obtained from free space, measurements and analytical modeling for VV antenna orientation at
RX1 placed on ground (left) and RX2 at 1.5 m above the ground (right) for (a) unobstructed UAV hovering, (c)
unobstructed UAV moving. The measurement results for UAV hovering with foliage obstruction are shown in (b).

23
10 20 30 UAV height (m)
70
72
74
76
78
80
82
84
86
88
Path loss (dB)
x=15 m, VH, measurement x=30 m, VH, measurement x=15 m, VH, analytical x=30 m, VH, analytical
10 20 30 UAV height (m)
70
72
74
76
78
80
82
84
86
88
Path loss (dB)
x=15 m, VH, measurement x=30 m, VH, measurement x=15 m, VH, analytical x=30 m, VH, analytical
RX1 RX2
(a) Unobstructed UAV hovering.
10 20 30 UAV height (m)
70
72
74
76
78
80
82
84
86
88
Path loss (dB)
x=15 m, VH, measurement x=30 m, VH, measurement
10 20 30 UAV height (m)
70
72
74
76
78
80
82
84
86
88
Path loss (dB)
x=15 m, VH, measurement x=30 m, VH, measurement
RX1 RX2
(b) Foliage obstructed UAV hovering.
10 20 30 UAV height (m)
70
72
74
76
78
80
82
84
86
88
Path loss (dB)
x=15 m, VH, measurement x=30 m, VH, measurement x=15 m, VH, analytical x=30 m, VH, analytical
10 20 30 UAV height (m)
70
72
74
76
78
80
82
84
86
88
Path loss (dB)
x=15 m, VH, measurement x=30 m, VH, measurement x=15 m, VH, analytical x=30 m, VH, analytical
RX1 RX2
(c) Unobstructed UAV moving.
Fig. 14: Path loss obtained from free space, measurements and analytical modeling for VH antenna orientation at
RX1 placed on ground (left) and RX2 at 1.5 m above the ground (right) for (a) unobstructed UAV hovering, (c)
unobstructed UAV moving. The measurement results for UAV hovering with foliage obstruction are shown in (b).

24
F. Empirical and Analytical Path Loss Results
In this subsection, we first provide empirical path loss results, shown in Fig. 13 and Fig. 14 for VV and VH
antenna orientations, respectively. Subsequently we compare the analytical results from Section IV-C, IV-D and IV-E
with measurement results. Free space path loss calculated at the center frequency of 3.95 GHz for co-polarization
is also provided for comparison.
Fig. 13 shows the path loss for the three propagation scenarios at RX1 and RX2 for VV antenna orientation. At
RX1, for the unobstructed UAV hovering scenario shown in Fig. 13(a), we observe higher path loss at UAV height
of 10 m for x = 30 m than for x = 15 m due to larger link distance. However, as the UAV height increases, the
path loss at x = 15 m increases faster than that at x = 30 m. As a result, the path loss at UAV height of 30 m
becomes larger for the UAV at x = 15 m than at x = 30 m. This increase in the path loss is due to the smaller
antenna gain at higher elevation angles as discussed in Section IV-A, and results in the two curves for VV crossing
each other as the UAV height increases. Similar observations were made at RX2 for this scenario. This is a critical
observation, since larger path loss can be observed at shorter distance due to antenna effects and TX/RX geometry.
The path loss for unobstructed UAV moving scenario and VV antenna orientation is shown Fig. 13(c). Here we
observe closely spaced curves. This can be explained by considering the antenna gain in the azimuth plane, shown
in Fig. 10(a). Due to the motion of the UAV in a circular path, the RX antenna gain will change continuously in
the azimuth and elevation planes. In the azimuth plane, the gain of the antenna is smaller at 0◦ and 180◦. Similarly,
the antenna gain in the elevation plane has slightly larger values at certain elevation angles, as can be observed in
Fig. 11. However, considering a large number of samples of the antenna gain pattern in the elevation plane forming
the overall three dimensional pattern, the antenna gain variations in the elevation plane are somewhat averaged
out by the UAV motion. This phenomenon leads to closely spaced path loss curves for unobstructed UAV moving
scenario at x = 15 m and x = 30 m for three UAV heights. Similar observations can be made at RX2.
The path loss results for VH antenna orientation are shown in Fig. 14 for RX1 and RX2. The path loss here is
larger than the VV antenna orientation at RX1 and RX2 due to polarization mismatch as discussed in Section IV-A.
Hence the effect of the antenna gain in the elevation plane is negligible compared to that in the VV antenna
orientation. An interesting observation is that the polarization mismatch has a smaller effect for the unobstructed
UAV moving scenario than for the unobstructed UAV hovering scenario. This is due to a larger number of cross
polarized components arising during the UAV motion than when the UAV is hovering, and also suppression of the
dominant LOS component. For VH antenna orientation, the boresight of the antenna is facing the ground (direction
of “azimuth” emission) shown in Fig. 2. Thus the ground and any ground-based scattering objects are illuminated and
additional components reach the RXs. The motion of the UAV results in more cross-polarized components (assuming
the ground surface is not uniform) than when the UAV is hovering. This results in higher received power. This
phenomenon is more evident at x = 15 m than at x = 30 m. The weak cross-polarized components generated at
x = 15 m are stronger than at x = 30 m.
The path loss for unobstructed UAV hovering scenario shows the largest change experienced due to antenna
orientation misalignment VH compared to aligned VV shown in Fig. 14(a). In contrast, for the foliage obstructed

25
UAV hovering scenario shown in Fig. 14(b), the path loss approximately remains constant. This is because of the
obstruction of the dominant LOS path which carries the largest power – significantly larger (approximately 20 dB)
than the other MPCs. The path loss for the foliage obstructed scenario does not show any significant effect of antenna
orientation or link distance for either RX1 or RX2. The path loss only shows a change at RX1 for UAV height of
10 m at x = 15 m. This is likely due to the smaller obstruction (thin tree trunk) experienced by the RX placed on
the ground from the low altitude UAV. However, for RX2, and larger UAV heights, the tree crown obstructs the
path. Moreover, at a horizontal distance of x = 30 m, the visibility of the RXs from the UAV become better, yet,
the path loss is larger because of larger link distance. Therefore, path loss remains approximately constant.
In addition to link distance d between the GS and the UAV, the path loss is dependent on the elevation angle
between the TX and the RX (12), and antenna orientation–see Section IV-A. The larger the elevation angle and
orientation mismatch, the greater the path loss. This effect is more prominent when the antennas have the same
orientation. Moreover, the foliage introduces additional path loss due to partial obstruction of the LOS component.
We also note that the path loss at RX1 is larger than at RX2 for the unobstructed UAV hovering and unobstructed
UAV moving scenarios for both VV and VH antenna orientations. This is attributable to antenna deformation at
RX1. RX2 has better ground clearance than RX1.
The path loss results obtained using the analytical modeling for unobstructed UAV hovering and moving sce
narios (discussed in Section IV-C, IV-D and IV-E) are shown in Fig. 13 and Fig. 14 alongside the measurement
results. The value of |Γ1(Ψ)| is obtained from [31], for vertical polarization and relative permittivity of 35 for the
grassy ground surface at respective grazing angles. The value of |Γ1(Ψ)| is provided in Table V and is same for
both UAV hovering and moving scenarios. The value of |cpol| from Section IV-E, for different propagation scenario
settings is also shown in Table V. The value of the receiver antenna gain G(c)
R , for unobstructed UAV moving
scenario (discussed in Section IV-D) is taken as 0.5. Comparing the analytical results with the empirical results
we observe slightly larger path loss for the analytical results. This is mainly due to considering only the LOS
component for RX1, and LOS and GRC for RX2 and ignoring the other MPCs in the analytical modeling. Overall,
we observe a reasonably close match between the empirical results and our analytical results that incorporate 3D
antenna radiation effects.
RX1 (VV), x = 15 m RX1 (VV), x = 30 m RX2 (VV), x = 15 m RX2 (VV), x = 30 m
Param. h=10 m h=20 m h=30 m h=10 m h=20 m h=30 m h=10 m h=20 m h=30 m h=10 m h=20 m h=30 m
|Γ1(Ψ)| - - - - - - 0.59 0.67 0.7 0.39 0.57 0.64
|cpol| [dB]
“(UAV hovering)”
12.9 7.3 5.6 8 6.3 6.0 11.2 8.2 5.7 11.3 8.8 8.0
|cpol| [dB]
“(UAV moving)”
0.6 0.4 2 5.4 4.6 4.3 1.8 0.7 2.2 5.8 2.5 4.1
TABLE V: Ground reflection coefficient, |Γ1(Ψ)|, and polarization mismatch loss factor ratio, |cpol|, values obtained
from measurement data. The value of |cpol|, for unobstructed UAV hovering scenario and UAV moving scenario.

26
RXs
TX, h=30 m, x={15 m, 30 m}
Trees
Buildings
Fig. 15: The simulation setup of the measurements created using Wireless InSite (ray tracing software).
10 20 30 UAV height (m)
60
65
70
75
80
85
90
95
100
105
110
Path loss (dB)
x=15 m, VV, ray tracing x=30 m, VV, ray tracing x=15 m, VV, measurements x=30 m, VV, measurements x=15 m, VH, ray tracing x=30 m, VH, ray tracing
10 20 30 UAV height (m)
60
65
70
75
80
85
90
95
100
105
110
Path loss (dB)
x=15 m, VV, ray tracing x=30 m, VV, ray tracing x=15 m, VV, measurements x=30 m, VV, measurements x=15 m, VH, ray tracing x=30 m, VH, ray tracing
RX1 RX2
Fig. 16: (a) Ray tracing simulation results of path loss (VV and VH) alongside measurement results (VV) for
unobstructed UAV hovering at x = 15 m, and x = 30 m for different heights for (a) RX1, at ground, (b) RX2, at
1.5 m height from the ground.
G. Ray Tracing Simulation Setup and Path Loss Results
Ray tracing simulations were carried out using the Wireless InSite software to compare with our empirical findings
for unobstructed UAV hovering scenario. The foliage obstructed scenario was not simulated using ray tracing due
to the limitation of creating a particular real-world tree structure in simulations for UWB propagation. Similarly, the
unobstructed UAV moving scenario was also not simulated, as the effect of the motion on a given UWB propagation
environment cannot be easily captured.
Fig. 15 shows the simulation environment created using ray tracing. The majority of the MPCs arise from
scatterers near the RXs, e.g., tripod, measuring equipment, and humans that were modeled accordingly. The MPCs

27
from the buildings and foliage in the surroundings were not considered as our empirical excess time delay for
each scan is limited to 100 ns (30 m). This corresponds to reflections only from the objects that are not farther
than 15 m (considering two-way reflection distance 2 × 15 m) from the RXs. Similarly, due to the limited time
resolution of MPCs in the ray tracing software compared to measurements, only path loss results are considered
for comparison.
The path loss results obtained from ray tracing simulations for unobstructed UAV hovering scenario for VV and
VH antenna orientations are shown in Fig. 16. Measurement results of unobstructed UAV hovering for VV antenna
orientation are also provided in Fig. 16. Comparing with the empirical results at RX1 and RX2, respectively, we
observe a reasonably close match. Cross overs between the path loss results at 15 m and 30 m for VV scenario can
also be observed in ray tracing simulations, similar to measurement and analytical results. However, we observe
smaller path loss at smaller UAV heights compared to empirical results. Similarly, larger path loss can be observed
at larger elevation angles compared to empirical results. This is mainly due to the perfect donut shaped antenna
radiation pattern in simulations.
For the VH antenna orientation, we found that the path loss from ray tracing simulations differs from that
observed empirically in Fig. 14(a). This is because the MPCs (with weak or no LOS component) obtained due
to reflections from surrounding objects are dependent on the actual geometry and placement of these objects,
which we have not modeled with high precision. In addition, the path loss obtained for VH antenna orientation is
significantly larger than measurements. First, the additional scatterers not modeled in ray tracing but present in the
actual measurements contribute to additional MPCs. This results in a reduction of path loss. Another reason is the
non-ideal cross-polarization discrimination for real-world antennas that results in the reduction of the path loss for
VH antenna orientation.
V. CONCLUSION
In this work, we have reported UWB AG propagation channel measurements in an open field using a small UAV
in three propagation scenarios: unobstructed UAV hovering, foliage obstruction, and unobstructed UAV moving in
a constant-altitude circle. Measurements were obtained at three UAV heights and two horizontal distances for two
different antenna orientations at the UAV TX. We observed that the received power is highly dependent on the
antenna gain of the LOS component in the elevation plane when the antennas are aligned (same orientation). The
antenna gain for the LOS component can be approximated by a sine function of the elevation angle. This antenna
gain was used in an analytical model for the path loss for unobstructed UAV hovering and moving scenarios. In
addition, empirical path loss results for unobstructed UAV hovering scenario are corroborated using ray tracing
simulations. Moreover, it was found that the antenna orientation mismatch results in higher path loss and a larger
number of MPCs, smaller K-factor, and larger RMS-DS than in the co-polarized case. The OLOS scenario due to
foliage between the TX and the RX, while the UAV is hovering, introduces additional attenuation, and additional
MPCs due to foliage, resulting in further reduction in the K-factor. The motion of the UAV in a circular path
provided better mitigation against antenna orientation mismatch than the unobstructed UAV hovering scenario. A
statistical channel model based upon the SV model was derived from the empirical results. The SV model was

28
found to provide a better fit for the PDP than a single exponential fit. Future work includes channel characterization
for suburban and urban areas and air-to-air propagation channel measurements and modeling.
REFERENCES
[1]W. Khawaja, O. Ozdemir, F. Erden, I. Guvenc, and D. Matolak, “UWB air-to-ground propagation channel measurements and modeling
using UAVs,” in Proc. IEEE Aerospace Conf., Big Sky, MT, Mar., 2019.
[2]W. Khawaja, I. Guvenc, D. Matolak, U.-C. Fiebig, and N. Schneckenberger, “A survey of air-to-ground propagation channel modeling for
unmanned aerial vehicles,” IEEE Commun. Surveys & Tutorials, May, 2019.
[3]A. Merwaday, A. Tuncer, A. Kumbhar, and I. Guvenc, “Improved throughput coverage in natural disasters: Unmanned aerial base stations
for public-safety communications,” IEEE Vehic. Technol. Mag., vol. 11, no. 4, pp. 53–60, Nov., 2016.
[4]J. Brodkin, “AT&T drone providing cellular coverage,” Nov., 2017, accessed: 6-27-2018. [Online]. Available: https://arstechnica.com/
information-technology/2017/11/att-drone-brings-lte-access-to-hurricane-damaged-puerto-rico/.
[5]A. A. Khuwaja, Y. Chen, N. Zhao, M. Alouini, and P. Dobbins, “A survey of channel modeling for UAV communications,” IEEE Commun.
Surveys & Tutorials, vol. 20, no. 4, pp. 2804–2821, Fourthquarter 2018.
[6]M. Simunek, F. P. Font a ́n, and P. Pechac, “The UAV low elevation propagation channel in urban areas: Statistical analysis and time-series
generator,” IEEE Trans. Ant. Propag., vol. 61, no. 7, pp. 3850–3858, July 2013.
[7]F. Ono, K. Takizawa, H. Tsuji, and R. Miura, “S-band radio propagation characteristics in urban environment for unmanned aircraft
systems,” in Proc. IEEE Int. Symposium Ant. Propag. (ISAP), Hobart, TAS, Australia, Nov., 2015, pp. 1–4.
[8]D. W. Matolak and R. Sun, “Air to ground channel characterization for unmanned aircraft systems-part:I: Methods, measurements, and
models for over-water settings,” IEEE Trans. Vehic. Technol., vol. 66, no. 1, pp. 26–44, Jan. 2017.
[9]R. Sun and D. W. Matolak, “Air to ground channel characterization for unmanned aircraft systems-part: II: Hilly and mountainous settings,”
IEEE Trans. Vehic. Technol., vol. 66, no. 3, pp. 1913–1925, Mar. 2017.
[10]D. W. Matolak and R. Sun, “Air to ground channel characterization for unmanned aircraft systems-part:III: The suburban and near-urban
environments,” IEEE Trans. Vehic. Technol., vol. 66, no. 8, pp. 6607–6618, Aug. 2017.
[11]W. Khawaja and O. Ozdemir and I. Guvenc, “Temporal and spatial characteristics of mmWave propagation channels for UAVs,” in Proc.
IEEE Global Symposium on Millimeter Waves (GSMM), Boulder, CO, May, 2018, pp. 1–6.
[12]W. Khawaja, O. Ozdemir, and I. Guvenc, “UAV Air-to-Ground channel characterization for mmWave systems,” in Proc. IEEE Vehic.
Technol. Conf. (VTC-Fall), Toronto, ON, Canada, Sep., 2017, pp. 1–5.
[13]X. Chu, C. Briso, D. He, X. Yin, and J. Dou, “Channel modeling for low-altitude UAV in suburban environments based on ray tracer,” in
Proc. IEEE European Conf. Ant. Propag. (EuCAP 2018), London, UK, Apr., 2018, pp. 1–5.
[14]J. Chen, D. Raye, W. Khawaja, P. Sinha, and I. Guvenc, “Impact of 3D UWB antenna radiation pattern on air-to-ground drone connectivity,”
Proc. IEEE Vehic. Technol. Conf. (VTC), Chicago, Aug., 2018.
[15]E. Yanmaz, R. Kuschnig, and C. Bettstetter, “Channel measurements over 802.11-a based UAV-to-ground links,” in Proc. IEEE Global
Commun. Conf. (GLOBECOM) Workshops, Houston, TX, Dec., 2011, pp. 1280–1284.
[16]C.-M. Cheng, P.-H. Hsiao, H. Kung, and D. Vlah, “Performance measurement of 802.11-a wireless links from UAV to ground nodes with
various antenna orientations,” in Proc. IEEE Int. Conf. Computer Commun. Netw., (ICCCN), Arlington, VA, Oct., 2006, pp. 303–308.
[17]W. Khawaja, I. Guvenc, and D. Matolak, “UWB channel sounding and modeling for UAV air-to-ground propagation channels,” in Proc.
IEEE Global Commun. Conf. (GLOBECOM), Washington, D.C., Dec., 2016, pp. 1–7.
[18]“DJI ground station Pro,” accessed: 2-1-2018. [Online]. Available: https://www.dji.com/ground-station-pro.
[19]Federal Communications Commission, “Rules regarding ultra-wideband transmission systems,” Technical Report FCC 10-151, Aug. 2010.
[20]T. L. Foreman, “Application of the CLEAN detector to low signal to noise ratio targets,” in Proc. IEEE Radar Conf., Washington, D.C.,
May, 2010, pp. 150–155.
[21]“Time domain p440 UWB radios,” accessed: 2-1-2018. [Online]. Available: http://www.timedomain.com/products/pulson-440/.
[22]A. A. Saleh and R. Valenzuela, “A statistical model for indoor multipath propagation,” IEEE Select. Areas Commun., vol. 5, no. 2, pp.
128–137, 1987.
[23]H. Arslan, Z. N. Chen, and M.-G. Di Benedetto, “Ultra wideband wireless communication,” John Wiley & Sons, 2006.
[24]A. F. Molisch, K. Balakrishnan, C.-C. Chong, S. Emami, A. Fort, J. Karedal, J. Kunisch, H. Schantz, U. Schuster, and K. Siwiak, “IEEE
802.15. 4a channel model-final report,” IEEE P802, vol. 15, no. 04, p. 0662, 2004.

29
[25]T. S. Rappaport, “Wireless communications: principles and practice,” Prentice Hall PTR New Jersey, vol. 2, 1996.
[26]C. Carbonelli and U. Mitra, “Clustered channel estimation for UWB signals,” in Proc. IEEE Int. Conf. Commun. (ICC), vol. 4, Paris,
France, Jun., 2004, pp. 2432–2436.
[27]T. A. Milligan, “Modern antenna design,” John Wiley & Sons, 2005.
[28]A. B. Constantine, “Antenna theory: analysis and design,” Third Edition, John Wiley & Sons, 2005.
[29]W. C. Jakes and D. C. Cox, “Microwave mobile communications,” Wiley-IEEE Press, 1994.
[30]T. S. Rappaport, G. R. MacCartney, M. K. Samimi, and S. Sun, “Wideband millimeter-wave propagation measurements and channel models
for future wireless communication system design,” IEEE Trans. Commun., vol. 63, no. 9, pp. 3029–3056, May, 2015.
[31]C. Hansen, C. Doolan, and K. Hansen, “Ground reflection coefficient calculations,” Wiley Online Library, Online ISBN: 9781118826140,
Feb., 2017, accessed: 2-7-2018. [Online]. Available: https://onlinelibrary.wiley.com/doi/pdf/10.1002/9781118826140.app3