---
zotero-key: E3DE29MY
zt-attachments:
  - "719"
title: Progressive Distillation for Fast Sampling of Diffusion Models
authors:
  - Tim Salimans
  - Jonathan Ho
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2202.00512
DOI: 10.48550/arXiv.2202.00512
---
# Progressive Distillation Method 
## Idea
The core idea involves a distillation process where a pre-trained "teacher" model, which requires a high number of sampling steps (up to 8192), is used to train a "student" model that takes significantly fewer steps. This distillation is progressively applied, effectively halving the number of required sampling steps at each iteration. Remarkably, this approach allows for models that can generate samples in as few as 4 steps while still maintaining high perceptual quality
## Method
**Require:**
- Trained teacher model $\hat{x}_\eta(z_t)$
- Data set $\mathcal{D}$
- Loss weight function $w()$
- Student sampling steps $N$
---
**For** $K$ iterations **do**
1. $\theta \leftarrow \eta$ ⟶ Init student from teacher
    **While** not converged **do**
    - $\mathbf{x} \sim \mathcal{D}$
    - $t = i / N,\ i \sim \text{Cat}[1, 2, \dots, N]$
    - $\epsilon \sim \mathcal{N}(0, \mathbb{I})$
    - $z_t = \alpha_t \mathbf{x} + \sigma_t \epsilon$
    - 2 steps of DDIM with teacher
    - $t' = t - 0.5 / N, \ t'' = t - 1 / N$
    - $z_{t'} = \alpha_{t'} \hat{x}_\eta(z_t) + \frac{\sigma_{t'}}{\sigma_t}(z_t - \alpha_t \hat{x}_\eta(z_t))$
    - $z_{t''} = \alpha_{t''} \hat{x}_\eta(z_{t'}) + \frac{\sigma_{t''}}{\sigma_{t'}}(z_{t'} - \alpha_{t'} \hat{x}_\eta(z_{t'}))$
    - $\hat{x} = \dfrac{z_t'' - (\sigma_{t''} / \sigma_t)z_t}{\alpha_{t''} - (\sigma_{t'} / \sigma_t) \alpha_t}$ ⟶ Teacher $\hat{x}$ target
    - $\lambda_t = \log\left(\frac{\alpha_t^2}{\sigma_t^2}\right)$
    - $L_\theta = w(\lambda_t) \left\| \hat{x} - \hat{x}_\theta(z_t) \right\|_2^2$
    - $\theta \leftarrow \theta - \gamma \nabla_\theta L_\theta$
    **End while**
2. $\eta \leftarrow \theta$ ⟶ Student becomes next teacher
3. $N \leftarrow N / 2$ ⟶ Halve number of sampling steps
**End for**
---
Where the target $\hat{x}$ is set to $\dfrac{z_t'' - (\sigma_{t''} / \sigma_t)z_t}{\alpha_{t''} - (\sigma_{t'} / \sigma_t) \alpha_t}$ such that if we use the student model to sample $1$ [[Denoising Diffusion Implicit Models (DDIM)|DDIM]] step from $z_t$ using the mean determined by $\hat{x}$ (with zero variance in DDIM), then the denoised result $z_{t'}'$  should equal to $z_{t''}$, which the the denoised result of the teacher model after $2$ DDIM steps with the mean determined by $\hat{x}_\eta$

# New parameterization method: v-prediction
## Idea
The authors proposed an alternative method of **v-prediction**, which involves predicting a latent variable $v$ instead of directly predicting the noise $\epsilon$. This approach provides more stable training dynamics, particularly when distilling diffusion models to fewer steps. The relationship between $v$ and $\epsilon$ is defined through the following key ideas:
- $v$ is a transformation of both the original data and the noise.
- By predicting $v$, the model can smoothly transition between steps, allowing it to interpolate between predicting the noise $\epsilon$ directly and predicting the clean data.
## Formulation
For two times $s, t\in[0, 1]$, we want to update from $t$ to $s$ ($t > s$), and the update rule given by DDIM is
$$
z_s = \alpha_s x_s + \sigma_s\epsilon_s = \alpha_s \hat{x}_\theta(z_t) + \sigma_s \dfrac{z_t - \alpha_t \hat{x}_\theta(z_t)}{\sigma _t}
$$
We can simplify the DDIM update rule by expressing it in terms of $\phi_t = \arctan(\sigma_t / \alpha_t)$. Assuming a variance preserving diffusion process, we have $\alpha_\phi = \cos(\phi),\ \sigma_\phi=\sin(\phi)$, and hence
$$
z_\phi = \cos(\phi) x + \sin (\phi) \epsilon
$$
And we define the velocity of $z_\phi$
$$
v_\phi = \frac{ \mathrm{d} z_\phi }{ \mathrm{d} \phi } = \cos(\phi) \epsilon - \sin(\phi) x
$$
Furthermore, we define the predicted velocity as
$$
\hat{v}_\theta (z_\phi) = \cos (\phi) \hat{\epsilon}_\theta(z_\phi) - \sin (\phi) \hat{x}_\theta (z_\phi)
$$
where $\hat{\epsilon}_\theta(z_\phi) = (z_\phi - \cos(\phi)\hat{x}_{\theta} (z  _\phi)) / \sin(\phi)$. And now we have
$$
\begin{aligned}
z_{\phi_s} &= \cos(\phi_s) \hat{x}_\theta (z_{\phi_t}) + \sin(\phi_s) \hat{\epsilon}_\theta (z_{\phi_t}) \\
&= \cos(\phi_s) \left( \cos(\phi_t)z_{\phi_t} - \sin(\phi_t)\hat{v}_\theta (z_{\phi_t}) \right) + \sin(\phi_s) \left( \sin(\phi_t) z_{\phi _t} + \cos(\phi_t) \hat{v}_{\theta}(z_{\phi_t}) \right)  \\
&= \cos(\phi_s - \phi_t) z_{\phi_t} + \sin(\phi _s- \phi_t) \hat{v}_\theta (z_{\phi_t})
\end{aligned}
$$
Viewed from this perspective, DDIM thus evolves $z_{\phi_s}$ by moving it on a circle in the $(z_{\phi_t}, \hat{v}_{\phi_t})$ basis, along the $-\hat{v}_{\phi_t}$ direction, gradually denoising smoothly towards $x$
![[AI-v-prediction.png]]