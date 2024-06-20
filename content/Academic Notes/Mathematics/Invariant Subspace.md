# 定义
设$\mathcal A \in \mathcal L(V)$, $U$是$V$的子空间. 如果$\mathcal A(U) \subset U$, 即$\forall \boldsymbol u \in U , \mathcal A(\boldsymbol u) \in U$. 则称$U$是$\mathcal A$的*不变子空间*, 或者称$U$是 *$\mathcal A$-子空间*

设$U$是$\mathcal A$的不变子空间，则$\mathcal A |_U$可以看做$U$上的[[Linear Operator|线性算子]]，可简记限制映射$\mathcal A|_U$为$\mathcal A_U$

# 单和半单
$\{\boldsymbol 0\},V$都是$\mathcal A$的不变子空间，我们称它们是*平凡的*

如果$V$没有*非平凡*的子空间，我们称$V$是*单(simple)* 的，也可以称为是*不可分子空间*

如果$V$是一系列*单不变子空间*的直和，则称$V$是*半单(semisimple)* 的。$\cal A$的[[Diagonalization|可对角化]]性质蕴含了$V$是半单的；当$V$是复线性空间时，半单和可对角化等价

下面三点总是等价的
1. $V$是半单的
2. 如果$W\subset V$是不变子空间，那么它就有一个不变的*补*，也就是说存在不变子空间$W'$使得$V = W \oplus W'$
3. $V$由它的单不变子空间们生成

通过*循环子空间*，有判定一个子空间是否为单不变子空间的[[Cyclic Subspace#不可分子空间的判定准则|定理]]
# 常见的不变子空间

设$\mathcal A\in \mathcal L(V)$满足$\mathcal A \mathcal B = \mathcal B \mathcal A$，则$\ker(\mathcal B), \mathrm{im}(\mathcal B)$是$\mathcal A$的不变子空间，由$F[A]$是交换环，故有

> [!Note]
> - 设$\mathcal A \in \mathcal{L}(V), f\in F[t]$. 则$\ker(f(\mathcal A))$和$\mathrm{im}(f(\mathcal A))$都是$\mathcal A$的不变子空间
> - 特别地，$\ker(\mathcal A), \mathrm{im}(\mathcal A)$是$\mathcal A$的不变子空间

# 不变子空间的交、和
设$\mathcal A \in \mathcal{L}(V)$, $U_1, U_2$是$\mathcal A$-子空间. 则$U_1 + U_2$和$U_1 \cap U_2$都是$\mathcal A$-子空间

# 线性轨道
设$\boldsymbol v\in V$，那么算子$\mathcal A$在$\boldsymbol v$上的*轨道(orbit)* 被定义为集合$\displaystyle \left\{ \mathcal A^k \boldsymbol v \right\}_{k=0}^\infty$

而$\boldsymbol v$的*线性轨道(linear orbit)* $[\boldsymbol v]$就是由$\mathcal A$在$\boldsymbol v$上的*轨道* 张成的子空间，即
$$
[\boldsymbol v ] = \left< \boldsymbol v,\mathcal A(\boldsymbol v), \mathcal A^2(\boldsymbol v),\ldots \right> 
$$
对于任意的$\boldsymbol v \in V$, $[\boldsymbol v]$总是$V$的不变子空间，并且**它是最小的包含$\boldsymbol v$的不变子空间**，也就是说如果$W\subset V$是一个包含$\boldsymbol v$的不变子空间，则$[\boldsymbol v] \in W$

# 算子矩阵的形式

**例子**：设$\mathcal D$是$\mathbb{R}[x]^{(n)}$上的导数算子，则$\mathbb{R}[x]^{(k)}$是$\mathcal D$的不变子空间，$k = 1, 2,\ldots, n$. 
设$\lambda \in F$, 则$\mathcal{L}(V)$中的每一个线性算子都是关于$\lambda \mathcal E$不变的

设$\mathcal A \in \mathcal L(V)$，$U$是$\mathcal A$的$d$维不变子空间，$0 < d < n$. 则存在$V$的一组基使得$\mathcal A$在该基底下的矩阵为
$$
A = \begin{pmatrix}
B & C \\
O & D
\end{pmatrix}
$$
其中$B \in \mathrm{M}_d(F)$是$\mathcal A_U$的某个矩阵表示，进而$\mu_{\mathcal A_U} \mid \mu_\mathcal A, \mu_B \mid \mu_A, \mu_D \mid \mu_A$, ($\mu_\mathcal A$的定义见[[Minimal Polynomial#整除判别法|首一极小多项式]])

有这样的矩阵表示是因为$\mathcal A(\boldsymbol e_j), j \in \{1, 2, \ldots,d\}$关于$\boldsymbol e_{d + 1}, \ldots, \boldsymbol e_n$的坐标都等于$0$, 所以左边是$\begin{pmatrix}B \\ O\end{pmatrix}$
由于可直接验证对$\forall k \in \mathbb{N}$, $A^k = \begin{pmatrix}B^k & * \\ O & E^k\end{pmatrix}$，其中$*$是某个$d\times(n - d)$阶的矩阵，于是对任意$f \in F[t]$有
$$
f(A) = \begin{pmatrix}
f(B) & * \\
O & f(D)
\end{pmatrix}
$$
因为$\mu_A(A) = O_{n \times n}$所以$\mu_A(B) = O_{d \times d}, \mu_A(D) = O_{(n-d) \times (n-d)}$. 故由[[Minimal Polynomial#整除判别法|整除判别法]]，$\mu_B \mid \mu_A, \mu_D \mid \mu_A$且$\mu_{\mathcal A_U} \mid \mu_\mathcal A$
# 算子的不变子空间分解（矩阵的分块对角化）
设$\mathcal A \in \mathcal{L}(V)$, $U_1, U_2$是非平凡$\mathcal A$-子空间，且$V = U_1 \oplus U_2$. 设$\epsilon_1, \ldots, \epsilon_{d_{1}}$是$U_1$的基，$\delta_1, \ldots, \delta_{d_2}$是$U_2$的基，则在$V$的基底$\epsilon_1, \ldots, \epsilon_{d_1}, \delta_1, \ldots, \delta_{d_2}$下$\mathcal A$的矩阵是
$$
A = \begin{pmatrix}
A_1 & O \\
O & A_2
\end{pmatrix}
$$
其中$A_i \in M_{d_i}(F)$是$\mathcal A_{U_i}$在对应基下的矩阵，$i = 1, 2$. 进而$\mu_{\mathcal A} = \mathrm{lcm}(\mu_{\mathcal A_{U_1}}, \mu_{\mathcal A_{U_2}})$

> [!Tip] 例
> 计算$\mu_A, \; A = \begin{pmatrix}1 & 0 \\ 0 & 0\end{pmatrix}$; 则$\mu_A = \mathrm{lcm}(\mu_{(1)}, \mu_{(0)}) = \mathrm{{lcm}(t - 1, t)} = (t-1)t$

设$\mathcal A \in \mathcal{L}(V)$满足$\ker(\mathcal A) \oplus \mathrm{im}(\mathcal A)$, 射$\boldsymbol e_1, \ldots, \boldsymbol e_r$是$\mathrm{im}(\mathcal A)$的一组基，$\boldsymbol e_{r + 1}, \ldots, \boldsymbol e_n$是$\ker(\mathcal A)$的一组基，则$\mathcal A$在这些基底下的矩阵是
$$
A = \begin{pmatrix}
B & O \\
O & O
\end{pmatrix}
$$
其中$B \in M_r(F)$满秩，当$r = n$时有$B = A$, 否则$\mu_A = \mathrm{lcm}(\mu_B. t)$

设$\mathcal A \in \mathcal{L}(V),\; U_1, \ldots, U_k$是非平凡$\mathcal A$-子空间满足$V = U_1\oplus \cdots \oplus U_k$. 设$Z_i$是$U_i$的一组基，$i = 1, \ldots, k$, 则$\mathcal A$在$V$的基底$Z_1\cup \cdots \cup Z_k$下的矩阵
$$
A = \begin{pmatrix}
A_1 & O & \cdots & O \\
O & A_2 & \cdots & O \\
\vdots & \vdots & \ddots & \vdots \\
O & O & \cdots & A_k
\end{pmatrix}
$$
其中$A_i$是$\mathcal A_{U_i}$在$Z_i$下的矩阵，$i = 1, 2, \ldots, k$, 进而
$$
\mu_\mathcal A = \mathrm{lcm}(\mu_{\mathcal A_{U_1}}, \ldots, \mu_{\mathcal A_{U_k}})
$$
# 核核分解
回顾[[Multivariate Polynomial Ring#核核分解|多元多项式环上的核核分解]]，若$\mathcal A \in \mathrm{Hom}(V,V), \; f\in F[x]$且$f(\mathcal A) = \mathcal O$, 如果有
$f = pq$, 其中$p, q \in F[x]$互素，则有
$$
V = \ker(p(\mathcal A)) \oplus \ker(q(\mathcal A))
$$
现对该结论进行推广

若$\mathcal A \in \mathrm{Hom}(V,V), \; f\in F[x]$且$f(\mathcal A) = \mathcal O$, 如果
$$
f = p_1\cdots p_m
$$
其中$p_1, \ldots, p_m \in F[x]$两两互素，则
$$
V = K_1 \oplus \cdots \oplus K_m
$$
其中$K_i = \ker(p_i(\mathcal A))$

## 极小多项式版本
设$\mathcal A \in \mathcal{L}(V), \; \mu_\mathcal A = p_1^{m_1} \cdots P_s^{m_s}$, 其中$p_1, \ldots, p_s \in F[t]\backslash F$不可约且两两互素，$m_1, \ldots, m_s \in \mathbb{Z}^+$，令
$$
K_i = \ker(P_i^{m_i}(\mathcal A))
$$
则
$$
V = K_1 \oplus \cdots \oplus K_s
$$
且$\mathcal A|_{K_i}$的极小多项式是$p_i^{m_i}$



