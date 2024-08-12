In probability theory, *Hoeffding's inequality* provides **an upper bound on the probability that the sum of bounded independent random variables deviates from its expected value by more than a certain amount.** Hoeffding's inequality was proven by Wassily Hoeffding in 1963

Let $X_1, \cdots , X_n$ be independent random variables such that $\displaystyle a_{i} \le X_{i} \le b_{i}$almost surely. Consider the sum of these random variables
$$
S_n = X_1 + \cdots + X_n
$$
Then Hoeffding's theorem states that, for all $t > 0$
$$
{\begin{aligned}\mathbb{P} \left(S_{n}-\mathbb {E} \left[S_{n}\right]\geq t\right)&\; \leq \exp \left(-{\frac {2t^{2}}{\sum _{i=1}^{n}(b_{i}-a_{i})^{2}}}\right)\\\mathbb{P} \left(\left|S_{n}-\mathbb{E} \left[S_{n}\right]\right|\geq t\right)&\;\leq 2\exp \left(-{\frac {2t^{2}}{\sum _{i=1}^{n}(b_{i}-a_{i})^{2}}}\right)\end{aligned}}
$$


