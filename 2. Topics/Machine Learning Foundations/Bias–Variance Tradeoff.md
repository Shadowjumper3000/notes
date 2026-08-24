# Bias–Variance Tradeoff

**Tags:** #topic #ml #bias-variance

The bias–variance tradeoff is a central concept in supervised learning that decomposes the expected generalization error of a model into three sources: **bias**, **variance**, and **irreducible noise**. It guides model selection and the understanding of overfitting and underfitting.

## Mathematical Decomposition

Let $f(\mathbf{x})$ be the true underlying function, and $\hat{f}(\mathbf{x})$ an estimator trained on dataset $\mathcal{D}$. For a test point $\mathbf{x}$ with target $y = f(\mathbf{x}) + \epsilon$ where $\mathbb{E}[\epsilon] = 0$ and $\text{Var}(\epsilon) = \sigma^2_\epsilon$, the expected squared error is:

$$
\begin{aligned}
\mathbb{E}_\mathcal{D}[(y - \hat{f}(\mathbf{x}))^2] &= \mathbb{E}_\mathcal{D}[(f(\mathbf{x}) + \epsilon - \hat{f}(\mathbf{x}))^2] \\
&= \underbrace{(f(\mathbf{x}) - \mathbb{E}_\mathcal{D}[\hat{f}(\mathbf{x})])^2}_{\text{Bias}^2} \;+\; \underbrace{\mathbb{E}_\mathcal{D}[(\hat{f}(\mathbf{x}) - \mathbb{E}_\mathcal{D}[\hat{f}(\mathbf{x})])^2]}_{\text{Variance}} \;+\; \underbrace{\sigma^2_\epsilon}_{\text{Irreducible Error}}
\end{aligned}
$$

### Interpretation

- **Bias**: The systematic error from incorrect assumptions in the learning algorithm. High bias leads to **underfitting** (too simple a model).
- **Variance**: The sensitivity of $\hat{f}$ to fluctuations in the training set. High variance leads to **overfitting** (too complex a model).
- **Irreducible error**: The noise inherent in the data, which no model can eliminate.

## The Tradeoff

Model complexity controls the balance:

- **Simple models** (e.g., linear regression): High bias, low variance.
- **Complex models** (e.g., deep trees, neural networks): Low bias, high variance.

The optimal model minimizes the sum of bias$^2$ and variance at the "sweet spot" of complexity.

## Strategies for Managing the Tradeoff

### Reducing Variance
- [[Bagging and Random Forests]] — averaging over bootstrap samples
- [[Improving MLPs]] — dropout, weight decay, early stopping
- [[Losses & Regularization]] — L1/L2 penalties shrink coefficients

### Reducing Bias
- [[Boosting]] — sequentially correcting errors of weak learners
- Adding more features or increasing model capacity (e.g., kernel trick, deeper networks)

### Both
- Cross-validation to select the optimal complexity point
- Ensemble methods that combine models with different bias-variance profiles

## Related Concepts

- [[Decision Trees]] — high-variance learners often pruned to manage the tradeoff
- [[Boosting]] — reduces bias by focusing on misclassified examples
- [[Bagging and Random Forests]] — reduces variance by averaging decorrelated trees
- [[Principal Component Analysis (PCA)]] — dimensionality reduction that can reduce variance at the cost of some bias
