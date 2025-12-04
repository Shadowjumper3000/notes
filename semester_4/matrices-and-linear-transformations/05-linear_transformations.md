# Linear Transformations

## Introduction

A **linear transformation** $T: V \to W$ is a function between vector spaces that preserves vector addition and scalar multiplication.

### Definition

$T$ is linear if for all vectors $\mathbf{u}, \mathbf{v} \in V$ and scalar $c$:

1. **Additivity**: $T(\mathbf{u} + \mathbf{v}) = T(\mathbf{u}) + T(\mathbf{v})$
2. **Homogeneity**: $T(c\mathbf{u}) = cT(\mathbf{u})$

**Equivalent condition:**
$$
T(c_1\mathbf{u} + c_2\mathbf{v}) = c_1T(\mathbf{u}) + c_2T(\mathbf{v})
$$

---

## Matrix Representation

Every linear transformation $T: \mathbb{R}^n \to \mathbb{R}^m$ can be represented as:
$$
T(\mathbf{x}) = A\mathbf{x}
$$

where $A$ is an $m \times n$ matrix.

### Finding the Matrix

The columns of $A$ are the images of the standard basis vectors:
$$
A = [T(\mathbf{e}_1) \quad T(\mathbf{e}_2) \quad \cdots \quad T(\mathbf{e}_n)]
$$

---

## Common Transformations in 2D

### Rotation

Rotate by angle $\theta$ counterclockwise:
$$
R_\theta = \begin{bmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{bmatrix}
$$

### Reflection

**Across x-axis:**
$$
\begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
$$

**Across y-axis:**
$$
\begin{bmatrix} -1 & 0 \\ 0 & 1 \end{bmatrix}
$$

**Across line $y = x$:**
$$
\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
$$

### Scaling

Scale by factor $s_x$ in x-direction, $s_y$ in y-direction:
$$
\begin{bmatrix} s_x & 0 \\ 0 & s_y \end{bmatrix}
$$

### Shear

**Horizontal shear:**
$$
\begin{bmatrix} 1 & k \\ 0 & 1 \end{bmatrix}
$$

**Vertical shear:**
$$
\begin{bmatrix} 1 & 0 \\ k & 1 \end{bmatrix}
$$

### Projection

**Onto x-axis:**
$$
\begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}
$$

**Onto y-axis:**
$$
\begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix}
$$

---

## Properties of Linear Transformations

### Kernel (Null Space)

$$
\ker(T) = \{\mathbf{v} \in V : T(\mathbf{v}) = \mathbf{0}\}
$$

**Properties:**
- Subspace of $V$
- $T$ is injective (one-to-one) iff $\ker(T) = \{\mathbf{0}\}$

### Image (Range)

$$
\text{Im}(T) = \{T(\mathbf{v}) : \mathbf{v} \in V\}
$$

**Properties:**
- Subspace of $W$
- $T$ is surjective (onto) iff $\text{Im}(T) = W$

---

## Rank-Nullity Theorem

For $T: V \to W$:
$$
\dim(\ker(T)) + \dim(\text{Im}(T)) = \dim(V)
$$

Also written as:
$$
\text{nullity}(T) + \text{rank}(T) = n
$$

---

## Composition of Transformations

If $T: U \to V$ and $S: V \to W$, the composition is:
$$
(S \circ T)(\mathbf{u}) = S(T(\mathbf{u}))
$$

**Matrix representation:**
$$
[S \circ T] = [S][T]
$$

**Note:** Matrix multiplication is NOT commutative: $AB \neq BA$ in general.

---

## Inverse Transformations

$T: V \to W$ is **invertible** if there exists $T^{-1}: W \to V$ such that:
$$
T^{-1}(T(\mathbf{v})) = \mathbf{v} \quad \text{and} \quad T(T^{-1}(\mathbf{w})) = \mathbf{w}
$$

**Matrix form:** $T$ is invertible iff its matrix $A$ is invertible.

**Conditions for invertibility:**
- $T$ is both injective and surjective (bijective)
- $\det(A) \neq 0$
- Columns of $A$ are linearly independent
- $\text{rank}(A) = n$

---

## Change of Basis

### Coordinate Vectors

Given basis $\mathcal{B} = \{\mathbf{b}_1, \ldots, \mathbf{b}_n\}$, if:
$$
\mathbf{v} = c_1\mathbf{b}_1 + \cdots + c_n\mathbf{b}_n
$$

then the **coordinate vector** is:
$$
[\mathbf{v}]_{\mathcal{B}} = \begin{bmatrix} c_1 \\ \vdots \\ c_n \end{bmatrix}
$$

### Change of Basis Matrix

To convert from basis $\mathcal{B}$ to basis $\mathcal{C}$:
$$
[\mathbf{v}]_{\mathcal{C}} = P_{\mathcal{B} \to \mathcal{C}} [\mathbf{v}]_{\mathcal{B}}
$$

where $P_{\mathcal{B} \to \mathcal{C}}$ has columns $[{\mathbf{b}_i}]_{\mathcal{C}}$.

---

## Eigenvalues and Eigenvectors

### Definition

$\lambda$ is an **eigenvalue** and $\mathbf{v} \neq \mathbf{0}$ is an **eigenvector** of $A$ if:
$$
A\mathbf{v} = \lambda\mathbf{v}
$$

**Geometric interpretation:** $\mathbf{v}$ is only scaled (not rotated) by $A$.

### Characteristic Equation

$$
\det(A - \lambda I) = 0
$$

This is a polynomial equation in $\lambda$ called the **characteristic polynomial**.

### Finding Eigenvectors

For each eigenvalue $\lambda$:
1. Solve $(A - \lambda I)\mathbf{v} = \mathbf{0}$
2. Solutions form the **eigenspace** for $\lambda$

---

## Diagonalization

A matrix $A$ is **diagonalizable** if:
$$
A = PDP^{-1}
$$

where $D$ is diagonal and $P$ has eigenvectors as columns.

**Diagonal entries of $D$:** Eigenvalues of $A$.

**Conditions for diagonalizability:**
- $A$ has $n$ linearly independent eigenvectors
- For each eigenvalue, geometric multiplicity = algebraic multiplicity

### Benefits

- Easy to compute powers: $A^k = PD^kP^{-1}$
- Solve differential equations and recurrence relations
- Analyze long-term behavior of systems

---

## Orthogonal Diagonalization

A **symmetric matrix** $A$ (where $A^T = A$) can be orthogonally diagonalized:
$$
A = QDQ^T
$$

where $Q$ is orthogonal ($Q^T = Q^{-1}$) and $D$ is diagonal.

**Spectral Theorem:** Every symmetric matrix has:
- Real eigenvalues
- Orthogonal eigenvectors

---

## Singular Value Decomposition (SVD)

For any $m \times n$ matrix $A$:
$$
A = U\Sigma V^T
$$

where:
- $U$: $m \times m$ orthogonal matrix (left singular vectors)
- $\Sigma$: $m \times n$ diagonal matrix (singular values)
- $V$: $n \times n$ orthogonal matrix (right singular vectors)

**Singular values:** $\sigma_1 \geq \sigma_2 \geq \cdots \geq 0$

### Applications

- **Image compression:** Low-rank approximation
- **Principal Component Analysis (PCA):** Dimensionality reduction
- **Least squares:** Pseudoinverse computation
- **Recommendation systems:** Matrix factorization

---

## Jordan Normal Form

For matrices that aren't diagonalizable, there exists a **Jordan normal form**:
$$
A = PJP^{-1}
$$

where $J$ consists of **Jordan blocks**:
$$
J_k(\lambda) = \begin{bmatrix}
\lambda & 1 & 0 & \cdots & 0 \\
0 & \lambda & 1 & \cdots & 0 \\
\vdots & \vdots & \ddots & \ddots & \vdots \\
0 & 0 & 0 & \lambda & 1 \\
0 & 0 & 0 & 0 & \lambda
\end{bmatrix}
$$

---

## Applications of Linear Transformations

### Computer Graphics

- **3D transformations:** Rotation, translation, scaling
- **Perspective projection:** 3D to 2D rendering
- **Animation:** Interpolation between transformations

### Data Science

- **PCA:** Find principal components via eigenvectors
- **Linear regression:** Least squares as projection
- **Neural networks:** Layers as linear transformations + activations

### Differential Equations

- **System of ODEs:** $\frac{d\mathbf{x}}{dt} = A\mathbf{x}$
- **Solution:** $\mathbf{x}(t) = e^{At}\mathbf{x}_0$ (using diagonalization)

### Quantum Mechanics

- **State transformations:** Unitary matrices
- **Observables:** Hermitian matrices
- **Measurement:** Eigenvalues and eigenstates

### Engineering

- **Control systems:** State-space representation
- **Signal processing:** Fourier transform as linear operator
- **Structural analysis:** Stiffness matrices

---

## Summary

- Linear transformations preserve vector operations
- Can be represented as matrices
- Common transformations: rotation, reflection, scaling, shear, projection
- Kernel and image characterize injectivity and surjectivity
- Eigenvalues and eigenvectors reveal intrinsic properties
- Diagonalization simplifies computations
- SVD provides optimal low-rank approximations
- Applications span mathematics, computer science, and engineering
