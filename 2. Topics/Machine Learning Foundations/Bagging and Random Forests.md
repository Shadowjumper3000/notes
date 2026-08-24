# Bagging and Random Forests

**Tags:** #topic #ml #ensembles #random-forest #bagging

**Bagging** (Bootstrap Aggregating) and **Random Forests** are ensemble methods that combine multiple [[Decision Trees]] to improve predictive accuracy and control overfitting. They belong to the class of ensemble learning techniques alongside [[Boosting]].

## Bagging

Given a dataset $\mathcal{D} = \{(\mathbf{x}_i, y_i)\}_{i=1}^n$, bagging generates $B$ bootstrap replicates $\mathcal{D}_b$ (sampled with replacement from $\mathcal{D}$) and trains a model $f_b$ on each:

$$
\hat{f}_{\text{bag}}(\mathbf{x}) = \frac{1}{B} \sum_{b=1}^B f_b(\mathbf{x}) \quad \text{(regression)} \quad\text{or}\quad \hat{y} = \text{majority vote}\{f_b(\mathbf{x})\} \quad\text{(classification)}
$$

### Bias–Variance Tradeoff

Bagging reduces **variance** without increasing bias by averaging uncorrelated (or weakly correlated) models. If each model has identically distributed predictions with variance $\sigma^2$ and pairwise correlation $\rho$, the ensemble variance is:

$$
\rho\,\sigma^2 + \frac{1 - \rho}{B}\,\sigma^2
$$

As $B \to \infty$, variance approaches $\rho\,\sigma^2$, making low correlation critical.

## Random Forests

Random Forests (Breiman, 2001) extend bagging by introducing **feature subsampling**: at each split, only a random subset of $m \ll p$ features is considered. This decorrelates the trees further, reducing variance beyond standard bagging.

### Algorithm

1. For $b = 1$ to $B$:
   - Draw a bootstrap sample $\mathcal{D}_b$ of size $n$.
   - Grow a decision tree $f_b$ on $\mathcal{D}_b$:
     - At each node, select $m$ features uniformly at random from all $p$ features.
     - Pick the best split among those $m$ features.
     - Grow the tree to full depth (no pruning).
2. Output the ensemble $\{f_b\}_{b=1}^B$.

### Hyperparameters

- **$B$** (number of trees): Larger values improve stability; diminishing returns after a few hundred.
- **$m$** (features per split): Default $m = \sqrt{p}$ (classification) or $m = p/3$ (regression).
- **Minimum node size**: Controls leaf granularity.

## Properties

- **Robust to overfitting**: Increasing $B$ does not cause overfitting; trees are de-correlated.
- **Handles mixed data types**: Naturally accommodates categorical and numerical features.
- **Feature importance**: Can compute permutation importance or mean decrease in impurity across trees.
- **Out-of-bag (OOB) error**: Each tree is trained on ~63.2% of the data; the remaining 36.8% can be used as a validation set without cross-validation.

## Applications

- Classification and regression on tabular data
- Feature selection via importance ranking
- Anomaly detection (isolation forests)
- Missing value imputation (proximity matrix)

## Related Concepts

- [[Decision Trees]] — the base learner used in Random Forests
- [[Boosting]] — sequential ensemble method that reduces bias rather than variance
- [[Bias–Variance Tradeoff]] — theoretical framework explaining why bagging works
