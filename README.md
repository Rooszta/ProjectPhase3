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
    1.Handle Missing Values 
+ Univariate Analysis
    1. Dependent Variable Analysis
    2. Independent Variable Analysis
        - Numerical features
            - Steps taken for numerical data
            - Encoding Numerical features
        - Categorical features
            - Steps taken for categorical data
            - Encoding Categorical features    
+ Bivariate Analysis
    1. Numerical Features
    2. Categorical features
+ Data Modelling
    1. Pipeline
    2. Baseline Model - Logistic Regression
        - Visualize results
    3. Decision Tree
        - Visualize results
    4. Evaluation 
        - Visualize Results 
        - Logistic Regression Evaluation
        - Decision Tree Evaluation

+ Conclusions
+ Recommendations
+ Next Steps

# Results
## Target feature encoded
    CRASH_TYPE identified as te tarhet variable. 
    using `LabelEncoder`, the column was transformed 
    the unique values in the columns were: 
            **'INJURY AND / OR TOW DUE TO CRASH'** encoded as `0`
            ** 'NO INJURY / DRIVE AWAY',** encoded as `1`
    No null values noticed, although the class had high imbalance

## Univariate Analysis
    + Target Variable Analysis

    


     + Independent variable analysis
        - Numerical features


        - Categorical Features


## Bivariate analysis
    + Numerical features


    + Categorical analysis

## Data Modeling 
    + Baseline Model

    + Decision Tree

## Evaluation
    + Vizualization

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





