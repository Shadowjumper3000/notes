# Vector Calculus

## Vector Fields

A **vector field** assigns a vector to each point in space.

### Two Dimensions
$$
\mathbf{F}(x, y) = \langle P(x, y), Q(x, y) \rangle = P(x, y)\mathbf{i} + Q(x, y)\mathbf{j}
$$

### Three Dimensions
$$
\mathbf{F}(x, y, z) = \langle P, Q, R \rangle = P\mathbf{i} + Q\mathbf{j} + R\mathbf{k}
$$

**Examples:**
- **Gravitational field:** $\mathbf{F} = -\frac{GMm}{r^2}\hat{\mathbf{r}}$
- **Velocity field:** Flow of fluid

---

## Line Integrals

### Line Integral of a Scalar Function

Along curve $C$ parameterized by $\mathbf{r}(t) = \langle x(t), y(t) \rangle$, $a \leq t \leq b$:
$$
\int_C f(x, y)\,ds = \int_a^b f(x(t), y(t)) |\mathbf{r}'(t)|\,dt
$$

where $ds = |\mathbf{r}'(t)|\,dt$ is arc length element.

---

### Line Integral of a Vector Field

$$
\int_C \mathbf{F} \cdot d\mathbf{r} = \int_a^b \mathbf{F}(\mathbf{r}(t)) \cdot \mathbf{r}'(t)\,dt
$$

**Alternative notation:**
$$
\int_C P\,dx + Q\,dy = \int_a^b \left(P\frac{dx}{dt} + Q\frac{dy}{dt}\right)\,dt
$$

**Physical interpretation:** Work done by force field $\mathbf{F}$ along curve $C$.

---

### Properties

1. **Reversal:** $\int_{-C} \mathbf{F} \cdot d\mathbf{r} = -\int_C \mathbf{F} \cdot d\mathbf{r}$
2. **Additivity:** $\int_{C_1 + C_2} \mathbf{F} \cdot d\mathbf{r} = \int_{C_1} \mathbf{F} \cdot d\mathbf{r} + \int_{C_2} \mathbf{F} \cdot d\mathbf{r}$
3. **Linearity:** $\int_C (c\mathbf{F} + d\mathbf{G}) \cdot d\mathbf{r} = c\int_C \mathbf{F} \cdot d\mathbf{r} + d\int_C \mathbf{G} \cdot d\mathbf{r}$

---

## Fundamental Theorem for Line Integrals

If $\mathbf{F} = \nabla f$ (conservative field), then:
$$
\int_C \mathbf{F} \cdot d\mathbf{r} = f(\mathbf{r}(b)) - f(\mathbf{r}(a))
$$

**Path independence:** The integral depends only on endpoints, not the path.

---

## Conservative Vector Fields

A vector field $\mathbf{F}$ is **conservative** if:
$$
\mathbf{F} = \nabla f
$$

for some scalar function $f$ (called the **potential function**).

### Test for Conservative Field (in 2D)

$\mathbf{F} = \langle P, Q \rangle$ is conservative if:
$$
\frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x}
$$

(on a simply connected domain)

### Finding Potential Function

If $\mathbf{F} = \langle P, Q \rangle$ is conservative:

1. Integrate $P$ with respect to $x$: $f(x, y) = \int P(x, y)\,dx + g(y)$
2. Differentiate with respect to $y$ and set equal to $Q$
3. Solve for $g(y)$

**Example:** $\mathbf{F} = \langle 2xy, x^2 \rangle$

Check: $\frac{\partial P}{\partial y} = 2x = \frac{\partial Q}{\partial x}$ ✓

Find $f$:
$$
f(x, y) = \int 2xy\,dx = x^2y + g(y)
$$

$$
\frac{\partial f}{\partial y} = x^2 + g'(y) = x^2 \implies g'(y) = 0 \implies g(y) = C
$$

$$
f(x, y) = x^2y
$$

---

## Green's Theorem

For a positively oriented (counterclockwise), simple closed curve $C$ and region $D$:
$$
\oint_C P\,dx + Q\,dy = \iint_D \left(\frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y}\right)\,dA
$$

**Alternative form:**
$$
\oint_C \mathbf{F} \cdot d\mathbf{r} = \iint_D \left(\frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y}\right)\,dA
$$

### Applications

**Area of region:**
$$
A = \frac{1}{2}\oint_C x\,dy - y\,dx
$$

---

## Curl and Divergence

### Curl (3D)

Measures rotation of a vector field:
$$
\text{curl}\,\mathbf{F} = \nabla \times \mathbf{F} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ P & Q & R \end{vmatrix}
$$

$$
= \left\langle \frac{\partial R}{\partial y} - \frac{\partial Q}{\partial z}, \frac{\partial P}{\partial z} - \frac{\partial R}{\partial x}, \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right\rangle
$$

**Properties:**
- If $\text{curl}\,\mathbf{F} = \mathbf{0}$, then $\mathbf{F}$ is **conservative** (on simply connected domain)
- $\text{curl}(\nabla f) = \mathbf{0}$ for any scalar $f$

---

### Divergence

Measures "outflow" from a point:
$$
\text{div}\,\mathbf{F} = \nabla \cdot \mathbf{F} = \frac{\partial P}{\partial x} + \frac{\partial Q}{\partial y} + \frac{\partial R}{\partial z}
$$

**Properties:**
- Positive divergence: Source (expanding)
- Negative divergence: Sink (contracting)
- Zero divergence: Incompressible

**Identity:** $\text{div}(\text{curl}\,\mathbf{F}) = 0$

---

## Parametric Surfaces

A surface $S$ can be parameterized as:
$$
\mathbf{r}(u, v) = \langle x(u, v), y(u, v), z(u, v) \rangle
$$

for $(u, v)$ in some domain $D$.

### Tangent Vectors

$$
\mathbf{r}_u = \frac{\partial \mathbf{r}}{\partial u}, \quad \mathbf{r}_v = \frac{\partial \mathbf{r}}{\partial v}
$$

### Normal Vector

$$
\mathbf{n} = \mathbf{r}_u \times \mathbf{r}_v
$$

---

## Surface Integrals

### Surface Integral of a Scalar Function

$$
\iint_S f(x, y, z)\,dS = \iint_D f(\mathbf{r}(u, v)) |\mathbf{r}_u \times \mathbf{r}_v|\,du\,dv
$$

### Surface Integral of a Vector Field

**Flux** of $\mathbf{F}$ across surface $S$:
$$
\iint_S \mathbf{F} \cdot d\mathbf{S} = \iint_S \mathbf{F} \cdot \mathbf{n}\,dS = \iint_D \mathbf{F}(\mathbf{r}(u, v)) \cdot (\mathbf{r}_u \times \mathbf{r}_v)\,du\,dv
$$

---

## Stokes' Theorem

For an oriented surface $S$ with boundary curve $C$:
$$
\oint_C \mathbf{F} \cdot d\mathbf{r} = \iint_S (\nabla \times \mathbf{F}) \cdot d\mathbf{S}
$$

**In words:** The circulation around the boundary equals the flux of curl through the surface.

### Special Case: Green's Theorem

Green's Theorem is a 2D version of Stokes' Theorem.

---

## Divergence Theorem (Gauss's Theorem)

For a closed surface $S$ enclosing solid region $E$:
$$
\iint_S \mathbf{F} \cdot d\mathbf{S} = \iiint_E \nabla \cdot \mathbf{F}\,dV
$$

**In words:** The flux out of a closed surface equals the total divergence inside.

---

## Summary of Major Theorems

### Fundamental Theorem of Calculus
$$
\int_a^b f'(x)\,dx = f(b) - f(a)
$$

### Fundamental Theorem for Line Integrals
$$
\int_C \nabla f \cdot d\mathbf{r} = f(\mathbf{r}(b)) - f(\mathbf{r}(a))
$$

### Green's Theorem
$$
\oint_C \mathbf{F} \cdot d\mathbf{r} = \iint_D (\nabla \times \mathbf{F}) \cdot \mathbf{k}\,dA
$$

### Stokes' Theorem
$$
\oint_C \mathbf{F} \cdot d\mathbf{r} = \iint_S (\nabla \times \mathbf{F}) \cdot d\mathbf{S}
$$

### Divergence Theorem
$$
\iint_S \mathbf{F} \cdot d\mathbf{S} = \iiint_E \nabla \cdot \mathbf{F}\,dV
$$

---

## Physical Interpretations

### Work
$$
W = \int_C \mathbf{F} \cdot d\mathbf{r}
$$

### Circulation
Line integral around a closed curve:
$$
\oint_C \mathbf{F} \cdot d\mathbf{r}
$$

### Flux
Flow through a surface:
$$
\iint_S \mathbf{F} \cdot d\mathbf{S}
$$

---

## Applications

### Fluid Dynamics
- Velocity fields
- Incompressible flow: $\nabla \cdot \mathbf{v} = 0$
- Irrotational flow: $\nabla \times \mathbf{v} = \mathbf{0}$

### Electromagnetism

**Maxwell's Equations:**
1. Gauss's law: $\nabla \cdot \mathbf{E} = \frac{\rho}{\epsilon_0}$
2. No magnetic monopoles: $\nabla \cdot \mathbf{B} = 0$
3. Faraday's law: $\nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}$
4. Ampère-Maxwell law: $\nabla \times \mathbf{B} = \mu_0\mathbf{J} + \mu_0\epsilon_0\frac{\partial \mathbf{E}}{\partial t}$

### Heat Flow

Heat flux vector: $\mathbf{q} = -k\nabla T$

---

## Summary

- **Vector fields** assign vectors to points in space
- **Line integrals** compute work and circulation
- **Conservative fields** have potential functions
- **Curl** measures rotation; **divergence** measures expansion
- **Surface integrals** compute flux
- **Major theorems** (Green's, Stokes', Divergence) relate integrals across dimensions
- Applications in physics, engineering, and fluid dynamics
