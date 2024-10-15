---
zotero-key: A7XN4M8X
zt-attachments:
  - "685"
title: Scalable Diffusion Models with Transformers
authors:
  - William Peebles
  - Saining Xie
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2023
url: http://arxiv.org/abs/2212.09748
DOI: 10.48550/arXiv.2212.09748
---
# Motivation
Replace the commonly-used U-Net backbone with a transformer that operates on latent patches in [[LDM - High-Resolution Image Synthesis with Latent Diffusion Models|latent diffusion]]

![[AI-DiT-Arch.png]]
# `adaLN-Zero` Block
## Adaptive Layer Normalization (`AdaLN`)
 `AdaLN` is designed to adaptively normalize layer outputs based on task-specific characteristics. It allows models to efficiently handle different types of data (e.g., images from various domains) without needing separate models for each task.

In contrast to standard layer normalization, which applies fixed scaling and shifting parameters, `AdaLN` learns these parameters dynamically. Specifically, it regresses the scale and shift parameters ($\gamma$ and $\beta$) from the sum of the input embeddings, allowing for better adaptation to different tasks while maintaining a shared model architecture.

## `adaLN-Zero`
Unlike standard `AdaLN`, which uses **learned** parameters for scaling and shifting, `adaLN-Zero` starts with zero weights for these parameters. This means that initially, the output of the normalization layer does not alter the input, effectively allowing the model to learn from the raw input data without any initial bias introduced by these parameters


