# LIVERAID: A study in liver diseases

A study was conducted by Global Burden of Disease and Institute of Health Metrics and Evaluation at the University of Washington, Seattle about the different burden of diseases(number of incidence and death) for 195 countries. One of the diseases included in the study is liver diseases such as Hepatitis B, Hepatitis C, alcohol liver disease, nonalcoholic fatty liver, and cirrhosis. The result of their study estimates that liver diseases account for 2.2 million deaths in 2017 worldwide. In addition to that, there were about one million new cases of liver cancer and 5.2 million cases of cirrhosis estimated diagnosed in 2017.

Liver disease is the 12th cause of death in the United States based on the study by CDC in 2017 and the top cause of death for those aged 35 - 49 years old in England and Wales.


## Project Goal
Understand the different factors associated with diagnosing liver disease and train a Machine Learning model that would be able to help identify the presence of a liver disease.

Note: The prediction of the trained model is not a definite diagnosis of having such liver disease. Further tests and interpretation from medical practitioners should be done to properly detect the presence of a disease.

##### Data Overview
The data for this project was obtained from [Kaggle](https://www.kaggle.com/uciml/indian-liver-patient-records).

> Patients with Liver disease have been continuously increasing because of excessive consumption of alcohol, inhale of harmful gases, intake of contaminated food, pickles and drugs. This dataset was used to evaluate prediction algorithms in an effort to reduce burden on doctors.

>This data set contains 416 liver patient records and 167 non liver patient records collected from North East of Andhra Pradesh, India. The "Dataset" column is a class label used to divide groups into liver patient (liver disease) or not (no disease). This data set contains 441 male patient records and 142 female patient records.
Any patient whose age exceeded 89 is listed as being of age "90".

From [Kaggle](https://www.kaggle.com/uciml/indian-liver-patient-records) Dataset Homepage

| Columns                    | Data Type   |
|----------------------------|-------------|
| Age                        | Ratio     |
| Gender                     | Nominal |
| Total_Bilirubin            | Ratio            |
| Direct_Bilirubin           | Ratio            |
| Alkaline_Phosphate         | Ratio            |
| Alamine_Aminotransferate   | Ratio            |
| Aspartate_Aminotransferate | Ratio            |
| Total_Proteins             | Ratio            |
| Albumin                    | Ratio            |
| Albumin_and_Globulin_Ratio | Ratio            |
| Dataset                    | Nominal            |

#### Data Challenges
1. Imbalanced Datadistribution
The dataset is composed of 583 rows of data with 416 records representing liver patients and 167 records represents non-liver patient records. 
2. Data Multicollinearity
There are some features in our dataset that are highly correlated to each other.
1. Total_Bilirubin and Direct_Bilirubin
2. Aspartate_Aminotransferate and Alamine_Aminotransferase
3. Albumin and Total Proteins
4. Albumin_and_Globulin_Ratio and Albumin

#### Model Evaluation
Laying what the confusion matrix means for our classifier will help us determine what evaluation metrics are necessary for us to create a system that will help diagnose whether a patient has liver disease.

* True Positive: Patients with liver disease that is predicted to have the disease.
* True Negative: Patients without liver disease that is predicted to have no disease.
* False Positive: Patients without liver disease that is predicted to have the disease.
* False Negative: Patients with liver disease that is predicted to have no disease.

Our dataset is highly imbalanced. The evaluation of the model should rule out the use of accuracy as a sole metric because a high classification accuracy can still be achieved even with high false-positive and negative rates. Given this, we decided to use F1-Score as the primary metric to evaluate our models, a combination of precision and recall.

This project aims to create a system that should only be treated as an aid to medical professionals and should not be the primary tool for deciding a patient's status concerning liver diseases. A classifier with a high false-positive and false-negative rate can still be catastrophic for diagnosis.

* Precision =  \frac{True Positive }{(True Positive + False Positive)}
* Recall =  \frac{True Positive }{(True Positive + False Negative)}
* F1 =  \frac{2 * (Precision * Recall)}{(Precision + Recall)}

Having a high precision value means the desire to lessen the false-positive diagnosis of liver disease to avoid unnecessary medicine recommendation and cost to the patient. On the other hand, high recall is how much we want the classifier to correctly diagnose those with liver disease patients as much as possible. F1 is a combination of precision and recall that will suitably address both of the wanted metrics.

#### Model Training and Selection

The task involves trying to identify whether a person given its information, and chemical compounds has a probability of exhibiting a liver disease(Patient_status = 1) or not (Patient_Status = 0). We will experiment different kinds of classification models to in order to find which model can give us the highest F1 score. 

Cluster-Based Model
* K-Nearest Neighbors

Probabilitic Model
* Naive Bayes

Tree Based Models
* Decision Tree
* Random Forest
* XGBoost

Ensemble Model
* Voting classifier

<ins>Ensemble Model</ins>
* Voting classifier

We will perform two experiments to address the data challenges that we have.
1. Experiment 1: Without Undersampling
2. Experiment 2: With Undersampling

#### Future Work
1. Feature Improvements, Selection, and Elimination
Due to the data limitation that we have, having additional features would greatly increase  our model's performance.
2. Predict Probablity of having the disease*
In addition to predict whether a person is sick or not. It would be good to include models that gives the probability(%) or having liver disease.

#### Conclusion
"Health is wealth", a famous saying that explains how important our health is. The goal of this project is to utilize technology using Machine Learning algorithm in helping to diagnose whether a person is having liver disease or not given its information.

After doing experiments with insufficient and imbalanced dataset, we found how important it is to understand some techniques to handle these kinds of problems. For example, stratification and proper use of scalers helped us achieve a model that does not overfit or underfit.

The model that has the highest F1 score is Voting Classifier with having 85%. With this model, we can help our medical practitioners in diagnosing various liver diseases such as Hepatitis B or C. But keep in mind that result of this project does not aim to replace a proper diagnosis of medical professionals. 


#### References
1. Indian Liver Patient Records. (2020). Retrieved 16 July 2020, from https://www.kaggle.com/uciml/indian-liver-patient-records
2. Liver disease is now the biggest cause of death in those aged between 35-49 years old, new report reveals. (2019, August 21). Retrieved July 16, 2020, from https://britishlivertrust.org.uk/liver-disease-is-now-the-biggest-cause-of-death-in-those-aged-between-35-49-years-old-new-report-reveals/
3. Holland, K. (2020). 12 Leading Causes of Death in the United States. Retrieved 16 July 2020, from https://www.healthline.com/health/leading-causes-of-death#heart-disease
4. "Accuracy, Precision, Recall or F1?", Medium, 2020. [Online]. Available: https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9. [Accessed: 27- Aug- 2020].

#### Contributors
Juan Miguel Trinidad | Jonathan Musni
Data Science | Masters Technical Intern at DXC Technology Applied AI Center of Excellence: DXC Applied AI Studio
