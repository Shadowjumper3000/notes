# Deep Learning Architectures

**Tags:** #topic #ml #deep-learning #architectures

Deep learning architectures are neural network topologies that compose multiple layers of learned transformations. They extend [[Neural Foundations]] to enable representation learning at multiple levels of abstraction.

## Core Architectures

- **[[Multilayer Perceptron]] (MLP)**: A fully connected feedforward network with one or more hidden layers. The universal approximator.
- **[[Feedforward Neural Network]]**: The general class of networks where information moves only forward (no cycles); MLPs are a special case.
- **Convolutional Neural Network (CNN)**: Uses convolutional filters and pooling to exploit spatial structure in images, audio, or sequences.
- **Recurrent Neural Network (RNN)**: Processes sequential data by maintaining a hidden state across timesteps; variants include LSTM and GRU.
- **Transformer**: Relies on self-attention mechanisms rather than recurrence or convolution. The dominant architecture in NLP and increasingly in vision and audio.

## Learning Paradigms

- **[[Backpropagation]]**: The algorithm that computes gradients by applying the chain rule through the computation graph. Every deep architecture relies on it.
- **[[Epoch]]**: One complete pass through the training dataset during optimization.

## Architectural Innovations

- **Residual Networks (ResNets)**: Skip connections ($\mathbf{y} = \mathcal{F}(\mathbf{x}) + \mathbf{x}$) allow training hundreds of layers by mitigating the vanishing gradient problem.
- **Attention Mechanisms**: Allow the model to focus on relevant parts of the input; the key building block of Transformers.
- **Normalization Layers**: Batch, Layer, Instance, and Group normalization stabilize training across architectures.
- **Mixture of Experts (MoE)**: Sparsely activated sub-networks that scale model capacity without proportional compute increase.

## Modern Trends

- **Foundation models**: Large-scale pre-trained models (e.g., GPT, BERT, CLIP) fine-tuned for downstream tasks.
- **Diffusion-based architectures**: U-Nets and Transformers for [[Diffusion Models]].
- **Neural Architecture Search (NAS)**: Automated discovery of optimal topologies.

## Related Concepts

- [[Neural Foundations]] — the perceptron, activation functions, and bias
- [[Improving MLPs]] — practical techniques for training deeper networks
- [[Generative Adversarial Networks (GANs)]] — generator/discriminator architectures
- [[Diffusion Models]] — U-Net and Transformer-based generative backbones
- [[Losses & Regularization]] — loss functions and regularizers used across all architectures
