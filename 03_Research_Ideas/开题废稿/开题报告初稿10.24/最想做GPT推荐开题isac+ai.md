对，而且如果你的目标是**“AI + ISAC，但不要老套”**，我建议我们把思路彻底换一下。

现在的 ISAC+AI 已经不是简单的：

> ISAC 建模 → DQN/PPO → 波束/功率优化

2025 年的综述已经把波束跟踪、功率、频谱、波形、AoA/AoD 等大量“AI for ISAC”问题梳理得比较成熟了。[IEEE Xplore](https://ieeexplore.ieee.org/document/11062661?utm_source=chatgpt.com)

而你所在的 北京交通大学 徐少毅老师团队本身已经有 **ISAC 跟踪、复杂轨迹、多基站协同、联邦学习、人工智能、低空智能通信**这些基础，所以我反而建议你往**“AI-native ISAC”**走，而不是继续做普通 DRL 波束优化。徐老师主页目前列出的研究方向也明确包括人工智能和低空智能通信与网联技术。[北京交通大学](https://faculty.bjtu.edu.cn/8305/?utm_source=chatgpt.com)

---

# 一、我先给你一个新的方向地图

我把目前值得考虑的方向分成两类：

### AI for ISAC

> 用 AI 让 ISAC 更聪明

包括：

1. **World Model / 世界模型**
2. **Continual Learning / 持续学习**
3. **Foundation Model / 基础模型**
4. **GNN + Multi-Agent RL**
5. **Diffusion / Generative AI**
6. **Agentic AI / LLM Agent**
7. **主动感知 + RL**

### ISAC for AI

> 让 ISAC 给 AI 提供数据、感知和通信能力

包括：

8. **感知辅助边缘 AI**
9. **ISAC + Federated Learning**
10. **任务导向语义通信**
11. **多模态感知 + 语义通信**

后面这类其实更“6G味”，而且可能比单纯波束优化更新。

---

# 二、我最推荐你的 7 个方向

## 🥇 方向 1：ISAC + World Model

### 推荐题目

> **面向低空动态环境的通感一体化世界模型与主动波束决策研究**

或者更硕士化：

> **面向低空无人机通信的通感一体化世界模型预测与智能决策研究**

### 为什么这个方向有意思？

这是我目前**最推荐你重点关注的方向之一**。

传统 AI：

```
当前感知
 ↓
神经网络
 ↓
当前动作
```

World Model：

```
历史感知
   ↓
世界模型
   ↓
预测未来环境
   ↓
模拟不同动作
   ↓
选择未来最优动作
```

也就是说：

> **不是让 AI 直接学“看到什么 → 选哪个波束”，而是让 AI 学会“这个无线环境接下来会怎么变化”。**

2026 年 10 月刚出现的 WM4ISAC 就已经开始研究这个方向：利用 radar heatmap 学习 latent dynamics，再预测 LoS 对齐、遮挡以及 NLoS 波束机会，而不是直接从观测映射到 beam index。[arXiv](https://arxiv.org/abs/2610.08267?utm_source=chatgpt.com)

所以这个方向非常新，但也意味着竞争非常激烈。
# ==wm4isac大白话翻译+解释摘要==

## 背景问题

车载的**通感一体化ISAC**用的是毫米波，波束很窄。路上车辆、障碍物会突然挡住视线链路（动态遮挡）。一旦视线链路被挡住或者波束对不准，通信质量就会暴跌。 传统做法：等链路被挡了之后，再去调整波束，属于被动补救，经常来不及。

## 本文提出：WM4ISAC

一套**预判式（主动）ISAC框架**，核心是**世界模型（world model）**。 它不是简单地“看到当前画面，直接输出波束编号”；而是从下行雷达热力图里，学习出交通环境背后可复用的环境变化规律（隐动力学模型）。

### 框架里三个主要模块

1. **视觉V模块**：把雷达感知到的环境信息压缩提炼；
2. **带动作条件的记忆M模块**：预测这个环境接下来会怎么变化；
3. **轻量事件预测头**：评估备选波束三种情况：是否直视对准、会不会被遮挡、能不能靠反射散射走非视距NLoS通路。

最后有一个码本层面控制器：**不用预先知道未来车辆、障碍物的位置**，依靠上面的预测结果，主动在直视（LoS）波束和反射非视距（NLoS）波束之间提前切换。

## 仿真结果

在有动态遮挡的场景测试：

- 和传统只跟踪直视链路的方案相比，平均通信速率提升 **28.9%**
- 最差5%用户的速率（5%-tile，代表弱用户性能）：从0.9 Mbps → 30.5 Mbps
- 性能能达到“拥有全部未来信息的理想上限”的88.7%

---

## 一句话极简版

毫米波车载通感一体化很容易被路上车辆挡住信号。这篇论文用世界模型学习交通环境变化，提前预判遮挡，主动切换直视/反射波束，不用预知障碍物未来位置，大幅提升通信速率，尤其改善最差用户的通信体验。

如果你需要，我可以再给你一段适合组会口头汇报的精简英文摘要转述。
### 你可以进一步往 UAV 做

例如：

**无人机突然转弯**

传统：

> 预测位置 → 选波束

World Model：

> 根据过去 1 秒的感知序列 → 预测无人机未来轨迹、遮挡状态、信道变化 → 在多个候选未来状态下进行规划 → 决定波束。

甚至可以：

\[ z_{t+1:t+H} = f_\theta(z_{t-k:t},a_{t-k:t}) \]

然后利用模型预测：

\[ \hat R_{t+1:t+H} \]

再做 Model Predictive Control / Model-Based RL。

### 创新潜力

⭐⭐⭐⭐⭐

### 毕业风险

⭐⭐⭐

### AI味

⭐⭐⭐⭐⭐

**很适合你。**

---

# 🥈 方向 2：ISAC + Continual Learning

这个我其实认为**非常适合你现在的情况**。

### 推荐题目

> **面向低空动态场景的通感一体化持续学习与跨域波束管理研究**

或者：

> **面向无人机通感一体化系统的跨场景持续学习与自适应波束管理研究**

---

## 为什么它比 DQN 新？

==现实中的无人机通信环境不是固定分布。==

训练的时候：

```
晴天
低速无人机
开阔区域
```

部署之后：

```
城市峡谷
高速飞行
建筑遮挡
不同高度
不同基站
不同频段
```

于是：

$\[ P_{\text{train}}(x) \neq P_{\text{test}}(x) \]$

甚至环境随着时间不断变化：

\[ $P_1(x)\rightarrow P_2(x)\rightarrow P_3(x)$ \]

这就是：

> **Concept Drift / Domain Shift**

传统神经网络重新训练很贵，而且容易灾难性遗忘。

这其实特别适合 ISAC：

> **感知系统本身就是一个不断产生新数据的数据流。**

---

### 一个很漂亮的研究问题

比如你训练了：

> 北京城市环境模型

然后无人机进入：

> 新区域

ISAC 基站不断获得：

- CSI
- AoA
- Doppler
- Radar feature
- position
- beam feedback

然后：

> ==**如何让 AI 在不保存全部历史数据的情况下持续学习新的无线环境，同时不忘掉以前学到的知识？**==

这就从：

**“AI 优化 ISAC”**

升级成：

**“ISAC 给 AI 提供持续学习的数据流”。**

这已经很接近 AI-native wireless。

2025 年已经有 EdgeCL 研究专门研究 ISAC 网络中的跨域持续学习：CSI 与活动之间存在明显 domain dependence，并通过 Transformer + core-set 知识保留缓解遗忘。[arXiv](https://arxiv.org/abs/2502.12736?utm_source=chatgpt.com)

这篇论文非常值得你精读。

### 你可以进一步做

```
ISAC感知
   ↓
CSI / Radar Feature
   ↓
Domain Shift Detection
   ↓
判断环境有没有变化
   ↓
Continual Learning
   ↓
更新 Beam Prediction Model
```

甚至可以做：

### “什么时候应该学习？”

也就是：

\[ $\text{Learning Trigger} = f(\text{uncertainty},\text{prediction error},\text{environment shift})$ \]

AI 自己决定：

> “现在环境已经变了，我应该更新模型。”

这个点就比“用 Transformer 做波束预测”有意思很多。

### 创新潜力

⭐⭐⭐⭐⭐

### 毕业风险

⭐⭐⭐⭐

### AI味

⭐⭐⭐⭐⭐

### 与徐老师方向匹配

⭐⭐⭐⭐⭐

**这是我非常建议你认真考虑的一个。**

---

# 🥉 方向 3：ISAC + Agentic AI

这个是**目前最前沿**的方向。

甚至可以说是 2026 年 ISAC+AI 很明显的新趋势。

---

## 什么叫 Agentic ISAC？

传统：

> ISAC → AI → 输出一个 beam

Agentic ISAC：

```
感知
 ↓
理解环境
 ↓
推理
 ↓
制定目标
 ↓
调用算法
 ↓
调整波束/功率/资源
 ↓
获得反馈
 ↓
重新规划
```

2026 年已经出现专门讨论 Agentic AI + ISAC 的工作，把整个系统描述为：

> observation → contextualization → reasoning/prediction → planning → execution → feedback

并明确指出 **physical-to-semantic grounding、world model、real-time agent-PHY interaction、safe tool use** 等仍然是开放问题。[arXiv](https://arxiv.org/abs/2608.05792?utm_source=chatgpt.com)

2025 年也已有 Agentic AI for ISAC 的框架和案例研究。[arXiv](https://arxiv.org/abs/2512.15044?utm_source=chatgpt.com)

甚至 2026 年已经有人提出：

> **LLM-driven Agent Compiler for ISAC Networks**

让 LLM 把高层工程意图转换成 ISAC 网络配置，并强调 LLM 做慢时间尺度决策，传统算法负责实时控制。[arXiv](https://arxiv.org/abs/2607.16269?utm_source=chatgpt.com)

---

## 你不要直接做“LLM控制波束”

这个很危险。

容易变成：

> 调个 ChatGPT API + ISAC

老师很可能问：

**“LLM和通信有什么本质关系？”**

---

## 更好的做法

让 LLM / Agent 负责：

### 高层任务规划

例如用户告诉系统：

> “保障无人机 U1 的低时延通信，同时跟踪 U2。”

Agent：

```
任务解析
 ↓
目标优先级
 ↓
调用感知模块
 ↓
调用波束预测模型
 ↓
调用资源优化器
 ↓
输出策略
```

而底层：

> MPC / RL / SCA / Beamforming

继续负责实时控制。

这样就形成：

\[ $\boxed{ \text{LLM Agent} \rightarrow \text{Reasoning / Planning} \rightarrow \text{RL / Optimization} \rightarrow \text{PHY} }$ \]

这个架构就合理很多。

### 创新潜力

⭐⭐⭐⭐⭐

### 毕业风险

⭐⭐

### AI味

⭐⭐⭐⭐⭐⭐

### 新颖程度

⭐⭐⭐⭐⭐⭐

但是：

**我不建议把它作为你硕士唯一主线。**

太新，而且很容易陷入“概念很大、实验很虚”。

更适合：

> **主线是 World Model / Continual Learning，Agent 作为后续扩展。**

---

# 4. ISAC + GNN + Multi-Agent RL

这个相对稳。

### 题目

> ==**面向低空多无人机协同感知通信的图神经网络与多智能体强化学习研究**==

场景：

```
          UAV1
           ↕
BS1 ←→ BS2 ←→ BS3
           ↕
          UAV2
           ↕
          UAV3
```

天然就是一个图：

\[ G=(V,E) \]

节点：

- UAV
- BS
- RIS
- sensing target

边：

- 通信关系
- 干扰关系
- 感知关系
- 邻居关系

GNN：

$\[ h_i^{l+1} = \text{AGG} \left( h_i^l,\{h_j^l:j\in\mathcal N_i\} \right) \]$

然后：

> GNN负责空间关系建模  
> MARL负责动态资源决策

这个方向现在已经有很多研究，所以**单纯 GNN + MADRL 已经不新**。例如 2025 年已有 UAV-SAGIN 中利用 MADRL 联合优化 UAV 轨迹、匹配和波束。[IEEE Xplore](https://ieeexplore.ieee.org/document/11148209/?utm_source=chatgpt.com)

所以如果做这个，我建议增加：

> **动态图 + 环境变化 + 泛化**

比如：

### “训练 3 架 UAV，测试 10 架 UAV”

如果你的 GNN 策略仍然有效：

> 这个就比“多智能体 PPO”有价值很多。

---

# 5. ISAC + Diffusion Model

这个方向非常适合你这种**喜欢深度学习的人**。

### 题目

> ==**基于扩散模型的通感一体化信道生成与智能波束设计研究**==

或者：

> **面向低空无人机 ISAC 的扩散模型驱动信道预测与波束生成研究**

---

## Diffusion 可以干什么？

不是只能生成图片。

可以让 diffusion 学：

\[ $p(\mathbf H_{t+1}|\mathbf H_{1:t})$ \]

生成：

- CSI
- Radar map
- channel map
- beam candidates
- future trajectories

例如：

```
过去 CSI
   ↓
Diffusion Model
   ↓
生成未来可能的多个信道状态
   ↓
得到 uncertainty / distribution
   ↓
Beam optimization
```

这比：

> LSTM预测一个CSI

高级很多。

而且 2025 年已经有 diffusion 用于 ISAC 安全感知；2026 年还有 diffusion + fluid antenna 的 ISAC 工作，说明生成式 AI 已经开始进入 ISAC 物理层设计。[IEEE Xplore](https://ieeexplore.ieee.org/document/11004012/?utm_source=chatgpt.com)

### 真正值得做的是：

**不要做“Diffusion预测CSI”。**

这个很容易被问：

> 为什么不用 Transformer？

更有意思的是：

> **Diffusion生成多个未来无线环境状态，用于风险感知波束决策。**

也就是：

\[ $\{\hat H_{t+1}^{(1)},...,\hat H_{t+1}^{(N)}\}$ \]

然后计算：

\[ $P(\text{Beam Failure}|a)$ \]

这样 diffusion 就不只是“换个预测模型”。

### 创新

⭐⭐⭐⭐⭐

### 难度

⭐⭐⭐⭐

### AI味

⭐⭐⭐⭐⭐

---

# 6. ISAC + 多模态 AI / 语义通信

这个方向我也很看好。

因为未来低空网络不是只需要：

> “无人机在哪？”

而是：

> “无人机看到什么？”

比如无人机拍摄：

```
Camera
LiDAR
Radar
CSI
GPS
```

这些都是不同模态。

---

### 可以研究

> **面向低空无人机任务的多模态感知与语义通信**

例如：

无人机发现：

> 前方出现异常车辆。

传统通信：

> 上传 10 MB 视频。

语义通信：

> 只上传和任务相关的信息。

```
Video
 ↓
Vision Encoder
 ↓
目标/事件语义
 ↓
Semantic Encoder
 ↓
ISAC transmission
 ↓
BS
 ↓
AI inference
```

2025 年已经出现 UAV-assisted ISAC 多模态语义通信工作，把 HSI 和 LiDAR 用于目标分类和数据重建。[IEEE Xplore](https://ieeexplore.ieee.org/document/11162428/?utm_source=chatgpt.com)

同时，大模型驱动的多模态语义通信也已经开始出现。[IEEE Xplore](https://ieeexplore.ieee.org/document/10670195/?utm_source=chatgpt.com)

所以不要做：

> “CNN + ISAC + 语义通信”

太普通。

可以做：

### “任务驱动”

例如：

\[ \text{任务} = \text{目标检测} \]

与：

\[ \text{任务} = \text{目标跟踪} \]

需要传输的语义信息不同。

于是：

$\[ \text{Task} \rightarrow \text{Semantic Importance} \rightarrow \text{ISAC Resource Allocation} \]$

这个研究逻辑就比较漂亮。

### 创新

⭐⭐⭐⭐

### AI味

⭐⭐⭐⭐⭐⭐

### 数据工作量

⭐⭐⭐⭐⭐

### 毕业风险

⭐⭐⭐

---

# 7. ISAC + Federated Learning

这个其实非常适合你们组。

因为徐老师团队已经有 FL 相关工作。[北京交通大学电子信息工程学院](https://eie.bjtu.edu.cn/faculty/8305.html?utm_source=chatgpt.com)

但是：

> “ISAC + FL + PPO”

现在已经比较多了。

例如已有研究利用 FL + multi-agent actor-critic 处理 ISACP 资源优化，也有 2026 年工作直接研究非 IID ISAC 多智能体 FL。[IEEE Xplore](https://ieeexplore.ieee.org/document/10620738/?utm_source=chatgpt.com)

所以不要做：

> 联邦学习优化功率分配

太老。

---

## 我更建议：

### “感知驱动的联邦持续学习”

题目：

> **面向低空动态环境的通感一体化联邦持续学习与资源协同优化研究**

这个就有意思了：

```
UAV1              UAV2
  ↓                 ↓
本地感知数据       本地感知数据
  ↓                 ↓
Local Model       Local Model
       ↘          ↙
        Federated Server
               ↓
        Global Model
               ↓
          下发到 UAV
```

但是环境又不断变化：

\[ D_1\rightarrow D_2\rightarrow D_3 \]

所以：

> **FL + Continual Learning + ISAC**

会比：

> FL + PPO

新很多。

---

# 三、如果按照“你的情况”重新排名

考虑到你：

- 通信硕士
- 深度学习 / 强化学习比较擅长
- 想做 AI + ISAC
- 徐老师组
- 希望开题有创新
- 但最终还是要稳妥毕业

我的排名会变成：

| 排名  | 方向                                | 创新     | 难度    | 毕业稳妥性 | 推荐        |
| --- | --------------------------------- | ------ | ----- | ----- | --------- |
| 🥇  | **ISAC + Continual Learning**     | ⭐⭐⭐⭐⭐  | ⭐⭐⭐   | ⭐⭐⭐⭐⭐ | **★★★★★** |
| 🥈  | **ISAC + World Model**            | ⭐⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐  | ⭐⭐⭐⭐  | **★★★★★** |
| 🥉  | **ISAC + Active Sensing + RL**    | ⭐⭐⭐⭐⭐  | ⭐⭐⭐⭐  | ⭐⭐⭐⭐  | **★★★★★** |
| 4   | **ISAC + Diffusion**              | ⭐⭐⭐⭐⭐  | ⭐⭐⭐⭐  | ⭐⭐⭐   | ★★★★      |
| 5   | **ISAC + GNN + MARL**             | ⭐⭐⭐⭐   | ⭐⭐⭐   | ⭐⭐⭐⭐⭐ | ★★★★      |
| 6   | **ISAC + Multimodal/Semantic AI** | ⭐⭐⭐⭐⭐  | ⭐⭐⭐⭐  | ⭐⭐⭐   | ★★★★      |
| 7   | **ISAC + Agentic AI/LLM**         | ⭐⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐    | ★★★       |

---

# 四、但我真正建议你重点看这三个

如果让我现在帮你**重新推翻之前那个“预测式波束 + DQN”题目**，我会留下：

## 🥇 方向 A

### **面向低空动态场景的通感一体化持续学习与自适应波束管理研究**

核心：

> **环境会变，AI 怎么自己学？**

---

## 🥈 方向 B

### **面向低空无人机的通感一体化世界模型与主动决策研究**

核心：

> **AI 能不能预测无线世界，而不仅仅预测无人机位置？**

---

## 🥉 方向 C

### **面向低空无人机的通感一体化主动感知与长期资源决策研究**

核心：

> **基站什么时候应该“主动感知”，而不是被动接收感知结果？**

---

# 五、其实还有一个我非常想让你注意的变化

你之前一直在想：

> **“AI 怎么帮助 ISAC？”**

现在可以反过来想：

> **“ISAC 怎么帮助 AI？”**

这个思想可能更重要。

2026 年已经出现明确提出 **AISAC（AI-integrated sensing and communication）** 的工作，其核心观点就是：ISAC 不应该只是 AI 的一个优化对象，ISAC 本身可以成为 AI 获取现实世界数据、上下文和连接能力的物理基础。[arXiv](https://arxiv.org/abs/2607.16507?utm_source=chatgpt.com)

于是：

```
传统
AI → 优化 ISAC
```

变成：

```
        ┌──── AI ────┐
        ↓            ↑
     感知数据      决策
        ↑            ↓
        └── ISAC ───┘
```

这才是真正的：

# AI-Native ISAC

而不是：

> **“ISAC + 一个深度学习算法”。**

---

## 六、如果是我替你选，我会这么设计硕士论文

我甚至觉得可以把整篇论文设计成：

### **《面向低空动态网络的AI原生通感一体化智能感知与资源决策研究》**

下面分三章：

### 第一部分：AI 感知

**跨场景持续学习**

解决：

> 环境变化导致 AI 模型失效。

↓

### 第二部分：AI 预测

**World Model**

解决：

> AI 不知道无线环境未来会怎么变化。

↓

### 第三部分：AI 决策

**主动感知 + RL**

解决：

> AI 知道未来可能发生什么以后，应该什么时候感知、什么时候通信、什么时候切换波束。

最后形成：

\[ \boxed{ \text{ISAC Sensing} \rightarrow \text{Continual Learning} \rightarrow \text{World Model} \rightarrow \text{Planning} \rightarrow \text{Active Sensing/Communication} } \]

这就已经不是“DQN 优化波束”了，而是一套比较完整的 **AI-native ISAC** 思路。

**不过我不建议你直接把这么大的框架拿去开题。** 对硕士来说，最好选其中一个作为主线，其余作为扩展。特别是 World Model 和 Agentic AI 目前发展太快，2026 年已经有非常新的工作进入同一赛道。[arXiv](https://arxiv.org/abs/2610.08267?utm_source=chatgpt.com)

如果你愿意，我下一步可以直接给你做一件更有价值的事：

**把这 7 个方向各找 5～10 篇 2024—2026 年真正值得精读的论文，整理成“论文 → 已解决问题 → 没解决的问题 → 可以怎么创新 → 适不适合硕士开题”的选题地图。**

这样我们可以从**论文缺口**反推你的开题题目，而不是先拍脑袋定一个“AI+ISAC”标题。