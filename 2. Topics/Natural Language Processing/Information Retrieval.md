**Tags:** #topic #hub #nlp
**Related:** [[Natural Language Processing]], [[TF–IDF]]

## Overview
Information Retrieval (IR) is the science and engineering of finding material (usually documents) of an unstructured nature (usually text) that satisfies an information need within large collections. Unlike information extraction, which seeks to identify specific facts, IR is fundamentally a ranking problem. It involves processing a user query and comparing it against a corpus of documents to return a set of results ordered by their **relevance**. As the volume of digital information has exploded, IR has moved from simple keyword matching to sophisticated models that incorporate semantics, link analysis (like PageRank), and personalized user history.

## Technical Depth
The foundation of modern IR is the **Vector Space Model (VSM)**, where both documents and queries are represented as vectors in a high-dimensional space. The similarity between them is typically calculated using the **Cosine Similarity** of their vectors. To represent these vectors effectively, IR systems use weighting schemes like **TF-IDF (Term Frequency-Inverse Document Frequency)** to balance the importance of words that appear frequently in a document against their overall prevalence in the corpus.

$$\text{TF-IDF}(t, d, D) = \text{TF}(t, d) \times \text{IDF}(t, D)$$
Where:
- **TF (Term Frequency):** Measures how frequently a term $t$ occurs in a document $d$.
- **IDF (Inverse Document Frequency):** $\log(N/n_t)$, where $N$ is the total number of documents and $n_t$ is the number of documents containing term $t$. This penalizes common words like "the" or "and."

Beyond the VSM, other key models include:
- **Probabilistic Models (e.g., BM25):** The current industry standard for ranking, BM25 (Best Matching 25) is a sophisticated variant of TF-IDF that incorporates document length normalization and term frequency saturation, making it more robust in real-world scenarios.
- **Latent Semantic Analysis (LSA):** Uses Singular Value Decomposition (SVD) to project documents into a lower-dimensional latent space, allowing the system to retrieve documents that are semantically related even if they don't share identical keywords (e.g., "car" and "automobile").
- **Neural/Dense Retrieval:** The most recent advancement, which uses dual-encoder Transformers (like BERT) to map queries and documents into a shared dense embedding space, where relevance is determined by the dot product or cosine distance between embeddings.

## Applications/Examples
Information Retrieval is the engine behind:
- **Web Search Engines:** Google, Bing, and DuckDuckGo use IR to index and rank billions of web pages.
- **Enterprise Search:** Companies use IR systems to allow employees to search across internal emails, wikis, and document repositories.
- **Legal and Medical Discovery:** IR tools help lawyers and doctors find relevant case law or medical research from massive databases.
- **Recommendation Systems:** Often modeled as a retrieval problem where "relevant" items are those the user is likely to interact with based on their historical behavior.

## References
- Manning, C. D., Raghavan, P., & Schütze, H. (2008). *Introduction to Information Retrieval*.
- Croft, B., Metzler, D., & Strohman, T. (2010). *Search Engines: Information Retrieval in Practice*.
- Robertson, S., & Zaragoza, H. (2009). "The Probabilistic Relevance Framework: BM25 and Beyond."
- Jurafsky, D., & Martin, J. H. *Speech and Language Processing* (3rd ed. draft).

## Knowledge Map
### 1. Concepts
- [[Information Retrieval vs Information Extraction]]
- [[Statistical Relevance]]

### 2. Mechanisms
- [[Relevance Feedback]]
- [[TF–IDF]]
- [[Cosine Similarity]]

### 3. Constraints
- [[Limits of Statistical Relevance]]

<!-- unified:backlinks:start -->
## Topic Backlinks

- Knowledge Representation
<!-- unified:backlinks:end -->
