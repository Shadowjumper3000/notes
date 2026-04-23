# Singular Value Decomposition (SVD)

## Overview
Singular Value Decomposition (SVD) is arguably the most powerful and versatile tool in linear algebra. Unlike diagonalization, which only applies to square matrices, SVD can be applied to any $m \times n$ matrix. It factorizes a matrix $A$ into three distinct components: $A = U\Sigma V^T$. This decomposition reveals the underlying geometric structure of the linear transformation, breaking it down into a rotation, a scaling, and another rotation.

## Technical Depth
### Mathematical Components
For an $m \times n$ matrix $A$:
- **$U$ ($m \times m$):** An orthogonal matrix whose columns are the **left-singular vectors**. These are the eigenvectors of $AA^T$ and provide a basis for the output space.
- **$\Sigma$ ($m \times n$):** A diagonal matrix containing the **singular values** $\sigma_1 \ge \sigma_2 \ge \dots \ge 0$. These values represent the "strength" or "energy" along each singular direction and are the square roots of the eigenvalues of $A^TA$ or $AA^T$.
- **$V$ ($n \times n$):** An orthogonal matrix whose columns are the **right-singular vectors**. These are the eigenvectors of $A^TA$ and provide a basis for the input space.

### Low-Rank Approximation
The Eckart-Young-Mirsky theorem states that the best rank-$k$ approximation of a matrix $A$ (in terms of the Frobenius norm) is obtained by keeping only the $k$ largest singular values and their corresponding vectors: $A_k = \sum_{i=1}^k \sigma_i u_i v_i^T$. This is the basis for data compression and noise reduction techniques, as it allows us to discard "noise" represented by small singular values.

## Applications
- **Image Compression:** By performing SVD on an image (represented as a matrix of pixels) and retaining only the top $k$ singular values, one can significantly reduce file size while maintaining the essential visual structure.
- **Latent Semantic Analysis (LSA):** In NLP, SVD is applied to a term-document matrix to uncover latent concepts and relationships between words, effectively reducing the "synonymy" and "polysemy" problems.
- **Recommendation Systems:** SVD is used in collaborative filtering (e.g., the Netflix Prize) to decompose user-item rating matrices and predict missing ratings based on latent factors.

## References
- Golub, G. H., & Van Loan, C. F. (2013). *Matrix Computations*. Johns Hopkins University Press.
- Klema, V., & Laub, A. (1980). *The singular value decomposition: Its computation and some applications*. IEEE Transactions on Automatic Control.
