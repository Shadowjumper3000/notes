# Regularization in Machine Learning

## What is Regularization?

**Regularization** is a technique used to prevent overfitting by adding a penalty term to the loss function. It discourages overly complex models by constraining model parameters.

### The Problem: Overfitting

- **Overfitting** occurs when a model learns not only the underlying patterns but also the noise in the training data.
- High training accuracy but poor generalization to new data.
- Complex models with many parameters are more prone to overfitting.

---

## Types of Regularization

### 1. L1 Regularization (Lasso)

**L1 regularization** adds the sum of the absolute values of the model parameters to the loss function.

**Loss function with L1:**
$$
\mathcal{L}(\mathbf{w}) = \text{Loss} + \lambda \sum_{i=1}^{n} |w_i|
$$

**Properties:**
- **Feature Selection**: Can drive some weights to exactly zero, effectively performing feature selection.
- **Sparsity**: Produces sparse models with fewer non-zero parameters.
- **Use Case**: When you suspect many features are irrelevant.

**Gradient:**
- Not differentiable at zero; uses subgradient methods.

---

### 2. L2 Regularization (Ridge)

**L2 regularization** adds the sum of the squared values of the model parameters to the loss function.

**Loss function with L2:**
$$
\mathcal{L}(\mathbf{w}) = \text{Loss} + \lambda \sum_{i=1}^{n} w_i^2
$$

**Properties:**
- **Weight Decay**: Encourages small weights but doesn't force them to zero.
- **Smooth Penalty**: Differentiable everywhere.
- **Use Case**: When all features are potentially relevant but should be weighted carefully.

**Gradient:**
$$
\frac{\partial \mathcal{L}}{\partial w_i} = \frac{\partial \text{Loss}}{\partial w_i} + 2\lambda w_i
$$

---

### 3. Elastic Net

**Elastic Net** combines both L1 and L2 regularization.

**Loss function:**
$$
\mathcal{L}(\mathbf{w}) = \text{Loss} + \lambda_1 \sum_{i=1}^{n} |w_i| + \lambda_2 \sum_{i=1}^{n} w_i^2
$$

**Properties:**
- **Balance**: Gets benefits of both L1 and L2.
- **Grouped Selection**: Can select groups of correlated features.
- **Use Case**: When you have correlated features and want both feature selection and weight regularization.

---

## Hyperparameter: λ (Lambda)

The regularization parameter $\lambda$ controls the strength of regularization:

- **λ = 0**: No regularization (risk of overfitting).
- **Small λ**: Slight penalty, model complexity less constrained.
- **Large λ**: Strong penalty, model forced to be simpler (risk of underfitting).

**Choosing λ:**
- Use **cross-validation** to find the optimal value.
- Grid search or random search over a range of λ values.

---

## Dropout (Neural Networks)

**Dropout** is a regularization technique specific to neural networks.

**How it works:**
- During training, randomly "drop" (set to zero) a fraction of neurons in each layer.
- Forces the network to learn robust features that work with different subsets of neurons.
- At test time, use all neurons but scale their outputs.

**Dropout rate:**
$$
p = 0.2 \text{ to } 0.5 \text{ (typically)}
$$

**Benefits:**
- Prevents co-adaptation of neurons.
- Acts like training an ensemble of networks.

---

## Early Stopping

**Early stopping** monitors the model's performance on a validation set during training and stops when performance starts to degrade.

**Process:**
1. Train the model while monitoring validation loss.
2. Stop training when validation loss stops improving.
3. Restore the model to the state with the best validation performance.

**Benefits:**
- Simple and effective.
- Prevents overfitting without explicit penalty terms.

---

## Data Augmentation

**Data augmentation** artificially increases the size of the training dataset by creating modified versions of existing data.

**Examples:**
- **Images**: Rotation, flipping, cropping, color jittering.
- **Text**: Synonym replacement, back-translation.
- **Audio**: Time stretching, pitch shifting, adding noise.

**Benefits:**
- Helps the model generalize better.
- Reduces overfitting by exposing the model to more variations.

---

## Batch Normalization

**Batch normalization** normalizes the inputs of each layer to have mean 0 and variance 1.

**Formula:**
$$
\hat{x} = \frac{x - \mu_B}{\sqrt{\sigma_B^2 + \epsilon}}
$$

where $\mu_B$ and $\sigma_B^2$ are the mean and variance of the mini-batch.

**Benefits:**
- Stabilizes and accelerates training.
- Acts as a form of regularization.
- Reduces internal covariate shift.

---

## Weight Constraints

**Max-norm constraints** limit the magnitude of weight vectors.

**Constraint:**
$$
\|\mathbf{w}\|_2 \leq c
$$

If $\|\mathbf{w}\|_2 > c$, rescale $\mathbf{w}$ to satisfy the constraint.

**Benefits:**
- Prevents weights from growing too large.
- Often used with dropout in neural networks.

---

## Comparison of Regularization Techniques

| Technique | Type | Use Case | Effect on Weights |
|-----------|------|----------|-------------------|
| **L1** | Penalty | Feature selection | Some weights → 0 |
| **L2** | Penalty | All features relevant | All weights small |
| **Elastic Net** | Penalty | Correlated features | Combination of L1/L2 |
| **Dropout** | Stochastic | Neural networks | Random neuron removal |
| **Early Stopping** | Training control | Any model | Stops before overfitting |
| **Data Augmentation** | Data expansion | Limited data | More training examples |
| **Batch Normalization** | Normalization | Deep networks | Stabilizes training |

---

## Mathematical Intuition

### L2 Regularization as Prior

L2 regularization can be viewed as imposing a **Gaussian prior** on the weights:
$$
p(\mathbf{w}) \sim \mathcal{N}(0, \frac{1}{2\lambda} I)
$$

This corresponds to **Maximum A Posteriori (MAP)** estimation.

### L1 Regularization as Prior

L1 regularization corresponds to a **Laplace prior**:
$$
p(\mathbf{w}) \sim \text{Laplace}(0, \frac{1}{\lambda})
$$

This encourages sparsity in the solution.

---

## Practical Guidelines

1. **Start with L2** as a baseline regularization.
2. **Try L1** if you suspect many features are irrelevant.
3. **Use Dropout** in deep neural networks.
4. **Always use Early Stopping** as a safety net.
5. **Cross-validate** to find the best λ value.
6. **Combine techniques** for best results (e.g., L2 + Dropout + Early Stopping).

---

## Summary

Regularization is essential for building models that generalize well to unseen data. By adding constraints or modifying the training process, regularization techniques help prevent overfitting and lead to more robust machine learning models.
