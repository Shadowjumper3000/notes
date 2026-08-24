# Neural Foundations

**Tags:** #topic #ml #neural-networks #deep-learning

This note covers the fundamental building blocks of neural networks, from the first mathematical model of a neuron to the core components of modern [[Deep Learning Architectures]].

## The McCulloch-Pitts Neuron (The Logic Gate)

Proposed by McCulloch and Pitts (1943), the first mathematical model of a biological neuron. It computes a binary output from weighted binary inputs:

$$
y = \phi\!\left(\sum_{i=1}^n w_i x_i - \theta\right)
$$

where $x_i \in \{0,1\}$ are inputs, $w_i$ are weights, $\theta$ is a threshold, and $\phi$ is a step function. This model can represent basic logical functions (AND, OR, NOT) but cannot learn — weights are hand-set.

## The Perceptron (The Learner)

Rosenblatt (1958) introduced the perceptron, adding a learning rule. The perceptron takes real-valued inputs and uses a step activation:

$$
\hat{y} = \begin{cases} 1 & \text{if } \mathbf{w}^\top \mathbf{x} + b > 0 \\ 0 & \text{otherwise} \end{cases}
$$

The **perceptron learning rule** updates weights when a misclassification occurs:

$$
\mathbf{w} \leftarrow \mathbf{w} + \eta\,(y - \hat{y})\,\mathbf{x}, \qquad b \leftarrow b + \eta\,(y - \hat{y})
$$

The perceptron convergence theorem guarantees convergence for linearly separable data, but it fails on non-linear problems (e.g., XOR).

## Bias (Neural Networks)

The bias term $b$ (or $\theta$) shifts the activation function:

$$
z = \mathbf{w}^\top \mathbf{x} + b
$$

It acts as an intercept, allowing the neuron to fire even when the weighted sum of inputs is zero. Without bias, the decision boundary always passes through the origin, severely limiting representational power.

## Activation Functions

Activation functions introduce non-linearity, enabling neural networks to learn complex patterns. Common choices:

- **Sigmoid**: $\sigma(x) = 1 / (1 + e^{-x})$, outputs in $(0,1)$. Used historically in binary classification output layers. Suffers from vanishing gradients.
- **Tanh**: $\tanh(x) = (e^x - e^{-x}) / (e^x + e^{-x})$, outputs in $(-1,1)$. Zero-centered, but still has vanishing gradient issues.
- **ReLU**: $\max(0, x)$. Default for most hidden layers. Mitigates vanishing gradients; can produce "dead neurons."
- **Leaky ReLU / Parametric ReLU**: $\max(\alpha x, x)$ with small $\alpha$ to allow negative gradients.
- **Softmax**: $\text{softmax}(\mathbf{z})_i = e^{z_i} / \sum_j e^{z_j}$. Converts logits to a probability distribution. Used in the output layer for multi-class classification.

## From Neurons to Networks

A single neuron (perceptron) produces a linear decision boundary. Stacking neurons into layers creates an MLP:

$$
\mathbf{h}_1 = \phi_1(\mathbf{W}_1 \mathbf{x} + \mathbf{b}_1), \quad \mathbf{h}_2 = \phi_2(\mathbf{W}_2 \mathbf{h}_1 + \mathbf{b}_2), \quad \dots
$$

With one or more hidden layers, the network can approximate any continuous function (universal approximation theorem). Learning is driven by [[Backpropagation]] and gradient-based optimization.

## Related Concepts

- [[Deep Learning Architectures]] — how these foundations scale to modern topologies
- [[Improving MLPs]] — activation choices, initialization, normalization
- [[Losses & Regularization]] — loss functions that pair with activation choices
- [[Backpropagation]] — the learning algorithm that makes deep networks trainable
