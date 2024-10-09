The *likelihood function*, parameterized by a (possibly multivariate) parameter $\theta$, is usually defined differently for discrete and continuous probability [[Distributions of Random Variables|distributions]]
# Discrete Case
Let $X$ be a discrete [[Random Variables|random variable]] with [[Random Variables#Probability Mass Function|PMF]] $p$ depending on a parameter $\theta$. Then the function
$$
\mathcal{L}(\theta|x) = p_{\theta}(x) = P_\theta (X = x)
$$
considered as a function of $\theta$, is the *likelihood function*, given the outcome $x$ of the random variable $X$. Sometimes this can be written as $P(X = x| \theta)$.

**The likelihood is the probability that a particular outcome $x$ is observed when the true value of the parameter is $\theta$**.

This should not be confused with $P(\theta|x)$, which is the posterior probability of $\theta$ given the data $x$

## Example
Imagine a coin with a probability of $p_H$ to land heads up, and consider the observing two heads in two tosses ("HH"):
$$
\mathcal{L}(p_H = 0.5 \mid \mathrm{HH}) = P(\mathrm{HH} \mid p_H = 0.5) = 0.5^{2} = 0.25
$$
and also
$$
\mathcal{L}(p_H = 0.3 \mid \mathrm{HH}) = P(\mathrm{HH} \mid p_H = 0.3) = 0.3^{2} = 0.09
$$
# Continuous Case
Let $X$ be a [[Continuous Random Variables|continuous r.v.]] with [[Continuous Random Variables#Probability Density Function|PDF]] $f(x)$ which depends on a parameter $\theta$. Then the function
$$
\mathcal{L}(\theta|x) = f_\theta(x)
$$
considered as a function of $\theta$, is the *likelihood function* (of $\theta$, given the outcome $X = x$).

