---
zotero-key: 9PT7NYUC
zt-attachments:
  - "166"
title: "U-Net: Convolutional Networks for Biomedical Image Segmentation"
authors:
  - Olaf Ronneberger
  - Philipp Fischer
  - Thomas Brox
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2015
url: http://arxiv.org/abs/1505.04597
DOI: 10.48550/arXiv.1505.04597
---
# Idea
The U-Net architecture consist of two main paths: the **contracting path** (encoder) and the **expansive path** (decoder), forming a U-shaped structure
-  **Contracting Path**: This part captures context through a series of convolutional layers (3x3 convolutions) followed by [[Rectified Linear Unit (ReLU)|ReLU]] activation and max pooling operations. Each downsampling step doubles the number of feature channels, allowing the network to learn increasingly abstract features while reducing spatial dimensions.
- **Expansive Path**: This path is responsible for upsampling the feature maps to the original image size. It includes up-convolutions (2x2 convolutions) that halve the number of feature channels, followed by **concatenation with the corresponding feature maps from the contracting path** (called *skip connections*). This concatenation helps retain localization information lost during downsampling, enabling precise segmentation.
![[AI-U-Net-Arch.png]]
The model is designed for biomedical image segmentation where the training data is fewer and expansive. Therefore, the U-Net architecture employs the symmetric skip connections to produce high-quality segmentation results even with limited training data. 

In addition, the robustness of U-Net has let it be applied to general image segmentation tasks, and the performances are also fantastic.