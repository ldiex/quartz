# 定义
设$\mathcal A\in \mathcal{L}(V)$. 如果$\mathcal A$在$V$的某组基下的矩阵是对角矩阵，则称$\mathcal A$是*可对角化的*（相似对角化）. 如果$A\in \mathrm{M}_n(F)$相似于一个对角矩阵，则称$A$是*可对角化的*

# 判别法
## $n$个特征向量线性无关（充要）
设$n = \dim(V)$和$\mathcal A \in \mathcal{L}(V)$. 则$\mathcal A$可对角化当且仅当$\mathcal A$有$n$个线性无关的[[Eigenvectors and Characteristic Polynomial#特征向量|特征向量]]

设$A\in \mathrm{M}_n(F)$. 则$A$可对角化当且仅当$A$有$n$个线性无关的特征向量，设它们为$\boldsymbol v_1, \ldots, \boldsymbol v_n$. 令$P=(\boldsymbol v_1, \ldots, \boldsymbol v_n)$. 则$P^{-1}AP$是对角矩阵

线性算子$\mathcal A\in \mathcal{L}(V)$可对角化当且仅当$\mathcal A$在$V$的任何一组基下的矩阵可对角化
## $n$个不同的特征根（充分不必要）
设$\mathcal A \in \mathcal{L}(V), n = \dim(V)$. 如果$\chi_A$在$F$中有$n$个不同的根，则$\mathcal A$可对角化. 设$\mathcal A \in \mathrm{M}_n(F)$. 如果$\chi_A$在$F$中有$n$个不同的根，则$A$可对角化

> [!Note] 判断重根的技巧
> 对于一个多项式$f\in \mathbb{C}[t]$或者$f\in \mathbb{R}[t]$，如果$\gcd(f,f') = 1$则说明$f$没有重根。因为如果$f$有重根$a$，可以把$f$写成$f=(t-a)^2g$，则$f'$必然有$(t-a)$因子，二者不可能互素

**需要注意的是，如果出现重根，则需要讨论对应$V^\lambda$的维数，也就是要考虑其他判别法了**
## 特征子空间的和（充要）
设$\mathcal A \in \mathcal{L}(V)$且
$$
\mathrm{spec}_F(\mathcal A) = \{\lambda_1, \cdots, \lambda_k\}
$$
则$\mathcal A$可对角化当且仅当$V = V^{\lambda_1} + \cdots + V^{\lambda_k}$
## 特征子空间的维数和（充要）
设$\mathcal A \in \mathcal{L}(V)$且
$$
\mathrm{spec}_F(\mathcal A) = \{\lambda_1, \cdots, \lambda_k\}
$$
则$\mathcal A$可对角化当且仅当$\dim(V) = \dim(V^{\lambda_1}) + \cdots + \dim(V^{\lambda_k})$
## 几何重数等于代数重数（充要）
设$A\in \mathrm{M}_n(F)$, 则$A$可对角化当且仅当
1. $\chi_A(t)$在$F[t]$中可以分解为一次因子之积，即$\chi_A(t)$的所有根都在$F$中（例如如果$F = \mathbb{R}$则$\chi_A(t)$不能有复根）
2. 对任意$\lambda\in \mathrm{spec}_F(A)$，$\lambda$的[[Eigenvectors and Characteristic Polynomial#维数和重数|几何重数]]等于其[[Eigenvectors and Characteristic Polynomial#维数和重数|代数重数]]
## 极小多项式可一次分解
设$\mathcal A\in \mathcal{L}(V)$. 则$\mathcal A$可对角化当且仅当它的[[Minimal Polynomial|极小多项式]]$\mu_\mathcal A(t)$在$F[t]$中可以分解为两两互素一次因子之积
> [!Tip] 当算子或矩阵是通过多项式关系给出时，这个判别法比较容易应用
# 对角化结果
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
P^{-1}AP = \Lambda =\mathrm{diag}(\underbrace{\lambda_1,\ldots,\lambda_1}_{d_1\text{ times}},\underbrace{\lambda_2,\ldots,\lambda_2}_{d_2\text{ times}},\cdots,\underbrace{\lambda_k,\ldots,\lambda_k}_{d_k\text{ times}})
$$
如果要把$A$写成对角形式我们常用
$$
A = P^{-1}\Lambda P
$$
其中$d_i = \dim V^{\lambda_i}$，且若设$\boldsymbol e_1, \ldots,\boldsymbol e_n$是上述直和分解从左往右对应的一组基底，则由[[Linear Operator#矩阵相似|矩阵的基底变换]]可知有
$$
P = (\boldsymbol e_1, \boldsymbol e_2, \ldots, \boldsymbol e_n)
$$
