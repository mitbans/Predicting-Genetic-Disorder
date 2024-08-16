# Predicting the Genetic Disorder

## Context
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

## Business Understanding

#### Objective:
Predict the genetic disorder and its subclass in children based on various medical and genetic attributes.

#### Goals:
- Develop a model to accurately classify the type of genetic disorder and its subclass.
- Provide insights to aid healthcare professionals in early diagnosis and treatment planning.

## Data Understanding

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
16. **Respiratory Rate (breaths/min)**: The respiratory rate of the patient (Normal or abnormal).
17. **Heart Rate (rates/min)**: The heart rate of the patient (Normal or abnormal).
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

**Missing Values:**
- Several columns contain missing values, notably in maternal and paternal ages, certain medical tests, and specific genetic information.
- It is crucial to address these missing values through imputation or other suitable methods to ensure robust model training.

**Data Types:**
- The dataset includes both numerical (float64) and categorical (object) data types.
- Conversion and encoding of categorical variables will be necessary for machine learning model training.

**Initial Observations:**
- The dataset provides comprehensive medical and genetic information which can be leveraged to predict genetic disorders.
- The presence of symptoms, medical test results, and parental genetic information are likely to be key predictors for the target variables.
- Handling missing values, identifying outliers, data cleaning, data balancing and feature engineering are critical preprocessing steps to ensure the effectiveness of the predictive models.
  
#### Potential Challenges
- **Complex Interactions:** Genetic factors can interact with environmental and other factors in complex ways.
- **Data Privacy:** Handling sensitive patient data requires appropriate privacy measures. Remove such columns.
- **Interpretability:** Understanding the reasons behind model predictions can be challenging due to the complexity of genetic data.

By thoroughly understanding and preparing the data, we can build accurate and reliable models to predict genetic disorders and their subclasses, ultimately aiding in early diagnosis and treatment planning.

## Data Preparation

The data preparation phase is crucial for ensuring that the dataset is clean, consistent, and suitable for model training. This involves handling missing values, encoding categorical variables, scaling numerical features, and potentially feature engineering. Here are the detailed steps for data preparation:

#### Data Cleaning:

**Drop Irrelavent columns**
- Remove columns that do not contribute to the prediction of genetic disorders, ensuring a more focused dataset.
- Following columns are identified irrelavent: 'Patient Id', 'Patient First Name', 'Family Name', 'Father's name', 'Test 1', 'Test 2', 'Test 3', 'Test 5' (Test 1-3 and 5 have all values = 0)

**Find and Remove Duplicates (if any)**: No Duplicates found.

**Rename Columns**
- Rename columns with appropriate short names for clarity and ease of use.

### Exploratory Data Analysis (EDA)

In the Data Exploration phase, conducted a thorough analysis to uncover patterns, relationships, and insights within the dataset. 
Key activities included:

- Descriptive Statistics
- Distribution Analysis
- Correlation Analysis
- Missing Values Analysis
- Categorical Data Analysis
- Outlier Detection
- Bivariate Analysis


