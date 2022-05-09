## Classification Project: 
Predicting Length of Hospital Stays

### Abstract

Accurately predicting the length of stay (LOS) of hospital inpatients might help administrators to optimally allocate resources when needed. As hospitals have confronted space and staffing limitations throughout the pandemic, estimating the duration of patients’ occupancy at the time of their arrival could help maximize hospital capacity during a caseload surge. Using data collected from the early stages of the COVID-19 outbreak, I compared several classification models to predict a short or long-term LOS based on patient data available at the initial intake, obtaining a final F1 score of 0.81.

### Design

The challenge to predict LOS for Covid-19 patients at several hospitals was initially presented as part of an Analytics Vidhya classification hackathon. I adapted the original multiclass problem into a binary classification problem, predicting outcomes of either short or long stays. Short stays are in the minority for this dataset, but the cost of failing to predict a long stay may be more significant than the cost associated with falsely predicting a long stay. With that assumption, I slightly prioritized recall (with long stays labeled as the positive outcome) over precision. 

### Data
The dataset consisted of over 300,000 records, including multiple visits for individual patients. I retained about 13 features describing the hospital location and type, ward information, severity of illness, the patient’s age, and a few other measures related to the initial intake. Short stays were defined as the smallest two time bins present in the target variable, which comprised 1-20 days.  This class only made up 32% of the data, while the longer stays ranged from 21-100 days.

### Algorithms
####	Feature engineering:
- Converted categorial features to dummy variables
- Combined and discarded a few dummy-coded features to reduce multicollinearity
- Added a feature for the patient’s number of previous visits	

####	ML models:
- Compared KNN, Logistic Regression, and Decision Tree classifiers
- Tuned Random Forest hyperparameters	
- Compared the optimal Random Forest model with XGBoost on holdout data	
- Compared results with and without oversampling the minority label
- I mostly relied on f1 scoring, but would add ROC curves in future work
	
### Tools
Throughout this project, I mainly used Python and scikit-learn.

### References

https://www.medrxiv.org/content/10.1101/2020.04.30.20084780v3.full-text

https://www.kaggle.com/arashnic/covid19-hospital-treatment

https://datahack.analyticsvidhya.com/contest/janatahack-healthcare-analytics-ii/
