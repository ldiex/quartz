# 平均自由程
## 有效碰撞截面
### 弹性钢球分子
- 瞄准距离$b$: 入射方向和靶子分子之间的垂直具体
- 同种分子碰撞截面: $\sigma = \pi d^2$, 其中$d$为分子**直径**
- 不同种分子的碰撞截面: $\sigma = \pi \left(\dfrac{d_1 + d_2}{2}\right)^2$
### 实际气体分子
- 有效分子直径: 偏折角度等于$0$的最小瞄准距离$b_0 = d$称为分子的*有效直径*
- 有效碰撞截面: $\sigma = \pi d^2$

#### 影响有效分子直径(有效碰撞截面)的因素
- 入射分子的初始动量越大, 有效分子直径越小
- 而分子的平均动能和气体温度成正比
- 但是实验表明, 气体分子的有效碰撞截面随温度改变产生的变化较小
- **故对任一确定气体, 可将分子的有效直径近似为一个常数**

## 平均自由程
### 碰撞频率和自由程
- 碰撞频率$Z$: 一个分子在单位时间内与其他分子发生碰撞的次数
- 自由程$\lambda$: 一个分子在连续两次和其他分子发生碰撞之间经过的路程
引入*平均自由飞行时间*$\bar \tau = 1 / \bar Z$, 于是有
$$
\bar \lambda = \bar v \cdot \bar \tau = \bar v / \bar Z
$$
### 运动坐标系中的两体碰撞

可以将两个分子发生碰撞这个两体问题转化为一个分子（如分子$2$）参考系中的单体问题, 此时有折合质量
$$
\mu = \dfrac{m_1m_2}{m_1 + m_2}
$$
和相对速度$\boldsymbol{u} = \boldsymbol v_1 - \boldsymbol v_2$

在处于平衡态的单元系中, 有$m_1 = m_2 = m$且$\boldsymbol v_1, \boldsymbol v_2$满足[[Maxwell Distribution of Speed | Maxwell速度分布律]] , 于是
- 折合质量$\mu = m / 2$
- 相对速度$\boldsymbol u$也遵循Maxwell速度分布
- 由此可以推导出*平均相对速率*  $\bar u = \sqrt{2} \bar v$

### 平均碰撞频率和平均自由程
由上一节, 我们得到一个等价的碰撞模型: 一个质量为$\mu$的分子以平均的相对速率$\bar u$在有静止分子组成的气体中运动, 并与之发生碰撞

在$\Delta t$时间内, 入射分子发生碰撞的数目为
$$
n \Delta V = n \sigma \bar u \Delta t = \bar Z \Delta t
$$
平均碰撞频率
$$
\bar Z = n \sigma \bar u = \sqrt{2} n \sigma \bar v
$$
于是有平均自由程
$$
\bar \lambda = \bar v / \bar Z = \dfrac{1}{\sqrt{2}\sigma n}
$$
又由理想气体状态方程, 有
$$
\boxed{\bar \lambda = \dfrac{\bar v}{\bar Z} = \dfrac{1}{\sqrt{2} \pi n d^2} = \dfrac{k_B T}{\sqrt{2}\pi pd^2}}
$$
## 混合气体的平均自由程
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
- 在后面的运动过程中, 任一分子和其他分子发生碰撞, 则将其剔除出去, 该组分子就减少一个
- 设这组分子通过路径$\lambda$后还剩下$N(\lambda)$个, 而在下一段路程$\mathrm{d} \lambda$中, 分子数又改变了$\mathrm{d} N (\lambda)$
- $N(\lambda)$即为通过路程$\lambda$后还未发生碰撞的粒子数目, 即自由程大于$\lambda$的分子数目
- 在路程$\lambda \sim \lambda + \mathrm{d} \lambda$ 之间, 由于平均而言每个分子走过$\bar \lambda$距离会发生一次碰撞, 所以在这段路程中每个分子发生碰撞的概率为$\dfrac{\mathrm{d} \lambda}{\bar \lambda}$
由此可以推出
$$
-\mathrm{d} N(\lambda)= N(\lambda) \dfrac{\mathrm{d} \lambda}{\bar \lambda} \implies N(\lambda) = Ce^{-\lambda / \bar \lambda} = Ne^{-\lambda / \bar \lambda}
$$

于是
$$
-\dfrac{\mathrm{d} N(\lambda)}{N} = \dfrac{1}{\bar \lambda}e^{-\lambda/\bar \lambda} \mathrm{d} \lambda = f(\lambda)\mathrm{d} \lambda \implies \boxed{f(\lambda) = \dfrac{1}{\bar \lambda}e^{-\lambda/\bar \lambda}}
$$

