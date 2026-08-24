**Tags:** #concept #nlp #embeddings
**Related:** [[Word Embeddings]], [[CBOW vs Skip-gram]], [[Distributional Hypothesis]]

## Overview
Word2Vec is a foundational framework in modern NLP for learning dense, low-dimensional vector representations of words from large text corpora. Introduced by Tomas Mikolov and his team at Google in 2013, Word2Vec employs shallow, two-layer neural networks trained on a self-supervised prediction task. The core philosophy of Word2Vec is rooted in the **Distributional Hypothesis**, where a word's meaning is inferred by the words that frequently appear in its vicinity. By training the model to predict either a target word from its context (CBOW) or its context from a target word (Skip-gram), the model discovers latent semantic and syntactic patterns, mapping them to a continuous vector space where geometric relationships mirror linguistic properties.

## Technical Depth
The Word2Vec model consists of two primary architectures: **Continuous Bag-of-Words (CBOW)** and **Skip-gram**. While CBOW predicts a central word based on a window of surrounding context words, Skip-gram predicts the context words given a single target word. Skip-gram is generally preferred for larger datasets and better captures rare words.

The training objective of Skip-gram is to maximize the average log probability across all word-context pairs $(w_t, w_{t+j})$ within a window of size $c$:
$$\mathcal{L} = \frac{1}{T} \sum_{t=1}^{T} \sum_{-c \leq j \leq c, j \neq 0} \log P(w_{t+j} \mid w_t)$$

To model the conditional probability $P(w_{t+j} \mid w_t)$, the standard softmax function is used. However, computing the full softmax over a large vocabulary $V$ is computationally prohibitive. Word2Vec addresses this with two optimization techniques:
1. **Hierarchical Softmax:** Uses a binary Huffman tree to represent the vocabulary, reducing the complexity of the output layer from $O(V)$ to $O(\log V)$.
2. **Negative Sampling (NS):** Instead of calculating the probability over the entire vocabulary, the model learns to distinguish a target context word from $k$ randomly sampled "negative" noise words. This transforms the multiclass problem into a series of binary classification tasks using the logistic function:
   $$\log \sigma(\mathbf{v}_{w_O}^\prime{}^\top \mathbf{v}_{w_I}) + \sum_{i=1}^k \mathbb{E}_{w_i \sim P_n(w)} [\log \sigma(-\mathbf{v}_{w_i}^\prime{}^\top \mathbf{v}_{w_I})]$$

Through this process, the model updates two weight matrices ($\mathbf{W}_{in}$ and $\mathbf{W}_{out}$). After training, the rows of $\mathbf{W}_{in}$ serve as the final word embeddings.

## Applications/Examples
Word2Vec has been applied to a wide range of tasks beyond just providing features for NLP models:
- **Analogy Discovery:** Demonstrating semantic relationships through vector arithmetic (e.g., *Germany: Berlin :: France: Paris*).
- **Recommendation Systems (Item2Vec):** Treating items in a user session as "words" in a "sentence" to learn item embeddings for similarity-based recommendations.
- **Gene Sequences (BioVec):** Using Word2Vec to learn embeddings for biological sequences to identify functional similarities between genes.
- **Sentiment Analysis:** Pre-training word vectors on a large corpus before using them as inputs for sentiment classifiers, significantly improving performance compared to random initialization.

## References
- Mikolov, T., et al. (2013). "Efficient Estimation of Word Representations in Vector Space."
- Mikolov, T., et al. (2013). "Distributed Representations of Words and Phrases and their Compositionality." (Introduced Negative Sampling)
- Goldberg, Y., & Levy, O. (2014). "word2vec Explained: Deriving Mikolov et al.'s Negative-Sampling Word-Embedding Method."
- Jurafsky, D., & Martin, J. H. *Speech and Language Processing* (3rd ed. draft).

