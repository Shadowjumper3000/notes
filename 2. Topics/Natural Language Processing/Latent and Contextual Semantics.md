# Latent and Contextual Semantics

## Overview

Latent and contextual semantics refer to two families of approaches that go beyond surface-level [[Sparse Representations|bag-of-words representations]] to uncover deeper structure in text. **Latent semantics** discovers hidden (latent) topics or factors via matrix factorization; **contextual semantics** produces dynamic word representations that change based on surrounding context.

## Latent Semantic Analysis (LSA)

LSA (Deerwester et al., 1990) applies truncated Singular Value Decomposition (SVD) to the [[Sparse Representations#Term–Document Matrix|term–document matrix]] $X$:

$$
X \approx U_k \Sigma_k V_k^T
$$

Where:
- $U_k$: term–latent factor matrix.
- $V_k$: document–latent factor matrix.
- $\Sigma_k$: diagonal matrix of the $k$ largest singular values.

### Properties
- **Dimensionality reduction**: $k \ll \min(|V|, |D|)$ yields dense, continuous representations.
- **Synonymy capture**: Words that rarely co-occur may share latent factors via third words.
- **Polysemy limitation**: Each word has a single vector, conflating multiple senses.

### HAL — Hyperspace Analog to Language
HAL (Lund & Burgess, 1996) builds a word–word co-occurrence matrix from a sliding window and applies weighting, without SVD. It captures [[Distributional Meaning|local distributional context]].

**Key difference**: LSA captures global document-level structure; HAL captures local window-based co-occurrence.

## LSA vs HAL: Global vs Local Structure

| Aspect | LSA | HAL |
|---|---|---|
| Context unit | Document | Fixed window (~10 words) |
| Matrix | Term–document | Word–word |
| Dimensionality reduction | SVD | None (or later PCA) |
| Global structure | ✅ Captures topics | ❌ |
| Local syntactic cues | ❌ | ✅ |
| Computational cost | High (SVD is expensive) | Moderate |
| Best for | Topic modeling, document similarity | Word similarity, semantic priming tasks |

## Contextual Semantics (Word Sense Disambiguation)

Contextual semantics recognizes that word meaning is context-dependent. A single word has multiple senses; a good representation should reflect this:

$$
v(\text{"bank"}) \neq v(\text{"river bank"}) \neq v(\text{"investment bank"})
$$

### Static Embeddings + Sense Clustering
- **Multi-sense embeddings** (MSSG, SensEmbed): Cluster contexts of each word; learn separate vectors per cluster.
- Limitation: Number of senses is fixed; fine-grained distinctions are hard.

### Contextual Embeddings (Deep Learning)
- **ELMo** (Peters et al., 2018): Bidirectional LSTM produces context-sensitive embeddings from all layers.
- **BERT** (Devlin et al., 2019): Deep bidirectional transformer; each token's representation is a function of the entire sequence via self-attention.
- **GPT** (Radford et al., 2018): Autoregressive transformer; left-to-right context only.

Formally, contextual embedding:

$$
v_{\text{BERT}}(w_i) = f_{\text{BERT}}(\text{[CLS]}, w_1, \dots, w_i, \dots, w_n, \text{[SEP]})
$$

The same word $w_i$ receives different vectors in different sentential contexts.

## The Spectrum of Semantic Models

```
Sparse          Dense            Context-Sensitive
  │               │                    │
BoW / TF–IDF    LSA / word2vec    BERT / GPT
  │               │                    │
No semantics    Static spaces      Dynamic spaces
```

## Latent Topics vs. Contextual Meaning

- **Latent topics** (LSA, LDA): Document-level themes inferred from word co-occurrence patterns. Useful for retrieval, clustering, content analysis.
- **Contextual meaning** (BERT, GPT): Token-level meaning inferred from the local sentential context. Useful for QA, NER, sentiment, translation.

## Practical Applications

| Model | Application |
|---|---|
| LSA | Document similarity, essay grading, information retrieval |
| LDA | Topic modeling, content recommendation |
| word2vec / GloVe | Word similarity, feature augmentation |
| BERT | QA, NER, sentiment, sentence-pair tasks |
| GPT | Text generation, few-shot learning |

## Limitations

- **LSA**: No notion of word order; single vector per word; SVD does not scale trivially.
- **Contextual models**: Computationally expensive; over-parameterized for small data; less interpretable.
- **Both**: Cannot represent logical structure (negation, quantification, counterfactuals).

## Connection to Other Concepts

- [[Distributional Meaning]]: Both LSA and contextual embeddings operationalize the distributional hypothesis.
- [[From Symbols to Spaces]]: LSA produces the first continuous spaces; contextual models make them dynamic.
- [[Geometric View of Meaning]]: All representations support similarity measures in a geometric space.
- [[Semantic Gap and Meaning Representation]]: Contextual embeddings reduce the gap but do not close it.
- [[Statistical Language Models]]: Contextual embeddings are derived from language model training objectives.
- [[Limits of TF–IDF]]: LSA and contextual models directly address TF–IDF's semantic blindness.
