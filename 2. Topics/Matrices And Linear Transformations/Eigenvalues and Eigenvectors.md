# Eigenvalues and Eigenvectors

## Overview

Eigenvalues and eigenvectors reveal the intrinsic structure of a linear transformation. For a square matrix $A \in \mathbb{F}^{n \times n}$, a non-zero vector $\mathbf{v} \in \mathbb{F}^n$ is an **eigenvector** if applying $A$ only scales it:

$$
A \mathbf{v} = \lambda \mathbf{v}
$$

where $\lambda \in \mathbb{F}$ is the corresponding **eigenvalue**. Geometrically, eigenvectors are directions that are preserved (not rotated) by the transformation; they are only stretched, compressed, or reversed.

## Characteristic Polynomial

To find eigenvalues, re-arrange the defining equation:

$$
A \mathbf{v} = \lambda \mathbf{v} \implies A \mathbf{v} - \lambda I \mathbf{v} = \mathbf{0} \implies (A - \lambda I) \mathbf{v} = \mathbf{0}
$$

For non-zero $\mathbf{v}$ to exist, the matrix $A - \lambda I$ must be singular:

$$
\det(A - \lambda I) = 0
$$

This is the **characteristic equation**. The **characteristic polynomial** is:

$$
p_A(\lambda) = \det(\lambda I - A) = \lambda^n - (\operatorname{tr} A) \lambda^{n-1} + \dots + (-1)^n \det A
$$

For an $n \times n$ matrix, $p_A(\lambda)$ is a degree-$n$ polynomial. By the Fundamental Theorem of Algebra, it has exactly $n$ roots (counting multiplicity) over $\mathbb{C}$.

### Properties of the Characteristic Polynomial

- $\det(A) = \prod_{i=1}^n \lambda_i$ (product of eigenvalues)
- $\operatorname{tr}(A) = \sum_{i=1}^n \lambda_i$ (sum of eigenvalues, including multiplicities)
- $A$ and $A^T$ have the same characteristic polynomial (hence same eigenvalues)
- If $A$ is triangular, the eigenvalues are the diagonal entries

## Eigenspaces and Multiplicity

For each eigenvalue $\lambda_i$, the **eigenspace** is:

$$
E_{\lambda_i} = N(A - \lambda_i I) = \{ \mathbf{v} \in \mathbb{F}^n \mid (A - \lambda_i I) \mathbf{v} = \mathbf{0} \}
$$

- **Algebraic multiplicity** $m_i$: the multiplicity of $\lambda_i$ as a root of $p_A(\lambda)$.
- **Geometric multiplicity** $g_i$: $\dim(E_{\lambda_i}) = n - \operatorname{rank}(A - \lambda_i I)$.

We always have $1 \le g_i \le m_i$. When $g_i < m_i$, the eigenvalue is **defective**, and $A$ is not diagonalizable.

## Diagonalization

An $n \times n$ matrix $A$ is **diagonalizable** if it has $n$ linearly independent eigenvectors. Equivalently, $g_i = m_i$ for every eigenvalue.

If $A$ is diagonalizable, we can write:

$$
A = PDP^{-1}
$$

where:
- $P$ has the eigenvectors $\mathbf{v}_1, \dots, \mathbf{v}_n$ as columns
- $D = \operatorname{diag}(\lambda_1, \dots, \lambda_n)$ has the corresponding eigenvalues on the diagonal

### Power of Diagonalization

Diagonalization dramatically simplifies matrix powers:

$$
A^k = (PDP^{-1})^k = PD^k P^{-1} = P \operatorname{diag}(\lambda_1^k, \dots, \lambda_n^k) P^{-1}
$$

More generally, for any analytic function $f$:

$$
f(A) = P f(D) P^{-1} = P \operatorname{diag}(f(\lambda_1), \dots, f(\lambda_n)) P^{-1}
$$

This is used for the matrix exponential $e^{A}$ in solving systems of ODEs:

$$
\frac{d\mathbf{x}}{dt} = A \mathbf{x} \implies \mathbf{x}(t) = e^{At} \mathbf{x}(0)
$$

## Spectral Theorem

The **Spectral Theorem** is one of the most important results in linear algebra.

### Real Symmetric Matrices

If $A \in \mathbb{R}^{n \times n}$ is symmetric ($A = A^T$), then:
1. All eigenvalues are real.
2. There exists an orthonormal basis of eigenvectors.
3. $A$ is orthogonally diagonalizable: $A = Q \Lambda Q^T$, where $Q$ is orthogonal ($Q^T Q = I$).

### Normal Matrices

More generally, a matrix $A \in \mathbb{C}^{n \times n}$ is **normal** if $AA^* = A^*A$ (where $A^* = \overline{A}^T$). The Spectral Theorem for normal matrices states that $A$ is unitarily diagonalizable:

$$
A = U \Lambda U^*
$$

where $U$ is unitary ($U^* U = I$). This class includes:
- Hermitian matrices ($A = A^*$, real eigenvalues)
- Unitary matrices ($A^* A = I$, eigenvalues on the unit circle)
- Skew-Hermitian matrices ($A = -A^*$, purely imaginary eigenvalues)

## Rayleigh Quotient

For a Hermitian matrix $A$, the **Rayleigh quotient**:

$$
R(\mathbf{x}) = \frac{\mathbf{x}^* A \mathbf{x}}{\mathbf{x}^* \mathbf{x}}
$$

attains its minimum and maximum at the smallest and largest eigenvalues:

$$
\lambda_{\min} = \min_{\mathbf{x} \neq \mathbf{0}} R(\mathbf{x}), \quad \lambda_{\max} = \max_{\mathbf{x} \neq \mathbf{0}} R(\mathbf{x})
$$

More generally, by the Courant-Fischer min-max theorem:

$$
\lambda_k = \min_{\dim(S) = n-k+1} \max_{\mathbf{x} \in S \setminus \{\mathbf{0}\}} R(\mathbf{x})
$$

## Applications

### Principal Component Analysis (PCA)

Given data matrix $X \in \mathbb{R}^{m \times n}$ (rows = samples, columns = features), the covariance matrix is:

$$
\Sigma = \frac{1}{m-1} X^T X
$$

PCA finds the eigenvectors of $\Sigma$ (principal components). The eigenvalue $\lambda_i$ equals the variance along the $i$-th principal component. Projecting onto the top $k$ eigenvectors gives dimensionality reduction.

### PageRank

Google's PageRank algorithm models the web as a directed graph with adjacency matrix $M$. The "importance" vector $\mathbf{r}$ satisfies:

$$
\mathbf{r} = \alpha M \mathbf{r} + (1-\alpha) \frac{1}{n} \mathbf{1}
$$

This is solved as an eigenvector problem: $\mathbf{r}$ is the principal eigenvector of the Google matrix $G = \alpha M + (1-\alpha) \frac{1}{n} \mathbf{1}\mathbf{1}^T$.

### Stability of Dynamical Systems

For a linear system $\dot{\mathbf{x}} = A\mathbf{x}$, the solution is $\mathbf{x}(t) = e^{At} \mathbf{x}(0)$. The system is stable iff all eigenvalues of $A$ have negative real parts ($\operatorname{Re}(\lambda_i) < 0$).

### Spectral Graph Theory

The eigenvalues of the graph Laplacian $L = D - A$ (where $D$ is the degree matrix and $A$ the adjacency) encode structural properties: the number of zero eigenvalues equals the number of connected components, and the second smallest eigenvalue (the Fiedler value) measures graph connectivity.

## Relationships to Other Notes

- [[Vectors and Vector Spaces]]: Eigenvectors live in the vector space; they form a basis if the matrix is diagonalizable.
- [[Matrices and Linear Maps]]: Diagonalization decomposes a linear map into independent scaling along eigen-directions.
- [[Singular Value Decomposition]]: SVD generalizes eigendecomposition to non-square matrices. For symmetric positive-definite matrices, SVD equals eigendecomposition.

## References

- Trefethen, L. N., & Bau III, D. (1997). *Numerical Linear Algebra*. SIAM.
- Strang, G. (2016). *Introduction to Linear Algebra*. Wellesley-Cambridge Press.
- Page, L., Brin, S., Motwani, R., & Winograd, T. (1999). "The PageRank Citation Ranking: Bringing Order to the Web." Stanford InfoLab.
