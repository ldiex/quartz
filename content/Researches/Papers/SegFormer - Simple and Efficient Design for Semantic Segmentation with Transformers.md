---
zotero-key: JRWP5K2T
zt-attachments:
  - "249"
title: "SegFormer: Simple and Efficient Design for Semantic Segmentation with Transformers"
authors:
  - Enze Xie
  - Wenhai Wang
  - Zhiding Yu
  - Anima Anandkumar
  - Jose M. Alvarez
  - Ping Luo
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2021
url: http://arxiv.org/abs/2105.15203
DOI: 10.48550/arXiv.2105.15203
---
# Idea
Another application of [[Vision Transformer (ViT)]] in [[Semantic Segmentation|semantic segmentation]], with
- **Hierarchical Transformer Encoder** to produce multiscale features. *Mix-FFN* proves $3 \times 3$ convolution is enough to provide positional information **so that the positional encoding can be avoided**.
- **Lightweight MLP Decoder** combines both local and global attention mechanisms, allowing the model to generate powerful representations without the complexity typically associated with traditional decoders
# Architecture
![[AI-SegFormer-Arch.png]]
## Overlap Patch Merging
Allows for the unification of features from overlapping patches, which enhances the model's ability to preserve local details. Compared to non-overlap patch merging (e.g. in [[Swin Transformer]]), this approach improves **local continuity** and supports flexible input sizes.
