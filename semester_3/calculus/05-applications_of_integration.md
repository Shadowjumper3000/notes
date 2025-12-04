# Applications of Integration

## Area Between Curves

### Vertical Strips

If $f(x) \geq g(x)$ on $[a,b]$:
$$
A = \int_a^b [f(x) - g(x)]\,dx
$$

**Example:** Area between $y = x^2$ and $y = x$ from $x = 0$ to $x = 1$:
$$
A = \int_0^1 (x - x^2)\,dx = \left[\frac{x^2}{2} - \frac{x^3}{3}\right]_0^1 = \frac{1}{2} - \frac{1}{3} = \frac{1}{6}
$$

### Horizontal Strips

If functions are given as $x = f(y)$ and $x = g(y)$ with $f(y) \geq g(y)$ on $[c,d]$:
$$
A = \int_c^d [f(y) - g(y)]\,dy
$$

---

## Volumes of Solids

### Disk Method

Rotating $y = f(x)$ about the $x$-axis from $a$ to $b$:
$$
V = \pi \int_a^b [f(x)]^2\,dx
$$

**Example:** Volume of sphere with radius $r$ (rotate $y = \sqrt{r^2-x^2}$):
$$
V = \pi \int_{-r}^r (r^2 - x^2)\,dx = \pi\left[r^2x - \frac{x^3}{3}\right]_{-r}^r = \frac{4\pi r^3}{3}
$$

### Washer Method

Rotating region between $y = f(x)$ and $y = g(x)$ about the $x$-axis:
$$
V = \pi \int_a^b \left([f(x)]^2 - [g(x)]^2\right)\,dx
$$

**Example:** Rotate region between $y = x$ and $y = x^2$ about $x$-axis from $x = 0$ to $x = 1$:
$$
V = \pi \int_0^1 (x^2 - x^4)\,dx = \pi\left[\frac{x^3}{3} - \frac{x^5}{5}\right]_0^1 = \pi\left(\frac{1}{3} - \frac{1}{5}\right) = \frac{2\pi}{15}
$$

### Shell Method

Rotating about a vertical axis at $x = L$:
$$
V = 2\pi \int_a^b (x - L) \cdot f(x)\,dx
$$

For rotation about the $y$-axis ($L = 0$):
$$
V = 2\pi \int_a^b x \cdot f(x)\,dx
$$

**Example:** Rotate $y = x^2$ about the $y$-axis from $x = 0$ to $x = 2$:
$$
V = 2\pi \int_0^2 x \cdot x^2\,dx = 2\pi \int_0^2 x^3\,dx = 2\pi\left[\frac{x^4}{4}\right]_0^2 = 2\pi \cdot 4 = 8\pi
$$

### Cross-Sectional Method

If cross-sections perpendicular to the $x$-axis have area $A(x)$:
$$
V = \int_a^b A(x)\,dx
$$

**Example:** Square cross-sections perpendicular to $x$-axis, base on $y = \sin x$ from $0$ to $\pi$:

Side length = $\sin x$, Area = $\sin^2 x$:
$$
V = \int_0^\pi \sin^2 x\,dx = \int_0^\pi \frac{1-\cos 2x}{2}\,dx = \frac{\pi}{2}
$$

---

## Arc Length

### Arc Length of $y = f(x)$

From $x = a$ to $x = b$:
$$
L = \int_a^b \sqrt{1 + [f'(x)]^2}\,dx
$$

**Example:** Arc length of $y = \frac{x^{3/2}}{3}$ from $x = 0$ to $x = 4$:

$$
f'(x) = \frac{1}{2}\sqrt{x}
$$

$$
L = \int_0^4 \sqrt{1 + \frac{x}{4}}\,dx = \int_0^4 \frac{\sqrt{4+x}}{2}\,dx
$$

Let $u = 4+x$:
$$
L = \frac{1}{2} \cdot \frac{2}{3}[u^{3/2}]_4^8 = \frac{1}{3}(16\sqrt{2} - 8) = \frac{8(2\sqrt{2} - 1)}{3}
$$

### Arc Length of Parametric Curves

For $x = x(t)$, $y = y(t)$, $t \in [\alpha, \beta]$:
$$
L = \int_\alpha^\beta \sqrt{[x'(t)]^2 + [y'(t)]^2}\,dt
$$

---

## Surface Area

### Surface of Revolution (about $x$-axis)

$$
S = 2\pi \int_a^b f(x)\sqrt{1 + [f'(x)]^2}\,dx
$$

**Example:** Surface area of sphere (rotate $y = \sqrt{r^2-x^2}$ about $x$-axis):

$$
f'(x) = \frac{-x}{\sqrt{r^2-x^2}}
$$

$$
S = 2\pi \int_{-r}^r \sqrt{r^2-x^2} \cdot \sqrt{1 + \frac{x^2}{r^2-x^2}}\,dx = 2\pi \int_{-r}^r r\,dx = 4\pi r^2
$$

---

## Work

**Work** done by a constant force $F$ over distance $d$:
$$
W = F \cdot d
$$

### Variable Force

If force varies with position:
$$
W = \int_a^b F(x)\,dx
$$

### Example: Spring (Hooke's Law)

Force: $F(x) = kx$ where $k$ is the spring constant.

Work to stretch spring from $x = 0$ to $x = b$:
$$
W = \int_0^b kx\,dx = \frac{kb^2}{2}
$$

### Example: Pumping Water

Pump water from a tank. Force to lift a slice at height $y$:
$$
F(y) = \rho g \cdot V(y)
$$

where $\rho$ is density, $g$ is gravity, $V(y)$ is volume of slice.

Distance to lift: $d(y)$

Total work:
$$
W = \int_{y_1}^{y_2} \rho g \cdot A(y) \cdot d(y)\,dy
$$

---

## Average Value

The **average value** of $f(x)$ on $[a,b]$:
$$
f_{\text{avg}} = \frac{1}{b-a} \int_a^b f(x)\,dx
$$

**Mean Value Theorem for Integrals:** There exists $c \in [a,b]$ such that:
$$
f(c) = f_{\text{avg}}
$$

**Example:** Average value of $f(x) = x^2$ on $[0,2]$:
$$
f_{\text{avg}} = \frac{1}{2} \int_0^2 x^2\,dx = \frac{1}{2} \cdot \frac{8}{3} = \frac{4}{3}
$$

---

## Center of Mass

### One-Dimensional System

For masses $m_1, m_2, \ldots, m_n$ at positions $x_1, x_2, \ldots, x_n$:
$$
\bar{x} = \frac{\sum m_i x_i}{\sum m_i}
$$

### Continuous Distribution

For a thin rod with density $\rho(x)$ on $[a,b]$:
$$
\bar{x} = \frac{\int_a^b x\rho(x)\,dx}{\int_a^b \rho(x)\,dx} = \frac{M_y}{M}
$$

where $M$ is total mass and $M_y$ is the moment about the origin.

### Two-Dimensional (Centroid)

For a region bounded by $f(x)$ and $g(x)$ on $[a,b]$:
$$
\bar{x} = \frac{1}{A} \int_a^b x[f(x) - g(x)]\,dx
$$

$$
\bar{y} = \frac{1}{A} \int_a^b \frac{[f(x)]^2 - [g(x)]^2}{2}\,dx
$$

where $A = \int_a^b [f(x) - g(x)]\,dx$

---

## Fluid Pressure and Force

**Hydrostatic pressure** at depth $h$:
$$
P = \rho g h
$$

where $\rho$ is fluid density, $g$ is gravitational acceleration.

### Force on a Vertical Surface

If a vertical plate is submerged with its top at depth $a$ and bottom at depth $b$, and has width $w(y)$ at depth $y$:
$$
F = \int_a^b \rho g y \cdot w(y)\,dy
$$

**Example:** Rectangular dam, width $w$, height $h$:
$$
F = \int_0^h \rho g y \cdot w\,dy = \rho g w \left[\frac{y^2}{2}\right]_0^h = \frac{\rho g w h^2}{2}
$$

---

## Probability and Expected Value

For a probability density function $f(x)$ on $[a,b]$:

### Properties
1. $f(x) \geq 0$
2. $\int_a^b f(x)\,dx = 1$

### Probability
$$
P(c \leq X \leq d) = \int_c^d f(x)\,dx
$$

### Expected Value (Mean)
$$
E[X] = \mu = \int_a^b x f(x)\,dx
$$

### Variance
$$
\text{Var}(X) = \sigma^2 = \int_a^b (x - \mu)^2 f(x)\,dx = E[X^2] - (E[X])^2
$$

---

## Moments and Centers of Mass (Detailed)

### Planar Lamina

For a thin plate with density $\delta(x,y)$:

**Mass:**
$$
M = \iint_R \delta(x,y)\,dA
$$

**Moments:**
$$
M_x = \iint_R y\delta(x,y)\,dA
$$

$$
M_y = \iint_R x\delta(x,y)\,dA
$$

**Center of mass:**
$$
\bar{x} = \frac{M_y}{M}, \quad \bar{y} = \frac{M_x}{M}
$$

---

## Economic Applications

### Consumer Surplus

$$
CS = \int_0^{q_0} [D(q) - p_0]\,dq
$$

where $D(q)$ is demand function, $p_0$ is equilibrium price, $q_0$ is equilibrium quantity.

### Producer Surplus

$$
PS = \int_0^{q_0} [p_0 - S(q)]\,dq
$$

where $S(q)$ is supply function.

---

## Summary

Integration applications include:
- **Geometric:** Area, volume, arc length, surface area
- **Physical:** Work, center of mass, fluid force
- **Probabilistic:** Expected value, variance
- **Economic:** Consumer and producer surplus

Each application follows a similar pattern:
1. Identify the quantity to accumulate
2. Set up a representative element
3. Write the integral
4. Evaluate
