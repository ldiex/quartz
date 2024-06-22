# 概率论基础
## 概率
### 随机量
### 事件
### 概率
#### 概率测量
$$
P(X_i) = \lim_{N \to \infty} N(X_i) / N
$$
#### 归一化 (Normalization)
$$
\sum_i P(X_i) = 1
$$
在构造概率函数的时候在前面加上一个系数以满足归一化条件
## 统计规律
### 概率分布 (Probability Distribution)
*概率累计函数*
$$
F_X(x) = P(X \le x),\; x \in \mathbb R
$$
和*概率密度函数*
$$
P[a \le X \le b] = \int_a^b f_X(x) \mathrm{d} x
$$
反过来
$$
f_X(x) = \dfrac{\mathrm{d}}{\mathrm{d} {x}}F_X(x)
$$
### 期望值
$$
E[X] = \int_\Omega X \mathrm{d} P
$$
## 涨落
在任一给定的瞬间或在宏观系统中任一给定的局部范围内，所测到的宏观量的实际数值一般都与其统计平均值有所偏差，这种现象称为*涨落*
### 均方根涨落
又称为*标准差*
$$
\sigma = \sqrt{\overline{({\Delta X}^2)}} = \sqrt{\overline{(X - \overline X)^2}} = \sqrt{\overline{X^2} - \overline{X}^2}
$$

即方差为平方的期望减去期望的平方
### 相对涨落
$$
\delta = \sigma / {\overline X}
$$
是一个无量纲数
## 大数法则
- 采样越多，随机量的平均值越接近其期望值
- 采样越多，事件发生的比例越接近其概率分布

## 连续随机变量
对于概率密度函数$f(x)$
- 归一化条件
$$
\int f(x)\mathrm{d} x = 1
$$
- 统计平均值
$$
\bar x = \int xf(x) \mathrm{d} x
$$
- 均方根涨落
$$
\sigma = \sqrt{\overline{(x - \overline x)^2}} = \sqrt{\int f(x)(x - \bar x)^2 \mathrm{d} x}
$$
- 如果某一个物理量$g(x)$是$x$的函数，则其预期平均值
$$
\overline{g(x)} = \int f(x)g(x) \mathrm{d} x
$$
# Maxwell 分布律
## 速度空间
任何一个粒子的速度都可以用以$v_x,v_y,v_z$为轴构成的速度空间里的一个点表示
## 速度分布函数
$$
\mathrm{d} P(v_x, v_y,v_z) = f(v_x,v_y,v_z) \mathrm{d} v_x \mathrm{d} v_y \mathrm{d} v_z
$$
其中$f(v_x,v_y,v_z)$是速度分布的概率密度函数，它需要满足归一化条件
$$
\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(v_x,v_y,v_z) \mathrm{d} v_x \mathrm{d} v_y \mathrm{d} v_z = 1
$$
## 分布应该满足的条件
- 分布各向同性，只和速度大小有关
$$
f(v_x, v_y,v_z) = F(v_x^2+v_y^2+v_z^2) = F(v^2)
$$
- 三个方向上的速度分量相互独立
$$
f(v_x, v_y,v_z) = \phi(v_x)\phi(v_y)\phi(y_z) = g(v_x^2)g(v_y^2)g(v_z^2)
$$
- $v^2 \to 0 \implies F(v^2) \to 0$
## 速度分布律推导
$$
\begin{aligned}
F(v^2) &= g(v_x^2)g(v_y^2)g(v_z^2) \\
\implies \ln F(v^2) &= \ln g(v_x^2) + \ln g(v_y^2) + \ln g(v_z^2) \\
\end{aligned}
$$
于是
$$
\begin{aligned}
&\dfrac{\partial {\ln F(v^2)}}{\partial {v_x^2}} = \dfrac{\partial {\ln g(v_x^2)}}{\partial {v_x^2}},\; \dfrac{\partial {\ln F(v^2)}}{\partial {v_x^2}} = \dfrac{\partial {\ln F(v^2)}}{\partial {v^2}} \dfrac{\partial {v^2}}{\partial {v_x^2}} = \dfrac{\partial {\ln F(v^2)}}{\partial {v^2}} \\
&\implies \dfrac{\partial {\ln F(v^2)}}{\partial {v^2}} = \dfrac{\partial {\ln g(v_x^2)}}{\partial {v_x^2}} \\
&\implies \boxed{\dfrac{\partial {\ln F(v^2)}}{\partial {v^2}} = \dfrac{\partial {\ln g(v_x^2)}}{\partial {v_x^2}} =\dfrac{\partial {\ln g(v_y^2)}}{\partial {v_y^2}} =\dfrac{\partial {\ln g(v_z^2)}}{\partial {v_z^2}}}
\end{aligned}
$$
上式中的四个部分分别是不同变量的函数，为保证等式成立，它们必需是同一个常数. 又随$v^2$增大，$F(v^2)$应当减小，所以该常数为负数
$$
\dfrac{\partial {\ln F(v^2)}}{\partial {v^2}} = \dfrac{\partial {\ln g(v_x^2)}}{\partial {v_x^2}} =\dfrac{\partial {\ln g(v_y^2)}}{\partial {v_y^2}} =\dfrac{\partial {\ln g(v_z^2)}}{\partial {v_z^2}} = -\dfrac{1}{2\sigma^2} < 0
$$
从而
$$
g(v_x^2) =C\exp \left(-\dfrac{v_x^2}{2\sigma^2}\right), \; g(v_y^2) =C\exp \left(-\dfrac{v_y^2}{2\sigma^2}\right), \; g(v_z^2) =C\exp \left(-\dfrac{v_z^2}{2\sigma^2}\right)
$$
$$
f(v_x,v_y,v_z) =C^3 \exp \left[- \dfrac{v_x^2 + v_y^2 + v_z^2}{2\sigma^2}\right]
$$
由归一化条件知$C = \dfrac{1}{\sqrt{2\pi}\sigma}$ (因为$\displaystyle \int_{-\infty}^{\infty} e^{x^2} \mathrm{d}  x = \sqrt{\pi}$)

故
$$
f(v_x,v_y,v_z) =\left(\dfrac{1}{2\pi\sigma^2}\right)^{3/2} \exp \left[- \dfrac{v_x^2 + v_y^2 + v_z^2}{2\sigma^2}\right]
$$
这是一个*Gauss 函数*，也是*正态分布*，其中$\sigma$是标准差

## Maxwell 速度分布函数
由气体分子的平均动能$\bar \varepsilon = \dfrac{3}{2}k_BT$和$\bar\varepsilon = \dfrac{1}{2}m_0(v_x^2 + v_y^2 + v_z^2) = \dfrac{3}{2}m_0\sigma^2$
得到
$$
\boxed{f(v_x,v_y,v_z) =\left(\dfrac{m_0}{2k_B T}\right)^{3/2} \exp \left[- \dfrac{m_0}{2k_BT}(v_x^2 + v_y^2 + v_z^2)\right]}
$$
由
$$
f(v_x,v_y,v_z) = f(v_x)f(v_y)f(v_z)
$$
知
$$
\boxed{f(v_x) =\left(\dfrac{m_0}{2k_B T}\right)^{1/2} \exp \left(- \dfrac{m_0}{2k_BT}v_x^2 \right)}
$$
## Maxwell 速率分布律
速度分布在$v \sim v + \mathrm{d} v$的球壳中的分子数占总分子数的比率
$$
\dfrac{\mathrm{d} N(v)}{N} = f_M(v) \mathrm{d} v = \boxed{\left(\dfrac{m_0}{2k_B T}\right)^{3/2} \exp \left(- \dfrac{m_0}{2k_BT}v^2\right)} \color{red}{4\pi v^2 \mathrm{d} v}
$$

其中框选的部分表示球壳中任意一点的概率密度，而红色部分则是速度空间中球壳的体积，于是有
$$
f_M(v) = 4\pi v^2 \left( \dfrac{m_0}{2\pi k_B T} \right)^{3/2} \exp \left(-\dfrac{m_0}{2k_BT}v^2\right)
$$

## 最概然速率
速率分布函数$f_M(v)$的极大值相对应的速率$v_p$，称为*最概然速率*
$$
\dfrac{\mathrm{d}}{\mathrm{d} {v}}f_m(v) = 0 \implies \boxed{v_p = \sqrt{\dfrac{2k_BT}{m_0}} = \sqrt{\dfrac{2RT}{M}}}
$$
注意，速率函数分布的峰值和最概然速率负相关，也就是和温度负相关
$$
f_M(v_p) = \dfrac{4}{e}\sqrt{\dfrac{m_0}{2\pi k_B T}} = \dfrac{4}{e\sqrt{\pi}v_p}
$$
可以推出
- 温度$T$升高时，最概然速率$v_p$增大
- 曲线的峰值右移，且峰值降低，但曲线下总面积为$1$不变
- 温度升高时，气体中速率较小的分子数目减少，而速率较大的分子数增多

## 平均速率、方均根速率
高斯积分的计算见[[Gaussian Integral]]
$$
\bar v = \dfrac{\int_0^N v\mathrm{d} N}{N} = \dfrac{\int_0^\infty v N f_M(v) \mathrm{d} v}{N} = \int_0^\infty v f_M(v) \mathrm{d} v
$$
有
$$
\boxed{\bar v = \sqrt{\dfrac{8k_BT}{\pi m_0}}=\sqrt{\dfrac{8RT}{\pi M}}}
$$
$$
\bar v^2 = \dfrac{\int_0^N v^2\mathrm{d} N}{N} = \dfrac{\int_0^\infty v^2 N f_M(v) \mathrm{d} v}{N} = \int_0^\infty v^2 f_M(v) \mathrm{d} v
$$
有
$$
\boxed{\sqrt{\overline {v^2}} = \sqrt{\dfrac{3k_BT}{ m_0}}=\sqrt{\dfrac{3RT}{M}}}
$$
比较有
$$
\text{最概然速率} < \text{平均速率} < \text{方均根速率}
$$

不同的应用场景
- 在讨论速率分布时，利用最概然速率
- 在计算分子运动的平均距离时，利用平均速度
- 在计算分子的平均平动动能时，利用方均根速率
# Maxwell 分布律的应用
## 分子碰壁数
气体分子的碰壁数$\Gamma$是单位时间呢碰撞到单位面积器壁上的气体分子数
$$
\mathrm{d} N = n\mathrm{d} V \times f_M(v_x)\mathrm{d} v_x = n v_x\mathrm{d} S \mathrm{d} t \times f_M(v_x) \mathrm{d} v_x  
$$
于是可计算$\Gamma = \int \frac{\mathrm{d} N}{\mathrm{d} S \mathrm{d} T}$
$$
\Gamma = n\int_0^\infty v_xf_M(v_x) \mathrm{d} v_x = n \sqrt{\dfrac{k_B T}{2\pi m_0}} = \dfrac{1}{4}n\bar v
$$
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

## 星球大气成分和稳定性
### 误差函数
已知
$$
f_M(v) = 4\pi v^2 \left( \dfrac{m_0}{2\pi k_B T} \right)^{3/2} \exp \left(-\dfrac{m_0}{2k_BT}v^2\right)
$$
和
$$
v_p = \sqrt{\dfrac{2k_BT}{m_0}} = \sqrt{\dfrac{2RT}{M}}
$$
由此引入*无量纲速率*$u = v / v_p$
$$
f_M(v)\mathrm{d} v = f_M(u)\mathrm{d} u \implies f_M(u) = \dfrac{4}{\sqrt{\pi}}u^2 e^{-u^2}
$$
无量纲速率$u$大于某一个速率$u'$的气体分子比率
$$
\begin{aligned}
\dfrac{\Delta N(u > u')}{N} &= \int_{u'}^\infty f_M(u)\mathrm{d} u = 1- \dfrac{4}{\sqrt{\pi}} \int_0^{u'}u^2 e^{-u^2} \mathrm{d} u \\
&= 1 + \dfrac{2}{\sqrt{\pi}}\int_0^{u'} u\mathrm{d} e^{-u^2} = 1 + \dfrac{2}{\sqrt{\pi}} u'e^{-u'^2} - \mathrm{erf}(u')
\end{aligned}
$$
由此定义*误差函数*
$$
\mathrm{erf}(x) = \dfrac{2}{\sqrt{\pi}} \int_0^x e^{-u^2} \mathrm{d} u
$$
### 星球的逃逸速度（宇宙第二速度）
$$
v_{es} = \sqrt{2gR_s},\; g = GM_s /R_s^2
$$
大气的无量纲逃逸速率
$$
u' = \dfrac{v_{es}}{v_p} = \sqrt{\dfrac{GM_sm}{R_sk_B T}}
$$
假设每秒钟逃逸出的气体分子占总分子数的比例为$\Delta N(u > u')/N$，则经过它的倒数秒之后，则该气体组分将从大气中消失

| $u'$               | $1$       | $2$     | $6$        | $28$                    |
| ------------------ | --------- | ------- | ---------- | ----------------------- |
| $\Delta N(u>u')/N$ | $57.24\%$ | $4.6\%$ | $10^{-15}$ | $10^{-340}$             |
| $\tau$             | $2$秒     | $22$秒  | $0.32$亿年 | $3.2\times10^{324}$亿年 |

# Maxwell 分布律的实验验证
