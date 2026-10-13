---
title: "WDMoE Wireless Distributed Mixture of Experts for Large Language Models"
zotero_key: "J4JEDLUD"
pdf_key: "V3A5BBRB"
collection: "其他"
source: "Open-access PDF (arXiv, pypdf extraction)"
page_mapping: unverified
---

# WDMoE Wireless Distributed Mixture of Experts for Large Language Models — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
WDMoE: Wireless Distributed Mixture of Experts
for Large Language Models
Nan Xue, Yaping Sun, Zhiyong Chen, Meixia Tao, Fellow, IEEE, Xiaodong Xu, Liang Qian,
Shuguang Cui, Fellow, IEEE, Wenjun Zhang, Fellow, IEEE, and Ping Zhang, Fellow, IEEE
Abstract—Large Language Models (LLMs) have achieved
significant success in various natural language processing tasks,
but the role of wireless networks in supporting LLMs has not
been thoroughly explored. In this paper, we propose a wireless
distributed Mixture of Experts (WDMoE) architecture to enable
collaborative deployment of LLMs across edge servers at the
base station (BS) and mobile devices in wireless networks.
Specifically, we decompose the MoE layer in LLMs by placing the
gating network and the preceding neural network layer at BS,
while distributing the expert networks among the devices. This
deployment leverages the parallel inference capabilities of expert
networks on mobile devices, effectively utilizing the limited com-
puting and caching resources of these devices. Accordingly, we
develop a performance metric for WDMoE-based LLMs, which
accounts for both model capability and latency. To minimize the
latency while maintaining accuracy, we jointly optimize expert
selection and bandwidth allocation based on the performance
metric. Moreover, we build a hardware testbed using NVIDIA
Jetson kits to validate the effectiveness of WDMoE. Both theoret-
ical simulations and practical hardware experiments demonstrate
that the proposed method can significantly reduce the latency
without compromising LLM performance.
Index Terms—Distributed Large Language Models, Mixture of
Experts, Expert Selection, Wireless Communications, Resource
Allocation
I. I NTRODUCTION
The exciting advancements in large language models
(LLMs) have sparked a new wave of AI innovation. LLMs,
exemplified by ChatGPT [2], have demonstrated emergent
abilities [3], including better generalization, nuanced meaning
comprehension, and remarkable reasoning and generation ca-
pabilities. These advancements have led to widespread applica-
tions across various fields, illuminating the vision of artificial
general intelligence (AGI) [4]. In the field of 6G wireless
N. Xue, Z. Chen, M. Tao, L. Qian and W. Zhang are with the Coopera-
tive Medianet Innovation Center, Shanghai Jiao Tong University, Shanghai
200240, China. (email: {nan.xue, zhiyongchen, mxtao, lqian, zhangwen-
jun}@sjtu.edu.cn)
Y . Sun is with the Department of Broadband Communication, Pengcheng
Laboratory, Shenzhen 518000, China. Y . Sun is also with the Future Net-
work of Intelligent Institute (FNii), the Chinese University of Hong Kong
(Shenzhen), Shenzhen 518172, China (email: sunyp@pcl.ac.cn).
X. Xu and P. Zhang are with the Beijing University of Posts and Telecom-
munications, Beijing 100876, China, and affiliated with the Department of
Broadband Communication, Peng Cheng Laboratory, Shenzhen 518000, China
(email: xuxd@pcl.ac.cn; pzhang@bupt.edu.cn).
S. Cui is with the School of Science and Engineering (SSE) and the
Future Network of Intelligent Institute (FNii), the Chinese University of Hong
Kong (Shenzhen), Shenzhen 518172, China. S. Cui is also affiliated with the
Department of Broadband Communication, Peng Cheng Laboratory, Shenzhen
518000, China (email: shuguangcui@cuhk.edu.cn).
Part of this manuscript will be presented at IEEE GLOBECOM 2024 [1].
networks, LLMs have been used for wireless network resource
allocation [5]–[7], and applied in internet of vehicles [8] and
immersive communications [9].
The emergent abilities of LLMs stem from extensive com-
putation, a large number of model parameters, and massive
training datasets [3], [10], [11]. The vast number of model
parameters poses significant challenges for training, infer-
ence, and deployment. The training phase of LLMs involves
significant costs in time and computational power for most
individuals and organizations. Regarding LLMs inference and
deployment, they also require fast responses and ample mem-
ory. In this paper, we mainly focus on LLMs inference and
deployment.
Currently, LLMs can be classified into cloud-based LLMs
and on-device LLMs based on their deployment characteris-
tics. Cloud servers with numerous graphics processing units
(GPUs) and sufficient power supply are responsible for the
majority of model inference and deployment. Due to con-
cerns over latency and data privacy, the potential of on-
device LLMs is gaining increasing attention [12]. Researchers
compress LLMs through pruning [13], quantization [14], and
distillation [15] to meet the memory, computation, and energy
requirements of mobile devices. Limited by generation speed
and model capabilities, even a company as strong as Apple
has not been able to deploy a fully satisfactory LLM on
mobile devices. On the latest iPhone 16 Pro series, only simple
tasks are completed locally by a model with around 3 billion
parameters, whereas complex tasks are still handled by cloud-
based models like ChatGPT [16], [17]. Although in practical
LLMs application transformer’s KV cache [18] can speed up
the inference, it will cause considerable memory overhead,
which presents an obstacle for on-device LLMs.
In light of the rapid advancements of LLMs and the
widespread adoption of 5G/6G wireless networks, a natural
question arises: can wireless networks support LLMs? If so,
how? The answer lies in fully leveraging the multidimensional
resources of wireless networks, incorporating computing, com-
munications, and caching (3C) to support LLMs and enhance
user experience [19]. As a key technology of 5G, mobile
edge computing (MEC) has been thoroughly studied to im-
prove the quality of service for various network applications.
Recently, edge-cloud collaborative training and fine-tuning
are also researched [20], [21]. However, there is a lack of
specialized optimization research tailored to the characteristics
of LLMs in the scenario of distributed deployment in wireless
networks. To address this issue, this paper aims to bridge the
gap by proposing a distributed deployment of LLMs powered
arXiv:2411.06681v1  [cs.LG]  11 Nov 2024

2
by mixture of experts (MoE), modeling and optimizing the
latency during the inference phase, which can efficiently utilize
the 3C resources at both the MEC server and mobile devices.
The core idea of MoE architecture is to sparsify the neural
networks (NNs) based on the observation of sparse activa-
tion of NNs and allow each expert to specialize in their
specific tasks, reducing the floating point operations (FLOPs)
to achieve acceleration and increasing model capacity [22].
Transformer with MoE1 [23] replaces the original single dense
feedforward neural network (FFN) with a gating network and
multiple smaller expert networks, which often have the same
structure and different hidden layer dimensions. The expert
networks within the same MoE layer operate in parallel and
independently, providing high fault tolerance and making it
well-suited for wireless distributed deployment. Besides, we
find during the inference phase of MoE-based LLMs, decreas-
ing the number of participating experts will not degrade model
performance, showcasing the robustness of MoE. Capitalizing
on these attributes, we can deploy the gating network at MEC
server and each expert network in an MoE layer on diverse
mobile devices. Furthermore, due to the diversity of computing
capabilities among the mobile devices and communication
qualities between the base station (BS) and the mobile devices,
how to achieve a good balance between the inference accuracy
and latency also requires careful consideration.
A. Related Work
Current mainstream LLMs utilize Transformer architecture
[24]. LLMs based on the Transformer architecture can be
categorized into three types: encoder-decoder, decoder-only,
and encoder-only. For encoder-decoder structure, in the vanilla
Transformer [24], the multi-head attention mechanism fully
replaces traditional recurrent neural networks, making the
architecture more suitable for parallel computing. For decoder-
only structure, in [25], a decoder-only Transformer is utilized
with the optimization objective of standard language modeling.
This work achieves state of the art performance, and the
model is named GPT. For the encoder-only structure, [26]
designs Bidirectional Encoder Representations from Trans-
formers (BERT) and applies the training paradigm of pre-
training and fine-tuning to language model. BERT includes
a base model with 110 million parameters, similar to GPT
and a large model with 340 million parameters. The work
[25] and [26] lay the foundation for the model architecture,
training paradigm, and development direction of large lan-
guage models. GPT-2 is a scaled-up version of GPT with
1.5 billion parameters, focusing on zero-shot performance in
[27]. The work [10] proposes the scaling law of transformer-
based language models and suggests that larger models trained
on more data tend to perform better, supporting the later
development of large language models. GPT-3 is released in
[28] with 175 billion parameters and was the largest language
model at that time. It is applied without fine-tuning and
achieves state-of-the-art performance on various benchmarks.
Following the scaling law, an increasing number of large
1In this paper, MoE refers to Transformer with MoE unless otherwise
specified.
language models have appeared with more parameters, and
the largest open source model is Llama 3.1, with 405 billion
parameters, based on a dense Transformer [29].
Large model size makes the training and inference computa-
tionally expensive. Various methods of training and inference
have been proposed to improve model performance without ex-
cessive computational costs [22], among which the MoE archi-
tecture has been well-researched. The basic MoE layer consists
of a gating network and a number of experts, which are simple
feed-forward neural networks [30]. The work [22] introduces a
Sparsely-Gated MoE and expands the LSTM-based language
model to a configuration with 137 billion parameters. In the
Transformer era, [23] replaces all Feed-forward layers in the
model with MoE layers and achieves enhanced model capacity
while substantially reducing the training time. Mistral AI
successively releases two open-source MoE large language
models, Mixtral-8x7B and Mixtral-8x22B, both achieving the
state-of-the-art performance among open-source large models
at the time of their release [31]. The work [32] introduces an
adaptive MoE framework, AdaMV-MoE, designed for multi-
task vision recognition. Unlike conventional MoE approaches
with a fixed number of experts, AdaMV-MoE dynamically
adjusts the number of active experts per task based on training
dynamics, eliminating the need for manual tuning of model ca-
pacity. Based on the idea that harder tasks need more experts,
the work [33] develops a method for dynamically adjusting
the number and selection of experts to reduce computational
costs for simple tasks while enhancing model performance for
complex ones. Advance in MoE models have unlocked the
potential of model capability and computational efficiency.
On-device LLMs have been extensively researched as a
promising solution for personal assistants. By running LLMs
directly on devices such as smartphones or edge servers, they
offer enhanced privacy, lower latency, and reduced depen-
dence on cloud servers. The work [34] devises a KV cache
compression and swapping method with accuracy tolerance
awareness, significantly reducing the context switching latency
and extending the capacity of active contexts. In [35], a
highly efficient computation and memory framework named
Edge-LLM is proposed, reducing computation and memory
overhead through layer-wise unified compression and adaptive
backpropagation depth reduction. MobileLLM is a model
family with sub-billion parameters that surpasses previous
sub-billion models on mainstream benchmarks by adopting
deep and thin network architectures, embedding sharing, and a
grouped-query attention mechanism [36]. With privacy consid-
erations, [37] employs derivative-free optimization to update
the local LLM’s parameters during on-device fine-tuning phase
under the resource-constrained circumstances.
B. Contributions
Motivated by the above, we explore a wireless distributed
deployment architecture for LLMs with MoE, define and
model key performance metrics of LLMs within the frame-
work, and optimize resource allocation and expert selection
to improve the LLMs service capabilities within the wireless
network. The main contributions of this paper are summarized
as follows:

3
Self Attention
Add & Normalize
Gate
EN1 EN2 EN3 ······ENn
+
Add & Normalize
MoE Block
MoE Block
MoE Block
MoE Block …
Embedding & Encoding
Input
Post-processing
Output
Repeat
MoE Layer
(a)
Self Attention
Add & Normalize
Gate
MoE Blocks 
without EN
device 1
device 2
device 3
device n
···
+
Add & Normalize
Next 
block
Expert 
Networks
Wireless 
Channel
Downlink
Uplink
Rayleigh Fading
Base Station (BS)
EN1
EN2
EN3
ENn (b)
Fig. 1: (a) MoE-based LLMs architecture [23]; (b) The proposed WDMoE-based LLMs system model.
• We propose a novel wireless distributed MoE architec-
ture, WDMoE, for LLMs. The fundamental principle of
the WDMoE architecture is to leverage the independence
and parallelism of expert networks by deploying them on
multiple mobile devices, thereby utilizing the resource
advantages of wireless networks to facilitate distributed
deployment of large models. This architecture places
the computationally intensive and memory-demanding
multi-head attention mechanism on the MEC servers at
BS. Through collaborative token processing between BS
and mobile devices, the wireless network can support a
large number of LLMs service requests, addressing the
challenges of limited memory on a single device and data
privacy concerns in cloud-based LLMs deployment.
• We establish latency-aware performance metrics of
the WDMoE-based LLMs. By analyzing the attention
mechanism, we find that, during the wireless distributed
deployment of LLMs with MoE, the latency for expert
networks on different mobile devices to process tokens
and return them to the BS varies. This discrepancy can
cause earlier-arriving tokens to wait at the attention mod-
ule. We model this latency, referred to as attention waiting
latency, and design a bilevel optimization problem where
the upper-level objective is to minimize this latency while
ensuring model capabilities at the lower level, thereby
reducing latency without compromising model perfor-
mance. In addition, we propose an innovative metric, the
weight latency ratio (WLR), to comprehensively consider
the output weights of the MoE gating network and the
attention waiting latency of each device.
• We develop an expert selection policy to improve the
performance. Based on the defined WLR, the expert
selection policy can process tokens by considering the
processing time and weight of each mobile device for
allocated tokens. It dynamically adjusts the number of
experts per token, thereby reducing network transmission
and computational load.
• We build a hardware testbed using NVIDIA Jetson
kits to validate the effectiveness of the proposed
WDMoE. We use three NVIDIA Jetson kits and one
personal computer (PC) with an NVIDIA RTX 4070 Ti,
serving as four mobile devices, each running one expert
for each layer, and communicating with the server via
WiFi. Both simulation results and hardware experiment
results show that the proposed WDMoE architecture and
expert selection policy effectively reduce the latency
experienced by users. For example, compared to vanilla
expert selection, the proposed WDMoE reduces latency
by 45.75% on average on the PIQA dataset without model
capability deterioration.
The rest of this paper is organized as follows. The WDMoE-
based LLM architecture is introduced in Section II. The system
model and problem formulation are presented in Section III.
The WDMoE expert selection policy and bandwidth allocation
algorithm are introduced in Sections IV . Section V shows
extensive simulation results. Finally, the hardware testbed
experiments are presented in Section VI, and conclusions are
drawn in Section VII.
II. T HE PROPOSED WDM OE BASED LLM
A. Structure of MoE-based LLMs
The network structure of MoE-based LLMs is depicted in
Fig. 1(a), where each MoE block is based on a Transformer.
In these blocks, the FFN module is replaced by an MoE layer
[31]. An MoE layer consists of a gating network, also known
as a router, and multiple expert networks, each of which can
be any type of neural network. The gating network, which is
a simple neural network, processes the input token to produce
a weight vector for each expert.

4
The number of expert networks is denoted as n. Let xi ∈
RJ×m be the input token set of the gating network in the i-th
MoE block, where J is the total number of input tokens of
all prompts at present, and m is the dimension of a token’s
embedding. I denotes the total number of MoE blocks in the
LLMs. The element xij ∈ xi denotes the j-th input token of
the i-th MoE block. This token xij serves as the input to the
gating network, which then outputs weights wij for the j-th
token in the i-th block. Here, wij ∈ Rn is an n-dimension
column vector representing weights allocated to n experts. xij
is also fed into the expert networks, whose output yij is an
n-dimension column vector. The output oij of the j-th token
through the i-th MoE layer is:
oij = wij ⊤yij. (1)
B. Distributed Deployment of WDMoE
Experts operate in parallel and do not impact each other,
making this approach suitable for deployment in distributed
mobile edge networks. We consider a BS equipped with an
edge server that possess powerful computing capability, to
process multiple data streams simultaneously for n mobile
devices, as shown in Fig. 1(b). In the WDMoE architecture,
the attention mechanism and gating network are deployed at
the BS, while only expert networks are assigned to mobile
devices. Typically, the expert network consists of a simple
multilayer perceptron (MLP). When a user sends a prompt,
its embedding operation can be completed either locally or at
BS, depending on the choice of the user. In this paper, we
focus on the communications and computing costs incurred
during interactions between BS and mobile devices following
the first embedding module. The proposed WDMoE can be
integrated with existing splitting methods.
The mobile devices are connected to the BS via wireless
links. We denote the set of mobile devices as U ≜ {1, · · ·, U}.
Let Bk ∈ [0, B] denote the bandwidth allocated to the k-th
device. For the downlink transmission, the data transmission
rate from the BS to the k-th device is formulated as:
Rdk = Bk log2

1 + P dk gBS,k
N0Bk

, ∀k ∈ U, (2)
where P dk denotes the transmission power for device k, gBS,k
represents the channel gain from the BS to the k-th device, and
N0 is the noise power spectral density. The uplink transmission
rate from the k-th device to the BS is:
Ruk = Bk log2

1 + P uk gk,BS
N0Bk

, ∀k ∈ U, (3)
where P uk denotes the transmission power of the k-th device,
and gk,BS represents the channel gain from the k-th device to
the BS. For WDMoE, the token embeddings are transmitted
between the BS and the devices. The size of each token em-
bedding is denoted by m. The data size of a token embedding,
represented as Lcomm, can be calculated as follows:
Lcomm = ϵ × m, (4)
where ϵ is a coefficient determined by the quantization preci-
sion. For instance, a half-precision floating-point occupies 16
bits [38] and thus ϵ = 16.
x
W1
W2
Silu
W3 y∘
Multiplication
Multiplication
Activation
Element-wise
Multiplication
MultiplicationInput Output
Fig. 2: Expert network structure.
We consider each device is equipped with at least one
graphics processing unit (GPU). The expert network used in
this paper is an FFN, comprising neural network linear lay-
ers, activation functions, and element-wise multiplications, as
shown in Fig. 2. The primary floating-point operations include
matrix multiplications and element-wise multiplications, as
activation functions is expressed using these two fundamental
operations. The FLOPs required by our expert network is given
by [39]:
Lcomp = 4m × mh + 2mh × m + η × mh + mh, (5)
where mh is the hidden dimension of the FFN and η de-
notes the FLOPs required by the activation function in the
network. Considering the strong computational capability of
MEC servers, the computing latency at MEC server is negli-
gible compared to the communications time and computation
latency at mobile devices in this paper.
III. P ERFORMANCE METRICS AND PROBLEM
FORMULATION
A. Token Processing Latency
The output tensor retains the same shape as the input
tensor, indicating that the data transmission size for the uplink
is equivalent to that for the downlink. The communication
latency for the j-th token in the i-th block, processed by expert
k, is defined as:
tcommi,j,k = LcommRdk + LcommRuk . (6)
The computation latency for the j-th token in the i-th block
processed by the expert k is given by:
tcompi,j,k = LcompCk , (7)
where Ck denotes the computational capacity of expert k.
The total delay of the j-th token in the i-th block processed
by the expert k is given by:
ti,j,k = tcommi,j,k + tcompi,j,k . (8)
B. Attention Waiting Latency
Once each expert completes processing a token, the result
is transmitted back to the BS. The BS aggregates the results,
after which the tokens are forwarded to the next block. The
first operation in the subsequent block is the self-attention
mechanism. To more accurately model the latency experienced
by users, we account for the impact of token latency on

5
Hello, what are 
you doing
Hello
, 
what
are
you
doing
1.0
0.57 0.43
0.39 0.28 0.33
0.28 0.26 0.24 0.22
0.21 0.21 0.2 0.2 0.19
0.20 0.18 0.16 0.14 0.11 0.11
Hello
Hello
, 
who
are
you
doing
, who are you doing
Hello
, 
what
doing
you
are
timeline
-0.24
-0.36 -0.6
-0.24
-0.36 -0.6
-0.05 -0.1
-0.6
-0.24
-0.36 -0.6
-0.05 -0.1
-0.6
0.00
0.00
0.00
0.00
0.00
-0.24
-0.36 -0.6
-0.05 -0.1
-0.6
0.00
0.00
0.00
0.00
-0.17
-0.15
-0.05
-0.22
0.00
-0.24
-0.36 -0.6
-0.05 -0.1
-0.6
0.00
0.00
0.00
0.00
-0.17
-0.15
-0.05
-0.22
0.00 -0.28
-0.33
-0.07
0.00
-0.11
Attention Weight Matrix
Token Arrival Time Attention Weight Matrix Calculation Completion Degree versus Time (Attention Waiting Latency:                    ) 
Tokenization, Embedding and  Positional Encoding
Fig. 3: An example of waiting in the attention mechanism.
the following block’s modules. Although computation latency
at the BS is disregarded, the latency of preceding tokens
affects the overall practical latency. The attention mechanism
processes all tokens as a sequence to compute attention scores
and reconstructs the output tensor, which maintains the same
shape as the input token.
As illustrated in Fig. 3, the attention mechanism computes
the attention weight matrix, containing the attention scores
for each pair of input tokens. In the distributed deployment of
WDMoE, all tokens are transmitted to various mobile devices,
and their computation results arrive at the edge server at
different times due to factors such as channel uncertainty,
variations in mobile device workloads, and available resources.
In Fig. 3, the token doing is the last token in the sequence but
is among the first to be transmitted back to the server, along
with the fourth token, are, at time τ4,6. At this point, only the
attention scores for these two token pairs can be calculated.
The first two arriving tokens must wait for the remaining
tokens to arrive. At time τ2, the entire masked attention
weight matrix—formed by the multiplication of the query and
key—is completed and used for weighted calculation with the
corresponding values.
We denote the expert selection matrix for the i-th block as
Qi ∈ RJ×U . Each element of Qi, denoted by qij,k ∈ {0, 1},
represents the expert selected for the j-th token in the i-
th block. All the expert selections Qi, ∀i ∈ {1, · · ·, I} are
concatenated to get Q. Specifically, qij,k = 1 indicates that the
k-th expert is selected for the j-th token in the i-th block. The
total delay of the sequence is determined by the device with
the slowest processing and transmission time, necessitating
load balancing. The total number of tokens in the i-th block
assigned to the k-th device is given by:
qik =
JX
j=1
qij,k. (9)
Since all tokens have the same data size and computation
load, we have ti,k = ti,j,k for all j, and the total time required
for device k to process all allocated tokens is given by:
tik = qikti,k. (10)
Finally, the actual latency from the gating network of the
i-th block to the attention mechanism of the (i + 1)-th block
is:
ti = max
k∈U
tik. (11)
C. Weight-to-Latency Ratio
The attention waiting latency provides a more compre-
hensive and precise reflection of the latency experienced by
users. For any device involved in the network, it is crucial
to prioritize the overall benefits derived from processing the
assigned tokens. Thus, we introduce a weight-to-latency ratio
from the perspective of the processing device to quantify its
processing efficiency. The WLR for device k in the i-th block
is defined as
W LRik =
PJ
j=1 qij,kwij,k
tik . (12)
D. Problem Formulation
We formulate a bilevel optimization problem [40] to min-
imize the total system latency while ensuring comprehensive
system performance. For the bilevel optimization, the upper

6
Hello, 
who 
are you?
Embedding
Attention
Add & Norm
Necessary Preprocessing
Token 1
Token 2
Token 3
Token J
…
…
𝑤1,1 𝑤1,2 𝑤1,3 𝑤1,4 𝑤1,5 𝑤1,6 𝑤1,7 𝑤1,8
𝑤2,1 𝑤2,2 𝑤2,3 𝑤2,4 𝑤2,5 𝑤2,6 𝑤2,7 𝑤2,8
𝑤3,1 𝑤3,2 𝑤3,3 𝑤3,4 𝑤3,5 𝑤3,6 𝑤3,7 𝑤3,8
softmax
experts
…
Hi, I’m a pretrained 
large language 
model! …
J
Top-K
for a token 
47ms
80ms
Eq.(9)
Eq.(10)
Token 
index
User  
index
1 2 3 8
1
2
3
…
Algorithm 1 WDMoE Expert Selection at the BS
…
Processing either locally or at the BS
Token embedding after attention (at the BS)
Gating network (at the BS)
Weights for experts (at the BS)
WLR for devices (at the BS)
Final expert selection (at the BS)
Token transmission from the BS to users and 
result transmission from users to the BS
Data stream
Wireless transmission
Token processing latency
The BS
User devices
…J
Bandwidth Allocation
𝐵1 = 10 𝑀𝐻𝑧
𝐵2 = 15 𝑀𝐻𝑧
𝐵3 = 20 𝑀𝐻𝑧
𝐵8 = 20 𝑀𝐻𝑧
𝑤𝐽,1 𝑤𝐽,2 𝑤𝐽,3 𝑤𝐽,4 𝑤𝐽,5 𝑤𝐽,6 𝑤𝐽,7 𝑤𝐽,8
Fig. 4: The data stream, expert selection and bandwidth allocation in WDMoE. When a user sends a prompt to WDMoE,
it is preprocessed, embedded, and subjected to attention operations either locally or at BS, depending on user preference.
Each token’s embedding is analyzed by a gating network to assign weights to each expert. WDMoE dynamically adjusts these
weights, the number of experts, and optimize the bandwidth allocation based on gating network output and wireless channel
conditions. The token embeddings are sent to the respective devices for processing by expert networks. Once processed, the
results are sent back to BS, where they are weighted, summed, and then transformed from embeddings into words.
level problem seeks to minimize total latency by optimizing
the bandwidth allocation {Bk} and the expert selection matrix
Q, whereas the lower level problem aims to maximize device
profit by optimizing the expert selection matrix Q. The upper-
level problem is formulated as:
P1: min
B,Q
IX
i=1
ti
s.t.
UX
k=1
Bk = B, (13)
Bk ≥ 0, ∀k ∈ U, (14)
Q ∈ Φ(Q), (15)
where Φ(Q) = arg maxQ
PI
i=1
PU
k=1 W LRik is the expert
selection solution space at the lower level problem. The
constraints (13) and (14) represent that the bandwidth allocated
to each device is within the total bandwidth B.
The lower level problem is formulated as:
P2: max
Q
IX
i=1
UX
k=1
PJ
j=1 qij,kwij,k
qik · ti,k
s.t.
KX
k
qij,k ≥ 1, ∀j ∈ {1, · · ·, J}, (16)
qij,k ∈ {0, 1}. (17)
The j-th token in i-th MoE block is either processed by
the device k or not, and each token is processed on at least
one device. The lower level problem P2 is a combinatorial
optimization problem and can be reduced to the set cover
problem. Problem P2 is NP-hard, and thus the upper level
problem P1 also becomes an NP-hard optimization problem.
IV. E XPERT SELECTION POLICY AND BANDWIDTH
ALLOCATION
In this section, we first propose an expert selection policy to
solve the lower level problem P2, based on which we optimize
the bandwidth allocation to address problem P1. In particular,
the expert selection policy is first designed to dynamically
adjust the expert selection to improve the system’s overall
performance. Based on the proposed expert selection policy,
the bandwidth allocation algorithm is devised to optimize
the bandwidth allocation to minimize the total latency of the
system.
A. Expert Selection Policy
Retraining a LLM to account for wireless communication
conditions presents significant challenges, particularly in en-
abling the model to recognize and adapt to varying channel
conditions in distributed environments. Retraining the gating
network of an MoE layer is generally not advisable, as
it is both time-consuming and computationally demanding.

7
Furthermore, integrating wireless communication factors may
unintentionally disrupt the gating network, turning what is
originally a single-objective optimization problem into a multi-
objective problem, which can hinder model convergence. How-
ever, MoE-based LLMs are highly robust, even when expert
selection deviates from the trained gating network’s outputs.
In fact, moderate adjustments to expert selection are often
tolerated and may sometimes even outperform the original
selection. To address this, we propose a training-free scheme
to adjust expert selection and effectively solve the lower-level
optimization problem.
The data flow and the solution algorithm for the lower-
level optimization problem are depicted in Fig. 4. The process
begins when a sequence of tokens is fed into the gating
network, which assigns weights to each expert in the MoE
layer. Since the parameters of the router are frozen, the
output weights closely align with the model’s performance.
The device latency is estimated at the BS, where the BS has
access to the channel conditions of all devices and computes
the latency based on (8). Some devices may be located far
from the BS or in areas with poor coverage, potentially leading
to significant latency. The lower-level optimization objective
is designed to reduce the workload without degrading model
accuracy. To address this, we first compute the latency vector
for each token as tij = [ tij,1, · · ·, tij,k], assuming bandwidth
is evenly distributed. Next, cosine similarity is employed to
assess the relationship between the weights and the latency.
The cosine similarity is calculated as:
S(wij, tij) = wij ⊤tij|wij| · |tij| , (18)
where S(wij, tij) represents the cosine similarity of the j-th
token in the i-th block.
The expert selection policy is designed to adjust expert
selection based on cosine similarity. We define a threshold θ
to determine whether to drop the expert with minimal weights
after Top-K selection. The experts are sorted from the highest
weights to the lowest, and the top k experts are selected.
When S(wij, tij) ≤ θ, the expert with the lowest weights
will be dropped. Through this mechanism, we can reduce
communication and computational load without significant
impact on model performance. If we increase the threshold,
fewer experts will be chosen, which will decrease the total
load, though it may also affect model performance with greater
probability. This expert selection policy will benefit resource
allocation in the WDMoE-based LLM due to the reduction in
total load.
The threshold for expert selection can be adjusted based on
the WLR, with a higher threshold leading to the exclusion of
more experts and a corresponding increase in WLR to some
extent. It is crucial to note that a moderate increase in the
threshold can reduce latency without significantly impacting
model performance. However, an excessive increase in the
threshold may result in a substantial decline in performance,
despite achieving ultra-low latency. Thus, there may be a
trade-off between service latency and model performance. This
approach also supports dynamic expert selection, enabling
Algorithm 1 Expert Selection Policy for WDMoE
Input: Weights wij, and latency vectors tij for experts
Output: Optimized expert selection set Q
1: Initialize threshold θ ← 0.5
2: Select Top-2 experts based on weights Q ←
Top-K(wij, K= 2)
3: Compute initial WLR: PUk=1 ˆW LRik using Eq. (12)
4: while P3i=1 PUk=1 W LRik ≤ 1.01 × P3i=1 PUk=1 ˆW LRik
do
5: Compute cosine similarity S(wij, tij) using Eq. (18)
6: if S(wij, tij) ≤ θ and j ∈ Uthen
7: Update Q by dropping the expert with lower weights
for the j-th token
8: end if
9: Update threshold: θ ← θ + 0.1
10: end while
11: Recalculate cosine similarity S(wij, tij)
12: Update Q by removing experts with lower weights for the
j-th token
13: return Q
the system to select any number of experts as required. The
process can be iteratively repeated, as outlined in Algorithm
1. Dropping an expert is implemented by assigning a weight
of zero to that expert, thereby excluding the corresponding
device from participating in the processing.
B. Bandwidth Allocation
Given the expert selection Q, the upper level optimization
objective function is reorganized as
ti(B) = max
k∈U



JX
j=1
qij,k

 Lcomm
Bk log2

1 + P dk gBS,kN0Bk 
+ Lcomm
Bk log2

1 + P uk gk,BSN0Bk  + LcompCk




 ,
(19)
and Problem P1 is equivalent to
P3: min
B
IX
i=1
ti
s.t.
UX
k=1
Bk = B, (20)
Bk ≥ 0, ∀k ∈ U. (21)
Eq.(19) can be can be viewed as a composite form of several
functions:
ti(B) = max
k∈U
{fk(Bk)}, (22)
fk(Bk) =
JX
j=1
qij,kgj,k(Bk), (23)
gj,k(Bk) = h(vuj,k(Bk)) + h(vdj,k(Bk)) + LcompCk , (24)

8
TABLE I: Scores of different models on various benchmarks.
Model Active Params MMLU PIQA ARC-E ARC-C Humaneval GSM-8K BoolQ MBPP
Llama 2 7B 7B 46.8% 78.3% 56.1% 40.3% 12.8% 16.7% 74.9% 14.8%
Llama 2 13B 13B 55% 79.8% 71.8% 60.3% 18.9% 29.6% 82.4% 26.8%
Llama 2 70B 70B 69.7% 82.5% 85.9% 78.3% 26.2% 63.5% 87.7% 39.6%
Mistral 7B-v0.1 7B 64.1% 81.6% 83.6% 74.2% 22.6% 47.5% 84.1% 32.0%
Mixtral 8x7B-Instruct-v0.1 13B 70.0% 83.2% 92.8% 84.8% 47.6% 70.9% 88.72% 35.2%
WDMoE <13B 68.98% 83.51% 93.12% 86.78% 48.17% 71.29% 88.87% 37.4%
where
h(v) = Lcomm
v (25)
vuj,k(Bk) = Bk log2

1 + P uk gk,BS
N0Bk

, (26)
vdj,k(Bk) = Bk log2

1 + P dk gBS,k
N0Bk

. (27)
The domain of variable Bk is Bk > 0 and convex. The first
derivative of vuj,k(Bk) is given by:
vuj,k′(Bk) = log2

1 + P uk gk,BS
N0Bk

−
P uk gk,BS
ln 2
1
N0Bk + P uk gk,BS .
(28)
The second derivative of vuj,k(Bk) is given by:
vuj,k′′(Bk) = P uk gk,BSN0 ln 2 − P uk gk,BSN0Bk(Bk + P uk gk,BSN0 )2 ≤ 0. (29)
Since vu′′j,k(Bk) ≤ 0, we conclude that vuj,k(Bk) is concave.
In a similar way, vdj,k(Bk) is also a concave function. The
first derivative of h(v) is h′′(v) = − Lcommv2 < 0. The second
derivative of h(v) is h′′(v) = 2Lcommv3 and h′′(v) > 0 if v >
0. Here h is convex and nonincreasing. According to [41],
h(vdj,k(Bk)) and h(vuj,k(Bk)) are convex.
As a result, (24) is a form of nonnegative weighted sums that
preserves convexity, and (23) is also a nonnegative weighted
sums operation. It is proved that fk(Bk), k ∈ Uis convex.
Therefore, its pointwise maximum ti(B) is also convex.
Given a fixed Q, the constraint of P3 is affine, and the
domain of Bk is convex. Thus, Problem P3 is convex. It
is convenient to solve convex optimization problem through
various open source convex optimization algorithm, and Se-
quential Least Squares Programming implemented in SciPy
[42] is adopted in this paper.
V. S IMULATION RESULTS
In this section, we evaluate the performance of the proposed
WDMoE based on numerical results obtained from experi-
ments conducted on NVIDIA A40 GPUs.
A. Experiment Settings
In the simulation, we consider an MEC server deployed at
BS and 8 mobile devices. The expert network q in each MoE
layer is deployed on the q-th device. The distance between the
q-th device and BS is denoted as dq. We consider Rayleigh
fading channels with a mean 10−
P L(dq )
20 , where the path loss is
20 40 60 80 100 120
T otal bandwidth (MHz)
1000
2000
3000
4000
5000
6000
7000
8000Latency/batch (ms)
WDMoE
Mixtral-based method
Fig. 5: The latency per batch data versus total bandwidth based
on ARC-C dataset.
P L(dq)(dB) = 32.4 + 20log10(f carrier ) + 20log10(dq). The
carrier frequency f carrier is set as 3.5 GHz. The transmission
power of BS and the device is 10 Watts and 0.2 Watts,
respectively. The total bandwidth is 100 MHz, allocated evenly
among all devices.
We leverage OpenCompass Platform [43] to conduct an
in-depth and holistic evaluation of large language models.
The benchmarks include MMLU [44], PIQA [45], ARC-Easy,
ARC-Challenge [46], Humaneval [47], GSM-8K [48], BoolQ
[49], MBPP [50].
B. Performance Evaluation
We compare WDMoE with state-of-the-art models released
during the same period, including Llama 2 with 7B, 13B and
70B parameters, as well as Mistral (referred to as Mixtral
7B-v0.1) and Mixtral (referred to as Mixtral 8x7B-Instruct-
v0.1), across various benchmarks. Besides, we evaluate the
latency of Mixtral and WDMoE in the wireless network. The
Mixtral-based method represents distributedly deploy Mixtral
and allocates bandwidth evenly.
Model Capability. The detailed results are shown in Table
I. Due to the dynamic nature of WDMoE, the total number
of active parameters in the MoE remains under 13B, which is
fewer than both Llama 2 13B and Mixtral in certain instances.
From Table I, we observe that the WDMoE model outperforms
Llama 2 70B across most benchmarks while activating at
most 20% of the parameters and generally surpassing Mixtral.
Specifically, WDMoE achieves the best results on the PIQA,

9
humaneval mbpp gsm8k
Dataset
0
200
400
600
800
1000
1200
1400
1600
Latency/batch  (ms)
Mixtral-based method
WDMoE
(a)
ARC-e ARC-c BoolQ piqa mmlu
Dataset
0
50000
100000
150000
200000
250000
300000
Latency/batch  (ms)
Mixtral-based method
WDMoE (b)
Fig. 6: Latency versus different datasets: (a) Humaneval, MBPP and GSM-8K datasets; (b) The rest datasets.
600 700 800 900 1000 1100 1200 1300
T oken number
500
750
1000
1250
1500
1750
2000
2250Latency/batch (ms)
Mixtral-based method
WDMoE w./o bandwidth allocation
WDMoE w./o expert selection
WDMoE
Fig. 7: Ablation study for different cases based on ARC-C
dataset.
ARC-E, ARC-C, Humaneval, GSM-8K and BoolQ bench-
marks. WDMoE shows minimal performance degradation on
MMLU benchmarks. In the ARC-C benchmark, WDMoE
exhibits significantly higher accuracy compared to both Llama
2 70B and Mixtral, scoring 86.78% versus 78.3% and 84.8%,
respectively. Latency. We evaluate the end-to-end latency of
Mixtral and WDMoE. Fig. 5 illustrates the latency per batch
of data versus total bandwidth. The solid line represents the
performance of WDMoE, while the dashed line denotes the
performance of Mixtral with the uniform bandwidth allocation.
As bandwidth increases, both methods exhibit a decreasing
trend in latency. The proposed WDMoE consistently outper-
forms the Mixtral-based method, by maintaining significantly
lower latency across all bandwidth levels. Fig. 6 presents the
average latency per batch with different methods on various
datasets. We can see that, compared to the Mixtral-based
method, the proposed WDMoE reduces the latency by 41.40%,
47.14% and 41.96% for the corresponding dataset in Fig. 6(a)
and 40.41%, 42.03%, 45.14%, 47.50% and 42.19% for the
corresponding dataset in Fig. 6(b).
C. Ablation Study
We perform ablations on both the upper level and lower
level optimizations in the bilevel optimization problem to
evaluate their contributions to reducing latency. In Fig. 7,
using the change in latency with the number of tokens from
the ARC-C dataset as an example, the expert selection policy
achieves a 6.89% performance gain (WDMoE vs. WDMoE
w./o expert selection). Meanwhile, the bandwidth allocation
shows a 36.59% improvement (WDMoE vs. WDMoE w./o
bandwidth allocation). The primary reason for this fact is that
the upper level optimization focuses on reducing overall atten-
tion waiting latency, and its solution is specifically designed
to optimize this aspect. The ablation study is conducted on
all datasets used in this paper, and the results are presented in
Table II. A key finding from Table II is that the expert selection
yields a greater improvement when combined with bandwidth
optimization compared to the Mixtral with uniform bandwidth
allocation method. This suggests that the proposed expert
selection is particularly effective in communication scenarios
involving bandwidth allocation.
D. Insight for Practical Deployment of WDMoE-based LLMs
In terms of expert network with hundreds of million param-
eters, as the number of mobile devices in the wireless network
increases, mobile devices can load more expert networks from
a specific MoE layer while loading fewer expert networks from
other MoE layers. In the simulation, we observe a signifi-
cant phenomenon that various tokens in a text sequence are
transmitted to the same experts. Fig. 8 shows the proportion
of the same expert selection for distinct tokens in the first
MoE layer, the sixteenth MoE layer and the thirty-second
MoE layer. In the ARC-C dataset, the maximum proportion
of expert selection pairs exceeds 25% in most MoE layers.
Similar situations also appeared in other datasets and MoE
layers. We can conclude that if we deploy expert networks
of an MoE layer using an adjustable method to harness the

10
TABLE II: Latency/batch (ms) on all the components of WDMoE.
Components MMLU PIQA ARC-E ARC-C Humaneval GSM-8K BoolQ MBPP
Mixtral-based Method 298813.6 37183.1 36401.5 40367.1 572.6 1661.6 109957.8 847.9
WDMoE w./o bandwidth allocation 258884.0 33861.6 35043.3 37584.2 527.3 1491.5 106806.9 700.9
WDMoE w./o expert selection 195383.3 22114.1 22774.5 25598.4 335.2 1066.0 66684.0 538.1
WDMoE 172743.9 19522.2 21692.0 23400.0 305.9 964.5 63991.0 448.2
BoolQ Arc-c Arc-e PIQA
Dataset
0.00
0.05
0.10
0.15
0.20
0.25Proportion of Indentical Pairs
Layer
Layer 1
Layer 16
Layer 32
Fig. 8: The maximum ratio of the same expert selection in one
batch.
memory and computing power of a large amount of mobile
devices such as deploying the two most frequently selected
expert networks for the same token in an MoE layer, the
attention waiting latency will be decreased. This is because
a more efficient distributed deployment policy can prevent
duplicate transmission of a token. Reducing the volume of
token transmission at the source will benefit more efficient
bandwidth allocation and decrease latency.
VI. H ARDWARE TESTBED FOR WDM OE- BASED LLM S
In this section, we develop a hardware testbed for WDMoE
using NVIDIA Jetson Kits to demonstrate its efficiency in
terms of latency and model accuracy in a practical environ-
ment.
A. System Components
As shown in Fig. 9(a), the hardware platform consists of
two NVIDIA Jetson AGX Orin devices, an NVIDIA Jetson
Xavier NX, a computer with an NVIDIA RTX 4070 Ti, a
server equipped with four NVIDIA A40 GPUs, and a TP-
LINK AX3000 router.
The router serves as a wireless access point, simulating
the BS in our experiment and is responsible for receiving
processed results from mobile devices and distributing new
tokens to them. Devices equipped with different GPUs exhibit
varying computational resources, and communication latency
can be controlled by adjusting the physical placement of the
devices to vary their distance from the BS.
Each device is equipped with a subset of experts from all
MoE blocks. Due to the limited number of devices, only four
experts are allocated to each device for each MoE layer, while
the remaining expert networks are executed on the server.
In the WDMoE, devices receive tokens from the BS and
transmit processed tokens back to it. In our practical experi-
ment, the Transmission Control Protocol (TCP) is used at the
transport layer, while the wireless local area network operates
based on the IEEE 802.11ax protocol.
B. Simulated Scenarios
The simulated scenario involves the collaboration of multi-
ple mobile devices for the deployment and inference of LLMs
in communication networks, particularly in wireless networks,
according to our proposed WDMoE architecture. Fig. 9(b)
illustrates the geographical distribution. The length of the
square is 1.45 m, and the width is 0.8 m. The experiment
is conducted indoors. Fig. 9(b) shows the layout of the
transmitter and mobile devices. The transmitter is centrally
located, as represented by the blue square, while the UEs are
distributed around it—UE 1 (orange circle), UE 2 and UE
3 (green and purple stars), and UE 4 (yellow triangle). This
ensures a realistic wireless network environment for testing.
C. Wireless Distributed Acceleration Algorithm
The primary purpose of this hardware testbed system is
to verify the effectiveness of the WDMoE deployment archi-
tecture and the basic concepts for expert selection, without
estimating channel conditions, predicting transmission rates, or
allocating communication bandwidth to reduce latency. There-
fore, the optimization algorithm based on estimated latency,
as discussed in Section IV , is not suitable for this system. As
analyzed in Section V , balancing the workload across experts
can effectively accelerate processing under certain conditions
without degrading model performance. Consequently, we pro-
pose an expert selection policy specifically designed for this
hardware system to achieve faster model inference.
During program execution, the historical transmission and
processing latency for device k at each layer is recorded as
tk. The corresponding number of tokens processed by device
k is denoted as Jk. The average latency per token is given by:
tk = E
 tk
Jk

. (30)
Based on experimental data, the variance in latency per
token for each expert is sufficiently low, allowing the mean
latency per token to serve as a reliable estimate. Since the
gating network is deployed on the server, the server can use
this average latency per token, along with the number of tokens
processed by each device, to predict the total latency for each
device:
ˆtik = tk · Jk. (31)

11
Server Controller
UE 4: NVIDIA 
JETSON NX
UE 2: NVIDIA 
JETSON AGX Orin
UE 1: NVIDIA 
RTX 4070TI
Router:
TP-LINK 
AX3000
UE 3: NVIDIA 
JETSON AGX Orin
(a)
16.5m
UE 1 UE 2 Transmitter UE 4UE 3 (b)
Fig. 9: (a) System components of WDMoE hardware testbed; (b) Geographical distribution of experiment devices.
Algorithm 2 Expert Selection for WDMoE Hardware Testbed
Input: Weights wij, and historical latency tk
Output: Selected expert set ˆQ
1: ˆQ ← Top-K(wij), K= 2
2: Initialize ˆJ k ← 0, k ∈ U
3: Initialize ˆJ ← {}, ˆW ← {}
4: for k ∈ Udo
5: Calculate the allocated tokens for expert k: Jk
6: Predict latency for expert k: ˆtik ← Eq. 31
7: end for
8: Identify latency bottleneck: ˆk ← arg maxk∈U {ˆtik}
9: Analyze upper bound for dropable tokens: ˆJ dropk ←
Eq. 32
10: for all l ∈ Jdo
11: if wil,ˆk < 15 PJj=1 qij,ˆkwij,ˆk then
12: Add token l to ˆJ and its weight wil,ˆk to ˆW
13: Increment token count: ˆJ ˆk ← ˆJ ˆk + 1
14: end if
15: end for
16: if ˆJ ˆk > ˆJ dropˆk then
17: Select tokens to drop: Top-K (− ˆW), K= ˆJ dropˆk
18: Set weights of dropped tokens to zero and update ˆQ
19: else
20: Include tokens in ˆJ and update ˆQ
21: end if
22: return ˆQ
The expert ˆk = arg maxk∈U {tik} represents the bottleneck
expert, with ˆtiˆk being the estimated time for both communica-
tion and computation. When ˆtiˆk is significantly larger than that
of other experts, the load assigned to device ˆk must be reduced.
Specifically, if ˆtiˆk exceeds 1.5 times the third quartile of the
predicted latency across all devices, then device ˆk is identified
as a major contributor to the inference delay of the MoE layer.
The third quartile of the predicted latency is denoted as ˆti3
4
.
The maximum number of tokens that can be offloaded from
device ˆk is calculated by:
ˆJ dropk =
$ ˆtiˆk − ˆti34
ˆtik
%
(32)
where ⌊·⌋ denotes round down operation.
For higher model accuracy, the expert k will be excluded
from selection when its weight is excessively low for a
specific token. When the weight of expert k for a token is
the lowest after Top-K operation and satisfies the condition
wil,k < 15 PJj=1 qij,kwij,k, the token will be dropped and no
longer allocated to the expert k. If the number of tokens that
meet the above conditions exceeds ˆJ dropk , select the tokens
corresponding to the ˆJ dropk smallest weights to drop. If the
number of tokens that meet the exclusion criteria is less than
ˆJ dropk , the tokens corresponding to ˆJ dropk smallest weights will
be selected for dropping. If the number of tokens that meet the
exclusion criteria is less than ˆJ dropk , those tokens will not be
transmitted to the expert k. Otherwise, the tokens with the least
ˆJ dropk weights will be dropped to avoid the poor performance
due to the decrease in total weights. Assuming the latency
prediction is accurate, further reducing the number of trans-
mitted tokes will neither lower latency nor maintain model
performance. The expert selection process in the hardware
testbed system is described in the Algorithm 2. and the expert
selection is conducted on the server. The server determines the
assignment of token computation through expert selection ˆQ,
and the router distributes tokens to the devices in the network.
This method is specifically designed to reduce attention
waiting latency by identifying latency bottlenecks and em-
ploying targeted expert selection. Its key advantages lie in
its simplicity and efficiency, rendering it a viable solution for
performance optimization.
D. Hardware Experiment Results
We evaluate the performance of our hardware testbed system
from both model capability and attention waiting latency,
based on theoretically simulated experiments, and compare the
proposed method with the baseline Mixtral-based method. The

12
600 700 800 900 1000 1100 1200 1300
T oken number
20
40
60
80
100
120
140
160Latency/batch (ms)
Mixtral-based method
WDMoE
Fig. 10: Latency of different methods on the hardware testbed
system.
TABLE III: Model accuracy.
Model ARC-E ARC-C MBPP PIQA
Mixtral 92.42 86.1 37.8 83.41
WDMoE-testbed 92.95 87.12 38.8 83.51
Mixtral-based method refers to the Top-K selection method of
Mixtral. We conduct three experiments on various benchmarks
for both the vanilla selection and our proposed method under
the same environmental settings to eliminate random errors to
the best of our ability.
Based on theoretical simulated experiment results, the
model capability of the hardware system’s algorithm is verified
on only four benchmarks for convenience, including ARC-
E, ARC-C, MBPP, and PIQA. The evaluation results indicate
that our algorithm’s distributed deployment with expert selec-
tion outperforms the vanilla expert selection which does not
consider latency. The latency per batch in a layer versus the
number of tokens is shown in Fig. 10. The line represents the
mean latency, while the shaded area indicates the range of
latency values. The orange area is generally below the green
area, except at two points where the maximum latency values
are higher due to channel variation in practical experiments.
To present the results more fully, we record the latency data of
three groups of comparative experiments in Table IV, where
the maximum average latency reduction reaches 45.75%. The
hardware system experiments validate our theoretical analysis
and experimental results.
VII. C ONCLUSION
In this paper, we introduce WDMoE, a wireless distributed
MoE architecture for LLMs. This architecture enables the col-
laborative deployment of LLMs across the MEC server at the
BS and mobile devices in the wireless networks. By leveraging
the parallel characteristics of expert networks, the deployment
architecture effectively models attention waiting latency and
incorporates the WLR metric, which jointly assesses model
performance and service latency. Through the development
of expert selection and bandwidth allocation strategies, we
TABLE IV: Latency/batch (ms) in hardware testbed experi-
ments.
Model ARC-E ARC-C MBPP PIQA
Mixtral-based method-1 532.8 1625 38.77 616.7
WDMoE-testbed-1 468.3 1228 37.96 414.3
Mixtral-based method-2 418.1 2583 33.47 1380
WDMoE-testbed-2 372.6 1530 29.49 436.9
Mixtral-based method-3 383.5 1406 30.72 519.4
WDMoE-testbed-3 361.9 656.6 28.33 332.0
Average Gain 9.536% 39.523% 7.246% 45.750%
solve the formulated bilevel optimization problem. Besides,
we build a hardware testbed to validate the effectiveness
of the proposed method. Extensive experiments demonstrate
WDMoE ensures high performance and significantly reduces
latency, which verifies the feasibility of distributed LLMs
in wireless scenarios and highlights the promising future of
cooperative edge-device large models.
REFERENCES
[1] N. Xue, Y . Sun, Z. Chen, M. Tao, X. Xu, L. Qian, S. Cui, and P. Zhang,
“WDMoE: Wireless Distributed Large Language Models with Mixture
of Experts,” arXiv preprint arXiv:2405.03131 , 2024.
[2] OpenAI. (2022) Introducing ChatGPT. [Online]. Available: https:
//www.openai.com/blog/chatgpt/
[3] J. Wei, Y . Tay, R. Bommasani, C. Raffel, B. Zoph, S. Borgeaud,
D. Yogatama, M. Bosma, D. Zhou, D. Metzler, E. H. Chi, T. Hashimoto,
O. Vinyals, P. Liang, J. Dean, and W. Fedus, “Emergent Abilities of
Large Language Models,” Transactions on Machine Learning Research,
2022.
[4] S. Bubeck, V . Chandrasekaran, R. Eldan, J. Gehrke, E. Horvitz, E. Ka-
mar, P. Lee, Y . T. Lee, Y . Li, S. Lundberg, H. Nori, H. Palangi, M. T.
Ribeiro, and Y . Zhang, “Sparks of Artificial General Intelligence: Early
experiments with GPT-4,” arXiv preprint arXiv:2303.12712 , 2023.
[5] J. Shao, J. Tong, Q. Wu, W. Guo, Z. Li, Z. Lin, and J. Zhang,
“WirelessLLM: Empowering Large Language Models Towards Wireless
Intelligence,” arXiv preprint arXiv:2405.17053 , 2024.
[6] W. Lee and J. Park, “LLM-Empowered Resource Allocation in Wireless
Communications Systems,” arXiv preprint arXiv:2408.02944 , 2024.
[7] J. Shao, J. Tong, Q. Wu, W. Guo, Z. Li, Z. Lin, and J. Zhang,
“Wirelessllm: Empowering large language models towards wireless
intelligence,” Journal of Communications and Information Networks ,
vol. 9, no. 2, pp. 99–112, 2024.
[8] H. Zhou, C. Hu, Y . Yuan, Y . Cui, Y . Jin, C. Chen, H. Wu, D. Yuan,
L. Jiang, D. Wu, X. Liu, C. Zhang, X. Wang, and J. Liu, “Large Lan-
guage Model (LLM) for Telecommunications: A Comprehensive Sur-
vey on Principles, Key Techniques, and Opportunities,” arXiv preprint
arXiv:2405.10825, 2024.
[9] N. Sehad, L. Bariah, W. Hamidouche, H. Hellaoui, R. J ¨antti, and
M. Debbah, “Generative AI for Immersive Communication: The
Next Frontier in Internet-of-Senses Through 6G,” arXiv preprint
arXiv:2404.01713, 2024.
[10] J. Kaplan, S. McCandlish, T. Henighan, T. B. Brown, B. Chess, R. Child,
S. Gray, A. Radford, J. Wu, and D. Amodei, “Scaling Laws for Neural
Language Models,” arXiv preprint arXiv:2001.08361 , 2020.
[11] J. Hoffmann, S. Borgeaud, A. Mensch, E. Buchatskaya, T. Cai,
E. Rutherford et al., “Training Compute-Optimal Large Language Mod-
els,” in Proceedings of the 36th International Conference on Neural
Information Processing Systems , 2022, pp. 30 016–30 030.
[12] J. Xu, Z. Li, W. Chen, Q. Wang, X. Gao, Q. Cai, and Z. Ling, “On-
Device Language Models: A Comprehensive Review,” arXiv preprint
arXiv:2409.00088, 2024.
[13] X. Ma, G. Fang, and X. Wang, “LLM-Pruner: On the Structural Pruning
of Large Language Models,” Advances in neural information processing
systems, vol. 36, pp. 21 702–21 720, 2023.
[14] J. Lin, J. Tang, H. Tang, S. Yang, W.-M. Chen, W.-C. Wang, G. Xiao,
X. Dang, C. Gan, and S. Han, “AWQ: Activation-aware Weight Quanti-
zation for On-Device LLM Compression and Acceleration,”Proceedings
of Machine Learning and Systems , vol. 6, pp. 87–100, 2024.

13
[15] M. Abdin, J. Aneja, H. Awadalla, A. Awadallah, A. A. Awan, N. Bach
et al. , “Phi-3 Technical Report: A Highly Capable Language Model
Locally on Your Phone,” arXiv preprint arXiv:2404.14219 , 2024.
[16] T. Gunter, Z. Wang, C. Wang, R. Pang, A. Narayanan, A. Zhang
et al., “Apple Intelligence Foundation Language Models,” arXiv preprint
arXiv:2407.21075, 2024.
[17] OpenAI. (2024) OpenAI and Apple Announce Partnership to
Integrate ChatGPT into Apple Experiences. [Online]. Available:
https://openai.com/index/openai-and-apple-announce-partnership/
[18] R. Pope, S. Douglas, A. Chowdhery, J. Devlin, J. Bradbury, J. Heek,
K. Xiao, S. Agrawal, and J. Dean, “Efficiently Scaling Transformer
Inference,” Proceedings of Machine Learning and Systems , vol. 5, pp.
606–624, 2023.
[19] H. Liu, Z. Chen, and L. Qian, “The three primary colors of mobile
systems,” IEEE Communications Magazine , vol. 54, no. 9, pp. 15–21,
2016.
[20] Y . Tian, Z. Zhang, Y . Yang, Z. Chen, Z. Yang, R. Jin, T. Q. S. Quek, and
K.-K. Wong, “An edge-cloud collaboration framework for generative
ai service provision with synergetic big cloud model and small edge
models,” IEEE Network, vol. 38, no. 5, pp. 37–46, 2024.
[21] H. Wang, H. Li, M. Sheng, and J. Li, “Collaborative fine-tuning of
mobile aigc models with wireless channel conditions,” IEEE Wireless
Communications, vol. 31, no. 4, pp. 32–38, 2024.
[22] N. Shazeer, A. Mirhoseini, K. Maziarz, A. Davis, Q. Le, G. Hinton, and
J. Dean, “Outrageously Large Neural Networks: The Sparsely-Gated
Mixture-of-Experts Layer,” in International Conference on Learning
Representations, 2017.
[23] D. Lepikhin, H. Lee, Y . Xu, D. Chen, O. Firat, Y . Huang, M. Krikun,
N. Shazeer, and Z. Chen, “GShard: Scaling Giant Models with Condi-
tional Computation and Automatic Sharding,” in International Confer-
ence on Learning Representations , 2021.
[24] A. Vaswani, N. Shazeer, N. Parmar, J. Uszkoreit, L. Jones, A. N. Gomez,
L. u. Kaiser, and I. Polosukhin, “Attention is All you Need,” in Advances
in Neural Information Processing Systems , vol. 30, 2017.
[25] A. Radford, K. Narasimhan, T. Salimans, and I. Sutskever, “Improving
Language Understanding by Generative Pre-Training,” 2018.
[26] J. Devlin, M.-W. Chang, K. Lee, and K. Toutanova, “BERT: Pre-training
of Deep Bidirectional Transformers for Language Understanding,” arXiv
preprint arXiv:1810.04805, 2018.
[27] A. Radford, J. Wu, R. Child, D. Luan, D. Amodei, and I. Sutskever,
“Language Models Are Unsupervised Multitask Learners,” OpenAI blog,
vol. 1, no. 8, p. 9, 2019.
[28] T. Brown, B. Mann, N. Ryder, M. Subbiah, J. D. Kaplan, P. Dhariwal
et al., “Language Models are Few-Shot Learners,” in Advances in Neural
Information Processing Systems , vol. 33, 2020, pp. 1877–1901.
[29] A. Dubey, A. Jauhri, A. Pandey, A. Kadian, A. Al-Dahle, A. Letman
et al., “The Llama 3 Herd of Models,” arXiv preprint arXiv:2407.21783,
2024.
[30] R. A. Jacobs, M. I. Jordan, S. J. Nowlan, and G. E. Hinton, “Adaptive
Mixtures of Local Experts,” Neural Computation, vol. 3, no. 1, pp. 79–
87, 1991.
[31] A. Q. Jiang, A. Sablayrolles, A. Roux, A. Mensch, B. Savary, C. Bam-
ford et al., “Mixtral of experts,” arXiv preprint arXiv:2401.04088, 2024.
[32] T. Chen, X. Chen, X. Du, A. Rashwan, F. Yang, H. Chen, Z. Wang,
and Y . Li, “AdaMV-MoE: Adaptive Multi-Task Vision Mixture-of-
Experts,” in 2023 IEEE/CVF International Conference on Computer
Vision (ICCV), 2023, pp. 17 300–17 311.
[33] Q. Huang, Z. An, N. Zhuang, M. Tao, C. Zhang, Y . Jin, K. Xu, L. Chen,
S. Huang, and Y . Feng, “Harder Tasks Need More Experts: Dynamic
Routing in MoE Models,” arXiv preprint arXiv:2403.07652 , 2024.
[34] W. Yin, M. Xu, Y . Li, and X. Liu, “LLM as a System Service on Mobile
Devices,” arXiv preprint arXiv:2403.11805 , 2024.
[35] Z. Yu, Z. Wang, Y . Li, H. You, R. Gao, X. Zhou, S. R. Bommu,
Y . K. Zhao, and Y . C. Lin, “EDGE-LLM: Enabling Efficient Large
Language Model Adaptation on Edge Devices via Layerwise Unified
Compression and Adaptive Layer Tuning and V oting,” arXiv preprint
arXiv:2406.15758, 2024.
[36] Z. Liu, C. Zhao, F. Iandola, C. Lai, Y . Tian, I. Fedorov, Y . Xiong,
E. Chang, Y . Shi, R. Krishnamoorthi, L. Lai, and V . Chandra, “Mo-
bileLLM: Optimizing Sub-billion Parameter Language Models for On-
Device Use Cases,” arXiv preprint arXiv:2402.14905 , 2024.
[37] D. Peng, Z. Fu, and J. Wang, “PocketLLM: Enabling On-Device Fine-
Tuning for Personalized LLMs,”arXiv preprint arXiv:2407.01031, 2024.
[38] “IEEE Standard for Floating-Point Arithmetic,” IEEE Std 754-2019
(Revision of IEEE 754-2008) , pp. 1–84, 2019.
[39] P. Molchanov, S. Tyree, T. Karras, T. Aila, and J. Kautz, “Pruning
Convolutional Neural Networks for Resource Efficient Inference,” in
International Conference on Learning Representations , 2017.
[40] S. Dempe, Foundations of bilevel programming . Springer Science &
Business Media, 2002.
[41] S. Boyd and L. Vandenberghe, Convex Optimization . Cambridge
university press, 2004.
[42] P. Virtanen, R. Gommers, T. E. Oliphant, M. Haberland, T. Reddy,
D. Cournapeau et al., “SciPy 1.0: Fundamental Algorithms for Scientific
Computing in Python,” Nature Methods, vol. 17, pp. 261–272, 2020.
[43] O. Contributors, “OpenCompass: A Universal Evaluation Platform for
Foundation Models,” https://github.com/open-compass/opencompass,
2023.
[44] D. Hendrycks, C. Burns, S. Basart, A. Zou, M. Mazeika, D. Song, and
J. Steinhardt, “Measuring Massive Multitask Language Understanding,”
in International Conference on Learning Representations , 2021.
[45] Y . Bisk, R. Zellers, R. L. Bras, J. Gao, and Y . Choi, “PIQA: Reasoning
about Physical Commonsense in Natural Language,” in Proceedings of
the AAAI conference on artificial intelligence , vol. 34, no. 05, 2020, pp.
7432–7439.
[46] P. Clark, I. Cowhey, O. Etzioni, T. Khot, A. Sabharwal, C. Schoenick,
and O. Tafjord, “Think you have Solved Question Answering? Try ARC,
the AI2 Reasoning Challenge,” arXiv preprint arXiv:1803.05457, 2018.
[47] M. Chen, J. Tworek, H. Jun, Q. Yuan, H. P. de Oliveira Pinto, J. Kaplan
et al. , “Evaluating Large Language Models Trained on Code,” arXiv
preprint arXiv:2107.03374, 2021.
[48] K. Cobbe, V . Kosaraju, M. Bavarian, M. Chen, H. Jun, L. Kaiser,
M. Plappert, J. Tworek, J. Hilton, R. Nakano, C. Hesse, and J. Schulman,
“Training Verifiers to Solve Math Word Problems,” arXiv preprint
arXiv:2110.14168, 2021.
[49] C. Clark, K. Lee, M.-W. Chang, T. Kwiatkowski, M. Collins, and
K. Toutanova, “BoolQ: Exploring the Surprising Difficulty of Natural
Yes/No Questions,” arXiv preprint arXiv:1905.10044 , 2019.
[50] J. Austin, A. Odena, M. Nye, M. Bosma, H. Michalewski, D. Dohan,
E. Jiang, C. Cai, M. Terry, Q. Le, and C. Sutton, “Program Synthesis
with Large Language Models,” arXiv preprint arXiv:2108.07732, 2021.