# Continuous Random Variable
An [[Random Variables#Random Variable|r.v.]] has a *continuous distribution* if its [[Random Variables#Cumulative Distribution Function|CDF]] is [[Differential of Multivariable Functions|differentiable]]. We also allow there to be endpoints (or finitely many points) where the CDF is continuous but not differentiable, as long as the CDF is differentiable everywhere else. A *continuous random variable* is a random with a continuous distribution

Therefore, the [[Random Variables#Probability Mass Function|PMF]] of continuous r.v.s is $0$ everywhere since $P(X = x)$ is the height of a jump in the CDF at $x$, but the CDF of $X$ has no jumps.
# Probability Density Function
For a continuous r.v. $X$ with CDF $F$, the *probability density function (PDF)* of $X$ is the derivative $f$ of the CDF, given by $f(x) = F'(x)$. The *support* of $X$, and of its distribution, is the set of all $x$ where $f(x)>0$

On the other hand, we also have
$$
F(x) = \int_{-\infty}^x f(t)\mathrm{d}t
$$

The PDF $f$ of a continuous r.v. must satisfy the following two criteria
- Non-negative: $f(x)\geq0$
- Integrates to $1$: $\int_{-\infty}^\infty f(x) \mathrm{d}x =1$
