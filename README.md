
# Employee Attrition Prediction 🔮🏃‍♂️

## 🙇‍♂️ Problem definition and motivation
Employee attrition, or the rate at which employees leave a company, is a significant concern for organizations due to the high costs associated with hiring and training new employees. According to recent data, the average cost per hire rose to $4,700 in 2023. For specialized positions such as cybersecurity, engineering, or nursing, the cost per hire can be even higher, reaching up to $28,329 for executive positions. These costs, combined with factors such as ultra-low unemployment rates and an aging workforce, highlight the importance of predicting and mitigating employee attrition. ([source](https://toggl.com/blog/cost-of-hiring-an-employee)).<br>
<br>
By developing a machine learning model that can predict employee attrition, organizations can take proactive measures to retain valuable talent and reduce turnover costs. This project aims to leverage machine learning techniques to analyze factors such as job satisfaction, salary, work-life balance, etc., and predict which employees are most likely to leave the company. By doing so, organizations can optimize their hiring and retention strategies, ultimately reducing the financial burden of employee turnover.


## 🗂️ Dataset
We used the publicly available dataset on employee attrition: the IBM HR Analytics Employee Attrition & Performance dataset, which contains information about employees' demographics, job role, satisfaction levels, etc.<br>
[Link](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data)

## ❔ Evaluation metrics
The performance of our machine learning model will be evaluated using metrics such as accuracy, precision, recall, and F1-score. <br> Given that the classes are imbalanced, we will use <strong>weighted f1-score</strong> as our main metric of evaluation.


## 🧐 Data Exploring
(1) Dataset has 1470 rows and  35 columns. <br>
(2) Plot histogram for each numeric variable/feature of the dataset.
<img src="assets/histograms.png" alt="Histograms Image" >

(3) Check for nulls & duplicates <strong>➺</strong> Total number of duplicates : 0, Total number of missing values : 0<br>
(4) Get the number of unique values for each column.<br>
(5) Explore categorical featuresׂ <strong>➺</strong> Total number of categorical variable : 8<br>
(6) Explore outliers <strong>➺</strong> Print number of outliers in each column.<br>
(7) Show Correlation Between the target variables and each feature
<img src="assets/correlation_matrix.png" alt="Correlation matrix Image" >
(8) Confusion matrix:<br>
<img src="assets/confusion_matrix.png" alt="Confusion matrix Image" >
(9) Check data imbalance.<br>
<img src="assets/data_balance.png" alt="Attrition Balance Image" >


## 🔧 Preprocessing

1- Drop ('EmployeeCount', 'Over18', 'StandardHours') columns as they were found to have constant values for all 1470 rows. Also, 'EmployeeNumber' is a unique identifier for all 1470 rows.<br>
2- Encode categorical variables.<br>
3- Remove MonthlyIncome,TotalWorkingYears, YearsInCurrentRole and YearsWithCurrManager taking a cutoff of 0.7 correlation coefficient. This will retain JobLevel and YearsAtCompany and remove possibility of multicollinearity from the features.<br>
4- Scale the date.<br>
5- Split The Data into training, validation, and testing sets.<br>
6- Resampling.<br>
<img src="assets/after_resampling.png" alt="After resampling Image" >

## Models

### Zero-R model (baseline model):

<img src="assets/zero-R-metrics.png" alt="Zero-R" >

### AdaBoost

**Performing grid search to get the best parameters:**

<img src="assets/AdaBoost/grid_search.png" alt="Grid Search" >

**Parameters of Best Model:**

<img src="assets/AdaBoost/best_model.png" alt="Best Model" >

**Evaluation metrics on Validation Set:**

<img src="assets/AdaBoost/evaluation_metrics.png" alt="evaluation_metrics" >

**Classification report for validation set:**

<img src="assets/AdaBoost/val_classification_report.png" alt="Classifiction report" >

**Confusion Matrix for validation set**

<img src="assets/AdaBoost/confusion_matrix.png" alt="Classifiction report" >

**Learning Curve (Scores)**

<img src="assets/AdaBoost/learning_curve_score.png" alt="Classifiction report" >

**Learning Curve (errors)**

<img src="assets/AdaBoost/learning_curve_error.png" alt="Classifiction report" >

**AdaBoost Learning Curve Insights:**

• The decreasing training score suggests that as more training examples are provided,
the model is exposed to a wider variety of instances and is learning to generalize
better.

• This is a positive sign as it indicates that the model is not memorizing the training data
but rather learning meaningful patterns.

• The increasing validation score indicates that the model's performance on unseen
data is improving as more training examples are provided.

• This suggests that the model is generalizing well to new instances and is not overfitting
to the training data.

• The small gap between the training and validation scores suggests that the model is
not suffering from significant overfitting.

• The fact that both scores are increasing with a small gap indicates that the model is
learning to generalize well to unseen data without excessively fitting to the training
data.

• The fact that both the training and validation scores are eventually increasing slowly
that the model's performance is stabilizing as more data is provided.

• This is a desirable outcome, indicating that additional data may not significantly
improve the model's performance further.

**Training & Validation errors vs number of learning estimators:**

<img src="assets/AdaBoost/errors_vs_number_of_estimators.png" alt="Classifiction report" >

• Boosting is often robust to overfitting.

• Test set error decreases even after training error is almost zero

**After Training over all the data (training + validation):**

<img src="assets/AdaBoost/test_metrics.png" alt="Classifiction report" >

**Classification Report for Test Set:**

<img src="assets/AdaBoost/test_classification_report.png" alt="Classifiction report" >

**Confusion Matrix for Testset:**

<img src="assets/AdaBoost/test_confusion_matrix.png" alt="Classifiction report" >
