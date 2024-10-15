# Derive from Fourier Series
## Fourier Series
See [[Fourier Series]] for details, we will directly give its form:
The Fourier series expansion of the function $f$ is
$$
f(x) \sim \dfrac{a_0}{2} + \sum_{n = 1}^{\infty} \left(a_n \cos \dfrac{n\pi x}{l} + b_n \sin \dfrac{n\pi x}{l}\right)
$$
where
$$
\begin{aligned}
a_n &= \dfrac{1}{l}\int_{-l}^l f(x) \cos \dfrac{n\pi x}{l} \mathrm{d} x, \quad n = 0, 1, 2, \cdots \\
b_n &= \dfrac{1}{l}\int_{-l}^l f(x) \sin \dfrac{n\pi x}{l} \mathrm{d} x, \quad n = 1, 2, \cdots
\end{aligned}
$$
## Complex Form of Fourier Series
Using [[Euler's Formula|Euler's formula]], we can derive
$$
\cos \theta = \dfrac{\mathrm{e}^{\mathrm{i}\theta}+\mathrm{e}^{-\mathrm{i}\theta}}{2}, \quad \sin \theta = -\mathrm{i}\left( \dfrac{\mathrm{e}^{\mathrm{i}\theta}-\mathrm{e}^{-\mathrm{i}\theta}}{2} \right) 
$$
Substituting them into the above series expression, assuming the series converges, let $\omega = \dfrac{2\pi}{T} = \dfrac{2\pi}{2l} = \dfrac{\pi}{l}$, we have
$$
\begin{aligned}
f(x) & = \dfrac{a_0}{2} + \sum_{n = 1}^\infty \left( a_n \dfrac{\mathrm{e}^{\mathrm{i}n\omega_0x}+\mathrm{e}^{-\mathrm{i}n\omega_0x}}{2}-\mathrm{{i}}b_n\dfrac{\mathrm{e}^{\mathrm{i}n\omega_0x}-\mathrm{e}^{-\mathrm{i}n\omega_0x}}{2}\right) \\
 & =\dfrac{a_0}{2} + \sum_{n = 1}^\infty \dfrac{1}{2}(a_n - \mathrm{i}b_n) \mathrm{e}^{\mathrm{i}n\omega_0x} + \sum_{n = 1}^\infty \dfrac{1}{2}(a_n + \mathrm{i}b_n)\mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & =\dfrac{a_0}{2} + \sum_{n = 1}^\infty \dfrac{1}{2}(a_n - \mathrm{i}b_n) \mathrm{e}^{\mathrm{i}n\omega_0x} + \sum_{n = -\infty}^{-1} \dfrac{1}{2}(a_{-n} + \mathrm{i}b_{-n})\mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & = \sum_{-\infty}^\infty d_n \mathrm{e}^{\mathrm{i}n\omega_0x}
\end{aligned}
$$
where
$$
d_n = \begin{cases}
\dfrac{1}{2}(a_n - \mathrm{i}b_{-n}),  & n>0 \\
\dfrac{1}{2}a_0,  & n = 0 \\
\dfrac{1}{2}(a_{-n}-\mathrm{i} b_{-n}), & n < 0
\end{cases}
$$
It can be verified that for any value of $n$, $d_n$ can be expressed as
$$
d_n = \dfrac{1}{2l}\int_0^{2l}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x = \dfrac{1}{T}\int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x
$$
where $\omega_0=\dfrac{2\pi}{T}$ is called the *fundamental frequency*, and thus we obtain the complete expression of the complex exponential form Fourier series expansion
$$
f(x) = \sum_{n =-\infty}^{+\infty} \left[ \dfrac{1}{T} \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x}
$$
# Fourier Transform
Fourier series expansion is for **periodic functions**, but in reality, most signals are non-periodic. Non-periodic functions can be viewed as periodic functions with $T\to +\infty$, and when $T = +\infty$, the fundamental frequency $\omega_0$ becomes the differential $\mathrm{d} \omega$, so the summation needs to be converted to an integral
$$
\begin{aligned}
f(x) & = \sum_{n =-\infty}^{+\infty} \left[ \dfrac{1}{T} \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & =  \sum_{n =-\infty}^{+\infty} \left[ \dfrac{\omega_0}{2\pi} \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x} \\
 & = \sum_{n =-\infty}^{+\infty} \left[ \omega \int_0^{T}\mathrm{e}^{-in\omega_0x} f(x) \mathrm{d} x\right] \mathrm{e}^{\mathrm{i}n\omega_0x} 
\end{aligned}
$$
Here we take $\omega = \dfrac{\omega_0}{2\pi}$, let $\omega = \mathrm{d} \omega\to 0$ then we have
$$
f(x)=\frac1{2\pi}\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}e^{-i2\pi\omega x}\cdot f(x)\mathrm{~}\mathrm{d} x\cdot e^{i2\pi\omega x}\mathrm{~}\mathrm{d} \omega 
$$
where
$$
F(\omega) = \int_{-\infty}^{+\infty}e^{-i2\pi\omega x}\cdot f(x)\mathrm{~}\mathrm{d} x
$$
is called the *Fourier transform*, and
$$
f(x)=\frac1{2\pi}\int_{-\infty}^{+\infty}F(\omega)\cdot e^{i2\pi\omega x}\mathrm{~}\mathrm{d} \omega 
$$
is called the *inverse Fourier transform*