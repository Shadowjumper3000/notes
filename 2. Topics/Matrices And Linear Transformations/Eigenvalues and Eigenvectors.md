# Eigenvalues and Eigenvectors

## Overview
Eigenvalues and eigenvectors provide deep insights into the behavior of square matrices. An eigenvector is a non-zero vector that changes only by a scalar factor when that linear transformation is applied to it. This scalar factor is known as the eigenvalue. Geometrically, if a matrix $A$ represents a transformation, an eigenvector $x$ points in a direction that is preserved by $A$, and the eigenvalue $\lambda$ describes how much the vector is stretched or shrunk in that direction: $Ax = \lambda x$.

## Technical Depth
### The Characteristic Equation
To find the eigenvalues of a square matrix $A$, we solve the characteristic equation $\det(A - \lambda I) = 0$. This yields a polynomial in $\lambda$, known as the characteristic polynomial. The roots of this polynomial are the eigenvalues. For each eigenvalue $\lambda_i$, the corresponding eigenvectors are found by solving the homogeneous system $(A - \lambda_i I)x = 0$, which defines the **eigenspace** for that value.

### Diagonalization and the Spectral Theorem
If an $n \times n$ matrix $A$ has $n$ linearly independent eigenvectors, it is said to be **diagonalizable**. It can be decomposed as $A = PDP^{-1}$, where $D$ is a diagonal matrix of eigenvalues and $P$ is a matrix whose columns are the eigenvectors. This decomposition is incredibly useful for calculating high powers of a matrix ($A^k = PD^kP^{-1}$).

For symmetric matrices ($A = A^T$), the **Spectral Theorem** guarantees that all eigenvalues are real and that there exists an orthonormal basis of eigenvectors. In this case, $A = Q\Lambda Q^T$, where $Q$ is an orthogonal matrix ($Q^T = Q^{-1}$). This is the foundation for Principal Component Analysis (PCA).

## Applications
- **Principal Component Analysis (PCA):** PCA uses the eigenvectors of the data covariance matrix to find the directions of maximum variance, allowing for effective dimensionality reduction.
- **Google's PageRank:** The algorithm treats the web as a massive graph and finds the "importance" of pages by calculating the principal eigenvector of a probability transition matrix (the Google Matrix).
- **Stability Analysis:** In control theory and physics, the sign of the eigenvalues of a system's Jacobian matrix determines whether the system's equilibrium is stable or unstable.

## References
- Trefethen, L. N., & Bau III, D. (1997). *Numerical Linear Algebra*. SIAM.
- Page, L., Brin, S., Motwani, R., & Winograd, T. (1999). *The PageRank Citation Ranking: Bringing Order to the Web*. Stanford InfoLab.
