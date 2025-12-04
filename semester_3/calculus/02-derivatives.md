# Derivatives and Differentiation

## Introduction to Derivatives

The **derivative** of a function measures the rate of change of the function with respect to its input.

### Geometric Interpretation
The derivative at a point gives the **slope of the tangent line** to the curve at that point.

### Physical Interpretation
If $s(t)$ represents position, then $s'(t)$ represents **velocity**.

---

## Definition of the Derivative

### Limit Definition

$$
f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}
$$

### Alternative Form

$$
f'(a) = \lim_{x \to a} \frac{f(x) - f(a)}{x - a}
$$

---

## Notation

Multiple notations for derivatives:

1. **Leibniz:** $\frac{df}{dx}$, $\frac{d}{dx}f(x)$
2. **Lagrange:** $f'(x)$, $f''(x)$, $f'''(x)$
3. **Newton:** $\dot{y}$, $\ddot{y}$
4. **Euler:** $D_x f$

---

## Basic Differentiation Rules

### Power Rule
$$
\frac{d}{dx}(x^n) = nx^{n-1}
$$

**Example:**
$$
\frac{d}{dx}(x^5) = 5x^4
$$

### Constant Rule
$$
\frac{d}{dx}(c) = 0
$$

### Constant Multiple Rule
$$
\frac{d}{dx}[cf(x)] = c \cdot f'(x)
$$

### Sum/Difference Rule
$$
\frac{d}{dx}[f(x) \pm g(x)] = f'(x) \pm g'(x)
$$

---

## Derivatives of Common Functions

### Exponential Functions
$$
\frac{d}{dx}(e^x) = e^x
$$

$$
\frac{d}{dx}(a^x) = a^x \ln a
$$

### Logarithmic Functions
$$
\frac{d}{dx}(\ln x) = \frac{1}{x}
$$

$$
\frac{d}{dx}(\log_a x) = \frac{1}{x \ln a}
$$

### Trigonometric Functions
$$
\frac{d}{dx}(\sin x) = \cos x
$$

$$
\frac{d}{dx}(\cos x) = -\sin x
$$

$$
\frac{d}{dx}(\tan x) = \sec^2 x
$$

$$
\frac{d}{dx}(\cot x) = -\csc^2 x
$$

$$
\frac{d}{dx}(\sec x) = \sec x \tan x
$$

$$
\frac{d}{dx}(\csc x) = -\csc x \cot x
$$

### Inverse Trigonometric Functions
$$
\frac{d}{dx}(\arcsin x) = \frac{1}{\sqrt{1-x^2}}
$$

$$
\frac{d}{dx}(\arccos x) = -\frac{1}{\sqrt{1-x^2}}
$$

$$
\frac{d}{dx}(\arctan x) = \frac{1}{1+x^2}
$$

### Hyperbolic Functions
$$
\frac{d}{dx}(\sinh x) = \cosh x
$$

$$
\frac{d}{dx}(\cosh x) = \sinh x
$$

$$
\frac{d}{dx}(\tanh x) = \text{sech}^2 x
$$

---

## Advanced Differentiation Rules

### Product Rule
$$
\frac{d}{dx}[f(x) \cdot g(x)] = f'(x)g(x) + f(x)g'(x)
$$

**Example:**
$$
\frac{d}{dx}[x^2 \sin x] = 2x \sin x + x^2 \cos x
$$

### Quotient Rule
$$
\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}
$$

**Example:**
$$
\frac{d}{dx}\left[\frac{x^2}{x+1}\right] = \frac{2x(x+1) - x^2(1)}{(x+1)^2} = \frac{x^2 + 2x}{(x+1)^2}
$$

### Chain Rule
$$
\frac{d}{dx}[f(g(x))] = f'(g(x)) \cdot g'(x)
$$

**Alternative notation:**
$$
\frac{dy}{dx} = \frac{dy}{du} \cdot \frac{du}{dx}
$$

**Example:**
$$
\frac{d}{dx}[\sin(x^2)] = \cos(x^2) \cdot 2x = 2x\cos(x^2)
$$

---

## Implicit Differentiation

For equations not solved for $y$, differentiate both sides with respect to $x$:

**Example:**
$$
x^2 + y^2 = 25
$$

Differentiating:
$$
2x + 2y\frac{dy}{dx} = 0
$$

$$
\frac{dy}{dx} = -\frac{x}{y}
$$

---

## Logarithmic Differentiation

Useful for products, quotients, and powers involving variables.

**Steps:**
1. Take natural log of both sides
2. Use log properties to simplify
3. Differentiate implicitly
4. Solve for $\frac{dy}{dx}$

**Example:**
$$
y = x^x
$$

$$
\ln y = x \ln x
$$

$$
\frac{1}{y}\frac{dy}{dx} = \ln x + 1
$$

$$
\frac{dy}{dx} = y(\ln x + 1) = x^x(\ln x + 1)
$$

---

## Higher-Order Derivatives

### Second Derivative
$$
f''(x) = \frac{d^2f}{dx^2} = \frac{d}{dx}[f'(x)]
$$

**Physical meaning:** Acceleration (if $f$ is position)

### Third Derivative
$$
f'''(x) = \frac{d^3f}{dx^3}
$$

**Physical meaning:** Jerk (rate of change of acceleration)

### nth Derivative
$$
f^{(n)}(x) = \frac{d^nf}{dx^n}
$$

---

## Derivatives of Parametric Equations

For parametric equations $x = x(t)$, $y = y(t)$:

$$
\frac{dy}{dx} = \frac{dy/dt}{dx/dt} = \frac{y'(t)}{x'(t)}
$$

### Second Derivative
$$
\frac{d^2y}{dx^2} = \frac{d}{dx}\left(\frac{dy}{dx}\right) = \frac{d/dt(dy/dx)}{dx/dt}
$$

---

## Related Rates

When two or more quantities are related and change with time, their rates of change are related by the chain rule.

**Strategy:**
1. Identify given rates and the rate to find
2. Write an equation relating the quantities
3. Differentiate both sides with respect to time
4. Substitute known values and solve

**Example:**
A ladder 10m long leans against a wall. If the bottom slides away at 2 m/s, how fast is the top sliding down when the bottom is 6m from the wall?

Let $x$ = distance from wall (bottom), $y$ = height on wall (top)
$$
x^2 + y^2 = 100
$$

$$
2x\frac{dx}{dt} + 2y\frac{dy}{dt} = 0
$$

When $x = 6$: $y = 8$
$$
2(6)(2) + 2(8)\frac{dy}{dt} = 0
$$

$$
\frac{dy}{dt} = -\frac{24}{16} = -1.5 \text{ m/s}
$$

---

## Linearization and Differentials

### Linear Approximation
$$
L(x) = f(a) + f'(a)(x - a)
$$

Near $x = a$, $f(x) \approx L(x)$

### Differentials
$$
dy = f'(x)dx
$$

Used to approximate changes:
$$
\Delta y \approx dy = f'(x)\Delta x
$$

---

## Mean Value Theorem

If $f$ is continuous on $[a,b]$ and differentiable on $(a,b)$, then there exists $c \in (a,b)$ such that:
$$
f'(c) = \frac{f(b) - f(a)}{b - a}
$$

**Interpretation:** At some point, the instantaneous rate equals the average rate.

---

## Rolle's Theorem

If $f$ is continuous on $[a,b]$, differentiable on $(a,b)$, and $f(a) = f(b)$, then there exists $c \in (a,b)$ such that:
$$
f'(c) = 0
$$

---

## Derivatives and Function Behavior

### Increasing/Decreasing Test
- If $f'(x) > 0$ on an interval, $f$ is **increasing**
- If $f'(x) < 0$ on an interval, $f$ is **decreasing**

### Critical Points
Points where $f'(x) = 0$ or $f'(x)$ does not exist.

### First Derivative Test
For a critical point $c$:
- If $f'$ changes from + to -, $f$ has a **local maximum** at $c$
- If $f'$ changes from - to +, $f$ has a **local minimum** at $c$
- If $f'$ doesn't change sign, $c$ is not an extremum

### Second Derivative Test
For a critical point $c$ where $f'(c) = 0$:
- If $f''(c) > 0$, $f$ has a **local minimum** at $c$ (concave up)
- If $f''(c) < 0$, $f$ has a **local maximum** at $c$ (concave down)
- If $f''(c) = 0$, test is inconclusive

### Concavity
- If $f''(x) > 0$, $f$ is **concave up** (shaped like ∪)
- If $f''(x) < 0$, $f$ is **concave down** (shaped like ∩)

### Inflection Points
Points where concavity changes; $f''(x) = 0$ or undefined.

---

## Common Derivative Patterns

### Polynomial
$$
\frac{d}{dx}(a_nx^n + \cdots + a_1x + a_0) = na_nx^{n-1} + \cdots + a_1
$$

### Exponential with Chain Rule
$$
\frac{d}{dx}(e^{u(x)}) = e^{u(x)} \cdot u'(x)
$$

### Trig with Chain Rule
$$
\frac{d}{dx}[\sin(u(x))] = \cos(u(x)) \cdot u'(x)
$$

---

## Summary

- Derivatives measure instantaneous rate of change
- Multiple rules exist for different function types
- Chain rule is essential for composite functions
- Implicit differentiation handles non-explicit functions
- Derivatives reveal function behavior (increasing/decreasing, concavity)
- Applications include related rates, optimization, and approximation
