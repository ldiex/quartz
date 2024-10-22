当光照射到折射率为$n_1$的介质与折射率为$n_2$的第二介质之间的界面时, 可能会发生光的反射和折射. *菲涅尔方程*给出了两个[[Polarization | 偏振]] 分量中的每一个的反射波电场与入射波电场之比, 以及透射波电场与入射波电场之比

# S 和 P 偏振
对于入射波的两个不同的线性偏振分量, 有两组菲涅耳系数. 由于任何偏振态都可以分解为两个正交线性偏振的组合, 因此这足以解决任何问题

s偏振是指垂直于*入射面 (plane of incidence)*（也就是平行于界面, 下面推导中的$z$方向）的波电场的偏振；那么磁场位于入射平面内.  p偏振是指电场在*入射面*（下面推导中的$x-y$平面）内的偏振；那么磁场垂直于入射平面. 
![[光学-Fresnel方程.png]]
# 偏振光的反射率
我们将从界面反射的功率和入射功率的比值称为*反射率* $R$, 折射到第二介质中的部分功率和入射功率的壁纸称为*折射率* $T$

s偏振光的反射率为
$$
R_\mathrm{s}=\left|\frac{Z_2\cos\theta_\mathrm{i}-Z_1\cos\theta_\mathrm{t}}{Z_2\cos\theta_\mathrm{i}+Z_1\cos\theta_\mathrm{t}}\right|^2
$$
p偏振光的反射率为
$$
R_\mathrm{p}=\left|\frac{Z_2\cos\theta_\mathrm{t}-Z_1\cos\theta_\mathrm{i}}{Z_2\cos\theta_\mathrm{t}+Z_1\cos\theta_\mathrm{i}}\right|^2
$$
其中$Z_1,Z_2$分别是介质$1, 2$的*波阻抗*

如果介质是非磁性的（即$\mu_1  = \mu_2 = \mu_0$）, 那么波阻抗只有折射率决定
$$
Z_i = \dfrac{Z_0}{n_i}
$$
由此我们得到
$$\begin{aligned}R_\mathrm{s}=\left|\frac{n_1\cos\theta_\mathrm{i}-n_2\cos\theta_\mathrm{t}}{n_1\cos\theta_\mathrm{i}+n_2\cos\theta_\mathrm{t}}\right|^2=\left|\frac{n_1\cos\theta_\mathrm{i}-n_2\sqrt{1-\left(\frac{n_1}{n_2}\sin\theta_\mathrm{i}\right)^2}}{n_1\cos\theta_\mathrm{i}+n_2\sqrt{1-\left(\frac{n_1}{n_2}\sin\theta_\mathrm{i}\right)^2}}\right|^2,\\\\R_\mathrm{p}=\left|\frac{n_1\cos\theta_\mathrm{t}-n_2\cos\theta_\mathrm{i}}{n_1\cos\theta_\mathrm{t}+n_2\cos\theta_\mathrm{i}}\right|^2=\left|\frac{n_1\sqrt{1-\left(\frac{n_1}{n_2}\sin\theta_\mathrm{i}\right)^2}-n_2\cos\theta_\mathrm{i}}{n_1\sqrt{1-\left(\frac{n_1}{n_2}\sin\theta_\mathrm{i}\right)^2}+n_2\cos\theta_\mathrm{i}}\right|^2.\end{aligned}$$
# 偏振光的透射率
根据能量守恒有
$$
T_s = 1- R_s ; \quad T_p  = 1 - R_p
$$
# Brewster 角
令$R_p = 0$, 结合 Snell 定律$n_1\sin \theta_1 = n_2 \sin \theta_2$, 可以得到
$$
\tan \theta_i = \dfrac{n_2}{n_1}
$$
这里的$\theta_i = \theta_B$ 为*Brewster 角*, 这个时候, 反射光线为完全偏振光, 仅有s方向的振动分量

# 半波损失
当波从波疏介质垂直入射到波密介质并从波疏介质和波密介质的分界面反射回波疏介质时,反射波在离开反射点时的振动相位相对于入射波到达入 射点时的振动相位相差$π$,也就是发生了$π$相位突变,这种现象称为*半波损失*

# 需要了解的结论
1. 自然光（部分偏振光）入射 - 反射和折射是部分偏振光
2. 圆偏振光（椭圆偏振光）入射 - 反射和折射是椭圆偏振光
3. 线偏振光入射 - 反射和折射是线偏振光, 但是振动面有旋转
4. 全反射 - 反射光是椭圆偏振光
5. Brewster角入射 - 反射光是s线偏振光
