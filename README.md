# Coding Pattern Recognition Engine (ML + NLP)

## Overview
This project explores whether classical Natural Language Processing (NLP) techniques can infer **algorithmic problem-solving patterns** directly from coding problem descriptions.
The task is formulated as a **7-class supervised text classification problem**, where the model predicts the dominant algorithmic strategy required to solve a given coding problem.
The goal of this project is to evaluate how well classical machine learning models combined with TF-IDF text representations can distinguish between different algorithmic patterns.

## Problem Definition

**Input:**  
Natural language description of a coding problem.

**Output:**  
Predicted algorithmic pattern.

### Target Classes
- Two Pointers  
- Sliding Window  
- Binary Search  
- Dynamic Programming  
- Graph  
- Greedy  
- Heap / Priority Queue  

This is a **single-label multi-class classification problem.**

## Dataset

- ~240 manually curated coding problems
- Each problem assigned a **single dominant algorithmic pattern**
- Balanced class distribution across 7 categories
- Dataset cleaned and stored as CSV
- Stratified train/test split (80/20)

⚠️ **Note:**  
The dataset is not included in this repository due to licensing restrictions of the original problem sources (NeetCode / LeetCode).

## Machine Learning Pipeline

### 1. Text Preprocessing
- Lowercasing
- Encoding cleanup
- Punctuation removal
- Whitespace normalization

### 2. Feature Representation
TF-IDF vectorization was used to convert problem descriptions into numerical features.

Experiments included:
- Unigram TF-IDF
- Unigram + Bigram TF-IDF

### 3. Baseline
A **majority class baseline** was computed to establish a minimum benchmark.

### 4. Models Tested
- Logistic Regression
- Linear Support Vector Machine (SVM)

### 5. Evaluation Metrics
Models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

## Results

| Model | Features | Accuracy |
|------|------|------|
Majority Baseline | - | ~0.15 |
Logistic Regression | TF-IDF (Unigrams) | ~0.44 |
Logistic Regression | TF-IDF (Unigrams + Bigrams) | ~0.46 |
Linear SVM | TF-IDF | ~0.43 |

Macro F1 score ≈ **0.45**

The classifier achieves approximately **3× improvement over the majority baseline**, indicating that algorithmic patterns can be partially inferred from problem descriptions.

## Key Observations

### Graph Problems Perform Best
Graph-related problems contain distinctive vocabulary such as:
- node
- edge
- bfs
- dfs

These lexical cues make them easier for the model to identify.

### Strategy Overlap Limits Performance
Conceptual patterns such as **Dynamic Programming** and **Greedy** often share similar vocabulary (e.g., “maximum”, “minimum”, “cost”), making them harder to distinguish using bag-of-words representations.

### Representation Bottleneck
Performance plateaus around **45–50% accuracy**, suggesting that classical TF-IDF representations capture surface-level lexical patterns but struggle with deeper semantic reasoning.

## Key Insight

This experiment demonstrates that **classical bag-of-words representations can partially infer algorithmic solution strategies from natural language descriptions**, but their effectiveness is limited when strategies differ conceptually rather than lexically.

More expressive semantic representations (such as transformer-based embeddings) may improve performance for this task.

## Project Structure

coding-pattern-recognition-ml/

├── notebooks/  
│   └── modeling.ipynb        # Full ML pipeline and experiments  

├── results/  
│   └── model_results.png     # Evaluation output screenshot  

├── README.md                 # Project documentation  

├── requirements.txt          # Python dependencies  

└── .gitignore                # Files ignored by Git

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- TF-IDF Vectorization
- Logistic Regression
- Linear SVM

## Installation

Install required dependencies:
pip install -r requirements.txt

## Future Work

Possible improvements include:

- Transformer-based sentence embeddings
- Larger dataset (500–1000 samples per class)
- Structural feature extraction from problem statements
- Multi-label classification for problems with multiple valid strategies

## Author

**Isha Patel**  
Final-year Information Technology student exploring applied Machine Learning and NLP experimentation.
