# Geometric View of Meaning

## Overview

The geometric view of meaning treats words, phrases, and documents as points or vectors in a high-dimensional semantic space. Operations in this space — distance, angle, projection — encode linguistic relationships. This view underlies [[From Symbols to Spaces|vector space models]], [[Distributional Meaning|distributional semantics]], and modern neural [[Latent and Contextual Semantics|representations]].

## The Semantic Space

A word $w$ is represented as a vector $\mathbf{v}(w) \in \mathbb{R}^d$. The space $\mathbb{R}^d$ is called the **semantic space**, and its axes are *latent semantic dimensions* (not individual words unless using [[Sparse Representations|sparse representations]]).

Key properties:
- **Distance encodes dissimilarity**: $\|\mathbf{v}(a) - \mathbf{v}(b)\|$ is small for similar words.
- **Angle encodes relatedness**: $\cos \theta_{a,b}$ is close to 1 for related words.
- **Direction encodes semantic features**: Directions for gender, tense, plurality emerge.

## Cosine Similarity

The most widely used similarity measure in semantic spaces. For vectors $\mathbf{a}, \mathbf{b} \in \mathbb{R}^d$:

$$
\text{cosine}(\mathbf{a}, \mathbf{b}) = \frac{\mathbf{a} \cdot \mathbf{b}}{\|\mathbf{a}\| \|\mathbf{b}\|} = \frac{\sum_{i=1}^d a_i b_i}{\sqrt{\sum_{i=1}^d a_i^2} \sqrt{\sum_{i=1}^d b_i^2}}
$$

- **Range**: $[-1, 1]$ (in practice $[0, 1]$ for non-negative vectors).
- **Magnitude invariance**: Only direction matters — document length is normalized away.
- **Relationship to Euclidean distance** for unit vectors: $\|\mathbf{a} - \mathbf{b}\|^2 = 2(1 - \cos \theta)$.

## Set Similarity Coefficients

For [[Sparse Representations#Bag-of-Words|sparse, binary vectors]] (sets of terms), several set-based measures are used:

### Jaccard Coefficient
$$
J(A, B) = \frac{|A \cap B|}{|A \cup B|}
$$

### Dice Coefficient
$$
D(A, B) = \frac{2 |A \cap B|}{|A| + |B|}
$$

### Overlap Coefficient
$$
O(A, B) = \frac{|A \cap B|}{\min(|A|, |B|)}
$$

These are related to cosine similarity for binary vectors: $\text{cosine}(A, B) = \frac{|A \cap B|}{\sqrt{|A| \cdot |B|}}$.

## Normalization: Magnitude vs. Direction

### Magnitude
- Raw frequency vectors have magnitudes proportional to document length.
- Magnitude captures "how much" but often confounds relevance with length.
- [[Term Weighting|Length normalization]] (augmented TF, BM25) controls for this.

### Direction
- After normalization, only the relative proportions of terms matter.
- Cosine similarity operates on direction only.
- A short, focused document may be more similar to a query than a long, diffuse one.

**When to normalize?**
- **Document retrieval**: Normalize to ignore length.
- **Word similarity**: Usually no normalization needed (vectors are already unit-length from training).
- **Classification**: Depends on the classifier; SVMs often benefit from normalization.

## Vector Arithmetic

Semantic spaces support algebraic operations that capture linguistic regularities:

### Classic Analogy (word2vec)
$$
\mathbf{v}(\text{king}) - \mathbf{v}(\text{man}) + \mathbf{v}(\text{woman}) \approx \mathbf{v}(\text{queen})
$$

This is the **parallelogram model**: the vector from man to king is approximately the same as from woman to queen.

### Offset Patterns
- **Plurality**: $\mathbf{v}(\text{apple}) - \mathbf{v}(\text{apples}) \approx \mathbf{v}(\text{car}) - \mathbf{v}(\text{cars})$
- **Tense**: $\mathbf{v}(\text{walk}) - \mathbf{v}(\text{walked}) \approx \mathbf{v}(\text{run}) - \mathbf{v}(\text{ran})$
- **Gender**: $\mathbf{v}(\text{king}) - \mathbf{v}(\text{queen}) \approx \mathbf{v}(\text{actor}) - \mathbf{v}(\text{actress})$

### Word Analogy Test Set
The standard benchmark: given $a : b :: c : ?$, find $d$ that maximizes:

$$
\argmax_{d \in V} \cos(\mathbf{v}(d), \mathbf{v}(b) - \mathbf{v}(a) + \mathbf{v}(c))
$$

## Projection and Subspaces

### Centering and PCA
Projecting vectors onto principal components reveals dominant semantic dimensions. The first PC often captures a "size" or "sentiment" axis.

### Linear Separability
Semantic classes (nouns vs. verbs, positive vs. negative sentiment) are often approximately linearly separable in the space.

## Geometric Interpretations of Linguistic Phenomena

| Phenomenon | Geometric Interpretation |
|---|---|
| Synonymy | Nearby points (small angle) |
| Antonymy | Opposite directions (angle near $\pi$) |
| Analogy | Parallelogram completion |
| Polysemy | Single point surrounded by sense-specific neighbors |
| Hypernymy | Hierarchical structure; not purely linear |
| Composition | Vector addition, weighted averaging, or learned composition functions |

## Limitations of the Geometric View

- **No logical structure**: Cannot represent negation or disjunction naturally.
- **Compositionality is unclear**: "Not good" ≠ opposite of "good" in a simple additive model.
- **Fragile analogies**: Many reported analogies are artifacts of nearest-neighbor bias.
- **Static similarity**: Does not capture context-dependent shifts (solved by [[Latent and Contextual Semantics|contextual models]]).

## Connection to Other Concepts

- [[Distributional Meaning]]: The empirical basis for geometric semantic spaces.
- [[From Symbols to Spaces]]: The geometric view is what replaces symbolic representations.
- [[Sparse Representations]]: Produce high-dimensional, non-Euclidean geometry.
- [[Latent and Contextual Semantics]]: Contextual models produce dynamic geometries.
- [[Limits of TF–IDF]]: TF–IDF vectors live in this space and inherit its limitations.
- [[Semantic Gap and Meaning Representation]]: Geometric similarity ≠ formal meaning representation.
