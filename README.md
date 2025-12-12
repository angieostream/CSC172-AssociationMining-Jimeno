# Symptom Association Analysis using Apriori Algorithm  
**CSC172 Data Mining and Analysis Final Project**   
*Mindanao State University - Iligan Institute of Technology*   
**Student:** Angelyn Jimeno, 2022-4037    
**Semester:** AY 2025-2026 Sem 1 

## Abstract
This project implements the Apriori algorithm for association rule mining on the **Disease Symptom Prediction** dataset containing approximately 4,920 patient transactions. The goal is to identify strong "symptom clusters" to aid in differential diagnosis. The analysis pipeline includes data preprocessing (one-hot encoding of sparse symptom lists), exploratory data analysis (EDA), rule generation, and evaluation using **Support, Confidence, Lift, Conviction, and Leverage**. Clinical insights and actionable diagnostic rules are derived from the strongest associations found in the data.

## Table of Contents
- [Abstract](#abstract)
- [1. Introduction](#1-introduction)
  - [1.1 Problem Statement](#11-problem-statement)
  - [1.2 Objectives](#12-objectives)
  - [1.3 Scope and Limitations](#13-scope-and-limitations)
- [2. Dataset Description](#2-dataset-description)
  - [2.1 Source and Acquisition](#21-source-and-acquisition)
  - [2.2 Data Structure](#22-data-structure)
  - [2.3 Sample Transactions](#23-sample-transactions)
- [3. Methodology](#3-methodology)
  - [3.1 Data Preprocessing](#31-data-preprocessing)
  - [3.2 Exploratory Data Analysis](#32-exploratory-data-analysis)
  - [3.3 Apriori Algorithm Implementation](#33-apriori-algorithm-implementation)
  - [3.4 Evaluation Metrics](#34-evaluation-metrics)
- [4. Results](#4-results)
  - [4.1 Top Association Rules](#41-top-association-rules)
  - [4.2 Key Visualizations](#42-key-visualizations)
  - [4.3 Performance Metrics](#43-performance-metrics)
- [5. Discussion](#5-discussion)
  - [5.1 Clinical Insights](#51-clinical-insights)
  - [5.2 Actionable Recommendations](#52-actionable-recommendations)
  - [5.3 Limitations](#53-limitations)
- [6. Conclusion](#6-conclusion)
- [7. Video Presentation](#7-video-presentation)
- [References](#references)
- [Appendix: Full Results](#appendix-full-results)

## 1. Introduction
### 1.1 Problem Statement
In healthcare, accurate differential diagnosis relies on recognizing patterns of co-occurring symptoms. However, relying solely on intuition can lead to missed diagnoses. This project applies data mining to patient symptom data to statistically uncover "symptom clusters" and generate rules that predict potential conditions based on initial presenting symptoms.

### 1.2 Objectives
- Preprocess medical dataset to standardize symptom labels and handle missing values
- Implement Apriori algorithm with parameter tuning for sparse medical data
- Generate and evaluate diagnostic association rules
- Visualize symptom heatmaps and derive clinical insights

### 1.3 Scope and Limitations
**Scope:** Analysis of symptom co-occurrence patterns to identify potential syndromes using the Apriori algorithm.  
**Limitations:** The dataset represents a static snapshot of patient cases. The analysis identifies correlation (co-occurrence), not necessarily biological causation.

## 2. Dataset Description
### 2.1 Source and Acquisition
**Source:** [Disease Symptom Prediction (Kaggle)](https://www.kaggle.com/datasets/itachi9604/disease-symptom-description-dataset)  
**Size:** ~4,920 transactions (Patient Cases), 132 unique symptoms  
**Format:** Disease Label + List of Symptoms (Wide Format)

### 2.2 Data Structure
**Raw format (Wide):**
Rows represent patients; columns represent potential symptoms. Most cells are empty (NaN) because patients only exhibit a few symptoms out of hundreds.

**Transaction format (Processed):**
A boolean matrix where rows are patients and columns are symptoms (True/False).

### 2.3 Sample Transactions
* **Transaction 1:** `['itching', 'skin_rash', 'nodal_skin_eruptions', 'dischromic_patches']`
* **Transaction 2:** `['continuous_sneezing', 'shivering', 'chills', 'watering_from_eyes']`
* **Transaction 3:** `['stomach_pain', 'acidity', 'ulcers', 'vomiting']`

## 3. Methodology

### 3.1 Data Preprocessing
1.  **Cleaning:** String standardization (removing underscores, trimming whitespace).
2.  **Imputation:** Handling `NaN` values in the raw dataset.
3.  **Encoding:** Converting symptom lists into a One-Hot Encoded matrix using `mlxtend.preprocessing.TransactionEncoder`.
4.  **Sparsity Handling:** Resulting matrix is highly sparse (most values are 0).

### 3.2 Exploratory Data Analysis
* **Frequency Analysis:** Identifying the most common symptoms across all diseases.
* **Distribution:** analyzing the average number of symptoms per patient case.
* **Co-occurrence:** Generating heatmaps to visualize which symptoms frequently appear together before running the algorithm.

### 3.3 Apriori Algorithm Implementation
**Implementation:** `mlxtend.frequent_patterns.apriori()` to find frequent itemsets followed by `association_rules()` to generate metrics.
**Parameters:** Initial tuning targets `min_support=0.01`, `min_confidence=0.5`.

### 3.4 Evaluation Metrics
- **Support:** Percentage of patients having the symptom set.
- **Confidence:** Probability of Symptom B appearing if Symptom A is present.
- **Lift:** Strength of the association (Is it a coincidence?).
- **Conviction:** The dependency of the consequent on the antecedent.
- **Leverage:** Difference between observed and expected co-occurrence.

## 4. Results
### 4.1 Top Association Rules
| Rank | Antecedents | Consequents | Support | Confidence | Lift | Conviction | Leverage |
|------|-------------|-------------|---------|------------|------|------------|----------|
| 1 | - | - | - | - | - | - | - |
| 2 | - | - | - | - | - | - | - |
| 3 | - | - | - | - | - | - | - |

### 4.2 Key Visualizations


### 4.3 Performance Metrics
**Runtime:** [ - ] seconds  
**Scalability:** Processed 4,900+ records efficiently using sparse matrix handling.

## 5. Discussion


### 5.1 Clinical Insights
1.  **Insight 1:** [Example: High lift between specific symptoms suggests a distinct syndrome]
2.  **Insight 2:** [Example: Common flu symptoms have high support but low lift due to ubiquity]

### 5.2 Actionable Recommendations
1.  **Diagnostic Checklist:** Prioritize checking for [Symptom B] if [Symptom A] is observed.
2.  **System Design:** Use identified rules to weight probability scores in a diagnostic app.

### 5.3 Limitations
- Analysis is limited to the specific symptoms present in the training set.
- Does not account for symptom severity or duration.

## 6. Conclusion
The Apriori algorithm is expected to identify key diagnostic rules from the medical dataset. By filtering for high **Lift** and **Conviction**, I aim to distinguish between general symptoms (like fatigue) and specific disease indicators.

## 7. Video Presentation


## References
1. mlxtend Documentation: https://rasbt.github.io/mlxtend/
2. Disease Symptom Prediction Dataset: https://www.kaggle.com/datasets/itachi9604/disease-symptom-description-dataset
3. 

## Appendix: Full Results
