# Idea
## Towards Frequency Domain
The *Fourier Transformation* is a mathematical technique that transforms a signal from its *original domain* (often time or space) into a representation in the *frequency domain*. It allows us to break down complex signals into simpler components—specifically, the different frequencies that make up the signal. In essence, the Fourier Transformation **provides a different perspective on the same information**, highlighting the underlying frequency components and their amplitudes.
## High Level Idea
Fourier transformation can be understood as a transformation of coordinates in a *Hilbert space* (A infinite dimensional [[Linear Space|vector space]] equipped with an [[Euclidean Space#$V$上的内积|inner product]]). The general idea is that, every function can be seen as a vector in a infinite dimensional space, and the transformation between functions could be the different representations of a function vector in different coordinates.

### Hilbert Space
A **Hilbert space** is a complete vector space equipped with an inner product. It generalizes the notion of [[Euclidean Space|Euclidean space]] to infinite dimensions and provides the framework for discussing concepts like [[Euclidean Space#正交|orthogonality]], [[Projection|projection]], and more in a rigorous manner. Functions can be elements of a Hilbert space, with operations like addition and scalar multiplication defined **pointwise**.
### Function Space
In the context of Fourier transforms, we typically consider the Hilbert space $L^2(\mathbb{R})$, the space of square-integrable functions. This means functions $f$ such that:
$$
\int_{-\infty}^{\infty} |f(x)|^2 \, dx < \infty
$$
### Coordinate Transformation
The Fourier transform can be viewed as changing the "basis" in this function space from the time (or spatial) domain to the frequency domain. 

In $L^2(\mathbb{R})$, functions are often represented in terms of the **standard basis**, which consists of functions like Dirac delta functions that are localized in space. To simplify this, you could view a function as
$$
\boldsymbol f = \sum_{n = -\infty}^{\infty} f(n) \boldsymbol e_n
$$
where $f(n)$ is the value of $f$ at point $n$, and $\boldsymbol e_n$ is the corresponding standard basis.

Now, if we apply a coordinate transformation $\boldsymbol e_n \to \boldsymbol d_n$, to obtain the representation  of $\boldsymbol f$ in this new space,  we are supposed to calculate its *projection*
$$
f(n)\cdot \boldsymbol d_n = \left< \boldsymbol f, \boldsymbol d_n \right> \boldsymbol {\hat{d}}_n = \int_{-\infty}^{\infty} f(t)d_n(t) \mathrm{d}t\cdot \boldsymbol {\hat{d}}_n
$$
where $\left< \cdot,\ast \right> = \int\cdot \ast \mathrm{d}t$  is the inner product, and then we sum them up
$$
\boldsymbol f = \sum_{n = -\infty}^{\infty} F(n) \boldsymbol{\hat{d}}_n 
$$
where
$$
F(n) = \left< \boldsymbol f,\boldsymbol{d}_n \right>= \int_{-\infty}^{\infty} f(t)d_n(t) \mathrm{d}t
$$

In particular, the Fourier transform projects these functions onto an orthogonal basis of complex exponentials $e^{i \omega x}$. These exponentials are eigenfunctions of the Fourier transform operator and form a complete orthonormal set in $L^2(\mathbb{R})$.
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

# Applications of Fourier Transform
[[Fourier Transform in Optics|Applications of Fourier Transform in Optics]]
[[Fourier Optics|Fourier Optics]]