# Definition
*Convolution* is a mathematical operation used to combine two functions into a third function, expressing how the shape of one is modified by the other. It is widely used in various fields such as signal processing, probability, and differential equations.

The convolution of two functions $f$ and $g$ is defined as:

$$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau) g(t - \tau) \, d\tau
$$

In this integral, $\tau$ is a dummy variable of integration, and $t$ is the variable for which the convolution is being evaluated. The result of the convolution $(f * g)(t)$ depends on $t$ and reflects the amount of overlap between $f(\tau)$ and a time-reversed and shifted version of $g(\tau)$.

# Properties of Convolution

Some key properties of convolution include:

1. **Commutativity**:   $$
   f * g = g * f
   $$
2. **Associativity**:   $$
   (f * g) * h = f * (g * h)
   $$
3. **Distributivity**:   $$
   f * (g + h) = f * g + f * h
   $$
4. **Identity Element**:
   The [[Dirac Delta Function|Dirac Delta Function]] $\delta(t)$ acts as the identity element for convolution:
   $$
   f * \delta = f
   $$
   Moreover, use the *shift property* of $\delta(t)$, we also have
   $$
   f(x) *\delta(x-x_0) = f(x-x_0)
   $$

# Relationship with Fourier Transformation

The convolution operation in the time domain is intimately connected to multiplication in the frequency domain through the [[Fourier Transform|Fourier Transform]]. The Fourier transform $\mathscr{F}$ of a function $f(t)$ is given by:

$$
\mathscr{F}\{f(t)\} = F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-i \omega t} \, dt
$$

One of the most important properties of the Fourier transform is the **Convolution Theorem**, which states:

$$
\mathscr{F}\{f * g\} = \mathscr{F}\{f\} \cdot \mathscr{F}\{g\}
$$

This means that convolution in the time domain corresponds to multiplication in the frequency domain. Conversely, multiplication in the time domain corresponds to convolution in the frequency domain:

$$
\mathscr{F}\{f \cdot g\} = \mathscr{F}\{f\} * \mathscr{F}\{g\}
$$

# Implications
The Convolution Theorem simplifies many calculations, especially in signal processing, by transforming a convolution problem into a multiplication problem, which is typically easier to handle. For example, if $f(t)$ and $g(t)$ are two signals, their convolution $(f * g)(t)$ can be efficiently computed by:

1. Taking the Fourier transforms of $f(t)$ and $g(t)$,
2. Multiplying the resulting transforms,
3. Taking the inverse Fourier transform of the product.

This process leverages the fast Fourier transform (FFT) algorithms for computational efficiency.
