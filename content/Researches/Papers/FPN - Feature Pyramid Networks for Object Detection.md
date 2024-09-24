---
zotero-key: AFURHPNR
zt-attachments:
  - "418"
title: Feature Pyramid Networks for Object Detection
authors:
  - Tsung-Yi Lin
  - Piotr Dollár
  - Ross Girshick
  - Kaiming He
  - Bharath Hariharan
  - Serge Belongie
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2017
url: http://arxiv.org/abs/1612.03144
DOI: 10.48550/arXiv.1612.03144
---
# Motivation
- Feature pyramids are a basic component in recognition systems for detecting objects at different scales.
- Deep learning object detectors avoid pyramid representation, in part because they are compute and memory intensive.
- We develop a **top-down** architecture with lateral connections for building high-level semantic feature maps at all scales, called *Feature Pyramid Network (FPN)*

# Pyramid Usage in Detection
![[AI-FPN-Four-Kinds-Pyramids.png]]
- **(a) Using an image pyramid to build a feature pyramid:** Features are computed on each of the image scales independently, which is slow.
- **(b) Use only single scale features for fast detection:** such as [[Fast R-CNN]], [[Faster R-CNN]], [[SPP-Net - Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition|SPP-Net]]
- **(c) Reuse the pyramidal feature hierarchy computed by a ConvNet as if it were a featurized image pyramid:** like [[SSD - Single Shot MultiBox Detector|SSD]]
- **(d) Feature Pyramid Network:** fast and accurate
# Architecture
## Bottom-up pathway
The bottom-up pathway is the feed-forward computation of the backbone ConvNet, which computes a feature hierarchy consisting of feature maps at several scales with a scaling step of $2$. 

There are often many layers producing output maps of the same size and we say these layers are in the same network **stage**. For our feature pyramid, we choose the output of the last layer of each stage as our **reference set of feature maps**.

## Top-down pathway and lateral connections
The top-down pathway hallucinates higher resolution features by upsampling **spatially coarser**, but **semantically stronger**, feature maps from higher pyramid levels.

These features are then enhanced with features from the bottom-up pathway via **lateral connections**. Each lateral connection merges feature maps of the same spatial size from the bottom-up feature map and the top-down pathway.
![[AI-FPN-Lateral-Connection.png]]
