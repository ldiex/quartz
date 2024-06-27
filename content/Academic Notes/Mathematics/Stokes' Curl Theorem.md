Let $\Sigma$ be a smooth oriented surface in $\mathbb{R}^3$ with boundary $\delta \Sigma = \Gamma$. If a vector field
$$
\boldsymbol F(x,y,z) = (F_x(x,y,z),\;F_y(x,y,z),\;F_z(x,y,z))
$$
is defined and has continuous first order [[Differential of Multivariable Functions#偏导数|partial derivatives]] in a region containing $\Sigma$, then
$$
\iint_\Sigma (\nabla \times \boldsymbol F)\cdot \mathrm{d} \boldsymbol {\Sigma} = \int_{\delta \Sigma} \boldsymbol F\cdot \mathrm{d}(\boldsymbol \Gamma)
$$where the '$\cdot$' operation stands for the [[Euclidean Space#$V$上的内积|inner product]] on $\mathbb{R}^3$

More explicitly, the equality says that
$$
\begin{aligned}
&\iint_\Sigma \left[ \left( \frac{ \partial F_z }{ \partial y } - \frac{ \partial F_y }{ \partial z }  \right) \mathrm{d}y \mathrm{d}z + \left( \frac{ \partial F_x }{ \partial z } -\frac{ \partial F_z }{ \partial x }  \right) \mathrm{d}z \mathrm{d}x + \left( \frac{ \partial F_y }{ \partial x } - \frac{ \partial F_x }{ \partial y }   \right) \mathrm{d}x \mathrm{d}y  \right] \\  
= &\int_{\delta \Sigma} F_x \mathrm{d}x + F_y \mathrm{d}y + F_z \mathrm{d}z
\end{aligned}
$$

This is actually an extension of [[Multiple Integral#Green公式|Green's theorem]], and similarly if $\Omega$ is a [[Multiple Integral#单联通区域|simply connected]] space in $\mathbb{R}^{3}$, and $\boldsymbol F(x,y,z) = (P(x,y,z),Q(x,y,z),R(x,y,z))$ is a vector field with continuous first order partial derivatives, the following four statements are identical
1. For all smooth, closed curve $L$ in $\Omega$, we have
$$
\oint_L \boldsymbol F\cdot \mathrm{d}\ell = 0
$$
2. For all smooth curve $L$ in $\Omega$, the [[Curve Integral|curve integral]]
$$
\int_L \boldsymbol F\cdot \mathrm{d}\ell
$$
is independent from the integrating path
3. There exists a function $u(x,y,z)$ (or *potential function*) such that
$$
\mathrm{d}u = P \mathrm{d}x + Q \mathrm{d}y + R \mathrm{d}z
$$
which could be attained by
$$
u(A) = u(x,y,z) = \int_{A_0}^{A} \boldsymbol F \mathrm{d} \ell
$$
where $A_0$ is the *reference point*
4. Every point in $\Sigma$ satisfies
$$
\frac{ \partial P }{ \partial y } = \frac{ \partial Q }{ \partial x } ,\;\frac{ \partial Q }{ \partial z } = \frac{ \partial R }{ \partial y },\;\frac{ \partial R }{ \partial x } = \frac{ \partial Q }{ \partial z }  
$$


