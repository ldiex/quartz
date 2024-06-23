# 响应函数
引入如下参数的原因是这些参量是容易测量的，且**可以帮助描述除了理想气体之外的一般气体甚至是固体和液体的性质，并可由此得到对应的物态方程**
## 体膨胀系数
$$
\alpha = \frac{1}{V} \left(\dfrac{\partial {V}}{\partial {T}}\right)_p
$$
## 压强系数
$$
\beta = \frac{1}{p} \left( \dfrac{\partial {p}}{\partial {T}} \right)_V
$$
## 等温压缩系数
表示在等温条件下，单位受到的压力变化能够造成多少体积比例的变化
$$
\kappa_T = - \frac{1}{V}\left( \dfrac{\partial {V}}{\partial {p}} \right)_T
$$
# 理想气体的响应函数
$$
\alpha = \frac{1}{T},\; \beta = \frac{1}{T}, \; \kappa_T = \frac{1}{p}
$$
![[热学-响应函数推到物态方程.png]]
具体说明：
$$
\begin{aligned}
\mathrm{d} V &= \frac{\nu R}{pV} V \mathrm{d} T - \left(\frac{1}{p} + \frac{a}{V}\right)V\mathrm{d} p \\
\implies p\mathrm{d} V &= \nu R \mathrm{d} T - (V + ap) \mathrm{d} p \\
\implies \mathrm{d}(pV) &= \nu R\mathrm{d} T -\frac{1}{2}a \mathrm{d} (p^2) \\
\implies pV &= \nu RT - \frac{1}{2}ap^2 + C^\boxed{= 0}
\end{aligned}
$$

全微分的计算参考[[Differential of Multivariable Functions|多元函数微分]]
