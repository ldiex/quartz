---
zotero-key: AWZEEY7N
zt-attachments:
  - "366"
title: Per-Pixel Classification is Not All You Need for Semantic Segmentation
authors:
  - Bowen Cheng
  - Alexander G. Schwing
  - Alexander Kirillov
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2021
url: http://arxiv.org/abs/2107.06278
DOI: 10.48550/arXiv.2107.06278
---
# Idea
![[AI-MaskFormer-Per-Mask-Classification.png]]
Instead for pre-pixel classification, we could first predict a set of binary masks and then assign a single class to each mask. 

Each prediction is supervised with a per-pixel binary mask loss and a classification loss

# Architecture
![[AI-MaskFormer-Arch.png]]
1. Using a backbone to extract images features $\mathcal F$
2. Upsample the features to obtain per-pixel embeddings $\mathcal E_{\mathrm{pixel}}$
3. A [[Vision Transformer (ViT)|transformer]] decoder attends to image features and produces $N$ per-segment embeddings $\mathcal Q$, then embeddings then independently generate
	- $N$ class predictions (shape $N \times (K + 1)$), where $\emptyset$ is introduced to represent "no-object" class
	- $N$ corresponding mask embeddings $\mathcal E_{\mathrm{mask}}$
4. Predict $N$ possibly overlapping binary mask predictions via a dot product between pixel embeddings $\mathcal E_{\mathrm{pixel}}$ and mask embeddings $\mathcal E_{\mathrm{mask}}$ followed by a sigmoid activation.
5. Finally we can get the prediction by combining $N$ binary masks with their class predictions using a simple matrix multiplication.

