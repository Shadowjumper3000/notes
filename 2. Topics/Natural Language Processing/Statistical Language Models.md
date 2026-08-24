# Statistical Language Models

## Overview

A statistical language model (LM) assigns a probability to a sequence of words $P(w_1, w_2, \dots, w_n)$. These models capture the statistical regularities of natural language, enabling tasks such as prediction, generation, and scoring of text.

## Mathematical Formulation

By the chain rule of probability, any joint distribution over a word sequence factorizes as:

$$
P(w_1, w_2, \dots, w_n) = \prod_{i=1}^{n} P(w_i \mid w_1, \dots, w_{i-1})
$$

The goal is to estimate the conditional probability of the next word given the history.

## N-Gram Models

The **Markov assumption** limits the history to the last $N-1$ words:

$$
P(w_i \mid w_1, \dots, w_{i-1}) \approx P(w_i \mid w_{i-N+1}, \dots, w_{i-1})
$$

Common variants:

- **Unigram** ($N=1$): $P(w_i)$ — no context.
- **Bigram** ($N=2$): $P(w_i \mid w_{i-1})$.
- **Trigram** ($N=3$): $P(w_i \mid w_{i-2}, w_{i-1})$.

Maximum Likelihood Estimation (MLE) gives:

$$
P_{\text{MLE}}(w_i \mid w_{i-N+1}^{i-1}) = \frac{\text{count}(w_{i-N+1}^{i})}{\text{count}(w_{i-N+1}^{i-1})}
$$

## Smoothing

Raw MLE assigns zero probability to unseen n-grams—a severe [[The OOV Problem|sparsity problem]]. Smoothing redistributes probability mass:

- **Laplace (add-1) smoothing**: Add 1 to all counts.
- **Kneser-Ney smoothing**: Interpolates higher- and lower-order models, considered state-of-the-art for n-grams.
- **Good-Turing estimation**: Adjusts counts based on the frequency of rare events.
- **Backoff and interpolation**: Use lower-order n-grams when higher-order counts are zero.

## Perplexity

The standard evaluation metric for language models:

$$
\text{Perplexity}(P, Q) = 2^{-\frac{1}{n} \sum_{i=1}^{n} \log_2 P(w_i \mid w_1, \dots, w_{i-1})}
$$

Lower perplexity indicates a better fit to test data. Perplexity is the exponent of the average negative log-likelihood per word.

## Limitations of N-Gram Models

- **Fixed context window**: Cannot capture long-range dependencies beyond $N-1$ words.
- **Sparsity**: The number of possible n-grams grows exponentially with $N$; most never appear in training data.
- **No generalization**: "I ate an orange" and "I ate a banana" share no parameters—the model cannot learn that "orange" and "banana" play similar roles.
- **Surface form**: Treats each word as an atomic symbol, ignoring [[Distributional Meaning|distributional similarity]].

## Neural Language Models

Neural LMs address these limitations by learning [[From Symbols to Spaces|distributed representations]]:

- **Feedforward LMs** (Bengio et al., 2003): Project word indices to dense embeddings; predict the next word via a hidden layer.
- **Recurrent LMs** (RNN, LSTM): Process sequences with hidden states that summarize arbitrarily long histories.
- **Transformer LMs** (GPT, BERT): Use self-attention to model all pairwise interactions; enable massive scaling and [[Latent and Contextual Semantics|deep contextualization]].

### Key Advantages

- Parameter sharing via continuous embeddings.
- Generalization across semantically similar contexts.
- Handling of [[The OOV Problem|OOV words]] via subword tokenization ([[Statistical Language Models|BPE, WordPiece]]).

## Applications

- **Speech recognition**: $P(\text{text} \mid \text{audio}) \propto P(\text{audio} \mid \text{text}) P(\text{text})$.
- **Machine translation**: Scoring and reranking candidate translations.
- **Text generation**: Sampling from $P(w_i \mid w_{<i})$ to produce fluent sequences.
- **Spelling correction**: Ranking corrections by language model probability.
- **Dialogue systems**: Predicting the next utterance.

## Evaluation Beyond Perplexity

While perplexity is widely used, it does not always correlate with downstream task performance. Modern evaluation also uses:

- **Intrinsic**: perplexity, cross-entropy.
- **Extrinsic**: BLEU (translation), ROUGE (summarization), accuracy (classification).

## Connection to Other Concepts

- [[Two Ways of Thinking About Language]]: LMs exemplify the **statistical view** where language structure emerges from usage patterns rather than explicit rules.
- [[Term Weighting]]: TF–IDF is a form of unigram "model" but without probability normalization.
- [[Semantic Gap and Meaning Representation]]: LMs output probabilities, not meaning representations—they model form better than content.
- [[Statistical Language Models|Distributional meaning]] is the linguistic foundation: words with similar contexts receive similar probability estimates.
