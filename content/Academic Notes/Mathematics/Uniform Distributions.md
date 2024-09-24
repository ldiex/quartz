# Discrete Uniform Distribution
Let $C$ be a finite, non-empty set of numbers. Choose one of these numbers uniformly at random (i.e. all values in $C$ are equally likely). Call the chosen number $X$. Then $X$ is said to have the *Discrete Uniform Distribution* with parameter $C$; we denote this by $X \sim \mathrm{DUnif}(C)$

The [[Random Variables#Probability Mass Function|PMF]] of $X \sim \mathrm{DUnif}(C)$ is
$$
P(X = x) = \dfrac{1}{\left|C\right|}
$$
for $x\in C$. Specifically, for $A \subset C$, we have
$$
P(X\in A) = \dfrac{\left|A\right|}{\left|C\right|}
$$
# Continuous Uniform Distribution
A [[Continuous Random Variables|continuous r.v.]] $U$ is said to have the *Uniform Distribution* on the interval $(a,b)$ is its [[Continuous Random Variables#Probability Density Function|PDF]] is
$$
f(x) = \begin{cases}
\frac{1}{b-a}, & \text{if } a < x< b \\
0, &\text{otherwise}
\end{cases}
$$
We denote this by $U \sim \mathrm{Unif}(a,b)$
# Universality of the Uniform
Let $F$ be a [[Random Variables#Cumulative Distribution Function|CDF]] which is a continuous function and strictly increasing on the support of the distribution. This ensures that the inverse function $F^{-1}$ exists, as a function from $(0,1)$ to $\mathbb{R}$. We then have the following results.
1. Let $U \sim \mathrm{Unif}(0,1)$ and $X = F^{-1}(U)$. Then $X$ is an r.v. with CDF $F$.
2. Let $X$ be an r.v. with CDF $F$, then $F(X) \sim \mathrm{Unif}(0,1)$
**Proof**
1. Let $U \sim \mathrm{Unif}(0,1)$ and $X = F^{-1}(U)$. For all real $x$,
$$
P(X \leq x) = P(F^{-1}(U) \leq x) = P( U \leq F(x)) = F(x)
$$
so the CDF of $X$ is F.
2. Let $X$ have CDF $F$, and find the CDF of $Y = F(X)$. Since $Y$ takes values in $(0,1)$, $P(Y \leq y)$ equals $0$ for $y \leq 0$ and equals $1$ for $y \geq 1$. For $y\in(0,1)$
$$
P(Y \leq y) = P(F(X) \leq y) = P(X \leq F^{-1}(y)) = F(F^{-1}(y)) = y
$$
> [!Info]
> To naturally understand these properties, we imagine a large number of students take a certain exam, graded on a scale from $0$ to $100$. Let's approximate the discrete distribution of scores using a continuous distribution, and let $X$ be the score of a random student. Suppose that $X$ is continuous, with a CDF $F$ that is strictly increasing on $(0,100)$
> 
> If Bob scores a $60$ on the exam, and $60$ happens to be the median score of the exam, then we have $F(60) = 1/2$, or equivalently, $F^{-1}(1/2)=60$
> 
> If Fred scores a $72$ on the exam, then his *percentile* is the fraction of students who score below a $72$. This is $F(72)$, which is some number in $(1/2,1)$. In general, a student with score $x$ has percentile $F(x)$. Going the other way, if we start with a percentile, say $0.95$, then $F^{-1}(0.95)$ is the score that has that percentile. A percentile is also called a *quantile*, which is why $F^{-1}$ is called the *quantile function*.
> 
> The strange operation of plugging $X$ into its own CDF now has a natural interpretation: **$F(X)$ is the percentile attained by a random student**. It often happens that the distribution of scores on an exam looks very non-Uniform. And on the other hand, the distribution of *percentiles* of the students is Uniform: the universality property says that $F(X) \sim \mathrm{Unif}(0,1)$


