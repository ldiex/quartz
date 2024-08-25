---
zotero-key: 7N9KVBYG
zt-attachments:
  - "87"
title: "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale"
authors:
  - Alexey Dosovitskiy
  - Lucas Beyer
  - Alexander Kolesnikov
  - Dirk Weissenborn
  - Xiaohua Zhai
  - Thomas Unterthiner
  - Mostafa Dehghani
  - Matthias Minderer
  - Georg Heigold
  - Sylvain Gelly
  - Jakob Uszkoreit
  - Neil Houlsby
collections:
  - Vision Backbone > Computer Vision > Artificial Intelligence
publish-date: 2021
url: http://arxiv.org/abs/2010.11929
DOI: 10.48550/arXiv.2010.11929
---

# Idea
- Apply [[Transformer - Attention Is All You Need|transformer]] (the same architecture as in NLP) to vision tasks, which paves the road for multi-modal models
- Completely abandon [[Convolutional Neural Networks (CNNs)|CNNs]], which may need more data to achieve the same performance as convolutional neural networks since the transformer has no *inductive bias*, which refers to the inherent assumptions or preferences that guide the model's learning process, **such as locality and translation equivariance presented in CNNs**
# Model
![[AI-Vision-Transformer.png]]
- Slice the original image into $16 \times 16$ pixel *patches*
- Convert these patches to embeddings (each patch has a vector embedding, similar as word2vec) through a linear layer
- Add positional embeddings
- Append a special token to the front of the embedding sequence. This can be a `[CLS]` token (see [[BERT - Bidirectional Encoder Representation from Transformers#Steps]]), whose corresponding output vector representation in the latent space after the final layer can hold the information of the whole sequence (image)  