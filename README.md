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

Total Calls Distribution by Churn Status

![alt text](image-1.png)

Conclusion

**Non-Churned Users:**

The distribution of total calls for users who did not churn (churn = False) is symmetric and follows a normal distribution centered around 300 calls.

The spread of calls is quite wide, ranging from about 200 to 400 calls.

**Churned Users:**

For users who churned (churn = True), the distribution is also symmetric but with a lower center around 250 calls.

The distribution is narrower, suggesting that churned users tend to have fewer total calls compared to non-churned users.

International plan vs churn

![alt text](image-2.png)

Conclusion :

Customers without an international plan are much more likely to stay (not churn) compared to those with an international plan. Additionally, the proportion of customers who churn is relatively higher among those with an international plan compared to those without one.

Features Correlations with Churn

![alt text](image-3.png)

Distribution of Area Code Feature

![alt text](image-4.png)

* Half of the customers have the area code 415. 
* One fourth of customers have the area code 510 and another fourth have the area code 408.

Correlation Heatmap for Numeric Features

![alt text](image-5.png)

**Positive Correlations**: Features like customer service calls, total day minutes, and total day charge show a positive correlation with churn, indicating that higher usage in these areas is associated with a higher likelihood of customer churn.

**Negative Correlations**: Features such as number vmail messages and total intl calls show a negative correlation with churn, suggesting that higher usage in these areas might reduce the likelihood of churn.

**Weak or Negligible Correlations**: Several features like total night calls and account length have little to no correlation with churn, indicating minimal influence on the likelihood of a customer churning.


### Insights
Average Values of Numerical Features for Churned Users

The following table represents the average (mean) values of numerical features for users who have churned:

- **Account Length**: The average length of time that churned users had their accounts is about **102.66** days.
- **Area Code**: The average area code for churned users is **437.82**. (Note: Area codes are categorical, so this value is less meaningful).
- **Number of Voicemail Messages**: On average, churned users had about **5.12** voicemail messages.
- **Total Day Minutes**: Churned users spent an average of **206.91** minutes on daytime calls.
- **Total Day Calls**: The average number of daytime calls made by churned users is **101.34**.
- **Total Day Charge**: Churned users were charged an average of **$35.18** for daytime calls.
- **Total Evening Minutes**: On average, churned users spent **212.41** minutes on evening calls.
- **Total Evening Calls**: The average number of evening calls made by churned users is **100.56**.
- **Total Evening Charge**: Churned users were charged an average of **$18.05** for evening calls.
- **Total Night Minutes**: The average night minutes for churned users is **205.23** minutes.
- **Total Night Calls**: Churned users made an average of **100.40** night calls.
- **Total Night Charge**: Churned users were charged an average of **$9.24** for night calls.
- **Total International Minutes**: Churned users spent an average of **10.70** minutes on international calls.
- **Total International Calls**: The average number of international calls made by churned users is **4.16**.
- **Total International Charge**: Churned users were charged an average of **$2.89** for international calls.
- **Customer Service Calls**: On average, churned users made **2.23** calls to customer service.

This summary provides insight into the usage patterns and characteristics of customers who decided to leave the service.

## Feature Engineering
Feature Reduction with Feature Importances

By selecting the most important features, we reduce the dimensionality of the dataset. This will lead to simpler models that are potentially more generalizable, and also reduces the risk of overfitting.

## Evaluating and Comparing the different  Models


# Model Performance Comparison

| Model                                    | Confusion Matrix              | Precision (Class 0) | Recall (Class 0) | F1-Score (Class 0) | Precision (Class 1) | Recall (Class 1) | F1-Score (Class 1) | Accuracy | Macro Avg F1 | Weighted Avg F1 |
|------------------------------------------|-------------------------------|---------------------|------------------|--------------------|---------------------|------------------|--------------------|----------|--------------|-----------------|
| **Decision Tree - No Scaling, No SMOTE** | `[[717, 28], [19, 70]]`       | 0.974               | 0.962            | 0.968              | 0.714               | 0.787            | 0.749              | 0.944    | 0.858        | 0.945           |
| **Logistic Regression - With Scaling, No SMOTE** | `[[737, 8], [69, 20]]` | 0.914               | 0.989            | 0.950              | 0.714               | 0.225            | 0.342              | 0.908    | 0.646        | 0.885           |
| **Decision Tree - No Scaling, With SMOTE** | `[[668, 77], [17, 72]]` | 0.975               | 0.897            | 0.934              | 0.483               | 0.809            | 0.605              | 0.887    | 0.770        | 0.899           |
| **Logistic Regression - With Scaling, With SMOTE** | `[[719, 26], [54, 35]]` | 0.930               | 0.965            | 0.947              | 0.574               | 0.393            | 0.467              | 0.904    | 0.707        | 0.896           |
| **Decision Tree - Reduced Features, With SMOTE** | `[[641, 104], [19, 70]]` | 0.971               | 0.860            | 0.912              | 0.402               | 0.787            | 0.532              | 0.853    | 0.722        | 0.872           |
| **Logistic Regression - Reduced Features, With SMOTE** | `[[589, 156], [24, 65]]` | 0.961               | 0.791            | 0.867              | 0.294               | 0.730            | 0.419              | 0.784    | 0.643        | 0.820           |




### Comparison of ROC Curves for Different Models

![alt text](image-6.png)


### Model Accuracy Comparison

![alt text](image-7.png)



**Conclusion**: 

# Summary of the Results

## 1. Decision Tree - No Scaling, No SMOTE
- **Accuracy**: 94.36%
- **Precision**: 71.43%
- **Recall**: 78.65%
- **Analysis**: 
  - This model achieved the highest accuracy with a good balance between precision and recall.
  - It effectively predicts churn without needing any preprocessing.
  - However, it may favor the majority class (non-churners), which can lead to fewer detected churn cases.

## 2. Logistic Regression - With Scaling, No SMOTE
- **Accuracy**: 90.77%
- **Precision**: 71.43%
- **Recall**: 22.47%
- **Analysis**:
  - This model shows high accuracy and excellent precision but suffers from low recall.
  - It misses many potential churners, making it less suitable for identifying at-risk customers.

## 3. Decision Tree - No Scaling, With SMOTE
- **Accuracy**: 88.73%
- **Precision**: 48.32%
- **Recall**: 80.90%
- **Analysis**:
  - Improved recall at the cost of lower precision.
  - This model is better at catching more churners, even if it introduces more false positives.
  - Suitable for broad retention strategies where catching all possible churners is crucial.

## 4. Logistic Regression - With Scaling, With SMOTE
- **Accuracy**: 90.41%
- **Precision**: 57.38%
- **Recall**: 39.33%
- **Analysis**:
  - Offers a balanced performance with decent overall accuracy.
  - This model provides a middle ground between precision and recall.

## 5. Decision Tree - Reduced Features, With SMOTE
- **Accuracy**: 85.25%
- **Precision**: 40.23%
- **Recall**: 78.65%
- **Analysis**:
  - Moderate accuracy with high recall.
  - The reduced feature set simplifies the model but slightly reduces its effectiveness.

## 6. Logistic Regression - Reduced Features, With SMOTE
- **Accuracy**: 78.42%
- **Precision**: 29.41%
- **Recall**: 73.03%
- **Analysis**:
  - This model has the lowest performance, with lower precision and recall.
  - It is less effective for practical use compared to the other models.

## Conclusion and Final Model Selection

**Selected Model**: **Decision Tree - No Scaling, With SMOTE**

### Justification:
- **High Recall**: 
  - The selected model’s recall of 80.90% is crucial for identifying customers at risk of churn, aligning with the primary business goal.
- **Cost of False Positives vs. False Negatives**: 
  - Although precision is lower, the cost of false positives (offering incentives to customers who may not churn) might be lower than the cost of false negatives (missing customers who do churn).
- **Balanced Performance**:
  - The model’s balanced accuracy and F1 score make it an optimal choice.

### Business Implications

- **High Recall**: 
  - The model effectively identifies a majority of high-risk customers, allowing Syriatel to take preemptive action to retain them.
- **SMOTE Usefulness**: 
  - The application of SMOTE improves the model’s ability to detect churn by oversampling the minority class (churners).
- **Feature Importance**: 
  - The use of all features without reduction yields better predictive performance, implying that every bit of customer information contributes to understanding churn risk.

### Future Work:
This model can be used to develop targeted retention strategies, such as personalized offers or customer engagement programs, to minimize churn and maximize customer loyalty.










