---
zotero-key: CTQS2ZVD
zt-attachments:
  - "425"
title: Mask R-CNN
authors:
  - Kaiming He
  - Georgia Gkioxari
  - Piotr Dollár
  - Ross Girshick
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2018
url: http://arxiv.org/abs/1703.06870
DOI: 10.48550/arXiv.1703.06870
---
# Motivation
- Extend [[Faster R-CNN]] by **adding a branch for predicting an object mask** in parallel with the existing branch for bounding box recognition
- The mask branch is a small [[FCN - Fully Convolutional Networks for Semantic Segmentation|FCN]] applied to each RoI, predicting a segmentation mask in a pixel-to-pixel manner.
# Architecture
![[AI-Mask-RCNN-Arch.png]]
## Procedure
Mask R-CNN adopts the same two-stage procedure as [[Faster R-CNN]], with an identical first stage (which is [[Faster R-CNN#Region Proposal Network (RPN)|RPN]]). In the second stage, in parallel to predicting the class and box offset, Mask R-CNN **also outputs a binary mask for each RoI** via a small [[FCN - Fully Convolutional Networks for Semantic Segmentation|FCN]]

Formally, during training, we define a multi-task loss on each sampled RoI as $L = L_\text{cls} + L_\text{box} + L_\text{mask}$, where $L_\text{cls}$ and $L_\text{box}$ are identical as Faster R-CNN. The mask branch has a $Km^{2}$-dimensional output for each RoI, which encodes $K$ binary masks of resolution $m \times m$, one for each of the $K$ classes. To this we apply a per-pixel [[Sigmoid Function|sigmoid]], and define $L_\text{mask}$ as the average binary cross-entropy loss. For an RoI associated with ground-truth class $k$, $L_\text{mask}$ is only defined on the $k$-th mask.



