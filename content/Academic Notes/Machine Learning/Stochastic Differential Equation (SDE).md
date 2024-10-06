# Forward and Backward Updates in Gradient Descent
Recall the equation of a step in [[Gradient Descent|gradient descent]]
$$
\boldsymbol x_i- \boldsymbol x_{i -1} = -\beta_{i -1} \nabla f(\boldsymbol x_{i -1})
$$
And we can rewrite this into
$$
\Delta \boldsymbol x = -\beta \Delta t\cdot \nabla f(\boldsymbol x)
$$
Take $\Delta t \to0$, we will have
$$
\mathrm{d}\boldsymbol x = -\beta \nabla f(\boldsymbol x) \mathrm{d}t
$$
Consider the iteration of the descent procedure. For a quite small step, we have the **forward equation**, it is a ODE
$$
\boldsymbol x_i \approx \boldsymbol x_{i - 1} - \beta\nabla f(\boldsymbol x_{i - 1})  \mathrm{d}t
$$
Similarly, we can write the **reverse equation** (See [[Gradient Ascent|gradient ascent]])
$$
\boldsymbol x_{i - 1} \approx \boldsymbol x_{i -1} + \beta \nabla f(\boldsymbol x_i) \mathrm{d}t
$$
# Stochastic Differential Equation
If we introduce a noise term $\boldsymbol z_t \sim \mathcal N(0, \textbf{I})$ to the gradient descent algorithm, then the ODE will become a stochastic differential equation (SDE). If denote the noise term by $\boldsymbol z(t)$, we will have (treating $\boldsymbol x(t)$ as a continuous function)
$$
\boldsymbol x(t + \Delta t) = \boldsymbol x(t) - \tau \nabla f(\boldsymbol x(t)) + \boldsymbol z(t)
$$
And we define a random process $\boldsymbol w(t)$ such that $\boldsymbol z(t) = \boldsymbol w(t + \Delta t) - \boldsymbol w(t) \approx \frac{ \mathrm{d} \boldsymbol w(t) }{ \mathrm{d} t }\Delta t$ for a very small $\Delta t$. In computation, we can generate $\boldsymbol w(t)$ by integrating $\boldsymbol z(t)$. We can therefore write
$$
\begin{aligned}
\boldsymbol x(t + \Delta) - \boldsymbol x(t) &= -\tau \nabla f(\boldsymbol x(t)) + \boldsymbol w(t + \Delta t) - \boldsymbol w (t) \\
\implies \mathrm{d} \boldsymbol x &= - \tau \nabla f(\boldsymbol x) \mathrm{d}t + \mathrm{d}\boldsymbol w
\end{aligned}
$$
This equation reveals a generic form of the SDE, that is
$$
\boxed{
\mathrm{d} \boldsymbol x = \underbrace{\boldsymbol f(\boldsymbol x, t)}_{\text{drift}} \mathrm{d}t + \underbrace{g(t)}_{\text{diffusion}} \mathrm{d}\boldsymbol w
}
$$
where in terms of physics
- The **drift** coefficient defining how molecules in a closed system would move in the absence of random effects. For the gradient descent algorithm, the drift is defined by the negative gradient of the objective function. That is, we want the solution trajectory to follow the gradient of the objective.
- The **diffusion** coefficient is a scalar function describing how the molecules would randomly walk from one position to another.
# Stochastic Differential Equation for DDPM
We consider the discrete-time [[Denoising Diffusion Probabilistic Models (DDPM)|DDPM]] iteration, for $i =1,2, \ldots ,N$ (check [[Denoising Diffusion Probabilistic Models (DDPM)#Transition Block|this equation]] for details, and here we define $\beta_i = \bar{\alpha}_i$)
$$
\boldsymbol x_i = \sqrt{ 1-\beta_i } \boldsymbol x_{i -1} + \sqrt{ \beta_i } \boldsymbol z_{i-1}, \quad \boldsymbol z_{i -1} \sim \mathcal N(0, \textbf{I})
$$
And this sampling equation can be written as an SDE via
$$
\mathrm{d} \boldsymbol x = \underbrace{- \dfrac{\beta(t)}{2} \boldsymbol x}_{\text{drift}} \mathrm{d}t + \underbrace{\sqrt{ \beta(t) } }_{\text{diffusion}}\mathrm{d}\boldsymbol w
$$
This is because if we define a step size $\Delta t = \dfrac{1}{N}$, and rewrite $\beta_i$ as
$$
\beta_i = \beta \left( \dfrac{i}{N} \right)\cdot \dfrac{1}{N} = \beta(t + \Delta t) \Delta t
$$
where we start by $t = 0$ and $i = 1$. Similarly, we can define
$$
\begin{aligned}
\boldsymbol x_i &= \boldsymbol x\left( \dfrac{i}{N} \right) = \boldsymbol x(t + \Delta t)\\
\boldsymbol z_i &= \boldsymbol z\left( \dfrac{i}{N} \right) = \boldsymbol z(t + \Delta t)
\end{aligned}
$$
Hence, we have
$$
\begin{aligned}
\boldsymbol x_i &= \sqrt{ 1-\beta_i } \boldsymbol x_{i -1} + \sqrt{ \beta_i } \boldsymbol z_{i -1} \\
\implies \boldsymbol x(t + \Delta t) &= \sqrt{ 1 -\beta(t + \Delta t)\cdot \Delta t  } \ \boldsymbol x(t) + \sqrt{ \beta( t + \Delta t)\cdot \Delta t } \  \boldsymbol z(t) \\
\implies \boldsymbol x(t + \Delta t) &\approx \left( 1 - \dfrac{1}{2} \beta(t + \Delta t)\cdot \Delta t \right) \boldsymbol x(t) + \sqrt{ \beta(t + \Delta t)\cdot \Delta t } \ \boldsymbol z(t) \\
\implies \boldsymbol x(t + \Delta t) &\approx \boldsymbol x(t) - \dfrac{1}{2} \beta(t) \Delta t \ \boldsymbol x(t) + \sqrt{ \beta(t) \Delta t} \  \boldsymbol z(t)
\end{aligned}
$$
As $\Delta \to0$, we have
$$
\mathrm{d}\boldsymbol x = -\dfrac{1}{2} \beta(t) \boldsymbol x \mathrm{d}t + \sqrt{ \beta(t) } \mathrm{d}\boldsymbol w
$$
Being able to write the DDPM forward update iteration as an SDE means that **the DDPM estimates can be determined by solving the SDE.** In other words, for an appropriately defined SDE solver, we can throw the SDE into the solver. The solution returned by an appropriately chosen solver will be the DDPM estimate.
