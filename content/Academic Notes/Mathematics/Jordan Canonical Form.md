# $\mathbb{C}$上的Jordan标准型
## Jordan块
设$\mathcal A \in \mathcal{L}(V)$. 则$V$是$\mathcal A$-[[Invariant Subspace#单和半单|不可分]]的当且仅当存在$\lambda\in \mathbb{C}$使得[[Minimal Polynomial|极小多项式]]$\mu_\mathcal A = (t-\lambda)^n$. 此时, $\mathcal A$在$V$的某组基下的矩阵是
$$
J_n(\lambda) = 
\begin{pmatrix}
\lambda & 1 & 0 & \cdots & 0 & 0 \\
0 & \lambda & 1 & \cdots & 0 & 0 \\
0 & 0 & \lambda & \cdots & 0 & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & 0 & \cdots & \lambda & 1 \\
0 & 0 & 0 & \cdots & 0 & \lambda
\end{pmatrix}
$$

我们称此矩阵为关于$\lambda$的$n$阶*Jordan块*

### 变换为Jordan块的矩阵 
事实上, 满足$P^{-1}AP =  J_n(\lambda)$的那个转移矩阵$P$为
$$
P = (\boldsymbol \epsilon_1, \ldots,\boldsymbol \epsilon_n)
$$
其中$\boldsymbol\epsilon_j = (\mathcal A - \lambda\mathcal E)^{n-j}(\boldsymbol v)$, 且$\boldsymbol v$满足$V =F[\mathcal A]\cdot \boldsymbol v$. 或者说$\boldsymbol v \in K_\lambda$是特征值$\lambda$对应的一个[[Generalized Eigenvectors and Eigenspaces|广义特征向量]], 而$\boldsymbol \epsilon_1, \ldots,\boldsymbol \epsilon_n$代表了$\boldsymbol v$的一个[[Generalized Eigenvectors and Eigenspaces#Basis of a Jordan block|广义特征向量循环]]

由[[Linear Operator#矩阵相似|矩阵的基底变换]]可知有$J_n(\lambda) = P^{-1}AP \implies A = P J_n(\lambda)P^{-1}$

### Jordan块的基本性质
*Jordan块*的基本性质如下
1. 如果$\lambda\neq 0$,则$\mathrm{rank}(J_n(\lambda)) = n$, 而$\mathrm{rank}(J_n(0)) = n - 1$
2. $J_n(\lambda) = \lambda E_n + J_n(0)$
3. $J_n(\lambda)$的[[Minimal Polynomial|极小多项式]]和[[Characteristic Polynomial|特征多项式]]都等于$(t-\lambda)^n$, 从而把$J_n(\lambda)$看成$\mathbb{C}^n$上的算子后, $\mathbb{C}^n$是$J_n(\lambda)$-[[Cyclic Subspace|循环]]的
4. $J_n(\lambda)$的唯一特征值为$\lambda$, 从而对应的[[Eigenvectors and Characteristic Polynomial#特征子空间|特征子空间]]的维数为$1$, 这是因为
$$
J_n(\lambda)-\lambda E_n = J_n(0)
$$
于是
$$
\begin{aligned}
J_n(\lambda) \boldsymbol v  & = \lambda \boldsymbol v \implies J_n(0)\boldsymbol v = 0  \\
\implies \dim V^{\lambda}  & = \dim \ker J_n(0) = n-(n-1) = 1
\end{aligned}
$$
5. $J_n(\lambda)$可[[Diagonalization|对角化]]当且仅当$n = 1$
6. $J_n^t(\lambda) = B^{-1}J_n(\lambda)B = BJ_n(\lambda)B^{-1}$, 其中
$$
B = \begin{pmatrix}
0 & 0 & \cdots & 0 & 1 \\
0 & 0 & \cdots & 1 & 0 \\
\vdots & \vdots &\ddots &\vdots & \cdots \\
0 & 1 & \cdots & 0 & 0  \\
1 & 0 & \cdots & 0 & 0 
\end{pmatrix}
$$

### Jordan块的幂
Jordan块可以写成如下形式
$$
J = \lambda E + N
$$
其中
$$
N = 
\begin{pmatrix}
0 & 1 & 0 & \cdots & 0 & 0 \\
0 & 0 & 1 & \cdots & 0 & 0 \\
0 & 0 & 0 & \cdots & 0 & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & 0 & \cdots & 0 & 1 \\
0 & 0 & 0 & \cdots & 0 & 0
\end{pmatrix}
$$
由$\lambda E$和$N$的可交换性以及二项式定理可以给出
$$
J_k(\lambda)^n = (\lambda E+N)^n = \sum_{r=0}^n\binom{n}{r} \lambda^{n-r}N^{r} = \sum_{r = 0}^{\min(n,k-1)} \binom{n}{r} \lambda^{n-r}N^{r}
$$
也就是
$$
J_k(\lambda)^n=\begin{pmatrix}\lambda^n&\binom n1\lambda^{n-1}&\binom n2\lambda^{n-2}&\cdots&\cdots&\binom n{k-1}\lambda^{n-k+1}\\&\lambda^n&\binom n1\lambda^{n-1}&\cdots&\cdots&\binom n{k-2}\lambda^{n-k+2}\\&&\ddots&\ddots&\ddots&\vdots\\&&&\ddots&\ddots&\vdots\\&&&&\lambda^n&\binom n1\lambda^{n-1}\\&&&&&\lambda^n\end{pmatrix}
$$


## Jordan标准型的形式
设$\mathcal A \in \mathcal{L}(V)$. 则$\mathcal A$在$V$的某组基下的矩阵是
$$
\begin{pmatrix}
J_{d_1}(\lambda_1)  & O & \cdots & O \\
O & J_{d_2}(\lambda_2)  & \cdots & O \\
\vdots & \vdots & \ddots & \vdots \\
O & O & \cdots & J_{d_k}(\lambda_k)
\end{pmatrix}
$$
其中$d_1,\ldots,d_k \in \mathbb{N}^*,\;\lambda_1,\ldots,\lambda_k \in \mathbb{C}$, 都**不必两两不同**

这是因为总可以作[[Cyclic Subspace#循环子空间分解|循环子空间分解]]使得
$$
V = W_1\oplus \cdots \oplus W_k
$$
其中$W_i$是$\mathcal A$-循环且$\mathcal A$-不可分的, 由[[Cyclic Subspace#不可分子空间的判定准则|不可分子空间的性质]]得到$\mu_{W_i}$一定是$\mathbb{C}[t]$的重某个不可约多项式的幂次, 而由代数基本定理$\mathbb{C}[t]$中的不可约多项式总是一次的, 故可设$\mu_{W_i} = (t-\lambda_i)^{d_i}$, 因为对于循环空间$\deg \mu_{W_i} = \deg{\chi_{W_i}} = d_i$. 所以由Jordan块的定义就可知$\mathcal A_{W_i}$在$W_i$的某组基下的矩阵是$J_{d_i}(\lambda_i)$

我们称上面的矩阵为$\mathcal A$的一个*Jordan标准型*, 其基本性质如下
1. $\mathrm{rank}(J_A) = \sum_{i = 1}^k \mathrm{rank}(J_{d_i}(\lambda_i))$
2. $J_A$的（也是$A$的）极小多项式为
$$
\mathrm{lcm}((t-\lambda_1)^{d_1},\ldots,(t-\lambda_k)^{d_k})
$$
特征多项式为
$$
(t-\lambda_1)^{d_1}\cdots(t-\lambda_k)^{d_k}
$$
3. 设$\lambda \in \mathrm{spec}_\mathbb{C} (\mathcal A)$, 则$J_A$中至少有一个关于$\lambda$的Jordan块
4. $\lambda$的[[Eigenvectors and Characteristic Polynomial#维数和重数|代数重数]]等于$\lambda$在$J_A$主对角线上出现的次数；$\lambda$的[[Eigenvectors and Characteristic Polynomial#维数和重数|几何重数]]等于关于$\lambda$的Jordan块在$J_A$中出现的次数
5. $\lambda$在极小多项式中的[[Gauss's Lemma and Eisenstein's Irreducibility Criterion#重数|重数]]等于$J_A$中关于$\lambda$的Jordan块出现的最大阶数
6. $A$可对角化当且仅当$d_1 = \cdots = d_k = 1$

### 例子
#### 例1
设$\alpha\in \mathbb{C}$,
$$
A =\begin{pmatrix}
\alpha  & 0 & 0 \\
0 & \alpha & 0 \\
\alpha & 0 & \alpha
\end{pmatrix}
$$
则可以直接计算$\chi_A = (t-\alpha)^3$, 故特征值为$\alpha$, 代数重数为$3$, 而且
$$
\mathrm{rank}(A-\alpha E) = \mathrm{rank} \begin{pmatrix}
0 & 0 & 0    \\
0 & 0 & 0   \\
\alpha & 0 & 0 
\end{pmatrix}
$$
当$\alpha \neq 0$时, $\dim(V^\alpha) = 3-\mathrm{rank}(A-\alpha E) = 2$, 故$\alpha$几何重数为$2$
于是由上面的性质$(4)$就有
$$
A \sim J_A = \begin{pmatrix}
J_2(\alpha)  & O \\
O & J_1(\alpha)
\end{pmatrix} = \begin{pmatrix}
\alpha  & 1 & 0 \\
0 & \alpha & 0 \\
0 & 0 & \alpha
\end{pmatrix}
$$
当$\alpha = 0$时, $\dim(V^\alpha) = 3 - 0 = 3$, 几何重数为$3$, 故而
$$
A \sim \begin{pmatrix}
J_1(\alpha)  & 0 & 0 \\
0 & J_1(\alpha) & 0 \\
0 & 0 & J_1(\alpha)
\end{pmatrix} = O_{3\times3}
$$

#### 例2
已知复方阵$A$的特征多项式和极小多项式分别为
$$
\begin{aligned}
\chi_A  & = (t-1)^4(t+1)^3t^2 \\
\mu_A  & = (t-1)^3(t+1)^3t^2
\end{aligned}
$$
对于特征值$1$, 其代数重数为$4$, 由性质$(4)$知$1$在对角线上出现了$4$次；而由于$t-1$在$\mu_A$中的重数为$3$, 由性质$(5)$知存在一个$J_3(1)$, 且这是最大的$1$的Jordan块. 
所以只能有一种情况, 就是存在两个关于$1$的Jordan块$J_3(1),J_1(1)$, 特征值$1$的几何重数为$2$

对于特征值$-1$和$0$, 同理知道它们对应的Jordan块只能是$J_3(-1);J_2(0)$

综上
$$
A \sim \mathrm{diag}(J_1(1),J_3(1),J_3(-1),J_2(0))
$$

