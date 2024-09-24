A *maximum a posteriori probability (MAP) estimate* is an estimate of an unknown quantity, that equals the mode of the posterior distribution.

MAP estimation can be seen as a regularization of [[Maximum Likelihood Estimation (MLE)]]

Assume that we want to estimate an unobserved population parameter $\theta$ on the basis of observations $x$. Let $f$ be the sampling distribution of $x$, so that $f(x|\theta)$ is the probability of $x$ when the underlying population parameter is $\theta$. Then the function
$$
\theta \to f(x | \theta)
$$
is known as the [[Likelihood Function|likelihood function]] and the estimate
$$
\hat{\theta}_{\mathrm{MLE}}(x) = \underset{\theta}{\arg \max} \ f(x |\theta)
$$
is the [[Maximum a Posteriori Probability (MAP)|maximum likelihood estimate]] of $\theta$

Now assume that a prior distribution $g$ over exists. This allows us to treat $\theta$ as a random variable. We can calculate the posterior distribution of $\theta$ using [[Bayes' Theorem]]:
$$
\theta \to f(\theta|x) = \dfrac{f(x|\theta)g(\theta)}{\int_{\Theta} f(x | \vartheta)g(\vartheta) \mathrm{d}\vartheta}
$$
where $g$ is the [[Continuous Random Variables#Probability Density Function|PDF]] of $\theta$, and $\Theta$ is the domain of $g$

The method of maximum a posteriori estimation then estimates $\theta$ as the mode of the posterior distribution of this random variable
$$
\begin{aligned}
\hat{\theta}_\mathrm{MAP}(x) &= \underset{\theta}{\arg \max}\ f(\theta | x) \\
&= \underset{\theta}{\arg \max} \  \dfrac{f(x|\theta)g(\theta)}{\int_{\Theta} f(x | \vartheta)g(\vartheta) \mathrm{d}\vartheta} \\
&= \underset{\theta}{\arg \max} \ f(x |\theta)g(\theta)
\end{aligned}
$$
