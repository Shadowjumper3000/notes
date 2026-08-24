# Vectors and Vector Spaces

## Overview

A **vector space** (or linear space) is a fundamental algebraic structure in linear algebra. It consists of a set $V$ of vectors, a field $\mathbb{F}$ of scalars (typically $\mathbb{R}$ or $\mathbb{C}$), and two operations: vector addition and scalar multiplication. These operations must satisfy eight axioms: associativity and commutativity of addition, existence of an additive identity $\mathbf{0}$, existence of additive inverses, and four distributive/associative properties for scalar multiplication.

Formally, for all $\mathbf{u}, \mathbf{v}, \mathbf{w} \in V$ and $a, b \in \mathbb{F}$:

$$
\mathbf{u} + (\mathbf{v} + \mathbf{w}) = (\mathbf{u} + \mathbf{v}) + \mathbf{w}
$$
$$
\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}
$$
$$
\exists \mathbf{0} \in V \text{ such that } \mathbf{v} + \mathbf{0} = \mathbf{v}
$$
$$
\forall \mathbf{v} \in V, \exists (-\mathbf{v}) \in V \text{ such that } \mathbf{v} + (-\mathbf{v}) = \mathbf{0}
$$
$$
a(b\mathbf{v}) = (ab)\mathbf{v}
$$
$$
1\mathbf{v} = \mathbf{v}
$$
$$
a(\mathbf{u} + \mathbf{v}) = a\mathbf{u} + a\mathbf{v}
$$
$$
(a + b)\mathbf{v} = a\mathbf{v} + b\mathbf{v}
$$

The prototypical example is $\mathbb{R}^n$, the set of all $n$-tuples of real numbers:

$$
\mathbb{R}^n = \{(x_1, x_2, \dots, x_n) \mid x_i \in \mathbb{R}\}
$$

with component-wise addition and scalar multiplication.

## Linear Independence

A set of vectors $\{\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_k\} \subset V$ is **linearly independent** if the only solution to the equation

$$
c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \dots + c_k\mathbf{v}_k = \mathbf{0}
$$

is the trivial solution $c_1 = c_2 = \dots = c_k = 0$ (where $c_i \in \mathbb{F}$). If a non-trivial solution exists, the set is **linearly dependent**.

Equivalently, a set is linearly dependent iff at least one vector can be expressed as a linear combination of the others.

## Span and Basis

The **span** of a set $S = \{\mathbf{v}_1, \dots, \mathbf{v}_k\}$ is the set of all finite linear combinations:

$$
\operatorname{span}(S) = \left\{ \sum_{i=1}^k c_i \mathbf{v}_i \;\Big|\; c_i \in \mathbb{F} \right\}
$$

A **basis** of a vector space $V$ is a set $B \subset V$ that is both:
- **Linearly independent**, and
- **Spanning** (i.e., $\operatorname{span}(B) = V$).

Every vector $\mathbf{v} \in V$ can be expressed uniquely as a linear combination of basis vectors. If $B = \{\mathbf{b}_1, \dots, \mathbf{b}_n\}$ is a basis, then:

$$
\mathbf{v} = \sum_{i=1}^n \alpha_i \mathbf{b}_i
$$

where the scalars $\alpha_i$ are the **coordinates** of $\mathbf{v}$ with respect to $B$.

## Dimension

The **dimension** of a vector space $V$, denoted $\dim(V)$, is the cardinality of any basis. All bases of a finite-dimensional vector space have the same number of elements. For example:

$$
\dim(\mathbb{R}^n) = n, \quad \dim(\mathbb{C}^n) = n, \quad \dim(\mathbb{F}^{m \times n}) = mn
$$

The dimension of the trivial space $\{\mathbf{0}\}$ is $0$.

A key relationship: if $U$ is a subspace of $V$, then $\dim(U) \le \dim(V)$, with equality iff $U = V$.

## Inner Products

An **inner product** is a function $\langle \cdot, \cdot \rangle : V \times V \to \mathbb{F}$ satisfying:

1. **Conjugate symmetry:** $\langle \mathbf{u}, \mathbf{v} \rangle = \overline{\langle \mathbf{v}, \mathbf{u} \rangle}$
2. **Linearity in the first argument:** $\langle a\mathbf{u} + b\mathbf{v}, \mathbf{w} \rangle = a\langle \mathbf{u}, \mathbf{w} \rangle + b\langle \mathbf{v}, \mathbf{w} \rangle$
3. **Positive definiteness:** $\langle \mathbf{v}, \mathbf{v} \rangle \ge 0$ with equality iff $\mathbf{v} = \mathbf{0}$

The standard inner product on $\mathbb{R}^n$ (the dot product) is:

$$
\langle \mathbf{u}, \mathbf{v} \rangle = \mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^n u_i v_i
$$

For complex spaces $\mathbb{C}^n$, the standard inner product is:

$$
\langle \mathbf{u}, \mathbf{v} \rangle = \sum_{i=1}^n u_i \overline{v_i}
$$

## Norms

An inner product induces a **norm** (length):

$$
\|\mathbf{v}\| = \sqrt{\langle \mathbf{v}, \mathbf{v} \rangle}
$$

For $\mathbb{R}^n$ with the standard inner product, this is the Euclidean norm:

$$
\|\mathbf{v}\|_2 = \sqrt{\sum_{i=1}^n v_i^2}
$$

The **Cauchy-Schwarz inequality** is fundamental:

$$
|\langle \mathbf{u}, \mathbf{v} \rangle| \le \|\mathbf{u}\| \|\mathbf{v}\|
$$

with equality iff $\mathbf{u}$ and $\mathbf{v}$ are linearly dependent.

The **triangle inequality** follows:

$$
\|\mathbf{u} + \mathbf{v}\| \le \|\mathbf{u}\| + \|\mathbf{v}\|
$$

Other important norms include the $\ell^1$ norm $\|\mathbf{v}\|_1 = \sum_i |v_i|$ and the $\ell^\infty$ norm $\|\mathbf{v}\|_\infty = \max_i |v_i|$.

## Orthogonality

Two vectors $\mathbf{u}, \mathbf{v} \in V$ are **orthogonal** if:

$$
\langle \mathbf{u}, \mathbf{v} \rangle = 0
$$

A set of vectors is **orthonormal** if each pair is orthogonal and each has unit norm:

$$
\langle \mathbf{v}_i, \mathbf{v}_j \rangle = \delta_{ij} = \begin{cases} 1 & i = j \\ 0 & i \neq j \end{cases}
$$

Orthonormal bases are computationally convenient because coordinates are given by inner products:

$$
\mathbf{v} = \sum_{i=1}^n \langle \mathbf{v}, \mathbf{b}_i \rangle \mathbf{b}_i
$$

for an orthonormal basis $\{\mathbf{b}_i\}$.

## Gram-Schmidt Process

The **Gram-Schmidt process** converts any basis $\{\mathbf{v}_1, \dots, \mathbf{v}_n\}$ into an orthonormal basis $\{\mathbf{q}_1, \dots, \mathbf{q}_n\}$:

$$
\mathbf{u}_1 = \mathbf{v}_1, \quad \mathbf{q}_1 = \frac{\mathbf{u}_1}{\|\mathbf{u}_1\|}
$$

For $k = 2, \dots, n$:

$$
\mathbf{u}_k = \mathbf{v}_k - \sum_{j=1}^{k-1} \langle \mathbf{v}_k, \mathbf{q}_j \rangle \mathbf{q}_j, \quad \mathbf{q}_k = \frac{\mathbf{u}_k}{\|\mathbf{u}_k\|}
$$

This ensures $\operatorname{span}\{\mathbf{q}_1, \dots, \mathbf{q}_k\} = \operatorname{span}\{\mathbf{v}_1, \dots, \mathbf{v}_k\}$ for all $k$.

The **QR decomposition** encodes this process: $A = QR$, where $Q$ has orthonormal columns and $R$ is upper-triangular.

## Applications

- **Feature Vectors:** In ML, each data point is a vector in $\mathbb{R}^d$. Distances are measured via norms: $\|\mathbf{x} - \mathbf{x}'\|_2$ (Euclidean) or $\frac{\langle \mathbf{x}, \mathbf{x}' \rangle}{\|\mathbf{x}\|\|\mathbf{x}'\|}$ (cosine similarity).
- **Computer Graphics:** 3D positions, directions, and colors are vectors. Transformations like rotation and translation are linear (or affine) maps.
- **Signal Processing:** Orthogonal bases (Fourier, wavelets) allow efficient representation via [[Singular Value Decomposition|SVD]] and related decompositions.

## Relationships to Other Notes

- [[Matrices and Linear Maps]]: Matrices represent linear maps between vector spaces.
- [[Eigenvalues and Eigenvectors]]: Eigenvectors are special vectors preserved (up to scaling) by a linear map.
- [[Singular Value Decomposition]]: SVD finds orthonormal bases for the four fundamental subspaces.

## References

- Strang, G. (2016). *Introduction to Linear Algebra*. Wellesley-Cambridge Press.
- Axler, S. (2015). *Linear Algebra Done Right*. Springer.
- Boyd, S., & Vandenberghe, L. (2018). *Introduction to Applied Linear Algebra*. Cambridge University Press.
