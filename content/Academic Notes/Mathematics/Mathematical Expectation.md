# Definition
The *expected value* of a discrete [[Random Variables|r.v.]] $X$ whose distinct possible valances are $x_1,x_2, \ldots$ is defined by
$$
\mathrm{E} [X] = \sum_{j = 1}^{\infty} x_j P(X = x_j)
$$
If the support is finite, then this is replaced by a finite sum, and we can also write
$$
\mathrm{E}[X] = \sum_{x} \underbrace{x}_{\text{value}} \underbrace{P(X = x)}_{\text{PMF at }x}
$$
The expectation is **undefined** is $\sum_{j=1}^\infty \left|x_j\right| P(X = x_j)$ diverges.

> [!Tip]
> If $X$ and $Y$ are discrete r.v.s with the same distribution (need not to be independent from each other), then $\mathrm{E}[X] = \mathrm{E}[Y]$

# Linearity of Expectation
For any r.v.s $X, Y$ and any constant $c$,
$$
\begin{aligned}
\mathrm{E}[X + Y] &= \mathrm{E}[X] + \mathrm{E}[Y] \\
\mathrm{E}[cX] &= c \mathrm{E}[X]
\end{aligned}
$$
## Intuitive Proof
Recall $X$ is a function which assigns a real number to every outcome $s$ in the sample space. The r.v. $X$ may assign the same value to multiple sample outcomes. When this happens, out definition of expectation groups all these outcomes together, and whose weight, $P(X = x)$, is the total weight of the constituent outcomes.
![[Math-Expectation-Proof.png]]
If $X(s)$ is the value that $X$ assigns to outcome $s$, we can take the weighted average
$$
\mathrm{E}[X] = \sum_s X(s) P(\left\{ s \right\} )
$$
where $P(\left\{ s \right\})$ is the weight of outcome $s$. So we have
$$
\begin{aligned}
\mathrm{E}[X] + \mathrm{E}[Y] &= \sum_s X(s ) P(\left\{ s \right\} ) + \sum_s Y(s) P(\left\{ s \right\} ) \\
&= \sum_s (X + Y) (s) P(\left\{ s \right\} )\\
&= \mathrm{E} (X + Y)
\end{aligned}
$$
# Expectation of the Product of Independent Random Variables
For independent r.v.s $X_1, \ldots ,X_n$, we have
$$
\mathrm{E}[X_1 \cdots X_n] = \mathrm{E}[X_1] \cdots \mathrm{E}[X_n]
$$
