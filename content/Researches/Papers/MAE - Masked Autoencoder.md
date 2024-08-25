---
zotero-key: W6PD38LF
zt-attachments:
  - "140"
title: Masked Autoencoders Are Scalable Vision Learners
authors:
  - Kaiming He
  - Xinlei Chen
  - Saining Xie
  - Yanghao Li
  - Piotr Dollár
  - Ross Girshick
collections:
  - Vision Backbone > Computer Vision > Artificial Intelligence
publish-date: 2021
url: http://arxiv.org/abs/2111.06377
DOI: 10.48550/arXiv.2111.06377
---
# Idea
Develop an asymmetric encoder-decoder model, where
- A **large** random subset of image patches is masked out, and the **visible patches** are taken as the input of the encoder
- Masked tokens are introduces **after** the encoder, and the full set of encoded patches and mask tokens is processed by a small decoder that aims to reconstruct the original image in pixels.
- The two steps above is during the pre-training process. After per-training, the decoder is **discarded** and the encoder is applied to uncorrupted images for recognition tasks
![[AI-MAE-Masked-AutoEncoder.png]]
# Questions
- Why mask a large ratio of image patches (such as 75%): 
	- It optimizes accuracy since the task is becoming challenging
	- Reduce memory and time costs during pre-training