---
zotero-key: 8IF8VSZ2
zt-attachments:
  - "233"
title: "PointRend: Image Segmentation as Rendering"
authors:
  - Alexander Kirillov
  - Yuxin Wu
  - Kaiming He
  - Ross Girshick
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2020
url: http://arxiv.org/abs/1912.08193
DOI: 10.48550/arXiv.1912.08193
---
# Idea
View image segmentation as rendering problem and to adapt classical idea from computer graphics to efficiently "render" high-quality label maps, that is, for each "rendering" iteration **focus on the most ambiguous points to recover detail** on the finer gird.
![[AI-PointRend-Adaptive-Subdivison-Step.png]]
# Method
1. A point selection strategy chooses a small number of real-value points to make predictions on (**these points should be located more densely near high-frequency areas**), avoiding excessive computation for all pixels in the high-resolution output grid. 
2. In each iteration, PointRend upsamples its previously predicted segmentation using bilinear interpolation and then selects the $N$ most uncertain points (e.g., those with probabilities closest to $0.5$ for a binary mask) on this denser grid. PointRend then computes the point-wise feature representation for each of these $N$ points and predicts their labels. This process is repeated until the segmentation is upsampled to a desired resolution.
![[AI-PointRend-Point-Sampling.png]]
# Architecture
![[AI-PointRend-Arch.png]]
Select key points to refine the coarse prediction to better predict the  details