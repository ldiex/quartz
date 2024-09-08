---
zotero-key: 6RI7LFDS
zt-attachments:
  - "380"
title: Segment Anything
authors:
  - Alexander Kirillov
  - Eric Mintun
  - Nikhila Ravi
  - Hanzi Mao
  - Chloe Rolland
  - Laura Gustafson
  - Tete Xiao
  - Spencer Whitehead
  - Alexander C. Berg
  - Wan-Yen Lo
  - Piotr Dollár
  - Ross Girshick
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2023
url: http://arxiv.org/abs/2304.02643
DOI: 10.48550/arXiv.2304.02643
---
# Idea
## Goal
Build a foundation model for image segmentation: develop a prompt-able model and pre-train it on a board dataset using a task that enables powerful generalization
## Three key components
1. What **task** will enable zero-shot generalization
2. What is the corresponding **model** architecture
3. What **data** can power this task and model
![[AI-Segment-Anything-Task-Model-Data.png]]
# Task
## Task Types
- A set of foreground / background points
- A rough box or mask
- Free-from text
The *prompt-able segmentation task* is to return a valid segmentation mask given any prompt. The requirement of a *valid* mask simply means that even when a prompt is ambiguous and could refer to multiple objects, the output should be a reasonable mask for at least **one** of those objects.
## Pre-training
The prompt-able segmentation task suggests a natural pre-training algorithm that simulates a sequence of prompts (e.g. points, boxes or masks) for each training sample and compares the model's mask predictions against the ground truth.
## Zero-shot Transfer
Intuitively, the pre-training task endows the model with the ability to respond appropriately to any prompt at inference time, and thus **downstream tasks can be solved by engineering appropriate prompts**

For example, if one has a bounding box detector for cats, cat instance segmentation can be solved by providing the detector's box output as a prompt to this model.
# Model
![[AI-Segment-Anything-Arch.png]]
## Image Encoder
Apply an [[MAE - Masked Autoencoder|MAE]] pre-trained [[Vision Transformer (ViT)]] minimally adapted to process high resolution inputs
## Prompt Encoder
Represent points and boxes by positional encodings summed with learned embedding for each prompt type and free-form text with an off-the-shelf encoder from [[CLIP - Learning Transferable Visual Models From Natural Language Supervision|CLIP]]
## Mask Decoder
Employs modification of a Transformer decoder block followed by a dynamic mask prediction head. The modified decoder block uses prompt self-attention and cross-attention in two directions (prompt-to-image embedding and vice-versa) to update **all** embeddings.

# Data
As segmentation masks are not abundant on the internet, the authors built a **data engine** to enable the collection of their 1.1B mask dataset, SA-1B. The data engine has three stages
1. A model-assisted manual annotation stage
2. A semi-automatic stage with a mix of automatically predicted masks and model-assisted annotation
3. A fully automatic stage in which the model generates masks without annotator input

# Code Implementation
## Prompt Encoder Module
### Input
The `forward` method takes in three kinds of prompts: 
- `points: tuple(Tensor, Tensor)` where the two tensors represents point coordinates and labels to embed. And the label can be
	- `0` if the point belongs to the object you want to segment
	- `1` if you want to exclude the point from the object
- `boxes: Tensor` 
- `masks: Tensor`.
### Embed Points
1. Apply `points += 0.5` to shift the points to center of pixel
2. If the input `boxes` is `None`, for each minibatch, pad $1$ point `(0, 0)` and $1$ label `-1` at the end of the batch
3. Normalize the `points` to `[0, 1]` relative to the whole image size and then add positional encoding, return shape $B \times N_p \times\text{Embed\_dim}$
4. Add additional point embedding according to the labels, and finally returns the `points`
### Embed Boxes
1. Apply `boxes += 0.5` to shift the points to center of pixel
2. Reshape to $B \times 2 \times 2$, and the do the normalization and add positional encoding, return shape $B \times 2N_b \times\text{Embed\_dim}$
3. Add corner embeddings to distinguish the left-up corner point and the right-down corner point
### Embed Masks
1. Apply convolutional layers to downscale the masks to the target shape
2. If no input masks are given, use `no_masks_embedding` instead
### Output
Two kinds of embeddings as the output: 
- `sparse_embeddings: Tensor` for the points and boxes with shape $B \times N\ \times\text{Embed\_dim}$, where $N = N_p + 2N_b$ if $N_b \neq 0$, otherwise $N= N_p + 1$
- `dense_embeddings: Tensor` for the masks with shape $B \times\text{Embed\_dim} \times\text{Embed\_H} \times\text{Embed\_W}$, where $(\text{Embed\_H},\text{Embed\_W})$ is the spatial size of the image embedding.
