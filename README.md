# Coding Pattern Recognition Engine (ML + NLP)

## Overview
A supervised NLP project to classify coding problems into 7 algorithmic patterns using TF-IDF and linear models.

---

## Problem
**Input:** Problem description  
**Output:** Algorithmic pattern  

Classes:
- Two Pointers
- Sliding Window
- Binary Search  
- Dynamic Programming
- Graph
- Greedy  
- Heap / Priority Queue  

---

## Dataset
- ~700 manually curated problems (~100 per class)  
- Balanced across 7 categories  
- Stratified train/test split  

⚠️ Dataset not included (sourced from NeetCode / LeetCode).

---

## Approach
- Text preprocessing (cleaning, normalization)  
- TF-IDF (unigrams + bigrams)  
- Logistic Regression (baseline model)  
- Evaluation: Accuracy, Precision, Recall, F1  

---

## Results

| Model | Accuracy |
|------|--------|
Baseline | ~0.15 |
TF-IDF + LR (Unigrams) | ~0.44 |
TF-IDF + LR (Bigrams) | **~0.71** |

Macro F1 ≈ **0.71**

---

## Key Insights
- Performance improved significantly with more data and bigrams  
- Graph problems perform best due to distinctive vocabulary  
- Greedy & DP are harder due to semantic overlap  
- TF-IDF captures lexical patterns but struggles with conceptual differences  

---

## Tech Stack
Python, Pandas, Scikit-learn, TF-IDF, Logistic Regression

---

## Author
Isha Patel  
Final-year IT student
