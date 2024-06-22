# 响应函数
## 体膨胀系数
$$
\alpha = \frac{1}{V} \left(\dfrac{\partial {V}}{\partial {T}}\right)_p
$$
## 压强系数
$$
\beta = \frac{1}{p} \left( \dfrac{\partial {p}}{\partial {T}} \right)_V
$$
## 等温压缩系数
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
