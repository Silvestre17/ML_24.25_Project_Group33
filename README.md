# ML Project 24.25 - [WCB | Notebooks]

Work developed in the **Machine Learning** project of the **Master's in Data Science and Advanced Analytics** at **NOVA IMS**.

> The main goal of this project is develop a multiclass classification model to predict the New York Workers' Compensation Board's decision on injury claims, optimize its performance, and provide additional insights through feature analysis and model improvements. 

<br>

### **TP2 | TBL Group 33**

- André Silvestre, 20240502
- João Henriques, 20240499
- Simone Genovese, 20241459
- Steven Carlson, 20240554
- Vinícius Pinto, 20211682
- Zofia Wojcik, 20240654
  
<br>

---

## **Table of Contents**

- [1. Data Understanding & EDA]('./1_BU&EDA_MLProject_Group33.ipynb')
  - **Missing Values**
  - **Data Types**
  - **Descriptive Statistics**
  - **Exploratory Data Analysis**
    - Univariate Analysis
    - Bivariate Analysis
    - Multivariate Analysis
  - **New Features Creation**
- [2. Data Preparation & Feature Engineering]('./2_FeatureEngineering_MLProject_Group33.ipynb')
  - **Data Cleaning**
  - **Feature Selection**
    - Filter Methods (`Spearmans'` Correlation, `Cramér's V` Correlation & `Chi-Squared` Test)
    - Wrapper Methods (Recursive Feature Elimination (`RFE`))
    - Embedded Methods (`LASSO` & `RIDGE` Regularization)
    - Final Decision
- [3. Modeling & Evaluation]('./3_Modeling&Evaluation_MLProject_Group33.ipynb')
  - Imbalanced Treatment (`KMeansSMOTE`)
  - **Classification Models**
    - Logistic Regression
    - Naive Bayes (Gaussian & Categorical)
    - Neural Network (MLP)
    - Decision Tree
    - Random Forest
    - Bagging Classifier (Logistic Regression)
    - CatBoost
    - ExtraTrees
    - Stacking Classifier (...)

**Note 1 |** All the notebooks need to be run in order to ensure the correct execution of the code.

**Note 2 |** Some code cells are commented out to avoid running them all at once. Please uncomment them if you want to run them. Otherwise, the results can be found in the **[Excel Results](./ML_Excel_ReportResults_Group33.xlsx)** file.

<br>

### Open-Ended Section

- **[Feature Importance](./3_Modeling&Evaluation_MLProject_Group33.ipynb)**
- **[Web Application](https://github.com/Silvestre17/ML_WebApp_Group33)**