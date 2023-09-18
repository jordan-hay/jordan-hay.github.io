---
layout: post
title:  "Predicting the Dependent Variable Using the Regression Model"
date:   2023-09-16 06:25:17 -0800
categories: jekyll update
---

In the realm of data analysis, unraveling intricate patterns and relationships within datasets is paramount to gaining profound insights. In this extended analysis, we will embark on a journey into a dataset comprising two pivotal columns, X and Y, to delve deeper into the intricate relationship between them.

### Table 1: The X and Y Dataset

Before we immerse ourselves in the intricacies of data analysis, let's take a moment to acquaint ourselves with the dataset at hand. Here, we encounter a collection of X and Y values, denoting some underlying connection between the two. X stands as the independent variable, while Y assumes the role of the dependent variable.

|   X   |   Y   |
|-------|-------|
|  10   |  25   |
|  15   |  35   |
|  20   |  40   |
|  25   |  55   |
|  30   |  60   |
|  40   |  70   |
|  50   |  80   |

### Visualizing the Relationship

Our journey into this data begins with a compelling visualization - the scatter plot. This visualization serves as a window into the heart of the relationship between X and Y, revealing the fundamental nature of their connection.

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="3cec3c57-7ea9-4c11-9528-301fcae2a354" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("3cec3c57-7ea9-4c11-9528-301fcae2a354")) {                    Plotly.newPlot(                        "3cec3c57-7ea9-4c11-9528-301fcae2a354",                        [{"hovertemplate":"X=%{x}\u003cbr\u003eY=%{y}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":"#636efa","symbol":"circle"},"mode":"markers","name":"","orientation":"v","showlegend":false,"x":[10,15,20,25,30,40,50],"xaxis":"x","y":[25,35,40,55,60,70,80],"yaxis":"y","type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"X"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Y"}},"legend":{"tracegroupgap":0},"title":{"text":"Scatter Plot"}},                        {"responsive": true}                    )                };                            </script>        </div>

As evident from the scatter plot, a clear positive linear relationship emerges. This visual cue suggests that as X values ascend, Y values accompany them in a harmonious ascent, signifying a robust correlation between the two variables.

### Regression Analysis - The Heart of the Matter

To dissect and quantify this relationship with precision, we turn to the statistical technique of regression analysis. It provides the tools to not only affirm our visual observations but also to uncover nuanced insights. The results of this analysis are displayed in Table 2.

### Table 2: Regression Statistics

| Statistic             | Value        |
|-----------------------|--------------|
| Multiple R            | 0.9827       |
| R Square              | 0.9658       |
| Adjusted R Square     | 0.9589       |
| Standard Error        | 4.006        |
| Observations          | 7            |

Delving into these statistics reveals the depth of the connection between X and Y:

**Multiple R (Multiple Correlation Coefficient)**: With a value of 0.9827, we confirm our visual assessment of a robust positive correlation. This statistic elucidates the strength of the linear relationship.

**R Square (Coefficient of Determination)**: At 0.9658, this metric informs us that approximately 96.58% of the variance in Y can be ascribed to variations in X. Such a high R Square underscores the potency of X as a predictor of Y in our dataset.

**Adjusted R Square**: This statistic, standing at 0.9589, reflects the model's adaptability when considering the number of variables involved. The fact that it remains high reinforces the soundness of our model.

**Standard Error**: Marking the spread between actual Y values and their corresponding predictions, the standard error is a valuable measure at 4.006.

**Observations**: The dataset comprises seven data points, underpinning the analysis.

### ANOVA (Analysis of Variance) - The Model's Significance

To appraise the model's overall significance, we deploy the venerable statistical tool - ANOVA. Its application to our regression model yields Table 3, offering a comprehensive view of the analysis's validity.

### Table 3: ANOVA (Analysis of Variance) Table

|      | df |       SS       |        MS        |        F        | Significance F   |
|------|----|----------------|------------------|-----------------|-------------------|
| Regression | 1  | 2262.617622 | 2262.617622 | 140.9914712 | 7.46229E-05 |
| Residual   | 5  | 80.23952096   | 16.04790419   |                  |                       |
| Total       | 6  | 2342.857143   |                       |                  |                       |

**Regression**: This row scrutinizes the model's overarching influence in explaining the dataset's variance. With a degrees of freedom (df) of 1, it reflects the model's complexity.

**Sum of Squares (SS)** for regression (2262.617622) accounts for the total variance elucidated by our model. The **Mean Square (MS)** is derived by dividing SS by its degrees of freedom, offering an insightful metric for variability within the regression.

The **F-statistic** (140.9914712) acts as a sentinel, guarding the model's integrity. It quantifies the ratio of variance clarified by the model against the unexplained variance (residual). A lofty F-value confirms the model's statistical significance, which is further corroborated by the minuscule **Significance F (p-value)** of 7.46229E-05. This tiny p-value signals that the regression model is indisputably significant, signifying that the relationship between X and Y isn't due to mere chance.

### Coefficients - The Precise Formula

In Table 4, we examine the coefficients that define our regression model, offering us precise insights into how X and the intercept contribute to the prediction of Y.

### Table 4: Coefficients Table

|            | Coefficients | Standard Error | t Stat     | P-value       | Lower 95%   | Upper 95%   | Lower 95.0% | Upper 95.0% |
|------------|--------------|----------------|------------|---------------|-------------|-------------|-------------|-------------|
| Intercept  | 14.76047904  | 3.49343596     | 4.225203843| 0.008286304   | 5.78031602  | 23.74064206 | 5.78031602  | 23.74064206 |
| X Variable 1 | 1.377245509  | 0.115988503    | 11.87398295| 7.46229E-05   | 1.07908757  | 1.675403448 | 1.07908757  | 1.675403448 |

In Table 4, we unearth the precise formula that describes the relationship:

**Intercept**: At 14.76047904, the intercept represents the estimated value of Y when X is zero. This value holds valuable insights, revealing the starting point of our relationship.

**X Variable 1**: The coefficient for X, marked at 1.377245509, portrays the extent to which Y is projected to change for every unit increase in X. In this case, for each unit rise in X, we expect Y to ascend by approximately 1.3772 units.

**Standard Error**: This metric, found in the same table, stands as a sentinel, guarding the precision of the coefficient estimates.

**t Stat (t-Statistic)** and **P-value**: These components confer the statistical significance of each coefficient. In

 both instances, the p-values are remarkably low (7.46229E-05), indicating that both the intercept and X Variable 1 hold immense statistical significance as predictors of Y.

**Lower 95%** and **Upper 95%**: These columns divulge the lower and upper bounds of the 95% confidence interval for each coefficient. This vital information guides us in assessing the range in which the true coefficient values likely reside, bolstering our confidence in the model.

### Implications and Beyond

In this comprehensive analysis, we unearthed a robust positive relationship between X and Y, validated by regression statistics, ANOVA results, and precise coefficient estimates. Our understanding of these statistical measures empowers us to make data-driven decisions and forecasts, unraveling insights that reverberate across a multitude of fields.

The significance of data analysis becomes abundantly clear as we unearth meaningful patterns and insights from raw data. Our exploration of this dataset serves as an inspiring testament to the potency of data analysis in deciphering complex relationships, shedding light on a path toward more informed decisions and innovative solutions.

So, as you venture into the realm of data analysis, remember that beneath the numbers lies a wealth of knowledge, waiting to be revealed.

### Predicting with Confidence: Understanding Prediction Intervals in Regression Analysis

Regression analysis is a powerful tool in statistics and data analysis, allowing us to understand and predict relationships between variables. One essential aspect of regression analysis is making predictions, and that's where prediction intervals come into play. In this blog post, we'll explore prediction intervals and how they can be calculated using two fundamental equations.

**Equation 1: Prediction Interval for Response**
$$
\widehat{y} = \pm \, t_{\frac{\alpha}{2}, n-2} \, \text{SYX} \, \sqrt{1 + \frac{1}{n} + \frac{\left(x_{p} - \overline{x}\right)^2}{\text{SSX}}}
$$

**Equation 2: Confidence Interval for Response**
$$
\widehat{y} = \pm \, t_{\frac{\alpha}{2}, n-2} \, \text{SYX} \, \sqrt{\frac{1}{n} + \frac{\left(x_{p} - \overline{x}\right)^2}{\text{SSX}}}
$$

### What are Prediction Intervals?

Prediction intervals are a vital component of regression analysis that help us estimate the range within which we can expect future observations to fall. Unlike confidence intervals, which provide an interval estimate for a population parameter, prediction intervals give us an interval estimate for an individual observation or the mean response.

### Understanding the Equations

Let's break down these equations step by step:

-  $$\widehat{y}$$ represents the predicted mean response.
- $$t_{\frac{\alpha}{2}, n}$$ is the critical t-score, depending on the desired confidence level ($$\alpha$$) and the sample size ($$ n $$).
- $$\text{SYX}$$ denotes the standard error of the regression, measuring the typical error in the model's predictions.
- $$x_p$$ is the value of the predictor variable for which you want to make a prediction.
- $$\overline{x}$$ represents the sample mean of the predictor variable.
- $$\text{SSX}$$ is the sum of squares of the predictor variable.

### Conclusion

Prediction intervals are valuable tools in regression analysis, providing us with a measure of uncertainty in our predictions. These two equations give you the flexibility to choose the most suitable prediction interval for your specific analysis. Whether you're forecasting the average response or predicting individual outcomes, understanding and using prediction intervals can enhance the reliability of your regression models.

### Confidence Interval and Prediction Interval of Predictions (Excel)

![image tooltip here](/assets/regexcel.PNG){: width="1000" }

The table provides a comprehensive overview of various variables and their corresponding amounts, along with the formulas used to calculate them in a tabulated format. Notably, it includes essential statistical and mathematical parameters for data analysis. For instance, 'n' represents the sample size, calculated as 7. The 'df' value signifies degrees of freedom, computed as 5. 'alpha' is the significance level, set at 0.05. 'SYX' denotes the standard error of the regression, while 'SSX' represents the sum of squared deviations. 'X_p' is a calculated value using randomization, while 'X_bar' represents the sample mean. 'Y_hat_i' signifies the predicted value, and 'Critical T' is a critical value used in t-distribution. Additionally, the table displays two types of margin of errors (MOE) and corresponding prediction and confidence intervals, providing crucial information for statistical analysis.



## Predicting with Confidence: Using Python for Linear Regression

Linear regression is a powerful statistical technique used to model the relationship between a dependent variable (Y) and one or more independent variables (X). It allows us to make predictions based on this relationship. In this blog post, we'll walk through the process of fitting a simple linear regression model using Python and then using that model to calculate both a 95% confidence interval and a 95% prediction interval for a given value of X.

### The Code

We'll start by importing the necessary libraries, including pandas for data manipulation and statsmodels for the linear regression model. Then, we'll create a sample dataset and fit a linear regression model to it.

```python
import pandas as pd
import statsmodels.api as sm

# Create a data frame with your data
data = pd.DataFrame({
    'X': [10, 15, 20, 25, 30, 40, 50],
    'Y': [25, 35, 40, 55, 60, 70, 80]
})

# Fit a linear regression model
X = data['X']
X = sm.add_constant(X)  # Add a constant term (intercept) to the model
Y = data['Y']
model = sm.OLS(Y, X).fit()
```

Once we have our linear regression model, we can use it to make predictions. In this case, we want to predict the value of Y for a given value of X, specifically, when X is 32.62. We create a new data frame `new_X` with this value.

```python
# Define the value of X for which you want to make predictions
new_X = pd.DataFrame({'const': [1], 'X': [32.62]})  # Adding a constant for the intercept
```

Now comes the interesting part-calculating the confidence and prediction intervals. A confidence interval gives us a range in which we can be reasonably confident that the true value of Y lies, while a prediction interval is a wider range that accounts for both the uncertainty in our model and the randomness of individual data points.

```python
# Calculate the 95% confidence interval
confidence_interval = model.get_prediction(new_X).conf_int()

# Calculate the 95% prediction interval
prediction_interval = model.get_prediction(new_X).conf_int(obs=True)
```

Finally, let's print the results to see our calculated intervals.

```python
# Print the results
print("95% Confidence Interval:")
print(confidence_interval)
print("\n95% Prediction Interval:")
print(prediction_interval)
```


## Predicting with Confidence: Using R for Linear Regression

Linear regression is a fundamental statistical technique used to model the relationship between variables. It enables us to make predictions based on this relationship. In this blog post, we'll explore how to fit a simple linear regression model using R and then use that model to calculate both a 95% confidence interval and a 95% prediction interval for a specific value of X.

### The Code

We'll start by creating a sample dataset and fitting a linear regression model to it using R. In this example, we have a dataset with two variables, X and Y.

```R
# Create a data frame with your data
data <- data.frame(
  X = c(10, 15, 20, 25, 30, 40, 50),
  Y = c(25, 35, 40, 55, 60, 70, 80)
)

# Fit a linear regression model
model <- lm(Y ~ X, data = data)
```

Once we have our linear regression model, we can use it to make predictions. To predict the value of Y for a given value of X (in this case, when X is 32.62), we create a new data frame `new_X` with this value.

```R
# Define the value of X for which you want to make predictions
new_X <- data.frame(X = 32.62)
```

Now, let's calculate the confidence and prediction intervals. A confidence interval provides a range within which we can reasonably expect the true value of Y to fall, while a prediction interval accounts for both the model's uncertainty and the variability of individual data points.

```R
# Calculate the 95% confidence interval
confidence_interval <- predict(model, newdata = new_X, interval = "confidence", level = 0.95)

# Calculate the 95% prediction interval
prediction_interval <- predict(model, newdata = new_X, interval = "prediction", level = 0.95)
```

Finally, let's print the results to see the calculated intervals.

```R
# Print the results
cat("95% Confidence Interval:", confidence_interval, "\n")
cat("95% Prediction Interval:", prediction_interval, "\n")


```

## Visualizing Confidence and Prediction Intervals at 95% Confidence Level

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="c20ef20d-a2a2-4079-8573-ccf5bebc5d2f" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("c20ef20d-a2a2-4079-8573-ccf5bebc5d2f")) {                    Plotly.newPlot(                        "c20ef20d-a2a2-4079-8573-ccf5bebc5d2f",                        [{"hovertemplate":"X=%{x}\u003cbr\u003eY=%{y}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":"#636efa","symbol":"circle"},"mode":"markers","name":"","orientation":"v","showlegend":false,"x":[10,15,20,25,30,40,50],"xaxis":"x","y":[25,35,40,55,60,70,80],"yaxis":"y","type":"scatter"},{"mode":"lines","name":"Predictions","x":[10.0,10.404040404040405,10.808080808080808,11.212121212121213,11.616161616161616,12.02020202020202,12.424242424242424,12.828282828282829,13.232323232323232,13.636363636363637,14.040404040404042,14.444444444444445,14.848484848484848,15.252525252525253,15.656565656565657,16.060606060606062,16.464646464646464,16.86868686868687,17.272727272727273,17.676767676767675,18.080808080808083,18.484848484848484,18.88888888888889,19.292929292929294,19.696969696969695,20.1010101010101,20.505050505050505,20.909090909090907,21.313131313131315,21.717171717171716,22.12121212121212,22.525252525252526,22.929292929292927,23.333333333333336,23.737373737373737,24.141414141414142,24.545454545454547,24.949494949494948,25.353535353535353,25.757575757575758,26.161616161616163,26.565656565656564,26.96969696969697,27.373737373737374,27.77777777777778,28.18181818181818,28.585858585858585,28.98989898989899,29.393939393939394,29.7979797979798,30.2020202020202,30.606060606060606,31.01010101010101,31.414141414141415,31.818181818181817,32.22222222222222,32.62626262626263,33.03030303030303,33.43434343434343,33.838383838383834,34.24242424242424,34.64646464646465,35.05050505050505,35.45454545454545,35.858585858585855,36.26262626262626,36.66666666666667,37.07070707070707,37.474747474747474,37.878787878787875,38.282828282828284,38.686868686868685,39.09090909090909,39.494949494949495,39.898989898989896,40.3030303030303,40.707070707070706,41.111111111111114,41.515151515151516,41.91919191919192,42.323232323232325,42.72727272727273,43.13131313131313,43.535353535353536,43.93939393939394,44.343434343434346,44.74747474747475,45.15151515151515,45.55555555555556,45.95959595959596,46.36363636363636,46.76767676767677,47.17171717171717,47.57575757575758,47.97979797979798,48.38383838383838,48.78787878787879,49.19191919191919,49.5959595959596,50.0],"y":[28.53293413173653,29.08939696364846,29.645859795560398,30.202322627472334,30.758785459384264,31.3152482912962,31.871711123208133,32.428173955120066,32.984636787032,33.54109961894393,34.097562450855875,34.654025282767805,35.210488114679734,35.76695094659167,36.32341377850361,36.879876610415536,37.43633944232747,37.99280227423941,38.54926510615134,39.10572793806327,39.66219076997521,40.21865360188714,40.77511643379908,41.331579265711014,41.88804209762294,42.44450492953487,43.000967761446816,43.557430593358745,44.11389342527068,44.67035625718261,45.22681908909455,45.783281921006484,46.33974475291841,46.89620758483035,47.452670416742286,48.009133248654216,48.56559608056615,49.12205891247808,49.67852174439002,50.234984576301954,50.79144740821389,51.34791024012582,51.90437307203776,52.460835903949686,53.01729873586162,53.57376156777355,54.13022439968549,54.686687231597425,55.24315006350936,55.7996128954213,56.35607572733323,56.912538559245164,57.46900139115709,58.02546422306903,58.58192705498096,59.138389886892895,59.69485271880484,60.25131555071677,60.8077783826287,61.36424121454063,61.92070404645256,62.47716687836451,63.033629710276436,63.590092542188366,64.1465553741003,64.70301820601225,65.25948103792417,65.8159438698361,66.37240670174805,66.92886953365996,67.4853323655719,68.04179519748384,68.59825802939578,69.15472086130771,69.71118369321964,70.26764652513157,70.82410935704351,71.38057218895545,71.93703502086737,72.49349785277931,73.04996068469126,73.60642351660317,74.16288634851512,74.71934918042706,75.27581201233897,75.83227484425092,76.38873767616285,76.94520050807478,77.50166333998672,78.05812617189865,78.61458900381058,79.17105183572252,79.72751466763444,80.28397749954638,80.84044033145832,81.39690316337024,81.95336599528218,82.50982882719413,83.06629165910607,83.62275449101799],"type":"scatter"},{"fill":"none","line":{"width":0},"mode":"lines","name":"Confidence Interval Lower Bound","x":[10.0,10.404040404040405,10.808080808080808,11.212121212121213,11.616161616161616,12.02020202020202,12.424242424242424,12.828282828282829,13.232323232323232,13.636363636363637,14.040404040404042,14.444444444444445,14.848484848484848,15.252525252525253,15.656565656565657,16.060606060606062,16.464646464646464,16.86868686868687,17.272727272727273,17.676767676767675,18.080808080808083,18.484848484848484,18.88888888888889,19.292929292929294,19.696969696969695,20.1010101010101,20.505050505050505,20.909090909090907,21.313131313131315,21.717171717171716,22.12121212121212,22.525252525252526,22.929292929292927,23.333333333333336,23.737373737373737,24.141414141414142,24.545454545454547,24.949494949494948,25.353535353535353,25.757575757575758,26.161616161616163,26.565656565656564,26.96969696969697,27.373737373737374,27.77777777777778,28.18181818181818,28.585858585858585,28.98989898989899,29.393939393939394,29.7979797979798,30.2020202020202,30.606060606060606,31.01010101010101,31.414141414141415,31.818181818181817,32.22222222222222,32.62626262626263,33.03030303030303,33.43434343434343,33.838383838383834,34.24242424242424,34.64646464646465,35.05050505050505,35.45454545454545,35.858585858585855,36.26262626262626,36.66666666666667,37.07070707070707,37.474747474747474,37.878787878787875,38.282828282828284,38.686868686868685,39.09090909090909,39.494949494949495,39.898989898989896,40.3030303030303,40.707070707070706,41.111111111111114,41.515151515151516,41.91919191919192,42.323232323232325,42.72727272727273,43.13131313131313,43.535353535353536,43.93939393939394,44.343434343434346,44.74747474747475,45.15151515151515,45.55555555555556,45.95959595959596,46.36363636363636,46.76767676767677,47.17171717171717,47.57575757575758,47.97979797979798,48.38383838383838,48.78787878787879,49.19191919191919,49.5959595959596,50.0],"y":[22.10843849142919,22.760323799422558,23.41134176994242,24.061452337910687,24.71061335348971,25.35878048397486,26.005907114836866,26.651944250768974,27.29684041778091,27.940541567594195,28.58299098583293,29.22412920577086,29.863893929690306,30.502219960228434,31.13903914443074,31.77428033359364,32.407869362351704,33.03972905083962,33.66977923412108,34.297936823407774,34.9241159038706,35.548227874044045,36.170181631913216,36.78988381271386,37.40723908323312,38.022150496928944,38.63451991345319,39.24424848513034,39.85123721158543,40.45538756201631,41.05660216257517,41.65478554398735,42.249844941954095,42.841691140144704,43.43023934280687,44.015410061360114,44.59712999695974,45.17533289911298,45.74996037917684,46.32096265713071,46.88829922052042,47.45193937598026,48.011862676254346,48.56805920907914,49.120529738498924,49.66928569394344,50.21434900743024,50.755751804265465,51.29353595731224,51.827752519007795,52.35846104862664,52.88572885466119,53.40963017355609,53.93024530639586,54.44765973458397,54.96196323419543,55.473249006700215,55.98161284132542,56.487152321634,56.9899660861172,57.49015314987373,57.98781229189645,58.48304151019257,58.97593754497839,59.46659546854048,59.95510833904429,60.44156691458299,60.92605942306605,61.40867138311236,61.88948547089857,62.36858142787812,62.8460360043917,63.3219229344035,63.79631293688395,64.26927373969762,64.74087012221901,65.21116397327441,65.68021436138068,66.14807761461141,66.61480740776243,67.08045485480429,67.54506860490145,68.00869494053947,68.47137787653757,68.93315925893319,69.39407886290799,69.85417448908531,70.31348205766753,70.77203570000027,71.22986784725234,71.68700931598538,72.14348939045962,72.59933590158171,73.05457530245047,73.50923274049626,73.96333212624288,74.41689619874664,74.86994658778752,75.32250387290331,75.77458763936912],"type":"scatter"},{"fill":"tonexty","line":{"width":0},"mode":"lines","name":"Confidence Interval Upper Bound","x":[10.0,10.404040404040405,10.808080808080808,11.212121212121213,11.616161616161616,12.02020202020202,12.424242424242424,12.828282828282829,13.232323232323232,13.636363636363637,14.040404040404042,14.444444444444445,14.848484848484848,15.252525252525253,15.656565656565657,16.060606060606062,16.464646464646464,16.86868686868687,17.272727272727273,17.676767676767675,18.080808080808083,18.484848484848484,18.88888888888889,19.292929292929294,19.696969696969695,20.1010101010101,20.505050505050505,20.909090909090907,21.313131313131315,21.717171717171716,22.12121212121212,22.525252525252526,22.929292929292927,23.333333333333336,23.737373737373737,24.141414141414142,24.545454545454547,24.949494949494948,25.353535353535353,25.757575757575758,26.161616161616163,26.565656565656564,26.96969696969697,27.373737373737374,27.77777777777778,28.18181818181818,28.585858585858585,28.98989898989899,29.393939393939394,29.7979797979798,30.2020202020202,30.606060606060606,31.01010101010101,31.414141414141415,31.818181818181817,32.22222222222222,32.62626262626263,33.03030303030303,33.43434343434343,33.838383838383834,34.24242424242424,34.64646464646465,35.05050505050505,35.45454545454545,35.858585858585855,36.26262626262626,36.66666666666667,37.07070707070707,37.474747474747474,37.878787878787875,38.282828282828284,38.686868686868685,39.09090909090909,39.494949494949495,39.898989898989896,40.3030303030303,40.707070707070706,41.111111111111114,41.515151515151516,41.91919191919192,42.323232323232325,42.72727272727273,43.13131313131313,43.535353535353536,43.93939393939394,44.343434343434346,44.74747474747475,45.15151515151515,45.55555555555556,45.95959595959596,46.36363636363636,46.76767676767677,47.17171717171717,47.57575757575758,47.97979797979798,48.38383838383838,48.78787878787879,49.19191919191919,49.5959595959596,50.0],"y":[34.95742977204387,35.418470127874365,35.88037782117837,36.34319291703398,36.80695756527882,37.27171609861754,37.7375151315794,38.20440365947116,38.67243315628309,39.14165767029367,39.61213391587882,40.083921359764744,40.55708229966916,41.0316819329549,41.507788412576474,41.985472887237435,42.46480952230324,42.9458754976392,43.4287509781816,43.91351905271876,44.40026563607982,44.88907932973024,45.38005123568494,45.87327471870817,46.368845112012764,46.8668593621408,47.36741560944044,47.87061270158715,48.376549638955936,48.88532495234891,49.39703601561393,49.91177829802562,50.42964456388273,50.950724029515996,51.4751014906777,52.00285643594832,52.53406216417257,53.06878492584318,53.607083109603195,54.1490064954732,54.69459559590736,55.24388110427138,55.79688346782117,56.353612598820234,56.91406773322432,57.47823744160366,58.04609979194073,58.617622658929385,59.192764169706486,59.7714732718348,60.35369040603982,60.93934826382914,61.5283726087581,62.1206831397422,62.716194375377945,63.31481653959036,63.91645643090946,64.52101826010811,65.1284044436234,65.73851634296405,66.3512549430314,66.96652146483257,67.58421791036031,68.20424753939834,68.82651527966013,69.4509280729802,70.07739516126536,70.70582831660616,71.33614202038373,71.96825359642136,72.60208330326569,73.23755439057598,73.87459312438806,74.51312878573147,75.15309364674165,75.79442292804413,76.43705474081261,77.08093001653023,77.72599242712333,78.3721882977962,79.01946651457823,79.6677784283049,80.31707775649076,80.96732048431655,81.61846476574476,82.27047082559385,82.92330086324039,83.57691895848203,84.23129097997317,84.88638449654496,85.54216869163578,86.19861428098542,86.85569343368716,87.51337969664229,88.17164792242039,88.8304742004976,89.48983579181773,90.14971106660073,90.81007944530883,91.47092134266686],"type":"scatter"},{"fill":"none","line":{"width":0},"mode":"lines","name":"Prediction Interval Lower Bound","x":[10.0,10.404040404040405,10.808080808080808,11.212121212121213,11.616161616161616,12.02020202020202,12.424242424242424,12.828282828282829,13.232323232323232,13.636363636363637,14.040404040404042,14.444444444444445,14.848484848484848,15.252525252525253,15.656565656565657,16.060606060606062,16.464646464646464,16.86868686868687,17.272727272727273,17.676767676767675,18.080808080808083,18.484848484848484,18.88888888888889,19.292929292929294,19.696969696969695,20.1010101010101,20.505050505050505,20.909090909090907,21.313131313131315,21.717171717171716,22.12121212121212,22.525252525252526,22.929292929292927,23.333333333333336,23.737373737373737,24.141414141414142,24.545454545454547,24.949494949494948,25.353535353535353,25.757575757575758,26.161616161616163,26.565656565656564,26.96969696969697,27.373737373737374,27.77777777777778,28.18181818181818,28.585858585858585,28.98989898989899,29.393939393939394,29.7979797979798,30.2020202020202,30.606060606060606,31.01010101010101,31.414141414141415,31.818181818181817,32.22222222222222,32.62626262626263,33.03030303030303,33.43434343434343,33.838383838383834,34.24242424242424,34.64646464646465,35.05050505050505,35.45454545454545,35.858585858585855,36.26262626262626,36.66666666666667,37.07070707070707,37.474747474747474,37.878787878787875,38.282828282828284,38.686868686868685,39.09090909090909,39.494949494949495,39.898989898989896,40.3030303030303,40.707070707070706,41.111111111111114,41.515151515151516,41.91919191919192,42.323232323232325,42.72727272727273,43.13131313131313,43.535353535353536,43.93939393939394,44.343434343434346,44.74747474747475,45.15151515151515,45.55555555555556,45.95959595959596,46.36363636363636,46.76767676767677,47.17171717171717,47.57575757575758,47.97979797979798,48.38383838383838,48.78787878787879,49.19191919191919,49.5959595959596,50.0],"y":[16.395514901616252,17.002214973892123,17.607919093466826,18.212614989310907,18.81629044544825,19.418933312487802,20.020531519472897,20.621073086033128,21.22054613482129,21.818938904216296,22.41623976127098,23.012437214881516,23.607519929153742,24.2014767369391,24.79429665351161,25.385968890355173,25.976482869028786,26.565828235075518,27.15399487193976,27.74097291485551,28.32675276466735,28.911325101544357,29.494680898546676,30.076811435002973,30.657708309656954,31.237363453540432,31.81576914253022,32.392918009546264,32.96880305634881,33.54341766489239,34.11675560819606,34.68881106068936,35.25957860799569,35.8290532561155,36.39723043997398,36.96410603129996,37.529676345804575,38.09393814963102,38.65688866504959,39.218525575374365,39.778847029081795,40.33785164311387,40.89553850535235,41.45190717625357,42.006957689637275,42.56069055262583,43.11310674473437,43.664207716115484,44.21399538496591,44.76247213410593,45.30964080674568,45.85550470145594,46.4000675663638,46.94333359259714,47.485307407004015,48.02599406417639,48.565399037809485,49.103528211430586,49.64038786853311,50.17598468215323,50.71032570392812,51.24341835267606,51.77527040253945,52.30588997073285,52.83528550493826,53.363465770390405,53.89043983669458,54.416217064419705,54.940807091508155,55.464219819544006,55.98646539992021,56.50755421994366,57.02749688891704,57.546304224233864,58.06398723752235,58.58055712087198,59.09602523317484,59.61040308661208,60.12370233331424,60.635934752222,61.14711223617188,61.657246779230164,62.16635046429559,62.674435450989556,63.181513963851344,63.68759828085304,64.19270072224727,64.69683363975973,65.20000940613558,65.7022404050478,66.20353902137421,66.70391763184732,67.20338859608076,67.70196424797409,68.19965688749626,68.69647877284751,69.19244211299772,69.68755906059796,70.18184170526214,70.67530206721331],"type":"scatter"},{"fill":"tonexty","line":{"width":0},"mode":"lines","name":"Prediction Interval Upper Bound","x":[10.0,10.404040404040405,10.808080808080808,11.212121212121213,11.616161616161616,12.02020202020202,12.424242424242424,12.828282828282829,13.232323232323232,13.636363636363637,14.040404040404042,14.444444444444445,14.848484848484848,15.252525252525253,15.656565656565657,16.060606060606062,16.464646464646464,16.86868686868687,17.272727272727273,17.676767676767675,18.080808080808083,18.484848484848484,18.88888888888889,19.292929292929294,19.696969696969695,20.1010101010101,20.505050505050505,20.909090909090907,21.313131313131315,21.717171717171716,22.12121212121212,22.525252525252526,22.929292929292927,23.333333333333336,23.737373737373737,24.141414141414142,24.545454545454547,24.949494949494948,25.353535353535353,25.757575757575758,26.161616161616163,26.565656565656564,26.96969696969697,27.373737373737374,27.77777777777778,28.18181818181818,28.585858585858585,28.98989898989899,29.393939393939394,29.7979797979798,30.2020202020202,30.606060606060606,31.01010101010101,31.414141414141415,31.818181818181817,32.22222222222222,32.62626262626263,33.03030303030303,33.43434343434343,33.838383838383834,34.24242424242424,34.64646464646465,35.05050505050505,35.45454545454545,35.858585858585855,36.26262626262626,36.66666666666667,37.07070707070707,37.474747474747474,37.878787878787875,38.282828282828284,38.686868686868685,39.09090909090909,39.494949494949495,39.898989898989896,40.3030303030303,40.707070707070706,41.111111111111114,41.515151515151516,41.91919191919192,42.323232323232325,42.72727272727273,43.13131313131313,43.535353535353536,43.93939393939394,44.343434343434346,44.74747474747475,45.15151515151515,45.55555555555556,45.95959595959596,46.36363636363636,46.76767676767677,47.17171717171717,47.57575757575758,47.97979797979798,48.38383838383838,48.78787878787879,49.19191919191919,49.5959595959596,50.0],"y":[40.670353361856804,41.1765789534048,41.68380049765397,42.19203026563376,42.70128047332028,43.2115632701046,43.72289072694337,44.235274824207,44.748727439242714,45.26326033367157,45.77888514044077,46.295613350654094,46.81345630020573,47.33242515624424,47.852530903495605,48.3737843304759,48.89619601562616,49.419776313403304,49.94453534036292,50.470482961271024,50.997628775283076,51.525982102229925,52.05555196905148,52.586347096419054,53.11837588558893,53.65164640552931,54.18616638036342,54.72194317717123,55.25898379419255,55.797294849472834,56.33688256999304,56.87775278132361,57.419910897841135,57.9633619135452,58.50811039351059,59.05416046600847,59.60151581532773,60.15017967532514,60.70015482373044,61.251443577229544,61.804047787345986,62.35796883713777,62.913207638723165,63.4697646316458,64.02763978208597,64.58683258292128,65.14734205463661,65.70916674707937,66.27230474205281,66.83675365673666,67.40251064792078,67.96957241703439,68.53793521595038,69.10759485354092,69.6785467029579,70.2507857096094,70.8243063998002,71.39910289000295,71.97516889672428,72.55249774692803,73.131082388977,73.71091540405295,74.29198901801342,74.87429511364388,75.45782524326235,76.04257064163409,76.62852223915377,77.21567067525251,77.80400631198795,78.39351924777593,78.9841993312236,79.57603617502402,80.16901916987452,80.76313749838155,81.35838014891694,81.95473592939116,82.55219348091218,83.15074129129883,83.7503677084205,84.35106095333663,84.95280913321064,85.55560025397618,86.15942223273464,86.76426290986456,87.3701100608266,87.9769514076488,88.58477463007843,89.19356737638982,89.80331727383786,90.4140119387495,91.02563898624695,91.63818603959773,92.25164073918812,92.86599075111867,93.48122377542039,94.09732755389297,94.71428987756664,95.33209859379029,95.95074161295,96.57020691482266],"type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"X"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Y"}},"legend":{"tracegroupgap":0},"title":{"text":"Linear Regression Predictions with Intervals"}},                        {"responsive": true}                    )                };                            </script>        </div>


