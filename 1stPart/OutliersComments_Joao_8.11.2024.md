#### **1. | Handling outlier values** <a class='anchor' id='1-outliers'></a>

To address outlier values, we considered three primary strategies:

- **Total or partial removal**: This involves removing all outliers or a subset based on a predefined threshold.
- **Adjust values to reduce extremity**: Known as "winsorizing," this approach modifies extreme values to bring them closer to the general range, based on a threshold established a priori.
- **Retain all values**: This approach keeps all data points, preserving the full range of variability.

We chose to retain all outlier values to maintain data integrity and avoid introducing potential biases. Removing outliers risks eliminating natural variability, potentially distorting the data's inherent distribution. Additionally, the process of outlier removal can be subjective, introducing bias by making arbitrary decisions on which data points to exclude. Keeping all data points avoids arbitrary decisions that could affect the analysis.


Although we did not remove outliers directly, two preprocessing steps implemented throughout the project helped mitigate their impact:

- **Feature standardization**: By scaling all features to a comparable range, standardization ensures that extreme values do not disproportionately influence model training.
- **Creation of new features**: New features, such as ‘Weekly Wage Reported’ and ‘IME-4 Reported,’ helped manage outliers by focusing on binary indicators rather than raw values. This approach simplifies complex variables, reducing the impact of extreme values and enhancing the model's robustness against variability.


---
---