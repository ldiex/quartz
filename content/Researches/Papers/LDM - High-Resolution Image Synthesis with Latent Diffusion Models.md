---
zotero-key: 5BGVE2ZZ
zt-attachments:
  - "681"
title: High-Resolution Image Synthesis with Latent Diffusion Models
authors:
  - Robin Rombach
  - Andreas Blattmann
  - Dominik Lorenz
  - Patrick Esser
  - Björn Ommer
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2112.10752
DOI: 10.48550/arXiv.2112.10752
---
# Idea
Lower the computational cost of [[Denoising Diffusion Probabilistic Models (DDPM)|diffusion models]] by performing the denoising process in a low dimensional latent space.
![[AI-Latent-Diffusion.svg]]
# VAE
## KL Regularization (KL-reg)
This method applies a [[Kullback–Leibler Divergence]] penalty, which helps push the latent space distribution to match a standard normal distribution. This is similar to a [[Variational Auto-Encoder (VAE)|VAE]], where the KL-divergence between the learned latent distribution and a prior (usually normal) is minimized. It prevents the latent space from becoming overly spread out or having high variance.
## Vector Quantization Regularization (VQ-reg)
In this variant, the model incorporates **vector quantization (VQ)** into the decoder. Vector quantization means that instead of a continuous latent space, the latent representations are discretized into a set of predefined "codebook" vectors. This method is associated with **VQGAN (Vector Quantized Generative Adversarial Network)**, which uses a similar mechanism. However, in this case, the quantization is **absorbed by the decoder**, simplifying the architecture.
> [!Note]
> This is not a [[VQ-VAE - Neural Discrete Representation Learning|VQ-VAE]]
## Latent Space and Compression
The learned latent space $z=\mathcal E(x)$, where $\mathcal E(x)$ is the encoder mapping the input to the latent space, is structured in two dimensions. This is important because the latent diffusion model (DM) works with a **two-dimensional latent space**, preserving more structure and detail from the input xxx.

In contrast to other works that use a 1D latent representation (ignoring much of the structure), this model uses a mild compression rate, leading to **better reconstructions** of the input.