---
type: literature-fulltext
title: "MTL-CNET: An Advanced Integrated Sensing and Communication Framework Utilizing Complex Neural Networks and Multi-Task Learning"
zotero_key: "I6SRNUEU"
pdf_key: "6PCASD4J"
doi: "10.1109/TWC.2025.3596901"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/MTL-CNET- An Advanced Integrated Sensing and Communication Framework Utilizing Complex Neural Networks and Multi-Task Learning.md"
fulltext_path: "03fulltext/备选讲组会论文/I6SRNUEU.md"
zotero_item: "zotero://select/library/items/I6SRNUEU"
zotero_pdf: "zotero://open-pdf/library/items/6PCASD4J"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# MTL-CNET: An Advanced Integrated Sensing and Communication Framework Utilizing Complex Neural Networks and Multi-Task Learning

> PDF 原文逐页文本抽取；来源文件 SHA-256：`e8436a33333cc864e9fd32d08d337de1823286c149d4535eb3fc1614031b0cee`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

2484 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
MTL-CNET: An Advanced Integrated Sensing and
Communication Framework Utilizing Complex
Neural Networks and Multi-Task Learning
Qingqing Cheng
 , Member , IEEE, Zhenguo Shi
 , Member , IEEE, and Jinhong Yuan
 , Fellow, IEEE
Abstract—Integrated sensing and communication (ISAC) is
anticipated as a “game-changer” for the sixth generation systems
by enhancing both efﬁciency and reliability. However, critical
challenges remain, including performance degradation due to
the separate treatment of sensing and communication, ineffec-
tive processing of complex-valued wireless signals, and limited
adaptability to dynamic wireless environments. To address these
limitations, this paper explores orthogonal delay-Doppler divi-
sion multiplexing (ODDM)-enabled ISAC with passive sensing
(ISAC-PS) systems and proposes a novel ISAC framework,
called MTL-CNET, which leverages multi-task learning and
complex neural networks. MTL-CNET can facilitate sensing
and communication tasks concurrently while improving robust-
ness to environmental variations. Speciﬁcally, we develop a
novel three-dimensional complex convolutional neural network
(3D-CCNN) approach to process complex-valued ODDM signals
in a singular architecture, as opposed to two separate networks
in conventional methods. The 3D-CCNN effectively captures
the characteristics of real and imaginary components of sig-
nals and the intrinsic relationship between them for ISAC-PS
tasks. Moreover, we propose a multi-task learning framework
with inter-layer information exchange (MTL-IE), which achieves
simultaneous sensing and communication enhancement by using
the property of MTL and information exchange design. Addi-
tionally, a novel transfer-learning-based self-updating scheme
is proposed to enhance resilience to environmental ﬂuctuations
with minimized updating frequency and effort. Experimental
results demonstrate that MTL-CNET outperforms state-of-the-
art methods in sensing accuracy, communication reliability and
environmental robustness.
Index Terms—ISAC, complex deep neural network, mutli-task
learning, transfer learning, ODDM.
I. I NTRODUCTION
T
HE future wireless system, e.g., the sixth generation
(6G), is expected to bring paramount revolutions in
device-environment interactions. One of its primary objectives
Received 4 March 2025; revised 4 June 2025; accepted 5 August 2025.
Date of publication 15 August 2025; date of current version 22 December
2025. This work was supported by the ARC DECRA Scheme under Grant
DE250101065. The associate editor coordinating the review of this article and
approving it for publication was J. Xu. (Corresponding author: Zhenguo Shi.)
Qingqing Cheng was with the School of Electrical Engineering and
Telecommunications, University of New South Wales, Sydney, NSW 2033,
Australia. She is now with the School of Electrical Engineering and Robotics,
Queensland of University Technology, Brisbane, QLD 4000, Australia (e-mail:
qingqing.cheng@qut.edu.au).
Zhenguo Shi is with the School of Computer Science, Queens-
land of University Technology, Brisbane, QLD 4000, Australia (e-mail:
zhenguo.shi@qut.edu.au).
Jinhong Yuan is with the School of Electrical Engineering and Telecom-
munications, University of New South Wales, Sydney, NSW 2033, Australia
(e-mail: j.yuan@unsw.edu.au).
Digital Object Identiﬁer 10.1109/TWC.2025.3596901
is to encompass not just communication but also sensing
functionalities to address the escalating demands for advanced
wireless services, such as intelligent transportation systems,
environmental monitoring and healthcare, rather than focusing
on communications solely as done in the existing ﬁfth-
generation (5G) technologies [1], [2], [3]. A key enabler of
this vision is integrated sensing and communication (ISAC),
which enhances both capabilities within a uniﬁed framework.
In such a system, users will be endowed with the ability
to not only “talk” (communicate) to other entities but also
“see and hear” (sense) the surroundings, using the same
frequency resource and infrastructure [4], [5], [6]. This inte-
gration enhances spectrum efﬁciency, reduces hardware costs,
and enables applications such as autonomous driving and
immersive extended reality (XR). Recent advancements in
multiple-input multiple-output (MIMO) further enhance ISAC
by utilizing large antenna arrays for directional beamforming
and interference mitigation [7], [8]. MIMO improves spatial
resolution, enabling simultaneous multi-target sensing and
multi-user communication [9], [10]. As an advanced MIMO
technology, holographic MIMO enhances angular resolution
and energy efﬁciency, allowing ISAC to track multiple objects
while ensuring reliable communication [11], [12]. There-
fore, ISAC offers potential for improving spectrum efﬁciency
and reducing hardware costs, attracting tremendous research
attention.
To enable efﬁcient ISAC, various waveforms have been
explored, including orthogonal frequency division multiplex-
ing (OFDM) [13], [14], orthogonal time frequency space
(OTFS) [15], [16], and orthogonal delay-Doppler division
multiplexing (ODDM) [17], [18]. While OFDM is adopted
for its robustness against multipath fading and effective
frame synchronization, it suffers from a high peak-to-average
power ratio, leading to increased power inefﬁciency and
hardware complexity. Additionally, its sensitivity to fast
time-varying channels causes Doppler-induced inter-carrier
interference (ICI), disrupting subcarrier orthogonality and
degrading performance in high-mobility scenarios [16]. Given
these limitations, research has shifted from time-frequency
(TF) domain modulation in OFDM to delay-Doppler (DD)
domain modulation, including OTFS and ODDM [15], [18].
DD-domain modulation transforms time-varying channels in
the TF domain into quasi-time-invariant channels, enhancing
robustness against Doppler effects in high-speed environ-
ments. Among these, ODDM stands out for its practical
DD-domain pulses, superior resilience to Doppler shifts,
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

CHENG et al.: MTL-CNET: AN ADV ANCED INTEGRATED SENSING AND COMMUNICATION FRAMEWORK 2485
and inherent preservation of DD characteristics [3], [17].
These bring multiple beneﬁts including simpliﬁed input-
output relationships and channel operations, which are crucial
for sensing. These properties enable efﬁcient integration
of sensing and communication, making ODDM a promis-
ing and practical alternative for ISAC in high-mobility
systems.
Generally, the sensing function in ISAC can be catego-
rized into active sensing and passive sensing, based on the
characteristics of the sensing signals [19], [20]. For “active
sensing”, the sensing receiver is co-located with the transmit-
ter, utilizing self-transmitted signals for sensing. Conversely,
in “passive sensing”, the sensing receiver and transmitter
are positioned separately, performing sensing tasks based on
signals from other entities [19], [21]. While “active sensing”
holds the promise for accuracy enhancement by leveraging
known transmitted signals, it may disclose sensitive informa-
tion about the transmitter or its surroundings, thereby posing
privacy issues [22]. In contrast, “passive sensing” effectively
addresses this concern by relying on signals from other nodes,
avoiding the transmission of private data inherent in active
sensing. Therefore, in this paper, we investigate ISAC with
passive sensing (ISAC-PS) due to its potential for privacy
protection.
In ISAC-PS, the sensing receiver is spatially separated from
the corresponding transmitter (similar to traditional commu-
nication processes). The key principle is utilizing the same
communication waveform for sensing, eliminating the need for
dedicated sensing signals. Toward that end, the pilot signals
in the communication process are usually used for sensing
activities, but effectiveness remains limited due to constraints
in time-frequency resources. Unlike pilot signals, data signals
offer abundant time-frequency features that can be explored
for sensing, but their unknown structure presents challenges
for direct utilization. Recognizing this problem, the authors
in [13] ﬁrst demodulated communication information, then
performed the sensing task by processing the demodulated
data and extracting multi-path echo signals reﬂected by the
target. With the same purpose, recent work in [23] devel-
oped a method for target sensing based on the multi-element
complex Taylor series of the demodulated communication
data. Similarly, a tensor decomposition-based method is
proposed in [24] to estimate the target’s parameters by ana-
lyzing the characteristics of communication data. The authors
in [14] designed a multiple-signal classiﬁcation (MUSIC)-
based sensing method using received communication signals.
While these methods achieved some progress, their sensing
performance is highly dependent on communication errors.
Moreover, they necessitate accurate wireless channel mod-
els beforehand, posing challenges in practical application
scenarios.
Deep learning (DL) demonstrates great potential in address-
ing the above challenges, so various DL architectures have
been widely employed. To name a few, the authors in [25] and
[26] utilized two-dimensional convolutional neural networks
(2D-CNN) and recurrent neural network (RNN), respectively,
to realize signal detection in the communication stage. The
authors in [27] developed a scheme to improve detection per-
formance, drawing support from the spatial-based generative
adversarial network. Apart from the above, a deep CNN was
utilized in [28] to sense targets while reducing processing over-
head. The authors in [29] and [30] employed three-dimensional
CNN and deep neural networks (DNN), respectively, for
target parameter sensing in multiple-input multiple-output
(MIMO) systems. Additionally, a recent scheme was pro-
posed in [31] to achieve joint sensing and communication
tasks by leveraging approximate message passing (MAP) and
DNN.
Despite advancements in DL-based ISAC-PS methods, sev-
eral challenges remain. First, most DL-based methods treat
sensing and communication as separate tasks, inevitably miss-
ing out on potential gains from their integration. Second,
wireless signals are inherently complex-valued, including real
and imagery components. However, conventional DL-based
methods always process these components independently,
neglecting their intrinsic connections and leading to degraded
performance in both sensing and communication. Third,
traditional DL models struggle with changes in wireless envi-
ronments caused by user movement or temporal variations.
Maintaining their effectiveness requires frequent updating
or re-training, demanding substantial new data from unseen
environments and considerable training effort. Therefore, DL-
based methods are still open research problems for ISAC-PS
systems.
Inspired by the above challenges, this work develops a
novel scheme to realize simultaneous sensing and com-
munication tasks in ISAC-PS systems, by leveraging the
property of a multi-task learning and complex neural net-
work, namely MTL-CNET. Our MTL-CNET aims to achieve
accurate sensing, reliable communication and environmental-
robust performance. It is important to note that conventional
DL-based methods typically execute sensing and communi-
cation tasks with two separate DL models via a sequential
order. This would increase the overall process overhead, lose
inherent interactions and risk error propagation from one task
to the next. To address the aforementioned problems, our
MTL-CNET enables mutual improvement and execution of
these tasks within a uniﬁed framework by leveraging the
property of multi-task learning (MTL) [32]. Speciﬁcally, we
for the ﬁrst time utilize MTL to effectively explore potential
features commonly shared between sensing and communi-
cation. As a result, the information mutually beneﬁcial for
both tasks is extracted, improving performance in both tasks
compared to their independent process. Moreover, to overcome
the constraints of traditional DL-based methods in processing
complex-valued numbers, we creatively exploit the complex
neural network (CNET) [33] to process complex-valued data
in an integrated manner, capturing the intrinsic relationships
between the real and imaginary parts of wireless signals.
This enables a more accurate representation and processing
of wireless signals, offering an enhancement in both sensing
and communication performance. To the best of the authors’
knowledge, this is the ﬁrst attempt to leverage MTL and CNET
to achieve joint sensing and communication tasks in ISAC-PS
systems. The major contributions of this work are summarized
below.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

2486 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
• We propose a novel framework speciﬁcally tailored
for concurrent sensing and communication tasks in
ISAC-PS systems, referred to as MTL-CNET. MTL-
CNET creatively leverages the properties of MTL and
CNET for simultaneous multi-task processing and com-
prehensive feature extraction, along with an innovative
updating scheme for updating effort reduction. As a
result, our MTL-CNET can accomplish simultaneous
sensing and communication tasks, offering precise sens-
ing, reliable communication and strong environmental
robustness.
• To achieve effective feature extraction, we develop an
innovative three-dimensional complex convolutional neu-
ral network (3D-CCNN) approach to process complex-
valued wireless signals in an integrated manner. The
proposed 3D-CCNN enables us to explore interconnec-
tions between the real and imaginary components of
complex-valued wireless signals. Consequently, a more
comprehensive representation of signal features can be
extracted, enhancing performance in both sensing and
communication tasks. By contrast, traditional DL models
typically handle two components of wireless signals
individually and separately, inevitably losing phase infor-
mation within complex-valued data and degrading system
performance.
• We design a novel scheme to accomplish tasks with
precise sensing and reliable communication performance
simultaneously, leveraging the property of MTL and the
information exchange module (MTL-IE). In particular,
we develop an inter-layer information exchange module
to achieve mutual improvement between sensing and
communication, contributing to enhanced performance in
both tasks. Moreover, our MTL-IE also enhances the gen-
eralization capabilities of MTL-CNET by mitigating the
risk of overﬁtting on task-speciﬁc data. It also enhances
computational and parameter efﬁciency by reducing the
need for separate DL models.
• To enhance environmental robustness, we develop an
innovative adaptive self-updating scheme (ASS), by uti-
lizing the power of transfer learning. The proposed
ASS effectively utilizes the knowledge acquired from
prior environments and bridges the feature gap between
these environments and the new (unseen) environment.
This enables our MTL-CNET to adapt to different envi-
ronmental conditions without requiring large amounts
of labeled data from the new environment which is
often scarce or costly to obtain. Moreover, rather than
retraining the entire DL model, our ASS selectively
updates speciﬁc parts of DL architecture, considerably
minimizing updating effort and improving environmental
robustness.
• We design and conduct comprehensive experiments
to verify the effectiveness of proposed MTL-CNET
under diverse settings and conﬁgurations. Extensive
results demonstrate that our MTL-CNET outperforms
the existing related methods, particularly in terms of
sensing precision, detection accuracy and updating effort
reduction.
II. S YSTEM MODEL AND PROBLEM FORMULATION
A. Principles of ISAC-PS
Without loss of generality, we consider a MIMO-enabled
ISAC-PS system, as illustrated in Fig. 1, where ODDM
is adopted for both sensing and communication due to its
robustness in high-mobility scenarios [3]. In this framework,
the sensing receiver operates separately from the transmit-
ter, reusing the same ODDM communication waveforms for
sensing. By processing the received ODDM signals, the pro-
posed MTL-CNET extracts unique features for simultaneous
multi-user communication and target sensing within a uni-
ﬁed framework. According to this ﬁgure, the transmitter and
receiver are equipped with Nt and Nr antennas, respectively.
Each antenna of the ISAC receiver captures signals from
multiple paths, including line-of-sight (LOS) and Non-line-
of-sight (NLOS) components. LOS signals, characterized by
their direct path from the transmitter to the receiver, are pivotal
for demodulating communication content due to their minimal
obstruction and reﬂection. Conversely, NLOS signals are the
reﬂections or diffractions from environmental objects, carrying
critical information about the surroundings. Consequently,
NLOS signals play a signiﬁcant role in both demodulat-
ing communication content and sensing objects/targets in
environments. According to this ﬁgure, the total number of
LOS and NLOS paths is Lp, and the number of targets
is Lp− 1.
Given the above discussion, for a pair of receive-transmit
antennas (nr,nt), the signal transmitted by nt-th transmit
antenna in the DD domain is expressed xnt [n,m ], where
n∈{ 0,...,N − 1} stands for the index along the Doppler
domain and m ∈ {0,...,M − 1} indicates the index
along the delay domain. According to [3], ODDM maps
DD domain symbols into M multi-carrier (MC) symbols,
where the symbol period is NT, the subcarrier spacing is
1
NT , and the symbol interval is TM . Then, we can obtain the
ODDM signal with cyclic preﬁx (CP) in the time domain
by [3]
ˆwnt(t)=
M−1∑
m=0
N−1∑
n=0
ˆscp
(
t−mTM)xnt[n,m ]ej2π nNT (t−mTM),
(1)
where−(G +Ds− 1)TM ≤ t≤ NT + (G− 1)TM , G≪ M2
is an integer. Ds denotes the delay spread. ˆscp(t) = 0
for t ∈
(
−T +GTM,−GTM) and ˆscp(t) = ˆ stx(t) for
t ∈
(
−GTM, (N− 1)T +GTM). ˆstx(t) is the transmitting
pulse. Note that, ˆstx(t) represents a DD domain pulse and
is orthogonal according to the DD resolutions, which can be
obtained by
ˆstx(t) =
N−1∑
n=0
a(t−nT ), (2)
where a(t) refers to the time-symmetric real-valued square-
root Nyquist pulse, with a time duration of 2GTM . Notably, as∫ +∞
−∞|a(t)|2dt = 1N ,∫ +∞−∞|ˆstx(t)|2dt = 1.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

CHENG et al.: MTL-CNET: AN ADV ANCED INTEGRATED SENSING AND COMMUNICATION FRAMEWORK 2487
Fig. 1. System model for ISAC-PS system.
At the receiver side, the transmitted signal for −(Ds +G−
1)TM≤t≤NT + (Ds +G− 2)TM is captured, expressed as
Ynr(t)
=
Lp∑
p=1
Nt∑
nt=1
hp(nr,nt) ˆwnt(t−τpnr)ej2πνpnr (t−τpnr )+znr(t)
=
Lp∑
p=1
Nt∑
nt=1
M−1∑
m=0
N−1∑
n=0
hp(nr,nt)x[n,m ]ˆsup
(
t−(m +lτpnr )TM)
×e
j2π
n+kνpnr
NT
(
t−(m+lτpnr )TM
)
ej2π
mkνpnr
MN + znr(t), (3)
where nr denotes the nrth receive antenna, Lp is the total
number of paths. τpnr = lτpnrM∆f stands for the delay shift at
the pth path, where lτpnr represents the corresponding delay
index, and ∆f means the subcarrier spacing. νpnr = kνpnrNT
depicts Doppler shift at the pth path, where kνpnr means thecorresponding Doppler index. znr(t) stands for the noise in the
DD domain.hp(nr,nt) is the channel coefﬁcient for the pth path
for the antenna pair (nr,nt), which can be written by angle-
of-arrival (AoA)θp and angle-of-departure (AoD) φp as hp =
βpar(θp)aHt (φp). βp refers to the path gain, and ar(θp)∈
CNr×1 and at(φp)∈ CNt×1 mean the receive and transmit
array response vectors, respectively, which are expressed as
ar(θp)=[1,e−j 2πλ dr cos (θp),...,e−j 2πλ dr(Nr−1) cos (θp)]T,
at(φp)=[1,e−j 2πλ dt cos (φp),...,e−j 2πλ dt(Nt−1) cos (φp)]T, (4)
where dr and dt are the antenna spacing for the receive and
transmit antennas, respectively. λ is the wavelength. Next, the
received signal in Equation (3) is transferred to DD domain
by applying the matched ﬁlter with ˆstx(t), which is [34]
ynr[n,m ]=
Lp∑
p=1
Nt∑
nt=1
hp(nr,nt)xnt
[
[n−kνpnr ]N,(m−lτpnr )
]
×ej2π
kνpnr (m−lτpnr )
MN +Znr[n,m], (5)
where [.]N denotes the mod N operation. Znr[n,m ] is the
noise in the DD domain. The vectorized representation of
input-output relation in the DD domain can be obtained as
ynr =
Nt∑
nt=1
H(nr,nt)xnt + znr, (6)
where xnt ∈ CNM×1, ynr ∈ CNM×1, and znr ∈ CNM×1
stand for the vectorized form of transmit signal from the
ntth transmit antenna, received signal and noise at the nrth
receive antenna, respectively. H(nr,nt) ∈ CNM×NM repre-
sents DD domain effective channel, which is [7], shown at
the bottom of the page,where Hl,m(nr,nt) = ∑Kˆk=−Kg(ˆk +
K + 1,l )ej2π
ˆk(m−l)
MN Qˆk, where g(.) means the channel coef-
ﬁcient. Q denotes the N× N cyclic permutation matrix.
B stands for the additional phase rotation term, given by
B = diag
{
1,e−j 2πN,...,e −j 2π(N−1)N }.
Based on the above, the input-output relation in Equation (6)
can be re-expressed as
Y = HX + Z, (8)
H(nr,nt) =


H0,0(nr,nt) HDs−1,0(nr,nt) B ··· H1,0(nr,nt)B... ... ...
HDs−2,Ds−2(nr,nt) ... H0,Ds−2(nr,nt) HDs−2,Ds−1(nr,nt) B
HDs−1,Ds−1(nr,nt) ... ... H0,Ds−1(nr,nt)
... ... ...
0 HDs−1,M−1(nr,nt) ... ... H0,M−1(nr,nt)

, (7)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

2488 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
where Y = [ yT1,..., yTnr,..., yTNr]T , X =
[xT1,..., xTnt,..., xTNt]T and Z = [ zT1,..., zTnr,..., zTNt]T .
The channel matrix H can be written as
H=


H(1,1) ··· H(1,nt) ··· H(1,Nt)
... ... ... ...
H(nr,1) ··· H(nr,nt) ··· H(nr,Nt)
... ... ... ...
H(Nr,1) ··· H(Nr,nt) ··· H(Nr,Nt)

. (9)
B. Target Sensing in ISAC-ODDM System
For target sensing of ISAC-PS systems, it is accomplished
by estimating the positions and velocities of targets. Towards
that end, one of the most commonly adopted methods is to
analyze delays and Doppler shifts from the received signal.
As shown in Fig. 1, for the pth target, its corresponding delay
τp and Doppler shift νp are deﬁned as follows [31]
τp = rp
c = rp,t +rp,rc ,
νp = Vp
λ =
ˆVp
c fc cos
(
µp− θp +φp
2
)
cos
(θp−φp
2
)
,
(10)
where rp is the estimated distance of the target. rp,t denotes
the distance between the target and the transmitter, while rp,r
is the distance between the target and the receiver. c indicates
the light of speed. Vp and ˆVp mean the radial velocity and
absolute velocity of the target, respectively. µp represents the
angle of the target velocity in the horizontal direction. Target
sensing can be accomplished by estimating the delay and
Doppler shift to get the rp and Vp of the pth target.
Based on the above, several sensing algorithms can
be employed to sense targets’ parameters, including two-
dimensional discrete Fourier transform (2D-DFT) and MUSIC
methods [14]. Despite the outcomes achieved, those conven-
tional sensing methods suffer from some challenges, including
low sensing precision and high computational complexity.
To address these problems, DL has emerged as a promising
solution for target sensing. Nevertheless, existing DL methods
always prioritize sensing while overlooking signal detection
considerations, restricting its applicability in practical scenar-
ios. Moreover, environmental adaptability is another concern
of DL-based methods, requiring further research attention.
Additionally, conventional DL-based sensing methods have
shown limitations in handling complex-valued wireless sig-
nals, thus restricting sensing precision. Consequently, it is
essential to propose a novel DL approach to address the
challenges of existing DL-based sensing methods.
C. Signal Detection in ISAC-ODDM System
From the communication perspective, the ISAC receiver
detects the transmitted content by processing the received
data. Given the input-output relation in the DD domain in
Equation (8), along with the perfectly known channel matrix
H, the transmitted ODDM signals can be modulated by
applying typical detection methods in communication systems,
such as maximum likelihood and minimum mean squared
error.
Despite the progress, the performance of these methods is
signiﬁcantly dependent on acquiring perfect channel knowl-
edge or accurate estimations. However, achieving ideal channel
information in practical applications is usually costly and
challenging, leading to a considerable detection performance
drop. DL has been utilized to tackle this challenge by alleviat-
ing the necessity for channel knowledge. Although DL-based
methods have shown some promise, they still encounter crucial
limitations that hinder their application capabilities. First,
traditional DL-based methods primarily focus on the detection
aspect alone and neglect the concurrent sensing and communi-
cation requirements, limiting their potential and adaptability in
ISAC-PS systems. Second, conventional DL-based detection
is susceptible to changes in wireless environments caused
by user mobility or temporal ﬂuctuations. Their performance
will deteriorate signiﬁcantly when directly applying them
to unseen ISAC-PS scenarios. Third, most DL architectures
typically process complex-valued numbers separately and
independently, which inevitably loses inherent connections
between the real and imaginary components, thereby restrict-
ing the detection performance in ISAC-PS systems. Therefore,
DL-based detection in ISAC-PS is still challenging and
requires further research efforts.
III. T HE PROPOSED MTL-CNET FOR ISAC-PS S YSTEMS
This section develops a novel scheme to achieve accurate
sensing, reliable detection and environmental-robust perfor-
mance in ISAC-PS systems. To accomplish that, we creatively
propose an innovative three-dimensional complex CNN archi-
tecture (3D-CCNN) for comprehensive and effective feature
extraction. Then, we propose a novel MTL-IE scheme to
achieve sensing and signal detection simultaneously, by lever-
aging the principle of multi-task learning and information
exchange design. Next, we employ transfer learning to design
an updating scheme, referred to as ASS, aimed at minimizing
updating effort and frequency and enhancing robustness to
environmental variations.
A. Framework of MTL-CNET
The framework of the developed MTL-CNET is provided
in Fig. 2, consisting of two main phases: ofﬂine training, and
online detection and sensing. The ﬁrst phase aims to pre-train
the MTL-CNET model in an ofﬂine manner, by leveraging the
properties of 3D-CCNN and MTL-IE. In the next phase, the
well-trained model is deployed to sense the targets and detect
the transmitted ODDM signals simultaneously. Meanwhile,
our MTL-CNET updates itself automatically and adaptively
to maintain effectiveness in both sensing and communication
functions across various wireless environments.
To train MTL-CNET, a training dataset is generated with
I training pairs, denoted as {Yi;Xi,Ri,Vi}Ii=1, where Yi∈
CN×M×Nr andXi∈ CN×M×Nt refer to the 3-dimensional
received and transmitted signal in the delay-Doppler-spatial
(DDS) domain, respectively. Ri,Vi stand for the target dis-
tance and speed, respectively. For simplicity, in the rest
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

CHENG et al.: MTL-CNET: AN ADV ANCED INTEGRATED SENSING AND COMMUNICATION FRAMEWORK 2489
Fig. 2. Framework of MTL-CNET.
text, we omit the subscription and use Y,X,R,V to denote
Yi,Xi,Ri,Vi, respectively.
B. 3D-CCNN for Feature Extraction
From the above discussions, traditional DL-based models
typically decompose complex-valued signals into their real and
imaginary components, treating each as separate real numbers.
This separation overlooks the intrinsic connections between
phase and amplitude information, potentially losing features
essential for both sensing and communication tasks [35].
A further limitation of conventional DL models lies in their
inadequate utilization of spatial information that is essential
for task accomplishment in ISAC systems. While these DL
methods capture correlation features between the delay and
Doppler domains, they do not fully extract features from
the spatial domain. To overcome the above challenges, in
this work, we creatively develop a complex neural network,
i.e., 3D-CCNN, to effectively preserve inherent characteristics
between real and imaginary components. Additionally, the
connection between multiple domains, i.e., delay, Doppler and
spatial domains, can be effectively explored. Thus, holistic
properties of signals can be extracted, enhancing the accuracy
and stability of both target sensing and signal detection.
Speciﬁcally, the proposed 3D-CCNN utilizes 3 convolu-
tional kernels to preserve multiple domain information of the
input signals, i.e., delay, Doppler and spatial domains. In
particular, the spatial dimension is integrated as an additional
convolutional kernels, designed to process spatial charac-
teristics of input signals. This enables the extraction of
multi-domain features, with particular preservation of spatial
information in MIMO systems. Moreover, the feature extrac-
tion is performed directly on complex-valued data, rather than
decomposition into separate real components, ensuring the
preservation of phase information in input signals. From Fig. 2,
the feature extraction is executed by several stacked 3D-CCNN
units, and each unit consists of three layers: a complex-valued
convolutional layer, a complex-valued activation layer, and a
complex-valued pooling layer.
1) Complex-V alued Convolutional Layer: The complex-
valued convolutional layer is designed to extract multi-domain
features and explore inherent inter-domain relationships
among the delay, Doppler, and spatial domains. The input
of the complex-valued convolutional layer, referred to as the
feature map, is the output of the preceding 3D-CCNN unit.
Kernels or ﬁlter banks process it for convolution operations
on the feature map by convoluting the units with the weight
matrices within the complex domain. In particular, for the kth
3D-CCNN unit, let ωk ∈ CNk×Mk×Nkr×Qk denote kernel.
Nk, Mk and Nkr stand for the kernel sizes in Doppler, delay
and spatial dimensions, respectively. Qk refers to the number
of kernels, and bk ∈ C is the bias. Then, the feature map
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

2490 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fk∈ C can be obtain by
Fk = R(ωk)∗ R(Fk−1)− I(ωk)∗ I(Fk−1)
+ i·
(
R(ωk)∗ I(Fk−1) + I(ωk)∗ R(Fk−1))
+ R(bk) + i·(I(bk)), (11)
where R(.) and I(.) represent the real and imaginary compo-
nents of a complex-valued number, respectively.∗ denotes the
convolutional operation, and i =√−1 means the imaginary
unit. Notably, Fk−1 is equal to Y with k = 1 . Following
the above steps, the deeper-level features of input signals can
be extracted, which will be passed to the complex-valued
activation layer for further processing.
2) Complex-V alued Activation Layer: It is important to note
that the outcome of the preceding layer is the linear feature
representation of input signals. For more comprehensive signal
features, a nonlinear activation function is employed to capture
the nonlinear characteristics inherent within the data. In partic-
ular, the complex rectiﬁed linear unit (CReLu) is applied here
to process the feature signals in the complex domain. It uses
separate rectiﬁed linear units for both the real and imaginary
components of complex-valued signals, which is
CReLU(Fk) = ReLU(R(Fk)) + i· ReLU(I(Fk)). (12)
3) Complex-V alued Pooling Layer: To reduce processing
complexity, the pooling layer is employed to decrease the
dimensionality of the data from the preceding layer across
width, height, and depth dimensions. Extending mean-pooling
for the complex-valued data is rooted in mathematical prin-
ciples and is straightforward to implement [36]. Speciﬁcally,
the complex mean-pooling operation can be expressed as:
PL(CReLU(Fk)) = PL(R(CReLU(Fk)))
+ i· PL(I(CReLU(Fk))), (13)
where PL(.) stands for the pooling operation. It is noteworthy
that although the pooling layer can reduce the dimensionality
of data, large pooling sizes or excessive pooling layers may
compromise the quality of feature extraction. Given that, only
one pooling layer with a kernel size of 2× 2× 1 is employed
in this work. Based on empirical experience, this selection
can prevent premature merging of the spatial dimension and
maintain compatibility with its length.
C. MTL-IE for Concurrent Sensing and Communication
In this section, we develop MTL-IE to accomplish sens-
ing and communication tasks simultaneously with a singular
framework, drawing support from the property of MTL and
information exchange design. Conventional DL methods use
two individual DL networks to process these two tasks
separately. Despite the achievement, this operation requires
additional resources and increases processing overhead due to
the deployment of two separate DL networks. To address this
concern, we propose MTL-IE to concurrently achieve target
sensing and signal detection using a uniﬁed DL architecture.
As illustrated in Fig. 2, the proposed MTL-IE is composed
of two sub-networks: shared-feature sub-network (SFS) and
task-speciﬁc sub-network (TSS). The layers in SFS are shared
between sensing and communication functions with identical
weights and parameters, aiming to learn common knowledge
from input signals. Subsequently, three independent and paral-
lel networks are designed in TSS, which are tailored to sense
targets and detect transmitted signals, respectively.
The architecture of SFS consists of four consecutive
3D-CCNN units, aiming to extract generalized features shared
by both sensing and communication tasks. Additionally, our
SFS applies a residual branch to address the vanishing gradient
problem. Speciﬁcally, we design a shortcut path in SFS to
directly connect the output of the second 3D-CCNN unit to the
output of the fourth 3D-CCNN unit, as illustrated in Fig. 2. By
doing so, the feature maps generated by the fourth 3D-CCNN
unit of SFS incorporate input from the second, allowing for
a deeper understanding of the input signal features. It also
enables the network to learn intricate connections within the
inter-layer data, leading to improved generalized performance
across both sensing and communication tasks. Let S denote
the output of SFS, which is
S =Gs(ˆY;WS), (14)
whereGS(.) represents the non-linear function of SFS, and
WS is the weights of the SFS.
Next, the output of SFS is fed into TSS for target sensing
and signal detection. The key objective of TSS is to explore
and utilize the inter-task relationship to effectively achieve
multiple tasks. To achieve that, we creatively utilize the tensor
normal distribution to explore inter-task connections, given the
inherent tensor nature of DL parameters [37]. The distribu-
tion serves as the prior information for network parameters
across task-speciﬁc layers to capture ﬁne-grained and effective
relationships across various tasks. According to Fig. 2, TSS
comprises three parallel branches, and each branch is stacked
by three 3D-CCNN units followed by a fully connected
layer. Additionally, a novel information exchange (IE) module
is designed to enable mutual enhancement between sensing
and communication tasks through dynamic feature fusion. It
selectively exchanges and reﬁnes extracted features from both
branches based on task relevance, improving overall system
performance. To achieve this, the IE module operates through
an adaptive learning mechanism that prioritizes task-relevant
feature sharing, ensuring that sensing features contribute to
improved communication reliability, and vice versa. Instead of
a static feature-sharing approach, the IE module dynamically
assigns importance weights to extracted features through an
attention-based mechanism, ﬁltering out irrelevant information
and enhancing task-speciﬁc learning. Moreover, the residual
branch within the IE module plays a vital role in preserving
task-speciﬁc integrity while facilitating cross-domain feature
reﬁnement. By integrating residual connections, IE module
ensures communication tasks beneﬁt from sensing features,
improving BER performance, while sensing tasks leverage
communication features for higher localization accuracy.
Speciﬁcally, let Wt,𝓁∈ CD𝓁1×D𝓁2 denote the TSS parameters
of the t-th task in the 𝓁-th 3D-CCNN units, with t =
[1, 2,..., T ] and𝓁 = [1, 2,..., L]. In this work, three tasks are
simultaneously addressed using three 3D-CCNN units for each
task branch, so T = 3, andL = 3. D𝓁1 and D𝓁2 are the rows
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

CHENG et al.: MTL-CNET: AN ADV ANCED INTEGRATED SENSING AND COMMUNICATION FRAMEWORK 2491
and columns of matrix Wt,𝓁. To learn the task relationship
across allT tasks, we construct W𝓁 =[W1,𝓁;... ; WT,𝓁]∈
CD𝓁1×D𝓁2×T . Accordingly, the TSS parameters forT tasks and
L task-speciﬁc 3D-CCNN units isW =
{
W𝓁 :𝓁∈L}. Given
the training dataset {Y;X,R,V} as stated in Section III-A,
the TSS parameters W can be achieved by
P (W|{Y ;X,R,V})∝ P (W)· P ({X,R,V}|Y ,W ), (15)
where P(.) stands for the probability density function. With a
prior P (W), theW𝓁 is assumed to be independent to W𝓁′⁄=𝓁,
which aligns the common assumption in most feed-forward
neural networks [37]. According to Equation (15), P (W) plays
a vital role in learning inter-task relationships across parameter
tensors. The prior at the 𝓁-th task-speciﬁc 3D-CCNN units is
deﬁned based on tensor normal distribution [37], by
P
(
W𝓁) = TND(Σ𝓁1, Σ𝓁2), (16)
where Σ𝓁1 ∈ CD𝓁1×D𝓁1 and Σ𝓁2 ∈ CT×T denote the mode-
1 and mode-2 covariance matrices, respectively [37]. Based
on equation (15) and (16), W can be learned and obtained
through the training process, enabling mutual improvement
among multiple tasks. Note that, the above steps of TSS can
be regarded as an embedded process [38], expressed as
{ˆY, ˆD, ˆV} =GT (S;W), (17)
whereGT is the embedded function, and S is the output of
SFS. ˆD∈ CLp−1, ˆV∈ RLp−1 and ˆY∈ CN×M×Nr denote the
estimated range, velocity and transmitted signal, respectively,
which are the ﬁnal outputs of TSS.
Note that, while MTL has been studied, our system proposes
a novel inter-layer IE mechanism that distinguishes it from
conventional MTL designs. Traditional MTL typically relies
on shared low-level features with limited interaction between
task branches. In contrast, our approach enables hierarchical
feature exchange across multiple layers between the sensing
and communication pathways. This design supports mutual
enhancement of task-speciﬁc features, which is particularly
important for ISAC systems where the two tasks are inherently
coupled but have distinct objectives and signal features.
IV. ASS FOR ROBUSTNESS IMPROVEMENT
A. Design of Loss Function
The primary objective of the loss function is to effectively
train the proposed MTL-CNET to extract effective features
for simultaneous target sensing and signal detection. It is
composed of three major components: range loss function,
velocity loss function and detection loss function. The range
loss function and velocity loss function enable comprehensive
feature extraction for sensing purposes by capturing signal
characteristics from multiple domains and complex-valued
data. Similarly, the detection loss function ensures the signal
features extracted are essential for signal detection. The overall
training objective is to minimize the combined loss of func-
tions by integrating the three loss functions, thereby allowing
them to mutually enhance and achieve an optimal outcome.
Given the above, the overall multi-task loss is designed as
Lml =αrLr +αvLv +αdLd, (18)
whereLr,Lv andLd stand for the range loss, velocity loss and
detection loss, respectively.αr,αv andαd are the correspond-
ing learnable weights to balance the impact of various tasks to
enhance overall performance and generalization capabilities.
This study adopts the L1 loss function [39] to deﬁne the
range loss, velocity loss and detection loss, given by
Lr =
Lp−1∑
p=1
‖ˆD(p)− D(p)‖1,Lv =
Lp−1∑
p=1
‖ˆV(p)− V(p)‖1,
Ld =
N∑
k=1
M∑
l=1
Nr∑
nr=1
‖ˆY(k,l,n r)− X(k,l,n r)‖1, (19)
where ˆD(p) and ˆV(p) represent the estimated range (distance)
and velocity of pth target, respectively. D(p) and V(p) are the
actual range and velocity information, respectively. ˆY(k,l,n r)
and X(k,l,n r) denote the (k,l,n r)th information cube of the
detected signal ˆY and the transmitted signal X, respectively.
During the training process of MTL-CNET, the primary goal
is to minimize the loss function Lml in Equation (18).
B. Design of ASS
It is worth noting that wireless channels often undergo
variations due to user mobility and the dynamic nature of
wireless environments. Thus, DL models trained on past
wireless environments may lose efﬁcacy when applied directly
to a new environment. To ensure reliable performance, one
option is to retrain the entire model for the new environment,
but this process is resource-intensive and time-consuming.
To overcome these problems, we develop ASS to enable
the pre-trained DL model to suit new environments, thereby
improving the capabilities of MTL-CNET in resource uti-
lization, adaptability environmental robustness. To achieve
that, the proposed ASS leverages transfer learning techniques
[40] in a novel and efﬁcient manner. Different from con-
ventional transfer learning methods, which typically require
extensive retraining of the entire model for new domains, our
ASS introduces a lightweight adaptation framework specif-
ically tailored for ISAC scenarios. By utilizing a shared
feature-distribution similarity assessment, ASS determines the
necessity and extent of model updates based on environmental
variations. Consequently, only a single frame of pilot ODDM
signals from the new environment, together with pre-extracted
features from historical environments, is sufﬁcient to ﬁne-tune
selected layers of the MTL-CNET. This selective updating
signiﬁcantly reduces computational complexity and parame-
ter requirements, enabling rapid and efﬁcient adaptation to
new wireless conditions. Thus, the proposed ASS extends
traditional transfer learning methodologies, providing an efﬁ-
cient and environment-aware adaptation solution that achieves
robust sensing and communication performance with minimal
resource overhead.
To achieve the above goal, we ﬁrst freeze all layers of
MTL-CNET except for the last two layers. Then, we modify
the parameters and settings of these two layers to adapt
MTL-CNET to the new environment. Let us deﬁne WO
and WT as the frozen parameters and updated parameters
of MTL-CNET, respectively. Suppose that ˜Yi∈ CN×M×Nr
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

2492 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
is the training data collected from the new environment,
˜Di∈ RLp−1, ˜Vi∈ RLp−1 and ˜Xi∈ CN×M×Nt stands for
the corresponding labels of distance, velocity and transmitted
signals,i = 1, 2,...,I U , whereIU denotes the number of new
training samples. The loss function for ASS is expressed as
˜L =Lml
(
{˜Yi, ˜Di, ˜Vi ˜Xi}IUi=1,WO;WT
)
. (20)
The update process is aimed at minimizing the loss function
for the dataset obtained from the new environment, written as
WT = arg minWT ˜L(WT ). (21)
Following the above steps,WT can be achieved, and the MTL-
CNET will be updated accordingly.
Although ASS strengthens the resilience of MTL-CNET
to variations in wireless environments, its frequent use may
lead to increased processing overhead. Thus, determining the
timing for ASS activation is crucial. According to the domain
transfer theory [41], if the feature space of the testing dataset
closely aligns with that of the training dataset, the trained DL
model can be applied with reliable performance. Otherwise,
the trained DL model for testing would result in a substantial
performance drop. Inspired by this, we propose a similarity-
based method to determine the activation timing of ASS.
A straightforward method to measure similarity is compar-
ing the feature space of new samples with those of all samples
from the training dataset [17]. However, this approach is
computationally intensive, as computing the similarity for each
new sample against every past training sample requires sub-
stantial resources and time. Given the potentially large training
dataset size, this method is impractical for real-time scenar-
ios. To address this challenge, we propose a shared feature
distribution-based similarity calculation approach. Speciﬁcally,
the features extracted from the SFS will be utilized for
calculating the similarity score, which is
Γ(˜Yi) = P(Gs({Yj}Jj=1;WS))·P (Gs(˜Yi;WS)‖P (Gs({Yj}Jj=1;WS))‖‖P (Gs(˜Yi;WS)‖,
(22)
where ˜Yi stands for the ith sample gathered from the new envi-
ronment.P(.) is the distribution function using the histogram
method. It is noteworthy that P(Gs(˜Yi;WS) only needs to be
calculated once ofﬂine, as it will not be required during online
sensing, detection or updating stages. Thus, this operation
does not need resources from the online stages. The activation
mechanism for ASS can be deﬁned as
Ω =
{
1, if Γ(˜Yi)< Υ,
0, if Γ(˜Yi)≥ Υ, (23)
where Ω is the activation indicator, Ω = 1 means that ASS
requires activation, and MTL-CNET should be updated before
applying to new environments. Conversely,Ω = 0 denotes that
the previously trained model does not necessitate updating
and can be directly deployed in new environments. Υ is
the threshold for ASS activation, and its inﬂuence will be
demonstrated in Fig. 17 later. By integrating the adaptive ASS
scheme, our MTL-CNET, incorporating 3D-CCNN and inter-
layer information exchange, enables effective learning from
TABLE I
SETUP PARAMETERS FOR ODDM S YSTEM
complex-valued signals and facilitates joint optimization of
sensing and communication. This joint design differs funda-
mentally from conventional CNNs and directly contributes
to the improvements in both robustness and accuracy, as
demonstrated in Section V.
V. S IMULATION RESULTS
A. Experimental Set-Up
To evaluate the system performance, we ﬁrst establish the
MIMO-enabled ISAC-PS system using a practical channel
model, speciﬁcally the 3rd Generation Partnership Project
(3GPP) tapped delay line-C model [42]. A uniform linear array
is employed for the MIMO system, where the antenna spacings
dr and dt are set to half the wavelength. Unless otherwise
speciﬁed, all experiments are conducted using the parameters
listed in Table I. To simulate mobility dynamics, we introduce
motion-related parameters: without loss of generality, the
maximum speed of each vehicle is set to 20 m/s, and the initial
positions of vehicles are randomly assigned. The Doppler
index is randomly selected from the interval [−kνmax,kνmax],
wherekνmax represents the maximum Doppler index, which is
determined by the user’s velocity. The delay index is randomly
chosen from the range [0,lτmax], with the maximum delay
index set to lτmax = 10 . The received signal-to-noise ratio
(SNR) is varied between 0 dB and 10 dB to evaluate system
performance under different noise conditions.
The proposed MTL-CNET is trained on a high-performance
computing system equipped with an Nvidia GeForce RTX
3080 GPU and a 3.6 GHz processor. The learning rate, batch
size, and training iterations are set to 0.001, 128, and 1000,
respectively. The labeled dataset consists of 106 samples,
corresponding to approximately 7812 ODDM symbols. The
performance evaluation follows a cross-validation approach
[43], where the dataset is split into 60% for training and 40%
for testing, and the process is repeated over 10 independent
runs to obtain averaged results.
B. Performance Evaluation
This section will ﬁrst thoroughly evaluate the proposed
MTL-CNET and up-to-date related methods for both sensing
and communication performance in ISAC-PS systems. Then,
we will examine the impact of key components in the proposed
MTL-CNET on system performance. The bit-error-rate (BER)
is adopted for performance validation of the communication
function, as it directly reﬂects the accuracy of signal detection
and ensures reliable data transmission. For the sensing func-
tion, the normalized mean squared errors (NMSEs) of range
and velocity are considered as performance metrics, as they
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

CHENG et al.: MTL-CNET: AN ADV ANCED INTEGRATED SENSING AND COMMUNICATION FRAMEWORK 2493
TABLE II
COMPARISON OF SCOPES FOR DIFFERENT METHODS
measure the precision of target localization and motion estima-
tion, which are critical for ISAC-PS applications. Additionally,
to further assess the statistical performance, we provide a
cumulative distribution function (CDF) analysis of estimation
errors. A similar conclusion holds for signal detection and is
omitted here to avoid redundancy.
Table II compares the research scopes of different methods,
providing a comprehensive performance evaluation. As illus-
trated, most of the existing works focus on either sensing ([28],
[29]) or communication [25], [27]), with only ISAC-NET
([31]) and our proposed MTL-CNET addressing both simulta-
neously. Speciﬁcally, 2D-CNN ([25]) serves as a classical deep
learning-based detection method, making it a relevant base-
line for evaluating the effectiveness of ISAC-speciﬁc feature
integration. SG-ODDM ([27]) represents a communication
framework tailored for high-mobility scenarios, establishing
a benchmark for communication capability in ISAC systems.
DCNN ([28]) is a deep learning model designed for target
sensing but does not include communication functionalities,
making it useful for highlighting the advantages of multi-task
learning in ISAC. 3D-CNN ([29]) extends CNN-based archi-
tectures by incorporating spatial-temporal feature extraction
for sensing, allowing us to analyze the impact of temporal
features on sensing results. ISAC-NET ([31]), as the closest
ISAC-based deep learning approach, integrates both sensing
and communication, making it a key baseline for perfor-
mance comparison. However, it struggled with reliable data
transmission while ensuring precise sensing. Moreover, it has
limited adaptability to dynamic environments. By contrast, our
proposed MTL-CNET creatively leverages multi-task learning,
information exchange strategy, and complex-valued feature
extraction for reliable and simultaneous sensing and com-
munication. Additionally, our MTL-CNET proposes ASS, a
novel adaptive updating mechanism, to enhance adaptability,
generalization, and environmental robustness. Therefore, our
MTL-CNET surpasses all the relevant works in sensing pre-
cision, detection reliability, and environmental robustness.
1) Overall Performance Comparison: Fig. 3 demonstrates
the BER performance of different methods across different
SNR conditions. From this ﬁgure, we can observe that the
proposed MTL-CNET outperforms all evaluated detection
methods under various SNR conditions. This is thanks to our
designed 3D-CCNN that can effectively capture the intrinsic
connections between real and imaginary parts of complex-
valued signals. Moreover, the proposed MTL-IE is able to
extract and utilize shared generalized features between sensing
and communication tasks to enhance the performance of each
task. Fig. 4 and Fig. 5 illustrate the NMSEs of range and
Fig. 3. BER performance comparison of different methods.
Fig. 4. NMSE of range of different methods.
Fig. 5. NMSE of velocity of different methods.
Fig. 6. The CDF of estimated errors for range.
velocity for different methods. As can be observed, higher
SNR conditions correspond to improved NMSE performance
in both range and velocity sensing tasks. Second, the proposed
MTL-CNET is superior to all the other methods in both range
and velocity NMSEs, across all SNR settings.
Furthermore, Fig. 6 and Fig. 7 demonstrate the CDF of
range and velocity estimation errors, respectively, highlight-
ing the advantages of MTL-CNET over existing methods.
A similar CDF conclusion holds for communication and thus is
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

2494 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE III
COMPLEXITY COMPARISON FOR DIFFERENT DETECTION METHODS
Fig. 7. The CDF of estimated errors for velocity.
omitted here to avoid redundancy. These ﬁgures reveal two key
ﬁndings. First, our MTL-CNET consistently outperforms other
methods in both range and velocity estimation, demonstrating
its superior accuracy and reliability. Speciﬁcally, the median
errors for range and velocity using the proposed MTL-CNET
are only about 0.1m and 0.062m/s, respectively, whereas
DCNN exhibits signiﬁcantly larger errors of 0.89m and
0.53m/s. This is attributed to the designed 3D-CCNN, which
effectively captures crucial phase and amplitude information
within complex-valued signals, enabling more precise sensing.
Additionally, our MTL-CNET incorporates MTL-IE, which
exploits the interdependence between sensing and communi-
cation tasks, resulting in mutual performance enhancement.
In contrast, the other relevant works either lack explicit task
information exchange or fail to effectively utilize complex-
valued signals for task accomplishment, leading to degraded
sensing performance. These results further validate that the
proposed MTL-CNET not only enhances individual sensing
performance but also optimally balances ISAC-PS system
efﬁciency, making it a more effective solution than existing
deep learning-based approaches.
Then, we examine the communication and sensing perfor-
mance of various methods across different target numbers,
as illustrated in Fig. 8 to Fig. 10. The SNR conditions in
these ﬁgures are set as 8dB. Several important insights can
be found in these ﬁgures. Firstly, all methods suffer from
a degradation in BER and NMSE performance with more
targets, due to more severe multi-path effects and interference
caused. Secondly, our MTL-CNET shows a stronger robust-
ness to the impact of target numbers, compared to other related
methods. This is credited to our elaborated MTL-CNET that
can efﬁciently process complex-valued ODDM signals, extract
spatial information provided by MIMO systems and utilize the
relationship between sensing and communication functions.
Therefore, our MTL-CNET is able to achieve successful and
Fig. 8. BER performance versus the number of targets with SNR = 8dB.
Fig. 9. Range performance versus the number of targets with SNR = 8dB.
Fig. 10. Velocity performance versus the number of targets with SNR = 8dB.
concurrent communication and sensing performance in the
presence of multiple targets.
We further evaluate the computational complexity of differ-
ent methods, as shown in Table III. This table considers both
the neural network operations and the corresponding inference
time. The inference time refers to the duration required for
the DL network to process an input signal and generate an
output prediction. NT andNR are the number of transmit and
receive antennas, respectively. For 2D-CNN [25] and DCNN
[28],WlfHlf represents the ﬁlter size at the lth layer, whileNlf
indicates the number of ﬁlters. Clin and Clout are the number
of input and output channels at each layer. For 3D-CNN [29],
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

CHENG et al.: MTL-CNET: AN ADV ANCED INTEGRATED SENSING AND COMMUNICATION FRAMEWORK 2495
Fig. 11. Impact of 3D-CCNN on BER performance with SNR = 8dB.
Fig. 12. Impact of 3D-CCNN on range performance with SNR = 8dB.
Lp deﬁnes the processing depth, and D denotes the additional
complexity introduced by 3D feature extraction. Our MTL-
CNET integrates a complex convolutional structure, where Q
represents the number of complex-valued ﬁlters. LS and LT
are shared and task-speciﬁc layers, respectively.
As can be observed, although MTL-CNET does not have
the lowest computational complexity, it achieves an inference
time of 12.31ms, meeting the 20ms real-time requirement
[44]. Additionally, as shown in Fig. 3–Fig. 10, the designed
MTL-CNET ensures superior performance in both sensing
and communication functions, making it suitable for real-time
applications. Note that, while 2D-CNN and SG-ODDM have
lower complexity and inference times (4)-5ms), they are lim-
ited to communication function, lacking the ability to perform
both sensing and communication concurrently. DCNN and
3D-CNN have inference times of 8.1ms and 11.3ms, respec-
tively, however, they are designed solely for sensing and
do not consider communication functionality. ISAC-NET
demonstrates a comparable inference time to our MTL-
CENT, i.e., 13.82ms, but it is less effective in ensuring
reliable data transmission, precise sensing, and environmen-
tal robustness, as veriﬁed in Fig. 3–Fig. 10. Therefore, our
proposed MTL-CNET is a strong candidate for practical
ISAC-PS applications, offering a balanced trade-off between
reliability, adaptability, computational efﬁciency, and real-time
processing.
2) Performance Evaluation of MTL-CNET: In Fig. 11 to
Fig. 13, we evaluate the impact of our proposed 3D-CCNN
in MTL-CNET on sensing and communication performance,
respectively, with SNR=8dB. The term “MTL-CNET with
3D-CCNN” denotes the case of utilizing 3D-CCNN for fea-
ture extraction. Conversely, the term “MTL-CNET without
3D-CCNN” means the utilization of traditional CNNs to
Fig. 13. Impact of 3D-CCNN on velocity performance with SNR = 8dB.
handle sensing and communication tasks. Like conventional
DL models, this method treats the complex-valued ODDM
signals as two independent real numbers. As illustrated in
the ﬁgures, “MTL-CNET with 3D-CCNN” signiﬁcantly out-
performs “MTL-CNET without 3D-CCNN” for both sensing
and communication functions, achieving 30−− 50% BER
improvement and 20−− 40% NMSE reduction. This is
because incorporating 3D-CCNN enables our MTL-CNET to
explore and utilize the inherent relationship between ampli-
tude and phase information in complex-valued data. As a
result, more comprehensive and effective features can be
extracted for both sensing and communications, resulting
in enhanced BER and NMSE performance. Regarding the
computational complexity, “MTL-CNET with 3D-CCNN”
and “MTL-CNET without 3D-CCNN” have complexities
of O
(
4((2LS + 6LT )QNMNr + TLT (NMNr)2)) and
O
(
2((2LS +6LT )QNMNr+TLT (NMNr)2)), respectively.
Although “MTL-CNET with 3D-CCNN” has higher com-
plexity than “MTL-CNET without 3D-CCNN”, the inference
time increases marginally by only 2−− 3 ms. This minimal
increase is attributed to the modern parallel hardware (e.g.,
GPUs/TPUs), which optimizes complex CNN operations,
reducing the actual runtime difference. Therefore, “MTL-
CNET with 3D-CCNN” is an effective solution for ISAC-PS
systems, offering a balanced trade-off between accuracy and
efﬁciency.
Additionally, we observe that as the number of anten-
nas increases, the performance of both methods improves
due to the richer spatial information provided by larger
antenna arrays, which enhances both sensing accuracy and
communication reliability. However, the performance gain of
“MTL-CNET with 3D-CCNN” is more signiﬁcant than “MTL-
CNET without 3D-CCNN”. The key reason is that 3D-CCNN
can better exploit the spatial correlations in the received
signal, effectively capturing and utilizing the additional spatial
diversity offered by larger antenna arrays. This advantage is
particularly notable in dynamic and multipath-rich environ-
ments, where 3D-CCNN’s complex-valued feature extraction
enables a more precise representation of signal characteristics,
leading to superior robustness and adaptability.
Then, we discuss the effectiveness of the proposed MTL-
based scheme on both BER and NMSE performance, as
depicted in Fig. 14–Fig. 16. “MTL-CNET with IE” refers
to the case of leveraging MTL and IE for signal processing
and feature extraction. “MTL-CNET without IE” implies that
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

2496 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 14. Impact of IE on BER performance.
Fig. 15. Impact of IE on range estimation performance.
Fig. 16. Impact of IE on velocity estimation performance.
MTL-CNET uses MTL solely to achieve sensing and commu-
nication tasks simultaneously. In contrast, “Individual” denotes
using two sets of individual CNN networks for sensing and
communication, respectively. Given the same dataset condi-
tion, it is clear that “MTL-CNET with IE” achieves the best
BER and NMSE results among all methods. The reason is
that it can efﬁciently capture the intrinsic connections between
two functions for sensing and signal detection in the ISAC-PS
system. Moreover, the information exchange design enables
mutual improvement between the two functions, enhancing
performance for both tasks. Conversely, “MTL-CNET without
IE” lacks the exchange of mutual information between sensing
and communication functions, leading to the inevitable loss of
crucial features for both tasks.
Next, we provide Fig. 17 to Fig. 20 to further assess the
impact of the proposed updating scheme with SNR=6dB.
Fig. 17 to Fig. 19 demonstrate the generalization capability of
the proposed “MTL-CNET with ASS” by analyzing its BER
and NMSE performance for range and velocity estimation
across different similarity scores. As shown in Fig. 17, the
BER performance of “MTL-CNET with ASS” signiﬁcantly
Fig. 17. Impact of training strategies on BER performance, with SNR = 6dB.
Fig. 18. Impact of training strategies on NMSE of range, with SNR = 6dB.
Fig. 19. Impact of training strategies on NMSE of velocity, with SNR = 6dB.
outperforms the model without ASS, particularly when the
similarity score between training and testing environments is
lower than 0.6, where “MTL-CNET without ASS exhibits
a considerable degradation in BER. Similarly, Fig. 18 and
Fig. 19 illustrate that “MTL-CNET with ASS” consistently
achieves lower NMSE values for both range and velocity
estimation compared to the model without ASS. The NMSE of
“MTL-CNET with ASS” closely matches that of “Retraining
MTL-CNET” when the similarity score exceeds 0.6, conﬁrm-
ing its ability to effectively adapt to environmental changes
without requiring full retraining. These results verify that
ASS signiﬁcantly enhances the generalization capability of
MTL-CNET across diverse sensing and communication tasks.
Fig. 20 further shows the robustness of “MTL-CNET with
ASS” by comparing its convergence rate against “Retraining
MTL-CNET”. While both methods eventually achieve similar
performance levels, “MTL-CNET with ASS converges sig-
niﬁcantly faster, requiring approximately 80 iterations under
an early stopping strategy, whereas “Retraining MTL-CNET”
takes substantially more iterations. This indicates that the
designed ASS accelerates adaptation to new environments
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

CHENG et al.: MTL-CNET: AN ADV ANCED INTEGRATED SENSING AND COMMUNICATION FRAMEWORK 2497
Fig. 20. Impact of training strategies on convergence rate.
Fig. 21. BER performance of applying the proposed MTL-CNET for different
waveforms.
while maintaining stability. Additionally, the improved conver-
gence speed offered by ASS reduces the computational cost
of retraining, making “MTL-CNET with ASS” well-suited for
dynamic and real-time applications.
We further assess the performance of MTL-CNET in OFDM
systems, as shown in Fig. 21. While the framework can be
applied in this OFDM setting, its performance declines com-
pared to results in ODDM systems. This reduction is mainly
due to the nature of OFDM, which transmits signals in the TF
domain. In high-mobility environments, Doppler shifts disrupt
subcarrier orthogonality, leading to strong ICI. In contrast,
ODDM transmits in the DD domain using orthogonal pulses,
offering greater resistance to Doppler effects. Therefore, to
ensure reliable detection in OFDM under such conditions,
further reﬁnement of the architecture is needed to better
suppress ICI.
VI. C ONCLUSION
In this study, we developed a novel MTL-CNET frame-
work for ISAC-PS systems to achieve simultaneous sens-
ing and communication tasks with strong environmental
robustness. We proposed a 3D-CCNN approach to process
complex-valued wireless signals in a singular architecture,
extracting comprehensive features for ISAC tasks. Moreover,
we designed an MTL-IE scheme to concurrently facilitate
sensing and communication tasks while enhancing mutual
performance, by leveraging MTL and inter-layer information
exchange module. To enhance environmental robustness, we
proposed the ASS scheme to enable MTL-CNET to adapt
to various wireless environments with minimized updating
frequency and effort. The experimental results veriﬁed the
superior performance of our MTL-CNET over other related
works in terms of sensing precision, detection reliability and
environmental robustness. As a forward step, our future work
will focus on extending the proposed framework to more
complex ISAC scenarios and real-world hardware impair-
ments, while also exploring lightweight models to enhance
computational efﬁciency for real-time ISAC applications.
REFERENCES
[1] A. Liu et al., “A survey on fundamental limits of integrated sensing
and communication,” IEEE Commun. Surveys Tuts. , vol. 24, no. 2,
pp. 994–1034, 2nd Quart., 2022.
[2] F. Liu, C. Masouros, A. P. Petropulu, H. Grifﬁths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun., vol. 68, no. 6, pp. 3834–3862, Jun.
2020.
[3] H. Lin and J. Yuan, “Orthogonal delay-Doppler division multiplex-
ing modulation,” IEEE Trans. Wireless Commun. , vol. 21, no. 12,
pp. 11024–11037, Dec. 2022.
[4] K. Zheng, Q. Zheng, H. Yang, L. Zhao, L. Hou, and P. Chatzimisios,
“Reliable and efﬁcient autonomous driving: The need for heterogeneous
vehicular networks,” IEEE Commun. Mag. , vol. 53, no. 12, pp. 72–79,
Dec. 2015.
[5] X. Chen, Z. Feng, J. A. Zhang, X. Yuan, and P. Zhang, “Kalman ﬁlter-
based sensing in communication systems with clock asynchronism,”
IEEE Trans. Commun. , vol. 72, no. 1, pp. 403–417, Jan. 2024.
[6] S. Xu, Y . Du, J. Zhang, J. Liu, J. Wang, and J. Zhang,
“Intelligent reﬂecting surface enabled integrated sensing, communication
and computation,” IEEE Trans. Wireless Commun. , vol. 23, no. 3,
pp. 2212–2225, Mar. 2024.
[7] X. Zhang, H. Zhang, L. Liu, Z. Han, H. V . Poor, and B. Di, “Target
detection and positioning aided by reconﬁgurable surfaces: Reﬂective
or holographic?,” IEEE Trans. Wireless Commun. , vol. 23, no. 12,
pp. 19215–19230, Dec. 2024.
[8] N. T. Nguyen, L. V . Nguyen, N. Shlezinger, Y . C. Eldar, A. L. Swindle-
hurst, and M. Juntti, “Joint communications and sensing hybrid
beamforming design via deep unfolding,” IEEE J. Sel. Topics Signal
Process., vol. 18, no. 5, pp. 901–916, Jul. 2024.
[9] F. Liu, L. Zhou, C. Masouros, A. Li, W. Luo, and A. Petrop-
ulu, “Toward dual-functional radar-communication systems: Optimal
waveform design,” IEEE Trans. Signal Process. , vol. 66, no. 16,
pp. 4264–4279, Aug. 2018.
[10] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. Eldar, “Joint
transmit beamforming for multiuser MIMO communications and MIMO
radar,” IEEE Trans. Signal Process. , vol. 68, pp. 3929–3944, 2020.
[11] H. Zhang et al., “Holographic integrated sensing and communication,”
IEEE J. Sel. Areas Commun. , vol. 40, no. 7, pp. 2114–2130, Jul. 2022.
[12] Z. Wan, Z. Gao, F. Gao, M. D. Renzo, and M.-S. Alouini, “Terahertz
massive MIMO with holographic reconﬁgurable intelligent surfaces,”
IEEE Trans. Commun. , vol. 69, no. 7, pp. 4732–4750, Jul. 2021.
[13] C. R. Berger, B. Demissie, J. Heckenbach, P. Willett, and S. Zhou,
“Signal processing for passive radar using OFDM waveforms,” IEEE
J. Sel. Topics Signal Process. , vol. 4, no. 1, pp. 226–238, Feb. 2010.
[14] J. B. Sanson, P. M. Tom ´e, D. Castanheira, A. Gameiro, and
P. P. Monteiro, “High-resolution delay-Doppler estimation using received
communication signals for OFDM radar-communication system,” IEEE
Trans. V eh. Technol., vol. 69, no. 11, pp. 13112–13123, Nov. 2020.
[15] P. Raviteja, K. T. Phan, Y . Hong, and E. Viterbo, “Interference
cancellation and iterative detection for orthogonal time frequency
space modulation,” IEEE Trans. Wireless Commun. , vol. 17, no. 10,
pp. 6501–6515, Oct. 2018.
[16] W. Yuan, S. Li, Z. Wei, J. Yuan, and D. W. K. Ng, “Data-aided
channel estimation for OTFS systems with a superimposed pilot and
data transmission scheme,” IEEE Wireless Commun. Lett., vol. 10, no. 9,
pp. 1954–1958, Sep. 2021.
[17] Q. Cheng, Z. Shi, J. Yuan, P. G. Fitzpatrick, and T. Sakurai,
“A novel environmentally robust ODDM detection approach using con-
trastive learning,” IEEE Trans. Commun., vol. 71, no. 9, pp. 5274–5286,
Sep. 2023.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

2498 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[18] Q. Cheng, Z. Shi, J. Yuan, and H. Lin, “MIMO-ODDM signal detection:
A spatial-based generative adversarial network approach,” IEEE Trans.
Wireless Commun., vol. 23, no. 9, pp. 12499–12512, Sep. 2024.
[19] J. A. Zhang et al., “Enabling joint communication and radar sensing
in mobile networks—A survey,” IEEE Commun. Surveys Tuts. , vol. 24,
no. 1, pp. 306–345, 1st Quart., 2022.
[20] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[21] A. Zhang, Md. L. Rahman, X. Huang, Y . J. Guo, S. Chen, and
R. W. Heath, “Perceptive mobile networks: Cellular networks with radio
vision via joint communication and radar sensing,” IEEE V eh. Technol.
Mag., vol. 16, no. 2, pp. 20–30, Jun. 2021.
[22] Y . Cui, H. Ding, L. Zhao, and J. An, “Integrated sensing and communi-
cation: A network level perspective,” IEEE Wireless Commun. , vol. 31,
no. 1, pp. 103–109, Feb. 2024.
[23] Z. Ni, J. A. Zhang, K. Wu, and R. P. Liu, “Uplink sensing using CSI ratio
in perceptive mobile networks,” IEEE Trans. Signal Process. , vol. 71,
pp. 2699–2712, 2023.
[24] B. Kong, Y . Wang, X. Deng, and D. Qin, “Joint range-Doppler-angle
estimation for OFDM-based RadCom system via tensor decomposition,”
Wireless Commun. Mobile Comput., vol. 2018, no. 1, Jan. 2018, Art. no.
2708416.
[25] Y . K. Enku, B. Bai, S. Li, M. Liu, and I. N. Tiba, “Deep-learning based
signal detection for MIMO-OTFS systems,” in Proc. IEEE Int. Conf.
Commun. Workshops (ICC Workshops) , May 2022, pp. 1–5.
[26] Y . Zhang, S. Zhang, B. Wang, Y . Liu, W. Bai, and X. Shen,
“Deep learning-based signal detection for underwater acoustic OTFS
communication,” J. Mar . Sci. Eng., vol. 10, no. 12, p. 1920, Dec. 2022.
[27] Q. Cheng, Z. Shi, J. Yuan, and H. Lin, “A spatial generative adversarial
network-based signal detection for MIMO-ODDM systems,” in Proc.
IEEE Global Commun. Conf. , Dec. 2023, pp. 6536–6541.
[28] Y . Chen, L. Yan, and C. Han, “Hybrid spherical {-} and planar-
wave modeling and DCNN-powered estimation of terahertz ultra-
massive MIMO channels,” IEEE Trans. Commun. , vol. 69, no. 10,
pp. 7063–7076, Oct. 2021.
[29] C. Wu et al., “Learning to localize: A 3D CNN approach to user
positioning in massive MIMO-OFDM systems,” IEEE Trans. Wireless
Commun., vol. 20, no. 7, pp. 4556–4570, Jul. 2021.
[30] H. Huang, J. Yang, H. Huang, Y . Song, and G. Gui, “Deep learning
for super-resolution channel estimation and DOA estimation based
massive MIMO system,” IEEE Trans. V eh. Technol. , vol. 67, no. 9,
pp. 8549–8560, Sep. 2018.
[31] W. Jiang, D. Ma, Z. Wei, Z. Feng, and P. Zhang, “ISAC-NET: Model-
driven deep learning for integrated passive sensing and communication,”
2023, arXiv:2307.15074.
[32] Y . Zhang and Q. Yang, “An overview of multi-task learning,” Nat. Sci.
Rev., vol. 5, no. 1, pp. 30–43, Jan. 2018.
[33] Z. Zhang, H. Wang, F. Xu, and Y .-Q. Jin, “Complex-valued convolu-
tional neural network and its application in polarimetric SAR image
classiﬁcation,” IEEE Trans. Geosci. Remote Sens. , vol. 55, no. 12,
pp. 7177–7188, Dec. 2017.
[34] H. Lin and J. Yuan, “Multicarrier modulation on delay-Doppler plane:
Achieving orthogonality with ﬁne resolutions,” in Proc. IEEE Int. Conf.
Commun., May 2022, pp. 2417–2422.
[35] C. Lee, H. Hasegawa, and S. Gao, “Complex-valued neural networks:
A comprehensive survey,” IEEE/CAA J. Autom. Sinica , vol. 9, no. 8,
pp. 1406–1426, Aug. 2022.
[36] Z. Fan, Z. Ji, P. Fu, T. Wang, X. Shen, and Q. Sun, “Complex-
valued spatial-scattering separated attention network for PolSAR image
classiﬁcation,” in Proc. IEEE Int. Geosci. Remote Sens. Symp. , Sep.
2020, pp. 1723–1726.
[37] M. Ohlson, M. Rauf Ahmad, and D. von Rosen, “The multilinear normal
distribution: Introduction and some basic properties,” J. Multivariate
Anal., vol. 113, pp. 37–47, Jan. 2013.
[38] Z. Shi, J. A. Zhang, R. Y . Xu, and Q. Cheng, “Environment-robust
device-free human activity recognition with channel-state-information
enhancement and one-shot learning,” IEEE Trans. Mobile Comput. ,
vol. 21, no. 2, pp. 540–554, Feb. 2022.
[39] X. Gao and Y . Fang, “A note on the generalized degrees of freedom
under the L1 loss function,” J. Stat. Planning Inference , vol. 141, no. 2,
pp. 677–686, Feb. 2011.
[40] F. Zhuang et al., “A comprehensive survey on transfer learning,” Proc.
IEEE, vol. 109, no. 1, pp. 43–76, Jan. 2021.
[41] S. J. Pan and Q. Yang, “A survey on transfer learning,” IEEE Trans.
Knowl. Data Eng. , vol. 22, no. 10, pp. 1345–1359, Oct. 2009.
[42] 5G: NR; Base Station (BS) Radio Transmission and Reception , document
TS 38.104, 3GPP, 2019.
[43] X. Zhang, Y . Zhang, Z. Shi, and T. Gu, “MmFER: Millimetre-wave radar
based facial expression recognition for multimedia IoT applications,” in
Proc. 29th Annu. Int. Conf. Mobile Comput. Netw. , Oct. 2023, pp. 1–15.
[44] NR; Physical Layer Procedures for Data , document TS 38.214, 3GPP,
2018.
Qingqing Cheng (Member, IEEE) received the M.E.
degree from Harbin Institute of Technology, China,
in 2015, the Master of Research (MRes) degree
from Macquarie University, Australia, in 2016, and
the Ph.D. degree from the University of Technology
Sydney, Australia, in 2020. From 2020 to 2024, she
was a Post-Doctoral Research Associate with the
School of Electrical Engineering and Telecommu-
nications, University of New South Wales, Sydney,
Australia. Since 2024, she has been working as a
Lecturer with the School of Electrical Engineering
and Robotics, Queensland University of Technology (QUT), and is currently
an ARC DECRA Fellow. Her research interests include deep learning,
integrated sensing and communications, high mobility systems, 5G security,
privacy preservation, cognitive radio, and massive MIMO.
Zhenguo Shi (Member, IEEE) received the M.S. and
Ph.D. degrees from Harbin Institute of Technology
(HIT), China, in 2011 and 2016, respectively, and
the Ph.D. degree from the University of Technology
Sydney (UTS), Australia, in 2022. He was a Post-
Doctoral Research Associate with the School of
Computing, Macquarie University, Australia, from
2021 to 2023, and a Senior Post-Doctoral Research
Fellow with the School of Computing Engineering,
University of New South Wales (UNSW), Australia,
from 2023 to 2025. He is currently working as a
Senior Post-Doctoral Research Fellow with the School of Computer Science,
Queensland University of Technology (QUT), Australia. His research interests
include wireless sensing, human activity recognition, the IoT, deep learning,
cognitive radio, interference alignment, and wireless communication.
Jinhong Yuan (Fellow, IEEE) received the B.E.
and Ph.D. degrees in electronics engineering from
Beijing Institute of Technology, Beijing, China, in
1991 and 1997, respectively. From 1997 to 1999,
he was a Research Fellow with the School of Elec-
trical Engineering, University of Sydney, Sydney,
Australia. In 2000, he joined the School of Electrical
Engineering and Telecommunications, University of
New South Wales, Sydney, where he is currently a
Professor and the Head of School. He has published
two books, ﬁve book chapters, more than 300 articles
in telecommunications journals and conference proceedings, and 50 industrial
reports. He is a co-inventor of one patent on MIMO systems and four patents
on low-density-parity-check codes. His current research interests include error
control coding and information theory, communication theory, and wireless
communications. He has co-authored four Best Paper Awards and one Best
Poster Award, including the Best Paper Award from the IEEE International
Conference on Communications, Kansas City, MO, USA, in 2018; the Best
Paper Award from the IEEE Wireless Communications and Networking
Conference, Canc ´un, Mexico, in 2011; and the Best Paper Award from
the IEEE International Symposium on Wireless Communications Systems,
Trondheim, Norway, in 2007. He served as the IEEE NSW Chapter Chair
for Joint Communications/Signal Processing/Ocean Engineering Chapter from
2011 to 2014 and served as an Associate Editor for IEEE T RANSACTIONS ON
COMMUNICATIONS from 2012 to 2017. He is currently serving as an Asso-
ciate Editor for IEEE T RANSACTIONS ON WIRELESS COMMUNICATIONS
and IEEE T RANSACTIONS ON COMMUNICATIONS .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:52 UTC from IEEE Xplore.  Restrictions apply.
