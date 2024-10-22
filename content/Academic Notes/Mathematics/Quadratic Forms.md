# 定义
设$q: V \to F$是$V$上的二次型, 如果
1. 对于$\forall \boldsymbol v \in V,\; q (\boldsymbol v) = q(- \boldsymbol v)$
2. 对于$\forall \boldsymbol x, \boldsymbol y \in V$
$$
f(\boldsymbol x, \boldsymbol y) = \dfrac{1}{2}(q(\boldsymbol x + \boldsymbol y) - q(\boldsymbol x) - q(\boldsymbol y)) 
$$
是$V$上的[[Bilinear Form#对称双线性型 | 对称双线性型]] (关键是双线性型, 显然是对称的), $f$称为$q$的*配极*, 或者叫做*相伴双线性型*(*associated bilinear form*)

由此定义可知$q(\boldsymbol 0) = 0$

# 基本性质

设$q: V \to F$. 则$q$是二次型当且仅当存在$f \in \mathcal L_2^+(V)$使得$\forall \boldsymbol x \in V, \; q(\boldsymbol x) = f(\boldsymbol x, \boldsymbol x)$. 此时$q$的配极是$f$

这告诉我们二次型可以看做是一个二次齐次多项式, 于是有

设$q$是$V$上的二次型. 则对任意的$\alpha \in F$和$\boldsymbol v \in V, \; q(\alpha \boldsymbol v) = \alpha^2 q(\boldsymbol v)$

# 表示
设$V$的一组基为$\boldsymbol e_1, \cdots, \boldsymbol e_n$, $q$是$V$上的二次型. 则存在唯一的矩阵$A \in \mathrm{SM}_n(F)$使得对于任意的$\boldsymbol x = x_1 \boldsymbol e_1 + \cdots + x_n \boldsymbol e_n$有
$$
q(\boldsymbol x) = (x_1, \cdots, x_n)A\begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix}
$$
这时称矩阵$A$是二次型$q$在基地$\boldsymbol e_1, \cdots, \boldsymbol e_n$下的矩阵. *二次型的秩*就是这个对称矩阵$A$的秩

此时$q$的配极满足
$$
f(\boldsymbol x, \boldsymbol y) = \boldsymbol x^t A \boldsymbol y = \boldsymbol y^t A \boldsymbol x
$$
故二次型的秩和配极的秩相同, **二次型和它的配极（一个对称双线性型）是一一对应的**
## 例子
设$p \in F[x_1, \cdots, x_n]$齐二次, 多项式函数$p:F^n \to F$由公式$p(\boldsymbol v) = p(v_1, \cdots, v_n)$给出, 其中$\boldsymbol v = (v_1, \cdots, v_n)^t$是$F^n$中的任意元素. 则$p$是$F^n$上的二次型

例如, 对于
$$
p = \sum_{1 \le i \le j \le n} \alpha_{i,j} x_i x_j
$$
有
$$
A = \begin{pmatrix}
\alpha_{1, 1} & \dfrac{\alpha_{1,2}}{2} & \cdots & \dfrac{\alpha_{1, n}}{2} \\ 
\dfrac{\alpha_{1, 2}}{2} & \alpha_{2, 2} & \cdots &\dfrac{\alpha_{2, n}}{2} \\
\vdots & \vdots & \ddots & \vdots \\
\dfrac{\alpha_{1, n}}{2} & \dfrac{\alpha_{2, n}}{2}  & \cdots & \alpha_{n,n}
\end{pmatrix}
$$
且
$$
\mathrm{rank}(p) = \mathrm{rank}(A)
$$


# 可一次多项式分解的二次型的秩
设$p\in F[x_1, \ldots, x_n]$非零齐二次. 那么如果$p$可以分解为两个一次多项式之积, 则$p$作为$F^n$上的二次型秩小于$3$

设$p = fg$, 其中$f,g$是$F[x_1, \ldots, x_n]$的齐一次多项式. 令
$$
f = \alpha_1 x_1 + \cdots + \alpha_n x_n, \quad g = \beta_1 x_1 + \cdots + \beta_n x_n
$$
其中$\alpha_1, \ldots, \alpha_n \in F$不全为零, $\beta_1, \ldots, \beta_n \in F$也不全为零. 直接计算$p$作为$F^n$上的二次型矩阵为
$$
\begin{aligned}
A &= \left(\dfrac{\alpha_i\beta_j + \beta_i \alpha_j}{2}\right)_{n \times n} \\
&= \dfrac{1}{2}\begin{pmatrix}\alpha_1 \\ \vdots \\ \alpha_n\end{pmatrix} (\beta_1, \ldots, \beta_n)   + \dfrac{1}{2}\begin{pmatrix}\beta_1 \\ \vdots \\ \beta_n\end{pmatrix} (\alpha_1, \ldots, \alpha_n) 
\end{aligned}
$$
于是
$$
\mathrm{rank}(p) = \mathrm{rank}(A) = \mathrm{rank}(B + C) \le \mathrm{rank}(B) + \mathrm{rank}(C) = 2
$$

# 坐标变换
设$V$的两组基为$\boldsymbol e_1, \ldots, \boldsymbol e_n$和$\boldsymbol e_1', \ldots, \boldsymbol e_n'$且
$$
(\boldsymbol e_1', \dots, \boldsymbol e_n') = (\boldsymbol e_1, \ldots, \boldsymbol e_n) P
$$
其中$P \in \mathrm{GL_n}(F)$ (见 [[General Linear Group]]) 设$V$上的二次型$q$在$\boldsymbol e_1, \ldots, \boldsymbol e_n$和$\boldsymbol e_1', \cdots, \boldsymbol e_n'$下的矩阵分别为$A, B$, 则$B = P^t A P$

设$q$是$V$上的二次型. 则存在$V$的一组基$\epsilon_1, \ldots, \epsilon_n$使得$q$在该基下的矩阵是对角阵. 再设该对角阵为$\mathrm{diag}(\lambda_1, \ldots, \lambda_n)$. 则对任意$\boldsymbol x = x_1 \epsilon_1 + \cdots + x_n \epsilon_n \in V$,
$$
q(\boldsymbol x) = \lambda_1 x_1^2 + \cdots + \lambda_n x_n^2
$$
这时候我们称$\epsilon_1, \ldots, \epsilon_n$是$q$的一组*规范基*, 上述方程称为$q$的一个*规范型*

## 配方法
- 按照$x_1, x_2, \ldots$的顺序依次配方
- 每次需要提出所有含有$x_i^2$和$x_i$的项, 来保证变量替换的可逆性
- 如果没有关于$x_i^2$的项但是有关于$x_i$的项, 则取$j \neq i$, 作换元$y_i = x_i + x_j;y_j = x_i - x_j; y_k = x_k,\; \forall k \neq i,j$之后再配方






