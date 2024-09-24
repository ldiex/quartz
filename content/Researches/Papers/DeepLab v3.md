---
zotero-key: N396QIBQ
zt-attachments:
  - "188"
title: Rethinking Atrous Convolution for Semantic Image Segmentation
authors:
  - Liang-Chieh Chen
  - George Papandreou
  - Florian Schroff
  - Hartwig Adam
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2017
url: http://arxiv.org/abs/1706.05587
DOI: 10.48550/arXiv.1706.05587
---
# Architectures to Capture Multi-scale Context
![[AI-Alternative-Arch-Capture-Multi-Scale-Context.png]]
# Atrous Spatial Pyramid Pooling
Improve from [[DeepLab v1]]
![[AI-ASPP.png]]
## Method 
Four parallel atrous convolutions with different atrous rates are applied on top of the feature map. 
## Problem
As the sampling rate becomes larger, the number of valid filter weights (i.e., the weights that are applied to the valid feature region, instead of padded zeros) becomes smaller.
## Solution
Concatenate the pooling result with image level features. Specifically, apply [[Global Pooling#Global Average Pooling|global average pooling]] on the last feature map of the model, feed the resulting image-level features to a $1 × 1$ convolution with $256$ filters (and [[Batch Normalization|batch normalization]]), and then bilinearly upsample the feature to the desired spatial dimension.

The resulting features from all the branches are then concatenated and pass through another $1 × 1$ convolution (also with $256$ filters and batch normalization) before the final $1 × 1$ convolution which generates the final logits.
