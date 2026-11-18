# Machine Learning & Data Mining 2 — Labworks

This repository contains my practical work for the Machine Learning & Data Mining 2 course, including notebooks, analysis results, visualizations, and reports.

It will be updated throughout the course to include four labworks.

## Labwork Overview

| Labwork | Topic | Status | Report Link |
|---------|-------|--------|--------|
| Lab 1 | Data Exploration, Preprocessing, and PCA | In progress | [Report](https://www.overleaf.com/project/6afdf0b41440e618e3d70f10/share#d7022eb372149f63419e8da1042b0802fd225b8afdfc1eb7)
| Lab 2 | To be announced | Not started |
| Lab 3 | To be announced | Not started |
| Lab 4 | To be announced | Not started |

## Lab 1 — Data Exploration, Preprocessing, and PCA

### Objectives

- Explore the structure and characteristics of two selected datasets.
- Identify missing values, duplicates, and potential outliers.
- Apply data cleaning, integration, and transformation.
- Analyze numerical and categorical features using appropriate statistics.
- Examine correlations between numerical features.
- Apply Principal Component Analysis (PCA) and evaluate dimensionality reduction.

### Current Dataset: Olist Products

The current analysis uses the products table from the Brazilian E-Commerce Public Dataset by Olist.

### Completed Work

- Inspected the dataset structure, feature types, and descriptive statistics.
- Checked missing values, duplicate rows, and potential outliers using IQR.
- Treated four zero-weight measurements as missing.
- Removed rows with missing values in the selected numerical features.
- Integrated English category names using a validated many-to-one merge.
- Standardized the numerical features using Z-score normalization.
- Calculated means, variances, covariance, and Pearson correlation.
- Summarized category frequencies and percentages.
- Visualized the correlation matrix and identified the strongest feature relationships.

### Preliminary Findings

- Cleaning removed 615 rows (1.87%), leaving 32,336 products.
- Category translation preserved the number of products.
- Thirteen products had no English category translation; their original category names were retained as display labels.
- Weight and height showed the highest absolute correlation (r = 0.5626), indicating a moderate positive linear relationship.
- Physical measurements showed positive correlations of varying strengths.
- Text-length features and photo count showed weak linear relationships with physical measurements.

Potential outliers were retained because there was insufficient evidence that they were invalid. Their possible influence remains a limitation of the analysis.

### Next Steps

- Apply PCA to the standardized numerical features.
- Analyze individual and cumulative explained variance.
- Compare different numbers of retained components.
- Visualize products using the first two principal components.
- Discuss information preservation, interpretability, and limitations.
- Complete the corresponding analysis for the second selected dataset.

## Tools

- Python
- Jupyter Notebook
- pandas
- Matplotlib
- seaborn

Additional dependencies will be documented as the labworks progress.

## Data Source

Lab 1 currently uses the
[Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

## Academic Context

These labworks are completed as part of the Machine Learning & Data Mining 2 course. The repository documents my implementation, observations, and interpretation of the results.
