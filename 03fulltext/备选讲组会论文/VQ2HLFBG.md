---
type: literature-fulltext
title: "Multi-Domain Supervised Contrastive Learning for UAV Radio-Frequency Open-Set Recognition"
zotero_key: "VQ2HLFBG"
pdf_key: "QRNY7ANU"
doi: "10.1109/JSAC.2026.3669136"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Multi-Domain Supervised Contrastive Learning for UAV Radio-Frequency Open-Set Recognition.md"
fulltext_path: "03fulltext/备选讲组会论文/VQ2HLFBG.md"
zotero_item: "zotero://select/library/items/VQ2HLFBG"
zotero_pdf: "zotero://open-pdf/library/items/QRNY7ANU"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Multi-Domain Supervised Contrastive Learning for UAV Radio-Frequency Open-Set Recognition

> PDF 原文逐页文本抽取；来源文件 SHA-256：`4f1fbaad29c4af6bfb07028db6fda5050b731c11eba5d0dbcb04a23ba5221e91`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026 4083
Multi-Domain Supervised Contrastive Learning for
UA V Radio-Frequency Open-Set Recognition
Ning Gao
 , Member , IEEE, Tianrui Zeng, Student Member , IEEE, Bowen Chen,
Donghong Cai
 , Senior Member , IEEE, Shi Jin
 , Fellow, IEEE, and Michail Matthaiou
 , Fellow, IEEE
Abstract—5G-Advanced (5G-A) has enabled the vibrant devel-
opment of low altitude integrated sensing and communication
(LA-ISAC) networks. As a core component of these networks,
uncrewed aerial vehicles (UA Vs) have witnessed rapid prolifer-
ation in recent years. However, due to the lag in traditional
industry regulatory norms, unauthorized ﬂight incidents occur
frequently, posing a severe security threat to LA-ISAC networks.
To surveil the non-cooperative UA Vs, in this paper, we propose a
multi-domain supervised contrastive learning (MD-SupContrast)
framework for UA V radio frequency (RF) open-set recognition.
Speciﬁcally, ﬁrst, the texture features and the time-frequency
position features from the ResNet and the TransformerEncoder
(TE) are fused, and then the supervised contrastive learning is
applied to optimize the feature representation of the closed-set
samples. Next, to surveil the invasive UA Vs that appear in real life,
we propose an improved generative OpenMax (IG-OpenMax)
algorithm and construct an open-set recognition model, namely
Open-RFNet. According to the unknown samples, we ﬁrst freeze
the feature extraction layers and then only retrain the classiﬁ-
cation layer, which achieves excellent recognition performance
both in closed-set and open-set recognitions. We analyze the
computational complexity of the proposed model. Experiments
are conducted with a large-scale UA V open dataset. The results
show that the proposed Open-RFNet outperforms the existing
benchmark methods in terms of recognition accuracy between the
known and the unknown UA Vs, as it achieves 95.12% in closed-
set and 96.08% in open-set under 25 UA V types, respectively.
Index Terms—Low altitude, ISAC, open-set recognition, super-
vised contrastive learning, UA V RF recognition.
I. I NTRODUCTION
A. Background
U
NCREWED Aerial Vehicles (UA Vs), which are
uncrewed aircrafts controlled by a wireless remote
control device and their own program control device,
Received 25 July 2025; revised 20 December 2025; accepted 24 February
2026. Date of publication 2 March 2026; date of current version 17 March
2026. This work was supported in part by the National Key Research and
Development Program of China under Grant 2024YFE0200700, in part by the
National Science Foundation of China (NSFC) under Grant 62371131, and in
part by the Program of Zhishan Young Scholar of Southeast University under
Grant 2242024RCB0030. The work of Michail Matthaiou was supported
by the European Research Council (ERC) under the European Union’s
Horizon 2020 Research and Innovation Programme under Grant 101001331.
(Corresponding author: Shi Jin.)
Ning Gao, Tianrui Zeng, and Bowen Chen are with the School of Cyber Sci-
ence and Engineering, Southeast University, Nanjing 210096, China (e-mail:
ninggao@seu.edu.cn; 220245586@seu.edu.cn; 213232141@seu.edu.cn).
Donghong Cai is with the College of Cyber Security, Jinan University,
Guangzhou 510632, China (e-mail: dhcai@jnu.edu.cn).
Shi Jin is with the National Mobile Communications Research Laboratory,
Southeast University, Nanjing 210096, China (e-mail: jinshi@seu.edu.cn).
Michail Matthaiou is with the Centre for Wireless Innovation
(CWI), Queen’s University Belfast, BT3 9DT Belfast, U.K. (e-mail:
m.matthaiou@qub.ac.uk).
Digital Object Identiﬁer 10.1109/JSAC.2026.3669136
have the advantages of small size, low cost and strong
ﬂexibility. Initially, UA Vs were applied in military operations
for reconnaissance and target strikes. With technological
advancements and cost reduction, UA Vs have gradually been
applied in the civilian domain. Currently, the application
scenarios of UA Vs are becoming increasingly diverse, and
they have been widely used in ﬁelds, such as forestry plant
protection, communications and emergency rescue, etc., [1],
[2], and [3].
However, the contradiction between the advancement of the
UA V technology and the regulatory perplexities has gradu-
ally exposed the security risks and management loopholes.
Commercial UA Vs are easy to purchase and develop, though
most of them still do not have the online registration function.
Furthermore, many of them do not have a geofencing or the
geofencing option can be easily turned off by modifying their
global positioning system (GPS). Since the ﬂight rules of the
UA Vs are not easily followed by the malicious users, illegal
invasion and privacy leakage become signiﬁcantly likely in
low altitude (LA) networks. In this case, the question of
“who is ﬂying?” has to be urgently addressed. From an anti-
UA V perspective, the UA V type recognition is a prerequisite
technique to counter the invasion of the non-cooperative UA Vs.
With the development of 5G-Advanced (5G-A) base sta-
tions, LA-integrated sensing and communication (ISAC) has
become one of the promising technologies for the development
of future wireless communications. The surveillance of LA
UA Vs is an important LA-ISAC application scenario. Tra-
ditionally, LA UA V surveillance mainly focuses on physical
surveillance, which can be used for the surveillance of the
ﬂight trajectory for safety purposes. Therein, the physical
states of the UA V are perceived via multi-modal sensing,
including visual, acoustic and radar, etc. Nevertheless, the
passive surveillance function for UA V types or identities, based
on 5G-A base stations, has been less investigated.
The radio frequency (RF) signal-based UA V recognition is a
promising method to recognize UA V types, which is attributed
to the following advantages. Compared with the radar and light
detection, it is environmental friendly, since passive monitor-
ing does not cause electromagnetic interference to the wireless
environments and has low energy consumption. Compared
with the vision and acoustic detection, it is environmentally
robust, since it is insensitive to obstacles, non line-of-sight
(NLoS) propagation conditions and the atmospheric sounds
[4]. The recognition performance is irrelevant to the size of
the UA V , which makes it possible to identify even very covert
illegal activities. The underlying principle of the RF signal-
1558-0008 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

4084 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 1. The schematic diagram of a UA V RF signal.
based UA V recognition is that different types of UA Vs have
different spectrum features in raw RF signals, such as the duty
ratio, modulation pattern, which is regarded as an intrinsic
signature of the UA V type. Figure 1 shows a schematic
diagram of the UA V RF signal of the popular DJI Phantom 4
Pro. The large red rectangle represents the video transmission
signal (VTS), which carries the UA V’s camera video stream.
The small red rectangle represents the control signal, which
carries ﬂight commands and logs.
B. Motivation and Contribution
There are some recent works that have studied the RF
signal-based UA V recognition. The authors in [5] proposed a
deep neural network (DNN)-based method to detect the UA V
presence, type and ﬂight mode, where the results showed a
general decline in performance when increasing the number of
classes, i.e., the average accuracy decreased from 99.7% for 2
classes to 46.8% for 10 classes. The reason is that when the
number of UA Vs increase, the features among UA Vs become
extremely similar, whereas the signal of the commercial UA V
is usually non-stationary and frequency hopping, which makes
the basic CNNs struggle to classify. On the other hand, many
works focus on the closed-set recognition, where the UA Vs
are categorized to the known classes under the assumption
that the environment is completely closed. However, for illegal
modiﬁed UA Vs, the RF sample distribution is unknown, thus,
there are signiﬁcant limitations with closed-set recognition [6],
[7], [8], [9]. On the other hand, open-set techniques accept
test samples from unknown classes, which requires the model
to not only classify known classes but also detect unknown
classes. This setting better reﬂects practical UA V surveillance
environments, where many non-cooperative UA Vs often do not
appear in the training dataset. Recently, Tao et al. proposed an
open-set recognition method, based on a neural network and
the OpenMax algorithm, for radar automatic UA V target recog-
nition [8]. Yu et al. proposed a signal semantic-based open-set
recognition which designs an outlier analysis-based semantic
classiﬁer to detect the unknown instances [9]. However, the
performance in open-set recognition is achieved at the expense
of a performance reduction in closed-set recognition, where
the recognition accuracies of some known classiﬁcations are
signiﬁcantly reduced. To the best of the authors’ knowledge,
the open-set recognition for non-cooperative UA Vs has not
yet been well studied. These limitations in existing RF-based
UA V recognition studies directly motivate our work. There-
fore, in this paper, we attempt to address the following
problems: i) How to accurately recognize a UA V when the
signal is subject to non-stationarities and frequency hopping?
ii) How to improve the performance of open-set recognition
while maintaining the performance of closed-set recognition
as much as possible? To this end, we propose a multi-domain
supervised contrastive learning (MD-SupContrast) framework
to recognize the non-cooperative UA Vs with RF signals.
Speciﬁcally, both the texture feature and position feature are
fused to represent the RF feature, while contrastive learning is
used to optimize the feature representation. Then, the improved
generative OpenMax (IG-OpenMax) algorithm is proposed to
balance the recognition performance between the closed-set
and the open-set. Our main contributions are summarized as
follows:
• An MD-SupContrast framework is proposed for UA V
RF recognition, where the texture feature and the time-
frequency position feature are jointly considered and
fused via multiple non-linear layers (MNLs). Speciﬁcally,
the texture feature is used to mitigate the negative impact
from non-stationary signals and frequency hopping, while
the position feature is used to enhance the recognition
ability among known/unknown classes. In addition, to
avail of texture features and time-frequency position
features and avoid the unbalanced feature optimization,
MD-SupContrast employs supervised contrastive learning
to perform optimization with the feature representations
of the samples themselves.
• Based on the proposed MD-SupContrast framework, we
propose the Open-RFNet for recognizing the known
and the unknown UA Vs. In particular, to address
the unbalanced recognition performance between the
closed-set and the open-set, we propose a two-stage
IG-OpenMax algorithm based on the generative Open-
Max (G-OpenMax) algorithm. We ﬁrst freeze the feature
extraction layers of the trained closed-set model and
then only retrain the classiﬁcation layer for the unknown
samples with a low training overhead.
• We adopt a large-scale UA V RF open dataset, namely
DroneRFa [10], to evaluate the performance of the pro-
posed Open-RFNet. The results show that the proposed
Open-RFNet outperforms the benchmark methods in
terms of recognition accuracy both in the known and the
unknown UA Vs. The proposed Open-RFNet can achieve
recognition accuracy of 95.12% in closed-set and 96.08%
in open-set with 25 UA V types, respectively, while the
performance gap between the closed-set and the open-set
is only 0.96%.
C. Overview
The rest of this paper is organized as follows: The related
works are presented in Section II. The framework and the
data preprocessing are presented in Section III. The closed-
set recognition and the open-set recognition are proposed in
Section IV and Section V, respectively. The experimental
results are showcased in Section VI, while the paper is
concluded in Section VII.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

GAO et al.: MULTI-DOMAIN SUPERVISED CONTRASTIVE LEARNING FOR UA V RF OPEN-SET RECOGNITION 4085
II. R ELATED WORK
A. RF Recognition Methods
RF recognition methods can accurately recognize the emit-
ter target through RF signals. In the early stage, these methods
relied on the manual feature extraction and expert knowl-
edge. The high computational complexity makes it difﬁcult
to handle complex multi-dimensional features. For example,
the expert knowledge would extract features by analyzing the
deviation between the modulated signals and the ideal signals.
These features include inphase/quadrature (I/Q) imbalance,
amplitude error, and phase error, etc. Subsequently, machine
learning methods, such as support vector machines (SVM)
were typically used [11]. However, this approach has some
limitations as it relies on time-consuming feature engineering,
thus being sensitive to environmental noise.
In recent years, deep learning has gradually been intro-
duced into the RF recognition space [12]. This effectively
solves the generalization problem faced by traditional RF
recognition methods in complex channel environments and
provides strong support for large-scale device recognition
tasks. For example, the authors in [13] proposed the ORACLE
method, which uses a convolutional neural network (CNN)
to achieve high-precision classiﬁcation. Reference [14] pro-
posed the differential constellation trace ﬁgure (DCTF)-CNN
method, which uses the DCTF to convert the differential
relationship of signal time series into a two-dimensional
image. Without carrier frequency and time synchronization,
the CNN is directly employed to automatically learn the
features, effectively reducing the recognition difﬁculty of
hardware-similar ZigBee devices at low signal-to-noise ratio
(SNR). With the popularity of large language models (LLMs),
a LLM-enabled lightweight CNN framework was conceived
in [15] to conduct the RF ﬁngerprint identiﬁcation for edge
intelligence. In addition to the single modulation domain,
feature extraction can be extended to multi-domain features,
such as statistical, frequency domain, and wavelet domain[16],
[17], [18].
RF recognition methods have been utilized in recognizing
UA Vs, but they are still relatively scarce. For example, a RF
signal-based UA V surveillance system was developed in [19],
with a high performance CNN which uses a structure of multi-
level skip-connection and multi-level pooling. The authors in
[20] employed a lightweight backbone network with multiscale
convolution blocks to reduce the model size and enhance
the feature extraction ability, which can achieve an excellent
accuracy at different SNRs.
B. Other Recognition Methods
UA V recognition could be also performed by leveraging
vision, sound and radar-based methods. Vision-based recogni-
tion mainly relies on the image or video data stream captured
by cameras. The authors in [21] used Haar-like features,
local binary patterns (LBP), and histogram of oriented gra-
dients (HOG) to extract different features from images, and
constructs a cascaded classiﬁer. However, the vision-based
detection is sensitive to environment factors, including the
lighting, weather and background noise, which degrade the
recognition performance, especially of fast ﬂying objects.
Radar-based UA V recognition utilizes radio-echoes to detect
the distant UA Vs, where the position, speed, altitude, and the
direction of the UA V can be determined. Compared with the
vision-based methods, radar-based recognition is not limited
by lighting conditions and can operate at night or in adverse
weather. Reference [22] was based on an X-band frequency
modulated continuous wave (FMCW) radar. Through digital
beamforming and 2D fast Fourier transform (FFT), it realized
the detection of commercial UA Vs within 2 km and has excel-
lent range-speed association capability. However, radar-based
UA V recognition has limited capabilities in detecting ﬁne fea-
tures, such as the UA V speciﬁc type. Moreover, the recognition
performance for low-altitude, slow-moving and small-sized
airborne targets is not very satisfactory. Sound-based UA V
recognition captures sound signals generated during UA V
ﬂight, such as noise, rotor rotation sounds, and motor vibration
sounds with microphone arrays. Then, it analyzes the acoustic
features via signal processing and recognition algorithms to
achieve UA V recognition and positioning. Reference [23]
proposed a method based on three neural networks, which
realizes UA V detection and type recognition by extracting the
acoustic ﬁngerprint features and integrating data augmentation.
However, this approach is highly susceptible to interference.
Background noise in outdoor environments, such as wind, rain,
trafﬁc noise, biological sound and distance, may mask or dis-
tort the UA V’s acoustic signals, which leads to a deterioration
in the recognition accuracy.
C. Open-Set Recognition
Traditional machine learning and CNNs mainly focus on
closed-set environments, which can only distinguish classiﬁ-
cations that already exist in the training set. For the unknown
classiﬁcations, the traditional methods mistakenly identify
them as known classiﬁcations. Therefore, open-set recognition,
which is closer to real-world scenarios, has been proposed
[24], [25], [26], [27]. It requires the established model to
not only distinguish classiﬁcations that appear in the training
process but also effectively handle unseen classiﬁcations. Ref-
erence [24] proposed a 1-vs-set machine learning framework
based on a linear kernel SVM, which restricts the decision
boundaries of known classes to reduce the risk of open-
set space by constructing a “double-plane decision space”.
However, a single algorithm imposes certain limitations on
the model. Then, [25] adopted the idea of integration, fusing
multiple algorithms to achieve open-set recognition. All the
above methods are implemented based on traditional machine
learning. For methods based on DNNs, the OpenMax was
proposed in [26], which combines the Weibull distribution with
the softmax layer to realize open-set recognition. This method
successfully estimates the pseudo-probability of unknown
classiﬁcations and achieves open-set recognition without con-
sidering the prior knowledge of unknown classiﬁcations.
Reference [27] improved the OpenMax and then proposed
the G-OpenMax, which synthesizes new sample classiﬁcation
via generative adversarial networks (GANs) to simulate real
unknown category samples, thereby improving the recognition
performance. However, this study has shown that although
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

4086 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 2. The constructed Open-RFNet model based on the proposed MD-SupContrast framework.
TABLE I
LIST OF SYMBOLS
G-OpenMax can improve the performance of open-set recogni-
tion on monochromatic datasets, its performance improvement
on natural images is not signiﬁcant. Furthermore, there is still
limited research on open-set recognition for UA Vs [8], [9].
III. P RELIMINARIES
In this section, we ﬁrst propose the MD-SupContrast frame-
work, and then formulate the signal preprocessing. Table I
provides clear deﬁnitions of the mainly used symbols in this
paper.
A. Training Framework and Model
We construct the Open-RFNet model based on the proposed
MD-SupContrast framework, which is shown in Fig. 2. The
proposed framework mainly consists of four stages: data
preprocessing, Open-RFNet training, Weibull model train-
ing, and sample inference. In the ﬁrst stage, the collected
UA V I/Q signals are sliced and denoised, and then trans-
formed into time–frequency representations via the short-time
Fourier transform (STFT). The obtained samples are sub-
sequently partitioned into a training set Dtrain and a test
set Dtest, which serve as the inputs for the subsequent
stages. In the second stage, the proposed Open-RFNet is
trained on Dtrain under supervised contrastive learning, and
the resulting model is denoted as Open-RFNet-C, which is
capable of performing closed-set recognition on the known
classes. To further enable open-set recognition, we pro-
pose an IG-OpenMax algorithm. Speciﬁcally, a generator is
trained based on the Wasserstein GAN with gradient penalty
(WGAN-GP) framework to simulate unknown class sam-
ples, which is denoted as Dgan. The set Dgan is fed into
Open-RFNet-C for prediction, and the misclassiﬁed samples
are collected to form D′gan. The mixed dataset formed by
Dtrain∪D′gan is used to retrain the classiﬁcation head while
keeping the feature extractor frozen, yielding the ﬁnal Open-
RFNet model. In the third stage, a Weibull distribution is
ﬁtted to the activation values produced by Open-RFNet on
Dtrain to perform statistical modeling. Finally, in the fourth
stage, the trained Weibull calibration model is applied to revise
the prediction results of samples in Dtest, thereby enabling
effective open-set recognition.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

GAO et al.: MULTI-DOMAIN SUPERVISED CONTRASTIVE LEARNING FOR UA V RF OPEN-SET RECOGNITION 4087
Fig. 3. Air-to-ground LoS sensing link between the UA V and the base station.
B. Data Preprocessing
The monitoring link between the UA V and the base sta-
tion can be regarded as an air-to-ground channel, which is
dominated by the line-of-sight (LoS) link, as illustrated in
Fig. 3. On the other hand, various external factors, such as
wind gust, may severely affect the phase of the propagation
path, which is one of the important reasons making the signal
non-stationary, especially in hover mode [28]. Under these
conditions, the I/Q signal transmitted over the wireless channel
experiences attenuation and wobbling, and the demodulated
I/Q signal received by the base station is
r =
√
PL (d) exp
(
−j 2πλ(d + ∆d))s +η, (1)
where d is the distance between the transmitter and the
receiver, PL (d) denotes the distance-dependent path-loss
function between the UA V and the base station, which char-
acterizes the large-scale fading over the air-to-ground link.
The symbol ∆d is the phase affected by wobbling that
is modeled as a zero-mean Gaussian random process, i.e.,
∆d∼N (0,σ 2d), whereσ2d denotes the variance of the random
perturbation. The symbol λ is the wavelength of the signal, s
denotes the baseband I/Q signal, and η represents the additive
white Gaussian noise (AWGN), which follows a zero-mean
complex Gaussian distribution with variance σ2.
Since the UA V signals exhibit periodicity, there is a possibil-
ity of generating samples that contain only background noise
without any UA V signals. Thus, when slicing the collected
I/Q signals, we divide the original signal into sub-slices each
with a size of 1/3 of the target slice. Subsequently, sub-slices
with signal strength below a predeﬁned noise threshold are
ﬁltered out. Finally, the retained sub-slices are concatenated
sequentially to complete the denoising process. After slicing,
the STFT is applied to each slice, where the STFT represen-
tation of the received I/Q signal is expressed as
X[n,q ] =
M−1∑
m=0
r[m]ω[n−m] exp (−j2πqm), (2)
where n is the time index, q is the frequency index, r[m] is
the discrete time received signal, while ω[m] is the discrete
window function with size M. The signal power spectrum of
each time-frequency information can be given by
dB
[
X[n,q ]
]
= 20 log10
⏐⏐X[n,q ]⏐⏐, (3)
where|·| indicates the modulus of a complex number. The
placement of the UA Vs at different locations makes the UA V
signal power close to the RF receiver much larger than that
of the remote UA Vs. Thus, for the fairness of model training,
we normalize each time-frequency information of the signal
power spectrum to
ˆX[n,q ] = dB
[
X[n,q ]
]
− min(dB
[
X(n,q )
]
)
max(dB
[
X(n,q )
]
)− min(dB
[
X(n,q )
]
), (4)
where min(dB[X(n,q )]) and max(dB[X(n,q )]) represent
the minimum value and the maximum value of all elements
in matrix dB[X(n,q )], respectively.
IV. C LOSED -SET RECOGNITION
In this section, we construct the feature extraction modules
and the supervised contrastive learning, which is used for
the UA V RF closed-set recognition. In general, supervised
contrastive learning encourages samples from the same class
to cluster together while pushing apart samples from different
classes in the feature space, thereby enhancing the discrim-
inability of RF representations [29].
A. Feature Extraction
The ResNet-18 is used to extract texture features, which
is primarily composed of 8 residual blocks with each block
comprising two convolutional layers, a batch normalization
layer, a ReLU activation function, and a shortcut connection.
For the l-th residual block, the output can be expressed as
Hl = Fl(Il;Wl) +Il, (5)
where Fl is the combination of the convolutional, the batch
normalization, and the activation operations in thel-th residual
block,Wl is the weight parameter of this block, and Il is the
input of this block.
Following the last residual block, its output H last is pro-
cessed by the global average pooling (GAP) and a ﬂatten
layer to obtain the ﬁnal texture feature representation, which
is represented as
˜za = Flatten (GlobalAvgPooL(H last)), (6)
where GlobalAvgPooL(·): Rc×d1×d2 → Rc×1 is the global
average pooling, while symbol Flatten(·): Rc×1 → Rc
represents the ﬂattening operation. Here, c denotes the number
of feature channels, while d1 and d2 represent the height
and width of the feature map, respectively. The TE is used
to extract the time-frequency position features. Therein, the
time domain position features are extracted by using the
time-frequency signal ˆX(n,q ), while the frequency domain
position features are extracted by using the transpose of
ˆX(n,q ), i.e., ˆX T(n,q ).
To extract the time domain position features, MNLs are
ﬁrst employed to perform preliminary feature extraction on
ˆX(n,q ), yielding ˆX pre(n,g ). Subsequently, the position
encoding is incorporated into the preliminary features to distill
the time domain position features, which are denoted as
ˆX time(n,g ) = ˆX pre(n,g ) +P (n,g ), (7)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

4088 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
P (n,g ) =
{
sin(θgn), if g%2 = 0,
cos(θgn), if g%2 = 1, (8)
whereg is the feature dimension index, while the total number
of feature dimensions is ˜G. The symbol P (·) is the position
encoding operation, ˆX time(n,g ) is the preliminary position
features in time domain, % represents the remainder operation,
and θg is the hand crafted frequency, i.e., θg = 10000− 2g˜G .
TE is based on the self-attention mechanism, which allows
the model to ﬂexibly focus on different positions in the input
sequence, enabling the capture of long and short distance
dependencies and performs well in learning long range depen-
dencies and interactions in sequence data. In this mechanism,
each word in the input sequence calculates its correlation with
other words in the self-attention layer through the query ( Q),
key (K), and value (V ) vectors, thereby generating a weighted
output. Note thatQ represents the information that the current
word needs to focus on, while the K vector represents the
features of each word, which is used to compare with the Q
vectors of other words to determine their correlations, and the
value vector represents the actual content of each word. The
weights of all words are assigned according to the similarity
betweenQ andK to generate the output. The TE module is
composed of multiple stacked TransformerEncoders. The l-th
TE can be given by [9]
ϕl(Yl) = softmax
(
YlQlKTlY Tl√γl
)
YlVl, (9)
where Yl denotes the input to the l-th TE. For the ﬁrst TE,
i.e., l = 0, Y 0 is equivalent to ˆX time(n,g ), softmax(·) rep-
resents the softmax activation function, Ql,Kl,Vl∈ Rn×γ
are learnable parameters, and γ is the size of the mapping
dimension. Therefore, the output of the TE module can be
given by
˜X time =ϕL−1
(
ϕL−2
(
... (ϕ1(ϕ0( ˆX time(n,g ))))), (10)
where L is the number of TransformerEncoders. After that,
the output is ﬂattened and further mapped by MNLs to obtain
the time domain position features, which are expressed as
˜zb = MNLs
(
Flatten
( ˜X time)). (11)
On the other hand, the same procedure is applied to the
transpose of ˆX(n,q ) to obtain the frequency domain position
features ˜zc.
After extracting the texture features and the time-frequency
position features, we use MNLs to fuse the multi-domain
features to obtain the fused feature representation, as follows
˜z = MNLs((˜za⊕ ˜zb⊕ ˜zc, )), (12)
where⊕ represents the concatenation operation, ˜za denotes
the texture features, ˜zb and ˜zc denote the time-domain
position features and frequency-domain position features,
respectively.
Remark 1: As shown in Fig. 1, the texture features focus
on the basic geometric features of the red matrix, such as
the length-to-width ratio of the rectangle, the sharpness of the
edge contour, and the spatial distribution pattern of the internal
amplitude, including the uniformity and gradient trend of the
energy amplitude. The texture features are local features which
have no global statistical characteristics, thereby reducing the
negative impact of non-stationary UA V signals and frequency
hopping in VTS. On the other hand, the model uses the
TE module to extract position features in the time-frequency
domain. This emphasizes the speciﬁc location of the red matrix
in these domains and its relative position to other signal
blocks globally. These are global features which have the
proﬁle features of UA V types, thereby enhancing the UA V
RF recognition performance.
B. Supervised Contrastive Learning
The supervised contrastive learning is used to optimize the
fused features, enabling effective utilization between features
from different domains. Compared with unsupervised con-
trastive learning, supervised contrastive learning makes full
use of label information. It can use multiple samples of the
same class as positive sample pairs, rather than relying only
on the data augmentation to generate positive samples, which
helps to better learn the consistency within the classiﬁcation. In
addition, supervised contrastive learning employs the SupCon
loss function, which overcomes various shortcomings of the
cross-entropy loss function, such as lack of robustness to noisy
labels, insufﬁcient margin between the classes, and unbalanced
optimization of multiple features [30], [31], [32], [33]. These
advantages contribute to recognizing the type of UA Vs from
the extremely similar and noisy I/Q signals.
Speciﬁcally, given a batch of input samples, random data
augmentation is performed to generate two different signal
views. These two views pass through the previously mentioned
feature extraction network to obtain two feature represen-
tations. Finally, the supervised contrastive loss function is
calculated based on these feature representations. The main
idea is to regard all samples of the same category as pos-
itive samples and reduce the distance between them, while
regarding samples of other classiﬁcations as negative samples
and increasing the distance between them. In supervised
contrastive learning, each sample in the batch is sequentially
taken as an anchor sample, and its corresponding positive and
negative sample sets are constructed according to the class
labels. The supervised contrastive loss function is denoted as
Lsup =
∑
i∈I
− 1|P (i)| ∑p∈P (i) log exp(zi· zpT )∑a∈A(i) exp(zi· zaT ),
(13)
where I is the set of all anchor samples, and i is a single
anchor sample; P (i) is the set of all positive samples of the
anchor samplei, andA(i) is the set of all negative samples of
the anchor sample i. Moreover, zi,zp,za are the projection
vectors corresponding to the anchor sample, positive samples,
and negative samples, respectively, while T represents the
temperature parameter.
Remark 2: The Open-RFNet model fuses texture features
and time-frequency position features to obtain the fused fea-
ture representation. The traditional cross-entropy loss function
is prone to the unbalanced optimization problem for multiple
features. This is because it only focuses on the matching
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

GAO et al.: MULTI-DOMAIN SUPERVISED CONTRASTIVE LEARNING FOR UA V RF OPEN-SET RECOGNITION 4089
degree between the overall prediction result and the real label.
When a certain feature, such as texture feature, has better pre-
diction performance, it contributes more to the ﬁnal prediction,
and the corresponding gradient dominates in backpropagation.
Then, the model can prioritize optimizing the parameters of
this dominant feature. Nevertheless, supervised contrastive
learning is used to optimize feature representations at the
feature level. This not only enhances intra-class consistency
but also expands inter-class differences, and avoids such
unbalanced feature optimization problems.
V. O PEN -SET RECOGNITION
In this section, we ﬁrst propose the two-stage IG-OpenMax
algorithm and then discuss the training details of the GAN for
the UA V RF open-set recognition.
A. Problem F ormulation of Open-Set Recognition
LetYK ={1, 2,...,N } denote the set of known classes
(KKCs) accessible during the training phase, and let YU
denote the set of unknown classes (UUCs) that do not appear
in training but may occur during testing. Based on these label
spaces, we deﬁne the corresponding sample domains as
DK ={(x,y )|y∈Y K}, (14)
DU ={(x,y )|y∈Y U}. (15)
Accordingly, the training and testing datasets satisfy the
following inclusion relations:
Dtrain⊆D K, (16)
Dtest⊆D K∪DU. (17)
The goal of open-set recognition is to learn a classiﬁer f
that simultaneously achieves correct identiﬁcation of known
class samples and reliable rejection of unknown class samples.
Formally,f should satisfy
∀(x,y )∈D test∩DK : f(x) =y, (18)
∀(x,y )∈D test∩DU : f(x) = unknown. (19)
In other words, the classiﬁer is required to output the correct
class label for test samples belonging to DK and assign all
samples originating fromDU to an additional unknown class.
B. IG-OpenMax
Open-RFNet implements the IG-OpenMax algorithm to
detect illegal UA Vs, which is an improved version of the G-
OpenMax algorithm. Similar to G-OpenMax, the IG-OpenMax
algorithm also introduces unknown class sample data during
closed-set recognition training by providing explicit prob-
ability estimation for the unknown classes. The explicit
representation of unknown classes enables the classiﬁer to
leverage the knowledge of both known and unknown sam-
ples to locate decision boundaries more effectively, thereby
achieving clearer differentiation between known and unknown
classes. Speciﬁcally, a conditional deep convolutional gen-
erative adversarial network (cDCGAN) is ﬁrst employed to
synthesize labeled samples for each known class. Given a
random noise vector z and the encoded label informationeg(y)
of a known class y∈Y K, the generator produces
˜x =G
(
[z,eg(y)]
)
, ˜y =y, (20)
where G is the generator model, z is sampled from a prior
distribution, and eg(y) denotes the label embedding used for
conditioning. All such generated labeled samples form the
synthetic dataset
Dgan =
{
(˜x, ˜y)
⏐⏐ ˜x =G([z,eg(y)]), y∈Y K}. (21)
These generated samples are then fed into the baseline
model Open-RFNet-C with classiﬁerfC(·) for closed-set eval-
uation. The subset of generated samples that are misclassiﬁed
by Open-RFNet-C is collected as simulated unknown samples:
D′gan ={(˜x, unknown)⏐⏐ (˜x, ˜y)∈D gan, fC(˜x)⁄= ˜y}. (22)
These misclassiﬁed samples serve as approximations to real
unknown class data and are used to expand the open-set
training set:
DOSRtrain =Dtrain∪D′gan. (23)
Unlike the traditional G-OpenMax algorithm, the proposed
IG-OpenMax freezes the feature extraction part of Open-
RFNet-C and only retrains the classiﬁcation head. This design
is adopted because retraining the entire network would destroy
the original feature distribution, causing the generated samples
to deviate from real unknown class samples in the new feature
space.
After training the classier, the prediction results of the
known and unknown class samples from Open-RFNet are fed
into the OpenMax layer to obtain the open-set recognition
result. Speciﬁcally, for each known category j, we ﬁrst cal-
culate the activation vectors (A V) of all training samples that
are correctly recognized as this classiﬁcation, as follows
Sj ={vi(xi)| ˆyi =yi =j, xi,yi∈D train}, (24)
where vi(xi) = (v i,0(x), vi,1(x),..., v i,N(x)) consists of
the logits from this sample to all classiﬁcations with the num-
ber of the known classiﬁcations N, while Dtrain represents
the training set. Denoting the mean activation vector (MA V)
of the j-th class as µj, then we use the Weibull distribution
to ﬁt the distance of each classiﬁcation, according to
ρj =
(τj,κj,χj) = FitHigh(‖Sj−µj‖, Ltail), (25)
whereτj is the shape parameter, κj is the scale parameter, χj
is the location parameter and Ltail represents the tail length
hyperparameter controlling the number of extreme samples
used for ﬁtting. Moreover, FitHigh(·) denotes the Weibull tail-
ﬁtting function, commonly used in OpenMax-based open-set
recognition, which ﬁts a Weibull distribution to the largestLtail
activation distances of class j to model its tail behavior. For a
test sample, we ﬁrst compute vi(x) and then adjust the A Vs
with
˜vi(x) =vi(x)◦cj(x) = (˜vi,0(x), ˜vi,1(x),..., ˜vi,N(x)),
(26)
where vi(x) ◦ cj(x) represents the element-wise
(Hadamard) multiplication between the original activation
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

4090 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
vector and the calibration coefﬁcient vector. The term
(˜vi,0(x), ˜vi,1(x), ..., ˜vi,N(x)) is the explicit expansion of
the adjusted activation vector, which lists all of its (N + 1)
components. The decrements sum of the original scores is
used to derive the score of the unknown classiﬁcation, which
is given by
˜vi,N +1(x) =
N∑
j=0
(
vi,j(x)− ˜vi,j(x)
)
, (27)
where cj(x) is the correction weight vector generated for
samples in class j based on the ﬁtting results of the Weibull
distribution, which only corrects the top-α classiﬁcations with
the highest probabilities. For the A Vs of the known classes,
we have
cs(k)(x) = 1− α−kα exp(−(‖x−τs(k)‖χs(k) )κs(k)), (28)
whereas for the unknown class, we have
cs(k)(x) = 1− α−kα , (29)
wheres(k) = argsort(vi(x)) denotes the index corresponding
to the k-th largest probability classiﬁcation. Finally, we per-
form a softmax operation on the scores of all classiﬁcations
and the score of the unknown classiﬁcation to obtain the ﬁnal
open-set recognition distribution, which is given by
ˆP (y =C|x) = exp
(
˜vi,C(x)
)
∑N +1
j=0 exp
(
˜vi,j(x)
). (30)
Unlike traditional threshold-based open-set methods, Open-
Max does not rely on a manually ﬁxed conﬁdence threshold for
rejection. Instead, it estimates the unknown probability through
Weibull ﬁtting based on extreme value theory (EVT). In our
implementation, the only tunable parameter is the tail size
Ltail, which controls the number of extreme distances used
for Weibull ﬁtting of each class. This parameter determines
how much probability mass is redistributed from the known
classes to the unknown class, thus affecting the trade-off
between known class accuracy and unknown class accuracy.
We validate multiple Ltail values on the validation set and
select the one that yields a balanced performance between
closed-set and open-set performances.
Remark 3: In the traditional G-OpenMax framework, the
entire model, which includes the feature extractor, is retrained
after incorporating the generated samples. This retraining
substantially alters the original feature space learned by the
closed-set model Open-RFNet-C. In the newly formed feature
space, the distributional discrepancy between the generated
samples and real data becomes more pronounced, enabling
the model to easily distinguish between them. As a result,
the generated samples tend to be separated from real sam-
ples, including real unknown class samples, rendering them
ineffective for approximating the unknown class distribution.
In contrast, the proposed IG-OpenMax freezes the feature
extractor during the second training stage and updates only
the classiﬁcation head, thus preserving the original feature
space. Within this unchanged feature space, the misclassiﬁed
generated samples typically lie in boundary regions, where real
unknown class samples are also likely to appear. Consequently,
these generated samples can more accurately approximate
the distribution of real unknown classes in the preserved
feature space, thereby substantially improving the open-set
recognition performance.
C. GAN Training
We use the WGAN-GP framework to train a generator
based on the cDCGAN architecture. By introducing a gradient
penalty, WGAN-GP effectively alleviates the training instabil-
ity of the original WGAN [34]. The WGAN utilizes weight
clipping to ensure the Lipschitz constraint of the discriminator,
which is referred to as the critic. Different from the WGAN,
the WGAN-GP enforces the Lipschitz constraint by penalizing
the gradient norm of the critic with respect to the input.
Speciﬁcally, the objective function of the WGAN-GP adds a
gradient penalty term on the basis of the original WGAN, and
the critic loss can be expressed as
Lc = E˜x,˜y∼Pg[C(˜x, ˜y)]− Ex,y∼Pr[C(x,y )]
+βEˆx,ˆy∼Pˆx
[
(‖∇ˆxC(ˆx, ˆy)‖2− 1)2
]
. (31)
For the generator, its objective is to maximize the critic’s
estimation for the generated samples, which corresponds to
minimizing the following generator loss:
Lg =−E˜x,˜y∼Pg[C(˜x, ˜y)], (32)
where Ex∼P[·] denotes the expectation taken over the ran-
dom variable x drawn from the probability distribution P.
E˜x,˜y∼Pg[C(˜x, ˜y)]− Ex,y∼Pr[C(x,y )] is the objective func-
tion of the original WGAN, which represents the difference
between the expected values of the generated samples and
the real samples in the critic, respectively. The expres-
sionβEˆx,ˆy∼Pˆx
[
(‖∇ˆxC(ˆx, ˆy)‖2− 1)2
]
is the gradient penalty
term, which is used to ensure that the gradient norm of the
critic is close to 1, thus satisfying the Lipschitz constraint.
Therein, C is the critic model, β is the coefﬁcient of the
gradient penalty, x, y are the real samples and their corre-
sponding labels, whereas ˜x, ˜y are the generated samples and
their corresponding labels. Speciﬁcally, ˜x = G
(
[z,eg(y)]
)
and ˜y = y, where G is the generator model, z is the
input random noise, and eg(y) is the result of the generator
encoding the label information. The symbols ˆx, ˆy are the
random interpolation points between the real samples and
the generated samples, such that ˆx = ϵx + (1− ϵ)˜x and
ˆy =y, where ϵ is a random number uniformly distributed in
the interval [0, 1]. We summarize the proposed IG-OpenMax
algorithm in Algorithm1.
VI. C OMPLEXITY ANALYSIS
Firstly, we analyze the time complexity of the Open-RFNet
for closed-set recognition, which can be divided into two parts:
the texture feature extraction part and the positional feature
extraction part. Texture features are extracted through a ResNet
network, wherein the time complexity mainly comes from the
convolutional layers, batch normalization layers, and pooling
layers. In the ResNet-based texture feature extractor, each
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

GAO et al.: MULTI-DOMAIN SUPERVISED CONTRASTIVE LEARNING FOR UA V RF OPEN-SET RECOGNITION 4091
Algorithm 1 IG-OpenMax for Open-Set Recognition
1: Input: Training datasetDtrain consisting of known class
samples, test datasetDtest consisting of both known class
and unknown class samples, number of known classiﬁ-
cations N, number of top-score predictions to calibrate
α.
2: Stage-I: Train
3: Initialize Open-RFNet as Open-RFNet-B with feature
extraction moduleF, classiﬁcation headC, and projection
headP, that is Open-RFNet-B ={F,C,P};
4: Train Open-RFNet-B from Dtrain;
5: Train a DCGAN model G fromDtrain;
6: Select simulated unknown samples Dsimu with Open-
RFNet-B;
7: Construct Open-RFNet by freezingF and retrainingC on
Dtrain∪D simu;
8: for each sample xi∈D train do
9: vi(x), ˆyi = Open-RFNet(xi);
10: end for
11: for each known classiﬁcation j∈{ 1,...,N } do
12: CalculateSj with Eq. (24);
13: Calculate MA V ,µj = mean(Sj);
14: Calculate ρj with Eq. (25);
15: end for
16: Stage-II: Test
17: for each sample xi∈D test do
18: vi(x), ˆyi = Open-RFNet(xi);
19: Lets(k) = argsort(vi(x)), Let cj(x) = 1;
20: fork = 1,...,α do
21: ifs(k)⁄=N + 1 then
22: Calculatecs(k)(x) with Eq. (28);
23: else
24: Calculatecs(k)(x) with Eq. (29);
25: end if
26: end for
27: Calculate ˜vi(x) with Eq. (26);
28: Calculate ˜vi,N +1(x) with Eq. (27) and calculate ˆP (y =
C|x) with Eq. (30);
29: Let ˜y = argmax( ˆP (y =C|x));
30: Output: Open-set recognition result ˜y.
31: end for
convolutional unit consists of a convolution layer followed
by a batch normalization layer. We denote by U the total
number of such convolution–batch normalization units, while
the index u = 1,...,U is used to enumerate them in the
subsequent complexity analysis. We assume that the batch size
is B, the number of input channels is Cin, the number of
output channels is Cout, the size of the input feature map is
H×W . We assume that all convolution kernels and pooling
windows are square, where Kconv, Kavg and Kmax denote
the side lengths of the convolution kernel, average pooling
window, and max pooling window, respectively. Then, the time
complexity of the convolutional layers can be represented as
O(Cin×Cout×K 2conv×H×W ), the batch normalization
layers can be represented asO(B×Cout×H×W ), the average
pooling layer can be represented as O(Cin×K 2avg×H×W ),
and of the max pooling layer can be represented as O(Cin×
K 2max×H×W ). Hence, the time complexity of the texture
feature extraction can be denoted as
O
( U∑
u=1
Cuin×Cuout× (Kuconv)2×Hu×Wu
)
+O
( U∑
u=1
B×Cuout×Hu×Wu
)
+O(Cin×K 2avg×H×W ) +O(Cin×K 2max×H×W ).
(33)
The time complexity of position features mainly comes from
position encoding and the TE. Therein the time complexity
of position encoding is O(𝓁× d), where 𝓁 is the length
of the sequence, while d is the length of the word vector.
The time complexity of TE mainly comes from the matrix
operation among the linear transformation and the query ( Q),
the key (K), and the value (V ). The time complexity of linear
transformation can be expressed asO(𝓁×d2), whereas the time
complexity of matrix operations can be denoted as O(𝓁2×d).
Therefore, the overall time complexity can be denoted as
O(𝓁×d2 +𝓁2×d). (34)
Hence, the time complexity of the entire feature extraction part
can be represented as
O(𝓁×d) +O(𝓁×d2 +𝓁2×d). (35)
With the quantitative analysis, we can calculate the
parameter count and the computational complexity of the
Open-RFNet, as shown in Table II. It can be found that by
incorporating the position feature extraction module based on
ResNet, the total number of parameters and their size increased
by nearly 292 times, whereas the total number of ﬂoating-point
operations (FLOPs) required for a single forward propagation
of the model increased by 1.19 times, i.e., the ﬁnal FLOPs are
2.19 times the original.
As UA V RF recognition is a real-time application, we
further analyze the end-to-end response time of the system,
including: (i) signal receiving time, (ii) signal preprocess-
ing time with slicing, denoising, and STFT operations, and
(iii) model inference time. In practice, the receiving time
is determined by the sampling window. In the DroneRFa
dataset used in this study, each sample contains approxi-
mately 300,000 IQ samples, collected at a sampling rate of
100 MS/s, corresponding to a signal receiving time of about
3 ms. The preprocessing stage is dominated by the STFT
operation, with an average latency of 21.76 ms per sample. For
model inference, the inference latency is 14.41 ms for ResNet
and 54.21 ms for Open-RFNet. Although the latter incurs
slightly higher latency, both remain within the millisecond
range. Overall, the entire processing pipeline operates at the
millisecond level, which can meet the real-time requirements
of UA V monitoring and identiﬁcation applications.
VII. E XPERIMENTS
A. Experimental Setting
To compare the performances with the state-of-the-art meth-
ods [9], [26], [27], [35], we use the public dataset DroneRFa
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

4092 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
TABLE II
MODEL PARAMETERS , C OMPUTATION , AND INFERENCE LATENCY
TABLE III
THE CLASSES OF THE USED DATASET
as the benchmark dataset, which includes the RF signals
of 24 common types of UA Vs and ﬂight controllers, and
one type of background signal as a reference. The speciﬁc
settings are shown in Table III. The RF signal collection
covers three Industrial Scientiﬁc Medical (ISM) bands, namely
915 MHz, 2.4 GHz and 5.8 GHz, which are collected by
a universal software radio peripheral (USRP) and monitored
simultaneously in a dual-channel mode. Therein, 15 types of
UA V signals are collected indoors in hovering mode and 5
meters away from the receiver. In addition, the signals of 9
types of UA Vs are collected outdoors and are divided into
three classiﬁcations according to the actual ﬂight distance:
near, medium, and far. However, some signals at medium
and long distances are very weak or even non-existent, which
makes these data samples untrainable. Therefore, considering
the availability of the data, we select the signals collected at
near distances and indoors for experiment evaluation. Finally,
we slice the I/Q data into small segments of 3 ms with 300,000
data points and obtain a time-frequency matrix of (775, 775)
via the STFT.
The division of the known and the unknown classiﬁcations
is shown in Table IV. A total of 20 known classiﬁcations and
5 unknown classiﬁcations are selected. The model is trained
using a Tesla V100 SXM2 32GB graphics card. The sampling
rate is 100 MS/s, the batchsize is 128 and the optimizer
is Adam. The maximum number of epochs for contrastive
Fig. 4. Training loss with respect to the epoch.
TABLE IV
THE DIVISION OF KNOWN CLASSES AND UNKNOWN CLASSES
IN THE DATASET
learning pre-training is set to be 30, while the subsequent
classiﬁcation ﬁne-tuning training lasts for 10 epochs. The
learning rate is scheduled by using the cosine annealing
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

GAO et al.: MULTI-DOMAIN SUPERVISED CONTRASTIVE LEARNING FOR UA V RF OPEN-SET RECOGNITION 4093
TABLE V
COMPARISON OF OPEN -RFN ET WITH SUPRESNET, TRANS NET, AND RESNET
TABLE VI
COMPARISON BETWEEN THE DENOISED AND THE NOISY DATA
algorithm. Figure 4 shows that the proposed Open-RFNet can
converge normally in both stages and has no overﬁtting.
B. Evaluation Indicator
We use the known accuracy rate (KAR), unknown accuracy
rate (UAR), known precision (KP), unknown precision (UP),
and performance gap (GAP) to comprehensively evaluate the
proposed method, which are given by
KAR = CKTK +FU ,
UAR = TUTU +FK ,
KP = CKTK +FK ,
UP = TUTU +FU ,
GAP =|UAR− KAR|, (36)
where TK , TU , FK and FU are the numbers of test
samples that are identiﬁed as true known, true unknown,
false known, and false unknown, respectively. The number
of correctly known samples, i.e., CK , represents the total
number of the known test samples that are correctly classiﬁed
into the exact known classiﬁcations. The GAP is deﬁned as
the absolute value of the difference between UAR and KAR,
which is used to measure the balance between the recognition
performance of the known classiﬁcation and the unknown
classiﬁcation.
C. Ablation Experiment
Before presenting the ablation results, we clarify the def-
initions of the comparison models used in this section.
SupResNet refers to a ResNet backbone equipped only with
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

4094 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
TABLE VII
COMPARISON OF THE PROPOSED OPEN -RFN ET WITH S3R M ODEL AND UIOS M ODEL
TABLE VIII
COMPARISON AMONG OPEN -SET RECOGNITION METHODS
the supervised contrastive learning module. TransNet denotes
a model where the ResNet is replaced by the proposed
TE, without using supervised contrastive learning. These two
models are designed to isolate the effects of the TE and
the supervised contrastive learning, respectively, and serve
as baseline variants for evaluating the contribution of each
component in the proposed Open-RFNet. To verify the effec-
tiveness of the constructed TE, supervised contrastive learning
and the denoising preprocessing module in the proposed Open-
RFNet, the ablation experiments are conducted for open-set
recognition. We ﬁrst verify the importance of the introduced
TE and supervised contrastive learning, which as illustrated
in Table V. The red values in the parentheses of the table
represent the differences of the component missing models
compared to Open-RFNet. It can be seen that when the TE
or the supervised contrastive learning is introduced alone on
the basis of ResNet, no performance improvement can be
achieved. However, if both the Transformer structure and the
supervised contrastive learning are added simultaneously, a
signiﬁcant improvement in recognition performance can be
obtained. Speciﬁcally, the KAR of TransNet with the TE
introduced alone is only 95.79%, and the UAR is 87.6%.
Compared with the ResNet, they decrease by 0.73% and 3.68%
respectively. This indicates that the recognition performance
deteriorates both in the known classiﬁcations and the unknown
classiﬁcations, especially for the latter. After introducing the
supervised contrastive learning only, the KAR and UAR also
decrease by 0.77% and 0.8% respectively. Yet, after adding
both the TE and the supervised contrastive learning, the TKR
decreases by 1.4%, while the TUR increases by 4.8%. This
implies that we sacriﬁce a certain recognition performance of
the known classiﬁcations in exchange for a huge performance
improvement in the recognition of the unknown classiﬁcations.
From the perspective of the overall recognition performance,
we ﬁnd that the proposed Open-RFNet is more balanced
and has better performance in the recognition of both the
known and the unknown classiﬁcations. Additionally, we ver-
ify the effectiveness of the proposed denoising preprocessing.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

GAO et al.: MULTI-DOMAIN SUPERVISED CONTRASTIVE LEARNING FOR UA V RF OPEN-SET RECOGNITION 4095
The results are shown in Table VI. The red values in the
parentheses of the table represent the differences between
the denoised model and the noisy model. It can be clearly
observed that after data denoising, the open-set recognition
performance has been signiﬁcantly improved compared with
the noisy data. Speciﬁcally, in the noisy data, the IG-OpenMax
algorithm performs poorly on each model, with the highest
accuracy for the unknown classiﬁcation recognition being only
66.08% and the lowest being 52.16%, indicating a relatively
low recognition performance. After denoising preprocessing,
the recognition performance for the unknown classiﬁcations
increased signiﬁcantly, where the highest is 96.08% and the
lowest is 87.6%.
D. Comparison of Different Algorithms
Here, we focus on comparing different state-of-the-art
open-set recognition algorithms. To ensure clarity, we ﬁrst
describe the models involved in this comparison. The Open-
RFNet is the proposed model based on the IG-OpenMax
algorithm. Open-RFNet-B follows the same feature extraction
pipeline but replaces IG-OpenMax with the classical OpenMax
algorithm [26]. Open-RFNet-G further replaces the open-set
module with the G-OpenMax method [27]. In addition, S3R
[9] and UIOS [35] are two state-of-the-art open-set recognition
methods, and we reproduce their models strictly following
the conﬁgurations described in their original papers. Further-
more, Open-RFNet-S3R-O and Open-RFNet-UIOS-O denote
the variants where the open-set module in Open-RFNet is
replaced by the S3R and UIOS algorithms, respectively, while
keeping the feature extraction network unchanged. Based on
these deﬁnitions, we compare the proposed Open-RFNet with
Open-RFNet-B, Open-RFNet-G, the S3R model, and the UIOS
model to evaluate open-set recognition performance under
consistent settings. First, we compare the proposed Open-
RFNet with the open-set recognition S3R and UIOS models,
and the results are shown in Table VII. The red values
in the parentheses of the table represent the performance
differences. It can be found that the KUR of the S3R model
is extremely high, and can almost recognize the unknown
classes with 100% accuracy, but it performs poorly in terms
of KAR, which is only 90.86%. Moreover, there is a large
difference in the recognition accuracy of various classes. In
particular, the recognition accuracies of the classes T0011,
T0100, and T0111 are all less than 80%. On the contrary,
Open-RFNet performs well on the known classes, with each
recognition accuracy of class above 90% and an overall
recognition accuracy of 95.12%. For the UIOS model, its
KAR is close to that of the the Open-RFNet, but the UAR
is 2.16% lower than that of Open-RFNet, which indicates
that its recognition ability for the unknown samples is weaker
than that of the Open-RFNet. Next, to further evaluate the
performance of the proposed IG-Openmax algorithm, we com-
pare the Open-RFNet with Open-RFNet-B, Open-RFNet-G,
Open-RFNet-S3R-O, and Open-RFNet-UIOS-O algorithms,
where the abbreviations S3R-O and UIOS-O denote the
open-set algorithms of the S3R and the UIOS models. The
results are shown in Table VIII. The red values in the
parentheses of the table represent the performance differ-
Fig. 5. Visualization of the distribution of known classiﬁcations.
ences. For the Open-RFNet, compared with the OpenMax
algorithm, the IG-OpenMax algorithm increases the UAR
by 2.24%, and compared with the G-OpenMax algorithm,
the UAR increases by 2.96%, with the KAR also remaining
almost unchanged. The IG-OpenMax algorithm can effec-
tively improve the recognition performance of the unknown
classes without compromising the recognition performance of
the known classes. Compared with the S3R-O and UIOS-O
algorithms, the IG-OpenMax algorithm shows improvements
in both the KAR and UAR. Moreover, the UIOS-O algorithm
cannot recognize the unknown classes based on the Open-
RFNet structure, where the performance gap reaches 93.98%.
The signiﬁcant performance differences between the UIOS-O
and the S3R-O algorithms arise from both the model structure
and the loss function, as well as the training strategy. The
UIOS-O and S3R-O algorithms have to revise the loss
functions for subsequent open-set recognition during model
training, whereas the proposed IG-OpenMax algorithm only
uses the commonly cross-entropy loss function, which is more
versatile and has lower training overhead.
E. Explanation of IG-OpenMax
Figure 5 provides a feature-level visualization of the real
unknown class samples and the generated unknown samples
under the G-OpenMax and IG-OpenMax algorithms. In the IG-
OpenMax case, i.e., Fig. 5a, the generated unknown samples
almost fully overlap with the real unknown samples in the fea-
ture space. This conﬁrms that, by freezing the feature extractor
and retraining only the classiﬁcation head, the original feature
structure learned by Open-RFNet-C is preserved. Within this
unchanged feature space, the misclassiﬁed generated samples
tend to lie in boundary regions, where real unknown sam-
ples are also likely to appear. As a result, the generated
samples can faithfully approximate the true unknown class
distribution, enabling the classiﬁer to learn more effectively
decision boundaries for open-set recognition.
In contrast, the G-OpenMax visualization in Fig. 5b shows
that the generated unknown samples form a cluster that is
entirely separated from the real unknown samples. This sepa-
ration arises because G-OpenMax retrains the entire network,
which causes the feature space to shift signiﬁcantly. In the new
feature space, the model is able to easily distinguish generated
samples from real data, which prevents the generated unknown
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

4096 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 6. Visualization of the distribution of known classiﬁcations.
Fig. 7. Visualization of the distributions of known and unknown classiﬁcations.
samples from serving as valid approximations of the real
unknown classes.
These observations demonstrate that freezing the feature
extractor is crucial. Therein, the IG-OpenMax maintains the
discriminative structure of the original feature space, ensures
similarity between generated and real unknown samples at the
feature level, and ultimately leads to substantially improved
open-set recognition performance.
F . Explanation of Proposed Model With Visualization
The performance among the models can be explained by
visualizing the A Vs. In Fig. 6and Fig. 7, we illustrate a visual-
ization of the A Vs for the four models, which are Open-RFNet,
SupResNet, TransNet, and ResNet. To clearly demonstrate the
performance differences, the models are completely generated
from the known classiﬁcation, and no generated unknown
classiﬁcation samples are added. This is because the generated
unknown classiﬁcation samples selected by different models
are inconsistent, which can avoid the inﬂuence caused by
inconsistent training data. For the unknown classiﬁcation, only
T10110 is selected, and for the known classiﬁcations, T10101,
T10010, T10111, and T1110 are selected.
First, we focus on ResNet and SupResNet. It can be clearly
observed that the distance between classes has signiﬁcantly
increased, whether in the separation of known classes or the
distribution of unknown classes. This reﬂects the characteristic
of supervised contrastive learning in pulling apart heteroge-
neous samples. However, the overlap between the unknown
classes and the known classes still exists, indicating that
the known and the unknown classes cannot be distinguished
relying solely on texture features. Then, we focus on ResNet
and TransNet, both of which are trained using the cross-
entropy loss function. It can be found that the two models are
highly similar in the distribution of known categories. In the
joint distribution of the known and the unknown classes, and
although there are slight differences between them, the overlap
between unknown and known classes is similar. This indicates
that when training with the cross-entropy loss function, an
imbalance in multi-feature optimization occurs; that is, the
model pays much attention to the texture features while
ignoring the time-frequency position features, leading to the
similarity in the visualization results. Then, for the ResNet
and the Open-RFNet, it can be seen that after adding both
time-frequency position features and supervised contrastive
learning, the known classes and the unknown classes are
clearly distinguished. Although there are still a few unknown
class samples close to the known classes, they are all at the
edge of the distribution, which can be easily recognized by
open-set recognition algorithms. This shows that the super-
vised contrastive learning effectively solves the problem of
imbalance in multi-feature optimization, enabling the model to
fully learn the position features, thereby achieving enhanced
UA V RF recognition performance.
VIII. C ONCLUSION
This paper proposed an MD-SupContrast framework for
UA V recognition for an open-set scenario. The proposed
Open-RFNet utilized the ResNet and the TE modules to
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

GAO et al.: MULTI-DOMAIN SUPERVISED CONTRASTIVE LEARNING FOR UA V RF OPEN-SET RECOGNITION 4097
extract texture features and time-frequency position features
of the RF signals, realized feature fusion, and incorporated
supervised contrastive learning to further optimize the features.
In addition, an IG-OpenMax algorithm was also conceived to
balance the recognition performance between the closed-set
and the open-set. When introducing the generated unknown
samples, the feature extraction part is frozen, and only the
classiﬁcation head is retrained, enabling the model to better
distinguish between the known and the unknown classiﬁca-
tions. Compared with the advanced methods, the superiority of
the proposed method was demonstrated. Speciﬁcally, we can
recognize 25 UA V types with recognition accuracy 95.12%
in closed-set and 96.08% in open-set, respectively, while the
performance gap is less than 1%. We found that the comple-
mentary recognition mechanism between the time-frequency
domain position features and the supervised contrastive learn-
ing effectively improves the distribution relationship between
the samples of the known and the unknown classiﬁcations,
thereby signiﬁcantly enhancing the UA V RF open-set recog-
nition performance.
It is worth noting that the proposed framework is developed
under the single UA V emitter assumption, where only one
UA V RF emission is present within the given time. However,
simultaneously recognizing multiple UA V emitters is a mean-
ingful and challenging problem, as superimposed RF signals
will introduce severe mutual interference and signiﬁcantly
complicate the extraction of discriminative features. Thus,
in our future research, we will focus on multiple UA V RF
recognition and further pursue their open-set recognition.
REFERENCES
[1] J. Mu, R. Zhang, Y . Cui, N. Gao, and X. Jing, “UA V meets integrated
sensing and communication: Challenges and future directions,” IEEE
Commun. Mag., vol. 61, no. 5, pp. 62–67, May 2023.
[2] N. Gao, Z. Qin, X. Jing, Q. Ni, and S. Jin, “Anti-intelligent UA V
jamming strategy via deep Q-networks,” IEEE Trans. Commun., vol. 68,
no. 1, pp. 569–581, Jan. 2020.
[3] N. Gao, L. Liang, D. Cai, X. Li, and S. Jin, “Coverage control for UA V
swarm communication networks: A distributed learning approach,”IEEE
Internet Things J., vol. 9, no. 20, pp. 19854–19867, Oct. 2022.
[4] M. H. Rahman, M. A. S. Sejan, M. A. Aziz, R. Tabassum, J.-I. Baik,
and H.-K. Song, “A comprehensive survey of unmanned aerial vehicles
detection and classiﬁcation using machine learning approach: Chal-
lenges, solutions, and future directions,” Remote Sens., vol. 16, no. 5,
p. 879, Mar. 2024.
[5] M. F. Al-Sa’D, A. Al-Ali, A. Mohamed, T. Khattab, and A. Erbad, “RF-
based drone detection and identiﬁcation using deep learning approaches:
An initiative towards a large open source drone database,” Future Gener .
Comput. Syst., vol. 100, pp. 86–97, Nov. 2019.
[6] R. Xie et al., “A generalizable model-and-data driven approach for open-
set RFF authentication,” IEEE Trans. Inf. F orensics Security, vol. 16,
pp. 4435–4450, 2021.
[7] D. Cai et al., “Reconﬁgurable intelligent surface-induced randomness for
mmWave key generation,” in Proc. IEEE ICC, May/Jun. 2025, pp. 1–6.
[8] S. Tao, M. Mei, J. Luo, L. Yan, and X. Huang, “A threshold insensitive
open-set recognition scheme for AA V targets based on HRRP,” IEEE
Trans. Aerosp. Electron. Syst., vol. 61, no. 2, pp. 4766–4775, Apr. 2025.
[9] N. Yu, J. Wu, C. Zhou, Z. Shi, and J. Chen, “Open set learning for
RF-based drone recognition via signal semantics,” IEEE Trans. Inf.
F orensics Security, vol. 19, pp. 9894–9909, 2024.
[10] N. Yu, S. Mao, C. Zhou, G. Sun, Z. Shi, and J. Chen, “DroneRFa:
A large-scale UA V RF signal dataset for low-altitude drone detection,”
J. Electron. Inf. Technol., vol. 46, no. 4, pp. 1147–1156, 2024.
[11] V . Brik, S. Banerjee, M. Gruteser, and S. Oh, “Wireless device iden-
tiﬁcation with radiometric signatures,” in Proc. 14th ACM Int. Conf.
Mobile Comput. Netw., Sep. 2008, pp. 116–127.
[12] Y . Lin, Y . Tu, and Z. Dou, “An improved neural network pruning
technology for automatic modulation classiﬁcation in edge devices,”
IEEE Trans. V eh. Technol., vol. 69, no. 5, pp. 5703–5706, May 2020.
[13] K. Sankhe, M. Belgiovine, F. Zhou, S. Riyaz, S. Ioannidis, and
K. Chowdhury, “ORACLE: Optimized radio clAssiﬁcation through
convolutional neural networks,” in Proc. IEEE Conf. Comput. Commun.
(INFOCOM), Apr. 2019, pp. 370–378.
[14] L. Peng, J. Zhang, M. Liu, and A. Hu, “Deep learning based RF
ﬁngerprint identiﬁcation using differential constellation trace ﬁgure,”
IEEE Trans. V eh. Technol., vol. 69, no. 1, pp. 1091–1095, Jan. 2020.
[15] N. Gao, Y . Liu, Q. Zhang, X. Li, and S. Jin, “Let RFF do the
talking: Large language model enabled lightweight RFFI for 6G edge
intelligence,” Sci. China Inf. Sci., vol. 68, no. 7, Jul. 2025, Art. no.
170308.
[16] Y . Wang, G. Gui, H. Gacanin, T. Ohtsuki, O. A. Dobre, and H. V . Poor,
“An efﬁcient speciﬁc emitter identiﬁcation method based on complex-
valued neural networks and network compression,” IEEE J. Sel. Areas
Commun., vol. 39, no. 8, pp. 2305–2317, Aug. 2021.
[17] D. Xu, Y . Zhu, Y . Lu, Y . Feng, Y . Lin, and Q. Xuan, “MCLRL: A multi-
domain contrastive learning with reinforcement learning framework for
few-shot modulation recognition,” 2025, arXiv:2502.19071.
[18] M. Ezuma, F. Erden, C. K. Anjinappa, O. Ozdemir, and I. Guvenc,
“Micro-UA V detection and classiﬁcation from RF ﬁngerprints using
machine learning techniques,” in Proc. IEEE Aerosp. Conf., Mar. 2019,
pp. 1–13.
[19] T. Huynh-The, Q.-V . Pham, T.-V . Nguyen, D. B. D. Costa, and
D.-S. Kim, “RF-UA VNet: High-performance convolutional network
for RF-based drone surveillance systems,” IEEE Access, vol. 10,
pp. 49696–49707, 2022.
[20] Z. Cai, Y . Wang, Q. Jiang, G. Gui, and J. Sha, “Toward intelligent
lightweight and efﬁcient UA V identiﬁcation with RF ﬁngerprinting,”
IEEE Internet Things J., vol. 11, no. 15, pp. 26329–26339, Aug. 2024.
[21] F. G ¨okc ¸e, G.¨Uc ¸oluk, E. S ¸ahin, and S. Kalkan, “Vision-based detection
and distance estimation of micro unmanned aerial vehicles,” Sensors,
vol. 15, no. 9, pp. 23805–23846, Sep. 2015.
[22] ´A. D. de Quevedo, F. I. Urzaiz, J. G. Menoyo, and A. A. L ´opez, “Drone
detection with X-band ubiquitous radar,” in Proc. 19th Int. Radar Symp.
(IRS), Jun. 2018, pp. 1–10.
[23] S. Al-Emadi, A. Al-Ali, A. Mohammad, and A. Al-Ali, “Audio based
drone detection and identiﬁcation using deep learning,” in Proc. 15th
Int. Wireless Commun. Mobile Comput. Conf. (IWCMC), Jun. 2019,
pp. 459–464.
[24] W. J. Scheirer, A. de Rezende Rocha, A. Sapkota, and T. E. Boult,
“Toward open set recognition,” IEEE Trans. Pattern Anal. Mach. Intell.,
vol. 35, no. 7, pp. 1757–1772, Jul. 2013.
[25] M. A. Cordova Neira, P. Ribeiro Mendes Junior, A. Rocha, and
R. Da Silva Torres, “Data-fusion techniques for open-set recognition
problems,” IEEE Access, vol. 6, pp. 21242–21265, 2018.
[26] A. Bendale and T. E. Boult, “Towards open set deep networks,” in
Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2016,
pp. 1563–1572.
[27] Z. Ge, S. Demyanov, Z. Chen, and R. Garnavi, “Generative openmax
for multi-class open set classiﬁcation,” 2017, arXiv:1707.07418.
[28] J. Qian, J. Wang, X. Li, and S. Jin, “UA V-MIMO under wobbling: A
comparative analysis of centralized and distributed implementations,”
IEEE Trans. Commun., vol. 73, no. 8, pp. 6825–6839, Aug. 2025.
[29] P. Khosla et al., “Supervised contrastive learning,” in Proc. NIPS, 2020,
pp. 18661–18673.
[30] T. Chen, S. Kornblith, M. Norouzi, and G. Hinton, “A simple framework
for contrastive learning of visual representations,” in Proc. ICML, Jul.
2020, pp. 1597–1607.
[31] M. Bi, M. Wang, Z. Li, and D. Hong, “Vision transformer with
contrastive learning for remote sensing image scene classiﬁcation,” IEEE
J. Sel. Topics Appl. Earth Observ. Remote Sens., vol. 16, pp. 738–749,
2023.
[32] W. Liu, Y . Wen, Z. Yu, and M. Yang, “Large-margin softmax loss for
convolutional neural networks,” 2016, arXiv:1612.02295.
[33] X. Peng, Y . Wei, A. Deng, D. Wang, and D. Hu, “Balanced
multimodal learning via on-the-ﬂy gradient modulation,” in Proc.
IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), Jun. 2022,
pp. 8228–8237.
[34] I. Gulrajani, F. Ahmed, M. Arjovsky, V . Dumoulin, and A. C. Courville,
“Improved training of Wasserstein GANs,” in Proc. Adv. Neural Inf.
Process. Syst., vol. 30, 2017, pp. 1–11.
[35] M. Wang et al., “Uncertainty-inspired open set learning for retinal
anomaly identiﬁcation,” Nature Commun., vol. 14, no. 1, p. 6757, Oct.
2023.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

4098 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Ning Gao (Member, IEEE) received the Ph.D.
degree in information and communications engi-
neering from Beijing University of Posts and
Telecommunications, Beijing, China, in 2019. From
2017 to 2018, he was a Visiting Ph.D. Student
with the School of Computing and Communica-
tions, Lancaster University, Lancaster, U.K. From
2019 to 2022, he was a Research Fellow with the
National Mobile Communications Research Labo-
ratory, Southeast University, Nanjing, China. He is
currently an Associate Professor with the School of
Cyber Science and Engineering, Southeast University. His research interests
include AI enabled wireless communications and security, RIS, and UA V
communications.
Tianrui Zeng (Student Member, IEEE) received the
B.S. degree in information security from the Uni-
versity of Science and Technology, Beijing, China,
in 2024. He is currently pursuing the M.S. degree
with the School of Cyber Science and Engineering,
Southeast University, Nanjing, China. His research
interests include wireless communication security
and deep learning.
Bowen Chen is currently pursuing the B.S. degree
with the School of Cyber Science and Engi-
neering, Southeast University, Nanjing, China. His
research interests include radio frequency ﬁngerprint
identiﬁcation and deep learning for wireless commu-
nications.
Donghong Cai (Senior Member, IEEE) received
the B.S. degree from the School of Mathemat-
ics and Information Sciences, Shaoguan University,
Shaoguan, China, in 2012, and the M.S. and
Ph.D. degrees from Southwest Jiaotong University,
Chengdu, China, in 2015 and 2020, respectively.
From October 2017 to October 2018, he was a
Visiting Ph.D. Student with Lancaster University,
Lancaster, U.K., and The University of Manch-
ester, Manchester, U.K. He is currently an Associate
Professor with the College of Information Science
and Technology/College of Cyber Security, Jinan University, Guangzhou,
China. His current research interests include signal detection, security coding,
machine learning, privacy preservation, semantic communication, and multiple
access techniques.
Shi Jin (Fellow, IEEE) received the B.S. degree in
communications engineering from Guilin University
of Electronic Technology, Guilin, China, in 1996, the
M.S. degree from Nanjing University of Posts and
Telecommunications, Nanjing, China, in 2003, and
the Ph.D. degree in information and communications
engineering from Southeast University, Nanjing, in
2007. From June 2007 to October 2009, he was a
Research Fellow with the Adastral Park Research
Campus, University College London, London, U.K.
He is currently afﬁliated as a Faculty Member of the
National Mobile Communications Research Laboratory, Southeast University.
His research interests include wireless communications, random matrix theory,
and information theory. He and his co-authors were awarded the 2011 IEEE
Communications Society Stephen O. Rice Prize Paper Award in the ﬁeld
of Communication Theory, the 2022 Best Paper Award, the 2010 Young
Author Best Paper Award by the IEEE Signal Processing Society, the 2023
Jack Neubauer Memorial Award by the IEEE Vehicular Technology Society,
and the 2024 Marconi Prize Paper Award by the IEEE Communications
Society. He serves as an Area Editor for IEEE T RANSACTIONS ON COM-
MUNICATIONS and IET Electronics Letters. Previously, he was an Associate
Editor of IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE
COMMUNICATIONS LETTERS , and IET Communications.
Michail Matthaiou (Fellow, IEEE) received the
Ph.D. degree from the University of Edinburgh,
U.K., in 2008. He is currently a Professor of Com-
munications Engineering and Signal Processing and
Deputy Director of the Centre for Wireless Innova-
tion (CWI) at Queen’s University Belfast, U.K. He
is also an Eminent Scholar at the Kyung Hee Univer-
sity, Republic of Korea. He has held research/faculty
positions at Munich University of Technology
(TUM), Germany, and Chalmers University of Tech-
nology, Sweden. His research interests span signal
processing for wireless communications, beyond massive MIMO, reﬂecting
intelligent surfaces, mm-wave/THz systems, and AI-empowered communi-
cations. He and his coauthors received the IEEE Communications Society
(ComSoc) Leonard G. Abraham Prize in 2017. He currently holds the
ERC Consolidator Grant BEATRICE (2021-2026) focused on the interface
between information and electromagnetic theories. To date, he has received
the prestigious 2023 Argo Network Innovation Award, the 2019 EURASIP
Early Career Award and the 2018/2019 Royal Academy of Engineering/The
Leverhulme Trust Senior Research Fellowship. His team was also the Grand
Winner of the 2019 Mobile World Congress Challenge. He was the recipient of
the 2011 IEEE ComSoc Best Young Researcher Award for the Europe, Middle
East and Africa Region and a co-recipient of the 2006 IEEE Communications
Chapter Project Prize for the best M.Sc. dissertation in the area of commu-
nications. He has co-authored papers that received best paper awards at the
2018 IEEE WCSP and 2014 IEEE ICC. In 2014, he received the Research
Fund for International Young Scientists from the National Natural Science
Foundation of China. He is currently the Editor-in-Chief of Elsevier Physical
Communication, a Senior Editor for IEEE W IRELESS COMMUNICATIONS
LETTERS and IEEE S IGNAL PROCESSING MAGAZINE , an Area Editor for
IEEE T RANSACTIONS ON COMMUNICATIONS and Editor-in-Large for OPEN
JOURNAL OF THE COMMUNICATIONS SOCIETY . He is an AAIA Fellow.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:15:31 UTC from IEEE Xplore.  Restrictions apply.
