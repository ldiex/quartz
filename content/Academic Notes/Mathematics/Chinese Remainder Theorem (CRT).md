Let $n_1, \ldots ,n_k$ be integers greater than $1$, and $N = \prod_{i=1}^k n_i$. If the $n_i$ are pair-wise co-prime, and if $a_1, \ldots ,a_k$  are any integers, then the system
$$
\begin{aligned}
x &\equiv a_1 \pmod{n_1} \\
&\ \ \vdots  \\
x & \equiv a_k \pmod{n_k}
\end{aligned}
$$
has a solution, and any two solutions, say $x_1$ and $x_2$, satisfy $x_1 \equiv x_2 \pmod{N}$

A trivial case is if
$$
\begin{aligned}
x &\equiv a \pmod{n_1} \\
&\ \ \vdots  \\
x & \equiv a \pmod{n_k}
\end{aligned}
$$
then we have $x \equiv a \pmod{N}$

To construct a solution, let $N_i = N/n_i$ be the product of all moduli but one. As the $n_i$ are pair-wise co-prime, $N_i$ and $n_i$ are co-prime. Thus Bezout's identity applies, and there exist integers $M_i$ and $m_i$ such that
$$
M_i N_i + m_i n_i = 1
$$
A solution of the system of congruences is
$$
x = \sum_{i = 1}^k a_i M_i N_i
$$
In fact, as $N_j$ is a multiple of $n_i$ for $i \neq j$, we have
$$
x \equiv a_i M_iN_i \equiv a_i(1-m_in_i) \equiv a_i \pmod{n_i}
$$
> [!Note]
> We can use [[Exgcd - Extended Euclidean Algorithm|extended Euclidean algorithm]] to calculate $M_i$ and $m_i$
