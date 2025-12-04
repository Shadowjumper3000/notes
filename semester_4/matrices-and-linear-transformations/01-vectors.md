# Vectors - Comprehensive Guide

## Introduction to Vectors

- **Definition**: A vector is a quantity with both magnitude and direction.
- **Geometric interpretation**: Can be represented as an arrow in space
- **Algebraic representation**: An ordered list of numbers

### Vector Formats

- **Column vector**: 
  $$ \mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix} $$
  
- **Row vector**: 
  $$ \mathbf{v} = \begin{bmatrix} v_1 & v_2 & \dots & v_n \end{bmatrix} $$

### Vector Spaces

A **vector space** $V$ over a field $F$ is a set with two operations (addition and scalar multiplication) satisfying:

1. **Closure under addition**: $\mathbf{u} + \mathbf{v} \in V$
2. **Closure under scalar multiplication**: $c\mathbf{v} \in V$
3. **Associativity of addition**: $(\mathbf{u} + \mathbf{v}) + \mathbf{w} = \mathbf{u} + (\mathbf{v} + \mathbf{w})$
4. **Commutativity of addition**: $\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}$
5. **Identity element**: $\mathbf{0} + \mathbf{v} = \mathbf{v}$
6. **Inverse elements**: $\mathbf{v} + (-\mathbf{v}) = \mathbf{0}$
7. **Distributivity**: $c(\mathbf{u} + \mathbf{v}) = c\mathbf{u} + c\mathbf{v}$
8. **Scalar associativity**: $(cd)\mathbf{v} = c(d\mathbf{v})$
9. **Scalar identity**: $1\mathbf{v} = \mathbf{v}$

---

## Vector Operations

### Addition and Subtraction

$$
\mathbf{u} + \mathbf{v} = \begin{bmatrix} u_1 + v_1 \\ u_2 + v_2 \\ \vdots \\ u_n + v_n \end{bmatrix}
$$

**Properties:**
- Commutative: $\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}$
- Associative: $(\mathbf{u} + \mathbf{v}) + \mathbf{w} = \mathbf{u} + (\mathbf{v} + \mathbf{w})$

### Scalar Multiplication

$$
c\mathbf{v} = \begin{bmatrix} cv_1 \\ cv_2 \\ \vdots \\ cv_n \end{bmatrix}
$$

**Geometric effect:**
- Scales the magnitude by $|c|$
- If $c < 0$, reverses direction

---

## Distance Metrics

### Minkowski Distance
$$ d(\mathbf{u}, \mathbf{v}) = \left(\sum_{i=1}^n |u_i - v_i|^p\right)^{\frac{1}{p}} $$

- Special cases:
  - Manhattan distance ($$ p = 1 $$)
  - Euclidean distance ($$ p = 2 $$)

### Unit Vectors

- A unit vector has a magnitude of 1:
  $$ \mathbf{u} = \frac{\mathbf{v}}{\|\mathbf{v}\|} $$

### Angle Between Vectors

- Cosine formula:
  $$ \cos \theta = \frac{\mathbf{u} \cdot \mathbf{v}}{\|\mathbf{u}\| \|\mathbf{v}\|} $$

### Vector Operations

- **Dot Product**:
  $$ \mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^n u_i v_i $$
- **Cross Product** (in 3D):
  $$ \mathbf{u} \times \mathbf{v} = \begin{bmatrix} u_2 v_3 - u_3 v_2 \\ u_3 v_1 - u_1 v_3 \\ u_1 v_2 - u_2 v_1 \end{bmatrix} $$

- **Norms**:
  $$ \|\mathbf{v}\|_p = \left(\sum_{i=1}^n |v_i|^p\right)^{\frac{1}{p}} $$
  - $$ \|\mathbf{v}\|_1 $$ (Manhattan norm): $$ \sum_{i=1}^n |v_i| $$
  - $$ \|\mathbf{v}\|_2 $$ (Euclidean norm): $$ \sqrt{\sum_{i=1}^n v_i^2} $$
  - $$ \|\mathbf{v}\|_\infty $$ (Maximum norm): $$ \max_i |v_i| $$

---

## Linear Independence and Dependence

### Linear Combination

A vector $\mathbf{v}$ is a **linear combination** of vectors $\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_k$ if:
$$
\mathbf{v} = c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \cdots + c_k\mathbf{v}_k
$$

### Linear Independence

Vectors $\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_k$ are **linearly independent** if:
$$
c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \cdots + c_k\mathbf{v}_k = \mathbf{0} \implies c_1 = c_2 = \cdots = c_k = 0
$$

**Test for independence:**
- Form matrix with vectors as columns
- Compute rank or row reduce to check for pivot in every column

### Span

The **span** of vectors $\{\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_k\}$ is the set of all linear combinations:
$$
\text{span}(\mathbf{v}_1, \ldots, \mathbf{v}_k) = \{c_1\mathbf{v}_1 + \cdots + c_k\mathbf{v}_k : c_i \in \mathbb{R}\}
$$

### Basis and Dimension

A **basis** for a vector space $V$ is a linearly independent set that spans $V$.

The **dimension** of $V$ is the number of vectors in any basis.

**Standard basis for $\mathbb{R}^n$:**
$$
\mathbf{e}_1 = \begin{bmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{bmatrix}, \quad \mathbf{e}_2 = \begin{bmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{bmatrix}, \quad \ldots, \quad \mathbf{e}_n = \begin{bmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{bmatrix}
$$

---

## Orthogonality

### Orthogonal Vectors

Vectors $\mathbf{u}$ and $\mathbf{v}$ are **orthogonal** if:
$$
\mathbf{u} \cdot \mathbf{v} = 0
$$

### Orthogonal Projection

Projection of $\mathbf{v}$ onto $\mathbf{u}$:
$$
\text{proj}_{\mathbf{u}}\mathbf{v} = \frac{\mathbf{u} \cdot \mathbf{v}}{\mathbf{u} \cdot \mathbf{u}}\mathbf{u}
$$

Orthogonal component:
$$
\mathbf{v} - \text{proj}_{\mathbf{u}}\mathbf{v}
$$

### Gram-Schmidt Process

Convert a basis into an orthonormal basis:

1. $\mathbf{u}_1 = \mathbf{v}_1$
2. $\mathbf{u}_2 = \mathbf{v}_2 - \text{proj}_{\mathbf{u}_1}\mathbf{v}_2$
3. $\mathbf{u}_3 = \mathbf{v}_3 - \text{proj}_{\mathbf{u}_1}\mathbf{v}_3 - \text{proj}_{\mathbf{u}_2}\mathbf{v}_3$
4. Continue for all vectors
5. Normalize: $\mathbf{e}_i = \frac{\mathbf{u}_i}{\|\mathbf{u}_i\|}$

---

## Vector Products in Detail

### Dot Product Properties

1. **Commutative**: $\mathbf{u} \cdot \mathbf{v} = \mathbf{v} \cdot \mathbf{u}$
2. **Distributive**: $\mathbf{u} \cdot (\mathbf{v} + \mathbf{w}) = \mathbf{u} \cdot \mathbf{v} + \mathbf{u} \cdot \mathbf{w}$
3. **Scalar multiplication**: $(c\mathbf{u}) \cdot \mathbf{v} = c(\mathbf{u} \cdot \mathbf{v})$
4. **Positive definite**: $\mathbf{v} \cdot \mathbf{v} \geq 0$, with equality iff $\mathbf{v} = \mathbf{0}$

### Cross Product Properties (3D only)

1. **Anti-commutative**: $\mathbf{u} \times \mathbf{v} = -(\mathbf{v} \times \mathbf{u})$
2. **Distributive**: $\mathbf{u} \times (\mathbf{v} + \mathbf{w}) = \mathbf{u} \times \mathbf{v} + \mathbf{u} \times \mathbf{w}$
3. **Orthogonality**: $\mathbf{u} \times \mathbf{v}$ is orthogonal to both $\mathbf{u}$ and $\mathbf{v}$
4. **Magnitude**: $\|\mathbf{u} \times \mathbf{v}\| = \|\mathbf{u}\|\|\mathbf{v}\|\sin\theta$

**Geometric interpretation:** Area of parallelogram formed by $\mathbf{u}$ and $\mathbf{v}$

### Scalar Triple Product

$$
\mathbf{u} \cdot (\mathbf{v} \times \mathbf{w})
$$

**Geometric meaning:** Volume of parallelepiped formed by three vectors

---

## Applications

### Physics

- **Displacement vectors**: Position changes
- **Velocity and acceleration**: Time derivatives of position
- **Force vectors**: Direction and magnitude of forces
- **Electric and magnetic fields**: Field vectors at each point

### Computer Graphics

- **3D transformations**: Rotation, translation, scaling
- **Normal vectors**: Surface orientations
- **Lighting calculations**: Dot products for intensity

### Machine Learning

- **Feature vectors**: Data representation
- **Weight vectors**: Model parameters
- **Gradients**: Direction of steepest ascent

---

## Summary

- Vectors represent quantities with magnitude and direction
- Vector spaces have specific algebraic properties
- Linear independence and span are fundamental concepts
- Orthogonality provides geometric structure
- Dot and cross products have both algebraic and geometric interpretations
- Vectors are essential across mathematics, physics, and computer science
