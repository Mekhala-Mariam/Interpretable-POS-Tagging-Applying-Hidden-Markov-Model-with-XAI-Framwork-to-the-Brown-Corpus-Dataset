# Interpretable POS Tagging via HMM & XAI

**Author:** Mekhala Mariam Mary  
**Student ID:** 17101368  

---

## 📄 Abstract
Prepared by Mekhala Mariam Mary, ID:17101368. Part-of-speech tagging identifies a word's syntactic category based on context. Used to quickly disambiguate natural language with high accuracy, it supports critical NLP tasks like speech synthesis pronunciation (e.g., noun "discount" vs. verb "dis-count"), information retrieval, and word sense resolution.

---

## 📌 Project Overview
While modern NLP relies heavily on deep neural networks, their "black-box" nature makes structural debugging difficult. This project presents an inherently interpretable (ante-hoc) sequence labeling pipeline by applying a first-order **Hidden Markov Model (HMM)** optimized via the **Baum-Welch algorithm** to the **Brown Corpus dataset** (mapped to the Universal Tagset). 

Instead of relying on post-hoc surrogates (like LIME or SHAP), this system treats its actual parameter matrices as its explanation layer, achieving high performance alongside absolute mathematical traceability.

### 📊 Performance Highlights
* **Global POS Accuracy:** `94.2%` on unseen test data.
* **Macro F1-Score:** `0.91`, ensuring stability across infrequent tags.
* **Convergence:** Optimization routine successfully stabilizes by **Iteration 15**.

---

## 🔍 Explainable AI (XAI) Matrix
* **Global Interpretability:** Row-normalized transition matrices ($A$) serve as the model’s "internal grammar book" (e.g., a learned probability of `0.85` for the `DET` $\rightarrow$ `NOUN` transition).
* **Local Interpretability:** Emission profiles ($B$) track localized word attribution drivers (e.g., $P(\text{"time"} \mid \text{NOUN}) = 0.0124$).

---

## 📁 Repository Structure

```text
├── data/                  # Data downloading and mapping utilities
├── src/                   # Core Source Code
│   ├── preprocessing.py   # Universal mapping, boundary padding, and OOV handling
│   ├── model.py           # Baum-Welch training and Viterbi decoding implementation
│   └── visualize.py       # Code for transition heatmaps and emission bar charts
├── requirements.txt       # Project python dependencies
└── README.md              # Project documentation (This file)
