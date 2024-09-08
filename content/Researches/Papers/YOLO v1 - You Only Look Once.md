---
zotero-key: UEL3JDQ5
zt-attachments:
  - "404"
title: "You Only Look Once: Unified, Real-Time Object Detection"
authors:
  - Joseph Redmon
  - Santosh Divvala
  - Ross Girshick
  - Ali Farhadi
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2016
url: http://arxiv.org/abs/1506.02640
DOI: 10.48550/arXiv.1506.02640
---
# Idea
Use a single neural network to predict bounding boxes and class probabilities directly from full images in one evaluation.
# Method
- Divide the input image into an $S \times S$ grid. If the center of an object falls into a grid cell, that grid cell is responsible for detecting that object
- Each grid cell predicts $B$ bounding boxes and confidence scores for those boxes. These confidence score reflect how confident the model is that the box contains an object and also how accurate it thinks the box is that it predicts.
- Each gird cell also predicts $C$ conditional class probabilities. These probabilities are conditioned on the grid cell containing an object. The model only predict one set of class probabilities per gird cell, regardless of the number of boxes $B$
- Therefore, the predictions are encoded as an $S \times S \times (5B+C)$ tensor
![[AI-YOLO-v1-Method.png]]
# Architecture
![[AI-YOLO-v1-Arch.png]]
Apply $20$ convolutional layers pre-trained on ImageNet
# Loss Function
$$
\begin{aligned}
\mathcal L &= \lambda_\text{coord} \sum_{i = 0}^{S^{2}} \sum_{j = 0}^B  \mathbb{1}_{ij}^\text{obj} \left[ (x_i - \hat{x}_i)^{2} + (y_i -\hat{y}_i)^{2} \right] \\
&+ \lambda_\text{coord} \sum_{i = 0}^{S^{2}} \sum_{j = 0}^B  \mathbb{1}_{ij}^\text{obj} \left[ (\sqrt{ w_i }-\sqrt{ \hat{w}_i })^{2} + (\sqrt{ h_i }-\sqrt{ \hat{h}_i })^{2} \right] \\
&+ \sum_{i = 0}^{S^{2}}\sum_{j = 0}^B \mathbb{1}_{ij}^\text{obj} \left( C_i - \hat{C}_i \right) ^{2} + \lambda_\text{noobj} \sum_{i = 0}^{S^{2}} \sum_{j = 0}^B  \mathbb{1}_{ij}^\text{noobj} \left( C_i - \hat{C}_i \right)^{2} \\
&+ \sum_{i = 0}^{S^{2}} \mathbb{1}_{i}^\text{obj} \left( p_i(c) - \hat{p}_i (c) \right) ^{2}
\end{aligned}
$$
where the $x,y$ coordinates represent the center of the box relative the bounds of the grid cell. and the width $w$ and height $h$ are predicted relative to the whole image
