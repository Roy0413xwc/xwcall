---
title: "Cooperative ISAC-Empowered Low-Altitude Economy"
zotero_key: "8A5WX5RQ"
pdf_key: "AC6Q6PHJ"
doi: "10.1109/TWC.2025.3542399"
collection: "UAV"
source: "Zotero imported PDF (pypdf extraction)"
page_mapping: "unknown"
source_sha256: "873408ca1d54772e24f763344afb24d5fe41dfd8ac77a40c0fd6066f681c660e"
pdf_pages: 16
---

# Cooperative ISAC-Empowered Low-Altitude Economy — Fulltext

> 由 Zotero 附件 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证。

---


<!-- extraction_page_index: 1 -->

1
Cooperative ISAC-empowered
Low-Altitude Economy
Jun Tang, Yiming Yu, Cunhua Pan, Hong Ren, Dongming Wang, Jiangzhou Wang, Fellow, IEEE and
Xiaohu You, Fellow, IEEE
Abstract—This paper proposes a cooperative integrated sens-
ing and communication (ISAC) scheme for the low-altitude
sensing scenario, aiming at estimating the parameters of the
unmanned aerial vehicles (UA Vs) and enhancing the sensing
performance via cooperation. The proposed scheme consists of
two stages. In Stage I, we formulate the monostatic parameter
estimation problem via using a tensor decomposition model. By
leveraging the Vandermonde structure of the factor matrix, a
spatial smoothing tensor decomposition scheme is introduced
to estimate the UA Vs’ parameters. To further reduce the com-
putational complexity, we design a reduced-dimensional (RD)
angle of arrival (AoA) estimation algorithm based on generalized
Rayleigh quotient (GRQ). In Stage II, the positions and true
velocities of the UA Vs are determined through the data fusion
across multiple base stations (BSs). Specifically, we first develop
a false removing minimum spanning tree (MST)-based data
association method to accurately match the BSs’ parameter
estimations to the same UA V . Then, a Pareto optimality method
and a residual weighting scheme are developed to facilitate the
position and velocity estimation, respectively. We further extend
our approach to the dual-polarized system. Simulation results
validate the effectiveness of the proposed schemes in comparison
to the conventional techniques.
Index Terms—Integrated sensing and communication (ISAC),
cooperative sensing, tensor decomposition, parameter estimation,
data fusion.
I. I NTRODUCTION
In the forthcoming fifth-generation advanced (5G-A) and
sixth-generation (6G) mobile communication systems, the
plethora of low-altitude applications in transportation, tourism,
agriculture and emergency services boosts the burgeoning
of low-altitude economy (LAE) [1]. In LAE, the interaction
between the unmanned aerial vehicles (UA Vs) and the base
stations (BSs) is critical. On one hand, the UA Vs need to
communicate with the BSs for data transmission. On the
other hand, the BSs are also supposed to sense and detect
the UA Vs to prevent the unauthorized intrusion or collision.
To this end, the novel paradigm known as integrated sensing
and communication (ISAC) is recognized as a promising
solution. Compared to the conventional radar deployment,
ISAC systems can simultaneously achieve the superior sensing
capabilities and high data transmission rates [2].
Jun Tang, Cunhua Pan, Hong Ren, Dongming Wang, Jiangzhou Wang and
Xiaohu You are with National Mobile Communications Research Labora-
tory, Southeast University, Nanjing, China. (e-mail: 220241016, cpan, hren,
wangdm, j.z.wang, xhyu@seu.edu.cn).
Yiming Yu is with the Department of Radio Engineering, China
Mobile Group Design Institute Company Ltd., Beijing, China. (e-
mail:yuyiming@cmdi.chinamobile.com).
Corresponding author: Cunhua Pan.
In the low-altitude sensing scenarios, depending on the
spatial deployment of the transmitter and the receiver, ISAC
configurations can be classified into three primary categories:
monostatic [3], [4], bistatic [5], [6] and multistatic [7], [8].
Specifically, in the bistatic and multistatic systems, one or
several BSs acts as the transmitters with others served as
the receivers to receive the sensing symbols. However, these
configurations impose high requirements on the deployment
locations and the synchronization across multiple BSs. Differ-
ently, in the monostatic setup, the BS transmits the sensing
symbols simultaneously while receiving the echo signals re-
flected by the UA Vs, which simplifies the deployment of BS
and enhances the system’s tolerance to asynchronization. How-
ever, conventional monostatic configuration still faces several
challenges. First, due to the path loss, the sensing performance
for the distant UA Vs is relatively poor [9]. In addition, if
there exists the obstructions (such as the tall buildings or
trees) between the UA Vs and the BSs, the detection probability
will decrease dramatically. Moreover, the comprehensive status
of the UA Vs, such as their true velocities cannot be fully
captured, since only the radial velocities can be derived from
the echo signals [7].
To overcome the above limitations of the conventional
monostatic configuration, the cooperative ISAC framework
was proposed [10]–[14]. In the cooperative ISAC networks,
each BS first estimates the targets’ parameters from the
received echo signals. Then, the estimated parameters are
fused in the cloud to enhance the sensing performance. In
this scenario, targets that are far from a certain BS may be
relatively close to other BSs, thereby enhancing the detection
probability and the coverage of the ISAC network. Moreover,
more diverse sensing directions and richer targets’ information
brought by the distributed deployment of BSs further boosts
the sensing performance, thereby reducing the estimation
error and enabling the ability to recover more comprehensive
information of the UA Vs, such as their true velocities in the
three-dimensional (3-D) space. Recent studies in the field
of cooperative ISAC have aimed at designing the sensing
solutions to facilitate the sensing capabilities in various scenar-
ios. In the single-antenna setup, [12], [13] designed the two-
stage target localization schemes in the orthogonal frequency
division multiplexing (OFDM) network, where the ranges of
targets were respectively derived via the compressed sensing
(CS) and the two-dimensional (2-D) fast Fourier transform
(FFT) algorithms, then the targets’ positions were estimated
based on the range estimations. Likewise, [14] first derived
the target’s range and radial velocity, and then proposed a
arXiv:2412.20371v1  [eess.SP]  29 Dec 2024

<!-- extraction_page_index: 2 -->

2
symbol-level fusion scheme across multiple BSs to facilitate
the position and velocity estimation. In the multi-antenna
setup, in addition to the ranges and velocities, the BSs are
also supposed to capture the angles of arrival (AoAs) of
the targets to further enhance the sensing performance, and
several classic AoA estimation techniques such as multiple
signal classification (MUSIC) algorithm have been adopted
to derive the targets’ AoAs in ISAC systems [15]. Beyond
the aforementioned conventional estimation methods, tensor
techniques are gaining increasing popularity for extracting the
multi-dimensional parameters recently, and have been applied
for the channel and target parameter estimation due to its
superior estimation accuracy and the guaranteed automatic
parameter pairing [16]–[19]. The authors of [16] delved into a
preliminary exploration of the tensor-based ISAC, where the
channel and target parameter estimation were achieved through
a unified tensor approach. However, [16] did not reveal the
benefits of improving the sensing accuracy through the multi-
BS cooperation.
As previously mentioned, although the above studies have
preliminarily demonstrated the potential of the cooperative
ISAC configuration, most of the existing studies only consid-
ered some special scenarios of the cooperative ISAC networks
(such as the single-antenna or the single-target cases), lacking
the generality to extend to the more complex and practical sce-
narios. Specifically, for the monostatic parameter estimation,
several estimation algorithms only considered the single-target
scenarios, when extended to the multi-target scenario, how to
match the multi-dimensional parameters to the same target
still needs to be well designed. For the multi-BS cooperation,
the data association across BSs is another critical issue in the
multi-target scenario. Although several association methods
have been developed [12], [13], they are merely designed
for the single-antenna setup. To address these issues, this
paper aims to provide a comprehensive scheme for a more
general multi-antenna multi-target sensing scenario within the
cooperative ISAC framework. The main contributions of this
work are summarized as follows:
1) We consider a general cooperative ISAC system, aiming
at sensing multiple UA Vs via the cooperation across the
multiple multi-antenna BSs. To address the challenging
sensing issue, a comprehensive scheme is developed.
2) First, several preliminary steps are presented to provide
some prior and guidelines for the subsequent sens-
ing scheme. Then, the monostatic parameter estimation
problem is formulated via using a tensor decomposition
model. By leveraging the Vandermonde structure of the
factor matrix, an spatial smoothing tensor decomposition
algorithm is developed to derive the AoAs, ranges, radial
velocities, and channel coefficients of the UA Vs. Addi-
tionally, we develop a reduced-dimensional (RD) AoA
estimation algorithm based on generalized Rayleigh quo-
tient (GRQ) to further reduce the complexity.
3) Subsequently, a false removing minimum spanning tree
(MST)-based multi-BS data association method is pre-
sented. Compared to the conventional exhaustive permu-
tation method, this approach not only prevents the false
detections from impacting the subsequent data fusion,
but also reduces the complexity effectively when there
are a large number of UA Vs.
4) Finally, a Pareto optimality method and a residual
weighting scheme are presented to facilitate the position
and velocity estimation, respectively.
5) We also extend our approach to the dual-polarized sys-
tem via a forth-order tensor decomposition formulation,
which improves the estimation accuracy when the array
size is limited.
The remainder of this paper is organized as follows. In
Section II, we present the signal and channel model of the
cooperative ISAC system. In Section III, we provide sev-
eral preliminary steps for the proposed cooperative sensing
scheme. In Section IV, the parameter estimation problem is
formulated via using a tensor decomposition model and a
spatial smoothing tensor decomposition scheme is developed.
In Section V, we estimate the positions and velocities of the
UA Vs. In Section VI, we extend our approach to the dual-
polarized system. Finally, the simulations and conclusion are
provided in Sections VII and VIII, respectively.
Notations: Lowercase letter, boldface lowercase letter, bold-
face uppercase letter and calligraphy uppercase letter denote
the scalars, vectors, matrices and tensors, respectively, i.e., y,
y, Y, Y. The operations (·)∗, (·)T , (·)H and (·)† represent
the conjugate, transpose, Hermitian transpose, and Pseudo-
inverse, respectively. The notations Tr(Y), ∥Y∥F , ∥y∥2 and
|y| denote the trace of matrix Y, the Frobenius norm of matrix
Y, the L2-norm of vector y, and the modulus of scalar y,
respectively. The notations R and C represent the real field and
the complex field, respectively. The symbol [Y]ij refers to the
(i, j)-th entry of matrix Y. The operators ◦, ⊗ and ⊙ denote
the outer product, Kronecker product and Khatri-Rao product,
respectively. The notation D (y) denotes the diagonal matrix
formed by vector y. The operation unvecM ×N (y) rearranges
M N× 1 vector y into M × N matrix Y. For two sets A
and B, A ∪ Bdenotes the set {x|x ∈ Aor x ∈ B}, and A \ B
denotes the set {x|x ∈ Aand x /∈ B}.
II. S YSTEM MODEL
A. Signal Model
As shown in Fig. 1, we consider a cooperative ISAC
system aiming at sensing the low-altitude UA Vs’ flight status,
including their positions and velocities. In this system, J
BSs first estimate the parameters of UA Vs from the echo
signals, then the estimated parameters are fused in the cloud
to enhance the sensing performance. In order to avoid the
interference between the BSs, we assume that each BS op-
erates in the non-overlapping frequency band. In addition,
as shown in Fig. 2, to achieve the high spectral efficiency
and flexible resource allocation [20]–[22] while reducing the
deployment costs of radio frequency (RF) chains, we consider
a MIMO-OFDM framework with partially-connected hybrid
beamforming (HBF) structure, where each BS is equipped with
R RF chains and L antennas. Specifically, each RF channel
is assumed to be equipped with L/R antennas, where L/R is
assumed to be an integer. Moreover, we assume that all the BSs

<!-- extraction_page_index: 3 -->

3
BSJ
1UAV
UAVK
Cloud
UAVk
1BS
BS j
Transmit signal
Echo signal
Fig. 1. Cooperative ISAC system.
perform the same parameter estimation algorithm before the
data fusion is performed. Thus, for notational simplicity, we
omit the subscript j of BSs temporarily. In order to facilitate
the formulation of parameter estimation problem via a using
tensor decomposition model in the following contents of this
paper, we assume that all RF channels of each BS share only
one data stream for sensing. In this way, the transmitted signal
is given by
s (t)
=
M −1X
m=0
N −1X
n=0
sm,n · ej2πm∆f t· r (t − nTs) , n= 0, . . . , N− 1,
(1)
where M and N denote the numbers of subcarriers and
OFDM symbols, respectively. The notation ∆f denotes the
subcarrier spacing (SCS), Ts denotes the OFDM symbol
period (including the cyclic prefix), and r (t) is the transmit
pulse shaping filter, respectively. The symbol sm,n denotes
the complex data allocated in the m-th subcarrier and the n-
th OFDM symbol. Without loss of generality, we assume that
|sm,n|2 = 1 , ∀m, n. Then, the transmitted frequency domain
signal vector can be expressed as
xm,n = FT Xe · sm,n ∈ CL×1, (2)
where FT X≜ FAT XFDT X, FAT X∈ CL×R and FDT X∈ CR×R
denote the transmit analog and digital precoding matrices,
respectively. The non-zero elements of FAT Xare subjected to
the constant module constraint. The symbol e = [1, . . . ,1]T ∈
RR×1 denotes an all-one vector. The received frequency
domain signal vector is given by
ym,n = FHRX Hm,nxm,n + FHRX nm,n ∈ CR×1, (3)
where FRX ≜ FARX FDRX, FARX ∈ CL×R and FDRX ∈ CR×R
denote the receive analog and digital combining matrices,
respectively. The non-zero elements of FARX are also sub-
jected to the constant module constraint. Hm,n is the discrete
frequency domain sensing channel, which will be given in
the following subsection. The notation nm,n denotes the
additive white Gaussian noise (AWGN). Then, we multiply
the received signal vector by the conjugate of the transmitted
data to eliminate its impacts, i.e.,
˜ym,n = s∗m,nym,n = FHRX Hm,nfT X+ ˜nm,n, (4)
R
/LR
/LR
Digital 
Precoding/Combining
Analog
Precoding/Combining
Baseband 
Signal 
Processing
N-point
IFFT/FFT
Add/Remove 
CP
RF 
Chain
N-point
IFFT/FFT
Add/Remove 
CP
RF 
Chain
    
    
    
  
Fig. 2. Partially-connected HBF structure.
where fT X ≜ FT Xe, and ˜nm,n ≜ s∗m,nFHRX nm,n is the
equivalent noise.
B. Sensing Channel Model
We assume that there are K UA Vs in the cooperative
ISAC system. In order to derive the positions and velocities
of the UA Vs in 3-D space, each BS is equipped with an
uniform planar array (UPA) with P and Q antennas located
in horizontal and vertical direction, respectively. Thus, the
horizontal and vertical steering vector can be respectively
represented as
ap (θk, ϕk) =
h
1, . . . , ej2π(P −1)d sin(θk) cos(ϕk)/λ
iT
∈ CP ×1,
(5)
aq (θk) =
h
1, . . . , ej2π(Q−1)d cos(θk)/λ
iT
∈ CQ×1, (6)
where d and λ denote the antenna spacing and the wavelength,
respectively. The notations θk and ϕk denote the elevation and
azimuth angles of the k-th UA V , respectively. For notational
simplicity, we define the virtual angles as ϑ ≜ sin(θ) cos(ϕ)
and ψ ≜ cos(θ). In this way, the steering vector of UPA can
be rewritten in a compact form as
a (ϑk, ψk) = aq (ψk) ⊗ ap (ϑk) ∈ CP Q×1. (7)
For the considered low-altitude sensing scenario, we assume
that there always exists the line-of-sight (LoS) paths between
the BSs and the UA Vs, while the echo signals reflected by
other scatterers are very weak. In addition, we ignore the sig-
nals from other BSs (including those transmitted by other BSs
and then reflected by the UA Vs to the current BS). Because
in the case of multi-BS frequency division configuration, the
signals from other BSs can be effectively suppressed by each
BS designing its own frequency band filter before receiving
the echo signals. Thus, the time and delay domain sensing
channel can be expressed as
H(t, τ) =
KX
k=1
αkδ (τ − τk) a (ϑk, ψk) a (ϑk, ψk)H · ej2πf dk t,
(8)
where αk denotes the channel coefficient, τk = 2dkc0 and
f dk = 2vkλ are the echo delay and the Doppler frequency shift
caused by the k-th UA V , respectively. The notationc0 denotes
the speed of light. The notations dk and vk denote the range

<!-- extraction_page_index: 4 -->

4
between the k-th UA V and the BS and its radial velocity to the
BS, respectively. Then, by performing the Fourier transform
(FT) of delay τ and sampling the received signal at the n-th
OFDM symbol, the discrete frequency domain channel can be
expressed as
Hm,n =
KX
k=1
αka (ϑk, ψk) a (ϑk, ψk)H ·e−j2πm∆f τk ·ej2πf dk nTs .
(9)
III. P RELIMINARY STEPS FOR
THE COOPERATIVE SENSING SCHEME
To enhance the practicality of the proposed cooperative
sensing scheme, we present several preliminary steps to pro-
vide some prior information and guidelines for the subsequent
sensing scheme.
A. Beam Scanning and UA V Detection
It should be noted that in the scenario where the UA Vs are
close to the BSs (e.g., less than a hundred meters), the signal-
to-noise ratio (SNR) of the echo signals is sufficient to meet
the requirements of UA V detection and parameter estimation.
In such cases, precise localization of UA Vs can be achieved
directly through the parameter estimation schemes without
additional beam scanning or alignment procedures. However,
by considering the scenario where the UA Vs may be far
from the BSs, the following beam scanning and alignment are
required to counteract the severe path loss, thereby improving
the SNR to facilitate the subsequent parameter estimation.
As shown in Fig. 3(a), we first determine the approximate
locations of the UA Vs via beam scanning. To further enhance
the SNR of the received signals, we combine all the received
symbols on each RF chain. In this way, the received signal
can be expressed as
ˇym,n = eT ˜ym,n = f HRX Hm,nfT X+ ˇnm,n, (10)
where fT X and fRX ≜ FRX e respectively represent the
equivalent beamforming vector and combining vector, e =
[1, . . . ,1]T ∈ RR×1 denotes an all-one vector, and ˇnm,n
denotes the equivalent noise. During the beam scanning period,
we assume that
fRX (θi, ϕj) = fT X(θi, ϕj) =
s
PT
P Qa (ϑi, ψj) , (11)
where PT denotes the transmit power of BS, and
θi = θ0 + i∆θ, i = 0, . . . , NH − 1, (12a)
ϕj = ϕ0 + j∆ϕ, j = 0, . . . , NV − 1, (12b)
where θ0 and ϕ0 denote the initial scan angles, ∆θ and ∆ϕ
denote the scan angle steps, i and j denote the beam indices,
NH and NV respectively denote the number of beams on
horizontal and vertical directions, and the total number of
scan beams is give by NHNV. The equivalent beamforming
and combining design in (11) can be simply achieved by
setting the digital precoding/combining matrix to the identity
matrix and filling the non-zero elements of the analog precod-
ing/combining matrix with the steering vector at (θi, ϕj).
To detect the presence of UA Vs within the beam range,
we formulate the following binary hypothesis testing (BHT)
problem as [23]
ˇym,n =
 H0 : ˇnm,n,
H1 : f HRX Hm,nfT X+ ˇnm,n, (13)
where the null hypothesis ( H0) assumes that the BS receives
only noise, whereas the alternative hypothesis ( H1) suggests
that the BS receives both the reflected echo signals and noise.
To solve the above BHT problem, we first need to construct a
detector T (·) to map ˜ym,n to a real number, and then compare
it with a predefined threshold γ to determine whether to accept
H0 or H1 [23], i.e.,
T (ˇym,n)
H1
≷
H0
γ. (14)
By considering the particular scenarios and available prior
knowledge, various hypothesis testing methods such as likeli-
hood ratio test (LRT) can be utilized to develop a detector [24].
For further manipulation, we introduce {di,j}NH−1,NV−1i=0,j=0 as the
detection flag. Specifically, if the UA Vs are detected within
the beam range with index (i, j), then di,j = 1 ; otherwise,
di,j = 0.
B. Estimation of the Number of UA Vs
For the beam range where the presence of UA Vs is detected
(i.e., di,j = 1), it is necessary to further estimate the number
of UA Vs within the beam range, which can be achieved by
considering the information theoretic criteria [4]. Specifically,
we first estimate the covariance of the received signal ˜ym,n
as
ˆR = 1M N
M −1X
m=0
N −1X
n=0
˜ym,n ˜yHm,n ∈ CR×R. (15)
Then, we perform the singular value decomposition (SVD)
of ˆR, i.e., ˆR = UΛUH, where Λ = D([ λ1, . . . , λR]) is
a diagonal matrix with the eigenvalues sorted in descending
order, i.e., λ1 ≥ λ2 ≥ · · · ≥λR. Subsequently, by adopting the
minimum description length (MDL) criterion [25], the number
of UA Vs within the beam range is estimated as 1
Ki,j = arg min
k∈{1,...,R−1}
MDL(k), (16)
with
MDL(k) = − ln
 QR
i=k+1 λ1/(R−k)i
1
R−k
PR
i=k+1 λi
!(R−k)M N
+ 12 k(2R − k) ln (M N) .
(17)
1Noting that we assume that the UA Vs outside the current beam range will
not be detected by the side lobes of the current beam. This is because the
side lobe power is much less than the main lobe power. Additionally, we can
further eliminate the redundant detections of the same UA Vs within adjacent
beams via the pruning procedures proposed in [4].

<!-- extraction_page_index: 5 -->

5
x
y
BS
0θ
θ∆
1θ
H 1Nθ −
BS
(a) Beam scanning.
 
RF 
Chain
 
RF 
Chain
 
 
RF 
Chain
 
RF 
Chain
 
  (b) Beam alignment.
Fig. 3. An illustration of the beam scanning and alignment.
C. Beam Alignment
After the aforementioned steps, the approximate locations
of the UA Vs in 3-D space can be determined by recording the
indices of elements that are equal to 1 in {di,j}NH−1,NV−1i=0,j=0 ,
and the total number of UA Vs can be derived by summing up
the estimated number of UA Vs in each beam range as
K =
NH−1,NV−1X
i=0,j=0
di,jKi,j, (18)
which provide valuable prior information and guidelines for
the subsequent monostatic parameter estimation. Specifically,
as illustrated in Fig. 3(b), we divide the entire antenna ar-
ray into N ′ = PNH−1,NV−1i=0,j=0 di,j groups with each group
formulating the beam aligned with the directions of (θi, ϕj).
For instance, we can assume that digital precoding matrix
as the identity matrix, while the non-zero elements of the
analog precoding matrix are filled with the normalized steering
vectors corresponding to the direction of (θi, ϕj). However,
the non-zeros elements of the combining matrix are chosen
uniformly from a normalized unit circle to mitigate the AoA
estimation ambiguity caused by the dimensional reduction
in the HBF structure. Noting that the aforementioned beam-
related steps have been widely studied and are not the focus
of this paper, in the following part of this paper, we assume
that the required prior information, i.e., the beam detection
flag {di,j}NH,NVi=1,j=1 and the total number of the UA Vs K, have
been accurately derived via the aforementioned steps.
IV. T ENSOR DECOMPOSITION APPROACH FOR
PARAMETER ESTIMATION
In this section, we begin by providing several preliminaries
of tensor. Then, we formulate the parameter estimation prob-
lem via using a tensor decomposition model. Subsequently,
a parameter estimation scheme based on spatial smoothing
tensor decomposition is developed. Finally, we discuss the
uniqueness and complexity of the tensor decomposition steps.
A. Tensor Preliminaries
To enhance the readability of this paper, some basic theory
and key definitions about tensor are provided. We recommend
the readers to refer to [26] for more details.
1) Unfolding: Mode-n unfolding of a tensor X ∈
CI1×I2×···×IN denotes that one rearranges the tensor to a
matrix. Specifically, tensor element (i1, i2, . . . , iN ) maps to
matrix element (in, j), where
j = 1 +
NX
k=1
k̸=n
(ik − 1) Jk, with Jk =
k−1Y
m=1
m̸=n
Im. (19)
2) Rank-1 Tensor: An N-th-order tensor X is a rank-1
tensor if it can be expressed as the outer product of N vectors,
i.e.,
X = a(1) ◦ a(2) ◦ · · · ◦a(N ). (20)
3) CP decomposition: CANDECOMP/PARAFAC (CP) de-
composition denotes that one decomposes a tensor into a sum
of component rank-1 tensors, i.e.,
X =
RX
r=1
λra(1)r ◦ a(2)r ◦ · · · ◦a(N )r , (21)
where R denotes the rank of X . The corresponding fac-
tor matrix to the n-th mode is defined as A(n) =h
a(n)1 , . . . ,a(n)R
i
, n= 1 , . . . , N. The mode- n unfolding ver-
sion of X is given by
X(n) =
A(n)Λ A(N ) ⊙ · · · ⊙A(n+1) ⊙ A(n−1) ⊙ · · · ⊙A(1)T ,
(22)
where Λ = D ([λ1, . . . , λR]).
B. Tensor F ormulation
Recalling the expression of the received signal and the
channel model provided in Section II, we find that the
AoAs, Doppler shifts and time delays caused by the UA Vs
independently affect the received signal in spatial, time and
frequency dimensions, which prompts us to formulate the
multi-dimensional parameter estimation via using a tensor
decomposition model. Specifically, by substituting (9) into (4)
and stacking the received signal among N OFDM symbols
and M subcarriers, it is readily verified that the received signal
vector ˜ym,n can be formulated into a third-order tensor as
Y =
KX
k=1
αkb (ϑk, ψk) ◦ o
 
f dk  ◦g (τk) + N ∈ CR×N ×M ,
(23)
where N ∈ CR×N ×M is the equivalent noise tensor, K
denotes the total number of UA Vs, which can be derived by
the preliminary steps provided in Section III, and
b (ϑk, ψk) = FHRX a (ϑk, ψk) a (ϑk, ψk)H fT X∈ CR×1,
(24)
o
 
f dk  = h1, ej2πTsf dk , ..., ej2π(N −1)Tsf dk iT ∈ CN ×1, (25)
g (τk) =
h
1, e−j2π∆f τk , ..., e−j2π(M −1)∆f τk
iT
∈ CM ×1,
(26)

<!-- extraction_page_index: 6 -->

6
respectively. The corresponding factor matrices of Y are given
by
A(1) = [b(ϑ1, ψ1), . . . ,b(ϑK, ψK)] ∈ CR×K, (27)
A(2) = o(f d1 ), . . . ,o(f dK) ∈ CN ×K, (28)
A(3) = [α1g(τ1), . . . , αKg(τK)] ∈ CM ×K. (29)
Then, the tensor decomposition model is given by
min
A(1),A(2),A(3)
Y − KXk=1 αkb (ϑk, ψk) ◦ o  f dk  ◦g (τk)2F .(30)
C. Factor Matrices Recovery
Instead of solving Problem (30) via the well-known alter-
native least square (ALS) method [17], we recover the factor
matrices by leveraging the Vandermonde structure of A(3).
For notational simplicity, the noise component is ignored in
the following derivations. First, the mode-1 unfolding of the
third-order tensor Y can be expressed as [26]
YT(1) = A(3) ⊙ A(2) A(1)T ∈ CM N×R. (31)
Then, we choose a pair of integer {L1, L2} satisfying L1 +
L2 = M + 1 and define the following cyclic choose matrix as
Jl =

0L1×(l−1), IL1 , 0L1×(L2−l)

∈ CL1×M . (32)
We then smooth the mode-1 unfolding of Y as
YS = h(J1 ⊗ IN ) YT(1), . . . ,(JL2 ⊗ IN ) YT(1)i
(a)
=

A(L1,3) ⊙ A(2)
 
A(L2,3) ⊙ A(1)
T
∈ CL1N ×L2R,
(33)
where A(L,3) denotes the 1 to L rows of A(3). Equation (a)
is derived by leveraging the property of Khatri-Rao product,
i.e., (A ⊗ B) (C ⊙ D) = ( AC) ⊙ (BD) [27] and the Van-
dermonde structure of A(3), while the details are omitted due
to the space limitations. We then perform the truncated SVD
of YS as
YS = UΣVH , (34)
where U ∈ CL1N ×K, Σ ∈ CK×K and V ∈ CL2R×K. Given
that the columns of U span the same subspace as the columns
of YS, there always exists a full rank matrix M ∈ CK×K
satisfying [28]
A(L1,3) ⊙ A(2) = UM ∈ CL1N ×K, (35)
A(L2,3) ⊙ A(1) = V∗ΣM−T ∈ CL2R×K. (36)
Noting the Vandermonde structure of A(L1,3), we have

A(L1,3) ⊙ A(2)

Z = A
(L1,3) ⊙ A(2), (37)
where Z = D
 
[e−j2π∆f τ1 , . . . , e−j2π∆f τK ], A(L1,3) and
A
(L1,3) denote the deletions of the last row and the first row
of A(L1,3), respectively. Then, one obtains
A(L1,3) ⊙ A(2) = U1M, (38)
A
(L1,3) ⊙ A(2) = U2M, (39)
where U1 = U1:(L1−1)N,: denotes the 1 to (L1 − 1) N rows
of U, and U2 = UN +1:L1N,: denotes the N + 1 to L1N rows
of U, respectively. Then, combining (38), (39) with (37), we
have
U1MZ = U2M ⇒ MZM−1 = U†1U2 ≜ Ξ. (40)
Thus, by performing the eigenvalue decomposition (EVD)
of Ξ, we can derive the estimations of Z and M.
Since the normalized diagonal elements of Z, i.e., ˆzk =
[Z]k,k /| [Z]k,k |, k= 1, . . . , Kare actually the generators of
A(3), each column of A(3) can be recovered as
ˆa(3)k = 1, ˆzk, . . . ,ˆzM −1k T , k= 1, . . . , K.(41)
Then, recalling the definition of Khatri-Rao product, we have
A(L1,3)⊙A(2) = ha(L1,3)1 ⊗ a(2)1 , . . . ,a(L1,3)K ⊗ a(2)K i = UM.
(42)
Thus, given ˆA(L1,3) and M, each column of A(2) can be
derived as [28]
a(2)k (a)=

 a(L1,3)k Ha(L1,3)k 22 ⊗ IN

 a(L1,3)k ⊗ a(2)k 
(b)
=

 a(L1,3)k Ha(L1,3)k 22 ⊗ IN

 Umk, k= 1, . . . , K,
(43)
where (a) is obtained by using the mixed-producted property
of Kronecker product, i.e., (A ⊗ B)(C ⊗ D) = AC ⊗ BD,
(b) is based on (42), and mk denotes the k-th column of M.
Similarly, letting P ≜ M−T , we can recover each column of
A(1) as [28]
a(1)k (a)=

 a(L2,3)k Ha(L2,3)k 22 ⊗ IR

 a(L2,3)k ⊗ a(1)k 
(b)
=

 a(L2,3)k Ha(L2,3)k 22 ⊗ IR

 V∗Σpk, k= 1, . . . , K,
(44)
where pk denotes the k-th column of P.
D. Parameter Estimation
In this subsection, we estimate the parameters from the
recovered factor matrices. First, the estimation of the time
delay {τk}Kk=1 can be derived from the generators of A(3),
i.e.,
ˆτk = ∡ˆzk−2π∆f , (45)
where ∡ˆzk denotes the angle of ˆzk. The estimation of the
range {dk}Kk=1 between the UA Vs and the BS can be derived
as
ˆdk = ˆτkc02 . (46)

<!-- extraction_page_index: 7 -->

7
The estimation of the Doppler frequency shift {f dk }Kk=1 can
be derived by the following correlation-based scheme as [17]
ˆf dk = arg maxf dk
ˆoHk o  f dk 2 , (47)
where ˆok denotes the k-th column of ˆA(2). The radial velocity
{vk}Kk=1 of the UA Vs to the BS can be estimated as
ˆvk =
ˆf dk λ
2 . (48)
Similarly, the estimation of {ϑk, ψk}Kk=1 can be derived as
{ ˆϑk, ˆψk} = arg maxϑ,ψ
ˆbHk b(ϑ, ψ)2
∥b(ϑ, ψ)∥22 , (49)
where ˆbk denotes the k-th column of ˆA(1). Noting that
Problem (47) can be directly solved by the one-dimensional (1-
D) search method. However, performing the two-dimensional
(2-D) search method in (49) will result in a heavy com-
putational burden. Thus, we develop a low-complexity AoA
estimation algorithm based on GRQ to address Problem (49).
Specifically, the objective function (OF) of Problem (49)
can be rewritten as (52) shown at the bottom of this page,
where equation (a) is derived by eliminating the common
factor a (ϑ, ψ)H fT Xf HT Xa (ϑ, ψ) from both the numerator and
denominator, equation (b) comes from the reformulation of
a (ϑ, ψ). In specific, we have
a (θ, ψ) = (aq (ψ) · 1) ⊗ (Ipap (θ))
= (aq (ψ) ⊗ Ip) ap (θ) , (50)
which can be derived by leveraging the mixed-producted
property of Kronecker product, i.e., (A ⊗ B) (C ⊗ D) =
AC ⊗ BD. Equation (c) is obtained by defining
Qk1(ψ) ≜ [aq(ψ) ⊗ IP ]H FRX ˆbk ˆbHk FHRX [aq(ψ) ⊗ IP ] ,
(51a)
Qk2 (ψ) ≜ [aq(ψ) ⊗ IP ]H FRX FHRX [aq(ψ) ⊗ IP ] , (51b)
respectively. Then, Problem (49) can be reformulated as
max
ϑ,ψ
ap(ϑ)H Qk1(ψ)ap(ϑ)
ap(ϑ)H Qk2(ψ)ap(ϑ) . (53)
Noting that with fixed ψ, Problem (53) has a well-known GRQ
form [27]. It is readily verified that ap(ϑ) is an eigenvector
of the matrix Φk (ψ) ≜  Qk2(ψ)† Qk1(ψ), and the OF value
of Problem (53) is the corresponding eigenvalue of Φk (ψ).
Consequently, we estimate ψk as
ˆψk = arg maxψ λmax{Φk (ψ)}, (54)
where λmax{·} denotes the maximum eigenvalue of a matrix,
and the above problem can be solved by the 1-D search
method. At the first glance, performing the EVD of Φk (ψ)
to obtain the maximum eigenvalue of Φk (ψ) on several grids
will still incur considerable calculation burden. However, the
following lemma proves that the EVD of Φk (ψ) on each grid
is unnecessary.
Lemma 1 : Problem (54) is equivalent to the following
problem:
ˆψk = arg maxψ Tr Φk (ψ) . (55)
Proof: According to the expression of (51a), it is readily
verified that the rank of Qk1 (ψ) is 1. Then, based on the
property of the rank of matrix multiplication [27], i.e.,
rank (AB) ≤ min {rank (A) , rank (B)} , (56)
we can prove that the rank of Φk (ψ) is always 1. In addition,
according to the property of rank-1 matrix [27], we have
Tr
 
Φk (ψ) = λ, (57)
where λ denotes the unique non-zero eigenvalue of Φk (ψ).
Additionally, it is readily verified that Φk (ψ) is a positive
semi-definite matrix, thus, we have Tr
 
Φk (ψ) = λ =
λmax

Φk (ψ)	 and the proof is completed. ■
According to Lemma 1, we address Problem (55) to
estimate ψk by the 1-D search method. Subsequently, the
estimation of ap (ϑ) is given by the eigenvector corresponding
to the maximum eigenvalue of Φk( ˆψk). We let ˆap(ϑ) ←
ˆap(ϑ)/[ˆap(ϑ)]1 to eliminate the scaling ambiguity brought by
the EVD, where [·]1 denotes the first element of a vector. Then,
we estimate ϑk as
ˆϑk = arg minϑ ∥ap (ϑ) − ˆap (ϑ)∥2 , (58)
which can still be solved by the 1-D search method. The
detailed procedures of the proposed GRQ-based algorithm
are summarized in Algorithm 1. Then, the estimation of the
elevation and azimuth angles can be derived as
ˆθk = arc cos(ˆψk), (59)
ˆϕk = arc cos
 ˆϑk
sin(ˆθk)
!
. (60)
Finally, we eliminate the scaling ambiguity and estimate the
channel coefficients as [18]
[Λ1]k,k = b†

ˆϑk, ˆψk

ˆbk, (61a)
[Λ2]k,k = o†

ˆf dk

ˆok, (61b)
Λ3 = (Λ1)−1 (Λ2)−1 , (61c)
ˆαk =

[Λ3]k,k g (ˆτk)
†
ˆgk. (61d)
f (ϑ, ψ) =
ˆbHk FHRX a (ϑ, ψ) a (ϑ, ψ)H fT Xf HT Xa (ϑ, ψ) a (ϑ, ψ)H FRX ˆbk
f HT Xa (ϑ, ψ) a (ϑ, ψ)H FRX FHRX a (ϑ, ψ) a (ϑ, ψ)H fT X
(a)
= a (ϑ, ψ)H FRX ˆbk ˆbHk FHRX a (ϑ, ψ)
a (ϑ, ψ)H FRX FHRX a (ϑ, ψ)
(b)
= ap(ϑ)H [aq(ψ) ⊗ IP ]H FRX ˆbk ˆbHk FHRX [aq(ψ) ⊗ IP ] ap(ϑ)
ap(ϑ)H [aq(ψ) ⊗ IP ]H FRX FHRX [aq(ψ) ⊗ IP ] ap(ϑ)
(c)
= ap(ϑ)H Qk1(ψ)ap(ϑ)ap(ϑ)H Qk2(ψ)ap(ϑ) . (52)

<!-- extraction_page_index: 8 -->

8
Algorithm 1 GRQ-Based Method to Solve Problem (49)
1: Estimate ψk in (55) by the 1-D search method;
2: Calculate the maximum eigenvalue of Φk( ˆψk) and the
corresponding eigenvector ˆap(ϑ);
3: Calculate ˆap(ϑ) ← ˆap(ϑ)/[ˆap(ϑ)]1 to eliminate the scal-
ing ambiguity;
4: Estimate ϑk in (58) by the 1-D search method.
The detailed procedures of the tensor-based parameter estima-
tion scheme are summarized in Algorithm 2.
E. Uniqueness Analysis
In this subsection, we discuss the uniqueness of the above
tensor decomposition, which guarantees the correct recovery
of the factor matrices and the subsequent parameter estima-
tion. A well-known Kruskal sufficient uniqueness condition is
provided in [29]. In addition, by leveraging more structural
information of factor matrices, the uniqueness can be further
relaxed as [16], [28]
Lemma 2: Let X ∈ CI1×I2×I3 be a tensor with three factor
matrices A(1) ∈ CI1×K, A(2) ∈ CI2×K and A(3) ∈ CI3×K,
where A(3) is a Vandermonde matrix with distinct generators
{zk}Kk=1. Denote kA as the Kruskal-rank of matrix A, if(
k(A(L1 ,3)⊙A(2)) = K,
k(A(L2 ,3)⊙A(1)) = K, (62)
then the rank of X is K, and the tensor decomposition is
unique. In the generic case, condition (62) becomes
min ((L1 − 1) I2, L2I1) ≥ K. (63)
Proof: Please refer to [28]. ■
Recalling the formulation of Y, the notations I1, I2 and
I3 in Lemma 2 respectively denote the number of RF chains
R, the number of OFDM symbols N, and the number of
subcarriers M. Since there are a large number of subcarriers
in current MIMO-OFDM systems, we can readily choose
a pair of integer {L1, L2} satisfying L1 + L2 = M + 1,
(L1 − 1) I2 = ( L1 − 1)N ≥ K and L2I1 = L2R ≥ K.
Therefore, the uniqueness condition can be readily satisfied. In
addition, the uniqueness implies that the AoAs, Doppler shifts,
and time delays will automatically be associated with the same
target without designing additional pairing procedures [28].
F . Complexity Analysis
We next analyze the complexities of the steps in Algorithm
2. It should be pointed out that the complexity of step 2 is
negligible, since we can leverage the property of the sparse
cyclic choose matrices, i.e., Jl to collect specific rows of YT(1)
and stack them into the extended matrix YS instead of actually
multiplying YT(1) by Jl. At step 3, we perform the truncated
SVD of YS, which has the complexity of O (L1N KL2R).
At step 4, performing the EVD of Ξ incurs the complexity
of O
 
K 3. From step 5 to step 6, the reconstruction of A(3)
mainly requires the complexity of O (KM ). Next, the total
complexity of the reconstruction of A(2) and A(1) is given by
Algorithm 2 Spatial Smoothing Tensor Decomposition Ap-
proach For Parameter Estimation
1: Mode-1 unfold Y as (31);
2: Choose {L1, L2} and smooth YT(1) to YS as (33);
3: Perform the SVD of YS as (34);
4: Perform the EVD of Ξ as (40);
5: Calculate the generators ˆzk = [ Z]k,k/|[Z]k,k|, K =
1, . . . , K;
6: Construct each column of A(3) by ˆg(τk) =
1, ˆzk, . . . ,ˆzM −1k T , k= 1, . . . , K;
7: Construct each column of A(2) via (43);
8: Construct each column of A(1) via (44);
9: Derive the time delay {ˆτk}Kk=1, range { ˆdk}Kk=1, Doppler
frequency shift { ˆf dk }Kk=1, radial velocity {ˆvk}Kk=1, eleva-
tion angle {ˆθk}Kk=1 and azimuth angle { ˆϕk}Kk=1 via (45),
(46), (47), (48), (59) and (60), respectively.
10: Eliminate the scaling ambiguity and estimate the channel
coefficients via (61a), (61b), (61c) and (61d), respectively.
y
z
x
z
x
B
j
Local coordinate’s axis
Global coordinate’s axis
BS j
y
x
Fig. 4. The relationship between the local and the global coordinate.
O
 
L1N 2K + L1N K2 + L2R2K + L2RK 2. In the stage of
parameter estimation, the derivations of { ˆf dk }Kk=1 has the
complexity of O (N GK), and the complexity of Algorithm
1 is given by O
 
P 3GK + P GK, where G denotes the
grid size. Finally, step 10 mainly has the complexity of
O ((R + M + N ) K). Thus, the total complexity of Algo-
rithm 2 can be expressed as O
 
L1N KL2R + K 3 + KM +
L1N 2K + L1N K2 + L2R2K + L2RK 2 + N GK+ P 3GK.
V. P OSITION AND VELOCITY ESTIMATION
In this section, we enhance the positioning accuracy of
the UA Vs and recover their true velocities through the multi-
BS cooperation, as the above monostatic parameter estima-
tion method can only derive the UA Vs’ radial velocities.
Specifically, we first develop a false removing MST-based
data association method, and then estimate the positions and
velocities of the multiple UA Vs relying on the parameters es-
timated by the BSs, i.e., {ˆθk,j , ˆϕk,j , ˆdk,j , ˆvk,j }K,Jk=1,j=1, where
the subscript j denotes the BS’s index.
A. False Removing MST-Based Data Association
Noting that in conventional device-based sensing for active
targets that can send/receive RF signals with different signa-
tures, the BSs know the exact mapping between the estimation
parameters of a certain target, i.e., each BS knows the true

<!-- extraction_page_index: 9 -->

9
1
2 3
7
9 8
5
4
10 11
6
12
Isolated vertex
UAV1
UAVk
UAVK
BS1 Estimation BS3 Estimation
BS2 Estimation BS4 Estimation
BS1 Estimation BS3 Estimation
BS2 Estimation BS4 Estimation
Fig. 5. An illustration of the MST of graph ˜G.
indices for all K UA Vs. However, in the considered device-
free sensing scenario, the detected UA Vs’ indices may be
different across BSs. Thus, before performing the data fusion,
we develop a false removing MST-based data association
method. The initial phase of data association involves each
BS roughly estimating the positions of K UA Vs relying on
the AoA and range estimations, i.e., {ˆθk,j , ˆϕk,j , ˆdk,j }K,Jk=1,j=1.
Specifically, the k-th UA V’s position estimated by BSj is given
by
ˆpk,j = ˆdk,jˆrk,j + pBj , (64)
where pBj denotes the position of BSj in the global coordinate,
and
ˆrk,j = T  ϕBj 

 sin

ˆθk,j

cos

ˆϕk,j

sin

ˆθk,j

sin

ˆϕk,j

cos

ˆθk,j


 , (65)
is the direction vector in the global coordinate. The notation
T
 
ϕBj  denotes the transform matrix from the BS j’s local
coordinate to the global coordinate. Without loss of generality,
as shown in Fig. 4, we assume that the antenna panel of each
BS is parallel to the z-axis of the global coordinate, and ϕBj is
the angle between the x-axis of the BS j’s local coordinate and
the x-axis of the global coordinate. In this way, the transform
matrix can be expressed as [7]
T
 
ϕBj  =


cos
 
ϕBj  sin  ϕBj  0
− sin
 
ϕBj  cos  ϕBj  0
0 0 1

 . (66)
Then, according to the positioning results of BSs, i.e.,
{ˆpk,j }K,Jk=1,j=1 and leveraging the similarity of positioning re-
sults for the same UA V across multiple BSs, a straightforward
association approach is to minimize the sum of the Euclidean
distances between the positioning results from different BSs
via the exhaustive permutation method [30]. However, the
complexity rises sharply with the value of K. In addition,
the permutation method does not remove the false detections,
while it is evident that integrating these false detection results
with the correct detection results will greatly impact the
following data fusion process.
To address these issues, we propose a false removing MST-
based data association method. Specifically, we first construct
an undirected weighted graph G = (V, E). The vertex set V
represents the union of a series of sub-vertex sets, i.e.,
V = V1 ∪ V2 ∪ · · · ∪VJ , (67)
BSj
Rough estimation relying 
on mean fusion
BSJ1BSx
z
y
UAVk
Lattice points 𝑈𝑈𝑘𝑘
(a) Rough position estimation rely-
ing on mean fusion.
r () kf p
d () kf p
(b) Calculate the OF values.
Fig. 6. An illustration of the Pareto optimality fusion scheme.
where Vj = {(j − 1) K + 1, . . . , jK} , j= 1, . . . , Jdenotes
the K positioning results of BS j. The edge set E is defined
as
E = {(a, b) |a ∈ Vj, b∈ V \ Vj, j= 1, . . . , J} , (68)
and the weights of edges are defined as the Euclidean distances
between the positioning results derived by BSs, i.e.,
Wab = ||ˆp(a−1) mod K+1,⌊ a−1K ⌋+1
− ˆp(b−1) mod K+1,⌊ b−1K ⌋+1||2, ∀a, b∈ E, (69)
where the notations mod and ⌊·⌋ denote the modulus and
floor operations, respectively. To prevent the false detection
results from impacting the subsequent data fusion, we define
the following edge set as
E′ = {(a, b) |Wmin (a) > ς, a, b∈ E} , (70)
where Wmin (a) > ςindicates that the shortest adjacent edge
of vertex a is longer than the threshold ς. Then, we update
the edge set as 2
˜E = E \ E′. (71)
In this way, in the updated graph ˜G = ( V, ˜E), these false
detection results are displayed as the isolated vertices. Then,
we derive the MST of the connected components of graph ˜G
via the well-known Prim [31] or Kruskal [32] algorithm. As
shown in Fig. 5, given that the positioning results of multiple
BSs for the same UA V are more similar than those for distinct
UA Vs, the MST algorithm will always connect the positioning
results of multiple BSs for the same UA V . Subsequently, by
removing K − 1 longest edges from the MST, the positioning
results from multiple BSs for K UA Vs are divided into K
sub-graphs. By collecting the vertex indices in each sub-graph,
the data association can be immediately accomplished. In the
following contents of this paper, we assume that each BS holds
the same indices of UA Vs. In addition, for a certain UA V , these
false detections and estimations derived by BSs will not be
incorporated in the data fusion, even though we still utilize
the notation J for notational simplicity.
2Assuming that BS j successfully detects the k-th UA V , there always exists
at least one another BS whose positioning result for the same UA V is similar
to the BS j’s estimation, guaranteeing Wmin (a) ≤ ς, where a denotes the
vertex corresponding to BSj’s estimation. In contrast, Wmin (a) > ςindicates
that BSj fails to detect the k-th UA V . Thus, to prevent the false detection from
impacting the following data fusion, the vertex a should be recognized as an
isolated vertex in the updated graph ˜G.

<!-- extraction_page_index: 10 -->

10
B. Position Estimation
After accurate data association, we then perform the data
fusion across the multiple BSs. In general, there are two
primary fusion strategies: hard fusion and soft fusion [7].
Specifically, the former denotes that each BS estimates and
sends the final positioning results, i.e., {ˆpk,j }K,Jk=1,j=1 to the
cloud. Then, the cloud integrates the position estimations via
the (weighted) mean fusion scheme. For instance, the position
estimation relying on mean fusion is given by
ˆpk = 1J
JX
j=1
ˆpk,j , k = 1, . . . , K. (72)
Differently, with soft fusion strategy, all BSs send the initial
parameter estimations, including the AoAs and ranges to the
cloud. Then, the cloud performs the estimation of positions
via integrating these uploaded parameters. Since soft fusion
provides more fine-grained information for the data fusion, we
mainly focus on this fusion strategy in the following contents
of this paper. Specifically, noting that the accuracy of position
estimation mainly depends on the range and radial direction
(determined by AoAs) estimations, we respectively define the
following range loss function and direction loss function as
fr (pk) =
PJ
j=1 αk,j
dk,j (pk) − ˆdk,j 
PJ
j=1 αk,j
, (73a)
fd (pk) =
PJ
j=1 αk,j ∥rk,j (pk) − ˆrk,j ∥2
PJ
j=1 αk,j
, (73b)
where dk,j (pk) =
pk − pBj 2 denotes the true range be-tween the UA V and the BS, and rk,j (pk) denotes the true
radial direction vector determined by the k-th UA Vs’ true
position pk. The notation αk,j denotes the weight assigned
to BSj. Specifically, due to path loss, the SNR of echo signals
decrease with the increase of the range between the UA V and
BSs. Thus, we define the weighting coefficient as
αk,j = 1(dk,j (pk))β1 , (74)
where β1 > 0 is a factor introduced to control the weighting
intensity. Then, we address the following problem to estimate
the position of the k-th UA V , i.e.,
min
pk
{fr (pk) , fd (pk)} , (75)
which is a highly nonlinear multi-objective optimization prob-
lem with the OFs holding the distinct dimensions. To address
Problem (75), we propose a Pareto optimality strategy to
determine the UA Vs’ positions. Specifically, as shown in
Fig. 6, we first take the mean fusion result in (72) as a
rough position estimation. Then, we construct L lattice points
around the rough estimation and calculate the two OF values
corresponding to these lattice points. To minimize both two
OF values simultaneously, we first recognize the dominated
solutions among the lattice points, i.e.,
˜Uk = {pl1k |fr(pl1k ) > fr(pl2k ), fd(pl1k ) > fd(pl2k ),
pl1k , pl2k ∈ Uk}, (76)
x
y
z
BSj
UAVk y
kv
z
kv
True
kv
x
kv
,kjv
,kjφ
,90 kjθ° −
Fig. 7. The relationship between the radial velocity and the true velocity
(assume that the global coordinate coincides with the local coordinate).
where Uk =

p1k, . . . ,pLk 	 denotes the set formed by L lattice
points. Then, we remove the dominated solutions and retain
the Pareto set of solutions as
¯Uk = Uk\ ˜Uk. (77)
Finally, we determine the solution from the Pareto set as
the final position estimation relying on the system configu-
ration. Specifically, in scenarios where each BS is allocated
a substantial number of subcarriers but only equipped with
relatively a small number of antennas, the range estimation
always exhibits a higher precision than AoA estimation. Thus,
the range estimation should be more dominant for positioning.
In such cases, we can choose the solution from the Pareto set,
which has the minimum range loss function value, i.e.,
ˆpk = arg min
plk∈ ¯Uk
fr
 
plk . (78)
On the flip side, when the BSs are equipped with a large
number of antennas but a small number of subcarriers, the
AoA estimation becomes the critical factor, guiding the choice
of the solution with minimum direction loss function value
from the Pareto set, i.e.,
ˆpk = arg min
plk∈ ¯Uk
fd
 
plk . (79)
In addition, we can also take into account the accuracy
of AoA and range estimation in the designed monostatic
parameter estimation algorithm to achieve better positioning
performance. Noting that only several simple calculations are
required to calculate the OF values corresponding to the lattice
points, so the complexity is tolerant.
C. V elocity Estimation
Noting that relying on the above positioning scheme, we
always achieve an enhanced estimation of UA Vs’ positions via
cooperation compared to the monostatic position estimation.
Thus, we can calibrate the previous AoA and range estima-
tions, i.e., {ˆθk,j , ˆϕk,j , ˆdk,j }K,Jk=1,j=1relying on the cooperative
position estimations. For notational simplicity, we continue to
use the original notations to denote the calibrated estimations.
According to the tensor decomposition procedures in Sec-
tion IV, each BS can only estimate the radial velocities of
UA Vs, i.e., {ˆvk,j }K,Jk=1,j=1. In this subsection, we estimate
the true velocity of each UA V based on {ˆvk,j }K,Jk=1,j=1 and

<!-- extraction_page_index: 11 -->

11
{ˆθk,j , ˆϕk,j }K,Jk=1,j=1. To perform the estimation, we first ex-
plore the relationship between the true velocity and the radial
velocity. As shown in Fig. 7, we denote vTruek = [vxk , vyk, vzk]T
as the true velocity of the k-th UA V , where the elements
represent the velocity components on the three coordinate
axises of the global coordinate. Then, by projecting the three
components to the radial direction, we have
ˆrTk,j vTruek = ˆvk,j + εk,j , j = 1, . . . , J, (80)
where ˆrk,j denotes the (calibrated) radial direction vector
defined by (65), and εk,j denotes the estimation error. As such,
stacking all the radial velocity estimations derived by J BSs,
(80) can be rewritten in a more compact form as
ˆΩkvTruek = ˆvk + εk, (81)
where
ˆΩk =


ˆrTk,1
...
ˆrTk,J

 , ˆvk =


ˆvk,1
...
ˆvk,J

 , εk =


εk,1
...
εk,J

 . (82)
Then, the true velocity of the k-th UA V can be derived by the
well-known weighted LS (WLS) estimation, i.e.,
ˆvTruek =  ˆΩTk Wk ˆΩk−1 ˆΩTk Wk ˆvk, (83)
where Wk = D ([ γk,1, . . . , γk,J ]) denotes the weighting
matrix with the diagonal element γk,j = 1( ˆdk,j)β2 denoting the
weight assigned to BS j’s estimation, and β2 > 0 denotes the
weighting intensity factor. However, noting that the number
of BSs in the cooperative ISAC systems is limited, which
makes the above WLS method still sensitive to the estimation
error. Therefore, we propose a more robust residual weighting-
based method to suppress the impacts of estimation error.
Specifically, the method mainly includes the following three
steps [33]:
1) Grouping BSs: Noting that to recover the true velocity, at
least three BSs’ estimations are required. Therefore, we select
all combinations from J ≥ 3 BSs including at least three BSs.
In this way, the total number of combinations is given by
I =
JX
j=3
C jJ . (84)
Then, we collect all the combinations into a set as χ =
{Xi|i = 1, . . . , I}.
2) Calculating residuals: For a certain combination, we
adopt the mentioned WLS method to derive the rough esti-
mation of the k-th UA V’s true velocity relying on the BSs’
estimations within the combination, which is denoted as ˆvik.
Then, we calculate the residuals among all BSs, i.e.,
Res (Xi) =
JX
j=1
γk,j
 ˆrTk,j ˆvik − ˆvk,j 2, i= 1, . . . , I.(85)
3) Weighting the estimations based on the residuals: Relying
on the calculated residuals, the true velocity is estimated as
ˆvTruek =
PI
i=1
n
Res (Xi)−1 ˆvik
o
PI
i=1 Res (Xi)−1 . (86)
Algorithm 3 Cooperative Position and Velocity Estimation
Scheme
1: Multi-BS data association:
2: Calculate the UA Vs’ positions {ˆpk,j }K,Jk=1,j=1 via (64);
3: Construct graph G with {ˆpk,j }K,Jk=1,j=1;
4: Update graph ˜G by removing the false detection results
via (71);
5: Derive the MST of graph ˜G;
6: Remove the K −1 longest edges from the MST and collect
the vertex indices in each sub-graph.
7: Position estimation:
8: Derive the rough position estimation {ˆpk}Kk=1 via (72);
9: Construct L lattice points Uk around the rough position
estimation;
10: Calculate the two OF values corresponding to lattice
points Uk via (73a) and (73b);
11: Remove the dominated solutions and retain the Pareto set
¯Uk via (77);
12: Estimate the UA Vs’ positions via (78) or (79).
13: Velocity estimation:
14: Calibrate the previous AoA and range estimations, i.e.,
{ˆθk,j , ˆϕk,j , ˆdk,j }K,Jk=1,j=1relying on the cooperative posi-
tion estimations;
15: Group the BSs and adopt the WLS method to derive the
rough estimation of UA Vs’ true velocity;
16: Calculate the residuals of each combination of BSs via
(85);
17: Weight the estimations with residuals via (86).
As previously stated, the number of BSs in cooperative ISAC
systems is often limited, so the computational complexity of
the above method is tolerant. When the number of BSs is
large, we can adopt several existing greedy strategies to further
reduce the complexity [34].
Based on the above discussions, the detailed procedures
of the overall cooperative position and velocity estimation
method are summarized in Algorithm 3.
VI. E XTENSION TO THE DUAL-POLARIZED SYSTEM
In this section, we extend the proposed tensor decomposi-
tion parameter estimation scheme to the dual-polarized system.
Specifically, the sensing channel matrix is modified as [35]
Hm,n =
"
H(Vr,Vt)m,n H(Vr,Ht)m,n
H(Hr,Vt)m,n H(Hr,Ht)m,n
#
∈ C2P Q×2P Q, (87)
where H(Vr,Vt)m,n ∈ CP Q×P Qdenotes the sub-channel matrix
between the vertical (V)-polarized transmit antennas and V-
polarized receive antennas (for monostatic sensing scenario,
the transmit antennas are also served as the receive antennas),
and likewise for the other three blocks in (87). For notational
simplicity, let δ ∈ {Vr, Hr} and η ∈ {Vt, Ht}. Then, similar

<!-- extraction_page_index: 12 -->

12
to the channel modeling in Section II-B, the (δ, η) -th sub-
channel matrix is modeled as
Hδ,ηm,n
=
KX
k=1
β(δ,η)k a (ϑk, ψk) a (ϑk, ψk)H · e−j2πm∆f τk · ej2πf dk nTs ,
(88)
where
β(δ,η)k = αkγ(δ,η)k , (89)
and γ(δ,η)k denotes the polarization factor [35]. In order to
formulate the received signal into a forth-order tensor, we set
the transmit precoding and the receive combining matrices for
both V-polarized and H-polarized channels to be same. In this
way, the equivalent transmit precoding and receive combining
matrices for dual-polarization are respectively given by
˜FRX =I2 ⊗ FRX ∈ C2P Q×2R, (90a)
˜FT X=I2 ⊗ FT X∈ C2P Q×2R. (90b)
To avoid the interference between dual-polarization, we as-
sume that both dual-polarized channels share the same trans-
mitted data. Then, the received signal vector of each polariza-
tion can be expressed as
yδm,n = FHRX Hδm,n ˜FT X˜e · sm,n + FHRX nδm,n ∈ CR×1, (91)
where Hδm,n = hH(δ,Vt)m,n , H(δ,Ht)m,n i , δ∈ {Vr, Hr}, and ˜e =
[1, . . . ,1]T ∈ R2R×1 denotes an all-one vector. Similarly, we
still multiply the received signal vector by the conjugate of
the transmitted data to eliminate its impacts, i.e.,
˜yδm,n = s∗m,nyδm,n = FRX Hm,n ˜FT X˜e + ˜nδm,n ∈ CR×1.
(92)
Then, stacking the received signal ˜yδm,n among dual polariza-
tion, N OFDM symbols and M subcarriers into the following
forth-order tensor as
Z =
KX
k=1
αkb (ϑk, ψk) ◦ηk ◦ g (τk) ◦ o
 
f dk  + N , (93)
where ηk =
h
γ(Vr,Vt)k + γ(Vr,Ht)k , γ(Hr,Vt)k + γ(Hr,Ht)k
iT
, and
the corresponding factor matrix introduced by the dual-
polarization is given by
B = [η1, . . . ,ηK] ∈ C2×K. (94)
The mode-1 unfolding of Z is given by
ZT(1) = A(3) ⊙ A(2) ⊙ B A(1)T ∈ C2N M×R. (95)
Similarly, by defining the combining factor matrix as
E ≜ A(2) ⊙ B, (96)
we can perform the tensor decomposition procedures proposed
in Section IV to recover the factor matrices, i.e, A(1), A(3)
and E. The decoupling of A(2) and B are as follows. Let
ˆEk = unvec2×N (ˆek), where ˆek denotes the k-th column ofˆE. Then, each column of A(2) and B can be estimated by
addressing the following problem as [19]
{ˆok, ˆηk} = arg minok,ηk
 ˆEk − ηkoTk 2F , (97)
x
UAV
BS UPA Panel
y
1r
2r
Fig. 8. The top view of simulation layout.
which can be solved via performing the SVD of ˆEk. Specif-
ically, according to Eckart–Young–Mirsky theorem [36], we
have ˆηk = λk,1uk,1 and ˆok = v∗k,1, where λk,1, uk,1
and vk,1 denote the maximum singular value of ˆEk, the
corresponding left singular vector, and the corresponding right
singular vector, respectively. Subsequently, we can estimate the
multiple parameters from the recovered matrices as discussed
in Section IV-D.
VII. N UMERICAL SIMULATIONS
In this section, simulation results are presented to evaluate
the performance of the proposed schemes. We first provide
the simulation parameter settings. Then, we compare the
performance of the proposed monostatic parameter estimation
scheme with that of conventional techniques. Subsequently,
we demonstrate the performance of the cooperative position
and velocity estimation. Finally, we evaluate the generality of
the proposed scheme in a degraded scenario and compare its
performance with the state-of-the-art scheme.
A. Simulation Settings
Unless stated otherwise, the simulation parameters are set
as follows: Each BS is equipped with a half-wavelength UPA
with P = 16 and Q = 24 antennas located in horizontal
and vertical direction, respectively. The number of RF chains
is given by R = 64. The non-zero elements of the precoding
matrix is designed with the guidelines of the prior information
provided in Section III. The non-zeros elements of the com-
bining matrix are chosen uniformly from a normalized unit
circle to guarantee the uniqueness of tensor decomposition
[17] and the unambiguity of AoA estimation in the HBF
structure. In order to avoid the interference between the BSs,
we assume that each BS is allocated a non-overlapping 20
MHz bandwidth with 612 subcarriers. We set the central
frequency of 4.9 GHz and the SCS of ∆f = 30 KHz.
The number of OFDM symbols utilized for sensing is set
to N = 7. According to 5G new radio (NR) standard, the
total period of OFDM symbol (including the cyclic prefix) is
given by Ts = 35.677 µs [37]. The velocity of each UA V is
uniformly distributed in [Vmin, Vmax], where Vmin = 5 km/h
and Vmax = 100 km/h denote the minimum and the maximum
velocity of UA V , respectively. The RCS of each UA V is set to
σ = 0.01 m 2. The path loss in dB is given by [38]
PL = 103.4 +20 lg (f /MHz) +40 lg (d/km) −10 lg
 
σ/m2 ,
(98)

<!-- extraction_page_index: 13 -->

13
45 50 55 60 65
Transmit power (dBm)
10-3
10-2
10-1
100
101
102
RMSE (deg)
Tensor, K = 2
Benchmark1, K = 2
Tensor, K = 4
Benchmark1, K = 4
(a) AoA
45 50 55 60 65
Transmit power (dBm)
10-2
100
102
RMSE (m)
Tensor, K = 2
Benchmark1, K = 2
Tensor, K = 4
Benchmark1, K = 4 (b) Range
45 50 55 60 65
Transmit power (dBm)
10-2
10-1
100
101
102
RMSE (m/s)
Tensor, K = 2
Benchmark1, K = 2
Tensor, K = 4
Benchmark1, K = 4
(c) Radial velocity
45 50 55 60 65
Transmit power (dBm)
10-2
10-1
100
101
102
103
RMSE (m)
Tensor, K = 2
Benchmark1, K = 2
Tensor, K = 4
Benchmark1, K = 4 (d) Position
Fig. 9. Estimation RMSE vs. the transmit power budget.
where f denotes the central frequency, d denotes the range
between the UA V and the BS. The noise power density is
set to -174 dBm/Hz. For the simulation layout, as depicted in
Fig. 8, there are J = 4 BSs uniformly situated on a circle
with the radius of r2 = 450 m, with their UPA panels point
towards the center of the circle, and the height of each BS
is set to 30 m. The transmit power budget of each BS is set
to 58 dBm. In addition, it is assumed that there are K = 4
UA Vs uniformly distributed with their projections on the x-
y plane within a circle with the radius of r1 = 400 m, and
the heights of UA Vs are uniformly distributed in [hmin, hmax],
where hmin = 35 m and hmax = 300 m denote the lowest and
highest flight heights of UA Vs, respectively. To evaluate the
performance of parameter estimation, the following root mean
square error (RMSE) is adopted [16], i.e.,
RMSE (x) =
vuut 1
K
KX
k=1
∥ˆxk − xk∥22, (99)
where ˆxk and xk respectively denote the estimated and the true
value of parameters, including AoAs, range, radial velocity,
position and true velocity. The simulation results are obtained
by averaging over 95% of more than 1000 independent re-
alizations to ignore the effect of outliers [16]. Additionally,
we consider a conventional approach relying on MUSIC and
FFT algorithms as a benchmark (denoted as “Benchmark1”).
Specifically, in this scheme, the UA Vs’ AoAs are first derived
by the well-known 2-D MUSIC algorithm [39]. Then, the 2-D
FFT operation is performed to estimate the ranges and radial
velocities of UA Vs [7]. To ensure the automatic pairing of
multi-dimensional parameters, this benchmark also operates
on the formulation of the mode-1 unfolding of tensor, i.e.,
(31).
45 50 55 60 65
Transmit power (dBm)
10-1
100
101
102
RMSE of position estimation (m)
SP
DP
Double SP
Fig. 10. Position estimation RMSE vs. the transmit power budget in the dual-
polarized system.
B. Monostatic Parameter Estimation
According to the above discussions, since each BS performs
the same parameter estimation algorithm before data fusion,
we first set J = 1 to evaluate the performance of the proposed
monostatic parameter estimation scheme.
Figs. 9(a)-9(c) respectively illustrate the RMSE of AoA,
range and radial velocity estimation versus the transmit power
budget. From Figs. 9(a)-9(c), we observe that as the transmit
power increases, both two schemes achieve lower estimation
RMSE. In addition, due to limitations in antenna array size and
sensing resource allocation, we find that the estimation RMSE
of Benchmark1 is prone to encountering a performance bottle-
neck. However, the estimation RMSE of the proposed scheme
shows a significant decline with the increase of transmit power,
which validates its effectiveness. Correspondingly, Fig. 9(d)
illustrates that the proposed tensor decomposition scheme
achieves higher positioning accuracy than Benchmark1, since
the former achieves enhanced AoA and range estimation
performance.
In addition, we also provide the position estimation results
in the dual-polarized system (denoted as “DP”) and compare
with the single-polarized configuration (denoted as “SP”) in
Fig. 10 with the number of UA Vs of K = 4. The parameters
of DP configuration are set as follows. For sake of clarity, we
rewrite the polarization factor as
γ(δ,η)k =
q
r(δ,η)k ejϕ(δ,η)k , (100)
where r(δ,η)k denotes the random variable representing the
power ratio of waves from η = {Vt, Ht} transmit antennas
to δ ∈ {Vr, Hr} receive antennas, ϕ(δ,η)k denotes the ad-
ditional phase. According to the 3rd generation partnership
project (3GPP) technical report (TR) [40], we let r(Vr,Vt)k =
r(Hr,Ht)k = 1 and r(Vr,Ht)k , r(Hr,Vt)k = 1 /ξ, where ξ denotes
the cross-polarization discrimination (XPD) obeying the Log-
Normal distribution, i.e., ξ ∼ N
 
µ, σ2 dB with the ex-
pectation of µ = 8 and the standard deviation of σ = 4.
The phases are assumed to be random variables obeying the
uniform distribution, i.e., ϕ(δ,η)k ∼ U(0, 2π). To guarantee
the fairness, we also incorporate the double SP configuration

<!-- extraction_page_index: 14 -->

14
1 2 3 4 5
The number of UAVs, K
2
3
4
5
6
7
8
9
10
11
12CPU Time (s)
Tensor
Benchmark1
Fig. 11. The CPU time of the monostatic parameter estimation.
2 4 6 8 10
The number of UAVs, K
10-4
10-2
100
102
CPU Time (s)
Prop.
Exhaustive permutation
Fig. 12. The CPU time of the multi-BS data association.
(denoted as “Double SP”). Specifically, we set the number of
RF chains as ˜R = 2R = 128, the number of antennas located
in horizontal direction as ˜P = 2 P = 32 in this configura-
tion. Fig. 10 illustrates that DP configuration achieves higher
positioning accuracy than the SP configuration, since the DP
configuration provides more abundant amount of samples for
parameter estimation. However, the double SP configuration
achieves even higher positioning accuracy than the DP con-
figuration due to enhanced AoA estimation achieved by more
sufficient array manifold information and reduced cumulative
error. Nevertheless, the employment of dual polarization is
still promising, since it reduces the antenna deployment area
compared to the double SP configuration.
Fig. 11 depicts the central processing unit (CPU) time of the
monostatic parameter estimation versus the number of UA Vs.
It can be observed that the proposed tensor decomposition-
based scheme is more efficient than Benchmark1. The reason
lies in the fact that the MUSIC algorithm requires the 2-
D search on (θ, ϕ) for AoA estimation, whereas for the
tensor decomposition scheme, the proposed GRQ-based AoA
estimation algorithm can effectively reduce the computational
complexity. In addition, we also find that with increasedK, the
CPU time for both two schemes increases as more calculations
are required to estimate more parameters.
Fig. 13. Cooperative position estimation RMSE vs. the number of BSs.
C. Cooperative Position and V elocity Estimation
Fig. 12 illustrates the efficiency of the proposed multi-BS
data association algorithm. It can be observed that with a small
number of UA Vs, the CPU time of the proposed algorithm
exceeds that of the exhaustive permutation scheme. This is
because, in addition to deriving the MST of the updated graph
˜G, the proposed algorithm needs additional procedures to
calculate the distances between the positioning results of each
BS and those of other BSs to recognize and remove the false
detection results to enhance the cooperative sensing scheme.
Moreover, as the number of UA Vs increases, the computational
complexity of the exhaustive permutation method rises sharply,
while the CPU time of the proposed algorithm increases
slowly, which allows the algorithm to perform well even when
there are many UA Vs.
Fig. 13 depicts the cooperative position estimation RMSE
versus the number of BSs with the weighting intensity factor of
β1 = 0.5. As previously outlined, our strategy for selecting the
lattice point from the Pareto set is contingent upon the system
configuration and the precision of AoA and range estimation.
Specifically, for the tensor decomposition scheme, noting that
we assign 612 subcarriers but only 384 antennas (with HBF
structure) to each BS. In addition, the AoA estimation will also
be degraded by the cumulative error effect, which makes the
estimation of range more precise than AoA. Thus, we choose
the lattice point from the Pareto set according to (78). From
Fig. 13, we make the following observations: First, we observe
that the increase of BSs leads to a continuous improvement
in cooperative positioning accuracy, which is significantly
higher than the monostatic positioning results (i.e., K = 1).
This is attributed to the fact that more BSs provide richer
UA Vs’ parameter estimations, i.e., AoAs and range estimations
for the data fusion. Furthermore, it also can be observed
that the proposed Pareto optimality scheme further reduces
the positioning error compared to the mean fusion scheme.
This is because it takes the AoA and range estimations into
account with a finer granularity, rather than merely fuse the
final positioning results. In addition, it also allocates distinct
weights to the BSs according to the ranges between them
and the UA Vs, making the more accurate estimations more
dominant in the fusion process.

<!-- extraction_page_index: 15 -->

15
Fig. 14. Cooperative true velocity estimation RMSE vs. the number of BSs.
Fig. 14 shows the cooperative velocity estimation RMSE
versus the number of BSs with the weighting intensity factor
of β2 = 0.5. Similarly, it can be observed again from Fig. 14
that the velocity estimation error decreases as the number of
BSs increases. This is because more BSs provide more infor-
mation about the radial velocities and AoAs. Furthermore, the
proposed residual weighting-based scheme further facilitates
the velocity estimation compared to the WLS method due to
the suppression of estimation errors.
D. Performance Evaluation in the Degraded Scenario
To further evaluate the versatility and generality of the
proposed sensing scheme, we degrade it to the single-antenna
single-target scenario and compare its performance with the
state-of-the-art cooperative sensing scheme proposed in [14]
(denoted as “Benchmark2”). In the degraded scenario, the
following adjustments are performed:
1) The parameter estimation problem formulated in (30)
degenerates into a second-order tensor decomposition
model, while the Vandermonde property of the factor
matrix can still be utilized to recover the factor matrices
and estimate the UA V’s range and radial velocity via the
similar procedures provided in Section IV.
2) Without AoA estimation, the rough estimation of the
UA V’s position is derived by the LS method [14].
3) Without AoA estimation, the determination of the final
position estimation from the lattice points union should
only take the minimization of the range loss function
into consideration, i.e., (78).
Fig. 15 illustrates the sensing performance of the proposed
scheme and of Benchmark2. It should be noted that in the
considered single-antenna setup, due to the severe path loss
and the limited antenna gain, it is hard to achieve sufficient
received SNR to meet the UA V detection and parameter
estimation requirements, especially when the UA V is far from
the BSs. Thus, in this simulation, we adjust the simulation
parameters as r1 = 100 m, r2 = 125 m. In addition, for ease
of algorithm implementation, we assume that the UA V and
the BSs are situated on the same horizontal plane, and its
velocity component in the z-axis is set to zero. From Fig.
15, we find that the proposed scheme demonstrates significant
45 50 55 60 65
Transmit power (dBm)
10-2
10-1
RMSE (m)
Prop.
Benchmark2
(a) Range
45 50 55 60 65
Transmit power (dBm)
10-1
100
RMSE (m/s)
Prop.
Benchmark2 (b) Radial velocity
45 50 55 60 65
Transmit power (dBm)
10-2
10-1
RMSE (m)
Prop.
Benchmark2
(c) Position
45 50 55 60 65
Transmit power (dBm)
10-1
100
RMSE (m/s)
Prop.
Benchmark2 (d) True Velocity
Fig. 15. Estimation RMSE vs. the transmit power budget in the degraded
scenario.
performance gains in range and position estimation compared
to Benchmark2, due to its off-grid approach to directly derive
the range estimation relying on the Vandermonde structure of
the factor matrix. In terms of radial velocity estimation, the
proposed scheme slightly performs worse than Benchmark2,
attributed to the cumulative effect of errors, since the radial
velocity estimation is affected by the previous range estima-
tion. However, due to the superior position estimation, the
proposed solution still achieves comparable performance in
true velocity estimation. Additionally, different from Bench-
mark2’s symbol-level multi-BS fusion approach, the proposed
data fusion scheme requires each BS to upload fewer sensing
parameters to the cloud, thereby reducing the transmission
overhead and synchronization requirements.
VIII. C ONCLUSION
In this paper, we proposed a comprehensive cooperative
ISAC scheme for the low-altitude sensing scenario that in-
cludes the monostatic parameter estimation, multi-BS data
association, and multi-BS cooperative sensing. Specifically,
we first provided preliminary steps for the sensing scheme
and formulated the monostatic parameter estimation problem
via using a tensor decomposition model to estimate the
UA Vs’ parameters. Then, a false removing MST-based data
association method was developed to accurately match the
multiple BSs’ estimations to the same UA V . Subsequently, we
proposed a Pareto optimality method and a residual weight-
ing scheme to improve the position and velocity estimation,
respectively. Additionally, we also extended our approach to
the dual-polarized system. Simulation results demonstrated the
superiority of proposed schemes in terms of generality and
estimation accuracy to the conventional techniques.

<!-- extraction_page_index: 16 -->

16
REFERENCES
[1] Q. Wu, J. Xu, Y . Zeng, D. W. K. Ng, N. Al-Dhahir, R. Schober, and A. L.
Swindlehurst, “A comprehensive overview on 5G-and-beyond networks
with UA Vs: From communications to sensing and intelligence,” IEEE
J. Sel. Areas Commun. , vol. 39, no. 10, pp. 2912–2945, Oct. 2021.
[2] F. Liu, Y . Cui, C. Masouros, J. Xu, T. X. Han, Y . C. Eldar, and S. Buzzi,
“Integrated sensing and communications: Toward dual-functional wire-
less networks for 6G and beyond,” IEEE J. Sel. Areas Commun. , vol. 40,
no. 6, pp. 1728–1767, Jun. 2022.
[3] S. Lu, F. Liu, and L. Hanzo, “The degrees-of-freedom in monostatic
ISAC channels: NLoS exploitation vs. reduction,” IEEE Trans. V eh.
Technol., vol. 72, no. 2, pp. 2643–2648, Feb. 2023.
[4] L. Pucci, E. Paolini, and A. Giorgetti, “System-level analysis of joint
sensing and communication based on 5G new radio,” IEEE J. Sel. Areas
Commun., vol. 40, no. 7, pp. 2043–2055, Jul. 2022.
[5] C. Cui, J. Xu, R. Gui, W.-Q. Wang, and W. Wu, “Search-free DOD,
DOA and range estimation for bistatic FDA-MIMO radar,” IEEE Access,
vol. 6, pp. 15 431–15 445, Mar. 2018.
[6] L. Leyva, D. Castanheira, A. Silva, and A. Gameiro, “Two-stage
estimation algorithm based on interleaved OFDM for a cooperative
bistatic ISAC scenario,” in Proc. IEEE V eh. Technol. Conf. (VTC) , Jun.
2022, pp. 1–6.
[7] Z. Han, H. Ding, L. Han, L. Ma, X. Zhang, M. Lou, Y . Wang, J. Jin,
Q. Wang, G. Liu et al. , “Cellular network based multistatic integrated
sensing and communication systems,” IET Commun. , vol. 6, pp. 1–11,
Jan. 2024.
[8] Z. Han, H. Ding, X. Zhang, Y . Wang, M. Lou, J. Jin, Q. Wang, and
G. Liu, “Multistatic integrated sensing and communication system in
cellular networks,” in Proc. IEEE Globecom Workshops (GC Wkshps) ,
Dec. 2023, pp. 123–128.
[9] G. Li, S. Wang, K. Ye, M. Wen, D. W. K. Ng, and M. Di Renzo,
“Multi-point integrated sensing and communication: Fusion model and
functionality selection,” IEEE Wireless Commun. Lett. , vol. 11, no. 12,
pp. 2660–2664, Dec. 2022.
[10] P. Gao, L. Lian, and J. Yu, “Cooperative ISAC with direct localization
and rate-splitting multiple access communication: A pareto optimization
framework,” IEEE J. Sel. Areas Commun. , vol. 41, no. 5, pp. 1496–1515,
May. 2023.
[11] Y . Cao and Q.-Y . Yu, “Joint resource allocation for user-centric cell-free
integrated sensing and communication systems,” IEEE Commun. Lett. ,
vol. 27, no. 9, pp. 2338–2342, Sep. 2023.
[12] Q. Shi, L. Liu, S. Zhang, and S. Cui, “Device-free sensing in OFDM
cellular network,” IEEE J. Sel. Areas Commun. , vol. 40, no. 6, pp. 1838–
1853, Jun. 2022.
[13] Z. Zhang, H. Ren, C. Pan, S. Hong, D. Wang, J. Wang, and X. You,
“Target localization in cooperative ISAC systems: A scheme based on
5G NR OFDM signals,” IEEE Trans. Commun. , pp. 1–1, 2024.
[14] Z. Wei, R. Xu, Z. Feng, H. Wu, N. Zhang, W. Jiang, and X. Yang,
“Symbol-level integrated sensing and communication enabled multiple
base stations cooperative sensing,” IEEE Trans. V eh. Technol., vol. 73,
no. 1, pp. 724–738, Jan. 2024.
[15] X. Lu, Z. Wei, R. Xu, L. Wang, B. Lu, and J. Piao, “Integrated sensing
and communication enabled multiple base stations cooperative UA V
detection,” in Proc. IEEE Int. Conf. on Commun. Workshops (ICC
Workshops), Jun. 2024, pp. 1882–1887.
[16] R. Zhang, L. Cheng, S. Wang, Y . Lou, Y . Gao, W. Wu, and D. W. K.
Ng, “Integrated sensing and communication with massive MIMO: A
unified tensor approach for channel and target parameter estimation,”
IEEE Trans. Wireless Commun. , vol. 23, no. 8, pp. 8571–8587, Aug.
2024.
[17] Z. Zhou, J. Fang, L. Yang, H. Li, Z. Chen, and R. S. Blum, “Low-
rank tensor decomposition-aided channel estimation for millimeter wave
MIMO-OFDM systems,” IEEE J. Sel. Areas Commun. , vol. 35, no. 7,
pp. 1524–1538, Jul. 2017.
[18] Y . Lin, S. Jin, M. Matthaiou, and X. You, “Tensor-based channel esti-
mation for millimeter wave MIMO-OFDM with dual-wideband effects,”
IEEE Trans. Commun. , vol. 68, no. 7, pp. 4218–4232, Jul. 2020.
[19] R. Wang, H. Ren, C. Pan, G. Zhou, and J. Wang, “Tensor
decomposition-based time varying channel estimation for mmwave
MIMO-OFDM systems,” 2024, arXiv:2403.02942. [Online]. Available:
https://arxiv.org/abs/2403.02942.
[20] H. Zhu and J. Wang, “Chunk-based resource allocation in OFDMA
systems—part I: Chunk allocation,” IEEE Trans. Commun. , vol. 57,
no. 9, pp. 2734–2744, Sep. 2009.
[21] H. Zhu and J. Wang, “Chunk-based resource allocation in OFDMA
systems—part II: Joint chunk, power and bit allocation,” IEEE Trans.
Commun., vol. 60, no. 2, pp. 499–509, Feb. 2012.
[22] Y . Cui, X. Jing, and J. Mu, “Integrated sensing and communications
via 5G NR waveform: Performance analysis,” in Proc. IEEE Int. Conf.
Acoust. Speech Signal Process. (ICASSP) , May 2022, pp. 8747–8751.
[23] F. Liu and C. Masouros, “A tutorial on joint radar and communication
transmission for vehicular networks—part I: Background and fundamen-
tals,” IEEE Commun. Lett. , vol. 25, no. 2, pp. 322–326, Feb. 2021.
[24] S. M. Kay, Fundamentals of Statistical Signal Processing . Englewood
Cliffs, NJ, USA: Prentice-Hall, 1998.
[25] M. Wax and T. Kailath, “Detection of signals by information theoretic
criteria,” IEEE Trans. Acoust. Speech Signal Process. , vol. 33, no. 2, pp.
387–392, Apr. 1985.
[26] T. G. Kolda and B. W. Bader, “Tensor decompositions and applications,”
SIAM Review , vol. 51, no. 3, pp. 455–500, 2009. [Online]. Available:
https://doi.org/10.1137/07070111X.
[27] X. Zhang, Matrix analysis and applications . Beijing, CHN: Tsinghua
University Press, 2004.
[28] M. Sørensen and L. De Lathauwer, “Blind signal separation via tensor
decomposition with vandermonde factor: Canonical polyadic decompo-
sition,” IEEE Trans. Signal Process. , vol. 61, no. 22, pp. 5507–5519,
Nov. 2013.
[29] J. B. Kruskal, “Three-way arrays: rank and uniqueness of trilinear
decompositions, with application to arithmetic complexity and statistics,”
Linear Algebra and its Applications , vol. 18, no. 2, pp. 95–138, 1977.
[Online]. Available: https://www.sciencedirect.com/science/article/pii/
0024379577900696.
[30] X. Zhang, F. Wang, and H. Li, “An efficient method for cooperative
multi-target localization in automotive radar,” Signal Process. Lett. ,
vol. 29, pp. 16–20, Oct. 2022.
[31] R. C. Prim, “Shortest connection networks and some generalizations,”
Bell Syst. Tech. J., , vol. 36, no. 6, pp. 1389–1401, Nov. 1957.
[32] J. B. Kruskal, “On the shortest spanning subtree of a graph and the
traveling salesman problem,” in Proc. Am. Math. Sot. , vol. 7, no. 1,
1956, pp. 48–50.
[33] P.-C. Chen, “A non-line-of-sight error mitigation algorithm in location
estimation,” in Proc. Wireless Commun. Netw. Conf. (WCNC), Sep. 1999,
pp. 316–3201.
[34] J. Xing, J. Zhang, L. Jiao, X. Zhang, and C. Zhao, “A robust wireless
sensor network localization algorithm in NLoS environment,” in Proc.
IEEE Int. Conf. Control Automat. (ICCA) , May 2007, pp. 3244–3249.
[35] C. Qian, X. Fu, N. D. Sidiropoulos, and Y . Yang, “Tensor-based channel
estimation for dual-polarized massive MIMO systems,” IEEE Trans.
Signal Process., vol. 66, no. 24, pp. 6390–6403, Dec. 2018.
[36] G. H. Golub, A. Hoffman, and G. W. Stewart, “A
generalization of the eckart-young-mirsky matrix approx-
imation theorem,” Linear Algebra and its applications ,
vol. 88, pp. 317–327, Apr. 1987, [Online]. Available:
https://www.sciencedirect.com/science/article/pii/0024379587901145.
[37] 3GPP, “5G; NR; user equipment (UE) radio transmission and reception;
part 1: Range 1 stand alone,” 3rd Generation Partnership Project (3GPP),
Technical Specification (TS) 38.101, Jul. 2023, version 17.10.0.
[38] ITU, “Calculation of free-space attenuation,” International Communica-
tion Union (ITU), Tech. Rep. P.524-4, Aug. 2019.
[39] P. Stoica and A. Nehorai, “MUSIC, maximum likelihood, and cramer-
rao bound,” IEEE Trans. Acoust. Speech Signal Process. , vol. 37, no. 5,
pp. 720–741, May 1989.
[40] 3GPP, “Study on channel model for frequencies from 0.5 to 100 GHz,”
3rd Generation Partnership Project (3GPP), Technical Specification (TS)
38.901, Dec. 2023, version 17.1.0.
