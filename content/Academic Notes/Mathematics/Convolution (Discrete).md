*Convolution* is a mathematical operation that combines two sequences (or signals) to produce a third sequence. In the discrete case, convolution is commonly used in signal processing, image processing, and various applications in engineering and mathematics.

# Definition
Given two discrete sequences $x[n]$ and $h[n]$, the convolution $y[n]$ of these sequences is defined by the following formula:
$$
y[n] = (x * h)[n] = \sum_{m=-\infty}^{\infty} x[m] h[n - m]
$$
where 
  - $x[n]$ is the input signal or sequence.
  - $h[n]$  is known as the *impulse response* or *kernel*. It defines how the input signal is transformed.
  - $y[n]$ is the resulting convoluted signal that represents the combined output of $x[n]$ and $h[n]$.

Besides, the summation runs over all values of $m$. It essentially slides the sequence $h[n]$ over the sequence $x[n]$ and accumulates the products of overlapping values.
# Properties

1. **Commutative**:
   $$ x * h = h * x $$
2. **Associative**:
   $$ x * (h * g) = (x * h) * g $$
3. **Distributive**:
   $$ x * (h + g) = (x * h) + (x * g) $$
4. **Identity**:
   If $h[n]$ is the delta function $\delta[n]$, then:
   $$ x * \delta[n] = x[n] $$

# Example

Let's consider a simple example with sequences:
- $x[n] = [1, 2, 3]$ (which can be expressed as $x[0] = 1, x[1] = 2, x[2] = 3$)
- $h[n] = [0.5, 1]$ (with $h[0] = 0.5, h[1] = 1$)

We can compute $y[n]$:
$$
\begin{align*}
y[0] & = x[0]h[0] = 1 \cdot 0.5 = 0.5 \\
y[1] & = x[0]h[1] + x[1]h[0] = 1 \cdot 1 + 2 \cdot 0.5 = 1 + 1 = 2 \\
y[2] & = x[1]h[1] + x[2]h[0] = 2 \cdot 1 + 3 \cdot 0.5 = 2 + 1.5 = 3.5 \\
y[3] & = x[2]h[1] = 3 \cdot 1 = 3 \\
\end{align*}
$$
Thus, the resulting convolution $y[n]$ can be represented as:
$$
y[n] = [0.5, 2, 3.5, 3]
$$

# Application
Convolution is a powerful operation for analyzing the behavior of linear systems and signals. It allows us to understand how an input signal is affected by a system's characteristics (represented by the impulse response). In practical applications, convolution is often implemented using efficient algorithms, especially in digital signal processing, such as the Fast Fourier Transform (FFT).