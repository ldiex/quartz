---
zotero-key: MQLV88KA
zt-attachments:
  - "222"
title: Asymmetric Non-local Neural Networks for Semantic Segmentation
authors:
  - Zhen Zhu
  - Mengde Xu
  - Song Bai
  - Tengteng Huang
  - Xiang Bai
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2019
url: http://arxiv.org/abs/1908.07678
DOI: 10.48550/arXiv.1908.07678
---
# Idea
Another improvement for [[Non-local Neural Networks]]
- Embed a **pyramid sampling module** (See [[PSPN - Pyramid Scene Parsing Network|PSPNet]]) into non-local blocks, which could largely reduce the computation cost yet provide substantial semantic feature statistics
- Use the same method not only for the self-attention computation, but also to calculate the correlations between every pixel of the low-level and high-level feature maps 
# Architecture
![[AI-ANN-Arch.png]]
## Pyramid Pooling Could Reduce Computational Cost
![[AI-ANN-Paramid-Pooling.png]]