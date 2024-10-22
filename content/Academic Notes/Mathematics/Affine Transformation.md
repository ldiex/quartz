# 仿射变换
设$\phi: V \to V$是线性同构, $\boldsymbol v \in V$是一个固定的向量. 映射
$$
\begin{aligned}
\rho: V &\to V \\
\boldsymbol x &\to \phi(\boldsymbol x) + \boldsymbol v
\end{aligned}
$$
称为$V$上一个由$\phi$和$\boldsymbol v$定义的*仿射变换*, 其中$\boldsymbol v$称为$\rho$的*平移向量*

当$\phi$时恒同映射时, $\rho$称为*平移变换*

## 性质
- 仿射变换的复合也是仿射变换
- 仿射变换可逆, 且其逆也是仿射变换

这两点说明$V$上所有仿射变换关于$\circ$构成群

## $\mathbb R^n$上的仿射变换
即
$$
\begin{aligned}
\rho : \mathbb R^n &\to \mathbb R^n \\
\begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix} 
&\to 
A \begin{pmatrix}
x_1 \\ \vdots \\ x_n
\end{pmatrix}
+ \begin{pmatrix}
v_1 \\ 
\vdots \\
v_n
\end{pmatrix}
\end{aligned}
$$
其中$A \in \mathrm{GL}_n(\mathbb R)$



# 二次曲面
设$p \in \mathbb R[x_1, \ldots, x_n]$的次数等于$2$, 其齐$2$次部分记为$h_2$. 把$p$看成$\mathbb R^n$到$\mathbb R$的函数, $h_2$看成相应的二次型. 则存在$\mathbb R^n$上的仿射变换$\rho$使得
$$
\begin{aligned}
p \circ \rho: \mathbb R^n &\to \mathbb R \\
\boldsymbol x = \begin{pmatrix}
x_1 \\ \vdots \\ x_n 
\end{pmatrix} &\to
x_1^2 + \cdots x_k^2 - x_{k + 1}^2 - \cdots - x_{k + l}^2 - \lambda x_{k + l + 1} - \mu
\end{aligned}
$$
其中$(k, l)$是$h_2$的[[Real Quadratic Forms#惯性定理 (Sylvester) | 签名]] , $\lambda \in \{0, 1\}$且$\mu \in \mathbb R$
