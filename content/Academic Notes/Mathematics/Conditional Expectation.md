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
# Conditional Variance
For two r.v.s $X, Y$, we have
$$
\mathrm{Var}[Y] = \mathrm{Var}\left[ \mathrm{E}[Y | X] \right] + \mathrm{ E}\left[ \mathrm{Var}[Y|X] \right] 
$$
> [!Tip]
> The variance of a r.v. is the sum of variance of conditional expectation and the expectation of conditional variance

This is because
$$
\mathrm{Var}[\mathrm{E}[Y|X]] = \mathrm{E[\mathrm{E^{2}[Y|X]}]} - \mathrm{E}^{2}\left[ E[Y | X] \right]  = \mathrm{E}\left[ \mathrm{E}^{2}[Y|X] \right] - \mathrm{E}^{2}[Y]
$$
and
$$
\mathrm{E}\left[ \mathrm{Var}[Y|X] \right] = \mathrm{E}[\mathrm{E}[Y^{2}|X] - \mathrm{E}^{2}[Y|X]] = \mathrm{E}[Y^{2}] - \mathrm{E}^{2}\left[ \mathrm{E}[Y|X] \right] 
$$
Adding the two formulas above gets the result.