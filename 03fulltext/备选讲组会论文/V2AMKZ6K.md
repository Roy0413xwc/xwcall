---
type: literature-fulltext
title: "Radio Map Prediction From Aerial Images and Application to Coverage Optimization"
zotero_key: "V2AMKZ6K"
pdf_key: "YNFJHDHR"
doi: "10.1109/TWC.2025.3583171"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Radio Map Prediction From Aerial Images and Application to Coverage Optimization.md"
fulltext_path: "03fulltext/备选讲组会论文/V2AMKZ6K.md"
zotero_item: "zotero://select/library/items/V2AMKZ6K"
zotero_pdf: "zotero://open-pdf/library/items/YNFJHDHR"
source_type: "pypdf direct PDF text extraction"
page_mapping: verified by PDF page index
---

# Radio Map Prediction From Aerial Images and Application to Coverage Optimization

> PDF 原文逐页文本抽取；来源文件 SHA-256：`36a96471722a9274cd103ba3409994731c5e98bb1a11d61f1b5a61b17e264b40`。抽取页码按 PDF 页序号标记。

## PDF 第 1 页

308 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Radio Map Prediction From Aerial Images and
Application to Coverage Optimization
Fabian Jaensch
 , Giuseppe Caire
 , Fellow, IEEE, and Beg ¨um Demir
 , Senior Member, IEEE
Abstract—Several studies have explored deep learning algo-
rithms to predict large-scale signal fading, or path loss, in
urban communication networks. The goal is to replace costly
measurement campaigns, inaccurate statistical models, or com-
putationally expensive ray-tracing simulations with machine
learning models that deliver quick and accurate predictions. We
focus on predicting path loss radio maps using convolutional
neural networks, leveraging aerial images alone or in combination
with supplementary height information. Notably, our approach
does not rely on explicit classiﬁcation of environmental objects,
which is often unavailable for most locations worldwide. While
the prediction of radio maps using complete 3D environmental
data is well-studied, the use of only aerial images remains
under-explored. We address this gap by showing that state-of-
the-art models developed for existing radio map datasets can
be effectively adapted to this task. Additionally, we introduce
a new model dubbed UNetDCN that achieves on par or better
performance compared to the state-of-the-art with reduced com-
plexity. The trained models are differentiable, and therefore they
can be incorporated in various network optimization algorithms.
While an extensive discussion is beyond this paper’s scope, we
demonstrate this through an example optimizing the directivity of
base stations in cellular networks via backpropagation to enhance
coverage.
Index Terms —Convolutional neural networks, machine
learning, path loss, radio map, RSSI, coverage.
I. I NTRODUCTION
W
IRELESS communication systems are fundamentally
based on radio waves radiated by a transmitter
(Tx) antenna carrying a signal to send information to a
receiving (Rx) antenna. To model the effects of the propagation
channel between Tx and Rx, it is convenient to distinguish
between “small-scale” and “large-scale” effects. The small-
scale effects are due to the constructive/destructive interference
between the propagation paths that add with different phases,
amplitudes, and delays at the Rx antenna. This results in a
time and frequency selective fading process usually modeled
Received 26 September 2024; revised 10 February 2025 and 5 May 2025;
accepted 21 June 2025. Date of publication 2 July 2025; date of current
version 22 December 2025. The work of Fabian Jaensch and Giuseppe Caire
was supported by the Bundesministrium f ¨ur Bildung und Forschung (BMBF)
Germany in the Program of “Souver ¨an. Digital. Vernetzt.” Joint Project 6G-
RIC under Project 16KISK030. The associate editor coordinating the review
of this article and approving it for publication was Y . Shu. (Corresponding
author: Fabian Jaensch.)
Fabian Jaensch and Giuseppe Caire are with the Communications and
Information Theory Group, Technische Universit ¨at Berlin, 10623 Berlin,
Germany (e-mail: f.jaensch@tu-berlin.de).
Beg¨um Demir is with the Remote Sensing Image Analysis Group, Technis-
che Universit¨at Berlin, 10623 Berlin, Germany, and also with Berlin Institute
for the Foundations of Learning and Data (BIFOLD), 10623 Berlin, Germany.
Digital Object Identiﬁer 10.1109/TWC.2025.3583171
as a correlated Gaussian random process with normalized
second moment. In contrast, the large-scale effects capture the
attenuation of the received signal power, or path loss. This
attenuation depends on distance-dependent power dissipation
in free space, reﬂections from building and street surfaces,
and attenuation by tree canopies. To capture this quantity, we
consider the radio map of a transmitter consisting of the path
loss values for different potential Rx locations of interest.
Important applications of radio maps include the optimiza-
tion of cellular network layout to achieve good coverage of
an area (Section IV), link scheduling [1], localization of user
equipment (UE) based on RSS measurements at the Rx [2]
or, in the context of 5G and 6G, beam management [3]. Since
measurement campaigns are impractical and too expensive
on a large scale, different methods have been developed to
approximate the path loss. Statistical path loss models that
express the attenuation solely as a function of the distance
between Tx and Rx and additional stochastic effects are
inherently unable to capture the radio wave propagation in
a speciﬁc environment. Ray-tracing simulations provide an
option to approximate the underlying physical phenomena
with high accuracy [4]. However, due to the relatively long
run times of the simulations and the need for detailed 3D city
models, they can be infeasible for applications in real time or
on large scale.
Recently, several works have explored the application of
machine learning (ML) algorithms and, in particular, deep
neural networks (DNNs) to the path loss prediction problem.
The general idea is that a properly designed ML model
can learn the underlying physical phenomena of radio wave
propagation to a certain extent, given a sufﬁcient amount of
training data. Albeit the training process can be very time- and
resource-intensive, the run time of the inference task once the
model is deployed is typically in the order of milliseconds.
This opens up a range of applications in which statistical
path loss models are too inaccurate and ray-tracing is too
slow, [5], [6]. Additionally, DNNs are a very ﬂexible tool for
extracting information and patterns implicitly from data. We
show that convolutional neural networks (CNN) are capable
of implicitly extracting information about the presence, shape,
and height of buildings and trees that is necessary to determine
radio maps from aerial images.
In the remainder of this Section, we give an account of
the relevant literature for radio map prediction, in particular
using deep learning, and a comparison to our contributions.
Section II reviews some necessary wireless communication
background to precisely deﬁne the investigated problem, fol-
© 2025 The Authors. This work is licensed under a Creative Commons Attribution 4.0 License.
For more information, see https://creativecommons.org/licenses/by/4.0/

## PDF 第 2 页

JAENSCH et al.: RADIO MAP PREDICTION FROM AERIAL IMAGES AND APPLICATION 309
lowed by a description of the generation of the dataset,
CNN architectures and other aspects of the experiments. In
Section III, we discuss the results on radio map prediction
and provide an ablation study for the proposed UNetDCN.
Lastly, Section IV showcases applications to network coverage
optimization and Section V ﬁnishes with the conclusions.
A. General Approach and Related Works
A common way to model the path loss is to use the log
normal shadowing models in different variations (e.g. the
3GPP model described in [7]). They originate from the idea
to express the path loss merely as a function of the distance
between Tx and Rx and to model deviations as the realization
of a Gaussian random variable in the log (dB) domain. Albeit
the resulting graph of the function together with the stochastic
spread may ﬁt measurement points, these models completely
disregard the radio wave propagation in a speciﬁc environment
along speciﬁc paths.
Ray-tracing [8] provides a more accurate, site-speciﬁc solu-
tion by modeling electromagnetic waves as rays launched in a
very ﬁne subdivision of the space around the Tx. Reﬂections
from surfaces and potentially other effects such as diffractions
or transmissions are calculated upon contact with objects [4].
The rays arriving at the Rx are combined to generate the path
loss as deﬁned in Section II-A, (1), or other channel state
information. As mentioned before, potential drawbacks for
certain applications are the runtime of typically at least several
seconds to generate a complete radio map and the need to have
a complete 3D model of the environment available.
Other methods include completing the radio map from
sparse measurements [9] or estimating the path loss for a single
Rx position at a time via ML [10].
In the following, we describe approaches to predict the
whole radio map at once using ML. Each pixel in the target
radio map, represented by a two-dimensional image, corre-
sponds to a different location in the considered environment
from a birds-eye perspective, and its value is the path loss
on an appropriate scale. The input information about the
presence and potentially height of objects like buildings or
trees, the transmitter position, and possibly other parameters
that differ from sample to sample are usually encoded in two-
dimensional images of the same shape as the target and stacked
along an additional channel dimension. All works described
in the following build on CNN models [11], which have
been shown to be effective in other tasks such as semantic
segmentation, image denoising, or image-to-image translation
that are structurally similar in the sense that input and output
of the model are image-like tensors.
A ﬁrst seminal contribution investigating the prediction
of the whole radio map at once using CNNs came out of
our research group [12] and considered a UNet [13] model
trained in a supervised manner to approximate radio maps
generated with two-dimensional ray-tracing from city maps
and Tx locations. The presence or absence of buildings and
the Tx are encoded in binary input images. The authors
explore strategies to incorporate available signal measurements
and adapt the trained models to more realistic scenarios
and show applications to coverage estimation and ﬁngerprint
localization. Several other works have extended this approach
to the more challenging scenario of radio maps generated
with 3D ray-tracing, e.g. [14], [15], [16]. In these works,
the binary input information per pixel is usually replaced by
height information. Some works have experimented with more
variables between the different samples encoded in additional
inputs, for example the carrier frequency of the transmitted
signal [16] or antenna patterns and orientations [14]. Albeit
the basic encoder-decoder with skip-connections design of the
UNet has been used in most works since then, it has been soon
recognized that standard UNets are inherently limited when
it comes to propagating information over longer distances,
which is especially important to accurately predict reﬂections.
Several approaches make use of dilated convolutions [17] to
increase the receptive ﬁeld [5], [18], [19], whereas in [16]
vision transformer layers [20] are added to the CNN to allow
modeling long-range relationships. Besides changes to the net-
work architecture, some authors propose feature engineering
to resolve the described problem and improve the accuracy.
In [21], the network is provided with an input image containing
the spatial distance of each pixel position to the transmitter
location. The authors of [16] propose to feed the coordinates
of each pixel and the Tx to the network in all positions. To
show the validity of training CNNs on simulated data, in [14]
a model tested ﬁrst on radio maps generated by ray-tracing is
retrained on real-world measurements and shown to perform
better than all conventional methods.
Only one work we are aware of investigates path loss
prediction for a whole area from aerial images [22]. The
scenario considered in that study differs from ours as Tx
are mounted on autonomous aerial vehicles (UA V) instead of
buildings, and the developed model seems rather inaccurate
with RMSE over 43dB.
The authors of [5] and [12] regard general application of
radio maps to coverage area classiﬁcation and UE localization,
which are not speciﬁcally requiring DNNs. In [15] it is
shown that by making use of the fast inference speed of the
trained model, a large number of combinations of potential Tx
locations can be evaluated quickly in terms of the coverage
provided in an area, reducing the time needed to ﬁnd the
optimal combination signiﬁcantly compared to using ray-
tracing. A review on more applications is provided in [6].
B. Our Contribution
We investigate the prediction of radio maps from aerial
images and potentially unclassiﬁed height maps for scenar-
ios in which a complete 3D model of the environment is
not available. The radio map is only determined from the
information about the environment and the Tx. In particular,
contrary to some other works, we do not assume measure-
ments to be available. Our results (RMSE of 6.7dB without
height information and 5.2dB with height information) show
a signiﬁcant improvement over the only other work we are
aware of considering a similar scenario (44dB in [22]).
For this purpose, we have generated city geometries
from real places in the city of Berlin and conducted ray-
tracing simulations to obtain a large collection of path loss
maps modeling typical urban cellular networks, described in

## PDF 第 3 页

310 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE I
OVERVIEW OF OPEN RADIO MAP DATASETS
Section II-B. In contrast to the other publicly available radio
map datasets we are aware of [5], [12], and [23], ours is
the ﬁrst one to feature directional antennas at the Tx and
to include trees and realistic building heights with approx-
imated roof shapes taken from the real world as well as
aerial images. Table I provides an overview of the similarities
and differences between other openly accessible datasets and
ours.1
We perform experiments with different CNN architectures
and input features in order to encode the city geometry, the
relative position of the Tx to locations on the map, and the
Tx antenna characteristics, including several ideas proposed
in the literature (Section II-C2). Lastly, we consider the usage
of deformable convolutional layers [25] for the radio map
prediction task and show that our proposed model achieves
the same or higher accuracy as the state of the art, depending
on the scenario, with reduced complexity.
In Section IV, we show how a trained model can be
used to solve an optimization problem in a cellular network.
In contrast to applications in previous works, such as [15],
where the fast inference speed of the trained network is used
to optimize BS deployment via exhaustive search over all
possible combinations of locations, we also take advantage
of backpropagation through a trained and frozen network.
This allows us to directly optimize input parameters deﬁned
as trainable variables with respect to some loss or score
function calculated from the predicted radio maps via gra-
dient descent. Although this technique has been used in e.g.
inverse material design [26], we are not aware of previous
usage in our ﬁeld. Note that the optimization of antenna
characteristics and materials is also possible with the recently
developed ray-tracer Sionna [27]. Our approach, however,
does not require a 3D model of the environment and works
just with aerial images as inputs, whereas Sionna requires
an explicit 3D model as input. Additionally, optimization
using our models is signiﬁcantly faster than with Sionna,
which has to recalculate the radio map via ray-tracing in each
iteration [28].
1The dataset and some numerical comparisons of model architectures and
input features have already been presented in our preprint [24]. For this paper,
we have focused more deeply on the investigation of prediction from images,
reﬁned our model architecture, and added the investigation of applications to
network coverage optimization. Our dataset can be found at https://zenodo.org/
records/13834313, the code at https://github.com/fabja19/RML v2 img
II. S YSTEM AND METHODOLOGY
A. Wireless Communication Background
Consider a Tx-Rx pair in a ﬁxed environment with n paths
establishing the link from the Tx to the Rx. These may
include a direct line-of-sight path and multipaths undergoing
reﬂections from surfaces such as the ground or building walls
and diffractions around edges or corners of objects. In our
simulation scenario described in Section II-B, we assume that
the wavelength of the communication signal is signiﬁcantly
smaller than the accuracy of spatial positions and shapes of
objects in the environment. This implies that it is impossible
to model the phase differences between different paths appro-
priately, and any small-scale fading due to constructive and
destructive interference between paths arriving with different
phase shifts is modeled as a random effect. In fact, in standard
wireless communication theory it is customary to separate the
large-scale path loss from the small-scale random fading and
consider normalized statistics for the latter (e.g., Rayleigh or
Rician fading with unit second moment, see [29]).
We consider a time-varying uncorrelated scattering
model [30] with transfer function
H(t,f ) =
n∑
p=1
cpejψpej2πνpte−j2πfτ p,
where cp ∈ C is the complex amplitude of the p-th path
coefﬁcient,ψp the corresponding phase factor that depends on
the radio between the path lengthdp and the carrier wavelength
λ, νp is the Doppler shift, τp the delay, t,f denote time and
frequency, respectively, and j is the imaginary unit. We deﬁne
the ratio between received and transmitted power, i.e., the
channel power attenuation or path loss, as
PR
PT
=
n∑
p=1
E
[
|cp|2], (1)
in order to capture the large-scale fading and average out
random ﬂuctuations. More precisely, since the coefﬁcients cp
are the result of a large number of microscopic multipath
components adding with slightly different phases, they are
modeled as complex circularly symmetric random variables
cp∼CN (µp,σ 2p)
such that E[|cp|2] = |µp|2 + σ2p is the power attenuation
along the p-th path. In addition, since the phase ψp depends

## PDF 第 4 页

JAENSCH et al.: RADIO MAP PREDICTION FROM AERIAL IMAGES AND APPLICATION 311
on dpλ , and since 2πdpλ mod 2π can be any number in [0, 2π]
depending on the very exact details of the environment, it is
reasonable to model these phases as mutually independent,
independent of the cp, and uniformly distributed in [0, 2π].
Therefore, φp−φq is uniformly distributed over [0, 2π] for
p⁄=q and it follows that
E[|H(t,f )|2]
=
n∑
p,q=1
E[cpc∗qej(cp−cq)]ej2π(νp−νq)te−j2π(τp−τq)f
=
n∑
p=1
E[|cp|2], (2)
where ·∗ denotes the complex conjugate, thus justifying
deﬁnition (1) for the large-scale path loss.
We notice here that the ensemble expectation in (2) can also
be justiﬁed in terms of local averaging over time and frequency
of the instantaneous received signal power. In fact, in practice,
the received signal power is always measured at the receiver
as a local average. Even if the coefﬁcients cpejφp are not
modeled as random variables, but are completely deterministic,
considering a time window of duration T and the channel of
bandwidth W, we have
PR
PT
= 1WT ∫ T0 ∫ W/2−W/2|H(t,f )|2 dt df
= 1WT ∫ T0 ∫ W/2−W/2 n∑p,q=1cpc∗qej(φp−φq)ej2π(νp−νq)t
×e−j2π(τp−τq)f dt df
≈
n∑
p=1
|cp|2
since
1
T
∫ T
0
ej2π(νp−νq)t dt≈ 0
for all νp⁄=νq when|νp−νq|> 1/T , i.e., when the time
variations due to the Doppler spread are signiﬁcant over the
averaging interval, and
1
W
∫ W/2
−W/2
e−j2π(τp−τq)f df≈ 0
for all τp ⁄= τq when|τp− τq| > 1/W , i.e., when the
frequency variations due to the delay spread are signiﬁcant
over the channel bandwidth. Note also that if two paths
have both Doppler shift difference less than 1/T and delay
difference less than 1/W , then they can be counted as a single
path since they are indistinguishable [31]. Hence, the above
conditions are always satisﬁed for all distinguishable paths.
We conclude that whether we model the path coefﬁcients
as uncorrelated random variables and adopt the deﬁnition of
average power as an ensemble average, or model them as
deterministic quantities and use the deﬁnition of average power
as a local time-frequency average, the macroscopic path loss
is consistently deﬁned as the sum of the squares (or the sum
of the second moments) of the path coefﬁcients.
Fig. 1. Sample from the dataset -(a) aerial image (b) nDSMs of buildings
(red) and vegetation (green) overlaid, with darker colors corresponding to
greater height values (c) 3D model in simulation with Tx (green cube) and
different orientations of the antenna main lobe (red lines) (d) example of a
radio map.
The radio map of the Tx for a ﬁxed set D⊂ R2 of locations
of interest may now formally be deﬁned as a function RM :
D → R, which maps each location to the path loss value
for an Rx in the considered position according to (1). In the
following, we will only consider the case that D corresponds
to a uniform grid over a square-shaped area. This allows us
to regard the radio map as a matrix or image.
As elaborated in [12], it is reasonable to truncate the path
loss from below at a threshold corresponding to the noise ﬂoor,
as lower power levels are irrelevant in practice, and to work
with powers and losses in dB scale, see Section II-B2.
B. Dataset
Our dataset consists of 74,515 radio maps simulated using
ray-tracing on 424 city maps from Berlin. The environment
data and the radio maps cover an area of 256m ×256m with a
spatial resolution of 1m. For each city map, several potential
Tx locations on the corners and edges of building rooftops
were identiﬁed. Simulations were conducted for each location
using different antenna characteristics and orientations.
1) City Maps: Our goal was to simulate cellular net-
works in urban environments corresponding to places in the
real world and featuring buildings with realistic shapes and
heights and also trees. Although a few public institutions
provide open 3D models of certain cities, municipalities, or
even whole countries, we could not ﬁnd any that contained
information about foliage. However, available height maps or
digital surface models (DSMs) lack the necessary classiﬁcation
of objects into buildings, vegetation, and ground. We have
therefore decided to generate a new dataset of city maps from
raw airborne light detection and ranging (LiDAR) point clouds
provided by the Geoportal Berlin [32]. Using the software
LAStools [33], we have automatically separated the point
clouds into the classes ground, building, and vegetation. The
recognition of buildings has been further improved by incorpo-
rating building footprints from [32], categorizing all elevated
(above-ground) points inside the footprints as buildings. From
there we extracted normalized digital surface models (nDSM),
representing the height above the ground for the two classes
buildings and vegetation. Since Berlin shows a small deviation
in elevation in most areas, we approximated the ground as a
ﬂat surface and normalized the heights of objects relative to it.
2) Radio Map Simulations: The ground truth radio maps
were generated with the GPU accelerated X3D propaga-
tion model in the widely used ray-tracing software Wireless

## PDF 第 5 页

312 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
TABLE II
ANTENNA PARAMETERS
Fig. 2. 3D plot of antenna radiation patterns. The values in bracket indicate
the half power beam width and ﬁrst null beam width, respectively.
InSite [34]. Since it was impossible to determine the exact
materials of speciﬁc houses or types of trees, we have chosen
standard material types for these upon import to the simulation
software. The nDSMs have been converted to polygons for the
simulations by grouping up neighboring pixels with approx-
imately the same height and interpolating the boundaries.
The ground and all buildings are assumed to represent solid
structures, allowing reﬂections from surfaces and diffractions
around edges but blocking transmissions. Vegetation on the
other hand is modeled as a solely attenuating material. Exploit-
ing that the exact shape of foliage objects is therefore less
important, we have chosen less accurate interpolation for the
vegetation layers upon constructing the polygons. By doing
so, we could signiﬁcantly reduce the runtime, which depends
heavily on the number of faces in the environment geometry,
and hence generate a larger dataset.
To simulate a realistic cellular environment, Tx that model
cellular base stations were placed on the edges of buildings at
a height of 2m from the roof and restricted to heights between
6m and 30m above the ground. A dense grid of receivers with
isotropic antennas and a spacing of 1m at a height of 1.5m was
deﬁned to model typical UE in the network, e.g. smartphones
of people walking on the sidewalks or devices in cars.
For the Tx, we have selected the directional antenna type
in the ray-tracing software. It allows to simulate an idealized
main beam without any side lobes. By adjusting the parameters
half power beam width and ﬁrst null beam width, it can model
very narrow beams or antennas covering wider sectors. For
each Tx position, we test several combinations of azimuth and
tilt angles in the direction pointing away from the building,
on which the Tx is placed, with a line of sight algorithm.
Orientations that do not cover at least a certain area on the
ground are disregarded. For all angle combinations found,
we select one of the narrow and one of the wide antenna
patterns in Table II. Although on each city map we consider
different Tx positions and orientations, each of them is used in
a separate simulation, resulting in a different radio map with
a single Tx per data sample.
In Table III we list further parameters. Note that only the
values in the upper part of the table are used to conﬁgure
TABLE III
SIMULATION AND DATASET PARAMETERS
the ray-tracing simulations, whereas the values below are
calculated or assumed for post-processing, as described below.
The simulation output are the magnitudes of the channel
coefﬁcients at each Rx on the grid, which we use to calculate
the path loss (1). The path loss values are converted to
dB-scale and rescaled and cut following [12]. Assuming a
bandwidth of B = 10 MHz, thermal noise power spectral
density (N0)dBm/ Hz = −174 dBm/ Hz and an idealistic
noise ﬁgure of (NF)dB = 0dB at the Rx (Table III), the noise
ﬂoorN is calculated as
(N )dB
= 10· log10(B) + (N0)dBm/ Hz + (NF)dB =−127dB.
We are interested in locations where the received signal
satisﬁes a signal-to-noise ratio of at least (SNR)dB = 0dB, i.e.
where the path loss is greater than or equal to the threshold
(PLthr)dB =−(PT)dBm + (SNR)dB + (N )dB =−127dB.
Any signal arriving with a path loss below this threshold is
irrelevant in practice, but it may be beneﬁcial for the model
to also see values slightly below it during training in order to
understand propagation phenomena better. Therefore, we cut
off the path loss values at a second threshold PLtrnc, which
is chosen so that
(PLmax)dB− (PLthr)dB≈ 4 ((PLthr)dB− (PLtrnc)dB),
where (PLmax)dB = −50dB is the largest path loss value
occurring across our dataset, which yields (PLtrnc)dB =
−147dB. Finally, the values are mapped with an afﬁne-linear
transformation to the interval [0, 1] so that PLtrnc and PLmax
correspond to 0 and 1, respectively, to obtain the radio map as
a grayscale image. The rescaling assures that, in contrast do
dB-scale, the most relevant parts of the radio map containing
strong signal dominate parts with very low signal in terms of
magnitude.
3) Other Data: We also include images from [35] taken
about 2 months after the LiDAR measurements, cut and down-
scaled to match the position and resolution of the nDSMs.
Furthermore, the dataset contains 2D polygons with height

## PDF 第 6 页

JAENSCH et al.: RADIO MAP PREDICTION FROM AERIAL IMAGES AND APPLICATION 313
Fig. 3. Illustration (inspired by [25]) of sampling points in standard, dilated
and deformable convolution with kernel size 3 × 3.
attributes extracted from the nDSMs, which have been used
for the ray-tracing simulations. Files containing line-of-sight
information for each radio map are also included but not
considered in this work.
C. Experiment Design
1) CNN-Architectures: As a lightweight baseline model, we
use the RadioUNet [12], more concretely the ﬁrst part of the
WNet described by the authors. In principle, it follows the
structure of the original UNet [12], but it features more down
and upsampling layers and, in some parts, convolutions with
a larger kernel size, allowing to propagate information over
longer distances. As a second baseline, we include experi-
ments with the PMNet proposed in [5], featuring a relatively
deep encoder consisting of stacked ResNet-layers and several
parallel convolutional layers with varying dilation [17] after
the encoder. PMNet has been shown to perform better than
RadioUNet and other architectures on different datasets [5],
[36]. These were the only architectures designed for the radio
map prediction task available in the literature, for which the
code has been made publicly available.
We propose the use of a model dubbed UNetDCN that com-
bines the structure of UNet [13] with deformable convolutions.
Originally presented in [25], this CNN layer has been used
in several computer vision problems, but, to the best of our
knowledge, we are the ﬁrst ones to apply it for radio map
prediction. Similar to a dilated convolution, it allows to enlarge
the receptive ﬁeld by sampling the input at positions further
away. The sampling points are not ﬁxed (Fig. 3), instead, the
offset compared to a standard convolution is computed from
the input with learnable parameters. Intuitively, this should
make it easier to propagate information in arbitrary directions
compared to dilated convolutions. Furthermore, in comparison
to standard convolutions with a large kernel size, deformable
convolutions require less parameters and numeric operations.
The architecture is illustrated in Fig. 4 and the exact imple-
mentation can be found on our GitHub page mentioned in
Section I. Many aspects of the network are similar to the
original UNet [13], such as repeated convolutions increasing
the channel dimension and max pooling reducing the spatial
dimension in the encoder part, upsampling and simultaneous
reduction of the channel dimension in the decoder part and
skip connections from the encoder to the decoder at several
stages to preserve information. The main changes on the other
hand are the replacement of some standard convolutions by
deformable convolutions, additional batch normalization and
residual connections. In Section III-A, we provide an ablation
study investigating the choice of the hyperparameters in Fig. 4
and the use of deformable convolutions.
Fig. 4. Outline of the UNetDCN architecture. The numbers on the left
describe the spatial dimensions and the numbers on top the channel dimension
of the tensors, represented as gray blocks. In our experiments, H = W =
256, Cout = 1, Cin depends on the chosen inputs and the width and depth
hyperparameters are set to C = 32 , d = 3 . Blocks of network layers are
depicted by arrows, and explained below. The channel dimension is always
changed by the ﬁrst convolution inside of each block. The layers used are
standard 3 × 3 convolutions (Conv), batch normalization ( BN), rectiﬁed linear
unit ( ReLU), residual connections ( res), concatenation of tensors along the
channel dimension (cat), downsampling with 2 × 2 MaxPool and upsampling
with 2 × 2 transposed convolutions (ConvT).
TABLE IV
COMPLEXITY OF THE CONSIDERED ARCHITECTURES FOR THE DEFAULT
INPUTS AND BATCH SIZE 1. aCALCULATED USING DEEP SPEED [37]
Table IV compares the complexity of the different architec-
tures across various aspects. PMNet exhibits the highest com-
plexity in terms of multiply-accumulate operations (MACs)
and number of parameters. The proposed UNetDCN has the
smallest number of parameters, resulting in a minimal memory
footprint, while its MAC count is slightly higher than that of
RadioUNet.
2) Input Features: Following the related literature
(Section I-A), we aim to encode all relevant parameters that
change between the different simulations in 2D images, with
each pixel representing a speciﬁc location on the map. In the
following, we provide an explanation of the input features we
consider. Several examples for a sample from the dataset are

## PDF 第 7 页

314 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 5. Example radio map (a) and (normalized) input features. (b) Tx location (visibility enhanced, in reality only marked by one pixel), (c) aerial image,
(d) nDSM, (e) 2D distance to Tx, (f) azimuth angle, (g), (h) map coordinates from GA [16], (i) Tx antenna pattern projected onto the ground.
shown in Fig. 5, and further details of the implementation
can be found in the code. All inputs are normalized to values
in [−1, 1] before being fed to the CNN.
In the 2D setting, the positions of the Tx, buildings, and
potentially other objects are often given in a one-hot encoding
in separate binary tensors, where a 1 indicates the presence of
the Tx or object and a 0 absence in the location corresponding
to each pixel (see e.g. [12]). Since in our work the height of
the Tx, buildings, and vegetation are relevant, we assign these
as the values to the pixels instead, as it is done in [15] or
[16] for example (Fig. 5(b)-(h)). The sparsity of the tensor
representing the Tx location is potentially problematic, as the
standard layers used in CNNs inherently have a very limited
ﬁeld of view, and it therefore takes several convolutional and
downsampling operations to spread the information to other
parts of the map.
The authors of [16] propose to tackle this issue by mak-
ing the information about the spatial position of each pixel
together with the location of the Tx explicitly available to the
model in the form of constant input tensors for the x,y and z
coordinates of the Tx and two tensors showing the x and y
coordinates of each pixel. Although they state that their main
intention was to ﬁnd an alternative to the usual positional
embedding in vision transformer layers, we have found that
this approach also improves the performance of other CNN
models. They denote their idea as Grid Anchor (GA). Addi-
tionally, we provide the azimuth angle between the direction
the Tx is pointing at and the straight line to each point of
the map, as in [14]. This encodes Tx directivity and helps
determine whether two objects lie along the same path. Lastly,
we also include the distance in the x−y plane from the Tx
to each point as in [21]. All these inputs related to positions
on the maps are together denoted as coords in Sec. III.
To link the antenna pattern to the spatial positions, we use
spherical coordinates centered in the Tx location and rotated
according to the Tx orientation to look up the gain in dB
corresponding to azimuth and tilt angle for each point on the
ground, as it is done in [14] as well.
As described in the introduction, precise information about
the locations, heights, and shapes of buildings, and especially
vegetation is scarce. Aerial imagery, on the other hand, is
an, in many cases, easier accessible data source which at
least partially contains this information implicitly. We perform
experiments to see to what extent the models are capable
of predicting the radio map from just images or potentially
with additional sight information. Intuitively, this requires
the models to implicitly perform a semantic segmentation,
i.e. pixel-wise classiﬁcation, of the input image in order
to ﬁnd objects relevant for the signal propagation and to
estimate the heights of the found objects. The images contain,
besides the usual RGB channels, an infrared channel, which
we include by default. Performance without it is also tested
(w/o IR ). Lastly, we additionally provide the networks with
an unclassiﬁed nDSM depicting elevation of buildings and
vegetation together, as this kind of information is easier to
acquire than height maps for each class individually.
III. R ESULTS ON RADIO MAP PREDICTION
We use about 80% of the samples as the training set, 10%
for validation, and 10% for testing, ensuring that the city maps
do not overlap between the different sets. The validation set is
applied to ﬁrst reduce the learning rate and later stop training
when the loss stagnates, and to determine the best model
weights to save. The test set is only used at the very end to
evaluate the ﬁnal performance and generalization capability.
During training, we apply random ﬂips and rotations as data
augmentations.
All models are trained with respect to mean-squared error
(MSE) between the predicted and ground truth radio maps. We
measure the ﬁnal performance in terms of root-mean-square
error (RMSE) in grayscale. Recall that the grayscale radio map
values in [0, 1] stem from an afﬁne transformation of the pos-
sible path loss values in dB, which lie in [−127dB,−50dB],
hence, the RMSE in dB can be obtained from multiplying the
RMSE in grayscale by a factor of 77. Furthermore, we report
the normalized mean-squared error (NMSE) after conversion
to dB scale, which emphasizes the importance of samples with
a high signal power (see [12]).
Our code is implemented in PyTorch Lightning. All models
are trained with a batch size of 32 using the Adam optimizer
with an initial learning rate of 10−4 on A100 GPUs. Typically,
the training is stopped due to stagnating validation loss within
the ﬁrst 40 epochs. The reported losses are generated on the
test set.
In Table V, we list the results. Overall, all models are
able to estimate the radio maps with very good accuracy
between 5.2 and 7.2 dB RMSE. Removing the infrared channel
from the input image causes a slight decrease in accuracy.
The height map improves the predictions signiﬁcantly for all
models, as expected, since inferring the height of objects from
a two-dimensional image is inherently ill-posed [38]. Across
all models, the additional inputs related to the positions on
the map provide a slight improvement when also the height
map is used. However, they deteriorate performance when
only the image is provided, which is rather surprising. A
possible explanation could be that the height information, map

## PDF 第 8 页

JAENSCH et al.: RADIO MAP PREDICTION FROM AERIAL IMAGES AND APPLICATION 315
TABLE V
ERRORS ON THE TEST SET (IN BRACKETS ON THE TRAINING /VALIDATION SET). L OWEST TEST ERRORS IN EACH COLUMN (INPUT )
WITHOUT N DSM IN ITALICS , WITH N DSM U NDERLINED AND PER ROW (MODEL ) IN BOLD
Fig. 6. Errors per epoch on the training and on the validation set. Dots mark
epochs in which the learning rate is reduced due to stagnating validation loss.
The ﬁnal model weights stem from the epoch with the lowest validation loss,
which is marked with a cross.
coordinates, and distances share the same physical units, while
the channels of the aerial images contain a completely different
type of information. We observe that, for all inputs considered,
the more lightweight RadioUNet performs slightly worse than
the two other models. The UNetDCN we propose achieves
comparable accuracy when height information is included and
outperforms the baselines when height data is absent.
The numeric errors appear relatively close. Visual inspection
of the predictions reveals that our dataset contains diverse
sample types. For some samples, there are clear differences
between models and/or inputs, while other predictions appear
very similar both visually and in terms of loss. In Fig. 7,
we provide a visual comparison of the predictions of the
models with and without access to height information for
a few exemplary samples. While all models generate sat-
isfactory predictions in most cases and correctly recognize
buildings, trees, and the encoded antenna orientation and pat-
tern, PMNet and UNetDCN appear to have an advantage over
the RadioUNet when it comes to predicting long reﬂections,
as in the ﬁrst and third rows in Fig. 7. We attribute this to
the dilated and deformable convolutional layers, increasing the
receptive ﬁeld size.
In Fig. 6, we plot the averaged training and validation losses
for each epoch in the two most relevant scenarios. We observe
that without height information, the gap between training and
validation loss increases stronger, which implies overﬁtting.
The reason for this could be that inferring the correct height
of objects and their precise locations from just an image is
very hard and the images do not contain sufﬁcient information
for stronger generalization. UNetDCN demonstrates better
resistance to overﬁtting, as shown by the smaller gap between
training and validation/test loss. In the ﬁrst row of Fig. 8,
for example, we can see that the network without access to
height information does not recognize that the house in the
main lobe completely blocks the signal. Below in the second
row, it seems to misinterpret the exact shape of the buildings
due to shadows and predicts a non-existent propagation path.
A. Ablation Study
We have performed additional experiments to investigate the
effect of the complexity of the proposed UNetDCN in Fig. 4 on
the achieved accuracy and to evaluate the usage of deformable
convolutions (DC). For the two most relevant input features,
Table VI lists the training and validation error together with the
complexity in terms of the number of parameters and MACs
for the baseline model and modiﬁed versions.
Reducing the model complexity, either by decreasing depth
(d) or width (number of channels, C), increases the validation
loss notably by up to 0.004. On the other hand, increasing the
number of channels ( C) only slightly improves validation loss
at the cost of a signiﬁcant increase in computational demand.
The gap between training and validation loss is much larger
when height information is absent. This could potentially mean
a higher risk of overﬁtting. For deeper networks ( d = 3, 4),
we observe slight improvements when predicting from images
alone. However, when height information is included, valida-
tion loss remains the same or slightly worsens. Overall, the

## PDF 第 9 页

316 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 7. Examples of predictions – (a) overlayed height maps with buildings in red, vegetation in green and Tx position in blue, (b) aerial image, (c) ground
truth radio map, predictions only from images and from images, nDSMs and coords by: (d) RadioUNet [12], (e) PMNet [5], (f) UNetDCN, MSE below.
Fig. 8. Examples of prediction, where height and positions of buildings are not determined correctly without nDSM. (a) aerial image and Tx position in blue
(b) antenna gain projected onto the ﬂoor (c) ground truth radio map, predictions by PMNet [5] with inputs: (d) only image (e) image and unclassiﬁed nDSM,
MSE below.
proposed parameters d = 3 and C = 32 provide a good
validation accuracy at a low complexity. Increasing the size
of the model could lead to marginal improvements but at the
cost of signiﬁcantly higher computational complexity and, in
some cases, potentially a larger risk of overﬁtting.
To assess the impact of deformable convolutions (DC), we
also experiment with models following the same structure
illustrated in Fig. 4, but with all DC layers replaced by
other modules. We consider two alternatives: First, standard
convolutions with larger kernel sizes and second, the atrous
spatial pyramid pooling (ASPP) block from [5]. The ASPP
block is an inception module with parallel 3× 3 convolutions
at different dilation rates (Fig. 3). With standard convolutions,
even with large kernel sizes it is not possible to reach the same
accuracy as with DC, despite a high complexity. Increasing
the kernel size beyond 9× 9 provides no further beneﬁt but
rather leads to performance deterioration. Also the ASPP block
does not work well as a drop-in replacement in our proposed
architecture. As we observe signs of potential overﬁtting in
the ﬁrst column of Table VI, we also try two more variants
with reduced complexity in terms of the parameters d and C,
but the performance is still subpar compared to DC. These
ﬁndings support our hypothesis that DC are a very efﬁcient
way to increase the receptive ﬁeld in the radio map prediction
task.
IV. A PPLICATION TO COVERAGE OPTIMIZATION
To showcase an application of the proposed models, we
consider the problem of optimizing the directivity of cellular
BS to maximize the coverage in a given area. We study two

## PDF 第 10 页

JAENSCH et al.: RADIO MAP PREDICTION FROM AERIAL IMAGES AND APPLICATION 317
TABLE VI
COMPARISON OF TRAINING /VALIDATION LOSS AND COMPLEXITY
IN TERMS OF THE NUMBER OF PARAMETERS AND MAC S FOR
DIFFERENT VARIATIONS OF UN ETDCN. R ESULTS FOR THE
PROPOSED MODEL WITH NO MODIFICATION ARE
LISTED IN THE FIRST ROW FOR COMPARISON
possible formulations of the problem that model different sce-
narios, utilizing the fast interference time and differentiability
of the CNN models. More precisely, we freeze the network
after training and treat it as a differentiable function from the
inputs, that include a representation of the antenna orientation
which we aim to optimize, to the generated radio maps.
Via backpropagation through the frozen network and gradient
descent, we can optimize the antenna orientation parameters
with respect to the coverage, that is deﬁned as a function of
the radio maps.
A. Coverage Deﬁnition and Optimization Objective
Assume thatM∈ N BS are installed at ﬁxed positions on a
given city map. The idealized antenna patterns considered are
symmetric around the boresight, allowing us to characterize
the orientation of a Tx by an azimuth angle ϕ and an elevation
angle θ with reference to the standard coordinate system.
Using any of the CNN models described before, we obtain
an estimate of the path loss (PLi(ϕ,θ,x,y ))dB for the i-th
BS, with directivity deﬁned by the azimuth angle ϕ∈ [0, 2π]
and elevation angle θ∈ [0,π ], in any point (x,y )∈ T, where
T⊂ D ={1,..., 256}×{ 1,..., 256} is a given target area.
Assuming a ﬁxed input power (PT )dBm∈ R for all BS, we
calculate the received power Pi as a function of (ϕ,θ,x,y )
according to (1) for each BS.
As the ﬁrst scenario, we consider a macro-diversity
system [39], in which signals from multiple BS are combined
non-coherently and therefore the total received power in linear
scale is deﬁned as the sum
(
Ptot(⃗ ϕ,⃗θ,x,y )
)
W
=
M∑
i=1
(Pi(ϕi,θi,x,y ))W, (3)
with ⃗ ϕ= ( ϕi)Mi=1,⃗θ = ( θi)Mi=1. We aim to ﬁnd ⃗ ϕ∈
[0, 2π]M,⃗θ∈ [0,π ]M that maximize the 10-th percentile p10
of (3) in dBm scale over the locations in the target area, which
is
p10(⃗ ϕ,⃗θ) = min{t∈ R : ( Ptot(⃗ ϕ,⃗θ,x,y ))dBm≤t
for 10%of the points (x,y )in T}. (4)
In other words, we seek to maximize a lower bound for (3)
that holds for 90% of the potential UE locations. Attempting to
maximize the minimum value rather than the 10-th percentile,
which would be a lower bound for all locations, only worked
for very restrictive target areas. This is because some locations
are difﬁcult or impossible to cover by any Tx, and the
models sometimes fail to accurately identify the exact edges
of buildings at the pixel level.
As a second scenario, we assume non-cooperative BS
and aim to guarantee a strong signal from one of the
BS while keeping the interference from the other BS low.
More precisely, we consider the maximum of the signal-to-
interference-plus-noise ratio (SINR) across all BS,
SINR(⃗ ϕ,⃗θ,x,y )
= max
i=1,...,M
(Pi(ϕi,θi,x,y ))W∑
j⁄=i (Pj(ϕi,θi,x,y ))W + (PN )W
, (5)
where PN denotes the power of the noise in the system. This
time, we aim to guarantee a sufﬁciently good SINR level in
the largest possible area, i.e. ﬁnd ⃗ ϕ∈ [0, 2π]M,⃗θ∈ [0,π ]M
that maximize
#{(x,y )∈ T : SINR( ⃗ ϕ,⃗θ,x,y )≥t} (6)
for some threshold t> 0, where # denotes the cardinality of
a set.
B. Implementation and Results
To predict the radio maps, we choose the DCN model
that only receives an aerial image, the Tx location and the
antenna gain as input. As starting and reference values for
the optimization, we deﬁne the elevation angle between the
z-axis (pointing straight up) and the antenna boresight as
θ0 = 34π and we choose the azimuth angle ϕ0 so that
the boresight of the Tx points away from the building the
BS is located on. The ﬁrst optimization routine we consider
is random search, i.e. trying angles (ϕ,θ ) randomly drawn
from
[
ϕ0− 34π,ϕ 0 + 34π]× [π/2,π ] for a ﬁxed number of
iterations. Note that we restrict the domain of the angles to
avoid clearly suboptimal conﬁgurations in which the Tx points
onto the building it is located on or towards the sky. As a
second option, we investigate leveraging the differentiability
of the CNN model. To achieve this, we deﬁne the angles as
trainable parameters, freeze the network weights, and treat the
antenna gain as a differentiable function of the angles. This
allows us to optimize the angles of all BS simultaneously
using gradient descent. Although it is not possible to calculate
the true optima analytically or numerically, we can compare
the ﬁnal coverage score with that of the initial antenna
conﬁguration.
Minimizing (4) directly with gradient descent is problem-
atic, since in each iteration only the value at one or a few
speciﬁc locations with the current 10-th percentile is taken into

## PDF 第 11 页

318 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
Fig. 9. Coverage optimization.
account during backpropagation. To obtain an approximate
formulation, we replace the 10-th percentile in (4) by the
Boltzmann operator [40], deﬁned as
Bα(S) =
∑
x∈Sx exp(αx)∑
x∈S exp(αx) ,
for a ﬁnite set S⊂ R and a parameter α <0. For negative
values of α with large magnitude, Bα approximates the
minimum and forα close to 0 the mean of the set S. Similarly,
the thresholding and counting in (6) are not differentiable.
In our implementation, for gradient descent, we replace the
thresholding operation by an appropriately shifted sigmoid
function in order to obtain a smooth transition from 0 to 1
for values below and above the threshold, and we implement
the cardinality by summing over all pixels. We consider
M = 3 BS, a 120 ◦ sector antenna pattern, noise power of
−104dBm (corresponding to a noise power spectral density
of−174dBm/Hz and 10MHz bandwidth), and we assume a
Tx input power of 23dBm as detailed in Section II-B2. Both
methods are run for 500 iterations, which takes about 15s with
random search and 60s with gradient descent, although we
observed that gradient descent is already close to the optimal
value after about 50 iterations. The SINR threshold in (6) is
set to t = 20dB.
The results are listed in Tables VII and VIII and visualized
in Figures 9(a) and 9(b). Both methods provide a solid
improvement over the baseline in scenario 1 and a large
improvement in scenario 2, with gradient descent performing
slightly better. This also shows that our approach of optimizing
a differentiable approximation of the coverage score with
TABLE VII
RESULTS OF SCENARIO 1 (4) IN D BM
TABLE VIII
RESULTS OF SCENARIO 2 (6), N UMBER OF PIXELS IN THE
TARGET AREA WITH SINR A BOVE THE THRESHOLD
gradient descent is indeed valid in order to maximize the true
score.
V. C ONCLUSION
In this paper, we demonstrate that accurate path loss radio
maps can be predicted even without full 3D environmental
data, using only aerial images or with the addition of height but
no classiﬁcation information. This opens up new possibilities,
such as using data from a UA V ﬂyover, where images and
potentially a LiDAR scan are captured, allowing direct and
efﬁcient radio map prediction from this data.
As a further potential extension of this, predicting the
radio map from satellite data available for the whole planet
(similarly to [22], but in cellular networks) would allow
large-scale applications to network planning and related tasks.
The often lower spatial resolution may make the recognition

## PDF 第 12 页

JAENSCH et al.: RADIO MAP PREDICTION FROM AERIAL IMAGES AND APPLICATION 319
of objects and shapes more difﬁcult. On the other hand,
incorporation of other spectral bands or radar data could be
beneﬁcial for the implicit classiﬁcation of objects and height
estimation [41].
In this work, we made certain assumptions, such as approx-
imating the ground as ﬂat, to simplify the modeling process.
We acknowledge that these simpliﬁcations may limit the
applicability of our models to regions with signiﬁcant elevation
variations. Future work could involve retraining models with
datasets that include ground elevation data to better accom-
modate diverse geographic scenarios, as in [15]. While we
have presented the radiomap prediction results in terms of the
RMSE averaged over the whole map, in line with the existing
literature, a more reﬁned study of the “conditional” RMSE
(e.g., RMSE versus distance from Tx, or RMSE conditioned
on (non-)line-of-sight propagation) is certainly an interesting
topic for future work.
Although this study does not cover it, the dataset could
be used to explore joint semantic segmentation and height
estimation from aerial images [38], [42]. This could serve as
an intermediate step toward improving radio map predictions.
By making our dataset and code available for public
use, we aim to facilitate the work of other researchers
and promote reproducible and comparable investigations.
Featuring directive Tx antennas, the dataset opens poten-
tial for the investigation of more downstream tasks in
5G/6G networks, such as beam codebook design and beam
management [3].
ACKNOWLEDGMENT
The authors would like to thank C ¸ aˇgkan Yapar for advice
on the dataset generation and the related literature, Ron Levie
for discussions on how to generate and use line-of-sight
information, Tom Burgert for advice on curriculum learning
and the recommendation to use PyTorch Lightning, and Saeid
Dehkordi for proofreading.
REFERENCES
[1] X. Wu et al., “FlashLinQ: A synchronous distributed scheduler for
peer-to-peer ad hoc networks,” IEEE/ACM Trans. Netw., vol. 21, no. 4,
pp. 1215–1228, Aug. 2013.
[2] C ¸ . Yapar, R. Levie, G. Kutyniok, and G. Caire, “Real-time out-
door localization using radio maps: A deep learning approach,”
IEEE Trans. Wireless Commun. , vol. 22, no. 12, pp. 9703–9717,
Dec. 2023.
[3] D. E. Berraki, S. M. D. Armour, and A. R. Nix, “Codebook
based beamforming and multiuser scheduling scheme for mmWave
outdoor cellular systems in the 28, 38 and 60GHz bands,”
in Proc. IEEE Globecom Workshops (GC Wkshps) , Dec. 2014,
pp. 382–387.
[4] M. Lecci, P. Testolina, M. Polese, M. Giordani, and M. Zorzi, “Accuracy
versus complexity for mmWave ray-tracing: A full stack perspective,”
IEEE Trans. Wireless Commun. , vol. 20, no. 12, pp. 7826–7841, Dec.
2021.
[5] J.-H. Lee and A. F. Molisch, “A scalable and generalizable pathloss
map prediction,” IEEE Trans. Wireless Commun. , vol. 23, no. 11,
pp. 17793–17806, Nov. 2024.
[6] S. Bakirtzis, C. Yapar, M. Fiore, J. Zhang, and I. Wassell, “Empowering
wireless network applications with deep learning-based radio propaga-
tion models,” 2024, arXiv:2408.12193.
[7] G. Calcev et al., “A wideband spatial channel model for system-wide
simulations,” IEEE Trans. Veh. Technol. , vol. 56, no. 2, pp. 389–403,
Mar. 2007.
[8] Z. Yun and M. F. Iskander, “Ray tracing for radio propagation modeling:
Principles and applications,” IEEE Access, vol. 3, pp. 1089–1100, 2015.
[9] M. Kasparick et al., “Kernel-based adaptive online reconstruction of
coverage maps with side information,” IEEE Trans. Veh. Technol. ,
vol. 65, no. 7, pp. 5461–5473, Jul. 2016.
[10] S. I. Popoola et al., “Determination of neural network parameters for
path loss prediction in very high frequency wireless channel,” IEEE
Access, vol. 7, pp. 150462–150483, 2019.
[11] Z. Li, F. Liu, W. Yang, S. Peng, and J. Zhou, “A survey of convo-
lutional neural networks: Analysis, applications, and prospects,” IEEE
Trans. Neural Netw. Learn. Syst. , vol. 33, no. 12, pp. 6999–7019,
Dec. 2022.
[12] R. Levie, C ¸ . Yapar, G. Kutyniok, and G. Caire, “RadioUNet:
Fast radio map estimation with convolutional neural networks,”
IEEE Trans. Wireless Commun. , vol. 20, no. 6, pp. 4001–4015,
Jun. 2021.
[13] O. Ronneberger, P. Fischer, and T. Brox, “U-Net: Convolutional net-
works for biomedical image segmentation,” in Proc. Med. Image
Comput. Comput.-Assist. Intervent. (MICCAI) , N. Navab, J. Hornegger,
W. M. Wells, and A. F. Frangi, Eds., Cham, Switzerland: Springer, Aug.
2015, pp. 234–241.
[14] X. Zhang, X. Shu, B. Zhang, J. Ren, L. Zhou, and X. Chen, “Cellular
network radio propagation modeling with deep convolutional neural
networks,” in Proc. 26th ACM SIGKDD Int. Conf. Knowl. Discovery
Data Mining, Aug. 2020, pp. 2378–2386.
[15] V . V . Ratnam et al., “FadeNet: Deep learning-based mm-Wave large-
scale channel fading prediction and its applications,” IEEE Access ,
vol. 9, pp. 3278–3290, 2021.
[16] Y . Tian, S. Yuan, W. Chen, and N. Liu, “Transformer based radio
map prediction model for dense urban environments,” in Proc. 13th
Int. Symp. Antennas Propag. EM Theory (ISAPE) , vol. 1, 2021,
pp. 1–3.
[17] F. Yu and V . Koltun, “Multi-scale context aggregation by
dilated convolutions,” in Proc. Int. Conf. Learn. Represent. ,
Jan. 2015, pp. 2–3.
[18] M. R. Ziemann, J. S. Hyatt, and M. S. Lee, “Convolutional
neural networks for radio frequency ray tracing,” in Proc. MIL-
COM - IEEE Mil. Commun. Conf. (MILCOM) , Nov. 2021,
pp. 618–622.
[19] S. Bakirtzis, K. Qiu, J. Zhang, and I. Wassell, “DeepRay: Deep learning
meets ray-tracing,” in Proc. 16th Eur. Conf. Antennas Propag. (EuCAP),
Mar. 2022, pp. 1–5.
[20] A. Dosovitskiy et al., “An image is worth 16 ×16 words: Transformers
for image recognition at scale,” in Proc. Int. Conf. Learn. Repre-
sent., Jan. 2020, pp. 3–4. [Online]. Available: https://openreview.net/
forum?id=YicbFdNTTy
[21] K. Qiu, S. Bakirtzis, H. Song, J. Zhang, and I. Wassell, “Pseudo ray-
tracing: Deep leaning assisted outdoor mm-Wave path loss prediction,”
IEEE Wireless Commun. Lett. , vol. 11, no. 8, pp. 1699–1702, Aug.
2022.
[22] A. Marey, M. Bal, H. F. Ates, and B. K. Gunturk, “PL-GAN: Path loss
prediction using generative adversarial networks,” IEEE Access, vol. 10,
pp. 90474–90480, 2022.
[23] C. Yapar, R. Levie, G. Kutyniok, and G. Caire, “Dataset of pathloss and
toa radio maps with localization application,” 2024, arXiv:2212.11777.
[24] F. Jaensch, G. Caire, and B. Demir, “Radio map estimation—An open
dataset with directive transmitter antennas and initial experiments,”
2024, arXiv:2402.00878.
[25] J. Dai et al., “Deformable convolutional networks,” in Proc. IEEE Int.
Conf. Comput. Vis. (ICCV) , Oct. 2017, pp. 764–773.
[26] J. Peurifoy et al., “Nanophotonic particle simulation and inverse design
using artiﬁcial neural networks,” Sci. Adv. , vol. 4, no. 6, p. 4206,
Jun. 2018. [Online]. Available: https://www.science.org/doi/abs/10.1126/
sciadv.aar4206
[27] J. Hoydis et al., “Sionna: An open-source library for next-generation
physical layer research,” 2022, arXiv:2203.11854.
[28] J. Hoydis et al., “Sionna RT: Differentiable ray tracing for radio
propagation modeling,” 2023, arXiv:2303.11103.
[29] A. F. Molisch, Wireless Communications, 2nd ed., Hoboken, NJ, USA:
Wiley, 2011.
[30] P. Bello, “Characterization of randomly time-variant linear channels,”
IEEE Trans. Commun. , vol. COM-11, no. 4, pp. 360–393, Dec. 1963.
[31] J. G. Proakis and M. Salehi, Digital Communications , 5th ed., New
York, NY , USA: McGraw-Hill, 2008.
[32] B. u. W. Senatsverwaltung F ¨ur Stadtentwicklung . Accessed: Jun. 25,
2025. [Online]. Available: https://fbinter.stadt-berlin.de/fb/index.jsp

## PDF 第 13 页

320 IEEE TRANSACTIONS ON WIRELESS COMMUNICATIONS, VOL. 25, 2026
[33] Rapidlasso GmbH. Lastools—Efﬁcient LiDAR Processing Software. .
Accessed: Jun. 25, 2025. [Online]. Available: http://rapidlasso.com/
LAStools
[34] Remcom. Wireless Insite. [Online]. Available: https://www.remcom.com/
wireless-insite-em-propagation-software/
[35] Geobroker. L. und Geobasisinformation Brandenburg . [Online]. Avail-
able: https://geobroker.geobasis-bb.de/
[36] C ¸ . Yapar, F. Jaensch, R. Levie, G. Kutyniok, and G. Caire, “The ﬁrst
pathloss radio map prediction challenge,” in Proc. IEEE Int. Conf.
Acoust., Speech Signal Process. (ICASSP) , Jun. 2023, pp. 1–2.
[37] Microsoft. Deepspeed Flops Proﬁler . [Online]. Available: https://
www.deepspeed.ai
[38] S. Du et al., “IMG2HEIGHT: Height estimation from single
remote sensing image using a deep convolutional encoder–decoder
network,” Int. J. Remote Sens. , vol. 44, no. 18, pp. 5686–5712,
Sep. 2023.
[39] F. Kirsten, D. ¨Ohmann, M. Simsek, and G. P. Fettweis, “On the utility
of macro- and microdiversity for achieving high availability in wireless
networks,” in Proc. IEEE 26th Annu. Int. Symp. Pers., Indoor, Mobile
Radio Commun. (PIMRC) , Aug. 2015, pp. 1723–1728.
[40] K. Asadi and M. L. Littman, “An alternative softmax operator for rein-
forcement learning,” in Proc. 34th Int. Conf. Mach. Learn. , D. Precup
and Y . W. Teh, Eds., Aug. 2017, pp. 243–252. [Online]. Available:
https://proceedings.mlr.press/v70/asadi17a.html
[41] D. Frantz et al., “National-scale mapping of building height using
Sentinel-1 and Sentinel-2 time series,” Remote Sens. Environ., vol. 252,
Jan. 2021, Art. no. 112128.
[42] S. Srivastava, M. V olpi, and D. Tuia, “Joint height estimation
and semantic labeling of monocular aerial images with CNNS,” in
Proc. IEEE Int. Geosci. Remote Sens. Symp. (IGARSS) , Jul. 2017,
pp. 5173–5176.
Fabian Jaensch received the B.Sc. and M.Sc.
degrees in mathematics from Technische Universi ¨at
Berlin in 2016 and 2021, respectively. He is
currently working as a Ph.D. Student at the Commu-
nications and Information Theory Chair, Technische
Universit¨at Berlin. His research interests include
machine learning, in particular computer vision, and
applications to wireless communications.
Giuseppe Caire (Fellow, IEEE) was born in Turin,
in 1965. He received the B.Sc. degree in electri-
cal engineering from the Politecnico di Torino in
1990, the M.Sc. degree in electrical engineering
from Princeton University in 1992, and the Ph.D.
degree from the Politecnico di Torino in 1994. He
was a Post-Doctoral Research Fellow with European
Space Agency and Technology Centre (ESTEC),
Noordwijk, The Netherlands, from 1994 to 1995;
an Assistant Professor in telecommunications at the
Politecnico di Torino; an Associate Professor at the
University of Parma, Italy; a Professor with the Department of Mobile
Communications, Eurecom Institute, Sophia-Antipolis, France; a Professor of
electrical engineering with the Viterbi School of Engineering, University of
Southern California, Los Angeles, CA, USA, and he is currently an Alexander
von Humboldt Professor with the Faculty of Electrical Engineering and
Computer Science, Technische Universit¨at Berlin, Germany. His main research
interests include communications theory, information theory, and channel and
source coding with particular focus on wireless communications.
Dr. Caire received the Jack Neubauer Best System Paper Award from
the IEEE Vehicular Technology Society in 2003; the IEEE Communications
Society and Information Theory Society Joint Paper Award in 2004, 2011,
and 2025; the Okawa Research Award in 2006; the Alexander von Humboldt
Professorship in 2014; the V odafone Innovation Prize in 2015; an ERC
Advanced Grant in 2018; the Leonard G. Abraham Prize for best IEEE JSAC
paper in 2019; the IEEE Communications Society Edwin Howard Armstrong
Achievement Award in 2020; the 2021 Leibniz Prize of the German National
Science Foundation (DFG); and the CTTC Technical Achievement Award of
the IEEE Communications Society in 2023. He has served on the Board of
Governors of the IEEE Information Theory Society from 2004 to 2007 and
as an ofﬁcer from 2008 to 2013. He was President of the IEEE Information
Theory Society in 2011.
Beg¨um Demir (Senior Member, IEEE) received
the B.Sc., M.Sc., and Ph.D. degrees in electronic
and telecommunication engineering from Kocaeli
University, Kocaeli, T ¨urkiye, in 2005, 2007, and
2010, respectively.
She is currently a Full Professor and the Founder
Head of the Remote Sensing Image Analysis (RSiM)
Group, Faculty of Electrical Engineering and Com-
puter Science, TU Berlin, and the Head of the
Big Data Analytics for Earth Observation Research
Group, Berlin Institute for the Foundations of Learn-
ing and Data (BIFOLD). Her research activities lie at the intersection of
machine learning, remote sensing and signal processing. Speciﬁcally, she
performs research in the ﬁeld of processing and analysis of large-scale Earth
observation data acquired by airborne and satellite-borne systems.
Dr. Demir is a scientiﬁc committee member of several international confer-
ences and workshops. She was awarded by the prestigious “2018 Early Career
Award” by the IEEE Geoscience and Remote Sensing Society for her research
contributions in machine learning for information retrieval in remote sensing.
In 2018, she received a Starting Grant from European Research Council (ERC)
for her project “BigEarth: Accurate and Scalable Processing of Big Data in
Earth Observation.” She is an Fellow of European Laboratory for Learning
and Intelligent Systems (ELLIS). She is a Referee for several journals, such
as Proceedings of the IEEE , IEEE T RANSACTIONS ON GEOSCIENCE AND
REMOTE SENSING , IEEE G EOSCIENCE AND REMOTE SENSING LETTERS ,
IEEE T RANSACTIONS ON IMAGE PROCESSING , Pattern Recognition, IEEE
TRANSACTIONS ON CIRCUITS AND SYSTEMS FOR VIDEO TECHNOLOGY ,
IEEE J OURNAL OF SELECTED TOPICS IN SIGNAL PROCESSING , Interna-
tional Journal of Remote Sensing , and several international conferences. She
is an Associate Editor for IEEE Geoscience and Remote Sensing Magazine .
