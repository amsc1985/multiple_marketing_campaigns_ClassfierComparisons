### Overview ###
In this practical application, our goal is to compare the performance of the classifiers specifically, K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines. Dataset related to marketing bank products over the telephone from a Portugese banking institution and is a collection of the results of multiple marketing campaigns. Our dataset comes from the UCI Machine Learning repository [link](https://archive.ics.uci.edu/ml/datasets/bank+marketing).  

### Business Objective ###
-  11% customer subscription rate was the baseline based on the 52,944 customers that were considered between May 2008 to Jun 2013. Objective is to maximize selling bank long term financial assets with effective marketing campaigns by making fewer contacts while retaining same or higher success of clients subscribing to the deposit.
- Due to the imbalanced data, the area under the ROC curve was used as a metric for comparing the different models. High AUC for ROC curve implies both high TPR and low FPR 
- All models were checking with Probabilites was another measure for evaluating model as it is a measure of the AUC
- Data Mining is used to identify the relationships between customer profile characteristics (predictors) and if they accepted the service (target). Logistic Regression, K Nearest Neighbor (KNN), Decision Trees, and Support Vector Machines (SVMs) are used for evaluation 

### Understanding the Data ### 
Original data comprised on 52,944 contacts made by the Portugese retail bank from May 2008 through June 2013. Additional data related to the clients social and economic influence features were gathered externally from the central bank of the Portugene Republic statistical website.
The data contains information from 17 different marketing campaigns, conducted by a Portugese bank. The campaign was conducted primarily by phone, to customers in Portugal. Data contains features on customer information. The target is to see if the customer signed up for the promoted service.

<img width="408" alt="DataFrame Overview" src="https://github.com/amsc1985/multiple_marketing_campaigns_ClassfierComparisons/assets/37163650/a13073e5-7925-4ceb-9e07-2a0eff3cc16a">
 
The dataframe comprised of 5 float64, 6 int64, and 10 object data types. 12 duplicated rows were dropped. The acceptance of the customer was changed into numeric datatype by changing categorical value of yes to 1 and no to 0

![Featured Based Customer Acceptance Rate Bar Charts](https://github.com/amsc1985/multiple_marketing_campaigns_ClassfierComparisons/assets/37163650/75be0853-97fa-4197-9278-319c6c244ec8)

While no missing values were found. A lot of unknown values were found. Data was prepared initially, by reducing features. I considered the following features: job, marital status, loan, education, default, housing, and age. Furthermore, the values over mean and below mean were grouped together. Mapped features can be looked up as the dataframe is modified for tracability. A preliminary correlation matric helped identify features for building the initial model for data mining.

![Numeric Data Correlation Plot ](https://github.com/amsc1985/multiple_marketing_campaigns_ClassfierComparisons/assets/37163650/e8d0b31b-aac0-46c6-bda8-750eb0967edf)


### Modeling ### 
Logistic regression, K nearest neighbor (KNN), decition tree classifier, and support vector machine (SVM) I tried four different classification models were used for analysis. For all simulations, an 80/20 test-train split, with training y feature stratified. For improved model a 5-fold cross-validation with increased features using Logistic regression was simulated.

<img width="412" alt="Model Summary" src="https://github.com/amsc1985/multiple_marketing_campaigns_ClassfierComparisons/assets/37163650/36ca06fe-cfdd-4461-a4a7-0246f45a6b7a">

Logistic Regression ran the fastest with an accuracy of 64%. Unbalanced data with 11% acceptance rate corresponding to 4369 customers, a Receiver Operating Characteristic (ROC) curve was also conssidered as a metric for sucess. 

![ROC Curve Summary](https://github.com/amsc1985/multiple_marketing_campaigns_ClassfierComparisons/assets/37163650/e9e9c4fc-0581-4f7b-8c0a-eac43e6f3984)


### Improving the Model ### 
Model Accuracy was improved by accounting for more features and performing One Hot Enconding (OHE) and Target Encoding (TE). Features with three or less values (marital, housing, loan, contact, and poutcome) were encoded with OHE, while the rest (job, education, month, day_of_week) used TE. Due to imbalance in dataset SMOTE was used to increase the minority class (1, 'yes'). Infact, it actually nearly doubled the acceptance. 


Logistic Regression was chosen because of initial highest accuracy and test score.A similar analysis can be performed based on KNN, DT and SVM but was not perfomred in this section.Particularly, a 5 foldf for each of the 6 candidates was performed totalling 30 fits. 
![Modified LR FA](https://github.com/amsc1985/multiple_marketing_campaigns_ClassfierComparisons/assets/37163650/2c3c6c99-9cad-43e1-bc46-66a063a8baf9)


Improved Model Summary: Upon increasing the attributes for regression consideration, the logistic regression model accuracy increased to 89% and a ROC-AUC value of 0.86. Economic variables having corrleation to the consumer purchasing power of the bank service. From Permutation importance, we can see importance arising from employee variation rate, euribor 3 month rate (euribor3m), and consumer price index.
Banks can segment customers based on categories as identified from the importance table eg. when to contact, how to contact, previous service acceptance, etc  

Future Consideration: Other consideration not present in the study (eg customer account balance, complaints, frequency of commuincation, etc) to the bank can assist in building a stronger model.
