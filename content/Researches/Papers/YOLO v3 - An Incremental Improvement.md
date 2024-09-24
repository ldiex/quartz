---
zotero-key: CY2JZSCH
zt-attachments:
  - "430"
title: "YOLOv3: An Incremental Improvement"
authors:
  - Joseph Redmon
  - Ali Farhadi
collections:
  - Object Detection > Computer Vision > Artificial Intelligence
publish-date: 2018
url: http://arxiv.org/abs/1804.02767
DOI: 10.48550/arXiv.1804.02767
---
# Motivation
- Improvement of [[YOLO v1 - You Only Look Once|YOLO v1]] and [[YOLO v2 (YOLO 9000)|YOLO v2]]
# Architecture
![[AI-YOLO-v3-Arch.webp]]
YOLOv3 makes detections at 3 different places in the network. These are layers 82nd, 94th and 106th layer. 
- Network Input $(416, 416)$
- For $82$nd layer the stride is $32$ and the output size is $13 \times 13$ and it is responsible to **detect large objects**
- For $94$th layer the stride is $16$ and the output size is $26 \times 26$ and it is responsible to **detect medium objects**
- For $106$nd layer the stride is $8$ and the output size is $52 \times 52$ and it is responsible to **detect small objects**

To produce outputs YOLO v3 applies $1 \times 1$ kernels at three output layers in the network. The shape of the kernels has its depth that is calculated by $b \times (5 + c)$, where $b =3$ is the number of bonding boxes, and $c = 80$ is the number of classes for COCO dataset. Therefore, the depth is $3 \times (5 + 80)= 255$, and the shapes of these output feature maps are $(13 \times 13 \times 255), (26 \times 26 \times 255),(52 \times 52\times 255)$
# Box Generation
[[Faster R-CNN#Anchor Boxes|Anchor Boxes]] is used to predict bounding boxes. YOLO v3 uses predefined bounding boxes to calculate real width and real height for predicted bounding boxes.

In total $9$ anchor boxes are used, $3$ anchor boxes for each scale. This means at each output layer every grid scale of feature map can predict $3$ bounding boxes using $3$ anchor boxes.

To calculate these anchor, YOLO v3 uses $k$-means clustering as in [[YOLO v2 (YOLO 9000)|YOLO v2]]

![[AI-YOLO-v3-Box-Offset.png]]
- To predict center coordinates of bounding boxes $(b_x,b_y)$, YOLO v3 passes outputs $(t_x,t_y)$ through [[Sigmoid Function|sigmoid function]]
- Then based on the above equations given in figure we get center coordinates and width and height of the bounding boxes.
- All the redundant bounding boxes are suppressed using [[Non-maximum Suppression]]
