# Train–Validate Customer Segmentation (Temporal Validation)

## Overview

This project builds a customer segmentation model using historical transactional data and validates the segmentation logic on a future time window.

Unlike traditional clustering projects, this implementation follows a strict temporal validation framework to evaluate cluster stability and behavioral drift over time.

---

## Key Features

- RFM + behavioral + temporal feature engineering
- Strict train–validation time split (no data leakage)
- Log transformation for heavy skew reduction
- Correlation-based feature selection
- Standardization using training-set parameters only
- PCA comparison (selected non-PCA for interpretability)
- Algorithm comparison:
  - KMeans
  - Hierarchical (Ward linkage)
- Final model: KMeans (k = 5)
- Cluster assignment applied to validation dataset

---

## Project Structure

```
customer-segmentation-temporal-validation/
│
├── notebooks/
│   ├── 01_data_understanding_time_audit.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_clustering_model_selection.ipynb
│
├── data/                # Not included in repository
│   ├── raw/
│   ├── interim/
│   └── processed/
│
├── reports/
│   └── figures/
│
├── requirements.txt
└── README.md
```

---

## Dataset

Dataset used: Online Retail II dataset (UCI / Kaggle)

Note: Dataset files are not included in this repository.

---

## Methodology Summary

1. Data Understanding and Time Audit  
2. Data Cleaning and Transaction Validation  
3. Advanced Feature Engineering (RFM + Behavioral + Temporal Metrics)  
4. Log Transformation for skew reduction  
5. Correlation-based feature reduction  
6. StandardScaler fit on training data only  
7. Model selection using Elbow and Silhouette  
8. Algorithm comparison (KMeans vs Hierarchical)  
9. Final selection: KMeans (k = 5)  

---

## Final Model Selection

KMeans (k = 5) was selected based on:

- Clear elbow bend at k = 5  
- Acceptable silhouette score  
- Better separation compared to hierarchical clustering  
- Preserved business interpretability without PCA  
- Ability to consistently assign validation customers to clusters  

---

## How To Run

1. Clone the repository:

```
git clone <your_repository_link>
```

2. Navigate into project folder:

```
cd customer-segmentation-temporal-validation
```

3. Install dependencies:

```
pip install -r requirements.txt
```

4. Run notebooks in order from `01_` to `04_`.

---

## Author

**Yasas Rangana**  
Business Analyst | Aspiring Data Scientist