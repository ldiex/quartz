# 多项式作用不改变相似关系
设$A, B \in \mathrm{M}_n(F)$且$A\sim_s B$. 则存在$P \in \mathrm{{GL}_n(F)}$使得$A = P^{-1}BP$,  即
$$
\forall k \in \mathbb{N}, A^k = P^{-1}B^k P
$$
进而
$$
\forall f \in F[t], f(A) = P^{-1} f(B) P
$$
即$f(A) \sim_s f(B)$

# 零化多项式和极小多项式
设$f \in F[t], \mathcal A \in \mathcal L(V)$. 如果$f(\mathcal A) = \mathcal O$, 则称$f$是关于$\mathcal A$的*零化多项式*.  类似地可对$A \in \mathrm{M_n}(F)$定义$A$的零化多项式的概念. 在这些零化多项式中，我们把**次数最小**的称为*极小多项式*
> [!Note]
> 设$A, B\in \mathrm{M}_n(F)$，则$A \sim_s B \implies \mu_A = \mu_B$

$\mathcal A$的[[Characteristic Polynomial|特征多项式]]是$\mathcal A$的一个特殊的零化多项式，通过后面的整除判别法，**我们可以从它的因子中寻找极小多项式**
# 整除判别法
设$\mathcal{A} \in \mathcal{L}(V)$和$p(t) \in F[t] \backslash \{0\}$零化$\mathcal{A}$.  则$p$是$\mathcal{A}$的极小多项式$\iff$对任意$f\in F[t]$零化$\mathcal{A}$, $p \mid f$

> [!Tip]
> 由此可知，$\mathcal{A}$的两个极小多项式必然在$F[t]$中相伴. **我们把关于$\mathcal{A}$的[[Multivariate Polynomial Ring#首一多项式|首一多项式]]记为$\mu_\mathcal{A}$**. 
> 由于上述判别法对方阵也成立，于是我们也把$A \in\mathrm{M}_n(F)$的首一极小多项式记为$\mu_A$

# 极小多项式的性质
## 特殊算子的极小多项式
### 数乘算子
设$\mathcal{A} \in \mathcal{L}(V)$. 则$\deg(\mu_\mathcal{A}) = 1$当且仅当$\mathcal{A}$是[[Linear Operator#线性算子代数|数乘算子]].

类似地，$A \in \mathrm{M}_n(F)$是数乘矩阵当且仅当$\deg \mu_A = 1$. 

由此可知，数乘矩阵和非数乘矩阵必然不相似

### 幂零算子
$\mathcal A \in \mathcal{L}(V)$是*幂零算子*当且仅当$\mu_\mathcal A \in F[t]$是$t$的幂次. 

由此可知微分算子$\mathcal D:\mathbb{R}[x]^n \to \mathbb{R}[x]^n$的极小多项式是$t^n$

## 相似等价下的不变量
设$A, B \in \mathrm{M}_n(F)$. 如果$A \sim_s B$, 则$\mu_A = \mu_B$.

## 极小多项式的次数
设$\mathcal A \in \mathcal{L}(V)$, 则 $\dim(F[\mathcal A]) = \deg(\mu_\mathcal A)$

## $0$根和算子的可逆性
设$\mathcal A \in \mathcal{L}(V)$, 则$\mathcal A$可逆$\iff \mu_\mathcal A (0) \neq 0$

值得注意的是，极小多项式和[[Characteristic Polynomial|特征多项式]]的根都是$\mathcal A$的[[Eigenvectors and Characteristic Polynomial#特征值|特征值]]，所以$\mathcal A$可逆同样蕴含了$\chi_\mathcal A(0)\neq 0$

# 计算方法
## 通过特征多项式
由[[Cyclic Subspace#Hamilton-Cayley定理加强版|Hamilton-Cayley定理]]，极小多项式一定是特征多项式的因子，即$\mu_\mathcal A \mid \chi_\mathcal A$
## 可对角化的情况
如果$\mathcal A$是[[Diagonalization|可对角化]]的，且拥有**不同的**特征值$\lambda_1,\ldots,\lambda_d$，那么$\mathcal A$的极小多项式就是
$$
\mu_\mathcal A = \prod_{i = 1}^d (t-\lambda_i)
$$
# 零化某个向量的极小多项式
设$\mathcal A \in \mathcal{L}(V), \boldsymbol v \in V, f(t) \in F[t]$. 如果$f(\mathcal A)(\boldsymbol v) = \boldsymbol 0$, 则称$f(t)$是*通过$\mathcal A$零化$\boldsymbol v$的多项式*. 

非零、次数最小的这样的多项式称为*通过$\mathcal A$零化$\boldsymbol v$的极小多项式*，记为$\mu_{\mathcal A, \boldsymbol v}$, 它通常是首一的. 

## 零化某个向量的极小多项式的性质
### 平凡情况
对$\forall \boldsymbol v \in V$, 有$\boldsymbol v = \boldsymbol 0 \iff \mu_{\mathcal A,\boldsymbol v} = 1$

### 多项式下的变换
对任意$f\in F[t]$, 我们有$\mu_{\mathcal A,\boldsymbol v} = \mu_{\mathcal A,  f(\mathcal A)\boldsymbol v}\cdot \gcd(\mu_{\mathcal A,\boldsymbol v},f)$，利用这一点，当我们知道零化$\boldsymbol v$的极小多项式时，就可以很方便地求出零化$f(\mathcal A)\boldsymbol v$的极小多项式
### 次数
类似于$\dim(F[\mathcal A]) = \deg(\mu_\mathcal A)$，我们有$\dim(F[\mathcal A]\cdot \boldsymbol v) = \deg(\mu_{\mathcal A, \boldsymbol v})$，其中$F[\mathcal A]\cdot \boldsymbol v$表示[[Cyclic Subspace|循环子空间]]

### 和极小多项式之间的联系
1. $\mu_{\mathcal A ,\boldsymbol v} \mid \mu_\mathcal A$
2. 对$\forall \mathcal A \in \mathcal{L}(V)$，总存在$\boldsymbol v\in V$使得$\mu_{\mathcal A, \boldsymbol v} = \mu_\mathcal A$. 也就是说，总是存在这样一个$\boldsymbol v$使得$f(\mathcal A)(\boldsymbol v) = \boldsymbol 0\implies f(\mathcal A) = \mathcal O$ (要把它'杀死'就必须先把$\mathcal A$ '杀死')

> [!Tip] 特征向量
> 上面的$\boldsymbol v$可称为“同归于尽向量”，与之相对的还有[[Eigenvectors and Characteristic Polynomial#特征向量|特征向量]]，它被称为“懦弱的向量”，即可以在$f(\mathcal A) \neq \mathcal O$的情况下使得$f(\mathcal A)(\boldsymbol v) = \boldsymbol 0$，也就是自己先“投降”了

