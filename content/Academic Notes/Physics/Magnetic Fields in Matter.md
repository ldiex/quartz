# 磁介质

## 磁化

### 磁介质的分类

* 顺磁体: 磁化方向和外场相同
* 抗磁体: 磁化方向和外场相反 （类似于一般电介质的性质）
* 铁磁体: 有外加磁场时表现出很强的顺磁性, 并且就算去掉外场后仍然能够保持磁性

### 磁偶极子的受力

直接类比电偶极子, 显然磁偶极子再均匀场中不受力, 但是受到力矩

$$
\boldsymbol{\tau} = \boldsymbol{m} \times \boldsymbol{B}
$$

其中$\boldsymbol{m} = I \boldsymbol{a}$为磁偶极子的磁矩, 这和电偶极子的所受力矩$\boldsymbol{\tau} = \boldsymbol{p} \times \boldsymbol{E}$是相同的.

于是, 再次类比电偶极子在非均匀场中受到的梯度力$\boldsymbol{F} = \nabla (\boldsymbol{p} \cdot \boldsymbol E)$, 我们有
$$
\boldsymbol{F} = \nabla (\boldsymbol{m} \cdot \boldsymbol B)
$$

### 顺磁性和抗磁性的原子解释

电子的两种磁矩

* 轨道磁矩: 在有外场时抵消外场, 贡献抗磁性

* 自旋磁矩: 若有偶数个电子, 总效应忽略不计, 原子总体表现出抗磁性；若有奇数个电子, 电子自旋可以顺应外场变化, 原子可能表现出顺磁性

### 磁化强度

$$
\boldsymbol{M} := \textit{单位体积内总的磁偶极矩}
$$

## 磁化物体的磁场

### 束缚电流

为描述某一个磁化强度为$\boldsymbol{M}$的磁化物体产生的磁场, 我们先计算一个磁偶极子产生的磁矢势

$$
\boldsymbol A (\boldsymbol r) = \dfrac{\mu_0}{4\pi}\frac{\boldsymbol m \times \boldsymbol r}{r^3}
$$
在现实模型中, 每个$\mathrm{d}\tau'$的体积元带有$\boldsymbol M \mathrm{d}\tau'$的磁偶极矩. 积分后, 上面的式子可以写成
$$
\boldsymbol A (\boldsymbol r) = \frac{\mu_0}{4\pi} \int \frac{1}{|\boldsymbol{r'-r}|}\left( \nabla'\times \boldsymbol {M(r')} \mathrm{d} \tau' + \boldsymbol{M(r')} \times \mathrm{d} \boldsymbol{a'} \right)
$$
其中有体电流
$$
\boxed{\boldsymbol J = \nabla \times \boldsymbol M}
$$
和面电流
$$
\boxed{\boldsymbol K = \boldsymbol M \times \boldsymbol{\hat n}}
$$
所以我们可以把$\boldsymbol {A(r)}$写成
$$
\boldsymbol{A(r)} = \frac{\mu_0}{4\pi} \int_{V} \frac{\boldsymbol {J(r')} \mathrm{d}\tau'}{|\boldsymbol{r'-r}|} + \frac{\mu_0}{4\pi} \int_{\delta V} \frac{\boldsymbol {K(r')} \mathrm{d}a'}{|\boldsymbol{r'-r}|}
$$
此式表明一个磁化物体的矢势是由整个物体中的体电流和边界上的面电流共同产生的

**例子: 求一个均匀磁化球体的磁场**

设$\boldsymbol M$沿着$z$轴方向, 空间某点关于球心的法向量$\boldsymbol{\hat n}$和$z$轴的夹角为$\theta$, 则有
$$
\boldsymbol {J} = \nabla \times \boldsymbol{M} = \boldsymbol{0}, \; \boldsymbol{K} = \boldsymbol{M} \times \boldsymbol{\hat n} = M \sin \theta \boldsymbol{\hat \varphi}
$$
类比一个带有均匀面电荷$\sigma$的旋转球壳, 会产生相似的面电流密度
$$
\boldsymbol K = \sigma \boldsymbol{\omega \times r}
$$
这个时候积分得到
$$
\boxed {\boldsymbol {A(r)} = \begin{cases} \dfrac{\mu_0 R \sigma}{3} (\boldsymbol{\omega \times r} ),&\text{球内} \\ \dfrac{\mu_0 R^4 \sigma}{3r^3} (\boldsymbol{\omega \times r}), &\text{球外}\end{cases}}
$$
且在球内的时候有
$$
\boldsymbol{B(r)} = \nabla \times \boldsymbol{A} = \frac{2}{3}\mu_0\sigma R\boldsymbol{\omega}
$$
利用$M = \sigma \omega R$, 代入上式, 即有
$$
\boldsymbol {B(r)} = \frac{2}{3}\mu_0\boldsymbol{M}
$$
注意这里的$M$还可以用螺线管参量$nI$来替换, 也就是说
$$
[K] = [M] = [nI]
$$
这三个量具有相同的单位

## 辅助场$\boldsymbol H$

### 磁介质中的安培定理

空间中的总电流由束缚电流和自由电流两部分构成
$$
\boldsymbol{J = J_b+ J_f}
$$
于是安培定理可以写成
$$
\frac{1}{\mu_0} (\nabla \times \boldsymbol{B}) = \boldsymbol J = \boldsymbol{J_b + J_f} = \boldsymbol{J_f} + \nabla \times \boldsymbol{M} \\
\implies \nabla \times \left( {\frac{\boldsymbol{B}}{\mu_0}} - \boldsymbol{M}\right) = \boldsymbol {J_f}
$$
令$\boxed{\displaystyle \boldsymbol H = {\frac{\boldsymbol{B}}{\mu_0}} - \boldsymbol{M}}$, 即有
$$
\nabla \times \boldsymbol{H} = \boldsymbol{J_f}
$$
也可以写成积分形式
$$
\oint \boldsymbol{H} \cdot \mathrm{d}\boldsymbol{l} = I_f
$$

在实际运用中, 我们更加常用$\boldsymbol{H}$或者$\boldsymbol{E}$来描述磁场或电场. 因为在实验中我们用一载流线圈可以产生一个磁场, 而$\boldsymbol{H}$只有电流决定, 和介质无关；而当我们需要产生一个电场时, 我们使用的电压计测得的是$\boldsymbol{E}$场的线积分, 和介质也无关

### 边界条件

对于$\boldsymbol{H}$场, 一般不在边界上连续: 
$$
\begin{aligned} H_{up}^{\perp} - H_{dn}^{\perp} &= -(M_{up}^{\perp} - M_{dn}^{\perp}) \\
\boldsymbol{H_{up}^{\parallel} - H_{dn}^{\parallel}} &= \boldsymbol{K_f \times \hat n} \end{aligned}
$$
对于$\boldsymbol{B}$场, 其垂直分量在边界上连续: 
$$
\begin{aligned} B_{up}^{\perp} - B_{dn}^{\perp} &= 0 \\
\boldsymbol{B_{up}^{\parallel} - B_{dn}^{\parallel}} &= \mu_0 \boldsymbol{K \times \hat n} \end{aligned}
$$
回忆电场: $\boldsymbol D$场的垂直分量连续, $\boldsymbol E$场的平行分量连续

## 线性与非线性介质

### 磁化率和磁导率

和电学不同, 我们把磁化率的定义写为
$$
\boxed{\boldsymbol M = \chi_m \boldsymbol H}
$$
遵从此关系的介质被称为线性介质, 于是对$\boldsymbol B$, 有
$$
\boldsymbol B = \mu_0 (\boldsymbol H  + \boldsymbol M) = \mu_0 (1 + \chi_m) \boldsymbol H = \mu \boldsymbol H
$$
其中$\displaystyle \boxed{\mu := \mu_0 (1 + \chi_m)}$称为材料的磁导率

从这个式子中可以看出, 线性材料中束缚电流密度是和自由电流密度成比例的
$$
\boldsymbol J_b = \nabla \times \boldsymbol M = \chi_m \nabla \times \boldsymbol H = \chi_m \boldsymbol J_f
$$

### 铁磁性

铁磁体显然是非线性介质, 因为即使外场消失, 其磁化状态依然能够得到保留. 
