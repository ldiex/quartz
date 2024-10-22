# 伴随算子
设$\mathcal A\in \mathcal{L}(V)$, 如果算子$\mathcal B\in \mathcal{L} (V)$满足对任意$\boldsymbol x, y\in V$都有$(\mathcal A(\boldsymbol x) \vert \boldsymbol y) = (\boldsymbol x \vert \mathcal B(\boldsymbol y))$, 则称$\mathcal B$是$\mathcal A$的*伴随算子（Adjoint Operator）*

设$\mathcal A\in \mathcal{L}(V)$, 则$\mathcal A$的伴随算子存在且唯一. 如果$\mathcal A$在$V$的[[Euclidean Space#单位正交基|单位正交基]]$\boldsymbol e_1, \ldots ,\boldsymbol e_n$下的矩阵等于$A$, 则其伴随算子在该基下的矩阵等于$A^t$

我们把$\mathcal A$的伴随算子记为$\mathcal A^*$
# 正规算子
> [!Tip]
> 我们只在$V = \mathbb{R}^n$时讨论正规算子

设$\mathcal A\in \mathcal{L} (V)$, 如果$\mathcal A \mathcal A^* = \mathcal A^* \mathcal A$, 则称$\mathcal A$是*正规算子（Normal Operator）*, 类似地, 设$A\in \mathrm{M}_n(\mathbb{R})$, 如果$AA^t = A^tA$, 则称$A$是*正规矩阵（Normal Matrix）*

特别地, 若$\mathcal A \mathcal A^* = \mathcal E$, 则称$\mathcal A$是*正交算子（Orthogonal Operator）*

由定义, 设$\mathcal A\in \mathcal{L} (V)$, $\mathcal A$在$V$的单位正交基$\boldsymbol e_1, \ldots ,\boldsymbol e_n$下的矩阵为$A$, 则$\mathcal A$正规当且仅当$A$正规

设$\mathcal A\in \mathcal{L}(V)$, 如果$\mathcal A^* = \mathcal A$, 则称$\mathcal A$是*对称算子（Symmetric Operator）*, 如果$\mathcal A^* = - \mathcal A$, 则称$\mathcal A$是*斜对称算子（Skew-symmetrix Operator）* . 由此可知, 对称和斜对称算子都是正规算子, 对称和斜对称矩阵都是正规矩阵

> [!Tip]
> [[Euclidean Space#正交矩阵|正交矩阵]]是正规矩阵, 这是因为设$P\in \mathrm{O}_n(\mathbb{R})$, 则有$P^tP = E = PP^t$
# 正规算子的保内性
设$\mathcal A\in \mathcal{L}(V)$, 如果对于任意$\boldsymbol x,\boldsymbol y\in V$
$$
(\boldsymbol x \vert \boldsymbol y) = \left( \mathcal A(\boldsymbol x)  \vert \mathcal A(\boldsymbol y)\right) 
$$
则称$\mathcal A$是*保内(积)的（preserve the inner product）*

若$\mathcal A$在$V$的单位正交基$\boldsymbol e_1, \ldots ,\boldsymbol e_n$下的矩阵为$A$, 则下列断言等价
1. $\mathcal A$保内
2. $A\in \mathrm{O}_n(\mathbb{R})$
3. 对任意$\boldsymbol x\in V,\; \Vert \boldsymbol x \Vert = \Vert \mathcal A(\boldsymbol x) \Vert$ （保长）
4. 对任意$\boldsymbol x, \boldsymbol y\in V,\; \Vert \boldsymbol x - \boldsymbol y \Vert = \Vert \mathcal A(\boldsymbol x) - \mathcal A(\boldsymbol y)\Vert$（保距离）
上述等价命题说明了正交矩阵的“旋转”性质, 且*保内算子*是正规算子, 也称为正交（保长, 保距）算子, 因为正交算子一定是正规算子

# 正规算子的不可分子空间分解
## 正规矩阵的形式
设$n$阶实方阵
$$
A = \begin{pmatrix}
B & C \\
O_{(n-k)\times k} & D
\end{pmatrix}
$$
其中$B\in \mathrm{M}_k(\mathbb{R})$, 那么如果$A$正规, 则$C = O_{k\times(n-k)}$, 这一点可以通过矩阵[[Matrix Trace|迹]]的交换不变性导出

## 正规算子的不变子空间
设$\mathcal A\in \mathcal{L}(V)$是正规算子, $W \subset V$是$\mathcal A$-子空间（$\mathcal A$的[[Invariant Subspace|不变子空间]]）, 则
1. $W^{\perp}$是$\mathcal A$-子空间
2. $\mathcal A$在$W$上的限制算子$\mathcal A |_W$是正规算子

这说明, 如果一个算子$\mathcal A$是正规的, 那么$W$是$\mathcal A$-不变子空间$\iff$ $W^{\perp}$是$\mathcal A$-不变子空间

## 实空间中不变子空间的维数
设$\mathcal A\in \mathcal{L}(V)$, 则$V$有一维或二维的$\mathcal A$子空间

这是因为$\mathbb{R}[t]$中的非平凡[[Gauss's Lemma and Eisenstein's Irreducibility Criterion#Eisenstein 不可约性判别法|不可约]]多项式的次数都不大于$2$, 所以设$A$的[[Minimal Polynomial|极小多项式]]$\mu_A = pq$,其中$p,q\in \mathbb{R}[t],0 < \deg{(p)} \leq 2$, $p$在$\mathbb{R}[t]$中不可约. 因为$\deg{(q) < \deg{(\mu_A)}}$且$\mu_A$是最小的零化$\mathcal A$的多项式, 故$q(\mathcal A) \neq \mathcal O$. 于是存在$\boldsymbol v\in V$使得$\boldsymbol w := q(\mathcal A)(\boldsymbol v) \neq \boldsymbol 0$. 设[[Cyclic Subspace|循环子空间]]$W = F[A]\cdot \boldsymbol w$, 则$\dim(W) > 0$, 又因为
$$
p(\mathcal A)(\boldsymbol w) = p(\mathcal A)q(\mathcal A)(\boldsymbol v) = \mu_A(\boldsymbol v)= \boldsymbol 0
$$
所以$\deg{(\mu_{\mathcal A, \boldsymbol w})} \leq 2$, 从而$\dim (W) \leq 2$, （考虑[[Minimal Polynomial#次数|零化某个向量的极小多项式的次数]]）

## 分解为正规算子的不可分子空间
设$\mathcal A\in \mathcal{L}(V)$正规, $n = \dim (V)$, 则
$$
V = U_1 \oplus \cdots \oplus  U_s \oplus  U_{2s+1} \oplus  \cdots \oplus  U_n
$$
其中
1. $U_1, \ldots ,U_s$是二维$\mathcal A$-不可分子空间
2. $U_{2s+1}, \ldots ,U_n$是一维$\mathcal A$-不可分子空间
3. $U_1, \ldots ,U_s,U_{2s+1}, \ldots ,U_n$两两正交




