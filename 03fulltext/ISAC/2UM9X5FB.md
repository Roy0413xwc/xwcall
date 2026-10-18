---
title: "A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Near-Field and Far-Field Scenarios"
zotero_key: "2UM9X5FB"
pdf_key: "G9CX5BUU"
doi: "10.1109/jiot.2025.3559924"
collection: "ISAC"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# A Novel Angle-Delay-Doppler Estimation Scheme for AFDM-ISAC System in Mixed Near-Field and Far-Field Scenarios — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
A Novel Angle-Delay-Doppler Estimation Scheme
for AFDM-ISAC System in Mixed Near-field and
Far-field Scenarios
Yirui Luo, Student Member , IEEE, Yong Liang Guan, Senior Member , IEEE, Yao Ge, Member , IEEE,
David Gonz ´alez G., Senior Member , IEEE, and Chau Yuen, Fellow, IEEE
Abstract—The recently proposed multi-chirp waveform, affine
frequency division multiplexing (AFDM), is considered as a
potential candidate for integrated sensing and communication
(ISAC). However, acquiring accurate target sensing parameter
information becomes challenging due to fractional delay and
Doppler shift occurrence, as well as effects introduced by the
coexistence of near-field (NF) and far-field (FF) targets associated
with large-scale antenna systems. In this paper, we propose a
novel angle-delay-Doppler estimation scheme for AFDM-ISAC
system in mixed NF and FF scenarios. Specifically, we model
the received ISAC signals as a third-order tensor that admits a
low-rank CANDECOMP/PARAFAC (CP) format. By employing
the Vandermonde nature of the factor matrix and the spatial
smoothing technique, we develop a structured CP decomposition
method that guarantees the condition for uniqueness. We further
propose a low-complexity estimation scheme to acquire target
sensing parameters with fractional values, including angle of
arrival/departure (AoA/AoD), delay and Doppler shift accurately.
We also derive the Cram ´er-Rao Lower Bound (CRLB) as a
benchmark and analyze the complexity of our proposed scheme.
Finally, simulation results are provided to demonstrate the
effectiveness and superiority of our proposed scheme.
Index Terms —ISAC, AFDM, DAFT, high mobility, MIMO,
tensor signal processing, mixed NF and FF sensing, Internet of
Everything (IoE).
I. I NTRODUCTION
The sixth-generation (6G) wireless systems are anticipated
to maintain reliable communication in high mobility scenarios
while significantly enhancing spectral and energy efficiencies,
and supporting ubiquitous Internet of Things (IoT) connec-
tivity for all devices [1]. A variety of emerging 6G wireless
services, such as unmanned vehicles, V2X, as well as the In-
dustrial Internet of Things (IIoT), require wireless networks to
provide prompt target sensing and communication capabilities
[1]–[4]. Simultaneously, wireless communication and radar
sensing systems are increasingly converging and expanding
This work was supported under the RIE2020 Industry Alignment
Fund—Industry Collaboration Projects (IAF-ICP) Funding Initiative, as well
as cash and in-kind contribution from the industry partner(s). The work of
Chau Yuen was supported by National Research Foundation FCP-NTU-RG-
2024-025.
Yirui Luo, Yong Liang Guan and Chau Yuen are with School of
Electrical and Electronic Engineering, Nanyang Technological Univer-
sity, Singapore (e-mail: yirui001@e.ntu.edu.sg, eylguan@ntu.edu.sg, and
chau.yuen@ntu.edu.sg.)
Yao Ge is with the Continental-NTU Corporate Lab, Nanyang Technolog-
ical University, Singapore (e-mail: yao.ge@ntu.edu.sg).
David Gonz ´alez G. is with the Wireless Communications Technologies
Group, Continental AG, Germany (e-mail: david.gonzalez.g@ieee.org).
their frequency bands in response to the rising demand for
high-speed communication and high-resolution radar sens-
ing, leading to the spectrum congestion of the two systems.
Therefore, integrated sensing and communication (ISAC) is
regarded as a promising technology for realizing 6G wireless
communications by integrating the two functions within a
single system to improve spectrum and energy efficiency [4].
In fact, ISAC has garnered significant attention from both
academia and industry [4]. Most existing studies aim to
achieve the integration of the two systems by employing
the same waveform and hardware. In particular, orthogonal
frequency division multiplexing (OFDM) is widely employed
in ISAC due to the high spectral efficiency and robustness
for target sensing [5]. However, as the mobility and carrier
frequency continues to increase in the 6G system, the resulting
severe Doppler spreads can disrupt the orthogonality between
subcarriers, thereby making OFDM suffer from intercarrier
interference (ICI). One solution is to reduce the duration of the
OFDM symbols to render the channel quasi-stationary during
each symbol [6], but at a cost of lower spectral efficiency due
to the increased cyclic prefix (CP) number. Another approach
is to mitigate ICI [7], which, however, incurs the cost of a
more complex transceiver design and is only effective at rel-
atively low Doppler shift. Therefore, the development of new
waveforms for the 6G wireless system to cope with doubly
dispersive channels in high-mobility scenarios is particularly
critical.
So far, several new modulation waveforms have been
developed for doubly dispersive channels. The authors in
[8] proposed a two-dimensional modulation technique named
orthogonal time frequency space (OTFS). Unlike traditional
OFDM in the time-frequency (TF) domain, OTFS symbols
are modulated in the delay-Doppler (DD) domain, thereby
achieving potential full diversity as each data symbol spans to
the entire TF domain [9]–[11]. Furthermore, this modulation
allows to directly interact with channel delay and Doppler
shift parameters, satisfying the sensing requirements of the
ISAC system [12]. Another kind of modulation waveform to
cope with doubly dispersive channels is the chirp-based signals
whose frequency varies linearly with time. Orthogonal chirp
division multiplexing (OCDM) [13] exemplifies this approach
and has been demonstrated to outperform OFDM in doubly
dispersive channels due to the unique features of the chirp
spread spectrum [14]. However, the diversity order of OCDM
in the doubly dispersive system cannot be optimal due to the
arXiv:2504.06567v1  [eess.SP]  9 Apr 2025

2
limited representation of the channel delay-Doppler profile.
Recently, affine frequency division multiplexing (AFDM), a
new multi-chirp waveform based on one-dimensional discrete
affine Fourier transform (DAFT), is proposed in [15]. By
adapting the chirp parameters of the DAFT based on the max-
imum channel delay and Doppler shift information, AFDM
can separate all the paths in the discrete affine Fourier (DAF)
domain and let each symbol experience all path coefficients,
thus obtaining full diversity in the doubly dispersive system
[15]–[18]. Meanwhile, compared to OTFS, it has been proved
that AFDM has comparable BER performance but with less
pilot overhead [15]–[17], [19], [20] and lower implementation
complexity [21]. Moreover, due to the ability to support
reliable communication in high-mobility scenarios and to
distinguish multiple targets in the DAF domain, AFDM is
considered as a promising candidate for 6G ISAC system.
Until now, the research of AFDM-based ISAC is still in
its infancy. Authors in [22] study a bistatic static target
sensing scenario by using AFDM. Unfortunately, their method
is unavailable for velocity sensing. For high-mobility target
sensing, a simple match filter-based method for ISAC was
proposed in [23], while the estimation performance of the
Doppler shift is limited by the number of AFDM symbols
in use, which is undesirable due to the requirement of low
latency for next generation wireless networks. Furthermore,
the match filter-based method requires an assumption that
the delay is on the grid, which may be impractical in real
wireless systems because of the limited spectral and temporal
resources, resulting in insufficient resolution for both delay and
Doppler shift. In order to obtain super-resolution estimations
of both delay and Doppler shift, the authors in [24] proposed
an approximate maximum likelihood (ML) algorithm by using
just one AFDM symbol. However, ML suffers from a high
computational complexity in an exhausted 2D grid search.
Authors in [21] and [25] exploited the sparsity of delay
and Doppler in the DAF domain and proposed Bayesian
principle based approaches for sensing parameter estimation.
Although the methods in [21] and [25] have the computational
cost advantage over that in [24], they still suffer from a
high complexity due to the inverse of a large matrix. These
aforementioned issues inspire us to develop a low-complexity
algorithm that can estimate fractional delay and fractional
Doppler shift, thereby enhancing the sensing accuracy.
Multiple-input multiple-output (MIMO) technique can pro-
vide additional spatial degrees of freedom (DoF) [26], which
helps to enable spatial multiplexing, spatial diversity, and
angle estimation. So far, MIMO technique has been widely
employed in both communication and sensing systems. Au-
thors in [27] proposed a two-stage estimation algorithm where
the angle of arrival (AoA) is estimated by multiple signal
classification (MUSIC), in which the range and velocity of
the targets are matched by the estimation AoA. To avoid
searching, authors in [28] proposed a super-resolution param-
eter estimation method via rotational invariance techniques
(ESPRIT) for MIMO-OFDM ISAC system. Besides, based
on the angle sparsity, authors in [29] [30] proposed the
compressed sensing (CS)-based methods for AoA, AoD, and
delay estimation. Recently, tensor-based signal processing has
received wide attention in the fields of channel estimation
[31]–[33], radar parameter estimation [34] [35], ISAC [36]–
[38], etc., due to the ability to exploit the multidimensional
characteristics of MIMO channels for parameters matching
and performance enhancement.
However, all the aforementioned works only consider far-
field (FF) scenarios and may not be directly applicable to
near-field (NF) scenarios. As the MIMO array size continues
to increase, the Rayleigh distance also grows, allowing for a
larger number of targets to potentially fall within the near-
field region [39] [40]. This trend will significantly change the
electromagnetic (EM) properties of the wireless environment
from planar-wave propagation to spherical-wave propagation,
leading to an inevitable near-field effect [41]. The NF-ISAC
framework was first investigated by the authors in [42] with
a full-duplex antenna for simultaneous transmission and re-
ception. To reduce power consumption and construction cost,
authors in [43] proposed a novel framework with double-
array structure for NF integrated sensing, positioning and
communication. To deal with the mixed NF and FF scenarios,
authors in [44] proposed a subspace-based method and authors
in [45] proposed a fourth-order cumulant base method for
source localization. However, the aforementioned studies do
not consider the case with high mobility.
Against the background, we propose a novel angle-delay-
Doppler estimation scheme for AFDM-ISAC system in the
mixed NF and FF scenarios in this paper. The main contribu-
tions of our work are summarized as follows:
1) We propose a novel AFDM-ISAC scheme for parameter
estimation of mixed NF and FF targets, which takes
into account the AoA, AoD, delay, and Doppler shift
simultaneously. Specifically, we formulate the received
AFDM-ISAC signal as a third-order tensor that admits a
low-rank CANDECOMP/PARAFAC (CP) format, whose
factor matrices contain the multi-target parameters. The
high-dimensional estimation problem is parameterized by
a small number of physical parameters due to the sparsity
of the system.
2) We apply a structured CP decomposition method by
exploiting the Vandermonde nature of the factor matrix
and the spatial smoothing technique. We also analyze the
uniqueness condition for the CP decomposition, which
defines the feasible applications of our proposed scheme,
and demonstrate that the condition can be relaxed.
3) We develop a subspace-based method that avoids high-
complexity eigendecomposition for AoA estimation with
mixed NF and FF targets. We further propose a super-
resolution joint delay-Doppler estimation scheme by
leveraging the full representation of the channel delay-
Doppler profile provided by AFDM in the DAF domain,
where the fractional components can be estimated by
using one-dimensional iterative process for sensing en-
hancement with low complexity.
4) Finally, we derivate the Cram ´er-Rao lower bound (CRLB)
for the corresponding parameter estimation and evaluate
the performance of our proposed AFDM-ISAC scheme
with NF and FF targets in terms of the normalized

3
Target R
Target 1
User
ISAC receiver
ISAC transmitter
Near field area
Multipath P
AFDM ISAC signal
Fig. 1. Mixed near-field and far-field AFDM-ISAC system model.
mean square error (NMSE) of the estimated AoA, AoD,
delay and Doppler shift. Simulation results indicate the
performance of the proposed scheme outperforms the
other benchmark schemes and is also close to that of
the corresponding CRLB.
The remainder of the paper is organized as follows. Section
II depicts the signal model of the AFDM-based mixed NF
and FF ISAC system. Section III explains the establishment
of the structured tensor model and analyzes the uniqueness
of CP decomposition. Section IV introduces our proposed
algorithm for AoA, AoD, delay, and Doppler shift estimation.
Section V provides the CRLB and complexity analysis of our
scheme. Section VI presents the numerical results, followed
by concluding remarks in Section VII.
Notation: If not specified, lowercase letter x, lowercase
bold letter x, and uppercase bold letter X donate variables,
vectors, and matrices, respectively. The calligraphy letter X
represents tensor and its mode-n unfolding matrix is donated
by X(n). (·)−1, (·)†, (·)∗, (·)T , (·)−T and (·)H stands for
the inverse, pseudo-inverse, conjugate, transpose, transpose-
inverse and conjugate transpose, respectively. ◦, ⊙, and ∗
stand for the outer product, the Khatri-Rao and Hadamard
product, respectively. Let X ∈ CM ×N , X = X (2 : M, :)
stands for the matrices without the first row of X. The identity
matrix and all-zeros matrix are denoted by IN ∈ CN ×N and
0M ×N ∈ CM ×N , respectively.
II. M IXED NF AND FF AFDM-ISAC S YSTEM MODEL
As illustrated in Fig. 1, we consider a AFDM-ISAC system
with the coexistence of NF and FF targets operating over
a channel with a carrier frequency fc and bandwidth BW .
Specifically, the micro-cell base station, equipped with a uni-
form linear array (ULA) of K antennas, transmits the AFDM
ISAC signals to communicate with a specific communication
user and serves as the ISAC transmitter. The AFDM ISAC
signals can also be reflected by environmental targets and
subsequently reused by a nearby macro-cell base station for
sensing purpose. The macro-cell base station serves as the
ISAC receiver and is equipped with a ULA consisting of G
antennas. Considering the size of the macro-cell base station
array is much larger than that of the micro-cell base station, we
assume a one-side mixed NF and FF sensing channel model for
the ISAC system. Specifically, we make an FF assumption at
the ISAC transmitter side and a mixed NF and FF assumption
at the ISAC receiver side. Moreover, the signals transmitted by
the ISAC transmitter (i.e., micro-cell base station) are known
by the ISAC receiver (i.e., macro-cell base station) due to the
backhaul connection facilitated by optical fiber.
A. Transmitted AFDM ISAC Signal
In this subsection, we provide a concise overview of
transmitted AFDM signal as introduced in [15]. The ISAC
transmitter and receiver processing diagrams of the AFDM
system are shown in Fig. 2. Consider an AFDM symbol with
a bandwidth BW = Nc∆f and a duration of Ta, where Nc
is the number of the chirp subcarriers and ∆f = 1/Ta is the
chirp subcarrier spacing. Let x be a Nc × 1 symbol vector
in the DAF domain. To transform x into the time domain, an
Nc-point inverse DAFT (IDAFT) is applied, yielding
s [n] =
Nc−1X
m=0
x [m] ϕn (m), (1)
where n = 0 , . . . , Nc − 1 and ϕn (m) =
1√
N c
exp

j2π
 
c1n2 + c2m2 + nm/Nc. As defined
in [15], c1 > 0 and c2 > 0 are the AFDM chirp
parameters to be optimized for full diversity. In the
matrix form, (1) can be expressed as s = ΛHc1 FH ΛHc2 x, where
Λci = diag

e−j2πcin2 , n= 0, 1, ..., Nc − 1, i= 1, 2 and F
is the normalized Nc-point DFT matrix. Before transmitting,
a chirp-periodic prefix (CPP) of length Lcpp should be
appended to let the channel lie in a periodic domain, which
has an expression of
s[n] = s [Nc + n] e−j2πc1(N 2c +2Ncn), n = −Lcpp, ...,−1,
(2)
where Lcpp is set to be an integer equal to or larger than the
maximum channel delay taps. We can also write down s (t)
as a continuous version of the transmitted AFDM signal with
the expression of
s (t) = 1√
T a
Nc−1X
m=0
x [m]ej2π(c2m2+Φm(t)), 0 ⩽ t < Ta, (3)
where Φm (t) is defined in segments over intervals that cor-
respond to the partition {tm,q}q=0,...,2Ncc1 of [0, Ta) with
tm,0 = 0 and tm,q = Nc−m2N c1 Ts + q−12c1 Ts for q > 0.Ts = Ta/Nc is the sampling interval and Φm (t) is defined
as Φm (t) = c1T 2s t2 + mNcTs t − qTs t for t ∈ [tm,q, tm,q+1) [24].
B. Sensing Channel Model
Consider a doubly dispersive sensing channel with R targets
for sensing purpose, and each target is only characterized by

4
Modulation
Tune              based on maximum Doppler shift
( )12,cc
Demodulation
ChannelS\P P\SIFFT AddCPP
2
H
cΛ
1
H
cΛ
S\P P\SIFFT AddCPP
2
H
cΛ
1
H
cΛ
 FFTS\P P\S
Remove
CPP
1cΛ
2cΛ
 FFTS\P P\S
Remove
CPP
1cΛ
2cΛ
Modulation
Tune              based on maximum Doppler shift
( )12,cc
Demodulation
ChannelS\P P\SIFFT AddCPP
2
H
cΛ
1
H
cΛ
 FFTS\P P\S
Remove
CPP
1cΛ
2cΛ
DAFT
Channel FFTS\P P\S
Remove
CPP
1cΛ
2cΛ
IDAFT
S\P P\SIFFT AddCPP
2
H
cΛ
1
H
cΛ
IDAFT
S\P P\SIFFT AddCPP
2
H
cΛ
1
H
cΛ
Fig. 2. Block diagram for AFDM transmitter and receiver.
1
… …
0-𝐺𝑥
𝜃𝑟
𝑟0,r
𝑑
- 𝐺𝑥 +1 𝐺𝑥 -1
Target r 
𝐺𝑥-1 1
ISAC transmitter ISAC receiver
Target r 
𝜃𝑟
𝜙𝑟
(a)
1
… …
0-G
𝜃𝑟
𝑟0,r
𝑑
-G+1 G-1
Target r 
G-1 1
ISAC transmitter ISAC receiver
Target r 
𝜃𝑟
𝜙𝑟 (b)
Fig. 3. (a) ULA configuration of ISAC receiver. (b) Illustration of system
geometry.
its line-of-sight (LOS) path. As depicted in Fig. 3 (a), we
assume the ISAC receiver has a symmetrical ULA consisting
of G = 2 Gx + 1 antennas along x-axis, where the middle
element is located at the origin and set to be the reference
antenna.
The array response of the ISAC receiver for target r at the
g-th antenna of the ISAC receiver is given by [44]
[aR (θr, r0,r)]g= ej 2πλ (√r20,r+(gd)2−2r0,rgd sin θr−r0,r) sin θr
≈ ejgρ r+jg 2ξr ,
(4)
where [aR (θr, r0,r)]g is the g-th entry of array response vector
aR (θr, r0,r), ρr = − 2πdλ sin θr and ξr = πd2λr20,r cos θr, forg = −Gx, −Gx + 1, ..., Gx. d is the receive antenna spacing,
λ is the wavelength, θr is the AoA of the r-th target and
r0,r ∈
h
0.62
 
D3/λ1/2, +∞ is the distance between the r-
th target and the reference antenna (i.e., g = 0). When r0,r is
within the Rayleigh distance (i.e., r0,r ≤ 2D2/λ), the phase of
the electromagnetic wave from near-field target r impinging on
the ISAC receiver has to be calculated based on the spherical
wave model and the phase shift caused by distance information
cannot be ignored.
If the target r is in the far field, i.e., r0,r ∈
 
2D2/λ, +∞,
jg 2ξr is approximated equal to zero and (4) simplifies to
[aR (θr)]g = ejgρ r . (5)
Even though the array response of the ISAC receiver for
the far-field targets can be simplified to (5), the form of (4)
is employed throughout to provide a unified representation
for both near-field and far-field targets, thereby simplifying
the overall expression. Denote the scattering coefficient, total
range, and relative velocity of target r as γr, Lr, and vr,
respectively. Then, the total delay and Doppler shift can be
expressed as τr = Lrc and fd,r = vrfcc with c denotes the
speed of light. Thus, the matrix impulse response for the time-
varying MIMO sensing channel can be expressed as
H (t, τ) =
RX
r=1
γraR (θr, r0,r) aT (ϕr)H δ (τ − τr) ej2πfd,rt,
(6)
where
aT (ϕr) =
h
1, e−jπ sin ϕr , ..., e−jπ(K−1) sinϕr
iT
(7)
is the linear array response of the ISAC transmitter with half
wavelength antenna spacing and ϕr denotes the AoD of target
r. The system geometry explanation for AoA and AoD is
illustrated in Fig. 3 (b).
C. Received AFDM ISAC Signals
After through the channel in (6), the received time domain
signal at the g-th antenna of the ISAC receiver can be
expressed as
rg (t) =
RX
r=1
K−1X
k=0
γr [aR (θr, r0,r)]g [aT (ϕr)]kej2πfd,rt
× s (t − τr) + wg (t) ,
(8)
where wg (t) is the additive Gaussian noise in the time domain
received by the g-th antenna with g = −Gx, ..., Gx and
[aT (ϕr)]k is the k-th entry of the vector aT (ϕr). By sampling
with the interval Ts, the received samples R [n] ∈ CG×1 in
the time domain at time instant n can be expressed as
R [n] =
RX
r=1
K−1X
k=0
γraR (θr, r0,r) [aT (ϕr)]kej2πνrn/Nc
× s [n − βr] + W [n] ,
(9)
with n = 0 , . . . ,(Nc + Lcpp) − 1. The normalized delay
and Doppler shift of target r are given by βr = τr/Ts and
νr = Ncfd,rTs. We define βr = ℓr + ιr and νr = αr + µr
with ℓr ∈ (0, ℓmax], ιr ∈
 
− 12 , 12 , αr ∈ [−αmax, αmax]
and µr ∈
 
− 12 , 12  referring to the integer normalized delay,
fractional normalized delay, integer normalized Doppler shift,
and fractional normalized Doppler shift, respectively, where
ℓmax is the maximum normalized delay and αmax is the
maximum normalized Doppler shift in the ISAC system.
To avoid overlapping for different non-zero entries at the
same position, c1 is set to be [15]
c1 = 2 (αmax + kv) + 12Nc , (10)

5
where kv is the parameter according to the Doppler spread.
Moreover, the maximum normalized delay and Doppler shift
should satisfy
2 (αmax + kv) + ℓmax + 2 (αmax + kv) ℓmax < Nc. (11)
to achieve the optimal diversity order.
After serial to parallel conversion and discarding CPP, the
received time domain sensing signal is transferred back to the
DAF domain through DAFT. The received signal in the DAF
domain can be expressed as
Y [m] =
Nc−1X
n=0
R [n] ϕ∗n (m) , (12)
with m = 0, ..., Nc − 1. In the matrix form, the output Y ∈
CG×Nc can be represented by
Y =
RX
r=1
K−1X
k=0
γraR (θr, r0,r) [aT (ϕr)]k(Erx)T + ˜W, (13)
where
Er = Λc2 FΛc1 ΓCP Pr ∆νr Πβr ΛHc1 FH ΛHc2 , (14)
and ˜W = Λc2 FΛc1 W is the corresponding noise in
the DAF domain. ∆νr has an expression of ∆νr =
diag(e−j2π(0:Nc−1)νr/Nc ) and Πβr has the expression of
Πβr = FHdiag(e−j2π(0:Nc−1)βr/Nc )F. ΓCP Pr is a diagonal
matrix with the expression of
ΓCP Pr = diag
 (
e−j2πc1(N 2c −2Nc(ℓr−n)) n < ℓr
1 n ⩾ ℓr
!
.
(15)
We can see from (15) that if Nc is an even number and 2Ncc1
is an integer, ΓCP Pr = I.
Meanwhile, the AFDM signal received at the communica-
tion user side can be expressed as
ycom =
PX
p=1
K−1X
k=0
γp[aT (ϕp)]kΛc2 FΛc1 ΓCP Pp
× ∆νp Πβp ΛHc1 FH ΛHc2 x + ˜W,
(16)
where P is the number of paths and γp is the pathloss of the
p-th path. In this paper, we mainly focus on the target sensing
algorithm design. Details for the communication processing,
i.e., channel estimation and symbol detection, can refer to the
reference [15].
III. T ENSOR REPRESENTATION AND ANALYSIS
In this section, we first elucidate how to formulate the
received sensing signal into a tensor model. We then discuss
the uniqueness of the structured CP decomposition.
A. Low-rank Tensor Model
By utilizing (13) with its structure, we can represent the
received DAF domain signal as a third-order tensor Y ∈
CG×Nc×K, which is given by
Y = X + W, (17)
where X ∈ CG×Nc×K is a tensor form for the received signal
in the DAF domain and W ∈ CG×Nc×K is the corresponding
noise in the DAF domain.
It is worth noting that X can be written in the CANDE-
COMP/PARAFAC (CP) decomposition form, i.e.,
X = [ [γ; AR, BC, AT ] ]
=
X
r
γraR (θr, r0,r) ◦ b (βr, νr) ◦ aT (ϕr) , (18)
where γ = [γ1, γ2, ..., γR]T and
b (βr, νr) = Λc2 FΛc1 ΓCP Pr ∆νr Πβr ΛHc1 FH ΛHc2 x. (19)
Additionally, AR ∈ CG×R, BC ∈ CNc×R and AT ∈
CK×R are the related factor matrices with the respective
expression as
AR =
 aR (θ1, r0,1) aR (θ2, r0,2) · · ·aR (θR, r0,R)  ,
BC =
 b (β1, ν1) b (β2, ν2) · · ·b (βR, νR)  ,
AT =
 aT (ϕ1) aT (ϕ2) · · ·aT (ϕR)  .
B. Uniqueness Property Analysis
The uniqueness condition of the CP decomposition prob-
lem is crucial for target parameter estimation, which can
ensure that the decomposed factor matrices contain accurate
information of targets’ parameters. According to Kruskal’s
condition [46], the uniqueness of the CP decomposition can
be guaranteed by
kAR + kBC + kAT ⩾ 2R + 2, (20)
where kA is the Kruskal rank of matrix A and R is the rank
of the tensor. In the generic case 1, the condition (20) becomes
min(G, R) + min(Nc, R) + min(K, R) ⩾ 2R + 2. (21)
The condition (20) specifies that each factor matrix is
required to possess a Kruskal-rank greater than one, which
implies that there are no linearly dependent columns in one
factor matrix and the system must include at least two targets.
By leveraging the Vandermonde nature of AT due to the
inherent structures of far-field ULA and spatial smoothing,
the unique condition of the CP decomposition of X can be
relaxed to [47]



rank

A(K3−1)T ⊙ AR

= R,
rank

A(L3)T ⊙ BC

= R,
(22)
where K3 + L3 = K + 1 and K3 ∈ [1, K] is the parameters
for spatial smoothing [47]. A(M ) denotes the sub-matrix which
1Generic case means that the CP decomposition property holds with
probability one when the entries of factor matrices are drawn from absolutely
continuous probability density functions.

6
contains the first M rows of matrix A. Generically, the unique
condition (22) is satisfied if
min ((K3 − 1) G, L3Nc) ⩾ R. (23)
With the structural constraints, the condition (23) can be
satisfied when R = 1 and even holds for the case that AR or
BC is not full Kruskal-rank (i.e., some targets have the same
AoA or delay and Doppler shift).
IV. P ROPOSED ANGLE -D ELAY-D OPPLER ESTIMATION
SCHEME
In this section, we propose a novel tensor-based angle-
delay-Doppler estimation scheme for AFDM-ISAC system
with mixed NF and FF targets in two phases. In the first phase,
we exploit the structural characteristics of the factor matrices
in our model to perform CP decomposition. In the second
phase, we extract the relevant interested sensing parameters
from the estimated factor matrices obtained in the first phase.
A. Structured CP Decomposition for Factor Matrices
Before CP decomposition, the number of the targets needs to
be known and can be easily obtained by the minimum descrip-
tion length (MDL) approach [48]. Then, the CP decomposition
of (17) can be achieved by solving
min
ˆAR, ˆBC , ˆAT





Y − Xr ˆγrˆ aR (θr, r0,r) ◦ ˆb (βr, νr) ◦ ˆ aT (ϕr)




2F .(24)
One of the most renowned algorithms for solving (24) is the
alternating least squares (ALS) scheme, which alternatively
optimizes one of the factor matrices while keeping the other
two factor matrices fixed to minimize the data fitting error until
convergence [49]. However, the outcome of the alternating
process is significantly influenced by the initial state, poten-
tially leading to convergence towards a biased local optimum.
Additionally, ALS treats factor matrices as random ones rather
than structured ones, which consequently impacts performance
and effectiveness due to the neglect of prior information. More
importantly, the computational complexity is sometimes high
because of the slow convergence speed of this iterative method.
To address the aforementioned issues, we develop an en-
hanced structured tensor decomposition approach in this paper.
To be specific, we take the unfolding matrix of Y along its
second dimension and we have
Y(2) = BC (AT ⊙ AR)T + W(2), (25)
and W(2) ∈ CNc×KG is the unfolding matrix of W along
its second dimension. Due to the Vandermonde nature of AT ,
the spatial smoothing technique can be applied to Y(2) for
expanding the dimension and also overcoming the problems
for the rank deficient case.
Specifically, we define an integer pair (K3, L3) with K3 +
L3 = K + 1 and a cyclic selection matrix Jl3 ∈ CK3G×KG
with the expression of
Jl3 ≜

0K3×(l3−1) IK3 0K3×(L3−l3)

⊗ IG, (26)
where l3 ∈ [1, L3]. Then, the processing matrix after spatial
smoothing can be obtained by
Υ =
h
J1YT(2) J2YT(2) ... JL3 YT(2)
i
+ WΥ
=

A(K3)T ⊙ AR

Λ

A(L3)T ⊙ BC
T
+ WΥ,
(27)
with Λ = diag (γ1, . . . , γR). WΥ ∈ CK3G×L3Nc is the
corresponding noise after spatial smoothing.
According to [47], we utilize the ESPRIT-like approach for
the factor matrices estimation. In particular, we compute the
singular value decomposition (SVD) Υ = USVH, where
U ∈ CK3G×R and V ∈ CL3Nc×R are singular matrices.
S ∈ CR×R is a diagonal matrix formed by R singulars. Then,
there exists a nonsingular matrix M ∈ CR×R to satisfy
UM = A(K3)T ⊙ AR, (28)
and
V∗SP = A(L3)T ⊙ BC. (29)
where P = M−T . Define the generators of AT as {zr}Rr=1.
Due to the Vandermonde structure of AT , we have
A(K3−1)T ⊙ AR

Z = A
(K3)
T ⊙ AR, (30)
with Z = diag (z1, z2, ..., zR). Then, the relation (28) can also
be expressed as
U1M =

A(K3−1)T ⊙ AR

, U2M = A
(K3)
T ⊙ AR, (31)
where U1 = U (1 : (K3 − 1) G, :) and U2 =
U ((G + 1) : K3G, :). M and Z can be obtained by the
eigenvalue decomposition (EVD) U†1U2 = MZM−1, and
the columns of the estimated ˆAT can be generated by
ˆaT (ϕr) = 1, ˆzr, ˆz2r , . . . ,ˆzK−1r T , (32)
where ˆzr = Z[r,r]|Z[r,r]| is the estimated generator of the r-th
column of ˆAT for r = 1 , .., R, and Z [r, r] is the (r, r)-th
entry of Z.
According to (28) and (32), the columns of the estimated
ˆAR can be obtained by
ˆaR (θr, r0,r) =

ˆa(K3)T,r
H
⊗ IG

Umr, (33)
for r = 1, ..., R. mr is the r-th column of M and ˆaT,r is the
simplified expression of ˆaT (ϕr).
Finally, from (29), the columns of ˆBC can be obtained by
ˆbr =



ˆ a(L3)T,r
H

ˆ a(L3)T,r
H
ˆ a(L3)T,r
⊗ INc

 V∗Σpr, (34)
where pr is the r-th column of P and r = 1, ..., R. ˆbr is the
simplified expression of ˆb (βr, νr).
The structured CP decomposition algorithm is summarized
in Algorithm 1.
B. Sensing Parameters Estimation
This subsection explains how we extract the relevant inter-
ested sensing parameters from the estimated factor matrices
obtained in Algorithm 1.

7
Algorithm 1: Structured CP Decomposition
Input: Y(2), number of the targets R
1 Select an integer pair (K3, L3) subject to
K3 + L3 = K + 1;
2 Perform spatial smoothing for Y(2) according to (27);
3 Reconstruct ˆAT by (32);
4 Reconstruct ˆAR by (33);
5 Obtain ˆBC according to (34);
Output: ˆAR, ˆBC, ˆAT .
1) AoD: Each column of ˆAT is associated with one AoD.
Since we already got the generators of ˆAT , the AoD can be
estimated directly by
ˆϕr = arcsin
 ∠ˆzr
−π

, (35)
where ∠ is the phase angle extraction operator and r =
1, ..., R.
2) AoA: The AoA information of target r can be extracted
from the covariance matrix CR,r with the expression of
CR,r = ˆaR (θr, r0,r) ˆaR (θr, r0,r)H (36)
To resolve the coupling between distance and AOA caused
by the spherical wavefront of the near-field targets, we form
an (Gx + 1)×(Gx + 1) Toeplitz correlation matrix TR,r with
the expression of
TR,r =

cR,r (Gx + 1) cR,r (Gx) · · · cR,r (1)
cR,r (Gx + 2) cR,r (Gx + 1) · · · cR,r (2)
... ... ... ...
cR,r (2Gx + 1) cR,r (2Gx) · · ·cR,r (Gx + 1)


= ˜aR (θr) ˜aHR (θr) ,
(37)
where cR,r (a) is the (a, 2Gx + 2 − a)-th entry of CR,r,
˜ aR (θr) =

1, ej2ρr , ...., ej2Gxρr
T
and d is set to be a quarter
wavelength to avoid ambiguity [44] for AoA estimation. By
leveraging (37), the distance and AOA information can be
effectively decoupled2.
For estimating AoA of target r in (37), the multiple signal
classification (MUSIC) algorithm is commonly used. However,
the MUSIC algorithm suffers from a high complexity of eigen-
decomposition. To avoid the high complexity eigendecompo-
sition, we derive TR,r to two parts as TR,r =

TT1,r, TT2,rT ,
where T1,r is the first row of TR,r while T2,r is the last Gx
rows of TR,r. Then, θr can be obtained by
ˆθr = minθ ˜ aHR (θ) ΠQr ˜ aR (θ) , (38)
where
ΠQr = Qr
 
QHr Qr−1QHr , (39)
2Regardless of whether the target r is a near-field or far-field target, we
can obtain the Toeplitz correlation matrix in (37), which only contains the
AoA information. Therefore, our proposed AoA estimation scheme does not
require differentiation between near-field and far-field targets.
Qr =

PTr , −IGx T , (40)
and
Pr =
 
T1,rTH1,r−1T1,rTH2,r. (41)
3) Delay and Doppler Shift: Both the delay and Doppler
shift information are included in ˆBC. However, a direct 2D
exhaustive search requires high complexity. Thus, by leverag-
ing the full representation of the channel delay-Doppler profile
provided by AFDM in the DAF domain, we propose a two-
stage super-resolution joint delay-Doppler estimation scheme,
where fractional components can be estimated by using a one-
dimensional iterative process for sensing enhancement with
low complexity.
To enhance the understanding of the proposed scheme, we
first present an intuitive representation of the delay-Doppler
profile provided by AFDM in the DAF domain, as included
in ˆb (βr, νr). Recall the vector representation in (34), the m-th
entry of b (βr, νr) can be expressed as
br [m] = 1Nc
Nc−1X
m′=0
x [m′]ej2π

− βr m′Nc +c1β2r +c2(m′2−m2)
×
Nc−1X
n=0
ej 2πnNc (m′−m−locr)ej2πιrCm,n,r
| {z }
Fr[m,m′]
,
(42)
where br is the simplified expression of b (βr, νr). locr =
(2Ncc1βr − νr)Nc, Cm,n,r =
2Ncc1P
q=0
qILm,q
 
(n − βr)Nc

, and
(·)Nc is the modulo Nc operation. ILm,q is the indicatorfunction of the set Lm,q = {nm,q + 1, ..., nm,q+1}, where
nm,0 = 0 and nm,q =
j
Nc−m
2Ncc1 + q−12c1
k
for q >0 [24].
Since c2 is set to be a number sufficiently smaller than 12Nc
[15], the value of Ncc2
 
m′2 − m2 is approximately approach
zero, which can be ignored. It is worth noting that Fr [m, m′]
in (42) simplifies to ej2π(m′ −m−locr)−1
e
j 2πNc (m′ −m−locr)−1 for integer normalized
Doppler shift case, and to Ncδ (m′ − m − locr) when both
the normalized delay and Doppler shift have zero fractional
components.
Inspired by pulse compression in radar sensing, we propose
a low-complexity estimation scheme based on one-dimentional
(1D) pulse compression in stage one according to (42). Specif-
ically, the vector for target r after 1D pulse compression is
donated as ur, with the p-th element expressed as
ur [p] =
Nc−1X
m=0
ˆb∗r [m]x (m − p)Nc  e−j 2πNc
j
Nc +1−p
2Nc c1
k
(m−p)Nc ,
(43)
where p ∈ [0, Nc − 1] and r = 1 , ..., R. To provide a better
illustration, Fig. 4 shows an example of our proposed method
for one target with β = 8.13, ν = 1.67, c1 = 9512 and c2 = 0
at SNR = 15 dB. In this example, information symbols in x
are randomly generated 16-QAM symbols, and the subcarrier
number Nc is set to be 256. The DAF domain vector br
is shown in Fig. 4 (a), and the vector ur after 1D pulse
compression is shown in Fig. 4 (b). The results in Fig. 4 clearly
demonstrate that after the pulse compression, the vector ur

8
Algorithm 2: Proposed Two-stage Delay and Doppler
Shift Estimation Scheme
Input: Factor matrix ˆBC, transmit symbol vector x
1 Initialization: η =
√
5−1
2 ;
2 for r = 1 : R do
3 Obtain

ˆℓr, ˆαr

by (44);
4 yr = ΛHc2 FH ΛHc1 ˆbr, l(0) = ˆℓr, α(0) = ˆαr, t = 1;
5 for t ≤ T do
6 al = α(t−1) − 1, au = α(t−1) + 1;
7 repeat
8 g1 = au−η (au − al) , g2 = al+η (au − al);
9 f1 =
∆g1 Πl(t−1) sH yr2,
10 f2 =
∆g2 Πl(t−1) sH yr2;
11 if f1 ≤ f2, al = g1, g1 = g2;
12 if f1 > f2, au = g2, g2 = g1;
13 until Stopping criteria ;
14 α(t) = al+au2 ;
15 bl = l(t−1) − 1, bu = l(t−1) + 1;
16 repeat
17 q1 = bu − η (bu − bl) , q2 = bl + η (bu − bl);
18 f3 =
(∆α(t) Πq1 s)H yr2,
19 f4 =
(∆α(t) Πq2 s)H yr2;
20 if f3 ≤ f4, bl = q1, q1 = q2;
21 if f3 > f4, bu = q2, q2 = q1;
22 until Stopping criteria ;
23 l(t) = bl+bu2 ;
24 t = t + 1;
25 end
26 ˆβr = l(T ), ˆνr = α(T );
27 ˆτr = ˆβrts, ˆfd,r = νr∆f;
28 end
Output: Delay ˆτ , and Doppler shift ˆfd of the targets.
contains the information of interest about this target with the
noise. The value of locr can be obtained directly from the
index of the peak in ur.
Due to the predefined c1, the DAF domain impulse response
of our AFDM system can constitute a full delay-Doppler
representation of the sensing channel [15]. Therefore, the delay
and Doppler shift information can be obtained unambiguously
from ˆlocr by
ˆℓr =
$ ˆlocr
2Ncc1
%
, ˆαr = 2Ncc1 ˆℓr − ˆlocr. (44)
However, the pulse compression-based method can only
obtain the integer components of the normalized delay and
Doppler shift. Therefore, in stage two, we need to perform an
off-grid search based on the integer components we obtained
in the first stage. To further reduce the complexity, we employ
an iterative 1D golden section search method for the estimation
of fractional parts of normalized delay and Doppler shift. The
0 50 100 150 200 250
Subcarrier Index
0
0.1
0.2
0.3
0.4
0.5
0.6
0.7
0.8
0.9
1
Normalized Amplitude
(a) Signal vector before pulse compression.
0 50 100 150 200 250
loc Index
0
0.1
0.2
0.3
0.4
0.5
0.6
0.7
0.8
0.9
1
Normalized Amplitude
(b) Signal vector after pulse compression.
Fig. 4. The result comparison of 1D pulse compression performance.
two-stage low-complexity delay and Doppler shift estimation
scheme is summarized in Algorithm 2.
Algorithm 3: Proposed Angle-Delay-Doppler Estima-
tion Scheme
Input: Y(2), number of the targets R
1 For r = 1 to R do
2 Perform structured CP decomposition according to
Algorithm 1;
3 Estimate ˆϕr according to (35);
4 Estimate ˆθr according to (38);
5 Calculate ˆτr and ˆfd,r via Algorithm 2;
6 End;
Output: Estimated AoA ˆθ, AoD ˆϕ, delay ˆτ , and the
Doppler shift ˆfd of the targets.
The locations and the relative velocities for all the targets
can be obtained after the estimation of parameters of interest.
The whole processing of our proposed angle-delay-Doppler
estimation scheme is summarized in Algorithm 3.
V. P ERFORMANCE ANALYSIS
A. CRLB
In this subsection, we develop the Cram ´er-Rao lower bound
(CRLB) for the target parameter estimation. Note that the

9
CRLB serves as a minimum limit for the variance of any
unbiased estimator [50]. It also acts as a benchmark for
evaluating the effectiveness of the proposed approach. The
CRLB for the estimated parameters can be calculated by the
inverse of the Fisher information matrix (FIM) [51]
CRB (Ψ) = Ω−1 (Ψ) , (45)
where the estimated parameters Ψ includes Ψ =
[θ, r0, τ , fd, ϕ, γ], with θ = [θ1, ..., θR], r0 = [r0,1, ..., r0,R],
τ = [ τ1, ..., τR], fd = [ fd,1, ..., fd,R], ϕ = [ ϕ1, ..., ϕR] and
γ = [γ1, ..., γR].
Here, it is worth mentioning that although the proposed
scheme does not require to estimate the values of γr and
r0,r, they still influence the CRLB. Consequently, we have to
include them as estimated variables in the derivation calcula-
tions. Details for the derivation can be found in the Appendix.
B. Computational Complexity
The computational complexity of our proposed angle-
delay-Doppler estimation scheme for AFDM-ISAC sys-
tem in mixed NF and FF scenarios is elaborated as
follows. The truncated SVD of Υ has a computational
complexity of O (K3L3GNcR) and the EVD of U†1U2
has the complexity of O
 
R2K3G + R3. The complex-
ity of estimating the factor matrices AR, BC and AT
are O
 
K3GR2, O  L3NcR2 and O (KR), respectively.
For the complexity of parameters estimation, {ϕr}Rr=1
and {θr}Rr=1 has the complexity order of O (R) and
O (RGεθ), where εθ is the number of one dimensional AoA
search grids. The complexity for the estimation of {τr}Rr=1
and {fd,r}Rr=1 are both O (RNc log Nc + T RNc log Nc).
Thus, the total complexity of our proposed estima-
tion scheme is O (RNc (K3L3G + L3R + 2 (T + 1) logNc))
+O
 
R2K3 (2G + R) +O (R (K + Gεθ + 1)).
VI. N UMERICAL RESULTS
In this section, we conduct numerical simulations to inves-
tigate the performance of our proposed angle-delay-Doppler
estimation scheme for mixed NF and FF AFDM-ISAC system
based on Monte Carlo simulations. We consider a scenario
where the micro-cell base station employs a ULA with K = 8
antenna elements, and the macro-cell base station employs a
ULA with Gx = 50. The spatial smoothing parameter K3 is
set to be 5 and L3 = 4 . The carrier frequency is 60 GHz.
So the Rayleigh distance in our simulations is 6.25 m. The
number of subcarriers in the simulation is Nc = 256 and we
employ 16-QAM symbols. The AoDs and AoAs are randomly
distributed in [−π/2, π/2], and the number of mixed NF and
FF targets is set to be R = 3 with one target in the near-
field and two in the far-field. The maximum integer part of
the normalized Doppler shift is considered to be αmax = 1,
which corresponds to a maximum speed of 540 km/h. The
maximum delay is considered to be ℓmax = 12, then Lcpp is
set 12 to avoid ISI. Chirp parameters c1 = 9512 and c2 = 0.
The signal-to-noise ratio (SNR) is defined as
SNR ≜ ∥Y − W∥2F
∥W∥2F ,
-10 -5 0 5 10 15 20
SNR (dB)
10-8
10-7
10-6
10-5
10-4
10-3
10-2
10-1
NMSE (AoD)
OMP [30]
MUSIC [4]
Proposed
CRLB
Fig. 5. The NMSE performance of AoD estimation versus SNR.
-10 -5 0 5 10 15 20
SNR (dB)
10-9
10-8
10-7
10-6
10-5
10-4
NMSE (AoA)
FF
Subspace-based [44]
Proposed
CRLB
Fig. 6. The NMSE performance of AoA estimation versus SNR.
where Y and W represent the received signal and the noise
defined in (17), respectively.
First, we evaluate the estimation accuracy of the target
sensing parameters {θr, τr, fd,r, ϕr}Rr=1 measured by the nor-
malized mean square error (NMSE), which are defined as
NMSEθ ≜



θ − ˆθ


2
F
∥θ∥2F , NMSEτ ≜ ∥τ − ˆτ ∥2F∥τ ∥2F ,
NMSEfd ≜



fd − ˆfd


2F
∥fd∥2F , NMSEϕ ≜



ϕ − ˆϕ


2
F
∥ϕ∥2F .
Fig. 5 depicts the NMSE performance of AoD versus SNR
for our proposed scheme, which is compared with the MUSIC-
based method [4], orthogonal matching pursuit (OMP) method
[30] and the CRLB. The results demonstrate that the perfor-
mance of our proposed scheme exhibits exponential improve-
ment as the SNR increases. Also, the proposed scheme can
achieve the lowest NMSE compared with the MUSIC-based
method and OMP method, and is relatively close to the CRLB.
The performance gain of our proposed method arises from the
ability to capture the intrinsic multidimensional structure of the
multi-way data and the gridless processing approach, which

10
1 2 3 4 5 6 7 8 9 10
The number of iterations T
10-8
10-7
10-6
10-5
10-4
NMSE (Delay)
SNR=-10 dB
SNR=0 dB
SNR=10 dB
SNR=20 dB
Fig. 7. The NMSE performance of delay estimation versus the number of
iterations T .
1 2 3 4 5 6 7 8 9 10
The number of iterations T
10-6
10-5
10-4
10-3
10-2
NMSE (Doppler shift)
SNR=-10 dB
SNR=0 dB
SNR=10 dB
SNR=20 dB
Fig. 8. The NMSE performance of Doppler shift estimation versus the
number of iterations T .
helps to be free from the grid discretization error. What’s
more, the performance of the MUSIC method is constrained
by the number of transmitted antennas, and the OMP method
is limited by the grid resolution.
We further investigate the AoA estimation performance of
our proposed scheme in Fig. 6 for mixed NF and FF targets.
Different from AoD estimation, AoA estimation is affected by
the presence of near-field targets. We compare the NMSE per-
formance of our proposed scheme with the FF-based scheme,
which only considers the plane wavefront, the subspace-based
method [44], and the CRLB. We can observe that our proposed
scheme achieves superior performance and closely approaches
the corresponding CRLB. For the near-field target, the impact
of the spherical wavefront propagation becomes significant,
which is neglected in the FF-based scheme. Therefore, the FF-
based scheme has the worst performance. More importantly,
our proposed scheme also has a performance gain compared
with the subspace-based method due to the ability to capture
the intrinsic multidimensional structure of received signals and
the ability to avoid inter-target interference.
Next, we investigate the convergence performance of the
proposed Algorithm 2 for delay and Doppler shift estimation.
-10 -5 0 5 10 15 20
SNR (dB)
10-9
10-8
10-7
10-6
10-5
10-4
10-3
10-2
NMSE (Delay)
CS [19]
AML [24], grid=0.1
AML [24], grid=0.01
AML [24], grid=0.001
Proposed
CRLB
Fig. 9. The NMSE performance of delay estimation versus SNR.
-10 -5 0 5 10 15 20
SNR (dB)
10-7
10-6
10-5
10-4
10-3
10-2
10-1
100
NMSE (Doppler shift)
CS [19]
AML [24], grid=0.1
AML [24], grid=0.01
AML [24], grid=0.001
Proposed
CRLB
Fig. 10. The NMSE performance of Doppler shift estimation versus SNR.
Fig. 7 and Fig. 8 illustrate the NMSE performance of the
proposed Algorithm 2 versus the number of iterations T
under different SNRs for delay and Doppler shift estimation,
respectively. It is obvious that, as the number of iterations in-
creases, the estimation performance of both delay and Doppler
shift progressively enhanced and ultimately converged. This
implies that our proposed scheme can rapidly converge to
a stationary solution. Specifically, our proposed Algorithm 2
only requires around 3 iterations for convergence. In the rest of
our experiments, we shall use T = 3 unless otherwise noted.
Fig. 9 and Fig. 10 provide the NMSE performance of the de-
lay and Doppler shift estimation versus SNR, respectively. For
comparison, we apply the compressed sensing (CS) method
[19], the approximate maximum likelihood (AML) method
with different delay and Doppler shift resolutions [24], and
CRLB as benchmarks. We again notice that the performance
of our proposed scheme approaches the associated CRLB.
However, the CS method is strictly limited by the sampling
rate and bandwidth, which can only estimate the integer
components of normalized delay and Doppler shift, resulting
in the worst performance. The performance of the AML
method is under the control of the searching resolution and has
a complexity of O

R (lmax + 1) (2αmax + 1) N 2cετ εf , where

11
ετ is the searching grid resolution of delay and εf is the
searching grid resolution of Doppler shift. We compare with
the performance of AML method [24] in the case of choosing
different resolutions of ετ = εf = 0.1, ετ = εf = 0.01, and
ετ = εf = 0 .001. It is obvious that higher resolution leads
to better estimation performance, but at the cost of increased
computational complexity. Our proposed method can achieve
the same performance as the case of ετ = εf = 0.001 but with
much lower complexity. To be specific, the complexity for the
case of ετ = εf = 0.001 for AML is of order O
 
1012 while
our proposed method has the complexity of order O
 
104 in
the same simulation setup.
VII. C ONCLUSION
In this paper, we proposed a novel angle-delay-Doppler
estimation scheme for the AFDM-ISAC system in mixed
NF and FF scenarios. Based on the echoes reflected by the
targets, the AoDs, AoAs, delays and Doppler shifts can be
respectively estimated via a structured tensor decomposition
based method. Specifically, we formulated the received ISAC
signal as a third-order tensor with factor matrices containing
sensing target parameters. We then applied a structured CP
decomposition method by employing the Vandermonde nature
of the factor matrix and the spatial smoothing. Subsequently,
we developed a subspace-based method that avoids high-
complexity eigendecomposition for AoA estimation in mixed
NF and FF scenario. By leveraging the full representation of
channel delay-Doppler profile provided by AFDM in the DAF
domain, we also proposed a joint delay-Doppler estimation
scheme, where the fractional components can be estimated by
using one-dimensional iterative process for sensing enhance-
ment with low complexity. Simulation results validated the
accuracy of our proposed method and demonstrated that the
performance of the proposed scheme outperforms the other
benchmark schemes and also close to that of the corresponding
CRLB.
APPENDIX
DERIVATION OF CRLB
The observation tensor Y ∈ CG×Nc×K has the expression
of
Y = [ [γ; AR, BC, AT ] ] +W. (46)
Let A = AR, B = BC and C = diag (γ) AT . Therefore,
the log-likelihood function of Ψ can be written as
L (Ψ) = f (Y; A, B, C)
= −GNcK ln
 
πσ 2 − 1σ2 


YT(1) − (C ⊙ B) AT 


2F
= −GNcK ln
 
πσ 2 − 1σ2 


YT(2) − (C ⊙ A) BT 


2F
= −GNcK ln
 
πσ 2 − 1σ2 


YT(3) − (B ⊙ A) CT 


2F ,
(47)
where σ2 is the noise variance. The Fisher information matrix
(FIM) for Ψ is given by [51]
Ω (Ψ) = E
( ∂L (Ψ)
∂Ψ
H  ∂L (Ψ)
∂Ψ
)
. (48)
For problems considered in this paper, (48) is equivalent to
Ω (Ψ) =


Ωθθ Ωθr0 Ωθτ Ωθfd Ωθϕ Ωθγ
ΩHθr0 Ωr0r0 Ωr0τ Ωr0fd Ωr0ϕ Ωr0γ
ΩHθτ ΩHr0τ Ωτ τ Ωτ fd Ωτ ϕ Ωτ γ
ΩHθfd ΩHr0fd ΩHτ fd Ωfdfd Ωfdϕ Ωfdγ
ΩHθϕ ΩHr0ϕ ΩHτ ϕ ΩHfdϕ Ωϕϕ Ωϕγ
ΩHθγ ΩHr0γ ΩHτ γ ΩHfdγ ΩHϕγ Ωγγ

 .
(49)
We first compute the partial derivative ofL (Ψ) with respect
to Ψ. According to [49], the partial derivative of L (Ψ) with
respect to θr can be expressed as
∂L (Ψ)
∂θr
= tr
( ∂L (Ψ)
∂A
T ∂A
∂θr
+
 ∂L (Ψ)
∂A∗
T ∂A∗
∂θr
)
,
(50)
where
∂L (Ψ)
∂A = 1σ2 YT(1) − (C ⊙ B) AT H (C ⊙ B) ,
∂L (Ψ)
∂A∗ =
 ∂L (Ψ)
∂A
∗
,
∂A
∂θr
=
 0 · · ·˜ aθ,r · · ·0  ,
with ˜ aθ,r = ∂aR(θr,r0,r)∂θr . Therefore, (50) can be calculated as
∂L (Ψ)
∂θr
= 2 Re

eTr 1σ2 (C ⊙ B)T ˜Y∗1 ˜Aθer

, (51)
where ˜Y1 = YT(1) − (C ⊙ B) AT , er is a canonical vector
whose non-zero element has the index of r, Re (·) is the real
part extraction operator, and ˜Aθ = [˜ aθ,1, ˜ aθ,2, ...,˜ aθ,R].
Similarly, the partial derivatives with respect to other pa-
rameters can be respectively expressed as
∂L (Ψ)
∂r0,r
= 2 Re

eTr 1σ2 (C ⊙ B)T ˜Y∗1 ˜Ar0 er

,
∂L (Ψ)
∂τr
= 2 Re

eTr 1σ2 (C ⊙ A)T ˜Y∗2 ˜Bτ er

,
∂L (Ψ)
∂fd,r
= 2 Re

eTr 1σ2 (C ⊙ A)T ˜Y∗2 ˜Bf er

,
∂L (Ψ)
∂ϕr
= 2 Re

eTr 1σ2 (B ⊙ A)T ˜Y∗3 ˜Cer

,
∂L (Ψ)
∂γr
= eTr 1σ2 (B ⊙ A)T ˜Y∗3AT er,
with ˜Y2 = YT(2) − (C ⊙ A) BT , ˜Y3 = YT(3) −
(B ⊙ A) CT and ˜Ar0 = [ ˜ ar0,1, ˜ ar0,2, ...,˜ ar0,R], ˜Bτ =h
˜bτ,1, ˜bτ,2, ...,˜bτ,R
i
, ˜Bf =
h
˜bf,1, ˜bf,2, ...,˜bf,R
i
, ˜C =
[˜ c1, ˜ c2, ...,˜ cR], where ˜ ar0,r = ∂aR(θr,r0,r)∂r0,r , ˜bτ,r = ∂b(βr,νr)∂τr ,
˜bf,r = ∂b(βr,νr)∂fd,r and ˜ cr = γr∂aT (ϕr)∂ϕr for r = 1, ..., R.Next, we do the calculation for components in the principal
minors of the FIM. The (r1, r2)-th entry of
Ωθθ = E
( ∂L (Ψ)
∂θ
H  ∂L (Ψ)
∂θ
)
(52)

12
is given by
E
 ∂L (Ψ)
∂θr1
∗  ∂L (Ψ)
∂θr2

= Cnaθ (m, n)+C∗naθ (m, n),
(53)
where m = R(r1 − 1) + r1, n = R(r2 − 1) + r2 and Cnaθ =
E

naθ nHaθ
	
with naθ = 1σ2

˜ATθ ⊗ (C ⊙ B)T

vec

WH(1)

.
Similarly, other components in the principal minors of
Ω (Ψ) can also be calculated by
E
 ∂L (Ψ)
∂r0,r1
∗  ∂L (Ψ)
∂r0,r2

= Cnar0(m, n)+Cnar0(m, n)∗,
E
 ∂L (Ψ)
∂τr1
∗  ∂L (Ψ)
∂τr2

= Cnbτ (m, n)+Cnbτ (m, n)∗,
E
 ∂L (Ψ)
∂fd,r1
∗  ∂L (Ψ)
∂fd,r2

= Cnbf (m, n)+Cnbf (m, n)∗,
E
 ∂L (Ψ)
∂ϕr1
∗  ∂L (Ψ)
∂ϕr2

= Cnϕ (m, n) + Cnϕ (m, n)∗,
E
 ∂L (Ψ)
∂γr1
∗  ∂L (Ψ)
∂γr2

= Cnγ (m, n)∗.
Similarly to naθ,
nar0 = 1σ2  ˜ATr0 ⊗ (C ⊙ B)T  vec WH(1) ,
nbτ =

˜BTτ ⊗ (C ⊙ A)T

vec

WH(2)

,
nbf =

˜BTf ⊗ (C ⊙ A)T

vec

WH(2)

,
nϕ =

˜CT ⊗ (B ⊙ A)T

vec

WH(3)

,
nγ =

ATT ⊗ (B ⊙ A)T

vec

WH(3)

.
For the elements in the off-principal minors, we can obtain
E
 ∂L (Ψ)
∂θr1
∗  ∂L (Ψ)
∂r0,r2

= 2 Re

Cnaθ ,nar0 (m, n)

,
E
 ∂L (Ψ)
∂θr1
∗  ∂L (Ψ)
∂τr2

= 2 Re

Cnaθ ,nbτ (m, n)

,
E
 ∂L (Ψ)
∂θr1
∗  ∂L (Ψ)
∂fd,r2

= 2 Re

Cnaθ ,nbf (m, n)

,
E
 ∂L (Ψ)
∂θr1
∗  ∂L (Ψ)
∂ϕr2

= 2 Re

Cnaθ ,nϕ (m, n)

,
E
 ∂L (Ψ)
∂θr1
∗  ∂L (Ψ)
∂γr2

= Cnaθ ,nγ (m, n)∗,
E
 ∂L (Ψ)
∂r0,r1
∗  ∂L (Ψ)
∂τr2

= 2 Re

Cnar0 ,nbτ (m, n)

,
E
 ∂L (Ψ)
∂r0,r1
∗  ∂L (Ψ)
∂fd,r2

= 2 Re

Cnar0 ,nbf (m, n)

,
E
 ∂L (Ψ)
∂r0,r1
∗  ∂L (Ψ)
∂ϕr2

= 2 Re

Cnar0 ,nϕ (m, n)

,
E
 ∂L (Ψ)
∂r0,r1
∗  ∂L (Ψ)
∂γr2

= Cnar0 ,nγ (m, n)∗,
E
 ∂L (Ψ)
∂τr1
∗  ∂L (Ψ)
∂fd,r2

= 2 Re

Cnbτ ,nbf (m, n)

,
E
 ∂L (Ψ)
∂τr1
∗  ∂L (Ψ)
∂ϕr2

= 2 Re
 
Cnbτ ,nϕ (m, n)

,
E
 ∂L (Ψ)
∂τr1
∗  ∂L (Ψ)
∂γr2

= Cnbτ ,nγ (m, n)∗,
E
 ∂L (Ψ)
∂fd,r1
∗  ∂L (Ψ)
∂ϕr2

= 2 Re

Cnbf ,nϕ (m, n)

,
E
 ∂L (Ψ)
∂fd,r1
∗  ∂L (Ψ)
∂γr2

= Cnbf ,nγ (m, n)∗,
E
 ∂L (Ψ)
∂ϕr1
∗  ∂L (Ψ)
∂γr2

= Cnϕ,nγ (m, n)∗,
where
Cnaθ ,nar0= 1σ2  ˜Aθ ⊗ (C ⊙ B)T ˜A∗r0 ⊗ (C ⊙ B)∗ ,
Cnaθ ,nbτ= 1σ4  ˜Aθ ⊗ (C ⊙ B)TCw1,w2 ˜B∗τ ⊗ (C ⊙ A)∗ ,
Cnaθ ,nbf= 1σ4  ˜Aθ ⊗ (C ⊙ B)TCw1,w2 ˜B∗f ⊗ (C ⊙ A)∗ ,
Cnaθ ,nϕ= 1σ4  ˜Aθ ⊗ (C ⊙ B)TCw1,w3 ˜C∗ ⊗ (B ⊙ A)∗ ,
Cnaθ ,nγ= 1σ4  ˜Aθ ⊗ (C ⊙ B)TCw1,w3 A∗T ⊗ (B ⊙ A)∗ ,
Cnar0 ,nbτ= 1σ4  ˜Ar0 ⊗ (C ⊙ B)TCw1,w2 ˜B∗τ ⊗ (C ⊙ A)∗ ,
Cnar0 ,nbf= 1σ4  ˜Ar0 ⊗ (C ⊙ B)TCw1,w2 ˜B∗f ⊗ (C ⊙ A)∗ ,
Cnar0 ,nϕ= 1σ4  ˜Ar0 ⊗ (C ⊙ B)TCw1,w3 ˜C∗ ⊗ (B ⊙ A)∗ ,
Cnar0 ,nγ= 1σ4  ˜Ar0 ⊗ (C ⊙ B)TCw1,w3 A∗T ⊗ (B ⊙ A)∗ ,
Cnbτ ,nbf= 1σ2  ˜Bτ ⊗ (C ⊙ A)T ˜B∗f ⊗ (C ⊙ A)∗ ,
Cnbτ ,nϕ= 1σ4  ˜Bτ ⊗ (C ⊙ A)TCw2,w3 ˜C∗ ⊗ (B ⊙ A)∗ ,
Cnbτ ,nγ= 1σ4  ˜Bτ ⊗ (C ⊙ A)TCw2,w3 A∗T ⊗ (B ⊙ A)∗ ,
Cnbf ,nϕ= 1σ4  ˜Bf ⊗ (C ⊙ A)TCw2,w3 ˜C∗ ⊗ (B ⊙ A)∗ ,
Cnbf ,nγ= 1σ4  ˜Bf ⊗ (C ⊙ A)TCw2,w3 A∗T ⊗ (B ⊙ A)∗ ,
Cnϕ,nγ= 1σ2  ˜C ⊗ (B ⊙ A)T A∗T ⊗ (B ⊙ A)∗ ,
in which the covariance matrix for the noise is expressed as
Cwp,wq = E

vec

WH(p)

vec

WT(q)
T 
, p̸= q. (54)
Finally, the CRLB for the estimated parameters can be
calculated by (45).

13
REFERENCES
[1] D. C. Nguyen, M. Ding, P. N. Pathirana, A. Seneviratne, J. Li, D. Niyato,
O. Dobre, and H. V . Poor, “6G internet of things: A comprehensive
survey,” IEEE Internet Things J. , vol. 9, no. 1, pp. 359–383, Jan. 2022.
[2] Z. Zhang, Y . Xiao, Z. Ma, M. Xiao, Z. Ding, X. Lei, G. K. Karagiannidis,
and P. Fan, “6G wireless networks: vision, requirements, architecture,
and key technologies,” IEEE V eh. Technol. Mag. , vol. 14, no. 3, pp.
28–41, Sep. 2019.
[3] L. Meng, Y . L. Guan, Y . Ge, and Z. Liu, “Flag sequence set design
for low-complexity delay-doppler estimation,” IEEE Transactions on
V ehicular Technology, pp. 1–17, 2025.
[4] F. Liu, C. Masouros, A. P. Petropulu, H. Griffiths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun. , vol. 68, no. 6, pp. 3834–3862, Jun.
2020.
[5] Z. Wei, H. Qu, Y . Wang, X. Yuan, H. Wu, Y . Du, K. Han, N. Zhang, and
Z. Feng, “Integrated sensing and communication signals toward 5G-A
and 6G: A survey,” IEEE Internet Things J. , vol. 10, no. 13, pp. 11 068–
11 092, July 2023.
[6] T. Wang, J. Proakis, E. Masry, and J. Zeidler, “Performance degradation
of OFDM systems due to Doppler spreading,” IEEE Trans. Wireless
Commun., vol. 5, no. 6, pp. 1422–1432, Jun. 2006.
[7] Y . Zhao and S. G. Haggman, “Intercarrier interference self-cancellation
scheme for OFDM mobile communication systems,” IEEE Trans. Com-
mun., vol. 49, no. 7, pp. 1185–1191, Jul. 2001.
[8] R. Hadani, S. Rakib, M. Tsatsanis, A. Monk, A. J. Goldsmith, A. F.
Molisch, and R. Calderbank, “Orthogonal time frequency space mod-
ulation,” in Proc. IEEE Wireless Commun. Net. Conf. (WCNC) , Mar.
2017, pp. 1–6.
[9] Z. Wei, W. Yuan, S. Li, J. Yuan, G. Bharatula, R. Hadani, and
L. Hanzo, “Orthogonal time-frequency space modulation: A promising
next-generation waveform,” IEEE Wireless Commun., vol. 28, no. 4, pp.
136–144, Aug. 2021.
[10] Q. Deng, Y . Ge, and Z. Ding, “A unifying view of OTFS and its many
variants,” IEEE Commun. Surv. Tuts. , pp. 1–1, 2025.
[11] Z. Wei, W. Yuan, S. Li, J. Yuan, and D. W. K. Ng, “Off-grid channel
estimation with sparse bayesian learning for OTFS systems,” IEEE
Trans. on Wireless Commun. , vol. 21, no. 9, pp. 7407–7426, Sep. 2022.
[12] J. Wu, W. Yuan, Z. Wei, K. Zhang, F. Liu, and D. Wing Kwan Ng,
“Low-complexity minimum BER precoder design for ISAC systems: A
delay-doppler perspective,” IEEE Trans. on Wireless Commun. , vol. 24,
no. 2, pp. 1526–1540, Feb. 2025.
[13] X. Ouyang and J. Zhao, “Orthogonal chirp division multiplexing,” IEEE
Trans. Commun., vol. 64, no. 9, pp. 3946–3957, Sep. 2016.
[14] M. S. Omar and X. Ma, “Performance analysis of OCDM for wireless
communications,” IEEE Trans. Wireless Commun. , vol. 20, no. 7, pp.
4032–4043, Jul. 2021.
[15] A. Bemani, N. Ksairi, and M. Kountouris, “Affine frequency division
multiplexing for next generation wireless communications,” IEEE Trans.
Wireless Commun., vol. 22, no. 11, pp. 8214–8229, Nov. 2023.
[16] Q. Luo, P. Xiao, Z. Liu, Z. Wan, N. Thomos, Z. Gao, and Z. He,
“AFDM-SCMA: A promising waveform for massive connectivity over
high mobility channels,” IEEE Trans. Wireless Commun., vol. 23, no. 10,
pp. 14 421–14 436, Oct. 2024.
[17] K. Zheng, M. Wen, T. Mao, L. Xiao, and Z. Wang, “Channel estimation
for AFDM with superimposed pilots,” IEEE Trans. V eh. Technol. , pp.
1–6, 2024.
[18] Y . Tao, M. Wen, Y . Ge, J. Li, E. Basar, and N. Al-Dhahir, “Affine
frequency division multiplexing with index modulation: Full diversity
condition, performance analysis, and low-complexity detection,” IEEE
J. Sel. Areas Commun. , vol. 43, no. 4, pp. 1041–1055, Apr. 2025.
[19] W. Benzine, A. Bemani, N. Ksairi, and D. Slock, “Affine frequency divi-
sion multiplexing for compressed sensing of time-varying channels,” in
Proc. IEEE 25th Int. Workshop Signal Process. Adv. Wireless Commun.
(SPA WC), Sep. 2024.
[20] H. Yin, X. Wei, Y . Tang, and K. Yang, “Diagonally reconstructed channel
estimation for MIMO-AFDM with inter-doppler interference in doubly
selective channels,” IEEE Trans. Wireless Commun. , vol. 23, no. 10, pp.
14 066–14 079, Oct. 2024.
[21] K. R. R. Ranasinghe, H. S. Rou, G. T. F. De Abreu, T. Takahashi, and
K. Ito, “Joint channel, data and radar parameter estimation for AFDM
systems in doubly-dispersive channels,” IEEE Trans. Wireless Commun.,
2024, early access.
[22] J. Zhu, Y . Tang, F. Liu, X. Zhang, H. Yin, and Y . Zhou, “AFDM-
based bistatic integrated sensing and communication in static scatterer
environments,” IEEE Commun. Lett. , vol. 13, no. 8, pp. 2245–2249,
Aug. 2024.
[23] Y . Ni, Z. Wang, P. Yuan, and Q. Huang, “An AFDM-based integrated
sensing and communications,” in Proc. Int. Sym. Wireless Commun. Syst.
(ISWCS), Oct 2022, pp. 1–6.
[24] A. Bemani, N. Ksairi, and M. Kountouris, “Integrated sensing and
communications with affine frequency division multiplexing,” IEEE
Wireless Commun. Lett. , vol. 13, no. 5, pp. 1255–1259, May 2024.
[25] Y . Luo, Y . Guan, Y . Ge, and C. Yuen, “Target sensing with off-grid
sparse bayesian learning for AFDM-ISAC system,” arXiv:2503.10011,
2025.
[26] Z. Xiao, R. Liu, M. Li, Q. Liu, and A. L. Swindlehurst, “A novel
joint angle-range-velocity estimation method for MIMO-OFDM ISAC
systems,” IEEE Trans. Signal Process. , vol. 72, pp. 3805–3818, Aug.
2024.
[27] L. Leyva, D. Castanheira, A. Silva, and A. Gameiro, “Two-stage
estimation algorithm based on interleaved OFDM for a cooperative
bistatic ISAC scenario,” in Proc. IEEE 95th V eh. Technol. Conf. (VTC-
Spring), Jun. 2022, pp. 1–6.
[28] Y . Xiang, Y . Gao, X. Yang, S. Kang, and M. Shao, “An ESPRIT-based
moving target sensing method for MIMO-OFDM ISAC system,” IEEE
Commun. Lett. , vol. 27, no. 12, pp. 3205–3209, Dec. 2023.
[29] Z. Gao, C. Hu, L. Dai, and Z. Wang, “Channel estimation for millimeter-
wave massive MIMO with hybrid precoding over frequency-selective
fading channels,” IEEE Commun. Lett. , vol. 20, no. 6, pp. 1259–1262,
Jun. 2016.
[30] J. Lee, G.-T. Gil, and Y . H. Lee, “Channel estimation via orthogonal
matching pursuit for hybrid MIMO systems in millimeter wave com-
munications,” IEEE Trans. Commun. , vol. 64, no. 6, pp. 2370–2386,
Jun. 2016.
[31] Z. Zhou, J. Fang, L. Yang, H. Li, Z. Chen, and R. S. Blum, “Low-
rank tensor decomposition-aided channel estimation for millimeter wave
MIMO-OFDM systems,” IEEE J. Sel. Areas Commun. , vol. 35, no. 7,
pp. 1524–1538, Jul. 2017.
[32] Y . Lin, S. Jin, M. Matthaiou, and X. You, “Tensor-based channel esti-
mation for millimeter wave MIMO-OFDM with dual-wideband effects,”
IEEE Trans. Commun. , vol. 68, no. 7, pp. 4218–4232, Jul. 2020.
[33] R. Zhang, L. Cheng, S. Wang, Y . Lou, W. Wu, and D. W. K. Ng, “Tensor
decomposition-based channel estimation for hybrid mmwave massive
MIMO in high-mobility scenarios,” IEEE Trans. Commun. , vol. 70,
no. 9, pp. 6325–6340, Sep. 2022.
[34] D. Nion and N. D. Sidiropoulos, “Tensor algebra and multidimensional
harmonic retrieval in signal processing for MIMO radar,” IEEE Trans.
Signal Process., vol. 58, no. 11, pp. 5693–5705, Nov. 2010.
[35] M. Cao, S. A. V orobyov, and A. Hassanien, “Transmit array interpolation
for DOA estimation via tensor decomposition in 2-D MIMO radar,”
IEEE Trans. Signal Process. , vol. 65, no. 19, pp. 5225–5239, Oct. 2017.
[36] X. Li, B. Chang, and Z. Chen, “Tensor decomposition based THz
channel estimation in OTFS for integrated sensing and communications,”
in Proc. IEEE Global Comm. Conf. , Dec. 2023, pp. 3996–4001.
[37] R. Zhang et al. , “Integrated sensing and communication with massive
MIMO: A unified tensor approach for channel and target parameter
estimation,” IEEE Trans. Wireless Commun. , vol. 23, no. 8, pp. 8571–
8587, Aug. 2024.
[38] Y . Luo, Y . Guan, and E. Gunawan, “Uplink sensing with unknown
transmitter position in clutter environment via tensor decomposition,”
in Proc. IEEE 97th V eh. Technol. Conf. (VTC-Spring) , Jun. 2023, pp.
1–5.
[39] M. Cui and L. Dai, “Channel estimation for extremely large-scale
MIMO: Far-field or near-field?” IEEE Trans. Commun. , vol. 70, no. 4,
pp. 2663–2677, Jan. 2022.
[40] L. Wei, C. Huang, G. C. Alexandropoulos, Z. Yang, J. Yang, W. E. I.
Sha, Z. Zhang, M. Debbah, and C. Yuen, “Tri-polarized holographic
MIMO surfaces for near-field communications: Channel modeling and
precoding design,” IEEE Trans. Wireless Commun. , vol. 22, no. 12, pp.
8828–8842, Dec. 2023.
[41] Y . Pan, C. Pan, S. Jin, and J. Wang, “RIS-aided near-field localization
and channel estimation for the terahertz system,” IEEE J. Sel. Topics
Signal Process., vol. 17, no. 4, pp. 878–892, Jul. 2023.
[42] Z. Wang, X. Mu, and Y . Liu, “Near-field integrated sensing and
communications,” IEEE Commun. Lett. , vol. 27, no. 8, pp. 2048–2052,
Aug. 2023.
[43] H. Li, Z. Wang, X. Mu, P. Zhiwen, and Y . Liu, “Near-field integrated
sensing, positioning, and communication: A downlink and uplink frame-
work,” IEEE J. Sel. Areas Commun. , vol. 42, no. 9, pp. 2196–2212, Sep.
2024.

14
[44] W. Zuo, J. Xin, N. Zheng, and A. Sano, “Subspace-based localization
of far-field and near-field signals without eigendecomposition,” IEEE
Trans. Signal Process. , vol. 66, no. 17, pp. 4461–4476, Sep. 2018.
[45] Z. Zheng, M. Fu, W.-Q. Wang, S. Zhang, and Y . Liao, “Localization
of mixed near-field and far-field sources using symmetric double-nested
arrays,” IEEE Trans. on Antennas and Propagation , vol. 67, no. 11, pp.
7059–7070, Nov. 2019.
[46] J. B. Kruskal, “Three-way arrays: Rank and uniqueness or trilinear de-
compositions, with applications to arithmetic complexity and statistics,”
Linear Algebra Appl. , vol. 18, no. 2, pp. 95–138, 1977.
[47] M. Sørensen and L. D. Lathauwer, “Blind signal separation via tensor
decomposition with vandermonde factor: Canonical polyadic decompo-
sition,” IEEE Trans. Signal Process. , vol. 61, no. 22, pp. 5507–5519,
Aug. 2013.
[48] E. Fishler, M. Grosmann, and H. Messer, “Detection of signals by
information theoretic criteria: General asymptotic performance analysis,”
IEEE Trans. Signal Process. , vol. 50, no. 5, pp. 1027–1036, May 2002.
[49] T. Kolda and B. Bader, “Tensor decompositions and applications,” SIAM
Rev., vol. 51, no. 3, pp. 455–500, Sep. 2009.
[50] S. M. Kay, Fundamentals of Statistical Signal Processing: Estimation
Theory. Prentice Hall, 1993.
[51] X. Liu and N. D. Sidiropoulos, “Cramer-Rao lower bounds for low-
rank decomposition of multidimensional arrays,” IEEE Trans. Signal
Process., vol. 49, no. 9, pp. 2074–2086, Sep. 2001.