---
html-source: 6acf2693-9358-83ee-8bf9-ca0c1775d9e8.html
---
给我生成一个UAV动力学的obisidian笔记md文件直接给我

已经生成好了，直接导入 Obsidian 即可：

笔记结构按照你之前的论文学习习惯整理：

- ✅ YAML 元数据（Obsidian可识别）
- ✅ UAV动力学背景
- ✅ 3-DoF模型
- ✅ 6-DoF刚体模型
- ✅ 坐标系解释
- ✅ 升力/阻力/重力模型
- ✅ 四旋翼旋翼控制原理
- ✅ Roll/Pitch/Yaw力矩
- ✅ 状态空间模型
- ✅ 控制变量设计
- ✅ 与ISAC轨迹优化的关系
- ✅ 后续连接 MPC / 最优控制 / 强化学习

内容基于你上传的论文《A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System》，尤其是论文中 Section II-B 的 UAV Dynamic Model 部分。论文明确区分了3-DoF与6-DoF模型，并指出传统方法忽略旋转运动和力矩会导致实际控制跟踪误差。 Li 等 - 2026 - A Control-Based D…

下一步建议继续做一个 **“6-DoF UAV动力学公式逐项推导 Obsidian笔记”** ，因为这篇论文真正的控制创新就在公式(14)→(21)→(36)这一条链路。 Li 等 - 2026 - A Control-Based D… Li 等 - 2026 - A Control-Based D…

UAV动力学建模_Obsidian笔记.md

带我学习SCA/SDR优化方法，先抛开论文从基础概念开始学习，再结合论文

很好，这一步非常重要。

你现在学习的这篇 UAV-ISAC 论文，本质上不是单纯做通信优化，而是在解决一个典型问题：

> **非凸优化问题如何转化为可以求解的凸优化问题。**

其中两个核心工具：

1. **SCA（Sequential Convex Approximation，序列凸近似）**
2. **SDR（Semidefinite Relaxation，半正定松弛）**

这两个方法在：

- ISAC波束成形
- MIMO优化
- RIS优化
- UAV轨迹优化
- 资源分配

里面非常常见。

我们先完全脱离论文学习基础，然后再回来看论文中的公式。

---

## 第一部分：为什么需要SCA和SDR？

## 1. 优化问题分类

优化问题一般分：

## 线性规划 LP

例如：

max ⁡ c T x \max c^Tx

约束：

A x ≤ b Ax\le b

容易求。

---

## 凸优化 Convex Optimization

例如：

min ⁡ f (x) \min f(x)

如果：

f (x) f(x)

是凸函数。

特点：

任何局部最优都是全局最优。

可以用：

- CVX
- 内点法

解决。

---

## 非凸优化 Non-convex Optimization

例如：

max ⁡ x 2 \max x^2

或者：

通信里面常见：

$S I N R = ∣ h H w ∣ 2 ∑ ∣ h H w i ∣ 2 + σ 2 SINR = \frac{|h^Hw|^2} {\sum |h^Hw_i|^2+\sigma^2}$

分子分母都有变量。

这种：

- 凹凸混合
- 多峰

求解困难。

---

所以通信优化经常流程：

`原始问题 ↓ 非凸 ↓ 数学变换 ↓ 凸优化 ↓ CVX求解`

SCA和SDR就是干这个的。

---

## 第二部分：凸优化基础

## 1. 什么是凸函数？

简单理解：

两点连线在函数上方。

数学：

对于任意：

x 1,x 2 x_1,x_2

有：

$f (θ x 1 + (1 − θ) x 2) ≤ θ f (x 1) + (1 − θ) f (x 2) f(\theta x_1+(1-\theta)x_2) \le \theta f(x_1) +(1-\theta)f(x_2)$

其中：

0 ≤ θ ≤ 1 0\le\theta\le1

图像：

凸函数：

`/ / _____/____`

像碗。

---

## 2. 为什么凸重要？

因为：

凸优化：

不会陷入局部最优。

比如：

非凸：

`* * * * * ______________`

可能有很多坑。

凸：

`* * * * * ____________`

只有一个最低点。

---

## 第三部分：SCA（序列凸近似）

这是通信论文最常用的方法。

---

## 1. SCA核心思想

一句话：

> 用一个容易求解的凸问题，逐渐逼近原来的非凸问题。

类似：

爬山：

不是直接找最高峰：

而是：

`当前位置 ↓ 局部拟合 ↓ 移动 ↓ 重新拟合 ↓ 直到收敛`

---

## 2. 一个简单例子

假设：

max ⁡ f (x) \max f(x)

但是：

f (x) f(x)

非凸。

例如：

f (x) = x 2 f(x)=x^2

怎么办？

在当前点：

x 0 x_0

做泰勒展开。

一阶近似：

$f (x) ≈ f (x 0) + ∇ f (x 0) (x − x 0) f(x) \approx f(x_0) + \nabla f(x_0)(x-x_0)$

得到：

一个线性函数。

然后：

求这个近似问题。

得到：

x 1 x_1

继续：

x 2 x_2

...

直到：

∣ x k + 1 − x k ∣ < ϵ |x_{k+1}-x_k|<\epsilon

---

## 3. SCA数学形式

原问题：

max ⁡ f (x) \max f(x)

约束：

g i (x) ≤ 0 g_i(x)\le0

如果非凸。

构造：

f ~ (x ∣ x (k)) \tilde f(x|x^{(k)})

满足：

## 条件1

当前位置相同：

f ~ (x (k)) = f (x (k)) \tilde f(x^{(k)}) = f(x^{(k)})

## 条件2

梯度相同：

∇ f ~ (x (k)) = ∇ f (x (k)) \nabla \tilde f(x^{(k)}) = \nabla f(x^{(k)})

## 条件3

近似函数是凸的。

然后：

第k次：

求：

max ⁡ f ~ (x ∣ x (k)) \max \tilde f(x|x^{(k)})

得到：

x (k + 1) x^{(k+1)}

---

## 第四部分：SDR（半正定松弛）

SDR主要解决：

## 二次优化问题

例如：

波束成形。

---

## 1. 通信中的典型形式

波束：

w w

信号功率：

∣ h H w ∣ 2 |h^Hw|^2

展开：

(h H w) H (h H w) (h^Hw)^H(h^Hw)

得到：

w H h h H w w^Hhh^Hw

这是：

二次形式。

---

但是：

变量：

w w

导致：

非凸。

---

## 2. SDR核心技巧

定义：

W = w w H W=ww^H

那么：

w H h h H w w^Hhh^Hw

变成：

T r (h h H W) Tr(hh^HW)

因为：

矩阵迹：

T r (A B) = T r (B A) Tr(AB)=Tr(BA)

---

## 3. 但是产生新约束

因为：

W = w w H W=ww^H

所以：

必须满足：

## 半正定：

W ⪰ 0 W\succeq0

## 秩1：

r a n k (W) = 1 rank(W)=1

问题：

rank约束是非凸的。

于是：

SDR：

去掉：

r a n k (W) = 1 rank(W)=1

得到：

r a n k (W) ≤ 1 rank(W)\le1

或者直接删除。

于是：

得到凸优化。

---

## 4. SDR流程

原问题：

`w优化 ↓ 令 W=wwᴴ ↓ 去掉rank约束 ↓ 凸优化 ↓ 得到W ↓ 恢复w`

---

## 第五部分：SCA和SDR区别

||SCA|SDR|
|---|---|---|
|解决问题|一般非凸|二次非凸|
|核心|局部近似|矩阵提升|
|数学工具|Taylor展开|矩阵变量|
|结果|迭代优化|凸松弛|
|常用于|SINR、轨迹|波束成形|

---

## 第六部分：回到你的论文

现在看论文。

论文有两个优化部分：

---

## 1. Beamforming优化

变量：

w m (t) w_m(t)

以及：

G d (t) G_d(t)

目标：

最大通信速率：

R m = log ⁡ 2 (1 + S I N R) R_m = \log_2(1+SINR)

问题：

SINR：

∣ g m H w m ∣ 2 ∑ ∣ g m H w i ∣ 2 + g m H G d g m + σ 2 \frac{ |g_m^Hw_m|^2 } { \sum |g_m^Hw_i|^2+ g_m^HG_dg_m+\sigma^2 }

明显非凸。

---

## 第一步：SDR

论文定义：

W m = w m w m H W_m=w_mw_m^H

于是：

∣ g H w ∣ 2 |g^Hw|^2

变成：

T r (g g H W m) Tr(gg^HW_m)

论文：

> Let W m [τ n] = w m [τ n] w m H [τ n] W_m[\tau_n]=w_m[\tau_n]w_m^H[\tau_n]

并加入：

r a n k (W m) ≤ 1 rank(W_m)\le1

Li 等 - 2026 - A Control-Based D…

---

但是：

rank约束非凸。

所以：

SDR删除：

r a n k (W m) ≤ 1 rank(W_m)\le1

得到凸问题。

---

## 第二步：SCA

虽然用了SDR：

SINR里面：

log ⁡ (1 + A B) \log(1+\frac{A}{B})

仍然非凸。

论文把：

速率：

写成：

两个log差：

log ⁡ (A + B) − log ⁡ (B) \log(A+B)-\log(B)

然后：

对第二项做一阶Taylor。

论文：

> first-order Taylor expansion

采用SCA迭代。 Li 等 - 2026 - A Control-Based D…

得到：

凸优化问题。

---

## 第七部分：论文整体算法逻辑

现在你应该能看懂：

`原始问题 P2 最大通信速率 变量: 轨迹p(t) 波束w(t) ↓ 交替优化 ================ 固定轨迹 ↓ 优化波束 ↓ SDR ↓ SCA ↓ CVX求解 ================ 固定波束 ↓ 优化轨迹 ↓ 控制模型 ↓ SQP`

---

## 你现在需要掌握的程度

对于硕士ISAC方向：

至少掌握：

## SCA

必须会：

- 为什么非凸
- Taylor展开
- 局部凸近似
- 迭代收敛思想

## SDR

必须会：

- 为什么引入矩阵W
- 二次形式转trace
- rank-1为什么重要
- 为什么松弛后凸

---

下一步建议学习顺序：

1. **详细推导SDR：从 ∣ h H w ∣ 2 → T r (H W) |h^Hw|^2 \rightarrow Tr(HW)**
2. **详细推导SCA：论文公式(26)→(28)到底怎么变凸**
3. **结合论文完整复现Beamforming优化部分**

这三个弄懂，你基本就能看懂90%的 UAV-ISAC优化论文。

给我生成这个概念的笔记obisidian版本md

已经生成好了 Obsidian 版本笔记：

这个版本按照你学习 ISAC 论文的路线整理：

- ✅ 凸优化基础
- ✅ 非凸优化为什么难
- ✅ SCA核心思想
- ✅ Taylor一阶近似数学推导
- ✅ SCA迭代过程
- ✅ SDR核心思想
- ✅ W = w w H W=ww^H 矩阵提升
- ✅ 二次形式转 Trace 形式
- ✅ Rank-1约束为什么产生
- ✅ 为什么可以松弛
- ✅ SCA和SDR区别对比表
- ✅ ISAC波束成形中的实际应用流程
- ✅ UAV-ISAC论文整体优化框架

建议你后续在 Obsidian 里面把这篇笔记和：

- UAV动力学建模
- MPC
- 凸优化
- 波束成形

建立双向链接。

下一步最适合继续学习的是：

**《SDR详细推导：从波束成形 ∣ h H w ∣ 2 |h^Hw|^2 到 T r (H W) Tr(HW) 》**

因为这是你后面看 ISAC、MIMO、RIS 论文最常遇到的数学核心。

SCA与SDR优化方法基础_Obsidian笔记.md

半正定是什么意思

这个问题非常关键，因为 **SDR（Semidefinite Relaxation，半正定松弛）**里面的“半正定”就是核心概念。

我们一步一步理解。

---

## 1. 先回顾：什么是正定？

在数学里面，一个矩阵可以描述一个二次函数：

f (x) = x T A x f(x)=x^TAx

例如：

A = [2 0 0 3] A= \begin{bmatrix} 2&0\\ 0&3 \end{bmatrix}

那么：

x T A x x^TAx

展开：

= 2 x 1 2 + 3 x 2 2 =2x_1^2+3x_2^2

因为：

x 1 2 ≥ 0 x_1^2\ge0 x 2 2 ≥ 0 x_2^2\ge0

所以：

x T A x > 0 x^TAx>0

除了：

x = 0 x=0

以外永远大于0。

这种矩阵叫：

## 正定矩阵（Positive Definite）

记：

A ≻ 0 A\succ0

含义：

> 对任何非零向量x，二次型一定为正。

---

## 2. 为什么叫“半”正定？

如果允许：

x T A x = 0 x^TAx=0

也可以。

那么：

A ⪰ 0 A\succeq0

叫：

## 半正定矩阵（Positive Semi-Definite, PSD）

数学定义：

对于任意向量：

x x

满足：

x T A x ≥ 0 x^TAx\ge0

就是半正定。

---

## 3. 一个简单例子

考虑：

A = [1 0 0 0] A= \begin{bmatrix} 1&0\\ 0&0 \end{bmatrix}

那么：

x = [x 1 x 2] x= \begin{bmatrix} x_1\\ x_2 \end{bmatrix}

计算：

x T A x x^TAx

得到：

= x 1 2 = x_1^2

因为：

x 1 2 ≥ 0 x_1^2\ge0

所以：

x T A x ≥ 0 x^TAx\ge0

但是：

如果：

x = [0 1] x= \begin{bmatrix} 0\\ 1 \end{bmatrix}

那么：

x T A x = 0 x^TAx=0

不是严格大于0。

所以：

它不是正定。

但是：

是半正定。

---

## 4. 几何理解

看函数：

f (x) = x T A x f(x)=x^TAx

## 正定

像一个碗：

`* * * * * * * _______________ 最低点唯一`

所有方向都向上。

---

## 半正定

像一个“碗+平面方向”：

`* * * * * ______________ 可以有平坦方向`

某些方向：

不会下降到负数。

---

## 5. 为什么SDR需要半正定？

回到通信问题。

波束：

w w

信号功率：

∣ h H w ∣ 2 |h^Hw|^2

展开：

= h H w w H h =h^Hww^Hh

定义：

W = w w H W=ww^H

注意：

这个矩阵一定满足：

W ⪰ 0 W\succeq0

为什么？

任意向量x：

x H W x x^HWx

代入：

= x H w w H x =x^Hww^Hx

整理：

= (w H x) ∗ (w H x) =(w^Hx)^*(w^Hx)

也就是：

= ∣ w H x ∣ 2 =|w^Hx|^2

平方一定：

≥ 0 \ge0

所以：

W = w w H W=ww^H

天然是半正定。

---

## 6. 为什么还有rank=1？

这里是SDR最关键。

假设：

w = [a b] w= \begin{bmatrix} a\\ b \end{bmatrix}

那么：

W = w w H W=ww^H

展开：

W = [a b] [a ∗,b ∗] W= \begin{bmatrix} a\\ b \end{bmatrix} [a^*,b^*]

得到：

W = [∣ a ∣ 2 a b ∗ b a ∗ ∣ b ∣ 2] W= \begin{bmatrix} |a|^2&ab^*\\ ba^*&|b|^2 \end{bmatrix}

这个矩阵：

只有一个方向。

所以：

r a n k (W) = 1 rank(W)=1

---

## 7. SDR为什么去掉rank约束？

原问题：

W = w w H W=ww^H

必须：

{ W ⪰ 0 r a n k (W) = 1 \begin{cases} W\succeq0\\ rank(W)=1 \end{cases}

问题：

r a n k (W) = 1 rank(W)=1

是非凸约束。

导致：

不能直接优化。

于是SDR：

删除：

r a n k (W) = 1 rank(W)=1

只保留：

W ⪰ 0 W\succeq0

变成：

代码

`原问题 W=wwᴴ ↓ 要求： 半正定 + rank=1 ↓ SDR松弛 ↓ 只要求： 半正定 ↓ 凸优化`

---

## 8. 在ISAC论文里的意义

论文波束优化：

原变量：

w m w_m

有：

∣ g m H w m ∣ 2 |g_m^Hw_m|^2

非凸。

令：

W m = w m w m H W_m=w_mw_m^H

之后：

W m ⪰ 0 W_m\succeq0

并且：

r a n k (W m) = 1 rank(W_m)=1

但是rank约束难。

所以：

SDR：

去掉：

r a n k (W m) = 1 rank(W_m)=1

然后用CVX求：

W m W_m

---

## 9. 你现在可以这样记

一句话：

> **半正定就是一个矩阵对应的二次函数永远不会小于0。**

在SDR里面：

> 因为 W = w w H W=ww^H 天然满足半正定，所以把波束向量问题转换成矩阵问题后，只保留 W ⪰ 0 W\succeq0 ，删除难处理的rank=1约束，从而把非凸问题变成凸优化问题。

你下一步最好学习：

**为什么 W = w w H W=ww^H 一定是 rank-1 半正定矩阵，以及如何从 W W 恢复 w w** 。

这两个点是看懂所有 ISAC 波束成形论文的关键。

把这个弄成obisidian标签给我

你这个截图里面的是 Zotero/Obsidian 里论文标签，转换成 **Obsidian标准标签格式（YAML + #标签）** 可以这样写：

## 方式1：Obsidian YAML标签（推荐）

放在笔记顶部：

YAML

```
---
tags:
  - alternating-optimization
  - beamforming-design
  - control-parametrization
  - ISAC
  - trajectory-optimization
  - UAV-enabled-ISAC-system
---
```

---

## 方式2：正文内标签

直接写：

Markdown

`#alternating-optimization #beamforming-design #control-parametrization #ISAC #trajectory-optimization #UAV-enabled-ISAC-system`

---

## 方式3：更适合你的ISAC知识库的规范化版本

我建议你统一一下命名，因为 Obsidian 标签最好不要太长、不要大量连字符。

改成：

YAML

```
---
tags:
  - ISAC
  - UAV
  - beamforming
  - trajectory-optimization
  - control
  - alternating-optimization
  - parameterization
---
```

这样以后你的知识库会更好管理。

例如：

你的论文笔记：

代码

`Li_2026_Control-Based_UAV_ISAC.md`

顶部：

YAML

```
---
title: A Control-Based Design of Beamforming and Trajectory for UAV-Enabled ISAC System

tags:
  - ISAC
  - UAV
  - beamforming
  - trajectory-optimization
  - control
  - alternating-optimization
  - SCA
  - SDR
---
```

之后你点：

#ISAC

就能看到：

点：

#trajectory-optimization

就能聚合：

对于你现在搭建的 **ISAC硕士论文知识库** ，建议采用：

代码

`领域标签 ↓ ISAC UAV MIMO 方法标签 ↓ SCA SDR MPC SQP 任务标签 ↓ beamforming trajectory-optimization resource-allocation 算法关系 ↓ alternating-optimization`

这样后面写开题报告会非常方便。

ChatGPT 可能会出错。请核查重要信息。