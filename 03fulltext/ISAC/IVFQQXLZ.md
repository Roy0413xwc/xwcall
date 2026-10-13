---
title: "An AFDM-Based Integrated Sensing and Communications"
zotero_key: "IVFQQXLZ"
pdf_key: "Z2RV53DR"
doi: "10.1109/ISWCS56560.2022.9940346"
collection: "ISAC"
source: "Zotero imported PDF (pypdf extraction)"
page_mapping: "unknown"
source_sha256: "1fba312a708de3cb8c4f950888a0155dc6f5682f130ab31e263c33bba6299a9d"
pdf_pages: 6
---

# An AFDM-Based Integrated Sensing and Communications — Fulltext

> 由 Zotero 附件 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证。

---


<!-- extraction_page_index: 1 -->

An AFDM-Based Integrated Sensing and
Communications
Yuanhan Ni, Zulin Wang, Peng Yuan and Qin Huang
School of Electronic and Information Engineering, Beihang University, Beijing, 100191, China
Email:{yuanhanni, wzulin, yuanpeng9208}@buaa.edu.cn, qhuang.smash@gmail.com (corresponding author)
Abstract—This paper considers an afﬁne frequency division
multiplexing (AFDM)-based integrated sensing and communi-
cations (ISAC) system, where the AFDM waveform is used
to simultaneously carry communications information and sense
targets. To realize AFDM-based sensing functionality, two pa-
rameter estimation methods are designed to process echoes
in the time domain and the discrete afﬁne Fourier transform
(DAFT) domain, respectively. It allows us to decouple delay and
Doppler shift in the fast time axis and can maintain good sensing
performance even in large Doppler shift scenarios. Numerical
results verify the effectiveness of our proposed AFDM-based
system in high mobility scenarios.
Index Terms —Integrated sensing and communications, inte-
grated waveform, afﬁne frequency division multiplexing, discrete
afﬁne Fourier transform.
I. I NTRODUCTION
Next-generation wireless systems (beyond 5G/6G) are ex-
pected to maintain reliable communications in high mobility
scenario, improve spectral and energy efﬁciencies signiﬁcantly
and support ubiquitous connections of everything [1]. The inte-
grated sensing and communications (ISAC) technique is one of
the key enablers for beyond 5G/6G due to its ability to improve
spectral and energy efﬁciencies and obtain information about
the environment [2], [3].
Integrated waveform design is one of the cornerstones of
ISAC. One approach to design the integrated waveform is to
endow new functionality to traditional waveforms that have
been used in radar or communications systems [4]–[7]. For
example, the linear frequency modulation (LFM) waveform, a
classical radar waveform, is used to embed communications
information [4], [5]. Meanwhile, sensing functionality is added
to the orthogonal frequency division multiplexing (OFDM)
waveform that has been widely used in communications
systems (LTE, 5G NR, WiFi, etc.) due to its robustness
against multipath fading [6], [7]. Speciﬁcally, in [6], a symbol
division-based method is proposed to suppress the sidelobes of
radar image caused by random communications symbols and
estimate parameters of targets, i.e., range and velocity. The
symbol division operation is replaced with symbol conjugate
multiplication by utilizing the cyclic cross-correlation (CCC)
to avoid amplifying the noise background when symbols have
non-constant modulus in the frequency domain [7]. However,
the peak-to-sidelobe level ratio (PSLR) of radar images may
deteriorate severely in the high mobility scenarios due to the
couple of delay and large Doppler shift in the fast time axis.
Apart from traditional waveforms, some new waveforms are
investigated for both sensing and communications to improve
the overall performance of ISAC systems [8], [9]. The or-
thogonal time-frequency space (OTFS) waveform multiplexes
information symbols in the delay-Doppler domain [8], [10].
From the perspective of communications, the OTFS has the
ability to deal with large Doppler shift and obtain both
time and frequency diversities in doubly selective channels.
Moreover, it can achieve similar sensing performance with
OFDM as shown in [11]. Meanwhile, a chirp-based multicar-
rier waveform is proposed, namely orthogonal chirp-division
multiplexing (OCDM) [9], [12]. An important advantage of
chirp-based waveform is the potential to support full duplex
operation [13]. The OCDM multiplexes a set of orthogonal
chirps that are complex exponentials with linearly varying
instantaneous frequencies. Since each information is spanned
the entire bandwidth, OCDM can achieve full diversity in
frequency selective channels, which outperforms OFDM. The
sidelobe level of resulting radar image is slightly increased
compared with the OFDM waveform [14], [15]. However,
OCDM can not achieve full diversity in doubly selective
channels [16].
Recently, another chirp-based waveform, namely afﬁne fre-
quency division multiplexing (AFDM), is proposed by mul-
tiplexing information symbols in the discrete afﬁne Fourier
transform (DAFT) domain [16]–[18]. The AFDM waveform
can adapt to the channel proﬁle by optimizing its parameters
such that all paths can be separated in the DAFT domain. As
a result, AFDM can achieve full diversity in doubly selective
channels. The communications performances as well as pro-
cessing algorithms have been investigated for AFDM in [16]–
[18]. Results in [16] show that compared with OTFS, AFDM
has comparable communications performance in terms of bit
error rate (BER) but with lower complexity and the advantage
of less channel estimation overhead [16], [18]. Therefore,
AFDM is considered as a potential candidate waveform for
the ISAC system [13]. However, it remains interesting to
investigate the sensing performance of the AFDM waveform.
In this paper, we propose an AFDM-based ISAC system,
where the AFDM waveform is used to simultaneously carry
communications information of downlink user and sense in-
formation about the targets. Two methods are designed to esti-
mate the range and velocity parameters of targets using random
information symbols. The ﬁrst method extracts parameters in
the time domain utilizing the CCC with low complexity. The
arXiv:2208.13430v1  [eess.SP]  29 Aug 2022

<!-- extraction_page_index: 2 -->

Fig. 1. AFDM-based integrated sensing and communications system.
second method estimates parameters in the DAFT domain
by compensating for the linear phase shift and estimating
the cyclic shift of information symbols in the fast time axis.
Beneﬁting from decoupling delay and Doppler shift in the
fast time axis, the second method can enlarge the maximum
unambiguous Doppler shift and maintain good sensing perfor-
mance in large Doppler shift scenarios. Numerical results show
that our proposed AFDM-based system enjoys better PSLR
performance than the OFDM-based system in high mobility
scenarios.
II. S YSTEM MODEL
We consider an AFDM-based ISAC system, where the
ISAC base station (BS) transmits the AFDM waveform to the
downlink user and simultaneously receives echoes reﬂected by
the targets around it, as shown in Fig. 1.
A. Communications Signal Model
In this subsection, we brieﬂy review the basic concepts of
AFDM proposed in [16]–[18]. Let x denote an N×1 vector
of quadrature amplitude modulation (QAM) symbols. The N
points inverse DAFT (IDAFT) is performed to map x to the
time domain as
s [n] = 1√
N
∑N−1
m=0
x [m]ej2π(c1n2+ 1Nmn+c2m2), (1)
where c1 and c2 are the AFDM parameters, and n =
0,...,N −1. Then, a chirp-periodic preﬁx (CPP) is added with
a length of Ncp.
After transmission over the channel, discarding CPP and
performing N points DAFT, the received sample matrix in
the DAFT domain can be written in the matrix form as
y = Heﬀ x + ˜w, (2)
where ˜w ∼ CN
(
0,σ2c I) is an additive Gaussian noise
vector and Heﬀ=Λc2 F Λc1 HcΛHc1 F HΛHc2 with F be-
ing the discrete Fourier transform (DFT) matrix [16],
Λci=diag
(
e−j2πcin2,n = 0,...,N −1), Hc being the ma-
trix representation of the communications channel in the time
domain, and (·)H denoting Hermitian transpose.
B. Radar Signal Model
This paper considers that the ISAC BS uses an AFDM frame
withNsym AFDM symbols to sense the targets around it. We
derive the AFDM-based signal model of target echoes.
Let X=
[
x0,..., xNsym−1
]
and S=
[
s0,..., sNsym−1
]
denote the N×Nsym blocks of QAM symbols and modulated
signals in time domain, respectively. After adding CPP and
parallel to serial conversion, the signal to be transmitted
is given by ˜s∈C(N+Ncp)Nsym×1. Consider P targets. The
scattering coefﬁcient, range, velocity, time delay and Doppler
frequency of the i-th target are denoted by hi, Ri, vrel,i,
τi=2Ri/c, fd,i=2vrel,ifc/c with c and fc being the speed
of light and the frequency of carrier, respectively, and i =
1,...,P . The received target echo in the time domain is [19,
Eq. (6)]
r [n] =
∑P
i=1
˜his [n−li]ej2πfin + wr [n], (3)
where n=0,..., (N+Ncp)Nsym−1, wr [n]∼CN
(
0,σ2r) is
the noise, ˜hi=hie−j2πfd,iτi, li=τi/ts, fi=fd,its, and ts de-
notes the sampling interval. Following [6], [7], [16], it is
assumed thatNcp is greater than the maximum delaylmax. We
deﬁne νi =Nfi = fd,i∆f =αi +ai, where νi∈ [−νmax,ν max]
is the Doppler shift normalized with respect to the subcar-
rier spacing ∆f, αi∈ [−αmax,α max] is its integer part, and
ai∈
(
− 12, 12] is its fractional part [16].
After serial to parallel conversion and discarding CPP, the
received target echo can be expressed as
R [n,k ] =
P∑
i=1
˜hiS [n−li,k ]ej2πfi[n+(N+Ncp)k]+Wr [n,k ],
(4)
where Wr denotes noise matrix, n = 0,...,N −1, and k =
0,...,N sym−1. Performing N points DAFT on each column
of R, the DAFT domain samples matrix Yr can be given by
Yr [m,k ] = 1N
N−1∑
n=0
R [n,k ]e−j2π(c1n2+ 1Nmn+c2m2), (5)
where m = 0,...,N −1 and k = 0,...,N sym−1.
As a result, motivated by [16, Eq. (26)], the input-output
relation in DAFT domain can be written in the matrix form
as
Yr =
∑P
i=1
˜hiHiXDi + ˜Wr, (6)
where Di = diag
(
e−j2πfi(N+Ncp)k), k=0,...,N sym−1,
Hi [p,q ] = 1Nej 2πN (Nc 1l2i−qli+Nc 2(q2−p2))Fi (p,q )
and ˜Wr = Λc2 F Λc1 Wr. Different from [16], here
Fi (p,q ) =e−j2π(p−q−vi +2Nc 1li)−1e−j 2πN (p−q−vi +2Nc 1li)−1. Similar to [16], in theinteger normalized Doppler shift case, i.e., ai=0, there is only
one non-zero element in each row of Hi, i.e., the element of
Hi at row p and column q can be written as
Hi [p,q ] =
{
ej 2πN (Nc 1l2i−qli+Nc 2(q2−p2)), q = (p +loci)N,
0, otherwise,
(7)

<!-- extraction_page_index: 3 -->

where loci=(2Nc1li−αi)N and (·)N is the modulo N oper-
ation. Hence, the input-output relation can be rewritten as
Yr [p,k ] =
P∑
i=1
˜hiej2πfi(N+Ncp)k
×ej 2πN (Nc 1l2i−qili+Nc 2(q2i−p2))X [qi,k ] + ˜Wr [p,k ], (8)
where p=0,...,N −1, qi=(p +loci)N and k=0,...,
Nsym−1. In the fractional normalized Doppler shift case,
there are 2kv+1 non-zero elements and the peak is still at
q=(p +loci)N in each row of Hi.
C. Communications Processing
The communications processing algorithms for AFDM, i.e.,
channel estimation, equalization and symbol detection, have
been studied in [16]–[18], [20]. In the AFDM-based ISAC
system, the downlink user can exploit these methods to process
received AFDM waveform and obtain the communications
information. In this paper, we mainly focus on estimating the
parameters of targets based on the AFDM waveform.
III. AFDM-B ASED PARAMETER ESTIMATION METHODS
In this section, we propose two parameter estimation meth-
ods based on the AFDM waveform to estimate the range and
velocity of targets in the time domain and the DAFT domain,
respectively.
A. Parameter Estimation in Time Domain
We exploit the Fast Cyclic Correlation Radar (FCCR)
algorithm [7] to estimate the range and velocity of targets.
Speciﬁcally, each column of the received signal matrix R
and the transmit matrix S in the time domain undergoes
the N points DFT, which results in two N×Nsym matrices
in the frequency domain. Then, the element-based conjugate
multiplication is performed on the resulting matrices. The N
points inverse DFT (IDFT) is computed for each column of
matrix and the Nsym points DFT is calculated for each row
of matrix. After these steps, a two-dimensional (2-D) range-
Doppler matrix (RDM) is produced, which represents a 2-D
radar image in range and Doppler.
As mentioned in [6], the processing gain Gp=NNsym,
and the maximum unambiguous Doppler shift is given by
±1/(2TAFDM ), where TAFDM denotes the duration of a
AFDM symbol including CPP.
B. Parameter Estimation in DAFT Domain
We start from analyzing the input-output relation in the
DAFT domain and then propose a method to estimate the
range and velocity of targets in the DAFT domain. This
method is derived utilizing the input-output relation in the
integer normalized Doppler shift case, and numerical results
show that it is also suitable for the fractional normalized
Doppler shift case.
Following [16],c1 is set as c1 = 2(αmax+kv)+12N andc2 is set
to be a rational number sufﬁciently smaller than 12N . Thus, if
c2 is small enough, the value of Nc2
(
qi2−p2) will approach
zero. Let qi=(p +loci)N=p+di, i.e., di=(p +loci)N−p.
Equation (8) can be rewritten as
Yr [p,k ]≈
P∑
i=1
ζiej2πfi(N+Ncp)ke−j 2πN lipX [p+di,k ]
+ ˜Wr [p,k ], (9)
where ζi = ˜hiej 2πN (Nc 1l2i−dili). We can see from (9) that in
each row of Yr, i.e. ﬁxing p, there is the linear phase shift be-
tween the information symbols X [p, :] along thek-axis, which
is caused by the Doppler shift. In each column of Yr, i.e. ﬁxing
k, there are the linear phase shift between the information
symbols X [:,k ] and the cyclic shift of information symbols
X [:,k ]. The former is caused by the delay li, and the latter
is caused by the delay li and the integer part of normalized
Doppler shift, i.e., αi. Due to this couple of linear phase
shift and cyclic shift along the p-axis, the sidelobes of the
radar image obtained by the FCCR algorithm will be severely
deteriorated when the Doppler shift is large. Numerical results
will verify this conclusion.
To this end, we propose a parameter estimation method in
the DAFT domain, which consists of four steps, to enjoy good
performance in large Doppler scenarios. Speciﬁcally, in the
ﬁrst step, we compensate for the linear phase shift along the
p-axis caused by the delay li. The index of the cyclic shift
of information symbols X and the linear phase shift along
the k-axis caused by the Doppler shift are estimated by the
matched ﬁler in the DAFT domain and the DFT operation,
respectively, in the second step. In the third step, the delay
and Doppler shift are extracted from the resulting matrices
using our derived relationships of delay and Doppler shift to
the peak index. In the fourth step, the extracted integer and
fractional normalized Doppler shifts are combined to enlarge
the maximum unambiguous Doppler shift.
1) Compensating for linear phase shift: We ﬁrst remove
the effect of the linear phase shift in each column of Yr
by actively compensating for it. According to the above
assumption that the CPP length Ncp is greater than the
maximum delay lmax, the delay l is satisﬁed 0≤ l < Ncp.
For each delay l, we generate a compensation matrix Ll =
diag
(
ej 2πN lp,p =0,...,N − 1) and multiply it by Yr, i.e.,
Zl = LlY and
Zl [p,k ] =
P∑
i=1
ζiej2πfi(N+Ncp)kej 2πN (l−li)pX [p +di,k ]
+ ˜Wr [p,k ], l=0,...,N cp− 1. (10)
This process results in Ncp matrices.
2) Matched ﬁler in DAFT domain and DFT: Next, we
exploit the matched ﬁlter in the DAFT domain to estimate
the index of the cyclic shift of information symbols X.
Speciﬁcally, for l=0,...,N cp− 1, each column of Zl and X
undergoes aN points DFT. Then, the element-based conjugate
multiplication is performed. Finally, the N points IDFT is
computed for each column and the Nsym points DFT is

<!-- extraction_page_index: 4 -->

calculated for each row 1. The resulting matrix can be written
in the matrix form as
Wl = F H((F LlYr)∗⊙ (F X)) F, (11)
where (·)∗ and ⊙ are conjugate and Hadamard product,
respectively.
3) Extracting delay and Doppler shift: After the previ-
ous steps, we get Ncp matrices that contain the delay and
Doppler information of P targets. Next, we investigate how
to extract these information from these Ncp matrices. When
l=li, ej 2πN (l−li)p=1 for p=0,...,N − 1, i.e., the effect of
linear phase shift caused by the delay is removed, and the
resulting matrix Wl will contain one or more peaks (depending
on how many targets have this delay and different Doppler
shift). We can use the existing constant false alarm rate
(CFAR) algorithm to detect the existence of targets [21]. If
the magnitude of peak of Wl, l=0,...,N cp− 1, exceeds
the threshold, there is a target whose corresponding delay
estimation is ˆli =l. Let ¯pi and ¯ki denote the indexes of row
and column of the peak exceeding the threshold in Wl. As
mentioned earlier, the index of the cyclic shift of X is caused
by li and αi. Therefore, we can get the estimation of integer
part of normalized Doppler shift, given by
ˆαi = 2Nc1ˆli−(1− ¯pi)N. (12)
Similar to the time domain method in Sec. III. A, the max-
imum unambiguous Doppler shift that ¯ki can represent is
±1/(2TAFDM )=± 12∆f′, where ∆f′=1/TAFDM . We de-
ﬁneν′i=fd,i∆f′ =βi+bi, where ν′i∈ [−ν′max,ν′max] is the Doppler
shift normalized with respect to the maximum unambiguous
Doppler shift ∆f′, βi∈ [−βmax,β max] is its integer part, and
bi∈
(
− 12, 12] is the fractional part. Consequently, the estimation
of the fractional Doppler shift bi is given by
ˆbi =
(¯ki− 1−Nsym/2)
Nsym
. (13)
4) Combining integer and fractional Doppler shift: Now,
we have extracted the delay li, the integer Doppler shift αi
(normalized with ∆f) and the fractional Doppler shift bi
(normalized with ∆f′) from matrices Wl, l=0,...,N cp− 1.
If integer and fractional Doppler shifts can be combined, the
maximum unambiguous Doppler shift will be signiﬁcantly
increased for a given TAFDM . Note that the values of αi and
bi cannot be directly added because they are the integer and
fractional parts of two different normalized Doppler shifts ν
andν′, respectively. According to the deﬁnitions of αi andbi,
we can get
ˆfd,i = (ˆαi + ˆai) ∆f =
(
ˆβi + ˆbi
)
∆f′, (14)
and
ˆai = ∆f′∆f ( ˆβi + ˆbi)− ˆαi
= NN +Ncp ˆβi + NN +Ncpˆbi− ˆαi. (15)
1The result of DFT is circularly shifted by Nsym/2 positions.
(a)
 (b)
Fig. 2. Judgment criterion: (a) if Wˆli
[
¯pi−1, ¯ki] > Wˆli [¯pi+1, ¯ki],ˆβi=ˆβi,min; (b) if Wˆli [¯pi−1, ¯ki] ≤ Wˆli [¯pi+1, ¯ki], ˆβi=ˆβi,max.
We can see that ˆai is a function of ˆβi. According
to the condition ai ∈
(
− 12, 12], we can get ˆβi ∈(
N+Ncp
N ˆαi− ˆbi− 0.5N+NcpN , N+NcpN ˆαi− ˆbi + 0.5N+NcpN
]
.
The minimum and maximum values of ˆβi are
ˆβi,min =
⌈
N+Ncp
N ˆαi− ˆbi− 0.5N+NcpN
⌉
and ˆβi,max =⌊
N+Ncp
N ˆαi− ˆbi + 0.5N+NcpN
⌋
, respectively, where ⌈·⌉ and
⌊·⌋ denote the cell and ﬂoor functions, respectively. When
0≤Ncp <N , there are only two cases, either ˆβi,max= ˆβi,min
or ˆβi,max= ˆβi,min+1. If ˆβi,max= ˆβi,min, let ˆβi= ˆβi,max and
substitute it into (15) to compute ˆai. If ˆβi,max= ˆβi,min+1, we
introduce a criterion to judge whether ˆβi should be equal toˆβi,max or ˆβi,min, i.e.,
ˆβi =
{
ˆβi,min, Wˆli
[
¯pi− 1, ¯ki]> Wˆli[¯pi + 1, ¯ki],ˆβi,max, otherwise,
(16)
where Wˆli
[
¯pi−1, ¯ki] and Wˆli[¯pi+1, ¯ki] are two elements
next to the peak (i.e., Wˆli
[
¯pi, ¯ki]) along the p-axis, as shown
in Fig. 2.
IV. N UMERICAL SIMULATIONS AND ANALYSES
In this section, numerical results based on Monte Carlo sim-
ulations are presented. Following [6], our simulation parame-
ters are listed in Table I. The information bits are modulated by
16-QAM. Let SNRsig denote the signal-to-noise ratio (SNR)
of received signal, and we set αmax = 2 and kv = 4 [16]. As a
comparison, the performance of OFDM waveform processed
by the symbol division method is also presented [6].
Figure 3 shows the normalized radar images obtained by
the OFDM and AFDM waveforms with different Doppler
shift. “OFDM-symbol-division”, “Pro-time-domain” and “Pro-
DAFT-domain” represent the OFDM-based symbol division
method, our proposed AFDM-based methods in the time
domain and the DAFT domain, respectively. For the symbol
division method and our time-domain method, this radar image
denotes radar range proﬁle whose peak indicates the range of
target. For our DAFT-domain method, the peak of this radar
image simultaneously contains the information of the range
and velocity of target. Therefore, the location of the peak
obtained by our DAFT-domain method differs from that of
the other two methods, as shown in Fig. 3. When fd=0.1∆f ,

<!-- extraction_page_index: 5 -->

TABLE I
PARAMETERS IN OUR SIMULATIONS
Symbol Parameter Value
fc Carrier frequency 24 GHz
N Number of subcarriers 4096
Nsym Number of AFDM symbols 256
B Signal Bandwidth 93.1 MHz
∆f Subcarrier spacing 22.729 kHz
T AFDM symbol duration 44 µs
Ncp Chirp-periodic preﬁx length 256 µs
Tcp Chirp-periodic preﬁx duration 2.75 µs
TAF DM Total AFDM symbol duration 46.75 µs
∆R Range resolution 1.61 m
∆v Velocity resolution 0.52 m/s
Gp Processing gain 60.2 dB
0 1000 2000 3000 4000
index
-80
-70
-60
-50
-40
-30
-20
-10
0
Normalized magnitude of output (dB)
OFDM-symbol-division
Pro-time-domain
Pro-DAFT-domain
(a) fd=0.1∆f
0 1000 2000 3000 4000
index
-70
-60
-50
-40
-30
-20
-10
0
Normalized magnitude of output (dB)
OFDM-symbol-division
Pro-time-domain
Pro-DAFT-domain
(b) fd=0.98∆f
Fig. 3. Calculated radar image for OFDM and AFDM waveforms with
SNRsig=10 dB, P =1 and l=128.
our time-domain and DAFT-domain methods offer similar
PSLRs, which are slightly lower than that of the symbol
division method. When fd=0.98∆f , the PSLRs of our time-
domain method and the symbol division method deteriorate
severely. However, our DAFT-domain method still maintains
good PSLR performance.
Figure 4 illustrates the corresponding image SNR, which is
the ratio between the peak caused by target and the average
noise level in the 2-D radar image [6], versus the SNR of
received signal. The solid and dashed lines represent the cases
offd=0.1∆f andfd=0.98∆f , respectively. It can be observed
that in the case of fd=0.1∆f , the available image SNRs
decrease almost linearly with SNRsig for all methods for a
-40 -30 -20 -10 0 10 20
Input SNR (dB)
0
10
20
30
40
50
60
70Image SNR (dB)
OFDM-symbol-division
Pro-time-domain
Pro-DAFT-domain
Fig. 4. Image SNR versus the SNR of received signal with P =1 andl=128.
0 0.5 1 1.5 2
-10
0
10
20
30
40
50
60
Image SNR (dB)
OFDM-symbol-division
Pro-time-domain
Pro-DAFT-domain
Fig. 5. Image SNR versus the normalized Doppler shift ν with SNRsig=0
dB, P =1 and l=128.
SNRsig below 0 dB. There appears a saturation of image
SNR starting approximately at the SNRsig of 10 dB for our
proposed methods. The symbol division method can output
higher image SNR at high SNRsig regions. In the case of
fd=0.98∆f , there appears a saturation of image SNR for all
methods, and the image SNRs severely decrease for our time-
domain method and the symbol division method. However, the
image SNR of our DAFT-domain method decreases slightly.
Furthermore, our two methods outperform the symbol division
method.
We compare the image SNR versus normalized Doppler
shift ν, as shown in Fig. 5. It can be seen that in the low
Doppler shift region ( ν < 0.5), all three methods output
similar image SNRs. As Doppler shift increases, the image
SNRs of our time-domain method and the symbol division
method decreases severely ﬁrst and then increases. The min-
imum SNRs ( <0 dB) are achieved at integer ν. However,
our DAFT-domain method can always output an image SNR
greater than 50 dB, which veriﬁes that our DAFT-domain
method can work in both integer and fractional normalized
Doppler shift scenarios.
Figure 6 shows radar image obtained by our DAFT-
domain method for multiple targets. There are P =3 point-
like targets with ranges R= [400 m, 402 m, 402 m] and ve-
locities vrel= [255 m/s, 255 m/s, 256 m/s] (corresponding
fd=1.8∆f ). Unlike the radar image obtained by the symbol
division method [6], our DAFT-domain method produces mul-

<!-- extraction_page_index: 6 -->

-15 -14 -13 -12 -11 -10
Velocity (m/s)
865
870
875
880
885 index
(a)
-15 -14 -13 -12 -11 -10
Velocity (m/s)
839
844
849
854
859 index
10
20
30
40
50
60 (b)
Fig. 6. Normalized radar images calculated with our AFDM-based DAFT-
domain method for 3 targets with SNRsig=0 dB, corresponding the range
(a) R=400 m and (b) R=402 m, respectively.
TABLE II
COMPARISON OF ESTIMATION OF VELOCITY
fd Velocityvrel Velocity ˆv1 Velocity ˆv2
0.45∆f 63.9 m/s (230.1 km/h) 63.7 m/s 63.7 m/s
1.4∆f 197.6 m/s (711.5 km/h) 63.7 m/s 197.4 m/s
2.0∆f 284.1 m/s (1022.74 km/h) -65.3 m/s 284.1 m/s
tiple radar image simultaneously. Each radar image contains
the information of the targets having the same range. As shown
in Figs. 6(a) and 6(b), there are two radar images that contain
peaks exceeding the threshold. The latter contains two targets
with different velocity. Hence, all three targets can be detected
from these radar images.
Table II lists the velocity estimation of our time-domain
and DAFT-domain methods with P =1 and l=128, where
fd and vrel denote truth Doppler shift and corresponding
velocity of target, respectively. ˆv1 and ˆv2 are estimated ve-
locities of time-domain and DAFT-domain methods, respec-
tively. We can see that when fd=0.45∆f , both methods
can correctly estimate the velocity. When fd=1.4∆f and
fd=2.0∆f , the time-domain method outputs the wrong veloc-
ity due to ambiguity (its maximum unambiguous Doppler shift
=± 1/(2TAFDM )=± 0.47∆f ). However, the DAFT-domain
method still works well.
V. C ONCLUSION
In this paper, we proposed an AFDM-based ISAC systems.
Two methods were proposed to estimate the range and ve-
locity of targets in the time domain and the DAFT domain,
respectively. The latter signiﬁcantly increased the maximum
unambiguous Doppler shift and still enjoyed good PSLR and
image SNR performances in high mobility scenarios.
ACKNOWLEDGMENT
This work was supported by the National Natural Science
Foundation of China under Grant 61971025, 62071026 and
61941106. This research was supported by the high perfor-
mance computing (HPC) resources at Beihang University.
REFERENCES
[1] IMT-2030 (6G) Promotion Group, “White paper on 6G vision and
candidate technologies,” http://www.caict.ac.cn/english/news/202106/
t20210608 378637.html, 2021.
[2] F. Liu, C. Masouros, A. Petropulu, H. Grifﬁths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun., vol. 68, no. 6, pp. 3834–3862, Jun
2020.
[3] F. Liu, Y . Cui, C. Masouros, J. Xu, X. Han, Y . Eldar, and S. Buzzi, “In-
tegrated sensing and communications: Towards dual-functional wireless
networks for 6G and beyond,” IEEE J. Sel. Areas Commun. , 2022.
[4] Y . Ni, Z. Wang, Q. Huang, and M. Zhang, “High throughput rate-shift
integrated system for joint radar-communications,” IEEE Access, vol. 7,
pp. 78 228–78 238, May 2019.
[5] Y . Zhang, Q. Li, L. Huang, C. Pan, and J. Song, “A modiﬁed waveform
design for radar-communication integration based on LFM-CPM,” in
Proc. 85th IEEE Veh. Technol. Conf. (VTC Spring) , Jun 2017, pp. 1–5.
[6] C. Sturm and W. Wiesbeck, “Waveform design and signal processing
aspects for fusion of wireless communications and radar sensing,” Proc.
IEEE, vol. 99, no. 7, pp. 1236–1259, Jul.
[7] Y . Zeng, Y . Ma, and S. Sun, “Joint radar-communication with cyclic
preﬁxed single carrier waveforms,” IEEE Trans. Veh. Technol., vol. 69,
no. 4, pp. 4069–4079, Apr 2020.
[8] P. Raviteja, K. T. Phan, Y . Hong, and E. Viterbo, “Interference can-
cellation and iterative detection for orthogonal time frequency space
modulation,” IEEE Trans. Wireless Commun., vol. 17, no. 10, pp. 6501–
6515, Oct 2018.
[9] X. Ouyang and J. Zhao, “Orthogonal chirp division multiplexing,” IEEE
Trans. Commun., vol. 64, no. 9, pp. 3946–3957, Sep 2016.
[10] R. H. et al., “Orthogonal time frequency space (OTFS) modulation
for millimeter-wave communications systems,” in Proc. IEEE MTT-S
International Microwave Symposium (IMS) . IEEE, Jun 2017, pp. 681–
683.
[11] L. Gaudio, M. Kobayashi, G. Caire, , and G. Colavolpe, “On the
effectiveness of OTFS for joint radar parameter estimation and commu-
nication,” IEEE Trans. Wireless Commun., vol. 19, no. 9, pp. 5951–5965,
Sep 2020.
[12] M. S. Omar and X. Ma, “Performance analysis of OCDM for wireless
communications,” IEEE Trans. Wireless Commun. , vol. 20, no. 7, pp.
4032–4043, Jul 2021.
[13] Q. Wang, A. Kakkavas, X. Gong, and R. A. Stirling-Gallacher, “Towards
integrated sensing and communications for 6g,” in Proc. 2nd IEEE
International Symposium on Joint Communications & Sensing (JC&S) .
IEEE, 2022, pp. 1–6.
[14] L. G. de Oliveira and M. B. Alabd and B. Nuss and T. Zwick,
“An OCDM radarcommunication systemn,” in Proc. 14th European
Conference on Antennas and Propagation (EuCAP), Mar 2020, pp. 1–5.
[15] L. G. de Oliveira and B. Nuss and M. B. Alabd and Y . Li and
L. Yu and T. Zwick, “MIMO-OCDM-based joint radar sensing and
communication,” in Proc. 15th European Conference on Antennas and
Propagation (EuCAP), Mar 2021, pp. 1–5.
[16] A. Bemani, N. Ksairi, and M. Kountouris, “Afﬁne frequency divi-
sion multiplexing for next generation wireless communications,” arXiv
preprint arXiv:2204.12798, 2022.
[17] A. Bemani and N. Ksairi and M. Kountouris, “AFDM: A full diversity
next generation waveform for high mobility communications,” in IEEE
International Conference on Communications Workshops (ICC Work-
shops). IEEE, 2021, pp. 1–6.
[18] A. Bemani, G. Cuozzo, N. Ksairi, and M. Kountouris, “Afﬁne frequency
division multiplexing for next-generation wireless networks,” in Proc.
17th International Symposium on Wireless Communication Systems
(ISWCS). IEEE, 2021, pp. 1–6.
[19] K. Wu, J. A. Zhang, X. Huang, and Y . J. Guo, “Integrating low-
complexity and ﬂexible sensing into communication systems,” IEEE J.
Sel. Areas Commun. , vol. 40, no. 6, pp. 1873–1889, Jun 2022.
[20] H. Yin and Y . Tang, “Pilot aided channel estimation for afdm in doubly
dispersive channels,” arXiv preprint arXiv:2203.05781 , 2022.
[21] M. Kronauge and H. Rohling, “Fast two-dimensional CFAR procedure,”
IEEE Trans. Aerosp. Electron. Syst. , vol. 49, no. 3, pp. 1817–1823, Jul
2013.
