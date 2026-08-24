# Distributional Meaning

## Overview

Distributional meaning is the foundational idea in computational linguistics that the meaning of a word is determined by the contexts in which it appears. It is most famously captured by J. R. Firth's aphorism: *"You shall know a word by the company it keeps."*

## The Distributional Hypothesis

The **distributional hypothesis** — attributed to Zellig Harris (1954) — states that words occurring in similar contexts tend to have similar meanings. This is the operational principle behind virtually all modern [[From Symbols to Spaces|vector space models of meaning]].

Formally, for words $w_i$ and $w_j$, if:

$$
\text{context}(w_i) \approx \text{context}(w_j)
$$

then:

$$
\text{meaning}(w_i) \approx \text{meaning}(w_j)
$$

## Types of Context

### 1. Document-Level Context (Bag-of-Words)
Two words are similar if they co-occur in the same documents. This is the basis for [[Latent Semantic Analysis (LSA)]].

$$
\text{Co-occurrence}_{i,j} = \sum_{d \in D} \text{count}(w_i, d) \cdot \text{count}(w_j, d)
$$

### 2. Window-Based Context
Two words are similar if they share neighboring words within a fixed window (e.g., ±5 words). This is the approach used in word2vec (Skip-gram, CBOW) and [[Term Weighting#Pointwise Mutual Information|PMI-based models]].

### 3. Syntactic Context
Two words are similar if they share syntactic dependencies (subject-of, object-of, etc.). This yields syntactically informed embeddings.

## Co-Occurrence Matrices

The distributional hypothesis is operationalized by counting co-occurrences to build a word–word or word–context matrix $M \in \mathbb{R}^{|V| \times |C|}$:

$$
M_{ij} = \text{count}(w_i, \text{context}_j)
$$

Each row of $M$ is a [[Sparse Representations#One-hot Encoding|sparse vector]] representing a word's distributional profile. Similarity is measured via [[Geometric View of Meaning|cosine similarity]] between rows.

## Count-Based vs. Predictive Models

A major divide exists between **count-based** and **predictive** distributional models:

### Count-Based (Matrix Factorization)
- Build $M$ explicitly from corpus counts.
- Apply weighting (e.g., [[Term Weighting#PMI|PMI]], TF–IDF) and dimensionality reduction ([[Latent Semantic Analysis (LSA) |SVD]]).
- Examples: LSA, HAL, GloVe (which blends count and predictive).

### Predictive (Neural)
- Train a classifier to predict a word given its context (or vice versa).
- The learned weight matrix serves as the embedding.
- Examples: word2vec (Skip-gram, CBOW), fastText.
- Scale more gracefully and often produce better embeddings for downstream tasks.

## Mathematical Equivalence

Levy and Goldberg (2014) showed that Skip-gram with negative sampling implicitly factorizes a word–context PMI matrix:

$$
\text{word2vec}(w_i, c_j) \approx \text{PMI}(w_i, c_j) - \log k
$$

where $k$ is the number of negative samples. This bridges count-based and predictive approaches.

## Relationship to Semantic Theories

- **Structuralist linguistics** (Saussure): Meaning arises from differences within a system, not from reference to the world.
- **Wittgenstein's meaning-as-use**: "The meaning of a word is its use in the language."
- **Connectionism**: Distributed representations in neural networks echo the idea that concepts are patterns of activation across many units.

## Implications for NLP

Distributional meaning provides a data-driven way to acquire semantic knowledge without manual annotation:

- **Synonymy detection**: Words with similar distributional vectors are likely synonyms.
- **Analogy solving**: Vector arithmetic (e.g., $\text{king} - \text{man} + \text{woman} \approx \text{queen}$).
- **Clustering and topic modeling**: Grouping distributionally similar words reveals semantic categories.
- **Word similarity benchmarks**: WordSim-353, SimLex-999 evaluate models on human-annotated similarity ratings.

## Limitations

- **No grounding**: Distributional models learn meanings from text alone; they lack sensorimotor grounding (see [[Semantic Gap and Meaning Representation]]).
- **Polysemy**: A single vector conflates multiple senses of ambiguous words.
- **No logical structure**: Cannot represent negation, quantification, or logical relations.
- **Corpus bias**: Co-occurrence patterns reflect the corpus's biases and stereotypes.

## Connection to Other Concepts

- [[Two Ways of Thinking About Language]]: Distributional meaning exemplifies the **statistical view** — meaning emerges from usage patterns, not from explicit rules.
- [[Geometric View of Meaning]]: Distributional vectors live in a semantic space where distance encodes (dis)similarity.
- [[Sparse Representations]]: The raw co-occurrence matrix is extremely sparse; dimensionality reduction is essential.
- [[Latent and Contextual Semantics]]: Extends distributional meaning to handle ambiguity through latent topics or contextualized representations.
- [[The OOV Problem]]: Rare words have sparse distributional profiles, making their embeddings poorly estimated.
