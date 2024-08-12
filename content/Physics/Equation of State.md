# 状态参数和物态方程
## 状态参数
一个确定的平衡态可以用一些基本的参量描述，这些表征系统状态的参数被称为*状态参数*，如 体积$V$, 压强$p$, 粒子数$N$, 温度$T$
## 物态方程
即约束系统状态参数的方程
$$
f(T, p, V) = 0
$$
- 状态方程的具体形式由实验决定
- $T, p, V$中的任意两个可以完全确定系统的状态

# 理想气体物态方程
## 几个实验定律
### Boyle 定律
$$
pV = C \; (\text{when } T = \text{constant})
$$
### Gay-Lussac 定律
$$
V = V_0 (1 + \alpha_V t) \; (\text{when } p = \text{constant})
$$
### Charles 定律
$$
p = p_0(1 + \alpha_p t) \; (\text{when } V = \text{constant})
$$
### *Avogadro 定律*
当气体压强趋于零时，同温同压的$1 \text{mol}$的任何气体所占的体积都相同
## 理想气体物态方程
$$
pV = \nu RT
$$
其中$R \approx 8.31 \mathrm{J} \cdot \mathrm{mol}^{-1} \cdot \mathrm{K}^{-1}$为*普适气体常量*
可给出*定压理想气体温标* $T = \dfrac{V^*}{V_{tr}} \times 273.16 \mathrm{K}$
在压强趋于零的极限情况下，一切气体都严格遵守理想气体状态方程. 而在通常的压强下各种气体只是近似地遵循此方程
## Dalton 分压定律
对于混合理想气体，其每一组分的体积、温度和混合气体相同时
$$
p = p_1 + p_2 + \cdots + p_n = \sum_i p_i
$$
定义各组分的*分压*为$p_i = \dfrac{\nu_i}{\nu} p$
# 非理想气体物态方程
## Van der Waals 方程
考虑到气体分子间吸引力和排斥力的作用，修正理想气体物态方程为
$$
(p + a\dfrac{\nu^2}{V^2})(V - \nu b) = \nu RT
$$
对于$1 \; \mathrm{mol}$气体有$\displaystyle \boxed{(p + a / V_m^2)(V_m - b) = RT}$
上面的$a,b$对于一定的气体是常量，可由实验测定. 在低温或高压的情况下，Van der Waals方程偏离实际情况较大
## Onnes 方程
$$
\begin{aligned}
pV_m &= A + Bp + Cp^2 +\cdots \\
pV_m &= A' + B'V_m^{-1} + C'V_m^{-2} + \cdots
\end{aligned}
$$
当$p \to 0, V_m \to \infty$应得到理想气体方程，故有$A = A' = RT$
剩下的系数被称为*位力系数*，由实验测定，随着级数的增加迅速减少
Van der Waals 方程也可用这样的级数表示
# 广义坐标和物态方程的普遍形式
把系统的温度、压强、表面张力、拉伸力、电场强度等强度量称为*广义力*$X$
把系统的体积、面积、长度、电量等广延量称为*广义坐标*$Y$
则物态方程式所有相关广义力和广义坐标的函数
$$
f(T; X_1, Y_1; X_2, Y_2; \cdots) = 0
$$
广义力和广义坐标可以两两配对，温度可以和*熵*配对
