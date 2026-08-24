# Transformer Architecture
The Transformer is a deep learning architecture that relies on attention mechanisms (particularly self-attention) to process input sequences in parallel. It replaced recurrent and convolutional sequence models in many domains because it scales well with data and model size and captures long-range dependencies efficiently.

## Core components
- Input tokenisation & embeddings (positional encodings added to preserve order)
- Multi-head self-attention layers (queries, keys, values)
- Position-wise feed-forward networks
- Layer normalisation and residual connections

## Brief mechanics
Each self-attention layer computes attention weights using dot-products between queries and keys, then applies those weights to the values to produce contextualised token representations. Multiple attention heads allow the model to attend to different subspaces of the representation.

## Applications
- Machine translation, language modelling, summarization, question answering, code generation, and multimodal models.

## Topic Backlinks

- Self-Attention
<!-- unified:backlinks:end -->

