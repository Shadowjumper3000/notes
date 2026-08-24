# MDS & Isomap

**Tags:** #topic #ml #dimensionality-reduction #manifold-learning

Multi-Dimensional Scaling (MDS) and Isomap are unsupervised dimensionality reduction techniques that preserve the geometric structure of data. MDS focuses on pairwise Euclidean distances, while Isomap extends the idea to geodesic distances along a manifold.

## Multi-Dimensional Scaling (MDS)

Given pairwise dissimilarities $\delta_{ij}$ between points $\mathbf{x}_i, \mathbf{x}_j \in \mathbb{R}^p$, MDS finds a low-dimensional embedding $\mathbf{z}_1, \dots, \mathbf{z}_n \in \mathbb{R}^d$ (with $d \ll p$) that minimizes:

### Classical (Metric) MDS

$$
\min_{\mathbf{z}_1,\dots,\mathbf{z}_n} \sum_{i,j} \bigl( \|\mathbf{z}_i - \mathbf{z}_j\| - \delta_{ij} \bigr)^2
$$

This is solved by double-centering the squared distance matrix $\Delta^{(2)}$ (where $\Delta_{ij} = \delta_{ij}$) and performing eigendecomposition. If $\delta_{ij}$ are Euclidean distances, classical MDS is equivalent to [[Principal Component Analysis (PCA)]].

### Non-metric MDS

Preserves only the **rank order** of dissimilarities (ordinal scaling), using isotonic regression to fit distances to a monotonic transformation of the original dissimilarities.

## Isomap (Isometric Mapping)

Isomap (Tenenbaum, de Silva & Langford, 2000) approximates geodesic distances along a data manifold and then applies MDS to those distances.

### Algorithm

1. **Construct neighborhood graph**: Connect each point $\mathbf{x}_i$ to its $k$ nearest neighbors (or all points within radius $\epsilon$). Edge weights are Euclidean distances.
2. **Compute geodesic distances**: Find shortest paths between all pairs of nodes in the graph using Floyd–Warshall or Dijkstra's algorithm, yielding matrix $D_G$ where $(D_G)_{ij}$ is the geodesic distance estimate.
3. **Apply classical MDS**: Find embedding $\mathbf{z}_i$ that minimizes $\sum_{i,j} (\| \mathbf{z}_i - \mathbf{z}_j \| - (D_G)_{ij})^2$.

## Properties

### MDS
- **Advantages**: Simple, closed-form solution (classical); works from any distance matrix.
- **Limitations**: Assumes Euclidean structure; fails on curved manifolds.

### Isomap
- **Advantages**: Captures non-linear manifold structure; globally optimal via eigen-decomposition.
- **Limitations**: Sensitive to neighborhood size $k$ — too small creates disconnected components, too large causes "short-circuit" errors; computationally expensive ($O(n^3)$ for Floyd–Warshall).

## Applications

- Visualization of high-dimensional data in 2D/3D
- Analysis of similarity matrices (e.g., psychological survey data)
- Manifold learning for face images, hand-written digits, and motion capture

## Related Concepts

- [[Principal Component Analysis (PCA)]] — linear counterpart; when using Euclidean distances, classical MDS and PCA produce equivalent results
- [[Clustering]] — embedding via MDS/Isomap can reveal cluster structure for visualization
- [[Deep Learning Architectures]] — autoencoders and UMAP are modern alternatives to classic manifold learning
