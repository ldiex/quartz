# Idea
*Layer normalization* is a technique used in machine learning to normalize the inputs across features **for each sample** in a layer independently, regardless of batch size.

# [[Batch Normalization]] vs Layer Normalization
**Batch Normalization**:
- Normalizes inputs across the batch dimension ($N$) for each feature
- Computes mean and variance across the batch for each feature channel independently
- Works well with fully connected layers and [[Convolutional Neural Networks (CNNs)|CNNs]]
- Performance can depend on batch size, which can be problematic for small batches or recurrent models

**Layer Normalization**:
- Normalizes inputs across the feature dimension ($C$) for each sample individually
- Computes mean and variance across all features for each individual sample
- Works better with [[Recurrent Neural Networks (RNNs)|RNNs]]
- Does not depend on batch size, making it more suitable for scenarios with variable batch sizes

![[AI-Batch-vs-layer-norm.png]]
In the diagram, $C$ stands for channels/features, $N$ stands for batches and $H,W$ stand for the height and weight of the feature map

For detail algorithm implement, refer to [[Batch Normalization]]
