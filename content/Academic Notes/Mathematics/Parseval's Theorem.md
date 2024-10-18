# Idea
*Parseval's theorem* usually refers to the result that the [[Fourier Transform]] is **unitary**. That is, the sum (or integral) of the square of a function is equal to the sum (or integral) of the square of its transform.
# General Form
Suppose that $A(x)$ and $B(x)$ are two complex-valued functions on $\mathbb{R}$ of period $2\pi$ that are **square integrable** over intervals of period length, with [[Derive Fourier Transform from Fourier Series#Fourier Series|Fourier Series]]
$$
A(x) = \sum_{n = -\infty}^{\infty} a_n \exp(jnx)
$$
and
$$
B(x) = \sum_{n = -\infty}^{\infty} b_n \exp(jnx)
$$
respectively. Then
$$
\sum_{n = -\infty}^\infty a_n\bar{b}_n = \dfrac{1}{2\pi} \int_{-\pi}^\pi A(x) \overline{B(x)} \mathrm{d}
$$
# In Signal Processing
In [[Signals and Systems]], the theorem is often written as
$$
\int_{-\infty}^{\infty} \left|x(t)\right|^2 \mathrm{d}t = \dfrac{1}{2\pi} \int_{-\infty}^{\infty} \left|X(\omega)\right|^{2} \mathrm{d}\omega
$$
where $X(\omega) = \mathcal F \left\{ x(t) \right\}$ represents the CTFT of $x(t)$.

For discrete time signals, the theorem becomes:
$$
\sum_{n = -\infty}^{\infty} \left|x[n]\right|^{2} = \dfrac{1}{2\pi} \int_{0}^{2\pi} \left|X(\omega)\right|^{2} \mathrm{d}\omega 
$$
where $X(\omega)$ is the [[Fourier Transform#Non-periodic Discrete Function|DTFT]] of $x$.

Alternatively, for the [[Fourier Transform#Periodic Discrete Function|DFT]], the relation becomes
$$
\sum_{n = 0}^{N-1} \left|x[n]\right|^{2} = \dfrac{1}{N} \sum_{k = 0}^{N-1} \left|X[k]\right|^{2}
$$
where $X[k]$ is the DFT of $x[n]$, both of length $N$

And for DFS
$$
\dfrac{1}{N}\sum_{n = 0}^{N-1} \left|x[n]\right|^{2} = \sum_{k = 0}^{N-1} \left|X[k]\right|^{2}
$$