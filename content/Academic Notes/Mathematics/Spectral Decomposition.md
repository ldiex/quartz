*谱分解*理论是对[[Linear Operator|线性算子]]的[[Diagonalization|对角化]]过程在剔除[[Matrix Representation of Linear Map|矩阵表示]]下的抽象
# 完全正交等方组
设$\sigma_1, \ldots ,\sigma_k\in \mathcal{L} (V)$, 如果
1. 正交性: 对任意$i,j\in \left\{ 1, \ldots ,k \right\},i\neq j$都有$\sigma_i \circ \sigma_j = \mathcal O$
2. 等方性: 对任意$i\in \left\{ 1, \ldots ,k \right\}$都有$\sigma_i^{2} = \mathcal E$
3. 完全性: $\sigma_1+ \cdots +\sigma_k = \mathcal E$
则称$\sigma_1, \ldots ,\sigma_k$是*完全正交等方组*

例如设$V = U_1 \oplus \cdots \oplus U_k$, 其中$U_1, \ldots ,U_k$是[[Linear Space#子空间|子空间]], 若令$\pi_i:V\to V$是从$V$到$U_i$的[[Projection|投影映射]], 则$\pi_1, \ldots ,\pi_k$是完全正交等方组

反过来, 我们可以证明, 如果$\sigma_1, \ldots ,\sigma_k\in \mathcal{L}(V)$是完全正交等方组, 则有
$$
V = \mathrm{im}(\sigma_1) \oplus \cdots \oplus  \mathrm{im}(\sigma_k)
$$
由正交性和等方性, 如果我们再设$\alpha_1, \ldots ,\alpha_k\in F$, 则对于任意非负整数$m$都有
$$
(\alpha_1\pi_1+ \cdots +\alpha_k\pi_k)^m = \alpha_1^m\pi_1+ \cdots +\alpha_k^m\pi_k
$$
# 谱分解定理
设$\mathcal A\in \mathcal{L}(V)$可[[Diagonalization|对角化]], 则
1. 存在唯一的$\lambda_1, \ldots ,\lambda_k\in F$两两不同, 和完全正交等方组$\pi_1, \ldots ,\pi_k$满足
$$
\mathcal A = \lambda_1\pi_1+ \cdots +\lambda_k\pi_k
$$
2. 存在$f_1, \ldots ,f_k\in F[t]$满足$f_i(\lambda_j) = \delta_{i,j},\;\pi_i = f_i(\mathcal A)$, $i,j\in \left\{ 1,2, \ldots ,k \right\}$
