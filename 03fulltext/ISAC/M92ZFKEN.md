---
title: "Integrated Sensing and Communications Toward Dual-Functional Wireless Networks for 6G and Beyond"
zotero_key: "M92ZFKEN"
pdf_key: "4FBXFUUM"
collection: "ISAC"
source: "Open-access PDF (arXiv, pypdf extraction)"
page_mapping: unverified
---

# Integrated Sensing and Communications Toward Dual-Functional Wireless Networks for 6G and Beyond — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
Integrated Sensing and Communications:
Towards Dual-functional Wireless Networks
for 6G and Beyond
Fan Liu, Member, IEEE, Yuanhao Cui, Member, IEEE, Christos Masouros, Senior Member, IEEE,
Jie Xu, Member, IEEE, Tony Xiao Han, Member, IEEE, Yonina C. Eldar, Fellow, IEEE,
and Stefano Buzzi, Senior Member, IEEE
Abstract—As the standardization of 5G is being solidiﬁed,
researchers are speculating what 6G will be. Integrating sensing
functionality is emerging as a key feature of the 6G Radio Access
Network (RAN), allowing to exploit the dense cell infrastructure
of 5G for constructing a perceptive network. In this paper, we
provide a comprehensive overview on the background, range of
key applications and state-of-the-art approaches of Integrated
Sensing and Communications (ISAC). We commence by dis-
cussing the interplay between sensing and communications (S&C)
from a historical point of view, and then consider multiple facets
of ISAC and its performance gains. By introducing both ongoing
and potential use cases, we shed light on industrial progress and
standardization activities related to ISAC. We analyze a number
of performance tradeoffs between S&C, spanning from informa-
tion theoretical limits, tradeoffs in physical layer performance,
to the tradeoff in cross-layer designs. Next, we discuss signal
processing aspects of ISAC, namely ISAC waveform design and
receive signal processing. As a step further, we provide our vision
on the deeper integration between S&C within the framework of
perceptive networks, where the two functionalities are expected
to mutually assist each other, i.e., communication-assisted sensing
and sensing-assisted communications. Finally, we summarize the
paper by identifying the potential integration between ISAC and
other emerging communication technologies, and their positive
impact on the future of wireless networks.
Index Terms—Integrated sensing and communications, perfor-
mance tradeoff, waveform design, perceptive network.
F. Liu is with the Department of Electrical and Electronic Engineering,
Southern University of Science and Technology, Shenzhen 518055, China
(e-mail: liuf6@sustech.edu.cn).
Y . Cui is with the Department of Communication Engineering, Beijing
University of Posts and Telecommunications, Beijing, China (e-mail: cuiyuan-
hao@bupt.edu.cn).
C. Masouros is with the Department of Electronic and Electrical En-
gineering, University College London, London, WC1E 7JE, UK (e-mail:
chris.masouros@ieee.org).
J. Xu is with the Future Network of Intelligence Institute (FNii), The Chi-
nese University of Hong Kong (Shenzhen), Shenzhen 518172, China, and also
with the School of Science and Engineering, The Chinese University of Hong
Kong (Shenzhen), Shenzhen 518172, China (e-mail: xujie@cuhk.edu.cn).
T. X.-Han is with Huawei Technologies Co., Ltd (email:
tony.hanxiao@huawei.com).
Y . C. Eldar is with the Faculty of Mathematics and Computer
Science, Weizmann Institute of Science, Rehovot, Israel (e-mail: yon-
ina.eldar@weizmann.ac.il).
S. Buzzi is with the Department of Electrical and Information Engineering,
University of Cassino and Southern Lazio, I-03043 Cassino, Italy, with the
Consorzio Nazionale Interuniversitario per le Telecomunicazioni (CNIT), I-
43124 Parma, Italy, and also with GBB Wireless Research, I-80143, Napoli,
Italy (e-mail: buzzi@unicas.it).
I. I NTRODUCTION
A. Background and Motivation
N
EXT-generation wireless networks (such as beyond 5G
(B5G) and 6G) have been envisioned as a key enabler
for many emerging applications, such as connected intel-
ligence, smart cities and industry, connected vehicles and
remote health-caring. These applications demand high-quality
wireless connectivity as well as high-accuracy and robust
sensing capability. Among many visionary assumptions about
the B5G/6G networks, a common theme is that sensing will
play a signiﬁcant role more than ever before, particularly for
location/environment-aware scenarios [1]. It is foreseeable that
future networks will go beyond classical communication and
provide a sensing functionality to measure or even to image
the surrounding environment. This sensing functionality and
the forthcoming ability of the network to collect sensory data
from the environment, is seen as an enabler for learning and
building intelligence in future smart cities. Therefore, it is
natural to connect both operations in B5G/6G networks, which
motivates the recent research theme of Integrated Sensing and
Communications (ISAC) [2].
Sensing and communication (S&C) process information
in different ways. Sensing collects and extracts information
from noisy observations, while communication focuses on
transferring information via speciﬁcally tailored signals and
then recovers it from the noisy reception. The ultimate goal
of ISAC is to unify these two operations and to pursue direct
tradeoffs between them as well as mutual performance gains.
On one hand, ISAC is expected to considerably improve
spectral and energy efﬁciencies, while reducing both hard-
ware and signaling costs, since it attempts to merge sensing
and communication into a single system, which previously
competed over various types of resources. On the other hand,
ISAC also pursues deeper integration where the two func-
tionalities are no longer viewed as separate end-goals but are
co-designed for mutual beneﬁts, i.e., communication-assisted
sensing and sensing-assisted communication. Proﬁting from
the above attributes, the usage of ISAC is not restricted to
cellular networks, but has been extended to a wide variety of
applications, such as Wi-Fi networks [3], [4], unmanned aerial
vechile (UA V) networks [5], and military communications [6].
arXiv:2108.07165v1  [eess.SP]  16 Aug 2021

2
B. Historical View of ISAC
Although only recently gaining growing attention from
both academia and industry, ISAC dates back to as early
as the 1960s. ISAC, in its oldest form, was implemented
in [7] over a missile range instrumentation radar via pulse
interval modulation (PIM), where information was embed-
ded into a group of radar pulses. Such systems are deﬁned
by different names, e.g., Radar-Communications (RadCom)
[8], Joint Communication and Radar (JCR) [9], Joint Radar
and Communication (JRC) [10], and Dual-functional Radar-
Communications (DFRC) [10]. The sensing functionality in
these systems mainly refers to radar sensing, which has long
been a mainstream in ISAC. In fact, as a major representative
of sensing technologies, radar’s development has been pro-
foundly affected by wireless communications, and vice versa.
1) The Birth of Radar: Since its birth in the ﬁrst half of
the 20th century, radar systems have been deployed worldwide,
carrying out various sensing tasks, such as geophysical moni-
toring, air trafﬁc control, weather observation, and surveillance
for defence and security. The term RADAR was ﬁrst used
by the US Navy as an acronym for “RAdio Detection And
Ranging” in 1939 [11]. During the two World Wars, radar
was independently and secretly created by different nations,
and was soon put into use in the war to provide early warning
of incoming threats.
Driven by mechanical motors, a classical rotary radar
searches for targets in the space via periodically rotating its an-
tenna(s). Such radars, however, face several critical challenges,
e.g., the lack of multi-functionality and ﬂexibility, as well as
being relatively easy to jam and interfer. In view of this, the
phased-array, a.k.a. the electronically-scanned array technique,
was born at the right moment [12]. Instead of mechanically
rotating its antennas, phased-array systems generate spatial
beams of signals that can be electronically steered to different
directions. This type of radar was applied for the ﬁrst time
to assist the landing of aircrafts in World War II, by Nobel
laureate Luis Alvarez [13]. In later times of the war, a long-
range early warning phased-array radar, named “FuMG 41/42
Mammut” (or “Mammut” in short), was developed by the
German company GEMA, capable of detecting targets ﬂying
at an altitude of 8 km at a range of 300 km [14].
2) How Radar and Communication Inspire Each Other:
“Mammut” might not only be the ﬁrst phased-array radar sys-
tem, but also the ﬁrst multi-antenna system, which inspired the
invention of multi-input multi-output (MIMO) communication
systems. In 1994, the ﬁrst patent on MIMO communication
was granted to Paulraj and Kailath [15], which led to the
new eras of 3G, 4G, and 5G wireless networks [16], [17].
Triggered by MIMO communication techniques, collocated
MIMO radar was proposed ten years later at the 2004 IEEE
Radar Conference by the MIT Lincoln Lab [18]. In MIMO
radar, each antenna transmits individual waveforms instead
of phase-shifted counterparts of a benchmark waveform [19].
This leads to enlarged virtual aperture, which improves the
ﬂexibility and the sensing performance compared to phased-
array radars. Concepts such as degrees-of-freedom (DoFs) and
diversity, which were “borrowed” from MIMO communication
theory, became corner stones of the MIMO radar theoretical
foundation [20], [21].
The research on radar and communication began to merge
in the early 1990s-2000s. In the 1990s, the Ofﬁce of Naval
Research (ONR) of the US initiated the Advanced Multi-
function Radio Frequency (RF) Concept (AMRFC) Program,
aiming to design integrated RF front-ends by partitioning
multiple antennas into different functional modules, for e.g.,
radar, communications, and electronic warfares [22], [23],
respectively. The ISAC research that emerged in the 1990s-
2000s was largely motivated by the AMRFC and its follow-
up projects, such as the Integrated Topside (InTop) program
sponsored by the ONR [24]. During that period, various ISAC
schemes were proposed by the radar community, where the
general idea was to embed communication information into
commonly employed radar waveforms. For instance, the pio-
neering work of [25] proposed to combine chirp signals with
PSK modulations, which was the ﬁrst ISAC waveform design
to exploit chirp signals. Since then, many researches began to
focus on modulating communication data by leveraging radar
waveforms (such as chirp signals and frequency/phase-coded
waveforms) as carriers [26]–[29].
Orthogonal Frequency Division Multiplexing (OFDM), one
of the key techniques in wireless networks including 4G and
5G, has been found to be useful in radar sensing as well in
the early 2010s [8]. In particular, in OFDM radar, the impact
of random communication data can be straightforwardly mit-
igated, and the delay and Doppler processing are decoupled,
which can be simply performed by the Fast Fourier Transform
(FFT) and its inverse (IFFT) [8]. The two types of schemes
based on chirp and OFDM signals, are examples for “sensing-
centric” and “communication-centric” designs, respectively, as
will be detailed in later sections.
In 2013, the Defense Advanced Research Projects Agency
(DARPA) of the US funded another project named “Shared
Spectrum Access for Radar and Communications (SSPARC)”,
which aimed to release part of the sub-6 GHz spectrum from
the radar bands for the shared use of radar and communication
[30]. This leads to another interesting research topic of “radar-
communication coexistence (RCC)” within the framework of
cognitive radio, where individual radar and communication
systems are expected to coexist in the same frequency band,
without unduly interfering with each other [31]–[35]. Going
beyond the spectral coexistence and interference management
involved in RCC, ISAC pursues a deeper integration of the
two functionalities through a common infrastructure.
3) Parallel Development of Radar and Communication: In
2010, massive MIMO (mMIMO) was proposed in Marzetta’s
seminal work, which later became one of the core technologies
for 5G-and-beyond networks [37], [43]. Three years later in
2013, NYU WIRELESS published their landmark paper on the
feasibility of exploiting millimeter wave (mmWave) signals
for mobile communications [39]. From then on, mmWave
and mMIMO became a perfect couple that mutually aid
each other. Massive MIMO arrays can be made physically
much smaller thanks to the signal wavelength at the mm
level, and mmWave signals can be transmitted farther away
owing to the high beamforming gain provided by the mMIMO

3
1939
2021
The term RADAR is ﬁrst used by the US Navy [11].
The ﬁrst microwave phased-array antenna is invented by the Nobel laureate Luis Alvarez [13].
1942
The ﬁrst practical phased-array radar, FuMG 41/42 Mammut, is built by the Germany company
GEMA [14].
1944
The world’s ﬁrst ISAC signaling scheme is proposed in [7], in which the communication bits are
modulated on the radar pulse interval.
1963
The ﬁrst patent on MIMO communication system is granted [15].
1994
The Advanced Multifunction RF Concept (AMRFC) Program [22] is initiated by the Ofﬁce of
Naval Research (ONR) of the US.
1996
The ﬁrst ISAC scheme that exploits chirp signals is proposed [25].
2003
The concept of the collocated MIMO radar is proposed in [18] by the MIT Lincoln Lab.
The HAD structure is introduced into MIMO communication [36].
T. L. Marzetta’s seminal work [37] on massive MIMO communication is published.
2010
The concept of the phased-MIMO radar is proposed [38], with a similar RF front-end structure to
the HAD communication system.
The OFDM based ISAC signaling scheme is proposed [8].
NYU WIRELESS’s landmark paper [39] on mmWave mobile communication is published.
2013
DARPA launches the project “Shared Spectrum Access for Radar and Communications (SS-
PARC)”, which aims at releasing part of the radar spectrum for use of commercial communication.
The HAD technique is applied to the mmWave massive MIMO communication system [40].
The concept of the perceptive mobile network is proposed [41].
2017
The ﬁrst theoretical analysis of the asymptotic performance of the massive MIMO radar is
presented [42].
The deﬁnition and scope of ISAC are formally given in [2] and this paper.
Fig. 1. Interplay between S&C - A Historical View.
array. Nevertheless, a critical challenge preventing large-scale
deployment of mMIMO mmWave technologies is that huge
hardware costs and energy consumption are imposed, due to
the large number of mmWave RF chains required. This forced
wireless researchers to rethink the RF front-end architecture
of mMIMO systems. Among others, the hybrid analog-digital
(HAD) structure became a viable promising solution, which
connects massive antennas with a small number of RF chains
through a well-designed phase-shifter network, thus leading to
reduced costs and energy consumption [36], [40], [44].
Coincidentally, in the same year when the mMIMO was
born, the concept of the phased-MIMO radar was proposed
in [38], which attempts to achieve a balance between phased-
array and MIMO radars. Notice that by transmitting individual
waveforms at each antenna, the MIMO radar is beneﬁcial
in increasing the DoFs at a cost of limited array gains; by
contrast, via focusing the transmit power towards a target
direction, the phased-array radar is advantageous in achieving
higher array gains but with compromised DoFs. A natural idea
is therefore to design a system architecture which bridges the
gap between the two, by linking multiple antennas with a
limited number of RF chains via phase-shifter arrays. This
achieves a ﬂexible tradeoff between phased-array and MIMO
radars [38]. In the extreme case when there is only a single
RF chain, phased-MIMO radar reduces to the phased-array
radar. On the other hand, if the number of RF chains equals
the number of antennas, phased-MIMO radar is equivalent
to MIMO radar. More recently, advantages of leveraging
mMIMO for radar detection are considered in [42], where a
target can be accurately sensed via a single snapshot in the
presence of disturbance with unknown statistics.
Due to the above parallel, yet largely independent devel-
opment, there exist duplications in devices, such as between
phased arrays for radar and for communications, MIMO radar
and MIMO communications, while multi-static radars can be
paralleled to cooperative communications. Notably, there are
also parallels between the radar signal processing and that of
communications, including between beamforming for commu-
nications and for radar, hypothesis testing for target detection
and signal detection, millimeter-wave communication channel

4
1. Information 
Theoretical Limits
2. Tradeoff in PHY
3. Tradeoff in S&C 
Channels
4. Tradeoff in Cross 
Layers
1. Sensing-Centric 
Waveform Design
2. Comms-Centric 
Waveform Design
3. Joint Waveform 
Design
4. Receive Signal 
Processing
2. Using NR 
Frame/Waveform for 
Sensing
3. Using C-RAN for 
Networked Sensing
1. Sensing-Assisted 
Beam Training
2. Sensing-Assisted 
Beam Tracking & 
Prediction
3. Sensing-Assisted 
Resource Allocation
Performance Tradeoff
Sec. III
Signal Processing
Sec. IV–Sec. V
Comms-Assisted Sensing
Sec. VI
Sensing-Assisted Comms
Sec. VII
1. Sensing as A Service
2. Smart Home and In-
Cabin Sensing
6. Environmental 
Monitoring
Applications
Sec. II
3. V2X Network
5. Remote Sensing and 
Geoscience
7. Human Computer 
Interaction (HCI)
Integration Gain Coordination Gain
ISAC Framework & Paper Structure
1. Perceptive Mobile 
Network
4. Sensing-Assisted 
PHY Security
4. Smart Manufacturing 
and Industrial IoT
Fig. 2. Framework of ISAC technologies and structure of the paper.
estimation and radar angle detection, among others that will
be detailed in the following sections.
4) Convergence of S&C: The above similarities provide a
clear opportunity for the convergence of the two technologies
into systems and devices, that can serve sensing and commu-
nications with a single transmission. Indeed, one may observe
from the above interesting parallel, that radar and communi-
cation technologies are so deeply interweaved with each other
that they evolve towards the same direction eventually. That is,
high frequency band and large-scale antenna array, which are
essentially demands for more spectral and spatial resources.
From the communication perspective, large bandwidth and
antenna arrays boost the communication capacity and provide
massive connections. On the other hand, increasing bandwidth
and number of antennas will also considerably improve the
radar performance in range and angular resolutions, i.e., the
ability to more accurately sense more targets, or to map a
complex environment.
Radar and communication also tend to be similar in both
channel characteristics and signal processing, as their opera-
tion frequencies go up to the mmWave band [43]. In particular,
the mmWave communication channel is sparse, dominated by
Line of Sight (LoS), due to the fact that the available propaga-
tion paths are not as rich as those in the sub-6 GHz band. The
mmWave channel model is thereby aligns better to the physical
geometry, which, in conjunction with the mMIMO, triggers the
development of beam domain signal processing for mmWave
communications [1], [45]. These include but are not limited
to, beam training, beam alignment, beam tracking, and beam
management, all of which can be based on an HAD structure
[46]. It is noteworthy that communication in the beam domain
mimics the conventional radar signal processing to a certain
degree, where beam training and tracking can be viewed
as target searching and tracking. To that end, the boundary
between radar and communication turns to be more and more
ambiguous, and the sensing functionality is not necessarily
restricted to the radar infrastructure. Wireless infrastructures
and devices can also perform sensing via its radio emission and
signaling, which forms the technical foundation and rationale
of ISAC [2]. For the sake of clarity, we have summarized the
historical development of S&C and their interplay in Fig. 1.
C. ISAC: A Paradigm Shift in Wireless Network Design
Given the above technical trends, the wireless community
is now witnessing a new paradigm shift that may shape
our modern information society in profound ways. While
wireless sensors are already ubiquitous, they are expected to
be further integrated into wireless networks of the future. More
precisely, sensing functionality could be a native capability of
the next-generation wireless network, not only as an auxiliary
method, but also as a basic service provided to vast number
of users [57]. This magniﬁcent picture has brought us a huge
space for imagination. The sensory data can be collected
and utilized for the purpose of enhancing the communica-
tion performance, e.g., sensing aided vehicular beamforming
and resource management. Moreover, equipped with sensing
functionality, future mobile networks open their “eyes” and
become perceptive networks [41], [50]. Such a network senses
the surrounding environment ubiquitously, providing various
services such as urban trafﬁc monitoring, weather observation,
and human activity recognition. The wealth of data collected
provides the basis for building intelligence both for the ISAC
network itself, and also for emerging smart home and city
applications.
We deﬁne ISAC as a design methodology and corresponding
enabling technologies that integrate sensing and communi-
cation functionalities to achieve efﬁcient usage of wireless
resources and to mutually beneﬁt each other [2]. Within this
deﬁnition, we further identify two potential gains of ISAC,
namely, i) Integration Gain attained by the shared use of
wireless resources for dual purposes of S&C to alleviate
duplication of transmissions, devices and infrastructure, and
ii) Coordination Gain attained from the mutual assistance be-
tween S&C [2]. By foreseeing that ISAC will play a signiﬁcant

5
TABLE I
EXISTING OVERVIEW PAPERS ON ISAC
Existing Works Type Applications Fundamental
Tradeoff
Signal Processing Communications and Networking
Waveform
Design
Transceiver
Design
Resource
Management
Network
Architecture
Network
Protocol
[8], [47]–[49] Tutorial √ √
[50], [51] Survey √ √ √
[10], [52] Survey √ √ √ √
[53] Survey √ √ √ √ √
[54] Survey √ √ √
[55] Survey √ √ √ √
[56] Survey √
[2] Survey √ √ √ √ √
This Paper Survey √ √ √ √ √ √ √
role in B5G/6G cellular systems, the next-generation WLAN,
and the V2X network, we overview the applications and use
cases, technical approaches, as well as challenges and future
directions related to ISAC.
D. Structure of the Paper
In this paper, we provide a comprehensive technical
overview on the theoretical framework of ISAC. We ﬁrst
study use cases and industrial activities related to ISAC in
Sec. II. Then, we look into ISAC theory and performance
tradeoffs between S&C in Sec. III, ranging from information
theoretical limits, to tradeoffs in physical layer (PHY) and
ISAC channels, and to the tradeoff in cross-layer designs.
We then overview signal processing aspects of ISAC, such
as ISAC waveform design, and receive signal processing in
Sec. IV and V , respectively. As a step further, we investi-
gate the mutual assistance between S&C by discussing the
design of the perceptive mobile network in Sec. VI and
VII, respectively, i.e., communication-assisted sensing, and
sensing-assisted communications, including sensing-assisted
beam training, beam tracking, and generic resource allocation.
Finally, we summarize the paper by identifying the potential
interplay between ISAC and other emerging communication
technologies in Sec. VIII.
We note that there have been several survey/tutorial papers
on ISAC-related topics, e.g., [10] on the general designs of
JRC systems, [56] on fundamental limits of ISAC, [58] on
the spectral coexistence of radar and communication sys-
tems, [59] on the sensing-centric DFRC design, [47] on the
mmWave JRC, and [48] on DFRC for autonoumous vehicles.
Unlike previous works that depict only part of the picture
of ISAC, our overview has demonstrated the panorama of
the ISAC theoretical framework, by shedding light on the
basic performance tradeoffs, waveform design, and receiver
design in ISAC systems, as well as the mutual assistance
between S&C at a network level. For clarity, we have provided
a detailed comparison between existing overviews and our
paper in TABLE. I. Our hope is that this paper can provide a
reference point for wireless researchers working in the area of
ISAC, by offering both the bird-eye view and technical details
in the state-of-the-art ISAC innovations.
II. A PPLICATIONS AND INDUSTRIAL PROGRESS
In this section, we ﬁrst extend the use case studies in [2]
to further illustrate our ISAC vision of the future wireless
networks. In particular, we elaborate seven potential ISAC
application scenarios followed by several key use cases for
each. Then, recent ISAC-related industrial activities and re-
search efforts are introduced to ﬁll the gap between academia
and industry communities.
A. Case Studies
1) Sensing as a Service: The recent deployment of dense
cellular networks as part of 5G provides unique opportunities
for sensing. Current communication infrastructures can be
reused for sensing with only small modiﬁcations in hardware,
signaling strategy, and communication standards. In such a
case, integrating sensing into current IoT devices and cellular
networks would be performed rapidly and cheaply, by reusing
reference or synchronization signals as sensing waveforms. As
a step forward, sensing and communication functionalities can
be fully integrated into all radio emissions [60], where both
pilot and payload signals can be exploited for sensing. This
kind of ISAC strategy is able to achieve better integration
and coordination gains, however, raising more difﬁculties in
receiver architecture and signaling designs, which will be
detailed in Sec. VI.
With the use of ISAC technologies, the role of existing
cellular networks will turn to a ubiquitously deployed large-
scale sensor network, namely a perceptive network [50],
which triggers a variety of novel applications for the current
communication industry. We provide some examples below:
Enhanced Localization and Tracking : Localization has
been a key feature in the standardization, implementation,
and exploitation of existing cellular networks, from 1G to the
future 6G [61]. Due to the low range and angle resolutions
that are respectively caused by the bandwidth and antenna
limitations, most of current cellular networks (i.e. 4G and
5G) only provide measurement data with meter-level accu-
racy to assist in global navigation satellite systems (GNSS).
According to the key parameter indicators (KPIs) of 5G New
Radio (NR) Release 17 [62], the highest required localization
accuracies are 0.2 m/1 m horizontally/vertically in industrial

6
IoT applications, which are unable to meet the requirement
of future applications. Particularly, location resolution require-
ments to pinpoint the position of users are higher in indoor
environments than that in outdoor, e.g., indoor human activity
recognition [63] (∼1 cm), autonomous robot and manufactur-
ing [64] (∼5 mm). On the other hand, current cellular based
localization technologies are mostly implemented in a device-
based manner, where a wireless equipment (e.g., a smartphone)
is attached to the locating object by computing its location
through signal interactions and geometrical relationships with
other deployed wireless equipments (e.g. a Wi-Fi access point
or a base station (BS)). However, the device-based approach
limits the choice of locating objects and does not generalize
to diverse scenarios.
Beneﬁting from additional Doppler processing and by ex-
ploiting useful information from multi-path components, ISAC
enabled cellular networks are able to improve the localization
accuracy compared to current localization technologies. On
top of that, a cellular network with sensing functionality is
not limited to just pinpointing the location of a certain object
with a smartphone, but also suits boarder scenarios that extract
spectroscopic and geometric information from the surrounding
environment.
Area Imaging: The RF imaging technology generates high-
resolution, day-and-night, and weather-independent images
for a multitude of applications ranging from environmen-
tal monitoring, climate change research, and security-related
applications [65]. Importantly, compared to camera based
imaging, it is less intrusive and allows focusing on the intended
information without revealing sensitive information in the sur-
rounding environment. Due to the narrow-band nature of past-
generation cellular systems, the range resolution is roughly
meter-level which does not support high-resolution services.
Thanks to the deployment of mmWave and massive MIMO
technologies, future BSs could possibly pursue high range
and angle resolutions by cooperatively sensing and imaging
a speciﬁed area. In such a case, the radio access network
acts as a distributed MIMO radar as elaborated in Section VI.
Consequently, the future cellular network and user equipment
(UE) could “see” the surrounding environment, which would
further support high-layer applications such as digital twins,
virtual reality, and more [66]. Furthermore, with signiﬁcantly
improved imaging resolutions due to higher frequencies, future
cellular network would also support spectrogram-related and
spatial/location-aware services. Finally, cellular BSs and UEs
with imaging abilities could provide additional commercial
values to traditional telecommunication carriers, as a new
billing service for civilians.
Drone Monitoring and Management : In recent years,
the enthusiasm for using UA Vs in civilian and commercial
applications has skyrocketed [67]. However, the civilization of
drones is posing new regulatory and management headaches.
As an aerial platform that could ﬂy over various terrains,
drones have the potential to be employed in non-ﬂy zones
and in illegal activities, e.g., unauthorized reconnaissance,
surveillance of objects and individuals. With the merits of low
attitude, small size and varying shape, such non-cooperative
UA Vs always operate below the line-of-sight (LoS) of current
airborne radars, and are difﬁcult to be detected by other
surveillance technologies such as video or thermal sensor. The
existing cellular network with sensing functionality would not
only provide an affordable solution to monitor non-cooperative
UA Vs in low-attitude airspace, but act as a radio access
network to manage and control cooperative UA Vs with cellular
connections, and assist their navigation in swarms. As a
result, the ISAC cellular network could develop into the drone
infrastructure that provides drone monitoring and management
services to secure future low-attitude airspace applications.
2) Smart Home and In-Cabin Sensing: Currently, in most
indoor applications, such as in-home and in-cabin scenarios,
electronic devices are expected to be interactable and intel-
ligent to ﬁt out a comfortable, convenient and safe living
condition. Aiming for this purpose, smart IoT devices should
be able to understand the residents both physically and physi-
ologically. With the merits of privacy-preserving, unobtrusive
and ubiquitous, standardized wireless signals have been widely
employed to ﬁgure out what is going on in the surrounding
indoor scenario [68], [69].
Recently, ISAC enabled IoT has shown great potential in
daily activity recognition, daily health care, home security,
driver attention monitoring, etc., in which several of them have
been implemented into household products [70]. To mention
but a few:
Human Activity Recognition : Activity recognition is es-
sential to both humanity and computer science, since it records
people’s behaviors with data that allows computing systems
to monitor, analyze, and assist their daily life. Over-the-air
signals are affected by both static or moving objects, as
well as dynamic human activities. Therefore, amplitude/phase
variations of wireless signal could be employed to detect or to
recognize human presence/proximity/fall/sleep/breathing/daily
activities [3], by extracting the range, Doppler, or micro-
Doppler features while moving indoor. Moreover, if the
sensing resolution is high enough, fatigue driving could be
recognized by identifying the driver’s blink rate. By integrating
sensing functionality into current commercial wireless devices,
e.g., Wi-Fi devices, they are able to detect and recognize
resident’s activities to support a smart and human-centric
living environment.
Spatial-aware Computing : Let’s switch our sight from
the resident to the indoor device. The further exploitation
of geometric relationship among massive IoT devices also
potentially enhance resident well-being as well as living
comfort. The ubiquity of wireless signals with high spatial
resolution represent an opportunity for gathering all spatial
relationships between the indoor devices [71], which may be
densely and temporarily deployed in a cramped space. For
instance, a smartphone with centimeter-level sensing precision
is able to pinpoint the location of any electronic devices with
the angle resolution reaching ±3°. Therefore, once directing
the smartphone towards a given device, they would connect
and control with each other automatically [72].
In addition, knowing where the devices are in space and
time promises a deeper understanding of neighbors, networks,
and the environment. By considering spatial relationships
between moving devices and access points, initial access

7
TABLE II
CASE STUDIES AND KEY PERFORMANCE INDICATORS
Key Performance Indicators
Application Case Max. Range Max.Velocity Range Doppler Temporal Angular Data Rate Per mmWave
(m) (m/s) Resolution Resolution Resolution Resolution User (Avg. / Peak.)
• Drone Monitoring and Management 500 40 / Low /
• Localization and Tracking in Cellular Network 300 10 / Low/Very High /
• Human Authorization and Identiﬁcation 300 5 / Low/Very High /
Sensing as • Human Counting 200 5 Low/Very High /
a Service • Area Imaging 200 / Low/Very High √
• Mobile Crowd Sensing 300 5 / Low/Very High /
• Channel Knowledge Map Construction 300 5 / Low/Very High /
• Passive Sensing Network 300 30 / / Low/Very High /
• Human Presence Detection 20 2 High /
• Human Proximity Detection 20 4 High /
• Fall Detection 10 3 High /
• Sleep Monitoring 1 2 High /
Smart Home • Daily Activity Recognition 10 4 High /
and In-Cabin • Breathing/Heart Rate Estimation 1 2 High /
Sensing • Intruder Detection 20 5 High /
• Location-aware Control 20 3 / High /
• Sensing Aided Wireless Charging 5 4 High √
• Passenger Monitoring 2 / High √
• Driver Attention Monitoring 1 / High √
• Raw Data Exchange and High Precision Location 300 30 / / High /
• Secure Hand-Free Access 300 / / Low/Very High /
Vehicle to Everything • Vehicle Platooning 100 30 / High /
• Simultaneous Localization and Mapping 300 30 / Low/Very High /
• Extended Sensor 300 30 / Low /
• Employee Localization and Authorization 1000 5 / Low/Very High /
Smart Manufacturing • Manufacture Defect Analysis 20 / / High √
and Industrial IoT • Automatic Guided Vehicles 500 5 / Low √
• Predictive Maintenance 100 / / Low/Very High √
Remote Sensing • Drone Swarm SAR Imaging 1000 40 / / Low √
and Geoscience • Satellite Imaging and Broadcasting 10000 / / / / Low √
• Weather Prediction 500 / / / / Low/Very High √
Environmental • Pollution Monitoring 200 / / / / Low/Very High √
Monitoring • Rain Monitoring 200 / / / / Low/Very High √
• Insect Monitoring 200 / / / / Low/Very High √
• Gesture Recognition 1 20 / Low/Very High √
Human Computer • Keystroke Recognition 1 20 / Low/Very High √
Interaction • Head Activity Recognition >2 20 / Low/Very High √
• Arm Activity Recognition >2 10 / Low/Very High /
(*) In order to indicate different requirements of Range/Doppler/Temporal/Angular resolutions, we artiﬁcially categorize these KPI values into four levels,
e.g. : very low, : low, : high, : very high.
(*) The symbol “/” represents that there are few requirements on this scenario.
or cross-network handover operations would probably be
expedited, rather than SINR-only considerations, as will be
detailed in Section VII-C. Furthermore, spatial-aware comput-
ing promises to coordinate distributedly deployed household
products to jointly analyze the movement, understand patterns
of mobility, and eventually to support augmented virtual reality
applications.
3) Vehicle to Everything (V2X): Autonomous vehicles
promise the possibility of fundamentally changing the trans-
portation industry, with an increase in both highway capacity
and trafﬁc ﬂow, less fuel consumption and pollution, and
hopefully fewer accidents [73]. To achieve this, vehicles are
equipped with communication transceivers as well as various
sensors, aiming to simultaneously extract the environmental
information and exchange information with road side units
(RSUs), other vehicles, or even pedestrians [74]. The com-
bination of sensing and communications is provably a viable
path, with reduced number of antennas, system size, weight
and power consumption, as well as alleviate concerns for
electromagnetic compatibility and spectrum congestion [73].
For example, ISAC-aided V2X communications could provide
environmental information to support fast vehicle platooning,
secure and seamless access, simultaneous localization and
mapping (SLAM). RSU networks can provide sensing services
to extend the sensing range of a passing vehicle beyond its
own LoS and ﬁeld-of-view (FoV). We brieﬂy discuss two
representative use cases:
Vehicle Platooning: Autonomous vehicles in tightly spaced,
computer-controlled platoons will lead to increased highway
capacity and increased passenger comfort. Current vehicle
platooning schemes are mostly based on cooperative adaptive
cruise control (CACC) through a conventional leader-follower
framework [75], [76], which requires multi-hop Vehicle-to-
Vehicle (V2V) communications to transfer the state informa-
tion of each vehicle over all the platooned vehicles. However,
the high latency of multi-hop communications leads to the out-

8
of-sync problem on situational information of the platooned
vehicles, particularly when the platoon is very long and highly
dynamic. In this case, platooned vehicles that are unaware of
situational changes increase the control risk. RSU, as vehicle
infrastructure, offers a more reliable approach to form and
maintain the vehicle platoon, as it serves multiple vehicles
simultaneously [77], [78]. More importantly, the wireless
sensing functionality equipped on the RSU provides an al-
ternative way to acquire vehicles’ states in a fast and cheap
manner, which in turn facilitates the V2I communications
and platooning by signiﬁcantly reducing the beam training
overhead and latency [79], [80], as will be detailed in Sec.
VII.
Simultaneous Localization and Mapping (SLAM) : Joint
localization and mapping can provide vehicles with situa-
tional awareness without the need for high-precision maps
[81]. Based on the environment data extracted from various
sensors, a vehicle could obtain its current location and the
spatial relationship with the objects in a local area, based
on which to perform navigation and path planning. Most of
previous SLAM studies rely on camera or lidar sensors, which
overlooked the fact that the channel propagation characteristics
could be utilized to construct 2D or 3D maps of the surround-
ing environment. In this sense, ISAC-based radio sensing has
the potential to become a key component to be integrated
into current SLAM solutions, by endowing communication
devices with sensing functionalities while requiring minimum
hardware/software modiﬁcation. The ISAC receive signal pro-
cessing pipeline for SLAM poses a number of challenges, such
as the separation of sensing and communication signals, and
the reconstruction of high-quality point cloud.
4) Smart Manufacturing and Industrial IoT: The penetra-
tion of wireless networks in the hard industries such as con-
struction, car manufacturing, and product lines among others
has given rise to the revolution of Industrial IoT [82], showing
orders-of-magnitude increase in automation and production
efﬁciency. Such scenarios often involve network nodes and
robots that coordinate to carry out complex and often delicate
tasks, that require connectivity in large numbers and with
severe latency limitations.
ISAC offers paramount advantages in such smart factory
scenarios, where in addition to ultra-fast, low-latency commu-
nications typical for such scenarios [83] the integration of the
sensing functionality will enable the factory nodes and robots
to seamlessly navigate, coordinate, map the environment and
potentially cut signaling overheads dedicated to such function-
alities. The desired technology here involves elements of the
above cases such as swarm navigation, platooning, imaging,
but under the important constraints of ultra reliability, ultra low
latency and massive connectivity, often encountered in smart
factory scenarios [82].
5) Remote Sensing and Geoscience: Radar carried by satel-
lites or planes has been widely applied in geoscience and
remote sensing to provide high-resolution all-weather day-and-
night imaging. Today, more than 15 spaceborne radar systems
are operated for innumerous applications, ranging from en-
vironmental and Earth system monitoring, change detection,
4D mapping (space and time), security-related applications
to planetary exploration [65]. All these radars are operated
in synthetic aperture radar (SAR) mode, mostly using chirp
or OFDM waveforms. Communication data can be embedded
into these waveforms, as will be detailed in Sec. IV , enabling
these radar infrastructures to broadcast low-speed data streams
to its imaging area, or provide covert communication services
in a battleﬁeld.
Being able to rapidly deploy and loiter over a disaster
area for hours, drones provide essential emergency response
capability against many natural disasters. Such response tasks
include damage assessment, search-and-rescue operation [84],
and emergency communication for disaster areas. To accom-
plish these tasks, drones should carry various heavy and
energy-consuming payloads, including airborne imaging radar,
communication BS, and thermal sensors, which severely limits
drones’ endurance. Beneﬁting from ISAC, the radio sensing
system and emergency communication system can be merged
to achieve higher energy and hardware efﬁciency, i.e., the
integration gain.
More interestingly, a swarm of drones or satellites could
exchange sensed information, and therefore cooperatively act
as a mobile antenna array forming a large virtual aperture.
In such a case, drone swarm based SAR algorithms may be
exploited to implement a high-resolution low-attitude airborne
imaging system.
6) Environmental Monitoring: Environmental information
such as humidity and particle concentration can be indicated
by the propagation characteristics of transmitted wireless sig-
nals [85]. Wireless signals operating on different frequencies
are aware of different environmental changes. For instance,
high-frequency mmWave signals are sensitive to humidity
because they are closer to the water vapor absorption bands.
By analyzing the path-loss data of city-wide mmWave links
between BSs and smart phones, it is possible to monitor
rainfall or other variations in the atmospheric environment
such as water vapor, air pollutants, and insects. As such, a
cellular network with a sensing function serves as a built-
in real-time monitoring facility and therefore, be utilized
as a widely-distributed large-scale atmospheric observation
network. Moreover, with the continuous exploitation of higher
frequency, future urban cellular networks could also monitor
locusts or other insects, serving as an insect observation
network in urban areas.
7) Human Computer Interaction (HCI): An object’s
characteristics and dynamics could be captured from the
time/frequency/Doppler variations of the reﬂected signal.
Therefore, gesture interaction detection via wireless signals is
a promising HCI technology. For instance, a virtual keyboard
that projects onto a desk could be constructed by recognizing
the keystroke gesture at the corresponding position. Another
well-known example is the Soli project of Google [86], which
demonstrated radio sensing in HCI. Based on advanced signal
processing from a broad antenna beam, Soli delivers an
extremely high temporal resolution instead of focusing on
high spatial resolution, i.e. its frame rates range from 100 to
10,000 frames per second, such that high dynamic gesture
recognition is feasible. Beneﬁting from integrating sensing
capability into smartphone and other UEs’ communication

9
systems, gesture-based touchless interaction may serve as the
harbinger of new HCI applications, which may play a key
role in the post COVID-19 era. The main challenges are how
to improve micro-Doppler recognition accuracy and how to
design a signal processing strategy providing high temporal
resolution.
We summarize the above case studies and required KPIs for
different ISAC use cases in TABLE II, where supplementary
information on other potential cases within different scenarios
is also provided.
B. Industry Progress and Standardization
As initial research efforts towards 6G are well-underway,
ISAC has drawn signiﬁcant attention from major industrial
companies. Recently, Ericsson [87], NTT DOCOMO [88],
ZTE [89], China Mobile, China Unicom [89], Intel [90],
and Huawei [66] have all suggested that sensing will play
an important role in their 6G white papers and Wi-Fi 7
visions. In particular, in November 2020 Huawei identiﬁed
harmonized sensing and communication as one of the three
new scenarios in 5.5G (a.k.a. B5G) [91]. The main focus of
this new technology is to exploit the sensing capability of
the existing massive MIMO BS, and to support future UA Vs
and automotive vehicles. Six months later, Huawei further
envisioned that 6G new air interface will support simultaneous
wireless communication and sensing signaling [66]. This will
allow ISAC enabled cellular networks to “see” the physical
world, which is one of the unique capabilities of 6G. Nokia
has also launched a uniﬁed mmWave system as a blueprint of
future indoor ISAC technology [92].
The IEEE standardization association (SA) and the third-
generation partnership project (3GPP) have also devoted sub-
stantial efforts to develop ISAC related speciﬁcations. In
particular, IEEE 802.11 formed the WLAN Sensing Topic
Interest Group and Study Group in 2019, and created a new
ofﬁcial Task Group IEEE 802.11bf [93] in 2020 1, intend-
ing to deﬁne the appropriate modiﬁcations to existing Wi-
Fi standards to enhance sensing capabilities through 802.11-
compliant waveforms. On the other hand, in the NR Release
16 speciﬁcation, the redeﬁned positioning reference signal
(PRS) obtains a more regular signal structure and a much
larger bandwidth, which allows for easier signal correlation
and parameter estimation (e.g., by estimating the time of
arrival, ToA). Moreover, the measurements for PRSs received
from multiple distinct BSs could be shared and fused at
either the BS side or the UE side, which further enhance the
parameter estimation accuracy to support advanced sensing
ability. Furthermore, to foster the research and innovation
surrounding the study, design, and development of ISAC, IEEE
Communications Society (ComSoc) established an Emerging
Technology Initiative (ETI) 2 and IEEE Signal Processing
Society (SPS) created a Technical Working Group (TWG) 3,
all focusing on integrated sensing and communications.
1https://www.ieee802.org/11/Reports/tgbf update.htm
2https://isac.committees.comsoc.org/
3https://signalprocessingsociety.org/community-involvement/
integrated-sensing-and-communication-technical-working-group/integrated
III. P ERFORMANCE TRADEOFFS IN ISAC
In this section, we identify performance tradeoffs in ISAC,
including tradeoffs in information-theoretical limits, PHY
performance, propagation channels, and cross-layer metrics.
We ﬁrst introduce basic S&C performance metrics, and then
provide some insights into their connections and tradeoffs.
A. S&C Performance Metrics
1) Sensing Performance Metrics: Sensing tasks can be
roughly classiﬁed into three categories, detection, estimation,
and recognition, which are all based on collecting signals/data
with respect to the sensed objects [3]. While these terminlogies
can have varying connotations under different scenarios, and
can be performed over different layers, we attempt to deﬁne
them as follows:
• Detection: Detection refers to making binary/multiple
decisions on the state of a sensed object, given the
noisy and/or interfered observations. Such states typically
include: presence/absence of a target (PHY), and occur-
rence of an event (application layer), e.g., motion detec-
tion. This can be modeled as a binary or multi-hypothesis
testing problem. Taking the binary detection problem as
an example, we choose from the two hypotheses H1 and
H0, e.g., target present or absent, based on the observed
signals. Detection metrics include detection probability,
which is deﬁned as the probability thatH1 holds true and
the detector choosesH1, and the false-alarm probability,
thatH0 holds true but the detector chooses H1 [94].
• Estimation: Estimation refers to extracting useful pa-
rameters of the sensed object from the noisy and/or
interfered observations. This may include estimating dis-
tance/velocity/angle/quantity/size of target(s). Estimation
performance can be measured by mean squared error
(MSE) and Cram´er-Rao Bound (CRB) [95]. In particular,
MSE is deﬁned as the mean of the squared error between
the true value of a parameter θ and its estimate ˆθ. CRB is
a lower bound on the variance of any unbiased estimator
over θ, which is deﬁned as the inverse of the Fisher
Information (FI). FI is the expectation of the curvature
(negative second derivative) of the likelihood function
with respect to θ, which measures the “sharpness” or the
accuracy of the estimator.
• Recognition: Recognition refers to understanding what
the sensed object is based on the noisy and/or interfered
observations. This may include target recognition, and
human activity/event recognition. Recognition is typically
deﬁned as a classiﬁcation task on the application layer,
whose performance is evaluated by the recognition accu-
racy [96].
For sensing tasks over PHY , detection probability, false-alarm
probability, MSE, and CRB are of particular interest. For
higher-layer applications, recognition accuracy is at the core
of learning based schemes. More advanced sensing tasks, e.g.,
imaging, require multiple detection and estimation operations
to be performed over a complex target.

10
2) Communication Performance Metrics: Similar to sens-
ing, communication tasks can also be built on different layers.
In this section, we consider PHY performance metrics for
communications. In general, communication performance can
be evaluated from two aspects, i.e., efﬁciency and reliability,
with the following deﬁnitions:
• Efﬁciency: The successful transmission of the informa-
tion is at the cost of wireless resources, e.g., spectrum,
spatial, and energy resources. Accordingly, efﬁciency is a
metric to evaluate how much information is successfully
delivered from the transmitter to the receiver, given
limited available resources [97], [98]. Spectral efﬁciency
and energy efﬁciency are widely adopted, deﬁned as the
achievable rate per unit bandwidth/energy, with units of
bit/s/Hz or bits/channel use, and bit/s/Joule, respectively.
Moreover, channel capacity, coverage, and maximum
number of served users are also important efﬁciency
metrics.
• Reliability: A communication system should have re-
siliance towards harmful factors within the communica-
tion channel. In other words, we expect communication
system to operate in the presence of noise, interference,
and fading effects. Accordingly, reliability is to measure
the ability of a communication system to reduce or
even to correct the erroneous information bits [97], [98].
Commonly used metrics include outage probability, bit
error rate (BER), symbol error rate (SER) and frame error
rate (FER).
Signal-to-interference-plus-noise ratio (SINR) plays a key
role that links to both S&C metrics. While the deﬁniton of
SINR may depend on the speciﬁc S&C scenario, in most
circumstances, an increase of SINR leads to improved per-
formance for both functionalities. For instance, the detection
probability for sensing and the achievable rate for communi-
cation both improve at high SINR.
B. Information-Theoretical Limits
Information theory is key in evaluating wireless commu-
nication systems [99]. However, the performance of sensing,
from information theoretical perspectives, is not as clearly de-
ﬁned as in that of communications. Therefore, new analytical
techniques are needed to evaluate ISAC systems [56].
The most well-known information theoretical result related
to ISAC comes from the seminal paper by Guo et al. [100],
which connects the input-output mutual information, a com-
munication metric, and the minimum mean squared error
(MMSE), a sensing metric, via an elegant formula. Given a
real-valued Gaussian channel and denoting its received signal-
to-noise ratio as snr, the mutual information I (snr) and the
MMSE MMSE (snr) of the channel input and output are
related by
d
d snrI (snr) = 12MMSE (snr). (1)
That is, the derivative of the mutual information with respect
to snr is equal to half of the MMSE regardless of the input
statistics. Eq. (1) highlights a connection between information
Encoder Decoder
W
S
( | , )p y x s
( ),X W S
Y
( ˆ )ˆ,WS
(a)
Encoder
Estimator
Receiver
SP
ˆS
W
iX
|YZ XSP
1iZ −
iS
iY
ˆW
Transmitter
(b)
Fig. 3. (a) Information transmission over a state-dependent channel; (b)
Mono-static ISAC Channel: Information transmission over a state-dependent
channel with generalized feedback.
theory and estimation theory, which play fundamental roles in
communication and sensing, respectively. It can be observed
from (1) that, while a Gaussian input maximizes the mutual
information for Gaussian channels, it also maximizes the
MMSE, making it the most favorable for communication yet
the least favourable for sensing.
More relevant to ISAC, the classical capacity-distortion
tradeoff was ﬁrst studied in [101] by Chiang and Cover. The
basic scenario is to consider a communication problem with
channel state information [102]–[105]. As shown in Fig. 3 (a),
the sender wishes to transmit both pure information, i.e., an
index W∈
{
1, 2,..., 2nR}, and description ˆS of the channel
state S to the receiver. Given the information index W and
state S, the sender transmits a code X (W,S ) to the receiver,
with a rate of R. The receiver observes
Y ∼
∏n
i=1
p (yi|xi,si ). (2)
The receiver then decodes the information fromY as ˆW (Y )∈{
1, 2,..., 2nR}, and estimates the state as ˆS (Y ). Deﬁne the
decoding error probability and state estimation error as
P(n)e = 12nR∑2nRi=1 Pr{ ˆW⁄=i|W =i},
D = E
{
d
(
S, ˆS
)}
,
(3)
whered
(
S, ˆS
)
is a distortion measure between S and ˆS. We
say that a rate-distortion pair (R,D ) is achievable if there
exists a sequence of
(
2nR,n) codesX (W,S ), such that [103]
E
{
d
(
S, ˆS
)}
≤D,P(n)e → 0,n→∞. (4)
If the distortion function is chosen as the squared state
estimation error, then the estimation MSE can be given as
E
{
d
(
S, ˆS
)}
= 1n E‖‖‖S− ˆS (Y )‖‖‖2. (5)
By leveraging the above metric for state estimation and given
a state-depenedent Gaussian channel Y =X (W,S ) +S +N,

11
where Si∼N (0,QS),Ni∼N (0,QN), the Pareto-optimal
boundray of the (R,D ) pair is [103]
(R,D ) =
 12 log(1 + γPQN),Q S (γP +QN )(√QS +√(1−γ)P)2 +γP +QN

,
γ∈ [0, 1],
(6)
where 1n E{∑ni=1X2i (W,S )} ≤ P is an expected power
constraint on X. It can be shown that the above tradeoff
is achieved by the power-sharing strategy, which splits the
transmit power into γP and (1−γ)P , for transmitting the
pure information and a scaled signal of the channel state, re-
spectively [103]. That is, the power resource is shared between
pure information delivering and channel state estimation to
achieve the optimal tradeoff.
The above rate-distortion tradeoff fails to capture an impor-
tant feature for typical ISAC scenarios, i.e., the estimation of
a target from a reﬂected echo. Indeed, in mono-static radar,
it is impossible for the transmitter to know the target channel
state a priori, otherwise there is no point to sense the target.
The work of Kobayashi and Caire proposed to model the
target return as a delayed feedback channel [106]. As shown
in Fig. 3 (b), the channel state is available at the receiver,
but is unknown to the transmitter. At each transmission, the
transmitter reconstructs the state estimate ˆS from the delayed
feedback outputZ∈Z via an estimator. By picking a message
W , the transmitter sends a symbol X ∈X via an encoder
based on both W and ˆS. The channel outputs Y ∈Y to the
receiver, and feeds back a state to the transmitter. The joint
distribution of SXYZ ˆS can be expressed by
PSXYZ ˆS (s,x,y,z, ˆs) =
PS (s)PX (x)PYZ|XS (y,z|x,s )P ˆS|XZ ( ˆs|x,z ). (7)
Given a distortionD, the capacity-distortion tradeoff C (D) is
deﬁned as the supremum of the rate R, such that the (R,D )
pair is achievable.
With the above model at hand, and by imposing an average
power constraint, the capacity-distortion tradeoff is [106]
C (D) = max
PX: 1n ∑ni=1 E{X 2i}≤PI (X;Y|S)
s.t. E
{
d
(
S, ˆS
)}
≤D,
(8)
where PX denotes the distribution of channel input X. The
above problem is convex in general, and can be solved via a
modiﬁed Blahut-Arimoto algorithm. As a step further, multi-
user channels are considered under this framework, where
inner and outer bounds for capacity-distortion region are
investigated in terms of both multiple access and broadcast
channels. We refer the reader to [106]–[108] for more details.
C. Tradeoff in PHY
When wireless resources are shared between S&C function-
alities, their integration into a common infrastructure allows
the design of scapable tradeoffs between, often contradictory,
sensing and communication objectives and metrics. In general,
PHY tradeoffs can be analyzed by investigating the relation-
ship between the native performance metrics of S&C, which
follows exactly the spirit of the information theoretical frame-
work introduced above. Alternatively, one may also deﬁne a
new information metric for sensing, which is more convenient
to tradeoff with conventional communication metrics. In what
follows, we overview recent works focusing on both aspects.
1) Tradeoff between Native S&C Metrics: PHY sensing
performance is typically measured by the detection probability
and the MSE, respectively. In the event that a closed-form
expression for the MSE is not obtainable, CRB, which rep-
resents the lower bound on the variance of all the unbiased
estimators, is an alternative option, as it can often be expressed
analytically.
Detection vs. Communication: We consider a tradeoff
example between the detection probability and the achievable
rate, which was proposed in [109] for a joint communication
and passive radar system. As shown in Fig. 4 (a), an ISAC
transmitter emits a sensing waveform sR (t) to detect targets
using a portion of its total power budget, and emits a communi-
cation waveformsC (t) using another portion. The two signals
are scheduled over orthogonal resources (time-frequency) such
that they are not interfering with each other. The sensing
receiver (SR) receivessR (t) from both the direct channel and
the surveillance channel, and wishes to detect the presence of
a target in the latter. On the other hand, the communication
user (CU) receives sC (t), which contains useful information.
The problem is then to optimally allocate power to S&C
functionalities, such that the detection performance can be
optimized while ensuring a minimum communication rate.
This can be formulated as the following optimization problem
max
PR,PC
PD s.t.R ≥Rth, PR +PC =PT, (9)
where PR and PC represent the transmit power of radar
and communication signals, respectively, and PT is the total
power budget. PD denotes the radar detection probability,
R = log (1 +PCγc) is the achievable rate, with γc being the
communication channel gain normalized by the noise variance.
Finally,Rth is a rate threshold.
In a passive radar system, the SR detects the target in the
surveillance channel by correlating the reﬂected signal with
the reference signal received from the direct channel [110].
By sampling the received signals as L time-domain samples,
the detection problem can be modeled as the following binary
hypothesis testing problem (ignoring clutter):
H0 :
{
yd =γdGdsR + nd
ys = ns
, H1 :
{
yd =γdGdsR + nd
ys =γsGssR + ns
,
(10)
whereH0 andH1 stand for the hypotheses of target absent
(null hypothesis) and target present, yd and ys are the signals
received from direct and surveillance channels, Gd and Gs
represent the L×L unitary delay-Doppler operator matrices
corresponding to the direct and surveillance channels, respec-
tively, with γd and γs being the scalar coefﬁcients of the
two channels. Finally, nd and ns are additive white Gaussian
noise (AWGN) with variance σ2. The detection is performed
via a generalized likelihood ratio test (GLRT), for which the

12
Comms User
Passive Sensing 
Receiver
ISAC Transceiver
Surveillance 
Channel Direct 
Channel
Target
(a)
CU 1
CU 2
CU K
ISAC Transceiver
...
Target (b)
Fig. 4. (a) Joint passive sensing and communication; (b) Joint active sensing and multi-user communication.
corresponding PD can be approximated in the case of high
direct-path SNR (D-SNR) as
PD≈Q1


√
2PR|γd|2
σ2 ,
√
2γ

, (11)
where Q1 (a,b ) denotes the Marcum Q-function of the ﬁrst
order with parametersa andb, andγ is the detection threshold.
Using the rate expression, and the relation PR +PC = PT ,
the detection probability can be recast as [109]
PD≈Q1


√
2
(
PT− 1γc (2Rth− 1))|γd|2σ2 ,√2γ.
(12)
In (12), the sensing metricPD is related to the communication
rate threshold Rth, which clearly shows that there exists
a tradeoff between S&C if the power resources are shared
between them. In [111], the authors further generalize the
above power allocation design to a multi-static passive radar-
communication system. The approach proposed in [109], [111]
can also be extended to active and monostatic ISAC/radar-
communication systems.
Estimation vs. Communication: While the assumption of
non-overlapping resources makes the analysis more tractable,
this results in low efﬁciency, and does not address the more
practical secenairos where resources are required to be reused
between S&C. To this end, the authors of [112] consider
optimizing estimation performance of an ISAC system via the
use of a common waveform, where the temporal, spectral,
power, and signaling resources are fully reused for S&C,
thus to achieve the maximum integration gain. Consider a
multi-antenna ISAC transceiver with Nt transmit and Nr≥
Nt receive antennas, which serves K single-antenna users,
and in the meantime detects target(s), as shown in Fig. 4
(b). This forms a multi-user multi-input single-output (MU-
MISO) downlink communication system as well as a monos-
tatic/active MIMO radar. By transmitting an ISAC waveform
matrix X∈ CNt×L, which is constrained by a power budget
PT , the BS receives the following echo signal
YR = GX + NR, (13)
where G ∈ CNr×Nt represents the target response matrix
(TRM), which can be of different forms for different target
models, and NR is an AWGN matrix with variance of σ2R.
The receive signal model for multi-user communication is
YC = HX + NC, (14)
where H = [h1, h2,..., hK]H∈ CK×Nt is the communica-
tion channel matrix, which is assumed to be known to the BS,
and again, NC is an AWGN matrix with variance σ2C.
The maximum likelihood estimation (MLE) of G is known
to be ˆGMLE = YRXH(XXH)−1 [95]. Accordingly, the
MSE of estimating G can be computed as [95]
E
{‖‖‖G− ˆGMLE‖‖‖2} = σ2RNrL tr(R−1X ), (15)
where RX = 1LXXH is the sample covariance matrix of X.
Note that since the MLE problem reduces to a linear estimation
problem in the presence of the i.i.d. Gaussian noise, its CRB
is achieved by the above MSE. To design an ISAC waveform
X that is favorable for both target estimation and information
delivering, one can formulate an optimization problem as
min
X
tr
(
R−1X ) s.t. ‖X‖2F≤LPT, ci (X) ⊴Ci,∀i, (16)
where ⊴ can represent either ≥,≤, or =, and ci (X) is a
communication utility function constrained by Ci, e.g., per-
user SINR, sum-rate, SER, etc. In (16), an S&C tradeoff exists
due to the reuse of a single waveform X towards conﬂicting
objectives.
Remark: Note that in (16) the existence of R−1X implies that
X is of full rank. Otherwise, an unbiased estimator does not
exist, neither does the MLE [113]. This can be interpreted
as follows. In order to estimate a rank- Nt matrix G, the

13
transmitted waveform should utilize all the available DoFs in
the system, and to transmit a rank- Nt waveform for sensing.
This, however, leads to an interesting conﬂict between S&C.
In conventional MU-MISO downlink, the number of DoFs is
limited by min (Nt,K ), where K ≤ Nt is almost always
the case, especially for mMIMO scenarios. That is to say,
in each transmission, K individual data streams should be
communicated from the BS to K users, which is typically
implemented by precoding a rank-K data matrix SC∈ CK×L
into X. In the event that a linear precoder is employed, i.e.,
X = WCSC, WC = [w1, w2,..., wK]∈ CNt×K, X should
have rank of K, which means that RX ∈ CNt×Nt is rank-
deﬁcient and thereby non-invertible.
To resolve the above issue, a promising method is to
augument the data matrix SC by adding at least Nt− K
dedicated sensing streams SA, which contain no useful in-
formation and are orthogonal to the data streams SC [112],
[114]. Accordingly, the precoding matrix WC should also be
augumented by an additional precoder WA. This suggests that
X = [WC, WA]
[
SC
SA
]
= WCSC + WASA. (17)
By doing so, X can be of full rank. It can be observed at
the receiver that the communication data will be corrupted by
the dedicated sensing streams SA, in which case the per-user
SINR is expressed as (assuming unitary SC and SA)
γk =
⏐⏐hHk wk⏐⏐2
∑K
i=1,i⁄=k
⏐⏐hHk wi⏐⏐2 +‖‖hHk WA‖‖2 +σ2C,∀k, (18)
where the ﬁrst item in the denominator is the multi-user
interference, and the second item is the interference imposed
by dedicated sensing streams. On the other hand, both WCSC
and WASA can be used for monostatic sensing, which sug-
gests that communication will not interfere sensing. Instead, it
will facilitates target estimation4. By substituting (18) into (16)
as communication utility functions, problem (16) minimizes
the estimation MSE subject to per-user SINR constraints,
which can be optimally solved via semideﬁnite relaxation
(SDR) [116].
In addition to improving the sensing performance, the
addition of a dedicated sensing waveform WASA also beneﬁts
the MIMO radar beampattern design. As discussed in [114],
the extra DoFs provided by the dedicated sensing signals
enables the formation of a better MIMO radar beampattern
with guaranteed SINR of CUs, compared to the conventional
ISAC scheme that exploits WCSC only [117]. We refer
readers to [112], [114], [115] for more details on the use of
dedicated sensing signals.
2) Tradeoff between Novel Sensing Metrics and Communi-
cation Metrics: On top of the tradeoff between native S&C
metrics, there were also research efforts focusing on deﬁning
4Notice that the dedicated sensing signals WASA can also be a-priori
designed, and thus can be known at the communication receivers prior to
the transmission. In this case, the communication receivers can pre-cancel the
interference caused by the sensing signals before decoding the communication
signal, thus leading to an increased SINR with
‖‖hHk WA‖‖2 disappeared inthe denominator in (18) [115].
Angle
Resolution Unit and
Information Bit



"0", target absent
"1", target present
Fig. 5. Radar sensing resolution unit.
a new measure of “capacity” for sensing, and in particular for
radar sensing. In light of this, a basic question is, how much
information is gained from a sensing operation?
Guerci et al. [118] studied the radar capacity from a reso-
lution point of view. As shown in Fig. 5, a resolution unit/cell
can be deﬁned in three dimensions, i.e., range, Doppler, and
angle. Each unit accomodates only one point target. If there
are more than one target in the same resoultion unit, the radar
would not be able to identify them and would regard them
as a single target. In this sense, each resolution unit can be
considered as a binary information storage unit where a binary
decision is made for target detection, i.e., “0” = target absent,
“1” = target present. The maximum “capacity” of a moving
target indication (MTI) radar can be expressed by the Hartley
capacity measure as [118]
CR = logNu, (19)
where Nu is the total number of resolution cells, which
satiesﬁes
Nu∝
(Dmax
∆D
)( 2π
∆θ
)(PRF
∆fD
)
, (20)
where ∆D, ∆θ, and ∆fD stand for the range resolution,
angular resolution, and Doppler resolution of the radar, and
Dmax and PRF denote the maximum detectable range and
the pulse repetition frequency (PRF), respectively.
The capacity in (19) is simply a noiseless measure on how
many point targets can be distinguished by the radar system.
Consider an Nt-antenna pulsed radar whose antenna array is
uniformly and linearly placed. Its range, velocity, and angular
resolutions can be calculated by
∆D = c2B, ∆fD = 1Td, ∆θ≈ 2Nt, (21)
where B is the bandwidth, and Td represents the dwell time,
i.e., the duration that a target stays in radar’s illumination. It
can be seen that the resolution of a radar is determined by its
physical limit, or the maximum available amount of temporal,
spectral, and spatial resources. This being the case, it is still not

14
straightforward to see how the capacity in (19) trades off with
the fundamental communication metrics, as it is speciﬁcally
restricted to the identiﬁability of targets.
Inspired by classical rate distortion theory 5, the authors of
[119], [120] proposed the “estimation rate” as a sensing metric.
Consider the range estimation problem in radar sensing. By
transmitting a radar pulse sR (t) with bandwidth B and pulse
durationT , a single target is sensed with delayτ and amplitude
hR, yielding the following echo signal
yR (t) =hR
√
PRsR (t−τ) +nR (t), (22)
wherenR (t) is the AWGN with the variance of σ2R. The CRB
for delay estimation is given by
CRB (τ) ≜σ2τ,est = σ2R8π2h2RB2rmsBTPR, (23)
where Brms is the root-mean-square (RMS) bandwidth of
sR (t).
Suppose that the radar is operating in tracking mode, and
prior knowledge on the range of the target is available, subject
to some random ﬂuctuations. The radar can therefore predict
the delay of the target by leveraging a prediction function,
which we denote as τpre. The true delay for the target can
therefore be expressed as
τ =τpre +npre, (24)
where npre∼N
(
0,σ 2τ,pre) represents the range ﬂuctuation.
The radar estimation rate is deﬁned as the cancellation of
the uncertainty in target parameters per second, with the unit
of bit/s, which is upper-bounded by [120]
Rest≤ Hτ,rr−Hτ,estTPRI , (25)
where TPRI is the pulse repetition interval, and
Hτ,rr = 12 log(2πe(σ2τ,pre +σ2τ,est)),
Hτ,est = 12 log(2πeσ2τ,est) (26)
are the received signal entropy and the estimation entropy,
respectively. Using (23), the estimation rate bound is expressed
as [120]
Rest≤ 12TPRI log
(
1 + 8π2h2Rσ2τ,preB2rmsBTPR
σ2R
)
. (27)
This estimation rate can be then employed to tradeoff with
the communication rate. Let us consider an ISAC receiver,
which receives both the communication signal from the user(s)
and the echo signal reﬂected from the target, yielding
y (t) =hC
√
PCsC (t) +hR
√
PRsR (t−τ) +n (t), (28)
wherehC,PC andsC (t) are the communication channel coef-
ﬁcient, transmit power and communication signal, respectively.
Such a scenario can be modeled as a multi-access channel,
where the target is viewed as a virtual user that unwillingly
communicates information with the ISAC receiver on its
5Note that rate-distortion theory is distinctly different from the rate-
distortion tradeoff discussed above.
ISAC Transceiver
Comms User 
and TargetClutter/NLoS
Clutter/NLoS
Fig. 6. Tradeoff in S&C channels: NLoS Reduction or Exploitation?
parameters [120]. Different inner bounds between communi-
cations rate and estimation rate can be achieved via schemes
of isolated sub-band allocation, successive interference can-
cellation, water ﬁlling, and Fisher Information optimization
[120].
D. Tradeoff in S&C Spatial Degrees-of-Freedom
A fundamental tradeoff naturally arises in ISAC systems due
to the different treatment towards the spatial resources in S&C.
In a generic communication system, one needs to “exploit all
the available degrees of freedom (DoFs) in the channel” [98]
for enhancing the communication performance. For example,
Non-LoS (NLoS) was initially considered harmful to wireless
systems, as it results in channel fading. With the development
of the multi-antenna technology, surprisingly, a common sense
is condensed, that NLoS paths and fading effects can be
exploited to provide diversity and DoFs for MIMO commu-
nications. For sensing, on the contrary, not all the paths are
useful. Instead, some of them may have negative impact on
the sensing performance. In most cases, sensing requires the
existence of an explicit LoS path between the sensor and
the object to be sensed. In typical radar applications, signals
reﬂected by objects other than targets of interest are referred
to as “clutter”, and are regarded as harmful and needs to be
mitigated. NLoS components fall into this category in general.
Accordingly, a speciﬁc propagation path can be useful for both
functinalities, as long as it contains information of the target
of interest. Otherwise, it is useful to communication only, but
harmful to sensing. This again reﬂects the contradictory needs
in S&C.
To see this more clearly, consider a simple scenario shown
in Fig. 6, where a mmWave BS acts also as a monostatic
radar, equipped withNt andNr transmit and receive antennas.
The ISAC BS serves an Nv-antenna vehicle while tracking its
movement, which suggests that the vehicle is both a CU and
a target. By transmitting an ISAC signal matrix X∈ CNt×L,

15
the received signal at the vehicle is expressed as
YC =α0b (φ0) aH (θ0) X
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
LoS
+
∑I
i=1
αib (φi) aH (θi) X
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
NLoS
+ ZC
/dcurly.alt2
Noise
≜ HX + ZC,
(29)
where αi, θi and φi represents the channel coefﬁcient, the
angle of departure (AoD) and the angle of arrival (AoA) of
theith path, with i = 0 andi≥ 1 being the indices of the LoS
path and NLoS paths, at (θ)∈ CNt×1 and av (φ)∈ CNv×1
being the steering vectors for the transmit antenna array of the
BS and the receive antenna array of the vehicle, and I being
the total number of available paths in the channel. Note that
we omit the delay and Doppler of each path without loss of
generality.
By assuming each NLoS path corresponds to a clutter
source, the ISAC BS receives the reﬂected echo from the
vehicle as
YR =β0ar (θ0) aHt (θ0) X/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
Target
+
∑I
i=1
βiar (θi) aHt (θi) X
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
Clutter
+ ZR
/dcurly.alt2
Noise
,
(30)
where βi is the reﬂection coefﬁcient of the ith clutter, and
ar (θ)∈ CNr×1 is the steering vector of the receive antenna
array of the ISAC BS. From (29), we see that the receive SNR
of the vehicle is given by
SNRC =‖HX‖2FLσ2C , (31)
where all the propagation paths contribute to the receive power.
From (30), on the other hand, the signal-to-clutter-plus-noise
ratio (SCNR) of the target return is expressed as [121]
SCNRR =
‖‖β0ar (θ0) aHt (θ0) X‖‖2F‖‖‖∑Ii=1βiar (θi) aHt (θ0) X‖‖‖2F +σ2R. (32)
To balance the S&C performance, the ISAC waveform X
should be carefully designed to allocate power and other
resources to each of the propagation paths, such that both S&C
performance can be guaranteed, where convex optimization
techniques may be employed to solve the problem. The
tradeoff discussed above can be extended to generic ISAC
scenarios with multiple targets/CUs of interest, where multiple
paths can be useful for sensing.
E. Cross-Layer Tradeoff
As discussed in Sec. II, S&C operations can be performed
at different layers, instead of being restricted to the PHY
only. An interesting example is mobile sensing or wireless
sensing, where commercial wireless devices are employed
for both purposes of communication and higher-layer sensing
tasks, e.g., human detection, which is typically realized by
training a deep neural network (DNN) using the sensory data.
Accordingly, the performance tradeoff of S&C may no longer
be analyzed through conventional framework built upon PHY ,
where cross-layer designs are required. In wireless sensing,
a commonly employed sensing metric is the recognition
frequency
time
…… 
Target 1
TS
User 1Target N
TS
…… 
User K
Sensing Phase
Cycle 1
Comms Phase
B
…… 
Target 1
TS
Target N
TS
Sensing Phase
Cycle C
…… 
T
t1 tk
…… 
Fig. 7. Target recognition and communication in a time-division manner.
accuracy rate, i.e., the probability that the mobile sensor
correctly detects the human activities/events. Nonetheless, the
exploitation of the DNN for such sensing tasks makes the
resource allocation between S&C challenging, given that the
relationship between accuracy rate and the amount of allocated
wireless resources could be mathematically intractable for
DNN based recognition tasks.
To reveal the above cross-layer tradeoff, [122] considered
an ISAC scenario in Fig. 7, where the time budget T is
divided into interleaved sensing and communication cycles.
In each sensing cycle, N targets are sensed, each of which is
allocated a sensing duration tS. On the other hand, for each
communication cycle,K users are scheduled through a round-
robin protocol, via allocating each of them a communication
duration t1,t 2,...,t K. By assuming constant-power transmis-
sion, the following multi-objective optimization problem is
formulated to allocate time slots to S&C [122]
max
A,R,C,tk
(A,R )
s.t. A = Θ (C),
R = min
k=1,2..,K
tk
TB log
(
1 +hkPσ2C
)
,
CNtS +
∑K
k=1
tk =T,
(33)
whereA is the sensing accuracy rate of a well-trained DNN,R
is the minimum achievable rate among K users, C stands for
the number of sensing cycles, andhk is the channel coefﬁcient
of the kth user. In particular, the relationship of the accuracy
rate and the allocated number of sensing cycles is represented
byA = Θ (C), which may be an unknown nonlinear function.
The authors proposed to employ the classical nonlinear model
Θ (C) ≈ 1− αC−β to approximately capture the shape
of Θ (C), and to ﬁnd (α,β ) by least-squares ﬁtting using
training data. Problem (33) can be then optimally solved via
the Lagrangian multiplier method, where the Pareto frontier is
achieved.
IV. W AVEFORM DESIGN FOR ISAC
Waveform design plays a key role in ISAC systems, which
mainly focuses on designing a dual-functional waveform that
is capable of S&C by the shared use of signaling resources,
such that the intergation gain can be achieved. Depending on
the integration level, ISAC waveform can be conceived from
the most loosely coupled approach (time/frequency/spatial-
division), to the most tightly coupled one (fully uniﬁed
waveform). In this section, we will ﬁrst overview the ISAC

16
waveform design with non-overlapped resource allocation, and
then discuss approaches for fully uniﬁed waveform design.
A. Non-Overlapped Resource Allocation
It is straightforward to see that S&C can be scheduled on
orthogonal/non-overlapped wireless resources, such that they
do not interfere with each other. This could be realized over
temporal, spectral, or spatial domains, which is known as time-
division ISAC, frequency-division ISAC, and spatial-division
ISAC, respectively.
Time-Division ISAC: Time-division ISAC is the most
loosely coupled waveform design, which can be conveniently
implemented into the existing commercial systems. For in-
stance, in [28], a joint radar-communication waveform de-
sign was proposed, where the transmission duration is split
into radar cycle and radio cycle. In particular, frequency-
modulated continuous waveform (FMCW) with up- and down-
chirp modulations is used for radar sensing, while various
modulation schemes, e.g., BPSK, PPM, and OOK can be
ﬂexibly leveraged for communication. More recently, time-
division ISAC is realized in a number of commercial wireless
standards, such as IEEE 802.11p and IEEE 802.11ad, where
the CEF/pilot signals, originally designed for channel estima-
tion, are exploited for radar sensing [123]–[126].
Frequency-Division ISAC: Frequency-division ISAC is an-
other simple option, which is typically constructed on the basis
of an OFDM waveform. In this sense, it is not as ﬂexible as
its time-division counterpart where any S&C waveforms may
be employed. To be speciﬁc, S&C functionalities are allocated
to different subcarriers given the channel conditions, required
KPIs for S&C, and power budget of the transmitter [127],
[128]. For instance, in [128], a power allocation and subcarrier
selection scheme is designed to minimize the transmit power,
while guaranteeing both the mutual information and achievable
data rate constraints for radar sensing and communications,
respectively.
Spatial-Division ISAC: On top of the above two division
schemes, spatial-division has recently gained attentions due to
research progress in MIMO and massive MIMO technologies
[129]. In such methods, S&C are performed over orthogonal
spatial resources, e.g., different antenna groups [117]. In the
event that the communication channel is dominated by a
LoS component, the S&C waveforms can be transmitted over
different spatial beams, which show strong orthogonality in
the case of massive MIMO [33]. On the other hand, if the
communication channel is composed by rich scattering paths,
the sensing waveform may be projected into its null space to
avoid interfering with the communication functionality [32],
[130].
Although being relatively easy to implement on a single
hardware platform, the above waveform designs suffer from
poor spectral and energy efﬁciencies. To increase the inte-
gration gain to its maximum, it is favorable to design a
fully uniﬁed ISAC waveform, where the temporal, sepctral,
and spatial resources are utilized in a shared and overlapped
manner [34], [35].
B. Fully Uniﬁed Waveform
Fully uniﬁed ISAC waveforms are generally designed fol-
lowing three philosophies, namely, sensing-centric design
(SCD), communication-centric design (CCD), and joint design
(JD) [48], [53], which we elaborate as follows.
1) Sensing-Centric Design: SCD aims to incorporate the
communication functionality into existing sensing wave-
forms/infrastructures. In other words, the sensing performance
needs to be primarily guaranteed. Nevertheless, a pure radar
sensing waveform is unable to be directly exploited for
communcation, as it contains no signaling information. The
essence of SCD is to embed information data into the sensing
waveform, without unduly degrading the sensing performance.
To provide insight into such an operation, consider a radar
waveform matrix SR, and a communication data matrix D.
The sensing-centric waveform can be designed by [131]
X =C (SR, D), (34)
whereC (·) represents the embedding operation. Similar to
Sec. IV-A, the communication data can be embedded into
different domains of the sensing signal, in order to formulate
an ISAC waveform.
Chirp-based Waveform Design (Time-Frequency Do-
main Emdedding): Early SCD schemes typically focus on
time-frequency domain embedding, where a chirp signal,
which is widely employed in various radar applications, acts
as an information carrier [25], [26]. A generic chirp signal is
given by
schirp (t) =A exp
(
j2π
(
f0t + 12kt2
)
+φ0
)
,t∈ [0,T 0],
(35)
where A,f 0,k,φ 0, and T0 stand for the amplitude, start
frequency, chirp slope, initial phase, and duration of the chirp
signal, respectively. The derivative of the overall phase of (35)
with respect to timet is a linear function. This suggests that the
frequency of the chirp signal is linearly increasing with time,
resulting in a bandwidth B =kT0, and large time-bandwidth
productBT0 =kT 20 . Given the design DoFs available in (35),
one may represent communication symbols using the variation
of the parameters A,f 0, and φ0. Accordingly, a wide variety
of modulation formats, e.g., ASK, FSK, and PSK, can be
straightforwardly applied by using chirp signals as carriers.
It is also possible to modulate communication symbols onto
the chirp slope k.
Sidelobe Control Approach (Spatial Domain Emded-
ding): To equip a MIMO radar with communication function-
ality, recent SCD schemes consider embedding useful data into
the radar’s spatial domain [132], [137], [138]. One classical
approach is to represent each communication symbol by the
sidelobe level of the MIMO radar beampattern, where the
main beam is solely used for target sensing [132]. Suppose
that an Nt-antenna MIMO radar is transmitting information
to an Nr-antenna CU located at angle θC. Within each radar
pulse, a Q-bit message is represented by a binary sequence
Bq,q = 1,...,Q . Let SR = [sR,1,..., sR,Q]H∈ CQ×L be Q

17
TABLE III
ISAC W AVEFORM DESIGNS
Waveform
Designs
Methodologies Representative Techniques Pros Cons
Non-overlapped
Resource
Allocation
Time-Division • TD between FMCW and comms modulations [28]
• Using CEF of IEEE 802.11ad frame for sensing [124] Easy to implement Low efﬁciency
Frequency-Division • Subcarrier allocation between S&C in OFDM [128]
Spatial-Division • Antenna separation between S&C [117]
Fully
Uniﬁed
Waveform
Sensing-Centric
• Using chirp signals as information carriers [26]
• MIMO radar sidelobe embedding approach [132]
• Index modulation [133]–[135]
Guaranteed sensing
performance
Low infomation rate/
spectral efﬁciency
Communication-Centric • Using OFDM for sensing [8] Guaranteed comms
performance
Unreliable sensing
performance
Joint Design • Waveform design based on optimization [60], [114], [117], [136] Scalable S&C
performance tradeoff
High complexity
orthogonal radar waveforms. The transmitted ISAC signal can
be represented by
X = WSR, (36)
where W∈ CNt×Q is an ISAC beamforming matrix, which
is expressed as [132]
W = [B1w1 + (1−B1) w0,...,B Qw1 + (1−BQ) w0],
(37)
where w0 and w1 are beamforming vectors associated with
“0” and “1” data, which are designed ofﬂine to satisfy certain
radar beamforming constraints. For example, wi,i = 0, 1 may
be designed by solving the following optimization problem
[132]
min
wi
max
θ
⏐⏐G (θ)−⏐⏐wHi a (θ)⏐⏐⏐⏐, θ∈ Θ
s.t.
⏐⏐wHi a (θ)⏐⏐≤ε,θ∈ ¯Θ, wHi a (θC) =δi, (38)
where a (θ) is the transmit steering vector of the MIMO
radar. The objective function is to approximate the desired
beampattern magnitude G (θ) within the mainlobe region Θ.
The ﬁrst constraint is imposed to control the sidelobe level
within the sidelobe regin ¯Θ. The second constraint is to ensure
that the sidelobe level at the direction of the CU equals to a
given value δi, with δ0 <δ 1.
When transmitting X, the CU receives
YC =βb (φC) aH (θC) WSR + ZC =
αb (φC) aH (θC)
Q∑
q=1
(
Bqw1sHR,q + (1−Bq) w0sHR,q) + ZC,
(39)
whereα is the channel coefﬁcient, b (φ) is the receive steering
vector at the communication receiver, and φC is the angle
of arrival (AoA) of the ISAC signal, which can be readily
estimated at the receiver’s side via various algorithms, e.g.,
MUSIC and ESPRIT.
Matched-ﬁltering YC with the qth waveform yields the
signal vector
yC,q =
{
αb (φC) aH (θC) w0 + zC,q, Bq = 0,
αb (φC) aH (θC) w1 + zC,q, Bq = 1, (40)
where zC,q is the output noise of the q-th matched ﬁlter. Note
that wH0 a (θC) = δ0 < δ1 = wH1 a (θC). By multiplying
(40) with a receive beamformer bH (φC), Bq can be simply
detected as [132]
ˆBq =
{
0,
⏐⏐bH (φC) yC,q⏐⏐<λ,
1,
⏐⏐bH (φC) yC,q⏐⏐>λ, (41)
where λ is a pre-deﬁned threshold. The above scheme can
also be extended to M-ary modulation by designing M
beamforming vectors wi,i = 1,...,M , while maintaining a
desired MIMO radar beampattern.
We show a numerical example of the sidelobe control
scheme in Fig. 8, where a 10-antenna MIMO radar serves
a single CU while formulating a wide radar beam towards
Θ ∈ [−10◦, 10◦]. The CU is located at −50◦. The overall
sidelobe level is controlled to be less than ε = −20dB.
Accordingly, the sidelobe level radiated towards the CU’s
direction alternates between δ0 =−40 dB and δ1 =−20 dB,
which represents the “0” and “1” data. It can be observed in the
ﬁgure that the −50◦ sidelobe is indeed exploited to transmit
communication bits, and that the the two beamforming vectors
generate almost the same pattern at the main beam.
We note that while the main beam shape for target detection
can be kept unchanged in the sidelobe control scheme, it may
not ensure 100% radar performance, as the frequent ﬂuctuation
in the sidelobe of the radar beampattern may lead to high
false alarm rate, which is particularly pronounced when the
communcation channel changes rapidly.
Index Modulation: To fully guarantee the radar sensing
performance, a more promising SCD approach is to realize
ISAC via index modulation. Pioneered by [138], when Nt or-
thogonal waveforms are transmitted by an Nt-antenna MIMO
radar, the communication functionality can be implemented
by shufﬂing the waveforms across antennas. In this case,
the communication codeword is represented by a permutation
matrix, resulting a maximum bit rate of fPRF· log2Nt!, where
fPRF is the radar’s PRF.
As a further study, an index modulation scheme based on
carrier agile phased arrary radar (CAESAR) is proposed to
enable the ISAC capability, namely the multi-carrier agile joint
radar communication (MAJoRCom) system [133], [139]. In

18
-90 -60 -30 0 30 60 90
Angle (Degree)
-40
-35
-30
-25
-20
-15
-10
-5
0
5
10Transmit beampattern (dB)
1st transmit beam (communication SLL = -20.00 dB)
2nd transmit beam (communication SLL = -40.00 dB)
Fig. 8. ISAC beamforming based on sidelobe control.
particular, it randomly changes the carrier frequencies pulse
to pulse, and randomly allocates frequencies to each antenna
element, thus to introduce agility to both spatial and frequency
domains. Suppose that the available carrier frequencies forms
the following set with the cardinality Mf :
F :={fc +m∆f|m = 0, 1,...,M f− 1}, (42)
where fc is the initial carrier frequency, and ∆f is the
frequency step. In each pulse, the radar randomly chooses
Kf frequencies from F. The resultant number of possible
selections is
N1 =
(
Mf
Kf
)
= Mf!Kf! (Mf−Kf)!. (43)
Once Kf frequencies are selected, each antenna will be allo-
cated a carrier frequency to transmit a monotone waveform.
All Nt antennas are arranged into LK = NtKf with LK beingan integer, where antennas in one group share the same carrier
frequency. By doing so, the number of possible allocation
patterns is
N2 = Nt!(LK!)Kf. (44)
Accordingly, the total number of bits that can be represented
by varying the selections of carrier frequencies and allocation
patterns is calculated as
log2N1 + log2N2 = log2
Mf!
Kf! (Mf−Kf)! + log2
Nt!
(LK!)Kf
≈Kflog2Mf +Ntlog2Kf, (45)
where the approximation is based on the Stirling’s
formula. The maximum bit rate is therefore fPRF ·
(Kflog2Mf +Ntlog2Kf). For clarity, a simple example with
2 transmit antennas is illustrated in Fig. 9, where the input bits
are mapped to selected carrier frequencies and antennas using
index modulation.
We note that the sensing performance of MAJoRCom is
almost unaffected by transmitting communication bits, since
Input
bits
Frequency modulation
Spatial modulation
0
1
1
0
Antenna 0
Antenna 1
Antenna 0
Antenna 1
Fig. 9. ISAC signaling based on Index Modulation.
communication codewords are random and equally distributed
over different pulses, just as in a standard CAESAR radar
[139]. This allows the use of random sensing matrices for
range-Doppler reconstruction with guaranteed estimation per-
formance. In addition to the pulsed radar, the index modulation
technique can also be applied in conjunction with frequency
modulated continuous wave (FMCW) signaling, leading to
a FMCW-based radar-communication system (FRaC) [135].
FRaC achieves higher increased bit rate than that of the
MAJoRCom, through an extra level of phase modulation on
the ISAC signal.
Note that most SCD schemes employ slow-time coding, i.e.,
inter-pulse modulations rather than inner-pulse approaches,
resulting in a bit rate that is tied to the PRF of the radar. Conse-
quently, while SCD provides a favorable sensing performance,
its application is limited to scenarios requiring low/moderate
data rate only.
2) Communication-Centric Design: In contrast to SCD,
communication-centric design is to implement the sens-
ing functionality over an existing communication wave-
form/system, i.e., communication is the primary functionality
to be guaranteed. In principle, any communication waveform
can be utilized for mono-static sensing, as it is fully known
to the transmitter. Nevertheless, the randomness brought by
the communication data may considerably degrade the sensing
performance.
As a representative CCD strategy, the use of OFDM wave-
form for radar sensing has recently received growing attention,
thanks to its compatibility with the state-of-the-art 4G and 5G
standards [8]. A baseband OFDM communication signal, in
its simplest form, is analytically given by
sOFDM (t) =
Ns∑
m=1
Nc∑
n=1
dm,nej2πfnt rect
(t− (m− 1)TOFDM
TOFDM
)
,
(46)
where Ns and Nc are the number of OFDM symbols and
subcarriers within a signal frame,dm,n is them-th data symbol
at the n-th subcarrier, fn = (n− 1) ∆f is the n-th subcarrier
frequency with subcarrier interval ∆f, TOFDM = Ts +Tg is
the overall OFDM symbol duration, with Ts andTg being the
duration of an elementary symbol and a cyclic preﬁx (CP),
and rect (t/T ) depicts a rectangular window with duration T .
At the ISAC BS, (46) is transmitted to sense a point target
with Doppler fD and delay τ. The noiseless echo signal

19
Data
Mod
 IFFT
FFT
S
P
S
P
P
S
S
P
D/A
A/D
LO
Data 
Payload
Radar 
Sensing
Data
Demod
( )OFDMst
Comms Receiver 
and Radar Target
( )Ryt
Fig. 10. Signal processing ﬂow chart for OFDM based ISAC signaling.
received at the BS is then
yR (t) =
Ns∑
m=1
ej2πfDt·
Nc∑
n=1
αm,n
(
dm,ne−j2πfnτ)ej2πfnt rect(t− (m− 1)Ts−τTs ),
(47)
where αm,n is the channel coefﬁcient at the mth OFDM
symbol and the nth subcarrier. By assuming that the guard
intervalTg is properly chosen, the time shift on the rectangular
function can be neglected. Through sampling at each OFDM
symbol, and performing block-wise FFT, the received discrete
signal can be arranged into a matrix, with the (m,n )th entry
being
ym,n =αm,ndm,ne−j2π(n−1)∆fτej2πfD(m−1)TOFDM, (48)
where the noise is again omitted for simplicity. We ﬁrst
observe that, the random communication data dm,n can be
mitigated by simple element-wise division, which yields
˜ym,n = ym,ndm,n =αm,ne−j2π(n−1)∆fτej2πfD(m−1)TOFDM.
(49)
Furthermore, (49) can be recast into a matrix form as
˜Y = A⊙ vτvHf , (50)
where
(
˜Y
)
m,n
= ˜ym,n, (A)m,n =αm,n, and
vτ =
[
1,e−j2π∆fτ,...,e−j2π(Nc−1)∆fτ
]T
,
vf =
[
1,e−j2πfDTOFDM,...,e−j2πfD(Ns−1)TOFDM
]T
.
(51)
To sense the target, we compute the FFT on each column of ˜Y
to obtain the Doppler estimate, and then compute the IFFT on
each row to obtain the delay estimate. This can be represented
as [8]
¯Y = FNs ˜YFHNc, (52)
where FN is the N-dimensional DFT matrix. The resultant
¯Y forms a 2-dimensional delay-Doppler proﬁle, where a
peak is detected at the corresponding delay-Doppler grid that
contains the target. Unlike conventional chirp signals, delay
and Doppler processing are decoupled in OFDM waveforms,
which is favorable for radar applications.
Although the above OFDM-based ISAC waveform is able
to fully guarantee the communication performance, its sensing
performance is rather restricted, since many desired properties
for sensing are not addressed. To begin with, constant envelope
is typically needed for radar to transmit at the maximum avail-
able power budget without signal distortion, such that the SNR
of the received echo signal is maximized. Second, the reliance
to clutter interference, a key requirement in radar sensing, is
rarely considered in CCD schemes. Last but not least, the
sensing waveform should possess good correlation properties,
so that the temporal/spectral/angular sidelobes are reduced to
the lowest level to avoid false target detection. In order to
improve the sensing performance, the CCD ISAC waveform
needs to be well-shaped subject to the above sensing-speciﬁc
constraints.
3) Joint Design: As mentioned above, while SCD and
CCD schemes realize ISAC to a certain extent, they fail to
formulate a scalable tradeoff between S&C. That is to say,
SCD and CCD are two extreme cases in ISAC waveform
design, where the communication/sensing functionality is im-
plemented in a rather restricted manner provided that the
sensing/communication performance is fully guaranteed. To
address this issue, joint design is regarded as a promising
methodology. Unlike its SCD and CCD counterparts, JD aims
at conceiving an ISAC waveform from the ground-up, instead
of relying on existing sensing and communication waveforms
[10], [60], [114], [117], [136]. This offers extra DoFs and
ﬂexibility, and thereby improves the S&C performance simul-
taneously. In what follows, we overview a state-of-the-art JD
scheme in detail [60].
We consider an Nt-antenna ISAC BS, serving K single-
antenna users in an MU-MISO downlink while sensing targets.
Suppose that an ISAC signal matrix X∈ CNt×L is transmit-
ted, with L being the length of the radar pulse/communication
block. The received signal at the users can be modeled as [60],
[140]
YC = HX + Z = SC + (HX− SC)
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
MUI
+Z, (53)
where H∈ CK×N is the MU-MISO communication channel
matrix, and ZC ∈ CK×L is again an AWGN noise matrix
with variance σ2C. Finally, SC ∈ CK×L contains communi-
cation data streams intended for K users, with each entry
being a communication symbol drawn from some pre-deﬁned
constellations, e.g., QPSK or 16-QAM. Here, (HX− SC) is
the multi-user interference (MUI). By zero-forcing the MUI,
the channel H vanishes, and the MU-MISO channel becomes
a standard AWGN channel.
The reduction of the MUI term leads to higher communi-
cation sum-rate [140], which motivates the use of MUI as a
cost function for communications. In addition to bearing the
information matrix SC, the ISAC signal X should possess
a number of aforementioned features that are favorable for
sensing, which would be quite challenging to be implemented
simultaneously in a single waveform. Therefore, an alterna-
tive option is to approximate a well-designed pure sensing
waveform X0, e.g., orthogonal chirp waveform, which is
known to have superior sensing performance. With the above

20
2.6 2.7 2.8 2.9 3 3.1 3.2 3.3 3.4 3.5
Average achievable rate (bps/Hz/user)
0.75
0.8
0.85
0.9
0.95
1
PD
K = 4, Total
K = 4, perAnt
K = 6, Total
K = 6, perAnt
K = 8, Total
K = 8, perAnt
Scalable
Tradeoff
Sensing-
Optimal
Comms-
Optimal
Fig. 11. Performance tradeoff between S&C by the joint design, Nt = 16
radar SNR = -6 dB, PF A = 10 −7.
consideration, we formulate the following ISAC waveform
design problem.
min
X
ρ‖HX− SC‖2F + (1−ρ)‖X− X0‖2F
s.t. fn (X) ⊴Cn,∀n,
(54)
where we use a weighting factor ρ ∈ [0, 1] to control the
weight assigned to S&C functionalities, i.e., ρ and 1− ρ
represent the priority/preference for the communication and
sensing performance in the ISAC system, respectively. In
addition to minimizing the weighted cost function, N wave-
form shaping constraints are imposed on X, which may
include overall power budget constraint, per-antenna power
budget constraint, constant-modulus (CM) constraint (in order
to enable the full-power and distortionless signal emission
for radar sensing), and range/Doppler/angle sidelobe control
constaints. For instance, by imposing a total transmit power
constraint PT , (54) can be reformulated into
min
X
ρ‖HX− SC‖2F + (1−ρ)‖X− X0‖2F
s.t. ‖X‖2F =LPT. (55)
Note that if ρ = 1, communication is given the full priority,
and solving problem (55) yields a zero-forcing (ZF) precoded
signal with respect to the channel H. On the contrary, ifρ = 1,
sensing is given the full priority, and the optimal solution is
exactly X = X0, provided that X0 is also constrained by the
same power budgetPT . Whenρ varies from 0 to 1, a favorable
S&C performance tradeoff can be obtained via solving (55).
We show a numerical example of the joint design in (54)
for Nt = 16,K = 4, 6, 8, by using orthogonal waveform X0
as a benchmark, which is known to have superior sensing
performance for MIMO radar. We consider a scenario where
a point-like target located at the angle of 36◦ is to be sensed
via the constant false-alarm rate (CFAR) detection approach,
with the false-alarm probability and receive SNR ﬁxed at 10−7
and−6 dB, respectively. The tradeoff between the detection
probablity PD and the avaerage achievable rate per user is
investigated in Fig. 11 by varying ρ from 0 to 1, under both
total and per-antenna (perAnt) power constraints. Accordingly,
the ISAC performance varies from sensing-optimal smoothly
to communication-optimal, which suggests that SCD and CCD
performance are two end-points on the JD tradeoff curve.
Another tradeoff can be observed from Fig. 11 is that, with
the reduced number of communcation users, the detection
probability is on the rise. When K = 4, the achievable rate is
increased without sacriﬁcing too much sensing performance.
Despite the higher computational complexity of the JD
scheme, it often outperforms conventional schemes in many
aspects, as elaborated below.
1) While most SCD waveforms are based on inter-pulse
modulation (slow-time coding), the JD waveform in
(54) modulates communication data through an inner-
pulse manner (fast-time coding), where each fast-time
snapshot represents a communication symbol. This sig-
niﬁcantly improves the data rate.
2) While the classical sidelobe control scheme in (36)-(41)
serves communication users in LoS channels only, the
JD waveform in (54) is not conditional on any speciﬁc
channel. In fact, any MIMO channel matrix H can be
inserted into (54) for designing the JD waveform.
3) Problem (54) takes into account sensing-speciﬁc con-
straints, such as constant modulus and waveform simi-
larity, which improves the sensing quality compared to
CCD schemes, such as OFDM-based designs.
We summarize the pros and cons for different ISAC wave-
form designs in TABLE. III.
V. R ECEIVE SIGNAL PROCESSING
The requirement for simultaneously accomplishing S&C
tasks poses unique challenges in receive signal processing.
In general, an ISAC receiver should be able to decode useful
information from the communication signal, and at the same
time detect/estimate targets from the echoes. In the event that
the two signals do not overlap, conventional signal processing
can be applied unalteredly, as both S&C are interference
free. However, mutual interference occurs if the two signals
are fully/partially overlapped on both temporal and frequency
domains, which is the price to pay for acquiring the integration
gain.
We demonstrate a generic ISAC receiver structure in Fig.
12, where the mixed communication and echo signals are
received from the same antenna array, and are ampliﬁed,
down-converted, and sampled from the RF chain. The sampled
signals are then fed into communication and sensing proces-
sors for the purpose of information decoding and target de-
tection/estimation/recognition, where the cooperation between
S&C is required to facilitate mutual interference cancellation.
Within this framework, below we overview state-of-the-art
ISAC receive signal processing techniques.
A. Fundamental Insights from a Toy Model
Let us ﬁrst examine a toy model in an AWGN channel,
which was considered in [141], [142], where a transmitter
wishes to communicate with a receiver in the presence of
strong radar interference. The radar signal is modeled as a

21
LNAA/D Down-Conversion
Comm Signal 
Processing
Sensing Signal 
Processing
S&C 
Coordination
Target Return + 
Comm Signals
Data 
Demod
Target 
Detection/
Estimation/
Recognition
Fig. 12. General structure of an ISAC receiver.
short-duration pulse with large amplitude, while the com-
munication signal is assumed to be of small bandwidth and
considerably lower power with 100% duty cycle. From the
communication point of view, the radar interference can be
approximated as a constant modulus signal, whose amplitude
is accurately estimated, but the phase shift is randomly ﬂuc-
tuated and thus is difﬁcult to track. In this case, the received
signal at the communication receiver is given as [141]
y =
√
PCsC
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
Comms Signal
+
√
PRejθ
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
Radar Interference
+ z/dcurly
Noise
, (56)
wherePC andPR represent the received power of the commu-
nication and radar signals, respectively, which are assumed to
be known to the receiver. Moreover, sC is a communication
symbol to be detected, which is drawn from a constellation
S = {s1,s 2,...,s M}, and θ is an unknown phase shift
randomly distributed over [0, 2π]. Finally, z is the Gaussian
noise with zero mean and unit variance. Two fundamental
problems arise from the model in (56). The ﬁrst one is what
the optimal decision region is for a given constellation in
accordance with the maximum likelihood (ML) criterion. The
second one is how to design a self-adaptive constellation that
optimizes communication metrics, e.g., the communication
rate and the SER.
To answer the ﬁrst question, one may form an ML decoder
by averaging over all the possible phases θ, which yields
ˆmopt =
arg min
m∈[1:M]
(⏐⏐⏐y−√PCsm⏐⏐⏐2− lnI0(2√PR⏐⏐⏐y−√PCsm⏐⏐⏐)),
(57)
where I0 (·) is the zero-order modiﬁed Bessel function of the
ﬁrst kind. For low interference-to-noise (INR) regime, i.e.,
αR
√PR ≪ αC√PC, the ML decoder reduces to a Treat-
Interference-as-Noise (TIN) decoder, i.e., the radar interfer-
ence is regarded as noise. This can be approximated by
ˆmopt = arg min
m∈[1:M]
⏐⏐⏐y−√PCsm⏐⏐⏐2. (58)
On the contrary, when αC
√PC≪ αR√PR, i.e., the INR is
high, the ML decoder can be approximately expressed as
ˆmopt = arg min
m∈[1:M]
(⏐⏐⏐y−√PCsm⏐⏐⏐−√PR)2, (59)
which is known as Interference-Cancellation (IC) receiver,
where the radar interference is pre-canceled before communi-
cation symbols are decoded. By taking low-, mid-, and high-
INR regimes into consideration, the authors analyze in detail
the SER for commonly-employed constellations, including
PAM, QAM, and PSK.
Based on the above analysis, one may answer the second
question by employing optimization techniques to design
interference-aware constellations. The ﬁrst design, which op-
timizes the communication rate, i.e., the cardinality of the
constellation, can be formulated as [141]
max
S
M
s.t. S ={s1,s 2,...,s M},
Pe (S)≤ε,
1
M
∑M
m=1
|sm|2≤ 1, sm∈ C,
(60)
where Pe (S) in the second constraint is the SER of the
constellation, which is required to be smaller than a given
thresholdε, and the third constraint is imposed as a normalized
power constraint. Accordingly, the SER minimization problem
can be formulated into [141]
min
S
Pe (S)
s.t.S ={s1,s 2,...,s M},
1
M
∑M
m=1
|sm|2≤ 1, sm∈ C.
(61)
The above two optimization problems are non-convex in
general, which can be sub-optimally solved via the MATLAB
Global Optimization Toolbox using the Global Search (GS)
method. The numerical results show that for both design
criteria, the optimal constellation is with concentric hexagon
shape for low-INR regime, and is with unequally spaced PAM
shape for high-INR counterpart.
The study of the toy model (56) shows that, in the regime
of mid/high radar INR, one may consider to recover/estimate
the radar interference ﬁrst, and pre-cancel it from the mixed
reception y. More importantly, a good ISAC receiver design
should exploit the structural information of the S&C signals .
For instance, the constant modulus of the radar signal is
considered when developing the optimal decoder. In the next
subsection, we will show that the hidden sparsity of S&C
signals can also be employed for receiver design.
B. ISAC Receiver Design based on Sparsity
Inline with the above spirit, a practical receiver design has
been proposed in [143], where an ISAC receiver receives
the communication signals from a single user, as well as
interference from J radar/sensing systems. The aim is to
correctly demodulate the communication data while recovering
the radar signals. The generic form of the received coded
signal can be given as
y (t) =yC (t) +yR (t) +z (t) =
N−1∑
n=0
x (n)ε (t−nT )
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
Comms Signal
+
J∑
j=1
N−1∑
n=0
cjgj (n)ε (t−nT−τj)
/dcurlyleft/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlymid/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/udcurlymod/dcurlyright
Radar Interference
+z (t)
/dcurly.alt3
Noise
(62)
where yC (t), yR (t), and z (t) stand for the communication
signal, coded radar signal, and noise in the time domain, ε (t)

22
is a basic pulse satisfying the Nyquist criterion with respect to
its lengthT ,N is the code length for both communication and
radar,τj andcj denote the delay and complex channel coefﬁ-
cient between the jth radar interference and the communica-
tion receiver,gj (n) is thenth code for thejth radar signal, and
ﬁnally,x (n) is the nth communication signal sample. It is as-
sumed that the radar code gj = [gj (1),gj (2),...,g j (N)]T
lies in a low-dimensional subspace, spanned by the columns
of a known matrix D, such that gj = Dhj. This can be
interpreted as an implementation scheme of radar waveform
diversity, where radar copes with different situations, e.g.,
interference, clutter, spectrum sharing, by varying the transmit
waveforms via selecting from a given waveform dictionary.
Moreover, we have x = [ x (0),x (1),...,x (N− 1)]T =
HCb, where HC and b ∈ Bare communication channel
and data symbols, respectively, withB being a communication
alphabet. After standard signal processing, the received signal
can be arranged into a discrete form as
r = HCb + HRα + z, (63)
where HR is a matrix function of a over-complete dictio-
nary/grid formed by time delays ˜τ1, ˜τ2,..., ˜τ ˜J, ˜J ≥ N and
the known matrix D, and α =
[
c1hT1,c 2hT2,...,c ˜JhT˜J
]T
.
The sparsity-based receiver design is implemented in an iter-
ative manner. To proceed, an initial symbol demodulation is
operated over r, yielding an incorrectly detected symbol vector
ˆb(0) due to the strong radar interference. One may recover
the communication signal by HC ˆb(0), and substract it from
r, leading to
r(1) = HC
(
b−ˆb(0)
)
+ HRα + z
≜ HCv(1) + HRα + z, (64)
where v(1) = b−ˆb(0) is the demodulation error.
Then, in each iteration we reconstruct v for communication
and α for radar simultaneously (e.g., from r(1) in (64) in
the ﬁrst iteration), and reﬁne the demodulation process. Given
J≪ N ≤ ˜J, α should be a sparse vector. Furthermore, to
minimize the SER, we need v to be as sparse as possible,
i.e., the number of zero elements in v should be maximized.
With these two observations in mind, an iterative on-grid
compressed sensing (CS) problem is formulated. For the lth
iteration, we have
(
ˆα(l), ˆ v(l)
)
= arg min
α,v(l)
1
2
‖‖‖r(l)− HCv(l)− HRα‖‖‖22
+λ
‖‖‖v(l)‖‖‖
1
+ γ‖α‖1,
(65)
where l1 norm penalties are imposed to replace the non-
convexl0 norm. Moreover, λ and γ are weights determining
the sparsity of the reconstruction. After solving the convex
problem (65), we obtain the demodulation error ˆ v(l). By
combining ˆ v(l) and ˆb(l−1), the data symbols can be re-
demodulated as
ˆb(l) = arg min
b∈B
‖‖‖b−ˆb(l−1)− v(l)‖‖‖2
2
, (66)
and we update v(l+1) and α as
v(l+1) = r(l)− HCˆb(l), α = ˆα(l). (67)
The algorithm terminates if ˆb(l) = ˆb(l−1), or if the maximum
iteration number is reached. To further boost the performance,
off-grid CS algorithm can also be developed, where the atomic
norm is used instead of the l1 norm [143].
VI. C OMMUNICATION -A SSISTED SENSING : P ERCEPTIVE
NETWORK
As discussed in Sec. I and II, the sensing functionality is
expected to be integrated into the future wireless network
to form a perceptive network [50], [144], [145], such that
it becomes a native capability that provides various sensing
services to users, e.g., localization, recognition, and imaging.
In this sense, communication can assist sensing with the
following two levels of design methodologies:
• Frame-Level ISAC: Sensing supported by default com-
munication frame structures and protocols, such as Wi-Fi
7 and 5G NR 6.
• Network-Level ISAC: Distributed/Networked sensing
supported by state-of-the-art wireless network architec-
tures, such as Cloud-RAN (C-RAN).
Below we overview the basic framework and technical issues
raised in the perceptive network. Without loss of generality,
our discussion is based on a general cellular network, namely a
perceptive mobile network (PMN). We refer readers to [2] for
a detailed examination on other types of perceptive networks,
such as Wi-Fi and IoT.
A. General Framework
Before presenting the basic framework, we ﬁrst investigate
and classify the objects to be sensed, i.e., targets, in a PMN.
A target to be sensed can either be a communication or non-
communication object. The ﬁrst case often emerges in high-
mobility scenarios, where the BS/UE wishes to communicate
with a mobile terminal while tracking its movement, which
is quite typical in V2X or UA V networks. This will be
discussed in Sec. VII in detail, where we show that the V2X
beamforming performance can be signiﬁcantly improved with
the aid of downlink active sensing. In the second case, the
target usually belongs to the surronding environment, which
needs to be localized, recognized or even imaged for further
applications, e.g., high-precision mapping. In this subsection,
we will not differentiate between these two types of targets,
but will focus on the technical challenges on realizing sensing
using 5G-and-beyond communication infrastructures.
In a PMN, sensing can be performed in ways that are similar
to communication links. That is, it can be implemented by
using downlink or uplink signals, which are transmitted from
a BS or a UE, respectively. This, accordingly, deﬁnes downlink
and uplink sensing operations. Furthermore, one may deﬁne
6We note that in the frame-level ISAC, sensing as a basic functionality is
implemented by standardized communication frame structures and waveforms,
which can be recognized as a communication-assisted sensing technique,
despite that the coordination gain is not as explicit as in the network-level
ISAC.

23
240
subcarriers
0
47
56
182
192
239
4 symbols
PBCH
PSS
PBCH-DMRS
SSS
0 1 2 3 4 5 6 7 8 9 10 11 12 130 1 2 3 4 5 6 7 8 9 10 11 12 13
0 1 2 3 4 5 6 7 8 9 10 11 12 13 0 1 2 3 4 5 6 7 8 9 10 11 12 130 1 2 3 4 5 6 7 8 9 10 11 12 13
0 1 2 3 4 5 6 7 8 9 10 11 12 13
1 slot = 14 symbols 
Fig. 13. Structure of 2 slots within a subframe of 5G NR, µ = 4.
mono-static, bi-static, and distributed/networked sensing oper-
ation modes, which are determined by the locations of the
transmitter(s) and receiver(s). For clarity, we split sensing
operations in a PMN into following categories [144]:
• Downlink Mono-static Sensing: Downlink signals trans-
mitted from the BS to the UE are exploited for sensing,
while the BS receives the echo signals reﬂected from
targets by its own receiver. In this case, BS acts as
a mono-static radar, for which the transmitter and the
receiver are collocated.
• Uplink Mono-static Sensing: Uplink signals transmitted
from the UE to the BS are exploited for sensing, and the
UE receives the signals reﬂected from targets by itself.
• Downlink Bi-static Sensing: Downlink signals are ex-
ploited for sensing, which hits the target(s) and is re-
ﬂected to another BS. This is deemed to be similar to a
bi-static radar, where transmitter and receiver are well-
separated.
• Uplink Bi-static Sensing: Uplink signals transmitted
from the UE to the BS are exploited for sensing, and the
BS receives the uplink signals scattered from the targets.
This is again a bi-static radar architecture.
• Distributed/Networked Sensing: Sensing signals can
be emitted from multiple transmitters, and are received
by multiple receivers after hitting the target. Both BSs
and UEs can act as transmitters and receivers. This
corresponds to a multi-static radar system, where a certain
level of cooperation is required between transceivers.
Note that uplink mono-static sensing is rarely considered, due
to the fact that UEs with small size normally only have limited
sensing capability when acting as sensing receiver, which is
the general case for small-size UEs. Nevertheless, we note
that for speciﬁc UEs with high computational capacity, e.g.,
vehicles, uplink mono-static sensing could also be possible.
B. Using 5G-and-Beyond Waveform for Sensing
In this subsection, we provide our insights into the feasi-
bility of using 5G-and-beyond waveform for sensing, and the
challenges and opportunities therein.
1) Feasibility: For any sensing operation mode in ISAC
systems, a known reference signal is indispensible, either
for matched-ﬁltering the received echo signal and thereby to
extract the target information, or simply for mitigating the
impact of the random communication data. In both 4G LTE
and 5G NR, OFDM is the default waveform format, which can
be exploited for sensing in the PMN following the general
signal processing pipeline overviewed in Sec. IV-B. Recall
that in (49), the dependence of the data is removed from the
echo signal via element-wise division. This requires that the
communication signal sent from the transmitter is known to the
receiver before the target is sensed, which motivates examining
the signal resources that are available for sensing within a
communication frame.
Let us investigate a standard frame structure for NR, which
is based on 3GPP Technical Speciﬁcation 38.211, Release
15 [146]. A 5G NR frame lasts for 10 ms, consisting of
10 subframes, each with a duration of 1 ms. Each subframe
consists of 2µ time slots, with µ being a numerology ranging
from 0 to 5, referring to a subcarrier spacing of 2µ· 15 kHz.
Each slot occupies 14 or 12 OFDM symbols, determined by
whether normal or extended CP is used.
Fig. 13 shows the structure of 2 time slots for µ = 4, i.e.,
28 OFDM symbols. It can be seen that in addition to the
data payload, there are 4 signal synchronization blocks (SSBs),
each of which occupies 4 OFDM symbols. The components
of the SSB include a Primary Synchronization Signal (PSS), a
Secondary Synchronization Signal (SSS), Physical Broadcast
Channel (PBCH), and its Demodulation Reference Signal
(PBCH-DMRS). SSB is broadcasted periodically for channel
estimation and synchronization. Under certain circumstances,
multiple SSBs can be transmitted within a localized burst to

24
support possible beam sweeping operations. Signals accom-
modated in an SSB are known to both BS and UE, and can
be easily exploited for sensing. In particular, synchronization
signals, i.e., PSS and SSS, are typically with ﬁxed structures,
while the PBCH and its DMRS are more ﬂexible and could
be optimized for both S&C, through speciﬁcally tailored
precoding and scheduling schemes. Further to that, the PRS
deﬁned in Release 16 of NR can also be readily utilized
for localization. These designs fall into the scope of time-
frequency division ISAC discussed in Sec. IV-A, where only
part of a frame structure is exploited for sensing. In line
with the design philosophy of the fully uniﬁed waveform, one
may further employ the data payload available in the frame
for sensing, which would signiﬁcantly improve the matched
ﬁltering gain and the sensing SNR.
2) Challenges and Opportunities: As per the analysis
above, we next discuss the crictical challenges raised in
waveform-level ISAC design using 5G NR, as well as their
potential solutions.
Limited Bandwidth for High-Precision Sensing: 3GPP
has deﬁned 2 frequency range (FR) types for NR. FR1 (sub-
6 GHz) is from 450 MHz to 6 GHz, and FR2 (mmWave) is
from 24.25 GHz to 52.6 GHz. The channel bandwidth is up
to 100 MHz in FR1, and 400 MHz in FR 2, which correspond
to range resolutions of 1.5 m and 0.375 m, respectively, as
per (20). While these resolutions may be sufﬁcient for basic
sensing services, they are unable to fulﬁll the demand of high-
precision localization applications, e.g., autonomous vehicles
that require sensing resolution at the level of 0.1 m. One
possible way to improve the range resolution is to leverage the
carrier aggregation (CA) technique, which is able to boost the
data rate by assigning multiple frequency blocks to the same
user. In this spirit, one may also assign multiple frequency
blocks to sense the same target. For example, if 16 carriers are
aggregated within the sub-6 GHz band, the overall bandwidth
can be up to 1.6 GHz, leading to a range resolution of 0.094 m.
However, if the aggregated bandwidths are discontinued, high
range sidelobes may occur, which possibly results in a high
false-alarm probability. To that end, proper measures should
be taken to reduce the sidelobes.
Self-Interference in Mono-static Sensing: For mono-static
sensing operation, while both the SSB and the data payload
are known and can thus be used for target probing, self-
interference (SI) is a problem that can not be bypassed. Let us
take the the case with µ = 4 frames as an example, for which
the subcarrier spacing is 240 kHz, and the corresponding
OFDM symbol plus CP lasts for 4.46 µs. Such a duration
translates to a target at a distance of 670 m. That is to say,
if a target is within the range of 670 m, its echo signal will
be reﬂected back to the BS within a duration of an OFDM
symbol, while the BS is still transmitting. The leaked signal
from the transmitter to the receiver results in strong SI, which
saturates the receiver’s ampliﬁers and masks the target return.
For a moving target, the SI could be less harmful as long as the
BS can distinguish it on the Doppler spectrum. Nevertheless,
for static targets, this leads to “black zone” at the level of 100-
1000 m, even if only a single OFDM symbol is employed,
not to mention the use of both the SSB and the data payload,
which generates even larger black zone. In fact, large signal
dynamic range is required to resolve both types of targets,
which practical analog-to-digital converters (ADCs) are unable
to handle. To address this issue, full-duplex and SI cancellation
techniques are necessary [147], or at least a certain degree of
isolation between transmit and receive antennas is required.
Fortunately, recent research has reported that by leveraging
both RF and digital cancelers, a 100 dB SI suppresion can be
reached for OFDM signaling, which is sufﬁcient for the BS
to identify a static drone at a distance of 40 m [148].
Unknown Data Payload in Bi-static Sensing: For bi-static
sensing where the transmitter and receiver are separated, the
SI is no longer an issue, and known SSB signals can be
readily leveraged as sensing waveforms. Nevertheless, the data
payload is unable to be straightforwardly utilized, as it may be
unknown to the receiver side in the case that there are no direct
channels/links in between. To tackle this problem, the receiver
may ﬁrst estimate the channel matrix by using the PBCH
available in the SSB, and demodulate the data symbols using
the estimated channel. By doing so, the demodulated symbols
in conjunction with the SSB can be used for estimating the
target parameters of interest.
For clarity, let us revisit the OFDM model present in (47) by
taking into account the spatial channel. Through transmitting
a symbol vector xm,n∈ CNt×1 at the n-th subcarrier and the
m-th OFDM symbol to sense L targets, which correspond to
L propagation paths from the transmitter to the receiver, the
receivedNr-dimensional signal vector at the same subcarrier
and OFDM symbol can be expressed as
ym,n =
L∑
l=1
αle−j2π(n−1)∆fτ lej2πfD,l(m−1)TOFDM·
b (φl) aH (θl) xm,n + zm,n,
(68)
where αl,τl,fD,l,φl and θl represent the amplitude, delay,
Doppler, AoA and AoD of the l-th target/path, respectively,
and zm,n is a Gaussian noise vector. By letting
B (Φ) = [ b (φ1),..., b (φL)], A (Θ) = [a (θ1),..., a (θL)],
Cn = diag
{[
α1e−j2π(n−1)∆fτ 1,...,α Le−j2π(n−1)∆fτ L
]}
,
Dm = diag
{[
ej2πfD,1(m−1)TOFDM,...,e j2πfD,L(m−1)TOFDM
]}
,
(69)
the relation (68) can be written in compact form as
ym,n = B (Φ) CnDmAH (Θ) xm,n + zm,n
≜ Hm,nxm,n + zm,n.
(70)
For communication purposes, the ISAC channel matrix
Hm,n can be estimated via the known pilots in the NR
frame, without the need of knowing its inner structure. On
the other hand, for sensing purposes, the target parameters
αl,τl,fD,l,φl, and θl need to be estimated. To proceed,
one can either extract these parameters from the estimated
channel ˆHm,n directly, or ﬁrst demodulate the data symbols
and reconstruct xm,n by using ˆHm,n, and then estimate the
target parameters by further exploiting the reconstruced signal
ˆ xm,n as a reference signal [144]. With the latter design, not
only the target can be more accurately estimated, but also the

25
Target 
Localization 
and 
Recognition
Comms 
Processing
RRH 1
Downlink momo-static sensing
Clutter
RRH 2
RRH 3
C-RAN Enabled 
Networked Sensing
Fronthaul
Fig. 14. C-RAN architecture for networked sensing.
communication channel estimate can be further reﬁned, which
is an example for attaining the coordination gain.
C. Using 5G-and-Beyond Network Architecture for Sensing
In this subsection, we show how 5G-and-beyond network
architectures can be utilized for sensing.
1) Feasibility: Over the past decades, networked sensing
has been well-studied for a variety of sensing systems, in-
cluding wireless sensor network (WSN), multi-static radar,
and distributed MIMO radar (a.k.a. MIMO radar with widely
separated antennas) [21], [149], [150]. Among these sensing
systems, a common structure is that the sensing operation is
performed by multiple sensing nodes, and the sensed results
are collected by a centralized unit for further processing, e.g.,
data fusion. By doing so, better sensing performance can be
achieved over single-node sensing operation.
Depending on the processing pipeline at the centralized unit,
networked sensing can be generally split into the following two
categories:
• Information-Level Fusion: Each sensing node performs
individual sensing by its own observations. The sensed
parameters are collected and fused at the centralized
unit. Conventional WSN that localizes an agent (target)
using measurements of received signal strength (RSS),
ToA, AoA, and time difference of arrival (TDoA) from
anchors (sensing nodes), is a representative system using
information-level fusion [151], [152].
• Signal-Level Fusion: Each sensing node observes sig-
nals reﬂected/scattered from the target, which could be
transmitted from other nodes. The signals, instead of
the sensed parameters, are collected and fused at the
centralized unit, where an important application of such
techniques is distributed MIMO radar [21], [153]. Signal-
level fusion is known to be superior to information-level
fusion, as the latter may discard important information
relevant for sensing by individually processing the sens-
ing signals at each node [149].
While it is plausible that the signal-level fusion provides
performance gains over its information-level counterpart, it
suffers from much higher computational and signaling over-
heads, as well as hardware costs. This is particularly pro-
nounced for distributed MIMO radar, in which case a huge
amount of sensed data needs to be communicated to a fusion
center with strong computational power.
Fortunately, the C-RAN architecture designed for 5G-and-
beyond communications provides a ﬂexible and reconﬁgurable
framework that enables a variety of sensing modes discussed
above [154], [155]. As shown in Fig. 14, a typical C-RAN
consists of a pool of base band units (BBUs), a large number
of remote radio heads (RRHs), and a fronthaul network that
connects RRHs to BBUs. The BBU pool is deployed at a
centralized site, with software-deﬁned BBUs that process the
baseband signals and coordinate the wireless resource alloca-
tion. Eventually, the BBU pool can act as a centralized signal
processing unit for networked sensing. RRUs are in charge
of RF ampliﬁcation, up/down-coversion, ﬁltering, analog-to-
digital/digital-to-analog conversion, and interface adaption,
which can be leveraged as radar sensors supported by the
NR waveform and relevant ISAC signaling techniques. Finally,
the fronthaul link is typically realized by optical ﬁber com-
munication technologies with high capacity and low latency,
which can be exploited to transmit both S&C data with high
reliability [156].
2) Challenges and Opportunities: We end this subsection
by identifying the unique challenges and opportunities im-
posed in C-RAN based ISAC, from a networked sensing
perspective.
Is Inter-Cell Interference a Friend or Foe? C-RAN is
able to effectively mitigate the inter-RRH interference by
using interference management approaches, e.g., coordinated
multi-point (CoMP) or soft fractional frequency reuse (S-FFR)
techniques [154], [157]. In most cases, inter-cell interference
in communication networks is recognized as a harmful factor
that needs to be reduced. For perceptive networks, however,
inter-RRH interference may contain useful information with
respect to targets of interest, which needs to be exploited to
enhance the sensing performance, rather than being cancelled.
In addition to receiving the echo signal originating from the
mono-static sensing operation, each RRH may also receive the
target return generated from ISAC signals transmitted by other
RRHs or UEs.
Assuming that there are Q RRHs connected to a BBU pool,
and recalling (70), the sensing signals received at theqth RRH,
themth OFDM symbol, and thenth subcarrier can be modeled
as [50]
yq,m,n = Hq,m,nxq,m,n+
Q∑
q′=1
q′⁄=q
Hq′,m,nxq′,m,n+zq,m,n, (71)
where Hq,m,n represents the ISAC channel matrix for mono-
static sensing, Hq′,m,n is the ISAC channel matrix for bi-static
sensing between the q′th and the qth RRHs, and xq,m,n and

26
TABLE IV
FEASIBLE TECHNIQUES AND CHALLENGES IN PERCEPTIVE MOBILE NETWORK
Sensing Operation Modes Feasible Techniques Challenges
Downlink Mono-static
(RRH mono-static sensing)
Using both SSB and data for sensing • SI cancellation
• transmitter/receiver isolation
Downlink Bi-static
(RRH-RRH bi-static sensing)
Using both SSB and data for sensing • Interference management
Uplink Bi-static
(UE-RRH bi-static sensing)
Using SSB only for sensing • Low matched-ﬁltering gain
• Synchronization issue
Using both SSB and data for sensing • Unknown data payload
• Synchronization issue
Networked Sensing Using C-RAN architecture for sensing
• Interference management
• Scheduling with target return
• Network synchronization issue
xq′,m,n stand for the OFDM ISAC signals transmitted from
the q′th and the qth RRHs, respectively, and ﬁnally zq,m,n is
the noise. While the qth RRH may be interested in recovering
the target information from the mono-static channel matrix
Hq,m,n, bi-static channel matrices Hq′,m,n,∀q′⁄=q may also
contain useful information with respect to the same target,
which need to be estimated and recovered. By doing so, the
ﬂuctuation in the radar cross section (RCS) of the target can be
easily compensated, since the same target may be sensed from
different looking directions [21]. This provides coordination
gains to the sensing performance, which is similar to the
diversity gain in MIMO communications.
Target Return as an Outlier in C-RAN Scheduling: On
top of the interference management, sensing operations also
impose challenges in resource scheduling in a PMN. In the
control plane of the C-RAN system, the resource management
module is composed of three functions: the context-aware
function (CAFun), the resource scheduling function (RSFun),
and the reconﬁguration function (RFun). The CAFun collects
context information, e.g., Channel State Information (CSI),
Quality-of-Service (QoS) requirements, battery consumption,
from the network and forwards it to the RSFun. The RS-
Fun then generates the scheduling strategy given the con-
text information, and communicates it to the RFun, which
executes the scheduling decision for RANs and UEs [156].
In a communication-only C-RAN, the above framework is
sufﬁcient to coordinate the resource allocation for RRHs and
UEs, as they are generally controllable in terms of their
transmission and reception operations. Nevertheless, for PMN,
the target return tends to be an outlier, as it could randomly
appear in time, frequency, and spatial domains. To this end,
novel scheduling approaches are needed to incorporate the
prediction of target echoes into the control plane.
Network Synchronization: A more critical challenge hap-
pens in the sensing scenario between multiple UEs and RRHs.
While the RRHs can be precisely synchronized at a clock
level since they are connected to the centralized BBU via
fronthaul links, UEs and RRHs are unlikely to be clock-
synchronized due to the wireless channel in between. This
leads to severe phase noise in terms of timing offset (TO) and
carrier frequency offset (CFO) between the sensing transmitter
Data Block Data Block Data Block
Data Block Data Block Data Block
Beam 
Training
Uplink 
Feedback
Beam 
Traking
(a) Beam Training 
Scheme
(b) Beam Tracking 
Scheme
(c) Beam Prediction 
using ISAC
Beam 
Prediction
ISAC Block ISAC BlockISAC Block
Fig. 15. Frame structures for feedback based beam training and tracking, and
ISAC based beam prediction.
and receiver, and thereby causes ambiguity in estimating the
delay and Doppler frequency of the target. As an example, a
clock stability of 20 parts-per-million (PPM) may generate a
TO of 20 ns over 1 ms, which leads to ranging error of 6 m
[53]. For typical coherent radar signal processing across pack-
ets/pulses, the sensing performance will be seriously degraded
due to the accumulation of the TO and CFO. To overcome this
challenge, a cross-antenna cross-correlation (CACC) method
was proposed for passive Wi-Fi sensing [158]. A more recent
work addressing this issue for uplink sensing between the
UE and the RRH is [145], where MUSIC-like algorithms are
developed to further enhance the performance of the CACC
method.
In light of the discussion above, we summarize the feasible
techniques and challenges in perceptive mobile networks in
TABLE. IV Among all the sensing operation modes, we
highlight that the downlink bi-static sensing between RRHs
is the most promising technique. Since RRHs are connected
via fronthaul links to the BBU pool, both the SSB and the data
payload transmitted from one RRH can be straightforwardly
known to another RRH through coordination, and can thus
be exploited for sensing. This also removes the necessity of
complicated phase noise compensation and synchronization
algorithms thanks to the high-capacity and low-latency optical
ﬁber fronthaul.

27
VII. S ENSING -A SSISTED COMMUNICATION
Despite being rarely discussed in an explicit manner, com-
munication systems are often assisted by sensing in a general
setting. An example is the estimation of CSI before data
transmission by sending pilots from the transmitter to the
receiver. Another example for sensing-assisted communication
is spectrum sensing in the context of cognitive radio, where the
secondary user detects the precense of the primary user over
a frequency band of interest, and then utilizes the spectrum
to transmit information if the band is not occupied [159]–
[161]. While sensing techniques have been indeed employed to
assist communication in the aforementioned applications, we
underline that conventional sensing-assisted communication
schemes generally rely on deviced-based and cooperative
sensing, i.e., a sensing device should be attached to the sensed
target, where device-free techniques such as radar sensing
remains widely unexplored for improving the communication
peformance.
In what follows, we take the sensing-assisted V2X network
as an example, to shed light on how sensing, especially
device-free sensing, can be employed to enhance mmWave
communication performance, thus to pursue the coordination
gain. For convenience, we consider mono-static sensing with
the assumption that the SI is fully cancelled.
A. Sensing-Assisted Beam Training
In mmWave communication systems, a communication link
is conﬁgured via classical beam training protocols [162],
[163]. As illustrated in Fig. 15, the transmitter sends pilots
to the receiver over different spatial beams. The receiver
measures the SNR of the received pilots by leveraging different
receive combiners/beamformers, and feeds back to the trans-
mitter the indices of the beam pair that yields the highest SNR.
In this way, the transmit and receive beams are aligned with
each other. Nevertheless, an exhaustive search of the optimal
pair requires a large number of pilots as well as frequent uplink
feedback, which causes large overheads and latency.
To guarantee the communication QoS for latency-critical ap-
plications such as V2X networks, the beam training overhead
needs to be reduced to the minimum, which motivates research
on sensor-aided beam alignment. Indeed, by leveraging the
prior information provided by the sensors, such as GNSS,
radar, lidar, and camera, the search space of the beams can
be narrowed down [164]. It has been shown in [165] that,
for a V2I communication system with 64 ×16 = 1024 beam
pairs, the search space can be reduced to 475 beam pairs
through the use of the positioning information generated by
the GPS, and to 32 beam pairs with the help of the radar-
based positioning, both of which attain the same accuracy
compared to the exhaustive search method. On top of that,
it is also possible to use a hierarchical beam search method in
conjuction with the positioning information from the sensors,
which further reduces overheads.
A more interesting example can be found in [166], where
a MIMO radar mounted on the RSU is exploited to sense
the vehicle. By assuming that the radar and communication
channels share the same dominant paths, the covariance matrix
ISAC RSU
Beam Tracking and 
Prediction at the RSU
Fig. 16. ISAC-enanbled V2I downlink system.
of the communication channel can be estimated by relying
on the echo signals. Based on this information, the RSU
can further design a precoder and send pilots to the vehicle
to facilitate its receive beamforming. In this case, feedback
between the vehicle and the RSU is no longer needed, as the
channel reciprocity is employed.
B. Sensing-Assisted Beam Tracking and Prediction
Once the communication link is established, i.e., the initial
access is accomplished by beam training, both the transmitter
and receiver are required to keep tracking the variation of
the optimal beam pairs for the purpose of preserving the
communication quality, which is known as beam tracking
[167], [168]. Beam tracking schemes exploit the temporal
correlation between adjacent signal blocks, i.e., the previously
estimated beams are utilized as prior information for the
current epoch. By doing so, the search space of the beams
can be maintained to a small interval centered around the
previous beam, thus avoiding the transmission of redundant
pilots. Nonetheless, the receiver still needs to feed back the
optimal beam index to the transmitter in each of beam tracking
cycles. Again, it is possible to remove the feedback loop by
using a radar sensor mounted on the transmitter.
By taking a closer look at the above radar-aided beam train-
ing and tracking schemes, we see that the S&C coordination
gain is achieved by reducing the training overheads, but at the
cost of extra radar hardware, i.e., with the loss of integration
gain [165], [166]. Moreover, in high-mobility communication
channels, e.g., V2X channels, it is necessary to have the
capability of beam prediction , as beam tracking may not be
sufﬁcient to adapt to fast-changing channels. To address these
issues, the authors of [79], [80] consider employing ISAC
signaling in V2I beam tracking and prediction, which demands
no dedicated sensors and hence realizes both integration and
coordination gains.
Consider an ISAC-enabled V2I downlink shown in Fig.
16, where an RSU equipped with Nt transmit and Nr re-
ceive antennas is serving a single-antenna vehicle in the LoS
channel. The ISAC signal is transmitted on a block-by-block

28
basis. At the nth transmission block, the vehicle’s state is
represented by xn = [dn,vn,θn]T , where dn, vn, and θn are
the distance, velocity, and azimuth angle of the vehicle relative
to the RSU, which are assumed to be constant within a single
block. Suppose that the initial access is performed via radar-
aided beam training method upon the arrival of the vehicle,
based on which the RSU acquires the parameter estimates
ˆ x0 =
[
ˆd0, ˆv0, ˆθ0
]T
. The RSU then tracks and predicts the
vehicle’s state following the steps below:
State Prediction: At the (n− 1)th epoch, the RSU predicts
the vehicle’s state at the nth epoch as
ˆ xn|n−1 ≜
[
ˆdn|n−1, ˆvn|n−1, ˆθn|n−1
]T
=P (ˆ xn−1), (72)
where ˆ xn|n−1 stands for the nth predicted state based on
the (n− 1)th estimate, and P (·) is a predictor, which can
be designed either through model-based or model-free meth-
ods. While the model-based prediction typically relies on
the vehicle’s kinetic model, model-free approaches can be
built upon machine learning frameworks, which is particularly
useful in the case of complex trafﬁc environment and channel
conditions.
Beamforming: With the predicted angle ˆθn|n−1 at hand,
the RSU transmits the following ISAC signal to the vehicle at
the nth epoch
˜ sn (t) = fHn sn (t), (73)
where fn and sn (t) are the predictive beamformer and the
unit-power data stream intended for the vehicle at epoch n.
The beamformer fn is given by
fn = a
(
ˆθn|n−1
)
, (74)
where a (θ)∈ CNt×1 is again the transmit steering vector. Ac-
cordingly, the received signal at the vehicle can be expressed
as
yC,n (t) =αnaH (θn) fnsn (t) +zC,n (t), (75)
where αn and zC (t) represents the channel coefﬁcient and
the AWGN with zero mean and varianceσ2C, respectively. The
achievable rate can be computed as
Rn = log
(
1 +
⏐⏐αnaH (θn) fn⏐⏐2
σ2C,n
)
. (76)
If the predicted angle is sufﬁciently accurate, i.e.,⏐⏐⏐ˆθn|n−1−θn⏐⏐⏐≈ 0, then the resulting high beamforming gain
aH (θn) fn is able to support reliable V2I communications.
State Tracking: Once the ISAC signal hits the vehicle, it
will be partially recived by the vehicle’s receiver, and will
also be partially reﬂected back to the RSU. The received echo
signal at the RSU can be modeled as
yR,n (t) =
βnej2πfD,ntb (θn) aH (θn) fnsn (t−τn) +zR,n (t), (77)
where βn is the reﬂection coefﬁcient, fD,n = 2vnfcc is the
Doppler frequency, with fc and c being the carrier frequency
and the speed of the light, respectively. Again, b (θ) denotes
the receive steering vector. τn = 2dnc stands for the round-
trip delay. Finally, zR,n (t) is the AWGN with zero mean and
variance of σ2R. By inputing (77) into the estimator F (·), the
nth state can be estimated as
ˆ xn =F (yR,n). (78)
Alternatively, by taking into account the prediction ˆ xn|n−1,
one can use a Bayesian ﬁlter FB (·), e.g., Kalman ﬁlter, to
improve the estimation precision. This can be expressed as
ˆ xn =FB
(
yR,n, ˆ xn|n−1
)
. (79)
The estimate ˆ xn is then served as the input of the predictor
for the (n + 1)th epoch.
By iteratively performing state/beam prediction and track-
ing, the RSU is able to keep up with the movement of the
vehicle, while preserving a high-quality V2I downlink. As
observed from the ISAC frame structure shown in Fig. 15,
ISAC based beam tracking /prediction schemes outperform the
communication-only protocols in the following aspects [169]:
• No downlink pilots are needed: The entire ISAC signal
block is exploited for both V2I communication and
vehicle sensing, where dedicated downlink pilots are no
longer needed. This reduces downlink overheads, while at
the same time improving radar estimation performance.
• No uplink feedbacks are needed: The uplink feedback
signal is replaced with the echo signal reﬂected by the
vehicle, which reduces the uplink overheads.
• No quantization errors: The communication-only
scheme requires quantizing the estimated angle before
feeding it back to the RSU. In contrast to that, the ISAC
scheme performs continuous angle estimation by relying
on the echoes received by the RSU, which improves the
estimation accuracy.
• Signiﬁcant matched-ﬁltering gain: The use of the entire
ISAC signal block for radar sensing beneﬁts from the
matched-ﬁltering gain, which is equal to the ISAC block
length. In general, the matched ﬁltering gain that spans
the whole communication block, is much more signiﬁcant
than that of the feedback based scheme, where only a
limited number of pilots are used for beam tracking. As
a result, the estimation accuracy is improved.
While the above study mainly focues on V2I communi-
cations, it can be straightforwardly genaralized to the V2V
scenairo, for which the above features still hold.
In Fig. 17, we consider a scenario where a 64-antenna
RSU serves a vehicle on a straight road, where the vehicle
is driving from one side at a distance of 25 m and a speed
of 18 m/s, passing by the RSU to another side. Since the
RSU transmits at a ﬁxed power, the communication rate ﬁrstly
increases and then decreases. We compare the achievable rate
of the ISAC scheme using extended Kalman ﬁltering (EKF),
and a feedback based communication-only scheme, namely the
auxiliary beam pair (ABP) tracking method proposed in [168].
It can be observed that while the ISAC scheme maintains a
relatively stable rate, the achievable rate of the ABP technique
goes down to zero drastically at 1040 ms, as it loses the track
of the vehicle’s angle. This further proves the superiority of
ISAC signaling for V2I beam tracking and prediction.

29
0 400 800 1200 1600 2000 2400
Time (ms)
0
5
10
15
20
25Achievable Rate (bps/Hz)
EKF-ISAC
ABP-Comms-Only
Vehicle RSU
Fig. 17. Achievable rates comparison of the ISAC based and communication-
only beam tracking schemes.
C. Sensing-Assisted Resource Allocation
Apart from assisting in mmWave beamforming, sensing can
also be a powerful tool for supporting the efﬁcient allocation
of more general wireless resources.
Sensing-Assisted Cell Handover: Let us consider again a
V2I downlink, where a vehicle drives from a cell into another.
In order to provide continuous communication service, han-
dover is typically needed between the RSUs. The conventional
handover protocol is built upon dual-connection techniques
[170], in which the vehicle is connected simultaneously with
a serving RSU and an idle RSU. The QoS of the two
links is measured by their receive SINR, i.e., SINR serve and
SINRidle. If SINR serve < SINRidle due to blockage or large
distance, then the serving RSU will handover and forward
the buffered data to the idle RSU. Given the high mobility
of the vehicle, frequent handovers and re-connections are
needed, which consume extra wireless resources. In view of
that, a more efﬁcient approach is to equip RSUs with the
ISAC ability, such that the idle RSU can actively monitors the
vehicle’s state, including the distance, velocity, azimuth angle,
and heading direction, by sending ISAC signals and hearing
their echoes. These results are then exploited to estimate the
time and location at when/where the vehicle enters into the
idle RSU’s coverage. Accordingly, the RSU then prepares the
resources and data intended for the vehicle in advance, such
that seamless high-quality service can be provided in an almost
handover-free mode.
Under the framework above, it would be even more inter-
esting to consider V2X scenarios where multiple vehicles are
served simultaneously. The resource allocation can be again
designed based on sensing the kinematic states, driving envi-
ronment, and geometrical relationship of vehicles, where both
S&C performance should be taken into account. Below we list
some potential allocation strategies for different resources.
Bandwidth Allocation: Bandwidth allocation for commu-
nications aims to maximize the spectral efﬁciency, or to satisfy
individual QoS requirement of users. In the case that the
spectrum is reused among multiple users, bandwidth allocation
should also take into account the avoidance/mitigation of
mutual interference [171], [172]. While bandwidth is key
to increasing the communication rate, one may recall (21)
to see that the it also determines the range resolution for
sensing. In ISAC-powered V2X networks, different vehicles
may demand different S&C services, and hence have various
needs for communication rate and sensing resolution. All
these requirements can be imposed as constraints in bandwidth
allocation designs given the overall spectrum available.
Beamwidth Allocation: Beamwidth plays an important role
for both S&C [173]. For faraway vehicles that are deemed to
be point-like targets, the transmit beam can be made as narrow
as possible, thus providing both high beamforming gain for
communication and superior angular resolution for sensing.
For nearby vehicles, however, things become distinctly differ-
ent, as the vehicle is no longer viewed as a point target but
an extended target. To sense the vehicle, a wide beam should
be employed to cover the vehicle’s body. On the other hand, a
narrow beam is still preferred for communication, since the
RSU should accurately steer the beam towards the receive
antennas mounted on the vehicle. Moreover, it is readily seen
that velocity also affects the beamwidth allocation, where
narrow and wide beams are preferred for low- and high-speed
vehicles, respectively [174].
Power Allocation: Power allocation affects almost all
aspects of S&C, as it is involved in all the performance
metrics. For multi-user communications, while the classical
water-ﬁlling power allocation design is able to maximize
the communication rate, it is not able to address the issue
of minimizing estimation errors. In V2X scenarios where
both high-throughput communication and high-accuracy lo-
calization services are required, S&C performance metrics
including CRB and communication rate, should be considered
simultaneously in the problem formulation. For instance, ISAC
power allocation designs are proposed in [79], [175], where
the CRB for vehicle tracking is minimized, subject to the sum-
rate constraint of multiple vehicles.
While Sec. VII mainly concentrates on vehicular com-
munications served by radar, we remark that sensing, not
just restricted to mono-static sensing, can indeed assist in a
wide variety of communication applictions that require low
overhead and latency, as well as efﬁcient resource allocation.
D. Sensing-Assisted PHY Security
The compelling applications emerging with 5G and beyond
such as remote-Health, V2X communications, are expected
to carry conﬁdential personal data. Ensuring security and
privacy is of key importance, and traditional cryptographic
techniques at the network layer [176] face a number of issues,
most importantly an increasing vulnerability with the relentless
growth of computational power. Critically, cyber threats start
from the acquisition of access to wireless trafﬁc, and this has
motivated decades-long research in security solutions at the
physical (PHY) layer.
Furthermore, the ISAC transmission poses unique security
challenges. The inclusion of data into the probing signal, used
to illuminate targets, makes it prone to eavesdropping from
potentially malicious radar targets [177]. Even if the data itself

30
is protected with higher layer encryption, the existence of a
communication link can still be detected from a malicious
target which can jeopardize the communication privacy, reveal
the AP’s location and ID and make it prone to cyberattacks
[178]–[180]. Classical communications-only PHY security so-
lutions often involve reducing the signal power at the direction
of the eavesdropper (target), which would severely deteriorate
the sensing performance of ISAC. There is an abundance of
communications-only PHY layer security approaches, ranging
from secure beamforming, jamming, artiﬁcial noise design,
as well as cooperative security designs [181], that could be
adopted to address this challenge. Recent work has focused
on addressing this vulnerability of ISAC by designing secure
ISAC transmission [177], [182]. This aims to address the
conﬂicting objectives of illuminating signal energy to the radar
target, while at the same time constraining the useful signal
energy (SNR) towards the same direction of the sensed target,
to inhibit its capability do eavesdrop the information signal
towards the communication users.
In addition to unique security challenges ISAC offers, it
provides key opportunities to address the limitations of PHY
security solutions. Importantly, the sensing functionality offers
new opportunities in making PHY security solutions practical
[183]. The major limitation of a large class of PHY security
solutions stems from the need for knowing the eavesdroppers’
(Eves) channels, or direction as a minimum. The sensing
capability has an enabling role for PHY security, where the
detected targets’ (Eves’) AoAs can be used to enable null
steering and secure beamforming, and provides new ground for
the development of sensing-assisted secure communications.
The provision of security is an additional requirement in the
wireless network of the future, that gives rise to new and unex-
plored tradeoffs at the cross-domain among communications,
sensing, and security.
VIII. T HE ROAD AHEAD
A. Summary
In this paper, we provided our vision of the future dual-
functional wireless networks supported by integrated sensing
and communications (ISAC) technologies. To begin with, we
overviewed the historical development of radar and commu-
nications systems, based on which a formal deﬁnition and
rationale for ISAC was given, followed by the deﬁnition of
two types of gains in ISAC. We discussed various applications
and use cases supported by ISAC, as well as its industrial
progress and relevant standardization activities. We further
investigated the technical aspects of ISAC, from the perfor-
mance tradeoff between S&C, to the ISAC waveform design,
and ISAC receiver design. As a step further, we have shown
the great beneﬁts achieved by communication-assisted sens-
ing and sensing-assisted communication, respectively, which
paves the way towards the future perceptive network. In the
next subsection, we speculate on the potential interplay and
connection between ISAC and other emerging communication
technologies.
ISAC 
Transceiver
Targets
Edge 
server
Local AI
models
Global AI
models
Local AI models 
uploading
Global AI models 
downloading
Fig. 18. ISAC meets edge intelligence.
B. Interplay Between ISAC and Other Emerging Technologies
1) ISAC Meets Edge Intelligence: Edge intelligence has
been recognized as another key technology towards the next-
generation wireless networks such as 6G (see, e.g., [184]).
Driven by the recent success of mobile edge computing
(MEC) [185], [186], edge intelligence pushes the computation-
intensive artiﬁcial intelligence (AI) tasks from the centralized
cloud to distributed BSs at the wireless network edge, in order
to efﬁciently utilize the massive data generated at a large
number of edge devices. The integration with edge intelligence
is important to unlock the full potential of ISAC. In particular,
the ISAC is expected to generate a large volume of data at
distributed wireless transceivers, which need to be properly
processed (potentially jointly processed with sensed data from
other sensors like camera and lidar) via AI algorithms in
a swift manner (for, e.g., recognition), in order to support
applications with ultra-low-latency sensing-communication-
computation-control requirements. Towards this end, the fed-
erated edge learning has emerged as a promising solution, in
which the sensing devices can iteratively exchange their locally
trained AI models for updating the desired global AI model
in a distributed manner, while preserving data privacy at each
sensing device, as shown in Fig. 18 [187], [188].
Integration between ISAC and edge intelligence poses new
technical challenges [189]. First, due to the scarcity of spec-
trum resources, the wireless communication for exchanging
AI models between sensing devices and edge servers is
recognized as the performance bottleneck for federated edge
learning. With the integration of ISAC, this issue will become
even more severe, as the limited spectrum resources need to
be further reused to support the radio sensing functionality.
To resolve this problem, a new multiple access technique,
namely over-the-air computation (AirComp) [190], has been
utilized to enhance the communication efﬁciency of federated
edge learning (see, e.g., [191]), in which the sensing devices
can simultaneously transmit their local AI models over the
same frequency band for global aggregation, by exploiting the
wireless signal superposition at the edge server. With AirComp
involved, it becomes an interesting new research direction
to coordinate its integration with ISAC. How to optimize
the power control (see, e.g., [192]) and wireless resource
allocation to balance the AirComp and sensing performances,
and how to properly control the multi-cell sensing and Air-

31
Comp interference (see, e.g., [193]) are interesting problems
to be investigated. Proper precoding design may also play an
important role (see, e.g., [194]).
Furthermore, the ISAC-and-edge-intelligence integration in-
troduces more complicated tradeoffs among sensing, com-
munication, and computation. In particular, the demand of
higher sensing accuracy and resolution in ISAC may lead
to more data to be processed, which thus induces higher
communication and computational burden. To deal with such
tradeoffs, the joint design over the sensing-communication-
computation ﬂow is crucial, in which the ultimate goals of the
AI tasks (e.g., recognition accuracy) should be adopted as new
optimization objectives (instead of considering conventional
sensing/communication metrics). For instance, adaptive AI-
task-aware ISAC may be an interesting direction worth pursu-
ing, in which the sensing devices can adaptively adjust their
sensing area/accuracy/resolution based on the requirements
of AI tasks subject to wireless and computation resource
constraints.
2) ISAC Supported By Reconﬁgurable Intelligent Surface
(RIS): Reconﬁgurable intelligent surface (RIS), also known as
intelligent reﬂecting surface (IRS) and large intelligent surface
(LIS), is a new type of passive metamaterial device consisting
of a large number of reﬂecting elements whose reﬂecting
amplitudes and phases can be independently controlled to
reconﬁgure the wireless environment [195], [196]. While RIS
has shown great potential in increasing the spectrum and en-
ergy efﬁciency of wireless communications, it is also expected
to beneﬁt the ISAC by providing better sensing coverage,
and enhancing the sensing accuracy and resolution. First, in
conventional ISAC systems, sensing generally depends on
the LoS link between the ISAC transmitter and the target
of interes. How to sense targets without LoS connections
is quite challenging. To resolve this issue, RIS can serve
as a viable new solution by potentially providing additional
LoS links with targets in those conventionally NLoS covered
areas, as shown in Fig. 19. Next, RIS is also beneﬁcial to
facilitate the sensing of targets with LoS links, via providing
an additional link to see the targets from a different angle, thus
potentially enhancing the sensing and localization accuracy
and resolution. To fully reap these beneﬁts, it is important to
properly design the deployment locations of RISs based on
the new sensing requirements, and optimize their reﬂecting
amplitudes and phases in real time by taking into account the
new sensing performance metrics and new co-channel sensing-
communication interference. This is a challenging task, espe-
cially when there are many RISs deployed in a distributed
manner and when the RIS-related network information is only
partially available due to its passive nature.
One the other hand, ISAC in return can also be useful for
enhancing wireless communication performance with RISs.
One of the key technical challenges faced in RIS-enabled
wireless communications is that the RIS-related CSI is difﬁcult
and costly to obtain due to the lack of signal processing
capability at the RIS, thus making beam tracking and beam
alignment difﬁcult. In this case, by employing the sensing
function to measure the parameters related to communication
users (e.g., the angle-of-arrival/departure), ISAC provides an
ISAC 
Transceiver
RIS 1
 Target 1
Obstacle
CU
 Target 2
RIS 2
Fig. 19. ISAC served by Reconﬁgurable Intelligent Surface.
alternative approach to acquire the CSI to facilitate the RISs’
passive beamforming.
3) ISAC With UAVs: With recent technical advances, UA Vs
have found abundant applications in wireless networks as,
e.g., aerial users, relays, BSs, or APs. In this case, wireless
networks are experiencing a paradigm shift from conventional
terrestrial ones to terrestrial-and-aerial integration (see, e.g.,
[197] and the references therein). As a result, the interplay
between UA Vs and ISAC is becoming another interesting
research topic, in which the UA Vs may act as sensing targets,
communication users, and aerial ISAC platforms, respectively,
depending on different application scenarios discussed in Sec.
II.
First, similar to conventional radar, ISAC enabled cellular
networks can be used to detect and monitor the undesirable
or suspicious UA V targets in the sky to protect the cyber
and physical security. Next, when UA Vs are connected into
wireless networks as communication users, the on-ground BSs
can send ISAC signals to localize these UA Vs during the
communication, and measure the related channel parameters.
Such information may be utilized to facilitate the transmit
beam tracking and wireless resource allocation, thus increasing
the communication data rate and reliability, mitigating the
severe ground-air interference, and enhancing the data security,
with reduced signaling overhead. Finally, UA Vs can act as
mobile aerial platforms to perform ISAC with on-ground
targets and communication users. This is appealing for both
sensing and communication, as UA Vs are highly likely to
have strong LoS links towards users. By exploiting the UA Vs’
fully controllable mobility, they are able to maneuver towards
desired locations to provide ISAC services on demand, and the
UA Vs’ maneuver control provides a new DoF for optimizing
ISAC performance. How to properly design the ISAC signal
processing and resource allocation, together with the UA Vs’
deployment or trajectory optimization is an interesting but
challenging problem. Moreover, as discussed in Sec. VII-D,
security of ISAC transmission should be guaranteed in the
event that an unauthorized UA V eavesdrops the information
intended for the legitimate UA V user.
In addition to the above research directions, ISAC may also
ﬁnd potential usage in conjunction with other emerging and

32
Ground ISAC 
Transceiver
 Ground 
Targets
Ground CU
UAV Target (Potential 
Evaesdropper)
UAV User
UAV ISAC 
Transceiver
Fig. 20. ISAC with unmanned aerial vehicles.
important technologies, e.g., low-earth-orbit (LEO) satellite
networks [198], [199], Terahertz (THz) communications and
sensing [200], [201], digital twin [202], [203], orthogonal time
frequency space (OTFS) modulation [204]–[206], and more.
Given the page limit, we will not elaborate on these aspects.
We ﬁrmly believe that ISAC will not only serve as the
foundation of the new air interface for the 6G network, but
will also act as the bond to bridge the physical and cyber
worlds, where everything is sensed, everything is connected,
and everything is intelligent.
REFERENCES
[1] W. Saad, M. Bennis, and M. Chen, “A vision of 6G wireless systems:
Applications, trends, technologies, and open research problems,” IEEE
Network, vol. 34, no. 3, pp. 134–142, 2020.
[2] Y . Cui, F. Liu, X. Jing, and J. Mu, “Integrating sensing and communi-
cations for ubiquitous IoT: Applications, trends and challenges,” IEEE
Network, 2021.
[3] Y . Ma, G. Zhou, and S. Wang, “Wiﬁ sensing with channel state
information: A survey,” ACM Comput. Surv., vol. 52, no. 3, Jun. 2019.
[Online]. Available: https://doi.org/10.1145/3310194
[4] D. K. P. Tan, R. Du, Y . Sun, T. X. Han, D. X. Yang, W. Tong, W. Ding,
Y . Li, and Y . Zhang, “Wi-sneeze- sneeze sensing using wi-ﬁ signals,”
in 2020 IEEE Globecom Workshops (GC Wkshps) , 2020, pp. 1–6.
[5] X. Wang, Z. Fei, J. A. Zhang, J. Huang, and J. Yuan, “Constrained
utility maximization in dual-functional radar-communication multi-
UA V networks,”IEEE Trans. Commun., vol. 69, no. 4, pp. 2660–2672,
2021.
[6] S. D. Blunt, P. Yatham, and J. Stiles, “Intrapulse radar-embedded
communications,” IEEE Trans. Aerosp. Electron. Syst. , vol. 46, no. 3,
pp. 1185–1200, 2010.
[7] R. M. Mealey, “A method for calculating error probabilities in a radar
communication system,” IEEE Trans. Space Electron. Telemetry, vol. 9,
no. 2, pp. 37–42, Jun. 1963.
[8] C. Sturm and W. Wiesbeck, “Waveform design and signal processing
aspects for fusion of wireless communications and radar sensing,”Proc.
IEEE, vol. 99, no. 7, pp. 1236–1259, Jul. 2011.
[9] P. Kumari, A. Mezghani, and R. W. Heath, “JCR70: A low-complexity
millimeter-wave proof-of-concept platform for a fully-digital SIMO
joint communication-radar,” IEEE Open J. Veh. Technol. , vol. 2, pp.
218–234, 2021.
[10] F. Liu, C. Masouros, A. Petropulu, H. Grifﬁths, and L. Hanzo, “Joint
radar and communication design: Applications, state-of-the-art, and the
road ahead,” IEEE Trans. Commun., vol. 66, no. 6, pp. 3834–3862, Jun.
2020.
[11] D. N. Lapedes, McGraw-Hill dictionary of scientiﬁc and technical
terms., 1974.
[12] A. J. Fenn, D. H. Temme, W. P. Delaney, and W. E. Courtney, “The
development of phased-array radar technology,” Lincoln Laboratory
Journal, vol. 12, no. 2, pp. 321–340, 2000.
[13] R. L. Walker, “Alvarez: Adventures of a physicist,” Science, vol. 240,
no. 4855, pp. 1065–1067, 1988.
[14] H. Grifﬁths, “The MAMMUT phased array radar: Compulsive hoard-
ing,” in Proc. International Radar Conference (RADAR) , Sept. 2019,
pp. 23–27.
[15] A. J. Paulraj and T. Kailath, “Increasing capacity in wireless broadcast
systems using distributed transmission/directional reception (DTDR),”
Sept. 1994, US Patent 5,345,599.
[16] G. Foschini and M. Gans, “On limits of wireless communications in a
fading environment when using multiple antennas,” Wireless Personal
Commun., vol. 6, no. 3, pp. 311–335, Mar 1998.
[17] E. Telatar, “Capacity of multi-antenna gaussian channels,” European
Trans. Telecommun., vol. 10, no. 6, pp. 585–595, 1999.
[18] E. Fishler, A. Haimovich, R. Blum, D. Chizhik, L. Cimini, and
R. Valenzuela, “MIMO radar: An idea whose time has come,”
in Proceedings of the 2004 IEEE Radar Conference (IEEE Cat.
No.04CH37509), Apr. 2004, pp. 71–78.
[19] D. Cohen, D. Cohen, and Y . C. Eldar, “High resolution FDMA MIMO
radar,” IEEE Trans. Aerosp. Electron. Syst. , vol. 56, no. 4, pp. 2806–
2822, 2020.
[20] J. Li and P. Stoica, “MIMO radar with colocated antennas,” IEEE
Signal Process. Mag. , vol. 24, no. 5, pp. 106–114, Sept. 2007.
[21] A. M. Haimovich, R. S. Blum, and L. J. Cimini, “MIMO radar with
widely separated antennas,” IEEE Signal Process. Mag., vol. 25, no. 1,
pp. 116–129, 2008.
[22] P. K. Hughes and J. Y . Choe, “Overview of advanced multifunction
RF system (AMRFS),” in Proceedings 2000 IEEE International Con-
ference on Phased Array Systems and Technology (Cat. No.00TH8510),
May 2000, pp. 21–24.
[23] G. C. Tavik, C. L. Hilterbrick, J. B. Evins, J. J. Alter, J. G. Crnkovich,
J. W. de Graaf, W. Habicht, G. P. Hrin, S. A. Lessin, D. C. Wu, and
S. M. Hagewood, “The advanced multifunction RF concept,” IEEE
Trans. Microw. Theory Technol., vol. 53, no. 3, pp. 1009–1020, Mar.
2005.
[24] J. A. Molnar, I. Corretjer, and G. Tavik, “Integrated topside - integration
of narrowband and wideband array antennas for shipboard communica-
tions,” in 2011 - MILCOM 2011 Military Communications Conference,
Nov. 2011, pp. 1802–1807.
[25] M. Roberton and E. R. Brown, “Integrated radar and communications
based on chirped spread-spectrum techniques,” in IEEE MTT-S Int.
Microw. Symp. Dig., vol. 1, Aug. 2003, pp. 611–614.
[26] G. N. Saddik, R. S. Singh, and E. R. Brown, “Ultra-wideband multi-
functional communications/radar system,” IEEE Trans. Microw. Theory
Technol., vol. 55, no. 7, pp. 1431–1437, Jul. 2007.
[27] M. Jamil, H.-J. Zepernick, and M. I. Pettersson, “On integrated radar
and communication systems using Oppermann sequences,” in Proc.
MILCOM IEEE Military Commun. Conf. , Nov. 2008, pp. 1–6.
[28] L. Han and K. Wu, “Joint wireless communication and radar sensing
systems-state of the art and future prospects,” IET Microw. Antennas
Propag., vol. 7, no. 11, pp. 876–885, 2013.
[29] D. Garmatyuk, J. Schuerger, and K. Kauffman, “Multifunctional
software-deﬁned radar sensor and data communication system,” IEEE
Sensors J., vol. 11, no. 1, pp. 99–106, Jan. 2011.
[30] DARPA. (2016) Shared spectrum access for radar and communications
(SSPARC). [Online]. Available: https://www.darpa.mil/program/
shared-spectrum-access-for-radar-and-communications
[31] B. Li and A. P. Petropulu, “Joint transmit designs for coexistence of
MIMO wireless communications and sparse sensing radars in clutter,”
IEEE Trans. Aerosp. Electron. Syst. , vol. 53, no. 6, pp. 2846–2864,
Dec. 2017.
[32] J. A. Mahal, A. Khawar, A. Abdelhadi, and T. C. Clancy, “Spectral
coexistence of MIMO radar and MIMO cellular system,” IEEE Trans.
Aerosp. Electron. Syst., vol. 53, no. 2, pp. 655–668, Apr. 2017.
[33] C. D’Andrea, S. Buzzi, and M. Lops, “Communications and radar
coexistence in the massive MIMO regime: Uplink analysis,” IEEE
Trans. Wireless Commun., vol. 19, no. 1, pp. 19–33, 2020.
[34] K. V . Mishra, Y . C. Eldar, E. Shoshan, M. Namer, and M. Meltsin, “A
cognitive sub-Nyquist MIMO radar prototype,” IEEE Trans. Aerosp.
Electron. Syst., vol. 56, no. 2, pp. 937–955, 2020.
[35] D. Cohen, K. V . Mishra, and Y . C. Eldar, “Spectrum sharing radar: Co-
existence via Xampling,” IEEE Trans. Aerosp. Electron. Syst. , vol. 54,
no. 3, pp. 1279–1296, 2018.
[36] X. Zhang, A. F. Molisch, and Sun-Yuan Kung, “Variable-phase-shift-
based RF-baseband codesign for MIMO antenna selection,” IEEE
Trans. Signal Process., vol. 53, no. 11, pp. 4091–4103, Nov. 2005.
[37] T. L. Marzetta, “Noncooperative cellular wireless with unlimited num-
bers of base station antennas,” IEEE Trans. Wireless Commun., vol. 9,
no. 11, pp. 3590–3600, Nov. 2010.

33
[38] A. Hassanien and S. A. V orobyov, “Phased-MIMO radar: A tradeoff
between phased-array and mimo radars,” IEEE Trans. Signal Process.,
vol. 58, no. 6, pp. 3137–3151, Jun. 2010.
[39] T. S. Rappaport, S. Sun, R. Mayzus, H. Zhao, Y . Azar, K. Wang, G. N.
Wong, J. K. Schulz, M. Samimi, and F. Gutierrez, “Millimeter wave
mobile communications for 5G cellular: It will work!” IEEE Access ,
vol. 1, pp. 335–349, 2013.
[40] O. E. Ayach, S. Rajagopal, S. Abu-Surra, Z. Pi, and R. W. Heath,
“Spatially sparse precoding in millimeter wave MIMO systems,” IEEE
Trans. Wireless Commun., vol. 13, no. 3, pp. 1499–1513, Mar. 2014.
[41] J. A. Zhang, A. Cantoni, X. Huang, Y . J. Guo, and R. W. Heath,
“Framework for an innovative perceptive mobile network using joint
communication and sensing,” in 2017 IEEE 85th Vehicular Technology
Conference (VTC Spring) , 2017, pp. 1–5.
[42] S. Fortunati, L. Sanguinetti, F. Gini, M. S. Greco, and B. Himed, “Mas-
sive MIMO radar for target detection,” IEEE Trans. Signal Process. ,
vol. 68, pp. 859–871, Jan. 2020.
[43] J. G. Andrews, S. Buzzi, W. Choi, S. V . Hanly, A. Lozano, A. C. K.
Soong, and J. C. Zhang, “What will 5G be?” IEEE J. Sel. Areas
Commun., vol. 32, no. 6, pp. 1065–1082, 2014.
[44] T. Gong, N. Shlezinger, S. S. Ioushua, M. Namer, Z. Yang, and Y . C.
Eldar, “RF chain reduction for MIMO systems: A hardware prototype,”
IEEE Syst. J. , vol. 14, no. 4, pp. 5296–5307, 2020.
[45] R. W. Heath, N. Gonz ´alez-Prelcic, S. Rangan, W. Roh, and A. M.
Sayeed, “An overview of signal processing techniques for millimeter
wave MIMO systems,” IEEE J. Sel. Topics Signal Process. , vol. 10,
no. 3, pp. 436–453, Apr. 2016.
[46] X. Yu, J.-C. Shen, J. Zhang, and K. B. Letaief, “Alternating mini-
mization algorithms for hybrid precoding in millimeter wave MIMO
systems,” IEEE J. Sel. Topics Signal Process. , vol. 10, no. 3, pp. 485–
500, 2016.
[47] K. V . Mishra, M. Bhavani Shankar, V . Koivunen, B. Ottersten, and
S. A. V orobyov, “Toward millimeter-wave joint radar communications:
A signal processing perspective,” IEEE Signal Process. Mag. , vol. 36,
no. 5, pp. 100–114, 2019.
[48] D. Ma, N. Shlezinger, T. Huang, Y . Liu, and Y . C. Eldar, “Joint radar-
communication strategies for autonomous vehicles: Combining two key
automotive technologies,” IEEE Signal Process. Mag. , vol. 37, no. 4,
pp. 85–97, Jul. 2020.
[49] A. Hassanien, M. G. Amin, Y . D. Zhang, and F. Ahmad, “Signaling
strategies for dual-function radar-communications: An overview,”IEEE
Aerospace and Electronic Systems Magazine , 2016.
[50] A. Zhang, M. L. Rahman, X. Huang, Y . J. Guo, S. Chen, and R. W.
Heath, “Perceptive mobile networks: Cellular networks with radio
vision via joint communication and radar sensing,” IEEE Veh. Technol.
Mag., vol. 16, no. 2, pp. 20–30, 2021.
[51] J. A. Zhang, M. L. Rahman, K. Wu, X. Huang, Y . J. Guo, S. Chen,
and J. Yuan. (2020) “Enabling joint communication and radar sensing
in mobile networks – a survey”. Submitted to IEEE Commun. Surveys
Tuts. [Online]. Available: https://arxiv.org/abs/2006.07559
[52] B. Paul, A. R. Chiriyath, and D. W. Bliss, “Survey of RF communi-
cations and sensing convergence research,” IEEE Access , vol. 5, pp.
252–270, 2017.
[53] J. A. Zhang, F. Liu, C. Masouros, R. W. Heath, Z. Feng, L. Zheng, and
A. Petropulu. (2021) “An overview of signal processing techniques for
joint communication and radar sensing”. IEEE J. Sel. Topics Signal
Process., in press. [Online]. Available: https://arxiv.org/abs/2102.12780
[54] T. Wild, V . Braun, and H. Viswanathan, “Joint design of communication
and sensing for beyond 5G and 6G systems,” IEEE Access, vol. 9, pp.
30 845–30 857, 2021.
[55] Z. Feng, Z. Fang, Z. Wei, X. Chen, Z. Quan, and D. Ji, “Joint radar
and communication: A survey,” China Commun. , vol. 17, no. 1, pp.
1–27, 2020.
[56] A. Liu et al. (2021) “A survey on fundamental limits of integrated
sensing and communication”. Submitted to IEEE Commun. Surveys
Tuts. [Online]. Available: https://arxiv.org/abs/2104.09954
[57] D. K. Pin Tan, J. He, Y . Li, A. Bayesteh, Y . Chen, P. Zhu, and
W. Tong, “Integrated sensing and communication in 6G: Motivations,
use cases, requirements, challenges and future directions,” in 2021 1st
IEEE International Online Symposium on Joint Communications &
Sensing (JC&S), 2021, pp. 1–6.
[58] L. Zheng, M. Lops, Y . C. Eldar, and X. Wang, “Radar and communi-
cation coexistence:An overview: A review of recent methods,” IEEE
Signal Process. Mag. , vol. 36, no. 5, pp. 85–99, 2019.
[59] A. Hassanien, M. G. Amin, E. Aboutanios, and B. Himed, “Dual-
function radar communication systems: A solution to the spectrum
congestion problem,” IEEE Signal Process. Mag. , vol. 36, no. 5, pp.
115–126, 2019.
[60] F. Liu, L. Zhou, C. Masouros, A. Li, W. Luo, and A. Petropulu, “To-
ward dual-functional radar-communication systems: Optimal waveform
design,” IEEE Trans. Signal Process. , vol. 66, no. 16, pp. 4264–4279,
Aug. 2018.
[61] J. A. del Peral-Rosado, R. Raulefs, J. A. L ´opez-Salcedo, and G. Seco-
Granados, “Survey of cellular mobile radio localization methods: From
1G to 5G,” IEEE Commun. Surveys Tuts. , vol. 20, no. 2, pp. 1124–
1148, 2018.
[62] 3GPP, “Study on NR positioning support,” TR 38.855 16.0.0 , 2019.
[63] K. Chen, D. Zhang, L. Yao, B. Guo, Z. Yu, and Y . Liu, “Deep learning
for sensor-based human activity recognition: Overview, challenges,
and opportunities,” ACM Comput. Surv. , vol. 54, no. 4, May 2021.
[Online]. Available: https://doi.org/10.1145/3447744
[64] H. Lasi, P. Fettke, H.-G. Kemper, T. Feld, and M. Hoffmann, “Industry
4.0,” Business & information systems engineering , vol. 6, no. 4, pp.
239–242, 2014.
[65] A. Moreira, P. Prats-Iraola, M. Younis, G. Krieger, I. Hajnsek, and K. P.
Papathanassiou, “A tutorial on synthetic aperture radar,” IEEE Geosci.
Remote Sens. Mag. , vol. 1, no. 1, pp. 6–43, 2013.
[66] D. K. Pin Tan, J. He, Y . Li, A. Bayesteh, Y . Chen, P. Zhu, and
W. Tong, “Integrated sensing and communication in 6G: Motivations,
use cases, requirements, challenges and future directions,” in 2021 1st
IEEE International Online Symposium on Joint Communications and
Sensing (JC&S), 2021, pp. 1–6.
[67] Y . Zeng, Q. Wu, and R. Zhang, “Accessing from the sky: A tutorial
on UA V communications for 5G and beyond,” IEEE Proc., vol. 107,
no. 12, pp. 2327–2375, 2019.
[68] Q. Huang, H. Chen, and Q. Zhang, “Joint design of sensing and
communication systems for smart homes,” IEEE Network , vol. 34,
no. 6, pp. 191–197, 2020.
[69] Q. Huang, Z. Luo, J. Zhang, W. Wang, and Q. Zhang, “LoRadar:
Enabling concurrent radar sensing and LoRa communication,” IEEE
Trans. Mobile Comput. , pp. 1–1, 2020.
[70] W. Shoulberg, “Ces comes home: The best intros at the show,” Forbes,
Jan 2021.
[71] S. Shekhar, S. K. Feiner, and W. G. Aref, “Spatial computing,”
Commun. ACM , vol. 59, no. 1, p. 72–81, Dec. 2015. [Online].
Available: https://doi.org/10.1145/2756547
[72] Xiaomi. (2021) XIAOMI introduces groundbreaking UWB
technology. [Online]. Available: https://blog.mi.com/en/2020/10/13/
xiaomi-introduces-groundbreaking-uwb-technology
[73] T. Luettel, M. Himmelsbach, and H.-J. Wuensche, “Autonomous
ground vehicles—concepts and a path to the future,” IEEE Proc., vol.
100, no. Special Centennial Issue, pp. 1831–1839, 2012.
[74] O. Kaiwartya, A. H. Abdullah, Y . Cao, A. Altameem, M. Prasad, C.-T.
Lin, and X. Liu, “Internet of vehicles: Motivation, layered architecture,
network model, challenges, and future aspects,” IEEE Access , vol. 4,
pp. 5356–5373, 2016.
[75] M. Sybis, V . Vukadinovic, M. Rodziewicz, P. Sroka, A. Langowski,
K. Lenarska, and K. Wesołowski, “Communication aspects of a modi-
ﬁed cooperative adaptive cruise control algorithm,” IEEE Trans. Intell.
Transp. Syst., vol. 20, no. 12, pp. 4513–4523, 2019.
[76] T. Zeng, O. Semiari, W. Saad, and M. Bennis, “Joint communication
and control for wireless autonomous vehicular platoon systems,” IEEE
Trans. Commun., vol. 67, no. 11, pp. 7907–7922, 2019.
[77] L. Wang, Y . Duan, Y . Lai, S. Mu, and X. Li. (2021) “V2I-based
platooning design with delay awareness”. Submitted to IEEE Trans.
Intell. Transp. Syst. [Online]. Available: https://arxiv.org/abs/2102.
03243
[78] V . Milanes, J. Villagra, J. Godoy, J. Simo, J. Perez, and E. Onieva, “An
intelligent v2i-based trafﬁc management system,” IEEE Trans. Intell.
Transp. Syst., vol. 13, no. 1, pp. 49–58, 2012.
[79] F. Liu, W. Yuan, C. Masouros, and J. Yuan, “Radar-assisted predictive
beamforming for vehicular links: Communication served by sensing,”
IEEE Trans. Wireless Commun., vol. 19, no. 11, pp. 7704–7719, 2020.
[80] W. Yuan, F. Liu, C. Masouros, J. Yuan, D. W. K. Ng, and N. Gonz ´alez-
Prelcic, “Bayesian predictive beamforming for vehicular networks:
A low-overhead joint radar-communication approach,” IEEE Trans.
Wireless Commun., vol. 20, no. 3, pp. 1442–1456, 2021.
[81] C. B. Barneto, E. Rastorgueva-Foi, M. F. Keskin, T. Riihonen, M. Tu-
runen, J. Talvitie, H. Wymeersch, and M. Valkama, “Millimeter-wave
mobile sensing and environment mapping: Models, algorithms and
validation,” 2021.
[82] S. K. Rao and R. Prasad, “Impact of 5G technologies on industry 4.0,”
Wireless personal communications, vol. 100, no. 1, pp. 145–159, 2018.

34
[83] P. Popovski, c. Stefanovic, J. J. Nielsen, E. de Carvalho, M. Angjelichi-
noski, K. F. Trillingsgaard, and A.-S. Bana, “Wireless access in ultra-
reliable low-latency communication (urllc),” IEEE Trans. Commun. ,
vol. 67, no. 8, pp. 5783–5801, 2019.
[84] D. C. Schedl, I. Kurmi, and O. Bimber, “An autonomous drone
for search and rescue in forests using airborne optical sectioning,”
Science Robotics , vol. 6, no. 55, 2021. [Online]. Available:
https://robotics.sciencemag.org/content/6/55/eabg1188
[85] H. Messer, A. Zinevich, and P. Alpert, “Environmental monitoring
by wireless communication networks,” Science, vol. 312, no. 5774,
pp. 713–713, 2006. [Online]. Available: https://science.sciencemag.
org/content/312/5774/713
[86] J. Lien, N. Gillian, M. E. Karagozler, P. Amihood, C. Schwesig,
E. Olson, H. Raja, and I. Poupyrev, “Soli: Ubiquitous gesture sensing
with millimeter wave radar,” ACM Transactions on Graphics (TOG) ,
vol. 35, no. 4, pp. 1–19, 2016.
[87] Ericsson, “A research outlook towards 6G,” Ericsson, White Paper.
[88] N. DOCOMO, “White paper 5G evolution and 6G (version 3.0),” NTT
DOCOMO, White Paper.
[89] M. W. Live, “China unicom, zte explore 6g options.”
[90] C. Cordeiro, “Next-generation Wi-Fi: Wi-
Fi 7 and beyond,” Intel Corporation,
https://www.intel.com/content/dam/www/public/us/en/documents/pdf/wi-
ﬁ-7-and-beyond.pdf, Technical Report, July 2020.
[91] M. W. Live. (2021) Huawei readies 5.5G as bosses push evolution. [On-
line]. Available: https://www.mobileworldlive.com/featured-content/
home-banner/huawei-readies-5-5{G}-as-bosses-push-evolution
[92] M. Alloulah and H. Huang, “Future millimeter-wave indoor systems:
A blueprint for joint communication and sensing,” Computer, vol. 52,
no. 7, pp. 16–24, July 2019.
[93] F. Restuccia, “IEEE 802.11 bf: Toward ubiquitous Wi-Fi sensing,”
arXiv preprint arXiv:2103.14918 , 2021.
[94] S. M. Kay, Fundamentals of Statistical Signal Processing, Vol. II:
Detection Theory. Englewood Cliffs, NJ, USA: Prentice Hall, 1998.
[95] ——, Fundamentals of Statistical Signal Processing, Vol. I: Estimation
Theory. Englewood Cliffs, NJ, USA: Prentice Hall, 1998.
[96] P. Tait, Introduction to radar target recognition . IET, 2005, vol. 18.
[97] A. Goldsmith, Wireless communications. Cambridge university press,
2005.
[98] D. Tse and P. Viswanath, Fundamentals of wireless communication .
Cambridge university press, 2005.
[99] T. M. Cover, Elements of information theory . John Wiley & Sons,
1999.
[100] D. Guo, S. Shamai, and S. Verdu, “Mutual information and minimum
mean-square error in Gaussian channels,” IEEE Trans. Inf. Theory ,
vol. 51, no. 4, pp. 1261–1282, 2005.
[101] A. Sutivong, T. Cover, and M. Chiang, “Tradeoff between message and
state information rates,” in Proceedings IEEE International Symposium
on Information Theory (ISIT) , 2001, pp. 303–.
[102] A. Sutivong, T. Cover, M. Chiang, and Y .-H. Kim, “Rate vs. distortion
trade-off for channels with state information,” in Proceedings IEEE
International Symposium on Information Theory (ISIT), 2002, pp. 226–
.
[103] A. Sutivong, M. Chiang, T. Cover, and Y .-H. Kim, “Channel capacity
and state estimation for state-dependent Gaussian channels,” IEEE
Trans. Inf. Theory, vol. 51, no. 4, pp. 1486–1495, 2005.
[104] W. Zhang, S. Vedantam, and U. Mitra, “Joint transmission and state
estimation: A constrained channel coding approach,” IEEE Trans. Inf.
Theory, vol. 57, no. 10, pp. 7084–7095, 2011.
[105] C. Choudhuri, Y .-H. Kim, and U. Mitra, “Causal state communication,”
IEEE Trans. Inf. Theory , vol. 59, no. 6, pp. 3709–3719, 2013.
[106] M. Kobayashi, G. Caire, and G. Kramer, “Joint state sensing and
communication: Optimal tradeoff for a memoryless case,” in 2018
IEEE International Symposium on Information Theory (ISIT) , 2018,
pp. 111–115.
[107] M. Kobayashi, H. Hamad, G. Kramer, and G. Caire, “Joint state sensing
and communication over memoryless multiple access channels,” in
2019 IEEE International Symposium on Information Theory (ISIT) ,
2019, pp. 270–274.
[108] M. Ahmadipour, M. Wigger, and M. Kobayashi, “Joint sensing and
communication over memoryless broadcast channels,” in 2020 IEEE
Information Theory Workshop (ITW) , 2021, pp. 1–5.
[109] B. K. Chalise, M. G. Amin, and B. Himed, “Performance tradeoff
in a uniﬁed passive radar and communications system,” IEEE Signal
Process. Lett., vol. 24, no. 9, pp. 1275–1279, 2017.
[110] H. D. Grifﬁths and C. J. Baker, An introduction to passive radar .
Artech House, 2017.
[111] B. K. Chalise and B. Himed, “Performance tradeoff in a uniﬁed multi-
static passive radar and communication system,” in 2018 IEEE Radar
Conference (RadarConf18), 2018, pp. 0653–0658.
[112] F. Liu, Y .-F. Liu, A. Li, C. Masouros, and Y . C. Eldar. (2021)
“Cram´er-Rao bound optimization for joint radar-communication
design”. Submitted to IEEE Trans. Signa Process. [Online]. Available:
https://arxiv.org/abs/2101.12530
[113] Z. Ben-Haim and Y . C. Eldar, “On the constrained cram ´er–rao bound
with a singular ﬁsher information matrix,” IEEE Signal Process. Lett. ,
vol. 16, no. 6, pp. 453–456, Jun. 2009.
[114] X. Liu, T. Huang, N. Shlezinger, Y . Liu, J. Zhou, and Y . C. Eldar,
“Joint transmit beamforming for multiuser MIMO communications and
MIMO radar,” IEEE Trans. Signal Process. , vol. 68, pp. 3929–3944,
2020.
[115] H. Hua, J. Xu, and T.-X. Han. (2021) “Optimal transmit beamforming
for integrated sensing and communication”. Submitted to IEEE
Trans. Wireless Commun. [Online]. Available: https://arxiv.org/abs/
2104.11871
[116] Z.-Q. Luo, W.-K. Ma, A. M.-C. So, Y . Ye, and S. Zhang, “Semideﬁnite
relaxation of quadratic optimization problems,” IEEE Signal Process.
Mag., vol. 27, no. 3, pp. 20–34, 2010.
[117] F. Liu, C. Masouros, A. Li, H. Sun, and L. Hanzo, “MU-MIMO
communications with MIMO radar: From co-existence to joint trans-
mission,” IEEE Trans. Wireless Commun. , vol. 17, no. 4, pp. 2755–
2770, Apr. 2018.
[118] J. R. Guerci, R. M. Guerci, A. Lackpour, and D. Moskowitz, “Joint
design and operation of shared spectrum access for radar and com-
munications,” in 2015 IEEE Radar Conference (RadarCon) , 2015, pp.
0761–0766.
[119] D. W. Bliss, “Cooperative radar and communications signaling: The
estimation and information theory odd couple,” in 2014 IEEE Radar
Conference, May 2014, pp. 0050–0055.
[120] A. R. Chiriyath, B. Paul, G. M. Jacyna, and D. W. Bliss, “Inner
bounds on performance of radar and communications co-existence,”
IEEE Trans. Signal Process. , vol. 64, no. 2, pp. 464–474, Jan. 2016.
[121] G. Cui, H. Li, and M. Rangaswamy, “MIMO radar waveform design
with constant modulus and similarity constraints,” IEEE Trans. Signal
Process., vol. 62, no. 2, pp. 343–353, 2014.
[122] G. Li, S. Wang, J. Li, R. Wang, F. Liu, M. Zhang, X. Peng, and
T. X. Han. (2021) “Rethinking the tradeoff in integrated sensing
and communication: Recognition accuracy versus communication
rate”. Submitted to IEEE Trans. Mobile Comput. [Online]. Available:
https://arxiv.org/abs/2107.09621
[123] J. B. Kenney, “Dedicated short-range communications (DSRC) stan-
dards in the united states,” Proc. IEEE, vol. 99, no. 7, pp. 1162–1182,
Jul. 2011.
[124] P. Kumari, J. Choi, N. Gonz ´alez-Prelcic, and R. W. Heath, “IEEE
802.11ad-based radar: An approach to joint vehicular communication-
radar system,” IEEE Trans. Veh. Technol. , vol. 67, no. 4, pp. 3012–
3027, Apr. 2018.
[125] E. Grossi, M. Lops, L. Venturino, and A. Zappone, “Opportunistic radar
in IEEE 802.11ad networks,” IEEE Trans. Signal Process. , vol. 66,
no. 9, pp. 2441–2454, May 2018.
[126] H. Wymeersch, G. Seco-Granados, G. Destino, D. Dardari, and
F. Tufvesson, “5G mmwave positioning for vehicular networks,” IEEE
Wireless Commun., vol. 24, no. 6, pp. 80–86, Dec. 2017.
[127] M. Bic ˘a and V . Koivunen, “Radar waveform optimization for target
parameter estimation in cooperative radar-communications systems,”
IEEE Trans. Aerosp. Electron. Syst. , vol. 55, no. 5, pp. 2314–2326,
2019.
[128] C. Shi, F. Wang, M. Sellathurai, J. Zhou, and S. Salous, “Power
minimization-based robust OFDM radar waveform design for radar and
communication systems in coexistence,” IEEE Trans. Signal Process. ,
vol. 66, no. 5, pp. 1316–1330, 2018.
[129] R. Fu, S. Mulleti, T. Huang, Y . Liu, and Y . C. Eldar, “Hardware pro-
totype demonstration of a cognitive radar with sparse array antennas,”
Electron. Lett., vol. 56, pp. 1210–1212, Oct. 2020.
[130] S. Sodagari, A. Khawar, T. C. Clancy, and R. McGwier, “A projection
based approach for radar and telecommunication systems coexistence,”
in 2012 IEEE Global Communications Conference (GLOBECOM) ,
Dec. 2012, pp. 5010–5014.
[131] F. Liu and C. Masouros, “A tutorial on joint radar and communication
transmission for vehicular networks—Part I: Background and funda-
mentals,” IEEE Communications Letters , vol. 25, no. 2, pp. 322–326,
2021.

35
[132] A. Hassanien, M. G. Amin, Y . D. Zhang, and F. Ahmad, “Dual-function
radar-communications: Information embedding using sidelobe control
and waveform diversity,” IEEE Trans. Signal Process. , vol. 64, no. 8,
pp. 2168–2181, Apr. 2016.
[133] T. Huang, N. Shlezinger, X. Xu, Y . Liu, and Y . C. Eldar, “MAJoRCom:
A dual-function radar communication system using index modulation,”
IEEE Trans. Signal Process. , vol. 68, pp. 3423–3438, 2020.
[134] D. Ma, N. Shlezinger, T. Huang, Y . Shavit, M. Namer, Y . Liu, and Y . C.
Eldar, “Spatial modulation for joint radar-communications systems:
Design, analysis, and hardware prototype,” IEEE Trans. Veh. Technol.,
vol. 70, no. 3, pp. 2283–2298, 2021.
[135] D. Ma, N. Shlezinger, T. Huang, Y . Liu, and Y . C. Eldar. (2021)
“FRaC: FMCW-based joint radar-communications system via index
modulation”. Submitted to IEEE Trans. Signa Process. [Online].
Available: https://arxiv.org/abs/2106.14671
[136] L. Chen, F. Liu, W. Wang, and C. Masouros, “Joint radar-
communication transmission: A generalized pareto optimization frame-
work,” IEEE Trans. Signal Process. , vol. 69, pp. 2752–2765, 2021.
[137] A. Hassanien, M. G. Amin, Y . D. Zhang, F. Ahmad, and B. Himed,
“Non-coherent PSK-based dual-function radar-communication sys-
tems,” in Proc. IEEE Radar Conf. (RadarConf) , May 2016, pp. 1–6.
[138] E. BouDaher, A. Hassanien, E. Aboutanios, and M. G. Amin, “Towards
a dual-function MIMO radar-communication system,” in Proc. IEEE
Radar Conf. (RadarConf) , May 2016, pp. 1–6.
[139] T. Huang, N. Shlezinger, X. Xu, D. Ma, Y . Liu, and Y . C. Eldar, “Multi-
carrier agile phased array radar,” IEEE Trans. Signal Process., vol. 68,
pp. 5706–5721, 2020.
[140] S. K. Mohammed and E. G. Larsson, “Per-antenna constant envelope
precoding for large multi-user MIMO systems,” IEEE Trans. Commun.,
vol. 61, no. 3, pp. 1059–1071, 2013.
[141] N. Nartasilpa, A. Salim, D. Tuninetti, and N. Devroye, “Commu-
nications system performance and design in the presence of radar
interference,” IEEE Trans. Commun. , vol. 66, no. 9, pp. 4170–4185,
Sept. 2018.
[142] S. Shahi, D. Tuninetti, and N. Devroye, “On the capacity of the AWGN
channel with additive radar interference,” IEEE Trans. Commun. ,
vol. 66, no. 2, pp. 629–643, 2018.
[143] L. Zheng, M. Lops, and X. Wang, “Adaptive interference removal for
uncoordinated radar/communication coexistence,” IEEE J. Sel. Topics
Signal Process., vol. 12, no. 1, pp. 45–60, Feb. 2018.
[144] M. L. Rahman, J. A. Zhang, X. Huang, Y . J. Guo, and R. W. Heath,
“Framework for a perceptive mobile network using joint communica-
tion and radar sensing,” IEEE Trans. Aerosp. Electron. Syst. , vol. 56,
no. 3, pp. 1926–1941, 2020.
[145] Z. Ni, J. A. Zhang, X. Huang, K. Yang, and J. Yuan, “Uplink sensing
in perceptive mobile networks with asynchronous transceivers,” IEEE
Trans. Signal Process., vol. 69, pp. 1287–1300, 2021.
[146] X. Lin, J. Li, R. Baldemair, J.-F. T. Cheng, S. Parkvall, D. C. Larsson,
H. Koorapaty, M. Frenne, S. Falahati, A. Grovlen, and K. Werner, “5G
New Radio: Unveiling the essentials of the next generation wireless
access technology,” IEEE Commun. Standards Mag. , vol. 3, no. 3, pp.
30–37, 2019.
[147] A. Sabharwal, P. Schniter, D. Guo, D. W. Bliss, S. Rangarajan, and
R. Wichman, “In-band full-duplex wireless: Challenges and opportu-
nities,” IEEE J. Sel. Areas Commun. , vol. 32, no. 9, pp. 1637–1652,
2014.
[148] C. Baquero Barneto, T. Riihonen, M. Turunen, L. Anttila, M. Fleischer,
K. Stadius, J. Ryyn ¨anen, and M. Valkama, “Full-Duplex OFDM
Radar With LTE and 5G NR Waveforms: Challenges, solutions, and
measurements,” IEEE Trans. Microw. Theory Technol., vol. 67, no. 10,
pp. 4042–4054, 2019.
[149] Y . Shen, H. Wymeersch, and M. Z. Win, “Fundamental limits of
wideband localization— Part II: Cooperative networks,” IEEE Trans.
Inf. Theory, vol. 56, no. 10, pp. 4981–5000, 2010.
[150] M. Z. Win, A. Conti, S. Mazuelas, Y . Shen, W. M. Gifford, D. Dardari,
and M. Chiani, “Network localization and navigation via cooperation,”
IEEE Commun. Mag. , vol. 49, no. 5, pp. 56–62, 2011.
[151] N. Patwari, J. Ash, S. Kyperountas, A. Hero, R. Moses, and N. Cor-
real, “Locating the nodes: cooperative localization in wireless sensor
networks,” IEEE Signal Process. Mag., vol. 22, no. 4, pp. 54–69, 2005.
[152] I. Guvenc and C.-C. Chong, “A survey on TOA based wireless
localization and NLOS mitigation techniques,” IEEE Commun. Surveys
Tuts., vol. 11, no. 3, pp. 107–124, 2009.
[153] H. Godrich, A. M. Haimovich, and R. S. Blum, “Target localization
accuracy gain in MIMO radar-based systems,” IEEE Trans. Inf. Theory,
vol. 56, no. 6, pp. 2783–2803, 2010.
[154] M. Peng, C. Wang, V . Lau, and H. V . Poor, “Fronthaul-constrained
cloud radio access networks: Insights and challenges,” IEEE Wireless
Commun., vol. 22, no. 2, pp. 152–160, 2015.
[155] M. Peng, Y . Sun, X. Li, Z. Mao, and C. Wang, “Recent advances in
cloud radio access networks: System architectures, key techniques, and
open issues,” IEEE Commun. Surveys Tuts. , vol. 18, no. 3, pp. 2282–
2308, 2016.
[156] J. Wu, Z. Zhang, Y . Hong, and Y . Wen, “Cloud radio access network
(C-RAN): A primer,” IEEE Network, vol. 29, no. 1, pp. 35–41, 2015.
[157] L. Wang, K.-K. Wong, M. Elkashlan, A. Nallanathan, and S. Lam-
botharan, “Secrecy and energy efﬁciency in massive MIMO aided
heterogeneous C-RAN: A new look at interference,”IEEE J. Sel. Topics
Signal Process., vol. 10, no. 8, pp. 1375–1389, 2016.
[158] X. Li, D. Zhang, Q. Lv, J. Xiong, S. Li, Y . Zhang, and H. Mei,
“Indotrack: Device-Free Indoor Human Tracking with Commodity Wi-
Fi,” Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. , vol. 1,
no. 3, Sep. 2017. [Online]. Available: https://doi.org/10.1145/3130940
[159] D. Cohen, S. Tsiper, and Y . C. Eldar, “Analog-to-digital cognitive
radio: Sampling, detection, and hardware,” IEEE Signal Process. Mag.,
vol. 35, no. 1, pp. 137–166, 2018.
[160] T. Yucek and H. Arslan, “A survey of spectrum sensing algorithms for
cognitive radio applications,” IEEE Commun. Surveys Tuts. , vol. 11,
no. 1, pp. 116–130, 2009.
[161] Y .-C. Liang, Y . Zeng, E. C. Peh, and A. T. Hoang, “Sensing-throughput
tradeoff for cognitive radio networks,” IEEE Trans. Wireless Commun.,
vol. 7, no. 4, pp. 1326–1337, 2008.
[162] J. Wang, Z. Lan, C. woo Pyo, T. Baykas, C. sean Sum, M. Rahman,
J. Gao, R. Funada, F. Kojima, H. Harada, and S. Kato, “Beam codebook
based beamforming protocol for multi-Gbps millimeter-wave WPAN
systems,” IEEE J. Sel. Areas Commun. , vol. 27, no. 8, pp. 1390–1399,
2009.
[163] A. Alkhateeb, O. El Ayach, G. Leus, and R. W. Heath, “Channel
estimation and hybrid precoding for millimeter wave cellular systems,”
IEEE J. Sel. Topics Signal Process. , vol. 8, no. 5, pp. 831–846, 2014.
[164] C. Aydogdu, F. Liu, C. Masouros, H. Wymeersch, and M. Rydstr ¨om,
“Distributed radar-aided vehicle-to-vehicle communication,” in 2020
IEEE Radar Conference (RadarConf20) , 2020, pp. 1–6.
[165] N. Gonz ´alez-Prelcic, R. M ´endez-Rial, and R. W. Heath, “Radar aided
beam alignment in mmWave V2I communications supporting antenna
diversity,” in 2016 Information Theory and Applications Workshop
(ITA), 2016, pp. 1–7.
[166] A. Ali, N. Gonzalez-Prelcic, R. W. Heath, and A. Ghosh, “Leverag-
ing sensing at the infrastructure for mmwave communication,” IEEE
Commun. Mag., vol. 58, no. 7, pp. 84–89, 2020.
[167] J. Zhang, Y . Huang, J. Wang, X. You, and C. Masouros, “Intelligent
interactive beam training for millimeter wave communications,” IEEE
Trans. Wireless Commun., vol. 20, no. 3, pp. 2034–2048, 2021.
[168] D. Zhu, J. Choi, and R. W. Heath, “Auxiliary beam pair enabled AoD
and AoA estimation in closed-loop large-scale millimeter-wave mimo
systems,” IEEE Trans. Wireless Commun. , vol. 16, no. 7, pp. 4770–
4785, 2017.
[169] F. Liu and C. Masouros, “A tutorial on joint radar and communication
transmission for vehicular networks—Part II: State of the art and
challenges ahead,” IEEE Commun. Lett. , vol. 25, no. 2, pp. 327–331,
2021.
[170] S. Kang, S. Choi, G. Lee, and S. Bahk, “A dual-connection based
handover scheme for ultra-dense millimeter-wave cellular networks,” in
2019 IEEE Global Communications Conference (GLOBECOM) , 2019,
pp. 1–6.
[171] J. Huang, Z. Fei, T. Wang, X. Wang, F. Liu, H. Zhou, J. A. Zhang,
and G. Wei, “V2X-communication assisted interference minimization
for automotive radars,” China Commun., vol. 16, no. 10, pp. 100–111,
2019.
[172] C. Aydogdu, M. F. Keskin, N. Garcia, H. Wymeersch, and D. W.
Bliss, “RadChat: Spectrum sharing for automotive radar interference
mitigation,” IEEE Trans. Intell. Transp. Syst. , vol. 22, no. 1, pp. 416–
429, 2021.
[173] J. Zhang and C. Masouros, “Beam drift in millimeter wave links:
Beamwidth tradeoffs and learning based optimization,” IEEE Trans.
Commun., pp. 1–1, 2021.
[174] G. R. Muns, K. V . Mishra, C. B. Guerra, Y . C. Eldar, and K. R.
Chowdhury, “Beam alignment and tracking for autonomous vehicular
communication using IEEE 802.11ad-based radar,” inIEEE INFOCOM
2019 - IEEE Conference on Computer Communications Workshops
(INFOCOM WKSHPS), 2019, pp. 535–540.

36
[175] F. Liu and C. Masouros, “Joint localization and predictive beamform-
ing in vehicular networks: Power allocation beyond water-ﬁlling,” in
ICASSP 2021 - 2021 IEEE International Conference on Acoustics,
Speech and Signal Processing (ICASSP) , 2021, pp. 8393–8397.
[176] J. Massey, “An introduction to contemporary cryptology,” Proceedings
of the IEEE , vol. 76, no. 5, pp. 533–549, 1988.
[177] N. Su, F. Liu, and C. Masouros, “Secure radar-communication systems
with malicious targets: Integrating radar, communications and jamming
functionalities,” IEEE Trans. Wireless Commun., vol. 20, no. 1, pp. 83–
95, 2021.
[178] A. Dimas, M. A. Clark, B. Li, K. Psounis, and A. P. Petropulu,
“On radar privacy in shared spectrum scenarios,” in ICASSP 2019 -
2019 IEEE International Conference on Acoustics, Speech and Signal
Processing (ICASSP), 2019, pp. 7790–7794.
[179] A. Dimas, B. Li, M. Clark, K. Psounis, and A. Petropulu, “Spectrum
sharing between radar and communication systems: Can the privacy of
the radar be preserved?” in 2017 51st Asilomar Conference on Signals,
Systems, and Computers , 2017, pp. 1285–1289.
[180] A. A. Hilli, A. Petropulu, and K. Psounis, “Mimo radar privacy
protection through gradient enforcement in shared spectrum scenarios,”
in 2019 IEEE International Symposium on Dynamic Spectrum Access
Networks (DySPAN), 2019, pp. 1–5.
[181] Y . Liang, H. V . Poor, and S. Shamai, “Secure communication over
fading channels,” IEEE Trans. Inf. Theory , vol. 54, no. 6, pp. 2470–
2492, 2008.
[182] N. Su, F. Liu, Z. Wei, Y . Liu, and C. Masouros, “Secure dual-
functional radar-communication transmission: Exploiting interference
for resilience against target eavesdropping,” submitted to IEEE Trans.
Wireless Commun.
[183] Z. Wei, F. Liu, N. Su, and P. Athina, “Towards multi-functional 6g
wireless networks: Integrating sensing, communication and security,”
submitted to IEEE Wireless Comm. Mag.
[184] K. B. Letaief, W. Chen, Y . Shi, J. Zhang, and Y .-J. A. Zhang, “The
roadmap to 6g: Ai empowered wireless networks,” IEEE Communica-
tions Magazine, vol. 57, no. 8, pp. 84–90, 2019.
[185] Y . Mao, C. You, J. Zhang, K. Huang, and K. B. Letaief, “A survey
on mobile edge computing: The communication perspective,” IEEE
Communications Surveys Tutorials , vol. 19, no. 4, pp. 2322–2358,
2017.
[186] F. Wang, J. Xu, and S. Cui, “Optimal energy allocation and task of-
ﬂoading policy for wireless powered mobile edge computing systems,”
IEEE Trans. Wireless Commun. , vol. 19, no. 4, pp. 2443–2459, Apr.
2020.
[187] G. Zhu, D. Liu, Y . Du, C. You, J. Zhang, and K. Huang, “Toward
an intelligent edge: Wireless communication meets machine learning,”
IEEE Communications Magazine , vol. 58, no. 1, pp. 19–25, 2020.
[188] T. Gafni, N. Shlezinger, K. Cohen, Y . C. Eldar, and H. V .
Poor. (2021) “Federated learning: A signal processing perspective”.
Submitted to IEEE Signal Process. Mag. [Online]. Available:
https://arxiv.org/abs/2103.17150
[189] T. Zhang, S. Wang, G. Li, F. Liu, G. Zhu, and R. Wang.
(2021) “Accelerating edge intelligence via integrated sensing and
communication”. Submitted to IEEE Trans. Veh. Technol . [Online].
Available: https://arxiv.org/abs/2107.09574
[190] G. Zhu, J. Xu, and K. Huang, “Over-the-air computing for wireless
data aggregation in massive iot,” CoRR, vol. abs/2009.02181, 2020.
[Online]. Available: https://arxiv.org/abs/2009.02181
[191] X. Cao, G. Zhu, J. Xu, Z. Wang, and S. Cui, “Optimized power
control design for over-the-air federated edge learning,” CoRR, vol.
abs/2106.09316, 2021. [Online]. Available: https://arxiv.org/abs/2106.
09316
[192] X. Cao, G. Zhu, J. Xu, and K. Huang, “Optimized power control for
over-the-air computation in fading channels,” IEEE Trans. Wireless
Commun., vol. 19, no. 11, pp. 7498–7513, 2020.
[193] ——, “Cooperative interference management for over-the-air compu-
tation networks,” IEEE Trans. Wireless Commun. , vol. 20, no. 4, pp.
2634–2651, 2021.
[194] T. Sery, N. Shlezinger, K. Cohen, and Y . C. Eldar, “Over-the-air feder-
ated learning from heterogeneous data,” IEEE Trans. Signal Process. ,
vol. 69, pp. 3796–3811, 2021.
[195] Q. Wu, S. Zhang, B. Zheng, C. You, and R. Zhang, “Intelligent
reﬂecting surface-aided wireless communications: A tutorial,” IEEE
Trans. Commun., vol. 69, no. 5, pp. 3313–3351, 2021.
[196] M. Di Renzo, A. Zappone, M. Debbah, M.-S. Alouini, C. Yuen,
J. de Rosny, and S. Tretyakov, “Smart radio environments empowered
by reconﬁgurable intelligent surfaces: How it works, state of research,
and the road ahead,” IEEE J. Sel. Areas Commun. , vol. 38, no. 11, pp.
2450–2525, 2020.
[197] Q. Wu, J. Xu, Y . Zeng, D. W. K. Ng, N. Al-Dhahir, R. Schober, and
A. L. Swindlehurst, “A comprehensive overview on 5G-and-beyond
networks with uavs: From communications to sensing and intelligence,”
IEEE J. Sel. Areas Commun. , pp. 1–1, 2021.
[198] M. Giordani and M. Zorzi, “Non-terrestrial networks in the 6G era:
Challenges and opportunities,” IEEE Network, vol. 35, no. 2, pp. 244–
251, 2021.
[199] O. Kodheli, E. Lagunas, N. Maturo, S. K. Sharma, B. Shankar, J. F. M.
Montoya, J. C. M. Duncan, D. Spano, S. Chatzinotas, S. Kisseleff,
J. Querol, L. Lei, T. X. Vu, and G. Goussetis, “Satellite communications
in the new space era: A survey and future challenges,” IEEE Commun.
Surveys Tuts., vol. 23, no. 1, pp. 70–109, 2021.
[200] T. S. Rappaport, Y . Xing, O. Kanhere, S. Ju, A. Madanayake, S. Man-
dal, A. Alkhateeb, and G. C. Trichopoulos, “Wireless communications
and applications above 100 GHz: Opportunities and challenges for 6G
and beyond,” IEEE Access, vol. 7, pp. 78 729–78 757, 2019.
[201] I. F. Akyildiz, J. M. Jornet, and C. Han, “TeraNets: Ultra-broadband
communication networks in the terahertz band,” IEEE Wireless Com-
mun., vol. 21, no. 4, pp. 130–135, 2014.
[202] Y . Lu, X. Huang, K. Zhang, S. Maharjan, and Y . Zhang, “Low-latency
federated learning and blockchain for edge association in digital twin
empowered 6G networks,” IEEE Trans. Ind. Informat. , vol. 17, no. 7,
pp. 5098–5107, 2021.
[203] H. X. Nguyen, R. Trestian, D. To, and M. Tatipamula, “Digital twin
for 5G and beyond,” IEEE Commun. Mag. , vol. 59, no. 2, pp. 10–15,
2021.
[204] R. Hadani, S. Rakib, M. Tsatsanis, A. Monk, A. J. Goldsmith,
A. F. Molisch, and R. Calderbank, “Orthogonal time frequency space
modulation,” in 2017 IEEE Wireless Communications and Networking
Conference (WCNC), 2017, pp. 1–6.
[205] L. Gaudio, M. Kobayashi, G. Caire, and G. Colavolpe, “On the
effectiveness of OTFS for joint radar parameter estimation and com-
munication,” IEEE Trans. Wireless Commun., vol. 19, no. 9, pp. 5951–
5965, 2020.
[206] W. Yuan, Z. Wei, J. Yuan, and D. W. K. Ng, “A simple variational bayes
detector for orthogonal time frequency space (OTFS) modulation,”
IEEE Trans. Veh. Technol., vol. 69, no. 7, pp. 7976–7980, 2020.