---
title: "Diagonally Reconstructed Channel Estimation for MIMO-AFDM With Inter-Doppler Interference in Doubly Selective Channels"
zotero_key: "KAZLUQJK"
pdf_key: "J9MI4NV7"
doi: "10.1109/twc.2024.3408458"
collection: "信道估计"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# Diagonally Reconstructed Channel Estimation for MIMO-AFDM With Inter-Doppler Interference in Doubly Selective Channels — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
Diagonally Reconstructed Channel Estimation for
MIMO-AFDM with Inter-Doppler Interference in
Doubly Selective Channels
Haoran Yin, Xizhang Wei, Yanqun Tang, and Kai Yang, Member, IEEE
Abstract
On the heels of orthogonal time frequency space (OTFS) modulation, the recently discovered
affine frequency division multiplexing (AFDM) is a promising waveform for the sixth-generation
wireless network. In this paper, we study the widely-used embedded pilot-aided (EPA) chan-
nel estimation in multiple-input multiple-output AFDM (MIMO-AFDM) system with fractional
Doppler shifts. We first formulate the vectorized input-output relationship of MIMO-AFDM, and
theoretically prove that MIMO-AFDM can achieve full diversity in doubly selective channels.
Then we illustrate the implementation of EPA channel estimation in MIMO-AFDM and unveil
that serious inter-Doppler interference (IDoI) occurs if we try to estimate the channel gain,
delay shift, and Doppler shift of each propagation path. To address this issue, the diagonal
reconstructability of AFDM subchannel matrix is studied and a low-complexity embedded pilot-
aided diagonal reconstruction (EPA-DR) channel estimation scheme is proposed. The EPA-DR
scheme calculates the AFDM effective channel matrix directly without estimating the three
channel parameters, eliminating the severe IDoI inherently. Since the effective channel matrix
is necessary for MIMO-AFDM receive processing, we believe this is an important step to bring
AFDM towards practical communication systems. Finally, we investigate the orthogonal resource
allocation of affine frequency division multiple access (AFDMA) system. Simulation results validate
the effectiveness of the proposed EPA-DR scheme.
Index Terms
MIMO-AFDM, DAFT domain, doubly selective channels, diversity analysis, channel estimation,
AFDMA.
This work was supported by Guangdong Natural Science Foundation under Grant 2019A1515011622. ( Corresponding author:
Yanqun Tang.)
Haoran Yin, Xizhang Wei, and Yanqun Tang are with the School of Electronics and Communication Engineering, Sun Yat-sen
University, China (e-mail: yinhr6@mail2.sysu.edu.cn, weixzh7@mail.sysu.edu.cn, tangyq8@mail.sysu.edu.cn).
Kai Yang is with the School of Information and Electronics, Beijing Institute of Technology, Beijing, China (email:
yangkai@ieee.org).
arXiv:2206.12822v6  [cs.IT]  28 Aug 2023

2
I. I NTRODUCTION
The sixth-generation wireless network is envisioned to provide ultra-reliable, high data rate,
and low-latency communications in high-mobility scenarios, including vehicle-to-vehicle (V2V),
unmanned aerial vehicles (UA V), high-speed trains, and low-earth-orbit satellite (LEOS), etc.
The dynamic channels therein are characterized by heavy delay-Doppler spreads, which cast a
huge challenge to the current widely adopted waveforms, such as orthogonal frequency division
multiplexing (OFDM). The non-negligible Doppler shifts greatly devastate the orthogonality
between the subcarriers in OFDM, which is a serious problem especially in the case of higher
frequency bands used in the future communication systems [1], [2]. Therefore, many efforts have
been made to design a new modulation waveform to accommodate time- and frequency-selective
channels. In particular, a two-dimensional (2D) modulation waveform named orthogonal time
frequency space (OTFS) has attracted substantial attention [3], [4]. The main idea of OTFS is
multiplexing the information symbols in the delay-Doppler (DD) domain, where a quasi-static
channel representation can be obtained. The recent works on OTFS have shown the performance
superiority of OTFS over OFDM in both single-antenna and multiple-antenna systems [5]–[14].
However, a disadvantage of OTFS is the heavy guard symbol overhead when conducting the
widely used embedded pilot-aided (EPA) channel estimation due to its 2D structure [15].
Another promising candidate is affine frequency division multiplexing (AFDM), which is a
newly discovered waveform and always attains full diversity in doubly selective channels [16].
Information symbols in AFDM are multiplexed on a set of orthogonal chirps via inverse discrete
affine Fourier transform (DAFT), which is a generalization of the widely adopted inverse discrete
Fourier transform (DFT) [17], [18]. It is shown in [16] that the AFDM modulation/demodulation
can be implemented efficiently using the OFDM modulator/demodulator as an inner core. More-
over, by tuning the chirp slope according to the Doppler profile of the channel appropriately,
AFDM manages to separate the propagation paths with distinct delay or Doppler shifts in the
one-dimensional DAFT domain. Hence, similar to OTFS, AFDM can transform a time-variant
channel in the time-frequency domain into a quasi-time-invariant channel. Some recent works are
conducted to unleash the potential of AFDM. For example, by exploring the diagonal property of
the AFDM effective channel matrix, a weighted maximal-ratio combining based low-complexity
iterative decision feedback equalizer and a low-complexity MMSE detector were proposed for
AFDM signal detection in [19]. The potential of AFDM for communication at high-frequency

3
bands was presented in [20], showing that AFDM is robust against radio frequency impairments,
such as carrier frequency offset and phase noise. The suitability of AFDM for integrated sensing
and communications was investigated in [21] and [22]. Simulation results in [15], [16], [19],
[20] show that AFDM has a bit error ratio (BER) performance similar to OTFS and outperforms
OFDM greatly in doubly selective channels.
While the aforementioned excellent works have revealed the superiority of AFDM, they all
assume perfect channel state information (CSI), which has to be estimated in practice. A pilot-
aided path detection based channel estimation scheme was presented in [23], where the delay
and Doppler shift of each propagation path was assumed to be the integral multiple of the sample
interval and subcarrier spacing, respectively. These assumptions are partly rational as generally a
wideband system can provide sufficient delay resolution so that fractional delay shifts do not need
to be considered [7]. However, the Doppler resolution depends on the time duration of AFDM
frame, which is typically small due to the low-latency demand and channel aging problem in
high-mobility scenarios. Assuming integer Doppler shifts in the condition of insufficient Doppler
resolution will induce significant modelling errors [24]. To tackle this problem, an embedded
pilot-aided approximated maximum likelihood (EPA-AML) channel estimation scheme was pro-
posed for single-input single-output AFDM (SISO-AFDM) in [15], where the fractional Doppler
was taken into account preliminarily. However, the authors in [15] hypothesized that the delay
shift of each propagation path is different from each other and the number of propagation paths
is known in advance. These hypotheses undermine its feasibility greatly given that the delay-
Doppler profile of any general doubly selective channel should cover the three cases listed in
Table I. Moreover, high computation complexity is required in EPA-AML, making it not suitable
for multiple-input multiple-output AFDM (MIMO-AFDM) system.
TABLE I
THREE CASES OF DELAY-DOPPLER PROFILE IN DOUBLY SELECTIVE CHANNEL
Case 1 Paths with different delay shifts and different Doppler shifts
Case 2 Paths with different delay shifts and same Doppler shift
Case 3 Paths with same delay shift and different Doppler shifts
In this paper, we aim to address the issue of MIMO-AFDM channel estimation with specific
attention to fractional Doppler shifts. To this end, we investigate the influence of fractional
Doppler shifts on the EPA channel estimation in MIMO-AFDM. In specific, we reveal that
there exists serious inter Doppler interference (IDoI) among the received pilot symbols when
two propagation paths have the same delay shift and different Doppler shifts. This casts a

4
huge challenge to the estimation of the three channel parameters of each propagation path,
i.e., the channel gain, the delay shift, and the Doppler shift. In order to avoid the IDoI, we
prove theoretically that the AFDM subchannel matrix is diagonally reconstructable, making it
possible to estimate the AFDM effective channel matrix directly rather than first estimate the
three channel parameters and then calculate it. Furthermore, we unveil that exploring the diagonal
reconstructability to perform channel estimation can inherently avoid the severe IDoI. In contrast
to the state-of-the-art method, our proposed channel estimation scheme is more robust to the
fractional Doppler and enjoys much lower computation complexity. The BER of the MIMO-
AFDM with perfect CSI and estimated CSI are compared to demonstrate the effectiveness of
the proposed algorithm. Our contributions can be summarized as follows.
• We develop the settings of MIMO-AFDM system and derive the associated input-output
relationship in the DAFT domain. Based on that, we extend the diversity analysis of SISO-
AFDM in [15] to MIMO-AFDM with perfect CSI. It is shown that MIMO-AFDM can
achieve full diversity in doubly selective channels, where the full diversity order refers to
the number of receive antennas multiplied by the number of paths that are separable in
either delay or Doppler domain.
• After demonstrating the implementation of EPA channel estimation in MIMO-AFDM, we
study the interference among the received pilot symbols caused by fractional Doppler. We
reveal that there are four kinds of interference, namely inter-Doppler interference (IDoI),
inter-delay interference (IDI), inter-pilot interference (IPI), and inter-pilot-data interference
(IPDI). Among them, the IDoI is the most serious and impossible to be eliminated if we
try to estimate the channel gain, delay shift, and Doppler shift of each propagation path.
• Next, we prove that the AFDM subchannel matrix can be diagonally reconstructed by
utilizing some precalculable transform factors iteratively. Based on this unique characteristic,
we propose a low-complexity channel estimation method named embedded pilot-aided
diagonal reconstruction (EPA-DR), which can avoid IDoI perfectly.
• Finally, we propose an orthogonal resource allocation scheme for affine frequency division
multiple access (AFDMA) system based on the EPA-DR channel estimation method. By
exploring the differences in the delay-Doppler profiles between the base station and all the
users, we manage to reduce the guard symbol overhead to the greatest extent.
The rest of this paper is organized as follows. Section II reviews the basic concepts of AFDM

5
and introduces MIMO-AFDM system, which lays the foundations for the interference analysis of
the EPA channel estimation in Section III. Section IV presents the EPA-DR channel estimation
method for MIMO-AFDM, followed by the resource allocation for AFDMA in Section V.
Simulation results are presented in Section VI, while Section VII concludes this paper.
Notations: Symbols a[i] and A[i, j] denote the i-th element of a and the ( i, j)-th element of
A respectively; C denotes the set of complex numbers and CM ×N denotes the set of all M × N
matrices with complex entries; IN denotes the identity matrix of size N × N; a ∼ CN(0, N0IN )
means that a follows the complex Gaussian distribution with zero mean and covariance N0IN;
δ(·) denotes the Dirac delta function; diag(·) denotes a square diagonal matrix with the elements
of input vector on the main diagonal; (·)∗, (·)H, (·)T , and ∥·∥ denote the conjugate, Hermitian,
transpose, and Euclidean norm operations; |·| denotes the absolute value of a complex scalar;
(·)N denotes the modulus operation with respect to N; E[·] denotes the expectation; Q(·) denotes
the tail distribution function of the standard normal distribution.
II. AFDM S YSTEM MODEL
In this section, the basic concepts of AFDM from [15] and [16] are reviewed. Based on that,
we establish the settings of MIMO-AFDM system.
S\P
 S\P
P\S
 P\S
Doubly selective channel
IDAFT
IFFT FFT
DAFT
DiscardAdd
CPP CPP
Fig. 1. SISO-AFDM modulation/demodulation block diagrams [15].
A. AFDM modulation
1) AFDM modulation : Fig. 1 shows the modulation/demodulation block diagrams of SISO-
AFDM system. Let Ts denote sample period (delay resolution), N denote the number of subcarri-
ers (chirps), then AFDM signal has a bandwidth B = 1Ts , subcarrier spacing (Doppler resolution)
∆f = BN = 1N Ts . Let x ∈ AN ×1 denote a vector of N quadrature amplitude modulation (QAM)
symbols that reside on the DAFT domain, A represents the modulation alphabet. After the serial
to parallel operation, N-point inverse DAFT (IDAFT) is performed to map x to the time domain
as [15]
s[n] =
N −1X
m=0
x[m]ϕm[n], n = 0, · · ·, N− 1 (1)

6
where n and m denote the time and DAFT domains indices, respectively, and subcarrier ϕm[n]
is given by
ϕm[n] = 1√N ej2π(c1n2+c2m2+nm/N), m = 0, · · ·, N− 1 (2)
c1 and c2 are two AFDM parameters, where c1 determines the chirps’ slope. Equation (1) can
be written in matrix form as
s = ΛHc1FHΛHc2x = AHx (3)
where A = Λc2FΛc1 ∈ CN ×N represents the DAFT matrix, F is the DFT matrix with entries
e−j2πmn/N/√N, Λc ≜ diag e−j2πcn2, n= 0, 1, . . . , N− 1. Before transmitting s, an chirp-
periodic prefix (CPP) should be added, which plays the same role as the cyclic prefix (CP) in
OFDM to cope with the multipath propagation and makes the channel lie in a periodic domain
equivalently.
B. Channel model
Assume the doubly selective channel has the following impulse response with delay τ and
Doppler κ as
h(τ, κ) =
PX
i=1
hiδ (τ − liTs) δ (κ − νi∆f ) (4)
where P is the number of paths, hi denotes the channel gain of the i-th path, non-negative
integer li ∈ [0, lmax] is the associated delay normalized with Ts, νi = αi + βi represents the
associated Doppler shift normalized with subcarrier spacing and has a finite support bounded
by [−νmax, νmax], αi ∈ [−αmax, αmax] and βi ∈ (− 12 , 12 ] are the integer and fractional parts of
νi respectively, νmax denotes the maximum Doppler and αmax denotes its integer component. In
this paper, we assume that lmax and νmax are known in advance.
C. AFDM demodulation
At the receiver, the relationship between the received time domain symbols d and s can be
expressed as
d[n] =
PX
i=1
hie−j 2πN νins[(n − li)N ] + v[n] (5)
where v ∼ CN(0, N0) represents the additive white gaussian noise (AWGN) component. Equa-
tion (5) can be vectorized as
d =
PX
i=1
hi ˜His + v = ˜Hs + v (6)

7
where v ∼ CN(0, N0IN ) is the time domain noise vector, ˜H ∈ CN ×N denotes the effec-
tive time domain channel matrix, ˜Hi = ∆νiΠli represents the time domain subchannel ma-
trix of the i-th path (each path can be viewed as one subchannel), Π denotes the forward
cyclic-shift matrix which models the delay, while the digital frequency shift matrix ∆νi ≜
diag

e−j 2πN νin, n= 0, 1, · · ·, N− 1 models the Doppler.
Finally, N-point DAFT is implemented and d are transformed to the DAFT domain symbols
y with
y[m] =
N −1X
m=0
d[n]ϕ∗m[n] + w[m] (7)
where w represents the noise in the DAFT domain. The matrix representation of (7) is
y = Λc2FΛc1d = Ad. (8)
Since A is a unitary matrix, w has the same statistical properties as v.
D. Input-output relationship
Substituting (1) and (5) into (7), we have the input-output relationship of SISO-AFDM system
in the DAFT domain as [15]
y[m] = 1N
PX
i=1
N −1X
m′=0
hi ej 2πN (N c1l2i −m′li+N c2(m′2−m2))| {z }
C(li, m, m′)
ej2π(m+indi −m′+βi) − 1
ej 2πN (m+indi −m′+βi) − 1| {z }
Spreading factor F (li, νi, m, m′)
x[m′] + w[m] (9)
where the index indicator of the i-th path is defined as
indi ≜ (αi + 2N c1li)N . (10)
For the convenience of illustration, we define
C(li, m, m′) = ej 2πN (N c1l2i −m′li+N c2(m′2−m2)) (11)
and the spreading factor caused by fractional Doppler as
F (li, νi, m, m′) = ej2π(m+indi −m′+βi) − 1ej 2πN (m+indi −m′+βi) − 1 . (12)
The matrix form of (9) can be obtained by substituting (3) and (6) into (8) as
y =
PX
i=1
hiHix + w = Heffx + w (13)

8
where Hi = A ˜HiAH denotes the DAFT domain subchannel matrix of the i-th path, Heff =
PP
i=1 hiHi is the effective channel matrix, w ∼ CN(0, N0IN ) is the DAFT domain noise
vector. Note that
Hi[m, m′] = 1N C(li, m, m′)F (li, νi, m, m′). (14)
Remark 1: It has been proven in [15] (Theorem 1) that AFDM can achieve full diversity in
doubly selective channels as long as
c1 = 2(αmax + kν) + 12N (15)
and c2 is set as either an arbitrary irrational number or a rational number sufficiently smaller
than 12N (spacing factor kν is a non-negative integer used to combat the fractional Doppler and
will be illustrated in Section III).
E. MIMO-AFDM System
S/P IDAFT S/P DAFTP/S P/S
...
...
Doubly 
selective 
channels
Add
CPP
Discard
CPP
...
...
...
... ... ...
S/P IDAFT P/SAddCPP
 S/P DAFT P/SDiscardCPP
Fig. 2. Nt × Nr MIMO-AFDM modulation/demodulation block diagrams.
We next introduce MIMO-AFDM system with its modulation/demodulation block diagrams
provided in Fig. 2. Let Nt and Nr denote the number of transmit antennas (TA) and receive an-
tennas (RA) respectively. Then the linear system model based input-output relationship between
the r-th RA and Nt TAs from an Nt × Nr MIMO-AFDM system can be derived from (9) as
yr[m] =
NtX
t=1
PX
i=1
N −1X
m′=0
1
N h[r,t]i C(li, m, m′)F (li, νi, m, m′)xt[m′] + wr[m] (16)
where m ∈ [0, N− 1], integer r ∈ [1, Nr] and t ∈ [1, Nt] denote the index of the RA and TA
respectively, h[r,t]i is the channel gain of the i-th path between the r-th RA and the t-th TA,
wr ∼ CN(0, N0) represents the noise in DAFT domain at the r-th RA. Then the matrix form
of the input-output relationships between all pairs of RAs and TAs can be denoted as
y1 = H1,1x1 + H1,2x2 + · · ·+ H1,NtxNt + w1
...
yNr = HNr,1x1 + HNr,2x2 + · · ·+ HNr,NtxNt + wNr
(17)

9
with
Hr,t =
PX
i=1
h[r,t]i Hi (18)
representing the effective channel matrix between the r-th RA and the t-th TA, noise vector
w ∼ CN(0, N0IN ). For the sake of compactedness, we define the effective MIMO channel
matrix for the above MIMO-AFDM system as
HMIMO =

 H1,1 . . . H1,Nt... ... ...
HNr,1 . . .HNr,Nt

 (19)
where HMIMO ∈ CN Nr×N Nt, transmitted vector xMIMO = xT1 , xT2 , · · ·, xTNtT ∈ CN Nt×1, received
vector yMIMO =

yT1 , yT2 , · · ·, yTNr
T
∈ CN Nr×1, and noise vector wMIMO = wT1 , wT2 , · · ·, wTNrT ∈
CN Nr×1. Then (17) can be rewritten as
yMIMO = HMIMOxMIMO + wMIMO. (20)
Theorem 1: For a linear time-varying channel with a maximum normalized delay lmax and
maximum normalized Doppler αmax, MIMO-AFDM with parameter c1 satisfying (15) achieves
full diversity order of P Nr.
Proof: The proof is given in Appendix A.
In the sequel, we study the EPA channel estimation of MIMO-AFDM with fractional Doppler
shifts.
III. I NTERFERENCE ANALYSIS OF EPA C HANNEL ESTIMATION IN MIMO-AFDM
In practice, HMIMO must be estimated at the receiver to perform signal detection with (20).
To meet this requirement, we analyze the biggest challenge of the widely-used EPA channel
estimation in MIMO-AFDM system with fractional Doppler.
A. Effective channnel matrix analysis
We first illustrate the influence of fractional Doppler on the AFDM subchannel matrix. From
(14), we have
|Hi[m, m′]| = | 1N F (li, νi, m, m′)|. (21)
The magnitude |F (li, νi, m, m′)| reaches the peak at m′ = ( m + indi)N and decreases as m′
moves away from (m + indi)N. Therefore, in the m-th row of Hi, m ∈ [0, N− 1], the index of
entry that has the greatest magnitude, i.e., central point, is
m′ = (m + indi)N . (22)

10
0
0 ∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
Fig. 3. Structure of Hi with fractional Doppler shift [15] (the darker the color, the larger the magnitude; ‘ ∆’: the central point
in each row or column).
While the energy of the adjacent entries decays as their indices move away from (m + indi)N,
i.e., the larger the value of |m+ind i −m′|, the smaller magnitude of Hi[m, m′]. This also implies
that the non-zero entries are “diagonally” distributed in Hi, as shown in Fig. 3. Note that in the
case of integer Doppler, there is only one non-zero entry (i.e., the central point) in each row of
Hi. The “spreading” phenomenon in Hi shown in Fig. 3 is caused by fractional Doppler shift
[15], which casts a huge challenge to the CSI estimation and will be illustrated later in Section
III-C.
Moreover, submitting c1 in (15) into the index indicator defined in (10), we have
indi =
 
αi + (2(αmax + kν) + 1)li

N . (23)
It indicates that the central point of the 0-th row of Hi (i.e., indi) is determined by the delay-
Doppler profile ( li, αi) of the i-th path, αmax, and kν jointly. Fig. 4(b) shows the central points
of all the possible paths with integer delay-Doppler profiles li ∈ [0, lmax], αi ∈ [−αmax, αmax].
It can be observed that they do not overlap with each other [15]. We further distinguish them
with different colors according to their delay shifts, and hence we have lmax + 1 delay blocks
with a size of 2αmax + 1. Each delay block is surrounded by two protection bands with a size
of kν in the head and tail of it, respectively.
Define
L ≜ (lmax + 1)
 
2(αmax + kν) + 1

− 1 (24)
where L + 1 ≪ N, i.e., the channels are underspread. Then according to (18), there is a large
value non-zero band with a size of L + 1 in each row and column of Heff, as an example of
H1,1 shown in Fig. 5.

11
‘    ’: Energy from     
  .   .   .
N-10 1
(a) The energy from the 0-th row of AFDM effective channel matrix, IDI (left) versus IDoI (right).      
(b) The 0-th row of  AFDM effective channel matrix.             
‘    ’: Energy from     IDI 
∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ... ∆ ∆ ∆ ...... ∆ ∆ ∆ ... ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ... ∆
Doppler 0 1-1-
l = 0 l = 1 l = ......
0 1-1- -1-0 1
Delay

‘    ’: Energy from     
‘    ’: Energy from     
IDoI 
Fig. 4. Characteristics illustration of AFDM effective channel matrix (‘ ∆’: large non-zero value, ˜0: small non-zero value).
Remark 2: The indices and values of the entries in any large value non-zero band of the
effective channel matrix reflect the delay-Doppler profiles and channel gains of the propagation
paths, respectively, which means every large value non-zero band contains all the CSI.
B. EPA channel estimation in MIMO-AFDM
We arrange the pilot, guard, and data symbols in the DAFT domain at the t-th TA ( t =
1, · · ·, Nt) as
xt[m] =



xpilott , m = (L + 1)t − 1
0, m ∈ [0, (L + 1)Nt + L − 1]
and m ̸= (L + 1)t − 1
xdatat [m], m ∈ [md, N− 1]
(25)
where xpilott is the pilot symbol of t-th TA with index mpilott = ( L + 1)t − 1, xdatat [m] is the
data symbol in the m-th slot of the t-th TA, and the index of the first data symbol is md =
(L + 1)Nt + L. An example of 2 × 1 MISO-AFDM system is presented in Fig. 5. The main idea
of the symbol arrangement in (25) is embedding one pilot in the transmitted AFDM symbol at
each TA to extract a large value non-zero band from Hr,t at the r-th RA. Zero guard symbol
bands with a size of L are placed in the adjacency of all the pilots so that the extracted non-zero
bands at any RA from different TA can be separated approximately.
At the r-th RA ( r = 1 , · · ·, Nr), the indices of received symbols yr[m] that are used for
channel estimation between the r-th RA and the t-th TA are
m ∈ [αmax + kν + (L + 1)(t − 1), αmax + kν + (L + 1)t − 1]. (26)

12
∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ... ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ... ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ...
... ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆
∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆
∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆
0
Large value
Non-zero 
band of 
0 0 0 0 0 0 0 0 0 0 P 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 x x x
x
x
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
∆
...
∆
∆
∆
∆
∆
x
x
x
x
x
x
x
x
x
x
x
l = 0
l =     
...
...
0
L+1
Large value
Non-zero 
band of 
L+1
L
 L
 L
∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ... ∆ ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ... ∆ ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ... ∆
∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ...
... ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆
∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆
∆ ∆ ... ∆ ∆ ∆ ∆ ∆ ∆ ∆ ∆
0
0
0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 P 0 0 0 0 0 0 0 0 0 0 x x x
L
 L
 L
Fig. 5. EPA channel estimation for 2 × 1 MISO-AFDM system (‘P’:pilot, ‘0’:guard, ‘x’:data, ‘ ∆’: large non-zero value, ‘blank’
in Hr,t: small non-zero value).
C. Interference analysis among received pilot symbols
We next show the challenges of acquiring CSI from the received pilot symbols. For ease of
illustration, we assume in this subsection that the exact or estimated delay-Doppler profile of
the P paths is known at the receiver, while their associated channel gains are to be determined.
We categorize all the propagation paths according to their delay shifts in the following. The
subscript (l, j) represents the j-th path with delay l. Then the corresponding channel gain,
Doppler shift, index indicator, and subchannel matrix can be denoted as h[r,t]l,j , νl,j = αl,j + βl,j,
indl,j, and H(l,j), respectively. Denote the number of paths with delay l as Pl ≥ 0, where
Plmax
l=0 Pl = P . Then (18) can be rewritten as
Hr,t =
lmaxX
l=0
PlX
j=1
h[r,t]l,j H(l,j). (27)
Without loss of generality, we attempt to estimate the channel gain of the j′-th path
with delay l′ between the r-th RA and t′-th TA, i.e., h[r,t′]l′,j′ in the following. To this end, we
consider coordinate [m, mpilott′ ] as the central point in the m-th row of H(l′,j′), i.e., m from (26)
is chosen elaborately to satisfy
mpilott′ = (m + indl′,j′)N . (28)
Then from (16) and (17), the received pilot symbol yr[m] can be decomposed into five compo-

13
nents apart from the noise wr[m] as
yr[m] =
NtX
t=1
lmaxX
l=0
PlX
j=1
N −1X
m′=0
h[r,t]l,j H(l,j)[m, m′]xt[m′] + wr[m] = h[r,t′]l′,j′ H(l′,j′)[m, mpilott′ ]xpilott′
| {z }
Desired component
+
Pl′X
j=1, j̸=j′
h[r,t′]l′,j H(l′,j)[m, mpilott′ ]xpilott′
| {z }
IDoI
+
lmaxX
l=0, l̸=l′
PlX
j=1
h[r,t′]l,j H(l,j)[m, mpilott′ ]xpilott′
| {z }
IDI
+
NtX
t=1, t̸=t′
lmaxX
l=0
PlX
j=1
h[r,t]l,j H(l,j)[m, mpilott ]xpilott
| {z }
IPI
+
NtX
t=1
lmaxX
l=0
PlX
j=1
N −1X
m′=md
h[r,t]l,j H(l,j)[m, m′]xdatat [m′]
| {z }
IPDI
+wr[m].
(29)
From (22) and (28) we know that the term with H(l′,j′)[m, mpilott′ ] contains the strongest energy
of h[r,t′]l′,j′ . If we could separate the Desired component from yr[m], h[r,t′]l′,j′ can be recovered given
that mpilott′ and H(l′,j′)[m, mpilott′ ] are known at the receiver ( H(l′,j′)[m, mpilott′ ] can be calculated
with (14)). However, this separation hypothesis is impossible to achieve without being aware
of the channel gains of the other paths. Therefore, the residuals of yr[m] should be seen as
interference to the estimation of h[r,t′]l′,j′ , which can be divided into the following four parts:
1) Inter-Doppler interference (IDoI): components conveyed by the pilot xpilott′ and belong
to the paths with the same delay shift l′ but different Doppler shifts (occur in the thrid case of
Table I). In this case, according to (23), the distance between the central points of H(l′,j′) and
any H(l′,j) with j ̸= j′, i.e.,
δ(l′,j′)(l′,j) ≜ | indl′,j′ − indl′,j |N (30)
is relatively small, which is within [1, 2αmax]. Therefore, the magnitude of H(l′,j)[m, mpilott′ ] is
comparable to H(l′,j′)[m, mpilott′ ] from the desired component. Furthermore, the energy of pilot
symbol is large in practice, making the IDoI term extremely serious. We visualize IDoI on the
right side of Fig. 4(a) with an example that l′ = lmax, j′ = 1 (αlmax,1 = −1), j = 2 (αlmax,2 = 0),
and δ(lmax,1)(lmax,2) = 1. we can observe that when the two paths have the same delay shift, i.e., their
index indicators belong to the same delay block, their subchannel matrice overlap severely.
2) Inter-delay interference (IDI): components conveyed by the pilot xpilott′ and belong to the
paths with delay shifts l ̸= l′ (occur in the first and second cases of Table I). The distance
between the central points of H(l′,j′) and any H(l,j) with l ̸= l′, namely δ(l′,j′)(l,j) , has an lower
bound of 2kν + 1. Therefore, when the spacing factor kν is sufficiently large, the magnitude
of H(l,j)[m, mpilott′ ] is relatively small, which means IDI is much more moderate than IDoI. We

14
visualize IDI on the left side of Fig. 4(a) with an example that l′ = 0 (j′ = 1, α0,1 = αmax),
l = 1 (j = 1, α1,1 = −αmax) and δ(0,1)(1,1) = 2kν + 1. We can notice that the two subchannel matrice
overlap level is much smaller than the IDoI case. Moreover, increasing kν can further lower the
overlap level between the two subchannel matrice and hence suppresses the IDI.
3) Inter-pilot interference (IPI): components contributed by the pilot symbols xpilott from
the other TA, i.e., t ̸= t′. The “blank slot” in AFDM effective channel matrix represents a
small non-zero value, and the non-zero bands of effective channel matrice from all the TA are
extracted simultaneously at the r-th RA in MIMO-AFDM system. Therefore, the pilots symbol
from the other TA will affect yr[m], which can be observed from Fig. 5. Note that IPI becomes
comparable to IDI at the connection of two adjacent large value non-zero bands. Moreover,
increasing kν can enlarge the distances between xpilott (t ̸= t′) and the central points of the m-th
row of all the H(l,j) and thus lower the magnitude of H(l,j)[m, mpilott ], i.e., IPI can be alleviated.
4) Inter-pilot-data interference (IPDI): components contributed by the data symbols. Similar
to IPI, data symbols from all the TA will affect yr[m]. However, since the energy of data symbol
is much smaller than the pilot symbol in practice, IPDI is less significant compared to IPI.
Moreover, it can be mitigated by increasing kν for the same reason.
Remark 3: In the presence of fractional Doppler shifts, four types of interference occur when
estimating the channel gains from the received pilot symbols. Their relative interference degree
is given by
Desired component ≈ IDoI ≫ IDI > IPI > IPDI. (31)
Increasing the kν is equivalent to enlarging the distance between two consecutive delay blocks,
and hence can only suppress the IPI, IPDI, and IDI, not the most serious IDoI.
Note that the above attempt to estimate h[r,t′]l′,j′ is carried out under the premise that we have the
exact or estimated delay-Doppler profile of the P paths, which is another difficulty that needs
to be addressed in advance. The main purpose of this section is to elaborate that estimating the
three channel parameters of each propagation path, i.e., the channel gain, the delay shift, and the
Doppler shift between all pairs of RA and TA in MIMO-AFDM system with the serious IDoI
is extremely intractable. This motivates us to seek for another way to estimate HMIMO.
IV. EPA-DR C HANNEL ESTIMATION FOR MIMO-AFDM
In this section, we study the diagonal reconstructability of AFDM subchannel channel matrix.
Based on that, we propose a low-complexity method named embedded pilot-aided diagonal
reconstruction (EPA-DR) to estimate HMIMO.

15
A. Diagonal reconstructability of AFDM subchannel matrix
We first investigate the diagonal reconstructability of subchannel matrix H(l,j), ∀ l ∈ [0, lmax]
and j ∈ [0, Pl]. Lets define the transform factor between H(l,j)[m, m′] and H(l,j)[(m+1)N , (m′+
1)N ] as
T (l, νl,j, m, m′) = H(l,j)[(m + 1)N , (m′ + 1)N ]H(l,j)[m, m′] . (32)
Substituting (14) into (32), we have
T (l, νl,j, m, m′) = C(l, (m + 1)N , (m′ + 1)N )C(l, m, m′) F (l, νl,j, (m + 1)N , (m′ + 1)N )F (l, νl,j, m, m′) . (33)
Since
F (l, νl,j,(m + 1)N , (m′ + 1)N )
= ej2π((m+1)N +indl,j −(m′+1)N +βl,j) − 1
ej 2πN ((m+1)N +indl,j −(m′+1)N +βl,j) − 1 = ej2π(m+indl,j −m′+βl,j +λ(m,m′)N) − 1ej 2πN (m+indl,j −m′+βl,j +λ(m,m′)N) − 1 (34)
where variable λ(m, m′) = 0 , 1, 2 is introduced due to the N modulus operation in (m + 1)N
and (m′ + 1)N, we have
F (l, νl,j, (m + 1)N , (m′ + 1)N ) = ej2π(m+indl,j −m′+βl,j) − 1
ej 2πN (m+indl,j −m′+βl,j) − 1 = F (l, νl,j, m, m′). (35)
Substituting (35) and (11) into (33), we have
T (l, νl,j, m, m′) = C
 
l, (m + 1)N , (m′ + 1)N 
C(l, m, m′) = ej 2πN
 
(m′−(m′+1)N )l+N c2

((m′+1)N )2+m2−((m+1)N )2−m′2

=



ej 2πN
 
−l+2N c2(m′−m)

, m<N − 1, m′<N − 1
ej 2πN
 
−l+N c2(m2+2m′+1)

, m = N − 1, m′<N − 1
ej 2πN
 
−l−N c2(m′2+2m+1)

, m<N − 1, m′ = N − 1
e−j 2πN l, m = N − 1, m′ = N − 1.
(36)
It is important to notice that T (l, νl,j, m, m′) has no relevance to the Doppler shift νl,j, which
means T (l, νl,j, m, m′) can be represented as T (l, m, m′) instead. This makes a fundamental
contribution to the robustness of the proposed channel estimation scheme to IDoI and will be
illustrated in the next subsection.
Consequently, according to (32), as long asH(l,j)[m, m′] is obtained, H(l,j)[(m+1)N , (m′+1)N ]
can be calculated directly with T (l, m, m′) given in (36) as
H(l,j)[(m + 1)N , (m′ + 1)N ] = T (l, m, m′)H(l,j)[m, m′]. (37)

16
This implies that as long as we acquire an arbitrary column of H(l,j), the whole H(l,j) can
be reconstructed “diagonally”. We refer to this unique characteristic of H(l,j) as diagonal
reconstructability.
B. EPA-DR channel estimation scheme
We next explore the diagonal reconstructability to estimate effective channel matrix Hr,t′ with
the received pilot symbols yr[m] given in (26).
Following the consideration in Section III-C that coordinate [m, mpilott′ ] is the central point in
the m-th row of H(l′,j′), an estimation of Hr,t′[m, mpilott′ ] can be obtained with (29) as
ˆHr,t′[m, mpilott′ ] = yr[m]xpilott′
=
Pl′X
j=1
h[r,t′]l′,j H(l′,j)[m, mpilott′ ]
| {z }
Main component of Hr,t′ [m,mpilott′ ]
+
lmaxX
l=0,l̸=l′
PlX
j=1
h[r,t′]l,j H(l,j)[m, mpilott′ ]
| {z }
Normalized IDI from (29)
| {z }
Hr,t′ [m,mpilott′ ]
+IPI + IPDI + wr[m]
xpilott′ (38)
where the first term is composed of the desired component and the IDoI from (29), while
the second term comes from the IDI. They constitute the real Hr,t′[m, mpilott′ ] and the first
term contributes the most energy of ˆHr,t′[m, mpilott′ ] since (m, mpilott′ ) belongs to the l′-th delay
block. Therefore, the original strong IDoI term when estimating h[r,t′]l′,j′ should no longer be
considered as interference. The actual interference for estimating Hr,t′[m, mpilott′ ] are the third
term in (38).
With ˆHr,t′[m, mpilott′ ] in hand, an estimation of Hr,t′[(m + 1)N , (mpilott′ + 1)N ] can be acquired
by exploring (37) as
ˆHr,t′[(m + 1)N , (mpilott′ + 1)N ] = T (l′, m, mpilott′ ) ˆHr,t′[m, mpilott′ ] (39)
given that
T (l′, m, mpilott′ )
Pl′X
j=1
h[r,t′]l′,j H(l′,j)[m, mpilott′ ]
| {z }
Main component of Hr,t′ [m,mpilott′ ]
=
Pl′X
j=1
h[r,t′]l′,j H(l′,j)[(m + 1)N , (mpilott′ + 1)N ] (40)
is the main component of Hr,t′[(m+1)N , (mpilott′ +1)N ]. This because coordinate [(m+1)N , (mpilott′ +
1)N ] still belongs to the l′-th delay block.

17
Remark 4: The residual errors of ˆHr,t′[(m + 1)N , (mpilott′ + 1)N ] in (39) are the IDI, IPI,
IPDI, and noise wr[m], which are weighted by T (l′, m, mpilott′ ) and inherited from ˆHr,t′[m, mpilott′ ].
According to Remark 3, their energy is much smaller than the main component and hence can
be modeled as additive noise. It is worth emphasizing that there is no IDoI anymore, which
means the IDoI can be avoided naturally.
Consequently, by performing (39) iteratively, i.e.,
ˆHr,t′[(m + i + 1)N , (mpilott′ + i + 1)N ]
= T (l′, (m + i)N , (mpilott′ + i)N ) ˆHr,t′[(m + i)N , (mpilott′ + i)N ], i = 0, · · ·, N− 2 (41)
ˆHr,t′[(m + 1)N , (mpilott′ + 1)N ], · · ·, ˆHr,t′[(m + N − 1)N , (mpilott′ + N − 1)N ] can be obtained
successively, where the main component of Hr,t′[(m + 1)N , (mpilott′ + 1)N ], · · ·, Hr,t′[(m + N −
1)N , (mpilott′ +N −1)N ] are reserved therein. Moreover, since all the transform factors provided in
(36) are complex exponentials with energy one, the inherited errors of ˆHr,t′[(m + 1)N , (mpilott′ +
1)N ], · · ·, ˆHr,t′[(m + N − 1)N , (mpilott′ + N − 1)N ] have the same magnitude, i.e., no error
accumulation occurs during the iterative estimation process.
In addition, to combat the interference of the noise wr[m] in yr[m], we should first conduct
the threshold-based magnitude detection, which is given by
ˆHr,t[m, mpilott ] =



yr[m]
xpilott , |yr[m]| ≥ζ
0, otherwise.
(42)
The influence of the threshold ζ selection on the channel estimation accuracy will be shown in
Section VI-B. By performing the above diagonal estimation on all the received pilot symbols
yr[m] with magnitude exceeds the threshold, the estimation of large value non-zero bands in
all the columns of Hr,t′ can be obtained. We name the above procedures used to estimate the
effective channel matrix Hr,t′ as embedded pilot-aided diagonal reconstruction (EPA-DR) scheme
and summarize it in Algorithm 1.
With the above EPA-DR scheme, we can estimate the effective channel matrices between all
pairs of receive antennas and transmit antennas at the receiver simultaneously. The estimated
ˆHMIMO are then used to detect the received data symbols yr[m], m /∈ [αmax + kν, αmax + kν +
(L + 1)tNt − 1], which is given by
yr[m] =
NtX
t=1
N −1X
m′= ˜md
lmaxX
l=0
Pl′X
j=1
h[r,t]l,j H(l,j)[m, m′]xdatat [m′]+
NtX
t=1
lmaxX
l=0
PlX
j=1
h[r,t]l,j H(l,j)[m, mpilott ]xpilott
| {z }
IPDI
+wr[m].
(43)

18
Algorithm 1: EPA-DR scheme for HMIMO estimation
-Transmitter:
Input: lmax, αmax, c1, c2, Nt, and mpilott , t = 1, · · ·, Nt.
for t = 1, 2, · · ·, Nt do
Arrange the pilot, guard, and data symbols at the t-th transmit antenna with (25).
end
-Receiver:
Input: lmax, αmax, c1, c2, Nt, Nr, ζ, and mpilott , t = 1, · · ·, Nt.
1 for r = 1, 2, · · ·, Nr do
2 for t = 1, 2, · · ·, Nt do
3 Step 1: Obtain the large value non-zero band in the mpilott -th column of Hr,t
from yr according to (26);
4 Step 2: Perform threshold-based magnitude detection using (42);
5 Step 3: Reconstruct ˆHr,t iteratively using (41).
6 end
7 end
Output: Assemble ˆHr,t into ˆHMIMO using (19).
We can observe from (43) that, due to the fractional Doppler, the received data symbols are
interfered by all the pilots, which can also be alleviated by enlarging the spacing factor kν.
C. Performance assessment of EPA-DR algorithm
1) Overhead analysis : The pilot and guard overhead for each transmit antenna in an Nt × Nr
MIMO-AFDM system is given by
OMIMO-AFDM = (Nt + 1)L + Nt = (Nt + 1)(lmax + 1)
 
2(αmax + kν) + 1

− 1. (44)
While the Nt × Nr MIMO-OTFS counterpart is [7]
OMIMO-OTFS =
 
(Nt + 1)lmax + Nt
 
4(αmax + kν) + 1

(45)
which is nearly twice of OMIMO-AFDM. This implies that AFDM maintains its advantage over
OTFS on less channel estimation overhead in MIMO system.
2) Computational complexity analysis : The total computation complexity of the EPA-DR
scheme is dominated by Step 3 at the receiver, which requires at most only (L + 1)(N −

19
1) complex multiplications (assume all the magnitude of received pilot symbols exceed the
threshold).
It is worth emphasizing that once the AFDM parameters c1 and c2 are determined, all the
transform factors needed in Step 3 can be calculated with (36) only once in advance at the
receiver despite the ever-changing channels ( li can be obtained from the bijective relationship
between the coordinate ( m, m′) and the li-th delay block). To be specific, when m < N− 1 and
m′ < N− 1, T (li, m, m′) is determined by m − m′, i.e., only four transform factors are required
to be calculated for each received pilot symbol (for m = m′, it is one). Therefore, the total
number of transform factors needed to be calculated in practice is 4L + 1, whose computation
complexity is ignorable.
3) Comparison between EPA-DR and EPA-AML [15] schemes : In EPA-AML scheme, the
delay and Doppler shifts of the P paths are first estimated with brute force search, and then the
associate channel gains are estimated. Finally, the AFDM effective channel matrix is calculated
with the three estimated parameters of each path according to (18). Therefore, the number of
paths should be known in advance, and high computation complexity is unavoidable in the brute
force search and effective channel matrix calculation. More importantly, it suffers from serious
IDoI as we unveiled in Section III-C.
In contrast, the proposed EPA-DR scheme does not need to know the number of paths in
advance since a threshold-based magnitude detection procedure is adopted. Moreover, the AFDM
effective channel matrix is obtained directly without estimating the three channel sparameters
and hence lowers the computation complexity significantly. Furthermore, the serious IDoI can
be avoided inherently by exploring the diagonal reconstructability of AFDM subchannel matrix.
These outstanding advantages of EPA-DR over EPA-AML ensure its feasibility, especially in
multiple-antenna-based AFDM systems.
V. O RTHOGONAL RESOURCE ALLOCATION AND CHANNEL ESTIMATION FOR AFDMA
Inspired by the symbol arrangement in EPA-DR channel estimation scheme, we propose a
practical and efficient resource allocation scheme for AFDMA system. For ease of illustration,
we consider NU users with single antenna, while the base station (BS) has NBS antennas.
Different from the point-to-point MIMO-AFDM system discussed above, the delay-Doppler
profiles between the BS and different users are independent of each other. Let α[BS,u]max and l[BS,u]max
denote the maximum Doppler and maximum delay between the BS and theu-th user, respectively,

20
˜αmax = max{α[BS,u]max |u ∈ [1, Nu]}. Then the AFDM parameter c1 should be set as 2( ˜αmax+kν )+12N .
Define Lu ≜ (l[BS,u]max + 1) 2( ˜αmax + kν) + 1 − 1, where Lu satisfy
L1 ≤ L2 ≤ · · · ≤LNu ≤ Lmax (46)
i.e., the users are sorted in order of value Lu. The parameter Lmax is an arbitrary integer that
satisfies equation (46). Suppose that the BS is aware of Lmax and all the Lu, while each user
only knows Lmax and its own Lu.
A. Downlink
In downlink communication, the symbol arrangement at the b-th transmit antenna ( b =
1, · · ·, NBS) in the BS is
xb[m] =



xpilotb , m = (Lmax + 1)b − 1
xdatab,u [m], m ∈ Du, u= 1, · · ·, Nu
0, otherwise
(47)
where xpilotb is the pilot, Du is the resource block allocated to the u-th user for data transmission
(each user is assumed to know their own Du), xdatab,u [m] are the corresponding data symbols. Guard
symbol blocks (GSB) are inserted among the resource blocks to avoid inter-user interference
(IUI). Each pilot should be surrounded by two GSBs with a size no less than LNu, while the
u-th resource block Du should be protected by two GSBs with a size no less than Lu. When
these conditions are satisfied, all the users can separate their own received data symbols from
the others, making the data detection for each user simpler. An example of AFDMA downlink
system with three single-antenna users and a three-antenna BS is presented in Fig. 6 1.
The pilot and guard overhead for one TA of BS in downlink communication is given by
Odownlink = (NBS + 1)Lmax + NBS +
NuX
u=2
Lu. (48)
The size of Du (u = 1, · · ·, Nu) can be tuned flexibly according to the throughput demands of
different users, as long as their summation satisfies
NuX
u=1
|Du| = N − Odownlink. (49)
Based on the symbol arrangement in (47), each user exploits the associated received symbols
for EPA-DR channel estimation and data detection.
1Although the data symbols for user 1 and user 2 will coincide with each other at user 3, it is acceptable since the target data
symbols of user 3 are not contaminated. Moreover, if we shift the orders of D2 and D3 in Fig. 6, then the GSB with the size
of L2 need to be enlarged to L3, i.e., fewer data symbols can be transmitted.

21
0 0 0 P 0 0 0 0 0 0 0 0 0 0 0 d d d 0 0 0 ◊ ◊ ◊ 0 0 0 □ □ □
0
(d) Downlink, base station, (‘P’: pilot; ‘d’ ,‘◊’ and ‘□’ : data for user 1, 2 and 3; ‘0’: guard)
0 0 0 0 0 0 0 P 0 0 0 0 0 0 0 d d d 0 0 0 ◊ ◊ ◊ 0 0 0 □ □ □
0
0 0 0 0 0 0 0 0 0 0 0 P 0 0 0 d d d 0 0 0 ◊ ◊ ◊ 0 0 0 □ □ □
0
(a) Base station 1st TA
(b) Base station 2nd TA
(c) Base station 3rd TA
L1 L2 L3 Lmax
Lmax Lmax Lmax Lmax
Lmax Lmax Lmax Lmax
Lmax Lmax Lmax Lmax
L2 L3
L2 L3
L2 L3
N-1
N-1
N-1
Fig. 6. AFDMA downlink system with three single-antenna
users and a three-antenna BS (‘P’: pilot, ‘0’: guard, ‘d’: data
symbol for the user 1, ‘ ⋄’: data symbol for the user 2, ‘ □’: data
symbol for the user 3).
0 0 0 P 0 0 0 d d d 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
0
(a) User 1 TA
0 0 0 0 0 0 0 0 0 0 0 0 0 P 0 0 0 ◊ ◊ ◊ 0 0 0 0 0 0 0 0 0 0
0
(b) User 2 TA
0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 P 0 0 0 □ □ □
0
(c) User 3 TA
L1 L2 L3 Lmax
L1 L1
L2 L2
L3 L3
N-1
N-1
N-1
Fig. 7. AFDMA uplink system with three single-antenna
users and a three-antenna BS (‘P’: pilot, ‘0’: guard, ‘d’:
data symbol of the user 1, ‘ ⋄’: data symbol of the user 2,
‘□’: data symbol of the user 3).
B. Uplink
We first divide the entire AFDM frame into Nu orthogonal resource blocks as B1, B2, · · ·, BNu
according to the throughput demands of different users (suppose that the BS is aware of the
resource blocks allocation thoroughly, while each user only knows its own resource block Bu),
where PNuu=1 |BNu| = N. Then each user arranges its pilot and data block Du in its own resource
block. Similar to the downlink case, GSBs should be placed appropriately to avoid IUI. An
example of AFDMA uplink system with three single-antenna users and a three-antenna BS is
presented in Fig. 7. The pilot and guard overhead of the u-th user in uplink communication is
Ouuplink = 2Lu.
With the above symbol arrangement, the received symbols corresponding to different users can
be separated in the BS perfectly. The BS explores the associated received symbols to perform
EPA-DR channel estimation and data detection for each user. Note that in uplink communication,
sorting the users in the order of their Lu values is not necessary.
A simpler solution is to replace all the Lus with Lmax roughly in both downlink and uplink
communications, and the users ordering in (46) is no longer necessary. However, this simplifi-
cation will incur spectral efficiency degradation.
The main idea of the above downlink and uplink symbol arrangements is reducing the guard
symbols used to ensure orthogonal resource allocation and channel estimation to the greatest
extent. It is done by flexibly exploring the differences in the delay-Doppler profiles between the
BS and all the users, i.e., the sizes of the non-zero bands of different effective channel matrices.
Compared to the orthogonal resource allocation based OTFS-MA system proposed in [11], which
suffers from excessive guard symbol overhead due to the 2D structure of OTFS, the AFDMA

22
system designed above is efficient and easy to implement. Meanwhile, it preserves a large
degree of freedom for the BS and users to accommodate various communication requirements.
Therefore, we can conclude that AFDMA is a promising solution for multiple access in doubly
selective channels.
VI. S IMULATION RESULTS
In this section, following the vectorized input-output relationship in equation (20), we present
the performance of MIMO-AFDM in terms of BER with ideal and our estimated CSI. Both
integer and fractional Doppler cases are considered. Each transmit antenna transmits independent
information symbols, and the channel gains of all paths follow the distribution of CN (0, 1/P ).
In the case of large frame size, many low-complexity detectors proposed for AFDM and OTFS
can be applied to MIMO-AFDM directly [19], [24]–[26]. We adopt the widely-used message
passing (MP) detector proposed in [24] with a complexity order of O(niterN NrS|A|), where niter
is the maximum number of iteration, S ≤ L + 1 is the number of received pilot symbols whose
energy exceed the preset threshold, |A| represents the modulation order.
A. Perfect CSI
0 5 10 15 20 25 30
SNR in dB
10-7
10-6
10-5
10-4
10-3
10-2
10-1
100
BER
SISO-AFDM, P = 2
SISO-AFDM, P = 3
MIMO-AFDM, P = 2
MIMO-AFDM, P = 3
(SNR)-2
(SNR)-3
(SNR)-4
(SNR)-6
Fig. 8. BER performance of SISO-AFDM and 2 × 2 MIMO-
AFDM systems with integer Doppler. The normalized delay-
Doppler profiles (li, νi) of two paths: (0, 0) and (1, 1); three
paths: (0, 0), (0, 1) and (1, 1).
0 5 10 15 20 25 30
SNR in dB
10-8
10-7
10-6
10-5
10-4
10-3
10-2
10-1
100
BER
SISO-AFDM, P = 2
SISO-AFDM, P = 3
1  2 SIMO-AFDM, P = 2
1  2 SIMO-AFDM, P = 3
(SNR)-2
(SNR)-3
(SNR)-4
(SNR)-6
Fig. 9. BER performance of SISO-AFDM and 1 × 2
SIMO-AFDM systems with fractional Doppler. The nor-
malized delay-Doppler profiles (li, νi) of two paths: (0,
0) and (1, 0.5); three paths: (0, 0), (0, 0.5) and (1, 0.8).
We first apply maximum likelihood (ML) detector to verify the diversity order of MIMO-
AFDM with small frame sizes. Fig. 8 shows the BER performance of SISO-AFDM and 2 × 2
MIMO-AFDM systems with integer Doppler ( βi = 0 and kν = 0). Without losing of generality,
we consider NAFDM = 6 , P = 2 , and 3. Asymptotic lines with slopes of 2 ((SNR)−2), 3

23
((SNR)−3), 4 ((SNR)−4), and 6 ((SNR)−6) are plotted. We can observe that the MIMO-AFDM
system outperforms SISO-AFDM system thanks to the space diversity gain from multiple RAs.
Meanwhile, the multiple TAs of MIMO-AFDM system bring in the advantages of linear incre-
ment in spectral efficiency with the number of TAs. Furthermore, the diversity orders achieved
by SISO-AFDM in channels with two and three paths are 2 and 3 respectively, while the 2 × 2
MIMO-AFDM counterparts are 4 and 6 respectively, verifying the validity of Theorem 1. Fig.
9 shows that Theorem 1 also holds for the fractional Doppler case.
0 2 4 6 8 10 12 14
SNR in dB
10-6
10-5
10-4
10-3
10-2
10-1
100
BER
SISO-AFDM
SISO-OTFS
2 2 MIMO-OFDM
2 2 MIMO-AFDM
2 2 MIMO-OTFS
3 3 MIMO-AFDM
3 3 MIMO-OTFS
Fig. 10. BER comparisons among SISO-AFDM, SISO-OTFS,
MIMO-OFDM, MIMO-AFDM and MIMO-OTFS systems with
integer Doppler and N = 1024. The normalized delay-Doppler
profiles of five paths: (0, 0), (1, 1), (2, 2), (3, 3), (4, 4).
0 2 4 6 8 10 12 14
SNR in dB
0
0.25
0.5
0.75
1
1.25
1.5
1.75
2
2.25
2.5
Spectral Efficiency (bit/s/Hz)
2 2 MIMO-AFDM
2 2 MIMO-OTFS
3 3 MIMO-AFDM
3 3 MIMO-OTFS
Fig. 11. Spectral efficiency comparison between the 2×2
MIMO-AFDM and the 2×2 MIMO-OTFS systems in Fig.
10.
Fig. 10 shows the BER performance comparisons among SISO-AFDM, SISO-OTFS, MIMO-
OFDM, MIMO-AFDM, and MIMO-OTFS systems with integer Doppler. Recalling that an
OTFS frame with duration NOTFSTOTFS (seconds) and bandwidth MOTFS∆fOTFS (Hz) transmits
NOTFSMOTFS symbols, where TOTFS and ∆fOTFS represent the time and frequency domain sample
intervals, respectively, and satisfy TOTFS∆fOTFS = 1 ; NOTFS and MOTFS denote the number
of samples in the time-frequency plane (or Doppler-delay plane). We adopt fc = 4 GHz,
∆fAFDM = 500 Hz, NAFDM = 1024, ∆fOTFS = ∆fOFDM = 16 kHz, NOTFS = MOTFS = 32 to ensure
the same resources are occupied, i.e., bandwidth BAFDM = NAFDM∆fAFDM = MOTFS∆fOTFS =
BOTFS = 512 kHz. P = 5 paths with BPSK and MP detection are applied. We can observe that
the 2×2 MIMO-AFDM system outperforms the 2×2 MIMO-OFDM system significantly. This is
because MIMO-OFDM suffers from severe inter-carrier interference caused by the heavy Doppler
shifts. Moreover, owing to the equivalent delay-Doppler channel representation in the DAFT
domain, AFDM establishes nearly the same BER performance as OTFS in SISO and MIMO

24
configurations with large frame sizes 2. However, considering the lower overhead of MIMO-
AFDM system when conducting the pilot-aided channel estimation, MIMO-AFDM will enjoy
higher spectral efficiency than MIMO-OTFS. For example, according to (44) and (45), the pilot
and guard overhead of 2 × 2 MIMO-AFDM for channel estimation is 134 slots, corresponding
to 13.08% of the entire AFDM frame, while the 2 × 2 MIMO-OTFS counterpart is 238 slots,
corresponding to 23.24% of the entire OTFS frame. This difference translates into a huge spectral
efficiency gap between MIMO-AFDM and MIMO-OTFS, as shown in Fig. 11, where the values
of spectral efficiency were calculated from the BER values in Fig. 10.
B. Imperfect CSI
We next apply the EPA-DR scheme for channel estimation. P = 4 paths with normalized
delay profile of [0, 0, 1, 2] are adopted to cover all the cases in Table I. The Doppler shift of
each path is generated by using Jakes’ formula, i.e., νi = νmax cos (θi), where θi is uniformly
distributed over [−π, π], νmax = 2 corresponds to a maximum Doppler shift of 2000 Hz and
a maximum UE speed of 540 kmph. The pilot signal for SNR is denoted as SNRp, while the
received data signal for SNR is denoted as SNRd. Other parameters considered for the simulation
are provided in Table II.
TABLE II
SIMULATION PARAMETERS FOR IMPERFECT CSI
Parameter Value
Carrier frequency fc (GHz) 4
Subcarrier spacing ∆fAFDM (kHz) 1
Number of subcarrier (frame size) NAFDM 1024
Bandwidth BAFDM (kHz) 1024
Maximum UE speed (kmph) 540
Maximum Doppler shift (kHz) 2
Number of paths ( P ) 4
Modulation scheme BPSK, 4-QAM,and 16-QAM
MIMO configuration 2 × 2
Detector MP
Fig. 12 shows the BER versus SNRd of MIMO-AFDM with different SNRp. Integer Doppler
is considered. In this case, there is no IDoI, IDI, and IPI among the received pilot symbols
and thus the EPA-AML scheme [15] is feasible. We can observe that the BER performance
2It is worth mentioning that, although the diversity order of uncoded OTFS is proven to be one, it enjoys nearly full diversity
in the finite SNR region when the frame size NOTFSMOTFS is sufficiently large [6]. Therefore, the above observations that AFDM
systems show almost the same BER performance as OTFS systems do not conflict with the conclusion that MIMO-AFDM can
achieve full diversity.

25
0 2 4 6 8 10 12 14 16 18
SNRd in dB
10-5
10-4
10-3
10-2
10-1
100
BER
Perfect CSI
EPA-DR, SNRp = 20 dB
EPA-DR, SNRp = 25 dB
EPA-DR, SNRp = 30 dB
EPA-AML [15], SNRp = 20 dB
EPA-AML [15], SNRp = 25 dB
EPA-AML [15], SNRp = 30 dB
BPSK
4-QAM
16-QAM
Fig. 12. BER versus SNRd of 2 × 2 MIMO-AFDM system
with different SNRp, integer Doppler.
0 2 4 6 8 10 12 14
SNRd in dB
10-5
10-4
10-3
10-2
10-1
100
BER
BPSK
4-QAM
Fig. 13. BER versus SNRd of 2 × 2 MIMO-AFDM system with
different spacing factors kν, SNRp = 45 dB, fractional Doppler.
enhances as SNRp increases. This is because the only error is the AWGN, which is normalized
by xpilott in Step 2 of EPA-DR. Therefore, the larger energy of the pilot, the more accurate the
estimated ˆHr,t. Moreover, when SNRp reaches 30 dB, the BER of MIMO-AFDM system using
the estimated CSI shows only marginal degradation compared to that with Perfect CSI, which
validates the effectiveness of the EPA-DR scheme. In addition, we can notice that, with much
lower computation complexity, EPA-DR delivers nearly the same channel estimation performance
as EPA-AML.
We next investigate the effect of spacing factor kν on the BER performance of MIMO-AFDM
system with fractional Doppler. In this case, the EPA-AML suffers from serious IDoI and hence
is impracticable. Therefore, we simulate three kν values ( kν = 1, 4, and 8) with the proposed
EPA-DR scheme. We can observe from Fig. 13 that, as kν increases, the BER performance
improves. This is because the protection bands between two contiguous delay blocks in the
effective channel matrix are widened, as shown in Fig. 4, making the IDI, IPI, and IPDI smaller.
However, according to (44), as kν increases, the pilot and guard overhead OMIMO-AFDM will
increase correspondingly (the OMIMO-AFDM of the three used kν values are 62, 116, and 188,
respectively, corresponding to 6.05%, 11.33%, and 18.40% of the entire AFDM frame), leading
to fewer data symbols can be transmitted in each transmit antenna. We can also notice that
compared to the integer Doppler case in Fig. 12, a higher SNRp is required for the fractional
Doppler case.
Fig. 14 shows the BER versus different thresholds of MIMO-AFDM system with fractional
Doppler. We set the thresholds by taking N0 (the variance of noise) as a reference. Three different
SNRp values are adopted. Setting ζ = 0 represents that we do not conduct the threshold-based

26
0 3N0 6N0 9N0 12N0
Threshold 
10-4
10-3
10-2
10-1
BER
SNRp = 25 dB
SNRp = 30 dB
SNRp = 35 dB
Fig. 14. BER versus different thresholds of 2×2 MIMO-AFDM
system, fractional Doppler, kν = 8.
30 35 40 45 50 55
SNRp in dB
10-5
10-4
10-3
10-2
BER
Fig. 15. BER versus SNRp of 2 × 2 MIMO-AFDM
system with different spacing factors kν, SNRd = 14 dB,
fractional Doppler.
magnitude detection in Step 2 of EPA-DR. We can observe that there exists an optimal threshold,
which is around 6N0. According to (42), if ζ is set higher than the optimal threshold, the CSI
in the received pilot symbols with small energy will be omitted inappropriately; if ζ is set lower
than the optimal threshold, the interference of noise with large energy will be reserved. Both of
the cases will deteriorate the accuracy of EPA-DR channel estimation, followed by the detection
performance degradation. Moreover, we find that with SNRp increasing, the BER performance
is less sensitive to the threshold variation. This is because with the increase of pilot symbols’
energy, the IDI, IPI will dominate the overall interference in EPA-DR gradually, as analyzed in
(29) and Remark 4.
Fig. 15 shows the BER versus SNRp of MIMO-AFDM in the case of fractional Doppler.
We can observe that, as the SNRp increases, the BER performance first enhances and then
degrades. This is because when SNRp is smaller than 40 dB, the noise plays the major role of
interference in channel estimation and can be suppressed by enlarging the energy of the pilot.
However, according to (43), the IPDI in the received data symbols will be magnified at the
same time, making signal detection more difficult even if a more accurate channel estimate is
obtained. Therefore, there is a tradeoff between the pilot-aided channel estimation accuracy and
the pilot-data symbols separability at the receiver in AFDM with fractional Doppler, which can
be interpreted as the cost of compressing the two-dimensional delay-Doppler domain into the
one-dimensional DAFT domain.
VII. C ONCLUSION
In this paper, we investigate the channel estimation in MIMO-AFDM with specific attention
to fractional Doppler shifts. With ideal CSI, MIMO-AFDM is shown to achieve full diversity

27
and establishes a BER performance similar to MIMO-OTFS and superior to MIMO-OFDM
significantly, while showing a great advantage in spectral efficiency over MIMO-OTFS. Next,
by exploring the unique diagonal reconstructability of the AFDM subchannel matrix, we propose
a low-complexity channel estimation scheme for MIMO-AFDM to eliminate the serious IDoI
induced by fractional Doppler shifts. Finally, we propose an orthogonal resource allocation
scheme for AFDMA system. Simulation results show that the BER performance of MIMO-
AFDM applying EPA-DR channel estimation is very close to the case with ideal CSI. In the
future, space-time coding can be investigated to acquire transmit diversity in MIMO-AFDM
system with the proposed EPA-DR channel estimation method [28].
APPENDIX
PROOF OF THEOREM 1
For ease of derivations, we assume the Doppler shifts as integers. Simulation results given in
Section VI-A show that the derived diversity order also holds for the fractional Doppler case.
Considering there are P propagation paths between all pairs of RAs and TAs, and the fractional
parts of all the associated Doppler shifts are zero ( βi = 0 and kν = 0), then the spreading factor
F (li, νi, m, m′) in (12) satisfies
F (li, νi, m, m′) = ej2π(m+indi −m′) − 1ej 2πN (m+indi −m′) − 1 =  N, m ′ = (m + indi)N0, otherwise. (50)
Hence, the input-output relationship of SISO-AFDM in (9) can be simplified as
y[m] =
PX
i=1
hiC(li, m, m′)x[m′] + w[m] (51)
where m ∈ [0, N− 1], m′ = ( m + indi)N. Therefore, there are P non-zero elements in each
row and column of Hr,t, ∀ r ∈ [1, Nr], t∈ [1, Nt]. Equation (13) can then be presented in an
alternate way as [15]
y =
PX
i=1
hiHix + w = Φ(x)h + w (52)
where Φ(x) = [H1x, H2x, . . . ,HP x ] ∈ CN ×P , channel gain vector h = [h1, h2, . . . , hP ]T ∈
CP ×1.
Similarly, the input-output relationship of MIMO-AFDM in (16) can be simplified as
yr[m] =
NtX
t=1
PX
i=1
h[r,t]i C(li, m, m′)xt[m′] + wr[m] (53)

28
where m′ = (m + indi)N. From (53) we can see that each row of HMIMO has only P Nt non-zero
elements. Therefore, the vectorized input-output relationship in (20) can also be presented as
Y = ˜Φ(X)˜h + W (54)
where received symbol matrix Y = [y1, y2, . . . ,yNr] is an N × Nr matrix whose r-th column
is the received symbol vector of the r-th RA, transmitted symbol matrix X = [x1, x2, . . . ,xNt]
is an N × Nt matrix whose t-th column is the transmitted symbol vector of the t-th TA, ˜Φ(X)
is an N × P Nt concatenated matrix with a definition of
˜Φ(X) = [ Φ(x1), Φ(x2), . . . ,Φ(xNt) ] (55)
˜h ∈ CP Nt×Nr is channel gain matrix with a definition of
˜h =

 h1,1 . . . hNr,1... ... ...
h1,Nt . . .hNr,Nt

 (56)
where hr,t ∈ CP ×1 denotes the channel gain vector between the r-th RA and t-th TA, and its
elements hr,ti are assumed to follow the distribution of CN (0, 1/P ) (uniform scattering profile),
W ∈ CN ×Nr is the noise matrix.
For convenience, we normalize the transmit symbol matrix X so that the signal-to-noise
ratio (SNR) at each receive antenna is 1No . Let Xi and Xj be two transmit symbol matrices.
Assuming perfect CSI and maximum likelihood (ML) detection at the receiver, the probability
of transmitting the symbol matrix Xi and deciding in favor of Xj at the receiver is the pairwise
error probability (PEP) between Xi and Xj, which can be expressed as [27]
P

Xi → Xj | ˜h, Xi

= Q


vuut 


 ˜Φ(Xi) − ˜Φ(Xj) ˜h


2
2N0

 . (57)
The PEP averaged over the channel statistics can be denoted as
P (Xi → Xj) = E

Q


vuut 


 ˜Φ(Xi) − ˜Φ(Xj) ˜h


2
2N0



 . (58)
Define difference matrix as δ(i,j) ≜ Xi −Xj, where the t-th column of δ(i,j) is δ(i,j)t = x(i)t −x(j)t ,
which denotes the difference of two transmitted symbols at the t-th TA. Since ˜Φ is a linear
operator, we have
P (Xi → Xj) = E

Q


vuut 


 ˜Φ(δ(i,j))˜h


2
2N0



 . (59)

29
Using Chernoff bound and the fact that each TA transmits independent AFDM symbols, an upper
bound on the PEP in (59) can be obtained as [27]
P (Xi → Xj) ≤


kY
l=1
1
1 +
λ2t,l
4P N0


Nr
(60)
where λt,l is the l-th singular value of the matrix Φ(δ(i,j)t ) (t ∈ 1, 2, . . . , Nt ) and k is the rank
of Φ(δ(i,j)t ). At high SNR regime, (60) can be further simplified as
P (Xi → Xj) ≤ 1N kNro
 kY
l=1
λ2t,l
4P
!−Nr
. (61)
We can observe from (61) that the exponent of the SNR term 1No is kNr, and the overall bit
error ratio (BER) is dominated by the PEP with the minimum value of k, for all i, j, i̸= j.
Therefore, the diversity order of MIMO-AFDM, denoted by ρ, is given by
ρ = Nr · mini,j,i̸=j rank

Φ(δ(i,j)t ) . (62)
In [15] (Appendix A), the term mini,j,i̸=j rank

Φ(δ(i,j)t ) is proven to be P whenever the
AFDM parameters c1 and c2 are tuned as described in Remark 1, and the number of subcarriers
N satisfies
N ≥ (lmax + 1) (2αmax + 1) . (63)
In practice, N ≫ (lmax + 1) (2αmax + 1), thus the diversity order of MIMO-AFDM is P Nr, i.e.,
MIMO-AFDM achieves full diversity in doubly selective channels. This completes the proof of
Theorem 1.
REFERENCES
[1] T. Wang, J. G. Proakis, E. Masry, and J. R. Zeidler, “Performance degradation of OFDM systems due to doppler spreading,”
IEEE Transactions on Wireless Communications , vol. 5, no. 6, pp. 1422-1432, 2006.
[2] T. Hwang et al., “OFDM and its wireless applications: a survey,” IEEE Transactions on Vehicular Technology, vol. 58, no.
4, pp. 1673-1694, May 2009.
[3] R. Hadani et al., “Orthogonal time frequency space modulation,” IEEE Wireless Communications and Networking
Conference (WCNC), pp. 1-6, 2017.
[4] S. K. Mohammed, “Derivation of OTFS modulation from first principles,” IEEE Transactions on Vehicular Technology ,
vol. 70, no. 8, pp. 7619-7636, Aug. 2021.
[5] M. K. Ramachandran and A. Chockalingam, “MIMO-OTFS in high-doppler fading channels: signal detection and channel
estimation,” IEEE Global Communications Conference (GLOBECOM) , pp. 206-212, 2018.
[6] G. D. Surabhi, R. M. Augustine, and A. Chockalingam, “On the diversity of uncoded OTFS modulation in doubly-dispersive
channels,” IEEE Transactions on Wireless Communications , vol. 18, no. 6, pp. 3049-3063, Jun. 2019.
[7] P. Raviteja, K. T. Phan, and Y . Hong, “Embedded pilot-aided channel estimation for OTFS in delay-doppler channels,”
IEEE Transactions on Vehicular Technology, vol. 68, no. 5, pp. 4906-4917, 2019.

30
[8] W. Shen, L. Dai, J. An, P. Fan and R. W. Heath, “Channel estimation for orthogonal time frequency space (OTFS) massive
MIMO,” IEEE Transactions on Signal Processing , vol. 67, no. 16, pp. 4204-4217, Aug. 2019.
[9] Z. Ni, J. A. Zhang, X. Huang, K. Yang and J. Yuan, “Uplink sensing in perceptive mobile networks with asynchronous
transceivers,” IEEE Transactions on Signal Processing , vol. 69, pp. 1287-1300, 2021.
[10] Y . Hong, T. Thaj, and E. Viterbo, Delay Doppler Communications: Principles and Applications . Elsevier, 2022.
[11] S. Rakib and R. Hadani, “Multiple access in wireless telecommunications system for high-mobility applications,” US Patent
No.US9722741B1, Aug. 2017.
[12] V . Khammammetti and S. K. Mohammed, “OTFS-based multiple-access in high doppler and delay spread wireless
channels,” IEEE Wireless Communications Letters , vol. 8, no. 2, pp. 528-531, April 2019.
[13] G. Surabhi, R. M. Augustine, and A. Chockalingam, “Multiple access in the delay doppler domain using OTFS modulation,”
arXiv preprint arXiv:1902.03415 , 2019.
[14] A. Thomas, K. Deka, P. Raviteja and S. Sharma, ”Convolutional sparse coding based channel estimation for OTFS-SCMA
in uplink,” IEEE Transactions on Communications , vol. 70, no. 8, pp. 5241-5257, Aug. 2022.
[15] A. Bemani, N. Ksairi and M. Kountouris, “Affine frequency division multiplexing for next generation wireless communi-
cations,” IEEE Transactions on Wireless Communications , early access, 2023.
[16] A. Bemani, N. Ksairi and M. Kountouris, “AFDM: a full diversity next generation waveform for high mobility
communications,” IEEE International Conference on Communications Workshops (ICC Workshops) , pp. 1-6, 2021.
[17] S. Chang Pei and J. Jiun Ding, “Closed-form discrete fractional and affine fourier transforms,” IEEE Transactions on
Signal Processing, vol. 48, no. 5, pp. 1338-1353, May 2000.
[18] T. Erseghe, N. Laurenti, and V . Cellini, “A multicarrier architecture based upon the affine fourier transform,” IEEE
Transactions on Communications , vol. 53, no. 5, pp. 853-862, May 2005.
[19] A. Bemani, N. Ksairi and M. Kountouris, “Low complexity equalization for AFDM In doubly dispersive channels,” IEEE
International Conference on Acoustics, Speech and Signal Processing (ICASSP) , pp. 5273-5277, 2022.
[20] A. Bemani, G. Cuozzo, N. Ksairi and M. Kountouris, “Affine frequency division multiplexing for next-generation wireless
networks,” International Symposium on Wireless Communication Systems (ISWCS) , pp. 1-6, 2021.
[21] Q. Wang, A. Kakkavas, X. Gong and R. A. Stirling-Gallacher, “Towards integrated sensing and communications for 6G,”
2nd IEEE International Symposium on Joint Communications & Sensing (JC&S) , pp. 1-6, 2022.
[22] Y . Ni, Z. Wang, P. Yuan and Q. Huang, “An AFDM-based integrated sensing and communications,”International Symposium
on Wireless Communication Systems (ISWCS) , pp. 1-6, 2022.
[23] H. Yin and Y . Tang, “Pilot aided channel estimation for AFDM in doubly dispersive channels,” IEEE/CIC International
Conference on Communications in China (ICCC) , pp. 308-313, 2022.
[24] P. Raviteja, K. T. Phan, Y . Hong, and E. Viterbo, “Interference cancellation and iterative detection for orthogonal time
frequency space modulation,” IEEE Transactions on Wireless Communications, vol. 17, no. 10, pp. 6501-6515, Oct. 2018.
[25] W. Yuan, Z. Wei, J. Yuan and D. W. K. Ng, “A simple variational bayes detector for orthogonal time frequency space
(OTFS) modulation,” IEEE Transactions on Vehicular Technology, vol. 69, no. 7, pp. 7976-7980, July 2020.
[26] T. Thaj and E. Viterbo, “Low complexity iterative rake decision feedback equalizer for zero-padded OTFS systems,” IEEE
Transactions on Vehicular Technology, vol. 69, no. 12, pp. 15 606-15 622, Dec. 2020.
[27] D. Tse and P. Viswanath, Fundamentals of Wireless Communication. Cambridge, U.K.: Cambridge University Press, 2005.
[28] H. Yin et al., “Cyclic delay-doppler shift: a simple transmit diversity technique for delay-doppler waveforms in doubly
selective channels,” IEEE International Conference on Acoustics, Speech and Signal Processing Workshops (ICASSP
Workshops), pp. 1-5, 2023.