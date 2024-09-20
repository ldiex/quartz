# Derive the ELBO
In [[Variational Inference#Variational Bayesian Inference|variational inference]] we want to approximate the true posterior distribution $p_\theta(z|x)$ from a known distribution family $q_\phi(z|x)$.

We often choose [[Kullback–Leibler Divergence|KL divergence]] as the loss function to measure the difference between two probability distributions. Therefore, we need to minimize
$$
\begin{aligned}
\mathbb{D}_{\mathrm{KL}}(q_\phi (z|x) \Vert p_\theta(z | x)) &= \mathbb{E}_{q_\phi(z | x)}\left[ \log \dfrac{q_\phi(z|x)}{p_\theta(z|x)} \right]  \\
&= \mathbb{E}_{q_\phi(z | x)} \log q_\phi(z|x) - \mathbb{E}_{q_\phi(z | x)} \log p_\theta(z|x) \\
&= \mathbb{E}_{q_\phi(z | x)} \log q_\phi(z|x) - \mathbb{E}_{q_\phi(z | x)} \left\{ \log \left[ \dfrac{p_\theta(x,z)}{p_\theta(x)} \right]  \right\} \\
&= \mathbb{E}_{q_\phi(z | x)} \log q_\phi(z|x) - \mathbb{E}_{q_\phi(z | x)} \left[ \log p_\theta(x,z) \right]  + \mathbb{E}_{q_\phi(z | x)} \left[ \log p_\theta(x) \right] \\ 
&= \underbrace{\mathbb{E}_{q_\phi(z | x)} \log q_\phi(z|x) - \mathbb{E}_{q_\phi(z | x)} \left[ \log p_\theta(x,z) \right]}_{-\mathrm{ELBO}}  +   \log p_\theta(x)  
\end{aligned}
$$
where we define
$$
\mathrm{ELBO}(x) =  \mathbb{E}_{q_\phi(z | x)} \left[ \log p_\theta(x,z) \right] - \mathbb{E}_{q_\phi(z | x)} \log q_\phi(z|x) 
$$
Then we have
$$
\log p_\theta(x) = \mathrm{ELBO}(x) + \mathbb{D}_{\mathrm{KL}}(q_\phi (z|x) \Vert p_\theta(z | x)) 
$$
Since the left hand side is constant (not depending on $\phi$), too minimize KL divergence is equivalent to maximize $\mathrm{ELBO}(\phi)$

> [!Tip] Why Evidence Lower Bound
> The name of ELBO comes from $\mathbb{D}_{\mathrm{DL}}(\cdot) \geq 0 \implies \log p_\theta(x)\geq \mathrm{ELBO}(x)$

![[Math-ELBO.png]]



