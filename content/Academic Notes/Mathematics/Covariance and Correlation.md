# Covariance
## Definition
The *covariance* between r.v.s $X$ and $Y$ is
$$
\mathrm{Cov}(X,Y) = \mathrm{E}\left[ (X-\mathrm{E}[X])(Y - \mathrm{E}[Y]) \right] 
$$
Multiplying this out and using linearity, we have an equivalent expression
$$
\mathrm{Cov}(X,Y) = \mathrm{E}[XY] - \mathrm{E}[X] \mathrm{E}[Y]
$$
Think about the definition intuitively: If $X$ and $Y$ tend to move in the same direction, then $X - \mathrm{E}[X]$ and $Y-\mathrm{E}[Y]$ will be positive on average, giving a positive covariance. If $X$ and $Y$ tend to move in opposite directions, then the covariance would to negative.

If $X$ and $Y$ are independent, then their covariance is zero. We say that r.v.s with zero covariance are *uncorrelated*

> [!Warning]
> While independence implies a zero covariance, $X$ and $Y$ are uncorrelated does not mean they are independent. 

For example, let $X \sim \mathcal N(0,1)$, and let $Y = X^{2}$. Then $\mathrm{E}[XY] = \mathrm{E}[X^3]=0$ because the **odd** moments of the standard [[Normal Distribution (Gaussian Distribution)|Normal distribution]] are equal to $0$ by symmetry. Thus
$$
\mathrm{Cov}(X,Y) = \mathrm{E}[XY] - \mathrm{E}[X] \mathrm{E}[Y] = 0
$$
Covariance is a measure of **linear association**, so r.v.s can be dependent in nonlinear ways and still have zero covariance. 
## Property
If $X, T, W, V$ are real-valued random variables and $a, b, c, d$ are real-valued constants we have
1. $\mathrm{Cov}(X, a) = 0$
2. $\mathrm{Cov}(X,X) = \mathrm{Var}(X)$
3. $\mathrm{Cov}(X,Y) = \mathrm{Cov}(Y, X)$
4. $\mathrm{Cov}(X+ a, Y + b) = \mathrm{Cov}(X, Y)$
5. 
$$
\begin{aligned}
\mathrm{Cov}(aX + bY, cW + dV) &= ac\ \mathrm{Cov}(X, W)+ ad\ \mathrm{Cov}(X, V)  \\
&\quad+ bc\ \mathrm{Cov}(Y, W) + bd \ \mathrm{Cov}(Y,V)
\end{aligned}
$$
6. Cauchy-Schwarz Inequality
$$
\mathrm{Cov}(X, Y) \leq \sqrt{ \mathrm{Var}(X) } \sqrt{ \mathrm{Var}(Y) }
$$
this can be proved by
$$
\cos \left< X, Y \right> = \dfrac{\mathrm{E}[XY]}{\sqrt{ \mathrm{E}[X^{2}] }\sqrt{ \mathrm{E}[Y^{2}] }} \leq 1
$$
where we define $\left< X, Y \right> = \mathrm{E}[XY]$ as the [[Euclidean Space#内积的定义|inner product]]
# Correlation
The *correlation* between r.v.s $X$ and $Y$ is
$$
\mathrm{Corr}(X,Y) = \dfrac{\mathrm{Cov}(X,Y)}{\sqrt{ \mathrm{Var}(X) \mathrm{Var}(Y) }}
$$
Therefore, for any r.v.s $X$ and $Y$
$$
-1 \leq \mathrm{Corr}(X,Y) \leq 1
$$

