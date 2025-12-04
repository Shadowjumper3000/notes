# Notes on Marginal and Joint Probabilities, and PMFs

## Marginal Probability

Marginal probability refers to the probability of a single event occurring, regardless of the outcome of other variables.

### Definition
Given a joint probability distribution \( P(X, Y) \), the marginal probability of \( X \) is calculated as:

$$
P(X = x) = \sum_{y} P(X = x, Y = y)
$$

Similarly, the marginal probability of \( Y \) is:

$$
P(Y = y) = \sum_{x} P(X = x, Y = y)
$$

### Example
If the joint probabilities of \( X \) and \( Y \) are:

| \(X \backslash Y\) | \(Y = 1\) | \(Y = 2\) |
|-------------------|------------|------------|
| \(X = 1\)         | 0.2        | 0.3        |
| \(X = 2\)         | 0.1        | 0.4        |

Then:

- \( P(X = 1) = 0.2 + 0.3 = 0.5 \)
- \( P(X = 2) = 0.1 + 0.4 = 0.5 \)

## Joint Probability

Joint probability is the probability of two (or more) events happening at the same time.

### Definition
The joint probability \( P(X = x, Y = y) \) is the probability that \( X \) takes the value \( x \) and \( Y \) takes the value \( y \).

### Properties
- The sum of all joint probabilities is 1:
  
  $$
  \sum_x \sum_y P(X = x, Y = y) = 1
  $$

### Example
Using the same table as above:
- \( P(X = 1, Y = 1) = 0.2 \)
- \( P(X = 2, Y = 2) = 0.4 \)

## Probability Mass Function (PMF)

The probability mass function defines the probability distribution for discrete random variables.

### Definition
For a discrete random variable \( X \):

$$
P(X = x) = f(x)
$$

Where \( f(x) \) satisfies the following conditions:
1. \( f(x) \geq 0 \) for all \( x \).
2. The sum of probabilities over all possible values of \( X \) is 1:
   
   $$
   \sum_x f(x) = 1
   $$

### Joint PMF
For two discrete random variables \( X \) and \( Y \), the joint PMF is defined as:

$$
P(X = x, Y = y) = f(x, y)
$$

### Marginal PMF
The marginal PMF can be derived from the joint PMF:

$$
P(X = x) = \sum_y f(x, y)
$$

## Relationship Between Marginal and Joint Probabilities
- The marginal probability is obtained by summing over the joint probabilities.
- If \( X \) and \( Y \) are independent:
  
  $$
  P(X = x, Y = y) = P(X = x) \cdot P(Y = y)
  $$
