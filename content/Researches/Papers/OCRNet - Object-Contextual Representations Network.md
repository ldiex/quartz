---
zotero-key: HQ37DLXJ
zt-attachments:
  - "229"
title: "Segmentation Transformer: Object-Contextual Representations for Semantic Segmentation"
authors:
  - Yuhui Yuan
  - Xiaokang Chen
  - Xilin Chen
  - Jingdong Wang
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2021
url: http://arxiv.org/abs/1909.11065
DOI: 10.48550/arXiv.1909.11065
---
# Idea
- For each pixel, aggregating the pixel with its region information (the category this pixel belongs to predicted by the backbone network, regularized by the ground-truth segmentation with a auxiliary loss during training) to obtain **Object Region Representations**
- Compute the relation between each pixel and each object region, and augment the representation of each pixel with the object-contextual representation which is a weighted aggregation of all the object region representations. 
![[AI-OCRNet-Arch.png]]
# Segmentation Transformer
The pipeline above can be rephrased into the following [[Transformer - Attention Is All You Need|transformer]] encoder-decoder architecture
![[AI-OCRNet-Segmentation-Transformer.png]]