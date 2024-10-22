设$V$是$\mathbb R$上的$n$维线性空间, $V$上所有[[Quadratic Forms | 二次型]] 的集合记为$\mathcal Q(V)$
# 惯性定理 (Sylvester)
设$q$是$V$上的二次型. 则存在$q$的一组规范基$\boldsymbol e_1, \cdots, \boldsymbol e_n$使得在该基下$q$的矩阵为
$$
\begin{pmatrix}
E_k & O & O \\
O & -E_\ell & O \\
O & O & O
\end{pmatrix}
$$
且$k + \ell = \mathrm{rank} (q)$. 进而, 如果$q$在另一组规范基下的矩阵是
$$
\begin{pmatrix}
E_s & O & O \\
O & -E_t & O \\
O & O & O
\end{pmatrix}
$$
则$s = k, t = \ell$

这里之所以会出现负号是因为负实数的不可开方性质

由此, 我们称$k$是$A$的*正惯性指数*, $\ell$是$A$的*负惯性指数*, 并称$(k, \ell)$为$A$的*签名*, 且这**两个惯性指数的和为矩阵的秩**


> [!Tip]
> 如果$A$的正惯性指数是$k$, 那么必然存在一个$k$维的$V$的子空间$W$使得$q |_{W}$恒正（除去零向量）

对于$A, B \in \mathrm{SM}_n(\mathbb R)$, 则$A \sim_c B$当且仅当$A,B$有共同的签名

## 一个特殊的实二次型
设
$$
\begin{aligned}
q: \mathrm{M}_n(\mathbb R) &\to \mathbb R \\
A &\to \mathrm{tr} (A^2)
\end{aligned}
$$
其中$\mathrm{tr} A$表示$A$的[[Matrix Trace| 迹]]
则$q$是二次型, 且它的签名是
$$
\left(\dfrac{n(n + 1)}{2}, \dfrac{n(n - 1)}{2}\right)
$$
# （半）正定二次型
设$q$是$V$上的二次型
- 如果对$\forall \boldsymbol x \in V, \; q(\boldsymbol x) \ge 0$,则称$q$是*半正定*的
- 如果对$\forall \boldsymbol x \in V \backslash \{\boldsymbol 0\}, \; q(\boldsymbol x) > 0$,则称$q$是*正定*的
- 如果对$\forall \boldsymbol x \in V, \; q(\boldsymbol x) \le 0$,则称$q$是*半负定*的
- 如果对$\forall \boldsymbol x \in V \backslash \{\boldsymbol 0\}, \; q(\boldsymbol x) < 0$,则称$q$是*负定*的
- 如果$q$既不是半正定也不是半负定的, 则称$q$是*不定*的

设$\dim(V) = n$且$q$是$V$上的二次型, 它的签名是$(k, \ell)$, 则
- $q$是半正定的$\iff \ell = 0$
- $q$是正定的$\iff k = n$
- $q$是半负定的$\iff k = 0$
- $q$是负定的$\iff \ell = n$
- $q$是不定的$\iff k > 0, l > 0$

半正定, 正定, 半负定, 负定二次型分别有下列规范型
$$
x_1^2 + \cdots + x_k^2, \quad x_1^2 + \cdots + x_n^2, \quad -x_1^2 -\dots -x_l^2,\quad -x_1^2 - \cdots - x_n^2
$$
类似地, 对于$\forall A \in \mathrm{SM}_n(\mathbb R)$, 可类似定义矩阵的正定性

## 锥面
设$q \in \mathcal Q(V)$, 定义
$$
C_q = \{\boldsymbol v \in V \mid q(\boldsymbol v) = 0\}
$$
则称$C_q$为$q$确定的*锥面*

设$q \in \mathcal Q(V)$. 则$C_q$是$V$的子空间当且仅当$q$是半正定或半负定的

# （半）正定矩阵的等价条件
实数域的一个基本性质是: 设$x_1, \cdots, x_n \in \mathbb R$. 则
$$
x_1^2 + \cdots + x_n^2 \ge 0;\quad x_1^2 + \cdots + x_n^2 = 0 \implies x_1 = \cdots = x_0 = 0
$$
于是, 设
$$
\boldsymbol x = \begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix} \in \mathbb R^n
$$
则有
$$
\boldsymbol x^t \boldsymbol x \ge = 0; \quad \boldsymbol x^t\boldsymbol x = 0 \implies \boldsymbol x = 0
$$
设$A \in \mathbb R^{m \times n}$. 则$A^t A \in \mathrm{SM}_n(\mathbb R)$半正定且$\mathrm{rank}(A^tA) = \mathrm{rank}(A)$
> [!Note] （半）正定矩阵的等价条件
> 设$A \in \mathrm{SM}_n(\mathbb R)$. 则
> - $A$半正定当且仅当存在$B \in \mathrm{M}_n(\mathbb R)$使得$A = B^t B$
> - $A$正定当且仅当存在$B \in \mathrm{GL}_n(\mathbb R)$使得$A = B^t B$

这里利用了
$$
\begin{pmatrix}
E_r & O \\ 
O & O
\end{pmatrix} = \begin{pmatrix}
E_r & O \\ 
O & O
\end{pmatrix} \begin{pmatrix}
E_r & O \\ 
O & O
\end{pmatrix}
$$
若$A$是正定矩阵, 那么$\det(A) > 0$且$A^{-1}$也正定
> [!tip] 算子的情况
> 利用[[Spectral Decomposition|谱分解定理]], 我们知道若$\mathcal A\in \mathcal{L}(V)$是半正定算子, 则存在唯一的半正定算子$\mathcal B$使得$\mathcal B^{2} = \mathcal A$且$\mathcal B\in \mathbb{R}[\mathcal A]$

事实上, 如果$\mathcal A$的谱分解有如下形式
$$
\mathcal A = \lambda_1\pi_1+ \cdots +\lambda_k\pi_k
$$
则对应的$\mathcal B$为
$$
\mathcal B = \sqrt{ \lambda_1 }\pi_1+ \cdots +\sqrt{ \lambda_k } \pi_k
$$
# Jacobi公式
设$A \in \mathrm{SM}_n(F)$. 设$\Delta_0 = 1,\; \Delta_i$是$A$中第$1 \sim i$行和$1\sim i$列构成的对称矩阵的行列式（也就是[[Matrix Minor#Leading Principal Minor | 顺序主子式]]）, 则
$$
A \sim_c \mathrm{diag} \left(\dfrac{\Delta_1}{\Delta_0}, \dfrac{\Delta_2}{\Delta_1},\ldots,\dfrac{\Delta_{n}}{\Delta_{n - 1}}\right)
$$
## 和正定矩阵的关系
设$\Delta_k$是$A$的$k$阶顺序主子式, $k = 1, 2, \ldots, n$. 则下列命题等价
1. $A$正定
2. $A$的任何$k$阶[[Matrix Minor#Principal Minor | 主子式]] 都大于$0$
3. $\Delta_1 > 0, \ldots, \Delta_n > 0$
> [!Note] 负定(Negative Definite)的情况
> 如果$A$是负定的, 那么$-A$是正定的, 考虑到$\det(-A) = (-1)^n \det A$, 此时$A$的顺序主子式需要满足$\Delta_1 < 0, \Delta_2 > 0, \Delta_3 < 0, \Delta_4 > 0, \ldots$
# Hadamard 不等式
设$A \in \mathrm{SM}_n(\mathbb R)$正定. 则$\det(A)$不大于$A$的对角线上元素之积, 即
$$
\left|{\det(A)}\right| \le \mathrm{tr} A
$$

于是有*Hadamard不等式*
$$
\left|{\det(A)}\right| \le \sqrt{\prod_{i = 1}^n \sum_{j = 1}^n a_{i, j}^2},\quad \left|{\det(A)}\right| \le \sqrt{\prod_{i = 1}^n \sum_{j = 1}^n a_{j,i}^2}
$$


