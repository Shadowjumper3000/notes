**Tags:** #hub #nlp #embeddings
**Related:** [[Natural Language Processing]], [[Embeddings]], [[Distributional Hypothesis]]

## Overview
Word embeddings are dense, low-dimensional, continuous vector representations of words that capture semantic and syntactic information based on a word's context. Unlike traditional sparse representations (such as One-Hot Encoding or Bag-of-Words), where each word is represented by a large vector of mostly zeros, word embeddings map thousands of words into a much smaller, fixed-dimensional space (e.g., 50 to 300 dimensions). This transformation is based on the **Distributional Hypothesis**, which posits that "words that occur in similar contexts tend to have similar meanings." By learning these representations from massive text corpora, embeddings enable machines to perform mathematical operations on language, such as calculating similarity or solving analogies.

## Technical Depth
The shift from symbolic to distributed representations was driven by the need to handle the "curse of dimensionality" and capture relationships between words. Mathematically, a word embedding is a learned function $f: V \to \mathbb{R}^d$, where $V$ is the vocabulary and $d$ is the embedding dimension. In this $d$-dimensional space, the distance between vectors—typically measured using **Cosine Similarity**—corresponds to the semantic similarity between the words they represent.

$$\text{similarity}(\mathbf{A}, \mathbf{B}) = \cos(\theta) = \frac{\mathbf{A} \cdot \mathbf{B}}{\|\mathbf{A}\| \|\mathbf{B}\|}$$

Technically, embeddings can be learned through various methods:
- **Prediction-based models (e.g., Word2Vec):** Use shallow neural networks to predict a word from its context (CBOW) or vice-versa (Skip-gram).
- **Matrix Factorization (e.g., GloVe):** Leverages global co-occurrence statistics across the entire corpus rather than local windows.
- **Character-level models (e.g., fastText):** Represent words as bags of character n-grams, allowing the model to handle out-of-vocabulary (OOV) words by leveraging morphological sub-structures.

These models create a manifold where linguistic regularities emerge as linear offsets. For example, the vector operation $\vec{\text{king}} - \vec{\text{man}} + \vec{\text{woman}}$ typically results in a vector closest to $\vec{\text{queen}}$, demonstrating the model's ability to capture gender-based relationships.

## Applications/Examples
Word embeddings are foundational to almost all modern NLP tasks:
- **Semantic Search:** Finding documents relevant to a query based on meaning rather than just keyword matching.
- **Text Classification:** Providing high-quality input features for sentiment analysis or topic categorization.
- **Machine Translation:** Helping models understand the relationships between words across different languages by mapping them to a shared semantic space.
- **Recommendation Systems:** Using item embeddings (analogous to word embeddings) to find similar products or content based on user interaction patterns.

## References
- Mikolov, T., et al. (2013). "Efficient Estimation of Word Representations in Vector Space." (Word2Vec)
- Pennington, J., et al. (2014). "GloVe: Global Vectors for Word Representation."
- Bojanowski, P., et al. (2017). "Enriching Word Vectors with Subword Information." (fastText)
- Jurafsky, D., & Martin, J. H. *Speech and Language Processing* (3rd ed. draft).

## Knowledge Map

### 1. Prediction-Based Models
- [[Word2Vec]]
- [[CBOW vs Skip-gram]]

### 2. Count-Based Models
- [[GloVe]]

### 3. Subword Models
- [[fastText]]

### 4. Evaluation
- [[Intrinsic vs Extrinsic Evaluation of Embeddings]]

> [!question]- Common Exam Questions
> - What is the difference between CBOW and Skip-gram in Word2Vec?
> - How does GloVe combine global co-occurrence statistics with local context?
> - Why does fastText handle OOV words better than Word2Vec?
> - What is the analogy test and what does passing it imply about an embedding space?
