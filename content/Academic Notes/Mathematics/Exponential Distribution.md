# Intuition
The exponential distribution is the continuous counterpart to the [[Geometric and Hypergeometric Distributions#Geometric Distribution|geometric distribution]]. Recall that a geometric random variable counts the number of failures before the first success in a sequence of [[Bernoulli and Binomial Distributions#Bernoulli Trial|Bernoulli trials]]. Likewise, the random variable $x$ below will represent the waiting time until the first arrival of a success which arrives at a rate of $\lambda$ successes per unit of time.
# Definition
A [[Continuous Random Variables|continuous r.v.]] $X$ is said to have the *exponential distribution* with parameter $\lambda >0$ if its [[Continuous Random Variables#Probability Density Function|PDF]] is
$$
f(x) =\lambda e^{-\lambda x}, \quad x>0
$$
We denote this by $X \sim \mathrm{Expo}(\lambda)$.

The corresponding [[Random Variables#Cumulative Distribution Function|CDF]] is 
$$
F(x) = 1-e^{-\lambda x}, \quad x>0
$$
The mean of exponential distribution is $\dfrac{1}{\lambda}$ and the variance is $\dfrac{1}{\lambda^{2}}$
# Memoryless Property
A continuous distribution is said to have the *memoryless property* if a random variable $X$ from that distribution satisfies
$$
P(X \geq s+t \mid X\geq s) = P(X \geq t)
$$
for all $s, t \geq 0$

And this also implies
$$
E(X|X \geq s) = s+ E(X)
$$
We can directly verify that the Exponential distribution has the memoryless property. Let $X \sim \mathrm{Expo}(\lambda)$, then
$$
P(X \geq s+t \mid X \geq s) = \dfrac{P(X \geq s + t)}{P(X \geq s)} = \dfrac{e^{-\lambda(s + t)}}{e^{-\lambda s}} = e^{-\lambda t} = P(X \geq t)
$$
Note that [[Geometric and Hypergeometric Distributions#Geometric Distribution|Geometric distribution]] also has the memoryless property.
> [!Tip]
> On the other hand, if $X$ is a **positive** continuous random variable with the memoryless property, then $X$ has an Exponential distribution

**Proof**. Suppose $X$ is a positive continuous random variable with the memoryless property. Let $F$ be the [[Random Variables#Cumulative Distribution Function|CDF]] of $X$ and $G$ be the *survival function* of $X$, given by $G(x) = 1-F(x)$. The memoryless property says that
$$
G(s + t) = G(s)G(t)
$$
for all $s, t \geq 0$. Putting $s = t$, we have $G(2t)= G(t)^{2}$, and we can generalize it into
$$
G(mt) = G(t)^m
$$
for $m$ a positive integer, Replacing $t$ by $\frac{t}{2}$, similarly
$$
G\left( \frac{t}{n} \right)   = G(t)^{1/n}
$$
for any positive integer $n$. It follows that
$$
G\left( \frac{m}{n}t \right) = \left( G\left( \frac{t}{n} \right) \right) ^m = G(t)^{m/n}
$$
for all positive rational numbers $x$. Any positive real number can be written as a limit of positive numbers so, using the fact that $G$ is a continuous function, the above equation holds for all positive real numbers $x$. Taking $t=1$, we have
$$
G(x) = G(1)^x = e^{\lambda x}
$$
where $\lambda = -\log(G(1))>0$, so $X$ has an Exponential distribution.



