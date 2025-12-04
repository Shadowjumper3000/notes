# Applications of Derivatives

## Optimization Problems

**Optimization** involves finding maximum or minimum values of a function.

### Strategy for Optimization

1. **Understand the problem** and identify what to optimize
2. **Draw a diagram** if applicable
3. **Define variables** and identify constraints
4. **Express the quantity to optimize** as a function of one variable
5. **Find the domain** of the function
6. **Take the derivative** and find critical points
7. **Test critical points** and endpoints
8. **Answer the question** with proper units

---

### Example: Maximizing Area

Find the dimensions of a rectangle with perimeter 100m that maximizes area.

**Solution:**
- Let length = $x$, width = $y$
- Constraint: $2x + 2y = 100 \implies y = 50 - x$
- Area: $A = xy = x(50-x) = 50x - x^2$
- Domain: $0 < x < 50$
- Derivative: $A' = 50 - 2x$
- Critical point: $50 - 2x = 0 \implies x = 25$
- Second derivative: $A'' = -2 < 0$ (maximum)
- Dimensions: $25m \times 25m$ (square)

---

### Example: Minimizing Cost

A cylindrical can must hold 1000 cm³. Find dimensions that minimize surface area.

**Solution:**
- Volume: $\pi r^2 h = 1000 \implies h = \frac{1000}{\pi r^2}$
- Surface area: $S = 2\pi r^2 + 2\pi rh$
- Substitute: $S(r) = 2\pi r^2 + 2\pi r \cdot \frac{1000}{\pi r^2} = 2\pi r^2 + \frac{2000}{r}$
- Derivative: $S'(r) = 4\pi r - \frac{2000}{r^2}$
- Critical point: $4\pi r = \frac{2000}{r^2} \implies r^3 = \frac{500}{\pi} \implies r = \sqrt[3]{\frac{500}{\pi}}$
- Height: $h = \frac{1000}{\pi r^2} = 2r$

---

## Curve Sketching

A systematic approach to graphing functions using calculus.

### Steps for Curve Sketching

1. **Domain:** Find where $f(x)$ is defined
2. **Intercepts:**
   - $y$-intercept: $f(0)$
   - $x$-intercepts: Solve $f(x) = 0$
3. **Symmetry:**
   - Even: $f(-x) = f(x)$ (symmetric about $y$-axis)
   - Odd: $f(-x) = -f(x)$ (symmetric about origin)
4. **Asymptotes:**
   - Vertical: Where denominator = 0
   - Horizontal: $\lim_{x \to \pm\infty} f(x)$
   - Oblique: If degree(numerator) = degree(denominator) + 1
5. **First Derivative:** Find $f'(x)$
   - Critical points: $f'(x) = 0$ or undefined
   - Increasing/decreasing intervals
   - Local extrema
6. **Second Derivative:** Find $f''(x)$
   - Inflection points: $f''(x) = 0$ or undefined
   - Concavity intervals
7. **Sketch:** Combine all information

---

### Example: Sketch $f(x) = \frac{x^2}{x^2-4}$

1. **Domain:** $x \neq \pm 2$
2. **Intercepts:** $(0,0)$
3. **Symmetry:** Even function
4. **Asymptotes:**
   - Vertical: $x = 2$, $x = -2$
   - Horizontal: $\lim_{x \to \infty} \frac{x^2}{x^2-4} = 1$, so $y = 1$
5. **First derivative:**
   $$
   f'(x) = \frac{2x(x^2-4) - x^2(2x)}{(x^2-4)^2} = \frac{-8x}{(x^2-4)^2}
   $$
   - Critical point: $x = 0$
   - Decreasing: $x > 0$ (excluding asymptotes)
   - Increasing: $x < 0$ (excluding asymptotes)
6. **Second derivative:** (compute for inflection points)
7. Sketch shows local maximum at origin, asymptotes at $x = \pm 2$ and $y = 1$

---

## Related Rates (Revisited)

### Common Related Rate Problems

#### 1. **Changing Volumes**

A spherical balloon is inflated at 50 cm³/s. How fast is the radius increasing when $r = 10$ cm?

**Solution:**
- Volume: $V = \frac{4}{3}\pi r^3$
- Differentiate: $\frac{dV}{dt} = 4\pi r^2 \frac{dr}{dt}$
- Given: $\frac{dV}{dt} = 50$, $r = 10$
- Solve: $50 = 4\pi(100)\frac{dr}{dt} \implies \frac{dr}{dt} = \frac{50}{400\pi} = \frac{1}{8\pi}$ cm/s

#### 2. **Moving Objects**

Two cars start from the same point. Car A travels north at 60 km/h, car B travels east at 80 km/h. How fast is the distance between them increasing after 2 hours?

**Solution:**
- Let $x$ = distance of B, $y$ = distance of A, $z$ = distance between
- $z^2 = x^2 + y^2$
- Differentiate: $2z\frac{dz}{dt} = 2x\frac{dx}{dt} + 2y\frac{dy}{dt}$
- After 2 hours: $x = 160$, $y = 120$, $z = 200$
- $2(200)\frac{dz}{dt} = 2(160)(80) + 2(120)(60)$
- $\frac{dz}{dt} = 100$ km/h

---

## Linear Approximation and Newton's Method

### Linear Approximation

Approximate $f(x)$ near $x = a$:
$$
f(x) \approx L(x) = f(a) + f'(a)(x-a)
$$

**Example:** Approximate $\sqrt{26}$

Use $f(x) = \sqrt{x}$, $a = 25$
$$
f'(x) = \frac{1}{2\sqrt{x}}, \quad f'(25) = \frac{1}{10}
$$

$$
\sqrt{26} \approx 5 + \frac{1}{10}(1) = 5.1
$$

(Actual: 5.099...)

---

### Newton's Method

Iterative method to find roots of $f(x) = 0$:
$$
x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
$$

**Example:** Find $\sqrt{2}$ (root of $f(x) = x^2 - 2$)

- $f'(x) = 2x$
- Start with $x_0 = 1$
- $x_1 = 1 - \frac{1^2-2}{2(1)} = 1 - \frac{-1}{2} = 1.5$
- $x_2 = 1.5 - \frac{1.5^2-2}{2(1.5)} = 1.5 - \frac{0.25}{3} \approx 1.4167$
- $x_3 \approx 1.4142$ (very close to $\sqrt{2}$)

---

## Extreme Value Theorem

If $f$ is continuous on $[a,b]$, then $f$ attains both absolute maximum and absolute minimum on $[a,b]$.

**To find absolute extrema:**
1. Find critical points in $(a,b)$
2. Evaluate $f$ at critical points and endpoints
3. Compare values

---

## Fermat's Theorem

If $f$ has a local extremum at $c$ and $f'(c)$ exists, then $f'(c) = 0$.

**Note:** Critical points are **candidates** for extrema, but not all critical points are extrema.

---

## L'Hôpital's Rule (Application)

For indeterminate forms $\frac{0}{0}$ or $\frac{\infty}{\infty}$:
$$
\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)}
$$

### Other Indeterminate Forms

Convert to $\frac{0}{0}$ or $\frac{\infty}{\infty}$:

- **$0 \cdot \infty$:** Rewrite as $\frac{0}{1/\infty}$ or $\frac{\infty}{1/0}$
- **$\infty - \infty$:** Factor or rationalize
- **$0^0$, $1^\infty$, $\infty^0$:** Take logarithm first

**Example:** $\lim_{x \to 0^+} x \ln x$ (form $0 \cdot \infty$)

Rewrite: $\lim_{x \to 0^+} \frac{\ln x}{1/x}$ (form $\frac{\infty}{\infty}$)

Apply L'Hôpital:
$$
\lim_{x \to 0^+} \frac{1/x}{-1/x^2} = \lim_{x \to 0^+} \frac{x^2}{-x} = \lim_{x \to 0^+} (-x) = 0
$$

---

## Elasticity of Demand

In economics, **elasticity** measures how quantity demanded responds to price changes:
$$
E = -\frac{p}{q} \cdot \frac{dq}{dp}
$$

- **Elastic** ($E > 1$): Demand is sensitive to price
- **Inelastic** ($E < 1$): Demand is insensitive to price
- **Unit elastic** ($E = 1$): Proportional response

---

## Marginal Analysis

### Marginal Cost
$$
MC = C'(x)
$$
Approximates the cost of producing one more unit.

### Marginal Revenue
$$
MR = R'(x)
$$
Approximates the revenue from selling one more unit.

### Profit Maximization
Profit $P(x) = R(x) - C(x)$ is maximized when:
$$
MR = MC \quad \text{or} \quad P'(x) = 0
$$

---

## Implicit Differentiation Applications

### Example: Related Rates with Implicit Functions

For the ellipse $\frac{x^2}{25} + \frac{y^2}{16} = 1$, if $\frac{dx}{dt} = 3$ when $(x,y) = (3,3.2)$, find $\frac{dy}{dt}$.

**Solution:**
Differentiate implicitly:
$$
\frac{2x}{25}\frac{dx}{dt} + \frac{2y}{16}\frac{dy}{dt} = 0
$$

Substitute values:
$$
\frac{2(3)}{25}(3) + \frac{2(3.2)}{16}\frac{dy}{dt} = 0
$$

Solve for $\frac{dy}{dt}$.

---

## Summary

- **Optimization** uses derivatives to find extrema in real-world problems
- **Curve sketching** combines multiple derivative tests for comprehensive graphs
- **Related rates** apply the chain rule to changing quantities
- **Linear approximation** and **Newton's method** provide numerical solutions
- **L'Hôpital's Rule** handles indeterminate limits
- Applications extend to economics, physics, and engineering
