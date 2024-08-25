---
zotero-key: 2AM2QXPE
zt-attachments:
  - "173"
title: Pyramid Scene Parsing Network
authors:
  - Hengshuang Zhao
  - Jianping Shi
  - Xiaojuan Qi
  - Xiaogang Wang
  - Jiaya Jia
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2017
url: http://arxiv.org/abs/1612.01105
DOI: 10.48550/arXiv.1612.01105
---
# Scene Parsing vs Semantic Segmentation
| Feature               | Semantic Segmentation                    | Scene Parsing                              |
| --------------------- | ---------------------------------------- | ------------------------------------------ |
| **Focus**             | Classifies each pixel into categories    | Segments image into regions with semantics |
| **Instance Handling** | Does not differentiate instances         | Differentiates between instances           |
| **Complexity**        | Simpler, focuses on broad categorization | More complex, includes relationships       |
| **Applications**      | General scene understanding              | Detailed understanding of scene context    |
# Idea
The core innovation of *PSPNet* is its **Pyramid Pooling Module**. This module aggregates contextual information from different regions of the image by partitioning the feature map into several segments and applying pooling operations at multiple scales.
![[AI-PSPNet-Arch.png]]
# Method
The pyramid pooling module fuses features under four different pyramid scales. The coarsest level highlighted in red is [[Global Pooling|global pooling]] to generate a single bin output. The following pyramid level separates the feature map into different sub-regions and forms pooled representation for different locations. 

The output of different levels in the pyramid pooling module contains the feature map with varied sizes. To maintain the weight of global feature, we use $1×1$ convolution layer after each pyramid level to reduce the dimension of context representation to $1/N$ of the original one if the level size of pyramid is $N$ . Then we directly upsample the low-dimension feature maps to get the same size feature as the original feature map via bilinear interpolation. Finally, different levels of features are concatenated as the final pyramid pooling global feature.