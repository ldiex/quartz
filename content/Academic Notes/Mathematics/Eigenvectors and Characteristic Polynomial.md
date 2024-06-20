# 特征向量
设$\mathcal A \in \mathcal{L}(V),\;\boldsymbol v \in V \backslash \{\boldsymbol 0\}$. 如果$\langle\boldsymbol v\rangle$是$\mathcal A$-子空间，则称$\boldsymbol v$是$\mathcal A$的一个*特征向量*，其中$\mathcal A$-子空间表示$\mathcal A$的[[Invariant Subspace|不变子空间]]

设$\mathcal A \in \mathcal{L}(V), \;\boldsymbol v \in V \backslash\left\{ \boldsymbol 0 \right\}$. 则下列结论等价：
1. $\boldsymbol v$是$\mathcal A$的特征向量
2. $\mathcal A(\boldsymbol v) \in \langle \boldsymbol v \rangle$
3. $\exists \lambda \in F,\; \mathcal A(\boldsymbol v) = \lambda \boldsymbol v$

# 特征值
我们称上面等价结论$3.$中的$\lambda$是关于特征向量$\boldsymbol v$的*特征值*，简称$\mathcal A$的*特征值*。

特别地，如果$0$是$\mathcal A$的一个特征值，那么$\mathcal A$必然是不可逆的。

对于$\lambda \in F$，以下两个结论等价
1. $\lambda$是$\mathcal A$的特征值
2. $\mu_\mathcal A(\lambda) = 0$，其中$\mu_\mathcal A$是$\mathcal A$的极小多项式
# 特征多项式
设$\mathcal A \in \mathcal{L}(V),\;\boldsymbol e_1, \ldots,\boldsymbol e_n$是$V$的一组基，$\mathcal A$在该基底下的矩阵为$A$. 设$\boldsymbol x = x_1\boldsymbol e_1 + \cdots + x_n\boldsymbol e_n$且$\boldsymbol x \neq \boldsymbol 0$. 则$\boldsymbol x$是$\mathcal A$的特征向量当且仅当
$$
\lambda \begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix} = A \begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix} \iff (\lambda E - A) \begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix} = \begin{pmatrix}
0 \\ \vdots \\ 0
\end{pmatrix}
$$
由此知$\det(\lambda E - A) = 0$. 设$\chi_A(t) = \det(tE-A) \in F[t]$. 则$\boldsymbol x$是$\mathcal A$的特征向量蕴含着它对应的特征值$\lambda$是$\chi_A(t)$的根，反之它的根也是$\mathcal A$的特征值

设$A \in \mathrm{M}_n(F), t$是$F$上的未定元，则多项式
$$
\det(tE-A) \in F[t]
$$
称为$A$的*特征多项式*，记为$\chi_A(t)$

>[!Tip] 矩阵的特征多项式是相似不变量
>设$A, B \in \mathrm{M}_n(F)$则$A \sim_s B \implies \chi_A = \chi_B$

设$A \in \mathrm{M}_n(F)$. 特征多项式$\chi_A$在$F$中的根称为$A$的*特征根(eigenroots)*，这些特征根的集合记为$\mathrm{spec}_F(A)$，称为$A$在$F$中的*谱(spectrum)*

矩阵的特征根就是矩阵的特征值，且$\mathrm{spec}_F(A)$也是相似不变量

设$V$是$\mathbb{C}$上的线性空间，$\mathcal A \in \mathcal{L}(V)$，则$\mathcal A$一定有特征向量
## 特征多项式的形式
**特征多项式的次数为$n = \dim(V)$**
设$A \in \mathrm{M}_n(F)$
$$
\chi_A(t) =t^n +a_{n - 1}t^{n - 1}+ \cdots +a_1t + a_0, \quad a_i \in F
$$
则有$a_{n - 1} = -\mathrm{tr}(A), a_0 = (-1)^n \det (A)$. 特别地，$A$可逆$\iff$$0$不是$A$的特征根

设$A\in\mathrm{M}_n(F)$是如下分块上三角矩阵
$$
\begin{pmatrix}
A_1 & * & * & \cdots & * \\
O & A_2 & * & \cdots & * \\
O & O & A_3 & \cdots & * \\
\vdots & \vdots & \vdots & \ddots & * \\
O & O & O & \cdots & A_k
\end{pmatrix}
$$
则有$\chi _A = \chi_{A_1}\cdots\chi_{A_k}$
# 特征子空间
设$\lambda \in F$是$\mathcal A$的特征值，令
$$
V^\lambda = \left\{ \boldsymbol x \in V \mid \mathcal A(\boldsymbol x) = \lambda \boldsymbol x \right\} 
$$
称为$\mathcal A$关于$\lambda$的*特征子空间*，可以验证$V^\lambda$是$\mathcal A$-子空间

由定义，特征子空间可以写成
$$
V^\lambda = \ker(\lambda E-A)
$$
## 特征子空间的和
以下三个结论等价
1. $\mathcal A$是[[Diagonalization|可对角化]]的
2. $V = V^{\lambda_1} + \cdots+V^{\lambda_k}$
3. $V^{\lambda_1} + \cdots+V^{\lambda_k}$是直和
## 维数和重数
由[[Linear Map#线性映射基本定理|对偶定理]]可以得到
$$
\dim V^\lambda = \dim \ker(\lambda E - A) = n - \mathrm{rank}(\lambda E - A)
$$
我们把$\dim V^\lambda$称为$\lambda$的*几何重数*，而把$\lambda$在$\chi_A(t)$中的[[Gauss's Lemma and Eisenstein's Irreducibility Criterion#重数|重数]]称为$\lambda$的*代数重数*
> [!Tip] $\lambda$的代数重数总是大于等于它的几何重数
