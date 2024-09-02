# Accident Report for Sanlam Insurance

**Author:** Charles Ndegwa
***

# Overview

The goal of the report is to enhance the underwriting process by leveraging data analytics to gain insights into the factors contributing to severe crashes. The focus is on predicting the likelihood of a crash resulting in "INJURY AND / OR TOW DUE TO CRASH" versus "NO INJURY / DRIVE AWAY." This prediction will enable Sanlam Insurance to more accurately assess risk and make informed decisions regarding insurance pricing, ultimately reducing claims costs and increasing profitability.

To achieve this, data from historical accident reports is analyzed, with a focus on features like weather conditions, lighting, road defects, and time factors such as the day of the week and month. By using various machine learning models, including Logistic Regression and Decision Tree Classifiers, the project evaluates the impact of different data preprocessing techniques, such as scaling and encoding, on model performance. The goal is to identify the b
est approach for predicting crash severity, thereby providing actionable insights that can improve risk assessment and policy pricing strategies.

# Business Problem

Sanlam Insurance faces significant challenges in accurately assessing the risk of accidents that result in injuries or severe vehicle damage, leading to higher claims costs. The traditional underwriting process may not fully account for the myriad factors that contribute to crash severity, potentially leading to suboptimal pricing strategies and increased financial risk.

To address this pain point, the project explores key questions related to the factors influencing crash outcomes. By understanding these factors through data analysis, Sanlam Insurance can refine its underwriting models, improve risk predictions, and ultimately reduce the frequency and cost of claims. These improvements are crucial for maintaining a competitive edge in the insurance market and ensuring long-term profitability.

The output shoud be able to draw the conclusion that, following the stipulated parameters for a accident to occur, the type of accident / crash should fall either injured or not injured, and a suitable critea can be selected by the company to state the renumuration from claims that are in those categories
***

# Methodology

The project wasa clasiffier model where data from the [Chicago Data Portal](https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if/about_data) was analysed to predict crash / accident type. Using the CRISP-DM framework the Data Understanding steps were:

+ Importing Libraries and Data
+ Label Encode target Features
+ Split the Data
+ Independent features selection
+ Exploratory Data Analysis (EDA)
  1. Handle Missing Values 
  2. Univariate Analysis
     + Target Variable Analysis
     + Independent Variable Analysis
       + Numerical features
        - Steps taken for numerical data
        - Encoding Numerical features
      - Categorical features
        - Steps taken for categorical data
        - Encoding Categorical features    
  3. Bivariate Analysis
    + Numerical Features
    + Categorical features
+ Data Modelling
  1. Pipeline
  2. Baseline Model - Logistic Regression
  3. Visualize results
  4. Decision Tree
  5. Visualize results
+ Evaluation 
  - Visualize Results 
  - Logistic Regression Evaluation
  - Decision Tree Evaluation
+ Conclusions
+ Recommendations
+ Next Steps

# Results

## Target feature encoded

CRASH_TYPE identified as the target variable. 
using `LabelEncoder`, the column was transformed 
the unique values in the columns were: 
**'INJURY AND / OR TOW DUE TO CRASH'** encoded as `0`
**'NO INJURY / DRIVE AWAY',** encoded as `1`

No null values, although the class has high imbalance

## Univariate Analysis

1. Target Variable Analysis

  ![image](https://github.com/user-attachments/assets/6f48cdcd-6c23-4f2a-8f6e-6dfe78ea4645)
  
2. Independent variable analysis
    The Independent features with most frequent value and unique value count:
  
    - WEATHER_CONDITION: Mode = CLEAR, Unique Values = 12
    - LIGHTING_CONDITION: Mode = DAYLIGHT, Unique Values = 6
    - ALIGNMENT: Mode = STRAIGHT AND LEVEL, Unique Values = 6
    - ROADWAY_SURFACE_COND: Mode = DRY, Unique Values = 7
    - ROAD_DEFECT: Mode = NO DEFECTS, Unique Values = 7
    - DAMAGE: Mode = OVER $1,500, Unique Values = 3
    - STREET_NO: Mode = 1600, Unique Values = 11559
    - STREET_NAME: Mode = WESTERN AVE, Unique Values = 1617
    - NUM_UNITS: Mode = 2, Unique Values = 17
    - CRASH_HOUR: Mode = 15, Unique Values = 24
    - CRASH_DAY_OF_WEEK: Mode = 6, Unique Values = 7
    - CRASH_MONTH: Mode = 7, Unique Values = 12`

  
2.1 Numerical features

  ![image](https://github.com/user-attachments/assets/bf511c3b-2763-4e99-8b97-1df6253b47ed)

2.2 Categorical Features

  ![image](https://github.com/user-attachments/assets/094adaa2-83fb-4b5d-97b2-7b9b70d82a07)

  ![image](https://github.com/user-attachments/assets/5e7bfb4a-23db-4423-a7fa-ef57551f2411)

  ![image](https://github.com/user-attachments/assets/fba8b265-c17d-4bb0-b33f-649434b96678)

  ![image](https://github.com/user-attachments/assets/e596ac90-e04d-4527-8061-52183b28f86e)

  ![image](https://github.com/user-attachments/assets/4cca3982-d3a0-443f-9d28-c9e7285653b8)

  ![image](https://github.com/user-attachments/assets/196c897a-fcca-4a69-bd0e-2e4753f4208d)

  ![image](https://github.com/user-attachments/assets/ffa0d4bf-f3f0-44b8-8e65-dc10308587de)



## Bivariate analysis

+ Numerical features

  ![image](https://github.com/user-attachments/assets/8b8ace96-c524-470c-8624-68ef3ff2d35a)

+ Categorical analysis

  
## Data Modeling 

+ Baseline Model

  ![image](https://github.com/user-attachments/assets/4673b005-3d3a-431d-bd34-a6ff2f3fe435)
  
+ Decision Tree

  ![image](https://github.com/user-attachments/assets/f86c5c7a-bb66-4387-b1f3-2ab0d991f566)
  
## Evaluation

  ![image](https://github.com/user-attachments/assets/998498f1-944d-433f-a2c7-ac489c05cc9b)

## Conclusions

### Overall Model Performance:

`Logistic Regression` slightly outperformed the `Decision Tree` in terms of accuracy, precision, and ROC-AUC. However, both models have relatively low recall, which indicates they miss a significant number of true positive cases (i.e., severe crashes).
The Decision Tree model has a lower overall performance compared to the Logistic Regression, especially in terms of precision and ROC-AUC. However, it had fewer false negatives than Logistic Regression, indicating it might slightly better capture severe crashes, although this comes at the cost of overall predictive accuracy.

### Trade-off Between Precision and Recall:

Both models have similar F1-scores (~0.67), suggesting a balance between precision and recall. However, the recall is notably low for both models, which is concerning given the context of the problem (i.e., identifying severe crashes is crucial for insurance underwriting).
The models' ability to correctly classify severe crashes is inadequate, as reflected by the high number of false negatives. This means that in many cases where a crash is severe, the models fail to predict it correctly, which could result in underestimating the risk for certain claims.

### Model Discriminative Power:

The ROC-AUC scores for both models (Logistic Regression: ~63.42%, Decision Tree: ~58.87%) suggest that neither model is particularly strong at distinguishing between severe and non-severe crashes. The discriminative power of the models is relatively modest, indicating that more sophisticated models or additional data/features might be needed to improve prediction performance


## Recommendations

**Feature Engineering**: Explore creating new features or transforming existing ones to capture more relevant information.

**Hyperparameter Tuning**: Fine-tune the hyperparameters of both models to optimize their performance.

**Ensemble Methods**: Combine multiple models (e.g., using random forests or gradient boosting) to potentially improve overall performance and reduce overfitting.

**Consider Other Models**: Experiment with other machine learning algorithms that might be better suited to your specific problem.

**Domain Expertise**: Leverage insights from insurance experts to identify additional factors that might influence crash severity.

**Cross-Validation**:Use cross-validation techniques to ensure that the model performance observed is generalizable and not due to specificities in the train-test split. This will give a better estimate of model performance across different data subsets.

## Next Steps
**Data Quality**: Ensure the quality and completeness of your data to avoid biases in your analysis. Using other datasets analysyze features that would increase model efficeincy

**Cost-Sensitive Learning**:Given the high cost of missing severe crashes, explore cost-sensitive learning approaches where the model penalizes false negatives more heavily. This could help improve the recall for severe crashes, which is critical for the business problem.





