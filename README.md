# Predicting the 🧬 Genetic Disorder
Capstone Project at UC Berkeley: PC-MLAI

**Author:** Mitali Bansal

**🔍 Research Question:** How can we accurately predict the type and subclass of genetic disorders in children based on their medical information and family history?

## 🎯 Executive summary
### Rationale
As per reports, as a consequence of the unsustainable increase in population and a lack of access to adequate health care, food, and shelter, the number of genetic disorder ailments have increased. Hereditary illnesses are becoming more common due to a lack of understanding about the need for genetic testing. Often kids die as a result of these illnesses, thus genetic testing during pregnancy is critical.

<div align="center">
    <img width="383" alt="image" src="https://github.com/mitbans/Predicting-Genetic-Disorder/blob/main/images/dna.png">
</div>

#### CRISP-DM (Cross-Industry Standard Process for Data Mining) Framework
- Using CRISP-DM framework to predict genetic disorders and their subclasses.
- CRISP-DM consists of six phases: Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, and Deployment.

  <div align="center">
    <img width="354" alt="image" src="https://github.com/mitbans/Predicting-Genetic-Disorder/blob/main/images/crisp.png">
  </div>

## 🌐 Business Understanding
#### Objective:
Predict the genetic disorder and its subclass in children based on various medical and genetic attributes.

#### Goals:
- Develop a model to accurately classify the type of genetic disorder and its subclass.
    - Genetic Disorders -> Disorder Subclass
        - Mitochondrial genetic inheritance disorders
            - Leigh syndrome
            - Mitochondrial myopathy
            - Leber's hereditary optic neuropathy 
        - Single-gene inheritance diseases
            - Cystic fibrosis
            - Tay-Sachs
            - Hemochromatosis 
        - Multifactorial genetic inheritance disorders
            - Diabetes
            - Alzheimer's
            - Cancer
- Provide insights to aid healthcare professionals in early diagnosis and treatment planning.

## 🗂️ Data Understanding

#### Overview:
The dataset, sourced from Kaggle, contains medical information about 22,083 children with genetic disorders with genetic disorders, aimed at predicting the type of genetic disorder and its subclass. There are 45 columns, each representing different attributes related to the patients' genetic, parental, and medical conditions, including 2 columns of target outputs - genetic disoder and its subclass.

- DataSet URL: https://www.kaggle.com/datasets/mukund23/predict-the-genetic-disorder/data

#### Data Collection
- Load the DataSet: ../data/train.csv

#### Data Description:

1. **Patient Id**: A unique identifier for each patient.
2. **Patient Age**: The age of the patient (child) in years.
3. **Genes in mother's side**: Information on whether there are genetic conditions in the maternal family.
4. **Inherited from father**: Information on genetic traits inherited from the father.
5. **Maternal gene**: Whether genes inherited from the mother.
6. **Paternal gene**: Whether genes inherited from the father.
7. **Blood cell count (mcL)**: Blood cell count measured in microliters.
8. **Patient First Name**: First name of the patient.
9. **Family Name**: Family name of the patient.
10. **Father's name**: Name of the patient's father.
11. **Mother's age**: Age of the mother at the time of the child's birth.
12. **Father's age**: Age of the father at the time of the child's birth.
13. **Institute Name**: Name of the medical institute where the patient is being treated.
14. **Location of Institute**: Geographical location of the medical institute. 
15. **Status**: The current health status of the patient (e.g., alive, deceased).
16. **Respiratory Rate**: The respiratory rate of the patient (Normal or abnormal).
17. **Heart Rate**: The heart rate of the patient (Normal or abnormal).
18. **Test 1**: Results from unspecified medical test.
19. **Test 2**: Results from unspecified medical test.
20. **Test 3**: Results from unspecified medical test.
21. **Test 4**: Results from unspecified medical test.
22. **Test 5**: Results from unspecified medical test.
23. **Parental consent**: Whether parental consent was obtained for genetic testing.
24. **Follow-up**: Follow-ups after initial diagnosis or treatment.
25. **Gender**: Gender of the patient (e.g., male, female).
26. **Birth asphyxia**: Information on whether the patient experienced birth asphyxia.
27. **Autopsy shows birth defect (if applicable)**: Whether autopsy revealed any birth defects.
28. **Place of birth**: The location where the patient was born (Institute or Home).
29. **Folic acid details (peri-conceptional)**: Details about folic acid intake during the peri-conceptional period.
30. **H/O serious maternal illness**: History of serious maternal illness during pregnancy.
31. **H/O radiation exposure (x-ray)**: History of maternal radiation exposure (e.g., X-rays) during pregnancy.
32. **H/O substance abuse**: History of maternal substance abuse during pregnancy.
33. **Assisted conception IVF/ART**: Whether the child was conceived via assisted reproductive technologies like IVF.
34. **History of anomalies in previous pregnancies**: Information on any anomalies in previous pregnancies.
35. **No. of previous abortions**: Number of abortions the mother had before this pregnancy.
36. **Birth defects**: Presence of any birth defects in the patient.
37. **White Blood cell count (thousand per microliter)**: White blood cell count in thousands per microliter.
38. **Blood test result**: Results of unspecified blood tests.
39. **Symptom 1**: Result from unspecified symptom observed in the patient.
40. **Symptom 2**: Result from unspecified symptom observed in the patient.
41. **Symptom 3**: Result from unspecified symptom observed in the patient.
42. **Symptom 4**: Result from unspecified symptom observed in the patient.
43. **Symptom 5**: Result from unspecified symptom observed in the patient.
44. **Genetic Disorder**: The type of genetic disorder diagnosed in the patient (target variable).
45. **Disorder Subclass**: The subclass of the genetic disorder diagnosed in the patient (target variable).

#### Data Summary:
- **12 Numerical Columns**: 'Patient Age', 'Blood cell count (mcL)', "Mother's age", "Father's age", 'Test 1', 'Test 2', 'Test 3', 'Test 4', 'Test 5', 'No. of previous abortion', 'White Blood cell count (thousand per microliter)', 'Symptom 1', 'Symptom 2', 'Symptom 3', 'Symptom 4', 'Symptom 5'.

- **23 Categorical Columns**: 'Patient Id', "Genes in mother's side", 'Inherited from father', 'Maternal gene', 'Paternal gene', 'Patient First Name', 'Family Name', "Father's name", 'Institute Name', 'Location of Institute', 'Status', 'Respiratory Rate (breaths/min)', 'Heart Rate (rates/min', 'Parental consent', 'Follow-up', 'Gender', 'Birth asphyxia', 'Autopsy shows birth defect (if applicable)', 'Place of birth', 'Folic acid details (peri-conceptional)', 'H/O serious maternal illness', 'H/O radiation exposure (x-ray)', 'H/O substance abuse', 'Assisted conception IVF/ART', 'History of anomalies in previous pregnancies', 'Birth defects', 'Blood test result', 'Genetic Disorder', 'Disorder Subclass'.

#### Data Considerations
- **Missing Values:**
    - Several columns contain missing values, notably in maternal and paternal ages, certain medical tests, and specific genetic information.
    - It is crucial to address these missing values through imputation or other suitable methods to ensure robust model training.
- **Data Types:**
    - The dataset includes both numerical (float64) and categorical (object) data types.
    - Conversion and encoding of categorical variables will be necessary for machine learning model training.
- **Initial Observations:**
    - The dataset provides comprehensive medical and genetic information which can be leveraged to predict genetic disorders.
    - The presence of symptoms, medical test results, and parental genetic information are likely to be key predictors for the target variables.
    - Handling missing values, identifying outliers, data cleaning, data balancing and feature engineering are critical preprocessing steps to ensure the effectiveness of the predictive models.

#### Potential Challenges
- **Complex Interactions:** Genetic factors can interact with environmental and other factors in complex ways.
- **Data Privacy:** Handling sensitive patient data requires appropriate privacy measures. Remove such columns.
- **Interpretability:** Understanding the reasons behind model predictions can be challenging due to the complexity of genetic data. 

By thoroughly understanding and preparing the data, we can build accurate and reliable models to predict genetic disorders and their subclasses, ultimately aiding in early diagnosis and treatment planning.

## 🧰 Data Preparation

The data preparation phase is crucial for ensuring that the dataset is clean, consistent, and suitable for model training. This involves handling missing values, encoding categorical variables, scaling numerical features, and potentially feature engineering. Here are the detailed steps for data preparation:

### Data Cleaning:
- **Drop Irrelavent columns**
    - Remove columns that do not contribute to the prediction of genetic disorders, ensuring a more focused dataset.
    - Following columns are identified irrelavent: 'Patient Id', 'Patient First Name', 'Family Name', 'Father's name', 'Test 1', 'Test 2', 'Test 3', 'Test 5' (Test 1-3 and 5 have all values = 0)
- **Find and Remove Duplicates (if any)**: No Duplicates found.
- **Rename Columns**
  - Rename columns with appropriate short names for clarity and ease of use.

### 📊 Exploratory Data Analysis (EDA)

In the Data Exploration phase, conducted a thorough analysis to uncover patterns, relationships, and insights within the dataset. 
Key activities included:

#### **Missing Values Analysis:** 
Most columns have a missing rate of around 9-10%, with a few columns having more substantial gaps.
- **Low Missing Values (1% - 10%)**: *Inherited from father* (1.39%), *Patient Age* (6.46%).
- **Moderate Missing Values (9% - 10%)**: Many columns, such as *Respiratory Rate*, *Heart Rate*, *Parental Consent*, *Gender*, *Birth Asphyxia*, *WBC Count*, *Test 4* and *Genetic Disorder*, have around 9-10% missing data.
- **High Missing Values (Above 10%)**: *Maternal gene* (12.72%), *Birth Defect* (19.89%).
- **Very High Missing Values (Above 20%)**: *Mother's Age* (27.33%) and *Father's Age* (27.11%).    
    
#### **Descriptive Statistics**
- **Patient Age**: Average of 6.97 years, ranging from 0 to 14 years.
- **Blood Cell Count**: Average of 4.90 mcL, with values between 4.09 and 5.61 mcL.
- **Mother's Age**: Average of 34.53 years, ranging from 18 to 51 years.
- **Father's Age**: Average of 41.97 years, ranging from 20 to 64 years.
- **Test 4**: Uniform value of 1.0 across all records with ~10% missing values.
- **Previous Abortion Count**: Average of 2.0, ranging from 0 to 4.
- **WBC Count**: Average of 7.49 (thousand per microliter), ranging from 3.0 to 12.0.
- **Symptoms 1-5**: Binary indicators (0 or 1) for the presence of symptoms.

#### **Distribution Analysis:**
Visualized the distributions of key variables using histograms, density plots and box plots to understand their spread and identify any skewness or kurtosis. This helped in detecting potential outliers and understanding the general data shape.

- **Summary of the Distribution Analysis for Numerical Variables:**

    - **patient age** shows a median of 7 years, with the majority of patients falling between 3 and 11 years. The whiskers extend from 0 to 14 years, indicating the full range of data, with no significant outliers beyond these whiskers.
    - **Blood Cell Count** shows a normal distribution centered around an average of 4.90 mcL, with the majority of values between 4.75 mcL and 5.25 mcL. The full range spans from 4.4 mcL to 5.4 mcL, with some outliers extending to 4.09 mcL and 5.61 mcL.
    - **Mother age** shows a median of 35 years, with majority of mothers falling between 25 to 45 years. The whiskers extend from 18 to 51, with no significant outliers.
    - **Father age** shows a median of 42 years, with majority of fathers falling between 30 to 53 years. The whiskers extend from 20 to 64, with no significant outliers.
    - **Test 4** shows all data has a value of 1 excluding the ones missing.
    - **Previous Abortion Count** shows a median of 2 years, with majority of data falling between 1 to 3. The whiskers extend from 0 to 4, with no significant outliers.
    - **WBC Count** shows a normal distribution centered around an average of 7.49 (thousand per microliter), with the majority of values between 5.5 and 9.5. The full range spans from from 3.0 to 12.0, with no outliers.

- **Summary of the Distribution Analysis for Categorical Variables:**
    - **Data Categorization and Distribution Analysis**: To effectively analyze and model this data, we can categorize the features into several groups, this categorization can help in understanding the relationships between different features and their impact on predicting genetic disorders:
        - **Patient Demographics**:
            - Patient Age
            - Gender (Ambiguous, male, female) - distribution is quite balanced, slightly higher for ambiguous
        - **Patient Birth History**:
            - Birth defect (Yes, No) - **strong skew** towards no birth defects
            - Birth defects (Singular, Multiple) - equal distribution, no significant skew
            - Birth asphyxia (Yes, No) - majority: **strong skew** towards no birth asphyxia
            - Autopsy shows birth defect (Yes, No)
            - Place of birth (Institute or Home)
        - **Patient Current Health Status:**
            - Status (alive, deceased) - no significant skew in this category, equal distribution
            - Respiratory Rate (Normal, Tachypnea) - no strong skew, nearly equal distribution
            - Heart Rate (Normal, Tachycardia) - occurrence of a normal heart rate is slightly higher but the difference is not substantial
            - Blood cell count (mcL)
            - White Blood cell count (thousand per microliter)
            - Blood test result (Slightly abnormal, normal, Inconclusive, abnormal) - relatively balanced, no strong skew
            - Test 1 - Test 5 (1, 0)
            - Symptom 1 - Symptom 5 (1, 0)
        - **Parents Demographics**
            - Mother's age
            - Father's age
        - **Genetic Information**
            - Genes in mother's side (Yes, No) - skew towards maternal inheritance
            - Inherited from father (Yes, No) - skew towards no paternal inheritance
            - Maternal gene (Yes, No) - higher occurrence of maternal gene, difference is less pronounced
            - Paternal gene (Yes, No) - higher occurrence of no paternal gene
        - **Pregnancy related factors**
            - H/O serious maternal illness (Yes, No) - equal distribution, no significant skew
            - Folic acid details (peri-conceptional) (Yes, No) - equal distribution, no significant skew
            - Assisted conception IVF/ART (Yes, No) - equal distribution, no significant skew
        - **Environmental factors**
            - H/O radiation exposure (x-ray) (Yes, No) - strong skew towards no radiation exposure
            - H/O substance abuse (Yes, No) - strong skew towards no substance abuse
        - **Previous Pregnancies**
            - History of anomalies in previous pregnancies (Yes, No) - nearly even distribution, no strong skew
            - No. of previous abortions
        - **Consents & Follow-ups**
            - Parental consent - all cases have parental consent
            - Follow-up (Low, High) - no significant skew in this category, equal distribution
        - **Target Variables**
            - Genetic Disorder (target variable) - a skew towards mitochondrial disorders
            - Disorder Subclass (target variable) -  skewed towards a few dominant subclasses
    
- **Summary of Outlier Detection:**
    - `Blood Cell Count` shows some outliers in the box plot, may require handling (if required).

#### **Bivariate Analysis:**

##### **Correlation Analysis - Numerical vs. Numerical variables**
- Compute the correlation matrix for numeric features using .corr().
- Visualize correlations using a heatmap.
- Explore relationships between features, especially between features and the target variable.
    - Use pair plots or scatter plots for this purpose.

    **Correlation Summary:**
    - The correlation matrix shows how each feature in the dataset is related to the others. 
    - Most correlations are close to zero, indicating weak or no linear relationships between the variables.
    - The strongest positive correlation is seen between Symptom 4 and Symptom 5 (0.0368)
    - Patient Age has minimal correlations with other features.
    - The NaN values for Test 4 suggest there was no data available for this feature, leading to undefined correlations.

##### **Categorical Vs. Categorical Variables**
- Histograms for all categorical variable to visualize the distribution by target variable (Genetic Disorder).

##### **Numerical vs. Categorical:** 
Analyze Box plots, bar plots for Numerical Vs. Target cols.

### Data Pre-processing
- Handling Missing Values
- Handling Outliers (if required)

####  Handling Missing Values

Missing values can significantly affect the performance of machine learning models. We need to address them appropriately.

- **Numerical Columns**:
    - Binary Columns like `Symptom 1 - 5` and `Test 4`, we can fill Nan values with 0.
    - For columns like 'Patient Age', 'Blood cell count', 'Mother age', 'Father age', 'Previous abortion count', 'WBC count', we can fill missing values with the median of the column to avoid the influence of outliers.

- **Categorical Columns**: For columns like `Inherited from father`, `Maternal gene`, `Respiratory Rate`, `Heart Rate`, `Parental consent`, `Follow-up`, `Gender`, `Birth asphyxia`, `Birth defect`, `Place of birth`, `Folic acid`, `Serious maternal illness`, `Radiation exposure`, `Substance abuse`, `Assisted conception`, `Anomalies in previous pregnancies`, `Birth defects`, `Blood test result`, we can fill missing values with `'Not Available'` for each column.

- **Target Columns**: First, the missing values in the `Genetic Disorder` column are filled based on the `Disorder Subclass`. After that, the missing values in the `Disorder Subclass` are filled with the mode for each `Genetic Disorder` category.olumn.

### Feature Selection: Filter Methods
- Chi-Sqaure Tests
- ANOVA Tests

#### **Contingency tables (cross-tabulation) and Chi-square tests**
- Measures the dependence between categorical features and the target categorical variable.

- **Summary of Chi-Square Tests for 'Genetic Disorder'**

    The Chi-Square test results indicate significant associations between the following features and genetic disorders:
    
    1. **Inherited from mother**: Chi-Square = 203.93, p-value = 5.21e-45
    2. **Inherited from father**: Chi-Square = 198.35, p-value = 8.51e-42
    3. **Maternal gene**: Chi-Square = 126.59, p-value = 2.09e-26
    4. **Paternal gene**: Chi-Square = 115.47, p-value = 8.43e-26
    5. **Blood test result**: Chi-Square = 21.40, p-value = 0.0062
    
    These features show a significant relationship with the presence of a genetic disorder.
    
    On the other hand, several features, such as **Status**, **Respiratory Rate**, **Heart Rate**, **Parental consent**, and others, do not show a significant association with genetic disorders based on their high p-values.
    
    The **selected features** that are significantly associated with genetic disorders are:
    - 'Inherited from mother', 'Inherited from father', 'Maternal gene', 'Paternal gene', 'Blood test result'

- **Summary of Chi-Square Tests for 'Disorder Subclass'**

    The Chi-Square test results show significant associations between the following features and **Disorder Subclass**:
    
    1. **Inherited from mother**: Chi-Square = 761.40, p-value = 4.28e-159
    2. **Inherited from father**: Chi-Square = 718.09, p-value = 1.82e-142
    3. **Maternal gene**: Chi-Square = 620.84, p-value = 8.65e-122
    4. **Paternal gene**: Chi-Square = 545.36, p-value = 1.29e-112
    5. **Blood test result**: Chi-Square = 46.72, p-value = 0.045
    
    These features have a significant association with Disorder Subclass.
    
    Other features, such as **Status**, **Respiratory Rate**, **Heart Rate**, **Parental consent**, and others, do not show a significant association with Disorder Subclass, as indicated by their high p-values.
    
    The **selected features** significantly associated with Disorder Subclass are:
    - 'Inherited from mother', 'Inherited from father', 'Maternal gene', 'Paternal gene', 'Blood test result'

#### **ANOVA (Analysis of Variance) Tests** 
- The goal is to see if there is a significant difference in the mean of continuous features across the different categories of Genetic Disorder (target variable).

- **Summary ANOVA tests for 'Genetic Disorder'**

    The ANOVA results reveal significant associations between **Symptom 1**, **Symptom 2**, **Symptom 3**, **Symptom 4**, and **Symptom 5** with **Genetic Disorder**, as indicated by their low p-values:
    
    1. **Symptom 1**: F-statistic = 107.55, p-value = 3.33e-47
    2. **Symptom 2**: F-statistic = 185.16, p-value = 1.83e-80
    3. **Symptom 3**: F-statistic = 307.47, p-value = 2.08e-132
    4. **Symptom 4**: F-statistic = 341.09, p-value = 1.37e-146
    5. **Symptom 5**: F-statistic = 521.79, p-value = 4.42e-222
    
    These symptoms show a significant association with the presence of a genetic disorder.
    
    Other variables, such as **Patient Age**, **Blood cell count**, **Mother age**, **Father age**, and **Previous abortion count**, do not show a significant association with Genetic Disorder, as indicated by their high p-values.
    
    The **selected features** significantly associated with Genetic Disorder based on ANOVA are:
    - 'Symptom 1', 'Symptom 2', 'Symptom 3', 'Symptom 4', 'Symptom 5'

- **Summary ANOVA tests for 'Disorder Subclass'**

    The ANOVA results for **Disorder Subclass** indicate significant associations with the following symptoms:
    
    1. **Symptom 1**: F-statistic = 118.10, p-value = 2.27e-194
    2. **Symptom 2**: F-statistic = 204.27, p-value = 0.0
    3. **Symptom 3**: F-statistic = 295.72, p-value = 0.0
    4. **Symptom 4**: F-statistic = 385.57, p-value = 0.0
    5. **Symptom 5**: F-statistic = 556.77, p-value = 0.0
    
    These symptoms are significantly associated with Disorder Subclass.
    
    On the other hand, features such as **Patient Age**, **Blood cell count**, **Mother age**, **Father age**, **Test 4**, **Previous abortion count**, and **WBC count** do not show a significant association with Disorder Subclass, as their p-values are high.
    
    The **selected features** significantly associated with Disorder Subclass based on ANOVA are:
    - 'Symptom 1', 'Symptom 2', 'Symptom 3', 'Symptom 4', 'Symptom 5'

#### Selected Featues from Chi-Square and ANOVA Methods:
- **Categorical:** 'Inherited from mother', 'Inherited from father', 'Maternal gene', 'Paternal gene', 'Blood test result'
- **Numerical/Binary:** 'Symptom 1', 'Symptom 2', 'Symptom 3', 'Symptom 4', 'Symptom 5'

### Engineering Features
#### Encoding Categorical Variables and Scaling Numnerical Variables
Machine learning algorithms require numerical input. Hence, we need to convert categorical variables into numerical formats. Common techniques include:
- **Standard Scalar**: for numerical cols (not required as selected cols are binary 1,0)
- **Ordinal Encoding**: for categorical cols: 'Inherited from mother', 'Inherited from father', 'Maternal gene', 'Paternal gene', 'Blood test result'
    - Output: {'Inherited from mother': {0: 'No', 1: 'Yes'}, 'Inherited from father': {0: 'No', 1: 'Not Available', 2: 'Yes'}, 'Maternal gene': {0: 'No', 1: 'Not Available', 2: 'Yes'}, 'Paternal gene': {0: 'No', 1: 'Yes'}, 'Blood test result': {0: 'Not Available', 1: 'abnormal', 2: 'inconclusive', 3: 'normal', 4: 'slightly abnormal'}}
- **Label Encoding**: for Target cols, two target variables will be predicted and evaluated separately:
    - Genetic Disorder
        - 'Mitochondrial genetic inheritance disorders': 0,
        - 'Multifactorial genetic inheritance disorders': 1,
        - 'Single-gene inheritance diseases': 2
    - Disorder Subclass
        - "Alzheimer's": 0,
        - 'Cancer': 1,
        - 'Cystic fibrosis': 2,
        - 'Diabetes': 3,
        - 'Hemochromatosis': 4,
        - "Leber's hereditary optic neuropathy": 5,
        - 'Leigh syndrome': 6,
        - 'Mitochondrial myopathy': 7,
        - 'Tay-Sachs': 8

### Train/Test Split: y1: Predicting Genetic Disorder
- Selected 80% train size and 20% test size
- Used SMOTE for balancing the target variables

## 🤖 Modeling

In the Modeling Phase, focused on developing and evaluating seven different machine learning models to predict the target variable. The primary goal was to build models that can accurately classify instances based on the input features. 

Utilized the following seven models for evaluation:

1. **K-Nearest Neighbors (KNN)** - `OneVsRestClassifier(KNeighborsClassifier())`
2. **Logistic Regression (LogReg)** - `LogisticRegression(multi_class='multinomial', solver='lbfgs', max_iter=1000)`
3. **Decision Tree Classifier (dTree)** - `DecisionTreeClassifier(random_state=42)`
4. **Support Vector Machine (SVM)** - `SVC(probability=True, random_state=42)`
5. **Random Forest Classifier (RFC)** - `RandomForestClassifier(n_estimators=100, random_state=42)`
6. **Gradient Boosting Machine (GBM)** - `GradientBoostingClassifier(n_estimators=100, random_state=42)`
7. **XGBoost Classifier (XGB)** - `XGBClassifier(objective='multi:softmax', num_class=len(np.unique(y)), eval_metric='mlogloss')`

<div align="center">
    <img width="559" alt="image" src="https://github.com/user-attachments/assets/f11aff11-6c52-409c-95bd-0f795befa4de">
    <img width="986" alt="image" src="https://github.com/user-attachments/assets/7a89812f-6d3a-4551-b487-ead4cface7b9">
    <img width="1121" alt="image" src="https://github.com/user-attachments/assets/7d38531b-9919-400a-8a18-966d8e4a2eba">
    <img width="1122" alt="image" src="https://github.com/user-attachments/assets/1e6a8689-ed16-41dc-b5da-02de4fabd10c">
    <img width="1127" alt="image" src="https://github.com/user-attachments/assets/a7798633-33b1-4c4e-8ac3-762770dbc6bc">
</div>


## ✅ Model Evaluation
- Each model was trained and evaluated using the resampled dataset (via SMOTE to handle class imbalance).
- Metrics such as **accuracy**, **precision**, **recall**, **F1-score**, and **AUC (Area Under the Curve)** were calculated to assess model performance.
- Both weighted and macro/micro-averaged versions of precision, recall, and F1-score were considered for a balanced evaluation across all classes.

### 📝 Initial Findings

1. **SVC is computationally most expensive**: 
   - **SVC** took the longest time to train, indicating it is the most computationally intensive model, with a train time of **152.73 seconds** compared to much faster models like **KNN (0.0664 seconds)** and **XGB (0.5177 seconds)**.

2. **XGB seems to have better results than others**: 
   - **XGBoost (XGB)** consistently outperformed most models with the best **Test Accuracy (0.59)** and **ROC-AUC (Micro: 0.79, Macro: 0.74)**, making it the top-performing model overall.

3. **Based on F1 Score**: 
   - **XGB**, **GBM** and **Random Forest Classifier (RFC)** showed better performance compared to other models, with strong F1 Scores:
     - **XGB**: F1 Macro of **0.54**
     - **GBM**: F1 Macro of **0.53**
     - **RFC**: F1 Macro of **0.52**

4. **Based on ROC-AUC Scores**: 
   - **XGB** and **Gradient Boosting Machine (GBM)** have the best AUC scores:
     - **XGB**: **ROC-AUC Micro: 0.79**, **Macro: 0.74**
     - **GBM**: **ROC-AUC Micro: 0.77**, **Macro: 0.71**
   - They are followed by **SVM** and **RFC**, which have comparable ROC-AUC scores:
     - **SVM**: **ROC-AUC Micro: 0.76**, **Macro: 0.73**
     - **RFC**: **ROC-AUC Micro: 0.75**, **Macro: 0.70**
    
5. **Class 0** is best identified by SVM, GBM, XGB
6. **Class 1** is best identified by logreg, SVM, GBM 
7. **Class 2** is best identified by logreg, KNN, RFC 

These findings indicate that **XGB** and **GBM** offer the best performance across the majority of metrics, making them the top choices for further model refinement or deployment.

### Improving the Models
- **Summary of Findings Following Hyperparameter Tuning and Grid Search**

    - **Best Parameters:**
        - knn_grid_best_params:  {'estimator__metric': 'euclidean', 'estimator__n_neighbors': 15, 'estimator__weights': 'distance'}
        - logreg_grid_best_params:  {'C': 10, 'class_weight': 'balanced', 'penalty': 'l2', 'solver': 'sag'}
        - dtree_grid_best_params:  {'criterion': 'gini', 'max_depth': None, 'min_samples_leaf': 2, 'min_samples_split': 5}
        - svm_grid_best_params:  {'C': 10, 'gamma': 'scale', 'kernel': 'rbf'}
        - rfc_grid_best_params:  {'bootstrap': True, 'max_depth': 50, 'min_samples_leaf': 1, 'min_samples_split': 10, 'n_estimators': 200}
        - gbm_grid_best_params:  {'learning_rate': 0.1, 'max_depth': 4, 'n_estimators': 200, 'subsample': 1.0}
        - xgb_grid_best_params:  {'colsample_bytree': 1.0, 'gamma': 0, 'learning_rate': 0.2, 'max_depth': 5, 'n_estimators': 200, 'subsample': 0.8}

    - **SVC is computationally most expensive**: 
       - **SVC** took the longest time to train, indicating it is the most computationally intensive model, with a train time of **16 min 17 seconds** compared to much faster models like **decision tree (12 seconds)** and **KNN (181 seconds)**.
    
    - **XGB seems to have better results than others**: 
       - **XGBoost (XGB)** consistently outperformed most models with the best **Test Accuracy (0.59)** and **ROC-AUC (Micro: 0.79, Macro: 0.74)**, making it the top-performing model overall.
    
    - **Based on F1 Macro Score**: 
       - **XGB**, **GBM**, **Random Forest Classifier (RFC)** and **SVM** showed better performance compared to other models, with strong F1 Scores:
         - **XGB**: F1 Macro of **0.54**
         - **GBM**: F1 Macro of **0.54**
         - **RFC**: F1 Macro of **0.53**
         - **SVM**: F1 Macro of **0.53**
    
    - **Based on ROC-AUC Scores**: performance improved slightly after hyperparameter tuning
       - **XGB** and **Gradient Boosting Machine (GBM)** have the best AUC scores:
         - **XGB**: **ROC-AUC Micro: 0.79**, **Macro: 0.74**
         - **GBM**: **ROC-AUC Micro: 0.78**, **Macro: 0.73**
       - They are followed by **SVM** and **RFC**, which have comparable ROC-AUC scores:
         - **SVM**: **ROC-AUC Micro: 0.77**, **Macro: 0.73**
         - **RFC**: **ROC-AUC Micro: 0.77**, **Macro: 0.72**
    
    - **Class 0** is best identified by GBM, XGB, SVM
    - **Class 1** is best identified by logreg, SVM, XGB 
    - **Class 2** is best identified by KNN, logreg, RFC, dtree
    - **Logreg with Thresholds:** Although class 0 improved drastically but calss 1 prediction accuracy reduced and class 2 accuracy fell to 0%.
    - **Voting and Stacking Classifiers** did not lead to a noticeable improvement in the prediction outcomes.

These findings indicate that **XGB** and **GBM** offer the best performance across the majority of metrics, making them the top choices for further model refinement or deployment.

<div align="center">
    <img width="605" alt="image" src="https://github.com/user-attachments/assets/2de4a5e7-d13f-4994-9d72-b4013b5e2916">
    <img width="1006" alt="image" src="https://github.com/user-attachments/assets/0c104f4d-31d8-4a5c-bfcb-6eb8434cc3bf">
    <img width="1123" alt="image" src="https://github.com/user-attachments/assets/fd089786-8eb1-4607-9ee1-e1089283d566">
    <img width="1136" alt="image" src="https://github.com/user-attachments/assets/13c6dde3-574e-4140-adc8-64eb40874206">
    <img width="1139" alt="image" src="https://github.com/user-attachments/assets/5602f839-d0d3-45e0-8209-c71ae1d3e0a3">
    <img width="1124" alt="image" src="https://github.com/user-attachments/assets/9163d2f1-7787-418e-8abe-aedb1a234e8e">
</div>


### Feature Importances (XGB model)
#### 🏆 Key Results: 
- **Symptoms:** The five symptoms (Symptom 1 to Symptom 5) are the most important features, accounting for over 90% of the model's predictive power.
- **Genetic Information:** Features related to inheritance (Inherited from mother, Paternal gene, Inherited from father, Maternal gene) have moderate importance.
- **Blood Test Result:** This feature has the lowest importance among the listed features.

## 🚀 Deployment Summary

In the deployment phase, focused on saving the trained models for future use. This step ensures that the models can be easily loaded and reused without the need to retrain them, saving time and computational resources.

### Steps in Deployment:
1. **Model Selection for Deployment**:
   - Based on the evaluation of metrics like accuracy, F1 score, and ROC-AUC, the top-performing models (**XGB**, **GBM**, and **RFC**) were chosen for deployment.
2. **Model Serialization**:
   - Each trained model was serialized and saved using **`joblib.dump`**. This library efficiently saves large models, ensuring they can be reloaded for future predictions.
3. **Model Reloading**:
   - Reload a saved model using **`joblib.load`**
4. **Future Integration**:
   - These saved models are ready for integration into any application or system, where they can be utilized for real-time predictions or batch processing tasks.
   - The deployment ensures that the models can be reused across different environments without re-training, allowing seamless transition from experimentation to production.
5. **Scalability**:
   - Since the models are saved as standalone files, they can be shared across different platforms and systems, making it easier to scale the solution as needed.

By saving the models using `joblib`, ensured the longevity and reusability of the trained models, supporting efficient and scalable deployment.


## ➡️ Next steps
- **Predict type of Disorder Subclass:**
    - Implement machine learning algorithms to classify and predict the specific subclass of a disorder.
      
- **Leverage Neural Networks** to enhance performance metrics.

- **Integration of Diverse Data Types:**
    - **Genomic Data:** Incorporate data from genomic sequencing (e.g., whole genome sequencing, exome sequencing) that provides detailed insights into genetic variations.
    - **Clinical Data:** Gather clinical records, treatment histories, and patient outcomes to provide context to genetic information and enrich feature sets.
    - **Phenotypic Data:** Use phenotypic data (observable traits and characteristics) to correlate genetic variants with clinical manifestations, helping improve model accuracy.
    - **Environmental Factors:** Consider integrating environmental or lifestyle data (e.g., diet, exposure to toxins) that may influence the manifestation of genetic disorders.

- **Utilizing Techniques for Explainability:**
    - **LIME (Local Interpretable Model-agnostic Explanations):** Use LIME to generate locally faithful explanations by approximating the model with an interpretable one around a given prediction.
    - **SHAP (SHapley Additive exPlanations):** Implement SHAP values to quantify the contribution of each feature to individual predictions, providing a global understanding of feature importance and interactions.
    - **Feature Visualization:** For neural networks, techniques like Grad-CAM can be employed to visualize which parts of the input contribute most to the prediction, especially for image data.

## Repository Structure
- <code>data/train.csv</code>: Contains dataset used in the analysis.
- <code>data/test.csv</code>: Contains dataset used for business evaluation / validation.
- <code>deployment/</code>: Contains models ready for deployment or to be used in apps.
- <code>notebooks/Predicting-Genetic-Disorder.ipynb</code>: Jupyter notebook with code for data analysis and modeling.
- <code>README.md</code>: Summary of findings and link to notebook

## Notebook
The detailed analysis and code can be found in the Jupyter notebook <a href="https://github.com/mitbans/Predicting-Genetic-Disorder/blob/main/notebooks/Predicting-Genetic-Disorder.ipynb">here</a>.

---
