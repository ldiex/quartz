# Definition
The *Dirac Delta Function* $\delta(x)$ is **a quantity that is zero everywhere except at the origin, where it goes to infinity in a manner so as to encompass a unit area**, that is,
$$
\delta(x) = \begin{cases}
0  & x\neq 0 \\
\infty  & x = 0
\end{cases}
$$
and
$$
\int_{-\infty}^{+\infty}\delta(x)\mathrm{d} x = 1
$$

# Physical Background
Many physical phenomena occur over very short durations in time with great intensity, and one is frequently concerned with the consequent response of some system to such stimuli. 

For example: How will a mechanical device, like a billiard ball, respond to being slammed with a hammer? Or how will a particular circuit behave if the input is a short burst of current? In much the same way, we can envision some stimulus that is a sharp pulse in the space, rather than the time, domain. A bright minute source of light embedded in a dark background is essentially a highly localized, two-dimensional, spatial pulse—a spike of irradiance. 

A convenient idealized mathematical representation of this sort of sharply peaked stimulus is the *Dirac delta function*

# Property
## The Sifting Property
Since we can obtain
$$
\int_{-\infty}^{+\infty}\delta(x)f(x)\mathrm{d} x = f(0)
$$
then we have
$$
\int_{-\infty}^{+\infty}\delta(x-x_0)f(x)\mathrm{d} x = f(x_0)
$$

# Two-dimensional Case
$$
\delta(x,y) = \begin{cases}
\infty  & x = y = 0 \\
0  & \text{otherwise}
\end{cases}
$$
and
$$
\int_{-\infty}^{+\infty} \int_{-\infty}^{+\infty}\delta(x,y)\mathrm{d} x \mathrm{d} y= 1
$$
and the sifting property becomes

$$
\int_{-\infty}^{+\infty} \int_{-\infty}^{+\infty}f(x,y)\delta(x-x_0,y-y_0)\mathrm{d} x \mathrm{d} y= f(x_0,y_0)
$$
