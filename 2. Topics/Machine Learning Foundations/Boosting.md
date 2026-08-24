# Boosting

**Tags:** #topic #ml #boosting #adaboost #gradient-boosting

Boosting is an ensemble technique that combines many **weak learners** (models slightly better than random chance) into a single strong learner by training them sequentially, where each new learner focuses on the mistakes of its predecessors. Unlike [[Bagging and Random Forests]], which reduces variance, boosting primarily reduces **bias**.

## AdaBoost (Adaptive Boosting)

AdaBoost (Freund & Schapire, 1997) was the first practical boosting algorithm. Each training example is assigned a weight $w_i$, updated after each round.

### Algorithm

1. Initialize weights $w_i^{(1)} = 1/n$ for $i = 1, \dots, n$.
2. For $t = 1, \dots, T$:
   - Train a weak learner $h_t(\mathbf{x})$ on the weighted training set.
   - Compute weighted error: $\epsilon_t = \frac{\sum_{i: h_t(\mathbf{x}_i) \neq y_i} w_i^{(t)}}{\sum_i w_i^{(t)}}$.
   - Set learner weight: $\alpha_t = \frac{1}{2} \ln\!\left(\frac{1 - \epsilon_t}{\epsilon_t}\right)$.
   - Update instance weights: $w_i^{(t+1)} = w_i^{(t)} \exp(-\alpha_t y_i h_t(\mathbf{x}_i))$.
   - Normalize weights so $\sum_i w_i^{(t+1)} = 1$.
3. Final prediction: $H(\mathbf{x}) = \text{sign}\!\left(\sum_{t=1}^T \alpha_t h_t(\mathbf{x})\right)$.

## Gradient Boosting

Gradient Boosting (Friedman, 2001) generalizes boosting to arbitrary differentiable loss functions. At each iteration $t$, a weak learner $h_t$ is fitted to the **negative gradient** (pseudo-residual) of the loss with respect to the current prediction.

Given loss $L(y, F(\mathbf{x}))$:

$$
F_0(\mathbf{x}) = \arg\min_\gamma \sum_{i=1}^n L(y_i, \gamma)
$$

For $t = 1$ to $T$:

$$
r_{it} = -\left[ \frac{\partial L(y_i, F(\mathbf{x}_i))}{\partial F(\mathbf{x}_i)} \right]_{F=F_{t-1}}, \quad i = 1,\dots,n
$$

$$
F_t(\mathbf{x}) = F_{t-1}(\mathbf{x}) + \eta \cdot h_t(\mathbf{x})
$$

where $\eta$ is a learning rate (shrinkage) that controls regularization.

### Popular Gradient Boosting Variants

- **XGBoost**: Adds L1/L2 regularization, second-order gradients (Newton boosting), and column subsampling. Highly optimized for speed.
- **LightGBM**: Uses histogram-based splits and Gradient-based One-Side Sampling (GOSS) for efficiency on large datasets.
- **CatBoost**: Optimized for categorical features using ordered target statistics and symmetric decision trees.

## Properties

- **Low bias**: Weak learners can be very simple (e.g., stumps — depth-1 trees).
- **Overfitting risk**: Too many iterations can overfit; early stopping, shrinkage, and subsampling mitigate this.
- **Feature importance**: Can aggregate split-based importance across all trees.
- **Handles mixed data types**: Naturally works with tabular data.

## Applications

- Winning many Kaggle competitions on structured/tabular data
- Ranking (LambdaRank, LambdaMART)
- Click-through rate prediction in advertising
- Credit scoring and risk modeling

## Related Concepts

- [[Bagging and Random Forests]] — parallel ensemble method vs. sequential boosting
- [[Decision Trees]] — the most common weak learner for boosting
- [[Bias–Variance Tradeoff]] — boosting reduces bias while carefully controlling variance
- [[Losses & Regularization]] — the loss functions minimized by gradient boosting
