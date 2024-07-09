# 外场中粒子数密度的分布
## 重力场中微粒按高度的分布
设大气层是等温的，且其中的重力加速度$g$不变.  气体在重力场作用下达到平衡态（无容器）

平衡后大气维持在地球周围，大气的每一个宏观物理量随高度$z$都有一个确定的、稳定的分布$n(z), p(z)$

由力学平衡条件$\mathrm{d} p = -nm_0g \mathrm{d} z$和理想气体状态方程$p = nk_B T$可知
$$
\dfrac{\mathrm{d} p}{p} = -\dfrac{m_0 g}{k_B T}\mathrm{d} z \implies p(z) = p_0\exp(-m_0gz/k_BT)
$$
故也有
$$
n(z) = n_0\exp(-m_0 gz / k_B T)
$$
由此计算底面积$\mathrm{d} S$柱体（高度无限延伸）中的粒子数为
$$
N = n_0 \dfrac{k_B T}{m_0 g} \mathrm{d} S
$$
重力场中微粒随高度的等温分布律为
$$
f(z) = \dfrac{\mathrm{d} N(z)}{N \mathrm{d} z} = \dfrac{m_0 g}{k_B T} \exp\left(-\dfrac{m_0gz}{k_BT}\right) = \dfrac{m_0g}{k_BT}\exp\left[-\dfrac{\varepsilon_p(z)}{k_BT}\right]
$$
## 离心力场中微粒按径向的分布
$$
\varepsilon_p(r) = -\dfrac{1}{2}m_0\omega^2r^2
$$
$$
\begin{aligned}
n(r) = n_0e^{-\varepsilon_p(r)/k_BT} = n_0e^{m_0\omega^2r^2/2k_BT} \\
p(r) = p_0e^{-\varepsilon_p(r)/k_BT} = p_0e^{m_0\omega^2r^2/2k_BT}
\end{aligned}
$$
随着与转动轴距离的增加，粒子数密度和压强都平方指数增加.  故台风、飓风的沿破坏力极大，而其中心却没什么破坏力. 

# Boltzmann 密度分布
把重力场中的密度函数推广到任意外场
$$
f_B(\boldsymbol r) = \dfrac{n_0}{N}e^{-\varepsilon_p(\boldsymbol r)/k_BT}
$$
# Boltzmann 分布律
微观粒子按速度$\boldsymbol v$的分布
$$
f(\boldsymbol v) =\left(\dfrac{m_0}{2k_B T}\right)^{3/2} \exp \left[- \dfrac{m_0v^2}{2k_BT}\right] = \left(\dfrac{m_0}{2k_B T}\right)^{3/2} \exp \left[- \dfrac{\varepsilon_k(\boldsymbol v)}{k_BT}\right]
$$
按照位置$\boldsymbol r$的分布
$$
f_B (\boldsymbol r) = \dfrac{n_0}{N} \exp\left[-\dfrac{\varepsilon_p(\boldsymbol r)}{k_BT}\right]
$$
二者相乘即为*Boltzmann分布律*
$$
f_{MB} (\boldsymbol v, \boldsymbol r) = \dfrac{n}{N} \left(\dfrac{m_0}{2\pi k_BT}\right)^{3/2} \exp \left[-\dfrac{\varepsilon_p(\boldsymbol r) + \varepsilon_k(\boldsymbol v)}{k_BT}\right]
$$
由此可以得到
$$
\dfrac{\mathrm{d} N(\boldsymbol v, \boldsymbol r)}{N} = f_{MB}(\boldsymbol v, \boldsymbol r) {\mathrm{d}}^3 \boldsymbol v {\mathrm{d}}^3 \boldsymbol r
$$

