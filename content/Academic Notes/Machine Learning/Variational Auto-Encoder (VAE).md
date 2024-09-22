# Model
A variational auto-encoder (VAE) is an approach to generate images from a latent code.
![[AI-VAE-Arch.png]]
The name “variational” comes from the factor that we use probability distributions to describe $\boldsymbol x$ and $\boldsymbol z$. Instead of resorting to a deterministic procedure of converting $\boldsymbol x$ to $\boldsymbol z$, we are more interested in ensuring that the distribution $p(\boldsymbol x)$ can be mapped to a desired distribution $p(\boldsymbol z)$, and go backwards to $p(\boldsymbol x)$.
![[AI-VAE-Latent-Attrbutes.png]]
Since it's hard to directly access $p(\boldsymbol z|\boldsymbol x)$ (the decoder) and $p(\boldsymbol x | \boldsymbol z)$ (the encoder), we consider the following two proxy distributions to approximate them:
- $q_{\boldsymbol \phi}(\boldsymbol z|\boldsymbol x)$: The proxy for $p(\boldsymbol z|\boldsymbol x)$ with learnable parameter $\boldsymbol \phi$. We will make it [[Normal Distribution (Gaussian Distribution)|Gaussian]] to simplify the computation
- $p_{\boldsymbol \theta}(\boldsymbol x|\boldsymbol z)$: The proxy for $p(\boldsymbol x|\boldsymbol z)$ with learnable parameter $\boldsymbol \theta$. We will also make it [[Normal Distribution (Gaussian Distribution)|Gaussian]] to simplify the computation
So the whole procedure of VAE can be
$$
\boldsymbol x \xrightarrow{p(\boldsymbol z | \boldsymbol x) \approx q_{\phi}(\boldsymbol z| \boldsymbol x)} \boldsymbol z \xrightarrow{p(\boldsymbol x | \boldsymbol z) \approx p_\theta(\boldsymbol x | \boldsymbol z)} \boldsymbol x
$$
![[AI-VAE-Model.png]]
# ELBO in VAE Setting
In [[Variational Inference|variational inference]], minimizing the difference (here to minimize the [[Kullback–Leibler Divergence|KL divergence]]) between two probability distributions is equivalent to maximizing the [[Evidence Lower Bound (ELBO)|ELBO]]. Here, we need to minimize $\mathbb{D}_{\mathrm{KL}}(q_{\boldsymbol \phi} (\boldsymbol z | \boldsymbol x) \Vert p(\boldsymbol z | \boldsymbol x))$, that is, to maximize
$$
\mathrm{ELBO}(\boldsymbol \phi) =  \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \left[ \log p(\boldsymbol x, \boldsymbol z) \right] - \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \log q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x) 
$$
However, the ELBO above may not too useful because it involves $p(\boldsymbol x, \boldsymbol z)$, something we have no access to. So we need to do something more:
$$
\boxed{\begin{aligned}
\mathrm{ELBO}(\boldsymbol \phi) &=  \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \left[ \log p(\boldsymbol x, \boldsymbol z) \right] - \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \log q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)  \\
&= \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)}\left[ \log p(\boldsymbol x | \boldsymbol z) \right] + \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \left[ \log p(\boldsymbol z) \right]  - \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \log q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x) \\
&= \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)}\left[ \log p(\boldsymbol x | \boldsymbol z) \right] + \mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \left[ \log \dfrac{p(\boldsymbol z)}{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \right]  \\
&= \underbrace{\mathbb{E}_{q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)} \left[ \log p_\theta(\boldsymbol x | \boldsymbol z) \right]}_{\text{how good your decoder is}} + \underbrace{\left[ -\mathbb{D}_{\mathrm{KL}} (q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x) \Vert p(\boldsymbol z)) \right] }_{\text{how good your encoder is}}
\end{aligned}}
$$
where in the last line we replace $p(\boldsymbol x| \boldsymbol z)$ by its proxy $p_{\boldsymbol \theta }(\boldsymbol x | \boldsymbol z)$, and there are two terms:
- **Reconstruction**. The first term is about the decoder. We want the decoder to produce a good image $\boldsymbol x$ if we feed a latent $\boldsymbol z$ into the decoder. So, we want to maximize $\log p_{\boldsymbol \theta}(\boldsymbol x | \boldsymbol z)$. (We sample $X, Z$ from real distribution $p(\boldsymbol x, \boldsymbol z)$, and the goal of decoder is to approximate $p_{\boldsymbol \theta}$ to $p$). The expectation here is taken with respect to the samples $\boldsymbol z$ conditioned on $\boldsymbol x$
- **Prior Matching**. The second term is the KL divergence for the encoder. We want the encoder to turn $\boldsymbol x$ into a latent vector $\boldsymbol z$ such that the latent vector will follow our choice of (good) distribution such as a [[Normal Distribution (Gaussian Distribution)|Gaussian distribution]]. 
To conclude, the training goal will be
- **Decoder**. For given $(\boldsymbol z, \boldsymbol x)$, find $\boldsymbol \theta$ to maximize $p_{\boldsymbol \theta}(\boldsymbol x | \boldsymbol z)$
- **Encoder**. For given $(\boldsymbol z, \boldsymbol x)$, find $\boldsymbol \phi$ to minimize $\mathbb{D}_{\mathrm{KL}} (q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x) \Vert p(\boldsymbol z))$

# Training VAE
## Encoder
We know that $\boldsymbol z$ is generated from the distribution $q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)$. We also know that $q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)$ should be simple as a Gaussian. Assume that for any give input $\boldsymbol x$ this Gaussian has a mean $\boldsymbol \mu$ and a covariance matrix $\sigma^{2} \textbf{I}$. We use a deep neural network (DNN) to predict them:
$$
\boldsymbol \mu = \underbrace{\boldsymbol \mu_{\boldsymbol \phi}}_{\text{DNN}} (\boldsymbol x), \quad \sigma^{2} = \underbrace{\sigma^{2}_{\boldsymbol \phi}}_{\text{DNN}} (\boldsymbol x), 
$$
Therefore, the samples $\boldsymbol z^{(\ell)}$ can be sampled from the Gaussian distribution
$$
\boldsymbol z^{(\ell)} \sim \mathcal N(\boldsymbol z^{\ell} \mid \boldsymbol \mu_{\boldsymbol \phi}(\boldsymbol x^{(\ell)}), \ \sigma_{\boldsymbol \phi}^{2} (\boldsymbol x^{(\ell)}) \textbf{I})
$$
## Decoder
The decoder is implemented through a neural network, denoted as $\mathrm{decoder}_{\boldsymbol \theta}$. The job of the decoder network is to take a latent variable $\boldsymbol z$ and generates an image $\hat{\boldsymbol x}$:
$$
\hat{\boldsymbol x} = \mathrm{decoder}_{\boldsymbol \theta}(\boldsymbol z)
$$
Let's make one more assumption that the decoded image $\hat{\boldsymbol x}$ and the ground truth image $\boldsymbol x$ is Gaussian, that is
$$
(\hat{\boldsymbol x} - \boldsymbol x) \sim \mathcal N(0, \sigma_{\mathrm{ dec}}^{2})
$$
Then, it follows that the distribution $p_{\boldsymbol \theta}(\boldsymbol x | \boldsymbol z)$ (marked to be Gaussian)
$$
\begin{aligned}
\log p_{\boldsymbol \theta}(\boldsymbol x | \boldsymbol z) &= \log \mathcal N(\boldsymbol x \mid \mathrm{decode}_{\boldsymbol \theta}(\boldsymbol z),\ \sigma^{2}_{\mathrm{dec}} \textbf{I} ) \\
&= \log \left\{ \dfrac{1}{\sqrt{ (2\pi \sigma^{2}_{\mathrm{dec}})^D }} \exp \left[ - \dfrac{\Vert \boldsymbol x - \mathrm{decode}_{\boldsymbol \theta}(\boldsymbol z) \Vert^{2} }{2\sigma_\mathrm{{dec}}^{2}} \right] \right\}   \\
&= - \dfrac{\Vert \boldsymbol x - \mathrm{decode}_{\boldsymbol \theta}(\boldsymbol z) \Vert^{2} }{2\sigma_\mathrm{{dec}}^{2}}  - \log \sqrt{ (2\pi \sigma^{2}_\mathrm{dec})^D }
\end{aligned}
$$
where $D$ is the dimension of $\boldsymbol x$. This equation says that the maximization of the likelihood term in ELBO is literally just the $\ell_2$ loss between the decoded image and ground truth.

## Loss Function
To approximate the expectation, we use Monte-Carlo simulation:
$$
\mathbb{E}_{q_{\boldsymbol{\phi}}(\boldsymbol{z}|\boldsymbol{x})}[\log p_{\boldsymbol{\theta}}(\boldsymbol{x}|\boldsymbol{z})]\approx\frac1L\sum_{\ell=1}^L\log p_{\boldsymbol{\theta}}(\boldsymbol{x}^\ell|\boldsymbol{z}^{(\ell)}),\quad\boldsymbol{z}^{(\ell)}\sim q_{\boldsymbol{\phi}}(\boldsymbol{z}|\boldsymbol{x}^{(\ell)})
$$
where $\boldsymbol x^{(\ell)}$ is the $\ell$-th sample in the training set, and the distribution $q_{\boldsymbol \theta}$ is $q_{\boldsymbol \phi}(\boldsymbol z \vert \boldsymbol x^{(\ell)})= \mathcal N (\boldsymbol z \mid \boldsymbol \mu_{\boldsymbol \phi}(\boldsymbol x ^{(\ell)}), \ \sigma_{\boldsymbol \phi}^2(\boldsymbol x ^{(\ell)})\textbf{I})$

Now we have the **training loss of VAE**
$$
\underset{\boldsymbol \phi, \boldsymbol \theta}{\arg \max}\left\{ \dfrac{1}{L} \sum_{\ell = 1}^L \log p_{\boldsymbol \theta}(\boldsymbol x^{(\ell)}| \boldsymbol z^{(\ell)})- \mathbb{D}_\mathrm{KL} (q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x^{(\ell)}) \Vert p(\boldsymbol z)) \right\} 
$$
where the first term can be simplified to the $\ell_2$ loss between $\boldsymbol x$ and $\mathrm{decode}_{\boldsymbol \theta}(\boldsymbol z)$ as mentioned above, and the second term can be simplified by the solution of KL divergence between two Gaussian distributions:
$$
\mathbb{D}_{\mathrm{KL}}(\mathcal{N}(\boldsymbol{\mu}_0,\boldsymbol{\Sigma}_0),\mathcal{N}(\boldsymbol{\mu}_1,\boldsymbol{\Sigma}_1))=\frac12\left(\mathrm{Tr}(\boldsymbol{\Sigma}_1^{-1}\boldsymbol{\Sigma}_0)-d+(\boldsymbol{\mu}_1-\boldsymbol{\mu}_0)^T\boldsymbol{\Sigma}_1^{-1}(\boldsymbol{\mu}_1-\boldsymbol{\mu}_0)+\log\frac{\mathrm{det}\boldsymbol{\Sigma}_1}{\mathrm{det}\boldsymbol{\Sigma}_0}\right)
$$

and in this case $\boldsymbol \mu_0 = \boldsymbol \mu_{\boldsymbol \phi}(\boldsymbol x^{(\ell)}),\ \boldsymbol \Sigma_0 = \sigma^{2}_{\boldsymbol \phi}(\boldsymbol x^{(\ell)})\textbf{I},\ \boldsymbol \mu_1 = 0, \boldsymbol \Sigma_1 = 1$, thus
$$
\mathbb{D}_{\mathrm{KL}}(q_{\boldsymbol{\phi}}(\boldsymbol{z}|\boldsymbol{x}^{(\ell)})\parallel p(\boldsymbol{z}))=\frac12\left((\sigma_{\boldsymbol{\phi}}^2(\boldsymbol{x}^{(\ell)}))^d+\boldsymbol{\mu}_{\boldsymbol{\phi}}(\boldsymbol{x}^{(\ell)})^T\boldsymbol{\mu}_{\boldsymbol{\phi}}(\boldsymbol{x}^{(\ell)})-d\log(\sigma_{\boldsymbol{\phi}}^2(\boldsymbol{x}^{(\ell)}))\right)
$$
where $d$ is the dimension of the vector $\boldsymbol z$

## Reparameterization
Note that the latent variable $\boldsymbol z$ in the loss function is **sampled** from $q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)$, which **cannot be differentiated during the back-propagation process**. So we need to express $\boldsymbol z$ as some differentiable transformation of another random variable $\boldsymbol \epsilon$, given $\boldsymbol z$ and $\boldsymbol \phi$
$$
\boldsymbol z = \boldsymbol g(\boldsymbol \epsilon, \boldsymbol \phi,\boldsymbol x)
$$
where the distribution of random variable $\boldsymbol \epsilon$ is independent of $\boldsymbol x$ and $\boldsymbol \phi$. 

Specifically, the distribution $q_{\boldsymbol \phi}(\boldsymbol z | \boldsymbol x)$ can be written as:
$$
\begin{aligned}
q_{\boldsymbol \phi} (\boldsymbol z | \boldsymbol x) &= \mathcal N(\boldsymbol z \mid \boldsymbol \mu_{\boldsymbol \phi}(\boldsymbol x), \ \sigma_{\boldsymbol \phi}^{2}(\boldsymbol x) \textbf{I})  \\
&= \boldsymbol \mu_{\boldsymbol \phi}(\boldsymbol x) + \sigma_{\boldsymbol \phi}(\boldsymbol x) \mathcal N(0, \textbf{I}) \\
&= \boldsymbol \mu_{\boldsymbol \phi}(\boldsymbol x) + \sigma_{\boldsymbol \phi}(\boldsymbol x) \boldsymbol \epsilon
\end{aligned}
$$
where $\boldsymbol \epsilon \sim \mathcal N(0, \textbf{I})$. By this way, the gradient of the loss function can be back-propagated to the parameter $\boldsymbol \phi$
![[AI-VAE-Reparameterization.png]]
# Visualization of Latent Space
The main benefit of a variational autoencoder is that we're capable of learning **smooth** latent state representations of the input data.

For standard autoencoders, **we simply need to learn an encoding which allows us to reproduce the input**. As you can see in the left-most figure, focusing only on reconstruction loss does allow us to separate out the classes (in this case, MNIST digits).

However, there's an **uneven** distribution of data within the latent space. In other words, there are areas in latent space which don't represent **any** of our observed data. **So we cannot just simply sample from the latent space to generate realistic images.**
![[AI-VAE-on-MNIST.png]]
On the flip side, if we only focus only on ensuring that the latent distribution is similar to the prior distribution (through our KL divergence loss term), we end up describing **every** observation using the same unit Gaussian. **So we failed to describe the original data from the latent space.**

![[AI-VAE-Latent-Space-Visualization.png]]