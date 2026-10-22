---
type: literature-fulltext
title: "Multimodal Visual Image Based User Association and Beamforming Using Graph Neural Networks"
zotero_key: "PXAAE5YF"
pdf_key: "HYWXBGVL"
doi: "10.1109/TWC.2025.3582887"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Multimodal Visual Image Based User Association and Beamforming Using Graph Neural Networks.md"
fulltext_path: "03fulltext/备选讲组会论文/PXAAE5YF.md"
zotero_item: "zotero://select/library/items/PXAAE5YF"
zotero_pdf: "zotero://open-pdf/library/items/HYWXBGVL"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Multimodal Visual Image Based User Association and Beamforming Using Graph Neural Networks

> PDF 原文逐页文本抽取；来源文件 SHA-256：`20eef3b7d5197f6f562640deb1ed1de951d029c62ee8b884f9f28774ddfad854`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

292 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Multimodal Visual Image Based User Association
and Beamforming Using Graph Neural Networks
Yinghan Li
 , Graduate Student Member, IEEE , Yiming Liu
 , Graduate Student Member, IEEE ,
and Wei Yu
 , Fellow, IEEE
Abstract—This paper proposes an approach that leverages
multimodal data by integrating visual images with radio fre-
quency (RF) pilots to optimize user association and beamforming
in a downlink wireless cellular network under a max-min fairness
criterion. Traditional methods typically optimize wireless system
parameters based on channel state information (CSI). However,
obtaining accurate CSI requires extensive pilot transmissions,
which lead to increased overhead and latency. Moreover, the
optimization of user association and beamforming is a discrete
and non-convex optimization problem, which is challenging to
solve analytically. In this paper, we propose to incorporate visual
camera data in addition to the RF pilots to perform the joint
optimization of user association and beamforming. The visual
image data help enhance channel awareness, thereby reducing
the dependency on extensive pilot transmissions for system opti-
mization. We employ a learning-based approach based on using
ﬁrst a detection neural network that estimates user locations
from images, and subsequently two graph neural networks
(GNNs) that extract features for system optimization based on the
location information and the received pilots, respectively. Then, a
multimodal GNN is constructed to integrate the features for the
joint optimization user association and beamforming. Simulation
results demonstrate that the proposed method achieves superior
performance, while having low computational complexity and
being interpretable and generalizable, making it an effective
solution as compared to traditional methods based only on RF
pilots.
Index Terms —Multimodal learning, base-station handover,
beamforming, graph neural network (GNN), max-min fairness,
user association, computer vision.
I. I NTRODUCTION
I
N WIRELESS communication, deploying multiple access
points (APs) is an efﬁcient approach to enhance network
coverage, capacity, and reliability in densely populated urban
areas with numerous building obstacles. In multi-AP systems,
ﬁnding efﬁcient user association, power allocation, and beam-
forming strategies based on the channel state information
(CSI) is the central task for optimizing system performance
[1]. However, obtaining accurate CSI between multiple access
points (APs) and user equipments (UEs) solely from RF
Received 23 November 2024; revised 19 March 2025 and 16 May 2025;
accepted 16 June 2025. Date of publication 1 July 2025; date of current
version 22 December 2025. This work was supported by Natural Sciences
and Engineering Research Council through Canada Research Chairs Program.
The associate editor coordinating the review of this article and approving it
for publication was Y . Zhou. (Corresponding author: Wei Yu.)
The authors are with The Edward S. Rogers Sr. Department of Electrical
and Computer Engineering, University of Toronto, Toronto, ON M5S 3G4,
Canada (e-mail: yinghan.li@mail.utoronto.ca; eceym.liu@mail.utoronto.ca;
weiyu@ece.utoronto.ca).
Digital Object Identiﬁer 10.1109/TWC.2025.3582887
pilots is a challenging and resource-intensive task. Addi-
tionally, realizing coordinated optimization among multiple
transmitters is a nontrivial problem. The main objective of this
paper is to enhance channel awareness by integrating insights
from diverse data sources, enabling more efﬁcient data-driven
solutions for complex user association and beamforming
optimization.
This paper proposes a method that leverages both visual
data from images and radio frequency (RF) pilots to address
the downlink user association and beamforming problem,
with an aim to maximize the minimum achievable rate
across all users and ensure fairness. Based on the pilots
and images, a central server assigns each user to an AP
and designs the downlink beamformers for all the target
users for the AP under the power constraints to optimize
certain system-level objective. In densely deployed cellular
networks, user mobility across the cells leads to frequent
ﬂuctuations in CSI, which requires accurate and consistent re-
estimation in order to maintain effective network performance.
In this case, conventional methods, which rely solely on
pilots to realize highly accurate channel estimation [2], would
result in substantial overhead and latency. Visual data offers
the advantage of providing complementary real-time insights
into the propagation environment and channel characteristics
without consuming spectral resources. This motivates the
approach proposed in this paper for integrating visual images
with pilot signals to enhance channel awareness, thereby
reducing the reliance on extensive pilot transmissions for
accurate CSI estimation.
Multimodal data based user association and beamforming
optimization is complex due to the challenge of aligning and
integrating different types of data. In this paper, we propose
to use neural networks to detect and to extract user locations
from the visual images, and to perform system optimization
based on the channel characteristics information implicitly
contained in the user locations. The proposed method bypasses
explicit CSI estimation from the two data sources, and employs
two graph neural networks (GNNs) [3] to extract essential
features to perform user association and beamforming. The
ﬁrst GNN extracts features from the locations estimated from
the images, and another GNN extracts features from RF pilots.
Speciﬁcally, the two GNNs process their inputs independently,
then reﬁne feature representations in successive neural network
layers to extract the speciﬁc channel characteristics needed for
system-level optimization based on their respective input data
types. A third GNN is then introduced to integrate the updated
1536-1276 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 293
features extracted by the two GNNs, and to further reﬁne the
combined information for improved performance and more
efﬁcient decision-making.
This paper adopts GNNs for their ability to capture underly-
ing graph-based relationships, which makes them particularly
effective for optimization tasks that involve parameters with
complex interdependencies. In this paper, each node in the
GNN represents a UE and is associated with a user association
decision and an assigned beamforming vector. The graphical
structure enables the GNN to determine the optimal allocation
strategy for each user, while leveraging the dependencies
between users, such as the inter-user interference which is a
function of their spatial locations. In addition, the GNN-based
framework has generalization capability that enables a single
model to adapt seamlessly across varying network scenarios
with different number of UEs. The capacity to handle com-
plex interdependencies and the capability for generalization
make GNNs a robust and adaptable framework for solving
user association and beamforming optimization problems in
cellular networks.
A. Related Works
The user association problem has been considered exten-
sively in the literature [4]. The simplest way to determine
the user associations is based on the signal-to-noise ratio
(SNR), where each UE connects to the AP that provides the
strongest SNR [5]. The limitation of the max-SNR strategy
is that it often results in unfairness due to uneven loading
at the APs when the UE distribution is uneven, leading to
poor service for users connected to congested APs. In many
works, it has been demonstrated that strategically optimizing
system conﬁgurations can achieve better performance than the
max-SNR strategy. The optimized strategy is designed based
on various objective functions, such as enhancing power efﬁ-
ciency [6], maximizing sum rate [7], and improving fairness
[8]. The works in the area of power efﬁciency mostly focus on
minimizing the total power consumption while maintaining the
required quality of service (QoS) for users [9], [10], [11], [12],
[13]. The works in the area of rate maximization primarily
focus on developing strategies to optimize resource allocation
and user association to ensure that the combined or weighted
data rates of all users are maximized across the network [7],
[14], [15], [16].
This paper focuses on a fairness-oriented approach to solve
the user association and resource allocation problem. Research
in this area typically seeks fairness by employing objective
functions such as proportional fairness and max-min fairness.
In this realm, traditional model based methods [8], [17],
[18] address the user association problem by simplifying the
problem into a more manageable form — either by optimizing
an upper bound or by relaxing the binary constraints into
continuous ones. In contrast, more recent works have proposed
data-driven methods, for example [19], which utilizes deep
reinforcement learning (DRL) to tackle the user association
problem. However, these works primarily focus on single-
antenna scenarios [8], [17], [18], [19], [20], limiting their
applicability in more complex multi-antenna environments,
where the use of beamforming may require a very different
association strategy as compared to single-antenna setups.
The studies [14], [21], [22] explore analytic methods to
address beamforming design, power allocation, and user asso-
ciation under the fairness criterion in multi-antenna scenarios.
In [21], the authors propose a distributed pricing-based method
that leverages a dual coordinate descent approach to optimize
the system conﬁguration. Using weighted rate maximization
as the objective function, fairness is achieved by deﬁning
the weight as the reciprocal of each user’s long-term average
rate. However, long-term fairness cannot guarantee user QoS
in the short term. This brings us to the instantaneous max-
min fairness criterion, which helps users with the weakest
channel conditions by maximizing the minimum rate in each
scheduling instance. In [14], the instantaneous α-proportional
fairness objective function is introduced to guarantee the
fairness. Although the authors suggest that setting α to inﬁnity
theoretically approaches max-min fairness, the method in [14]
can suffer from numerical instability when α is very large,
making it impractical for solving problems under the max-
min fairness criterion. Optimization under the instantaneous
max-min fairness criterion is considered in [22]. However,
the authors simplify the optimization problem by ignoring the
interference and by replacing the constraint that each user must
be assigned to only one AP with a constraint that limits the
number of users each AP can serve. The user association and
beamforming problem can also be tackled using exhaustive
search, which evaluates all possible user association conﬁg-
urations to ﬁnd the optimal one. For each conﬁguration, the
corresponding multipoint beamforming problem can be solved
using the method proposed in [23]. However, this approach is
impractical for large-scale systems due to its high complexity.
Finally, all the above methods assume high-accuracy CSI,
which has to be obtained from extensive pilot signals. A
key contribution of the proposed method in this paper is its
ability to enhance system performance without extensive pilot
transmissions by leveraging multimodal data.
One of the key differentiating features of this paper, com-
pared to conventional approaches, is the utilization of visual
data to enhance communication efﬁciency [24]. Prior studies
have demonstrated the potential of visual information for
solving key tasks in wireless communication, such as channel
estimation [25], handover [26] and beamforming [27], [28],
[29], [30], [31]. In the context of beamforming, most prior
works, such as [27] and [28], focus on optimizing beam-
forming by maximizing signal-to-noise ratio (SNR) based
on the image data. However, these approaches simplify the
problem by omitting interference considerations, so they can
lead to suboptimal solutions in realistic multi-user environ-
ments. For example, [29], [30] propose using multimodal data,
including image combined with accurate channel information
and the user location information for beamforming, but they
do not fully address the interference among the users. In
[31], interference is considered only for power allocation
optimization, while the beamforming design remains focused
on maximizing SNR, which may not be ideal in multi-user
scenarios. Moreover, all these methods rely on supervised
learning, which requires optimal or suboptimal labels for
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

294 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
large training datasets—an often unrealistic assumption in
complex, real-world wireless networks. Additionally, none of
these works consider the user association optimization without
CSI.
B. Contributions
This paper considers the joint user association and beam-
forming optimization problem under a max-min fairness
objective. The main contributions of this paper are summarized
as follows.1
1) Multimodal Data Integration for Enhanced CSI Aware-
ness: This paper introduces a multimodal approach that
combines visual images and RF pilots to optimize user asso-
ciation and beamforming. In mobile user scenarios, accurate
channel information is usually a prerequisite for ensuring
optimal system performance. However, relying solely on pilot
signals for CSI estimation leads to signiﬁcant overhead and
latency. To solve this problem, this paper integrates visual
data with RF pilots to provide real-time channel insights
without consuming additional spectral resources. Speciﬁcally,
our approach employs two GNNs to independently learn
critical features for optimization from RF data and from
location information derived from the images. A third GNN
then integrates these features to optimize user association
and beamforming, in effect combining insights from both
data sources to enable comprehensive decision-making. The
simulation results demonstrate signiﬁcant performance gains
of the proposed multimodal data based method over pilot-
based benchmark methods.
2) Detection Network for Location Estimation: We propose
a location detection stage to map image data captured by
cameras at APs to the estimated user locations. The network
includes a well-trained location detection model that identiﬁes
and localizes targets within the images, a ﬁltering block that
reﬁnes the detection results, and a calibration matrix that
maps pixel coordinates from the images to the real-world
coordinates. Additionally, we provide a detailed analysis of
location estimation errors to demonstrate the effectiveness of
the detection network, and to show that it is a reliable tool for
enhancing environmental awareness.
3) GNN-Based Neural Network for User Association and
Beamforming: This paper proposes a GNN-based neural net-
work to optimize user association and beamforming based
on multimodal data, i.e., the estimated user locations and the
pilots transmitted by the users. The user association and beam-
forming problem is challenging due to the need for coordinated
decision-making across APs, where each user’s association
and beamforming conﬁguration both affects and is affected by
others. In addition, dynamic network scenarios require adapt-
ability to varying user distributions. In the proposed GNN,
each user is modelled as a node. This GNN-based framework
excels at capturing complex interdependencies among the
nodes, and has strong generalization ability, enabling it to
perform effectively across scenarios with varying numbers of
users.
1The codes and dataset for this paper are available at: https://github.com/
Leeyyhh/Multimodal-Based-User-Association-and-Beamforming
4) Unsupervised Learning With a Modiﬁed Straight-
Through Estimator (STE) for Binary User Association: In this
paper, we utilize unsupervised learning to avoid the complexity
of obtaining labels for non-convex optimization problem with
discrete user associations constraints. However, directly quan-
tizing the outputs from the proposed GNN into the required
binary user associations during training disrupts gradient ﬂow
from the loss function to the neural network coefﬁcients. To
maintain accurate and stable gradient backpropagation, the
STE is employed to enable gradients to ﬂow through despite
the non-differentiability. Furthermore, since user associations
act as coefﬁcients for beamforming vectors, setting some user
associations to 0 in the early stages of training can negatively
impact the optimization process. To prevent this, we propose a
modiﬁed STE that avoids the premature exclusion of user-AP
pairs and ensures continuous updates to both user associations
and beamforming vectors throughout the training process.
C. Paper Organization and Notations
The rest of this paper is organized as follows. Section II
introduces the problem formulation. Section III describes the
proposed image-based location estimation neural network.
Section IV outlines the proposed GNN framework for solving
the user association and beamforming problem. Sections V
and VI present simulation results and interpret the learned
solutions from the GNNs. Section VII concludes the paper.
The notations used in this paper are as follows: Scalars are
denoted by lowercase letters. Column vectors are denoted by
bold lowercase letters. Matrices are denoted by bold uppercase
letters. The i-th element of the vector a is denoted by ai. The
transpose and Hermitian transpose of matrices are represented
by (·)⊤ and (·)H, respectively. The complex Gaussian distri-
bution is represented by CN (·,·), and expectation is denoted
by E[·]. Additionally, (·)I, (·)P, and (·)C are used to indicate
components associated with image-based, pilot-based, and
combined data-based optimization, respectively. Additionally,
(·)I, (·)P, and (·)C are used to indicate components associated
with image-based, pilot-based, and combined multimodal data-
based optimization, respectively.
II. P ROBLEM FORMULATION
A. System Model and Problem Formulation
Consider a downlink wireless multi-user multiple-input
single-output (MU-MISO) system where L APs intend to
communicate to K mobile UEs. Each AP is equipped with
a camera and a planar antenna array of M antennas, while
each UE is equipped with a single antenna. Let i and k be
the indices of UEs, where i,k ∈{ 1, 2,...,K }, and let l be
the index of APs, where l ∈ {1, 2,...,L }. The l-th AP is
represented by Bl, and the k-th mobile UE is represented by
theUk. Let akl denote whether or not Uk is associated with
APBl, where akl should satisfy
akl∈{ 0, 1}. (1)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 295
Since each UE is assumed to be uniquely associated with a
single AP, we have
L∑
l=1
akl = 1,∀k. (2)
Let vkl∈ CM be the transmit beamforming vector from Bl
intended for Uk. The beamforming vectors need to satisfy a
sum power constraint
K∑
k=1
||vkl||22≤pl,∀l, (3)
where||vkl||22 represents the transmit power allocated to Uk
by Bl, and pl represents the maximum transmit power of
Bl. We assume that all APs share the same frequency and
time resources for communication. The block-fading model
is adopted in this paper, where the channel remains constant
within each fading block but varies independently between
different blocks. Let hkl ∈ CM denote the channel vectors
from Bl to Uk. The set of all channel vectors is denoted
by h =
[
h⊤11, h⊤12,..., h⊤1L, h⊤21,..., h⊤KL]⊤. Given h, the
received signal at Uk is given by
rk =
L∑
l=1
aklh⊤klvklsk +
L∑
l=1
∑
i⁄=k
ailh⊤klvilsi +nk, (4)
wherenk∼CN (0,σ 2k) is the additive Gaussian noise, and sk
denotes the data symbol intended for Uk, with E[|sk|2] = 1 .
The achievable rate of Uk can be expressed as
Rk = log
(
1 +
∑L
l=1akl|h⊤klvkl|2∑L
l=1
∑
i⁄=kail|h⊤klvil|2 +σ2k
)
. (5)
The objective of the user association and beamforming
optimization in this paper is to ensure fairness among users
by maximizing the minimum achievable rate across all users.
This problem can be formulated mathematically as:
maximize
(a,v)
min
k
Rk (6a)
subject to (1), (2), (3), (6b)
where a = [ a11,a 12,··· ,a 1L,a 21,··· ,aKL]⊤
is the user association vector, and v =
[v11, v12,..., v1L, v21,..., vKL]⊤ denotes the collection of
all beamforming vectors.
Accurately calculating the achievable rates for all users is a
required ﬁrst step for optimizing the minimum achievable rate
across all users, and the channel h is needed for calculating the
rate as formulated in (5). Thus, for optimizing the user rate as
a function of user association and beamforming analytically,
the availability of CSI is crucial.
In this paper, we assume a time-division-duplex (TDD)
system with uplink-downlink channel reciprocity, so that the
CSI can be estimated through uplink pilots. During the uplink
pilot transmission phase, each UE transmits Nu orthogonal
pilots. Let ¯sk ∈ CNu denote the pilot sequence transmitted
fromUk. The pilot sequence should satisfy the power con-
straint ¯sHk ¯sk = ¯pNu, where ¯p denotes the transmit power
of each pilot. The received pilots at Bl are represented by¯Yl∈ CM×Nu, given by:
¯Yl =
K∑
k=1
hkl¯sHk + ¯N, (7)
where ¯N ∈ CM×Nu represents a noise matrix with each
element independently distributed as CN (0,σ 2p).
The pilot assignment for different users follows the tradi-
tional pilot transmission protocol, where different orthogonal
pilots are assigned to different users, i.e., ¯sHk ¯si = 0 if i⁄=k.
The AP correlates ¯Yl with the known pilot sequence ¯sk to
isolate the channel of Uk:
¯rkl = 1¯pNu ¯Yl¯sk = hkl + 1¯pNu ¯N¯sk, (8)
where ¯rkl∈ CM×1 represents the estimated channel between
Uk andBl. In this paper, we denote the received RF pilot
from K UEs to L APs as ¯R ∈ CM×KL, where ¯R =
[¯r11, ¯r12,..., ¯r1L, ¯r21,..., ¯rKL], and ¯rkl is obtained from (8).
We note here that the accuracy of channel estimation is
directly inﬂuenced by the number of available pilots Nu.
Traditional optimization method typically assumes perfect
CSI. Inaccuracies in channel estimation due to limited pilots
can degrade overall system performance. While extensive pilot
transmission can improve channel estimation accuracy, it also
results in increased latency and overhead. To prevent excessive
pilot transmission while enhancing channel awareness, this
paper proposes to utilize visual data as a complementary
source of channel information. The images captured by cam-
eras at each AP provide estimates of the target UE’s location,
which is a primary factor inﬂuencing channel characteristics.
By leveraging both RF pilots and location information derived
from images, the system can more easily learn the channel
characteristics, even in scenarios with limited pilots.
B. Visual Data for Enhanced Channel Awareness
In this paper, we assume that each AP is equipped with
a camera to capture images, and each AP processes these
images locally to estimate the locations of the UEs. The
location information is then transmitted to the central server,
where multiview spatial information from different APs is
utilized for subsequent system optimization. We assume that
the UE locations remain static within each fading block, which
is consistent with the assumption of block-fading channel
models. Let Il∈ RSx×Sy×3 represent the image taken at Bl,
whereSx andSy represent the width and height of the image
in pixels, respectively, and the third dimension corresponds to
the three color channels (RGB). Let ˆqkl∈ R3×1 represent the
location information ofUk from image Il. IfUk is not detected
in the image Il, set ˆqkl =−1, where 1 represents an all-ones
vector. The ˆqkl can be obtained from the image Il using a
functionGl, deﬁned as:
{ˆqkl}Kk=1 =Gl(Il). (9)
Typically, large-scale fading coefﬁcients, which reﬂect long-
term channel conditions and can be estimated based on
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

296 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
location information, are directly utilized for user associa-
tion. However, in urban environments, buildings, roads, and
other obstacles can cause persistent and signiﬁcant multipath
propagation and obstruct the propagation of signal paths.
In such scenarios, relying solely on location information is
insufﬁcient. Therefore, some recent studies consider multipath
channel models to more accurately capture the propagation
environment. By taking into account reﬂected paths, these
approaches aim to provide a more realistic basis for user
association and beamforming optimization [32], [33], [34]. In
this paper, multipath effects are considered as part of the large-
scale fading characteristics, and a learning-based method is
employed to capture the complex channel characteristics.
Let NRkl represent the number of paths from Uk to Bl.
The relationship between the multipath components and the
channel hkl can be expressed as:
hkl =
NRkl∑
n=1
ζ(dnkl)a(θnkl,φnkl) + nkl, (10)
where dnkl represents the distance of the n-th path from
Uk toBl, and θnkl and φnkl represent the elevation angle
and azimuth angle of arrival of the n-th path from Uk to
Bl, respectively. The parameter ζ(dnkl) is the large-scale
fading coefﬁcient associated with the respective path. The term
a(θnkl,φnkl) represents the antenna array response vector at
Bl based on the angles of arrival θnkl and φnkl. The term
nkl∈ CM represents the channel characteristics that are not
explicitly captured by the channel model.
The distance dnkl and the angles of arrival φnkl and θnkl
are determined by the locations of the transmitters, APs,
and objects that reﬂect signals in the environment. Under
the assumption that the locations of the APs and most of
the objects, such as buildings and roads, are ﬁxed, the CSI
can be approximately determined from the locations of the
transmitters. Let ˆQ = [ˆq11, ˆq12,..., ˆqKL] denote the location
matrix. The relationship between the location of UEs and
CSI can be expressed by rewriting (10) using a deterministic
functionM as:
h =M( ˆQ) + ˆN, (11)
where ˆN ∈ CMKL is a matrix representing environmental
factors that inﬂuence the channel characteristics independently
of the location matrix ˆQ.
To realize the functionGl(·) in equation (9), we propose to
utilize a detection neural network to map the images to the UE
locations. Advances in detection neural network models can
now allow the location matrix ˆQ to be accurately obtained
from the images [35]. To further enhance the accuracy and
robustness of ˆQ, multiview images are utilized to increase the
likelihood of detecting UEs and to provide location informa-
tion from multiple perspectives, which collectively mitigate
the effects of occlusions and detection errors. In this way, the
location estimate ˆQ can be made highly reliable.
The matrix ˆQ can then be used to infer channel char-
acteristics, because location information directly inﬂuences
key parameters such as path loss, angles of arrival, and
line-of-sight (LoS) conditions. Based on the above discussion
and the relationships described in (9) and (11), we see that
the multiview images captured by AP cameras can provide
reliable information for inferring the channel h. This motivates
the use of images as a secondary data source that can provide
information complementary to the RF pilots, which can be
used to support system optimization.
C. Multimodal Data-Driven Optimization
In this paper, we aim to optimize system conﬁgurations
using received pilots and captured images. Traditional systems
typically involve a two-step process, where the channels are
ﬁrst estimated based on received data, and system variables
are then optimized accordingly. Since channel estimation
primarily serves as an intermediate step for beamforming
and user association optimization, we propose a data-driven
approach that eliminates the need for explicit channel estima-
tion. The proposed method directly maps received pilots and
image-derived location data to optimized user association and
beamforming decisions. Let F(·) represent the function that
maps the user location matrix ˆQ(t) and the RF pilots ¯R(t) at
the t-th time slot to the optimized system conﬁgurations a(t)
and v(t), deﬁned as:
(a(t), v(t)) =F
(
ˆQ(t), ¯R(t)
)
(12)
Then the multimodal data based optimization can be formu-
lated as
maximize
(a(t),v(t))
min
k
Rk(t) (13a)
subject to (1), (2), (3), (9), (12). (13b)
Due to the complex nature of the functions F(·), ﬁnding
a globally optimal solution analytically for this problem is
intractable. This paper proposes a data-driven approach to
make this problem tractable.
III. I MAGE -BASED LOCATION ESTIMATION
In this section, we provide details of the image detection
neural network, which is utilized for mapping visual data to the
estimated user locations, i.e., implementing the function Gl(·)
as deﬁned in (9). We assume that each AP is equipped with a
camera to capture images of the surrounding environment. To
reduce data transmission load and protect user privacy, only
the estimated user locations, rather than the full image data,
are transmitted to the central server for subsequent system
optimization.
In a system with K users, L APs, and each AP equipped with
M antennas, the amount of data in the transmitted pilots from
the BS to the central server is O(MKL ) complex numbers.
The transmission of image-based location information intro-
duces an additional data overhead ofO(3KL). Typically, M is
much larger than 3, therefore transmitting location estimates
is an efﬁcient method.
To enable local location estimation, we assume that each AP
deploys an image detection neural network to estimate user
locations from the captured images. As shown in Fig. 1, the
architecture of the proposed image detection network consists
of three main components:
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 297
Fig. 1. Architecture of the image detection network.
A. Detection Block
The ﬁrst component is the detection block, where we utilize
YOLOv5 [36], short for “You Only Look Once,” to detect the
target UEs within the images. We assume that the UEs are
cars having different colors to differentiate them in the image,
and each car is assigned a distinct class label. This assumption
enables us to generate a labeled dataset containing bounding
boxes and class labels for each UE. By training YOLOv5 on
this dataset, the model learns to accurately detect and localize
the target UEs in the images. Once trained, the parameters of
YOLOv5 are ﬁxed, and the model can process the new images
to provide the detection results. The detection results are
divided into three components: bounding boxes, class labels,
and conﬁdence scores. The bounding box contains information
about the target UE’s center coordinates, width, and height to
specify the location and size of the detected object within the
image. The class labels identify different detected cars, and the
conﬁdence scores represent the probability that the detection
is accurate.
B. Filtering Block
The second component is the ﬁltering block. It reﬁnes
detected results by ﬁltering out those with conﬁdence scores
below 0.7, and then resolves redundancy by retaining only
the detected object with the highest conﬁdence score when
multiple detected objects share the same class label. This
process ensures that only the most accurate detection is used
for further processing.
C. Camera Calibration Block
The third component is the camera calibration block [37].
Camera calibration is a commonly used method in computer
vision that maps pixel points in the image to their correspond-
ing real-world locations. As shown in Fig. 2, three coordinate
systems are involved in this calibration process: i) the world
coordinate system, which deﬁnes the positions of objects in
the real world; ii) the camera coordinate system, centered at
the camera’s optical center and inﬂuenced by the camera’s
position and rotation; and iii) the pixel coordinate system,
where coordinates correspond to the pixel grid on the camera
sensor, with its origin at the principal point on the image plane.
Let (xwk,y wk, zwk) represent the coordinates of the center ofUk
in the world coordinate system, and let (xckl,y ckl, zckl) denote
Fig. 2. Three coordinate systems used in the camera calibration.
the corresponding point in the camera coordinate system of
the camera at Bl. The transformation between the world
coordinates and the camera coordinates is given by:


xckl
yckl
zckl

 = [Ql| Tl]


xwk
ywk
zwk
1

, (14)
where [Ql| Tl] is known as the extrinsic matrix. Here, Ql∈
R3×3 is the rotation matrix that describes the orientation of the
camera relative to the world coordinate system, and Tl∈ R3 is
the translation vector that speciﬁes the position of the camera’s
optical center in the world coordinate system. The notation
[·|· ] represents the column-wise concatenation of the rotation
matrix and the translation vector.
AtBl, the functional relationship between the coordinates
(xckl,y ckl, zckl) in the camera coordinate system and the corre-
sponding pixel coordinates (xpkl,y pkl) in the pixel coordinate
system can be represented by:
ℏkl


xpkl
ypkl
1

 = Dl


xckl
yckl
zckl

 =


fl 0 c1,l
0 fl c2,l
0 0 1




xckl
yckl
zckl

, (15)
where ℏkl is a scaling factor that aligns the pixel and camera
coordinate systems and Dl represents the intrinsic camera
matrix for camera Bl. In the matrix Dl, fl represents the
focal length of the camera at Bl, while (c1,l,c 2,l) represent
the horizontal and vertical coordinates of the principal point
of the camera at Bl.
In practical scenarios, it is reasonable to assume that the
height of the cars can be estimated. Let ˆzwk denote the esti-
mated height of the center of Uk in the world coordinate
system. Based on (14) and (15), the estimated location of the
k-th car, [ˆxwk, ˆywk ], can be derived from the pixel coordinates
(xpkl,y pkl) by substituting the real height zwk with the ˆzwk . This
estimation follows from (16), as shown at the bottom of the
next page, where Fl = Dl× [Ql| Tl], and [Fl]m,n indicates
the element in the m-th row and n-th column of the matrix Fl.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

298 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
After the images are processed by the detection, ﬁltering,
and calibration blocks within the image detection network, the
AP transmits the obtained location information to the server.
IV. P ROPOSED GNN F RAMEWORK FOR SOLVING USER
ASSOCIATION AND BEAMFORMING
The user association and beamforming optimization prob-
lem (13) follows certain permutation equivariance property,
i.e., the permutation of the users’ locations or users’ CSI
would result in the same permutation of the optimal akl and
vkl. This motivates the use of GNN as a suitable neural
network architecture for user association and beamforming
optimization. In a wireless network, the user association
and beamforming for a user can inherently affect and be
affected by the corresponding decisions made for other users.
This paper proposes a GNN-based archiecture to map the
obtained information (the estimated locations from images
or the received pilots) to the designed beamforming and
user association parameters. GNNs are adopted in this paper,
because they are well-suited for optimization problems with
the permutation equivariance property and excel at capturing
complex relational dependencies between nodes (UEs) in the
graph.
We introduce three GNNs to solve the user association and
beamforming problem:
• GNN-I, which uses image based location estimation as
input to produce a set of candidate user association and
beamforming patterns;
• GNN-P, which uses received pilots as input to produce
another set of candidate user association and beamform-
ing patterns;
• GNN-C, which utilizes features from GNN-I and features
from GNN-P as input to produce the ﬁnal optimized set
of user association and beamforming patterns.
GNN-I and GNN-P are trained separately using their respec-
tive training data and can be directly utilized when only
one type of data is available. For the training of GNN-
C with multimodal data, we ﬁrst ensure that GNN-I and
GNN-P are well-trained independently to guarantee robust
feature extraction from two different data sources. Then,
GNN-C leverages the multimodal features extracted from the
well-trained GNN-I and GNN-P to optimize user association
and beamforming.
As illustrated in Fig. 3, we model the relationships among
users using a graph, where K nodes represent the K users in
the network, and the edges indicate that the connected nodes
are interdependent and can exchange information during the
feature update process. In the optimization problem, a fully
connected graph is utilized to model the relationships among
the users, because the conﬁgurations of the user association
and beamforming are interdependent across the users and
the APs. The k-th node in the graph is associated with the
updated feature vector of Uk. We utilize dIk,n, dPk,n, and dCk,n
to represent Uk’s feature vector after the n-th update from
GNN-I, GNN-P, and GNN-C, respectively.
A. GNN Based on Location Information Derived From
Images
The main goal of GNN-I is to reﬁne the features dIi,n,∀n,
to capture the necessary information aligned with the objective
of the optimization. In this section, we ﬁrst introduce the
input features for GNN-I. Next, we describe the three main
components of GNN-I, which are designed for mapping the
input features to the optimized conﬁgurations. Finally, we
discuss the training and inference processes.
1) Input Features: As shown in Fig. 3, each AP is equipped
with an image detection neural network that processes the cap-
tured images to estimate the locations of UEs. The estimated
locations are transmitted to a central server, where they are
aggregated and sorted according to the class labels of the UEs.
For the GNN, the input features of the k-th node correspond
to the estimated locations ofUk across all APs, represented as
{ˆqkl}Ll=1.
2) GNN Block: The GNN block takes features extracted
from images as input and reﬁnes node features by aggregating
information from neighboring nodes to realize more effective
user association and beamforming optimization. The input
{ˆqkl}Ll=1 of the k-th node is provided to a function ψI0(·) to
produce the initial node features dk,0, i.e.,
dIk,0 =ψI0({ˆqkl}Ll=1), (17)
where ψI0(·) denotes a fully connected network (FCN) with
N I0 layers and each layer is followed by a batch normaliza-
tion (BN) layer and a rectiﬁed linear unit (ReLU) activation
function. The initial features dIk,0 are then processed through
a series of aggregation and combination (AC) blocks, where
each stage updates the node features by integrating information
from neighboring nodes. Let dIk,n denote the output features
of the k-th node after the n-th AC block. The features are
updated according to the following equation:
dIk,n =ξn
(
ψM
({
ψIn(dIi,n−1)}Ki=1,i⁄=k),ϱ In(dIk,n−1)),
(18)
where ψM(·) is an element-wise mean pooling function. The
functions ψIn(·), ϱIn(·), and ξIn(·) represent fully connected
networks (FCNs) with N In,1, N In,2, and N In,3 layers, respec-
tively. Each fully connected layer is followed by a BN layer
and a ReLU activation function. The neural networks ψIn(·)
and ϱIn(·) are applied to extract information from the fea-
tures of neighboring nodes and the node itself, respectively.
The extracted information is concatenated and subsequently
processed by ξn(·), which integrates the combined data to
produce updated node features dIk,n. To ensure sufﬁcient
information change and extraction, the AC block reﬁnes the
initial features for N I times, resulting in the updated node
features dIk,1, dIk,2,..., dIk,N I.
[ ˆxwkl
ˆywkl
]
=
[xpkl[Fl]3,1− [Fl]1,1, xpkl[Fl]3,2− [Fl]1,2
ypkl[Fl]3,1− [Fl]2,1, ypkl[Fl]3,2− [Fl]2,2
]−1
·
[ˆzwk[Fl]1,3 + [Fl]1,4− ˆzwkxpkl[Fl]3,3−xpkl[Fl]3,4
ˆzwk[Fl]2,3 + [Fl]2,4− ˆzwkypkl[Fl]3,3−ypkl[Fl]3,4
]
. (16)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 299
Fig. 3. Architecture of the proposed GNN network.
3) Linear Layer Block: After N I updates, the outputs of
the k-th node dIk,N I are fed into a linear function gI0(·). The
linear layer is designed to transform the node features to a
ﬁxed length vector dIk,N I+1∈ CML +L. The ﬁrst L elements
of dIk,N I+1 represent the user association decisions forUk and
are denoted as {˜aIkl}Ll=1. The last ML elements of dIk,N I+1
is deﬁned as {˜vIkl}Ll=1, corresponding to the beamforming
designed forUk.
4) Normalization Block: This block is designed to map the
output ˜aIkl and ˜vIkl from the linear layer to the normalized
outputs that satisfy the constraints (1), (2) and (3). First,
the user association ˆaIkl and beamforming vector ˆvIkl can be
normalized via the equation:
ˆaIkl = |˜aIkl|∑L
l=1|˜aIkl|, ˆvIkl =√¯pl ˜vIkl√∑Ki=1‖˜vIil‖22, (19)
where the obtained ˆaIkl and ˆvIkl satisfy the (2) and (3). Finally,
we quantize the maximum of the elements in {ˆaIkl}Ll=1 as one
and others as zeros, in order to ensure that it satisﬁes the
binary constraints (1), as follows:
ˆaI⋆kl =



1, if l = argmax
j
(ˆaIkj),
0, otherwise.
(20)
The quantization process ensures that each user is asso-
ciated with exactly one AP. However, quantization is
a non-differentiable function, which poses challenges for
backpropagation-based neural network learning. The STE
modiﬁcation can be used to solve this problem. The STE
enables gradient-based learning by allowing non-differentiable
discrete variables, such as user associations, to be treated as
differentiable during the backpropagation. This can be realized
by
aIkl = ˆaIkl + stop grad(ˆaI⋆kl− ˆaIkl), (21)
where stop grad(·) stops the gradient from being computed
during backpropagation for the enclosed expression but still
passes through the forward values during forward propagation.
Observe from (5) that the user association decisions aIkl
can be thought of as a binary coefﬁcient of the beamforming
vectors vIkl. Thus, if aIkl is set as 0 at any point in the learning
process, vIkl would be excluded from subsequent gradient
calculation, thus preventing updates to the beamforming vector
for that speciﬁc user-AP pair. This can impede the learning
process, because no further updates can occur for such user-
AP pairs. To address this issue, we propose to update the user
association decision aIkl as follows:
aIkl = (1−λ)· ˆaIkl +λ·(ˆaIkl + stop grad(ˆaI⋆kl− ˆaIkl))
= ˆaIkl +λ· stop grad(ˆaI⋆kl− ˆaIkl), (22)
where λ is a balancing coefﬁcient that controls the trade-
off between continuous learning and the binary output. By
introducing λ, we allow for a gradual transition between
continuous learning and binary decisions, ensuring that the
model adjusts and updates beamforming vectors vIkl during
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

300 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
early epochs of training. As λ increases over time, the system
moves closer to binary outputs, progressively locking in ﬁnal
user associations. This gradual transition mechanism prevents
the premature exclusion of user-AP pairs from the optimization
process and ensures that the beamforming vectors are jointly
optimized with the user association decisions.
5) Neural Network Training: Since (13) is a nonconvex
problem with discrete constraints, obtaining labeled data for
training GNN can be challenging and costly. Given the nor-
malized ˆvIkl and aIkl from GNN, we can obtain the estimated
rate ˆRIk from (5). By deﬁning the negative of the objective
function as the loss, the GNN model can learn directly from
the input data by optimizing the objective function given
in (13a). Additionally, to prevent the learned user associ-
ation from being 0 in the initial epochs, we introduce a
penalty term∑kl(aIkl− 1L)2 that prevents values from being
directly set to 1. The loss function can be formulated as
−E
[
min1≤k≤K ˆRIk
]
+λp
∑
kl
(
aIkl− 1L)2, where the expec-
tation E[·] represents the average over the training batch, and
λp is a penalty coefﬁcient that decreases over time to allow
for smoother transitions during optimization.
6) Neural Network Inference: During the inference phase,
as gradient backpropagation is not required, we utilize ˆaI⋆kl as
the ﬁnal user association decision to make the output satisfy
the binary constraint.
B. GNN Based on Received Pilots
As shown in the Fig. 3, the GNN-P leverages RF pilots
to optimize beamforming vPkl and user association aPkl. The
training and inference process of GNN-P are exactly the same
as GNN-I. The structure of GNN-P is shown in Fig. 3, where
dPk,n represents the node features at the n-th layer for Uk.
C. GNN Based on Multimodal Data
As shown also in Fig. 3, the GNN-C leverages both image
and pilot data to optimize beamforming vCkl and user asso-
ciaiton aCkl. When GNN-I and GNN-P are well-trained, their
node features capture essential features from the images and
received pilots, respectively, based on the objective of the
system optimization. We propose to use the concatenation of
the node features from GNN-I and GNN-P as input to GNN-
C. The structure, training, and inference process of GNN-C
are exactly the same as GNN-I and GNN-P. The structure of
GNN-C is shown in Fig. 3, where dCk,n represents the node
features at the n-th layer for Uk.
In this paper, we only consider the permutation equivariance
property of the users, because UE distribution is typically
dynamic and more complex than that of APs. In the user
association and beamforming problem, the APs also exhibit
permutation equivariance properties. When the number of APs
is large and the network becomes more complex, the GNN
structure proposed in [38] and [39] can be utilized for the
APs for better adaptation.
V. S IMULATION RESULTS
In this section, we generate the dataset and evaluate the
performance of the proposed deep learning method.
TABLE I
SCENARIO SETTINGS FOR SIONNA SIMULATION
A. Image Generation
We utilize the open-source simulator for autonomous driv-
ing, CARLA [40], to construct the simulation environment.
As shown in Fig. 4(a), the scenario covers an area of
150 meters by 150 meters. The running area for the cars is
conﬁned to a smaller square road with a length of approxi-
mately 110 meters. In the simulation, four APs are positioned
at the four corners of the intersection, which is represented by
the four orange spheres in the ﬁgure. These APs are positioned
at the coordinates B1 [60,−55, 15], B2 [−55,−60, 15], B3
[−60, 55, 15], and B4 [55, 60, 15]. Each AP is equipped
with a camera, and all APs are strategically positioned to
ensure coverage of two intersecting roads. The orientations
for the cameras are set as follows: [−30◦,−224◦, 0◦] for
B1, [−30◦,−315◦, 0◦] forB2, [−30◦,−43◦, 0◦] forB3, and
[−30◦,−135◦, 0◦] forB4, where three elements represent the
pitch, roll, and yaw angles, respectively. All cameras have
a 100-degree ﬁeld of view (FOV) and capture images at a
resolution of 1280× 720 pixels. From Fig. 4(c-f), we observe
that each camera provides a clear view of two intersecting
roads, ensuring comprehensive coverage of the area of interest.
The simulation utilizes cars to represent the UEs, with each
car assigned a unique color for identiﬁcation. The cars are
randomly generated at various spawn points on the roads and
are assigned random speeds to ensure a realistic variation in
trafﬁc ﬂow. Four cameras at 4 APs are positioned to take
pictures simultaneously at randomly selected time intervals
during the simulation.
B. Channel Generation
In this simulation, we utilize Sionna [41], an open-source
ray tracing software, to model and to analyze the propagation
of wireless signals in the simulation environment. The system
operates at a carrier frequency of 3.5 GHz. The transmit power
of the APs is set to 25 dBm, and the transmit power of the
vehicles is set to 5 dBm. The noise power is set at −55 dBm
for both the APs and the UEs. The APs are equipped with
planar array antennas withMr = 4 rows andMc = 4 columns.
We import simpliﬁed representations of buildings, roads,
ground, and trees into Sionna to create a realistic yet simpliﬁed
simulation environment, as shown in Fig. 4(b). The inﬂuence
of leaves of trees is omitted to simplify the model. The
blue points represent the APs, and the green points represent
the cars. Sionna allows for accurate simulation of complex
environments by taking into account various materials and
their electromagnetic properties. The materials used in our
simulation are shown in Table I. The antennas of the UEs
are assumed to be placed at a ﬁxed height of 0.4 meters.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 301
Fig. 4. (a) The 3D model of the simulation environment in the CARLA simulator. (b) The 3D model of the environment recreated in the Sionna simulator.
(c)-(f) Visualization of the detection results for B1 to B4, respectively.
We obtain the complex channel coefﬁcients, angles of
arrival, and angles of departure for each multipath component
from Sionna. Let NRkl represent the number of paths from Uk
toBl. LetARkl(n) denote the complex channel coefﬁcient to be
multiplied with the n-th multipath component. Let φRkl(n) and
θRkl(n) denote the azimuth and zenith departure angle of the
n-th multipath component from Bl, respectively. For a planar
array, the elements experience different phase shifts based on
their spatial positions. We deﬁne functions v1(m,Mc) and
v2(m,Mc) to map the element index m to the respective row
and column positions in the planar array, centered around the
array’s midpoint:
v1(m,Mc) =
⌊
m
Mc
⌋
− Mr−12 , (23)
v2(m,Mc) = mod (m,Mc)− Mc−12 . (24)
Deﬁne the intermediate variables for clarity:
αRkl(n,m ) =v1(m,Mc) sin(θRkl(n)) cos(φRkl(n)), (25)
βRkl(n,m ) =v2(m,Mc) cos(θRkl(n)), (26)
where αRkl(n,m ) and βRkl(n,m ) denote the phase shifts intro-
duced by the row and column positions, respectively. The
complex channel coefﬁcient for the m-th array element is given
as a summation over all multipath components:
[hkl]m =
∑
n
ARkl(n)e
2jπdR
λc (αRkl(n,m)+βRkl(n,m)), (27)
whereλc denote the wavelength, and dR represent the spacing
between the antenna elements. In this setup, dR is set as half
of the wavelength λc/2. The channel coefﬁcients are utilized
to train the proposed GNN under realistic conditions.
C. Neural Network Conﬁgurations
This section introduces the proposed neural network con-
ﬁgurations and training setups.
For the image detection framework, we employ YOLOv5s
for object detection tasks. The CARLA simulator is used to
generate a dataset with bounding boxes and labels, consisting
of 16,000 images for training and 200 images for validation.
The training epoch is set as 200. After training, the YOLOv5s
parameters are ﬁxed and applied to subsequent tasks.
For the GNN framework, the number of AC blocks in
GNN-I, GNN-P, and GNN-C is set to 2, i.e., N I = N P =
N C = 2 . The architecture and parameters of the FCNs for
GNN-I, GNN-P and GNN-C are summarized in Table II. The
Adam optimizer is employed for all GNNs, with a learning rate
set to 0.0002. The batch sizes for GNN-I, GNN-P, and GNN-C
are 512, 1024, and 1024, respectively. The dataset generated
using CARLA and Sionna is shared across three GNN models,
with a training set comprising 1.97× 105 samples, a valida-
tion set of 1.8× 103 samples, and a test set consisting of
200 samples.
D. Benchmarks
We compare the proposed method with the following bench-
marks. The necessary statistics for the linear minimum mean
square error (LMMSE) estimator are derived from 10,000
channel realizations. Additionally, all learning-based methods
are designed with a carefully optimized structure to ensure a
fair comparison:
1) Exhaustive Search With Perfect CSI: Given perfect CSI,
we perform an exhaustive search to evaluate all possible user
association conﬁgurations. For each conﬁguration, the problem
reduces to the multipoint downlink beamforming problem,
which can be solved using the method proposed in [23]. The
conﬁguration with the highest minimum SINR is then selected
as the ﬁnal result.
2) Perfect-CSI-Based GNN: This method employs the pro-
posed GNN structure with perfect CSI as input, providing an
upper bound on the minimum rate performance achievable by
the proposed GNN structure.
3) Perfect-Location-Based GNN: This method employs the
proposed GNN structure with perfect location as input. It is
used to validate the effectiveness of the proposed image-based
location estimation neural network.
4) Pilot-Based GNN and Imaged-Based GNN: The GNN-P
utilizes the RF pilots rkl as input. The GNN-I utilizes esti-
mated location ˆqkl from images as input. Instead of explicitly
estimating the CSI and then optimizing the problem, the GNN
is designed to directly optimize the proposed problem based
on the input.
5) Direct Multimodal GNN: This method employs a single
GNN structure that directly takes all available data as input,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

302 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE II
ARCHITECTURE AND PARAMETERS OF THE NEURAL NETWORKS (GNN-I, GNN-P, GNN-C)
Fig. 5. Errors of estimated locations from the image detection network:
(a) cumulative distribution function (CDF) for estimated location errors of
cars, (b) mean localization error vs. different distance ranges.
including the estimated location and pilot data, without the
separate feature extraction process [42]. It serves as a baseline
to evaluate the advantages of using two separate GNNs for
feature extraction prior to multimodal fusion.
6) Exhaustive Search With LMMSE Channel Estimation:
The channel is estimated using the LMMSE method. Based
on the estimated channel, we perform an exhaustive search to
evaluate all possible user association conﬁgurations. For each
conﬁguration, the multipoint downlink beamforming problem
is solved using the approach described in [23]. The best
conﬁguration is selected as the ﬁnal solution.
7) Strongest-Channel-Based Assignment with LMMSE
Channel Estimation: We use the LMMSE method for channel
estimation. Based on the estimated channel, each user is
associated with the AP that provides the highest channel gain.
After determining the user association, the problem is solved
using the approach from [23].
E. Performance Evaluation of Image Detection Network
To demonstrate the performance of the detection based
neural network, Fig. 5(a) presents the cumulative distribution
function (CDF) of location estimation errors for different cars.
The data is averaged over 10,000 images. The CDF curves
demonstrate that 70% of the location errors are smaller than
0.5 meters, and more than 99% of the errors are smaller
than 1 meter. The location error CDF of Car 1 differs from
the other cars due to its bright color, which improves detection
accuracy. The CDF of other cars exhibits similar location error
performance.
Additionally, the mean errors of location estimation range
from 0.257 to 0.316 meters, which are relatively small.
In conclusion, the proposed detection based neural network
demonstrates robust and reliable performance in accurately
estimating the locations of different cars.
Fig. 5(b) shows the mean localization error as a function
of distance. It demonstrates that while location estimates from
images cannot provide accurate CSI, they can infer channel
characteristics and are less affected by the distance between
UEs and APs. This stability contrasts with traditional RF
pilot based methods, where estimation accuracy degrades with
increased distance. The results underscore the robustness of the
proposed multimodal approach, especially when users are far
from APs but within the camera’s ﬁeld of view.
F . Performance of User Association and Beamforming GNN
We illustrate the impact of the number of uplink pilots on
the downlink minimum rate performance for different methods
in Fig. 6(a). In the simulation, the number of antennas is set
to 16. All methods are evaluated on the same test dataset to
ensure a fair comparison, and the performance is averaged over
200 samples to ensure the reliability of the results.
In Fig. 6(a), the exhaustive search algorithm with perfect
CSI method consistently achieves the highest minimum rate of
3.28 bps/Hz across all pilot numbers. This method serves as an
upper bound on the performance, since it utilizes perfect CSI
to evaluate every possible user association conﬁguration to ﬁnd
the most effective solution. The proposed GNN architecture
achieves a performance with only about a 7.6% reduction
in the downlink minimum rate as compared with exhaustive
search with perfect CSI. This indicates that the proposed
GNN structure is capable of learning and approximating the
exhaustive search based method effectively.
Furthermore, the Image-Based GNN performs closely to
the Perfect-Location-Based GNN method, which shows the
efﬁciency of the proposed image based location detection
neural network in providing accurate location estimates for
system optimization.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 303
Fig. 6. Minimum rate performance of the proposed GNN with K = 6 and L = 4.
The pilot based GNN demonstrates a notable improve-
ment in minimum rate performance as the number of pilots
increases. From (8), it is evident that the obtained CSI
approaches the perfect CSI with an increasing number of
pilots. Consequently, reliable channel information derived
from pilots leads to improved overall system performance. The
Image-Based GNN performs well in environments with limited
pilot signals because it provides accurate location information
independent of the number of pilot signals. The minimum
rate performance of the Direct Multimodal GNN is much
lower than that of the Image-and-Pilot-Based GNN, which
indicates that it is challenging for a single GNN to effectively
learn from different data sources without separate feature
extraction. The proposed multimodal GNN, which integrates
image and pilot data, consistently outperforms the approach of
using images alone or using pilots alone. The superior perfor-
mance of the multimodal GNN indicates that the proposed
GNN-based neural network effectively integrates features
extracted from images and RF pilot signals and effec-
tively utilizes the combined information for efﬁcient system
optimization.
Other traditional methods fall short as compared to
the proposed GNN-based approaches, further demonstrat-
ing the effectiveness of the proposed method. In conclusion,
the integration of visual data with pilot signals proves espe-
cially beneﬁcial for improving the minimum rate performance
compared with pilot-based benchmarks.
Next, we illustrate the impact of the number of antennas
on the minimum rate performance for different methods in
Fig. 6(b), with the number of pilots set to 16. As the
number of antennas increases, the minimum rate improves
across all methods. The Perfect-CSI-Based GNN achieves
the highest performance and serves as an upper bound. The
proposed Image-and-Pilot-Based GNN achieves a competitive
minimum rate as compared to the Perfect- CSI-Based GNN,
which demonstrates the effectiveness of the proposed GNN
across different numbers of antennas. Furthermore, the pro-
posed Image-and-Pilot-Based GNN consistently outperforms
the Pilot-Based GNN, which demonstrates the beneﬁts of
utilizing multimodal data for user association and beamform-
ing optimization.
From Fig. 6(a) and Fig. 6(b), we observe that the pro-
posed Image-and-Pilot-Based GNN consistently achieves a
higher minimum rate than traditional and pilot-based meth-
ods, regardless of the number of pilots or antennas. These
results conﬁrm the effectiveness of multimodal data fusion
for optimizing user association and beamforming in wireless
networks.
G. Complexity Comparison
To evaluate the computational complexity of the proposed
methods, we compare the average running time required to
solve a single instance of the problem. The results are averaged
over 200 samples to ensure reliability. All the methods are
implemented on a computer equipped with a Intel R©CoreTM
i7-12700 CPU (2.10GHz) and an NVIDIA GeForce RTX 4090
GPU. The results are summarized in Table III.
In Table III, the exhaustive search methods exhibit the
longest running time; the excessive running time makes
them impractical for real-time applications. In contrast, the
strongest-channel-based assignment method offers a signif-
icantly faster solution; however, it sacriﬁces optimality, as
observed in Fig. 6. The GNN-based approaches demonstrate
substantial improvements in efﬁciency, with all methods hav-
ing running time lower than 5ms. The fast running time makes
the proposed GNN suitable for real-time applications. The pro-
posed multimodal based GNN completes the location detection
in 4.613ms and requires 0.171ms to process the features
and to provide the ﬁnal output. This method, while slightly
slower than the image-only GNN and pilot-only GNN, offers
a balanced trade-off between computational efﬁciency and the
robustness of the solution. Overall, the compelling advan-
tages in both running time and performance of the proposed
GNN-based approach make it well suited for practical
deployment.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

304 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE III
AVERAGE RUNNING TIME FOR SOLVING ONE USER ASSOCIATION PROBLEM
Fig. 7. Generalization Performance of the Proposed GNN Models. a) Minimum rate performance with varying and ﬁxed car (UE) numbers for training.
b) Minimum rate performance of GNN models trained with different numbers of pilots.
H. Generalization
In this section, we evaluate the generalization capability of
the proposed method. We compare the performance of two
GNN models: one trained with a ﬁxed number of cars and
another trained with varying number of cars. Both models are
tested on a dataset with a ﬁxed number of cars to ensure a con-
sistent basis for comparison. Fig. 7(a) illustrates the minimum
rate performance of the two GNN models as a function of the
number of pilots. Although scenarios with varying numbers of
cars introduce increased complexity and require more ﬂexible
decision-making, the proposed method maintains a similar
minimum rate as the model trained with a ﬁxed number of
cars. This result demonstrates the effectiveness of the proposed
method in generalizing across scenarios with varying numbers
of cars, which is essential for practical applications.
In Fig. 7(b), we illustrates the minimum-rate performance
of the GNN models trained with different numbers of pilots.
The Standard-Image-and-Pilot-Based GNN is trained using
a dataset where the number of pilots matches the number
of pilots used during inference. The Image-and-Pilot-Based
GNN (N trainu = ω) represents the GNN trained on a dataset
with a ﬁxed number of ω pilots, regardless of the number of
pilots used during inference. To evaluate the generalization
performance of the proposed GNN, we measure its minimum
rate performance when the proposed GNN is trained with
16 pilots and 64 pilots, and then tested under different numbers
of pilots. When trained with 16 pilots, the GNN performs
as well as the Standard-Image-and-Pilot-Based GNN when
the number of pilots used for inference is low. However,
when the number of pilots is signiﬁcantly greater than 16,
its performance fails to match the Standard-Image-and-Pilot-
Based GNN. This is reasonable because a low number of
pilots provides less reliable CSI, which limits the ability of the
GNN to learn meaningful representations during the training
process. In such cases, the GNN relies more on image-based
information for decision-making. When trained with 64 pilots,
the proposed GNN method performs almost as well as the
Standard-Image-and-Pilot-Based GNN when the number of
pilots ranges from 16 to 1024. This strong performance across
different pilot settings indicates that the GNN trained with
64 pilots has robust generalization capabilities.
If the length of pilots can be provided as additional informa-
tion, combining the results from Image-and-Pilot-Based GNN
(N trainu = 16) and Image-and-Pilot-Based GNN ( N trainu = 64)
could achieve performance very close to that of the Standard-
Image-and-Pilot-Based GNN across a pilot range from 1 to
1024. When the length of pilots is 16 or fewer, we choose
the result from the GNN trained with N trainu = 16 , and
when it is greater than 16, we choose the result from the
GNN trained with N trainu = 64. The results demonstrate that
with pilot information, two GNN models trained with a ﬁxed
number of pilots can be efﬁciently utilized to solve the user
association and beamforming problems across a large range
of pilot lengths.
Using a dataset with varying number of cars for training
the neural network leads to high variation in user distributions
and makes it difﬁcult for the neural network to realize effective
optimization. Furthermore, achieving effective optimization on
a dataset different from training requires high generalization
capability of the trained neural network. Despite the chal-
lenges, the proposed method exhibits strong generalization
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 14 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 305
Fig. 8. Array response of the APs and user association decisions for the cars obtained from GNN-P and GNN-C. The transmitted pilot length is set as 4.
properties. This is largely due to three key characteristics of
the proposed GNN structure. First, the structure of GNNs is
designed to capture interactions between nodes (UEs) through
graph structures rather than relying solely on memorizing
data distributions. This property enables GNNs to naturally
capture relational dependencies between UEs, regardless of the
number of UEs in the system. Moreover, GNNs apply the same
message-passing function to all nodes, which means GNNs
are more data efﬁcient. Lastly, the proposed method is less
sensitive when the distribution of the data changes, because
it extracts features separately using two different GNNs. This
separate feature extraction ensures that changes in the distribu-
tion of one type of data do not interfere with feature extraction
from the other type. These properties enable the proposed
method to generalize effectively. In conclusion, the results
from Fig. 7 demonstrate strong generalization capability and
effectiveness of the proposed GNN-based framework.
VI. I NTERPRETATION OF SOLUTIONS FROM GNN
To interpret the solutions from the GNN, this section
visually veriﬁes that the designed beamformer maximizes the
transmitted signal power at the angle of the dominant path
from the target UE. Additionally, this section demonstrates that
the user association conﬁgurations are designed based on the
appropriate optimization criteria, rather than merely assigning
users to their nearest APs. We use the array response function
to qualitatively evaluate the correctness of the beamforming
vector learned by the proposed GNN. Let φk andθk represent
the azimuth and zenith angles of arrival fromUk to the associ-
ated AP, respectively. Let vk denote the learned beamforming
vector forUk from the associated AP. The array response for
Uk is a function of the angles θk and φk deﬁned by
fk(θk,φk) =||p(θk,φk)Hvk||22, (28)
where
[p(θk,φk)]m =e
2jπdR
λc (v1(m,Mc) sin(θk) cos(φk)+v2(m,Mc) cos(θk)).
(29)
Fig. 8(a-f) presents the learned array responses for 6 UEs
generated by GNN-P, while Fig. 8(h-m) shows the learned
array responses generated by GNN-C. The color intensity
represents the array response strength as deﬁned in (28).
The red point represents the target user, while the black
points represent other cars that are not the primary focus
of the beamformer. The length of transmitted pilots, Nu, is
set to 4. Fig. 6 indicates that the minimum rate performance
of GNN-C is better than that of GNN-P. From the array
response pattern for U2, it is evident that the array response
differs between GNN-P and GNN-C. Compared with GNN-P,
the beamforming vectors generated by GNN-C are more
accurately directed towards the target users. This difference
indicates the proposed GNN-C’s ability to effectively combine
pilot and image information for a more precise and efﬁcient
beamforming vector design.
Fig. 8(g) and Fig. 8(n) illustrate the optimized user asso-
ciation decisions from the GNN-P and GNN-C. Each subplot
shows the spatial distribution of APs and UEs. The UEs are
represented by red dots, and the APs are represented by blue
dots. If the dashed line connects a UE and an AP, it indicates
that the UE is associated with that AP based on the optimized
user association decisions. To verify the effectiveness of the
user association decisions, we compare the user association
decision from the propose method with the simplest nearest-
AP association rule. Observing from Fig. 8(g), the UEs are
not optimally associated with the APs when the number of
pilot signals is set to 4. The reason is that the insufﬁcient
number of pilots leads to inaccurate CSI, which affects the
optimization performance. In contrast, as shown in Fig. 8(n),
GNN-C demonstrates a more effective user association pattern
by leveraging additional location information from the images.
In Fig. 8(n), most UEs are associated with the nearest AP.
However, the user association decision forU1 does not simply
follow the nearest AP association rule. As shown in Fig. 8,
the Cartesian coordinates ofU1 are [−48.6304,−2.6822, 0.4].
The distance between U1 andB2 is 59.49, and the distance
between U1 and B3 is 60.58. Despite U1 being closer to
B2, it is associated with B3 instead. Under the max-min
objective function, this user association conﬁguration from
GNN-C can be explained. SinceB2 is already serving 2 users,
associatingU1 withB2 would likely result in a lower data
rate as compared to associating it with B3, whose load is
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 15 页

306 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
lighter. The small distance difference between U1 and the two
APs is negligible when compared to the beneﬁt of better load
balancing. Comparing the performance of GNN-C and GNN-P,
the proposed method, which integrates pilot and image data
for system optimization, provides better system conﬁgurations
than methods that rely solely on pilots.
VII. C ONCLUSION
This paper introduces a learning-based approach that inte-
grates visual images with RF pilots to solve the joint user
association and beamforming optimization problem in a down-
link wireless cellular network. The incorporation of images
enhances the channel awareness of wireless communication
systems and ensures robust system performance without rely-
ing on extensive pilot transmissions for channel estimation.
Speciﬁcally, we ﬁrst propose a detection neural network to
estimate the user locations from images. Then, we introduce a
GNN-based neural network that effectively maps the location
information derived from images and RF pilots to the opti-
mized system conﬁgurations. Simulation results demonstrate
that integrating visual data with RF signals provides superior
optimization performance compared with methods relying
solely on RF signals. The strong generalization capabilities
and low computational complexity make the proposed GNNs
suitable for real-time applications in dynamically varying user
scenarios.
REFERENCES
[1] Y . Xu, G. Gui, H. Gacanin, and F. Adachi, “A survey on resource
allocation for 5G heterogeneous networks: Current research, future
trends, and challenges,” IEEE Commun. Surveys Tuts. , vol. 23, no. 2,
pp. 668–695, 2nd Quart., 2021.
[2] S. Coleri, M. Ergen, A. Puri, and A. Bahai, “Channel estimation
techniques based on pilot arrangement in OFDM systems,” IEEE Trans.
Broadcast., vol. 48, no. 3, pp. 223–229, Sep. 2002.
[3] W. Hamilton, Z. Ying, and J. Leskovec, “Inductive representation
learning on large graphs,” in Proc. Adv. Neural Inf. Process. Syst.
(NeurIPS), vol. 30, 2017, pp. 1024–1034.
[4] D. Liu et al., “User association in 5G networks: A survey and an
outlook,” IEEE Commun. Surveys Tuts. , vol. 18, no. 2, pp. 1018–1044,
2nd Quart., 2016.
[5] A. Goldsmith, Wireless Communications. Cambridge, U.K.: Cambridge
Univ. Press, 2005.
[6] A. Mesodiakaki, F. Adelantado, L. Alonso, and C. Verikoukis, “Energy-
efﬁcient user association in cognitive heterogeneous networks,” IEEE
Commun. Mag., vol. 52, no. 7, pp. 22–29, Jul. 2014.
[7] S. Corroy, L. Falconetti, and R. Mathar, “Dynamic cell association for
downlink sum rate maximization in multi-cell heterogeneous networks,”
in Proc. IEEE Int. Conf. Commun. (ICC) , Jun. 2012, pp. 2457–2461.
[8] R. Sun, M. Hong, and Z.-Q. Luo, “Joint downlink base station
association and power control for max-min fairness: Computation
and complexity,” IEEE J. Sel. Areas Commun. , vol. 33, no. 6,
pp. 1040–1054, Jun. 2015.
[9] L. P. Qian, Y . J. A. Zhang, Y . Wu, and J. Chen, “Joint base station
association and power control via Benders’ decomposition,” IEEE Trans.
Wireless Commun., vol. 12, no. 4, pp. 1651–1665, Apr. 2013.
[10] L. P. Qian, Y . Wu, H. Zhou, and X. Shen, “Joint uplink base
station association and power control for small-cell networks with non-
orthogonal multiple access,” IEEE Trans. Wireless Commun. , vol. 16,
no. 9, pp. 5567–5582, Sep. 2017.
[11] T. Zhou, Z. Liu, D. Qin, N. Jiang, and C. Li, “User association with
maximizing weighted sum energy efﬁciency for massive MIMO-enabled
heterogeneous cellular networks,” IEEE Commun. Lett., vol. 21, no. 10,
pp. 2250–2253, Oct. 2017.
[12] R. D. Yates and C.-Y . Huang, “Integrated power control and base station
assignment,” IEEE Trans. Veh. Technol. , vol. 44, no. 3, pp. 638–644,
Aug. 1995.
[13] F. Rashid-Farrokhi, K. J. R. Liu, and L. Tassiulas, “Downlink power
control and base station assignment,” IEEE Commun. Lett., vol. 1, no. 4,
pp. 102–104, Jul. 1997.
[14] M. Sanjabi, M. Razaviyayn, and Z.-Q. Luo, “Optimal joint base station
assignment and beamforming for heterogeneous networks,” IEEE Trans.
Signal Process., vol. 62, no. 8, pp. 1950–1961, Apr. 2014.
[15] Z. Cui and R. Adve, “Joint user association and resource allocation
in small cell networks with backhaul constraints,” in Proc. 48th Annu.
Conf. Inf. Sci. Syst. (CISS) , Mar. 2014, pp. 1–6.
[16] N. Zhao, Y .-C. Liang, D. Niyato, Y . Pei, and Y . Jiang, “Deep
reinforcement learning for user association and resource allocation
in heterogeneous networks,” in Proc. IEEE Global Commun. Conf.
(GLOBECOM), Dec. 2018, pp. 1–6.
[17] H. Zhang, S. Huang, C. Jiang, K. Long, V . C. M. Leung, and H. V . Poor,
“Energy efﬁcient user association and power allocation in millimeter-
wave-based ultra dense networks with energy harvesting base stations,”
IEEE J. Sel. Areas Commun. , vol. 35, no. 9, pp. 1936–1947, Sep. 2017.
[18] D. Liu, L. Wang, Y . Chen, T. Zhang, K. K. Chai, and M. Elkashlan,
“Distributed energy efﬁcient fair user association in massive MIMO
enabled HetNets,” IEEE Commun. Lett., vol. 19, no. 10, pp. 1770–1773,
Oct. 2015.
[19] J. Jang and H. J. Yang, “A-fairness-maximizing user association in
energy-constrained small cell networks,” IEEE Trans. Wireless Com-
mun., vol. 21, no. 9, pp. 7443–7459, Sep. 2022.
[20] Y . Jia, M. Zhao, and W. Zhou, “Joint user association and eICIC for
max–min fairness in HetNets,” IEEE Commun. Lett. , vol. 20, no. 3,
pp. 546–549, Mar. 2016.
[21] K. Shen and W. Yu, “Distributed pricing-based user association for
downlink heterogeneous cellular networks,” IEEE J. Sel. Areas Com-
mun., vol. 32, no. 6, pp. 1100–1113, Jun. 2014.
[22] Z. Wang, M. Li, R. Liu, and Q. Liu, “Joint user association and hybrid
beamforming designs for cell-free mmWave MIMO communications,”
IEEE Trans. Commun. , vol. 70, no. 11, pp. 7307–7321, Nov. 2022.
[23] D. W. H. Cai, T. Q. S. Quek, C. W. Tan, and S. H. Low, “Max-
min SINR coordinated multipoint downlink transmission—Duality
and algorithms,” IEEE Trans. Signal Process. , vol. 60, no. 10,
pp. 5384–5395, Oct. 2012.
[24] Y . Tian, G. Pan, and M.-S. Alouini, “Applying deep-learning-based com-
puter vision to wireless communications: Methodologies, opportunities,
and challenges,” IEEE Open J. Commun. Soc. , vol. 2, pp. 132–143,
2021.
[25] W. Xu, F. Gao, J. Zhang, X. Tao, and A. Alkhateeb, “Deep learning
based channel covariance matrix estimation with user location and scene
images,” IEEE Trans. Commun. , vol. 69, no. 12, pp. 8145–8158, Dec.
2021.
[26] G. Charan, M. Alrabeiah, and A. Alkhateeb, “Vision-aided 6G wireless
communications: Blockage prediction and proactive handoff,” IEEE
Trans. Veh. Technol., vol. 70, no. 10, pp. 10193–10208, Oct. 2021.
[27] S. Jiang and A. Alkhateeb, “Computer vision aided beam tracking in
a real-world millimeter wave deployment,” in Proc. IEEE Globecom
Workshops, Dec. 2022, pp. 142–147.
[28] W. Xu, F. Gao, X. Tao, J. Zhang, and A. Alkhateeb, “Computer vision
aided mmWave beam alignment in V2X communications,” IEEE Trans.
Wireless Commun., vol. 22, no. 4, pp. 2699–2714, Apr. 2023.
[29] B. Lin, F. Gao, Y . Zhang, C. Pan, and G. Liu, “Multi-camera views based
beam searching and BS selection with reduced training overhead,” IEEE
Trans. Wireless Commun., vol. 72, no. 5, pp. 2793–2805, Jan. 2024.
[30] G. Charan, T. Osman, A. Hredzak, N. Thawdar, and A. Alkhateeb,
“Vision-position multi-modal beam prediction using real millimeter
wave datasets,” in Proc. IEEE Wireless Commun. Netw. Conf. (WCNC) ,
Apr. 2022, pp. 2727–2731.
[31] W. Xu, F. Gao, Y . Zhang, C. Pan, and G. Liu, “Multi-user matching
and resource allocation in vision aided communications,” IEEE Trans.
Commun., vol. 71, no. 8, pp. 4528–4543, Aug. 2023.
[32] M. Feng and S. Mao, “Interference management and user association for
nested array-based massive MIMO HetNets,” IEEE Trans. Veh. Technol.,
vol. 67, no. 1, pp. 454–466, Jan. 2018.
[33] L. Qi, M. Peng, Y . Liu, and S. Yan, “Advanced user association in
non-orthogonal multiple access-based fog radio access networks,” IEEE
Trans. Commun., vol. 67, no. 12, pp. 8408–8421, Dec. 2019.
[34] D. Zhao, H. Lu, Y . Wang, H. Sun, and Y . Gui, “Joint power allocation
and user association optimization for IRS-assisted mmWave systems,”
IEEE Trans. Wireless Commun., vol. 21, no. 1, pp. 577–590, Jan. 2022.
[35] S. Srivastava, A. V . Divekar, C. Anilkumar, I. Naik, V . Kulkarni, and
V . Pattabiraman, “Comparative analysis of deep learning image detection
algorithms,” J. Big Data , vol. 8, no. 1, p. 66, Dec. 2021.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 16 页

LI et al.: MULTIMODAL VISUAL IMAGE BASED USER ASSOCIATION AND BEAMFORMING 307
[36] Ultralytics, Frederick, MD, USA. (2020). ultralytics/yolov5: v7.0—
YOLOv5 SOTA Realtime Instance Segmentation , doi: 10.5281/
zenodo.7347926. [Online]. Available: https://github.com/ultralytics/
yolov5.com
[37] J. Weng, P. Cohen, and M. Herniou, “Camera calibration with distortion
models and accuracy evaluation,” IEEE Trans. Pattern Anal. Mach.
Intell., vol. 14, no. 10, pp. 965–980, Oct. 1992.
[38] Y . Wang, Y . Li, Q. Shi, and Y .-C. Wu, “ENGNN: A general edge-
update empowered GNN architecture for radio resource management
in wireless networks,” IEEE Trans. Wireless Commun. , vol. 23, no. 6,
pp. 5330–5344, Jun. 2024.
[39] J. Guo and C. Yang, “Learning power allocation for multi-cell-multi-
user systems with heterogeneous graph neural networks,” IEEE Trans.
Wireless Commun., vol. 21, no. 2, pp. 884–897, Feb. 2022.
[40] A. Dosovitskiy, G. Ros, F. Codevilla, A. Lopez, and V . Koltun,
“CARLA: An open urban driving simulator,” in Proc. Conf. Robot
Learn., 2017, pp. 1–16.
[41] J. Hoydis et al., “Sionna: An open-source library for next-generation
physical layer research,” 2022, arXiv:2203.11854.
[42] H. Zhang, X. Ma, X. Liu, L. Li, and K. Sun, “GNN-based power
allocation and user association in digital twin network for the terahertz
band,” IEEE J. Sel. Areas Commun. , vol. 41, no. 10, pp. 3111–3121,
Oct. 2023.
Yinghan Li (Graduate Student Member, IEEE)
received the B.S. and M.S. degrees in electronic and
information engineering from Beihang University,
Beijing, China, in 2018 and 2021, respectively. She
is currently pursuing the Ph.D. degree in electri-
cal and computer engineering with the University
of Toronto, Toronto, ON, Canada. Her research
interests include multimodal learning, wireless com-
munications, and optimization.
Yiming Liu (Graduate Student Member, IEEE)
received the M.S. degree in information and com-
munication engineering from Tongji University,
Shanghai, China, in 2022. He is currently pursuing
the Ph.D. degree in electrical and computer engi-
neering with the University of Toronto, Toronto,
ON, Canada. His research interests include commu-
nications and sensing, signal processing, information
theory, and machine learning. He was a recipient
of China National Scholarship in 2018 and 2021,
Shanghai Outstanding Graduate Award in 2022, the
HKUST Redbird Ph.D. Award in 2022, and the Connaught International
Scholarship in 2023. He was also recognized as an Exemplary Reviewer for
IEEE W IRELESS COMMUNICATIONS LETTERS in 2022.
Wei Yu (Fellow, IEEE) received the B.A.Sc. degree
in computer engineering and mathematics from the
University of Waterloo, Waterloo, ON, Canada, and
the M.S. and Ph.D. degrees in electrical engineering
from Stanford University, Stanford, CA, USA. He
is currently a Professor with the Electrical and
Computer Engineering Department, University of
Toronto, Toronto, ON, Canada, where he holds
Canada Research Chair (Tier 1) in Information The-
ory and Wireless Communications. He is a Fellow
of Canadian Academy of Engineering and a member
of the College of New Scholars, Artists, and Scientists of the Royal Society
of Canada. He received the Steacie Memorial Fellowship in 2015, the IEEE
Marconi Prize Paper Award in Wireless Communications in 2019, the IEEE
Communications Society Award for Advances in Communication in 2019, the
IEEE Signal Processing Society Best Paper Award in 2008, 2017, and 2021,
the Journal of Communications and Networks Best Paper Award in 2017, the
IEEE Communications Society Best Tutorial Paper Award in 2015, the IEEE
Communications Society and Information Theory Society Joint Paper Award
in 2024, the Frontiers of Science Award in 2024, and the R. A. Fessenden
Award from IEEE Canada in 2024. He served as the President for the IEEE
Information Theory Society in 2021 and the Chair for the Signal Processing
for Communications and Networking Technical Committee of the IEEE Signal
Processing Society from 2017 to 2018. He served as an Area Editor for IEEE
TRANSACTIONS ON WIRELESS COMMUNICATIONS , an Associate Editor for
IEEE T RANSACTIONS ON INFORMATION THEORY , and an Editor for IEEE
TRANSACTIONS ON COMMUNICATIONS and IEEE T RANSACTIONS ON
WIRELESS COMMUNICATIONS . He was an IEEE Communications Society
Distinguished Lecturer in 2015 and 2016. He is a Clarivate Highly Cited
Researcher.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:03:06 UTC from IEEE Xplore.  Restrictions apply.
