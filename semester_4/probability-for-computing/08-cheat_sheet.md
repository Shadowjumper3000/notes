This cheatsheet provides a clear overview of the main topics, problem types, and solution techniques you'll encounter in the final exam. It includes examples, identification tips, and step-by-step guides.

---

## 📐 1. Bayesian Network Factorization

### 🧠 **Problem Type:** Factorization Structure of BNs

### 🔍 **How to Identify:**
- Keywords: "Which term is (not) part of the factorization", "DAG", "Bayesian Network", or expressions like $$P(A)P(B|A)P(C|B,A)$$

---

### 🧪 **Example Problem:**
**Q:** Which of the following is *not* a valid term in the factorization of the BN?

- A. $$P(A)$$  
- B. $$P(B|A)$$  
- C. $$P(C|B,A)$$  
- D. $$P(D|C,A,B)$$

---

### ✅ **Solution Steps:**

1. **Understand the DAG Structure:**
   - Nodes represent random variables.
   - Edges represent direct dependencies (i.e., parents).

2. **Factorization Rule:**
   For any BN over variables $$X_1, X_2, ..., X_n$$:
   $$
   P(X_1, X_2, ..., X_n) = \prod_{i=1}^n P(X_i \mid \text{Parents}(X_i))
   $$

3. **Apply Rule:**
   - If a node has no parents: use $$P(X)$$.
   - If a node has parents: use $$P(X \mid \text{Parents}(X))$$.
   - Ensure each conditional matches the parent structure of the DAG.

4. **Invalid terms** condition on variables that are *not* parents of the node.

---

## 🔗 2. Conditional Independence

### 🧠 **Problem Type:** d-separation and Conditional Independence

### 🔍 **How to Identify:**
- Look for symbols like $$\perp\!\!\!\perp$$
- Questions ask: "Which of the following independences holds?"

---

### 🧪 **Example Problem:**
**Q:** Which of the following is guaranteed to hold?

- A. $$A \perp\!\!\!\perp B$$  
- B. $$A \perp\!\!\!\perp D \mid E$$  
- C. $$D \perp\!\!\!\perp I \mid \{E, G\}$$  
- D. None of the others

---

### ✅ **Solution Steps:**

1. **Use d-Separation:**
   - A path is blocked if at least one of the following holds:
     - Chain: $$A \rightarrow B \rightarrow C$$ blocked by conditioning on $$B$$.
     - Fork: $$A \leftarrow B \rightarrow C$$ blocked by conditioning on $$B$$.
     - Collider: $$A \rightarrow B \leftarrow C$$ *only unblocked* if you **condition on the collider or its descendants**.

2. **Walk through each path** and check if conditioning blocks or opens the path.

3. If all paths between two nodes are blocked, they are conditionally independent given the conditioning set.

---

## 🎯 3. Sampling Methods

Sampling methods help estimate probabilities in complex Bayesian networks where exact inference is infeasible.

---

### 🧪 **Key Definitions:**

- **Prior Sampling:** Samples entire network from the joint.
- **Rejection Sampling:** Samples from the prior and rejects those that don't match the evidence.
- **Likelihood Weighting:** Samples only non-evidence variables and weights each sample by the likelihood of the evidence.

---

### ✅ **3.1 Rejection Sampling**

#### **Goal:** Estimate $$P(X \mid E = e)$$ by generating samples from the joint distribution and rejecting those where $$E \ne e$$.

#### **Steps:**
1. Sample full assignment of all variables from BN using the prior.
2. If the sample agrees with evidence $$E = e$$, keep it; otherwise, reject it.
3. Compute the fraction:
   $$
   P(X = x \mid E = e) \approx \frac{\text{\# of samples with } X = x \text{ and } E = e}{\text{\# of samples with } E = e}
   $$

#### **Pros:** Simple  
#### **Cons:** Inefficient when evidence is rare

---

### ✅ **3.2 Likelihood Weighting**

#### **Goal:** Estimate $$P(X \mid E = e)$$ more efficiently by avoiding rejection.

#### **Steps:**

1. Fix evidence variables $$E = e$$ in each sample.
2. Sample the remaining variables from the BN.
3. Compute a **weight** for each sample:  
   $$
   w = \prod_{i \in E} P(e_i \mid \text{Parents}(E_i))
   $$
4. Estimate:
   $$
   P(X = x \mid E = e) \approx \frac{\sum_{i: x_i = x} w_i}{\sum w_i}
   $$

#### **Example:**

| Sample | A  | B  | D = +d (evidence) | Weight |
|--------|----|----|-------------------|--------|
| 1      | +a | +b | +d                | 0.8    |
| 2      | -a | +b | +d                | 0.6    |
| 3      | +a | -b | +d                | 0.4    |

**Estimate:**  
$$
P(+a \mid +d) = \frac{0.8 + 0.4}{0.8 + 0.6 + 0.4} = \frac{1.2}{1.8} = 0.67
$$

#### **Pros:** Efficient  
#### **Cons:** High variance when many evidence variables

---

## 📨 4. Naive Bayes Classification

### 🧠 **Problem Type:** Classifying samples or estimating probabilities using a Naive Bayes model.

---

### 🔍 **How to Identify:**
- References to spam filters, classifying emails, estimating $$P(Y \mid X_1, X_2, ...)$$

---

### 📘 **Theory:**

Naive Bayes assumes features are conditionally independent given the class:

$$
P(Y \mid X_1, ..., X_n) \propto P(Y) \prod_{i=1}^n P(X_i \mid Y)
$$

**With Laplace Smoothing (k):**
$$
P(X_i = x \mid Y = y) = \frac{N_{x,y} + k}{N_y + k \cdot V}
$$
Where:
- $$N_{x,y}$$: count of $$X_i = x$$ when $$Y = y$$
- $$N_y$$: total count of $$Y = y$$
- $$V$$: number of possible values of $$X_i$$

---

### 🛠 **Example Problem:**
You are given 3 spam and 2 ham emails. Word counts:
- "gold" appears only in spam.
- Classify the email containing just "gold".

### ✅ **Steps:**
1. Compute:
   - $$P(\text{spam}) = \frac{3}{5}$$
   - $$P(\text{ham}) = \frac{2}{5}$$
2. Use MLE (no smoothing):
   - $$P(\text{"gold"} \mid \text{spam}) = \frac{1}{3}$$
   - $$P(\text{"gold"} \mid \text{ham}) = 0$$ → classifier predicts spam (zero in ham)

---

### 🧮 **With Smoothing:**
If using Laplace smoothing:
$$
P(\text{"gold"} \mid \text{ham}) = \frac{0 + 1}{\text{total words in ham} + V}
$$

---

## 📊 5. CPT Size and Parameter Counting

### 🧠 **Problem Type:** How many parameters or rows in a CPT?

---

### 🔍 **How to Identify:**
- "How many entries are needed..." or "How many parameters define..."

---

### ✅ **Steps:**
1. Let node $$X$$ have $$r$$ possible values.
2. Let it have $$k$$ parents, each with $$v$$ values.
3. Then CPT has $$v^k \cdot (r - 1)$$ independent parameters.

---

### 🧪 **Example:**
- Node $$X$$ has 4 values.
- It has 2 binary parents: $$2^2 = 4$$ combinations.
- Parameters: $$4 \cdot (4 - 1) = 12$$

---

## ⛓️ 6. Markov Chains

### 🧠 **Problem Type:** Stationary distribution, classification of states

---

### ✅ **Stationary Distribution:**
For transition matrix $$P$$:
$$
\pi = \pi P, \quad \sum_i \pi_i = 1
$$

Solve this linear system to find the stationary distribution.

---

### 🛠 **Example:**

Given:  
$$
P = \begin{bmatrix}
0.6 & 0.4 \\
0.2 & 0.8
\end{bmatrix}
$$

Solve:
$$
\pi_1 = 0.6 \pi_1 + 0.2 \pi_2 \\
\pi_2 = 0.4 \pi_1 + 0.8 \pi_2 \\
\pi_1 + \pi_2 = 1
$$

Solving gives:  
$$
\pi = \left(\frac{1}{3}, \frac{2}{3} \right)
$$

---

## ⏳ 7. Poisson Process & Queuing

### 🧠 **Problem Type:** Arrival rates, service rates, M/M/1 queue metrics

---

### ✅ **Common Formulas:**

- **Utilization:** $$\rho = \frac{\lambda}{\mu}$$
- **Probability of k customers in system:**
  $$
  P(k) = (1 - \rho) \cdot \rho^k
  $$
- **Expected time until nth arrival in Poisson(λ):**
  $$
  E[T_n] = \frac{n}{\lambda}
  $$

---

### 🛠 **Example:**

λ = 10 calls/hour  
Find expected time until 4th call:

$$
E[T_4] = \frac{4}{10} = 0.4 \text{ hours} = 24 \text{ minutes}
$$

---

If you’d like this as a downloadable `.md` file, I can export it directly.
