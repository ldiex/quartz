---
zotero-key: WQVV6T6G
zt-attachments:
  - "588"
title: Denoising Diffusion Implicit Models
authors:
  - Jiaming Song
  - Chenlin Meng
  - Stefano Ermon
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2010.02502
DOI: 10.48550/arXiv.2010.02502
---
# Abandon Bayes and Markov
In [[Review DDPM]] and [[Denoising Diffusion Probabilistic Models (DDPM)|DDPM]], to get the distribution $p(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$, we applied [[Bayes' Theorem]]:
$$
p(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0) = \dfrac{p(\boldsymbol x_t | \boldsymbol x_{t-1})p(\boldsymbol x_{t-1}|\boldsymbol x_0)}{p(\boldsymbol x_t| \boldsymbol x_0)}
$$
where we set $p(\boldsymbol x_t | \boldsymbol x_{t-1})$ as a series of [[Normal Distribution (Gaussian Distribution)|Gaussian distribution]], so that we can derive $p(\boldsymbol x_{t-1}|\boldsymbol x_0)$ and $p(\boldsymbol x_{t}|\boldsymbol x_0)$ from it and therefore obtain $p(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$.

The Gaussian we chose for $p(\boldsymbol x_t | \boldsymbol x_{t-1})$ is 
$$
p(\boldsymbol x_t | \boldsymbol x_{t  -1}) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \alpha_t }\boldsymbol x_{t - 1}, \ (1-\alpha_t) \textbf{I})
$$
This transition satisfies [[Markov Property]]. 

In DDIM, we choose a another way to obtain $p(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$ by assuming it as a Gaussian
$$
p(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0) = \mathcal N(\boldsymbol x_{t-1} \mid \kappa_t \boldsymbol x_t + \lambda_t \boldsymbol x_0, \ \sigma_t^{2} \textbf{I})
$$
This is a general form for $p(\boldsymbol x_t|\boldsymbol x_{t-1},\boldsymbol x_0)$, which should satisfy
$$
\int p(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0) p(\boldsymbol x_t|\boldsymbol x_0) \mathrm{d} \boldsymbol x_t = p(\boldsymbol x_{t-1}|\boldsymbol x_0)
$$
Now we could get the form of $p(\boldsymbol x_t|\boldsymbol x_{t-1}, \boldsymbol x_0)$ by setting up $p(\boldsymbol x_t|\boldsymbol x_0)$ and $p(\boldsymbol x_{t-1}|\boldsymbol x_0)$. To reuse the model we trained in DDPM, we remain the same distribution of them
$$
\begin{aligned}
p(\boldsymbol x_{t-1}|\boldsymbol x_0) &= \mathcal N(\boldsymbol x_{t-1} | \sqrt{ \bar{\alpha}_{t-1}} \boldsymbol x_{t - 1}, (1-\bar{\alpha}_{t-1})\textbf{I}) \\
p(\boldsymbol x_t | \boldsymbol x_0) &= \mathcal N(\boldsymbol x_t | \sqrt{ \bar{\alpha}_t} \boldsymbol x_0, (1-\bar{\alpha}_t)\textbf{I}
\end{aligned}
$$
Then we can solve 
$$
\kappa_t = \dfrac{\sqrt{ 1-\bar{\alpha}_{t-1} - \sigma_t^{2}}}{\sqrt{ 1-\bar{\alpha}_{t} }}, \quad \lambda_t = \sqrt{ \bar{\alpha}_{t-1} } - \dfrac{\sqrt{ \bar{\alpha}_t\left( 1-\bar{\alpha}_{t-1} -\sigma_t^{2}\right)  }}{\sqrt{  1- \bar{\alpha}_t }}
$$
So $p(\boldsymbol x_{t-1} | \boldsymbol x_t, \boldsymbol x_0)$ is a set of distributions depend on $\sigma_t^{2}$. If we chose $\sigma_t^{2}$ as the same in DDPM, the $p(\boldsymbol x_{t-1}|\boldsymbol x_t , \boldsymbol x_0)$ will also be the same.

Now, by [[Bayes' Theorem]] we could obtain the forward process $p(\boldsymbol x_t|\boldsymbol x_{t-1}, \boldsymbol x_0)$, which is no longer Markovian as $p(\boldsymbol x_t|\boldsymbol x_{t-1}, \boldsymbol x_0) = p(\boldsymbol x_t | \boldsymbol x_{t-1})$ in DDPM
> [!Tip]
> The general idea of DDIM is, specific $p(\boldsymbol x_t | \boldsymbol x_0)$ and $p(\boldsymbol x_{t-1}|\boldsymbol x_0)$ by $\bar{\alpha}_t$ and $\bar{\alpha}_{t-1}$ to get $p(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$, rather than by defining $p(\boldsymbol x_t|\boldsymbol x_{t-1})$ to get all other distributions in DDPM
# Training and Inference
As same in DDPM, DDIM trains a denoise network $\boldsymbol {\hat{x}}_0 = \boldsymbol {\hat{x}}_{\theta}(\boldsymbol x_t)$ to get $p(\boldsymbol x_{t-1}|\boldsymbol x_t)$ from $p(\boldsymbol x_{t-1}|\boldsymbol x_t , \boldsymbol x_0)$. Since the loss function, as the same in DDPM, does not include $\sigma_t^{2}$, so we can use a pre-trained DDPM model for DDIM inference by changing the value of $\sigma_t^{2}$.

In particular, if we set $\sigma_t^{2} = 0$, the inference process would be determinant, and this is what the **Implicit** in DDIM mean.
# Accelerate Generation
In DDPM, the generative process is considered as the approximation to the reverse process; since of the forward process has $T$ steps, the generative process is also forced to sample $T$ steps.

However, the denoising network we trained in DDPM does not rely on any specific forward procedure. That is, as long as $\boldsymbol x_t$ is fixed by $p(\boldsymbol x_{t}|\boldsymbol x_0)$ with parameter $\bar{\alpha}_t$, the denoising network $\boldsymbol {\hat{x}_0} = \boldsymbol{\hat{x}}_{\boldsymbol \theta,t}(\boldsymbol x_t)$ would work regardless $\boldsymbol x_t$ is sampled from $\boldsymbol x_{t-1}$ or $\boldsymbol x_{t-100}$. Therefore, a DDPM trained for $[1, \ldots ,T]$ includes all the parameters we need for any subsequence $[\tau_1, \ldots ,\tau_S] \subset [1, \ldots ,T]$, and we could build a DDIM model on this new sequence without training a new model.

By this way, we can directly accelerate the generation process to $S$ steps by recalculating $\bar{\alpha}_1, \ldots ,\bar{\alpha}_S$ from $\alpha_{\tau_1}, \ldots ,\alpha_{\tau_S}$. 



