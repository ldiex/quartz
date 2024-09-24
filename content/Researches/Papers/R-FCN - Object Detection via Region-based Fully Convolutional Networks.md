---
zotero-key: WZ7QYIZS
zt-attachments:
  - "412"
title: "R-FCN: Object Detection via Region-based Fully Convolutional Networks"
authors:
  - Jifeng Dai
  - Yi Li
  - Kaiming He
  - Jian Sun
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2016
url: http://arxiv.org/abs/1605.06409
DOI: 10.48550/arXiv.1605.06409
---
# Motivation
- Previous region-based detectors such as [[Fast R-CNN]] and [[Faster R-CNN]] apply a costly per-region subnetwork hundreds of times
- Instead, use a fully convolutional network with almost computation shared on the entire image
That is, from
```
feature_maps = process(image)  
ROIs = region_proposal(feature_maps)  
for ROI in ROIs  
	patch = roi_pooling(feature_maps, ROI)  
	class_scores, box = detector(patch)  
	class_probabilities = softmax(class_scores)
```
To
```
feature_maps = process(image)  
ROIs = region_proposal(feature_maps)  
score_maps = compute_score_map(feature_maps)  
for ROI in ROIs  
	V = region_roi_pool(score_maps, ROI)  
	class_scores, box = average(V) # Much simpler!  
	class_probabilities = softmax(class_scores)
```
# General Idea
If we need to detect the position of a human face, the traditional approach is to develop a feature map for this category. However, if we have other feature maps specialized in detecting the left eye, the nose or the mouth, we can combine information together to make face detection easier and more accurate. 

To generalize this solution, we create 9 **region-based** **feature maps** each detecting the top-left, top-middle, top-right, middle-left, … or bottom-right area of an object. By combing the votes from these feature maps, we determine the class and the location of the objects.
# Example
![[AI-R-FCN-Example.png]]
1. For the **whole** input image, compute feature scores of each position ($k^{2}$ in total, here $k = 3$) of each class ($C+1$ in total). 
2. Generate RoIs via a RPN
3. Divide the RoI into $k^{2}$ regions, compute the scores for each region
4. If the final vote is high, then this RoI is likely to be the region for the specific class
# Architecture
![[AI-R-FCN-Arch.png]]
![[AI-R-FCN-Arch-1.png]]
## Overview
Adopt the popular two-stage object detection strategy that consists of
1. Region proposal via [[Faster R-CNN#Region Proposal Network (RPN)|RPN]]
2. Region classification via R-FCN

Given the proposal regions (RoIs), the R-FCN architecture is designed to **classify the RoIs into object categories and background**. In R-FCN, all learnable weight layers are convolutional and are computed on the entire image. The last convolutional layer produces a bank of $k^{2}$ position-sensitive score maps for each category, and thus has a $k^{2}(C+1)$-channel output layer with $C$ object categories ($+1$ for background). 

The bank of $k^{2}$ score maps correspond to a $k \times k$ spatial grid describing relative positions. For example, with $k \times k = 3 \times 3$, the $9$ score maps encode the cases of $\left\{ \text{top-left}, \text{top-center},\text{top-right}, \ldots ,\text{bottom-right} \right\}$ of an object category.

R-FCN ends with a position-sensitive RoI pooling layer. This layer aggregates the outputs of the last convolutional layer and generates scores for each RoI. The layer conducts **selective** pooling, and each of the $k \times k$ bin aggregates responses from only one score map out of the bank of $k \times k$ score map
