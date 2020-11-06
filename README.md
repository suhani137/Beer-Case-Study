# Beer-Case-Study
This case study has been solved as Regression problem with review/overall as the dependent variable.

1. Sentiment Analysis
This involves using the review/text column and classifying each review as positive, negative and neutral based on compound score. This variable will then be used for model building to predict overall review score.

2. Data Cleaning and Preprocessing
Out of the 18 variables, the following variables were dropped for model building because of having mostly missing values and with unique IDs: 'user/ageInSeconds','user/birthdayRaw','user/birthdayUnix','user/gender','user/profileName','review/timeUnix','index','beer/beerId','beer/brewerId','review/timeStruct'.
Out of 37500 rows, 10 rows with no review text were droppped.
Finally, taking beer/ABV, beer/name, beer/style, review/appearance, review/aroma, review/overall, review/palate, review/taste and sentiment as predictors and review/overall score as target variable with 37490 rows.

3. Feature Engineering
a) Feature Selection - Correlation Heatmap: Dropping review/taste due to multi-collinearity, correlation more than 0.6 with two variables
b) Feature Transformation - Dummies: Taking dummies for the 3 categorical variables (sentiment, beer style and beer name). This gives us 1790 predictors in total.
c) Feature Selection - p-values: From the 1790 independent variables created, choosing only those for prediction with p-values < 0.05, by running ordinary least squares regression. We are left with just 120 variables (including dummy coded and continous variables)
d) Feature Selection - Variable Importance: We further reduce the the number of independent variables by determining variable importance for both models. Decision Tree leaves us with only 14 variables for the final model and catboost leaves us with 4 out of 7 variables in final model.

4. Model Building
a) Decision Tree
b) CatBoost - Since the variables beer style and beer name contain multiple levels, CatBoost has been used. This does not need any label encoding and model can be built after the first step of feature selection (correlation heatmap)

5. Model Validation
a) Mean Squared Error
b) Mean Absolute Percentage Error
On the basis of MAPE, we can say that Decision Tree with 14 predictors is a better model as MAPE for decision tree is 10.81%, which is lower than CatBoost with 4 pedictors (21.17%).
