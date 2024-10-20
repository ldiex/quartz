The *variance* of a [[Random Variables|r.v.]] $X$ is
$$
\mathrm{Var}(X) = \mathrm{E} \left[ \left( X - \mathrm{E[X]} \right) ^{2} \right] 
$$
The square root of the variance is called the *standard deviation (SD)*
$$
\mathrm{SD}(X) = \sqrt{ \mathrm{Var}(X)}
$$
With the linearity of [[Mathematical Expectation|expectation]], we have
$$
\mathrm{Var} (X) = \mathrm{E}\left[ X^{2} \right] - \mathrm{E}^{2}[X]
$$
Since $\mathrm{Var}(X) \geq0$, we then have $\mathrm{E} \left[ X^{2} \right] \geq \mathrm{E}^{2}[X]$
# Property
- $\mathrm{Var}(X+c) = \mathrm{Var}(X)$ for any constant $c$
- $\mathrm{Var}(cX) = c^{2} \mathrm{Var}(X)$ for any constant $c$
- If $X$ and $Y$ are independent, then $\mathrm{Var}(X+Y) = \mathrm{Var}(X) + \mathrm{Var}(Y)$
- For any constant $c$, $\mathrm{Var}(X) \leq \mathrm{E}\left[ \left( X-c \right)^{2} \right]$. The equality holds if and only if $c = \mathrm{E}[X]$. This means $\mathrm{E}\left[ (X-c)^{2} \right]$ reaches its minimum when $c = \mathrm{E}[X]$, and the value of this minimum is $\mathrm{Var}(X)$


