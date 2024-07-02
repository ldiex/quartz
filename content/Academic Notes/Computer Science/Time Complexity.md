# Notations
## Big $\Theta$
For function $f(n), g(n)$, $f(n) = \Theta (g(n))$ if and only if $\exists c_1, c_2, n_0 > 0$ s.t. 
$$
\forall n \ge n_0, 0 \le c_1 \cdot g(n) \le f(n) \le c_2 \cdot g(n)
$$
Big $\Theta$ symbol indicates both the upper and lower bound of a time function

## Big $O$
We say $f(n) = O(g(n))$ if and only if $\exists c, n_0$ s.t.
$$
\forall n \ge n_0, 0\le f(n) \le c \cdot g(n)
$$
This gives us the upper bound of a time function.

## Big $\Omega$
We say $f(n) = \Omega(g(n))$ if and only if $\exists c, n_0$, s.t. 
$$
\forall n \ge n_0, 0 < c \cdot g(n) \le f(n)
$$
## Little $o$
We say that $f(n) = o(g(n))$ if and only if for every positive constant $\varepsilon$ there exists a constant $n_0$ such that
$$
\forall n \geq n_0, \left|f(x)\right| \leq \varepsilon g(n)
$$
The difference between the definition of the big-$O$ notation and the definition of little-$o$ is that while the former has to be true for at least one constant $M$, the latter must hold for every positive constant $ε$, however small. That is, $f(x)$ is a **higher order infinitesimal** of $g(x)$

# Complexity Theory
[[P Versus NP Problem]]
[[Complexity Classes]]
[[Master Theorem]]

