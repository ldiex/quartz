Tweedie’s Formula states that the true mean of an exponential family distribution, given samples drawn from it, can be estimated by the [[Maximum Likelihood Estimation (MLE)|maximum likelihood estimate]] of the samples (aka empirical mean) plus some correction term involving the score of the estimate.

# Selection Bias
If we have observed a series of $z_i$, where each $z_i \sim \mathcal N(\mu_i, \sigma^{2})$, for $i = 1,2, \ldots ,N$.

Then we select the $m$ **biggest** ones. What can we say about their corresponding $\mu$ values? They will usually be smaller than the selected $z$'s, and this is called the *Selection Bias*
# Tweedie's Formula
Image we sample $\mu$ from a unknown distribution $\mu \sim g(\cdot)$, and then sample the corresponding $z | \mu \sim \mathcal N(\mu, \sigma^{2})$

Now we calculate the [[Joint Distributions#Marginal PDF|marginal PDF]]: $f(z) = \int_{-\infty}^\infty \varphi(z-\mu)g(\mu) \mathrm{d}\mu$, where $\varphi(z) = \dfrac{\exp \left( -\tfrac{1}{2} z^{2}\right)}{\sqrt{ 2\pi }}$ (See [[Normal Distribution (Gaussian Distribution)#Standard Normal Distribution|standard normal distribution]])

Then we use *Tweedie's Formula* to estimate true mean of the observed $z$
$$
\mathbb{E}[\mu|z] = z + \sigma^{2} \frac{ \mathrm{d}  }{ \mathrm{d} z } \left[ \log f(z) \right] 
$$
where
- $z$ is the [[Maximum Likelihood Estimation (MLE)|MLE]] of $\mu$, aka empirical mean
- $\frac{ \mathrm{d}  }{ \mathrm{d} z }\left[ \log f(z) \right]$ is the correction term. If the observed sample lies on one end of the underlying distribution, this term calculate a score to correct the estimation.


