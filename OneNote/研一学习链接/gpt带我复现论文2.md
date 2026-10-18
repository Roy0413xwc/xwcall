---
onenote-id: 6e5f1ec7-f78e-4302-b74f-c26666b18bb6:1
---
2026.6.12

| **优先级** | **论文** | **年份/篇幅** | **方向** | **IEEE Xplore** | **GitHub** | **复现建议** |
| --- | --- | --- | --- | --- | --- | --- |
| **1** | **NOMA Empowered Integrated Sensing and Communication** | 2022，5页 | ISAC + NOMA + 波束优化/资源权衡 | https://ieeexplore.ieee.org/document/9668964 | https://github.com/zhaolin820/noma-empowered-integrated-sensing-and-communication | **最适合今天做**。仓库有 main.m 和完整 function 文件夹，入口明确。README 写明 MATLAB + CVX，运行 main.m。唯一注意：main.m 里写了 cvx_solver mosek，你没有 MOSEK 就改成 cvx_solver sdpt3。([GitHub](https://github.com/zhaolin820/noma-empowered-integrated-sensing-and-communication)) |

来自 \<https://chatgpt.com/g/g-p-69fde43cf40c8191b4ab3deff5ea899a-xwc/c/6a2b7965-9f0c-83ee-867c-655c3dda5e3b>

SIC = **Successive Interference Cancellation，串行干扰消除**。

![[gpt带我复现论文2 image.png]]

![[gpt带我复现论文2 image 1.png]]

**NOMA = 叠加发送，强弱分功率，强用户做 SIC。**

更具体一点：

弱用户：分大功率，直接解自己，把强用户当干扰。

强用户：先解弱用户，消掉弱用户，再解自己。

NOMA 的 SIC 规则是：用户 $k$ 可以消除所有比它弱的用户 $j$$<$$k$，但会把更强的用户 $j$$>$$k$ 当干扰。论文也写到，user $K$ 通过 SIC 消除了所有其他用户的干扰，所以速率式只有噪声项，没有其他用户干扰项。

==🟡正式读论文==

![[gpt带我复现论文2 image 2.png]]