# Limits and Continuity

## Introduction to Limits

A **limit** describes the value that a function approaches as the input approaches some value.

### Formal Definition

$$
\lim_{x \to a} f(x) = L
$$

means that for every $\epsilon > 0$, there exists a $\delta > 0$ such that:
$$
0 < |x - a| < \delta \implies |f(x) - L| < \epsilon
$$

---

## Computing Limits

### 1. Direct Substitution

If $f(x)$ is continuous at $x = a$, then:
$$
\lim_{x \to a} f(x) = f(a)
$$

**Example:**
$$
\lim_{x \to 2} (x^2 + 3x - 1) = 2^2 + 3(2) - 1 = 9
$$

---

### 2. Factoring

When direct substitution gives $\frac{0}{0}$, try factoring:

**Example:**
$$
\lim_{x \to 3} \frac{x^2 - 9}{x - 3} = \lim_{x \to 3} \frac{(x-3)(x+3)}{x-3} = \lim_{x \to 3} (x+3) = 6
$$

---

### 3. Rationalization

Multiply by the conjugate to eliminate radicals:

**Example:**
$$
\lim_{x \to 0} \frac{\sqrt{x+1} - 1}{x} = \lim_{x \to 0} \frac{(\sqrt{x+1} - 1)(\sqrt{x+1} + 1)}{x(\sqrt{x+1} + 1)}
$$
$$
= \lim_{x \to 0} \frac{x}{x(\sqrt{x+1} + 1)} = \lim_{x \to 0} \frac{1}{\sqrt{x+1} + 1} = \frac{1}{2}
$$

---

### 4. L'Hôpital's Rule

If $\lim_{x \to a} \frac{f(x)}{g(x)}$ gives $\frac{0}{0}$ or $\frac{\infty}{\infty}$:
$$
\lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)}
$$

**Example:**
$$
\lim_{x \to 0} \frac{\sin x}{x} = \lim_{x \to 0} \frac{\cos x}{1} = 1
$$

---

## One-Sided Limits

### Left-Hand Limit
$$
\lim_{x \to a^-} f(x) = L
$$
(approaching from the left)

### Right-Hand Limit
$$
\lim_{x \to a^+} f(x) = L
$$
(approaching from the right)

### Existence of Limit
$$
\lim_{x \to a} f(x) = L \iff \lim_{x \to a^-} f(x) = \lim_{x \to a^+} f(x) = L
$$

---

## Infinite Limits

### Vertical Asymptotes

$$
\lim_{x \to a} f(x) = \infty
$$
means $f(x)$ grows without bound as $x$ approaches $a$.

**Example:**
$$
\lim_{x \to 0^+} \frac{1}{x} = \infty, \quad \lim_{x \to 0^-} \frac{1}{x} = -\infty
$$

---

## Limits at Infinity

### Horizontal Asymptotes

$$
\lim_{x \to \infty} f(x) = L
$$
means $f(x)$ approaches $L$ as $x$ grows without bound.

**Example:**
$$
\lim_{x \to \infty} \frac{3x^2 + 2x + 1}{x^2 + 5} = \lim_{x \to \infty} \frac{3 + \frac{2}{x} + \frac{1}{x^2}}{1 + \frac{5}{x^2}} = 3
$$

---

## Special Limits

### Trigonometric Limits

$$
\lim_{x \to 0} \frac{\sin x}{x} = 1
$$

$$
\lim_{x \to 0} \frac{1 - \cos x}{x} = 0
$$

$$
\lim_{x \to 0} \frac{\tan x}{x} = 1
$$

### Exponential Limits

$$
\lim_{x \to 0} \frac{e^x - 1}{x} = 1
$$

$$
\lim_{x \to \infty} \left(1 + \frac{1}{x}\right)^x = e
$$

### Logarithmic Limits

$$
\lim_{x \to 0^+} x \ln x = 0
$$

$$
\lim_{x \to \infty} \frac{\ln x}{x} = 0
$$

---

## Continuity

### Definition

A function $f(x)$ is **continuous at $x = a$** if:

1. $f(a)$ is defined
2. $\lim_{x \to a} f(x)$ exists
3. $\lim_{x \to a} f(x) = f(a)$

---

### Types of Discontinuities

#### 1. Removable Discontinuity
The limit exists but doesn't equal the function value.

**Example:**
$$
f(x) = \frac{x^2 - 4}{x - 2}, \quad x \neq 2
$$

#### 2. Jump Discontinuity
Left and right limits exist but are not equal.

**Example:**
$$
f(x) = \begin{cases} 
x + 1 & x < 0 \\
x - 1 & x \geq 0
\end{cases}
$$

#### 3. Infinite Discontinuity
The function approaches infinity.

**Example:**
$$
f(x) = \frac{1}{x}
$$
at $x = 0$.

---

## Intermediate Value Theorem

If $f$ is continuous on $[a, b]$ and $N$ is between $f(a)$ and $f(b)$, then there exists $c \in (a, b)$ such that:
$$
f(c) = N
$$

**Application:** Proving existence of roots.

---

## Squeeze Theorem

If $g(x) \leq f(x) \leq h(x)$ near $x = a$ and:
$$
\lim_{x \to a} g(x) = \lim_{x \to a} h(x) = L
$$
then:
$$
\lim_{x \to a} f(x) = L
$$

**Example:**
$$
\lim_{x \to 0} x^2 \sin\left(\frac{1}{x}\right) = 0
$$

---

## Properties of Limits

Let $\lim_{x \to a} f(x) = L$ and $\lim_{x \to a} g(x) = M$. Then:

1. **Sum:** $\lim_{x \to a} [f(x) + g(x)] = L + M$
2. **Product:** $\lim_{x \to a} [f(x) \cdot g(x)] = L \cdot M$
3. **Quotient:** $\lim_{x \to a} \frac{f(x)}{g(x)} = \frac{L}{M}$ (if $M \neq 0$)
4. **Scalar Multiple:** $\lim_{x \to a} [c \cdot f(x)] = c \cdot L$
5. **Power:** $\lim_{x \to a} [f(x)]^n = L^n$

---

## Practical Problem-Solving Strategies

1. **Try direct substitution first**
2. **Factor and simplify** if you get $\frac{0}{0}$
3. **Rationalize** if radicals are present
4. **Use L'Hôpital's Rule** for indeterminate forms
5. **Check one-sided limits** for piecewise functions
6. **Consider special limits** (trig, exp, log)
7. **Apply theorems** (Squeeze, IVT) when appropriate

---

## Summary

- Limits form the foundation of calculus
- Continuity requires the limit to equal the function value
- Various techniques exist for computing limits
- Understanding discontinuities helps analyze function behavior
- Theorems like IVT and Squeeze Theorem are powerful tools
