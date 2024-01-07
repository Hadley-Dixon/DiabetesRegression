# Project Description
This project is to analyze a dataset, from start to finish, based on the multiple linear regression model. Students can discuss with each other to get a better understanding of the project, but submitted work must be done on an individual level.

## Data Description
The data “diabetes.txt” contains 16 variables on 366 subjects who were interviewed in a study to understand the prevalence of obesity, diabetes, and other cardiovascular risk factors in central Virginia for African Americans. We will consider building regression models with glyhb as the response variable, as Glycosolated Hemoglobin levels greater than 70 is often taken as a positive diagnosis of diabetes. The goal is to find the “best” model for explaining the factors which are predictive of diabetes diagnosis.

## Data Analysis
### Data exploration and data splitting
1. Among all the variables, which are quantitative variables? Which are qualita- tive variables? Draw histogram for each quantitative variable and comment on its distribution. Draw pie chart for each qualitative variable and comment on how its classes are distributed. Draw scatterplot matrix and obtain the pairwise correlation matrix for all quantitative variables in the data. Comment on their relationships.

2. Regress glybh on all predictor variables (Model 1). Draw the diagnostic plots of the model and comment.

3. You want to check whether any transformation on the response variable is needed. You use the function ‘boxcox’ to help you make the decision. State the transformation you decide to use. In the following, we denote the transformed response variable to be glyhb∗. Regress glyhb∗ on all predictor variables (Model 2). Draw the diagnostic plots of this model and comment. Apply boxcox again on Model 2; what do you find?

4. Set the seed to “372” and randomly split data into two parts: a training data set (70%) and a test data set (30%).

### Selection of first-order effects
We now consider subsets selection from the pool of all first-order effects of the 15 predictors. glyhb* is used as the response variable for the following problems.

5. Fit a model with all first-order effects (Model 3). How many regression coefficients are there in this model? What is the MSE from Model 3?

6. Consider best subsets selection using the R function regsubsets() from the leaps library with Model 3 as the full model. Return the top 1 best subset of all subset sizes (i.e., number of X variables) up to 16 (because frame has 3 levels). Compute SSEp , Rp2, Ra2,p, Cp, AICp, and BICp for each of models, as well as the intercept-only model. Identify the best model according to each criterion. For the best model according to Cp, what do you observe about its Cp value? Do you have a possible explanation for it? (Note: for the intercept-only model, you may have to calculate some statistics by hand. For this purpose, you can use the following conventions (which ignore extraneous constants) to compare with the leaps package: AIC = n log(SSE) + 2p, BIC = n log(SSE) + p log(n)).

7. Denote the best models according to AIC, BIC, and adjusted R2 as Models 3.1, 3.2, and 3.3, respec- tively. Specify which predictors are included in each. It is possible that some of the three models are the same. We will examine these later on.

### Selection of first-order and interactions effects.
We now consider subset selection from the pool of first-order effects and the 2-way interactions between the 15 predictors.

8. Fit a model with all first-order and 2-way interaction effects (Model 4). How many regression coeffi- cients are there in this model? What is the MSE from this model? Do you have any concern about the fit of this model? If yes, why?

9. Apply ridge regression using glmnet. Consider (at least) the penalty parameters λ = 0.01, 0.1, 1, 10, 100. Use cross validation to select the best value of λ. What is the model being selected with this λ value? Name this model Model 4.1. How many predictors does it contain?

10. Apply LASSO regression using glmnet. Consider (at least) the penalty parameters λ = 0.01, 0.1, 1, 10, 100. Use cross validation to select the best value of λ. Which predictors are included in the model being selected with this λ value? Recall that if there are interactions selected by LASSO, then we must also include their first-order effects. Name the model fit on the variables selected by LASSO and their corresponding first-order effects Model 4.2. How many predictors does it contain? What are the predictors?

11. Discuss the difference in methodologies behind ridge and LASSO regression. Why do they result in such different models?

### Model validation.
We now consider validation of the models (Model 3.1, Model 3.2, Model 3.3, Models 4.1, Models 4.2) you selected in the previous studies.

12. Internal evaluation. We use PRESS for this purpose. Calculate PRESS for each of these models. Comment. (Note: you may have to write a function to carry out the LOOCV process in order to calculate PRESS for the ridge model.)
13. External evaluation using the test set. For each of these models (Model 3.1, Model 3.2, Model 3.3, Model 4.1, Model4.2), calculate the mean squared prediction error (MSPE), i.e., you use the model to predict the 110 observations in the test set and calculate the averaged squared prediction error. How do these MSPEs compare with the respective PRESS/n (here n is the sample size of the training data, i.e., 256). Which model has the smallest MSPE?
14. Based on both internal and external validation, which model you would choose as the final model? Fit the final model using the entire data set (training and validation combined) (Model 5). Write down the fitted regression function and report the R summary(). Give a complete interpretation of your model in terms of the real life context of the problem.
