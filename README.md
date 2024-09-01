# SyriaTel Customer Churn Prediction

## Overview

Customer churn, where customers stop using Syriatel's services, is a significant issue, with the telecom industry facing average churn rates between 30% to 35%. Retaining existing customers is more cost-effective than acquiring new ones, making churn prediction crucial for sustaining business growth. This project aims to equip Syriatel with a robust predictive model to identify high-risk customers and tailor retention strategies accordingly.

Stakeholders:

Syriatel Management: To strategize and implement customer retention programs.

Customer Service Teams: To identify and engage with high-risk customers effectively.

Data Analysts: To continuously monitor and refine the model for better accuracy.

**Author**: Geoffrey Mwangi

## Dataset Overview

### Data Understanding

The dataset utilized in this project originates from Syriatel, containing detailed information about the company's customers. Each record corresponds to a unique customer, with attributes that provide insights into their interaction with Syriatel's services. These attributes include demographic information, service usage patterns, and customer engagement metrics, all of which are crucial for understanding and predicting customer churn.

**Data Source and Suitability:**
The dataset is well-suited for the objective of predicting customer churn, as it includes both behavioral and service-related features that are likely to influence a customer's decision to terminate their contract. By analyzing these features, the model can identify patterns and correlations that contribute to churn, enabling targeted retention strategies.

**Dataset Size and Descriptive Statistics:**
- The dataset includes 3333 rows and 21 columns, representing a substantial amount of data for robust analysis.
- **Key Features and Descriptive Statistics:**
  - **State:** The state where the customer resides. This categorical variable can help identify geographic patterns in churn.
  - **Account Length:** The number of days the customer has had this account. Longer account durations might correlate with customer loyalty.
  - **Area Code:** The area code associated with the customer's phone number. This categorical variable could influence service usage patterns.
  - **Phone Number:** The customer's phone number. This feature is excluded from the analysis as it is not relevant for predicting churn.
  - **International Plan:** Indicates whether the customer has subscribed to an international calling plan (binary: True/False). This feature might impact customer satisfaction and churn rates.
  - **Voice Mail Plan:** Indicates whether the customer has subscribed to a voicemail plan (binary: True/False). This feature could also influence customer satisfaction and churn.
  - **Number Vmail Messages:** The number of voicemail messages the customer has received. This numerical variable might indicate how much the customer relies on voicemail services.
  - **Total Day Minutes:** The total number of minutes the customer has spent on calls during the day. Higher usage could be an indicator of engagement with the service.
  - **Total Day Calls:** The total number of calls the customer has made during the day. This metric, like total day minutes, provides insight into customer engagement.
  - **Total Day Charge:** The total charges incurred by the customer for daytime calls. This feature is directly related to revenue and could affect satisfaction.
  - **Total Eve Minutes:** The total number of minutes the customer has spent on calls during the evening. Evening usage patterns might differ from daytime patterns and affect churn.
  - **Total Eve Calls:** The total number of calls the customer has made during the evening. Like total eve minutes, this provides additional insight into customer behavior.
  - **Total Eve Charge:** The total charges incurred by the customer for evening calls. This feature, like total day charge, is related to revenue and customer satisfaction.
  - **Total Night Minutes:** The total number of minutes the customer has spent on calls during the night. Nighttime usage might reflect different customer needs or behaviors.
  - **Total Night Calls:** The total number of calls the customer has made during the night. This metric, together with total night minutes, provides a complete picture of the customer’s usage patterns.
  - **Total Night Charge:** The total charges incurred by the customer for nighttime calls. This is another revenue-related feature that could influence satisfaction and churn.
  - **Total Intl Minutes:** The total number of minutes the customer has spent on international calls. This metric could be particularly relevant for customers with an international plan.
  - **Total Intl Calls:** The total number of international calls the customer has made. This could indicate how valuable the international plan is to the customer.
  - **Total Intl Charge:** The total charges incurred by the customer for international calls. This feature might significantly influence churn, especially for international callers.
  - **Customer Service Calls:** The number of times the customer has called customer service. High values might indicate dissatisfaction and be a strong predictor of churn.
  - **Churn:** The target variable, indicating whether the customer has terminated the contract (binary: True/False).

**Feature Relevance:**
Each feature included in the dataset has been selected based on its potential relevance to customer churn. For instance, service usage patterns (e.g., total minutes and charges) and customer service interactions are directly linked to customer satisfaction, which is a strong predictor of churn. The inclusion of these features allows the model to capture a comprehensive view of customer behavior.

**Data Limitations:**
- **Lack of Demographic Data:** While the dataset includes the state and area code, more granular demographic data such as age, income, or occupation could provide deeper insights into churn behavior.
- **Potential Class Imbalance:** The dataset may have an imbalance between the number of churned and non-churned customers, which could impact model performance and necessitate techniques like SMOTE (Synthetic Minority Over-sampling Technique).
- **Temporal Aspects:** The dataset does not include time-based variables that could reveal trends or shifts in customer behavior over time, limiting the ability to detect seasonality or changes in churn patterns.

These limitations, while significant, do not outweigh the strengths of the dataset. The comprehensive nature of the included features still provides a solid foundation for building effective predictive models aimed at reducing customer churn for Syriatel.

## Data Preprocessing

Data Cleaning

In this section, we prepare the data for exploratory data analysis (EDA) and modeling. The following checks are performed:

- **Duplicated Rows**: Identifying and removing any duplicate entries.
- **Missing Values**: Detecting and addressing any gaps in the data.
- **Irrelevant Columns**: Removing columns that do not contribute to the analysis.

### Feature Types

* This step seperates all of the useful features in the dataset so that they can be analyzed accordingly ahead of modeling.  

#### Continuous Features:
* account length
* number vmail messages
* total day minutes
* total day calls
* total day charge
* total eve minutes
* total eve calls
* total eve charge
* total night minutes 
* total night calls
* total night charge
* total intl minutes
* total intl charge
* customer service calls

#### Categorical Features:
* state
* area code
* international plan
* voicemail plan

### Encoding Categorical Features

Categorical features were encoded using `LabelEncoder` and `OneHotEncoder` to convert them into a format suitable for machine learning models. This step was crucial for ensuring that the categorical data could be effectively used in the models.

### Data Normalization

Numerical features were normalized using `MinMaxScaler` to ensure that they were on the same scale, which is particularly important for models like SVM and K-Nearest Neighbors.

## Exploratory Data Analysis (EDA)

### Visualizations

### Churn vs Did not Churn representation

![alt text](image.png)



### Insights

- **Age and Tenure**: Older customers and those with longer tenure showed different churn rates.
- **Service Usage**: Features like `OnlineSecurity`, `TechSupport`, and `Contract` type were significant in determining churn.
- **Payment Method**: Certain payment methods showed higher churn rates.

## Feature Engineering


## Model Selection



### Training Set Results



**Conclusion**: 


## Feature Importance




## Conclusion and Recommendations

### Business Implications


### Future Work



