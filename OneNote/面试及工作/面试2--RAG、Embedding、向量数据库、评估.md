---
onenote-id: ce371dbe-1462-4ed1-9d92-7e87b93f6ada:1
---
**第2天：RAG 完整体系**

RAG 是五天内最值得重点学习的内容，因为它容易落地、适合做项目，也容易在面试中展开。

**上午：RAG 总流程**

完整流程：

\[

\text{文档}

\rightarrow

\text{解析}

\rightarrow

\text{切分}

\rightarrow

\text{向量化}

\rightarrow

\text{建立索引}

\]

查询时：

\[

\text{问题}

\rightarrow

\text{检索}

\rightarrow

\text{重排序}

\rightarrow

\text{组装上下文}

\rightarrow

\text{LLM生成}

\]

数学表示：

\[

D_q=\operatorname{Retrieve}(q,D)

\]

\[

y=\operatorname{LLM}(q,D_q)

\]

需要理解：

- RAG 不直接修改模型参数；
- 知识库更新后通常不需要重新训练模型；
- RAG 适合企业文档、规章制度、技术资料；
- 微调主要改变模型行为，RAG主要补充动态知识。

**中午：Embedding 与相似度**

文本经过 Embedding 模型得到向量：

\[

q\rightarrow \mathbf q,\qquad

d_i\rightarrow \mathbf d_i

\]

余弦相似度：

**\[**

**\boxed{**

**\operatorname{sim}(\mathbf q,\mathbf d_i)**

\frac{

\mathbf q^\top\mathbf d_i

}{

\|\mathbf q|_2|\mathbf d_i|_2

}

}

\]

相似度越高，通常表示语义越接近。

需要区分：

- 关键词检索：BM25；
- 稠密检索：Embedding；
- 混合检索：关键词与向量检索结合；
- Reranker：对初步召回结果重新排序。

**下午：文档切分和检索**

重点学习：

**Chunk Size**

切分过小：

- 上下文不完整；
- 一个知识点被切断。

切分过大：

- 噪声增加；
- 检索不够精确；
- 占用更多上下文。

**Chunk Overlap**

相邻片段保留部分重叠，减少语义被边界截断的问题。

**Top-k**

检索前 (k) 个片段：

- (k) 太小：可能漏掉答案；
- (k) 太大：增加噪声和 Token 成本。

**晚上：RAG 评估**

检索指标：

**Recall@k**

**\[**

**\operatorname{Recall@k}**

\frac{

\text{前}k\text{个结果中召回的相关内容数}

}{

\text{全部相关内容数}

}

\]

**Precision@k**

**\[**

**\operatorname{Precision@k}**

\frac{

\text{前}k\text{个结果中相关内容数}

}{k}

\]

**MRR**

若第一个正确答案排名为 (\operatorname{rank}_i)：

**\[**

**\operatorname{MRR}**

\frac{1}{N}

\sum_{i=1}^{N}

\frac{1}{\operatorname{rank}_i}

\]

生成部分关注：

- 忠实性；
- 回答相关性；
- 是否引用来源；
- 是否出现幻觉。

**第2天产出**

画一张自己的 RAG 架构图，最好结合你的背景：

面向通信标准、论文或操作系统文档的智能问答系统。

并能解释：

- 为什么采用 RAG，而不是微调；
- Chunk Size 如何设置；
- 为什么需要 Reranker；
- 如何评价系统效果。