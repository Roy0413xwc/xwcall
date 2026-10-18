---
title: "Under-Determined DOA Estimation A Method Based on Higher-Order Statistics and Non-Uniform Arrays"
zotero_key: "74WGPALB"
pdf_key: "MD4SYGJS"
collection: "信道估计"
source: "User-provided PDF (pypdf extraction)"
page_mapping: unverified
---

# Under-Determined DOA Estimation A Method Based on Higher-Order Statistics and Non-Uniform Arrays — Fulltext

> 由用户提供的 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 23, NO. 11, NOVEMBER 2024 15903
Under-Determined DOA Estimation: A Method
Based on Higher-Order Statistics and
Non-Uniform Arrays
Wei Peng
 , Senior Member , IEEE, Peng Li, Xinyi Wu
 , Kai Luo
 , Member , IEEE, Gan Zheng
 , Fellow, IEEE,
and Dong Li
 , Member , IEEE
Abstract— Direction of arrival (DOA) estimation is widely
used in many applications. Traditional DOA estimation generally
adopts the second-order statistics and the uniform linear array
(ULA) structure. However, the second-order statistics and the
uniform array structure restrict the number of DOAs that
can be accurately estimated. In addition, the performance of
the second-order statistics-based methods is sensitive to noise.
As the wireless environment is becoming increasingly complex
with the advent of the 5G era, the propagation channel can
be composed of numerous paths. When the number of paths
exceeds the size of the antenna array, DOA estimation becomes
an under-determined problem, which the second-order statistics-
based traditional methods fail to deal with. In order to address
the under-determined DOA estimation problem, this paper
proposes a method based on higher-order statistics and non-
uniform array structure. Higher-order statistics-based methods
can not only expand the array aperture, but also suppress the
additive Gaussian noise. However, if combined with a uniform
array structure, the degrees of freedom of the expanded array
is limited. Therefore, we further adopt a non-uniform array
structure and optimize its structure. Consequently, the proposed
method is capable of achieving M 2-level DOA estimation with an
M -element array, while simultaneously providing good robust-
ness to noise. For instance, using the proposed method, the DOAs
of 20 incoming wave directions can be accurately estimated with
a 6-antenna non-uniform array when the signal-to-noise ratio is
as low as 0 dB.
Manuscript received 18 January 2024; revised 13 May 2024; accepted
13 July 2024. Date of publication 5 August 2024; date of current version
13 November 2024. This work was supported in part by the National Key
Research and Development Program under Grant 2019YFE0110200, in part by
the National Natural Science Foundation of China under Grant 6217011548,
Grant 62071352, and Grant U20B200077, in part by the Shenzhen Science
and Technology Fund under Grant JCYJ20210324135206018, and in part by
the Science and Technology Development Fund, Macau, SAR, under Grant
0188/2023/RIA3. The associate editor coordinating the review of this article
and approving it for publication was S. Mazuelas. (Corresponding author:
Wei Peng.)
Wei Peng is with the School of Cyber Science and Engineering, Huazhong
University of Science and Technology, Wuhan 430074, China, and also with
the Research Institute, Huazhong University of Science and Technology,
Shenzhen 518038, China (e-mail: pengwei@hust.edu.cn).
Peng Li and Xinyi Wu are with the Research Center of 6G Mobile Com-
munications and the School of Electronic Information and Communications,
Huazhong University of Science and Technology, Wuhan 430074, China.
Kai Luo is with the School of Electronics and Communication Engi-
neering, Sun Yat-sen University, Guangzhou 510275, China (e-mail:
kluo@mail.sysu.edu.cn).
Gan Zheng is with the School of Engineering, University of Warwick, CV4
7AL Coventry, U.K. (e-mail: Gan.Zheng@warwick.ac.uk).
Dong Li is with the School of Computer Science and Technology,
Macau University of Science and Technology, Macau, China (e-mail:
dli@must.edu.mo).
Color versions of one or more figures in this article are available at
https://doi.org/10.1109/TWC.2024.3434981.
Digital Object Identifier 10.1109/TWC.2024.3434981
Index Terms — DOA estimation, higher-order statistics, non-
uniform array, under-determined estimation.
I. I NTRODUCTION
D
IRECTION of arrival (DOA) is widely used in location-
based services, such as wireless indoor positioning, radar
detection, underwater sonar reconnaissance and other applica-
tions [1]. With the advent of the 5G era, the communication
scenarios are becoming more complex and heterogeneous, and
the DOA estimation problem is becoming more challenging.
For example, the DOA estimation in millimeter-wave MIMO
systems [2], and in the unmanned aerial vehicle (UA V) sys-
tems for air-to-ground (A2G) communication [3]. One of the
greatest challenges is that, in a rich scattering environment,
the number of signal propagation paths can be greater than the
number of receive antennas. In this case, the DOA estimation
becomes under-determined, which is much more difficult than
the determined estimation.
Traditional DOA estimation algorithms generally employ
second-order statistics based subspace methods, which can be
categorized into two distinct groups. The first group makes
use of the orthogonality between the signal and the noise
spaces, such as MUSIC [4], [5], [6] and Min-Norm [7],
[8], [9] algorithms. The second approach makes use of the
rotational invariance of the signal subspace, such as ESPRIT
[10] algorithm and its derivative methods [11], [12], [13],
[14], [15], [16]. However, it is well established that traditional
methods based on the second-order statistics are only suitable
for determined scenarios. With an M-antenna uniform linear
array (ULA), the traditional DOA estimation methods can
at most estimate M− 1 DOAs. Furthermore, these methods
are sensitive to the influence of additive noise, which can
significantly impair the estimation performance in the presence
of substantial noise. In addition, a considerable number of
artificial intelligence (AI) and machine learning-based DOA
estimation methods [17], [18], [19], [20] have been reported
in recent years. These data-driven works map the input signal
and output estimation results through neural networks. They
usually require a large amount of labelled data for training, and
are less readily interpretable. In addition, the under-determined
scenario is rarely considered in these works.
To deal with the under-determined DOA estimation prob-
lem, higher-order statistics [21], [22], [23], [24], [25], [26],
[27], [28], [29], [30], [31], [32], [33], [34], [35] are exploited
in combination with MUSIC [22], [23], [24] or ESPRIT [33],
1536-1276 © 2024 IEEE. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

15904 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 23, NO. 11, NOVEMBER 2024
[34], [35] algorithms. By calculating the Kronecker products
of the received signals, higher-order statistics expand the array
size by virtually generated antennas, and the M× M covari-
ance matrix used by the second-order statistics is replaced by
an M 2×M 2 quasi-covariance matrix. In theory, an M-element
antenna array can at most estimate M 2− 1 DOAs using
the higher-order statistics. However, when the uniform linear
array (ULA) is used, there will be M 2− 2M + 1 duplicated
virtual antennas and the number of paths that can be effectively
estimated will be greatly reduced to 2M− 1.
ULA is a commonly used array structure. It is typically
designed with a half-wavelength space between the neigh-
boring antennas. As previously mentioned, when the number
of antennas increases, the array can be used to estimate a
larger number of DOAs. However, it is uneconomical or
even impossible to increase the number of antennas without
limit. Non-uniform array structure [36], [37], [38], [39], [40],
[41], [42], [43], [44], [45], [46], [47], [48] can be employed
to achieve a larger array aperture without the necessity of
increasing the number of antennas. The minimun redundant
array (MRA) is a typical non-uniform array geometry [36],
among this kind of array, nested arrays [38], [39], [40], [41]
and co-prime arrays [43], [44], [45] are intensively studied,
and closed-form solutions have been obtained [46]. However,
the MRA still has the problem of duplicated virtual antennas
when combied with higher-order cumulants, which is similar
to the ULA. The sparse array (SA) also uses the non-uniform
array geometry. A ULA fitting principle has been proposed
for SA designing to improve the uniform degrees of freedom
(uDOF) thus expand the aperture of the array [47], [48]. In
addition, AI-based methods has also been proposed to select
a non-uniform active sub-arrays to save energy and training
overhead [49], [50].
This paper aims for accurate DOA estimation for the DOA
of each propagation path in an under-determined scenario.
To achieve this goal, we propose a DOA estimation method
using the fourth-order cumulants and the non-uniform antenna
array. Specifically, the contributions of this paper are as
follows: Firstly, an algorithm for DOA estimation based on
the fourth-order cumulant quasi-covariance matrix is proposed,
which can expand the array aperture as well as significantly
suppress the additive Gaussian noise. Secondly, in order to
further improve the under-determined estimation ability of
the proposed algorithm, the non-uniform array geometry is
employed. In addition, a maximum non-redundancy principle
is proposed to optimize the non-uniform array structure. As a
whole, the proposed method enables M (M + 1) /2− 1 accu-
rate DOA estimation by an M-antenna array.
Simulations are carried out to validate the effectiveness of
the proposed under-determined DOA estimation method. The
results demonstrate that the proposed method outperforms the
other methods under consideration., particularly in the low
SNR region. For instance, the DOAs of 20 incoming wave
directions can be accurately estimated with a 6-element non-
uniform linear array (NULA) when the SNR is as low as 0 dB.
The rest of the paper is organized as follows. The channel
model is introduced in Section II. The DOA estimation using
the fourth-order cumulants is proposed in Section III. The
TABLE I
DESCRIPTION OF SYMBOLS
expanded antenna array with virtual antennas is analyzed in
Section IV and then the optimal non-uniform antenna array
structure is designed in Section V. Simulation results are
presented in Section VI and finally the paper is concluded
in Section VII.
Notations: in this paper, (·)T denotes the transpose oper-
ation, (·)H denotes the conjugate transpose operation, E{·}
denotes the expectation, and⊗ denotes the Kronecker product.
Other frequently used symbols are listed in Table I.
II. C HANNEL MODEL
Assume that the base station has a linear array with M
omnidirectional antennas. Taking the first array element as
the reference, the position vector of the array elements is
d = [0, d1,··· , dM−1]T . Under the far-field assumption, the
transmitted signal s (t) reaches the base station through P
propagation paths, and the received signal in the narrow-band
system is given by [51]
y (t) =
PX
p=1
βpa (θp) s (t− τp) + w (t), (1)
where y (t)∈ CM×1 denotes the received signal vector of
M antennas at the time instant t, βp, θp, and τp denote
the complex gain, DOA, and time delay of the p-th path,
respectively. a (θp) is the corresponding steering vector of
the p-th path. λ denotes the wavelength of the signal, and
w (t) ∈ CM×1 is the vector of additive white Gaussian
noise.
For the sake of simplicity, we use the ULA structure as
an example to illustrate the steering vector of the antenna
array. Actually, other geometries can also be adopted as the
array structure. For a ULA, the antennas are uniformly spaced.
Define the unit spacing between the antenna elements as d,
which is often set to be half of the wavelength, i.e., d = λ2 .
Thus, the steering vector a (θp) is given by
a (θp) =
h
1, e−j2π dλ sin(θp),··· , e−j2π (M−1)dλ sin(θp)iT . (2)
In matrix form, Eq. (1) is re-written as
y (t) = A (θ) Fs (t) + w (t) , (3)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

PENG et al.: UNDER-DETERMINED DOA ESTIMATION 15905
where A (θ) = [ a (θ1), ··· , a (θP )], F =
diag (β1,··· , βP ), and s (t) = [s (t− τ1) ··· s (t− τP )]T is
the transmit signal vector.
Assume the length of the sampling sequence is K, then the
received signal is given as
Y = A (θ) FSTt · g (τ1) ,··· , g (τP)T + W, (4)
where Y∈ CM×K, St is the Toeplitz matrix composed of the
sampling sequence of the transmitted signal, g (τi)∈ CK×1 is
the pulse-shaping vector, and W∈ CM×K is the noise matrix.
III. U NDER -D ETERMINED DOA E STIMATION METHOD
BASED ON THE FOURTH -O RDER CUMULANTS
A. Gaussian Noise Suppression by Higher-Order Cumulants
The principle of Gaussian noise suppression by higher-order
cumulants is as follows. Given a random variable x, its char-
acteristic function is defined as Φ (ω) = E

ejωx 	, it is also
known as the first characteristic function. Then the derivative
of the first characteristic function at the origin is defined as
the moment. The second characteristic function is calculated as
Ψ(ω) = ln Φ(ω). Next, the higher-order cumulants are defined
as the derivatives of the second characteristic function at the
origin. Therefore, the second characteristic function is also
called the cumulant generation function (CGF). Let {x (n)}
be a q order stationary random process with zero mean, then
the qth order cumulant of the process is defined as
cqx (τ1,··· , τq−1)
= cum{x(n), x(n + τ1) ,··· , x(n + τq−1)} . (5)
Namely, the qth-order cumulant of the process {x (n)}
is essentially the qth-order cumulant of the vector
[x(n), x(n + τ1) ,··· , x(n + τq−1)], where x1 = x(n), x2 =
x (n + τ1) ,··· , xq = x (n + τq−1). Note that, the qth-order
cumulant of a qth-order stationary process is only related to
the time lags τ1, τ2,··· , τq−1, and is independent of the time
index n.
For a Gaussian process ξ ∼ N
 
µ, σ2, its characteristic
function is Φξ(ω) = exp

jωµ− 12 ω2σ2	. If µ = 0 , the
characteristic function becomes Φξ(ω) = exp

− 12 ω2σ2	 and
the CGF is Ψξ (ω) = ln Φ ξ (ω) = − (1/2) ω2σ2. According
to the definition, the cumulants of ξ can be given as
cqξ =



0,
σ2,
0,
q = 1
q = 2
q≥ 3
. (6)
It is evident that, the qth-order cumulant of a Gaussian
process will become 0 when q≥ 3. Consequently, higher-
order cumulants can be employed to mitigate the impact of
Gaussian noise. However, as the order of high-order cumulants
increases, the computational complexity of calculating the
high-order cumulant-based quasi-covariance matrix also rises.
Therefore, in practice, third-order or fourth-order cumulants
are commonly utilized. Besides, the third-order cumulants of
certain signals, such as the quadrature amplitude modulation
(QAM) signal, are often found to be 0. Thus, the use of
fourth-order cumulants is more practical. For this reason, the
fourth-order cumulants are used in this paper.
B. F ourth-Order Cumulants of the Received Signals
Given the received signal vector in Eq. (3), its fourth-order
cumulant can be calculated as
c4y (k1, k2, k3; m1, m2, m3, m4) = cum{ym1 (n),
ym2 (n + k1) , y∗m3 (n + k2) , y∗m4 (n + k3)	 , (7)
where mi ∈ {1, 2,··· , M} (i = 1, 2, 3, 4) is the index of
the antennas, ymi denotes the received signal vector on the
mi-th antenna, and kj(j = 1, 2, 3) are the time lags. Following
the works in the array direction finding field [21], [25], [26],
[27], [28], [29], [30], [31], [32], [33], [34], k1 = k2 = k3 = 0
is used, and Eq. (7) is re-written as
c4y (m1, m2, m3, m4)
= cum

ym1 (n), ym2 (n) , y∗m3 (n) , y∗m4 (n)	 . (8)
The fourth-order cumulant in Eq. (8) can then be caculated
as [52]
cum

ym1 (n), ym2 (n) , y∗m3 (n) , y∗m4 (n)	
= E

ym1 (n)ym2 (n) y∗m3 (n) y∗m4 (n)	
− E{ym1 (n)ym2 (n)} E

y∗m3 (n) y∗m4 (n)	
− E

ym1 (n)y∗m3 (n)	 E ym2 (n) y∗m4 (n)	
− E

ym1 (n)y∗m4 (n)	 E ym2 (n) y∗m3 (n)	 . (9)
Substituting Eq. (1) into Eq. (9), the fourth-order cumulant of
the received signals is given as Eq. (10), shown at the bottom
of the next page. In Eq. (10), ami (θ) is the mi-th element of
the steering vector a (θ), and nmi (t) is the mi-th element of
the noise vector.
In the following, the properties of the cumulants will be
used to simplify the calculation of Eq. (10).
Property 1: If random variables xi (i = 1, 2, . . . , k) are
independent of random variables yj (j = 1, 2, . . . , k), then
cum (x1 + y1, x2 + y2,··· , xk + yk)
= cum (x1, x2,··· , xk) + cum (y1, y2,··· , yk) .
Since the signal and the noise are independent of each other,
according to Property 1, Eq. (10) can be split to the cumulants
of signal and noise, given as
c4y (m1, m2, m3, m4)
= cum
 PX
p=1
βpam1 (θp) s (t− τp),
PX
p=1
βpam2 (θp) s (t− τp) ,
PX
p=1
β∗p a∗m3 (θp) s∗ (t− τp),
PX
p=1
β∗p a∗m4 (θp) s∗ (t− τp)
!
+ cum
 
nm1 (t) , nm2 (t) , n∗m3 (t) , n∗m4 (t) . (11)
Note that, the fourth-order cumulant of the Gaussian noise
is zero. Therefore, Eq. (11) equals to
c4y (m1, m2, m3, m4)
= cum
 PX
p=1
βpam1 (θp) s (t− τp),
PX
p=1
βpam2 (θp) s (t− τp),
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

15906 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 23, NO. 11, NOVEMBER 2024
PX
p=1
β∗p a∗m3 (θp) s∗ (t− τp),
PX
p=1
β∗p a∗m4 (θp) s∗ (t− τp)
!
.
(12)
Property 2: Given constants λi (i = 1, 2, . . . , k),
cum (λ1x1, λ2x2,··· , λkxk)
=
 kY
i=1
λi
!
cum (x1, x2,··· , xk) .
According to Property 2 , Eq. (12) can then be calculated
as Eq. (13), shown at the bottom of the page.
Property 3: If a subset of variables {xi} (i = 1, 2, . . . , k)
is independent of the rest, then
cum (x1, x2,··· , xk) = 0.
Note that, signals are transmitted independently through multi-
ple propagation paths. Therefore, according to Property 3, the
cross-path terms in Eq. (13) are zeros. Then, the fourth-order
cumulant of the received signals is further simplified, and
finally we have
c4y (m1, m2, m3, m4)
=
PX
p=1
am1 (θp) am1 (θp) a∗m3 (θp) a∗m4 (θp) γ4sp , (14)
where
γ4sp = cum (βps (t− τp) , βps (t− τp) ,
β∗p s∗ (t− τp) , β∗p s∗ (t− τp)
represents the fourth-order cumulant of the signal through the
p-th path. By altering the antenna index m1, m2, m3 and m4,
M 4 fourth-order cumulants can be obtained, which can then
be organized to form a quasi-covariance matrix. The newly
formed covariance matrix, denoted by R4, is an M 2× M 2
matrix. Its (( m1-1)M + m2,(m3-1)M + m4)-th element is
c4y (m1, m2, m3, m4), given as [29]
R4 ((m1− 1) M + m2, (m3− 1) M + m4)
= c4y (m1, m2, m3, m4) . (15)
Therefore, we have
R4 = E
n
(y⊗ y) (y⊗ y)H
o
− E{y⊗ y} E
n
(y⊗ y)H
o
− E

yyH 	⊗ E yyH 	
= B (θ) R4SBH (θ) , (16)
where B (θ) = [ b (θ1),··· , b (θP )] is the virtual array
manifold matrix, and b (θi) = a (θi)⊗ a (θi). R4S is the
fourth-order cumulant quasi-covariance matrix of the trans-
mitted signal.
With K-length samples, R4 in Eq. (16) is approximated by
ˆR4 =
KX
k=1
(y (k)⊗ y (k)) (y (k)⊗ y (k))H
−
KX
k=1
(y (k)⊗ y (k))
KX
k=1
(y (k)⊗ y (k))H
−
KX
k=1
 
y (k) yH (k)⊗ KX
k=1
 
y (k) yH (k), (17)
where y (k) denotes the k-th sample of the received signal vec-
tor y (t). Perform eigen-decomposition on the approximated
quasi-covariance matrix ˆR4, and then we have
ˆR4 = UΣUH , (18)
where Σ∈ CM 2×M 2 is a diagonal matrix composed of the
eigenvalues in descending order. With steps similar to the
MUSIC algorithm, the signal subspace and noise subspace can
be separated. Namely, the eigenvectors corresponding to the
largest P eigenvalues will form the signal sub-space Us, while
the rest of the eigenvectors will form the noise sub-space Un.
Actually, the signal subspace Us formed by the eigenvectors
is the same subspace represented by the virtual steering vector
B (θ). Therefore, the angular spectrum of the signal subspace
can be given as
Spec (θ) = 1bH (θ) UnUHn b (θ) . (19)
By searching the peaks of Eq. (19), the estimates of the DOAs
can then be obtained.
As described in Section III, the DOA estimation is based on
the quasi-covariance matrix R4. Therefore, the steering vector
of the virtual array is
b (θ) = a (θ)⊗ a (θ) .
(20)
c4y (m1, m2, m3, m4)= cum
 PX
p=1
βpam1 (θp) s (t− τp) + nm1 (t),
PX
p=1
βpam2 (θp) s (t− τp) + nm2 (t),
PX
p=1
β∗p a∗m3 (θp) s∗ (t− τp) + n∗m3 (t),
PX
p=1
β∗p a∗m4 (θp) s∗ (t− τp) + n∗m4 (t)
!
, (10)
c4y (m1, m2, m3, m4) =
PX
p1=1
PX
p2=1
PX
p3=1
PX
p4=1
am1 (θp1 ) am1 (θp2 ) a∗m3 (θp3 ) a∗m4 (θp4 )cum (βp1 s (t− τp1 ) ,
βp2 s (t− τp2 ) , β∗p3 s∗ (t− τp3 ) , β∗p4 s∗ (t− τp4 ) . (13)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

PENG et al.: UNDER-DETERMINED DOA ESTIMATION 15907
Fig. 1. The flowchart of the proposed DOA estimation method.
Substitutting Eq. (2) into Eq. (20), we have Eq. (21), shown
at the bottom of the page.
C. Analysis on the Complexity of the Proposed DOA
Estimation Method
In this subsection, the computational complexity of the
proposed DOA estimation method will be analyzed and com-
pared with the traditional method. The step-by-step process
of the proposed DOA estimation method is summarized as
follows: Firstly, input K samples of the received signal vector.
Then, the approximation of the fourth-order cumulant quasi-
covariance matrix ˆR4 is calculated according to Eq. (17).
Next, perform the eigenvalue decomposition on ˆR4 following
Eq. (18). Finally, the signal subspace and the noise subspace
are separated, and the angular spectrum is then calculated
according to Eq. (19). The flowchart of the proposed DOA
estimation method is presented in Fig. 1.
According to Eq. (17), in order to calculate the M 2×
M 2 fourth-order cumulant quasi-covariance matrix ˆR4, M 4K
multiplications are required. And the computational complex-
ity of the eigen-decomposition of ˆR4 isO  M 6. Furthermore,
the computational complexity of calculating the angular spec-
trum at every angle value is O
 
M 4 Therefore, the total
TABLE II
COMPUTATIONAL COMPLEXITY OF THE PROPOESD AND
TRADITINOAL METHODS
computational complexity of the proposed DOA estimation
method can be obtained as O
 
M 6 + M 4K.
For comparison, taking the MUSIC algorithm as a rep-
resentative of the traditional DOA estimation methods,
the computational complexity of the MUSIC algorithm is
evaluated as follows. The complexity of calculating the
second-order statistics covariance matrix is O
 
M 2K. The
eigen-decomposition of the M × M covariance matrix is
O
 
M 3. When searching the angular spectrum, the compu-
tational complexity can be seen as O
 
M 2. In summary,
the computational complexity of the MUSIC algorithm is
O
 
M 3 + M 2K. The computational complexity comparison
between the proposed method and the traditional MUSIC
method is presented in Table II.
It is clear that, with the same number of antennas, the
proposed DOA estimation method has a higher computational
complexity than the traditional second-order statistic-based
methods. However, it is important to highlight that when
the non-uniform array structure is adopted, the proposed
method can take a much smaller number of antennas than
the traditional methods. Moreover, the proposed method is
robust to Gaussian noise, and has better angular resolution
and estimation accuracy than the traditional methods.
IV. A NALYSIS OF VIRTUAL ANTENNAS AND
ARRAY EXPANSION
Take a ULA with 4 antennas as an example. Since d = 0 d 2d 3d T , the steering vector corresponding to the virtual
array is given in Eq. (22), shown at the bottom of the page.
b (θ) =
h
e−j2π 0λ sin(θ), e−j2π d1λ sin(θ),··· , e−j2π dM−1λ sin(θ),··· ,
e−j2π
dM−1 +0
λ sin(θ), e−j2π
dM−1 +d1
λ sin(θ),··· , e−j2π
dM−1 +dM−1
λ sin(θ)
iT
. (21)
bU LA=
h
e−j2π 0λ sin(θ) , e−j2π dλ sin(θ), e−j2π 2dλ sin(θ), e−j2π 3dλ sin(θ),
e−j2π dλ sin(θ), e−j2π 2dλ sin(θ), e−j2π 3dλ sin(θ), e−j2π 4dλ sin(θ),
e−j2π 2dλ sin(θ), e−j2π 3dλ sin(θ), e−j2π 4dλ sin(θ), e−j2π 5dλ sin(θ),
e−j2π 3dλ sin(θ), e−j2π 4dλ sin(θ), e−j2π 5dλ sin(θ), e−j2π 6dλ sin(θ)iT . (22)
bN U LA=
h
e−j2π 0λ sin(θ) ,e−j2π dλ sin(θ), e−j2π 4dλ sin(θ), e−j2π 6dλ sin(θ),
e−j2π dλ sin(θ), e−j2π 2dλ sin(θ), e−j2π 5dλ sin(θ), e−j2π 7dλ sin(θ),
e−j2π 4dλ sin(θ), e−j2π 5dλ sin(θ), e−j2π 8dλ sin(θ), e−j2π 10dλ sin(θ),
e−j2π 6dλ sin(θ), e−j2π 7dλ sin(θ), e−j2π 10dλ sin(θ), e−j2π 12dλ sin(θ)iT . (23)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

15908 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 23, NO. 11, NOVEMBER 2024
Fig. 2. The virtually expanded array of the four-antenna ULA.
Observing Eq. (22), it is found that, the original
4-dimensional array manifold is expanded to a 16-dimensional
one. Meanwhile, there are 9 repeating elements in the vector,
and only 7 elements are non-repeating, as marked in red in
Eq. (22). Furthermore, comparing the virtual steering vector
with the original one, it is found that the last three items in
the vector, namely, ej2π 4dλ sin(θ), ej2π 5dλ sin(θ) and ej2π 6dλ sin(θ)
are newly added. They can be treated as the virtual antennas
placed at 4d, 5d and 6d, respectively. Therefore, the 4-antenna
array is virtually expanded to a 7-antenna array, as shown in
Fig. 2.
Actually, an M-antenna ULA will have M− 1 virtual
antennas by using the fourth-order cumulants. As a result,
the expanded virtual antenna array has 2M− 1 elements in
total. However, the virtual array manifold has M 2 elements.
Therefore, the ULA structure is inefficient in array expansion,
which limits the DOA estimation capability.
In order to make better use of the array expansion property
of the fourth-order cumulants, a non-uniform array structure is
considered in this paper. Although the non-uniform array may
take a larger space, its virtual array will have more antennas
than the uniform array without additional hardware cost.
Therefore, the non-uniform array will be a more economical
solution if the space condition permits.
Similarly, consider a four-antenna NULA as the example.
Suppose the antennas are placed at
dN U LA=
 0 d 4d 6d T .
Its virtual steering vector is given in Eq. (23), shown at the
bottom of the previous page. Now, it is observed that there are
10 non-repeating elements in Eq. (23). Namely, the expanded
virtual array has 10 antennas, and 6 of them are newly added,
as shown in Fig. 3.
According to Eq. (21), if the M 2 elements in the steering
vector are arranged into an M× M matrix, then it is diago-
nally symmetric. For a ULA, all the non-repeating elements
included are in the top row and the right column. However,
for a NULA, the elements in the upper triangular matrix can
be different from each other if the array structure is properly
designed. Namely, there can be M (M + 1) /2 antennas in the
expanded virtual array.
It is worth mentioning that, although its degrees of freedom
(DoF) can be as large as M (M + 1) /2, the computational
complexity of the proposed method increases rapidly with M
as discussed in Section III-C. Therefore, the proposed method
is more practical in the under-determined scenario with a
small or moderate number of antennas. Otherwise, the works
in [47] and [48] can be applied. Actually, the uDoF lower
bounds of the methods in [47] and [48] are 2M 2/3 and M 2/2,
respectively.
V. N ON-UNIFORM ARRAY STRUCTURE OPTIMIZATION
As analyzed in Section IV, when using the fourth-order
cumulant, the antenna array can be expanded to a virtual array
that has more antennas. The number of virtual antennas is
determined by the array structure. Therefore, the non-uniform
array has to be carefully designed so that the array can
be expanded to the most extent. This section considers the
optimization of both linear and non-linear non-uniform array
structure. When the linear array is considered, the NULA
structure optimization can be formulated as a mixed integer
linear programming problem. For the purpose to save space,
the non-uniform planar array (NUPA) is also considered
and formulated as a general non-linear integer programming
problem. The principle of the array structure optimization is
described as follows.
Suppose that a planar array with M antennas is placed on
the X-Y plane, and the coordinate of the m-th antenna is
(dxm, dym). It is assumed that dx1≤ dx2≤···≤ dxM , and
dy1≤ dy2≤···≤ dyM . Define matrix D∈ N2×M as
D =
 dx1
dy1
··· dxM
dyM

and matrix Q∈ Z(M−1)×M as
Q =


−1 1
−1 1
...
−1 1


where the unmarked elements are 0. Then, to ensure that every
antenna has a different position, we have
QDT r̸=0. (24)
where
r
̸= denotes the row-by-row inequality.
Let U = M (M− 1) /2, and define matrix J∈ ZU×M as
J =

JT1 JT2 ··· JTM−1 T , (25)
where Ji ∈ Z(M−i)×M =  0M−i,i−1 1M−i IM−i , i =
1,··· , M− 1. 0M−i,i−1 ∈ Z(M−i)×(i−1) is consisting
of all 0 elements, 1M−i denotes an (M− i)-dimensional
column vector with all 1 elements, and IM−i is an (M− i)-
dimensional unit matrix. Then the product JDT can be used to
represent the positions of all the possible antennas. Therefore,
the following constraint should be satisfied to ensure that the
virtual antennas will have different positions.
1U−1j(u)DT r̸=J[u]DT , u = 1,··· , U (26)
where 1U−1 denotes a (U− 1)-dimensional column vector
with all 1 elements, j(u) represents the u-th row of matrix J,
and J[u] denotes the remnant of matrix J after removing the
u-th row.
Thus, with the objective to obtain the most virtual antennas
while minimizing the space occupied by the antenna array, the
NUPA structure optimization can be formulated as a nonlinear
integer programming problem, given as
min
D∈Z+
max (dxm + dym )
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

PENG et al.: UNDER-DETERMINED DOA ESTIMATION 15909
Fig. 3. The virtually expanded array of the four-antenna NULA.
Fig. 4. Six-antenna NULA.
Fig. 5. Six-antenna NUPA.
s.t. QDT r̸=0,
j(u)A DT r̸=j(u)B DT u = 1, . . . , U(U− 1) , (27)
where max (dxm + dym) denotes the space taken by
antenna m. JA =

1U−1j(1),··· , 1U−1j(U ) T , JB =
J[1],··· , J[U ] T . j(u)A and j(u)B are u-th row of matrix JA
and JB, respectively.
Actually, the problem in Eq. (27) is very complicated.
Instead of solving Eq. (27), the original problem is relaxed
in order to obtain a fast solution, as described in Appendix .
The optimization problem after relaxation can be written as
Eq. (28), shown at the bottom of the next page. In Eq. (28),
INF is a reasonably large number, zm and z′u are binary
varible vectors. m = 1,··· ,M− 1, u=1,··· ,U (U− 1). The
re-formulated problem in Eq. (28) can then be solved by
MATLAB using the CVX toolbox.
When the linear array is considered, the structure opti-
mization can be obtained similarly by changing the two-
dimensional coordinates into one-dimensional coordinates.
It is clear that the solution of the problem is not unique,
and the decision can be made according to other conditions.
As an example, when a six-antenna array is used, the NUPA
and NULA are designed, and their structures are shown in
Fig. 5 and Fig. 4, respectively.
VI. S IMULATION RESULTS
In this section, some representative simulation results
will be shown to verify the effectiveness of the proposed
TABLE III
DESCRIPTION OF SIMULATION EXPERIMENTS
under-determined DOA estimation method based on the
fourth-order cumulants and non-uniform antenna array. A
6-antenna NULA is used as an example. The 6 antennas are
placed at dN U LA=
 0 2d 8d 13d 17d 20d T , as shown in
Fig. 4. The ULA structure is also used for comparison, and
dU LA=
 0 d 2d 3d 4d 5d T .
The center frequency of the signal is 3.5G Hz, the band-
width is 100M Hz, and the frequency interval is 30k Hz.
The maximum number of propagation paths is set to be 20,
of which the DOAs uniformly distribute within [−64◦, +64◦],
and the corresponding path delays evenly value from 10 ns to
200 ns.
The following experiments will be carried out, as listed in
Table III.
A. Experiment I: The Ability of A WGN Suppression
One advantage of our proposed method is the ability to
suppress the Gaussian noise. In order to testify this ability,
the number of propagation paths is set to 4, which is less than
the number of antennas. Therefore, the effect of multi-path
interference can be ignored. The fourth-order cumulants are
used in combination with the ULA and NULA, respectively.
We calculate the rate of success γSU Cand root mean square
error (RMSE), which are respectively defined as follows :
γSU C=
I
ˆθi− θi≤ ε, i= 1,··· , P
IP (29)
RM SE= 1IP
vuut IX
i=1
PX
p=1

ˆθi− θi
2
(30)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

15910 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 23, NO. 11, NOVEMBER 2024
Fig. 6. The ability of Gaussian noise suppression. (a) γSU Cfor ULA. (b) γSU Cfor NULA.
Fig. 7. The ability of AOA detection. (a) Angular Spectrum for ULA. (b) Estimated AOAs v.s. true AOAs for ULA. (c) Angular Spectrum for NULA.
(d) Estimated AOAs v.s. true AOAs for NULA.
where I indicates the number of Monte-Carlo runs, which
is set to 10000 in our experiment. P indicates the number of
propagation paths. I
ˆθi− θi≤ ε, i= 1,··· , P is the times
of accurate estimation for θ. And ε is the pre-defined threshold,
which is set to be 2 ◦ in our experiment.
The simulation results are shown in Fig. 6. In Fig. 6(a),
the ULA structure is used, and the proposed fourth-order
cumulant-based algorithm (denoted as 4C-ULA) is com-
pared with the traditional second-order statistics (denoted as
S-ULA). Then, the NULA is used, as shown in Fig. 6(b). It is
clear that, by using the fourth-order cumulants, the AWGN
noise can be effectively suppressed. In the low SNR region,
an obvious improvement of γSU Ccan be observed by using the
4C-ULA/NULA. In addition, the NULA structure also leads to
performance improvement, which benefits from the additional
degrees of freedom of the virtual antennas.
B. Experiment II: The Ability of AOA Detection
Another advantage of our proposed method is the ability
of DOA estimation in the existence of a large number of
propagation paths which is greater than M and less than
or equal to M (M + 1) /2− 1. To testify this ability, the
min
D∈Z+,zm,z′ u∈{0,1},∀m,∀udxM + dyM
s.t. 1− INF· zm≤ q(m)DT≤− 1 + INF· (1− zm)
1− INF· z′u≤ sum j(u)A − j(u)B  DT≤− 1 + INF· (1− z′u) (28)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

PENG et al.: UNDER-DETERMINED DOA ESTIMATION 15911
Fig. 8. The rate of success and RMSE for 9 paths. (a) γSU C. (b) RMSE.
Fig. 9. The rate of success and RMSE for 20 paths. (a) γSU C. (b) RMSE.
Fig. 10. Energy performance of the paths estimated at 5 dB. (a) ULA, 9 paths. (b) NULA, 9 paths. (c) ULA, 20 paths. (d) NULA, 20 paths.
AWGN is removed so that we can focus on the effect of
the multiple paths. The number of paths is set to 20 in this
experiment. The angular spectrum is calculated by Eq. (19),
and then the DOAs are obtained by searching for the peaks
in the angular spectrum. The simulation results are shown in
Fig. 7. It can be observed that, by using the ULA structure,
the angular spectrum has smooth peaks. As a result, there are
large differences between the estimated AOAs and their true
values. By contrast, using the fourth-cumulants and NULA,
the proposed DOA estimation method yields very sharp peaks
in the angular spectrum, and the estimated AOAs are almost
the same as their true values.
C. Experiment III: Effect of the Number of Paths
It should be noted that, the number of propagation paths
vary in different scenarios. In this experiment, we use a
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

15912 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 23, NO. 11, NOVEMBER 2024
Fig. 11. Effect of the sampling length. (a) γSU C. (b) RMSE.
6 antenna array to study the rate of success as well as the
RMSE of the proposed DOA estimation method in under-
determined scenarios. The path numbers are set to be 9 and 20,
and their corresponding results are shown in Fig. 8 and Fig. 9,
respectively. The ULA structure (denoted by 4C-ULA) and
the NULA structure (denoted by 4C-NULA) are used. In fact,
the NULA can be replaced by the NUPA as well. In addi-
tion, the performance of the convolutional neural network
(CNN) and NULA-based DOA estimation method (denoted by
CNN-NULA) [20] is also presented for comparison.
It is observed that, as expected, when the number of paths
increases from 9 to 20, both the rate of success γSU Cand the
RMSE degrade, which is due to the closer peaks in the angular
spectrum. However, even in the extreme under-determined
scenario with 20 paths, the γSU C with 4C-NULA can still
be as high as 0.92 at SNR =0 dB. It is also observed that,
the performance of the CNN-NULA is clearly inferior to the
proposed method. Here we attempt to give an explanation. The
possible reasons might be twofold. On one hand, the proposed
method is more powerful due to the AWGN suppression
provided by fourth-order cumulants. On the other hand, the
antenna array has been utilized to the maximum extent by
the proposed non-uniform optimization method. Therefore, our
proposed method, which is model driven, outperforms the data
driven deep learning-based method.
D. Experiment IV: Effect of the Sampling Length
As we know, the proposed method is based on the fourth-
order cumulants. Its performance depends on the proximity
between the sampled statistical characteristic and actual one.
The effect of the sampling length is presented in Fig. 11. It is
shown that, a certain length, e.g. K=300, is required to achieve
a promising estimation.
VII. C ONCLUSION
In this paper, an under-determined DOA estimation method
based on the fourth-order cumulants and non-uniform antenna
array has been proposed. The fourth-order cumulants have
been employed to effectively suppress the AWGN, and expand
the antenna array by the virtual antennas. In order to fur-
ther expand the antenna array, a non-uniform antenna array
structure has been adopted, with the number of virtual
antennas in the expanded array being optimized. Conse-
quently, the proposed method is capable of detecting at
most M (M + 1) /2− 1 incoming wave directions using an
M-antenna non-uniform array. The effectiveness of the pro-
posed DOA estimation method has been validated through
simulation results. It has been demonstrated that, the proposed
DOA estimation method can be applied in under-determined
scenarios, while having significantly better performance com-
pared to existing methods, and accurate estimation can be
achieved, even in the low SNR region.
APPENDIX
[Relaxation of the optimation problem in Eq. (27)] In the
next, the optimization problem in Eq. (27) will be relaxed to
obtain a quick solution. To satisfy the constraint
QDT r̸=0,
we have (dxi , dyi ) ̸=
 
dxj , dyj

,∀i ̸= j. To simplify the
problem, we relax the condition to be dxi̸= dxj &dyi̸= dyj ,
∀i̸= j. Remember that (dxm , dym ) denotes the coordinate of
the m-th antenna on the X-Y plane. dxm and dym are positive
and the constraint QDT r̸=0 is relaxed as
 dxi− dxj ≥ 1dyi− dyj ≥ 1 ,∀i̸= j, i, j∈{ 1,··· , M} (31)
By defining a reasonably large number INF and a binary
variable z, the inequality in (31) can be re-formed as
1− INF· z≤ dxi− dxj≤− 1 + INF· (1− z) ,
∀i̸= j, i, j∈{ 1, . . . , M} (32)
1− INF· z≤ dyi− dyj≤− 1 + INF· (1− z) ,
∀i̸= j, i, j∈{ 1, . . . , M} (33)
Then, the vector form of the constraint QDT r̸=0 after the
relaxation is given as
1− INF· zm≤ q(m)DT≤− 1 + INF· (1− zm)
m = 1,··· , M− 1 (34)
where q(m) denotes the m-th row of Q and zm denotes the
2× 1 binary vector.
To satisfy the constraint
1U−1j(u)DT r̸=J[u]DT u = 1,··· , U
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

PENG et al.: UNDER-DETERMINED DOA ESTIMATION 15913
virtual antennas in the expanded array should be in different
positions. To simplify the solution, this constraint is relaxed
as
sum

j(u)A − j(u)B

DT

̸= 0, (35)
where sum (·) denotes the sum operation of the 2D coor-
dinates. Since the coordinates of the virtual antennas are
integers, the inequality in (35) can similarly be re-formed as
1− INF· zu≤ sum

j(u)A − j(u)B

DT

≤− 1 + INF· (1− zu)
u= 1,··· ,U (U− 1) (36)
Substituting (34) and (36) into Eq. (27), the relaxed opti-
mization problem in Eq. (28) is then obtained.
REFERENCES
[1] Z. Chen, G. Gokeda, and Y . Yu, Introduction to Direction-of-Arrival
Estimation. Norwood, MA, USA: Artech House, 2010.
[2] D. Zhu, J. Choi, and R. W. Heath, “Auxiliary beam pair enabled AoD
and AoA estimation in closed-loop large-scale millimeter-wave MIMO
systems,” IEEE Trans. Wireless Commun., vol. 16, no. 7, pp. 4770–4785,
Jul. 2017.
[3] H. Jiang et al., “A novel 3D UA V channel model for A2G communi-
cation environments using AoD and AoA estimation algorithms,” IEEE
Trans. Commun., vol. 68, no. 11, pp. 7232–7246, Nov. 2020.
[4] Y . Hu, T. D. Abhayapala, and P. N. Samarasinghe, “Multiple source
direction of arrival estimations using relative sound pressure based
MUSIC,” IEEE/ACM Trans. Audio, Speech, Language Process. , vol. 29,
pp. 253–264, Jul. 2021.
[5] X. Wang, L. Wan, M. Huang, C. Shen, Z. Han, and T. Zhu, “Low-
complexity channel estimation for circular and noncircular signals
in virtual MIMO vehicle communication systems,” IEEE Trans. V eh.
Technol., vol. 69, no. 4, pp. 3916–3928, Apr. 2020.
[6] U. M. Butt, S. A. Khan, A. Ullah, A. Khaliq, P. Reviriego, and A. Zahir,
“Towards low latency and resource-efficient FPGA implementations of
the MUSIC algorithm for direction of arrival estimation,” IEEE Trans.
Circuits Syst. I, Reg. Papers , vol. 68, no. 8, pp. 3351–3362, Aug. 2021.
[7] D. H. Johnson, “The application of spectral estimation methods to bear-
ing estimation problems,” Proc. IEEE , vol. 70, no. 9, pp. 1018–1028,
Sep. 1982.
[8] V . Vasylyshyn and V . Martynova, “DOA estimation by root-min-norm
using power basis and persymmetric covariance matrix,” in Proc. IEEE
Ukrainian Microw. Week, Sep. 2020, pp. 1–4.
[9] A. Naceur and K. Ali, “Direction-of-arrival estimation with new versions
of min-norm algorithm based on Nystram method,” in Proc. Int. Conf.
Image Signal Process. Appl. (ISPA) , May 2022, pp. 1–5.
[10] J. Pan, M. Sun, Y . Wang, and X. Zhang, “An enhanced spatial
smoothing technique with ESPRIT algorithm for direction of arrival
estimation in coherent scenarios,” IEEE Trans. Signal Process. , vol. 68,
pp. 3635–3643, 2020.
[11] K. Ardah, S. Gherekhloo, A. L. F. de Almeida, and M. Haardt, “TRICE:
A channel estimation framework for RIS-aided millimeter-wave MIMO
systems,” IEEE Signal Process. Lett. , vol. 28, pp. 513–517, 2021.
[12] J. Zhang, D. Rakhimov, and M. Haardt, “Gridless channel estimation
for hybrid mmWave MIMO systems via tensor-ESPRIT algorithms in
DFT beamspace,” IEEE J. Sel. Topics Signal Process. , vol. 15, no. 3,
pp. 816–831, Apr. 2021.
[13] B. Jo, F. Zotter, and J.-W. Choi, “Extended vector-based EB-ESPRIT
method,” IEEE/ACM Trans. Audio, Speech, Language Process. , vol. 28,
no. 1, pp. 1692–1705, Oct. 2020.
[14] Y . Fang, S. Zhu, Y . Gao, L. Lan, C. Zeng, and Z. Liu, “Direction-of-
arrival estimation of coherent signals for uniform linear antenna arrays
with mutual coupling in unknown nonuniform noise,” IEEE Trans. V eh.
Technol., vol. 71, no. 2, pp. 1656–1668, Feb. 2022.
[15] A. Wang, R. Yin, and C. Zhong, “PCA-based channel estimation
and tracking for massive MIMO systems with uniform rectangular
arrays,” IEEE Trans. Wireless Commun., vol. 19, no. 10, pp. 6786–6797,
Oct. 2020.
[16] W.-X. Long, R. Chen, M. Moretti, and J. Li, “AoA estimation for
OAM communication systems with mode-frequency multi-time ESPRIT
method,” IEEE Trans. V eh. Technol. , vol. 70, no. 5, pp. 5094–5098,
May 2021.
[17] S. Feintuch, J. Tabrikian, I. Bilik, and H. Permuter, “Neural network-
based DOA estimation in the presence of non-Gaussian interference,”
IEEE Trans. Aerosp. Electron. Syst. , vol. 60, no. 1, pp. 1–30, Feb. 2023.
[18] D. Hu, Y . Zhang, L. He, and J. Wu, “Low-complexity deep-learning-
based DOA estimation for hybrid massive MIMO systems with uniform
circular arrays,” IEEE Wireless Commun. Lett. , vol. 9, no. 1, pp. 83–86,
Jan. 2020.
[19] M. Chen, Y . Gong, and X. Mao, “Deep neural network for estima-
tion of direction of arrival with antenna array,” IEEE Access , vol. 8,
pp. 140688–140698, 2020.
[20] X. Wu, X. Yang, X. Jia, and F. Tian, “A gridless DOA estimation method
based on convolutional neural network with Toeplitz prior,” IEEE Signal
Process. Lett., vol. 29, pp. 1247–1251, 2022.
[21] B. Porat and B. Friedlander, “Direction finding algorithms based on
high-order statistics,” IEEE Trans. Signal Process. , vol. 39, no. 9,
pp. 2016–2024, Sep. 1991.
[22] M. Barat, M. Karimi, and M. A. Masnadi-Shirazi, “High-order maximum
likelihood methods for direction of arrival estimation,” IEEE Open
J. Signal Process. , vol. 2, pp. 359–369, 2021.
[23] Z. Chen, Y . Jiang, D. Xiong, and S. Ren, “Underdetermined DOA
estimation of non-circular sources exploiting generalized qth-order dif-
ference and sum co-array concept,” in Proc. 4th Int. Conf. Inf. Commun.
Signal Process. (ICICSP) , Sep. 2021, pp. 36–40.
[24] M. Yang, G. Guo, Y . Huang, and Y . Sun, “DOA estimation algorithm
based on extension and shift of sparse polarization sensitive array,”
in Proc. 7th Int. Conf. Signal Image Process. (ICSIP) , Jul. 2022,
pp. 116–120.
[25] U. Sharma and M. Agrawal, “Fourth-order cumulants based underdeter-
mined 2-D DOA estimation using single A VS,” in Proc. Global Oceans
Singap., Oct. 2020, pp. 1–6.
[26] C. Liu, Z. Ye, and Y . Zhang, “DOA estimation based on fourth-order
cumulants with unknown mutual coupling,” Signal Process. , vol. 89,
no. 9, pp. 1839–1843, Sep. 2009.
[27] R. Jiang, “A high-efficient algorithm for DOA estimation,” in Proc. 10th
Int. Comput. Conf. Wavelet Act. Media Technol. Inf. Process. , Dec. 2013,
pp. 126–130.
[28] M. Muhammad, M. Li, Q. H. Abbasi, C. Goh, and M. Imran, “Direction
of arrival estimation using hybrid spatial cross-cumulants and root-
MUSIC,” in Proc. 14th Eur . Conf. Antennas Propag. , Mar. 2020,
pp. 1–5.
[29] G. Prabha and G. Shanmugha Sundaram, “Estimation of DOA using a
cumulant based quadricovariance matrix,” in Proc. Eur . Conf. Antennas
Propag., Apr. 2016, pp. 1–5.
[30] J. Liang, “Joint azimuth and elevation direction finding using cumulant,”
IEEE Sensors J. , vol. 9, no. 4, pp. 390–398, Apr. 2009.
[31] X. Dingjie, L. Moxuan, W. Wei, and W. Xianpeng, “Joint DOD and
DOA angle estimation of coherent targets for bistatic MIMO radar,”
in Proc. 3rd Int. Conf. Instrum., Meas., Comput., Commun. Control ,
Sep. 2013, pp. 1025–1028.
[32] Z. Zheng, M. Fu, D. Jiang, W.-Q. Wang, and S. Zhang, “Localization of
mixed far-field and near-field sources via cumulant matrix reconstruc-
tion,” IEEE Sensors J. , vol. 18, no. 18, pp. 7671–7680, Sep. 2018.
[33] L. Haomiao, M. Hongguang, L. Zhiqiang, and X. Donghui, “An
ESPRIT-like algorithm for angle estimation in bistatic MIMO radar,”
in Proc. IEEE Int. Conf. Signal Process., Commun. Comput. (ICSPCC) ,
Sep. 2015, pp. 1–4.
[34] X. Li, Q. Gong, S. Zhong, and S. Ren, “Near-field noncircular sources
localization based on fourth-order cumulant,” IEEE Access , vol. 8,
pp. 120575–120585, 2020.
[35] A. Ahmed, M. F. Khan, and M. Tufail, “Multiple invariance cumulant
ESPRIT for DOA estimation,” in Proc. Int. Conf. Robot. Emerg. Allied
Technol. Eng., Apr. 2014, pp. 157–159.
[36] A. Moffet, “Minimum-redundancy linear arrays,” IEEE Trans. Antennas
Propag., vols. AP-16, no. 2, pp. 172–175, Mar. 1968.
[37] M. Wagner, Y . Park, and P. Gerstoft, “Gridless DOA estimation and root-
MUSIC for non-uniform linear arrays,” IEEE Trans. Signal Process. ,
vol. 69, pp. 2144–2157, 2021.
[38] L. Zhou, K. Ye, J. Qi, and H. Sun, “DOA estimation based on pseudo-
noise subspace for relocating enhanced nested array,” IEEE Signal
Process. Lett., vol. 29, pp. 1858–1862, 2022.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply. 

15914 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 23, NO. 11, NOVEMBER 2024
[39] Y . Tian and H. Xu, “Calibration nested arrays for underdetermined DOA
estimation using fourth-order cumulant,” IEEE Commun. Lett. , vol. 24,
no. 9, pp. 1949–1952, Sep. 2020.
[40] S. Ren, W. Dong, X. Li, W. Wang, and X. Li, “Extended nested arrays for
consecutive virtual aperture enhancement,” IEEE Signal Process. Lett. ,
vol. 27, pp. 575–579, 2020.
[41] Y . Zhou, Y . Li, L. Wang, C. Wen, and W. Nie, “The compressed nested
array for underdetermined DOA estimation by fourth-order difference
coarrays,” in Proc. IEEE Int. Conf. Acoust., Speech Signal Process.
(ICASSP), May 2020, pp. 4617–4621.
[42] T. Li, P. Han, G. Zhou, and X. Yao, “A joint processing-MUSIC
algorithm in multipath environment based on non-uniform line array,”
in Proc. 13th Int. Congr . Image Signal Process., Biomed. Eng. Informat.
(CISP-BMEI), Oct. 2020, pp. 495–500.
[43] X. Huang, X. Yang, L. Cao, and W. Lu, “Pseudo noise subspace based
DOA estimation for unfolded coprime linear arrays,” IEEE Wireless
Commun. Lett. , vol. 10, no. 11, pp. 2335–2339, Nov. 2021.
[44] S. Liu, Z. Mao, Y . D. Zhang, and Y . Huang, “Rank minimization-based
Toeplitz reconstruction for DoA estimation using coprime array,” IEEE
Commun. Lett. , vol. 25, no. 7, pp. 2265–2269, Jul. 2021.
[45] Z. Fu, P. Chargé, and Y . Wang, “Fourth order cumulant based active
direction of arrival estimation using coprime arrays,” in Proc. IEEE
Int. Conf. Acoust., Speech Signal Process. (ICASSP) , May 2020,
pp. 4547–4551.
[46] A. Ahmed and Y . D. Zhang, “Generalized non-redundant sparse array
designs,” IEEE Trans. Signal Process. , vol. 69, pp. 4580–4594, 2021.
[47] W. Shi, S. A. V orobyov, and Y . Li, “ULA fitting for sparse array design,”
IEEE Trans. Signal Process. , vol. 69, pp. 6431–6447, 2021.
[48] W. Shi and Y . Li, “Improved uniform linear array fitting scheme
with increased lower bound on uniform degrees of freedom for DOA
estimation,” IEEE Trans. Instrum. Meas. , vol. 71, pp. 1–14, 2022.
[49] S. Zhang, S. Zhang, F. Gao, J. Ma, and O. A. Dobre, “Deep learning
optimized sparse antenna activation for reconfigurable intelligent sur-
face assisted communication,” IEEE Trans. Commun. , vol. 69, no. 10,
pp. 6691–6705, Oct. 2021.
[50] B. Lin, F. Gao, S. Zhang, T. Zhou, and A. Alkhateeb, “Deep
learning-based antenna selection and CSI extrapolation in massive
MIMO systems,” IEEE Trans. Wireless Commun. , vol. 20, no. 11,
pp. 7669–7681, Nov. 2021.
[51] W. Peng, W. Li, W. Wang, X. Wei, and T. Jiang, “Downlink channel
prediction for time-varying FDD massive MIMO systems,” IEEE J. Sel.
Topics Signal Process. , vol. 13, no. 5, pp. 1090–1102, Sep. 2019.
[52] M. C. Dogan and J. M. Mendel, “Applications of cumulants to array
processing. I. Aperture extension and array calibration,” IEEE Trans.
Signal Process., vol. 43, no. 5, pp. 1200–1216, May 1995.
Wei Peng (Senior Member, IEEE) received the
Ph.D. degree in wireless communications from The
University of Hong Kong in 2007. She was a
Post-Doctoral Research Fellow with Tohoku Uni-
versity, Japan, from 2008 to 2009, where she was
an Assistant Professor from 2009 to 2013. She held
a visiting position with Columbia University, USA,
in 2012. Since 2013, she has been with Huazhong
University of Science and Technology, China, where
she is currently a Professor. Her research interests
include signal processing for large-scale wireless
communication systems, online learning-based network optimization, and
space-ground integrated networks.
Peng Li received the bachelor’s degree in communi-
cation engineering from the University of Electronic
Science and Technology of China (UESTC) in
2019 and the master’s degree in communication
engineering from Huazhong University of Science
and Technology (HUST) in 2022. His research inter-
ests include wireless communications, with a focus
on massive MIMO systems, channel estimation, arti-
ficial intelligence, and deep learning.
Xinyi Wu received the bachelor’s degree in elec-
tromagnetic field and wireless technology and the
master’s degree in information and communication
engineering from the School of Electronics Informa-
tion and Communications, Huazhong University of
Science and Technology, China, in 2021 and 2024,
respectively. Her research interests include wireless
communications, with a focus on massive MIMO
systems, channel parameter estimation, and physical
layer security.
Kai Luo (Member, IEEE) received the B.S. degree
from the School of Electronics Information and
Communications, Huazhong University of Science
and Technology, Wuhan, China, in 2006, and the
Ph.D. degree from the Department of Electrical and
Electronic Engineering, Imperial College London,
U.K., in 2013. From 2013 to 2014, he was a
Research Associate with the Institute of Electron-
ics, Chinese Academy of Sciences, Beijing, China.
From 2014 to 2023, he was with Huazhong Uni-
versity of Science and Technology, where he was
a Professor in 2021. Since 2024, he has been a Professor with the School
of Electronics and Communication Engineering, Sun Yat-sen University,
Guangzhou, China. His research interests include integrated radar and com-
munications, MIMO radar, and MIMO communications.
Gan Zheng (Fellow, IEEE) received the B.Eng.
and M.Eng. degrees in electronic and information
engineering from Tianjin University, Tianjin, China,
in 2002 and 2004, respectively, and the Ph.D. degree
in electrical and electronic engineering from The
University of Hong Kong in 2008. He is cur-
rently a Professor of connected systems with the
School of Engineering, University of Warwick, U.K.
His research interests include machine learning for
wireless communications, reconfigurable intelligent
surfaces, and satellite communications. He was the
first recipient of the 2013 IEEE Signal Processing Letters Best Paper
Award. He received the 2015 GLOBECOM Best Paper Award and the 2018
IEEE Technical Committee on Green Communications and Computing Best
Paper Award. He was listed as a Highly Cited Researcher by Thomson
Reuters/Clarivate Analytics in 2019. He currently serves as an Associate
Editor for IEEE W IRELESS COMMUNICATIONS LETTERS and IEEE T RANS -
ACTIONS ON COMMUNICATIONS .
Dong Li (Member, IEEE) received the Ph.D. degree
in electronics and communication engineering from
Sun Yat-sen University, Guangzhou, China, in 2010.
Since 2010, he has been with the School of Com-
puter Science and Engineering (formally, Faculty of
Information Technology), Macau University of Sci-
ence and Technology (MUST), Macau, China, where
he is currently a Full Professor. He held a visiting
position with the Institute for Infocomm Research,
Singapore, in 2012. His current research interests
include 6G wireless communications, battery-free
Internet of Things (IoT), and wireless AI. He is an Executive Board Member
of the IEEE Macau Section and a member of the Association for Promotion
of Science and Technology of Macau. He was a recipient of the MUST Best
Research Output Award in 2022 and the MUST Bank of China (BoC) Excel-
lent Research Award in 2011, 2016, 2019 and 2021. He was a co-recipient
of the Best Paper Awards of IEEE ICCT 2023, IEEE HealthCom 2023, and
MICCIS 2024; and the Distinguished Paper Award of IEEE GreenCom 2023.
He has been listed among the World’s Top 2% Scientists recognized by
Stanford University since 2020. He is currently an Editor of IEEE MMTC
Review.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on June 06,2026 at 02:21:54 UTC from IEEE Xplore.  Restrictions apply.