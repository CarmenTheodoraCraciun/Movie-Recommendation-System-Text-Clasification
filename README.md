# Movie-Recommendation-System-Text-Clasification

---

## **1. Project Overview**

This repository hosts a research-oriented recommendation engine designed to suggest movies based on content similarity. The project structures a comparative study between traditional statistical NLP techniques and modern Transformer-based architectures.

By analyzing movie plot summaries, genres, and keywords, the system overcomes the **Cold-Start Problem** (recommending without user history). The core objective is to optimize **Precision@K** and visualize the semantic relationships between films using dimensionality reduction.

## **2. Methodology & Architectures**

The project implements a progressive pipeline, treating the problem through four levels of complexity:

### **Level 1: Statistical Optimization (LSA)**

* **Technique:** TF-IDF (Term Frequency-Inverse Document Frequency) followed by Truncated SVD (Latent Semantic Analysis).
* **Goal:** To compress sparse vectors (5000+ words) into dense latent concepts (~50 dimensions).
* **Performance:** Effective for exact keyword matching but struggles with synonyms and context.

### **Level 2: Semantic Search (SBERT - Bi-Encoder)**

* **Technique:** Utilizes the `all-mpnet-base-v2` Sentence Transformer.
* **Goal:** To generate dense vector embeddings where distance represents semantic meaning.
* **Innovation:** Implements "Prompt Engineering" for embeddings by structuring input text as: `[Title] + [Genres] + [Keywords] + [Overview]`.

### **Level 3: Hybrid System (Weighted Ensemble)**

* **Technique:** Mathematical combination of Normalized SBERT vectors and LSA vectors.
* **Formula:** 
* **Goal:** To leverage the contextual power of Transformers while retaining the keyword specificity of statistical models.


* **Performance:** Achieves State-of-the-Art accuracy by simulating a "reading comprehension" task rather than simple vector distance.

## **3. Visualization**

The project includes a custom **Dual-View Visualization Engine**:

1. **Global Map:** Uses **t-SNE** to project the high-dimensional movie universe into 2D, revealing genre clusters.
2. **Local Zoom:** Dynamically focuses on the query movie and its top 10 recommendations, using `adjustText` to prevent label overlapping.

## **4. Key Results**

The evolution of the model shows a clear trajectory in performance (measured via Genre Matching Precision):

| Model Architecture | Technology | Accuracy (Approx) | Characteristics |
| --- | --- | --- | --- |
| **Baseline** | LSA / SVD | 83.80% | Fast, rigid, misses context. |
| **Deep Learning** | SBERT (MPNet) | 89.60% | Understands context, good clustering. |
| **Hybrid** | MPNet + LSA | 92.00% | Balanced, robust against edge cases. |
