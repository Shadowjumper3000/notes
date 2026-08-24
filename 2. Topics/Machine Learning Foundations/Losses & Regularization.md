# Losses & Regularization

**Tags:** #topic #ml #loss #regularization

Loss functions quantify the discrepancy between model predictions and ground-truth targets, providing the signal for learning via [[Backpropagation]]. Regularization techniques modify the training objective or procedure to improve generalization by penalizing model complexity.

## Common Loss Functions

### Regression Losses

- **Mean Squared Error (MSE)**:
  $$
  \mathcal{L}_{\text{MSE}} = \frac{1}{n} \sum_{i=1}^n (y_i - \hat{y}_i)^2
  $$
  Sensitive to outliers; corresponds to Gaussian likelihood maximization.

- **Mean Absolute Error (MAE)**:
  $$
  \mathcal{L}_{\text{MAE}} = \frac{1}{n} \sum_{i=1}^n |y_i - \hat{y}_i|
  $$
  Robust to outliers; corresponds to Laplace likelihood.

- **Huber Loss**: Combines MSE and MAE:
  $$
  L_\delta(y, \hat{y}) = \begin{cases}
  \frac{1}{2}(y - \hat{y})^2 & \text{if } |y - \hat{y}| \le \delta \\
  \delta|y - \hat{y}| - \frac{1}{2}\delta^2 & \text{otherwise}
  \end{cases}
  $$

### Classification Losses

- **Binary Cross-Entropy (Log Loss)**:
  $$
  \mathcal{L}_{\text{BCE}} = -\frac{1}{n} \sum_{i=1}^n y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i)
  $$

- **Categorical Cross-Entropy**:
  $$
  \mathcal{L}_{\text{CE}} = -\frac{1}{n} \sum_{i=1}^n \sum_{k=1}^K y_{ik} \log(\hat{y}_{ik})
  $$

- **Hinge Loss** (SVM):
  $$
  \mathcal{L}_{\text{hinge}} = \frac{1}{n} \sum_{i=1}^n \max(0, 1 - y_i \hat{y}_i), \quad y_i \in \{-1, +1\}
  $$

### Generative / Structured Losses

- **Kullback–Leibler Divergence**: $D_{\text{KL}}(P \| Q) = \sum_x P(x) \log\frac{P(x)}{Q(x)}$
- **Wasserstein (Earth Mover's) Distance**: Used in WGANs and optimal transport.
- **Contrastive / Triplet Loss**: Used in metric learning and siamese networks.

## Regularization Techniques

### Parameter Norm Penalties

- **L1 (Lasso)**: $\Omega(\mathbf{w}) = \lambda \|\mathbf{w}\|_1$ — encourages sparsity (many weights become zero).
- **L2 (Ridge / Weight Decay)**: $\Omega(\mathbf{w}) = \frac{\lambda}{2} \|\mathbf{w}\|_2^2$ — encourages small weights without sparsity.
- **Elastic Net**: $\Omega(\mathbf{w}) = \lambda_1 \|\mathbf{w}\|_1 + \lambda_2 \|\mathbf{w}\|_2^2$.

### Structured Regularization

- **Dropout**: Randomly drops neurons during training (see [[Improving MLPs]]).
- **Batch Normalization**: Normalizes layer inputs, providing an implicit regularization effect.
- **Label Smoothing**: Replaces one-hot targets with smoothed versions $y_{ik} = (1 - \epsilon)\delta_{k, \text{true}} + \epsilon/K$.
- **Data Augmentation**: Generates transformed training examples (rotations, crops, noise).

### Early Stopping

Halts training when validation loss increases for a patience window, acting as a form of implicit regularization by limiting the effective model capacity.

## Bias–Variance Perspective

Regularization typically increases bias while reducing variance, shifting the model along the [[Bias–Variance Tradeoff]] curve toward simpler solutions.

## Related Concepts

- [[Improving MLPs]] — practical training techniques for neural networks
- [[Bias–Variance Tradeoff]] — theoretical framework for understanding regularization
- [[Decision Trees]] — pruning as a form of regularization
- [[Boosting]] — shrinkage (learning rate) as a regularizer
