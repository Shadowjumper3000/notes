# Improving MLPs

**Tags:** #topic #ml #mlp #neural-networks #deep-learning

Multilayer Perceptrons (MLPs) are foundational [[Deep Learning Architectures]], but their performance depends heavily on careful engineering. This note covers practical techniques for training deeper and more effective MLPs, all built on [[Neural Foundations]].

## Activation Functions

The choice of activation function dramatically affects gradient flow:

- **ReLU** ($\max(0, x)$): Mitigates vanishing gradients; prone to dead neurons.
- **Leaky ReLU / PReLU**: $\max(\alpha x, x)$ with small $\alpha$ to avoid dead ReLU.
- **ELU / SELU**: Exponential variants that produce negative activations, pushing mean toward zero.
- **Swish / SiLU**: $x \cdot \sigma(x)$, a smooth non-monotonic function that often outperforms ReLU.

## Weight Initialization

Proper initialization prevents vanishing or exploding activations:

- **Xavier (Glorot) initialization**: $W \sim \mathcal{U}\!\left(-\sqrt{\frac{6}{n_{\text{in}} + n_{\text{out}}}}, \sqrt{\frac{6}{n_{\text{in}} + n_{\text{out}}}}\right)$ — designed for tanh activations.
- **He (Kaiming) initialization**: $W \sim \mathcal{N}\!\left(0, \sqrt{\frac{2}{n_{\text{in}}}}\right)$ — designed for ReLU activations.

## Batch Normalization (Ioffe & Szegedy, 2015)

Normalizes the input to each layer across a minibatch:

$$
\hat{x}_i = \frac{x_i - \mu_{\mathcal{B}}}{\sqrt{\sigma^2_{\mathcal{B}} + \epsilon}}, \qquad y_i = \gamma \hat{x}_i + \beta
$$

where $\mu_{\mathcal{B}}$, $\sigma^2_{\mathcal{B}}$ are batch statistics, and $\gamma, \beta$ are learnable scale and shift. Benefits:

- Enables higher learning rates
- Reduces internal covariate shift
- Provides mild regularization

## Dropout (Srivastava et al., 2014)

Randomly sets a fraction $p$ of neuron activations to zero during training, preventing co-adaptation:

$$
\tilde{\mathbf{h}} = \mathbf{r} \odot \mathbf{h}, \quad r_i \sim \text{Bernoulli}(1-p)
$$

At test time, all neurons are scaled by $1-p$ (or inverted dropout is used).

## Learning Rate Schedules

- **Step decay**: Multiply LR by factor $\gamma$ every $k$ epochs.
- **Exponential decay**: $\eta_t = \eta_0 \cdot e^{-kt}$.
- **Cosine annealing**: LR follows a cosine curve; often combined with warm restarts (SGDR).
- **Cyclical LR**: Oscillates between bounds to escape saddle points.

## Optimization Algorithms

[[Backpropagation]] with advanced optimizers improves convergence:

- **Adam**: Adaptive learning rates per parameter with momentum. Default choice for most tasks.
- **SGD + Momentum**: Strong generalization, especially with proper scheduling.
- **RAdam / NAdam / AdamW**: Variants that correct variance or decouple weight decay.

## Regularization Techniques

- **Early stopping**: Monitor validation loss and halt when it plateaus.
- **Weight decay (L2 regularization)**: Penalizes large weights.
- **Data augmentation**: Artificially expands the training set via label-preserving transformations.

## Related Concepts

- [[Losses & Regularization]] — loss functions and regularization strategies
- [[Deep Learning Architectures]] — how MLPs fit into broader neural network families
- [[Neural Foundations]] — the perceptron, activation functions, and backpropagation
