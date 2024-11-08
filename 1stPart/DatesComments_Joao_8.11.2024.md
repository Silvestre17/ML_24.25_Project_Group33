### **Feature Selection | Key Notes**

#### **Numerical Data Summary**

<center><b>Table 1 | </b> Summary of Feature Selection for Numerical Variables <br><br>


> Consider the table of feature selection results for numerical variables.


| **Predictor**                  | **Correlation** | **Ridge**     | **Lasso**     | **RFE**       | **Multicollinearity?** | **What to do?**              |
|--------------------------------|-----------------|---------------|---------------|---------------|-------------------------|------------------------------|
| Accident Date Day              | Negligible            | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| Accident Date Month            | Negligible             | Not Selected  | Not Selected  | Selected      | Yes                     | Consider for exclusion       |
| Accident Date Weekday          | Negligible             | Not Selected  | Not Selected  | Selected      | Yes                     | Consider for exclusion       |
| Accident Date Year             | Negligible             | Not Selected  | Not Selected  | Not Selected  | Yes                     | Discard                      |
| Age at Injury Clean            | Weak        | Not Selected  | Selected      | Not Selected  | Yes                     | **Try with and without**     |
| Alternative Dispute Resolution | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | **Consider including**       |
| Assembly Date Day              | Negligible             | Not Selected  | Not Selected  | Not Selected  | Yes                     | Discard                      |
| Assembly Date Weekday          | Negligible             | Not Selected  | Not Selected  | Not Selected  | Yes                     | Discard                      |
| Assembly Date Month            | Negligible             | Not Selected  | Not Selected  | Selected      | Yes                     | Consider for exclusion       |
| Assembly Date Year             | Negligible             | Not Selected  | Not Selected  | Not Selected  | Yes                     | Discard                      |
| Attorney/Representative        | Relatively Strong             | Selected      | Selected      | Selected      | No                      | **Consider including**       |
| C-2 Date Day                   | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| C-2 Date Month                 | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| C-2 Date Weekday               | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| C-2 Date Year                  | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| C-3 Date Binary                | Relatively Strong             | Selected      | Selected      | Selected      | No                      | **Consider including**       |
| Carrier Type Bucket            | Negligible             | Selected      | Not Selected  | Selected      | No                      | **Consider including**       |
| County of Injury               | Negligible             | Not Selected  | Not Selected  | Selected      | Yes                     | Consider for exclusion       |
| COVID-19 Indicator             | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| District Name                  | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| First Hearing Date Binary      | Relatively Strong         | Selected      | Selected      | Selected      | Yes                     | **Try with and without**     |
| Gender                         | Negligible             | Not Selected  | Not Selected  | Selected      | No                      | **Consider including**       |
| IME-4 Reported                 | Relatively Strong         | Selected      | Selected      | Selected      | Yes                     | **Try with and without**     |
| Industry Code                  | Negligible             | Not Selected  | Not Selected  | Selected      | Yes                     | Include with caution         |
| Medical Fee Region             | Negligible            | Not Selected  | Not Selected  | Selected      | Yes                     | Consider for exclusion       |
| Number of Dependents           | Negligible             | Not Selected  | Not Selected  | Not Selected  | No                      | Discard                      |
| WCIO Cause of Injury Bucket    | Weak        | Selected      | Not Selected  | Selected      | Yes                     | **Include in model**         |
| WCIO Nature of Injury Bucket   | Negligible             | Not Selected  | Not Selected  | Selected      | Yes                     | Consider for exclusion       |
| WCIO Part of Body Bucket       | Weak             | Not Selected  | Not Selected  | Selected      | Yes                     | Consider for exclusion       |
| Weekly Wage Reported           | Very Strong            | Selected      | Selected      | Selected      | No                      | **Include in model**         |


</center> 

---


> **`?`** - Indicates variables with potential multicollinearity. Further analysis may be required for confirmation. <br>
> **Note:** Features with low or no selection across methods can likely be discarded to improve model efficiency.

---

#### **Categorical Data Summary**

<center><b>Table 2 | </b> Summary of Feature Selection for Categorical Variables <br><br>

| **Predictor**                      | **Chi-Square** | **Ridge**     | **Lasso**     | **RFE**       | **Multicollinearity?** | **What to do?**              |
|------------------------------------|----------------|---------------|---------------|---------------|-------------------------|------------------------------|
| Alternative Dispute Resolution     | High           | Selected      | Not Selected  | Selected      | No                      | **Consider including**       |
| Carrier Type Bucket                | Low            | Selected      | Not Selected  | Selected      | No                      | Discard                      |
| COVID-19 Indicator                 | Low            | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| District Name                      | Low            | Not Selected  | Not Selected  | Selected      | No                      | Consider for exclusion       |
| Gender                             | High           | Not Selected  | Not Selected  | Selected      | No                      | **Consider including**       |
| Industry Code                      | Moderate       | Not Selected  | Not Selected  | Selected      | Yes                     | **Try with and without**     |
| WCIO Cause of Injury Bucket        | Moderate       | Selected      | Selected      | Selected      | Yes                     | **Include in model**         |
| WCIO Nature of Injury Bucket       | Moderate       | Selected      | Not Selected  | Selected      | Yes                     | **Try with and without**     |

</center>

---

> **Interpretation:** Categorical features with significant Chi-Square values are likely important for model predictions, but those not selected by Ridge, Lasso, or RFE can be discarded.

---

#### **Feature Selection Summary for Both Numerical and Categorical Variables**

- **Features Consistently Selected Across All Methods**: 
  - **Weekly Wage Reported**
  - **Attorney/Representative**
  - **IME-4 Reported**
  - **First Hearing Date Binary**

- **Multicollinearity Concerns**: 
  - Variables such as **IME-4 Reported**, **WCIO Cause of Injury Bucket**, and **Industry Code** may have multicollinearity issues that need further assessment, such as testing different model configurations or applying regularization techniques.

- **Consider for Exclusion**: 
  - Variables with low correlation with the target and that were not selected across multiple methods, such as **Assembly Date Day**, **County of Injury**, and **Number of Dependents**.

<div class="alert alert-block alert-danger" style="font-weight: bold; font-size: 45px;">

FINISH AND CONFIRM THIS SECTION (Just a ChatGPT output)

</div>