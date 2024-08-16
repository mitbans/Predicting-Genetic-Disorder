## Predicting the Genetic Disorder

### Context
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

### Business Understanding

#### Objective:
Predict the genetic disorder and its subclass in children based on various medical and genetic attributes.

#### Goals:
- Develop a model to accurately classify the type of genetic disorder and its subclass.
- Provide insights to aid healthcare professionals in early diagnosis and treatment planning.

### Data Understanding

#### Overview:
The dataset, sourced from Kaggle, contains medical information about 22,083 children with genetic disorders with genetic disorders, aimed at predicting the type of genetic disorder and its subclass. There are 39 columns, each representing different attributes related to the patients' genetic, parental, and medical conditions.

- DataSet URL: https://www.kaggle.com/datasets/mukund23/predict-the-genetic-disorder/data

#### Data Collection
- Load the DataSet: ../data/train.csv


