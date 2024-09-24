---
zotero-key: J9DMQPTY
zt-attachments:
  - "500"
title: End-to-End Object Detection with Transformers
authors:
  - Nicolas Carion
  - Francisco Massa
  - Gabriel Synnaeve
  - Nicolas Usunier
  - Alexander Kirillov
  - Sergey Zagoruyko
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2020
url: http://arxiv.org/abs/2005.12872
DOI: 10.48550/arXiv.2005.12872
---
# Motivation
- The previous object detection models are designed in an **indirect** way to tackle the problem, by defining surrogate regression and classification problems on a large set of [[R-CNN - Rich feature hierarchies for accurate object detection and semantic segmentation#Region Proposals|proposals]], [[Faster R-CNN#Anchor Boxes|anchor]] or windows centers. This includes many hand-designed procedures such as anchor generation and [[Non-maximum Suppression]]
- To simplify these pipelines, the author proposes a **end-to-end** approach to bypass the surrogate tasks.
# General Idea
View the object detection as a direct set prediction problem, that is, directly predicts the final set of boxes without redundant bounding boxes 
# Set Prediction Loss
## Bipartite matching
Let the ground truth set of objects be denoted by $y$, and $\hat{y} = \left\{ \hat{y}_i \right\}_{i = 1}^N$ for the set of $N$ predictions. Assuming $N$ is larger than the number of objects in the image, we consider $y$ also as a set of size $N$ padded with $\emptyset$ (no object). To find a **bipartite matching** between these two sets we search for a [[Permutation|permutation]] of $N$ elements $\sigma\in S_n$ with the lowest cost:
$$
\hat{\sigma} = \underset{\sigma\in S_n}{\arg \min} \sum_{i}^N  \mathcal{L}_\text{match} \left( y_i, \hat{y}_{\sigma(i)} \right) 
$$
where $\mathcal{L}_\text{match}(\cdot , \cdot)$ is a pair-wise **matching cost**

Each element $i$ of the ground truth set can be seen as a $y_i = (c_i, b_i)$ where $c_i$ is the target class label and $b_i\in[0,1]^4$  is a vector that defines ground truth box center coordinates and its height and width relative to the image size. If $\hat{p}_{\sigma(i)}(c_i)$ is the predicted probability of class $c_i$ of the prediction with index $\sigma(i)$, we define
$$
\mathcal{L}_\text{match} (y_i, \hat{y}_{\sigma(i)}) = -\mathbb{1}_{\left\{ c_i \neq \emptyset \right\} } \hat{p}_{\sigma(i)}(c_i) + \mathbb{1}_{\left\{ c_i \neq \emptyset \right\} } \mathcal{L}_\text{box}(b_i,\hat{b}_{\sigma(i)})
$$
where
$$
\mathcal{L}_\text{box} (b_i, \hat{b}_{\sigma(i)}) = \lambda_\text{iou} \mathcal{L}_\text{iou} (b_i,\hat{b}_{\sigma(i)}) + \lambda_\text{L1} \Vert b_i - \hat{b}_{\sigma(i)} \Vert_1
$$
and $\mathcal{L}_\text{iou}$ the [[Non-maximum Suppression#IoU|IoU loss]]
## Hungarian Loss
 In the previous section we find **the permutation $\hat{\sigma}$ that best match the set of prediction and the set of ground truth**, and then we need to compute the loss function:
$$
\mathcal{L}_\text{Hungarian}(y,\hat{y}) = \sum_{i}^N  \mathcal{L}_\text{match} \left( y_i, \hat{y}_{\hat{\sigma}(i)} \right) 
$$
# Method
![[AI-DETR-Arch.png]]
## Backbone
Starting from the initial image $x_\text{img}\in \mathbb{R}^{3 \times H_0\times W_0}$, a conventional [[Convolutional Neural Networks (CNNs)|CNN]] backbone generates a lower-resolution activation map $f\in \mathbb{R}^{C \times H \times W}$. The typical values are $C = 2048, H = \dfrac{H_0}{32}, W = \dfrac{W_0}{32}$
## Transformer Encoder
1. a $1 \times 1$ convolution reduces the channel dimension of the high-label activation map $f$ from $C$ to a smaller dimension $d$, creating a new feature map $z_0\in \mathbb{R}^{d \times H \times W}$
2. Collapse the spatial dimensions of $z_0$ to $d \times HW$ and add positional encodings, and then fed into the transformer
## Transformer Decoder
The input of the decoder is a sequence of learnable positional encodings called **object queries**. This can be seen as something like learned [[Faster R-CNN#Anchor Boxes|anchor boxes]], which give the model some prior knowledge about how to bound the boxes etc. but without human design

## Prediction Feed-forward networks
Takes in the output of the transformer decoder and obtain the $(\hat{c}_i,\hat{b}_i)$ mentioned [[DETR - End-to-End Object Detection with Transformers#Set Prediction Loss|above]]




