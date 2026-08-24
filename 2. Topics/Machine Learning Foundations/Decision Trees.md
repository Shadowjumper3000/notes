# Decision Trees

**Tags:** #topic #ml #decision-trees #classification #regression

Decision Trees are a non-parametric supervised learning method that partitions the input space into axis-aligned regions via a hierarchical sequence of binary decisions. Each internal node tests a feature, each branch represents the outcome, and each leaf assigns a prediction (class label or numerical value).

## Tree Construction (CART)

Most decision tree algorithms (CART, ID3, C4.5) grow trees greedily using a top-down recursive partitioning strategy.

### Splitting Criteria

At a node containing $N$ samples, the algorithm selects the feature $j$ and threshold $t$ that maximize the **purity gain**:

$$
G(j, t) = I(\text{parent}) - \frac{N_{\text{left}}}{N} I(\text{left}) - \frac{N_{\text{right}}}{N} I(\text{right})
$$

where $I$ is an impurity measure:

- **Gini impurity** (classification):
  $$
  I_{\text{Gini}} = 1 - \sum_{k=1}^K p_k^2
  $$

- **Cross-entropy / Deviance** (classification):
  $$
  I_{\text{CE}} = -\sum_{k=1}^K p_k \log p_k
  $$

- **Mean squared error** (regression):
  $$
  I_{\text{MSE}} = \frac{1}{N} \sum_{i=1}^N (y_i - \bar{y})^2
  $$

### Stopping and Pruning

To prevent overfitting:
- **Pre-pruning**: Stop splitting when depth reaches a maximum, a node contains too few samples, or impurity decrease falls below a threshold.
- **Post-pruning (Cost-complexity pruning)**: Grow a full tree, then collapse branches that contribute little to overall loss:

  $$
  \min_T \sum_{\text{leaf } \ell} N_\ell \cdot I(\ell) + \alpha \cdot |T|
  $$

  where $|T|$ is the number of leaf nodes and $\alpha \geq 0$ controls regularization.

## Algorithm (CART)

1. Start with all data at the root node.
2. For each node:
   - For each feature $j$ and possible split value $t$, compute gain $G(j, t)$.
   - Select the split $(j^*, t^*)$ that maximizes $G$.
   - Partition the data into left and right child nodes.
   - Recurse on each child until a stopping criterion is met.
3. Optionally, prune the resulting tree.

## Properties

- **Interpretability**: Trees can be visualized and understood by humans.
- **Non-parametric**: No assumption about data distribution.
- **Handles mixed types**: Naturally processes numerical and categorical features.
- **Variance**: Fully grown trees have high variance — small changes in data yield very different trees.
- **Instability**: Greedy partitioning is prone to local optima; mitigated by [[Bagging and Random Forests]].

## Applications

- Credit scoring and risk assessment
- Medical diagnosis (interpretable decision rules)
- As base learners for [[Bagging and Random Forests]] and [[Boosting]]

## Related Concepts

- [[Bagging and Random Forests]] — averages many deep trees to reduce variance
- [[Boosting]] — sequentially fits shallow trees to residuals, reducing bias
- [[Bias–Variance Tradeoff]] — tree depth directly controls the bias-variance balance
- [[Clustering]] — decision trees can segment the input space similarly
