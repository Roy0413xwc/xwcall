---
type: literature-fulltext
title: "Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network"
zotero_key: "S9X64ASI"
pdf_key: "2URLRKQX"
doi: "10.1109/TWC.2025.3649505"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network.md"
fulltext_path: "03fulltext/备选讲组会论文/S9X64ASI.md"
zotero_item: "zotero://select/library/items/S9X64ASI"
zotero_pdf: "zotero://open-pdf/library/items/2URLRKQX"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network

> PDF 原文逐页文本抽取；来源文件 SHA-256：`870598b016395574b45924ff3b2f2e353d6bc32d77fad580da809820277d891e`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 9295
Synesthesia of Machines (SoM)-Enhanced Sub-THz
ISAC Transmission for Air–Ground Network
Zonghui Yang
 , Graduate Student Member, IEEE , Shijian Gao
 , Member, IEEE, Xiang Cheng
 , Fellow, IEEE,
and Liuqing Yang
 , Fellow, IEEE
Abstract—Integrated sensing and communication (ISAC) at
sub-THz frequencies is crucial for future air-ground net-
works. However, optimizing ISAC performance while managing
operational latency is challenging due to unique propagation
characteristics and hardware limitations. This paper introduces
a multi-modal sensing fusion framework inspired by synesthesia
of machine (SoM) to enhance sub-THz ISAC transmission. By
exploiting inherent degrees of freedom in sub-THz hardware and
channels, the framework succeeds in tuning the radio-frequency
environment. It features squint-aware beam management to
improve air-ground network adaptability, enabling dynamic
three-dimensional ISAC links. By leveraging multi-modal infor-
mation, the framework enhances ISAC performance and reduces
latency. Visual data is used to rapidly localize users and targets,
while a customized multi-modal learning algorithm optimizes the
hybrid precoder. A new metric is proposed for comprehensive
performance evaluation. Extensive experiments demonstrate that
the proposed scheme signiﬁcantly improves ISAC efﬁciency.
Index Terms —Integrated sensing and communication, synes-
thesia of machine, sub-terahertz, hybrid precoding, beam squint,
air-ground network.
I. I NTRODUCTION
T
HE air-ground network is a foundational infrastructure
for networked intelligence and low-altitude economy,
addressing safety and efﬁciency needs in intelligent trans-
portation, autonomous logistics, and other next-generation
applications [1]. These networks require high-speed data trans-
mission and precise sensing capabilities [2]. Base stations
Received 6 June 2025; revised 20 October 2025; accepted 20 December
2025. Date of current version 12 January 2026. This work was supported
in part by the National Natural Science Foundation of China under Grant
62125101, Grant 62341101, Grant 62401488, and Grant U23A20339; in part
by the New Cornerstone Science Foundation through the XPLORER PRIZE;
in part by Guangzhou-[The Hong Kong University of Science and Technology
(HKUST)] (GZ) Joint Funding Scheme, under Grant 2025A03J3878; in part
by Guangzhou Municipal Project under Grant 2023A03J0011 and Grant
2024D03J0008; and in part by Guangdong Provincial Project under Grant
2023ZDZX1037 and Grant 2023ZT10X009. The associate editor coordinating
the review of this article and approving it for publication was Z. Liu.
(Corresponding author: Xiang Cheng.)
Zonghui Yang and Xiang Cheng are with the State Key Laboratory of Pho-
tonics and Communications, School of Electronics, Peking University, Beijing
100871, China (e-mail: yzh22@stu.pku.edu.cn; xiangcheng@pku.edu.cn).
Shijian Gao is with the Internet of Things Thrust, The Hong Kong
University of Science and Technology (Guangzhou), Guangzhou 511400,
China (e-mail: shijiangao@hkust-gz.edu.cn).
Liuqing Yang is with the Internet of Things Thrust & Intelligent Trans-
portation Thrust, The Hong Kong University of Science and Technology
(Guangzhou) Guangzhou 511400, China, and also with the Department of
Electronic and Computer Engineering, The Hong Kong University of Science
and Technology, Hong Kong, SAR, China (e-mail: lqyang@ust.hk).
Digital Object Identiﬁer 10.1109/TWC.2025.3649505
(BS) must ensure the quality of services for communication
users, such as mobile ground vehicles, while localizing low-
altitude autonomous aerial vehicles (AA Vs). To meet these
dual demands, 6G has positioned integrated sensing and
communication (ISAC) as a crucial enabling technology [3].
Achieving data rates up to 100 Gbps and sub-millimeter-level
positioning accuracy necessitates designing ISAC transmission
at sub-THz frequencies [4]. As the Internet of intelligent
devices grows, future networks will incorporate non-radio
frequency (RF) sensors, such as cameras [5], [6], requir-
ing BSs to integrate multi-modal sensing with sub-THz RF
communications.
Designing efﬁcient ISAC transmission in sub-THz systems
faces three principal challenges. Firstly, the unique prop-
agation characteristics of sub-THz systems hinder ISAC
performance optimization and increase operational time over-
head. Secondly, the three-dimensional and dynamic nature
of air-ground networks introduces complex trade-offs in
ISAC transmission. Thirdly, integrating heterogeneous sens-
ing modalities remains an unresolved obstacle to enhancing
ISAC capabilities. Addressing these challenges is crucial for
developing robust and efﬁcient air-ground networks that can
meet the stringent demands of future applications.
Speciﬁcally, in sub-THz channels, beam squint effects can
signiﬁcantly degrade array gain, impairing dual-functional
performance [7], [8]. To counteract this, true time delay
(TTD) has been incorporated into hybrid precoders, enabling
frequency-dependent phase compensation for cross-subcarrier
beam alignment [9], [10]. For sensing applications, [11] proac-
tively controlled squint patterns through TTDs to achieve
frequency-aware target positioning. Nevertheless, current sub-
THz systems lack a uniﬁed design that optimally balances
both functions. Reference [12] explored the degree of freedom
(DoF) of sub-THz channels through reconﬁgurable intelligent
surfaces, expanding ISAC Pareto boundaries, but this method
is primarily suited for narrowband systems and exacerbates
beam squint in sub-THz. Beyond channel limitations, sub-
THz hardware introduces operational complexity, particularly
for channel state information (CSI) acquisition and precoder
optimization. References [13] and [14] accelerated sub-THz
channel estimation by exploiting sparsity and low-rank nature,
but neglected sensing-induced interference. References [15]
and [16] employed block coordinate descent (BCD) meth-
ods for efﬁcient hybrid precoding, yet incurred performance
degradation in sub-THz conﬁgurations.
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

9296 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Meanwhile, the three-dimensional topology and dynamic
characteristics of air-ground networks pose critical difﬁcul-
ties for sub-THz ISAC transmission. These challenges arise
from the need to accommodate complex spatial conﬁgurations
and movement patterns, which introduce intricate trade-offs
in signal processing and transmission strategies. To achieve
comprehensive coverage across both horizontal and elevation
directions, deploying uniform planar arrays (UPA) becomes
essential [17], [18]. Unfortunately, this spatial expansion intro-
duces more ﬂexible beam dispersion in sub-THz compared to
linear arrays. Hence, existing methodologies designed for lin-
ear arrays, such as [19] and [20], cannot be directly extended
to such three-dimensional scenarios. Recent advances like [21]
embedded two-dimensional TTD arrays for UPA to allevi-
ate beam squint, enabling three-dimensional communication
links. Nonetheless, the UPA-based three-dimensional sensing
under beam squint remains unexplored. This gap necessitates
customized beam squint manipulation for UPA to establish
a dual-functional trade-off. Furthermore, both ground users
and low-altitude targets exhibit high mobility. Although [22]
developed predictive precoding for vehicular mobility, they
assume ideal user-target alignment, a questionable premise.
Reference [23] deployed ISAC in doubly dynamic networks
yet neglected low-altitude links, failing to support air-ground
networks.
While leveraging multi-modal sensing data from BS shows
promise in addressing these challenges, aligning heteroge-
neous data and integrating them with ISAC introduces a
new set of complexities. Inspired by the concept of machine
synesthesia (SoM) [5], out-of-band information has been lever-
aged for transceiver optimization through judicious network
design, bringing potential for efﬁciency improvement [23],
[24], [25], [26], [27], [28]. For example, [26] utilized computer
vision for rapid user detection and beam prediction, while
[27] derived channel covariance matrices based on visual and
positioning knowledge. However, the unique characteristics of
sub-THz frequencies, air-ground networks, and RF sensing
tasks remain underexplored in these schemes. Moreover, most
of these approaches employ end-to-end modeling, aiming
to transfer multi-modal observations into direct networking
solutions. As a result, such a manner lacks interpretability
and principled design. To advance ISAC, [23] dynamically
adjusted mmWave hybrid precoders using CSI-GPS fusion,
yet encounters prohibitive sub-THz complexity. Furthermore,
positioning priors alone cannot fully characterize channel
states, limiting the performance. Reference [28] developed a
SoM-driven analog precoder to extend sub-THz ISAC per-
formance boundaries, but neglects the time overhead of prior
acquisition and precoder design, rendering it impractical for
real-world deployment.
To address the aforementioned challenges, we propose a
novel paradigm of SoM-enhanced ISAC transmission uniquely
designed for sub-THz air-ground networks that simultane-
ously improves dual-functional performance while minimizing
time overhead. This innovative methodology leverages the
intrinsic DoFs present in sub-THz hardware and channels,
and establishes a synergistic fusion between visual data and
RF measurements, where RF sensing compensates for the
limited precision of visual information, while visual obser-
vations enhance the efﬁciency of RF operations. Speciﬁcally,
to mitigate impairments associated with sub-THz channels, we
ﬁrst establish the critical dependence of ISAC performance on
the correlation between communication and sensing channels.
This allows us to proactively establish equivalent channels
for ISAC enhancement without the need to modify existing
hardware. For three-dimensional air-ground deployments, we
initiate the process by employing visual sensing for real-time
user and target detection. Subsequently, we develop a squint-
aware cross-pattern beam tracking (SA-CP-BT) mechanism for
UPA, enabling rapid and precise angle reﬁnement. Building
on these advancements, we design a hybrid precoder through
multi-modal data fusion via a dedicated neural network that
utilizes a customized loss function. To comprehensively eval-
uate the practical performance of our approach, we introduce
the concept of ISAC efﬁciency, a holistic metric that balances
performance gains against the corresponding time overhead,
a factor often overlooked in prior ISAC studies. Extensive
simulations validate the superiority of the proposed frame-
work, demonstrating its potential to enhance the effectiveness
of ISAC in future air-ground networks.
The key contributions are summarized as follows:
• The intrinsic DoF in sub-THz channels is leveraged
to optimize ISAC performance by establishing a key
relationship between communication-sensing channel
correlation and system effectiveness. This approach uses
existing hardware DoF to accelerate prior information
acquisition and extend ISAC capabilities.
• A squint-aware transmission scheme for UPA is devel-
oped to establish adaptable three-dimensional ISAC links
within dynamic air-ground networks. ISAC efﬁciency is
introduced as a comprehensive metric to evaluate and
measure system performance, with extensive analysis
providing practical design insights.
• An innovative ISAC transmission paradigm integrates
multi-modal sensing data, including RF measurements
and visual information. This method enhances prior data
acquisition and precoder design, signiﬁcantly reducing
time overhead while ensuring robust ISAC performance.
The remainder of this work is structured as follows.
Section II introduces the system model. Section III exhibits the
proposed SoM-enhanced prior information estimation scheme,
and Section IV explains the proposed SoM-enhanced ISAC
precoding approach for sub-THz systems. Section V includes
the performance analysis, Section VI presents the experimental
results, and Section VII concludes this work.
Notation: a, a and A represent a scalar, a vector and a
matrix. (·)T, (·)H,‖·‖2,‖·‖F denote the transpose, conjugate
transpose, 2-norm and Frobenius-norm. ⊙ and ⊗ denote
the Hadamard and Kronecker product. diag (a) and diag (A)
denote the vector diagonal matrixization and extracting diag-
onal elements from a matrix. U[a,b ] denotes the uniform
distribution between a andb.CN (m,σ 2) represents the com-
plex Gaussian distribution with mean being m and covariance
being σ2. E(·) denotes the expectation. ⋃ denotes the union
of sets. R and C denote the sets of real numbers and complex
numbers. Re denotes the real part of the complex numbers.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9297
Fig. 1. A diagram of ISAC systems in air-ground network.
II. S YSTEM MODEL
We consider a wideband multi-antenna ISAC BS that serves
U single-antenna ground users while simultaneously sensing
K nearby low-altitude targets, as illustrated in Fig. 1. The
ISAC signal is transmitted using orthogonal frequency division
multiplexing (OFDM) with M subcarriers. The frequency of
them-th subcarrier isfm =fc+BM(m− M +12 ), withfc being
the carrier frequency and B being the bandwidth. The BS is
equipped with a UPA consisting of Nt =Nth×Ntv antennas.
Additionally, a co-located UPA withNr =Nrh×Nrv antennas
is used for echo reception.
Furthermore, RGB-Depth (RGB-D) cameras are placed at
the BS to oversee the surroundings. The ﬁeld of view (FOV)
of cameras is denoted asfov (in radians).Nw andNh indicate
the number of pixels horizontally and vertically.
A. Hybrid Precoder
As illustrated in Fig. 2, a typical hybrid architecture is
employed in the sub-THz system, where TTDs are placed
between the PSs and the antenna array. This conﬁguration
facilitates the frequency-dependent adjustment of phase shifts
to alleviate beam squint effects. To start with, data across M
subcarriers are ﬁrst processed by frequency-dependent digi-
tal precoders, followed by NRFM-point inverse fast Fourier
transforms (IFFT). Then NRF RF chains, each connected to
Nt PSs, are deployed. After passing through these PSs, the
signals are combined by Qt = Qth×Qtv TTD units. Each
TTD is associated with Lt =Lh×Lv PSs for each RF chain,
where Lh =
Nth
Qth and Lv = NtvQtv . Additionally, the UPA ispartitioned intoQt =Qth×Qtv sub-arrays, each connected to
one TTD at the corresponding location. Thus, the transmitted
signal at the m-th subcarrier can be written as
xm =F T,mF PF D,msm. (1)
In Eq. (1), sm = [ s1,m,··· ,sU,m]T ∼ CN(0,IU) repre-
sents the data symbols for U users at the m-th subcarrier.
F D,m ∈ CNRF×U is the digital precoder at the m-th sub-
carrier. F P ∈ CNt×NRF denotes the frequency-independent
precoder executed by the PS network, with|F P[i,j ]| = 1. The
frequency-dependent phase shifts introduced by the TTDs can
be represented as
F T,m = diag
[
vec
(
ej2πfm(T⊗1Lh×Lv ))], (2)
where T ∈ [0,t max]Qth×Qtv is associated with the TTD’s
controllable delays, and 1Lh×Lv is an all-one matrix. tmax
indicates the maximum achievable time delay determined by
the hardware.
B. Communication Model
Similar to [29], the communication channel between the BS
and the u-th user at the m-th subcarrier at time instant t can
be modeled as
hu,m(t) =βu,m(t)e−j
2πfmdc,u
cv at(θc,u,φ c,u,fm)
+ 1√PuKf
Pu∑
p=1
βu,p,m(t)e−j
2πfmdc,u,p
cv at(θc,u,p,φ c,u,p,fm).
(3)
For user- u, θc,u ∈ [0,π ) and φc,u ∈ [−π/2,π/ 2) are
its elevation and azimuth angles of the line-of-sight (LoS)
path. βu,m(t) = cv4πfmdc,uej(2πfd,ut+˜υc,u), and βu,p,m(t) =cv
4πfmdc,u,pej ˜υc,u,p denote the path gain of the LoS path andnon-line-of-sight (nLoS) ones. Here, dc,u and dc,u,p represent
the propagation distances, fd,c,u = vc,ufc/cv is the Doppler
frequency shift of theu-th user withvc,u being its radial veloc-
ity. ˜υc,u and ˜υc,u,p are noise phases, modeled as uniformly
distributed variables within [ 0, 2π). at(θc,u,φ c,u,fm) =
ah(θc,u,φ c,u,fm)⊗ av(θc,u,fm) ∈ CNt×1 denotes the
steering vector at fm from the transmitter towards θc and
φc, with [ah(θ,φ,f m)]nth = 1√Nthejπfmfc sinφ sinθ(nth−1),
[av(θ,fm)]ntv = 1√Ntvejπfmfc cosθ(ntv−1). Omitting the time
index for brevity, based on the above setup, the received signal
at the u-th user at the m-th subcarrier is represented as
yc,u,m =hHu,mF T,mF PF D,msm + zc,u,m, (4)
where zc,u,m is additive white Gaussian noise with power
spectrum density nc,0 (W/Hz). Taking into account inter-
user interference, the corresponding spectrum efﬁciency (SE)
becomes
Ru,m = BM log2
(
1+ |hHu,mFm[:,u ]|2∑
i⁄=u|hHu,mFm[:,i ]|2+ BMnc,0
)
, (5)
whereFm =F T,mF PF D,m. Consequently, the overall spec-
trum efﬁciency (SE) is computed as
R =
M∑
m=1
U∑
u=1
Ru,m. (6)
R will be optimized by acquiring prior channel information
and then utilizing an appropriate hybrid precoding strategy.
C. Sensing Model
According to [30], the target response matrix at the m-th
subcarrier at time t can be expressed as
Gm(t) =Ar,mΣm(t)AHt,m, (7)
where At,m = [ at(θs,1,φ s,1,fm),··· ,at(θs,K,φ s,K,fm)],
and Σm(t) = diag(α1,m(t),··· ,αK,m(t)). αk,m(t) =√
c2vσRCS,k
(4π)3f 2md4s,kej(2πfd,s,kt+˜υs,k) denotes the complex reﬂection
coefﬁcient of the k-th target, with σRCS,k and ds,k being
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

9298 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 2. A diagram of hybrid precoding structure in sub-THz systems.
the RCS and the distance of the k-th target respectively,
fd,s,k = 2vs,kfc/cv being the Doppler frequency shift of the
k-th target and ˜υs,k ∼ U[0, 2π]. θs = [θs,1,··· ,θ s,K] and
φs = [φs,1,··· ,φ s,K] denote the elevation and azimuth angles
of the K targets respectively. Then the echo at the m-th
subcarrier (time index omitted) at BS can be written as
ys,m =GmF T,mF PF D,msm + zs,m, (8)
where zs,m denotes the ISAC receiver white Gaussian noise
with power spectral density ns,0 (W/Hz). To ensure that the
noise follows a complex Gaussian distribution, we consider
whitening the received noise before target sensing. Accord-
ingly, the Cram ´er-Rao bound (CRB) associated with the
unbiased angle estimation can be derived as
CRB(θs,φs) = Tr


( M∑
m=1
Jm
)−1
. (9)
Jm is the Fisher information matrix with respect to θs andφs
given by
Jm = 2Bns,0 Re[Jm(θs,θs), Jm(θs,φs)J Hm(θs,φs), Jm(φs,φs)]. (10)
Each entry of Jm can be computed as
Jm(θs,φs) = ( ˙AHr,θ,m ˙Ar,φ,m)⊙(Σ∗mAHt,mR∗x,mAt,mΣm)
+( ˙AHr,θ,mAr,m)⊙(Σ∗mAHt,mR∗x,m ˙At,φ,mΣm)
+(AHr,m ˙Ar,φ,m)⊙(Σ∗m ˙AHt,θ,mR∗x,mAt,mΣm)
+(AHr,mAr,m)⊙(Σ∗m ˙AHt,θ,mR∗x,m ˙At,φ,mΣm),
with Rx,m = E
[
xmxHm], ˙At,θ,m[:,k ] = ∂at(θs,kφs,k,fm)∂θs,k and
˙At,φ,m[:,k ] = ∂at(θs,k,φs,k,fm)∂φs,k ].
In conventional optimization frameworks, (θs,φs) is typ-
ically obtained through preamble-based beam scanning pro-
cedures [31], which introduces signiﬁcant overhead. The
proposed method instead acquires this prior information
through multi-modal sensing at the BS, establishing the foun-
dation for efﬁcient precoder design.
D. ISAC Performance Enhancer: C-S Channel Correlation
We ﬁrst deﬁne the communication-sensing (C-S) channel
correlation and reveal the relationship between this metric and
the dual-functional performance. The C-S channel correlation
is measured by the distance between the power distributions in
the beamspace. The communication and sensing channels are
ﬁrst transformed into the beamspace through Discrete Fourier
Transform (DFT) as
hbc,m =
U∑
u=1
DHthu,m, hbs,m = diag(DHrGmDt), (11)
whereDt∈ CNt×ND andDr∈ CNr×ND are the dictionary
uniformly sampled in beamspace [32], with the number of
codewords being ND. For communications, the beamspace
channels for all users are aggregated. It is also worth men-
tioning that Gm consists of the steering vectors at both
ends. Consequently, the transmitter and receiver are separately
transformed into the beamspace. The beamspace channels
across all subcarriers are then aggregated and normalized as
ˆhbc = ∑Mm=1|hbc,m|‖∑Mm=1|hbc,m|‖1, ˆhbs = ∑Mm=1|hbs,m|‖∑Mm=1|hbs,m|‖1. (12)
Note that they can also be interpreted as the discrete
probability distribution for communication and sensing in
the beamspace. With ˆhbc and ˆhbs deﬁned, the C-S channel
correlation is quantiﬁed as follows:
Cor(H,G) = 1
KL(ˆhbc,ˆhbs), (13)
where KL (p1,p2) = ∑Nn=1p1[n] lnp1[n]p2[n] denotes theKullback-Leibler (K-L) divergence between distributions p1
and p2, H ={hu,m}U,Mu=1,m=1 and G ={Gm}Mm=1 denote
the communication and sensing channels for all users across
all subcarriers.
Proposition 1: As the C-S channel correlation Cor (H,G)
increases, the SE improves, and the CRB decreases in a
monotonic way.
Proof: See Appendix A. □
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9299
Fig. 3. Frame structure comparison between RF-only and vision-aided schemes.
Remark 1: The communication-sensing channel correlation
is a key feature of ISAC transmission. From Proposition 1,
having channels with higher correlation helps align commu-
nication and sensing subspaces, potentially improving ISAC
system performance. This can be achieved without extra
components by using TTDs connected to the UPA to adjust the
equivalent channels. Essentially, TTDs are used to maximize
the C-S channel correlation, which will inform the design of
the hybrid precoder in the next sections.
III. S OM-E NHANCED PRIORS ACQUISITION
The current ISAC framework relies on arduous efforts on
obtaining prior CSI and optimizing the precoder. However,
the substantial antenna arrays and dense subcarrier conﬁg-
urations inherent to sub-THz systems impose considerable
latency during CSI acquisition and precoder design phases. To
address these challenges, this section proposes a sensor-aided
strategy that synergizes out-of-band visual data with sparse RF
measurements to augment operational efﬁciency.
A. Frame Structure
According to 3GPP Release 18 [33], [34], each new radio
(NR) frame is divided into Nsub subframes. The positions of
mobile users and targets are assumed to be invariant within
one subframe. As illustrated in Fig. 3, each subframe consists
of a reference signal (RS) stage and a data transmission stage.
• Reference signal: In the RS stage, visual information is
ﬁrst used to identify candidate users and targets, followed
by a fast beam tracking process to reﬁne communica-
tion user angles while ensuring user synchronizations.
These estimations are then used to generate a position-
ing spectrum containing channel-related parameters. The
positioning spectrum and images are input into a pre-
trained neural network to predict the hybrid precoding
parameters for ISAC.
• Data transmission: Once the precoding is designed, the
communication symbols are precoded and transmitted to
the users during the remaining time of the subframe,
while the targets are estimated through echo reception.
As demonstrated in Fig. 3, existing frame structures in RF-
only transmission protocols, such as [19] and [22], require an
additional synchronization signal block (SSB) at the beginning
of the frame for initial beam training. In contrast, the proposed
ISAC transmission frame eliminates the need for both initial
beam training and instantaneous channel estimation, resulting
in simpler operations in the RS.
B. Identiﬁcation of Candidate User and Target
Unlike beam training via RF measurements only, we lever-
age the visual information to instantaneously estimate potential
users’ angular ranges. To accommodate the rapidly chang-
ing environment, an efﬁcient visual processing method is
essential. To this end, we employ YOLO-v5-s, a widely
used lightweight object detector in the computer vision
ﬁeld.
1) Visual Detection per Camera: During the ofﬂine stage,
we pre-train a customized YOLO-v5-s model on our dataset,
by minimizing the MSE between the network’s output and
the annotation labels, enabling it to accurately detect the
candidates and identify them as users or targets. During the
deployment stage, the RGB image captured is input into this
pre-trained detector, so the corresponding bounding boxes of
the users and targets are obtained as
bi = [bx,i,by,i,bw,i,bh,i,ci], (14)
where [bx,i,by,i] (in pixels) signiﬁes the center of the i-th
bounding box. bw,i and bh,i (in pixels) denote its width and
height, and ci denotes the category (0 for the user and 1 for
the target). Subsequently, based on the principle of pinhole
imaging [35], we transform the points within the candidate
bounding boxes into the world coordinates as
pwd,i =R−1j (zcam,iK−1pimg,i−pcam), (15)
where pwd,i = [xwd,i,y wd,i, zwd,i]T denotes the world coordi-
nates of the corresponding center point pimg,i = [bx,i,by,i, 1]T.
zcam,i is the depth of this point according to the depth map.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

9300 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
pcam is the world coordinates of the camera. In the above
transformation process,
K =


Nw
2 tan(fov/ 2), 0, Nw2
0, Nw2 tan(fov/ 2), Nh2
0, 0, 1

, (16)
represents the intrinsic matrix of the camera determined by
its conﬁguration. R =RzRyRx denotes the rotation matrix,
with
Rx =


1, 0, 0
0, cosγx, − sinγx
0, sinγx, cosγx

, (17a)
Ry =


cosγy, 0, sinγy
0, 1, 0
− sinγy, 0, cosγy

, (17b)
Rz =


cosγz, − sinγz, 0
sinγz, cosγz, 0
0, 0, 1

, (17c)
where γx, γy and γz denote the angles of the camera
with respect to the x, y and z-axis. Denote pUPA =
[xUPA,y UPA, zUPA]T as the world coordinates of the UPA. Then
we can obtain the candidate’s polar coordinates with respect
to the UPA, [ˆφi,ˆθi,ˆdi], as
ˆφi = arctan
(ywd,i−yUPA
xwd,i−xUPA
)
, (18a)
ˆθi,j =π− arctan
(√
(xwd,i−xUPA)2+(ywd,i−yUPA)2
|zwd,i− zUPA|
)
,
(18b)
ˆdi =‖pwd,i−pUPA‖2. (18c)
The angular ranges of the candidates relative to the
UPA can be determined by calculating the polar coordi-
nates of the bounding box vertices in a similar manner.
Therefore, the horizontal and vertical angular ranges of
the users along with their distances can be obtained as
{[ˆφc,u,min, ˆφc,u,max, ˆθc,u,min, ˆθc,u,max, ˆdc,u]Uu=1}. Additionally,
the portion of the camera’s view outside the UPA coverage will
not be considered.
Then the angular ranges of targets can be determined
in a similar manner, which can be expressed as T =
{[ˆφs,k,min, ˆφs,k,max, ˆθs,k,min, ˆθs,k,max, ˆds,k]Kk=1}.
2) Multi-View Association: In real-world scenarios, mul-
tiple cameras may be deployed to expand coverage. In this
case, letBj ={bi,j} denotes the set of bounding boxes from
camera j. The world coordinates of points within each bi,j
are computed via Eq. (15), forming the corresponding 3D
projection Proj(bi,j). Two detections bi,j andbi′,j′ from two
cameras are considered same if:
• Their categories match: ci,j =ci′,j′.
• The Intersection-over-Union (IoU) of their projected 3D
bounding boxes in the same subframe exceeds a threshold
τIoU:
IoU(Proj(bi,j), Proj(bi′,j′))>τ IoU, (19)
For successfully matched detections, a weighted fusion strat-
egy is applied to obtain a more accurate estimate of the
position. This association strategy ensures consistent matching
of visual detections to corresponding RF channels.
C. Squint-Aware Fine Beam Tracking
In sub-THz systems, visual information alone is insufﬁcient
for accurately pointing extremely narrow beams. To improve
the accuracy of the prior information, incorporating a small
number of RF operations is necessary.
Based on the angular ranges obtained from visual detection,
we propose a squint-aware cross-pattern beam tracking scheme
(SA-CP-BT) for both fast downlink synchronization and angle
estimation reﬁnement. Current techniques like [19] and [20],
require a complete scan. In contrast, SA-CP-BT only needs to
cover the cross-pattern tracks within each rectangle, thereby
reducing time overhead.
First, downlink synchronization for users is implemented
within the RS stage. This is achieved by exploiting the known
structure of the wideband probing signals. The users perform
timing synchronization by locating the peak in the cross-
correlation function between the received signal and the known
cyclic preﬁx sequence. Frequency synchronization is subse-
quently performed by measuring the phase rotation between
consecutive symbols. The initial angular prior provided by
visual sensing ensures sufﬁcient array gain for the reception
of these probing signals, even in the absence of SSB.
Subsequently, in the angle reﬁnement stage, the beams
across all subcarriers can be zoomed in from (φ0,θ 0) to
(φ1,θ 1) by setting TTDs and PSs as Eq. (20) and Eq. (21),
shown at the bottom of the next page. The pointing angles on
each subcarrier can be arranged in sequence along this tra-
jectory. Building on this, we can effectively control the beam
squint to cover the desired angular trajectory. Nevertheless,
solely relying on beam squint to cover all angles across all
ranges remains time-consuming.
Consider a user located at (φu,θu) within an angular range,
where the width is ∆φ and the height is ∆θ. The beam squint
is controlled to traverse this range along a speciﬁc trajectory,
pointing to (φm,θm) at the m-th subcarrier. The angular
distance between the user and (φm,θm) can be computed as
d(φu,θu,m ) =
(
(φu−φm)2 + (θu−θm)2).
Proposition 2: If the angular range satisﬁes ∆θ⩽ ∆SAθ =4fc
NthfM and ∆φ⩽ ∆SAφ = 4fcNtvfM , the array gain at differentsubcarriers along this beam squint trajectory decreases with
d(φu,θu,m ).
Proof: See Appendix B. □
Lemma 1: When squint beams horizontally traverse an
angular range at a height of ∆θ⩽ ∆SAθ , the user azimuth angle
in this range can be unambiguously resolved by identifying the
subcarrier exhibiting maximal array gain.
Drawing on Proposition 2 and Lemma 1, within a suf-
ﬁciently small angular range, when squint beams simply
traverse this range along a straight line in a given direction,
there is no need to scan other angles within this region. Instead,
the actual angle of the user in this direction can be accurately
determined based on the current beam responses. In contrast,
if this range is exceeded, angle ambiguity may occur, meaning
that the angle corresponding to the subcarrier with the largest
response may not represent the user’s true angle.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9301
Based on the above analysis, we can simply con-
trol the beam squint in a cross-pattern manner to reﬁne
the angle estimate. The SA-CP-BT scheme ﬁrst partitions
the coarse-grained angular range to satisfy the condition
in Lemma 1, and then performs horizontal and vertical
searches to sequentially identify the azimuth and elevation
angles.
1) Angular Range Partitioning: We ﬁrst divide the angular
range vertically into Ng grids, such that
ˆθc,u,max−ˆθc,u,min
Ng ⩽
∆SAθ .
2) Horizontal Search: In each angular grid, the beam squint
is ﬁrst controlled for the horizontal search. Denote Tbt as the
number of time slots used for tracking in each angular grid.
In each slot, the beams cover the horizontal trajectory from
(φ0,θ 0) to (φ1,θ 1), with φ0 = ˆφc,u,min + ((tbt− 1)∆φ/Tbt),
φ1 = ˆφc,u,min + (tbt∆φ/Tbt), and θ0 = θ1 = ( ˆθc,u,min +
ˆθc,u,max)/2. To this end, the TTDs and the PSs are set as (20)
and (21). The transmitted probing signal is transmitted. Then
the received signal at the u-th user at the m-th subcarriers in
the tbt-th slot in the ng-th grid is
y(h,u,tbt,ng)m =hHu,mF (h,u,tbt,ng)TD,m f (h,u,tbt,ng)PS +zc,u,m. (22)
The user feeds back to the BS the subcarrier and slot
index at which the modulus of the received signal reaches
its maximum across all slots, i.e., (m∗h,t∗bt,h,n∗g) =
argmaxm,tbt,ng|y(h,u,tbt,ng)m |. This quantized feedback, con-
veyed as indices, is inherently robust to error and it can be
transmitted over a highly reliable control channel in practical
links. Then the azimuth of the u-th user can be calculated as
ˆφc,u
= arcsin
[(fM−fm∗h)f1
Bfm∗h
sin
(
ˆφc,u,min+((t∗bt−1)∆φ/Tbt))
− fM(f1−fm∗h)fm∗hB sin(ˆφc,u,min + (t∗bt∆φ/Tbt))]. (23)
3) Vertical Search: With the estimated azimuth angle, we
initiate squint-aware tracking along the vertical direction dur-
ing Tbt slots, by setting φ0 = φ1 = ˆφc,u, θ0 = ˆθc,u,min +
((tbt− 1)∆θ/Tbt) and θ1 = ˆθc,u,min + (tbt∆θ/Tbt) in the tbt-
th slot. The user then returns the subcarrier and slot index as
(m∗v,t∗bt,v) = argmaxm,tbt|y(v,u,tbt)m |. Eventually, the elevation
angle of the u-th user can be determined as
ˆθc,u
= arccos
[(fM−fm∗v )f1
Bfm∗v
cos
(
ˆθc,u,min+((t∗bt−1)∆θ/Tbt))
− fM
fm∗v
cos
(
ˆθc,u,min + (t∗bt∆θ/Tbt))]. (24)
Through SA-CP-BT, the accurate angles of the users,
represented asU ={(ˆφc,u, ˆθc,u, ˆdc,u)Uu=1}, can be obtained.
IV. S OM-E NHANCED ISAC P RECODING
Based on the prior information obtained from the afore-
mentioned steps, we devise an unsupervised learning-assisted
approach to jointly design the parameters of ISAC hybrid pre-
coding. In this approach, both the RF-based prior information
and visual information will be utilized to enhance the dual-
functional performance.
A. Data Pre-Processing
The input data contains both the users’ and targets’ posi-
tioning prior information represented by Spos∈ RNx×Ny×2
and the RGB-D images captured from cameras represented by
Simg∈ RNh×Nw×4×3.
• RF-related positioning prior: Once the angular prior
[ˆφc,u, ˆθc,u]Uu=1, [ˆφs,k,min, ˆφs,k,max, ˆθs,k,min, ˆθs,k,max]Kk=1
and depth prior {ˆdc,u}Uu=1,{ˆds,k}Kk=1 are obtained
through visual detection and ﬁne beam tracking, they
are transformed into a 3D positioning spectrum Spos
as
Spos[nx,ny, 1] =



1−
ˆdc,u
dmax
, ifSnx,ny
⋂U⁄ =∅,
0, Otherwise,
Spos[nx,n y, 2] =



1−
ˆds,k
dmax
, ifSnx,ny
⋂T⁄ =∅,
0, Otherwise.
whereSnx,ny ={[θnx,θnx+ 1)×[φny,φny+ 1)} denotes the
quantized angular grid, with θnx = πNx (nx− 1), φny =−π2 + πNy (ny− 1). dmax deﬁnes the maximal detectabledistance within the BS’s coverage.
• Visual information: At each camera, the RGB
image and the depth map are concatenated to form
I (j)vi = [ I (j)rgb,I (j)dep] ∈ RNh×Nw×4 (j ∈ {l,m,r}),
followed by the normalization operation. Consequently,
the RGB-D images from three perspectives,
i.e., Simg = [ I (l)vi,I (m)vi ,I (r)vi ], are fed into the
network.
T [qh,qv] = 1LhLv
qhLh∑
nth =(qh−1)Lh+1
qhLh∑
ntv =(qv−1)Lv+1
f1
2Bfc
(
sinθ0 sinφ0(nth− 1) + cosθ0(ntv− 1)
)
− fM
2Bfc
(
sinθ1 sinφ1(nth− 1) + cosθ1(ntv− 1)
)
, (20)
ϕ[nth,ntv] = 2f1T [qh,q v] +f1fc
(
sinθ0 sinφ0(nth− 1) + cosθ0(ntv− 1)
)
. (21)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

9302 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 4. An illustration of the initial beam training and the proposed beam
tracking scheme.
B. Network Architecture
We devise a vision-RF fusion network for squint-aware
hybrid precoder design, which is termed as ViR-Net. The
network model consists of four components, including a spec-
trum encoder (SpE), a vision encoder (ViE), a feature-fusion
transformer (FFTF), and a precoding head, as demonstrated in
Fig. 5.
1) Spectrum Encoder: The channel-related features from
the positioning spectrum Spos are extracted by SpE. One
layer of convolutional blocks is utilized, comprising one 5×5
convolutional layer, one Gaussian error linear unit (GELU)
activation function, and one batch normalization (BN) layer.
Subsequently, a residual block is appended, which incorporates
two 3× 3 convolutional layers along with a 1× 1 skip
convolutional layer. Then a fully connected (FC) embedding
layer projects the features into a uniﬁed feature space, yielding
Vpos∈ RLf×dpos, where Lf is the feature space dimension
and dpos is the number of features.
2) Vision Encoder: SinceSpos only encompasses the posi-
tioning prior for the LoS paths for communications, the
information regarding the non-LoS paths is overlooked. There-
fore, we exploit RGB-D images to implicitly capture the prior
of non-LoS paths.
ViE processes RGB-D images to extract channel-related
features as a supplement to SpE. For each perspective, ViE
consists of three convolutional blocks, each with a convo-
lutional layer, GELU, max-pooling, and BN. Then features
from the three perspectives are concatenated, followed by a
self-attention mechanism for visual feature fusion. An FC
embedding layer outputs Vimg ∈ RLf×dimg. To expedite
training, we use a self-supervised strategy to pre-train the
convolutional blocks of ViE. Speciﬁcally, we build an auto-
encoder to compress and recover RGB-D images, with the
encoder formed by the ViE convolutional blocks, as detailed
in [36]. After training, the encoder is isolated to construct ViE.
3) Feature Fusion Transformer: We utilize the Transformer
structure to globally extract the correlation between the fea-
tures from the positioning spectrum and the images. Vpos
and Vimg are ﬁrst concatenated into a sequence of feature
vectors with dimension Lf× (dpos +dimg). Then the posi-
tion embedding is used to represent the relative positions
[37]. Subsequently two layers of Transformer encoder, each
consisting of a multi-head self-attention sub-layer and a multi-
layer perceptron sub-layer.
4) Precoding Head: The precoding head projects the fused
features into the values of TTDs, PSs and the digital precoder
sequentially. Two FC layers are ﬁrst employed to predict the
normalized value of TTDs as ˆt∈ [0, 1]Qt, with the Sigmoid
activation function. The output is T out = reshape(tmaxˆt).
Concatenating fused features and ˆt as the input, we proceed
to predict PSs through two FC layers, and the output is
ˆϕ∈ [0, 1]Nt×NRF. Then PSs are calculated as ϕout = 2π ˆϕ.
Finally, we concatenate fused features, ˆt and ˆϕ to predict the
digital part using another FC layer. The output ˆf∈ R2N 2RFM×1
is reshaped as the complex matrices F out∈ CNRF×NRF×M , and
then normalized to satisfy the power constraint.
C. Loss Function
We employ an unsupervised learning-based method for the
model training. To achieve the goal of maximizing ISAC per-
formance with the awareness of the C-S channel correlation,
we customize the loss function for one batch as
L =− 1Nb
Nb∑
i=1
Cor(H (i),G(i))
Cor⋆(H (i),G(i))
×
[
CRB (i)min
CRB (i) −ηcReLU(Γc−R(i))
]
, (25)
whereφViR denote the parameters of ViR-Net, Nb is the batch
size, Γc denotes the SE threshold for communications and ηc
is the weighting coefﬁcient controlling the penalty imposed
when the communication constraint is not met. A higher ηc
prioritizes communication performance, ensuring the spectral
efﬁciency, whereas a lower ηc places greater emphasis on
sensing accuracy. In this loss function, the objective of model
training is twofold: To enhance the C-S channel correlation
for modulating the communication and sensing subspaces,
and to separately improve the performance of communication
and sensing, thereby expanding the performance boundaries of
ISAC. In the ofﬂine training stage, ViR-Net is updated with
this loss function by backpropagation in randomly sampled
batches. In the deployment, the positioning spectrum and the
RGB-D images are captured and input to the pre-trained ViR-
Net, and then the values of TTDs, PSs and digital precoding
are obtained sequentially.
V. P ERFORMANCE ANALYSIS
A. Robustness Against Adverse Effects
1) Robustness Under Visual Uncertainties: Practical
deployment encounters challenges from adverse weather and
illumination variations, which can degrade visual detection
accuracy and impair ISAC performance. These conditions
cause shifts in data distribution, necessitating adaptive
improvements to the visual detection module. Techniques
like dehazing or illumination enhancement [38], [39] can
be applied before identifying entities. For entities occluded
beyond LoS coverage, fallback strategies like relaying or
handover to neighboring BSs become necessary.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9303
Fig. 5. An illustration of the architecture of the proposed ViR-Net.
To ensure robustness, a conﬁdence-based mode switching
mechanism can be incorporated. With the detection conﬁdence
score denoted as Cdet∈ [0, 1], the system reverts to RF-only
prior acquisition when Cdet < γthresh, avoiding performance
degradation from unreliable visual inputs.
2) Impact of Feedback Delay and Errors: The pro-
posed framework allocates dedicated time for beam feedback
in SA-CP-BT. However, due to non-ideal link conditions
and computational constraints, the feedback remains sus-
ceptible to both delays and errors. For the u-th user,
feedback delay td,u causes outdated beam measurements,
creating misalignment between estimated and actual user posi-
tions. The resulting angular error ∆θu with radial velocity
vc,u follows E[(∆θ)2] ≈ (vc,utddc,u )2. This error degrades
both communication SE and sensing accuracy proportionally
to (∆θ)2.
To address feedback imperfections, we use a Kalman
ﬁltering-based fusion mechanism that effectively combines
delayed RF measurements with real-time visual predictions.
This ﬁlter maintains a dynamic state estimate of each user’s
position and velocity, continuously correcting angle predic-
tions using the latest visual data as a reliable prior. This
approach compensates for feedback latency, as the visual
stream provides low-latency spatial updates while the RF
measurements offer periodic calibration.
B. Parameter Sensitivity Analysis
1) Impact of Doppler Shift: The Doppler shift fd,c,u =
vc,ufc
cv leads to time-varying channels. For SA-CP-BT, thephase rotation ∆φ during tracking duration TRS is ∆φ =
2πfd,c,uTRS. Since SA-CP-BT relies on power-based detection
rather than phase coherence, it maintains robustness when
∆φ < π/2, corresponding to vc,u < cv4fcTRS . For our parame-ters (fc = 100 GHz,TRS = 1 ms), this allows robustness up to
vmax≈ 75 m/s, which adequately covers the typical velocity
range in air-ground networks.
To further enhance robustness, we could incorporate veloc-
ity prior, estimated from consecutive RGB-D frames, into
ViR-Net. The enhanced input in S′pos∈ RNx×Ny×3 becomes:
S′pos[nx,ny, 3]=



1− ˆvc,u
vmax
, ifSnx,ny
⋂U⁄ =∅,
1− ˆvs,u
vmax
, ifSnx,ny
⋂T⁄ =∅,
0, Otherwise,
enabling implicit Doppler compensation in precoder design.
This would allow ViR-Net to adapt to varying mobility.
2) Impact of Antenna Elements Nt: The number of anten-
nas fundamentally inﬂuences system performance through
multiple coupled mechanisms. The achievable array gain
scales as Garray = Nt, directly improving the received SNR.
The angular resolution, determining both beamforming preci-
sion and sensing accuracy, follows∆θ3dB≈ 1Nt . Consequently,
the CRB for angle estimation improves as CRB (θ)∝ 1N 2t·SNR,enabling more accurate target localization.
However, these performance gains are accompanied by esca-
lating costs. The minimum required beam scanning overhead
in SA-CP-BT, governed by the unambiguous angular region
in Proposition 2, scales as Nt, thereby increasing the tracking
duration TRS. Moreover, computational complexity of hybrid
precoding also grows super-linearly with Nt. Therefore the
time-averaged SE can be quantiﬁed as
R≈
(
1− TRS(Nt)Tsubframe
)
· log(1 + SNR·Nt), (26)
saturating when Nt exceeds an optimal value that balances
performance gains against practical constraints.
3) Impact of TTD Units Qt: The number of TTD units
Qt determines the system’s ability to manipulate beam squint
for C-S correlation enhancement and angle tracking. When
Qt = Nt, ideal frequency-dependent beamforming is achiev-
able and C-S channel correlation can be maximized. As Qt
decreases, the equivalent phase proﬁle becomes a piecewise-
constant approximation, introducing a beam deviation error:
ϵbeam∝ BQtfc. (27)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

9304 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
This error degrades both communication spectral efﬁciency
and sensing CRB proportionally to ϵ2beam.
4) Impact of Pilot Length Np: Pilot length Np determines
channel estimation accuracy and RF operation overhead. The
estimation error follows σ2e(Np) = E‖hu,m− ˆhu,m‖2F ∝1
Np·SNR, affecting both communication and sensing per-formance. The effective spectral efﬁciency accounting for
overhead is
R≈
(
1− Np
Nsymbols
)
E
[
log2det
(
I+ SNR· ˆH ˆHH
σ2e(Np)
)]
, (28)
where σ2e(Np) is the estimation error variance. The sensing
performance similarly improves with better channel knowl-
edge as
CRB∝ 1
1− NpNsymbols · 1σ2e(Np). (29)
Hence the overall ISAC efﬁciency exhibits a quasi-concave
relationship with Np, initially increasing due to better estima-
tion then decreasing due to excessive overhead.
5) Impact of SA-CP-BT Steps TBt: The number of beam
tracking steps Tbt also balances angular estimation accuracy
and training overhead. The variance of estimation error scales
as σ2θ(Tbt)∝ 1Tbt·SNR, affecting both beamforming gain and
sensing accuracy proportionally to σ2θ. The time-averaged
spectral efﬁciency captures the trade-off as
R∝ log2
(
1 + SNR1 +σ2θ(Tbt))| {z }
Performance term
×
(
1− αbtTbt
Tsubframe
)
| {z }
Overhead term
, (30)
whereαbt is the time per tracking step. Similarly, the effective
sensing performance follows
CRB∝ σ2θ(Tbt)1− αbtTbtTsubframe. (31)
Thus the ISAC efﬁciency ηISAC shows a quasi-concave pattern
concerningTbt. It initially improves with better estimation but
eventually declines due to excessive overhead.
C. Computational Complexity Analysis
We analyze the computational complexity of the proposed
framework by decomposing it into following three main
components. The complexity of each module is evaluated
in terms of ﬂoating-point operations (FLOPs) under typical
conﬁgurations.
1) Visual Detection (YOLO-v5s): Processing RGB-D inputs
from three cameras at 1024×1920 resolution requires approx-
imately 45.2 GFLOPs per frame, calculated as FYOLO =∑Ldet
l=1 (2Kl,hKl,wCl,inCl,outHlWl), where Lv is the number
of layers, Kl,h,Kl,w is the kernel size, Cl,v is the number of
channels, and Hl,Wl is the output feature map size at layer l.
2) SA-CP-BT: Each probing beam involves precoding and
beamforming across MM subcarriers and Tbt tracking slots,
amounting toFBT = 2UTbtMNt≈ 1.3 GFLOPs.
3) ViR-Net Inference: The FLOPs breakdown is as fol-
lows: FViE = ∑Lvl=1(2K 2l,vCl−1,vCl,vHlWl), FSpE =
2K 2sCs,inCs,outNxNy,FFFTF = 2LfD2(4+H)+4L2fD, and
FHead = 2(DinDhidden +DhiddenDout).Ks is the kernel size
in the SpE, Cs is the number of channels, Lf is the sequence
length, and D = dpos +dimg is the feature dimension. The
total ViR-Net FLOPs is approximately 18.7 GFLOPs.
Hence the total FLOPs for one full inference is
Ftotal =FYOLO +FBT +FViR−Net
= 45.2 + 1.3 + 18.7 = 65.2 GFLOPs,
which is linear to Nt,Tbt andM, and quadratic in the feature
dimension D. This computational requirement is feasible for
real-time execution on modern GPUs within a single subframe.
VI. S IMULATIONS
In this section, experimental results are presented to evaluate
the performance of the proposed schemes.
A. Scenario Construction
For model training, we construct multiple low-altitude ISAC
datasets comprising both urban intersections and suburban
road scenarios, with data collected from simulations and real-
world measurements. Each scenario includes ground vehicles
and low-altitude AA Vs, served by a roadside base station
equipped with a UPA and three RGB-D cameras. For sim-
ulated scenarios, visual and RF data are generated through the
following procedure:
• Scenario construction : We use Simulation of Urban
MObility (SUMO) software to simulate the trajectories
of moving vehicles and AA Vs at the intersection [40],
with the road width being 30 m. The vehicle trajecto-
ries include straight motion, turning and lane-changing,
while the AA V trajectories encompass horizontal straight-
line ﬂight and vertical lift. The world coordinates of
the vehicles and AA Vs in each frame are exported
as the positioning ground truth for the angle estimation
and the off-line model training.
• Visual data acquisition : We construct a simulated
urban-area scene in AirSim software by leveraging the
real-physics engine [41]. As the vehicles and AA Vs are
in motion, we use 3 cameras installed on the BS oriented
towards the left, middle, and right perspectives, to capture
RGB images and depth maps. This visual information
serves as training data for the candidate object detector
and ViR-Net. For the object detector, we annotate the
bounding boxes to train it. Regarding ViR-Net, unsuper-
vised training is carried out by using the acquired channel
truth and position truth.
• Channel data acquisition : We imported the scene into
the Wireless InSite R©software [42] and conﬁgured the
parameters of the BS and vehicle antenna arrays, along
with the surface parameters, to ensure its consistency
with the scene in AirSim. Post-scene import, communi-
cation and sensing channels for each frame are generated
through ray tracing, in accordance with the channel model
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9305
TABLE I
EXPERIMENTAL SCENARIOS DESCRIPTION
TABLE II
SYSTEM SETUP FOR THE TRANSCEIVER ’S HARDWARE
TABLE III
SYSTEM SETUP FOR THE SUB-TH Z CHANNELS
TABLE IV
SYSTEM SETUP FOR THE SENSOR EQUIPMENT
detailed in Section II. This channel information forms the
basis for loss calculation and model training.
The real-world data is obtained from the campus scenarios in
the SynthSoM dataset [43] which provides aligned positions,
CSI and visual measurements. The corresponding environmen-
tal parameters for each dataset are provided in Table I.
B. Parameters Setting
Unless otherwise speciﬁed, the system setup for the hard-
ware, the channels, the sensors and the hyper-parameters in
model training can be found in Table II, Table III, Table IV
and Table V, respectively. We deﬁne the SNR as PtBnc,0 . Weconducted the training of the neural networks on an NVIDIA
RTX4060Ti and tested the overall schemes in MATLAB
2024b. The system has 10 cores, a per-core clock speed of
2.5 GHz, and 160 ﬂoating-point operations per cycle.
TABLE V
HYPER -PARAMETERS FOR MODEL TRAINING
C. Comparison Methods
The methods to be evaluated include:
• SoM-ISAC: The proposed SoM-enhanced vision-RF
integrated ISAC transmission strategy.
• SA-Opt-ISAC: A near-optimal benchmark with only RF
operations. The BS ﬁrst implements the initial hier-
archical beam training as operated in [18] to acquire
coarse-grained angular information, followed by the pro-
posed SA-CP-BT in Section III and digital channel
estimation to obtain the complete communication and
sensing channel information as the prior. Then a squint-
aware optimization of hybrid precoding is implemented
as operated in [28] for ISAC transmission. The proposed
RF-only squint-aware optimization scheme for ISAC.
• Vi-ISAC: An ablation approach for the proposed SoM-
ISAC. The BS uses only visual information for end-to-
end ISAC precoder design without RF operations.
• BCD-ISAC: An RF-only block coordinate descent
(BCD)-based optimization approach without TTDs for
ISAC in sub-THz systems [16].
• DPP: Communication-centric squint elimination in [9].
• YOLO: Sensing-centric squint control in [11].
The computational complexity in terms of FLOPs among
these schemes are evaluated under the same system settings
in Table VI. The RF-only benchmarks exhibit FLOPs over
an order of magnitude higher than SoM-ISAC, highlighting
the signiﬁcant efﬁciency gain achieved through multi-modal
sensing and learning-based precoder design.
D. Evaluation Metric
Conventional ISAC studies predominantly focus solely on
the Pareto boundary between SE and CRB [16], [23], [28],
overlooking the essential time overhead required to attain such
performance. To offer a more realistic assessment in latency-
sensitive applications, we incorporate the achievable SE and
CRB during transmission, along with the time overhead for
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

9306 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 6. Network training.
TABLE VI
OVERALL COMPLEXITY COMPARISON [GFLOP S]
prior acquisition and precoder design, into a uniﬁed metric.
Speciﬁcally, we deﬁne the ISAC efﬁciency as the achievable
time-averaged SE–CRB pair per frame, i.e.,
EISAC(H,G,T,F P,F D) = (R,CRB). (32)
The time-averaged SE and CRB are calculated respectively as
R =R⋆TdataNsub
Tframe
, CRB =CRB⋆ Tframe
TdataNsub
, (33)
whereR⋆ andCRB⋆ denote the achievable SE-CRB pair on
the ISAC performance boundary based on multi-modal infor-
mation.Tframe is the duration per frame,Tdata is the duration for
each data transmission stage. Tframe =TSSB+Nsub(TRS+Tdata)
for RF-only schemes, andTframe =Nsub(TRS+Tdata) for vision-
aided schemes, withTSSB,TRS denoting the period of SSB and
RS stages. The achievable (R,CRB) pairs form an efﬁciency
boundary, quantifying the practical performance trade-off.
1) Comparison With the Traditional Pareto Boundary:
The conventional Pareto boundary describes the theoretical
performance trade-off assuming inﬁnite resources, whereas
ISAC efﬁciency reﬂects the practical trade-off under limited
time. A scheme optimal on the Pareto frontier may yield low
real-world efﬁciency due to excessive overhead.
2) Comparison With the Traditional Efﬁciency Metrics
(e.G., SE/EE): Metrics like SE or EE focus on hardware cost
but ignore dynamic adaptability. High ISAC efﬁciency implies
both high performance and rapid attainment, enhancing suit-
ability for dynamic environments.
E. Comparative Study
We ﬁrst visualize the performance of the proposed ViR-Net
model during the training process in D1 in Fig. 6. As the
number of training epochs increases, the loss function of ViR-
Net gradually decreases and rapidly converges after 10 epochs.
When only visual information is input to ViR-Net, the model’s
loss increases signiﬁcantly, implying the indispensable role of
RF data. Ablation experiments in Table VII further conﬁrm
TABLE VII
ABLATION EXPERIMENTS IN VIR-N ET
that the proposed approach improves SE, CRB, and channel
correlation, while also demonstrating the positive impact of
the position encoding and the Transformer layer in the model.
In Fig. 7(a), we compare the ISAC performance bound-
aries of different schemes achieved in D1, by optimizing the
CRB with varying SE thresholds and SNR ﬁxed at 10 dB.
SA-Opt-ISAC experiences errors in prior channel estimation,
resulting in performance loss compared to the perfect prior
case. However, it remains close to the theoretical optimal
bound. SoM-ISAC is inferior to SA-Opt-ISAC, as the visual
information combined with reduced RF overhead does not
provide more accurate prior data, but it still offers a better
ISAC trade-off than the existing RF-only schemes. Compared
to the non-TTD optimization scheme BCD-ISAC, TTD proves
advantageous in actively regulating the correlation between
communication and sensing channels, leading to better ISAC
performance trade-offs. Vi-ISAC, however, performs poorly,
highlighting that relying solely on visual information in
sub-THz systems without RF overheads is less effective.
Furthermore, we compare these schemes under different
user-target spatial distributions in Fig. 7(b) and Fig. 7(c),
with SNR ﬁxed at 10 dB. We deﬁne the mean squared
interval of angle (MSIA) between targets and the user as√ ∑U
u=1
∑K
k=1(θs,k−θc,u)2+(φs,k−φc,u)2
2UK . When MSIA = 0 (indi-
cating perfect user-target alignment), the RF-only schemes
achieve optimal performance by focusing all beams. How-
ever, due to the limited dispersion of beam squint, the array
gain decreases as the user-target angular separation increases,
causing the ISAC performance of existing benchmarks to
deteriorate signiﬁcantly. Notably, the SA-Opt-ISAC and SoM-
ISAC schemes effectively mitigate the performance loss by
actively tuning the channels through TTDs, demonstrating
better adaptation to spatial distribution.
In Fig. 8, we further compare the overall running time
of these schemes, incorporating both prior acquisition and
precoder design. SA-Opt-ISAC has the highest running time
due to the time-consuming initial beam training, channel esti-
mation, and precoder design processes. In contrast, SoM-ISAC
avoids these initial steps, with its primary time consumption
coming from network inference, resulting in an overall runtime
of approximately half that of SA-Opt-ISAC. The Vi-ISAC
scheme, with zero RF overhead, has the least time overhead,
which can be considered as an extreme case.
Taking the comprehensive operational time into account, we
evaluate the ISAC efﬁciency boundaries of different schemes
in scenario D1, with a frame period of 1 s and 10 sub-frames
per frame. As illustrated in Fig. 9, despite the performance
gap in absolute terms, SoM-ISAC demonstrates signiﬁcantly
higher efﬁciency than the RF-only schemes at the frame level.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9307
Fig. 7. ISAC performance comparison among different schemes. TABLE VIII
ISAC E FFICIENCY COMPARISONS ACROSS DIFFERENT SCENARIOS
Fig. 8. Running time comparison among different precoding schemes.
Fig. 9. Comparisons of ISAC efﬁciency among various schemes.
This enhanced efﬁciency results from the balance between
ISAC performance and time overhead, allowing more time for
data transmission and target sensing within each frame. In con-
trast, RF-only schemes exhibit lower efﬁciency, particularly
at high SE, where its sensing efﬁciency drops signiﬁcantly
and even becomes inferior to that of the vision-only scheme.
Therefore, it is evident that the proposed SoM-ISAC offers
superior efﬁciency for real-world ISAC tasks.
To validate performance across different environments and
channel conditions, Table VIII compares the ISAC efﬁciency
of various schemes on different datasets, with ηc = 10
and Γc = 20 . For each dataset, we independently train
visual detectors to adapt to varying data distributions and
select appropriate IoU thresholds. Results demonstrate that
SoM-ISAC achieves the best ISAC efﬁciency in all datasets,
even under challenging conditions including nighttime oper-
ations and dense user scenarios, conﬁrming its effectiveness
in diverse environments. By adaptively adjusting the visual
detector and relevant parameters, the proposed framework
effectively handles non-ideal conditions such as nighttime
operations and dense target scenarios.
We conduct ablation studies to assess the impact of non-
ideal factors on ISAC efﬁciency. In the dense scenario D3,
a low IoU threshold causes the visual detector to merge
nearby users, degrading performance due to erroneous priors.
Increasing the IoU threshold mitigates this issue, as shown in
Table IX. In scenario D1, we examine beam feedback errors
caused by inter-carrier interference, inter-user interference,
or feedback delays. These errors are simulated by adding
Gaussian noise to beam indices. Table X shows that as
feedback errors increase, the SA-Opt-ISAC benchmark suffers
from signiﬁcant spectral efﬁciency degradation due to beam
misalignment. In contrast, SoM-ISAC maintains more stable
performance by using visual information to compensate for
such errors.
Additionally, we investigate the impact of system con-
ﬁgurations on ISAC efﬁciency in following experiments. In
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

9308 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE IX
ABLATION STUDY ON THE IOU T HRESHOLD IN VISUAL DETECTION
TABLE X
ABLATION STUDY ON THE IMPACT OF FEEDBACK ERROR
IN SA-CP-BT ON THE TIME -AVERAGED SE
Fig. 10. Time-averaged CRB versus number of slots in SA-CP-BT Tbt.
Fig. 11. Time-averaged SE versus number of pilots Np.
Fig. 10, we compare the inﬂuence of the number of slots Tbt
in SA-CP-BT. A similar trend is observed in both RF-only
and vision-aided schemes: As Tbt increases, the time-averaged
sensing efﬁciency initially improves but then declines. This
is because increasing Tbt improves the accuracy of prior
angle estimation, which in turn enhances the precoding per-
formance. However, once Tbt exceeds a certain threshold, the
performance gain no longer compensates for the increased
time overhead, leading to a decrease in overall efﬁciency.
SoM-ISAC is more sensitive to the number of slots, as the
time required for beam tracking constitutes a larger portion
of the total operation time, resulting in greater variation. A
similar trend is observed for time-averaged SE, which is thus
omitted here, with individual component efﬁciency serving
as the representative metric for analysis of ISAC efﬁciency.
For brevity, the same convention applies to the subsequent
analyses.
Subsequently, we examine the effect of the number of
pilots on ISAC efﬁciency in Fig. 11. With different pilot
Fig. 12. Time-averaged CRB versus number of TTDs Qt.
Fig. 13. Time-averaged SE versus number of transmitting antennas Nt.
conﬁgurations, SA-Opt-ISAC scheme maintains its superiority
in the RF-only category. All RF-only schemes show a trend
of increasing and then decreasing efﬁciency as the number
of pilots increases, indicating that a moderate number of
pilots can enhance efﬁciency. In contrast, the vision-aided
scheme operates with zero pilots, as it does not require channel
estimation, yet its efﬁciency consistently surpasses that of
RF-only schemes due to the complementary enhancement
from visual information. This highlights the efﬁciency of the
proposed vision-aided zero-pilot scheme.
In terms of hardware conﬁgurations, we compare ISAC
efﬁciency under different TTD numbers in Fig. 12. When
Qt = Nt, the TTD offers maximum ﬂexibility, enabling the
achievement of the optimal CRB and SE for the highest efﬁ-
ciency. As the number of TTDs decreases, both the accuracy of
beam tracking and the DoF in correlation regulation diminish,
leading to performance degradation and subsequent reduction
in ISAC efﬁciency. Thus, the role of TTDs in enhancing ISAC
efﬁciency in sub-THz systems is demonstrated. This trend is
more pronounced in the SA-Opt-ISAC, where the reduction
in the number of TTDs ampliﬁes the errors in channel prior
information. In contrast, SoM-ISAC is relatively less affected
by the reduction in accuracy.
Fig. 13 further investigates the impact of antenna numbers
Nt on ISAC efﬁciency. We train separate models for different
antenna numbers and evaluate them on Dataset D1. As Nt
increases, higher array gain improves both the accuracy of
prior estimation in beam tracking and the capability of the
precoding matrix, leading to enhanced absolute ISAC perfor-
mance. However, the accompanying increase in RF overhead
causes the ISAC efﬁciency to approach saturation and eventu-
ally decline when the antenna array becomes sufﬁciently large.
We further test ISAC efﬁciency under varying velocities in
Dataset D1 using an enhanced ViR-Net incorporating speed
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9309
Fig. 14. Time-averaged SE versus moving speed of users and targets.
Fig. 15. Time-averaged SE versus subframe duration Tsubframe.
priors. As shown in Fig. 14, with increasing Doppler shift,
RF-only benchmarks exhibit little change in time overhead,
yet suffer from beam misalignment due to feedback inaccu-
racy and inter-carrier interference during channel estimation,
degrading precoding performance. In contrast, SoM-ISAC
directly extracts speed information from visual data, thereby
maintaining robust ISAC efﬁciency across different Doppler
conditions. This approach allows SoM-ISAC to better handle
the challenges posed by Doppler shifts, ensuring consistent
performance even as relative motion impacts traditional RF-
based systems.
Finally, we compare the ISAC efﬁciency across different
periods of time division duplexing (TDD) frames in Fig. 15. In
real-world scenarios, varying frame periods correspond to dif-
ferent user and target speeds. As the speeds of users and targets
increase, their positions change more rapidly, requiring more
frequent beam tracking, which results in a shorter subframe
period. In the experiments, as the subframe period increases,
the communication and sensing efﬁciency of each scheme
gradually improves until it stabilizes, reaching a convergence
point in a static scenario. Notably, the efﬁciency of SA-
Opt-ISAC improves more signiﬁcantly with longer periods,
eventually approaching or even surpassing that of SoM-ISAC
when the subframe period becomes sufﬁciently long. This
indicates that SA-Opt-ISAC is better suited for quasi-static
scenarios with longer subframes, while SoM-ISAC is more
advantageous for dynamic scenarios with shorter subframes.
VII. C ONCLUSION
This paper presented a SoM-enhanced framework for sub-
THz ISAC transmission in air-ground networks. By leveraging
the design degrees of freedom in sub-THz hardware and
channels, and integrating multi-modal sensing information, the
proposed solution signiﬁcantly improved ISAC performance
while accommodating three-dimensional air-ground dynamics.
The approach began with utilizing visual information and
sparse RF operations to swiftly acquire essential prior knowl-
edge about mobile users and targets within three-dimensional
networks. A multi-modal fusion learning technique was then
developed to optimize the ISAC hybrid precoder, achieving
a better balance between dual functionalities. Comprehensive
simulations demonstrated that the proposed framework not
only ensured robust ISAC performance in the sub-THz range
but also minimized operational time overhead, substantially
enhancing ISAC efﬁciency.
APPENDIX A
PROOF OF THE PROPOSITION 1
According to [44], the optimal Rx,m can be expressed as
R⋆x,m =UmΛmU Hm,
whereUm =[A∗t,m, ˙A∗t,θ,m, ˙A∗t,φ,m,{at(θc,u,φ c,u,fm)}Uu=1] =
[um,1,··· ,um,NR]∈ CNt×NR (NR = 3K +U) serving as the
basis vectors under the given channels Hm andGm, and Λm
is positive semi-deﬁnite with Λm[n1,n 2] = λm,n1,n2. Then
the achievable rate-CRB on the Pareto boundary is written as
R⋆ =
M∑
m=1
log2
[
1+ 1σ2c
NR∑
n1=1
NR∑
n2=1
λm,n1,n2Ξc,m[n1,n 2]
]
,
CRB⋆≈N 2R
[ M∑
m=1
NR∑
n1=1
NR∑
n2=1
λm,n1,n2Ξs,m[n1,n 2]
]−1
, (34)
Ξc,m[n1,n2] = ξc,m,n1,n2 = hbc,mHDHtum,n1uHm,n2Dthbc,m,
Ξs,m[n1,n2] =ξs,m,n1,n2=uHm,n1At,mΣmΣ∗mAHt,mum,n2 are
both determined by the channels. By solving this multi-
objective optimization, the optimal Λm can be written as
Λ⋆m = (Ξc,m +γΞs,m) PtMTr(Ξc,m +γΞs,m). (35)
By substituting (35) into (34), the rate and CRB at the Pareto
optimum can be described via Ξc,m and Ξs,m as
R⋆ =
M∑
m
log2
[
1+ 1σ2c
NR∑
n1
NR∑
n2
Pt(ξ2c,m,n1,n2 +γξs,m,n1,n2ξc,m,n1,n2)
MTr(Ξc,m+γΞs,m)
]
,
(36)
CRB⋆
≈N 2R
[M∑
m
NR∑
n1
NR∑
n2
Pt(γξ 2s,m,n1,n2 +ξs,m,n1,n2ξc,m,n1,n2)
MTr(Ξc,m+γΞs,m)
]−1
.
(37)
Leveraging the sparsity of beamspace channels [32], we denote
the indices of peaks in ˆhbc and ˆhbs as{ψc,m} and{ψs,k,m}.
The similarity of these peaks is deﬁned as Sm(H,G) =∑K
k=1 I(ψc,m =ψs,k,m) andS(H,G) =∑Mm=1Sm with I(·)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

9310 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
ξc,m,n1,n2≈ I(n1=n2>3K)+2I(1⩽n1⩽K,n2>3K)
K∑
k=1
I(ψs,k,m=ψc,m)+I(1⩽n1,n2⩽K)
K∑
k1
K∑
k2
I(ψs,k1,m=ψc,m)I(ψs,k2,m=ψc,m),
ξs,m,n1,n2≈ I(n1 =n2>3K)
K∑
k=1
I(ψc,m=ψs,k,m)|Σm[k,k ]|2+I(1⩽n1,n2⩽K)
K∑
k=1
|Σm[k,k ]|2. (38)
being the indicator function. It can be proved that a higher
Cor(H,G) gives rise to a higher S(H,G) [45]. As derived
in Eq. (38), shown at the top of the page,asS(H,G) increases,
bothξc,m,n1,n2 andξs,m,n1,n2 improve, leading to an increase
inR⋆ and a reduction in CRB⋆ along the Pareto boundary.
Therefore a higher C-S channel correlation improves the dual-
functional gain.
APPENDIX B
PROOF OF THE PROPOSITION 2
Denote the array gain towards the direction (φ,θ ) at the m-
th subcarrier, with the TTDs being T and the PSs connecting
to one RF chain being ϕ, as
g(θ,φ,f m;T,ϕ) =aH(θ,φ )F T,mF P
=
⏐⏐⏐⏐∑
nth
∑
ntv
ejπ (ϕ[nth,ntv]− 2fmT [nth,ntv]
−fm
fc
[sinθ sinφ(nth− 1) + cosθ(ntv− 1)]
)⏐⏐⏐⏐.
Note that g(θ,φ,f m;T,ϕ) reaches its maximum if and
only if each term of g(θ,φ,f m;T,ϕ) has phase 0 for any
(nth,ntv). When Qt = Nt, to make the diverged beams in
different subcarriers cover the angular trajectory from (φ0,θ 0)
to (φ1,θ 1), it is necessary to make the beam at the ﬁrst
subcarrier point to the starting angle and the beam at the M-th
subcarrier point to the ending angle, i.e.,
ϕ[nth,ntv]−2f1T [nth,ntv]−f1fc
(
sinθ0 sinφ0(nth−1)
+cosθ0(ntv−1)
)
=0,
ϕ[nth,ntv]−2fMT [nth,ntv]−fMfc
(
sinθ1 sinφ1(nth− 1)
+cosθ1(ntv−1)
)
=0.
Solving this set of equations gives rise to (20) and (21). By
substituting (20) and (21) into g(θ,φ,f m;T,ϕ), we have the
beam at the m-th subcarrier point to the direction
φm = arcsin
((fM−fm)f1
Bfm
sinφ0− fM(f1−fm)fmB sinφ1
)
,
θm = arccos
((fM−fm)f1
Bfm
cosθ0− fMfm cosθ1
)
.
It is easy to prove that both φm and θm are monotonous
with the index. When Qt⩽ Nt, simply averaging the delay
values within the same subarray can achieve the beam pointing
control, giving rise to Eq. (20) and Eq. (21), and the above
conclusion still holds true.
Controlling the beam squint in the angular trajectory from
(φ0,θ 0) to (φ1,θ 1), the array gain at the m-th subcarrier
received by the user within this range can be expressed as
g(θc,u,φc,u,fm;T,ϕ) =aH(θc,u,φc,u,fm)aθm,φm,fm
=
(
aHh(θc,u,φc,u,fm)ah(θm,φm,fm)
)(
aHv (θc,u,fm)av(θm,fm)
)
= 1N 2t
⏐⏐⏐⏐Φ(fmfc (sinφm sinθm− sinφc,u sinθc,u))⏐⏐⏐⏐
·
⏐⏐⏐⏐Φ(fmfc (cosθm− cosθc,u))⏐⏐⏐⏐,
where Φ(x) = sin(Ntπx/2)sin(πx/2) is the Dirichlet function. Note that
the main lobe of Φ(x) lies in the range
[
− 1Nt, 1Nt
]
.
When the angular constraints in the Proposition 2 are
satisﬁed, we have⏐⏐⏐⏐fmfc (sinφm sinθm− sinφc,u sinθc,u)⏐⏐⏐⏐
⩽ fM
fc
| sinφc,u|·| θm−θc,u|⩽ 2Nth,⏐⏐⏐⏐fmfc (cosθm− cosθc,u)⏐⏐⏐⏐
⩽ fM
fc
|φm−φc,u|⩽ 2Ntv.
Therefore the angular trajectory by the beam squint lies in the
main lobe of g(θc,u,φc,u,fm;T,ϕ), and the monotonicity in
the Proposition 2 is satisﬁed.
REFERENCES
[1] Q. Wu et al., “A comprehensive overview on 5G-and-beyond networks
with UA Vs: From communications to sensing and intelligence,” IEEE
J. Sel. Areas Commun. , vol. 39, no. 10, pp. 2912–2945, Oct. 2021.
[2] X. Cheng, D. Duan, S. Gao, and L. Yang, “Integrated sensing and
communications (ISAC) for vehicular communication networks (VCN),”
IEEE Internet Things J. , vol. 9, no. 23, pp. 23441–23451, Dec. 2022.
[3] Z. Wei et al., “Integrated sensing and communication signals toward
5G-A and 6G: A survey,” IEEE Internet Things J. , vol. 10, no. 13,
pp. 11068–11092, Jul. 2023.
[4] C. Han, Y . Wu, Z. Chen, Y . Chen, and G. Wang, “THz ISAC: A physical-
layer perspective of terahertz integrated sensing and communication,”
IEEE Commun. Mag. , vol. 62, no. 2, pp. 102–108, Feb. 2024.
[5] X. Cheng et al., “Intelligent multi-modal sensing-communication inte-
gration: Synesthesia of machines,” IEEE Commun. Surveys Tuts. ,
vol. 26, no. 1, pp. 258–301, 1st Quart., 2023.
[6] G. Charan, M. Alrabeiah, and A. Alkhateeb, “Vision-aided 6G wireless
communications: Blockage prediction and proactive handoff,” IEEE
Trans. Veh. Technol., vol. 70, no. 10, pp. 10193–10208, Oct. 2021.
[7] H. Do, N. Lee, R. W. Heath Jr., and A. Lozano, “Hybrid arrays: How
many RF chains are required to prevent beam squint?,” IEEE Trans.
Wireless Commun., vol. 23, no. 9, pp. 11708–11722, Sep. 2024.
[8] B. Wang, F. Gao, S. Jin, H. Lin, and G. Y . Li, “Spatial- and frequency-
wideband effects in millimeter-wave massive MIMO systems,” IEEE
Trans. Signal Process., vol. 66, no. 13, pp. 3393–3406, Jul. 2018.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 17 页

Y ANG et al.: SYNESTHESIA OF MACHINES (SoM)-ENHANCED SUB-THz ISAC TRANSMISSION 9311
[9] L. Dai, J. Tan, Z. Chen, and H. V . Poor, “Delay-phase precoding
for wideband THz massive MIMO,” IEEE Trans. Wireless Commun. ,
vol. 21, no. 9, pp. 7271–7286, Sep. 2022.
[10] D. Q. Nguyen and T. Kim, “Joint delay-phase precoding under true-time
delay constraints in wideband sub-THz hybrid massive MIMO systems,”
IEEE Trans. Commun. , vol. 72, no. 10, pp. 6633–6646, Oct. 2024.
[11] H. Luo, F. Gao, H. Lin, S. Ma, and H. V . Poor, “YOLO: An efﬁcient ter-
ahertz band integrated sensing and communications scheme with beam
squint,” IEEE Trans. Wireless Commun., vol. 23, no. 8, pp. 9389–9403,
Aug. 2024.
[12] J. Ye, L. Huang, Z. Chen, P. Zhang, and M. Rihan, “Unsupervised
learning for joint beamforming design in RIS-aided ISAC systems,”
IEEE Wireless Commun. Lett. , vol. 13, no. 8, pp. 2100–2104, Aug.
2024.
[13] S. Gao, X. Cheng, and L. Yang, “Estimating doubly-selective
channels for hybrid mmWave massive MIMO systems: A doubly-
sparse approach,” IEEE Trans. Wireless Commun. , vol. 19, no. 9,
pp. 5703–5715, Sep. 2020.
[14] A. Brighente, M. Cerutti, M. Nicoli, S. Tomasin, and U. Spagnolini,
“Estimation of wideband dynamic mmWave and THz channels for 5G
systems and beyond,” IEEE J. Sel. Areas Commun. , vol. 38, no. 9,
pp. 2026–2040, Sep. 2020.
[15] L. Li, J. Zhang, and T.-H. Chang, “Beamforming optimization for robust
sensing and communication in dynamic mmWave MIMO networks,”
IEEE J. Sel. Areas Commun. , vol. 43, no. 4, pp. 1354–1370, Apr. 2025.
[16] P. Wang, J. Fang, X. Zeng, Z. Chen, and H. Li, “Low-complexity joint
transceiver optimization for mmWave/THz MU-MIMO ISAC systems,”
IEEE Internet Things J. , vol. 12, no. 5, pp. 5289–5304, Mar. 2025.
[17] A. Liao et al., “Terahertz ultra-massive MIMO-based aeronautical com-
munications in space-air-ground integrated networks,”IEEE J. Sel. Areas
Commun., vol. 39, no. 6, pp. 1741–1767, Jun. 2021.
[18] B. Ning, Z. Chen, Z. Tian, C. Han, and S. Li, “A uniﬁed 3D beam
training and tracking procedure for terahertz communication,” IEEE
Trans. Wireless Commun., vol. 21, no. 4, pp. 2445–2461, Apr. 2022.
[19] J. Tan and L. Dai, “Wideband beam tracking in THz massive MIMO
systems,” IEEE J. Sel. Areas Commun. , vol. 39, no. 6, pp. 1693–1710,
Jun. 2021.
[20] X. Shi, J. Wang, Z. Sun, and J. Song, “Spatial-chirp codebook-based
hierarchical beam training for extremely large-scale massive MIMO,”
IEEE Trans. Wireless Commun. , vol. 23, no. 4, pp. 2824–2838, Apr.
2024.
[21] Y . Wu, G. Song, H. Liu, L. Xiao, and T. Jiang, “3-D hybrid beamforming
for terahertz broadband communication system with beam squint,” IEEE
Trans. Broadcast., vol. 69, no. 1, pp. 264–275, Mar. 2023.
[22] W. Yuan, F. Liu, C. Masouros, J. Yuan, D. W. K. Ng, and N. Gonz ´alez-
Prelcic, “Bayesian predictive beamforming for vehicular networks: A
low-overhead joint radar-communication approach,” IEEE Trans. Wire-
less Commun., vol. 20, no. 3, pp. 1442–1456, Mar. 2021.
[23] Z. Yang, S. Gao, X. Cheng, and L. Yang, “Synesthesia of machines
(SoM)-enhanced ISAC precoding for vehicular networks with double
dynamics,” IEEE Trans. Commun., vol. 73, no. 9, pp. 7967–7984, Sep.
2025.
[24] Z. Huang, L. Bai, M. Sun, and X. Cheng, “A LiDAR-aided channel
model for vehicular intelligent sensing-communication integration,”
IEEE Trans. Intell. Transp. Syst., vol. 25, no. 12, pp. 20105–20119, Dec.
2024.
[25] Z. Yang, S. Gao, X. Cheng, and L. Yang, “Superposed IM-
OFDM (S-IM-OFDM): An enhanced OFDM for integrated sensing
and communications,” IEEE Trans. Veh. Technol. , vol. 73, no. 10,
pp. 15832–15836, Oct. 2024.
[26] H. Zhang, S. Gao, X. Cheng, and L. Yang, “Integrated sensing and
communications toward proactive beamforming in mmWave V2I via
multi-modal feature fusion (MMFF),” IEEE Trans. Wireless Commun. ,
vol. 23, no. 11, pp. 15721–15735, Nov. 2024.
[27] W. Xu, F. Gao, J. Zhang, X. Tao, and A. Alkhateeb, “Deep learning
based channel covariance matrix estimation with user location and scene
images,” IEEE Trans. Commun. , vol. 69, no. 12, pp. 8145–8158, Dec.
2021.
[28] Z. Yang, S. Gao, and X. Cheng, “Synesthesia of machine (SoM)-driven
analog precoder optimization for enhanced ISAC performance in sub-
THz systems,” 2024, arXiv:2412.13532.
[29] C. Han and Y . Chen, “Propagation modeling for wireless communi-
cations in the terahertz band,” IEEE Commun. Mag. , vol. 56, no. 6,
pp. 96–101, Jun. 2018.
[30] Z. Gao et al., “Integrated sensing and communication with mmWave
massive MIMO: A compressed sampling perspective,” IEEE Trans.
Wireless Commun., vol. 22, no. 3, pp. 1745–1762, Mar. 2023.
[31] F. Liu, Y .-F. Liu, A. Li, C. Masouros, and Y . C. Eldar, “Cram ´er–Rao
bound optimization for joint radar-communication beamforming,” IEEE
Trans. Signal Process., vol. 70, pp. 240–253, 2022.
[32] S. Gao, X. Cheng, and L. Yang, “Mutual information maximizing
wideband multi-user (wMU) mmWave massive MIMO,” IEEE Trans.
Commun., vol. 69, no. 5, pp. 3067–3078, May 2021.
[33] S.-Y . Lien, S.-L. Shieh, Y . Huang, B. Su, Y .-L. Hsu, and H.-Y . Wei,
“5G new radio: Waveform, frame structure, multiple access, and initial
access,” IEEE Commun. Mag. , vol. 55, no. 6, pp. 64–71, Jun. 2017.
[34] X. Lin, “An overview of 5G advanced evolution in 3GPP release 18,”
IEEE Commun. Standards Mag. , vol. 6, no. 3, pp. 77–83, Sep. 2022.
[35] A. Geiger, F. Moosmann, ¨O. Car, and B. Schuster, “Automatic camera
and range sensor calibration using a single shot,” in Proc. IEEE Int.
Conf. Robot. Autom. , May 2012, pp. 3936–3943.
[36] K. Davaslioglu, S. Boztas, M. C. Ertem, Y . E. Sagduyu, and E. Ayanoglu,
“Self-supervised RF signal representation learning for NextG signal clas-
siﬁcation with deep learning,” IEEE Wireless Commun. Lett. , vol. 12,
no. 1, pp. 65–69, Jan. 2023.
[37] A. Dosovitskiy, L. Beyer, A. Kolesnikov, D. Weissenborn, and
N. Houlsby, “An image is worth 16 ×16 words: Transformers for image
recognition at scale,” 2020, arXiv:2010.11929.
[38] Y . Song, J. Li, X. Wang, and X. Chen, “Single image dehazing
using ranking convolutional neural network,” IEEE Trans. Multimedia ,
vol. 20, no. 6, pp. 1548–1560, Jun. 2018.
[39] X. Guo, Y . Li, and H. Ling, “LIME: Low-light image enhancement
via illumination map estimation,” IEEE Trans. Image Process., vol. 26,
no. 2, pp. 982–993, Feb. 2017.
[40] P. A. Lopez et al., “Microscopic trafﬁc simulation using SUMO,”
in Proc. 21st Int. Conf. Intell. Transp. Syst. (ITSC) , Nov. 2018,
pp. 2575–2582.
[41] S. Shah, A. Kapoor, D. Dey, and C. Lovett, “AirSim: High-ﬁdelity visual
and physical simulation for autonomous vehicles,” in Field and Service
Robotics: Results of 11th International Conference, Springer, Nov. 2017,
pp. 621–635.
[42] Wireless InSite . Accessed: Mar. 2022. [Online]. Available: https://
www.remcom.com/wireless-insite-em-propagation-software
[43] X. Cheng et al., “SynthSoM: A synthetic intelligent multi-modal
sensing-communication dataset for synesthesia of machines (SoM),” Sci.
Data, vol. 12, no. 1, p. 819, May 2025.
[44] S. Lu, X. Meng, Z. Du, Y . Xiong, and F. Liu, “On the performance
gain of integrated sensing and communications: A subspace corre-
lation perspective,” in Proc. IEEE Int. Conf. Commun. , May 2023,
pp. 2735–2740.
[45] J. R. Hershey and P. A. Olsen, “Approximating the Kullback Leibler
divergence between Gaussian mixture models,” in Proc. IEEE Int.
Conf. Acoust., Speech Signal Process. (ICASSP) , vol. 4, Apr. 2007,
pp. 317–320.
Zonghui Yang (Graduate Student Member, IEEE)
received the B.S. degree from the Department of
Electronic Engineering, Tsinghua University, Bei-
jing, China, in 2022. He is currently pursuing the
Ph.D. degree with the School of Electronics, Peking
University, Beijing. His current research interests
include AI-aided wireless communications, inte-
grated sensing and communications, and wireless
foundation models.
Shijian Gao (Member, IEEE) received the Ph.D.
degree from the University of Minnesota, Minneapo-
lis, USA, in 2022. After graduation, he was as a
Senior RF Engineer with Sam sung SoC Lab, San
Diego, USA. In February 2024, he joined the Inter-
net of Things Thrust, The Hong Kong University of
Science and Technology (Guangzhou), Guangzhou,
China, as an Assistant Professor. His research inter-
ests include statistical signal processing, wireless
communication, RF systems, and machine learning.
He was the co-recipient of 2021 MICCAI Young
Scientist Paper Award. He serves as an Associate Editor for IET Communi-
cations.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 18 页

9312 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Xiang Cheng (Fellow, IEEE) received the joint
Ph.D. degree from Heriot-Watt University and The
University of Edinburgh, Edinburgh, U.K., in 2009.
He is currently a Boya Distinguished Professor with
Peking University. He has authored or co-authored
more than 280 journals and conference papers, 11
books, and holds 32 patents in his research interests
which include in-depth integration of communica-
tion networks and artiﬁcial intelligence, including
intelligent communication networks and connected
intelligence. He was a recipient of the IEEE
Asia–Paciﬁc Outstanding Young Researcher Award in 2015, the Xplorer Prize,
am the Best Paper Awards at IEEE ITST’12, ICCC’13, ITSC’14, ICC’16,
ICNC’17, GLOBECOM’18, ICCS’18, and ICC’19 in 2023. He was a co-
recipient of the 2016 IEEE Journal on Selected Areas in Communications Best
Paper Award: Leonard G. Abraham Prize and the 2021 IET Communications
Best Paper Award: Premium Award. He has been a Highly Cited Chinese
Researcher since 2020. In 2021 and 2023, he was selected into two world
scientist lists, including the World’s Top2 released by Stanford University
and top computer science scientists released by Guide2Research. He was the
symposium lead chair, the co-chair, and a member of the technical program
committee for several international conferences. He led the establishment of
four Chinese standards (including industry standards and group standards)
and participated in the Formulation of Ten 3GPP International Standards
and two Chinese Industry Standards. He is currently a Subject Editor of
IET Communications , an Associate Editor of IEEE T RANSACTIONS ON
WIRELESS COMMUNICATIONS , IEEE T RANSACTIONS ON INTELLIGENT
TRANSPORTATION SYSTEMS , IEEE W IRELESS COMMUNICATIONS LET-
TERS , and Journal of Communications and Information Networks . He was
a Distinguished Lecturer of the IEEE Vehicular Technology Society.
Liuqing Yang (Fellow, IEEE) received the Ph.D.
degree from the University of Minnesota, Min-
neapolis, MN, USA, in 2004. She has been a
Faculty Member with the University of Florida,
Colorado State University, and the University of
Minnesota. She is currently a Chair Professor with
The Hong Kong University of Science and Technol-
ogy (Guangzhou), where she serves as the Acting
Director of the Low-Altitude Systems and Econ-
omy Research Institute (LASERi), and the Head of
the Intelligent Transportation (INTR) Thrust. Her
research interests include communications, sensing, and networked intelli-
gence, subjects on which she has published more than 400 journal and
conference papers, four book chapters, and ﬁve books. She is a Fellow
of AAIA. She was a recipient of the ONR YIP Award in 2007, the NSF
CAREER Award in 2009, and multiple Best Paper Awards. She is an
Executive Editorial Committee (EEC) Member of IEEE T RANSACTIONS
ON WIRELESS COMMUNICATIONS . She has also served as the Editor-
in-Chief of IET Communications , on the editorial board for an array of
elite journals, including IEEE T RANSACTIONS ON SIGNAL PROCESSING ,
IEEE T RANSACTIONS ON COMMUNICATIONS , and IEEE T RANSACTIONS
ON INTELLIGENT TRANSPORTATION SYSTEMS , in various roles of IEEE
ComSoc and IEEE ITSS, as well as in leadership roles for many conferences.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:13:03 UTC from IEEE Xplore.  Restrictions apply.
