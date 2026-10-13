---
type: navigation
title: "待补 PDF 论文清单"
last_updated: "2026-10-13"
---

# 待补 PDF 论文清单

> 以下论文已完成 Zotero 元数据入库（含 DOI），但**无合法开放获取版本**，因此尚未生成精读笔记。
> 经 **十条独立开放获取通道**检索，均确认无合法开放 PDF：
>
> | 通道 | 检索方式 |
> |---|---|
> | 1 | Semantic Scholar（按 DOI） |
> | 2 | OpenAlex（按 DOI） |
> | 3 | arXiv API（按标题精确） |
> | 4 | arXiv API（全文检索） |
> | 5 | Semantic Scholar（按标题） |
> | 6 | Unpaywall（经 CrossRef 重查 DOI） |
> | 7 | arXiv API（按作者 + 关键词） |
> | 8 | arXiv API（极宽松全文，人工核验候选） |
> | 9 | CORE（全球开放获取仓储聚合） |
> | 10 | DOAJ（开放获取期刊目录） |
>
> 根本原因：这批论文均发表于 IEEE 付费期刊（TCOM / TWC / JSAC / TSP 等），IEEE Xplore 直连返回 418（反爬）与 202（需订阅）。
> 补齐 PDF 后可立即生成精读笔记。

## 如何补齐

1. **机构权限**：在 Zotero 中选中条目 → 右键「查找可用 PDF」（需 IEEE 订阅）
2. **手动下载**：从 IEEE Xplore 下载后拖入 Zotero 条目
3. **本地目录**：若已有 PDF，告知目录路径即可批量挂载

## 清单（20 篇）

| # | Zotero Key | 标题 | DOI |
|---|---|---|---|
| 1 | `YGBNI2SI` | Farhadi 等 - 2025 - Joint Beamforming and Resource Allocation | — |
| 2 | `8RYAJQCF` | 3 Environment Sensing Considering the Occlusion Effect A Mul | — |
| 3 | `TD63PRHY` | OFDMA Uplink Scheduling in IEEE 802.11ax Networks | 10.1109/icc.2018.8422767 |
| 4 | `GMZWY6BE` | Near-Field Beamforming With 3D Velocity Sensing and Localiza | 10.1109/wcnc61545.2025.10978527 |
| 5 | `6B6VKJMD` | Huang 等 - 2026 - LLM in V2I A Data-Driven Predictive Beamfor | — |
| 6 | `8GWNV2BD` | Passive Human Tracking With WiFi Point Clouds | 10.1109/jiot.2024.3487193 |
| 7 | `YRL9LYJZ` | NOMA-Empowered Integrated Sensing and Communication With Mov | 10.1109/twc.2025.3637741 |
| 8 | `H2KDVSZE` | Optimal Transport Framework for ISAC in Low-Altitude Network | 10.1109/tcomm.2025.3642742 |
| 10 | `4E3GAEAI` | Situation-Aware Hybrid Sensing and Position Control for UAV- | 10.1109/twc.2026.3661956 |
| 12 | `DZKZL84H` | A One-Bit MIMO Detector for Accurate Static Target Localizat | — |
| 13 | `687LW855` | Xu 等 - 2022 - A Deep Reinforcement Learning Approach for Int | — |
| 14 | `BRK2A7ZC` | Wang 等 - 2024 - Deep Reinforcement Learning Based Resource A | — |
| 15 | `ZZM2CM8V` | Yang 等 - 2024 - Deep Reinforcement Learning-based Resource A | — |
| 20 | `Z6WYFP9C` | Joint Beamforming and UAV Deployment Optimization for ISAC-E | 10.1109/twc.2026.3694912 |

## 完成后

补齐 PDF 后，按 `zotero-fulltext-archiver` → `zotero-analytical-writer` 流程即可生成：

- `03fulltext/<collection>/<zotero_key>.md`（全文归档）
- `02vault/<collection>/<paper>.md`（中文精读笔记）