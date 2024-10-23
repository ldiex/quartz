---
zotero-key: 7ZMQDE8M
zt-attachments:
  - "677"
title: Photorealistic Text-to-Image Diffusion Models with Deep Language Understanding
authors:
  - Chitwan Saharia
  - William Chan
  - Saurabh Saxena
  - Lala Li
  - Jay Whang
  - Emily Denton
  - Seyed Kamyar Seyed Ghasemipour
  - Burcu Karagol Ayan
  - S. Sara Mahdavi
  - Rapha Gontijo Lopes
  - Tim Salimans
  - Jonathan Ho
  - David J. Fleet
  - Mohammad Norouzi
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2205.11487
DOI: 10.48550/arXiv.2205.11487
---
![[AI-Imagen.svg]]
# Large Guidance Weight Samplers
In [[Classifier-Free Diffusion Guidance|Classifier-Free Guidance]], increasing the classifier-free guidance weight improves image-text alignment, but **damages image fidelity producing highly saturated and unnatural images**. This is due to a train-test mismatch arising from high guidance weights. 

At each sampling step $t$, the $\boldsymbol x$-prediction $\boldsymbol{\hat{x}}_t$ must be within the same bounds as training data $\boldsymbol x$, i.e. within $[-1,1]$, but empirically that high guidance weights cause $\boldsymbol x$-predictions to exceed these bounds.
## Static Thresholding
Elementwise clipping the $\boldsymbol x$-prediction to $[-1,1]$
## Dynamic thresholding
At each sampling step set $s$ to a certain percentile absolute value in $\boldsymbol {\hat{x}}_t$, and if $s > 1$, then threshold $\boldsymbol{\hat{x}}_t$ to the range $[-s,s]$ and then divide by $s$.

# Robust Cascaded Diffusion Models
Imagen starts with a **64x64 image** generated by a base model, two **super-resolution diffusion models** are then used to progressively upscale this image:
- **First step**: Upsampling the 64x64 image to **256x256**.
- **Second step**: Further upsampling the 256x256 image to **1024x1024**.

These super-resolution models take the low-resolution image and use **text-conditional inputs** to generate higher resolutions while preserving quality and coherence with the text description.
## Noise Conditioning Augmentation
A key aspect that enhances the performance of super-resolution models is **noise conditioning augmentation**.
- The **noise level** added to the image is tracked and fed into the super-resolution models as part of the conditioning.
- This helps the models handle any artifacts or imperfections introduced in the earlier lower-resolution stages.
## Augmentation with Gaussian Noise
Imagen applies Gaussian noise to the low-resolution images (like $64\times64$) to **corrupt** them during training, simulating the noisy images that the model will denoise in real-world scenarios.

The noise is controlled using a parameter called `aug_level`, which specifies the strength of the noise added.
- `aug_level` $∈ [0, 1]$: It defines how much corruption (or noise) is applied to the image.
- In training, the value of `aug_level` is chosen **randomly**, which helps the model generalize across different noise conditions.
- During inference, different levels of `aug_level` are tested to determine which produces the best image quality.