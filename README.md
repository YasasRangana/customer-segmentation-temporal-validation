# Train–Validate Customer Segmentation with Temporal Validation

## Overview

This project develops a customer segmentation framework using transactional retail data and evaluates the segmentation stability across time.

Unlike typical clustering projects that analyze a single dataset, this implementation follows a **temporal validation approach**, where segmentation logic is learned from historical data and then applied to a future time period. This allows evaluation of cluster stability, behavioral drift, and customer segment migration over time.

The goal is to identify meaningful customer segments that can support **data-driven marketing, retention strategies, and customer value management**.

---

## Key Objectives

• Build meaningful customer segments using transactional purchase behavior  
• Engineer advanced behavioral features (RFM + temporal metrics)  
• Select optimal clustering strategy through model comparison  
• Validate segmentation stability across time periods  
• Analyze how customers move between segments over time

---

## Dataset

This project uses the **Online Retail II dataset**, which contains transactional records from a UK-based online retailer.

Dataset link:

https://archive.ics.uci.edu/ml/datasets/Online+Retail+II

Because of dataset size and licensing restrictions, the dataset is **not included in this repository**.

After downloading the dataset, place the files inside:

```
data/raw/
```

---

## Project Structure

```
customer-segmentation-temporal-validation
│
├── notebooks
│   ├── 01_Data_Understanding.ipynb
│   ├── 02_Data_Cleaning.ipynb
│   ├── 03_Feature_Engineering.ipynb
│   ├── 04_preprocessing_and_temporal_clustering.ipynb
│   └── 05_Cluster_Profiling_and_Temporal_Stability.ipynb
│
├── data
│   ├── raw
│   ├── interim
│   └── processed
│
├── requirements.txt
└── README.md
```

---

## Methodology

The project follows a structured analytics pipeline.

### 1. Data Understanding

• Loaded the transactional dataset  
• Analyzed schema, time ranges, and column consistency  
• Defined temporal windows for training and validation datasets

Training Period:
```
2009–2010
```

Validation Period:
```
2010–2011
```

---

### 2. Data Cleaning

• Removed cancelled invoices  
• Filtered invalid quantities and prices  
• Removed duplicate records  
• Handled missing customer IDs  
• Generated transaction-level revenue feature

---

### 3. Feature Engineering

Customer-level behavioral features were engineered including:

• Recency  
• Frequency  
• Monetary value  
• Customer lifespan  
• Average order value  
• Average purchase gap  
• Spending volatility  
• Average basket size  
• Active months  
• Revenue contribution

These features capture both **purchasing intensity and temporal engagement patterns**.

---

### 4. Feature Preparation

• Log transformation applied to reduce skewness  
• Highly correlated features removed  
• Features standardized using **training-set statistics only** to prevent data leakage

---

### 5. Model Selection

Clustering strategies were evaluated using:

• Elbow method  
• Silhouette score  

Two clustering algorithms were compared:

• **KMeans clustering**  
• **Hierarchical clustering (Ward linkage)**

PCA was also evaluated but excluded from the final model to preserve business interpretability.

Final selection:

```
KMeans (k = 5)
```

---

### 6. Cluster Profiling

Clusters were analyzed using behavioral feature averages to identify meaningful customer segments.

The following segments were identified:

| Cluster | Segment |
|------|------|
| 0 | Recent One-Time Buyers |
| 1 | VIP / Loyal Customers |
| 2 | Regular Mid-Value Customers |
| 3 | Dormant Customers |
| 4 | High-Value Occasional Buyers |

---

### 7. Temporal Stability Analysis

Cluster characteristics were compared between training and validation datasets.

Results show that the **relative behavioral structure of segments remains stable across time**, indicating that the segmentation framework captures meaningful customer patterns rather than dataset-specific noise.

---

### 8. Customer Migration Analysis

A migration matrix was constructed to analyze how customers moved between segments across time periods.

Key insights:

• Loyal customers show the highest stability across periods  
• Regular customers transition between segments depending on engagement changes  
• Recent buyers often evolve into regular customers or become inactive  
• Dormant customers occasionally re-engage with the business

Migration analysis provides valuable insights into **customer lifecycle dynamics**.

---

### 9. Revenue Contribution Analysis

Revenue distribution across clusters reveals a strong concentration of value among a small subset of customers.

The **VIP / Loyal Customers segment contributes the majority of total revenue**, highlighting the importance of retention strategies for this group.

---

## Business Recommendations

Based on the segmentation results:

**VIP / Loyal Customers**
- Maintain engagement through loyalty programs and personalized offers.

**High-Value Occasional Buyers**
- Encourage increased purchase frequency through targeted promotions.

**Regular Mid-Value Customers**
- Use cross-selling and upselling campaigns to increase customer value.

**Recent One-Time Buyers**
- Implement onboarding campaigns to convert them into repeat buyers.

**Dormant Customers**
- Launch reactivation campaigns to regain engagement.

---

## Technologies Used

Python  
Pandas  
NumPy  
Scikit-learn  
Matplotlib  
Seaborn  
Jupyter Notebook

---

