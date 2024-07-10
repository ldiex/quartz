# 定义
设$V$是域$F$上的$n$维线性空间，$\boldsymbol e_1, \ldots, \boldsymbol e_n$是$V$的一组基. 集合$\operatorname{Hom}(V, V)$记为$\mathcal L(V)$，其中的元素称为*线性算子*. 线性算子通常用$\mathcal A, \mathcal B, \ldots$表示. 特别地，$\mathcal O$表示零算子，$\mathcal E$表示恒等算子

# 矩阵相似
设$\boldsymbol \epsilon_1, \ldots, \boldsymbol \epsilon_n$是$V$的另一组基，且
$$
(\boldsymbol \epsilon_1, \ldots, \boldsymbol \epsilon_n) = (\boldsymbol e_1, \ldots, \boldsymbol e_n) P
$$
其中$P \in \mathrm{GL}_n(F)$. 设算子$\mathcal A \in \mathcal L(V)$在$\boldsymbol e_1, \ldots, \boldsymbol e_n$下的矩阵等于$A$. [[Matrix Representation of Linear Map#线性映射在不同基底下的矩阵|由此]]可知，$\mathcal A$在$\boldsymbol \epsilon_1, \ldots, \boldsymbol \epsilon_n$下的矩阵为$P^{-1}AP$

> [!Note] 
> 设$A, B \in \mathrm{M}_n(F)$. 如果存在$P \in \mathrm{GL}_n(F)$使得$B = P^{-1}AP$，则称$B$与$A$*相似*，记为$B \sim_s A$. 可以验证，相似关系是一个[[Equivalence Relation|等价关系]]

设$A, B \in \mathrm{M}_n(F)$. 如果$A \sim_s B$，则有如下*相似不变量*
$$
\mathrm{rank}(A) = \mathrm{rank}(B),\; \det(A) = \det(B), \;\mathrm{tr}(A) = \mathrm{tr}(B), \chi_A = \chi_B, \mu_A = \mu_B
$$
这一点告诉我们，无论通过选取何种基底得到的$\mathcal A$的矩阵$A$，它的[[Matrix Rank|秩]]、[[Determinant|行列式]]、[[Trace|迹]]、[[Characteristic Polynomial|特征多项式]]、[[Minimal Polynomial|极小多项式]]都是不变的. 
设$A, B \in \mathrm{M}_n(F)$. 如果$A \sim_s B$，则
$$
\forall f \in F[t], \; f(A) \sim_s f(B)
$$
这两个结论的逆命题是**不正确**的
> [!Summary] 矩阵关系总结
> *初等等价* $A \sim_e B \iff \mathrm{rank}(A) = \mathrm{rank}(B)$ 
> *合同等价* $A \sim_c B \iff \exists P \in \mathrm{GL}_n(F), B = P^t A P$
> *相似等价* $A \sim_s B \iff \exists P \in \mathrm{GL}_n(F), B = P^{-1} A P$ 
> 后面两种等价都蕴含第一种等价

# 线性算子代数
我们已知$(\mathcal L(V), +, \mathcal O, \text{数乘})$是$F$上的线性空间，再由复合的结合律，我们可推出$(\mathcal L(V), + \mathcal, O, \circ, \mathcal E)$是一个[[Ring|环]]，我们称$\mathcal L(V)$是$F$上的一个*代数*

设
$$
\begin{aligned}
\Phi : \mathcal L(V) &\to \mathrm{M}_n(F) \\
\mathcal A &\to A
\end{aligned}
$$
则$\Phi$既是[[Linear Isomorphism|线性同构]]又是环同构，此时称$\Phi$是*代数同构*

设$\mathcal A \in \mathcal L(V)$. 如果$\mathcal A$可逆，则称$\mathcal A$是*可逆算子*. 如果存在$\lambda \in F$使得对任意$\boldsymbol x \in V, \; \mathcal A(\boldsymbol x) = \lambda \boldsymbol x$，则称$\mathcal A$是*数乘算子*，此时$\mathcal A = \lambda \mathcal E$. 如果存在$k \in \mathbb Z^+$使得$\mathcal A^k = \mathcal O$，则称$\mathcal A$为*幂零算子*. 如果$\mathcal A^2 = \mathcal A$，则称$\mathcal A$为*幂等算子*. 如果$\mathcal A^2 = \mathcal E$，则称$\mathcal A$是*对合算子*

> [!Tip] 数乘算子和交换律
> 如果存在$\mathcal A \in \mathcal L(V)$使得对$\forall \mathcal B \in \mathcal L(V)$有$\mathcal A \mathcal B = \mathcal B \mathcal A$, 则$\mathcal A$是数乘算子
> **证明：**
> 取$\mathcal B \boldsymbol x= f(\boldsymbol x) \boldsymbol v$，其中$\boldsymbol x, \boldsymbol v \in V$且$f \in V^*$, 则
> $$
> \mathcal A \mathcal B = \mathcal B \mathcal A \implies \mathcal A (f(\boldsymbol x) \boldsymbol v) = f(\mathcal A \boldsymbol x) \boldsymbol v \implies f(\boldsymbol x) \mathcal A \boldsymbol v = f(\mathcal A \boldsymbol x) \boldsymbol v 
> $$
> 因为我们总可以取$f, \boldsymbol x$使得$f(\boldsymbol x) \neq 0$，故有
> $$
> \mathcal A \boldsymbol v = \alpha \boldsymbol v, \quad \alpha = \dfrac{ f(\mathcal A \boldsymbol x)}{ f(\boldsymbol x)}
> $$
> 即$\mathcal A$是数乘算子

## 核像分解
设$\mathcal A \in \mathcal L(V)$. 则
$$
V = \ker(\mathcal A) \oplus \mathrm{im}{\mathcal A} \iff \mathrm{rank}(\mathcal A) = \mathrm{rank}(\mathcal A^2)
$$
设$\mathcal A \in \mathcal L(V)$. 则
$$
V = \ker(\mathcal A) \oplus \mathrm{im}{\mathcal A} \iff V = \ker(\mathcal A) + \mathrm{im}({\mathcal A})
$$
> [!Note] 核核分解
> 若$\mathcal A \in \mathrm{Hom}(V,V), \; f\in F[x]$且$f(\mathcal A) = \mathcal O$.  如果有$f = p_1\cdots p_m$，其中$p_1, \ldots, p_m \in F[x]$两两互素，则
>$$V = K_1 \oplus \cdots \oplus K_m$$
> 其中$K_i = \ker(p_i(\mathcal A))$
> 具体参见[[Invariant Subspace#核核分解|核核分解]]




