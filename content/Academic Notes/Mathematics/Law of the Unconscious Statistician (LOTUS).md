# Idea
Find $\mathrm{E}[g(X)]$ directly using the distribution of $X$ without first having to find the distribution of $g(X)$

# Theorem
If $X$ is a discrete r.v. and $g$ is a function from $\mathbb{R}$ to $\mathbb{R}$, then
$$
\mathrm{E}[g(X)] = \sum_x g(x) P(X = x)
$$
where the sum is taken over all possible values of $X$.

This means that we can get the expected value of $g(X)$ knowing only $P(X=x)$, the [[Random Variables#Probability Mass Function|PMF]] of $X$; we don't need to know the PMF of $g(X)$. 

# Proof
Recall the proof in [[Mathematical Expectation#Intuitive Proof|expectation]], we have
$$
\begin{aligned}
\mathrm{E}[g(X)] &= \sum_s g(X(s)) P(\left\{ s \right\}  ) \\
&= \sum_s \sum_{s : X(s) = x} g(X(s)) P(\left\{ s \right\} ) \\
&= \sum_x g(x) \sum_{s: X(s) = x} P(\left\{ s \right\} ) \\
&= \sum_x g(x ) P(X = x)
\end{aligned}
$$
