# Bayes' Theorem

**Tags:** #concept #math #probability #ml
**Related:** [[Naïve Bayes]], [[Vectors and Vector Spaces]]

## Definition

Bayes' Theorem (also called Bayes' Rule or Bayes' Formula) describes the probability of an event based on prior knowledge of conditions that might be related to the event. It is a direct consequence of the definition of conditional probability.

## Formula Derivation

Starting from the definition of conditional probability:

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad P(B \mid A) = \frac{P(A \cap B)}{P(A)}
$$

Since $P(A \cap B) = P(B \cap A)$, we equate:

$$
P(A \mid B) P(B) = P(B \mid A) P(A)
$$

Rearranging gives Bayes' Theorem:

$$
P(A \mid B) = \frac{P(B \mid A) P(A)}{P(B)}
$$

This is the simplest form. For a partition $\{A_i\}$ of the sample space, the **law of total probability** gives:

$$
P(B) = \sum_i P(B \mid A_i) P(A_i)
$$

leading to the extended form:

$$
P(A_i \mid B) = \frac{P(B \mid A_i) P(A_i)}{\sum_j P(B \mid A_j) P(A_j)}
$$

## Terminology

Each term in Bayes' Theorem has a specific name:

| Term | Notation | Meaning |
|---|---|---|
| **Posterior** | $P(A \mid B)$ | Probability of hypothesis $A$ after seeing evidence $B$ |
| **Prior** | $P(A)$ | Initial belief about $A$ before evidence |
| **Likelihood** | $P(B \mid A)$ | Probability of evidence $B$ given hypothesis $A$ |
| **Evidence** | $P(B)$ | Marginal probability of the evidence |

Bayes' Theorem can thus be written as:

$$
\text{Posterior} = \frac{\text{Likelihood} \times \text{Prior}}{\text{Evidence}}
$$

## Derivation from the Product Rule

The product rule of probability states:

$$
P(A \cap B) = P(A \mid B) P(B) = P(B \mid A) P(A)
$$

From this, multiple forms follow:

### Multiple Events

For three events:

$$
P(A \mid B, C) = \frac{P(B \mid A, C) P(A \mid C)}{P(B \mid C)}
$$

### Odds Ratio Form

The posterior odds are:

$$
\frac{P(A \mid B)}{P(\lnot A \mid B)} = \frac{P(B \mid A)}{P(B \mid \lnot A)} \cdot \frac{P(A)}{P(\lnot A)}
$$

i.e., posterior odds = likelihood ratio $\times$ prior odds.

## Bayesian Inference

Bayesian inference treats unknown parameters $\theta$ as random variables. Given data $D$, we update:

$$
P(\theta \mid D) = \frac{P(D \mid \theta) P(\theta)}{P(D)} \propto P(D \mid \theta) P(\theta)
$$

The evidence $P(D) = \int P(D \mid \theta) P(\theta) \, d\theta$ normalizes the posterior.

### Conjugate Priors

A prior $P(\theta)$ is **conjugate** to a likelihood $P(D \mid \theta)$ if the posterior belongs to the same family as the prior. Examples:

| Likelihood | Conjugate Prior | Posterior |
|---|---|---|
| Bernoulli | Beta | Beta |
| Gaussian (known $\sigma^2$) | Gaussian | Gaussian |
| Poisson | Gamma | Gamma |
| Multinomial | Dirichlet | Dirichlet |

### Sequential Updating

Bayesian updating is sequential: the posterior from one observation becomes the prior for the next:

$$
P(\theta \mid D_1, D_2) \propto P(D_2 \mid \theta, D_1) P(\theta \mid D_1) \propto P(D_2 \mid \theta) P(D_1 \mid \theta) P(\theta)
$$

This is a key property for online learning and filtering (e.g., Kalman filters).

## Applications in Machine Learning

### Naive Bayes Classifier

Given features $\mathbf{x} = (x_1, \dots, x_d)$ and class $y$, the Naive Bayes assumption (conditional independence of features given the class) gives:

$$
P(y \mid \mathbf{x}) = \frac{P(y) \prod_{i=1}^d P(x_i \mid y)}{P(\mathbf{x})}
$$

The prediction is:

$$
\hat{y} = \arg\max_y P(y) \prod_{i=1}^d P(x_i \mid y)
$$

Despite its strong independence assumption, Naive Bayes performs well on many text classification problems.

### Bayesian Linear Regression

Instead of point estimates, Bayesian linear regression places a prior $P(\mathbf{w})$ on the weights:

$$
P(\mathbf{w} \mid X, \mathbf{y}) = \frac{P(\mathbf{y} \mid X, \mathbf{w}) P(\mathbf{w})}{P(\mathbf{y} \mid X)}
$$

For Gaussian likelihood and Gaussian prior, the posterior is Gaussian with closed-form mean and covariance.

### Bayesian Neural Networks

BNNs place distributions over network weights. Exact inference is intractable, so approximations like variational inference or Monte Carlo dropout are used:

$$
P(\mathbf{w} \mid D) \approx q(\mathbf{w}) = \arg\min_q \text{KL}(q(\mathbf{w}) \parallel P(\mathbf{w} \mid D))
$$

## Connections to Information Theory

Bayes' Theorem relates to mutual information $I(X; Y)$:

$$
I(X; Y) = \mathbb{E}_{P(x, y)} \left[ \log \frac{P(Y \mid X)}{P(Y)} \right] = \mathbb{E}_{P(x, y)} \left[ \log \frac{P(X, Y)}{P(X) P(Y)} \right]
$$

This is the expected log-Bayes factor between the joint and product distributions.

## Relationships to Other Notes

- [[Vectors and Vector Spaces]]: Probabilities can be viewed as vectors in $\mathbb{R}^n$ satisfying $\sum_i P(A_i) = 1$; Bayes' rule is a transformation on this simplex.
- [[Logarithms]]: Logarithms appear in the log-odds form and in information-theoretic interpretations of Bayes.
- [[Matrices and Linear Maps]]: Bayesian updating for Gaussian distributions involves matrix operations on covariance matrices.

## References

- Bayes, T. (1763). "An Essay towards solving a Problem in the Doctrine of Chances." *Philosophical Transactions of the Royal Society*, 53, 370-418.
- Bishop, C. M. (2006). *Pattern Recognition and Machine Learning*. Springer.
- Murphy, K. P. (2012). *Machine Learning: A Probabilistic Perspective*. MIT Press.
