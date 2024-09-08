*Non-Maximum Suppression (NMS)* is a crucial technique in [[Computer Vision|computer vision]], particularly in object detection, used to **filter out redundant bounding boxes that overlap significantly**. It helps in selecting the most relevant bounding box for each detected object, thereby improving the accuracy of object detection systems.

# Method
1. **Bounding Box Generation**: Object detection algorithms, like [[YOLO v1 - You Only Look Once|YOLO]] or [[SSD - Single Shot MultiBox Detector|SSD]], produce numerous bounding boxes around detected objects, each associated with a confidence score indicating the likelihood of containing an object.
2. **Sorting**: The bounding boxes are sorted based on their confidence scores in descending order.
3. **Selection Process**:
    - The bounding box with the highest score is selected and added to the final output list.
    - The *Intersection over Union (IoU)* is calculated between this selected box and all other boxes.
    - Any box that has an IoU greater than a defined threshold (commonly set at $0.5$) is removed from consideration.
4. **Iteration**: This process repeats: the next highest scoring bounding box is selected, and the IoU calculations are performed again until no boxes remain.

# IoU
*Intersection over Union (IoU)* is defined as the area of overlap between the predicted bounding box and the ground truth bounding box divided by the area of their union. Mathematically, it is expressed as:
$$
\mathrm{IoU}=\frac{\text{Area of Overlap}}{\text{Area of Union}}
$$
This metric ranges from $0$ to $1$, where $0$ indicates no overlap and $1$ indicates perfect overlap.

And the basic **IoU loss** can be expressed as:
$$
\mathcal{L}_\text{IoU} = 1- \mathrm{IoU}
$$
