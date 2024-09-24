---
zotero-key: JHDQM5HC
zt-attachments:
  - "421"
title: Focal Loss for Dense Object Detection
authors:
  - Tsung-Yi Lin
  - Priya Goyal
  - Ross Girshick
  - Kaiming He
  - Piotr Dollár
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2018
url: http://arxiv.org/abs/1708.02002
DOI: 10.48550/arXiv.1708.02002
---
# Motivation
- [[OHEM - Training Region-based Object Detectors with Online Hard Example Mining#Imbalance of foreground objects and background objects|The imbalance of foreground objects and background objects]] is a key problem in detection model training
- [[OHEM - Training Region-based Object Detectors with Online Hard Example Mining|OHEM]] automatically select hard examples to solve this issue
- This paper proposes the *Focal Loss* to down-weight the loss assigned to well-classified examples, which is a dynamically scaled cross-entropy loss
# Method
## Binary CE Loss
Starting from the [[Cross Entropy Loss|cross-entropy (CE) loss]] for binary classification
$$
\mathrm{CE}(p,y) = \begin{cases}
-\log p, & y = 1  \\
- \log (1- p), & \text{otherwise}
\end{cases}
$$
In the above $y\in \left\{ \pm 1 \right\}$ specifies the ground-truth class and $p\in[0,1]$ is the model's estimated probability for the class with label $y = 1$. For notation convenience, we define $p_t$ as
$$
p_t = \begin{cases}
p & \text{if } y = 1 \\
1 - p & \text{otherwise}
\end{cases}
$$
and rewrite $\mathrm{CE}(p,y) = -\log (p_t)$
## Balanced Cross Entropy
A common method for addressing class imbalance is to introduce a weighting factor $\alpha\in[0,1]$ for class $1$ and $1-\alpha$ for class $1$. In practice $\alpha$ may be set by inverse class frequency or treated as a hyper-parameter to set by cross validation. For notation convenience, we define $\alpha_t$ analogously to how we defined $p_t$. We write the $\alpha$-balanced CE loss as:
$$
\mathrm{CE}(p_t) = -\alpha_t \log (p_t)
$$
## Focal Loss
**While $\alpha$ balances the importance of positive/negative examples, it does not differentiate between easy/hard examples.**
![[AI-Focal-Loss-Diagram.png]]
Therefore, we propose to add a modulating factor $(1-p_t)^\gamma$ to the cross entropy loss with tunable *focusing* parameter $\gamma\geq0$. We define the focal loss as
$$
\mathrm{FL}(p_t) = -(1-p_t)^\gamma \log(p_t)
$$
## Properties of Focal Loss
- When an example is misclassified and $p_t$ is small, the modulating factor is near $1$ and the loss is unaffected. As $p_t \to1$, the factor goes to $0$ and the loss for well-classified examples is down-weighted.
- The focusing parameter $\gamma$ smoothly adjusts the rate at which easy examples are down-weighted. When $\gamma = 0$, FL is equivalent to CE, and as $\gamma$ is increased the effect of the modulating factor is likewise increased.
# RetinaNet
![[AI-RetinaNet-Arch.png]]
Combine [[FPN - Feature Pyramid Networks for Object Detection|FPN]] with Focal Loss
