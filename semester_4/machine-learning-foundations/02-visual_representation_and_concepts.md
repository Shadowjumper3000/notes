## Tomek Links

- **Definition**: Tomek Links are pairs of nearest neighbors of opposite classes in a dataset that can be used to identify noisy or borderline instances.
- **Purpose**: They help in cleaning datasets by removing ambiguities, improving classifier performance.
- **Visualization**:
    - **Point A (Class 1)** and **Point B (Class 2)** form a Tomek Link if the distance between them is minimal and no other point is closer to either.
    - Removal of such links typically results in better class separation.

---

## Empty Bag of Words

- **Definition**: A Bag of Words (BoW) model represents text data as a collection of word counts or occurrences, ignoring grammar and word order.
- **Empty Bag of Words**:
    - A scenario where no meaningful tokens exist in the text (e.g., completely filtered out after preprocessing).
    - Could occur due to overly aggressive text cleaning (e.g., removing all stopwords).
- **Implications**:
    - Indicates issues in preprocessing or insufficient vocabulary.
    - Leads to sparse and meaningless representations.

---

## Empty Bag of N Words

- **Definition**: Similar to the Bag of Words model, but considers **n-grams** (sequences of `n` words).
- **Empty Bag of N Words**:
    - Happens when no `n-grams` are generated, possibly due to insufficient text length or overly restrictive preprocessing.
    - Example: For `n=3`, a two-word sentence would result in no n-grams.
- **Visualization**:
    - Imagine a matrix where all rows (representing n-grams) are zero.

---

### Common Issues and Solutions:

1. **Issue**: Empty bags due to aggressive text preprocessing.
    - **Solution**: Tune preprocessing steps to retain relevant tokens.
2. **Issue**: Insufficient vocabulary.
    - **Solution**: Expand the vocabulary or use pre-trained embeddings.
3. **Issue**: No n-grams due to small text size.
    - **Solution**: Adjust `n` value or pad sequences.

---

### General Notes:

- These concepts are vital for understanding data cleaning, text representation, and dataset preparation.
- Visualizing sparse matrices or removed Tomek Links can provide insights into dataset quality and preprocessing effects.

## Topic Modeling

- **Definition**: A method for uncovering hidden semantic structures in text data by identifying topics across a collection of documents.
- **Common Algorithms**:
    1. **Latent Dirichlet Allocation (LDA)**: A probabilistic model assuming each document is a mixture of topics.
    2. **Non-Negative Matrix Factorization (NMF)**: Decomposes the document-term matrix into topic-term and document-topic matrices.
    3. **Latent Semantic Analysis (LSA)**: Uses singular value decomposition (SVD) to reduce the dimensionality of the document-term matrix.
- **Key Steps**:
    1. **Preprocessing**: Tokenize, remove stopwords, and stem/lemmatize the text.
    2. **Vectorization**: Convert text into numerical format (e.g., Bag of Words or TF-IDF).
    3. **Modeling**: Apply a topic modeling algorithm to extract topics.
    4. **Interpretation**: Analyze the terms within each topic to identify themes.
- **Applications**:
    - Document clustering.
    - Content recommendation systems.
    - Summarization of large text corpora.

---

## Features for Time Series

- **Definition**: Extracting meaningful attributes from raw time series data to use as inputs for machine learning models.
- **Types of Features**:
    1. **Statistical Features**:
        - Mean, median, variance, standard deviation, skewness, kurtosis.
    2. **Frequency Domain Features**:
        - Power spectral density, dominant frequencies, Fourier coefficients.
    3. **Time Domain Features**:
        - Peaks, troughs, autocorrelation, moving averages.
    4. **Derived Features**:
        - Rolling statistics, differences between successive observations.
- **Feature Extraction Tools**:
    - **tsfresh**: Automatically extracts a large set of features.
    - **Catch22**: Provides 22 well-known features for time series.
    - **PyWavelets**: For wavelet transform features.
- **Applications**:
    - Anomaly detection.
    - Forecasting (e.g., stock prices, weather).
    - Activity recognition.

---

## Feature Concatenation

- **Definition**: Combining features from multiple sources or data types into a single feature vector for machine learning models.
- **Approaches**:
    1. **Horizontal Concatenation**:
        - Concatenate features side-by-side to expand the feature space.
        - Example: Combining numerical features and one-hot encoded categorical features.
    2. **Vertical Concatenation**:
        - Stack feature vectors from different samples vertically to augment the dataset size.
    3. **Hybrid Concatenation**:
        - Combine horizontally concatenated features with additional features derived from domain knowledge.
- **Best Practices**:
    - Normalize or standardize features before concatenation to avoid scale issues.
    - Handle missing values appropriately in each feature set.
    - Use feature selection or dimensionality reduction to avoid overfitting.
- **Applications**:
    - Multimodal data fusion (e.g., combining image and text features).
    - Ensemble models requiring diverse feature representations.
    - Time series datasets with features from different time windows.

# Notes: Topic Modeling, Time Series Features, and Feature Concatenation

## Topic Modeling

- **Definition**: A method for uncovering hidden semantic structures in text data by identifying topics across a collection of documents.
- **Common Algorithms**:
    1. **Latent Dirichlet Allocation (LDA)**: A probabilistic model assuming each document is a mixture of topics.
    2. **Non-Negative Matrix Factorization (NMF)**: Decomposes the document-term matrix into topic-term and document-topic matrices.
    3. **Latent Semantic Analysis (LSA)**: Uses singular value decomposition (SVD) to reduce the dimensionality of the document-term matrix.
- **Key Steps**:
    1. **Preprocessing**: Tokenize, remove stopwords, and stem/lemmatize the text.
    2. **Vectorization**: Convert text into numerical format (e.g., Bag of Words or TF-IDF).
    3. **Modeling**: Apply a topic modeling algorithm to extract topics.
    4. **Interpretation**: Analyze the terms within each topic to identify themes.
- **Applications**:
    - Document clustering.
    - Content recommendation systems.
    - Summarization of large text corpora.

---

## Features for Time Series

- **Definition**: Extracting meaningful attributes from raw time series data to use as inputs for machine learning models.
- **Types of Features**:
    1. **Statistical Features**:
        - Mean, median, variance, standard deviation, skewness, kurtosis.
    2. **Frequency Domain Features**:
        - Power spectral density, dominant frequencies, Fourier coefficients.
    3. **Time Domain Features**:
        - Peaks, troughs, autocorrelation, moving averages.
    4. **Derived Features**:
        - Rolling statistics, differences between successive observations.
- **Feature Extraction Tools**:
    - **tsfresh**: Automatically extracts a large set of features.
    - **Catch22**: Provides 22 well-known features for time series.
    - **PyWavelets**: For wavelet transform features.
- **Applications**:
    - Anomaly detection.
    - Forecasting (e.g., stock prices, weather).
    - Activity recognition.

---

## Feature Concatenation

- **Definition**: Combining features from multiple sources or data types into a single feature vector for machine learning models.
- **Approaches**:
    1. **Horizontal Concatenation**:
        - Concatenate features side-by-side to expand the feature space.
        - Example: Combining numerical features and one-hot encoded categorical features.
    2. **Vertical Concatenation**:
        - Stack feature vectors from different samples vertically to augment the dataset size.
    3. **Hybrid Concatenation**:
        - Combine horizontally concatenated features with additional features derived from domain knowledge.
- **Best Practices**:
    - Normalize or standardize features before concatenation to avoid scale issues.
    - Handle missing values appropriately in each feature set.
    - Use feature selection or dimensionality reduction to avoid overfitting.
- **Applications**:
    - Multimodal data fusion (e.g., combining image and text features).
    - Ensemble models requiring diverse feature representations.
    - Time series datasets with features from different time windows.

---

## Cutting the Long Tail

- **Definition**: Reducing the influence of infrequent or rare features in the dataset, often for efficiency or noise reduction.
- **Techniques**:
    1. **Thresholding**: Removing features appearing less than a specified number of times.
    2. **Truncating Tail**: Only keeping top-k features based on frequency or importance.
- **Applications**:
    - Text classification to focus on dominant terms.
    - Reducing dimensionality in large datasets.
- **Challenges**:
    - Risk of losing rare but meaningful features.

---

## Boruta

- **Definition**: A wrapper feature selection method based on Random Forest.
- **Process**:
    1. Creates shadow features by shuffling original features.
    2. Trains a Random Forest model and compares the importance of original features to shadow features.
    3. Retains features that consistently outperform shadow features.
- **Advantages**:
    - Identifies all relevant features, not just a subset.
    - Works well for non-linear relationships.
- **Applications**:
    - High-dimensional datasets.
    - Feature selection in genomic or financial data.

---

## L1-Regularization (Lasso Regression)

- **Definition**: A regression method that applies L1 penalty to reduce feature coefficients to zero, effectively performing feature selection.
- **Key Properties**:
    - Encourages sparsity in feature coefficients.
    - Helps in interpreting models by highlighting important features.
- **Applications**:
    - Regression problems with many irrelevant features.
    - Reducing overfitting in linear models.
- **Limitations**:
    - Can struggle when features are highly correlated.

---

## Task-Specific Feature Selection

- **Definition**: Selecting features tailored to the specific requirements of a machine learning task.
- **Approaches**:
    1. **Domain Knowledge**: Leveraging expertise to manually select relevant features.
    2. **Automated Methods**: Using algorithms like Mutual Information, Recursive Feature Elimination (RFE).
    3. **Task-Driven Metrics**: Selecting features based on their performance for the target metric (e.g., precision, recall).
- **Applications**:
    - Optimizing for specific metrics in classification tasks.
    - Customizing features for domain-specific problems (e.g., medical diagnosis, fraud detection).