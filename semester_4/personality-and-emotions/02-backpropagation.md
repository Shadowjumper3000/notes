# How It Works

Backpropagation is a supervised learning algorithm used to train neural networks by minimizing the error between the predicted output and the actual target. It works by propagating the error backward through the network and updating the weights using gradient descent.

---

## Key Steps in Backpropagation

1. **Forward Pass**:
   - Compute the output of the network for a given input.
   - Calculate the loss (error) between the predicted output and the target.

2. **Backward Pass**:
   - Compute the gradient of the loss with respect to each weight in the network.
   - Update the weights using gradient descent.

---

## Mathematical Formulation

### 1. Forward Pass

For a neural network with \( L \) layers, the forward pass computes the output of each layer \( l \):

- **Weighted Sum**:
  $$
  z^{(l)} = W^{(l)} a^{(l-1)} + b^{(l)}
  $$
  where:
  - \( W^{(l)} \): Weight matrix for layer \( l \).
  - \( a^{(l-1)} \): Activation from the previous layer.
  - \( b^{(l)} \): Bias vector for layer \( l \).

- **Activation**:
  $$
  a^{(l)} = f(z^{(l)})
  $$
  where \( f \) is the activation function (e.g., ReLU, sigmoid).

- **Output Layer**:
  The final output \( a^{(L)} \) is compared to the target \( y \) using a loss function \( \mathcal{L} \):
  $$
  \mathcal{L} = \frac{1}{2} (a^{(L)} - y)^2 \quad \text{(for mean squared error)}
  $$

---

### 2. Backward Pass

The goal is to compute the gradient of the loss \( \mathcal{L} \) with respect to each weight \( W^{(l)} \) and bias \( b^{(l)} \).

- **Output Layer Gradient**:
  Compute the error at the output layer:
  $$
  \delta^{(L)} = \frac{\partial \mathcal{L}}{\partial a^{(L)}} \cdot f'(z^{(L)})
  $$
  where \( f' \) is the derivative of the activation function.

- **Hidden Layer Gradients**:
  Propagate the error backward through the network:
  $$
  \delta^{(l)} = \left( (W^{(l+1)})^T \delta^{(l+1)} \right) \cdot f'(z^{(l)})
  $$

- **Weight and Bias Updates**:
  Compute the gradients for weights and biases:
  $$
  \frac{\partial \mathcal{L}}{\partial W^{(l)}} = \delta^{(l)} (a^{(l-1)})^T
  $$
  $$
  \frac{\partial \mathcal{L}}{\partial b^{(l)}} = \delta^{(l)}
  $$

  Update the weights and biases using gradient descent:
  $$
  W^{(l)} \leftarrow W^{(l)} - \eta \frac{\partial \mathcal{L}}{\partial W^{(l)}}
  $$
  $$
  b^{(l)} \leftarrow b^{(l)} - \eta \frac{\partial \mathcal{L}}{\partial b^{(l)}}
  $$
  where \( \eta \) is the learning rate.

---

## Summary

- Backpropagation computes gradients of the loss with respect to each weight and bias.
- Gradients are propagated backward through the network using the chain rule.
- Weights and biases are updated iteratively to minimize the loss.

---

## Example

For a simple neural network with one hidden layer:

1. Forward pass:
   - Compute \( z^{(1)} = W^{(1)} x + b^{(1)} \).
   - Compute \( a^{(1)} = f(z^{(1)}) \).
   - Compute \( z^{(2)} = W^{(2)} a^{(1)} + b^{(2)} \).
   - Compute \( a^{(2)} = f(z^{(2)}) \).

2. Backward pass:
   - Compute \( \delta^{(2)} = (a^{(2)} - y) \cdot f'(z^{(2)}) \).
   - Compute \( \delta^{(1)} = (W^{(2)})^T \delta^{(2)} \cdot f'(z^{(1)}) \).
   - Update weights and biases using gradient descent.

---

## References

- Goodfellow, Ian, et al. "Deep Learning." MIT Press, 2016.
- Nielsen, Michael. "Neural Networks and Deep Learning." 2015.