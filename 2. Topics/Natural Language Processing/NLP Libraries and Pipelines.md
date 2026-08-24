# NLP Libraries and Pipelines

## Overview

An NLP pipeline transforms raw, unstructured text into structured, analyzable representations through a sequence of processing stages. Multiple libraries exist, each offering different trade-offs between speed, accuracy, model coverage, and programming paradigm.

## Core Pipeline Stages

Most NLP pipelines include the following steps:

### 1. Tokenization
Splitting text into atomic units—tokens—which may be words, subwords, or characters.

- **Word tokenization**: Splits on whitespace and punctuation. Handles contractions poorly ("don't" → ["don", "'t"] or ["do", "n't"]).
- **Subword tokenization**: [[The OOV Problem|BPE]], WordPiece, SentencePiece—handles unseen vocabulary by decomposing into known fragments.
- **Character tokenization**: Simplest but produces very long sequences.

### 2. Sentence Segmentation
Detecting sentence boundaries (periods, question marks, exclamation points), complicated by abbreviations ("Dr.") and decimal numbers.

### 3. Part-of-Speech (POS) Tagging
Assigning syntactic categories (noun, verb, adjective, etc.) to each token. Critical for [[Formal Language Theory|syntactic analysis]] and downstream tasks like [[Named Entity Recognition|NER]].

### 4. Lemmatization / Stemming
Reducing inflected forms to a base form.

- **Stemming**: Heuristic rules that chop affixes (Porter, Lancaster).
- **Lemmatization**: Uses vocabulary and morphological analysis to produce a valid lemma ("ran" → "run").

### 5. Dependency Parsing
Building a syntactic tree that represents grammatical relationships between words (subject, object, modifier). [[Statistical Language Models|Statistical parsers]] predict the structure; rule-based parsers use [[Formal Language Theory|formal grammars]].

### 6. Named Entity Recognition (NER)
Identifying and classifying named entities: persons, organizations, locations, dates, quantities, etc.

### 7. Coreference Resolution
Linking pronouns and referring expressions to their antecedents ("The cat ate; *it* was hungry").

## Major Libraries

### NLTK (Natural Language Toolkit)
- **Paradigm**: Educational and research-oriented.
- **Strengths**: Extensive corpora, lexical resources (WordNet), algorithmic implementations.
- **Weaknesses**: Slower; less suitable for production; object-heavy APIs.
- **Use case**: Teaching, prototyping, linguistic research.

### spaCy
- **Paradigm**: Industrial, production-first design.
- **Strengths**: Fast (Cython-based), memory-efficient, pre-trained pipelines for many languages, named entity recognition and dependency parsing out of the box.
- **Features**: `Doc` object with rich linguistic annotations, built-in [[Geometric View of Meaning|word vector]] support, rule-based matching.
- **Use case**: Production applications, information extraction, text classification.

### Hugging Face Transformers
- **Paradigm**: Deep learning, transfer learning.
- **Strengths**: Thousands of pre-trained transformer models (BERT, GPT, T5, RoBERTa, etc.), unified API, [[From Symbols to Spaces|contextual embeddings]].
- **Weaknesses**: Heavy GPU requirements; slower for inference.
- **Use case**: State-of-the-art NLP, [[Latent and Contextual Semantics|contextual semantics]], sequence classification, QA, generation.

### Gensim
- **Paradigm**: Topic modeling and similarity.
- **Strengths**: Efficient implementations of word2vec, fastText, doc2vec, [[Latent Semantic Analysis (LSA)]].
- **Use case**: [[Distributional Meaning|Distributional semantics]], [[Semantic Gap and Meaning Representation|topic modeling]], document similarity.

### Stanford CoreNLP / Stanza
- **Paradigm**: Java-based, research-quality.
- **Strengths**: Mature, comprehensive (all core NLP tasks), high accuracy.
- **Weaknesses**: Java dependency, heavier resource usage.

## Pipeline Architecture Patterns

- **Sequential**: Linear processing; simple but errors propagate.
- **Multi-pass**: Some stages feed back into earlier stages (e.g., parsing improves POS tagging).
- **End-to-end**: Deep learning models (BERT, T5) perform many tasks in a single forward pass, bypassing traditional pipelines entirely.

## Comparison of Libraries

| Feature | spaCy | NLTK | Hugging Face | Gensim |
|---|---|---|---|---|
| Tokenization | ✅ Fast | ✅ Flexible | ✅ Subword | ✅ Simple |
| POS Tagging | ✅ Built-in | ✅ Multiple models | ✅ With fine-tuning | ❌ |
| Dependency Parsing | ✅ Fast | ❌ Basic | ✅ | ❌ |
| NER | ✅ | ✅ | ✅ | ❌ |
| Word Vectors | ✅ | ❌ | ✅ Contextual | ✅ Static |
| Production Ready | ✅ | ❌ | ⚠️ Hardware req. | ⚠️ |
| Pythonic API | ✅ | ⚠️ Verbose | ✅ | ✅ |

## Modern Trends

- **Unified pipelines**: spaCy's `nlp` object encapsulates all stages in one call.
- **Disappearing intermediate representations**: End-to-end transformers bypass explicit tokenization→tagging→parsing.
- **Multilingual support**: spaCy and Hugging Face support 50+ languages.
- **Custom pipeline components**: spaCy allows inserting custom trainable components.

## Libraries vs. Frameworks

The division between **libraries** (spaCy, NLTK) and **model hubs** (Hugging Face) reflects the deeper divide between [[Two Ways of Thinking About Language|rule-based vs. statistical]] approaches, with modern practice favoring the hybrid use of both.
