---
zotero-key: TPXEYDQK
zt-attachments:
  - "214"
title: Dual Attention Network for Scene Segmentation
authors:
  - Jun Fu
  - Jing Liu
  - Haijie Tian
  - Yong Li
  - Yongjun Bao
  - Zhiwei Fang
  - Hanqing Lu
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2019
url: http://arxiv.org/abs/1809.02983
DOI: 10.48550/arXiv.1809.02983
---
# Idea
Append two types of attention modules on top of dilated [[FCN - Fully Convolutional Networks for Semantic Segmentation|FCN]], which model the sematic interdependencies in spatial and channel dimensions respectively.
# Architecture
![[AI-DAN-Arch.png]]
# Dual Attention Module
![[AI-DAN-Attention-Module.png]]
## Positional Attention Module
Just like the attention mechanism in [[Transformer - Attention Is All You Need|Transformer]], here we may consider $\textbf{B}$ as *key*, $\textbf{C}$ as *query* and $\textbf{D}$ as *value*. The difference is that here we apply convolution layers instead of a linear layer to convert $\textbf{A}$ to $\textbf{B}$, $\textbf{C}$ and $\textbf{D}$. The final self-attention score is 
$$
\textbf{S} = \mathrm{Softmax}\left( \textbf{B}^T\textbf{C} \right) \textbf{D}
$$
## Channel Attention Module
Apply channel-wise self-attention