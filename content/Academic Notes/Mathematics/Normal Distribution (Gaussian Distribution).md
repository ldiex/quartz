# Standard Normal Distribution
A [[Continuous Random Variables|continuous r.v.]] $Z$ is said to have the *standard normal distribution* if its [[Continuous Random Variables#Probability Density Function|PDF]] $\varphi$ is given by
$$
\varphi(z) = \frac{1}{\sqrt{ 2\pi }}e^{-z^{2}/2}, \quad -\infty < z <\infty
$$
We write this as $Z \sim \mathcal N(0,1)$ since, as we could obtain $Z$ has mean $0$ and variance $1$

# Normal Distribution
If $Z \sim \mathcal N(0,1)$, then
$$
X = \mu + \sigma Z
$$
is said to have the *normal distribution* with mean $\mu$ and variance $\sigma^{2}$, for any real $\mu$ and $\sigma^{2}$ with $\sigma > 0$. We denote this by $X \sim \mathcal N(\mu, \sigma^{2})$

And the PDF of Normal distribution is
$$
f(x) = \frac{1}{\sqrt{ 2\pi } \sigma} \exp \left[ - \dfrac{(x-\mu)^{2}}{2\sigma^{2}} \right] 
$$
# Multivariate Normal
A $k$-dimensional random vector $\textbf{X} = (X_1, \ldots ,X_k)$ is said to have a *Multivariate Normal (MVN)* distribution if every linear combination of the $X_j$ has a Normal distribution. That is, we require
$$
t_1X_1 + \cdots + t_k X_k
$$
to have a Normal distribution for any constants $t_1, \ldots ,t_k$. If $t_1X_1 + \cdots +t_kX_k$ is a constant, we also consider it to have a Normal distribution with variance $0$. An important special case is $k=2; this distribution is called the *Bivariate Normal (BVN)*

If $(X_1, \ldots ,X_k)$ is MVN, then the [[Joint Distributions#Marginal PDF|marginal distribution]] of $X_i$ is Normal, since we can take $t_i$ to be $1$ and all other $t_j$ to be $0$. However, the converse is false: it is possible to have Normally distributed r.v.s. $X_1, \ldots ,X_k$ such that $(X_1, \ldots ,X_k)$ is not Multivariate Normal.

