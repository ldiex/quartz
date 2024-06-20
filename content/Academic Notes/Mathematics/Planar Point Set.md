# 平面点集
坐标平面上满足某种条件$P$的集合称为*平面点集*，记为
$$
E =\{(x, y) \mid (x, y) \text{ satisfies } P\}
$$

平面点集
$$
\begin{aligned}
\{(x, y) &\mid (x - x_0)^2 + (y - y_0)^2 < \delta^2\} \\
\{(x, y) &\mid |x - x_0| < \delta, |y - y_0| < \delta\}
\end{aligned}
$$
分别称为以$(x_0, y_0)$为中心的$\delta$*圆邻域*和$\delta$*方邻域*

类似地可以定义相应的*空心邻域*
$$
\begin{aligned}
\{(x, y) &\mid 0 <(x - x_0)^2 + (y - y_0)^2 < \delta^2\} \\
\{(x, y) &\mid |x - x_0| < \delta, |y - y_0| < \delta, (x, y) \neq (x_0, y_0)\}
\end{aligned}
$$
注意$\delta$方空心邻域的定义

## 点和点集的关系
讨论点$A$和点集$E$的关系
### 内点
若存在点$A$的某邻域$U(A) \subset E$, 则称$A$是$E$的*内点*，$E$的全部内点构成的几何称为$E$的*内部*，记为$\operatorname{int} E$

### 外点
若存在点$A$的某邻域$U(A) \cap E = \emptyset$，则称$A$是$E$的*外点*

### 界点
若在点$A$的任何邻域内既含有属于$E$的点，又含有不属于$E$的点，则称$A$是$E$的界点。即对任何$\delta > 0$，恒有
$$
(U(A; \delta) \cap E \neq \emptyset ) \land (U(A; \delta) \cap E^c \neq \emptyset)
$$
其中$E^c = \mathbb R^2 \backslash E$是$E$关于全平面的*余集*
$E$的全部界点构成$E$的*边界*，记为$\delta E$

### 聚点
若在点$A$的任何空心邻域$U^\circ(A)$内都含有$E$中的点，则称$A$为$E$的*聚点*；$A$本身可以属于$E$,也可以不属于$E$

### 孤立点
若$A \in E$，但不是$E$的*聚点*，即存在某一个正数$\delta$使得$U^\circ(A;\delta) \cap E = \emptyset$，则称$A$是$E$的*孤立点*

由此可知，孤立点一定是界点，内点和非孤立点的界点一定是聚点，既不是聚点，又不是孤立点的点必为外点

## 开集和闭集
### 开集
若平面点集$E$所属的每一个点都是$E$的内点（即$\operatorname{int} E = E$），则称$E$为*开集*

### 闭集
若平面点集$E$的所有聚点都属于$E$，则称$E$为*闭集*；若$E$没有聚点，也称$E$为*闭集*

#### 任意平面点集的边界都是闭集
1. 考虑$\forall S \in \mathbb R^2$设$x_0$为$\delta S$的任一聚点，只需要证明$x_0 \in \delta S$
2. 由于$x_0$是聚点，所以对任意$\varepsilon > 0$，存在$y \in U^\circ (x_0; \varepsilon) \cap \delta S$
3. 由于$y$又是$S$的界点，所以对任意$U(y; \delta) \subset U(x_0; \varepsilon), U(y; \delta)$上既有$S$的点，也有非$S$的点
4. 所以$x_0$的任意$\varepsilon$邻域内也都存在属于$S$的点和不属于$S$的点，所以$x_0 \in \delta S$

## 开域和闭域
### 开域
若非空开集$E$具有*连通性*，即$E$中的任意两点之间都可用一条完全含于$E$的有限折线（由有限条直线段连接而成的折线）相连接，则称$E$为*开域*（即*非空连通开集*）

### 闭域
开域连同其边界所成的点集称为*闭域*

### 区域
开域、闭域或者开域连同其一部分边界所成的点集统称为*区域*

## 有界点集
对于平面点集$E$，若存在某一个正数$r$，使得
$$
E \subset U(O;r)
$$
其中$O$为坐标原点（也可以是其他点），则称$E$是*有界点集*，否则为*无界点集*

$E$为有界点集的一个等价定义是，存在矩形区域$E \subset [a, b] \times [c, d]$ 

### 点集的直径
定义点集$E$的*直径*
$$
d(E) = \sup_{P_1 ,P_2} \rho(P_1, P_2)
$$
其中$\rho$是欧几里得度规
$$
\rho(P, Q) = \sqrt{(x_P-x_Q)^2 + (y_P - y_Q)^2}
$$
于是，当且仅当$d(E)$是有限值时$E$是有限点集

# $\mathbb R^2$上的完备性定理
## 平面点列的收敛性
设$\{P_n\} \subset \mathbb R^2$为平面点列，$P_0 \in \mathbb R^2$为一固定点。若对任给的正数$\varepsilon$，存在正整数$N$，使得当$n > N$时，有$P_n \in U(P_0; \varepsilon)$，则称点列$\{P_n\}$收敛于$P_0$，记为
$$
\lim_{n \to \infty} P_n = P_0
$$
## Cauchy 准则
平面点列$\{P_n\}$收敛的充要条件是：任给正数$\varepsilon > 0$，存在正整数$N$，使得当$n > N$时，对一切正整数$p$都有
$$
\rho(P_n, P_{n + p}) < \varepsilon
$$
## 闭域套定理
设$\{D_n\}$是$\mathbb R^2$中的闭域列，它满足
1. $D_{n + 1} \subset D_n,\; n = 1, 2, \cdots$
2. $d_n = d(D_n), \lim_{n \to \infty} d_n = 0$
则存在唯一的点$P_0 \in D_n,\; n = 1, 2, \cdots$

## 聚点定理
设$E \subset \mathbb R^2$为有界无限点集，则$E$在$\mathbb R^2$中至少存在一个聚点

### 推论：有界无限点列必然存在收敛子列
## 有限覆盖定理
如果某一个有界闭域能被一开域族覆盖，那么必然可以从中选出有限个开域覆盖这个闭域
