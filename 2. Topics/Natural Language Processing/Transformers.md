# Transformers (NLP)

**Tags:** #topic #nlp #transformers #representation-learning

## Overview
Transformers are sequence models that use attention (self-attention) to compute contextualised token representations. In NLP they power pretrained language models (BERT, GPT, T5, etc.) used for tasks like classification, tagging, generation, retrieval, and understanding.

## Key concepts
- Tokenisation & subwords (WordPiece, BPE)
- Positional encodings (sinusoidal or learned)
- Multi-head self-attention (Q, K, V projections)
- Feed-forward networks and residual connections
- Pretraining objectives: masked language modelling (BERT), autoregressive language modelling (GPT), sequence-to-sequence objectives (T5)
- Fine-tuning and prompt-based/adapter-based adaptation

## Practical notes
- Dual-encoder vs cross-encoder for retrieval: dual-encoders encode query and document separately (fast approximate retrieval); cross-encoders compute interactions (more accurate, slower).
- Tokenisation decisions impact alignment between tokens and labels for sequence labelling tasks.
- Computational constraints: sequence length scales quadratically in attention; alternatives exist (sparse, linearised attention).

## Missing / Essential Topics Checklist
- [ ] Efficient attention variants (Longformer, Performer, Linformer)
- [ ] Scaling laws and model size implications
- [ ] Evaluation pitfalls for LLMs (distributional shift, adversarial prompts)
- [ ] Alignment, safety, and instruction-following techniques (RLHF)
- [ ] Retrieval-augmented generation (RAG) patterns

## Topic Backlinks

- Pretrained models - Transformers
- BERT for NER
- Transformer Architecture

