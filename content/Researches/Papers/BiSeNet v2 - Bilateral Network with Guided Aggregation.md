---
zotero-key: 6YV3RRX7
zt-attachments:
  - "237"
title: "BiSeNet V2: Bilateral Network with Guided Aggregation for Real-time Semantic Segmentation"
authors:
  - Changqian Yu
  - Changxin Gao
  - Jingbo Wang
  - Gang Yu
  - Chunhua Shen
  - Nong Sang
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2020
url: http://arxiv.org/abs/2004.02147
DOI: 10.48550/arXiv.2004.02147
---
# Idea
## Inherited from [[BiSeNet - Bilateral Segmentation Network for Real-time Semantic Segmentation|BiSeNet v1]]:
- **Detail Branch**, with wide channels and shallow layers to capture low-level details and generate high-resolution feature representation
- **Semantic Branch**, with narrow channels and deep layers to obtain high-level semantic context (lightweight with a fast-downsampling strategy)
## Improvements
- **Guided Aggregation Layer** to enhance mutual connections and fuse both types of feature representation
- **Booster Training Strategy**
# Architecture
![[AI-BiSeNet-v2-Arch.png]]
## Context Embedding Block
Uses the [[Global Pooling#Global Average Pooling|global average pooling]] and residual connection to embed the global contextual information efficiently
## Guided Aggregation Layer
![[AI-BiSeNet-v2-Guided-Aggregation-Layer.png]]
## Booster Training Strategy
Insert the auxiliary segmentation head to different position of the Semantic Branch, enhancing the feature representation in the training phase