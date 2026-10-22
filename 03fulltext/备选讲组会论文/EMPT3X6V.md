---
type: literature-fulltext
title: "RL-Based Anti-Jamming Maritime Communications for LLM Inference"
zotero_key: "EMPT3X6V"
pdf_key: "SFRGHSFF"
doi: "10.1109/TWC.2026.3679548"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/RL-Based Anti-Jamming Maritime Communications for LLM Inference.md"
fulltext_path: "03fulltext/备选讲组会论文/EMPT3X6V.md"
zotero_item: "zotero://select/library/items/EMPT3X6V"
zotero_pdf: "zotero://open-pdf/library/items/SFRGHSFF"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# RL-Based Anti-Jamming Maritime Communications for LLM Inference

> PDF 原文逐页文本抽取；来源文件 SHA-256：`65cc2b24a63b489da92b4da320bd18aedc943ba81537217b6b633fcac85bde56`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

14676 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
RL-Based Anti-Jamming Maritime Communications
for LLM Inference
Huanhuan Liu
 , Graduate Student Member , IEEE , Liang Xiao
 , Fellow, IEEE, Weiqi Lin
 , Pengli Zhang,
Haoyu Chen
 , Graduate Student Member , IEEE , Zefang Lv
 , Member , IEEE, and Manhao Jiang
Abstract—Reinforcement learning (RL)-based anti-jamming
communication schemes select the transmit power and channel
to send images or point clouds, but have low transmission
reliability due to lack of maritime environmental features and
the delayed feedback under harsh channel conditions caused
by sea surface reﬂections and wave ﬂuctuations. In this paper,
we propose an RL-based anti-jamming maritime communication
scheme for LLM inference that enables user equipment (UE)
to optimize uplink power, channel and data compression ratio
for transmitting multi-modal data based on data size of each
modality, number of received packets, environmental features
such as weather conditions and jamming features such as
the received jamming power with quality-of-service guarantee.
The historical anti-jamming experiences are used to recover the
delayed feedback or loss and reduce communication outage under
harsh maritime channel. The upper bound in terms of latency,
UE energy consumption and inference accuracy is provided
based on a maritime anti-jamming game to show the impact
of the number of modalities, bandwidth and channel gains.
The proposed scheme is implemented based on UEs equipped
with Jetson Orin, camera and BME280 sensors for transmitting
200-KB temperature, humidity and pressure as well as images
to the control center for LLaV A-based environmental feature
extraction and marine object detection. Experimental results
based on 4 UEs at Harbor show the performance gain with
40.5% less latency, 46.4% lower UE energy consumption and
10.9% higher inference accuracy against the smart jammer.
Index Terms—Maritime communications, large language
model, multi-modal data, jamming, reinforcement learning.
I. I NTRODUCTION
M
ARITIME communications enable the transmission of
multi-modal data such as audio, images, videos and
point clouds between user equipment (UE) such as ships and
Received 10 November 2025; revised 14 February 2026; accepted 28 March
2026. Date of current version 3 April 2026. This work was supported in part by
the National Natural Science Foundation of China under Grant U25A20388,
in part by the Fundamental Research Funds for the Central Universities
20720250036, in part by the National Key Research and Development Pro-
gram of China under Grant 2023YFB3107603, and in part by the Postdoctoral
Fellowship Program of Chinese Postdoctoral Science Foundation (CPSF)
under Grant GZC20252299. An earlier version of this paper was presented
in part at the 2025 IEEE 102nd Vehicular Technology Conference [DOI:
10.1109/VTC2025-Fall65116.2025.11310393]. The associate editor coordi-
nating the review of this article and approving it for publication was K. Zhang.
(Corresponding author: Liang Xiao.)
Huanhuan Liu, Liang Xiao, Weiqi Lin, Pengli Zhang, and Manhao Jiang are
with the Department of Informatics and Communication Engineering, Xiamen
University, Xiamen 361005, China (e-mail: lxiao@xmu.edu.cn).
Haoyu Chen is with the Institute of Artiﬁcial Intelligence, Xiamen Univer-
sity, Xiamen 361005, China.
Zefang Lv is with the Institute of Space Internet, Fudan University,
Shanghai 200438, China (e-mail: lvzefang@fudan.edu.cn).
Digital Object Identiﬁer 10.1109/TWC.2026.3679548
uncrewed aerial vehicles (UA Vs) and the control center [1].
Due to the heterogeneity of multi-modal data, large language
models (LLMs) such as LLaV A and NExT-GPT with scene
understanding and language generation capabilities are utilized
to perform inference for situational awareness, supporting
vessel trafﬁc monitoring and maritime search and rescue [2].
However, maritime communications are vulnerable to mali-
cious jamming and harsh channel conditions caused by sea
surface reﬂections, wave ﬂuctuations and weather conditions
such as rainfall and storms, which degrade transmission reli-
ability of multi-modal data and delay feedback information
such as performance metrics and inference results, and even
lead to mission failure or UE loss of control [3]. Furthermore,
the interference resulting from spectrum conﬂicts when mul-
tiple UEs contend for the same frequency resources further
complicates reliable communication in hotspot areas [4].
Reinforcement learning (RL)-based anti-jamming commu-
nication schemes optimize the power control and channel
selection based on the received signal strength indicator
and channel state to improve signal-to-interference-plus-noise
(SINR) and reduce the energy consumption and latency [5],
[6], [7], [8]. For example, a seminal scheme named DAS in
[6] adopts a dual-action network to select power and channel
for transmitting data packets based on power spectral density
against ﬁxed, sweep and random jamming. However, these
schemes fail to meet the quality of service (QoS) requirements
such as energy efﬁciency and inference accuracy of multi-
modal data transmission for maritime applications due to lack
of environmental features, the delayed feedback under harsh
channel conditions, and smart jamming.
In this paper, we propose a deep RL (DRL)-based anti-
jamming maritime communication scheme for LLM inference,
in which the UE uses an actor-critic algorithm to choose the
transmission policy for sending multi-modal data, including
data compression ratio, transmit power and channel to improve
the inference accuracy and reduce the latency and energy
consumption with QoS guarantee. The control center utilizes
LLM to perform the environmental feature extraction and
marine object detection such as ships and vessels based on
received multi-modal data.
Besides the data size per modality, number of received
packets, and jamming features such as jammed channels
and the received jamming power, environmental features
such as indoor or outdoor scenario and rainfall indicator
are incorporated in state formulation to guide the selection
of transmission policy. By sharing redundancy-reduced local
1536-1276 © 2026 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 2 页

LIU et al.: RL-BASED ANTI-JAMMING MARITIME COMMUNICATIONS FOR LLM INFERENCE 14677
observations among neighboring UEs, the proposed scheme
enlarges the receptive ﬁeld and enhances optimization efﬁ-
ciency in a partially observable marine environment. The
UE historical anti-jamming experiences in previous time slots
are employed to recover the delayed or missing feedback
under harsh channel conditions, thereby mitigating the risk
of selecting sub-optimal transmission policies that may lead
to communication outage.
The interaction between the UEs and the jammer is for-
mulated as the maritime anti-jamming game, in which the
smart jammer as the leader that optimizes the jamming power
to minimize the SINR received at the control center and
energy cost, while the UE as the follower selects the data
compression ratio, transmit power and channel to enhance
the inference accuracy with less UE energy consumption
and latency. The upper bound is provided according to the
Stackelberg equilibrium (SE), indicating that the latency and
UE energy consumption grow linearly with the number of
modalities and data size, and inference accuracy exhibits an
exponential saturation increase with the channel gain.
Our proposed scheme is implemented for transmitting multi-
modal data including temperature, humidity and pressure as
well as images through IEEE 802.11n protocol based on
the UE equipped with Jetson Orin, camera and BME280
sensors. The control center equipped with RTX 3060 GPU
generates inference results including environmental features
and marine objects and obtains jamming features via universal
software radio peripheral (USRP) B210. The multi-modal
data, performance metrics and inference results are visualized
through the graphical user interface (GUI).
Simulations are performed on 7 UEs transmitting 200-KB
text and images from the WaterScenes dataset [9] with up
to 100 mW power on 10 channels that depend on the three-
ray path loss model in [10] against a Q-learning-based smart
jammer. The control center running LLaV A integrates two
modalities via a vision CLIP encoder ViT-L/14 with a lan-
guage model Vicuna 7B to identify the marine communication
environment and objects such as boat and people.
Experiments are conducted at Harbor based on 4 UEs and
the control center running LLaV A against a USRP-based smart
jammer controlled by a laptop with GNU Radio installed,
emitting a 20 MHz Gaussian signal with jamming power up
to 100 mW at 2.4 GHz based on the message transmission
status and received signal strength. Experimental results show
the performance gain in terms of 40.5% less latency, 46.4%
lower UE energy consumption and 10.9% higher inference
accuracy over the benchmark DAS in [6].
The remainder of this paper is organized as follows. We
review the related work in Section II and present the system
model for maritime communications in Section III. Section IV
gives the anti-jamming maritime communications scheme. The
performance analysis including computational complexity and
upper bound is investigated in Section V, followed by imple-
mentation, simulation, experimental results, and conclusion
in Sections VI, VII, VIII, and IX, respectively. The main
contributions are summarized as follows:
• We propose a DRL-based anti-jamming maritime com-
munication scheme that enables UE to optimize uplink
power, channel selection and compression ratio for
transmitting multi-modal data based on the environmental
features extracted by LLM and jamming features to
improve the transmission quality with QoS guarantee.
• We provide the upper bound in terms of latency, UE
energy consumption and inference accuracy under the
given channel gain and number of modalities by analyz-
ing the SE of the maritime anti-jamming game and verify
the convergence of our proposed scheme via simulations.
• We implement our proposed scheme based on Jetson
Orin, camera and BME280 environmental sensor for
transmitting text including temperature, humidity and
pressure as well as images to the control center equipped
with RTX 3060 GPU against the USRP-based smart
jammer in marine environments.
II. R ELATED WORK
UEs such as ships and UA Vs optimize the transmit power
based on channel states and data features to enhance network
security [3], [5], [11] or meet QoS requirement [12], [13],
[14]. For example, the anti-jamming maritime communication
system in [3] optimizes transmit power and transmission
duration based on channel state information to improve system
energy efﬁciency under random jamming. The power alloca-
tion scheme in [5] applies a dueling network to avoid trigger
jammers and reduce UE energy consumption and bit error rate
based on the ship locations, received power and received signal
strength. The UA V-assisted maritime secure communication
in [11] optimizes UA V jamming power and vessel trajectory
using the iterative algorithm to save the jamming cost against
eavesdroppers.
The maritime wireless network in [12] uses successive con-
vex approximation to choose transmit power, bandwidth and
trajectory for uncrewed surface vehicles (USV) to maximize
the minimum expected throughput. The maritime mobile edge
computing scheme in [13] optimizes transmit power, time
slot allocation, data size and UA V trajectory to maximize
the minimum computing capacity. The UA V-USV intragroup
communication architecture in [14] applies multi-agent RL to
optimize transmit power and trajectory based on positions,
channel state and SINR to improve the average throughput
with the shortest path.
The transmission reliability and spectrum utilization can
be enhanced by channel selection in anti-jamming wireless
communications [7], [8] and maritime system [15], [16], [17].
For example, the receiver in [7] optimizes the transmit channel
based on the spectrum waterfall to avoid being jammed and
improve the SINR against comb, sweep, and smart jam-
ming. The DRL-based wireless communication scheme in [8]
improves the number of successful transmissions based on the
channel state against sweep and random jamming. In [15],
the maritime communication scheme uses the lagrangian dual
decomposition method to optimize the subcarrier based on
channel state and ship lanes to improve the ergodic capacity
under high path loss and limited base stations.
The marine IoT system in [16] estimates the channel state
based on the Age of Information to optimize the transmit
channel for sensing data with less packet loss. The RL-based
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 3 页

14678 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
maritime transmission scheme in [17] uses deep Q-network
with a softmax multiple classiﬁer to allocate the channel to
reduce energy consumption and transmission delay. However,
these schemes are vulnerable to smart jamming attacks or
harsh maritime channel due to the lack of jamming and envi-
ronmental features, resulting in link interruption and exposing
marine applications such as vessel trafﬁc monitoring and
resource exploration to further threats such as denial-of-service
attacks to consume network resources.
Data compression ratio is optimized based on channel
states and service requirement under limited communication
resources and large data size [18], [19], [20], [21]. For
example, the online optimization framework in [18] uses the
regularization technique to optimize the image resolution and
model selection to make a trade-off between inference accu-
racy and computational resources. The edge video streaming
system in [19] uses an RL algorithm to optimize the resource
allocation and compression ratio to enhance the weighted
sum of latency, energy consumption and processing accuracy.
In [20], the UE adjusts model parameters at different ratios
based on the UE computational capacity and data volume to
accelerate convergence. The channel-aware adjuster in [21] is
proposed to choose the data compression ratio based on the
channel state information to ensure real-time and high-quality
transmission.
Our previous work in [22] proposed an RL-based anti-
jamming maritime communication scheme to optimize the
uplink power, channel and compression ratio for transmitting
multi-modal data with higher reliability and less overhead.
Compared with the previous work, this paper further exploits
environmental features extracted from multi-modal data and
jamming features to guide policy selection. A feedback recov-
ery mechanism is designed to address delayed or missing
experiences and avoid communication outage under harsh
maritime channel. In addition, our proposed scheme is imple-
mented based on the UE equipped with Jetson Orin, camera
and BME280 sensors and the control center equipped with
RTX 3060 GPU and USRP B210 for feature extraction,
jamming detection and marine object detection. The upper
bound in terms of the latency, UE energy consumption and
inference accuracy is determined by the SE of the maritime
anti-jamming game between the control center and the jammer.
Experimental results at Harbor show the performance gain
against the USRP-based smart jammer over the benchmark.
III. S YSTEM MODEL
A. Task Model
UEs such as ships and UA Vs equipped with tempera-
ture and humidity sensors, microphone, camera, radar and
light detection and ranging to collect multi-modal data X (k)
consisting of U modalities such as text, images and point
clouds to achieve complementary sensing over the marine
communication environment [1]. For example, images contain
rich semantic information but are limited by visibility under
rain, fog and darkness, whereas the radar can provide reliable
distance, speed and azimuth even in poor lighting and adverse
weather conditions.
At time slot k, the massive multi-modal data X (k) is
compressed and transmitted as the uplink information to the
control center, where LLM inference is employed for feature
extraction and object detection. Speciﬁcally, U modalities are
encoded and projected into text embedding space to generate
sequence tokens, which are then concatenated and fed into
the language model such as Vicuna 7B, Vicuna 13B and
Mistral-7B consisting of multi-head self-attention and feed-
forward neural network to generate inference results R(k)
[23], i.e., environmental features α(k) = [α(k)1⩽j⩽C] such as
indoor or outdoor scenario and rainfall indicator and object
typeβ(k) =[β(k)1⩽j⩽D] such as ship, pier and people.
B. Communication Model
UEs moving at speed υ(k) ∈ [0,V ] evaluate the data
size z(k) = [z(k)1⩽j⩽U] of U modalities, and estimate the
channel gain h(k) to the control center located at LC∈ R3
using pilot signals. To reduce the communication overhead,
the raw multi-modal data X (k) is compressed with the ratio
a(k)1 ∈ (0, 1] according to the channel condition and trans-
mitted to the control center with power a(k)2 ∈ [0,P ] on
channel a(k)3 ∈{1, 2,...,F } with bandwidth B. Speciﬁcally,
the compressor consists of a single-layer encoder coupled
with 8-bit quantization, which avoids redundancy without
compromising inference accuracy and saves the storage and
computational resources [24].
The control center running LLM performs the decompres-
sion based on coupled inverse quantization and a single-layer
decoder, evaluates the SINR γ(k), number of received packets
ι(k) and inference accuracy ρ(k) based on the conﬁdence
score and obtains inference resultsR(k). The jamming features
µ(k) =[µ(k)1⩽i⩽J] such as jammed channels and the received
jamming power are estimated via the spectrum sensing tech-
nique, which are fed back to the UE over downlink channel
along with environmental features α(k) as well as inference
and communication performance to guide the anti-jamming
policy selection. In addition, the UE evaluates the latency
τ (k) including the transmission delay τ (k)1 and inference
latency τ (k)2 using timestamps synchronized via the network
time protocol and estimates the energy consumption ξ(k) that
depends on the transmission delay and transmit power.
C. Jamming and Interference Model
Malicious jammers use energy detection technology [25]
to monitor the message transmission status such as idle and
active, and transmit jamming signals to interrupt the legitimate
link between the UE and control center. As a consequence,
both communication reliability and inference accuracy for
multi-modal data are degraded, leading to maritime mission
failure and even posing risks of colliding with nearby UEs.
The smart jammer located at LJ ∈ R3 utilizes the RL
techniques like Q-learning to adjust the jamming policy y(k)
including powery(k)1 ∈ [0,Y ], center frequencyy(k)2 ∈ [f1,f 2]
and bandwidth y(k)3 ∈ [0,B J] based on the message trans-
mission status, the received signal strength and channel gain
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 4 页

LIU et al.: RL-BASED ANTI-JAMMING MARITIME COMMUNICATIONS FOR LLM INFERENCE 14679
g between the jammer and control center to maximize the
expected long-term utility u(k)J with minimal energy cost.
The neighboring UEs such as buoys and vessels j ∈
Z ={1,...,Z } transmit on the same channel as the current
UE, the resulting spectrum conﬂict can be quantiﬁed by the
interference levelI that depends on the transmit power pj and
channel gain hj to control center, i.e.,
I =
∑Z
j=1
pjhj. (1)
D. Problem F ormulation
The anti-jamming transmission policy a including data
compression ratio a1, transmit power a2 and channel a3 is
chosen by each UE from the action set A = (0, 1]× [0,P ]×
{1, 2,...,F } to maximize the weighted sum of inference
accuracy ρ, latency τ, and UE energy consumption ξ with
QoS requirement γ0, i.e.,
max Ea∈A
[∞∑
n=k
ϑ(n−k)
(
ρ(n)−ω0τ (n)−ω1ξ(n)
)]
(2a)
s.t., a1∈ (0, 1] (2b)
a2∈ [0,P ] (2c)
a3∈{ 1, 2,...,F } (2d)
a2h
σ +I +y1g≥γ0, (2e)
where ϑ and σ represent the discount factor and noise power.
The SINR threshold γ0 in (2e) is utilized to ensure the trans-
mission reliability under smart jamming, mutual interference
and harsh maritime channel. The inference accuracy, latency
and energy consumption of each UE vary with the SINR that
depends on the jamming model, the channel gain to the control
center, and the transmission policies of neighboring UEs.
Thus, the optimal transmission policy a∈A in optimization
problem (2) relies on above information, which are seldom
known by current UE accurately and timely under harsh
marine environments.
RL techniques are employed to address the formulated
problem via trial-and-error in the dynamic and harsh marine
environment and enhance the communication and inference
performance since the repeated anti-jamming policy selection
can be modeled as a Markov decision process, in which
the future state such as data size and environmental features
depends only on the current state and transmission policy,
and is independent of prior states and policies. Time index
k is omitted from the notation if no uncertainty occurs. The
notations adopted in this paper are listed in Table I for
convenience of reference.
IV. RL-B ASED ANTI -JAMMING MARITIME
COMMUNICATIONS FOR LLM I NFERENCE
We propose a DRL-based anti-jamming maritime commu-
nication scheme for LLM inference (LAMC) that uses an
actor-critic algorithm to choose the transmit power, channel
and data compression ratio to maximize the weighted sum
of inference accuracy, UE energy consumption and latency
with QoS guarantee. Besides channel state, data size and
TABLE I
SUMMARY OF SYMBOLS AND NOTATIONS
redundancy-reduced observation from neighboring UEs, envi-
ronmental features such as indoor or outdoor scenario and
rainfall indicator extracted by LLM and jamming features are
incorporated in the state formulation to guide the transmission
policy selection. A feedback recovery mechanism based on the
historical anti-jamming experiences is designed to mitigate the
impact of delayed feedback or loss and reduce communication
outage under harsh channel conditions.
At k-th time slot, the UE as the agent obtains the data size
z = [z1⩽j⩽U] ofU modalities, estimates the channel gain h to
control center using pilot signals, and evaluates the latency τ
based on timestamps as well as the energy consumption ξ that
depends on the transmission delay and transmit power. In addi-
tion, environmental features α extracted by LLM, jamming
featuresµ obtained via software-deﬁned radio, the number of
received packets ι, and inference accuracy ρ evaluated based
on the conﬁdence score are fed back from the control center
to the UE over the downlink channel.
The local observation o(k) consists of the data size z of U
modalities, the channel gain h to control center, UE energy
consumptionξ, latency τ, environmental features α, jamming
featuresµ, number of received packets ι and inference accu-
racy ρ, i.e.,
o(k) = [z,h,ξ,τ, α,µ,ι,ρ] . (3)
Due to partial observability in the marine environment,
UE integrates shared observations ˆo(k)j from adjacent UEs
j ∈Z into the state formulation for efﬁcient policy explo-
ration, which introduces information redundancy. Thus, the
attention-based aggregation method is employed to generate
the redundancy-reduced observation ˜o(k) = ∑Zj=1σ(k)j ˆo(k)j ,
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 5 页

14680 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 1. Illustration of the RL-based anti-jamming maritime communication scheme, in which the UE uses an actor-critic algorithm to choose the transmission
policy of multi-modal data a based on state information s such as environmental, jamming and data features.
where the attention weight σ(k)j decreases with the task
similarity, evaluated by Euclidean distance among shared
and local observations [26]. The state s(k) is formulated by
concatenating the local observation o(k) with the redundancy-
reduced observation ˜o(k), i.e.,
s(k) = [z,h,ξ,τ, α,µ,ι,ρ, ˜o]. (4)
As shown in Fig. 1, an actor network P and a critic
networkQ are designed to compress high-dimensional state
space and address the quantization error of data size and
channel gain, thereby improving learning efﬁciency as well
as communication and inference performance under harsh
channel conditions. The actor network P with weights
φ generates policy probability distribution π
(
s(k),a′;φ)
based on the state s(k) and selects the transmission policy
a(k) = [a 1,a 2,a 3] ∈ A, including the data compression
ratio a1 ∈ {m/M|1≤m≤M}, transmit power a2 ∈
{lP/L|1≤l≤L} and channel a3 ∈ {1, 2,...,F }, i.e.,
Pr
(
a(k) =a′) =π(s(k),a′;φ).
The UE compresses multi-modal data X with ratio a1 and
transmits them to the control center with power a2 on channel
a3 against jamming and interference. Upon receiving the
uplink information, the control center running LLM performs
inference to extract environmental features and detect marine
objects such as buoys and ships based on the cross-modal
encoder, multi-head self-attention and feed-forward neural
network. The utility u is evaluated to make tradeoff among
the SINR γ, inference accuracy ρ, latency τ and UE energy
consumption ξ, i.e.,
u(k) =ρ−ω0τ−ω1ξ− ΓI (γ≤γ0), (5)
where ω0 and ω1 represent the importance of latency and UE
energy consumption for the maritime communication applica-
tion, respectively. The penalty factor Γ is used to encourage
policy exploration with SINRγ exceeding a predeﬁned thresh-
old γ0, thereby ensuring transmission quality of multi-modal
data to meet QoS requirements.
Algorithm 1 RL-Based Anti-Jamming Maritime Communica-
tion Scheme for LLM Inference
1: Initialize η, δ, ϑ,φ,ϕ, and ξ(0) =τ (0) =ρ(0) = 0
2: fork = 1, 2,...,K do
3: Evaluate the data size z of each modality and the
channel gain h and obtain the shared observation ˜o
4: Formulates(k) via (4)
5: Choosea(k) based on π(s(k),a′;φ)
6: Compress multi-modal dataX with ratioa1 and trans-
mit them to the control center running LLM with power
a2 on channel a3
7: Obtain inference accuracy ρ, inference results R and
jamming features µ
8: Estimate the latency τ and UE energy consumption ξ
9: Evaluateu(k) via (5)
10: B←B ⋃{s(k),a(k),u (k),s(k+1)}
11: if|B|≥ D then
12: Randomly sample D experiencesD fromB
13: Updateφ andϕ via (7)-(8)
14: end if
15: end for
The experience replay mechanism is introduced to
update network weights and improve sample efﬁciency.
Speciﬁcally, UE formulates the transmission experience{
s(k),a(k),u (k),s(k+1)} according to current states(k), trans-
mission policy a(k), utility u(k), and next state s(k+1)
and stores them into the replay buffer B, i.e., B ←
B⋃{s(k),a(k),u (k),s(k+1)}. During weights update, D
experiences are randomly sampled to form a mini-batch D.
The delayed or missing feedback such as communication
and inference performance under harsh marine environments
caused by sea surface reﬂections and weather conditions,
introduces bias in value estimation during transmission policy
learning. The historical anti-jamming experiences are used
to minimize long-term estimation errors and avoid selecting
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 6 页

LIU et al.: RL-BASED ANTI-JAMMING MARITIME COMMUNICATIONS FOR LLM INFERENCE 14681
transmission policies that result in communication outage [27].
More speciﬁcally, if the feedback is delayed or partial missing
at time slot k, the utility u(k) is estimated based on the
weighted average of the utility from the previous T time slots
along with the correction term χ, i.e.,
u(k) = 1T
T∑
m=1
u(k−m)− ˆu(k−m) +χ(k−m)u(k−m). (6)
In addition, an entropy term log (π(·)) is introduced into the
objective function to balance utility maximization and policy
exploration with a temperature parameter δ in the marine
environment. Therefore, the weights φ are updated via policy
gradient with the learning rate η, i.e.,
L(φ)= 1D
D∑
d=1
(
δ log
(
π
(
s(d),a(d);φ))−Q(s(d), ¯a;ϕ)). (7)
The weights ϕ of the critic network Q are updated by
minimizing the mean squared error with the discount factor
ϑ, i.e.,
L (ϕ) = 1D
D∑
d=1
(
u(d)−Q(s(d),a(d);ϕ)
+ϑ
(
Q
(
s(d+1), ¯a;ϕ)−δ log(π(s(d+1), ¯a;φ))))2.
(8)
V. P ERFORMANCE ANALYSIS
We provide the upper bound in terms of latency, UE energy
consumption and inference accuracy by analyzing the SE of
the maritime anti-jamming game G between N UEs and the
jammer via backward induction method [28]. In addition, we
investigate the computational complexity of the proposed anti-
jamming maritime communication scheme.
A. Game Model
The jammer J as the leader chooses the jamming power
y(k)∈ [0,P J] for sending jamming signals to reduce the SINR
γi of UE i∈N ={1, 2,...,N } that reﬂects the transmission
quality under maritime channel, jamming and interference with
minimal energy cost, leading to the failure of LLM inference.
The jammer utility is given as
uJ =
N∑
i=1
1
γi
−ϖ0y. (9)
N UEs N as the follower select the transmission strat-
egy A = [a 1,a2,a3] ∈ AN including compression ratio
a1 = [ai,1]i∈N ∈ (0, 1]N , transmit power a2 = [ai,2]i∈N ∈
[0,P ]N and channel a3 = [ai,3]i∈N ∈ {1,...,F }N . The
zi = ∑Uj=1 zi,j-byte data with U modalities from UE i are
transmitted over bandwidth B to the control center of Ω
computational capacity, where LLM inference requiring Λ
ﬂoating-point operations. The overall utility ¯u as a weighed
sum of inference accuracyρi, latencyτi consisting of transmis-
sion delay τi,1 and inference latency τi,2, and transmit power
ai,2 reﬂecting UE energy consumption ξi, aggregated over all
N UEs, i.e.,
¯u =
N∑
i=1
ρi−ϖ1zi
( ai,1
B log2 (1 +γi) + ΛΩ)−ϖ2ai,2. (10)
Thus, maritime anti-jamming game is formulated as
G =
{
{N,J} ,
{
AN,Y},{¯u,u J}}. (11)
The SE strategies (A∗,y∗), from which no player can
unilaterally improve its utility, are given by deﬁnition as
y∗ = arg max
y∈Y
uJ
(
A,y
)
, (12a)
A∗ = arg max
A∈AN
¯u(A,y∗). (12b)
In particular, the inference accuracy ρi increases linearly
with data compression ratio ai,1 and in an exponential satura-
tion manner with SINR γi, i.e.,
ρi =Lai,1 (1− exp (−γi)), (13)
where L∈ (0, 1] represents the maximum accuracy.
Theorem 1: The performance bound of our proposed LAMC
scheme for UE i is given by
ˆτi = ziB log2 (1 + ˆγi) + ΛziΩ (14a)
ˆξi = P ziB log2 (1 + ˆγi) (14b)
ˆρi =L−L exp (−ˆγi) (14c)
where
ˆγi = Ph iσ +PJg, (15)
if
ˆγ2i exp (−ˆγi)≤ ϖ1ziLB ≤ ˆγi (1− exp (−ˆγi)) (16)
g≥ϖ0P
∑N
i=1
hi. (17)
Proof: See appendix A. □
Remark 1: UE i send zi-byte data with U modalities at
the maximum power P over channel i to the control center
for LLM inference. The smart jammer emits the jamming
signal with the maximum power PJ to interrupt the ongo-
ing maritime communication link for maximum disruption.
Simulation results based on 7 UEs and a random jammer in
Fig. 2 indicate that the latency, UE energy consumption and
inference accuracy converge to the performance bound given
by (14) after 600 time slots if the data size zi and channel
gain between the jammer and the control center g meet the
conditions given by (16)-(17).
B. Computational Complexity
The actor network P has ε = 2 (U +C +J + 5)-
dimensional input depending on the number of modalities as
well as environmental and jamming features, c1 andc2 ReLU-
activated nodes in hidden layers, andMLF output determined
by compression ratio level M, transmit power level L, and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 7 页

14682 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 2. Performance of anti-jamming maritime communications with 7 UEs
and a random jammer.
number of channels F . For transmission policy selection, ϵA,F
multiplications in forward propagation are performed, i.e.,
ϵA,F =εc1 + (c1 + 1)c2 +MLF (c2 + 1). (18)
Updating weights φ involvesϵA,F and ϵA,B multiplications in
forward and backward propagation by actor network P and
ϵC,F multiplications by critic network Q with ε +MLF , d1,
d2 and 1 nodes per layer for Q-value estimation, given by
ϵA,B = 2εc1 + 2(c1 + 1)c2 + 3MLF (c2 + 1) (19)
ϵC,F = (ε +MLF )d1 + (d1 + 1)d2 +d2 + 1. (20)
To update weightsϕ, the actor networkP performsϵA,F mul-
tiplications in forward propagation, while the critic networkQ
requiresϵC,F andϵC,B multiplications in forward and backward
propagation, respectively.
ϵC,B = 2 (ε+MLF )d1 + 2(d1 + 1)d2 + 3 (d2 + 1). (21)
The total number of multiplications denoted by ϵT are
performed, given by
ϵT = (2D + 1)ϵA,F + 2DϵC,F +DϵA,B +DϵC,B. (22)
Fig. 3. Anti-jamming maritime communication system implementation, in
which UEs equipped with Jetson Orin, camera and BME280 sensor transmit
multi-modal data to the control center for LLM inference and jamming
detection with USRP.
Fig. 4. Frame format of maritime communication protocol, in which each
UE transmits the compressed multi-modal data and receives jamming features
and inference results over the downlink channel.
Theorem 1: The computational complexity of the proposed
LAMC is given by O (DMLFK ).
Proof: See Appendix B. □
Remark 2: The computational complexity of LAMC Υ
increases linearly with data compression ratio level M, trans-
mit power level L and the number of channels F .
VI. I MPLEMENTATION
Our proposed scheme is implemented based on UEs
equipped with the computing unit, i.e., NVIDIA Jetson Orin,
BME280 sensor, camera and adapter transmitting multi-modal
data such as text and images to the control center equipped
with RTX 3060 GPU, supporting LLM inference including
environmental feature extraction and marine object detection,
as shown in Fig. 3.
Jetson Orin equipped with Cortex-A78 CPU and Ampere
architecture is deployed on UEs such as ships or UA Vs to
collect images and text including temperature, humidity and
pressure from the camera and BME280 sensor via USB and
I2C interface and optimize the data compression ratio, power
and channel via transmission policy selection module. The
multi-modal data are compressed, Base64-encoded, packed in
JSON format, encapsulated as the frame body within data
frames in Fig. 4 and transmitted to the control center via a
UDP socket using the Wi-Fi signal over a 10 MHz channel at
2.4 GHz.
Upon receiving the uplink information, the control center
equipped with RTX 3060 GPU, Ubuntu 20.04.6 operating
system, USRP Hardware Driver (UHD) and GNU Radio
performs data decompression and unpacking as well as gener-
ates environmental features, marine objects and performance
metrics based on the LLaV A with 7.3 billion parameters, INT4
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 8 页

LIU et al.: RL-BASED ANTI-JAMMING MARITIME COMMUNICATIONS FOR LLM INFERENCE 14683
Fig. 5. GUI of the anti-jamming maritime communication system.
Fig. 6. Initial topology setting of maritime communications against a smart
jammer located at (18, 2, 0) m.
quantization and 2.3 TFLOPs per inference [2]. In parallel,
USRP B210 uses the spectrum sensing technique to obtain
jamming features such as jammed channels and received
jamming power.
The environmental features, jamming features, number of
received packets and inference accuracy are sent as downlink
information in Fig. 4 via a TCP socket through the feedback
router and used for state formulation after being received by a
USB-connected external wireless adapter, thereby guiding the
policy selection.
In the RL-based scheme, for 2 modalities, 1 environmental
feature, and 1 jamming feature, the actor network has a
18-dimensional input, two hidden layers with 128 ReLU-
activated neurons, and a 125-dimensional output, while the
critic network has 143, 128, 128, and 1 nodes, respectively.
The weights φ and ϕ are updated with minibatch size 32,
learning rate 10−4, discount factor ϑ = 0.7 and temperature
parameter δ decaying from 1 to 0.1 after 100 time slots.
As shown in Fig. 5, the PyQT-based GUI displayed on
the laptop provides an interactive human-machine interface,
which controls the start and end of data transmission, displays
multi-modal data, UEs transmission policy and LLM inference
results, and supports real-time visualization and storage of
performance metrics for ofﬂine analysis.
VII. S IMULATION RESULTS
Simulations were performed on a Windows-based laptop
equipped with an Intel i9-13900 CPU, an NVIDIA GeForce
RTX 3060 GPU, and 512 GB of memory, using MATLAB
R2024b and Python 3.12 with PyTorch 2.7.1 and CUDA 12.8
to evaluate the performance gain of the proposed anti-jamming
maritime communications scheme over the benchmark DAS in
TABLE II
SIMULATION PARAMETERS
[6]. As shown in Fig. 6, each of 7 UEs moving with the random
walk model and speed ranging from 5 to 10 m/s chooses the
data compression ratio {0.2, 0.4, 0.6, 0.8, 1}, transmit power
up to 100 mW quantized into 5 levels and one of 10 channels
with the bandwidth of 10 MHz at 2.4 GHz for transmitting
200-KB text and camera images from WaterScenes dataset [9]
to the control center located at (3, 18, 2) m [29].
Upon receiving multi-modal data, the control center runs
LLaV A[2] that integrates the pre-trained CLIP visual encoder
ViT-L/14 and the Vicuna language model to extract environ-
mental features and detect marine objects such as boats and
people. In addition, the communication overhead introduced
by exchanging observations, including data, jamming and
environmental features as well as performance metrics, mainly
depends on the observation data size and the number of neigh-
boring UEs. Under the considered settings, the observation
exchange with 6 UEs yields about 162 bytes per time slot
and thus the resulting latency and energy consumption are
negligible compared with the multi-modal transmission.
The Q-learning-based smart jammer located at (18, 2, 0)
m emits the 20 MHz bandwidth Gaussian signal with the
power{20j|0≤j≤ 5} mW at 2.4 GHz based on message
transmission status and channel gain to the control center
for maximum disruption with minimal energy cost. The mar-
itime communication link operating in 2–20 GHz consists of
line-of-sight propagation, rough sea surface reﬂections and
over-the-horizon paths, affected by channel fading rf and
divergence ∆ due to wave ﬂuctuations and earth curvature.
The path loss Lp (dB) between the ship and control center at
a distance of d (m) is modeled as [10]
Lp = 20 log
(
λ
⏐⏐1 +rf∆rrejkl 1 +rdejkl 2⏐⏐
4πd
)
, (23)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 9 页

14684 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Performance of anti-jamming maritime communications with the
topology changing every 1000 time slots shown in Fig. 6.
where k = 2π/λ is the wavenumber. rr and rd are reﬂection
coefﬁcients of the rough sea surface and evaporation duct,
andl1 andl2 represent the differences in path length between
the two reﬂection paths and the direct path. In addition, the
channel gain between the jammer/UA V and control center
is modeled by the log-distance path loss model. Simulation
parameter settings are summarized in Table II.
The performance gain of our proposed LAMC outperforms
benchmark DAS in [6] with higher communication reliability
and inference accuracy against jamming as shown in Fig. 7.
Fig. 8. Average performance of LLM-aided anti-jamming maritime commu-
nications with different UE sizes over 50 runs.
For example, LAMC exceeds DAS with a 20.3% decrease
in latency, a 54.7% reduction in UE energy consumption
and a 11.2% increase in inference accuracy at the 1000-th
time slot due to the consideration of jamming features and
environmental features extracted by LLM and the feedback
recovery mechanism designed for harsh channel conditions.
The transmission and inference performance averaged over
50 runs consisting of 2000 time slots demonstrates the per-
formance gain of the proposed LAMC with varying numbers
of UEs as shown in Fig. 8. For example, LAMC reduces
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 10 页

LIU et al.: RL-BASED ANTI-JAMMING MARITIME COMMUNICATIONS FOR LLM INFERENCE 14685
Fig. 9. Experimental setting of the maritime communication scheme at
Harbor, in which 4 UEs transmit text and images against a USRP-based smart
jammer.
Fig. 10. Convergence performance of the anti-jamming maritime communica-
tions of the proposed LAMC versus learning rate and discount factor averaged
over 50 runs.
latency by 19.8% and UE energy consumption by 38.4%,
and enhances inference accuracy by 18.1% for the 20 UEs
over the benchmark DAS [6]. As the UE size increases from
5 to 25, the performance gain regarding the latency and
UE energy consumption of our proposed LAMC increases
from 8.4% to 25.9% and from 32.2% to 39.7%, respectively,
because the shared observations such as data, environmental
and jamming features from adjacent UEs are incorporated in
state formulation under a partial observable environment while
avoiding information redundancy.
VIII. E XPERIMENTAL RESULTS
Experiments were conducted at Harbor to evaluate the
performance gain against the USRP-based smart jammer with
Fig. 11. Performance of the anti-jamming maritime communication with
topology changing every 1000 time slots as shown in Fig. 9.
topology as shown in Fig. 9. Each UE processes 200-KB text
and camera-captured images with 5 data compression ratios
ranging from 0 to 1 and transmits them to the control center
according to IEEE 802.11n with the power quantiﬁed to ﬁve
levels up to 100 mW and 10 channels each with the bandwidth
of 10 MHz at 2.4 GHz.
Upon receiving multi-modal data, the control center running
LLaV A[2] understands scenes and generates inference results.
The extracted environmental features, measured jamming fea-
tures, and performance metrics are fed back to the UE over
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 11 页

14686 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 12. Inference results generated by the LLM running at control center
based on the received image at 1000 time slot.
2.472 GHz to guide the RL-based transmission policy selec-
tion. A smart jammer is implemented on USRP B210 and a
laptop equipped with Ubuntu 18.04, GNU Radio and UHD,
emits the 20 MHz bandwidth Gaussian signal to the control
center with up to 100 mW power at the center frequency of
2.4 GHz to degrade the transmission reliability.
As shown in Fig. 10, the convergence performance of our
proposed LAMC scheme averaged over 50 runs under the
topology in Fig. 9 is evaluated for different hyperparameters
such as learning rates and discount factors. Speciﬁcally, the
convergence performance with a discount factor ϑ ranging
from 0.5 to 0.9 indicates that ϑ = 0 .7 makes a tradeoff
between exploration and exploitation during learning. In addi-
tion, the learning rate η = 0.01 in the Adam optimizer for
network weights update yields the maximum utility for trans-
mitting temperature, humidity and pressure as well as images
against jamming and interference in the marine environment.
Experimental results shown in Fig. 11 also verify the
performance gain in terms of the latency, UE energy consump-
tion and inference accuracy against the USRP-based smart
jammer. For example, our proposed LAMC decreases latency
by 40.5%, reduces UE energy consumption by 46.4%, and
improves inference accuracy by 10.9% over the benchmark
[6] after 1000 time slots. The reason is that the DRL-based
anti-jamming scheme chooses the data compression ratio,
transmit power and channel for transmitting multi-modal data
based on the environmental features extracted by LLM and
jamming features obtained via software-deﬁned radio and
recovers the delayed or missing feedback under harsh channel
conditions, thereby improving the transmission reliability with
less overhead and supporting the marine object detection. In
addition, the inference results generated by the LLM based
on the received images as shown in Fig. 12 demonstrate that
the proposed LAMC has higher inference accuracy for marine
object detection due to the better transmission quality of multi-
modal data in the marine environment.
IX. C ONCLUSION
In this paper, we have proposed an RL-based maritime
communication scheme for LLM inference that chooses the
data compression ratio, transmit power and channel against
jamming and interference. The upper bound derived from
the Stackelberg equilibrium shows that both latency and UE
energy consumption grow linearly with the number of modal-
ities, while inference accuracy exhibits exponential saturation
with channel gains. Our proposed scheme was implemented
based on Jetson Orin, camera, BME280 sensors and RTX 3060
GPU to support reliable transmission of text and images and
marine object detection. Experimental results based on 4 UEs
transmitting 200-KB temperature, humidity and pressure as
well as images to the control center verify the performance
gain over the benchmark DAS against the USRP-based smart
jammer, e.g., 40.5% less latency, 46.4% lower UE energy
consumption and 10.9% higher inference accuracy.
APPENDIX A
PROOF OF THEOREM 1
Proof: By (9),∀A∈ (0, 1]N× [0,P ]N×{1,...,F }N and
∀y∈ [0,P J], we have
uJ (A,y ) =
N∑
i=1
σ +yg +Ii
pihi
−ϖ0y. (24)
By (17) and (24), we have
∂uJ (A,y )
∂y =
N∑
i=1
g
Ph i
−ϖ0≥ 0. (25)
Thus, by (25), we have
uJ (A,P J)≥uJ (A,y ). (26)
By (10), (13), (16) and (26), ∀A ∈ (0, 1]N× [0,P ]N×
{1,...,F }N , and N≤F , we have
¯u
(
A∗,P J) =LN−L N∑
i=1
exp
(
− Ph i
σ +PJg
)
− ϖ1ziai,1
BPh i
(σ +PJg)−ϖ1zi
Λ
Ω−ϖ2P
≥L
N∑
i=1
ai,1
(
1− exp
(
− ai,2hi
σ +PJg +Ii
))
− ϖ1ziai,1
Bai,2hi
(σ +PJg +Ii)−ϖ1zi
Λ
Ω−ϖ2ai,2
= ¯u
(
A,P J
)
, (27)
where A∗ = [1N, P· 1N, [1,··· ,N ]]. Thus, by (26) and
(27), (A∗,P J) is an SE of G and the upper bound of LAMC
is given by (14).
APPENDIX B
PROOF OF THEOREM 2
Proof: According to [30], the number of nodes c1 and
c2 depend on the transmission policy dimension MLF and
learning steps K, i.e.,
c1 =
√
(MLF + 2)K + 2
√
K
MLF + 2 (28)
c2 =MLF
√
K
MLF + 2. (29)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 12 页

LIU et al.: RL-BASED ANTI-JAMMING MARITIME COMMUNICATIONS FOR LLM INFERENCE 14687
Similarly, the number of nodes of the critic network are given
by d1 =
√
3K + 2
√
K/3 and d2 =
√
K/3.
By (18)-(21), we have
Υ =O
(
(4D + 1)εc1 + (4D + 1) (c1 + 1)c2
+MLF (5D + 1) (c2 + 1) + 4D (ε +MLF )d1
+ 4D (d1 + 1)d2 + 5D (d2 + 1)
)
(30)
=O
(
Dε
√
MLFK +DMLF
√
MLFK +DMLFK
)
(31)
=O(DMLFK ). (32)
where (31) is obtained by (28) and (29), and (32) is obtained
as K≫MLF .
REFERENCES
[1] Y . Qiao, J. Yin, W. Wang, F. Duarte, J. Yang, and C. Ratti, “Survey of
deep learning for autonomous surface vehicles in marine environments,”
IEEE Trans. Intell. Transp. Syst., vol. 24, no. 4, pp. 3678–3701, Apr.
2023.
[2] H. Liu, C. Li, Q. Wu, and Y . J. Lee, “Visual instruction tuning,” in Proc.
Adv. Neural Inf. Process. Syst., vol. 36, New Orleans, LA, USA, Dec.
2023, pp. 34892–34916.
[3] H. Yang, K. Lin, L. Xiao, Y . Zhao, Z. Xiong, and Z. Han, “Energy
harvesting UA V-RIS-assisted maritime communications based on deep
reinforcement learning against jamming,” IEEE Trans. Wireless Com-
mun., vol. 23, no. 8, pp. 9854–9868, Aug. 2024.
[4] C. Zeng, J.-B. Wang, C. Ding, M. Lin, and J. Wang, “MIMO unmanned
surface vessels enabled maritime wireless network coexisting with
satellite network: Beamforming and trajectory design,” IEEE Trans.
Commun., vol. 71, no. 1, pp. 83–100, Jan. 2023.
[5] C. Liu, Y . Zhang, G. Niu, L. Jia, L. Xiao, and J. Luan, “Towards
reinforcement learning in UA V relay for anti-jamming maritime
communications,” Digit. Commun. Netw., vol. 9, no. 6, pp. 1477–1485,
Dec. 2023.
[6] X. Li, J. Chen, X. Ling, and T. Wu, “Deep reinforcement learning-
based anti-jamming algorithm using dual action network,” IEEE Trans.
Wireless Commun., vol. 22, no. 7, pp. 4625–4637, Jul. 2023.
[7] Y . Li et al., “Dynamic spectrum anti-jamming access with fast conver-
gence: A labeled deep reinforcement learning approach,” IEEE Trans.
Inf. F orensics Security, vol. 18, pp. 5447–5458, 2023.
[8] S. B. Janiar and P. Wang, “Intelligent anti-jamming based on deep
reinforcement learning and transfer learning,” IEEE Trans. V eh. Technol.,
vol. 73, no. 6, pp. 8825–8834, Jun. 2024.
[9] S. Yao et al., “WaterScenes: A multi-task 4D radar-camera fusion dataset
and benchmarks for autonomous driving on water surfaces,” IEEE Trans.
Intell. Transp. Syst., vol. 25, no. 11, pp. 16584–16598, Nov. 2024.
[10] Y . Wang, T. Zhou, W. Feng, T. Xu, and H. Hu, “When maritime wireless
communications meet evaporation ducts: A three-ray path loss modeling
perspective,” IEEE Wireless Commun. Lett., vol. 14, no. 2, pp. 470–474,
Feb. 2025.
[11] L. Wu et al., “UA V-assisted maritime legitimate surveillance: Joint
trajectory design and power allocation,” IEEE Trans. V eh. Technol.,
vol. 72, no. 10, pp. 13701–13705, Oct. 2023.
[12] C. Zeng, J.-B. Wang, C. Ding, H. Zhang, M. Lin, and J. Cheng, “Joint
optimization of trajectory and communication resource allocation for
unmanned surface vehicle enabled maritime wireless networks,” IEEE
Trans. Commun., vol. 69, no. 12, pp. 8100–8115, Dec. 2021.
[13] F. Lu et al., “Resource and trajectory optimization for UA V-relay-
assisted secure maritime MEC,” IEEE Trans. Commun., vol. 72, no. 3,
pp. 1641–1652, Mar. 2024.
[14] T. Yang, Z. Jiang, R. Sun, N. Cheng, and H. Feng, “Maritime search and
rescue based on group mobile computing for unmanned aerial vehicles
and unmanned surface vehicles,” IEEE Trans. Ind. Informat., vol. 16,
no. 12, pp. 7700–7708, Dec. 2020.
[15] T. Wei, W. Feng, J. Wang, N. Ge, and J. Lu, “Exploiting the shipping
lane information for energy-efﬁcient maritime communications,” IEEE
Trans. V eh. Technol., vol. 68, no. 7, pp. 7204–7208, Jul. 2019.
[16] L. Lyu et al., “AoI-aware co-design of cooperative transmission and state
estimation for marine IoT systems,” IEEE Internet Things J., vol. 8,
no. 10, pp. 7889–7901, May 2021.
[17] T. Yang, J. Li, H. Feng, N. Cheng, and W. Guan, “A novel transmission
scheduling based on deep reinforcement learning in software-deﬁned
maritime communication networks,” IEEE Trans. Cognit. Commun.
Netw., vol. 5, no. 4, pp. 1155–1166, Dec. 2019.
[18] K. Zhao et al., “EdgeAdaptor: Online conﬁguration adaption, model
selection and resource provisioning for edge DNN inference serving at
scale,” IEEE Trans. Mobile Comput., vol. 22, no. 10, pp. 5870–5886,
Oct. 2023.
[19] S. Yuan et al., “Adaptive incentive and resource allocation for
blockchain-supported edge video streaming systems: A cooperative
learning approach,” IEEE Trans. Mobile Comput., vol. 24, no. 2,
pp. 539–556, Feb. 2025.
[20] R. Lu et al., “Data-aware gradient compression for FL in
communication-constrained mobile computing,” IEEE Trans. Mobile
Comput., vol. 24, no. 4, pp. 2755–2768, Apr. 2025.
[21] Y . Zhang et al., “SmartCooper: Vehicular collaborative perception with
adaptive fusion and judger mechanism,” in Proc. IEEE Int. Conf. Robot.
Autom. (ICRA), May 2024, pp. 4450–4456.
[22] H. Liu, W. Lin, L. Xiao, P. Zhang, H. Chen, and Z. Lv, “RL-based
anti-jamming maritime communications for multi-modal perception,” in
Proc. IEEE 102nd V eh. Technol. Conf., Oct. 2025, pp. 1–5.
[23] Y . Cao et al., “Survey on large language model-enhanced reinforcement
learning: Concept, taxonomy, and methods,” IEEE Trans. Neural Netw.
Learn. Syst., vol. 36, no. 6, pp. 9737–9757, Jun. 2025.
[24] Z. Hao, G. Xu, Y . Luo, H. Hu, J. An, and S. Mao, “Multi-agent
collaborative inference via DNN decoupling: Intermediate feature com-
pression and edge learning,” IEEE Trans. Mobile Comput., vol. 22,
no. 10, pp. 6041–6055, Oct. 2023.
[25] N. Van Huynh, D. T. Hoang, D. N. Nguyen, and E. Dutkiewicz,
“DeepFake: Deep dueling-based deception strategy to defeat reac-
tive jammers,” IEEE Trans. Wireless Commun., vol. 20, no. 10,
pp. 6898–6914, Oct. 2021.
[26] Z. Lv, L. Xiao, Y . Du, Y . Zhu, S. Han, and Y .-J. Liu, “Efﬁcient commu-
nications in multi-agent reinforcement learning for mobile applications,”
IEEE Trans. Wireless Commun., vol. 23, no. 9, pp. 12440–12454, Sep.
2024.
[27] Y . Yu, S. C. Liew, and T. Wang, “Multi-agent deep reinforcement
learning multiple access for heterogeneous wireless networks with
imperfect channels,” IEEE Trans. Mobile Comput., vol. 21, no. 10,
pp. 3718–3730, Oct. 2022.
[28] A. Garnaev, A. Petropulu, W. Trappe, and H. V . Poor, “An anti-jamming
multiple access channel game using latency as metric,” IEEE Wireless
Commun. Lett., vol. 11, no. 9, pp. 1800–1804, Sep. 2022.
[29] H. Zeng et al., “USV ﬂeet-assisted collaborative computation ofﬂoading
for smart maritime services: An energy-efﬁcient design,” IEEE Trans.
V eh. Technol., vol. 73, no. 10, pp. 14718–14733, Oct. 2024.
[30] G.-B. Huang, “Learning capability and storage capacity of two-hidden-
layer feedforward networks,” IEEE Trans. Neural Netw., vol. 14, no. 2,
pp. 274–281, Mar. 2003.
Huanhuan Liu (Graduate Student Member, IEEE)
received the B.S. degree in communication engi-
neering from Shenyang University of Technology
in 2020 and the M.S. degree in communica-
tion engineering from Xidian University in 2023.
She is currently pursuing the Ph.D. degree with
the Department of Informatics and Communica-
tion Engineering, Xiamen University. Her research
interests include network security and wireless
communications.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.

## PDF 第 13 页

14688 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Liang Xiao (Fellow, IEEE) received the B.S. degree
in communication engineering from Nanjing Uni-
versity of Posts and Telecommunications, China,
in 2000, the M.S. degree in electrical engineering
from Tsinghua University, China, in 2003, and the
Ph.D. degree in electrical engineering from Rutgers
University, NJ, USA, in 2009. She was a Visit-
ing Professor with Princeton University, Virginia
Tech, and the University of Maryland, College Park.
She is currently a Professor with the Department
of Informatics and Communication Engineering,
Xiamen University, Xiamen, China. She was a recipient of the Best Paper
Award for 2016 INFOCOM Big Security WS and 2017 ICC. She has
served as an Associate Editor for IEEE T RANSACTIONS ON INFORMATION
FORENSICS AND SECURITY and a Guest Editor for IEEE J OURNAL OF
SELECTED TOPICS IN SIGNAL PROCESSING .
Weiqi Lin received the B.S. degree in electronic
information engineering from Dalian Maritime
University, Dalian, China, in 2024. He is currently
pursuing the M.S. degree with the Depart-
ment of Informatics and Communication Engi-
neering, Xiamen University. His research interests
include wireless communications and reinforcement
learning.
Pengli Zhang received the B.S. degree in commu-
nication engineering from Anhui Normal University,
Wuhu, China, in 2023. She is currently pursuing the
Ph.D. degree with the Department of Informatics and
Communication Engineering, Xiamen University.
Her research interests include wireless communica-
tions, smart grids, and reinforcement learning.
Haoyu Chen (Graduate Student Member, IEEE)
received the B.Eng. and M.Sc. degrees from the
Department of Electronic Information Engineering,
Fuzhou University, Fujian, China, in 2020 and 2023,
respectively. He is currently pursuing the Ph.D.
degree with the Institute of Artiﬁcial Intelligence,
Xiamen University. His research interests include
wireless communications, smart grids, and reinforce-
ment learning.
Zefang Lv (Member, IEEE) received the B.S. degree
in statistics from Shandong University in 2016, the
M.S. degree in applied statistics from North China
Electric Power University in 2020, and the Ph.D.
degree in communication and information systems
from Xiamen University in 2024. She is currently
a Post-Doctoral Researcher with the Institute of
Space Internet, Fudan University, Shanghai. Her
research interests include wireless communications,
UA V communications, and reinforcement learning.
Manhao Jiang received the B.S. degree in electronic
information engineering from Fuzhou University,
Quanzhou, China, in 2025. He is currently pursuing
the M.S. degree with the Department of Infor-
matics and Communication Engineering, Xiamen
University. His research interests include wire-
less communications and multi-agent reinforcement
learning.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 22,2026 at 02:09:16 UTC from IEEE Xplore.  Restrictions apply.
