# CSC172 Association Rule Mining Project Proposal  
**Student:** Angelyn Jimeno, 2022-4037  
**Date:** 12/12/2025

## 1. Project Title
Symptom Association Analysis using Apriori Algorithm

## 2. Problem Statement
In healthcare, accurate differential diagnosis relies on recognizing patterns of co-occurring symptoms. This project analyzes patient symptom data to discover "symptom clusters" and strong association rules. This is relevant for building Clinical Decision Support Systems (CDSS) that help medical professionals predict potential conditions based on initial presenting symptoms, rather than relying on intuition alone.

## 3. Objectives
- Preprocess medical dataset to standardize symptom labels and handle missing values
- Perform EDA with visualizations including symptom frequency distributions and co-occurrence heatmaps
- Implement the Apriori algorithm to generate diagnostic association rules
- Evaluate rules using **Support, Confidence, Lift, Conviction, and Leverage** metrics to identify non-trivial clinical insights

## 4. Dataset Plan
- **Source:** [Disease Symptom Prediction - Kaggle](https://www.kaggle.com/datasets/itachi9604/disease-symptom-description-dataset)
- **Size:** ~4,920 records (Exceeds the 500 minimum requirement)
- **Domain:** Medical / Healthcare Diagnosis
- **Structure:** The dataset is in a "wide" format where each row represents a patient diagnosis and columns represent potential symptoms.
- **Sample Transactions:**

| Disease | Symptom_1 | Symptom_2 | Symptom_3 | Symptom_4 |
| :--- | :--- | :--- | :--- | :--- |
| Fungal infection | itching | skin_rash | nodal_skin_eruptions | dischromic _patches |
| Fungal infection | skin_rash | nodal_skin_eruptions | dischromic _patches | NaN |
| GERD | stomach_pain | acidity | ulcers | vomiting |
| Chronic cholestasis | itching | vomiting | yellowish_skin | nausea |

## 5. Technical Approach
- **Preprocessing:**
  - Cleaning: String formatting (remove underscores/whitespace)
  - Transformation: Convert list-based data to One-Hot Encoded format using `mlxtend.preprocessing.TransactionEncoder`
- **Algorithm:** Apriori (Initial tuning: min_support=0.01, min_confidence=0.5, min_lift=1.2)
- **Framework:** Python + pandas + mlxtend + matplotlib/seaborn
- **Environment:** Jupyter Notebook / Google Colab

## 6. Expected Challenges & Mitigations
- **Challenge:** High Sparsity (Patients have very few symptoms out of 132 possibilities)
  - **Solution:** Use `TransactionEncoder` specifically designed for sparse matrices to optimize memory usage

- **Challenge:** Trivial Rules (e.g., obvious associations like `{Sneezing} -> {Runny Nose}`)
  - **Solution:** Filter results by **Lift > 1.5** and **Conviction** to prioritize complex, clinically significant associations

- **Challenge:** Inconsistent Data Formatting (strings like "skin_rash" vs " skin rash")
  - **Solution:** Implement a strict string cleaning function during the preprocessing stage to standardize all item labels