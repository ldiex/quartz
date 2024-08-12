The *master theorem for divide-and-conquer recurrences* provides an asymptotic analysis for many recurrence relations that occur in the analysis of divide-and-conquer [[Algorithms|algorithms]].

Consider a problem that can be solved using a recursive algorithm such as the following:
$$
\begin{aligned}
&\textbf{Procedure} \  \mathrm{p}(\text{input } x \text{ of size } n) \\
&\quad \textbf{If }  n <\text{some constant } k \textbf{ then:} \\
&\quad \quad \text{Solve } x \text{ directly without recursion} \\
& \quad \textbf{Else:} \\
& \quad\quad \text{Create } a \text{ subproblems of } x, \text{each having size } \dfrac{n}{b} \\
&\quad \quad \text{Call procedure p recursively on each subproblem} \\
&\quad\quad \text{Combine the results from the subproblems}
\end{aligned}
$$
If each dividing and combining process of size $n$ takes a time of $f(n)$, the runtime of the algorithm can be expressed by the recurrence relation
$$
T(n) = aT(\dfrac{n}{b}) + f(n)
$$
The *master theorem* indicates that, for constants $a \geq 1$ and $b > 1$ with $f$ asymptotically positive, the following statements are true:
- **Case 1**. If $f(n) = O\left( n^{\log_b a-\varepsilon} \right)$ for sone $\varepsilon >0$, Then $T(n) = \Theta \left( n^{\log_b a} \right)$
- **Case 2**. If $f(n) = \Theta \left( n^{\log_b a} \right)$, then $T(n) = \Theta \left( n^{\log_b a} \log n \right)$
- **Case 3**. If $f(n) = \Omega \left( n^{\log_b a + \varepsilon} \right)$ for some $\varepsilon >0$ (and $af\left( \dfrac{n}{b} \right) \leq cf(n)$ for some $c < 1$ for all $n$ sufficiently large), then $T(n) = \Theta(f(n))$
