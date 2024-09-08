---
zotero-key: RANCH6QM
zt-attachments:
  - "101"
title: Fast R-CNN
authors:
  - Ross Girshick
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2015
url: http://arxiv.org/abs/1504.08083
DOI: 10.48550/arXiv.1504.08083
---
# Motivation
- [[R-CNN - Rich feature hierarchies for accurate object detection and semantic segmentation|R-CNN]] is slow because it performs a [[Convolutional Neural Networks (CNNs)|CNN]] forward pass for each object proposal, without sharing computation
- The **selective search** process is also time-consuming (The paper does not optimize this)
![[AI-Fast-R-CNN-Arch.png]]
# Method
1. Input the image and use **selective search** to generate object proposals ($\approx2000$)
2. Pass the **whole** input image into a CNN to extract feature maps
3. Apply **RoI Pooling** to extract feature map for each object proposal (**Key Optimization:** here the input of pooling is the projection of the CNN feature map output on these object proposals, therefore we save the CNN forward computing time)
4. Compute the classification loss and box regression loss
## RoI Pooling
Just like [[SPP-Net - Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition|SPP]], pool the input with multiple sizes into some fixed-size feature maps.