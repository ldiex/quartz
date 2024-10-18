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

Another way to calculate expectation for a **non-negative** r.v. $X$ is
$$
\mathrm{E}[X] = \int_0^{+\infty} P(X > t) \mathrm{d}t = \int_0^{+\infty} \left[ 1 - F_X(t) \right]  \mathrm{d}t = \int_0^{+\infty}  G(t) \mathrm{d}t
$$
where $G(x)$ is the [[Survival Function]] of $X$
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
# Expectation of Functions of Random Variables
See [[Law of the Unconscious Statistician (LOTUS)]]

# Conditional Expectation
For two r.v.s $X, Y$, we have
$$
\mathrm{E}[Y] = \mathrm{E}\left[ \mathrm{E}[Y | X] \right] 
$$
This is because
$$
\begin{aligned}
\mathrm{E}[Y]  &= \int_{-\infty}^{\infty} y f_Y(y) \mathrm{d}y \\
&= \int_{-\infty}^\infty y \int_{-\infty}^\infty f(x,y) \mathrm{d}x \mathrm{d}y \\
&= \int_{-\infty}^\infty \int_{-\infty}^\infty y f_{Y|X} f(y|x) f_X(x) \mathrm{d}x \mathrm{d}y\\
&= \int_{-\infty}^\infty f_X(x) \int_{-\infty}^\infty y f_{Y | X}(y|x) \mathrm{d}x \mathrm{d}y \\
&= \int_{-\infty}^\infty f_X(x) \mathrm{E}[Y| X] \mathrm{d}x\\
&= \mathrm{E}\left[ \mathrm{E}[Y|X] \right] 
\end{aligned}
$$
For discrete $X$, this gives
$$
\mathrm{E}[Y] = \sum_{i} P(X_i) \mathrm{E}[Y|X_i]
$$

For two r.v.s $X, Y$, we have
$$
\mathrm{Var}[Y] = \mathrm{Var}\left[ \mathrm{E}[Y | X] \right] + \mathrm{ E}\left[ \mathrm{Var}[Y|X] \right] 
$$
This is because
$$
\mathrm{Var}[\mathrm{E}[Y|X]] = \mathrm{E[\mathrm{E^{2}[Y|X]}]} - \mathrm{E}^{2}\left[ E[Y | X] \right]  = \mathrm{E}\left[ \mathrm{E}^{2}[Y|X] \right] - \mathrm{E}^{2}[Y]
$$
and
$$
\mathrm{E}\left[ \mathrm{Var}[Y|X] \right] = \mathrm{E}[\mathrm{E}[Y^{2}|X] - \mathrm{E}^{2}[Y|X]] = \mathrm{E}[Y^{2}] - \mathrm{E}^{2}\left[ \mathrm{E}[Y|X] \right] 
$$
Adding the two formulas above get the result.