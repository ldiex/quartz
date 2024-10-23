The Multinomial distribution is a generalization of the [[Bernoulli and Binomial Distributions#Binomial Distribution|Binomial]]. Whereas the Binomial distribution counts the successes in a fixed number of trails that can only be categorized as success or failure, the Multinomial distribution keeps track of trials whose outcomes can fall into multiple categories.

Let each of $n$ objects is independently placed into one of $k$ categories. An object is placed into category $j$ with probability $p_j$, where the $p_j$ are non-negative and $\sum_{j = 1}^k p_j$. Let $X_i$ be the number of objects in category $i$, so that $X_1 + \cdots +X_k = n$. Then $\textbf{X} = (X_1, \ldots ,X_k)$ is said to have the *Multinomial distribution* with parameters $n$ and $\boldsymbol p=(p_1, \ldots ,p_k)$. We write this as $\textbf{X} \sim \mathrm{Mult}_k(n, \boldsymbol p)$

Then the joint [[Random Variables#Probability Mass Function|PMF]] of $\textbf{X}$ is
$$
P(X_1=n_1, \ldots ,X_k = n_k) = \dfrac{n!}{n_1!n_2! \cdots n_k!}\cdot p_1^{n_1} p_2^{n_2} \cdots p_k^{n_k}
$$
where $n_1 + n_2 + \cdots + n_k = n$
## Property
- [[Mathematical Expectation|Mean]]: $\mathrm{E}[X_i] = np_i$
- [[Variance]]: $\mathrm{Var}(X_i) = np_i(1-p_i)$
- [[Covariance and Correlation|Covariance]]: $\mathrm{Cov}(X_i, X_j) = -np_ip_j \ (i \neq j)$