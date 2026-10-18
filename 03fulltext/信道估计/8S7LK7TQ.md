---
title: "SSNet Flexible and Robust Channel Extrapolation for Fluid Antenna Systems Enabled by a Self-Supervised Learning Framework"
zotero_key: "8S7LK7TQ"
pdf_key: "QEOR43QA"
doi: "10.1109/jsac.2025.3619472"
collection: "信道估计"
source: "Open-access PDF (pypdf extraction)"
page_mapping: unverified
---

# SSNet Flexible and Robust Channel Extrapolation for Fluid Antenna Systems Enabled by a Self-Supervised Learning Framework — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
SSNet: Flexible and robust channel extrapolation
for fluid antenna systems enabled by an
self-supervised learning framework
Yuan Gao, Yiming Liu, Runze Yu, Shengli Liu, Yanliang Jin, Shunqing Zhang, Shugong Xu,Fellow, IEEE,
Xiaoli Chu
Abstract—Fluid antenna systems (FAS) signify a pivotal ad-
vancement in 6G communication by enhancing spectral efficiency
and robustness. However, obtaining accurate channel state infor-
mation (CSI) in FAS poses challenges due to its complex physical
structure. Traditional methods, such as pilot-based interpolation
and compressive sensing, are not only computationally intensive
but also lack adaptability. Current extrapolation techniques
relying on rigid parametric models do not accommodate the
dynamic environment of FAS, while data-driven deep learning
approaches demand extensive training and are vulnerable to
noise and hardware imperfections. To address these challenges,
this paper introduces a novel self-supervised learning network
(SSNet) designed for efficient and adaptive channel extrapolation
in FAS. We formulate the problem of channel extrapolation in
FAS as an image reconstruction task. Here, a limited number
of unmasked pixels (representing the known CSI of the selected
ports) are used to extrapolate the masked pixels (the CSI of
unselected ports). SSNet capitalizes on the intrinsic structure of
FAS channels, learning generalized representations from raw CSI
data, thus reducing dependency on large labelled datasets. For
enhanced feature extraction and noise resilience, we propose a
mix-of-expert (MoE) module. In this setup, multiple feedforward
neural networks (FFNs) operate in parallel. The outputs of the
MoE module are combined using a weighted sum, determined by
a gating function that computes the weights of each FFN using a
softmax function. Extensive simulations validate the superiority
of the proposed model. Results indicate that SSNet significantly
outperforms benchmark models, such as AGMAE and long short-
term memory (LSTM) networks by using a much smaller labelled
dataset. A key observation is that the proposed model is more
effectively trained using a small unmasked ratio of known CSI.
Specifically, the proposed SSNet trained using CSI of 10 % total
ports outperforms that trained using CSI of 25 % and 50 %
total ports. This is because using a smaller number of known
CSIs during training, the proposed model is forced to learn
more effective channel correlation for channel extrapolation at
the expense of higher training complexities. Ablation experiments
reveal substantial performance gains from the MoE module’s
integration. Furthermore, zero-shot learning experiments show a
moderate performance degradation of about 3-5 dB, underscor-
This work was supported in part by Shanghai Natural Science Foundation
under Grant 22ZR1422200, and in part supported by the 6G Science and Tech-
nology Innovation and Future Industry Cultivation Special Project of Shanghai
Municipal Science and Technology Commission under Grant 24DP1501001.
(Corresponding author: Xiaoli Chu)
Yuan Gao, Yiming Liu, Runze Yu, Shengli Liu, Yanliang Jin and
Shunqing Zhang are with the School of Communication and Information
Engineering, Shanghai University, China, email: gaoyuansie@shu.edu.cn,
1975231949@shu.edu.cn, urleaves@shu.edu.cn, victoryliu@shu.edu.cn,
jinyanliang@staff.shu.edu.cn and shunqing@shu.edu.cn.
Shugong Xu is with Xi’an Jiaotong-Liverpool University, Suzhou, China,
email: shugong.xu@xjtlu.edu.cn.
Xiaoli Chu is with the Department of Electronic and Electrical Engineering,
the University of Sheffield, UK, e-mail: x.chu@sheffield.ac.uk.
ing the model’s robust generalization ability. Finally, the inference
speed experiments illustrate that the proposed model outperforms
the benchmark models dramatically at the expense of a slightly
longer execution time of 1.13 ms, 2.9 ms, and 3.12 ms on NVIDIA
RTX 4090, 4060, and 3060 graphics processing units (GPU)s,
respectively.
Index Terms—Fluid Antenna System, Channel Extrapolation,
Self-Supervised Learning, Flexibility, Robustness
I. INTRODUCTION
In the evolution towards the sixth generation mobile com-
munications (6G), fluid antenna systems (FAS) present an
innovative paradigm by dynamically adjusting the antenna’s
form and position to overcome the physical limitations of
traditional antennas [1], [2]. The core advantage of FAS
lies in its ability to control the spatial distribution of fluid
radiating elements through software, achieving multidimen-
sional flexibility such as frequency, radiation pattern, and
polarization. This enables the system to avoid deep fading and
enhance diversity gain in dense multipath environments [3].
Research indicates that FAS can significantly increase spectral
efficiency, provide new degrees of freedom for massive user
access [4], [5] and reduce outage probability [6]–[8].
A critical factor in harnessing the potential of FAS is
obtaining accurate channel state information (CSI). Traditional
CSI acquisition methods, reliant on pilot-based interpolation
or compressive sensing, face prohibitive overheads in case
of the high-dimensional spatial domain in FAS [9]–[12].
Channel extrapolation techniques [13]–[15] serve as a crucial
element in unlocking the potential of FAS by reconstructing
complete channel characteristics from partial observation data.
Existing research on channel extrapolation can be categorized
into two main approaches, and the first relies on parametric
models [16]–[21], such as sparse bayesian learning, which
employs sparsity across multiple domains to achieve chan-
nel extrapolation [22]. However, this approach depends on
prior assumptions about channel structure, making it less
adaptable to the highly dynamic nature of FAS. The second
approach is data-driven, employing methods like deep neural
networks (DNN) [23], [24] to extrapolate CSI [13], [25], [26].
Nonetheless, the training complexity of these models increases
exponentially with antenna array size and they are highly
sensitive to hardware imperfections [27].
Due to the importance of acquiring CSI to unleash the
potential of FAS, research on channel extrapolation of FAS
arXiv:2509.17797v1  [eess.SP]  22 Sep 2025

2
have been rolled out [28]. [29] proposes an asymmetric graph
masked autoencoder (AGMAE) for fluid antenna system chan-
nel extrapolation. Simulation results demonstrate that AGMAE
achieves accurate CSI reconstruction with low computational
complexity, even with a small number of observed antennas,
at the ratio of 20%. A masked language model is proposed for
channel extrapolation of FAS and simulation results show that
complete CSI can be effectively extrapolated from incomplete
observations, improving port selection accuracy and reducing
outage probability [30]. [31] uses deep reinforcement learning
to jointly optimize port selection and precoding in a fluid
antenna system for integrated sensing and communication
(ISAC) [32]–[35]. When only partial channel state information
is available, a masked autoencoder is used for channel extrapo-
lation, achieving significant sum-rate improvements compared
to conventional methods. A model-driven channel extrapola-
tion method for massive fluid antenna systems, leveraging the
inherent structure of Jake’s rich-scattering channel model is
proposed in [36], and achieves high accuracy with minimal
training data and robustly extrapolates CSI for all antenna
ports.
However, research on channel extrapolation of FAS are still
in its infancy and the following challenges have not been well
addressed.
•Lack of flexibility: The existing methods are not designed
to handle a variable number of CSI inputs. They often
rely on fixed-size input vectors, making them inflexible
and unable to adapt to scenarios where the number of
observable ports changes. This limits their applicability
to real-world, dynamic environments where the number
of available CSI measurements might vary.
•Large dataset required: The existing models require huge
dataset volume to train, for example 800,000 and 120,000
samples are using in training the models in [29] and [31],
respectively. Although such large volume dataset can be
relatively easy acquired via simulation, it is inevitable to
use measurement CSI data for model training to ensure
the applicability of the models in practical scenarios
and it is time-consuming and expensive to carry out
measurement for such large data volume.
•Poor Robustness to noise: The simulation results pre-
sented in the existing research focus on normalized mean
squared error (NMSE) under noise-free conditions. The
absence of experiments with added noise makes their
applicability in noisy scenarios in doubt.
Self-supervised learning has emerged as a transformative
approach to resolve the above challenges [37]–[39] and have
been applied in various fields of wireless communications
[25], [40], [41]. A key advantage of self-supervised learning
lies in its ability to reduce dependency on labeled datasets
[42], [43], which are costly to collect and often raise privacy
concerns. For instance, contrastive learning and autoencoder-
based frameworks enable models to learn generalized rep-
resentations directly from raw CSI data, achieving human
activity recognition accuracy comparable to supervised meth-
ods much less labeled data [44]. [42] indicates that self-
supervised learning outperforms supervised learning using the
same amount of labeled data in channel estimation for a RIS-
assisted communication system. Additional, self-supervised
learning excels at extracting spatiotemporal and frequency-
domain features from high-dimensional CSI. Techniques like
channel charting leverage autoencoders to map CSI into low-
dimensional latent spaces, preserving spatial correlations for
user localization in MIMO systems [45]. Channel charting
is also exploited in channel prediction by exploiting spatial
relationships between known estimates that are embedded in
the channel chart [46]. Models trained with self-supervised
learning often demonstrate better generalization to unseen data
and robustness to noisy or corrupted inputs [47], [48]. Further,
by learning underlying patterns and structures rather than
memorizing specific input lengths, self-supervised learning
can handle variations more effectively [49]. The ability of
self-supervised learning to handle variations in input lengths
is crucial for applications involving natural language pro-
cessing (NLP) [50], image processing [51], and other high-
dimensional data tasks.
Inspired by the above research, we proposed a self-
supervised learning-based network (SSNet) for channel extrap-
olation in FASs, tackling the shortcomings of prior work. The
key contributions are summarized as follows:
•We formulate channel extrapolation in FAS as an image
reconstruction task. In this framework, a few unmasked
pixels (known CSI of selected ports) guide the extrapo-
lation of masked pixels (CSI of unselected ports). Our
SSNet leverages the inherent structure of FAS channels
to learn generalized representations directly from raw
CSI data, thereby minimizing the need for extensive la-
beled datasets. Our detailed simulations demonstrate that
SSNet significantly surpasses benchmark models, such
as AGMAE [29] and long short-term memory (LSTM)
networks, utilizing just 2.5 % of the channel dataset.
•For enhanced feature extraction and noise resilience, we
propose a mix-of-expert (MoE) module. In this setup,
multiple feedforward neural networks (FFNs) operate in
parallel. The outputs of the MoE module are combined
using a weighted sum, determined by a gating function
that computes the weights of each FFN using a softmax
function. Ablation experiments reveal substantial perfor-
mance gains from the MoE module’s integration.
•A critical finding is that our model could be trained more
effectively with a smaller proportion of unmasked known
CSI. Specifically, the SSNet trained with CSI from 10
% of total ports outperforms versions trained with 25
% and 50 %. This is because a smaller dataset compels
the model to learn more effective channel correlations
for extrapolation at the expense of increased training
complexity.
•Additionally, zero-shot learning experiments indicate a
moderate reduction in performance, around 3-5 dB, high-
lighting the model’s robust generalization capabilities. In-
ference speed tests further reveal that our model achieves
significantly better performance over benchmark models,
despite slightly longer execution times of 1.13 ms, 2.9
ms, and 3.12 ms on NVIDIA RTX 4090, 4060, and 3060

3
TABLE I
Mathematical Symbols and Meanings
Symbol Meaning
dX Port spacing in thex-direction
dy Port spacing in they-direction
WX Physical dimension of FAS in thex-direction
WY Physical dimension of FAS in they-direction
Nx Number of ports in thex-direction
Ny Number of ports in they-direction
NS Total number of ports
Σclarke(i, j) Spatial correlation matrix of Clarke’s model
pi Position of thei-th port
pj Position of thej-th port
U Matrix of eigenvectors
A Diagonal matrix of eigenvalues
g CSI matrix
δ2 Path loss
G Matrix of i.i.d. complex Gaussian random variables
ub CSI of observed ports
Wp Projection matrix
xp Patch embeddings
Epos Positional embedding matrix
x′p Updated patch embedding sequence
ωk Frequency vector
Q Query matrix
K Key matrix
V Value matrix
dk Dimension of key vectors
xout Output of transformer block
z Latent feature representation from encoder
Wd Projection matrix of decoder
z′ Projected latent representation
Edecpos Positional embedding matrix for decoder
z′′ Updated latent representation
zout Output of decoder transformer block
Wr Reconstruction matrix
y Reconstructed patches
Y Reconstructed CSI
LCON Contrastive loss
LNMSE Normalized mean squared error loss
L Combined loss function
Ei Thei-th expert network in MoEBlock
G Gating network in MoEBlock
E Number of experts
K Number of activated experts per token
W(j)e1 First-layer weight matrix of thej-th expert
W(j)e2 Second-layer weight matrix of thej-th expert
Wg Weight matrix of the gating network
bg Bias vector of the gating network
π Gating scores (vector of expert affinities)
sk Gating weight for thek-th selected expert
lk Index of thek-th selected expert
ωk Frequency component for positional encoding
GPUs, respectively.
The structure of this paper is as follows. Section V presents
the system model for the FAS communication systems and the
definition of the channel prediction problem. Section III intro-
duces our proposed SSNet model in detail. Section IV details
our experimental results using simulated and measurement CSI
data with in-depth discussion. Section II offers concluding
remarks and future directions. Mathematical notations in this
manuscript can be found in Table I.
II. SYSTEMMODELANDCHANNELEXTRAPOLATION
As illustrated in Fig. 1, we consider a communication
system with one base station (BS) andKusers, where the BS
provide communication service for all theKusers with the
Fig. 1. An illustration for communication system with one base station and
N users equipped with FAS.
same time-frequency resource. BS implementedMantennas
with fixed locations and each user is equipped with an FAS.
The FAS is in shape of a 2D plane with a total number ofN S
switchable ports, which are uniformly distributed in a planar
surface with physical sizeW S. Thus, the spacing between ports
in thexandydirections is given by:
(
dX = WXNX−1 ,
dY = WYNY−1 , (1)
whereW X andW Y are the physical dimensions of the FAS in
thexandydirections, respectively, satisfyingW S =W X×WY.
Nx andN y are the number of ports in thexandydirections,
respectively, satisfyingN S =N X ×N Y.
We exploit Clarke’s isotropic scattering model [52], [53]
to compute the wireless channel of the FAS and the spatial
correlation matrixΣ clarke for two ports located at positions
pi = (xi, yi)andp j = (xj, yj)is calculated as:
Σclarke(i, j) =sinc(2· ∥pi −p j∥),(2)
where sinc(x) = sin(πx)πx and∥p i −p j∥is the Euclidean
distance between the two ports.
The spatial correlation matrixΣ clarke is decomposed into its
eigenvalues and eigenvectors:
Σclarke =UAU H ,(3)
whereUis the matrix of eigenvectors, andAis the diagonal
matrix of eigenvalues. The CSI matrixgis generated using
the following formula:
g=
√
δ2 ·U √AG,(4)
whereδ 2 is the path loss, andGis a matrix of independent
and identically distributed (i.i.d.) complex Gaussian random
variables with zero mean and variance 12.
In the context of FAS, the relationship between the physical
location of the antenna ports and the corresponding CSI
is inherently bijective. This bijective mapping, denoted as
Φg :{g B} → {gA}, ensures that each port’s position uniquely
determines its channel characteristics. The primary objective

4
Fig. 2. The proposed architecture for CSI extrapolation in FAS.
of channel extrapolation is to infer the CSI of unobserved ports
bgA based on the CSI of observed portsg B and minimize the
difference between extrapolated CSI bgA and real CSIg A. This
can be formally expressed as:
min
f(·)
(|bgA −g A|2).(5)
wheref(·)represents the mapping operation between the the
CSI of observed ports and the CSI of unobserved ports.
III. SELF-SUPERVISED LEARNING-BASED NETWORK
To extrapolate the complete CSI of all the switchable ports
using the CSI of a limited number of observable ports, we
propose an self-supervised learning-based model for channel
extrapolation in FAS. We formulate the channel extrapolation
of FAS as an image reconstruction problem, aiming to re-
construct all the pixels of an image-like structure (i.e., the
complete CSI of all the switchable ports) using the unmasked
pixels (CSI of the observable ports). Our method leverages
the principles of MAE, i.e., an encoder-decoder architecture,
where the encoder extracts the latent representation of the
unmasked CSI, which are subsequently exploited by the
decoder to reconstructs the full CSI. The architecture is
designed to handle the high-dimensional and non-linear nature
of FAS channels, while maintaining computational efficiency
and generalization capabilities.
A. CSI preprocessing
To model the process that the CSI of only a subset of ports
are exploited to extrapolate the CSI of all switchable ports, we
first perform masking on the CSI of all portsg∈R NS×2M ,
whereN S andMare the number of antennas at the BS and of
the FAS.2indicates that a CSI contains a real and imaginary
part. To mimic the channel acquisition process in practical
FAS, the ports with known CSI are randomly selected and the
percentage of unknown CSI is denoted as the mask ratioM r ∈
(0,1). Due to the limited overhead for channel acquisition in
FAS,M r is close to 1 in practical systems. Removing the CSI
of the masked ports and reshaping the CSI of unmasked ports

5
leads to the CSI of observable portsu b ∈R No×2M , where
No =N S ×M r is the number of observable ports.
B. Encoder
ub is the input of the encoder, and is first linearly projected
into a latent representationx p in high-dimensional latent space
as:
xp =u b ·W p,(6)
whereW p ∈R 2M×d model is a learnable projection matrix.x p ∈
RNo×dmodel, whered model is the embedding dimension.
To incorporate the spatial information of the antenna ports,
positional encodingE pos added element-wise to the embed-
dingx p as :
x′p =x p +E pos.(7)
To ensure thatE pos is channel-model-invariant, we adopt
the 2D sine-cosine positional encoding that is only determined
by the physical location of the port (i,j), whereiandj
are the location index of the port in horizontal and vertical
axis, respectively. For each antenna port position(i, j)in the
FAS grid, we generate aD-dimensional positional embedding
vectorE pos(i, j)∈R dmodel, whereE pos(i, j)is calculated as
follows:
Epos(i, j) =Concat(Erow(i),E col(j)),(8)
whereE row,E col ∈R No×dmodel/2.E row andE col are the posi-
tioning encoding in horizontal and vertical axis, respectively.
Erow(i,2k) = sin(i·ω k)(9)
Erow(i,2k+ 1) = cos(i·ω k)(10)
where0≤k < D/4. This alternating sine-cosine pattern
provides unique representations while maintaining linear re-
lationships between positions.ω k is the angular frequency
that forms a geometric progression across the embedding
dimension:
ωk = 1100002k/D ,0≤k <⌊D/4⌋,(11)
wherekis the frequency index. This exponential decay sched-
ule ensures wavelengths span multiple orders of magnitude,
capturing both fine-grained and coarse spatial relationships.
For the column indexj, we compute the remainingD/2
dimensions:
Ecol(j,2k) = sin(j·ω k)(12)
Ecol(j,2k+ 1) = cos(j·ω k)(13)
using thesamefrequency componentsω k as the row encoding.
The patch embeddings with positional information are then
passed through a series of encoder block. Each encoder block
is a s a stack of a multi-head self-attention (MSA) module, an
MoE, an MSA and a feed forward network (FFNs) interleaved
with residual connections and layer normalization (Layer-
Norm). The MSA module captures the relationships between
different observable antenna ports by computing attention
scores:
MSA(Q,K,V) =Concat(head 1, ...,headh)W O,(14)
whereQ=x ′pW Q,K=x ′pW K, andV=x ′pW V are the
query, key, and value matrices of the inputx ′p, respectively.
W O ∈R hdv×dmodel is the learnable metric, whereh,d v and
dmodel are the number of heads, the dimension of value metric,
the dimension of encoder. MSA basically concatenates the
attention of all thehheads. head i is the attention of thei-
th head, which is calculated as:
headi =Attention(x ′pW Qi ,x ′pW Ki ,x ′pW Vi ),(15)
where Attention(x ′pW Qi ,x ′pW Ki ,x ′pW Vi )is the self-attention,
which is calculated as:
Attention(x′pW Qi ,x ′pW Ki ,x ′pW Vi )
=softmax
 
x′pW Qi x′pW Ki√dk ! x′pW Vi , (16)
whereW Qi ∈R dmodel×dk,W Ki ∈R dmodel×dk, andW Vi ∈
Rdmodel×dv are learnable projection metrics of the query, key,
and value for thei-th head, respectively. A residual connection
if performed, then follows a LayerNorm as:
x′′p = (LayerNorm(x′p +MSA(x ′p))).(17)
To further enhance the feature extraction capabilities and
noise robustness of the SSNet framework, we integrate MoE
layers subsequently. As illustrated in Fig. 2, the MoE com-
prisesEexpert networks{E 1, ...,EE}and a trainable gating
networkG. Each expert implements a nonlinear transforma-
tion:
Ej(x′′p) =σ x′′pW(j)e1  W(j)e2 (18)
whereσdenotes the GELU activation function [54], with
weight matricesW (j)e1 ∈R D×Dh,W (j)e2 ∈R Dh×D andD h =
4Dfollowing the hidden dimension expansion convention in
Transformers [50].
The gating network computes expert selection probabilities
using a softmax-activated linear transformation:
g=softmax
 
x′′pWg +b g ,(19)
whereW g ∈R D×E is the learnable metric for gating. To
maintain computational efficiency, we employ top-Ksparse
activation:
{sk}Kk=1 =TopK(g, K)(20)
where only the top-Kexperts process each input token, which
preserves the capability of the model and effectively reduces
the computational complexity compared to dense activation.
The final output aggregates weighted expert contributions
with dropout regularization of probabilityp:
x′′′p =Dropout
 KX
k=1
sk · Elk (x)
!
.(21)
x′′′p is further computed by a stack of MSA and FFN
interleaved with residual connections and LayerNorm as:
x′′′′′p =LayerNorm(x ′′′′p +FFN(x ′′′′p )),(22)
where
x′′′′p =LayerNorm(x ′′′p +MSA(x ′′′p )),(23)

6
and FFN(·)is the computing of the multilayer perceptron
(MLP) [55].
x′p is computed through Eq. (14) (22) forN/2times, which
results in the output of the encoderx enc.
C. Decoder
The decoder is designed to be lightweight, with fewer layers
and a smaller hidden dimension compared to the encoder. It
takes the latent representation from the encoder and appends
mask tokens to reconstruct the full CSI. The decoder uses
a lightweight vision Transformer (ViT) to exploit the local
correlations and smoothness of the FAS channels. This local
diffusion mechanism allows the decoder to efficiently recover
the CSI of the masked ports by propagating information from
the observable ports. The latent representationx enc from the
encoder is first projected into a lower-dimensional space using
a linear transformation:
y=x encWd,(24)
whereW d is a learnable projection matrix, andz ′ ∈
RNo×Ddecoder is the projected latent representation with re-
duced dimensionalityD decoder.
Same as the positioning encoding of the encoder, channel-
invariant 2D sine-cosine positional encodingE decpos are added
to the projected latent representationyto incorporate spatial
information:
y′ =y+E decpos.(25)
The decoder applies a series of lightweight transformer
blocks to process the latent representation. Each block is a
stack of an MSA module, an FFN interleaved with residual
connections and LayerNorm. The computing of each Trans-
former for a givenzis given as:
z′′ =LayerNorm(z ′ +FFN(z ′)),(26)
wherez ′ is calculated as:
z′ =LayerNorm(z+MSA(z)),(27)
where MSA(·)is given in Eq. (14).y ′ is computed by Eq. (26)
and (27) forNtimes, which results in the output of decoder
ydec.
D. Output
The output of the decoder isy dec passed through a re-
construction head, which maps the latent representation back
to the original pixel space. This is achieved using a linear
projection:
z=y decWr,(28)
whereW r is the reconstruction matrix, andz∈R NS×2M
represents the reconstructed patches.
Finally, the reconstructed patches are reshaped back into
the original CSI format using the unpatchify operation. This
involves rearranging the patch sequence into 2-dimensional:
bg=Reshape(y),(29)
.
IV. SIMULATION
A. Simulation Settings
In our simulations, we consider a downlink system where
a base station equipped withM= 8fixed-position antennas
communicates withK= 8userss, each employing a two-
dimensional FAS. The FAS has a physical size ofW s and is
uniformly distributed withN s = 16×32switchable ports. The
operating frequency is 3.5 GHz, corresponding to a wavelength
ofλ= cf , wherecis the speed of light. The path loss is
characterized byδ 2 = 1. The settings for simulation can be
found in Table II.
TABLE II
Simulation Settings
Parameter Settings
BS Antennas (M) 8
Antenna System Type 2D Fluid Antenna System (FAS)
FAS Physical Size (W s)8×16&2×4cm 2
Switchable Ports (N s) 16×32 (512 in total)
Operating Frequency (f) 3.5 GHz
Wavelength (λ)8.57cm
Path Loss (δ 2) 1
Signal to noise ratio0,10,20dB
The dataset consists of 20,000 noise-free channel samples,
which is divided into training and testing sets with an 80:20
ratio. The quality of the channel extrapolation is evaluated
using the NMSE calculated as follows:
LNMSE =E
"
1
MN
NX
m=1
MX
n=1
(bgmn −g mn )2
#
,(30)
whereMandNrepresent the number of masked ports utilized
in each sample and the number of samples tested, respectively.
bgmn represents the predicted CSI for them-th masked port
of then-th sample,g mn represents the true masked CSI. The
NMSE is normalized by the energy of the target CSI, ensuring
that the it is scale-invariant and focuses on the relative error.
For comparison, we adopt AGMAE as the benchmark model
and use 800,000 noise-free channel samples for training, which
is same as that in [29]. Another benchmark is the long short-
term memory (LSTM), which has been widely used in series
prediction tasks, such as time-domain channel prediction [13].
LSTM is tailored to predict the masked CSI using the known
CSI.
B. Model Training
The proposed model is traning in a self-supervised manner
and the training configurations are summarized in Table III.
Specifically, we employed the AdamW optimizer, configured
with an initial learning rate of1.5×10 −4, a weight decay
of 0.05, and a cosine decay schedule for the learning rate.
Techniques like color jittering, drop path, or gradient clipping
are excluded to maintain simplicity. All Transformer blocks
are initialized via the Xavier weight initialization method, with
a batch size of 64 and a 40-epoch warm-up period included
in the training process. SSNet is rained using fixed masking
ratios of 75% and 90% (denoted as SSNet (25%) and SSNet
(10%) in the following context, respectively) on FAS of2×4

7
Fig. 3. An illustration for training process of SSNet trained with various
mask ratio.
TABLE III
Pre-training setting.
Training Settings Settings
Optimizer AdamW
Base learning rate 1.5e-4
Weight decay 0.05
Optimizer momentumβ 1, β2 = 0.9,0.98
Batch size 64
Learning rate schedule cosine decay
Warmup epochs 40
Augmentation Random Resized Crop
Dropout probability 0.1
Number of total experts 4
Number of activated experts 2
Training hardware platform NVIDIA RTX 4090
Testing hardware platform NVIDIA RTX 4090, 4060 and 3060
cm and8×16cm to ensure the model adapts to a range of
observation conditions. During evaluation, we test the model
on datasets with varying masking ratios to confirm its ability
to generalize. Experiments are performed using PyTorch 2.0.1
and DGL 1.1.2, with computations accelerated on an NVIDIA
GeForce RTX 4090 GPU.
Fig. 3 illustrates the change of loss for SSNet (10%) and
SSNet (25%) during training, which demonstrate a consistent
decline, starting from an initial value of approximately 2. Over
the 40 warm-up epochs, the loss decreases at distinct rates,
settling at the order of10 −2. Beyond this phase, the loss
decreases and eventually stabilize at10 −4. Notably, the loss
of SSNet (10%) keeps approximately constant at the order of
10−2 for over 30 epochs, which is much larger than that of
SSNet (25%), indicating that it is more challenging to train
SSNet with a smaller percentage of observed ports.
C. Results Analysis
1) Channel extrapolation accuracy:The extrapolation ac-
curacy of the proposed SSNet is comprehensively evaluated
against AGMAE [29] under varying channel environments and
mask ratios.
We first compare the performance of SSNet and AGMAE
quantitatively. Fig. 4 and 5 demonstrate the real part of the
channel extrapolation for2×4cm FAS with SNR of 0 and
20 dB with 10% observed ports. Specifically, the comparison
between Fig. 4(b)-4(d) and 5(b)-5(d) indicates that it is more
challenging to extrapolate FAS channel in 0 dB than 20
dB scenarios, which is intuitive. In addition, Fig. 5(b)-5(d)
demonstrate that SSNet (10%) and SSNet (25%) outperform
AGAME at 20 dB scenarios. The performance gap between
AGAME and SSNet (either SSNet (10%) and SSNet (25%))
becomes more significant at 0 dB scenarios, as illustrated in
Fig. 4(b)-4(d). This indicates that SSNet shows high robustness
to noise, while AGMAE works poorly at 0 dB scenarios.
As the Clarke channel is modeled as complex Gaussian and
symmetric, the simulation results of the imaginary part convey
essentially the same information as the real part, and are
omitted for conciseness.
To further support our quantitative observations, we carried
out quantitative comparison in Fig. 6 and 7, where both SSNet
(25%) and SSNet (10%) significantly outperform AGMAE
and LSTM with various percentage of observed ports. For
instance in Fig. 6(a), at 10% observed ports with SNR of 0
dB, SSNet (10%), SSNet (25%), AGMAE and LSTM achieve
NMSE of around−10.2dB,−9.1dB,−4.7dB and−0.4
dB, respectively. SSNet (10%) and SSNet (25%) outperform
AGMAE by around 117% and 93%, respectively. Illustrated
in Fig. 6(a), at 10% observed ports with SNR of 20 dB, SSNet
(10%), SSNet (25%) AGMAE and LSTM achieve NMSE of
around−29.3dB,−26.1dB and−16.6dB, respectively.
SSNet (10%) and SSNet(25%) outperform AGMAE by around
76% and 56%, respectively. This echos with the observation
that the performance gap between AGAME and SSNet (either
SSNet (10%) and SSNet (25%)) becomes more significant at
0 dB scenarios than 20 dB scenarios.
Fig. 7 illustrates the channel extrapolation results for8×16
cm FAS. However, the NMSE in8×16cm FAS is larger
than that in2×4for any given model, SNR and percentage
of observed ports. Taking 10% observed ports with SNR of
0 dB case in Fig. 7(a) as an example, the NMSE of SSNet
(10%), SSNet (25%), AGAME and LSTM are−7.3dB,−6.6
dB,−1.7dB and0.6dB for8×16cm FAS, while the
corresponding NMSE for2×4cm FAS are−10.2dB,−9.1
dB,−4.7dB and−0.4dB, respectively. This indicates that
channel extrapolation in8×16cm is more challenging than
that in2×4cm, which is attributed that the correlation between
adjacent antenna is more significant in FAS of a smaller size.
As illustrated in Fig. 8, intuitively, the channel extrapolation
performance of SSNet (10%) and SSNet (25%) degrade with
the increase of noise level. Notably, as illustrated in Fig. 8(a)
abd 8(b), the performance gap between SSNet (10%) and
SSNet (25%) with various percentages of observed ports for
2×4cm FAS is larger than that for8×16cm FAS. This
indicates that SSNet (10%) is more effective in learning the
correlation between antennas than SSNet (10%) for2×4cm
FAS.
Last but not least, both SSNet (25%) and SSNet (10%)
significantly outperform AGMAE using much less training
sample. Specifically, we use 20,000 CSI samples to train

8
(a) The Original CSI.
 (b) Output of SSNet (10%).
 (c) Output of SSNet (25%).
 (d) Output of AGMAE [29].
Fig. 4. Illustration of the real part of the channel extrapolation for2×4cm with10% observed ports at 0 dB. As the Clarke channel is modeled as complex
Gaussian and symmetric, the simulation results of the imaginary part convey essentially the same information as the real part, and are omitted for conciseness.
(a) The Original CSI.
 (b) Output of SSNet (10%).
 (c) Output of SSNet (25%).
 (d) Output of AGMAE [29].
Fig. 5. Illustration of the real part of the channel extrapolation for2×4cm with10% observed ports at 20 dB. As the Clarke channel is modeled as
complex Gaussian and symmetric, the simulation results of the imaginary part convey essentially the same information as the real part, and are omitted for
conciseness.
SSNet (25%) and SSNet (10%), and 800,000 CSI samples to
train AGAME. This indicates the SSNet outperforms AGAME
with only 2.5% of training samples, demonstrating that SSNet
is significantly more data-efficient than AGAME.
2) Effect of mask ratio in training SSNet:The impact of
mask ratios for training SSNet is also revealed. We first com-
pare SSNet (25%) and SSNet (10%) qualitatively. Generally,
SSNet (10%) outperforms SSNet (25%) in terms of real and
imaginary part of the channel extrapolation for 2 × 4 cm
FAS with SNR of 0 and 20 dB with 10% observed ports.
Specifically, comparing Fig. 5(b) and 5(c), we observe that
SSNet (10%) outperforms SSNet (25%) in 20 dB scenarios.
The same trend is revealed in 0 dB scenarios, as illustrated in
Fig. 4(b) and 4(c).
A concern for the performance superiority of SSNet (10%)
over SSNet (25%) may attribute to that the percentage of
observed ports for training and testing of SSNet (10%) are
the same in Fig. 4 and 5. We evaluate the effect of mask ratio
in modeling training comprehensively, we train the proposed
SSNet with a mask ratio of 50%, i.e., SSNet (50%). We tested
SSNet (10%), SSNet (25%) and SSNet (50%) in scenarios
with various percentages of observed ports up to 50%, which
is illustrated in Fig. 9.
SSNet (10%) outperforms SSNet (25%) and SSNet (50%)
with various percentages of observed ports, including 5%,
10%, 15%, 20%, 25% and 50%. Taking the 0 dB scenario
in Fig. 9(a), SSNet (10%) outperforms SSNet (25%) and
SSNet (50%) with 5% of observed ports by 1.2 and 3.8 dB,
respectively. By further increasing the percentage of observed
ports to 50%, the performance superiority of SSNet (10%)
over SSNet (25%) and SSNet (50%) decrease to 0.4 and 0.9
dB, showing that the channel extrapolation accuracy of SSNet
(10%), SSNet (25%) and SSNet (50%) are emerging towards
to the same level. Such trend is more obvious in 20 dB sceanrio

9
(a) 0 dB.
(b) 20 dB.
Fig. 6. Comparison of SSNet, LSTM and AGMAE [29] in for FAS with of
2×4cm.
in Fig. 9(b).
The above comparison of the proposed models trained with
different mask ratios demonstrates that by using a smaller per-
centage of observed ports during training, the capability of the
SSNet is enhanced in testing. This is attributed that by training
the model with CSI of a small number of ports, the model
is forced to learn the correlation between ports that is more
effective for channel extrapolation, thereby showing superior
NMSE. As illustrated in Fig. 3, although the training loss of
SSNet (10%), SSNet (25%) and SSNet (50%) converage to
the same level, approaching 0, they show different patterns
during training. After showing a sharp decrease, the training
loss SSNet (10%), SSNet (25%) and SSNet (50%) keep nearly
unchanged at the level of approximately 0.3 for 31, 18 and 13
epochs, respectively. This indicates that SSNet (10%) is more
(a) 0 dB.
(b) 20 dB.
Fig. 7. Comparison of SSNet, LSTM and AGMAE [29] in for FAS with of
8×16cm.
difficult to train than SSNet (25%) and SSNet (50%), which
echos with the above analysis that the superiority of SSNet
(10%) in channel extrapolation is achieved at the expense of
training difficulties illustrated.
3) Abliation experiments:To demonstrate the effectiveness
of the proposed MoE in channel extrapolation, we carried out
ablation experiments. We compare the compare the perfor-
mance between SSNet and SSNet w/o MoE comprehensively.
The MoE module in the endocer of SSNet is replaced by
an FFN, i.e., each encoder block of SSNet w/o MoE, is a
stack of an MSA module, an FFN interleaved with residual
connections and LayerNorm. Fig. 9 illustrates the NMSE of
channel extrapolation between SSNet and SSNet w/o MoE
in various cases. A remarkable performance gain of SSNet
over SSNet w/o MoE is observed. For example in Fig. 9(b),

10
(a) 5 % of ports are observable.
(b) 15 % of ports are observable.
Fig. 8. An illustration for the channel extrapolation accuracy of SSNet with
various SNR levels. (SSNet(x%), y×z) indicates the case that SSNet (x%)
is tested iny×zcm FAS withs% of observed ports.
SSNet (10%), SSNet (25%) and SSNet (50%) outperform
SSNet w/o MoE (10%), SSNet w/o MoE (25%) and SSNet
w/o MoE(50%) by 4.9 dB, 5.7 dB and 9.1 dB at 20 db
with 5% of port observable. The performance gain reduce
to 2.5, 3.6 and 6.8 dB, respectively at 20 db with 50% of
port observable. This indicates that MoE is more effective
to learn the channel correlation between ports with a smaller
percentage of observed ports.
4) Generalization evaluation:To rigorously evaluate the
generalization capability of SSNet under realistic propagation
conditions, we perform zero-shot learning of SSNet on the
fully correlated channel model [2]. This advanced model
captures directive scattering effects prevalent in urban envi-
ronments, providing a more challenging testbed compared to
(a) 0 dB.
(b) 20 dB.
Fig. 9. The effect of mask ratio for the proposed SSNet and the ablation
experiments to demonstrate the effectiveness of MoE in channel extrapolation.
Compared with the proposed SSNet, each encoder block of SSNet w/o MoE, is
a stack of an MSA module and an FFN interleaved with residual connections
and LayerNorm.
the isotropic Clarke’s model used during training. The fully
correlated model shares a similar structure as Clarke’s model,
including the eigenvalue decomposition framework in Eq. (3)
and the channel generation framework in Eq. (4).
The core distinction between the Clarke’s model and fully
correlated model is the spatial correlation computation. The
Clarke’s model assumes isotropic scattering with uniform
AoA distribution in Eq. (2), while the fully correlated model
employs the zero-order Bessel function of the first kind [56]
to model the channel spatial correlation:
Σfull(i, j) =J0 (2π· ∥pi −p j∥/λ)(31)
This Bessel-function formulationJ 0(·)fundamentally alters
the spatial correlation characteristics. The Bessel function
J0(·)introduces two critical physical phenomena not captured

11
by Clarke’s model: spatial correlation decays slower with
antenna separation distance, maintaining significant correlation
at larger spacings due to the oscillatory nature ofJ 0(z)∼p
2/(πz) cos(z−π/4)for largez[57]; and directional cor-
relation patterns emerge where spatial correlation varies with
orientation relative to dominant scattering paths, as the Bessel
solution satisfies the Helmholtz wave equation∇ 2Σ+k 2Σ = 0
withk= 2π/λ[58], inherently encoding directional wave
propagation effects absent in Clarke’s isotropic model.
A total number of 4,000 channel samples are generated
using the above fully correlated channel model. Additive
Gaussian noise is added to these samples under predefined
SNR for testing, which are illustrated in Fig. 10.The in-
distribution case indicates that the proposed SSNet is trained
and tested using the channel samples generated using the
CLarke’s model, while the out-of-distribution case indicates
that the proposed SSNet is trained and tested using the channel
samples generated using the CLarke’s model [52], [53] and
fully correlated channel model [2], respectively.
We carried out zero-shot learning of the proposed SSNet
in the dataset generated using the fully correlated channel
model, i.e., the pre-trained SSNet is directly tested using
the dataset without changing the weights of the proposed
model, such as fine turning. The simulation results are il-
lustrated in Fig. 10, where the in-distribution case indicates
that the proposed SSNet is trained and tested using the
channel samples generated using the CLarke’s model, while
the out-of-distribution case indicates that the proposed SSNet
is trained and tested using the channel samples generated using
the CLarke’s model [52], [53] and fully correlated channel
model [2], respectively. Iteratively, there are performance gaps
between the in-distribution cases and their out-of-distribution
counterparts. For various level of SNRs and percentages of
observed ports, the performance loss in out-of-distribution
cases are within the range between 3 dB and 5 dB. Such
moderate performance loss is manageable, which validates the
generalization capability of the proposed model.
5) Inference speed:To evaluate the execution speed of the
various models, we carried out the inference speed tests in
various percentages of observed ratio using three types of
GPU, i.e., NVIDIA RTX 4090, 4060 and 3060. The simulation
results are demonstrated in Table. IV. The inference speed of
the proposed SSNet, SSNet w/o MoE, AGMAE and LSTM
increase are the lowest using NVIDIA RTX 4090, and are
the highest using NVIDIA RTX 3060, which is attributed to
that computational capability of NVIDIA RTX 4090 is the
highest among the three GPUs. It is observed that a higher
percentage (25 %) of observed ports requires longer execution
time (than 5 % of observed ports), which is reasonable because
a larger volume of data are being processed. Among all the
models, AGMAE is most fast to execute, then comes the
LSTM, SSNet w/o MoE and SSNet. SSNet outperforms the
AGMAE significantly at the expense of approximately 1.13
ms, 2.9 ms and 3.12 ms longer execution time in NVIDIA RTX
4090, 4060 and 3060, respectively. SSNet w/o outperforms
the AGMAE moderately at the expense of approximately 0.45
ms, 2.30 ms and 2.22 ms longer execution time in NVIDIA
RTX 4090, 4060 and 3060, respectively, which strikes a good
Fig. 10. An illustration of the generalization performance. The in-distribution
case indicates that the proposed SSNet is trained and tested using the channel
samples generated using the CLarke’s model, while the out-of-distribution
case indicates that the proposed SSNet is trained and tested using the channel
samples generated using the CLarke’s model [52], [53] and fully correlated
channel model [2], respectively.
balance between the performance and inference time.
V. CONCLUSIONS
This paper propose SSNet, a novel self-supervised learn-
ing framework for channel extrapolation in FAS. To further
improve the feature extraction capability and the noise ro-
bustness of the self-supervised learning, we propose to train
the SSNet using a joint loss function of contrastive loss
and channel extrapolation normalized mean squared error.
Our findings demonstrate that SSNet significantly outperforms
existing methods in terms of accuracy, robustness to noise,
and flexibility in handling variable numbers of CSI inputs.
Specifically, SSNet outperforms benchmark model with only
5% data, demonstrating its efficiency in data utilization. The
improved robustness, evident in its performance across diverse
SNR conditions and FAS sizes, highlights the benefits of the
self-supervised learning approach and the joint loss function in
mitigating the challenges posed by noise and high-dimensional
data.
However, several key areas require further investigation.
While SSNet demonstrates impressive performance in offline
settings, the development of a real-time channel extrapolation
system is crucial for practical FAS deployment. Future re-
search should focus on optimizing SSNet’s architecture and
inference speed to enable real-time CSI estimation. More-
over, the optimal training strategy of SSNet requires fur-
ther research, for example, what is the optimal percentage
of observed ports for training, does a mix of percentage
of observed ports for training improve the performance of
SSNet. Additional, exploring the integration of SSNet with
advanced signal processing techniques, such as beamforming
and precoding, will be essential to fully realize the potential
of FAS. Finally, extending SSNet to handle more complex

12
TABLE IV
The comparison of various models in terms of inference time (ms) per sample in different hardware platforms and different percentages of observed ports.
NVIDIA GeForce RTX 4090 NVIDIA GeForce RTX 4060 NVIDIA GeForce RTX 3060
5% 25% 5% 25% 5% 25%
LSTM 3.02 3.01 10.09 10.67 12.11 12.35
AGMAE 2.75 2.82 9.52 9.67 11.32 11.45
SSNet w/o MoE (90%) 3.23 3.29 11.80 11.91 13.55 13.96
SSNet w/o MoE (75%) 3.31 3.35 11.41 11.72 12.96 13.12
SSNet (90%) 3.90 3.98 12.07 12.44 14.55 14.66
SSNet (75%) 3.88 4.06 12.40 12.53 14.49 14.78
scenarios, such as those involving ISAC, presents an exciting
direction for future research. The combination of SSNet’s
efficient channel extrapolation with advanced signal processing
techniques holds great promise for unlocking the full potential
of FAS in future 6G networks.
REFERENCES
[1] K.-K. Wong, K.-F. Tong, Y . Shen, Y . Chen, and Y . Zhang, “Bruce lee-
inspired fluid antenna system: Six research topics and the potentials for
6G,”Frontiers in Communications and Networks, vol. 3, p. 853416,
2022.
[2] W. K. New, K.-K. Wong, H. Xu, C. Wang, F. R. Ghadi, J. Zhang,
J. Rao, R. Murch, P. Ram ´ırez-Espinosa, D. Morales-Jimenezet al.,
“A tutorial on fluid antenna system for 6g networks: Encompassing
communication theory, optimization methods and hardware designs,”
IEEE Communications Surveys & Tutorials, 2024.
[3] E. Faddoul, G. M. Kraidy, C. Psomas, and I. Krikidis, “Advanced
channel coding designs for index-modulated fluid antenna systems,”
arXiv preprint arXiv:2403.06839, 2024.
[4] J. Zou, H. Xu, C. Wang, L. Xu, S. Sun, K. Meng, C. Masouros, and
K.-K. Wong, “Shifting the ISAC trade-off with fluid antenna systems,”
arXiv preprint arXiv:2405.05715, 2024.
[5] K.-K. Wong, C. Wang, H. Zhang, G. Li, C.-C. Wang, C.-B. Chae, and
R. Murch, “Virtual FAS by learning-based imaginary antennas,”IEEE
Wireless Communications Letters, 2024.
[6] H. Xu, K.-K. Wong, W. K. New, K.-F. Tong, Y . Zhang, and C.-B. Chae,
“Revisiting outage probability analysis for two-user fluid antenna mul-
tiple access system,”IEEE Transactions on Wireless Communications,
2024.
[7] W. K. New, K.-K. Wong, H. Xu, K.-F. Tong, and C.-B. Chae, “Fluid
antenna system: New insights on outage probability and diversity gain,”
IEEE Transactions on Wireless Communications, vol. 23, no. 1, pp. 128–
140, 2023.
[8] C. Psomas, G. M. Kraidy, K.-K. Wong, and I. Krikidis, “On the
diversity and coded modulation design of fluid antenna systems,”IEEE
Transactions on Wireless Communications, 2023.
[9] H. Xu, G. Zhou, K.-K. Wong, W. K. New, C. Wang, C.-B. Chae,
R. Murch, S. Jin, and Y . Zhang, “Channel estimation for FAS-assisted
multiuser mmWave systems,”IEEE Communications Letters, 2023.
[10] W. K. New, K.-K. Wong, H. Xu, F. R. Ghadi, R. Murch, and C.-B.
Chae, “Channel estimation and reconstruction in fluid antenna system:
Oversampling is essential,”arXiv preprint arXiv:2405.15607, 2024.
[11] C. Skouroumounis and I. Krikidis, “Fluid antenna with linear MMSE
channel estimation for large-scale cellular networks,”IEEE Transactions
on Communications, vol. 71, no. 2, pp. 1112–1125, 2022.
[12] Z. Zhang, J. Zhu, L. Dai, and R. W. Heath, “Successive Bayesian
reconstructor for channel estimation in fluid antenna systems,”IEEE
Transactions on Wireless Communications, 2024.
[13] Y . Jin, Y . Wu, Y . Gao, S. Zhang, S. Xu, and C.-X. Wang, “Linformer: A
linear-based lightweight transformer architecture for time-aware MIMO
channel prediction,”IEEE Transactions on Wireless Communications,
2025.
[14] S. Zhang, Y . Liu, F. Gao, C. Xing, J. An, and O. A. Dobre, “Deep
learning based channel extrapolation for large-scale antenna systems:
Opportunities, challenges and solutions,”IEEE Wireless Communica-
tions, vol. 28, no. 6, pp. 160–167, 2021.
[15] Z. Zhang, J. Zhang, Y . Zhang, L. Yu, and G. Liu, “AI-based time-,
frequency-, and space-domain channel extrapolation for 6G: Opportu-
nities and challenges,”IEEE Vehicular Technology Magazine, vol. 18,
no. 1, pp. 29–39, 2023.
[16] Y . Qiu, D. Wu, and Y . Zeng, “Can channels be fully inferred between
two antenna panels?”IEEE Communications Letters, vol. 28, no. 4, pp.
942–946, 2024.
[17] W. Liu, Z. Chen, and X. Gao, “Massive MIMO channel prediction in real
propagation environments using tensor decomposition and autoregres-
sive models,” in2022 IEEE 33rd Annual International Symposium on
Personal, Indoor and Mobile Radio Communications (PIMRC). IEEE,
2022, pp. 849–855.
[18] F. Rottenberg, R. Wang, J. Zhang, and A. F. Molisch, “Channel ex-
trapolation in FDD massive MIMO: Theoretical analysis and numerical
validation,” in2019 IEEE Global Communications Conference (GLOBE-
COM). IEEE, 2019, pp. 1–7.
[19] Y . Han, T.-H. Hsu, C.-K. Wen, K.-K. Wong, and S. Jin, “Efficient
downlink channel reconstruction for FDD multi-antenna systems,”IEEE
Transactions on Wireless Communications, vol. 18, no. 6, pp. 3161–
3176, 2019.
[20] W. Jin, J. Zhang, C.-K. Wen, and S. Jin, “Model-driven deep learning
for hybrid precoding in millimeter wave MU-MIMO system,”IEEE
Transactions on Communications, 2023.
[21] S. Zhang, S. Zhang, J. Ma, T. Liu, and O. A. Dobre, “Deep learning
based antenna-time domain channel extrapolation for hybrid mmwave
massive MIMO,”IEEE Transactions on Vehicular Technology, vol. 71,
no. 12, pp. 13 398–13 402, 2022.
[22] X. Xu, S. Zhang, F. Gao, and J. Wang, “Sparse bayesian learning
based channel extrapolation for RIS assisted MIMO-OFDM,”IEEE
Transactions on Communications, vol. 70, no. 8, pp. 5498–5513, 2022.
[23] Y . Gao, X. Xu, Y . Jin, W. Yuan, J. Zhang, and S. Xu, “Joint channel
estimation and data detection for OTFS systems: A lightweight deep
learning framework with a novel data augmentation method,”IEEE
Internet of Things Journal, 2025.
[24] W. Yu, J. Jiang, Y . Gao, and S. Xu, “Multi-scenario time-domain
channel extraploation: A Transformer-based approach,” in2024 IEEE
24th International Conference on Communication Technology (ICCT).
IEEE, 2024, pp. 1446–1450.
[25] J. Jiang, Y . Gao, X. Wu, and S. Xu, “Towards channel foundation models
(CFMs): Motivations, methodologies and opportunities,”arXiv preprint
arXiv:2507.13637, 2025.
[26] Y . Gao, Z. Lu, Y . Wu, Y . Jin, S. Zhang, X. Chu, S. Xu, and C.-
X. Wang, “Enabling 6G through multi-domain channel extrapolation:
Opportunities and challenges of generative artificial intelligence,”arXiv
preprint arXiv:2509.01125, 2025.
[27] B. Lin, F. Gao, S. Zhang, T. Zhou, and A. Alkhateeb, “Deep learning-
based antenna selection and CSI extrapolation in massive MIMO sys-
tems,”IEEE Transactions on Wireless Communications, vol. 20, no. 11,
pp. 7669–7681, 2021.
[28] N. Waqar, K.-K. Wong, K.-F. Tong, A. Sharples, and Y . Zhang, “Deep
learning enabled slow fluid antenna multiple access,”IEEE Communi-
cations Letters, vol. 27, no. 3, pp. 861–865, 2023.
[29] H. Zhang, J. Wang, C. Wang, C.-C. Wang, K.-K. Wong, B. Wang, and
C.-B. Chae, “Learning-induced channel extrapolation for fluid antenna
systems using asymmetric graph masked autoencoder,”IEEE Wireless
Communications Letters, 2024.
[30] X. Wu, H. Zhang, C.-C. Wang, and Z. Li, “Channel state information ex-
trapolation in fluid antenna systems based on masked language model,”
in2024 IEEE International Conference on Communications Workshops
(ICC Workshops). IEEE, 2024, pp. 1383–1388.
[31] C. Wang, G. Li, H. Zhang, K.-K. Wong, Z. Li, D. W. K. Ng, and
C.-B. Chae, “Fluid antenna system liberating multiuser MIMO for
ISAC via deep reinforcement learning,”IEEE Transactions on Wireless
Communications, 2024.
[32] Y . Jin, P. Qi, Y . Gao, and S. Liu, “Dual-path residual attention network

13
for efficient channel estimation in RIS-assisted communication systems,”
Physical Communication, vol. 68, p. 102577, 2025.
[33] Y . Gao, H. Hu, J. Zhang, Y . Jin, S. Xu, and X. Chu, “On the performance
of an integrated communication and localization system: An analytical
framework,”IEEE Transactions on Vehicular Technology, vol. 73, no. 7,
pp. 10 845–10 849, 2024.
[34] J. Jiang, S. Xu, W. Yu, and Y . Gao, “C2S-AE: CSI to sensing enabled
by an auto-encoder-based framework,”arXiv preprint arXiv:2503.00941,
2025.
[35] Y . Gao, X. Wu, Y . Gao, and S. Xu, “C2S: An Transformer-based
framework to extrapolate sensing channel from communication channel,”
in2024 IEEE 100th Vehicular Technology Conference (VTC2024-Fall).
IEEE, 2024, pp. 1–5.
[36] G. Li, H. Zhang, C. Wang, and B. Wang, “Model-driven channel
extrapolation for massive fluid antenna,” in2024 IEEE International
Conference on Communications Workshops (ICC Workshops). IEEE,
2024, pp. 1146–1151.
[37] Y . Jin, J. Zhou, and Y . Gao, “HSGAN-IoT: A hierarchical semi-
supervised generative adversarial networks for iot device classification,”
Computer Networks, vol. 243, p. 110299, 2024.
[38] Y . Jin, J. Fang, and Y . Gao, “SSCMT-ETC: A semi-supervised con-
trastive mean teacher model for encrypted traffic classification,” in2023
2nd International Conference on Sensing, Measurement, Communication
and Internet of Things Technologies (SMC-IoT). IEEE, 2023, pp. 127–
133.
[39] Y . Jin, X. Yu, and Y . Gao, “Multiclass malicious URL attack type
detection via capsule-based neural network,” inThird International Sem-
inar on Artificial Intelligence, Networking, and Information Technology
(AINIT 2022), vol. 12587. SPIE, 2023, pp. 520–525.
[40] N. Van Huynh, J. Wang, H. Du, D. T. Hoang, D. Niyato, D. N.
Nguyen, D. I. Kim, and K. B. Letaief, “Generative AI for physical
layer communications: A survey,”IEEE Transactions on Cognitive
Communications and Networking, vol. 10, no. 3, pp. 706–728, 2024.
[41] S. Xu, J. Jiang, W. Yu, Y . Gao, G. Pan, S. Mu, Z. Ai, Y . Gao,
P. Jiang, and C.-X. Wang, “Enhanced fingerprint-based positioning with
practical imperfections: Deep learning-based approaches,”arXiv preprint
arXiv:2509.01197, 2025.
[42] Z. Zhang, T. Ji, H. Shi, C. Li, Y . Huang, and L. Yang, “A self-supervised
learning-based channel estimation for IRS-aided communication without
ground truth,”IEEE Transactions on Wireless Communications, vol. 22,
no. 8, pp. 5446–5460, 2023.
[43] J. Gui, T. Chen, J. Zhang, Q. Cao, Z. Sun, H. Luo, and D. Tao, “A survey
on self-supervised learning: Algorithms, applications, and future trends,”
IEEE Transactions on Pattern Analysis and Machine Intelligence, 2024.
[44] Y . Wang, G. Yu, Y . Zhang, D. Liu, and Y . Zhang, “CSI-based location-
independent human activity recognition by contrast between dual stream
fusion features,”IEEE Sensors Journal, 2024.
[45] P. Ferrand, M. Guillaud, C. Studer, and O. Tirkkonen, “Wireless channel
charting: Theory, practice, and applications,”IEEE Communications
Magazine, vol. 61, no. 6, pp. 124–130, 2023.
[46] P. Stephan, F. Euchner, and S. t. Brink, “Channel charting-based channel
prediction on real-world distributed massive MIMO CSI,”arXiv preprint
arXiv:2410.11486, 2024.
[47] M. Dai, E. Zheng, Z. Feng, L. Qi, J. Zhuang, and W. Yang, “Vision-
based UA V self-positioning in low-altitude urban environments,”IEEE
Transactions on Image Processing, 2023.
[48] M. Oquab, T. Darcet, T. Moutakanni, H. V o, M. Szafraniec, V . Khalidov,
P. Fernandez, D. Haziza, F. Massa, A. El-Noubyet al., “Dinov2:
Learning robust visual features without supervision,”arXiv preprint
arXiv:2304.07193, 2023.
[49] K. He, X. Chen, S. Xie, Y . Li, P. Doll ´ar, and R. Girshick, “Masked au-
toencoders are scalable vision learners,” inProceedings of the IEEE/CVF
conference on computer vision and pattern recognition, 2022, pp.
16 000–16 009.
[50] A. Vaswani, N. Shazeer, N. Parmar, J. Uszkoreit, L. Jones, A. N. Gomez,
Ł. Kaiser, and I. Polosukhin, “Attention is all you need,”Advances in
neural information processing systems, vol. 30, 2017.
[51] V . Rani, S. T. Nabi, M. Kumar, A. Mittal, and K. Kumar, “Self-
supervised learning: A succinct review,”Archives of Computational
Methods in Engineering, vol. 30, no. 4, pp. 2761–2775, 2023.
[52] E. Bj ¨ornson and L. Sanguinetti, “Rayleigh fading modeling and channel
hardening for reconfigurable intelligent surfaces,”IEEE Wireless Com-
munications Letters, vol. 10, no. 4, pp. 830–834, 2020.
[53] P. Ram ´ırez-Espinosa, D. Morales-Jimenez, and K.-K. Wong, “A new
spatial block-correlation model for fluid antenna systems,”IEEE Trans-
actions on Wireless Communications, 2024.
[54] M. Lee, “Mathematical analysis and performance evaluation of the GeLu
activation function in deep learning,”Journal of Mathematics, vol. 2023,
no. 1, p. 4229924, 2023.
[55] A. Pinkus, “Approximation theory of the MLP model in neural net-
works,”Acta numerica, vol. 8, pp. 143–195, 1999.
[56] ´A. Baricz,Generalized Bessel functions of the first kind. Springer,
2010.
[57] F. Bowman,Introduction to Bessel functions. Courier Corporation,
2012.
[58] F. W. J. Olver, L. C. Maximon, D. Lozier, R. Boisvert, and C. Clark,
“Bessel functions,”NIST handbook of mathematical functions, no.
2655350, pp. 215–286, 2009.