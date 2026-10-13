---
title: "SeCo4: Co-Design of Sensing, Communication, and Computing for Intelligent Control in Industrial Cyber-Physical Systems"
zotero_key: "RFIP7ECI"
pdf_key: "4DDGZBQW"
doi: "10.1109/JSAC.2025.3574623"
collection: "ISAC"
source: "Zotero PDF (pypdf extraction)"
page_mapping: unverified
---

# SeCo4: Co-Design of Sensing, Communication, and Computing for Intelligent Control in Industrial Cyber-Physical Systems — Fulltext

> 由 Zotero PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射），需页码核验时请打开原始 PDF。

---

3362 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
SeCo4: Co-Design of Sensing, Communication, and
Computing for Intelligent Control in Industrial
Cyber-Physical Systems
Qinqin Tang
 , Member, IEEE, Yutian Yang
 , Jiayi Cui, Renchao Xie
 , Senior Member, IEEE,
Tao Huang
 , Senior Member, IEEE, Tianjiao Chen
 , Ran Zhang
 , Member, IEEE,
and Zehui Xiong
 , Member, IEEE
Abstract—Industrial Cyber-Physical Systems (CPS) have made
signiﬁcant strides in recent years, driving the future of man-
ufacturing. However, for further advancement in Cloud-Fog
Automation (CFA), several challenges remain: rigid sensor
sampling, inﬂexible communication conﬁgurations, insufﬁcient
coordination between cloud and fog resources, and a lack of
integration between sensing, communication, and computing for
effective control. To address these issues, this article presents
SeCo4, an intelligent control framework for the co-design of
sensing, communication, and computing in industrial CPS. The
SeCo4 optimization problem is analyzed and divided into two
sub-problems: a multi-controller cloud resource competition
problem, formulated with a combinatorial auction to enable
multi-controller competition for additional cloud resources and
improve control performance; and a joint resource optimization
problem for sensing, communication, and computing, modeled
using a Mixed Integer Programming (MIP) problem to minimize
control costs. Given the interdependence of these sub-problems,
a hierarchical solution based on the online matching mechanism
and the heuristic approach is developed to iteratively ﬁnd the
optimal solution. Finally, extensive simulations demonstrate the
effectiveness and superiority of the proposed approach.
Index Terms —Industrial cyber-physical systems, cloud-fog
automation, co-design approach, hierarchical framework.
Received 30 September 2024; revised 17 January 2025; accepted 28 Febru-
ary 2025. Date of publication 28 May 2025; date of current version 14 October
2025. This work was supported in part by the National Natural Science
Foundation of China under Grant 92367104 and in part by the Open
Research Fund from Guangdong Laboratory of Artiﬁcial Intelligence and
Digital Economy (SZ) under Grant GML-KF-24-25. (Corresponding author:
Renchao Xie.)
Qinqin Tang is with the State Key Laboratory of Networking and
Switching Technology, Beijing University of Posts and Telecommunications,
Beijing 100876, China, and also with Guangdong Laboratory of Artiﬁcial
Intelligence and Digital Economy (SZ), Shenzhen 518132, China (e-mail:
qqtang@bupt.edu.cn).
Yutian Yang and Jiayi Cui are with the State Key Laboratory of Networking
and Switching Technology, Beijing University of Posts and Telecom-
munications, Beijing 100876, China (e-mail: yangyt275@bupt.edu.cn;
JiayiCui@bupt.edu.cn).
Renchao Xie, Tao Huang, and Ran Zhang are with the State Key Laboratory
of Networking and Switching Technology, Beijing University of Posts and
Telecommunications, Beijing 100876, China, and also with Purple Mountain
Laboratories, Nanjing 211111, China (e-mail: Renchao xie@bupt.edu.cn;
htao@bupt.edu.cn; zhangran@bupt.edu.cn).
Tianjiao Chen is with China Mobile Research Institute, Beijing 100053,
China (e-mail: chentianjiao@chinamobile.com).
Zehui Xiong is with the Pillar of Information Systems Technology and
Design, Singapore University of Technology and Design, Singapore 639798
(e-mail: zehuixiong@sutd.edu.sg).
Digital Object Identiﬁer 10.1109/JSAC.2025.3574623
I. I NTRODUCTION
T
HE digital transformation driven by Industry 4.0 is
profoundly reshaping industrial systems, largely due to
signiﬁcant advancements in industrial Cyber-Physical Systems
(CPS) [1], [2], [3]. These advancements empower smart fac-
tory innovations to deliver efﬁcient and responsive services
to customers like never before, accelerating the adoption
of systems such as predictive maintenance, big data analyt-
ics, self-optimization, and self-healing. Such an integrated
approach boosts productivity, reduces unplanned downtime,
and signiﬁcantly cuts revenue losses, fostering a culture of
continuous improvement and innovation. Consequently, this
transformation is evident across all industrial sectors, driving
the future of manufacturing.
A key advantage of industrial CPS is full automation [4].
Currently, industrial automation relies on the traditional pyra-
mid architecture deﬁned by the ISA-95 model [5]. However,
advancements in next-generation wireless technologies, Artiﬁ-
cial Intelligence (AI), and cloud/fog computing are prompting
a shift from this conventional model toward a new paradigm:
Cloud-Fog Automation (CFA) [6], [7], [8]. This paradigm inte-
grates advanced control algorithms and machine intelligence
deeply into the control loop, leveraging a more powerful,
cost-effective, and ﬂexible computing infrastructure. As more
organizations adopt this paradigm, it is expected to drive
unprecedented levels of efﬁciency and productivity in the
industrial sector. Given such advantages of CFA, it has gar-
nered signiﬁcant attention from both industry and academia,
particularly in areas like network conﬁguration [1], wireless
control [7], and predictive maintenance [9].
In CFA systems, industrial applications demand real-time
and highly reliable control, reliant on efﬁcient information
sensing, communication, and computing decision-making [10],
[11], [12]. During the sensing stage, multi-functional sensors
gather data; the communication stage transmits this infor-
mation to the controller and relays control commands to
the sensors; and the computing stage processes and analyzes
the data to generate control commands. However, several
challenges remain in achieving accurate and reliable system
control throughout this process:
i) Highly ﬂexible sensing. Industrial channels and controller
loads change over time. Traditional ﬁxed-frequency sensing
is not conducive to efﬁcient transmission and analysis of
0733-8716 © 2025 IEEE. All rights reserved, including rights for text and data mining, and training of artiﬁcial intelligence and
similar technologies. Personal use is permitted, but republication/redistribution requires IEEE permission.
See https://www.ieee.org/publications/rights/index.html for more information.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3363
information. It is valuable to dynamically adjust the sensing
rate according to the environment to provide efﬁcient services.
ii) Reliable and real-time communication. Wired control
networks can no longer meet the demands of CFA systems.
Therefore, it is essential to explore Ultra-Reliable Low-
Latency Communication (URLLC) technology for industrial
control and optimize the conﬁguration of limited communica-
tion resources in relation to the environment [13].
iii) Efﬁcient and accurate processing.The information trans-
mitted to the controller must be processed to generate control
decisions. Computing resources distributed across fog and
cloud. The intelligent evolution of CFA systems allows for
the deployment of various AI models for efﬁcient analysis.
Distributed resources and heterogeneous AI models need to
be coordinated to obtain accurate control decisions [14], [15].
iv) Joint optimization of resources. Current advances in
sensing, communication, computing, and control often occur
in isolation, limiting the ability address complex real-world
scenarios. While some research has explored the joint opti-
mization of sensing and communication [16], as well as
communication and computing [17], these efforts tackle impor-
tant challenges in industrial automation. However, they do not
encompass a comprehensive integration of sensing, communi-
cation, and computing in CFA environments, which is crucial
for efﬁcient and cost-effective industrial control.
Therefore, in line with the development trend of CFA,
this article investigates the co-design problem of sensing,
communication, and computing for intelligent control in indus-
trial CPS to optimize the control performance of industrial
CPS. Speciﬁcally, we summarize our main contributions as
follows.
• We establish an intelligent Control framework SeCo4
with Co-design of Sensing, Communication and
Computing for CFA in industrial CPS. In this framework,
we introduce the SeCo4 co-design optimization problem,
which aims to minimize the system’s control overhead
by optimizing the sampling rate, power allocation, task
ofﬂoading, and resource competition.
• Considering the complexity of the co-design optimization
problem, we further decompose it into a multi-controller
cloud resource competition problem and a joint sensing,
communication, and computing resource allocation prob-
lem. In the multi-controller cloud resource competition
problem, multiple controllers compete for cloud resources
to achieve expansion of their limited local fog resources.
An online auction-based approach is adopted to describe
the competition process, and a Vickrey-Clarke-Groves
(VCG)-based matching algorithm is developed to obtain
the optimal solution. The joint sensing, communication,
and computing resource allocation problem is modeled as
a Mixed Integer Programming(MIP) problem to reduce
the control cost. A heuristic-based Differential Evolution
(DE) approach is proposed to obtain a highly adaptable
optimal joint resource optimization decision.
• A hierarchical solution is constructed iteratively addresses
the co-design optimization problem. The performance
of our proposed scheme is evaluated through extensive
simulations. Numerical results demonstrate the effective-
ness and superiority of our proposal compared to the
benchmark schemes in optimizing control performance.
The remainder of this article is organized as follows. In
Section II, we explore related studies. Section III provides an
in-depth discussion of the SeCo4 model design, and Section IV
presents the optimization problem associated with SeCo4. To
address this co-design optimization challenge, we propose a
hierarchical solution that integrates online auction and DE
approaches, which is detailed in Section V. Section VI show-
cases the numerical results obtained from our experiments, and
we conclude the article in Section VII.
II. R ELATED WORK
The elasticity, ﬂexibility, scalability, and synergy of cloud
and fog computing enhance the efﬁcient data processing of
industrial CPS, leading to improved response times and ful-
ﬁlling the real-time and high-reliability demands of industrial
applications. Numerous studies are investigating the integra-
tion of cloud and fog computing technologies in industrial
environments to enable more precise control operations. For
instance, Zhou et al. in [18] presented a reliable algo-
rithm for prioritizing and scheduling workﬂow applications
on cyber-physical cloud systems, which assigns a maximum
frequency to each task and dynamically allocates resources
accordingly. Niu and Wang in [19] developed a scheduling
optimization algorithm aimed at enhancing system efﬁciency
in big data-driven CPS on cloud platforms, proposing a task
scheduling solution for large-scale factory integration within a
cloud-edge collaborative computing framework. Additionally,
Asgarnezhad in [20] introduced a service placement solution in
CPS that leverages the Moth Flame Optimization (MFO) meta-
heuristic algorithm, focusing on the geographical distribution
of fog nodes to achieve high energy efﬁciency.
The traditional hierarchical pyramid architecture of indus-
trial automation systems is being replaced by a CFA
architecture designed to create a highly ﬂexible and scalable
infrastructure. This cloud-fog automation vision, ﬁrst concep-
tualized in [6], has garnered signiﬁcant attention. Jin et al. in
[1] introduced a cloud-fog automation paradigm characterized
by deterministic connectivity, interconnected intelligence, and
network computing, aligning with the Industry 4.0 vision. Lyu
et al. in [7] proposed a control-driven, delay-aware wireless
control framework for BB systems to address time delays and
instability factors arising in cloud-fog automation scenarios.
Additionally, Deivard and Johansson in [9] developed a novel
diagnostic method for time-critical control systems within
cloud-fog automation, aimed at evaluating the performance of
distributed control systems in these environments.
In the Fifth Generation (5G) mobile network era, the
complexity and diversity of data have driven industrial CPS
to integrate previously siloed resources such as sensing, com-
munication, and computing, enabling faster data transmission
and processing for precise control and optimized operations. In
[21], Meng et al. developed an analytical model for a closed-
loop industrial system with coupled communication, sensing,
and control, achieving coordination between communication
resource allocation and control methods. He et al. in [22]
introduced a three-layer system framework to provide reli-
able control for speciﬁc tasks and collaborative control for
distributed devices using integrated resources. Ji et al. in [23]
proposed an intelligent edge sensing and control collaboration
framework using multiple graph convolutional networks to
approximate optimal sensing and control coupling conditions.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3364 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
TABLE I
LIST OF NOTATIONS
Previous studies have partially optimized resources across
sensing, communication, computing, and control. However,
the co-design of sensing, communication, and computing in
industrial CPS for intelligent control remains underexplored.
To bridge this gap, this article propose a novel intelligent
control framework that jointly optimizes control task schedul-
ing and multi-dimensional resources, signiﬁcantly enhancing
overall control system performance.
III. S YSTEM DESCRIPTION
In this section, we give a broad overview of the SeCo4 sys-
tem model under consideration in our research. The deﬁnitions
of the main notations used in this article are listed in Table I.
A. SeCo4 System
1) System Model: As illustrated in Fig. 1, we focus on
a SeCo4 system, which comprises a sensing subsystem,
a communication subsystem, a fog computing subsystem,
and a cloud computing subsystem. The sensing subsystem
features multi-functional sensors, with sensing information
taking the form of images, videos, audio, and sporadic
small data. The communication subsystem facilitates wireless
communication between sensors and controllers, as well as
wired communication between controllers and the cloud, han-
dling the transmission of information and control commands.
The fog and cloud computing subsystems consist of dis-
tributed resources responsible for processing and analyzing the
Fig. 1. Illustration of the SeCo4 system.
collected data. Ultimately, the sensing, communication, com-
puting, and control ﬂows are interconnected through the SeCo4
system. Denote N ={1, 2,...,N } as the set of controllers,
each responsible for a distinct control area. Within each area,
numerous sensors collect diverse industrial data to accomplish
various industrial tasks. Let Kn ={1, 2,...,K n} represent
the set of industrial tasks under controller n ∈ N. For an
industrial task kn∈K n,Jn,k ={1, 2,··· ,Jn,k} denotes the
set of industrial sensors involved in that task. Each industrial
task relies on a series of continuous control commands rather
than a single command. Deﬁne In,k ={1, 2,··· ,In,k} as the
index of continuous sampling times for task kn. The subtask
of industrial task kn in the i∈In,kth cycle can be expressed
as kin. Once sensors capture samples of the current industrial
site status(e.g., equipment production status), these samples
are sent to the controller. After computational analysis, the
control commands are relayed back to the industrial site. The
cloud-fog collaborative framework facilitates computational
analysis, allowing it to occur both in the cloud and at the
controller. The controller utilizes fog resources in the working
area for localized data analysis, while also competing for
public edge cloud and data center cloud resources to enhance
computing capacity for industrial tasks. The set of cloud
nodes is represented by M ={1, 2,...,M }. With the rapid
advancement of AI technology, industrial CPS for cloud-fog
automation are becoming increasingly intelligent, employing
various AI models for accurate data analysis. Within the
cloud-fog collaborative computing framework, two types of AI
models are deployed: compressed AI models in fog environ-
ments, which are optimized through weight pruning techniques
to reduce computational complexity while maintaining similar
inference accuracy, and uncompressed AI models in the cloud.
This approach enables different AI models to work together
to meet diverse computational and analytical needs.
2) Implementation Process: SeCo4 is an advanced frame-
work for industrial environments, enabling intelligent control
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3365
Fig. 2. Illustration of the SeCo4 implementation process.
of physical equipment through the integration of sensing,
computing, and communication. The data ﬂow in SeCo4
tightly integrates multi-dimensional resources across the sens-
ing, fog computing, and cloud computing layers, covering
data collection, transmission, processing, and execution, as
shown in Fig. 2. Sensors in the sensing layer capture diverse
data(e.g., images, videos, audio) and wirelessly transmit it to
the fog computing layer for task generation and processing.
During transmission, data is abstracted into constraints such as
delay, reliability, and rate to ensure seamless handling. When a
control task is triggered, the fog computing layer leverages its
low latency to access local data and execute real-time control,
while the cloud computing layer manages complex, large-
scale tasks beyond the fog’s capabilities. After processing,
the controller sends control commands to the sensing layer
to adjust the equipment, completing the data ﬂow cycle.
The data ﬂow in SeCo4 follows a sequential structure
due to its temporal and causal nature, with communication
acting as middleware between sensing and computing. In the
sensing stage, data collection involves various sensors with
different temporal and spatial distributions. Raw data from
sensors is transmitted through communication channels to
the fog and cloud computing layers for further processing.
In the computing stage, the data is processed to generate
real-time control decisions, which are then transmitted to the
physical equipment in the sensing layer through structured
communication commands. This hierarchical framework relies
on communication resources to seamlessly integrate the sens-
ing, fog computing, and cloud computing layers, ensuring the
smooth operation of the SeCo4 control feedback loop.
B. Communication and Sensing Model
Given the time-varying nature of industrial CPS chan-
nels and controller loads, traditional ﬁxed-frequency sensing
is inefﬁcient for data transmission and analysis. Therefore,
this article adopts a ﬂexible sensing sampling approach that
dynamically adjusts the sampling rate based on channel con-
ditions and controller workload, aiming to enhance service
quality. Let ln,k,j be the raw sampling rate of sensor jn,k∈
Jn,k. During the period of task kin, the sampling rates of the
sensors can be represented asγin,k ={γin,k,j|j∈J n,k}, where
γin,k,j denotes the sampling rate of sensor jn,k. The sensing
delay istsam,in,k,j . Thus, the amount of data sensed by sensor jn,k
during the period of task kin can be expressed as:
Din,k,j =γin,k,j·ln,k,j·tsam,in,k,j. (1)
Considering that the wired control network can no longer
meet the requirements of the CFA, this work considers cen-
tralized wireless transmission to send the data to the controller
after the sensor completes data sensing. After the sensor
completes data sensing, it transmits the data to the controller
through centralized wireless transmission. Orthogonal Fre-
quency Division Multiplexing Access (OFDMA) modulation
is used in the uplink transmission, to allocate different band-
widths to different subtasks, thereby transmitting data through
multiple paths. The transmission distance between sensor jn,k
and its corresponding controller n is denoted as dn,k,j, with
a transmission signal frequency of fn,k,j. The free space path
loss for this data transmission is given by:
PLn,k,j =
(4π·dn,k,j·fn,k,j
c
)2
, (2)
where c is the speed of light.
Assuming that all sensors and the controller use the same
antenna parameters, let the antenna transmit gain be Gtg and
the receive gain be Grg. During the period of task kin, the
transmission power of sensors can be represented as ptpn,k =
{ptpn,k,j|j∈J n,k}, where ptpn,k,j is the transmission power of
sensor jn,k. The received power at controller n from sensor
jn,k is given by:
prpn,k,j = ptpn,k,j·Gtg·GrgPLn,k,j . (3)
Let the Power Spectral Density (PSD) of the Additive White
Gaussian Noise (AWGN) during wireless transmission be
represented asN0. Data of subtask kin is transmitted through a
set of subcarriersW ={1, 2,...,W } between sensorjn,k and
its corresponding controller n. The bandwidth of subcarrier
w is Bwn,k,j. Therefore, the Signal-to-Noise Ratio (SNR) at
controller n from sensor jn,k can be expressed as [24]:
SNRn,k,j =
prpn,k,j
N0
∑
w∈WBwn,k,j. (4)
In industrial environments with high-density equipment,
signal transmission is affected not only by noise but also
by interference from other sensors. In these conditions, the
SNR is no longer sufﬁcient to assess transmission reliability.
Instead, the Signal-to-Interference plus Noise Ratio(SINR) is
used, which can be expressed as:
SINRn,k,j =
prpn,k,j∑
i∈Jn,k,i⁄=jprpn,k,i +N0∑w∈WBwn,k,j. (5)
Finally, the channel capacity of sensor jn,k to controller n
can be calculated using the Shannon theory, given by:
Cn,k,j =
∑
w∈W
Bwn,k,j log (1 + SINRn,k,j). (6)
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3366 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
Efﬁcient and real-time wireless communication is essential
for industrial CPS. It is challenging for sensors to collect long
data packets and transmit them to the controller for decision-
making, rendering the Shannon formula inapplicable for short
data packets. To cope with this issue, this work incorporates
URLLC technology, speciﬁcally designed to meet the high
reliability and low-latency demands of the industrial CPS.
Based on ﬁnite block length coding theory, the maximum
transmission rate for URLLC can be calculated as:
RURLLCn,k,j =Cn,k,j−
√
Vn,k,j
r Q−1(ϵn,k,j), (7)
Here, Vn,k,j = 1− 1(1+SINRn,k,j)2 represents channel disper-sion;ϵn,k,j denotes the transmission error probability resulting
from this dispersion; r refers to the codeword length; and
Q−1 is the inverse of the Q function, where Q(x) =
1
2π
∫∞
x exp
(
−u22)du.
Therefore, in the case of ﬁnite code length, the Bit Error
Rate(BER) can be estimated using the Q function to relate the
SINR and the BER. The BERn,k,j is given by:
BERn,k,j =Q
(√
2SINRn,k,j
)
. (8)
Considering the successful communication transmission as
communication satisfaction, the communication satisfaction
for sensor jn,k can be deﬁned as:
ρtransn,k,j = 1− BERn,k,j. (9)
In an actual industrial CPS, it is not necessary for all sensors
to complete sensing and transmission to accurately execute
control operations. For different sensors with varying sens-
ing value coefﬁcients ωn,k,j such that ∑j∈Jn,kωn,k,j = 1 ,the subtask sensor communication satisfaction for intelligent
control task kn can be expressed as:
ρtransn,k = ∑
j∈Jn,k
ωn,k,j·ρtransn,k,j. (10)
Then, during the period of task kin, the delay required for
sensorjn,k to complete data transmission can be expressed as:
ttrans,in,k,j = Din,k,jRURLLCn,k,j . (11)
For each period of intelligent control tasks, different sensors
have varying times to complete data collection and transmis-
sion, which must be aggregated at the controller. During the
period of task kin, the total delay for all sensors Jn,k to
complete data collection and transmit their data to controller
n for aggregation can be expressed as:
tagg,in,k = maxj∈Jn,k
(
tsam,in,k,j +ttrans,in,k,j
)
. (12)
C. Computing Model
Once the collected data reaches the controller, it must
be processed and analyzed to generate control commands.
Depending on the requirements of the control task, available
computing resources, and network transmission conditions, the
controller can choose to utilize either nearby fog resources or
more distant cloud resources for computation and analysis.
During task kin, the task ofﬂoading decision is represented as
oin,k ={oin,k,m|m∈M} , where oin,k,m ={0, 1}. Speciﬁ-
cally, oin,k,m = 1 indicates that task kin will be ofﬂoaded to
cloud node m for processing, while oin,k,m = 0 signiﬁes that
the task will be handled using local fog resources.
1) Computing Queue Model: For fog and cloud nodes,
tasks that have arrived but are yet to be executed are stored
in a commuting buffer, modeled as a computing queue that
follows a ﬁrst-in-ﬁrst-out (FIFO) structure [25]. Given that
fog resources are limited, each fog node maintains its own
computing queue. Let the arrival time of task kin at controller
n be denoted as tarr(kin). The queue length, representing the
amount of unprocessed data at fog node n at this time, can be
expressed as
Qfogn (tarr(kin)) =Qfogn (tarr(ki−1n ))
+ ˆQfogn (tarr(ki−1n ),t arr(kin))
−
(
tarr(kin)−tarr(ki−1n ))·ffogn , (13)
where ffogn denotes the fog processing rate of fog node n.
Additionally, ˆQfogn (tarr(ki−1n ),t arr(kin)) represents the com-
putational effort required at fog node n between tasks ki−1n
and task kin, which can be calculated as
ˆQfogn (tarr(ki−1n ),t arr(kin))
=
N∑
˜k∈Kn/{k},˜i∈In,˜k
D
˜i
n,˜k
·cn,k· 1
{
tarr(ki−1n )<t arr(˜k˜in)<t arr(kin)}. (14)
Here, Din,k =∑j∈Jn,kDin,k,j is the total amount of kin; cn,k
is the required computing resources (in CPU cycles) to process
one bit of taskkn; 1(·) is an indicator function that evaluates to
1 if thecase in parentheses is true, and 0 otherwise. Meanwhile,
tarr(˜k˜in) satisﬁes the following progressive relationship:
tarr(˜k˜in) =tarr(˜k˜i−1n ) +Qfogn (tarr(ki−1n ))ffogn
+tfpro,i−1n,k +ttrans,in,k . (15)
This progressive relationship ensures that the next task period
can only begin after the control command reaches the sensors.
Since the delay required for the control command to travel
from the controller to the sensors is negligible compared to
the sensing, transmission, and processing of the collected data,
it is disregarded in this article.
In cloud computing, the cloud computing layer typically
consists of large-scale data centers equipped with high-
performance servers, offering signiﬁcantly more abundant
computing resources compared to the resource-limited fog
computing layer. As a result, the controller can increase their
computing capacity by utilizing cloud resources, enabling
more efﬁcient and accurate analysis of intelligent control tasks
and enhancing the overall performance of advanced control
systems. We denotefcloudm as the total computing resources of
cloud node m. The computing resource competition decision
is represented as an ={an,m|m∈M} , where an,m = [0, 1]
indicates the proportion of computing resources of cloud node
m acquired by controller n through competition. Note that
for the case an,m = 0 , we have oin,k,m = 0 . If controller
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3367
n competes for the computing resources of cloud node m, a
cloud computing queue will be maintained at cloud node m.
The deﬁnition and evolution of this queue are analogous to
the relationships described in Eq.(13)–(15).
2) Computing Delay Model: In the considered system, the
delay required for the computational analysis of intelligent
control tasks primarily consists of three components: the
waiting delay in the computing queue, the execution delay
of the task, and the transmission delay to the computing
node(applicable only for cloud resources).
The queue delay of task kin at fog node n and cloud node
m can be calculated as follows:
tfque,in,k =
(
1−∑m∈Moin,k,m)Qfogn (tarr(kin))
ffogn , (16)
and
tcque,in,k = ∑
m∈M
oin,k,mQcloudm (tarr(kin))
an,mfcloudm . (17)
whereQcloudm (tarr(kin)) is the queue length of cloud node m
when task kin arrives, indicating the amount of unprocessed
data at that time.
The execution delay required for fog node n and cloud node
m to process task kin can be calculated as follows:
tfpro,in,k =
(
1−∑m∈Moin,k,m)·Din,k
ffogn , (18)
and
tcpro,in,k = ∑
m∈M
oin,k,m·Din,k·cn,k
an,mfcloudm . (19)
Data is transmitted between the controller and the cloud
node via wired communication. The transmission delay from
controller n to cloud node m can be expressed as:
tctra,in,k = ∑
m∈M
oin,k,m·Din,k
RCSn,m , (20)
where RCSn,m represents the available network link capacity
between controller n and cloud node m. Given that the amount
of data transmitted back from the cloud to the controller after
processing is minimal, the return transmission delay can be
disregarded in this analysis.
Therefore, the total computing delay of task kin can be
calculated as
tcomp,in,k =tfpro,in,k +tfque,in,k +tcpro,in,k +tcque,in,k +tctra,in,k . (21)
To ensure reliable control of intelligent control tasks, the
computing delay threshold tcthn,k and the computing delay
satisfaction ρcp,in,k are established for each period of task kn.
The satisfaction ρcp,in,k approaches 1 when the total computing
delay is close to 0, while it drops to 0 when the computing
delay exceeds tcthn,k. ρcp,in,k satisﬁes the following relationship:
ρcp,in,k =



ζ1·

1−
(
tcomp,in,k
tcthn,k
)2
 +ζ2, 0<t comp,in,k ≤tcthn,k
0, t comp,in,k >t cthn,k
(22)
whereζ1 andζ2 are weight factors, and we have ζ1 +ζ2 = 1.
Fig. 3. Illustration of the real-time wireless control model.
3) Computing Accuracy Model: The AI model is employed
to perform computational analysis on the control task, with the
accuracy of this analysis inﬂuenced by both the sampling rate
of the task and the type of AI model used. The relationship
between the accuracy of the AI model and the sampling rate
can be speciﬁed using the accuracy function g
(
γin,k,j·ln,k,j
)
[26], [27]. Given the differences in resources between cloud
and fog nodes, along with the high resource demands of AI
models, we consider two types of AI models: compressed
and uncompressed. The compressed AI model deployed on
the fog node has an accuracy expressed as hfogn , while the
uncompressed AI model deployed on the cloud node has a
higher accuracy represented ashcloudm , satisfying the inequality
0 < hfogn < hcloudm < 1. This work focuses on an efﬁ-
cient cloud-fog collaborative computing framework, enabling
precise control decisions through the seamless integration of
distributed resources and heterogeneous AI capabilities across
the cloud and fog computing layers.
Since the selection of the AI model(i.e., task ofﬂoading
decision) and the sampling rate are independent, the overall
computing accuracy satisfaction for task kin can be expressed
as:
ρacc,in,k = 1Jn,k· ∑j∈Jn,kωn,k,jg(γin,k,j·ln,k,j)
·
[(
1−
∑
m∈M
oin,k,m
)
hfogn + ∑
m∈M
oin,k,mhcloudm
]
.
(23)
Note that the model can be readily extended to cases when
other AI inference methods are adopted, since the accuracy
values with respect to sampling rates and AI model types are
obtained via practical experiments.
D. Control Model
After sampling the current equipment states and envi-
ronmental conditions, the sensors transmit the data to the
controller. The controller processes the information and sends
control commands to the CPS to update the equipment states
and transition to the next state. Let t ={1, 2,··· ,T} rep-
resent the index of sampling times in the control process.
Fig. 3 illustrates the real-time wireless control model. Each
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3368 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
continuous-time industrial equipment is governed by the fol-
lowing equation [28], [29]:
dx(t) = A x(t)dt + B u(t)dt +dn(t), (24)
where x(t) and u(t) are the equipment state vector and control
input vector, respectively; n(t) is the state disturbance caused
by AWGN with mean 0 and variance σn. Moreover, A and B
are some constant matrices of appropriate dimensions.
To obtain discrete time control model, we assume that tsp,in,k
represents the sample period between the task ki−1n and task
kin, which consists of the sensing and transmission delaytagg,in,k ,
the computing delay tcomp,in,k and an idle delay tidlen,k ,
tsp,in,k =tagg,in,k +tcomp,in,k +tidlen,k. (25)
Then, considering the integration of multi-dimensional
resources, including sensing, communication, and computing,
the competition and allocation of these resources in CPS
will impact the overall sample period, thereby inﬂuencing the
system’s state. Therefore, the discrete time control model of
task kin with the sensing delay, transmission delay and the
computing delay can obtain as:
xi+1n,k = Ωin,kxin,k + Φ0,in,kuin,k + Φ1,in,kui−1n,k + nin,k, (26)
Here, i = 1, 2,...,I n,k represents the sampling time index
in the control process, Ωin,k = eAtsp,in,k . Moreover, Φ0,in,k =∫tidlen,k
0 eAtdt, Φ1,in,k = ∫tsp,in,ktidlen,k eAtdt, and nin,k represents thedisturbance caused by the AWGN in the ith(i∈In,k) sampling
cycle.
We assume that ξin,k = (xi⊤n,kui−1n,k )⊤ is the generalized state,
then the control function can be rewritten as:
ξi+1n,k = Ωdξin,k + Φduin,k + ¯nin,k, (27)
where Ωd =
(
Ωin,k Φ1,in,k
0 0
)
, Φd =
(Φ0,in,k
I
)
, ¯nin,k =
( ni⊤n,k 0)⊤.
Considering the communication satisfaction, the computing
accuracy satisfaction, and the computing delay satisfaction, we
assume that µin,k = 1 represents the control is satisﬁed and
µin,k = 0 represents it is unsatisﬁed. Then, we have
Pr
{
µin,k = 1} =ρtransn,k ·ρacc,in,k ·ρcp,in,k,
Pr
{
µin,k = 0} = 1−ρtransn,k ·ρacc,in,k ·ρcp,in,k. (28)
Moreover, we assume that the state estimator is perfect, and
then a linear uin,k = Πξin,k is used, where Π is the control
gain. Then, the control function can be rewritten as [23]:
ξi+1n,k =
{
(Ωd + ΦdΠ) ξin,k + nin,k, a in,k = 1
Ωdξin,k + nin,k, a in,k = 0, (29)
According to the optimal control theory, the control per-
formance index of industrial CPS consists of the control cost
of task kin in each period i∈I n,k and the continuous state
of the control system. Therefore, considering sensing( γin,k),
communication(ptpn,k), computing(oin,k and an,m) and control
comprehensively, the performance of the control system is
evaluated by the mathematical expectation Jn,k of the sum of
the ﬁnal performance and the control performance. The control
performance is the control cost, which can be calculated as:
Jn,k = E

ξIn,k⊤n,k ΛξIn,kn,k +
In,k−1∑
i=0
(
ξi⊤n,kΛξin,k+ui⊤n,k∆uin,k
)


(30)
where Λ and ∆ are both diagonal matrices whose dimensions
are related to the matrix dimensions of the state variables,
which are the weights of the state and control in the system,
respectively.
IV. J OINT OPTIMIZATION OF SENSING , COMMUNICATION ,
COMPUTING , AND CONTROL
This section begins with an introduction to the SeCo4 opti-
mization problem, followed by a discussion on its decoupling.
A. Problem Statement
Unlike the traditional isolated approaches to sensing, com-
munication, computing, and control, this work presents a
uniﬁed, integrated framework for CFA in industrial CPS.
Building on the communication and sensing model, computing
model, and control model presented in Section III, this section
introduces and discusses the SeCo4 co-design optimization
problem. The controller aims to enhance the effectiveness of
intelligent control in industrial CPS through the co-design of
sensing, communication, and computing. Moreover, recogniz-
ing the constraints of local computing and AI capabilities,
the controller can opt to compete for cloud resources that
provide greater availability and improved AI capabilities at
a certain cost, thereby achieving more intelligent and efﬁcient
control. Thus, we deﬁne the control overhead function En
of controller n as the sum of the control cost Jn and the
economic cost Pn generated by competing cloud resources.
Consequently, the SeCo4 co-design optimization problem(P1)
can be formulated as follows:
(P1) : min
γn,ptpn,on,an
En =χnJn +Pn (31)
Here, γn ={γin,k|i∈I n,k,k ∈K n}, ptpn ={ptpn,k|k∈K n},
on ={oin,k|i∈I n,k,k∈K n}, and an ={an,m|m∈M} .χn
is a mapping parameter that relates control cost to overhead,
and for task kn. Moreover, Jn = ∑k∈KnJn,k, where Jn,k
is the control cost, which can be calculated using Eq.(30) in
Subsection III-D.
To minimize control overhead En, problem(P1) optimizes
cloud resource competitionan to balance task processing qual-
ity and economic cost Pn. Additionally, the joint optimization
of sensing, communication, and computing resources evaluates
control effectiveness through control cost Jn. Key factors
include control satisfaction µin,k and sample period tsp,in,k ,
withµin,k factoring in communication satisfaction, computing
accuracy satisfaction, and computing delay satisfaction, while
tsp,in,k covers sensing, communication, and computing delays.
The joint optimization from the two dimensions of Pn and
Jn ultimately achieves the optimization of En. Problem (P1)
involves minimizing a utility function with binary integer and
complex continuous variables, making direct abstraction and
solution challenging. To address this problem, we decompose
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3369
(P1) into two subproblems: a multi-controller cloud resource
competition problem (P2) and a joint sensing, communica-
tion, and computing resource allocation problem (P3) for
control performance optimization. Problem (P2) focuses on
optimizing the economic utility of the controller by adjusting
cloud resource competition an, while problem (P3) aims to
reduce control costs by optimizing the sensing sampling rate
γn, communication power allocation ptpn , and task ofﬂoading
on. According to the communication, sensing, computing,
and control models in Section III, cloud resource competition
must consider the controller’s intelligent task control, requiring
optimal decisions in sensing, communication, and computing.
Conversely, making these optimal decisions also depends on
understanding the available cloud resources. Therefore, we
ﬁnally consider iteratively obtaining the joint solution set of
problem (P2) and problem (P3).
B. Multi-Controller Cloud Resource Competition Problem
This section formulates the multi-controller cloud resource
competition problem (P2). We propose a mechanism based on
many-to-many combinatorial auctions to facilitate on-demand
matching of resources and tasks, drawing inspiration from
third-party auction platforms. To address the varying demands
from different controllers, the auction-driven matching system
operates in discrete time intervals of equal duration, denoted
as τ = {1, 2,··· , Γ}. During each round τ, cloud nodes
make matching decisions after receiving bids from controllers,
allowing each controller to submit alternative bids from the
set G. Each bid g ∈ G consists of the proportion of the
required cloud resources an,m(τ) and the reported valuation.
We deﬁne a tuple {agn,m(τ),P gn(τ)} for the gth bid, where
agn,m(τ) represents the computing resource ratio for the gth bid
from controller n for the speciﬁed cloud node m, and Pgn(τ)
is the valuation report. At the end of each round τ, the cloud
node calculates the pricing decision and announces the match-
ing results. The variable zgn(τ) ∈ {0, 1} indicates whether
controller n successfully obtains the requested resources, with
zgn(τ) = 1 signifying a successful match where the controller
acquires the corresponding resources by paying Pgn(τ) to the
cloud node.
1) Ofﬂine Matching Problem: For such an auction, we
formulate an ofﬂine social welfare optimization problem for
auction-driven matching using the VCG mechanism, aiming to
establish an optimal matching strategy that adapts to diverse
needs throughout the system’s lifecycle [30]. Assuming that
all bids are legitimate, the problem can be represented as the
following binary integer programming model:
(P2) : max
∑
n∈N
∑
g∈G
∑
τ∈Γ
zgn(τ)En (32)
s.t.



∑
g∈G
zgn(τ)≤ 1, ∀τ∈ Γ, n∈N∑
g∈G
∑
τ∈Γ
Pgn(τ)zgn(τ)≤Bn, ∀n∈N∑
g∈G
∑
n∈N
vgn(τ)zgn(τ)≤V (τ), ∀τ∈ Γ
zgn(τ)∈{ 0, 1}, ∀τ∈ Γ, n∈N , g∈G
(33)
Among the constraints, the ﬁrst ensures that each controller
can secure at most one cloud match per bidding round. The
second outlines the budget constraints for each controller,
with Bn representing the budget of controller n. The third
constraint accounts for limited resources, stipulating that the
total resources allocated to the winning group cannot exceed
V (τ), where vgn(τ) = ∑m∈Magn,m(τ) represents the CPU
resource requirement of controller n in the gth bidding group.
The ﬁnal constraint determines the set of winners.
The optimal social welfare problem requires full system
knowledge across all rounds, which is impractical due to the
stochastic nature of resources and unpredictable user demands
and bids. Additionally, the interdependence of decisions across
rounds, driven by controllers’ budget constraints, complicates
the matching process. To address this, we must convert the
complex ofﬂine matching problem into a series of online
single-round matching problems.
2) Set of Online Matching Problem: For each controller,
we introduce auxiliary variables ygn(τ), initially set to 0 and
increasing towards 1 as the controller’s remaining budget
decreases, reaching 1 when the budget is fully exhausted.
We adjust the valuation at the start of each round τ to
wgn(τ) = (1 −ygn(τ− 1))Egn(τ). This budget-based bidding
method prevents early budget depletion, making the budget-
aware single matching problem deﬁned as follows [31]:
MPone(τ) : max
∑
g∈G
∑
n∈N
wgn(τ)zgn(τ) (34)
s.t.



∑
g∈G
zgn(τ)≤ 1, ∀n∈N∑
g∈G
∑
n∈N
vgn(τ)zgn(τ)≤V (τ)
zgn(τ)∈{ 0, 1}, ∀n∈N , g∈G
(35)
Using duality theory, the dual form of the linear pro-
gramming is expressed, introducing variables to transform the
NP-hard problem into a solvable form, denoted as (ˆP2):
MPLPone(τ) : max ∑
n∈N
qn(τ) +V (τ)r(τ) (36)
s.t.



qn(τ) +r(τ)vgn(τ)≥wgn(τ),
∀n∈N , g∈G
qn(τ),r (τ)≥ 0, ∀n∈N
(37)
where qn(τ) and r(τ) are the dual variables.
To appropriately represent the variableygn(τ), we deﬁne two
additional variables:
φ = (1 +Bmax)1/Bmax,
Bmax = maxτ∈Γ,n∈N,g∈G{Pgn(τ)/Bn}, (38)
whereBmax denotes the maximum ratio between any set’s val-
uation and the controller’s budget. This adjustment promotes
efﬁcient budget use and enhances the stability of matching.
C. Joint Sensing, Communication, and Computing
Optimization Problem
The complexity of intelligent control arises from the need to
account for various sensor parameters, channel conditions, and
control system conﬁgurations. Key factors inﬂuencing system
performance include sensor sampling rate, transmission power,
and computing accuracy. For instance, a higher sampling
rate may enhance control precision but leads to increased
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3370 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
bandwidth usage and data transmission delay. Insufﬁcient
transmission power can cause packet loss or signal attenuation,
impacting the timeliness and reliability of control decisions.
While cloud nodes offer greater computing capability and
higher-precision AI models compared to local fog nodes,
cloud processing incurs additional transmission overhead.
Thus, balancing these factors is crucial for achieving efﬁcient
and reliable control. Our objective is to identify a smooth
policy that includes sampling rate selection, power allocation,
and task ofﬂoading, to minimize the control cost Jn. The
optimization problem (P3) is formulated as:
(P3) : min
γn,ptpn,on
Jn (39)
Here, the decisions regarding sensing, communication, and
computing are interconnected through the control period and
the accuracy of control commands, thereby creating a joint
resource optimization problem for intelligent control.
V. H IERARCHICAL APPROACH FOR CO-D ESIGN
OPTIMIZATION PROBLEM
This section presents a solution to the joint optimization
problem. We ﬁrst propose solutions for (P2) and (P3) indi-
vidually. Next, we introduce a hierarchical joint optimization
framework to efﬁciently address the combinatorial problem.
A. Auction-Based Multi-Controller Cloud Resource
Competition
We divide the core process of the resource competition
algorithm into two parts to address problem(P2). The ﬁrst part
focuses on the online matching framework, while the second
part examines the single matching mechanism, highlighting
enhancements made to the matching algorithm.
1) Online Matching Framework: In the online matching
framework, the budget needs to be updated, for ∀n∈N ,g∈
G, which is expressed as:
wgn(τ) =
{
0, if ygn(τ− 1)≥ 1
(1−ygn(τ− 1))Pgn(τ− 1), otherwise.
(40)
Once the budget update is complete, a single VCG auction
algorithm is executed to determine the ﬁnal set of auction
winners. Bids for auction items from controllers not in the
winner set are set to 0. Finally, the auxiliary variables are
updated based on the budget:
ygn(τ) =
(Pgn(τ)
Bn
+ 1
)
ygn(τ− 1) + Pgn(τ)(φ− 1)Bn. (41)
2) Single Matching Mechanism: To address problem
MPone(τ), the VCG mechanism can be applied in the single
matching process. This algorithm maximizes social welfare
while ensuring authenticity and individual rationality. In this
mechanism, each controller’s payment depends solely on the
valuations of others, independent of its own bid. Consequently,
providing a dishonest reported valuation may result in a
higher payment obligation, making it a dominant strategy
for competitors to report truthfully. To represent the winner’s
reward, let Υ−n(τ) denote the social welfare obtained when
winner n is excluded. The payment of controller n is expressed
as: Pn(τ) = Υ−n(τ)−∑g∈G∑n′N/{n} zgn′(τ)wgn′(τ).
To solve a single matching problem, we ﬁrst obtain the
optimal fractional solution through LP relaxation. Next, we
decompose this solution into a combination of feasible integer
solutions based on LP duality. Finally, using the on-demand
matching decisions, we calculate the user satisfaction ratio to
derive the optimal solution that maximizes this ratio.
a) Optimal fractional solution based on LP relaxation:
We relax the constraint zgn(τ)∈{ 0, 1},∀τ∈ Γ,n∈N ,g∈G
to 0≤ zgn(τ)≤ 1. A feasible solution to MP one(τ) is denoted
as ZF(τ) ={zgFn (τ)|n∈N ,g ∈G} , where zgFn (τ)∈ [0, 1].
Additionally, the utility of each controller is typically deﬁned
as the difference between their payment and valuation. The
optimal fractional solution of MP LPone(τ) is determined by
wgn(τ) = max{0, (1−ygn(τ− 1))Egn(τ)}.
Algorithm 1 VCG-Based Multi-Controller Cloud Resource
Competition
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3371
Theorem 1: Single VCG matching obtains fractional solu-
tions while ensuring authenticity and individual rationality,
˜zgn(τ),∀n∈N ,g∈G .
b) Feasible integer solutions based on LP dual decompo-
sition: The solution derived from LP relaxation is a fractional
solution, whereas we require an integer matching scheme.
Therefore, we need to further decompose the optimal fractional
solution into combinations of feasible integer solutions using
a decomposition approach based on LP duality. Our purpose
is to determine βl∈ [0, 1] and a set of integer solutions zgln (τ)
makes zgFn (τ) =∑l∈Lβlzgln (τ),∀l∈L , whereL denotes the
index set, and ∑l∈Lβl = 1. However, a convex combination
of integer solutions that satisﬁes the above equality relation
does not exist. Thus, we need to scale down the optimal
fractional solution by a certain factor, using v as the scaling
factor to obtain a feasible solution. Given the high complexity
of traversing all potential integer solutions, we introduce the
dual variables ιgn(τ) and κ to formulate the dual problem:
MPLPfrac(τ) : max
(1
v
)∑
g∈G
∑
n∈N
zgFn (τ)ιgn(τ) +κ (42)
s.t.



∑
g∈G
∑
n∈N
zgln (τ)ιgn(τ) +κ≤ 1,
∀l∈L
τ≥ 0
(43)
The primal-dual problem can be solved by applying the
ellipsoid method.
Theorem 2: Our primal-dual algorithm provides feasible
solutions for MPone(τ) and MPLPone(τ), with a competitive ratio
of v, and
v = 1 +ϵ(τ)(e− 1) (1 + 1/ (Amin(τ)− 1))
ϵ(τ) = max
g1,g2
{cg1n (τ)/cg2n (τ)}, (44)
where Amin(τ) is the minimum value among the maximum
resource demand values; ϵ(τ) represents the maximum ratio
of all requirements.
c) Optimal solution based on on-demand matching
policy: To solve the cloud server resource competition
optimization problem, it is crucial to establish on-demand
matching and pricing decisions. A probability βl is selected
to generate an integer solution Zl(τ), and the user satisfaction
ratioρl(τ) is calculated as the ratio of total resources allocated
to a user over the user’s required resources. The optimal
solution Zl∗(τ) is then selected based on the highest user
satisfaction ratio. For the winning controller n, the payment
must satisfy two conditions: First, to ensure authenticity,
the expected payment must equal the scaled-down fractional
payment, expressed as ∑l∈LβlPln(τ) = PFn (τ)v . Second,
the payment Pln(τ) should not exceed the bidder’s valuation
of their winning set, given by ∑g∈Gwgn(τ)zgn(τ), to ensure
individual rationality.
Theorem 3: Integrating the single matching part into
the online matching framework can still ensure the
authenticity of the algorithm, individual rationality, and
(1 +Bmax)
(
v (1 +Bmax) + 1φ−1
)
competition ratio.
3) Improved Online Matching Algorithm: To enhance the
competition ratio of the overall online algorithm, we improve
upon Algorithm 1 by using a smaller scaling factor and
reducing the controller’s budget expenditure, resulting in an
improved online matching algorithm.
a) Update scaling factor: In the online matching process,
the scaling factor v inﬂuences the contention ratio. Reducing
v increases the contention ratio, but using a value smaller than
v may jeopardize feasibility. To address this, we implement a
binary search method to identify the smallest feasible scaling
factor for improvement. We set an allowable error δ and
deﬁne the scaling ratio v with initial values vl = 1 and
vx = v. We iteratively compute vh ← (vl +vx)/2 until
vr−vl≤δ. If this condition is not satisﬁed, we updatevx =vh
or vl = vh accordingly. Using this binary search method,
we can efﬁciently determine the minimum feasible reduction
factor v.
b) Reduce budget: Building on the improved factor, we
develop an online matching algorithm aimed at minimiz-
ing budget expenditure. We assume that each controller n
allocates at least βn(where 0 ≤ βn ≤ 1) of its budget
across all rounds, deﬁning β = min{βn},∀n as the min-
imum budget expenditure ratio. This strategy enables us to
achieve a more competitive ratio while reducing overall budget
expenditure.
Theorem 4: The improved algorithm is authenticity, individ-
ual rationality and (1+Bmax)
(
ν(1 +Bmax) + 1−βφ1−β−(1−β)
)
-
competition ratio.
The computational complexity of the proposed Algorithm 1
primarily arises from the resource competition process, which
iteratively selects the optimal combination of controllers
and resources using a greedy strategy. The complexity is
inﬂuenced by the number of controllers N, the size of
the candidate bid set G, and the duration of the auction
process Γ. Thus, the total computational complexity of Algo-
rithm 1 is O
(
N2GΓ).
B. Heuristic-Based Joint Sensing, Communication, and
Computing Optimization
To solve problem (P3), we utilized a heuristic-based DE
algorithm [32], an effective global optimization method. The
DE algorithm maintains a distance between new and original
genes to reduce the risk of local optima. By using ﬂoating-
point encoding for continuous space optimization, it effectively
addresses real variable optimization problems. Below, we
outline the solution process.
1) Question Coding: The decision for task kin is treated
as a population consisting of R individuals, represented as
Xn =
{
x1n,x 2n,...,x rn,...,x Rn}, where xrn denotes the gene
vector of individual r. This task, along with its associated
problem involving three solution variables, is mapped onto the
individuals in the population. Each individual is characterized
by three chromosomes, represented as xrn ={γrn,p tp,rn ,orn}.
2) Random Initialization: After encoding the population, it
must be initialized, and the genes of the individuals need to
be assigned values. Each gene locus has a speciﬁc constraint
range. For instance, for the sampling rate γn, the initialization
value of the gene locus is randomly generated between (0, 1);
the transmission power ptpn is generated within its minimum
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3372 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
Algorithm 2 DE-Based Joint Sensing, Communication, and
Computing Optimization Algorithm
and maximum limits; and the ofﬂoading decision on is ran-
domly generated between {0, 1}.
3) Dynamic Mutation: Let S denote the number of itera-
tions in the evolution of the proposed DE-based algorithm,
i.e., the number of generations. A mutant gene is generated
for each individual, representing the result of mutating the
original gene over different time periods. When mutating an
individual, three randomly selected individuals from the same
generation are used, and their genes undergo the following
operations:
Lr(s) =Xa(s) +W(Xb(s)−Xc(s)), (45)
Here, s = 1, 2,...,S denotes the sth generation individual,
while a,b,c represent different individuals. W is the scaling
factor,Xa(s) represents the original genes of individual a in
the sth generation, and Lr(s) denotes the mutant genes of
individual r in the sth generation. Additionally, the generated
mutant genes must be monitored during the mutation process
to ensure compliance with experimental constraints.
4) Flexible Crossover: Crossover involves replacing an
individual’s original gene with its mutated gene based on a
speciﬁc probability, with the crossover position determined
randomly. After crossover, it is essential to check whether the
resulting geneHr(s) complies with environmental constraints.
Since constraints are applied during population initialization
and mutation, the gene values after the crossover operation
should still satisfy these conditions.
5) Elite Selection: The DE algorithm selects the optimal
individual from each generation and compares it with those
from previous generations, retaining individuals with higher
ﬁtness values. The variables gbs and gbf are used to store the
joint optimization decision and ﬁtness value of the current
optimal individual. A greedy strategy guides the selection
Algorithm 3 Hierarchical Iterative Optimization Algorithm
process, which operates as follows:
gbs =
{
Hr(s), F (Hr(s))<F (gbs)
gbs, otherwise.
gbf =
{
F (Hr(s)), F (Hr(s))<F (gbs)
gbf, otherwise. (46)
where F represents the ﬁtness function. In the DE algorithm,
the ﬁtness value assesses how well individuals adapt to the
environment. Considering the research problem of this article,
the goal is to minimize Jn under resource constraints; thus,
Jn is deﬁned as the algorithm’s ﬁtness function. The com-
putational complexity of Algorithm 2 depends on the number
of controllers N, the population size R, and the number of
iterations S in the algorithm’s evolution. Therefore, the total
computational complexity of Algorithm 2 is O(NSR ).
C. Hierarchical Iterative Optimization Algorithm
Drawing on the individual convergence of problems (P2)
and (P3), we introduce a hierarchical iterative optimization
framework to provide iterative solutions for problems (P2)
and (P3) to achieve joint optimization of sampling rate,
power allocation, task ofﬂoading, and resource competition
decisions, as shown in 5. Algorithm 3 describes our hierar-
chical approach in detail. Speciﬁcally, after solving the ﬁrst
iteration of problem (P2), the cloud resource competition
policy{a(1)n | n ∈ N} is obtained and fed back into the
joint resource optimization problem (P3) to update the joint
resource optimization policies(i.e., sampling rate selection,
power allocation, task ofﬂoading) {γ(1)n ,p tp,(1)n ,o (1)n | n ∈
N} to reduce the control cost under the current resource
competition policy and minimize the control overhead of
each controller. Then, the second iteration starts to solve
(P2) and (P3) in turn to determine {a(2)n | n ∈ N} and
{γ(2)n ,p tp,(2)n ,o (2)n | n∈N} . This process is repeated until
the resource competition policy{a(η)n |n∈N} obtained after
multiple iterations is close to {a(η−1)n |n∈N} . The outputs
of (P2) and (P3) are a set of optimal solutions for resource
competition{a(∗)n | n∈N} and joint resource optimization
{γ(∗)n ,p tp,(∗)n ,o (∗)n | n∈N} , which collectively optimize the
control overhead of the SeCo4 system. After achieving con-
vergence, which is typically reached after XH iterations, the
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3373
Fig. 4. Illustration of the hierarchical optimization framework.
total computational complexity of the hierarchical algorithm
can be calculated as O
(
XH
(
N2GΓ +NSR)).
VI. S IMULATION RESULTS AND DISCUSSIONS
This section presents the simulation results, showcasing the
performance of our proposed intelligent control framework for
the co-design of sensing, communication, and computing.
A. Simulation Setup
The experimental parameters are established based on the
guidelines of previous studies [27], [33], [34]. The environ-
ment is built using the Pytorch framework. Our scenario
considers an intelligent control network consisting of multiple
cloud nodes and different numbers of controllers, each of
which controls a certain number of sensors. This work utilizes
datasets from the Alibaba Cluster Tracking Program [35],
[36] to simulate variations in cloud resources and tasks.
Assume that the sensor’s transmission power ranges from
0.1∼ 1 W, the sampling time is 0.1 seconds, the sampling
rate ranges from 5 ∼ 10 KHz, and the frequency of the
transmitted signal is 2400 MHz. The transmit and receive
antenna gains between the controller and the sensor are 0 dB.
In addition, the controller’s task processing rate is 104 Bps
with a processing accuracy of 70%; the cloud server’s task
processing rate is 5× 104 Bps with a processing accuracy
of 90%. For the proposed VCG-based resource competition
algorithm,{10, 100, 300} rounds of auctions are conducted,
the number of controllers is{5, 10, 15, 20, 25} and the number
of bids in each round is {5, 10, 15, 20, 25}, respectively. The
budget of each controller is set between 300 and 330. For
the proposed DE-based joint resource optimization algorithm,
the population size is set to 100, the maximum number of
iterations is set to 200, the number of tasks is 1∼ 7, the
number of controllers is {1, 2, 5, 10, 15, 30, 50}, the number
of sensors is {1, 2, 5, 10, 15, 30, 50}, the scaling factor is set
to 0.9, and the crossover probability is set to 90%.
We performed experiments to ensure accurate and reliable
results, comparing our proposed scheme with the following
benchmark methods:
Fig. 5. User’s experience of MatOnline.
• MatSPS scheme: at every computing resource competition
period, the MatSPS (Second Price Sealed Matching)
algorithm is employed for resource competition.
• MatRAN scheme : at every computing resource competi-
tion period, the MatRAN (Random Matching) is used to
compete computing resources to controllers randomly.
• GA scheme: at every joint resource optimization decision
period, the Genetic Algorithm (GA) method is used to
select optimization policies.
• SA scheme: at every joint resource optimization decision
period, the Simulated Annealing (SA) method is adopted
to select optimization policies.
• PSO scheme: at every joint resource optimization decision
period, the Particle Swarm optimization (PSO) method is
adopted to select optimization policies.
• EDA scheme: at every joint resource optimization deci-
sion period, the Estimation of Distribution Algorithm
(EDA) method is adopted to select optimization policies.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3374 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
Fig. 6. Social welfare and user satisfaction ratio of MatOnline, MatSPS and MatRAN.
Fig. 7. Performance of the proposed scheme and the benchmark joint optimization scheme.
Fig. 8. Performance of the proposed scheme and the benchmark joint optimization scheme.
B. Simulation Results
Based on the deﬁned parameters, we conducted simula-
tions to evaluate the efﬁciency of our proposed VCG-based
matching algorithm, MatOnline. In Fig. 5, we analyze its
performance in cloud computing resource competition from
four perspectives: controller satisfaction, individual expen-
diture, total expenditure, and budget utilization, comparing
the number of controllers to auction rounds. As shown in
Fig. 5(a), user satisfaction increases with the number of con-
trollers due to limited cloud resources, although more auction
rounds negatively impact satisfaction. Fig. 5(b) indicates that
individual expenditure rises with more controllers and fewer
auction rounds, consistent with the principle that scarcity
increases prices. Figs. 5(c) and 5(d) show that total expenditure
also increases with more auction rounds. Budget utilization
diverges from total expenditure; when the number of con-
trollers is low, resource oversupply diminishes competition,
leading to decreased total expenditure and subsequently lower
budget utilization.
Subsequently, we assess the performance of our pro-
posed scheme by comparing it to cloud resource competition
methods based on two other matching algorithms. In Fig. 6,
we analyze its effectiveness against the MatSPS-based and
MatRAN-based schemes, as well as a local scheme, con-
sidering varying auction rounds, controller numbers, and bid
set sizes. The evaluation metrics include social welfare and
user satisfaction. The bar chart shows social welfare trends,
while the line chart depicts user satisfaction. Social welfare
consistently increases with more auction rounds, controllers,
and bid set sizes. In contrast, user satisfaction declines with
increased controllers and bid set sizes, with auction rounds
having minimal impact. These ﬁndings suggest that height-
ened competition from more controllers and bid set sizes
leads to lower overall satisfaction. Our proposed scheme
consistently outperforms the others, with the MatSPS scheme
following, and the MatRAN scheme performing the weakest.
For instance, with 300 auction rounds, our scheme’s social
welfare is approximately 119.8% and 227.6% higher than
the MatSPS and MatRAN schemes, respectively, while user
satisfaction exceeds these by 234.4% and 576.9%. When the
number of controllers is 15, our scheme achieves social wel-
fare values of approximately 127.1% and 306.7% higher than
MatSPS and MatRAN, with user satisfaction at 248.8% and
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3375
Fig. 9. Performance of the proposed scheme and the benchmark joint optimization scheme.
Fig. 10. Performance of hierarchical iterative optimization algorithm.
888.3% higher. With a bid set size of 15, our scheme’s social
welfare is about 143.3% and 167.6% greater than MatSPS and
MatRAN, respectively, and user satisfaction is around 179.4%
and 508.3% higher.
In Fig. 7–Fig. 9, we analyze the performance of our
proposed solution for joint resource optimization, compar-
ing it with GA-based, SA-based, PSO-based and EDA-based
approaches in terms of average delay, control satisfaction
ratio, and control cost across varying task, controller, and
sensor numbers. As shown in Fig. 7, as the number of tasks
increases, the overall system load rises, leading to a signiﬁcant
increase in average delay and control cost, while control
satisfaction remains largely unchanged. Notably, our proposed
solution outperforms all benchmarks. For instance, with 5
tasks, the proposed solution achieves an average delay that are
approximately 21.2%, 27.3%, 18.4% and 14.1% lower than the
GA, SA, PSO and EDA solutions, respectively, and satisfaction
ratios that are about 76.7%, 483.8%, 29.5% and 25.8% higher.
Control costs are reduced by approximately 20.1%, 20.8%,
20.4% and 11.4% respectively. In Fig. 8, we observe that as
the number of controllers increases, average delay and control
cost rise signiﬁcantly, while control satisfaction remains stable.
With 15 controllers, the proposed solution achieves an average
delay that that are 15.5%, 36.5%, 25.3% and 18.9% lower
than the GA, SA, PSO and EDA solutions, respectively, and
satisfaction ratios of 169.3%, 227.1%, 106.8% and 36.2%
higher. Additionally, control costs are reduced by approx-
imately 25.1%, 29.4%, 22.6%, and 18.5%, respectively. In
Fig. 9, we ﬁnd that as the number of sensors increases, the
average delay and control cost increase signiﬁcantly, while the
control satisfaction decreases. With 30 sensors, the proposed
solution has average delays that are 11.9%, 18.3%, 7.3% and
12.2% lower than the GA, SA, PSO and EDA solutions,
respectively, and satisfaction ratios of 48.1%, 106.1%, 19.1%
and 28.8% higher. Control costs are approximately 35.6%,
60.1%, 24.4% and 12.5% lower.
Finally, in Fig. 10, we present simulation tests to validate the
effectiveness of the joint iterative optimization algorithm by
analyzing average delay, satisfaction, and control cost across
varying numbers of controllers and iterations. The results show
that as iterations increase, both average delay and control
cost decrease, while the satisfaction ratio gradually rises, with
slower changes around 30 iterations, indicating convergence.
This suggests a transition from a local to a global optimal
solution, conﬁrming the algorithm’s effectiveness. For exam-
ple, with four controllers, the average delay, satisfaction ratio,
and control cost after 30 iterations are approximately 47.6%,
200.1%, and 61.9% of their values at ﬁve iterations, respec-
tively, highlighting signiﬁcant optimization post-convergence.
Furthermore, the ﬁgure reveals that increasing the number of
controllers adds complexity, intensiﬁes competition for cloud
resources, and reduces individual controller performance.
In summary, the numerical results demonstrate the effec-
tiveness of the proposed scheme for the co-design of sensing,
communication, and computing in intelligent control through
an iterative process. In the cloud resource competition prob-
lem, it outperforms benchmark methods like MatSPS and
MatRAN in terms of social welfare and user satisfaction
across various metrics. Furthermore, in joint resource opti-
mization, the proposed scheme signiﬁcantly improves average
delay, controller satisfaction, and control costs compared
to four other benchmark approaches. These improvements
demonstrate the scheme’s ability to optimize cloud resource
competition and the coordination of sensing, communication,
and computing resources, leading to more efﬁcient data pro-
cessing and enhanced control performance.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3376 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
VII. C ONCLUSION
This article proposed SeCo4, an intelligent control frame-
work for co-design of sensing, communication, and computing
in industrial CPS. In this framework, the SeCo4 optimization
problem was explored and divided into two sub-problems to
address its complexity: a multi-controller cloud resource com-
petition problem, formulated using a combinatorial auction to
enhance control performance; a joint resource optimization
problem for sensing, communication, and computing, modeled
with a MIP to reduce control overheads. Given the interde-
pendence between these sub-problems, a hierarchical solution
combining the VCG mechanism and the DE approach was
developed to iteratively ﬁnd the optimal solution. Extensive
experiments were conducted to validate the proposed scheme’s
effectiveness and superiority.
APPENDIX A
PROOF OF THEOREM 1
Supposing the valuation of user n is ωgn(τ), and the val-
uation for other users n′ ⁄= n is ωgn′(τ). Then, un(τ) =∑
g∈G
∑
n∈N zgn(τ)ωgn(τ)− Υ−n(τ) represents the utility of
user n, where zgFn (τ) is obtained by maximizing the total
social welfare, hence we have ∑g∈G∑n∈N zgFn (τ)ωgn(τ)≥
Υ−n(τ). Since the latter has one less user’s value under
equal resources, therefore un(τ)≥ 0. We assume the reported
valuation of user n is a potentially false bid ˜ωgn(τ), and ˜zgFn (τ)
is the corresponding matching score decision. The utility of a
dishonest user is:
˜un(τ) =
∑
g∈G
˜zgFn (τ)ωgn(τ)− Υ−n(τ)
+
∑
g∈G
∑
n′⁄=n
˜zgFn′ (τ)ωgn′(τ). (47)
The difference between the utilities of the two bids is:
un(τ)− ˜un(τ) =
∑
g∈G
∑
n∈N
zgn(τ)ωgn(τ)
−
∑
g∈G
∑
n∈N
˜zgFn (τ)ωgn(τ). (48)
Since zgFn (τ) is the maximizer of the total social
welfare, it follows that ∑g∈G∑n∈N zgn(τ)ωgn(τ) −∑
g∈G
∑
n∈N ˜zgFn (τ)ωgn(τ) ≥ 0, thus un(τ) ≥ ˜un(τ).
Our algorithm ensures truthful bidding.
APPENDIX B
PROOF OF THEOREM 2
The ﬁrst and third constraints in constraint (34) are always
satisﬁed. We assume that ωgn∗n∗ is the ﬁrst to violate this
constraint at time τ∗ among the winning bids:
∑
n∈Φ
cgnn ≤V <∑
n∈Φ
cgnn +cgn∗n∗ . (49)
We have A≥cgn∗n∗ , thus
∑
n∈Φ
cgnn ≥V−A. (50)
Let Vr (τ∗− 1) =r
(∑
n∈Φcgnn
V−A
)
base ≥rbase where r(τ∗− 1) is
the value of r before roundτ∗. Therefore, the second constraint
of (34) is followed. This proves the feasibility of our MPone(τ)
primal-dual algorithm.
Let (qn(τ∗− 1),r (τ∗− 1)) denote the dual solution of
MPLPone(τ) before τ∗. We deﬁne f(r,n,g ) = ωgncgnr , and assumethat (qn(τ∗−1),ϵf (r,n∗,gn∗)r(τ∗−1)) is a possible solution
for MPLPone(τ). In the matching decision, user n∗ is chosen with
the maximum ωgn, therefore ωgnn ≥ωgn,∀n∈N ,g∈G . When
∀n /∈ Φ,g∈G , we then have
f(r,n∗,gn∗)cgnr(τ∗− 1)≥ωgn
ϵf(r,n∗,gn∗)cgnr(τ∗− 1)≥ωgn (51)
Thus, we prove that (qn(τ∗− 1),ϵf (r,n∗,gn∗)r(τ∗− 1))
is also feasible for MP LPone(τ) at time τ∗− 1.
Finally, we will prove that the competitive ratio of our
primal-dual algorithm is also ν. We execute Algorithm 1
for Γ rounds. Let d∗ be the optimal solution of MP LPone(τ),
d1(τ∗) = ∑n∈Nqn, d2(τ∗) = Vr (τ∗), where (n∗,g∗) is
the winning set in round τ∗. When all users win a set of
bids and Vr < rbase, Algorithm 1 ends after Γ rounds. In
this case, Algorithm 1 has a competitive ratio of ν. When
d2(τ∗) ≥ rbase,∃τ∗ ≤ Γ, i.e., λd1(τ∗ − 1) ≥ d∗,
Algorithm 1 ﬁnishes at Γ. Thus, the solution of Algorithm 1
is a ν-competition ratio of the social welfare. When d2(τ∗)≥
rbase and λd1(τ∗− 1)<d∗,∀τ∗≤ Γ, Algorithm 1 ends at Γ.
We have
d2(τ∗) =Vr (τ∗) =Vr (τ∗− 1)
(
1 + ηV/A− 1)cg∗n /V−A.
(52)
For any round τ∗ when η = (V/A− 1)(r1/(V/A−1)base − 1),
then we have
d2(τ∗)≤Vr (τ∗− 1)
(
1 + ηV/A− 1)cg∗n /V−A. (53)
We deﬁne O = max
{
ηV
V−A
}
, so we have
d2(τ∗)−Ocg∗n r(τ∗− 1)≤d2(τ∗− 1). (54)
Therefore, when V = Aminr, ηVV−A reaches its maximum
value because ηVV−A does not increase with V/r . We have
f(r,n,g )∗ = ωg∗n
cg∗n r , then cg∗n r(τ∗− 1)f(r,n,g )∗ = ωn(τ∗−
1)g(τ∗−1). Therefore, we get
f(r,n,g )∗ϵd2(τ∗− 1)≥d∗2−d1(τ∗− 1)
νϵd2(τ∗− 1)f(r,n,g )∗≥d∗(ν− 1) (55)
After the iterative formula d2(0)eϵpνO/((ν−1)d∗)≥ d2(Γ),
we get eϵpνO/((ν−1)d∗) ≥ rbase. Since d2(0) = 1 , d2(Γ)≥
rbase. Hence ϵpνO≥ (ν− 1)(A− 1)d∗ and ϵνO(ν−1)(A−1) =ν,
proving that the competitive ratio of our primal-dual algorithm
is also ν.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

TANG et al.: SeCo4: CO-DESIGN OF SENSING, COMMUNICATION, AND COMPUTING FOR INTELLIGENT CONTROL 3377
APPENDIX C
PROOF OF THEOREM 3
We assume that ρ(τ) = ∑g∈G∑n∈N zgn(τ)ωgn(τ) is the
objective value of MP one(τ), and the dual objective value in
MPLPone(τ) is d(τ) =r(τ) +∑n∈Nqn(τ).
Let ∆ρ(τ) =ρ(τ)−ρ(τ−1) and ∆d(τ) =d(τ)−d(τ−1).
We substituteρ(τ) =∑n∈N (1−ygn(τ− 1))Egnn (τ) forρ(τ),
so we get ∆ρ(τ) = ∑n∈NEgnn (τ). Therefore, Algorithm 1
ensures
(
ν + 1φ−1
)
ρ(τ)≥d(τ),∀τ∈ Γ.
Since the increment of total social welfare is determined by
calculating the minimum between the user’s reported valuation
and its remaining budget, the total social welfare should be at
least ρ(Γ)1+Bmax . Given (ν + 1φ−1) ∆ρ(τ)≥ d(τ),∀τ∈ Γ and
ρ(0) = d(0) = 0, we obtain
(
ν + 1φ−1
)
ρ(Γ)≥d(Γ). In the
worst case, the service provider can achieve social welfare as
follows:
Usp(Γ) = d(Γ)
(1 +Bmax)
(
ν + 1φ−1
) (56)
The expected increments of the primal problem and its dual
are E[∆ρ] and E[∆d]. At time τ, we have
E[∆ρ(τ)] =
∑
g∈G
∑
n∈N
E[zgn(τ)εgn(τ)]
(
ν(1 +Bmax) + 1φ− 1)E[∆ρ(τ)]≥E[∆d(τ)] (57)
Therefore, we can prove that Theorem 3.
APPENDIX D
PROOF OF THEOREM 4
Similar to Theorem 3, the only difference between the
improved algorithm and the previous one is the way we update
yn(τ). We have βnBn =∑τ∈ΓEgnn (τ) as the total reported
valuation for user n, andypn = βnφ1−βn−(1−βn). Whenβ′n >β n,we have
yn≥ (1−βn)(vβ′n−βn− 1)φ1−βn− (1−βn) +vβ′n−βnypn (58)
When β′n≤βn, we have
yn≥
( 1−βn
φ1−βn− (1−βn) +ypn
)
β′n (59)
We can prove three cases similar to Theorem 2.
REFERENCES
[1] J. Jin, K. Yu, J. Kua, N. Zhang, Z. Pang, and Q.-L. Han, “Cloud-
fog automation: Vision, enabling technologies, and future research
directions,” IEEE Trans. Ind. Informat. , vol. 20, no. 2, pp. 1039–1054,
Feb. 2024.
[2] S. Karnouskos, P. Leitao, L. Ribeiro, and A. W. Colombo, “Industrial
agents as a key enabler for realizing industrial cyber-physical systems:
Multiagent systems entering industry 4.0,” IEEE Ind. Electron. Mag. ,
vol. 14, no. 3, pp. 18–32, Sep. 2020.
[3] R. Muzaffar, M. Ahmed, E. Sisinni, T. Sauter, and H.-P. Bern-
hard, “5G deployment models and conﬁguration choices for industrial
cyber-physical systems—A state of art overview,” IEEE Trans. Ind.
Cyber-Phys. Syst., vol. 1, pp. 236–256, 2023.
[4] S. Waschull, J. A. C. Bokhorst, E. Molleman, and J. C. Wortmann,
“Work design in future industrial production: Transforming towards
cyber-physical systems,” Comput. Ind. Eng. , vol. 139, Jan. 2020, Art.
no. 105679.
[5] L. Apilio ˇgulları, “Digital transformation in project-based manufacturing:
Developing the ISA-95 model for vertical integration,” Int. J. Prod.
Econ., vol. 245, Mar. 2022, Art. no. 108413.
[6] K. B. Lee and K. B. Lee, “Reliable, high-performance wireless systems
for factory automation,” Dept. U.S. Dept. of Commerce, Nat. Inst.
Standards Technol., Gaithersburg, MD, USA, Tech. Rep. 8317, 2020.
[7] H. Lyu, Z. Pang, A. Bengtsson, S. Nilsson, A. J. Isaksson, and G. Yang,
“Latency-aware control for wireless cloud-fog automation: Framework
and case study,” IEEE Trans. Autom. Sci. Eng., vol. 22, pp. 5400–5410,
2025.
[8] H. Lyu, J. Yan, J. Zhang, Z. Pang, G. Yang, and A. Isaksson, “Cloud–fog
automation: Heterogenous applications over new-generation infrastruc-
ture of virtualized computing and converged networks,” IEEE Ind.
Electron. Mag., vol. 18, no. 4, pp. 30–42, Dec. 2024.
[9] A. Botta, W. de Donato, V . Persico, and A. Pescap ´e, “Integration of
cloud computing and Internet of Things: A survey,” Future Generat.
Comput. Syst., vol. 56, pp. 684–700, 2016.
[10] Z. Feng, Z. Wei, X. Chen, H. Yang, Q. Zhang, and P. Zhang, “Joint com-
munication, sensing, and computation enabled 6G intelligent machine
system,” IEEE Netw., vol. 35, no. 6, pp. 34–42, Nov. 2021.
[11] W. Xu, Z. Yang, D. W. K. Ng, M. Levorato, Y . C. Eldar, and M. Debbah,
“Edge learning for B5G networks with distributed signal processing:
Semantic communication, edge computing, and wireless sensing,” IEEE
J. Sel. Topics Signal Process. , vol. 17, no. 1, pp. 9–39, Jan. 2023.
[12] L. Liu, S. Liu, and W. Shi, “4C: A computation, communication,
and control co-design framework for CA Vs,” IEEE Wireless Commun.,
vol. 28, no. 4, pp. 42–48, Aug. 2021.
[13] B. S. Khan, S. Jangsher, A. Ahmed, and A. Al-Dweik, “URLLC and
eMBB in 5G industrial IoT: A survey,” IEEE Open J. Commun. Soc. ,
vol. 3, pp. 1134–1163, 2022.
[14] M. Kumar, G. K. Walia, H. Shingare, S. Singh, and S. S. Gill, “AI-based
sustainable and intelligent ofﬂoading framework for IIoT in collaborative
cloud-fog environments,” IEEE Trans. Consum. Electron., vol. 70, no. 1,
pp. 1414–1422, Feb. 2024.
[15] G. Liu et al., “An adaptive DNN inference acceleration framework with
end–edge–cloud collaborative computing,” Future Gener. Comput. Syst.,
vol. 140, pp. 422–435, Mar. 2023.
[16] S. Lu et al., “Integrated sensing and communications: Recent advances
and ten open challenges,” IEEE Internet Things J. , vol. 11, no. 11,
pp. 19094–19120, Nov. 2024.
[17] W. Zhang, N. Tang, D. Yang, R. Guo, H. Zhang, and X. Shen,
“Det(Com)2: Deterministic communication and computation integra-
tion toward AIGC services,” IEEE Wireless Commun. , vol. 31, no. 3,
pp. 32–41, Jun. 2024.
[18] J. Zhou, J. Sun, M. Zhang, and Y . Ma, “Dependable scheduling for
real-time workﬂows on cyber–physical cloud systems,” IEEE Trans. Ind.
Informat., vol. 17, no. 11, pp. 7820–7829, Nov. 2021.
[19] C. Niu and L. Wang, “Big data-driven scheduling optimization algo-
rithm for cyber–physical systems based on a cloud platform,” Comput.
Commun., vol. 181, pp. 173–181, Jan. 2022. [Online]. Available: https://
www.sciencedirect.com/science/article/pii/S0140366421003984
[20] R. Asgarnezhad, “An efﬁcient approach to reduce energy consumption
in a fog computing environment using a moth ﬂame optimization
algorithm,” Social Netw. Comput. Sci. , vol. 5, no. 6, p. 708, Jul. 2024.
[21] Z. Meng, D. Ma, S. Wang, Z. Wei, and Z. Feng, “Modeling and design
of the communication sensing and control coupled closed-loop industrial
system,” in Proc. GLOBECOM-IEEE Global Commun. Conf. , Dec.
2023, pp. 2626–2631.
[22] D. He et al., “Integrating sensing and communication for IoT systems:
Task-oriented control perspective,” IEEE Internet Things Mag. , vol. 7,
no. 4, pp. 76–83, Jul. 2024.
[23] Z. Ji, C. Chen, S. Zhu, Y . Ma, and X. Guan, “Intelligent edge
sensing and control co-design for industrial cyber-physical system,”
IEEE Trans. Signal Inf. Process. Over Netw. , vol. 9, pp. 175–189,
2023.
[24] T. Kallehauge, M. V . Vejling, P. Ram ´ırez-Espinosa, K. Kansanen,
H. Wymeersch, and P. Popovski, “On the statistical relation of
ultra-reliable wireless and location estimation,” IEEE Trans. Wireless
Commun., vol. 23, no. 8, pp. 10044–10057, Aug. 2024.
[25] Q. Tang et al., “Joint service deployment and task schedul-
ing for satellite edge computing: A two-timescale hierarchical
approach,” IEEE J. Sel. Areas Commun., vol. 42, no. 5, pp. 1063–1079,
May 2024.
[26] M. Kamran Chowdhury Shisher, B. Ji, I.-H. Hou, and Y . Sun, “Learning
and communications co-design for remote inference systems: Feature
length selection and transmission scheduling,” IEEE J. Sel. Areas Inf.
Theory, vol. 4, pp. 524–538, 2023.
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply. 

3378 IEEE JOURNAL ON SELECTED AREAS IN COMMUNICATIONS, VOL. 43, NO. 10, OCTOBER 2025
[27] W. Wu, P. Yang, W. Zhang, C. Zhou, and X. Shen, “Accuracy-guaranteed
collaborative DNN inference in industrial IoT via deep reinforcement
learning,” IEEE Trans. Ind. Informat. , vol. 17, no. 7, pp. 4988–4998,
Jul. 2020.
[28] R. Fu et al., “Smart sensing and communication co-design for IIoT-
based control systems,” IEEE Internet Things J. , vol. 11, no. 3,
pp. 3994–4014, Mar. 2023.
[29] X. Wen et al., “Age-of-task-aware co-design of sampling, scheduling,
and control for industrial IoT systems,” IEEE Internet Things J., vol. 11,
no. 3, pp. 4227–4242, Mar. 2023.
[30] K. Zhu, J. Liang, J. Li, and C. Yi, “Coded distributed computing with
predictive heterogeneous user demands: A learning auction approach,”
IEEE J. Sel. Areas Commun., vol. 40, no. 8, pp. 2426–2439, Aug. 2022.
[31] T. Huang, S. Tan, Q. Tang, R. Xie, C. Zhang, and F. Richard Yu,
“Coordinating services and networks with NaaS tickets towards service
customization in distributed clouds,” IEEE Trans. Mobile Comput. ,
vol. 23, no. 12, pp. 10984–10999, Dec. 2024.
[32] M. F. Ahmad, N. A. M. Isa, W. H. Lim, and K. M. Ang, “Differential
evolution: A recent review based on state-of-the-art works,” Alexandria
Eng. J., vol. 61, no. 5, pp. 3831–3872, May 2022.
[33] Y . Liu, P. Zeng, J. Cui, and C. Xia, “Co-design of control, computation,
and network scheduling based on reinforcement learning,” IEEE Internet
Things J., vol. 11, no. 3, pp. 5249–5258, Mar. 2024.
[34] Q. Tang et al., “Collective deep reinforcement learning for intelligence
sharing in the Internet of Intelligence-empowered edge computing,”
IEEE Trans. Mobile Comput. , vol. 22, no. 11, pp. 6327–6342, Nov.
2022.
[35] Z. Zhang, F. Zhang, Z. Xiong, K. Zhang, and D. Chen, “LsiA3CS: Deep-
reinforcement-learning-based cloud–edge collaborative task schedul-
ing in large-scale IIoT,” IEEE Internet Things J. , vol. 11, no. 13,
pp. 23917–23930, Jul. 2024.
[36] C. Lu, W. Chen, K. Ye, and C.-Z. Xu, “Understanding the workload
characteristics in alibaba: A view from directed acyclic graph analysis,”
in Proc. Int. Conf. High Perform. Big Data Intell. Syst.(HPBD&IS), May
2020, pp. 1–8.
Qinqin Tang (Member, IEEE) received the Ph.D.
degree from Beijing University of Posts and
Telecommunications (BUPT), Beijing, China, in
2022. She is currently an Associate Researcher
with the School of Information and Communication
Engineering, BUPT. Her current research interests
include mobile edge networks, network artiﬁcial
intelligence, trafﬁc ofﬂoading, and resource manage-
ment and allocation.
Yutian Yang is currently pursuing the Ph.D. degree
with the State Key Laboratory of Networking
and Switching Technology, Beijing University of
Posts and Telecommunications, China. His current
research interests include the industrial Internet of
Things (IIoT), wireless communications, and com-
puting ﬁrst network (CFN).
Jiayi Cui received the B.S. degree in information
and communication engineering from Beijing
University of Posts and Telecommunications
(BUPT), China, in 2022, where she is
currently pursuing the Ph.D. degree with
the State Key Laboratory of Networking
and Switching Technology. Her research
interests include intelligent computing power
networks.
Renchao Xie (Senior Member, IEEE) received the
Ph.D. degree from Beijing University of Posts and
Telecommunications, China, in 2012. He is currently
a Professor with the School of Information and
Communication Engineering, Beijing University of
Posts and Telecommunications. His research inter-
ests include edge intelligence, computing power
networks, integrated networking and computing, and
the industrial Internet of Things. He has served
as the technical program committee (TPC) co-chair
for numerous conferences. He has also served for
several journals as an associate editor or a reviewer.
Tao Huang (Senior Member, IEEE) received the
B.S. degree in communication engineering from
Nankai University, Tianjin, China, in 2002, and the
M.S. and Ph.D. degrees in communication and infor-
mation system from Beijing University of Posts and
Telecommunications, Beijing, China, in 2004 and
2007, respectively. He is currently a Professor with
Beijing University of Posts and Telecommunica-
tions. His current research interests include network
architecture, network artiﬁcial intelligence, routing
and forwarding, and network virtualization.
Tianjiao Chen received the Ph.D. degree from
Beijing University of Posts and Telecommunica-
tions, Beijing, China, in 2022. He is currently a
Research Fellow with China Mobile Research Insti-
tute. His research interests include machine learn-
ing, network virtualization, and software-deﬁned
networking (SDN).
Ran Zhang (Member, IEEE) received the Ph.D.
degree from Beijing University of Posts and
Telecommunications (BUPT), Beijing, China, in
2021. He is currently an Associate Researcher
with the School of Information and Communication
Engineering, BUPT. His research interests include
satellite communications, named data networking,
and artiﬁcial intelligence.
Zehui Xiong (Member, IEEE) received the Ph.D.
degree from Nanyang Technological University
(NTU), Singapore. He was a Visiting Scholar with
Princeton University and the University of Waterloo.
He is currently an Assistant Professor with Singa-
pore University of Technology and Design, and also
an Honorary Adjunct Senior Research Scientist with
the Alibaba-NTU Singapore Joint Research Institute,
Singapore. His research interests include wireless
communications, the Internet of Things, blockchain,
edge intelligence, and metaverse. He is serving as
an Editor or the Guest Editor for many leading journals, including IEEE
JOURNAL ON SELECTED AREAS IN COMMUNICATIONS , IEEE T RANSAC -
TIONS ON VEHICULAR TECHNOLOGY , and IEEE I NTERNET OF THINGS
JOURNAL .
Authorized licensed use limited to: Beijing Jiaotong University. Downloaded on October 13,2026 at 10:27:58 UTC from IEEE Xplore.  Restrictions apply.