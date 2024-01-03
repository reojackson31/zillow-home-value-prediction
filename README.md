# Zillow's Home Value Prediction ([Zestimate](https://www.zillow.com/z/zestimate/))
##### *- Project for MMA INSY662 - Data Mining & Visualization, McGill University*

## Problem Statement
This project focuses on predicting Zillow's Zestimate Log Error. The goal is to find potential inaccuracies in Zillow's home valuation model, by identifying the features that contribute to higher prediction errors. Using this model, Zillow can identify features that need to be prioritized during data collection to improve the accuracy of their home valuation model, thereby improving the predictions and increasing the probability of the property being sold on Zillow. 

## Data Description
Data Source - The dataset used for this project is taken from a competition hosted by Zillow on [Kaggle](https://www.kaggle.com/competitions/zillow-prize-1/overview)

The columns in the dataset can be grouped into the following categories:
| Category           | Description                                                                                                                                                                     |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Identifiers     | **parcelid**: Unique identifier for each property.                                                                                                                                      |
| 2. Date and Time   | **transactiondate**: Date of the property transaction.                                                                                                                                  |
| 3. Target Variable | **logerror**: The log error between Zillow's Zestimate and the actual sale price.                                                                                                       |
| 4. Property Features | **Physical Characteristics**: Features describing the physical attributes of the property like number of bathrooms, bedrooms, basement area, etc. (e.g., bathroomcnt, bedroomcnt, basementsqft). |
|                    | **Location and Area**: Geographic and area-related features (e.g., latitude, longitude, regionidcity, regionidcounty, regionidzip).                                                     |
|                    | **Tax-Related**: Information related to property taxation (e.g., taxvaluedollarcnt, landtaxvaluedollarcnt, taxamount, structuretaxvaluedollarcnt).                                     |
|                    | **Building Information**: Features related to the building's quality, class, and age (e.g., buildingqualitytypeid, buildingclasstypeid, yearbuilt).                                    |
|                    | **Additional Features**: Additional details about the property (e.g., airconditioningtypeid, heatingorsystemtypeid, pooltypeid).                                                        |



## Model Building Steps
- **Exploratory Data Analysis:** Analysis of target and predictor variables, including correlation analysis.
- **Data Preprocessing:** Handling missing data using methods like KNN, regression, and mean/mode imputation, feature engineering, and outlier removal.
- **Feature Selection:** Utilizing techniques like LASSO Regression and Random Forest for selecting significant predictors.

## Model Selection
| Model            | Working                                                                 | Pros                                         | Cons                                        | MSE     |
|------------------|-------------------------------------------------------------------------|----------------------------------------------|---------------------------------------------|---------|
| Linear Regression| Simple linear approach to modelling the relationship between a dependent variable and one or more independent variables.| Easy to implement and interpret.             | Can be prone to overfitting with many features.| 0.07438 |
| Ridge Regression | Extends linear regression by adding a penalty term to prevent overfitting.| Reduces model complexity and overfitting.    | May introduce bias in estimates.             | 0.02058 |
| LASSO Regression | Similar to Ridge but can set some coefficients to zero, effectively selecting features.| Performs feature selection.                | Can struggle with complex relationships.     | 0.02063 |
| KNN              | Predicts the value for a new point based on the 'k' nearest neighbors.  | Simple and effective for nonlinear data.     | Computationally intensive with large datasets.| 0.0214  |
| Decision Tree    | Creates a model that predicts the value by learning simple decision rules from features.| Easy to understand and visualize.          | Can easily overfit data.                     | 0.02063 |
| Random Forest    | Ensemble of decision trees, improving predictive quality and preventing overfitting.| Robust to overfitting and works well with non-linear data.| More complex and resource-intensive.       | 0.02041 |
| Gradient Boosting   | Boosting type ensemble learning that builds one tree at a time where each new tree helps to correct errors made by previous ones.| Often provides high accuracy.               | Can overfit and sensitive to noisy data.      | 0.02053 |
| ANN              | Artificial Neural Networks, capable of learning complex patterns using layers of neurons.| Highly flexible and powerful.               | Requires large data and is computationally intensive.| 0.023   |

Random Forest model was selected since it gave the lowest MSE with training data.

## Code Files
- Exploratory-Data-Analysis.ipynb - Jupyter notebook with results from Exploratory Data Analysis.
- EDA-Dashboard.html - HTML file for interactive dashboard for EDA.
- Model-Selection.ipynb - Jupyter notebook with data preprocessing and model building and selection steps.
