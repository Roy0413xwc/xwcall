我没有直接在 Zotero 里创建“论文目录”或手动改数据库。当前结构分两部分：

- Zotero 本身的分类目录（Collection）：通过 Zotero 本地 API/桌面端读取和使用，目录记录保存在 `F:\XWCos\zotero\zotero.sqlite`。
- Zotero 附件目录：Zotero 自动按条目 Key 在 `F:\XWCos\zotero\storage\` 下创建，例如 `storage\1A1B49FC\`。PDF 下载或拖入 Zotero 后，Zotero 会把文件复制到对应目录，并在数据库中建立附件关联。目录名不是论文标题，而是 Zotero 的内部 Key。

我建立的是 Obsidian 侧的目录和 Markdown 文件：

- `F:\XWCos\obisidian\xwcall\xwcall\02vault\`：精读笔记
- `F:\XWCos\obisidian\xwcall\xwcall\03fulltext\`：全文 Markdown 归档
- `F:\XWCos\obisidian\xwcall\xwcall\01knowledge\`：知识索引和日志
- `F:\XWCos\obisidian\xwcall\xwcall\模板\`：模板

这些 Markdown 文件里的 `zotero://select/...` 或 Zotero Key 链接，只是指向 Zotero 条目的引用，不会把文件重新复制进 Zotero。

目前 Zotero 本地 API 正常运行，版本为 10.0.6，数据目录就是：

`F:\XWCos\zotero`

所以，论文 PDF 如果通过 Zotero 下载，实际由 Zotero 写入 `storage\<Zotero条目Key>\`；我生成的笔记和全文归档则写入 Obsidian Vault。