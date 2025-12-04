# 🔗 Conditional and Marginal Independence – Examples

This document illustrates **marginal independence** and **conditional independence** between random variables using clean, LaTeX-rendered probability equations.

---

## 📘 Definitions

- **Marginal Independence**:

  $$
  X \perp\!\!\!\perp Y \iff P(X, Y) = P(X) \cdot P(Y)
  $$

- **Conditional Independence**:

  $$
  X \perp\!\!\!\perp Y \mid Z \iff P(X, Y \mid Z) = P(X \mid Z) \cdot P(Y \mid Z)
  $$

---

## ✅ Example 1: Marginal Independence Holds

Given:

- $$P(X = 1) = \frac{1}{2}$$
- $$P(Y = 1) = \frac{1}{4}$$
- $$P(X = 1, Y = 1) = \frac{1}{8}$$

Check:

$$
P(X = 1) \cdot P(Y = 1) = \frac{1}{2} \cdot \frac{1}{4} = \frac{1}{8} = P(X = 1, Y = 1)
$$

✅ Therefore:

$$
X \perp\!\!\!\perp Y
$$

---

## ❌ Example 2: Marginal Independence Fails

Given:

- $$P(X = 1) = \frac{1}{2}$$
- $$P(Y = 1) = \frac{1}{2}$$
- $$P(X = 1, Y = 1) = \frac{1}{3}$$

Check:

$$
P(X = 1) \cdot P(Y = 1) = \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{4} \neq \frac{1}{3}
$$

❌ Therefore:

$$
X \not\!\perp\!\!\!\perp Y
$$

---

## ✅ Example 3: Conditional Independence Holds

Given:

- $$P(X = 1 \mid Z = 0) = \frac{1}{2}$$
- $$P(Y = 1 \mid Z = 0) = \frac{1}{4}$$

Then:

$$
P(X = 1, Y = 1 \mid Z = 0) = \frac{1}{2} \cdot \frac{1}{4} = \frac{1}{8}
$$

✅ Therefore:

$$
X \perp\!\!\!\perp Y \mid Z
$$

---

## ❌ Example 4: Conditional Independence Fails

Given:

- $$P(X = 1 \mid Z = 1) = \frac{1}{2}$$
- $$P(Y = 1 \mid Z = 1) = \frac{3}{4}$$
- $$P(X = 1, Y = 1 \mid Z = 1) = \frac{1}{2}$$

Check:

$$
P(X = 1 \mid Z = 1) \cdot P(Y = 1 \mid Z = 1) = \frac{1}{2} \cdot \frac{3}{4} = \frac{3}{8} \neq \frac{1}{2}
$$

❌ Therefore:

$$
X \not\!\perp\!\!\!\perp Y \mid Z
$$

---

## ✅ Example 5: Conditional Independence from a Table

Suppose the conditional probability table is:

| Z | X | Y | $$P(X, Y \mid Z)$$ |
|---|---|---|--------------------|
| 0 | 0 | 0 | $$\frac{1}{4}$$     |
| 0 | 0 | 1 | $$\frac{1}{4}$$     |
| 0 | 1 | 0 | $$\frac{1}{4}$$     |
| 0 | 1 | 1 | $$\frac{1}{4}$$     |

Compute marginals:

- $$P(X = x \mid Z = 0) = \frac{1}{2}$$
- $$P(Y = y \mid Z = 0) = \frac{1}{2}$$

Then:

$$
P(X = x, Y = y \mid Z = 0) = P(X = x \mid Z = 0) \cdot P(Y = y \mid Z = 0)
$$

✅ Therefore:

$$
X \perp\!\!\!\perp Y \mid Z
$$

---

## ✅ Example 6: Chain Structure

Structure:

$$
X \rightarrow Y \rightarrow Z
$$

Here:

- $$X \not\!\perp\!\!\!\perp Z$$
- $$X \perp\!\!\!\perp Z \mid Y$$

Explanation:

Knowing \(Y\) blocks the information flow from \(X\) to \(Z\). Without \(Y\), \(X\) and \(Z\) are dependent.

---

## ✅ Example 7: Fork Structure

Structure:

$$
Z \rightarrow X, \quad Z \rightarrow Y
$$

Here:

- $$X \not\!\perp\!\!\!\perp Y$$
- $$X \perp\!\!\!\perp Y \mid Z$$

Explanation:

The shared cause \(Z\) induces dependence between \(X\) and \(Y\), which disappears when conditioning on \(Z\).

---
