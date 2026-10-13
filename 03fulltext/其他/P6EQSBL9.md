---
title: "Passive Human Tracking With WiFi Point Clouds"
zotero_key: "P6EQSBL9"
pdf_key: "VJYSUQP7"
doi: "10.1109/JIOT.2024.3487193"
collection: "其他"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# Passive Human Tracking With WiFi Point Clouds — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

5528 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
Passive Human Tracking With WiFi Point Clouds
Zhongqin Wang , J. Andrew Zhang , Senior Member, IEEE, Haimin Zhang , Min Xu , Member, IEEE,
and Jay Guo , Fellow, IEEE
Abstract—Integrated sensing and communication (ISAC) tech-
nology empowers WiFi to function as both sensors for wireless
sensing and communication devices for data exchange. Currently,
achieving accurate object tracking with commercial WiFi devices
is still challenging due to the limited bandwidth, a small number
of antennas, and the clock asynchronization in a bi-static setup.
Many existing methods achieve tracking only via extracting a
dominant Doppler frequency shift (DFS) from a moving person.
However, since the human body is nonrigid, various body parts
generate different DFSs, and different subcarriers can exhibit
varying Doppler characteristics in a multipath environment. This
work presents WiDFS2.0, an enhanced real-time tracking scheme
that leverages the micro-Doppler effect to extract multiple signal
features from various body parts of a moving person, represented
as WiFi point clouds. Each point cloud consists of Doppler,
Angle of Arrival, Range, and signal-to-noise ratio. We design a
novel signal processing chain to extract the WiFi point clouds.
Then, we reﬁne these point clouds and implement an extended
Kalman ﬁlter-based algorithm to track the person’s trajectory.
Our experiments demonstrate that WiDFS2.0 can achieve real-
time tracking with a median position error of 0.55 m, while
determining the presence of a moving person with over 98%
accuracy during tracking.
Index Terms —Channel state information (CSI), Doppler
frequency shift (DFS), integrated sensing and communication
(ISAC), tracking, WiFi point clouds, WiFi.
I. I NTRODUCTION
U
BIQUITOUS WiFi infrastructures are envisioned to play
a signiﬁcant role in realizing the integrated sensing and
communication (ISAC) technique [1], [2], [3], [4], [5], [6].T h e
future WiFi ISAC network can function as a sensor by leverag-
ing the wireless channel state information (CSI) for sensor-free
sensing during communication. The CSI, which contains
detailed information about the signal propagation environment,
can be exploited to perform various sensing tasks, including
gesture/activity recognition [7], [8], [9], [10], vital sign detec-
tion [11], [12], [13], user authentication [14], [15], and target
localization [16], [17], [18], [19]. By translating the CSI data,
it is possible to estimate the position of objects and individuals
Received 22 August 2024; revised 13 October 2024; accepted 23 October
2024. Date of publication 28 October 2024; date of current version
21 February 2025. This work was supported in part by the Australian
Government through the Australian Research Council’s Discovery Projects
Funding Scheme under Project DP210101411. (Corresponding author: J.
Andrew Zhang.)
Zhongqin Wang, J. Andrew Zhang, Haimin Zhang, and Min Xu are with
the School of Electrical and Data Engineering, University of Technology
Sydney, Ultimo, NSW 2007, Australia (e-mail: zhongqin.wang@uts.edu.au;
andrew.zhang@uts.edu.au; haimin.zhang@uts.edu.au; min.xu@uts.edu.au).
Jay Guo is with the Global Big Data Technologies Centre,
University of Technology Sydney, Ultimo, NSW 2007, Australia (e-mail:
jay.guo@uts.edu.au).
Digital Object Identiﬁer 10.1109/JIOT.2024.3487193
within the coverage area of the WiFi network. This capability
transforms WiFi networks from communication systems into
powerful sensing platforms, enabling accurate and real-time
localization without the need for dedicated sensors, which can
be used in a variety of applications, ranging from smart home
and security to healthcare monitoring and beyond.
Recent advancements in WiFi-based sensing systems have
demonstrated the potential of leveraging CSI for accurate
positioning. The CSI, obtained from commercial-off-the-shelf
(COTS) WiFi network interface controllers (NICs), offers a
reliable and information-rich signal metric for precise passive
object localization. However, most COTS WiFi hardware,
such as the Intel 5300 or Atheros NIC, is constrained by
limited bandwidth and a small number of antennas. For
instance, these devices typically offer bandwidths of 20 or
40 MHz and support only two or three antennas, resulting in
coarse distance and angle resolutions, approximately 7.5 m for
20 MHz bandwidth and 38 ◦ for three antennas. Despite these
limitations, many WiFi-based systems have demonstrated the
ability to achieve ﬁne localization accuracy, especially in
controlled or static environments. Furthermore, bi-static WiFi
systems, where transmitters and receivers are deployed at
different locations without clock synchronization, introduce
additional challenges, such as time offsets (TOs) and carrier
frequency offsets (CFOs), which cause random phase shifts
across CSI measurements. To mitigate the effects of TO and
CFO, numerous techniques have been proposed, including
linear regression [20], [21], conjugate multiplication [16],
[19], [22], [23], [24], CSI quotient [25], [26], [27], [28],
reference path [29], [30], [31], etc. These approaches have
been effective in improving the reliability of WiFi localization
systems. However, the removal of clock asynchronization
introduces additional terms and noise, complicating the signal
processing and impacting the overall localization accuracy.
To achieve more accurate passive tracking, we still need to
address two key challenges.
Challenge 1: Most WiFi tracking algorithms are constrained
by the preprocessing step of clock asynchrony removal, which
often simpliﬁes the process by assuming that a moving
person introduces only a single Doppler frequency shift (DFS).
However, the human body is not rigid; different body parts,
such as the head, arms, feet, and chest, move indepen-
dently, generating multiple DFSs with distinct motion patterns.
The challenge, therefore, lies in effectively extracting these
reﬂection paths from various parts of the body to improve
localization accuracy by obtaining more position estimates,
each incorporating DFS, Angle of Arrival (AoA), and Range
information.
2327-4662 c© 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5529
Challenge 2: In practical applications, it is essential not only
to track the target’s position in real-time but also to detect
the presence of a moving target. Many existing systems rely
on predeﬁned thresholds to detect the presence of a target,
which can lead to missed detections or false positives (FPs)
when the target’s signal falls below or ﬂuctuates around this
threshold. Moreover, the challenge in tracking extends to effec-
tively combine all detections and integrate multidimensional
information (DFS, AoA, and Range) to optimize the target’s
trajectory. Developing a more reliable and accurate tracking
system that ensures both robust detection and continuous
tracking is crucial for improving overall performance.
In this work, we present WiDFS2.0, an enhanced real-
time passive human tracking scheme that improves upon
the previous version, WiDFS [16], which utilizes a variant
of the cross-antenna cross-correlation (CACC) method (i.e.,
conjugate multiplication) to remove random phase offsets
in CSI and resolve DFS ambiguity for accurate and real-
time human tracking. WiDFS2.0 further enhances the CSI
processing scheme and the tracking algorithm to address
the two aforementioned challenges. Similar to most WiFi
localization systems, WiDFS2.0 also uses a bi-static COTS
WiFi transceiver to track a moving person. The transceiver
setup consists of a single transmitter (TX) antenna and a
receiver with three receiving (RX) antennas (i.e., 1TX-3RX).
The transmitter and receiver are implemented on laptops
equipped with a COTS Intel 5300 NIC, which supports up to
three external antennas. CSI data is extracted from the receiver
NIC using an open-source tool [32]. Speciﬁcally, WiDFS2.0
improves system performance and real-world applicability in
two key aspects as follows.
A. Object Detection
Most existing systems achieve passive tracking under the
assumption of a dominant reﬂection from a moving person.
They generally obtain a DFS estimate, which is then uti-
lized to generate an object position candidate for tracking.
As described above, however, various body parts generate
different reﬂection signals and motion patterns. These micro-
scale movements introduce the micro-Doppler effect [33], [34]
and produce various DFSs.
Our WiDFS2.0 leverages the fact that a moving person
produces different DFSs for object detection. It ﬁrst uses the
WiDFS’s method to remove random offsets, static clutter,
and DFS ambiguity. Next, WiDFS2.0 performs a Doppler
fast Fourier transform (FFT) over CSI sample windows. In
each Doppler bin, a linear least-squares method is employed
for AoA estimation, followed by range estimation using
a subspace-based minimum variance distortionless response
(MVDR) algorithm [35]. This process results in a Doppler-
Range heatmap. After that, a constant false alarm rate (CFAR)
detector [36] is applied on this heatmap to automatically ﬁnd
objects of interest. Finally, we detect the moving person by
extracting more signal features, called WiFi Point Clouds. Each
point cloud includes DFS, AoA, Range, and signal-to-noise
ratio (SNR), where the SNR serves as an indicator of reﬂection
intensity.
B. Object Tracking
Some systems typically assume that a moving target is
already present in the environment, while others require
detecting the presence or absence of a moving person using a
predeﬁned threshold. However, such threshold-based solutions
cannot adaptively adjust to changes in the environment, which
may impact tracking performance. Additionally, the prior
WiDFS uses two independent Kalman ﬁlters to separately
reﬁne AoA and range estimates but does not consider the joint
optimization of DFS, AoA, and Range.
WiDFS2.0 adopts a novel tracking scheme using the
extracted WiFi point clouds. By separating targets in the
Doppler domain, the DFSs caused by the moving person in
these point clouds differ from each other. However, their range
and AoA data can collectively indicate the position of the
tracked person. In this case, WiDFS2.0 ﬁrst enhances the
accuracy of tracking by aggregating the diverse data points to
better pinpoint the target’s location. Then, an extended Kalman
ﬁlter (EKF)-based tracker for the bi-static WiFi system is
designed to jointly optimize the DFS, AoA, and Range of
the target. Speciﬁcally, we devise a priority-based assignment
method to establish a track across consecutive frames. Finally,
the estimated track that exists for the longest duration is
considered the optimal trajectory, while the absence of any
track output indicates the nonexistence of a moving person.
Through the above steps, the estimated trajectory can exhibit
higher tracking accuracy than WiDFS.
Our main contributions are highlighted as follows.
1) To the best of our knowledge, WiDFS2.0 is the ﬁrst
WiFi system to leverage the micro-Doppler effect for
extracting multiple position candidates from a tracked
individual, capturing distinct motion patterns of various
body parts. This enhances the reliability of target detec-
tion compared to systems that rely on a single DFS
assumption.
2) We introduce a novel CSI processing chain that gener-
ates a Doppler-Range heatmap, coupled with a CFAR
detector, to extract signal features represented as WiFi
point clouds. Such point clouds can provide a com-
prehensive representation of the tracked individual’s
motion, incorporating multiple dimensions-DFS, AoA,
Range, and SNR.
3) We propose an EKF-based real-time tracking scheme
utilizing WiFi point clouds. This tracker can detect the
presence of a moving person without any prior knowl-
edge and optimizes the target’s trajectory by jointly
processing DFS, AoA, and Range dimensions. This
approach enhances continuous tracking performance in
practical applications.
4) We develop a real-time prototype of WiDFS2.0 and
demonstrated its effectiveness through extensive experi-
ments. WiDFS2.0 achieves a positioning error of 0.55 m
in the XY dimension, outperforming state-of-the-art
systems like Widar2.0 and WiDFS. And WiDFS2.0
introduces the capability to detect both the presence and
absence of a moving person with over 98% accuracy,
without relying on predeﬁned thresholds, making it more
adaptable to real-world environments.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

5530 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
Fig. 1. WiDFS2.0 workﬂow.
II. M ICRO DOPPLER -BASED CSI M ODEL
We ﬁrst improve most existing CSI models [4], [16],
[29], [37] through two insights: 1) the nonrigid human body
produces various reﬂections from arms, legs, head, and torso,
each potentially exhibiting a different DFS and 2) selective
frequency fading results in variations in amplitude and phase,
which also contributes to diverse DFSs.
Let a CSI measurement be CSI i,j,k, where i is the RX
antenna index, j is the subcarrier frequency index, and k is the
sampling packet index. When a moving person is present, the
improved CSI model is formulated as follows:
CSIi,j,k = Hej,kHhi
(
HSi,j + HXi,j,k
)
(1)
where ⎧
⎨
⎩
HSi,j = ρSi,je−J2π
fj
c dSi + NSi,j
HXi,j,k = ∑l ρXi,j,k[l]e−J2π fjc dXi,j,k[l]. (2)
The following explains the above parameters.
1) Hej,k is the channel frequency response (CFR) caused
by clock asynchronization, varying with different
frequencies and sampling time. Hhi is the hardware-
related CFR.
2) HSi,j is the time-invariant static CFR caused by static
clutter. ρSi,j is the attenuation of the Line of Sight (LOS)
path between the transmitter and the ith RX antenna, dSi
is the distance of the LOS path, fj is the jth subcarrier
frequency, c is the speed of the light, and NSi,j is the CFR
of the non-LOS (NLOS) paths caused by other static
clutter.
3) HXi,j,k denotes the dynamic CFR of interest caused by
a moving person. ρXi,j,k[l] is the attenuation of the
reﬂection path from the TX antenna to one of body part
and back to ith RX antenna. dXi,j,k[l] is the length of the
reﬂection path.
Given a coherent processing interval (CPI) [6] comprising
Np CSI samples (e.g., Np = 128 in this work, which
corresponds to a duration of approximately 0.128 s due to
the CSI sampling frequency of 1 kHz), we can make two
assumptions in this short-time window: 1) the environment
undergoes slight changes, so the amplitudes ρagck and ρXi,j,k
remain almost constant, i.e., ρagck ≈ ρagc and ρXi,j,k ≈ ρXi,j
and 2) each body part moves at a constant velocity. Then, the
dynamic component HXi,j,k during a CPI is simpliﬁed as
HXi,j,k = ∑
l
ρXi,j[l]e
−J2π
fj
c
[
dXj [l]+(i−1)/Delta1d sin θXj [l]+c f Dj [l]fc (k−1)/Delta1t]
(3)
where dXj represents the initial reﬂection distance of the RX
Antenna 1 within the CPI, f Dj is the DFS (vDj = cf Dj /fc is called
the Doppler velocity), θXj is the AoA, which represents the
direction of a human reﬂection with respect to RX antennas,
/Delta1d is the antenna spacing, fc is the center frequency, and /Delta1t
is the sampling interval (i.e., 0.001 s).
III. O VERVIEW
This work proposes WiDFS2.0, a novel scheme that extracts
multiple reﬂections from a moving person, denoted as WiFi
point clouds, to achieve real-time passive tracking. Various
body parts of the person reﬂect signals toward the receiver,
allowing us to separate these reﬂections and generate richer
signal features for tracking. WiDFS2.0 work with an 1TX-3RX
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5531
WiFi system with Intel 5300 NICs [32]. Notably, WiDFS2.0
is compatible with other COTS WiFi platforms, such as
Atheros WiFi NICs [38] and PicoScenes [39], and multi-
input–multioutput (MIMO) WiFi system. The workﬂow of
WiDFS2.0 is illustrated in Fig. 1, which includes as follows.
A. WiFi Point Cloud Generation
As detailed in Section IV, WiDFS2.0 ﬁrst uses a variant
CACC method [16] to preprocess the CSI. It then employs a
novel CSI processing chain across joint time (Doppler), spatial
(AoA), and frequency (Range) domains to detect WiFi point
clouds, each containing Doppler velocity, AoA, Range , and
SNR.
B. Passive Tracking With WiFi Point Clouds
As detailed in Section V, WiDFS2.0 optimizes the WiFi
point clouds for outlier removal and then applies an EKF-based
tracker to sense and track the moving person in real-time. This
process involves trajectory initialization, prediction, associa-
tion, update, and maintenance steps.
IV . WIFI POINT CLOUD GENERATION
This section introduces how to generate WiFi point clouds,
each of which represents DFS, AoA, Range, and SNR from a
reﬂected body part. The processing chain for WiFi point cloud
detection is detailed as follows.
A. CSI Preprocessing
In a bi-static WiFi system, raw CSI data are always affected
by clock asynchronization between a transmitter and receiver.
Here, we apply the variant CACC ﬁrst proposed in [16] to
remove random phase shifts, static clutter, and ambiguity in
DFS estimation. It can remain the linearity of original CSIs
for the following AoA and Range estimation. After processing
raw CSI data, we obtain the following dynamic component
sets for each antenna pair:
{ H12,j ={ H12,j,1, H12,j,2,..., H12,j,Np }
H23,j ={ H23,j,1, H23,j,2,..., H23,j,Np } (4)
where let us take H12,j,k as an example
H12,j,k =
HX1,j,k
HS1,j −
HX2,j,k
HS2,j/bracehtipupleft /bracehtipdownright/bracehtipdownleft /bracehtipupright
1©
+
HX3,j,k
HS3,j
(
HX1,j,k
HS1,j −
HX2,j,k
HS2,j
)
/bracehtipupleft /bracehtipdownright/bracehtipdownleft /bracehtipupright
2©
. (5)
The component 1© is the one of interest, while the component
2© is the unwanted byproduct term, which has a lower
amplitude and inaccurate signal parameters (Doppler, AoA,
and Range) compared to 1©. We can suppress it by combining
the separated dynamic components from the time (Doppler),
spatial (AoA), and frequency (Range) domains.
In each CPI, we use H12,j and H23,j to build a 3-D
CSI cube with the dimension of 128 × 30 × 2 (called
a CSI frame ), shown in Fig. 1. The ﬁrst dimension (i.e.,
time domain) stores Np = 128 CSI samples to estimate the
DFSs. The second dimension (i.e., subcarrier dimension) has
Fig. 2. Example of Doppler estimation via FFT. There exist four Doppler
velocity components of interest caused by human motion, including -0.44,
0.44, 1.98, and 3.75 m/s.
30 subcarrier frequencies to estimate the human reﬂection
ranges. The third dimension (i.e., antenna pair dimension)
consists of two different antenna pairs to estimate the AoAs.
B. DFS Estimation via FFT
Different body parts acts as individual reﬂectors that reﬂect
WiFi signals toward the receiver. The difference in spatial
positions and motion directions of body parts leads to different
changes in the distance of signal reﬂection in a short-time
interval, resulting in distinct DFSs. Also, different subcarriers
experience diverse propagation paths, potentially exhibiting
different Doppler characteristics. In WiDFS2.0, we ﬁrst sep-
arate dynamic human components from the time domain for
each antenna pair and subcarrier.
We apply a Doppler FFT, denoted as F(·), along the time
dimension on the 3-D CSI cube of each antenna pair and
subcarrier frequency. This process yields transformed CSI
cubes, denoted as ~H12,j = F{H12,j} and ~H23,j = F{H23,j}.
According to (4) and (5), the Doppler FFT results at each
Doppler bin with the DFS f D is
⎧
⎪⎨
⎪⎩
~H12,j = ∑Npk=1 H12,j,keJ2πf D(k−1)/Delta1t = ~HX1,jHS1,j − ~HX2,jHS2,j + nX12,j
~H23,j = ∑Npk=1 H23,j,keJ2πf D(k−1)/Delta1t = ~HX2,jHS2,j − ~HX3,jHS3,j + nX23,j
(6)
where
~HXi,j ≈ ∑
l
ρXi,j[l]e−J2π
fj
c
[
dXj [l]+(i−1)/Delta1d sin θXj [l]]. (7)
And nX12,j and nX23,j represent the Doppler FFT output of the
byproduct term. For the Doppler bin of being a moving body
part, the amplitudes of ~H12,j and ~H23,j will keep at a high
level and the amplitude of ~NXmn,j with the different DFS should
be much lower than other terms. In this case, the impact of the
byproduct item can be initially suppressed at this stage. In the
following sections, we can further suppress it at this Doppler
bin from AoA and Range dimensions.
To provide an intuitive understanding of the micro-Doppler
effect, we present an example in Fig. 2. It plots the Doppler
FFT results from 30 subcarriers for the two antenna pairs.
Considering the typical speeds of different body parts in
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

5532 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
indoor environments, the Doppler velocities is set within
[−5m / s, 5 m/s], corresponding to the Doppler frequencies of
[−88.7H z, 88.7 Hz]. We can see that body movements may
produce about four main Doppler velocities: −0.44, 0.44, 1.98,
and 3.75 m/s. Additionally, these subcarriers exhibit different
Doppler proﬁles. Some subcarriers do not have evident peaks
at certain Doppler bins of interest.
C. AoA Estimation via Least Squares
Considering the variation in spatial positions and velocities
among different body parts, it is reasonable to expect distinct
DFS values caused by the movement of a person. We assume
that each moving body part produces a unique DFS, meaning
that each Doppler bin corresponds to a speciﬁc body part of a
moving person. In this case, (7) can be simpliﬁed to focus on
a single target. Following the narrowband assumption, we also
have ρXj = ρX1,j ≈ ρX2,j ≈ ρX3,j at each Doppler bin. Besides,
since fc is the WiFi center frequency, then we have (fj/c)/Delta1d ≈
(fc/c)/Delta1d. In this way, (6) can be rewritten as⎧
⎪⎪⎨
⎪⎪⎩
~H12,j ≈
~HX2,j
HS2,j
(
eJ2π fcc /Delta1d sin θX HS2,j
HS1,j − 1
)
+ nX12,j
~H23,j ≈
~HX2,j
HS2,j
(
1 − e−J2π fcc /Delta1d sin θX HS2,j
HS3,j
)
+ nX23,j.
(8)
We divide the above two equations to remove ~HX2,j/HS2,j
~H12,j
~H23,j ≈
(
HS2,j
HS1,j eJ2π
fj
c /Delta1d sin θX − 1) + /Delta1nX12,j
(
1 −
HS2,j
HS3,j e−J2π
fj
c /Delta1d sin θX
)
+ /Delta1nX23,j
(9)
where /Delta1nX12,j and /Delta1nX23,j are the noise terms. And the ratio of
static components is calculated by
⎧
⎪⎨
⎪⎩
HS2,j
HS1,j = Hh1Hh2 U23,jU31,j
HS2,j
HS3,j = Hh3Hh2 U12,jU31,j . (10)
The static component in each CPI remains unchanged
and can be estimated by averaging over CACC outputs.
For example, we perform CACC between the CSI of
RX Antennas 1 and 2 for the jth subcarrier, resulting in
CSI12 ={ CSI1,j,1CSI2,j,1,..., CSI1,j,Np CSI2,j,Np }. The mean
value denoted as U12,j is
U12,j =
(
ρagc)2Hh1 Hh2HS1,jHS2,j ≈ 1Np Np∑k=1 CSI1,j,kCSI2,j,k. (11)
In particular, Hh1/Hh2 and Hh2/Hh3 are pre-estimated parameters
using the calibration method in [16], as different RX antennas
have distinct hardware characteristics. By ignoring the noise
terms in (9), the equation can be decomposed into its real and
imaginary parts. Given 30 subcarriers, we can construct 60 sets
of equations to minimize the impact of noise and solve for the
optimal cos (2π(fc/c)/Delta1d sinθX) and sin (2π(fc/c)/Delta1d sinθX)
using a linear least-squares method, thereby determining the
AoA θX.
Speciﬁcally, to mitigate the random phase shifts caused by
clock asynchrony between the transmitter and receiver, and to
Fig. 3. Example of 2-D Doppler-Range heatmap. The highlighted areas
indicate a higher probability of target presence.
resolve the Doppler ambiguity problem, we perform a series
of linear transformations by combining the CSI data from
Antennas 1 and 2, and from Antennas 2 and 3, respectively.
This will reduce the three antennas to two antenna pairs
(i.e., Antennas 1 and 2 and Antennas 2 and 3). Since most
commercial NICs support a maximum of three antennas, the
system requires all three antennas to achieve reliable AoA
estimation.
D. Range Estimation via MVDR
Given the estimated AoA, we can further use an MVDR
algorithm to achieve the reﬂection range estimation for each
Doppler bin. Here, a range spectrum is built at each Doppler
bin, which can represent the probability of a moving body
part being present at different ranges. Additionally, the impact
of the by-product terms can be further suppressed in range
estimation by combining 30 subcarriers.
We substitute each estimated AoA back into (8) to approx-
imately estimate ~HXi,j/HSi,j by ignoring noise terms, where i =
1, 2, 3, at each RX antenna pair and subcarrier frequency
for each Doppler bin. We then combine these estimates to
construct an observation matrix /Lambda1
/Lambda1 =
⎡
⎢⎢⎢⎢⎢⎢⎢⎢⎣
~HX1,1
HS1,1
~HX2,1
HS2,1
~HX3,1
HS3,1
~HX1,2
HS1,2
~HX2,2
HS2,2
~HX3,2
HS3,2
... ... ...
~HX1,30
HS1,30
~HX2,30
HS2,30
~HX3,30
HS3,30
⎤
⎥⎥⎥⎥⎥⎥⎥⎥⎦
30×3
. (12)
A 2-D steering vector A is built for 30 subcarriers, where
the searching range of d/Delta1 is set within (0m , 20 m ) with a
spacing of 0 .1m
A =
[
a
(
d/Delta11 ), a(d/Delta12 ),..., a(d/Delta1200)]30×200 (13)
where
a
(
d/Delta1) = [e−J2π f1c d/Delta1 , e−J2π f2c d/Delta1,..., e−J2π f30c d/Delta1]T (14)
where d/Delta1 is the difference between the transmitter-person-
receiver NLOS distance dX and transmitter-receiver LOS
distance dS, denoted as d/Delta1 = dX − dS, according to our
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5533
CSI model in (2).T h et e r mdS can be manually measured in
advance, while dX is the distance that needs to be estimated.
For each range bin, a 30×200 complex-valued beamforming
weight can be calculated by
w
(
d/Delta1) = R−1/Lambda1 a(d/Delta1)
aH(d/Delta1)R−1/Lambda1 a(d/Delta1) (15)
where R/Lambda1 = E(/Lambda1/Lambda1H) is the covariance matrix.
Finally, the corresponding range power spectrum with the
size of 1 ×200 is obtained by
P
(
d/Delta1) = ‖‖‖wH(d/Delta1)R/Lambda1w(d/Delta1)‖‖‖
= 1‖‖‖aH(d/Delta1)R−1/Lambda1 a(d/Delta1)‖‖‖. (16)
The MVDR algorithm can compute the output power for all
range bins. The power peak indicates the distance candidates.
The larger peak means the higher likelihood of the presence
of a target at this range bin. We repeat the range estimation
for each Doppler bin and then generate a 2-D Doppler-Range
heatmap. Fig. 3 shows the normalized 2-D heatmap, calculated
using the same data as presented in Fig. 2. The highlighted
regions indicate a higher likelihood of the presence of targets.
E. Object Detection via 1-D CFAR
This section aims to separate out moving objects from
the Doppler-Range heatmap. Since the Doppler dimension
has a much higher resolution than the Range dimension, the
maximum of the range power spectrum for each Doppler bin
is extracted to form an 1-D Doppler power sequence. An 1-D
CFAR detector is then applied to detect the Doppler bins of
interest with the presence of moving body parts. The CFAR
detector can adaptively identify peaks with power levels above
the average neighboring levels. The SNR for each detected
peak is calculated using the amplitudes in the training and
guard cells in the CFAR detector. As shown in Fig. 4,w e
apply an 1-D cell-averaging CFAR detector [40] to detect
objects. The red markers indicate the presence of targets at
these Doppler bins. We also plot the normalized results of the
Doppler FFT. Compared to the Doppler spectrum extracted
from the 2-D Doppler-Range heatmap, we can observe that
the peaks become shaper, enhancing the ability to distinguish
objects.
Considering that the human body generates multiple distinct
DFSs, the derived AoA and range measurements from these
Doppler bins can all be used during tracking. We deﬁne them
as WiFi Point Clouds, each consisting of the signal features of
Doppler, AoA, Range, and SNR. WiDFS2.0 can leverage more
localization information to facilitate more accurate tracking.
F . Example for WiFi Point Cloud Generation
We present an example to illustrate the process of WiFi
point cloud generation. In this experiment, WiFi point clouds
are obtained from a scenario where a person moved along
an elliptical trajectory multiple times. As shown in Fig. 5(d),
we plot the extracted Doppler, AoA, and Range for points
Fig. 4. Example of 1-D CFAR detection. The targets of interest can be
automatically detected by the 1-D CFAR detector.
with the highest SNR, highlighted in orange, while those
with lower SNR are shown in blue. The red lines represent
the ground truth captured by a mmWave radar. Due to the
differing positions of the WiFi Tx and Rx antennas compared
to the radar setup, the Doppler estimates vary between the two
systems. In this case, we only plot the ground-truth AoA and
Range from the radar.
The results show that most detected point clouds closely
align with the ground truth. However, the Range estimates
exhibit larger errors due to the limited bandwidth of 20 MHz.
Notably, the point clouds with higher SNR values generally
provide a more accurate match to the ground truth. Since the
human body generates multiple distinct DFSs, the correspond-
ing AoA and Range measurements from these Doppler bins
can also be used in tracking. The enhanced WiDFS2.0 can
leverage a greater number of high-SNR point clouds to enable
more precise human tracking.
V. P ASSIVE TRACKING WITH WIFI POINT CLOUDS
In this section, we design a point cloud optimization
technique and an EKF-based tracker for real-time human
tracking via optimized WiFi point clouds.
A. Coordinate System Transformation
We begin by converting the polar coordinates (Range and
AoA) of each point cloud into Cartesian coordinates in bistatic
WiFi systems. Let dX→RX be the distance of the tracked person
to the receiver. And let θS be the premeasured AoA of the
transmitter relative to the receiver. In our experiment setup,
the transmitter is placed on the left side of the receiver, and
the RX antennas on the receiver are numbered from left to
right as Antennas 1–3. According to [16],w eh a v e
dX→RX =
(
dX)2 − (dS)2
2[dX − dS cos(θX − θS)]. (17)
And each point cloud’s XY coordinates are
{ x = dX→RX sinθX
y = dX→RX cos θX. (18)
Hence, each point cloud includes ⟨x, y, vD, SNR⟩, where x and
y denote the Cartesian coordinates, vD is the Doppler velocity,
and SNR is the SNR value.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

5534 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
(a)
(b)
(c)
Fig. 5. Example of WiFi point clouds extracted from the Doppler bins of interest. A person moves along an elliptical trajectory several times, and the p oint
clouds in each frame show the Doppler velocity, AoA, and Range, where the Range represents the total distance of the tracked person to the transmitter a nd
receiver. (a) Doppler velocity. (b) AoA. (c) Range.
B. Joint Optimization of Point Clouds
Since most COTS WiFi platforms have a narrow bandwidth
(e.g., 20 MHz), inaccurate range estimation generates more
position outliers. The EKF tracker may not be well-suited
for the cases where anomalies are more frequent. Here, we
propose an outlier removal method based on the fact that
the actual XY coordinates of point clouds associated with a
moving person should be close to each other.
1) Centroid Selection: We ﬁrst capture the point clouds
across adjacent CSI frames and calculate the Euclidean
distance of each XY coordinate point to the cen-
ter of these points (i.e., the median of the XY
coordinates).
2) Weighted Averaging: We then extract the points that
have a distance less than the 60th percentile of all
distances. Subsequently, a weighted averaging method
is used to calculate an optimal XY coordinate and
Doppler velocity, where the weights are from the SNR
values.
3) Temporal Smoothing: As the latest WiFi frame arrives,
the impact of point clouds from earlier frames should be
reduced. To achieve this, the SNR values of the previous
frame’s point clouds are multiplied by a smoothing
factor (e.g., 0.9 or 0.98).
In this way, WiDFS2.0 ﬁlters point clouds that are far away
from the center of the data, considering them as outliers. Then,
the optimal point cloud is retained for subsequent tracking.
C. Real-Time Tracking via EKF
We adopt the following procedure to implement the EKF-
based tracker, which is capable of detecting the absence or
presence of a moving person and tracking the person.
1) Initializing Tracks: We initialize a set of track for each
point cloud at the ﬁrst frame. A constant acceleration model
is used in the EKF. The initial state s(0) is deﬁned as
s(0) =
[
x, y, vx, vy, ax, ay
]T (19)
where vx and vy are the velocities along the x and y axis,
vx = vy = 0.5vD m/s, ax and ay are the accelerations, and
ax = ay = 0.5 m/s2. Since the velocity and acceleration are
estimated by the EKF, we set limits for the maximum velocity
and acceleration to enhance the tracker’s stability: the x- and
y-axis velocity is constrained within [ −3m / s, 3 m/s], and the
x- and y-axis acceleration is limited to [ −1m / s2, 1m / s2].
Each track is assigned the following attributes.
1) ID is the ID of the track; 2) Num age is the number of
frames since the track was created; 3) Num vis is the number
of frames in which the track can associate with the point
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5535
clouds in the next frame; and 4) Num consInvis is the number of
consecutive frames for which the track cannot associate with
the point clouds in the next frame. In the initial state, we have
Numage = 1, Numvis = 1, and Num consInvis = 0.
2) Predicting Tracks: The predicted state sp(n) and the
predicted covariance matrix Pp(n) at the nth frame can be
calculated by
{ sp(n) = Fs(n − 1)
Pp(n) = FP(n − 1)FT + Q(n − 1) (20)
where F is the state transition matrix, P is the covariance
matrix of the state vector, Pp is the predicted covariance
matrix, and Q is the covariance matrix of the process noise.
3) Assigning Reﬁned Point Cloud to Tracks: W h e nan e w
reﬁned point cloud arrives, we compute the cost matrix using
the Euclidean distance to assign the point cloud to existing
tracks. Since there may exist multiple tracks, we adopt a
priority assignment strategy that assigns a detection to a track
with the larger Num age in priority. For example, Num age
of Track 1 is 20 while Num age of another Track 2 is 10.
Track 1 ﬁrst matches the detection. Also, a smaller distance
indicates a higher likelihood that the point cloud belongs to
Track 1. If the cost between the track and detection is less
than an empirical threshold of 2 m, we assign the detection to
Track 1; otherwise, we conduct the same procedure above for
Track 2. This assignment strategy ensures that the point cloud
is assigned to the track that exists for a longer time.
4) Updating Assigned Track: For those matched detection
and the assigned track, we use the EKF to reﬁne the predicted
state estimate of each track based on its matched detection in
the current frame. The Kalman gain K(n) is
{ C(n) = JH[sp(n)]Pp(n)JTH[sp(n)] + R(n)
K(n) = Pp(n)JTH[sp(n)] + [C(n)]−1 (21)
where JH is the Jacobian matrix and R is the covariance matrix
of the measurement error.
The updated state and the covariance matrix are updated by
{ s(n) = sp(n) + K(n)[u(n) − H(sp(n))]
P(n) = Pp(n) − K(n)JH
[
sp(n)
)
Pp(n) (22)
where u = [x, y, vD]T is the reﬁned point cloud in the current
frame and H is a measurement matrix calculated based on the
predicted states by
H
(
sp
)
=
⎡
⎢⎢⎢⎣
√
x2p + y2p
tan−1(xp, yp)
xpvx,p+ypvy,p√
x2p+y2p
+ (xp−xTX)vx,p+(yp−yTX)vy,p√
(xp−xTX)2+(yp−yTX)2
⎤
⎥⎥⎥⎦ (23)
where (xp, yp) and (vx,p, vy,p) are the predicted coordinates
and velocities from sp(n). (xTX, yTX) are the coordinates of
the transmitter, while the receiver is located at the coordinate
origin. The estimated DFS is associated with the positions of
the person relative to the transmitter and receiver [41].
In this assignment step, we increment Num age and Numvis
of the track by 1 and set Num consInvis to be 0.
5) Updating Unassigned Tracks: For those unassigned
tracks, the attributes Num age and Num consInvis of the corre-
sponding track are both increased by 1.
Fig. 6. CDF of tracking accuracy in LOS.
Fig. 7. CDF of tracking accuracy in NLOS.
Fig. 8. Tracking accuracy comparison.
6) Creating New Track: For the unassigned detection, we
create a new track. The unmatched detection serves as a start-
ing point of a new track. Likewise, we initialize Num age = 1,
Numvis = 1, and Num consInvis = 0.
7) Maintaining Tracks: Track maintenance involves dis-
carding some existing tracks and outputting the conﬁrmed
track. We remove the tracks that are invisible for many consec-
utive frames or have the small number of total visible frames.
In WiDFS2.0, we aim to perform single-target tracking. In this
case, if no track outputs, we consider that no person exists
or there is no person moving within the surveillance region.
If the tracker reports one track, we infer the presence of a
person moving. And the track with the maximum of Num age
is selected as the optimal track.
VI. I MPLEMENTATION AND EVA L UAT I O N
CSI Dataset: WiDFS2.0 is evaluated using the same CSI
dataset as WiDFS [16]. The dataset is collected using an 1TX-
3RX setup with Intel 5300 NICs. The Linux 802.11n CSI
tool [32] is conﬁgured in the monitor mode with the CSI
sampling rate of 1 kHz. The center frequency is at 5.32 GHz.
The dataset includes three types of tracks: 1) Elliptical Track;
2) Linear Track; and 3) Rectangle Track, shown in Figs. 9–11,
respectively. These tracks were collected in a relatively open
laboratory environment. The dataset primarily features LOS
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

5536 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
(a)
(b)
(c)
(d)
(e)
(f)
Fig. 9. Case of ellipse path tracking. (a) Elliptical trajectory. (b) AoA.
(c) Range. (d) X-axis coordinate. (e) Y-axis coordinate. (f) Estimated ellipse
trajectory.
scenarios in multipath environments with various reﬂectors,
such as tables, chairs, metal lockers, computers, large displays,
tempered glass, and hollow walls. Additionally, a NLOS
scenario dataset was collected by blocking the direct path from
the tracked person to the transceiver using a plastic box and
wood board. The distance between the transmitter and receiver
is approximately 2.3 m, and the AoA of the transmitter relative
to the receiver is around −70◦. Furthermore, we also collected
data in a smaller meeting room environment, as shown
in Fig. 18. Here, the distance between the transmitter and
receiver is approximately 1.2 m. In the experiments mentioned
above, by default, the speed of the tracked human target is
about 1 m/s, with only one moving individual present within
the monitoring area. The ground-truth tracks, with centimeter-
level accuracy, are obtained using a TI IWR1642 mmWave
radar.
Default Conﬁguration: 1) WiFi CSI Frame: A WiFi frame
consists of 128 CSI samples at different subcarriers for each
RX antenna. The step size is 48 CSI samples, resulting in an
overlap of 80 samples between two successive frames. It is
important to ensure that the average processing time per frame
should be less than the step-size time to maintain real-time
performance. 2) CFAR Detector: The CFAR object detector
uses 4 training cells and 2 guarding cells. The adaptive thresh-
old is determined by multiplying the background noise power,
derived from the training cells, with a multiplication threshold
factor. The threshold factor is set to 1.5. 3) EKF-based
Tracker: In the association step, the association threshold
based on the cost matrix is 2 m. For a track with Numage > 15,
if Numvis/Numage > 0.6 and Num consInvis < 5, we report this
track; otherwise, we remove it. And the tracks with Num age ≤
15 are retained.
Baseline: Two SOTA methods: 1) Widar2.0 [19] and
2) WiDFS [16], are implemented and compared with our
WiDFS2.0. It is worth noting that many Doppler-based track-
ing methods [18], [22], [42], [43] typically require multiple
receivers and may encounter cumulative errors in long-term
target tracking. In our experiments, we have not included
comparisons with these approaches. 1) Widar2.0 extracts a
single-side component from CACC terms by adding a constant
to the CSI amplitudes of the reference antenna and subtracting
another constant factor from the CSI amplitudes of other
antennas. It then employs a maximum likelihood estimation
(MLE)-based method to jointly estimate the DFS, AoA and
range. 2) WiDFS performs real-time single-target tracking by
assuming that a moving person only causes a DFS.
Metrics: We evaluate WiDFS2.0 using two metrics:
1) Tracking Accuracy quantiﬁes the position errors in meters
between the measured and actual positions when a moving
person is correctly detected and 2) Scene Sensing Accuracy is
the ratio of the number of frames in which WiDFS2.0 correctly
identiﬁes an empty room or the presence of a moving person
to the total number of frames.
VII. R ESULTS
A. Overall Tracking Accuracy in LOS and NLOS
We start by comparing WiDFS2.0’s tracking accuracy in
three LOS scenarios, where a person moves along elliptical,
linear, and rectangle tracks. Fig. 6 shows the 50th percentile
errors in the x, y, and xy dimensions are 0.29, 0.39, and 0.55 m,
respectively. Even the 90th percentile error is less than 0.75 m
in the x-axis and less than 1.3 m in the y-axis. Since three RX
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5537
(a)
(b)
(c)
(d)
(e)
(f)
Fig. 10. Case of linear path tracking. (a) Linear trajectory. (b) AoA.
(c) Range. (d) X-axis coordinate. (e) Y-axis coordinate. (f) Estimated linear
trajectory.
antennas form a linear array along the x-axis, the x-axis has a
lower error than the y-axis.
Next, we evaluate WiDFS2.0 in NLOS conditions by intro-
ducing two obstacles, i.e., plastic box and wood board, to
block direct signal propagation paths. As expected, the error
in LOS is slightly lower than in NLOS. Fig. 7 illustrates
(a)
(b)
(c)
(d)
(e)
(f)
Fig. 11. Case of ellipse path tracking. (a) Rectangular trajectory. (b) AoA.
(c) Range. (d) X-axis coordinate. (e) Y-axis coordinate. (f) Estimated rectangle
trajectory.
the tracking error before and after placing each obstacle.
The 50th percentile error is 0.66 m for the plastic box and
0.90 m for the wood board, whereas the tracking error in
LOS is 0.55 m. The presence of obstacles can introduce
additional complexities in the signal propagation process, and
even there may not exist a dominant signal path between the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

5538 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
Fig. 12. Impact of CSI packets in a frame.
Fig. 13. Impact of joint frame size.
Fig. 14. Impact of SNR smoothing factor.
transmitter and receiver. As a result, WiDFS2.0 may encounter
more multipath, leading to a lower accuracy. Despite the
challenges in NLOS, WiDFS2.0 still demonstrates competitive
performance in tracking.
To intuitively demonstrate the tracking performance, we plot
different estimated trajectories, shown in Figs. 9(g), 10(g),
and 11(g) respectively. The positions of the transmitter
and receiver are also highlighted. The results show that
WiDFS2.0 matches the ground-truth trajectories well. The
accuracy of the elliptical and linear tracks is higher compared
to the rectangle track. When a person moves along the x-axis
direction of the rectangle track, the change in the reﬂection
distance is relatively small, leading to smaller DFS values. As
a result, it is more challenging to accurately separate dynamic
components.
B. Comparison to SOTA
We then compare WiDFS2.0’s tracking accuracy to the
SOTA methods WiDFS and Widar2.0. Fig. 8 illustrates the
CDF of the combined xy tracking accuracy. Both WiDFS and
WiDFS2.0 utilize a joint optimization technique by combining
CSI data across multiple frames. To ensure fairness in com-
parison, WiDFS2.0 adopts the same time interval of about 1
s as WiDFS for joint optimization.
TABLE I
SCENE SENSING ACCURACY (%). T HE TABLE SHOWS THE SCENE
SENSING ACCURACY FOR THREE TYPES OF TRACKS WHEN A MOVING
PERSON IS PRESENT .I T ALSO INCLUDES THE SENSING ACCURACY FOR
THE EMPTY ROOM WHERE NO PERSON IS PRESENT
WiDFS2.0 achieves a 50th percentile position error of
0.63 m and a 90th percentile error of 1.70 m. In comparison,
WiDFS has 50th and 90th percentile errors of 0.72 and
1.72 m, while Widar2.0’s errors are about 1.07 and 2.38 m.
It can be observed that WiDFS2.0 achieves median accuracy
improvements of approximately 0.09 and 0.44 m, respectively,
compared to WiDFS and Widar2.0. Also, when a person
moves closer to the receiver, the previous work WiDFS
may experience sudden position jumps due to some range
estimation errors. However, WiDFS2.0 effectively avoids this
issue, resulting in a smoother trajectory.
Despite our COTS WiFi system offering only 20 MHz band-
width with a distance resolution of 7.5 m and three receiving
antennas with an AoA resolution of 38 .2◦, WiDFS2.0 still
improves positioning accuracy by about 10 cm than WiDFS.
WiDFS2.0 utilizes richer signal features from various Doppler
bins while WiDFS only focuses on extracting a dominant DFS.
WiDFS2.0 also enhances target association across frames,
leading to more accurate human tracking.
C. Scene Sensing Accuracy
We evaluate whether WiDFS2.0 can correctly detect the
absence or presence of a moving person based on the number
of detected tracks in EKF-based tracking. Table I presents the
results for different types of tracks, along with the performance
in an empty room where no person is present. The table
includes the FP count and true positive (TP) count, and
the scene sensing accuracy is calculated as TP/(FP+TP) and
represented as a percentage.
For the elliptical track, WiDFS2.0 achieves 100% accuracy
with no FPs and 5574 TPs. For the linear track, despite six
FPs, the system correctly identiﬁes 5190 instances, resulting
in 99.88% accuracy. The rectangle track also achieves 100%
accuracy. In an empty room, 24 FPs occur, but 1968 instances
are correctly identiﬁed, giving an accuracy of 98.78%. These
results highlight WiDFS2.0’s effectiveness in detecting a
moving person and its advantage over WiDFS, as it does not
require prior thresholds, making it more robust for practical
use.
D. Realtime Performance
Table II provides a comparison of the average running times
between WiDFS and WiDFS2.0 on the same laptop platform
(MacBook Pro 2019). Both implementations are developed
using Python. No Python acceleration tricks are utilized in
WiDFS2.0. The experimental results show that the average
computation time of WiDFS2.0 between adjacent frames is
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5539
TABLE II
RUNNING TIME OF WIDFS AND WIDFS2.0 (S ECONDS )
Fig. 15. Impact of TX-RX separation distance.
Fig. 16. Impact of motion speed.
0.024 s, which is lower than the step size of 48 CSI packets
(approximately 0.048 s). WiDFS2.0 can maintain real-time
performance similar to the previous work WiDFS, even with
the additional functionalities and improvements introduced in
WiDFS2.0.
E. Tracking Accuracy Versus Different Parameters
The following section evaluates WiDFS2.0’s tracking accu-
racy as a function of different parameters, including the
number of CSI samples in a frame, joint frame size, SNR
smoothing factor, TX-RX separation distance, motion speed,
multiple individuals, and environment.
1) Impact of CSI Samples in Frame: We vary the number
of CSI samples in a CPI to 48, 64, 96, 128, and 256, respec-
tively. Fig. 12 shows that WiDFS2.0 achieves the median
tracking accuracy of 0.62, 0.59, 0.56, 0.57, and 0.59 m in the
xy dimension. There is only a slight difference in accuracy,
and the highest accuracy is observed when a WiFi frame
contains 96 CSI packets. The frames with a smaller number of
CSI samples exhibit higher accuracy ﬂuctuations. WiDFS2.0
requires more time to perform AoA and range estimation
in more Doppler bins. However, a higher resolution of the
Doppler velocity can be obtained. Thus, the use of 96 or 128
CSI samples in a CPI is suggested to achieve a balance among
Doppler resolution, computation time, and tracking accuracy.
2) Impact of Joint Frame Size: We vary the number of
frames in the joint optimization from 10, 20, 30, 40, 50, and
60, respectively. The default step size is 48 CSI samples,
so WiDFS2.0 performs joint optimization by combining CSI
samples during the corresponding intervals of 0.48, 0.96, 1.44,
Fig. 17. Impact of multiple individuals.
1.92, 2.40, and 2.88 s. Fig. 13 shows that the tracking error
gradually decreases as the number of frames increases. More
point clouds help WiDFS2.0 effectively suppress outliers.
However, it leads to a longer delay for each estimation. Here,
WiDFS2.0 uses 40 frames for joint optimization.
3) Impact of SNR Smoothing Factor: We evaluate the
impact of the SNR smoothing factor on tracking accuracy
by varying it from 0.9 to 1.0 with a spacing of 0.02. The
basic idea behind using a smoothing factor is to give higher
importance to the point clouds in the latest frames during the
joint optimization process, as they contain more up-to-date
information about the person’s motion.
Fig. 14 shows that the case with a smoothing factor of 0.98
achieves the highest tracking accuracy of 0.57 m, which is
slightly better than the other cases. When the smoothing factor
is set to 0.9, WiDFS2.0 has the lowest tracking accuracy of
0.61 m. However, applying the smoothing factor in WiDFS2.0
results in evident accuracy improvement. This may be mainly
due to the presence of noise in the estimated point clouds. It is
challenging to associate changes in the point cloud positions
with human motion in an one-to-one frame manner. The noise
inherent in WiFi systems can introduce high ﬂuctuations and
uncertainties in the estimated positions, making it difﬁcult to
accurately track a person’s movement using individual frames.
4) Impact of TX-RX Separation Distance: We investigate
the impact of varying the TX-RX separation on tracking
accuracy. We keep the RX antenna array ﬁxed and adjust
the distance of TX from 1.0 to 4.0 m with a spacing of
1.0 m. The tracked person follows the same trajectory. Fig. 15
shows that the median tracking errors are 0.59, 0.54, 0.99, and
0.66 m, respectively. The minimum error occurs at a spacing
of 2.0 m. This outcome may highlight the existence of a
tradeoff between the antenna separation and tracking accuracy.
When the transmitter and receiver are placed too close,
the strength of the LOS signal can overwhelm dynamic
multipath, challenging the separation of human reﬂections.
On the other hand, when the separation distance is too large,
it challenges the assumption that there exists one dominant
LOS signal. Surrounding objects may produce static multipath
signals that cannot be neglected. Moreover, a larger TX-RX
distance increases the sensitivity to distance measurement
errors according to (17). For instance, if dX = 5m , dS = 1
m, and (θX − θS) = 45◦, we can obtain dX→RX = 2.68 m.
However, if dX is slightly noisy and is dX = 5.5 m, we obtain
dX→RX = 2.94 m, introducing a distance error of 0.26 m.
Similarly, when dS is enlarged to 3 m, the estimated dX→RX
are 2.34 and 2.71 m with and without the presence of noise,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

5540 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
(a)
(b)
Fig. 18. CDF of tracking accuracy in a meeting room. (a) Meeting room.
(b) Tracking error.
resulting in a higher error of 0.37 m. Therefore, we should
select a proper TX-RX distance to balance the accuracy in
dynamic component separation and distance measurement.
5) Impact of Motion Speeds: Fig. 16 illustrates the impact
of different motion speeds on position error. The speeds are
categorized into four ranges: a) slow walking (0.5–1 m/s);
b) normal walking (1–1.5 m/s); c) fast walking (1.5–2 m/s);
and d) running (2–2.5 m/s). The xy-axis errors tend to remain
stable across the different speeds. As the human speed
increases, the DFS may also increases, making it easier to
separate dynamic targets from static clutter in the environment.
However, at higher speeds (2–2.5 m/s), we observe an increase
in outliers in position error. This is likely due to the by-product
term introduced when using the CACC method to eliminate
random phase offsets, as higher speeds amplify the effect
of this term, impacting localization accuracy. Despite this,
the system maintains reasonable tracking accuracy, with most
errors around 0.6 m, demonstrating WiDFS2.0’s capability to
handle varying motion speeds.
6) Impact of Multiple Individuals: Fig. 17 shows the posi-
tion error in both single-target and multitarget scenarios,
evaluating the system’s performance in the presence of
interfering moving targets. In the single-target scenario, there
is no interference from other targets. In the multitarget
experiments, the tracked target was positioned closer to the
transmitter and receiver than the interfering targets. In multitar-
get scenario 1, the interfering targets conduct small movements
while seated and working at a desk, whereas in multitarget
scenario 2, the interfering targets walk around within a small
area. We can see that the presence of the interfering targets has
little impact on the system’s localization accuracy. Although
the interfering moving targets generate some noisy point
clouds, their lower SNR values allow the system to distinguish
them from the tracked target. These noisy point clouds are
effectively suppressed during the SNR-weighted joint point
cloud optimization. The optimal point cloud is then passed
to the EKF tracker. This experiment illustrates WiDFS2.0’s
robustness in handling interference from other individuals.
7) Impact of Environment: We conducted an experiment
in a meeting room shown in Fig. 18, which has a smaller
area compared to the open environments tested earlier. The
presence of glass walls in this setting results in more severe
multipath reﬂections. The transceiver distance was set to
1.2 m, and the environment included reﬂectors, such as tables,
chairs, monitors, and a blackboard. The person moved repeat-
edly around the table. As shown in Fig. 18(b), the CDF
of tracking accuracy along the x-, y-, and xy-axis shows
median errors of 0.35, 0.46, and 0.61 m, respectively, with
90th percentile errors of 0.81, 1.11, and 1.34 m. The tracking
accuracy in this environment remains comparable to that of
the ofﬁce scenario, demonstrating the robustness of WiDFS2.0
across different environments.
VIII. R ELATED WORK
This section presents an overview of passive WiFi tracking
techniques, which can be broadly classiﬁed into two cate-
gories: 1) signal model-based and 2) deep learning-based. The
signal model-based schemes utilize classical signal processing
algorithms to analyze CSI models, while deep learning-based
methods rely on precollected training data. At present, the
data-driven deep learning methods [44], [45], [46], [47], [48],
[49] have gained signiﬁcant attention in passive WiFi tracking.
However, they face two critical challenges: 1) the lack of
labeled data and 2) the inconsistency of WiFi ﬁngerprints in
different environments. In contrast, the signal model-based
methods stands out as an unsupervised scheme without the
need for labeled training data and without being sensitive to
changes in the deployment environment or transceiver posi-
tion. In the following, we will mainly review these methods.
Many previous works focus on estimating the Doppler
information of a moving person for passive WiFi tracking.
IndoTrack [22] uses CACC to remove clock asynchronization
and applies an add-minus solution to suppress the mirrored
Doppler component in DFS estimation. The periodicity-based
method [27] optimizes the CASR model and proposes a
more efﬁcient DFS estimation method. FingerDraw [26],
WiTraj [42], and TD-CSI [43] estimates DFS using the
CASR (i.e., CSI-quotient) model. PITrack [18] demonstrates
that accurate DFS estimation yields receiver locations, and
it proposes a joint DFS and AoA estimation scheme by
selecting an optimal receiver. These methods calculate the
displacements of a person along the x and y axis based on
the decomposed Doppler velocities. The trajectory is then
constructed by adding these xy displacements at each time to
the current position. However, these methods are challenging
for long-term tracking due to the accumulation of tracking
errors over time. And their setups often involve multiple
receivers.
Widar2.0 [19], mD-Track [50], and mirrored-MUSIC [24]
uses joint parameter estimation schemes that simultaneously
estimate range, AoA, and DFS for tracking. WiTrack 2.0
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5541
and mD-Track utilize the CACC-based signal processing
technique and formulate the joint parameter estimation as an
MLE problem. mD-Track improves localization performance
through an iterative path parameter reﬁnement method.
However, these methods require accurate initial guesses for
MLE and may have high computational requirements, which
may hinder real-time tracking. Mirrored-MUSIC addresses the
computational complexity by using a novel MUSIC algorithm
to reduce the number of unknown mirrored parameters by
half. However, the real-time performance of the estimation still
needs to be further improved. Instead, WiDFS [16] proposes
a step-by-step parameter estimation scheme. It introduces a
variant CACC-based method to suppress mirrored dynamic
components. It ﬁrst estimates a dominant DFS of a moving
person, followed by estimating AoA and range, respectively,
for real-time tracking. In comparison, the improved WiDFS2.0
in this work optimizes the signal processing chain and can
extract multiple DFS, AoA, and range candidates for tracking.
SHARP [31] and JUMP [29] aim to establish a reference
static path to compensate for the effects of TO and CFO.
Since the static path typically exhibits the strongest amplitude
in LOS scenarios, SHARP employs compressive sensing
techniques to construct the reference signal for each antenna.
Meanwhile, JUMP utilizes a correlation-based algorithm to
estimate the relative TO across successive packets. Based on
this, it then identiﬁes the strongest static component as the
reference signal for CFO removal. However, the performance
of Doppler extraction and tracking in these methods is
constrained by the accuracy of TO and CFO compensation.
Achieving precise TO and CFO compensation is particularly
challenging in WiFi systems with the limited bandwidth.
Although WiDFS2.0 suffers from the byproduct terms in
CACC, their impacts can be suppressed during tracking by
jointly combining time, spatial, and frequency domains.
IX. C ONCLUSION
WiDFS2.0 is a passive WiFi tracking system capable
of achieving real-time and submeter position accuracy. The
system introduces a novel WiFi processing chain that generates
WiFi point clouds containing position coordinates, Doppler
velocity, and SNR for potential reﬂection objects. WiDFS2.0
utilizes an augmented EKF tracker for trajectory optimization.
The experimental results demonstrate that WiDFS2.0 exhibits
very low computational complexity and achieves a median
tracking accuracy of 0.55 m. It can also achieve an accu-
racy of over 98% in determining the presence of a moving
person. WiDFS2.0 can function effectively in practical sce-
narios without the need for environment-speciﬁc training.
The combination of its accuracy, real-time capabilities, and
robustness across various environments makes WiDFS2.0 a
highly promising solution for passive tracking applications.
In future work, we aim to explore deep learning-based
approaches, using WiFi point clouds as inputs to neural
networks, to improve robustness in complex NLOS condi-
tions. Additionally, combining WiDFS2.0 with complementary
localization systems (such as mmWave radar or LiDAR)
for multimodal fusion could enhance tracking accuracy and
overcome the low-bandwidth limitations of WiFi systems,
especially in challenging environments.
REFERENCES
[1] Y . He, J. Liu, M. Li, G. Yu, and J. Han, “Forward-compatible integrated
sensing and communication for WiFi,” IEEE J. Sel. Areas Commun. ,
vol. 42, no. 9, pp. 2440–2456, Sep. 2024.
[2] S. Lu et al., “Integrated sensing and communications: Recent advances
and ten open challenges,” IEEE Internet Things J. , vol. 11, no. 11,
pp. 19094–19120, Jun. 2024.
[3] K. Wu et al., “Sensing in Bi-static ISAC systems with clock asynchro-
nism: A signal processing perspective,” 2024, arXiv:2402.09048.
[4] J. A. Zhang, K. Wu, X. Huang, Y . J. Guo, D. Zhang, and R. W. Heath,
“Integration of radar sensing into communications with asynchronous
transceivers,” IEEE Commun. Mag. , vol. 60, no. 11, pp. 106–112,
Nov. 2022.
[5] D. Zhang et al., “Practical issues and challenges in CSI-based inte-
grated sensing and communication,” in Proc. IEEE Int. Conf. Commun.
Workshops (ICC Workshops), 2022, pp. 836–841.
[6] J. A. Zhang et al., “An overview of signal processing techniques for joint
communication and radar sensing,” IEEE J. Sel. Topics Signal Process. ,
vol. 15, no. 6, pp. 1295–1315, Nov. 2021.
[7] F. Luo, S. Khan, B. Jiang, and K. Wu, “Vision transformers for human
activity recognition using WiFi channel state information,”IEEE Internet
Things J., vol. 11, no. 17, pp. 28111–28122, Sep. 2024.
[8] Y . Zhang, A. Cheng, B. Chen, Y . Wang, and L. Jia, “A location-
independent human activity recognition method based on CSI: System,
architecture, implementation,” IEEE Trans. Mobile Comput. , vol. 23,
no. 5, pp. 4793–4805, May 2024.
[9] Y . Zhang et al., “Widar3.0: Zero-effort cross-domain gesture recognition
with Wi-Fi,” IEEE Trans. Pattern Anal. Mach. Intell. , vol. 44, no. 11,
pp. 8671–8688, Nov. 2022.
[10] Z. Shi, J. A. Zhang, R. Y . Xu, and Q. Cheng, “Environment-robust
device-free human activity recognition with channel-state-information
enhancement and one-shot learning,” IEEE Trans. Mobile Comput. ,
vol. 21, no. 2, pp. 540–554, Feb. 2022.
[11] D. Fan et al., “A contactless breathing pattern recognition system using
deep learning and WiFi signal,” IEEE Internet Things J., vol. 11, no. 13,
pp. 23820–23834, Jul. 2024.
[12] Z. Guo, W. Yuan, L. Gui, B. Sheng, and F. Xiao, “BreatheBand: A ﬁne-
grained and robust respiration monitor system using WiFi signals,” ACM
Trans. Sensor Netw., vol. 19, no. 4, pp. 1–18, 2023.
[13] D. Zhang, Y . Zeng, F. Zhang, and J. Xiong, “WiFi CSI-based vital signs
monitoring,” in Contactless Vital Signs Monitoring . Amsterdam, The
Netherlands: Elsevier, 2022, pp. 231–255.
[14] J. Zhang, Z. Chen, C. Luo, B. Wei, S. S. Kanhere, and J. Li, “MetaGanFi:
Cross-domain unseen individual identiﬁcation using WiFi signals,” Proc.
ACM Interact., Mob., Wearable Ubiquitous Technol. , vol. 6, no. 3,
pp. 1–21, 2022.
[15] K. Liu et al., “WiCrew: Gait-based crew identiﬁcation for cruise ships
using commodity WiFi,” IEEE Internet Things J. , vol. 10, no. 8,
pp. 6960–6972, Apr. 2023.
[16] Z. Wang, J. A. Zhang, M. Xu, and Y . J. Guo, “Single-target real-time
passive WiFi tracking,” IEEE Trans. Mobile Comput. , vol. 22, no. 6,
pp. 3724–3742, Jun. 2023.
[17] W. Ge et al., “CrossTrack: Device-free cross-link tracking with commod-
ity Wi-Fi,” IEEE Internet Things J. , vol. 10, no. 20, pp. 18028–18041,
Oct. 2023.
[18] K. Niu, X. Wang, F. Zhang, R. Zheng, Z. Yao, and D. Zhang,
“Rethinking Doppler effect for accurate velocity estimation with com-
modity WiFi devices,” IEEE J. Sel. Areas Commun. , vol. 40, no. 7,
pp. 2164–2178, Jul. 2022.
[19] K. Qian, C. Wu, Y . Zhang, G. Zhang, Z. Yang, and Y . Liu, “Widar2.0:
Passive human tracking with a single Wi-Fi link,” in Proc. ACM 16th
Annu. Int. Conf. Mob. Syst., Appl., Serv. , 2018, pp. 350–361.
[20] N. Tadayon, M. T. Rahman, S. Han, S. Valaee, and W. Yu, “Decimeter
ranging with channel state information,” IEEE Trans. Wireless Commun.,
vol. 18, no. 7, pp. 3453–3468, Jul. 2019.
[21] M. Kotaru, K. Joshi, D. Bharadia, and S. Katti, “SpotFi: Decimeter level
localization using WiFi,” in Proc. ACM Conf. Spec. Interest Group Data
Commun., 2015, pp. 269–282.
[22] X. Li et al., “IndoTrack: Device-free indoor human tracking with
commodity Wi-Fi,” Proc. ACM Interact., Mob., Wearable Ubiquitous
Technol., vol. 1, no. 3, pp. 1–22, 2017.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

5542 IEEE INTERNET OF THINGS JOURNAL, VOL. 12, NO. 5, 1 MARCH 2025
[23] K. Qian, C. Wu, Z. Zhou, Y . Zheng, Z. Yang, and Y . Liu,
“Inferring motion direction using commodity Wi-Fi for interactive
exergames,” in Proc. CHI Conf. Hum. Factors Comput. Syst. , 2017,
pp. 1961–1972.
[24] Z. Ni, J. A. Zhang, X. Huang, K. Yang, and J. Yuan, “Uplink sensing
in perceptive mobile networks with asynchronous transceivers,” IEEE
Trans. Signal Process., vol. 69, pp. 1287–1300, Feb. 2021.
[25] Y . Zeng, D. Wu, J. Xiong, E. Yi, R. Gao, and D. Zhang, “FarSense:
Pushing the range limit of WiFi-based respiration sensing with CSI
ratio of two antennas,” Proc. ACM Interact., Mob., Wearable Ubiquitous
Technol., vol. 3, no. 3, pp. 1–26, 2019.
[26] D. Wu et al., “FingerDraw: Subwavelength level ﬁnger motion tracking
with WiFi signals,” Proc. ACM Interact., Mob., Wearable Ubiquitous
Technol., vol. 4, no. 1, pp. 1–27, 2020.
[27] X. Li, J. A. Zhang, K. Wu, Y . Cui, and X. Jing, “CSI-ratio-based Doppler
frequency estimation in integrated sensing and communications,” IEEE
Sensors J., vol. 22, no. 21, pp. 20886–20895, Nov. 2022.
[28] Z. Yao, X. Wang, K. Niu, R. Zheng, J. Wang, and D. Zhang, “WiProﬁle:
Unlocking diffraction effects for subcentimeter target proﬁling using
commodity WiFi devices,” in Proc. 30th Annu. Int. Conf. Mob. Comput.
Netw., 2024, pp. 185–199.
[29] J. Pegoraro et al., “JUMP: Joint communication and sensing with
unsynchronized transceivers made practical,” IEEE Trans. Wireless
Commun., vol. 23, no. 8, pp. 9759–9775, Aug. 2024.
[30] J. Zhao, Z. Lu, J. A. Zhang, S. Dong, and S. Zhou, “Multiple-target
Doppler frequency estimation in ISAC with clock asynchronism,” IEEE
Trans. Veh. Technol., vol. 73, no. 1, pp. 1382–1387, Jan. 2024.
[31] F. Meneghello, D. Garlisi, N. D. Fabbro, I. Tinnirello, and M. Rossi,
“SHARP: Environment and person independent activity recognition with
commodity IEEE 802.11 access points,” IEEE Trans. Mobile Comput. ,
vol. 22, no. 10, pp. 6160–6175, Oct. 2023.
[32] D. Halperin, W. Hu, A. Sheth, and D. Wetherall, “Tool release: Gathering
802.11n traces with channel state information,” ACM SIGCOMM
Comput. Commun. Rev., vol. 41, no. 1, p. 53, 2011.
[33] V . C. Chen, F. Li, S.-S. Ho, and H. Wechsler, “Micro-Doppler effect in
radar: Phenomenon, model, and simulation study,” IEEE Trans. Aerosp.
Electron. Syst., vol. 42, no. 1, pp. 2–21, Jan. 2006.
[34] A. Pearce, J. A. Zhang, R. Xu, and K. Wu, “Multiobject tracking with
mmWave radar: A review,” Electronics, vol. 12, no. 2, p. 308, 2023.
[35] A. M. Elbir, K. V . Mishra, S. A. V orobyov, and R. W. Heath,
“Twenty-ﬁve years of advances in beamforming: From convex and
nonconvex optimization to learning techniques,” IEEE Signal Process.
Mag., vol. 40, no. 4, pp. 118–131, Jun. 2023.
[36] M. A. Richards, Fundamentals of Radar Signal Processing ,v o l .1 .N e w
York, NY , USA: Mcgraw-hill, 2005.
[37] Y . Ma, G. Zhou, and S. Wang, “WiFi sensing with channel state
information: A survey,” ACM Comput. Surv. , vol. 52, no. 3, pp. 1–36,
2019.
[38] Y . Xie, Z. Li, and M. Li, “Precise power delay proﬁling with commodity
WiFi,” in Proc. 21st Annu. Int. Conf. Mob. Comput. Netw. , 2015,
pp. 53–64.
[39] Z. Jiang et al., “Eliminating the barriers: Demystifying Wi-Fi baseband
design and introducing the PicoScenes Wi-Fi sensing platform,” IEEE
Internet Things J. , vol. 9, no. 6, pp. 4476–4496, Mar. 2022.
[40] M. A. Richards, Fundamentals of Radar Signal Processing .N e wY o r k ,
NY , USA: McGraw-Hill Educ., 2014.
[41] Z. J. Ostrowski, “The Doppler effect in a bistatic system for determining
the position of moving targets,” Hydroacoustics, no. 17, pp. 161–170,
2014.
[42] D. Wu et al., “WiTraj: Robust indoor motion tracking with WiFi
signals,” IEEE Trans. Mobile Comput. , vol. 22, no. 5, pp. 3062–3078,
May 2023.
[43] W. Li et al., “WiFi-CSI difference paradigm: Achieving efﬁcient Doppler
speed estimation for passive tracking,” Proc. ACM Interact., Mob.,
Wearable Ubiquitous Technol., vol. 8, no. 2, pp. 1–29, 2024.
[44] J. Yang, X. Chen, H. Zou, D. Wang, and L. Xie, “AutoFi: Toward
automatic Wi-Fi human sensing via geometric self-supervised learn-
ing,” IEEE Internet Things J., vol. 10, no. 8, pp. 7416–7425, Apr. 2023.
[45] H. Huang, J. Yang, X. Fang, H. Jiang, and L. Xie, “VariFi: Variational
inference for indoor pedestrian localization and tracking using IMU and
WiFi RSS,” IEEE Internet Things J. , vol. 10, no. 10, pp. 9049–9061,
May 2023.
[46] X. Zhang, H. Xu, J. Liu, and J. Han, “TomFi: Small object tracking using
commodity WiFi,” ACM Trans. Sens. Netw. , vol. 24, no. 4, pp. 1–15,
2023.
[47] J. Yang et al., “SenseFi: A library and benchmark on deep-learning-
empowered WiFi human sensing,” Patterns, vol. 4, no. 3, 2023,
Art. no. 100703.
[48] X. Chen, Y . Zou, C. Li, and W. Xiao, “A deep learning based lightweight
human activity recognition system using reconstructed WiFi CSI,” IEEE
Trans. Human-Mach. Syst., vol. 54, no. 1, pp. 68–78, Feb. 2024.
[49] X. Zheng, K. Yang, J. Xiong, L. Liu, and H. Ma, “Pushing the limits of
WiFi sensing with low transmission rates,”IEEE Trans. Mobile Comput.,
vol. 23, no. 11, pp. 10265–10279, Nov. 2024.
[50] Y . Xie, J. Xiong, M. Li, and K. Jamieson, “mD-Track: Leveraging
multidimensionality for passive indoor Wi-Fi tracking,” in Proc. 25th
Annu. Int. Conf. Mob. Comput. Netw. , 2019, pp. 1–16.
Zhongqin Wang received the M.S. degree
from Nanjing University of Posts and
Telecommunications, Nanjing, China, in 2014, and
the Ph.D. degree from the University of Technology
Sydney, Ultimo, NSW, Australia, in 2021.
He is currently a Postdoctoral Research Fellow
with the School of Electrical and Data Engineering,
University of Technology Sydney. He was as
a Lecturer with the School of Information
Engineering, Capital Normal University, Beijing
China, from 2022 to 2023. He has many papers in
high-quality conferences and journals. His research interests include wireless
sensing and ISAC.
Dr. Wang also serves as a reviewer for IEEE I NTERNET OF THINGS
JOURNAL , IEEE J OURNAL OF SELECTED TOPICS IN SIGNAL PROCESSING ,
IET Communications, IJCAI, and IEEE ICC.
J. Andrew Zhang (Senior Member, IEEE)
received the B.Sc. degree from Xi’an Jiaotong
University, Xi’an, China, in 1996, the M.Sc.
degree from Nanjing University of Posts and
Telecommunications, Nanjing, China, in 1999,
and the Ph.D. degree from Australian National
University, Canberra, ACT, Australia, in 2004.
He is currently a Professor with the School
of Electrical and Data Engineering, University of
Technology Sydney, Ultimo, NSW, Australia. He
was a Researcher with Data61, CSIRO, Eveleigh,
NSW, from 2010 to 2016; Networked Systems, NICTA, Sydney, NSW,
from 2004 to 2010; and ZTE Corporation, Nanjing, from 1999 to 2001.
He has published more than 300 papers in leading journals and conference
proceedings. His research interests include area of signal processing for
wireless communications and sensing, with a focus on integrated sensing and
communications.
Dr. Zhang has won six Best Paper Awards for his work, including IEEE
ICC 2013. He is a recipient of the CSIRO Chair’s Medal and the Australian
Engineering Innovation Award in 2012 for exceptional research achievements
in multigigabit wireless communications.
Haimin Zhang received the bachelor’s degree from
Zhejiang Sci-Tech University, Hangzhou, China, in
2010, the master’s degree from Nankai University,
Tianjin, China, in 2015, and the Ph.D. degree from
University of Technology Sydney, Ultimo, NSW,
Australia, in 2020.
He is a Postdoctoral Research Associate with
the School of Electrical and Data Engineering,
University of Technology Sydney. His research
interests include pattern recognition, machine learn-
ing, computer vision, and multimedia analytics.
Dr. Zhang serves as a reviewer for many highly rated international
conferences and journals, such as IEEE T RANSACTIONS ON MULTIMEDIA
AND PATTERN RECOGNITION .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply. 

W ANG et al.: PASSIVE HUMAN TRACKING WITH WiFi POINT CLOUDS 5543
Min Xu (Member, IEEE) received the B.E. degree
from the University of Science and Technology of
China, Hefei, China, in 2000, the M.S. degree from
the National University of Singapore, Singapore, in
2004, and the Ph.D. degree from the University of
Newcastle, Callaghan NSW, Australia, in 2010.
She is currently an Associate Professor with the
University of Technology Sydney, Ultimo, NSW.
She has published over 100 research papers in high
quality international journals and conferences. Her
research interests include multimedia data analytics,
computer vision, and machine learning.
Dr. Xu has been invited to be a Program Committee Member for many
international top conferences, including ACM Multimedia Conference and
reviewer for various highly rated international journals, such as IEEE
TRANSACTIONS ON MULTIMEDIA and IEEE T RANSACTIONS ON CIRCUITS
AND SYSTEMS FOR VIDEO TECHNOLOGY . She is an Associate Editor of
Journal of Neurocomputing .
Jay Guo (Fellow, IEEE) received the bachelor’s
and master’s degrees from Xidian University, Xi’an,
China, in 1982 and 1984, respectively, and the Ph.D.
degree from Xi’an Jiaotong University, Xi’an, in
1987.
He is a Distinguished Professor and the Director
of the Global Big Data Technologies Centre,
University of Technology Sydney (UTS), Ultimo,
NSW, Australia. He is the Founding Technical
Director of the New South Wales Connectivity
Innovation Network, Ultimo. Prior to joining UTS
in 2014, he served as the Director with CSIRO, Acton, ACT, Australia, for
over nine years. Before joining CSIRO, he held various senior technology
leadership positions with Fujitsu, Düsseldorf, Germany, and Siemens and
NEC, Reading, U.K. He has published four books, over 600 research papers,
including 280 IEEE transactions papers, and 26 international patents. His
research interest includes antennas, mm-wave and THz communications and
sensing systems, and big data technologies.
Prof. Guo has won a number of most prestigious Australian Engineering
Excellence Awards in 2007 and 2012 and the CSIRO Chairman’s Medal
in 2007 and 2012. He was named one of the most inﬂuential engineers in
Australia, in 2014 and 2015, and one of the top researchers across ﬁelds
in Australia, in 2020 and 2021. He has chaired numerous international
conferences and served as guest editors for a number of IEEE publications.
He is the Chair of the International Steering Committee and the International
Symposium on Antennas and Propagation. He has been the International
Advisory Committee Chair of IEEE VTC 2017, the General Chair of ISAP
2022, ISAP 2015, iW AT 2014, and WPMC 2014, and the TPC Chair
of IEEE WCNC 2010 and IEEE ISCIT in 2012 and 2007. He served
as the Guest Editor for Special Issues on Low-Cost Wide-Angle Beam
Scanning Antennas, Antennas for Satellite Communications, and Antennas
and Propagation Aspects of 60–90 GHz Wireless Communications all in
IEEE T RANSACTIONS ON ANTENNAS AND PROPAGATION , Special Issue
on Communications Challenges and Dynamics for Unmanned Autonomous
Vehicles in IEEE J OURNAL ON SELECTED AREAS IN COMMUNICATIONS ,
and Special Issue on 5G for Mission Critical Machine Communications in
IEEE Network Magazine . He was a member of the College of Experts of
Australian Research Council from 2016 to 2018. He is a Fellow of IET and
the Australian Academy of Engineering and Technology.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:26:00 UTC from IEEE Xplore.  Restrictions apply.