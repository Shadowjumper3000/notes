# Singular Value Decomposition (SVD)

## Overview

The Singular Value Decomposition (SVD) is a factorization of any $m \times n$ matrix $A$ into three components:

$$
A = U \Sigma V^T
$$

where:
- $U \in \mathbb{R}^{m \times m}$ is orthogonal ($U^T U = I$) — the **left singular vectors**
- $\Sigma \in \mathbb{R}^{m \times n}$ is diagonal with non-negative entries — the **singular values**
- $V \in \mathbb{R}^{n \times n}$ is orthogonal ($V^T V = I$) — the **right singular vectors**

SVD exists for every matrix (real or complex). Unlike eigendecomposition, which requires a square diagonalizable matrix, SVD is universal. It reveals the intrinsic geometry of any linear transformation.

## Full Derivation

### Connection to Eigendecomposition

The SVD is intimately related to the eigendecompositions of $A^T A$ and $A A^T$.

**Right singular vectors** are eigenvectors of $A^T A$:

$$
A^T A = V \Sigma^T \Sigma V^T = V \begin{pmatrix}
\sigma_1^2 & & \\
& \ddots & \\
& & \sigma_r^2 \\
& & & 0
\end{pmatrix} V^T
$$

**Left singular vectors** are eigenvectors of $A A^T$:

$$
A A^T = U \Sigma \Sigma^T U^T = U \begin{pmatrix}
\sigma_1^2 & & \\
& \ddots & \\
& & \sigma_r^2 \\
& & & 0
\end{pmatrix} U^T
$$

### Derivation Steps

1. Compute the eigenvalues and eigenvectors of $A^T A$ (an $n \times n$ symmetric positive semi-definite matrix). The eigenvalues are $\sigma_i^2$ and the eigenvectors form the columns of $V$.

2. The singular values are $\sigma_i = \sqrt{\lambda_i} \ge 0$, sorted in descending order: $\sigma_1 \ge \sigma_2 \ge \dots \ge \sigma_r > 0$, where $r = \operatorname{rank}(A)$.

3. Compute $U$ via: for $i = 1, \dots, r$:

$$
\mathbf{u}_i = \frac{1}{\sigma_i} A \mathbf{v}_i
$$

Extend $\{\mathbf{u}_1, \dots, \mathbf{u}_r\}$ to an orthonormal basis of $\mathbb{R}^m$ to complete $U$.

Alternatively, compute $U$ directly from the eigendecomposition of $A A^T$.

## Reduced vs Full SVD

### Full SVD

$$
A = \begin{pmatrix}
\mathbf{u}_1 & \dots & \mathbf{u}_m
\end{pmatrix}
\begin{pmatrix}
\sigma_1 & 0 & \dots & 0 \\
0 & \ddots & \ddots & \vdots \\
\vdots & \ddots & \sigma_r & \vdots \\
\vdots & \ddots & \ddots & 0 \\
0 & \dots & \dots & 0
\end{pmatrix}_{m \times n}
\begin{pmatrix}
\mathbf{v}_1^T \\
\vdots \\
\mathbf{v}_n^T
\end{pmatrix}
$$

### Reduced (Economy) SVD

If $m > n$, only the first $n$ columns of $U$ are needed:

$$
A = U_n \Sigma_n V^T
$$

where $U_n \in \mathbb{R}^{m \times n}$, $\Sigma_n \in \mathbb{R}^{n \times n}$.

### Compact SVD

Keep only the $r = \operatorname{rank}(A)$ non-zero singular values:

$$
A = U_r \Sigma_r V_r^T
$$

where $U_r \in \mathbb{R}^{m \times r}$, $\Sigma_r \in \mathbb{R}^{r \times r}$, $V_r \in \mathbb{R}^{n \times r}$.

## Geometric Interpretation

The SVD decomposes a linear transformation $A: \mathbb{R}^n \to \mathbb{R}^m$ into three sequential operations:

1. **Rotation/reflection in input space:** $V^T$ (orthogonal)
2. **Scaling:** $\Sigma$ (stretching/shrinking along coordinate axes)
3. **Rotation/reflection in output space:** $U$ (orthogonal)

The unit sphere in $\mathbb{R}^n$ is mapped to an ellipsoid in $\mathbb{R}^m$ whose semi-axis lengths are the singular values $\sigma_i$.

## Low-Rank Approximation (Eckart-Young Theorem)

The **Eckart-Young-Mirsky theorem** states that the best rank-$k$ approximation to $A$ in both the Frobenius norm and the spectral norm is given by truncating the SVD:

$$
A_k = \sum_{i=1}^k \sigma_i \mathbf{u}_i \mathbf{v}_i^T = U_k \Sigma_k V_k^T
$$

For the Frobenius norm $\|A\|_F = \sqrt{\sum_{i,j} a_{ij}^2} = \sqrt{\sum_{i=1}^r \sigma_i^2}$:

$$
\|A - A_k\|_F = \sqrt{\sum_{i=k+1}^r \sigma_i^2}
$$

For the spectral norm $\|A\|_2 = \sigma_1$:

$$
\|A - A_k\|_2 = \sigma_{k+1}
$$

This is the mathematical foundation for lossy compression: discarding small singular values removes "noise" while preserving the essential structure.

## The Moore-Penrose Pseudoinverse

For any matrix $A$, the **pseudoinverse** $A^+$ is defined via the SVD:

$$
A = U \Sigma V^T \implies A^+ = V \Sigma^+ U^T
$$

where $\Sigma^+$ is obtained by transposing $\Sigma$ and inverting the non-zero singular values:

$$
\Sigma^+ = \operatorname{diag}\left(\frac{1}{\sigma_1}, \dots, \frac{1}{\sigma_r}, 0, \dots, 0\right)^T
$$

The pseudoinverse gives the minimum-norm least-squares solution to $A\mathbf{x} = \mathbf{b}$:

$$
\mathbf{x}^* = A^+ \mathbf{b}
$$

## Relationship to Eigendecomposition

For symmetric matrices, SVD and eigendecomposition coincide up to sign:

| Matrix Type | Eigendecomposition | SVD |
|---|---|---|
| Symmetric PD ($A = A^T \succ 0$) | $A = Q\Lambda Q^T$ | $A = U\Sigma V^T$ with $U=V=Q$, $\Sigma = \Lambda$ |
| Symmetric ($A = A^T$) | $A = Q\Lambda Q^T$ | $U = Q$, $V = Q$ (up to sign), $\sigma_i = |\lambda_i|$ |
| General square | $A = PDP^{-1}$ (if diagonalizable) | $A = U\Sigma V^T$ always exists |

SVD always exists, is always real (for real matrices), and reveals the rank explicitly through the number of non-zero singular values.

## Applications

### Principal Component Analysis (PCA)

Given centered data $X \in \mathbb{R}^{m \times n}$, the SVD of $X = U\Sigma V^T$ gives:
- Principal components = columns of $V$
- Variance along PC $i \propto \sigma_i^2$
- Projected data = $XV = U\Sigma$

This is numerically more stable than computing $X^T X$ directly.

### Image Compression

An $m \times n$ grayscale image has SVD $A = U\Sigma V^T$. Storing $A$ requires $mn$ values. Storing the rank-$k$ approximation requires $k(m + n + 1)$ values. For $k \ll \min(m,n)$, this is a significant compression.

### Recommendation Systems

In collaborative filtering, the user-item rating matrix $R$ is factorized via SVD (or truncated SVD for implicit feedback). Missing ratings are predicted by:

$$
\hat{r}_{ui} = (\mathbf{u}_u)^T \Sigma_k \mathbf{v}_i
$$

where $\mathbf{u}_u$ and $\mathbf{v}_i$ are the user and item latent factor vectors.

### Latent Semantic Analysis (LSA)

In NLP, a term-document matrix $A \in \mathbb{R}^{t \times d}$ (with TF-IDF weighting) is decomposed via SVD:

$$
A_k = U_k \Sigma_k V_k^T
$$

The rows of $U_k \Sigma_k$ give term embeddings; the rows of $V_k$ give document embeddings. This captures latent semantic concepts.

### Solving Linear Systems

For ill-conditioned or rank-deficient systems $A\mathbf{x} \approx \mathbf{b}$, the SVD-based solution $\mathbf{x} = V \Sigma^+ U^T \mathbf{b}$ is numerically stable. Truncating small singular values (truncated SVD) acts as regularization.

## Relationships to Other Notes

- [[Vectors and Vector Spaces]]: SVD finds orthonormal bases for all four fundamental subspaces.
- [[Matrices and Linear Maps]]: SVD reveals the geometric action of a linear map as rotation-scaling-rotation.
- [[Eigenvalues and Eigenvectors]]: SVD generalizes eigendecomposition to any matrix; singular values are square roots of eigenvalues of $A^T A$.

## References

- Golub, G. H., & Van Loan, C. F. (2013). *Matrix Computations*. Johns Hopkins University Press.
- Trefethen, L. N., & Bau III, D. (1997). *Numerical Linear Algebra*. SIAM.
- Eckart, C., & Young, G. (1936). "The approximation of one matrix by another of lower rank." *Psychometrika*, 1(3), 211-218.
