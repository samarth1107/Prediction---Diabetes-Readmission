# Prediction---Diabetes-Readmission   

Diabetes is a chronic metabolic disorder in which prevalence has been increasing steadily all over the world. As a
result of this trend, it is fast becoming an epidemic in some
countries of the world. The number of people affected is
expected to double in the next decade. Due to an increase
in the ageing population, they are thereby adding to the already existing burden of hospital management, especially in
poorly developed countries. This project is our contribution
to the doctors and hospital management in these difficult
times (COVID).
The purpose of this study is to classify the patients by
proposing a machine learning model to classify that a patient will be readmitted within 30 days or not. This model
will include risk factors like age, race, gender, etc. (Dataset
Description). In a broader sense, the goal of this study is
to help the hospital management by providing them with a
reasonable estimate of whether a patient will be readmitted
or not. So our research will help to increase the quality of
care and will increase efficiency and reduce the burden of
the hospital management staff.

### To run and apply techniques on dataset ipython file is attached main.


1. Introduction
Given the data of patients suffering from diabetes mellitus, we want to propose a model to predict that the patients
admitted once will be readmitted again within 30 days period or not.    

2. Dataset
There are 50 features present in the dataset. Out of
50, 24 marks the dosage of medications like Metformin,
Glipizide, etc., and the remaining 26 included features like
age, gender, weight, time in the hospital, etc. The 24
features which were marking the dosage of medications
can possess four different types of values:- Up(Increase
dosage), Down(Decrease dosage), Steady(Same dosage)
and No(Drug Not Prescribed). The feature “age” was
present in 10 groups showing the age groups like [0,10), [10,20) etc., and 66.2% of the total dataset population were
older than 60. The feature “race” consisted of values like
African American, Caucasian(74.7% of the entire dataset
population), Other and also there were some missing values. The feature “readmission rate” consisted of three types
of values:- “NO”, “30” days and “30” days. There were also
the results of the A1c test were shown, which is a preliminary test for diabetes mellitus. And there were many more
features which can be looked upon in the given.
UCI Machine Learning Repository


3. Preprocessing
Firstly, it was identified which features have missing
values. There were seven such features. Out of these,
”weight”, ”payer code”, ”medical speciality” had the majority of values missing, so these features were dropped. For
other features, the corresponding rows with missing values
were dropped. After this step, 94% of the data was retained.
The majority of features had string values, so they were converted to discrete integer values.

4. Feature Creation
A new feature was synthesized named ‘service taken’.
This feature was the sum of the columns ‘number outpatient’, ‘number inpatient’ and ‘number emergency’. This
feature summarised the comprehensive services utilized by
the patient before being admitted to the hospital for the first
time. The features ‘Service taken’, ‘number outpatient’,
‘number inpatient’, ‘number emergency’ had a lot of skewness, To overcome this, the log transform was applied to
these features. This helped in synthesizing the next feature.
Some of the features were multiplied with each other to find
a better relationship between them. Some of these are (num
of medications, time in hospital), (age, num of diagnoses).

5. Outlier Removal
The dataset included multiple occurrences of a single patient [3] [6]. For each patient, the subsequent data has been
removed. The reason behind this being characteristic of the
patient might change in terms of lifestyle, age, health, etc.,
which can affect the data. The data on which log transformations was applied have also been standardized.

6. Feature Encoding
The dataset included features like race, gender, admission type id, discharge disposition id, admission source id,
max gluserum, A1C result, level1 diag1 which can be divided into classes, so we used One-Hot Encoding to encode
them.


7. Feature Selection
Several techniques including ANOVA were tested to perform feature selection. The initial test using logistic regression and regularization technique coefficient’s p-values appeared to drop highly significant features from a medical
perspective. Hence, the random forest feature selection was
performed. The variable importance was then computed
during 48 iterations. A total of 25 predictors were thus selected after 48 iterations.


8. Evaluation Metric
Since we divided the dataset into three groups based
on the age of the patient, we decided different evaluation
metrics for each of them. For data corresponding to age
group 0-30 and 30-70, MCC score was a sufficient measure
to determine the best classifier. Along with these other
metrics like precision, recall, f1-score were also taken
into consideration. Those classifiers which were giving
excellent accuracy but performed poorly on other metrics
were not chosen.
For data corresponding to age group 70-100, we focused more on having low false-negativity. The reason
for the following being that this group denotes the senior
citizens. If the classifier predicts the patient doesn’t need to
be readmitted within 30 days, but actually the patient had
to be readmitted, this can lead to loss of life, which is a
severe consequence. The model with decent accuracy and
the comparatively low false-negativity (high MCC score)
was chosen in this case.
