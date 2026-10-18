---
onenote-id: 94dde383-ad61-419d-acc2-2ee0db462a32:1
---
Pdf1

普通图：节点 + 边

有向图：边有方向，比如转账、论文引用

二部图：两类节点之间连边，比如学生—课程

异构图：节点/边有多种类型，比如作者—论文—会议

\1. 图 = 节点 + 边，用来表达关系

\2. 很多现实问题都能建成图：社交、分子、交通、知识图谱、推荐

\3. 建图时要决定：节点是什么？边是什么？有向还是无向？是否异构？

\4. Graph ML 的任务：节点级、边级、子图级、图级

\5. 图比图片/文本难：没有固定节点顺序，结构不规则，大小不固定

\6. 模型要利用的不只是特征，还有节点在图中的结构位置

Pdf2

Node embedding 就是把图里的每个节点，变成一个向量，并且让图中“相似”的节点在向量空间里也相近。

Node Embedding = 给每个节点学习一个向量

Encoder = 节点 → 向量

Decoder = 向量 → 相似度

训练目标 = 图里相似的节点，向量也要相似

Random walk 用“走路时经常遇到谁”来定义节点相似性。

DeepWalk：

随机走，策略比较固定

node2vec：

带偏置地随机走，可以调 p、q

既可以偏 BFS，也可以偏 DFS

第一步：根据 p、q 计算随机游走的转移概率

第二步：从每个节点出发，模拟多条固定长度的 random walk

第三步：用这些 walk 里的共现节点训练 embedding

这份 PDF 的主线可以压缩成一句话：

==🟡通过 random walk 学习节点 embedding，让图中相似的节点在向量空间中接近，再把这些向量用于节点分类、链接预测、图分类等任务。==

你现在需要掌握的核心点是：

\1. Node embedding：节点 → 低维向量

\2. Encoder：节点变向量

\3. Decoder：用向量判断相似度

\4. Random walk：用“走路经常遇到谁”定义节点相似

\5. Negative sampling：用少量负样本替代全图比较，加速训练

\6. DeepWalk：无偏随机游走

\7. node2vec：带偏随机游走，用 p、q 控制 BFS/DFS 倾向

\8. Graph embedding：把节点向量聚合成整张图向量

\9. 局限：新节点难处理、结构角色相似捕捉不足、不能自然用节点特征

图机器学习需要特征

↓

手工特征很麻烦

↓

用 representation learning 自动学习节点向量

↓

让图中相似节点在向量空间中接近

↓

用 random walk 定义“相似”

↓

DeepWalk 是普通随机游走

↓

node2vec 用 p、q 控制 BFS/DFS 倾向

↓

但它们不能很好处理新节点，也不能自然利用节点特征

↓

所以引出 GNN

Pdf3

看整张图：换编号，结果不能变。

看每个节点：换编号，结果跟着换位置，但每个节点自己的表示不能错。

新表示 = 神经网络(邻居平均信息 + 自己的信息)

![[gpt学习图论与图 image.png]]

\1. DeepWalk/node2vec 是浅层 embedding，不能自然处理新节点和节点特征

\2. GNN 学的是共享的邻居聚合规则

\3. 一层 GNN 看一跳，多层 GNN 看多跳

\4. 图级任务要求排列不变，节点级任务要求排列等变

\5. GCN 的基本做法：平均邻居信息 + 自己信息 + 神经网络变换

\6. GNN 可以监督训练，也可以用图结构无监督训练

\7. CNN 和 Transformer 都可以看成特殊形式的 GNN

浅层 embedding 有局限

→ 需要能利用节点特征、能处理新节点的方法

→ GNN 通过邻居聚合生成节点表示

→ 聚合函数要满足排列不变/等变

→ GCN 是最基础形式：平均邻居 + 自身信息 + 神经网络变换

→ 多层 GNN 可以看到多跳邻居

→ CNN / Transformer 可以看成特殊图结构上的 GNN

GNN 有三个优势：

\1. 可以利用节点特征

\2. 可以聚合邻居信息

\3. 可以处理训练时没见过的新节点/新图

Pdf4

GNN Layer = Message + Aggregation

Message：每个节点先把自己的表示变成要发送的消

Aggregation：目标节点把邻居消息合起来

Self-message：不要忘了节点自己的信息

![[gpt学习图论与图 image 1.png]]

邻居 u 的消息 = W × u 的上一层表示 ÷ 邻居数量

节点 v 的新表示 = 把所有邻居消息加起来，再过激活函数

GCN：

更像“邻居平均后整体变换”

GraphSAGE：

先总结邻居，再和自己拼接，更强调 inductive 表示学习

GAT 的核心是：

A 聚合 B、C、D 时，不是简单平均，而是给每个邻居一个 attention weight

PDF 第 31–33 页把 attention 过程拆成三步：

第一步：计算 e_vu

表示邻居 u 对目标节点 v 有多重要

第二步：用 softmax 归一化成 α_vu

让所有邻居权重加起来等于 1

第三步：按 α_vu 加权求和邻居消息

换成人话：

先打分，再变成比例，最后按比例听取邻居意见

Batch Normalization：让训练更稳定

Dropout：防止过拟合

Attention / Gating：控制消息重要性

跳连

不要只依赖当前层变换后的结果，还把上一层的信息直接加过来。

在 GNN 里就是：

新表示 = GNN 聚合结果 + 旧表示

这样做的好处是：

深层信息可以用，浅层中更能区分节点的信息也能保留

总结

\1. 一层 GNN = Message + Aggregation

\2. Message：节点生成要发出的信息

\3. Aggregation：目标节点汇总邻居信息

\4. GCN：邻居基本平均

\5. GraphSAGE：先聚合邻居，再和自己拼接

\6. GAT：给不同邻居学习不同 attention 权重

\7. BatchNorm / Dropout 等模块可以加入 GNN

\8. GNN 不能盲目加深，会出现 over-smoothing

\9. 过平滑原因：感受野高度重叠

\10. 缓解：少加层、增强单层、加 MLP、加 skip connection

GNN 的本质是“消息传递 + 邻居聚合”，不同模型主要区别在于消息怎么算、邻居怎么聚合、层与层怎么连接。

GNN 层数控制感受野，不是越深越好；当任务只需要局部信息时，应使用较浅层 GNN，并通过增强单层表达能力或加入跳连来提升性能。

Pdf5

想泛化到新节点 / 大图：优先 constant feature 或其他可泛化特征

只在一个小图上做 transductive 学习：one-hot 可以用

virtual node 太强时可能会让全图信息混得太快，所以它是一个设计选择，不是无脑加。

Graph manipulation：原始图不一定适合直接训练，可以改造特征或结构。

Feature augmentation：没有节点特征时，可以用 constant 或 one-hot，也可以加入结构特征。

Structure manipulation：

图太稀 → 加 virtual node / edge

图太密 → 采样邻居

图太大 → 采样子图

节点级任务：用一个节点 embedding

边级任务：用两个节点 embedding

图级任务：聚合所有节点 embedding，或使用 virtual super node

用户是否欺诈 → 分类 → CE

药物活性分数是多少 → 回归 → MSE

Precision：模型报警的交易里，有多少真的欺诈？

Recall：所有真实欺诈交易里，模型抓住了多少？

F1：Precision 和 Recall 的综合

ROC AUC：模型区分正负样本的排序能力==🟡？？？==

**ROC AUC 高**说明模型更擅长：

给真实正样本更高分

给真实负样本更低分

比如欺诈检测里，就是：

欺诈交易的风险分数普遍高于正常交易

但它**不等于**某个固定阈值下的 Accuracy 一定高。因为 Accuracy 还取决于你最后把阈值设在哪里，比如 0.5、0.7、0.9。PDF5 第 52–53 页也是这个意思：ROC 曲线看的是不同阈值下 TPR 和 FPR 的权衡，ROC AUC 可以理解成模型把随机正样本排在随机负样本前面的概率。

你可以这样记：

ROC AUC 看排序能力

Accuracy 看固定阈值下的分类结果

举个极简例子：

欺诈边 A-B：0.80

正常边 A-C：0.60

如果阈值是 0.5，它俩都会被判成正类，Accuracy 未必好；

但从排序看，欺诈边分数更高，所以 ROC AUC 仍然可能不错。

Transductive：同一张图，划分标签。适合：一张 citation network 上做节点分类

Inductive：不同图，划分图。适合：分子图分类、新城市/新生物网络泛化

同一张图上做 link prediction，

但要把边分成“给模型看的边”和“让模型预测的边”。

训练时预测 training supervision edges；

验证时预测 validation edges；

测试时预测 test edges。

每一步都不能把当前要预测的边放进 GNN 的 message passing 图里。

==🟡PDF5 讲的是 GNN 的完整训练管线：如何改造图、如何接预测头、如何选择监督信号、loss、评价指标，以及如何正确划分图数据集。==

\1. Raw input graph 不一定等于 computational graph

\2. 没有节点特征时，可以用 constant feature 或 one-hot ID

\3. constant 泛化强，one-hot 表达强但偏 transductive

\4. 图太稀可以加 virtual node，图太密/太大可以采样邻居或子图

\5. Prediction head 按任务分 node / edge / graph level

\6. 分类用 CE，回归用 MSE

\7. 二分类不应只看 accuracy，还要看 precision / recall / F1 / ROC AUC

\8. Transductive：同一张图内划分标签

\9. Inductive：不同图之间划分，测试新图

\10. Link prediction 要特别小心，边既是结构也是标签，需要区分 message edges 和 supervision edges

Pdf6

PDF 第 35–37 页就是用类似例子说明：GCN 不能区分颜色比例相同但数量不同的 multiset。

GCN mean：看比例，可能丢数量

GraphSAGE max：看有没有，可能丢次数

GIN sum：保留数量，更不容易丢信息

sum：multiset，能保留重复次数

mean：distribution，更像保留比例

max：set，更像保留是否出现

Wl

**WL 是一种反复“根据自己颜色和邻居颜色重新染色”的图结构区分方法；GIN 则是把这个重新染色过程变成了可训练的神经网络。**

再压缩一点：

WL自己颜色 + 邻居颜色集合 → HASH → 新颜色

GIN：自己向量 + 邻居向量集合 → sum + MLP → 新向量

# 总结

GNN 表达能力

= 能不能区分不同图结构

GNN 看到的是 rooted subtree / computational graph

要区分不同 rooted subtree

→ aggregation 最好是 injective

mean pooling 会丢数量比例之外的信息

max pooling 会丢重复次数信息

sum pooling 更强

GIN = MLP + Sum + MLP

是 message-passing GNN 中表达能力很强的模型

GIN 和 WL graph kernel 等价

但它们仍然不能区分所有结构，比如某些 cycle / clique

Pdf7

Laplacian eigenvectors 是从图的 Laplacian 矩阵中提取出来的“结构坐标”，把每个 eigenvector 的第 i 个值作为节点 i 的特征，从而帮助 GNN 区分原本因对称性或缺少特征而难以区分的节点

==🟡Structure-aware：==

解决“结构不同但 GNN 分不清”

方法：cycle count、closed loops、clustering coefficient、PageRank、centrality、Laplacian eigenvectors

==🟡Position-aware：==

解决“结构相同但位置不同”

方法：anchor nodes、anchor sets、distance-based position encoding、P-GNN

structure-aware 让 GNN 知道节点“长得像什么结构角色”；position-aware 让 GNN 知道节点“在整张图的哪里”。

普通 GNN / WL 有表达力限制

↓

有些结构不同但 GNN 分不清

→ 加 structure-aware features

有些结构相同但位置不同

→ 加 position-aware features

Structure-aware GNN

目标：识别节点的结构角色

问题：普通 GNN 分不清某些 cycle / clique / 对称结构

方法：cycle count、closed-loop features、centrality、PageRank、Laplacian eigenvectors

例子：节点是否在三角形中、用户是否是中心人物

Position-aware GNN

目标：识别节点在整张图中的位置

问题：局部结构相同但全局位置不同

方法：anchor node、anchor set、distance-based position encoding、P-GNN

例子：路口在市中心还是郊区、网格图左下角还是右上角

Pdf8

Transformer 很强

→ self-attention 可以看成完全图上的 message passing

→ 所以可以把 Transformer 用到图上

但图不是普通序列

→ 需要重新设计三个东西：

\1. Tokenization

节点特征作为 token

\2. Positional Encoding

注入图结构/位置信息

例：relative distance、Laplacian eigenvectors

\3. Modified Attention

把边特征加入 attention score

一句话版：

**Graph Transformer = 把节点当 token，用位置编码补图结构，用 modified attention 融入边特征。**

Pdf9

第一部分

异质图是包含多种节点类型或边类型的图。它比普通图更适合描述现实世界中的复杂关系，比如电商图、学术图、生物医学知识图谱。异质图的关键概念是 relation type，也就是“起点节点类型、边类型、终点节点类型”的组合。我们虽然可以把类型当作普通特征，把异质图转成同质图，但当不同类型节点的特征空间不同，或者不同关系代表不同交互模式时，就需要专门的异质图建模方法。

\1. Homogeneous graph：节点/边类型基本相同。

\2. Heterogeneous graph：有多种节点类型或边类型。

\3. Relation type = 起点类型 + 边类型 + 终点类型。

第二部分

普通 GCN：

所有边一种关系 → 一个 W

异质图：

边有多种 relation type → 一个 W 不够

RGCN：

每种 relation type 一个 W_r

按 relation 分组传消息

再把不同 relation 的消息聚合

问题：

relation 很多 → 参数爆炸

解决：

block diagonal 降低矩阵参数

basis learning 让不同 relation 共享基础矩阵

RGCN 可以看成是 GCN 在异质图上的扩展。普通 GCN 默认所有边的语义相同，因此所有邻居消息都用同一个权重矩阵变换；而在异质图中，不同 relation type 表示不同交互，比如作者写论文和论文引用论文，所以 RGCN 为每种 relation type 使用不同的权重矩阵。节点更新时，模型会按 relation type 收集邻居消息，进行归一化和求和，再加上 self-loop 信息。RGCN 的主要问题是 relation 数量多时参数量会快速增长，因此可以用 block diagonal matrix 或 basis learning 来做参数正则化和共享。