---
zotero-key: PR8HPBPT
zt-attachments:
  - "133"
title: A ConvNet for the 2020s
authors:
  - Zhuang Liu
  - Hanzi Mao
  - Chao-Yuan Wu
  - Christoph Feichtenhofer
  - Trevor Darrell
  - Saining Xie
collections:
  - Vision Backbone > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2201.03545
DOI: 10.48550/arXiv.2201.03545
---
# Idea
If we modify traditional [[Convolutional Neural Networks (CNNs)|CNNs]] according to modern [[Transformer - Attention Is All You Need|Transformer]] architecture, they may perform better. The conclusion is that, in terms of Computer Vision, we cannot say Transforms is just better than CNNs.
# Improvement
## Architecture
### Stage Ratio
Adjust block size referring to [[AI-Swin-Transformer-Arch.png|Swin Transformer]], which is $2:2:6:2 = 1:1:3:1$. Therefore, improve the block size of each stage in ResNet-50 to $3:3:9:3$
![[AI-ConvNeXT-Block.png]]
### Patchify Stem
Use a stem layer to do the similar work as the patching layer in [[Vision Transformer (ViT)|vison Transformers]] does.
```python
stem = nn.Sequential(
    nn.Conv2d(in_chans, dims[0], kernel_size=4, stride=4),
    LayerNorm(dims[0], eps=1e-6, data_format="channels_first")
)
```
### Group Convolution
Divides the input channels into distinct groups, each of which is convolved with its own set of filters. This approach allows for a reduction in the number of parameters and computational complexity.
### Inverted Bottleneck
Unlike the traditional bottleneck layer, the inverted bottleneck has a hidden dimension of the MLP block is four times wider than the input dimension (Like the feed forward layer in [[Transformer - Attention Is All You Need|Transformer]] architecture, which may retain more information.

### Larger Kernel Size
In vision transformers, the self-attention enables each layer to have a global receptive field. Large kernel size could achieve this, too. In experiment, $7 \times 7$ kernel size performs the best
![[AI-ConvNeXT-inverted-bottleneck.png]]
The figure above: (a) is a ResNeXt block; in (b) we create an inverted bottleneck block and in (c) the position of the spatial depth-wise conv layer is moved up (since in Transformers the MSA block is placed prior to the MLP layers)
## Some detail optimization
- Switch to GeLU from [[Rectified Linear Unit (ReLU)|ReLU]]
- Use less [[Activation Functions|activation functions]] (as in [[Transformer - Attention Is All You Need|Transformers]])
- Less normalization layer and use [[Layer Normalization]] instead of [[Batch Normalization]]