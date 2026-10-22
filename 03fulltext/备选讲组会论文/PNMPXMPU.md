---
type: literature-fulltext
title: "From Sensing to Secrecy: Active Eavesdropper Localization in Massive MIMO ISAC"
zotero_key: "PNMPXMPU"
pdf_key: "6V2T7B7J"
doi: "10.1109/TWC.2026.3726300"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/From Sensing to Secrecy- Active Eavesdropper Localization in Massive MIMO ISAC.md"
fulltext_path: "03fulltext/备选讲组会论文/PNMPXMPU.md"
zotero_item: "zotero://select/library/items/PNMPXMPU"
zotero_pdf: "zotero://open-pdf/library/items/6V2T7B7J"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# From Sensing to Secrecy: Active Eavesdropper Localization in Massive MIMO ISAC

> PDF 原文逐页文本抽取；来源文件 SHA-256：`f63006448d549fc9c3ab81b42429cad813dc1f0c9e9a7085e5977332076e95cf`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 23487
From Sensing to Secrecy: Active Eavesdropper
Localization in Massive MIMO ISAC
Zonghan Wang
 , Member , IEEE, Jiajun He
 , Member , IEEE, Zahra Mobini
 , Senior Member , IEEE,
Hien Quoc Ngo
 , Fellow, IEEE, Hyundong Shin
 , Fellow, IEEE, and Michail Matthaiou
 , Fellow, IEEE
Abstract—This paper investigates a secure massive multiple-
input multiple-output (mMIMO) integrated sensing and commu-
nication (ISAC) system and proposes a framework capable of
precisely localizing an active eavesdropper (Eve) while simul-
taneously ensuring secure communication for legitimate user
equipment (UEs). Compared with existing ISAC studies that
primarily focus on sensing in the downlink phase, the pro-
posed design leverages the uplink and downlink structure of
time-division duplexing (TDD)-based ISAC systems by explicitly
exploiting uplink training information to assist downlink localiza-
tion. In the uplink, pilot-based channel estimation is performed
in the presence of a pilot spooﬁng attack (PSA), enabling reliable
detection of Eve’s angle of arrival (AoA). This coarse AoA
estimate is then used in the downlink to form a dedicated
sensing region that achieves precise, multipath-resilient direct
localization of the Eve. Closed-form expressions for the signal-
to-interference-plus-noise ratios (SINRs) at the legitimate UEs
and Eve are derived, facilitating a theoretical evaluation of the
system’s secrecy spectral efﬁciency (SSE). A tractable closed-form
Received 17 March 2026; revised 17 July 2026; accepted 13 August 2026.
Date of publication 1 September 2026; date of current version 18 September
2026. This work was supported by U.K. Engineering and Physical Sci-
ences Research Council (EPSRC) for TITAN Telecoms Hub under Grant
EP/X04047X/2. The work of Jiajun He was supported by the Horizon
Europe’s Marie Skłodowska-Curie Actions (HORIZON-MSCA) through the
Project Towards Energy- and Cost- Efﬁcient Cell-Free ISAC In Sub-6 GHz
and mmWave HetNets (ECO-ISAC) under Grant 101274088. The work of
Hien Quoc Ngo was supported in part by the Research Grant from the
Department for the Economy Northern Ireland under U.S.-Ireland Research
and Development Partnership Program and in part by the MULTIPLY-6G
Project from the Smart Networks and Services Joint Undertaking (SNS JU)
through European Union’s Horizon Europe Research and Innovation Program
under Grant 101293106. The work of Hyundong Shin was supported in
part by the National Research Foundation of Korea (NRF) grant funded by
Korean Government [Ministry of Science and ICT (MSIT)], South Korea,
under Grant RS-2025-00556064 and Grant RS-2025-25442355; and in part by
MSIT, through the Information Technology Research Center (ITRC) Support
Program supervised by the Institute for Information and Communications
Technology Planning and Evaluation (IITP) under Grant IITP-2025-RS-2021-
II212046. The work of Michail Matthaiou was supported by European
Research Council (ERC) through European Union’s Horizon 2020 Research
and Innovation Program under Grant 101001331. The associate editor coor-
dinating the review of this article and approving it for publication was B.
Chalise. (Corresponding authors: Michail Matthaiou; Hyundong Shin.)
Zonghan Wang, Jiajun He, and Hien Quoc Ngo are with the Centre for
Wireless Innovation (CWI), Queen’s University Belfast, BT3 9DT Belfast,
U.K. (e-mail: zwang95@qub.ac.uk; j.he@qub.ac.uk; hien.ngo@qub.ac.uk).
Zahra Mobini is with the Department of Electrical and Electronic Engi-
neering, The University of Manchester, M13 9PL Manchester, U.K. (e-mail:
zahra.mobini@manchester.ac.uk).
Hyundong Shin is with the Department of Electronics and Information
Convergence Engineering, Kyung Hee University, Yongin-si, Gyeonggi-do
17104, Republic of Korea (e-mail: hshin@khu.ac.kr).
Michail Matthaiou is with the Centre for Wireless Innovation (CWI),
Queen’s University Belfast, BT3 9DT Belfast, U.K., and also with the
Department of Electronic Engineering, Kyung Hee University, Yongin-si,
Gyeonggi-do 17104, Republic of Korea (e-mail: m.matthaiou@qub.ac.uk).
Digital Object Identiﬁer 10.1109/TWC.2026.3726300
expression for the position error bound (PEB) is also derived.
To jointly optimize sensing and communication performance, we
propose a power allocation problem that maximizes the SSE while
satisfying a given mainlobe-to-average-sidelobe ratio (MASR)
threshold and power constraints. Numerical results demonstrate
that the proposed joint uplink and downlink ISAC framework
achieves substantially improved localization accuracy in multi-
path scenarios and signiﬁcantly enhances secrecy performance,
compared to conventional secure ISAC systems.
Index Terms—Integrated sensing and communication, massive
multiple-input multiple-output, pilot spooﬁng attack, position
error bound, secrecy spectral efﬁciency.
I. I NTRODUCTION
T
HE integration of sensing functionalities into commu-
nication systems is expected to be a key component
of future wireless networks as outlined in ITU [1], [2].
By jointly utilizing shared spectrum and hardware resources in
a cooperative manner, integrated sensing and communication
(ISAC) systems enable the base station (BS) to acquire accu-
rate environmental information from sensing signals, while
simultaneously delivering data to multiple user equipment
(UEs). This paradigm facilitates adaptive resource allocation
strategies based on sensing outcomes, thereby enhancing the
performance of both sensing and communication tasks. In
parallel, massive multiple-input multiple-output (mMIMO)
systems, as one of the key enablers for sixth-generation
(6G) wireless communications, provide higher degrees of
freedom (DoF) and superior advanced signal processing capa-
bilities compared to conventional MIMO systems, thereby
signiﬁcantly improving the spectral and energy efﬁciency of
wireless communication networks [3]. Thanks to the abundant
hardware resources and DoF, the integration of the sensing
functionalities and mMIMO communications has attracted
widespread research interest from the academic and industrial
communities [4], [5].
However, due to the open nature of wireless channels,
enhancing the performance of legitimate communications can
inadvertently increase their vulnerability to eavesdroppers
(Eves) [6]. Ensuring the information security of UEs has
become a critical challenge, attracting extensive research atten-
tion and leading to the development of various approaches
aimed at enhancing wireless system security [7]. Traditional
approaches, such as those in [8], primarily rely on crypto-
graphic encryption to prevent eavesdropping. However, these
methods often incur high computational complexity [9]. As
a complement to cryptographic techniques, physical-layer
security (PLS) has attracted signiﬁcant research interest [10].
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

23488 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE I
COMPARISON WITH EXISTING SECURE ISAC S TUDIES
In this space, an active Eve can launch a pilot spooﬁng attack
(PSA) by transmitting the same pilot sequences as legitimate
UEs, thereby contaminating the channel estimation process at
the BS. This attack signiﬁcantly enhances the eavesdropping
capability of the Eve and degrades the achievable secrecy
spectral efﬁciency (SSE) [11], [12]. Consequently, ensuring
communication security is a major challenge in conventional
time-division duplexing (TDD)-based mMIMO systems [13].
Some studies have also investigated covert communication in
wireless networks. It is worth noting that PLS and covert-
ness address different security objectives. While PLS aims to
prevent Eves from decoding conﬁdential information, covert
communication aims to hide the existence of the transmission
from wardens. For instance, the covertness-outage tradeoff in
wireless transmission was analyzed in [14], which showed
that the performance of transmission outage probability and
covertness should be jointly considered. In ISAC systems,
this challenge becomes even more pronounced, as embed-
ding communication information into sensing waveforms may
expose private data to unintended receivers and increase the
detectability of transmissions by eavesdroppers [15], thereby
posing signiﬁcant risks to communication security.
Interestingly, the sensing functionality of ISAC can provide
a viable approach to address the challenges associated with
eavesdropping, offering new opportunities and critical insights
into future PLS [16]. With the assistance of the sensing func-
tion, the system can detect and obtain spatial characteristics
of the potential Eve, thereby providing enhanced positional
accuracy for authorized parties to legitimately monitor the
system. Given the unique security challenges and opportuni-
ties, PLS for ISAC systems has been the focus of extensive
research. In particular, the authors in [18] considered a single
BS ISAC system, leveraging information from cooperative
UEs to enable Eve’s detection and angle estimation. Similarly,
a two-stage transmission protocol was proposed in [19] to
estimate the angle of Eve. An optimal beamforming strategy
was designed to secure the communication with a legitimate
UE and minimize the information leakage to Eve. The study
in [16] considered a scenario with multiple Eves and a
single legitimate UE, utilizing dedicated sensing signals to
estimate the angles of Eves, while transmitting artiﬁcial noise
to degrade the eavesdropping performance. An optimization
problem was also formulated to minimize the mean squared
error of Eve’s angle estimation while ensuring secure com-
munication. Speciﬁcally, the authors in [17] considered the
effect of PSA, and an optimization problem was formulated
to maximize the received sensing signal-to-interference-plus-
noise ratio (SINR) while minimizing the Eve’s SINR. The
comparison between our system and existing secure ISAC
schemes is summarized in Table I.
Nevertheless, the existing secure ISAC frameworks still
treat the detection of a potential Eve as a primary sens-
ing task, which inherently restricts the system’s ability to
fully exploit spatial information for security enhancement.
To enhance the capabilities of ISAC systems, the sensing
function could be leveraged for higher-level services, such
as localization, rather than merely detecting the presence
of an Eve. By exploiting signals reﬂected from the target,
obtaining accurate location plays a crucial role in enhanc-
ing a network’s understanding of the radio environment,
enabling advanced tasks, such as efﬁcient channel estimation
and blockage detection [20], [21]. Some studies considered
high-precision localization as the primary sensing task. The
estimated Eve’s position provides spatial information for
secure transmission. It can be exploited to design artiﬁcial-
noise or jamming beams directed toward suspicious regions,
construct leakage-suppression or null-space beamforming to
reduce conﬁdential signal leakage toward Eve, and support
UE rescheduling for UEs that are spatially close to Eve. Once
Eve’s position is accurately estimated, the network operator
can apply authorized countermeasures, such as proactive moni-
toring [22], effective interception and capture [23] to secure the
wireless network. For instance, Shi et al. considered a cellular
ISAC network using orthogonal frequency-division multiplex-
ing (OFDM) and proposed a two-step localization algorithm
with data association to obtain a target’s precise location in
[24]. Similarly, [25], [26], [27] studied cell-free ISAC systems.
However, they mainly relied on indirect two-step estimation
methods, where intermediate parameters, such as distances and
angle information, were ﬁrst estimated and then combined via
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

W ANG et al.: FROM SENSING TO SECRECY: ACTIVE EA VESDROPPER LOCALIZATION IN MASSIVE MIMO ISAC 23489
trilateration or triangulation, which could lead to suboptimal
performance since useful information might be lost during the
intermediate process [28]. This limitation becomes particularly
severe in multipath environments, where identifying direct
path (DP) components among indirect path (IDP) is inherently
challenging, and small errors in any receiver access point’s
(Rx-AP’s) estimation could be ampliﬁed through the local-
ization process [29]. On the other hand, conventional direct
localization methods avoid intermediate parameter estimation
by searching for the target position over the entire region of
interest using dense spatial grids. However, an exhaustive grid
search incurs prohibitive computational complexity when high
resolution or large coverage areas are required. Although a
number of existing studies have investigated the function of
sensing in secure ISAC systems, the incorporation of precise
localization mechanisms into secure ISAC frameworks has
received comparatively limited attention. Furthermore, most
ISAC studies emphasize downlink transmission, while the
potential of uplink training and channel estimation remains
underexplored. By leveraging effective uplink training and
utilizing the characteristic of pilot spooﬁng, the transmitter AP
(Tx-AP) can efﬁciently obtain the Eve’s angle and concentrate
the transmission power in the direction of the Eve to improve
localization performance and avoid spending resources on
uninteresting targets [15].
Motivated by the above discussion, this paper proposes
an ISAC framework with one mMIMO Tx-AP and mul-
tiple Rx-APs for precise localization of an active Eve in
complex multipath environments. The approach leverages
cooperation among APs to enhance both communication
for legitimate UEs and localization accuracy for the active
Eve. In the uplink, pilot-based channel estimation is used
to precode downlink signals, explicitly accounting for pilot
spooﬁng and channel estimation errors. The system detects
Eve’s AoA in the uplink and then transmits a dedicated
sensing beam in the downlink for accurate position localiza-
tion. This joint uplink and downlink design enables efﬁcient
channel estimation and precise localization within a uniﬁed
ISAC framework. Combined with a power optimization strat-
egy, the proposed design offers a comprehensive solution
for secure ISAC operation. Our key contributions are as
follows:
• Tractable Secrecy Performance Analysis : A comprehen-
sive theoretical performance analysis of the proposed
secure ISAC system is presented. Closed-form expres-
sions for the effective SINRs at both the legitimate UEs
and Eve are derived using the use-and-then-forget bound-
ing technique. These analytical results lead to a tractable
expression for the SSE of the UE under eavesdropping
attacks.
• Robust Localizaiton of Eve : We derive a closed-form
expression for the PEB based on the received signals.
The localization problem in the downlink is addressed
using a direct localization approach, which avoids inter-
mediate parameter estimation errors. In addition, the
AoA estimates obtained in the uplink are incorporated to
enhance localization efﬁciency and accuracy in multipath
environments.
Fig. 1. Secure mMIMO ISAC system model.
• Power Optimization : To achieve an optimal trade-off
between secure communication and high-accuracy local-
ization, we formulate a power allocation problem that
adaptively allocates transmit power between commu-
nication and localization functions. The optimization
objective seeks to maximize the SSE while guarantee-
ing the SINR requirements of all legitimate UEs and
satisfying a mainlobe-to-average-sidelobe ratio (MASR)
constraint.
Notation: A complex Gaussian vector with mean vector a
and covariance matrix B is denoted byCN (a, B). The super-
scripts (·)H, (·)∗, (·)−1 and (·)T stand for the Hermitian,
conjugate, inverse and transpose operators; ||·|| denotes the
Euclidean norm; IN stands for the N×N identity matrix;
Re{·} and Im{·} are the real part and imaginary part of
a complex number. Moreover, E{·} denotes the statistical
expectation, while tr(·) denotes the trace of a matrix.
II. S YSTEM MODEL
We consider a multistatic mMIMO ISAC system with one
ISAC Tx-AP, M Rx-APs, K legitimate UEs and one target
regarded as a potential Eve as shown in Fig. 1. Through the
sensing function, the system can detect and extract the spatial
characteristics of the target (potential Eve), thereby accurately
localizing the Eve and enabling authorized parties to legally
monitor the system. The Tx-AP and Rx-APs are connected
to the central processing unit (CPU) via backhaul links. We
assume that each UE and the Eve are equipped with a single
antenna, while the Tx-AP and each Rx-AP are equipped with
Nt and Nr antennas, respectively. Without loss of generality,
we assume that the Eve aims to overhear UE 1 among the
K legitimate UEs. Assume that the TDD operation is adopted,
offering channel reciprocity between the uplink and downlink
transmissions.
Each channel vector between the Tx-AP to UE k, denoted
by gk, is modeled as a Ricean fading channel vector, while
the channel between the Tx-AP and the Eve, denoted by gE,
is modeled as pure LoS. Hence, the channels gk and gE are:
gk =
√
βkκ
1 +κa(θTx,k) +
√
βk
1 +κg′k, (1)
gE =
√
βEa(θTx,E), (2)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

23490 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
where βk = d−αTx,k and βE = d−αTx,E are the large-scale path-
loss coefﬁcients between the Tx-AP and UE k and between
the Tx-AP and Eve, respectively. The distances between the
Tx-AP and UE k, and the distances between the Tx-AP and
the Eve are denoted by dTx,k and dTx,E, respectively, while
α denotes the path-loss exponent. The Ricean K-factor is
denoted by κ. The deterministic LoS component of gk is
denoted by ¯gk =
√
βkκ
1+κ a(θTx,k), where a(θTx,k)∈ CNt×1
and a(θTx,E) ∈ CNt×1 in (2) denote the array steering
vectors corresponding to the angles of departure (AoD) θTx,E
and θTx,k, respectively. Moreover, the NLoS components are
modeled as spatially correlated complex Gaussian vectors
g′k∼CN (0, R′k), where R′k∈ CNt×Nt is the positive semi-
deﬁnite covariance matrix describing the spatial correlation
of the NLoS components. Accordingly, the effective channel
follows gk∼CN (¯gk, Rk), where Rk = βk1+κ R′k.
Remark 1: Although the Tx-AP → Eve link is modeled
as LoS for analytical tractability, the proposed localization
framework is not restricted to a pure LoS sensing environ-
ment, since the Eve → Rx-AP channels include multi-path
components. In particular, the LoS assumption is only adopted
for the Tx-AP → Eve illumination stage, where the Tx-AP
forms a directional sensing beam toward the Eve’s direction
obtained from uplink phase. In contrast, after the signal is
reﬂected by Eve, the propagation toward the distributed Rx-
APs contains multiple paths through scatterers. Therefore, the
overall cascaded sensing channel used for localization remains
a multi-path scenario.
A. Uplink Training
During the uplink training phase, each UE transmits a pilot
sequence of length τp, with the sequences assumed to be
mutually orthonormal. We consider that an active Eve launches
a PSA by transmitting the same pilot sequence as one of the
UEs (say UE 1), thereby enhancing its ability to overhear the
legitimate communication link. It should be noted that UE 1 is
used only to denote the targeted legitimate UE without loss of
generality.1 The channels between the Tx-AP and the UEs are
uncorrelated and independent. In this scenario, the received
pilot signal at the Tx-AP is given by:
Yp =
√
τpPp
∑K
k=1
gkϕHk +√τpPp,EgEϕH1 + Np, (3)
where ϕk∈ Cτp×1 denotes the pilot sequence of the UE k,
while Np ∈ CNt×τp has independent and identically dis-
tributed (i.i.d.) Gaussian random elements with zero mean and
varianceσ2. The transmit powers for pilot transmission at the
UEs and at the Eve are denoted by Pp andPp,E, respectively.
Under the assumption of orthonormal pilot sequences, we
obtain the processed received pilot signal ˇyp,k = Ypϕk as
ˇyp,k =
{√
τpPpgk + Npϕk, if k⁄= 1,√
τpPpgk +
√
τpPp,EgE + Npϕk, if k = 1.
(4)
1The pilot sequences are typically selected from public known transmission
protocols, follow a standardized structure, and can be repeatedly used over
coherence blocks [30]. Thus, an active Eve can obtain the pilot sequence
assigned to the overheard UE.
Assuming the system has no knowledge of the PSA,
the mean value of the processed received pilot signal is
¯yp,k = √τpPp ¯gk. By invoking the minimum-mean-square-
error (MMSE) estimation technique, the estimate of gk is [31]:
ˆgk = E{gk}+Cov{gkˇyHp,k}( Cov{ˇyp,k})−1(ˇyp,k−¯yp,k)
= ¯gk +
√
τpPp RkΨk(ˇyp,k− ¯yp,k)
= ¯˙gk+√τpPpRkΨk(√τpPp˜gk+Npϕk), (5)
where ¯˙gk = ¯gk for k ⁄= 1 , while ¯˙g1 = ¯g1 +
τp
√
PpPp,ER1Ψ1gE for k = 1 . The channel ˜gk =√
βk
1+κg′k∈ CNt×1 denotes the NLoS component in (1), which
includes the large-scale channel gain. From (5), the estimated
channel follows the distribution ˆgk ∼ CN(¯˙gk, Φk), where
the covariance matrix is given by Φk =τpPpRkΨkRk with
Ψk = Cov{ˇyp,k}−1 =(τpPpRk +σ2INt)−1.
Then, we propose a simple angle-domain estimation to
detect the AoA range of the Eve. Speciﬁcally, we deﬁne the
normalized discrete Fourier transform (DFT) of the vector as
ˇyDFT,k = Fˇyp,k, where F is an Nt×Nt DFT matrix, whose
(p,q )-th element is [F]pq = 1√Nte−j 2πNtpq. Each column of Frepresents a beam pointing in a speciﬁc physical direction.
Consequently, most of the channel power is concentrated
around the beam corresponding to the LoS component within
the beam-space domain. By following [32] and utilizing coop-
eration between the Tx-AP and legitimate UEs, the Tx-AP can
identify the AoAs of the legitimate UEs based on prior infor-
mation. Thus, when the UE is under a pilot spooﬁng attack,
the estimated channel in the beam domain exhibits multiple
peaks, each corresponding to a distinct direction, including the
direction of the Eve. The proposed AoA-assisted framework
can also be extended by replacing the far-ﬁeld steering vector,
a(θTx,E), with a hybrid-ﬁeld response, a(rTx,E,θ Tx,E) [33].
The uplink stage would then provide a coarse spatial prior in
the distance-angle domain, while the downlink sensing beam
would be designed as a near-ﬁeld focusing or hybrid-ﬁeld
beam.
Remark 2: In the uplink training phase, the beam-domain
observation of a UE may contain not only the LoS com-
ponent but also scatterer-induced NLoS components. If a
ﬁxed scatterer is visible to multiple UE–Tx-AP links, the
reﬂected signals from this scatterer arrive at the Tx-AP from
approximately the same angular direction, since the scatterer
and the Tx-AP have ﬁxed locations. Thus, by comparing the
beam-domain mappings obtained from different orthogonal
UE pilots, repeated angular peaks can be identiﬁed as scatterer-
related environmental components. In contrast, when UE 1
experiences pilot spooﬁng, the Eve-related peak appears only
in the beam-domain observation corresponding to the contam-
inated pilot. After excluding the known UE direction and the
common scatterer-related directions, the remaining additional
dominant peak can be used to obtain a coarse AoA estimate
of Eve.
We note that if a scatterer is only visible to one UE link,
its reﬂected peak may not be removed by the comparison
among all UEs. However, this detection is not the only mech-
anism for mitigating scatterer components in the uplink stage.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

W ANG et al.: FROM SENSING TO SECRECY: ACTIVE EA VESDROPPER LOCALIZATION IN MASSIVE MIMO ISAC 23491
In practice, multi-path components can also be distinguished
from the LoS component by using delay information, since
they experience longer propagation paths and thus exhibit a
larger time of arrival [34]. Moreover, dominant static reﬂectors
can be pre-estimated through ofﬂine environmental calibration
and canceled before Eve detection.
Note that during the uplink training phase, the objective
is not to obtain the precise location of the Eve but rather to
estimate its approximate AoA. This coarse angular estimation
ensures that the Eve’s direction lies within the main lobe of
the antenna, enabling the Tx-AP to beamform toward the iden-
tiﬁed direction in the downlink phase to maximize the array
gain. The AoA of Eve can be estimated as ˆθTx,E =θTx,E+∆θ,
where ∆θ is the angular error due to limited resolution, which
is based on the number of antenna elements on the Tx-AP [32].
If Eve is angularly very close to UE 1, the two peaks in
the beam domain may not be resolvable. For a ULA, this
occurs when their angular separation lies within the array
resolution region. This ambiguity can be reduced by increasing
the number of transmit antennas, which improves the angular
resolution of the Tx-AP. Moreover, we consider the scatterers
are visible to all UE links. In practice, additional multi-path
mitigation techniques [35] can be incorporated to identify and
remove multi-path components before detecting Eve. Once
the angular of the Eve is obtained, the proposed downlink
direct localization stage can further estimate Eve’s position
by exploiting the received signals across multiple Rx-APs.
B. Downlink Communication
During downlink, the Tx-AP beamforms the information-
bearing signal, sk, to the corresponding served user k, where
k = 1, 2,...,K , and the sensing signal, sE, for localizing
the Eve. Each symbol is zero mean with unit power i.e.
E
{
|sk|2} = 1 and E{|sE|2} = 1 . The power control
coefﬁcients for thek-th UE and for localizing Eve are denoted
by ηk and ηE, respectively. The transmitted signal from the
Tx-AP is:
x =
∑K
k=1
√
ηkPTxwksk +
√
ηEPTxwEsE, (6)
where wk = ˆgk is the precoding vector for the k-th UE,
and PTx is the maximum downlink transmit power of the
Tx-AP. The beamforming vector for sensing the target can
be denoted by wE = a(ˆθTx,E), where ˆθTx,E is the erro-
neous estimate of the target’s direction. In this work, MRT
precoding is adopted for the downlink communication. First,
MRT has low computational complexity, which is particularly
important when the number of transmit antennas is large.
Second, in the considered mMIMO system, the favorable
propagation property makes the channels of spatially separated
UEs become asymptotically orthogonal as Nt grows large. As
a result, MRT can provide effective spatial separation when the
Tx-AP is equipped with a sufﬁciently large antenna array.
Third, MRT enables tractable closed-form SINR derivations
under imperfect channel estimation and pilot spooﬁng, which
is essential for the secrecy performance analysis and the power
allocation problem [9], [31]. The received signal at the k-th
UE is
yk =
√
ηkPTxgHk wksk| {z }
DSk
+
∑K
k′⁄=k
√
ηk′PTxgHk wk′sk′
| {z }
IUIk′,k
+
√
ηEPTxgHk wEsE| {z }
SIk
+ nk|{z}
noise
, (7)
where DSk, IUIk′,k, and SIk denote the desired signal,
inter-UE and sensing interferences, respectively. The term
nk represents the additive white Gaussian noise (AWGN)
with nk∼CN (0,σ 2). The received signal at the Eve, which
overhears the conﬁdential messages intended for UE 1, can be
obtained as
yE = gHE√η1PTxw1s1| {z }
DSE
+
∑K
k′⁄=1 gHE√ηk′PTxwk′sk′| {z }
IUIE,k′
+ gHE√ηEPTxwEsE| {z }
SIE
+ nE|{z}
noise
, (8)
where DSE, IUIE,k′, SIE, and nE denote the strength of the
desired signal, inter-UE interference, sensing interference at
Eve and AWGN, respectively.
C. Sensing Model
We consider a multipath propagation environment fol-
lowing [36] to model the channel between the Eve and
an Rx-AP. Compared with conventional LoS channel models,
this model is more suitable for localization, as it can effectively
capture target related information embedded in multipath mea-
surements and exploit spatial diversity [37]. In a distributed
MIMO radar system, the signal transmitted from the Tx-AP
to the Rx-AP propagates through multiple paths, which can
be classiﬁed as follows: 1) DP, where the signal propagates
directly from the transmitter to the receiver via the target of
interest, i.e., the Eve; and 2) IDP, where the signal is reﬂected
not only by the target but also by other scatterers along its
propagation from the transmitter to the receiver. Paths that
do not involve the target of interest and are therefore not
useful for localization can be suppressed using background
cancellation techniques [36], [38]. For the second scenario,
IDPs can be classiﬁed into two types: 1) Tx-AP → Eve→
Scatterer→ Rx-AP; 2) Tx-AP → Scatterer→ Eve→ Rx-AP.
The two kinds of paths are shown in Fig. 1. With the assistance
of angle estimation during the uplink training phase, and
considering the high angular resolution and narrow beamwidth
offered by mMIMO beamforming, we assume that in the beam
domain, the beamforming direction is nearly orthogonal to
the directions corresponding to the multipath components in
the Tx-AP → Eve stage [39]. Therefore, for the Tx-AP →
Eve channel used for localization, only the LoS component
is considered, as described in (2). Accordingly, the channel
from the Eve to m-th Rx-AP includes DP and the ﬁrst IDP.
The multipath channel from the Eve to m-th Rx-AP, denoted
by hE,m∈ CNr×1, is modeled as
hE,m =
∑L
l=0
√
βE,m,l, a(θl,m), (9)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

23492 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
where
√
βE,m,l and θl,m denote the large-scale fading gain
and AoA of l-th path from the Eve to m-th Rx-AP. The DP
corresponds to the case when l = 0 , with θ0,m = θE,m
denoting the AoA of the LoS path from the Eve to the
m-th Rx-AP. Combining (2) and (9), the effective sensing
channel Hm ∈ CNr×Nt between the Tx-AP and the m-th
Rx-AP is
Hm =
∑L
l=0
am,l
√
βm,l, a(θl,m)aH(θTx,E), (10)
where
√
βm,l denotes the total large-scale fading gain of the
l-th path from the Tx-AP to m-th Rx-AP, and the channel
coefﬁcient am,l∼CN (0,σ 2s ) accounts for small-scale fading
and the reﬂection effect of the l-th path. The corresponding
large-scale fading coefﬁcient is given by βm,0 = d−αTx,m,0 =
(dTx,E +dE,m)−α [21], [35], [37], where dTx,E and dE,m
represent the distances between the Tx-AP and the Eve,
and between the Eve and the m-th Rx-AP, respectively.
Forl⁄= 0, the IDP experiences additional reﬂection losses, and
the corresponding large-scale fading coefﬁcients are modeled
as βm,l = d−αTx,m,l = (dTx,E +dE,l +dl,m)−α, where dE,l
and dl,m denote the distances between the Eve and the l-th
scatterer, and between the l-th scatterer and the m-th Rx-AP,
respectively.
The received signal at the m-th Rx-AP can then be:
ym = Hmx + nm
(a)
≈
∑L
l=0
am,l
√
βm,la(θl,m)Gant
√
ηEPTxsE+nm,
(11)
where in (a), we use a key property of mMIMO systems
that the uplink and downlink channels exhibit favorable prop-
agation, showing that the channel vectors associated with
different UEs become asymptotically orthogonal as the num-
ber of antennas grows large [40]. Consequently, the inner
product between the steering vector of the Eve and the LoS
of a legitimate UE k satisﬁes 1Nt aH(θTx,E)a(θTx,k) → 0,when Nt is large enough. Therefore, the communication
interference becomes negligible for localization. By exploit-
ing the narrow beamwidth of mMIMO beamforming, we
further formulate the inner product aH(θTx,E)a(ˆθTx,E) as
the array gain along the main lobe direction. Under the
ﬂat-top antenna pattern approximation [41], we approxi-
mate the antenna gain as aH(θTx,E)a(ˆθTx,E) = Gant.
In particular, the antenna gain Gant can be approximated
as
Gant =
{
Gmax, |∆θ|≤ θq,
Gmin, |∆θ|>θ q, (12)
where θq is the beamwidth of the main lobe, and Gmax and
Gmin are the array gains of main and side lobes, and can be
calculated following [41], respectively.
It is worth noting that the approximation in (11) is
made at the Tx-AP side rather than at the Rx-AP side.
Speciﬁcally, this approximation does not require each
Rx-AP to be equipped with a large number of anten-
nas. The array response of the l-th path, observed by the
Fig. 2. CDF of sensing SINR at four Rx-APs for κ = 3 dB, Nr = 8 ,
PTx = 3 W,K = 4, and r = 50 m.
m-th Rx-AP a(θl,m)∈ CNr×1, is still retained in the sens-
ing model and directly contributes to the AoA information
and PEB.
To validate the approximation in (11) for ﬁnite-dimensional
arrays, Fig. 2 compares the CDF of the sensing SINR at
the four Rx-APs. The numerical curves are obtained by
directly retaining the communication interference term, while
the marker curves are obtained from the approximated model.
It is observed that the approximated results closely match the
numerical results for both Nt = 64 and Nt = 128 across
all Rx-APs. This conﬁrms that the approximation is accurate
under the considered practical antenna conﬁgurations.
The proposed framework relies on parametric channel
assumptions to obtain tractable SINR, PEB, and power allo-
cation expressions. Nevertheless, the adopted models consider
various propagation conditions. The Tx-AP → UE links are
modeled as Ricean fading channels, where the Ricean fac-
tor κ controls the relative strength of the LoS and NLoS
components. For sensing, besides the direct path from the
Tx-AP → Eve→ Rx-APs, indirect paths caused by envi-
ronmental scatterers are also considered. The proposed direct
localization method is therefore evaluated under both LoS and
multi-path conditions.
III. P ERFORMANCE ANALYSIS
In this section, we derive closed-form expressions for secure
communication. We then analyze the fundamental limits of
the proposed localization scheme in secure ISAC systems by
deriving the PEB. Furthermore, we derive the MASR, which
is subsequently used as a constraint in Section V.
A. Secure Communication Performance
In this section, we derive closed-form expressions for the
downlink achievable SINR of the legitimate UE and Eve,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

W ANG et al.: FROM SENSING TO SECRECY: ACTIVE EA VESDROPPER LOCALIZATION IN MASSIVE MIMO ISAC 23493
respectively, by availing of the use-and-then-forget bounding
technique [42]. 2 The SSE can be then computed.
Proposition 1: By using the use-and-then-forget bounding
technique, the corresponding SINR of UE k can be calculated
as
SINRk
= |E{DSk}|2
E{|BUk|2} +∑Kk′⁄=k E{|IUIk′,k|2} + E{|SIk|2} +σ2,
(13)
E{DSk} =
√
ηkPTx
(
tr
(
Φk
)
+ ¯gHk ¯˙gk
)
, (14)
E
{
|BUk|2} =ηkPTx[¯gHk Φk¯gk+¯˙gHk Rk¯˙gk
+τpPptr(ΦkΨkR2k)+τpPpσ2tr(RkΨ2kR2k)],
(15)
E
{
|IUIk′,k|2}=PTxηk′[tr(RkΦk′)+ ¯˙gHk′Rk¯˙gk′ + ¯gHk Φk′ ¯gk
+
⏐⏐¯gHk ¯˙gk′⏐⏐2], (16)
E
{
|SIk|2}=PTxηEaH(ˆθTx,E)(Rk + ¯gk¯gHk)a(ˆθTx,E). (17)
Proof: See Appendix A. ■
Proposition 2: The SINR of Eve can be expressed as
SINRE
= |E{DSE}|2
E{|BUE|2} +∑Kk′⁄=1 E{|IUIk′,E|2} + E{|SIE|2} +σ2,
(18)
E{DSE} =
√
η1PTxgHE
(
¯g1 +τp
√
PpPp,ER1Ψ1gE
)
,
(19)
E
{
|BUE|2} =η1PTxgHE Φ1gE, (20)
E
{
|IUIE,k′|2} =PTxηk′gHE(Φk′ + ¯˙gk′¯˙gHk′)gE, (21)
E
{
|SIE|2}=PTxηEβE⏐⏐aH(θTx,E)a(ˆθTx,E)⏐⏐2. (22)
Proof: See Appendix B. ■
Based on Propositions 1 and 2, we can calculate the SSE
associated with UE 1 using the derived SINR expressions as
SSE≈
[
log2
1 + SINR1
1 + SINRE
]+
, (23)
where [x]+ = max{x, 0} [12].
B. Sensing Performance
1) PEB Derivation: To evaluate the localization accuracy,
we adopt the PEB, which represents the theoretical lower
bound on the root mean square error (RMSE) achievable by
2The proposed optimization framework is based on the closed-form SINR
expressions obtained from the use-and-then-forget bound. The key property
enabling the proposed AO and path-following algorithm is that the desired
signal and interference terms are afﬁne with respect to the power control
variables ηk and ηE. Therefore, if another SINR bound preserves the same
fractional afﬁne structure, the proposed framework remains applicable after
updating the corresponding coefﬁcients in (49).
any unbiased position estimator. The PEB is derived in two
steps. In the ﬁrst step, the Fisher Information Matrix (FIM)
corresponding to the AoAs on Rx-APs is computed based on
the received signal model. In the second step, the FIM of
the Eve’s position can be obtained by applying a coordinate
transformation matrix. Finally, the PEB is determined as the
square root of the trace of the inverse of the position-domain
FIM, representing the minimum achievable error of position
estimation under unbiased conditions. We express the true
value of the received signal at m-th Rx-AP, denoted by µm
as
µm =
∑L
l=0
˜αm,la(θm,l)Gant
√
ηEPTxsE, (24)
where ˜αm,l =αm,l
√
βm,l is the unknown channel coefﬁcient.
Let ψm = [ψTm,0,..., ψTm,L]∈ R3(L+1) be a vector of the
unknown parameters, consisting of (L+1) AoAs and channel
coefﬁcients of DP/IDPs for the m-th Rx-AP, given byψm,l =[
θm,l, ˜αTm,l]T , where ˜αm,l = [˜αm,l,R, ˜αm,l,I]T contains the
real and imaginary parts of ˜αm,l. Without loss of generality,
we assume that the steering vector of the l-th path from the
Eve to the m-th Rx-AP is given by a(θm,l)∈ CNr×1, whose
n-th element is
[a(θm,l)]n = exp
(
j2π ∆dλ (n− 1) cos(θm,l)), (25)
where ∆d is the distance between any two adjacent antennas
andλ is the wavelength. We deﬁne an unbiased estimator ˆψm,
while the mean square error (MSE) is bounded by
Eym|ψm
[
( ˆψm−ψm)( ˆψm−ψm)T]≽ J−1ψm, (26)
where the matrix Jψm∈ R3(L+1)×3(L+1) is the FIM.
Proposition 3: The FIM Jψm can be structured as
Jψm =


Ψm(ψm,0,ψm,0) ... Ψm(ψm,0,ψm,L)
... ... ...
Ψm(ψm,L,ψm,0) ... Ψm(ψm,L,ψm,L)

,
(27)
in which the 3× 3 matrix Ψm(ψm,r,ψm,s), can be derived
as (28), shown at the bottom of the next page.
The entries are given by
Ψm(θm,r,θm,s)=GtRe
{
˜α∗m,r ˜αm,sAθθ(θm,r,θm,s)},
(29)
Ψm(θm,r, ˜αm,s,R) = Ψm(˜αm,r,R,θm,s)
=GtRe
{
˜α∗m,rAθ(θm,r,θm,s)}, (30)
Ψm(θm,r, ˜αm,s,I) = Ψm(˜αm,r,I,θm,s)
=−GtIm
{
˜α∗m,rAθ(θm,r,θm,s)},
(31)
Ψm(˜αm,r,R, ˜αm,s,R) = Ψm(˜αm,r,I, ˜αm,s,I)
=GtRe
{
A(θm,r,θm,s)
}
, (32)
Ψm(˜αm,r,R, ˜αm,s,I) = Ψm(˜αm,r,I, ˜αm,s,R)
=−GtIm
{
A(θm,r,θm,s)
}
, (33)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

23494 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
where Gt = 2G2antηEPTxσ2 , while
A(θm,r,θm,s)
=
∑Nr
n=1
exp
[
j2π ∆dλ (n−1)×( cos(θm,s)−cos(θm,r))],
(34)
Aθ(θm,r,θm,s)
=−j2π ∆dλ sin(θm,r)∑Nrn=1(n− 1)
× exp
[
j2π ∆dλ (n− 1)( cos(θm,s)− cos(θm,r))], (35)
Aθθ(θm,r,θm,s)
=
(
2π ∆dλ )2 sin(θm,r) sin(θm,s)∑Nrn=1(n− 1)2
× exp
[
j2π ∆dλ (n− 1)( cos(θm,s)− cos(θm,r))]. (36)
Proof: See Appendix C. ■
To derive the FIM in the position domain, we perform
a variable transformation from angle to the position-related
parameter vector ˜ψm,l. Since the goal of localization is to
estimate only the position of the Eve, and not to estimate the
positions of the scatterers, we focus exclusively on the DP,
i.e. l = 0. Accordingly, the transformed parameter vector for
the direct path is deﬁned as ˜ψm,0 = [pT0,αTm,0]T , where
p0 = [ x0,y 0]T is the location of Eve and αm,0 denotes
the channel parameters associated with the DP between the
Tx-AP and the m-th Rx-AP. The positions of the Tx-AP
and the m-th Rx-AP are pTx = [ xTx,y Tx]T and pm =
[xm,ym]T , respectively. For the case l≥ 1, we retain their
previously estimated parameters without performing additional
transformations, since these paths are not used for position
estimation. Therefore, the transformed parameter vector is
˜ψm = [pT0,αTm,0,ψTm,1,..., ψTm,L]∈ R(3L+4).
The FIM of ˜ψm, denoted by J ˜ψm, can be obtained by means
of the transformation matrix T∈ R(3L+4)×(3L+3) as J ˜ψm =
TJψmTT . The transformation matrix T can be calculated
as
T = ∂ψTm
∂ ˜ψm =


T0,0 ... TL,0
... ... ...
T0,L ... TL,L

, (37)
in which Tl,l′ = ∂ψTm,l∂ ˜ψm,l′ . For the case l = l′⁄= 0 , we have
∂ψTm,l
∂ ˜ψm,l′ = I3. For the case l =l′ = 0, T0,0∈ R4×3 is:
T0,0 =


∂θm,0
∂p0
∂ ˜αm,0
∂p0
∂θm,0
∂αm,0
∂ ˜αm,0
∂αm,0

, (38)
where ∂ ˜αm,0∂αm,0 = √βm,0I2 and the entries in
∂θm,0
∂p0 =
[
∂θm,0
∂x0 , ∂θm,0∂y0
]T
can be calculated as ∂θm,0∂x0 =
−(y0−ym)
(x0−xm)2+(y0−ym)2 and ∂θm,0∂y0 = (x0−xm)(x0−xm)2+(y0−ym)2 . The
2× 2 matrix ∂ ˜αm,0∂p0 can be calculated by
∂ ˜αm,0
∂p0
=

αm,0,R
∂
√
βm,0
∂x0
αm,0,R
∂
√
βm,0
∂y0
αm,0,I
∂
√
βm,0
∂x0
αm,0,I
∂
√
βm,0
∂y0

, (39)
where
∂
√
βm,0
∂x0
=−α2 d−α2−1Tx,m,0( x0−xTx‖p0− pTx‖ + x0−xm‖p0− pm‖),
(40)
∂
√
βm,0
∂y0
=−α2 d−α2−1Tx,m,0( y0−yTx‖p0− pTx‖ + y0−ym‖p0− pm‖).
(41)
The remaining entries in T are zero. The PEB is obtained
using the formula
PEB =
vuuu√tr[(∑Mm=1 J ˜ψm)−1]
1:2,1:2


. (42)
The proposed multistatic localization framework assumes
known AP locations, synchronized Rx-APs, reliable back-
haul links, and calibrated antenna arrays. In the considered
framework, the transmitted sensing signal is generated and
known at the CPU, and hence the reference sensing signal
is perfectly available for signal processing. In practice, syn-
chronization errors, backhaul distortion, calibration mismatch,
or AP location uncertainty may introduce additional observa-
tion noise or mismatch, leading to some degradation in the
practical PEB and direct localization accuracy. However, such
effects can be mitigated by calibration methods [43] before
transmission.
2) MASR Derivation: MASR is a widely adopted measure
in beampattern design for mMIMO ISAC systems, as it
quantiﬁes how effectively the signal power is concentrated
toward a target direction [4], [26], [44]. In the proposed design,
the communication beams are not intended to participate
in the sensing operation, since localization primarily relies
on the sensing signal echoed by the Eve. Nevertheless, the
transmit power allocated to the UEs may still generate sidelobe
interference in the direction of the Eve, thereby degrading
the effective sensing gain. Hence, MASR can be used to
analyze the impact of communication transmission on sensing
performance. Let Pcom(θTx,E) denote the spatial power dis-
tortion at angle θTx,E caused by the communication signals,
which is
Pcom(θTx,E)
Ψm(ψm,r,ψm,s) =


Ψm(θm,r,θm,s) Ψ m(θm,r,˜αm,s,R) Ψ m(θm,r, ˜αm,s,I)
Ψm(˜αm,r,R,θm,s) Ψ m(˜αm,r,R, ˜αm,s,R) Ψ m(˜αm,r,R, ˜αm,s,I)
Ψm(˜αm,r,I,θm,s) Ψ m(˜αm,r,I, ˜αm,s,R) Ψ m(˜αm,r,I, ˜αm,s,I)

. (28)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

W ANG et al.: FROM SENSING TO SECRECY: ACTIVE EA VESDROPPER LOCALIZATION IN MASSIVE MIMO ISAC 23495
=PTx
∑K
k=1
ηkE
{
|aH(θTx,E)wk|2}
=PTx
∑K
k=1
ηk
(⏐⏐aH(θTx,E)¯˙gk⏐⏐2+aH(θTx,E)Φka(θTx,E)).
(43)
The desirable sensing beampattern is given by Psen(θTx,E) =
N 2tηEPTx. The MASR is deﬁned as the ratio of the main
sensing beampattern lobe to the distortion lobes, given by
MASR
= ηEN 2t∑K
k=1ηk
(⏐⏐aH(θTx,E)¯˙gk⏐⏐2 + aH(θTx,E)Φka(θTx,E)).
(44)
IV. D IRECT EVE POSITIONING
To address the target localization problem, we employ the
principles of compressive sensing, leveraging the inherent
sparsity of the received multipath signals. Speciﬁcally, a
grid-based approximate solution is used to localize a source
over a continuous spatial region, leveraging both element-
wise and row-wise sparsity in the received signal model.
The localization process in [45] was developed for a radar
system, where the source actively transmits probing signals
and all sensing operations are performed within a single phase,
while LoS components are extracted using matched ﬁltering to
mitigate the multipath interference. Since the radar architecture
does not operate under a TDD protocol, the aforementioned
procedures are inter-coupled within one transmission stage.
In contrast, we herein design a localization algorithm for the
TDD ISAC system, which separates the estimation process
into uplink and downlink phases. During the uplink phase,
the system estimates the AoA range of the Eve, and in the
subsequent downlink phase, this information can be directly
utilized to perform precise localization.
This estimation framework effectively restricts the search
region to an area bounded by the AoA resolution, ∆θ ∈[
− πNt, πNt
]
[32] and the cell boundary. Consequently, the com-
putational workload of the localization process is signiﬁcantly
reduced, and the search area becomes progressively smaller as
the number of antennas on Tx-AP increases, thereby enhancing
localization efﬁciency and accuracy. By following [45], we
ﬁrst introduce a uniform grid of U locations
L ={π1,..., πU}, (45)
and a uniform grid of V angles for each Rx-AP array
Am ={ϑ1,...,ϑ V}∈ [0, 2π). (46)
The key assumption is that the true target lies within one of the
predeﬁned grid locations, and the AoAs of the multipaths also
correspond to the angular grid. We deﬁne a complex matrix
X∈ CU×M , whose entry on row u and column m represents
the complex gain of a reﬂected path from grid location πu
to Rx-AP m. Furthermore, let qv,m be the complex gain of
an interference path arriving at the m-th Rx-AP with the
angle ϑv. Then, by deﬁnition of compressive sensing, only
one row in X is non-zero while qv,m is non-zero only if
ϑv is equal to the AoA of an interference path at Rx-AP
m. Thus, if the grids are dense enough, X is rowsparse and
qm = [q1,m,...,q V,m]T is sparse for allm [45]. Based on this
structure, the localization problem can be cast as the following
convex optimization problem:
(P1) : min
X,qm
w‖X‖2,1 +
∑M
m=1
‖qm‖1 (47a)
s.t.
∑M
m=1
‖¯zm− ˆzm‖22≤ϵ, (47b)
¯zm =
∑U
u=1
xu,ma(θE,m(πu))
+
∑V
v=1
qv,ma(ϑv). (47c)
The optimization is a second-order cone problem and can be
directly solved in CVX. The sufﬁcient condition for the correct
recovery of the source location is
√
M− 1≤w≤
√
M.
A sufﬁciently dense spatial and angular grid is essential
to ensure that the matrices X and qm remain sparse and to
achieve high localization resolution. However, an excessively
dense grid would substantially increase the computational
complexity of the optimization problem. To balance between
resolution and complexity, we adopt an iterative grid reﬁne-
ment algorithm as in [45], which progressively reﬁnes both
the spatial and angular grids around the estimated Eve position
and AoAs.
The grid reﬁnement procedure starts by selecting initial
resolution values for the candidate location grid, denoted as
RG, and for the AoA grid, denoted as RA. These deﬁne
the coarse sampling for the initial grids L(0) and A(0)l ,
respectively. A tolerance thresholdϵ> 0 is also speciﬁed, and
the iteration index is initialized as i = 0. At each iteration, the
optimization problemP1 is solved using the current discrete
grids. From the obtained solution, the estimated location π(i)
and the AoA ϑ(i)l corresponding to the l-th indirect path are
extracted. The resolution values are then reﬁned by halving
both grid steps, i.e., R(i)G = 12R(i−1)G and R(i)A = 12R(i−1)A .
Subsequently, a new set of candidate grid points is constructed
around the current estimates, where the location estimate π(i)
is expanded to include its 24 neighboring spatial points, and
each AoA estimate is supplemented with its 5 neighboring
angular candidates based on the updated resolutions. The
iterative process continues until the convergence condition
‖π(i)− π(i−1)‖ is smaller than a predeﬁned threshold is
satisﬁed.
The direct localization problem in (47a) can be for-
mulated as a second-order cone program (SOCP). For a
ﬁxed spatial grid with U candidate locations, M Rx-APs,
and V angular grid points at each Rx-AP, the complex-
ity of solving one SOCP is on the order of O
(
(UM +
MV )3.5
)
[45]. Since the proposed method adopts iterative
grid reﬁnement, the overall localization complexity is given
by O
(∑Imax
i=1 (UiM +MVi)3.5
)
, where Imax denotes the
number of reﬁnement iterations, and Ui and Vi denote the
numbers of spatial and angular grid points at the i-th iteration,
respectively.
The current framework adopts a narrowband channel model,
where the steering vector mainly depends on angle. It is
worth noting that a larger bandwidth can improve delay
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

23496 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
resolution and help separate multi-path components, which
is beneﬁcial for direct localization. However, for ultra-wide
bandwidth and massive antenna arrays, the steering vector
becomes frequency-dependent. Under hybrid-ﬁeld propaga-
tion, the response may further depend on distance, angle, and
frequency [46].
V. P OWER ALLOCATION
To balance between communication, secrecy, and sensing
performance, an optimized power allocation (OPA) scheme is
proposed, which aims to maximize the SSE while satisfying
the following constraints: the total transmit power at the
Tx-AP, the MASR constraint κsen, the minimum quality of
service requirement at legitimate UEs κk′, and the maximum
allowable SINR at the Eve, κE. Mathematically, this can be
formulated as
(P2) : max
ηk,ηE
1
ln 2
[
ln (1 + SINR1)− ln (1 + SINRE)
]+
(48a)
s.t.
∑K
k=1
ηk
(
tr
(
Φk
)
+ ¯gHk ¯˙gk
)
≥ 0, (48b)
MASR≥κsen, (48c)
0≤
∑K
k=1
ηk
(
tr
(
Φk
)
+ ¯gHk ¯˙gk
)
+ηENt≤ 1,
(48d)
SINRE≤ SINR1, (48e)
SINRk′≥κk′,k′ ={2,...,K }, (48f)
SINRE≤κE, (48g)
where SINRk and SINRE are shown in equations (13)
and (18), respectively. To further simplify the expression, we
introduce symbol ϱν with various subscripts ν from 1 to 8 to
represent the desired signal and interference plus noise, which
are independent of the power control coefﬁcients at the Tx-AP,
as:
ϱ1 =PTx
⏐⏐⏐tr(Φk) + ¯gHk ¯˙gk⏐⏐⏐2,
ϱ2 =PTx
[
¯gHk Φk¯gk+¯˙gHk Rk¯˙gk+τpPptr(ΦkΨkR2k)
+τpPpσ2tr(RkΨ2kR2k)],
ϱ3 =PTx
[
tr(RkΦk′) + ¯˙gHk′Rk¯˙gk′ + ¯gHk Φk′ ¯gk +⏐⏐¯gHk ¯˙gk′⏐⏐2],
ϱ4 =PTxaH(ˆθTx,E)(Rk + ¯gk¯gHk)a(ˆθTx,E),
ϱ5 =PTx
⏐⏐⏐gHE (¯g1 +τp√PpPp,ER1Ψ1gE)⏐⏐⏐2,
ϱ6 =PTxgHE Φ1gE,
ϱ7 =PTxgHE
(
Φk′ + ¯˙gk′¯˙gHk′
)
gE,
ϱ8 =PTxβE
⏐⏐aH(θTx,E)a(ˆθTx,E)⏐⏐2. (49)
We now deﬁne a vector η = [η1,η 2,...,η K], and due to
constraint (48e), [·]+ in the objective function of (P2) can be
removed, and hence, (P2) can be then reformulated into
(P2.1) : max
ηk,ηE
ln
(
1 + ϖ1(η1)ϖ2(η,η E))− ln(1 + ϖ3(η1)ϖ4(η,η E))
s.t. (48b)− (48g), (50a)
where ϖ1(η1) = η1ϱ1, ϖ2(η,η E) = ηkϱ2 +∑Kk′⁄=kηk′ϱ3 +
ηEϱ4 + σ2, ϖ3(η1) = η1ϱ5 and ϖ4(η,η E) = ηkϱ6 +∑K
k′⁄=kηk′ϱ7 +ηEϱ8 +σ2. The constraints in (48f) and (48g)
can be reformulated into
ηk′ϱ1≥κk′ϖ2(η,η E), (51)
ϖ3(η1)≤κEϖ4(η,η E). (52)
This optimization is difﬁcult to solve since the objective
function is not jointly concave with respect to ηk and ηE.
To address this problem, we use the following Lemma
from [47].
Lemma 1: Consider the function ϕ(t) =−tx+lnt+1. The
following equality holds for any x> 0,
− lnx = max
t>0
ϕ(t), (53)
and the optimal solution is t = 1x.
By applying Lemma 1, setting x =ϖ2(η,η E) and t =t1,
the ﬁrst term in the objective function (50a) can be further
reformulated as
ln
(
ϖ1(η1) +ϖ2(η,η E)
)
− ln
(
ϖ2(η,η E)
)
= max
t1>0
ϕk(ηk,η E,t 1), (54)
where ϕ1(ηk,η E,t 1) = ln
(
ϖ1(η1) +ϖ2(η,η E)
)
−
t1ϖ2(η,η E) + lnt1 + 1. Similarly, we can reformulate the
second term in the objective function (50a) by setting x =(
ϖ3(η1) +ϖ4(η,η E)
)
and t =tE as
ln
(
ϖ3(η1) +ϖ4(η,η E)
)
− ln
(
ϖ4(η,η E)
)
= min
tE>0
ϕE(ηk,η E,t E), (55)
where ϕE(ηk,η E,t E) = tE
(
ϖ3(η1) + ϖ4(η,η E)
)
−
ln
(
ϖ4(η,η E)
)
− ln (tE)− 1. Invoking (54) and (55), the
optimization problem can be reformulated into
(P2.2) : max
ηk,ηE,t1,tE
ϕ1(ηk,η E,t 1)−ϕE(ηk,η E,t E) (56a)
s.t. t1 > 0,t E > 0,
(48b)− (48e), (51), (52). (56b)
It is shown that the objective function is convex either on
(ηk,η E) or (t1,t E) and we know that given a ﬁxed(ηk,η E) the
optimal solution is t∗1 = 1/ϖ2(η,η E) and t∗E = 1/(ϖ3(η1) +
ϖ4(η,η E)
)
. For a given (t∗1,t∗E), we can now solve the
problem below to obtain η1 and ηE:
(P2.3) : max
ηk,ηE
ϕ1(ηk,η E,t∗1)−ϕE(ηk,η E,t∗E)
s.t. (48b)− (48e), (51), (52), (56b). (57a)
For solving this problem, we introduce a slack variable t and
reformulate the objective function as
(P2.4) : max
ηk,ηE,t
ϕ1(ηk,η E,t∗1)−t (58a)
s.t. ϕE(ηk,η E,t∗E)≤t,
(48b)− (48e), (51), (52), (56b). (58b)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

W ANG et al.: FROM SENSING TO SECRECY: ACTIVE EA VESDROPPER LOCALIZATION IN MASSIVE MIMO ISAC 23497
Algorithm 1 Alternating Optimization for Solving (P2)
Fig. 3. Convergence of Algorithm 1, for κ = 3 dB,K = 5,κsens = 5 dB,
tolerance ϵ = 10 −4 and r = 10 m.
The problemP2.4 can be solved using an alternating opti-
mization and path-following algorithm shown in Algorithm 1.
We note that the complexity of Algorithm 1 arises from
updating (t1,t E) and (ηk,η E). The computational complexity
of updating (t1,t E) is O(K + 1), while that of updating
(ηk,η E) isO
(
(K + 1)3). By denoting the iteration number
of inner and outer loop by I1 and I2, the total complexity
isO
(
I1I2((K + 1))3). The convergence of Algorithm 1 is
shown in Fig. 3. We can see that the algorithm converges
quickly, within just a few iterations.
VI. N UMERICAL RESULTS
In this section, we evaluate the security performance of the
considered mMIMO ISAC localization system and analyze
the impact of key system parameters. We consider a single
mMIMO Tx-AP, four Rx-APs for sensing, K legitimate UEs,
and one Eve. The UEs are randomly distributed within a
400×400 m2 area, while the Eve is placed randomly within a
circle of radius r centered at UE 1. The Tx-AP is positioned
at [−200, 0], and the four Rx-APs are symmetrically located
at the corners [±200,±200]. Each Rx-AP is equipped with
a uniform linear array (ULA) of Nr antennas, while the
distance between any two adjacent antennas is ∆d. For the
equal power allocation (EPA) scheme, the power coefﬁcients
TABLE II
SIMULATION PARAMETERS
are deﬁned as ηk = 0.5 PTx/∑Kk=1(tr(Φk) + ¯gHk ¯˙gk) and
ηE = 0.5 PTx/Nt, ensuring that the total transmit power
constraints are satisﬁed.
To benchmark the direct localization approach, a conven-
tional two-stage localization scheme is adopted. To begin with,
the AoAs are estimated at each Rx-AP by computing the
spatial spectrum and then determining the local maxima [48].
The process is similar to mechanically steering the array in
multiple directions and measuring the output power, and the
direction with the highest power is the estimated AoA. The
estimated AoAs at each m-th Rx-AP are then incorporated
into a linear least squares (LLS) framework to determine the
target’s position, following the approach in [38].
1) Analysis of closed-form downlink SINR : We ﬁrst consider
that the Tx-AP employs an EPA scheme in downlink transmis-
sion. To verify the accuracy of the closed-form expressions
presented in Section III-A, we plot their cumulative distribu-
tion functions (CDFs) and compare them with results obtained
through Monte-Carlo simulations, averaged over 1, 000 ran-
dom channel realizations. The simulation results in Fig. 4 lead
to the following observations:
• The analytical results (solid and dashed curves) closely
match the simulation results (markers), conﬁrming the
correctness of the derived closed-form expressions.
• Increasing the number of antennas at the Tx-AP
improves the SSE by simultaneously increasing
SINR1 and reducing SINRE. This improvement
arises for two main reasons. First, a larger
antenna array provides higher array gain, which
strengthens the desired signal received by UE 1.
Second, the narrower beams enhance spatial selectivity,
concentrating the transmitted power toward the intended
direction while reducing signal leakage toward the Eve.
• When the Eve moves closer to UE 1, the secrecy per-
formance degrades, with SINRE increasing and SINR1
decreasing simultaneously. This occurs since the Ricean
factor renders the channel highly directional, caus-
ing the precoding to concentrate most of the energy
toward the UE’s spatial direction. If the Eve is spa-
tially separated from UE 1, the steering vectors become
nearly orthogonal with large Nt. However, spatial
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

23498 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 4. CDF of key SINR metrics, for PTx = 3 W , κ = 3 dB and
σ2 = −40 dBm.
Fig. 5. PEB performance vs. noise variance, for PTx = 1 W.
proximity can compromise this orthogonality, resulting in
reduced SSE.
2) Analysis of PEB : Figure 5 compares the PEB as a
function of noise variance for different numbers of Rx-APs,
number of antennas on the Tx-AP and Rx-AP. In this case
study, we further deploy four additional Rx-APs located at
[±100,±100]. First, for any ﬁxed noise level, conﬁgurations
with a larger number of Rx-APs consistently achieve a lower
PEB. For instance, when the number of Rx-APs increases from
M = 4 toM = 8, the PEB is reduced by approximately 72%
across the entire range when Nt = 64 . This improvement
arises because additional Rx-APs provide independent geo-
metric measurements, and thus enhance the Fisher information
by improving its rank and conditioning. Second, increasing
the number of antennas at either the Rx-APs or the Tx-AP
also improves localization accuracy due to the increased array
gain. In particular, a larger Tx-AP array yields a narrower
sensing beam and higher directional gain toward the target,
which strengthens the received echoes and improves estima-
tion accuracy. By comparing the cases (M = 4, Nr = 8) and
(M = 8, Nr = 4), we observe that deploying more spatially
separated Rx-APs is more effective than merely increasing the
number of antennas per Rx-AP. This is because the PEB is
fundamentally constrained by geometric diversity: increasing
M improves the conditioning of the Jacobian matrix, whereas
Fig. 6. Localization performance vs the noise power in DP-only case, for
κ = 3 dB and Nr = 8.
Fig. 7. CDF of the RMSE under different scattering conditions, for
κ = 3 dB, Nt = 128 and σ2 = −30 dBm.
increasingNr primarily scales up the FIM without altering its
structure.
3) Analysis of two localization algorithms : Figure 6 com-
pares the localization RMSE of the proposed scheme and the
conventional two-step estimator with the corresponding PEB
under a pure LoS scenario. We observe that the proposed
method consistently achieves an RMSE closer to the PEB than
the two-step algorithm over the entire noise power range. This
is because the two-step approach is affected by AoA estimation
errors caused by peak ambiguities. Although in a pure LoS
scenario the AoA of the Eve can be estimated relatively
accurately, the two-step method still exhibits an error ﬂoor due
to the limited angular resolution of the AoA estimator in its
ﬁrst stage and the information loss between the two estimation
steps. In contrast, the proposed direct localization approach
mitigates this resolution limitation by jointly exploiting the
received signals.
4) Impact of multipaths : Figure 7 illustrates the CDF of
the localization RMSE for the proposed scheme and the
conventional two-step algorithm under multipath conditions.
In the absence of scatterers, both methods achieve relatively
low localization error. However, as the number of scatter-
ers increases, the performance degradation of the two-step
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

W ANG et al.: FROM SENSING TO SECRECY: ACTIVE EA VESDROPPER LOCALIZATION IN MASSIVE MIMO ISAC 23499
Fig. 8. SSE vs. the number of antennas at Tx-AP, for κsen = 5 dB,
κ = 3 dB and σ2 = −30 dBm.
estimator becomes signiﬁcant. This is because multipath
reﬂections may dominate the received power at certain
Rx-APs, causing the AoA estimator to mistakenly identify
an IDP as the DP. These erroneous AoA estimates then
propagate to the subsequent LLS stage, resulting in large
RMSE values. In contrast, the proposed scheme demonstrates
strong robustness against multipath effects. Although its per-
formance also degrades as the number of scatterers increases,
the corresponding CDF curves remain much closer to the
no-scatterer case. This robustness stems from the fact that
the proposed scheme does not rely on identifying a single
dominant AoA; instead, it exploits the joint sparsity structure
of the received signals across multiple Rx-APs and directly
estimates the target location in a single step without extracting
intermediate parameters.
5) Impact of optimization : Figure 8 compares the average
SSE achieved by the EPA scheme and the proposed OPA
scheme versus the number of transmit antennas under different
transmit power levels. First, we observe that increasing the
number of antennas consistently improves the average SSE
due to the enhanced array gain provided by mMIMO. Second,
reducing the distance between the Eve and UE 1 signiﬁcantly
degrades the SSE performance. For example, when the dis-
tance range decreases from r = 50 m to r = 10 m, the SSE is
reduced by approximately 55.6% at PTx = 1 W. This degra-
dation arises from two factors. On one hand, the legitimate
UE experiences stronger sensing-induced interference, leading
to a reduction in SINRk. On the other hand, a closer Eve
avails of more effective pilot spooﬁng and increased downlink
reception strength, thereby increasing SINRE. Moreover, the
results demonstrate that the proposed OPA scheme consis-
tently outperforms the EPA scheme across all values of PTx
andr. The performance gap becomes more pronounced as the
transmit power and the number of antennas increase. Notably,
for the scenario with r = 50 m, PTx = 3 W, and Nt = 128,
the OPA scheme achieves an SSE improvement of more than
59.1% compared with the EPA scheme.
Finally, Fig. 9 illustrates the average SSE as a function of
the MASR constraint κsen under different values of Nt and
transmit power PTx. First, increasing the sensing constraint
leads to a monotonic decrease in the SSE achieved by the OPA
Fig. 9. SSE vs. κsen, for κ = 3 dB and σ2 = −30 dBm.
scheme. This behavior arises since a larger MASR requirement
forces the transmitter to allocate more power toward the
sensing beam to guarantee sensing performance. Consequently,
less power is available for downlink communication, which
reduces SINRk and ultimately degrades the SSE. For relatively
loose sensing constraints, i.e., κsen in the range of −5 dB to
0 dB, the OPA scheme remains stable and maintains a favor-
able balance between communication and sensing. However,
when κsen≥ 5 dB, the SSE drops rapidly for all conﬁgura-
tions. In particular, atκsen = 15 dB, the OPA scheme achieves
almost no SSE improvement for the case Nt = 64 and
PTx = 1 W, indicating that an overly stringent sensing con-
straint can severely undermine communication performance.
These results highlight the importance of carefully selecting
the MASR constraint to achieve an effective trade-off between
sensing accuracy and secrecy performance.
VII. C ONCLUSION
This paper proposed a secure mMIMO ISAC framework
that integrates uplink AoA estimation with downlink direct
localization to determine the position of an active Eve in mul-
tipath environments. Closed-form expressions were derived
for the downlink SSE and the PEB. An optimized power
allocation problem was further formulated to enhance secure
communication performance while satisfying sensing con-
straints. Numerical results demonstrated that the proposed
scheme achieves accurate localization in multipath scenarios,
while the OPA scheme signiﬁcantly improves the robustness
of secrecy performance compared with the conventional EPA.
Furthermore, the results highlighted the critical role of the
MASR constraint and its impact on the achievable SSE,
emphasizing the importance of balancing sensing requirements
with secure communication performance.
APPENDIX A
PROOF OF PROPOSITION 1
1) Compute E{DSk}:
E{DSk}= E
{√
ηkPTx(¯gHk +˜gHk )(¯˙gk+τpPpRkΨk˜gk)}
=
√
ηkPTx
(
tr
(
Φk
)
+ ¯gHk ¯˙gk
)
. (59)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

23500 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
2) For calculating E
{
|BUk|2}, we ﬁrst calculate
E
{
|DSk|2}:
E
{
|DSk|2} =ηkPTxE{|gHk ˆgk|2}. (60)
Hereby, we expand the E
{
|gHk ˆgk|2} and obtain
E
{
|gHk ˆgk|2} = E{⏐⏐⏐(¯gHk +˜gHk)(¯˙gk+√τpPpRkΨk
×
(√
τpPp˜gk+Npϕk
))⏐⏐⏐2}
=
⏐⏐¯gHk ¯˙gk⏐⏐2+¯gHk Φk¯gk + ¯˙gHk Rk¯˙gk +⏐⏐tr(Φk)⏐⏐2
+τpPptr(ΦkΨkR2k) +τpPpσ2tr(RkΨ2kR2k)
+ 2tr
(
Φk
)
Re
{¯gHk ¯˙gk}. (61)
Combining (60) and (59), we can obtain
E
{
|BUk|2}
= E
{
|DSk|2}−| E{DSk}| 2
=ηkPTx
[
¯gHk Φk¯gk + ¯˙gHk Rk¯˙gk+τpPptr(ΦkΨkR2k)
+τpPpσ2tr(RkΨ2kR2k)]. (62)
3) Compute E
{
|IUIk′,k|2}: Since the channel of the k-th
UE and the channel estimation of the k′-th UE ˆgk′, where
k′⁄= k are uncorrelated, and using [49, Lemma 4], we can
derive
E
{
|IUIk′,k|2}=PTxηk′E{|gHk ˆgk′|2}
=PTxηk′
[
tr(RkΦk′) + ¯˙gHk′Rk¯˙gk′ + ¯gHk Φk′ ¯gk
+
⏐⏐¯gHk ¯˙gk′⏐⏐2]. (63)
4) Compute E
{
|SIk|2}:
E
{
|SIk|2}=PTxηEE{|gHk wE|2}
=PTxηEaH(ˆθTx,E)(Rk + ¯gk¯gHk)a(ˆθTx,E). (64)
APPENDIX B
PROOF OF PROPOSITION 2
1) Compute E{DSE}: By leveraging the independence
between ˜g1 and gE, we can obtain
E{DSE} = E
{√
η1PTxgHE ˆg1
}
=
√
η1PTxgHE
(
¯g1 +τp
√
PpPp,ER1Ψ1gE
)
.
(65)
2) Compute E
{
|BUE|2}: We ﬁrst calculate
E
{
|DSE|2}. Invoking ˆg1 = ¯g1 +τp√PpPp,ER1Ψ1gE +√
τpPpR1Ψ1(
√
τpPp˜g1+Npϕ1), we can deduce
gHE ˆg1 = gHE ¯g1+τp√PpPp,EgHE R1Ψ1gE
+
√
τpPpgHE R1Ψ1(√τpPp˜g1+Npϕ1). (66)
Moreover, E
{
|DSE|2} can be calculated as
E
{
|DSE|2} =η1PTx(⏐⏐gHE ¯g1+τp√PpPp,EgHE R1Ψ1gE⏐⏐2
+ gHE Φ1gE
)
. (67)
Combining (67) and (65), we can obtain
E
{
|BUE|2} = E{|DSE|2}−| E{DSE}| 2 =η1PTxgHE Φ1gE.
(68)
3) Compute E
{
|IUIE,k′|2}: Since ˆgk′ is independent of gE,
we can derive
E
{
|IUIE,k′|2} =PTxηk′E{|gHE ˆgk′|2}
=PTxηk′gHE
(
Φk′ + ¯˙gk′¯˙gHk′
)
gE. (69)
4) Compute E
{
|SIE|2}:
E
{
|SIE|2}=PTxηEE{|gHE wE|2}
=PTxηEβE
⏐⏐aH(θTx,E)a(ˆθTx,E)⏐⏐2. (70)
APPENDIX C
PROOF OF PROPOSITION 3
Following the formula Ψm(xr, xs) ≜
Eym|ψm
[
−∂2 lnf (ym|ψm)∂xr∂xTs ], the 3 × 3 matrix Ψm
(ψm,r,ψm,s), can be derived as follows:
Ψm(ψm,r,ψm,s) =
[
Ψm(θm,r,θm,s) Ψ m(θm,r, ˜αm,s)
Ψm(˜αm,r,θm,s) Ψm(˜αm,r, ˜αm,s)
]
.
(71)
Now, we derive the elements in (28), and the second
derivative by invoking (26) can be calculated as
∂2 lnf(ym|ψm)
∂θm,r∂θm,s
= 2σ2 Re{( ∂2µm∂θm,r∂θm,s)H (ym−µm)
−
(∂µm
∂θm,r
)H(∂µm
∂θm,s
)}
. (72)
Considering the fact that Eym|ψm{ym − µm} =
Eym|ψm{nm} = 0, and invoking (24), we ﬁrst derive
Ψm(θm,r,θm,s)
= 2σ2 Re{∂µHm∂θm,r ∂µm∂θm,s}
= 2G2antηEPTx
σ2 Re
{
˜α∗m,r ˜αm,sAθθ(θm,r,θm,s)}, (73)
whereAθθ(θm,r,θm,s) = aHθ (θm,r)aθ(θm,s). The ﬁrst deriva-
tive of [a(θm,l)]n denoted by
[
aθ(θm,l)
]
n is
[
aθ(θm,l)
]
n =−j2π ∆dλ (n− 1) sin(θm,l)ejπ(n−1) cos(θm,l).(74)
Thus, the term Aθθ(θm,r,θm,s) can be written as
Aθθ(θm,r,θm,s)
=
(
2π ∆dλ )2 sin(θm,r) sin(θm,s)∑Nrn=1(n−1)2
× exp
[
j2π ∆dλ (n− 1)( cos(θm,s)− cos(θm,r))]. (75)
The remaining terms in (28) can be derived by following
the same procedure used for (73), while the results are shown
in (29). In particular, Aθ(θm,r,θm,s) = aHθ (θm,r)a(θm,s)
and A(θm,r,θm,s) = aH(θm,r)a(θm,s) can be obtained by
combining (74) and (25). This completes the proof.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

W ANG et al.: FROM SENSING TO SECRECY: ACTIVE EA VESDROPPER LOCALIZATION IN MASSIVE MIMO ISAC 23501
REFERENCES
[1] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[2] F. Liu, C. Masouros, A. Li, H. Sun, and L. Hanzo, “MU-MIMO commu-
nications with MIMO radar: From co-existence to joint transmission,”
IEEE Trans. Wireless Commun. , vol. 17, no. 4, pp. 2755–2770, Apr.
2018.
[3] M. Mohammadi, Z. Mobini, H. Q. Ngo, and M. Matthaiou, “Ten
years of research advances in full-duplex massive MIMO,” IEEE Trans.
Commun., vol. 73, no. 3, pp. 1756–1786, Mar. 2025.
[4] B. Liao, H. Q. Ngo, M. Matthaiou, and P. J. Smith, “Power allocation
for massive MIMO-ISAC systems,” IEEE Trans. Wireless Commun. ,
vol. 23, no. 10, pp. 14232–14248, Oct. 2024.
[5] N. T. Nguyen, V .-D. Nguyen, H. V . Nguyen, H. Q. Ngo, A. L. Swindle-
hurst, and M. Juntti, “Performance analysis and power allocation for
massive MIMO ISAC systems,” IEEE Trans. Signal Process. , vol. 73,
pp. 1691–1707, 2025.
[6] J. Chen, X. Chen, W. H. Gerstacker, and D. W. K. Ng, “Resource
allocation for a massive MIMO relay aided secure communication,”
IEEE Trans. Inf. F orensics Security, vol. 11, no. 8, pp. 1700–1711, Aug.
2016.
[7] D. Kapetanovic, G. Zheng, and F. Rusek, “Physical layer security for
massive MIMO: An overview on passive eavesdropping and active
attacks,” IEEE Commun. Mag. , vol. 53, no. 6, pp. 21–27, Jun. 2015.
[8] Q. Wang, K. Xu, and K. Ren, “Cooperative secret key generation from
phase estimation in narrowband fading channels,” IEEE J. Sel. Areas
Commun., vol. 30, no. 9, pp. 1666–1674, Oct. 2012.
[9] Y . Wu, R. Schober, D. W. K. Ng, C. Xiao, and G. Caire, “Secure
massive MIMO transmission with an active eavesdropper,” IEEE Trans.
Inf. Theory , vol. 62, no. 7, pp. 3880–3900, Jul. 2016.
[10] Z. Mobini, M. Mohammadi, and C. Tellambura, “Wireless-powered
full-duplex relay and friendly jamming for secure cooperative
communications,” IEEE Trans. Inf. F orensics Security , vol. 14, no. 3,
pp. 621–634, Mar. 2019.
[11] X. Zhou, B. Maham, and A. Hjorungnes, “Pilot contamination for
active eavesdropping,” IEEE Trans. Wireless Commun. , vol. 11, no. 3,
pp. 903–907, Mar. 2012.
[12] Y . S. Atiya, Z. Mobini, H. Q. Ngo, and M. Matthaiou, “Secure
transmission in cell-free massive MIMO under active eavesdropping,”
IEEE Trans. Wireless Commun., vol. 23, no. 12, pp. 18036–18052, Dec.
2024.
[13] Z. Mobini, H. Q. Ngo, M. Matthaiou, and L. Hanzo, “Cell-free massive
MIMO surveillance of multiple untrusted communication links,” IEEE
Internet Things J. , vol. 11, no. 20, pp. 33010–33026, Oct. 2024.
[14] Y . Li, R. Zhao, Y . Deng, F. Shu, Z. Nie, and A. H. Aghvami,
“Harvest-and-opportunistically-relay: Analyses on transmission outage
and covertness,” IEEE Trans. Wireless Commun. , vol. 19, no. 12,
pp. 7779–7795, Dec. 2020.
[15] M. Huang, F. Gong, G. Li, N. Zhang, and Q.-V . Pham, “Secure precoding
for satellite NOMA-aided integrated sensing and communication,” IEEE
Internet Things J. , vol. 11, no. 18, pp. 29533–29545, Sep. 2024.
[16] Z. Ren, L. Qiu, J. Xu, and D. W. K. Ng, “Robust transmit beamforming
for secure integrated sensing and communication,” IEEE Trans. Com-
mun., vol. 71, no. 9, pp. 5549–5564, Sep. 2023.
[17] G. Li, C. Wang, H. Zhang, L. Jin, and N. Al-Dhahir, “Securing ISAC
against pilot spooﬁng attack: A deep plug-and-play countermeasure,”
IEEE Wireless Commun. Lett., vol. 14, no. 9, pp. 2813–2817, Sep. 2025.
[18] N. Su, F. Liu, and C. Masouros, “Sensing-assisted eavesdropper esti-
mation: An ISAC breakthrough in physical layer security,” IEEE Trans.
Wireless Commun., vol. 23, no. 4, pp. 3162–3174, Apr. 2024.
[19] Y . Cao, L. Duan, and R. Zhang, “Sensing for secure communication
in ISAC: Protocol design and beamforming optimization,” IEEE Trans.
Wireless Commun., vol. 24, no. 2, pp. 1207–1220, Feb. 2025.
[20] H. Guo et al., “Integrated communication, localization, and sensing
in 6G D-MIMO networks,” IEEE Wireless Commun. , vol. 32, no. 2,
pp. 214–221, Apr. 2025.
[21] J. He, H. Q. Ngo, H. Yu, H. Huang, H. Wymeersch, and M. Matthaiou,
“MmWave integrated localization, mapping, and communication: A
stochastic geometry perspective,” in Proc. IEEE Global Commun. Conf.
(GLOBECOM), Dec. 2025, pp. 1–6.
[22] Z. Wang, Z. Mobini, H. Q. Ngo, H. Shin, and M. Matthaiou, “Anti-
malicious ISAC: How to jointly monitor and disrupt your foes?” IEEE
Trans. Wireless Commun. , vol. 25, pp. 10514–10529, 2026.
[23] D. Wu and Y . Zeng, “Secure communication and eavesdropper localiza-
tion via channel knowledge map,” in Proc. IEEE 101st V eh. Technol.
Conf. (VTC-Spring) , Jun. 2025, pp. 1–5.
[24] Q. Shi, L. Liu, S. Zhang, and S. Cui, “Device-free sensing in
OFDM cellular network,” IEEE J. Sel. Areas Commun. , vol. 40, no. 6,
pp. 1838–1853, Jun. 2022.
[25] Z. Zhang et al., “Target localization in cooperative ISAC systems:
A scheme based on 5G NR OFDM signals,” IEEE Trans. Commun. ,
vol. 73, no. 5, pp. 3562–3578, May 2025.
[26] Z. Mobini, M. Mohammadi, J. He, H. Q. Ngo, and M. Matthaiou,
“Cell-free massive MIMO-assisted ISAC with beam scanning,” in Proc.
IEEE 26th Int. Workshop Signal Process. Artif. Intell. Wireless Commun.
(SPA WC), Jul. 2025, pp. 1–5.
[27] H. Yu, H. Q. Ngo, J. He, and M. Matthaiou, “Multi-target localization
and association in cell-free massive MIMO for multi-static isac,” in
Proc. IEEE Int. Conf. Commun. (ICC) , Jun. 2025, pp. 6663–6668.
[28] H. Zhao, N. Zhang, and Y . Shen, “Beamspace direct localization for
large-scale antenna array systems,” IEEE Trans. Signal Process., vol. 68,
pp. 3529–3544, 2020.
[29] G. Zhang, W. Yi, M. Matthaiou, and P. K. Varshney, “Direct target
localization with low-bit quantization in wireless sensor networks,”
IEEE Trans. Signal Process. , vol. 72, pp. 3059–3075, 2024.
[30] Y . Tao, X. Wang, B. Li, and C. Zhao, “Pilot spooﬁng attack detection and
localization with mobile eavesdropper,” IEEE Trans. Mobile Comput. ,
vol. 22, no. 3, pp. 1688–1701, Mar. 2023.
[31] H. Q. Ngo, A. Ashikhmin, H. Yang, E. G. Larsson, and T. L. Marzetta,
“Cell-free massive MIMO versus small cells,” IEEE Trans. Wireless
Commun., vol. 16, no. 3, pp. 1834–1850, Mar. 2017.
[32] M. Zhang, C. Liao, K. Xu, W. Xie, J. Xu, and L. Chen, “Angle-domain
channel and DOA estimation in airborne massive MIMO system with
eavesdropper,” in Proc. 28th Wireless Opt. Commun. Conf. (WOCC) ,
May 2019, pp. 1–6.
[33] Y . Li and A. S. Madhukumar, “Hybrid near- and far-ﬁeld THz
UM-MIMO channel estimation: A sparsifying matrix learning-aided
Bayesian approach,” IEEE Trans. Wireless Commun. , vol. 24, no. 3,
pp. 1881–1897, Mar. 2025.
[34] N. Garcia, A. M. Haimovich, J. A. Dabin, M. Coulon, and M. Lops,
“Direct localization of emitters using widely spaced sensors in multipath
environments,” in Proc. 48th Asilomar Conf. Signals, Syst. Comput. ,
Nov. 2014, pp. 695–700.
[35] B. Hu, H. Tian, W. Ni, S. Fan, W. Ni, and E. Hossain, “Multipath
identiﬁcation, user localization, and environment mapping in radio
SLAM,” IEEE Trans. Commun. , vol. 72, no. 10, pp. 6457–6473, Oct.
2024.
[36] J. Shen and A. F. Molisch, “Estimating multiple target locations in multi-
path environments,” IEEE Trans. Wireless Commun. , vol. 13, no. 8,
pp. 4547–4559, Aug. 2014.
[37] J. He et al., “RSS localization in cell-free massive MIMO: Algorithms,
analysis, and implementation,” IEEE Trans. Wireless Commun. , vol. 25,
pp. 4021–4037, 2026.
[38] Z. Reza and B. R. Michael, ’Fundamentals of Position Location’ in
Handbook of Position Location: Theory, Practice, and Advances . Wiley,
2019. [Online]. Available: https://onlinelibrary.wiley.com/doi/abs/
10.1002/9781119434610.ch3
[39] A. Fascista et al., “Uplink joint positioning and synchronization in cell-
free deployments with radio stripes,” in Proc. IEEE Int. Conf. Commun.
Workshops (ICC Workshops), May 2023, pp. 1330–1336.
[40] H. Q. Ngo, E. G. Larsson, and T. L. Marzetta, “Aspects of favorable
propagation in massive MIMO,” in Proc. 22nd Eur . Signal Process.
Conf. (EUSIPCO) , Sep. 2014, pp. 76–80.
[41] M. Di Renzo, “Stochastic geometry modeling and analysis of multi-tier
millimeter wave cellular networks,” IEEE Trans. Wireless Commun. ,
vol. 14, no. 9, pp. 5038–5057, Sep. 2015.
[42] H. Q. Ngo, L.-N. Tran, T. Q. Duong, M. Matthaiou, and E. G. Lars-
son, “On the total energy efﬁciency of cell-free massive MIMO,”
IEEE Trans. Green Commun. Netw. , vol. 2, no. 1, pp. 25–39,
Mar. 2018.
[43] P. Yin et al., “AutoCali: Enhancing AoA-based indoor localization
through automatic phase calibration,” in Proc. IEEE Int. Conf. Acoust.,
Speech Signal Process. (ICASSP) , Apr. 2024, pp. 9046–9050.
[44] M. Elﬁatoure, M. Mohammadi, H. Q. Ngo, H. Shin, and M. Matthaiou,
“Multiple-target detection in cell-free massive MIMO-assisted ISAC,”
IEEE Trans. Wireless Commun. , vol. 24, no. 5, pp. 4283–4298, May
2025.
[45] N. Garcia, H. Wymeersch, E. G. Larsson, A. M. Haimovich, and
M. Coulon, “Direct localization for massive MIMO,” IEEE Trans. Signal
Process., vol. 65, no. 10, pp. 2475–2487, May 2017.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

23502 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[46] Y . Li, A. S. Madhukumar, Z. Chu, G. Zheng, C.-X. Wang, and K. Yang,
“Wideband hybrid-ﬁeld THz UM-MIMO channel estimation: A dual-
attention-aided deep-unfolded Bayesian learning approach,” IEEE Trans.
Commun., vol. 74, pp. 6523–6540, 2026.
[47] X. Guan, Q. Wu, and R. Zhang, “Intelligent reﬂecting surface assisted
secrecy communication: Is artiﬁcial noise helpful or not?” IEEE Wireless
Commun. Lett. , vol. 9, no. 6, pp. 778–782, Jun. 2020.
[48] H. C. So, ’Source Localization: Algorithms and Analysis’ in Hand-
book of Position Location: Theory, Practice, and Advances . Wiley,
2019, pp. 59–106. [Online]. Available: https://onlinelibrary.wiley.com/
doi/book/10.1002/9781119434610
[49] ¨O. ¨Ozdogan, E. Bj ¨ornson, and E. G. Larsson, “Massive MIMO with
spatially correlated Rician fading channels,” IEEE Trans. Commun. ,
vol. 67, no. 5, pp. 3234–3250, May 2019.
Zonghan Wang (Member, IEEE) received the B.S.
degree in electronic and information engineering
from Nanjing University of Science and Technology,
China, in 2021, and the M.S. degree in communi-
cation systems from Lund University, Sweden, in
2023. He is currently pursuing the Ph.D. degree
with the Centre for Wireless Innovation (CWI),
Queen’s University, Belfast, U.K. His main research
interests include massive MIMO, integrated sensing
and communications, physical-layer security, and
reinforcement learning.
Jiajun He (Member, IEEE) was born in Guangzhou,
China. He received the Ph.D. degree from the
City University of Hong Kong, Hong Kong,
SAR, China, in 2024. Since June 2024, he has
been a Research Fellow with Queen’s University
Belfast, Belfast, U.K. His research interests include
source localization, radar signal processing, cell-
free massive MIMO, embedded system design, and
machine learning. He was a recipient of the Marie
Curie Postdoctoral Fellowship from European Union
in 2025.
Zahra Mobini (Senior Member, IEEE) received
the Ph.D. degree from K. N. Toosi University of
Technology, Tehran, Iran. She was a Post-Doctoral
Research Fellow with Queen’s University Belfast,
U.K., from 2021 to 2025. From November 2010
to 2011, she was a Visiting Researcher with the
School of Engineering, The Australian National Uni-
versity (ANU), Canberra, Australia. She is currently
an Assistant Professor in communications engineer-
ing and signal processing with The University of
Manchester, U.K. She has co-authored numerous
research articles in wireless communications. Her research interests include
physical-layer security, cell-free massive MIMO, integrated sensing and
communications (ISAC), reconﬁgurable intelligent surfaces, and resource
management and optimization. She has served as a Technical Program
Committee Member for prominent IEEE conferences, such as ICC, GLOBE-
COM, and VTC. She received the Commendation in the 2025 Postdoctoral
Support Award from Queen’s University Belfast. She serves as an Editor for
IEEE T RANSACTIONS ON COMMUNICATIONS and Physical Communication
(Elsevier); and as the Educational Services Coordinator for IEEE S IGNAL
PROCESSING AND COMMUNICATIONS ELECTRONICS (SPCC) Technical
Committee.
Hien Quoc Ngo (Fellow, IEEE) is currently a
Professor with Queen’s University Belfast, U.K.
He is also an Eminent Scholar with Kyung Hee
University, Republic of Korea. He has co-authored
many research articles in wireless communications
and co-authored textbook Fundamentals of Mas-
sive MIMO (Cambridge University Press, 2016).
His main research interests include cellular/cell-
free massive MIMO systems, integrated sensing and
communications, reconﬁgurable intelligent surfaces,
and physical layer security.
Dr. Ngo received the IEEE ComSoc Test of Time Paper Award for Advances
in Communications in 2026, the IEEE ComSoc Stephen O. Rice Prize in
2015, the IEEE ComSoc Leonard G. Abraham Prize in 2017, the Best Ph.D.
Award from EURASIP in 2018, and the IEEE CTTC Early Achievement
Award in 2023. He also received the IEEE Sweden VT-COM-IT Joint Chapter
Best Student Journal Paper Award in 2015. He was awarded the UKRI
Future Leaders Fellowship in 2019. He was an Editor of IEEE W IRELESS
COMMUNICATIONS LETTERS , a Guest Editor of IET Communications , and
a Guest Editor of IEEE A CCESS in 2017. He serves as an Editor for IEEE
TRANSACTIONS ON WIRELESS COMMUNICATIONS , IEEE T RANSACTIONS
ON COMMUNICATIONS , Digital Signal Processing , and Physical Communi-
cation (Elsevier).
Hyundong Shin (Fellow, IEEE) received the B.S.
degree in electronics engineering from Kyung Hee
University (KHU), Yongin-si, South Korea, in 1999,
and the M.S. and Ph.D. degrees in electrical engi-
neering from Seoul National University, Seoul,
South Korea, in 2001 and 2004, respectively. He
was a Post-Doctoral Researcher with the Labo-
ratory for Information Decision Systems (LIDS),
Massachusetts Institute of Technology (MIT), from
2004 to 2006. In 2006, he joined KHU, where he
is currently a Professor with the Department of
Electronic Engineering. His research interests include quantum information
science, wireless communications, and machine intelligence. He received the
IEEE Communications Society’s Guglielmo Marconi Prize Paper Award and
the William R. Bennett Prize Paper Award. He served as the Publicity Co-
Chair for IEEE PIMRC and the Technical Program Co-Chair for IEEE WCNC
and IEEE GLOBECOM. He was an Editor of IEEE T RANSACTIONS ON
WIRELESS COMMUNICATIONS and IEEE C OMMUNICATIONS LETTERS .
Michail Matthaiou (Fellow, IEEE) received the
Ph.D. degree from The University of Edinburgh,
U.K., in 2008.
He is currently a Professor of communications
engineering and signal processing and the Deputy
Director of the Centre for Wireless Innovation
(CWI), Queen’s University Belfast, U.K. He is also
an Eminent Scholar with Kyung Hee University,
Republic of Korea. He has held research/faculty
positions with Munich University of Technology
(TUM), Germany; and the Chalmers University of
Technology, Sweden. His research interests span signal processing for wireless
communications, beyond massive MIMO, reﬂecting intelligent surfaces, mm-
wave/THz systems, and AI-empowered communications. He is an AAIA
Fellow. He and his co-authors received the IEEE Communications Society
(ComSoc) Leonard G. Abraham Prize in 2017. He currently holds the ERC
Consolidator Grant BEATRICE (2021–2026) focused on the interface between
information and electromagnetic theories. To date, he has received the presti-
gious 2023 Argo Network Innovation Award, the 2019 EURASIP Early Career
Award, and the 2018/2019 Royal Academy of Engineering/The Leverhulme
Trust Senior Research Fellowship. His team was also the Grand Winner of the
2019 Mobile World Congress Challenge. He was a recipient of the 2011 IEEE
ComSoc Best Young Researcher Award for Europe, Middle East, and Africa
Region. He was a co-recipient of the 2006 IEEE Communications Chapter
Project Prize for the best M.Sc. dissertation in the area of communications. He
has co-authored articles that received Best Paper Awards at 2018 IEEE WCSP
and 2014 IEEE ICC. In 2014, he received the Research Fund for International
Young Scientists from the National Natural Science Foundation of China.
He is currently the Editor-in-Chief of Physical Communication (Elsevier), a
Senior Editor of IEEE W IRELESS COMMUNICATIONS LETTERS and IEEE
Signal Processing Magazine , an Area Editor of IEEE T RANSACTIONS ON
COMMUNICATIONS , and the Editor-in-Large of IEEE O PEN JOURNAL OF
THE COMMUNICATIONS SOCIETY .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:02:20 UTC from IEEE Xplore.  Restrictions apply.
