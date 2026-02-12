# Multi-Label Story Classification 📚

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AndreaTribotti/project/blob/main/Furlani_Serfilippi_Tribotti_ml_final_project.ipynb)

## 👥 Authors
* **Andrea Tribotti**
* **Sara Furlani**
* **Luca Serfilippi**

---

## 📖 Project Overview
This project focuses on **Multi-Label Text Classification** applied to the **TinyStories dataset**, a corpus of short children's stories written with simple vocabulary. The objective is to predict six predefined narrative tags based on the story content. Unlike standard classification, each story can belong to multiple categories simultaneously.

### 📊 Dataset Details
* **Source:** TinyStories dataset.
* **Scale:** The dataset consists of a **train set** (2,735,100 stories) and a **test set** (10,000 stories).
* **Methodology:** We utilized a subset of 250,000 stories for training and validation to optimize computational resources.
* **Integrity:** The test set was used exclusively for final evaluation to ensure unbiased performance metrics.
### 🏷️ Target Tags
The models are designed to identify the following six narrative elements:
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

### 3. [DistilBERT](https://huggingface.co/distilbert/distilbert-base-uncased) (Fine-Tuning)
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
2.  Run the cells sequentially to train the models.
