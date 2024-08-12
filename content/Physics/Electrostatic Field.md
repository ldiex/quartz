## 电偶极子
电势
$$
	\phi(\boldsymbol r) = \frac{1}{4 \pi \varepsilon_0} \frac{\boldsymbol p \cdot \boldsymbol r}{r^3} = \frac{1}{4 \pi \varepsilon_0} \frac{p\cos\theta}{r^2}
$$
在球坐标系中的电场
$$
\begin{aligned}
E_r &= - \dfrac{\partial {\phi}}{\partial {r}} = \frac{1}{4\pi\varepsilon_0} \frac{2p\cos \theta}{r^3} \\
E_\theta &= -\frac{1}{r} \dfrac{\partial {\phi}}{\partial {\theta}} = \frac{1}{4\pi \varepsilon_0} \frac{p \sin \theta}{r^3} \\
E_\varphi &= - \frac{1}{r\sin \theta} \dfrac{\partial {\phi}}{\partial {\varphi}} = 0
\end{aligned}
$$
能量
$$
	E_p = -\boldsymbol p \cdot\boldsymbol E
$$
受力矩
$$
\boldsymbol M = -\dfrac{\partial {E_p}}{\partial {\theta}} \hat{\boldsymbol \theta}= -\boldsymbol p \times \boldsymbol E
$$
受梯度力
$$
\boldsymbol F = -\nabla E_p = \nabla (\boldsymbol p \cdot \boldsymbol E)
$$
## 静电能

### 离散体系

$$
W_e = \frac{1}{2} \sum_i q_i \varphi_i
$$
### 连续体系
$$
W_e = \frac{1}{2} \int_V \rho_e \varphi \mathrm{d} V
$$
或者
$$
W_e = \int_V w_e \mathrm{d} V = \frac{\varepsilon_r \varepsilon_0}{2} \int_V E^2 \mathrm{d} V
$$

