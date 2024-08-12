`# 简谐振动
简谐振动就是旋转矢量
$$
x = A\cos(\omega t + \phi) = \text{Re} (Ae^{i(\omega t + \phi)})
$$
## 同方向不同频率简谐振动的合成
设两个同方向不同频率的简谐振动拥有相同的振幅和初相位
$$
\begin{aligned}
x_1 &= A\cos(\omega_1 t + \phi), \; x_2 = A\cos(\omega_2t + \phi) \\
\implies x &= x_1 + x_2 = 2A\cos(\frac{\omega_1 - \omega_2}{2}t)\cos(\frac{\omega_1 +\omega_2}{2}t+\phi)
\end{aligned}
$$
这里我们可以把振幅看作
$$
A(t) = 2A\cos(\frac{\omega_1 - \omega_2}{2}t)\
$$
振幅变化的频率为
$$
\nu_A = \frac{1}{2}\left|{\nu_1 - \nu_2}\right|
$$
由于振动的强弱和振幅的平方成正比，这里振动的强弱时间有关，这种现象为称为**拍现象**.  同时，我们也能推出振动强弱的变化频率
$$
\nu = 2\nu_A = \left|{\nu_1 - \nu_2}\right|
$$
我们把这个$\nu$称为**拍频**

## 简谐运动的动力学性质

### 位置和速度的关系
$$
A = \sqrt{x_0^2 + \frac{v_0^2}{\omega^2}}
$$
## 阻尼振动
阻力和速度成正比
$$
f = -\gamma \dot x
$$
运动方程
$$
m\ddot{x} = -kx - \gamma\dot x
$$
将其规范化
$$
\ddot{x} + 2\beta\dot x + \omega_0^2 x = 0 \tag{$\ast$}
$$
其中
1. **阻力**系数$\gamma$
2. **阻尼**系数$\beta = \dfrac{\gamma}{2m}$
3. **固有角频率**$\omega_0 = \sqrt{\dfrac{k}{m}}$
现在来讨论方程$(\ast)$的解，猜想
$$
x^* = e^{rt}
$$
带入方程，可以解得
$$
r_1 = -\beta + \sqrt{\beta^2 - \omega_0^2} ;\;r_2 =-\beta - \sqrt{\beta^2 - \omega_0^2}
$$
对于其特解，分三种情况讨论
#### 过阻尼$\beta > \omega_0$
有两个特解
$$
x_1^* = e^{r_1 t}\;,x_2^* = e^{r_2t}
$$
通解是以上两个解的线性组合
#### 临界阻尼$\beta = \omega_0$
这个时候$r_1 = r_2 = \beta$，只能得到一个特解
$$
x_1^* = e^{-\beta t}
$$
猜测另一个特解为
$$
x^*_2 = te^{-\beta t}
$$
通解是这两个解的线性组合
#### 低阻尼$\beta < \omega_0$
引入
$$
\omega = \sqrt{\omega_0^2 - \beta^2}
$$
那么有
$$
x_1^* = e^{(-\beta +\mathrm{i}\omega)t}; \;x_2^* = e^{(-\beta -\mathrm{i}\omega)t}
$$
可以引入两个新的独立特解
$$
x_1 = \frac{1}{2} (x_1^* + x_2^*); \; x_2 = \frac{1}{2}(x_1^* - x_2^*)
$$
取通解
$$
x = A_1x_1 - A_2 x_2 = e^{-\beta t} \sin (A_1\cos \omega t - A_2 \sin \omega t)

$$
$$
x = \sqrt{A_1^2+A_2^2} e^{-\beta t} (\frac{A_1}{\sqrt{A_1^2+A_2^2}}\cos \omega t - \frac{A_2}{\sqrt{A_1^2 + A_2^2}}\sin \omega t)
$$
令
$$
A = \sqrt{A_1^2+A_2^2},\; \cos \phi = \frac{A_1}{\sqrt{A_1^2+A_2^2}},\; \sin \phi = \frac{A_2}{\sqrt{A_1^2 + A_2^2}}
$$
则通解可以表示为
$$
x = Ae^{-\beta t} \cos(\omega t + \phi)
$$
## 受迫振动
驱动力
$$
F = F_0 \cos \omega t
$$
令
$$
\beta = \frac{\gamma}{2m}, \; \omega_0 = \sqrt{\frac{k}{m}}, \; f_0 = \frac{F_0}{m}
$$
可以得到稳态解
$$
x(t) = A\cos(\omega t + \phi)
$$
其中
$$
A = \frac{f_0}{\sqrt{(\omega_0^2 - \omega^2)+4\beta^2\omega^2}},\; \tan \phi = -\frac{2\beta \omega}{\omega_0^2 - \omega^2}
$$

# 波
## 波的表示
$$
\xi(x,t) = A\cos(\omega t - kx + \phi)
$$
其中$k = \dfrac{2\pi}{\lambda}$被称为波数
将其矢量化，则有
$$
\xi(x,\boldsymbol r) = A\cos(\omega t - \boldsymbol k \cdot \boldsymbol r+\phi)
$$
这里$\boldsymbol k$的方向和波的传播方向相同
## 波的干涉
### 驻波
取两列振幅相同的相干平面简谐波，假设分别沿$x$轴正、负方向传播，即有
$$
\xi_1 = A\cos(\omega t - kx +\phi),\; \xi_2 =A\cos(\omega t +kx+\phi)
$$
相干叠加后，就有
$$
\xi = \xi_1 + \xi_2 = 2A \cos(kx + \frac{\phi_2 - \phi_1}{2})\cos(\omega t + \frac{\phi_1 + \phi_2}{2})
$$
发现振幅和位置有关，且某些位置的振幅始终为零，称为**波节**；有些位置的振幅最大，称为**波腹**. 波节和波节、波腹和波腹之间的间距均为$\dfrac{\lambda}{2}$
## 波的反射
1. 端位自由，没有半波损
2. 端位固定，有半波损，即入射波和反射波的相位相差一个$\pi$
## Doppler 效应
$$
f' = \frac{u \pm v_\text{Observer}}{u \mp v_\text{Source}} f
$$
## 冲击波
当波源的运动速度$v$大于波的传播速度$u$时，会形成冲击波，此时波前会形成一个圆锥体
定义马赫数
$$
M = \frac{u}{v}
$$
则可以推得锥面半顶角为$\theta = \arcsin M = \arcsin \dfrac{v}{u}$
**注意这里的马赫数是小于一的**
## 波动方程
一维波$\xi = f(z, t)$满足下面的函数
$$
\boxed{\frac{\partial ^2 f}{\partial z^2} = \frac{1}{v^2} \frac{\partial^2 f}{\partial t^2}}
$$
### 弹性介质
定义**杨氏模量**
$$
E = \frac{F}{S}/\dfrac{\mathrm{d} {\xi}}{\mathrm{d} {x}}
$$
则在$E$均匀的介质中有**Hooke定律**
$$
F = k \Delta l, \; k = \frac{ES}{l_0}
$$
对于切向作用力，类似地定义**切变模量**
$$
G = \frac{T}{S} / \dfrac{\mathrm{d} {z}}{\mathrm{d} {x}}
$$
对于弹性介质中的横波和纵波，可以推导
$$
u_\parallel = \sqrt{\frac{E}{\rho}} \; \tag{纵波}
$$
$$
u_\perp = \sqrt{\frac{G}{\rho}} \; \tag{横波}
$$
### 弦上的横波
$$
u = \sqrt{\frac{T}{\lambda}}
$$
其中$T$为弦的张力，$\lambda$为弦的质量线密度

### 空气中的声波
$$
u = \sqrt{\frac{\gamma p_0}{\rho_0}}
$$
## 波的能量
记介质密度为$\rho$，振动方程为$\xi = A\cos \left(\omega(t - \dfrac{x}{u})\right)$，那么就有动能、势能的体密度
$$
\begin{aligned}
e_k &= \frac{1}{2} \rho (\frac{\partial \xi}{\partial t})^2 = \frac{1}{2}\rho \omega^2 A^2 \sin^2 \left(\omega(t - \frac{x}{u})\right) \\
e_p &= \frac{1}{2} k  (\xi(x + \mathrm{d} x, t) - \xi(x, t))^2 = \frac{1}{2}\frac{E\mathrm{d}S}{\mathrm{d}x} (\frac{\partial \xi}{\partial x} \mathrm{d}x)^2 \\
&= \frac{1}{2} E \frac{\omega^2}{u^2} A^2 \sin^2 \left(\omega(t - \frac{x}{u})\right) \\
&= \frac{1}{2}\rho \omega^2 A^2 \sin^2 \left(\omega(t - \frac{x}{u})\right)
\end{aligned}
$$
**Tip:** 上面的推导过程中用到了 $k = E\dfrac{\mathrm{d}S}{\mathrm{d}x}$ 和$u = \sqrt{\frac{E}{\rho}}$.
由此我们得到波的能量密度
$$
	\boxed{\varepsilon  = \varepsilon_k + \varepsilon_p = \rho \omega^2 A^2 \sin^2 \left(\omega(t - \frac{x}{u})\right)}
$$

