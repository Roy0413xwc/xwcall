---
onenote-id: 898d50e9-b91e-4253-b28e-f95b23c0acd0:1
---
[(12 封私信 / 80 条消息) MATLAB 学习路径：无线通信 - 知乎](https://zhuanlan.zhihu.com/p/1950935984364557892)

2026/5/27

[MATLAB 入门之旅 | 自定进度在线课程 - MATLAB & Simulink](https://matlabacademy.mathworks.com/cn/details/matlab-onramp/gettingstarted)

==🟡自带笔记==

[MATLAB 入门之旅 Quick Reference](https://matlabacademy.mathworks.com/artifacts/quick-reference.html?course=gettingstarted&language=cn&release=v2)2026.5.28已完成

2026/5/31

[Simulink 入门之旅 | 自定进度在线课程 - MATLAB & Simulink](https://matlabacademy.mathworks.com/cn/details/simulink-onramp/simulink)两小时完成

2026/5/31开始,6.7

[无线通信入门之旅 | 自定进度在线课程 - MATLAB & Simulink](https://matlabacademy.mathworks.com/cn/details/wireless-communications-onramp/wireless)

符号是信息单位，采样点是波形单位。一个符号为了变成可传输波形，通常要用多个采样点表示。

sigOut = awgn(sig,SNR,"measured")

MATLAB 先测量 sig 的实际功率，然后根据你设定的 SNR 自动计算应该加多大的噪声。

也就是 MATLAB 内部大概做了这件事：$﷐$$P$$﷮$$n$$﷯$$=$$﷐$$﷐$$P$$﷮$$s$$﷯$$﷮$$﷐$$10$$﷮$$﷐$$SNR$$﷮$$d$$B$$﷯$$/10$$﷯$$﷯$

滤波器延迟没看明白

一句话总结：

**低通 FIR 滤波器通常是对称的，真正的滤波作用集中在滤波器中心，因此输出要等到中心位置才形成，所以延迟等于滤波器长度的一半。**

![[gpt学无线通信matlab教程 image.png]]

多径 = 信号在空间传播过程中发生的现象

AWGN = 接收机或环境中叠加的随机噪声

所以先经过多径信道，再叠加噪声。

你先抓住一句话：**多径就是同一个信号经过不同路径、带着不同延迟和衰减，到达接收机后叠加在一起。**

![[gpt学无线通信matlab教程 image 1.png]]

频域子载波符号 → 时域 OFDM 信号

数学上可以写成：$x$$﷐$$n$$﷯$$=$$﷐$$1$$﷮$$N$$﷯$$﷐$$k$$=0$$﷮$$N$$−$$1$$﷮$$X$$﷯$$﷐$$k$$﷯$$﷐$$e$$﷮$$j$$2$$π$$kn$$/$$N$$﷯$

你现在不需要死记这个公式，先理解：**IFFT 把一组频域 QAM 符号合成为一个时域 OFDM 波形。**

ofdmmod文档

![[gpt学无线通信matlab教程 image 2.png]]