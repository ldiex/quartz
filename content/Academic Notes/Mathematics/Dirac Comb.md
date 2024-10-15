# Geometric Series of Exponentials
To calculate the sum $\displaystyle \sum_{k=-\infty}^{\infty} \exp(-j\omega k T)$, let $r = \exp(-j\omega T)$, and then our series can be written as $\displaystyle \sum_{k=-\infty}^{\infty} r^k$. We can split this into two parts:
$$
\displaystyle \sum_{k=-\infty}^{\infty} r^k = \displaystyle \sum_{k=-\infty}^{-1} r^k + r^0 + \displaystyle \sum_{k=1}^{\infty} r^k
$$
The right-hand sum $\displaystyle \sum_{k=1}^{\infty} r^k$ is a geometric series with first term $a=r$ and common ratio $r$. The sum of this series (if $|r| < 1$) is $\displaystyle \sum_{k=1}^{\infty} r^k = \frac{r}{1-r}$. Similarly, the left-hand sum is $\displaystyle \sum_{k=1}^{\infty} (r^{-1})^k = \frac{r^{-1}}{1-r^{-1}} = \frac{1}{r-1}$. Putting it all together:
$$
\displaystyle \sum_{k=-\infty}^{\infty} r^k = \frac{1}{r-1} + 1 + \frac{r}{1-r} = 0
$$
This result is valid when $r \neq 1$, which means $\omega T \neq 2\pi n$ for any integer $n$. When $r = 1$ (i.e., $\omega T = 2\pi n$), the series diverges. This sum can be expressed by the [[Dirac Delta Function]]
$$
\sum_{k=-\infty}^{\infty} \exp(-j\omega k T) = \dfrac{2\pi}{T} \sum_{n=-\infty}^{\infty} \delta\left( \omega - n\frac{2\pi}{T} \right)
$$
The factor $2\pi$ in front of the sum ensures that the integral of each impulse over frequency is unity

This representation is known as the *Dirac comb* or *Shah function*. It's a very important concept in signal processing, sampling theory, and Fourier analysis, as it represents the frequency-domain equivalent of a periodic impulse train in the time domain.

## Dirac Comb
$$
\operatorname {\text{Ш}} _{\ T}(t)\ :=\sum _{k=-\infty }^{\infty }\delta (t-kT)
$$
## Unit Dirac Comb
$$
\operatorname {\text{Ш}} (t)\ :=\sum _{k=-\infty }^{\infty }\delta (t-k)
$$
and
$$
\operatorname {\text{Ш}} _{\ T}(t) = \dfrac{1}{T}\operatorname {\text{Ш}} \left( \dfrac{t}{T} \right) 
$$

