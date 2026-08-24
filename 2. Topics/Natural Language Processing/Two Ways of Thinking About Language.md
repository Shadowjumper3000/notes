# Two Ways of Thinking About Language

## Overview

The study of natural language processing is characterized by a fundamental tension between two paradigms: the **symbolic view**, which treats language as a rule-governed combinatorial system, and the **statistical view**, which treats language as a probabilistic phenomenon emerging from usage patterns.

## The Symbolic View of Language

Rooted in formal linguistics (Chomsky, 1950s–60s) and [[Formal Language Theory]].

### Core Tenets
- **Discrete symbols**: Words are atomic symbols; sentences are structured sequences.
- **Compositionality**: The meaning of a sentence is a function of the meanings of its parts and their syntactic arrangement.
- **Rule-governed**: Grammar is a set of explicit, categorical rules.
- **Innate faculty**: Humans have an innate language faculty (Universal Grammar).

### Strengths
- **Explainability**: Rules make predictions about grammaticality that humans can inspect.
- **Productivity**: Finite rules generate infinite sentences.
- **Logical inference**: Supports deduction, theorem proving, reasoning.
- **Data efficiency**: A small set of rules covers a vast range of phenomena.

### Weaknesses
- **Brittleness**: Exceptions and gradience (e.g., "??The cat seems sleeping" vs. "The cat seems to be sleeping") are hard to handle.
- **Coverage gap**: Hand-crafting comprehensive grammars is labor-intensive.
- **Disagreement**: Linguists disagree on the "correct" grammar.
- **Unsupervised learning**: Learning symbolic grammars from raw text is NP-hard.

## The Statistical View of Language

Rooted in information theory (Shannon, 1948) and [[Distributional Meaning|distributional linguistics]] (Harris, 1950s).

### Core Tenets
- **Probabilistic patterns**: Language is modeled as a stochastic process; grammaticality is a matter of degree.
- **Learning from data**: Patterns are acquired from large corpora via [[Statistical Language Models|statistical estimation]].
- **Continuous representations**: Words and meanings live in [[From Symbols to Spaces|continuous vector spaces]].
- **Emergent structure**: Syntax and semantics emerge from usage statistics, not from innate rules.

### Strengths
- **Robustness**: Graded judgments, noise tolerance, graceful degradation.
- **Coverage**: Automatically captures patterns that would take years to hand-code.
- **Scalability**: Works for any language or domain with sufficient data.
- **State-of-the-art performance**: Dominates benchmarks in translation, QA, generation.

### Weaknesses
- **Data hunger**: Requires massive corpora; rare patterns are poorly estimated.
- **Opacity**: Statistical patterns are not human-readable explanations.
- **No deep generalization**: Can fail on systematic generalizations (e.g., "The cat that the dog that the boy liked chased ran").
- **Bias amplification**: Statistical models amplify biases present in training data.

## The Cost of Explicit Structure

The symbolic approach bears a significant **cost of explicit structure**:

- **Engineering cost**: Writing and maintaining broad-coverage grammars requires linguist-years.
- **Computational cost**: Parsing with expressive grammars can be O($n^3$) or worse.
- **Coverage cost**: No hand-crafted grammar covers all phenomena.
- **Portability cost**: A grammar for English news does not transfer to Twitter or to Japanese.

This cost drove the "statistical revolution" in NLP (1990s), where probabilistic models trained on annotated corpora (treebanks) replaced rule-based systems.

## The Spectrum, Not a Dichotomy

In practice, modern NLP blends both views:

| System | Symbolic Elements | Statistical Elements |
|---|---|---|
| **PCFG parser** | Formal grammar (CFG) | Probabilistic rule weights learned from treebanks |
| **BERT** | Subword vocabulary (discrete tokens) | Continuous embeddings, probabilistic attention |
| **Neural semantic parsing** | Logical form as output | Neural encoder generates the symbolic structure |
| **spaCy** | Tokenization rules, morphology tables | Statistical POS tagger, parser, NER |

## Historical Arc

1. **1950s–1980s**: Symbolic dominance. Rule-based MT, generative grammar, expert systems.
2. **1990s**: Statistical revolution. N-gram LMs, HMM tagging, IBM translation models, PCFG parsing.
3. **2010s**: Neural revolution. Word embeddings, end-to-end differentiable models, deep learning.
4. **2020s**: Hybrid integration. Symbolic constraints + neural learning. LLMs with tool use, chain-of-thought, structured output.

## Implications for Meaning

The two views offer different answers to "What is meaning?"

- **Symbolic**: Meaning is a mapping from sentences to logical forms ([[Semantic Gap and Meaning Representation]]).
- **Statistical**: Meaning is a location in a [[Geometric View of Meaning|vector space]] derived from [[Distributional Meaning|distributional patterns]].

## Connection to Other Concepts

- [[Formal Language Theory]]: The symbolic view's mathematical foundation.
- [[Statistical Language Models]]: The statistical view's core methodology.
- [[From Symbols to Spaces]]: Captures the paradigm shift itself.
- [[Semantic Gap and Meaning Representation]]: The symbolic approach to bridging the gap.
- [[Distributional Meaning]]: The statistical approach's linguistic foundation.
- [[Cost of explicit structure]]: The pragmatic reason for the statistical turn.
