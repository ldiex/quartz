# Single-shot Models
- [[SSD - Single Shot MultiBox Detector]]
- [[YOLO v1 - You Only Look Once]]
## YOLO vs SSD

| Feature       | YOLO                                           | SSD                                             |
| ------------- | ---------------------------------------------- | ----------------------------------------------- |
| Speed         | Up to 155 FPS                                  | 22-46 FPS                                       |
| Accuracy      | Generally lower, struggles with small objects  | Higher, better with varying object sizes        |
| Architecture  | Fully connected layers, grid-based predictions | Convolutional layers, anchor boxes              |
| Best Use Case | Real-time applications                         | Applications needing accuracy and speed balance |
## Development of YOLO
- [[YOLO v2 (YOLO 9000)]] adds [[Batch Normalization]], and starts to predict the anchor boxes via $k$-means clusters; Huge dataset with $9000$ object categories
- [[YOLO v3 - An Incremental Improvement]] makes detections at three different scales in the network, using a new backbone network called Darknet-53 with 53 convolutional layers
# Two-stage Models
## Traditional R-CNNs
- [[R-CNN - Rich feature hierarchies for accurate object detection and semantic segmentation|R-CNN]] first use selective search to find possible bounding boxes and converts detection task into classification task
- [[SPP-Net - Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition|SPP]] apply spatial pooling to enable the classification CNNs to accept multiple-size inputs
- [[Fast R-CNN]] boost the classification speed by first convert the whole image into a feature map and then apply selective search directly on these features
- [[Faster R-CNN]] further abandons the selective search to use a [[Faster R-CNN#Region Proposal Network (RPN)|RPN]] to find possible bounding boxes, and propose the [[Faster R-CNN#Anchor Boxes|anchor boxes]] method
- [[Mask R-CNN]] add a small [[FCN - Fully Convolutional Networks for Semantic Segmentation|FCN]] head to [[Faster R-CNN]] to output a segmentation prediction, originally for [[Semantic Segmentation#Semantic vs Instance vs Panoptic|instance segmentation]], but also improves the accuracy for detection task
## Novel CNN-based Architectures
- [[R-FCN - Object Detection via Region-based Fully Convolutional Networks|R-FCN]] divides the class feature into $3 \times 3$ parts and evaluate the scores for the certain part of the certain class on different positions of the **whole** image. Thus this eliminates the need to pass each RoI into a detector network.
- [[FPN - Feature Pyramid Networks for Object Detection|FPN]] proposes an additional top-down path to further enhance the semantic features.
## Tackle the [[OHEM - Training Region-based Object Detectors with Online Hard Example Mining#Imbalance of foreground objects and background objects|imbalance of foreground objects and background objects]]
- [[OHEM - Training Region-based Object Detectors with Online Hard Example Mining|OHEM]] proposes a read-only copy of the RoI network to first do a loss prediction on all RoIs and then select the regions with least accuracy to the RoI network that enables back-propagation.
- [[RetinaNet - Focal Loss for Dense Object Detection|RetinaNet]] invents Focal Loss to down-weight the loss assigned to well-classified examples

# Transformer-based Architectures
[[DETR - End-to-End Object Detection with Transformers|DETR]] considers the detection task as a set prediction problem, invents an end-to-end model based on [[Vision Transformer (ViT)|ViT]] that eliminates the need for [[Non-maximum Suppression]] and human designed [[Faster R-CNN#Anchor Boxes|anchor boxes]]
