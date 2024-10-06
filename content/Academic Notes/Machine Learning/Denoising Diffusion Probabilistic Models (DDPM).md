# Overview
Diffusion models are **incremental** updates where the assembly of the whole gives us the encoder-decoder structure. The transition from one state to another is realized by a *denoiser*.

![[AI-DDPM-Arch.png]]
The model whose structure is shown above is called the *variational diffusion model* *(VDM)*. The model has a sequence of states $\boldsymbol x_0, \boldsymbol x_1, \ldots , \boldsymbol x_T$
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
In a denoising diffusion probabilistic model, the transition distribution $q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t - 1})$ is defined (**yes, this is defined, not derived by training**) as
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
&= \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_T)p(\boldsymbol x_0 | \boldsymbol x_1) \prod_{t = 2}^T p(\boldsymbol x_{t-1}|\boldsymbol x_t)}{q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T-1})\prod_{t = 1}^{T-1}q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t-1})} \right] \quad \quad(\text{by Markov property}) \\
&= \mathbb{E}_{q_{\boldsymbol \phi} (\boldsymbol x_{1:T}| \boldsymbol x_0)} \left[ \log \dfrac{p(\boldsymbol x_T)p(\boldsymbol x_0 | \boldsymbol x_1) \color{red}{\prod_{t = 1}^{T-1} p(\boldsymbol x_{t}|\boldsymbol x_{t + 1})}}{q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_{T-1})\prod_{t = 1}^{T-1}q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t-1})} \right] \quad \quad(\text{shift} \ t \ \text{to} \ t+1)  \\
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
\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\prod_{t=1}^{T-1}\frac{p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})}\right]& =\sum_{t=1}^{T-1}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})}\right] \\
&=\sum_{t=1}^{T-1}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1},\boldsymbol{x}_t,\boldsymbol{x}_{t+1}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})}\right]  \\
&=-\underbrace{\sum_{t=1}^{T-1}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1},\boldsymbol{x}_{t+1}|\boldsymbol{x}_0)}\left[\mathbb{D}_{\mathrm{KL}}\left(q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1})\|p(\boldsymbol{x}_t|\boldsymbol{x}_{t+1})\right)\right]}_{\text{Consistency}}
\end{aligned}
$$
where the last line used:
$$
\begin{aligned}
q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1},\boldsymbol{x}_t,\boldsymbol{x}_{t+1}|\boldsymbol{x}_0) &= q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_t, \boldsymbol x_{t + 1} | \boldsymbol x_{t-1}, \boldsymbol x_{t + 1}, \boldsymbol x_0)\cdot q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_{t + 1}|\boldsymbol x_0) \\
&= q_{\boldsymbol \phi}(\boldsymbol x_t| \boldsymbol x_{t -1}, \boldsymbol x_{t + 1}, \boldsymbol x_0)\cdot q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_{t + 1}|\boldsymbol x_0) \\
&= q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t -1})\cdot q_{\boldsymbol \phi} (\boldsymbol x_{t - 1}, \boldsymbol x_{t + 1}|\boldsymbol x_0) \quad \quad{\text{(by Markov properity)}}
\end{aligned}
$$
# Rewrite the Consistency Term
If we want to maximize the ELBO above, we need to handle two opposite directions: $q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x _{t-1})$ and $p_{\boldsymbol \theta}(\boldsymbol x_t| \boldsymbol x_{t+1})$ in the consistency and prior matching term. However, we could use [[Bayes' Theorem]] to avoid this:
$$
q(\boldsymbol x_t | \boldsymbol x_{t-1}) = \dfrac{q(\boldsymbol x_{t-1}| \boldsymbol x_t)q(\boldsymbol x_t)}{q(\boldsymbol x_{t-1})} \implies q(\boldsymbol x_t | \boldsymbol x_{t-1}, \boldsymbol x_0) = \dfrac{q(\boldsymbol x_{t-1}| \boldsymbol x_t, \boldsymbol x_0)q(\boldsymbol x_t| \boldsymbol x_0)}{q(\boldsymbol x_{t-1}| \boldsymbol x_0)}
$$
The "$\implies$" step conditions the probability on $\boldsymbol x_0$ since we are primarily concerned with generating the data $\boldsymbol x_0$ in denoising diffusion models. By introducing this conditioning on $\boldsymbol x_0$, we aim to incorporate information about the full data trajectory when estimating $q(\boldsymbol x_t | \boldsymbol x_{t-1}, \boldsymbol x_0)$.
![[AI-DDPM-Rewrite-Consistency.png]]
For diffusion models, the reverse process can now be estimated with a noise predictor that approximates the distribution of $\boldsymbol x_{t-1}$ given $\boldsymbol x_t$. The ELBO maximization will involve minimizing the KL divergence between the learned model $p_{\boldsymbol \theta}$ and the posterior $q_{\boldsymbol \phi}(\boldsymbol x_{t-1} | \boldsymbol x_t, \boldsymbol x_0)$, that is, the new consistency term.

To be specific, starting from the Jenson inequality in section [[Denoising Diffusion Probabilistic Models (DDPM)#Proof of ELBO|Proof of ELBO]] above:
$$
\begin{aligned}
\log p(\boldsymbol{x})& \geq\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_{0:T})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\right] \\
&=\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_T)p(\boldsymbol{x}_0|\boldsymbol{x}_1)\prod_{t=2}^Tp(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_1|\boldsymbol{x}_0)\prod_{t=2}^Tq_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1},\boldsymbol{x}_0)}\right] \\
&=\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_T)p(\boldsymbol{x}_0|\boldsymbol{x}_1)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_1|\boldsymbol{x}_0)}\right]+\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1},\boldsymbol{x}_0)}\right]
\end{aligned}
$$
And now we can apply Bayes' Theorem in the second term
$$
\begin{aligned}
\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_{t-1},\boldsymbol{x}_0)}& =\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{\frac{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_0)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_0)}} \\

&=\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)}\times\prod_{t=2}^T\frac{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_0)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t|\boldsymbol{x}_0)} \\

&=\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)}\times\frac{q_{\boldsymbol{\phi}}(\boldsymbol{x}_1|\boldsymbol{x}_0)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_T|\boldsymbol{x}_0)}
\end{aligned}
$$
Then we could continue the inequality
$$
\begin{aligned}
\log p(\boldsymbol x) &\geq
\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_{0})}\left[\operatorname{log}\frac{p(\boldsymbol{x}_{T})p(\boldsymbol{x}_{0}|\boldsymbol{x}_{1})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1}|\boldsymbol{x}_{0})}\right]+\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_{0})}\left[\operatorname{log}\prod_{t=2}^{T}\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_{t})}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t}|\boldsymbol{x}_{t-1},\boldsymbol{x}_{0})}\right] \\
&=\mathbb{E}_{{q_{{\boldsymbol{\phi}}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_{0})}}\left[\log\frac{p(\boldsymbol{x}_{T})p(\boldsymbol{x}_{0}|\boldsymbol{x}_{1})}{q_{{\boldsymbol{\phi}}}(\boldsymbol{x}_{1}|\boldsymbol{x}_{0})}+\log\frac{q_{{\boldsymbol{\phi}}}(\boldsymbol{x}_{1}|\boldsymbol{x}_{0})}{q_{{\boldsymbol{\phi}}}(\boldsymbol{x}_{T}|\boldsymbol{x}_{0})}\right] \\
&\qquad+\mathbb{E}_{{q_{{\boldsymbol{\phi}}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_{0})}}\left[\log\prod_{t=2}^{T}\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_{t})}{q_{{\boldsymbol{\phi}}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_{t},\boldsymbol{x}_{0})}\right] \\
&=\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_T)p(\boldsymbol{x}_0|\boldsymbol{x}_1)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_T|\boldsymbol{x}_0)}\right]+\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)}\right]
\end{aligned}
$$
Now we have the new ELBO, where
$$
\begin{aligned}
\text{First Term} &= \mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_T)p(\boldsymbol{x}_0|\boldsymbol{x}_1)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_T|\boldsymbol{x}_0)}\right]\\ 
&=\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log p(\boldsymbol{x}_0|\boldsymbol{x}_1)\right]+\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\frac{p(\boldsymbol{x}_T)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_T|\boldsymbol{x}_0)}\right] \\
&=\underbrace{\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_1|\boldsymbol{x}_0)}\left[\log p(\boldsymbol{x}_0|\boldsymbol{x}_1)\right]}_{\text{Reconstruction}}-\underbrace{\mathbb{D}_{\mathrm{KL}}(q_{\boldsymbol{\phi}}(\boldsymbol{x}_T|\boldsymbol{x}_0)\|p(\boldsymbol{x}_T))}_{\text{Prior Matching}}
\end{aligned}
$$
and
$$
\begin{aligned} 
\text{Sencond Term}&=\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{1:T}|\boldsymbol{x}_0)}\left[\log\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)}\right] \\
&=\sum_{t=2}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t,\boldsymbol{x}_{t-1}|\boldsymbol{x}_0)}\log\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)}\\&=-\underbrace{\sum_{t=2}\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{x}_t,\boldsymbol{x}_{t-1}|\boldsymbol{x}_0)}\mathbb{D}_{\mathrm{KL}}(q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)\|p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t))}_{\text{Consistency}}
\end{aligned}
$$
To conclude
$$
\boxed{
\begin{aligned}
\mathrm{ELBO_{\boldsymbol \phi, \boldsymbol \theta}}(\boldsymbol x) &= \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_1 | \boldsymbol x_0)} \left[ \log \underbrace{p_{\boldsymbol \theta}(\boldsymbol x_0 | \boldsymbol x_1)}_{\text{Same Reconstruction}} \right]  \\
&\qquad - \underbrace{\mathbb{D}_\mathrm{KL} \left( q_{\boldsymbol \phi}(\boldsymbol x_T|\boldsymbol x_0) \ \Vert \ p(\boldsymbol x_T) \right)}_{\text{New Prior Matching}} \\
&\qquad -  \sum_{t = 2}^T \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[ \underbrace{\mathbb{D}_{\mathrm{KL} } \left( q_{\boldsymbol \phi}(\boldsymbol x_{t-1} | \boldsymbol x_t, \boldsymbol x_0) \ \Vert \ p_{\boldsymbol \theta}(\boldsymbol x_{t-1} \Vert \boldsymbol x_{t}) \right)}_{\text{New Consistency}}  \right] 
\end{aligned}
}
$$
- **Reconstruction**. The new reconstruction term is the same as before. We are still maximizing the log-likelihood.
- **Prior Matching**. The new prior matching is simplified to the KL divergence between $q_{\boldsymbol \phi}(\boldsymbol x_T | \boldsymbol x_0)$ and $p(\boldsymbol x_T)$. The change is due to the fact that we now condition upon $\boldsymbol x_0$. Thus, there is no need to draw samples from $q_{\boldsymbol \phi}(\boldsymbol x_{T-1}|\boldsymbol x_0)$ and take expectation.
- **Consistency**. The new consistency term is different from the previous one in two ways. Firstly, the running index $t$ starts at $t = 2$ and ends at $t = T$ . Previously it was from $t = 1$ to $t = T − 1$. Accompanied with this is the distribution matching, which is now between $q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$ and $p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_t)$. So, instead of asking a forward transition to match with a reverse transition, we use $q_{\boldsymbol \phi}$ to construct a reverse transition and use it to match with $p_{\boldsymbol \theta}$
# Derivation of the transition distribution given the initial state
Recall the **definition** of $q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)$
$$
q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_{t  -1}) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \alpha_t }\boldsymbol x_{t - 1}, \ (1-\alpha_t) \textbf{I})
$$
and the **transition distribution**
$$
q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \bar{\alpha}_t }\boldsymbol x_0,\ (1-\bar{\alpha}_t) \textbf{I}), \qquad \bar{\alpha}_t = \prod_{i = 1}^t \alpha_i
$$
with how we got $q_{\boldsymbol \phi}(\boldsymbol x_{t-1}| \boldsymbol x_t, \boldsymbol x_0)$ via Bayes' Theorem
$$
q(\boldsymbol x_{t-1} | \boldsymbol x_{t}, \boldsymbol x_0) = \dfrac{q(\boldsymbol x_{t}| \boldsymbol x_{t-1}, \boldsymbol x_0)q(\boldsymbol x_{t-1}| \boldsymbol x_0)}{q(\boldsymbol x_{t}| \boldsymbol x_0)}
$$
Then we get
$$
q(\boldsymbol x_{t-1} | \boldsymbol x_{t}, \boldsymbol x_0) = \dfrac{\mathcal N(\boldsymbol x_t | \sqrt{ \alpha_t} \boldsymbol x_{t - 1}, (1-\alpha_t)\textbf{I}) \mathcal N(\boldsymbol x_{t-1} | \sqrt{ \bar{\alpha}_{t-1}} \boldsymbol x_{t - 1}, (1-\bar{\alpha}_{t-1})\textbf{I})}{\mathcal N(\boldsymbol x_t | \sqrt{ \bar{\alpha}_t} \boldsymbol x_0, (1-\bar{\alpha}_t)\textbf{I})}
$$
Therefore
$$
q(\boldsymbol x_{t-1} | \boldsymbol x_{t}, \boldsymbol x_0) \propto \exp \left\{ \dfrac{(\boldsymbol x_t - \sqrt{ \alpha_t }\boldsymbol x_{t-1})^{2}}{2(1-\alpha_t)} + \dfrac{(\boldsymbol x_{t-1} - \sqrt{ \bar{\alpha}_{t-1} }\boldsymbol x_{0})^{2}}{2(1-\bar{\alpha}_{t-1})} - \dfrac{(\boldsymbol x_t - \sqrt{ \bar{\alpha}_t }\boldsymbol x_0)^{2}}{2(1-\bar{\alpha}_t)}\right\} 
$$
We know the product of Gaussians must also be a Gaussian, thus we just need to find the mean and variance of the product. For simplicity, treat the vectors as scalars. Consider the following mapping:
$$
x = \boldsymbol x_t, \  y = \boldsymbol x_{t -1}, \ z = \boldsymbol {x_0}, \quad a = \alpha_t, \  b= \bar{\alpha}_{t -1}, \ c = \bar{\alpha}_t
$$
Then we need to analyze the function
$$
f(y)=\frac{(x-\sqrt{a}y)^2}{2(1-a)}+\frac{(y-\sqrt{b}z)^2}{2(1-b)}-\frac{(x-\sqrt{c}z)^2}{2(1-c)}
$$
The minimizer of $f(y)$ is the mean of the resulting Gaussian. So, calculate
$$
f'(y)=\frac{1-ab}{(1-a)(1-b)}y-\left(\frac{\sqrt{a}}{1-a}x+\frac{\sqrt{b}}{1-b}z\right)
$$
Setting $f'(y)=0$ yields $\displaystyle y=\frac{(1-b)\sqrt{a}}{1-ab}x+\frac{(1-a)\sqrt{b}}{1-ab}z$. Note that $ab = \bar{\alpha}_t$, so
$$
\boldsymbol{\mu}_q(\boldsymbol{x}_t,\boldsymbol{x}_0)=\frac{(1-\overline{\alpha}_{t-1})\sqrt{\alpha_t}}{1-\overline{\alpha}_t}\boldsymbol{x}_t+\frac{(1-\alpha_t)\sqrt{\overline{\alpha}_{t-1}}}{1-\overline{\alpha}_t}\boldsymbol{x}_0
$$
Similarly, since
$$
f''(y)=\frac{1-ab}{(1-a)(1-b)}=\frac{1-\overline{\alpha}_t}{(1-\alpha_t)(1-{\overline{\alpha}_{t-1}})}
$$
And this gives us
$$
\boldsymbol{\Sigma}_q(t)=\frac{(1-\alpha_t)(1-{\overline{\alpha}_{t-1}})}{1-\overline{\alpha}_t}\mathbf{I}
$$
Now we know the distribution of $q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$
$$
q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0) = \mathcal N(\boldsymbol x_{t -1} \mid \boldsymbol \mu_q (\boldsymbol x_t, \boldsymbol x_0), \ \boldsymbol \Sigma_q(t))
$$
Therefore, we can calculate the ELBO of VDM! Through some boring algebraic calculation (assuming $p_{\boldsymbol \theta}$ as Gaussian):
$$
\begin{aligned}
&\mathbb{D}_{\mathrm{KL}} \left( q_{\boldsymbol \phi}(\boldsymbol x_{t - 1}| \boldsymbol x_t , \boldsymbol x_0) \ \Vert \ p_{\boldsymbol \theta}(\boldsymbol x_{t-1}| \boldsymbol{x}_t) \right)  \\
&=\mathbb{D}_{\mathrm{KL}} \left( \mathcal N(\boldsymbol{x}_{t-1} \mid \boldsymbol \mu_q(\boldsymbol x_t, \boldsymbol x_0), \ \sigma^{2}_q(t)\textbf{I} \ \Vert \ \mathcal N(\boldsymbol{x}_{t-1} \mid \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t),\ \sigma_q^{2}(t) \textbf{I})\right)  \\
&= \dfrac{1}{2\sigma_q^{2}(t)} \Vert \boldsymbol {\mu}_q(\boldsymbol x_t, \boldsymbol x_0) - \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t) \Vert 
\end{aligned}
$$
So we get
$$
\begin{aligned}
\mathrm{ELBO_{ \boldsymbol \theta}}(\boldsymbol x) &= \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_1 | \boldsymbol x_0)} \left[ \log {p_{\boldsymbol \theta}(\boldsymbol x_0 | \boldsymbol x_1)} \right] - \underbrace{\mathbb{D}_\mathrm{KL} \left( q_{\boldsymbol \phi}(\boldsymbol x_T|\boldsymbol x_0) \ \Vert \ p(\boldsymbol x_T) \right)}_{\text{Nothing to train}} \\
&\qquad -  \sum_{t = 2}^T \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[ \dfrac{1}{2\sigma_q^{2}(t)} \Vert \boldsymbol \mu_q(\boldsymbol x_t, \boldsymbol x_0) - \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t) \Vert^{2}  \right] 
\end{aligned}
$$
We don't need to train the second term since each step of $q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$ is fixed so there is no parameters to learn (the $\alpha_t$s are typically **human-designed**), and the $p(\boldsymbol x_T)$ is also fixed as a Gaussian $\mathcal N(0, \textbf{I})$
# Training and Inference
![[AI-DDPM-Forward-Sampling.png]]
In the ELBO we know
$$
\boldsymbol{\mu}_q(\boldsymbol{x}_t,\boldsymbol{x}_0)=\frac{(1-\overline{\alpha}_{t-1})\sqrt{\alpha_t}}{1-\overline{\alpha}_t}\boldsymbol{x}_t+\frac{(1-\alpha_t)\sqrt{\overline{\alpha}_{t-1}}}{1-\overline{\alpha}_t}\boldsymbol{x}_0
$$
But what about $\boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t)$? Like in [[Variational Auto-Encoder (VAE)#Encoder|VAE's encoder]], we could define it as
$$
\underbrace{\boldsymbol{\mu}_{\boldsymbol{\theta}}}_{\text{A Network}}(\boldsymbol{x}_t)\stackrel{\mathrm{def}}{=}\frac{(1-\overline{\alpha}_{t-1})\sqrt{\alpha_t}}{1-\overline{\alpha}_t}\boldsymbol{x}_t+\frac{(1-\alpha_t)\sqrt{\overline{\alpha}_{t-1}}}{1-\overline{\alpha}_t}\underbrace{\widehat{\boldsymbol{x}}_{\boldsymbol{\theta}}(\boldsymbol{x}_t)}_{\text{Another Network}}
$$
where $\boldsymbol {\hat{x}}_{\boldsymbol \theta}$ is a trainable network with parameter $\boldsymbol \theta$. Now we get
$$
\begin{aligned}
\dfrac{1}{2\sigma_q^{2}(t)} \Vert \boldsymbol \mu_q(\boldsymbol x_t, \boldsymbol x_0) - \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t) \Vert^{2} &= \dfrac{1}{2\sigma_q^{2}(t)} \left\Vert \dfrac{(1-\alpha_t)\sqrt{ \bar{\alpha}_{t-1} }}{1-\bar{\alpha}_t} \left( \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol x_0 \right) \right\Vert^{2} \\
&= \dfrac{1}{2\sigma_q^{2}(t)} \dfrac{(1-\alpha_t)^{2} \bar{\alpha}_{t-1}}{(1-\bar{\alpha}_t)^{2}} \Vert \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol x_0 \Vert ^{2}
\end{aligned}
$$
Therefore ELBO can be simplified into
$$
\mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_1 | \boldsymbol x_0)} \left[ \log {p_{\boldsymbol \theta}(\boldsymbol x_0 | \boldsymbol x_1)} \right] - \sum_{t = 2}^T \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[ \dfrac{1}{2\sigma_q^{2}(t)} \dfrac{(1-\alpha_t)^{2} \bar{\alpha}_{t-1}}{(1-\bar{\alpha}_t)^{2}} \Vert \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol x_0 \Vert ^{2} \right] 
$$
The first term is (using $\alpha_0 = 1$ and $\alpha_1 = \bar{\alpha}_1$)
$$
\begin{aligned}
\log {p_{\boldsymbol \theta}(\boldsymbol x_0 | \boldsymbol x_1)} &= \log \mathcal N(\boldsymbol x_0 \mid \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_1), \ \sigma_q^{2}(1)\textbf{I}) \propto -\dfrac{1}{2\sigma^{2}_q(q)} \Vert \boldsymbol\mu_{\boldsymbol \theta}(\boldsymbol x_1) - \boldsymbol x_0 \Vert^{2} \\
&=  -\dfrac{1}{2\sigma^{2}_q(q)} \left \Vert \frac{(1-\overline{\alpha}_{0})\sqrt{\alpha_1}}{1-\overline{\alpha}_1}\boldsymbol{x}_1+\frac{(1-\alpha_1)\sqrt{\overline{\alpha}_{0}}}{1-\overline{\alpha}_1}\boldsymbol{\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_1) - \boldsymbol x_0  \right \Vert^{2} \\
&=  -\dfrac{1}{2\sigma^{2}_q(q)} \left \Vert \frac{(1-\alpha_1)}{1-\overline{\alpha}_1}\boldsymbol{\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_1) - \boldsymbol x_0  \right \Vert^{2} \\
&=  -\dfrac{1}{2\sigma^{2}_q(q)} \left \Vert \boldsymbol{\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_1) - \boldsymbol x_0  \right \Vert^{2} 
\end{aligned}
$$
Now we get
$$
\mathrm{ELBO}_{\boldsymbol \theta} = -\sum_{t = 1}^T \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[ \dfrac{1}{2\sigma_q^{2}(t)} \dfrac{(1-\alpha_t)^{2} \bar{\alpha}_{t-1}}{(1-\bar{\alpha}_t)^{2}} \Vert \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol x_0 \Vert ^{2} \right] 
$$
And therefore the loss function
$$
\boxed{
\boldsymbol \theta^{*} = \underset{\boldsymbol \theta}{\arg \min}  \sum_{t = 1}^T \dfrac{1}{2\sigma_q^{2}(t)} \dfrac{(1-\alpha_t)^{2} \bar{\alpha}_{t-1}}{(1-\bar{\alpha}_t)^{2}}\mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[  \Vert \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol x_0 \Vert ^{2} \right] 
}
$$
Ignoring the constants and expectations, the main subject of interest, for a particular $\boldsymbol x_t$, is
$$
\underset{\boldsymbol \theta}{\arg \min} \Vert \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol x_0 \Vert^{2}
$$
So this is a **denoising problem**: we need to find a network $\boldsymbol {\hat{x}}_{\boldsymbol \theta}$ such that the denoised image $\boldsymbol{\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t)$ will be close to the ground truth $\boldsymbol x_0$. 

## Training Process
![[AI-DDPM-Training-Process.png]]
For every image $\boldsymbol x_0$ in the training dataset:
- Repeat the following steps until convergence
- Pick a random time stamp $t \sim \mathrm{Uniform}[1,T]$
- Draw a sample $\boldsymbol x_t \sim q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \bar{\alpha}_t  }\boldsymbol x_0, \ (1-\bar{\alpha}_t)\textbf{I})$, i.e.,
$$
\boldsymbol x_t = \bar{\alpha}_t \boldsymbol x_0 + \sqrt{ (1- \bar{\alpha}_t) } \boldsymbol z, \qquad \boldsymbol z \sim \mathcal N(0, \textbf{I})
$$
- Take gradient descent step on
$$
\nabla _{\boldsymbol \theta} \Vert \boldsymbol{\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol x_0 \Vert ^{2}
$$
## Inference Process

![[AI-DDPM-Inference-Process.png]]
Once the denoiser $\boldsymbol{\hat{x}}_{\boldsymbol \theta}$ is trained, we can apply it to do the inference. The inference is about sampling images from the distributions $p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_t)$ over the sequence of states $\boldsymbol x_T, \boldsymbol x_{T-1}, \ldots , \boldsymbol x_1$. Since it is the reverse diffusion process, we need to do it recursively via:
$$
\begin{aligned}
\boldsymbol x_{t - 1} \sim p_{\boldsymbol \theta}(\boldsymbol x_{t-1}| \boldsymbol x_t) &= \mathcal N(\boldsymbol x_{t - 1} \mid \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t),\ \sigma_q^{2}(t)\textbf{I}) \\
&= \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t) + \sigma_q^{2}(t) \boldsymbol z, \qquad \boldsymbol z \sim \mathcal N(0, \textbf{I}) \\
&= \frac{(1-\overline{\alpha}_{t-1})\sqrt{\alpha_t}}{1-\overline{\alpha}_t}\boldsymbol{x}_t+\frac{(1-\alpha_t)\sqrt{\overline{\alpha}_{t-1}}}{1-\overline{\alpha}_t} \boldsymbol {\hat{x}}_{\boldsymbol \theta} (\boldsymbol x_t) + \sigma_q(t) \boldsymbol z
\end{aligned}
$$
This leads to the inferencing algorithm
- Given a white noise vector $\boldsymbol x_T \sim \mathcal N(0, \textbf{I})$
- Repeat the following for $t = T, T-1, \ldots ,1$
	- Calculate $\boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t)$ using the trained denoiser
	- Update according to
$$
\boldsymbol x_{t - 1} = \frac{(1-\overline{\alpha}_{t-1})\sqrt{\alpha_t}}{1-\overline{\alpha}_t}\boldsymbol{x}_t+\frac{(1-\alpha_t)\sqrt{\overline{\alpha}_{t-1}}}{1-\overline{\alpha}_t} \boldsymbol {\hat{x}}_{\boldsymbol \theta} (\boldsymbol x_t) + \sigma_q(t) \boldsymbol z, \quad \boldsymbol z \sim \mathcal N(0, \textbf{I})
$$

# Inversion by Direct Denoising (InDI)
If we look at the updating equation above, we could see the following form:
$$
\boldsymbol x_{t - 1} = \left( \text{something} \right)\cdot \boldsymbol x_t + \left( \text{something else} \right)\cdot\text{denoise}(\boldsymbol x_t) + \text{noise}
$$
The first term is easy to understand, but what is "denoise"? 
## More about Denoise
Denoising is a generic procedure that removes noise from a noisy image. Given the observation model
$$
\boldsymbol y = \boldsymbol x + \boldsymbol \epsilon, \quad \boldsymbol \epsilon \sim \mathcal N(0, \textbf{I})
$$
A classical solution to find an estimator $g(\cdot)$ such that the mean squared error is minimized is
$$
\begin{aligned}
\mathrm{denoise}(\boldsymbol y) &= \underset{g}{\arg \min} \ \mathbb{E}_{\boldsymbol x, \boldsymbol y} \left[ \Vert g(\boldsymbol y)- \boldsymbol x \Vert ^{2} \right]  \\
&= \text{some steps} \\
&= \mathbb{E}[\boldsymbol x | \boldsymbol y]
\end{aligned}
$$
So, if we assume that during the forward path
$$
\boldsymbol x_t = \boldsymbol x_{t - 1} + \boldsymbol \epsilon_{t-1}, \qquad  \boldsymbol\epsilon \sim \mathcal N(0, \textbf{I})
$$
we can find the solution of denoiser
$$
\mathrm{denoise}(\boldsymbol x_t) = \mathbb{E} \left[ \boldsymbol x_{t-1} | \boldsymbol x_t \right] 
$$
Such a denoiser is called the *minimum mean squared error (MMSE)* denoiser. MMSE denoiser is **not** the "best" denoiser; It is only the optimal denoiser with respect to the mean squared error. Since mean squared error is never a good metric for image quality, minimizing the MSE will not necessarily give us a better image.
## Incremental Denoising Steps
The previous section tells us that an MMSE denoiser is equivalent to the conditional expectation of the posterior distribution. Now we introduce **incremental denoising**. Suppose that we have a clean image $\boldsymbol x_0$ and a noise image $\boldsymbol y$. Our goal is to form a linear combination of $\boldsymbol x_0$ and $\boldsymbol y$ via a simple equation
$$
\boldsymbol x_t = (1-t){\boldsymbol x_0} + t \boldsymbol y, \qquad 0 \leq t \leq 1
$$
Now, consider a small step $\tau: \ 0 \leq \tau < t \leq 1$, then it holds that
$$
\mathbb{ E}[\boldsymbol x_{t -\tau} | \boldsymbol x_t] = \left( 1 - \dfrac{\tau}{t} \right) \underbrace{\boldsymbol x_t}_{\text{current estimate}} + \dfrac{\tau}{t} \underbrace{\mathbb{ E}[\boldsymbol x_0 | \boldsymbol x_t]}_{\text{denoised}}
$$
If we define $\boldsymbol{\hat{x}}_{t -\tau}$ as the left hand side, replace $\boldsymbol x_t$ by $\boldsymbol{\hat{x}}_t$, and write $\mathbb{E}[\boldsymbol x_0 | \boldsymbol x_t]$ as $\mathrm{denoise}(\boldsymbol{\hat{x}}_t)$, then the above equation will become
$$
\boldsymbol {\hat{x}}_{t -\tau} = \left( 1 - \dfrac{\tau}{t} \right)\cdot \boldsymbol {\hat{x}}_t + \dfrac{\tau}{t} \mathrm{denoise}(\boldsymbol {\hat{x}}_t)
$$
where $\tau$ is a small step in time. This equation gives us an **inference** step. If you tell us the denoiser and suppose that you start with a noisy image $\boldsymbol y$, then you can iteratively apply this equation to retrieve the images $\boldsymbol {\hat{x}}_{t - 1}, \boldsymbol {\hat{x}}_{t-2}, \ldots ,\boldsymbol {\hat{x}}_0$

# Equivalent Interpretations
## Predicting noises
As discussed above, a Variational Diffusion Model can be trained by simply learning a neural network to predict the original natural image $\boldsymbol x_0$ form an arbitrary noised version $\boldsymbol x_t$ and its time index $t$. 

This interpretation is from the parameterization of $\boldsymbol x_t$, that is
$$
\boldsymbol x_t = \sqrt{\bar{\alpha}_t} \boldsymbol x_0 + \sqrt{ (1- \bar{\alpha}_t) } \boldsymbol z, \qquad \boldsymbol z \sim \mathcal N(0, \textbf{I})
$$
And we can rewrite this to 
$$
\boldsymbol x_0 = \dfrac{\boldsymbol x_t - \sqrt{ 1- \bar{\alpha}_t }\boldsymbol z}{\sqrt{ \bar{\alpha}_t }}
$$
Now we can change $\boldsymbol \mu_{q}(\boldsymbol x_t, \boldsymbol x_0)$ to a function of $\boldsymbol x_t, \boldsymbol z$ rather than $\boldsymbol x_0, \boldsymbol z$, that is
$$
\begin{aligned}
\boldsymbol{\mu}_q(\boldsymbol{x}_t,\boldsymbol{x}_0)& =\frac{\sqrt{\alpha_t}(1-\bar{\alpha}_{t-1})\boldsymbol{x}_t+\sqrt{\bar{\alpha}_{t-1}}(1-\alpha_t)\boldsymbol{x}_0}{1-\bar{\alpha}_t} \\
&=\frac{\sqrt{\alpha_t}(1-\bar{\alpha}_{t-1})\boldsymbol{x}_t+\sqrt{\bar{\alpha}_{t-1}}(1-\alpha_t)\frac{\boldsymbol{x}_t-\sqrt{1-\bar{\alpha}_t}\boldsymbol{z}}{\sqrt{\bar{\alpha}_t}}}{1-\bar{\alpha}_t} \\

&=\frac{\sqrt{\alpha_t}(1-\bar{\alpha}_{t-1})\boldsymbol{x}_t}{1-\bar{\alpha}_t}+\frac{(1-\alpha_t)\boldsymbol{x}_t}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}-\frac{(1-\alpha_t)\sqrt{1-\bar{\alpha}_t}\boldsymbol{z}}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}} \\

&=\left(\frac{\alpha_t(1-\bar{\alpha}_{t-1})}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}+\frac{1-\alpha_t}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}\right)\boldsymbol{x}_t-\frac{1-\alpha_t}{\sqrt{1-\bar{\alpha}_t}\sqrt{\alpha_t}}\boldsymbol{z} \\
&=\frac{\alpha_t-\bar{\alpha}_t+1-\alpha_t}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}\boldsymbol{x}_t-\frac{1-\alpha_t}{\sqrt{1-\bar{\alpha}_t}\sqrt{\alpha_t}}\boldsymbol{z} \\

&=\frac1{\sqrt{\alpha_t}}\boldsymbol{x}_t-\frac{1-\alpha_t}{\sqrt{1-\bar{\alpha}_t}\sqrt{\alpha_t}}\boldsymbol{z}
\end{aligned}
$$

Therefore, now we could set our predicted transition mean as
$$
\boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t, t) = \dfrac{1}{\sqrt{ \alpha_t }} \boldsymbol x_t - \dfrac{1-\alpha_t}{\sqrt{ 1-\bar{\alpha}_t }\sqrt{ \alpha_t }} \boldsymbol{\hat{z}}_{\boldsymbol \theta}(\boldsymbol x_t, t)
$$
And after some calculations, we just need to optimize
$$
\boxed{
\boldsymbol \theta^{*} = \underset{\boldsymbol \theta}{\arg \min}  \sum_{t = 1}^T \dfrac{1}{2\sigma_q^{2}(t)} \dfrac{(1-\alpha_t)^{2} }{(1-\bar{\alpha}_t)^{2}\alpha_t}\mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[  \Vert \boldsymbol {\hat{z}}_{\boldsymbol \theta}(\boldsymbol x_t) - \boldsymbol z_0 \Vert ^{2} \right] 
}
$$

We have therefore shown that learning a VDM by predicting the original image $\boldsymbol x_0$ **is equivalent to learning to predict the noise**; empirically, however, some works have found that predicting the noise resulted in better performance

## Predicting scores
As we have concluded
$$
q(\boldsymbol x_t|\boldsymbol x_0) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \bar{\alpha}_t }\boldsymbol x_0,\ (1-\bar{\alpha}_t)\textbf{I})
$$
by [[Tweedie's Formula]], we have
$$
\mathbb{E}[\boldsymbol \mu_{\boldsymbol x_t} | \boldsymbol x_t] = \boldsymbol x_t + (1-\bar{\alpha}_t) \nabla_{\boldsymbol x_t} \log p(\boldsymbol x_t)
$$
And we know the best estimate for the true mean of $\boldsymbol x_t$ given $\boldsymbol x_0$ is $\sqrt{ \bar{\alpha}_t }\boldsymbol x_0$, now we get (write $\nabla_{\boldsymbol x_t}$ as $\nabla$ for convenience)
$$
\sqrt{ \bar{\alpha}_t } \boldsymbol x_0 = \boldsymbol x_t + (1-\bar{\alpha}_t) \nabla \log p(\boldsymbol x_t)
$$
Now we get another way to express $\boldsymbol \mu_q(\boldsymbol x_t, \boldsymbol x_0)$
$$
\begin{aligned}
\boldsymbol{\mu}_q(\boldsymbol{x}_t,\boldsymbol{x}_0)& =\frac{\sqrt{\alpha_t}(1-\bar{\alpha}_{t-1})\boldsymbol{x}_t+\sqrt{\bar{\alpha}_{t-1}}(1-\alpha_t)\boldsymbol{x}_0}{1-\bar{\alpha}_t} \\
&=\frac{\sqrt{\alpha_t}(1-\bar{\alpha}_{t-1})\boldsymbol{x}_t+\sqrt{\bar{\alpha}_{t-1}}(1-\alpha_t)\frac{\boldsymbol{x}_t+(1-\bar{\alpha}_t)\nabla\log p(\boldsymbol{x}_t)}{\sqrt{\bar{\alpha}_t}}}{1-\bar{\alpha}_t} \\
&=\frac{\sqrt{\alpha_t}(1-\bar{\alpha}_{t-1})\boldsymbol{x}_t}{1-\bar{\alpha}_t}+\frac{(1-\alpha_t)\boldsymbol{x}_t}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}+\frac{(1-\alpha_t)(1-\bar{\alpha}_t)\nabla\log p(\boldsymbol{x}_t)}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}} \\
&=\left(\frac{\alpha_t(1-\bar{\alpha}_{t-1})}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}+\frac{1-\alpha_t}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}\right)\boldsymbol{x}_t+\frac{1-\alpha_t}{\sqrt{\alpha_t}}\nabla\log p(\boldsymbol{x}_t) \\
&=\frac{\alpha_t-\bar{\alpha}_t+1-\alpha_t}{(1-\bar{\alpha}_t)\sqrt{\alpha_t}}\boldsymbol{x}_t+\frac{1-\alpha_t}{\sqrt{\alpha_t}}\nabla\log p(\boldsymbol{x}_t) \\
&=\frac1{\sqrt{\alpha_t}}\boldsymbol x_t+\frac{1-\alpha_t}{\sqrt{\alpha_t}}\nabla\log p(\boldsymbol{x}_t)
\end{aligned}
$$
Therefore, we can also set our approximate denoising transition mean $\boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t)$ as
$$
\boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t) = \dfrac{1}{\sqrt{ \alpha_t }} \boldsymbol x_t + \dfrac{1 - \alpha_t}{\sqrt{ \alpha _t }} \boldsymbol s_{\boldsymbol \theta}(\boldsymbol x_t,t)
$$
And the corresponding optimization problem becomes
$$
\boxed{
\boldsymbol \theta^{*} = \underset{\boldsymbol \theta}{\arg \min}  \sum_{t = 1}^T \dfrac{1}{2\sigma_q^{2}(t)} \dfrac{(1-\alpha_t)^{2} }{\alpha_t}\mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[  \Vert \boldsymbol {s}_{\boldsymbol \theta}(\boldsymbol x_t) - \nabla \log p(\boldsymbol x_t)\Vert ^{2} \right] 
}
$$
One more problem is how to calculate $\nabla \log p(\boldsymbol x)_t$, this would be easy if we apply the relationship used in [[Denoising Diffusion Probabilistic Models (DDPM)#Predicting noises|predicting noises]]
$$
\boldsymbol x_0 = \dfrac{\boldsymbol x_t - \sqrt{ 1- \bar{\alpha}_t }\boldsymbol z}{\sqrt{ \bar{\alpha}_t }}
$$
This is equal to
$$
\boldsymbol x_0= \dfrac{\boldsymbol x_t + (1-\bar{\alpha}_t) \nabla \log p(\boldsymbol x_t)}{\sqrt{ \bar{\alpha}_t }}
$$
Now we get
$$
\nabla \log p(\boldsymbol x_t) = - \dfrac{1}{\sqrt{ 1- \bar{\alpha}_t }} \boldsymbol z
$$
> [!Tip]
> The score function measures how to move in data space to maximize the log probability; intuitively, since the source noise is added to a natural image to corrupt it, **moving in its opposite direction "denoises" the image and would be the best update to increase the subsequent log probability**.

# Score-Matching Langevin Dynamics (SMLD)
In this section we dive into the intuition of the score-matching interpretation. 
## Energy-based Models
To begin to understand why optimizing a score function makes sense, we shall first introduce **energy-based models**. Remember the form of [[Boltzmann Distribution|Boltzmann Distribution]], we have
$$
p_{\boldsymbol \theta} (\boldsymbol x) = \dfrac{1}{Z_{\boldsymbol \theta}} \exp \left[ -f_{\boldsymbol \theta}(\boldsymbol x) \right] 
$$
where $f_{\boldsymbol \theta}$ is an arbitrarily flexible, parameterizable function called the *energy function*, and $Z_{\boldsymbol \theta}$ is a normalizing constant to ensure that $\int p_{\boldsymbol \theta}(\boldsymbol x) \mathrm{d}x=1$. One way to learn this distribution is [[Maximum Likelihood Estimation (MLE)|MLE]], but this requires tractably computing the normalizing constant $Z_{\boldsymbol \theta} = \int \exp \left[ -f_{\boldsymbol \theta}(\boldsymbol x) \right]$, which may not be possible for complex $f_{\boldsymbol \theta}(\boldsymbol x)$ functions.

One way to avoid calculating or modeling the normalization constant is by using a neural network $\boldsymbol s_{\boldsymbol \theta}(\boldsymbol x)$ to learn the score function $\nabla \log p(\boldsymbol x)$ of distribution $p(\boldsymbol x)$ instead. This can be done by taking the derivative of the log of both sides of the equation above
$$
\begin{aligned}
\nabla_{\boldsymbol x} \log p_{\boldsymbol \theta}(\boldsymbol x) &= \nabla_{\boldsymbol x} \log \left\{ \dfrac{1}{Z_{\boldsymbol \theta}}\exp \left[ -f_{\boldsymbol \theta}(\boldsymbol x) \right]  \right\}  \\
&= \nabla_{\boldsymbol x} \log \dfrac{1}{Z_{\boldsymbol \theta}} + \nabla_{\boldsymbol x} \log \exp \left[ -f_{\boldsymbol \theta}(\boldsymbol x) \right]  \\
&= - \nabla_{\boldsymbol x} f_{\boldsymbol \theta}(\boldsymbol x) \\
&\approx \boldsymbol s_{\boldsymbol \theta}(\boldsymbol x)
\end{aligned}
$$
which can be freely represented as a neural network without involving any normalization constants. The score model can be optimized by minimizing the *Fisher Divergence* with the ground truth score function
$$
\mathbb{E}_{p(\boldsymbol x)} \left[ \Vert \boldsymbol s_{\boldsymbol \theta}(\boldsymbol x) - \nabla \log p(\boldsymbol x) \Vert^{2} \right] 
$$
## Langevin Dynamics
Imagine that we are given a distribution $p(\boldsymbol x)$ and suppose that we want to draw samples from $p(\boldsymbol x)$. *Langevin dynamics* is an iterative procedure that allows us to draw samples according to the following equation
$$
\boldsymbol x_{t + 1} = \boldsymbol x_t + \tau \nabla_{\boldsymbol x} \log p(\boldsymbol x_t) + \sqrt{ 2\tau } \boldsymbol z, \quad \boldsymbol z \sim \mathcal N(0, \textbf{I})
$$
where $\tau$ is the step size which users can control, and $\boldsymbol x_0$ is white noise.

Note that if we ignore the noise term $\sqrt{ 2\tau }\boldsymbol z$ at the end, the Langevin dynamics equation is **literally [[Gradient Descent|gradient descent]]**. The descent $\nabla_{\boldsymbol x} \log p(\boldsymbol x)$ is carefully chosen that $\boldsymbol x_t$ will converge to the distribution $p(\boldsymbol x)$.

The goal of this descent sampling process is to find a $\boldsymbol x$ where the probability is the highest, which is equivalent to solving the optimization
$$
\boldsymbol x^* = \underset{\boldsymbol x}{\arg \max} \ \log p(\boldsymbol x)
$$
> [!Warning]
> Note that this is not [[Maximum Likelihood Estimation (MLE)|MLE]]. In maximum likelihood, the data point $\boldsymbol x$ is fixed but the model parameters are changing. Here, the model parameters are fixed but the data point is changing.

And now we can understand the noise term $\sqrt{ 2\tau }\boldsymbol z$, which **literally changes the gradient descent to [[Stochastic Gradient Descent (SGD)|stochastic gradient descent]]**. Instead of shooting for the deterministic optimum, the stochastic gradient descent climbs up the hill randomly, so that there would be a lower probability to stuck into a local maximum

However, we actually do not care about the maximum of $p(\boldsymbol x)$, which is the final goal of the descent process. Instead, **we care about the sampling process itself**. As well as our descent algorithm is good at find peaks, then by **repeatedly initialize the algorithm at a uniformly distributed location, we will eventually collects samples that will follow the distribution we want to match**.

> [!Info]
> Suppose we initialize $10000$ uniformly distributed samples $x_0 \sim \mathrm{Uniform}[-3,3]$. We run Langevin updates for $t = 100$ steps. The histograms of generated samples are shown in the figures below
> ![[AI-DDPM-Langevin-Dynamics.png]]

In summary, Langevin dynamics gives us a more intuitive vision into the score-matching problem in energy-based models. In energy-based models, we learn the distribution of $p_{\boldsymbol \theta}$ by matching a score function $\boldsymbol s_{\boldsymbol\theta}$ with $\nabla \log p(\boldsymbol x)$. On the other hand, if we find a good estimation $\boldsymbol s_{\boldsymbol \theta}$ of the descent term $\nabla \log p(\boldsymbol x)$ in Langevin dynamics, the sampling process would do better in finding a peak in the neighborhood of its initial state $\boldsymbol x_0$, so that by initialize the $\boldsymbol x_0$ uniformly in the interval we interested with, the sampling would follow the $p(\boldsymbol x)$ we want to approximate.

