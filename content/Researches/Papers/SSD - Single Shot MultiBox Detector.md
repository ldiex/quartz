---
zotero-key: 9YXLKG8Q
zt-attachments:
  - "436"
title: "SSD: Single Shot MultiBox Detector"
authors:
  - Wei Liu
  - Dragomir Anguelov
  - Dumitru Erhan
  - Christian Szegedy
  - Scott Reed
  - Cheng-Yang Fu
  - Alexander C. Berg
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2016
url: http://arxiv.org/abs/1512.02325
---
# Idea
Another real-time object detection model faster than [[YOLO v1 - You Only Look Once|YOLO]]. The core of SSD is predicting category scores and box offsets for a fixed set of default bounding boxes using small convolutional filters applied to feature maps

# Method
![[AI-SSD-Framework.png]]
- Evaluate a small set (e.g. $4$ in the figure above) of default boxes (just like the **anchors** in [[Faster R-CNN]]) of different aspect ratios at each location in several feature maps with different scales (e.g $8 \times 8$ and $4 \times 4$ in (b) and (c) ). 
- For each default box, predict both the shape offsets and the confidences for all object categories ($c_1,c_2, \ldots ,c_p$)
# Architecture
![[AI-SSD-Arch.png]]
- The model is bases on a standard classification network
- Convolutional feature layers are added to the end of the backbone network. These layers decrease in size progressively and allow predictions of detections at multiple scales.
- For each feature layer of size $m \times n$ with $p$ channels, the basic element for predicting parameters of a potential detection is a $3 \times 3 \times p$ small kernel that produces either **a score for a category**, or **a shape offset relative to the default boxes coordinates**. At each of the $m \times n$ locations where the kernel is applied, it produces an output value.