---
type: literature-fulltext
title: "You Only Transmit Once: Unified Generation and Comprehension for Efficient Semantic Communication"
zotero_key: "RBIPFD3L"
pdf_key: "TIMMUKP4"
doi: "10.1109/JSAC.2026.3655643"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/You Only Transmit Once- Unified Generation and Comprehension for Efficient Semantic Communication.md"
fulltext_path: "03fulltext/备选讲组会论文/RBIPFD3L.md"
zotero_item: "zotero://select/library/items/RBIPFD3L"
zotero_pdf: "zotero://open-pdf/library/items/TIMMUKP4"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# You Only Transmit Once: Unified Generation and Comprehension for Efficient Semantic Communication

> PDF 原文逐页文本抽取；来源文件 SHA-256：`cab4905a909e25dfec4b22fe431d5caea6fbddd0f78fbe1ef12b242c245e3ed7`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026 3349
You Only Transmit Once: Uniﬁed Generation and
Comprehension for Efﬁcient Semantic
Communication
Li Yao
 , Yuan Wei
 , Yuning Zhou
 , Ziwei Li
 , Nan Chi
 , Senior Member , IEEE,
and Kai-Kit Wong
 , Fellow, IEEE
Abstract—Semantic communication (SC) systems face the
challenge of completing generation and comprehension tasks
simultaneously under high data compression. To address this
issue, this paper proposes a You Only Transmit Once (YOTO)
SC system, which achieves efﬁcient performance by syner-
gistically integrating images and texts. For generation tasks,
YOTO integrates a multiple granularity visual encoder, a digital
modulation autoencoder, and a conditional probability-based
visual decoder. These parts collectively ensure high-ﬁdelity image
reconstruction and accurate object detection. Meanwhile, YOTO
utilizes the Source Feature Selection (SFS) and Channel Feature
Selection (CFS) module for joint compression of source and
channel coding data. To achieve a globally optimal compression,
the Libra module dynamically adjusts feature retention ratios
between CFS and SFS. Regarding comprehension tasks, YOTO
eliminates the need for additional text data transmission by
simply replacing the visual decoder with a Multimodal Language
Model that incorporates the visual causality and bridging module.
This architecture effectively converts demodulated visual data
into descriptive captions while enabling emotion-aware text
generation through prompt engineering. Extensive simulation
experiments demonstrate the superior performance of YOTO
in diverse channel conditions. In generation tasks, the YOTO
system achieves PSNR values exceeding 30 dB both in the A WGN
and Rayleigh fading channels when the SNR is 6 dB. While in
comprehension tasks, it attains sentence similarity scores above
0.83 at 10 dB SNR. YOTO system effectively resolves cross-
modal semantic disparities, thereby paving the way for future
developments of SC systems that can balance generation and
comprehension tasks.
Index Terms—Deep learning, multimodal semantic com-
munication, multimodal language model, generative artiﬁcial
intelligence.
Received 18 March 2025; revised 11 December 2025; accepted 13 January
2026. Date of publication 19 January 2026; date of current version 24 February
2026. This work was supported in part by the National Key Research and
Development Program of China under Grant 2023YFB2804701 and in part
by the Natural Science Foundation of China Project under Grant 62525102.
(Corresponding authors: Ziwei Li; Nan Chi.)
Li Yao and Yuning Zhou are with the Key Laboratory for Infor-
mation Science of Electromagnetic Waves (MoE), College of Future
Information Technology, Fudan University, Shanghai 200433, China, and
also with Shanghai Innovation Institute, Shanghai 200231, China (e-mail:
23110720089@m.fudan.edu.cn).
Yuan Wei, Ziwei Li, and Nan Chi are with the Key Laboratory for
Information Science of Electromagnetic Waves (MoE), College of Future
Information Technology, Fudan University, Shanghai 200433, China (e-mail:
lizw@fudan.edu.cn; nanchi@fudan.edu.cn).
Kai-Kit Wong is with the Department of Electronic and Electrical Engi-
neering, University College London, WC1E 7JE London, U.K. (e-mail:
kai-kit.wong@ucl.ac.uk).
Digital Object Identiﬁer 10.1109/JSAC.2026.3655643
I. I NTRODUCTION
T
RADITIONAL wireless communication relies on bit-
level data transmission, which often fails to prioritize
critical information over redundant data in scenarios with
limited bandwidth or poor channel conditions. This inef-
ﬁciency leads to the allocation of resources to low-value
information, while essential data is transmitted unreliably [1].
Semantic Communication (SC) addresses these limitations by
focusing on the transmission of key semantic information [2],
[3], [4]. Generative Semantic Communication (GSC) further
advances this paradigm by integrating semantic extraction
from unimodal or multimodal data with generative models,
enabling the generation of high-quality data at the receiver
[5], [6]. At the transmitter, critical semantic information
is compressed into latent features, while at the receiver,
generative networks reconstruct semantically consistent out-
puts or produce enriched content by incorporating contextual
information.
A. Background and Related Work
In bandwidth-constrained GSC systems, key challenges
lie in optimizing transmission formats, compressing data
efﬁciently, integrating controllable generation, and unifying
generation and comprehension tasks. The systematic solution
is needed for practical deployment.
The performance of SC systems is affected by the format
of transmission information. Speciﬁcally, SC systems can be
categorized into analog and digital types. Analog SC systems
transmit encoded continuous feature vectors directly [7]. How-
ever, the absence of well-deﬁned semantic boundaries within
the latent space may result in ambiguous semantic representa-
tions, thereby limiting the performance of the model. In digital
SC systems, the encoded features require quantization prior
to transmission. In deep learning, Vector Quantization (VQ)
based models can discretize high-level semantic information
[8], [9], facilitating semantic alignment. Additionally, the
adaptive codebook better captures dependencies among pixels,
tokens, and phonemes, enabling higher-quality reconstruction.
[10], [11] have demonstrated that VQ based models effectively
handle both reconstruction and semantic downstream tasks.
Beyond the challenges posed by transmission formats,
GSC systems for multimodal signal transmission faces
the challenge of compressing data under limited radio
© 2026 The Authors. This work is licensed under a Creative Commons Attribution 4.0 License.
multicolumn1cFor more information, see https://creativecommons.org/licenses/by/4.0/

## PDF 第 2 页

3350 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
resources while preserving downstream task performance.
Zhang et al. [12] propose a task-oriented U-DeepSC that uses
the feature selection module to ﬁlter multimodal redundan-
cies and enables semantic sharing across tasks, improving
joint training and system performance. However, U-DeepSC
requires transmitting multiple modalities’ feature indices,
resulting in higher bandwidth consumption than single-
modality transmission. Han et al. [13] develop a speech-to-text
and speech-to-speech communication system that enhances
highly efﬁcient communication through soft alignment and
redundancy removal by extracting text semantic features. It
also leverages pre-trained models to reﬁne transcription and
incorporates features such as duration and pitch to support
high-quality audio reconstruction. Jiang et al. [14] introduce
a multimodal LAM-MSC leveraging large language models
to convert multimodal data into unimodal data, improving
information density of transmitted symbols and enabling high-
quality reconstruction. Nevertheless, LAM-MSC suffers from
irreversible information loss when converting multimodal data
to text as an intermediate representation. From these exist-
ing SC systems, there are two strategies for information
compression to address bandwidth constraints: 1) redun-
dancy elimination through intrinsic structural analysis of
source information and 2) channel-aware feature selection for
transmission optimization. Nevertheless, integrating these two
strategies to achieve global compression optimization remains
a technological bottleneck.
Furthermore, existing task-oriented SC systems rarely incor-
porate the functionality of controllable content generation.
In vision-to-text SC, achieving a balance between accurate
content transmission and alignment with user preferences or
emotional tones remains a key research focus.
Finally, multimodal GSC faces the challenge of jointly
optimizing diverse downstream tasks, which primarily include
generation and comprehension tasks. A uniﬁed GSC sys-
tem that efﬁciently integrates multimodal information and
balances accurate content reconstruction with adaptive high-
level semantic reasoning holds great promise. However,
achieving synergy between multimodal data generation and
comprehension remains challenging due to their inherently
conﬂicting objectives [15]. Generative tasks prioritize data
ﬁdelity, extracting low-level structural features for high-quality
reconstruction, such as textures in images [16], logical coher-
ence in text [17], and acoustic characteristics in audio [13]. In
contrast, comprehension tasks focus on semantic extraction
and diversity, emphasizing global context for cross-modal
transformation [18]. For example, image captioning highlights
salient objects and interactions [19].
B. Motivation and Contributions
Although SC has achieved success in many scenarios and
downstream tasks [20], [21], [22], challenges persist in com-
pressing encoded information, achieving personalized content
generation, and coordinating generation and comprehension
tasks. As shown in Fig. 1, deep learning-based lossy image
compression typically involves bit allocation for continuous
features, which leads to inconsistent bitstream lengths in
transmitted signals [23]. In bandwidth-constrained scenarios,
Fig. 1. Our YOTO system, using joint source-channel compression, achieves
efﬁcient transmission under constrained bandwidth and adapts more ﬂexibly
to diverse communication environments than traditional variable bit rate
methods. CBR: Channel Bandwidth Ratio.
this characteristic prevents the transmission of complete data.
However, image compression methods based on VQ can gen-
erate discrete indices, which means the length of transmitted
bitstreams is consistent [24]. Nevertheless, this method has
limited personalized generation capabilities. In this paper, we
propose a You Only Transmit Once (YOTO) SC system that
is based on a VQ encoder-decoder architecture and enables
joint source-channel compression to mask redundant indices.
Additionally, by transmitting only the visual modality, YOTO
can simultaneously perform generation and comprehension
tasks by modifying the receiver network. This single-modal
transmission and multi-modal decoding architecture facilitates
the co-evolution of generation and comprehension models
under a uniﬁed framework, serving as a new SC paradigm
capable of reconstructing and simulating the world, thereby
advancing artiﬁcial general intelligence development in SC.
For generation tasks, the YOTO system processes raw
images with the corresponding Region of Interest (ROI) masks
generated by the CLIPSeg model [25]. This operation guides
spatial information integration through multi-granularity visual
encoding [26]. The encoded features undergo end-to-end
optimized modulation and demodulation via a digital autoen-
coder (AE) before visual decoding for tasks execution. To
achieve controllable information compression, the Source
Feature Selection (SFS) module is employed in the visual
encoder to remove low-density feature patches. Since the
SFS process is parameter-free and the feature retention ratio
is user-deﬁned at the transmitter, the model can adjust the
number of transmitted symbols by tuning these ratios. Addi-
tionally, the Channel Feature Selection (CFS) module further
compresses the modulated data, with the compression rate
jointly regulated by the channel physical state and a Libra
module. For comprehension tasks, leveraging demodulated
signals from generation tasks without additional transmission,
the system trains a Multimodal Language Model (MLM)
through incremental ﬁne-tuning. A visual causality module
and bridging module align visual-textual semantics, while

## PDF 第 3 页

Y AO et al.: YOU ONLY TRANSMIT ONCE: UNIFIED GENERATION AND COMPREHENSION FOR EFFICIENT SC 3351
prompt engineering enables style-controlled text generation.
The YOTO architecture shares transmitter components but
switches receivers to execute generation tasks and comprehen-
sion tasks at the same time. Simulation experiments conﬁrm
YOTO’s superiority over unimodal systems in high-quality
image reconstruction and accurate caption generation. The
main contributions of this paper can be summarized as follows:
• We propose a novel SC framework integrating VQ and
residue state space blocks for completing generation and
comprehension tasks. This system shares the encoder
and digital modulation AE, performing different tasks
by varying the receiver network.
• We propose a joint source-channel compression algo-
rithm based on the SFS and CFS modules at the
transmitter, where the feature retention ratios of the SFS
and CFS modules are regulated by the Libra module.
• We design the visual causality and the bridging module
for incremental ﬁne-tuning of the MLM. In order to
enhance the personalized generation capability of MLM,
we design diverse prompt templates to guide the MLM
in generating texts of different styles.
C. Organization and Notations
The rest of this article is organized as follows. Section II
presents the overall framework of YOTO and the considered
tasks. Section III details the image-to-image transmission,
while section IV presents the principle of the SFS module,
the CFS module, and the Libra module. Section V discusses
the image-to-text transmission. Section VI provides simulation
results, and Section VIIconcludes the paper.
Notations: Scalars are represented by lowercase letters,
while vectors and matrices are represented by boldface letters.
Cm×n(Rm×n) are the m×n complex (real) matrices. E(·)
denotes the statistical expectation. ‖·‖ denotes the Euclidean
norm, |·| represents the number of elements in the set,
and (·)T denotes the transpose of the matrix. ⊙ represents
the Hadamard product. In multi-granularity visual encoding,
j∈{ fg, mg, cg}, where fg stands for ﬁne-grained, mg stands
for medium-grained, and cg stands for coarse-grained.
II. S YSTEM MODEL
In this section, we introduced the YOTO system, as well as
downstream tasks and corresponding evaluation metrics.
A. Vision-Text Transmission System
As shown in Fig. 2, the YOTO system performs gener-
ation and comprehension tasks. Generation tasks emphasize
reconstruction, whereas comprehension tasks prioritize scene
description. By transmitting visual information and adjusting
the receiver networks, both tasks can be executed simultane-
ously.
For the generation task, YOTO handles image-to-image
semantic communication. The input includes image sI ∈
Rh×w×c and the corresponding ROI mask sm ∈ Rh×w,
where h×w is the image resolution and c is the number of
channels. The mask is generated by the CLIPSeg model [25].
Fig. 2. The YOTO system diagram in two training stages. (a) shows the
image-to-image transmission. (b) shows the image-to-text transmission. The
generation task and comprehension task share the transmitter network, and
by varying the receiver network, the YOTO system can achieve decoding for
images and texts. In addition, we adopt the parameter-efﬁcient ﬁne-tuning for
MLM.
The CLIPSeg model introduces a lightweight decoder built
upon a frozen CLIP model [27], facilitating the generation
of image segmentation masks through text queries. CLIPSeg
requires 4.271 GFLOPs and 208ms per mask generation. To
enable low-latency communication, YOTO precomputes and
caches semantic priors ofﬂine, using them as static inputs to its
main encoder. These masks effectively delineate user-speciﬁed
regions and reduce key image information loss. In the source-
channel joint encoding stage, the visual encoder extracts
low-level visual features at three granularities, which are fused
with the ROI mask, resulting in feature vectors zvfg∈ RLfg×c1,
zvmg∈ RLmg×c2, and zvcg∈ RLcg×c3, where Lfg, Lmg, and Lcg
denote the number of symbols, while c1, c2, and c3 represent
the encoded feature dimensions. Next, interpolation is applied
between the ﬁne and medium granularities, aligning them with
the coarse granularity in terms of feature dimensions. After
alignment, features are vector quantized and undergo SFS to
eliminate redundancy, producing corresponding binary masks
mvfg∈ RLfg, mvmg∈ RLmg, and mvcg∈ RLcg. The quantized
vector are then multiplied by the masks and concatenated
along the symbol dimension to form visual tokens zvq ∈
RLv×c′, wherec′ denotes the codebook feature dimension and
Lv represents the number of quantized features.
In the digital modulation stage, the indices of the quantized
features are processed using a sliding window technique, gen-
erating a multi-dimensional one-hot vector zw∈ RLv×Lw×d,
where Lw is the window length and d is the size of the
codebook. zw is further processed for feature extraction
and compression through the digital modulation encoder to
produce zwe ∈ RLv×Lw×d′, where d′ is the compressed
dimension. The modulated features then pass through the CFS
module, where redundant modulation information is removed,
resulting in the ﬁnal real-valued communication information
xv∈ R2×Ls where Ls represents the number of transmission
symbols. The source feature retention ratio is negatively cor-
related with the channel feature retention ratio, as managed

## PDF 第 4 页

3352 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
by the Libra module. The information to be transmitted must
satisfy power normalization, denoted as 12Ls E||xv||2≤ 1.xv
is transmitted via the wireless channel.
The common baseband input-output relation of data trans-
mission over a frequency-ﬂat channel is ˜y = ˜h˜x + ˜n, where
˜y ∈ CLs is the complex-valued receiving data, ˜x ∈ QLs
is the transmission information. Here, Q is the transmitting
constellation set. ˜h∈ C represents the channel gain coefﬁcient
and n∼CN (0,σ 2I) is the Additive White Gaussian Noise
(AWGN), whereσ2 is the noise variance and I is the identity
matrix. In YOTO’s digital modulation stage, we employ an
end-to-end AE for real-valued signal transmission. Using the
deep unfolding strategy [28], the real-valued transmitted signal
is equivalent to the unfolded in-phase and quadrature compo-
nents of the complex signal, and the signal transmission can be
expressed as yv =hxv +n, where yv∈ R2×Ls is the real-
valued receiving data, h∈ R2×2 is the real-valued channel
coefﬁcient. The corresponding relationship can be expressed
as 


yv = [Re{˜y}T Im{˜y}T]T,
h =
[
Re{˜h}−Im{ ˜h}
Im{˜h} Re{˜h}
]
,
n =
[
Re{˜n}T Im{˜n}T
]T
,
xv = [Re{˜x}T Im{˜x}T]T.
(1)
After receiving the signal, channel equalization is performed
by multiplying h−1 to obtain ˆyv = xv + ˆn, where ˆn =
h−1n denotes the equivalent noise. The received signal ˆyv
is processed by a digital demodulation decoder to recover
visual tokens, which are then passed to a visual decoder for
image reconstruction. To enable hierarchical recovery of visual
features, additional transmission of mvfg, mvmg, and mvcg is
necessary. During training, all modules support gradient propa-
gation, while during inference, YOTO image transmission only
requires input images and their corresponding ROI masks.
For the comprehension task, the YOTO system freezes the
visual encoder and digital modulation AE. A bridging module
transforms demodulated visual tokens into semantic tokens
zsm, and it takes visual tokens and a causally-intervened
learnable query feature as inputs. Through the attention mech-
anism, visual tokens are effectively transformed into high-level
semantic representations.
In the training stage, the system takes an image, its ROI
mask, and the corresponding textual descriptions sT ∈ RLt,
whereLt is the sentence length. The description is tokenized to
produce text tokens xt∈ RNt using a Generative Pre-trained
Transformer (GPT) tokenizer based on the Byte Pair Encoding
(BPE) algorithm [29], where Nt represents the number of
text tokens and Nt<Lt. During tokenization, input text whose
length exceeds Nt is truncated, while shorter text is padded
to match this length. After the text tokens are embedded
and positionally encoded, the text features zt ∈ RNt×Nd
are obtained, where Nd is the feature dimension of word
embeddings. Subsequently,zsm andzt are concatenated along
the ﬁrst dimension and fed into the MLM to generate the cor-
responding visual description ˆsT . In addition, the [EOS] token
fromzt and the [CLS] token from zsm are further processed
by contrastive learning to improve the model’s understanding
of vision-text associations. In particular, prompts are added in
front of input texts to enhance the personalized generation
capability of MLM. In the testing stage, the image-to-text
transmission system only needs original images and ROI
masks, enabling the receiver to obtain text descriptions.
B. Downstream Tasks and Performance Metrics
Generation tasks include image reconstruction and object
detection, while comprehension tasks encompass image cap-
tion and sentiment polarity analysis.
Image reconstruction is a low-level vision task. Its evalua-
tion metrics include Peak Signal-to-Noise Ratio (PSNR) and
Structural Similarity Index Measure (SSIM). Object detection
belongs to high-level vision tasks and focuses on locating
and recognizing objects. The evaluation metric for this task
is mAP50, which represents the mean average precision across
all detection categories at an Intersection over Union (IoU)
threshold of 0.5.
In the image caption task, evaluation metrics include
ROUGE-L, the sentence similarity and Semantic Propositional
Image Caption Evaluation (SPICE) [30]. ROUGE-L is based
on the longest common subsequence (LCS), which effec-
tively captures both semantic coherence and coverage of key
information between the generated and reference descriptions.
Sentence similarity is calculated by obtaining the semantic
similarity of the generated text embedding vector and original
text embedding vector. The semantic similarity is calculated
by
similarity(sT, ˆsT ) = B(sT )·B(ˆsT )
||B(sT )||·|| B(ˆsT )||, (2)
whereB(·) represents the semantic representation of the text
obtained through a pre-trained BERT model. What’s more,
SPICE is a common metric for image caption evaluation [30],
which assesses the quality of generated captions by identifying
and matching entities, actions, and relationships between the
generated and reference captions.
Additionally, we adopt the Caption Hallucination Assess-
ment with Image Relevance (CHAIR) metric to evaluate
hallucinations in the image captioning task [31]. It comprises
sentence-level CHAIR (CHAIR s) and instance-level CHAIR
(CHAIRi). Lower values on both metrics signify greater
faithfulness of the generated captions to the visual content.
Specially, CHAIRs indicates whether a caption contains at
least one object not present in the image, which can be
expressed by
CHAIRs =|{sentences with hallucinated object}||{all sentences}| , (3)
where|·| represents the number of elements in the set {·}.
CHAIRi measures the fraction of mentioned object instances
that are absent from the image, which can be expressed by
CHAIRi = |{hallucinated objects}||{all objects mentioned}|. (4)
The sentiment polarity analysis focuses on the emotional
tendencies of texts generated by the MLM. We employ the

## PDF 第 5 页

Y AO et al.: YOU ONLY TRANSMIT ONCE: UNIFIED GENERATION AND COMPREHENSION FOR EFFICIENT SC 3353
Fig. 3. The proposed YOTO system architecture for the image transmission. CFS means the Channel Feature Selection module.
Valence Aware Dictionary and sEntiment Reasoner (V ADER)
[32], which is a lexicon-based and rule-based sentiment anal-
ysis tool. By analyzing the text descriptions, we can obtain
the sentiment compound score, which indicates the overall
sentiment polarity of the text. Compound scores near -1
reﬂect negative sentiment, while scores near 1 reﬂect positive
sentiment.
III. P ROPOSED SEMANTIC COMMUNICATION FOR
IMAGE -TO-IMAGE TRANSMISSION
In this section, we present the image-to-image transmission
system, which contains a visual encoder, a digital modulation
AE, and a visual decoder.
A. Visual Encoder
The 2D Selective Scan Module (2D-SSM) extends state
space mechanisms to spatial domains using parameterized
2D state transitions and depth-wise recursion, enabling efﬁ-
cient long-range dependency modeling and multi-scale feature
extraction with linear computational complexity [33]. In the
visual encoder and visual decoder, we adopt the Residue State
Space Block (RSSB), which builds upon the 2D-SSM and
enhances the vanilla Visual Mamba framework through local
feature enhancement and channel attention mechanisms [34].
According to the visual encoder part in Fig. 3, the input
image sI is ﬁrstly divided into patches. The patch features
are then fed into RSSB modules, generating the ofg,omg, and
ocg. To enhance semantic attention features within the image,
the ROI information fusion is performed across different
granularities. Speciﬁcally, ROI masks are downsampled using
CNN layers with different parameters. For the three granularity
levels of visual features, the corresponding ROI masks are
zmfg ∈ R1×Lfg, zmmg∈ R1×Lmg, and zmcg∈ R1×Lcg. The fusion
module incorporates Spatially-Adaptive Feature Transform
(SFT) blocks [35] and Generalized Divisive Normalization
(GDN) layers [36]. The role of SFT is to restore semantic-level
textures in deep visual features using ROI masks. Its inputs
areoj andzmj , and the mapping function M :zmj ↦→ (γ,β)
generates the afﬁne transformation parameters γ andβ. Deep
visual features are then scaled and shifted, which can be
expressed as wj = SFT(oj|γ,β) = γ⊙ oj +β, where
wj represents the output features of the SFT module at the
j-th granularity. Subsequently,wj is fed into a GDN layer for
feature normalization to generate zvj , which is the ﬁnal output
of the fusion module.
Furthermore, through the upsampling operation, the infor-
mation fusion data is aligned in the channel dimension, which
means that c1 and c2 are interpolated and elevated to c3,
resulting in feature vectors ˜zvfg, ˜zvmg, and ˜zvcg. These are
then passed through a VQ layer to obtain quantized features
zvqfg ∈ RLfg×c3, zvqmg ∈ RLmg×c3, and zvqcg ∈ RLcg×c3, along
with their corresponding discrete indices Indfg,Indmg, and
Indcg. It is worth noting that the dimension of the feature
vectors in the VQ codebook is c′ and c′ is equal to c3. The
VQ step quant(·) can be mathematically expressed as
zvqj,i = quant(ˆzvj,i) = arg min
ck∈C
||ˆzvj,i−ck||,
Ind j,i =k,
(5)
whereC ={ck}dk=1∈ Rc3 denotes the codebook of VQ, ck is
the k-th codeword in the codebook, and (j,i ) is the i-th vector
in the feature data of the j-th granularity. What’s more, the SFS
module reduces redundancy in quantiﬁed features, which are
then ﬂattened and concatenated into aggregated features zvq.
From zvq, we further extract their indices to form the index
set Ind v ={v1,v 2,...,v Lv}, where each element vi∈ N+
represents a index in the codebook. Finally, only the Ind v
needs to be transmitted. Further details are in Section IV.
B. Digital Modulation Autoencoder
Traditional communication systems suffer from subopti-
mal performance due to separately optimize modulation and
demodulation. However, the end-to-end AE, which jointly

## PDF 第 6 页

3354 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
optimizes encoding and decoding by leveraging physical chan-
nel characteristics, can achieve global optimal performance
[37]. YOTO innovatively integrates the end-to-end digital
modulation AE, resolving the inconsistency of simply com-
bining joint source-channel coding with conventional digital
modulation schemes such as QAM or APSK, as shown in
Fig. 3. While joint source-channel coding converts images
into discrete indices, recovering high-quality images under low
Signal-to-Noise Ratio (SNR) is challenging. To address this,
YOTO applies a sliding window operation on these indices.
Comprehensively, each index in the setInd v is applied with
a window whose size is an odd number Lw and the sliding
window stride is 1. The center of the window corresponds to
the target index, while the two sides of the target are redundant
indexes. The resulting sequence is denoted as Ind w, which
can be represented as
Ind w
=


vLv−(Lw−1)/2+1 ··· vLv v1 v2 ··· v(Lw +1)/2
vLv−(Lw−1)/2+2 ··· v1 v2 v3 ··· v(Lw +3)/2
... ... ... ... ... ... ...
vLv−(Lw−1)/2 ··· vLv−1 vLv v1 ··· v(Lw−1)/2

. (6)
Each element of Ind w is converted to a one-hot vector,
resulting inzw∈ RLv×Lw×d, where d is the number of feature
vectors in the codebook.
In the digital modulation AE, the modulation function
denotesfe(·, Φe), where Φe represents modulator parameters.
Unlike traditional methods like QAM and QPSK, this mod-
ulator learns channel characteristics and adapts modulation
strategies for downstream SC tasks. The demodulator denotes
fd(·, Φd), where Φd represents demodulator parameters. The
demodulator not only recovers transmitted visual indices but
also performs signal post-equalization, reducing noise and
identifying the decision threshold for symbol fuzziness.
The architecture comprises multiple DNN layers with tanh
activation and argmax operations. After modulation, zw is
processed to becomezwe , expressed aszwe =fe(zw, Φe).xv is
generated by processing zwe through the CFS module. Finally,
xv is power-normalized and subsequently transmitted through
the physical channel. After zero forcing equalization, the
received signal ˆyv is demodulated by the digital demodulator,
resulting in the discrete index set ˆInd v. The process is
ˆInd v =fd(ˆyv, Φd).
The visual decoder needs three masks generated by SFS to
reconstruct images. Additionally, the transmitter and receiver
share a common codebook. In this process, the Channel
Bandwidth Ratio (CBR) measures information compression in
YOTO, representing the proportion of transmitted signals to
the total original data [38]. Since the dimensions of the three
binary masks are much smaller than the dimension of xv,
with an information content of less than 0.1%, we only need
to consider visual modulated signals. Ultimately, CBR can be
expressed mathematically as CBR = (2×Ls)/(c×w×h).
C. Visual Decoder
In the image reconstruction architecture in Fig. 3, the visual
decoder recovers deep visual information in the form of
conditional probability [39]. Letyi be the output feature at the
i-th block. Moreover, the previous features{y1,y2,..., yi−1}
are input into the i-th reconstruction block to compute
p(yi|yi−1,..., y2,y1), which determines the likelihood ofyi.
Accurate previous latent representations enable the reconstruc-
tion of semantically rich yi.
Speciﬁcally, the feature vectors ˆyvq ∈ RLv×c3 are recon-
structed from the codebook using ˆInd v. ˆyvq is then multiplied
by binary masks, with masked portions ﬁlled with zeros. The
resulting feature is processed through the RSSB to obtain y1,
which serves as the prior input for the medium-granularity
layer to generate y2. Similarly, the ﬁne-granularity recon-
structiony3 is derived from y1 andy2. This process can be
expressed using conditional probability as
y1∼p(y1|ˆyvq⊙mvcg),
y2∼p(y2|y1, ˆyvq⊙mvmg),
y3∼p(y3|y2, ˆyvq⊙mvfg). (7)
The middle two decoder blocks take two inputs: the received
signal ( ˆyvq⊙mvj ) at the corresponding granularity and prior
information from the previous block. Accurate prior informa-
tion compensates for channel distortions, reﬁnes the latent
space progressively, and enhances reconstruction accuracy.
The formulation is as follows
y1 =D1(ˆyvq⊙mvfg),
y2 =D2(concat(y1, ˆyvq⊙mvmg)),
y3 =D3(concat(y2, ˆyvq⊙mvcg)),
ˆsI =Dr(y3), (8)
whereD1,D2, and D3 denote the coarse-grained, medium-
grained, and ﬁne-grained RSSB blocks, respectively. The
operation concat(·) represents the concatenation of two vectors
along the symbol length dimension. Dr refers to the reﬁne-
ment network, which aims to transform the ﬁnal deep visual
features into the reconstructed image.
D. Loss Function
The loss function Lgen of the YOTO image transmis-
sion system consists of the Vector Quantization-Variational
Autoencoder (VQ-V AE) componentLVQ and the Generative
Adversarial Network (GAN) component LGAN.
LVQ addresses two aspects: 1) minimizing the distor-
tion between the original input sI and its reconstruction
ˆsI, and 2) reducing the divergence between the continu-
ous representation ˆzvj and the quantized representation zvqj .
To reconstruct high-ﬁdelity images, we employ the Mean
Squared Error (MSE) and the Learned Perceptual Image Patch
Similarity (LPIPS) loss. Since the quantization process is non-
differentiable, the stop-gradient operator sg(·) is utilized to
optimize the feature vectors in the codebook while enabling
gradient backpropagation to the visual encoder. The hyperpa-
rameter µ is introduced to balance the relative weights of the
two loss terms. The whole process can be expressed as
LVQ =µ·d(sI, ˆsI)
+
∑
j∈{fg,mg,cg}
(||sg(˜zvj )−zvqj ||2+||sg(zvqj )−˜zvj||2), (9)

## PDF 第 7 页

Y AO et al.: YOU ONLY TRANSMIT ONCE: UNIFIED GENERATION AND COMPREHENSION FOR EFFICIENT SC 3355
Fig. 4. There are two information feature selection modules, namely the Source Feature Selection and Channel Feature Selection. Furthermore, the relationship
between the channel feature retention ratio and the source feature retention ratio can be further adjusted via the Libra module.
whered(·) represents the distortion metric between the original
and reconstructed data, which incorporates both the MSE and
LPIPS loss terms.
In the discriminator loss, we employ the original discrim-
inator Do and the patch-based discriminator Dp. LGAN is
computed as the average loss of these two GAN discrimi-
nators, which can be expressed as
LGAN =
∑
k∈{o,p}
[
logDk(sI) + log(1−Dk(ˆsI))]. (10)
To sum up, we combine the VQ-V AE loss and the GAN
loss to produce Lgen = LVQ + λgLGAN, where λg is a
hyperparameter used to balance LVQ andLGAN.
IV. R EDUCTION OF INFORMATION REDUNDANCY IN JOINT
SOURCE -CHANNEL CODING
This section details the SFS, CFS, and Libra modules
which are all integrated into the encoder. They can compress
information effectively while preserving essential semantics.
A. Source Feature Selection
During joint source-channel encoding, deep visual infor-
mation often contains ﬂat or gradually changing regions
with simple distributions and spatial redundancy. To enhance
efﬁciency, compressing these redundant features is crucial.
Inspired by [40], we use a non-parametric spatial entropy
algorithm to evaluate local patch information density, as shown
in Fig. 4. High-entropy patches indicate complexity and rich
semantics, while low-entropy patches represent redundancy.
Let Ω ∈ zvqj denote a patch in the deep visual feature,
and p∈ Ω represent a pixel within this patch, where p takes
values in the range [−1, 1]. The pixel value bin e is deﬁned as
e =−1 + 2mn−1, where m ={0, 1,...,n − 1} and n is the total
number of bins. The Gaussian distance fp,e between pixel p
and each bin e is then calculated, which can be expressed as
fp,e = exp
(
−(p−e)2
2σ2
)
, (11)
where exp(·) represents the exponential operation and σ is the
standard deviation.
Next, the Gaussian distances are normalized within the
feature patch. For a ﬁxed bin, the average Gaussian distance
fΩ,e across all pixels is computed. Using fΩ,e, we iterate over
all bins to obtain the ﬁnal normalized average fΩ,e, which can
be expressed as
fΩ,e = fΩ,e∑
bfΩ,b
, wherefΩ,e = 1|Ω|∑p∈Ωfp,e. (12)
Consequently, the spatial information entropy H(Ω) of the
local feature map is computed as H(Ω) =−∑efΩ,e logfΩ,e.
After computing the spatial information entropy for the fea-
ture maps at three granularity levels, we generate binary
masks mvfg, mvmg, and mvcg by retaining elements with the
lowest entropy according to user-speciﬁed retention ratios
(r1,r 2,r 3) ∈ [0, 1]. In these masks, elements with value 1
represent preserved features, while 0 indicates redundancy.
The binary masks are expanded via broadcasting to match
the dimensions of the corresponding deep visual features zvqj
and then perform element-wise multiplication betweenzvqj and
masks. During the SFS process, the source feature retention
ratio rSFS represents the proportion of element 1 in all data,
expressed as
rSFS = Lcg×r1 +Lmg×r2 +Lfg×r3
Lcg +Lmg +Lfg
. (13)
B. Channel Feature Selection
The digital modulator outputs zwe ={F w1,F w2,..., F wLv},
whereF wi denotes the windowed data. Compared tozw,zwe is
signiﬁcantly compressed in the last dimension, which enhances
communication efﬁciency. However, not all redundant win-
dowed information in F wi is able to resist physical channel
interference. As shown in Fig. 4, the CFS module generates
binary masks for each windowed data. F wi is multiplied by
its mask via the Hadamard product to remove redundancy,
producing sparse data for efﬁcient visual decoding.
Speciﬁcally, the estimated noise variance ˆσ2 and zwe are
the two inputs in the CFS module. ˆσ2 is derived from prior
knowledge obtained through long-term statistical averaging.
In practical training or inference of YOTO, we treat ˆσ2 as
the reciprocal of the SNR in the linear domain. A Multilayer

## PDF 第 8 页

3356 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Perceptron (MLP) transforms ˆσ2 into xvar ∈ RLv×Lw×d′,
which captures the physical characteristics of the channel.
In addition, the physical characteristics are integrated
into zwe , expressed as F f = Reshape(MLP(ˆσ2)) + zwe ,
where F f = {F 1,F 2,..., F Lv} ∈ RLv×Lw×d′
denote the fused data. Consider a windowed symbol
F a =
{
h1,..., h(Lw+1)/2,..., hLw
}
∈ RLw×d′,
where a ∈ {1, 2,...,L v} and hi ∈ Rd′. The center
feature hma = h(Lw+1)/2 represents the core target
information, while the surrounding features H a ={
h1,..., h(Lw−1)/2,h(Lw+3)/2,..., hLw
}
∈ R(Lw−1)×d′
constitute redundancy information. The scoring function
f s : R(Lw−1)×d′→ Rd′ is deﬁned to compute the relevance
Asa of redundant vectors to the target feature, which
can be expressed as Asa = fs(H a,hma ) = H TaW ahma ,
where W a ∈ R(Lw−1)×d′ is a trainable weight
matrix. Furthermore, by interacting the relevance Asa
with redundant vectors, the discretized features and
information on redundancy removal can be effectively
obtained, expressed as Ama = GS(AsaH Ta ), where GS
refers to the Gumbel Softmax function [41]. Besides,
Ama = {m1,...,m (Lw−1)/2,m (Lw+3)/2,...,m Lw} ∈
{0, 1}Lw−1 represent the contribution levels of
various redundancy variables. Intuitively, core target
information should not be masked. Therefore, ma ∈
{m1,...,m (Lw−1)/2, 1,m (Lw+3)/2,...,m Lw}∈{0, 1}Lw is
the ﬁnal binary mask in the CFS module. Each binary data
dimension is then expanded to d′ through a broadcasting
mechanism, resulting in the broadcasted maskmBa ∈ RLw×d′.
Ultimately, element-wise multiplication ofF a withmBa yields
the feature-selected data F CFSa , which can be expressed as
F CFSa =F a⊙mBa .
In the CFS process, rCFS denote the channel feature reten-
tion ratio, which can be calculated as
rCFS =
∑Lv
a=1gs(ma)
Lv×Lw
, (14)
wheregs(·) represents the number of elements 1 in the multi-
dimensional vector. mCFS ={m1,m2,..., mLv} represents
the collection of all binary masks. Each binary mask is applied
to thezwe for generating sparse dataxv. It is worth noting that∑Lv
a=1gs(ma) = Ls is the number of symbols transmitted
into the channel. Through the following transformation, we
can obtain the relationship between rCFS and CBR, which is
CBR = (2×Lv×Lw×rCFS)/(c×w×h). When the source
feature retention ratio is ﬁxed, Lv remain constant, and rCFS
is proportional to CBR. For simplicity, we only consider the
channel feature retention ratio rCFS.
C. The Libra Module
To balance reconstruction quality and compression, the
Libra module dynamically adjusts the channel feature retention
ratio based on the source feature retention ratio. A high
source ratio reduces the channel ratio for compression, while
a low source ratio increases the channel ratio for quality
preservation. This inverse relationship enables the CFS module
to maintain a controlled level of information compression
during end-to-end training aimed at minimizing distortion.
This adaptive trade-off is governed by a monotonic neural
network. The Libra module takes in the estimated noise
variance ˆσ2 and rSFS, consisting of two branches to balance
the source and channel ratios.
The ﬁrst branch consists of two interpretable layers and a
monotonic layer, withrSFS as its input. This branch is designed
to maintain an inverse relationship between the source and
channel feature retention ratios. The interpretable layer is
deﬁned as follows: let y(k) denote the output of the k-th
interpretable layer, where y(k)i is the i-th value of the output
vector. The mathematical expression for the (k + 1)-th layer
isy(k+1) = sigmoid(exp(W (k))y(k) +b(k)), whereW (k)
is the weight matrix of the k-th layer, exp(·) denotes element-
wise exponential operation,b(k) is the bias vector, and tanh(·)
represents the hyperbolic tangent activation function. If the k-
th interpretable layer has N(k) neurons, the partial derivative
relationship between the (k + 1)-th and k-th layers can be
expressed as
∂y(k+1)i
∂y(k)r =ψ′


N (k)∑
a=1
exp(W (k)i,a )y(k)a +b(k)i

 exp(W (k)i,r ),
(15)
where ψ denotes the sigmoid activation function, whose
derivative is expressed as ψ′(x) = ψ(x)(1− ψ(x)). This
derivative is always non-negative. Additionally, exp(W (k)i,r )
is non-negative, ensuring positive partial derivatives between
adjacent interpretable layers. Thus, stacking these layers main-
tains an increasing monotonic relationship.
Furthermore, in order to ﬂexibly control the monotonicity
(increasing or decreasing) of interpretable layers, the mono-
tonic layer must be placed between two interpretable layers.
Let ˜y(k) denote the output of the monotonic layer following
the k-th interpretable layer. We introduce a hyperparameter
η, which is broadcasted and multiplied element-wise with the
output of the k-th layer, expressed as ˜y(k) = η⊙y(k). The
partial derivative between interpretable layers with adjustable
monotonicity can then be expressed as ∂y(k+1)i /∂˜y(k)r =
(∂y(k+1)i /∂y(k)r )· (1/η), where 1/η acts as a multiplicative
factor. When η <0, the partial derivative becomes negative,
indicating that the interpretable layer with the monotonic layer
exhibits a monotonically decreasing relationship. In summary,
the ﬁrst branch begins with an interpretable layer l(1)I and a
monotonic layer l(1)M , establishing a monotonically decreasing
relationship. There is an interpretable layer at the end of the
branch l(2)I . The ﬁnal output of the ﬁrst branch, regulated
by the monotonic and interpretable layers, is denoted as
X ={χ1,χ 2,...,χ Lv}∈ RLv.
For the second branch, ˆσ2 andrSFS are concatenated into a
feature vector nf∈ R2. A gating network fG : R2→ RLv,
based on the MLP and sigmoid activation, regulates the mono-
tonic features of the ﬁrst branch. The output of this gating
network is g =fG(nf) =ψ(MLP(nf)) ={g1,g 2,...,g Lv}.
The second branch primarily restricts the magnitude of the
ﬁrst branch’s output between the outputs of the two branches,
expressed as XCFS = g⊙X ={g1·χ1,g 2·χ2,...,g Lv·
χLv} ={χg1,χ g2,...,χ gLv}, where XCFS serves as the output

## PDF 第 9 页

Y AO et al.: YOU ONLY TRANSMIT ONCE: UNIFIED GENERATION AND COMPREHENSION FOR EFFICIENT SC 3357
Fig. 5. The text decoder of the proposed YOTO system for the image-to-text
transmission. When the visual encoder and the digital modulation autoencoder
are frozen, the YOTO system can generate the corresponding text description
using the demodulated signal ˆyvq.
of the Libra module, representing the target feature retention
ratio for CFS. To align mCFS with XCFS, we design a loss
functionLlb that adjusts the masking ratio for each symbol,
expressed as
Llb = 1Lv
Lv∑
v=1
(
χgv− 1Lw
Lw∑
i=1
m(i)v
)
, (16)
wherem(i)v represents the i-th binary value in the mask cor-
responding to the v-th symbol and ∑Lwi=1m(i)v /Lw represents
the feature retention ratio corresponding to the v-th windowed
symbol.
In conclusion, the ﬁrst training stage loss function Limg is
Limg =Lgen +λlbLlb =LVQ +λgLGAN +λlbLlb, (17)
whereλlb represents the scaling factor for the Libra module’s
loss.
V. P ROPOSED SEMANTIC COMMUNICATION FOR
IMAGE -TO-TEXT TRANSMISSION
This section introduces image-to-text transmission, which
includes an MLM-based generator for image captions.
A. Image-to-Text Transmission System
Image captioning is a key multimodal task that involves
identifying objects in an image and describing their inter-
actions in natural language. However, existing systems often
struggle with semantic gaps between visual and text tokens due
to visual encoders lacking common-sense knowledge of object
relationships. We developed an image captioning system that
integrates a semantic token conversion module and an MLM.
In the image-to-text system, the visual encoder and the digital
modulation AE structure remain unchanged to receive visual
tokens ˆyvq.
The receiver for the semantic token conversion module
consists of a causal intervention adapter (also referred to as the
visual causality module) and a bridging module, as illustrated
in Fig. 5. These two modules work in tandem to address the
semantic discrepancy between images and texts.
The adapter in YOTO draws architectural inspiration from
the Deconfounded Qformer module proposed in [15]. How-
ever, while the Qformer primarily aims to disentangle visual
tokens from pixel-space confounders, the causal intervention
adapter is explicitly designed to enhance performance on com-
prehension tasks. In multi-object scenarios, dataset inductive
bias can signiﬁcantly affect ﬁne-grained caption generation in
Bayes rule-based models. The causal intervention adapter is
used to eliminate this bias, whose overall architecture inherits
the foundational design of the Q-Former from BLIP2 [42] and
incorporates a causal intervention mechanism. This adapter
infers causal relationships among visual objects by analyzing
the global context of images. The core of this part is to learn an
optimizable query vector q∈ RLc×Nc, where Nc represents
the number of visual objects to be extracted. In detail, the
query vector q interacts with the confounding dictionary Z
through a cross-attention mechanism, producing a globally
optimized visual representation qc∈ RNc×N . In this work, Z
is constructed by averaging the region features of each object,
extracted via an object detection algorithm across the entire
training dataset. The confounder dictionary can be represented
as Z ={zi}Ni=1∈ RN×Lc, where N denotes the number of
visual objects in the dataset, and Lc represents the dimen-
sionality of the confounder feature. The demodulated signal
ˆyvq serves as low-level visual tokens, representing visual fea-
tures. The bridging module is composed of slot attention and
self-attention. To capture interrelationships among key visual
objects, we use the Slot Attention [43], which aggregates
visual tokens into a compact set of dependent representations
and reduces token count as well as computational complexity
for the downstream MLM. In our framework, the slot tensor
is initialized with qc and undergoes T iterative updates to
generateqcT∈ RNc×N . Subsequently,qcT is processed through
causal self-attention to output qcf∈ RNc×N .
Furthermore, we design a mapping network at the tail
of the bridging module to align visual and text tokens in
feature space for multimodal fusion. This network implements
dimension transformation, which outputs the semantic token
zsm = qcfW M ∈ RNc×Nd, where W M ∈ RN×Nd and
Nd corresponds to the feature dimension of word embed-
dings in GPT models. Through this bridging process, the
quantized visual tokens are effectively transformed into seman-
tically aligned feature vectors. During model training, the
text modality is ﬁrst tokenized using a GPT tokenizer to
obtain text tokens xt = {t1,t 2,...,t Nt} ∈RNt, where ti
denotes the i-th text token. These tokens are then projected
into a high-dimensional space via an embedding layer, fol-
lowed by positional encoding to generate ordered text features
zt ={te1,te2,..., teNt} ∈RNt×Nd. After that, zt and zsm
are concatenated along the token dimension, which can be
expressed as zf = concat(zt,zsm) ∈ R(Nt+Nc)×Nd. This
fused representationzf is fed into the MLM for the generation
of the ﬁnal text. Our framework employs a GPT2-based MLM
to autoregressively generate image captions ˆsT usingzf as the
contextual preﬁx. In particular, we employ parameter-efﬁcient
ﬁne-tuning for the GPT2 model to enhance text generation
accuracy. Given the prohibitive training costs of full ﬁne-
tuning for MLMs, we integrate the Low-Rank Adaptation

## PDF 第 10 页

3358 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
(LoRA) module [44] into the self-attention mechanism’s QKV
projections and feed-forward networks. During inference, the
received signal ˆyvq acts as the preﬁx input for the MLM
to generate text autoregressively. For each token, the MLM
predicts vocabulary distributions, with beam search selecting
the next token. Tokens are appended until predeﬁned length
limits or the [EOS] token is reached. The GPT2 tokenizer’s
decoder then converts the tokens into textual descriptions.
The YOTO system generates customizable image captions
by using sentiment-oriented prompt engineering. It leverages
domain-speciﬁc prompts (hard, soft, or hybrid) as training
anchors to ensure varied caption styles within a uniﬁed and
robust model. For hard prompts, we use two templates, which
are “A positive picture shows that” for positive emotions
with the training dataset Dhp and “A negative picture shows
that” for negative emotions with the training dataset Dhn. The
prompts are added to the training texts. After being tokenized
and embedded, hard prompts are transformed into the positive
token embeddingP hp and the positive token embeddingP np.
Inspired by CoOp [45], we design an end-to-end automatically
learned soft prompt template P s = [ p]1[p]2... [p]Np ∈
RNp×Nd, where pi∈ RNd denotes the i-th embedding vector
initialized via Gaussian random sampling. During training, soft
prompts can be optimized to ensure that MLM generates text
accurately. The training dataset for this process is denoted as
Ds. Hybrid prompts combine hard prompts and soft prompts,
which can not only be optimized the prompt through back-
propagation, but also highlight the emotional tendency. The
hybrid prompt templates are expressed as P sp = [P hp,P s]
andP sn = [P hn,P s]. The training datasets for this process
are denoted as Dsp andDsn. In the inference stage, [BOS]
is ﬁrst encoded and combined with various prompt template
embeddings before being fed into the MLM. By switching
different prompts, the model can generate personalized text.
B. Loss Function
The training stage of the image-to-text system involves
autoregressive cross-entropy loss and contrastive learning
(CL).
Firstly, in order to achieve a uniﬁed model capable of
generating multi-style image captions, cross-entropy loss can
be computed separately across multiple datasets and then
the results are averaged together [46]. Thus, the system’s
autoregression loss function Lar can be expressed as
Lar=−
∑
j∈S
[
E(sI ,sT )∈Dj
[ Nt∑
i=1
logP (ti|zsm;P j;te<i)
]]
, (18)
whereS ={hp,hn,s,sp,sn} represents the set of all indices
for datasets and their corresponding prompts’ superscripts.
Next, we employ contrastive learning to enhance the seman-
tic alignment between text embeddings and visual feature
vectors in the latent space [47], [48]. Speciﬁcally, let k ∈
{1, 2,...,B } index the image-text pairs in a batch. In mul-
timodal processing, the [CLS] token serves as a special
token representing the global contextual feature of the image,
which is computed as the average sum of all semantic tokens
zCLS = ∑Nci=1zsmi ∈ RNd. For the text feature vectors
embedded by GPT, the [EOS] token signiﬁes both the end
of the sentence and the global contextual features of the text
sequence, denoted as zEOS =teNt∈ RNd. The contrastive loss
Lcl is formulated as
Lcl =−
∑
k∈B
log exp(sim(zCLSk ,zEOSk ))∑B
a=1 exp(sim(zCLSa ,zEOSa )), (19)
where zCLSk and zEOSk represent the [CLS] token and [EOS]
token of the k-th image-text pair within a batch, respectively.
The function sim(·,·) denotes cosine similarity. Consequently,
during the second training phase of the YOTO system, the
ﬁnal image-to-text transmission loss function Ltext can be
represented as
Ltext =Lar +Lcl. (20)
VI. S IMULATION RESULTS
In this section, we provide a detailed presentation of the
simulation setup and model performance.
A. Simulation Setup
1) Datasets: For generation tasks, the dataset is MS COCO
2014 & 2017 [49], with image resolutions set to 224× 224.
The downstream tasks include image reconstruction and object
detection, where object detection is performed using the
YOLOv8 algorithm based on reconstructed images [50]. For
comprehension tasks, the SentiCap dataset is utilized [51].
This dataset selects images from MS COCO and provides
corresponding textual descriptions labeled with positive or
negative sentiments. We also augment the Senticap with a
portion of the MS COCO dataset, ultimately constructing a
training dataset comprising 10,000 image-caption pairs.
2) Model Training Settings: For generation tasks, we
employ the Adam optimizer with a batch size of 8, a learning
rate of 1× 10−4, and train for 150 epochs. The VQ codebook
size is set to 1024. For comprehension tasks, we set the learn-
ing rate as 2.25× 10−5, and train the model for 100 epochs.
These training parameters were selected via grid search and
yield optimal performance on validation experiments. The
tokenizer’s maximum text length is 32, with truncation for
longer texts and padding for shorter ones. The model is trained
on both AWGN and Rayleigh fading channels at SNR=-4 dB,
2 dB, and 8 dB. After a two-stage training process, the model
is tested across an SNR range from −6 dB to 18 dB. Finally,
the MLM adopted in this paper is GPT2 Small, which is
sufﬁciently capable of handling comprehension tasks.
3) Benchmark Schemes: The benchmark schemes include
deep learning-based SC systems and classical separate source-
channel coding approaches. For the YOTO image transmission
experiments, the deep learning-based baseline method is Swin-
JSCC [38], which is a joint source-channel coding SC system
built on the Swin Transformer backbone and demonstrates
superior image reconstruction performance. The classical
approach uses JPEG for source coding, LDPC for channel
coding, and 16QAM for digital modulation. For the YOTO
image-to-text transmission experiments, the deep learning-
based baseline method is Text DeepSC [52], which enhances
the transmission capacity of the communication system by

## PDF 第 11 页

Y AO et al.: YOU ONLY TRANSMIT ONCE: UNIFIED GENERATION AND COMPREHENSION FOR EFFICIENT SC 3359
Fig. 6. The performance of the image reconstruction task among YOTO
and baseline methods versus SNR over the AWGN and the Rayleigh fading
channel.
Fig. 7. The performance of the object detection task among YOTO and
baseline methods versus SNR over the AWGN and the Rayleigh fading
channel.
Fig. 8. The PSNR performance versus SNR and Source Feature Retention
Ratio over the AWGN and the Rayleigh fading channel.
maximizing the preservation of sentence meaning. The tra-
ditional approach employs Huffman coding for English text
source coding, Reed-Solomon (RS) for channel coding, and
16QAM for digital modulation. To ensure fair comparisons,
all methods are trained and tested on the same datasets.
B. Task Performance
1) Image to Image Transmission: Image reconstruction is
the most fundamental task in image transmission systems.
As shown in Fig. 6, when SNR is less than 4 dB in the
AWGN channel, traditional separate source-channel coding
fails to reconstruct images, whereas the YOTO system and
SwinJSCC demonstrate strong resistance to channel interfer-
ence. Speciﬁcally, when SNR is 0 dB, the YOTO system
achieves a PSNR of 28 dB. When SNR is higher than 14 dB,
traditional coding systems outperform YOTO. This is because
YOTO performs lossy encoding and removes feature blocks
with low information density in the visual encoder, causing
the reconstructed image to lose more details. Notably, the
Fig. 9. PSNR and SSIM versus SNR across the AWGN and the Rayleigh
channel in ablation experiments.
highest PSNR achieved by the YOTO system is 37.03 dB,
indicating that it can reconstruct most texture details under
high SNR conditions. In the Rayleigh fading channel, as
shown in Fig. 6, the YOTO system consistently outperforms
other methods across all SNR levels, further demonstrating
the robustness of the proposed method. Object detection is
performed on the basis of the reconstructed images. This task
evaluates how well reconstruction methods preserve high-level
semantic features. Specially, YOTO transmits and reconstructs
500 random images from MSCOCO 2014 val, then tests
all SNR-level reconstructions with a pre-trained and ﬁxed
YOLOv8m model. As shown in Fig. 7, YOTO outperforms the
baseline at low SNRs in both AWGN and Rayleigh channels,
indicating better preservation of semantic content for object
detection under noisy conditions. The second row of Fig. 10
shows ROUGE-L scores for caption quality. In the AWGN
channel, YOTO’s score rises from 0.041 at 0 dB to 0.494
at 18 dB, surpassing deep learning–based SC methods. Even
under the Rayleigh fading channel, YOTO maintains strong
performance with a score of 0.425. Huffman + RS lags at low
SNR but improves rapidly, achieving the highest text quality
at 18 dB.
Fig. 8 illustrates the relationship among the source feature
retention ratio in the SFS module, channel SNR, and image
reconstruction quality. In both AWGN and Rayleigh fading
channels, a higher source feature retention ratio and favorable
channel conditions lead to enhanced reconstruction quality.
To validate the rationality and effectiveness of each module,
we progressively removed the ROI Fusion (RF), Libra Module
(LM), CFS module, and SFS module. Additionally, the multi-
granularity visual feature extractor can be replaced with a
single-granularity extractor, where only three RSSB modules
are used at both the transmitter and receiver, and the trans-
mitted information comprises the quantized output from the
ﬁnal RSSB in the visual encoder. There is no jump connection

## PDF 第 12 页

3360 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 10. Comparison of text generation quality between the proposed method
and baseline methods under AWGN and Rayleigh fading channels.
operation in single-granularity encoding and decoding. The
results are shown in Fig. 9. Both PSNR and SSIM metrics
are used to provide a comprehensive evaluation. Removing
the RF module reduces reconstruction quality in the YOTO
system due to the absence of critical visual guidance. Further
eliminating the LM disrupts inverse-proportional guidance. In
this ablation, with the Source Feature Retention Ratio ﬁxed
at 0.6 (a low level), the absence of LM’s guidance impairs
the system’s ability to retain and transmit richer features,
ultimately degrading downstream performance. Conversely,
removing the CFS module allows full feature transmission,
enhancing image reconstruction via the conditional proba-
bility decoder. Setting the source feature retention ratio to
1 (effectively removing the SFS) preserves all low-level
features, maximizing reconstruction quality. Moreover, the
single-granularity system, lacking multi-level feature extrac-
tion, provides insufﬁcient encoding and delivers the poorest
performance. Lastly, JPG + LDPC fails at low SNRs in
AWGN due to noise sensitivity but outperforms YOTO and
approaches near-lossless quality when SNR is above 16 dB.
In the Rayleigh fading channel, YOTO remains consistently
more robust than JPG + LDPC across all SNRs.
2) Image to Text Transmission: By replacing the visual
decoder with an MLM-based captioning system, the YOTO
system can perform image-to-text transmission. As shown
in Fig. 10, varying prompt templates yield different
text generation performances. Soft prompts are optimized
end-to-end and enable MLM to achieve optimal prompts and
generate the best-quality text. Hybrid prompts allow only par-
tial end-to-end optimization, resulting in lower performance.
The positive prompt and negative prompt are categorized
as hard prompts, which are manually designed and perform
the worst in prompt engineering. The training dataset in
comprehension tasks contains a small number of text descrip-
tions, which is insufﬁcient for training a text reconstruction
model from scratch. Additionally, such a small-scale model
Fig. 11. Positive and negative sentiment analysis across different SNR levels
for hard and hybrid prompts in both the AWGN channel and the Rayleigh
channel.
inherently has weaker generation capabilities compared to the
pre-trained MLM, leading to poor performance for the Text
DeepSC benchmark system. Traditional separate text transmis-
sion methods perform best at high SNR levels in both AWGN
and Rayleigh channels, achieving a similarity score of 1 at
SNR = 18 dB. Similar to the image transmission systems, lossy
compression and modality conversion contribute to the weaker
performance of deep learning-based SC systems compared to
traditional communication systems. To further highlight the
advantage of end-to-end architecture, we also evaluate a two-
stage pipeline: images are ﬁrst reconstructed using SwinJSCC
and then captioned with CLIPCap [53]. In CLIPCap, the
visual encoder is frozen, and only the single-layer MLP
mapping network and the autoregressive model are trained
and ﬁne-tuned on reconstructed images from SwinJSCC when
SNR=−4 dB, 2 dB, and 8 dB. As shown by the orange curve
in Fig. 10, this pipeline lags signiﬁcantly behind the end-to-
end architecture, demonstrating that decoupled designs cannot
effectively preserve task-critical semantics under channel dis-
tortion.
The generated texts using hard prompts and hybrid prompts
exhibit measurable sentiment biases, which are evaluated using
the V ADER model as shown in Fig. 11. Hybrid prompt
templates, beneﬁting from partial end-to-end optimization,
produce stronger sentiment biases compared to hard prompts.
When SNR is lower than 2 dB, reconstructed texts become gar-
bled and lose linguistic coherence, resulting in no discernible
sentiment bias. When SNR is higher than 2 dB, the improved
text quality enhances the manifestation of sentiment polarity.
Moreover, since the interference caused by AWGN on the
transmitted signal is less than that in the Rayleigh channel, the
YOTO system generates text with more pronounced emotional
tendencies in the AWGN channel. The above analysis demon-
strates that YOTO achieves high accuracy, strong robustness,
and controllable sentiment in the comprehension task, under-
scoring its high reliability.

## PDF 第 13 页

Y AO et al.: YOU ONLY TRANSMIT ONCE: UNIFIED GENERATION AND COMPREHENSION FOR EFFICIENT SC 3361
Fig. 12. The sentence similarity and SPICE performance versus SNR across
different channels in ablation experiments.
In the ablation study, we employ sentence similarity and
SPICE to analyze the impacts of the Visual Causality Module
(VCM) and Bridging Module (BM). When ablating the VCM,
the received ˆyvq transforms solely through slot attention,
self-attention and the mapping network during training and
testing. For the BM ablation, ˆyvq is processed exclusively
via the mapping network under the same training and testing
conditions. To explore the upper bound performance, we
train and test the complete system without channel physical
interference, achieving an Upper Bound of 0.9256 for sentence
similarity and 0.75 for SPICE.
As shown in Fig. 12, ablating the VCM leads to degraded
text generation quality due to dataset inductive bias. Removing
the BM further reduces system performance. Even at high
SNR levels, the model fails to reach the Upper Bound, indicat-
ing challenges in overcoming interference caused by AWGN
and Rayleigh fading channels under few-shot learning. At
SNR = 18 dB, our YOTO system achieves the highest sen-
tence similarity of 0.9057 and the highest SPICE of 0.5714
in the AWGN channel, and reaches 0.8864 and 0.4615 in
the Rayleigh fading channel, respectively. Additionally, Huff-
man + RS nearly fails to recover meaningful text when
SNR<6 dB, but its performance sharply improves beyond
14 dB, eventually surpassing YOTO.
What’s more, we explore how the Libra module guides the
reduction of the channel feature retention ratio through the
loss functionLlb. As illustrated in Fig. 13, under the AWGN
channel, increasing SNR and rSFS values correlate with a
sharp decline in the output of the Libra module. This trend
subsequently induces corresponding reductions in the CFS
module’s retention ratios through Llb. Similar relationships
persist in Rayleigh channels.
Table. I comprehensively evaluates the impact of back-
end language models with varying parameters on the
Fig. 13. The ﬁgures illustrate the channel feature retention ratio and Libra
module output versus SNR and source feature retention ratio over the AWGN
and the Rayleigh channel, respectively.
TABLE I
PERFORMANCE COMPARISON OF BACKEND LANGUAGE MODELS
TABLE II
COMPARISON OF HALLUCINATION RATES UNDER
NO-CHANNEL TRANSMISSION CONDITIONS
image-to-text task performance. The experiments, which are
assessed in terms of decoding latency and sentence similarity,
demonstrate the rationale behind the choice of GPT2 Small.
Notably, these results are conducted over an AWGN channel
at SNR= 2 dB, and the ﬁndings remain broadly representative.
Among the evaluated models, only GPT2 Small meets the
300 ms latency requirement for vision-based monitoring appli-
cations speciﬁed in the 5GCroCo/D3.2 standard. Furthermore,
under the same channel condition, GPT2 Small achieves a sen-
tence similarity score of 0.680, showing minimal performance
degradation compared to signiﬁcantly larger models.
Besides, the VCM and CL mechanisms in YOTO effectively
reduce hallucinations in the comprehension task. To verify this,
we remove the intermediate channel transmission focusing on
the model’s core functionality and perform ablation studies. As
shown in Table. II, under the channel-free condition, the full
model achieves the lowest CHAIRi and CHAIRs. Removing
either VCM or CL increases both CHAIRi and CHAIRs,
indicating a signiﬁcant rise in hallucination rate. In conclusion,

## PDF 第 14 页

3362 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
Fig. 14. Examples of neutral, positive, and negative captions for image
descriptions. Through prompt engineering, the YOTO system can generate
image captions with different emotional tendencies.
TABLE III
COMPUTATIONAL COST COMPARISON OF DIFFERENT SC S YSTEMS
TABLE IV
LATENCY COMPARISON OF DIFFERENT SC S YSTEMS
VCM and CL are crucial for mitigating object and attribute
hallucination in generated captions.
Lastly, we present three examples of the image-to-text
system, with the results shown in Fig. 14. Neutral captions
are generated via soft prompts, positive captions are produced
using positive prompt templates, and negative captions are
generated with negative prompt templates.
3) Complexity and Delay Analysis: This subsection pro-
vides a detailed analysis of YOTO’s computational complexity
and inference latency to evaluate its deployability. The exper-
imental results on computational complexity are presented in
Table. III. In the generation task, YOTO achieves a throughput
of 76.60 samples per second (sps) with only 13.76 M param-
eters and 166.65 GFLOPs, outperforming both traditional
and deep learning-based SC systems. This efﬁciency stems
from its linear-complexity Mamba backbone, which avoids
the quadratic cost of Transformers. For comprehension, YOTO
employs a large autoregressive model to ensure high accuracy
at the cost of reduced throughput.
The inference latency results for YOTO and the baseline
method are shown in Table. IV. YOTO delivers less than
Fig. 15. Performance Comparison of SC systems with Perfect and Imperfect
CSI under Quasi-static TDL-A Channels.
0.3 s end-to-end latency in generation, outperforming tra-
ditional methods in real-time response. For comprehension,
it exhibits elevated decoding latency, yet reuses visual fea-
tures to reduce bandwidth and power, making it ideal for
communication-efﬁcient deployment.
4) Performance Evaluation Under Imperfect Channel: To
investigate the performance of the YOTO system under non-
ideal channel conditions, we replace the ideal channel with
the 3GPP-speciﬁed Tapped Delay Line–A (TDL-A) channel
model, which is widely used in 5G system simulations and
performance evaluations for scenarios with low delay spread.
For analytical convenience, we model the TDL-A channel as
quasi-static, where the channel gains remain constant over the
duration of a single data block transmission. Furthermore,
the least squares (LS) algorithm is employed to estimate
the channel state information (CSI) for zero-forcing equal-
ization. Since the LS-based CSI estimates are imperfect,
primarily due to receiver noise, we evaluate the system’s
performance on both generation and comprehension tasks
under both perfect and imperfect CSI conditions. The results
are presented in Fig. 15. Under quasi-static TDL-A fading
channel with imperfect CSI, YOTO outperforms traditional
schemes in image reconstruction and caption at low SNR. At
SNR = 12 dB, it achieves 29.32 dB PSNR and 0.71 simi-
larity under imperfect CSI, which is far beyond conventional
methods. When SNR > 16 dB, YOTO’s lossy semantic com-
pression and noise ampliﬁcation limit decoder performance,
yielding lower PSNR and sentence similarity than traditional
schemes. Notably, YOTO’s performance under imperfect CSI
is consistently inferior to that under perfect CSI across all
evaluated scenarios.
VII. C ONCLUSION
In this paper, we propose a YOTO multimodal seman-
tic communication framework, which completes the image
generation task and the caption comprehension task under
high information compression. In particular, the transmitter
achieves optimal compression by jointly optimizing source
coding and channel coding within an end-to-end framework.
The powerful visual decoder is responsible for completing the
generation task at the receiver, while the MLM, enhanced
by a bridging module and prompt engineering, handles the
comprehension task. Extensive experiments demonstrate that
the proposed YOTO system achieves robust results. The YOTO
system achieves image reconstruction within 279.5 ms and

## PDF 第 15 页

Y AO et al.: YOU ONLY TRANSMIT ONCE: UNIFIED GENERATION AND COMPREHENSION FOR EFFICIENT SC 3363
TABLE V
SIMULATION PARAMETERS
attains PSNR values exceeding 30 dB in both AWGN and
Rayleigh channels when SNR is 6 dB. Moreover, it achieves
sentence similarity scores above 0.83 with channels’ SNR
ﬁxed at 10 dB. However, it is important to acknowledge the
current limitations of the YOTO framework. YOTO focuses on
single-image transmission and image-to-text comprehension,
ignoring the temporal dimension of videos. Future work will
extend the YOTO paradigm to video modalities. In summary,
this work provides critical insights and technical groundwork
for the development of future multimodal semantic com-
munication systems, which are expected to seamlessly inte-
grate generation capabilities with personalized comprehension
functionalities.
APPENDIX
DETAILED PARAMETER SPECIFICATIONS
In this appendix, we list all key model parameters and
hyperparameters of the YOTO system in the Table V below.
REFERENCES
[1] G. Shi, Y . Xiao, Y . Li, and X. Xie, “From semantic communication to
semantic-aware networking: Model, architecture, and open problems,”
IEEE Commun. Mag., vol. 59, no. 8, pp. 44–50, Aug.2021.
[2] K. Niu et al., “A paradigm shift toward semantic communications,”
IEEE Commun. Mag., vol. 60, no. 11, pp. 113–119, Nov.2022.
[3] J. Bao et al., “Towards a theory of semantic communication,” in Proc.
IEEE Netw. Sci. Workshop, Jun. 2011, pp. 110–117.
[4] X. Luo, H.-H. Chen, and Q. Guo, “Semantic communications: Overview,
open issues, and future research directions,” IEEE Wireless Commun.,
vol. 29, no. 1, pp. 210–219, Feb.2022.
[5] C. Liang et al., “Generative AI-driven semantic communication net-
works: Architecture, technologies, and applications,” IEEE Trans.
Cognit. Commun. Netw., vol. 11, no. 1, pp. 27–47, Feb.2025.
[6] S. Barbarossa, D. Comminiello, E. Grassucci, F. Pezone, S. Sardellitti,
and P. Di Lorenzo, “Semantic communications based on adaptive
generative models and information bottleneck,” IEEE Commun. Mag.,
vol. 61, no. 11, pp. 36–41, Nov.2023.
[7] T. Wu, Z. Chen, M. Tao, X. Xu, W. Zhang, and P. Zhang, “MambaJSCC:
Deep joint source-channel coding with visual state space model,” 2024,
arXiv:2405.03125.
[8] P. Esser, R. Rombach, and B. Ommer, “Taming transformers for high-
resolution image synthesis,” in Proc. IEEE/CVF Conf. Comput. Vis.
Pattern Recognit. (CVPR), Jun. 2021, pp. 12873–12883.
[9] A. van den Oord, O. Vinyals, and K. Kavukcuoglu, “Neural discrete
representation learning,” in Proc. Adv. Neural Inf. Process. Syst., 2017,
pp. 6306–6315.
[10] X. Zhang, D. Zhang, S. Li, Y . Zhou, and X. Qiu, “SpeechTokenizer:
Uniﬁed speech tokenizer for speech language models,” in Proc. Int.
Conf. Learn. Represent., 2024, pp. 31798–31818.
[11] Y . Xu, X. Yang, Y . Song, and C. Xu, “Libra: Building decoupled vision
system on large language models,” in Proc. Int. Conf. Mach. Learn.,
2024, pp. 55371–55388.
[12] G. Zhang, Q. Hu, Z. Qin, Y . Cai, G. Yu, and X. Tao, “A uniﬁed multi-
task semantic communication system for multimodal data,” IEEE Trans.
Commun., vol. 72, no. 7, pp. 4101–4116, Jul.2024.
[13] T. Han, Q. Yang, Z. Shi, S. He, and Z. Zhang, “Semantic-preserved
communication system for highly efﬁcient speech transmission,” IEEE
J. Sel. Areas Commun., vol. 41, no. 1, pp. 245–259, Jan.2023.
[14] F. Jiang et al., “Large AI model empowered multimodal semantic
communications,” IEEE Commun. Mag., vol. 63, no. 1, pp. 76–82,
Jan.2025.
[15] K. Pan et al., “Auto-encoding morph-tokens for multimodal LLM,” in
Proc. Int. Conf. Mach. Learn., 2024, pp. 39308–39323.
[16] D. Huang, F. Gao, X. Tao, Q. Du, and J. Lu, “Toward semantic
communications: Deep learning-based image semantic coding,” IEEE
J. Sel. Areas Commun., vol. 41, no. 1, pp. 55–71, Jan.2023.
[17] X. Peng et al., “A robust deep learning enabled semantic communication
system for text,” in Proc. IEEE Global Commun. Conf., Dec. 2022,
pp. 2704–2709.
[18] D. Caffagni et al., “The revolution of multimodal large language models:
A survey,” 2024, arXiv:2402.12451.
[19] M. Z. Hossain, F. Sohel, M. F. Shiratuddin, and H. Laga, “A compre-
hensive survey of deep learning for image captioning,” ACM Comput.
Surv., vol. 51, no. 6, pp. 1–36, Nov.2019.
[20] X. Yang, H. Yang, Y . Jiang, A. Alphones, and L. Xiao, “Game-
guided matching theory-based resource allocation for secure seman-
tic communications,” IEEE Trans. V eh. Technol. , vol. 74, no. 5,
pp. 8357–8362, May2025.
[21] Z. Tian, W. Wang, C. Zhang, and S. Yu, “Model-enabled task-oriented
semantic communications through knowledge synchronization,” IEEE
Trans. Cognit. Commun. Netw., vol. 11, no. 5, pp. 3371–3383, Oct.2025.
[22] X. Song et al., “UA V cognitive semantic communications enabled by
knowledge graph for robust object detection,” IEEE Trans. Commun.,
vol. 73, no. 8, pp. 6052–6067, Aug.2025.
[23] M. Li, W. Zuo, S. Gu, J. You, and D. Zhang, “Learning content-weighted
deep image compression,” IEEE Trans. Pattern Anal. Mach. Intell.,
vol. 43, no. 10, pp. 3446–3461, Oct.2021.
[24] Q. Fu, H. Xie, Z. Qin, G. Slabaugh, and X. Tao, “Vector quan-
tized semantic communication system,” IEEE Wireless Commun. Lett.,
vol. 12, no. 6, pp. 982–986, Jun.2023.
[25] T. Luddecke and A. Ecker, “Image segmentation using text and image
prompts,” in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit.
(CVPR), Jun. 2022, pp. 7086–7096.
[26] C.-H. Kao, Y .-C. Weng, Y .-H. Chen, W.-C. Chiu, and W.-H. Peng,
“Transformer-based variable-rate image compression with region-of-
interest control,” in Proc. IEEE Int. Conf. Image Process. (ICIP), Oct.
2023, pp. 2960–2964.
[27] A. Radford et al., “Learning transferable visual models from natural
language supervision,” in Proc. Int. Conf. Mach. Learn., vol. 139, 2021,
pp. 8748–8763.
[28] A. Balatsoukas-Stimming and C. Studer, “Deep unfolding for commu-
nications systems: A survey and some new directions,” in Proc. IEEE
Int. Workshop Signal Process. Syst. (SiPS), Nanjing, China, Oct. 2019,
pp. 266–271.
[29] R. Sennrich, B. Haddow, and A. Birch, “Neural machine translation of
rare words with subword units,” in Proc. 54th Annu. Meeting Assoc.
Comput. Linguistics, Aug. 2016, pp. 1715–1725.
[30] P. Anderson, B. Fernando, M. Johnson, and S. Gould, “SPICE: Semantic
propositional image caption evaluation,” in Proc. Eur . Conf. Comput.
Vis.Cham, Switzerland: Springer, 2016, pp. 382–398.
[31] A. Rohrbach, L. A. Hendricks, K. Burns, T. Darrell, and K. Saenko,
“Object hallucination in image captioning,” in Proc. Conf. Empirical
Methods Natural Lang. Process., 2018, pp. 4035–4045.
[32] C. Hutto and E. Gilbert, “V ADER: A parsimonious rule-based model
for sentiment analysis of social media text,” in Proc. Int. AAAI Conf.
Web Social Media, vol. 8, May 2014, pp. 216–225.
[33] J. Jiao et al., “VMamba: Visual state space model,” in Proc. Adv. Neural
Inf. Process. Syst., 2024, pp. 103031–103063.

## PDF 第 16 页

3364 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 44, 2026
[34] H. Guo, J. Li, T. Dai, Z. Ouyang, X. Ren, and S. Xia, “MambaIR: A sim-
ple baseline for image restoration with state-space model,” in Proc. Eur .
Conf. Comput. Vis.Cham, Switzerland: Springer, 2024, pp. 222–241.
[35] L. Sun, J. Dong, J. Tang, and J. Pan, “Spatially-adaptive feature
modulation for efﬁcient image super-resolution,” in Proc. IEEE/CVF
Int. Conf. Comput. Vis. (ICCV), Oct. 2023, pp. 13144–13153.
[36] J. Ball ´e, V . Laparra, and E. P. Simoncelli, “Density modeling of images
using a generalized normalization transformation,” in Proc. Int. Conf.
Learn. Represent., 2015, pp. 1–14.
[37] C. Zou, F. Yang, J. Song, and Z. Han, “Channel autoencoder for wireless
communication: State of the art, challenges, and trends,” IEEE Commun.
Mag., vol. 59, no. 5, pp. 136–142, May2021.
[38] K. Yang, S. Wang, J. Dai, X. Qin, K. Niu, and P. Zhang, “SwinJSCC:
Taming Swin transformer for deep joint source-channel coding,” IEEE
Trans. Cognit. Commun. Netw., vol. 11, no. 1, pp. 90–104, Feb.2025.
[39] A. Li, F. Li, Y . Liu, R. Cong, Y . Zhao, and H. Bai, “Once-for-all:
Controllable generative image compression with dynamic granularity
adaptation,” 2024, arXiv:2406.00758.
[40] T. Celik, “Spatial entropy-based global and local image con-
trast enhancement,” IEEE Trans. Image Process., vol. 23, no. 12,
pp. 5298–5308, Dec.2014.
[41] E. Jang, S. Gu, and B. Poole, “Categorical reparameterization with
gumbel-softmax,” in Proc. Int. Conf. Learn. Represent., 2016, pp. 1–13.
[42] J. Li, D. Li, S. Savarese, and S. C. H. Hoi, “BLIP-2: Bootstrap-
ping language-image pre-training with frozen image encoders and
large language models,” in Proc. Int. Conf. Mach. Learn., 2023,
pp. 19730–19742.
[43] F. Locatello et al., “Object-centric learning with slot attention,” in Proc.
Adv. Neural Inf. Process. Syst., 2020, pp. 11525–11538.
[44] J. E. Hu et al., “LoRA: Low-rank adaptation of large language models,”
in Proc. Int. Conf. Learn. Represent., 2021, p. 3.
[45] K. Zhou, J. Yang, C. C. Loy, and Z. Liu, “Learning to prompt for vision-
language models,” Int. J. Comput. Vis., vol. 130, no. 9, pp. 2337–2348,
2022.
[46] N. Wang, J. Xie, J. Wu, M. Jia, and L. Li, “Controllable image captioning
via prompting,” in Proc. AAAI Conf. Artif. Intell., 2023, vol. 37, no. 2,
pp. 2617–2625.
[47] X. Li et al., “LG-VQ: Language-guided codebook learning,” in Proc.
Adv. Neural Inf. Process. Syst. 37, 2024, pp. 139700–139724.
[48] J. Yang et al., “Uniﬁed contrastive learning in image-text-label space,”
in Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recogn., Jun. 2022,
pp. 19163–19173.
[49] T. Lin et al., “Microsoft COCO: Common objects in context,” in Proc.
Eur . Conf. Comput. Vis., 2014, pp. 740–755.
[50] R. Varghese and M. Sambath, “YOLOv8: A novel object detection
algorithm with enhanced performance and robustness,” in Proc. Int.
Conf. Adv. Data Eng. Intell. Comput. Syst. (ADICS), Apr. 2024, pp. 1–6.
[51] A. P. Mathews, L. Xie, and X. He, “SentiCap: Generating image
descriptions with sentiments,” in Proc. AAAI Conf. Artif. Intell., 2016,
vol. 30, no. 1, pp. 3574–3580.
[52] H. Xie, Z. Qin, G. Y . Li, and B.-H. Juang, “Deep learning enabled
semantic communication systems,” IEEE Trans. Signal Process.,
vol. 69, pp. 2663–2675, 2021.
[53] R. Mokady, A. Hertz, and A. H. Bermano, “ClipCap: CLIP preﬁx for
image captioning,” 2021, arXiv:2111.09734.
