# Geometric Distribution
*Geometric Distribution* is the probability distribution of the number $X$ of [[Bernoulli and Binomial Distributions#Bernoulli Trial|Bernoulli trails]] needed to get one success, [[Random Variables#Discrete Random Variable|supported]] on $X = 1,2, \ldots$

The [[Random Variables#Probability Mass Function|PMF]] of geometric distribution is
$$
P(X = k) = (1-p)^{k-1}p
$$
# Hypergeometric Distribution
The *hypergeometric distribution* describes the probability of $k$ success in $n$ draws, **without** replacement, from a finite population of size $N$ that contains exactly $K$ objects with that feature, wherein each draw is either a success or a failure.
> [!Tip]
> In contrast, the [[Bernoulli and Binomial Distributions#Binomial Distribution|binomial distribution]] describe the probability of $k$ successes in $n$ draws **with** replacement

The PMF of hypergeometric distribution is 
$$
P(X = k) = \dfrac{\binom{N}{k}\binom{N-K}{n-k}}{\binom{N}{n}}
$$



