# 不变子空间
## $\mathcal A$-不变子空间下的矩阵结构
设$\mathcal A \in \mathcal L(V)$，$U$是$\mathcal A$的$d$维不变子空间，$0 < d < n$. 则存在$V$的一组基使得$\mathcal A$在该基底下的矩阵为
$$
A = \begin{pmatrix}
B & C \\
O & D
\end{pmatrix}
$$
其中$B\in \mathrm{M}_d(F)$是$\mathcal A_U$的某个矩阵表示，这是因为当$\mathcal A$作用于$\boldsymbol e_1, \ldots ,\boldsymbol e_d$时得到的结果不能有关于$\boldsymbol e_{d+1}, \ldots ,\boldsymbol e_n$的坐标，所以坐标是$\begin{pmatrix}B \\ O\end{pmatrix}$

以及，可以看出这个矩阵的$k$次幂具有如下形式
$$
A^k = \begin{pmatrix}
B^k & * \\
O & D^k
\end{pmatrix}
$$
其中$*$是某个$d \times (n-d)$的矩阵，由此我们可以推广到对于任意$f\in F[t]$有
$$
f(A) = \begin{pmatrix}
f(B) & * \\
O & f(D)
\end{pmatrix}
$$
所以$\mu_{\mathcal A}(A) = O_{n\times n}$意味着
$$
\begin{pmatrix}
\mu_{\mathcal A}(B) & * \\
O & \mu_{\mathcal A}(D)
\end{pmatrix} = O_{n\times n}
$$
故而我们有$\mu_{\mathcal A}(B) = O_{d \times d},\; \mu_{\mathcal A}(D) = O_{(n-d)\times (n-d)}$，并且由[[Minimal Polynomial#整除判别法|整除判别法]]，$\mu_B \mid \mu_{\mathcal A}, \mu_D \mid \mu_{\mathcal A}$且$\mu_{\mathcal A_U} \mid \mu_\mathcal A$
## 常见的不变子空间的例子
设$\mathcal A\in \mathcal L(V)$满足$\mathcal A \mathcal B = \mathcal B \mathcal A$，则$\ker(\mathcal B), \mathrm{im}(\mathcal B)$是$\mathcal A$的不变子空间

特别地，因为$F[A]$是交换环，所以有
> [!Note]
> - 设$\mathcal A \in \mathcal{L}(V), f\in F[t]$. 则$\ker(f(\mathcal A))$和$\mathrm{im}(f(\mathcal A))$都是$\mathcal A$的不变子空间
> - 更特别地，$\ker(\mathcal A), \mathrm{im}(\mathcal A)$是$\mathcal A$的不变子空间

由$\mathcal A\in \mathcal{L}(V)$和$\boldsymbol v\in V$生成的[[Cyclic Subspace|循环子空间]]$F[\mathcal A]\cdot \boldsymbol v$是$\mathcal A$的不变子空间，且是包含$\boldsymbol v$的**最小**的$\mathcal A$-不变子空间

设$\lambda\in F$是$\mathcal A$的[[Eigenvectors and Characteristic Polynomial#特征值|特征值]]，则[[Eigenvectors and Characteristic Polynomial#特征子空间|特征子空间]]$V^\lambda$是$\mathcal A$的不变子空间
## 核核分解及极小多项式版
### 一般多项式版本
若$\mathcal A \in \mathrm{Hom}(V,V), \; f\in F[x]$且$f(\mathcal A) = \mathcal O$, 如果
$$
f = p_1\cdots p_m
$$
其中$p_1, \ldots, p_m \in F[x]$两两互素，则
$$
V = K_1 \oplus \cdots \oplus K_m
$$
其中$K_i = \ker(p_i(\mathcal A))$

### 极小多项式版本
设$\mathcal A \in \mathcal{L}(V), \; \mu_\mathcal A = p_1^{m_1} \cdots P_s^{m_s}$, 其中$p_1, \ldots, p_s \in F[t]\backslash F$不可约且两两互素，$m_1, \ldots, m_s \in \mathbb{Z}^+$，令
$$
K_i = \ker(P_i^{m_i}(\mathcal A))
$$
则
$$
V = K_1 \oplus \cdots \oplus K_s
$$
且$\mathcal A|_{K_i}$的极小多项式是$p_i^{m_i}$

这就是说，对$\mu_{\mathcal A}$的不可约因子分解可以看作是对空间的一个划分，其中每一个空间都是某个因子作用于$\mathcal A$后的核空间
# 特征值和特征向量
## 特征多项式
设$A \in \mathrm{M}_n(F), t$是$F$上的未定元，则多项式
$$
\det(tE-A) \in F[t]
$$
称为$A$的*特征多项式*，记为$\chi_A(t)$

特征多项式满足$\chi_A(A) = 0$，进而由[[Minimal Polynomial#整除判别法|整除判别法]]，$\mu_A \mid \chi_A$
## 特征子空间
设$\lambda \in F$是$\mathcal A$的特征值，令
$$
V^\lambda = \left\{ \boldsymbol x \in V \mid \mathcal A(\boldsymbol x) = \lambda \boldsymbol x \right\} 
$$
称为$\mathcal A$关于$\lambda$的*特征子空间*，可以验证$V^\lambda$是$\mathcal A$的[[Invariant Subspace|不变子空间]]

由定义，特征子空间可以写成
$$
V^\lambda = \ker(\lambda E-A)
$$

以下三个结论等价
1. $\mathcal A$是[[Diagonalization|可对角化]]的
2. $V = V^{\lambda_1} + \cdots+V^{\lambda_k}$
3. $V^{\lambda_1} + \cdots+V^{\lambda_k}$是直和
## 几何重数和代数重数
我们把$\dim V^\lambda$称为$\lambda$的*几何重数*，而把$\lambda$在$\chi_A(t)$中的[[Gauss's Lemma and Eisenstein's Irreducibility Criterion#重数|重数]]称为$\lambda$的*代数重数*

$\lambda$的代数重数总是大于等于它的几何重数
## 对角化条件和方法
### 判别法
1. $n$个特征向量线性无关（充要）
2. $n$个不同的特征根（充分不必要）
3. $V$是特征子空间的和（充要）
4. $\dim{V}$是特征子空间的维数和（充要）
5. 几何重数等于代数重数（充要）
6. 极小多项式可以分解为两两互素的一次因子之积（充要）
### 方法
如果$\mathcal A$可对角化，那么在对$V$作直和分解$V=V^{\lambda_1}\oplus\cdots\oplus V^{\lambda_k}$后得到的一组基下有$\mathcal A$的矩阵是
$$
\begin{pmatrix}
\lambda_1E  & O & \cdots & O \\
O & \lambda_2E & \cdots & O \\
\vdots & \vdots & \ddots & \vdots \\
O & O & \cdots & \lambda_kE
\end{pmatrix}
$$
这对应了这样的对角化形式
$$
\Lambda =\mathrm{diag}(\underbrace{\lambda_1,\ldots,\lambda_1}_{d_1\text{ times}},\underbrace{\lambda_2,\ldots,\lambda_2}_{d_2\text{ times}},\cdots,\underbrace{\lambda_k,\ldots,\lambda_k}_{d_k\text{ times}})
$$
其中$d_i = \dim V^{\lambda_i}$，如果要把$A$写成对角形式我们有变换
$$
A = P^{-1}\Lambda P
$$
若设$\boldsymbol e_1, \ldots,\boldsymbol e_n$是上述直和分解从左往右对应的一组基底，则由[[Linear Operator#矩阵相似|矩阵的基底变换]]可知有
$$
P = (\boldsymbol e_1, \boldsymbol e_2, \ldots, \boldsymbol e_n)
$$
## 性质
如果$\mathcal A$是[[Diagonalization|可对角化]]的，且拥有**不同的**特征值$\lambda_1,\ldots,\lambda_d$，那么$\mathcal A$的极小多项式就是
$$
\mu_\mathcal A = \prod_{i = 1}^d (t-\lambda_i)
$$
# 循环子空间
## 零化某个向量的极小多项式
设$\mathcal A \in \mathcal{L}(V), \boldsymbol v \in V, f(t) \in F[t]$. 如果$f(\mathcal A)(\boldsymbol v) = \boldsymbol 0$, 则称$f(t)$是*通过$\mathcal A$零化$\boldsymbol v$的多项式*. 

非零、次数最小的这样的多项式称为*通过$\mathcal A$零化$\boldsymbol v$的极小多项式*，记为$\mu_{\mathcal A, \boldsymbol v}$, 它通常是首一的. 

对任意$f\in F[t]$, 我们有$\mu_{\mathcal A,\boldsymbol v} = \mu_{\mathcal A,  f(\mathcal A)\boldsymbol v}\cdot \gcd(\mu_{\mathcal A,\boldsymbol v},f)$，利用这一点，当我们知道零化$\boldsymbol v$的极小多项式时，就可以很方便地求出零化$f(\mathcal A)\boldsymbol v$的极小多项式

类似于$\dim(F[\mathcal A]) = \deg(\mu_\mathcal A)$，我们有$\dim(F[\mathcal A]\cdot \boldsymbol v) = \deg(\mu_{\mathcal A, \boldsymbol v})$，其中$F[\mathcal A]\cdot \boldsymbol v$表示[[Cyclic Subspace|循环子空间]]

对$\forall \mathcal A \in \mathcal{L}(V)$，总存在$\boldsymbol v\in V$使得$\mu_{\mathcal A, \boldsymbol v} = \mu_\mathcal A$. 也就是说，总是存在这样一个$\boldsymbol v$使得$f(\mathcal A)(\boldsymbol v) = \boldsymbol 0\implies f(\mathcal A) = \mathcal O$ (要把它'杀死'就必须先把$\mathcal A$ '杀死'，称其为*同归于尽向量*)
## 循环子空间的定义
设$\mathcal A \in \mathcal{L}(V)$和$\boldsymbol v \in V$. 由$\boldsymbol v,\mathcal A(\boldsymbol v), \mathcal A^2(\boldsymbol v),\ldots$生成的子空间被称为由$\mathcal A$和$\boldsymbol v$生成的*循环子空间*. 记为$F[\mathcal A]\cdot \boldsymbol v$，或者表示成[[Invariant Subspace#线性轨道|线性轨道]]的形式$[\boldsymbol v]$

循环子空间包含了任意$\mathcal A$的多项式在$\boldsymbol v$上的作用，也就是说$F[\mathcal A]\cdot \boldsymbol v = \left\{ p(\mathcal A)(\boldsymbol v) \mid p(t)\in F[t]\right\}$

特别地，如果$\boldsymbol v$是$\mathcal A$的[[Eigenvectors and Characteristic Polynomial#特征向量|特征向量]]，则有$F[\mathcal A]\cdot \boldsymbol v =[\boldsymbol v]= \left< \boldsymbol v \right>$

设$\mathcal A \in \mathcal{L}(V),\; \boldsymbol v \in V$. 如果$V = F[\mathcal A]\cdot \boldsymbol v$，则称$\mathcal A$是$V$上的*循环算子*，$\boldsymbol v$是$V$中的*循环向量*，$V$是关于$\mathcal A, \boldsymbol v$的*循环空间*，简称 *$\mathcal A$-循环空间*

> [!Tip]
> 我们可以用任意的$\mathcal A\in \mathcal{L}(V), \boldsymbol v\in V$生成一个循环子空间，当我们选择一个合适的$\boldsymbol v$使得这个循环子空间就是$V$本身时，我们才能称$V$是$\mathcal A$-循环空间
## 循环子空间的性质
$V$是$\mathcal A$-循环的当且仅当$\mu_{\mathcal A} = \chi_{\mathcal A}$

 $F[\mathcal A]\cdot \boldsymbol v$是$\mathcal A$-[[Invariant Subspace|不变]]的，因为$F[\mathcal A]\cdot\boldsymbol v$自然包含了所有对$\mathcal A$的多项式作用的结果，它自然是$\mathcal A$封闭的
 
循环空间的所有不变子空间都是循环空间

循环子空间的维数和$\mathcal A$的零化$\boldsymbol v$的极小多项式的次数一致，即$\dim(F[\mathcal A]\cdot \boldsymbol v) =\deg \mu_{\mathcal A,\boldsymbol v}$

如果$V = F[\mathcal A]\cdot \boldsymbol v$是循环空间，则$\dim{(V)} = \deg{\mu_{\mathcal A, \boldsymbol v}}$，又$\deg{\mu_{\mathcal A}} \leq \deg{\chi_{\mathcal A}}= \dim{(V)}$且$\mu_{\mathcal A,\boldsymbol v} \mid \mu_{\mathcal A} \implies \deg{(\mu_{\mathcal A, \boldsymbol v}) \leq \deg{(\mu_{\mathcal A})}}$，故有$\dim(V) = \deg \mu_{\mathcal A,\boldsymbol v} =\deg \mu_\mathcal A$，且$\mu_{\mathcal A,\boldsymbol v} = \mu_{\mathcal A}$

反过来，若设$d = \deg \mu_\mathcal A$则存在$\boldsymbol v \in V$使得
$$
\dim (F[\mathcal A]\cdot \boldsymbol v) = d
$$
且不存在维数大于$d$的$\mathcal A$-循环子空间，也就是说，有$\mathcal A,\boldsymbol v$生成的循环子空间的最大维数就是$\mathcal A$的极小多项式的次数
# 空间分划
## 不可分子空间分解
### 判定规则
设$\mathcal A \in \mathcal{L}(V)$, $U$是$\mathcal A$-子空间，则$U$是$\mathcal A$-[[Invariant Subspace#单和半单|不可分]]的当且仅当下述两个条件都成立
1. $U$是$\mathcal A$-[[Cyclic Subspace|循环子空间]]
2. $\mu_{\mathcal A_U}$是$F[t]$中某个[[Unique Factorization Domain, UFD#不可约元|不可约多项式]]的幂次. 特别地，在$F= \mathbb{C}$也就是[[Complex Numbers|复数域]]上时，$\mu_{{\mathcal A}_U}$应当为某个一次多项式的幂次，及$\mu_{{\mathcal A}_U}(t) = (t-\lambda)^m$

> [!Tip]
> 由此可知，$\mathcal A$-不可分子空间一定是$\mathcal A$-循环的，不可分的条件比循环更强
### 不可分子空间直和分解
设$\mathcal A \in \mathcal{L}(V)$. 则存在$\mathcal A$-不可分子空间$W_1,\ldots,W_k$使得
$$
V = W_1\oplus\cdots\oplus W_k
$$
且$W_i$是$\mathcal A$-循环的，$\mu_{\mathcal A_{W_i}}$是$F[t]$中的某个不可约多项式的幂次，$i = 1, 2,\ldots,k$

同样地，如果$F = \mathbb{C}$，则$\mu_{\mathcal A_{W_i}}=(t-\lambda_i)^{d_i}$，其中$d_i= \dim{(W_i)}$，从而$\mathcal A_{W_i}$在$W_i$上的某一个矩阵表示是一个[[Jordan Canonical Form#Jordan块|Jordan块]]$J_{d_i}(\lambda)$
### 分解在多项式作用下的不变性
设$\mathcal A \in \mathcal{L}(V),\;f\in F[t]$，设$V$的$\mathcal A$-不可分子空间直和分解为
$$
V = U_1\oplus \cdots \oplus U_\ell
$$
则
$$
f(\mathcal A)(V) = f(\mathcal A)(U_1) \oplus \cdots \oplus f(\mathcal A)(U_\ell)
$$
# Jordan标准型
## Jordan块
设$\mathcal A \in \mathcal{L}(V)$. 则$V$是$\mathcal A$-[[Invariant Subspace#单和半单|不可分]]的当且仅当存在$\lambda\in \mathbb{C}$使得[[Minimal Polynomial|极小多项式]]$\mu_\mathcal A = (t-\lambda)^n$. 此时，$\mathcal A$在$V$的某组基下的矩阵是
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

事实上，满足$P^{-1}AP =  J_n(\lambda)$的那个转移矩阵$P$为
$$
P = (\boldsymbol \epsilon_1, \ldots,\boldsymbol \epsilon_n)
$$
其中$\boldsymbol\epsilon_j = (\mathcal A - \lambda\mathcal E)^{n-j}(\boldsymbol v)$，且$\boldsymbol v$满足$V =F[\mathcal A]\cdot \boldsymbol v$. 或者说$\boldsymbol v \in K_\lambda$是特征值$\lambda$对应的一个[[Generalized Eigenvectors and Eigenspaces|广义特征向量]]，而$\boldsymbol \epsilon_1, \ldots,\boldsymbol \epsilon_n$代表了$\boldsymbol v$的一个[[Generalized Eigenvectors and Eigenspaces#Basis of a Jordan block|广义特征向量循环]]

由[[Linear Operator#矩阵相似|矩阵的基底变换]]可知有$J_n(\lambda) = P^{-1}AP \implies A = P J_n(\lambda)P^{-1}$

*Jordan块*的基本性质如下
1. 如果$\lambda\neq 0$,则$\mathrm{rank}(J_n(\lambda)) = n$，而$\mathrm{rank}(J_n(0)) = n - 1$
2. $J_n(\lambda) = \lambda E_n + J_n(0)$
3. $J_n(\lambda)$的[[Minimal Polynomial|极小多项式]]和[[Characteristic Polynomial|特征多项式]]都等于$(t-\lambda)^n$，从而把$J_n(\lambda)$看成$\mathbb{C}^n$上的算子后，$\mathbb{C}^n$是$J_n(\lambda)$-[[Cyclic Subspace|循环]]的
4. $J_n(\lambda)$的唯一特征值为$\lambda$，从而对应的[[Eigenvectors and Characteristic Polynomial#特征子空间|特征子空间]]的维数为$1$，这是因为
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
6. $J_n^t(\lambda) = B^{-1}J_n(\lambda)B = BJ_n(\lambda)B^{-1}$，其中
$$
B = \begin{pmatrix}
0 & 0 & \cdots & 0 & 1 \\
0 & 0 & \cdots & 1 & 0 \\
\vdots & \vdots &\ddots &\vdots & \cdots \\
0 & 1 & \cdots & 0 & 0  \\
1 & 0 & \cdots & 0 & 0 
\end{pmatrix}
$$

## 低阶矩阵$J_A$的求法
### 一般方法
给定一个$F$上的[[Linear Space|线性空间]]$V$和一个定义在其上的[[Linear Operator|线性算子]]$\mathcal A\in \mathcal{L}(V)$，我们可以对$V$作[[Invariant Subspace#不可分子空间|不可分]]子空间[[Linear Space#子空间的直和|直和]]分解
$$
V = W_1 \oplus  \cdots \oplus  W_k
$$
其中每一个$W_i$都是$\mathcal A$-不可分子空间，这个性质等价于一下两条的联立：
1. $W_i$是$\mathcal A$-[[Cyclic Subspace|循环子空间]]
2. 设$\mathcal A_i=\mathcal A_{W_i}$为把$\mathcal A$的定义域限制在$W_i$上的新算子，则$\mathcal A_i$的[[Minimal Polynomial|极小多项式]]$\mu_i = \mu_{\mathcal A_i}$是$F[t]$中某个[[Unique Factorization Domain, UFD#不可约元|不可约多项式]]的幂次

我们称这里的每一个$\mu_i$为$\mathcal A$的一个*初等因子*，这些$\mu_i$是可以重复的，所以我们通过一个[[Elementary Divisors#重集|重集]]来将这些初等因子放在一起，称为$\mathcal A$关于上述不可分因子直和分解的[[Elementary Divisors#初等因子组|初等因子组]]，记为$\left\{ \mu_1, \ldots ,\mu_k \right\}$

考虑每一个初等因子$p^{m}$，其中$p$是$F[t]$中的一个不可约元，它们都对应着一个[[Jordan Canonical Form#Jordan块|Jordan块]]$J_m(\lambda)$，其中Jordan块的大小$m$就是$p$在该初等因子中的[[Gauss's Lemma and Eisenstein's Irreducibility Criterion#重数|重数]]，而$\lambda$则是$p(\lambda)=0$的解. 如果$\lambda$不唯一或者不存在，我们这样的$\mathcal A$的Jordan标准型就有可能不存在，具体细节不在此讨论

假设相同的初等因子$p^m$在初等因子组中出现了$n$次，在最后的[[Jordan Canonical Form#Jordan标准型的形式|Jordan标准型]]中$J_m(\lambda)$也就相应地出现了$n$次

把这些$J_n(\lambda)$在对角线上排列后（无所谓顺序）得到的大矩阵就是$\mathcal A$的Jordan标准型$J_A$，也就是
$$
J_A = \mathrm{diag}(J_{{n_1}}(\lambda_1), \ldots ,J_{n_k}(\lambda_k))
$$
所以要计算Jordan标准型，关键就是要确定这些初等因子，也就是
1. 有哪些可能的初等因子$p^m$
2. 每一种初等因子分别出现了几次

对第一个问题，我们只需要计算$\mathcal A$[[Matrix Representation of Linear Map|对应的矩阵表示]]$A$的[[Characteristic Polynomial|特征多项式]]，根据[[Cyclic Subspace#Hamilton-Cayley定理加强版|Hamilton-Cayley定理加强版]]，$A$的特征多项式和极小多项式具有相同的不可约因子，而由于$\mu_{\mathcal A_i} | \mu_{\mathcal A}$，所以$\mu_i = \mu_{\mathcal A_i}$的全部不可约因子都可以在$\chi_{A}$中找到，且$\chi _A$中的每一个不可约因子都是某个$\mu_i$的不可约因子

对于第二个问题，如果我们已经找到了所有可能的$p$，我们就可以利用一个递推公式来计算$p^m$在初等因子组中出现的次数

我们设从$\chi_A$找到的所有不可约因子为$p_1, \ldots ,p_s$，且设$\deg{p_i} = d_i$，那么$p_i^\ell$在初等因子组中出现的次数$N(i,\ell)$为
$$
N(i,\ell) = \dfrac{1}{d_i}\left( R(i,\ell -1)+R(i,\ell + 1)-2R(i,\ell) \right) 
$$
其中$R(i,j) = \mathrm{rank}(p_i^j(\mathcal A)),\; j \in \mathbb{N}$，这给出了计算Jordan标准型的一般方法

### 复数域的情况
我们来具体讨论复数域上的特例，因为$\mathbb{C}[t]$中的不可约因子都是一次的，所以这时候初等因子的形式为$\mu_i = (t-\lambda_i)^{m_i}$，其中$m_i = \dim{(W_i)}$，这是因为$W_i$是循环空间，所以$\mu_i$和$\mathcal A_i$的[[Characteristic Polynomial|特征多项式]]$\chi_i$相同，又$\chi_A$的次数等于$W_i$的维数，所以$\deg{(\mu_i)} = \dim{(W_i)}$

对于每一个特征根$\lambda_i$，$(t-\lambda_i)^\ell$出现的次数为
$$
N(i, \ell) = R(i,\ell-1) + R(i,\ell + 1) - 2R(i, \ell)
$$
其中$R(i,j) = \mathrm{rank}{((A-\lambda_iE)^j)}$. 
### 利用更多的信息
上面的计算对于高阶矩阵来说比较麻烦，所以我们考虑是否有其他的信息能帮助我们更方便地确定Jordan标准型的形式

我们可以直接从$\mathcal A$的矩阵表示求出$\chi_{\mathcal A}$，上面的标准算法中我们只利用了$\chi_A$的不可约因子，而没有利用它们对于的重数（也就是所谓的[[Eigenvectors and Characteristic Polynomial#维数和重数|代数重数]]），考虑所有初等因子的乘积
$$
p_\mu = \mu_1 \cdots \mu_n
$$
由于$W_i$都是循环的，所以$\deg{(\mu_i)} = \deg{(\chi_i)}= \dim{(W_i)}$，根据直和的性质，我们知道$\displaystyle\deg{(p_\mu)} = \sum_i \deg{(\mu_i)}= \sum_i\dim{(W_i)}=\dim{(V)} = \deg{(\chi_{\mathcal A})}$，而又由于$\mu_i \mid \mu_{\mathcal A} = \chi_{\mathcal A}$，所以$p_\mu \mid \chi_{\mathcal A}$，这两者又恰好维数相等，故而
$$
\chi_{\mathcal A} = \mu_1 \cdots \mu_n
$$
这说明了$\chi_{\mathcal A}$中每个不可约因子$(t-\lambda_i)$的重数就是每个$\lambda_i$的Jordan块的大小的和，也就是对应的$\lambda_i$在Jordan标准型的对角线上出现的次数

如果我们还知道极小多项式$\mu_{\mathcal A}$，我们就得到了每一个$p=t-\lambda$在$\mu_\mathcal A$中的重数，事实上，由于$\mu_i \mid \mu_{\mathcal A}$，故我们有
$$
\mu_\mathcal A = \mathrm{lcm}(\mu_1, \ldots ,\mu_n)
$$
从而如果某个$t-\lambda$在$\mu_{\mathcal A}$的重数$m$，那么必然存在一个初等因子$(t-\lambda)^m$

以上两个新增信息可以帮我们快速确定一些矩阵的Jodran标准型，例如

已知复方阵$A$的特征多项式和极小多项式分别为
$$
\begin{aligned}
\chi_A  & = (t-1)^4(t+1)^3t^2 \\
\mu_A  & = (t-1)^3(t+1)^3t^2
\end{aligned}
$$
对于特征值$1$，其代数重数为$4$，则知$1$在对角线上出现了$4$次；而由于$t-1$在$\mu_A$中的重数为$3$，则知存在一个$J_3(1)$，且这是最大的$1$的Jordan块

所以只能有一种情况，就是存在两个关于$1$的Jordan块$J_3(1),J_1(1)$

对于特征值$-1$和$0$，同理知道它们对应的Jordan块只能是$J_3(-1);J_2(0)$

综上
$$
A \sim \mathrm{diag}(J_1(1),J_3(1),J_3(-1),J_2(0))
$$
## 矩阵相似的判断
### 有共同的初等因子组
设$A\in \mathrm{M}_n(\mathbb{C})$，在不计Jordan块出现的顺序的前提下，$A$的Jordan标准型由A的初等因子组唯一确定

设$A,B\in \mathrm{M}_n(F)$，则$A\sim_sB$当且仅当$A$和$B$有共同的初等因子组

### 相等多项式和秩
设$A,B\in \mathrm{M}_n(F)$，则$A\sim_sB$当且仅当下述两点同时成立
1. $\chi_A = \chi_B$或$\mu_A = \mu_B$
2. 设$p_1,\ldots,p_s$是$\chi_A$或$\mu_A$在$F[t]$中两两互素的（首一的）不可约因子，且
$$
\forall i \in \left\{ 0,1,\ldots,n+1\right\},j\in \left\{ 1,2,\ldots,s \right\},\quad \mathrm{rank}(p_j(A)^i) = \mathrm{rank}(p_j(B)^i) 
$$
### 任意多项式下秩相等
设$A,B\in \mathrm{M}_n(F)$，则$A\sim_sB$当且仅当对任意$f\in F[t],\;\mathrm{rank}(f(A)) = \mathrm{rank}(f(B))$

# 欧式空间
## 向量代数和内积运算
### 内积
设$f(\boldsymbol x, \boldsymbol y)$是$V$上的[[Bilinear Form#对称双线性型|对称双线性型]]满足$f(\boldsymbol x,\boldsymbol x)$是[[Real Quadratic Forms#（半）正定二次型|正定]]的，则称$(V,f)$是一个*欧式空间*，$f$是$V$上的*内积*，记$f(\boldsymbol x,\boldsymbol y) = (\boldsymbol x\vert \boldsymbol y)$

内积的基本性质如下
- **双线性**：对任意的$\boldsymbol x, \boldsymbol y, \boldsymbol x \in V,\;\alpha,\beta \in \mathbb{R}$,
$$
(\alpha \boldsymbol x + \beta \boldsymbol y \vert \boldsymbol z) = \alpha(\boldsymbol x \vert \boldsymbol z) + \beta(\boldsymbol y \vert \boldsymbol z),\;(\boldsymbol x \vert \alpha \boldsymbol y + \beta \boldsymbol z) = \alpha(\boldsymbol x \vert \boldsymbol y) + \beta (\boldsymbol x \vert \boldsymbol z)
$$
- **对称性**：对任意$\boldsymbol x, \boldsymbol y \in V,\;(\boldsymbol x \vert \boldsymbol y) = (\boldsymbol y \vert \boldsymbol x)$
- **正定性**：对任意$\boldsymbol x \in V$
$$
(\boldsymbol x \vert \boldsymbol x) \geq 0 \text{ 且 } (\boldsymbol x \vert \boldsymbol x) = 0 \iff \boldsymbol x = \boldsymbol 0
$$
### 长度
设$V$是欧式空间，$\boldsymbol x \in V$. 称$\sqrt{ (\boldsymbol x \vert \boldsymbol x) }$是$\boldsymbol x$的*长度*，记为$\Vert \boldsymbol x \Vert$. 再设$\boldsymbol y \in V$. 则$\left\Vert \boldsymbol x - \boldsymbol y \right\Vert$称为$\boldsymbol x$到$\boldsymbol y$之间的*距离*

（Cauchy-Bunyakovsky不等式）设$\boldsymbol x,\boldsymbol y \in V$，则
$$
\left|(\boldsymbol x \vert \boldsymbol y)\right| \leq \Vert \boldsymbol x \Vert \Vert \boldsymbol y \Vert  
$$
特别地$\left|(\boldsymbol x \vert \boldsymbol y)\right| = \Vert \boldsymbol x \Vert \Vert \boldsymbol y \Vert$当且仅当$\boldsymbol x, \boldsymbol y$线性相关

在$\mathbb{R}^n$上，该不等式的形式是
$$
\left|x_1y_1+ \cdots +x_ny_n\right| \leq \sqrt{ x_1^{2}+ \cdots +x_n^{2} }\sqrt{ y_1^{2}+ \cdots +y_n^{2} }
$$
在$\mathrm{M}_n(\mathbb{R})$上，该不等式的形式是
$$
\left|\mathrm{tr}(A^tB)\right|\leq \sqrt{ \mathrm{tr}(A^tA) }\sqrt{ \mathrm{tr}(B^tB) }
$$

### 夹角和正交
设$\boldsymbol x, \boldsymbol y \in V \backslash \left\{ \boldsymbol 0 \right\}$，称
$$
\arccos \left( \dfrac{(\boldsymbol x \vert \boldsymbol y)}{\Vert \boldsymbol x \Vert \Vert \boldsymbol y \Vert } \right) 
$$
是$\boldsymbol x, \boldsymbol y$的*夹角*，其通常的取值范围为$[0,\pi]$

设$\boldsymbol x, \boldsymbol y \in V$. 如果$(\boldsymbol x \vert \boldsymbol y)=0$，则称$\boldsymbol x$和$\boldsymbol y$*正交*，记为$\boldsymbol x \perp \boldsymbol y$

设$\boldsymbol x, \boldsymbol x_1, \ldots ,\boldsymbol x_k \in V$,其中$\boldsymbol x_1 , \ldots , \boldsymbol x_k$非零，则
- $\boldsymbol x \perp \boldsymbol x \iff \boldsymbol x = \boldsymbol 0$
- 如果$\boldsymbol x_1, \ldots ,\boldsymbol x_k$两两正交，则它们线性无关

（勾股定理）设$\boldsymbol x, \boldsymbol y \in V$，则$\boldsymbol x \perp \boldsymbol y$当且仅当
$$
\Vert \boldsymbol x + \boldsymbol y \Vert ^{2} = \Vert \boldsymbol x \Vert ^{2} + \Vert \boldsymbol y \Vert ^{2}   
$$
## Gram-Schmidt正交化
### 正交化
设$\dim(V) = n,\; \boldsymbol e_1, \ldots ,\boldsymbol e_n$是$V$中两两正交的单位向量，则称它们为$V$的一组*单位正交基*

设$\boldsymbol v_1, \ldots ,\boldsymbol v_k\in V$线性无关，则存在两两正交的单位向量$\boldsymbol\epsilon_1, \ldots ,\boldsymbol\epsilon_k$使得
$$
\left< \boldsymbol v_1, \ldots ,\boldsymbol v_i \right> = \left< \boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_i \right>  
$$
其中$i = 1, 2, \ldots ,k$. 特别地，$V$有单位正交基

可以利用如下递推式构造$\boldsymbol \epsilon_i$,
$$
\boldsymbol \epsilon_i' = \boldsymbol v_i - (\boldsymbol v_i \vert \boldsymbol \epsilon_1)\boldsymbol \epsilon_1 - \cdots - (\boldsymbol v_i \vert \boldsymbol \epsilon_{i-1})\boldsymbol  \epsilon_{i - 1} \implies \boldsymbol \epsilon_i = \dfrac{\boldsymbol \epsilon_i'}{\Vert \boldsymbol \epsilon_i' \Vert }
$$
例如要求$U = \left< \boldsymbol u_1,\boldsymbol u_2,\boldsymbol u_3 \right>$是$\mathbb{R}^4$的子空间的一组正交单位基，其中
$$
\boldsymbol u_1 = \begin{pmatrix}
1 \\ 0 \\ 1 \\ 0
\end{pmatrix},\;\boldsymbol u_2 = \begin{pmatrix}
0 \\ -1 \\ 1 \\ -1
\end{pmatrix},\; \boldsymbol u_3 = \begin{pmatrix}
1 \\ 1 \\ 1 \\ 1
\end{pmatrix}
$$
则可由Gram-Schmidt正交化得
$$
\begin{gather}
\boldsymbol \epsilon_1 = \dfrac{{\boldsymbol u_1}}{\Vert \boldsymbol u_1 \Vert } = \dfrac{1}{\sqrt{ 2 }} \boldsymbol u_1 \\
\boldsymbol \epsilon_2' = \boldsymbol u_2 - (\boldsymbol u_2 \vert \boldsymbol \epsilon_1)\boldsymbol \epsilon_1 = \begin{pmatrix}
-\frac{1}{2} \\ -1\\ \frac{1}{2} \\ -1
\end{pmatrix} \\
\boldsymbol \epsilon_2 = \dfrac{\boldsymbol \epsilon_2'}{\Vert \boldsymbol \epsilon_2' \Vert } = \dfrac{1}{\sqrt{ 10 }} \begin{pmatrix}
-1 \\ -2 \\ 1 \\ -2
\end{pmatrix} \\
\boldsymbol \epsilon_3' = \boldsymbol u_3 - (\boldsymbol u_3 \vert \boldsymbol \epsilon_1) \boldsymbol \epsilon_1 -(\boldsymbol u_3 \vert \boldsymbol \epsilon_2)\boldsymbol \epsilon_2 = \dfrac{1}{5} \begin{pmatrix}
-2 \\ 1 \\ 2 \\ 1
\end{pmatrix} \\
\boldsymbol \epsilon_3 = \dfrac{\boldsymbol \epsilon_3'}{\Vert  \boldsymbol\epsilon_3' \Vert } = \dfrac{1}{\sqrt{ 10 }} \begin{pmatrix}
-2 \\ 1 \\ 2 \\ 1
\end{pmatrix}
\end{gather}
$$
### 正交基的性质
### 内积的形式
设$V$的一组单位正交基是$\boldsymbol e_1, \ldots ,\boldsymbol e_n,\;\boldsymbol x, \boldsymbol y\in V$在这组基下的坐标分别是$(x_1, \ldots ,x_n)^t$和$(y_1, \ldots ,y_n)^t$，则有
$$
(\boldsymbol x \vert \boldsymbol y) = x_1y_1+ \cdots +x_ny_n
$$
### 内积取坐标分量
设$V$的一组单位正交基是$\boldsymbol e_1, \ldots ,\boldsymbol e_n,\;\boldsymbol x \in V$. 则$\boldsymbol x$在该基下的第$i$个坐标分量为$(\boldsymbol x \vert \boldsymbol e_i)$，$i = 1,2, \ldots ,n$

### 维数相等的欧式空间线性同构且保持内积不变
设$V,W$是两个$n$-维欧式空间，其中的内积分别记为$(\vert)_V$和$(\vert)_W$，则存在[[Linear Isomorphism|线性同构]]$\phi:V \to W$满足对任意$\boldsymbol x, \boldsymbol y\in V$
$$
(\boldsymbol x \vert \boldsymbol y)_V = (\phi(\boldsymbol x) \vert \phi(\boldsymbol y))_W
$$

## 正交投影和正交补
设$\boldsymbol v\in V \backslash \left\{ \boldsymbol 0 \right\},\;\boldsymbol x\in V$,称
$$
\left( \boldsymbol x \vert \dfrac{\boldsymbol v}{\Vert \boldsymbol v \Vert } \right) \dfrac{\boldsymbol v}{\Vert \boldsymbol v \Vert }
$$
为$\boldsymbol x$在$\boldsymbol v$上的*投影*

设$\boldsymbol v\in V \backslash \left\{ \boldsymbol 0 \right\},\;\boldsymbol x\in V$，$\boldsymbol y$是$\boldsymbol x$在$\boldsymbol v$上的投影，则$(\boldsymbol v - \boldsymbol y)\perp \boldsymbol y$

设$X,Y \subset V$. 如果对任意的$\boldsymbol x\in X$和$\boldsymbol y\in Y$都有$\boldsymbol x \perp \boldsymbol y$，则称$X$和$Y$*正交*，记为$X \perp Y$. 特别地，当$X = \left\{ \boldsymbol x \right\}$时，则$X \perp Y$也记为$\boldsymbol x \perp Y$

设$U \subset V$是[[Linear Space#子空间|子空间]]，$\boldsymbol x\in V$，则存在唯一的$\boldsymbol u\in U$使得$(\boldsymbol x - \boldsymbol u)\perp U$，称这里的$\boldsymbol u$是$\boldsymbol x$在子空间$U$上的*正交投影*. 特别地，向量$\boldsymbol x$在$\boldsymbol v\in V \backslash \left\{ \boldsymbol 0 \right\}$上的投影就是$\boldsymbol x$在$\left< \boldsymbol v \right>$上的正交投影

我们记$\boldsymbol x$在子空间$U$上的正交投影为$\pi_U(\boldsymbol x)$

在上面的例子中$\boldsymbol u = \pi_U(\boldsymbol x)$，此时考虑$\forall \boldsymbol y\in U$，容易证明$\Vert \boldsymbol x - \boldsymbol u \Vert \leq \Vert \boldsymbol x - \boldsymbol y \Vert$，故我们称$\Vert \boldsymbol x - \pi_U(\boldsymbol x) \Vert$成为$\boldsymbol x$到$W$的*距离*，记为$d(\boldsymbol x, W)$

设$U \subset V$是子空间，令$U^{\perp} \coloneqq \left\{ \boldsymbol x \in V \mid \boldsymbol x\perp U \right\}$，则
1. $U^{\perp}$是子空间且$U \perp U^{\perp}$
2. $V = U \oplus U^{\perp}$，故称$U^{\perp}$是$U$的*正交补*
3. $\left( U^{\perp} \right)^{\perp} = U$，这是$(2)$的直接推论

由第$(2)$点我们知道，设$\boldsymbol e_1, \ldots ,\boldsymbol e_d$是$V$中的单位正交向量，则$\boldsymbol e_1, \ldots ,\boldsymbol e_d$可以扩充为$V$的一组单位正交基，比如说，设标准欧式空间$\mathbb{R}^3$的标准基为$\boldsymbol e_1,\boldsymbol e_2,\boldsymbol e_3$，则有
$$
\left< \boldsymbol e_1 \right>^{\perp} = \left< \boldsymbol e_2,\boldsymbol e_3 \right> ,\quad \left< \boldsymbol e_1 \right> ^{\perp\perp} = \left< \boldsymbol e_2,\boldsymbol e_3 \right> ^{\perp} = \left< \boldsymbol e_1 \right> 
$$
# 正规算子
## 正交矩阵
设$P\in \mathrm{GL}_n(\mathbb{R})$. 如果$P^t = P^{-1}$，则称$P$是*正交矩阵*. 所有$n$阶正交矩阵的集合记为$\mathrm{O}_n(\mathbb{R})$

集合$\mathrm{O}_n(\mathbb{R})$是$\mathrm{GL}_n(\mathbb{R})$的[[Group#Subgroup|子群]]

正交矩阵有如下性质
- 如果$P\in \mathrm{{O}}_n(\mathbb{R})$，则$\det (P) = \pm1$，这说明了正交矩阵是一个**旋转矩阵**
- $P\in \mathrm{O}_n(\mathbb{R})$当且仅当$P$的列向量是标准欧式空间$\mathbb{R}^n$中的一组单位正交基
- $P\in \mathrm{O}_n(\mathbb{R})$当且仅当$P$的行向量是标准欧式空间$\mathbb{R}^{1\times n}$中的一组单位正交基

特别地，$P\in \mathrm{O}_2(\mathbb{R})$当且仅当存在$\theta$使得
$$
P = \begin{pmatrix}
\cos \theta & -\sin \theta \\
\sin \theta  &  \cos \theta
\end{pmatrix}
\text{ or }
P = \begin{pmatrix}
\cos \theta & \sin \theta \\
\sin \theta  & -\cos \theta
\end{pmatrix}
$$
设欧式空间$V$由基$\boldsymbol e_1, \ldots , \boldsymbol e_n$和$\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n$，矩阵$P\in \mathrm{GL}_n(\mathbb{R})$满足
$$
(\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n) = (\boldsymbol e_1, \ldots ,\boldsymbol e_n)P
$$
再设$\boldsymbol e_1, \ldots ,\boldsymbol e_n$是单位正交基，则$\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n$是单位正交基当且仅当$P\in \mathrm{O}_n(\mathbb{R})$
## 正交等价
设$A,B\in \mathrm{M}_n(\mathbb{R})$. 如果存在$P\in \mathrm{O}_n(\mathbb{R})$使得$B = P^{-1}AP$，则称$A$与$B$*正交等价*（或*正交相似*），记为$A\sim_o B$

可以验证，$\sim_o$是[[Equivalence Relation|等价关系]]. 且若$A\sim_oB$，则由$A\sim _s B$且$A\sim_c B$，这是因为正交矩阵的逆和转置相等. 由此可得，矩阵的[[Linear Operator#矩阵相似|相似不变量]]和[[Bilinear Form#合同关系的不变量|合同不变量]]都是正交等价的不变量. 但是反之不然，不能用合同等价及相似等价同时成立推出正交等价

在正交等价下，可以同时用$B = P^{-1}AP$和$B = P^tAP$来表示基底变换
## 正交标准型

# 必考题
## 给定具体的矩阵，计算特征多项式，特征值和特征子空间，并判断是否可以对角化

## Hamilton-Cayley定理

## 确定低阶矩阵的Jordan标准型

## Gram-Schmidt正交化，正交补的构造

## 计算正交标准型