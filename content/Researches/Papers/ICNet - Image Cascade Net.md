---
zotero-key: YMXE2PJP
zt-attachments:
  - "202"
title: ICNet for Real-Time Semantic Segmentation on High-Resolution Images
authors:
  - Hengshuang Zhao
  - Xiaojuan Qi
  - Xiaoyong Shen
  - Jianping Shi
  - Jiaya Jia
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2018
url: http://arxiv.org/abs/1704.08545
DOI: 10.48550/arXiv.1704.08545
---
# Idea
Based on [[PSPN - Pyramid Scene Parsing Network|PSPNet]], make it faster and suitable for real-time semantic segmentation on high-resolution images.

# Architecture
![[AI-ICNet-Arch.png]]
## Cascade Image Input
Apply muti-resolution inputs. Though some details are missing and blurry boundaries are generated in the top branch, it already harvests most semantic parts. Therefore, we can safely limit the number of parameters in both middle and bottom branches.

**Light weighted [[Convolutional Neural Networks (CNNs)|CNNs]] are adopted in higher resolution branches.**
## Cascade Feature Fusion
![[AI-ICNet-Cascade-Feature-Fusion.png]]
The inputs are:
- two feature maps $F_1$ and $F_2$ with sizes $C_1 \times H_1 \times W_1$ and $C_2 \times H_2 \times W_2$ respectively
- one ground-truth label with resolution $1 \times H_2 \times W_2$
The outputs are:
- one concatenated feature map $F_2$ with sizes $C_3 \times H_2 \times W_2$
- one auxiliary loss (**cascade label guidance**)
