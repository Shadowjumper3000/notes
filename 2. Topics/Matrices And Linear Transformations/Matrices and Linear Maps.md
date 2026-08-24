# Matrices and Linear Maps

## Overview

A **matrix** is a rectangular array of numbers that represents a **linear map** (also called a linear transformation) between two vector spaces. If $T: V \to W$ is a linear map and bases are chosen for $V$ and $W$, then $T$ can be uniquely represented by a matrix $A$ such that for any vector $\mathbf{v} \in V$ (with coordinate representation $[\mathbf{v}]$), we have:

$$
[T(\mathbf{v})] = A [\mathbf{v}]
$$

This perspective unifies geometry and algebra: rotations, scalings, reflections, shears, and projections all become matrix multiplications.

## Matrix as a Linear Transformation

A map $T: V \to W$ is **linear** if for all $\mathbf{u}, \mathbf{v} \in V$ and $c \in \mathbb{F}$:

$$
T(\mathbf{u} + \mathbf{v}) = T(\mathbf{u}) + T(\mathbf{v})
$$
$$
T(c\mathbf{u}) = c T(\mathbf{u})
$$

Equivalently, $T(a\mathbf{u} + b\mathbf{v}) = aT(\mathbf{u}) + bT(\mathbf{v})$.

If $V = \mathbb{F}^n$, $W = \mathbb{F}^m$, and $A$ is an $m \times n$ matrix with entries $a_{ij}$, then:

$$
T(\mathbf{v}) = A\mathbf{v} = \begin{pmatrix}
a_{11} & a_{12} & \dots & a_{1n} \\
a_{21} & a_{22} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \dots & a_{mn}
\end{pmatrix}
\begin{pmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{pmatrix}
=
\begin{pmatrix}
\sum_{j=1}^n a_{1j} v_j \\
\sum_{j=1}^n a_{2j} v_j \\
\vdots \\
\sum_{j=1}^n a_{mj} v_j
\end{pmatrix}
$$

Each column of $A$ is the image of a standard basis vector: $A\mathbf{e}_j = \text{column } j$.

## Matrix Multiplication as Composition

If $T: V \to W$ is represented by $A$ ($m \times n$) and $S: W \to U$ is represented by $B$ ($p \times m$), then the composition $S \circ T: V \to U$ is represented by the matrix product $BA$ ($p \times n$):

$$
(S \circ T)(\mathbf{v}) = S(T(\mathbf{v})) = B(A\mathbf{v}) = (BA)\mathbf{v}
$$

The entry $(i, j)$ of the product $C = BA$ is:

$$
c_{ij} = \sum_{k=1}^m b_{ik} a_{kj}
$$

Matrix multiplication is associative: $(AB)C = A(BC)$, but not commutative: $AB \neq BA$ in general.

## The Four Fundamental Subspaces

For an $m \times n$ matrix $A$, there are four fundamental subspaces:

### 1. Column Space $C(A)$
The span of the columns of $A$, a subspace of $\mathbb{R}^m$:

$$
C(A) = \{ A\mathbf{x} \mid \mathbf{x} \in \mathbb{R}^n \} \subseteq \mathbb{R}^m
$$

$\dim(C(A)) = \operatorname{rank}(A)$. The equation $A\mathbf{x} = \mathbf{b}$ has a solution iff $\mathbf{b} \in C(A)$.

### 2. Nullspace (Kernel) $N(A)$
The set of all vectors mapped to zero:

$$
N(A) = \{ \mathbf{x} \in \mathbb{R}^n \mid A\mathbf{x} = \mathbf{0} \} \subseteq \mathbb{R}^n
$$

$\dim(N(A)) = \operatorname{nullity}(A)$.

### 3. Row Space $C(A^T)$
The span of the rows of $A$, a subspace of $\mathbb{R}^n$:

$$
C(A^T) = \{ A^T \mathbf{y} \mid \mathbf{y} \in \mathbb{R}^m \} \subseteq \mathbb{R}^n
$$

$\dim(C(A^T)) = \operatorname{rank}(A)$.

### 4. Left Nullspace $N(A^T)$
The set of vectors orthogonal to the columns:

$$
N(A^T) = \{ \mathbf{y} \in \mathbb{R}^m \mid A^T \mathbf{y} = \mathbf{0} \} \subseteq \mathbb{R}^m
$$

$\dim(N(A^T)) = m - \operatorname{rank}(A)$.

## Rank-Nullity Theorem

The **rank-nullity theorem** (also called the Fundamental Theorem of Linear Algebra) states:

$$
\dim(C(A)) + \dim(N(A)) = n
$$

or equivalently:

$$
\operatorname{rank}(A) + \operatorname{nullity}(A) = n
$$

For the transpose:

$$
\operatorname{rank}(A) + \dim(N(A^T)) = m
$$

A key corollary: $\operatorname{rank}(A) = \operatorname{rank}(A^T)$.

## Orthogonality of the Subspaces

The row space and nullspace are orthogonal complements in $\mathbb{R}^n$:

$$
C(A^T) \perp N(A), \quad C(A^T) \oplus N(A) = \mathbb{R}^n
$$

Similarly, the column space and left nullspace are orthogonal complements in $\mathbb{R}^m$:

$$
C(A) \perp N(A^T), \quad C(A) \oplus N(A^T) = \mathbb{R}^m
$$

This orthogonality is why solving $A\mathbf{x} = \mathbf{b}$ decomposes into finding a particular solution in $C(A^T)$ and a homogeneous solution in $N(A)$.

## Change of Basis

If a linear map $T: V \to V$ has matrix $A$ with respect to basis $B$, and we want its matrix $A'$ with respect to basis $B'$, the **change-of-basis formula** is:

$$
A' = P^{-1} A P
$$

where $P$ is the change-of-basis matrix whose columns are the coordinates of the old basis vectors in the new basis.

Two matrices $A$ and $A'$ related by $A' = P^{-1}AP$ are called **similar**. Similar matrices represent the same linear transformation in different bases.

## Matrix Representations of Linear Maps

Given $T: V \to W$ with $\dim(V) = n$, $\dim(W) = m$, basis $B_V = \{\mathbf{v}_1, \dots, \mathbf{v}_n\}$ for $V$, and basis $B_W = \{\mathbf{w}_1, \dots, \mathbf{w}_m\}$ for $W$, the matrix $A$ representing $T$ has entries defined by:

$$
T(\mathbf{v}_j) = \sum_{i=1}^m a_{ij} \mathbf{w}_i
$$

The $j$-th column of $A$ is $[T(\mathbf{v}_j)]_{B_W}$, the coordinates of $T(\mathbf{v}_j)$ in the basis $B_W$.

### Special Types of Matrices and Their Maps

| Matrix Property | Geometric Meaning |
|---|---|
| Orthogonal ($Q^T Q = I$) | Rotation or reflection (preserves lengths and angles) |
| Symmetric ($A = A^T$) | Self-adjoint map; real eigenvalues, orthogonal eigenvectors |
| Positive definite ($\mathbf{x}^T A \mathbf{x} > 0$) | Corresponds to an inner product |
| Projection ($P^2 = P$) | Projects onto a subspace along its complement |
| Nilpotent ($A^k = 0$) | Repeated application eventually gives zero |

## Applications

- **Neural Networks:** Each layer computes $\mathbf{h}_{l+1} = \sigma(W_l \mathbf{h}_l + \mathbf{b}_l)$ where $W_l$ is a weight matrix representing a learned linear map.
- **Computer Graphics:** A $4 \times 4$ transformation matrix can encode rotation, translation, scaling, and perspective projection in homogeneous coordinates.
- **Differential Equations:** Linear ODE systems $\frac{d\mathbf{x}}{dt} = A\mathbf{x}$ have solutions $\mathbf{x}(t) = e^{At}\mathbf{x}(0)$, where the matrix exponential is computed via eigen-decomposition.
- **Control Theory:** The state-space representation $\dot{\mathbf{x}} = A\mathbf{x} + B\mathbf{u}$, $\mathbf{y} = C\mathbf{x} + D\mathbf{u}$ uses matrices to model dynamical systems.

## Relationships to Other Notes

- [[Vectors and Vector Spaces]]: Matrices act on vectors; the four subspaces live in the domain and codomain.
- [[Eigenvalues and Eigenvectors]]: Diagonalization $A = PDP^{-1}$ decomposes a map into independent scaling along eigen-directions.
- [[Singular Value Decomposition]]: SVD $A = U\Sigma V^T$ generalizes diagonalization to any matrix and reveals the geometry of the linear map.

## References

- Strang, G. (2016). *Introduction to Linear Algebra*. Wellesley-Cambridge Press.
- Strang, G. (1993). "The Fundamental Theorem of Linear Algebra." *The American Mathematical Monthly*, 100(9), 848-855.
- Trefethen, L. N., & Bau III, D. (1997). *Numerical Linear Algebra*. SIAM.
