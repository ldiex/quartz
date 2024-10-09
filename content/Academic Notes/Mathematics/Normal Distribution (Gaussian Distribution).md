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
to have a Normal distribution for any constants $t_1, \ldots ,t_k$. If $t_1X_1 + \cdots +t_kX_k$ is a constant, we also consider it to have a Normal distribution with variance $0$. An important special case is $k=2$; this distribution is called the *Bivariate Normal (BVN)*

If $(X_1, \ldots ,X_k)$ is MVN, then the [[Joint Distributions#Marginal PDF|marginal distribution]] of $X_i$ is Normal, since we can take $t_i$ to be $1$ and all other $t_j$ to be $0$. However, **the converse is false**: it is possible to have Normally distributed r.v.s. $X_1, \ldots ,X_k$ such that $(X_1, \ldots ,X_k)$ is not Multivariate Normal.

If $\textbf{X} = (X_1, \ldots ,X_n)$ and $\textbf{Y} = (Y_1, \ldots ,Y_m)$ are Multivariate Normal random vectors with $\textbf{X}$ independent of $\textbf{Y}$, then the concatenated random vector $\textbf{W}=(X_1, \ldots ,X_n,Y_1, \ldots ,Y_m)$ is Multivariate Normal

To specify an MVN random vector $(X_1, \ldots ,X_k)$, we need the parameters as follows:
- the mean vector $(\mu_1, \ldots ,\mu_k)$ where $\mathbb{ E}[X_j] = \mu_j$
- the covariance matrix, which is the $k \times k$ matrix of covariances between components, arranged so that the $(i,j)$ entry is $\mathrm{Cov}(X_i,X_j)$

## Bivariate Normal
Let $(Z,W)$ be BVN with $\mathcal N(0, 1)$ marginals and $\mathrm{Corr}(Z,W) = \rho$. By the definition of Multivariate Normal, any $(Z,W)$ of the form
$$
\begin{aligned}
Z &= aX + bY \\
W &= cX + dY
\end{aligned}
$$
will be Bivariate Normal, where $X,Y$ i.i.d. $\mathcal N(0,1)$. The means are already $0$. Setting the variance qual to $1$ gives
$$
a^{2} + b^{2} = 1, \ c^{2} + d^{2} = 1
$$
Setting the [[Covariance and Correlation#Covariance|covariance]] of $Z$ and $W$ equal to $\rho$ gives $ac + bd = \rho$. There are more unknowns than equations here, and we just need one solution. To simplify, let’s look for a solution with $b = 0$, then we have
$$
\begin{aligned}
Z &= X \\
W &= \rho X + \sqrt{ 1-\rho^{2} } Y
\end{aligned}
$$
Let $\tau = \sqrt{ 1-\rho^{2} }$, we get
$$
\begin{aligned}
X &= Z \\
Y &= -\dfrac{\rho}{\tau} Z + \dfrac{1}{\tau} W
\end{aligned}
$$
By the [[Transformations of Random Variables#Change of Variables|changes of variables]], we have the Jacobian
$$
\frac{ \partial (x,y) }{ \partial (z,w) }  = \begin{pmatrix}
1 & 0 \\
-\dfrac{\rho}{\tau} & \dfrac{1}{\tau}
\end{pmatrix}
$$
which has absolute determinant $\dfrac{1}{\tau}$, therfore
$$
\begin{aligned}
f_{Z,W} (z,w) &= f_{X,Y}(x,y) \cdot \left|\left| \frac{ \partial (x,y) }{ \partial (z,w) } \right|\right| \\
&= \dfrac{1}{\tau} f_X(x) f_Y(y) \\
&= \dfrac{1}{2\pi \tau} \exp \left[ - \dfrac{1}{2} (x^{2}+y^{2}) \right]  \\
&= \dfrac{1}{2\pi \tau} \exp \left\{ -\dfrac{1}{2} \left[ z^{2} + \left( -\dfrac{\rho}{\tau} z + \dfrac{1}{\tau} w \right) ^{2} \right]  \right\}  \\
&= \dfrac{1}{2\pi \tau} \exp \left[ -\dfrac{1}{2\tau^{2}} \left( z^{2} + w^{2} - 2\rho zw \right)  \right] 
\end{aligned}
$$
