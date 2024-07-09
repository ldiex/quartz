*Euler's totient function* (also called the *Phi function*) counts the number of positive integers less than $n$ that are coprime to $n$. That is
$$
\phi(n) = \mathrm{card} \left\{ m\in \mathbb{N} \mid 1 \leq m < n \text{ and } \gcd(m,n) = 1 \right\} 
$$
We can calculate $\phi(n)$ via this formula
$$
\phi(n) = n\left( 1-\dfrac{1}{p_1} \right) \left( 1-\dfrac{1}{p_2} \right)\cdots \left( 1-\dfrac{1}{p_k} \right) 
$$
where $p_1,p_2, \ldots ,p_k$ are the distinct primes dividing $n$