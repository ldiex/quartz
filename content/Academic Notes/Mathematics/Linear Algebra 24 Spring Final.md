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

## 循环算子判别法
# 空间分划
## 不可分子空间分解
## 循环子空间分解
# Jordan标准型
## 低阶矩阵$J_A$的求法
## 初等因子组
## 矩阵相似的判断
## 通过秩序列计算$J_A$
# 欧式空间
## 向量代数和内积运算
## Gram-Schmidt正交化
## 正交投影和正交补
## 构造单位正交基

# 正规算子
## 正交等价
## 正交标准型

# 必考题
## 给定具体的矩阵，计算特征多项式，特征值和特征子空间，并判断是否可以对角化

## Hamilton-Cayley定理

## 确定低阶矩阵的Jordan标准型

## Gram-Schmidt正交化，正交补的构造

## 计算正交标准型