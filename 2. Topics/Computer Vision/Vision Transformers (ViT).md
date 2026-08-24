# Vision Transformers (ViT)

Vision Transformers (ViT) apply the Transformer architecture — originally developed for natural language processing — to computer vision tasks by dividing images into a sequence of fixed-size patches, linearly embedding each patch, and processing the resulting token sequence with a standard Transformer encoder. Introduced by Dosovitskiy et al. in 2020, ViT demonstrated that a pure Transformer can outperform state-of-the-art convolutional neural networks (CNNs) on image classification when pre-trained on sufficiently large datasets.

## Architecture

### Patch Embedding

Given an input image $I \in \mathbb{R}^{H \times W \times C}$ with height $H$, width $W$, and $C$ channels, ViT reshapes the image into a sequence of $N = \frac{HW}{P^2}$ patches of size $P \times P$:

$$x_p \in \mathbb{R}^{N \times (P^2 C)}$$

Each patch is flattened and linearly projected to a $D$-dimensional embedding using a trainable matrix $E \in \mathbb{R}^{(P^2 C) \times D}$:

$$z_0 = [x_{\text{class}}; x_p^1 E; x_p^2 E; \dots; x_p^N E] + E_{\text{pos}}$$

A learnable classification token $x_{\text{class}}$ is prepended to the sequence (its final representation serves as the image representation), and learned positional encodings $E_{\text{pos}} \in \mathbb{R}^{(N+1) \times D}$ are added to retain spatial information — since the Transformer is permutation-invariant.

### Transformer Encoder

The encoder consists of $L$ identical layers, each containing:

1. **Multi-Head Self-Attention (MHSA)**:
   $$Q = z_{\ell-1} W_Q, \quad K = z_{\ell-1} W_K, \quad V = z_{\ell-1} W_V$$
   $$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V$$
   where $d_k = D / h$ and $h$ is the number of attention heads. The outputs from all heads are concatenated and projected.

2. **MLP (Multilayer Perceptron)**: Two linear layers with a GELU activation:
   $$\text{MLP}(x) = W_2 \, \text{GELU}(W_1 x + b_1) + b_2$$

3. **Layer Normalization (LN)** and **Residual Connections** applied before each block (pre-norm):
   $$z'_\ell = \text{MHSA}(\text{LN}(z_{\ell-1})) + z_{\ell-1}$$
   $$z_\ell = \text{MLP}(\text{LN}(z'_\ell)) + z'_\ell$$

### Classification Head

The final output corresponding to the classification token $z_L^0$ is fed into a linear classifier (or MLP head) to produce class logits:

$$y = \text{softmax}(z_L^0 W_{\text{head}} + b_{\text{head}})$$

## Key Properties

- **Inductive Bias**: Unlike CNNs which encode strong inductive biases (locality, translation equivariance, weight sharing), ViT has minimal image-specific inductive bias. The model must learn spatial relationships entirely from the positional encodings and attention weights, which requires more data to converge but can capture more flexible patterns.
- **Global Receptive Field**: Self-attention layers connect every patch to every other patch in a single layer, giving ViT an inherently global receptive field from the first layer — a significant advantage over CNNs that grow their receptive field slowly through successive convolutions.
- **O(N^2) Complexity**: Standard self-attention has quadratic complexity in the number of patches, making ViT computationally expensive for high-resolution images. This motivates hierarchical or efficient variants.

## Variants and Improvements

### Data-Efficient ViT (DeiT)

DeiT introduces a knowledge distillation strategy using a CNN teacher and a distillation token (analogous to the class token) to train ViT effectively on ImageNet-1k without requiring the massive JFT-300M dataset. Uses hard and soft distillation losses:

$$\mathcal{L} = (1 - \lambda) \mathcal{L}_{\text{CE}}(\psi(Z_s), y) + \lambda \mathcal{L}_{\text{CE}}(\psi(Z_s), y_t)$$

where $y_t$ is the teacher's hard prediction and $\lambda$ controls distillation strength.

### Swin Transformer

Addresses ViT's quadratic complexity by introducing a **hierarchical** architecture with shifted windows. Self-attention is computed within local windows of $M \times M$ patches (reducing complexity to $O(N \cdot M^2)$), and the shifted window mechanism enables cross-window connections across layers. The patch merging layers progressively reduce spatial resolution while increasing channel dimension, mimicking CNN feature pyramids.

### Pyramid Vision Transformer (PVT)

Introduces a spatial-reduction attention (SRA) layer that reduces the spatial scale of keys and values before computing attention, enabling high-resolution feature maps and making PVT suitable for dense prediction tasks like [[Object Detection]] and [[Image Segmentation]].

### CrossViT

Uses dual-branch architecture with different patch sizes to capture both fine and coarse-grained features, fusing information across branches via cross-attention.

## Mathematical Analysis

### Computational Complexity

Standard ViT self-attention complexity per layer:

$$\Omega(\text{MHSA}) = O(N^2 D + N D^2)$$

where $N$ is the number of patches (sequence length). For a $224 \times 224$ image with $P = 16$, $N = 196$, giving $O(196^2 D) = O(38416 D)$.

Swin Transformer's windowed attention:

$$\Omega(\text{W-MSA}) = O\!\left(N \cdot M^2 D + N D^2\right)$$

Typically $M = 7$, so per-window complexity is $O(49 D)$ — a substantial reduction.

### Positional Encoding

ViT uses learned 1D positional embeddings. Alternatives explored include:
- **2D positional embeddings**: Encode explicit (x, y) coordinate information
- **Relative positional biases** (Swin): Add a learnable bias $B \in \mathbb{R}^{(2M-1) \times (2M-1)}$ to each attention logit:
  $$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}} + B\right) V$$
- **Rotary Position Embedding (RoPE)**: Encodes position through rotation matrices applied to queries and keys

## Training Requirements

ViT is a data-hungry architecture. When trained from scratch on ImageNet-1k (1.3M images), ViT underperforms comparable CNNs. However, when pre-trained on large datasets (JFT-300M, ImageNet-21k, LAION-5B), ViT surpasses CNN counterparts. This has driven the adoption of large-scale pre-training and self-supervised methods like MAE (Masked Autoencoders) for ViT.

## Key Papers

- Dosovitskiy et al., "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale" (ViT, 2020) — ICLR 2021
- Touvron et al., "Training Data-Efficient Image Transformers & Distillation Through Attention" (DeiT, 2021) — ICML
- Liu et al., "Swin Transformer: Hierarchical Vision Transformer using Shifted Windows" (2021) — ICCV
- Wang et al., "Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions" (PVT, 2021) — ICCV
- Carion et al., "End-to-End Object Detection with Transformers" (DETR, 2020) — ECCV
- He et al., "Masked Autoencoders Are Scalable Vision Learners" (MAE, 2022) — CVPR

## Applications

- **Image Classification**: ViT serves as a backbone achieving state-of-the-art top-1 accuracy on ImageNet.
- **[[Object Detection]]**: DETR and its variants use Transformer architectures for end-to-end detection; Swin Transformer serves as a backbone for COCO detection.
- **[[Image Segmentation]]**: SETR (Segmentation Transformer), SegFormer, and MaskFormer apply Transformer architectures to semantic and panoptic segmentation.
- **Video Understanding**: TimeSformer and Video ViT extend patch-based attention to the spatiotemporal domain.
- **Multi-Modal Learning**: CLIP and Flava use ViT as the vision encoder paired with a text Transformer for vision-language tasks.

## Related Topics

- [[Attention Mechanisms]]
- [[Convolutional Neural Networks]]
- [[Object Detection]]
- [[Image Segmentation]]
- [[Self-Supervised Learning]]
- [[Natural Language Processing — Transformers]]

## Trade-offs

- **Data Efficiency vs. Performance**: ViT excels with large-scale data but underperforms CNNs on small datasets. Techniques like DeiT's distillation, stronger augmentation, and self-supervised pre-training help close this gap.
- **Computational Cost**: Quadratic self-attention limits ViT on high-resolution inputs. Hierarchical variants (Swin, PVT) mitigate this at the cost of architectural complexity.
- **Spatial Granularity**: Large patch sizes ($P=16$ or $P=32$) lose fine spatial detail, while small patches ($P=8$ or $P=4$) dramatically increase sequence length and computational cost.
