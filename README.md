# Covid-Death-Predictions

### Purpose
The purpose of this project is to model death rates cause by COVID-19 using symptoms and patient characteristics. The data includes 21 variables per patient, with data for over a million patients. The goal of this project is to examine the correlations between patient variables and whether the patient passed away due to COVID, as well as build and tune a logistic regression model of patient deaths. 


### Analysis
The first step was to take a first glance at the data and beginning cleaning up the set. Data was organized / necessary columns created / null values removed after finding low correlation with death of patient. Distributions and box and whisker plots were generated for each variable. A heatmap of all the correlations between variables was generated, however, since we are trying to model the variables correlations with death, these specific correlations were printed as well. Finally, the logistic regression model was fit to the data, and hyperparameters were tuned via GridSearchCV.

### Results
A moderate positive correlation (0.42) was found only between whether the patient was intubated and their death, while a weak positive correlation with death was found with patient development of pneumonia (0.20) and COVID test results (0.21). A moderate negative correlation was also found between age and patient death (-0.31). 

The logistic regression model with default hyperparameters was fit to all variables and had an accuracy of 76%. This was good considering the low correlation coefficients between variables and death, however, the model had very low recall. Precision / accuracy / f1 score / and recall are list in the code output. Regressions were fit to only the variables with moderate correlations coefficients, however, the accuracies of these models were lower. GridSearchCV was used to iterate through and tune hyperparameters for optimization. Interestingly, this did not change the accuracy, recall, precision, and f1-scores of the model, and only ever so slightly decreased the number of false negatives predicted. The optimal parameters were found to be {'C': 0.1, 'l1_ratio': 0, 'max_iter': 5000, 'penalty': 'l2', 'solver': 'sag'}.


Histogram of higher correlation variables
![image](https://user-images.githubusercontent.com/103863038/206120514-c38b77f5-fb78-495a-ab4e-a5ebf7dcee15.png)
![image](https://user-images.githubusercontent.com/103863038/206120674-34baa185-c464-4763-ad31-44c11c0c22d2.png)
![image](https://user-images.githubusercontent.com/103863038/206120727-078fac50-ae7e-4fa0-81f8-e763d8aea60e.png)
![image](https://user-images.githubusercontent.com/103863038/206120786-aab9c842-80d9-4279-98ed-3e73c4cc1b31.png)

Correlation coefficient heatmap
![image](https://user-images.githubusercontent.com/103863038/206120847-1f883b8a-d333-43ff-8138-9e2ab6c67be5.png)

Confusion matrix for default logistic regression
![image](https://user-images.githubusercontent.com/103863038/206120973-56190e56-ba34-4781-b2e8-810a95e1c218.png)

AVG precision: 0.76
AVG recall: 0.76
AVG f1-score: 0.75
accuracy: 0.76

Confusion matrix for GridSearchCV tuned model
![image](https://user-images.githubusercontent.com/103863038/206121060-ae79b6f1-bfc8-4b56-85e7-20f048a672b9.png)

AVG precision: 0.76
AVG recall: 0.76
AVG f1-score: 0.75
accuracy: 0.76
