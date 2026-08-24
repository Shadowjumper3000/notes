# Logarithms

**Tags:** #concept #math #computerscience
**Related:** [[Algorithm Analysis]], [[Binary Search]], [[Bayes' Theorem]]

## Definition

The **logarithm** is the inverse operation of exponentiation. For $b > 0$, $b \neq 1$, and $x > 0$:

$$
y = \log_b(x) \iff b^y = x
$$

where:
- $b$ is the **base**
- $x$ is the **argument** (must be positive for real logarithms)
- $y$ is the **logarithm** (the exponent)

### Common Bases

| Base | Notation | Name | Use Case |
|---|---|---|---|
| $2$ | $\log_2(x)$ or $\lg(x)$ | Binary logarithm | Computer science (bits, divide-and-conquer) |
| $e$ | $\ln(x)$ or $\log_e(x)$ | Natural logarithm | Calculus, physics, continuous growth |
| $10$ | $\log_{10}(x)$ | Common logarithm | Engineering, decibels, pH scale |
| $b$ (general) | $\log_b(x)$ | — | Mathematical generality |

## Fundamental Properties

### Product Rule

$$
\log_b(xy) = \log_b(x) + \log_b(y)
$$

### Quotient Rule

$$
\log_b\left(\frac{x}{y}\right) = \log_b(x) - \log_b(y)
$$

### Power Rule

$$
\log_b(x^k) = k \log_b(x)
$$

### Change of Base

Any logarithm can be expressed in terms of any other base:

$$
\log_a(x) = \frac{\log_b(x)}{\log_b(a)}
$$

This is essential in computing: since most languages provide only $\ln$ and $\log_{10}$:

$$
\log_2(x) = \frac{\ln(x)}{\ln(2)}
$$

### Special Values

$$
\log_b(1) = 0, \quad \log_b(b) = 1, \quad \log_b\left(\frac{1}{x}\right) = -\log_b(x)
$$

## Relationship to Exponentials

The logarithm and exponential are inverses:

$$
\log_b(b^x) = x, \quad b^{\log_b(x)} = x
$$

The derivative and integral are:

$$
\frac{d}{dx} \ln(x) = \frac{1}{x}, \quad \int \frac{1}{x} \, dx = \ln|x| + C
$$

For an arbitrary base:

$$
\frac{d}{dx} \log_b(x) = \frac{1}{x \ln(b)}
$$

## Binary Logarithms in Computer Science

### Divide-and-Conquer Recurrence

Many algorithms halve the problem size at each step. If the base case is size $1$, the number of divisions from size $N$ is $k$ where:

$$
1 = \frac{N}{2^k} \implies 2^k = N \implies k = \log_2 N
$$

### Master Theorem

For recurrences of the form $T(n) = aT(n/b) + f(n)$, the solution often involves $\log_b(n)$. Three common cases:

1. **$f(n) \ll n^{\log_b a}$:** $T(n) = \Theta(n^{\log_b a})$
2. **$f(n) \approx n^{\log_b a}$:** $T(n) = \Theta(n^{\log_b a} \log n)$
3. **$f(n) \gg n^{\log_b a}$:** $T(n) = \Theta(f(n))$

### Stirling's Approximation

Factorials and logarithms are deeply connected:

$$
\ln(n!) = n \ln n - n + O(\log n)
$$

This is critical for analyzing sorting lower bounds and combinatorial algorithms.

## Logarithmic Complexity Classes

| Class | Description | Example |
|---|---|---|
| $O(1)$ | Constant | Array access |
| $O(\log n)$ | Logarithmic | Binary search, heap ops |
| $O(n \log n)$ | Linearithmic | Merge sort, FFT |
| $O(\log \log n)$ | Double logarithmic | Interpolation search |
| $O((\log n)^k)$ | Polylogarithmic | Parallel algorithms |

The relationship between these classes is:

$$
O(1) \subset O(\log \log n) \subset O(\log n) \subset O(\sqrt{n}) \subset O(n) \subset O(n \log n)
$$

## Information Theory and Entropy

Claude Shannon's **entropy** measures the average information content of a random variable:

$$
H(X) = -\sum_{i=1}^n P(x_i) \log_2 P(x_i)
$$

measured in **bits** (base 2). This is the expected number of bits needed to optimally encode the outcomes. Key properties:

- $H(X) \ge 0$, with equality iff one outcome is certain.
- $H(X) \le \log_2 n$, with equality iff all outcomes are equally likely (uniform distribution).

**Cross-entropy** between two distributions $P$ and $Q$:

$$
H(P, Q) = -\sum_x P(x) \log_2 Q(x)
$$

**KL divergence** measures the information lost when $Q$ approximates $P$:

$$
D_{\text{KL}}(P \parallel Q) = \sum_x P(x) \log_2 \frac{P(x)}{Q(x)} = H(P, Q) - H(P)
$$

### Self-Information

The **self-information** (or surprisal) of an event $x$ is:

$$
I(x) = -\log_2 P(x)
$$

A low-probability event has high self-information. Entropy is the expected self-information.

## Log-Odds in Bayesian Inference

The **log-odds** form of [[Bayes' Theorem]]:

$$
\log \frac{P(A \mid B)}{P(\lnot A \mid B)} = \log \frac{P(B \mid A)}{P(B \mid \lnot A)} + \log \frac{P(A)}{P(\lnot A)}
$$

The log-likelihood ratio is additive, which simplifies sequential Bayesian updating.

## Relationship to Other Notes

- [[Algorithm Analysis]]: Logarithmic complexity arises from divide-and-conquer; Stirling's approximation uses logs to analyze factorial runtimes.
- [[Binary Search]]: The canonical $O(\log n)$ algorithm.
- [[Bayes' Theorem]]: Log-odds form simplifies Bayesian updates; entropy measures information content.
- [[Singular Value Decomposition]]: Matrix rank and singular value decay are often plotted on log-log scales.

## References

- Shannon, C. E. (1948). "A Mathematical Theory of Communication." *Bell System Technical Journal*, 27(3), 379-423.
- Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2009). *Introduction to Algorithms*. MIT Press.
- Cover, T. M., & Thomas, J. A. (2006). *Elements of Information Theory*. Wiley.
