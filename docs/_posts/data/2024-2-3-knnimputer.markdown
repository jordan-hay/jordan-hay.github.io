---
layout: post
title:  "Imputing Missing Data with K-Nearest Neighbors Algorithm
"
date:   2024-2-3 07:25:17 -0800
categories: jekyll update data
---

# Introduction

Missing data is a common challenge in real-world datasets, and handling it appropriately is crucial for building robust machine learning models. In this blog post, we'll explore how to use the K-Nearest Neighbors (KNN) algorithm to impute missing values in a dataset. We'll implement this using Python and popular libraries such as NumPy, Pandas, Seaborn, and Scikit-Learn.

## Understanding the Problem

Let's start by loading our dataset and examining its structure:

```python
import numpy as np
import seaborn as sns
import pandas as pd
from sklearn.neighbors import KNeighborsClassifier
from sklearn.preprocessing import LabelEncoder

# Load the dataset
import gdown
gdown.download('https://github.com/stedy/Machine-Learning-with-R-datasets/raw/master/usedcars.csv','file.csv',quiet=True)
data = pd.read_csv('file.csv')
data_orig = data.copy()

# Display the first few rows of the dataset
data.head()
```

## Introducing Missing Data

To simulate missing data, we'll randomly set a fraction of cells to be missing. In this example, we set 5% of the data as missing:

```python
# Set a random seed for reproducibility
np.random.seed(42)

# Define the fraction of cells with missing data (e.g., 0.05 for 5% missing data)
missing_fraction = 0.05

# Calculate the number of cells to be set as missing
total_cells = data.size
num_missing = int(total_cells * missing_fraction)

# Generate random indices for missing data cells
missing_indices = np.random.choice(total_cells, num_missing, replace=False)

# Determine the row and column indices from the flattened DataFrame
num_rows, num_columns = data.shape
row_indices = missing_indices // num_columns
column_indices = missing_indices % num_columns

# Introduce missing data
for row, col in zip(row_indices, column_indices):
    data.iat[row, col] = np.nan

# Display the first 30 rows of the dataset with missing values
data.head(30)
```

## Imputing Missing Data with K-Nearest Neighbors

Now, let's use the KNN algorithm to impute the missing values. We'll iterate through each column with missing values and predict the missing values using the KNN classifier:

```python
data_missing = data.copy()

label_encoder = LabelEncoder()
knn_classifier = KNeighborsClassifier(n_neighbors=3)

# Iterate through each column with missing values
for column in data.columns:
    missing_mask = data[column].isnull()
    if missing_mask.any():
        # Split the dataset into features (X) and targets (y)
        X_all = pd.get_dummies(data.drop(columns=[column]))
        y = data.loc[~missing_mask, column]

        # Fit the KNN classifier on the non-missing data
        knn_classifier.fit(X_all.loc[~missing_mask].fillna(-1), y)

        # Extract features for missing values
        X_miss = pd.get_dummies(X_all.loc[missing_mask])

        # Predict missing values and fill them in
        imputed_values = knn_classifier.predict(X_miss.fillna(-1))
        data.loc[missing_mask, column] = imputed_values

# Display the first 30 rows of the dataset after imputation
data.head(30)
```

## Visualizing Imputation Results

We can visualize the imputation results using a heatmap to highlight the imputed values:

```python
# Visualize missing values after imputation
sns.heatmap(data.isna(), vmin=0, vmax=1)
```

## Comparing Imputed Values with Original Data

Finally, let's compare the imputed values with the original data:

```python
# Extract original, missing, and imputed values
missing_data = [data_missing.iloc[el[0], el[1]] for el in zip(row_indices, column_indices)]
filled_data = [data.iloc[el[0], el[1]] for el in zip(row_indices, column_indices)]
orig_data = [data_orig.iloc[el[0], el[1]] for el in zip(row_indices, column_indices)]
cols = [data_orig.columns[col] for col in column_indices]

# Create a DataFrame to display the comparison
comparison_df = pd.DataFrame(zip(cols, orig_data, missing_data, filled_data),
                             columns=['Feature', 'Original', 'Missing', 'Imputed'])
```

Now, `comparison_df` contains a comparison between the original, missing, and imputed values for the selected features. This can provide insights into the effectiveness of the imputation process.

In conclusion, using the K-Nearest Neighbors algorithm for imputing missing data is a powerful technique that leverages the similarity between data points to fill in the gaps. It's important to experiment with different values of `n_neighbors` and handle categorical features appropriately for optimal results.

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="8726573b-cb20-44dc-a9b1-48964e40f337" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("8726573b-cb20-44dc-a9b1-48964e40f337")) {                    Plotly.newPlot(                        "8726573b-cb20-44dc-a9b1-48964e40f337",                        [{"cells":{"align":"left","fill":{"color":"lavender"},"values":[["color","transmission","mileage","year","mileage","transmission","transmission","price","year","price","model","transmission","mileage","year","mileage","price","year","price","mileage","model","model","mileage","color","mileage","price","price","year","mileage","color","year","price","year","color","mileage","mileage","mileage","transmission","model","transmission","transmission","mileage","transmission","color","year","color"],["Silver","AUTO",28955,2009,27393,"AUTO","AUTO",15992,2011,16000,"SEL","AUTO",68901,2010,77231,12507,2010,13799,33302,"SES","SEL",78948,"Red",13541,12992,13995,2010,59013,"Silver",2009,14549,2008,"Red",53902,36124,69415,"AUTO","SE","AUTO","AUTO",40539,"AUTO","Gray",2006,"Red"],[null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null],["Black","AUTO",11165.0,2009.0,21026.0,"AUTO","AUTO",14893.0,2010.0,13997.0,"SE","AUTO",70036.0,2010.0,40330.0,12990.0,2010.0,7995.0,27528.0,"SE","SE",51311.0,"Black",15367.0,13992.0,12500.0,2009.0,86862.0,"Red",2009.0,12998.0,2007.0,"Black",32743.0,32559.0,42834.0,"AUTO","SES","AUTO","AUTO",21026.0,"AUTO","Black",2006.0,"Black"]]},"header":{"align":"left","fill":{"color":"paleturquoise"},"values":["Feature","Original","Missing","Imputed"]},"type":"table"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}}},                        {"responsive": true}                    )                };                            </script>        </div>