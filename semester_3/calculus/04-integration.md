# Integration Techniques

## Introduction to Integration

**Integration** is the inverse operation of differentiation. It's used to find areas, volumes, and accumulations.

### Indefinite Integral (Antiderivative)

$$
\int f(x)\,dx = F(x) + C
$$

where $F'(x) = f(x)$ and $C$ is the constant of integration.

### Definite Integral

$$
\int_a^b f(x)\,dx = F(b) - F(a)
$$

Represents the **net area** between the curve and the x-axis from $a$ to $b$.

---

## Fundamental Theorem of Calculus

### Part 1

If $f$ is continuous on $[a,b]$ and $F(x) = \int_a^x f(t)\,dt$, then:
$$
F'(x) = f(x)
$$

### Part 2

If $F$ is an antiderivative of $f$ on $[a,b]$, then:
$$
\int_a^b f(x)\,dx = F(b) - F(a)
$$

---

## Basic Integration Formulas

### Power Rule
$$
\int x^n\,dx = \frac{x^{n+1}}{n+1} + C \quad (n \neq -1)
$$

$$
\int \frac{1}{x}\,dx = \ln|x| + C
$$

### Exponential Functions
$$
\int e^x\,dx = e^x + C
$$

$$
\int a^x\,dx = \frac{a^x}{\ln a} + C
$$

### Trigonometric Functions
$$
\int \sin x\,dx = -\cos x + C
$$

$$
\int \cos x\,dx = \sin x + C
$$

$$
\int \sec^2 x\,dx = \tan x + C
$$

$$
\int \csc^2 x\,dx = -\cot x + C
$$

$$
\int \sec x \tan x\,dx = \sec x + C
$$

$$
\int \csc x \cot x\,dx = -\csc x + C
$$

### Inverse Trigonometric
$$
\int \frac{1}{\sqrt{1-x^2}}\,dx = \arcsin x + C
$$

$$
\int \frac{1}{1+x^2}\,dx = \arctan x + C
$$

$$
\int \frac{1}{x\sqrt{x^2-1}}\,dx = \text{arcsec}\,|x| + C
$$

---

## Substitution Method (u-Substitution)

When the integrand has the form $f(g(x))g'(x)$, use substitution:

### Process
1. Choose $u = g(x)$
2. Compute $du = g'(x)\,dx$
3. Rewrite integral in terms of $u$
4. Integrate
5. Substitute back

### Example 1
$$
\int 2x\cos(x^2)\,dx
$$

Let $u = x^2$, $du = 2x\,dx$:
$$
\int \cos u\,du = \sin u + C = \sin(x^2) + C
$$

### Example 2
$$
\int \frac{x}{\sqrt{1-x^2}}\,dx
$$

Let $u = 1-x^2$, $du = -2x\,dx$:
$$
-\frac{1}{2}\int u^{-1/2}\,du = -\frac{1}{2} \cdot 2u^{1/2} + C = -\sqrt{1-x^2} + C
$$

### Definite Integrals with Substitution

Either:
1. Change limits: If $u = g(x)$, new limits are $u(a)$ and $u(b)$
2. Substitute back and use original limits

---

## Integration by Parts

Based on the product rule:
$$
\int u\,dv = uv - \int v\,du
$$

### Strategy (LIATE)
Choose $u$ in order of preference:
- **L**ogarithmic
- **I**nverse trigonometric
- **A**lgebraic
- **T**rigonometric
- **E**xponential

### Example 1
$$
\int x e^x\,dx
$$

Let $u = x$, $dv = e^x\,dx$:
- $du = dx$, $v = e^x$

$$
\int x e^x\,dx = xe^x - \int e^x\,dx = xe^x - e^x + C = e^x(x-1) + C
$$

### Example 2
$$
\int \ln x\,dx
$$

Let $u = \ln x$, $dv = dx$:
- $du = \frac{1}{x}dx$, $v = x$

$$
\int \ln x\,dx = x\ln x - \int x \cdot \frac{1}{x}\,dx = x\ln x - x + C
$$

### Example 3: Repeated Integration by Parts
$$
\int x^2 e^x\,dx
$$

Apply twice:
$$
= x^2e^x - 2\int xe^x\,dx = x^2e^x - 2(xe^x - e^x) + C = e^x(x^2 - 2x + 2) + C
$$

---

## Trigonometric Integrals

### Powers of Sine and Cosine

#### Case 1: $\int \sin^m x \cos^n x\,dx$ (odd power)

If $m$ or $n$ is odd, save one factor and convert the rest using $\sin^2 x + \cos^2 x = 1$.

**Example:**
$$
\int \sin^3 x\,dx = \int \sin x \sin^2 x\,dx = \int \sin x(1-\cos^2 x)\,dx
$$

Let $u = \cos x$, $du = -\sin x\,dx$:
$$
= -\int (1-u^2)\,du = -u + \frac{u^3}{3} + C = -\cos x + \frac{\cos^3 x}{3} + C
$$

#### Case 2: Both powers even

Use power-reducing formulas:
$$
\sin^2 x = \frac{1-\cos 2x}{2}, \quad \cos^2 x = \frac{1+\cos 2x}{2}
$$

### Powers of Tangent and Secant

#### $\int \tan^m x \sec^n x\,dx$

- If $n$ is even: Save $\sec^2 x$, convert rest with $\sec^2 x = 1 + \tan^2 x$
- If $m$ is odd: Save $\sec x \tan x$, convert rest with $\tan^2 x = \sec^2 x - 1$

**Example:**
$$
\int \tan^2 x\,dx = \int (\sec^2 x - 1)\,dx = \tan x - x + C
$$

---

## Trigonometric Substitution

For integrals containing:

### 1. $\sqrt{a^2 - x^2}$
Use $x = a\sin\theta$, $dx = a\cos\theta\,d\theta$

$$
\sqrt{a^2 - x^2} = a\cos\theta
$$

### 2. $\sqrt{a^2 + x^2}$
Use $x = a\tan\theta$, $dx = a\sec^2\theta\,d\theta$

$$
\sqrt{a^2 + x^2} = a\sec\theta
$$

### 3. $\sqrt{x^2 - a^2}$
Use $x = a\sec\theta$, $dx = a\sec\theta\tan\theta\,d\theta$

$$
\sqrt{x^2 - a^2} = a\tan\theta
$$

### Example
$$
\int \frac{1}{\sqrt{1-x^2}}\,dx
$$

Let $x = \sin\theta$, $dx = \cos\theta\,d\theta$:
$$
\int \frac{\cos\theta}{\sqrt{1-\sin^2\theta}}\,d\theta = \int \frac{\cos\theta}{\cos\theta}\,d\theta = \int d\theta = \theta + C = \arcsin x + C
$$

---

## Partial Fractions

For rational functions $\frac{P(x)}{Q(x)}$ where degree$(P) <$ degree$(Q)$:

### Steps
1. Factor the denominator $Q(x)$
2. Write as sum of partial fractions
3. Solve for coefficients
4. Integrate each term

### Types of Factors

#### Linear factors: $(ax + b)^k$
$$
\frac{A_1}{ax+b} + \frac{A_2}{(ax+b)^2} + \cdots + \frac{A_k}{(ax+b)^k}
$$

#### Quadratic factors: $(ax^2 + bx + c)^k$
$$
\frac{A_1x + B_1}{ax^2+bx+c} + \cdots + \frac{A_kx + B_k}{(ax^2+bx+c)^k}
$$

### Example
$$
\int \frac{1}{x^2-1}\,dx = \int \frac{1}{(x-1)(x+1)}\,dx
$$

Partial fractions:
$$
\frac{1}{(x-1)(x+1)} = \frac{A}{x-1} + \frac{B}{x+1}
$$

Solving: $1 = A(x+1) + B(x-1)$
- $x = 1$: $A = \frac{1}{2}$
- $x = -1$: $B = -\frac{1}{2}$

$$
\int \frac{1}{x^2-1}\,dx = \frac{1}{2}\int\frac{1}{x-1}\,dx - \frac{1}{2}\int\frac{1}{x+1}\,dx = \frac{1}{2}\ln|x-1| - \frac{1}{2}\ln|x+1| + C
$$

$$
= \frac{1}{2}\ln\left|\frac{x-1}{x+1}\right| + C
$$

---

## Improper Integrals

### Type 1: Infinite Limits
$$
\int_a^\infty f(x)\,dx = \lim_{b \to \infty} \int_a^b f(x)\,dx
$$

**Example:**
$$
\int_1^\infty \frac{1}{x^2}\,dx = \lim_{b \to \infty} \left[-\frac{1}{x}\right]_1^b = \lim_{b \to \infty} \left(-\frac{1}{b} + 1\right) = 1
$$

(Converges)

### Type 2: Discontinuous Integrand

If $f$ has a discontinuity at $c \in [a,b]$:
$$
\int_a^b f(x)\,dx = \lim_{t \to c^-} \int_a^t f(x)\,dx + \lim_{s \to c^+} \int_s^b f(x)\,dx
$$

**Example:**
$$
\int_0^1 \frac{1}{\sqrt{x}}\,dx = \lim_{t \to 0^+} \int_t^1 x^{-1/2}\,dx = \lim_{t \to 0^+} [2\sqrt{x}]_t^1 = 2
$$

(Converges)

---

## Numerical Integration

### Riemann Sums
$$
\int_a^b f(x)\,dx \approx \sum_{i=1}^n f(x_i^*)\Delta x
$$

where $\Delta x = \frac{b-a}{n}$

### Trapezoidal Rule
$$
\int_a^b f(x)\,dx \approx \frac{\Delta x}{2}[f(x_0) + 2f(x_1) + 2f(x_2) + \cdots + 2f(x_{n-1}) + f(x_n)]
$$

### Simpson's Rule
$$
\int_a^b f(x)\,dx \approx \frac{\Delta x}{3}[f(x_0) + 4f(x_1) + 2f(x_2) + 4f(x_3) + \cdots + 4f(x_{n-1}) + f(x_n)]
$$

(Requires $n$ to be even)

---

## Summary

- **Substitution** for composite functions
- **Integration by parts** for products
- **Trigonometric identities** for trig integrals
- **Trigonometric substitution** for radicals
- **Partial fractions** for rational functions
- **Improper integrals** require limits
- **Numerical methods** approximate integrals
