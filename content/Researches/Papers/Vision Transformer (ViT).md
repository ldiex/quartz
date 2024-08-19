---
type: paper
title: "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale"
tags:
  - AI
  - Attention-Mechanism
  - Computer-Vision
author: Dosovitskiy Alexey
year: "2021"
link: http://arxiv.org/abs/2010.11929
---

# Idea
- Apply [[Transformer - Attention Is All You Need|transformer]] (the same architecture as in NLP) to vision tasks, which paves the road for multi-modal models
- Completely abandon [[Convolutional Neural Networks (CNNs)|CNNs]], which may need more data to achieve the same performance as convolutional neural networks since the transformer has no *inductive bias*, which refers to the inherent assumptions or preferences that guide the model's learning process, **such as locality and translation equivariance presented in CNNs**
# Model
![[AI-Vision-Transformer.png]]
- Slice the original image into $16 \times 16$ pixel *patches*
- Convert these patches to embeddings (each patch has a vector embedding, similar as word2vec) through a linear layer
- Add positional embeddings
- Append a special token to the front of the embedding sequence. This can be a `[CLS]` token (see [[BERT#Steps]]), whose corresponding output vector representation in the latent space after the final layer can hold the information of the whole sequence (image)  