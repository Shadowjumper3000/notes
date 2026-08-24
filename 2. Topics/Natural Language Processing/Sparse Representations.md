# Sparse Representations

## Overview

Sparse representations encode linguistic items (words, documents) as vectors where most entries are zero. They are the classical approach to representing text in computational linguistics and information retrieval, serving as the foundation for [[Term Weighting|TF–IDF]] and many early machine learning pipelines.

## One-Hot Encoding

The simplest sparse representation. Each word $w_i$ in a vocabulary $V$ of size $n$ is represented as a binary vector $\mathbf{v}_i \in \{0, 1\}^{n}$:

$$
\mathbf{v}_i = [0, 0, \dots, 1, \dots, 0]
$$

- Exactly one element is 1 (the index of $w_i$ in $V$); all others are 0.
- Cardinality: $|\mathbf{v}_i| = 1$.
- Orthogonality: $\mathbf{v}_i \cdot \mathbf{v}_j = 0$ for $i \neq j$ (no similarity between distinct words).

### Limitations
- **Dimensionality**: $|V|$ can be 50,000–500,000.
- **No similarity**: "car" and "automobile" are as different as "car" and "tangerine."
- **[[The OOV Problem]]**: Any word not in $V$ has no representation.

## Bag-of-Words (BoW)

Extends one-hot encoding to documents. A document $d$ is represented as a vector $\mathbf{d} \in \mathbb{R}^{|V|}$ where:

$$
\mathbf{d}_i = \text{count}(w_i, d)
$$

- Full vocabulary is the union of all terms across all documents.
- **Order is discarded**: "dog bites man" = "man bites dog."
- **Weighting can vary**: raw frequency, binary, or weighted via [[Term Weighting|TF–IDF]].

### Variants
- **Binary BoW**: $1$ if $w_i \in d$, else $0$.
- **Count BoW**: Raw term frequency.
- **TF–IDF BoW**: Frequency weighted by inverse document frequency.

## Term–Document Matrix

Collecting BoW vectors for all documents yields the term–document matrix $X \in \mathbb{R}^{|V| \times |D|}$:

$$
X_{ij} = \text{weight}(w_i, d_j)
$$

This matrix is:
- **Sparse** (>99% zeros for large vocabularies).
- **High-dimensional**: both $|V|$ and $|D|$ can be large.
- **The starting point** for many downstream techniques: [[Latent Semantic Analysis (LSA)]], topic modeling, document clustering.

## Sparsity Statistics

Zipf's law ensures sparsity: most words occur in very few documents, and most documents contain a small fraction of the total vocabulary.

For a corpus of 1M documents with a 100K vocabulary:
- Average document length: ~100 words.
- Density: $100 / 100{,}000 = 0.1\%$.
- $99.9\%$ of the matrix entries are zero.

## Advantages of Sparse Representations

- **Interpretability**: Each dimension corresponds to a known word.
- **Mathematical simplicity**: Operations are sums of weighted counts.
- **Computational efficiency**: Sparse matrix formats (CSR, CSC) enable fast dot products.
- **No training required**: Built from corpus statistics alone.
- **Exact memory**: Query results are directly attributable to specific term matches.

## Disadvantages

- **Semantic blindness**: No capture of synonymy, polysemy, or paraphrase (see [[Limits of TF–IDF]]).
- **High dimensionality**: Curse of dimensionality affects downstream classifiers.
- **No generalization**: Each word is independent.
- **Document length bias**: Longer documents dominate similarity computations.
- **OOV sensitivity**: Unseen terms contribute nothing.

## Dimensionality Reduction

Sparse representations are often transformed into dense ones:

- **Feature selection**: Keep only the top $k$ words by frequency or [[Term Weighting#Chi-Square|$\chi^2$]].
- **Matrix factorization**: [[Latent Semantic Analysis (LSA)|SVD]] produces dense latent vectors.
- **Neural embeddings**: word2vec, GloVe learn dense [[From Symbols to Spaces|distributed representations]] from co-occurrence statistics.

## Comparison with Dense Representations

| Property | Sparse (BoW / TF–IDF) | Dense (word2vec / BERT) |
|---|---|---|
| Vocabulary size | 50K–500K (each word is a dimension) | 50–300 dimensions |
| Representations | Explicit, interpretable | Implicit, opaque |
| [[Geometric View of Meaning|Similarity]] | Exact matches only | Semantic similarity |
| [[The OOV Problem]] | Catastrophic | Mitigated by subword |
| Training | None (count-based) | Requires large corpus |
| Storage | Large but sparse | Small and dense |

## Applications

- **Information Retrieval**: TF–IDF ranking, query-document matching.
- **Text Classification**: Naive Bayes, linear SVM on BoW features.
- **Topic Modeling**: LDA operates on the term–document count matrix.
- **Clustering**: K-means on document vectors.

## Connection to Other Concepts

- [[Term Weighting]]: Provides the weights that populate sparse vectors.
- [[Geometric View of Meaning]]: Cosine similarity between sparse vectors is the standard comparison metric.
- [[Limits of TF–IDF]]: Documents the shortcomings inherent in sparse, count-based representations.
- [[From Symbols to Spaces]]: Documents the transition from sparse to dense representations.
- [[Distributional Meaning]]: The distributional hypothesis is operationalized through sparse co-occurrence counts.
- [[The OOV Problem]]: Most acute in sparse representations where each word is a separate dimension.
