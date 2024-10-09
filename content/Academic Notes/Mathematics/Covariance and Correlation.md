# Covariance
The *covariance* between r.v.s $X$ and $Y$ is
$$
\mathrm{Cov}(X,Y) = \mathbb{E}\left[ (X-\mathbb{E}[X])(Y - \mathbb{E}[Y]) \right] 
$$
Multiplying this out and using linearity, we have an equivalent expression
$$
\mathrm{Cov}(X,Y) = \mathbb{E}[XY] - \mathbb{E}[X] \mathbb{E}[Y]
$$
Think about the definition intuitively: If $X$ and $Y$ tend to move in the same direction, then $X - \mathbb{E}[X]$ and $Y-\mathbb{E}[Y]$ will be positive on average, giving a positive covariance. If $X$ and $Y$ tend to move in opposite directions, then the covariance would to negative.

If $X$ and $Y$ are independent, then their covariance is zero. We say that r.v.s with zero covariance are *uncorrelated*

> [!Warning]
> While independence implies a zero covariance, $X$ and $Y$ are uncorrelated does not mean they are independent. 

For example, let $X \sim \mathcal N(0,1)$, and let $Y = X^{2}$. Then $\mathbb{E}[XY] = \mathbb{E}[X^3]=0$ because the **odd** moments of the standard [[Normal Distribution (Gaussian Distribution)|Normal distribution]] are equal to $0$ by symmetry. Thus
$$
\mathrm{Cov}(X,Y) = \mathbb{E}[XY] - \mathbb{E}[X] \mathbb{E}[Y] = 0
$$
Covariance is a measure of **linear association**, so r.v.s can be dependent in nonlinear ways and still have zero covariance. 
# Correlation
The *correlation* between r.v.s $X$ and $Y$ is
$$
\mathrm{Corr}(X,Y) = \dfrac{\mathrm{Cov}(X,Y)}{\sqrt{ \mathrm{Var}(X) \mathrm{Var}(Y) }}
$$
Therefore, for any r.v.s $X$ and $Y$
$$
-1 \leq \mathrm{Corr}(X,Y) \leq 1
$$

