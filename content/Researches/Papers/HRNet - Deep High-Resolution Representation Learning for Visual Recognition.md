---
zotero-key: 4MK8A9C7
zt-attachments:
  - "475"
title: Deep High-Resolution Representation Learning for Visual Recognition
authors:
  - Jingdong Wang
  - Ke Sun
  - Tianheng Cheng
  - Borui Jiang
  - Chaorui Deng
  - Yang Zhao
  - Dong Liu
  - Yadong Mu
  - Mingkui Tan
  - Xinggang Wang
  - Wenyu Liu
  - Bin Xiao
collections:
  - Vision Backbone > Computer Vision > Artificial Intelligence
publish-date: 2021
url: https://ieeexplore.ieee.org/document/9052469
DOI: 10.1109/TPAMI.2020.2983686
---
# Motivation
- Previous works first encode the input image as a low-resolution representation and then recover the high-resolution representation from the encoded low-resolution representation. This process loses quite a lot of information even when skip connections like in [[U-Net]], [[RefineNet]] are added
![[AI-HRNet-Previous-Arch.png]]
- Instead, the author presents a novel architecture, namely *High-Resolution (HRNet)*, which is able to **maintain high-resolution representation through the whole process**
![[AI-HRNet-Arch.png]]
- Start form a high-resolution convolution steam, gradually add high-to-low resolution convolution streams one by one, and add connect the multi-resolution streams in parallel. The resulting network consists of several stages, and the $n$-th stage contains $n$ streams corresponding to $n$ resolutions
# Method
## Parallel Muti-Resolution Convolution
The resolutions for the parallel streams of a later stage **consist of the resolutions from the previous stage, and an extra lower one**
## Repeated Multi-Resolution Fusion
Between each stage, there is a muti-resolution layer that fuse the features maps from each input resolution to each output resolution 

This is just like a **fully connected convolutional layer**, where the connections are up/down sampling convolution between different resolutions, the each output is the **sum** of the corresponding convolution results
$$
\textbf{R}_j^\text{out} = \sum_{i = 1}^{j -1} f_{ij}(\textbf{R}_i^\text{in})
$$
![[AI-HRNet-Feature-Fusing.png]]

## Final output
![[AI-HRNet-Versions.png]]
- (a) HRNetV1: only output the representation from the high-resolution convolution stream.
- (b) HRNetV2: concatenate the (upsampled) representations that are from all the resolutions
- (c) HRNetV2p: get multi-resolution output via downsampling the result of HRNet V2