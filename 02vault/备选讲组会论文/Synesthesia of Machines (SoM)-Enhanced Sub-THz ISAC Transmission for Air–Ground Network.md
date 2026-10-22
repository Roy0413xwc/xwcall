---
date_added: "2026-10-22"
priority: 中
status: 待读
tags:
- 论文笔记
- 信息与通信工程
title: "Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network"
author: "Zonghui Yang; Shijian Gao; Xiang Cheng; Liuqing Yang"
year: "2026"
source: "IEEE Transactions on Wireless Communications"
doi: "10.1109/TWC.2025.3649505"
type: literature-note
zotero_key: "S9X64ASI"
pdf_key: "2URLRKQX"
collection: "备选讲组会论文"
note_path: "02vault/备选讲组会论文/Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network.md"
fulltext_path: "03fulltext/备选讲组会论文/S9X64ASI.md"
theme: "Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propaga"
study_area: "Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network"
data_source: "按论文实验章节报告；具体数据集/测量数据名称需全文核实"
methodology: "Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics"
core_variable: "论文系统模型中的优化/预测变量；需查原文模型章节"
key_finding: "rs and targets, while a customized multi-modal learning algorithm optimizes the hybrid precoder. A new metric is proposed for comprehensive performance evaluation. Extensive experiments demonstrate that the proposed scheme signiﬁcantly improves ISAC efﬁciency."
relevance: "组会候选；可供信息与通信工程研究问题筛选"
---
# Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network

> [!abstract] 一句话概括
> Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.

## 0. 阅读导航

- [ ] 第一遍：标题、摘要、引言、结论
- [ ] 第二遍：系统模型、问题建模、算法流程
- [ ] 第三遍：推导公式、核对仿真设置、复现核心结果
- [ ] 记录疑问、不足与可借鉴想法

**阅读目的：** 组会论文筛选与 ISAC/无线通信研究方法学习。  
**阅读结论：** `精读候选`（读完当前可访问全文；复现状态待定）

## 1. 文献信息

| 项目 | 内容 |
|---|---|
| 论文标题 | Synesthesia of Machines (SoM)-Enhanced Sub-THz ISAC Transmission for Air–Ground Network |
| 作者 | Zonghui Yang; Shijian Gao; Xiang Cheng; Liuqing Yang |
| 年份 | 2026 |
| 期刊 / 会议 | IEEE Transactions on Wireless Communications |
| DOI / 链接 | 10.1109/TWC.2025.3649505 |
| 研究方向 | 由论文题名与摘要界定，见下文研究问题 |
| 场景 | Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics |
| 核心方法 | 以摘要与全文方法章节为依据；详细章节：B. Network Architecture; C. Comparison Methods |
| 代码 / 数据 | 当前全文材料未核实公开代码；数据/代码可用性需查论文声明 |
| Zotero 条目 | [S9X64ASI](zotero://select/library/items/S9X64ASI) · [PDF](zotero://open-pdf/library/items/2URLRKQX) · 全文 Markdown：[[03fulltext/备选讲组会论文/S9X64ASI]] |

**论文档次与发表信息核验：** 期刊与 DOI 取自现有 Zotero/全文元数据；分区/影响力和代码开放状态未独立核验。

## 2. 快速判断：这篇论文值不值得精读？

### 2.1 研究问题

- **应用场景：** Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-modal sensing fusion fr
- **具体问题：** 论文摘要明确指出的任务与目标见下方原文摘录；变量和约束按系统模型章节进一步核读。
- **为什么重要：** 作者将该问题置于摘要所述通信/感知场景，试图改善现有方法在该场景下的限制。
- **现有方法的主要缺陷：** However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations.
- **作者的核心思路：** This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.

### 2.2 30 秒总结

> Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.

### 2.3 初步评价

- [x] 研究问题可由摘要识别
- [ ] 方法差异与最接近工作的比较已完成
- [ ] 数学假设与实验公平性已逐项复核
- [ ] 可复现性已验证

**初读决定：** 值得围绕研究问题与方法章节精读。  
**理由：** 当前全文提供了摘要和结构化章节，可定位方法及实验；公开代码、强基线公平性与参数复现仍需核验。

## 3. 研究背景与文献脉络

### 3.1 背景与动机

- 研究背景：Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works.
- 现实需求或理论动机：论文摘要描述的目标场景与性能需求。
- 关键难点：However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations.
- 现有方法不足：以作者摘要表述为线索；完整分类需核读 Related Work。

### 3.2 相关工作分类

| 方法类别 | 代表性工作 | 基本思路 | 优点 | 局限 |
|---|---|---|---|---|
| 作者相关工作类别 | 见原文 Related Work 引文 | 本笔记未逐篇核对 | 待核实 | 待核实 |
| 传统/模型驱动基线 | 见实验基线章节 | 需逐项提取 | 待核实 | 待核实 |
| 学习型/近期方法 | 见实验基线章节 | 需逐项提取 | 待核实 | 待核实 |

### 3.3 研究空白（Research Gap）

作者声称的研究空白以摘要中对现有方法不足的描述为准；具体空白条目及其与最近工作的差别尚需逐条对照引言和相关工作。**我的判断：** 目前证据足以确认任务动机，不足以单独证明研究空白的新颖性。

## 4. 创新点拆解

| 创新点 | 具体内容 | 相比已有工作的差异 | 支撑证据 | 我的评价 |
|---|---|---|---|---|
| 1 | This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission. | 需核读最近邻工作 | 摘要及方法章节 | 暂定，待对照 |
| 2 | 论文摘要提及的模型/系统设计 | 需核读贡献与消融 | 摘要及实验章节 | 暂定 |

**创新类型：** 暂不勾选；需基于模型、算法、理论和实验逐项判定。  
**最值得借鉴的创新：** 论文把摘要中的目标问题与其提出的方法相连接。  
**创新是否扎实：** 需检查消融、复杂度、基线与假设适用范围后再判断。

## 5. 系统模型与问题建模

### 5.1 系统架构

- 网络/系统组成：按摘要描述为 Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-mod
- 节点数量与部署方式：需查系统模型原文。
- 链路与信号流程：需查系统模型/信号模型原文。
- 关键假设：不从摘要推断；待核对原文。
- 系统模型图说明：尚未从 PDF 图像提取，见全文 Markdown 及 Zotero PDF。

### 5.2 信道与信号模型

信道类型、路径损耗、衰落、噪声、CSI 假设、估计方式和移动性参数均需从原文模型公式核实；本次可访问的 Fulltext 是 PDF 文本抽取，未解析公式图像。关键符号表：**待按原文逐项补齐，避免猜测。**

### 5.3 通信 / 感知 / 定位指标

摘要明确报告的优化目标/指标：Extensive experiments demonstrate that the proposed scheme significantly improves ISAC efficiency. 其余指标须对照评价指标章节。

### 5.4 优化问题 / 学习任务

**决策变量、目标函数、约束、连续/离散类型与非凸性：** 需按原文问题建模章节抄录并解释；此处不依据摘要猜写数学式。  
**近似/松弛及理想化假设：** 待核对。

## 6. 方法与算法

### 6.1 方法总览

**方法名称：** This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.  
**核心思想：** Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.  
**输入/输出：** 依系统模型与方法章节核实。  
**关键变化：** 作者摘要指出的差异为：However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations.

### 6.2 算法流程

1. 按论文定义获取系统状态、观测或数据。
2. 执行摘要与方法章节所述模型/算法：B. Network Architecture; C. Comparison Methods。
3. 按原文目标更新决策/预测结果。
4. 约束处理、训练细节和停止条件需查算法框/正文。
5. 输出为论文研究任务所需的通信、感知或学习结果。

### 6.3 按方法类型补充

方法类型及其训练/求解流程：以论文上述方法章节为准。状态/输入、动作/输出、奖励/损失、网络结构、数据生成、复杂度及泛化条件需在原文对应小节核实；当前不将标题或摘要替代算法细节。

### 6.4 关键公式精读

| 公式编号 | 公式作用 | 推导思路 | 使用前提 | 是否理解 |
|---|---|---|---|---|
| 待核对 | 需从原文公式定位 | 当前文本抽取未可靠解析公式版式 | 待核实 | 否 |

**最关键公式 / 不理解概念：** 待按原文公式和符号表补录。

## 7. 仿真与实验分析

### 7.1 实验设置

| 项目 | 设置 | 依据/合理性 |
|---|---|---|
| 场景与拓扑 | 摘要描述的应用场景 | 具体参数待查实验章节 |
| 载频/带宽/功率/噪声 | 未从摘要确认 | 待核实原文表格 |
| 天线/用户/目标 | 未从摘要确认 | 待核实 |
| 数据/训练/随机种子 | 未从摘要确认 | 待核实 |
| 评价指标 | Extensive experiments demonstrate that the proposed scheme significantly improves ISAC efficiency. | 以实验定义为准 |

### 7.2 对比基线

| 基线方法 | 是否公平 | 差异 |
|---|---|---|
| 原文列出的基线 | 未核实 | 需读实验设置和实现说明 |

### 7.3 关键结果

| 图/表 | 参数变化 | 趋势 | 作者解释 | 我的理解 |
|---|---|---|---|---|
| 摘要结果 | 见摘要 | Extensive experiments demonstrate that the proposed scheme significantly improves ISAC efficiency. | 作者摘要报告 | 需与原图、实验条件核对 |

### 7.4 结果是否可信？

基线公平性、统计重复、消融、复杂度和场景外泛化尚未在此笔记逐项核验。最有说服力结果与最缺少实验需回到实验章节和图表判读。

## 8. 局限性与可改进方向

### 8.1 论文局限

目前能确认的限制为摘要指出的现有问题；论文自身局限不能仅凭摘要推断。需要核读局限声明、假设和实验范围，重点检查模型假设、算法复杂度、训练/部署差异及工程开销。

### 8.2 可以进一步研究的问题

| 改进方向 | 当前不足 | 可行方案 | 预期收益 | 难度 |
|---|---|---|---|---|
| 更真实信道/场景 | 适用范围待核实 | 加入不确定性或实测 | 检验鲁棒性 | 中 |
| 更强基线与消融 | 公平性待核实 | 统一资源和训练预算 | 增强证据 | 中 |

### 8.3 可形成的研究选题

**研究问题：** 在论文任务下评估更真实场景和资源约束的影响。  
**与本文区别：** 需精读后明确。  
**最小验证实验：** 复现一项关键图并改变一个关键假设。  
**风险：** 取决于代码、数据和系统参数可获得性。

## 9. 复现记录

- [ ] 找到代码/数据（当前未核实）
- [ ] 记录环境与依赖
- [ ] 复现系统模型
- [ ] 复现核心图
- [ ] 与原文结果核对

**硬件/软件环境：** 未执行复现。  
**代码仓库：** 未核实。  
**关键参数与差异：** 待复现后记录。

## 10. 组会汇报提纲

1. 背景与动机：Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works.
2. 现有工作不足：However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations.
3. 系统模型：根据原文系统模型图和公式补充。
4. 核心方法：This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.
5. 关键结果：Extensive experiments demonstrate that the proposed scheme significantly improves ISAC efficiency.
6. 创新与不足：创新暂定，局限需审读。
7. 讨论问题：关键性能提升依赖哪些假设，能否在更真实场景复现？

**用 1 分钟讲清：** Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.  
**组会讨论：** 原文实验是否覆盖了目标部署场景中的关键不确定性？

## 11. 最终总结与个人收获

### 11.1 三句话总结

- **问题：** Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works.
- **方法：** This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission.
- **结论：** Extensive experiments demonstrate that the proposed scheme significantly improves ISAC efficiency.

### 11.2 我真正学会了什么？

需精读模型、算法和结果后再填写，当前先记录作者摘要中的研究路径，不把它当作个人已掌握结论。

### 11.3 对自己的课题有什么帮助？

可能可作为研究问题、方法或基线的候选参考；需先确认任务、假设和数据与自身课题可比。  
**最值得记住：** Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmi  
**总体评价：** 暂不打分；**是否推荐：** 组会候选，推荐前需核验方法与实验。

## 12. 关联笔记

### 相关论文

- 同一 collection 中的直接关联论文尚未完成全文对读，暂不建立推测性链接。

### 相关概念

- [[ISAC]]
- [[无线通信]]
- [[深度学习]]

### 相关研究方向

- [[信息与通信工程]]

## 13. 阅读后续行动

- [ ] 补读系统模型与关键公式
- [ ] 对照 Related Work 选择最接近的 3 篇论文
- [ ] 核验实验设置、强基线及消融
- [ ] 检查代码/数据并决定是否复现

**下一步最具体的行动：** 依据全文章节逐项补充系统参数、公式和实验图表证据。  
**计划完成日期：** 待安排

---

### 原文证据

> Integrated sensing and communication (ISAC) at sub-THz frequencies is crucial for future air-ground net- works. However, optimizing ISAC performance while managing operational latency is challenging due to unique propagation characteristics and hardware limitations. This paper introduces a multi-modal sensing fusion framework inspired by synesthesia of machine (SoM) to enhance sub-THz ISAC transmission. By exploiting

来源：[S9X64ASI 全文 Markdown](03fulltext/备选讲组会论文/S9X64ASI.md)；PDF 页码依全文映射：verified by PDF page index。引文截取自原文摘要；结论和实验细节需回到全文相应章节核对。
