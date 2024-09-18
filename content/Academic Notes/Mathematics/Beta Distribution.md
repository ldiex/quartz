A [[Continuous Random Variables|continuous r.v.]] $X$ is said to have the *Beta Distribution* with parameters $a$ and $b$, where $a,b >0$, if its [[Continuous Random Variables#Probability Density Function|PDF]] is
$$
f(x) = \frac{1}{\beta(a,b)}x^{a-1}(1-x)^{b-1}, \quad 0 < x < 1
$$
where the constant $\beta(a,b)$ is chosen to make the PDF integrate to $1$. We write this as $X \sim \mathrm{Beta}(a,b)$

By definition, the constant $\beta(a,b)$ satisfies
$$
\beta(a,b) = \int_0^1 x^{a-1}(1-x)^{b-1} \mathrm{d}x
$$
which is the [[Euler Integral#Beta函数|beta function]]
