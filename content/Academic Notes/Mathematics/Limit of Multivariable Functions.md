# 二元函数
设平面点集$D \subset \mathbb R^2$，若安装某对应法则$f$，$D$中的每一点$P(x, y)$都有唯一确定的实数$z$与之对应，则称$f$为定义在$D$上的*二元函数*，记作
$$
\begin{aligned}
f: D &\to \mathbb R \\
P &\to z
\end{aligned}
$$

若二元函数的值域是有界数集，则称该函数为*有界函数*；若是无界数集，则称该函数为*无界函数*

类似地可定义$n$元函数
# 二元函数的极限
## 定义
设$f$为定义在$D \subset \mathbb R^2$上的二元函数，$P_0$是$D$的一个聚点，$A$是一个确定的实数. 若对任意正数$\varepsilon$, 都存在某正数$\delta$，使得当$P \in U^\circ(P_0;\delta) \cap D$时，都有
$$
\left|{f(P) - A}\right| < \varepsilon
$$
则称$f$在$D$上当$P \to P_0$时以$A$为极限，记作
$$
\lim_{P \to P_0,P \in D} f(P) = A
$$
当对$P \in D$不至于产生误解时可写作
$$
\lim_{P \to P_0} f(P) = A
$$
### 判定定理
$\displaystyle \lim_{P \to P_0, P \in D}f(P) = A$的充要条件是：对于$D$的任一子集$E$，只要$P_0$是$E$的聚点，就有
$$
\lim_{P \to P_0, P \in E} f(P) = A
$$
由此定理
1. 如果在某个$P_0$为聚点的子集$E_1$中极限不存在，在$D$中极限也不存在
2. 如果在某两个$P_0$为聚点的子集$E_1, E_2$中极限存在但是不同，则在$D$中极限也不存在
故若想证明不存在可以给$(x, y)$增加如一条直线这样的约束，观察通过不同轨迹趋近的结果是否相同

### 非正常极限
设$D$为二元函数$f$的定义域，$P_0(x_0, y_0)$是$D$的一个聚点. 若对任给正数$M$，总存在点$P_0$的一个$\delta$邻域，使得当$P(x,y) \in U^\circ(P_0; \delta) \cap D$时，都有$f(P) > M$. 则称$f$在$D$上当$P \to P_0$时，存在*非正常极限*$+\infty$，记作
$$
\lim_{(x, y) \to (x_0, y_0)} f(x, y) = +\infty
$$
## 累次极限
$(x, y) \to (x_0, y_0)$称为*重极限*

设$f(x, y),\; (x, y) \in D, D$在$x$轴、$y$轴上的投影分别为$X, Y$，即
$$
X= \{x \mid (x,y) \in D\},\; Y = \{y \mid (x, y) \in D\}
$$
$x_0, y_0$分别是$X, Y$的聚点，若对$\forall y \neq y_0 \in Y$,存在极限
$$
\varphi(y) = \lim_{x \to x_0} f(x, y)
$$
且进一步存在极限
$$
L = \lim_{y \to y_0} \varphi(y)
$$
则称此极限$L$为$f(x, y)$先对$x$后对$y$的*累次极限*，记作
$$
L = \lim_{y \to y_0} \lim_{x \to x_0} f(x, y)
$$
同理可以定义先$y$后$x$的累次极限
$$
K = \lim_{x \to x_0}\lim_{y \to y_0} f(x, y)
$$
**累次极限与重极限是两个不同的概念，它们的存在性没有必然的蕴含关系**

**但是如果重极限和累次极限（某一个）都存在，则它们必然相等**. 如果两个累次极限存在但是不相等，则重极限不存在

# 二元函数的连续性
## 定义
设$f$为定义在点集$D \subset \mathbb R^2$上的二元函数，$P_0 \in D$且它或者是$D$的[[Planar Point Set#聚点 |聚点]]或者是$D$的[[Planar Point Set#孤立点|孤立点]]. 对于任给的正数$\varepsilon$，总存在相应的正数$\delta$，只要$P \in U(P_0;\delta) \cap D$就有
$$
\left|{f(P) - f(P_0)}\right| < \varepsilon
$$
则称$f$**关于集合$D$** 在点$P_0$*连续*. 在不导致误解的情况下，也称$f$在点$P_0$连续. 若$f$在$D$上的任何点都关于$D$连续，则称$f$为$D$上的*连续函数*

由此可知，若$P_0$是$D$的[[Planar Point Set#孤立点|孤立点]]，也就说存在$P_0$的一个去心邻域使得它和$D$的交集为空集，那么$P_0$必然是$f$关于$D$的连续点；若$P_0$是$D$的[[Planar Point Set#聚点 |聚点]]，则$f$关于$D$在$P_0$连续等价于
$$
\lim_{P \to P_0;P \in D} f(P) = f(P_0)
$$
如果$P_0$是$D$的聚点其上述极限条件不满足，则称$P_0$是$f$的*不连续点*（或者称为*间断点*），如果左边极限存在且不等于右边，则称$P_0$是$D$的*可去间断点*（或第*一类不连续点*）

### 全增量和偏增量
#### 全增量
设$z = f(x, y)$, 则
$$
\Delta z = f(x, y) - f(x_0, y_0) = f(x_0 + \Delta x, y_0 + \Delta y) -f(x_0, y_0)
$$
为函数$f$在点$P_0(x_0, y_0)$的*全增量*，由此当
$$
\lim_{\substack{(\Delta x, \Delta y)\to (0, 0) \\ (x, y) \in D}} \Delta z =0
$$
时，$f$在$P_0$连续
#### 偏增量
如果在全增量中取$\Delta x = 0$或者$\Delta y = 0$，则相应的函数增量被称为*偏增量*，记作
$$
\begin{aligned}
\Delta_x z &= f(x_0 + \Delta x, y_0) - f(x_0, y_0) \\
\Delta_y z &= f(x_0, y_0 + \Delta y) - f(x_0, y_0)
\end{aligned}
$$
一般来说，函数的全增量不等于相应的两个偏增量之和
如果有$\displaystyle \lim_{\Delta x \to 0} \Delta_x f(x_0, y_0) =0$或者$\displaystyle \lim_{\Delta y \to 0} \Delta_x f(x_0, y_0) =0$，则称$f$作为$x$的一元函数在$x_0$连续或者作为$y$的一元函数在$y_0$连续. 但是，**二元函数对两个自变量都连续不能保证该函数的连续性**

### 复合函数的连续性
设函数$u = \varphi(x, y)$和$v = \psi(x, y)$在$xy$平面上点$P_0(x_0, y_0)$的某邻域内有定义，并在点$P_0$连续；函数$f(u, v)$在$uv$平面上的点$Q_0(u_0, v_0)$的某邻域内有定义且在$Q_0$连续，其中$u_0 = \varphi(x_0, y_0), v_0 = \psi(x_0, y_0)$. 则复合函数$f(x, y) = f[\varphi(x, y), \psi(x, y)]$在点$P_0$连续

## 有界闭域上连续函数的性质
### 有界性和最大、最小值定理
若函数$f$在有界[[Planar Point Set#闭域|闭域]]$D \subset \mathbb R^2$上连续，则$f$在$D$上有界，且能取到最大值与最小值
### 一致连续性定理
若函数$f$在有界闭域$D \subset \mathbb R^2$上连续，则$f$在$D$上*一致连续*. 即对$\forall \varepsilon > 0$，总存在之依赖于$\varepsilon$的正数$\delta$，使得对于一切点$P, Q$，$\rho(P, Q) < \delta \implies \left|{f(P) - f(Q)}\right| < \varepsilon$
### 介值性定理
设函数$f$在区域$D \subset \mathbb R^2$上连续，若$P_1, P_2 \in D$且$f(P_1) < f(P_2)$，则对任何满足$f(P_1) < \mu < f(P_2)$的$\mu$，必然存在$P_0 \in D$使得$f(P_0) = \mu$



