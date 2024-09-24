---
zotero-key: KMJ3L9CN
zt-attachments:
  - "376"
title: Masked-attention Mask Transformer for Universal Image Segmentation
authors:
  - Bowen Cheng
  - Ishan Misra
  - Alexander G. Schwing
  - Alexander Kirillov
  - Rohit Girdhar
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2112.01527
DOI: 10.48550/arXiv.2112.01527
---
# Idea
Based on [[MaskFormer - Per-Pixel Classification is Not All You Need for Semantic Segmentation|MaskFormer]], 
- Apply **masked attention** in the decoder
- Use multi-scale **high-resolution features**
# Architecture
Difference from [[MaskFormer - Per-Pixel Classification is Not All You Need for Semantic Segmentation|MaskFormer]]:
![[AI-Mask2Former-Arch.png]]
# Masked Attention
Constrain cross-attention within predicted mask regions, other than the whole image

From ($l$ is the layer index, and $\textbf{X}_l$ is the query features at $l$-th layer)
$$
\textbf{X}_l = \mathrm{softmax}(\textbf{Q}_l \textbf{K}_l^T ) \textbf{V}_l+ \textbf{X}_{l-1}, \quad \textbf{X}_l\in \mathbb{R}^{N \times C}
$$
to
$$
\textbf{X}_l = \mathrm{softmax}(\boldsymbol{\mathcal M}_{l -1} + \textbf{Q}_l \textbf{K}_l^T) \textbf{V}_l + \textbf{X}_{l-1}, \quad \textbf{X}_l\in \mathbb{R}^{N \times C}
$$
where
$$
\boldsymbol{\mathcal M}_{l-1} (x, y) = \begin{cases}
0, &\text{if } \textbf{M}_{l-1} (x, y) = 1  \\
-\infty &\text{otherwise}
\end{cases}
$$
here $\textbf{M}_{l-1}\in \left\{ 0,1 \right\}^{N \times H_lW_l}$ is the binarized output (with threshold at $0.5$) of the resized mask prediction of the previous $(l-1)$-th Transformer decoder layer
# High-resolution features
Instead of always using the high-resolution feature map, utilize a feature pyramid which consists of both low- and high-resolution features and feed one resolution of the multi-scale feature to one Transformer decoder layer at a time.

Specifically, use the feature map produced by the pixel decoder with resolution $\dfrac{1}{32}$, $\dfrac{1}{16}$ and $\dfrac{1}{8}$ of the original image.