# 映射的微分
设$D \subset \mathbb{R}^n$为[[Planar Point Set#开集|开集]]，向量值函数$f:D\to\mathbb{R}^m$写成分量形式为
$$
f(x_1, \ldots, f_n) = (f_1(x_1, \ldots, x_n), \ldots, f_m(x_1, \ldots,x_n))
$$
设$x^0 =(x_1^0, \ldots, x_n^0)\in D$，如果存在$A = (a_{ij})_{m\times n}$使得对于$x^0$附近的点$x$有
$$
\Vert f(x) - \left[ f(x^0)+A\cdot(x-x^0) \right] \Vert = o(\Vert x-x^0\Vert), \quad(x \to x^0)
$$
则称$f$在$x^0$处可微，且[[Linear Map|线性映射]]
$$
\begin{aligned}
\mathrm{d} f(x^0): \mathbb{R}^n \to \mathbb{R}^m  \\
\boldsymbol v \to A\boldsymbol v
\end{aligned}
$$
称为$f$在$x^0$处的*微分*
> [!Tip] 可微$\implies$可导
> 如果$f:D\to \mathbb{R}^m$在$x^0$处可微分，则其分量$f_i\;(1 \le i \le m)$在$x^0$处存在[[Differential of Multivariable Functions#方向导数|方向导数]]，并且有$$A = \left( \dfrac{\partial {f_i}}{\partial {x_j}} (x^0)\right)_{m\times n} $$ 

# Jacobian矩阵
在上面的情况中，还可以定义
$$
Jf = \left( \dfrac{\partial {f_i}}{\partial {x_j}} \right)_{m\times n}
$$
为$f$的*Jacobian矩阵*，当$m = 1$时，$Jf = \nabla f$, 即为$f$的[[Differential of Multivariable Functions#梯度|梯度]]
# 全微分
$$
\mathrm{d} f = \sum_{i = 1}^n \dfrac{\partial {f}}{\partial {x_i}} \mathrm{d} x_i = Jf\cdot(\mathrm{d} x_1, \ldots, \mathrm{d} x_n)^t 
$$
