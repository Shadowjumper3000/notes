# Linear Equations and Representations

## Systems of Linear Equations

A **system of linear equations** can be written as:
$$
\begin{align}
a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n &= b_1 \\
a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n &= b_2 \\
&\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \cdots + a_{mn}x_n &= b_m
\end{align}
$$

### Matrix Form

$$
A\mathbf{x} = \mathbf{b}
$$

where $A$ is the coefficient matrix, $\mathbf{x}$ is the variable vector, and $\mathbf{b}$ is the constant vector.

### Augmented Matrix

$$
[A|\mathbf{b}] = \left[\begin{array}{cccc|c}
a_{11} & a_{12} & \cdots & a_{1n} & b_1 \\
a_{21} & a_{22} & \cdots & a_{2n} & b_2 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn} & b_m
\end{array}\right]
$$

---

## Solution Types

1. **Unique solution**: One point of intersection
2. **Infinitely many solutions**: Dependent equations (overlapping lines/planes)
3. **No solution**: Inconsistent system (parallel lines/planes)

---

## Row Operations

Three **elementary row operations**:

1. **Swap rows**: $R_i \leftrightarrow R_j$
2. **Multiply row by nonzero scalar**: $kR_i \to R_i$
3. **Add multiple of one row to another**: $R_i + kR_j \to R_i$

---

## Gaussian Elimination

**Goal:** Transform to **row echelon form (REF)**

**REF properties:**
1. All zero rows are at the bottom
2. Leading entry (pivot) of each row is to the right of the pivot above it
3. All entries below a pivot are zero

**Steps:**
1. Use row operations to create zeros below the first pivot
2. Move to next row and repeat
3. Continue until in REF

---

## Gauss-Jordan Elimination

**Goal:** Transform to **reduced row echelon form (RREF)**

**RREF properties:**
1. Satisfies REF properties
2. Each pivot is 1
3. Each pivot is the only nonzero entry in its column

**Additional steps beyond Gaussian elimination:**
1. Scale pivot rows so pivots are 1
2. Create zeros above each pivot

---

## Column Picture Representation

- Solve $$ A\mathbf{x} = \mathbf{b} $$
- Matrix:
  $$ A = \begin{bmatrix} \mathbf{a}_1 & \mathbf{a}_2 & \cdots & \mathbf{a}_n \end{bmatrix} $$
  - Column picture: $$ \mathbf{b} = x_1 \mathbf{a}_1 + x_2 \mathbf{a}_2 + \cdots + x_n \mathbf{a}_n $$

**Interpretation:** Find scalars $x_i$ such that the linear combination of columns equals $\mathbf{b}$.

---

## Homogeneous Systems

A system is **homogeneous** if $\mathbf{b} = \mathbf{0}$:
$$
A\mathbf{x} = \mathbf{0}
$$

**Properties:**
- Always has at least the **trivial solution** $\mathbf{x} = \mathbf{0}$
- Has nontrivial solutions iff columns of $A$ are linearly dependent
- Solution set forms a **subspace** (the null space of $A$)

---

## Matrix Factorizations

## LU Factorization

- Decompose matrix $$ A $$ into:
  $$ A = LU $$
  - $$ L $$: Lower triangular matrix with 1's on diagonal
  - $$ U $$: Upper triangular matrix (REF form)

### Benefits
- Solve $A\mathbf{x} = \mathbf{b}$ efficiently for multiple $\mathbf{b}$ vectors
- Computational cost: $O(n^3)$ for factorization, $O(n^2)$ per solve

### Process

1. Perform Gaussian elimination, recording multipliers
2. $L$ contains the multipliers used
3. $U$ is the final upper triangular form

- Solving $$ A\mathbf{x} = \mathbf{b} $$:
  1. Solve $$ L\mathbf{y} = \mathbf{b} $$ (forward substitution)
  2. Solve $$ U\mathbf{x} = \mathbf{y} $$ (backward substitution)

### Example of LU Decomposition

For a matrix $$ A = \begin{bmatrix} 4 & 3 \\ 6 & 3 \end{bmatrix} $$:

1. Decompose into $$ L $$ and $$ U $$:
   $$ L = \begin{bmatrix} 1 & 0 \\ \frac{3}{2} & 1 \end{bmatrix}, \quad U = \begin{bmatrix} 4 & 3 \\ 0 & -\frac{3}{2} \end{bmatrix} $$

2. Verification:
   $$ A = L \cdot U $$

---

## QR Factorization

$$
A = QR
$$

where:
- $Q$: Orthogonal matrix ($Q^TQ = I$)
- $R$: Upper triangular matrix

**Method:** Use Gram-Schmidt process on columns of $A$

**Applications:**
- Least squares problems
- Eigenvalue algorithms

---

## Solving Linear Systems: Advanced Methods

### Cramer's Rule

For system $A\mathbf{x} = \mathbf{b}$ where $A$ is square and invertible:
$$
x_i = \frac{\det(A_i)}{\det(A)}
$$

where $A_i$ is $A$ with column $i$ replaced by $\mathbf{b}$.

**Note:** Computationally expensive; use for small systems or theoretical purposes.

---

### Matrix Inverse Method

If $A$ is invertible:
$$
\mathbf{x} = A^{-1}\mathbf{b}
$$

**Computing $A^{-1}$:**
1. Form $[A|I]$
2. Row reduce to $[I|A^{-1}]$

**Computational cost:** $O(n^3)$; not efficient for single solutions.

---

## Consistency and Solvability

### Theorem: Existence and Uniqueness

For system $A\mathbf{x} = \mathbf{b}$:

**Consistent (has solution) iff:**
$$
\text{rank}(A) = \text{rank}([A|\mathbf{b}])
$$

**Unique solution iff:**
$$
\text{rank}(A) = n \quad \text{(number of variables)}
$$

**Infinitely many solutions iff:**
$$
\text{rank}(A) < n \quad \text{and system is consistent}
$$

---

## Least Squares Solutions

When $A\mathbf{x} = \mathbf{b}$ has no exact solution (overdetermined system), find **least squares solution**:

$$
\mathbf{x}^* = \arg\min_{\mathbf{x}} \|A\mathbf{x} - \mathbf{b}\|^2
$$

**Solution via normal equations:**
$$
A^TA\mathbf{x}^* = A^T\mathbf{b}
$$

If $A^TA$ is invertible:
$$
\mathbf{x}^* = (A^TA)^{-1}A^T\mathbf{b}
$$

---

## Applications

### Computer Graphics

- Transformations: rotation, scaling, translation
- Projection matrices

### Economics

- Input-output models (Leontief models)
- Linear programming

### Engineering

- Circuit analysis (Kirchhoff's laws)
- Structural analysis
- Control systems

### Data Science

- Linear regression
- Principal component analysis (PCA)
- Recommendation systems

---

## Computational Considerations

### Numerical Stability

- **Pivoting:** Choose largest pivot to minimize rounding errors
- **Condition number:** Measures sensitivity to perturbations
  $$
  \kappa(A) = \|A\| \|A^{-1}\|
  $$
  Large condition number indicates ill-conditioned system

### Sparse Matrices

- Matrices with mostly zero entries
- Use specialized algorithms to save memory and time
- Examples: Graph adjacency matrices, finite element methods

---

## Summary

- Linear systems can be represented in multiple forms
- Row operations transform systems without changing solutions
- Gaussian and Gauss-Jordan elimination are fundamental algorithms
- Matrix factorizations (LU, QR) enable efficient solving
- Least squares provides approximate solutions for overdetermined systems
- Applications span mathematics, science, engineering, and data science
