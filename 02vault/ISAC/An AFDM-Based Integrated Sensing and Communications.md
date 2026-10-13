---
title: "An AFDM-Based Integrated Sensing and Communications"
aliases:
  - AFDM-ISAC
  - AFDM 通感一体化
tags:
  - literature-note
  - reading-note
  - ISAC
  - AFDM
  - waveform
created: 2026-10-13
source: 2022 25th International Symposium on Wireless Communication Systems (ISWCS), 2022
author: Yuanhan Ni, Zulin Wang, Peng Yuan, Qin Huang
year: 2022
journal: ISWCS 2022

theme: 用 AFDM 波形同时承载通信信息与感知目标，解决高移动性场景下的距离-多普勒耦合问题
study_area: 通感一体化 / 一体化波形设计 / 高移动性感知
methodology: AFDM 波形 + 两种参数估计（时域 FCCR / DAFT 域）+ 整数与分数多普勒合并
key_finding: DAFT 域方法在大多普勒下仍保持良好 PSLR 与图像 SNR，优于 OFDM 符号除法与时域方法
relevance: AFDM 是继 OFDM/OTFS/OCDM 之后的新候选波形，对高动态 UAV/车载 ISAC 场景直接相关

type: literature-note
zotero_key: "IVFQQXLZ"
pdf_key: "Z2RV53DR"
doi: "10.1109/ISWCS56560.2022.9940346"
collection: "ISAC"
note_path: "02vault/ISAC/An AFDM-Based Integrated Sensing and Communications.md"
fulltext_path: "03fulltext/ISAC/IVFQQXLZ.md"
status:
  - Reading
rating: 四星
---

# An AFDM-Based Integrated Sensing and Communications

---

# 📌 Basic Information（基本信息）

## Author
Yuanhan Ni, Zulin Wang, Peng Yuan, Qin Huang（北京航空航天大学电子信息工程学院）

## Year
2022

## Source
ISWCS 2022｜DOI: 10.1109/ISWCS56560.2022.9940346

> Zotero 入口：zotero://select/library/items/IVFQQXLZ
> PDF 入口：zotero://open-pdf/library/items/Z2RV53DR
> 全文 Markdown：[[03fulltext/ISAC/IVFQQXLZ]]

## Research Area

- Integrated Sensing and Communications (ISAC)
- Affine Frequency Division Multiplexing (AFDM)
- Integrated waveform design
- Discrete Affine Fourier Transform (DAFT)

---

# 1. Abstract Summary（一句话总结）

> 该文把 AFDM 波形用于通感一体化系统，使其同时承载通信信息与感知目标，并设计**时域**与 **DAFT 域**两种参数估计方法；DAFT 域方法能在快时间轴上解耦时延与多普勒，即使在大多普勒场景下仍保持良好的感知性能。

---

# 2. Research Background（研究背景）

## 背景：

- 下一代（beyond 5G/6G）无线系统需要在高移动性场景下保持可靠通信，同时提升频谱与能量效率。
- ISAC 因能同时提升频谱/能量效率并获取环境信息，被视为 6G 的关键使能技术之一。

> 原文：
> "The integrated sensing and communications (ISAC) technique is one of the key enablers for beyond 5G/6G due to its ability to improve spectral and energy efficiencies and obtain information about the environment."

## Motivation（研究动机）

- 一体化波形设计是 ISAC 的基石，但既有波形在高移动性下有硬伤：
  - OFDM 加感知功能后，**时延与大多普勒在快时间轴耦合**，导致雷达图像峰值旁瓣比（PSLR）严重恶化。
  - OTFS 能应对大多普勒但与 OFDM 感知性能相近。
  - OCDM（chirp 类）无法在双选择性信道中获得全分集。

> 原文：
> "the peak-to-sidelobe level ratio (PSLR) of radar images may deteriorate severely in the high mobility scenarios due to the couple of delay and large Doppler shift in the fast time axis."
>
> 原文：
> "OCDM can not achieve full diversity in doubly selective channels."

## Application Scenario（应用场景）

- 高移动性通感一体场景（车载、无人机、高铁）
- 需要同时测距与测速的双功能波形设计

---

# 3. Research Question（研究问题）

这篇论文试图解决：

> 如何让一体化波形在**大 Doppler 频移**下仍能可靠估计目标的距离与速度，同时不牺牲通信功能？

核心问题：

- AFDM 波形如何承载感知功能（回波处理）？
- 时域与 DAFT 域两种估计路径的性能差异是什么？
- 整数与分数归一化多普勒如何合并以扩大无模糊多普勒范围？

---

# 4. Related Work（相关工作）

已有方法：

1. **LFM 嵌入通信信息**：经典雷达波形承载通信符号。
2. **OFDM + 符号除法**：抑制随机通信符号带来的旁瓣并估计距离/速度；符号共轭乘法（CCC）避免放大噪声基底。
3. **OTFS**：在时延-多普勒域复用符号，能处理大多普勒。
4. **OCDM**：chirp 类多载波，频选信道全分集，但双选信道不行。

现有不足：

- OFDM 在大多普勒下 PSLR 严重恶化（时延-多普勒耦合）。
- OCDM 在双选择性信道不能全分集。
- 亟需一种在双选信道下既全分集、又便于感知参数提取的波形。

---

# 5. Methodology（研究方法）

## Overall Idea

核心思想：

- 采用 **AFDM** 波形：信息符号在 **DAFT 域**复用，是 chirp 类多载波的一种。
- 同一波形既做通信（下行用户用既有 AFDM 信道估计/均衡/检测），又做感知（处理目标回波）。
- 提出**两种参数估计方法**，分别在时域与 DAFT 域处理回波。

## Model / Framework

系统模型：

- 单站感知：接收目标回波，目标 i 的散射系数、距离、相对速度、时延、多普勒频率分别记为 `hi, Ri, v_rel,i, τi = 2Ri/c, fd,i = 2*v_rel,i*fc/c`。
- 时域回波：

> 原文（式 3）：
> "r[n] = Σ_{i=1}^{P} h̃_i s[n−l_i] e^{j2πf_i n} + w_r[n]"

- 对每列做 N 点 DAFT 得到 DAFT 域样本矩阵 `Yr`，并写成矩阵形式输入-输出关系：

> 原文（式 6）：
> "Yr = Σ_{i=1}^{P} h̃_i H_i X D_i + W̃r"

- 整数归一化多普勒（`a_i = 0`）时，`H_i` 每行仅一个非零元素，位于 `q = (p + loc_i)_N`，其中 `loc_i = (2Nc1*l_i − α_i)_N`；分数多普勒时每行有 `2k_v+1` 个非零元素，峰值位置不变。

## Algorithm / Technique

采用：

- **时域方法：FCCR（Fast Cyclic Correlation Radar）**——对接收矩阵与发射矩阵逐列做 N 点 DFT，逐元素共轭相乘，再逐列 IDFT、逐行 N_sym 点 DFT，得到二维距离-多普勒矩阵（RDM）。处理增益 `Gp = N*N_sym`，最大无模糊多普勒 `±1/(2 T_AFDM)`。
- **DAFT 域方法**：利用 DAFT 域输入-输出关系，通过循环移位补偿时延带来的线性相位，逐候选时延 `l` 构造矩阵 `W_l`，用 CFAR 检测峰值；峰值行/列索引分别给出整数多普勒与分数多普勒。

## Key Steps

1. 对接收回波去 CPP、串并转换，得到矩阵 `R`。
2. 逐列做 N 点 DAFT，得到 `Yr`。
3. 在 DAFT 域对每个候选时延 `l`（共 `N_cp` 个）构造 `W_l`（式 11：`Wl = F^H((F Ll Yr)* ⊙ (F X))F`）。
4. 用 CFAR 判断是否存在目标，峰值位置给出时延估计 `l̂_i` 与整数多普勒 `α̂_i = 2Nc1*l̂_i − (1 − p̄_i)_N`、分数多普勒 `b̂_i = (k̄_i − 1 − N_sym/2)/N_sym`。
5. 合并整数与分数多普勒：`f̂d,i = (α̂i + âi)Δf = (β̂i + b̂i)Δf′`，并用相邻峰值的比较准则在 `β̂i,min / β̂i,max` 之间判定（图 2）。

---

# 6. Mathematical Model / Theory（理论模型）

## Problem Formulation

回波模型与 DAFT 域输入-输出关系如上（式 3、式 6），核心是：

> 原文（式 12）：
> "α̂i = 2Nc1*l̂i − (1 − p̄i)_N"
>
> 原文（式 14）：
> "f̂d,i = (α̂i + âi)Δf = (β̂i + b̂i)Δf′"

## Assumptions

假设：

-  chirp 周期前缀长度 `N_cp` 大于最大时延 `l_max`。
- 整数多普勒情形下 `H_i` 每行单非零元素；分数情形下峰值位置不变。
- `c1 = 2(α_max + k_v)+1 / 2N`，`c2` 取足够小的有理数，使 `N c2 (q_i² − p²)` 趋近于零。
- 目标为点目标模型。

## Optimization Objective

目标：

- 本文是**参数估计**而非优化问题，目标是准确估计目标的**距离（时延）**与**速度（多普勒）**，评价指标为雷达图像 PSLR 与图像 SNR。

---

# 7. Experiment / Evaluation（实验与验证）

## Dataset / Environment

数据：蒙特卡洛仿真，参数见表 I。

- 载波频率 `fc = 24 GHz`，子载波数 `N = 4096`，AFDM 符号数 `N_sym = 256`
- 带宽 `B = 93.1 MHz`，子载波间隔 `Δf = 22.729 kHz`
- AFDM 符号时长 `T = 44 µs`，CPP 时长 `Tcp = 2.75 µs`，总时长 `T_AFDM = 46.75 µs`
- 距离分辨率 `ΔR = 1.61 m`，速度分辨率 `Δv = 0.52 m/s`，处理增益 `Gp = 60.2 dB`
- 调制：16-QAM；`α_max = 2`，`k_v = 4`

## Baseline

比较方法：

- **OFDM + 符号除法**（symbol division method）[6]
- 本文**时域方法**（Pro-time-domain）
- 本文**DAFT 域方法**（Pro-DAFT-domain）

## Metrics

评价指标：

- 归一化雷达图像（radar image）与 **PSLR**（峰值旁瓣比）
- **Image SNR**：目标峰值与二维雷达图像平均噪声电平之比
- 速度估计误差（表 II）

## Results

主要结果：

- **图 3（雷达图像）**：当 `fd = 0.1Δf` 时，本文时域与 DAFT 域方法 PSLR 相近，略低于符号除法；当 `fd = 0.98Δf` 时，符号除法与时域方法 PSLR 严重恶化，而 **DAFT 域方法仍保持良好 PSLR**。
- **图 4（图像 SNR vs 输入 SNR）**：`fd = 0.98Δf` 时，符号除法与时域方法图像 SNR 严重下降，**DAFT 域方法仅轻微下降**；本文两种方法均优于符号除法。
- **图 5（图像 SNR vs 归一化多普勒 ν）**：低多普勒区（ν < 0.5）三者相近；随 ν 增大，符号除法与时域方法先严重下降后回升，在**整数 ν 处出现最低值（< 0 dB）**，而 **DAFT 域方法始终输出 > 50 dB**。
- **表 II（速度估计）**：`fd = 2.0Δf`（284.1 m/s，约 1022.74 km/h）时，时域/符号除法给出 −65.3 m/s 的错误估计（模糊），**DAFT 域方法给出 284.1 m/s 的正确估计**。
- **图 6（多目标）**：3 个目标（R = [400, 402, 402] m，v = [255, 255, 256] m/s），DAFT 域方法同时产生多幅雷达图像，每幅包含同距离目标的信息。

> 原文：
> "our DAFT-domain method can always output an image SNR greater than 50 dB, which verifies that our DAFT-domain method can work in both integer and fractional normalized Doppler shift scenarios."

---

# 8. Key Findings（核心发现）

作者主要贡献：

1. 首次把 AFDM 波形引入 ISAC，使其同时承载通信信息与感知功能。
2. 提出**时域（FCCR）**与 **DAFT 域**两种参数估计方法，后者利用 DAFT 域输入输出关系解耦时延与多普勒。
3. 提出**整数与分数归一化多普勒合并准则**（式 14-16 与图 2 判定准则），显著扩展给定 `T_AFDM` 下的最大无模糊多普勒。
4. 仿真验证：大 Doppler 下 DAFT 域方法在 PSLR、图像 SNR、速度估计正确性上均优于 OFDM 符号除法与时域方法。

---

# 9. Innovation Analysis（创新分析）

## Author's Innovation

作者认为：

- AFDM 在 DAFT 域复用符号，天然具备在双选择性信道中获得全分集的能力，这使其优于 OFDM 与 OCDM。
- 把"整数+分数多普勒分离估计再合并"作为扩展无模糊范围的手段，是本方法的关键技巧。

## My Evaluation

我的评价：

四星

创新程度：

中高

理由：

- 切中 OFDM-ISAC 的真实硬伤（大 Doppler 下时延-多普勒耦合导致 PSLR 崩塌），并用 DAFT 域方法给出了可验证的改进（图 5 中 > 50 dB 的稳定表现很有说服力）。
- 表 II 的速度估计对比（1022 km/h 场景）是该方法的亮点证据。

- 局限：仿真参数下本文方法在**低多普勒、高 SNR** 区的图像 SNR 反而不如符号除法（图 4 实线区），说明优势是有条件的；且论文为会议短文（6 页），通信侧仅引用既有工作未做联合性能分析。

---

# 10. Limitation（不足）

论文不足：

1. **低多普勒高 SNR 区优势不明显**：图 4 显示 `fd = 0.1Δf` 时符号除法在高 SNR 区反而输出更高图像 SNR，本文两种方法在 ~10 dB 后出现饱和。
2. **通信与感知未联合优化**：论文聚焦感知参数估计，通信侧直接沿用既有 AFDM 信道估计/均衡方法，未分析感知占空比对通信速率的实际影响。
3. **全仿真，无实测**：所有结论基于蒙特卡洛仿真与点目标模型。
4. **分数多普勒为近似处理**：DAFT 域方法由整数多普勒情形推导，分数情形仅靠数值验证，无理论误差界。
5. 会议短文，系统模型为单站单天线，未涉及多天线/多目标分辨极限。

未来可能改进：

- 在低多普勒区设计方法切换/融合策略，兼顾两种场景。
- 给出分数多普勒下的估计误差理论界。
- 联合通信速率与感知精度的波形参数优化。
- 扩展到多天线 AFDM-ISAC 与实测验证。

---

# 11. My Thoughts（我的思考）

## What I Learned

我学到了：

- 一体化波形的"高移动性短板"根源在于**快时间轴上的时延-多普勒耦合**，这是 OFDM 类波形的结构性问题，不是参数调优能解决的。
- AFDM/DAFT 域的价值在于：在该域中多普勒表现为**循环移位**，因此可以用简单的移位补偿+相关把时延和多普勒分离——这是"选对域"带来的结构性收益。
- "整数+分数分开估计再合并"是扩展无模糊多普勒范围（等效于解速度模糊）的通用思路，可迁移到其他波形。

## Connection With My Work

和我的研究/项目关系：

- 与本 Vault 的 ISAC 波形方向直接相关，特别是高动态 UAV 场景（参见 [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]]）。
- AFDM 可作为 OTFS 之外的另一候选波形，用于对比"时延-多普勒域"与"DAFT 域"两类方案。
- 与本 Vault 中 [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] 为同一波形族，可对照阅读方法差异。

## Possible Ideas

可能的新想法：

- 把本文的 DAFT 域估计与本 Vault 中 AFDM-ISAC 角度-时延-多普勒估计（张量方法）结合，看能否在低多普勒区补上短板。
- 研究低多普勒/高多普勒自适应切换准则，避免本文图 4 中的性能倒挂。
- 分析 AFDM 感知占空比与通信可达速率的折衷，补齐本文未做的联合分析。

---

# 12. Related Notes（关联知识）

相关概念：

- 暂无（当前 Vault 中尚无已建立的概念页）

相关论文：

- [[02vault/ISAC/AFDM-ISAC Angle-Delay-Doppler Estimation|AFDM-ISAC 估计]] — 同波形族，用张量 CP 分解做角度-时延-多普勒估计，本文仅距离-速度
- [[02vault/ISAC/ISAC Toward Dual-Functional Wireless Networks (Survey)|ISAC 综述]] — 提供一体化波形设计的整体分类与权衡框架
- [[02vault/UAV/ISAC from the Sky UAV Trajectory Design|ISAC from the Sky]] — 同为 ISAC，但该文优化轨迹，本文设计波形

---

# 13. Summary Card（快速复习）

## Problem

> OFDM-ISAC 在高移动性下，时延与大多普勒在快时间轴耦合，导致雷达图像 PSLR 严重恶化，距离/速度估计失效。

## Method

> 采用 AFDM 波形，在 DAFT 域复用符号；提出时域（FCCR）与 DAFT 域两种参数估计，后者利用 DAFT 域中多普勒表现为循环移位的性质分离时延与多普勒，并合并整数/分数多普勒以扩展无模糊范围。

## Result

> `fd = 0.98Δf` 与 `ν = 2.0` 的大多普勒场景下，DAFT 域方法 PSLR 保持良好、图像 SNR 始终 > 50 dB，并正确估计 284.1 m/s（1022.74 km/h）的速度，而对比方法出现模糊。

## Importance

> 证明了 AFDM 作为一体化波形在高移动性场景的结构性优势，为 6G 高动态 ISAC 提供了 OFDM/OTFS/OCDM 之外的新选项。

## Flash Card

Q:
这篇论文解决什么问题？

A:
解决 OFDM-ISAC 在高多普勒下时延-多普勒耦合导致雷达图像 PSLR 恶化、测距测速失效的问题。

Q:
核心方法是什么？

A:
用 AFDM 波形，在 DAFT 域估计参数：多普勒表现为循环移位，通过移位补偿+相关分离时延与多普勒，并合并整数/分数多普勒扩展无模糊范围。

Q:
最大贡献是什么？

A:
验证了 AFDM 在大多普勒下仍保持 > 50 dB 图像 SNR 与正确速度估计，而 OFDM 符号除法与时域方法失效。

---

## 证据溯源说明

- 元数据来自 Zotero 条目 `IVFQQXLZ`，PDF 附件 `Z2RV53DR`（已挂载至 `F:\XWCos\zotero\storage\Z2RV53DR`）。
- 原文引用均取自全文 Markdown [[03fulltext/ISAC/IVFQQXLZ]]，由 Zotero 附件 PDF 经 pypdf 提取。
- PDF 页码未验证（pypdf 提取不含可靠页码映射），故未标注页码。
- 仿真数值（表 I/表 II、图 3-6 结论）均直接引自原文；未做推测或外推。
