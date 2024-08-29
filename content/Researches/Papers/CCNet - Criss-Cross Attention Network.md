---
zotero-key: 93BLFW99
zt-attachments:
  - "218"
title: "CCNet: Criss-Cross Attention for Semantic Segmentation"
authors:
  - Zilong Huang
  - Xinggang Wang
  - Yunchao Wei
  - Lichao Huang
  - Humphrey Shi
  - Wenyu Liu
  - Thomas S. Huang
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2020
url: http://arxiv.org/abs/1811.11721
DOI: 10.48550/arXiv.1811.11721
---
# Idea
To improve the [[Non-local Neural Networks|Non-local]] mechanism, for each pixel, we don't need to compute the attention scores of all the pixels in its region of interest. Instead, if in a module we just collect the contextual information in horizontal and vertical directions, then after feeding the result of the first module to a second one, the additional contextual information obtained form the criss-cross path finally enables the full image dependencies of all positions.
![[AI-CCNet-Criss-Cross-Attention-Block.png]]
# Architecture
![[AI-CCNet-Arch.png]]
## Criss-Cross Attention Module
![[AI-CCNet-Criss-Cross-Attention-Module.png]]