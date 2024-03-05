---
layout: post
title:  "Calculating Prediction Intervals in Regression Using Python Statsmodels"
date:   2024-3-04 07:25:17 -0800
categories: jekyll update data
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Calculating_Prediction_Intervals_in_Regression_Using_Python_Statsmodels.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>


## Setting Up the Regression Model

For a regression model, we'll use the IQ and Size dataset, which can be accessed [online](https://online.stat.psu.edu/stat501/lesson/7/7.2). The initial steps involve loading the data, selecting relevant features, defining the response variable, and fitting a linear regression model.

```python
import statsmodels.api as sm
from statsmodels.formula.api import ols
import numpy as np
import pandas as pd

# Load the dataset
df = pd.read_csv('https://online.stat.psu.edu/onlinecourses/sites/stat501/files/data/iqsize.txt', sep='\t')

# Select relevant features and response variable
Xdf = df[['Brain', 'Height']]
ydf = df[['PIQ']]

# Define the regression formula
formula = 'PIQ ~ Brain + Height'

# Display the first few rows of the dataset
df.head()

# Extract the response variable and predictor variables as arrays
y = ydf.values
X = Xdf.values

# Add a constant term to the predictor variables
Xo = sm.add_constant(X)
Xdfo = sm.add_constant(Xdf)

# Get the number of observations (n) and predictor variables (k)
n, k = X.shape

# Set the significance level and calculate alpha
sl = 0.95
alpha = 1 - sl

# Fit the linear regression model
model = ols(formula, data=df).fit()
```

## 1. Manual Calculation with Formula

One way to calculate prediction intervals manually is by using the formulae:

$$\hat{\beta} = ({X}^\prime {X})^{-1} {X}^\prime {y}$$

$$\hat{y} = {x}^*\hat{\beta}={x}^*({X}'{X})^{-1}{X}'{y}$$

$$\hat{\sigma}_e^2 = \frac{1}{n-k-1}({y} - {X}\hat{\beta})'
  ({y} - {X}\hat{\beta})$$

$$\hat{y} \pm t_{\text{mult}} \hat{\sigma}_e \sqrt{1 + {x}^* ({X}^\prime {X})^{-1} ({x}^*)'}$$

This involves estimating the regression coefficients ($$\hat{\beta}$$), the predicted response ($$\hat{y}$$), and the standard error of the residuals ($$\hat{\sigma}_e$$). Using these values, we can calculate the lower and upper bounds of the prediction interval.

```python
# Manual Calculation
Xstar = {"Brain": 90, "Height": 70}
xstar = np.asarray([list(Xstar.values())])

Bhat = inv(Xo.T @ Xo) @ Xo.T @ y
MSE = (1 / (n - k - 1) * (y - Xo @ Bhat).T @ (y - Xo @ Bhat))[0, 0]
tmult = t.ppf(1 - alpha / 2, df=(n - k - 1))
ME = tmult * np.sqrt(MSE * (1 + xstar @ np.linalg.inv(Xo.T @ Xo) @ xstar.T))[0, 0]
yhat = (xstar @ Bhat)[0, 0]
lower_bound, upper_bound = yhat - ME, yhat + ME
```

## 2. Using `get_prediction` Method

The `statsmodels` library provides a convenient `get_prediction` method for calculating prediction intervals. This method encapsulates the manual steps, making it simpler for users.

```python
# Using get_prediction method
Xstar = {"Brain": 90, "Height": 70}
model.get_prediction(Xstar).summary_frame(alpha=alpha).obs_ci_lower[0], model.get_prediction(Xstar).summary_frame(alpha=0.05).obs_ci_upper[0]
```

This method directly returns the lower and upper bounds of the prediction interval for a given set of predictor variables.

## 3. Leveraging Model Attributes

Another approach is to extract relevant attributes directly from the fitted model, obtaining similar results as the `get_prediction` method.

```python
# Leveraging Model Attributes
Xstar = {"Brain": 90, "Height": 70}
xstar = np.asarray([list(Xstar.values())])

tmult = model.get_prediction(Xstar).dist.ppf(1 - alpha / 2, *model.get_prediction(Xstar).dist_args)
ME = tmult * np.sqrt(model.mse_resid * (1 + xstar @ model.normalized_cov_params.values @ xstar.T))[0, 0]
yhat = model.predict(Xstar)[0]
lower_bound, upper_bound = yhat - ME, yhat + ME
```

## Conclusion
Calculating prediction intervals in regression using `statsmodels` can be approached in multiple ways. Depending on your preference and specific requirements, you can choose the method that best suits your needs. The key is to strike a balance between accuracy and ease of implementation.