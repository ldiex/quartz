# 技巧
## 计算压强时选取$p$的单位为水柱或者汞柱，使得系数$\rho g = 1$
# 导论
[[Introduction to Thermodynamics]]
## 系统的分类
封闭系统 vs 绝热系统 vs 孤立系统
单元 vs 多元
均匀 vs 非均匀

宏观量是系统相应微观量的统计平均值

# 温度和平衡态
[[Temperature and Equilibrium State]]
## 平衡态
平衡态 vs 稳定态
> 平衡态是孤立体系，稳定态只是宏观状态不变（如夹在热源和冷源之间的金属棒，温度分布稳定但是有热流）

弛豫时间？
动态平衡
> 微观量一直在变，但是宏观统计量不变

三个平衡条件？
> 力 热 化学
## 热平衡
热平衡？
> 通过传热达成的平衡态

热力学第零定律？
经验温标？
> 经验上以某一种物质属性随温度的变化为依据并用经验公式进行分度的温标统称经验温标

温标三要素？
> 测温属性需随温度有单调的、连续的、显著的变化. 
> 固定点
> 对测温属性随温度的变化关系作出规定
### 理想气体温标 
固定点？水的三相点
局限性？
> 气压越低、气体越稀薄越准确；不能用于测量极低温和极高温

热力学温标？

国际实用温标？

# 物态方程
理想气体物态方程
Dalton 分压定律

> [!Tip] 响应函数
> 体膨胀系数
> $$
> \alpha = \frac{1}{V} \left(\dfrac{\partial {V}}{\partial {T}}\right)_p
> $$
> 压强系数
> $$
> \beta = \frac{1}{p} \left( \dfrac{\partial {p}}{\partial {T}} \right)_V
> $$
> 等温压缩系数
> $$
> \kappa_T = - \frac{1}{V}\left( \dfrac{\partial {V}}{\partial {p}} \right)_T
> $$
> 
# 分子动理论

> [!Note] 三相
> **固体**：较低温度下，分子的无规则运动不够剧烈，分子在相互作用力的影响下被束缚在各自的平衡位置附近做微小的振动，表现为固体状态. 
> 
> **液体**：温度升高，无规则运动剧烈到某一限度时，分子力的作用已不能把分子束缚在固定的平衡位置附近做微小的振动，但还不能使分子分散远离，表现为液体状态. 
> 
> **气体**：温度再升高，无规则运动进一步剧烈到一定限度时，不但分子的平衡位置没有了，而且分子之间也不能再维持一定的距离，这时分子互相分散远离，分子的运动近似为自由运动，表现为气体状态. 

Brown 运动 vs 分子热运动 
> 宏观 vs 微观

压强公式
$$
p = \dfrac{2}{3}n \bar \varepsilon; \; p = nk_BT
$$
方均根速率
$$
\sqrt{\bar{v^2}} = \sqrt{\dfrac{3k_BT}{m_0}}
$$
数量级为$10^3 \text{ m} / \mathrm{s}$

# Van der Waals 方程
分子势能
![[热学-Van Der Walls Force.png]]
分子有效直径$d$满足
$$
E_p\bigg\vert_{r = d} = E_{k0}
$$
Van der Waals 方程
$$
(p + \dfrac{a}{V_m^2}) (V_m - b) = RT
$$
左边的修正是对压强的修正，考虑了分子间吸引力
右边的修正是对体积的修正，考虑了气体分子间隙（分子间斥力）
$$
b = 4N_A V_0,\quad V_0 = \dfrac{4}{3} \pi \left(\dfrac{d}{2}\right)^2
$$
# Maxwell 速度分布律
讨论的是**在平衡态时**的速度分布
## 含义
$$
\mathrm{d} P(v_x, v_y,v_z) = \dfrac{\mathrm{d} N}{N(v_x, y_y, v_z)} = f(v_x,v_y,v_z) \mathrm{d} v_x \mathrm{d} v_y \mathrm{d} v_z
$$
即概率密度乘上自变量的小量后得到概率，对某一上下限积分就得到在该积分限内的概率
## 分布应该满足的条件
- 分布**各向同性**，只和速度大小有关
$$
f(v_x, v_y,v_z) = F(v_x^2+v_y^2+v_z^2) = F(v^2)
$$
- 三个方向上的速度分量**相互独立**
$$
f(v_x, v_y,v_z) = \phi(v_x)\phi(v_y)\phi(y_z) = g(v_x^2)g(v_y^2)g(v_z^2)
$$
- $v^2 \to 0 \implies F(v^2) \to 0$
- 再通过**归一化条件**和**能量条件**给出两个系数
## 速度分布律
$$
\boxed{f(v_x) =\left(\dfrac{m_0}{2k_B T}\right)^{1/2} \exp \left(- \dfrac{m_0}{2k_BT}v_x^2 \right)}
$$
或者
$$
\boxed{f(v_x,v_y,v_z) =\left(\dfrac{m_0}{2k_B T}\right)^{3/2} \exp \left[- \dfrac{m_0}{2k_BT}(v_x^2 + v_y^2 + v_z^2)\right]}
$$
## 速率分布律
$$
f_M(v) = 4\pi v^2 \left( \dfrac{m_0}{2\boxed{\pi} k_B T} \right)^{3/2} \exp \left(-\dfrac{m_0}{2k_BT}v^2\right)
$$
## 特殊值
### 最概然速率
$$
v_p = \sqrt{\dfrac{2k_BT}{m_0}}
$$
### 平均速率
$$
\bar v = \sqrt{\dfrac{8k_BT}{\pi m_0}}
$$
### 方均根速率
$$
\sqrt{\overline {v^2}} = \sqrt{\dfrac{3k_BT}{ m_0}}
$$
## 某个关于速度的物理量
#### 的平均值
$$
\overline{g(v)} = \dfrac{\int_{v_1}^{v_2} g(v) f(v) \mathrm{d} v}{\int_{v_1}^{v_2}f(v) \mathrm{d} v}
$$
#### 的分布
令$g(v) \implies v = g^{-1}$
$$
f(g) \mathrm{d} g = \dfrac{\mathrm{d} N(g)}{N} = f_M(v) \mathrm{d} v = f(g^{-1})\mathrm{d}(g^{-1})
$$
## 分子碰壁数
$$
\Gamma = n\int_0^\infty v_xf_M(v_x) \mathrm{d} v_x = n \sqrt{\dfrac{k_B T}{2\pi m_0}} = \dfrac{1}{4}n\bar v
$$
## 泻流
### 热分子压强差现象
一**小孔**连接两个装有同种气体的容器，保持两边温度分别为$T_1$和$T_2$
- 达到稳定前，气体分子从一个容器喷射向另一个容器形成的流动称为*泻流 (effusion)*
- 达到稳定后，两容器中的气体压强不相等，该现象称为*热分子压强差现象*

**达到稳定时，两边的分子碰壁数应相等**，因此有
$$
\Gamma_1 = \Gamma_2 \implies\dfrac{p_1}{p_2} = \left(\dfrac{T_1}{T_2}\right)^{1/2}
$$
### 泻流分离
容器中装有温度为$T$的混合气体，它由质量分别为$m_1$和$m_2$的两种组元组成，则泻流分子束中两种组元的分子数目比
$$
\dfrac{I_1}{I_2} = \dfrac{n_1\bar v_1}{n_2 \bar v_2} = \dfrac{n_1}{n_2} \sqrt{\dfrac{m_2}{m_1}}
$$
通过多次连续泻流，可以提纯质量较轻的组元
$$
{\left(\dfrac{n_1}{n_2}\right)}_N = \dfrac{n_{10}}{n_{20}} {\left(\dfrac{m_2}{m_1}\right)}^{N/2}
$$

# Boltzmann 分布
## Boltzmann 密度分布
把重力场中的密度函数推广到任意外场
$$
f_B(\boldsymbol r) = \dfrac{n_0}{N}e^{-\varepsilon_p(\boldsymbol r)/k_BT}
$$
前面的系数可以由归一化条件给出
## Boltzmann 分布律
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

# 能量均分定理
## 振动自由度
$n$个原子构成的气体分子中的每一个原子质点都有$3$个总自由度，故振动有$s = (3n - t - r)$个自由度
## 理想气体热容
定体摩尔热容
$$
C_{V,m} = \dfrac{1}{2}(t + r + 2s)R
$$
对于非刚性的单原子和双原子理想气体，其定体摩尔热容分别为$\dfrac{3}{2}R$和$\dfrac{7}{2}R$
然而，在常温下，双原子气体的振动自由度未被激活，所以一般取其$C_{V,m} = \dfrac{5}{2}R$
且有
$$
C_{p, m} = C_{V, m} + R
$$

# 平均自由程
## 有效碰撞截面
**由碰撞的双方共同决定**
- 同种分子碰撞截面: $\sigma = \pi d^2$，其中$d$为分子**直径**
- 不同种分子的碰撞截面: $\sigma = \pi \left(\dfrac{d_1 + d_2}{2}\right)^2$
## 平均自由程
## 定义
- 碰撞频率$Z$: 一个分子在单位时间内与其他分子发生碰撞的次数
- 自由程$\lambda$: 一个分子在连续两次和其他分子发生碰撞之间经过的路程
引入*平均自由飞行时间*$\bar \tau = 1 / \bar Z$, 于是有
$$
\bar \lambda = \bar v \cdot \bar \tau = \bar v / \bar Z
$$
## 相对速率
*平均相对速率*  $\bar u = \sqrt{2} \bar v$

### 推导
在$\Delta t$时间内，入射分子发生碰撞的数目为
$$
n \Delta V = n \sigma \bar u \Delta t = \bar Z \Delta t
$$
平均碰撞频率
$$
\bar Z = n \sigma \bar u = \sqrt{2} n \sigma \bar v
$$
于是有平均自由程
$$
\bar \lambda = \bar v / \bar Z = \boxed{\dfrac{1}{\sqrt{2}\sigma n}}
$$
又由理想气体状态方程，有
$$
\bar \lambda = \dfrac{\bar v}{\bar Z} = \dfrac{1}{\sqrt{2} \pi n d^2} = \dfrac{k_B T}{\sqrt{2}\pi pd^2}
$$
### 混合气体的平均自由程
|           | A 类分子                                                     | B 类分子                                                     |
| --------- | --------------------------------------------------------- | --------------------------------------------------------- |
| 与A碰撞的平均频率 | $\bar Z_{AA} = n_A \pi d_A^2 \bar u_{AA}$                 | $\bar Z_{BA} = n_A \pi d_{AB}^2 \bar u_{AB}$              |
| 与B碰撞的平均频率 | $\bar Z_{BA} = n_B \pi d_{AB}^2 \bar u_{AB}$              | $\bar Z_{BB} = n_B \pi d_B^2 \bar u_{BB}$                 |
| 平均自由程     | $\bar \lambda_A = \bar v_A / (\bar Z_{AA} + \bar Z_{AB})$ | $\bar \lambda_B = \bar v_B / (\bar Z_{BA} + \bar Z_{BB})$ |
则混合气体的平均自由程则是这两种分子的算术平均值
$$
\bar \lambda = \dfrac{n_A \bar \lambda_A + n_B \bar \lambda_B}{n_A + n_B}
$$

## 气体按自由程的分布
- 设想在某一个时刻的一组分子有$N$个
- 在后面的运动过程中，任一分子和其他分子发生碰撞，则将其剔除出去，该组分子就减少一个
- 设这组分子通过路径$\lambda$后还剩下$N(\lambda)$个，而在下一段路程$\mathrm{d} \lambda$中，分子数又改变了$\mathrm{d} N (\lambda)$
- $N(\lambda)$即为通过路程$\lambda$后还未发生碰撞的粒子数目，即自由程大于$\lambda$的分子数目
- 在路程$\lambda \sim \lambda + \mathrm{d} \lambda$ 之间, 由于平均而言每个分子走过$\bar \lambda$距离会发生一次碰撞，所以在这段路程中每个分子发生碰撞的概率为$\dfrac{\mathrm{d} \lambda}{\bar \lambda}$
由此可以推出
$$
-\mathrm{d} N(\lambda)= N(\lambda) \dfrac{\mathrm{d} \lambda}{\bar \lambda} \implies N(\lambda) = Ce^{-\lambda / \bar \lambda} = Ne^{-\lambda / \bar \lambda}
$$

于是
$$
-\dfrac{\mathrm{d} N(\lambda)}{N} = \dfrac{1}{\bar \lambda}e^{-\lambda/\bar \lambda} \mathrm{d} \lambda = f(\lambda)\mathrm{d} \lambda \implies \boxed{f(\lambda) = \dfrac{1}{\bar \lambda}e^{-\lambda/\bar \lambda}}
$$


# 输运过程
## 分类
### 热传导
系统各区域温度不均匀而使**能量（热量）** 从高温区域传递到低温区域的现象，每一个分子传递的是动能（$c_VmT$, $c_V = \dfrac{C_V}{m}$）
### 扩散
系统各区域浓度不均匀而使**质量（粒子）** 从浓度高的区域传递到低浓度区域的现象，每一个分子传递的是质量
#### 压强扩散
扩散过程中系统的压强分布不均匀
密度不均匀$\to$数密度不均匀$\to$压强不均匀$\to$宏观气流

如一种气体在真空中的扩散
#### 纯扩散
扩散过程中系统的压强、温度分布均匀且恒定， 无宏观气流
扩散是由于分子热运动导致的

如种理想气体在某定容容器中之间的隔板被移除后的扩散

### 黏性
系统各区域粒子定向速度不均匀而使**动量**从动量高的区域传递到低动量区域的现象，每一个分子传递的是定向移动的动量（$m \boldsymbol u$, 其中$\boldsymbol u$是定向移动速度）

## Newton 定律
$$
F(z) = - \eta \left(\dfrac{\mathrm{d} {u}}{\mathrm{d} {z}}\right) \mathrm{d} S
$$
## Fourier 定律
$$
\dfrac{\mathrm{d} {Q}}{\mathrm{d} {t}} = - \kappa \left(\dfrac{\mathrm{d} {T}}{\mathrm{d} {z}}\right)_{z_0} \mathrm{d} S
$$
## Fick 定律
$$
\dfrac{\mathrm{d}}{\mathrm{d} { N_{\alpha}} }{t} = -D_{\alpha\beta} \left(\dfrac{\mathrm{d} {n_\alpha}}{\mathrm{d} {z}}\right) \mathrm{d} S
$$
> [!Tip]
> 从一侧移向另一侧的分子数$=$碰壁数$+$扩散效应（Fick 定律给出的一半）
> $$
> \mathrm{d} N = \left(\dfrac{1}{6} n \bar v + \dfrac{1}{6} \bar \lambda \dfrac{\mathrm{d} {n}}{\mathrm{d} {z}}\right) \mathrm{d} S
> $$
>注意在输运过程中课本采用$\Gamma = n \bar v /6$


> [!Note] 系数取值
> $$
> \begin{gather}
> \eta = \dfrac{1}{3}\rho \bar v \lambda \\
> \kappa = \dfrac{1}{3}\rho \bar v \lambda c_V, \quad c_V = C_V / m \\
> D = \dfrac{1}{3} \bar v \lambda
> \end{gather}
> $$

![[热学-期中复习提纲.jpg]]