---
zotero-key: TMUUVCU2
zt-attachments:
  - "245"
title: "Segmenter: Transformer for Semantic Segmentation"
authors:
  - Robin Strudel
  - Ricardo Garcia
  - Ivan Laptev
  - Cordelia Schmid
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2021
url: http://arxiv.org/abs/2105.05633
DOI: 10.48550/arXiv.2105.05633
---
# Idea
Apply [[Vision Transformer (ViT)]] for semantic segmentation, unlike [[DPT - Vision Transformers for Dense Prediction]], this paper also uses mask [[Transformer - Attention Is All You Need|Transformer]] as the decoder.

The class masks make the decoder focuses on specific foreground areas, and could help in extracting more relevant and localized features for segmentation
# Architecture
![[AI-Segmenter-Arch.png]]
## Encoder
Adopt flattening and linear projection as the embedding method. then added with position embedding. Just like the original vision transformer paper

## Decoder 
The sequence of path encodings $\boldsymbol z_L\in \mathbb{R}^{N \times D}$  is decoded to a segmentation map $\boldsymbol s\in \mathbb{R}^{H \times W \times K}$ where $K$ is the number of classes. 

The decoder learns to map patch-level encodings coming from the encoder to patch-level class scores. Next these patch-level class scores are upsampled by bilinear interpolation to pixel-level scores.
### Linear
A point-wise linear layer is applied to the patch encodings $\boldsymbol z_L\in \mathbb{R}^{N \times D}$ to produce patch-level class logits $\boldsymbol z_\mathrm{lin}\in \mathbb{R}^{N \times K}$. The sequence is then reshaped into a 2D feature map $\boldsymbol s_\mathrm{lin}\in \mathbb{R}^{H \times W \times K}$. A [[Softmax]] is then applied on the class dimension to obtain the final segmentation map
### Mask Transformer
Introduce a set of $K$ learnable class embeddings $\textbf{cls} = \left[ \mathrm{cls}_1, \ldots ,\mathrm{cls}_K \right]\in \mathbb{R}^{K \times D}$. Each class embedding is initialized randomly and assigned to a single semantic class. 

The class embedding $\textbf{cls}$ are processed jointly with patch encoding $\boldsymbol z_L$ by the decoder.

Mask transformer generates $K$ masks by computing the scalar product between L2-normalized patch embeddings $\boldsymbol z'_M\in \mathbb{R}^{N \times D}$ and class embeddings $\boldsymbol c\in \mathbb{R}^{K \times D}$ output by the decoder
$$
\mathrm{Masks}(\boldsymbol z_M', \boldsymbol c) = \boldsymbol z_M'\boldsymbol c^T
$$
These these mask sequences are reshaped into a 2D mask to form $\boldsymbol s_\mathrm{mask}\in \mathbb{R}^{H/P \times W/P \times K}$ and bilinearly upsampled to the original image size to obtain a feature map $\boldsymbol s\in \mathbb{R}^{H \times W \times K}$.
