---
zotero-key: LL5K85ZH
zt-attachments:
  - "225"
title: "GCNet: Non-local Networks Meet Squeeze-Excitation Networks and Beyond"
authors:
  - Yue Cao
  - Jiarui Xu
  - Stephen Lin
  - Fangyun Wei
  - Han Hu
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2019
url: http://arxiv.org/abs/1904.11492
DOI: 10.48550/arXiv.1904.11492
---
# Idea
![[AI-GCNet-Non-Local-Attention-Map-Visualization.png]]
Visualization shows that the global contexts modeled by [[Non-local Neural Networks]] **are almost the same** for different query positions within an image (The figure above shows the attention maps for different query positions (red points) in a non-local block on COCO object detection)

Therefore, we could simplify the non-local block by **explicitly using a query-independent attention map for all query positions**. Then we add the same aggregated features using the attention map to the features of all query positions to form the output
# Simplify the Non-local Block
![[AI-GCNet-Simplified-NL-Block.png]]

