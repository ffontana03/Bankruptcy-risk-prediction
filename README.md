# Bankruptcy Prediction: Robust Multivariate Analysis and Clustering/Prediction

**Authors:** Francesco Lops, Federico Fontana  
**Course:** Advanced Multivariate Statistics  

## Overview
This repository contains the code for the project of Advanced Multivariate Statistics. The project addresses corporate bankruptcy prediction by investigating the underlying structure and robustness of financial data. Rather than treating bankruptcy prediction exclusively as a standard classification exercise, this analysis combines predictive accuracy with a deep exploration of the multivariate structure of corporate financial indicators.

## Dataset
The empirical analysis is based on the **Taiwanese Bankruptcy Prediction dataset** obtained from the UCI Machine Learning Repository. It contains 6,819 firms and 95 financial predictors, along with a binary target variable indicating bankruptcy status. The dataset exhibits a severe class imbalance, with only about 3.23% of cases representing bankrupt firms.

## Research Questions
1. **RQ1:** Which financial ratios provide the strongest discrimination between bankrupt and non-bankrupt firms under severe class imbalance?
2. **RQ2:** What underlying financial profiles can be identified among firms, and how does robust clustering through TCLUST compare with probabilistic clustering through Gaussian Mixture Models?
3. **RQ3:** To what extent can the identified financial ratios and latent firm profiles be used to predict bankruptcy reliably on out-of-sample observations?

## Methodology
The analysis is structured around several key multivariate and predictive techniques:
- **Data Exploration & Univariate Analysis:** Assessment of skewness, kurtosis, and tail behaviors among financial predictors, providing justification for the use of robust statistical methods.
- **Redundancy Analysis & Hierarchical Clustering:** Reducing the feature space from 95 to 41 predictors using absolute Spearman rank correlation and average linkage hierarchical clustering to eliminate multicollinearity.
- **Multivariate Outlier Detection:** Comparing classical Mahalanobis distances with robust distances computed via the Minimum Covariance Determinant (MCD) estimator to identify masked multivariate outliers.
- **Clustering & Financial Profiling:** Identifying underlying firm profiles using:
  - *Gaussian Mixture Models (GMM)* for a probabilistic representation of latent profiles.
  - *Robust Clustering (TCLUST)* incorporating trimming and eigenvalue restrictions to limit the influence of atypical observations.
- **Predictive Modeling:** Estimating a Logistic Mixed-Effects Model (GLMM). The top discriminatory financial indicators (selected via ROC-AUC and PR-AUC screening) serve as fixed effects, while the TCLUST financial profiles are used to account for unobserved heterogeneity across groups of firms.

## Repository Structure
- `Advanced_multivariate_statistics.ipynb`: The Jupyter Notebook containing the complete analytical pipeline, including EDA, redundancy analysis, robust outlier detection, clustering, and predictive modeling.
- `README.md`: This project overview.

## Requirements and Installation
The code is written in Python and uses R (via the `rpy2` library) for specialized robust clustering and mixed-effects modeling (`tclust` and `lme4`). 

To run the analysis, ensure you have the following installed:
- **Python 3.x**
- **R** with `tclust` and `lme4` packages
- **Python libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `scipy`, `statsmodels`, `ucimlrepo`, `rpy2`.

You can install the Python dependencies using `pip` and the R dependencies directly from the notebook/script via:
```python
!R -e 'install.packages(c("tclust", "lme4"), repos="https://cloud.r-project.org")'
```
