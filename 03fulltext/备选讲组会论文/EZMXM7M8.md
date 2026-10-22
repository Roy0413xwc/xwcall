---
type: literature-fulltext
title: "UAV-Based Jamming Detection for Large Language Model-Enabled Wireless Networks"
zotero_key: "EZMXM7M8"
pdf_key: "A3KMJC5R"
doi: "10.1109/TCOMM.2026.3669447"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/UAV-Based Jamming Detection for Large Language Model-Enabled Wireless Networks.md"
fulltext_path: "03fulltext/备选讲组会论文/EZMXM7M8.md"
zotero_item: "zotero://select/library/items/EZMXM7M8"
zotero_pdf: "zotero://open-pdf/library/items/A3KMJC5R"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# UAV-Based Jamming Detection for Large Language Model-Enabled Wireless Networks

> PDF 原文逐页文本抽取；来源文件 SHA-256：`5345b40f3995458da80dffd8454fb13d739c0ee1984bdcdeee33fed7b1a27245`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026 5833
UA V-Based Jamming Detection for Large Language
Model-Enabled Wireless Networks
Qiaoxin Chen
 , Graduate Student Member , IEEE , Liang Xiao
 , Fellow, IEEE,
Pengcheng Wang
 , Graduate Student Member , IEEE , Jieling Li
 , Graduate Student Member , IEEE ,
Haoyu Chen
 , Graduate Student Member , IEEE , Hongbin Jin, and Ying-Jun Angela Zhang
 , Fellow, IEEE
Abstract—Reinforcement learning (RL) has been used for
uncrewed aerial vehicle (UA V)-based jamming detection by select-
ing hypothesis-test thresholds on received signal strength (RSS)
to safeguard large language model (LLM) inference over wireless
links. However, existing methods struggle against smart jammers
with dynamic jamming probability. In this paper, we propose a
UA V-based jamming detection scheme for LLM-enabled wire-
less networks to detect smart jamming. The proposed scheme
augments traditional wireless features with an LLM-inferred
communication environment indicator derived from multimodal
sensing (e.g., images/videos from mobile devices), improving
accuracy beyond RSS alone. Our approach jointly optimizes the
test threshold and the UA V’s sniffer channel assignment, even
with a limited number of antennas. We achieve this via a RL
policy that leverages UA V imagery, e.g., suspicious radio devices
and measuring relative distances, to accelerate detection speed.
We implement the proposed scheme on a UA V equipped with a
universal software radio peripheral to alert on jamming attacks
in a wireless network integrated with a 7-billion-parameter
vision-language multimodal LLM. Experiments with a UA V at
3 m detecting a smart jammer during image–text LLM inference
across three mobile devices and an edge server demonstrate
improvements in both detection accuracy and speed.
Index Terms—Uncrewed aerial vehicles, jamming detection,
large language model, reinforcement learning.
I. I NTRODUCTION
L
ARGE language models (LLMs) deployed on edge
servers near mobile devices complement cloud-based
inference by enabling latency-sensitive applications such as
real-time natural language assistance [2]. However, wireless
Received 3 November 2025; revised 28 January 2026; accepted 22 February
2026. Date of publication 2 March 2026; date of current version 11 March
2026. This work was supported in part by the National Natural Science
Foundation of China under Grant U25A20388, the Fundamental Research
Funds for the Central Universities under Grant 20720250036, and the
National Key Research and Development Program of China under Grant
2023YFB3107603. An earlier version of this paper was presented in part at
the 2025 IEEE ICC [DOI: 10.1109/ICC52391.2025.11161897]. The associate
editor coordinating the review of this article and approving it for publication
was B. Makki. (Corresponding author: Liang Xiao.)
Qiaoxin Chen, Liang Xiao, Pengcheng Wang, and Jieling Li are with
the Department of Informatics and Communication Engineering, Xiamen
University, Xiamen 361005, China (e-mail: lxiao@xmu.edu.cn).
Haoyu Chen is with the Institute of Artiﬁcial Intelligence, Xiamen
University, Xiamen 361005, China.
Hongbin Jin is with Sichuan Postdoctoral Practice Innovation Base [China
Mobile (Chengdu) Industrial Research Institute], Chengdu 610213, China
(e-mail: jinhongbin@cmii.chinamobile.com).
Ying-Jun Angela Zhang is with the Department of Information Engineering,
The Chinese University of Hong Kong, Hong Kong, China (e-mail:
yjzhang@ie.cuhk.edu.hk).
Digital Object Identiﬁer 10.1109/TCOMM.2026.3669447
links that carry prompts and multimodal inputs remain vulner-
able to jamming, which can corrupt critical tokens or images
and induce inference failures or hallucinations [3]. Detecting
jamming in LLM-enabled wireless networks is challenging
because such networks serve spatially distributed and het-
erogeneous users in three-dimensional space [4], including
connected autonomous vehicles and uncrewed aerial vehicles
(UA Vs). Conventional terrestrial detection systems struggle to
monitor such networks comprehensively due to shadowing and
limited sensing ranges. UA Vs provide a promising complement
thanks to their ﬂexible deployment and high line-of-sight
(LoS) probability [5].
Jamming detection relies on features from both the phys-
ical layer and the network layer such as received signal
strength (RSS) [6], [7], [8], packet delivery delay (PDD)
[9], packet delivery ratio (PDR) [10], and principal reference
signal direction [11]. Classic schemes train classiﬁers or
set thresholds on RSS or cross-layer metrics to distinguish
jammed from congested or faded conditions. For instance, [7]
employs a machine learning classiﬁer to evaluate the ﬂuctua-
tion range of the RSS compared with a threshold established
under static radio channel states. However, its performance
degrades for UA Vs due to long-range measurement noise,
especially against smart jammers that adapt their attack strate-
gies to mimic legitimate fading and poor links. Such adaptive
attacks confound threshold-based classiﬁers, which struggle
to distinguish normal congestion from deliberate jamming
[6].
Reinforcement learning (RL) has been used to adapt detec-
tion parameters, such as test thresholds, based on radio
frequency (RF) features and observed communication perfor-
mance metrics to improve detection accuracy. For example,
the RLJD scheme in [12] utilizes Q-learning to optimize
the test threshold based on the estimated signal energy
and packet loss rate. However, the detection performance
is hindered by incomplete observation of unknown radio
sources such as measurement distance [13]. Incorporating
environmental information from UA V imagery and additional
LLM inference helps identify radio device categories and
locations, as well as the building layouts and density. These
insights improve LoS/NLoS discrimination in radio frequency
measurements [14], thereby enhancing jamming detection
accuracy. The LLM serves both as the protected application
and the contributor to jamming detection, leveraging existing
sensing data from legitimate users with negligible resource
overhead.
0090-6778 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

5834 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Apart from threshold optimization, sniffer channel assign-
ment that directly affects jamming feature collection is also
critical for countering smart jammers [15], [16], [17]. In
LLM-enabled wireless networks operating over contiguous or
non-contiguous channels/bands [18], simultaneous full-band
channel detection via antenna-constrained UA Vs inevitably
results in undesirable channel switching delay and even jam-
ming feature loss, degrading the jamming detection speed
and accuracy. For instance, retuning the central frequency of
GNU Radio-based spectrum analyzer can introduce hundreds
of milliseconds delay [15].
In this paper, we propose a UA V-based jamming detection
scheme for LLM-enabled wireless networks. The proposed
scheme uses RL to jointly optimize sniffer channel assignment
and the test threshold, leveraging multimodal sensor data to
improve both detection accuracy and latency. Speciﬁcally, we
use a one-class support vector machine (OC-SVM) classiﬁer
to evaluate joint variations in multiple features. These features
include the RSS measured at the UA V , various network perfor-
mance metrics such as PDD, PDR, bit error rate (BER), and an
environmental indicator, e.g., likelihood of signal obstruction
by buildings, inferred by the LLM. The classiﬁer outputs a
jamming score, which is compared against the learned test
threshold to detect jamming attacks. Notably, our scheme can
be applied to other wireless systems, such as wireless sen-
sor networks, with reduced performance when LLM-inferred
information is unavailable.
UA V imagery-derived information (e.g., object classes and
UA V-object distances) acquired through lightweight computer
vision techniques is incorporated into the state representation
to discriminate between legitimate fading and covert jamming
attacks, thereby reducing the false alarm rate. To mitigate the
performance degradation caused by RSS measurement error at
the UA V , e.g., body vibrations and long-range measurements,
we maintain a sliding window of detection outputs and apply
an exponentially weighted moving average (EWMA) to assess
detection policy risk, reducing miss detections and unneces-
sary channel switching. Speciﬁcally, the policy distribution
combines a long-term utility that captures detection effec-
tiveness with a short-term miss-detection risk, accelerating
detection policy exploration.
We further employ a sequential classiﬁer, long short-term
memory (LSTM), to capture covert jamming attacks by the
temporal dependency of ﬁne-grained time-series features. As
the state space grows with the number of detected object
classes, we adopt deep RL with neural networks to estimate
the long-term rewards and risk values for the policy selection.
This deep RL design also mitigates quantization error in
UA V imagery-derived information for faster learning speed
and higher detection performance.
We derive a performance bound via a detection game
between a UA V and a smart jammer. In this game, the UA V
chooses both the sniffer channel assignment and test threshold
to maximize detection accuracy while minimizing delay. The
performance bound, derived by analyzing the Nash Equilib-
rium (NE) of the game for a given unit attack payoff parameter,
decreases with the sensing area of multimodal sensors, such as
the hovering height of a UA V . The computational complexity
of the proposed detection schemes mainly increases with the
scale of the monitored wireless network.
We implement a jamming detection system consisting of a
UA V equipped with a HackRF One that is controlled by a
Raspberry Pi, and a control center with a PyQt-based graph-
ical user interface (GUI) for real-time display of detection
outcomes. We conduct simulations using collected channel
states from diverse wireless scenarios and jammer–UA V links
to demonstrate that our schemes outperform JADE [7] and
RLJD [12] in both detection accuracy and reduced latency. We
observe a consistent decline in average detection performance
as UA V hovering height increases.
For real-world evaluation, we also conduct experiments
using the UA V-based jamming detection system to detect a
smart jammer, which is a universal software radio peripheral
(USRP) N210 controlled by a laptop to send Gaussian signals
with dynamic jamming probability, within an outdoor wireless
network. The network comprises three connected and auto-
mated vehicles (CA Vs) and a control center integrated with
LLaV A, a 7-billion-parameter vision-language LLM. Experi-
mental results show that our proposed scheme reduces 96.8%
false alarm rate, 90.4% miss detection rate and 12.6% delay
compared with the benchmarks.
The main contributions are summarized as follows:
1) We propose an environment-aware UA V-based jamming
detection scheme to optimize both the sniffer channel
assignment and the test threshold, enhancing the detec-
tion accuracy and speed, particularly in LLM-enabled
wireless networks facing smart jammers.
2) We introduce a deep-learning version that further
enhances the detection efﬁciency for UA Vs with higher
onboard computational capability. It employs a sequen-
tial classiﬁer to process ﬁne-grained time-series features,
and uses neural networks to compress the state space,
mitigating imagery-information quantization errors and
improving learning efﬁciency.
3) We derive performance upper bounds of detection accu-
racy and delay by analyzing the NE of a jamming
detection game between a UA V and a smart jammer.
Both simulations with collected data and experiments
conducted using our implemented system demonstrate
the performance gains over benchmark methods.
The rest of this paper is organized as follows. We review
the related work in Section II and formulate the system
model in Section III. We propose a UA V-based jamming
detection scheme in Section IV and a deep-learning version in
Section V. Section VI provides performance analysis.
Section VII presents the system implementation, followed
by simulation results using real data in Section VIII and
experimental results in Section IX. Section X concludes the
paper.
II. R ELATED WORK
Existing jamming detection schemes rely on statistical
hypothesis testing to evaluate features from both the physical
and network layers to identify jamming activity [6], [8], [9],
[10], [11], [19], [20], [22]. Table I summarizes the comparison
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

CHEN et al.: UA V-BASED JAMMING DETECTION FOR LLM-ENABLED WIRELESS NETWORKS 5835
TABLE I
SUMMARY OF JAMMING DETECTION SCHEMES FOR WIRELESS NETWORKS
of existing jamming detection schemes based on differences in
technique, detection location, and input features. For instance,
the scheme in [9] identiﬁes a phase transition phenomenon
for time-critical packet delivery under jamming and detects
attackers by comparing packet delivery delay against a test
threshold. The scheme that detects reactive jamming in [10]
evaluates an empirical model based on the chip error rate of
the direct-sequence spread spectrum and infers jamming by
contrasting the estimated packet delivery ratio of jamming-
free preamble symbols. In [11], the detector exploits principal
reference signal direction in the channel demodulation space to
detect jamming attacks, without relying on prior jammer infor-
mation. The detection method in [20] uses preset thresholds
of BER to evaluate the power level of symbol-level jamming,
assessing the threat to legitimate users. However, most of
these schemes depend on prior knowledge of jamming attack
patterns, which may not be available for UA Vs operating in
time-varying radio environments.
Learning-based jamming detection employs data-driven
approaches without predeﬁned jammer models to enhance
detection ﬂexibility and adaptability [1], [7], [12], [21]. For
instance, the Bayesian network-based scheme in [21] evaluates
cross-layer features such as channel quality indicator and
trafﬁc pattern to infer jamming. However, under a constant
threshold, detection accuracy against smart jammers degrades
because multipath and shadowing effects blur the distinction
between faded legitimate signals and jamming signals.
As a typical deployment, sensor networks collect signals
from distributed RF sensors or legitimate users and per-
form joint jamming detection or jammer localization at a
central node [8], [23], [24]. For example, the mix source
separation–based scheme in [8] separates jamming temporal
proﬁles from RSS estimates of multiple nodes and applies
causal inference to detect reactive jamming. The cooperative
jamming detection scheme in [23] organizes signals from
sensing nodes into a received signal matrix and exploits its
low-rank structure through a likelihood ratio test to detect
deceptive jamming. Moreover, the jammer localization scheme
in [24] aggregates jamming signal strengths from sensors, con-
structs a signal strength map via Gaussian process regression,
and estimates the jammer location by minimizing the error
between predicted and measured signals. However, shadowing
effects and limited sensing ranges signiﬁcantly degrade the
detection and localization accuracy of these schemes.
UA Vs have emerged as effective RF signal sampling sup-
plementary platforms offering both aerial vision and high
line-of-sight probability, thereby mitigating blind spots caused
by building occlusions and shadowing fading [1], [13], [14],
[25], [26], [27]. For instance, the detection strategy in [13]
identiﬁes stealthy jamming identiﬁcation through sustained
UA V observation, utilizing a sliding window to extract the
logarithmic energy sequence from received signals and a
hidden Markov model to classify them as jammed and standard
categories. The jamming detection scheme in [25] converts
the physical layer information obtained from UA Vs under a
low bit error rate into grey-scale images and deploys a sparse
auto-encoder to detect jamming-induced anomalies. The aerial
radio environment map in [14] utilizes UA V imagery to infer
building heights and device locations, estimate LoS/NLoS
probabilities, and optimize RF measurement trajectories to
improve mapping accuracy.
Monitoring a wireless network with a limited number of
sniffers (detectors) while reducing channel switching costs
such as delay and energy consumption has been recognized
as an important research area [15], [17], [28], [29], [30]. For
example, the sniffer channel assignment with switching costs
for the wireless network is formulated as a linear partial multi-
armed bandit monitoring problem in [15], which proposes
an upper conﬁdent bound policy to learn user activities and
make channel assignment decisions sequentially. Similarly,
[28] models misuse spectrum monitoring as an adversarial
multi-armed bandit, selecting monitoring-channel strategies
based on detection history and repeating the same strategy
for speciﬁc time slots to reduce switching costs. An RL-based
jamming detection scheme in [30] considers the switching cost
due to the duration of channel switching and jointly optimizes
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

5836 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 1. Illustration of the UA V-based jamming detection for the LLM-enabled
wireless network, in which each AP is wired to a server providing LLM
inference for the intended users.
channel selection and transmission modes of full-duplex nodes
against the reactive jamming, improving network throughput.
LLMs with powerful representational and learning capa-
bilities are emerging in wireless networks for tasks such
as channel prediction and communication policy optimiza-
tion, with support for edge inference [2], [31], [32], [33].
For example, the edge inference scheme in [2] enables
LLM access over wireless edge networks and enhances
throughput by jointly optimizing batching, model quantization,
and communication–computation resources. The channel-
associated multi-task learning scheme in [32] leverages a
ﬁne-tuned LLM to jointly model tasks such as channel esti-
mation, prediction, and localization, improving performance
via shared representations and transfer learning. The near-ﬁeld
communication scheme in [33] leverages a ﬁne-tuned LLM as
an optimization solver to jointly optimize precoding and power
allocation, thereby enhancing spectrum efﬁciency.
In our prior work [1], we proposed an RL-based mul-
timodal jamming detection scheme for a UA V swarm to
optimize test threshold based on visual features, RSS, and
communication performance metrics, improving the accuracy
of single-channel monitoring through result sharing. In this
paper, we extend the prior work to an LLM-enabled wireless
network, where the spatial distribution of heterogeneous users
can degrade detection performance [4]. Thus, we leverage the
LLM as a contributor to jamming detection by utilizing com-
munication environment indicators inferred from multimodal
sensing data captured by mobile devices in the area, and jointly
optimize sniffer channel assignment and threshold selection to
enhance detection accuracy while reducing delay.
III. S YSTEM MODEL
A. Network Model
As shown in Fig. 1, a UA V equipped with a camera and
RF sensors passively monitors a wireless network comprising
N access points (APs), indexed by N ={1, 2,··· ,N}, each
connected to a server via a wired link. Similar to [2], [15],
and [31], we assume that each user m∈M ={1, 2,··· ,M}
simultaneously transmits an LLM inference request to the
intended AP via FDMA with negligible interference, but
suffers interruptions from jamming attacks. Due to hardware
constraints, e.g., a limited number of antennas, the UA V can
TABLE II
SUMMARY OF KEY SYMBOLS AND NOTATIONS
monitor only one channel at a time, but can switch between
channels over time to cover multiple links.
At time slot k, the AP n∈N located at l(k)n receives up
to Jn request packets from the serving user m∈M at ˆl(k)m
that transmits with power p(k)m on one of the H orthogonal
channels. These packets contain the LLM service type, the
inference prompt, and user-captured sensory data, such as
images and videos, as inputs to the LLM. Upon receiving
packets, the AP n estimates the channel state g(k)m,n via pilot
measurements and evaluates the wireless network performance
metrics including the PDD series ρ(k)m,n = [ρ (k)1≤i≤Jn], the
PDR η(k)m,n and the BER χ(k)m,n through the timestamp checks
and cyclic redundancy checks. The environmental indicator
ϖ(k)m ∈{ 1, 2,··· ,L} can be derived by processing the multi-
modal sensor data and the preset inference prompts speciﬁc to
jamming detection. These indicators are independent of user
service requests, such as the likelihood of signal obstruction
by buildings as inferred by the RGB images. Each AP packs
the metrics into beacon frames and broadcasts through uni-
ﬁed control channels, which are captured by the UA V using
monitoring software, such as Wireshark.
Similar to [28], we partition a time slot into T sub-slots,
where T is set proportional to the number of APs N. At
time slot k, the UA V hovers at l(k) ∈ R3 and sequentially
measures T RSS series, δ(k)1≤t≤T . Each RSS series consists of
NS samples, i.e., δ(k)t = [δ(k)t,1≤i≤NS], which aggregate multi-
path components of the received signal based on the sniffer
channel assignment x(k) = [x(k)1≤i≤H], 0≤ x(k)i ≤ T . For
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

CHEN et al.: UA V-BASED JAMMING DETECTION FOR LLM-ENABLED WIRELESS NETWORKS 5837
example, at sub-slot t in time slot k, assuming that only the
user m is transmitting, the i-th measured RSS δ(k)t,i depends
on the transmit power of user p(k)m , the path loss PL (k)t,m, the
shadowing fading X (k)t,1 and the multi-path fading X (k)t,2 as
δ(k)t,i =p(k)m −PL (k)t,m +X (k)t,1 +X (k)t,2, (1)
where the path lossPL (k)t,m increases with the distance between
the user m and the UA V‖l(k)−ˆl(k)m‖. At the end of time slot
k, the UA V captures aerial RGB images of the area covered by
the RF sensors (e.g., Wi-Fi radius up to 250 m) and extracts
visual-geometric information on suspicious radio devices, i.e.,
object classes c(k) and UA V-object distancesd(k). Let r(k) =
[r(k)1≤i≤H] denote the detection result, where r(k)i = 1 indicates
the i-th channel is detected as jammed.
B. Jamming Model
The jammer located at l(k)J performs spectrum sensing to
monitor activity on the target channelh(k)J , and emits jamming
signals to corrupt critical prompts or images during LLM
requests, potentially causing inference failure or hallucina-
tions.
Speciﬁcally, the smart jammer degrades the SINR at the
target AP with a jamming probability y∈
[
Y,Y
]
via greedy
or RL schemes, thereby increasing the long-term fraction of
corrupted packets and reducing communication performance,
while remaining less detectable due to a lower average transmit
power [9], [34], [35]. Moreover, the smart jammer can generate
multiple jamming types as special cases, such as constant,
reactive [10] and protocol-aware jamming [29]. For example,
at y = 1 , the smart jammer generates constant or reactive
jamming depending on the availability of channel sensing,
while the protocol-aware jamming that only attacks the key
frames corresponds to an intermediate jamming probability.
According to [29], even with an error coding scheme such
as BCH, the jammer can make the application unreadable by
attacking 15% of the packets.
TABLE I summarizes key symbols and descriptions. Unless
otherwise stated, we omit the time index k and the indices of
AP n and paired user m when clear from context.
IV. E NVIRONMENT -AWARE UAV-BASED JAMMING
DETECTION
We propose an environment-aware UA V-based jamming
detection scheme, EUJD, for LLM-enabled wireless networks.
EUJD utilizes an OC-SVM-based classiﬁer to assess jamming
attacks using the multimodal sensor data, including average
RSS, wireless network performance metrics and an LLM-
inferred environmental indicator. We incorporate UA V imagery
into the RL state formulation to jointly optimize the test thresh-
old and the sniffer channel assignment, thereby improving
detection accuracy while minimizing delay. To guide explo-
ration, we combine a risk measure, an exponentially weighted
moving average of recent miss detections, with a long-term
utility that weights detection accuracy and delay. This yields
a Boltzmann policy distribution that enhances exploration
Algorithm 1 Environment-Aware UA V-Based Jamming Detec-
tion for LLM-Enabled-Wireless Networks
1: Initializes α, β, ψ, NA, NC, ι, ζ, f (0) = v(0) = 0, T ,
π(·,·) = 0,a(0) =[x(0),ξ (0)]
2: fork = 1, 2, 3,...,K do
3: Obtain the location l(k)
4: Capture the RGB image Z (k) and extract suspicious
object classes c(k) and UA V-object relative distances
d(k) via YOLOv5s
5: Formulates(k) via (4)
6: Inputs(k) to the top level of RL
7: Calculateπ(s(k),x(k)) via (5) and choose x(k)
8: fort = 1, 2, 3,...,T do
9: Measure RSS δ(k)
10: end for
11: Obtain channel states g(k), averaged PDDs ¯ρ(k), PDRs
η(k), BERs χ(k) and environmental indicators ϖ(k)
through decoding AP broadcast packets
12: Calculate ∆(k) = [∆(k)1≤h≤H] via (3)
13: Formulate ˆs(k) as the bottom level input
14: Calculateπ(ˆs(k),ξ (k)) via (5) and update ξ(k)
15: r(k) = 0H
16: fori = 1, 2, 3,··· ,H do
17: if ∆(k)i ≥ξ(k) then
18: r(k)i = 1
19: end if
20: end for
21: Update f (k), v(k), τ (k)
22: Calculate u(k) and e(k) via (6) and (7)
23: forj = 1, 2 do
24: Update Q and E values via (8) and (10)
25: end for
26: end for
efﬁciency in detection policy selection, as summarized in
Algorithm 1.
At time slot k, the UA V obtains its location l∈ R3 via
the global positioning system, captures an RGB image Z,
measures the RSS ¯δ = [¯δ1≤t≤T ] with each ¯δt averaged over
NS sampling batches at sub-slot t, i.e., ¯δt = ∑NSi=0δt,i/NS,
and decodes AP broadcasts to obtain the channel states
g = [g1≤i≤N], the averaged PDD ¯ρ = [¯ρ1≤i≤N] with each
¯ρi averaged over Ji packets, the BER χ = [χ 1≤i≤N] and
the environmental indicators derived from LLM inference
ϖ = [ϖ1≤i≤N]. The resulting feature vector is
o(k) =[l,g, ¯δ, ¯ρ,η,χ,ϖ], (2)
where all features are pre-processed appropriately before being
input to the classiﬁer. For example, we normalize the RSS and
communication performance metrics using min-max scaling,
following [21], and standardize the coordinates of UA V loca-
tion to zero mean and unit variance.
We train the jamming classiﬁer using the OC-SVM with a
radial basis function kernel to establish a hyperplane deﬁned
byNV support vectors. The communication performance met-
rics are set to null when the AP broadcast packets cannot
be decoded due to packet losses. In contrast to conventional
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

5838 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 2. Illustration of the environment-aware UA V-based jamming detection
scheme.
jamming classiﬁers that require labeled attack data [21], the
proposed scheme trains exclusively on mixed non-jamming
features from multiple channel observations through unsu-
pervised learning, thereby eliminating the need to annotate
jamming features. EUJD partitions the feature vector o(k) into
H channel-wise sub-vectors, o(k) = [ ˆo1, ˆo2,..., ˆoH], with
unmonitored channels zero-padded, to compute the jamming
scores ∆ = [∆ 1,..., ∆H]. Speciﬁcally, each ∆i represents
the deviation between ˆoi and the margin of the learned
hypersurface deﬁned by NV support vectors as follows
∆i =
NV∑
j=1
ιj exp
(
−κ‖˜oj− ˆoi‖2)−ζ, (3)
where ˜oj denotes the j-th support vector, ιj represents the
corresponding Lagrange multipliers,κ is the kernel bandwidth,
andζ is the bias term of the hyperplane. We perform a binary
hypothesis test to determine whether the channel is jammed
by comparing the jamming score with the test threshold ξ. If
∆i≤ξ, the classiﬁer outputs the i-th channel as normal, i.e.,
ri = 0, and the current detection feature vector o is recorded
for classiﬁer updates. Otherwise, it raises and broadcasts a
jamming alarm, i.e., ri = 1.
The state formulation incorporates the UA V imagery as
multi-dimensional feature indicators to mitigate detection per-
formance degradation caused by legitimate communication
ﬂuctuation in urban environments. Speciﬁcally, a lightweight
object detection (YOLOv5s; see Fig. 2) processes the imageZ
to estimate class probability c overNC target categories (e.g.,
USRP) and the corresponding minimum relative distances d,
yielding location information for potential malicious devices.
To reduce computational overhead, we quantize the suspicious
class probabilityc and relative distanced into ˆc and ˆd, respec-
tively. The current states(k) then combines the quantized class
probabilities ˆc and relative distances ˆd, the miss detection rate
v(k−1), the false alarm rate f (k−1), and the delay τ (k−1):
s(k) =[ˆc, ˆd,v (k−1),f (k−1),τ (k−1)]. (4)
The detection policy a(k) = [x,ξ ] consists of the sniffer
channel assignment for the next time slot x ={x1≤i≤H} and
the test threshold ξ for the jamming score-based hypothesis
testing. Speciﬁcally, we quantize the sampling time for the
i-th channel xi∈{m/T|0≤m≤T} into T levels with the
constraint∑Hi=1xi =T . Therefore, the total number of sniffer
channel assignments is Z1 =C H−1H+T−1. Similarly, we quantize
the test threshold ξ ∈
{
mξ/Z2|0≤m≤Z2− 1
}
into Z2
levels up to the maximum threshold ξ. Following [36], we
adopt a two-layer hierarchical RL indexed by j∈{ 1, 2} to
decompose the overall policy into two sub-policies. At the
top level (j = 1), given the initial state s(k), EUJD chooses
the sniffer allocation x using a Boltzmann policy distribution
π(s(k),x) computed from both the expected long-term reward
Q
(
s(k),x) and short-term risk E(s(k),x). At the bottom
level (j = 2), EUJD augments the state to ˆs(k) =[s(k),x] to
select the test threshold ξ based on π(ˆs(k),ξ ), i.e.,
π
(
˜s(k)j ,aj
)
=
exp
(
Q
(
˜s(k)j ,aj
)
1+E
(
˜s(k)j ,aj
)
)
∑
a′i∈Aj exp
(
Q
(
˜s(k)j ,a′j
)
1+E
(
˜s(k)j ,a′j
)
), (5)
where ˜s(k) = {s(k), ˆs(k)}. The risk value in the policy
distribution acts as a temperature parameter, modulating the
degree of random exploration in risky policies to enhance the
optimization efﬁciency of jamming detection. This distribution
increases the probability of selecting sniffer channel assign-
ments and test thresholds that achieve higher expected utility
and lower risk.
This scheme can verify the authenticity of detection results
through upper-layer checks, e.g., multi-dimensional diagnosis
by radio network engineers [7]. We utilize a sliding window
over the most recent NA time slots to assess the detection
accuracy, which is primarily inﬂuenced by sniffer channel
assignment and test threshold selection. Speciﬁcally, the false
alarm ratef is the fraction of legitimate transmissions mistak-
enly detected as jamming, and the miss detection rate v is the
fraction of jammed time slots that are incorrectly ignored. The
measured detection delay τ = τ0 +τ1 comprises a baseline
delay τ0 and a channel switching delay τ1. In particular, τ0
includes the total RSS sampling time across T sub-slots and
mandatory hardware initialization (e.g., clock synchroniza-
tion and local oscillator phase calibration) at new timeslot
boundaries. τ1 is determined by reconﬁguration duration for∑H
i=1 sgn (xi)−1 intra-slot channel switching events [15]. We
deﬁne the utility u to trade off delay and accuracy as
u(k) =−τ−w1v−w2 f, (6)
where the coefﬁcients 0<w 1 < 1 and 0<w 2 < 1 are preset
according to the sensing area of multimodal sensors. A high
f impedes sample collection and delays the necessary updates
to the jamming classiﬁer, hindering the adaptation of channel
time selectivity, while a high v misleads the classiﬁer update
and degrades detection performance.
Due to the wind-induced body vibrations and long-range
measurement, the RSS samples exhibit time-varying noise,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

CHEN et al.: UA V-BASED JAMMING DETECTION FOR LLM-ENABLED WIRELESS NETWORKS 5839
degrading accuracy even under a ﬁxed detection policy. To
mitigate detection errors arising from time-varying noise in
RSS samples, we introduce an exponentially weighted moving
average-based risk evaluation, especially in miss detections.
Let [ˆr(k−m)i ]1≤i≤H,0≤m≤NA denote the upper-layer feedback
of jamming results across H channels over the preceding NA
time slots. Then, we compute the detection policy risk e(k)
using a decay factor 0<λ< 1 as
e(k) =(1−λ)
NA−1∑
m=0
λm
H∑
i=1
max
(
0,
(
ˆr(k−m)i −r(k−m)i
))
, (7)
which is further incorporated into the Boltzmann policy distri-
bution as shown in (5). The risk value emphasizes recent miss
detections by assigning larger weights reﬂecting their higher
relevance.
Algorithm 2 Environment-Aware UA V-Based Jamming Detec-
tion With Deep Learning
1: Initializes NA, NC, NS, J,B, f (0) =v(0) = 0 , T , θ =
φ = 0,π(·,·) = 0,D = ∅,a(0) =[x(0),ξ (0)], I
2: fork = 1, 2, 3,...,K do
3: Same as Lines 3-11 in Algorithm 1
4: Calculate ˜∆(k) via (11)
5: Same as Lines 13-22 in Algorithm 1
6: D←D ⋃{s(k),a(k),u (k),e (k),s(k+1)}
7: Randomly sample the minibatch B fromD
8: forj = 1, 2 do
9: Updateθj andφj via (12)
10: end for
11: end for
The Bellman equation with distribution correction as pro-
posed in [37] updates the long-term expected values of
detection sub-policies Q
(
˜s(k)j ,a(k)1≤j≤2
)
as
Q
(
˜s(k)j ,a(k)j
)
←(1−αw(k)j )Q(˜s(k)j ,a(k)j )
+αw(k)j
(
u(k)+γ max
a′j
Q
(
˜s(k)j ,a′j
))
, (8)
where the learning rates α∈ (0, 1] and the discount factor
γ∈ [0, 1] represent the importance of the received utility of
the current test policy and the future utility in the following
learning process, respectively. We decrease the multiplierw(k)j
with the Bellman error and scale it by a temperature factor
ψ∈ (0, 1] as
w(k)j = exp
(
−ψ
⏐⏐⏐Q(˜s(k)j ,a(k)j )−u(k)−γ maxa′j Q(˜s(k)j ,a′j)⏐⏐⏐). (9)
Similarly, the risk values E
(
s(k),·) are the same for both
top and bottom levels, and are updated using the learning rate
β∈ (0, 1] and the risk e(k), i.e.,
E
(
˜s(k)j ,a(k)j
)
← (1−β)E
(
˜s(k)j ,a(k)j
)
+βe(k). (10)
V. E NVIRONMENT -AWARE UAV-BASED JAMMING
DETECTION WITH DEEP LEARNING
We further propose a deep-learning version, named DEUJD,
which enhances sniffer channel assignment efﬁciency and jam-
ming detection accuracy for UA Vs with higher computational
capability. This scheme leverages a sequential classiﬁer to
process ﬁne-grained time-series features, such as raw RSS
samples, to detect the temporal dependencies of covert jam-
ming attacks. Neural networks compress the high-dimensional
state space induced by multiple sensitive objects and snif-
fer channels, and mitigate image-feature quantization errors,
thereby enhancing detection performance.
Following Algorithm 1, the UA V evaluates the feature vector
similar to (2) without time averaging, including the RSS series
δ∈ RNL×T and the PDD series ρ∈ RNL×T , normalized and
temporally aligned by timestamps, so that NL = max(NS,J ).
The reason is that the average feature may mask variations in
the received signal and thus fails to detect a smart jammer with
low jamming probability, since different feature distributions
can yield the same mean. For example, a jamming signal with
half its RSS samples at 5 and half at 15 averages the same
as a legitimate one with all samples at 10. The sequence
is then equally split into a preﬁx ´o and a sufﬁx `o. An
LSTM time-series classiﬁer consumes the preﬁx to produce
a sequential prediction vector ˘o, which is compared against
the sufﬁx to detect ﬂeeting jamming events. Note that this
module can be replaced by an auto-encoder [21] or a quantized
large language model without UA V computational capability
constraints. Thus, we rewrite the jamming score for the i-th
channel clariﬁed in (3) as the cross entropy loss between ˆoi
and `oi as follows
˜∆i =−
NL/2∑
j=1
`oi,j log (˘oi,j). (11)
DEUJD formulates the current state according to (4) with-
out quantization, i.e., s(k) = [c,d,v (k−1),f (k−1),τ (k−1)].
This scheme then inputs s(k) into both the Q-network Q
and E-network E to estimate the expected long-term utility
Q(s(k),·;θ1) and the risk value E(s(k),·;φ1), respectively.
The Q and E networks share the same architecture, consisting
of an input fully connected (FC) layer with Ω1 = 2NC + 3
neurons, where NC denotes the number of suspicious object
classes, followed by two hidden FC layers with g1,1 and g2,1
neurons, and an output layer of Z1 neurons corresponding to
feasible sniffer channel assignments.
Likewise, the inputs of the bottom layer consist of Ω2 =
Ω1 + 1 neurons corresponding to the augmented state ˆs(k) =[
s(k),x]. DEUJD selects test threshold ξ based on an output
layer with Z2 neurons, each indexing a candidate threshold.
These outputs parameterize the policy distribution via (5). The
UA V evaluates the utilityu(k) via (6) and risk value e(k) via
(7) based on the detection accuracy v and f as well as the
detection delay τ.
After obtaining the subsequent state s(k+1) via (4), EDUJD
formulates the jamming detection experience by b(k) ={
s(k),a(k),u (k),e (k),s(k+1)} and stores it in the memory
poolD. This scheme randomly samples a minibatch B of I
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

5840 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
detection experiences from D, i.e., B ={b(i)|1≤ i≤ I},
and trains both policy and risk networks through forward
propagation. Speciﬁcally, the Q-network outputs the maximum
Q-value for the jamming detection policy under the current
state. We update the weights θ1≤j≤2 by minimizing the
temporal difference error through stochastic gradient descent,
i.e.,
θj← argmin
θj
1
I
I∑
i=1
(
u(i)−Q(s(i),a (i);θj)
+Θargmax
a′j∈Aj
Q
(
s(i+1),a′j;θj
))2
, (12)
where Θ ∈ [0, 1] is the discount factor. Similarly, the E
network outputs the risk value of policy to reduce detection
error, which updates the weights φ1≤j≤2. Algorithm 2 is the
pseudo-code of DEUJD.
VI. P ERFORMANCE ANALYSIS
We derive the performance bound that jointly captures
detection accuracy and latency based on the NE of the game
between a UA V and a smart jammer. We will also analyze the
computational complexity of our proposed schemes.
A. Game Model
In the jamming detection game, the UA V U chooses a
detection policya = [x,ξ ] to detect jamming attacks. Without
loss of generality, the smart jammer J selects a non-zero
jamming probability y∈ Y = [Y ,Y ] to send noise signals
based on estimated spectrum activity, e.g., the channel with
high RSS. The center frequency of the selectable jamming
channel is the same as that of the H communication channels
between the N AP-user pairs.
The UA V aims to maximize the detection utility u deﬁned
in (6), which depends on the jamming detection performance
including the false alarm rate f and miss detection rate v, the
intra-slot channel switching counts ∑Hi=1 sgn (xi)− 1 as well
as the costs of manual inspection w2/w1. The jammer’s utility
uJ decreases with the UA V’s utility and increases with both
the unit attack payoff µ, the jamming probability y, and is
deﬁned as
uJ =−u +µy. (13)
Thus, the jamming detection game between a UA V and a
smart jammer is given by G ={{U,J} ,{A,Y},{u,u J}}.
B. Performance Bound
We collected real datasets of RSS and channel gain while a
UA V detects a jammer, using 10 quantized levels of jamming
probability in a constant channel. For each setting, we gathered
detection accuracy statistics over 40,000 packets, following the
methodology of [38], which utilizes experimental results to ﬁt
spooﬁng attack detection accuracy using a logistic function.
Speciﬁcally, we estimated the jamming probabilities using
(2) and compared against 100 test thresholds. As shown in
Fig. 3, we model the expected miss detection rate v with a
Fig. 3. Nonlinear regression of the detection accuracy based on real datasets
collected by a UA V , a legitimate transceiver pair and a jammer in outdoor
experiments.
logistic function ﬁtted by regression, decreasing with jamming
probability and increasing with the test threshold, denoted by
v = 11 + exp(a1ξ +b1 (1−y) +c1), (14)
where a1 < 0, b1 < 0 and c1 > 0. Similarly, the expected
false alarm rate f, which depends on test threshold, is ﬁtted
with parameters a2 > 0 and b2 < 0 as
f =a2 exp (b2ξ). (15)
Without loss of generality, we assume independent jamming
detection across T sampling sub-slots, with all users having
the same packet rate J and transmit power p. According
to Theorem 1 in [28], which establishes the convergence of
sniffer channel assignment under detection result feedback, the
UA V will ultimately monitor the jammed channel.
Theorem 1: The performance bound of the proposed jam-
ming detection is given by
u∗ =−τ0−w2a2− w1
1+exp
(
b1−b1Y +c1
), (16)
if
µ≥ −b1 exp (c1)
(1 + exp (b1 +c1))2, (17)
0≤ w2
w1
≤ a1 exp (c1−b2)
a2b2
(
1 + exp (a1 +b1 +c1)
)2. (18)
Proof: See Appendix A. □
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

CHEN et al.: UA V-BASED JAMMING DETECTION FOR LLM-ENABLED WIRELESS NETWORKS 5841
Remark 1: Given the unit attack payoff in (17) and the
importance ratio of miss detection rate to false alarm rate
in (18), which is equivalent to the manual inspection cost
[7], the proposed scheme achieves the NE, i.e.,
(
[x∗, 0],Y).
Speciﬁcally, the jammer emits jamming signals with maximal
jamming probabilityy =Y if the unit attack payoff µ exceeds
the detected loss. The UA V monitors only one AP per time
slot and selects the minimal test threshold to avoid miss
detection. The performance bound, as given in (16), decreases
as the manual inspection cost w2/w1 and the baseline delay
τ0 increase, satisfying (18). It generally increases with the
sensing area of multimodal sensors, e.g., the hovering height
of a UA V [14].
Theorem 2: The performance bound of the proposed jam-
ming detection is given by
u∗ =−τ0−w2a2 expb2− w11+exp (a1 +b1−b1Y +c1), (19)
if
0<µ< −b1w1 exp (a1 +b1 +c1)(
1 + exp (a1 +c1)
)2 , (20)
w2
w1
≥ a1 exp (c1)
a2b2
(
1 + exp (a1 +b1 +c1)
)2. (21)
Proof: The proof is similar to that of Theorem 1. □
Remark 2: Given the unit attack payoff in (20) and the
manual inspection cost in (21), the proposed scheme achieves
the NE, i.e., ([x∗, 1],Y ). Speciﬁcally, the jammer has low
motivation to launch attacks against legitimate transmissions
and thus adopts the minimum jamming probabilityy =Y . The
UA V monitors only one AP per time slot and selects the max-
imum test threshold to avoid false alarms. The performance
bound, as given in (19), decreases as the manual inspection
costw2/w1 and the baseline delay τ0 increase, satisfying (21).
C. Computational Complexity
According to [36], the computational complexity of EUJD,
i.e., Algorithm 1, primarily arises from formulating the modi-
ﬁed Boltzmann distribution in (5) used to select the jamming
detection policy. Speciﬁcally, the hierarchical RL involves
assigning H optional sniffer channels (where the selection
sequence is irrelevant) over T sampling sub-slots, and then
selecting one of theZ2 test thresholds. This policy distribution
is formulated as a weighted sum of the Q and E values for
a given state, calculated by iterating over all possible sniffer
channel assignments Z1 and test thresholds Z2. Consequently,
the computational complexity for each time slot is given by
Γ1 = O
(∑2
j=1Zj
)
, which simpliﬁes to O (Z1) if K ≫
Z1≫ Z2 > 2NC + 4. In contrast, the non-hierarchical RL-
based jamming detection, e.g., RLJD [12], requires O(Z1Z2)
operations for each time slot.
Moreover, the computational complexity of DEUJD Γ2,
i.e., Algorithm 2, depends on the number of multiplication
operations. These operations include forward propagation to
estimate utility and risk for policy selection, and backward
propagation to update weights via gradient descent. Specif-
ically, each level j (where 1≤ j ≤ 2) of the hierarchical
Fig. 4. Hardware setting of the jamming detection system.
RL framework employs two identical neural networks. The
complexity at each level is a function of several parameters:
the input dimension Ω1≤j≤2, the number of sniffer channels
H, the total sampling sub-slotsT , and the number of quantized
test thresholdsZ2. The number of multiplication operations for
the forward pass ΦFj is therefore expressed by
ΦFj = Ωjg1,j + (g1,j + 1)g2,j + (g2,j + 1)Zj. (22)
Both Q and E networks perform ΦBj multiplications in the
backward propagation to update neural network weights θ and
φ via (12), i.e.,
ΦBj = 2Ωjg1,j + 2 (g1,j + 1)g2,j + 3 (g2,j + 1)Zj. (23)
At each level of DEUJD, both Q and E networks each
require ΦFj multiplications for the forward process to opti-
mize jamming detection policies and ΦBj multiplications for
backward propagation. Therefore, the total number of mul-
tiplications in DEUJD with I-experience minibatch per time
slot is
ΦT = 4I
2∑
j=1
ΦFj + 2I
2∑
j=1
ΦBj. (24)
Theorem 3: The computational complexity of EUJD and
REUJD are given by O (Z1K) and O (KIZ 1) if K≫Z1≫
Z2 > 2NC + 4 holds.
Proof: See Appendix B. □
Remark 3: A key observation is that the computational
complexity of both EUJD and DEUJD scales combinatorially
with Z1, the number of possible sniffer channel assignments.
Since Z1 is a function of the number of sniffers H, the sam-
pling sub-slots T , the complexity grows rapidly with network
size, i.e., the number of APs N. Increased complexity may
offer more policy selections with better detection performance.
This necessitates a practical design trade-off: the number of
sub-slots T must be chosen to balance ﬁnite computational
resources against jamming detection performance metrics like
accuracy and delay. Additionally, the number of test threshold
levels Z2 must be carefully selected to balance performance
gains with convergence speed, a consideration that is particu-
larly critical in small-scale networks.
VII. I MPLEMENTATION
As shown in Fig. 4, we implemented a UA V-based jamming
detection system for both simulation and experimental valida-
tion. The system consists of a DJI Mavic-3 equipped with a
HackRF One, a Raspberry Pi-4B with an ARM Cortex-A72
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

5842 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 5. GUI of the UA V-based jamming detection system running at the
control center.
1.5 GHz processor and 4 GB RAM, and a monocular camera.
This setup safeguards an LLM-enabled wireless network,
which includes a control center connected to multiple APs
via wired links and several CA Vs. We display the real-time
detection results in the PyQT-based GUI at the control center
as shown in Fig. 5.
The UA V captures RGB images and recognizes object
classes and relative distances using YOLOv5s with INT8
precision trained on 4,500 RGB images, each with a reso-
lution of 224× 224 pixels. Speciﬁcally, YOLOv5s employs
a backbone–neck architecture to extract and fuse multi-scale
image features, and a detection head to output bounding box
coordinates along with posterior probabilities over predeﬁned
object classes. We determine the object categories by selecting
the classes with maximum posterior probabilities. During
training, the activation functions are the sigmoid linear unit for
the backbone and neck layers, and the sigmoid for the detec-
tion head, respectively. The loss function for bounding box
regression is complete intersection over union, while binary
cross-entropy is used for object conﬁdence and classiﬁcation.
We then map these categories to “suspicious” (e.g., USRP)
or “safe” (e.g., laptop) for the RL state formulation, which
reduces computational complexity according to Remark 2. We
estimate the relative distance from the UA V using the inverse
relationship between bounding box height and actual distance,
based on known object size priors and a calibrated monocular
camera with a focal length of 3.58 mm. According to the
statistical data from 300 inferences, the processing latency is
658 ms with a variance of 33 ms, and the energy consumption
is 1.7 J, with an average inference power of 2.59 W and a
variance of 0.014 W.
The Raspberry Pi-4B equipped with two NICs drives a
HackRF One with an omnidirectional antenna to measure RSS.
Following [12], each RSS value represents the average spectral
power over a 10 MHz bandwidth centered at the monitored
frequency, computed from a discrete Fourier transform of the
received signal every second to mitigate temporary peaks.
The internal NIC decodes broadcast messages MSG-1 from
the control center, while the external NIC transmits feedback
message MSG-2 over a dedicated 2.408-2.440 GHz channel.
Fig. 6. Convergence performance of EUJD versus number of sub-slots,
learning rata and discount factor, averaged over 20 runs.
Fig. 7. Frame format of AP-UA V communication messages.
As shown in Fig. 7, the message frame format follows the
IEEE 802.11n protocol. The frame body of MSG-1 (L 1 +4
bytes) carries channel state information, communication per-
formance metrics between the AP and the intended user, and
environmental indicators derived from the LLM. Similarly,
MSG-2 (L 2 +2 bytes) carries detection performance and the
captured image for the GUI.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

CHEN et al.: UA V-BASED JAMMING DETECTION FOR LLM-ENABLED WIRELESS NETWORKS 5843
Fig. 8. Simulation settings for the UA V-based jamming detection for the
LLM-enabled wireless network, which consists of three AP-user pairs and a
smart jammer.
We trained the jamming classiﬁers based on 22,000 normal
samples collected during legitimate transmissions, with a raw
time-series feature batch size NS = 10. For the generalized
implementation, the sequential classiﬁer in DEUJD consists
of a single LSTM layer with 256 units, optimized using the
Adam with learning rate 0.001 and mean squared error loss
function similar to [21]. Each LSTM unit contains a cell state,
which is updated using the tanh function, while the gates
are controlled by the sigmoid functions. Similar to [15], we
quantize the test threshold of classiﬁers into 20 discrete levels,
set the optional number of sniffer channels H = 7 (excluding
one control channel) and the sub-slots T = 4 according to
Remark 2. In this case, the total number of possible sniffer
channel assignments is Z1 = 210, which balances the policy
exploration efﬁciency and computational complexity, as shown
in Fig. 6.(a).
The parameters for detection policy optimizing are α =
0.02, β = 0.03, ψ = 0.5 and γ = Θ = 0.2, which are
all ﬁne-tuned to enhance the learning speed and the detec-
tion performance. For example, Fig. 6.(b)-(c) presents the
simulation results of UA V-based jamming detection with the
initial topology shown in Fig. 8, demonstrating the effects of
the learning rate 0.01 ≤ α ≤ 0.1 and the discount factor
0.1≤ γ ≤ 0.5 on the convergence of the proposed EUJD.
The FC layers of DEUJD have g1 = 64 and g2 = 128, each
activated by a ReLU function, and the minibatch size B = 64.
The sliding window size for accuracy estimation is NA = 50.
We share the control center of the target wireless network
with the jamming detection system for simplicity of setup.
The control center is equipped with an Intel Core Ultra7
155H CPU (16 cores at 2.3 GHz) and an RTX 3060 GPU
with 8 GB VRAM, supporting the vision-language LLM
LLaV A-1.5 with 7 billion parameters and an INT4 quantiza-
tion. Following the user datagram protocol, each AP receives
224× 224 pixel images transmitted by the intended user,
i.e., a CA V equipped with a Raspberry Pi-4B, operating at
a center frequency of 2.4 GHz with a 10 MHz bandwidth
and a transmit power of up to 20 dBm. The system divides
each image into 400 packets of 760 bytes per time slot. For
simplicity, we take an LLM-based image-text inference task as
an example. The preset prompt recorded in the control center
is “Analyze communication-relevant entities in the image, and
output the environment indicators and relevant objects in the
format: Environment indicator: <1-5>; Objects: <comma-
separated list of objects>”. The average inference latency of
LLaV A-1.5 over 100 runs is 840 ms.
To mitigate performance degradation caused by the single
point of failure under physical attacks, we can extend the
proposed system to a UA V swarm with shared detection
results and learning experiences, following our prior work
[1]. For extreme conditions such as UA V damage or battery
depletion, the modular design enables the Raspberry Pi to be
re-integrated with other UA Vs and quickly reused via few-shot
policy ﬁne-tuning.
VIII. S IMULATION RESULTS
As shown in Fig. 8, the UA V traverses a trajectory at 3 m/s
following the Gaussian Markov mobility model, collecting
multimodal sensor data such as RSS and RGB images to
detect jamming attacks for the LLM-enabled wireless network,
which consists of three AP-user pairs. Each user transmits
760 bytes per time slot to the intended AP with a bandwidth of
10 MHz and a transmit power of up to 20 dBm. The presence
probability of the smart jammer is 0.5, which emits Gaussian
signals with a jamming power of 17 dBm over a bandwidth
of 5 MHz, and operates with 10 discrete jamming probability
levels ranging from 0.1 to 1.
Using the implemented system, we collected the channel
states from the APs to the intended users, the jammer, and the
UA V in various scenarios, including playgrounds and weed-
covered lawns with building obstructions. We also measured
the channel switching delay of the HackRF One, caused by
hardware-based baseband reconﬁguration, which follows an
exponential distribution with a mean of 24.2 ms, while the
average RSS sampling time per sub-time slot is 71.8 ms.
We compare the proposed schemes with the LSTM-based
jamming detection scheme JADE [7] and the RL-based scheme
RLJD [12], which optimizes the test threshold but does not
evaluate risk values. Both benchmarks use the same learn-
ing parameters and jamming detection policies as EUJD or
DEUJD, relying on RSS and communication performance as
inputs without incorporating environmental information from
UA V imagery or LLMs.
As shown in Fig. 9, the proposed jamming detection
schemes improve the average detection accuracy while reduc-
ing detection delay over time. For example, after 2500 time
slots, the proposed EUJD achieves a 97.7% reduction in the
false alarm rate, a 98.9% reduction in the miss detection rate,
and a 7.8% reduction in the detection delay compared with
JADE in [7]. The performance gain results from incorporating
LLM-derived environmental indicators and jointly optimiz-
ing sniffer channel assignment and test threshold selection
to counter covert jammer attacks. EUJD reduces the false
alarm rate by 88.6%, the miss detection rate by 88.3%, and
the detection delay by 7.1% compared with RLJD in [12],
thanks to accurate indication of device classes and relative
distances derived from UA V imagery in the state formula-
tion. In addition, EUJD accelerates the policy optimization
process, achieving jamming detection performance similar to
the converged RLJD, but 1000 time slots earlier. Moreover,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

5844 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 9. Jamming detection performance of the UA V using multimodal sensor
data as shown in Fig. 8.
EUJD achieves a detection error rate of less than 0.5% in
terms of both false alarm rate and miss detection rate against
the protocol-aware jamming [29], the reactive jamming [10]
and the constant jamming with signals that mimic legitimate
transmissions. The Boltzmann distribution incorporates the
exponentially weighted moving average-based miss detections
to enhance the discrimination of jamming features under
UA V vibration conditions, thereby reducing the occurrence
of detection policies associated with a higher probability of
jamming detection error.
Using deep learning, the policy and risk neural networks
address state quantization errors in the probability of sus-
picious object classes and distances, while the time-series
classiﬁer enhances detection sensitivity by capturing abnormal
variations in the raw RSS samples and PDD series to improve
the jamming detection performance. For instance, after 2500
time slots, DEUJD further reduces the false alarm rate by
95.5%, the miss detection rate by 91.1% and the detection
delay by 4.2% compared with EUJD. These improvements
result from leveraging time-series features such as raw RSS
series that are sensitive to the smart jammer even under
low jamming probability. Moreover, compressing the policy
space of sniffer channel assignments through neural networks
accelerates exploration efﬁciency and enhances detection per-
formance within limited time slots.
The averaged jamming detection performance as depicted
in Fig. 10 validates the effectiveness of our proposed schemes
across different hovering heights. For example, compared with
benchmark RLJD, the proposed DEUJD decreases the false
alarm rate by 99.2%, the miss detection rate by 98.3% and
the detection delay by 9.7% at the middle case, i.e., 7 m.
As the hovering height of a UA V increases from 3 to 11 m,
RF sampling attenuation due to antenna limitations degrades
detection performance in terms of accuracy and delay, while
the proposed methods remain robust with a miss detection
rate below 3%. Speciﬁcally, compared with RLJD, the miss
detection rate of DEUJD decreases by up to 99.6%, since
UA V imagery indicates the potential malicious devices to
help to separate congested and jammed scenarios. Moreover,
the proposed risk evaluation efﬁciently accelerates detection
policy exploration, mitigating RF sample degradation caused
by UA V vibrations and increased hovering height.
The convergence performance of EUJD in Fig. 12 illustrates
the impact of data poisoning attacks, which manipulate the
feedback for RL-based jamming detection (e.g., via noise
injection), thus degrading policy learning speed. Following the
poisoning model [39], let ϵ∈{ 0, 0.3, 0.5, 0.7, 0.9} denote the
relative magnitude of the Q-value modiﬁcation. As ϵ increases
from 0 to 0.9, the utility degrades due to the corrupted RL
feedback that impedes detection policy convergence. Neverthe-
less, the proposed scheme consistently outperforms JADE and
RLJD, beneﬁting from the miss-detection risk-aware policy
exploration.
IX. E XPERIMENTAL RESULTS
We conducted experiments using the UA V-based jamming
detection system and an outdoor wireless network with the
topology shown in Fig. 13. Following the implementation
details in Section VII, the target wireless network consists of
three users, a control center and a smart jammer, i.e., a USRP
N210 controlled by a laptop. The jammer continuously emits
Gaussian signals with a jamming power of 17 dBm [40], a
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

CHEN et al.: UA V-BASED JAMMING DETECTION FOR LLM-ENABLED WIRELESS NETWORKS 5845
Fig. 10. Average jamming detection performance of the UA V over 20 runs
each lasting 2500 time slots, with the hovering height increasing from 3 m
to 11 m.
bandwidth of 5 MHz, and a jamming probability chosen from
10 discrete levels spaced between 0.1 and 1.
As shown in Fig. 14, the results averaged over 10 runs,
each consisting of 3000 time slots, indicate that the proposed
Fig. 11. Detection error rate of EUJD under non-smart jamming attacks.
Fig. 12. Convergence performance of EUJD against data poison attacks.
Fig. 13. Experimental setting of the outdoor wireless network jamming
detection using UA V hovering at 3 m height.
schemes outperform JADE in [7] and in RLJD [12]. For
example, EUJD decreases the false alarm rate by 93.6%, the
miss detection rate by 97.8% and the detection delay by 10.6%
after 1500 time slots compared with JADE. The reason is that
the LLM-inferred environmental indicators can identify the
legitimate fading, while the suspicious object classes and UA V-
object relative distance further provide location information of
potential malicious devices. These indicators ensure the effec-
tiveness of test threshold selection by mitigating the confusion
among RSS and communication performance metrics between
legitimate channel fading and covert jamming attacks.
DEUJD further accelerates policy learning and improves
jamming detection performance, achieving a 96.8% reduction
in the false alarm rate, a 90.4% reduction in the miss detection
rate, and a 12.6% reduction in the detection delay compared
with RLJD. Compared with EUJD, DEUJD achieves an 85.5%
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

5846 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
Fig. 14. Jamming detection performance of the UA V hovering at 3 m height,
averaged over 10 runs each with 3000 time slots, using the initial topology
as shown in Fig. 13.
reduction in the false alarm rate, a 75.3% reduction in the miss
detection rate, and a 3.6% reduction in the detection delay.
These improvements result from the risk-aware evaluation that
focuses on recent miss-detections through the exponentially
weighted moving average, and from the reduced state quanti-
zation loss in policy updates.
X. C ONCLUSION
In this paper, we have proposed a UA V-based jamming
detection scheme for LLM-enabled wireless networks. Our
approach jointly evaluates jamming features, such as RSS
and other communication metrics, alongside LLM-derived
environmental indicators. It optimizes both sniffer channel
assignment and test threshold based on UA V imagery, e.g.,
suspicious radio objects, to improve detection accuracy and
reduce delay. To mitigate performance degradation from RSS
sampling errors, the system incorporates statistically derived
miss-detection results, calculated as exponentially weighted
moving averages, into an updated detection policy distribution.
An analysis of the Nash equilibrium in the jamming detection
game between a UA V and a smart jammer reveals a perfor-
mance bound, showing that utility decreases as the UA V’s
hovering height (i.e., the sensing area of multimodal sensors)
increases. Experiments were conducted using a UA V equipped
with a Raspberry Pi and a USRP to detect a smart jammer
in the LLM-enabled wireless network. Experimental results
demonstrate signiﬁcant performance gain over the benchmarks
JADE and RLJD, e.g., with 96.8% less false alarm rate, 90.4%
less miss detection rate and 12.6% less delay compared with
JADE.
APPENDIX A
PROOF OF THEOREM 1
Proof: By (6) and (13), we have
∂uJ ([x, 0],y )
∂y
= b1w1 exp (b1 (1−y) +c1)(
1 + exp (b1 (1−y) +c1)
)2 +µ≥ 0, (25)
Thus,∀y∈
[
Y,Y
]
, we have
uJ
(
[x, 0],Y
)
≥uJ ([x, 0],y ). (26)
By (17), (18) and (6), ∀ξ∈ [0, 1], we have
∂u
(
[x,ξ ],Y
)
∂ξ
=w1
a1 exp
(
a1ξ +b1
(
1−Y
)
+c1
)
(
1 + exp(a1ξ +b1
(
1−Y
)
+c1)
)2
−w2a2b2 exp(b2ξ)≤ 0, (27)
Thus,∀ξ∈ [0, 1], we have
u
(
[x, 0],Y
)
≥u
(
[x,ξ ],Y
)
. (28)
According to [15], by (6), we have
u
(
[x∗, 0],Y)≥u([x, 0],Y). (29)
wherex∗ ={0,T}H,∑Hi=1 sgn (x∗i ) = 1.
By (26), (28) and (29),
(
[x∗, 0],Y) is the NE of G. Thus,
the performance bound of the proposed jamming detection
scheme is given by (16).
The uniqueness of NE for (17) and (18) is proved by
contradictions. For a given x∗, assuming that there exists
another NE ([x∗,ξ′],y′) = (a′,y′)⁄= ([x∗, 0],Y), we have
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

CHEN et al.: UA V-BASED JAMMING DETECTION FOR LLM-ENABLED WIRELESS NETWORKS 5847
ξ′ > 0 andy′ <Y . By (25), we have uJ(a′,y ) increases with
y, thus uJ(a′,y′) < uJ(a′,Y ), contradicting the assumption
that (a′,y′) is NE. By (28), we have uS([x∗,ξ ],y′) decreases
with ξ, thus uS(a′,Y ) < uS([x∗, 0],Y ), contradicting the
assumption. Thus, although multiple equivalent realizations
of x∗ may exist due to symmetry, the equilibrium is unique
with respect to the continuous strategies (ξ,y ), and all such
realizations yield the same equilibrium utility.
APPENDIX B
PROOF OF THEOREM 2
Proof: According to [41], the number of neurons in two
hidden layers depends on the total learning steps K and the
output dimension in each level, i.e.,
g1,j =
√
K (Zj + 2) + 2
√
K
Zj + 2, (30)
and that in the second hidden layer is
g2,j =Zj
√
K
Zj + 2. (31)
As Ω1 = 2NC + 3, Ω2 = 2NC + 4, by (22)-(23) and (30)-
(31), the computational complexity of DEUJD is
Γ2 =O
(
2I
( 2∑
j=1
3Ωjg1,j + 3 (g1,j + 1)g2,j
+ 4 (g2,j + 1)Zj
))
(32)
=O

I


2∑
j=1
6Ωjg1,j +6g1,jg2,j +8 g2,jZj



 (33)
=O

I
2∑
j=1
(√
KZ j +KZ j +
√
KZ 3j
)

 (34)
=O
(
KI (Z1+Z2)
)
(35)
=O
(
KIZ 1
)
, (36)
where (32) and (33) are obtained by I≫ 2, (22)-(23), (34)
are derived by (30)-(31), and (35)-(36) are obtained as K≫
Z1≫Z2>2NC + 4.
REFERENCES
[1] Q. Chen et al., “Reinforcement learning based UA V swarm enabled
3-D multimodal jamming detection,” in Proc. IEEE Int. Conf. Commun.,
Jun. 2025, pp. 1079–1084.
[2] X. Zhang et al., “Beyond the cloud: Edge inference for generative large
language models in wireless networks,” IEEE Trans. Wireless Commun.,
vol. 24, no. 1, pp. 643–658, Jan. 2025.
[3] L. Huang et al., “A survey on hallucination in large language models:
Principles, taxonomy, challenges, and open questions,” ACM Trans.
Informat. Syst., vol. 43, no. 2, pp. 1–55, Jan. 2024.
[4] H. Zhou et al., “Large language model (LLM) for telecommunications: A
comprehensive survey on principles, key techniques, and opportunities,”
IEEE Commun. Surveys Tuts., vol. 27, no. 3, pp. 1955–2005, Jun. 2024.
[5] A. S. Abdalla, K. Powell, V . Marojevic, and G. Geraci, “UA V-assisted
attack prevention, detection, and recovery of 5G networks,” IEEE
Wireless Commun., vol. 27, no. 4, pp. 40–47, Aug. 2020.
[6] N. An and S. Weber, “Efﬁciency and detectability of random reactive
jamming in carrier sense wireless networks,” IEEE Trans. Commun.,
vol. 67, no. 10, pp. 6925–6938, Oct. 2019.
[7] C. Kilinc et al., “JADE: Data-driven automated jammer detection frame-
work for operational mobile networks,” in Proc. IEEE Conf. Comput.
Commun., May 2022, pp. 1139–1148.
[8] L. Arcangeloni, E. Testi, and A. Giorgetti, “Detection of jamming attacks
via source separation and causal inference,” IEEE Trans. Commun.,
vol. 71, no. 8, pp. 4793–4806, Aug. 2023.
[9] Z. Lu, W. Wang, and C. Wang, “Modeling, evaluation and detection
of jamming attacks in time-critical wireless applications,” IEEE Trans.
Mobile Comput., vol. 13, no. 8, pp. 1746–1759, Aug. 2014.
[10] M. Spuhler, D. Giustiniano, V . Lenders, M. Wilhelm, and
J. B. Schmitt, “Detection of reactive jamming in DSSS-based
wireless communications,” IEEE Trans. Wireless Commun., vol. 13,
no. 3, pp. 1593–1603, Mar. 2014.
[11] S.-D. Wang, H.-M. Wang, and P. Liu, “Fast detection of burst jamming
for delay-sensitive Internet-of-Things applications,” IEEE Trans. Wire-
less Commun., vol. 22, no. 6, pp. 3955–3967, Jun. 2023.
[12] C. Wang, Y . Chen, Z. Lin, Q. Chen, and L. Xiao, “Reinforcement
learning based jamming detection for reliable wireless communications,”
in Proc. IEEE 99th V eh. Technol. Conf. (VTC-Spring), Jun. 2024,
pp. 1–5.
[13] C. Zhang, L. Zhang, T. Mao, Z. Xiao, Z. Han, and X.-G. Xia, “Detection
of stealthy jamming for UA V-assisted wireless communications: An
HMM-based method,” IEEE Trans. Cognit. Commun. Netw., vol. 9,
no. 3, pp. 779–793, Jun. 2023.
[14] N. C. Matson and K. Sundaresan, “Online radio environment map
creation via UA V vision for aerial networks,” in Proc. IEEE Conf.
Comput. Commun. (INFOCOM), vol. 190, Vancouver, BC, Canada, May
2024, pp. 81–90.
[15] T. Le, C. Szepesvari, and R. Zheng, “Sequential learning for multi-
channel wireless network monitoring with channel switching costs,”
IEEE Trans. Signal Process., vol. 62, no. 22, pp. 5919–5929, Nov. 2014.
[16] L. Chen, Z. Lu, P. Zhou, and J. Xu, “Learning optimal sniffer channel
assignment for small cell cognitive radio networks,” in Proc. IEEE Conf.
Comput. Commun., Toronto, ON, Canada, Jul. 2020, pp. 656–665.
[17] J. Wang, W. Wang, C. Wang, and M. Song, “Spectrum activity surveil-
lance: Modeling and analysis from perspectives of surveillance coverage
and culprit detection,” IEEE Trans. Mobile Comput., vol. 21, no. 5,
pp. 1829–1846, May 2022.
[18] A. Benslimane and H. Nguyen-Minh, “Jamming attack model and
detection method for beacons under multichannel operation in vehicular
networks,” IEEE Trans. V eh. Technol., vol. 66, no. 7, pp. 6475–6488,
Jul. 2017.
[19] S.-D. Wang, H.-M. Wang, Z. Li, and V . C. M. Leung, “Joint space-time
sparsity based jamming detection for mission-critical mMTC networks,”
IEEE Trans. Commun., vol. 71, no. 2, pp. 1226–1238, Feb. 2023.
[20] Y . Shi, X. Lu, Y . Li, and K. An, “Active detection for symbol-
level jamming,” IEEE Trans. Wireless Commun., vol. 23, no. 10,
pp. 13039–13052, Oct. 2024.
[21] S. Jere, Y . Wang, I. Aryendu, S. Dayekh, and L. Liu, “Bayesian
inference-assisted machine learning for near real-time jamming detec-
tion and classiﬁcation in 5G new radio (NR),” IEEE Trans. Wireless
Commun., vol. 23, no. 7, pp. 7043–7059, Jul. 2024.
[22] M. Hossain and J. Xie, “Third eye: Context-aware detection for hidden
terminal emulation attacks in cognitive radio-enabled IoT networks,”
IEEE Trans. Cognit. Commun. Netw., vol. 6, no. 1, pp. 214–228, Mar.
2020.
[23] A. Mehrabian and G. Kaddoum, “Cooperative jamming detection using
low-rank structure of received signal matrix,” IEEE Trans. Commun.,
vol. 73, no. 11, pp. 12899–12912, Nov. 2025.
[24] Z. Jia et al., “Accurate jammer localization in wireless sensor networks
based on signal strength map,” IEEE Internet Things J., vol. 12, no. 24,
pp. 53353–53366, Dec. 2025.
[25] S. Sciancalepore, F. Kusters, N. K. Abdelhadi, and G. Oligeri, “Jamming
detection in low-BER mobile indoor scenarios via deep learning,” IEEE
Internet Things J., vol. 11, no. 8, pp. 14682–14697, Apr. 2024.
[26] W. Tian et al., “Contract-based incentive mechanisms for UA V networks
in covert communications,” IEEE Trans. V eh. Technol., vol. 74, no. 5,
pp. 7378–7391, May 2025.
[27] W. Tian, X. Dong, G. Pan, C. Pan, J. Nie, and Z. Han, “A preference
value-based reverse auction mechanism for satellite-assisted integrated
communication and jamming system in IoT,” IEEE Internet Things J.,
vol. 12, no. 24, pp. 55316–55329, Dec. 2025.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

5848 IEEE TRANSACTIONS ON COMMUNICATIONS, VOL. 74, 2026
[28] M. Li, D. Yang, J. Lin, M. Li, and J. Tang, “SpecWatch: Adversarial
spectrum usage monitoring in CRNs with unknown statistics,” in Proc.
IEEE Conf. Comput. Commun. (INFOCOM), Jul. 2016, pp. 1–9.
[29] H. Zhu, C. Fang, Y . Liu, C. Chen, M. Li, and X. S. Shen, “You can jam
but you cannot hide: Defending against jamming attacks for geo-location
database driven spectrum sharing,” IEEE J. Sel. Areas Commun., vol. 34,
no. 10, pp. 2723–2737, Oct. 2016.
[30] M. K. Hanawal, D. N. Nguyen, and M. Krunz, “Cognitive networks
with in-band full-duplex radios: Jamming attacks and countermeasures,”
IEEE Trans. Cognit. Commun. Netw., vol. 6, no. 1, pp. 296–309, Mar.
2020.
[31] Y . He, J. Fang, F. R. Yu, and V . C. Leung, “Large language models
(LLMs) inference ofﬂoading and resource allocation in cloud-edge com-
puting: An active inference approach,” IEEE Trans. Mobile Comput.,
vol. 23, no. 12, pp. 11253–11264, Dec. 2024.
[32] X. W. Liu, S. Gao, B. Liu, X. Cheng, and L. Yang, “LLM4WM:
Adapting LLM for wireless multi-tasking,” IEEE Trans. Mach. Learn.
Commun. Netw., vol. 3, pp. 835–847, 2025.
[33] Z. Xu, T. Zheng, and L. Dai, “LLM-empowered near-ﬁeld communica-
tions for low-altitude economy,” IEEE Trans. Commun., vol. 73, no. 11,
pp. 11186–11196, Nov. 2025.
[34] M. Li, I. Koutsopoulos, and R. Poovendran, “Optimal jamming attack
strategies and network defense policies in wireless sensor networks,”
IEEE Trans. Mobile Comput., vol. 9, no. 8, pp. 1119–1133, Aug. 2010.
[35] X. Cheng, J. Shi, M. Sha, and L. Guo, “Revealing smart selective
jamming attacks in WirelessHART networks,” IEEE/ACM Trans. Netw.,
vol. 31, no. 4, pp. 1611–1625, Aug. 2023.
[36] X. Lu, L. Xiao, G. Niu, X. Ji, and Q. Wang, “Safe exploration in wireless
security: A safe reinforcement learning algorithm with hierarchical
structure,” IEEE Trans. Inf. F orensics Security, vol. 17, pp. 732–743,
2022.
[37] A. Kumar, A. Gupta, and S. Levine, “DisCor: Corrective feedback in
reinforcement learning via distribution correction,” in Proc. Adv. Neural
Inf. Process. Syst. (NIPS), Mar. 2020, pp. 18560–18572.
[38] L. Xiao, X. Lu, T. Xu, W. Zhuang, and H. Dai, “Reinforcement learning-
based physical-layer authentication for controller area networks,” IEEE
Trans. Inf. F orensics Security, vol. 16, pp. 2535–2547, 2021.
[39] A. Rakhsha, G. Radanovic, R. Devidze, X. Zhu, and A. Singla, “Policy
teaching via environment poisoning: Training-time adversarial attacks
against reinforcement learning,” in Proc. Int. Conf. Mach. Learn., 2020,
pp. 7974–7984.
[40] W. Xu, W. Trappe, Y . Zhang, and T. Wood, “The feasibility of launching
and detecting jamming attacks in wireless networks,” in Proc. 6th ACM
Int. Symp. Mobile Ad Hoc Netw. Comput., May 2005, pp. 46–57.
[41] G.-B. Huang, “Learning capability and storage capacity of two-hidden-
layer feedforward networks,” IEEE Trans. Neural Netw., vol. 14, no. 2,
pp. 274–281, Mar. 2003.
Qiaoxin Chen (Graduate Student Member, IEEE)
received the B.S. degree in electronic and infor-
mation engineering from Fuzhou University, China,
in 2020, and the M.S. degree from Fujian Normal
University, China, in 2023. He is currently pursuing
the Ph.D. degree with the Department of Informatics
and Communication Engineering, Xiamen Univer-
sity. His research interests include network security
and wireless communication.
Liang Xiao (Fellow, IEEE) received the B.S. degree
in communication engineering from Nanjing Uni-
versity of Posts and Telecommunications, China,
in 2000, the M.S. degree in electrical engineering
from Tsinghua University, China, in 2003, and the
Ph.D. degree in electrical engineering from Rutgers
University, NJ, USA, in 2009. She was a Visiting
Professor with Princeton University, Virginia Tech,
and the University of Maryland, College Park. She is
currently a Professor with the Department of Infor-
mation and Communication Engineering, Xiamen
University, Xiamen, China. She was a recipient of the Best Paper Award for
the 2016 INFOCOM Big Security WS and the 2017 ICC. She has served as an
Associate Editor for IEEE T RANSACTIONS ON INFORMATION FORENSICS
AND SECURITY and a Guest Editor for IEEE J OURNAL OF SELECTED
TOPICS IN SIGNAL PROCESSING .
Pengcheng Wang (Graduate Student Member,
IEEE) received the B.S. degree in communication
engineering from Nanjing University of Informa-
tion Science and Technology, Nanjing, China, in
2024. He is currently pursuing the M.S. degree
with the Department of Informatics and Communi-
cation Engineering, Xiamen University. His research
interests include network security and reinforcement
learning.
Jieling Li (Graduate Student Member, IEEE)
received the M.S. degree in computer technol-
ogy from Fuzhou University, China, in 2022.
He is currently pursuing the Ph.D. degree with
the Department of Informatics and Communica-
tion Engineering, Xiamen University. His research
interests include network security, reinforcement
learning, and networking.
Haoyu Chen (Graduate Student Member, IEEE)
received the B.Eng. and the M.Sc. degrees from the
Department of Electronic Information Engineering,
Fuzhou University, Fujian, China, in 2020 and 2023,
respectively. He is currently pursuing the Ph.D.
degree with the Institute of Artiﬁcial Intelligence,
Xiamen University. His research interests include
radio localization, wireless communications, and
smart grids.
Hongbin Jin received the Ph.D. degree in electronic
science and technology from the School of Elec-
tronic Engineering, Beijing University of Posts and
Telecommunications, China, in 2019. His research
interests include stereo vision, deep learning, and
image classiﬁcation.
Ying-Jun Angela Zhang (Fellow, IEEE) received
the Ph.D. degree from the Department of Electri-
cal and Electronic Engineering, The Hong Kong
University of Science and Technology. She joined
the Department of Information Engineering, The
Chinese University of Hong Kong, in 2005, where
she is currently a Professor. She is the Steering Com-
mittee Chair of IEEE W IRELESS COMMUNICATION
LETTERS , a Member-at-Large of the IEEE ComSoc
Board of Governors, the Director of IEEE ComSoc
Asia–Paciﬁc Region Board, and a member of the
IEEE VTS Fellow Evaluation Standing Committee. As the only winner from
engineering science, she won the Hong Kong Young Scientist Award 2006,
conferred by The Hong Kong Institute of Science. She was a co-recipient of
the 2021 and 2014 IEEE ComSoc Asia–Paciﬁc Outstanding Paper Awards, the
2013 IEEE SmartGridComm Best Paper Award, and the 2011 IEEE Marconi
Prize Paper Award on Wireless Communications. Previously, she served as
Editor-in-Chief of IEEE O PEN JOURNAL OF THE COMMUNICATIONS SOCI -
ETY, the Chair of the Executive Editor Committee of IEEE T RANSACTIONS
ON WIRELESS COMMUNICATIONS , and a member of the IEEE ComSoc
Fellow Evaluation Standing Committee. She has served on the organizing
committees of many top conferences, such as IEEE GLOBECOM, ICC, VTC,
and SmartgridComm. She was the Founding Chair of the IEEE ComSoc
Technical Committee of Smart Grid Communications.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:39 UTC from IEEE Xplore.  Restrictions apply.
