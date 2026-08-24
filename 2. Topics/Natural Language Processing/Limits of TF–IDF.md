# Limits of TF–IDF

## Overview

[[Term Weighting|TF–IDF]] (Term Frequency–Inverse Document Frequency) is a foundational weighting scheme in information retrieval and text mining. Despite its effectiveness for keyword-based search and document ranking, it suffers from several fundamental limitations that motivate the use of [[Sparse Representations|denser or learned representations]].

## Semantic Blindness

TF–IDF operates purely at the lexical level and cannot capture semantic relationships between terms:

- **Synonymy**: Queries containing "car" will not match documents containing "automobile" unless both terms appear. No notion of semantic equivalence exists.
- **Polysemy**: The same term (e.g., "bank") is treated as a single dimension, conflating distinct senses (financial institution vs. river bank).
- **Hyponymy / Hypernymy**: Hierarchical relationships ("dog" ⊆ "animal") are invisible to TF–IDF.

This lexical gap is a direct consequence of the [[Bag-of-Words (BoW)|bag-of-words representation]] that discards all context.

## Word Order and Syntactic Structure

TF–IDF treats documents as unordered sets of terms. This discards:

- **Phrase structure**: "not good" and "very good" receive the same representation.
- **Word order**: "dog bites man" is identical to "man bites dog."
- **Negation and scope**: "I do not like spam" is represented as positive evidence for "like" and "spam."

## Document Length Bias

Raw term frequency is naturally higher in longer documents. While IDF normalization helps, TF–IDF still exhibits residual bias:

- Longer documents accumulate more distinct terms and higher term frequencies.
- Shorter documents are penalized even when they are highly relevant.
- Variants like [[Term Weighting#Augmented TF|augmented TF]] attempt to mitigate this by normalizing by maximum term frequency.

## Vocabulary Mismatch

The [[The OOV Problem|OOV problem]] applies directly: any word not seen during corpus construction receives a TF of zero and an undefined IDF. TF–IDF cannot generalize to unseen vocabulary without re-indexing the entire collection.

## Lack of Latent Structure

TF–IDF operates on surface-level term counts and cannot discover latent topics or underlying semantic dimensions. Compare with:

- [[Latent Semantic Analysis (LSA)]] which uses SVD to uncover latent factors.
- [[Latent and Contextual Semantics|Contextual embeddings]] which produce dynamic representations sensitive to surrounding text.

## Practical Consequences

| Limitation | Impact |
|---|---|
| Synonymy | Low recall for semantically related but lexically distinct queries |
| Polysemy | Low precision for ambiguous terms |
| No word order | Inability to distinguish negations or syntactic roles |
| Document length bias | Unfair ranking of short vs. long documents |
| No generalization | Requires full re-indexing for new vocabulary |

## Mitigations

- **Query expansion**: Adding synonyms to the query via [[Distributional Meaning|distributional thesauri]].
- **Dimensionality reduction**: Applying [[Latent Semantic Analysis (LSA)]] to the TF–IDF matrix.
- **Learned embeddings**: Replacing TF–IDF with [[Geometric View of Meaning|dense vector representations]] like word2vec or contextual transformers.
- **BM25**: An [[Term Weighting|improved probabilistic weighting]] that addresses some of TF–IDF's length and saturation issues.

## Relationship to Modern Approaches

The limits of TF–IDF directly motivate the shift from [[Sparse Representations|sparse, count-based representations]] to [[From Symbols to Spaces|dense, distributed representations]] and the broader transition from [[Two Ways of Thinking About Language|symbolic to statistical approaches]] in NLP.
