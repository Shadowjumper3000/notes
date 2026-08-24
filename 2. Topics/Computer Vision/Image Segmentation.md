# Image Segmentation

Image segmentation is the process of partitioning a digital image into multiple distinct regions or sets of pixels, with the goal of simplifying or changing the representation of an image into something more meaningful and easier to analyze. It is a fundamental task in computer vision and serves as a preprocessing step for many higher-level tasks such as [[Object Detection]], scene understanding, and medical image analysis.

## Types of Segmentation

- **Semantic Segmentation**: Assigns a class label to every pixel in the image. All pixels belonging to the same object category (e.g., "car", "road", "person") receive the same label, without distinguishing between individual instances of the same class.
- **Instance Segmentation**: Extends semantic segmentation by differentiating between individual objects of the same class. Each object instance receives a unique identifier, allowing separate counting and analysis of distinct objects.
- **Panoptic Segmentation**: Unifies semantic and instance segmentation by assigning both a semantic label and an instance ID to every pixel. "Stuff" classes (sky, grass, road) receive semantic labels, while "thing" classes (people, cars, animals) receive both a semantic label and a unique instance ID.

## Approaches

### Classical Methods

- **Thresholding**: Separates foreground from background based on pixel intensity values. Global methods like Otsu's thresholding automatically determine an optimal threshold by minimizing intra-class variance.
- **Edge-Based Segmentation**: Detects discontinuities in intensity using operators such as Sobel, Canny, or Laplacian of Gaussian, then groups pixels into regions bounded by these edges.
- **Region-Based Methods**: Region growing, split-and-merge, and watershed algorithms group neighboring pixels with similar properties (intensity, texture, color) into connected regions.
- **Clustering**: Algorithms like K-means, Mean Shift, and Fuzzy C-means partition the pixel feature space (e.g., RGB values, spatial coordinates) into clusters, each corresponding to a segment.
- **Graph-Cut**: Formulates segmentation as a graph partitioning problem where pixels are nodes and edge weights encode pairwise similarity, solved via min-cut/max-flow optimization.

### Deep Learning Methods

- **Fully Convolutional Networks (FCN)**: Replaces fully connected layers in classification networks with convolutional layers to produce spatial segmentation maps. FCNs can accept arbitrary input sizes and output dense pixel-wise predictions.
- **U-Net**: Introduced for biomedical image segmentation, U-Net features a symmetric encoder-decoder architecture with skip connections that preserve fine-grained spatial information lost during downsampling. The encoder extracts increasingly abstract features, while the decoder upsamples and refines the segmentation map.
- **DeepLab Family (v1, v2, v3, v3+)**: Uses atrous (dilated) convolutions to control the resolution of feature responses without increasing parameters. Employs Atrous Spatial Pyramid Pooling (ASPP) to capture multi-scale context by applying parallel atrous convolutions with different dilation rates.
- **Mask R-CNN**: Extends [[Object Detection#Faster R-CNN|Faster R-CNN]] by adding a mask branch that predicts a binary segmentation mask for each Region of Interest (RoI) in parallel with the existing classification and bounding-box regression heads.
- **SegFormer**: A Transformer-based segmentation framework that unifies a hierarchical Transformer encoder with a lightweight MLP decoder, achieving strong performance across diverse segmentation benchmarks.
- **Vision Transformers (ViT) for Segmentation**: Adapts [[Vision Transformers (ViT)]] by treating image patches as tokens and using Transformer encoders to capture global context, often combined with decoders that progressively upsample feature maps back to pixel resolution.

## Mathematical Formulation

For semantic segmentation, given an input image $I \in \mathbb{R}^{H \times W \times C}$ with height $H$, width $W$, and $C$ channels, the goal is to learn a mapping $f$:

$$f: \mathbb{R}^{H \times W \times C} \rightarrow \{1, \dots, K\}^{H \times W}$$

where $K$ is the number of semantic classes. The network outputs a probability distribution over classes for each pixel:

$$P(y_{ij} = k \mid I) = \frac{\exp(z_{ijk})}{\sum_{k'=1}^K \exp(z_{ijk'})}$$

The model is trained by minimizing the pixel-wise cross-entropy loss:

$$\mathcal{L} = -\frac{1}{HW} \sum_{i=1}^{H} \sum_{j=1}^{W} \sum_{k=1}^{K} \mathbb{1}\{y_{ij} = k\} \log P(y_{ij} = k \mid I)$$

For instance segmentation with Mask R-CNN, the multi-task loss combines classification, bounding-box regression, and mask prediction:

$$\mathcal{L} = \mathcal{L}_{\text{cls}} + \mathcal{L}_{\text{box}} + \mathcal{L}_{\text{mask}}$$

## Evaluation Metrics

- **Intersection over Union (IoU / Jaccard Index)**: Measures overlap between predicted and ground-truth regions:
  $$\text{IoU} = \frac{|A \cap B|}{|A \cup B|}$$
- **Mean IoU (mIoU)**: Average IoU across all classes, the most widely reported metric for semantic segmentation.
- **Pixel Accuracy**: Fraction of correctly classified pixels over total pixels.
- **Dice Coefficient (F1 Score)**: $2|A \cap B| / (|A| + |B|)$, commonly used in medical imaging.
- **Average Precision (AP)**: Used for instance segmentation, computed across IoU thresholds.

## Key Papers

- Long et al., "Fully Convolutional Networks for Semantic Segmentation" (2015) — CVPR
- Ronneberger et al., "U-Net: Convolutional Networks for Biomedical Image Segmentation" (2015) — MICCAI
- Chen et al., "DeepLab: Semantic Image Segmentation with Deep Convolutional Nets, Atrous Convolution, and Fully Connected CRFs" (2017) — TPAMI
- He et al., "Mask R-CNN" (2017) — ICCV
- Kirillov et al., "Panoptic Segmentation" (2019) — CVPR
- Xie et al., "SegFormer: Simple and Efficient Design for Semantic Segmentation with Transformers" (2021) — NeurIPS

## Related Topics

- [[Object Detection]]
- [[Vision Transformers (ViT)]]
- [[Image Classification]]
- [[Convolutional Neural Networks]]
- [[Graph Neural Networks for Vision]]

## Trade-offs

- **Speed vs. Accuracy**: Lightweight models (e.g., ENet, BiSeNet) run in real time on embedded devices but sacrifice accuracy, while heavy models (DeepLab, Mask R-CNN) achieve state-of-the-art results at slower inference speeds.
- **Global vs. Local Context**: CNNs capture local textures and edges well but struggle with long-range dependencies; Transformers excel at global context but may lose fine spatial detail, motivating hybrid architectures.
- **Annotation Cost**: Semantic segmentation requires dense pixel-level labels, which are far more expensive to produce than image-level labels or bounding boxes used in Object Detection.
