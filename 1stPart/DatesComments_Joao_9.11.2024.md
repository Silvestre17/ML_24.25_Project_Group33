
<div class="alert alert-block alert-danger" style="font-weight: bold; font-size: 60px;">

FINISH AND CONFIRM THIS SECTION

</div>

#### **`Accident Date` Analysis**

- **Missing Values:** Both the train and test data show approximately 0.6% of missing values for the "Accident Date" field.
- **Date Distribution:** Histograms and boxplots reveal a highly skewed distribution with numerous negative outliers in both the training and test datasets. In the training data, dates range from September 6, 1961, to September 29, 2023, while in the test data, they span from October 28, 1966, to June 4, 2024. This suggests a long record of historical accident data in both datasets
- **Interquartile Range (IQR):** For the training data, the IQR covers about 553 days, with most accidents occurring between *September 14, 2020*, and *March 21, 2022*. While for the test data, the IQR covers about 267 days with most accidents occuring between *April 14, 2023* and *January 6, 2024*. The training data shows a broader spread of accident dates (553 days) compared to the test data (267 days), indicating that accidents in the test data are more concentrated within a shorter timeframe.
- **Outliers:** In the training data, there are a total of **5,666 outliers** (0.99%) while in the test data there are a total of **5047 outliers** (1.3%). Despite both the training and test data having a small proportion of outliers, outliers in test data span from 1966 to 2022 while train data outliers only span from 1961 to 2018. This shows that the test set includes more recent outliers.


#### **`Assembly Date` Analysis**

- **Missing Values:** There are no missing values for the "Assembly Date" field.
- **Data Distribution**: While not perfectly uniform, the histogram shows a relatively steady count of occurrences across most time periods while having some clear fluctuations. 
- **Interquartile Range (IQR):** For the training data, the assembly data extends from *January 1, 2020* to *December 31, 2022* covering a total of 539 days. For the test data, the assembly data extrends from *January 2, 2023* to *June 5, 2024* covering a total of 261 days showing a similar behavior to accident dates where test data are more concentrated within a shorter timeframe.
- **Outliers:** There are no outliers detected, suggesting that the "Assembly Date" data is more consistent.




#### **`C-2` and `C-3 Date` Analysis**

- **Missing Values:** Missing values are a notable issue in both the training and test datasets, particularly for the "C-3 Date" feature, with 78% of data missing in the test data and 68% missing in the training data.
- **Data Distribution:**  Both features show a highly skewed distribution in training and test data, where the vast majority of records are concentrated in recent years. The long left "tail" extending to earlier years is explained by sparse outlier values.
 **Interquartile Range (IQR):** In both the training and test datasets, the features C-2 Date and C-3 Date have similar Interquartile Ranges (IQR). For the training data, C-2 Date spans 536 days, and C-3 Date spans 540 days. In the test data, C-2 Date covers 260 days, while C-3 Date covers 255 days. This reinforces the trend of test data being concentrated within a shorter timeframe compared to the training data.
- **Outliers:** While the "C-2 Date" has **1,229 outliers** (0.21%) in trainning data and **541 outliers** (0.14%) in test data, the "C-3 Date" shows a low prevalence of outliers in both train data (36) and test data (30). The presence of outliers in C-2 data suggests some potential discrepancies.




##### **`First Hearing Date` Analysis**

- **Missing Data:** Missing values are a notable ussue in both datasets with 74% of data missing in train data and 89% of data missing in the test data. This could impact any analysis related to legal or procedural timings
- **Data Distribution:**  In the training data, the distribution of dates appears roughly normal while in the test data, it seems to be left skewed with the data being more concentrated in recent years
- **Interquartile Range (IQR):** In the training data, the IQR spans 589 days (from June 1, 2021, to January 11, 2023), reflecting a wider distribution of hearing dates relative to accidents. In contrast, the test data's IQR covers only 190 days (from September 7, 2023, to March 15, 2024), indicating a higher concentration of hearings within a shorter timeframe in the test data. This suggests that the test data has less temporal variability compared to the training data.
- **Outliers:** There are no detected outliers for "First Hearing Dates," suggesting that despite missing data, the available dates fall within an expected range.

<br>

#### **Distribution Patterns**

- **By Weekday**
   - Claims predominantly occur on weekdays, with a significant drop over weekends, indicating that workplace-related accidents are more common during typical business days.

- **By Day of the Month**
   - Claims distribution is fairly consistent across different days of the month, showing no significant spikes or drops.

- **By Month**
  - There are observable seasonal trends, with March showing higher claims for various dates. This might indicate seasonal work-related risks or reporting patterns.

- **By Year**
  - Claims sharply increased around 2019, peaking in 2021 and 2022, possibly due to changes in reporting practices, regulations, or actual incident rates.
  - The decline in 2023 could indicate underreporting, changes in data collection, or improvements in workplace safety.

- **Outliers and Data Consistency**
  - The significant number of outliers for "Accident Dates" suggests the presence of legacy or erroneous records. It's crucial to validate these to prevent skewing the analysis.
  - The consistency in the "Assembly Date" and "C-3 Date" data, with no outliers, indicates higher data quality for these fields.

---

> **Summary:** The analysis highlights trends in accident claims related to weekdays, seasonal effects, and variations across years. The data quality varies by field, with significant missing values in some cases and historical outliers in others, which should be addressed to ensure accurate insights.

<br>

> It is important to note that we assuming that the logical chronological order is **Accident Date --> C-2 Date or C-3 Date --> Assembly Date --> First Hearing Date**, let's check if for each case **Accident date** is smaller than the others dates. (Consistency Check)
   
</div>