---
title: "OptiPMB Enhancing 3D Multi-Object Tracking With Optimized Poisson Multi-Bernoulli Filtering"
zotero_key: "7BGSJSQ3"
pdf_key: "DZT2R4A3"
doi: "10.1109/tits.2025.3619674"
collection: "其他"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# OptiPMB Enhancing 3D Multi-Object Tracking With Optimized Poisson Multi-Bernoulli Filtering — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
OptiPMB: Enhancing 3D Multi-Object Tracking
with Optimized Poisson Multi-Bernoulli Filtering
Guanhua Ding,Student Member, IEEE,Yuxuan Xia,Member, IEEE,Runwei Guan,Member, IEEE,
Qinchen Wu,Student Member, IEEE,Tao Huang,Senior Member, IEEE,Weiping Ding,Senior Member, IEEE,
Jinping Sun,Member, IEEE,and Guoqiang Mao,Fellow, IEEE
Abstract—Accurate 3D multi-object tracking (MOT) is cru-
cial for autonomous driving, as it enables robust perception,
navigation, and planning in complex environments. While deep
learning-based solutions have demonstrated impressive 3D MOT
performance, model-based approaches remain appealing for
their simplicity, interpretability, and data efficiency. Conven-
tional model-based trackers typically rely on random vector-
based Bayesian filters within the tracking-by-detection (TBD)
framework but face limitations due to heuristic data association
and track management schemes. In contrast, random finite set
(RFS)-based Bayesian filtering handles object birth, survival, and
death in a theoretically sound manner, facilitating interpretability
and parameter tuning. In this paper, we present OptiPMB, a
novel RFS-based 3D MOT method that employs an optimized
Poisson multi-Bernoulli (PMB) filter while incorporating several
key innovative designs within the TBD framework. Specifically,
we propose a measurement-driven hybrid adaptive birth model
for improved track initialization, employ adaptive detection
probability parameters to effectively maintain tracks for occluded
objects, and optimize density pruning and track extraction mod-
ules to further enhance overall tracking performance. Extensive
evaluations on nuScenes and KITTI datasets show that OptiPMB
achieves superior tracking accuracy compared with state-of-the-
art methods, thereby establishing a new benchmark for model-
based 3D MOT and offering valuable insights for future research
on RFS-based trackers in autonomous driving.
Index Terms—Autonomous driving, 3D multi-object tracking,
random finite set, Poisson multi-Bernoulli, Bayesian filtering.
© 2025 IEEE. Personal use of this material is permitted. Permission from
IEEE must be obtained for all other uses, in any current or future media,
including reprinting/republishing this material for advertising or promotional
purposes, creating new collective works, for resale or redistribution to servers
or lists, or reuse of any copyrighted component of this work in other works.
Digital Object Identifier 10.1109/TITS.2025.3619674
The work of Guanhua Ding, Qinchen Wu, and Jinping Sun was supported
by National Natural Science Foundation of China, Grant 62131001 and Grant
62171029.(Corresponding author: Jinping Sun.)
Guanhua Ding, Qinchen Wu, and Jinping Sun are with the School of
Electronic Information Engineering, Beihang University, Beijing 100191,
China (e-mail: buaadgh@buaa.edu.cn; wuqinchen@buaa.edu.cn; sunjinping@
buaa.edu.cn).
Yuxuan Xia is with the School of Automation and Intelligent Sensing,
Shanghai Jiaotong University, Shanghai 200240, China (e-mail: yuxuan.xia@
sjtu.edu.cn).
Runwei Guan is with the Department of Computer Science and Engineering,
The Hong Kong University of Science and Technology, Guangzhou 511455,
China (e-mail: runwayrwguan@hkust-gz.edu.cn).
Tao Huang is with the College of Science and Engineering, James Cook
University, Cairns QLD 4870, Australia. (e-mail: tao.huang1@jcu.edu.au).
Weiping Ding is with the School of Artificial Intelligence and Computer
Science, Nantong University, Nantong 226019, China, and also with the
Faculty of Data Science, City University of Macau, Macau 999078, China
(e-mail: dwp9988@163.com).
Guoqiang Mao is with Research Laboratory of Smart Driving and Intelligent
Transportation Systems, Southeast University, Nanjing 210096, China (e-mail:
g.mao@ieee.org).
I. INTRODUCTION
A
CCURATE and reliable 3D multi-object tracking is es-
sential for autonomous driving systems to enable robust
perception, navigation, and planning in complex dynamic
environments. Although deep learning has recently driven
the development of many learning-based tracking methods
[1–7], model-based approaches continue to attract significant
attention due to their simplicity and data sample efficiency.
In model-based tracking, a common design paradigm is to
employ random vector (RV)-based Bayesian filtering within
the tracking-by-detection (TBD) framework [8–16]. Specif-
ically, pre-trained detectors provide object bounding boxes,
which serve as inputs for computing similarity scores between
detections and existing objects to form an affinity matrix.
Assignment algorithms, such as greedy matching and the
Hungarian algorithm [17], then establish detection-to-object
associations. Bayesian filters (e.g., the Kalman filter) finally
update the object state vectors according to the association
result. However, because RV-based Bayesian filters estimate
each object’s state vector individually, these methods often
depend on complex heuristic data association steps and track
management schemes to effectively track multiple objects. For
example, while methods in [9, 11–16] achieve state-of-the-
art performance on large-scale autonomous driving datasets
like nuScenes [18] and KITTI [19], they employ multi-stage
data association and counter/score-based track management to
address the inherent limitation of RV-based Bayesian filters.
An important alternative design paradigm within the TBD
framework is to utilize random finite set (RFS)-based Bayesian
filtering [20–24]. Unlike conventional RV-based filters, RFS
filters model the MOT problem within a unified Bayesian
framework that naturally handles birth, survival, and death
of multiple objects. This comprehensive modeling not only
improves the interpretability of the algorithm but also facili-
tates effective parameter tuning. The Poisson multi-Bernoulli
mixture (PMBM) filter was first employed for 3D MOT in
autonomous driving scenarios [20, 21] due to its elegant
handling of detected and undetected objects. Subsequent work
[22] proposed a Poisson multi-Bernoulli (PMB) filter utilizing
the global nearest neighbor (GNN) data association strategy
as an effective approximation of the PMBM filter, which
improves computational efficiency and simplifies parameter
tuning. However, existing PMBM/PMB-based trackers [20–
22] with standard modeling assumptions may still experience
performance degradation in complex environments. This mo-
tivates the need for innovative algorithm designs tailored for
arXiv:2503.12968v2  [cs.CV]  3 Feb 2026

2
k - 1
k
Xk
Time Step
Time Step
Xk -1
State Set
Zk -1 Zk
Measurement Set
Raw 
Observation
Object
Detector
False Detection
() xn
() zn
Miss Detection
k -1
k
Xk
Time Step
Time Step
Xk -1
State Set
Zk -1 Zk
Measurement Set
Raw 
Observation
Object
Detector
False Detection
() xn
() zn
Miss Detection
1 1: 1(| )kkf −−XZ
1:(| )kkf XZRFS-BasedTracker
Multi-Object Posterior Density
Fig. 1. Illustration of the RFS-based 3D MOT system model. The top section
displays bounding boxes in different colors, representing tracks with distinct
IDs estimated by the RFS-based tracker.
practical autonomous driving scenarios that pushes the limits
of RFS-based 3D MOT methods.
To this end, a novel OptiPMB tracker is proposed in this
paper. The main contributions are summarized as follows:
•We provide a systematic analysis of the RFS-based 3D
MOT framework and introduce the OptiPMB tracker,
which achieves superior performance in tracking accuracy
and track ID maintenance compared with previous RFS-
based trackers in autonomous driving scenarios.
•Within the OptiPMB tracker, we propose a novel hybrid
adaptive birth model for effective track initialization in
complex environments. Additionally, we employ adaptive
detection probability parameters to enhance track main-
tenance for occluded objects, and optimize the density
pruning and track extraction modules to further boost
tracking performance.
•The OptiPMB tracker is comprehensively evaluated and
compared with other advanced 3D MOT methods on
the nuScenes [18] and KITTI [19] datasets. Our method
achieves state-of-the-art performance on the nuScenes
tracking challenge leaderboard with 0.767 AMOTA score,
which establishes a new benchmark for model-based
online 3D MOT and motivates future research on RFS-
based trackers in autonomous driving.
The rest of the paper is organized as follows. Related works
are reviewed in Section II. The basic concepts of RFS-based
3D MOT are introduced in Section III. Details of our proposed
OptiPMB tracker are illustrated in Section IV. We evaluate and
analyze the performance of OptiPMB on nuScenes and KITTI
datasets in Section V. Finally, Section VI concludes the paper.
II. RELATEDWORKS
A. Model-Based 3D Multi-Object Tracking Methods
1) TBD with RV-Based Bayesian filter:AB3DMOT [8]
establishes an early open-source baseline for 3D MOT on
autonomous driving datasets by adopting the TBD framework,
which performs tracking with object bounding boxes estimated
by pre-trained object detectors. It employs the Hungarian algo-
rithm [17] for detection-to-object association and the Kalman
filter (KF) to estimate object state vectors, thereby forming a
simple model-based paradigm that integrates TBD with RV-
based Bayesian filters. Building upon this paradigm, subse-
quent works have enhanced tracking performance by intro-
ducing multi-stage data association [10, 11, 13–16], exploiting
diverse features to measure affinities between detections and
objects [25, 26], and incorporating multiple sensing modalities
[9, 12, 16, 27–30]. For example, MCTrack [15] performs two-
stage matching on both the bird-eye’s-view (BEV) plane and
the range view plane, thereby reducing false positives and ID
switch errors when using low-quality detections. EMMS-MOT
[16] leverages spatial synergies between 3D and 2D detection
boxes by jointly estimating 3D and 2D motion states with KF
and adopting a three-stage data association strategy. Moreover,
alternative association methods, including joint probabilistic
data association [31, 32] and multiple hypothesis tracking [33],
have also been explored within this paradigm.
2) TBD with RFS-Based Bayesian filter:Unlike conven-
tional RV-based Bayesian filters, RFS-based filters model the
collection of object states as a set-valued random variable,
providing a mathematically rigorous framework to handle
uncertainties in object existence, births, and deaths. An early
attempt to utilize an RFS-based Bayesian filter within the TBD
framework for 3D MOT is proposed in [20], where the PMBM
filter is used to estimate object trajectories from monocular
camera detections. RFS-M 3 [21] further extends the PMBM
filter to LiDAR-based 3D MOT by using 3D bounding boxes
as inputs. To improve efficiency and simplify parameter tuning,
[22] combines the PMB filter with GNN data association,
proposing a simple yet effective GNN-PMB tracker. Other
RFS-based Bayesian filters, such as the probability hypothesis
density and labeled multi-Bernoulli filters, are also explored
for 3D MOT applications [23, 24].
3) JDT with MEOT:While the TBD framework relies on
object detectors to provide inputs for trackers, multi-extended
object tracking (MEOT) methods under the joint-detection-
and-tracking (JDT) framework can simultaneously estimate
the motion, shape, and size of objects directly from raw
point cloud measurements, reducing the reliance on accurate
3D bounding box detections. Different statistical modeling
of geometrically extended objects are utilized by RFS-based
filters to achieve 3D MEOT in [34–36]. Additionally, camera
images are used to improve point cloud clustering quality and
data association accuracy for 3D MEOT in [37, 38].
B. Learning-Based 3D Multi-Object Tracking Methods
1) TBD with Learning-Assisted Data Association:The
classical strategy to enhance model-based 3D MOT with
neural networks is employing learning-assisted data associa-
tion. In this approach, feature embeddings captured by neural
networks serve as an additional cue to construct the affinity
matrix, which is subsequently processed by conventional data
association methods, such as greedy matching [1, 3, 39–41]
and multi-stage Hungarian algorithm [2, 42, 43]. Object states
are then estimated by the Kalman filter based on association

3
results. For example, DINO-MOT [43] leverages the DINOv2
encoder to extract visual features of pedestrians and refines the
association results by computing cosine similarities between
embeddings. Similar strategies are also applied to RFS-based
filters [44, 45], where learned embeddings complement the
belief propagation messages to enhance the probabilistic data
association.
2) Learning-Based JDT:Recent advances in learning-based
JDT methods leverage neural networks to simultaneously
detect objects and establish associations across frames. For
instance, GNN3DMOT [46] employs a graph neural network
that fuses 2D and 3D features to capture complex spatial
relationships, while Minkowski Tracker [5] utilizes sparse
spatial-temporal convolutions to efficiently perform JDT on
point clouds. Other approaches combine cross-modal cues
from cameras and LiDAR [47, 48] or incorporate probabilistic
and geometric information [49, 50]. Transformer-based meth-
ods [4, 51, 52] further enhance performance by capturing
long-range dependencies through attention mechanisms. These
learning-based JDT approaches often offer improved accuracy
and robustness in complex autonomous driving scenarios,
but non-learnable assignment algorithms are still required to
obtain the hard association results.
C. End-to-End Learnable 3D Multi-Object Tracking Methods
1) Learnable Data Association Module:Although neural
networks have been utilized in learning-based 3D MOT, the
non-differentiable assignment modules could hinder fully data-
driven training of the tracker and subsequent networks. An
intuitive solution is using learnable modules for data associa-
tion. For instance, RaTrack [53] replaces the Hungarian algo-
rithm with a differentiable alternative, proposing an end-to-end
trainable tracker for 4D radars. SimTrack [54] eliminates the
heuristic matching step by utilizing a hybrid-time centerness
map to handle object birth, death, and association.
2) Tracking-by-Attention:The tracking-by-attention strat-
egy was initially proposed for 2D MOT [55, 56] and has
been extended to the 3D domain in recent studies [6, 7, 57].
The core idea is to represent objects with dedicated variable
queries learned from data. In each frame, new birth queries
with unique IDs are generated and subsequently propagated as
existing object queries, thus enabling the network to implicitly
handle data association with label assignment rules during
training. This approach facilitates end-to-end optimization and
makes such transformer-based trackers a key component in
recent autonomous driving pipelines [58, 59].
III. RFS-BASED3D MOT REVISITED
A. Basic Concept and Notation
In this section, we introduce the fundamental concepts
and notations of RFS-based 3D MOT. For a 3D object, the
state vectorx∈R nx usually consists of motion states (e.g.,
position, velocity, acceleration, turn rate) and extent states
(e.g., shape, size, and orientation of the object bounding box).
Under the RFS framework illustrated in Fig. 1, the multi-object
state is defined by a finite setX∈ F(R nx ), whereF(R nx )
is the space of all finite subsets of the object state spaceR nx.
Assuming thatN k objects exist at time stepk, then the multi-
object state can be represented asX k ={x 1k,x 2k, ...,xNkk },
whose cardinality (the number of elements) is|X k|=N k.
In autonomous driving applications, raw observations of the
objects (e.g., camera images, LiDAR and radar point clouds)
are often preprocessed by detectors to obtain bounding boxes,
enabling the trackers to perform MOT using these detections
under the TBD framework. Since TBD-based 3D MOT meth-
ods were proven to be simple and effective in many previous
studies, we employ the TBD framework in this paper and
assume that the measurement of an object is a bounding box
detection. At time stepk, assume that the objects are observed
by a set of measurementsZ k ={z 1k,z 2k, ...,zMkk } ∈ F(Rnz ).
Each measurementz k ∈R nz is a bounding box detected
from raw observations which contains measured object states
such as position, velocity, size, and orientation. The collection
of measurement sets from time step1tokis denoted by
Z1:k.In practical scenarios, some objects can be misdetected,
and the set of measurementsZoften consists of not only true
object detections but also false detections (clutter), as shown
in Fig. 1. The ambiguous relation between the objects and the
measurements increases the complexity of 3D MOT, while the
RFS-based Bayesian filtering aims to provide an effective and
rigorous solution to the multi-object state estimation problem.
B. Key Random Processes
There are three important RFSs widely used in MOT system
modeling, which are the Poisson point process (PPP) RFS,
the Bernoulli RFS, and the multi-Bernoulli RFS. A PPP
RFSXhas Poisson-distributed cardinality and independent,
identically distributed elements, which can be defined by the
probability density function
f ppp(X) =e −µ Y
x∈X
µp(x) =e −
R
λ(x)dx Y
x∈X
λ(x).(1)
Here,µis the Poisson rate of cardinality,p(x)is the spatial
distribution of each element, and the intensity functionλ(x) =
µp(x)completely parametrizesX. Due to its simplicity, the
PPP RFS is often used to model undetected objects, newborn
objects, and false detections in RFS-based trackers.
A Bernoulli RFSXcontains a single element with prob-
abilityror is empty with probability1−r. The probability
density function ofXis given by
f ber(X) =



1−rX=∅
rp(x)X={x}
0|X| ≥2.
(2)
The Bernoulli RFS can be used to model the state distribution
and the measurement likelihood function of an object.
A multi-Bernoulli RFSXis a union ofNindependent
Bernoulli RFSsX i, i.e.,X= SNi=1 Xi, whose probability
density function is defined by
f mb(X) =
(P
⊎i∈IXi=X
Q
i∈I f ber(Xi)|X| ≤N
0|X|> N (3)
whereI={1, ..., N}is an index set for the Bernoulli RFSs,
and⊎ i∈IXi =Xdenotes thatXis the union of mutually

4
disjoint subsets{X i}. The multi-Bernoulli RFS can be applied
for modeling states of multiple objects.
C. Bayesian Filtering with Conjugate Prior Densities
The goal of the RFS-based Bayesian filter is to recursively
estimate the multi-object posteriorf(X k|Z1:k), from which
the state of each object can be extracted. A Bayesian filtering
recursion includes a prediction step followed by an update
step. In the prediction step, the posterior density in the last
time step is predicted to the current time step by the Chapman-
Kolmogorov equation [60]
f(X k|Z1:k−1) =
R
g(Xk|Xk−1)f(X k−1|Z1:k−1)δXk−1 (4)
whereg(X k|Xk−1)is the multi-object state transition density.
Under conventional MOT assumptions of the RFS framework
[22, 60–62], an object with statex k−1 survives from time step
k−1tokwith probabilityp s(xk−1), and its state transits with
g(xk|xk−1). The newborn objects are modeled by a PPP RFS
with intensityλ b(·).
In the update step, the predicted densityf(X k|Z1:k−1)is
updated using the information of measurementsZ k. Given
the multi-object measurement likelihoodh(Z k|Xk), the multi-
object posterior can be calculated by Bayes’ rule [60]
f(X k|Z1:k) = h(Zk|Xk)f(X k|Z1:k−1)R h(Zk|Xk)f(X k|Z1:k−1)δX .(5)
Here, the physical process of objects generating measurements
is modeled in the likelihood functionh(Z k|Xk). Based on
the conventional assumptions, each object is detected with
probabilityp d(xk), and a detected object generates a measure-
ment according to the single-object measurement likelihood
h(zk|xk). The false detections (clutter) are assumed to follow
a PPP RFS with intensityλ c(·).
Conjugate prior densities are essential for efficient Bayesian
filtering, as such densities can preserve the same mathematical
form throughout filtering recursions. PMBM [60] andδ-
generalized labeled multi-Bernoulli (δ-GLMB) [62] are two
multi-object conjugate prior densities widely used in RFS-
based Bayesian filters. In this research, we adopt a simplified
form of the PMBM density, known as the PMB density, for
use in our proposed OptiPMB tracker.
IV. OPTIPMB TRACKER: IMPROVING THEPERFORMANCE
OFRFS-BASED3D MOT
In this section, we provide a detailed illustration of our
OptiPMB tracker and explain how its innovative designs and
modules enhance the performance of RFS-based 3D MOT.
The overall pipeline of the OptiPMB tracker is depicted in
Fig. 2, with a comprehensive description of each component
presented below.
A. Single-Object State Transition and Measurement Model
Before delving into the 3D MOT pipeline, it is necessary to
define the object state transition and measurement models. As
an RFS-based tracker, OptiPMB represents the multi-object
state as a set of single-object state vectors,X={x i}i∈I,
where eachx∈Xis defined as:
x= [x TM,x TA,x TU, xcnt, xlen, xs]T (6)
wherex M = [x, y, v, ϕ, ω, a]T,x A = [α, β, γ, ζ]T, andx U =
[c, t]T. The motion statex M comprises the object’s position on
the BEV plane(x, y), velocityv, heading angleϕ, turn rateω,
and accelerationa. The auxiliary statex A includes the length
α, widthβ, and heightγof the object bounding box as well
asζ, the object’s position along thez-axis. The time-invariant
statex U contains the object classcand track IDt. Finally,x cnt
records the number of consequent misdetections for this object,
xlen records the number of time steps the object has survived,
xs is a confidence score utilized in certain evaluation metrics.
It is worth noting that only the motion statex M is estimated
by Bayesian filtering recursions, while the non-motion states
(xA,x U, xcnt, xlen, xs)are processed by a light-weight filter
(see Section IV-F for details).
Accurate modeling of object motion is crucial for achieving
high tracking performance. In OptiPMB, the constant turn rate
and acceleration (CTRA) model [63] is employed to predict
the object’s motion state, formulated by
xM,k = ΓCTRA(xM,k−1) +v k (7)
whereΓ CTRA(·)denotes the nonlinear dynamic function of
the CTRA model (see [63, Section III-A]),v k ∼ N(0, Qk)is
Gaussian-distributed process noise. Unscented transform (UT)
[64] is applied to handle the nonlinear functions, and we have
the motion state transition density
g(xM,k|xM,k−1) =N(x M,k;m k|k−1, Pk|k−1)
Pk|k−1 = ¯Pk|k−1 +Q k
(mk|k−1, ¯Pk|k−1) = UT[ΓCTRA(·),m k−1, Pk−1].
(8)
Here,m k−1 andP k−1 denote the posterior mean and covari-
ance of the motion state, i.e.,x M,k−1 ∼ N(mk−1, Pk−1).
The transformationUT[Γ(·),m, P]computes the mean and
covariance projected through the nonlinear functionΓ(·). The
non-motion states remain unchanged in the transition model.
The survival probability is simplified as a predefined constant
dependent only on the object’s class, i.e.,p s(c).
In the TBD framework, removing false detections generated
by the object detector helps reduce false tracks and improves
computational efficiency [10, 22]. To achieve this, OptiPMB
employs a per-class score filter and non-maximum suppression
(NMS) for detection preprocessing [22]. Specifically, bounding
boxes with detection scores belowη sf are removed, and NMS
is applied for overlapping boxes with intersection over union
(IoU) [65] exceedingη iou. After preprocessing, the remaining
detections form the measurement setZ={z m}m∈M, where
each measurementz∈Zis defined by
z= [z TM,z TA, zc, zs]T (9)
wherez M = [zx, zy, zvx, zvy , zϕ]T andz A = [zα, zβ, zγ, zζ]T.
Here,z M is the observation of the object’s motion state, while

5
Adaptive pd(x+)
Off-the-Shelf
3D Object Detector
PMB Pruning
MisdetectedPredict ppp
11
u
:(| )kkf −XZppp u 1 11 :(| )kkf −−XZ uppp 1:(| )kkf XZ
Detected
Undetected Objects
Detection Preprocessing
Association Cost MatrixScore Filter NMS
1 11−−XZ :(| )kkf
Multi-Object State
Posterior Density
Misdetected
Detected
Predict mb
11
d
:(| )kkf −XZdmb 1 11 :(| )kkf −−XZ
Detected Objects
dmb
1:(| )kkf XZ
Hybrid Adaptive Birth Model
New PPP New Bernoulli
Data Association
Hungarian Algorithm
Most Likely Global Data 
Association Hypothesis
Adaptive Detection Probability
PMB Density Prediction and Update
1XZ :(| )kkf Track Extraction
Estimated Object Tracks
Redundant PPP Pruning
Bernoulli Pruning
Existence Probability Filter
Misdetection Counter
Object State Extraction
Raw Sensor Data
3D Bounding Boxes
Zk
(Section IV-G1) (Section IV-G2) (Section IV-H1)
(Section IV-H2)
Light-Weight Filter &
Track ID Assignment
Update
Occlusion Status 
Estimation
Fig. 2. Overall pipeline of the proposed OptiPMB tracker. Compared to the previous state-of-the-art PMB filter-based 3D MOT method [22], the innovative
differences and improvements of OptiPMB are highlighted in distinct colors.Yellowdenotes adaptive designs to improve the robustness of the tracker (see
Section IV-G for details).Greendenotes algorithm modules optimized for better tracking performance (see Section IV-H for details).
zA denotes the observation of the object’s auxiliary state. The
motion measurement model is given by
zM,k = H(xM,k) +w k
= [xk, yk, vk cosϕ k, vk sinϕ k, ϕk]T +w k (10)
wherew k ∼ N(0, Rk)is Gaussian measurement noise. Since
the object’s non-motion states are not estimated by Bayesian
filtering, we simply assumez A,k =x A,k andz c,k =c k. The
detection score of the measurementz k is denoted byz s,k ∈
(0,1], which is provided by the 3D object detector.
B. Basic Framework: Bayesian Filtering with PMB Density
The OptiPMB tracker is built upon the basic framework of
a PMB filter, which represents the multi-object state with a
PMB RFS and propagates its probability density through the
Bayesian filtering recursions outlined in Section III-C. Unlike
the PMBM filter [60], which maintains multiple probable
global data association hypotheses 1, the PMB filter selects
and propagates only the best global hypothesis. Consequently,
when properly designed and parameterized, the PMB filter can
achieve higher computational efficiency without compromising
3D MOT performance [22].
The OptiPMB tracker defines the multi-object posterior
density as follows
f(X k|Z1:k) =
X
Xuk⊎Xdk=Xk
f ppp(Xuk|Z1:k)f mb(Xdk|Z1:k)(11)
where the multi-object state is modeled as a union of two
disjoint subsets, i.e.,X uk ⊎X dk =X k. The PPP RFSX uk
denotes the state ofpotential objects which have never been
detected, while the MB RFSX dk denotes the state ofpotential
objects which have been detected at least once. This parti-
tion of detected and undetected objects enables an efficient
hypotheses management of potential objects [60, 61].
1The discussion on global and local hypotheses could be found in the
following content of this sub-section.
According to the definitions in Section III-B, the posterior
PMB density at time stepk−1,f(X k−1|Z1:k−1), can be fully
determined by a set of parameters
λuk−1,{(r ik−1, pik−1)}i∈Ik−1 .(12)
Here,λ uk−1(·)is the intensity of the PPP RFSX uk−1. Based
on our system modeling in Section IV-A, the PPP intensity
λuk−1(·)is a weighted mixture of Gaussian-distributed Poisson
components, defined as
λuk−1(x) = PN uk−1n=1 µu,nN(x;m u,nk−1, Pu,nk−1)(13)
whereµ u,n,m u,nk−1, andP u,nk−1 represent the weight, motion
state mean, and motion state covariance of then-th Poisson
component, respectively. The MB RFSX dk−1 consists of a set
of Bernoulli components, represented by{(r ik−1, pik−1)}i∈Ik−1
in (12). Thei-th Bernoulli component,X ik−1, is characterized
by existence probabilityr ik−1 and Gaussian spatial distribution
pik−1 ∼ N(mik−1, Pik−1). To improve the clarity of hypotheses
management, OptiPMB employs the track-oriented hypothesis
structure [22, 60], defining the MB index set as
Ik−1 = SN dk−1n=1 Lnk−1 (14)
whereN dk−1 denotes the number of previously detected po-
tential objects, andL nk−1 is the index set for the local data
association hypotheses of then-th potential object.
Alocal hypothesisrepresents the scenario where an object
either generates a measurement or is misdetected at the current
time step. As illustrated in Fig. 3, consider a case with
two previously detected potential objects,{x 1,x 2}, and three
measurements,{z 1,z 2,z 3}. According to the assumptions and
system modeling in Section III and IV-A, three types of local
hypotheses can then be identified:
•Misdetection Hypotheses:{l 0,1, l0,2}, corresponding to
objects{x 1,x 2}being misdetected (i.e., associated with
a dummy measurementz 0).
•Detection Hypotheses:{l m,n|n= 1,2;m= 1,2,3},
corresponding to cases where a previously detected po-
tential object is detected at the current time step and
generates one of the measurements.

6
New Objects
1z
2z
1x
2x
3z
1x
2x
3x
4x
5x
0z 1z 2z 3z
10,w 11,w 12,w 13,w
20,w 21,w 22,w 23,w
∞∞31,w∞
∞
∞
∞ 42,w ∞
53,w∞∞
New 
Objects
Misdetection
Cost Matrix
Previously Detected Objects 
& Measurements
1z
2z
1x
2x
3z
0z
1z
2z
3z
1x 2x 3x 4x
01,w 02,w
21,w
31,w
11,w 12,w
22,w
32,w
∞
∞13,w
∞
∞
∞∞
24,w
∞ 35,w∞
∞
Misdetection
Cost Matrix
Previously Detected Objects 
& Measurements
5x
New Objects
1z
2z
1x
2x
3z 0z
1z
2z
3z
1x 2x 3x 4x
01,l 02,l
21,l
31,l
11,l 12,l
22,l
32,l
13,l
24,l
35,l
Misdetection
Local Data Association Hypotheses
Objects and Measurements
5x
21,w
31,w
11,w 12,w
22,w
32,w
∞
∞13,w
∞ 24,w
∞ 35,w∞
∞
Cost Matrix
Fig. 3. Cost matrix and local data association hypotheses. The misdetection,
detection, and first-time detection hypotheses are highlighted in orange, green,
and blue, respectively. Cost matrix entries with infinity values represent
impossible association hypotheses.
•First-Time Detection Hypotheses:{l 1,3, l2,4, l3,5}, in-
dicating that the measurements originate from newly
detected objects or clutter, corresponding to new potential
objects{x 3,x 4,x 5}.
These three types of local hypotheses cover all possible data
associations between objects and measurements. Aglobal
hypothesisconsists of a set of local hypotheses that are
compatible with the system modeling, defining a valid as-
sociation between all objects and measurements. For exam-
ple,{l 0,1, l2,2, l1,3, l3,5}is a valid global hypothesis, while
{l1,1, l1,2, l3,2}is invalid, because it violates the constraint
that a measurement must associate with one and only one
potential object. Since OptiPMB only maintains the best global
data association hypothesis over time, each detected potential
object retains a single local hypothesis that is included in the
global hypothesis, while all other local hypotheses are pruned
after the PMB update. Therefore, the local hypothesis index set
of then-th detected potential object is defined asL nk−1 ={n}.
Details on local hypothesis management are in Section IV-D.
As illustrated in Fig. 2, at the subsequent time stepk,
the PMB densityf(X k−1|Z1:k−1)is first propagated through
the prediction step and then updated using the preprocessed
object detections. The situation that previously undetected
potential objects remain undetected at the current time step
is also considered within this pipeline (see Section IV-D3)
alongside the three types of local hypotheses. Following the
PMB prediction and update, the data association module
determines the optimal global data association hypothesis,
which is then utilized as protocol for the pruning module
to eliminate redundant PPP and Bernoulli components from
the PMB density. Next, the non-motion states (including track
IDs) of detected potential objects are determined by a light-
weight filter. Finally, the estimated posteriorf(X k|Z1:k)is
processed by the track extraction module to generate the object
tracks. The details of our OptiPMB tracker are explained in
the following subsections, where the time subscriptk|k−1is
abbreviated as+for simplicity. Pseudo code for the complete
OptiPMB recursion is provided in Algorithm 1.
Algorithm 1:Pseudo Code of OptiPMB
Input:Parameters of the PMB posterior at the previous time step
λuk−1,{(r ik−1, pik−1)}i∈Ik−1 , LiDAR point cloud, anddetected object 3D bounding boxes at the current time step.
Output:Estimated object tracks at current time stepk.
1Note:The subscript+is the abbreviation ofk|k−1. All detection
probabilityp d(x+)are adaptively determined (see Section IV-G1).
2/* PMB prediction (see Section IV-C) */
3forn∈ {1, ..., Nuk−1}do// PPP prediction
4Computem u,n+ , Pu,n+ fromm u,nk−1, Pu,nk−1 using (8);
5Computeλ u+ fromm u,n+ , Pu,n+ , µu,nk−1 using (15);
6fori∈I k−1 do// MB prediction
7Computem i+, Pi+ fromm ik−1, Pik−1 using (8);
8Computer i+, pi+ fromm i+, Pi+ using (16);
9/* PMB update (see Section IV-D) */
10Preprocess detected object 3D bounding boxes, obtain the
measurement setZ k;
11forn∈ {1, ..., Ndk−1}do// Iterate over previously detected
potential objects
12 ˆLnk ← {(0, n)};// Create misdetection hypothesis
13Computer 0,nk , p0,nk fromr n+, pn+ using (17);
14Perform gating withr n+, pn+, obtain the gate area for then-th
potential object;
15forz mk ∈Z k do
16ifz mk is in the gatethen
17 ˆLnk ← ˆLnk ∪ {(m, n)};// Create detection hypothesis
18Computer m,nk , pm,nk , wm,nk fromr n+, pn+,z mk using
(18);
19Initialize:M lowk ← ∅;
20forz mk ∈Z k do// Iterate over measurements
21n←N dk−1 +m, ˆLnk ← {(m, n)};// Create first-timedetection hypothesis
22Obtain the gate area ofz mk ;
23Fromλ u+, obtain the index setJ mk for Poisson components
inside the gate ofz mk ;
24ifJ mk ̸=∅then// Associate with undetected potential objects
25λ← Pj∈Jmk µu,j ps(cu,j )N(x;m u,j+ , Pu,j+ );
26forj∈J mk do
27Computee j , pj fromz mk , λusing (24);
28Computer m,nk , pm,nk , wm,nk from{(e j , pj )}j∈Jmk using(23);
29else// HABM (see Section IV-G2)
30Computep a(zmk )using (38);
31ifz ms,k < ηscore then// Low-score measurement
32Computer m,nk , wm,nk using (35);
33M lowk ←M lowk ∪ {m};
34else// High-score measurement
35Computer m,nk , pm,nk , wm,nk using (37);
36 ˆN dk ←N dk−1 +|Z k|, ˆIk ← ⊎ˆN dkn=1 ˆLnk ;
37Computeλ bk from{[z mk , pa(zmk )]}m∈Mlowk using (40);
38Compute ˆλuk fromλ u+, λbk with (28);// PPP update
39/* Data association and PMB pruning (see Section IV-E and Section
IV-H1) */
40From{w m,nk }, construct the cost matrixW;
41Obtain the optimal global hypothesis fromWwith the Hungarian
algorithm;
42Prune redundant Bernoulli and Poisson components from the
updated PMB density ˆλuk,{(r ik, pik)}i∈ˆIk ;
43/* Light-weight filtering (see Section IV-F) */
44Update non-motion states with the light-weight filter;
45Reconstruct MB and PPP densities with (32) and (33), obtain the
posterior PMB densityλ uk,{(r ik, pik)}i∈Ik ;
46/* Track extraction (see Section IV-H2) */
47Fromλ uk,{(r ik, pik)}i∈Ik , extract the object tracks at the currenttime step.

7
C. PMB Density Prediction
In the PMB prediction step, the posterior PPP intensity
is predicted as a Gaussian mixture according to the state
transition model in Section IV-A. Specifically, we have
λu+(x) = PN uk−1n=1 µu,n+ N(x;m u,n+ , Pu,n+ )
µu,n+ =µ u,nk−1ps(cu,n) (15)
where the predicted meanm u,n+ and covarianceP u,n+ of
then-th Poisson component is obtained from (8). Note that
OptiPMB does not introduce the birth intensityλ b(·)during
the prediction step, as is done in conventional PMBM/PMB
implementations [20–22, 60]. Instead, object birth is managed
in the update step using the newly proposed adaptive birth
model (see Section IV-G2 for details).
The predicted MB density is parameterized by the existence
probability and spatial distribution of Bernoulli components,
i.e.,{(r i+, pi+)}i∈I+, where
(
ri+ =r ik−1ps(ci)
pi+(x) =N(x;m i+, Pi+). (16)
The predicted meanm i+ and covarianceP i+ of thei-th
Bernoulli component are also calculated by (8). The MB index
set and local hypotheses index sets remain unchanged during
the PMB prediction, i.e.,I + =I k−1,{L n+}={L nk−1}.
D. PMB Density Update
In the PMB update step, OptiPMB enumerates local data as-
sociation hypotheses (defined in Section IV-B) and update the
predicted PMB density using Bayes’ rule. Update procedures
for each type of local hypothesis are described as follows.
1) MB Update for Misdetection and Detection Hypotheses:
After PMB prediction, misdetection and detection hypotheses
are generated for previously detected potential objects, which
are characterized by the predicted MB density{(r i+, pi+)}i∈I+.
As discussed in Section IV-B, then-th previously detected
potential object retains only one local hypothesis indexed by
n. The corresponding Bernoulli componentX n+ represents
the predicted object state with the existence probabilityr n+
and spatial distributionp n+(·)defined in (16). A misdetection
hypothesisl 0,nk is first generated as [60]
(
r=
rn+(1−pd(xn+))
1−rn++rn+(1−pd(xn+))
p(x) =p n+(x) (17)
where(r, p)are the parameters of the corresponding Bernoulli
component. Next, class gating is applied to select measure-
ments belonging to the same class as the object. Distance gat-
ing is then performed to identify measurements that fall within
a predefined distanceη dist from the object. Each measurement
zmk that falls within the gate of the object generates a detection
hypothesisl m,nk , defined as [60]


w=−ln
rn+pd(xn+)N(z mxy,k ;ˆznk ,Snk )
1−rn++rn+(1−pd(xn+))
r= 1
p(x) =N(x;m m,nk , Pm,nk )
(18)
wherewis the association cost,z mxy,k = [z mx,k, zmy,k]T is
the position measurement, ˆznk andS nk denote the mean and
covariance of the predicted position measurement. Real-world
data indicates that measured object velocity and heading
are often inaccurate and noisy, leading to fluctuations in
association costs. To mitigate the impact of outlier measure-
ments, OptiPMB employs a simplified measurement model for
computing association costs, which relies solely on position
information. The measurement model is formulated as
zxy,k =H xyxM,k +w xy,k
Hxy =

1 0 0 0 0 0
0 1 0 0 0 0
 (19)
wherew xy,k ∼ N(0, Rxy,k),R xy,k corresponds to the upper-
left2×2sub-matrix of the full covariance matrixR k. Con-
sequently, the mean and covariance of the predicted position
measurement in (18) are computed by
(
ˆznk =H xymn+
Snk =H xyP n+H Txy +R xy,k. (20)
Notably, (19) is used solely for calculating association costs,
whereas the complete measurement model (10) is applied in
the unscented Kalman filter (UKF) [64] to update the object’s
motion state. With measurementz mk , the motion state mean
mm,nk and covarianceP m,nk in (18) are updated as
(mm,nk , Pm,nk ) = UKF[H(·),m n+, Pn+,z mk , Rk].(21)
After generating all possible misdetection and detection
local hypotheses for then-th object, the index set of these
new local hypotheses is defined by
ˆLnk ={(0, n)} ∪ {(m, n)|m∈Mnk )}, n= 1, ..., Ndk−1 (22)
where(0, n)indexes the misdetection hypothesis,{(m, n)}
denote the indices for detection hypotheses,M nk is the index
set for measurements within the gate of then-th object.
2) MB Update for First-Time Detection Hypotheses:For
each measurement, a newly detected potential object is created
and a first-time detection hypothesis is generated for this
new object. Since the PPP components represent undetected
potential objects, if at least one Poisson component falls within
the gate of a measurementz mk , then the first-time detection
hypothesisl
m,N dk−1+m
k is generated as [60]



w=−ln[e+λ c(zmk )]
r=e/[e+λ c(zmk )]
p(x) = 1e Pj∈Jmk ejpj(x) (23)
where



e= Pj∈Jmk ej
ej =µ u,j+ pd(xu,j+ )N(z mxy,k; ˆzu,jk , Su,jk )
pj(x) =N(x;m m,jk , Pm,jk )
(24)
and the setJ mk denotes the indices of Poisson components
that fall inside the gate ofz mk . The clutter intensityλ c(·)is
characterized by a clutter rate parameterµ c(·)predefined for

8
each object class and a uniform spatial distributionp uni(·)over
the region of observation, i.e.,
λc(zmk ) =µ c(zmc,k)puni(zmxy,k) =µ c(zmc,k)/A(25)
whereAdenotes the area size of the observation region. The
mean and covariance of the predicted position measurement,
(ˆzu,jk , Su,jk ), as well as the updated mean and covariance of the
motion state,(m m,jk , Pm,jk ), are calculated in a manner similar
to (20) and (21). The updated densityp(x)is approximated as
a single Gaussian density via moment matching [60]. The de-
tection probabilityp d(x+)is adaptively determined based on
the object’s occlusion status, as further elaborated in Section
IV-G1. If no Poisson component falls inside the measurement’s
gate, the measurement is processed using the proposed hybrid
adaptive birth model (HABM) to determine the hypothesis
parameters(w, r, p). The HABM also adaptively generates
λbk(·)based on current measurements to model the undetected
newborn objects. Details of the HABM are in Section IV-G2.
The local hypothesis index set for each new object is
ˆLnk ={(n−N dk−1, n)}, n=N dk−1 +1, ..., Ndk−1 +Mk.(26)
After enumerating all possible local hypotheses, the index set
of the updated MB density is represented as
ˆIk = S ˆN dkn=1 ˆLnk (27)
where the number of detected potential objects increases by
the number of measurements, i.e., ˆN dk =N dk−1 +M k.
3) PPP Update:The updated PPP intensity for undetected
potential objects can be simply expressed as [60]
ˆλuk(x) = P ˆN ukn=1 µu,nk N(x;m u,nk , Pu,nk )
= PN uk−1n=1 µu,n+ pd(xu,n+ )N(x;m u,n+ , Pu,n+ ) +λ bk(x) (28)
since no measurement update is applied to its components.
E. Data Association and PMB Pruning
In the PMB update procedure, the association costswfor
each detection and first-time detection local hypothesis are
calculated, forming a cost matrix, as shown in Fig. 3. The
optimal global data association hypothesis, which minimizes
the total association cost while assigning each measurement
to a detected potential object, is determined from this cost
matrix using the Hungarian algorithm [22, 60]. To reduce
the computational complexity of data association, OptiPMB
employs gating to eliminate unlikely hypotheses and set the
corresponding association costs to infinity. After the data
association, Bernoulli components that are not included in
the optimal global hypothesis or determined as clutter by the
HABM are removed to reduce unnecessary filtering computa-
tion. If no Bernoulli component belongs to a detected potential
object after pruning, the object is then removed. The redundant
Poisson components are also pruned to reduce false tracks and
ID switch errors. See Section IV-H1 for details of PPP pruning.
F . Light-Weight Filter for Non-Motion States
As discussed in Section IV-A, the non-motion states of an
object are processed using a light-weight filter to enhance
computational efficiency. Specifically, when a newly detected
potential object is created from a measurementz mk , the time-
invariant state is determined by
xU = [c, t]T = [zmc,k,(k, m)]T.(29)
Here, the track ID(k, m)uniquely identifies a new object with
the time stepkand the measurement indexm. Throughout
the OptiPMB tracking recursions, the time-invariant states
remain unchanged. The counter variables for misdetections
and survival time steps are initialized asx cnt,k = 0and
xlen,k = 1. The object’s confidence score is defined as
xs,k = [1−exp(−x len,k)]zms,k (30)
wherez ms,k ∈(0,1]represents the detection score ofz mk ,
indicating thatx s,k is further down-scaled from the detection
score for tracks with shorter survival time.
After the optimal global hypothesis is determined and the
PMB density is pruned, if a remaining detected potential
object is associated with a measurementz mk under the global
hypothesis, its auxiliary state is updated by
xA,k = (1−z ms,k)xA,k−1 +z ms,kzmA,k,(31)
the misdetection counterx cnt,k is reset to zero, and the
confidence scorex s,k is calculated by (30). Otherwise, if the
object is misdetected, the auxiliary state remains unchanged,
the counter increments by onex cnt,k =x cnt,k−1 + 1, andx s,k
is set to zero. The number of survival time steps increases as
xlen,k =x len,k−1 + 1regardless of the association status.
After pruning and light-weight filtering, the MB density is
re-indexed as
Ik = SN dkn=1 Lnk = SN dkn=1{n}(32)
whereN dk is the number of remaining detected potential
objects. The PPP intensity after pruning is expressed as
λuk = PN ukn=1 µu,nk N(x;m u,nk , Pu,nk )(33)
whereN uk denotes the number of remaining Poisson compo-
nents. The posterior PMB density is then fully determined by
the parameters(λ uk,{(r ik, pik)}i∈Ik ).
G. Adaptive Designs
The performance of model-based 3D MOT methods de-
pends heavily on the alignment between the pre-designed
model and the actual tracking scenarios. To enhance robustness
of the tracker, OptiPMB proposes multiple adaptive modules
and integrates them in the Bayesian filtering pipeline, enabling
dynamic parameter adjustment and effective initialization of
new object tracks.

9
1)Adaptive Detection Probability (ADP):In urban traffic
scenarios, objects are frequently occluded by the environment
and other objects, leading to inaccurate detections or even
complete misdetections. To improve the track continuity and
reduce ID switch errors, OptiPMB adaptively adjusts the
detection probability based on the object’s occlusion status,
which is estimated using the LiDAR point cloud and the object
3D bounding box. Specifically, during the PMB update pro-
cedure, the predicted object 3D bounding boxes are projected
onto the LiDAR coordinates, and the number of LiDAR points
within each bounding box is counted. The adaptive detection
probability is then defined as
pd(x+) =p d0(c)·min[1,(1−s d(c)) PTS(x+)PTS0(c) +s d(c)](34)
where the baseline detection probabilityp d0(c), minimal scal-
ing factors d(c)∈(0,1], and expected number of LiDAR
pointsPTS 0(c)are parameters predefined based on the ob-
ject’s classc,PTS(x +)counts the actual number of LiDAR
points within the object’s predicted bounding box. Accord-
ing to this definition, the detection probability decreases as
PTS(x+)becomes smaller, indicating that the object may
be occluded. This adaptive mechanism enable OptiPMB to
maintain tracks for occluded objects and reduce ID switch
errors, improving robustness in complex urban environments.
2)Hybrid Adaptive Birth Model (HABM):The design of
the object birth model not only affects the initiation of object
trajectories but also influences the association between existing
objects and measurements. Consequently, it plays a critical
role in the performance of RFS-based tracking algorithms. Op-
tiPMB employs a hybrid adaptive birth model that integrates
the conventional PPP birth model with a measurement-driven
adaptive birth method, enabling fast-response and accurate
initialization of new object tracks.
According to the PMB update procedure described in Sec-
tion IV-D2, measurements that cannot be associated with any
Poisson component are processed by the HABM to determine
the local hypothesis parameters. Such “unused” measurement
may correspond to either the first-time detection of a new-
born object or a false detection. To handle false detections,
HABM filters out unused measurements with detection scores
zs below a predefined thresholdη score and collect them as
{zmk }m∈Mlowk , whereM lowk represents the index set for low-score measurements. During the PMB update step, a low-score
measurementz mk is assumed to originate from clutter, and the
first-time detection hypothesis is parameterized as(
w=−ln[λ c(zmk )]
r= 0. (35)
Note the spatial distributionp(x)is not specified, as this local
hypothesis is directly removed during the pruning step and
does not contribute to any object track.
For the remaining unused measurements with detection
scores greater than or equal to the thresholdη score, i.e.,
{zmk }m∈Mhighk , HABM treats them as first-time detections ofnewborn objects. Each high-score measurement is associated
with a specialized PPP intensity defined as
λb0(x) =µ b0(c)puni(x).(36)
wherep uni(x)represents a uniform spatial distribution over
the region of observation,µ b0(c)is the predefined birth rate
parameter for object classc. This special PPP intensityλ b0(x)
represents undetected objects within the observation region
at the previous time step. It is assumed to be time-invariant
and provides no prior information about the object’s motion
state. Therefore,λ b0(x)functions as an independent density
in HABM and is excluded from the PMB density recursions.
The first-time detection hypothesis generated for a high-score
measurementz mk is determined by


w=−ln[µ b0(zmc,k) 1−pa(zmk )A +λ c(zmk )]
r= 1
p(x) =N(x;m 0,mk , P0,mk )
(37)
whereAdenotes the area size of the observation region,
pa(zmk )is the estimated association probability betweenz mk
and existing objects, defined as:
pa(zmk ) = min[1, PN dk−1n=1 max({Lm,ik }i∈Lnk−1 )]
Lm,ik =N(z mxy,k; ˆzik, Sik). (38)
The calculation method for the likelihoodL m,ik is provided in
(18) and (20) in Section IV-D1. According to the definition of
(37), if the unused measurementz mk has a higher likelihood of
being associated with existing objects, the first-time detection
hypothesis will incur a higher association cost. The Gaussian
spatial distributionp(x)in (37) is characterized by the mean
vectorm 0,mk and the covariance matrixP 0,mk predefined for
each object class


m0,mk = [zmx,k, zmy,k, q(zmvx,k)2 + (zmvy,k )2,
arctan(zmvy,k , zmvx,k),0,0] T
P 0,mk =P 0(zmc,k).
(39)
This adaptive design helps reduce false track initializations
while allowing OptiPMB to promptly initialize new tracks
when measurements with high detection scores are observed.
To enhance recall performance and reduce false negative
errors, HABM creates a Poisson component for each low-
score measurement and defines the PPP intensity for newborn
undetected potential objects as
λbk(x) = Pm∈Mlowk µb,mk N(x;m 0,mk , P0,mk )
µb,mk =µ ab(zmc,k)[1−p a(zmk )] (40)
whereM lowk is the index set for low-score measurements, and
µab(zmc,k)denotes the adaptive birth rate parameter predefined
for each object class. If a low-score measurement originates
from a newborn object rather than clutter, its corresponding
Poisson component inλ bk(x)is likely to be associated with
subsequent measurements and initialize a new track later.
This measurement-driven definition ofλ bk(x)allows OptiPMB
to effectively account for measurements with low detection
scores while reducing the risk of missing newborn objects.
H. Optimizations
To further enhance 3D MOT performance, we optimize the
conventional PMB filter-based tracking pipeline by redesign-
ing two key algorithm modules in OptiPMB.

10
1)Redundant PPP Pruning (RPP):Although the HABM
proposed in OptiPMB can reduce false negative errors by
introducing the measurement-driven newborn PPP intensity
λbk(x), the number of Poisson components withinλ uk(x)
increases over time. To improve computational efficiency and
reduce false track initialization, removing redundant Poisson
components during the PPP pruning step is necessary. While
the previous PMBM-based 3D MOT methods [20, 21] did not
specify a dedicated pruning strategy, the original PMBM filter
[60] only prunes the Poisson components with weights below
a predefined threshold. However, this approach is not well-
suited for measurement-driven PPP birth modeling. Since the
PPP removal solely depends on one pruning threshold, new
Poisson components with low initial weights may be pruned
before they can correctly initialize a new track, while Poisson
components that have already generated detected potential
objects may persist unnecessarily, leading to false track initia-
tions. The GNN-PMB tracker [22] utilizes a full measurement-
driven approach for generatingλ bk(x)but removes all Poisson
components at the pruning step. This aggressive pruning
strategy may result in track initialization failures.
OptiPMB proposes a new pruning strategy to address these
limitations. Specifically, the PPP pruning module marks Pois-
son components that generate any first-time detection hypothe-
sis during the PMB update step and assigns a counter variable
to each Poisson component to track its survival duration.
After the PPP prediction and update steps, the pruning module
removes all marked Poisson components to prevent repeated
track initialization. Additionally, any remaining Poisson com-
ponents that have persisted for more thanη step time steps
are discarded. This PPP pruning mechanism balances between
reliable track initialization and computational efficiency, ben-
efiting MOT performance in complex scenarios.
2)Optimized Track Extraction (OTE):After perform-
ing PMB prediction and update, data association, and PMB
pruning steps, OptiPMB extracts object states from the pos-
terior PMB densityf(X k|Z1:k)and outputs the estimated
object tracks at current time. The previous PMBM/PMB-
based trackers [20–22] apply an existing probability filter to
extract tracks, where the Bernoulli componentX ik with an
existing probabilityr ik exceeding a predefined thresholdη ext
are selected as object tracks. However, relying on a single
extraction threshold makes it difficult to achieve both fast track
initialization and efficient track termination simultaneously, as
a high threshold may delay track initialization, while a low
threshold may cause misdetected or lost tracks persist longer
than necessary and result in false positive errors.
To improve the flexibility of track extraction, OptiPMB
introduces a misdetection counter and redesigns the existing
probability filter by applying two extraction thresholdsη ext1
andη ext2, satisfyingη ext1 ≤η ext2. The IDs of extracted tracks
are recorded in a setT k. Consider a Bernoulli componentX ik,
the track extraction logic is as follows:
•If the track corresponding toX ik has not been extracted
previously, i.e.,t ik /∈Tk−1, thenX ik is extracted as an ob-
ject track if its existence probability satisfiesr ik ≥η ext1.
•Ift ik ∈T k−1,X ik is extracted only ifr ik ≥η ext2 and
the misdetection counter variablex icnt,k is smaller than a
predefined limitη cnt.
This redesign of track extraction strategy allows faster track
initialization with a lower extraction thresholdη ext1. Addition-
ally, when an existing object is misdetected over multiple time
steps, the introduction ofη ext2 andη cnt enables faster track
termination, thereby reducing false positive errors.
V. EXPERIMENTS ANDPERFORMANCEANALYSIS
A. Dataset and Implementation Details
The proposed OptiPMB tracker is compared with published
and peer-reviewed state-of-the-art online 3D MOT methods
on two widely used open-source datasets: the nuScenes dataset
[18] and the KITTI dataset [19]. The official nuScenes tracking
task evaluates 3D MOT performance across seven object cat-
egories (bicycle, bus, car, motorcycle, pedestrian, trailer, and
truck) using average multi-object tracking accuracy (AMOTA)
and average multi-object tracking precision (AMOTP) [8] as
primary evaluation metrics. The official KITTI object tracking
benchmark evaluates 2D MOT performance, which involves
tracking 2D object bounding boxes in camera coordinates
for car and pedestrian categories. It primarily uses high-order
tracking accuracy (HOTA) [66] as the main evaluation metric.
To provide a more comprehensive performance analysis, we
extend the evaluation metrics as follows:
•nuScenes Dataset: We incorporate the HOTA metric
to further evaluate 3D MOT performance. Specifically,
HOTA evaluates tracking accuracy by matching tracking
results and ground truths based on a similarity scoreS
[66]. To adapt HOTA for 3D MOT evaluation, we define
the similarity scoreSas:
S= max[0,1−D( ˆxxy,x xy)/D0](41)
whereD( ˆxxy,x xy)calculates the Euclidean distance
between an object’s estimated 2D center position ˆxxy and
the ground truth center positionx xy on the ground plane,
D0 is the distance threshold, beyond which the similarity
score reduces to zero. For the nuScenes dataset evalua-
tion, we set the distance threshold asD 0 = 2m, meaning
that an estimated object can be matched with a ground
truth if their 2D center distance satisfiesD( ˆxxy,x xy)≤
2m. This matching criterion is consistent with the of-
ficial nuScenes tracking task settings 2, ensuring that our
HOTA-based evaluation aligns with standard benchmarks
for fair comparison.
•KITTI Dataset: We evaluate 3D MOT accuracy using the
multi-object tracking accuracy (MOTA), AMOTA, and
scaled AMOTA (sAMOTA) metrics, following the widely
accepted protocol proposed in [8].
Other commonly used secondary metrics, including detection
accuracy score (DetA), association accuracy score (AssA),
multi-object tracking precision (MOTP), true positives (TP),
false positives (FP), false negatives (FN), and ID switches
(IDS), are also reported in the following evaluations (see
[8, 18, 66] for definitions of these metrics). As shown in Table
I, the parameters of OptiPMB are finetuned on the nuScenes
2https://www.nuscenes.org/tracking

11
GNN
SHAFastpoly
Frame 1 Frame 2 Frame 3
(a) OptiPMB (Ours)
Frame 1 Frame 2 Frame 3
(c) GNN-PMB
Frame 1 Frame 2 Frame 3
(b) Fast-Poly
Frame 1 Frame 2 Frame 3
(d) ShaSTA
Fig. 4. Qualitative comparison among our proposed OptiPMB, Fast-Poly [14], GNN-PMB [22], and ShaSTA [3] on the nuScenes validation set (Scene-0095).
Black solid boxes denote ground truth objects. Dashed boxes represent estimated objects, with distinct colors indicating different IDs. Dashed colored lines
depict object trajectories. ID switch errors are highlighted by red arrows.
TABLE I
FINETUNEDOPTIPMBPARAMETERS.
Parameters nuScenes Category KITTIBic. Bus Car Mot. Ped. Tra. Tru. Car
Score filter thresholdη sf 0.15 0 0.1 0.16 0.2 0.1 0 0.3
NMS IoU thresholdη iou 0.1 0.1 0.1 0.1 0.1 0.1 0.1 0.1
Survival probabilityp s 0.99 0.99 0.99 0.99 0.99 0.99 0.99 1
Gating distance thresholdη dist 3 10 10 4 3 10 10 4
Baseline detection probabilityp d0 0.8 0.9 0.9 0.8 0.8 0.9 0.9 0.9
Expected number of pointsPTS 0 10 10 10 10 10 10 10 10
Minimal scaling factors d 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.7
HABM score thresholdη score 0.17 0.3 0.25 0.18 0.2 0.15 0.15 0.65
Adaptive birth rateµ ab 2 2 2 2 2 2 2 0.2
Undetected object birth rateµ b0 1 5 2 1 1 2 2 0.5
Clutter rateµ c 0.5 0.2 1 0.5 0.5 0.5 1 10
PPP max survival time stepsη step 3 3 3 2 2 2 2 1
Track extraction threshold 1η ext1 0.7 0.7 0.7 0.7 0.7 0.7 0.5 0.85
Track extraction threshold 2η ext2 0.95 0.7 0.8 0.95 0.8 0.8 0.9 0.9
Misdetection counter limitη cnt 3 2 2 2 2 2 2 5
and KITTI training sets using CenterPoint [67] and CasA [68]
detections, respectively.
B. Comparison with State-of-the-Arts
1) nuScenes Dataset:As shown in Table II, our proposed
OptiPMB demonstrates state-of-the-art online 3D MOT per-
formance on the nuScenes test set. Specifically, it achieves
overall AMOTA scores of 0.767 using the LargeKernel3D
[69] detector and 0.713 using the CenterPoint [67] detector.
With the same detectors, OptiPMB outperforms the previous
learning-assisted [1, 44], learning-based [3, 4] and model-
based [10, 13, 14, 21, 22] methods in terms of the primary
tracking accuracy metric, AMOTA. Our method also demon-
strates strong performance in secondary metrics, including
TP, FN, FP, and IDS, especially comparing with the previ-
ous model-based RFS trackers, the RFS-M 3 [21] and GNN-
PMB [22]. Our method is fully open-sourced, with code and
parameters available 3, to demonstrate the potential of RFS-
3Code is available at: https://github.com/dinggh0817/OptiPMB
based trackers and serve as a new baseline for model-based
3D MOT.
To comprehensively evaluate our proposed method, we
further compare OptiPMB with other state-of-the-art 3D MOT
methods across all seven object categories on the nuScenes
validation set with extended metrics. For a fair comparison,
we select three open-source trackers as baselines: Fast-Poly
[14], GNN-PMB [22], and ShaSTA [3]. These trackers all
employ the TBD strategy and provide parameters finetuned
for the CenterPoint detector while representing different design
approaches of 3D MOT methods:
•Fast-Poly: A state-of-the-art model-based tracker using
two-stage data association and confidence score-based
track management. Its design can be categorized as TBD
with RV-based Bayesian filter (Section II-A1).
•GNN-PMB: The previous state-of-the-art PMB-based
tracker, categorized as TBD with RFS-based Bayesian
filter (Section II-A2).
•ShaSTA: A learning-assisted TBD tracker using spatial-
temporal and shape affinities to improve association qual-
ity. Its design can be categorized as TBD with learning-
assisted data association (Section II-B1).
As demonstrated in Table III, with the same CenterPoint de-
tector, OptiPMB achieves the highest overall HOTA (52.06%)
and AMOTA (0.741) among the compared methods, indicating
its superior tracking accuracy. OptiPMB surpasses other meth-
ods in HOTA, AMOTA, and IDS across all object categories,
except for the bicycle category, where it ranks second. Notably,
compared to GNN-PMB, OptiPMB significantly improves
tracking accuracy (+6.03% HOTA and +3.4% AMOTA) and
track ID maintenance (-423 IDS) while utilizing a similar
PMB filter-based RFS framework. This performance differ-
ence underscores the effectiveness of the innovative designs
and modules proposed in OptiPMB. HOTA and its sub-
metrics (AssA and DetA) in Table III are evaluated across
multiple localization accuracy thresholds without considering
object confidence scores or applying track interpolation post-
processing [66]. Consequently, the DetA and AssA scores

12
TABLE II
ONLINE3D MOTPERFORMANCE OFOPTIPMBAND OTHER ADVANCED TRACKERS ON THE NUSCENES TEST SET. TRACKERS USINGCENTERPOINT[67]
ANDLARGEKERNEL3D [69]DETECTORS ARE DISTINGUISHED FOR FAIR COMPARISON,WITH DIFFERENT INPUT MODALITIES(C:CAMERA, L: LIDAR)
INDICATED.BOLDAND UNDERLINE DENOTE THE FIRST AND SECOND BEST RESULTS AMONG TRACKERS USING THE SAME DETECTOR. BLUE
HIGHLIGHTS THE PRIMARY TRACKING ACCURACY METRIC, AMOTA.
Method Detector Modal. AMOTA↑ AMOTP↓TP↑FN↓FP↓IDS↓Overall Bic. Bus Car Mot. Ped. Tra. Tru.
RFS-M3 (ICRA 2021) [21] CenterPoint L 0.619 N/A N/A N/A N/A N/A N/A N/A 0.752 90872 27168 16728 1525
OGR3MOT (RA-L 2022) [1] CenterPoint L 0.656 0.380 0.711 0.816 0.640 0.787 0.671 0.590 0.620 95264 24013 17877 288
SimpleTrack (ECCVW 2022) [10] CenterPoint L 0.668 0.407 0.715 0.823 0.674 0.796 0.673 0.587 0.550 95539 23451 17514 575
GNN-PMB (T-IV 2023) [22] CenterPoint L 0.678 0.337 0.744 0.839 0.657 0.804 0.715 0.647 0.560 97274 21521 17071 770
3DMOTFormer (ICCV 2023) [4] CenterPoint L 0.682 0.3740.7490.821 0.705 0.807 0.696 0.626 0.49695790 23337 18322 438
NEBP (T-SP 2023) [44] CenterPoint L 0.6830.4470.708 0.835 0.698 0.802 0.690 0.598 0.624 97367 21971 16773227
ShaSTA (RA-L 2024) [3] CenterPoint L 0.696 0.410 0.733 0.838 0.727 0.810 0.704 0.650 0.540 97799 21293 16746 473
OptiPMB (Ours) CenterPoint L 0.7130.414 0.748 0.860 0.751 0.836 0.727 0.658 0.54198550 20758 16566257
Poly-MOT (IROS 2023) [13] LargeKernel3D C+L 0.754 0.582 0.7860.865 0.810 0.820 0.751 0.662 0.422101317 17956 19673 292
Fast-Poly (RA-L 2024) [14] LargeKernel3D C+L 0.758 0.573 0.767 0.863 0.826 0.8520.768 0.656 0.479 100824 1841517098326
OptiPMB† (Ours) LargeKernel3D C+L 0.767 0.6000.774 0.870 0.8270.848 0.775 0.676 0.460 102899 1641118796 255
† OptiPMB ranked first by overall AMOTA on thenuScenes tracking challenge leaderboardat the submission time of our manuscript (Mar. 2025).
TABLE III
ONLINE3D MOTPERFORMANCE OFOPTIPMBAND OTHER STATE-OF-THE-ART TRACKERS ON THE NUSCENES VALIDATION SET. THECENTERPOINT
[67]DETECTOR IS EMPLOYED FOR ALL TRACKERS FOR A FAIR COMPARISON.BOLDAND UNDERLINE DENOTE THE FIRST AND SECOND BEST RESULTS
WITHIN EACH CATEGORY. BLUE INDICATES THE TWO PRIMARY TRACKING ACCURACY METRICS, HOTAANDAMOTA.
Method Category HOTA(%)↑DetA(%)↑AssA(%)↑ AMOTA↑AMOTP↓TP↑FN↓FP↓IDS↓
GNN-PMB† (IEEE T-IV 2023) [22]
Bic. 17.88 4.8266.54 0.513 0.602 1135 855 220 3
Bus 46.83 30.16 72.97 0.854 0.5461789 312155 11
Car 57.53 43.22 77.37 0.849 0.387 49182 8791 6140 344
Mot. 21.38 6.91 66.22 0.723 0.475 1494 477 247 6
Ped. 46.49 29.86 72.48 0.807 0.357 21149 4008 3669 266
Tra. 23.90 9.03 64.22 0.506 0.973 1378 1045 412 2
Tru. 36.13 17.38 75.36 0.695 0.581 7007 2625151918
Overall 46.03 28.15 75.45 0.707 0.560 83134 18113 12362 650
ShaSTA† (IEEE RA-L 2024) [3]
Bic. 13.62 2.58 72.12 0.5880.507 1187 8041432
Bus 45.17 26.85 76.16 0.856 0.527 1777 333 142 2
Car 57.05 41.48 78.67 0.8560.33749200 89866067131
Mot. 21.56 6.83 68.10 0.745 0.521 1457 513837
Ped. 46.99 29.48 74.95 0.814 0.378 20945 42583378220
Tra. 23.69 8.63 65.84 0.531 0.970 1284 11392382
Tru. 36.24 17.17 76.70 0.703 0.5727222 24211671 7
Overall 43.87 24.98 77.18 0.728 0.544 83072 1845411722371
Fast-Poly† (IEEE RA-L 2024) [14]
Bic. 16.36 3.6174.30 0.572 0.553 1218 775 189 0
Bus 46.30 27.97 76.90 0.855 0.522 1787 316 172 9
Car 62.63 49.4879.56 0.860 0.339 50443 76548057 220
Mot. 27.44 9.95 75.83 0.792 0.470 1559 4151783
Ped. 57.59 43.05 77.12 0.835 0.355 21916 33324070 175
Tra. 24.69 9.29 66.40 0.5290.9391440 984 371 1
Tru. 32.29 13.40 78.00 0.714 0.5337220 2424 1676 6
Overall 48.52 30.04 78.55 0.737 0.530 85583 1590014713 414
OptiPMB (Ours)
Bic. 17.50 4.20 73.07 0.575 0.514 1221 771208 1
Bus 55.91 40.69 77.27 0.8570.538 1785 327131 0
Car 62.6949.10 80.47 0.8700.359 50396 7864 685057
Mot. 32.5214.06 75.39 0.792 0.4701497 477 112 3
Ped. 61.73 49.41 77.24 0.8380.357 21365 3892 3401 166
Tra. 27.12 10.59 70.70 0.5340.949 1488 9373990
Tru. 38.77 19.05 79.21 0.7180.539 7211 2439 1576 1
Overall 52.06 34.31 79.27 0.7410.532 84963 16707 12677227
† Evaluated using the authors’ code and parameters. The tracking performance is identical to that reported in the original manuscripts.
indicate that OptiPMB achieves high detection and associ-
ation accuracy while evaluating all raw tracking results. A
qualitative comparison in Fig. 4 also illustrates the superior
tracking performance of OptiPMB. In a challenging scenario
where high-velocity cars enter the observation area, OptiPMB
correctly initiates and maintains tracks. In contrast, the model-
based methods Fast-Poly and GNN-PMB fail to associate the
new objects with subsequent detections, leading to ID switch
errors. The learning-assisted tracker ShaSTA exhibits fewer ID
switches but repeatedly initializes tracks in the first frame.
2) KITTI Dataset:Since the official KITTI object tracking
evaluation only includes 2D MOT metrics, we compare the
online 3D MOT performance of OptiPMB and other advanced
trackers on the car category of the KITTI validation dataset,
following the evaluation protocol proposed in [8]. This proto-
col designates sequences 1, 6, 8, 10, 12, 13, 14, 15, 16, 18,

13
TABLE IV
ONLINE3D MOTPERFORMANCE OFOPTIPMBAND OTHER ADVANCED TRACKERS ON THEKITTICAR VALIDATION SET. POINTRCNN [70],
POINT-GNN [71],ANDCASA [68]DETECTORS ARE DISTINGUISHED FOR FAIR COMPARISON,WITH DIFFERENT MODALITIES(CFOR CAMERA, LFOR
LIDAR)INDICATED.BOLDAND UNDERLINE DENOTE THE FIRST AND SECOND BEST RESULTS AMONG TRACKERS USING THE SAME DETECTOR.
Method 3D Detector Modality sAMOTA(%)AMOTA(%)↑AMOTP(%)↑MOTA(%)↑MOTP(%)↑IDS↓
AB3DMOT (IROS 2020) [8] PointRCNN L 93.28 45.43 77.41 86.24 78.430
ConvUKF (T-IV 2024) [73] PointRCNN L 93.32 45.46 78.09 N/A N/A N/A
GNN3DMOT (CVPR 2020) [46] PointRCNN C+L 93.68 45.2778.1084.7079.03 0
FGO-based 3D MOT (S-J 2024) [74] PointRCNN L 93.77 46.14 77.85 86.53 79.00 1
OptiPMB (Ours) PointRCNN L 93.78 48.4077.3087.5377.390
PolarMOT (ECCV 2022) [50] Point-GNN L 94.32 N/A N/A93.93N/A 31
CAMO-MOT (T-ITS 2023) [2] Point-GNN C+L 95.20 48.04 81.48N/A N/A N/A
OptiPMB (Ours) Point-GNN L 96.29 48.8779.39 93.48 78.750
RobMOT † (T-ITS 2025) [72] CasA L 91.16 46.95 82.06 89.53 83.570
MCTrack† (arXiv 2024) [15] CasA L 91.6947.2981.88 90.52 84.01 0
CasTrack† (T-GRS 2022) [68] CasA L 92.14 44.9482.6089.4584.342
OptiPMB (Ours) CasA L 93.4047.19 81.4791.0081.030
† Evaluated using the authors’ official code, parameters, and online tracking configurations.
TABLE V
ONLINE2D MOTPERFORMANCE OF OUR PROPOSEDOPTIPMBAND OTHER ADVANCED TRACKERS ON THEKITTICAR TEST DATASET. TRACKERS
USINGPOINTRCNN [70], POINT-GNN [71],ANDCASA [68]DETECTORS ARE DISTINGUISHED FOR FAIR COMPARISON,WITH DIFFERENT MODALITIES
(CFOR CAMERA, LFORLIDAR)INDICATED.BOLDAND UNDERLINE DENOTE THE FIRST AND SECOND BEST RESULTS AMONG TRACKERS USING THE
SAME DETECTOR. BLUE INDICATES THE PRIMARY TRACKING ACCURACY METRIC, HOTA.
Method 3D Detector Modality HOTA(%)↑DetA(%)↑AssA(%)↑MOTA(%)↑MOTP(%)↑TP↑FP↓IDS↓
AB3DMOT (IROS 2020) [8] PointRCNN L 69.99 71.13 69.33 83.6185.2329849 4543 113
Feng et al. (T-IV 2024) [29] PointRCNN C+L 74.81 N/A N/A 84.82 85.17 N/A N/A N/A
DeepFusionMOT (RA-L 2022) [12] PointRCNN C+L 75.46 71.54 80.05 84.63 85.02 29791 4601 84
StrongFusionMOT (S-J 2023) [30] PointRCNN C+L 75.65 72.0879.8485.5385.07 29734 4658 58
OptiPMB (Ours) PointRCNN L 75.57 70.1281.9081.97 84.7331763 2629 33
PolarMOT (ECCV 2022) [50] Point-GNN L 75.16 73.94 76.95 85.0885.6331724 2668 462
CAMO-MOT (T-ITS 2023) [2] Point-GNN C+L 79.95N/A N/A90.3885.00 N/A 2322 23
OptiPMB (Ours) Point-GNN L 79.08 75.13 83.8688.76 84.9032554 1838 23
UG3DMOT (SP 2024) [75] CasA L 78.60 76.01 82.28 87.9886.5631399 2992 30
MMF-JDT (RA-L 2025) [76] CasA C+L 79.52 75.83 84.01 88.06 86.24 N/A N/A 37
RobMOT (T-ITS 2025) [72] CasA L 81.22 77.48 85.7790.48 86.02 32670 1722 6
OptiPMB (Ours) CasA L 81.76 78.7085.57 91.5786.47 32909 148317
and 19 in the original KITTI training set as the validation set.
As shown in Table IV, OptiPMB achieves superior tracking
accuracy on the KITTI validation set, outperforming other
state-of-the-art trackers that use the same PointRCNN [70],
PointGNN [71], and CasA [68] detectors in sAMOTA scores.
Here, the online 3D MOT results of CasTrack [68], MCTrack
[15], and RobMOT [72] are evaluated using their online
tracking configurations and finetuned parameters provided by
the authors. For reference, the 2D MOT performance for the
compared trackers on the KITTI test set is presented in Table
V. With the PointRCNN [70] and PointGNN [71] detection re-
sults, OptiPMB achieves significantly higher tracking accuracy
than the baseline LiDAR-only trackers [8, 50] while generating
the fewest false positives and ID switch errors among the com-
pared methods. Although OptiPMB relies solely on LiDAR de-
tection results, its HOTA score is still comparable with camera-
LiDAR fusion-based trackers [2, 12, 29, 30]. Moreover, when
utilizing higher-quality CasA [68] detection results, OptiPMB
surpasses even the recently proposed RobMOT [72] and MMF-
JDT [76] trackers in HOTA, DetA, MOTA, TP, and FP scores,
demonstrating a strong tracking performance.
C. Ablation Study on OptiPMB
We conduct ablation experiments on the nuScenes validation
set to assess the influence of the proposed components in
OptiPMB, as summarized in Table VI. In the baseline tracker,
the adaptive detection probabilityp d(x+)is replaced with
the fixed parameterp d0, and object tracks with existence
probabilities exceeding the thresholdη ext1 are extracted. In
addition, the HABM and OTE modules are replaced by the
object birth model and the PPP pruning strategy employed
in the GNN-PMB [22] tracker. Except for the detection
probability and existence threshold settings described above,
all tracker variants share identical parameter configurations.
For clarity of comparison, trackers equipped with different
numbers of modules are grouped together and ranked within
each group according to their AMOTA scores. To analyze
the runtime impact of different modules, we also report the
average processed frames per second (FPS) of the Python
implementation of each tracker variant on our test platform,
running Ubuntu 22.04 with an AMD 7950X CPU and 64
GB of RAM. Consistent with common practice in the TBD
literature, these FPS values are measured without accounting
for detector latency.
As shown in Table VI, HABM is the primary contributor
to the effectiveness of OptiPMB, as trackers equipped with

14
TABLE VI
ABLATION STUDY OFOPTIPMBON THE NUSCENES VALIDATION SET
USING THECENTERPOINT[67]DETECTOR.
Modules Metrics
ADP HABM RPP OTE AMOTA↑AMOTP↓FN↓FP↓IDS↓FPS↑
0.696 0.622 20421 12362 250 17.5
✓ 0.688 0.609 21458 13755 178 15.4
✓ 0.692 0.614 19664 12683 325 4.7
✓ 0.701 0.627 20132 11020 334 19.0
✓ 0.726 0.551 16061 14403 214 20.1
✓ ✓ 0.688 0.597 20985 13820 203 4.3
✓ ✓ 0.697 0.632 19941 11082 414 4.7
✓ ✓ 0.705 0.621 20103 11301 275 14.6
✓ ✓ 0.721 0.535 17766 14975 163 13.2
✓ ✓ 0.727 0.551 17432 13097 206 17.2
✓ ✓ 0.731 0.569 17607 11385 264 19.7
✓ ✓ ✓ 0.708 0.615 19700 11214 414 4.3
✓ ✓ ✓ 0.722 0.529 17678 15046 163 13.3
✓ ✓ ✓ 0.732 0.563 17595 11391 264 15.6
✓ ✓ ✓ 0.739 0.534 16516 12911 233 13.4
✓ ✓ ✓ ✓ 0.741 0.532 16707 12677 227 11.3
HABM achieve the highest AMOTA scores within each group.
Incorporating this birth model not only substantially boosts
the baseline tracking performance (+3.0% AMOTA), but also
improves both track ID maintenance and runtime efficiency
(–36 IDS, +2.6 FPS) by generating more reliable newborn
objects and suppressing false potential objects. However, the
other three modules exhibit more complex effects and cannot
effectively improve tracking accuracy in isolation. Specifi-
cally, adding ADP reduces ID switch errors by enhancing
the maintenance of occluded tracks, but it also introduces
additional false tracks, which can reduce tracking accuracy.
The RPP module reduces false negatives by retaining PPP
components for a longer duration, but at the cost of increased
tracking latency due to the larger number of potential objects.
The OTE module improves accuracy and FPS by reducing
false tracks, yet simultaneously increases ID switch errors.
Nevertheless, when combined with HABM, the adverse effects
of these modules are mitigated, leading to the improvement
in overall tracking performance. Consequently, our OptiPMB
tracker equipped with all four modules achieves the highest
tracking accuracy (+4.5% AMOTA) among all tracker variants,
demonstrating the effectiveness of their joint design.
D. Parameter Sensitivity
The performance of model-based 3D MOT methods often
relies on careful selection of hyperparameters. Therefore, we
analyzed the impact of key parameters in OptiPMB on the car
category in the nuScenes validation set. As shown in Fig. 5,
the survival probability (ps), clutter rate (µc), and misdetection
counter threshold (η cnt) significantly influence both AMOTA
and HOTA scores. To achieve better track continuity and
recall performance without sacrificing tracking accuracy, we
suggest setting these parameters top s = 0.99,µ c = 1, and
ηcnt = 2. OptiPMB is less sensitive to other hyperparameters,
demonstrating the robustness of our proposed adaptive designs.
VI. CONCLUSION
In this study, we introduced OptiPMB, a novel 3D multi-
object tracking (MOT) approach that employs an optimized
GNN
SHAFastpoly
Frame 1 Frame 2 Frame 3
(a) Optimal-PMB (Ours)
Frame 1 Frame 2 Frame 3
(c) GNN-PMB
Frame 1 Frame 2 Frame 3
(b) Fast-Poly
Frame 1 Frame 2 Frame 3
(d) ShaSTA
Selected ParameterAMOTA HOTA
Fig. 5. Impact of key OptiPMB parameters on tracking accuracy for cars in the
nuScenes validation set with CenterPoint [67] detections. Selected parameters
are used to report the results in Table III.
Poisson multi-Bernoulli (PMB) filter within the tracking-by-
detection framework. Our method addressed critical challenges
in random finite set (RFS)-based 3D MOT by incorporating
a measurement-driven hybrid adaptive birth model, adaptive
detection probabilities, and optimized track extraction and
pruning strategies. Experimental results on the nuScenes and
KITTI datasets demonstrated the effectiveness and robust-
ness of OptiPMB, which achieved state-of-the-art performance
compared to existing 3D MOT methods. Consequently, a
new benchmark was established for RFS-based 3D MOT
in autonomous driving scenarios. Future research will focus
on enhancing real-time performance of OptiPMB through
parallelization techniques.
REFERENCES
[1] J.-N. Zaech, A. Liniger, D. Dai, M. Danelljan, and L. Van Gool,
“Learnable online graph representations for 3D multi-object tracking,”
IEEE Robot. Autom. Lett., vol. 7, no. 2, pp. 5103-5110, Jan. 2022.
[2] L. Wang et al., “CAMO-MOT: Combined appearance-motion optimiza-
tion for 3D multi-object tracking with camera-LiDAR fusion,”IEEE
Trans. Intell. Transp. Syst., vol. 24, no. 11, pp. 11981-11996, Jun. 2023.
[3] T. Sadjadpour, J. Li, R. Ambrus and J. Bohg, “ShaSTA: Modeling shape
and spatio-temporal affinities for 3D multi-object tracking,”IEEE Robot.
Autom. Lett., vol. 9, no. 5, pp. 4273-4280, May. 2024.
[4] S. Ding, E. Rehder, L. Schneider, M. Cordts, J. Gall, “3DMOT-
Former: Graph transformer for online 3D multi-object tracking,” inProc.
IEEE/CVF Int. Conf. Comput. Vis. (ICCV), 2023, pp. 9784-9794.
[5] J. Gwak, S. Savarese, and J. Bohg, “Minkowski tracker: A sparse spatio-
temporal R-CNN for joint object detection and tracking,”arXiv preprint,
2022. [Online]. Available: https://arxiv.org/abs/2208.10056.
[6] T. Zhang, X. Chen, Y . Wang, Y . Wang, and H. Zhao, “MUTR3D:
A multi-camera tracking framework via 3D-to-2D queries,” inProc.
IEEE/CVF Conf. Comput. Vis. Pattern Recognit. Workshop (CVPRW),
2022, pp. 4537-4546.
[7] C. Zhang, C. Zhang, Y . Guo, L. Chen, and M. Happold, “MotionTrack:
End-to-end transformer-based multi-object tracking with LiDAR-camera

15
fusion,” inProc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit.
Workshop (CVPRW), 2023, pp. 151-160.
[8] X. Weng, J. Wang, D. Held, and K. Kitani, “3D multi-object tracking:
A baseline and new evaluation metrics,” inProc. IEEE/RSJ Int. Conf.
Intell. Robots Syst. (IROS), 2020, pp. 10359-10366.
[9] A. Kim, A. O ˇsep, and L. Leal-Taix ´e, “EagerMOT: 3D multi-object
tracking via sensor fusion,” inProc. IEEE Int. Conf. Robot. Autom.
(ICRA), 2021, pp. 11315-11321.
[10] Z. Pang, Z. Li, and N. Wang, “SimpleTrack: Understanding and re-
thinking 3D multi-object tracking,” inProc. Eur. Conf. Comput. Vis.
Workshop (ECCVW), 2022, pp. 680-696.
[11] Y . Zhang et al., “ByteTrackV2: 2D and 3D multi-object tracking
by associating every detection box,”arXiv preprint, 2023. [Online].
Available: https://arxiv.org/abs/2303.15334.
[12] X. Wang, C. Fu, Z. Li, Y . Lai and J. He, “DeepFusionMOT: A 3D
multi-object tracking framework based on camera-LiDAR fusion with
deep association,”IEEE Robot. Autom. Lett., pp. 8260-8267, Jun. 2022.
[13] X. Li et al., “Poly-MOT: A polyhedral framework for 3D multi-object
tracking,” inProc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), 2023,
pp. 9391-9398.
[14] X. Li, D. Liu, Y . Wu, X. Wu, L. Zhao and J. Gao, “Fast-Poly: A fast
polyhedral algorithm for 3D multi-object tracking,”IEEE Robot. Autom.
Lett., vol. 9, no. 11, pp. 10519-10526, Nov. 2024.
[15] X. Wanget al., “MCTrack: A unified 3D multi-object tracking frame-
work for autonomous driving,”arXiv preprint, 2024. [Online]. Available:
arxiv.org/abs/2409.16149.
[16] X. Xu, W. Ren, X. Chen, H. Fan, Z. Han and H. Liu, “Exploiting multi-
modal synergies for enhancing 3D multi-object tracking,”IEEE Robot.
Autom. Lett., vol. 9, no. 10, pp. 8643-8650, Oct. 2024.
[17] B. Samuel, and R. Popoli,Design and Analysis of Modern Tracking
Systems.Norwood, MA, USA: Artech House Publishers, 1999.
[18] H. Caesar et al., “nuScenes: A multimodal dataset for autonomous
driving,” inProc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit.
(CVPR), 2020, pp. 11621-11631.
[19] A. Geiger, P. Lenz and R. Urtasun, “Are we ready for autonomous
driving? The KITTI vision benchmark suite,” inProc. IEEE/CVF Conf.
Comput. Vis. Pattern Recognit. (CVPR), 2012, pp. 3354-3361.
[20] S. Scheidegger, J. Benjaminsson, E. Rosenberg, A. Krishnan, and K.
Granstr¨om, “Mono-camera 3D multi-object tracking using deep learning
detections and PMBM filtering,” inProc. IEEE Intell. Veh. Symp. (IV),
2018, pp. 433-440.
[21] S. Pang, D. Morris, and H. Radha, “3D multi-object tracking using
random finite set-based multiple measurement models filtering (RFS-
M3) for autonomous vehicles,” inProc. IEEE Int. Conf. Robot. Autom.
(ICRA), 2021, pp. 13701-13707.
[22] J. Liu, L. Bai, Y . Xia, T. Huang, B. Zhu, and Q.-L. Han, “GNN-PMB:
A simple but effective online 3D multi-object tracker without bells and
whistles,”IEEE Trans. Intell. Veh., vol. 8, no. 2, pp. 1176-1189, Feb.
2023.
[23] J. Bai, S. Li, L. Huang, and H. Chen, “Robust detection and tracking
method for moving object based on radar and camera data fusion,”IEEE
Sens. J., vol. 21, no. 9, pp. 10761–10774, May 2021.
[24] C. Yang, X. Cao and Z. Shi, “Road-map aided Gaussian mixture labeled
multi-Bernoulli filter for ground multi-target tracking,”IEEE Trans. Veh.
Technol., vol. 72, no. 6, pp. 7137-7147, Jun. 2023.
[25] H. Wu, W. Han, C. Wen, X. Li, and C. Wang, “3D multi-object tracking
in point clouds based on prediction confidence-guided data association,”
IEEE Trans. Intell. Transp. Syst., vol. 23, no. 6, pp. 5668-5677, Jun.
2022.
[26] G. Guo and S. Zhao, “3D multi-object tracking with adaptive cubature
Kalman filter for autonomous driving,”IEEE Trans. Intell. Veh., vol. 8,
no. 1, pp. 84-94, Jan. 2023.
[27] P. Karle, F. Fent, S. Huch, F. Sauerbeck and M. Lienkamp, “Multi-modal
sensor fusion and object tracking for autonomous racing,”IEEE Trans.
Intell. Veh., vol. 8, no. 7, pp. 3871-3883, Jul. 2023.
[28] Y . Li et al., “FARFusion: A practical roadside radar-camera fusion
system for far-range perception,”IEEE Robot. Autom. Lett., vol. 9, no.
6, pp. 5433-5440, Jun. 2024.
[29] S. Feng et al., “Tightly coupled integration of LiDAR and vision for 3D
multiobject tracking,”IEEE Trans. Intell. Veh., early access, Jun. 13,
2024, doi: 10.1109/TIV .2024.3413733.
[30] X. Wang, C. Fu, J. He, S. Wang and J. Wang, “StrongFusionMOT: A
multi-object tracking method based on LiDAR-camera fusion,”IEEE
Sens. J., vol. 23, no. 11, pp. 11241-11252, Jun. 2023.
[31] A. Shenoi et al., “JRMOT: A real-time 3D multi-object tracker and a
new large-scale dataset,” inProc. IEEE/RSJ Int. Conf. Intell. Robots
Syst. (IROS), 2020, pp. 10335-10342.
[32] Z. Liu et al., “Robust target recognition and tracking of self-driving
cars with radar and camera information fusion under severe weather
conditions,”IEEE Trans. Intell. Transp. Syst., vol. 23, no. 7, pp.
6640–6653, Jul. 2022.
[33] S. Papais, R. Ren, S. Waslander, “SWTrack: Multiple hypothesis sliding
window 3D multi-object tracking,” inProc. IEEE Int. Conf. Robot.
Autom. (ICRA), 2024, pp. 4939-4945.
[34] F. Meyer, and J. L. Williams, “Scalable detection and tracking of
geometric extended objects,”IEEE Trans. Signal Process., vol. 69, no.
1, pp. 6283-6298, Oct. 2021.
[35] G. Ding, J. Liu, Y . Xia, T. Huang, B. Zhu, J. Sun, “LiDAR point cloud-
based multiple vehicle tracking with probabilistic measurement-region
association”, inProc. IEEE Int. Conf. Inf. Fusion (FUSION), 2024, pp.
1-8.
[36] J. Liu et al., “Which framework is suitable for online 3D multi-object
tracking for autonomous driving with automotive 4D imaging radar?”
inProc. IEEE Intell. Veh. Symp. (IV), 2024, pp. 1258-1265.
[37] J. Zeng, D. Mitra, M. Chen, E. Zhang, S. Chomal and R. Tharmarasa,
“Camera-assisted radar detection clustering for extended target track-
ing,”,IEEE Trans. Instrum. Meas, vol. 73, pp. 1-17, May 2024.
[38] J. Deng, Z. Hu, Z. Lu and X. Wen, “3D multiple extended object tracking
by fusing roadside radar and camera sensors”,IEEE Sens. J., vol. 25,
no. 1, pp. 1885-1899, Jan. 2025.
[39] H.-K. Chiu, J. Li, R. Ambrus ¸, and J. Bohg, “Probabilistic 3D multi-
modal, multi-object tracking for autonomous driving,” inProc. IEEE
Int. Conf. Robot. Autom. (ICRA), 2021, pp. 14227-14233.
[40] N. Baumann et al., “CR3DT: Camera-radar fusion for 3D detection and
tracking,” inProc. IEEE/RSJ Int. Conf. Intell. Robots Syst. (IROS), 2024,
pp. 4926-4933.
[41] Z. Zhang, J. Liu, Y . Xia, T. Huang, Q.-L. Han, and H. Liu, “LEGO:
Learning and graph-optimized modular tracker for online multi-object
tracking with point clouds,”IEEE Trans. Circuits Syst. Video Technol.,
early access, Aug. 20, 2025, doi: 10.1109/TCSVT.2025.3600881.
[42] H. Li, H. Liu, Z. Du, Z. Chen and Y . Tao, “MCCA-MOT: Multimodal
collaboration-guided cascade association network for 3D multi-object
tracking,”IEEE Trans. Intell. Transp. Syst., vol. 26, no. 1, pp. 974-989,
Jan. 2025.
[43] M. Y . Lee, C. D. W. Lee, J. Li and M. H. Ang, “DINO-MOT: 3D
multi-object tracking with visual foundation model for pedestrian re-
identification using visual memory mechanism,”IEEE Robot. Autom.
Lett., vol. 10, no. 2, pp. 1202-1208, Feb. 2025.
[44] M. Liang and F. Meyer, “Neural enhanced belief propagation for
multiobject tracking,”IEEE Trans. Signal Process., vol. 72, pp. 15-30,
Sep. 2023.
[45] S. Wei, M. Liang and F. Meyer, “A new architecture for neural enhanced
multiobject tracking,” inProc. IEEE Int. Conf. Inf. Fusion (FUSION),
2024, pp. 1-8.
[46] X. Weng, Y . Wang, Y . Man, and K. M. Kitani, “GNN3DMOT: Graph
neural network for 3D multi-object tracking with 2D-3D multi-feature
learning,” inProc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit.
(CVPR), 2020, pp. 6499–6508.
[47] Y . Zeng, C. Ma, M. Zhu, Z. Fan, and X. Yang, “Cross-modal 3D object
detection and tracking for auto-driving,” inProc. IEEE/RSJ Int. Conf.
Intell. Robots Syst. (IROS), 2021, pp. 3850-3857.
[48] K. Huang, and Q. Hao, “Joint multi-object detection and tracking with
camera-LiDAR fusion for autonomous driving,” inProc. IEEE/RSJ Int.
Conf. Intell. Robots Syst. (IROS), 2021, pp. 6983-6989.
[49] T. Wen, Y . Zhang, and N. M. Freris, “PF-MOT: Probability fusion based
3D multi-object tracking for autonomous vehicles,” inProc. IEEE Int.
Conf. Robot. Autom. (ICRA), 2022, pp. 700-706.
[50] A. Kim, G. Bras ´o, A. O ˇsep, and L. Leal-Taix ´e, “PolarMOT: How far
can geometric relations take us in 3D multi-object tracking?,” inProc.
Eur. Conf. Comput. Vis. (ECCV), 2022, pp. 41-58.
[51] F. Ruppel, F. Faion, C. Gl ¨aser, and K. Dietmayer, “Transformers for
multi-object tracking on point clouds,” inProc. IEEE Intell. Veh. Symp.
(IV), 2022, pp. 832-838.
[52] X. Chen et al., “TrajectoryFormer: 3D object tracking transformer with
predictive trajectory hypotheses,” inProc. IEEE/CVF Int. Conf. Comput.
Vis. (ICCV), 2023, pp. 18527-18536.
[53] Z. Pan, F. Ding, H. Zhong, and C. X. Lu, “Moving object detection and
tracking with 4D radar point cloud,” inProc. IEEE Int. Conf. Robot.
Autom. (ICRA), 2024, pp. 4480-4487.
[54] C. Luo, X. Yang, and A. Yuille, “Exploring simple 3D multi-object
tracking for autonomous driving,” inProc. IEEE/CVF Int. Conf. Comput.
Vis. (ICCV), 2021, pp. 10488-10497.
[55] F. Zeng, B. Dong, Y . Zhang, T. Wang, X. Zhang, and Y . Wei, “MOTR:
End-to-end multiple-object tracking with transformer,” inProc. Eur.

16
Conf. Comput. Vis. (ECCV), 2022, pp. 659-675.
[56] T. Meinhardt, A. Kirillov, L. Leal-Taixe, and C. Feichtenhofer, “Track-
Former: Multi-object tracking with transformers,” inProc. IEEE/CVF
Conf. Comput. Vis. Pattern Recognit. (CVPR), 2022, pp. 8844-8854.
[57] Z. Pang, J. Li, P. Tokmakov, D. Chen, S. Zagoruyko, and Y . X. Wang,
“Standing between past and future: Spatio-temporal modeling for multi-
camera 3D multi-object tracking,” inProc. IEEE/CVF Conf. Comput.
Vis. Pattern Recognit. (CVPR), 2023, pp. 17928-17938.
[58] Y . Hu et al., “Planning-oriented autonomous driving,” inProc.
IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR), 2023, pp.
17853-17862.
[59] J. Gu et al., “ViP3D: End-to-end visual trajectory prediction via 3D
agent queries,” inProc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit.
(CVPR), 2023, pp. 5496-5506.
[60] ´A. F. Garc´ıa-Fern´andez, J. L. Williams, K. Granstr ¨om, and L. Svensson,
“Poisson multi-Bernoulli mixture filter: Direct derivation and implemen-
tation,”IEEE Trans. Aerosp. Electron. Syst., vol. 54, no. 4, pp. 1883-
1901, Aug. 2018.
[61] F. Meyer et al., “Message passing algorithms for scalable multitarget
tracking,” inProc. IEEE, vol. 106, no. 2, pp. 221-259, Feb. 2018.
[62] S. Reuter, B. -T. V o, B. -N. V o and K. Dietmayer, “The labeled multi-
Bernoulli filter,”IEEE Trans. Signal Process., vol. 62, no. 12, pp. 3246-
3260, Jun. 2014.
[63] D. Svensson, “Derivation of the discrete-time constant turn rate and
acceleration motion model,” inProc. Sensor Data Fusion: Trends,
Solutions, Appl. (SDF), 2019, pp. 1-5.
[64] E. A. Wan and R. Van Der Merwe, “The unscented Kalman filter for
nonlinear estimation,” inProc. 2000 IEEE Adaptive Syst. for Signal
Process., Commun., and Control Symp., pp. 153-158.
[65] H. Rezatofighi, N. Tsoi, J. Gwak, A. Sadeghian, I. Reid, and S.
Savarese, “Generalized intersection over union: A metric and a loss
for bounding box regression,” inProc. IEEE/CVF Conf. Comput. Vis.
Pattern Recognit. (CVPR), 2019, pp. 658-666.
[66] J. Luiten et al. “HOTA: A higher order metric for evaluating multi-object
tracking,”Int. J. Comput. Vis., vol. 129, pp. 548–578, Oct. 2021.
[67] T. Yin, X. Zhou, and P. Krahenbuhl, “Center-based 3D object detection
and tracking,” inProc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit.
(CVPR), 2021, pp. 11784-11793.
[68] H. Wu, J. Deng, C. Wen, X. Li, C. Wang, and J. Li, “CasA: A cascade
attention network for 3D object detection from LiDAR point clouds,”
IEEE Trans. Geosci. Remote Sens., vol. 60, pp. 1-11, Aug. 2022.
[69] Y . Chen, J. Liu, X. Zhang, X. Qi, and J. Jia, “LargeKernel3D: Scaling
up kernels in 3D sparse CNNs,” inProc. IEEE/CVF Conf. Comput. Vis.
Pattern Recognit. (CVPR), 2023, pp. 13488-13498.
[70] S. Shi, X. Wang, and H. P. Li, “3D object proposal generation and
detection from point cloud,” inProc. IEEE/CVF Conf. Comput. Vis.
Pattern Recognit. (CVPR), 2019, pp. 16-20.
[71] W. Shi and R. Rajkumar, “Point-GNN: Graph neural network for 3D
object detection in a point cloud,” inProc. IEEE/CVF Conf. Comput.
Vis. Pattern Recognit. (CVPR), 2020, pp. 1711-1719.
[72] M. Nagy, N. Werghi, B. Hassan, J. Dias and M. Khonji, “RobMOT:
3D multi-object tracking enhancement through observational noise and
state estimation drift mitigation in LiDAR point clouds,” inIEEE Trans.
Intell. Transp. Syst., Jul. 4, 2025, doi: 10.1109/TITS.2025.3581980.
[73] S. Liu, W. Cao, C. Liu, T. Zhang and S. E. Li, “Convolutional unscented
Kalman filter for multi-object tracking with outliers,”IEEE Trans. Intell.
Veh., early access, Aug. 21, 2024, doi: 10.1109/TIV .2024.3446851.
[74] S. Feng et al., “Accurate and real-time 3D-LiDAR multiobject tracking
using factor graph optimization,”IEEE Sens. J., vol. 24, no. 2, pp. 1760-
1771, Jan. 2024.
[75] J. He, C. Fu, and X. Wang, J. Wang, “3D multi-object tracking based
on informatic divergence-guided data association,”Signal Process., vol.
222, pp. 109544, Sep. 2024.
[76] X. Wang et al., “A multi-modal fusion-based 3D multi-object tracking
framework with joint detection,”IEEE Robot. Autom. Lett., vol. 10, no.
1, pp. 532-539, Jan. 2025.
Guanhua Ding(Student Member, IEEE) received
the B.S. and M.Sc. degrees from Beihang University
(BUAA), Beijing, China, in 2020 and 2023, respec-
tively. He is currently pursuing the Ph.D. degree in
signal and information processing with the School of
Electronic Information Engineering, BUAA, Beijing,
China. His research interests include multi-object
tracking, extended object tracking, multi-sensor data
fusion, and random finite set theory.
Yuxuan Xia(Member, IEEE) received his M.Sc. in
communication engineering and Ph.D. in signal and
systems from Chalmers University of Technology,
Gothenburg, Sweden, in 2017 and 2022, respec-
tively. After obtaining his Ph.D., he first stayed at
the Signal Processing group, Chalmers University of
Technology as a postdoctoral researcher for a year,
and then he was with Zenseact AB and the Division
of Automatic Control, Link ¨oping University as an
Industrial Postdoctoral researcher for a year. He is
currently a researcher at the School of Automation
and Intelligent Sensing, Shanghai Jiaotong University. His main research
interests include sensor fusion, multi-object tracking and SLAM, especially for
automotive applications. He has organized tutorials on multi-object tracking
at the 2020-2025 FUSION conferences and the 2024 MFI conference. He has
received paper awards at 2021 FUSION and 2024 MFI.
Runwei Guan(Member, IEEE) is currently a re-
search fellow affiliated at Thrust of AI, Hong Kong
University of Science and Technology (Guangzhou).
He received his PhD degree from University of
Liverpool in 2024 and M.S. degree in Data Sci-
ence from University of Southampton in 2021. He
was also a researcher of the Alan Turing Insti-
tute and King’s College London. His research in-
terests include radar perception, multi-sensor fu-
sion, vision-language learning, lightweight neural
network, multi-task learning and statistical machine
learning. He has published more than 20 papers in journals and conferences
such as TIV , TITS, TMC, ESW A, RAS, Neural Networks, ICRA, IROS,
ICASSP, ICME, etc. He serves as the peer reviewer of TITS, TNNLS, TIV ,
TCSVT, ITSC, ICRA, RAS, EAAI, MM, etc.
Qinchen Wu(Student Member, IEEE) received the
B.S. and M.Sc. degrees from Beihang University
(BUAA), Beijing, China, in 2019 and 2021, respec-
tively. He is currently working toward the Ph.D.
degree in signal and information processing with
the School of Electronic Information Engineering,
Beihang University, Beijing, China. His research
interests include random finite set, group target
tracking, and multi-sensor data fusion.

17
Tao Huang(Senior Member, IEEE) received his
Ph.D. in Electrical Engineering from The University
of New South Wales, Australia, in 2016. Dr. Huang
is a Senior Lecturer at James Cook University (JCU),
Cairns, Australia. He is the Head of the International
Partnerships in the College of Science and Engineer-
ing and the Intelligent Computing and Communica-
tions Lab Director. He was an Endeavour Australia
Cheung Kong Research Fellow, a visiting scholar at
The Chinese University of Hong Kong, a research
associate at the University of New South Wales, and
a postdoctoral research fellow at James Cook University. Before academia,
Dr. Huang was a senior engineer, senior data scientist, project team lead, and
technical lead. Dr. Huang has received the Best Paper Award from the IEEE
WCNC, the IEEE Access Outstanding Associate Editor of 2023 and 2024,
and the IEEE Outstanding Leadership Award. He is an Associate Editor of
Scientific Reports (Nature Portfolio), IEEE Open Journal of Communications
Society, IEEE Access, and IET Communications. His research interests in-
clude deep learning, intelligent sensing, computer vision, pattern recognition,
wireless communications, system optimization, electronics systems, and IoT
security.
Weiping Ding(M’16-SM’19) received the Ph.D.
degree in Computer Science, Nanjing University of
Aeronautics and Astronautics, Nanjing, China, in
2013. From 2014 to 2015, he was a Postdoctoral
Researcher at the Brain Research Center, National
Chiao Tung University, Hsinchu, Taiwan, China.
In 2016, he was a Visiting Scholar at National
University of Singapore, Singapore. From 2017 to
2018, he was a Visiting Professor at University of
Technology Sydney, Australia. His main research
directions involve deep neural networks, granular
data mining, and multimodal machine learning. He ranked within the top 2%
Ranking of Scientists in the World by Stanford University (2020-2024). He has
published over 360 articles, including over 170 IEEE Transactions papers. His
twenty authored/co-authored papers have been selected as ESI Highly Cited
Papers. He has co-authored five books. He has holds more than 50 approved
invention patents, including three U.S. patents and one Australian patent. He
serves as an Associate Editor/Area Editor/Editorial Board member of more
than 10 international prestigious journals, such as IEEE TNNLS, IEEE TFS,
IEEE/CAA Journal of Automatica Sinica, IEEE TETCI, IEEE TITS, IEEE
TAI, Information Fusion, Information Sciences, Neurocomputing, Applied
Soft Computing, Engineering Applications of Artificial Intelligence, Swarm
and Evolutionary Computation, et al. He was/is the Leading Guest Editor of
Special Issues in several prestigious journals, including IEEE TEC, IEEE TFS,
Information Fusion, Information Sciences, et al. Now he is the Co-Editor-in-
Chief of Journal of Artificial Intelligence and Systems, Journal of Artificial
Intelligence Advances, and Sustainable Machine Intelligence Journal.
Jinping Sun(Member, IEEE) received the M.Sc.
and Ph.D. degrees from Beihang University
(BUAA), Beijing, China, in 1998 and 2001, respec-
tively. Currently, he is a Professor with the School of
Electronic Information Engineering, BUAA. His re-
search interests include statistical signal processing,
high-resolution radar signal processing, target track-
ing, image understanding, and robust beamforming.
Guoqiang Mao(Fellow, IEEE) is a Chair Professor
and the Director of the Center for Smart Driving
and Intelligent Transportation Systems, Southeast
University. From 2014 to 2019, he was a Leading
Professor, the Founding Director of the Research
Institute of Smart Transportation, and the Vice-
Director of the ISN State Key Laboratory, Xidian
University. Before that, he was with the University
of Technology Sydney and The University of Syd-
ney. He has published 300 papers in international
conferences and journals that have been cited more
than 15,000 times. His H-index is 57 and was in the list of Top 2% most-cited
scientists worldwide by Stanford University in 2022, 2023, and 2024 both by
Single Year and by Career Impact. His research interests include intelligent
transport systems, the Internet of Things, wireless localization techniques,
mobile communication systems, and applied graph theory and its applications
in telecommunications. He is a fellow of AAIA and IET. He received the
“Top Editor” Award for outstanding contributions to IEEE Transactions on
Vehicular Technology in 2011, 2014, and 2015. He has served as the chair, the
co-chair, and a TPC member in several international conferences. He has been
serving as the Vice-Director of Smart Transportation Information Engineering
Society and Chinese Institute of Electronics since 2022. He was the Co-Chair
of the IEEE ITS Technical Committee on Communication Networks from
2014 to 2017. He is an Editor of IEEE Transactions on Intelligent Transporta-
tion Systems (since 2018), IEEE Transactions on Wireless Communications
(2014–2019), and IEEE Transactions on Vehicular Technology (2010–2020).