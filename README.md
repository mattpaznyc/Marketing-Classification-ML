# Marketing Campaign Binary Classification Task

## Overview

Predict whether a consumer will respond to an offer from a sales campaign, with a binary target variable representing acceptance (1) or not-accepted (0).

## R Packages Used
- dplyr
- ggplot2
- caret
- pROC
- e1071
- RColorBrewer
- ROSE
- ggcorrplot
## Data
https://www.kaggle.com/datasets/ahsan81/superstore-marketing-campaign-dataset/data
### Dataset Overview
- A total of 2,208 observations in the dataset.
- In total, there are 22 columns in our dataset. Of these, approximately 86% are numeric (19 columns), and the remaining roughly 14% arecharacter columns (3 columns).
- Dataset comprises 21 features, including marital status, income, education, and various products sold at the store.
- Target variable is "Response," which indicates whether a customer accepted the offer from marketing campaigns in the last two years: 1 indicates that a customer accepted the offer in the previous campaigns, while 0 denotes that they did not accept it.
## Pre-Modeling
### Data Cleaning
- Filtered data to include only birth years greater than 1900, excluding outliers from this column.
- Identified outliers in the "Income" column: the row containing the maximum income value was removed
- Identified 182 duplicated rows and removed them but kept only the first occurrence of each unique row
- The prospective feature, Income, had 24 missing values as well, which only accounted for 1% of the dataset, so I ultimately dropped the missing data
### Feature Engineering 
- Applied feature transformation to 8 variables, including Marital Status, Education, and consumption of various products. Specifically, we reduced the number of categories in Marital Status and Education, while creating a new feature to capturethe total products sold for the remaining variables. 
- Combined the kids and teens at home variable, totaling the number of dependents in a new feature.
- Applied feature encoding to our 3 qualitative variables to convert them into a numerical format that machine learning algorithms can understand and process efficiently.
### Handling Class Imbalance
- Applied the oversampling method to the target variable, which increased the number of instances in the minority class (1) to balance it with the majority class (0). As a result, the minority class (1) increased by 239.58% after the oversampling method

## Models

Selected models appropriate for the binary classification task:
- Support Vector Machine (SVM)
- Logistic Regression
- Naive Bayes

## Results

### Confusion Matrix Summary
- **Logistic Regression**: performed reasonably well, with a relatively balanced number of true positives and true negatives. However, it had a higher number of false positives compared to false negatives.
- **Naive Bayes**: struggled more with false predictions, particularly false positives. It had a higher number of false positives and false negatives compared to the logistic regression model.
- **Support Vector Machine (SVM)**: demonstrated the best performance among the three models. It had the highest number of true positives and true negatives and the lowest number of false predictions overall.

### Accuracy
Comparing baseline, a majority classifier, to the complex models:

![Accuracy Comparison]

All of the complex models outperformed the baseline, suggesting that they were able to better capture the underlying patterns and nuances in the data. 

### ROC-AUC ANALYSIS

![ROC-AUC Viz]

Overall, the logistic regression and SVM models demonstrate strong performance, whereas the naïve bayes model displayed a moderate performance compared to the models with higher AUC scores.

### Precision
![Precision]

- In this project, I evaluated several models for classifying customer responses to marketing campaigns. The Support Vector Machine (SVM) model achieved the highest precision score of 0.85, correctly identifying likely responders 85% of the time.

## License

For this github repository, the License used is MIT License.
