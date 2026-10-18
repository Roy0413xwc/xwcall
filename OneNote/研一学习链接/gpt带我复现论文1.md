---
onenote-id: fcffc2e6-7bc4-4b10-ba53-06ceeac51528:1
---
**Optimal ISAC Beamforming Structure and Efficient Algorithms for Sum Rate and CRLB Balancing**

来自 \<https://ieeexplore.ieee.org/document/11523170>

先用gpt读完

再用copilot辅助理解代码

==🟡OBS_for_CRLB_ISAC\Fig2_trade_off_region\proposed_SCA.m==

![[gpt带我复现论文1 image.png]]

这一段的“计算依据”不是算法推导，而是**蒙特卡洛仿真的随机信道/目标场景生成**。也就是说，代码先随机造出一批通信信道和雷达目标参数，然后在这些随机场景上跑 SCA 算法，最后取平均性能。论文仿真部分也说明通信信道采用 Rayleigh fading，目标角度和 RCS 随机生成。

逐行看：

rng(1,'twister')

固定随机种子。作用是：每次运行代码，随机数都一样，这样你和作者、或者你自己多次运行，结果可复现。

alpha_all=0.1*(1+0.2*randn(M_max,1)).*exp(1j*2*pi*rand(M_max,1));

这是生成目标的复反射系数，也就是论文里的：

$﷐$$α$$﷮$$m$$﷯$

它可以理解成目标的 **RCS / 反射增益**。

这行代码分成两部分：

$0.1$$﷐$$1+0.2⋅$$randn$$﷯$

控制幅度，表示目标反射强度大约在 0.1 附近随机波动。

$﷐$$e$$﷮$$j$$2$$π$$⋅$$rand$$﷯$

控制相位，表示目标反射回来的信号有一个随机相位。

所以整体是：

$﷐$$α$$﷮$$m$$﷯$$=$$随机幅度$$×$$随机相位$

注意一个小细节：论文仿真部分写的是类似

$﷐$$α$$﷮$$m$$﷯$$=0.1$$﷐$$1+0.2$$﷐$$ν$$﷮$$m$$,$$q$$﷯$$﷯$$﷐$$e$$﷮$$2$$j$$π$$﷐$$ν$$﷮$$m$$,$$p$$﷯$$﷯$

其中 $ν$ 服从均匀分布；而你这份代码里幅度扰动用了 randn，是高斯分布。这个可能是作者代码版本和论文描述略有差异，或者是早期实验版本。复现时先保持源码不动，等能跑通后再考虑是否严格改成论文写法。

你可以用一个小例子理解：

A = randn(50,16,4);

B = A(2,:,:);          % size(B) 是 1×16×4

C = squeeze(A(2,:,:)); % size(C) 是 16×4

所以这里 squeeze 的目的就是：**把取出的第 channel 个三维信道样本，整理成正常的二维信道矩阵** $﷐$$N$$﷮$$t$$﷯$$×$$K$**。**

雷达感知要估计目标角度。目标角度不同，阵列接收到的相位差就不同。

所以需要一个函数描述：

如果目标在某个 $﷐$$θ$$﷮$$φ$$﷯$ 方向，阵列每根天线看到的相位是什么样的？

这就是 steering vector，阵列导向向量。

==🟡OBS_for_CRLB_ISAC\Fig1_convergence\propose_SCA.m==

![[gpt带我复现论文1 image 1.png]]

![[gpt带我复现论文1 image 2.png]]

\4. 通信辅助变量计算

![[gpt带我复现论文1 image 3.png]]

![[gpt带我复现论文1 image 4.png]]

![[gpt带我复现论文1 image 5.png]]

![[gpt带我复现论文1 image 6.png]]

![[gpt带我复现论文1 image 7.png]]

![[gpt带我复现论文1 image 8.png]]

![[gpt带我复现论文1 image 9.png]]

![[gpt带我复现论文1 image 10.png]]