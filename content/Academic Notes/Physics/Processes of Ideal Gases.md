# 理想气体经过不同过程的能量变化和热容

| 过程   | 系统吸热                          | 对外界做功                         | 内能变化             | 热容                              |
| ---- | ----------------------------- | ----------------------------- | ---------------- | ------------------------------- |
| 等体过程 | $C_V(T_2 - T_1)$              | $0$                           | $C_V(T_2 - T_1)$ | $C_V$                           |
| 等压过程 | $C_p(T_2 - T_1)$              | $p(V_2 - V_1)$                | $C_V(T_2 - T_1)$ | $C_p$                           |
| 等温过程 | $\nu RT \ln \dfrac{V_2}{V_1}$ | $\nu RT \ln \dfrac{V_2}{V_1}$ | $0$              | $\infty$                        |
| 绝热过程 | $0$                           | $-C_V(T_2 - T_1)$             | $C_V(T_2 - T_1)$ | $0$                             |
| 多方过程 | $C_n(T_2 - T_1)$              | $(C_n - C_V)(T_2 - T_1)$      | $C_V(T_2 - T_1)$ | $\dfrac{n - \gamma}{n - 1} C_V$ |

其中，对于理想气体而言，其[[The First Law of Thermodynamics|内能]]正比于温度$T$，故它的内能变化始终为$C_V(T_2-T_1)$，对外界做功可以通过积分$\displaystyle \int_0^1 p \mathrm{d}V$来求得，再利用[[The First Law of Thermodynamics|热力学第一定律]]就可以求得热量交换
# 绝热过程
即没有热量传递$\mathrm{d}Q = 0$的过程。在**准静态**的情况下，其过程方程为
$$
pV^\gamma = \text{const}
$$
或者
$$
TV^{\gamma - 1} =\text{const} \quad T^{\gamma}p^{1 - \gamma} = \text{const}
$$
其中*绝热指数*
$$
\gamma = \dfrac{C_p}{C_V}
$$
如果我们计算绝热线和等温线的斜率
$$
\left( \frac{ \mathrm{d} p }{ \mathrm{d} V }  \right)_T = -\dfrac{p}{V},\quad \left( \frac{ \mathrm{d} p }{ \mathrm{d} V }  \right)_S = -\dfrac{\gamma p}{V}
$$
因为$\gamma>1$，**所以绝热线比等温线更加陡峭**，也就是说，膨胀相同的体积，压强在绝热过程中下降得更快
> [!tip] 大气的绝热性质
> 干燥大气中沿垂直高度发生的过程可以近似为准静态的绝热过程，由此可以推导出大气温度随高度的变化率
> $$\frac{ \mathrm{d} T }{ \mathrm{d} z } = - \dfrac{mg}{k_B} \dfrac{\gamma-1}{\gamma}$$
# 多方过程
过程方程的状态方程如下
$$
pV^n = \text{const}
$$
它可以统一描述等压、等体、等温、绝热过程
>[!Note] 负热容现象
> 当$1 < n < \gamma$时，热容$C$为负数，即物体温度升高的同时放热
> - 膨胀过程中系统对外界所做的功大于它所吸收的热量，一部分功是靠减少内能（降低系统温度）来实现的；
> - 压缩过程中外界对系统所做的功大于气体放出的热量，一部分能量存储在系统中（系统温度升高）。
# Van der Waals气体的情况
## 等温过程
对于单位摩尔[[Van der Waals Equation of State|Van der Waals]]气体，其等温过程
$$
\begin{aligned}
W_m = \int_{V_{1m}}^{V_{2m}} p\mathrm{d} V   & = \int_{V_{1m}}^{V_{2m}} \left( \dfrac{RT}{V_m - b} -\dfrac{a}{V_m^2} \right) \mathrm{d} V_m  \\
 & = RT \ln \left( \dfrac{V_{2m}-b}{V_{1m}-b} \right)  + a\left( \dfrac{1}{V_{1m}}-\dfrac{1}{V_{2m}} \right) 
\end{aligned}
$$
而对于$\nu$摩尔的情况，由量纲分析可以得出
$$
W = \nu RT \ln\dfrac{V_2-\nu b}{V_1-\nu b} + a\left( \dfrac{
\nu^2
}{V_{1m}}-\dfrac{\nu^2}{V_{2m}} \right)
$$
回忆[[The First Law of Thermodynamics#Van der Waals气体的内能|Van der Waals气体的内能]]
$$
U = \int_{T_0}^T C_V\mathrm{d} T + U_0 - \dfrac{a\nu^2}{V}
$$
我们可以发现
$$
W_T = \nu RT \ln \dfrac{V_2'}{V_1'} + \left( \Delta U \right)_T
$$
也就是说Van der Waals气体在等温过程中对外做的功包含两个部分：修正气体体积后看作为理想气体对外做的功，和等温过程中其内能的改变量
# 绝热节流过程
## Joule-Thomson 实验
*多孔塞*：由多孔物质（如棉絮）做成的装置，对气流有较大的阻滞作用，使气体不容易很快通过它，从而能在两边维持一定的压强差

具体地讲，设多孔塞的左边压强维持在较高的数值$p_1$，气体经过多孔塞后压强降为右边的$p_2$，在稳定状态时，用温度计$T_1$和$T_2$分别测量两边的温度。

这种在绝热条件下高压气体经过多孔塞流到低压一边的过程叫做*绝热节流过程*
## 绝热节流过程中的不变量
设在$\Delta t$时间内，有一定量的高压气体通过多孔塞，状态从$(p_1, V_1, T_1)$变成$(p_2, V_2, T_2)$，则它对外界的做功为$p_2V_2 - p_1V_1$，由于过程绝热，由[[The First Law of Thermodynamics|热力学第一定律]]有
$$
U_2 - U_1 = p_1V_1 - p_2V_2 \iff U_1 + p_1V_1 = U_2 + p_2V_2
$$
即
$$
H_1 = H_2
$$
也就是说，**绝热节流过程是等焓过程**
## J-T 系数
对于理想气体，[[The First Law of Thermodynamics#焓|焓]]$H = C_pT$只是温度的函数，所以它在节流过程中温度不发生改变，但是对于实际气体而言，由于其焓还和压强（体积）有关，所以它在节流过程前后会有温度的变化，为了表示在节流膨胀过程后，随压强的稍许降低而引起的温度变化，引入*J-T系数*$\alpha$
$$
\alpha = \left(\dfrac{\partial {T}}{\partial {p}}\right)_H
$$
在准静态过程中，考虑焓$H(T,p)$[[Differential of Multivariable Functions#全微分|全微分]]（体积可由[[Equation of State#状态参数和物态方程|状态方程]]确定，$V = f(T,p)$）
$$
\mathrm{d}H = \left( \frac{ \partial H }{ \partial T }  \right)_p \mathrm{d}T+ \left( \frac{ \partial H }{ \partial p }  \right)_T \mathrm{d}p
$$
对于等焓过程，即有
$$
\alpha = \left( \frac{ \partial T }{ \partial p }  \right)_H = - \dfrac{\left( \frac{ \partial H }{ \partial p }  \right)_T}{\left( \frac{ \partial H }{ \partial T }  \right)_p } = -\dfrac{1}{C_p} \left( \frac{ \partial H }{ \partial p }  \right)_T
$$
对于一般临界温度不太低的气体如氮、氧、空气等，在常温下节流后温度都降低，$\alpha > 0$，称为*制冷效应*（或*正效应*）；对于临界温度很低的气体如氢气，在常温下节流温度反而升高，$\alpha < 0$，称为*负效应*。

节流制冷过程可用于气体降温和液化
# 循环过程
*循环过程*是一系列传递热量并做功的热力学过程组成的集合，通过压强、温度等状态变量的变化，**最终使热力学系统回到初始状态**。

状态量只依赖于热力学状态，沿热力学循环路径对此类物理量的路径积分结果为零；而像热量和功这样的过程量与循环过程有关，路径积分不为零

循环过程具有两个方向
- 正循环，顺时针，对外做功
- 逆循环，逆时针，做负功
## 热机
*热机*是能够将热源提供的一部分热量转化成为对外输出机械能的机器。热机的工作模式一般可以简化为一个循环过程，其总的效果就是利用从高温热源吸收的热量$Q_1$对外做功$W$

定义热机的*循环效率*为其对外做的有效功和其在**高温热源**吸收（高温热源、吸收热量两个限定缺一不可）的热量之比
$$
\eta = \dfrac{W}{Q_1} = \dfrac{Q_1 - Q_2}{Q_1} = 1-\dfrac{Q_2}{Q_1}
$$
## 制冷机
*制冷机*又称为*热泵*，是一个可以将热从一个较低温的热源转移到较高温的热源的机械装置，它也可以用一个循环过程来描述，其循环效果为利用外界做功$W$从低温热源处吸热$Q_2$，保持其低温环境

**注意这里的$Q_2$是从低温热源吸取的热量（即低温等温过程吸取的热量），而不是整个循环吸取的热量**

同理可定义制冷机的循环效率，或称为*制冷系数*
$$
\varepsilon = \dfrac{Q_2}{W} = \dfrac{Q_1}{W} - 1 = \dfrac{1}{\eta} - 1
$$
由此可知，对于一个循环过程，**正循环的热机效率越高，逆循环的制冷系数越低**
## Carnot 循环
*Carnot循环*是**工质只与两个恒温热源交换热量**的理想化循环，其中 
- 与两个恒温热源交换热量的过程：两个等温过程；
- 不与其它热源交换热量的过程：两个绝热过程。

可以计算得到理想Carnot循环的效率为
$$
\eta = 1 - \dfrac{Q_2}{Q_1} = 1 - \dfrac{T_2}{T_1}
$$
由此可知理想气体卡诺热机的效率**仅由两个热源的温度决定**。

在 $T-S$ 图上，任意工质的等温过程表示为一横线，任意工质的绝热过程表示为一竖线。故**任意工质的卡诺循环在 $T-S$ 图上表示为一个长方形**。

### Carnot热机效率对实际热机的指导
由Carnot热机的循环效率可知，提高效率的重要途经就是**要提高高温热源的温度和降低低温热源的温度**

从理论上，若要提高Carnot热机的效率，降低低温热源的温度比提高高温热源的温度更加有效，这是因为
$$
\frac{ \partial \eta }{ \partial T_1 }  = \dfrac{T_2}{T_1^{2}},\;\frac{ \partial \eta }{ \partial T_2 } = -\dfrac{1}{T_1} = -\dfrac{T_1}{T_1^{2}} \implies \left|\frac{ \partial \eta }{ \partial T_2 } \right|  > \left|\frac{ \partial \eta }{ \partial T_1 } \right|
$$
而对于实际热机而言，由于低温热源一般为大气、水等自然环境，故提高高温热源的温度更加实际，工作物质的燃烧温度越高，热机效率也就越高，这也是为什么在热机效率上
$$
\text{液体燃料火箭} > \text{柴油机} > \text{汽油机} > \text{蒸汽机}
$$
的主要原因