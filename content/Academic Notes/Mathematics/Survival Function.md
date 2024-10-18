The *survival function* of an [[Random Variables|r.v.]] $X$ with [[Random Variables#Cumulative Distribution Function|CDF]] $F$ is the function $G$ given by $G(x) = 1 - F(x) = P (X >x)$

Let $X$ be a **nonnegative** r.v. Its expectation can be found by integrating its survival function:
$$
\mathrm{E}[X] = \int_0^{\infty} P(X > x) \mathrm{d}x
$$
In the figure below, the area above a certain CDF and below the line $p = 1$ is shaded. We can calculate the area of the shaded region by two ways
1. $\mathrm{Area} = \displaystyle \int_0^1 F^{-1}(p) \mathrm{d} p =\mathrm{E}\left[ F^{-1}(U) \right] = \mathrm{ E[X]}$, where $U \sim \mathrm{Unif}(0,1)$
2. $\mathrm{Area} = \displaystyle \int_0^\infty  \left[ 1 - F(x) \right] \mathrm{d}x = \mathrm{E}[X]$
More about $1$ can be found in [[Uniform Distributions#Universality of the Uniform|the universality of the uniform distribution]]
![[Math-Calculate-Expectation-via-Survival.png]]
