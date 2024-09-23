# Overview
Diffusion models are **incremental** updates where the assembly of the whole gives us the encoder-decoder structure. The transition from one state to another is realized by a *denoiser*.

![[AI-DDPM-Arch.png]]
The model whose structure is shown above is called the *variational diffusion model (VDM)*. The model has a sequence of states $\boldsymbol x_0, \boldsymbol x_1, \ldots , \boldsymbol x_T$
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

&=\prod_{t=2}^T\frac{p(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t)}{q_{\boldsymbol{\phi}}(\boldsymbol{x}_{t-1}|\boldsymbol{x}_t,\boldsymbol{x}_0)}\times\frac{q_\boldsymbol{\phi}(\boldsymbol{x}_1|\boldsymbol{x}_0)}{q_\boldsymbol{\phi}(\boldsymbol{x}_T|\boldsymbol{x}_0)}
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
# Derivation of $q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$
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
f''(y)=\frac{1-ab}{(1-a)(1-b)}=\frac{1-\overline{\alpha}_t}{(1-\alpha_t)(1-\sqrt{\overline{\alpha}_{t-1}})}
$$
And this gives us
$$
\boldsymbol{\Sigma}_q(t)=\frac{(1-\alpha_t)(1-\sqrt{\overline{\alpha}_{t-1}})}{1-\overline{\alpha}_t}\mathbf{I}
$$
Now we know the distribution of $q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$
$$
q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0) = \mathcal N(\boldsymbol x_{t -1} \mid \boldsymbol \mu_q (\boldsymbol x_t, \boldsymbol x_0), \ \boldsymbol \Sigma_q(t))
$$
Therefore, we can calculate the ELBO of VDM! Through some boring algebraic calculation:
$$
\begin{aligned}
\mathrm{ELBO_{ \boldsymbol \theta}}(\boldsymbol x) &= \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_1 | \boldsymbol x_0)} \left[ \log {p_{\boldsymbol \theta}(\boldsymbol x_0 | \boldsymbol x_1)} \right] - \underbrace{\mathbb{D}_\mathrm{KL} \left( q_{\boldsymbol \phi}(\boldsymbol x_T|\boldsymbol x_0) \ \Vert \ p(\boldsymbol x_T) \right)}_{\text{Nothing to train}} \\
&\qquad -  \sum_{t = 2}^T \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol x_t | \boldsymbol x_0)} \left[ \dfrac{1}{2\sigma_q^{2}(t)} \Vert \boldsymbol \mu_q(\boldsymbol x_t, \boldsymbol x_0) - \boldsymbol \mu_{\boldsymbol \theta}(\boldsymbol x_t) \Vert^{2}  \right] 
\end{aligned}
$$
We don't need to train the second term since each step of $q_{\boldsymbol \phi}(\boldsymbol x_{t-1}|\boldsymbol x_t, \boldsymbol x_0)$ is fixed so there is no parameters to learn (the $\alpha_t$s are typically **human-designed**), and the $p(\boldsymbol x_T)$ is also fixed as a Gaussian $\mathcal N(0, \textbf{I})$

# Training 








