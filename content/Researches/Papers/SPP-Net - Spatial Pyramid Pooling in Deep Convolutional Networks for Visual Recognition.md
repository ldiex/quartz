---
zotero-key: GHEXRWCH
zt-attachments:
  - "397"
title: Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition
authors:
  - Kaiming He
  - Xiangyu Zhang
  - Shaoqing Ren
  - Jian Sun
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2014
url: http://arxiv.org/abs/1406.4729
---
# Idea
CNN-bases classification network requires a fixed size input, therefore the proposed regions must first be cropped or warped before fed in to the model\

The author introduces a *spatial pyramid pooling (SPP)* layer to remove fixed-size constraint of the network
# Architecture
![[AI-SPP-Net-Arch.png]]
# Method
Replace the last pooling layer (e.g. $\text{pool}_5$ after the last convolutional layer) with a spatial pyramid pooling layer. As shown in the figure above, in each spatial bin (having sizes proportional to the image size), the layer pools the response of each filter (e.g. max pooling).

The output of the spatial pyramid pooling are $kM$-dimensional vectors with the number of bins denoted as $M$. The fixed-dimensional vectors are the input to the fully-connected layer.

## Simple Implementation
``` python
class SpatialPyramidPooling(nn.Module):
    def __init__(self, output_sizes=[1, 2, 4]):
        super(SpatialPyramidPooling, self).__init__()
        self.output_sizes = output_sizes

    def forward(self, x):
        batch_size, channels, height, width = x.size()
        pooled_outputs = []

        for output_size in self.output_sizes:
            kernel_size = (
	            math.ceil(height / output_size), 
				math.ceil(width / output_size)
			)
            stride = (
	            math.floor(height / output_size),
			    math.floor(width / output_size)
			)
            padding = (
                (kernel_size[0] * output_size - height + 1) // 2,
                (kernel_size[1] * output_size - width + 1) // 2,
            )

            pooled = F.adaptive_max_pool2d(x, output_size)
            pooled_outputs.append(pooled.view(batch_size, -1))

        return torch.cat(pooled_outputs, dim=1)
```
