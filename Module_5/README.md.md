# Linear Models
- Most basic statistical model.
- Analyzes the relationship between a response variable and a set of explanatory variables.
- Predict unknown values
  
## Simple Linear Regression
$y = ax + b$
![[./LinearRegression.png]]
$a=ybar - b*xbar$

```R
lm(formula, data) #generates a model using ordinary least squares for the given formula
```

|Symbol|Usage|
|-|-|
|~|Separates response variable from explanatory variable|
|+|Separates predictor variables|
|:|Represents interaction between predictor variables|
| * |Shortcut to represent all possible interactions|
| ^ n| Represents Interaction upto degree n |
|.| Placeholder representing all other variables |
| - | Used to remove a predictor variable from the equation |
|-1| Forces the line through the origin x = 0 |



## Polynomial Regression
- The relationship is modelled as an $nth$ order polynomial
## Multiple Linear
- The response variable is predicted from two or more explanatory variables
## Multilevel
- Predicting the response variable from data that have a hierarchical structure
## Multivariate
- Predicting the value of multiple response variables
## Logistic Regression
- Prediction of a categorical response from the given explanatory variables
## Poisson Regression
- Prediction of the response variable from the counts for one or more explanatory variables
## Cox Proportional Hazards & Time Series
- Prediction of time
  
# Regression Analysis Types

| Type | Definition | 
|-|-|
|Nonlinear | Prediction of the response variable whose values in non linear|
|Nonparametric | The form of the model is derived from the data and not mentioned a priori|
|Robust | The values of response variable in this approach is resistant to the effect of influential observations|

