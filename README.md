# Capstone-Project
Capstone Project

### ML Models to Predict Product Type, Weight and Power

Michael King

#### Executive summary
Power information has not been centrally collected and managed and therefore many products have no data.  The goal is to develop a model to estimate typical power for our products where data is unavailable: There will be 3 parts to this project:

1. Using classification models, predict which class products belong to based on BOM information and other categorical data. Products can be considered mechanical, modular or power requiring products.
2. Based on the predicted classes and available data, use a supervised learning module to estimate product weight, as it’s related to product power.
3. For products identified as power requiring, use the new  data set to create a new supervised learning module to estimate the power for products with no power data.

#### Rationale
The energy my companies products consume is its largest source of greenhouse gas emissions. By better estimating the power from the products with no data we can more accurately estimate the annual total emissions from the sale of our products.

#### Research Question
What is the best machine learning algorthims to predict which class a product belongs to, what is the weight of the product and if it's a product that uses power, what is the estimated typical power.

#### Data Sources
Source: Internal systems
Rows/columns: 41,279/25
Number of numerical/categorical columns: 25/6
Target column: product type/weight/power

#### Methodology
To classify the products I will evaluate KNN, decision trees, logistic regression, SVM.
To predict  missing data I will use Linear Regression and evaluate L1, L2 regularization and KNN

For the initial model for Module 20, I will use a KNN classifier to predict the product type of the products.

#### Results

EDA
There are 25 columns in the data frame, 4 objects and the remaining are int64.
<img width="418" height="366" alt="image" src="https://github.com/user-attachments/assets/f706bbd9-3a75-49ca-b4d5-ca744878ea43" />

There is no missing data, all data is a value or a 0. There is also no duplicated values.
<img width="414" height="306" alt="image" src="https://github.com/user-attachments/assets/fe5de01a-b4c6-4c77-a2b7-c3ebb5602bbd" />

Initial count of the data shows most of the products are classified as mechanical, followed by modular, followed by power.
<img width="413" height="310" alt="image" src="https://github.com/user-attachments/assets/c57ae49a-bf01-4c2c-b094-f100155826e0" />

I selected a few sample features to check to see how skewed the data was. Based on the analysis, there are a lot of products that have smaller values and a longer tail of products with higher values, but fewer of them.
<img width="438" height="300" alt="image" src="https://github.com/user-attachments/assets/cda85cf8-c5ac-4422-9c7a-a3ebfd13c2eb" />

I corrected for the skewness by using a log function which created a more balanced data set which should help with optimizing a model
<img width="426" height="303" alt="image" src="https://github.com/user-attachments/assets/fb5bb479-dbcb-4aff-b248-7ab75df84a46" />

The initial target variable is "type", and base on the correlation matrix is shown to be correlated with the following:

- 28-Printed Circuit Board
- 29_27-Connector-Header_Terminal
- IC
- elec
- total_comp
<img width="754" height="673" alt="image" src="https://github.com/user-attachments/assets/f51131c6-d78a-4f68-b676-2bcdd25aea38" />

The pair plot analysis shows that there is strong linear correlation between the following:

- total_comp vs IC
- total_comp vs elec
- IC vs elec
<img width="586" height="565" alt="image" src="https://github.com/user-attachments/assets/d5237cd7-f1ec-4b55-85a4-976a083d6525" />

Initial Model

The initial model to classify the products was built using a KNN classifier with neighbors = 5. The model had an accuracy of 92%

<img width="480" height="445" alt="image" src="https://github.com/user-attachments/assets/131d5fd6-5cbe-4d11-91c7-8cc3ce75d8b0" />

In this model, the most important metric is the f1-score, which is the weighted average of precision and recall. For this model the f1-score is 95%.

The training accuracy also went from 95% to 92% on the test data which suggests that the model is not overfitting.

#### Next steps
The next steps are as follows:

- Complete model and perform grid search using all models, KNN, Logistic Regression, SVC and Decision Tree.
- Use best model to predict missing classes.
- Join data with predicted classes with data that is already classified.
- Split data that is missing weight with data that has a weight estimate.
- Perform modeling using linear regression with Lasso, Ridge and KNN.
- Repeat same process to estimate power data.

#### Outline of project

- [Link to notebook 1]()
