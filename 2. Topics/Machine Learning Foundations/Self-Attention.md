# Self-Attention
Self-attention is a mechanism that allows a model to weigh the importance of different parts of an input sequence relative to a specific element, enabling the capture of global dependencies regardless of distance.

## How it works (brief)
- Compute queries (Q), keys (K), and values (V) by linear projections of input token embeddings.
- Attention weights = softmax(Q K^T / sqrt(d_k)).
- Output = Attention weights × V.

## Why it's useful
- Computes interactions between all token positions in parallel.
- Handles long-range dependencies better than fixed-window RNN/CNN approaches.

