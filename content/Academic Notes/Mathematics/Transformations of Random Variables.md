# Change of Variables
## In one dimension
Let $X$ be a [[Continuous Random Variables|continuous r.v.]] with PDF $f_X$, and let $Y = g(X)$, where $g$ is [[Differential of Multivariable Functions|differentiable]] and strictly increasing (or strictly decreasing). Then the PDF of $Y$ is given by
$$
f_Y(y) = f_X(x) \left| \frac{ \mathrm{d} x }{ \mathrm{d} y } \right|
$$
where $x = g^{-1}(y)$. The support of $Y$ is all $g(x)$ with $x$ in the support of $X$.
> [!Tip]
> Do not forget specifying the support of $Y$
## General case
Let $\textbf{X} = (X_1, \ldots ,X_n)$ be a continuous random vector with [[Joint Distributions#Joint PDF|joint PDF]] $f_{\textbf{X}}$. Let $g: A_0 \to B_0$ be an **invertible** function, where $A_0$ and $B_0$ are open subsets of $\mathbb{R}^n$, $A_0$ contains the support of $\textbf{X}$, and $B_0$ is the range of $g$.

Let $\textbf{Y}= g(\textbf{X})$. and mirror this by letting $\boldsymbol y = g(\boldsymbol x)$. Since $g$ is invertible, we also have $\textbf{X} = g^{-1} (\textbf{Y})$ and $\boldsymbol x = g^{-1} (\boldsymbol y)$. 

Suppose that all the partial derivatives $\dfrac{ \partial x_i }{ \partial y_i }$ exist and are continuous, so we can form the [[Differential of Mappings#Jacobian矩阵|Jacobian matrix]]
$$
\frac{ \partial \boldsymbol x }{ \partial \boldsymbol y }  = \begin{pmatrix}
\frac{ \partial x_1 }{ \partial y_1 } &\frac{ \partial x_1 }{ \partial y_2 } & \cdots &\frac{ \partial x_1 }{ \partial y_n } \\
\vdots & & & \vdots \\
\frac{ \partial x_n }{ \partial y_1 } &\frac{ \partial x_n }{ \partial y_2 } & \cdots& \frac{ \partial x_n }{ \partial y_n } 
\end{pmatrix}
$$
Also assume that the determinant of this Jacobian matrix is never $0$. Then the joint PDF of $\textbf{Y}$ is
$$
f_{\textbf{Y}} (\boldsymbol y) = f_{\textbf{X}} \left( \boldsymbol g^{-1} (\boldsymbol y) \right) \cdot \left|\left|\frac{ \partial \boldsymbol x }{ \partial \boldsymbol y } \right|\right| \quad \text{for} \ \boldsymbol y\in B_0
$$
This relationship means that
$$
\int_A f_{\textbf{X}}(\boldsymbol x) \mathrm{d}\boldsymbol x = \int_B f_{\textbf{Y}}(\boldsymbol y) \mathrm{d}\boldsymbol y
$$

# Convolution
Let $X \sim f_X(x)$ and $Y \sim f_Y(y)$ are **[[Joint Distributions#Independence of continuous r.v.s|independent]]**, then the [[Continuous Random Variables#Probability Density Function|PDF]] of $Z = X+Y$ is the [[Convolution|convolution]] of $f_X,f_Y$:
$$
g(z) = \int_{-\infty}^{\infty} f_X(x)f_Y(z-x) \mathrm{d}x = \int_{-\infty}^{\infty} f_X(z-x)f_Y(x) \mathrm{d}x
$$
## Regenerative Property of Binomial Distribution
For [[Bernoulli and Binomial Distributions#Binomial Distribution|Binomial Distribution]], let $X \sim \mathrm{Bin}(n,p)$, $Y \sim \mathrm{Bin}(m,p)$, we compute the PDF of $Z = X+Y$
$$
\begin{aligned}
P(Z = z) &= \sum_{x= -\infty}^{\infty} P(X = x)P(Y = z - x) \\
&= \sum_{x = 0}^{z} \binom{n}{x} p^x (1-p)^{n-x} \binom{m}{z-x} p^{z-x} (1-p)^{m-z+x} \\
&=  p^z (1-p)^{m + n - z}\sum_{x = 0}^{z} \binom{n}{x} \binom{m}{z-x} \\
&= p^z (1-p)^{m + n - z} \binom{m+n}{z}
\end{aligned}
$$
Therefore, $Z \sim \mathrm{Bin} (m + n,p)$. This is a [[Convolution (Discrete)|discrete convolution]]
## Regenerative Property of Poisson Distribution
For [[Poisson Distribution]], let $X \sim \mathrm{Pois}(\lambda_1), \ Y \sim \mathrm{Posi}(\lambda_2)$, then if $X,Y$ are independent, we have $X + Y = \mathrm{Pois}(\lambda_1 + \lambda_2)$

> [!Tip]
> By replacing $Y$ by $-Y$, the convolution formula can also be used for $Z = X -Y$

# Product
Let the PDF of $(X,Y)^T$ be $f(x,y)$, then the PDF of $Z = XY$ is
$$
g(z) = \int_{-\infty}^{\infty} \dfrac{1}{\left|x\right|} f\left( x, \dfrac{z}{x} \right) \mathrm{d}x
$$
This is by
$$
\begin{aligned}
P(Z \leq z) &= P\left(   XY \leq z\right)  \\
&= P \left( Y \leq \dfrac{z}{X}, \ X \geq 0 \right)  + P\left( Y\geq \dfrac{z}{X}, \ X \leq0 \right)  \\
&= \int_{0}^{\infty} \int_{-\infty}^{z/x} f(x,y) \mathrm{d}y \mathrm{d}x + \int_{-\infty}^{0} \int_{z/x}^{\infty} f(x,y) \mathrm{d}y \mathrm{d}x
\end{aligned}
$$
Therefore
$$
\begin{aligned}
g(z) = \frac{ \partial  }{ \partial z } P(Z\leq z) &= \int_{0}^{\infty} \dfrac{1}{x}f\left( x, \dfrac{z}{x} \right) \mathrm{d}x - \int_{-\infty}^{0} \dfrac{1}{x} f\left( x, \dfrac{z}{x} \right)  \mathrm{d}x \\
&= \int_{-\infty}^{\infty} \dfrac{1}{\left|x\right|} f\left( x, \dfrac{z}{x} \right)  \mathrm{d}x
\end{aligned}
$$
# Division
Let the PDF of $(X,Y)^T$ be $f(x,y)$, then the PDF of $Z = \dfrac{X}{Y}$ is
$$
g(z) = \int_{-\infty}^{\infty} \left|u\right| f(zu,u) \mathrm{d}u
$$
This is by
$$
\begin{aligned}
P(Z \leq z) &= P\left(  \dfrac{X}{Y} \leq z\right)  \\
&= P(X\leq Yz, \ Y >0) + P(X > Yz, Y <0) \\
&= \int_{0}^{\infty} \int_{-\infty}^{yz} f(x,y) \mathrm{d}x \mathrm{d}y + \int_{-\infty}^{0} \int_{yz}^{\infty} f(x,y) \mathrm{d}x \mathrm{d}y
\end{aligned}
$$
Therefore
$$
\begin{aligned}
g(z) = \frac{ \partial  }{ \partial z } P(Z\leq z) &= \int_{0}^{\infty} y f(yz,y) \mathrm{d}y + \int_{-\infty}^{0} (-y) f(yz, y) \mathrm{d}y \\
&= \int_{-\infty}^{\infty} \left|y\right| f(yz, y) \mathrm{d}y
\end{aligned}
$$
