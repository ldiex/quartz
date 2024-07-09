## 波动方程
一维波$\xi = f(z, t)$满足下面的函数
$$
\boxed{\frac{\partial ^2 f}{\partial z^2} = \frac{1}{v^2} \frac{\partial^2 f}{\partial t^2}}
$$
在真空中，有
$$
\nabla^2 \boldsymbol E = \mu_0\varepsilon_0 \frac{\partial^2 \boldsymbol E}{\partial t^2}; \; \nabla^2 \boldsymbol B = \mu_0\varepsilon_0 \frac{\partial^2 \boldsymbol B}{\partial t^2}
$$
便有光速$c = \dfrac{1}{\sqrt{\mu_0\varepsilon_0}}$
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
## 真空单色平面电磁波
假设波在$z$方向传播，直接解电磁场的波动方程，有
$$
\tilde {\boldsymbol E}(z, t) = \tilde {\boldsymbol E}_0 \exp(\mathrm{i} (kz - \omega t));\; \tilde {\boldsymbol B}(z, t) = \tilde {\boldsymbol B}_0 \exp(\mathrm{i} (kz - \omega t));
$$
这里$\tilde {\boldsymbol E}$和$\tilde {\boldsymbol B}$是复振幅，物理中实际的场是其实部
因为$\boldsymbol{E}$在$z$轴上传播，和$x,y$无关，故由电场的高斯定理
$$
	\nabla \cdot \boldsymbol E = \frac{\partial E_x}{\partial x} + \frac{\partial E_y}{\partial y} + \frac{\partial E_z}{\partial z} = 0 \implies \frac{\partial E_z}{\partial z} = 0 
$$
这表明$E_z$是一个常数，但是我们期望着场的所有分量都会随着距离衰减，所以令$E_z = 0$; 同理由磁场的高斯定理也可以得到$B_z = 0$
所以电磁波是一个横波，电场和磁场的波动方向垂直于波的传播方向
再根据法拉第定律$\nabla \times \boldsymbol E = - \dfrac{\partial \boldsymbol B}{\partial t}$，这意味着电磁场的振幅直接存在关系
$$
-k(\tilde{E}_0)_y = \omega (\tilde {B}_0)_x, \; k(\tilde{E}_0)_x = \omega (\tilde {B}_0)_y
$$
或者写成
$$
\tilde {\boldsymbol B}_0 = \frac{k}{\omega} (\hat{\boldsymbol z} \times \tilde {\boldsymbol E}_0)
$$
所以，电场和磁场同相位且相互垂直，它们的实部（振幅）有如下关系
$$
\boxed{B_0 = \frac{k}{\omega} E_0 = \frac{1}{c}E_0}
$$
## 电磁波的能量
电磁场单位体积内储存的能量为
$$
u = \frac{1}{2} (\varepsilon_0 E^2 + \frac{1}{\mu_0}B^2)
$$
 则对于单色平面波有
 $$
		u = \frac{1}{2}(\varepsilon_0E^2 + \frac{1}{\mu_0}\frac{E^2}{c^2}) = \varepsilon_0 E^2
 $$
 那么其能流密度（波的能流密度$:=$波的能量密度 $\times$ 波速）
$$
	s = uc = \varepsilon_0 cE^2 = \varepsilon_0 c^2 EB = \frac{1}{\mu_0}EB
$$
在一般情况下，上面的$s$用 **坡印廷矢量$\boldsymbol S$** 表示: 
$$
	\boldsymbol S = \frac{1}{\mu_0} (\boldsymbol E \times \boldsymbol B)
$$
### 物质中的电磁波
类似地，可以推得
$$
u = \frac{1}{2} (\varepsilon E^2 + \frac{1}{\mu}B^2)
$$
和
$$
	\boldsymbol S = \frac{1}{\mu} (\boldsymbol E \times \boldsymbol B)
$$
