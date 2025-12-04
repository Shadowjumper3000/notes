## What is a Subspace?

A **subspace** of a vector space is a set of vectors that satisfies three conditions:

1. **Contains the Zero Vector**: The zero vector (0) is in the subspace.
2. **Closed under Addition**: If vectors **u** and **v** are in the subspace, then their sum **u + v** is also in the subspace.
3. **Closed under Scalar Multiplication**: If **u** is in the subspace and **c** is a scalar, then **c u** is also in the subspace.

## Types of Subspaces

For a given matrix **A**, the following subspaces are important:

### 1. Column Space (Range)

The **column space** of a matrix **A** is the set of all possible linear combinations of its columns. It represents all vectors that can be formed using the columns of **A**.

- **Notation**: Col(A)
- **Dimension**: The number of pivot columns in the row echelon form of **A**.
- **Subspace of**: **R^m** (where **m** is the number of rows of **A**).

**How to find the column space:**

- Convert **A** to row echelon form (RREF).
- Identify the pivot columns.
- The corresponding columns in the original matrix **A** form the basis for Col(A).

### 2. Row Space

The **row space** of a matrix **A** is the set of all linear combinations of its rows.

- **Notation**: Row(A)
- **Dimension**: The number of nonzero rows in the row echelon form of **A**.
- **Subspace of**: **R^n** (where **n** is the number of columns of **A**).

**How to find the row space:**

- Convert **A** to row echelon form.
- The nonzero rows form a basis for Row(A).
- Alternatively, Row(A) is the same as the column space of **A^T** (the transpose of **A**).

### 3. Null Space (Kernel)

The **null space** of **A** consists of all solutions to the equation **A x = 0**.

- **Notation**: Null(A)
- **Dimension**: Called the **nullity**, it is the number of free variables in the solution.
- **Subspace of**: **R^n** (where **n** is the number of columns of **A**).

**How to find the null space:**

- Solve **A x = 0** using Gaussian elimination.
- Express the solution in parametric form.
- The vectors that define the parametric form form a basis for Null(A).

### 4. Left Null Space

The **left null space** of **A** consists of all solutions to the equation **A^T y = 0**.

- **Notation**: Null(A^T)
- **Subspace of**: **R^m** (where **m** is the number of rows of **A**).

**How to find the left null space:**

- Solve **A^T y = 0**.
- The solution vectors form a basis for Null(A^T).

## Properties of Subspaces

### Dimension of a Subspace

The **dimension** of a subspace is the number of basis vectors for that subspace:

- The **rank** of **A** is the dimension of Col(A) and Row(A).
- The **nullity** of **A** is the dimension of Null(A).

### Rank-Nullity Theorem

The **Rank-Nullity Theorem** states:

**Rank(A) + Nullity(A) = n**

where:

- **Rank(A)** = Dimension of Col(A) (number of pivot columns).
- **Nullity(A)** = Dimension of Null(A) (number of free variables).
- **n** = Number of columns of **A**.

### Basis of a Subspace

A **basis** of a subspace is a set of linearly independent vectors that span the subspace.

**Finding a basis:**

- **Column Space**: Identify pivot columns in the original matrix.
- **Row Space**: Identify pivot rows in the row echelon form.
- **Null Space**: Solve **A x = 0**, and the free variable vectors form a basis.

## Conclusion

Understanding the different subspaces of a matrix is essential for solving linear systems and understanding matrix transformations. The column space, row space, null space, and left null space each provide unique insights into the structure of a matrix.