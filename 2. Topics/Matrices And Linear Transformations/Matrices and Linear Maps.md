# Matrices and Linear Maps

## Overview
A matrix is a rectangular array of numbers that can be used to represent a linear transformation between two vector spaces. When we multiply a vector by a matrix, we are essentially mapping that vector from its original space to a new one. This perspective allows us to treat complex operations like rotation, scaling, and projection as simple algebraic multiplications. Every linear map $T: V \to W$ between finite-dimensional vector spaces can be uniquely represented by a matrix once a basis for $V$ and $W$ has been chosen.

## Technical Depth
### The Four Fundamental Subspaces
For any $m \times n$ matrix $A$, there are four critical subspaces that describe its behavior:
1.  **Column Space $C(A)$:** The span of the columns of $A$. It contains all vectors $b$ for which the equation $Ax = b$ is solvable.
2.  **Null Space $N(A)$:** The set of all vectors $x$ that satisfy $Ax = 0$. The dimension of this space is the nullity.
3.  **Row Space $C(A^T)$:** The span of the rows of $A$, or the column space of its transpose.
4.  **Left Null Space $N(A^T)$:** The null space of the transpose of $A$.

The Fundamental Theorem of Linear Algebra states that the dimension of the column space (the **rank**) plus the dimension of the null space is equal to the number of columns $n$. This is often referred to as the Rank-Nullity Theorem.

### Linear Transformations as Matrix Operations
Linearity implies that the transformation preserves the operations of addition and scalar multiplication: $T(u + v) = T(u) + T(v)$ and $T(cu) = cT(u)$. In matrix form, this is inherently satisfied by the distributive and associative properties of matrix-vector multiplication. Common transformations in 3D space, such as rotation around an axis, can be represented by specialized orthogonal matrices where the transpose is equal to the inverse ($Q^T Q = I$).

## Applications
- **Neural Networks:** Layers in a neural network are essentially sequences of matrix-vector multiplications followed by non-linear activations. The weight matrices represent the learned linear transformations.
- **Image Processing:** Kernels used in convolution (like Gaussian blurs) can be viewed as local linear operators acting on the pixel grid.

## References
- Strang, G. (1993). *The Fundamental Theorem of Linear Algebra*. The American Mathematical Monthly.
- Goodfellow, I., Bengio, Y., & Courville, A. (2016). *Deep Learning*. MIT Press. (Chapter 2: Linear Algebra).
