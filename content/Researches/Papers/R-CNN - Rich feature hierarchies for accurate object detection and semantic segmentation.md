---
zotero-key: 4TRDCH9P
zt-attachments:
  - "97"
title: Rich feature hierarchies for accurate object detection and semantic segmentation
authors:
  - Ross Girshick
  - Jeff Donahue
  - Trevor Darrell
  - Jitendra Malik
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2014
url: http://arxiv.org/abs/1311.2524
DOI: 10.48550/arXiv.1311.2524
---
# Idea
Convert detection problem to classification problem
# Architecture
![[AI-R-CNN-Arch.png]]
## Region Proposals
Usually generated by **selective search**
## Feature Extraction
Before warping, the region size is expanded to a new size that will result in $16$ pixels of context in the warped frame. The [[Convolutional Neural Networks (CNNs)|CNN]] used is AlexNet and it is typically fine-tuned on a large dataset like ImageNet for generic feature representation.
![[AI-R-CNN-Warping.png]]
## Object Classification
The extracted feature vectors from the region proposals are fed into a separate machine learning classifier for each object class of interest. R-CNN typically uses **Support Vector Machines (SVMs)** for classification. For each class, a unique SVM is trained to determine whether or not the region proposal contains an instance of that class.