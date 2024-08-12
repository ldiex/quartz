## 瞬时功率
$$
p(t) = v(t) i(t)
$$
## 平均功率
$$
\begin{aligned}
P &= \frac{1}{T}\int_0^T p(t) \mathrm{d} t \\
&= \frac{1}{2} V_m I_m \cos(\theta_v -\theta_i) \\
&= V_{\text{rms}}I_{\text{rms}}\cos(\theta_v - \theta_i)
\end{aligned}
$$
这里$V_{\text{rms}},I_{\text{rms}}$为电压和电流的有效值
## 视在功率
在平均功率的计算式中
$$
P = VI \cos(\theta_v -\theta_i) = S\cos(\theta_v -\theta_i) 
$$
定义**视在功率**
$$
\boxed{S = VI}
$$
为电压和电流有效值的乘积
由此定义**功率因数**
$$
	\boxed{\text{pf} = \frac{P}{S} = \cos(\theta_v -\theta_i)}
$$
这里把$\theta_v - \theta_i$称为**功率因数角**
## 复功率
交流负载所吸收的**复功率**$\boldsymbol S$被定义为电压和**电流的共轭复数**的乘积的**一半**
$$
\boldsymbol S = \frac{1}{2} \boldsymbol {V} \boldsymbol I^* = \boldsymbol {V}_{\text{rms}} \boldsymbol {I}_{\text{rms}}^*
$$
这里的复有效值为
$$
\boldsymbol {V}_{\text{rms}} = \frac{\boldsymbol V}{\sqrt{2}};\; \boldsymbol {I}_{\text{rms}} = \frac{\boldsymbol I}{\sqrt{2}}
$$
那么我们可以得到
1. **用功功率**（即平均功率）$=P=\text{Re} (\boldsymbol S)$
2. **无功功率** $=Q=\text{Im}(\boldsymbol S)$
3. 视在功率 $=S=\left|{\boldsymbol S}\right|$
4. 功率因数$=\dfrac{P}{S}$

# 拓展
[[Resonant Circuit and Quality Factor Q|谐振电路和品质因子]]
[[Three-phase Circuit#三相电]]