The *Kullback-Leibler (KL) Divergence* (also called *relative entropy*), denoted $D_{\mathrm{KL}}(P \parallel Q)$, is a type of statistical distance, that is, a measure of how one probability distribution $P$ is different from a second, reference probability distribution $Q$. Mathematically, it is defined as 
$$
D_{\mathrm{KL}} (P \parallel Q) = \sum_{x\in \chi} P(x) \log \left( \dfrac{P(x)}{Q(x)} \right) 
$$
To intuitively understand the concept, imagine that we have to biased coins, where coin $A$ has probability $p_1$ for heads and $p_2$ for tails, coin $B$ has probability $q_1$ for heads and $q_2$ for tails. Now we want to know how similar these two coins are.

A straight-forward way to do this is to determine how easy one may confuse these two coins. On the other hand, this means to calculate the likelihood of the coins:
$$
\mathrm{likelihood} = \dfrac{P(\mathrm{Observations} \mid \mathrm{coin} \ A)}{P(\mathrm{Observations} \mid \mathrm{coin} \ B)}
$$
Suppose in a sequence of observations, we observed heads for $N_H$ times and tails for $N_T$ times, then the likelihood function would be
$$
\text{likelihood} = \dfrac{p_1^{N_H}p_2^{N_T}}{q_1^{N_H}q_2^{N_T}}
$$
Normalize the sample size by raising it to the power of $1$ and then take the log of the expression
$$
\begin{aligned}
\log \left(  \dfrac{p_1^{N_H}p_2^{N_T}}{q_1^{N_H}q_2^{N_T}}\right) ^{1/N} &= \dfrac{N_H}{N} \log p_1 + \dfrac{N_T}{N} \log p_2 - \dfrac{N_H}{N} \log q_1 - \dfrac{N_T}{N} \log q_2
\end{aligned}
$$

Assume the observations are generalized by coin $A$, then $\dfrac{N_H}{N} \to p_1$ and $\dfrac{N_T}{N} \to p_2$ when $N \to \infty$, so we get
$$
p_1 \log \dfrac{p_1}{q_1} + p_2 \log \dfrac{p_2}{q_2}
$$
This is exactly the KL-divergence of the two coins' distributions. The closer to $0$ the divergence is, the more similar these two distributions are.


