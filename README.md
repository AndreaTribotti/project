# Multi-Label Story Classification 📚

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AndreaTribotti/project/blob/main/Furlani_Serfilippi_Tribotti_ml_final_project.ipynb)

## 👥 Authors
* **Andrea Tribotti**
* **Sara Furlani**
* **Luca Serfilippi**

---

## 📖 Project Overview
This project focuses on **Multi-Label Text Classification** applied to a corpus of stories. The goal is to predict six predefined tags based on the text content. Unlike standard classification, each story can belong to multiple categories simultaneously.

### The Tags
The models predict the presence of the following narrative elements:
* `BadEnding`
* `Conflict`
* `Dialogue`
* `Foreshadowing`
* `MoralValue`
* `Twist`

---

## 🤖 Models Implemented
We developed and compared three different machine learning approaches, ranging from classical baselines to state-of-the-art Transformers.

### 1. Linear Model (Baseline)
* **Technique:** TF-IDF Vectorizer (5,000 features, unigrams + bigrams) + Logistic Regression.
* **Strategy:** One-vs-Rest Classifier with balanced class weights.
* **Characteristics:** Very fast training (~2 mins), high recall but lower precision.

### 2. Non-Linear Model (Custom Transformer)
* **Architecture:** A custom Transformer-based classifier built from scratch.
* **Components:** Token Embedding, Learned Positional Embedding, 1 Transformer Encoder Layer, Max Pooling.
* **Characteristics:** computationally efficient (~4 mins), higher precision than the baseline.

### 3. DistilBERT (Fine-Tuning)
* **Architecture:** Pre-trained **DistilBERT** (uncased) from Hugging Face.
* **Training:** Fine-tuned for 5 epochs with Binary Cross-Entropy Loss.
* **Characteristics:** Best overall performance (Accuracy & F1-Score), though computationally more expensive (~200 mins training time).

---

## 📊 Results & Performance
We evaluated the models using **Accuracy**, **Precision**, **Recall**, and **F1-Score**.

| Model | Accuracy | Average F1-Score | Training Time |
| :--- | :---: | :---: | :---: |
| **Linear (LogReg)** | 89.11% | 0.70 | ~2 min |
| **Custom Transformer** | 93.99% | 0.71 | ~4 min |
| **DistilBERT** | **94.43%** | **0.78** | ~200 min |

### Key Findings
* **DistilBERT** achieved the best balance between Precision and Recall.
* **Conflict** and **Foreshadowing** were the hardest tags to predict across all models due to their dependency on subtle context rather than specific keywords.
* **BadEnding** and **Dialogue** were the easiest to classify.

---

## 🚀 How to Run
You can run the full analysis directly in your browser using Google Colab. No installation required.

1.  Click the **"Open in Colab"** badge at the top of this README.
2.  Run the cells sequentially to train the models or view the pre-computed results.
