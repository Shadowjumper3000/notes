# Principal Component Analysis (PCA)

**Tags:** #topic #ml #pca #dimensionality-reduction

Principal Component Analysis (PCA) is a linear dimensionality reduction technique that finds a sequence of orthogonal directions, called **principal components**, that maximize the variance of the projected data. It is widely used for visualization, noise reduction, feature extraction, and as a preprocessing step.

## Mathematical Formulation

Let $\mathbf{X} \in \mathbb{R}^{n \times p}$ be the data matrix with $n$ observations and $p$ features, centered so that $\sum_i \mathbf{x}_i = \mathbf{0}$.

### Variance Maximization

The first principal component $\mathbf{w}_1$ (a unit vector) solves:

$$
\mathbf{w}_1 = \arg\max_{\|\mathbf{w}\|=1} \|\mathbf{X}\mathbf{w}\|^2 = \arg\max_{\|\mathbf{w}\|=1} \mathbf{w}^\top \mathbf{X}^\top \mathbf{X} \,\mathbf{w}
$$

Subsequent components $\mathbf{w}_k$ maximize variance subject to orthogonality: $\mathbf{w}_k \perp \mathbf{w}_1, \dots, \mathbf{w}_{k-1}$.

### Eigendecomposition

The solution is given by the eigendecomposition of the sample covariance matrix:

$$
\mathbf{S} = \frac{1}{n-1} \mathbf{X}^\top \mathbf{X}
$$

The principal component directions $\mathbf{w}_k$ are the eigenvectors of $\mathbf{S}$, and the corresponding eigenvalues $\lambda_k$ equal the variance along each component. The projection of a data point $\mathbf{x}$ onto the first $d$ components is:

$$
\mathbf{z} = \mathbf{W}_d^\top \mathbf{x}, \quad \mathbf{W}_d = [\mathbf{w}_1, \dots, \mathbf{w}_d]
$$

### Singular Value Decomposition (SVD)

PCA can be computed efficiently via the SVD of $\mathbf{X}$:

$$
\mathbf{X} = \mathbf{U} \boldsymbol{\Sigma} \mathbf{V}^\top
$$

where $\mathbf{V}$ contains the eigenvectors (principal component directions), $\boldsymbol{\Sigma}$ has singular values $\sigma_k = \sqrt{\lambda_k (n-1)}$, and $\mathbf{U} \boldsymbol{\Sigma}$ gives the principal component scores.

## Choosing the Number of Components

- **Explained variance ratio**: $\frac{\sum_{k=1}^d \lambda_k}{\sum_{k=1}^p \lambda_k}$ — select enough components to capture, e.g., 95% of variance.
- **Scree plot**: Elbow in the eigenvalue plot.
- **Kaiser rule**: Keep components with $\lambda_k > \bar{\lambda}$.

## Properties

- **Linearity**: PCA only captures linear structure; fails on curved manifolds.
- **Orthogonality**: Components are mutually orthogonal.
- **Optimal reconstruction**: Among all $d$-dimensional linear projections, PCA minimizes reconstruction error $\|\mathbf{X} - \mathbf{X} \mathbf{W}_d \mathbf{W}_d^\top\|^2_F$.
- **Sensitivity to scaling**: Variables should be standardized (z-scored) when measured on different scales.

## Applications

- Exploratory data analysis and 2D/3D visualization
- Noise reduction (drop components with small eigenvalues)
- Preprocessing for [[Decision Trees]], [[Clustering]], and regression models
- Face recognition (eigenfaces)
- Compression and whitening

## Related Concepts

- [[MDS & Isomap]] — classical MDS is equivalent to PCA when applying it to Euclidean distances; Isomap extends this to geodesic distances
- [[Clustering]] — PCA is often used to visualize clusters in reduced dimensions
- [[Deep Learning Architectures]] — autoencoders provide non-linear generalizations of PCA
- [[Losses & Regularization]] — PCA can be seen as minimizing MSE reconstruction loss
