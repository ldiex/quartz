# Intuition
Suppose we have an observable random variable $X$, and we want to find its true distribution $p^*$. This would allow us to generate data by sampling (such as [[Variational Auto-Encoder (VAE)|VAE]]), and estimate probabilities of future events. **In general, it is impossible to find $p^*$ exactly, forcing us to search for a good approximation**

To do this, we define a sufficiently large parametric family $\left\{ p_\theta \right\}_{\theta\in \Theta}$ of distributions (often "nice distributions" such as [[Normal Distribution (Gaussian Distribution)|Gaussian distributions]]), then solve for $\displaystyle \min_{\theta} L(p_{\theta}, p^*)$ for some loss function $L$. One possible way to solve this is by considering small variation from $p_{\theta}$ to $p_{\theta + \delta \theta}$, and solve for $\delta L = L(p_{\theta + \delta \theta}, p^*) - L(p_\theta,p^*) = 0$. This is called the **variational method**
# Variational Bayesian Inference
We consider implicitly parametrized probability distributions, and we define
- A simple distribution $p(z)$ over a latent random variable $Z$. Usually a [[Normal Distribution (Gaussian Distribution)|normal distribution]] or a [[Uniform Distributions|uniform distribution]]
- A family of complicated functions $f_{\theta}$ (such as [[Deep Learning|deep neural network]]) parametrized by $\theta$
- A way to convert any $f_\theta(z)$ into a simple distribution over the observable random variable $X$. For example, let $f_\theta(z) = (f_1(z), f_2(z))$ have two outputs, then we can define the corresponding distribution over $X$ to be the normal distribution $\mathcal N(f_1(z), e^{f_x(z)})$
All these define a family of [[Joint Distributions|joint distribution]] $p_\theta$ over $(X,Z)$. We can sample $(x, z)$ from $p_\theta$ by first sampling $z \sim p_\theta$, and then sample $x$ using $f_\theta(z)$

In other words, we have a generative model for both the observable and the latent. We consider a distribution $p_\theta$ good, if it is a close approximation of $p^*$, namely $p_\theta(X) \approx p^*(X)$

Since the $p^*(X)$ above is over $X$ only, so $p_\theta(X)$ must be derived by marginalizing the latent variable $Z$ away. **However, in general it's impossible to perform the integral $\displaystyle p_\theta(x) = \int p_\theta(x|z)p(z)\mathrm{d}z$, forcing us to perform another approximation**

From [[Bayes' Theorem]] we can know $\displaystyle p_\theta(x) = \dfrac{p_\theta(x | z)p(z)}{p_\theta(z | x)}$. Here, we already know $p_\theta(x | z)$ and $p(z)$, so if we can find a good approximation of $p_\theta(z|x)$, then we can get $p_\theta(x)$. Therefore, we define another distribution family $q_\phi(z | x)$ and use it to approximate $p_\theta(z | x)$.

In Bayesian language, $X$ is the observed **evidence**, and $Z$ is the latent/unobserved. The distribution $p$ over $Z$ is the **prior distribution** over $Z$, $p_\theta(x|z)$ is the [[Likelihood Function|likelihood function]], and $p_\theta(z | x)$ is the **posterior distribution** over $Z$

# Solve the Problem
See [[Evidence Lower Bound (ELBO)]]


