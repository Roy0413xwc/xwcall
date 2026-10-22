---
type: literature-fulltext
title: "Large-Model AI for Near-Field Beam Prediction: A CNN–GPT2 Framework for 6G XL-MIMO"
zotero_key: "ZA7G85FZ"
pdf_key: "VJCED2V5"
doi: "10.1109/TWC.2026.3682058"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Large-Model AI for Near-Field Beam Prediction- A CNN–GPT2 Framework for 6G XL-MIMO.md"
fulltext_path: "03fulltext/备选讲组会论文/ZA7G85FZ.md"
zotero_item: "zotero://select/library/items/ZA7G85FZ"
zotero_pdf: "zotero://open-pdf/library/items/VJCED2V5"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Large-Model AI for Near-Field Beam Prediction: A CNN–GPT2 Framework for 6G XL-MIMO

> PDF 原文逐页文本抽取；来源文件 SHA-256：`4e1e5a7072c4f5cb0e78f1a67fa238453a34bd27fc32367e04fed54b47121609`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 15149
Large-Model AI for Near-Field Beam Prediction: A
CNN–GPT2 Framework for 6G XL-MIMO
Wang Liu
 , Graduate Student Member, IEEE , Cunhua Pan
 , Senior Member, IEEE, Hong Ren
 , Member, IEEE,
Wei Zhang
 , Fellow, IEEE, Cheng-Xiang Wang
 , Fellow, IEEE, and Jiangzhou Wang
 , Fellow, IEEE
Abstract—The emergence of extremely large-scale antenna
arrays (ELAA) in millimeter-wave (mmWave) communications,
particularly in high-mobility scenarios, highlights the importance
of near-ﬁeld beam prediction. Unlike the conventional far-ﬁeld
assumption, near-ﬁeld beam prediction requires codebooks that
jointly sample the angular and distance domains, which leads
to a dramatic increase in pilot overhead. Moreover, unlike
the far-ﬁeld case where the optimal beam evolution is tem-
porally smooth, the optimal near-ﬁeld beam index exhibits
abrupt and nonlinear dynamics due to its joint dependence
on user angle and distance, posing signiﬁcant challenges for
temporal modeling. To address these challenges, we propose
a novel Convolutional Neural Network–Generative Pre-trained
Transformer 2 (CNN–GPT2) based near-ﬁeld beam prediction
framework. Speciﬁcally, an uplink pilot transmission strategy is
designed to enable efﬁcient channel probing through widebeam
analog precoding and frequency-varying digital precoding. The
received pilot signals are preprocessed and passed through a
CNN-based feature extractor, followed by a GPT-2 model that
captures temporal dependencies across multiple frames and
directly predicts the near-ﬁeld beam index in an end-to-end man-
ner. A pretraining–ﬁnetuning strategy is further adopted, where
the model is ﬁrst pretrained via masked prediction and then
ﬁnetuned for the downstream beam prediction task, signiﬁcantly
improving training efﬁciency and accuracy. Simulation results
under the 3GPP TR 38.901 channel model demonstrate that the
proposed method achieves higher beam prediction accuracy than
conventional recurrent models, while maintaining competitive
performance in normalized beamforming gain. These results
conﬁrm the feasibility of employing large-model AI for robust and
low-overhead near-ﬁeld beam management in future 6G systems.
Received 25 October 2025; revised 3 February 2026; accepted 31 March
2026. Date of current version 15 April 2026. The work of Cunhua Pan
was supported in part by the Key Research and Development Projects
under Grant 2023YFB2905100. The work of Cheng-Xiang Wang was
supported in part by the Major Science and Technology Project of
Jiangsu Province under Grant BG2025039; and in part by the Research
Fund of National Mobile Communications Research Laboratory, Southeast
University, under Grant 2026A05. The work of Jiangzhou Wang was sup-
ported in part by the Natural Science Foundation of China under Grant
62350710796. The associate editor coordinating the review of this article
and approving it for publication was E. Balevi. (Corresponding authors:
Cunhua Pan; Hong Ren.)
Wang Liu, Cunhua Pan, and Hong Ren are with the National Mobile
Communications Research Laboratory, Southeast University, Nanjing 211189,
China (e-mail: w liu@seu.edu.cn; cpan@seu.edu.cn; hren@seu.edu.cn).
Wei Zhang is with the School of Electrical Engineering and Telecommu-
nications, University of New South Wales, Sydney, NSW 2052, Australia
(e-mail: w.zhang@unsw.edu.au).
Cheng-Xiang Wang and Jiangzhou Wang are with the National Mobile
Communications Research Laboratory, School of Information Science and
Engineering, Southeast University, Nanjing 211189, China, and also with the
Pervasive Communication Research Center, Purple Mountain Laboratories,
Nanjing 211111, China (e-mail: chxwang@seu.edu.cn; j.z.wang@seu.edu.cn).
Digital Object Identiﬁer 10.1109/TWC.2026.3682058
Index Terms—ELAA, near ﬁeld, beam prediction, mmWave,
CNN, GPT-2.
I. I NTRODUCTION
M
ILLIMETER-W A VE (mmWave) bands provide abun-
dant spectrum resources and enable ultra-high data
rates, making them a cornerstone of current ﬁfth-generation
(5G) and future sixth-generation (6G) mobile communication
systems [1], [2], [3], [4]. However, mmWave signals suffer
from severe propagation loss compared to sub-6 GHz bands.
To overcome this challenge, 5G systems deploy massive
multiple-input multiple-output (MIMO) antenna arrays at the
base station (BS) to establish highly directional transmissions
[5]. Looking ahead to 6G, the scale of antenna deploy-
ment is expected to further increase, leading to the concept
of extremely large-scale antenna arrays (ELAA) [6]. With
a signiﬁcantly larger number of antenna elements, ELAA
can achieve sharper spatial focusing and higher array gains,
thereby offering unprecedented improvements in spectral efﬁ-
ciency [7], [8]. These factors prompted extensive research
into ELAA and mmWave systems from multiple perspectives,
including channel estimation and performance analysis [9],
[10].
To fully exploit the potential of ELAA systems, accurate
beam alignment between the BS and users is crucial [5].
Conventional codebook-based beam training enables optimal
beam selection but suffers from high-mobility scenarios, where
rapid user movement causes trained beams to become quickly
outdated, resulting in severe misalignment and throughput
loss. To overcome this limitation, beam prediction has been
introduced, leveraging temporal correlations in historical pilot
signals to infer future optimal beams with reduced delay
[11]. Speciﬁcally, in a typical prediction framework, the user
periodically transmits uplink pilot signals (e.g., Sounding Ref-
erence Signals). The BS collects a sequence of these historical
channel observations and employs a prediction algorithm to
infer the optimal beam index for future data transmission
frames. This approach eliminates the need for real-time beam
training on the target frame, thereby effectively resolving the
issue of selected beams becoming outdated rapidly.
However, beam prediction in ELAA systems presents
several key challenges. Firstly, the transition from the far-
ﬁeld to the near-ﬁeld regime fundamentally alters the array
response: while far-ﬁeld beamforming depends solely on
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

15150 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
the angular domain under planar-wave assumptions, near-
ﬁeld propagation involves spherical wavefronts, making the
array response jointly dependent on user angle and distance.
As a result, the near-ﬁeld beamforming codebook expands
from a one-dimensional angular space to a two-dimensional
angle–distance domain, dramatically increasing the number
of codewords and the required pilot overhead. This enlarged
codebook substantially raises pilot overhead and hinders fast
beam adaptation under user mobility [8], [12].
Secondly, from the perspective of temporal modeling, beam
prediction in ELAA systems presents unique challenges. In
far-ﬁeld systems, the optimal beam index primarily depends
on the user’s angular. As the user moves, the angle of arrival or
departure changes gradually, leading to a smooth evolution of
the optimal beam index over time. In contrast, in the near-ﬁeld
regime, the optimal beam index depends jointly on both the
angle and the distance of the user. This dual dependence intro-
duces strong spatial nonlinearity into the beam dynamics. Even
small user movements can cause signiﬁcant phase shifts across
the antenna array, resulting in abrupt changes in the optimal
near-ﬁeld beam index. Consequently, the temporal evolution
of the beam becomes highly non-smooth and less predictable,
making it substantially more difﬁcult for conventional time-
series models to capture long-term dependencies [13].
A. Related Work
In recent years, a wide range of signal processing and
learning-based techniques have been investigated for beam
prediction and tracking in mmWave systems [14], [15], [16],
[17], [18], [19], [20], [21], [22], [23], [24], [25]. Early studies
mainly relied on model-based approaches, such as extended
Kalman ﬁlter (EKF)-assisted beam tracking [14], [15] and
Gaussian process regression for UA V communications [16],
[17], where beam evolution is inferred from explicitly modeled
spatial dynamics. More recently, data-driven methods have
been widely adopted to improve robustness and reduce over-
head. Representative works include AI/ML-based time-domain
beam prediction aligned with 3GPP standards [18], demon-
strating the feasibility of AI-assisted beam prediction. Deep
learning frameworks that fuse sub-6 GHz CSI with sparse
mmWave measurements [19], and multi-stage or attention-
based neural architectures combining convolutional neural
network (CNN), recurrent Neural Network (RNN), and long
short-term memory (LSTM) modules [20], [21], [22], [23],
[24] were also proposed. In addition, large language model
(LLM)-based approach has been applied to beam prediction;
however, it relies heavily on accurate historical angular infor-
mation [25].
Despite their effectiveness, the above methods are predom-
inantly developed under the far-ﬁeld planar-wave assumption,
where the beam index evolution is governed mainly by angular
variations. As a result, they do not explicitly account for
distance-dependent effects or angle–distance coupling, and
their modeling assumptions and learned representations cannot
be directly extended to near-ﬁeld beam prediction scenarios.
For near-ﬁeld communications, a number of studies have
explicitly accounted for the spherical-wave propagation effect,
where the optimal near-ﬁeld beam is jointly determined by
the user’s angle and distance. Correspondingly, various beam
training strategies have been developed to mitigate the sharply
increased pilot overhead induced by the near-ﬁeld codebook
[26], [27], [28], [29], [30], [31]. Existing near-ﬁeld beam train-
ing methods can be broadly categorized into two classes. The
ﬁrst class follows a two-stage training paradigm. Representa-
tive works [26], [27] ﬁrst employed a far-ﬁeld discrete Fourier
transform (DFT) codebook to obtain a coarse estimate of the
user’s angle or distance range, and subsequently performed
reﬁned probing using a near-ﬁeld codebook within the reduced
search region to identify the optimal near-ﬁeld beam. The
second class relies on hierarchical near-ﬁeld codebooks with
multiple resolution levels [28], [29], [30]. These schemes ﬁrst
employed lower-resolution beam to estimate the user’s angle
and distance, then continuously employed higher-resolution
beams to determine the optimal codewords. In addition, a
Bayesian regression based near-ﬁeld beam training scheme
was recently proposed in [31], which exploited the strong
correlation among near-ﬁeld codewords to further reduce pilot
overhead. Additionally, various deep learning-based near-ﬁeld
beam training schemes utilizing CNNs and graph neural
networks (GNNs) have been proposed to reduce pilot overhead
[32], [33], [34].
Although the aforementioned methods can effectively
reduce training overhead and explicitly incorporate near-ﬁeld
spherical wave characteristics, they are primarily designed
for beam training or estimation under quasi-static assump-
tions. They do not explicitly address user mobility, and the
estimated near-ﬁeld beams may quickly become outdated in
high-mobility scenarios. As a result, these approaches are not
directly applicable to the near-ﬁeld beam prediction problem
considered in this work.
Beyond static or quasi-static beam training, several studies
have investigated beam tracking or prediction in near-ﬁeld
scenarios by explicitly accounting for user mobility. [35]
proposed a near-ﬁeld beam-tracking scheme based on dynamic
non-uniform grids under simple user motion trajectories. How-
ever, it requires near-ﬁeld beam scanning and thus does not
effectively reduce the pilot overhead. In[36], a low-complexity
near-ﬁeld beam tracking (NFBT) scheme was proposed, in
which the near-ﬁeld channel variation is characterized by a
kinematic motion model. Real-time channel parameters are
ﬁrst estimated, and then incorporated into an EKF framework
to track and predict the near-ﬁeld beam. Similarly, [37] applied
EKF to near-ﬁeld tracking by designing a speciﬁc observa-
tion model to mitigate near-ﬁeld phase non-linearities and
synchronization issues. Furthermore, [38] proposed a particle
ﬁlter (PF)-based near-ﬁeld beam tracking scheme, which is
better suited for handling the nonlinear phase characteristics
in the near ﬁeld but entails high computational complexity.
In speciﬁc scenarios such as high-speed railways (HSR), [39]
proposed a near-ﬁeld beam prediction scheme that utilizes the
periodicity and regularity of train trajectories and effectively
reduces system overhead. From a hardware perspective, [40]
introduced a beam tracking method using an overlapped sub-
array conﬁguration, estimating angle and range via differential
signal products.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15151
However, these near-ﬁeld beam tracking and prediction
methods based on conventional signal processing frameworks
typically depend on strong assumptions regarding pre-deﬁned
motion models and idealized channel assumptions [35], [36],
[37], [38], scenario-speciﬁc prior information [39], or array
structures [40]. Moreover, Doppler frequency shift and its
impact on beam prediction are typically not explicitly consid-
ered in these approaches, making them more challenging to
apply in practice. These limitations motivate the exploration
of data-driven approaches that can learn near-ﬁeld spatio-
temporal evolution directly from data, without relying on
explicit kinematic or channel models.
Recently, data-driven deep learning has also been introduced
to near-ﬁeld beam prediction and tracking, which aim to
approximate the non-linear beam evolution directly from data.
For instance, to handle dynamic user tracking, [41] introduced
an Interacting Multiple Model with Gated Recurrent Units
(IMM-GRU), which attempts to capture complex motion tra-
jectories that single-model ﬁlters often miss. A related line of
work in [42] employs a graph convolutional network (GCN)
followed by a GRU to output the future beam, aiming to
enhance tracking robustness by explicitly modeling spatial
relationships among nodes. However, the proposed network
requires precise knowledge of the user’s coordinates, path
gain, and velocity vector to construct the graph, which are
typically difﬁcult to obtain in practical systems. Moreover,
[43] proposed a CNN and LSTM assisted two-stage near-
ﬁeld beam tracking scheme. Although LSTM based scheme
performs well, it relies on a highly simpliﬁed channel model
characterised by single-carrier transmission, extremely sparse
non-line-of-sight (NLoS) components, and complete neglect
of Doppler shift. In practical settings, due to the Doppler
effect and abundant scattering, LSTMs with limited temporal
modelling capabilities may lead to a signiﬁcant decline in
prediction reliability. Similar inherent architectural limitations
were also observed in [41] and [42].
Collectively, these recurrent neural network (RNN) variants
(including LSTM and GRU) inherently suffer from the bot-
tlenecks of recursive processing mechanisms. They struggle
to capture global temporal correlations over long historical
sequences, often failing to retain early geometric cues that
are critical for learning the non-linear, angle-distance cou-
pled beam dynamics, especially under high-speed motion
and complex practical channels. Furthermore, training these
networks from scratch on limited datasets often results in
poor generalization capabilities. These persistent challenges
motivate the search for an architecture with superior temporal
modeling power and a more robust generalization paradigm,
necessitating the shift towards large-model AI frameworks.
B. Main Contributions
Motivated by the challenges of excessive pilot overhead,
nonlinear beam dynamics, and insufﬁcient temporal modeling
capability in near-ﬁeld extremely large-scale MIMO (XL-
MIMO) systems, this paper proposes a large-model-driven
end-to-end framework for near-ﬁeld beam prediction. In terms
of reducing overhead, our scheme only tests widebeam code-
words during the uplink pilot transmission of each frame. This
requires relatively little pilot resources, and the widebeam
pilot signals obtained from these tests contain coarse yet
sufﬁcient user angle and distance features [32], [34]. To predict
optimal near-ﬁeld beams from these historical widebeam pilot
signals and address the speciﬁc challenges of near ﬁeld,
we employ a CNN-GPT-2 architecture, which aligns well
with the considered near-ﬁeld beam prediction problem under
pilot overhead constraints: The raw widebeam pilot signal
exhibits high dimensionality and a highly structured nature,
and is susceptible to noise and multipath propagation effects.
The CNN, serving as the front-end, enables efﬁcient feature
extraction and dimensionality reduction to obtain a compact
embedding [44]. The subsequent GPT-2 module abandons the
recursive mechanism of traditional RNNs, instead adopting a
self-attention mechanism. This enables a global receptive ﬁeld
that accurately captures long-range temporal dependencies and
the non-smooth beam index evolution arising from near-ﬁeld
angle-distance coupling [45], [46]. Furthermore, a pre-training
and ﬁne-tuning paradigm is incorporated, thereby ensuring
robust generalization capabilities even under limited labeled
data.
The main contributions are summarized as follows:
• End-to-end near-ﬁeld beam prediction framework:We
reformulate near-ﬁeld beam training as a beam prediction
problem and build an end-to-end trainable network that
directly maps historical pilot signals to the next near-
ﬁeld beam index. This approach eliminates the need for
explicit channel estimation or intermediate parameters.
By integrating feature extraction, temporal modeling, and
beam decision into one coherent process, the frame-
work avoides the error accumulation seen in multi-stage
designs and achieves faster inference with better consis-
tency.
• Low-overhead and robust pilot transmission strategy
We design a universal uplink pilot transmission scheme
aiming at enabling efﬁcient channel probing with
low overhead. Speciﬁcally, widebeam analog precod-
ing is constructed to achieve comprehensive spatial
coverage using small number of pilot resources. More-
over, frequency-dependent digital precoding and pilot
sequences are employed to exploit spectral diversity and
ensure stable feature observations. To ensure realistic
performance evaluation, this generic strategy is instan-
tiated and validated using the standardized 5G NR frame
structure and 3GPP TR 38.901 channel speciﬁcations.
• Large-model-driven spatiotemporal learning architec-
ture: Considering the highly nonlinear and non-smooth
temporal evolution of near-ﬁeld beams, we adopt a
hybrid CNN–GPT-2 architecture. The convolutional mod-
ule extracts and compresses spatial information from
high-dimensional pilot data, while the GPT-2 module cap-
tures long-range temporal dependencies across multiple
radio frames.
• Pre-training and ﬁne-tuning strategy for enhanced
generalization: We further introduce a Bidirectional
Encoder Representations from Transformers (BERT)-
inspired pre-training–ﬁne-tuning paradigm. In pre-
training, a temporal masking task with an 80/10/10
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

15152 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
policy facilitates context-aware feature learning; during
ﬁne-tuning, the model specializes in next-frame beam
prediction. This two-stage training enhances temporal
modeling capability, leading to improved prediction accu-
racy and better generalization performance.
The remainder of this paper is organized as follows. Sec-
tion II introduces the considered system model and formulates
the beam prediction problem. Section III details the proposed
CNN–GPT-2-based prediction framework, including its net-
work architecture and processing pipeline. Section IV presents
and analyzes the simulation results, and Section V concludes
the paper with ﬁnal remarks.
The main notations used in this paper are as follows. Bold
lowercase and uppercase letters (e.g., a and A) denote vectors
and matrices, respectively; scalars and sets are represented by
a andA. The i-th entry of a and the (i,j )-th entry of A
are written as [a]i and [A]i,j. The absolute value is denoted
by|·|, while (·)∗, (·)T, and (·)H represent the conjugate,
transpose, and Hermitian transpose, respectively. A complex
Gaussian variable with mean µ and variance σ2 is expressed
asCN (µ,σ 2), and|·| F denotes the Frobenius norm.
II. S YSTEM MODEL
A. Downlink Signal Model
Consider a time-division duplexing (TDD) based multi-user
mmWave-orthogonal frequency division multiplexing (OFDM)
communication system. A BS equipped with a uniform linear
array (ULA)1 ofNBS antennas andNRF radio-frequency (RF)
chains simultaneously serves U single-antenna users over K
orthogonal subcarriers. The condition U ≤ NRF≪ NBS is
assumed to hold, and to reduce power consumption redundant
RF chains are switched off, i.e., NRF =U [47], [48].
Let hdlu,k∈ C1×NBS denote the downlink (DL) channel from
the BS to user u on thek-th subcarrier, whereu = 1, 2,...,U
and k = 1, 2,...,K . During DL transmission, the received
signal of user u on subcarrier k is given by
rdlu,k = hdlu,kFRFFBB,ksk +ndlu,k
= hdlu,kFRF
U∑
j=1
fBBj,ksj,k +ndlu,k, (1)
where sk = [s 1,k,s 2,k,...,s U,k]T ∈ CU×1 denotes the
transmitted signal vector on subcarrier k, satisfying the
power constraint E
[
sksHk] = PdlUK IU . Here, FBB,k =[
fBB1,k, fBB2,k,..., fBBU,k
]
∈ CU×U is the digital precoder on sub-
carrierk, while FRF =
[
fRF1 , fRF2 ,..., fRFU ]∈ CNBS×U is the
frequency-ﬂat analog precoder shared across all subcarriers.
Moreover, ndlu,k ∼ CN(0,σ 2dl) represents the additive white
Gaussian noise (AWGN) at user u on subcarrier k.
Since FRF is implemented via phase shifters, each of its
entries has a constant modulus normalized as
⏐⏐ [FRF]m,n⏐⏐2 =
1The proposed framework can be naturally extended to uniform planar array
(UPA) deployments. In this case, the array response depends on azimuth,
elevation and distance, and only a corresponding three-dimensional near-
ﬁeld codebook needs to be adopted. Hence, the proposed CNN–GPT-2-based
prediction model and pilot transmission strategy remain directly applicable,
since the underlying spherical-wavefront propagation and spatial–frequency
correlations are preserved.
1
NBS . Speciﬁcally, the elements take the form [FRF]m,n =1√NBSejφm,n, where φm,n is a quantized phase [47], [48].Furthermore, we assume equal power allocation across all
subcarriers and users [49], and the digital precoders are
required to satisfy the normalization constraint
‖‖FRFfBBu,k‖‖2F = 1, ∀u = 1, 2,...,U, k = 1, 2,...,K, (2)
such that no additional power gain is introduced by the digital
domain.
B. Channel Model
In this work, we consider a geometry based stochastic
channel model (GSCM) for mmWave systems. The channel is
represented as a sum of a ﬁnite number of paths whose delays,
directions, and complex weights are generated statistically
while remaining consistent with an underlying propagation
geometry. For ELAA systems, we further adopt a spherical
wavefront representation in the channel model so that the
phase of each path is governed by the exact element wise
propagation distance rather than a plane wave approximation.
The channel impulse response between the s-th transmit
antenna element at the BS and the n-th receive antenna
element at the user is expressed as a combination of line-
of-sight (LoS) and non-line-of-sight (NLoS) components:
Hn,s(τ,t) =
√
1
KR + 1HNLoSn,s (τ,t)
+
√
KR
KR + 1HLoSn,s,1(t)δ(τ−τ1), (3)
where KR is the Rician factor, and τ1 denotes the delay of
the LoS path.
Distinct from the far-ﬁeld model, the LoS component
HLoSn,s,1(t) in the near-ﬁeld regime is formulated based on the
precise Euclidean distance between antenna elements:
HLoSn,s,1(t) = Γn,s· exp
(
−j2π|⃗ rn,s|λ0
)
· exp(j2πνn,st). (4)
Here, |⃗ rn,s| represents the exact distance between the s-th
transmit element and the n-th receive element, and λ0 is
the carrier wavelength. The scalar term Γn,s incorporates the
combined effect of path loss, transmit and receive antenna ﬁeld
patterns, and polarization projection matrices dependent on the
LoS direction. νn,s denotes the Doppler frequency shift.
Crucially, the phase term exp(−j2π|⃗ rn,s|/λ0) inherently
captures the spherical wavefront curvature, as this element-
wise distance is jointly determined by the user’s angle
and distance. This non-linear phase structure serves as the
fundamental motivation for our proposed beam prediction
framework: the objective of near-ﬁeld beamforming is to select
a codeword that compensates for these non-linear geometric
phase differences. Moreover, this spherical distance based
representation is generic: Since this formulation relies strictly
on the physical geometry of propagation, it provides a broadly
applicable representation for near-ﬁeld channels valid for any
ELAA systems governed by spherical wave physics.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15153
Similarly, the NLoS component is modeled as a sum of
contributions from L scattering clusters or subpaths:
HNLoSn,s (τ,t) =
L∑
l=1
βn,s,l· exp
(
−j2π|⃗ rn,s,l|λ0
)
· exp(j2πνn,s,lt)·δ(τ−τl), (5)
where|⃗ rn,s,l| is the total geometric path length of the l-th
NLoS subpath between the s-th transmit element and the n-
th receive element, and τl is its corresponding delay. νn,s,l
denotes the Doppler frequency shift of the l-th NLoS sub-
path. The coefﬁcient βn,s,l is the element dependent complex
path weight that accounts for the large scale attenuation, the
cluster and subpath power, the antenna ﬁeld patterns, and the
polarization coupling associated with the l-th subpath. This
formulation ensures that both LoS and NLoS components
share the same near-ﬁeld mechanism with the spherical wave
assumption.
1) OFDM-Domain Channel Representation: The
time–delay channel model in (3) can be transformed to
the OFDM subcarrier domain by taking the Fourier transform
with respect to delay. Let the subcarrier spacing be ∆f
and the k-th subcarrier frequency be fk = fc +k∆f with
k = 0, 1,...,K − 1. The frequency-domain channel between
the s-th transmit element and the n-th receive element on
subcarrier k at time t is given by
Hn,s[k,t] =
∫ ∞
−∞
Hn,s(τ,t) e−j2πfkτ dτ. (6)
Substituting (3) into (6) and using the fact that the LoS term
contains a Dirac impulse at τ =τ1 yields
Hn,s[k,t] =
√
1
KR + 1
∫
HNLoSn,s (τ,t) e−j2πfkτ dτ
| {z }
HNLOSn,s [k,t]
+
√
KR
KR + 1 HLoSn,s,1(t)e−j2πfkτ1. (7)
In practical channel generation and simulation, the NLoS
component is commonly represented by a ﬁnite set of discrete
delay taps (clusters/subpaths). Let the NLoS part be modeled
as
HNLoSn,s (τ,t) =
L∑
l=1
βn,s,l(t)δ(τ−τl),
where βl(t) and τl denote the complex gain and the delay of
thel-th NLoS tap (cluster or subpath). The OFDM-frequency-
domain NLoS contribution then becomes
HNLOSn,s [k,t] =
L∑
l=1
βn,s,l(t)e−j2πfkτl. (8)
Combining (7) with (8), the per-subcarrier channel used in the
OFDM system is
Hn,s[k,t] =
√
1
KR + 1
L∑
l=1
βn,s,l(t)e−j2πfkτl
+
√
KR
KR + 1HLOSn,s,1(t)e−j2πfkτ1. (9)
Since each user is equipped with a single antenna, the
receive-antenna indexn can be dropped. Denote by Hs[k,t] ≜
Hn0,s[k,t] the frequency-domain channel between the s-th BS
antenna element and the (single-antenna) user on subcarrier k
at time t, where n0 indicates the only receive element. The
BS-to-user channel thus admits the vector form
h[k,t] =
[
H1[k,t], H2[k,t], ..., HNBS[k,t]
]
∈ C1×NBS,
(10)
which is the frequency-domain row-vector channel used in
the OFDM-based downlink expressions (e.g., (1)) by replacing
hdlu,k with h[k,t] when referring to the considered user.
C. Problem Formulation
The key task is to determine the analog precoder FRF
from a near-ﬁeld codebook, while the digital precoder can be
obtained using conventional methods such as zero-forcing (ZF)
or minimum mean-squared error (MMSE). Due to hardware
constraints, each column of FRF must be selected from a ﬁnite
codebook. Unlike the discrete Fourier transform (DFT)-based
far-ﬁeld codebook, the near-ﬁeld codebook is constructed
under the spherical-wave assumption, incorporating both angu-
lar and distance domains [7], [8], [12], [13]. Speciﬁcally, the
codebook is deﬁned as
N =
{
b(ψs,rm)
⏐⏐ s = 1,...,N BS; m = 1,...,M }, (11)
where ψs and rm denote the sampled angle and distance,
respectively. The steering vector b(ψs,rm)∈ CNBS×1 associ-
ated with the direction ψs and distance rm is expressed as
b(ψs,rm) = 1√NBS
[
ej 2πλ (r(1)m−rm),...,e j 2πλ
(
r
(NBS )m −rm)]T,
(12)
wherer(s)m denotes the distance from the s-th antenna element
(s = 1, 2,...,N BS) to the sampling point (ψs,rm), and λ is
the carrier wavelength.
The downlink analog precoder design can thus be formu-
lated as a beam training problem. For user u, the optimal
codeword is chosen to maximize its effective beamforming
gain across all K subcarriers:
max
f RFu ∈N gu, g u =
K∑
k=1
⏐⏐hdlu,kfRFu ⏐⏐. (13)
However, the near-ﬁeld codebook contains a signiﬁcantly
larger number of codewords compared to the far-ﬁeld case, due
to the additional distance dimension. Exhaustively searching
for the optimal codeword not only incurs excessive pilot
overhead but also lowers the likelihood of ﬁnding the best
beam in practical systems. This challenge becomes even more
critical for extremely large-scale antenna arrays (ELAA). To
overcome this, we recast the beam selection process as a
end-to-end beam prediction problem. Speciﬁcally, the user
transmits uplink pilot signals, and the BS employs a large
model to directly predict the near-ﬁeld codeword for the
next frame based on historically received pilot signals. This
approach reduces pilot overhead while enabling timely and
accurate beam selection.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

15154 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. Transmission organization in 5G NR.
III. GPT-2 B ASED NEAR -FIELD BEAM
PREDICTION SCHEME
A. 5G NR Frame Structure and SRS Placement
The proposed near-ﬁeld beam prediction framework itself
is independent of any speciﬁc standard and is applicable to
general TDD systems with periodic uplink pilot. Without loss
of generality, and to ensure the evaluation reﬂects realistic
deployment constraints, we adopt the standardized 5G New
Radio (NR) frame structure speciﬁed by 3GPP as shown in
Fig. 1. In particular, a radio frame has duration of 10 ms and
consists of 10 subframes. With subcarrier spacing (SCS) of
120 kHz (numerologyµ = 3), each subframe contains 2µ = 8
slots and each slot occupies 14 OFDM symbols with normal
cyclic preﬁx [50]. Hence, the slot duration is 0.125 ms and the
frame contains 80 slots in total [50], [51].
In our design, the system operates in TDD mode with a
periodic DL/UL pattern. In this work, we use a repeating
D–S/F–U–D arrangement over slots, where D, U, and S/F
denote downlink, uplink, and ﬂexible (switching) slot types,
respectively. The exact per-symbol DL/UL/Flexible allocation
within each slot follows the 3GPP NR slot-format framework
[50]. This setting captures the symbol-level ﬂexibility of NR
while matching practical deployments.
For uplink channel sounding, we transmit the sounding
reference signal (SRS) in the last n OFDM symbols of each U
slot, enabling the BS to estimate wideband CSI and perform
near-ﬁeld beam prediction. According to 3GPP TS 38.211, the
SRS time-domain allocation resides within the last six symbols
of a slot; common conﬁgurations allocate N SRSsymb∈{1, 2, 4}
symbols starting from symbol index l0∈{8,..., 13} so that
the SRS remains in the slot tail [50]. In this paper, we set
n =N SRSsymb = 4,
which corresponds to allocating SRS over symbols l0 =
10, 11, 12, and 13, i.e., the last four OFDM symbols of
each uplink slot. This conﬁguration is standard-compliant and
widely used in practice [52].
The above frame and SRS design ensures that our near-
ﬁeld beam prediction uses measurements consistent with NR
physical-layer timing and resource mapping while keeping the
pilot overhead low. Under this conﬁguration, a radio frame
thus provides a total of 80 OFDM symbols available for SRS
transmission per frame.
B. Uplink Pilot Transmission Strategy
To enable the BS to acquire sufﬁcient channel informa-
tion for near-ﬁeld beam prediction, we design a practical
uplink pilot transmission strategy that includes the standard-
compliantpilot sequence, the analog precoder design, and the
digital precoder design. The overall idea is to maintain low
pilot overhead while ensuring the received pilot signals contain
stable and sufﬁcient information for the large model to perform
near-ﬁeld beam prediction. It is worth noting that the strategy
described here corresponds to the pilot transmission scheme
within a single radio frame. Moreover, to ensure mutual
orthogonality among users, different SRS ports and cyclic
shift mechanisms can be employed as speciﬁed in the 5G NR
standard [50], thus assuming that pilot transmission and beam
prediction for each user are independent.
1) Standard-Compliant Pilot Sequence: Each user trans-
mits SRS during the last four OFDM symbols of the uplink
slot. For each user, the pilot sequence on each OFDM symbol
is generated by a ZC sequence of length K, where K is the
number of subcarriers. The ZC root index is varied across
OFDM symbols to further improve the orthogonality and
frequency diversity. Speciﬁcally, the pilot matrixXzc∈ CK×T
pilot OFDM symbols is constructed as
Xzck,t = 1√K exp(−jπrtk(k +η)K ), (14)
wherert denotes the ZC root index for thet-th OFDM symbol,
andη = 0 (resp.η = 1) when K is odd (resp. even). The root
indices{rt} are chosen to be coprime with K, ensuring good
correlation properties. The adoption of ZC sequences in this
work is primarily motivated by standard alignment. In practical
5G NR systems, ZC-based sequences are widely used for
SRS transmission due to their constant-envelope property and
well-established implementation advantages. The ZC sequence
is also adopted due to its frequency-varying phase structure,
which can help provide stable and diverse observations for
feature extraction. By employing ZC sequences, our simulation
setup remains consistent with the 5G NR beam management
framework, rather than introducing pilot structures that deviate
from standardized practice [51]. It is worth noting, however,
that the proposed framework is not strictly dependent on
ZC sequences. Other frequency-variant pilot structures, such
as random QPSK or orthogonal DFT sequences, are equally
applicable as veriﬁed in our ablation studies.
2) Analog Precoder Design: During pilot transmission, the
analog precoder is constructed from a widebeam codebook that
is derived from the far-ﬁeld DFT codebook. Speciﬁcally, each
widebeam codeword is generated by combining v adjacent
DFT codewords and then normalizing the phase of each
antenna element to satisfy the constant-modulus constraint
imposed by hardware. The g-th widebeam codeword is given
by
fRF,g = 1√NBS exp
(
j∠
(
1
v
v−1∑
i=0
fDFT, (g−1)v+i+1
))
, (15)
where fDFT,m denotes the m-th DFT codeword of length
NBS, v is the grouping factor, and G is the total number of
widebeam codewords.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15155
Since the BS is equipped with only NRF RF chains, it can
simultaneously activate at most NRF widebeam codewords
per OFDM symbol. Therefore, the widebeam codewords are
grouped in order, and NRF beams are probed in each OFDM
symbol until the entire codebook is swept. The analog pre-
coder corresponding to the t-th OFDM pilot symbol is then
FRF,t =
[
fRF, (t−1)NRF+1, fRF, (t−1)NRF+2, ..., fRF,tN RF
]
(16)
where t = 1 ,..., ⌈G/NRF⌉. In this way, approximately
G/NRF OFDM symbols are required to exhaustively probe
all widebeam codewords.
It is worth highlighting the motivation behind constructing
the analog precoder from widebeam codewords. The received
pilot signals under these widebeams contain sufﬁcient spatial
information to infer the near-ﬁeld beam index, although their
nonlinear mapping is highly complex [32], [53]. Compared
with exhaustive narrow-beam scanning, the number of wide-
beam codewords G is much smaller, which greatly reduces
the overhead required to cover the entire angular space.
Moreover, these widebeams are designed to provide complete
coverage of the spatial domain without the need to switch
off subsets of antenna elements, which is often required in
conventional widebeam codebooks. This property makes the
proposed widebeam codebook more efﬁcient and hardware-
friendly for practical near-ﬁeld channel sounding.
3) Digital Precoder Design: In addition to analog beam
sweeping, we introduce frequency-varying digital precoding to
further exploit the frequency-domain resources. The idea is to
assign different orthogonal directions on different subcarriers,
so that the BS receives richer channel observations.
Let Q∈ CNRF×NRF denote the a NRF-dimensional unitary
DFT matrix, whose columns are NRF mutually orthogonal
basis vectors. For the k-th subcarrier and the t-th pilot OFDM
symbol, the digital precoder is deﬁned as
FBB,k,t = Q(:,Ik), (17)
whereIk is the index set of selected columns. To ensure that
different subcarriers probe different combinations of direc-
tions, we use a cyclic-shift rule:
Ik =
{
(j +k− 1 modNRF) + 1
⏐⏐j = 0, 1,...,N RF− 1}.
(18)
In other words, the k-th subcarrier takes a shifted version
of the DFT basis compared with the (k− 1)-th subcarrier.
This guarantees that across the entire band, the system cycles
through all orthogonal directions, thereby enhancing the diver-
sity of pilot measurements without introducing extra signaling
overhead.
4) Received Pilot Signal: By jointly applying the analog
and digital precoders, the effective hybrid precoder at the BS
is given by Fhyb,k,t = FRF,tFBB,k,t. The received pilot signal
at the BS corresponding to user u on subcarrier k and OFDM
symbol t can be expressed as
yu,k,t =
√
Pul FHhyb,k,thulu,k,tXzck,t + FHhyb,knk,t, (19)
where hulu,k,t∈ CNBS×1 denotes the uplink channel of user u,
Xzck,t is the transmitted pilot symbol, Pul represents the uplink
pilot power, and nk,t is the noise. Since a TDD system is
considered, the uplink channel hulu,k is the transpose of the
downlink channel hdlu,k due to channel reciprocity.
To collect responses from all G widebeam codewords, the
BS performs a beam sweeping procedure over Tp =G/NRF
symbols. For each subcarrier k, the BS concatenates the
received signals across these Tp symbols to form a widebeam
response vector ¯yu,k = [ yTu,k,1, yTu,k,2,..., yTu,k,Tp]∈ C1×G.
Finally, the BS aggregates the responses from allK subcarriers
into the measurement matrix:
Yu =
[¯yTu,1, ¯yTu,2,..., ¯yTu,K]T∈ CK×G. (20)
This measurement matrix serves as the input feature for the
subsequent large-model-based beam prediction scheme.
In summary, the proposed pilot scheme within one radio
frame occupies G/NRF OFDM symbols. The pilot measure-
ment matrix obtained for the p-th radio frame is denoted by
Yu,p, which will serve as the input feature for the subsequent
large-model-based beam prediction scheme.
C. Proposed GPT-2 Based Near-Field Beam Prediction
Scheme
As discussed in (13), the analog precoder design can be
formulated as a beam training problem, where the goal is to
select, for each user, the near-ﬁeld codeword that maximizes
its effective beamforming gain across all subcarriers. Unlike
far-ﬁeld cases with angular-only codebooks, near-ﬁeld training
requires joint angle–distance search, dramatically enlarging the
codebook and causing prohibitive pilot overhead in ELAA
systems.
To address this challenge, we propose a CNN-GPT2 frame-
work, aiming to replace the costly search procedure with direct
prediction from observed pilot signals. Our primary motivation
for adopting the CNN-GPT2 architecture is its excellent suit-
ability for the considered near-ﬁeld beam prediction problem
with low pilot overhead. Speciﬁcally, on the one hand, we
consider employing the raw pilot signals Yu,p as input to
the neural network. However, it exhibits high dimensionality
and a highly structured property, and is affected by noise
and multipath propagation, which partially masks the effective
features. As a result, directly feeding such raw signals directly
into sequence models is typically inefﬁcient and hinders effec-
tive learning of temporal dependencies [44]. To address this
issue, we employ a CNN, which is widely used as a robust
front-end encoder due to its local connectivity and weight-
sharing properties. Speciﬁcally, CNNs can effectively extract
features from raw noisy inputs and signiﬁcantly reducing
the dimensionality of the input signals [21], [44]. On the
other hand, as the optimal near-ﬁeld beam index is jointly
determined by both angle and distance, its temporal evolution
exhibits a highly non-smooth property [13], [54], [55]. This
necessitates a robust sequence model capable of capturing
long-range dependencies. In this respect, GPT-2 equipped with
a self-attention mechanism is capable of performing global
temporal inference on extracted embeddings, making it well-
suited for predicting beamforming decisions for the next frame
[45]. Moreover, the GPT-2 architecture supports a pre-training
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

15156 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 2. An illustration of the network architecture of CNN-GPT-2.
and ﬁne-tuning paradigm, enabling efﬁcient use of labeled data
and improving robustness and generalization under varying
propagation conditions [46].
These considerations motivate us to recast near-ﬁeld beam
training as a sequence-to-label prediction problem, where the
input is a sequence of pilot signals and the output is the index
of the predicted near-ﬁeld beam. Speciﬁcally, we collect the
uplink pilots from the past P radio frames for each user,
denoted as{Yu,1, Yu,2,..., Yu,P}, and feed them into a GPT-
2 based prediction model. The model then directly outputs the
index of the near-ﬁeld codeword at the next radio frames. This
process can be expressed mathematically as
{
b⋆u,P+1} =fCNN−GPT2(Yu,1,..., Yu,P), (21)
where b⋆u,P+1 denotes the predicted index of the predicted
near-ﬁeld beam index for user u at the next radio frames, and
fCNN−GPT2(·) represents the mapping implemented by the
CNN-GPT-2 model. The complete architecture of CNN-GPT-
2 model is shown in Fig. 2.
1) Preprocessing Module: Before feeding the pilot obser-
vations into the GPT-2 network, a preprocessing step is applied
to ensure that the input is real-valued and properly normalized.
Let the pilot sequence of user u from the past P radio frames
be denoted as
Yu =
[
Yu,1, Yu,2,..., Yu,P
]
∈ CP×K×G. (22)
SinceYu is complex-valued, we ﬁrst separate it into real and
imaginary parts:
~Yu =[ℜ(Yu),ℑ(Yu)]∈ RP×2×K×G. (23)
To further enhance training stability and reduce the impact
of amplitude variations, we apply per-sample normalization.
Speciﬁcally, for each entry z in ~Yu, we compute
ˆz = z−µσ , (24)
where µ and σ denote the mean and standard deviation of
the corresponding sample, respectively. In this way, each
processed input tensor has zero mean and unit variance, i.e.,
ˆYu∈ RP×2×K×G, E[ˆYu] = 0, Var[ˆYu] = 1. (25)
The normalized tensor ˆYu is then passed to the subsequent
CNN-based feature extraction and sequence modeling blocks
of the GPT-2 based prediction framework.
2) CNN-Based Feature Extraction Module: To effectively
extract discriminative features from the preprocessed pilot
tensors, we adopt a CNN with residual connections. The
CNN is designed to compress the high-dimensional pilot
input into a compact feature representation while preserving
key spatial–frequency structures that are relevant for beam
prediction.
a) Residual block: Each residual block consists of two
convolutional layers with batch normalization (BN) and ReLU
activation, followed by a skip connection to improve training
stability. Given an input feature map X ∈ RC×H×W , the
residual block computes
ResBlock(X) = ReLU
(
F(X; Θ) +R(X)
)
, (26)
whereF(·) denotes the stacked convolution–BN–ReLU layers
with learnable parameters Θ, and R(·) is either the identity
mapping or a 1× 1 convolution when downsampling is
required. Dropout is further employed to enhance generaliza-
tion.
b) CNN feature extractor: The overall CNN feature
extractor ﬁrst applies an initial convolution to expand the
channel dimension (here, the term channel refers to the
input feature channels of the CNN, rather than the wireless
communication channel), followed by three residual blocks:
H1 = ResBlock1(X), H2 = ResBlock2(H1),
H3 = ResBlock3(H2). (27)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15157
Here ResBlock1 includes downsampling to reduce spa-
tial dimensions by a factor of two, while ResBlock2 and
ResBlock3 preserve the feature resolution.
c) Global pooling and projection: To generate a ﬁxed-
size feature embedding, we apply adaptive average pooling to
compress each feature map into a spatial grid of size Hp×Wp:
Hpool = Pool(H3)∈ RCp×Hp×Wp, (28)
where Cp denotes the number of feature channels after the
last residual block, and Hp, Wp denote the height and width
of the pooled feature maps, respectively.
The pooled features are ﬂattened and passed through a fully
connected layer with ReLU activation and dropout to obtain
the ﬁnal embedding of dimension Dout:
f = ReLU(W vec(Hpool) + b)∈ RDout, (29)
where vec(Hpool) denotes the vectorization of the pooled
feature tensor Hpool ∈ RCp×Hp×Wp into a column vector
of length CpHpWp, W∈ RDout×(CpHpWp) is the learnable
weight matrix of the fully connected layer, and b∈ RDout is
the corresponding bias term.
d) Output representation: ForP input frames, the CNN
operates on eachp sample individually and outputs a sequence
of feature embeddings:
F = [f1, f2,... fP ]∈ RP×Dout, (30)
which is then fed into the GPT-2 sequence modeling module.
In this way, the CNN serves as a projection head that converts
complex-valued pilot observations into compact, real-valued
feature sequences suitable for temporal prediction.
3) GPT-2 Based Beam Prediction Module: After feature
extraction, the temporal modeling and codeword prediction are
carried out by a GPT-2 style Transformer network. The GPT-
2 model is particularly suitable for this task due to its strong
capability of capturing long-range dependencies in sequential
data, which in our case correspond to the temporal evolution
of pilot measurements across multiple frames.
a) Input embedding and positional encoding: Let F∈
RP×Dout denote the feature sequence obtained from the CNN
module. Here, we set Dout = Demb so that the CNN
output dimension matches the embedding dimension of the
Transformer where Demb is the Transformer embedding size,
ensuring seamless integration between the two modules. For
each time step p, a learnable positional embedding ep ∈
RDemb is added to the input, yielding
zp = fp + ep, (31)
where fp is the CNN feature at step p. A dropout layer is then
applied to improve generalization.
b) Transformer blocks: The core of GPT-2 consists of
stacked Transformer blocks. Each block is composed of a
multi-head self-attention layer followed by a position-wise
feed-forward network (FFN), with residual connections and
layer normalization applied around both components. Denote
the input to the l-th block as Z(l−1) =[z(l−1)1 ,..., z(l−1)P ]T∈
RP×Demb, then the block computes
H(l) = Z(l−1) + MHA(Norm1(Z(l−1))), (32)
Z(l) = H(l) + FFN(Norm2(H(l))), (33)
where MHA(·) denotes multi-head self-attention, and FFN(·)
is the feed-forward module.
c) Multi-head self-attention: Given the normalized input
Z∈ RP×Demb, the query, key, and value matrices are ﬁrstly
computed as
Q = ZWQ, K = ZWK, V = ZWV, (34)
where WQ, WK, WV ∈ RDemb×Demb are learnable projec-
tion matrices.
To realize multi-head attention, the embedding dimension
is divided into Nh heads, each of dimension dh =Demb/Nh.
Speciﬁcally, Q, K, V are reshaped into
Q, K, V∈ RNh×P×dh, (35)
so that attention can be computed in parallel across all heads.
For the j-th head, the scaled dot-product attention is calcu-
lated as
Attnj(Qj, Kj, Vj) = softmax
(
QjK⊤j√dh
)
Vj, (36)
where Qj, Kj, Vj ∈ RP×dh are the query, key, and value
matrices corresponding to head j.
The outputs of all heads are then concatenated along the
last dimension:
A = Concat
(
Attn1, Attn2,..., AttnNh
)
∈ RP×Demb,
(37)
and projected to the original embedding space through a linear
layer (LL):
LL(A) = A WO + bO, (38)
where WO∈ RDemb×Demb is the learnable output projection
matrix.
In summary, multi-head attention enables the model to
jointly attend to information from multiple representation sub-
spaces, enhancing its ability to capture diverse dependencies
across the pilot sequence.
d) Feed-forward network and normalization: The FFN
consists of two layers with ReLU activation in between:
FFN(x) = ReLU(xW1 + b1)W2 + b2. (39)
where x denotes the input feature vector at a given time step,
and W1, W2, b1, and b2 are trainable parameters. Layer
normalization is applied before both the attention and FFN
modules, while residual connections ensure stable gradient
propagation.
e) Output layer: After passing through L Transformer
blocks, the sequence is normalized and projected to the
codebook size. Speciﬁcally, for the last hidden representation
Z(L), the prediction logits are given by
op = z(L)p Wout + bout, op∈ R|N|, (40)
where|N| is the size of the near-ﬁeld codebook. The predicted
codeword index is obtained by applying a softmax classiﬁer
over op.
Thus, the GPT-2 module serves as the temporal predictor
that maps a sequence of pilot-derived features into the most
likely near-ﬁeld beam index at future time instants.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

15158 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
4) Model Training Strategy: Inspired by the BERT
paradigm in natural language processing, we adopt a two-stage
training strategy consisting of pre-training and ﬁne-tuning.
The pre-training stage allows the model to learn general
temporal–spatial representations from large-scale pilot data
through a masking task, while the ﬁne-tuning stage specializes
the model for the downstream beam prediction objective.
Moreover, throughout both stages, the GPT-2 module is
conﬁgured to use a bidirectional (non-causal) self-attention
mechanism, so that the model can aggregate information glob-
ally across the observed pilot sequence. Bidirectional attention
enables the model to more effectively capture global temporal
correlations, long-range dependencies, and beam evolution
patterns embedded in the pilot signals, which are particularly
important for near-ﬁeld scenarios.
a) Pre-training: The objective of the pre-training stage is
to expose the model to large amounts of pilot–beam correspon-
dence data and to encourage it to learn temporal dependencies
across multiple frames. Given the input pilot tensor
X∈ RB×P×2×K×G,
where B is the batch size. We ﬁrst perform random mask-
ing over the temporal dimension. Speciﬁcally, let α denote
the overall masking ratio. A proportion of αP frames are
randomly selected as masked positions. Among these masked
positions, 80% are replaced by all-zero inputs, 10% are substi-
tuted with randomly sampled pilot features, and the remaining
10% are left unchanged. This design prevents the model from
overﬁtting to a trivial “mask token” and encourages it to
robustly capture both local and global temporal correlations.
After masking, the data is passed through the CNN feature
extractor:
F = CNN(Xmasked)∈ RB×P×Dout,
and then into the GPT-2 module, which outputs the prediction
logits:
O = GPT− 2(F)∈ RB×P×|N|,
where O ∈ RB×P×|N| stores the model’s unnormalized
prediction scores, with indices (b,p,n) specifying the batch
index, temporal index, and codeword index, respectively. The
training objective is the cross-entropy loss computed over all
time steps:
Lpre =− 1BP
B∑
b=1
P∑
p=1
log
exp
(
[O]b,p,yb,p
)
∑|N|
n=1 exp
(
[O]b,p,n
),, (41)
where yb,p denotes the ground-truth index of the optimal
near-ﬁeld codeword for user b at frame p and [O]b,p,n denotes
the predicted logit value (before softmax) corresponding to
the n-th codeword in the near-ﬁeld codebook N for batch b
at frame p.
b) Fine-tuning: In the ﬁne-tuning stage, the model is
adapted for the actual prediction task: forecasting the near-
ﬁeld beam index at the next frame given the past P frames.
To this end, we only use the output at the last context position
P :
[O]b,P∈ R|N|,
which already represents the prediction logits over the near-
ﬁeld codebook for batch b. The predicted codeword index for
the (P + 1)-th frame is then obtained as
ˆyb,P+1 = arg maxn
(
[O]b,P,n
)
. (42)
The ﬁne-tuning loss is deﬁned as the cross-entropy between
the predicted logits and the ground-truth index yb,P+1:
Lﬁne =− 1B
B∑
b=1
log
exp
(
[O]b,P,yb,P +1
)
∑|N|
n=1 exp
(
[O]b,P,n
). (43)
In this way, pre-training equips the model with the ability to
learn general pilot–beam patterns under noisy and incomplete
observations, while ﬁne-tuning specializes the model for next-
frame beam prediction with improved accuracy and reduced
overhead.
c) Advantages of the training strategy: The proposed
pre-training and ﬁne-tuning strategy offers the following
advantages:
• Dense supervision: During pre-training, the model
receives feedback from multiple temporal positions
through the masking strategy, allowing it to capture richer
sequential dependencies and converge more smoothly
over time.
• Robustness: By adopting a denoising-style masking
scheme (80/10/10), the network becomes less sensitive
to missing or corrupted pilot signals, showing stronger
resistance to noise and improved generalization across
different channel conditions.
• Label efﬁciency: When ﬁne-tuning, the pre-trained rep-
resentation enables the model to adapt to new tasks with
only a small number of labeled samples, greatly reducing
data requirements and facilitating practical deployment in
real systems.
d) Computational complexity analysis: The computa-
tional complexity of the proposed CNN–GPT-2 framework
consists of two main parts: the convolutional feature extrac-
tion and the GPT-2-based temporal modeling. For the CNN
module, each convolutional layer involves operations with a
complexity proportional to the product of the number of input
channels Cin, output channels Cout, the spatial size of the
feature map H×W , and the squared kernel size Kc2. The
complexity for a single layer is thus O
(
CinCoutKc2HW).
Since the number of convolutional layers LCNN is ﬁxed and
small, and the kernel size Kc is typically small (e.g., 3), this
component scales linearly with the input spatial size and the
number of channels.
For the GPT-2 module, the dominant cost arises from
the multi-head self-attention mechanism. Given a context
length P , embedding dimension Demb, and number of lay-
ers LGPT−2, the complexity of each attention block is
O(P 2Demb) due to the pairwise attention computation, while
the feed-forward network within each layer adds an additional
O(PD 2emb). Stacking LGPT−2 such blocks yields an overall
complexity ofO
(
LGPT−2
(
P 2Demb +PD 2emb)).
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15159
TABLE I
DEFAULT SYSTEM PARAMETERS
Combining both modules, the overall computational com-
plexity of the proposed framework is expressed as:
O
(LCNN∑
𝓁=1
C(𝓁)in C(𝓁)outKc(𝓁)2H(𝓁)W (𝓁)
+LGPT−2
(
P 2Demb +PD 2emb)). (44)
IV. S IMULATION RESULTS
In this section, we present simulation results to evaluate
the performance of the proposed CNN–GPT-2 based near-ﬁeld
beam prediction scheme. The simulations are conducted under
a standardized 5G NR frame structure and a channel model
highly consistent with 3GPP TR 38.901 Release 19. We ﬁrst
describe the channel generation settings and network model
conﬁgurations used in the experiments, and then provide
detailed performance comparisons with conventional beam
training baselines.
A. Simulation Parameter Settings
The simulation setup follows the 3GPP TR 38.901 Urban
Macrocell (UMa) LoS scenario [56]. All channel realizations
are generated using the QuaDRiGa (Quasi Deterministic Radio
Channel Generator) platform, which provides a geometry
based stochastic channel modeling framework that is highly
aligned with TR 38.901 in terms of scenario conﬁguration,
large scale parameter generation, and cluster and subpath
construction [57], [58]. To capture near ﬁeld propagation, we
enable the enhanced QuaDRiGa spherical wave feature, such
that the phase of each path is computed from the element-
wise distances between antenna elements rather than a plane
wave approximation. This setting naturally introduces near-
ﬁeld spherical wave effect, while preserving the standardized
TR 38.901 statistical structure. Users are randomly distributed
within an angular range of [−60◦, 60◦] and a distance range of
[5, 20] meters from the base station, with velocities uniformly
sampled from [30, 100] km/h. The detailed channel and sys-
tem parameters are summarized in Table I.
For pilot transmission, we adopt a widebeam analog precod-
ing codebook, where each widebeam is obtained by combining
v = 4 adjacent DFT beams into a single probing beam.
With NBS = 256 antennas and v = 4 , the total widebeam
codebook size is G = 64. Hence, in each radio frame, only
G/NRF = 64/8 = 8 OFDM symbols are required to complete
the widebeam sweeping process, which keeps the pilot over-
head extremely low. The near-ﬁeld codebook is generated by
jointly sampling the angular domain with NBS = 256 antenna
steering directions and the distance domain with ﬁve uniformly
distributed sampling points in [5, 20]m. Hence, the total size
of the near-ﬁeld codebook is |N| = 1280.
During training, the proposed CNN–GPT-2 framework ﬁrst
undergoes pre-training on 80k samples, followed by ﬁne-
tuning on an additional 20k samples. In contrast, all baseline
models are directly trained on 100k labeled samples without
pre-training. In the ﬁne-tuning stage, the CNN encoder and the
ﬁrst Transformer block are frozen to preserve low-level spatial
feature extraction, while the remaining GPT-2 layers are fully
trainable to capture temporal dependencies. This conﬁguration
balances parameter efﬁciency and representation adaptability,
facilitating fast convergence during ﬁne-tuning. Moreover, the
Adam optimizer is adopted with a learning rate of 4× 10−4
and a batch size of 256. The pre-training and ﬁne-tuning stages
are conducted for 60 and 20 epochs, respectively. During pre-
training, a default temporal masking ratio of 0.3 is applied
to encourage robust representation learning under incomplete
observations.
On the learning side, the network parameters are selected
to balance modeling capacity and computational efﬁciency.
The CNN module extracts features of dimension Dout =
512, which is matched to the embedding dimension of the
Transformer to enable seamless integration. The GPT-2 model
is conﬁgured with L = 4 layers and Nh = 8 attention
heads, which provides sufﬁcient representational power for
capturing long-term dependencies without incurring excessive
complexity.
The detailed model parameters are summarized in Table II.
B. Evaluation Metrics and Baseline Algorithms
To validate the effectiveness of the proposed CNN–GPT-2
based near-ﬁeld beam prediction framework, we adopt three
evaluation metrics and compare our approach with several
representative baselines.
1) Evaluation Metrics:
• Prediction Accuracy: The ratio of correctly predicted
beams over the total number of test samples. Formally, it
is deﬁned as
Acc = 1B
B∑
b=1
1
(
ˆyb =yb
)
, (45)
whereB is the number of test samples, yb is the ground-
truth optimal codeword index, ˆyb is the predicted index.
Here, 1(·) denotes the indicator function, which outputs
1 if the condition is satisﬁed and 0 otherwise.
• Top-2 Accuracy: This metric evaluates whether the true
optimal codeword lies within the two most probable
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

15160 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE II
CNN–GPT-2 M ODEL PARAMETERS
predictions. It is deﬁned as
AccTop2 = 1B
B∑
b=1
1
(
yb∈ Top2(ˆpb)), (46)
where ˆpb = [ O]b,P denotes the predicted probabil-
ity distribution over the codebook for sample b, and
Top2(·) returns the indices of the two highest-probability
codewords. The Top-2 accuracy provides a practically
meaningful measure: if the optimal beam is contained
within the top two candidates, the BS can perform a
lightweight second-stage beam training by probing only
these two beams. This enables near-optimal beam align-
ment with minimal additional pilot overhead compared
to exhaustive search.
• Normalized Beamforming Gain (NBG): To assess
link-level performance, we compute the normalized
beamforming gain, which measures how close the pre-
dicted beam is to the optimal one in terms of received
signal power:
NBG =
∑K
k=1
⏐⏐⏐hdlu,kfpredu ⏐⏐⏐2
max
f RFu ∈N
∑K
k=1
⏐⏐⏐hdlu,kfRFu ⏐⏐⏐2. (47)
A higher NBG indicates that the predicted beam achieves
signal power close to the optimal one on average across
all subcarriers.
2) Comparison Baselines: We compare our proposed
method with the following baselines:
• RNN-based beam prediction: A recurrent neural net-
work is trained to capture temporal dependencies in pilot
sequences for predicting the optimal codeword index.
• LSTM-based beam prediction: A long short-term mem-
ory network is employed to improve long-term memory
capability compared to vanilla RNNs.
• GRU-based beam prediction: A gated recurrent unit
network is adopted as a lighter alternative to LSTMs,
balancing performance and complexity.
• CNN–GPT-2 (direct training): A variant of our pro-
posed CNN–GPT-2 architecture that is trained directly
on labeled beam prediction data without the pre-
training–ﬁne-tuning paradigm. This baseline highlights
the beneﬁts of the designed pre-training strategy by
providing a fair comparison between direct supervised
learning and the proposed two-stage training scheme.
• Perfect-CSI based exhaustive search (Upper bound):
An upper bound benchmark that selects the optimal
near-ﬁeld codeword by an exhaustive search overN using
the perfect channel at target frame:
b
⋆
u = arg maxb∈N
1
K
K∑
k=1
⏐⏐bHhulu,k⏐⏐2. (48)
• Noisy exhaustive search (high-overhead reference): A
strong reference that tests every codeword at the target
frame under noise and selects the one with the largest
beamformed power:
ˆbu = arg maxb∈N 1K
K∑
k=1
⏐⏐√Pul bHhulu,k + bHnu,k⏐⏐2.
(49)
3) Ablation Baselines: To further analyze the effectiveness
of each component in the proposed framework, we also
consider the following ablation settings:
• Varying mask ratioα: We investigate different masking
ratios in the pre-training stage (e.g., α = 0.2, 0.4, 0.6) to
evaluate how the amount of masked frames affects the
representation learning and downstream beam prediction
accuracy.
• Supervision scope (Masked-only loss): Instead of com-
puting the loss across all time steps, we consider the
variant that only supervises the masked positions during
pre-training. This ablation highlights the beneﬁt of lever-
aging both masked and unmasked positions for stable
optimization.
• Simpliﬁed pilot transmission: We replace the proposed
Zadoff–Chu based pilots and frequency-varying digi-
tal precoding with simpliﬁed pilots (all-ones sequence,
identity digital precoder). This variant evaluates the per-
formance gain brought by the carefully designed pilot
transmission scheme.
C. Simulation Results
In this subsection, we present the performance of the pro-
posed CNN–GPT-2 based near-ﬁeld beam prediction scheme
and compare it with several baseline algorithms, including
RNN, LSTM, GRU, and the direct training. Furthermore,
we conduct ablation studies to evaluate the impact of key
components such as the pilot transmission design and the pre-
training strategy.
Fig. 3 compares the convergence of the proposed pre-
training + ﬁne-tuning scheme with direct training. The
proposed scheme rapidly reaches over 80% validation accuracy
within ﬁve epochs and stabilizes around 83% ∼ 84%. In
contrast, direct training requires more than 30 epochs to
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15161
Fig. 3. Illustration of the convergence.
approach similar performance and remains unstable around
70%. These results conﬁrm that pre-training provides a favor-
able initialization, leading to faster convergence, higher ﬁnal
accuracy, and reduced training cost.
The superior convergence of our approach highlights two
main advantages. First, it reduces the overall training time and
computational cost, which is crucial when handling large-scale
near-ﬁeld datasets. Second, it improves robustness to training
instability, as evidenced by the stable accuracy curve compared
to the oscillatory behavior of direct training.
Fig. 4(a) illustrates the prediction accuracy of different
algorithms as a function of the uplink pilot noise power. The
proposed CNN–GPT-2 with pre-training consistently achieves
the highest accuracy across all noise levels, reaching over 85%
when the noise power decreases below−113 dBm. In contrast,
conventional RNN, LSTM, and GRU models show slower per-
formance growth with SNR, and their accuracy saturates below
that of our scheme. The direct training CNN–GPT-2 baseline
also lags behind, especially in the low-SNR regime, conﬁrming
that pre-training provides more robust initialization.
Fig. 4(b) presents the Top-2 prediction accuracy, which
evaluates the probability that the true optimal beam is con-
tained within the top two predicted candidates. This metric
is particularly relevant in practice, as a small number of
secondary pilot measurements can be used to identify the ﬁnal
optimal beam. The results show that the proposed CNN–GPT-
2 scheme achieves near-perfect Top-2 accuracy (above 97%)
when the noise power is below −110 dBm, substantially
outperforming recurrent baselines. Even at higher noise levels,
the proposed scheme maintains a clear advantage, reﬂecting its
strong ability to capture temporal dependencies and generate a
reliable candidate set for efﬁcient near-ﬁeld beam reﬁnement.
Fig. 4(c) presents the normalized beamforming gain (NBG)
performance under different uplink noise power values. The
proposed CNN–GPT-2 model with pre-training achieves the
highest NBG across all noise levels, exceeding 0.95 when
the noise power is below −110 dBm. In contrast, the directly
trained CNN–GPT-2 and recurrent baselines (RNN, LSTM,
GRU) show a clear degradation, particularly in the low-SNR
regime. The performance gap between the proposed and direct-
training variants highlights the beneﬁt of the pre-training stage
in learning robust temporal dependencies from noisy pilot
signals. Moreover, the relatively smooth NBG curve of the
proposed model indicates stronger resilience to channel noise
and better generalization across varying SNR conditions.
To further assess how close the proposed framework oper-
ates relative to the fundamental performance limits, Fig. 4(a)
through Fig. 4(c) also include two exhaustive-search-based
benchmarks: the perfect-CSI based exhaustive search (rep-
resenting the upper bound) and the noisy exhaustive search
(representing the high-performance but high-overhead refer-
ence). As illustrated in Fig. 4(c), the proposed CNN–GPT-2
scheme achieves a Normalized Beamforming Gain (NBG) of
approximately 95.8% as the noise power decreases, which
is remarkably close to the perfect-CSI upper bound. This
indicates that even in cases where the predicted index does not
perfectly match the ground truth, the predicted beam remains
within the high-gain main lobe of the optimal beam. Although
performance gaps exist compared to noisy exhaustive search
in high-noise environments, our framework relies solely on
historical pilot signals, requiring only one-twentieth of the
pilot resources needed for exhaustive search.
Fig. 5(a), Fig. 5(b), and Fig. 5(c) illustrate the abla-
tion results under different masking ratios α and design
variations. Speciﬁcally, Fig. 5(a) and Fig. 5(b) show the pre-
diction accuracy and top-2 accuracy versus noise power, while
Fig. 5(c) presents the corresponding normalized beamforming
gain (NBG). The proposed conﬁguration with α = 0.3
achieves the best overall performance across all noise levels,
demonstrating that an appropriate masking ratio effectively
balances information retention and contextual learning. When
α is too small, the model receives insufﬁcient self-supervised
signal, limiting its generalization, whereas an excessively
large α makes the prediction unstable due to the scarcity of
visible context. The “Masked-only Supervision” variant yields
lower accuracy, conﬁrming that incorporating both masked and
unmasked frames in the loss computation stabilizes optimiza-
tion and improves temporal consistency.
Notably, the “Simpliﬁed Pilot” conﬁguration exhibits poor
performance at high noise levels (e.g., above −102 dBm),
while remaining reasonably effective in low-noise conditions.
This phenomenon is mainly attributed to the signiﬁcant reduc-
tion of information in the observed signal after removing
the pilot structure and digital precoding of the frequency
variation. Speciﬁcally, the received signal exhibits weaker
and more uniform spatio-temporal variations, rendering the
model incapable of forming stable, effective features at low
SNR ratios to exhibit robustness against noise. By contrast,
the proposed scheme can provide more reliable and feature-
rich observations for neural network learning, which translates
into signiﬁcantly enhanced robustness under various noise
conditions.
To further assess the dependence of the proposed framework
on the speciﬁc pilot waveform, we conducted an extended
ablation study by replacing the standard ZC sequence with
random QPSK pilots and orthogonal DFT-based pilots, while
maintaining identical power and resource allocation. The
comparative numerical results are summarized in Table III.
It is observed that the performance variations among the
ZC, QPSK, and DFT schemes are marginal across the entire
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

15162 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 4. Comparison of beam prediction performance among different baseline models under various noise power levels.
Fig. 5. Ablation study of the proposed CNN–GPT-2 framework under different conﬁgurations.
Fig. 6. Generalization evaluation of the proposed CNN–GPT-2 framework across different scenarios: (a) prediction performance under varying user speeds,
(b) cross-channel adaptation under different K-factors, and (c) transferability to the UMi channel with varying noise power.
tested noise regime. The ZC, QPSK, and DFT pilot sequence
all possess distinct frequency-variant structures (i.e., varying
phases or symbols across subcarriers). This inherent spectral
diversity ensures that they all provide sufﬁciently rich spectral
excitation and stable observation features for the network.
Consequently, this conﬁrms that the predictive capability of
the proposed CNN-GPT2 model derives from learning the
intrinsic near ﬁeld propagation patterns rather than overﬁtting
to a speciﬁc waveform. We therefore retain the ZC sequence
in our ﬁnal design primarily for its alignment with 5G NR
standards and favorable hardware properties, such as low peak-
to-average power ratio (PAPR), rather than strictly algorithmic
necessity.
Fig. 6(a) illustrates the prediction accuracy of different
models under varying user speeds. As the mobility increases
from 30 km/h to 110 km/h, all schemes exhibit a gradual
decline in performance due to the faster channel variations
and reduced temporal correlation across frames. Nevertheless,
the proposed CNN–GPT-2 model consistently outperforms
the baseline methods at all speeds, maintaining an accuracy
above 0.80 even at 110 km/h. This robustness stems from the
GPT-2 module’s strong temporal modeling capability, which
effectively captures long-term dependencies and mitigates the
channel decorrelation caused by user motion. Moreover, it
can be observed that the two exhaustive search approaches
remain unaffected by user speed, as they employ exhaustive
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15163
TABLE III
PERFORMANCE COMPARISON OF DIFFERENT PILOT
WAVEFORMS ACROSS NOISE LEVELS
searches of the target frame’s channel rather than predictive
algorithms.
1) Model Generalization Across Channel Conditions:
Fig. 6(b) illustrates the prediction accuracy of different
schemes under channels with varying Rician KR-factors. The
proposed CNN–GPT-2 model was pre-trained on channels
with KR = 10 dB using 80k samples, and subsequently
ﬁne-tuned with 20k samples for each new KR-factor. Mean-
while, to ensure a fair comparison regarding data availability,
all baseline models (CNN–GPT2 with direct training, RNN,
LSTM, and GRU) were trained from scratch using the identical
total number of samples (i.e., 100k samples per condition,
equivalent to the sum of the pre-training and ﬁne-tuning
sets). As shown in the ﬁgure, the proposed pretrain–ﬁnetune
framework consistently achieves higher accuracy across a wide
range of KR-factors. In particular, the performance gain is
more pronounced at lower KR values, where the channel
exhibits stronger multipath components and higher nonlin-
earity. This demonstrates that the proposed model effectively
captures the underlying temporal–spatial correlations of near-
ﬁeld propagation and generalizes well to unseen scattering
conditions.
2) Cross-Scenario Transferability: To further evaluate the
cross-environment adaptability, Fig. 6(c) compares the pre-
diction accuracy under the 3GPP UMi channel model. The
proposed model was ﬁrst pre-trained on UMa channel data
(80k samples) and then ﬁne-tuned with only 20k UMi samples,
whereas all baseline models were trained directly on 100k
UMi samples. As observed, the proposed approach achieves
consistently superior performance, particularly in the low-SNR
regime, indicating its strong transferability across channel
environments. This result highlights that the proposed large-
model-based framework can effectively leverage knowledge
learned from one propagation scenario to another, thereby
exhibiting strong generalization and robustness to channel
variations.
3) Discussion on Practical SRS Impairments: Finally, it
is worth noting that the simulation results presented in this
section are obtained under idealized SRS assumptions, includ-
ing full bandwidth allocation, ﬁxed transmit power, and the
absence of multi-user collisions. Nevertheless, in practical sys-
tems, SRS impairments such as partial bandwidth allocation,
power control, and potential multi-user collisions may degrade
the quality of the received pilot signals and consequently affect
beam prediction performance. For instance, partial bandwidth
allocation reduces the effective frequency-domain observa-
tion dimension and weakens frequency-dependent variations,
power control introduces time-varying SNR and amplitude
ﬂuctuations, and multi-user collisions may contaminate the
pilot measurements through structured interference. Although
these effects are not explicitly modeled in the current simula-
tions, the proposed framework inherently allows extensions
toward improved robustness. Speciﬁcally, partial bandwidth
allocation can be accommodated through bandwidth-related
training, such as randomly masking portions of subcarriers
during training. The impact of power control can be mitigated
by introducing random gain and dynamic SNR into the train-
ing data. Interference caused by collisions can be alleviated
through SRS scheduling, which allocates different resources
(time-frequency blocks and ports). A systematic incorporation
of these practical impairments into the end-to-end learning and
evaluation framework is an important and meaningful direction
for future work.
V. C ONCLUSION
This paper proposed an end-to-end CNN–GPT-2 framework
for near-ﬁeld beam prediction in extremely large-scale antenna
systems. By integrating convolutional spatial feature extrac-
tion with GPT-2-based temporal modeling, the framework
efﬁciently infers near-ﬁeld beam indices from uplink pilots,
achieving near-optimal performance without exhaustive beam
search. A BERT-inspired pre-training and ﬁne-tuning strategy
was developed to enhance convergence stability and general-
ization. Moreover, a practical uplink pilot transmission scheme
combining Zadoff–Chu sequences, widebeam analog precod-
ing, and frequency-dependent digital precoding effectively
reduces pilot overhead while preserving rich spatial–frequency
information. Simulation results under standardized 5G NR and
3GPP channel models conﬁrmed that the proposed method
achieves superior prediction accuracy and robustness com-
pared with RNN-, LSTM-, and GRU-based baselines.
REFERENCES
[1] S. A. Busari, K. M. S. Huq, S. Mumtaz, L. Dai, and J. Rodriguez,
“Millimeter-wave massive MIMO communication for future wireless
systems: A survey,” IEEE Commun. Surveys Tuts., vol. 20, no. 2,
pp. 836–869, 2nd Quart., 2018.
[2] T. S. Rappaport et al., “Millimeter wave mobile communications for 5G
cellular: It will work!,” IEEE Access, vol. 1, pp. 335–349, 2013.
[3] C.-X. Wang, Z. Lv, X. Gao, X. You, Y . Hao, and H. Haas, “Pervasive
wireless channel modeling theory and applications to 6G GBSMs for all
frequency bands and all scenarios,” IEEE Trans. Veh. Technol., vol. 71,
no. 9, pp. 9159–9173, Sep. 2022.
[4] C.-X. Wang et al., “An enhanced 6G pervasive channel model towards
standardization,” Sci. China Inf. Sci., vol. 68, no. 6, Jun. 2025, Art. no.
162301.
[5] Q. Xue et al., “A survey of beam management for mmWave and THz
communications towards 6G,” IEEE Commun. Surveys Tuts., vol. 26,
no. 3, pp. 1520–1559, 3rd Quart., 2024.
[6] Y . Han, S. Jin, M. Matthaiou, T. Q. S. Quek, and C.-K. Wen, “Toward
extra large-scale MIMO: New channel properties and low-cost designs,”
IEEE Internet Things J., vol. 10, no. 16, pp. 14569–14594, Aug. 2023.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

15164 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[7] Y . Liu, C. Ouyang, Z. Wang, J. Xu, X. Mu, and A. L. Swindlehurst,
“Near-ﬁeld communications: A comprehensive survey,” IEEE Commun.
Surveys Tuts., vol. 27, no. 3, pp. 1687–1728, Jun. 2025.
[8] M. Cui and L. Dai, “Channel estimation for extremely large-scale
MIMO: Far-ﬁeld or near-ﬁeld?,” IEEE Trans. Commun., vol. 70, no. 4,
pp. 2663–2677, Apr. 2022.
[9] H. Lin, Y . Li, G. Chen, Z. Liu, and Y . Huang, “Performance analysis for
mmWave cell-free access network based on terahertz backhaul,” IEEE
Commun. Lett., vol. 29, no. 6, pp. 1181–1185, Jun. 2025.
[10] Y . Li and A. S. Madhukumar, “Hybrid near- and far-ﬁeld THz
UM-MIMO channel estimation: A sparsifying matrix learning-aided
Bayesian approach,” IEEE Trans. Wireless Commun., vol. 24, no. 3,
pp. 1881–1897, Mar. 2025.
[11] W. Yi, W. Zhiqing, and F. Zhiyong, “Beam training and tracking in
mmWave communication: A survey,” China Commun., vol. 21, no. 6,
pp. 1–22, Jun. 2024.
[12] M. Cui and L. Dai, “Near-ﬁeld wideband channel estimation for
extremely large-scale MIMO,” Sci. China Inf. Sci., vol. 66, no. 7, Jun.
2023, Art. no. 172303.
[13] M. Cui, Z. Wu, Y . Lu, X. Wei, and L. Dai, “Near-ﬁeld MIMO
communications for 6G: Fundamentals, challenges, potentials, and future
directions,” IEEE Commun. Mag., vol. 61, no. 1, pp. 40–46, Jan. 2023.
[14] L. Chen, S. Zhou, and W. Wang, “mmWave beam tracking with spatial
information based on extended Kalman ﬁlter,” IEEE Wireless Commun.
Lett., vol. 12, no. 4, pp. 615–619, Apr. 2023.
[15] S. Jayaprakasam, X. Ma, J. W. Choi, and S. Kim, “Robust beam-tracking
for mmWave mobile communications,” IEEE Commun. Lett., vol. 21,
no. 12, pp. 2654–2657, Dec. 2017.
[16] H.-L. Song and Y .-C. Ko, “Beam alignment for high-speed UA V
via angle prediction and adaptive beam coverage,” IEEE Trans. Veh.
Technol., vol. 70, no. 10, pp. 10185–10192, Oct. 2021.
[17] J. Zhang, S. Gao, X. Feng, H. Yang, and G. Sun, “An accurate
beam-tracking algorithm with adaptive beam reconstruction via UA V-
BSs for mobile users,” IEEE Trans. Veh. Technol., vol. 73, no. 9,
pp. 13164–13177, Sep. 2024.
[18] Q. Li et al., “Machine learning based time domain millimeter-wave
beam prediction for 5G-advanced and beyond: Design, analysis, and
over-the-air experiments,” IEEE J. Sel. Areas Commun., vol. 41, no. 6,
pp. 1787–1809, Jun. 2023.
[19] K. Ma, S. Du, H. Zou, W. Tian, Z. Wang, and S. Chen, “Deep
learning assisted mmWave beam prediction for heterogeneous networks:
A dual-band fusion approach,” IEEE Trans. Commun., vol. 71, no. 1,
pp. 115–130, Jan. 2023.
[20] P. Wang, K. Ma, Y . Bai, C. Sun, and Z. Wang, “Deep learning assisted
mmWave beam prediction with ﬂexible network architecture,” IEEE
Trans. Wireless Commun., vol. 24, no. 11, pp. 9435–9448, Nov. 2025.
[21] K. Ma, D. He, H. Sun, Z. Wang, and S. Chen, “Deep learning assisted
calibrated beam training for millimeter-wave communication systems,”
IEEE Trans. Commun., vol. 69, no. 10, pp. 6706–6721, Oct. 2021.
[22] P. Wang, C. Sun, K. Ma, Y . Bai, and Z. Wang, “mmWave beam
prediction under hand blockage,” IEEE Wireless Commun. Lett., vol. 13,
no. 12, pp. 3598–3602, Dec. 2024.
[23] Q. Xue, A. Nordio, K. Niu, C. Dong, and C. Fabiana Chiasserini,
“Integrated probing-beam pattern learning and beam prediction for
mmWave massive MIMO,” IEEE Trans. Commun., vol. 73, no. 8,
pp. 6499–6513, Aug. 2025.
[24] R. Wang, C. She, Y . Li, and B. Vucetic, “Attention mechanism for
beam prediction in mmWave communications with mission-critical
applications,” in Proc. IEEE Globecom Workshops (GC Wkshps), Dec.
2022, pp. 1454–1459.
[25] Y . Sheng, K. Huang, L. Liang, P. Liu, S. Jin, and G. Ye Li, “Beam
prediction based on large language models,” IEEE Wireless Commun.
Lett., vol. 14, no. 5, pp. 1406–1410, May 2025.
[26] Y . Zhang, X. Wu, and C. You, “Fast near-ﬁeld beam training for
extremely large-scale array,” IEEE Wireless Commun. Lett., vol. 11,
no. 12, pp. 2625–2629, Dec. 2022.
[27] X. Wu, C. You, J. Li, and Y . Zhang, “Near-ﬁeld beam training: Joint
angle and range estimation with DFT codebook,” IEEE Trans. Wireless
Commun., vol. 23, no. 9, pp. 11890–11903, Sep. 2024.
[28] Y . Lu, Z. Zhang, and L. Dai, “Hierarchical beam training for extremely
large-scale MIMO: From far-ﬁeld to near-ﬁeld,” IEEE Trans. Commun.,
vol. 72, no. 4, pp. 2247–2259, Apr. 2024.
[29] X. Shi, J. Wang, Z. Sun, and J. Song, “Spatial-chirp codebook-based
hierarchical beam training for extremely large-scale massive MIMO,”
IEEE Trans. Wireless Commun., vol. 23, no. 4, pp. 2824–2838, Apr.
2024.
[30] C. Wu, C. You, Y . Liu, L. Chen, and S. Shi, “Two-stage hierarchical
beam training for near-ﬁeld communications,” IEEE Trans. Veh. Tech-
nol., vol. 73, no. 2, pp. 2032–2044, Feb. 2024.
[31] Z. Xu, Z. Zhang, and L. Dai, “Near-optimal near-ﬁeld beam training:
From searching to inference,” IEEE Trans. Wireless Commun., vol. 24,
no. 11, pp. 9173–9185, Nov. 2025.
[32] W. Liu, H. Ren, C. Pan, and J. Wang, “Deep learning based beam
training for extremely large-scale massive MIMO in near-ﬁeld domain,”
IEEE Commun. Lett., vol. 27, no. 1, pp. 170–174, Jan. 2023.
[33] W. Liu, C. Pan, H. Ren, J. Wang, and R. Schober, “Near-ﬁeld multiuser
beam-training for extremely large-scale MIMO systems,” IEEE Trans.
Commun., vol. 73, no. 4, pp. 2663–2679, Apr. 2025.
[34] G. Jiang and C. Qi, “Near-ﬁeld beam training based on deep learning
for extremely large-scale MIMO,” IEEE Commun. Lett., vol. 27, no. 8,
pp. 2063–2067, Aug. 2023.
[35] P. Gavriilidis and G. C. Alexandropoulos, “Near-ﬁeld beam tracking with
extremely large dynamic metasurface antennas,” IEEE Trans. Wireless
Commun., vol. 24, no. 7, pp. 6257–6272, Jul. 2025.
[36] K. Chen, C. Qi, C.-X. Wang, and G. Y . Li, “Beam training and
tracking for extremely large-scale MIMO communications,” IEEE Trans.
Wireless Commun., vol. 23, no. 5, pp. 5048–5062, May 2024.
[37] S. Palmucci, A. Guerra, A. Abrardo, and D. Dardari, “Two-timescale
joint precoding design and RIS optimization for user tracking in
near-ﬁeld MIMO systems,” IEEE Trans. Signal Process., vol. 71,
pp. 3067–3082, 2023.
[38] Y . Wu, W. Zhou, N. Gao, D. Cai, B. Su, and L. Yu, “Low-altitude
UA V position prediction-assisted near-ﬁeld adaptive beamwidth con-
trol for XL-MIMO systems,” IEEE Internet Things J., vol. 13, no. 4,
pp. 5477–5490, Feb. 2026.
[39] W. Yi, J. Zhang, Z. Wang, H. Xiao, and B. Ai, “Mobility-aware near-
ﬁeld beam training in XL-MIMO systems for high-speed railway,” IEEE
Wireless Commun. Lett., vol. 14, no. 9, pp. 2708–2712, Sep. 2025.
[40] Y . Kim and Y . J. Kim, “A near-ﬁeld beam-tracking technique for
extremely large uniform planar array systems with overlapped subarray
conﬁguration,” IEEE Commun. Lett., vol. 30, pp. 747–751, 2026.
[41] M. Yuan, J. Jiang, D. Qiao, and Y . Li, “IMM-UKF model based adaptive
beam tracking in XL-MIMO systems,” in Proc. 7th Int. Conf. Natural
Lang. Process. (ICNLP), Mar. 2025, pp. 713–718.
[42] Y . Qian, J. Jiang, M. Yuan, Y . Ye, S. Chen, and J. Zhang, “Spatio-
temporal graph convolutional network-based beam training and tracking
for XL-MIMO systems,” IEEE Wireless Commun. Lett., vol. 15,
pp. 1400–1404, 2026.
[43] Y . Wang, C. Qi, W. He, and A. Nallanathan, “Near-ﬁeld beam training
and tracking with deep learning for extremely large-scale MIMO,” IEEE
Trans. Veh. Technol., vol. 74, no. 12, pp. 19783–19788, Dec. 2025.
[44] T. O’Shea and J. Hoydis, “An introduction to deep learning for the
physical layer,” IEEE Trans. Cognit. Commun. Netw., vol. 3, no. 4,
pp. 563–575, Dec. 2017.
[45] B. Liu, X. Liu, S. Gao, X. Cheng, and L. Yang, “LLM4CP: Adapting
large language models for channel prediction,” J. Commun. Inf. Netw.,
vol. 9, no. 2, pp. 113–125, Jun. 2024.
[46] B. Liu, S. Gao, X. Liu, X. Cheng, and L. Yang, “WiFo: Wireless
foundation model for channel prediction,” Sci. China Inf. Sci., vol. 68,
no. 6, May 2025, Art. no. 162302.
[47] X. Sun, C. Qi, and G. Y . Li, “Beam training and allocation for mul-
tiuser millimeter wave massive MIMO systems,” IEEE Trans. Wireless
Commun., vol. 18, no. 2, pp. 1041–1053, Feb. 2019.
[48] A. Alkhateeb, G. Leus, and R. W. Heath Jr., “Limited feedback hybrid
precoding for multi-user millimeter wave systems,” IEEE Trans. Wire-
less Commun., vol. 14, no. 11, pp. 6481–6494, Nov. 2015.
[49] A. Alkhateeb and R. W. Heath Jr., “Frequency selective hybrid precoding
for limited feedback millimeter wave systems,” IEEE Trans. Commun.,
vol. 64, no. 5, pp. 1801–1818, May 2016.
[50] Technical Speciﬁcation Group Radio Access Network; NR; Physi-
cal Channels and Modulation, document TS 38.211, 3rd generation
partnership project, 2023. [Online]. Available: https://www.3gpp.org/ftp/
Specs/archive/38 series/38.211/
[51] 5G; NR; Physical Channels and Modulation, document TS 38.211,
3GPP, Jul. 2023. [Online]. Available: https://www.etsi.org/deliver/
etsi ts/138200 138299/138211/
[52] 5G; NR; User Equipment (UE) Radio Transmission and Reception;
Part 1: Range 1 Stand Alone, document TS 38.101-1, 3rd Generation
Partnership Project, Jul. 2023. [Online]. Available: https://www.etsi.org/
deliver/etsi ts/138100 138199/13810101/
[53] K. Ma, D. He, H. Sun, and Z. Wang, “Deep learning assisted mmWave
beam prediction with prior low-frequency information,” in Proc. IEEE
Int. Conf. Commun., Jun. 2021, pp. 1–6.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 17 页

LIU et al.: LARGE-MODEL AI FOR NEAR-FIELD BEAM PREDICTION: A CNN–GPT2 FRAMEWORK 15165
[54] Y . Xie, B. Ning, L. Li, and Z. Chen, “Near-ﬁeld beam training in THz
communications: The merits of uniform circular array,” IEEE Wireless
Commun. Lett., vol. 12, no. 4, pp. 575–579, Apr. 2023.
[55] H. Wang, J. Fang, H. Duan, and H. Li, “Fast hybrid far/near-ﬁeld beam
training for extremely large-scale millimeter wave/terahertz systems,”
IEEE Trans. Commun., vol. 73, no. 6, pp. 3956–3970, Jun. 2025.
[56] Study on Channel Model for Frequencies From
0.5 to 100 Ghz, document TR 38.901, 3GPP, Oct.
2025. [Online]. Available: https://www.etsi.org/deliver/
etsi tr/138900 138999/138901/19.01.00 60/tr 138901v190100p.pdf
[57] S. Jaeckel, L. Raschkowski, K. B ¨orner, and L. Thiele, “QuaDRiGa: A 3-
D multi-cell channel model with time evolution for enabling virtual ﬁeld
trials,” IEEE Trans. Antennas Propag., vol. 62, no. 6, pp. 3242–3256,
Jun. 2014.
[58] Y . Lu and L. Dai, “Near-ﬁeld channel estimation in mixed LoS/NLoS
environments for extremely large-scale MIMO systems,” IEEE Trans.
Commun., vol. 71, no. 6, pp. 3694–3707, Jun. 2023.
Wang Liu (Graduate Student Member, IEEE)
received the B.S. degree from the School of
Electronics and Information Engineering, Nanjing
University of Information Science and Technology,
Nanjing, China, in 2021. He is currently pursuing the
Ph.D. degree with the School of Information Science
and Engineering, Southeast University, Nanjing. His
research interests include massive MIMO, recon-
ﬁgurable intelligent surfaces (RIS), and machine
learning.
Cunhua Pan (Senior Member, IEEE) is currently
a Full Professor with Southeast University. He has
published over 200 IEEE journal articles. His papers
got over 24 000 Google Scholar citations with an H-
index of 76. His research interests mainly include
reconﬁgurable intelligent surfaces (RIS), AI for
wireless, near ﬁeld communications and sensing, and
integrated sensing and communications. He received
the IEEE ComSoc Leonard G. Abraham Prize in
2022, the IEEE ComSoc Asia–Paciﬁc Outstanding
Young Researcher Award in 2022, the IEEE ComSoc
Fred W. Ellersick Prize in 2024, the IEEE ComSoc CTTC Early Achievement
Award in 2024, the IEEE ComSoc SPCC Early Achievement Award in
2024, the IEEE ComSoc RCC Early Achievement Award in 2025, the IEEE
ComSoc Heinrich Hertz Award in 2025, and the IEEE ComSoc SPCC
Best Paper Award in 2025. He supervised Ph.D. Thesis won the IEEE
Signal Processing Society Best Ph.D. Dissertation Award in 2024. He is a
Clarivate Highly Cited Researcher. He is/was an Editor of IEEE T RANS -
ACTIONS ON COMMUNICATIONS , IEEE T RANSACTIONS ON VEHICULAR
TECHNOLOGY , IEEE W IRELESS COMMUNICATIONS LETTERS , and IEEE
COMMUNICATIONS LETTERS . He serves as the Leading Guest Editor for
IEEE J OURNAL ON SELECTED AREAS IN COMMUNICATIONS and IEEE
JOURNAL OF SELECTED TOPICS IN SIGNAL PROCESSING .
Hong Ren (Member, IEEE) received the B.S. degree
from the School of Information Science and Engi-
neering, Southwest Jiaotong University, Chengdu,
China, in 2011, and the M.S. and Ph.D. degrees from
Southeast University, Nanjing, China, in 2014 and
2018, respectively. From 2016 to 2018, she was a
Visiting Student with the University of Southamp-
ton, U.K., and from 2018 to 2020, a Post-Doctoral
Scholar with the Queen Mary University of London,
U.K. She is currently an Associate Professor with
Southeast University. Her research interests include
communication and signal processing, cooperative ISAC, AI, and URLLC.
She was recognized as a Clarivate Highly Cited Researcher in 2024 and
2025. She was a recipient of the IEEE ComSoc Heinrich Hertz Award
in 2025, the IEEE ComSoc SPCC Best Paper Award in 2025, the IEEE
Communications Society Fred W. Ellersick Prize in 2024, and the IEEE
Communications Society Leonard G. Abraham Prize in 2022. She is also an
Editor of IEEE T RANSACTIONS ON VEHICULAR TECHNOLOGY and IEEE
WIRELESS COMMUNICATIONS LETTERS .
Wei Zhang (Fellow, IEEE) received the Ph.D.
degree in electronics engineering from The Chinese
University of Hong Kong in 2005. He is currently a
Professor with the University of New South Wales,
Sydney, Australia. His research interests include
6G, AI for communications, and space informa-
tion networks. He served as the Vice President for
IEEE ComSoc from 2022 to 2025. He received
the 2024 IEEE Communications Society Joseph
LoCicero Award. He also served as the Chair for
the Wireless Communications Technical Committee
(2019–2020), the Vice Director for the Asia–Paciﬁc Board (2016–2021),
and the Editor-in-Chief for IEEE W IRELESS COMMUNICATIONS LETTERS
(2016–2019). He is also the Editor-in-Chief of the Journal of Communications
and Information Networks.
Cheng-Xiang Wang (Fellow, IEEE) received the
B.Sc. and M.Eng. degrees in communication and
information systems from Shandong University,
China, in 1997 and 2000, respectively, and the Ph.D.
degree in wireless communications from Aalborg
University, Denmark, in 2004.
He was a Research Assistant with Hamburg Uni-
versity of Technology, Hamburg, Germany, from
2000 to 2001, a Visiting Researcher with Siemens
AG Mobile Phones, Munich, Germany, in 2004, and
a Research Fellow with the University of Agder,
Grimstad, Norway, from 2001 to 2005. He was with Heriot-Watt University,
Edinburgh, U.K., from 2005 to 2018, where he was promoted to a Professor in
2011. He has been with Southeast University, Nanjing, China, as a Professor
since 2018, and he is currently the Dean of the School of Information Science
and Engineering. He is also a Professor with Purple Mountain Laboratories,
Nanjing. He has authored four books, three book chapters, and over 700 papers
in refereed journals and conference proceedings, including over 270 IEEE
journal/magazine papers and 33 highly cited papers. He has also delivered
39 invited keynote speeches and 24 tutorials in international conferences. His
current research interests include wireless channel measurements and model-
ing, 6G/B6G ubiquitous intelligent connectivity networks, and electromagnetic
information theory.
Dr. Wang is a member of the Academia Europaea (The Academy of Europe)
and European Academy of Sciences and Arts (EASA), a fellow of the Royal
Society of Edinburgh (FRSE), IET, and China Institute of Communications
(CIC), an IEEE Communications Society Distinguished Lecturer in 2019 and
2020, and a Highly-Cited Researcher recognized by Clarivate Analytics in
2017–2020 and 2025. He was an Executive Editorial Committee Member
of IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS from 2019
to 2025. He has served as an Editor for over ten international journals,
including IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS from
2007 to 2009, IEEE T RANSACTIONS ON VEHICULAR TECHNOLOGY from
2011 to 2017, and IEEE T RANSACTIONS ON COMMUNICATIONS from 2015
to 2017. He was a Guest Editor of the IEEE J OURNAL ON SELECTED AREAS
IN COMMUNICATIONS , IEEE T RANSACTIONS ON BIG DATA, and IEEE
TRANSACTIONS ON COGNITIVE COMMUNICATIONS AND NETWORKING .
Jiangzhou Wang (Fellow, IEEE) is currently a
Professor with Southeast University and an Emer-
itus Professor with the University of Kent. He has
published more than 600 articles and ﬁve books. His
research interests include mobile communications.
He is an International Member of Chinese Academy
of Engineering (CAE) and a fellow of the Royal
Academy of Engineering (RAEng), U.K. He was a
recipient of the 2024 IEEE Communications Society
Fred W. Ellersick Prize and the 2022 IEEE Com-
munications Society Leonard G. Abraham Prize. He
is the General Chair of the 2026 IEEE Global Communications Conference
(GLOBECOM2026), Macau. He was the Technical Program Chair of the 2019
IEEE International Conference on Communications (ICC2019), Shanghai, the
Executive Chair of the IEEE ICC2015, London, and the Technical Program
Chair of the IEEE WCNC2013.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:10:08 UTC from IEEE Xplore.  Restrictions apply.
