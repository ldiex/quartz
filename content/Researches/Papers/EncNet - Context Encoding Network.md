---
zotero-key: 8LWL4BDY
zt-attachments:
  - "210"
title: Context Encoding for Semantic Segmentation
authors:
  - Hang Zhang
  - Kristin Dana
  - Jianping Shi
  - Zhongyue Zhang
  - Xiaogang Wang
  - Ambrish Tyagi
  - Amit Agrawal
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2018
url: http://arxiv.org/abs/1803.08904
DOI: 10.48550/arXiv.1803.08904
---
# Idea
Improve the semantic segmentation results by effectively utilizing global context, which captures the semantic context of scenes and selectively enhances class-dependent feature maps.
![[AI-EncNet-Arch.png]]
# Context Encoding Module
## Encoding Layer
### Input
Considering the input feature map with the shape of $C \times H \times W$ as a set of $C$-dimensional input features $X = \left\{ x_1, \ldots ,x_N \right\}$, where $N = H \times W$
### Codebook
The Encoding Layer learns a codebook $D$ containing $K$ codewords (or visual centers)
$$
D = \left\{ d_1,d_2, \ldots ,d_K \right\} 
$$
Each $d_k$ represents a distinct visual center in the feature space that captures a specific semantic meaning or category in the input data
### Smoothing Factor
Alongside the codebook, the layer also learns a set of smoothing factors
$$
S = \left\{ s_1,s_2, \ldots ,s_K \right\}  
$$
Each $s_k$ corresponds to a smoothing factor for the visual center $d_k$. These factors are used to control the influence of each visual center on the feature representation
### Output
The layer outputs the residual encoder by aggregating the residuals with soft-assignment weights $e_k = \sum_{i = 1}^N e_{ik}$, where
$$
e_{ik} = \dfrac{\exp (-s_k \Vert r_{ik} \Vert^{2} )}{\sum_{j = 1}^K \exp(-s_j \Vert r_{ij} \Vert^{2} )} r_{ik}
$$
and the residuals are given by $r_{ik} = x_i - d_k$. The final output is $e = \sum_{k = 1}^K \phi(e_k)$, where $\phi$ denotes [[Batch Normalization]] with [[Rectified Linear Unit (ReLU)|ReLU]] activation. ($e$ is a $C$-dimensional vector)
## Feature Map Attention
Use a fully connected layer to predict feature map scaling factors $\gamma = \delta(We)$, where $W$ denotes the layer weights and $\delta$ is the [[Sigmoid Function|sigmoid]] function. Then the module output is given by $Y = X \otimes \gamma$.