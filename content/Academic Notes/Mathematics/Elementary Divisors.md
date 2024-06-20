该节通过*初等因子组*讨论一般域下的[[Jordan Canonical Form|Jordan标准型]]

# 重集
*重集*是元素可以重复出现的集合

设$S = \left\{ a,a,b \right\},\;T = \left\{ a,b \right\}$. 它们作为重集不相等. 元素$a$在$S$中的*重数*等于$2$，在$T$中等于$1$

可以利用重集表示$24$的素因子为$\left\{ 2,2,2,3 \right\}$

> [!Tip]
> 下文中出现的重数一般指重集概念中的重数
# 初等因子组
设$\mathcal A \in \mathcal{L}(V)$
$$
V = W_1\oplus \cdots \oplus W_k
$$
是$V$的$\mathcal A$-[[Cyclic Subspace#不可分子空间的判定准则|不可分子空间直和分解]]，设$\mathcal A_i = \mathcal A_{W_i},\;\mu_i = \mu_{\mathcal A_i}$，重集$\left\{ \mu_1,\ldots,\mu_k \right\}$称为$\mathcal A$关于上述不可分子空间直和分解的*初等因子组*，由[[Cyclic Subspace#不可分子空间的判定准则|不可分子空间的判断准则]]，初等因子组中的元素都是$F[t]$中首一的不可约多项式的幂次

例如$\mathcal E$是$V$上的恒同算子，$\boldsymbol e_1, \ldots, \boldsymbol e_n$是$V$的一组基，则有
$$
V = \left< \boldsymbol e_1 \right> \oplus\cdots \oplus \left< \boldsymbol e_n \right> 
$$
且$\mathcal E$关于这个直和分解的初等因子组为
$$
\underbrace{\left\{ t-1,\ldots,t-1 \right\}}_n
$$
又如$\mathcal D$是$\mathbb{R}[x]^n$上的导数算子，则$\mathbb{R}[x]^n$是$\mathcal D$-不可分的. 于是，$\mathcal D$的初等因子组是$\left\{ t^n \right\}$

# 不可分子空间极小多项式的秩
设$\mathcal A \in \mathcal{L}(V)$，$V$是$\mathcal A$-[[Cyclic Subspace#循环空间和循环算子|循环]]的. 设$\mu_\mathcal A = p^m$，其中$p\in F[t]\backslash F$，则
$$
\mathrm{rank}(p(\mathcal A)^k) = \begin{cases}
(m-k)\deg(p), &0\le k \le m \\
0,&k>m
\end{cases}
$$
回忆[[Cyclic Subspace#不可分子空间的判定准则|不可分子空间的性质]]，首先它是循环的，其次$\mathcal A$限制在$V$上的算子的极小多项式是$F[t]$中某个**不可约多项式**的幂次，不妨设为$\mu_\mathcal A = p^m$，那么我们就可以给出它的所有因子作用在$\mathcal A$上后形成的新算子的[[Matrix Rank|秩]]
# 只有一个不可约因子的情况
如果$\mathcal A$的[[Characteristic Polynomial|特征多项式]]（容易得到）只有一个不可约因子$p$，那么它的极小多项式必然也只有一个因子，这个时候就可以给出这个因子的某个幂次$p^\ell$在直和分解产生的*初等因子组*中的[[Elementary Divisors#重集|重数]]（在集合中出现的次数）。从[[Jordan Canonical Form#Jordan标准型的形式|Jordan标准型的形式]]中，我们知道
- 某个初等因子$p^\ell$是对应不可分空间的极小多项式，它的*重数*（多项式的重数），即$\ell$，就对应着Jordan块的大小$J_\ell(\lambda)$，这里的$\lambda$满足$p(\lambda)=0$
- 这个初等因子$p^\ell$在整个初等因子组中的*重数*（出现的次数），设为$n_\ell$，则为对应Jordan块$J_\ell(\lambda)$在Jordan标准型中出现的次数，也就是$\lambda$对应特征子空间的[[Eigenvectors and Characteristic Polynomial#维数和重数|几何重数]]

下面给出$n_\ell$的计算方式：

设$\mathcal A \in \mathcal{L}(V),\;\mu_\mathcal A = p^m$. 其中$p \in F[t]\backslash F$不可约，对任意$\ell \in \mathbb{Z}^+$，设$n_\ell$是$p^\ell$在$V$的某个$\mathcal A$-不可分子空间直和分解的*初等因子组*中$p^\ell$的重数. 令$d = \deg(p)$和$r_i = \mathrm{rank}(p^i(\mathcal A)),i \in \mathbb{N}$，则
$$
n_\ell = \dfrac{1}{d}(r_{\ell -1}+r_{\ell + 1}-2r_{\ell})
$$
## 例子
例如有
$$
A =\begin{pmatrix}
-3 & 1 & -6 & 5 \\
5 & -1 & 8 & -7 \\
-2 & 1 & -5 & 4 \\
-5 & 2 & -11 & 9
\end{pmatrix} \in \mathrm{M}_4(\mathbb{C})
$$
已知$\chi_A = t^4$. 则有$p = t$，那么就有$r_0 = \mathrm{rank}(A^0) = 4\;,r_1 = \mathrm{rank}(A) = 2$
于是，$0$的[[Eigenvectors and Characteristic Polynomial#维数和重数|几何重数]]为$n - \mathrm{rank}(A) = 4  - 2 = 2$，由此推出$J_A$中有两个关于$0$的[[Jordan Canonical Form#Jordan块|Jordan块]]，且又由于
$$
r_2 = \mathrm{rank}(A^2) = \mathrm{rank} \begin{pmatrix}
1 & 0 & 1 & -1 \\
-1 & 0 & -1 & 1 \\
1 & 0 & 1 & -1 \\
2 & 0 & 2 & -2
\end{pmatrix} = 1
$$
于是
$$
n_1 = 4+1-2\times 2 = 1
$$
由此可直接推出$n_2 = 0,n_3 = 1, n_4 = 0$，故
$$
J_A = \begin{pmatrix}
J_3(0)  &  \\
 &  J_1(0)
\end{pmatrix} = \begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

# 有多个不可约因子的情况
设$\mathcal A \in \mathcal{L}(V)$，$\mu_\mathcal A$在$F[t]$中的两两互素首一不可约因子是$p_1,\ldots,p_s$，它们的次数分别是$d_1,\ldots,d_s$. 设$\ell \in \mathbb{Z}^+,\; i \in \left\{ 1,2,\ldots,s \right\}$. $N(i,\ell)$是$p_i^\ell$在$V$的某个$\mathcal A$-不可分子空间直和分解的初等因子组中的重数（出现的次数），则
$$
N(i,\ell) = \dfrac{1}{d_i}\left( R(i,\ell -1)+R(i,\ell + 1)-2R(i,\ell) \right) 
$$
其中$R(i,j) = \mathrm{rank}(p_i(\mathcal A)^j),\; j \in \mathbb{N}$. 特别地，**任何$\mathcal A$-不可分子空间直和分解的初等因子组都相等**（称为$\mathcal A$的初等因子组）

# 矩阵相似的判定
## 有共同的初等因子组
设$A\in \mathrm{M}_n(\mathbb{C})$，在不计Jordan块出现的顺序的前提下，$A$的Jordan标准型由A的初等因子组唯一确定

设$A,B\in \mathrm{M}_n(F)$，则$A\sim_sB$当且仅当$A$和$B$有共同的初等因子组

## 相等多项式和秩
设$A,B\in \mathrm{M}_n(F)$，则$A\sim_sB$当且仅当下述两点同时成立
1. $\chi_A = \chi_B$或$\mu_A = \mu_B$
2. 设$p_1,\ldots,p_s$是$\chi_A$或$\mu_A$在$F[t]$中两两互素的（首一的）不可约因子，且
$$
\forall i \in \left\{ 0,1,\ldots,n+1\right\},j\in \left\{ 1,2,\ldots,s \right\},\quad \mathrm{rank}(p_j(A)^i) = \mathrm{rank}(p_j(B)^i) 
$$
## 任意多项式下秩相等
设$A,B\in \mathrm{M}_n(F)$，则$A\sim_sB$当且仅当对任意$f\in F[t],\;\mathrm{rank}(f(A)) = \mathrm{rank}(f(B))$

