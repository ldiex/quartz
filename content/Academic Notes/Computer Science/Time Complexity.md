# Big $\Theta$
For function $f(n), g(n)$, $f(n) = \Theta (g(n))$ if and only if $\exists c_1, c_2, n_0 > 0$ s.t. 
$$
\forall n \ge n_0, 0 \le c_1 \cdot g(n) \le f(n) \le c_2 \cdot g(n)
$$
Big $\Theta$ symbol indicates both the upper and lower bound of a time function

# Big $O$
We say $f(n) = O(g(n))$ if and only if $\exists c, n_0$ s.t.
$$
\forall n \ge n_0, 0\le f(n) \le c \cdot g(n)
$$
This gives us the upper bound of a time function.

# Big $\Omega$
Way say $f(n) = \Omega(g(n))$ if and only if $\exists c, n_0$, s.t. 
$$
\forall n \ge n_0, 0 < c \cdot g(n) \le f(n)
$$
# Small $o$



