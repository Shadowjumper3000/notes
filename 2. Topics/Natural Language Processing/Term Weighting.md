# Term Weighting

## Overview

Term weighting assigns numerical values to terms in a document to quantify their importance, relevance, or discriminative power. It is a core component of [[Sparse Representations|bag-of-words models]] and [[Limits of TF–IDF|information retrieval systems]].

## Term Frequency (TF)

The simplest weight: how often a term $t$ appears in document $d$.

$$
\text{TF}(t, d) = f_{t,d}
$$

Variants:

- **Raw count**: $f_{t,d}$.
- **Binary**: $1$ if $t \in d$, else $0$ (used in set-based similarity).
- **Log-normalized**: $\log(1 + f_{t,d})$ — dampens the effect of frequency differences.
- **Augmented TF**: $\frac{f_{t,d}}{\max\{f_{t',d} : t' \in d\}}$ — normalizes by the most frequent term in the document, mitigating [[Limits of TF–IDF|document length bias]].

## Inverse Document Frequency (IDF)

IDF measures how rare a term is across the corpus $D$, under the assumption that rare terms carry more information:

$$
\text{IDF}(t, D) = \log \frac{N}{n_t}
$$

Where $N = |D|$ and $n_t$ is the number of documents containing $t$.

Variants:

- **Unsmoothed IDF**: $\log (N / n_t)$.
- **Smooth IDF**: $\log (1 + N / n_t)$.
- **Probabilistic IDF**: $\log \frac{N - n_t}{n_t}$ (used in BM25).

## TF–IDF

The product of the two components:

$$
\text{TF–IDF}(t, d, D) = \text{TF}(t, d) \times \text{IDF}(t, D)
$$

This produces a [[Sparse Representations#Term–Document Matrix|term–document matrix]] where each document is a vector in $\mathbb{R}^{|V|}$ (with $V$ the vocabulary).

## BM25 (Okapi BM25)

A probabilistic refinement of TF–IDF that introduces saturation and document length normalization:

$$
\text{BM25}(t, d, D) = \text{IDF}(t) \cdot \frac{f_{t,d} \cdot (k_1 + 1)}{f_{t,d} + k_1 \cdot \left(1 - b + b \cdot \frac{|d|}{\text{avgdl}}\right)}
$$

Where $k_1$ (typically 1.2–2.0) controls TF saturation and $b$ (typically 0.75) controls length normalization.

## Other Weighting Schemes

### Pointwise Mutual Information (PMI)
Measures association between a term and a class/category:

$$
\text{PMI}(t, c) = \log \frac{P(t, c)}{P(t) P(c)}
$$

### Chi-Square ($\chi^2$)
Tests independence between term occurrence and class label; high values indicate informative features.

### Information Gain
Measures the reduction in entropy about the class label when the presence/absence of a term is known.

### LTC (Log, IDF, Cosine normalization)
A variant where TF is log-normalized, IDF is applied, and the resulting vector is cosine-normalized to unit length.

## Applications

- **Information Retrieval**: Ranking documents by relevance to a query.
- **Text Classification**: Feature vectors for [[Statistical Language Models|Naive Bayes]], SVM, logistic regression.
- **Keyword Extraction**: Identifying representative terms for a document.
- **Document Summarization**: Scoring sentences by aggregate term weights.

## Limitations and Alternatives

TF–IDF and its variants are fundamentally limited by their [[Limits of TF–IDF|bag-of-words assumption]] and lack of semantic understanding. Modern alternatives include:

- **Dense embeddings** (word2vec, GloVe): [[From Symbols to Spaces|Distributed representations]] that capture similarity.
- **Contextual embeddings** (BERT, GPT): [[Latent and Contextual Semantics|Dynamic, context-sensitive weights]].
- **Neural IR models**: End-to-end learned ranking with transformers.

## Connection to Other Concepts

- [[Sparse Representations]]: TF–IDF produces sparse vectors in a high-dimensional vocabulary space.
- [[Distributional Meaning]]: The co-occurrence statistics that TF encodes are the raw material for distributional semantics.
- [[Geometric View of Meaning]]: Weighted vectors enable cosine similarity for document comparison.
- [[Latent Semantic Analysis (LSA)]]: Applies SVD to the TF–IDF matrix to discover latent factors.
