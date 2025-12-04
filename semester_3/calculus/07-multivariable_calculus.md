# Multivariable Calculus

## Functions of Several Variables

A function of two variables:
$$
z = f(x, y)
$$

A function of three variables:
$$
w = f(x, y, z)
$$

### Domain

The set of all points $(x, y)$ (or $(x, y, z)$) for which $f$ is defined.

### Graphs and Level Curves

**Graph:** The set of points $(x, y, z)$ where $z = f(x, y)$.

**Level curves:** Curves in the $xy$-plane where $f(x, y) = k$ for constant $k$.

**Example:** For $f(x, y) = x^2 + y^2$, level curves are circles $x^2 + y^2 = k$.

---

## Limits and Continuity

### Limit

$$
\lim_{(x,y) \to (a,b)} f(x,y) = L
$$

means $f(x,y)$ approaches $L$ as $(x,y)$ approaches $(a,b)$ along **any path**.

**Two-path test:** If $f$ approaches different values along different paths, the limit does not exist.

### Continuity

$f$ is **continuous at $(a,b)$** if:
$$
\lim_{(x,y) \to (a,b)} f(x,y) = f(a,b)
$$

---

## Partial Derivatives

### Definition

The **partial derivative** with respect to $x$:
$$
\frac{\partial f}{\partial x} = f_x = \lim_{h \to 0} \frac{f(x+h, y) - f(x, y)}{h}
$$

Similarly for $y$:
$$
\frac{\partial f}{\partial y} = f_y = \lim_{h \to 0} \frac{f(x, y+h) - f(x, y)}{h}
$$

**Interpretation:** Rate of change in one direction while holding other variables constant.

---

### Computing Partial Derivatives

**Rule:** Treat other variables as constants.

**Example:** $f(x, y) = x^2y + 3xy^2$

$$
f_x = 2xy + 3y^2
$$

$$
f_y = x^2 + 6xy
$$

---

### Higher-Order Partial Derivatives

$$
f_{xx} = \frac{\partial^2 f}{\partial x^2} = \frac{\partial}{\partial x}\left(\frac{\partial f}{\partial x}\right)
$$

$$
f_{yy} = \frac{\partial^2 f}{\partial y^2}
$$

$$
f_{xy} = \frac{\partial^2 f}{\partial y \partial x} = \frac{\partial}{\partial y}\left(\frac{\partial f}{\partial x}\right)
$$

$$
f_{yx} = \frac{\partial^2 f}{\partial x \partial y}
$$

**Clairaut's Theorem:** If $f_{xy}$ and $f_{yx}$ are continuous, then:
$$
f_{xy} = f_{yx}
$$

---

## Chain Rule

### Case 1: One Independent Variable

If $z = f(x, y)$ where $x = x(t)$ and $y = y(t)$:
$$
\frac{dz}{dt} = \frac{\partial f}{\partial x}\frac{dx}{dt} + \frac{\partial f}{\partial y}\frac{dy}{dt}
$$

### Case 2: Multiple Independent Variables

If $z = f(x, y)$ where $x = x(s, t)$ and $y = y(s, t)$:
$$
\frac{\partial z}{\partial s} = \frac{\partial f}{\partial x}\frac{\partial x}{\partial s} + \frac{\partial f}{\partial y}\frac{\partial y}{\partial s}
$$

$$
\frac{\partial z}{\partial t} = \frac{\partial f}{\partial x}\frac{\partial x}{\partial t} + \frac{\partial f}{\partial y}\frac{\partial y}{\partial t}
$$

---

## Gradient Vector

The **gradient** of $f$:
$$
\nabla f = \left\langle \frac{\partial f}{\partial x}, \frac{\partial f}{\partial y} \right\rangle = \langle f_x, f_y \rangle
$$

For three variables:
$$
\nabla f = \langle f_x, f_y, f_z \rangle
$$

**Properties:**
- Points in the direction of **maximum increase** of $f$
- Magnitude $|\nabla f|$ is the **maximum rate of increase**
- Perpendicular to level curves/surfaces

---

## Directional Derivatives

The **directional derivative** of $f$ at $(x_0, y_0)$ in the direction of unit vector $\mathbf{u} = \langle a, b \rangle$:
$$
D_{\mathbf{u}}f = \nabla f \cdot \mathbf{u} = f_x a + f_y b
$$

**Maximum rate of increase:** In direction of $\nabla f$, with value $|\nabla f|$.

**Minimum rate of increase:** In direction of $-\nabla f$, with value $-|\nabla f|$.

**Zero rate of change:** Perpendicular to $\nabla f$.

---

## Tangent Planes and Linear Approximation

### Tangent Plane

At point $(x_0, y_0, z_0)$ on surface $z = f(x, y)$:
$$
z - z_0 = f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0)
$$

### Linear Approximation

$$
f(x, y) \approx f(x_0, y_0) + f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0)
$$

---

## Differentials

$$
dz = f_x\,dx + f_y\,dy
$$

Used to approximate change in $z$:
$$
\Delta z \approx dz
$$

---

## Optimization

### Critical Points

Points where $\nabla f = \mathbf{0}$:
$$
f_x = 0 \quad \text{and} \quad f_y = 0
$$

### Second Derivative Test

At critical point $(a, b)$, compute:
$$
D = f_{xx}(a,b) \cdot f_{yy}(a,b) - [f_{xy}(a,b)]^2
$$

- If $D > 0$ and $f_{xx}(a,b) > 0$: **Local minimum**
- If $D > 0$ and $f_{xx}(a,b) < 0$: **Local maximum**
- If $D < 0$: **Saddle point**
- If $D = 0$: **Inconclusive**

---

### Absolute Extrema on Closed Region

1. Find critical points in the interior
2. Find extreme values on the boundary
3. Compare all values

---

## Lagrange Multipliers

To optimize $f(x, y, z)$ subject to constraint $g(x, y, z) = k$:

**Method:**
Solve the system:
$$
\nabla f = \lambda \nabla g
$$
$$
g(x, y, z) = k
$$

**Example:** Maximize $f(x, y) = xy$ subject to $x + y = 10$.

$$
\nabla f = \langle y, x \rangle, \quad \nabla g = \langle 1, 1 \rangle
$$

$$
y = \lambda, \quad x = \lambda, \quad x + y = 10
$$

From first two: $x = y$. From constraint: $2x = 10 \implies x = y = 5$.

Maximum value: $f(5, 5) = 25$.

---

## Double Integrals

### Iterated Integrals

$$
\iint_R f(x, y)\,dA = \int_a^b \int_{g_1(x)}^{g_2(x)} f(x, y)\,dy\,dx
$$

or

$$
\iint_R f(x, y)\,dA = \int_c^d \int_{h_1(y)}^{h_2(y)} f(x, y)\,dx\,dy
$$

### Fubini's Theorem

If $f$ is continuous on rectangle $R = [a,b] \times [c,d]$:
$$
\iint_R f(x,y)\,dA = \int_a^b \int_c^d f(x,y)\,dy\,dx = \int_c^d \int_a^b f(x,y)\,dx\,dy
$$

---

### Properties

1. **Linearity:** $\iint_R [cf + dg]\,dA = c\iint_R f\,dA + d\iint_R g\,dA$
2. **Additivity:** $\iint_{R_1 \cup R_2} f\,dA = \iint_{R_1} f\,dA + \iint_{R_2} f\,dA$
3. **Area:** $\iint_R 1\,dA = \text{Area of } R$

---

### Polar Coordinates

For region described in polar coordinates:
$$
\iint_R f(x, y)\,dA = \int_\alpha^\beta \int_{r_1(\theta)}^{r_2(\theta)} f(r\cos\theta, r\sin\theta) \cdot r\,dr\,d\theta
$$

**Note:** The extra $r$ factor comes from the Jacobian.

**Example:** Area of circle of radius $a$:
$$
A = \int_0^{2\pi} \int_0^a r\,dr\,d\theta = \int_0^{2\pi} \frac{a^2}{2}\,d\theta = \pi a^2
$$

---

## Triple Integrals

$$
\iiint_E f(x, y, z)\,dV
$$

### Cylindrical Coordinates

$$
x = r\cos\theta, \quad y = r\sin\theta, \quad z = z
$$

$$
\iiint_E f(x,y,z)\,dV = \int \int \int f(r\cos\theta, r\sin\theta, z) \cdot r\,dz\,dr\,d\theta
$$

### Spherical Coordinates

$$
x = \rho\sin\phi\cos\theta, \quad y = \rho\sin\phi\sin\theta, \quad z = \rho\cos\phi
$$

$$
\iiint_E f(x,y,z)\,dV = \int \int \int f(\rho,\phi,\theta) \cdot \rho^2\sin\phi\,d\rho\,d\phi\,d\theta
$$

---

## Applications of Multiple Integrals

### Volume

$$
V = \iint_R f(x, y)\,dA
$$

### Surface Area

For surface $z = f(x, y)$ over region $R$:
$$
S = \iint_R \sqrt{1 + (f_x)^2 + (f_y)^2}\,dA
$$

### Mass

For lamina with density $\delta(x, y)$:
$$
M = \iint_R \delta(x, y)\,dA
$$

### Center of Mass

$$
\bar{x} = \frac{1}{M}\iint_R x\delta(x,y)\,dA, \quad \bar{y} = \frac{1}{M}\iint_R y\delta(x,y)\,dA
$$

---

## Change of Variables

### Jacobian

For transformation $x = g(u, v)$, $y = h(u, v)$:
$$
J = \frac{\partial(x, y)}{\partial(u, v)} = \begin{vmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{vmatrix}
$$

$$
\iint_R f(x, y)\,dA = \iint_S f(g(u,v), h(u,v)) |J|\,du\,dv
$$

---

## Summary

- **Partial derivatives:** Rate of change in one direction
- **Gradient:** Vector pointing toward maximum increase
- **Directional derivatives:** Rate in any direction
- **Optimization:** Critical points and second derivative test
- **Lagrange multipliers:** Constrained optimization
- **Multiple integrals:** Volume, mass, and other applications
- **Coordinate systems:** Cartesian, polar, cylindrical, spherical
