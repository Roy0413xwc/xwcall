## 推荐课题的数学建模

我建议把三个切入点合并成一个课题，而不是分别写三篇论文。

建议作为正式开题候选

# ==基于物理约束世界模型的车联网 ISAC 感知—通信联合预测式资源调度研究==

英文题目：

Physics-Constrained World Model-Aided Predictive Joint Sensing and Communication Resource Scheduling for Vehicular ISAC Networks

### 4.1 系统模型

考虑一个车联网场景：

- 一个 RSU 负责车辆通信和无线感知。
    
- K 辆车辆在道路上高速移动。
    
- RSU 使用 OFDM-ISAC 信号，同时完成车辆感知和数据传输。
    
- 系统具有有限的带宽、发射功率和感知时隙。
    
- 车辆之间存在动态遮挡，信道和目标跟踪精度随时间变化。
    ![[Pasted image 20261105152158.png]]

[Radar-Assisted Multiple Base Station Cooperative mmWave Beam Tracking](https://images.openai.com/static-rsc-4/6ukZ3IbMptrTq0auXAK7CK3Ss_Hn0iYG9YsXojZix0_Aqntc5HLH7-KysImEmWb49wSzwz2NlwG2ec-sH6GqD4vThVf8yw4SgQDAwf_hnZK8TuLatmayWZO5z4Ke0AKB3NUfy58B--uR0yVnvman4Ly6WwBwEk7ozDz5otdZbes?purpose=inline)

[mdpi.com](https://www.mdpi.com/2079-9292/12/7/1672?utm_source=chatgpt.com)

先从一个 RSU 开始，后续扩展为两个 RSU 协同工作。

### 4.2 车辆运动模型

将车辆表示为二维运动目标：

\[ \mathbf{x}_{k,t}= [x_{k,t},y_{k,t},v^x_{k,t},v^y_{k,t}]^T \]

采用常速度模型：

\[ \mathbf{x}_{k,t+1} =\mathbf F\mathbf{x}_{k,t}+\mathbf w_{k,t} \]

其中：

\[ \mathbf F= \begin{bmatrix} 1&0&\Delta t&0\\ 0&1&0&\Delta t\\ 0&0&1&0\\ 0&0&0&1 \end{bmatrix} \]

\(\mathbf w_{k,t}\) 是车辆运动过程中的随机扰动。

后续可以增加转弯、加速和减速模型。

### 4.3 感知模型：用跟踪误差衡量感知质量

RSU 对车辆进行雷达感知，获得距离、角度和多普勒等观测。

使用 EKF 或 UKF 更新车辆状态估计：

\[ \mathbf P^-_{k,t} =\mathbf F\mathbf P_{k,t-1}\mathbf F^T+\mathbf Q \]

如果当前时隙分配了感知资源，则进行观测更新：

\[ \mathbf P_{k,t} = (\mathbf I-\mathbf K_{k,t}\mathbf H_{k,t}) \mathbf P^-_{k,t} \]

其中：

- \(\mathbf P^-_{k,t}\)：预测误差协方差。
    
- \(\mathbf P_{k,t}\)：更新后的跟踪误差协方差。
    
- \(\mathbf K_{k,t}\)：卡尔曼增益。
    
- \(\mathbf H_{k,t}\)：观测模型雅可比矩阵。
    

如果没有安排感知，则只进行预测，误差协方差通常会逐渐增大。

这就是我们要研究的关键问题：

有限的感知资源应该优先分配给哪些车辆？

可以使用：

\[ E_{k,t}=\operatorname{Tr}(\mathbf P_{k,t}) \]

衡量车辆跟踪不确定性。

也可以进一步研究 PCRB，作为理论性能下界。

### 4.4 通信模型：用速率和信息新鲜度衡量通信质量

车辆与 RSU 之间的通信速率可以写为：

\[ R_{k,t} = B_{k,t}^{c} \log_2\left( 1+\frac{p_{k,t}^{c}g_{k,t}} {N_0B_{k,t}^{c}+I_{k,t}} \right) \]

其中：

- \(B_{k,t}^{c}\)：通信带宽。
    
- \(p_{k,t}^{c}\)：通信功率。
    
- \(g_{k,t}\)：信道增益。
    
- \(I_{k,t}\)：干扰功率。
    
- \(N_0\)：噪声功率谱密度。
    

另外，引入信息年龄 AoI：

\[ \Delta_{k,t+1}= \begin{cases} 1,&\text{成功收到新状态信息}\\ \Delta_{k,t}+1,&\text{没有成功收到新信息} \end{cases} \]

这样就同时有了两个关键指标：

- 感知：跟踪误差。
    
- 通信：传输速率和信息新鲜度。
    

### 4.5 联合资源调度优化问题

RSU 每个时隙需要决定：

1. 给哪些车辆分配感知资源。
    
2. 给哪些车辆分配通信资源。
    
3. 感知与通信分别使用多少带宽。
    
4. 感知和通信分别使用多少功率。
    

设决策变量为：

\[ \mathcal A_t= \{b^s_{k,t},b^c_{k,t}, p^s_{k,t},p^c_{k,t}\}_{k=1}^{K} \]

建立优化目标：

\[ \begin{aligned} \max_{\pi}\quad &\mathbb E_\pi \left[ \sum_{t=0}^{T}\gamma^t r_t \right]\\ r_t={}& w_R\sum_k\log(1+R_{k,t})\\ &-w_P\sum_k\operatorname{Tr}(\mathbf P_{k,t})\\ &-w_A\sum_k\Delta_{k,t}\\ &-w_E\sum_k E_{k,t}^{\rm tx} \end{aligned} \]

约束：

\[ \sum_k(b^s_{k,t}+b^c_{k,t})\leq B \]

\[ \sum_k(p^s_{k,t}+p^c_{k,t})\leq P_{\max} \]

同时可以设置最低通信可靠性和最大允许跟踪误差约束。

这里的 \(\pi\) 是资源调度策略，\(w_R,w_P,w_A,w_E\) 是归一化后的目标权重。

这个模型已经可以作为第一个仿真实验的核心。

## 五、世界模型如何真正融入通信问题？

这是整个课题最重要的 AI 创新部分。

### 5.1 普通强化学习存在的问题

假设车辆 A 当前 SINR 很好，但它马上进入大型车辆遮挡区域。

普通 PPO 可能只根据当前观测分配资源。

但是未来：

- 信道可能快速恶化；
    
- 感知误差可能快速增加；
    
- 车辆状态信息可能变得陈旧；
    
- RSU 可能来不及重新调整感知资源。
    

因此，我们需要预测未来状态。

### 5.2 建立 RSSM 世界模型

[0基础速通RSSM based world model dreamer系列工作_dreamerv1-CSDN博客](https://images.openai.com/static-rsc-4/lkLgyXBuloXP3G4pmmslnduYgEzGAkvJAUgUOBk3zXZnCVqa-ubHODzDQ_Gi3PIV2L_kQpP5H81Y7I9hREHcvfDupa3tjw4RQ55hF24O6cYikScEaJqTgmIOCQOyHrDWRA9iuI22c8nxrbk6TQ6-Uax5tYegI7omC_2tzca0agM?purpose=inline)
![[Pasted image 20261105152236.png]]
[blog.csdn.net](https://blog.csdn.net/makechen666/article/details/146170133?utm_source=chatgpt.com)

建议使用 RSSM（Recurrent State Space Model）。

输入状态：

\[ o_t= [ \hat{\mathbf x}_t, \mathbf P_t, \mathrm{SINR}_t, \mathrm{AoI}_t, q_t ] \]

其中 \(q_t\) 表示信道遮挡状态或其估计概率。

世界模型学习：

\[ p_\theta(o_{t+1}|o_{1:t},a_{1:t}) \]

实际实现中，利用循环隐状态 \(h_t\) 和随机隐变量 \(z_t\) 描述环境动态：

\[ h_t=f_\theta(h_{t-1},z_{t-1},a_{t-1}) \]

\[ z_t\sim p_\theta(z_t|h_t) \]

再预测未来信道、车辆状态和跟踪误差。

### 5.3 我建议加入物理约束

这是区别于直接套用 RSSM 的重要设计。

世界模型不仅要预测数据，还要符合物理规律。

例如：

- 车辆运动应该满足运动学约束。
    
- 感知误差应该满足预测与观测更新规律。
    
- 无线信道应该体现移动和遮挡的影响。
    
- 资源分配不能超过带宽和功率限制。
    

可以设计联合训练损失：

\[ \mathcal L= \mathcal L_{\rm RSSM} +\lambda_1\mathcal L_{\rm motion} +\lambda_2\mathcal L_{\rm tracking} +\lambda_3\mathcal L_{\rm channel} \]

其中：

- \(\mathcal L_{\rm RSSM}\)：世界模型重建与 KL 损失。
    
- \(\mathcal L_{\rm motion}\)：车辆运动预测误差。
    
- \(\mathcal L_{\rm tracking}\)：跟踪协方差预测误差。
    
- \(\mathcal L_{\rm channel}\)：信道状态预测误差。
    

进一步让模型预测不确定性，而不是只输出一个确定的未来值。

### 5.4 使用世界模型进行预测式资源调度

[Model-based reinforcement learning for sample-efficient planning](https://images.openai.com/static-rsc-4/N3xpCMLpOvayXEAmJtRWNRFSEbiFmE3U0q0fUFXndFHr7R-Mw0G2MNBaCB9xRwunexC0HSqZIZwuaMiHO_ta7qgCRWzFWAMaqJJzoekGjs7yT4JvlX6uL7GfNNkpXtCP4Pb3eXuuKmAYMqdxKT8EVCNyjacz5mLq4n5s9WppLao?purpose=inline)

[research.mental-momentum.ai](https://research.mental-momentum.ai/r/model-based-reinforcement-learning-1lmsua?utm_source=chatgpt.com)

整体流程：

1. RSU 获得当前车辆和无线网络状态。
    
2. RSSM 预测未来 5—10 个时隙的环境变化。
    
3. Actor-Critic 根据未来预测状态生成资源调度策略。
    
4. 在想象轨迹中评估长期收益。
    
5. 执行当前时隙的资源分配。
    
6. 获取新观测，更新世界模型。
    

这里建议采用轻量级 Dreamer 风格的模型预测与 Actor-Critic，不要一开始就完整复现 Dual-Mind 的 System 1 + System 2 + LINN + LE-ELBO。

你可以先做标准 RSSM，再加入运动学和跟踪误差约束。

![[Pasted image 20261105152324.png]]![[Pasted image 20261105152334.png]]