This article is a simplified interpretation of [[Denoising Diffusion Probabilistic Models (DDPM)|DDPM]].

The general target of diffusion models is to learn a real world distribution $p(\boldsymbol x)$. DDPM chooses a step-by-step [[Markov Property|Markov Chain]] to do this
$$
p_{\boldsymbol \theta}(\boldsymbol x_0) = \int p_{\boldsymbol \theta}(\boldsymbol x_{0:T}) \mathrm{d}\boldsymbol x_{1:T}
$$
where we set $p(\boldsymbol x_T)= \mathcal N(\boldsymbol x_T | \boldsymbol 0, \ \textbf{I})$, and 
$$
p_{\boldsymbol \theta} (\boldsymbol x_{0:T}) = p_{\boldsymbol \theta}(\boldsymbol x_T) \prod_{t = 1}^T p_{\boldsymbol \theta}(\boldsymbol x_{t-1} | \boldsymbol x_{t}) 
$$
We don't know what is $p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_t)$, so we apply [[Bayes' Theorem]],
$$
p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_t) = \dfrac{p_{\boldsymbol \theta}(\boldsymbol x_{t}|\boldsymbol x_{t-1})p_{\boldsymbol \theta}(\boldsymbol x_{t-1})}{p_{\boldsymbol \theta}(\boldsymbol x_t)}
$$
Recall the definition of the [[Denoising Diffusion Probabilistic Models (DDPM)#Transition Distribution|transition distribution]]
$$
p_{\boldsymbol \theta}(\boldsymbol x_t | \boldsymbol x_{t  -1}) = \mathcal N(\boldsymbol x_t \mid \sqrt{ \alpha_t }\boldsymbol x_{t - 1}, \ (1-\alpha_t) \textbf{I})
$$
So we therefore can conclude $p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_0)$ and $p_{\boldsymbol \theta}(\boldsymbol x_t|\boldsymbol x_0)$, than we would have
$$
\begin{aligned}
p_{\boldsymbol \theta}(\boldsymbol x_{t-1} | \boldsymbol x_{t}, \boldsymbol x_0) &= \dfrac{p_{\boldsymbol \theta}(\boldsymbol x_{t}|\boldsymbol x_{t-1})p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_0)}{p_{\boldsymbol \theta}(\boldsymbol x_t| \boldsymbol x_0)} \\
&= \dfrac{\mathcal N(\boldsymbol x_t | \sqrt{ \alpha_t} \boldsymbol x_{t - 1}, (1-\alpha_t)\textbf{I}) \mathcal N(\boldsymbol x_{t-1} | \sqrt{ \bar{\alpha}_{t-1}} \boldsymbol x_{t - 1}, (1-\bar{\alpha}_{t-1})\textbf{I})}{\mathcal N(\boldsymbol x_t | \sqrt{ \bar{\alpha}_t} \boldsymbol x_0, (1-\bar{\alpha}_t)\textbf{I})} \\
&= \mathcal N(\boldsymbol x_{t -1} \mid \boldsymbol \mu (\boldsymbol x_t, \boldsymbol x_0), \ \sigma_t^{2} \textbf{I})
\end{aligned}
$$
where
$$
\begin{aligned}
\boldsymbol{\mu}(\boldsymbol{x}_t,\boldsymbol{x}_0)&=\frac{(1-\overline{\alpha}_{t-1})\sqrt{\alpha_t}}{1-\overline{\alpha}_t}\boldsymbol{x}_t+\frac{(1-\alpha_t)\sqrt{\overline{\alpha}_{t-1}}}{1-\overline{\alpha}_t}\boldsymbol{x}_0 \\
\sigma_t^{2} &= \frac{(1-\alpha_t)(1-{\overline{\alpha}_{t-1}})}{1-\overline{\alpha}_t}\
\end{aligned}
$$
However, we want $p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_t)$ other than $p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_t,\boldsymbol x_0)$. To solve this, we train a model $\boldsymbol {\hat{x}} = \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t)$to predict $\boldsymbol x_0$ from $\boldsymbol x_t$, so that the probability would only depend on $\boldsymbol x_t$. Therefore
$$
p_{\boldsymbol \theta}(\boldsymbol x_{t-1}|\boldsymbol x_t) \approx p_{\boldsymbol \theta}(\boldsymbol x_{t-1}| \boldsymbol x_t, \boldsymbol x_0 = \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t)) = \mathcal N(\boldsymbol x_{t -1} \mid \boldsymbol \mu (\boldsymbol x_t, \boldsymbol {\hat{x}}_{\boldsymbol \theta}(\boldsymbol x_t)), \ \sigma_t^{2} \textbf{I})
$$
This is what **denoising** means.
