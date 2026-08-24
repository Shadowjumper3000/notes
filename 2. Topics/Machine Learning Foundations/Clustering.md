# Clustering

**Tags:** #topic #ml #clustering #unsupervised-learning

Clustering is a fundamental unsupervised learning task that partitions a dataset $\mathcal{D} = \{\mathbf{x}_1, \dots, \mathbf{x}_n\}$ into $K$ disjoint groups (clusters) $\mathcal{C}_1, \dots, \mathcal{C}_K$ such that points within the same cluster are more similar to each other than to points in other clusters. Clustering is used for exploratory data analysis, pattern discovery, and as a preprocessing step.

## Types of Clustering Algorithms

### Centroid-based (K-Means)

Minimizes the within-cluster sum of squares:

$$
\min_{\mathcal{C}_1,\dots,\mathcal{C}_K} \sum_{k=1}^K \sum_{\mathbf{x} \in \mathcal{C}_k} \|\mathbf{x} - \boldsymbol{\mu}_k\|^2
$$

where $\boldsymbol{\mu}_k = \frac{1}{|\mathcal{C}_k|} \sum_{\mathbf{x} \in \mathcal{C}_k} \mathbf{x}$ is the centroid.

**Algorithm (Lloyd's)**:
1. Initialize $K$ centroids $\boldsymbol{\mu}_1,\dots,\boldsymbol{\mu}_K$.
2. Assign each point to nearest centroid.
3. Recompute centroids.
4. Repeat steps 2–3 until convergence.

**Variants**: K-Means++ (smarter initialization), Mini-batch K-Means, Bisecting K-Means.

### Hierarchical Clustering

Builds a tree of clusters (dendrogram) either **agglomerative** (bottom-up: merge closest pairs) or **divisive** (top-down: recursively split). Linkage criteria define inter-cluster distance:

- **Single linkage**: $d_{\min}(\mathcal{C}_i, \mathcal{C}_j) = \min_{\mathbf{x} \in \mathcal{C}_i, \mathbf{y} \in \mathcal{C}_j} \|\mathbf{x} - \mathbf{y}\|$
- **Complete linkage**: $d_{\max}(\mathcal{C}_i, \mathcal{C}_j) = \max_{\mathbf{x} \in \mathcal{C}_i, \mathbf{y} \in \mathcal{C}_j} \|\mathbf{x} - \mathbf{y}\|$
- **Average linkage**: mean pairwise distance

### Density-based (DBSCAN)

Groups points that are densely packed, marking points in low-density regions as outliers. Parameters: $\epsilon$ (neighborhood radius) and minPts (density threshold).

- **Core point**: at least minPts points within radius $\epsilon$.
- **Border point**: reachable from a core point but not core itself.
- **Noise point**: not reachable from any core point.

Advantages: discovers arbitrary-shaped clusters, robust to outliers, no need to specify $K$.

### Spectral Clustering

Uses the eigenvalues of the graph Laplacian constructed from a similarity matrix $W$. The algorithm:

1. Build affinity matrix $W_{ij} = \exp(-\| \mathbf{x}_i - \mathbf{x}_j \|^2 / 2\sigma^2)$.
2. Compute normalized graph Laplacian $L = I - D^{-1/2} W D^{-1/2}$.
3. Extract the eigenvectors of the $K$ smallest eigenvalues.
4. Run K-Means on the rows of the eigenvector matrix.

## Evaluating Clusters

- **Inertia (within-cluster sum of squares)**: minimized by K-Means; decreases with $K$.
- **Silhouette score**: $\frac{b(i) - a(i)}{\max(a(i), b(i))}$ where $a$ is mean intra-cluster distance and $b$ is mean nearest-cluster distance.
- **Davies–Bouldin index**: ratio of within-cluster to between-cluster scatter.
- **Gap statistic**: compares observed inertia to that expected under a null reference distribution.

## Applications

- Customer segmentation in marketing
- Image segmentation (pixel clustering)
- Document topic discovery
- Anomaly detection (outliers are small or sparse clusters)
- Biological sequence clustering (e.g., gene expression)

## Related Concepts

- [[Principal Component Analysis (PCA)]] — often used to visualize clusters in 2D/3D
- [[MDS & Isomap]] — manifold-based dimensionality reduction can reveal cluster structure
- [[Decision Trees]] — can be used to produce interpretable cluster descriptions
