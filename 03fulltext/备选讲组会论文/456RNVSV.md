---
type: literature-fulltext
title: "Deep Learning-Based Dynamic Environment Reconstruction for Vehicular ISAC Scenarios"
zotero_key: "456RNVSV"
pdf_key: "HU9A4BHV"
doi: "10.1109/TWC.2026.3676063"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Deep Learning-Based Dynamic Environment Reconstruction for Vehicular ISAC Scenarios.md"
fulltext_path: "03fulltext/备选讲组会论文/456RNVSV.md"
zotero_item: "zotero://select/library/items/456RNVSV"
zotero_pdf: "zotero://open-pdf/library/items/HU9A4BHV"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Deep Learning-Based Dynamic Environment Reconstruction for Vehicular ISAC Scenarios

> PDF 原文逐页文本抽取；来源文件 SHA-256：`eedcef8fa485c698700881b73d1c9ac4e99024818494f24d7b2f2096bc13239a`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

14198 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Deep Learning-Based Dynamic Environment
Reconstruction for Vehicular ISAC Scenarios
Junzhe Song
 , Ruisi He
 , Senior Member, IEEE, Mi Yang
 , Member, IEEE,
Zhengyu Zhang
 , Student Member, IEEE, Bingcheng Liu
 , Jiahui Han, Haoxiang Zhang
 ,
and Bo Ai, Fellow, IEEE
Abstract—Integrated Sensing and Communication (ISAC)
technology plays a critical role in future intelligent transportation
systems, by enabling vehicles to perceive and reconstruct the
surrounding environment through reuse of wireless signals,
thereby reducing or even eliminating the need for additional
sensors such as LiDAR or radar. However, existing ISAC-based
reconstruction methods often lack the ability to track dynamic
scenes with sufﬁcient accuracy and temporal consistency, lim-
iting the real-world applicability. To address this limitation,
we propose a deep learning based framework for vehicular
environment reconstruction by using ISAC channels. We ﬁrst
establish a joint channel–environment dataset based on multi-
modal measurements from real-world urban street scenarios.
Then, a multi-stage deep learning network is developed to recon-
struct the environment. Speciﬁcally, a scene decoder identiﬁes
the environmental semantic context such as buildings, trees,
and so on; a semantic center decoder predicts coarse spatial
layouts by localizing dominant object centers; a point cloud
decoder recovers ﬁne-grained geometry and structure of sur-
rounding environments. Experimental results demonstrate that
the proposed method achieves high-quality global reconstruction
of dynamic environments, with a Chamfer Distance of 0.29
and F-score@0.5m of 0.87. In addition, complexity analysis
demonstrates the efﬁciency and practical applicability of the
method in real-time scenarios. This work provides a pathway
toward low-cost environment reconstruction based on ISAC for
future intelligent transportation.
Index Terms—ISAC, dynamic environment reconstruction,
channel measurement, deep learning.
I. I NTRODUCTION
I
NTEGRATED Sensing and Communication (ISAC) has
been identiﬁed by International Telecommunication Union
Received 30 July 2025; revised 16 December 2025 and 12 March 2026;
accepted 15 March 2026. Date of current version 26 March 2026. This work
was supported by the National Natural Science Foundation of China under
Grant 62431003 and Grant 62271037. The associate editor coordinating the
review of this article and approving it for publication was N. Shlezinger.
(Corresponding author: Ruisi He.)
Junzhe Song, Ruisi He, Mi Yang, Zhengyu Zhang, and Bo Ai are with
the State Key Laboratory of Advanced Rail Autonomous Operation, the
School of Electronics and Information Engineering, and the Frontiers Science
Center for Smart High-Speed Railway System, Beijing Jiaotong University,
Beijing 100044, China (e-mail: 23125052@bjtu.edu.cn; ruisi.he@bjtu.edu.cn;
myang@bjtu.edu.cn; 21111040@bjtu.edu.cn; boai@bitu.edu.cn).
Bingcheng Liu is with the Aerospace Information Research Insti-
tute, Chinese Academy of Sciences, Beijing 100094, China (e-mail:
liubc@aircas.ac.cn).
Jiahui Han and Haoxiang Zhang are with China Academy of Industrial,
Ministry of Industry and Information Technology, Beijing 100804, China
(e-mail: hjh1760708@126.com; zhx61778294@126.com).
Digital Object Identiﬁer 10.1109/TWC.2026.3676063
Radiocommunication Sector (ITU-R) as a key feature of next-
generation networks and is recognized as one of the six core
visions of IMT-2030 (6G) [1], [2], [3]. ISAC aims to achieve a
deep integration of communication and sensing functionalities
by leveraging shared spectrum and hardware resources [4], [5].
In ISAC-enabled scenarios, network infrastructure is no longer
limited to data transmission and connectivity, it also serves
as a distributed sensing platform for environmental imaging
and three-dimensional (3D) reconstruction tasks. Millimeter-
wave (mmWave) frequencies, with their large bandwidth,
narrow beamwidth, and high spatial resolution, offer unique
advantages in ISAC systems [6], [7]. These characteristics
make mmWave ISAC particularly effective for target detec-
tion, scene modeling, and environmental perception [8]. In
vehicular ISAC scenarios, vehicles can use existing commu-
nication systems to perceive the surrounding environment.
This offers a low-cost, highly integrated solution that reduces
the dependency on expensive dedicated sensing equipment,
such as LiDAR or radar, particularly for large-scale deploy-
ment, thereby signiﬁcantly lowering the cost of environmental
perception [9]. Unlike traditional static ISAC scenarios, vehic-
ular ISAC faces unique challenges such as rapidly changing
environments and continuously varying observation angles,
which impose stricter requirements on perception accuracy
and temporal consistency [10]. Therefore, developing dynamic
environment reconstruction techniques tailored for vehicular
ISAC scenarios has signiﬁcant practical relevance and techni-
cal value.
Traditionally, 3D environment reconstruction using wireless
signals primarily relies on Frequency-Modulated Continuous
Wave (FMCW) signals transmitted by mmWave radar systems,
with Fast Fourier Transform (FFT) techniques commonly
employed for echo signal processing [11]. Various work
has focused on leveraging mmWave radar echoes for target
detection, point cloud reconstruction, and even scene-level
semantic understanding, demonstrating considerable potential
in applications such as autonomous driving [12], [13], [14],
security and health monitoring [15], [16], and Internet of
Things (IoT) [17], [18]. However, such works typically rely
on dedicated sensing hardware (e.g., LiDAR, RGB-D cam-
eras), which are costly, power-intensive, and highly sensitive
to adverse environmental conditions such as rain, fog, and
lighting variations, making them unsuitable for long-term
deployment in resource-constrained edge dynamic scenarios
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

SONG et al.: DEEP LEARNING-BASED DYNAMIC ENVIRONMENT RECONSTRUCTION 14199
[19]. Moreover, sensing tasks are often designed indepen-
dently and deployed redundantly, resulting in low spectral
efﬁciency and failing to meet the demands of future ubiquitous
intelligent systems for low-cost, highly integrated sensing-
communication platforms [20], [21]. With the advancement of
ISAC, communication-based environment reconstruction has
become a new research trend. ISAC offers inherent advan-
tages such as spectrum sharing, joint resource scheduling,
and hardware co-design, enabling the development of highly
integrated and energy-efﬁcient 3D dynamic reconstruction
systems. However, FMCW waveforms are not compatible
with communication schemes, making existing reconstruction
solutions difﬁcult to adapt to ISAC applications [22], [23].
Therefore, the development of ISAC-based environment recon-
struction methods has become critical.
In wireless communication systems, the channel refers to
the physical medium through which electromagnetic signals
propagate from the transmitter (Tx) to the receiver (Rx).
Unlike traditional communication channels that are used exclu-
sively for data transmission, ISAC channels simultaneously
carry user signals and embed rich information of surrounding
environments [24]. Channel parameters, such as delay, azimuth
angle of arrival (AoA), and elevation angle of arrival (EoA),
essentially characterize the physical propagation process of
signals in space, making the reconstruction of the environ-
mental geometry from the channel information physically
feasible [25]. Current research on ISAC-enabled environment
reconstruction mainly follows two pathways: one relies on
communication channel information, and the other on sens-
ing channel feedback. The former often adopts multi-node
cooperative architectures, leveraging geometric patterns and
statistical variations in received signals to infer the environ-
ment. For example, Chang et al. proposed a multi-object
reconstruction method by clustering reﬂection points along
communication paths, validated under THz band experiments
[26], Lu et al. developed a communication channel-driven
reconstruction framework enabling multi-user joint modeling
[27]. However, this work relies on simulation data and employs
deep learning primarily for point cloud density enhancement
following traditional signal processing (e.g., MUSIC, CFAR),
rather than direct channel-to-geometry mapping. In contrast,
reconstruction approaches based on sensing channels typically
extract multi-path characteristics from the observation points
to restore environmental structure. For example, Blandino et al.
reconstructed UA V 3D positions based on sensing channel
observations [28], while Yin et al. proposed a dual-base
cooperation model that utilizes uplink echoes to achieve 3D
imaging [29]. Although these studies demonstrate the feasi-
bility of using ISAC channels for environment reconstruction,
most existing works still rely on simulation data or idealized
experimental setups, such as indoor scenes, static targets, or
isolated object localization. Consequently, their performance
degrades signiﬁcantly in highly dynamic trafﬁc scenarios.
As highlighted in [30], when dynamic scatterers vary fre-
quently, the stability and interpretability of mmWave channel
parameters deteriorate, severely impacting the continuity and
accuracy of 3D reconstruction. Moreover, Ref. [31] points
out that current methods generally lack effective alignment
mechanisms for dynamic target features, limiting their appli-
cability in high-mobility tasks such as Vehicle-to-Everything
(V2X) communication and autonomous driving. Therefore, the
development of ISAC channel-based reconstruction methods
adapted for dynamic environments has become urgent and
critical for future research.
Although the ISAC channel inherently contains rich
information about the surrounding environment, its high-
dimensional and abstract features make it challenging to
establish an explicit mapping to dynamic environments [32].
In this context, deep learning excels at modeling such complex
and structured data [33], [34]. Several studies have explored
the application of deep learning techniques to tasks involv-
ing channel feature processing. For example, Nagao et al.
employed a Vision Transformer architecture to process multi-
channel spatiotemporal features for detecting weak seismic
events [35], Yun et al. utilized a Transformer to extract the
impact of channel variations on semantic tasks, addressing
multi-task optimization in dynamic wireless environments
[36]; Fang et al. proposed a digital twin-assisted deep rein-
forcement learning (DT-DRL) framework to learn directional
channel characteristics and reconstruct wireless environments
[37], Liu et al. leveraged generative adversarial networks
(GANs) to learn channel characteristics in IoV scenarios,
generating adaptive channel responses to the environment[38].
These studies demonstrate the signiﬁcant advantages of deep
learning models in handling high-dimensional, dynamic, and
structurally dependent channel characteristics.
Dynamic vehicular scenarios impose stringent requirements
on 3D environment reconstruction, demanding both low-
cost and high-accuracy solutions. However, most existing
works often fail to perform well in dynamic and complex
environments, whereas the structural information embedded
in ISAC channels opens up new possibilities for accurate
and robust reconstruction. Speciﬁcally, this paper utilizes
ISAC channel information (multi-path parameters: delay,
AoA, and EoA) for reconstruction, addressing two core
challenges: 1) The difﬁculty of establishing an explicit map-
ping from the high-dimensional and abstract ISAC channel
characteristics to the dynamic environment. 2) Overcoming
the limitations of existing ISAC methods that rely heav-
ily on simulation or idealized static data, demanding a
robust solution for highly dynamic vehicular scenarios. To
address the aforementioned challenges, this paper proposes
a dynamic 3D environment reconstruction method based on
ISAC channel, integrated with deep learning. The main con-
tributions and innovations of this work are summarized as
follows:
• A deep learning based dynamic environment method is
proposed, driven by ISAC channel data. This method
exploits the physical characteristics of multi-path prop-
agation in sensing channel to recover complete 3D
environment point cloud from sparse channel parameters.
• A uniﬁed vehicle-mounted ISAC and LiDAR measure-
ment platform is developed and deployed for synchro-
nized data collection at 28 GHz in real road scenarios,
enabling joint acquisition of channel data and LiDAR
point clouds in dynamic environments.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

14200 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. An overview of the proposed method framework.
• A multi-stage channel-to-reconstruction network (MSCR-
Net) is proposed, following a progressive training and
cascade guidance strategy to sequentially achieve scene
classiﬁcation, semantic center localization, and point
cloud generation.
The remainder of this paper is organized as follows:
Section II outlines the proposed framework. Section III
presents the ISAC channel measurement. SectionIV details the
data pre-processing. Section V details the architecture of the
proposed MSCR-Net. Section VI evaluates the performance of
the model. Finally, Section VII concludes the paper.
II. E NVIRONMENT RECONSTRUCTION FRAMEWORK
We propose a mmWave ISAC channel data driven method
for dynamic 3D environment reconstruction, with the over-
all framework illustrated in Fig. 1. The proposed method
leverages both channel characteristics and LiDAR point cloud
data to train a model capable of reconstructing dynamic 3D
environment. ISAC channel data can typically be obtained
through Ray-Tracing simulations [39] or real-world measure-
ments. Compared to Ray-Tracing, measurement-based data
offer greater authenticity and representativeness in capturing
environmental complexity and dynamic variations, making
them more suitable for evaluating the generalization capability
of the model. We built an integrated measurement platform,
where a pair of transceivers forms the sensing link. Meanwhile,
LiDAR is employed to acquire high-resolution point clouds
as ground-truth supervision for model training. In addition, a
RGB panoramic camera is employed to assist in identifying
the scene category of each sample.
During the data pre-processing stage, the receiver ﬁrst
acquires the raw in-phase and quadrature (IQ) signals, which
are calibrated and transformed to obtain the Channel Impulse
Response (CIR). Subsequently, the CIR data are processed
using the Space Alternating Generalized Expectation Maxi-
mization (SAGE) algorithm to extract the channel parameters
for each snapshot, including the propagation delay τ, AOA
θ, and EOA φ. The SAGE algorithm is a widely used high-
resolution parameter estimation (HRPE) algorithm based on
the expectation-maximization (EM) framework, with detailed
descriptions found in [40], [41], and [42]. Finally, de-noising
and spurious path ﬁltering are applied to construct a set of
channel feature vectors consisting ofN multi-path components
(MPCs). This can be expressed as:
Θ ={(τi,θi,φi)}Ni=1 (1)
The point cloud data acquired from LiDAR is ﬁrst down-
sampled to reduce environmental redundancy and alleviate
training complexity. Subsequently, Principal Component Anal-
ysis (PCA) is applied to align the coordinate axes of the
point cloud data. Since the raw LiDAR data is in a Cartesian
ego-centric frame, PCA is utilized to align the principal
axes—orienting the y-axis parallel to the vehicle’s heading, the
x-axis to the sensing direction, and the z-axis vertically. This
correction addresses axis offsets caused by vehicle motion and
ensures spatial consistency. Detailed descriptions of PCA can
be found in [43] and [44]. Given that the LiDAR provides a
360-degree ﬁeld of view while the ISAC channel has a limited
sensing range, certain parts of the point cloud may contain
information beyond the ISAC perception scope. Therefore,
spatial cropping is essential to ensure spatial consistency
between the point cloud and the channel data. Each frame
of point cloud is denoted as:
P ={pj = (xj,yj, zj)}Mj=1 (2)
where M represents the number of valid points in the point
cloud and pj denotes the 3D coordinates of the j-th sampled
point.
Subsequently, the processed point cloud P and the set of
channel parameters Θ are paired sample by sample based
on timestamp and spatial location to ensure environmental
consistency across the training data. Scene labels are manually
annotated using panoramic RGB video frames in conjunction
with the point cloud data, and are categorized into classes
such as “scenes containing buildings or trees only”, “scenes
containing both buildings and trees”. These labels support the
multi-task training process in the proposed framework.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

SONG et al.: DEEP LEARNING-BASED DYNAMIC ENVIRONMENT RECONSTRUCTION 14201
Fig. 2. The measurement campaign.
The model is trained on the constructed dataset to learn a
mapping from channel characteristics to environmental repre-
sentations:
ˆP =f(Θ) (3)
where Θ denotes the input set of channel characteristics, ˆP
is the reconstructed 3D environment, and f represents the
proposed MSCR-Net, which will be elaborated in Section V.
In this work, we adopt point clouds, a widely used format
in the robotics domain to represent the geometric structure
of the reconstructed 3D environment [45]. This representation
has been utilized in recent learning-based 3D reconstruction
studies [46], [47], [48]. A point cloud models an object as
an unordered set of points sampled from its surface, each
represented by its 3D Cartesian coordinates. Compared to
voxel-based representations, point clouds offer high-resolution
geometry encoding with signiﬁcantly lower memory overhead.
III. ISAC C HANNEL MEASUREMENTS
In this section, we present the vehicular ISAC channel
measurement campaign conducted to validate the proposed
reconstruction framework. We detail the construction of a
high-precision multi-modal measurement platform capable of
simultaneously capturing mmWave channel parameters and
environmental ground truths. These real-world measurements
serve as the fundamental basis for establishing the joint
channel-environment dataset, ensuring that the subsequent
deep learning model is trained on physically accurate prop-
agation characteristics.
A. Measurement Equipment
The vehicular channel measurement system for ISAC sce-
narios is designed with key components, as shown in Fig. 2.
These include a signal generator-based TX, a signal digitizer-
based RX, a LiDAR, and a 360-degree camera. This setup
enables simultaneous sensing of the electromagnetic and phys-
ical environments for comprehensive situational awareness.
The TX employs a signal generator, the National Instru-
ments (NI) PXIe-5745 (also known as the PXI FlexRIO
Signal Generator). The RX employs a signal analyzer, the NI
PXIe-5775 (also known as the PXI FlexRIO Digitizer). The
probing signal is a multi-carrier waveform with a center
frequency of 28 GHz and a bandwidth of 1 GHz. For antenna
conﬁgurations, the Tx is equipped with a horn antenna, while
TABLE I
CONFIGURATIONS OF MEASUREMENT SYSTEM
the Rx uses a 4× 8 antenna array. To ensure synchronization
between the Tx and Rx, both ends are disciplined by GPS-
referenced rubidium clocks providing a 10 MHz reference
pulse. The detailed conﬁguration of the measurement system
is summarized in TABLE I. For physical dynamic environment
sensing, a LiDAR and 360-degree panoramic camera are
positioned with the TX/RX, capturing point cloud data, RGB
video, and channel data simultaneously.
It is important to note that while this speciﬁc measurement
setup is specialized, the employed SAGE algorithm effectively
de-embeds the antenna patterns during parameter extraction.
Consequently, the resulting channel parameters represent the
intrinsic propagation environment, independent of the speciﬁc
measurement hardware. The primary objective of this setup
is channel sounding rather than practical beamforming for
data transmission. In channel sounding, using a Tx horn
antenna ensures that the probing signal illuminates a broader
spatial area to capture all potential environmental multipath
components comprehensively, whereas practical directional
beamforming would spatially ﬁlter out many reﬂectors. The
main advantage of this setup, combined with the planar Rx
array, is its ability to extract highly stable and accurate
angular and delay resolutions of the intrinsic environment
without being biased by a narrow transmit beam. However,
the limitation is that this sounding-focused setup does not
reﬂect the hardware imperfections or dynamic beam-sweeping
overhead inherent in practical commercial ISAC transceivers.
B. Measurement Campaign
To construct ISAC channel characteristics and the corre-
sponding LiDAR point cloud dataset, we conducted a ﬁeld
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

14202 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
measurement campaign at Beijing Jiaotong University in
Beijing, China. The measurement campaign covers four test
routes, as illustrated in Fig. 2. The test vehicle moved at
a constant speed of approximately 10 km/h in a clockwise
direction. The sensing direction of the channel measurement
equipment is ﬁxed to the left side of the vehicle’s motion.
This side-looking conﬁguration was speciﬁcally selected to
optimize the 3D reconstruction of roadside infrastructure (e.g.,
street canyons and building facades) for high-precision map-
ping tasks. Unlike front-facing setups where angular resolution
degrades towards the vanishing point, the side-facing orien-
tation allows the system to scan the environmental proﬁle
orthogonal to the vehicle’s motion vector, capturing a con-
tinuous and high-resolution layout of parallel static structures.
Consequently, the measurement focuses primarily on the
outer perimeter of the sensing loop, capturing a variety of
typical urban road scenarios, as illustrated in Fig. 2. These
scenarios consider various spatial conﬁgurations of buildings
and trees (e.g., buildings only, trees only, and coexistence
of buildings and trees), simulating the sensing of roadside
environments as a vehicle travels through the scene. Specif-
ically, Route 2 features a scene with only roadside trees,
characterized by irregular distribution and non-deterministic
channel reﬂections. Route 3 includes a scene bordered only by
buildings, where the channel exhibited strong, continuous, and
structured reﬂections. In addition, all routes contain composite
scenes with both trees and buildings. Compared to buildings,
trees were generally positioned closer to the vehicle, resulting
in more diverse sensing paths and complex structural channel
characteristics. This combination of heterogeneous environ-
ments effectively simulates common perception tasks in V2X
and autonomous driving systems, providing a solid foundation
for evaluating the model’s generalization capability across
different environmental conditions.
IV. D ATA PRE-PROCESSING
In this section, we detail the comprehensive data pre-
processing pipeline designed to transform the raw multi-modal
measurements into a high-quality, uniﬁed dataset suitable
for deep learning training. As the raw signals captured by
different sensors vary signiﬁcantly in format, sampling rate,
and coordinate systems, a systematic processing workﬂow
is essential. We ﬁrst elaborate on the extraction of intrinsic
channel parameters using the SAGE algorithm, followed by
the rigorous spatiotemporal alignment and cropping of LiDAR
point clouds. Finally, we describe the semantic labeling strat-
egy and the partitioning of the dataset, which ensures the
reliability and generalization capability of the subsequent
environment reconstruction model.
A. Multi-Path Estimation
The Channel parameters are extracted from the measured
raw data by ﬁrst processing the IQ signals to obtain the
CIR. Subsequently, the SAGE algorithm, conﬁgured with
Serial Interference Cancellation (SIC) and a model order of
L = 50, is employed to jointly estimate the MPCs (delay,
AoA, and EoA) on a single-snapshot basis to preserve dynamic
Fig. 3. Channel parameters extracted by SAGE. (a) Delay. (b) AOA and EOA.
environmental features. The estimation utilizes a rectangular
window and terminates after 5 iterations or upon convergence,
after which the top-40 MPCs ranked by power magnitude are
selected as the ﬁnal input features. To enhance data integrity
and improve the reliability of environment reconstruction,
outliers are identiﬁed and removed. Fig. 3 illustrates the
distribution of pre-processed multi-path channel parameters
across different dimensions. Speciﬁcally, Fig. 3(a) shows the
distribution of path delays across multiple snapshots, while
Fig. 3(b) presents the angular distribution of path directions
of arrival (DoA) for a single snapshot. Each scatter point in
the ﬁgures represents a valid multi-path component estimated
at the corresponding snapshot, with the color indicating the
power attenuation experienced by the signal during propaga-
tion through the channel.
B. LiDAR Data Pre-Processing
LiDAR point cloud data are subjected to three main steps:
synchronization, alignment, and cropping. First, temporal
synchronization is achieved by uniformly downsampling the
10 Hz LiDAR stream to match the 2 Hz channel acquisition
rate. Subsequently, PCA is employed to align the coordinate
system—orienting the y-axis to the vehicle’s heading and the
x-axis to the sensing direction—followed by manual ﬁne-
tuning to correct residual rotational offsets. Finally, to ensure
Field-of-View (FOV) consistency with the ISAC system,
the point cloud is spatially cropped to match the Tx horn
antenna’s beamwidth, speciﬁcally limiting the valid volume to
within±10◦ in both azimuth and elevation. Finally, the exact
1000-point sampling procedure involves uniformly downsam-
pling the variable-length cropped point cloud for each snapshot
to a ﬁxed size of 1000 points to facilitate batch training.
As shown in Fig. 4(b), the point cloud represents the sur-
rounding environment of the vehicular transceiver. Due to
the non-omnidirectional sensing range of the ISAC channel,
environmental elements outside the valid sensing area, such
as ground points and point clouds from the non-sensing direc-
tion, are considered unnecessary. In addition, as illustrated in
Fig. 4(a), the axis offset caused by the vehicle’s heading devi-
ation must be corrected via PCA to ensure spatial alignment.
The processed point cloud data after these steps is shown in
Fig. 4(f).
C. Dataset Labeling
After pre-processing, channel data and LiDAR point clouds
are aligned frame by frame and labeled according to the types
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

SONG et al.: DEEP LEARNING-BASED DYNAMIC ENVIRONMENT RECONSTRUCTION 14203
Fig. 4. LiDAR point cloud pre-processing. (a) The xy-plane of the point
cloud of a frame. (b) One frame of point cloud. (c) The xy-plane of the point
cloud of a frame after PCA. (d) One frame of point cloud after PCA. (e) The
xy-plane of the point cloud of a frame after cropping. (f) One frame of point
cloud after cropping.
of scatterers present in the environment, which is essential
for the staged training of the proposed model in Section V.
The manual annotation was performed by two independent
personnel using MATLAB as the labeling tool. Speciﬁcally,
the labeling rule is based on observing the presence of trees
and buildings in the pre-processed LiDAR data, classifying
the scene of each sample into two categories: (1) scenes con-
taining buildings or trees only, and (2) scenes containing both
buildings and trees. Because the pre-processed LiDAR data
provides sufﬁcient resolution for the surveyed urban scenarios,
there is practically no ambiguity in distinguishing between
buildings and trees, making the labeling process largely unaf-
fected by subjective human bias. For the consistency check
method, since the LiDAR and channel data are strictly aligned
frame-by-frame, the process primarily involved verifying the
categorical accuracy of the labels assigned by the annotators.
The scene categories for each sample are also cross-referenced
using RGB video data acquired from a panoramic camera.
Fig. 5 illustrates the real-world scenes corresponding to two
Fig. 5. RGB and LiDAR data of different scene categories. (a) Scene con-
taining trees only. (b) Scene containing both buildings and trees. (c) LiDAR
point cloud corresponding to Fig. 5(a). (d) LiDAR point cloud corresponding
to Fig. 5(b).
representative samples. Speciﬁcally, Fig. 5(a) shows a sample
categorized as a scene containing trees only, while Fig. 5(b)
depicts a scene containing both buildings and trees. Based on
this classiﬁcation, we further deﬁne a “semantic object” as a
single building facade or a group of trees. In vehicular dynamic
scenarios, trees are typically located in front of buildings. It
is important to note that the building facades almost always
face the direction of channel sensing; thus, the term “building”
in this paper speciﬁcally refers to the facade of a building.
These labels effectively capture the structural diversity and
complexity of the environment, providing the model with more
discriminative training samples.
D. Dataset Partitioning
Each pre-processed channel data sample has a size of 3×40,
representing 40 multi-path components characterized by their
delay, AoA, and EoA. The corresponding point cloud data
have a size of 1000× 3, representing 1000 3D coordinates
within the environment. To ensure generalization across dif-
ferent environmental settings, the dataset maintains a roughly
balanced number of samples across the two deﬁned scene
categories. A total of 4000 sample pairs are collected. Among
them, data from Routes 1 through 3 are used to construct the
training and validation sets. Speciﬁcally, 90% of the samples
from these routes are used for training, while the remaining
10% are randomly selected as the validation set for model
selection. Route 4, which represents a distinct path not seen
during the training phase, is reserved as the test set to evaluate
the ﬁnal generalization performance.
V. M ODEL DESIGN
Due to the differences in scattering characteristics
between ISAC mmWave signals and LiDAR signals, their
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

14204 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 6. The proposed MSCR-Net.
environmental sensing capabilities vary signiﬁcantly. As a
result, directly constructing an end-to-end network that maps
ISAC channels to point clouds proves to be highly challeng-
ing in practice. However, by leveraging the inherent spatial
consistency between channel parameters and surrounding envi-
ronments, it becomes feasible to progressively decouple the
spatial structure of the environment from the sparse channel
characteristics. This process is analogous to the gradual per-
ception of a scene by a human visual system: ﬁrst identifying
the number of objects, then locating their centers, and ﬁnally
reﬁning their shapes.
Motivated by this observation, a multi-stage training and
reconstruction model based on MSCR-Net is proposed. The
model consists of three structurally identical but indepen-
dently parameterized feature encoders and a three-stage serial
decoder. Together, they form three consecutive training phases,
responsible for inferring scene category, semantic center
position, and point cloud details, respectively. The general
architecture of the model is illustrated in Fig. 6. In the
following sections, we elaborate on model design, workﬂow,
loss function formulation, and training strategy.
A. Model Structure
The feature encoder comprises three components: a distance
feature encoder, an angle feature encoder, and a hybrid feature
encoder. The distance and angle encoders are each imple-
mented as two independent multi-layer perceptrons (MLPs),
responsible for processing delay and angular characteristics,
respectively. The hybrid feature encoder consists of an input
feature fusion module, a four-layer Transformer architec-
ture, a global pooling layer, and a linear projection layer.
Each Transformer layer includes a multi-head self-attention
mechanism with four attention heads, a feedforward neural
network, residual connections, and layer normalization. This
structure facilitates the deep integration and encoding of
delay and angular characteristics, ultimately generating a high-
dimensional fused channel representation.
The feature decoder consists of three modules: a scene
decoder, a semantic center decoder, and a point cloud decoder.
1) Scene Decoder: The scene decoder adopts a multi-
layer fully connected neural network structure, including an
input normalization layer followed by two fully connected
layers. It predicts the scene category from the fused channel
characteristics. The predicted category is represented in binary
form (1 or 2), where 1 indicates scenes containing either
buildings or trees, and 2 indicates scenes containing both
buildings and trees.
2) Semantic Center Decoder: The semantic center decoder
is a fully connected network that selects appropriate linear
layers based on the output of the scene decoder, and predicts
the 3D coordinates of semantic object centers within the
environment.
3) Point Cloud Decoder: The point cloud decoder uses
the semantic center predictions to generate point cloud dis-
tributions, outputting a total of 1000 3D points to represent
the reconstructed environment. Given that mixed scenes con-
taining both buildings and trees pose greater challenges for
point cloud generation, we speciﬁcally design a dedicated
sub-network composed of three MLP layers to improve recon-
struction performance in such cases.
B. Workﬂow
The input of three feature encoders consists of multi-
dimensional channel parameters, where each sample contains
MPCs characterized by delay, AOA, and EOA. The fused
channel characteristics generated by the encoders are fed
into the decoders of the three prediction stages. The design
objective is to freeze the gradient updates of the encoder
corresponding to each current stage, ensuring that the training
of subsequent stages remains unaffected.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

SONG et al.: DEEP LEARNING-BASED DYNAMIC ENVIRONMENT RECONSTRUCTION 14205
In addition, the decoders in the semantic center prediction
stage and point cloud prediction stage require auxiliary input
from the output of the preceding stages. Speciﬁcally, the output
of the scene decoder guides the semantic center decoder in
generating an appropriate number of semantic object centers.
The output of the semantic center decoder provides the spatial
coordinates of semantic object centers, which are then used
by the point cloud decoder to generate localized point cloud
distributions.
It is worth noting that when information is passed from
the ﬁrst stage to the second, the output format must be
transformed. Since binary outputs hinder effective gradient
propagation, we adopt a probabilistic output form for scene
category classiﬁcation. The ﬁnal binary label (1 or 2) is
determined only after completing the inference in the ﬁrst
stage and is then passed to the semantic center decoder for
further processing.
C. Loss Functions and Training Strategies
In the multi-stage serial prediction architecture, the output
of each preceding stage plays a critical role in training the
subsequent stage. Accurate intermediate predictions serve as
informative inputs, enabling the next-stage network to more
effectively identify gradient descent directions and accelerate
convergence. To support this process, we design dedicated
loss functions and training strategies for each of the three
prediction stages.
1) Training Stage I: Scene Category: We adopt a cross-
entropy loss to supervise the prediction of scene categories,
as deﬁned by the following equation:
Lscene =− 1B
B∑
i=1
1∑
c=0
yi,c log (pi,c) (4)
where yi,c denotes the one-hot encoded ground truth label
of the scene category derived from the radar point cloud,
pi,c is the predicted probability for the scene category, and
B represents the batch size. To determine when to terminate
training, we use a Mean Squared Error (MSE)-based evalua-
tion criterion deﬁned as follows:
LMSE = 1B
B∑
i=1
(ˆni−ni)2 (5)
where ˆni, ni∈{ 1, 2} represent the ground truth and predicted
scene categories, respectively. A value of 1 indicates a scene
containing only buildings or trees, while a value of 2 indicates
a scene with both buildings and trees. The ground truth label
ˆni is obtained directly from the label, whereas the predicted
label ni is inferred from the class probabilities pi,c. Training
is terminated if both of the following conditions are satisﬁed:
1) At least 90% of the validation samples achieve a local
MSE (LMSE) below 0.1.
2) The validation loss ﬂuctuates by less than 5% over ﬁve
consecutive epochs.
In the ﬁrst stage, we train the network using pi,c to ensure
proper gradient updates, while using ni for termination crite-
ria. This design guaranties that the training process remains
stable while maintaining the accuracy of the outputs fed into
subsequent prediction stages.
2) Training Stage II: Semantic Center Position: We use
MSE to measure the discrepancy between the predicted and
ground-truth semantic object centers. The corresponding loss
function is deﬁned as follows:
Lcenter = 1B
B∑
i=1
1
K
K∑
k=1
‖‖‖ ˆCi,σ(k)−Ci,σ(k)‖‖‖22 (6)
where ˆCi ∈ RK×3 denotes the predicted coordinates of
the semantic object centers, and Ci represent the ground-
truth centers, derived by calculating the geometric centroid
of all LiDAR points belonging to a speciﬁc semantic cate-
gory (manually annotated as Tree or Building). We set the
maximum number of semantic categories to K = 2, covering
the dominant scatterer types in the dataset. The function σ(·)
sorts the centers based on ascending x-coordinate values. This
sorting strategy is physically motivated by the typical urban
street layout, where roadside trees are positioned closer to the
sensing vehicle (smaller x-value) than the building facades
behind them. This ensures a consistent one-to-one correspon-
dence between the predicted and ground-truth centers during
the loss calculation for mixed scenes. This stage of training is
terminated when the averageLcenter in the validation set falls
below 2.0.
3) Training Stage III: Point Cloud Details: In the point
cloud generation stage, we adopt an adaptively weighted multi-
objective loss function:
Lpointcloud =
2∑
i=1
(exp (−λi)Li +λi) +LV AT (7)
where λi is a trainable log-variance parameter. Lpointcloud
consists of two main components:
1) ChamferDistance (CD) [49], which restricts the
global geometric structure.
L1 = 1BN
B∑
i=1
(
1
|Pi|
∑
p∈Pi
min
q∈Qi
‖p−q‖2
+ 1|Qi| ∑q∈Qi minp∈Pi‖q−p‖2
)
(8)
Speciﬁcally, let Pi and Qi denote the predicted and
ground truth point clouds, respectively, with N = 1000
points.
2) LocalFeatureLoss [50], which captures ﬁne-grained
details of the predicted point cloud.
L2 = 1B
B∑
i=1
1
k
k∑
j=1
‖‖‖µ(NPj )−µ(NQj )‖‖‖2 (9)
whereNj denotes the set of 50 nearest neighbors of
point j, and µ(·) computes the centroid of the local
neighborhood.
Regarding the optimization details, we employ the Adam
optimizer with a learning rate of 1× 10−4 across all three
stages. Crucially, the optimizer is re-initialized at the begin-
ning of each stage: Stage I optimizes the scene predictor and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

14206 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
encoders; Stage II optimizes the semantic center decoder while
freezing the encoders; and Stage III optimizes the point cloud
decoder while freezing all preceding modules. The batch size
is set to 10, for which the variable-length cropped point clouds
are uniformly downsampled to a ﬁxed size of N = 1000 to
facilitate batch processing. In addition, we incorporate Virtual
Adversarial Training (V AT) [51] to enhance the robustness
of the model. The V AT is conﬁgured with a loss weight
α = 1.0, a perturbation magnitude ϵ = 10−3, an initial
variance ξ = 10−5, and employs an L2-norm constraint with
a single power iteration step.
VI. E XPERIMENTS AND ANALYSIS
In this section, we ﬁrst introduce the evaluation metrics
used to assess the performance of the proposed MSCR-
Net. Subsequently, we present the experiments conducted
on the dataset described in Section IV. To comprehensively
evaluate the effectiveness of MSCR-Net, we designed a
series of experiments comprising both comparative evaluations
against state-of-the-art models and ablation studies. Speciﬁ-
cally, comparative experiments benchmark our method against
traditional algorithms and advanced deep learning baselines
to demonstrate its performance superiority. Ablation studies
focus on analyzing the contribution of speciﬁc modules to
the local features in sample-level reconstruction, while the
spatial consistency experiment evaluates the dynamic global
characteristics of the reconstructed environment.
A. Evaluation Metrics
Let Pout denote the point cloud reconstruction, and let
PGT represent the set of LiDAR point clouds. The evaluation
employs two metrics:
1) ChamferDistance (CD) measures the closeness
between two sets of points based on nearest neighbor
distances. In the computation, it only needs to replace
Pi in (8) withPout , Qi withPGT , and set B = 1.
2) F−score@0.5m [52] assesses the quality of recon-
struction through precision and recall with a distance
thresholdtr = 0.5m. This threshold is chosen to enforce
strict geometric accuracy relative to the large spatial
scale of dynamic vehicular environments (spanning tens
of meters):
F -score (Pout,PGT ) = 2×Ptr×RtrPtr +Rtr (10)
wherePtr and Rtr denote precision and recall, respec-
tively:
Ptr = 1|Pout| ∑x∈Pout [miny∈PGT‖x−y‖2 <tr ]
Rtr = 1|PGT| ∑x∈PGT [miny∈Pout‖x−y‖2 <tr ] (11)
It is apparent that smaller values of CD correspond to
higher accuracy in reconstruction, while larger values of F-
score@0.5m indicate a wider coverage range in reconstruction.
B. Performance Comparison and Ablation Studies
We benchmarked MSCR-Net against two distinct baseline
strategies: 1) ResNet [53], a standard deep network that treats
channel parameters as three-channel images, ignoring the
speciﬁc physical properties of ISAC signals; and 2) AGGRNN
[27], a two-step reconstruction framework that ﬁrst maps
channel parameters to sparse point clouds in 3D space and
subsequently utilizes a densiﬁcation network to generate the
ﬁnal environment. As visually demonstrated in Fig. 7, the
ResNet baseline exhibits signiﬁcant inaccuracies. While it
can approximately locate structures in single-object scenes,
it fails to identify scenes with multiple types of scatterers
and cannot distinguish between buildings and trees, resulting
in blurred and fused outlines. AGGRNN shows improved
performance over ResNet by explicitly utilizing spatial point
representations. However, its reconstruction quality is limited
by the sparsity of the intermediate representation, leading to
loss of ﬁne structural details and geometric distortions in com-
plex mixed scenes. In contrast, MSCR-Net achieves the most
complete scene reconstructions. By using the speciﬁc physics
of the channel data, it generates sharper outlines and accurately
distinguishes between buildings and trees as distinct scatter-
ers, resulting in high consistency with the LiDAR ground
truth.
To investigate the necessity of the proposed multi-
stage architecture, we evaluated two ablation variants:
1) E2E-Transformer, a single-stage baseline that employs
a Transformer-based architecture to directly map chan-
nel parameters to point clouds in an end-to-end manner;
and 2) CR-Net (Channel-to-Reconstruction Network), which
retains the encoder and point cloud decoder of MSCR-Net
but removes the progressive multi-stage training structure,
effectively stacking the decoders and supervising them solely
by the ﬁnal reconstruction loss. The results reveal that the
E2E-Transformer, despite its powerful attention mechanism,
struggles to converge to a precise geometric structure due
to the huge modality gap between abstract channel features
and dense point clouds. The CR-Net shows better spatial
localization than the single-stage Transformer but remains
indistinct in boundary deﬁnition. As seen in mixed scenes
(Fig. 7), CR-Net tends to merge proximal trees and buildings
into a single object. This conﬁrms that without the progressive
guidance of scene classiﬁcation (Stage I) and semantic center
Positioning (Stage II), the network struggles to decouple the
complex spatial relationships.
Figs. 8 and 9 present the quantitative performance of all
ﬁve networks on the test set. MSCR-Net outperforms both
the comparative baselines (ResNet, AGGRNN) and the abla-
tion variants (E2E-Transformer, CR-Net) across all evaluation
metrics. It demonstrates a superior capability in reconstructing
point clouds with richer local and global structural features.
Furthermore, MSCR-Net exhibits the smallest dispersion in
both CD and F-score@0.5m, whereas the baselines show
signiﬁcantly higher variance. This highlights that MSCR-Net
possesses strong generalization ability and robustly handles
the non-linear mapping from ISAC channels to environmental
structures.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

SONG et al.: DEEP LEARNING-BASED DYNAMIC ENVIRONMENT RECONSTRUCTION 14207
Fig. 7. Comparison against different methods.
Fig. 8. Chamfer Distance comparison against different methods.
TABLE II
QUANTITATIVE COMPARISON OF MSCR-N ET PERFORMANCE WITH DIF-
FERENT NUMBERS OF INPUT MPC S
Finally, regarding the robustness to the number of MPCs,
we conducted additional ablation studies with MPC counts
of 20 and 60, comparing them to our default setting of 40.
As summarized in Table II, the 40-MPC setting achieves the
optimal geometric accuracy with the lowest Average CD. In
Fig. 9. F-score@0.5m comparison against different methods.
comparison, the 20-MPC conﬁguration yields a slightly higher
geometric error, indicating potential information loss from
insufﬁcient paths. In contrast, increasing to 60 MPCs leads
to performance degradation, likely due to the introduction of
noise from weaker signal components. Despite these minor
ﬂuctuations, the overall performance variance is minimal,
demonstrating that MSCR-Net is robust to variations in input
sparsity.
C. Spatial Consistency
In dynamic trafﬁc environments, although the acquisition
rate of ISAC channel data is higher than the rate of scene
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

14208 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 10. Comparison of proposed method with LiDAR. (a) Comparison of
reconstructed scene and LiDAR ground truth in a uniﬁed coordinate system.
(b) Comparison of proposed method with LiDAR.
Fig. 11. Comparison of proposed method with traditional method. (a) Recon-
structing scenarios with traditional methods. (b) Reconstructing scenarios with
proposed method. (c) LiDAR point cloud.
variation, the continuous motion of the vehicle leads to
changes in both the observation angle and spatial position
associated with each channel snapshot. Consequently, even
when multi-ple samples perceive the same scene, the extracted
channel features exhibit differences. These differences not only
reﬂect variations in viewing angles across samples, but also
capture the dynamic nature of channel perception with respect
to spatial structures. The model’s ability to effectively capture
and leverage these variations is critical for achieving spatially
consistent reconstruction. It directly inﬂuences the complete-
ness and stability of dynamic 3D scene reconstruction, helping
to prevent perception misalignment and the emergence of
ghost targets [54].
We performed temporal reconstruction on the test set sam-
ples by cumulatively mapping the reconstructed point clouds
along the y-axis according to the vehicle’s measured speed
TABLE III
PERFORMANCE AND COMPLEXITY COMPARISON
and the channel sampling rate. To provide a performance
benchmark, we evaluated a traditional geometry-based chan-
nel inversion method [55]. This baseline combines Digital
Beamforming (DBF) to scan for angular directions using
2D steering vectors and Matched Filtering (MF) to estimate
target distances based on the peak offsets of the received
echo correlation. Fig. 11(a) illustrates the global reconstruction
results of this traditional approach. It can be observed that the
reconstruction quality is suboptimal: many building structures
are incomplete, trees are poorly resolved, and signiﬁcant ghost
targets are present due to multipath interference.
In contrast, Fig. 10 and Fig. 11(b) present the global
reconstruction using the proposed MSCR-Net. The recon-
structed geometry changes smoothly over time, maintaining
high continuity with the true environment, and crucially, no
ghost targets are observed around trees or other scatterers.
It is important to note that in the test scenarios, there are
almost no effective scatterers between adjacent buildings that
can be captured by the sensing system. As a result, such
samples were excluded during dataset construction. Therefore,
the reconstructed environments shown in Fig. 10 and Fig. 11
are not continuous. TABLE III compares the performance
of the proposed MSCR-Net with that of traditional meth-
ods. It is important to note that unlike the single-snapshot
evaluation in Figs. 8 and 9, the metrics in TABLE III are
calculated based on the complete, globally reconstructed envi-
ronment (Fig. 11(b)). The lower CD (0.29) achieved here
compared to the single-snapshot result (0.5846) is due to the
accumulation of overlapping snapshots, which densiﬁes the
point cloud and improves structural completeness. MSCR-
Net outperforms traditional approaches across all evaluation
metrics, demonstrating superior reconstruction accuracy. The
column ‘Elevation (dB)’ indicates the relative improvement
in reconstruction quality compared to the traditional baseline.
This demonstrates that the model tracks the evolution of the
environment in time well and is more suitable for dynamic
environment reconstruction. Note that since LiDAR’s method
is treated as the true value of the benchmark in this work, the
metrics here are of no practical signiﬁcance and are listed here
to analyze their complexity below.
D. Complexity Analysis
To evaluate the feasibility of the proposed method for
real-world deployment, we analyzed the model’s parameter
count, computational complexity, and inference speed. The
overall parameter size of MSCR-Net is 15.53M, with a
computational complexity of approximately 0.53 GFLOPs,
demonstrating high inference efﬁciency while maintaining
strong reconstruction performance. On an NVIDIA RTX 5080
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

SONG et al.: DEEP LEARNING-BASED DYNAMIC ENVIRONMENT RECONSTRUCTION 14209
GPU, the proposed method achieves an average inference
time of approximately 0.9 ms per sample, signiﬁcantly out-
performing traditional reconstruction algorithms (15 ms) and
LiDAR-based methods (100 ms). Even on a general-purpose
computing platform without GPU acceleration (using an Intel
Core Ultra 9 275HX CPU with 24 cores and a base speed of
2.70 GHz), MSCR-Net achieves an inference time of only
3 ms per sample, further highlighting its strong hardware
adaptability and potential for edge deployment.
Finally, we address the generalization capability regarding
hardware changes and new scenes. While real-world data
collection is labor-intensive, the proposed architecture captures
fundamental physical mappings between channel parameters
and spatial structures, which are independent of speciﬁc hard-
ware. Therefore, when hardware conﬁgurations (e.g., antenna
placement or frequency) change, transfer learning can be
effectively employed to ﬁne-tune the pre-trained backbone
with minimal new data, signiﬁcantly reducing recollection
overhead [56], [57]. Furthermore, since the model learns
the consistent electromagnetic scattering properties of typical
urban elements (buildings and trees), it has strong potential
to generalize across other urban vehicular environments with
similar structural compositions.
VII. C ONCLUSION
This paper presents an ISAC-driven reconstruction frame-
work tailored for dynamic vehicular environment, which
jointly leverages mmWave ISAC channel parameters and
LiDAR-derived point cloud data to achieve efﬁcient envi-
ronment reconstruction. Experimental results demonstrate
that in complex dynamic scenes composed of diverse scat-
terers, the proposed model signiﬁcantly outperforms the
traditional beamforming-based methods and deep learning
baselines, achieving a Chamfer Distance (CD) of 0.29 and an
F-score@0.5m of 0.87. This study further veriﬁes that, when
properly extracted and modeled, channel characteristics can
serve as a powerful alternative to radar sensing, offering a
low-cost, highly integrated solution for 6G V2X applications.
Future work will focus on extending the proposed framework
to multi-vehicle cooperative sensing tasks and exploring its
real-time deployment potential on edge computing platforms.
REFERENCES
[1] D. Wen, Y . Zhou, X. Li, Y . Shi, K. Huang, and K. B. Letaief, “A
survey on integrated sensing, communication, and computation,” IEEE
Commun. Surveys Tuts., vol. 27, no. 5, pp. 3058–3098, Oct. 2025.
[2] R. He and B. Ai, Wireless Channel Measurement and Modeling in
Mobile Communication Scenario: Theory and Application. Boca Raton,
FL, USA: CRC Press, 2024.
[3] J. Tian, Y . Han, S. Jin, J. Zhang, and J. Wang, “Analytical channel
modeling: From MIMO to extra large-scale MIMO,” Chin. J. Electron.,
vol. 34, no. 1, pp. 1–15, Jan. 2025.
[4] Z. Lyu et al., “Multi-channel photonic THz-ISAC system based on
integrated LFM-QAM waveform,” J. Lightw. Technol., vol. 42, no. 11,
pp. 3981–3988, Jun. 1, 2024.
[5] Z. Zhang et al., “A cluster-based statistical channel model for integrated
sensing and communication channels,” IEEE Trans. Wireless Commun.,
vol. 23, no. 9, pp. 11597–11611, Sep. 2024.
[6] R. He et al., “Propagation channels of 5G millimeter-wave vehicle-to-
vehicle communications: Recent advances and future challenges,” IEEE
Veh. Technol. Mag., vol. 15, no. 1, pp. 16–26, Mar. 2020.
[7] R. He, B. Ai, G. L. Stuber, G. Wang, and Z. Zhong, “Geometrical-based
modeling for millimeter-wave MIMO mobile-to-mobile channels,” IEEE
Trans. Veh. Technol., vol. 67, no. 4, pp. 2848–2863, Apr. 2018.
[8] Z. Wei et al., “Integrated sensing and communication signals toward
5G-A and 6G: A survey,” IEEE Internet Things J., vol. 10, no. 13,
pp. 11068–11092, Jul. 2023.
[9] Z. Zhang et al., “Channel measurements and modeling for dynamic
vehicular ISAC scenarios at 28 GHz,” IEEE Trans. Commun., vol. 73,
no. 8, pp. 6884–6897, Aug. 2025.
[10] Z. Zhang et al., “A general channel model for integrated sensing
and communication scenarios,” IEEE Commun. Mag., vol. 61, no. 5,
pp. 68–74, May 2023.
[11] S. Sun, A. P. Petropulu, and H. V . Poor, “MIMO radar for advanced
driver-assistance systems and autonomous driving: Advantages and
challenges,” IEEE Signal Process. Mag., vol. 37, no. 4, pp. 98–117,
Jul. 2020.
[12] Z. Qiu et al., “A multi-feature fusion approach for road surface
recognition leveraging millimeter-wave radar,” Sensors, vol. 25, no. 12,
p. 3802, Jun. 2025.
[13] H. Zifeng, W. Hongyan, and M. Jiakang, “4D millimeter-wave radar
target detection method based on graph neural network,” J. Comput.
Eng. Appl., vol. 61, no. 10, p. 145, 2025.
[14] Z. Luo, Y . Wang, Y . He, and W. Wang, “Improving multi-vehicle
perception fusion with millimeter-wave radar assistance,” 2025,
arXiv:2506.00837.
[15] L. Li, C. Liu, W. Yu, and T. J. Cui, “Diff-HPE: Multihypothesis human
pose estimation based on mmWave radar and diffusion framework,”
IEEE Sensors J., vol. 25, no. 13, pp. 25185–25197, Jul. 2025.
[16] Y . Wang, M. Xu, Z. Wang, Y . Wang, and J. A. Zhang, “User reidentiﬁca-
tion through mmWave radio imaging,” IEEE Internet Things J., vol. 12,
no. 16, pp. 33293–33310, Aug. 2025.
[17] Y . Chang et al., “MmYodar+: Robust human detection using mmWave
signals,” IEEE Internet Things J., vol. 12, no. 16, pp. 33702–33713,
Aug. 2025.
[18] L. Zhao, R. Lyu, A. Zhou, Q. Guo, and H. Ma, “MmCG: Noncontact
millimeter-wave cardiography for heart rate variability monitoring,”
IEEE Internet Things J., vol. 12, no. 15, pp. 30955–30969, Aug. 2025.
[19] H. Chen et al., “RaGeoSense for smart home gesture recognition using
sparse millimeter wave radar point clouds,” Sci. Rep., vol. 15, no. 1,
p. 15267, May 2025.
[20] L. Chen, K. Liu, Q. Gao, X. Wang, and Z. Zhang, “Enhancing
integrated sensing and communication (ISAC) performance for
a searching–deciding alternation radar-comm system with multi-
dimension point cloud data,” Remote Sens., vol. 16, no. 17, p. 3242,
Sep. 2024.
[21] X. Cheng et al., “M3SC: A generic dataset for mixed multi-modal
(MMM) sensing and communication integration,” China Commun.,
vol. 20, no. 11, pp. 13–29, Nov. 2023.
[22] Y . Niu, Z. Wei, L. Wang, H. Wu, and Z. Feng, “Interference management
for integrated sensing and communication systems: A survey,” IEEE
Internet Things J., vol. 12, no. 7, pp. 8110–8134, Apr. 2025.
[23] C. Meng, Z. Wei, and Z. Feng, “Adaptive waveform optimization for
MIMO integrated sensing and communication systems based on mutual
information,” in Proc. 14th Int. Conf. Wireless Commun. Signal Process.
(WCSP), 2022, pp. 472–477.
[24] S. Lu et al., “Integrated sensing and communications: Recent advances
and ten open challenges,” IEEE Internet Things J., vol. 11, no. 11,
pp. 19094–19120, Jun. 2024.
[25] J. Zhang et al., “Integrated sensing and communication channel:
Measurements, characteristics, and modeling,” IEEE Commun. Mag.,
vol. 62, no. 6, pp. 98–104, Jun. 2024.
[26] Z. Chang, P. Tang, J. Zhang, H. Jiang, and G. Liu, “Environment recon-
struction with multi-targets reﬂectors-merged sensing method based on
THz single-sided channel characteristics,” 2024, arXiv:2412.03960.
[27] B. Lu et al., “Deep-learning-based multinode ISAC 4D environmental
reconstruction with uplink–downlink cooperation,” IEEE Internet Things
J., vol. 11, no. 24, pp. 39512–39526, Dec. 2024.
[28] S. Blandino et al., “Detecting airborne objects with 5G NR radars,”
2025, arXiv:2505.24763.
[29] L. Yin and Y . Wang, “Tomographic bistatic 3-D imaging and coordinate
reconstruction method based on uplink communication process,” IEEE
Trans. Geosci. Remote Sens., vol. 63, 2025, Art. no. 5208316.
[30] N. Avazov, R. Hicheri, M. Muaaz, F. Sanﬁlippo, and M. P ¨atzold,
“A trajectory-driven 3D non-stationary mm-wave MIMO channel
model for a single moving point scatterer,” IEEE Access, vol. 9,
pp. 115990–116001, 2021.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

14210 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[31] Z. Du et al., “Integrated sensing and communications for V2I
networks: Dynamic predictive beamforming for extended vehicle
targets,” IEEE Trans. Wireless Commun., vol. 22, no. 6, pp. 3612–3627,
Jun. 2023.
[32] B. He, F. Wang, and T. Q. S. Quek, “Secure semantic communication
via paired adversarial residual networks,” IEEE Wireless Commun. Lett.,
vol. 13, no. 10, pp. 2832–2836, Oct. 2024.
[33] R. He, N. D. Cicco, B. Ai, M. Yang, Y . Miao, and M. Boban, “COST
CA20120 INTERACT framework of artiﬁcial intelligence-based chan-
nel modeling,” IEEE Wireless Commun., vol. 32, no. 4, pp. 200–207,
Aug. 2025.
[34] C. Huang et al., “Artiﬁcial intelligence enabled radio propaga-
tion for communications—Part II: Scenario identiﬁcation and chan-
nel modeling,” IEEE Trans. Antennas Propag., vol. 70, no. 6,
pp. 3955–3969, Jun. 2022.
[35] S. Katoh, H. Nagao, and Y . Iio, “MultiDLFormer: A vision transformer-
based deep learning model for detecting deep low-frequency earthquakes
across multiple stations,” Authorea Preprints, pp. 1–17, Jul. 2025.
[36] S. Yun, J. Pei, and P. Wang, “TOAST: Task-oriented adaptive
semantic transmission over dynamic wireless environments,” 2025,
arXiv:2506.21900.
[37] Y . Fang, S. Xu, P. Fang, J. Zhang, Y . Huang, and L. Yang, “Optimizing
codebook design in mmWave massive MIMO using digital twin-
assisted DRL,” IEEE Trans. Veh. Technol., vol. 74, no. 12, pp. 1–16,
Dec. 2025.
[38] H. Liu et al., “AI-empowered channel generation for IoV semantic
communications in dynamic conditions,” 2025, arXiv:2507.02013.
[39] A. Klautau, A. de Oliveira, I. P. Trindade, and W. Alves, “Generating
MIMO channels for 6G virtual worlds using ray-tracing simulations,”
in Proc. IEEE Stat. Signal Process. Workshop (SSP), Jul. 2021,
pp. 595–599.
[40] J. A. Fessler and A. O. Hero, “Space-alternating generalized expectation-
maximization algorithm,” IEEE Trans. Signal Process., vol. 42, no. 10,
pp. 2664–2677, Oct. 1994.
[41] C. C. Chong, D. I. Laurenson, C. M. Tan, S. McLaughlin, M. A. Beach,
and A. R. Nix, “Joint detection-estimation of directional channel param-
eters using the 2-D frequency domain SAGE algorithm with serial
interference cancellation,” in Proc. IEEE Int. Conf. Commun., vol. 2,
Aug. 2002, pp. 906–910.
[42] M. Matthaiou, D. I. Laurenson, N. Razavi-Ghods, and S. Salous,
“Characterization of an indoor MIMO channel in frequency domain
using the 3D-SAGE algorithm,” in Proc. IEEE Int. Conf. Commun.,
Jun. 2007, pp. 5868–5872.
[43] H. Hotelling, “Analysis of a complex of statistical variables into
principal components,” J. Educ. Psychol., vol. 24, no. 6, pp. 417–441,
Sep. 1933.
[44] J. Shlens, “A tutorial on principal component analysis,” 2014,
arXiv:1404.1100.
[45] C. X. Lu et al., “See through smoke: Robust indoor mapping with
low-cost mmWave radar,” in Proc. 18th Int. Conf. Mobile Syst., Appl.,
Services, Jun. 2020, pp. 14–27.
[46] C. R. Qi, H. Su, K. Mo, and L. J. Guibas, “PointNet: Deep learning on
point sets for 3D classiﬁcation and segmentation,” in Proc. IEEE Conf.
Comput. Vis. Pattern Recognit. (CVPR), Jul. 2017, pp. 652–660.
[47] H. Fan, H. Su, and L. J. Guibas, “A point set generation network for
3D object reconstruction from a single image,” in Proc. IEEE Conf.
Comput. Vis. Pattern Recognit., Jun. 2017, pp. 605–613.
[48] C. R. Qi, L. Yi, H. Su, and L. J. Guibas, “PointNet++: Deep hierarchical
feature learning on point sets in a metric space,” in Proc. Adv. Neural
Inf. Process. Syst., vol. 30, 2017, pp. 1–11.
[49] T. Wu, L. Pan, J. Zhang, T. Wang, Z. Liu, and D. Lin, “Balanced chamfer
distance as a comprehensive metric for point cloud completion,” in Proc.
Adv. Neural Inf. Process. Syst., vol. 34, 2021, pp. 29088–29100.
[50] Y . Feng, Y . Zhang, Z. Zhao, R. Ji, and Y . Gao, “Point2Sequence:
Learning the shape representation of 3D point clouds with an attention-
based sequence to sequence network,” in Proc. AAAI Conf. Artif. Intell.,
vol. 33, 2019, pp. 8439–8446.
[51] T. Miyato, S.-I. Maeda, M. Koyama, and S. Ishii, “Virtual adversarial
training: A regularization method for supervised and semi-supervised
learning,” IEEE Trans. Pattern Anal. Mach. Intell., vol. 41, no. 8,
pp. 1979–1993, Aug. 2019.
[52] M. Tatarchenko, S. R. Richter, R. Ranftl, Z. Li, V . Koltun, and T. Brox,
“What do single-view 3D reconstruction networks learn?,” in Proc.
IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2019,
pp. 3400–3409.
[53] C. Xu, W. Wang, Y . Zhang, J. Qin, S. Yu, and Y . Zhang, “An
indoor localization system using residual learning with channel state
information,” Entropy, vol. 23, no. 5, p. 574, May 2021.
[54] L. Zheng, J. Long, M. Lops, F. Liu, X. Hu, and C. Zhao, “Detection of
ghost targets for automotive radar in the presence of multipath,” IEEE
Trans. Signal Process., vol. 72, pp. 2204–2220, 2024.
[55] J. Song et al., “3D environment reconstruction based on ISAC
channels,” in Proc. Int. Conf. Ubiquitous Commun. (Ucom), Jul. 2024,
pp. 487–491.
[56] G. Omondi and T. O. Olwal, “Advancing MIMO adaptation with transfer
learning: Pioneering approaches and emerging perspectives,” Cogent
Eng., vol. 13, no. 1, Dec. 2026, Art. no. 2602250.
[57] Z. Hu, Y . Li, and C. Han, “Transfer learning enabled transformer-
based generative adversarial networks for modeling and gener-
ating terahertz channels,” Commun. Eng., vol. 3, no. 1, p. 153,
Nov. 2024.
Junzhe Song received the B.S. degree in com-
munication engineering from Nanjing University of
Posts and Telecommunications, Nanjing, China, in
2023. He is currently pursuing the Ph.D. degree with
the School of Electronic Information Engineering,
Beijing Jiaotong University, Beijing, China.
His research interests include ISAC, wireless
communications, site-speciﬁc wireless channel mod-
eling, and deep learning.
Ruisi He (Senior Member, IEEE) received the B.E.
and Ph.D. degrees from Beijing Jiaotong University
(BJTU), Beijing, China, in 2009 and 2015, respec-
tively.
He has been a Visiting Scholar with Georgia
Institute of Technology, Atlanta, GA, USA; the
University of Southern California, Los Angeles, CA,
USA; and the Universit ´e Catholique de Louvain,
Belgium. He is currently a Professor with the School
of Electronics and Information Engineering, BJTU.
He has authored/co-authored eight books, ﬁve book
chapters, more than 200 journal and conference papers, and several patents.
His research interests include wireless propagation channels and 5G and 6G
communications.
Dr. He served as the Early Career Representative (ECR) of Commission
C, International Union of Radio Science (URSI). He received the URSI
Issac Koga Gold Medal in 2021, the IEEE ComSoc Asia–Paciﬁc Outstanding
Young Researcher Award in 2019, the URSI Young Scientist Award in 2015,
and several Best Paper Awards in IEEE journals and conferences. He has
been an Editor of IEEE T RANSACTIONS ON COMMUNICATIONS , IEEE
TRANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE T RANSACTIONS
ON ANTENNAS AND PROPAGATION , IEEE Antennas and Propagation Mag-
azine, IEEE C OMMUNICATIONS LETTERS , and IEEE O PEN JOURNAL OF
VEHICULAR TECHNOLOGY , and a Lead Guest Editor of IEEE J OURNAL
ON SELECTED AREA IN COMMUNICATIONS and IEEE T RANSACTIONS ON
ANTENNAS AND PROPAGATION .
Mi Yang (Member, IEEE) received the M.S. and
Ph.D. degrees from Beijing Jiaotong University, Bei-
jing, China, in 2017 and 2021, respectively.
He is currently an Associate Professor with the
School of Electronic and Information Engineering,
Beijing Jiaotong University. His research interests
are focused on wireless channel measurement and
modeling, vehicular and railway communications,
and AI-enabled channel research.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

SONG et al.: DEEP LEARNING-BASED DYNAMIC ENVIRONMENT RECONSTRUCTION 14211
Zhengyu Zhang (Student Member, IEEE) received
the B.S. and M.S. degrees in electronic and com-
munication engineering and the Ph.D. degree in
information and communication systems from Bei-
jing Jiaotong University, China, in 2018, 2021, and
2025, respectively.
From 2024 to 2025, he was a Visiting Ph.D.
Student with the University of Bologna, Italy. He
is currently a Lecturer with the School of Elec-
tronic and Information Engineering, Beijing Jiaotong
University. His research interests include integrated
sensing and communications (ISAC), channel semantics, deep learning, 6G
wireless channel measurement, and modeling.
Bingcheng Liu received the B.E. degree from Bei-
jing Jiaotong University, Beijing, China, in 2009,
and the M.S. degree from Beihang University, Bei-
jing, in 2012.
He is currently an Associate Professor with the
Aerospace Information Research Institute, Chinese
Academy of Sciences, Beijing. His work currently
focuses on the processing, analysis, and application
of global navigation satellite system precision local-
ization and navigation.
Jiahui Han received the B.E. and M.S. degrees from
Beijing Jiaotong University, Beijing, China, in 2012
and 2016, respectively.
She is currently the Deputy Director of the
Scientiﬁc Research Management and Business
Development Department, Master Planning Insti-
tute, China Academy of Industrial Internet, Beijing.
Her research focuses on information and com-
munications, digital transformation for small- and
medium-sized enterprises, industrial Internet, and
big data.
Haoxiang Zhang received the B.E. and M.S.
degrees from Beijing Jiaotong University, Beijing,
China, in 2008 and 2012, respectively, and the Ph.D.
degree from Renmin University of China, Beijing, in
2019.
He is currently the Deputy Director (presiding)
of the Master Planning Institute, China Academy
of Industrial Internet, Beijing. His current research
interests include wireless communications, industrial
internet platform construction, regional planning,
industrial applications, and technical management.
He is a member of the Editorial Board of Journal of New Industrialization.
Bo Ai (Fellow, IEEE) received the M.S. and Ph.D.
degrees from Xidian University, Xi’an, China, in
2002 and 2004, respectively.
He was with Tsinghua University, Beijing, China,
where he was an Excellent Post-Doctoral Research
Fellow in 2007. He is currently a Professor and an
Advisor of Ph.D. Candidates with Beijing Jiaotong
University, Beijing, where he is also the Deputy
Director of the State Key Laboratory of Rail Trafﬁc
Control and Safety. He is also with the Engineer-
ing College, Armed Police Force, Xi’an. He has
authored or co-authored six books and 270 scientiﬁc research articles, and
holds 26 invention patents in his research areas. His interests include the
research and applications of orthogonal frequency-division multiplexing tech-
niques, high-power ampliﬁer linearization techniques, radio propagation and
channel modeling, global systems for mobile communications for railway
systems, and long-term evolution for railway systems. He is a fellow of The
Institution of Engineering and Technology. He has received many awards, such
as the Qiushi Outstanding Youth Award by Hong Kong Qiushi Foundation, the
New Century Talents by Chinese Ministry of Education, the Zhan Tianyou
Railway Science and Technology Award by Chinese Ministry of Railways,
and the Science and Technology New Star by Beijing Municipal Science and
Technology Commission. He was the Co-Chair or the Session/Track Chair
for many international conferences, such as the 9th International Heavy Haul
Conference in 2009; the 2011 IEEE International Conference on Intelligent
Rail Transportation; HSRCom2011; the 2012 IEEE International Symposium
on Consumer Electronics; the 2013 International Conference on Wireless,
Mobile and Multimedia; IEEE Green HetNet 2013; and the IEEE 78th
Vehicular Technology Conference in 2014. He is an Associate Editor of IEEE
TRANSACTIONS ON CONSUMER ELECTRONICS and an Editorial Committee
Member of Wireless Personal Communications.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:03 UTC from IEEE Xplore.  Restrictions apply.
