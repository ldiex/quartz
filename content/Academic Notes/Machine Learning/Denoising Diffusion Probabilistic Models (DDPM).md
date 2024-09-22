# Overview
Diffusion models are **incremental** updates where the assembly of the whole gives us the encoder-decoder structure. The transition from one state to another is realized by a *denoiser*.

![[AI-DDPM-Arch.png]]
The model whose structure is shown above is called the *variational diffusion model*. The model has a sequence of states $\boldsymbol x_0, \boldsymbol x_1, \ldots , \boldsymbol x_T$
- $\boldsymbol x_0$: the original image, which is the same as $\boldsymbol x$ in [[Variational Auto-Encoder (VAE)|VAE]]
- $\boldsymbol x_T$: the latent variable, which is the same as $\boldsymbol z$ in VAE, and we want to make it [[Normal Distribution (Gaussian Distribution)|Gaussian]]: $\boldsymbol x_T \sim \mathcal N(0, \textbf{I})$
- $\boldsymbol x_1, \ldots ,\boldsymbol x_{T-1}$: the intermediate states, which are also the latent variables, but not white Gaussian
# Building Blocks
## Transition Block
The $t$-th transition block consists of three states $\boldsymbol x_{t-1}, \boldsymbol x_t$ and $\boldsymbol x_{t + 1}$. There are two possible paths to get to state $\boldsymbol x_t$
![[AI-DDPM-Transition-Block.png]]
- The forward transition that goes from $\boldsymbol x_{t - 1}$ to $\boldsymbol x_t$. The associated transition distribution is $p(\boldsymbol x_t | \boldsymbol x_{t - 1})$. That is, we can sample $\boldsymbol x_t$ from $p(\boldsymbol x_t | \boldsymbol x_{t-1})$ for given $\boldsymbol x_{t-1}$. Just like [[Variational Auto-Encoder (VAE)|VAE]], we do not have access to $p(\boldsymbol x_t|\boldsymbol x_{t-1})$, so we will approximate it by a Gaussian $q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t - 1})$
- The reverse transition  goes from $\boldsymbol x_{t + 1}$ to $\boldsymbol x_t$. Again, we never know $p(\boldsymbol x_{t + 1} | \boldsymbol x_t)$ so we use another Gaussian $p_{\boldsymbol \theta}(\boldsymbol x_{t+1}|\boldsymbol x_{t})$ to approximate it
## Initial Block
![[AI-DDPM-Initial-Block.png]]
Just without forward path. 
## Final Block
![[AI-DDPM-Final-Block.png]]
Just without reverse path, and the final variable $\boldsymbol x_T$ should be Gaussian
## Transition Distribution
In a denoising diffusion probabilistic model, the transition distribution $q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t - 1})$ is defined as
$$
q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t  -1}) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \alpha_t }\boldsymbol x_{t - 1}, \ (1-\alpha_t) \textbf{I})
$$
That is, the transition distribution is a Gaussian with mean $\sqrt{ \alpha_t } \boldsymbol x_{t}$ and variance $1-\alpha_t$. The choice of the scaling factor $\sqrt{ \alpha_t}$ is to make sure that the variance magnitude is preserved so that it will not explode and vanish after many iterations

> [!Tip]
> $\sqrt{ \alpha_t }$ and $1-\alpha_t$ are chosen so that the distribution of $\boldsymbol x_t$ will become $\mathcal N(0, \textbf{I})$ when $t$ is large enough.

From this transition distribution, we can obtain how $\boldsymbol x_t$ will be distributed if we are given $\boldsymbol x_0$:
$$
q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \bar{\alpha}_t }\boldsymbol x_0,\ (1-\bar{\alpha}_t) \textbf{I})
$$
where $\bar{\alpha}_t = \prod_{i = 1}^t \alpha_i$

![[AI-DDPM-From-Transition-To-Final.png]]
# Evidence Lower Bound
Like in [[Variational Auto-Encoder (VAE)|VAE]], we need to maximize the [[Evidence Lower Bound (ELBO)|ELBO]] to train the model, the ELBO in variational diffusion model is
$$
\boxed{
\begin{aligned}
\mathrm{ELBO}_{\boldsymbol \phi,\boldsymbol \theta} (\boldsymbol x) &= \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_1 | \boldsymbol x_0)} \left[ \log \underbrace{p_{\boldsymbol \theta}(\boldsymbol x_0 | \boldsymbol x_1)}_{\text{how good the initial block is}} \right]  \\
&\qquad- \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_{T-1}|\boldsymbol x_0)}\left[ \underbrace{\mathbb{D}_\mathrm{KL} \left( q_{\boldsymbol \phi}(\boldsymbol x_{T}|\boldsymbol x_{T-1}) \Vert p(\boldsymbol x_T) \right) }_{\text{how good the final block is}} \right]  \\
&\qquad -\sum_{t = 1}^{T - 1} \mathbb{E}_{q_{\boldsymbol \phi}} (\boldsymbol x_{t - 1}, \boldsymbol x_{t + 1} \vert \boldsymbol x_0) \left[ \underbrace{\mathbb{D}_{\mathrm{KL}} \left( q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t - 1})\ \Vert \  p_{\boldsymbol \theta}(\boldsymbol x_t | \boldsymbol x_{t + 1}) \right) }_{\text{how good the transition blocks are}} \right] 
\end{aligned}
}
$$
The ELBO here consists of three components:
- **Reconstruction**. This term is based on the initial block. We use the log-likelihood $p_{\boldsymbol \theta}(\boldsymbol x_0 | \boldsymbol x_1)$ to measure how good the neural network associated with $p_{\boldsymbol \theta}$ can recover from the latent variable $\boldsymbol x_1$. The expectation is taken with respect to the samples drawn from $q_{\boldsymbol \phi}(\boldsymbol x_1 | \boldsymbol x_0)$ during the encoding process.
- **Prior Matching**. The prior matching term is based on the final block. We use [[Kullback–Leibler Divergence|KL divergence]] to measure the difference between $q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T - 1})$ and $p(\boldsymbol x_T)$. We want how $\boldsymbol x_T$ is generated, $q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T - 1})$, to be as close to our desired $p(\boldsymbol x_T)$, namely $\mathcal N(0, \textbf{I})$, as possible. The samples here are $\boldsymbol x_{T -1}$ which are drawn from $q_{\boldsymbol \phi}(\boldsymbol x_{T - 1} | \boldsymbol x_0)$ because this distribution provides the forward sample generation process.
- **Consistency**. The consistency term is based on the transition blocks, which uses the KL divergence to measure the deviation between the forward path and the reverse path.
## Proof of ELBO
Recall by the definition of [[Evidence Lower Bound (ELBO)|ELBO]], we have
$$
\log p(x) = \mathrm{ELBO}(x) + \mathbb{D}_{\mathrm{KL}}(q_\phi (z|x) \Vert p(z | x)) 
$$
This means that ELBO is an evidence lower bound for $\log p(x)$, and now we try to estimate it. Let's define the notation: $\boldsymbol x_{0:T} = \left\{ \boldsymbol x_0, \ldots ,\boldsymbol x_T \right\}$ means the collection of all state variable from $t = 0$ to $t = T$. We recall that the prior distribution $p(\boldsymbol x)$ is the distribution of the image $\boldsymbol x_0$, so
$$
\begin{aligned}
\log p(\boldsymbol x) &= \log p(\boldsymbol x_0) \\
&= \log \int p(\boldsymbol x_{0:T}) \mathrm{d}\boldsymbol x_{1 : T} \\
&= \log \int p (\boldsymbol x_{0:T}) \dfrac{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)}{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \mathrm{d}\boldsymbol x_{1:T} \\
&= \log \int q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0) \left[ \dfrac{p(\boldsymbol x_{0:T})}{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \right] \mathrm{d}\boldsymbol x_{1 : T} \\
&= \log \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \dfrac{p(\boldsymbol x_{0:T})}{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \right] 
\end{aligned}
$$
With Jensen's inequality, which states that for any random variable $X$ and any concave function $f$, it holds that $f(\mathbb{E}[X]\geq \mathbb{E}[f(X)]$, so we have
$$
\begin{aligned}
\log p(\boldsymbol x) &= \log \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \dfrac{p(\boldsymbol x_{0:T})}{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \right]  \\
&\geq   \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_{0:T})}{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \right]  \\
&= \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_T)p(\boldsymbol x_0 | \boldsymbol x_1) \prod_{t = 2}^T p(\boldsymbol x_{t-1}|\boldsymbol x_t)}{q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T-1})\prod_{t = 1}^{T-1}q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t-1})} \right] \hfill \quad(\text{by Markov property}) \\
&= \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_T)p(\boldsymbol x_0 | \boldsymbol x_1) \color{red}{\prod_{t = 1}^{T-1} p(\boldsymbol x_{t}|\boldsymbol x_{t + 1})}}{q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T-1})\prod_{t = 1}^{T-1}q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t-1})} \right] \hfill \quad(\text{shift} \ t \ \text{to} \ t+1)  \\
&= \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_T)p(\boldsymbol x_0 | \boldsymbol x_1)}{q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T-1})} \right] + \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \prod_{t = 1}^{T-1} \dfrac{p(\boldsymbol x_t | \boldsymbol x_{t + 1})}{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t-1})} \right] 
\end{aligned}
$$
where the first item can be decomposed into two parts:
$$
\begin{aligned}
\mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_T)p(\boldsymbol x_0 | \boldsymbol x_1)}{q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T-1})} \right] &= \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log p(\boldsymbol x_0|\boldsymbol x_1) \right]  \\
&\qquad + \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_T)}{q_{\boldsymbol \phi}(\boldsymbol x_T|\boldsymbol x_{T - 1})} \right]  \\
&= \underbrace{\mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_1| \boldsymbol x_0)} \left[ \log p(\boldsymbol x_0|\boldsymbol x_1) \right]}_{\text{Reconstruction}}  \\
&\qquad- \underbrace{\mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_{T -1}, \boldsymbol x_T| \boldsymbol x_0)} \left[ \mathbb{D}_\mathrm{KL} (q_{\boldsymbol \phi}(\boldsymbol x_{T}| \boldsymbol x_{T-1}) \ \Vert \ p(\boldsymbol x_T)) \right] }_{\text{Prior Matching}}
\end{aligned}
$$
and the second term is
$$
\begin{aligned}
\mathbb{E}_{q_\boldsymbol{\phi}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\prod_{t=1}^{T-1}\frac{p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})}\right]& =\sum_{t=1}^{T-1}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})}\right] \\
&=\sum_{t=1}^{T-1}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1},\boldsymbol{x}_t,\boldsymbol{x}_{t+1}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})}\right]  \\
&=-\underbrace{\sum_{t=1}^{T-1}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1},\boldsymbol{x}_{t+1}|\boldsymbol{x}_0)}\left[\mathbb{D}_{\mathrm{KL}}\left(q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})\|p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})\right)\right]}_{\text{Consistency}}
\end{aligned}
$$
where the last line used:
$$
\begin{aligned}
q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1},\boldsymbol{x}_t,\boldsymbol{x}_{t+1}|\boldsymbol{x}_0) &= q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_t, \boldsymbol x_{t + 1} | \boldsymbol x_{t-1}, \boldsymbol x_{t + 1}, \boldsymbol x_0)\cdot q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_{t + 1}|\boldsymbol x_0) \\
&= q_{\boldsymbol \phi}(\boldsymbol x_t| \boldsymbol x_{t -1}, \boldsymbol x_{t + 1}, \boldsymbol x_0)\cdot q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_{t + 1}|\boldsymbol x_0) \\
&= q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t -1})\cdot q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_{t + 1}|\boldsymbol x_0) \quad \hfill{\text{(by Markov properity)}}
\end{aligned}
$$








