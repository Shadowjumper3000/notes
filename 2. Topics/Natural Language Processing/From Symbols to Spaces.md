# From Symbols to Spaces

## Overview

"From Symbols to Spaces" describes the paradigm shift in NLP from representing words as discrete, atomic symbols to embedding them as continuous vectors in a high-dimensional semantic space. This transition underpins the success of modern [[Statistical Language Models|statistical]] and [[Latent and Contextual Semantics|neural NLP]].

## The Symbolic Representation

In classical symbolic NLP, words are treated as atomic symbols from a fixed vocabulary $V$:

- **One-hot vectors**: $w_i \in \{0, 1\}^{|V|}$ with a single 1 at position $i$.
- **No similarity structure**: $\text{distance}(w_i, w_j) = \sqrt{2}$ for all $i \neq j$.
- **Mismatch with linguistic reality**: The symbol "car" and "automobile" are formally as different as "car" and "banana."

This is the [[Sparse Representations#One-hot Encoding|one-hot encoding]] approach, which forms the basis of [[Sparse Representations#Bag-of-Words|bag-of-words]] and [[Term Weighting|TF–IDF]].

## The Continuous Space Representation

A distributed representation maps each word to a dense vector $v(w) \in \mathbb{R}^d$ where $d \ll |V|$:

$$
v(w) = [x_1, x_2, \dots, x_d]
$$

These vectors satisfy:

- **Similar words cluster**: $\text{cosine}(v(\text{car}), v(\text{automobile})) \approx 1$.
- **Arithmetic operations**: $v(\text{king}) - v(\text{man}) + v(\text{woman}) \approx v(\text{queen})$.
- **Dimensionality reduction**: $d = 50{-}300$ instead of $|V| = 50{,}000{-}500{,}000$.

## Key Milestones

### 1. Vector Space Model (VSM)
Salton (1975): documents projected into a term space. The origin of [[Sparse Representations#Term–Document Matrix|term–document matrices]] and [[Geometric View of Meaning|geometric similarity]].

### 2. Latent Semantic Analysis (LSA)
Deerwester et al. (1990): [[Latent Semantic Analysis (LSA)|SVD on the term–document matrix]] produces continuous latent factors — the first truly distributed word representations.

### 3. Neural Word Embeddings
- **word2vec** (Mikolov, 2013): Efficient training of dense embeddings via Skip-gram and CBOW.
- **GloVe** (Pennington, 2014): Factorizes a word–co-occurrence matrix using weighted least squares.
- **fastText** (Bojanowski, 2016): Adds subword n-gram information for [[The OOV Problem|OOV robustness]].

### 4. Contextual Embeddings
- **ELMo** (Peters, 2018): Deep contextualized representations from bidirectional LSTM.
- **BERT / GPT** (Devlin, 2018 / Radford, 2018): Transformer-based models that produce different vectors for the same word in different [[Latent and Contextual Semantics|contexts]].

## The Embedding Space

The learned space exhibits remarkable structure:

### Directional Meaning
Directions in the space encode specific semantic relationships (gender, tense, plurality, etc.).

### Hierarchical Structure
Hypernymy relationships (animal → dog → poodle) correspond to hierarchical organization, though not always linear.

### Analogical Reasoning
Parallelogram analogy:

$$
v(a) - v(b) \approx v(c) - v(d)
$$

The classic test: "a is to b as c is to ?"

## Implications

| Aspect | Symbols | Spaces |
|---|---|---|
| Similarity | None | Cosine / Euclidean distance |
| [[The OOV Problem]] | Catastrophic | Mitigated by subword info |
| Generalization | None | Similar words behave similarly |
| Data efficiency | High (rules require few examples) | Low (requires large corpora) |
| Interpretability | High (rules are human-readable) | Low (vectors are opaque) |
| [[Semantic Gap and Meaning Representation]] | Can be bridged via logic | Learned implicitly, hard to verify |

## The Continuum

The distinction is not binary. Modern systems blend both:

- **Symbolic inputs**: Words as tokens (still discrete indices).
- **Continuous representations**: Embedding lookup renders symbols as vectors.
- **Symbolic outputs**: Softmax over a discrete vocabulary; structured prediction.

## The Cost

The shift to spaces sacrifices:

- **Compositional transparency**: How is "very happy" composed from "very" and "happy"? In symbolic systems, this is explicit; in vector spaces, it is learned but opaque.
- **Logical inference**: Symbolic systems support deduction (syllogisms, theorem proving); vector spaces support similarity but not entailment.
- **Explainability**: The "why" behind a prediction is harder to trace in a neural space than a rule-based system.

## Connection to Other Concepts

- [[Geometric View of Meaning]]: The key operations in the space — distances, angles, projections.
- [[Distributional Meaning]]: The empirical foundation — similar contexts produce similar vectors.
- [[Two Ways of Thinking About Language]]: This note captures the transition from the symbolic to the statistical view.
- [[Sparse Representations]]: The starting point; dense representations are its successor.
- [[Latent and Contextual Semantics]]: Contextual spaces extend static embeddings to dynamic, polysemy-aware representations.
- [[Semantic Gap and Meaning Representation]]: Vectors bridge part of the gap but do not provide explicit meaning representations.
