<p align="center">
   <a href="https://mlproject-wcb-group33.streamlit.app/">
        <img src="https://github.com/Silvestre17/ML_WebApp_Group33/blob/main/static/WCB_Group33_Banner.png" alt="WCB Group33 Banner" width="800">
    </a>
</p>

# 🤖 ML Project: Predicting Workers' Compensation Claim Severity 🗽

## ✨ Project Overview

This project, completed for the **Machine Learning** course within the **[Master's in Data Science and Advanced Analytics](https://www.novaims.unl.pt/en/education/programs/postgraduate-programs-and-master-degree-programs/master-degree-program-in-data-science-and-advanced-analytics-with-a-specialization-in-data-science/)** program at **NOVA IMS**, focuses on applying supervised learning techniques to predict the severity of workers' compensation claims handled by the New York Work Compensation Board (NWCB). The primary objective is to develop a **robust multiclass classification model** to predict one of eight possible `Claim Injury Type` categories, aiming to automate and streamline the claim adjudication process, addressing the increasing volume and manual review time.

<p align="center">
    <!-- Project Links -->
    <a href="https://github.com/Silvestre17/ML_24.25_Project_Group33"><img src="https://img.shields.io/badge/Project_Repo-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Repo"></a>
    <a href="https://mlproject-wcb-group33.streamlit.app/"><img src="https://img.shields.io/badge/Live_App-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Live Streamlit App"></a>
    <a href="https://github.com/Silvestre17/ML_WebApp_Group33"><img src="https://img.shields.io/badge/WebApp_Repo-100000?style=for-the-badge&logo=github&logoColor=white" alt="WebApp Repo"></a>
</p>

## 📚 Context

Analyzing and adjudicating workers' compensation claims is a critical but resource-intensive task for the NWCB. Facing an upward trend in claim submissions (as noted in the NWCB 2023 Annual Report), this project leverages machine learning to predict claim severity, potentially freeing up resources and improving processing efficiency.

## 👥 Team

**TP2 | TBL Group 33**

*   André Silvestre, 20240502
*   João Henriques, 20240499
*   Simone Genovese, 20241459
*   Steven Carlson, 20240554
*   Vinícius Pinto, 20211682
*   Zofia Wojcik, 20240654

## 🏗️ Project Methodology (CRISP-DM)

The project meticulously followed the **CRISP-DM (Cross Industry Standard Process for Data Mining)** framework, ensuring a structured approach from problem definition to solution deployment.

<p align="center">
    <img src="./img/ProjectFlowchart.png" alt="Project Flowchart" width="400" style="background-color: white;">
</p>
<p align="center"><i>Figure 1: Overall Project Flow (CRISP-DM Cycle)</i></p>

Here's a breakdown of the activities undertaken in each phase:

1.  **Business Understanding:** 💡
    *   **Problem:** High volume and manual processing time for NWCB workers' compensation claims.
    *   **Goal:** Develop an ML model to automatically predict claim severity (Claim Injury Type) based on initial claim data.
    *   **Objective:** Build a multiclass classification model distinguishing between 8 injury types, aiming for high F1-Macro performance.
    <p align="center">
        <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" /></a>
    </p>

2.  **Data Understanding:** 🔍
    *   **Data Collection:** Utilized NWCB public data (Train: ~593K rows, 33 cols; Test: ~388K rows, 30 cols).
    *   **Initial Exploration:** Analyzed feature types, distributions (Appendix C), identified the target (`Claim Injury Type`) and unique ID (`Claim Identifier`). Key challenge identified: **significant class imbalance** (Figure C1).
    *   **Quality Assessment:** Detected missing values, potential outliers (Age, Dates), and inconsistencies (non-numeric Zips, date ranges).
    *   *Link to Notebook:* [`1_BU&EDA_MLProject_Group33.ipynb`](./1_BU&EDA_MLProject_Group33.ipynb)
    <p align="center">
        <a href="https://pandas.pydata.org/"><img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas" /></a>
        <a href="https://numpy.org/"><img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy" /></a>
        <a href="https://matplotlib.org/"><img src="https://img.shields.io/badge/Matplotlib-FFFFFF?style=for-the-badge&logo=matplotlib&logoColor=black" alt="Matplotlib" /></a>
        <a href="https://seaborn.pydata.org/"><img src="https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge&logo=seaborn&logoColor=white" alt="Seaborn" /></a>
        <a href="https://docs.scipy.org/doc/scipy/reference/stats.html"><img src="https://img.shields.io/badge/SciPy.Stats-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white" alt="SciPy Stats" /></a>
    </p>

3.  **Data Preparation:** 🛠️
    *   **Initial Cleaning:** Dropped irrelevant/non-test columns, handled rows with many missing values, addressed specific anomalies (Table 2.2 / C1).
    *   **Missing Values:** Imputed numerical features using **KNN Imputer**; created 'Unknown' category for `Industry Code Description`.
    *   **Outlier Handling:** Analyzed using IQR, retained most outliers to preserve data variability, but created binary features (e.g., `IME-4 Reported`, `Average Weekly Wage Reported`) to mitigate the impact of extreme values/missingness patterns.
    *   **Feature Engineering:** Extracted temporal components (Year, Month, Day, Weekday) from dates; cleaned `Age at Injury`/`Birth Year` and created `Age at Injury Group`; bucketed high-cardinality categoricals (`WCIO` codes, `Carrier Type`); created binary flags for missing dates/specific reports.
    *   **Encoding:** Applied `OrdinalEncoder` (`Age at Injury Group`) and `OneHotEncoder` (other nominal/binary categoricals).
    *   **Data Splitting:** Used a 75% Training / 25% Validation Hold-Out split.
    *   **Feature Selection:** Implemented a multi-faceted strategy (visualized below) combining Filter (`Spearman`, `Cramér's V`, `Chi-Squared`, `VIF`), Wrapper (`RFE`), and Embedded (`Lasso`, `Ridge`) methods. A **2/3 majority vote** selected the final **27 features** (Appendix D).
    *   **Scaling:** Tested `MinMaxScaler`, `StandardScaler`, `RobustScaler` to prepare data for scale-sensitive algorithms and feature selection steps (Annex D).
    *   *Link to Notebook:* [`2_FeatureEngineering_MLProject_Group33.ipynb`](./2_FeatureEngineering_MLProject_Group33.ipynb)
    <p align="center">
      <img src="./img/FeatureSelectionFlowchart.png" alt="Feature Selection Flowchart" width="600" style="background-color: white;">
    </p>
    <p align="center"><i>Figure 2: Feature Selection Process Flowchart</i></p>
    <p align="center">
        <a href="https://scikit-learn.org/stable/"><img src="https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn" /></a>
        <a href="https://imbalanced-learn.org/stable/"><img src="https://img.shields.io/badge/imbalanced_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Imbalanced-Learn" /></a>
        <a href="https://www.statsmodels.org/stable/index.html"><img src="https://img.shields.io/badge/Statsmodels-150458?style=for-the-badge&logo=python&logoColor=white" alt="Statsmodels" /></a>
        <a href="https://docs.scipy.org/doc/scipy/reference/stats.html"><img src="https://img.shields.io/badge/SciPy.Stats-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white" alt="SciPy Stats" /></a>
    </p>

4.  **Modeling:** 🤖
    *   **Algorithms:** Trained and evaluated **Logistic Regression**, **Naive Bayes** (Gaussian/Categorical), **KNN**, **MLP Neural Network**, **Decision Tree**, **Random Forest**, **CatBoost**, **ExtraTrees**, **Bagging** (LR base), and **Stacking** (RF + LR).
    *   **Strategy:** Models were tested on original and scaled (MinMax, Standard, Robust) data. **K-Means SMOTE** resampling was tested (Annex F) but ultimately discarded as it increased overfitting without improving validation performance compared to models trained on original imbalanced data (Table G1). The Hold-Out strategy was maintained (Figure 3).
    *   **Hyperparameter Tuning:** Optimized **Random Forest** using `GridSearchCV` (Table H1), improving validation F1-Macro from 0.40 to 0.42. Base parameters were used for **CatBoost** due to computational cost.
    *   *Link to Notebook:* [`3_Modeling&Evaluation_MLProject_Group33.ipynb`](./3_Modeling&Evaluation_MLProject_Group33.ipynb)
    <p align="center">
        <img src="./img/ModelingFlowchart.png" alt="Modeling Flowchart" width="600" style="background-color: white;">
    </p>
    <p align="center"><i>Figure 3: Model Training and Evaluation Strategy Flowchart</i></p>
    <p align="center">
        <a href="https://scikit-learn.org/stable/"><img src="https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn" /></a>
        <a href="https://catboost.ai/"><img src="https://img.shields.io/badge/CatBoost-00AEEF?style=for-the-badge&logo=yandex&logoColor=white" alt="CatBoost" /></a>
        <a href="https://imbalanced-learn.org/stable/"><img src="https://img.shields.io/badge/imbalanced_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Imbalanced-Learn" /></a>
    </p>

5.  **Evaluation:** ✅
    *   **Metrics:** Performance assessed using Accuracy, Precision, Recall, **F1-Score (Macro)** (primary due to imbalance), and AUROC.
    *   **Selection Criteria:** Focused on high validation F1-Macro (>0.4), low overfitting (Train-Validation F1 difference < 0.1), and strong secondary metrics (Accuracy, AUROC), detailed in Table F1.
    *   **Results:** **CatBoost** (on original data) and **Random Forest** were the top models. CatBoost achieved the best performance on the final Kaggle test set evaluation (Appendix G).
    <!-- Scikit-learn used extensively for metrics -->

6.  **Deployment:** 🚀
    *   **Web Application:** Developed an interactive **Streamlit** dashboard ([Live App](https://mlproject-wcb-group33.streamlit.app/)) featuring:
        *   A prediction interface using the final CatBoost model.
        *   A data exploration section for interactive analysis (Figure I1).
    *   **Interpretability:** Integrated **LIME** to explain individual predictions, showing feature contributions for transparency and actionable insights (Figure J1).
    <p align="center">
        <a href="https://streamlit.io/"><img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit App"/></a>
        <a href="https://github.com/marcotcr/lime"><img src="https://img.shields.io/badge/LIME-4CAF50?style=for-the-badge&logo=python&logoColor=white" alt="LIME" /></a>
        <a href="https://plotly.com/python/"><img src="https://img.shields.io/badge/Plotly-3F4F75?style=for-the-badge&logo=plotly&logoColor=white" alt="Plotly" /></a>
    </p>

## 📈 Deliverables & Outputs

*   **Jupyter Notebooks:** Organized by CRISP-DM phase within the [main project repository](https://github.com/Silvestre17/ML_24.25_Project_Group33).
    *   [`1_BU&EDA_MLProject_Group33.ipynb`](./1_BU&EDA_MLProject_Group33.ipynb)
    *   [`2_FeatureEngineering_MLProject_Group33.ipynb`](./2_FeatureEngineering_MLProject_Group33.ipynb)
    *   [`3_Modeling&Evaluation_MLProject_Group33.ipynb`](./3_Modeling&Evaluation_MLProject_Group33.ipynb)
*   **Excel Report:** Comprehensive results, analysis, and model comparisons in [`ML_Excel_ReportResults_Group33.xlsx`](./ML_Excel_ReportResults_Group33.xlsx).
*   **Streamlit Web App:**
    *   Deployed Application: [https://mlproject-wcb-group33.streamlit.app/](https://mlproject-wcb-group33.streamlit.app/)
    *   Source Code Repository: [https://github.com/Silvestre17/ML_WebApp_Group33](https://github.com/Silvestre17/ML_WebApp_Group33)

## 🔑 Keywords

Workers' Compensation Claims; Machine Learning; Multiclass Classification; Classification Models; Ensemble Learning; Random Forest; CatBoost; Feature Engineering; Feature Selection; Data Exploration; Imbalanced Data; KMeansSMOTE; CRISP-DM; Streamlit; LIME; Predictive Modeling; Data Science.

## 📔 Conclusion

This project successfully navigated the CRISP-DM process to develop and evaluate machine learning models for predicting workers' compensation claim severity. Ensemble methods, particularly **CatBoost** and **Random Forest**, demonstrated the strongest performance despite the challenge of significant class imbalance. The implemented **Streamlit application** provides a practical interface for prediction, while **LIME** enhances model transparency. While resampling techniques like K-Means SMOTE did not improve final results in this case, the thorough feature engineering and selection process proved crucial. This work establishes a strong foundation for data-driven decision support within the NWCB, with potential for further refinement through techniques like textual analysis or more advanced resampling/validation strategies.

---

Explore the notebooks and the live application for a deeper dive into the methodology and results!
