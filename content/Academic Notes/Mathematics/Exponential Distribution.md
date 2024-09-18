The exponential distribution is the continuous counterpart to the [[Geometric and Hypergeometric Distributions#Geometric Distribution|geometric distribution]]. Recall that a geometric random variable counts the number of failures before the first success in a sequence of [[Bernoulli and Binomial Distributions#Bernoulli Trial|Bernoulli trials]]. Likewise, the random variable $x$ below will represent the waiting time until the first arrival of a success which arrives at a rate of $\lambda$ successes per unit of time.

A [[Continuous Random Variables|continuous r.v.]] $X$ is said to have the *exponential distribution* with parameter $\lambda >0$ if its [[Continuous Random Variables#Probability Density Function|PDF]] is
$$
f(x) =\lambda e^{-\lambda x}, \quad x>0
$$
We denote this by $X \sim \mathrm{Expo}(\lambda)$.

The corresponding [[Random Variables#Cumulative Distribution Function|CDF]] is 
$$
F(x) = 1-e^{-\lambda x}, \quad x>0
$$

