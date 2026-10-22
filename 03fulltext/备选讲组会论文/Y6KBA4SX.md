---
type: literature-fulltext
title: "Passive UAV Detection Based on Channel Estimation and Temporal Variation Network"
zotero_key: "Y6KBA4SX"
pdf_key: "CC82545V"
doi: "10.1109/TWC.2026.3676229"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Passive UAV Detection Based on Channel Estimation and Temporal Variation Network.md"
fulltext_path: "03fulltext/备选讲组会论文/Y6KBA4SX.md"
zotero_item: "zotero://select/library/items/Y6KBA4SX"
zotero_pdf: "zotero://open-pdf/library/items/CC82545V"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Passive UAV Detection Based on Channel Estimation and Temporal Variation Network

> PDF 原文逐页文本抽取；来源文件 SHA-256：`4a8ea86c30be5ce11a2ddaf7e653ece322c66e364ce4159eae588ba70e58d484`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 14351
Passive UA V Detection Based on Channel
Estimation and Temporal Variation Network
Jing Bai
 , Senior Member, IEEE, Zhuo Zhang
 , Zhu Xiao
 , Senior Member, IEEE, Huaji Zhou
 ,
Yongqiang Hei
 , Xiaohui Liu, Tong Li, Member, IEEE, and Licheng Jiao
 , Life Fellow, IEEE
Abstract—The increasing proliferation of unmanned aerial
vehicles (UA Vs) poses signiﬁcant challenges to airspace security,
necessitating the development of effective detection technologies.
Passive detection techniques, such as passive radar, offer key
advantages including spectrum efﬁciency and covert opera-
tion. However, passive radars that rely on coherent integration
are often computationally expensive and dependent on strong
Doppler signatures, rendering them ineffective for detecting low-
speed or hovering UA Vs. To overcome these limitations, we
explore the use of channel state information (CSI) time series
to characterize UA V presence and propose a temporal variation
network for detecting UA V states, including hovering conditions.
Our method utilizes digital terrestrial multimedia broadcast
(DTMB) signals, which have wide coverage and high transmission
power. By capturing DTMB signals with a single receiver, we
reduce the complexity of passive detection systems. First, we
perform channel estimation on the received signal to obtain CSI,
which is arranged in frame order to form a CSI time series. This
enables the modeling of interference channels caused by UA Vs.
We then propose the Channel Estimation and Temporal Variation
Network (CETVNet), which leverages an adaptive noise reduction
module and a multi-period feature extraction module to process
these series for passive UA V state detection. Finally, a real-world
signal dataset is collected using a software-deﬁned radio device to
train and evaluate CETVNet. Experimental results demonstrate
that CETVNet achieves superior performance compared to state-
of-the-art methods.
Index Terms—Passive radar, UA V detection, channel estima-
tion, multivariate time series analysis, neural network.
Received 18 May 2025; revised 21 October 2025 and 26 January 2026;
accepted 17 March 2026. Date of current version 26 March 2026. This
work was supported in part by the National Natural Science Foundation
of China under Grant U24A20247, Grant 62276206, and Grant 62231027;
in part by the Key Research and Development Program of Hunan Province
under Grant 2024AQ2032; and in part by Shenzhen Science and Technology
(S&T) Program under Grant JCYJ20250604185802004. The associate editor
coordinating the review of this article and approving it for publication was
N. Shlezinger. (Corresponding author: Zhu Xiao.)
Jing Bai, Zhuo Zhang, and Licheng Jiao are with the Key Laboratory
of Intelligent Perception and Image Understanding of Ministry of Edu-
cation, School of Artiﬁcial Intelligence, Xidian University, Xi’an 710071,
China (e-mail: baijing@mail.xidian.edu.cn; zhangzhuo@stu.xidian.edu.cn;
lchjiao@mail.xidian.edu.cn).
Zhu Xiao and Tong Li are with the College of Computer Science and
Electronic Engineering, Hunan University, Changsha 410082, China, and also
with Shenzhen Research Institute, Hunan University, Shenzhen 518055, China
(e-mail: zhxiao@hnu.edu.cn; litong@hnu.edu.cn).
Huaji Zhou is with the National Key Laboratory of Electromagnetic Space
Security, Jiaxing 314033, China (e-mail: 19172110640@stu.xidian.edu.cn).
Yongqiang Hei is with the State Key Laboratory of Integrated Services Net-
works (ISN), Xidian University, Xi’an 710071, China (e-mail: yqhei@mail.
xidian.edu.cn).
Xiaohui Liu is with the College of Electronic Science, National Univer-
sity of Defense Technology, Changsha 410073, China (e-mail: liuxh@nudt.
edu.cn).
Digital Object Identiﬁer 10.1109/TWC.2026.3676229
I. I NTRODUCTION
I
N RECENT years, Unmanned Aerial Vehicles (UA Vs)
have been widely applied in various ﬁelds, including aerial
photography, agriculture, logistics, and military operations [1],
[2], [3]. Although the application of UA Vs has signiﬁcantly
improved efﬁciency in these ﬁelds, the widespread presence of
UA Vs has introduced new challenges related to airspace secu-
rity and privacy protection. For example, UA Vs operating in
sensitive or restricted areas, such as airports or military zones,
can enable illicit activities and pose serious threats to aviation
safety and national security [4], [5]. These concerns highlight
the growing need for reliable UA V detection technologies that
are capable of identifying UA V activity regardless of intent or
authorization status.
UA V detection technologies can be classiﬁed into active
and passive approaches, depending on whether the detec-
tion system transmits signals or radiates energy [6]. To
specify, active systems emit dedicated probing signals, such
as radar pulses, to illuminate the environment and detect
reﬂections from aerial targets [7]. In certain environments,
such as battleﬁelds, active systems are susceptible to tar-
geted jamming and may reveal their positions, making them
vulnerable to precision strikes [8], [9]. In contrast, passive
systems rely on analyzing either existing ambient signals
or UA V-generated emissions, such as radio frequency (RF)
and acoustic signals. By avoiding active signal transmission,
passive systems inherently evade detection, resist interference,
and reduce the risk of precision strikes. These advantages
make passive systems particularly suitable for deployment in
sensitive scenarios, including covert operations, electromag-
netic silent missions, and protection of concealed military
installations.
Traditional passive UA V detection systems, using optical
signals, RF signals radiated by aerial targets, or acous-
tic methods, face several challenges [10]. Optical systems
are sensitive to lighting and weather conditions, making
them unsuitable for all-weather surveillance tasks [11]. RF
approaches rely on intercepting control or telemetry signals
emitted by UA Vs, which may be unavailable when UA Vs
operate autonomously, reducing the reliability of such methods
in adversarial or stealth settings [12]. Acoustic-based methods
exploit the distinctive sound signatures generated by UA V
rotors, their performance degrades sharply in the presence
of wind, multiple coexisting sound sources, or unfamiliar
UA V types whose acoustic signatures are not represented
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

14352 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. Passive UA V state detection framework based on channel estimation
and deep learning.
in the training data [13]. In addition to optical methods,
these limitations arise largely from reliance on UA V-emitted
signals.
The above-mentioned observations motivate the exploration
of passive detection approaches that do not depend on such
emissions. In this paper, we aim at developing a passive UA V
detection method using ambient RF signals, which are not
sensitive to visibility and are independent of RF signals or
acoustic emissions generated by UA Vs. To implement such
a method, one can borrow the idea of passive radar, which
operates by exploiting ambient communication signals and
improving target echoes through coherent integration [14].
Note that the coherent integration process relies primarily
on the time delay and Doppler shift of the target echo
relative to the direct-path signal. This method has demon-
strated effectiveness in detecting large, fast-moving objects
such as aircraft and vehicles [15], [16]. In UA V detection
scenarios, its effectiveness is signiﬁcantly reduced due to
the small radar cross-sections (RCS) and low velocities of
UA Vs, which inevitably lead to weak echo signals and min-
imal Doppler shifts [17], [18]. These limitations are further
exacerbated when UA Vs are hovering, as they produce neg-
ligible Doppler variation, rendering them nearly invisible to
the passive detection systems based on coherent integration
[19].
In response to the limitations of coherent integration, partic-
ularly its dependence on strong Doppler shifts and large RCS,
we propose a novel passive UA V detection approach based
on channel estimation. As illustrated in Fig. 1. This method
aims to characterize the presence and movement of UA Vs by
leveraging variations in the wireless channel, enabling passive
detection without requiring pronounced Doppler signatures.
Channel estimation extracts channel state information (CSI),
which captures multipath effects and ﬁne-grained variations in
the channel between the ambient RF source and the receiver.
In the presence of a UA V , its physical movement perturbs
the electromagnetic ﬁeld, altering the channel characteristics.
These changes, resulting from various UA V states such as hov-
ering, vertical ascent, or horizontal ﬂight, are encoded in the
CSI and can serve as discriminative features for detecting UA V
states. This approach follows the general architecture of pas-
sive radar but requires only a single receiving antenna, making
it lightweight and easily deployable. Channel estimation-based
passive sensing has proven effective in some contexts, such
as human pose estimation [20] and indoor localization [21],
where small movements induce measurable changes in the
wireless channel. Despite its promising performance, applying
channel estimation to UA V detection in dynamic outdoor
environments introduces two challenging issues. i) Channel
estimation provides only instantaneous snapshots of the wire-
less channel, making it difﬁcult to establish a reliable mapping
between transient CSI patterns and speciﬁc UA V states.ii) The
subtle nature of UA V-induced channel variations, particularly
in the case of small or hovering UA Vs, makes the system
susceptible to environmental noise.
To specify, two technical challenges remain unresolved.
• How can an accurate mapping be established between
channel estimation results and UAV states? The inﬂuence
of UA Vs on the wireless channel is dynamic, while
channel estimation captures only instantaneous snapshots
of channel characteristics. It is a challenging problem to
establish an accurate mapping between complex varia-
tions of channel characteristics and UA V states.
• How can the impact of environmental noise on detection
performance be effectively mitigated? In practical com-
munication environments, noise is unavoidable and can
signiﬁcantly degrade the accuracy of channel estimation.
Given the small RCS of UA Vs, the resulting variations in
CSI are often subtle, making it particularly challenging
to strike a balance between noise suppression and the
preservation of UA V-speciﬁc features.
To address these challenges, we propose a novel passive
UA V detection framework that leverages deep learning to
map CSI to UA V states to address these challenges. Specif-
ically, CSI is extracted from the frame headers of DTMB
signals and sequentially arranged across multiple frames to
construct a time series that captures temporal variations in
the wireless channel. We then employ deep learning methods
to extract discriminative features from the CSI time series.
We propose a temporal variation network, CETVNet, which
is designed to handle the complexity and noise sensitivity
of the CSI time series. CETVNet consists of two key mod-
ules: an Adaptive Noise Reduction Module (ANRM) and
a Multi-period Feature Extraction Module (MPFEM). The
ANRM exploits the locally linear time-invariant (LTI) nature
of wireless channels to adaptively suppress environmental
noise while preserving UA V-induced variations. The MPFEM
decomposes the CSI time series to extract underlying peri-
odic patterns associated with different UA V motion states.
Finally, a classiﬁcation module maps the extracted features
to a predeﬁned set of UA V states, enabling accurate passive
detection.
The main contributions are highlighted as follows.
• We propose a passive UA V detection method that
employs the CSI time series to characterize the state of
UA V . The presence and movement of UA Vs introduce
variations in the wireless propagation channel, which can
be captured at the receiver through channel estimation.
These variations enable passive UA V detection without
relying on prominent Doppler shifts.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

BAI et al.: PASSIVE UA V DETECTION BASED ON CHANNEL ESTIMATION AND TEMPORAL V ARIATION NETWORK 14353
• We propose a novel temporal variation network, termed
CETVNet, which maps CSI time series to UA V state
classes. CETVNet integrates an adaptive noise reduction
module and a multi-period feature extraction module to
establish an effective mapping between the CSI time
series and UA V states.
• We introduce an adaptive noise reduction method based
on a neural network, which leverages the locally LTI
properties of the channel over short time intervals. The
method employs a multi-scale pooling architecture to sup-
press noise while preserving essential channel estimation
features.
• We collected a real-world dataset using a multirotor UA V
and an SDR device, with DTMB signals serving as the
ambient RF source. The dataset captures the complexity
of practical wireless environments. Experimental results
demonstrate the effectiveness of CETVNet in real-world
UA V detection scenarios.
The remainder of the paper is organized as follows.
Section II reviews related work on passive radar target detec-
tion, channel estimation, and multivariate time-series analysis.
Section III provides a detailed explanation of channel esti-
mation and CETVNet for UA V detection. In Section IV,
we present the experimental setup and results, comparing
CETVNet with other deep learning methods, followed by
analysis and discussion. Finally, Section V concludes the
paper.
II. R ELATED WORK
In this section, we provide a brief overview of the passive
radar system, channel estimation-based passive sensing, and
multivariate time series analysis methods.
A. Passive Radar Systems
In passive radar systems, target detection is typically accom-
plished through coherent integration of signals from the
monitoring channel and the reference channel [14]. Coherent
integration leverages the time delay and Doppler shift between
the target echo signal in the monitoring channel and the direct-
path signal in the reference channel. This process computes
a range-Doppler spectrum, from which the target’s range and
velocity are derived using threshold detection methods. The
efﬁcacy of this approach has been validated across various
signal illumination sources and target types. Xie et al. [22]
designed a passive radar system based on a digital beam-
forming method, which utilized multiple FM signals to detect
civil aircraft taking off and landing at an airport 80 km
away, achieving this with relatively low system complexity.
Pastina et al. [15] utilized the global navigation satellite
system (GNSS) as an opportunistic signal to perform passive
radar imaging of ship targets. Samczy ´nski et al. [16] used
electromagnetic waves generated by 5G cellular network base
stations to remotely sense moving cars in a bistatic geometry.
However, the focus has largely been on high-speed or large
targets, while the challenge of detecting slow or hovering
UA Vs remains less explored.
UA V generates minimal Doppler shift and possesses a small
RCS, leading to a weak echo signal, which makes it difﬁcult
to distinguish from clutter and noise. Recent advancements
have started to address this limitation. Milani et al. [19]
addressed the issue of passive radar’s inability to detect hover-
ing UA Vs by proposing a method that integrates passive radar
with passive source localization technology, enabling UA V
detection based on mobile-static-mobile WiFi communication.
However, this approach requires the UA V to establish Wi-Fi
communication, which limits its applicability.
B. Channel Estimation-Based Passive Sensing
Passive sensing technologies based on various illumina-
tion sources have made signiﬁcant progress through channel
estimation techniques [20], [23]. One prominent application
is WiFi-based human activity recognition, which has gained
attention due to its ability to utilize existing WiFi signals to
estimate human body movements [24], [25]. By analyzing the
CSI of reﬂected WiFi signals, researchers have been able to
infer the position and pose of individuals within a given space.
Similarly, indoor positioning systems based on signals from
WiFi, Bluetooth, and 5G have been developed to provide
accurate location tracking in environments where GPS signals
are unavailable [21], [26]. By leveraging channel estimation
from these wireless signals, these systems can calculate the
relative position of objects or people with high precision,
enabling applications such as asset tracking, smart navigation,
and augmented reality in indoor settings.
Furthermore, advancements in trafﬁc monitoring have also
utilized channel estimation techniques. Tulay and Koksal [27]
designed a system that captures CSI from vehicles and road-
side units (RSUs), making use of existing infrastructure to
monitor trafﬁc conditions. This approach reduced the need
for traditional monitoring equipment while maintaining high
accuracy in tracking trafﬁc states.
C. Multivariate Time Series Analysis
In multivariate time series analysis, deep learning meth-
ods have become the state-of-the-art approach for capturing
complex temporal dependencies and automatically extracting
relevant features from high-dimensional data. Among the
various types of deep learning models, recurrent neural net-
works (RNNs), multilayer perceptrons (MLPs), convolutional
neural networks (CNNs), and transformer models have been
extensively utilized for time series tasks.
One class of methods utilizes RNNs to model sequential
time points under the Markov assumption [28], [29]. However,
these methods often fail to capture long-term dependencies,
and their efﬁciency is affected by the sequential computation
paradigm.
Another class of methods leverages MLPs for time series
analysis. The LightTS [30] captures short-term local patterns
through continuous sampling and long-term dependencies
through sparse sampling, achieving a lightweight MLP struc-
ture for multivariate time series analysis.
CNNs are also widely used for extracting temporal infor-
mation. TCN [31] uses causal convolutions and dilated
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

14354 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
convolutions to enable parallelized time series modeling.
MICN [32] captures data features at different time scales
through a multi-layer convolution network, improving accu-
racy while maintaining lower computational overhead and
fewer parameters. ModernTCN [33] introduces variable-
independent embeddings and, combined with depthwise
separable convolutions, independently models variables and
channels. However, the localized nature of 1D convolution
kernels limits their ability to detect variations over consecutive
time steps. TimesNet [34] extends multivariate time series
from a 1D space to a 2D space, enabling uniﬁed model-
ing of intra-period and inter-period variations in the time
series.
Recently, Transformer models have gained popularity in
sequence modeling for their effectiveness in capturing long-
range dependencies through self-attention mechanisms [35],
[36], [37], [38], [39]. PatchTST [35] uses patch-based
input and independent channels to effectively capture long-
term information in time series while reducing the model’s
spatiotemporal complexity. TST [37] is an unsupervised rep-
resentation learning method for multivariate time series, where
the Transformer architecture is used for autoregressive train-
ing and applied to time series regression and classiﬁcation
tasks. Crossformer [38] uses a dimension-wise embedding
technique to convert time series data into a 2D vector array,
while employing a two-stage attention mechanism to capture
both variable and temporal dependencies, thus modeling both
variable dependencies and time dependencies in time series
data.
Deep learning-based time series analysis has been widely
applied in wireless communication systems [40], [41], [42],
[43], [44], [45], [46]. Building on these developments, we
propose CETVNet, a neural network architecture speciﬁcally
designed for CSI time series analysis in UA V state detection.
CETVNet integrates multi-periodic temporal feature extraction
and adaptive noise reduction to enhance the accuracy of
passive UA V detection.
III. D ETECTION FRAMEWORK FOR UAV STATE
This section describes in detail how to use CETVNet for
passive detection of the UA V state. We ﬁrst describe the
fundamental problem of the passive detection mission of UA V
and the motivation for the proposed CETVNet. Then the
overall framework of CETVNet is previewed, followed by
the introduction of three key components of the CETVNet
framework: CSI time series extraction, adaptive noise reduc-
tion module, and multi-period feature extraction module.
A. Problem Formulation
The passive detection of UA V state based on DTMB signal
can be described as determining the presence and state of
UA V according to the features extracted from the received
DTMB signal. As illustrated in Fig. 2, there is a transmitting
source transmitting the DTMB signal, a receiving antenna,
and possibly UA Vs in the environment. We use a single-
antenna SDR device for signal sampling to save data ofﬂine
for subsequent processing. The DTMB signal received by the
receiver can be expressed as
r(t) =A0s(t) +
Nc∑
n=1
Ans(t−τn)
+
Nt∑
m=1
Bms(t−τm)ej2πfdmt +n(t), (1)
where s(t) is the direct-path signal from the transmitting
source, A0 is its complex amplitude. An is the complex
amplitude, and τn is the delay (relative direct-path signal
delay) of the n-th multipath signal, and Nc is the number of
multipath signals.Bm,τm andfdm are the complex amplitude,
delay, and Doppler frequency shift of m-th target echoes, and
Nt is the number of UA V targets. n(t) is the noise such as
Additive White Gaussian Noise (AWGN).
The signal model can be simpliﬁed by using the channel
model as follows:
h(t) =
Nc∑
n=1
Anδ(t−τn) +
Nt∑
m=1
Bmδ(t−τm)ej2πfdmt, (2)
where h(t) is the channel impulse response and δ(t) is the
unit impulse response function.
The received signal r(t) is a convolution of the transmitted
signals(t) with the channel response h(t), plus noise n(t). In
continuous time, the r(t) can be expressed as
r(t) =
∫ ∞
−∞
s(t)h(t−τ)dτ +n(t). (3)
From Eq. (3) and Eq. (2), it is evident that the presence and
movement of the UA V along the signal transmission path alter
both the channel response h(t) and the received signal r(t).
As a result, the UA V state can be detected through the received
DTMB signalr(t). However, the variability of obstacles in the
transmission path and the inherent noise uncertainty present
signiﬁcant challenges for detection. If DTMB signals corre-
sponding to different UA V states can be obtained through prior
preparation, the core challenge in DTMB-based UA V state
detection becomes establishing a reliable mapping between
the received DTMB signals and the UA V states.
An obvious problem is that the s(t) is constantly changing,
thus the r(t) is constantly changing even if the h(t) is
unchanged. If the r(t) is used directly as the independent
variable of the mapping, the mapping function will be difﬁcult
to optimize because it contains too much uncertain informa-
tion. Fortunately, part of the s(t) is known, which means h(t)
is available. Therefore, using h(t) as the mapping parameter
will be more conducive to the optimization of the mapping
function.
The primary objective of this paper is to establish a mapping
from the channel impulse response h to the UA V statey. The
collected DTMB signal passes through h, which belongs to
the sample space H, while y represents the UA V state within
the category space Y. The joint probability distribution of H
andY is denoted as PH×Y. UA V state feature extractor and
classiﬁer is modeled as a function F(W) with parameters
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

BAI et al.: PASSIVE UA V DETECTION BASED ON CHANNEL ESTIMATION AND TEMPORAL V ARIATION NETWORK 14355
Fig. 2. CETVNet framework for UA V state passive detection. In the ﬁrst stage, an SDR device, such as the USRP B210, is used to capture the DTMB
signal. The frame header of the signal frame is then extracted, and channel estimation is performed. The results of multi-frame estimations are combined to
form a CSI time series. In the second stage, the proposed CETVNet model is applied for supervised training of the CSI time series, establishing the mapping
between the CSI time series and the UA V state.
W (W∈W ). The goal is to determine W such thatF(W) :
H→Y is optimized. This can be formulated as
W∗ = arg min
W∈W
E(h,y)∼PH×YLcls(F(h; W),y ), (4)
whereLcls is a supervised loss function used to measure the
difference between predicted labelF(h; W) and the true label
y.
SincePH×Y is typically unknown, it is approximated using
a training dataset Dh, leading to the revised optimization
objective:
W∗ = arg min
W∈W
E(h,y)∼DhLcls(F(h; W),y ), (5)
where Dh ={(hn,yn)}Nn=1 contains a ﬁnite set of labeled
channel response samples.
In this paper, we ﬁnd a suitable method to construct Dh,
and propose a deep learning model named CETVNet to
construct the mapping relationship F(W). The UA V state
detection method based on channel estimation and CETVNet
is illustrated in Fig. 2.
The ﬁrst stage is the construction of the dataset Dh con-
taining channel response and UA V state information. Using
a single receiver to capture the DTMB signal, the UA V
in the signal propagation path causes multipath fading and
Doppler shift of the transmitted signal, which is implicit in
the channel response. By extracting the pilot portion of the
DTMB signal frame and performing channel estimation, the
channel response corresponding to each pilot can be obtained.
By combining the channel response of multiple continuous
frames and recording the corresponding UA V state at this time,
a sample (hn,yn) of Dh can be obtained.
The second stage is to establish the mapping between h and
y, i.e.F(W), to enable the detection of the UA V state. This
mapping function, F(W), is implemented by the proposed
CETVNet model. CETVNet is built on two core modules:
the ANRM and the MPFEM. The former performs pooling
and reorganization of the channel estimation results from
adjacent frames, leveraging the properties of the LTI system
to achieve adaptive noise reduction. The latter extracts multi-
period features by expanding the 1D space of the CSI time
series into a 2D space, capturing both local oscillations and
long-term trends. Finally, an MLP classiﬁer is used to assess
the UA V state.
B. Channel Estimation
DTMB is the digital terrestrial television broadcasting
standard in China, released in August 2006. It employs
time-domain synchronized orthogonal frequency division mul-
tiplexing (TDS-OFDM) technology. A signal frame comprises
a frame header (FH) and a frame body (FB), both operating
at a baseband symbol rate of 7.56 Msps. The FH is composed
of a pseudorandom noise (PN) sequence, modulated with
4QAM. The FH is inserted before each FB as a guard interval,
with higher transmission power, used for synchronization
and channel estimation. Each FB in a signal frame carries
3,780 valid symbols, lasting 500 µs (3,780× 1/7.56 µs).
To meet different application requirements, the DTMB sys-
tem deﬁnes three types of frame modes, as illustrated in Fig. 3.
Among them, frame mode (a) with a 420-symbol frame header
(PN420 mode) and frame mode (c) with a 945-symbol frame
header (PN945 mode) are multi-carrier modes, while frame
mode (b) with a 595-symbol frame header (PN595 mode) is
a single-carrier mode.
Taking the PN420 mode as an example, its structure is
illustrated in Fig. 4. The frame header comprises 420 symbols,
including a preamble, a PN255 sequence, and a postamble.
The preamble and postamble are deﬁned as the cyclic exten-
sions of the PN255 sequence, with the preamble length being
82 symbols and the postamble length being 83 symbols. The
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

14356 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 3. Three types of frame modes in DTMB system.
Fig. 4. Frame header structure of PN420 mode.
PN255 sequence is generated by an 8th-order linear feedback
shift register (LFSR) polynomial.
Based on the initial state of the 8th-order LFSR, 255 dif-
ferent phase-shifted PN420 sequences can be generated.
To minimize the correlation between adjacent values, the
PN420 mode selects 225 PN420 sequences from a total of
255 sequences, numbered from 0 to 224, which are used as
identiﬁers for the signal frame number. At the beginning of
each superframe, the sequence number resets to 0. Further-
more, when frame number indication is not required, the PN
sequence does not undergo phase shifts and instead uses the
PN sequence with sequence number 0 uniformly.
Frame header extraction is the ﬁrst step in channel estima-
tion. This process involves determining the frame mode of the
received signal, which can be detected by sliding correlation
with local PN sequences. The method primarily leverages
the strong autocorrelation properties of the PN frame header
sequence. The received signal is cross-correlated with the three
types of local PN sequences, and the peak magnitude of the
autocorrelation result is used to identify the frame header
mode. DTMB signal frame synchronization is then achieved
by analyzing the differences in the peak positions of the cross-
correlation results for each frame mode. This process relies on
the cyclic displacement relationship between the parity and
zero-phase frames.
Channel estimation utilizes the extracted FH to estimate
the channel impulse response h, based on the known train-
ing sequence x, and the received signal r. The received
signal is the convolution of the transmitted signal with the
channel response, plus noise. In practice, the continuous-
time channel impulse response h(t) deﬁned in Eq. 2 is
sampled at the baseband symbol rate and approximated by
a ﬁnite-length discrete-time impulse response, assuming a
ﬁnite channel delay spread. Let the FH sequence be denoted
as x = [ x1,x 2,...,x N]T , the received signal as r =
[r1,r 2,...,r N]T , and the channel’s ﬁnite impulse response
as h = [h 1,h 2,...,h L]T . The relationship between these
variables can be expressed as
rn =
L∑
k=1
hkxn−k+1 +nn, for n = 1, 2,...,N, (6)
where n = [n 1,n 2,...,n N]T represents the AWGN, which
follows the distribution N (0,σ 2).
The convolution operation can be represented using a
Toeplitz matrix. The Toeplitz matrix X is constructed from
the FH sequence as shown below:
X =


x1 x2 x3 ... x L
x2 x3 x4 ... x L+1
x3 x4 x5 ... x L+2
... ... ... ... ...
xN−L+1 xN−L+2 xN−L+3 ... x N

.
(7)
The dimensions of this matrix are (N−L + 1)×L, where
N is the length of the training sequence and L is the channel
estimation length. Using this construction, the received signal
model can be rewritten as
r = Xh + n, (8)
where r∈ C(N−L+1)×1, X∈ C(N−L+1)×L, and h∈ CL×1.
To estimate the channel impulse response h, the least
squares (LS) method minimizes the error between the received
signal and the model-predicted signal:
ˆh = arg min
h
‖r− Xh‖2, (9)
where‖·‖ 2 represents the 𝓁2-norm.
By expanding the cost function:
J(h) = (r− Xh)H(r− Xh), (10)
and taking the derivative with respect to h, then setting it
to zero, the least squares solution for channel estimation is
derived as:
ˆh = (XH X)−1XH r, (11)
where XH denotes the conjugate transpose of the X.
The dimension of ˆh is determined by L, which corresponds
to varying levels of granularity in channel estimation. The
impact of this parameter is tested in detail in Section IV.
To capture the channel’s temporal variations, we construct
the CSI time series vector ˜h by aggregating magnitude infor-
mation from multiple consecutive frames. The magnitude of
each element in ˆh, denoted as|ˆh|∈ RL, is computed element-
wise to retain the amplitude information. To form the CSI time
series ˜h∈ RL×T , we sequentially stack the magnitude vectors
fromT adjacent frames, starting at time index t. That is, ˜h is
deﬁned as
˜h =[|ˆh1|,|ˆh2|,..., |ˆhT|]. (12)
In Eq. (5), Dh can be reformulated as {(˜hn,yn)}Nn=1.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

BAI et al.: PASSIVE UA V DETECTION BASED ON CHANNEL ESTIMATION AND TEMPORAL V ARIATION NETWORK 14357
C. Adaptive Noise Reduction
The denoising strategy in the proposed CETVNet archi-
tecture is grounded in a fundamental statistical principle:
in a locally linear time-invariant (LTI) system, the variance
of independent noise components decreases with temporal
averaging.
In practice, each complex-valued CSI sample can be
expressed as
ˆhi =hi +ni, (13)
where hi is the true complex channel coefﬁcient and ni
denotes zero-mean complex Gaussian noise with E[ni] = 0
and Var(ni) =σ2.
The amplitude observation|ˆhi| follows a Rician distribution,
which can be approximated as a locally additive Gaussian
process under moderate-to-high SNR conditions. By align-
ing hi = |hi|ejφi to the real axis through an equivalent
phase rotation, and linearizing |ˆhi| =√(|hi| +X)2 +Y 2 at
(X,Y ) = (0, 0) with X,Y ∼N
(
0,σ 2/2), we obtain
|ˆhi|≈| hi| +ξi, (14)
where ξi∼N
(
0,σ 2/2) is a zero-mean real Gaussian pertur-
bation. Hence, at moderate-to-high SNR, the CSI amplitude
can be modeled as an approximately additive real Gaussian
process:
|ˆhi| =|hi| + ˜ni, (15)
where ˜ni are i.i.d. noise terms when the true channel varies
slowly within the averaging window.
To further improve the effective SNR, multiple consecutive
observations are averaged. Given N independent CSI samples
{|ˆh1|,..., |ˆhN|}, the averaged observation is
¯h = 1N
N∑
i=1
|ˆhi| = 1N
N∑
i=1
|hi| + 1N
N∑
i=1
˜ni = ¯s + ¯n, (16)
where ¯s and ¯n denote the averaged channel and noise compo-
nents, respectively.
Since the duration of a DTMB frame is less than 1 ms,
the channel can be regarded as quasi-static over several
consecutive frames, i.e., |hi| ≈¯s when N is small. Under
this assumption,
¯h =|hi| + ¯n. (17)
Because the ˜ni are i.i.d. with Var(˜ni) =σ2/2, the variance
of the averaged noise is reduced to
Var(¯n) = σ2
2N. (18)
This relationship demonstrates the denoising effect of tem-
poral averaging: as N increases, the noise variance decreases
proportionally to 1/N. The corresponding SNR improvement
can be quantiﬁed as
SNR¯h = E[|hi|2]E[|¯n|2] = E[|hi|2]σ2/(2N) = 2N· SNRhi. (19)
Consequently, the averaged observation ¯h effectively
enhances the CSI quality by a factor proportional to the
averaging window size N.
Fig. 5. Adaptive Noise Reduction Module (ANRM).
In practical applications, determining the optimal value of
N for temporal averaging is non-trivial. A too-small N pro-
vides insufﬁcient noise suppression, while an excessively large
N violates the assumption of a locally time-invariant (LTI)
channel. To overcome this limitation, we propose the Adaptive
Noise Reduction Module (ANRM), which performs learnable
multi-scale averaging for noise reduction, as illustrated in
Fig. 5. ANRM leverages the theoretical variance-reduction
principle described in Eq. (19) and implements it in a data-
driven, adaptive fashion.
The input tensor is a single-sample CSI time series Xin∈
RL×T , where L denotes the feature dimension corresponding
to the per-frame CSI vector length, andT denotes the temporal
dimension representing the number of CSI frames.
To enhance SNR while retaining discriminative channel
variations, the ANRM applies multi-scale 1-D average pooling
along the temporal axis (T dimension):
pk = AvgPool1dk,s =1(Xin), k ∈{ 2, 3, 4}, (20)
where k and s denote the pooling kernel size and stride,
respectively. Padding is applied to preserve the temporal length
T for all outputs. Each pooling operation performs a local
temporal average, reducing noise variance approximately by
1/k and improving the SNR of the CSI sequence.
The resulting multi-scale averaged features {pk}k=2,3,4
capture CSI dynamics at different temporal resolutions and
are concatenated along the feature dimension:
P = concat
(
p2, p3, p4
)
∈ R3L×T. (21)
To fuse these multi-scale averaged features, we concatenate
them and apply a 1D convolution with kernel size 1, which
performs a point-wise linear projection to map the concate-
nated representation back to the original channel dimension.
P′(:,t) = W1 P(:,t), t = 1,...,T, (22)
where W1∈ RL×3L denotes the shared weight matrix of a
1D convolution with kernel size 1.
The convolution layer serves as a learnable weighting mech-
anism, allowing the model to adaptively integrate multi-scale
averaged features at each time step, thereby attenuating noise
while preserving key CSI details.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

14358 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Finally, a residual connection adds the original input xin
back to the fused output P′:
Xnr = Xin + P′. (23)
Essentially, the ANRM leverages the fundamental statis-
tical principle of variance reduction through averaging and
transforms it into a trainable adaptive denoising module,
addressing the challenge of selecting the averaging windowN.
By utilizing multi-scale average pooling and learnable fusion
steps, the module effectively approximates the integration of
denoised samples at different noise reduction levels, providing
a robust foundation for feature extraction.
D. Multi-Period Feature Extraction
The MPFEM is designed to capture periodic patterns in the
CSI time series that arise from UA V motion. In a CSI time
series, consecutive channel estimates record both short-term
ﬂuctuations and long-term variations of the wireless chan-
nel. These variations include periodic micro-Doppler effects
produced by rotor rotation and distinct multipath dynamics
associated with different ﬂight states (e.g., vertical or hori-
zontal movement). To model such periodic behaviors across
multiple temporal scales, MPFEM reshapes the 1D CSI time
series into a 2D tensor according to predeﬁned period lengths,
where each row represents time samples within one period and
each column corresponds to the same phase across different
periods.
As shown in Fig. 2, CETVNet adopts a residual structure.
Given a CSI time series input X1D∈ RL×T , the input is ﬁrst
projected into a latent feature space through a learnable 1-D
convolutional embedding layer:
X01D = Embed(X1D) = Conv1dk=3(X1D; Wemb), (24)
where Wemb∈ Rdmodel×L×3 is a 1-D convolution kernel with
input channelsL and output channelsdmodel, kernel size 3, and
circular padding to preserve temporal length T . The output
X01D∈ Rdmodel×T serves as the embedded representation fed
into the ﬁrst MPFEM layer.
For the l-th MPFEM layer, the operation is expressed as
Xl1D = MPFEM(Xl−11D ) + Xl−11D . (25)
The core operation of MPFEM is to convert 1D input into
2D and then extract features using Inception blocks. Given
a predeﬁned period set P = {p1,p 2,...,p s}, each period
length pi reshapes the 1D sequence into a 2D tensor Xl,i2D∈
Rdmodel×pi×T/p i. The reshaping and convolutional operations
are deﬁned as
Xl,i2D = Reshapepi(Padding(Xl−11D )),
ˆXl,i2D = InceptionBlock(Xl,i2D),
ˆXl,i1D = ReshapeT(ˆXl,i2D), (26)
where the InceptionBlock(·) employs multi-scale 2D convolu-
tions to capture both local and global periodic dependencies.
An InceptionBlock consists of two sequential Inception layers
with a GELU activation in between, formally expressed as
InceptionBlock = Inception1(dmodel,d mid)
Algorithm 1 Calculation Flow of MPFEM
Input: X∈ RC×T ;P ={p1,p 2,...,p s}; K.
Output: Xf∈ RC×T .
1: Initialize an empty list res list = [].
2: forp∈P do
3: Reshape X to X′∈ RC×(T/p)×p .
4: ¯X1← Inception(X′,K ).
5: X′′← GELU( ¯X1).
6: ¯X2← Inception(X′′,K ).
7: Reshape ¯X2 to Xb∈ RC×T .
8: res list← res list∪{Xb}.
9: end for
10: ˆX← sum(res list).
11: Xf← X +ˆX.
12: return Xf .
GELU
−−−→Inception2(dmid,d model). (27)
wheredmodel denotes the number of input and output channels
of the block, and dmid denotes the number of intermediate
channels between the two Inception layers.
The Inception(·) performs multi-scale 2-D convolutions to
jointly model ﬁne-grained and global periodic variations in
the reshaped CSI maps. Speciﬁcally, it applies four parallel
convolutional kernels with sizes 1× 1, 3× 3, 5× 5, and 7× 7.
The outputs of all kernels are averaged to form a uniﬁed multi-
scale representation:
Inception(X2D) = 1K
K∑
i=1
Conv(2i−1)×(2i−1)(X2D), (28)
where K = 4 is the number of convolution kernels.
After processing all s period transformations, the results are
aggregated:
MPFEM(Xl1D) =
s∑
i=1
ˆXl,i1D. (29)
In Algorithm 1, the number of feature channels after
embedding is explicitly deﬁned as C =dmodel. Each MPFEM
block receives X∈ RC×T and outputs Xf∈ RC×T , ensuring
consistency across layers.
Following the MPFEM feature extraction, the fused feature
map Xf is passed through a lightweight classiﬁer to produce
the ﬁnal UA V-state prediction:
y = Softmax(W2· Flatten(Xf) + b), (30)
where W2 and b denote the learnable weights and bias of the
ﬁnal fully connected layer.
IV. E XPERIMENTS
In this section, we demonstrate the superiority of CETVNet
in the UA V state detection task through a series of experiments.
First, we describe the data collection process and experimental
setup. Next, we compare CETVNet with other existing meth-
ods. Finally, we conduct ablation experiments to evaluate the
effectiveness of the proposed modules.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

BAI et al.: PASSIVE UA V DETECTION BASED ON CHANNEL ESTIMATION AND TEMPORAL V ARIATION NETWORK 14359
Fig. 6. Multi-period feature extraction module (MPFEM).
A. Data Acquisition
We use a ground-mounted DTMB receiving antenna and a
USRP B210 to capture over-the-air DTMB broadcasts at three
frequency points. Although the USRP B210 supports multiple
receive channels, only a single RX antenna and one receive
channel are used in the experiments. The DTMB broadcasts act
as the opportunistic illuminator, while a DJI Matrice 350 RTK
(large platform) serves as the primary controllable UA V target.
To assess generalization to unseen platforms, we additionally
collect data with a DJI Air 3s (medium) and a DJI Mini 4 Pro
(small).
Data are collected in two representative environments:
(i) Scene A (clean)—an open area with no pedestrians or vehi-
cles within a∼50 m radius of the receiver; (ii) Scene B (lightly
interfered)—near a road intersection with slow pedestrians and
passing vehicles within ∼30 m of the receiver, introducing
low-frequency clutter-like temporal variations unrelated to the
UA V .
As illustrated in Fig. 7, we consider ﬁve classes with
consistent notation throughout the paper.
Y1 (horizontal along antenna boresight): The UA V ﬂies
approximately along the RX boresight at a ground range of
200−300 m from the RX, with an altitude of about 50 m.
The speed is 8− 14 m/s.
Y2 (horizontal perpendicular to boresight): The UA V ﬂies
on a lateral track perpendicular to the RX boresight at a
nominal ground range of 200 m from the RX. The cross-
track excursion is±100m around the boresight intercept, the
altitude is about 50 m, and the speed is 8−14 m/s.
Y3 (vertical up-and-down): The UA V holds a nearly ﬁxed
ground range of about 200 m from the RX and performs
Fig. 7. UA V state in this work: (a) Y1: horizontal motion along the antenna
boresight, (b) Y2: horizontal motion perpendicular to the boresight, (c) Y3:
vertical up-and-down motion, (d) Y4: hovering, and (e) N: No-UA V .
Fig. 8. Real-world passive DTMB sensing setup: opportunistic DTMB
transmitter, receiving antenna, USRP B210 sampler, and the UA V target. Two
environments are considered: an open, clean Scene A and a lightly interfered
Scene B near a road intersection.
repeated vertical motions between 30−80 m. The vertical
speed is approximately 3 m/s.
Y4 (hovering): The UA V hovers at a ﬁxed point at a ground
range of about 200 m from the RX and an altitude of about
50 m.
N (No-UAV): No UA V is present within the monitored
area during acquisition. The RX receives only the direct-path
DTMB signal and environmental multipath/clutter.
The real-world acquisition setup is shown in Fig. 8. Three
broadcast frequency points correspond to distinct DTMB
frame-header modes. After channel estimation (Sec. III-B),
we obtain three datasets named PN420, PN595, and PN945.
Table I summarizes the dataset information.
B. Implementation Details and Metrics
1) Dataset Splits: We conducted experiments on each of the
three frame header modes, namely PN420, PN595, and PN945.
For each mode, we randomly split the data into 70%/30% for
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

14360 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE I
DATASET PARAMETERS AND COMPOSITION
train/test, ensuring no temporal overlap between segments. We
designed three sets of experiments to evaluate the performance
of CETVNet.
• Basic experiment. Training and testing are conducted in
scenario A, where ﬁve states of the UA V are classiﬁed
to demonstrate the effectiveness of CSI-based passive
sensing.
• Cross-scene. Train on Scene A (clean), and test on Scene
B (lightly interfered); and the reverse (train on B, test on
A). This setup probes robustness to ambient, non-UA V
temporal variations near the RX.
• Cross-UAV (leave-one-platform-out). Using the three
UA V platforms (large: Matrice 350 RTK; medium: Air
3s; small: Mini 4 Pro), we train on two platforms and
test on the held-out platform.
2) Experimental Setup: We set the period set in Eq. (26) to
P ={8, 16, 32} (i.e.,s = 3 periods), and set the dmodel,dmid
in Eq. (27) to 32, 24, respectively. We use Adam with learning
rate 1e−3, batch size 32, weight decay 1e−4, and train for up
to 100 epochs. Early stopping monitors the validation loss with
patience 5. The classiﬁer employs a dropout rate of 0.2.
Data preprocessing and channel estimation are performed in
MATLAB R2023a; neural network models are implemented in
PyTorch 1.13. All experiments run on a workstation with an
NVIDIA GTX 1080 GPU (8 GB) and an Intel Xeon(R) Gold
6240 CPU @2.60GHz CPU.
3) Evaluation Metrics: We report standard classiﬁcation
metrics and diagnostic measures as follows:
Accuracy (%): overall correct predictions over all classes.
Precision, Recall, and F1-score (%): computed per class and
then macro-averaged across {N, Y1–Y4} unless speciﬁed.
Confusion Matrices: shown per mode to visualize inter-class
confusions.
False-Alarm Rate (FAR): proportion of No-UA V segments
misclassiﬁed as any UA V-present class, deﬁned as
FAR = #{N→ Y1−Y4}#{N} × 100%. (31)
Two-Class Accuracy: In cross-scene and cross-UA V testing,
we also report binary classiﬁcation accuracy between UA V-
present and No-UA V conditions, where the four UA V motion
states{Y1–Y4} are merged into a single positive class.
Fig. 9. The coherent integration results of the UA V target in the four states.
(a) Y1: horizontal motion along the antenna boresight, (b) Y2: horizontal
motion perpendicular to the boresight, (c) Y3: vertical up-and-down motion,
and (d) Y4: hovering in the air.
C. Performance of the Proposed CETVNet
1) Coherent-Integration Baseline: Firstly, the four states of
the UA V are detected using the coherent integration method,
with an integration time of 1 second. The detection results are
shown in Fig. 9. Under our experimental conditions, the UA V
target in all four states is undetectable.
2) Comparison With Time-Series and CSI-Speciﬁc Mod-
els: We next classify CSI sequences and compare CETVNet
against two groups of baselines (all models take 128× 128
CSI as input and follow the protocols in Sec. IV-B).
a) General time-series models: LSTM [28], LightTS
[30], MICN [32], TimesNet [34], ModernTCN [33], Auto-
Former [36], TST [37], CrossFormer [38], PatchTST [35],
iTransformer [39].
b) CSI-speciﬁc models: WPFormer —a Transformer
backbone tailored to CSI tokenization/fusion for wire-
less sensing [47]; CaiT & VanillaViT—vision-style self-
attention applied to CSI-derived time–channel maps [48];
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

BAI et al.: PASSIVE UA V DETECTION BASED ON CHANNEL ESTIMATION AND TEMPORAL V ARIATION NETWORK 14361
TABLE II
PERFORMANCE COMPARISON OF CETVN ET WITH OTHER NETWORKS FOR TIME SERIES CLASSIFICATION ON THREE DATASETS
Fig.
10. Confusion matrices of CETVNet for PN420, PN595, and PN945.
THAT—a two-stream convolution–Transformer hybrid mod-
eling temporal–spectral dependencies in CSI [49].
Table II reports multi-class Accuracy and macro-averaged
Precision/Recall/F1 for PN420/PN595/PN945. All methods
achieve meaningful detection, conﬁrming that CSI sequences
carry UA V-induced signatures. CETVNet achieves the best
results, with accuracy consistently above 94% and F1 typically
2–5 percentage points higher than strong baselines. This
demonstrates the superiority of the CETVNet model for this
task.
Across the three DTMB FH modes, detection accuracy
follows PN945> PN420> PN595. This stems from PN struc-
ture/protocol details: PN595’s single-PN design and lower FH
power yield lower-quality CSI time series, whereas PN945’s
longer FH and higher FH power deliver the best detection
performance.
3) Confusion Matrices and FAR: To analyze error modes,
Fig. 10 shows CETVNet’s confusion matrices per DTMB
mode. Confusion mainly occurs between Y1 and Y2, and
between Y3 and Y4, because the speeds of these states are
close. From the confusion matrix, it can be derived that the
FAR for the PN420 mode is 1.32%, while no false alarms
TABLE III
CROSS -SCENE PERFORMANCE (ACCURACY %)
occur in the other two modes, resulting in an average FAR of
0.44% across the three frame header modes.
4) Cross-Scene Generalization: We evaluate robustness
across environments by training on one scene and testing on
the other (Sec. IV-B). Table III summarizes the results.
Moving from the clean Scene A to the lightly interfered
Scene B incurs a larger drop in multi-class accuracy due
to pedestrian/vehicle-induced low-frequency clutter near the
RX, which partially overlaps with UA V temporal signatures.
Nevertheless, binary detection (UA V-present vs. N) remains
high (≥ 97.97%), indicating CETVNet reliably distinguishes
UA V presence under varying environmental conditions.
5) Cross-UAV Generalization: We further examine transfer-
ability to unseen UA V platforms by holding out one platform at
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

14362 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 11. Experimental results of UA V state classiﬁcation in different average window size. (a) PN420. (b) PN595. (c) PN945.
TABLE IV
CROSS -UAV PERFORMANCE (ACCURACY %)
test time while training on the other two (Sec. IV-B). Table IV
reports the multi-class accuracy.
CETVNet maintains >85% multi-class accuracy and
>97% two-class accuracy when tested on an unseen UA V
type, demonstrating strong platform-level generalization. This
robustness stems from CETVNet’s cross-period aggregation,
which captures geometry/kinematics-invariant temporal struc-
tures.
In summary, CETVNet achieves state-of-the-art accuracy,
low FAR, and strong robustness to environmental and platform
variations, demonstrating its effectiveness and generalizability
for real-world passive UA V detection.
D. Ablation Study
1) Average Denoising Effectiveness Validation: To assess
the validity of the LTI system assumption and identify an
appropriate average window size, we calculate the averaged
CSI time series using various values of N in Eq. 16. Average
window size N denotes the number of CSI frames. Then we
compare the performance of CETVNet (without the ANRM
module) and other methods with different average window
sizes. We evaluate results with no denoising and for N values
ranging from 2 to 8. The results, illustrated in Fig. 11, indicate
that although there are performance differences across meth-
ods, the best results were achieved whenN was between 2 and
6. This demonstrates the effectiveness of averaging denoising.
However, the optimal value of N for each model, including
TABLE V
COMPARISON OF ANRM, W AVELET DENOISING (WD), AND KALMAN
FILTERING (KF) IN TERMS OF ACCURACY (%)
CETVNet (without the ANRM module), varies across different
modes. Despite this, CETVNet still achieved the best overall
performance. All experiments are performed on time series
with a shape of 128× 128.
2) ANRM Versus Wavelet and Kalman Filtering: We further
compare the proposed ANRM with two representative classical
denoising methods applied to the CSI time series before
classiﬁcation: (i) discrete wavelet denoising (WD) and (ii)
Kalman ﬁltering (KF).
For each dataset, the parameters of both ﬁlters were opti-
mized through grid search on the validation set to balance
noise suppression and feature preservation. In the Kalman
ﬁlter, different values ofα,Q (process noise), andR (measure-
ment noise) were explored. For wavelet denoising, multiple
mother wavelets (db4, sym4) and decomposition levels (3)–(6)
were tested under both VisuShrink and SURE thresholding
rules. All denoised sequences were then fed into the same
CETVNet backbone with identical training hyperparameters
to ensure fair comparison. Table V reports the multi-class
accuracy for each DTMB frame-header mode.
Beneﬁting from its adaptive capability, ANRM demonstrates
consistently superior accuracy compared to the two ﬁxed
ﬁltering approaches.
3) Evaluate the Inﬂuence of CSI Phase: Through this
experiment, we demonstrated the reason for not using CSI
phase information. In the Amplitude-only setting, the CSI
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

BAI et al.: PASSIVE UA V DETECTION BASED ON CHANNEL ESTIMATION AND TEMPORAL V ARIATION NETWORK 14363
TABLE VI
COMPARISON OF AMPLITUDE -ONLY AND AMPLITUDE +PHASE CSI
INPUTS (ACCURACY %)
amplitude matrix (L×T ) is directly used as input, which is the
default conﬁguration in our method. In the Amplitude+Phase
setting, both the amplitude and the phase (2L ×T ) of the
CSI are included. Both variants are processed by the same
CETVNet architecture under identical training settings, differ-
ing only in input channel dimension.
The results are shown in Table VI, including phase infor-
mation does not improve performance and in fact reduces
accuracy. This degradation is possibly caused by residual asyn-
chronous phase errors (e.g., carrier frequency offset, sampling
frequency offset, and oscillator jitter) that introduce non-
stationary noise and disrupt temporal consistency.
4) Dimension of CSI Time Series: We explore different
combinations of the CSI dimension and the CSI time series
length to determine the most suitable dimensions for the
CSI time series. The CSI dimensions are set to [32, 64,
128], and the CSI time series lengths to [32, 64, 128, 256],
with CETVNet used for comparison. The accuracy results,
illustrated in Table VII, indicate that the optimal combination
across all three frame header modes is 128×128. A reasonable
explanation is that longer time windows raise the incidence of
transient interference/impulsive noise and thereby degrade the
CSI time-series quality. Hence, in the following experiments
we adopt an input size of 128× 128.
5) Effectiveness of ANRM and MPFEM: Ablation exper-
iments were conducted to evaluate the effectiveness of the
two main components of CETVNet, ANRM and MPFEM.
The performance of the model was compared across four
different combinations under the three frame header modes.
For MPFEM, the multi-period parameters were set to the
sequence length for the ablation study. The results, illustrated
in Table VIII, demonstrate that, compared to the baseline,
ANRM improves performance by 2% to 6%, MPFEM pro-
vides a 2% to 9% performance boost, and the combination
of ANRM and MPFEM results in a 5% to 13% performance
improvement. These ﬁndings validate the effectiveness of both
modules.
6) Interpretability Analysis of ANRM: To further enhance
the interpretability of the ANRM module, this section analyzes
the behavior of the learnable fusion weights through visual-
izations and experiments under different scenarios.
Fig. 12 shows the learned fusion weights in the 1D convo-
lution layer of ANRM, while Fig. 13 plots the weight variance
for each input CSI channel. Both ﬁgures reveal non-uniform
fusion patterns across pooling scales, with higher variance
concentrated in the early part of the CSI response (short-delay
components), suggesting that the fusion layer applies more
selective weighting to this region.
Fig. 14 compares the relative branch contribution of ANRM
pooling scales for two models trained separately on Scene A
Fig. 12. Heatmap of the learned 1D convolution fusion weights in ANRM
(input channels are concatenated from three pooling-scale branches).
Fig. 13. Variance (across output channels) of the learned fusion weights for
each input CSI channel.
Fig. 14. Relative contribution of each pooling-scale branch in two scenes.
and Scene B, where the contribution at scale k is measured
as its normalized share of the 1D convolution fusion output.
In Scene A, k = 2 has the largest contribution, suggesting
that smaller pooling scales better capture ﬁne-grained details
under low noise. In Scene B, k = 4 becomes the most
prominent, indicating that larger pooling scales tend to be
favored to suppress interference and yield more stable feature
representations.
7) Computational Complexity and Real-Time Feasibility:
CETVNet is designed to be lightweight and efﬁcient for
real-time UA V detection. Table IX compares its computa-
tional complexity and inference latency with the four best-
performing baseline models—THAT, CrossFormer, TimesNet,
and MICN—using a 128× 128 CSI input.
CETVNet achieves the best trade-off between accuracy
and efﬁciency, requiring only 0.24M parameters and 69.5M
FLOPs—signiﬁcantly fewer than Transformer-based baselines
such as CrossFormer and THAT. Its inference latency is
extremely low: 0.24 ms on GPU and 1.03 ms on CPU per
sample. These results demonstrate that CETVNet satisﬁes the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

14364 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE VII
THE EFFECT OF THE DIMENSION OF CSI AND THE LENGTH OF CSI T IME SERIES ON CETVN ET PERFORMANCE
TABLE VIII
ANRM AND MPFEM M ODULE ABLATION EXPERIMENTS
TABLE IX
COMPARISON OF MODEL COMPLEXITY AND INFERENCE LATENCY
low-latency and low-power requirements for real-world edge
deployment and real-time UA V monitoring.
V. C ONCLUSION
In this paper, we address the challenges of passive UA V
state detection using ambient RF signals. We identify two
key technical barriers. i) The difﬁculty of detecting slow-
moving or hovering small UA V based on coherent integration;
ii) The need for the detection system to adapt to variations in
the signal source and the channel noise. To overcome these
challenges, we propose CETVNet, which leverages channel
estimation to capture the channel response over time, treating
it as time-series data to detect interference caused by UA V .
Assuming an LTI system, we introduce an adaptive noise
reduction module to mitigate the effects of channel noise.
Additionally, we present the multi-period feature extraction
module to extract multi-period features by processing the
CSI time series in a two-dimensional space. Experiments on
real SDR-collected data prove CETVNet’s effectiveness. The
CETVNet signiﬁcantly improves the detection of low-speed
or hovering UA V , making it a promising solution for passive
UA V detection.
REFERENCES
[1] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets integrated
sensing and communication: Challenges and future directions,” IEEE
Commun. Mag., vol. 61, no. 5, pp. 62–67, May 2023.
[2] X. Yuan, T. Yang, Y . Hu, J. Xu, and A. Schmeink, “Trajectory
design for UA V-enabled multiuser wireless power transfer with nonlinear
energy harvesting,” IEEE Trans. Wireless Commun., vol. 20, no. 2,
pp. 1105–1121, Feb. 2021.
[3] N. Cheng et al., “AI for UA V-assisted IoT applications: A comprehensive
review,” IEEE Internet Things J., vol. 10, no. 16, pp. 14438–14461,
Aug. 2023.
[4] Q. Xiao, Y . Li, F. Luo, and H. Liu, “Analysis and assessment of risks to
public safety from unmanned aerial vehicles using fault tree analysis and
Bayesian network,” Technol. Soc., vol. 73, May 2023, Art. no. 102229.
[5] D. Mu, C. Yue, and A. Chen, “Are we working on the safety of
UA Vs? An LDA-based study of UA V safety technology trends,” Saf.
Sci., vol. 152, Aug. 2022, Art. no. 105767.
[6] J. Yousaf et al., “Drone and controller detection and localization: Trends
and challenges,” Appl. Sci., vol. 12, no. 24, p. 12612, Dec. 2022.
[7] C. Wang, J. Tian, J. Cao, and X. Wang, “Deep learning-based UA V
detection in pulse-Doppler radar,” IEEE Trans. Geosci. Remote Sens.,
vol. 60, 2022, Art. no. 5105612.
[8] H. Xu, Y . Quan, X. Zhou, H. Chen, and T. J. Cui, “A novel approach for
radar passive jamming based on multiphase coding rapid modulation,”
IEEE Trans. Geosci. Remote Sens., vol. 61, 2023, Art. no. 5101614.
[9] H. Yang, J. Yang, and Z. Liu, “Localizing ground-based pulse emitters
via synthetic aperture radar: Model and method,” IEEE Trans. Geosci.
Remote Sens., vol. 61, 2023, Art. no. 5216714.
[10] F.-L. Chiper, A. Martian, C. Vladeanu, I. Marghescu, R. Craciunescu,
and O. Fratu, “Drone detection and defense systems: Survey and a
software-deﬁned radio-based solution,” Sensors, vol. 22, no. 4, p. 1453,
Feb. 2022.
[11] J. Zhao, J. Zhang, D. Li, and D. Wang, “Vision-based anti-UA V detec-
tion and tracking,” IEEE Trans. Intell. Transp. Syst., vol. 23, no. 12,
pp. 25323–25334, Dec. 2022.
[12] S. Basak, S. Rajendran, S. Pollin, and B. Scheers, “Combined RF-based
drone detection and classiﬁcation,” IEEE Trans. Cognit. Commun. Netw.,
vol. 8, no. 1, pp. 111–120, Mar. 2022.
[13] W. Wang, K. Fan, Q. Ouyang, and Y . Yuan, “Acoustic UA V detection
method based on blind source separation framework,” Appl. Acoust.,
vol. 200, Nov. 2022, Art. no. 109057.
[14] C. R. Berger, B. Demissie, J. Heckenbach, P. Willett, and S. Zhou,
“Signal processing for passive radar using OFDM waveforms,” IEEE
J. Sel. Topics Signal Process., vol. 4, no. 1, pp. 226–238, Feb. 2010.
[15] D. Pastina, F. Santi, F. Pieralice, M. Antoniou, and M. Cherni-
akov, “Passive radar imaging of ship targets with GNSS signals
of opportunity,” IEEE Trans. Geosci. Remote Sens., vol. 59, no. 3,
pp. 2627–2642, Mar. 2021.
[16] P. Samczynski et al., “5G network-based passive radar,” IEEE Trans.
Geosci. Remote Sens., vol. 60, 2022, Art. no. 5108209.
[17] A. Aldowesh, T. Alnuaim, and A. Alzogaiby, “Slow-moving micro-UA V
detection with a small scale digital array radar,” in Proc. IEEE Radar
Conf. (RadarConf), Apr. 2019, pp. 1–5.
[18] J. L. Garry, C. J. Baker, and G. E. Smith, “Evaluation of direct signal
suppression for passive radar,” IEEE Trans. Geosci. Remote Sens.,
vol. 55, no. 7, pp. 3786–3799, Jul. 2017.
[19] I. Milani, C. Bongioanni, F. Colone, and P. Lombardo, “Fusing mea-
surements from Wi-Fi emission-based and passive radar sensors for
short-range surveillance,” Remote Sens., vol. 13, no. 18, p. 3556, Sep.
2021.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

BAI et al.: PASSIVE UA V DETECTION BASED ON CHANNEL ESTIMATION AND TEMPORAL V ARIATION NETWORK 14365
[20] Q. He, E. Yang, and S. Fang, “A survey on human proﬁle information
inference via wireless signals,” IEEE Commun. Surveys Tuts., vol. 26,
no. 4, pp. 2577–2610, 4th Quart., 2024.
[21] Z. Li and X. Rao, “Toward long-term effective and robust device-free
indoor localization via channel state information,” IEEE Internet Things
J., vol. 9, no. 5, pp. 3599–3611, Mar. 2022.
[22] D. Xie, J. Yi, J. Shen, and X. Wan, “Experimental research of multi-FM
based passive radar,” in Proc. 12th Int. Symp. Antennas, Propag. EM
Theory (ISAPE), Dec. 2018, pp. 1–5.
[23] V . V . Ratnam, H. Chen, H.-H. Chang, A. Sehgal, and J. Zhang, “Optimal
preprocessing of WiFi CSI for sensing applications,” IEEE Trans.
Wireless Commun., vol. 23, no. 9, pp. 10820–10833, Sep. 2024.
[24] W. Meng, Z. Liu, B. Li, W. Cui, J. T. Zhou, and L. Zhang, “GrapHAR:
A lightweight human activity recognition model by exploring the sub-
carrier correlations,” IEEE Trans. Wireless Commun., vol. 23, no. 4,
pp. 2755–2770, Apr. 2024.
[25] W. Li, M. J. Bocus, C. Tang, R. J. Piechocki, K. Woodbridge, and
K. Chetty, “On CSI and passive Wi-Fi radar for opportunistic physical
activity recognition,” IEEE Trans. Wireless Commun., vol. 21, no. 1,
pp. 607–620, Jan. 2022.
[26] W. Li, X. Meng, Z. Zhao, Z. Liu, C. Chen, and H. Wang, “LoT:
A transformer-based approach based on channel state information for
indoor localization,” IEEE Sensors J., vol. 23, no. 22, pp. 28205–28219,
Nov. 2023.
[27] H. B. Tulay and C. E. Koksal, “Road state inference via channel state
information,” IEEE Trans. Veh. Technol., vol. 72, no. 7, pp. 8329–8341,
Jul. 2023.
[28] S. Hochreiter and J. Schmidhuber, “Long short-term memory,” Neural
Comput., vol. 9, no. 8, pp. 1735–1780, Nov. 1997.
[29] G. Lai, W.-C. Chang, Y . Yang, and H. Liu, “Modeling long-and short-
term temporal patterns with deep neural networks,” in Proc. Int. ACM
Conf. Res. Devel. Inf. Retrieval (SIGIR), 2018, pp. 95–104.
[30] D. Campos, M. Zhang, B. Yang, T. Kieu, C. Guo, and C. S. Jensen,
“LightTS: Lightweight time series classiﬁcation with adaptive ensemble
distillation,” Proc. ACM Manage. Data, vol. 1, no. 2, pp. 1–27, Jun.
2023.
[31] S. Bai, J. Zico Kolter, and V . Koltun, “An empirical evaluation of generic
convolutional and recurrent networks for sequence modeling,” 2018,
arXiv:1803.01271.
[32] H. Wang, J. Peng, F. Huang, J. Wang, J. Chen, and Y . Xiao, “MICN:
Multi-scale local and global context modeling for long-term series
forecasting,” in Proc. Int. Conf. Learn. Represent. (ICLR), Kigali,
Rwanda, May 2023, pp. 1–5.
[33] D. Luo and X. Wang, “ModernTCN: A modern pure convolution
structure for general time series analysis,” in Proc. Int. Conf. Learn.
Represent. (ICLR), Vienna, Austria, May 2024, pp. 1–5.
[34] H. Wu, T. Hu, Y . Liu, H. Zhou, J. Wang, and M. Long, “TimesNet:
Temporal 2D-variation modeling for general time series analysis,” in
Proc. Int. Conf. Learn. Represent. (ICLR), Kigali, Rwanda, May 2023,
pp. 1–5.
[35] Y . Nie, N. H. Nguyen, P. Sinthong, and J. Kalagnanam, “A time series is
worth 64 words: Long-term forecasting with transformers,” in Proc. Int.
Conf. Learn. Represent. (ICLR), Kigali, Rwanda, May 2023, pp. 1–5.
[36] H. Wu, J. Xu, J. Wang, and M. Long, “AutoFormer: Decomposition
transformers with auto-correlation for long-term series forecasting,” in
Proc. NIPS, vol. 34, Dec. 2021, pp. 22419–22430.
[37] G. Zerveas, S. Jayaraman, D. Patel, A. Bhamidipaty, and C. Eickhoff, “A
transformer-based framework for multivariate time series representation
learning,” in Proc. 27th ACM SIGKDD Conf. Knowl. Discovery Data
Mining, Aug. 2021, pp. 2114–2124.
[38] W. Wang et al., “CrossFormer: A versatile vision transformer hinging
on cross-scale attention,” in Proc. Int. Conf. Learn. Represent. (ICLR),
Apr. 2022, pp. 1–5.
[39] Y . Liu et al., “iTransformer: Inverted transformers are effective for time
series forecasting,” in Proc. Int. Conf. Learn. Represent. (ICLR), Vienna,
Austria, May 2024, pp. 1–5.
[40] J. Bai et al., “A multiscale discriminative attack method for automatic
modulation classiﬁcation,” IEEE Trans. Inf. Forensics Security, vol. 20,
pp. 294–308, 2025.
[41] Z. Xiao, Y . Zhang, T. Li, J. Bai, S. Zhou, and Y . Zhang, “Parameter
estimation for adaptive impulsive noise suppression: A deep learning-
based memoryless nonlinearity approach,” IEEE Trans. Broadcast.,
vol. 71, no. 2, pp. 641–652, Jun. 2025.
[42] Z. Xiao, X. Jiang, T. Li, T. Li, Y . Zhang, and S. Zhou, “Compound
interference recognition for GNSS via integrating time–frequency with
power spectrum features,” IEEE Trans. Aerosp. Electron. Syst., vol. 61,
no. 5, pp. 13010–13021, Oct. 2025.
[43] Y . Wang et al., “AutoSMC: An automated machine learning framework
for signal modulation classiﬁcation,” IEEE Trans. Inf. Forensics Secu-
rity, vol. 19, pp. 6225–6236, 2024.
[44] J. Bai et al., “An interpretable explanation approach for signal mod-
ulation classiﬁcation,” IEEE Trans. Instrum. Meas., vol. 73, pp. 1–13,
2024.
[45] Y . Wang, J. Bai, Z. Xiao, H. Zhou, and L. Jiao, “MsmcNet: A modular
few-shot learning framework for signal modulation classiﬁcation,” IEEE
Trans. Signal Process., vol. 70, pp. 3789–3801, 2022.
[46] Z. Xiao et al., “Robustness-enhanced narrowband interference detection
by utilizing unlabeled data,” IEEE Trans. Wireless Commun., vol. 25,
pp. 8645–8659, 2026.
[47] Y . Zhou, H. Huang, S. Yuan, H. Zou, L. Xie, and J. Yang, “MetaFi++:
WiFi-enabled transformer-based human pose estimation for meta-
verse avatar simulation,” IEEE Internet Things J., vol. 10, no. 16,
pp. 14128–14136, Aug. 2023.
[48] F. Luo, S. Khan, B. Jiang, and K. Wu, “Vision transformers for
human activity recognition using WiFi channel state information,” IEEE
Internet Things J., vol. 11, no. 17, pp. 28111–28122, Sep. 2024.
[49] B. Li, W. Cui, W. Wang, L. Zhang, Z. Chen, and M. Wu, “Two-stream
convolution augmented transformer for human activity recognition,” in
Proc. AAAI Conf. Artif. Intell., vol. 35, no. 1, 2021, pp. 286–293.
Jing Bai (Senior Member, IEEE) received the B.S.
degree in electronic and information engineering
from Zhengzhou University, Zhengzhou, China, in
2004, and the Ph.D. degree in pattern recogni-
tion and intelligent systems from Xidian University,
Xi’an, China, in 2009. She is currently a Profes-
sor with Xidian University. Her research interests
include image processing, machine learning, and
intelligent information processing.
Zhuo Zhang received the B.S. degree in intelli-
gent science and technology from Xidian University,
Xi’an, China, in 2023, where he is currently pursuing
the M.S. degree in computer science and technology
with the Key Laboratory of Intelligent Perception
and Image Understanding of the Ministry of Educa-
tion. His research interests include machine learning
and intelligent signal processing.
Zhu Xiao (Senior Member, IEEE) received the M.S.
and Ph.D. degrees in communication and informa-
tion systems from Xidian University, Xi’an, China,
in 2007 and 2009, respectively. From 2010 to 2012,
he was a Research Fellow with the Department of
Computer Science and Technology, University of
Bedfordshire, Luton, U.K. He is currently a Full
Professor with the College of Computer Science and
Electronic Engineering, Hunan University, Chang-
sha, China. His research interests include mobile
computing, intelligent information processing, and
artiﬁcial intelligence.
Huaji Zhou was born in Jinhua, Zhejiang, China, in
1988. He received the M.S. degree in pattern recog-
nition and intelligent system and the Ph.D. degree in
electronic and information from Xidian University,
Xi’an, China, in 2013 and 2023, respectively. He is
currently an Associate Researcher with the National
Key Laboratory of Electromagnetic Space Secu-
rity, Jiaxing, China. His current research interests
include machine learning and electromagnetic signal
processing.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

14366 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Yongqiang Hei received the B.E. and Ph.D. degrees
in telecommunication engineering from Xidian Uni-
versity, Xi’an, China, in 2006 and 2010, respectively.
He is currently a Professor with the State Key
Laboratory of Integrated Services Networks, Xidian
University. His research interests include 5G/6G
communication, massive MIMO, green communica-
tion, and intelligent communication.
Xiaohui Liu received the Ph.D. degree in infor-
mation and communication engineering from the
National University of Defense Technology, Chang-
sha, China, in 2013. She is currently a Professor
with the National University of Defense Technology.
Her main research interests include signal processing
technology, multi-source fusion navigation technol-
ogy, and quantum navigation theory and technology.
Tong Li (Member, IEEE) received the B.S. and
M.S. degrees in communication engineering from
Hunan University, Changsha, China, in 2014 and
2017, respectively, and the Ph.D. degree in computer
science and engineering from The Hong Kong Uni-
versity of Science and Technology, Hong Kong, in
2021. He is currently a Professor with the College
of Computer Science and Electronic Engineering,
Hunan University. His research interests include
wireless network digital twins, network simulation
and optimization, and data-driven networking.
Licheng Jiao (Life Fellow, IEEE) received the B.S.
degree from Shanghai Jiao Tong University, Shang-
hai, China, in 1982, and the M.S. and Ph.D. degrees
from Xi’an Jiaotong University, Xi’an, China, in
1984 and 1990, respectively. Since 1992, he has
been a Professor with the School of Electronic Engi-
neering, Xidian University, Xi’an. He is currently
the Director of the Key Laboratory of Intelligent
Perception and Image Understanding of the Min-
istry of Education, International Research Center
of Intelligent Perception and Computation, Xidian
University. His research interests include intelligent information processing,
image processing, machine learning, and pattern recognition. He is a member
of the IEEE Xi’an Section Execution Committee; the President of the
Computational Intelligence Chapter, the IEEE Xi’an Section, and the IET
Xi’an Network; the Chairperson of the Awards and Recognition Committee;
the Vice Board Chairperson of Chinese Association of Artiﬁcial Intelligence;
a Councilor of Chinese Institute of Electronics; a Committee Member of
Chinese Committee of Neural Networks; and an Expert on the Academic
Degrees Committee of the State Council.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:07:48 UTC from IEEE Xplore.  Restrictions apply.
