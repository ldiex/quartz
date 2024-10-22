# 波的叠加和干涉
## 波的叠加原理
**波的独立传播定律**: 当两列（或多列）波同时存在时, 在它们的交迭区域内, 每个点的**振动**是各列波单独在该点产生振动的线性迭加, 表述为: 
$$
\vec{U} (p, t) = \vec{U}_1 (p, t) + \vec{U}_2 (p, t)+ \cdots
$$
**注意这里独立传播的是振动, 而不是光强或者振幅**
光波在真空中总是独立传播的, 而在媒质中, 有时会违反独立传播定律, 出现“*非线性*”
## 波的干涉和相干条件
合成波
$$
\tilde U(p, t) = \tilde U_1(p, t) + \tilde U_2(p, t)
$$
合成波的强度
$$
\begin{aligned}
I(p) &= \overline{\tilde U(p, t) \cdot \tilde U^*(p, t)} \\
&= I_1(p) + I_2(p) + \overline{2\boldsymbol{A}_1(p) \cdot \boldsymbol A_2(p) \cos [(\omega_1 - \omega_2)t + \delta(p)]}
\end{aligned}
$$
其中`\overline`表示平均值, 且有
$$
\delta(p) = \varphi_1(p) - \varphi_2(p)
$$
和*干涉项*
$$
\overline{2\boldsymbol{A}_1(p) \cdot \boldsymbol A_2(p) \cos [(\omega_1 - \omega_2)t + \delta(p)]}
$$
要让上面这项不为$0$, 我们有*相干条件*
- 频率相同
- 存在着相互平行的振动分量
- 存在着稳定的相位差
## 普通光源发光的机制
原子和分子（微观客体）内部的能量改变特点: 
- 不同原子或分子所发射的波列在振动方向和位相上相互独立, 没有联系
- 每个原子或分子发光的持续时间极短
所以两个普通光源发出的光波之间很难相干
> [!note]
>几个重要的时间间隔: 
> 1. 光扰动的时间周期:  $T \sim 10^{-15}$ sec 
> 2. 实验观测的时间（人眼的响应时间）:  $τ \sim 10^{-1}$ sec 
> 3. 探测器响应时间: $\Delta t \sim 10^{-9}$ sec

由于$τ >> \Delta t>> T$ 所以**无论是实际观察还是仪器接收, 得到的都不可能是某一瞬间的扰动分布, 而只能是扰动强度的时间平均值,  即*强度*. ** 

**相干光源和非相干光源**: 
- 两光源间有固定的位相差, 因而按振幅进行迭加, 那么它们称为*相干光源*
- 而若两光源之间没有固定的位相差, 因而按强度进行迭加, 则称为*非相干光源*
## 干涉的反衬度
*反衬度（可见度）*: 
$$
\gamma = \dfrac{I_M - I_m}{I_M + I_m},\quad 0 \le \gamma \le 1
$$
对于两束光的干涉
$$
\gamma = \dfrac{\boldsymbol A_1 \cdot \boldsymbol A_2 \cdot 1 - \boldsymbol A_1 \cdot \boldsymbol A_2 \cdot (-1)}{I_1 + I_2} = \dfrac{2\boldsymbol A_1 \cdot \boldsymbol A_2}{I_1 + I_2}
$$
此时$I = (I_1 + I_2)(1 + \gamma \cos \delta)$

# 两个点源的干涉
## 两列球面波的干涉
设有两个强度相等的相干光源$Q_1, Q_2$, 在$r_1, r_2 \gg Q_1Q_2$的情况下有
$$
\delta(p) = \dfrac{2\pi}{\lambda}(r_1 - r_2)
$$
故条纹
$$
\begin{cases}
\text{max} , & r_1 - r_2 = k \lambda \\
\text{min} , & r_1 - r_2 = (k + 1/2)\lambda
\end{cases}
$$
等强面为回转双曲面
![[光学-干涉双曲面.png]]
## 杨氏（T. Young, 1801）双缝实验
![[光学-杨氏双缝.png]]
强度分布
$$
I(x',y') = 4\left(\dfrac{a}{D}\right)^2\cos^2\left(\dfrac{\pi d}{\lambda D} x'\right)
$$
条纹间距
$$
\Delta x = \dfrac{\lambda D}{d}
$$
Young氏实验最重要的一点在于: 利用次光源分解, 巧妙地获得了相干光源
## 两束平行光的干涉
两束平行光束的传播方向为$(\alpha_1, \beta_1, \gamma_1), (\alpha_2, \beta_2, \gamma_2)$
![[光学-平行光干涉.png]]
在$z = 0$的波前上
$$
\begin{gathered}
\left.\left\{\begin{aligned}\varphi_1(x^{\prime},y^{\prime})&=k(x^{\prime}\cos\alpha_1+y^{\prime}\cos\beta_1)-\varphi_{10}\\\varphi_2(x^{\prime},y^{\prime})&=k(x^{\prime}\cos\alpha_2+y^{\prime}\cos\beta_2)-\varphi_{20}\end{aligned}\right.\right. \\ \\
\delta(x^{\prime},y^{\prime})=kx^{\prime}(\cos\alpha_1-\cos\alpha_2)+ky^{\prime}(\cos\beta_1-\cos\beta_2) 
+\varphi_{20}-\varphi_{10} \\\\
I(x^{\prime},y^{\prime})=(A_1^2+A_2^2)\{1+\gamma\cos[kx^{\prime}(\cos\alpha_1-\cos\alpha_2) \\
+ky'(\cos\beta_1-\cos\beta_2)+\varphi_{20}-\varphi_{10}]\} 
\end{gathered}
$$
有反衬度
$$
\gamma=\frac{2A_1/A_2}{1+\left(A_1/A_2\right)^2}=\frac{2A_1A_2}{A_1^2+A_2^2}
$$
### 空间频率
凡是有周期, 就可以引入频率

干涉条纹的间隔
$$
\begin{cases}\Delta x'=\dfrac{\lambda}{\cos\alpha_1-\cos\alpha_2}\\\Delta y'=\dfrac{\lambda}{\cos\beta_1-\cos\beta_2}&\end{cases}
$$
条纹的*空间频率*
$$
\begin{cases}f_{x^{\prime}}=\dfrac{\cos\alpha_1-\cos\alpha_2}{\lambda}\\f_{y^{\prime}}=\dfrac{\cos\beta_1-\cos\beta_2}{\lambda}\end{cases}
$$
![[Images/光学-空间频率.png]]

