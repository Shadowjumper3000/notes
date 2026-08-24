# Semantic Gap and Meaning Representation

## Overview

The **semantic gap** is the disconnect between surface-level linguistic form (text, speech) and the underlying meaning that a human reader extracts. **Meaning representation** encompasses the formal frameworks designed to bridge this gap by encoding meaning in a structured, machine-tractable format.

## The Semantic Gap

The semantic gap manifests in several ways:

### Surface vs. Deep Structure
Chomsky's distinction: "John is easy to please" and "John is eager to please" have identical surface structure but different deep structures (John is the object of pleasing vs. the subject).

### Paraphrase Equivalence
Multiple surface forms express the same meaning:
- "The cat chased the mouse."
- "The mouse was chased by the cat."
- "It was the cat that chased the mouse."

A meaning representation should map these to a single canonical form.

### Ambiguity
A single surface form maps to multiple meanings:
- **Lexical ambiguity**: "bank" (river/institution).
- **Structural ambiguity**: "I saw the man with the telescope" (who has the telescope?).
- **Scope ambiguity**: "Every man loves a woman" (∃∀ vs. ∀∃).

### Pragmatics and Implicature
Meaning goes beyond literal semantics: "Can you pass the salt?" is usually a request, not a yes/no question about ability.

## Abstract Meaning Representation (AMR)

AMR (Banarescu et al., 2013) is a semantic formalism that represents sentence meaning as a rooted, directed, labeled graph:

- **Nodes**: Concepts — words or PropBank framesets (e.g., `want-01`, `cat`, `possible`).
- **Edges**: Semantic relations — `ARG0` (agent), `ARG1` (patient), `location`, `time`, `manner`, etc.

### AMR Example

Sentence: "The boy wants the girl to believe him."

```
(w / want-01
   :ARG0 (b / boy)
   :ARG1 (b2 / believe-01
            :ARG0 (g / girl)
            :ARG1 b))
```

### Key Properties
- **Abstract**: Surface details (syntax, inflection, word order) are discarded.
- **PropBank-based**: Predicate-argument structure aligns with a verb lexicon.
- **Graph-based**: Not a tree — reentrancy allows shared arguments (coreference).
- **No quantifier scope**: Does not attempt to resolve scope ambiguities.

### Active vs. Passive Equivalence
AMR maps active and passive voice to the same graph:

- "The cat chased the mouse."
- "The mouse was chased by the cat."

Both produce:
```
(c / chase-01 :ARG0 (c2 / cat) :ARG1 (m / mouse))
```

This is a major advantage over syntactic representations.

## Other Meaning Representation Formalisms

### 1. First-Order Logic (FOL)
Traditional formal semantics (Montague): translates sentences into FOL for inference.

$$
\exists x \, \text{cat}(x) \land \text{chase}(x, \text{mouse})
$$

**Pros**: Supports reasoning, quantification, negation.  
**Cons**: Expensive to produce; brittle; no gradient.

### 2. Semantic Role Labeling (SRL)
Identifies predicates and their arguments: Who did what to whom, when, where, how.

Form: `[ARG0 The cat] chased [ARG1 the mouse]`

### 3. Universal Dependencies (UD)
A dependency grammar framework that includes a semantic layer (Enhanced UD) capturing predicate-argument structure with additional edges for control, raising, and relative clauses.

### 4. Discourse Representation Theory (DRT)
Extends FOL with a dynamic account of anaphora and discourse-level semantics. Handles "donkey sentences": "Every farmer who owns a donkey beats it."

### 5. Frame Semantics (FrameNet)
Events and situations are described by frames (scripts) with frame elements (roles). "Commerce_transfer" frame involves a Buyer, Seller, Goods, and Money.

## Vector-Based Meaning Representations

Modern NLP often skips explicit symbolic meaning representations in favor of [[From Symbols to Spaces|distributed vector representations]]:

- **Sentence embeddings**: BERT `[CLS]` token, Sentence-BERT, InferSent.
- **Cross-encoders**: Directly model the relationship between two texts without an intermediate meaning representation.

These are powerful but:
- **Opacity**: Hard to inspect or verify what meaning is captured.
- **No logical inference**: Cannot guarantee faithfulness of deductions.
- **Evaluation**: Tested indirectly via downstream task accuracy.

## Bridging the Gap

| Approach | Gap Addressed | Notable Weakness |
|---|---|---|
| AMR | Paraphrase equivalence, predicate-argument structure | No quantifier scope, pragmatics |
| FOL / DRT | Logical inference, quantification | Coverage, scalability |
| SRL | "Who did what" | Event semantics only |
| UD (Enhanced) | Dependency + some semantics | Still syntactic in flavor |
| Vector embeddings | Massive coverage, fuzzy similarity | No explicit meaning, no inference |
|    | distributional meaning |    | 

## The Semantic Gap Today

Despite progress, the gap remains open:

- **Commonsense reasoning**: "The trophy would not fit in the suitcase because it was too big" — what is "too big"? Symbolic and vector systems both struggle.
- **Pragmatics**: Irony, sarcasm, indirect speech acts.
- **Grounding**: Meaning tied to perception and action (embodied semantics).

## Connection to Other Concepts

- [[Two Ways of Thinking About Language]]: AMR and FOL represent the **symbolic** attempt to close the gap; embeddings represent the **statistical** attempt.
- [[Formal Language Theory]]: Provides the syntactic structures that AMR abstracts away from.
- [[Distributional Meaning]]: The basis for vector-based meaning representations.
- [[Latent and Contextual Semantics]]: Contextual embeddings provide dynamic meaning judgments without explicit representation.
- [[Geometric View of Meaning]]: The space in which vector meaning representations are compared.
- [[Sparse Representations]]: The raw material from which meaning must be extracted.
