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
# Fourier Series as Special Case of Fourier Transform
We define the Forward Fourier Transform as
$$
X(\omega) = \mathcal F\left\{ x(t)  \right\}  = \int_{-\infty}^{\infty} x(t) \exp(-j\omega t) \mathrm{d}t
$$
and the Inverse Fourier Transform as
$$
x(t) = \mathcal F^{-1} \left\{ X(\omega) \right\} = \dfrac{1}{2\pi}\int_{-\infty}^{\infty} X(\omega) \exp(j\omega t) \mathrm{d}\omega
$$
For periodic $x(t)$, assuming $x(t + T) = x(t)$, we can break this integral into a sum of integrals over each period:
$$
X(\omega) = \sum_{k=-\infty}^{\infty} \int_{kT}^{(k+1)T} x(t) \exp(-j\omega t) \mathrm{d}t
$$
Because $x(t)$ is the same over each period, we can factor out the integral over a single period $[0, T]$ or any interval of length $T$:
$$
\begin{aligned}
X(\omega) &= \sum_{k = -\infty}^{\infty} \left( \exp(-j\omega kT) \int_{0}^{T} x(t) \exp(-j\omega t) \mathrm{d}t \right)  \\
 &= \left( \int_0^T x(t) \exp(-j\omega t) \mathrm{d}t \right) \sum_{k=-\infty}^{\infty} \exp(-j\omega k T)
\end{aligned}
$$
where the second term is a [[Dirac Comb#Geometric Series of Exponentials|Dirac comb]] $\displaystyle\dfrac{2\pi}{T} \sum_{n=-\infty}^{\infty} \delta\left( \omega - n\frac{2\pi}{T} \right)$. Therefore
$$
X(\omega) = \dfrac{2\pi}{T} \left( \int_{0}^T x(t) \exp(-j \omega t) \mathrm{d} t \right) \sum_{n = -\infty}^{\infty} \delta \left( \omega - n \dfrac{2\pi}{T} \right) 
$$
Substitute it to the inverse transform
$$
x(t) = \frac{1}{T} \int_{-\infty}^{\infty} \left( \int_{0}^{T} x(\tau) e^{-j\omega \tau} \, d\tau \right) \sum_{n=-\infty}^{\infty} \delta\left(\omega - n\frac{2\pi}{T}\right) e^{j\omega t} \, d\omega
$$
 Since the Dirac delta functions select specific frequencies, we can interchange the sum and the integral
$$
 \begin{aligned}
   x(t) &= \frac{1}{T} \sum_{n=-\infty}^{\infty} \int_{0}^{T} x(\tau) e^{-j n \frac{2\pi}{T} \tau} e^{j n \frac{2\pi}{T} t} \, d\tau \\
   &=\frac{1}{T} \sum_{n=-\infty}^{\infty} e^{j n \frac{2\pi}{T} t} \int_{0}^{T} x(\tau) e^{-j n \frac{2\pi}{T} \tau} \, d\tau
\end{aligned}
$$
 Let's define the coefficients $a_n$ as:

$$
   a_n = \frac{1}{T} \int_{0}^{T} x(\tau) e^{-j n \omega_0 \tau} \, d\tau \quad \text{where} \quad \omega_0 = \frac{2\pi}{T}
$$
Then we get the Fourier Series as a special case of Fourier Transform (we replace $n$ by $k$ here)
$$
x(t)  = \sum_{k = -\infty}^{\infty} a_k \exp \left( jk \omega_0 t \right),\quad \text{where} \ a_k = \dfrac{1}{T} \int_{0}^T x(t)\exp(-jk\omega_0t) \mathrm{d}t
$$

# From Continuous to Discrete
## Non-periodic Discrete Function
Assuming we sampling the function $x(t)$ with a time interval of $\Delta t$, let $t = n \Delta t$. Then the $\mathrm{d}t$ in continuous Fourier transform becomes $\Delta t$, and the new formula will be
$$
X(\omega) = \sum_{n = -\infty}^{\infty} x(n\Delta t) \exp \left( -j\omega n\Delta t \right) \Delta t
$$
This is called discrete-time Fourier transform (DTFT). 

If we set $\Delta t$ to be $1$, we have
$$
X(\omega) =  \sum_{n = -\infty}^\infty x(n) \exp(-j\omega n)
$$
where we can notice that $X(\omega)$ is a periodic since $X(\omega) = X(\omega + 2\pi)$.

Note that $\exp(-j\omega n\Delta t)$ is the Fourier transform of $\delta(t - n \Delta t)$, so we can also define DTFT as
$$
X(\omega) = \mathcal F \left\{  \sum_{n = -\infty}^{\infty} x(n \Delta t) \delta(t - n\Delta t) \right\} 
$$
When $\Delta t = 1$, this is
$$
X(\omega) = \mathcal F \left\{  \sum_{n = -\infty}^{\infty} x(n) \delta(t - n) \right\} 
$$
From this we can get the formula for inverse DFDT when $\Delta t = 1$. Performing the inverse Fourier transform at both sides gives 
$$
\sum_{n = -\infty}^{\infty} x(n) \delta(t - n) = \mathcal F^{-1} \left\{ X(\omega) \right\} = \dfrac{1}{2\pi} \int_{-\infty}^\infty X(\omega) \exp(j\omega t) \mathrm{d} \omega
$$
Sampling from $t = n$, we could have (Nothing that DTFT converts a non-periodic discrete function in time domain to a periodic continuous function in frequency domain, which happens to be the inverse of Fourier series, therefore the inverse of DTFT can be seen as the calculation of Fourier Series)
$$
x[n] = \dfrac{1}{2\pi} \int_0^{2\pi} X(\omega)\exp(j\omega n) \mathrm{d}\omega
$$
## Periodic Discrete Function
If we have $x(t) = x(t + T)$, we can sample $x(t)$ from $[0, T)$ with $N$ points, that is, $T = N \cdot \Delta t$. If we set $\Delta t = 1$, then it gives $T = N$ and $t = n\Delta t = n$. In this way, $t\in[0, T) \implies n\in \left\{ 0,1, \ldots ,N-1 \right\}$. Now we can rewrite the formula of continuous Fourier series (since Fourier series is a special case of Fourier transform for periodic functions) as
$$
a_k = \dfrac{1}{N}  \sum_{n = 0}^{N-1} x(n) \exp \left( -j  k \omega_0 n\right) 
$$
where $\omega_0 = \dfrac{2\pi}{T} = \dfrac{2\pi}{N}$. Similarly, $a_k$ is also periodic since $a_{k + N} = a_k$. This is know as discrete Fourier series (DFS)
$$
x[n] = \dfrac{1}{N}\sum_{k = 0}^{N-1} a_k\exp(jk\omega_0 n)
$$
# See Also
[[Derive Fourier Transform from Fourier Series]]

[[Fourier Analysis in Signals]]
[[Fourier Transform in Optics|Applications of Fourier Transform in Optics]]
[[Fourier Optics|Fourier Optics]]