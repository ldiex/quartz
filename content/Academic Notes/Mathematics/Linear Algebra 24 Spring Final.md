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
# 正交和正规
## 正交矩阵
设$P\in \mathrm{GL}_n(\mathbb{R})$. 如果$P^t = P^{-1}$，则称$P$是*正交矩阵*. 所有$n$阶正交矩阵的集合记为$\mathrm{O}_n(\mathbb{R})$

集合$\mathrm{O}_n(\mathbb{R})$是$\mathrm{GL}_n(\mathbb{R})$的[[Group#Subgroup|子群]]

正交矩阵有如下性质
- 如果$P\in \mathrm{{O}}_n(\mathbb{R})$，则$\det (P) = \pm1$，这说明了正交矩阵是一个**旋转矩阵**或者是一个**反射矩阵**
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
前面这种行列式为$1$，代表旋转；后面这种行列式为$-1$，代表反射

设欧式空间$V$由基$\boldsymbol e_1, \ldots , \boldsymbol e_n$和$\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n$，矩阵$P\in \mathrm{GL}_n(\mathbb{R})$满足
$$
(\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n) = (\boldsymbol e_1, \ldots ,\boldsymbol e_n)P
$$
再设$\boldsymbol e_1, \ldots ,\boldsymbol e_n$是单位正交基，则$\boldsymbol \epsilon_1, \ldots ,\boldsymbol \epsilon_n$是单位正交基当且仅当$P\in \mathrm{O}_n(\mathbb{R})$
## 正交等价
设$A,B\in \mathrm{M}_n(\mathbb{R})$. 如果存在$P\in \mathrm{O}_n(\mathbb{R})$使得$B = P^{-1}AP$，则称$A$与$B$*正交等价*（或*正交相似*），记为$A\sim_o B$

可以验证，$\sim_o$是[[Equivalence Relation|等价关系]]. 且若$A\sim_oB$，则由$A\sim _s B$且$A\sim_c B$，这是因为正交矩阵的逆和转置相等. 由此可得，矩阵的[[Linear Operator#矩阵相似|相似不变量]]和[[Bilinear Form#合同关系的不变量|合同不变量]]都是正交等价的不变量. 但是反之不然，不能用合同等价及相似等价同时成立推出正交等价

在正交等价下，可以同时用$B = P^{-1}AP$和$B = P^tAP$来表示基底变换
## 伴随算子
设$\mathcal A\in \mathcal{L}(V)$，如果算子$\mathcal B\in \mathcal{L} (V)$满足对任意$\boldsymbol x, y\in V$都有$(\mathcal A(\boldsymbol x) \vert \boldsymbol y) = (\boldsymbol x \vert \mathcal B(\boldsymbol y))$，则称$\mathcal B$是$\mathcal A$的*伴随算子（Adjoint Operator）*

设$\mathcal A\in \mathcal{L}(V)$，则$\mathcal A$的伴随算子存在且唯一. 如果$\mathcal A$在$V$的[[Euclidean Space#单位正交基|单位正交基]]$\boldsymbol e_1, \ldots ,\boldsymbol e_n$下的矩阵等于$A$，则其伴随算子在该基下的矩阵等于$A^t$

我们把$\mathcal A$的伴随算子记为$\mathcal A^*$
## 正规算子
> [!Tip]
> 我们只在$V = \mathbb{R}^n$时讨论正规算子

设$\mathcal A\in \mathcal{L} (V)$，如果$\mathcal A \mathcal A^* = \mathcal A^* \mathcal A$，则称$\mathcal A$是*正规算子（Normal Operator）*，类似地，设$A\in \mathrm{M}_n(\mathbb{R})$，如果$AA^t = A^tA$，则称$A$是*正规矩阵（Normal Matrix）*

特别地，若$\mathcal A \mathcal A^* = \mathcal E$，则称$\mathcal A$是*正交算子（Orthogonal Operator）*

由定义，设$\mathcal A\in \mathcal{L} (V)$，$\mathcal A$在$V$的单位正交基$\boldsymbol e_1, \ldots ,\boldsymbol e_n$下的矩阵为$A$，则$\mathcal A$正规当且仅当$A$正规

设$\mathcal A\in \mathcal{L}(V)$，如果$\mathcal A^* = \mathcal A$，则称$\mathcal A$是*对称算子（Symmetric Operator）*，如果$\mathcal A^* = - \mathcal A$，则称$\mathcal A$是*斜对称算子（Skew-symmetrix Operator）* . 由此可知，对称和斜对称算子都是正规算子，对称和斜对称矩阵都是正规矩阵

> [!Tip]
> [[Euclidean Space#正交矩阵|正交矩阵]]是正规矩阵，这是因为设$P\in \mathrm{O}_n(\mathbb{R})$，则有$P^tP = E = PP^t$
## 正规算子的保内性
设$\mathcal A\in \mathcal{L}(V)$，如果对于任意$\boldsymbol x,\boldsymbol y\in V$
$$
(\boldsymbol x \vert \boldsymbol y) = \left( \mathcal A(\boldsymbol x)  \vert \mathcal A(\boldsymbol y)\right) 
$$
则称$\mathcal A$是*保内(积)的（preserve the inner product）*

若$\mathcal A$在$V$的单位正交基$\boldsymbol e_1, \ldots ,\boldsymbol e_n$下的矩阵为$A$，则下列断言等价
1. $\mathcal A$保内
2. $A\in \mathrm{O}_n(\mathbb{R})$
3. 对任意$\boldsymbol x\in V,\; \Vert \boldsymbol x \Vert = \Vert \mathcal A(\boldsymbol x) \Vert$ （保长）
4. 对任意$\boldsymbol x, \boldsymbol y\in V,\; \Vert \boldsymbol x - \boldsymbol y \Vert = \Vert \mathcal A(\boldsymbol x) - \mathcal A(\boldsymbol y)\Vert$（保距离）
上述等价命题说明了正交矩阵的“旋转”性质，且*保内算子*是正规算子，也称为正交（保长，保距）算子，因为正交算子一定是正规算子

# 正交标准型
## 正规矩阵的标准型
设$\dim (V) = 1$，则任意的$\mathcal A\in \mathcal{L}(V)$都是[[Normal Operator and Normal Matrix#正规算子|正规算子]]，这是因为对$V$中的单位向量$\boldsymbol v$，$\mathcal A(\boldsymbol v) = \lambda \boldsymbol v$，其中$\lambda$是某个实数

设$\dim{(V)}=2,\;\mathcal A\in \mathcal{L}(V)$正规，且$V$是$\mathcal A$-不可分的（在可分的情形下$A$可以通过一维形式的直和得到），则$\mathcal A$在$V$的任意[[Euclidean Space#单位正交基|单位正交基]]下的矩阵式
$$
A = \begin{pmatrix}
\alpha  &  - \beta \\
\beta  &  \alpha
\end{pmatrix}
$$
其中$\alpha,\beta\in \mathbb{R}$且$\beta \neq 0$

设$\mathcal A\in \mathcal{L}(V)$正规，则存在$V$的一组单位正交基$\boldsymbol e_1, \ldots ,\boldsymbol e_n$和$\alpha_1,\beta_1, \ldots , \alpha_s,\beta_s,\;\lambda_{2s+1},\lambda_n\in \mathbb{R}$，其中$\beta_1, \ldots ,\beta_s \neq 0$，使得$\mathcal A$在这组基下的矩阵等于
$$
B=\begin{pmatrix}
N(\alpha_1,\beta_1) & & & & &\\
& \ddots & & & &\\
& & N(\alpha_s,\beta_s) & & & \\
& & & \lambda_{2s+1} & & \\
& & & & \ddots & \\
& & & & & \lambda_n
\end{pmatrix}
$$
其中
$$
N(\alpha,\beta) = \begin{pmatrix}
\alpha & -\beta \\
\beta & \alpha
\end{pmatrix}
$$
也就是说，存在如上这样一个标准型$B$使得$A$[[Euclidean Space#正交等价|正交等价]]于$B$，即$A \sim_o B$，弱化这个结论就是有$A$[[Linear Operator#矩阵相似|相似]]于$B$，即$A \sim_s B$
## 实对称矩阵的标准型
求解该对角矩阵的算法
1. 计算$\mathcal A$的特征根，设互不相同的特征根是$\lambda_1, \ldots ,\lambda_k$
2. 对$i\in \left\{ 1,2, \ldots ,k \right\}$，求$V^{\lambda_i}$的一组基
3. 对$i\in \left\{ 1,2, \ldots ,k \right\}$，利用[[Euclidean Space#Gram-Schmidt正交化|Gram-Schmidt正交化]]求$V^{\lambda_i}$的一组单位正交基$\boldsymbol e_{i,1}, \ldots ,\boldsymbol e_{i,d_i}$
4. 由此得到的$\boldsymbol e_{1,1}, \ldots ,\boldsymbol e_{1,d_1}, \ldots ,\boldsymbol e_{k,1}, \ldots ,\boldsymbol e_{k,d_k}$是$V$的一组单位正交基，且在该基下$\mathcal A$是对角的

例如，设
$$
A = \begin{pmatrix}
0 & 1 & 1 & -1 \\
1 & 0 & -1 & 1 \\
1 & -1 & 0 & 1 \\
-1 & 1 & 1 & 0
\end{pmatrix}\in \mathrm{SM}_4(\mathbb{R})
$$
则可计算$\chi_A(t) = (t-1)^3(t+3) \implies \lambda_1 = 1,\lambda_2 = -3$，由于$4 = \dim{V^{\lambda_1}} + \dim{V^{\lambda_2}}$且$\dim{V^{\lambda_2}}$至少为$1$且其最大值为$\lambda_2$的[[Eigenvectors and Characteristic Polynomial#维数和重数|代数重数]]也为$1$，故$\dim{V^{\lambda_2}}=1,\dim{V^{\lambda_1}} = 3$，(事实上，由于$A$是[[Diagonalization|可对角化的]]，故$\lambda_1$的代数重数必然等于其几何重数)，考虑到
$$
{V^{\lambda_1}} = {{\ker \left( \lambda_1E-A \right) }} = \ker \begin{pmatrix}
1 & -1 & -1 & 1 \\
-1 & 1 & 1 & -1 \\
-1 & 1 & 1 & -1 \\
1 & -1 & -1 & 1
\end{pmatrix}
$$
只需要考虑方程
$$
x_1 -x_2-x_3+x_4 = 0
$$
的解空间即可，直接得出
$$
V^{\lambda_1} = \left< \begin{pmatrix}
1 \\ 1 \\ 0 \\ 0
\end{pmatrix}, \begin{pmatrix}
0 \\ 0 \\ 1 \\ 1
\end{pmatrix}, \begin{pmatrix}
1 \\ 0 \\ 0 \\ -1
\end{pmatrix} \right> 
$$
再计算$V^{\lambda_2}$，因为$V^{\lambda_1} {\perp} V^{\lambda_2}$且$\mathbb{R}^4 = V^{\lambda_1} \oplus V^{\lambda_2}$，所以$V^{\lambda_2}$为$V^{\lambda_1}$的[[Euclidean Space#正交补|正交补]]，由于上述方程已经给出了
$$
(1,-1,-1,1)\cdot(x_1,x_2,x_3,x_4) = 0
$$
故
$$
V^{\lambda_2} = \left< \begin{pmatrix}
1 \\ -1 \\ -1 \\ 1
\end{pmatrix} \right> 
$$
利用Gram-Schmidt正交化可分别求出$V^{\lambda_1},V^{\lambda_2}$的单位正交基
$$
\boldsymbol \epsilon_1 = \dfrac{1}{\sqrt{ 2 }} (1,1,0,0)^t,\boldsymbol \epsilon_2 = \dfrac{1}{\sqrt{ 2 }}(0,0,1,1)^t,\boldsymbol \epsilon_3 = \dfrac{1}{2}(1,-1,1,-1)^t;\;\boldsymbol \epsilon_4 = \dfrac{1}{2} (1,-1,-1,1)^t
$$
故
$$
P = \begin{pmatrix}
\dfrac{1}{\sqrt{ 2 }} & 0 & \dfrac{1}{2} & \dfrac{1}{2} \\
\dfrac{1}{\sqrt{ 2 }} & 0 & -\dfrac{1}{2} & -\dfrac{1}{2} \\
0 & \dfrac{1}{\sqrt{ 2 }} & \dfrac{1}{2} & -\dfrac{1}{2} \\
0 & \dfrac{1}{\sqrt{ 2 }} & -\dfrac{1}{2} & \dfrac{1}{2}
\end{pmatrix}
$$
我们得到$P^tAP = \mathrm{diag}(1,1,1,-3)$
## 惯性指数的求法
设$A\in \mathrm{SM}_n(\mathbb{R})$，则$A$的正（负）[[Real Quadratic Forms#惯性定理 (Sylvester)|惯性指数]]等于$\mathrm{spec}(A)$中正（负）根的个数（在记重数的意义下），特别地，$A$（半）正定当且仅当$A$的特征根都是正的（非负的）

特别地，设$A,B\in \mathrm{SM}_n(\mathbb{R})$且$A$正定，则存在$P\in \mathrm{GL}_n(\mathbb{R})$使得$P^tAP=E$和$P^tBP$是对角阵，这是因为
1. 由于$A$正定，所以存在$P_1\in\mathrm{GL}_n(\mathbb{R})$使得$P_1^tAP_1=E$
2. 令$C = P_1^tBP_1$，则$C$也对称，故存在$P_2\in \mathrm{O}_n(\mathbb{R})$使得$D = P_2^tCP_2$是对角阵
3. 令$P = P_1P_2$，则$P^tBP = P_2^tCP_2 = D$且
$$
P_2\in \mathrm{{O}_n(\mathbb{R}) \implies }P^tAP = P_2^tEP_2 = P_2^tP_2 = E
$$
由此可以证明**对于正定矩阵**
$$
\det{(A+B)} \geq \det{(A)} + \det{(B)}
$$
由于存在$P\in \mathrm{GL_n}(\mathbb{R})$使得$P^tAP = E,P^tBP = \mathrm{diag}(\alpha_1, \ldots ,\alpha_n)$，于是
$$
P^t(A+B)P = \mathrm{diag}(1+\alpha_1, \ldots ,1+\alpha_n)
$$
两边取行列式有
$$
\det{(P)}^{2} \det{(A+B)} = \prod_{i = 1}^n(1+\alpha_i)
$$
而
$$
\det{(P)}^{2}\left( \det{(A)} + \det{(B)}\right)  = \det{(P^tAP)} + \det{(P^tBP)} = 1+ \prod_{i = 1}^n \alpha_i
$$
因为$B$正定，所以$\alpha_1, \ldots ,\alpha_n\in \mathbb{R}^+$，于是$\prod(1+\alpha_i) \geq 1+ \prod\alpha_i$，故命题得证
## 斜对称矩阵的标准型
设$\mathcal A\in \mathcal{L}(V)$斜对称，则存在$\beta_1, \ldots ,\beta_s\in \mathbb{R} \backslash \left\{ 0 \right\}$，使得$\mathcal A$在$V$的某组单位正交基下的矩阵为
$$
M = \begin{pmatrix}
N(0,\beta_1) & & & & & \\
& \ddots & & & &  \\
& & N(0,\beta_s) & & & \\
& & & 0 & & \\
& & & & \ddots &  \\
& & & & & 0
\end{pmatrix}
$$
设$A\in \mathrm{SSM}_n(\mathbb{R})$，则$A$正交相似于上述形式的矩阵

实斜对称矩阵和欧式空间上的斜对称算子的特征根或者是纯虚数，或者等于$0$

## 正交矩阵的标准型
设$\mathcal A\in \mathcal{L}(V)$正交，则存在$\theta_1, \ldots ,\theta_s\in(0,\pi) \cup (\pi,2\pi)$和$\lambda_{2s+1}, \ldots ,\lambda_n\in \left\{ -1,1 \right\}$使得$\mathcal A$在$V$的某组单位正交基下的矩阵为
$$
M=\begin{pmatrix}
N(\cos \theta_1,\sin \theta_1) & & & & &\\
& \ddots & & & &\\
& & N(\cos \theta_s, \sin \theta_s) & & & \\
& & & \lambda_{2s+1} & & \\
& & & & \ddots & \\
& & & & & \lambda_n
\end{pmatrix}
$$
设$A\in \mathrm{O}_n(\mathbb{R})$，则$A$正交相似于上述形式的矩阵$M$

正交矩阵和正交算子的（复）特征根的模长都等于$1$

# 必考题
## 给定具体的矩阵，计算特征多项式，特征值和特征子空间，并判断是否可以对角化

## Hamilton-Cayley定理

## 确定低阶矩阵的Jordan标准型

## Gram-Schmidt正交化，正交补的构造

## **计算正交矩阵的标准型**

# 例题
## T1
> 设复数矩阵$\displaystyle A = \begin{pmatrix}1 & 0 & a \\ 0 & 1 & 0 \\ 0 & 0 &1 \end{pmatrix}$. 计算$A$的特征多项式和Jordan标准型.

由于$\displaystyle tE-A$为上三角矩阵，故$\chi_A = \det{(tE-A)} = (t-1)^3$，考虑到
$$
A - E = \begin{pmatrix}
0 & 0 & a  \\
0 & 0 & 0  \\
0 & 0 & 0
\end{pmatrix}, \quad (A - E)^{2} = \begin{pmatrix}
0 & 0 & 0  \\
0 & 0 & 0  \\
0 & 0 & 0
\end{pmatrix}
$$
故若$a = 0$，则$\mu_A = t-1$，那么最大的Jordan块是一阶的，所以$J_A=\mathrm{diag}{(1,1,1)}$
若$a \neq0$，则$\mu_A = (t-1)^{2}$，那么最大的Jordan块是二阶的，所以$J_A = \mathrm{diag}{(J_1(1),J_2(1))}$
## T2
> 设复数方阵$A$的特征多项式是$(t-2)^{2}(t+3)^3$.
> (i). 设$A$的极小多项式是$(t-2)^{2}(t+3)^2$. 计算$A$的Jordan标准型
> (ii). 设$\mathrm{rank}{(A-2E)}=3,\;\mathrm{rank}{(A+3E)}=4$，计算$A$的Jordan标准型和极小多项式

(i). 由特征多项式我们知道$J_A$的对角线上出现了两个$2$和三个$-3$，又根据极小多项式存在$J_2(2)$和$J_2(-3)$，故$J_A = \mathrm{diag}{(J_2(2),J_2(-3),J_1(-3))}$

(ii). 注意到几何重数的定义$\displaystyle m_\lambda = \dim{V^\lambda} = \dim{\ker(A-\lambda E)}= n-\mathrm{rank}{(A-\lambda E)}$，从而我们知道$2$的几何重数为$5-3=2$和$-3$的几何重数$5-4=1$，所以我们有两个$J(2)$和一个$J(-3)$，故$J_A$只能为$J_A = \mathrm{diag}{(J_1(2),J_1(2),J_3(-3))}$，其中最大的$2$的Jordan块是$1$阶的，而最大的$-3$的Jordan块是$3$阶的，故$\mu_A = (t-2)(t+3)^3$

## T3
> 设标准欧式空间$\mathbb{R}^3$中的子空间$U$是方程$x_1-x_2+x_3$的解空间.
> (i). 计算$U$的正交补$U^{{\perp}}$的一组基
> (ii). 计算$\mathbb{R}^3$的一组单位正交基$\boldsymbol u_1, \boldsymbol u_2, \boldsymbol u_3$，其中$\boldsymbol u_1, \boldsymbol u_2\in U$且$\boldsymbol u_3\in U^{\perp}$

(i). 由题意，$U$中所有的元素$(x_1,x_2,x_3)^T$都满足
$$
x_1-x_2+x_3 = 0 \iff (1,-1,1)\cdot(x_1,x_2,x_3) = 0
$$
于是$U^{\perp} = \left< \begin{pmatrix}1\\-1\\1\end{pmatrix} \right>$
(ii). 先直接写出$\boldsymbol u_3 = \dfrac{1}{\sqrt{ 3 }}\left( 1,-1,1 \right)^T$. 接着我们再来求解$U$的一组基，不妨直接用$x_1,x_3$来表示$x_2$即$x_2 = x_1 + x_3$，由此我们容易写出$U$的一组基为
$$
\boldsymbol v_1 = (1,1,0)^T,\quad\boldsymbol v_2=(0,1,1)^T
$$
考虑Gram-Schmidt正交化，有
$$
\begin{gather}
\boldsymbol u_1' = (1,1,0)^T \implies \boldsymbol u_1 = \dfrac{1}{\sqrt{ 2 }}(1,1,0)^T\\
\boldsymbol u_2' = \boldsymbol v_2 - (\boldsymbol v_2\vert \boldsymbol u_1)\boldsymbol u_1 = (0,1,1)^T - \dfrac{1}{2}(1,1,0)^T = (-\dfrac{1}{2}, \dfrac{1}{2},1)^T
\end{gather}
$$
从而有
$$
\boldsymbol u_1 = \dfrac{1}{\sqrt{ 2 }}(1,1,0)^T,\;\boldsymbol u_2 = \dfrac{1}{\sqrt{ 6 }}(-1,1,2)^T,\;\boldsymbol u_3 = \dfrac{1}{\sqrt{ 3 }}(1,-1,1)^T
$$
## T4
> 设实对称矩阵$A = \begin{pmatrix}0 & -1 & 1 & -1 \\-1 & 0 & -1 & 1 \\1 & -1 & 0 & -1 \\-1 & 1 & -1 & 0\end{pmatrix}$，已知$A$的特征多项式为$(t-3)(t+1)^3$，计算正交矩阵$P$和对角矩阵$D$使得$P^tAP=D$

我们需要计算$V^{3}$和$V^{-1}$，显然后者好看一些，考虑矩阵
$$
A + E= \begin{pmatrix}1 & -1 & 1 & -1 \\-1 & 1 & -1 & 1 \\1 & -1 & 1 & -1 \\-1 & 1 & -1 & 1\end{pmatrix}
$$
容易看出$\mathrm{rank}{(A+E)} = 1$，从而$\dim{V^{-1}} = 4 - 1=3, \dim{V^3}= 4 -3=1$，而$A+E$的第一行就直接告诉我们了$V^3$的一个基底
$$
V^3 = \left< (1,-1,1,-1)^T \right>  
$$
考虑$x_1-x_2+x_3-x_4 = 0$，把$x_1,x_2,x_3$作为自由变量，则写出$V^{-1}$的一组基（先省略转置）
$$
\boldsymbol v_1 = (1,0,0,1),\; \boldsymbol v_2 = (0,1,0,-1),\; \boldsymbol v_3 = (0,0,1,1)
$$
然后正交化
$$
\begin{gather}
\boldsymbol e_1' = \boldsymbol v_1 = (1,0,0,1) \implies \boldsymbol e_1 = \dfrac{1}{\sqrt{ 2 }}(1,0,0,1) \\
\boldsymbol e_2' = \boldsymbol v_2 - (\boldsymbol v_2 \vert \boldsymbol e_1)\boldsymbol e_1 = (0,1,0,-1) - \left( -\dfrac{1}{2} \right) (1,0,0,1) = (\dfrac{1}{2}, 1,0,-\dfrac{1}{2})  \\
\implies \boldsymbol e_2 = \dfrac{1}{\sqrt{ 6 }}(1,2,0,-1) \\
\boldsymbol e_3' = \boldsymbol v_3- (\boldsymbol v_3\vert \boldsymbol e_1) \boldsymbol e_1 - (\boldsymbol v_3\vert \boldsymbol e_2) \boldsymbol e_2 = (0,0,1,1) -\dfrac{1}{2}(1,0,0,1)+\dfrac{1}{6}(1,2,0,-1)  \\
 = (-\dfrac{1}{3}, \dfrac{1}{3}, 1, \dfrac{1}{3}) \implies \boldsymbol e_3 = \dfrac{1}{2\sqrt{ 3 }}(-1,1,3,1)
\end{gather}
$$
故而我们有
$$
P = \begin{pmatrix}
\dfrac{1}{\sqrt{ 2 }} & \dfrac{1}{\sqrt{ 6 }} & -\dfrac{1}{2\sqrt{ 3 }} & \dfrac{1}{2} \\
0 & \dfrac{2}{\sqrt{ 6 }} & \dfrac{1}{2\sqrt{ 3 }} & -\dfrac{1}{2} \\
0 & 0 & \dfrac{3}{2\sqrt{ 3 }} & \dfrac{1}{2} \\
\dfrac{1}{\sqrt{ 2 }} & -\dfrac{1}{\sqrt{ 6 }} & \dfrac{1}{2\sqrt{ 3 }} & -\dfrac{1}{2}
\end{pmatrix}
$$
从而$P^tAP= \mathrm{diag}{(-1,-1,-1,3)}$

## T5
> 设$P = \begin{pmatrix}\cos \theta & \sin \theta \\ \sin \theta & -\cos \theta\end{pmatrix}, \; Q = \begin{pmatrix}0 & -1 \\ 1 & 0\end{pmatrix}$和$A = \begin{pmatrix} P & O \\ O & Q\end{pmatrix}$. 计算$A$的极小多项式和$A^{2023}$

$A$的极小多项式为$\mu_P$和$\mu_Q$的乘积，我们直接计算$\chi_P = t^{2}-1,\chi_Q = t^{2}+1$，而$\mu_P,\mu_Q$显然都不能是一次的，故$\mu_P = \chi_P = t^{2}-1,\mu_Q = \chi_Q = t^{2}+1$，从而$\mu_A = \mu_P\mu_Q = t^4-1$
由对角分块矩阵的性质有$A^{2023} = \begin{pmatrix}P^{2023} & O \\ O & Q^{2023}\end{pmatrix}$，而$P^2 = E,Q^2 = -E$，从而
$$
A^{2023} = \begin{pmatrix}
P & O \\ O & -Q
\end{pmatrix}
$$

## T6
> 设$V$是域$F$上的有限维线性空间，$\mathcal A$是$V$上的线性算子，$\boldsymbol v_1$和$\boldsymbol v_2$是$\mathcal A$的两个线性无关的特征向量. 证明：$\boldsymbol v_1+\boldsymbol v_2$是$\mathcal A$的特征向量$\iff \boldsymbol v_1,\boldsymbol v_2$在同一个特征子空间中

右边推左边是显然的，故我们来证明左边推右边，设$\mathcal A \boldsymbol v_1 = \lambda_1 \boldsymbol v_1,\;\mathcal A \boldsymbol v_2 = \lambda_2 \boldsymbol v_2$和$\mathcal A(\boldsymbol v_1 + \boldsymbol v_2) = \lambda_3(\boldsymbol v_1+\boldsymbol v_2)$，第三个式子减去前面两个式子就有
$$
(\lambda_3-\lambda_1)\boldsymbol v_1 + (\lambda_3-\lambda_2)\boldsymbol v_2 = \boldsymbol 0
$$
由于$\boldsymbol v_1,\boldsymbol v_2$线性无关，故$\lambda_1=\lambda_2 = \lambda_3$，所以它们在一个特征子空间中

## T7
> 设$V$是域$F$上的$n$维线性空间，$\mathcal A$是$V$上的线性算子. 证明：$\mathcal A$在$F$中有$n$个互不相同的特征根当且仅当以下两个条件同时满足 (i). $\mathcal A$可对角化; (ii). $V$是$\mathcal A$-循环的

先证明充分性，因为$\mathcal A$可对角化，故$\mathcal A$的Jordan标准型中每一个Jordan块的大小均为一，所以$\mathcal A$的极小多项式中每一个不可约元的重数都为$1$，即
$$
\mu_{\mathcal A}=(t-\lambda_1)(t-\lambda_2) \cdots (t-\lambda_s)
$$
其中$\lambda_1, \ldots ,\lambda_s$两两不同，而又因为$V$是$\mathcal A$-循环的，所以$\deg{(\mu_{\mathcal A})} = \deg{(\chi_{\mathcal A})} = n$，故$s = n$，从而$\mathcal A$有$n$个互不相同的特征根

再证必要性，如果$\mathcal A$有$n$个互补相同的特征根，则
$$
\chi_{\mathcal A}= (t-\lambda_1)(t-\lambda_2) \cdots (t-\lambda_n)
$$
由Hamilton-Cayley定理，$\chi_{\mathcal A}$的不可约元都是$\mu_{\mathcal A}$的不可约元，从而$\mu_{\mathcal A}= \chi_{\mathcal A}$，故$V$是$\mathcal A$-循环的，且$\mathcal A$的Jordan标准型中每一个Jordan块的大小均为一，进而$\mathcal A$可对角化

## T8
> 设$V$是$n$维欧氏空间
> (i). 设$n=2$，$\boldsymbol e_1, \boldsymbol e_2$是$V$的一组单位正交基，且$\mathcal A\in \mathcal{L}(V)$由$\mathcal A(\boldsymbol e_1)= \boldsymbol e_2,\mathcal A(\boldsymbol e_2)=-\boldsymbol e_1$确定，证明$\mathcal A$可逆且对任意$\boldsymbol x\in V$有$\boldsymbol x {\perp} \mathcal A{(\boldsymbol x)}$
> (ii). 设$n=3$，是否存在$V$上的可逆线性算子$\mathcal B$使得对于任意$\boldsymbol x\in V$，$\boldsymbol x {\perp} \mathcal B(\boldsymbol x)$?

(i). 设$\mathcal A^*$由$\mathcal A(\boldsymbol e_1)= \boldsymbol -e_2,\mathcal A(\boldsymbol e_2)=\boldsymbol e_1$确定，那么对于任意的$\boldsymbol v = x\boldsymbol e_1+y\boldsymbol e_2\in V$，我们有$(\mathcal A^*\mathcal A)\boldsymbol v =\mathcal A^*(-y\boldsymbol e_1+x\boldsymbol e_2)=x \boldsymbol e_1+y\boldsymbol e_2 = \boldsymbol v$，从而$\mathcal A^*\mathcal A = \mathcal E$，故$\mathcal A$可逆. 同时又因为$(\boldsymbol x \vert \mathcal A(\boldsymbol x)) = (-y\boldsymbol e_1+x\boldsymbol e_2 \vert x\boldsymbol e_1 + y\boldsymbol e_2) = -yx+xy = 0$，于是$\forall \boldsymbol x\in V, \boldsymbol x {\perp} \mathcal A(\boldsymbol x)$

(ii). 因为$\chi_{\mathcal B}$的次数等于$3$，所以$\mathcal B$有实特征根$\lambda$（三次方程一定有一个实根），因为$\mathcal B$可逆，所以$\lambda \neq0$，设$\boldsymbol v$为$\lambda$对应的特征向量，则
$$
(\boldsymbol v \vert \mathcal B(\boldsymbol v))=(\boldsymbol v \vert \lambda \boldsymbol v)=\lambda \Vert \boldsymbol v \Vert ^{2} \neq 0
$$
所以这样的$\mathcal B$不存在

或者，设$\boldsymbol e_1,\boldsymbol e_2,\boldsymbol e_3$为$V$的一组单位正交基，则$\mathcal B$在该基底下的矩阵为$B=(b_{i,j})\in \mathrm{M}_3(\mathbb{R})$，因为特别地有$\boldsymbol e_i {\perp} \mathcal B(\boldsymbol e_i)$，所以$b_{ii}=0$，而对$\forall \boldsymbol v = x \boldsymbol e_1 + y \boldsymbol e_2 + z \boldsymbol e_3\in V$，我们有
$$
\boldsymbol v {\perp} \mathcal B(\boldsymbol v) \implies x(b_{12}y+b_{13}z) + y(b_{21}x+b_{23}z)+ z(b_{31}x + b_{32}y)=0
$$
整理后得到$(b_{12}+b_{21})xy + (b_{13}+b_{31})xz + (b_{23}+b_{32})yz=0$，所以$b_{ij} + b_{ji}=0$，从而$B$是斜对称的，可以计算三阶斜对称矩阵的行列式总是为$0$，故$B$不可逆，进而$\mathcal B$不存在

## T9
> (i). 设$P$是$n$阶正交矩阵，证明$-n \leq \mathrm{tr}{(P)} \leq n$
> (ii). 设$A,B\in \mathrm{SM}_n(\mathbb{R})$都正定，证明如果$A-B$正定，那么$B^{-1}-A^{-1}$正定

(i). 由矩阵乘法的定义$\displaystyle (AB)_{ij} = \sum_{k=1}^n \sum_{i = 1}^m \sum_{j = 1}^s A_{ik}B_{kj}$，知
$$
n = \mathrm{tr}{(E_n)} = \mathrm{tr}{(PP^t)} = \sum_{i = 1}^n (PP^t)_{ii} = \sum_{i=1}^n \sum_{j = 1}^n P_{ij}P^t_{ji } = \sum_{i = 1}^n \sum_{j = 1}^n P_{ij}^{2}
$$
于是我们有
$$
\sum_{i = 1}^n P_{ii}^{2} \leq \sum_{i = 1}^n \sum_{j = 1}^n P_{ij}^{2} = n
$$
由Cauchy不等式
$$
\left( \sum_{i = 1}^n P_{ii}^{2} \right) \left( \sum_{i = 1}^n 1^{2} \right)  \geq \left( \sum_{i = 1}^n P_{ii}\cdot1 \right) ^{2}
$$
即有$n\cdot n \geq \left(\mathrm{tr}{(P)} \right)^{2} \implies -n \leq \mathrm{tr}{(P) \leq n}$

或者说，因为$P$是正交矩阵，所以$P$的列向量都是单位向量，$P$中的每一个元素的绝对值都不大于$1$，所以命题得证

(ii). 因为$A$正定，所以存在$P\in \mathrm{GL}_n(\mathbb{R})$使得$E = P^tAP,\;D=P^tBP$，其中$D = \mathrm{diag}{(\lambda_1, \ldots ,\lambda_n)}$，又因为$B$正定，所以$\lambda_1, \ldots ,\lambda_n >0$. 又因为$A-B$正定，所以$E-D$正定，于是
$$
1-\lambda_1, \ldots ,1-\lambda_n >0 \implies 0 < \lambda_i < 1,\; i = 1,2, \ldots ,n
$$
从而$D^{-1}-E = \mathrm{diag}{(\dfrac{1}{\lambda_1}-1, \ldots \dfrac{1}{\lambda_n}-1)}$正定，所以$B^{-1}-A = (P^t)^{-1}(D^{-1}-E)P^{-1}$正定，命题得证

## T10
> 设$A\in \mathrm{M}_n(\mathbb{C})$，它的特征多项式是$(t-\lambda_1)^{d_1}\cdots(t-\lambda_s)^{d_s}$，其中$\lambda_1, \ldots ,\lambda_s\in \mathbb{C}$两两不同，$d_1, \ldots ,d_s\geq1$，再设$k$是大于$1$的正整数
> (i). 证明$A^k$的特征多项式是$(t-\lambda_1^k)^{d_1}\cdots (t-\lambda_s^k)^{d_s}$
> (ii). 再设$A$与$A^k$相似，证明$A$的非零特征值都是单位根，即满足方程$z^m=1 \;(m\in \mathbb{N}^*)$的复数根

(i). 设$J_A$的对角线是
$$
\underbrace{ \lambda_1, \ldots ,\lambda_1 }_{ d_1 }, \ldots ,\underbrace{ \lambda_s, \ldots ,\lambda_s }_{ d_s }
$$
因为$J_A$是上三角的，所以$J_A^k$的对角线就是
$$
\underbrace{ \lambda_1^k, \ldots ,\lambda_1^k }_{ d_1 }, \ldots ,\underbrace{ \lambda_s^k, \ldots ,\lambda_s^k }_{ d_s^k }
$$
因为$A^k$和$J^k_A$相似，所以$A^k$的特征多项式就是$J_A^k$的，也就是$(t-\lambda_1^k)^{d_1}\cdots (t-\lambda_s^k)^{d_s}$

(ii). 由于特征多项式是相似不变量，故而
$$
(t-\lambda_1)^{d_1}\cdots(t-\lambda_s)^{d_s} = (t-\lambda_1^k)^{d_1}\cdots (t-\lambda_s^k)^{d_s}
$$
故而左边和右边的特征根一一对应，我们设$\lambda_i$和$\lambda_j^k$的对应关系用一个置换$\sigma\in S_s$来表示，使得对任意$i = 1,2, \ldots ,s$有$\lambda_i = \lambda_{\sigma(i)}^k$，从而我们有
$$
\lambda_i = \lambda_{\sigma(i)}^k = \lambda_{\sigma^{2}(i)}^{k^{2}} = \cdots = \lambda_{\sigma^m(i)}^{k^m} = \lambda_i^{k^m}
$$
其中$m$为$\sigma$的[[Permutation#Order of a Permutation|阶数]]，进而$\lambda_i^{k^m-1}=1$，命题得证

## T11
> 计算$J_5^2(0)$和$J_5^3(0)$的Jordan标准型

由[[Linear Algebra 24 Spring Final#T10|T10]]的(i)我们知道$J_5(0),J_5^2(0),J_5^3(0)$的特征多项式都为$t^5$，而它们的极小多项式分别为$t^5,t^3,t^2$（$J_5^2(0)$需要乘三次才能大于等于$5$次，$J_5^3(0)$需要乘两次才能大于等于$5$次），又注意到它们的秩分别为$4,3,2$，也即是说它们的几何重数分别为$1,2,3$，进而唯一确定它们的Jordan标准型分别为$J_5(0),\mathrm{diag}{(J_3(0),J_2(0))},\mathrm{diag}{(J_2(0),J_2(0),J_1(0))}$

也可以直接通过秩序列公式$n_\ell = \mathrm{rank}{(J_5^{\ell +1}(0))} + \mathrm{rank}{(J_5^{\ell -1}(0))}-2\mathrm{rank}{(J_5^\ell (0))}$来求

## T12
> 若$\mathcal A\in \mathcal{L}(V)$可逆，且$W \subset V$是$\mathcal A$-不变子空间，证明$W$也是$\mathcal A^{-1}$-不变子空间

因为$\mathcal A$可逆，所以$\mathcal A_W$是单射，即$\ker \mathcal A = \left\{ \boldsymbol 0 \right\}$，则$\dim{(\mathrm{im(\mathcal A)})}= \dim{W} - 0 = \dim{W}$，所以$\mathrm{im}(\mathcal A)= W$，从而$\mathcal A_W$也是满射，进而$\mathcal A_W$是双射. 所以对任意$\boldsymbol w\in W$，存在$\boldsymbol v\in W$使得$\mathcal A(\boldsymbol v) = \boldsymbol w\implies \mathcal A^{-1}(\boldsymbol w)\in W$，故$W$也是$\mathcal A^{-1}$-不变子空间

另外，由[[Matrix Inverse#Polynomials|矩阵求逆的多项式法]]可知，$\mathcal A^{-1}\in F[\mathcal A]$，所以该命题是显然的

## T13
> 设$V$是域$F$上的线性空间，$\mathcal A\in \mathcal{L}(V)$. 设$p\in F[t]\backslash F$使得$\mu_{\mathcal A}=p^kq$，其中$q\in F[t]$，且有$\gcd(p,q)=1$，证明$\ker (p(\mathcal A)^{k-1}) \varsubsetneqq \ker (p(\mathcal A)^k) = \ker(p(\mathcal A)^{k+1})$

因为$\mu_\mathcal{A}(\mathcal A)=0$，且$\gcd(p,q)=1$，故由核核分解定理
$$
V = \ker(p^k) \oplus  \ker(q)
$$
设$P = \ker(p^k),Q = \ker(q)$，则$P,Q$都是$\mathcal A$-不变子空间且$\mu_{\mathcal A_P}=p^k,\mu_{\mathcal A_Q} = q$（因为这两者显然是$\mathcal A_P$和$\mathcal A_Q$的零化多项式，且它们的次数最小，否则它们乘起来就会有比$\mu_{\mathcal A}$次更小的零化$\mathcal A$的多项式）

于是$\ker (p(\mathcal A)^{k-1}) \neq \ker (p(\mathcal A)^k)$，因为如果不然$p^k$就不是$\mathcal A_P$的极小多项式；另一方面，由于$p^{k+1}q=p\mu_{\mathcal A}$自然也零化$\mathcal A$且$\gcd(p^{k+1},q)=0$，故再利用核核分解
$$
V = \ker(p^{k+1}) \oplus  \ker(q)
$$
故必然有$\ker (p(\mathcal A)^k) = \ker(p(\mathcal A)^{k+1})$

## T14
> 设$A,B\in \mathrm{M}_n(\mathbb{R})$证明 
> (i). 如果$A$是正交矩阵且$\det{(A)} = -1$，则$-1$是$A$的特征根
> (ii). 如果$A$是正定矩阵且$B$是斜对称矩阵，则$A+B$可逆

(i). 因为$A$正交，所以存在$P\in \mathrm{O}_n(\mathbb{R})$使得
$$
P^tAP = M = \mathrm{diag}{(N(\cos \theta_1,\sin \theta_1), \ldots ,N(\cos \theta_s,\sin \theta_s),1, \ldots ,1,-1, \ldots ,-1)}
$$
故$\det{(M)} = \det{(P^tAP)}= \det{(P^{-1}AP)} = \det{(A)} = -1$，而$\det{(N(\cos \alpha,\sin \alpha))}=1$，故$A$必有$-1$作为特征根
(ii). 因为$A$正定，所以存在$P\in \mathrm{GL}_n(\mathbb{R})$使得$P^tAP= E$，从而
$$
\det{(A+B)} \neq 0 \iff \det{(P^t(A+B)P)} \neq 0 \iff \det{(E + P^tBP)} \neq 0
$$
而其中$P^tBP + (P^tBP)^t = P^tBP + P^tB^t P = P^t(B + B^t)P = P^tOP = O$，故$P^tBP$也是斜对称的，故要证明原命题，只需证明对任意$B\in \mathrm{SSM}_n(\mathbb{R})$，$E + B$可逆

由于$B$是斜对称的，所以存在$Q\in \mathrm{O}_n(\mathbb{R})$使得
$$
Q^tBQ = M = \mathrm{diag}{(N(0,\beta_1), \ldots ,N(0,\beta_s),0, \ldots ,0)}
$$
从而
$$
Q^t(E+B)Q = Q^{-1}EQ + Q^tBQ = \mathrm{diag}{(N(1,\beta_1), \ldots ,N(1,\beta_s),1, \ldots ,1)}
$$
故$\det{(E+B)} = \det{(Q^t(E+B)Q)} = \det{N(1,\beta_1) \cdots \det{N(1,\beta_s)}} \geq1$，于是$E+B$可逆, 原命题进而也得证

## T15
> 设$A,B\in \mathrm{M}_n(\mathbb{R})$. 证明$AB$和$BA$的特征多项式相等; 如果考虑一般域$F$, 该命题还成立吗

如果$B$可逆, 则有$B(AB)B^{-1} = BA$即$AB$和$BA$相似, 故它们有相同的特征多项式. 

由于可逆矩阵在$\mathrm{M}_n(\mathbb{R})$上是稠密的, 所以存在实数$a > 0$使得对任意的$\varepsilon\in(0,a)$, 我们有$\varepsilon E + B$可逆, 故而$A(\varepsilon E + B)$和$(\varepsilon+B)A$相似, 所以它们拥有相同的特征多项式, 即
$$
\det{(tE-A(\varepsilon E+B))} = \det{(tE - (\varepsilon E + B)A)}
$$
注意到上式两侧都是关于$\varepsilon$的多项式, 故而取$\varepsilon=0$时上述等式依然成立, 即$AB$和$BA$的特征多项式相等

如果考虑一般域, 命题也是成立的. 这是因为我们设$\varepsilon\in F$, 则$\varepsilon E + B\in \mathrm{M}_n(F[\varepsilon])$, 且$\det{(\varepsilon E + B)}$是关于$\varepsilon$的$n$次多项式, 故而不等于$0$, $\varepsilon + B$可逆, 所以我们仍然能通过上面的方式证明$AB$和$BA$的特征多项式相等

## T16
> 设$M\in \mathrm{M}_m(F)$和$N\in \mathrm{M}_n(F)$. 证明$(m+n)$阶矩阵$\begin{pmatrix} M & O \\ O & N\end{pmatrix}$和$\begin{pmatrix}N & O \\ O & M\end{pmatrix}$相似

同一算子在不同基底下的矩阵表示是相似的, 故而上述两个矩阵可以看成某个线性算子在两组基底的交换后的结果, 从而我们容易给出
$$
Q^{-1} \begin{pmatrix}
 M & O \\ O & N
\end{pmatrix} Q = \begin{pmatrix}
N & O \\
O & M
\end{pmatrix}
$$
其中
$$
Q = \begin{pmatrix}
O & E_m \\ E_n & O
\end{pmatrix}, \quad Q^{-1} = \begin{pmatrix}
O & E_n \\
E_m & O
\end{pmatrix}
$$
## T17
> 设$V$是域$F$上的$n$维线性空间, $\mathcal A$是$V$上的线性算子. 如果$W$既是$\mathcal A$-循环子空间又是$\mathcal A$的一个特征子空间, 计算$\dim{(W)}$

因为$W$是$\mathcal A$的一个特征子空间, 所以$\mathcal A_W$是一个数乘算子, 记为$\mathcal A_W = \lambda \mathcal E$, 所以它的极小多项式是$\mu_{\mathcal A_W} = t- \lambda$, 又因为$W$是$\mathcal A$-循环的, 所以就有$\dim{(W)} = \deg{\chi_{\mathcal A_W}} = \deg{\mu_{\mathcal A_W}} = 1$

## T18
> 设$\mathbb{R}^n$是标准欧式空间, 其中的向量为列向量. 设$\boldsymbol v\in \mathbb{R}^n$是单位向量. 令$n$阶方阵$H_{\boldsymbol v } = E - 2\boldsymbol v \boldsymbol v^t$, 计算$H_{\boldsymbol v}$的所有特征根和它们的几何重数

考虑到
$$
H_{\boldsymbol v} \boldsymbol v = \boldsymbol v - 2 \boldsymbol v \boldsymbol v^t \boldsymbol v = \boldsymbol v - 2\boldsymbol v\cdot1 = - \boldsymbol v
$$
故$-1$是$H_{\boldsymbol v}$的特征根. 而由$\boldsymbol v$出发可以得到$V$的一组单位正交基$\boldsymbol v, \boldsymbol e_2, \ldots ,\boldsymbol e_n$, 则有
$$
H_{\boldsymbol v} \boldsymbol e_i = \boldsymbol e_i -2 \boldsymbol v \boldsymbol v^t \boldsymbol e_i = \boldsymbol e_i - 2\boldsymbol v\cdot0 = \boldsymbol e_i
$$
所以$1$也是$H_{\boldsymbol v}$的特征根, 并且$V^1 = \left< \boldsymbol e_2, \ldots ,\boldsymbol e_n \right>$是$1$的特征子空间, 所以自然有$1$的几何重数为$n-1$, 而$-1$的几何重数为$1$, 不可能存在其他的特征根

## T19
> 设$A\in \mathrm{M}_n(\mathbb{R})$是正规矩阵, 证明$A$和$A^t$正交相似

由于$A$正规, 则存在$P\in \mathrm{O}_n(\mathbb{R})$使得
$$
P^t A P = M = \mathrm{diag}{(N(\alpha_1,\beta_1), \ldots ,N(\alpha_s,\beta_s),\lambda_{2s+1}, \ldots ,\lambda_n)}
$$
两边取转置, 则有
$$
P^t A^t P = M^t = \mathrm{diag}{(N^t(\alpha_1,\beta_1), \ldots ,N^t(\alpha_s,\beta_s),\lambda_{2s+1}, \ldots ,\lambda_n)}
$$
要证明$A \sim_o A^t$, 只需证明$M \sim_o M^t$, 考虑最小的单位, 容易发现
$$
\begin{pmatrix}
-1 & 0  \\
0 & 1
\end{pmatrix} \begin{pmatrix}
\alpha & -\beta \\
\beta & \alpha
\end{pmatrix} \begin{pmatrix}
-1 & 0  \\
0 & 1
\end{pmatrix} = \begin{pmatrix}
\alpha & \beta \\
-\beta & \alpha
\end{pmatrix}
$$
也就是$Q^tN(\alpha,\beta)Q = N^t(\alpha,\beta)$, 其中$Q = \begin{pmatrix}-1 & 0 \\ 9 & 1\end{pmatrix}$是正交矩阵, 从而就有$Q^tMQ = M^t$, 故$M$和$M^t$正交相似, 原命题也得证

