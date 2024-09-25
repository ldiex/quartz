# Bernoulli Distribution
An [[Random Variables|r.v.]] $X$ is said to have the *Bernoulli distribution* with parameter $p$ if $P(X = 1)=p$ and $P(X =0) = 1-p$, where $0 < p < 1$. We write this as $X\sim \mathrm{Bern}(p)$. (or $B(1,p)$, $\mathrm{Bin}(1,p)$ as a special case of binomial distribution)

## Bernoulli Trial
An experiment that can result in either a "success" of a "failure" (but not both) is called *Bernoulli trial*. A Bernoulli random variable can be thought of as the *indicator of success* in a Bernoulli trial: it equals $1$ if success occurs and $0$ if failure occurs in the trail.

# Binomial Distribution
Suppose that $n$ **independent** Bernoulli trials are performed, each with the same success probability $p$. Let $X$ be the number of successes. The distribution of $X$ is called the *Binomial distribution* with parameters $n$ and $p$. We write $X \sim \mathrm{Bin}(n,p)$ or $X \sim B(n,p)$ to mean that $X$ has the Binomial distribution with parameters $n$ is $p$, where $n$ is a positive integer and $0 < p < 1$

## Properties
If $X \sim \mathrm{Bin}(n,p)$, then the [[Random Variables#Probability Mass Function|PMF]] of $X$ is
$$
P(X = k) = \binom{n}{k}p^k(1-p)^{n - k}
$$
for $k = 0,1, \ldots ,n$

Let $X \sim \mathrm{Bin}(n,p)$, and $q = 1-p$, then $n - X \sim \mathrm{Bin}(n,q)$

Let $X \sim \mathrm{Bin}(n,p)$ with $p = \dfrac{1}{2}$ and $n$ even. Then the distribution of $X$ is symmetric about $\dfrac{n}{2}$, that is, $P(X = n/2 + j) = P(X = n/2 -j)$ for all nonnegative integers $j$

# Regenerative Property
Let $X_1 \sim \mathrm{Bin}(n,p)$ and $X_2 \sim \mathrm{Bin}(m, p)$, if $X_1$ and $X_2$ are independent, we have $X_1 + X_2 \sim \mathrm{Bin}(n+m, \ p)$. 

To generalize, if $X_i \sim \mathrm{Bin}(n_i,p)$ and $X_1, \ldots ,X_k$ are independent, we can conclude
$$
\sum_{i = 1}^k X_i \sim \mathrm{Bin}\left( \sum_{i= 1}^k n_i,\ p \right) 
$$
# Negative Binomial Distribution (Pascal Distribution)
This distribution models the number of **failures** in a sequence of independent and identically distributed Bernoulli trials **before a specified (non-random) number of successes (denoted $r$) occurs.** 
$$
X \sim \mathrm{NB}(r,p)
$$

The [[Random Variables#Probability Mass function|PMF]] of the negative binomial distribution is
$$
P(X = k) = \binom{k + r - 1}{k} (1-p)^k p^r
$$
