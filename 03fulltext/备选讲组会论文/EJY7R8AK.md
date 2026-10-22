---
type: literature-fulltext
title: "Cross-Domain Continual Learning for Edge Intelligence in Wireless ISAC Networks"
zotero_key: "EJY7R8AK"
pdf_key: "GG8UIJF7"
doi: "10.1109/TWC.2025.3588914"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Cross-Domain Continual Learning for Edge Intelligence in Wireless ISAC Networks.md"
fulltext_path: "03fulltext/备选讲组会论文/EJY7R8AK.md"
zotero_item: "zotero://select/library/items/EJY7R8AK"
zotero_pdf: "zotero://open-pdf/library/items/GG8UIJF7"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Cross-Domain Continual Learning for Edge Intelligence in Wireless ISAC Networks

> PDF 原文逐页文本抽取；来源文件 SHA-256：`d915cbf96801fe5b901b18ec2b0a20d6822c126c7573804602f25cd7704c2f8a`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026 1109
Cross-Domain Continual Learning for Edge
Intelligence in Wireless ISAC Networks
Jingzhi Hu
 , Member, IEEE, Xin Li
 , Member, IEEE, Zhou Su
 , Senior Member, IEEE,
and Jun Luo
 , Fellow, IEEE
Abstract—In wireless networks with integrated sensing and
communications (ISAC), edge intelligence (EI) is expected to
be developed at edge devices (ED) for sensing user activities
based on channel state information (CSI). However, due to the
CSI being highly speciﬁc to users’ characteristics, the CSI-
activity relationship is notoriously domain dependent, essentially
demanding EI to learn sufﬁcient datasets from various domains
in order to gain cross-domain sensing capability. This poses a
crucial challenge owing to the EDs’ limited resources, for which
storing datasets across all domains will be a signiﬁcant burden.
In this paper, we propose the EdgeCL framework, enabling
the EI to continually learn-then-discard each incoming dataset,
while remaining resilient to catastrophic forgetting. We design a
transformer-based discriminator for handling sequences of noisy
and nonequispaced CSI samples. Besides, we propose a distilled
core-set based knowledge retention method with robustness-
enhanced optimization to train the discriminator, preserving
its performance for previous domains while preventing future
forgetting. Experimental evaluations show that EdgeCL achieves
89% of performance compared to cumulative training while
consuming only 3% of its memory, mitigating forgetting by 79%.
Index Terms—Continual learning, core-set selection, edge intel-
ligence, perceptive wireless networks, integrated sensing and
communications.
I. I NTRODUCTION
I
NTEGRATED sensing and communications (ISAC) tech-
niques are widely recognized as a crucial enabler for
6G communications [1] as it helps establish cognitive and
perceptive wireless networks in a cost-efﬁcient manner without
requiring extensive additional infrastructure [2]. Speciﬁcally,
by utilizing the readily available channel state information
(CSI), ISAC enables edge devices (EDs), such as cellular base
stations and Wi-Fi access points, to perceive channel variations
caused by human motions and environment dynamics. By
handling the channel variations with powerful signal process-
ing techniques empowered by edge intelligence (EI), i.e., the
artiﬁcial intelligence on the edge, the EDs can develop various
Received 12 October 2024; revised 14 April 2025 and 19 June 2025;
accepted 8 July 2025. Date of publication 23 July 2025; date of current version
22 December 2025. The associate editor coordinating the review of this article
and approving it for publication was B. Guler. (Corresponding author: Jun
Luo.)
This work involved human subjects or animals in its research. The authors
conﬁrm that all human/animal subject research procedures and protocols are
exempt from review board approval.
Jingzhi Hu, Xin Li, and Jun Luo are with the College of Computing and
Data Science, Nanyang Technological University, Singapore 639798 (e-mail:
jingzhi.hu518@gmail.com; l.xin@ntu.edu.sg; junluo@ntu.edu.sg).
Zhou Su is with the School of Cyber Science and Engineering, Xi’an
Jiaotong University, Xi’an 710049, China (e-mail: zhousu@ieee.org).
Digital Object Identiﬁer 10.1109/TWC.2025.3588914
sensing functionalities. These sensing functionalities, in which
human activity recognition (HAR) is a prominent example [3],
can retrospectively beneﬁt communications through improved
context and mobility awareness [4], [5]. With advances in
EI and the increasingly large bandwidth and antenna arrays
used by wireless transceivers, the sensing capability of EDs
in wireless ISAC networks is expected to grow rapidly, paving
the way for more intelligent and adaptive wireless networks.
Nevertheless, the EI tends to be highly domain-dependent.
According to [6], a domain in this context can be deﬁned
as the statistical relationship between CSI variations and user
activities. In practice, the domains should be designated as
the variable that changes during the EI’s deployment and
whose change has a signiﬁcant inﬂuence on this CSI-activity
relationship. Existing studies pursue the cross-domain sensing
capability of EI through extracting domain-invariant features
from CSI, either by using the Doppler frequency shifts (DFS)
[7], [8] or adversarial learning [9], [10], [11]. However,
domain-invariant features discard domain-relevant information
in CSI [12] and thus suffer from deﬁcient accuracy. Moreover,
in common situations where users are in close proximity to
their devices, their individual characteristics, such as body
contours and subtle movements, have a signiﬁcant impact
on CSI [13], which can hardly be removed without sub-
stantially degrading the sensing potential of CSI. Due to the
unpredictable nature of environment dynamics and user char-
acteristics in practice, substantial discrepancies exist between
the domains in ofﬂine pre-training and those encountered in
online deployments, making it challenging for EI to obtain
robust and high-accuracy cross-domain sensing capabilities.
Essentially, to guarantee practical cross-domain sensing
capability, the EI needs to actually learn for the domains
encountered during online deployment [14]. This requires the
collection of sufﬁcient training datasets and timely update
of the EI to extend its sensing capability to new domains.
However, as new domains continually emerge, the CSI datasets
expand over time; storing these datasets in an ED, which
generally has rather limited memory resources, becomes
increasingly prohibitive [15], [16], especially when CSI data
is collected over large bandwidths of multiple bands for high
sensing precision [17]. Although it is possible for the ED
to upload the datasets and its EI to a cloud server and
conduct training remotely to alleviate its local burden [18],
this approach will inevitably incur substantial communication
overheads to the backbone network and lead to high latency
[19].
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

1110 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. Working principle of EdgeCL: The CSI dataset of current domain
and the knowledge learned from previous domains are jointly used for the
cross-domain continual learning of EI.
Fortunately, as different domains emerge at different times,
the datasets for each domain, referred to as domain datasets,
are gathered sequentially. This allows an ED to train its EI
on each domain dataset one by one. For example, consider a
scenario where a new domain dataset is collected periodically
to accommodate newly emerged users within the period. At
the end of each period, the EI can be trained solely on
this new domain dataset, which is then discarded to free up
memory resources on the ED, preparing for subsequent domain
datasets. Nevertheless, such sequential training suffers from
the catastrophic forgetting problem [20], [21], i.e., the EI
tends to rapidly forget its knowledge of previous domains
when trained on the current domain dataset. This problem
severely hinders the EI from gaining the cross-domain sensing
capability and, consequently, limits its potential for enabling
ubiquitous sensing applications in resource-constrained EDs.
In this paper, we propose EdgeCL, a resource-efﬁcient
framework that enables the EI to continually learn-then-discard
domain datasets without catastrophic forgetting, achieving
cross-domain continual learning for discriminative sensing
tasks in wireless ISAC networks. The working principle of
EdgeCL is illustrated in Fig. 1. Treating EI as a parameterized
neural model, we formulate its continual learning over a
sequence of domain datasets as a sequence of optimizations of
neural parameters. EdgeCL jointly considers the loss on the
current domain dataset and a regularization term employed
to preserve the knowledge that the EI has learned from
previous domain datasets. After each training, the knowledge
is updated, and the used domain dataset is discarded to free up
memory occupation, preparing the system to learn subsequent
domains. In particular, in stark contrast with existing studies
[22], [23] that consider continual learning of EI in ISAC but
focus only on the adaptation to the newest domain, EdgeCL
aims to achieve high sensing accuracy across all domains. As
far as the authors know, there are no existing proposals for
this important problem in wireless ISAC networks.
Developing EdgeCL involves addressing three major chal-
lenges. Firstly, unlike video or radar images, the low spatial
resolution of EDs and the multipath effects of wireless
transmissions make the relationship between CSI and user
activities highly intricate, which is further complicated by
the nonequispaced sampling time, requiring specialized neural
model design. Secondly, both the knowledge and its corre-
sponding regularization term are essential for cross-domain
continual learning, yet they are challenging to derive. In
addition, they must be memory and computational efﬁcient
to be applicable given the limited resources of EDs. Thirdly,
the training on subsequent domain datasets inevitably leads
to deviation of neural parameters from the optimal point for
the current domain, degrading its sensing accuracy. However,
such deviations are highly unpredictable, making it difﬁcult to
mitigate the accuracy degradation.
To handle the above challenges efﬁciently, we ﬁrst design
a transformer-based discriminative neural model capable of
handling sequences of noisy and nonequispaced CSI samples,
which has a compact architecture and relies on no compli-
cated time-frequency transformations. Then, we propose a
regularization term for knowledge retention based on distilled
core-sets of few exemplar CSI data, which are signiﬁcantly
smaller than the domain dataset, and improve their efﬁcacy by
a novel hybrid clustering-herding exemplar selection method.
Finally, we prevent the neural model from rapid performance
loss by endowing it with enhanced robustness towards worst-
case parameter deviations. Our main contributions are:
• We propose EdgeCL, the ﬁrst cross-domain continual
learning framework for resource-limited EDs in wire-
less ISAC networks, enabling the EI to learn across
a sequence of domain datasets without catastrophic
forgetting.
• We design an efﬁcient algorithm to handle nonequispaced
noisy CSI samples, preserve previous knowledge by
replaying distilled core-sets of exemplars, and enhance
robustness against unpredictable parameter deviations.
• We perform practical experimental evaluations using a
real-world wireless ISAC system for HAR, conﬁrming
that EdgeCL signiﬁcantly improves the cross-domain
capability of EI, achieving 89% of the cross-domain
training accuracy of cumulative training while consuming
only 3% of its memory, mitigating catastrophic forgetting
by 79%.
The rest of this paper is organized as follows: In Section II,
we establish the system model, including the models for CSI
and EI in wireless ISAC networks. We formulate the EdgeCL
framework for the cross-domain continual learning of EI in
Section III, and design the algorithm to solve it in Section IV.
Experimental setups and results are presented in Section V.
Finally, a conclusion is drawn in Section VI.
II. S YSTEM MODEL
We consider a system comprising an ED hosting a wireless
network for groups of users, where each user connects to
the network with its own user device (UD) carried in close
proximity. The wireless network possesses ISAC capability as
the ED uses the uplink CSI to sense each user. Here, we focus
on general discriminative sensing tasks as they are one of the
most common tasks in ISAC sensing services. Without loss
of generality, we refer to the sensing target uniformly as user
activity, regardless of its actual physical meaning.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

HU et al.: CROSS-DOMAIN CONTINUAL LEARNING FOR EDGE INTELLIGENCE IN WIRELESS ISAC NETWORKS 1111
With its limited computational and memory resources, the
ED trains an EI to learn the intricate relationship between
CSI variations and user activities. However, due to notoriously
strong multi-path interference in wireless channels, this rela-
tionship, referred to as a domain, can be highly speciﬁc to
surrounding environment and user characteristics. As a result,
the EI tends to be domain-speciﬁc and face difﬁculties in
applying to other domains. For the considered system, users
are designated as the domains since users change while the
ED is ﬁxed in an environment, and user characteristics have
a determinant impact on the CSI-activity relationship, which
will be demonstrated in Sec. II-A2. In other ISAC systems,
domains can be represented differently. For example, if the
UD senses its user by downlink CSI, domains can be the EDs
that the UD connects to, whose distinct antenna and frequency
band determine the CSI-activity relationship. Furthermore, for
the EI of a mono-static ISAC system as in [24], domains can
be the environmental conditions, which determine the signal
echoes associated with user activities.
To endow the EI with cross-domain sensing capability, the
most effective method is to train it on sufﬁcient training
datasets for target domains, referred to as the domain datasets;
yet, this is impractical since the ED has limited memory
resources and cannot afford storing all domain datasets. To
facilitate addressing the challenges faced by the EI in wireless
ISAC networks, below, we establish a general model of
the CSI in wireless transmissions, demonstrating its domain
speciﬁcity. In addition, we deﬁne the EI model and outline
how the domain datasets are collected and used.
A. CSI in Wireless Transmissions
1) Model of CSI: In view of the symmetric status of each
user and its UD, we hereby focus on the CSI between an
arbitrary UD and the ED. Given an uplink data transmitted
by a UD as the Tx, the ED as the Rx obtains a CSI sample
by using the channel sounding mechanism [25], [26]. Here,
a CSI sample comprises the channel gains measured by the
ED at a certain time for each pair of Tx-Rx antennas over the
transmission bandwidth. Speciﬁcally, for a pair of Tx and Rx
antennas, within a time duration T and bandwidth B, the CSI
of frequency f and time t can be modeled as [27] and [28]:
h(f,t ) =
(
hS(f) +hD(f,t ) +hU(f,t ) +ϵ(f,t )
)
eiϕ(f,t),
(1)
wherehU(f,t )∈ C denotes the channel gain for the dynamic
scattering paths relating to the movements of the UD’s user,
which lays the foundation of sensing the user’s activities. In
contrast, the other terms in (1) constitute interference for the
sensing: hS(f) ∈ C represents the channel gain for static
paths;hD(f,t )∈ C represents the channel gain resulting from
user-independent dynamic paths, such as scattering on moving
surroundings or on other users; and ϵ(f,t )∈ C denotes the
noise that exists inherently in wireless channels.
Besides, in (1), the phase shift ϕ(f,t )∈ R represents the
random phase error caused by the inevitable unsynchronization
between wireless transceivers, resulting from carrier frequency
offset, sampling time offset, packet detection delay, etc [28].
Theoretically, ϕ(f,t ) can be modeled as a random variable
following a uniform distribution within [ 0, 2π), hS(f) can
be modeled as a constant complex number, and ϵ(f,t ) can
be modeled as a small random variable following complex
Gaussian distribution. Moreover, based on [27], hU(f,t ) and
hD(f,t ) can be modeled approximately by the sum of gains
of S scattering paths. We can focus on the paths experience
single scattering since multiple scattering causes signiﬁcant
attenuation. Therefore, hU(f,t ) can be expressed as
hU(f,t ) =
S∑
s=1
λ
√
G(s)α(s)U ·e−i2π(d(s)Tx,U(t)+d(s)Rx,U(t))/λ
(4π)3/2d(s)Tx,U(t)·d(s)Rx,U(t) ,
(2)
where s is the index of the scattering paths, λ = c/f is the
wavelength of frequency f with c being the light speed, and
i is the imaginary unit. Moreover, G(s) and α(s)U denote the
antenna gain and radar cross section for the scattering path,
respectively, and d(s)Tx,U(t) and d(s)Rx,U(t) denote the distance
from the Tx and Rx antennas to the scattering point of the
s-th path at time t. Similar to hU(f,t ), channel gain hD(f,t )
can be modeled by (2) with subscript “U” substituted by “D”.
2) Analysis of Domain Speciﬁcity: From (1) and (2), it
can be observed that sensing the user activity with CSI is
susceptible to multiple of interference and noise. Although the
phase errorϕ(f,t ) can be handled by conjugate multiplication
[29] (details in Sec. IV-A), and the static gain hS(f) and the
noise ϵ(f,t ) can be handled through band-pass ﬁltering, it is
difﬁcult to separate between hD(f,t ) and hU(f,t ). This is
because the other users’ movements are similar to the target
user’s movements, resulting in similar channel variations as
indicated by (2). Fortunately, in the considered daily scenarios
where users keep their UDs in a close distance (e.g., 20 cm),
obtaining the CSI variations of the target user is feasible.
Speciﬁcally, based on [13, Eqn. (4)], the following relationship
between the CSI variation rates ofh(s)U andh(s)D can be derived
|∂h(s)U /∂t|
|∂h(s)D /∂t|∝
(
d(s)Tx,U(t)
d(s)Tx,D(t)
)−1
, (3)
whereh(s)U andh(s)D denote the gain of the s-th path ofhU(f,t )and hD(f,t ), respectively. Therefore, since the Tx antenna
of the UD is closer to the user while further away from the
surroundings and other users, then d(s)Tx,U(t)≪d(s)Tx,D(t), indi-
cating that the CSI variations caused by the user’s movements
dominate that caused by other users.
Although the close proximity between user and its UD helps
separate the CSI variations caused by the user from those
induced by other dynamics, it leads to higher domain speci-
ﬁcity of the CSI-activity relationship compared with when the
user is far from its UD. From (2), it is evident that the mapping
between CSI and user activity largely depends on the detailed
positions and scattering characteristics of the user’s scattering
points. Therefore, for CSI-based sensing in close proximity
to the UD, subtle nuances in user behavior have a more
pronounced impact compared with non-proximity sensing. The
following corollary provides a theoretical explanation.
Corollary 1: Denote by h the channel gain for a single
scattering path as deﬁned in (2). In addition, denote the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

1112 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
distance between the UD’s Tx antenna to the scattering point
by d. Then, the inﬂuence of d on the relative variation rate of
h is inversely proportional to d, i.e.,
∂
∂d
(⏐⏐⏐∂h∂t⏐⏐⏐)/⏐⏐⏐∂h∂t⏐⏐⏐≈− 1d. (4)
Proof: Eqn. (4) can be derived by ﬁrst taking partial
derivative of d on the root of Eqn. (4) and then calculating
the relative ratio.■
Eqn. (4) indicates that when a user is closer to its UD, the
CSI variation rate changes more rapidly with the deviation
of the scattering point than when the user is farther away.
Although this implies a higher sensitivity, it also means that the
discrepancy among the users’ contours and subtle movements
will be more inﬂuential. In summary, in scenarios where users
are in close proximity to their UDs, the resulting CSI variations
can effectively capture the user’s activity with minimal inter-
ference from other users or environmental dynamics. However,
this comes at the cost of increased domain speciﬁcity of the
CSI-activity mapping to individual user nuances.
B. Edge Intelligence in Wireless ISAC Network
Without loss of generality, an EI can be represented as a
neural model, which in essential is a parameterized mapping
g(·;θ) : H→P . Here, g represents the architecture of the
neural model, and θ∈ RV is its trainable parameters of size
V. In wireless ISAC networks, the input space H is the space
of time series of CSI samples within duration T, each of which
is represented by a matrix H referred to as CSI data, i.e.,
H={H∈ CN×(1+LH)| [H]n =(t[n],h [n]),n =1,...,N },
(5)
where N and n denote the number of CSI samples and
its index, respectively, and t[n] ∈ [0,T ] is the sampling
time corresponding to the n-th data packet. We note that
the sequence of t[n] is generally nonequispaced according to
practical data trafﬁc. Vector h[n]∈ CLH denotes the n-th CSI
sample, comprisingLH elements, and each element represents
a channel gain measurement of a certain subcarrier and a
Tx-Rx link as deﬁned in (1). For the output space P, it
comprises probability vectors for C classes of user activities,
i.e.,
P =
{
p∈ RC|∑Cj=1pj = 1, 0≼p≼ 1}, (6)
where the number of classes C is a predetermined integer and
known to the EI.
Therefore, the sensing of the EI is equivalent to processing
H by p = g(H;θ), where both the architecture g and the
parameter vector θ play a crucial role. However, determining
them analytically is prohibitively challenging due to the highly
intricate relationship between H and p, which cannot be
addressed in closed-form. In contrast, deep learning techniques
leverage a general neural network architecture and optimize
parameters on training datasets, offering a powerful solution
that achieves superior accuracy.
In particular, a training dataset for the EI comprises CSI data
and activity labels sampled following the distribution Γ of a
certain domain, i.e., D ={(Hm, ˆpm)∼Γ}Mm=1, and thus we
refer toD as domain dataset. Here, ˆpm represents class label
of Hm in the form of a one-hot vector, M denotes the size of
domain dataset. Owing to the signiﬁcant inﬂuence of users’
nuances on the CSI as analyzed in Sec. II-A2, the domain
is highly dependent on the users whom the CSI data are
associated with. Notably, a neural model is only statistically
guaranteed to perform well for the domain of its training
dataset, and using it in a different domain, i.e., for a different
user, generally leads to poor performance [30]. Therefore,
to develop cross-domain sensing capability and ensure high
sensing performance across all users, the EI must be trained
on various domain-speciﬁc datasets.
However, due to the ED’s limited memory resources, storing
all domain datasets is impractical. For instance, with a sam-
pling rate of 100 packets per second, an 80 MHz bandwidth,
and 2× 2 Tx-Rx pairs, a 20-activity dataset for 20 users will
exceed 100 GB if each activity involves just 5 minutes of CSI
data. This imposes a signiﬁcant storage burden on the ED and
results in substantial overhead if the data is uploaded to a cloud
server. Moreover, as these datasets are collected over extended
periods, the need for periodic retraining to incorporate new
domains adds a considerable computational load.
To alleviate such heavy memory burdens, a potential
approach is for the EI to sequentially learn the domain datasets
collected over different time periods. For clarity, we assume
that in the k-th (k = 1,...,K ) period, a domain dataset Dk is
collected. The EI then updates the neural model’s parameters
θ usingDk before discarding the dataset to free up memory.
We note that, without loss of generality, a domain dataset may
contain labeled CSI data from multiple users, while different
domain datasets correspond to different users. Although this
approach alleviates storage pressure, it introduces the chal-
lenge of catastrophic forgetting during sequential learning. In
the following section, we formally formulate this issue and
propose the EdgeCL framework to address it.
III. E DGE CL: C ROSS -DOMAIN CONTINUAL LEARNING
FOR EDGE INTELLIGENCE OF ISAC
We propose the EdgeCL framework to handle the catas-
trophic forgetting challenge by optimizing the cross-domain
sensing accuracy of the EI during it continually learns a
sequence of domain datasets D1,..., DK. At each period k,
EdgeCL aims to minimize the empirical classiﬁcation loss
of the EI across the current and previous domain datasets
D1,... Dk. The optimization problem can be expressed as the
following sequential training problem for parameter θ:
(P0)k minθ C(θ;D1:k),
s.t.C(θ;D1:k) =∑(H, ˆp)∈D1:k𝓁(g(H;θ), ˆp),
whereD1:k =∪ki=1Di denotes the union set of D1,..., Dk,
and 𝓁(p, ˆp) represents the cross-entropy (CE) loss given the
sensing result of the EI and the ground truth one-hot label.
More speciﬁcally, the CE loss can be expressed as
𝓁(p, ˆp) =−∑Cj=1 ˆpj log(pj). (7)
However, the direct formulation of (P0) k is intractable
because at the k-th period, the previous domain datasets
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

HU et al.: CROSS-DOMAIN CONTINUAL LEARNING FOR EDGE INTELLIGENCE IN WIRELESS ISAC NETWORKS 1113
D1,... Dk−1 have already been discarded. To convert (P0) k
into a tractable form, we reformulate it as an equivalent prob-
lem: Solving the parameter θ with the maximum a posteriori
probability given domain datasets D1,..., Dk, i.e.,
θ∗ = arg max
θ
log(Pr(θ|D1:k)). (8)
Based on Bayes’ rule, the objective in (8) is derived as:
log(Pr(θ|D1:k))
= log(Pr(Dk|θ)) + log(Pr(θ|D1:k−1))− log(Pr(Dk)), (9)
where log(Pr(Dk|θ)) is the log-likelihood function of Dk
given parameter θ, which is negatively proportional to the
CE loss over Dk, i.e., log(Pr(Dk|θ)) ∝ −C(θ;Dk). Since
Pr(Dk) is independent of θ, (9) reveals that (P0) k can be
handled without directly accessing D1:k−1 but by leveraging
a posteriori probability distribution Pr(θ|D1:k−1).
As the exact a posterior probability distribution can hardly
be obtained in practice, it is necessary to adopt an approxima-
tion of − log(Pr(θ|D1:k−1)). Without loss of generality, we
denote the approximation by function R(θ;Kk), withKk rep-
resenting a core-set of knowledge from the domains preceding
the k-th domain. Consequently, (P0) k can be converted to
(P1)k minθ Lk(θ) =R(θ;Kk) +C(θ;Dk).
In the converted problem (P1) k,R(θ;Kk) serves as regu-
larization, incorporating knowledge of previous domains into
the training of θ overDk, thereby enabling continual learning
across the k domains and preventing catastrophic forgetting.
Therefore, we formulate the cross-domain continual learning
of the EI as a sequence of optimization problems, i.e., (P1) k
(k = 1,...,K ). It can be seen that the key to effectively
solving (P1) k is to determine the appropriate regularization
R(θ;Kk) as well as the core-set of knowledge Kk. Further-
more, owing to the limited resources of the ED, solving (P1) k
is subject to the following two implicit constraints:
• Memory constraint : In line with the goal of alleviating
the memory burden of ED, the memory consumption of
Kk should be signiﬁcantly lower than that of D1:k−1.
• Computation constraint : Given the limited computa-
tional resources of the ED, the algorithmic complexity
for derivingKk must be kept low.
Solving (P1) k under the memory and computation con-
straints faces three critical challenges: First, for the neural
parameters to map CSI data into accurate user activities,
their architecture needs to be carefully designed, which is
challenging due to the difﬁculty in handling nonequispaced
CSI samples affected by noise and interference. Second,
due to the complexity of the high-dimensional a posteriori
probability distribution Pr(θ|D1:k−1), determining the reg-
ularization function that can effectively approximate it and
prevent catastrophic forgetting is a major challenge, which
is exacerbated by the resource constraints of the ED. Third,
since subsequent training following (P1)k will cause deviations
in the optimized neural parameters, it is challenging to solve
(P1)k with robustness against such unpredictable changes.
Fig. 2. Diagram of the proposed algorithm, including the transformer-based
discriminator, the robustness-enhanced optimization, and the distilled core-set
selection.
IV. A LGORITHM DESIGN
We propose an efﬁcient algorithm for EdgeCL to handle the
cross-domain continual learning problem (P1) k of the EI. As
illustrated in Fig. 2, the algorithm comprises three parts: We
ﬁrst design the neural model as a transformer-based discrim-
inator with compact architecture, handling the ﬁrst challenge
of (P1) k. Then, to handle the second challenge, we derive
a resource-efﬁcient regularization function and corresponding
knowledge to prevent catastrophic forgetting in training by
replaying distilled core-sets. Furthermore, for the third chal-
lenge, we leverage robustness-enhanced optimization to reduce
performance degradation caused by worst-case deviations. We
note that although we designate domains as users due to
their dominant impacts on the CSI-activity relationship, our
proposed algorithm is independent of domain designation and
thus effective for arbitrary designation of domains in various
wireless ISAC systems.
A. Transformer-Based Discriminator for CSI Sequences
We design the architecture of the neural model to comprise
two parts: a CSI pre-processor and transformer-based sequence
classiﬁer. The transformer module is adopted to handle CSI
data because CSI data are composed of sequences of CSI
samples, and transformers are universal approximators for
arbitrary sequence functions [31]. Moreover, based on [32],
transformers can handle nonequispaced time series efﬁciently.
In the following, we describe the key components of the CSI
pre-processor and the sequence classiﬁer, respectively.
1) CSI Pre-Processor: The pre-processor serves two pur-
poses. Firstly, it expands each scalar sampling time into a
temporal feature vector to help capture temporal relationship
among CSI samples. Secondly, it processes each complex CSI
sample into a real-valued vector, suppressing random phase
errors in (1) by conjugate multiplication and normalization.
In particular, for the n-th row of H (n = 1,...,N ), i.e.,
[H]n = (t[n],h [n]) deﬁned in (5), we expand the scalar time
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

1114 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
t[n] into a vectorτ[n]∈ CLT by leveraging a series of periodic
trigonometric functions. This enhances the representation of
temporal information [33], allowing the neural model to better
capture detailed temporal relationships between CSI samples,
particularly the periodicity of phase variations at different
speeds. More speciﬁcally, the j-th (j = 1,··· ,L T) element
of temporal feature vector τ[n] can be expressed as
τj[n] =
{
sin(t[n]/Tj/LT), if j is even,
cos(t[n]/T (j−1)/LT), otherwise, (10)
where T denotes the maximum time duration that the CSI data
spans, i.e., t[N]≤T .
Subsequently, we handle the n-th CSI sample, i.e., h[n],
which comprises the channel gains between each pair of Tx
and Rx antennas for all subcarriers. To handle the random
phase error in (1), we adopt the conjugate multiplication
method in [29], which multiplies the conjugate channel gain
of the ﬁrst Rx antenna with the channel gains of the other
antennas. This approach effectively suppresses random phase
errors, as the RF chains of different Rx antennas share a
common oscillator, causing their random phase errors on the
CSI to be similar. Moreover, we normalize the conjugate
multiplication result by subtracting the mean and then dividing
by the maximum. Therefore, for an arbitrary Tx antenna and
subcarrier with their indexes omitted for clarity, the n-th pre-
processed CSI sample comprises xr[n],∀r = 2,...,N Rx, and
each xr[n] is computed by
x′r[n] =hr[n]·h1[n]− mean({hr[n]·h1[n]}Nn=1), (11a)
xr[n] =x′r[n]/ max({x′r[n]}Nn=1). (11b)
In (11a) and (11b), r is the index of the Rx antenna, NRx
denotes the total number of Rx antennas, and hr[n] andh1[n]
denote the elements of h[n] corresponding to the CSI at the
r-th and the ﬁrst Rx antennas, respectively. Consequently, the
efﬁcacy of the CSI pre-processing in (11b) is validated by
Proposition 1 below.
Proposition 1 (Efﬁcacy of CSI Preprocessing): Assume
that the UD is in proximity to its user, and that the channel
gain of static paths is much larger than that of dynamic paths
because of line-of-sight transmission over the static paths. For
an arbitrary Tx antenna and subcarrier, denote the difference of
the pre-processed CSI in (11b) by ∆xr[n] =xr[n]−xr[n−1].
Then, based on (1), it can be derived that the following
relationship holds approximately:
∆xr[n]∝ ∆hU,r[n] +βr∆hU,1[n], (12)
where ∆hU,r[n] =hU,r[n]−hU,r[n−1] denote the difference
of the channel gain at the r-th Rx antenna associated with the
user’s movements, and βr = hS,r/hS,1 with hS,r being the
static channel gain at the r-th Rx antenna.
Proof: See Appendix.■
Proposition 1 indicates that the pre-processed CSI holds
the information of the channel changes caused by the user’s
movements in proximity to the UD. We note that in (12),
βr∆hU,1[n] is environment dependent, which may hinder the
clear correlation between ∆xr[n] and ∆hU,r[n]. Nevertheless,
its impact can be less signiﬁcant when the r-th Rx antenna is
closer to the ﬁrst Rx antenna. In that case, since|hS,r|≈| hS,1|
and|∆hU,r[n]| ≈ |∆hU,1[n]|, based on (12) and the Euler
equation, it can be derived that
∆xr[n]∝eiϕr[n]·⏐⏐∆hU,r[n]⏐⏐· cos(∠(∆hU,r[n])−ϕr[n]),
whereϕr[n] =∠(βr·∆hU,r[n]/∆hU,1[n])/2. As the phase of
channel gain generally changes much faster than its amplitude,
it can be observed that |∆hU,r[n]| can be inferred by the
envelope of |∆xr[n]|, and ∠(∆hU,r[n]) can be inferred by
subtracting cosine phase of |∆xr[n]| by ∠(∆xr[n]). This
demonstrates the feasibility of obtaining channel variations
caused by the user’s movements from the CSI samples after
the pre-processing in (11b).
In more complex scenarios where the Rx antennas are
separated more widely, the relationship between ∆hU,r[n] and
∆xr[n] can be more intricate, and thus an efﬁcient neural
model is needed by the EI. As neural models are more efﬁcient
in handling real values instead of complex values, we convert
each complex-valued input element x∈ C into its equivalent
real-valued vector (|x|, cos∠x, sin∠x) as in [32]. In effect,
this complex-to-real conversion preserves the cyclicity of ∠x
and avoids the discontinuity between 0 and 2π.
Concatenating each temporal feature vector in (10) and the
corresponding pre-processed real-valued vector in (11b), the
resulting sequence can be arranged as a matrix:
[X]n =
(
τ[n],|x[n]|, cos(∠x[n]), sin(∠x[n])
)
, (13)
where n = 1,...,N , X ∈ RN×LP with LP denoting the
vector length after pre-processing, x[n] comprises the pre-
processed CSI for all subcarriers and Tx-Rx antenna pairs. In
(13),∠x[n] denotes the argument vector computed element-
wise for x[n], where the argument of a complex number
x =a +bi is deﬁned as ∠x = tan−1(b/a).
2) Sequence Classiﬁer: Considering the limited computa-
tional resource of the ED, we avoid complicated architectures
with massive parameters and design the following compact
architecture, which comprises three modules: a multi-layer
perceptron (MLP) encoder, a transformer encoder, and a fully-
connected (FC) classiﬁer. The details of the architecture are
illustrated in the left part of Fig. 2. Ass MLPs and transformers
are proven universal approximators for arbitrary functions
[31], [34], the proposed architecture is expected to achieve
high performance for general CSI-activity mapping.
MLP Encoder : To extract activity-related features from
each pre-processed sample, i.e., [X]n, the MLP encoder maps
each sample into a feature vector, leveraging two cascaded
FC layers. The ﬁrst FC layer takes each [X]n (n = 1,...,N )
as input and outputs a feature vector of 2L dimensions. The
second FC layer takes the output feature vectors from the ﬁrst
layer, mapping each of them to an output of L dimensions. In
particular, given an input feature vector xin∈ RLin, each FC
layer can be expressed as a function below:
FC(xin) = Norm
(
ReLU(Wx in +b)
)
, (14)
where W ∈ RLout×Lin and b∈ RLout denote the trainable
weight and bias parameters, respectively, ReLU(·) is the ReLU
activation function, and Norm(·) represents normalizing to zero
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

HU et al.: CROSS-DOMAIN CONTINUAL LEARNING FOR EDGE INTELLIGENCE IN WIRELESS ISAC NETWORKS 1115
mean and unit variance. Collecting the N output vectors of
L dimensions from the second FC layer, the MLP encoder
arranges them as a new sequence denoted by Z ∈ RN×L,
which is then fed into the transformer encoder.
Transformer Encoder The transformer encoder comprises
cascaded multi-head self-attention (MHSA) layers and feed
forward (FF) layers, where each layer is equipped with a
residual connection (RC) [35] to mitigate the vanishing gra-
dient problem in training a deep neural model. The core of
the transformer encoder is using MHSA layers to enable the
information in individual feature vectors of a sequence to
complement each other according to their correlation. The
ﬁrst MHSA layer is fed with the sequence Z ∈ RN×L
obtained from the MLP encoder. It splits each input vector
to apply multiple self-attention layers and then concatenates
the outputs, which can be expressed as
MHSA(Z) = Attn1(Z1)⊕... ⊕ AttnA(ZA),
Attna(Za) = softmax
(
ZaWQ,a(ZaWK,a)⊤
√
L/A
)
· (ZaWV,a),
where Za∈ RN×L/A is the a-th (a = 1,...,A ) sub-matrix
of Z with Z = Z1⊕... ⊕ZA,⊕ denotes the column-wise
matrix concatenation, and WQ,a,W K,a,W V,a∈ RL/A×L/A, are
trainable parameters referred to as the query, key, and value
matrices, respectively. The output of the MHSA layer is added
with its input through the RC, which can be expressed as
˜Z =Z + MHSA(Z).
Then, ˜Z is sent to the FF layer, which comprises two FC
layers with equal dimensions of input and output. The FF layer
handles each row vector ˜z∈ RL in ˜Z by
FF(˜z) = FC2(FC1(˜z)), (15)
which reﬁnes feature representations by feature-level interac-
tions. The output of the FF layer is added with its input through
the RC, which is then fed into the next MHSA layer.
Probability Predictor: As the feature vectors are mutually
complemented in the transformer encoder, we can use the
ﬁrst feature vector in the sequence as the input for the ﬁnal
classiﬁcation, which reduces the computational cost. This
input feature vector is handled by an FC layer to reduce its
dimension to the number of classes C, the resulting logits are
denoted by vector y ∈ RC. Finally, a softmax function is
employed to convert the logit vector into probability predic-
tions for the C classes, i.e.,
p = softmax(y) = exp(y)∑C
i=1 exp(yi)
. (16)
B. Knowledge Retention by Replaying Distilled Core-Set
We then design the regularization function R(θ;Kk) in
(P1)k, which should approximate − log(Pr(θ|D1:k−1)). In
the context of solving sequential training (P1) k, a common
approach to approximate Pr(θ|D1:k−1) is using a multivari-
ate Gaussian distribution, with the initial point of (P1) k, or
equivalently, the result of (P1)k−1, as the mean and variance
estimated statistically. In this case, the regularization function
can be expressed as
RP(θ;Kk) = 12∑Vi=1vk,i(θi−θ∗k−1,i)2, (17)
where core-set knowledge Kk = {θ∗k−1,vk}, θ∗k−1 =
(θ∗k−1,1,...,θ ∗k−1,V ) denotes the result of solving (P1)k−1,
and vk = (vk,1,...,v k,V ) denotes the variance vector. Due to
its intuitive interpretation of penalizing deviations in important
parameters for knowledge retention, such approximation has
been widely used in mainstream continual learning studies
[36], [37], [38], which are referred to as parameter regular-
ization (PR) approaches.
However, despite their merit in intuitive interpretation
and constant memory consumption, the performance of PR
approaches is usually unsatisfactory [39], [40], [41] since
approximating the a posteriori distribution as a Gaussian
can be overly simplistic. As practical Pr(θ|D1:k−1) is highly
complex, a simple parametric distribution such as the Gaussian
can only approximate it within a rather limited local region.
Yet, during the sequential training, the neural parameters
deviate from their initial points to learn new domain datasets.
As a result, the penalty inevitably becomes increasingly less
accurate, causing PR to fail in preserving prior knowledge.
For the above reasons, we design the regularization function
based on an alternative type of approaches named experience
replay (ER) [42], where the approximation of the a posteriori
distribution is less constrained to a local region. The principle
of ER is to select a small set of exemplars S1:k−1 from
previous domain datasetsD1:k−1 as the core-set of knowledge
and replay them during training on Dk. Essentially, it is
equivalent to applying the following approximation:
log
(
Pr(θ|D1:k−1)
)
≈ log
(
Pr(θ|S1:k−1)
)
. (18)
WhenS1:k−1 is randomly sampled from D1:k−1 and|S1:k−1|
is sufﬁciently large, the approximation in (18) is expected to
holds for all θ, rather than restricted to a local region as in PR
approaches. Here,|·| denotes the cardinality of the given set. In
this regard, by using a set of randomly selected data samples
from previous domain datasets as the core-set of knowledge
and involving their CE loss in (P1) k as the regularization term,
it seems (P1) k can be readily handled.
Nevertheless, to satisfy the memory constraint of the ED, the
number of selected exemplars needs to be sufﬁciently small.
In this case, random selection often results in a highly biased
and non-representative core-set, compromising the efﬁcacy of
knowledge retention. Several studies propose using generative
models [43] or data condensation techniques [44] to generate
core-sets that possess full knowledge of previous datasets,
but these methods are unsuitable for the ED due to their
high computational complexity. In contrast, herding [45] and
clustering-based [46] exemplar selection are more compu-
tationally efﬁcient while achieving comparable performance
[39]; yet, each of them have its own strengths and limitations.
To enhance the efﬁciency of selecting representative exem-
plars, we propose a novel hybrid method to combine the
strengths of herding and clustering-based selection while
addressing their limitations. Preliminarily, the clustering-based
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

1116 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
method selects exemplars whose feature vectors are closest to
the cluster centers revealed by the K-means algorithm. The
herding-based method, on the other hand, selects exemplars
whose mean feature vector is closest to the overall mean
of the feature vectors in the domain dataset. The detailed
expressions of the two methods will be provided in (19) and
(20), respectively.
Without loss of generality, we denote the neural parameter
after training in the current period byθ∗, omitting the subscript
for period index. Using the two encoder parts of g(·;θ∗), we
project the current domain dataset D onto its latent feature
space in RL, yielding F. Then, F is divided according to
the classes, with the subset of class c being denoted by Fc.
For eachFc, the budget for exemplars is denoted by E, with
E≪|F c|, which is allocated between clustering and herding-
based selection according to the ratio β∈ [0, 1], referred to as
the clustering-herding ratio.
The ﬁrst βE exemplars are selected by using the K-means
clustering algorithm, representing βE centers of the feature
vectors in Fc. In particular, it is equivalent to ﬁnding βE
centroid feature vectors inFc that minimizes their collective
distance to the rest of the feature vectors, i.e.,
f∗c,1,...,f ∗c,βE = argmin
fj∈Fc|j=1,...,βE
∑
f∈Fc
min
j=1,...,βE
(‖f−fj‖22).
(19)
Although the above clustering problem is a combinatorial
optimization problem and is NP-hard, it can be solved approx-
imately by a greedy algorithm named Lloyd’s algorithm [47].
The Lloyd’s algorithm starts from randomly picking initial
cluster centroids and then iterates between clustering feature
vectors to their nearest centroids and updating centroids as the
means of the clusters. In addition, we employ the k-means++
method [48] to enhance the random selection of initial cen-
troids, which essentially increases the mutual distance among
the selected centroids, leading to better convergence and
clustering results.
Nevertheless, solely using the clustering method to select
exemplars may result in lack of representation for the center
of the entire feature vector set, i.e., ¯fc = ∑f∈Fcf/|Fc|.Based on [49], minimizing the distance between the mean of
feature vectors of the selected exemplars and ¯f is important
for matching the distributions between the selected exemplars
and the original dataset. To achieve this goal, we employ the
herding method [45] to select the rest of (1−β)E exemplars
so that the overall mean of the selected feature vectors has
a minimal distance from ¯fc. It is equivalent to solving the
following optimization problem:
f∗c,βE+ 1,...,f ∗c,E = argmin
fj∈Fc|j=βE+ 1,...,E
‖‖∑Ej′=1fj′− ¯f‖‖22
s.t.fj′ =f∗c,j′,∀j′ = 1,··· ,βE.
(20)
Again, although (20) is a challenging combinational opti-
mization problem, it can be solved approximately using a
greedy algorithm. Speciﬁcally, we employ the nearest-class-
mean algorithm in [45], which iteratively ﬁnds each feature
vector to minimize the current distance.
Consequently, the CSI data corresponding to the E feature
vectors obtained by (19) and (20) are selected as the exem-
plars, forming the core-set of class c, i.e.,
Sc ={(H, ˆp)∈D c|ˆg(H;θ∗) =f∗j, ∃j = 1,...E }, (21)
where ˆg(·) denotes the encoder parts of the neural model, i.e.,
the neural model without the probability predictor.
We then proceed to deriving the regularization function.
Since the empirical CE loss approximates the negative log-
arithmic a posterior distribution, it is intuitive to adopt the
CE loss over the core-set as the regularization function.
Nevertheless, due to the small size of the core-set, the precision
of is approximation is low. To enhance the precision, instead
of using the one-hot class label ˆp of each exemplar, we adopt
the probability vector predicted by the trained neural model.
Furthermore, to mitigate the over-conﬁdence issue [50] of
the neural model during training on the small number of
exemplars, we divide the logits output associated with the
exemplars in g(·) by a conﬁdence downscaling factor η >1
before the softmax. This design essentially coincides with
the distillation loss [51], which is proven to enhance the
knowledge transfer between models. In this regard, we refer
to the selected core-set with low-conﬁdence probability labels
as distilled core-set. For the k-th period, the distilled core-set
can be expressed as:
˜Sk =⋃Cc=1 ˜Sk,c, ˜Sk,c
={(H, ˜p)|˜p = gη(H;θ∗k),H ∈S k,c},
whereSk,c denotes the core-set in (21) for the k-th period,
gη(H;θ) denotes the neural model with its conﬁdence being
divided by η, and ˜p is referred to as a distilled label.
Consequently, we propose to achieve the knowledge reten-
tion by replaying the distilled core-set during the training, and
thus the regularization function can be derived as
R(θ;Kk) =∑(H, ˜p)∈Kk𝓁(gη(H;θ), ˜p), (22)
where knowledge core-set Kk =∪k−1k′=1 ˜Sk′.
C. Robustness-Enhanced Parameter Optimization
We address the performance degradation due to the unpre-
dictable neural parameter deviation caused by training in
subsequent domains. Intuitively, given the optimized neural
parameters at the k-th period denoted by θ∗k, the training in
the subsequent domains will inevitably lead to a deviation
δ∈ RV fromθ∗k, and thus we need to minimizeLk(θ∗k+δ) and
Lk(θ∗k). Nevertheless, owing to the causality, the deviation δ
is unknown in the training for the k-th domain. To handle this
problem, we can solve the θ∗k while minimizing the worst-case
loss for all possible deviations from it, which we refer to as
the robustness-enhanced parameter optimization:
θ∗k = arg minθ max‖δ‖2≤ϵLk(θ +δ), (23)
whereϵ denotes the considered deviation radius and is gener-
ally small (10−2∼10−1) to ensure the efﬁciency of optimizing
θ. The optimization objective in (23) can be viewed as ﬁnding
an optimal θ where the sharpness of its local loss landscape
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

HU et al.: CROSS-DOMAIN CONTINUAL LEARNING FOR EDGE INTELLIGENCE IN WIRELESS ISAC NETWORKS 1117
is minimized [52], which is closely related to the principle
of meta-learning [53]. By substituting the objective of (P1) k
with that of (23), the robustness of the resulting θ∗k can
be signiﬁcantly enhanced, enduring deviations with minimal
potential increase in loss during subsequent training.
To handle (23) efﬁciently, we apply ﬁrst-order Taylor expan-
sion onLk(θ+δ) aroundθ. Then, the deviation that maximizes
the loss around θ can be approximated by
δ∗≈ argmax
‖δ‖2≤ϵ
Lk(θ) +δ
⊤
∇θLk(θ) (24)
=ϵ·∇θLk(θ)/‖∇θLk(θ)‖2, (25)
which is an insightful result since the direction of gradient
∇θLk(θ) indicates the direction of the steepest increase of
Lk(θ). Leveraging (24), problem (23) can be converted to
θ∗k = arg minθ Lk
(
θ +ϵ· ∇θLk(θ)‖∇θLk(θ)‖2
)
. (26)
Without loss of generality, we assume that the optimizer
employed to solve the converted problem (26) is gradient-
based. In this case, the gradient of the objective function in
(26) can be approximately calculated by
∇θLk(θ +δ∗)
≈∇ θLk(θ)|θ=θ+δ∗
+ϵ·
(
∇θ
∇θLk(θ)
‖∇θLk(θ)‖2
)⊤
∇θLk(θ)|θ=θ+δ∗. (27)
On the right hand side of (27), the ﬁrst term is the gradient
of loss function at θ + δ∗ instead of θ, and the second
term represents the compensation for the change of gradient
direction from θ to θ + δ∗, which is generally small due
to small ϵ. However, calculating the second term requires
the estimation of the Hessian matrix of Lk(θ), which can
result in substantial computational burden for the ED. Besides,
as shown in [52], involving high-order derivatives of Lk(θ)
may degrade the performance for estimating ∇θLk(θ +δ∗)
due to more numerical errors. Therefore, we omit the second
term in (27). Consequently, the robustness-enhanced parameter
optimization (23) can be solved by
θ =θ−α∇θ(C(θ;Dk) +R(θ;Kk))|θ=θ+δ∗, (28)
where α denotes the learning rate.
In summary, the complete algorithm for solving the sequen-
tial training problem of EdgeCL is presented in Algorithm 1.
D. Complexity Analysis
We analyze the computational complexity of the training
and the core-set selection in the proposed Algorithm 1, as
well as the extra memory consumption. Speciﬁcally, we focus
on the inﬂuence of key parameters, including: sequence length
of CSI data N, dimension of CSI samples LH, dimension of
latent feature vectors L, size of domain datasets M, number of
classes C, number of exemplars per class E, clustering-herding
ratio β, and number of training iterations I.
Algorithm 1 Robustness-enhanced sequential training with
distilled core-set replay for transformer-based discriminator.
Input: Number of classes C, number of exemplars per class E,
conﬁdence downscaling factor η, clustering-herding ratio
β, deviation radius ϵ, and learning rate α.
1: Initialize g(·;θ) based on transformer-based architecture
in Sec. IV-A with random parameters, and set K1 =∅.
2: for Period k = 1,...,K do
3: Collect domain dataset Dk ={(H, ˆp)} for new users.
4: WithDk andKk, solve the robustness-enhanced opti-
mization (23) by the parameter update in (28) for I
iterations.
5: Generate feature vector setFk by processing CSI data
inDk with ˆg(·;θ∗k).
6: for Class c = 1,...,C do
7: Select set Sk,c of E exemplars based on Fk,c
by hybrid clustering and herding method in (19)
and (20).
8: With gη(·;θ∗k), predict probabilities for feature vec-
tors inSk,c to obtain ˜Sk,c.
9: end for
10: Update the knowledge core-set by Kk+1 = Kk∪
{ ˜Sk,c}Cc=1.
11: DiscardDk to free the memory for the next domain
dataset.
12: end for
1) Training Complexity: Since the computational cost of
the core back-propagation process for training scales linearly
with the loss calculation [30], we focus on analyzing the
complexity of computing the objective function in (P1) k. For
each CSI data, the complexity of predicting its class and
computing the loss depends on the architecture of g(·), which
mainly comprises FC and MHSA layers. The complexity
of an FC layer is proportional to the product of its input
and output dimensions, while an MHSA layer processing
a sequence of length N and element dimension L has a
complexity ofO(N 2L+NL 2) [54]. Therefore, the complexity
of predicting and calculating the loss for each CSI data is
O(NL HL + N 2L + NL 2 + NLC ). Thus, for the domain
datasetDk of M CSI samples and the knowledge core-set
of (k− 1)CE exemplars from the previous k− 1 domains,
the complexity of calculating the objective function and back-
propagation over I training iterations is expressed as:
O
(
INL× (N +LH +L +C)(M + (k− 1)CE)
)
. (29)
The robustness-enhanced optimization (28) approximately
doubles the computation per iteration due to calculating gra-
dients twice, therefore does not change the overall complexity
expression (29). Since LH>L≫C and M ≫ (k− 1)CE ,
(29) can be simpliﬁed toO((N 2L+NL HL+NL 2)MI ), i.e.,
the training time for solving (P1) k increases linearly with M,
I, and LH and quadratically with N and L.
2) Core-Set Selection Complexity: As for the selection
of the exemplars in Dk after solving (P1) k, our designed
algorithm has a low complexity. It is worth noting that the
feature vector for each CSI data can be reused from the last
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

1118 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
training iteration to form Fk,c, thus incurring no additional
cost. Selecting βE exemplars using the K-means cluster-
ing method with k-means++ initialization has a complexity
of O(βEML ) [55], and the complexity of selecting the
remaining (1−β)E exemplars with the herding method is
O((1−β)EML ). Overall, it needs O(CEML ) computation
to obtain the knowledge core-set for Dk, which is negligible
compared to the training complexity.
3) Extra Memory Consumption: We analyze the extra
memory required to store the knowledge core-set at the end
of the k-th period, i.e., Kk+1. Set Kk+1 consists of kCE
exemplars, each comprising a CSI data of size NL H and a
probability vector of size C. Consequently, the total memory
requirement isk(NL H +C)CE ﬂoating-point numbers. Since
CE ≪ M, the memory consumption for storing the knowl-
edge core-set is signiﬁcantly lower than that required to store
the full domain datasets.
V. E VALUATIONS
In this section, we describe the evaluations for the proposed
EdgeCL framework and the designed algorithm. We ﬁrst
elaborate on the experimental setup, including details of the
adopted multi-user HAR dataset, collected by using a practical
wireless ISAC system, and the hyper-parameters in the imple-
mentation of the algorithm. Following that, we present the
experimental results, including benchmark comparisons and
impact factor analyses.
A. Experimental Setup
1) Dataset Collection: To evaluate the EdgeCL, we collect
an HAR dataset by using a practical wireless ISAC system,
where multiple users connect to a Wi-Fi access point (AP).
The Wi-Fi network setup by the AP follows IEEE 802.11ac
standard [25], operating at 5.28 GHz and using a bandwidth
of B = 40 MHz. The UDs generate uplink data trafﬁc by
engaging in an online Zoom meeting. A laptop placed next to
the AP emulates the ED and uses PicoScenes [56] to collect
CSI samples from UDs’ uplink Quality-of-Service (QoS) data
packets sent to the AP. Each CSI sample is a complex array
of size 117× 2, corresponding to the channel gains for the
117 subcarriers at two Rx antennas of the AP.
The complete HAR dataset consists of 20 hours of CSI sam-
ples for C = 10 activities performed by 8 recruited volunteers
in two environments, including a meeting room and a lecture
room. The 8 volunteers consist of 6 males and 2 females,
and Informed Consent was obtained. The 10 activities consist
of 4 body activities: bending, jumping, rotating, and walking;
and 6 gesture activities: push&pull, sweeping, drawing circle,
drawing zigzag, typing-on-phone, and hand-shaking. In each
collection scenario, four volunteers acting as users are present
simultaneously to perform the same activities, with each UD
positioned around 20 cm away from its user, as illustrated
in Figs. 3(a) and 3(b). Each activity consists of two seconds
of movement followed by one second of rest, leading to CSI
sequence durationT =3 s. After segmenting CSI samples into
sequences and labeling each sequence according to activities,
the complete dataset is constructed. The domain datasets are
Fig. 3. (a) Layouts of the experimental environments in a meeting room and
(b) a lecture room.
obtained by splitting the complete dataset based on individual
users. By default, each domain dataset contains data from a
user collected in the two environments.
2) Algorithm Hyper-Parameters: For the transformer-based
discriminator in Sec. IV-A, we implement it with the following
hyper-parameters: i) in the CSI pre-processor, the length of
temporal feature vector is LT = 16; ii) in the MLP encoder,
there are two FC layers, sequentially encoding each input
vector to feature vectors of sizes ﬁrst 128 and then 64;
iii) in the transformer encoder, there are two MHSA and FF
layers, with number of heads A = 8 and feature vector length
L = 64; iv) in the probability predictor, the ﬁrst 64-dim feature
vector in each sequence is mapped to C = 10 logits and then
converted to probabilities by a default softmax function.
Before training on the ﬁrst domain dataset, the neural
parameters are initialized using the Xavier uniform distribution
as in [57]. By default, during the training of each domain
dataset, the learning rate is α = 10−3, and the number of
training iterations is I = 500. In addition, the dropout rate for
feature elements is set to 0.1 to improve generalizability. The
deviation radius in the robustness-enhanced optimization is set
toϵ = 0.03. In each domain dataset, the number of exemplars
to select for each class is E = 10, and the clustering-herding
ratio during exemplar selection is β = 0.9. The conﬁdence
downscaling factor is set to η = 2.
B. Experimental Results
Below, we present the experimental results on EdgeCL from
two perspectives, including the overall benchmark comparison
and impact factor analysis. Each experiment is conducted
with 30 trials using different random seeds to account for
randomness in stochastic training and clustering. By default,
we use the complete domain dataset in each training period to
train the neural model and consistently measure the accuracy
on that dataset in subsequent training periods, which facilitates
a low-variance evaluation of knowledge retention.
1) Overall Comparison: Firstly, we split the CSI data for
the eight users into eight domain datasets, resulting in an
average domain dataset size ofM = 3013. We train the neural
model sequentially on the eight domain datasets, using the
EdgeCL framework with the proposed algorithm, and com-
pare its performance against four state-of-the-art benchmarks
from the two most common categories of continual learning
methods: ER-based and PR-based methods.
• ER-Kmeans: Core-sets of exemplars are selected by
the K-means clustering method [46], and their empirical
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

HU et al.: CROSS-DOMAIN CONTINUAL LEARNING FOR EDGE INTELLIGENCE IN WIRELESS ISAC NETWORKS 1119
Fig. 4. Comparison between the proposed algorithm and the benchmarks and baselines for the accuracy on each of the eight domain datasets after each
training period, averaged over 30 trials.
CE loss is included in the training as the regularization
function.
• ER-herding: Core-sets of exemplars are selected by the
herding method, and their empirical CE loss is included
in the training as the regularization function [45].
• PR-EWC: The regularization function in (17) is used for
knowledge retention, where the variance vector is derived
by the elastic weight consolidation (EWC) method [36].
• PR-MAS: The regularization function in (17) is used for
knowledge retention, where the variance vector is derived
by the memory-aware synapses (MAS) method [37].
Fig. 4 shows the comparison results in terms of the clas-
siﬁcation accuracy. In Fig. 4, the x-axis is divided into eight
regions, showing the accuracy of the neural model on D1 to
D8, respectively. In the k-th region (k = 1,..., 8), the x-axis
range spans the training periods from k to 8, representing the
model’s accuracy onDk after it is ﬁrstly trained on Dk in the
k-th period and subsequently trained on eachDk′ (k<k ′≤ 8)
in later periods. Fig. 4 shows that the proposed algorithm
outperforms the four bulleted continual learning benchmarks,
resulting in an average accuracy of 0.853, which surpasses
the second-best (ER-Kmeans, 0.787) by a noticeable 8%.
Besides, for the proposed algorithm, the average accuracy
loss forD1,..., D7 due to forgetting is 0.144, which is 21%
less than 0.183 of the second-best. Moreover, our evaluation
conﬁrms that, for CSI processing, the ER-based approaches
also signiﬁcantly outperform the PR-based ones, 0.806 vs.
0.356 in average.
Furthermore, we compare four baselines (BL) in Fig. 4. We
ﬁrst evaluate the ER method with random core-set selection,
named BL-ER-rand, showing its average results given 30
random seeds. It can be observed that randomly selected
samples result in less effective exemplars for knowledge
retention compared with those selected by herding, K-means
clustering, and the proposed method. In addition, we evalu-
ate the proposed method with non-distilled core-set, where
the exemplars have hard one-hot labels, referred to as the
BL-nondistill baseline. As shown in Fig. 4, BL-nondistill
exhibits a decline in accuracy compared with the proposed
method, highlighting the importance of using distilled core-
set for knowledge retention. The other two baselines include
the sequential ﬁne-tuning baseline, named BL-FT, and the
cumulative baseline, named BL-cumulative. In BL-FT, the
model is ﬁrstly trained on D1 with a learning rate α and
then ﬁne-tuned on each subsequent domain dataset with a
reduced learning rate of 0.1α, without any continual learning
Fig. 5. Impact of (a) number of domains K and (b) number of exemplars per
class on the average accuracy across the eight domains and 30 trials.
schemes. In BL-cumulative, all the previous domain datasets
are fully stored and re-trained in each period. As expected,
BL-FT results in catastrophic forgetting: the accuracy for
previous domains drops rapidly in subsequent training. Nev-
ertheless, its outperforms PR-based methods for D5 toD8,
as parameter regularization for previous domains severely
undermines the ability of the neural model to learn new
domain datasets.
Another interesting observation is that though
BL-cumulative completely preserve the accuracy for
previous domains, the re-training over previous domain
datasets hinders it adapting to the current domain. Comparing
the proposed algorithm with the BL-FT for D1 to D7
after the eighth training, the proposed algorithm alleviates
the catastrophic forgetting of BL-FT by 79%. In addition,
comparing the proposed algorithm with the BL-cumulative,
it can be calculated that the proposed algorithm achieves
89% of the accuracy for D1 toD7 with only 3% memory
consumption, storing 100 instead of average 3013 CSI data
for each domain dataset.
2) Impact Factor Analyses: We then investigate the impact
of six factors on the proposed algorithm and the EdgeCL
framework, including a) number of domains K, b) number
of exemplars E, c) number of training iterations I, d) learning
rateα, e) clustering-herding ratio β, and f) deviation radius ϵ.
Fig. 5(a) shows that as the number of domains K increases,
the average accuracy for the domain datasets after training
decreases linearly. Nevertheless, with more exemplars allowed,
the decrease rate can be reduced. On the other hand, Fig. 5(b)
reveals a promising sign that using a few exemplars ( E =
10) achieves comparable average accuracy to that of a much
larger number (E = 30), which is consistent across different
values of K. These observations indicate that the proposed
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

1120 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 6. Impact of (a) number of training iterations I and (b) learning rate
α on the average accuracy across the eight domains. Box plots indicate the
distribution over the 30 trials.
Fig. 7. Impact of (a) maximum deviation distance ϵ and (b) on accuracy after
training. Box plots indicate the distribution over the 30 trials, curves connect
median values, and stars represent the highest values.
algorithm has the potential to help the EI handle large numbers
of domains with a small number of exemplars.
Figs. 6(a) and 6(b) demonstrate how the training depth
and intensity, represented by the number of iteration I and
learning rate α, respectively, impact the accuracy for each
domain after the eight periods of training. Speciﬁcally, the
eight box plots, from left to right, in each case represent the
accuracy distributions forD1 toD8 over the 30 trials. Fig. 6(a)
shows that increasing the number of iterations I from 200 to
500 improves the accuracy for all the eight domain datasets.
However, when I is further increased to 800, the accuracy for
earlier domain datasets (D1 toD4) tends to decrease. Notably,
while a moderate increase in learning depth improves the
learning for the current domain datasets, an excessive depth
may cause more forgetting of previously learned knowledge.
Fig. 6(b) compares the accuracy distributions of the eight
domains for different learning rate α. Between α = 0.0005
and α = 0.001, a smaller learning rate improves accuracy on
the earlier domain datasets, i.e., D1 toD4, but decreases it
for the later ones, i.e., D5 toD8. This is probably because
a small learning rate prevents the parameters from deviating
from the training results of previous domains, thereby aiding
in the preservation of previous knowledge. Moreover, using
a large learning rate, e.g., α = 0 .002 results in general
accuracy drop and training instability. Nevertheless, it is worth
noting that the proposed algorithm remains relatively robust to
variations in training depth and intensity over I∈ [500, 800]
and α∈ [0.0005, 0.001].
Figs. 7(a) and 7(b) show how the two key hyper-parameters
of the proposed algorithm, i.e., the clustering-herding ratioβ in
core-set selection and the deviation radius ϵ in the robustness-
enhanced optimization, impact the average accuracy. Fig. 7(a)
demonstrates that the accuracy increases as more exemplars
are selected by clustering, while drop when β = 1. Therefore,
the best strategy for core-set selection is to select most of
them by clustering while using a few to ensure the closeness
between the center of core-set and that of the full domain
dataset in the latent feature space. Fig. 7(b) conﬁrms that by
optimizing the maximum loss within a small deviation radius
ϵ ∈ (0, 0.03), the average accuracy can be improved. It is
worth noting that when ϵ gets larger, e.g.,ϵ≥ 0.03, the result-
ing accuracy drops rapidly since the ﬁrst-order approximation
in (24) becomes highly inaccurate for large ϵ. Furthermore,
it can also be observed that the proper deviation radius for a
smaller learning rate should also be smaller.
VI. C ONCLUSION
This paper has proposed the EdgeCL framework to enable
cross-domain continual learning for EI in wireless ISAC
networks to handle discriminative tasks. First, we have mod-
eled the CSI data and analyzed its domain speciﬁcity. Given
the limited memory and computational resources of EDs,
which cannot support joint re-training on all domain datasets,
EdgeCL reformulates cross-domain continual learning as a
sequential training problem. We have designed a novel efﬁcient
algorithm to solve this problem, integrating the transformer-
based discriminator for CSI sequences, knowledge retention
through replaying distilled core-sets selected by hybrid clus-
tering and herding, and robustness-enhanced optimization to
mitigate accuracy decline due to parameter deviations. On a
real-world ISAC HAR dataset, we have validated that EdgeCL
mitigates the accuracy decline due to catastrophic forgetting by
79%, achieving 89% of the cross-domain training performance
while using only 3% of memory of the cumulative training.
Several promising directions for future research stem from
the results of this work. First, to further mitigate the growth of
core-set size, it is worth exploring the removal of correlated
exemplars. Second, developing expandable neural models may
help enhance the ability of EI to preserve all learned knowl-
edge. Finally, studies on continual learning for wireless ISAC
systems rely on the availability of comprehensive CSI datasets
across varying domains. However, the establishment of such
datasets has received limited research attention so far, and
increased efforts in this direction are expected to substantially
beneﬁt future advancements in the ﬁeld.
APPENDIX
PROOF OF PROPOSITION 1
Substitute (1) into (11a), and omit the gains for the environ-
mental dynamic paths and noise, as they are dominated by the
dynamic channel gains for the user’s motions in the proximity
to the UD. Then, the ﬁrst term of (11a) can be computed by
hr[n]·h1[n]≈hS,rhS,1 +hU,r[n]hS,1 +hU,1[n]hS,r, (30)
where hU,r[n]hU,1[n] is also omitted based on the assump-
tion that gains of static paths are much larger than those
of dynamic paths. Moreover, since hU,r[n] and hU,1[n] are
dynamic channel gains, and such gains typically follow a zero-
mean complex Gaussian distribution, thus the mean value of
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

HU et al.: CROSS-DOMAIN CONTINUAL LEARNING FOR EDGE INTELLIGENCE IN WIRELESS ISAC NETWORKS 1121
{hr[n]·h1[n]}Nn=1 can be approximated by hS,rhS,1. Conse-
quently, based on (11a), x′r[n]≈ hU,r[n]hS,1 +hU,1[n]hS,r,
and xr[n] in (11b) can be expressed as
xr[n]≈ hU,r[n]hS,1 +hU,1[n]hS,r
hU,r[n∗]hS,1 +hU,1[n∗]hS,r (31)
∝hU,r[n] +βrhU,1[n], (32)
where n∗ = argmaxn′|hU,r[n′]hS,1 +hU,1[n′]hS,r| since the
maximum of complex numbers is deﬁned in terms of their
magnitudes, and βr = hS,r/hS,1. Substituting (32) into the
expression of ∆xr[n] proves Proposition 1.
REFERENCES
[1] F. Dong, F. Liu, Y . Cui, W. Wang, K. Han, and Z. Wang, “Sensing as
a service in 6G perceptive networks: A uniﬁed framework for ISAC
resource allocation,” IEEE Trans. Wireless Commun. , vol. 22, no. 5,
pp. 3522–3536, May 2023.
[2] F. Liu et al., “Integrated sensing and communications: Toward dual-
functional wireless networks for 6G and beyond,” IEEE J. Sel. Areas
Commun., vol. 40, no. 6, pp. 1728–1767, Jun. 2022.
[3] X. Li, Y . Cui, J. A. Zhang, F. Liu, D. Zhang, and L. Hanzo, “Integrated
human activity sensing and communications,” IEEE Commun. Mag. ,
vol. 61, no. 5, pp. 90–96, May 2023.
[4] E. C. Strinati et al., “Distributed intelligent integrated sensing and
communications: The 6G-DISAC approach,” in Proc. Joint Eur. Conf.
Netw. Commun. 6G Summit (EuCNC/6G Summit) , Antwerp, Belgium,
Jun. 2024, pp. 392–397.
[5] U. Saleem, Y . Liu, S. Jangsher, Y . Li, and T. Jiang, “Mobility-
aware joint task scheduling and resource allocation for cooperative
mobile edge computing,” IEEE Trans. Wireless Commun., vol. 20, no. 1,
pp. 360–374, Jan. 2021.
[6] M. Akrout, A. Feriani, F. Bellili, A. Mezghani, and E. Hossain, “Domain
generalization in machine learning models for wireless communications:
Concepts, state-of-the-art, and open issues,” IEEE Commun. Surveys
Tuts., vol. 25, no. 4, pp. 3014–3037, 4th Quart., 2023.
[7] Y . Zhang et al., “Widar3.0: Zero-effort cross-domain gesture recognition
with Wi-Fi,” IEEE Trans. Pattern Anal. Mach. Intell. , vol. 44, no. 11,
pp. 8671–8688, Nov. 2022.
[8] K. Niu, F. Zhang, X. Wang, Q. Lv, H. Luo, and D. Zhang,
“Understanding WiFi signal frequency features for position-independent
gesture sensing,” IEEE Trans. Mobile Comput. , vol. 21, no. 11,
pp. 4156–4171, Nov. 2022.
[9] W. Jiang et al., “Towards environment independent device free human
activity recognition,” in Proc. 24th Annu. Int. Conf. Mobile Comput.
Netw., New Delhi, India, Oct. 2018, pp. 289–304.
[10] D. Wang, J. Yang, W. Cui, L. Xie, and S. Sun, “AirFi: Empowering
WiFi-based passive human gesture recognition to unseen environment
via domain generalization,” IEEE Trans. Mobile Comput., vol. 23, no. 2,
pp. 1156–1168, Feb. 2024.
[11] X. Li et al., “CrossGR: Accurate and low-cost cross-target gesture recog-
nition using Wi-Fi,” Proc. ACM Interact., Mobile, Wearable Ubiquitous
Technol., vol. 5, no. 1, pp. 1–23, Mar. 2021.
[12] M.-H. Bui, T. Tran, A. Tran, and D. Phung, “Exploiting domain-speciﬁc
features to enhance domain generalization,” in Proc. NeurIPS , Dec.
2021, pp. 1–13.
[13] J. Hu, T. Zheng, Z. Chen, H. Wang, and J. Luo, “MUSE-Fi: Contactless
muti-person sensing exploiting near-ﬁeld Wi-Fi channel variation,” in
Proc. ACM MobiCom , Madrid, Spain, Oct. 2023, pp. 1–15.
[14] I. Gulrajani and D. Lopez-Paz, “In search of lost domain generalization,”
in Proc. ICLR, May 2021, pp. 1–27.
[15] Y . Mao, C. You, J. Zhang, K. Huang, and K. B. Letaief, “A survey
on mobile edge computing: The communication perspective,” IEEE
Commun. Surveys Tuts., vol. 19, no. 4, pp. 2322–2358, 4th Quart., 2017.
[16] L. A. Haibeh, M. C. E. Yagoub, and A. Jarray, “A survey on mobile
edge computing infrastructure: Design, resource management, and opti-
mization approaches,” IEEE Access, vol. 10, pp. 27591–27610, 2022.
[17] X. Li, H. Wang, Z. Chen, Z. Jiang, and J. Luo, “UWB-Fi: Pushing Wi-
Fi towards ultra-wideband for ﬁne-granularity sensing,” in Proc. 22nd
Annu. Int. Conf. Mobile Syst., Appl. Services , Tokyo, Japan, Jun. 2024,
pp. 42–55.
[18] L. Lin, X. Liao, H. Jin, and P. Li, “Computation ofﬂoading toward edge
computing,” Proc. IEEE, vol. 107, no. 8, pp. 1584–1607, Aug. 2019.
[19] M. V . Barbera, S. Kosta, A. Mei, and J. Stefa, “To ofﬂoad or not to
ofﬂoad? The bandwidth and energy costs of mobile cloud computing,”
in Proc. IEEE INFOCOM , Turin, Italy, Apr. 2013, pp. 1285–1293.
[20] I. J. Goodfellow, M. Mirza, X. Da, A. C. Courville, and Y . Bengio,
“An empirical investigation of catastrophic forgetting in gradient-based
neural networks,” in Proc. ICLR , Banff, AB, Canada, Apr. 2014,
pp. 1–9.
[21] R. Kemker, M. McClure, A. Abitino, T. Hayes, and C. Kanan,
“Measuring catastrophic forgetting in neural networks,” in Proc. AAAI,
New Orleans, LA, USA, Feb. 2018, pp. 1–9.
[22] S. Hu et al., “Digital twin-based user-centric edge continual learning
in integrated sensing and communication,” in Proc. IEEE Int. Conf.
Commun. (ICC), Denver, CO, USA, Jun. 2024, pp. 5646–5651.
[23] S. Ji, Y . Xie, and M. Li, “SiFall: Practical online fall detection with
RF sensing,” in Proc. 20th ACM Conf. Embedded Netw. Sensor Syst. ,
Boston, MA, USA, Nov. 2022, pp. 563–577.
[24] Y . He, G. Yu, Y . Cai, and H. Luo, “Integrated sensing, computation,
and communication: System framework and performance optimization,”
IEEE Trans. Wireless Commun. , vol. 23, no. 2, pp. 1114–1128, Feb.
2024.
[25] IEEE Standard for Information Technology—Telecommunications and
Information Exchange between Systems—Local and Metropolitan
Area Networks–Speciﬁc Requirements—Part 11: Wireless LAN
Medium Access Control (MAC) and Physical Layer (PHY)
Speciﬁcations—Redline, IEEE Standard 802.11-2020 (Revision of
IEEE Standard 802.11-2016)—Redline, Feb. 2021.
[26] 3GPP, Physical Channels and Modulation , document 138.211, Jan.
2020, release 15.
[27] A. Goldsmith, Wireless Communications. Cambridge, U.K.: Cambridge
Univ. Press, 2005.
[28] C. Chen, G. Zhou, and Y . Lin, “Cross-domain WiFi sensing with channel
state information: A survey,” ACM Comput. Surv. , vol. 55, no. 11,
pp. 1–37, Nov. 2023.
[29] X. Li et al., “IndoTrack: Device-free indoor human tracking with
commodity Wi-Fi,” Proc. ACM Interact., Mobile, Wearable Ubiquitous
Technol., vol. 1, no. 3, pp. 1–22, Sep. 2017.
[30] I. Goodfellow, Y . Bengio, and A. Courvile, Deep Learning. Cambridge,
MA, USA: MIT Press, 2016.
[31] C. Yun, S. Bhojanapalli, A. S. Rawat, S. J. Reddi, and S. Kumar,
“Are transformers universal approximators of sequence-to-sequence
functions?,” in Proc. ICLR, Apr. 2020, pp. 1–23.
[32] J. Hu, D. Niyato, and J. Luo, “Cross-domain learning framework for
tracking users in RIS-aided multi-band ISAC systems with sparse labeled
data,” IEEE J. Sel. Areas Commun., vol. 42, no. 10, pp. 2754–2768, Oct.
2024.
[33] Q. Wen et al., “Transformers in time series: A survey,” in Proc. IJCAI,
Macao, China, Aug. 2023, pp. 1–9.
[34] T. Chen and H. Chen, “Universal approximation to nonlinear operators
by neural networks with arbitrary activation functions and its applica-
tion to dynamical systems,” IEEE Trans. Neural Netw. , vol. 6, no. 4,
pp. 911–917, Jul. 1995.
[35] K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for
image recognition,” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit.
(CVPR), Las Vegas, NV , USA, Jun. 2016, pp. 770–778.
[36] J. Kirkpatrick et al., “Overcoming catastrophic forgetting in neural
networks,” Proc. Natl. Acad. Sci. USA, vol. 114, no. 13, pp. 3521–3526,
Mar. 2017.
[37] R. Aljundi, F. Babiloni, M. Elhoseiny, M. Rohrbach, and T. Tuytelaars,
“Memory aware synapses: Learning what (not) to forget,” in Proc. Eur.
Conf. Comput. Vis. (ECCV), Munich, Germany, Sep. 2018, pp. 139–154.
[38] X. Zhao, H. Wang, W. Huang, and W. Lin, “A statistical theory
of regularization-based continual learning,” in Proc. ICML , Vienna,
Austria, Jul. 2024, pp. 1–19.
[39] G. M. Van de Ven, T. Tuytelaars, and A. S. Tolias, “Three types of incre-
mental learning,” Nature Mach. Intell. , vol. 4, no. 12, pp. 1185–1197,
Dec. 2022.
[40] M. De Lange et al., “A continual learning survey: Defying forgetting in
classiﬁcation tasks,” IEEE Trans. Pattern Anal. Mach. Intell. , vol. 44,
no. 7, pp. 3366–3385, Jul. 2022.
[41] M. Akrout, A. Feriani, F. Bellili, A. Mezghani, and E. Hossain,
“Continual learning-based MIMO channel estimation: A benchmarking
study,” in Proc. IEEE Int. Conf. Commun. (ICC) , Rome, Italy, May/Jun.
2023, pp. 2631–2636.
[42] A. Chaudhry et al., “Continual learning with tiny episodic memories,”
in Proc. ICML, Long Beach, CA, USA, May 2019, pp. 1–13.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

1122 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[43] H. Shin, J. K. Lee, J. Kim, and J. Kim, “Continual learning with deep
generative replay,” in Proc. NIPS, Long Beach, CA, USA, Dec. 2017,
pp. 1–10.
[44] Y . Liu, Y . Su, A.-A. Liu, B. Schiele, and Q. Sun, “Mnemonics
training: Multi-class incremental learning without forgetting,” in Proc.
IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR) , Jun. 2020,
pp. 12242–12251.
[45] S.-A. Rebufﬁ, A. Kolesnikov, G. Sperl, and C. H. Lampert, “ICaRL:
Incremental classiﬁer and representation learning,” in Proc. IEEE Conf.
Comput. Vis. Pattern Recognit. (CVPR) , Honolulu, HI, USA, Jul. 2017,
pp. 5533–5542.
[46] C. V . Nguyen, Y . Li, T. D. Bui, and R. E. Turner, “Variational continual
learning,” in Proc. ICLR, Vancouver, BC, Canada, May 2018, pp. 1–18.
[47] T. Kanungo, D. M. Mount, N. S. Netanyahu, C. D. Piatko, R. Silverman,
and A. Y . Wu, “An efﬁcient k-means clustering algorithm: Analysis and
implementation,” IEEE Trans. Pattern Anal. Mach. Intell., vol. 24, no. 7,
pp. 881–892, Jul. 2002.
[48] D. Arthur and S. Vassilvitskii,“K-means++: The advantages of careful
seeding,” in Proc. Annu. ACM.SIAM Symp. Discrete Algorithms (SODA),
New Orleans, LA, USA, Jan. 2007, pp. 1027–1035.
[49] A. Gretton, K. M. Borgwardt, M. J. Rasch, B. Sch ¨olkopf, and A. Smola,
“A kernel two-sample test,” J. Mach. Learn. Res. , vol. 13, no. 1,
pp. 723–773, Mar. 2012.
[50] C. Guo, G. Pleiss, Y . Sun, and K. Q. Weinberger, “On calibration of
modern neural networks,” in Proc. ICML, Sydney, NSW, Australia, Aug.
2017, pp. 1–10.
[51] J. Gou, B. Yu, S. J. Maybank, and D. Tao, “Knowledge distillation: A
survey,” Int. J. Comput. Vis., vol. 129, no. 6, pp. 1789–1819, Mar. 2021.
[52] P. Foret, A. Kleiner, H. Mobahi, and B. Neyshabur, “Sharpness-aware
minimization for efﬁciently improving generalization,” in Proc. ICLR,
New Orleans, LA, USA, May 2021, pp. 1–20.
[53] C. Finn, P. Abbeel, and S. Levine, “Model-agnostic meta-learning for
fast adaptation of deep networks,” in Proc. ICML , Sydney, NSW,
Australia, Aug. 2017, pp. 1–10.
[54] K. Han, A. Xiao, E. Wu, J. Guo, C. Xu, and Y . Wang, “Transformer in
transformer,” in Proc. NeurIPS, Dec. 2021, pp. 1–12.
[55] M. Ahmed, R. Seraj, and S. M. S. Islam, “The k-means algorithm: A
comprehensive survey and performance evaluation,” Electronics, vol. 9,
no. 8, p. 1295, Aug. 2020.
[56] Z. Jiang et al., “Eliminating the barriers: Demystifying Wi-Fi baseband
design and introducing the PicoScenes Wi-Fi sensing platform,” IEEE
Internet Things J. , vol. 9, no. 6, pp. 4476–4496, Mar. 2022.
[57] X. Glorot and Y . Bengio, “Understanding the difﬁculty of training deep
feedforward neural networks,” in Proc. AISTATS, Sardinia, Italy, May
2010, pp. 1–8.
Jingzhi Hu (Member, IEEE) received the B.S.
degree from the School of Electrical Engineering
and Computer Science, Peking University, in 2017,
and the Ph.D. degree from the School of Electronics,
Peking University, in 2022. After the graduation,
he works as a Research Fellow at the College of
Computing and Data Science, Nanyang Technolog-
ical University. His main research interests include
generative semantic communications, wireless ISAC
systems, and reconﬁgurable intelligent surface-aided
RF sensing techniques for the Internet of Things.
Xin Li (Member, IEEE) received the Ph.D. degree
in power machinery and engineering from Tianjin
University, China, in 2022. From 2022 to 2023,
he worked as a Senior Software Engineer with
the Intelligent Automotive Solution Business Unit,
Huawei Technologies Company Ltd. He is currently
a Research Fellow at the College of Computing
and Data Science, Nanyang Technological Univer-
sity. His research interests include machine learning,
signal processing, and wireless sensing.
Zhou Su (Senior Member, IEEE) is currently
a Professor with Xi’an Jiaotong University. He
has published technical papers, including top jour-
nals and top conferences, including IEEE J OUR -
NAL ON SELECTED AREAS IN COMMUNICATIONS ,
IEEE/ACM T RANSACTIONS ON NETWORKING ,
IEEE T RANSACTIONS ON WIRELESS COMMU -
NICATIONS , and IEEE INFOCOM. His research
interests include multimedia communication, wire-
less communication, network security, and network
trafﬁc. He received the Best Paper Award of the
International Conference IEEE AIoT2024, IEEE WCNC2023, IEEE VTC-
Fall2023, and IEEE ICC2020. He is the Chair of the IEEE VTS Xi’an Chapter
Section. He is an Associate Editor of IEEE I NTERNET OF THINGS JOURNAL
and IEEE O PEN JOURNAL OF THE COMPUTER SOCIETY .
Jun Luo (Fellow, IEEE) received the B.S. and
M.S. degrees in electrical engineering from Tsinghua
University, China, and the Ph.D. degree in computer
science from the Swiss Federal Institute of Tech-
nology in Lausanne (EPFL), Lausanne, Switzerland.
From 2006 to 2008, he worked as a Post-Doctoral
Research Fellow with the Department of Elec-
trical and Computer Engineering, University of
Waterloo, Waterloo, Canada. In 2008, he joined
Nanyang Technological University, Singapore, as a
Faculty Member, where he is currently an Associate
Professor. His research interests include mobile and pervasive computing,
machine learning and computer vision, applied operations research, as well
as security. More information can be found at http://www.ntu.edu.sg/home/
junluo
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:01:08 UTC from IEEE Xplore.  Restrictions apply.
