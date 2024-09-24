---
zotero-key: J8LAJN9E
zt-attachments:
  - "105"
title: "Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks"
authors:
  - Shaoqing Ren
  - Kaiming He
  - Ross Girshick
  - Jian Sun
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2016
url: http://arxiv.org/abs/1506.01497
DOI: 10.48550/arXiv.1506.01497
---

# Motivation
- Selective search is slow in [[R-CNN - Rich feature hierarchies for accurate object detection and semantic segmentation|R-CNN]] and [[Fast R-CNN]] 
- Use a single CNN to generate region proposals
# Architecture
![[AI-Faster-RCNN-Arch.png]]
## Region Proposal Network (RPN)
To generate region proposals, we slide a small network over the convolution feature map output by the last shared convolution layer. This small network takes as input an $n \times n$ spatial windows of the input convolutional feature map. Each sliding windows is mapped to a lower-dimensional feature.

This feature is fed into two sibling fully-connected layers
- box-regression layer (`reg`)
- box-classification layer (`cls`)
Note that the mini-network operates in a sliding-window fashion, the fully-connected layers are shared across all spatial locations.

At each sliding-window location, we simultaneously predict multiple region proposals, where the number of maximum possible proposals for each location is denoted as $k$. Then, 
- the `reg` layer has $4k$ outputs encoding the coordinates of $k$ boxes
- the `cls` layer outputs $2k$ scores that estimate probability of **object** or **not object** for each proposal
## Anchor Boxes
The $k$ proposals are parameterized **relative** to $k$ reference boxes, which we call *anchors*. The network predicted the **offsets** that indicate how much the anchor box needs to be modified to better fit the actual object in the image.
![[AI-Faster-RCNN-Region-Proposal-Network.png]]