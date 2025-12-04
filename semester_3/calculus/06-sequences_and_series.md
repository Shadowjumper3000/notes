# Sequences and Series

## Sequences

A **sequence** is an ordered list of numbers: $\{a_n\}_{n=1}^{\infty} = a_1, a_2, a_3, \ldots$

### Limit of a Sequence

$$
\lim_{n \to \infty} a_n = L
$$

means that $a_n$ approaches $L$ as $n$ grows large.

**Definition:** For every $\epsilon > 0$, there exists $N$ such that for all $n > N$:
$$
|a_n - L| < \epsilon
$$

### Convergence and Divergence

- **Converges** if the limit exists and is finite
- **Diverges** otherwise (including oscillation or approaching infinity)

---

## Properties of Limits of Sequences

If $\lim_{n \to \infty} a_n = L$ and $\lim_{n \to \infty} b_n = M$:

1. $\lim_{n \to \infty} (a_n + b_n) = L + M$
2. $\lim_{n \to \infty} (ca_n) = cL$
3. $\lim_{n \to \infty} (a_n b_n) = LM$
4. $\lim_{n \to \infty} \frac{a_n}{b_n} = \frac{L}{M}$ (if $M \neq 0$)

---

## Common Sequence Limits

$$
\lim_{n \to \infty} \frac{1}{n^p} = 0 \quad (p > 0)
$$

$$
\lim_{n \to \infty} r^n = 0 \quad (|r| < 1)
$$

$$
\lim_{n \to \infty} r^n = \infty \quad (r > 1)
$$

$$
\lim_{n \to \infty} \left(1 + \frac{1}{n}\right)^n = e
$$

$$
\lim_{n \to \infty} \frac{a^n}{n!} = 0 \quad (\text{for any } a)
$$

---

## Monotonic Sequences

- **Increasing:** $a_{n+1} \geq a_n$ for all $n$
- **Decreasing:** $a_{n+1} \leq a_n$ for all $n$
- **Monotonic:** Either increasing or decreasing

**Monotonic Sequence Theorem:** Every bounded monotonic sequence converges.

---

## Series

A **series** is the sum of a sequence:
$$
\sum_{n=1}^{\infty} a_n = a_1 + a_2 + a_3 + \cdots
$$

### Partial Sums

$$
S_n = \sum_{k=1}^{n} a_k
$$

The series **converges** to $S$ if:
$$
\lim_{n \to \infty} S_n = S
$$

---

## Geometric Series

$$
\sum_{n=0}^{\infty} ar^n = a + ar + ar^2 + ar^3 + \cdots
$$

**Convergence:**
- If $|r| < 1$: Converges to $\frac{a}{1-r}$
- If $|r| \geq 1$: Diverges

**Example:**
$$
\sum_{n=0}^{\infty} \frac{1}{2^n} = \frac{1}{1 - 1/2} = 2
$$

---

## Harmonic Series

$$
\sum_{n=1}^{\infty} \frac{1}{n} = 1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \cdots
$$

**Diverges** (even though terms approach 0)

### p-Series

$$
\sum_{n=1}^{\infty} \frac{1}{n^p}
$$

- **Converges** if $p > 1$
- **Diverges** if $p \leq 1$

**Example:** $\sum \frac{1}{n^2}$ converges (Basel problem: sum = $\frac{\pi^2}{6}$)

---

## Convergence Tests

### Divergence Test (nth Term Test)

If $\lim_{n \to \infty} a_n \neq 0$, then $\sum a_n$ **diverges**.

**Note:** If $\lim_{n \to \infty} a_n = 0$, the test is **inconclusive**.

---

### Integral Test

If $f$ is continuous, positive, and decreasing on $[1,\infty)$ and $a_n = f(n)$:
$$
\sum_{n=1}^{\infty} a_n \text{ and } \int_1^{\infty} f(x)\,dx
$$
**both converge or both diverge**.

**Example:** Test $\sum \frac{1}{n^2}$

$$
\int_1^{\infty} \frac{1}{x^2}\,dx = \lim_{b \to \infty} \left[-\frac{1}{x}\right]_1^b = 1
$$

Integral converges, so series converges.

---

### Comparison Test

For series with positive terms:

**Direct Comparison:**
- If $0 \leq a_n \leq b_n$ and $\sum b_n$ converges, then $\sum a_n$ converges
- If $0 \leq b_n \leq a_n$ and $\sum b_n$ diverges, then $\sum a_n$ diverges

**Limit Comparison:**
If $a_n, b_n > 0$ and $\lim_{n \to \infty} \frac{a_n}{b_n} = c$ where $0 < c < \infty$:
- Both series converge or both diverge

---

### Ratio Test

$$
L = \lim_{n \to \infty} \left|\frac{a_{n+1}}{a_n}\right|
$$

- If $L < 1$: **Converges absolutely**
- If $L > 1$: **Diverges**
- If $L = 1$: **Inconclusive**

**Example:** Test $\sum \frac{n!}{n^n}$

$$
\frac{a_{n+1}}{a_n} = \frac{(n+1)!/(n+1)^{n+1}}{n!/n^n} = \frac{(n+1) \cdot n^n}{(n+1)^{n+1}} = \frac{n^n}{(n+1)^n} = \left(\frac{n}{n+1}\right)^n
$$

$$
L = \lim_{n \to \infty} \left(\frac{n}{n+1}\right)^n = \lim_{n \to \infty} \left(\frac{1}{1+1/n}\right)^n = \frac{1}{e} < 1
$$

Converges.

---

### Root Test

$$
L = \lim_{n \to \infty} \sqrt[n]{|a_n|}
$$

- If $L < 1$: **Converges absolutely**
- If $L > 1$: **Diverges**
- If $L = 1$: **Inconclusive**

---

### Alternating Series Test

For an **alternating series** $\sum_{n=1}^{\infty} (-1)^{n+1} b_n$ where $b_n > 0$:

If:
1. $b_{n+1} \leq b_n$ (decreasing)
2. $\lim_{n \to \infty} b_n = 0$

Then the series **converges**.

**Example:** Alternating harmonic series
$$
\sum_{n=1}^{\infty} \frac{(-1)^{n+1}}{n} = 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \cdots
$$

Converges (to $\ln 2$).

---

## Absolute vs Conditional Convergence

- **Absolutely convergent:** $\sum |a_n|$ converges
- **Conditionally convergent:** $\sum a_n$ converges but $\sum |a_n|$ diverges

**Theorem:** If $\sum |a_n|$ converges, then $\sum a_n$ converges.

---

## Power Series

A **power series** centered at $a$:
$$
\sum_{n=0}^{\infty} c_n(x-a)^n = c_0 + c_1(x-a) + c_2(x-a)^2 + \cdots
$$

### Radius of Convergence

Every power series has a **radius of convergence** $R$ such that:
- **Converges absolutely** for $|x-a| < R$
- **Diverges** for $|x-a| > R$
- **Test endpoints** separately

**Finding $R$:**
$$
\frac{1}{R} = \lim_{n \to \infty} \left|\frac{c_{n+1}}{c_n}\right| \quad \text{or} \quad \frac{1}{R} = \lim_{n \to \infty} \sqrt[n]{|c_n|}
$$

### Interval of Convergence

The set of all $x$ for which the series converges.

**Example:** $\sum_{n=1}^{\infty} \frac{x^n}{n}$

Ratio test:
$$
\lim_{n \to \infty} \left|\frac{x^{n+1}/(n+1)}{x^n/n}\right| = |x| \lim_{n \to \infty} \frac{n}{n+1} = |x|
$$

Converges for $|x| < 1$, so $R = 1$.

Test endpoints:
- $x = 1$: $\sum \frac{1}{n}$ diverges
- $x = -1$: $\sum \frac{(-1)^n}{n}$ converges

**Interval of convergence:** $[-1, 1)$

---

## Taylor and Maclaurin Series

### Taylor Series

For a function $f$ infinitely differentiable at $x = a$:
$$
f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!}(x-a)^n
$$

### Maclaurin Series

Taylor series centered at $a = 0$:
$$
f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(0)}{n!}x^n
$$

---

## Common Maclaurin Series

### Exponential
$$
e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
$$

### Sine
$$
\sin x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{(2n+1)!} = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots
$$

### Cosine
$$
\cos x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n}}{(2n)!} = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots
$$

### Geometric
$$
\frac{1}{1-x} = \sum_{n=0}^{\infty} x^n = 1 + x + x^2 + x^3 + \cdots \quad (|x| < 1)
$$

### Natural Logarithm
$$
\ln(1+x) = \sum_{n=1}^{\infty} \frac{(-1)^{n+1}x^n}{n} = x - \frac{x^2}{2} + \frac{x^3}{3} - \cdots \quad (|x| < 1)
$$

### Binomial
$$
(1+x)^k = \sum_{n=0}^{\infty} \binom{k}{n} x^n \quad (|x| < 1)
$$

where $\binom{k}{n} = \frac{k(k-1)(k-2)\cdots(k-n+1)}{n!}$

---

## Taylor's Theorem with Remainder

$$
f(x) = \sum_{n=0}^{N} \frac{f^{(n)}(a)}{n!}(x-a)^n + R_N(x)
$$

where $R_N(x)$ is the remainder.

### Lagrange Form of Remainder

$$
R_N(x) = \frac{f^{(N+1)}(c)}{(N+1)!}(x-a)^{N+1}
$$

for some $c$ between $a$ and $x$.

---

## Operations on Power Series

Within the interval of convergence:

### Addition/Subtraction
$$
\sum c_n x^n \pm \sum d_n x^n = \sum (c_n \pm d_n) x^n
$$

### Multiplication by Scalar
$$
k \sum c_n x^n = \sum (kc_n) x^n
$$

### Differentiation
$$
\frac{d}{dx} \sum_{n=0}^{\infty} c_n x^n = \sum_{n=1}^{\infty} nc_n x^{n-1}
$$

### Integration
$$
\int \sum_{n=0}^{\infty} c_n x^n\,dx = C + \sum_{n=0}^{\infty} \frac{c_n}{n+1} x^{n+1}
$$

---

## Applications

### Approximations

Use partial sums to approximate function values:
$$
e \approx 1 + 1 + \frac{1}{2!} + \frac{1}{3!} + \frac{1}{4!} = 2.7083\ldots
$$

### Solving Differential Equations

Power series solutions for differential equations.

### Evaluating Limits

$$
\lim_{x \to 0} \frac{\sin x - x}{x^3} = \lim_{x \to 0} \frac{(x - \frac{x^3}{6} + \cdots) - x}{x^3} = -\frac{1}{6}
$$

---

## Summary

- **Sequences:** Ordered lists; may converge or diverge
- **Series:** Sums of sequences; various convergence tests
- **Power series:** Functions as infinite polynomials
- **Taylor/Maclaurin series:** Represent functions as power series
- **Applications:** Approximation, solving equations, evaluating limits
