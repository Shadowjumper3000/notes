# Object Detection

Object detection is a computer vision task that involves both identifying the class of an object (classification) and determining its precise spatial location in an image (localization), typically using axis-aligned bounding boxes. It is one of the most widely studied problems in vision and serves as a foundation for applications ranging from autonomous driving to medical imaging.

## Problem Definition

Given an input image $I \in \mathbb{R}^{H \times W \times C}$, object detection aims to produce a set of detections $\mathcal{D} = \{d_1, d_2, \dots, d_N\}$, where each detection $d_i = (c_i, b_i)$ consists of:
- A class label $c_i \in \{1, \dots, K\}$ (or a background label indicating no object)
- A bounding box $b_i = (x, y, w, h)$ or $(x_1, y_1, x_2, y_2)$ representing the spatial extent of the object

## Approaches

### Two-Stage Detectors

These methods first generate a sparse set of candidate region proposals, then classify and refine each proposal.

- **R-CNN** (Region-based CNN): Extracts ~2000 region proposals using selective search, warps each to a fixed size, runs a CNN independently on each, and classifies with SVMs. Accurate but extremely slow due to per-proposal forward passes.
- **Fast R-CNN**: Improves R-CNN by processing the entire image through a CNN once, projecting region proposals onto the resulting feature map, and using RoI Pooling to extract fixed-size feature vectors for each proposal. Multi-task loss jointly optimizes classification and bounding-box regression.
- **Faster R-CNN**: Introduces the Region Proposal Network (RPN), a fully convolutional network that shares features with the detection network, enabling nearly cost-free region proposals. The RPN slides a small network over the feature map and outputs objectness scores and box coordinates at each location using anchor boxes of multiple scales and aspect ratios.
- **Mask R-CNN**: Extends Faster R-CNN with a parallel mask prediction branch for [[Image Segmentation#Instance Segmentation|instance segmentation]], replacing RoI Pooling with RoI Align to eliminate quantization errors.

### One-Stage Detectors

These methods directly predict class probabilities and bounding box coordinates from the image in a single pass, trading some accuracy for significantly faster inference.

- **YOLO (You Only Look Once)**: Divides the image into an $S \times S$ grid; each cell predicts $B$ bounding boxes, confidence scores, and $C$ class probabilities. Unified, end-to-end architecture enabling real-time detection at 45+ FPS.
- **YOLOv3-v9**: Successive improvements add multi-scale predictions (FPN), residual blocks, anchor-free detection, and backbone architectures like DarkNet and CSPNet.
- **SSD (Single Shot MultiBox Detector)**: Uses a feed-forward CNN to produce a fixed collection of bounding boxes and scores at multiple feature map resolutions, capturing objects at different scales without explicit region proposals.
- **RetinaNet**: Addresses the extreme foreground-background class imbalance inherent in one-stage detectors through Focal Loss:
  $$\text{FL}(p_t) = -\alpha_t (1 - p_t)^\gamma \log(p_t)$$
  where $p_t$ is the model's estimated probability for the ground-truth class, $\gamma \geq 0$ is the focusing parameter, and $\alpha_t$ is a weighting factor. Focal Loss down-weights easy examples, allowing the model to focus on hard, misclassified examples.

### Transformer-Based Detectors

- **DETR (DEtection TRansformer)**: Treats detection as a direct set prediction problem using a Transformer encoder-decoder architecture. A fixed set of learned object queries is decoded into predictions, and bipartite matching (Hungarian algorithm) assigns predictions to ground-truth objects during training, eliminating the need for anchor boxes and NMS post-processing.
- **Deformable DETR**: Addresses DETR's slow convergence by introducing deformable attention modules that attend to a sparse set of key sampling points around a reference, making the architecture more efficient for high-resolution feature maps.

## Mathematical Formulation

### Bounding Box Regression

Faster R-CNN performs bounding-box regression by predicting offsets relative to anchor boxes. Given an anchor box $A = (A_x, A_y, A_w, A_h)$ and a ground-truth box $G = (G_x, G_y, G_w, G_h)$, the target offsets are:

$$t_x = \frac{G_x - A_x}{A_w}, \quad t_y = \frac{G_y - A_y}{A_h}$$
$$t_w = \log\frac{G_w}{A_w}, \quad t_h = \log\frac{G_h}{A_h}$$

The smooth L1 loss is used for regression:

$$\mathcal{L}_{\text{reg}} = \sum_{i \in \{x,y,w,h\}} \text{smooth}_{L_1}(t_i - \hat{t}_i)$$

$$\text{smooth}_{L_1}(x) = \begin{cases} 0.5 x^2 & \text{if } |x| < 1 \\ |x| - 0.5 & \text{otherwise} \end{cases}$$

### Multi-Task Loss (Faster R-CNN)

The total loss for each RoI combines classification and regression:

$$\mathcal{L} = \mathcal{L}_{\text{cls}} + \lambda \mathcal{L}_{\text{reg}}$$

where $\mathcal{L}_{\text{cls}}$ is the log loss over $K+1$ classes (including background) and $\lambda$ controls the balance between the two terms.

### Non-Maximum Suppression (NMS)

Post-processing step that removes duplicate detections by iteratively selecting the highest-confidence detection and suppressing others with IoU above a threshold $\tau$ (typically 0.5):

$$\text{IoU}(b_i, b_j) = \frac{|b_i \cap b_j|}{|b_i \cup b_j|}$$

## Evaluation Metrics

- **Precision and Recall**: Precision = TP / (TP + FP), Recall = TP / (TP + FN)
- **Average Precision (AP)**: Area under the precision-recall curve interpolated at 11 (or 101) recall points. Often reported at IoU thresholds of 0.5 (AP$_{50}$) and 0.75 (AP$_{75}$).
- **Mean Average Precision (mAP)**: AP averaged over all classes, the standard metric on datasets like COCO and PASCAL VOC.
- **FPS (Frames Per Second)**: Inference speed, critical for real-time applications like autonomous driving.

## Key Datasets

- **PASCAL VOC 2007/2012**: 20 object classes, ~11k images. Historically the benchmark that drove early progress.
- **MS COCO**: 80 object classes, 330k images, 1.5M instances. Introduces evaluation across multiple IoU thresholds and small/medium/large object subsets.
- **ImageNet Detection**: 200 object classes, ~470k images.
- **Open Images**: ~9M images with 600+ classes, including visual relationships.

## Key Papers

- Girshick et al., "Rich Feature Hierarchies for Accurate Object Detection and Semantic Segmentation" (R-CNN, 2014) — CVPR
- Girshick, "Fast R-CNN" (2015) — ICCV
- Ren et al., "Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks" (2015) — NeurIPS
- Redmon et al., "You Only Look Once: Unified, Real-Time Object Detection" (YOLO, 2016) — CVPR
- Liu et al., "SSD: Single Shot MultiBox Detector" (2016) — ECCV
- Lin et al., "Focal Loss for Dense Object Detection" (RetinaNet, 2017) — ICCV
- Carion et al., "End-to-End Object Detection with Transformers" (DETR, 2020) — ECCV
- Zhu et al., "Deformable DETR: Deformable Transformers for End-to-End Object Detection" (2021) — ICLR

## Related Topics

- [[Image Segmentation]]
- [[Vision Transformers (ViT)]]
- [[Image Classification]]
- [[Convolutional Neural Networks]]
- [[Multi-Task Learning]]
- [[Attention Mechanisms]]

## Trade-offs

- **Two-Stage vs. One-Stage**: Two-stage detectors (Faster R-CNN) achieve higher accuracy on small objects and at higher IoU thresholds, while one-stage detectors (YOLO, SSD) offer superior speed with slightly lower accuracy. RetinaNet's Focal Loss largely closes this gap.
- **Anchor-Based vs. Anchor-Free**: Anchor-based methods require careful tuning of anchor sizes, scales, and aspect ratios for each dataset. Anchor-free methods (CenterNet, FCOS) simplify the pipeline and reduce hyperparameters but may struggle with overlapping objects.
- **Speed vs. Accuracy**: Real-time detectors (YOLOv8-tiny, MobileNet-SSD) achieve 30-100+ FPS on edge devices, while large models (DETR with ResNeXt, Mask R-CNN with FPN) require high-end GPUs for acceptable latency.
