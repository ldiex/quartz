---
zotero-key: 3WZ86D4D
zt-attachments:
  - "415"
title: "YOLO9000: Better, Faster, Stronger"
authors:
  - Joseph Redmon
  - Ali Farhadi
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2016
url: http://arxiv.org/abs/1612.08242
DOI: 10.48550/arXiv.1612.08242
---
# Motivation
An improvement of [[YOLO v1 - You Only Look Once|YOLO v1]], and generated a bigger object detection dataset.
# Better (Accuracy Improvement)
- Apply [[Batch Normalization]]
- Use **high resolution** classifier backbone, like [[SSD - Single Shot MultiBox Detector|SSD]]
- Use **anchor boxes** instead of directly predicting the exact coordinates, like [[Faster R-CNN]], [[SSD - Single Shot MultiBox Detector|SSD]]
- Other than hand-pick the dimensions (heights and weights) of the anchor boxes, the new architecture first collect the ground truth dimensions in the training data and then **run $k$-means** to find out the best dimensions
- Predict the positions of box center $x, y$ using **relative coordinates** (so that $x, y$ fall in $(0,1)$) instead of exact positions
-  Get the features of multi-scale objects via a **pass-through** layer to concatenate the low-level features with high level features (while [[Faster R-CNN]] and [[SSD - Single Shot MultiBox Detector|SSD]] run their proposal networks on feature maps with different sizes)
# Faster
- Use customized backbone network *Darknet-19*

# Stronger (More Categories Supported)
Since object detection datasets are way more limited than classification datasets, the author proposes a mechanism for **jointly training on classification and detection data**.

When the network sees an image labelled for detection it can back-propagate based on the full YOLOv2 loss function. When it sees a classification image we only back-propagate loss from the classification-specific parts of the architecture.

## Hierarchical Classification

