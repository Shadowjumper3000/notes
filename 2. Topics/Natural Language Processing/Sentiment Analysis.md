**Tags:** #hub #nlp #sentiment
**Related:** [[Natural Language Processing]], [[Naïve Bayes]], [[Logistic Regression]]

## Overview
Sentiment Analysis, often referred to as **Opinion Mining**, is the branch of Natural Language Processing dedicated to identifying, extracting, and quantifying subjective information—such as emotions, attitudes, and opinions—from textual data. It addresses the fundamental question: "How does the author feel about a specific topic?" This field has evolved from basic binary polarity detection (e.g., positive vs. negative) to nuanced multiclass classification (e.g., extremely satisfied to extremely dissatisfied) and fine-grained aspect-based analysis that pinpoints the specific target of an opinion within a sentence.

## Technical Depth
There are three primary methodologies used in Sentiment Analysis:
1. **Lexicon-Based Approaches:** These methods rely on pre-built dictionaries (lexicons) where words are assigned sentiment scores. A document's overall sentiment is calculated as the sum or average of the scores of its constituent words. For example, **VADER** (Valence Aware Dictionary and sEntiment Reasoner) is a popular lexicon-based tool specifically tuned for social media text. It accounts for linguistic nuances like intensity (using CAPS or punctuation) and negation (e.g., "not good").
2. **Machine Learning Approaches:** These involve training supervised classifiers like Naïve Bayes, Support Vector Machines (SVM), or Logistic Regression on labeled datasets. These models often use features like Bag-of-Words (BoW) or N-grams. The challenge here is the reliance on high-quality labeled data and the risk of being domain-specific (e.g., a "fast" car is good, but a "fast" battery drain is bad).
3. **Deep Learning Approaches:** Modern state-of-the-art systems utilize pre-trained Transformers (like BERT or RoBERTa) which are fine-tuned for sentiment tasks. These models capture context and long-range dependencies, allowing them to handle complex linguistic phenomena like sarcasm, irony, and double negatives that often confuse simpler models.

**Aspect-Based Sentiment Analysis (ABSA)** is a more granular task that decomposes sentiment into three components: the **Aspect Term** (e.g., "service"), the **Sentiment** (e.g., "slow"), and the **Entity** (e.g., "The restaurant"). This allows businesses to understand exactly what part of their product or service is receiving praise or criticism.

## Applications/Examples
Sentiment Analysis is widely used in:
- **Brand Monitoring:** Tracking social media mentions and news articles to gauge public perception of a company or product.
- **Customer Feedback:** Automatically categorizing thousands of support tickets or product reviews to identify common pain points.
- **Stock Market Prediction:** Using sentiment from news feeds and social media to predict market trends (often referred to as "sentiment-driven trading").
- **Political Analysis:** Monitoring public opinion on candidates or policies during election cycles.

## References
- Liu, B. (2020). *Sentiment Analysis: Mining Opinions, Sentiments, and Emotions*.
- Hutto, C. J., & Gilbert, E. (2014). "VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text."
- Jurafsky, D., & Martin, J. H. *Speech and Language Processing* (3rd ed. draft).
- Zhang, L., et al. (2018). "Deep Learning for Sentiment Analysis: A Survey."

## Knowledge Map

### 1. Core Tasks
- [[Opinion Mining]]
- [[Subjectivity vs Objectivity in Text]]

### 2. Lexicon-Based Approaches
- [[Sentiment Lexicons]]
- [[VADER]]

### 3. ML-Based Approaches
- [[Aspect-Based Sentiment Analysis]]

> [!question]- Common Exam Questions
> - What is the difference between subjectivity detection and polarity classification?
> - How does VADER handle negation and intensifiers?
> - What are the limitations of lexicon-based sentiment analysis on domain-specific text?
> - What makes aspect-based sentiment analysis harder than document-level SA?

