---
layout: post
title:  "Understanding and Addressing Imbalanced Datasets in Machine Learning"
date:   2023-11-29 06:25:17 -0800
categories: jekyll update data
---
## Introduction

Imbalanced datasets, where one class significantly outnumbers the others, can pose challenges for machine learning models. This blog post explores strategies to address such imbalances using Python and scikit-learn. We will work through a real-world example using the eBay Auctions dataset.

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="bcec3dbb-a463-4a03-bea1-f708acabe953" class="plotly-graph-div" style="height:100%; width:400px;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("bcec3dbb-a463-4a03-bea1-f708acabe953")) {                    Plotly.newPlot(                        "bcec3dbb-a463-4a03-bea1-f708acabe953",                        [{"domain":{"x":[0.0,1.0],"y":[0.0,1.0]},"hole":0.3,"hovertemplate":"index=%{label}\u003cbr\u003eValues=%{value}\u003cextra\u003e\u003c\u002fextra\u003e","labels":[1,0],"legendgroup":"","name":"","showlegend":true,"values":[1066,906],"type":"pie","pull":[0.1,0.1],"textinfo":"percent+label"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"legend":{"tracegroupgap":0},"title":{"text":"No Sampling"},"piecolorway":["blue","orange"],"width":400},                        {"responsive": true}                    )                };                            </script>        

                       <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="672d9b2b-b219-4844-9730-be9dd6791779" class="plotly-graph-div" style="height:100%; width:400px;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("672d9b2b-b219-4844-9730-be9dd6791779")) {                    Plotly.newPlot(                        "672d9b2b-b219-4844-9730-be9dd6791779",                        [{"domain":{"x":[0.0,1.0],"y":[0.0,1.0]},"hole":0.3,"hovertemplate":"index=%{label}\u003cbr\u003eValues=%{value}\u003cextra\u003e\u003c\u002fextra\u003e","labels":[0,1],"legendgroup":"","name":"","showlegend":true,"values":[906,906],"type":"pie","pull":[0.1,0.1],"textinfo":"percent+label"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"legend":{"tracegroupgap":0},"title":{"text":"Under-sampling"},"piecolorway":["blue","orange"],"width":400},                        {"responsive": true}                    )                };                            </script>        </div>

## Loading and Exploring the Dataset

We begin by importing necessary libraries and loading the dataset. The eBay Auctions dataset, available in the [DMBA repository](https://github.com/gedeck/dmba), contains information about auctions on eBay.

```python
# Code for loading the dataset
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import gdown
from imblearn.under_sampling import RandomUnderSampler
from imblearn.over_sampling import RandomOverSampler
from imblearn.pipeline import Pipeline
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import cross_val_score

# Download and load the eBay Auctions dataset
url="https://github.com/gedeck/dmba/raw/master/datasets/dmba-datasets.zip"
gdown.download(url,'file.zip',quiet=True)
!unzip -o file.zip &> /dev/null
df=pd.read_csv('/content/dmba/eBayAuctions.csv')
df.head()
```

Next, we preprocess the data by one-hot encoding categorical variables and preparing the features (X) and labels (y) for model training.

```python
# Code for data preprocessing
df=pd.get_dummies(data=df,columns=df.columns[0:-1]).assign(**{f"Competitive?": df['Competitive?'].to_list()})
df.head()

# Split the data into features(X) and labels(y)
Xtrain=df.drop('Competitive?',axis=1)
ytrain=df['Competitive?']

# Visualize class distribution
counts = ytrain.value_counts()
plt.pie(counts, labels=counts.index, autopct=lambda p: '{:.0f}'.format(p * sum(counts) / 100))
plt.show()
```

## Handling Imbalanced Data

Imbalanced datasets can lead to biased models. To address this, we explore two common techniques: random under-sampling and random over-sampling.

### Random Under-sampling

```python
# Code for random under-sampling
rus = RandomUnderSampler(sampling_strategy=1)
Xtrain_us, ytrain_us = rus.fit_resample(Xtrain, ytrain)
counts = ytrain_us.value_counts()
plt.pie(counts, labels=counts.index, autopct=lambda p: '{:.0f}'.format(p * sum(counts) / 100))
plt.title("Under-sampling");
```

### Random Over-sampling

```python
# Code for random over-sampling
ros = RandomOverSampler(sampling_strategy=1)
Xtrain_os, ytrain_os = ros.fit_resample(Xtrain, ytrain)
counts = ytrain_os.value_counts()
plt.pie(counts, labels=counts.index, autopct=lambda p: '{:.0f}'.format(p * sum(counts) / 100))
plt.title("Over-sampling");
```

## Model Training and Evaluation

We train a Decision Tree Classifier using a pipeline that incorporates either under-sampling or over-sampling.

```python
# Code for model training and evaluation
steps = [('under', RandomUnderSampler()), ('model', DecisionTreeClassifier())]
pipeline = Pipeline(steps=steps)
scores_us = cross_val_score(pipeline, Xtrain, ytrain, scoring='f1_micro', cv=10, n_jobs=-1)
score = np.mean(scores_us)
print('F1 Score (Under-sampling): %.3f' % score)

steps = [('over', RandomOverSampler()), ('model', DecisionTreeClassifier())]
pipeline = Pipeline(steps=steps)
scores_os = cross_val_score(pipeline, Xtrain, ytrain, scoring='f1_micro', cv=10, n_jobs=-1)
score = np.mean(scores_os)
print('F1 Score (Over-sampling): %.3f' % score)
```

## Assessing the Impact

To understand the impact of under-sampling and over-sampling on model performance, we perform a two-sample t-test on the F1 scores.

```python
# Code for two-sample t-test
import scipy.stats as stats
t_statistic, p_value = stats.ttest_rel(scores_us, scores_os)

# Print the results
print(f"T-statistic: {t_statistic}")
print(f"P-value: {p_value}")

# Interpret the results
if p_value < 0.05:
    print("The difference between the two samples is statistically significant.")
else:
    print("There is no significant difference between the two samples.")
```

## Conclusion

In this guide, we explored techniques for handling imbalanced datasets using under-sampling and over-sampling. We applied these methods to a real-world dataset and evaluated their impact on model performance. The two-sample t-test provided a statistical assessment of the differences in F1 scores between the under-sampling and over-sampling approaches. Understanding and addressing imbalanced datasets are crucial steps towards building more robust and unbiased machine learning models.

## Note
The following equations describe the process of conducting a t-test for two independent samples, where \(d\) represents the difference between paired observations. Here's an explanation for each equation:

1. **Mean of Differences (\\(\bar{d}\\)):**
   \\[
   \bar{d} = \frac{\sum d_i}{n}
   \\]
   This equation calculates the average difference (\\(\bar{d}\\)) between paired observations. It involves summing up all the differences (\\(d_i\\)) and dividing by the number of pairs (\\(n\\)).

2. **Standard Deviation of Differences (\\(s_d\\)):**
   \\[
   s_d = \sqrt{\frac{\sum\left(d_i-\bar{d}\right)^2}{n-1}}
   \\]
   \\(s_d\\) represents the standard deviation of the differences. It is computed by taking the square root of the sum of squared deviations from the mean difference, divided by \(n-1\) (for sample standard deviation).

3. **T-statistic (\\(t\\)):**
   \\[
   t = \frac{\bar{d}-\mu_d}{s_d / \sqrt{n}}
   \\]
   The t-statistic measures how many standard deviations the sample mean difference (\(\bar{d}\)) is from the hypothesized population mean difference (\\(\mu_d\\)). It is calculated by dividing the difference between \\(\bar{d}\\) and \\(\mu_d\\) by the standard error of the mean difference (\\(s_d / \sqrt{n}\\)).

4. **Alternative T-statistic (\\(t\\)):**
   
\\[
   t = \frac{\bar{x_1} - \bar{x_2}} {\text{var}(x_{1} - x_{2}) / n}
   \\]
   Alternatively, you can compute the t-statistic directly using the sample means (\\(\bar{x_1}\\) and \\(\bar{x_2}\\)) and the variance of the differences (\\(\text{var}(x_{1} - x_{2})\\)) divided by \\(n\\).

These equations are fundamental in hypothesis testing to determine if the means of two independent samples are significantly different.

Once you have calculated the t-statistic, the next step is to determine whether it is significant. The significance of the t-statistic is typically assessed by comparing it to a critical value from the t-distribution or by calculating a p-value.

### Using Critical Values:

1. **Determine Degrees of Freedom (\\(df\\)):**
   The degrees of freedom for the t-distribution in a two-sample t-test is given by \\(df = n_1 + n_2 - 2\\), where \\(n_1\\) and \\(n_2\\) are the sample sizes.

2. **Find Critical Value:**
   Look up the critical value for your chosen significance level (e.g., 0.05) and degrees of freedom in the t-distribution table. The critical value corresponds to the point beyond which you would reject the null hypothesis.

3. **Compare t-statistic and Critical Value:**
   If the absolute value of the t-statistic is greater than the critical value, you reject the null hypothesis. The greater the difference between the t-statistic and the critical value, the stronger the evidence against the null hypothesis.

### Using P-Value:

1. **Calculate P-Value:**
   Use the t-statistic and the degrees of freedom to calculate the p-value. The p-value represents the probability of observing a t-statistic as extreme as, or more extreme than, the one obtained, assuming the null hypothesis is true.

2. **Compare P-Value and Significance Level:**
   Compare the p-value to your chosen significance level (e.g., 0.05). If the p-value is less than or equal to the significance level, you reject the null hypothesis. A smaller p-value indicates stronger evidence against the null hypothesis.

### Decision:

- **Reject Null Hypothesis:**
  - If t-statistic > Critical Value (or) P-Value ? Significance Level
  - Conclude that there is sufficient evidence to reject the null hypothesis.

- **Fail to Reject Null Hypothesis:**
  - If t-statistic $$\leq$$ Critical Value (or) P-Value > Significance Level
  - Conclude that there is not enough evidence to reject the null hypothesis.

In summary, the decision to reject or fail to reject the null hypothesis is based on comparing the t-statistic to critical values or using p-values, depending on the chosen approach.


