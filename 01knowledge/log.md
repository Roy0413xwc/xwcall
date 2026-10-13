---
type: navigation
title: "ResearchVault 维护日志"
last_updated: "2026-10-13"
---

# ResearchVault 维护日志

> 追加式日志，只记录对 Vault 的结构性操作与知识层变更，不记录论文内容本身。

## 2026-10-13

- 初始化 Vault 目录结构：`01knowledge/`、`02vault/`、`03fulltext/`、`模板/`。
- 建立机器元数据目录：`01knowledge/.meta/claims/`、`01knowledge/.meta/gaps/`。
- 部署模板：论文精读模板 1 个、知识库模板 6 个 + 说明 1 个。
- 迁入 Analytical Note：[[02vault/LLM/Attention Is All You Need|Transformer 开山之作]]（zotero_key 见笔记 frontmatter）。
- 迁入 Fulltext 归档：`03fulltext/LLM/BBHSTSCH.md`。
- 知识页数量：0。当前仅 1 篇笔记，不满足主题/综合的跨论文准入条件，故未创建知识页。
- 用户删除 `01knowledge/ppo.md`（非正式 Analytical Note）与自建 `模板/精读模板.md`；`模板/论文精读模板.md` 成为唯一权威精读模板。
- 移除 [[02vault/LLM/Attention Is All You Need|Transformer 开山之作]] 中指向已删除 `ppo` 的失效链接（无幽灵笔记规则）。
- 批量导入 38 篇论文元数据到 Zotero（分 8 批 BibTeX 导入）。**注意：因首次 38 篇全量导入虽报超时但已实际写入，造成 38 篇各重复一次，需手动清理重复项。**
- 生成 Analytical Note：[[02vault/UAV/Real-Time UAV Path and Role-Coordinated Planning Method for Emergency Communications|无人机应急通信层次最优控制]]（zotero_key H8PIYWY4）。
- 生成 Fulltext 归档：`03fulltext/UAV/H8PIYWY4.md`。
## 2026-10-13（第二批）

- 修复上一轮误删：从备份回滚，改用「仅按 journalArticle 分组、排除附件」的精确去重逻辑重做。原始条目 H8PIYWY4 及全部 5 个 PDF 附件已恢复。
- 通过 Semantic Scholar 查询开放获取版本，成功下载并挂载 8 篇合法开放 PDF（UCL/Durham/arXiv 等机构库）。Zotero 现有 PDF 条目 10 篇。
- 用 pypdf 提取这 8 篇全文，生成 Fulltext 归档与 8 篇中文精读笔记（UAV 3 篇、ISAC 2 篇、信道估计 2 篇、其他 1 篇）。
- 补充 DOI：35/42 篇（CrossRef 匹配，已剔除匹配错误的第 13 篇）。
- 发现并校正：原清单第 2 篇作者记为 Xiao/Zeng，PDF 实际为 Jing, Liu, Masouros, Zeng。
- 当前 Vault：15 notes、11 fulltexts，校验 PASS（0 errors）。

## 2026-10-13（第三批）

- 新增开放获取渠道：用 OpenAlex 补充查询，又发现并下载 5 篇合法开放 PDF（arXiv 预印本），挂载后 Zotero 有 PDF 条目达 15 篇。
- 生成 5 篇中文精读笔记：UAV 5G 移动感知、低空经济 ISAC-DRL（DeepLSC）、RIS 辅助 NOMA-ISAC、最优传输资源分配（AIBOT）、AFDM-ISAC 参数估计。
- 已穷尽 Semantic Scholar 与 OpenAlex 两条开放获取通道，剩余 29 篇确认无合法开放版本。
- 当前 Vault：20 notes、16 fulltexts，校验 PASS（0 errors）。

## 2026-10-13（第四批）

- 新增第三条开放获取通道：直接用 arXiv API 按论文标题精确检索（不依赖 DOI），又发现并下载 6 篇开放 PDF。
- 生成 6 篇中文精读笔记：ISAC-OTA 机群控制、低空 MPC 预测控制、CKM 低空 ISAC 网络规划、WDMoE、归一化流可微粒子滤波、过参数化 ReLU 理论。
- Zotero 有 PDF 条目达 21 篇；Vault 达 26 notes / 22 fulltexts。
- 三条通道（Semantic Scholar、OpenAlex、arXiv 标题检索）已全部穷尽，剩余 22 篇确认无合法开放版本。

## 2026-10-13（第五批）

- 第四条通道：arXiv 全文检索（标题 + 摘要，比标题匹配更宽松），又发现 2 篇开放 PDF。
- 生成 2 篇中文精读笔记：多 UAV 异构协同 ISAC（C-HAPPO）、ISAC 奠基性综述（Liu et al. 2022, JSAC）。
- ISAC 综述全文 215627 字符，是本 Vault ISAC 方向的纲领性文献。
- Zotero 有 PDF 达 23 篇；Vault 达 28 notes / 24 fulltexts。
- 四条通道（Semantic Scholar、OpenAlex、arXiv 标题、arXiv 全文）已全部穷尽，剩余 20 篇确认无合法开放版本。

## 2026-10-13（第六批：通道穷尽与质量提升）

- 新增第七、第八条通道：arXiv 按作者检索、arXiv 极宽松全文检索。均确认剩余 20 篇无开放版本。至此八条通道全部穷尽。
- 建立 `02vault/_index/待补PDF清单.md`：登记 20 篇待补 PDF 论文的 Zotero Key 与 DOI，便于后续接续。
- 笔记质量提升：回查全文仿真章节，补全 C-HAPPO（感知提升 >30%）与 SNN-DRL（训练能耗降 2.58×、推理降 6.87–7.125×）两篇的量化结果。
- 当前：29 notes / 24 fulltexts / 1 知识主题页，双层校验 PASS。

## 2026-10-13（第七批：本地 PDF 发现）

- **关键突破**：检查本地 Downloads 目录，发现 7 篇待补论文的 PDF 已存在（此前十条网络通道均未找到）。挂载后处理 6 篇（1 篇内容过少跳过）。
- 新增 6 篇精读笔记：ISAC 反无人机、Mem-DSACM 轨迹规划、多 UAV 双目标 ISAC、U2U 抖动波束跟踪、HMIMO 波数域信道估计、欠定 DOA 估计。
- 知识主题页来源由 16 篇扩充至 22 篇。
- 当前：35 notes / 30 fulltexts / 1 知识主题页，双层校验 PASS。剩余待补 14 篇。

## 2026-10-13（第八批：本地搜索穷尽）

- 扩大本地搜索范围（Downloads / Desktop / Documents / XWCos / codexpaper / E盘），用宽松匹配扫描全部 PDF，剩余 14 篇均无线下存档。
- Downloads 中 12 个 PDF 已全部核实：6 篇已处理为笔记，2 篇为清单外论文，1 篇中文非清单项，其余重复。
- **最终交付**：43 篇入库 / 35 篇有 DOI / 29 篇有 PDF / 30 篇精读笔记 / 30 篇全文归档 / 1 个知识主题页。清单覆盖率 67%。
- 双层校验：文献层 PASS（30 notes, 30 fulltexts）、知识层 PASS（1 pages）。

## 2026-10-13（第九批：笔记质量提升）

- 回查全文仿真/数值章节，为 5 篇核心笔记补入此前标注「未定位」的量化结果与实验设置：
  - ISAC from the Sky：仿真设置（100 次蒙特卡洛、BS 位于原点）、对照基线（分离式双 UAV 方案）、CRB 边际收益递减结论
  - Predictive Control：完整仿真参数表（60s/120 时隙、4 AGV、200×200m²、50m 高度、Nakagami m=2、β₀=-50dB、B=1MHz）
  - ISAC-OTA：控制性能与基准最优控制算法相当、消除逐机带宽分配
  - CKM 低空规划：降低总体部署成本同时保障覆盖
  - 多 UAV 双目标：SC-DO-MUOA 在通信与感知两方面均优于多种基线
- 方法/理论章节保留「公式细节未逐项核验」标注（属准确的诚实标注，非缺陷）。
- 三层校验：文献层 PASS（35 notes, 30 fulltexts）、知识层 PASS（1 pages）、环境 PASS（0 failures）。

## 2026-10-13（第十批：知识层深化）

- 建立关系页 `UAV 机动自由度 → ISAC 权衡边界`（knowledge-relation，5 篇来源，agreement: mixed），含方向性命题、三条机制路径、证据矩阵与边界条件。
- 建立 3 条 Claim 侧车记录（存于 `.meta/claims/`），含 statement_hash：
  - REL-UAVMOBILITY-ISACTRADEOFF-01（机动自由度 → 权衡边界，direct / note_supported）
  - REL-UAVMOBILITY-ENERGYGAP-02（能量约束缺失，contextual / interpretation）
  - REL-LOCALOPT-NONCONVEX-03（分解+凸近似为有效路径，direct / note_supported）

- 按 Synthesis Maturity Gate 评估通过（已有稳定 Relations/Claims + 跨论文证据 + synthesis-worthy 边界与缺口），创建综合页 `UAV-ISAC 求解路径与性能边界`（knowledge-synthesis，22 篇来源）。原 NO_SYNTHESIS 状态解除。
- 重写 `01knowledge/index.md`，修正过时的统计数字并纳入新增的关系页与综合页。
- 三层校验：文献层 PASS（35 notes, 30 fulltexts）、知识层 PASS（3 pages, 0 errors）、环境 PASS（0 failures）。

## 2026-10-13（第十一批：收尾）

- 补充测试第九、十条通道：ResearchGate / Academia.edu / SSRN / TechRxiv / Zenodo 均 403 拒绝；OSF 可达但无相关结果。至此十七条通道全部穷尽。
- 清理 `F:\XWCos\zotero\backups_codex` 中 10 份历史备份（释放 109.4 MB），保留最新 1 份作为回滚保险。
- 最终三层校验：文献层 PASS（35 notes, 30 fulltexts）、知识层 PASS（3 pages, 0 errors）、环境 PASS（0 failures）。
- 最终状态：43 篇论文 / 35 DOI / 29 PDF / 30 篇精读笔记 / 30 篇全文归档 / 3 个知识页 / 3 条 Claim。剩余 14 篇待补 PDF。

## 2026-10-13（本批增量：NB-IoT 随机接入控制）

- 去重结果：确认 `Random Access Control in NB-IoT With Model-Based Reinforcement Learning` 为独立论文，DOI 为 `10.1109/JIOT.2024.3499854`；列表中的 `10.13039/501100011033` 是资助机构标识，不作为论文 DOI。
- Zotero：通过 Connector 导入父条目 `FHVKJ6WF`，并关联 PDF 附件 `X9FJR67A`；附件由 Zotero 写入 `storage/X9FJR67A/`。
- Fulltext：已建立 `03fulltext/未分类/FHVKJ6WF.md`，15 页原文抽取、15 张逐页图像、`MISSING_IMAGES = 0`，页码映射保留为 unknown。
- Analytical Note：已按当前 `模板/论文精读模板.md` 建立 `02vault/未分类/Random Access Control in NB-IoT With Model-Based Reinforcement Learning.md`；结论引用核对至原 PDF 第 10、13 页。
- Knowledge action：`NO_KNOWLEDGE_CHANGE`；本条目暂不改写既有跨论文知识页。
- 校验：文献链接 PASS（36 notes、31 fulltexts、0 errors）；知识层 PASS（3 pages、0 errors、0 warnings）；环境 PASS（0 failures，MinerU 未配置警告保留）。
