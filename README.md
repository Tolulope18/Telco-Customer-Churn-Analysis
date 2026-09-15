# Telco-Customer-Churn-Analysis
Analysis and prediction of customer churn using the IBM Telco Customer Churn dataset.

## Project Overview

Customer churn is an important problem for telecom companies because losing existing customers can have a direct impact on revenue.

In this project, I analysed customer data to understand the factors associated with churn and identify the types of customers who are more likely to leave.

I started by exploring the data and looking at churn across different customer groups. I then focused more closely on month-to-month customers because they had the highest churn rate. Finally, I built and compared classification models to see how well customer information could be used to predict churn.

## Business Problem

The main questions I wanted to answer were:

* Which customer characteristics are associated with higher churn?
* Which customer groups are more likely to leave?
* Can a model identify customers who are likely to churn?
* What does the model rely on when making its predictions?
* Which churners does the model fail to identify?

Missing a customer who eventually churns is more concerning in this case than incorrectly flagging a customer who stays. However, too many false positives would also mean that retention efforts are being spent on customers who may not actually be at risk.

## Dataset

The project uses the IBM Telco Customer Churn dataset.

The dataset contains 7,043 customers and 21 columns, including information about:

* Customer demographics
* Services
* Contract type
* Payment method
* Monthly and total charges
* Customer tenure
* Churn

## Analysis

I first explored the overall churn rate and then compared churn across different customer groups.

Some of the areas I looked at included:

* Contract type
* Tenure
* Number of services
* Internet service
* Add-on services
* Monthly charges

The analysis showed that month-to-month customers had the highest churn rate, so most of the deeper analysis was focused on this group.

I also created features such as `ServiceCount` and `AddOnServices` based on the services customers use.

## Key Findings

* Month-to-month customers have the highest churn rate.
* Newer customers are more likely to churn, and churn generally decreases as tenure increases.
* Fiber optic customers have a higher churn rate than DSL customers. Looking across tenure groups showed that tenure alone does not explain this difference.
* Among month-to-month customers, customers who churned had higher average monthly charges than customers who stayed.
* Having more add-on services did not automatically result in lower churn. The relationship between service count and churn is more complicated and depends on the type of services customers use.

## Modelling

I compared three classification models:

* Logistic Regression
* Random Forest
* XGBoost

Since missing a customer who churns was more concerning, recall was the main metric used when comparing the models, while precision and F1 score were also considered.

After comparing the models, I tuned the Logistic Regression model using GridSearchCV.

## Final Model

The final Logistic Regression model identified about **79% of the customers who actually churned**.

Its precision was about **51%**, meaning that a fair number of customers predicted to churn did not actually churn.

The model was therefore better at finding potential churners than at making every prediction correct. This was expected given the decision to place more importance on recall.

## Model Interpretation

I used three approaches to understand the model:

* Logistic Regression coefficients to understand the direction and strength of feature relationships.
* Permutation importance to see which original features had the biggest effect on model performance.
* SHAP to understand how features contributed to individual predictions.

Tenure, contract type, and internet service were among the features that showed the strongest influence.

## Error Analysis

I looked mainly at false negatives, customers who actually churned but were predicted to stay.

The model was much more likely to miss churners with longer tenure.

Among customers who actually churned, those correctly identified had an average tenure of about 12 months, while the customers missed by the model had an average tenure of about 32 months.

This suggests that the model is better at identifying the more obvious churn patterns among newer customers, but has more difficulty identifying customers who churn after staying with the company for longer.

## Limitations

There are some things this analysis cannot tell us.

The analysis shows relationships between variables and churn, but it cannot tell us that one variable directly causes customers to leave.

The dataset also does not contain some information that could help explain why customers churn, such as customer satisfaction, complaints, service quality, outages, or offers from competitors.

Some relationships could also be influenced by other variables that were not controlled for in every comparison.

Finally, the data is historical, so the patterns found here may not remain the same if customer behavior or the company's situation changes.

## Tools

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* XGBoost
* SHAP

## Project Notebook

The full analysis and modelling process can be found in the notebook in this repository.
