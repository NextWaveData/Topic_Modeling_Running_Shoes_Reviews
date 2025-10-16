# Multilingual Running Shoes Reviews Analysis  
**Understanding what customers say about running shoes using NLP and BERTopic**
---

## Overview

This project explores **30,000+ online reviews of running shoes** written in **Italian, French, and English**.  
Using **Natural Language Processing (NLP)** and **BERTopic**, the goal is to understand what customers talk about most, from comfort and fit to quality, design, and value for money.

It’s an **end-to-end multilingual pipeline** covering:  
Data cleaning → Semantic embeddings (MPNet) → Topic modeling → Evaluation → Human interpretation.

---

## Goals

- Identify key **themes** in customer reviews across languages  
- Compare linguistic and sentiment patterns  
- Turn unstructured feedback into **actionable business insights**

---

## Project Workflow

<p align="center">
  <b>BERTopic Pipeline</b><br>
  <img src="results/figures/bertopic_pipeline.png" alt="BERTopic Pipeline Diagram" width="700"/>
</p>



The figure above summarizes the full process:
1. **Web Scraping** from public e-commerce pages (Decathlon, Amazon, Zalando)  
2. **EDA & Cleaning** to handle duplicates, encoding errors, and detect language  
3. **Word Embeddings** with MPNet  
4. **Dimensionality Reduction** using UMAP  
5. **Clustering** with HDBSCAN  
6. **Tokenizer & Weighting** via c-TF-IDF (BERTopic)  
7. **Evaluation & Fine-Tuning** for coherence and interpretability  
8. **Results & Insights** for customer understanding

## Methodology

| Step | Description |
|------|--------------|
| **EDA & Cleaning** | Handle missing values, encoding errors, and language detection |
| **Preprocessing** | Multilingual stopwords, normalization, text cleaning |
| **Embeddings** | SentenceTransformer (`all-mpnet-base-v2`) |
| **Topic Modeling** | UMAP + HDBSCAN + BERTopic |
| **Evaluation** | Coherence (c_v), silhouette, % noise |
| **Topic Reduction** | Merge similar topics into macro-categories |

---

## Dataset

- **Size:** ~30k reviews  
- **Languages:** 🇮🇹 Italian, 🇫🇷 French, 🇬🇧 English  
- **Sources:** Decathlon (52%), Amazon (36%), Zalando (12%)  
- **Timeframe:** Nov 2024 – Feb 2025  
- **Fields:** Product info, technical specs, ratings, and text reviews  

---

## Main Results

### Top Macro-Categories

| Category | Description | Share |
|-----------|-------------|-------|
| **Comfort & Fit** | How shoes feel, adapt, and support | ~50% |
| **Performance & Cushioning** | Running efficiency and energy return | ~20% |
| **Quality & Durability** | Longevity and material quality | ~10% |
| **Design & Style** | Aesthetic preferences and branding | ~8% |
| **Price & Value** | Perceived fairness and expectations | ~7% |
| **Purchase Experience** | Delivery, sizing, returns | ~5% |

**Model performance:**  
- *Coherence:* 0.68 (after topic reduction)  
- *Silhouette score:* 0.38  
- *Noise:* ~15%

---

## Key Insights

### General Findings
- **Comfort and fit** are the strongest drivers of satisfaction across all languages.  
  Customers consistently associate comfort, foot support, and fit precision with positive ratings.  
- **Durability and quality** emerge as the most frequent negative aspects, especially for high-performance models.  
- **Price fairness** appears in both positive and negative reviews; people praise good deals but criticize overpriced products.  
- **French** reviews often discuss **value-for-money** and **aesthetic appeal**, while **Italian** reviews include more **contextual and emotional tone** (e.g. “great for daily runs”).  
- **English** reviews are shorter and more direct, focusing mainly on **comfort** and **durability**.

### Business Implications
- Highlight “comfort-driven design” in **product storytelling**.  
- Invest in **durability communication** (materials, lifespan).  
- Localize content:  
  - 🇮🇹 Focus on emotional and lifestyle tone  
  - 🇫🇷 Emphasize quality/price ratio  
  - 🇬🇧 Keep concise, technical information  
- Monitor recurring mentions of **sizing issues** and **wear resistance** for product feedback loops.

---

## Tech Stack

**Languages & Tools:**  
Python 3.11 · pandas · numpy · matplotlib · seaborn · spaCy · nltk · ftfy  
sentence-transformers · BERTopic · umap-learn · hdbscan · gensim · scikit-learn  


---

## Limitations

- **Short reviews:** Most comments are under 30 words, limiting topic coherence.  
- **Language imbalance:** English reviews dominate, slightly biasing results.  
- **Hardware constraints:** The analysis was run on CPU, preventing large-scale fine-tuning.  
- **Sentiment approximation:** Ratings were used as sentiment labels (not direct text classification).  
- **Temporal gap:** Reviews were scraped over different months, so no consistent time trend was analyzed.  



