---
layout: post
title:  "Linear Regression: Exploring Quadratic Least Squares Optimization with Gurobipy"
date:   2024-1-2 06:25:17 -0800
categories: jekyll update data
---

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="6d27e3fb-3cbe-4796-8431-70a73c1d4d5f" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("6d27e3fb-3cbe-4796-8431-70a73c1d4d5f")) {                    Plotly.newPlot(                        "6d27e3fb-3cbe-4796-8431-70a73c1d4d5f",                        [{"hovertemplate":"X=%{x}\u003cbr\u003ey=%{y}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":"blue","symbol":"circle"},"mode":"markers","name":"Actual (y)","orientation":"v","showlegend":false,"x":[0.9878815626061143,0.8586392717444565,0.4881504758595939,0.5860416364893802,0.9476173162873508,0.2840714711931782,0.2374676328515889,0.5101955995099972,0.5140943067409424,0.868538309282994,0.44480754802641864,0.8382192263440047,0.3893526302287973,0.2481745376688509,0.22789597443881504,0.558393426399411,0.8281535093152781,0.3706758669868059,0.591931889716399,0.6952410617658505,0.9305617285040494,0.167090772212503,0.16334815365244892,0.15557159945585075,0.7073542185199545,0.10574181878673916,0.9034803073440424,0.31948849832384674,0.5103728922268073,0.04948409580961233,0.44806453107772903,0.6227932865536052,0.578133122209726,0.14188225485163242,0.8240624804281149,0.10537089723277959,0.1126046243179809,0.6431436983638777,0.057163689836169596,0.43426899483272396],"xaxis":"x","y":[0.8262935771545186,-0.6942476999995896,1.5936247061820457,-0.44731840699962794,-0.6008382066626708,-1.1372870159337414,-0.39714133091094594,0.821987020980484,0.5820255143550546,-0.8553204972470373,-1.192981219449443,-0.5631905269207241,-0.5050422640757323,-2.493191317673965,-1.2086884427449176,0.8987889821092869,0.38833939902253456,0.13989957521509153,-0.24877828136380042,-0.24542487361991214,0.8644792467420136,-0.3658811743284728,-1.3928715030705967,1.7178026867145886,-1.8878974332792269,-0.1870562260499175,0.6449570361652639,0.2624124705876247,-0.2769655073404999,-1.5121536424366409,0.40174272698805247,1.5953155133027574,-0.37236692706616636,-0.13411187622758658,2.187630703476166,-0.586796575023825,-0.8630073616017592,1.058767188260707,0.3238551035933914,0.27229376692316487],"yaxis":"y","type":"scatter"},{"line":{"color":"red"},"mode":"lines","name":"Predicted (y_hat)","x":[0.9878815626061143,0.8586392717444565,0.4881504758595939,0.5860416364893802,0.9476173162873508,0.2840714711931782,0.2374676328515889,0.5101955995099972,0.5140943067409424,0.868538309282994,0.44480754802641864,0.8382192263440047,0.3893526302287973,0.2481745376688509,0.22789597443881504,0.558393426399411,0.8281535093152781,0.3706758669868059,0.591931889716399,0.6952410617658505,0.9305617285040494,0.167090772212503,0.16334815365244892,0.15557159945585075,0.7073542185199545,0.10574181878673916,0.9034803073440424,0.31948849832384674,0.5103728922268073,0.04948409580961233,0.44806453107772903,0.6227932865536052,0.578133122209726,0.14188225485163242,0.8240624804281149,0.10537089723277959,0.1126046243179809,0.6431436983638777,0.057163689836169596,0.43426899483272396],"y":[0.41870749942129104,0.2876811424020981,-0.0879218968010888,0.011320557632274464,0.3778874437096651,-0.2948180168502591,-0.3420651765864333,-0.06557246131296468,-0.06161993615924444,0.297716826681783,-0.13186313227954116,0.26697921781418066,-0.18808355215432343,-0.33121047319326347,-0.3517689625847821,-0.016709309542299766,0.2567745531934348,-0.20701813024167381,0.017292120168897473,0.12202737648525275,0.3605964198569611,-0.41341352244527724,-0.417207804273361,-0.4250917063595075,0.1343077437776553,-0.47560933947023454,0.333141165591185,-0.258912091549471,-0.06539272123984474,-0.5326436464818468,-0.12856118969371028,0.048579529059158855,0.003302873880393742,-0.43897001926709156,0.2526270515670589,-0.47598538124132356,-0.4686517994754329,0.06921085883181477,-0.5248580430081105,-0.14254716011607071],"type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"X"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"y"}},"legend":{"tracegroupgap":0,"x":0,"y":1,"traceorder":"normal","orientation":"h"},"margin":{"t":60}},                        {"responsive": true}                    )                };                            </script>        </div>


**Introduction:**
Linear regression is a fundamental technique in statistics and machine learning for modeling the relationship between a dependent variable and one or more independent variables. In this blog post, we'll explore how to use the Gurobi optimization library to perform linear regression, comparing the results with the popular scikit-learn implementation.

**Installing Gurobi:**
To get started, ensure you have Gurobi installed by running the following command in your Python environment:
```bash
!pip install gurobipy &> /dev/null
```

**Setting up the Problem:**
Let's generate some random data for our linear regression problem. We'll create a dataset with 40 examples and 3 features, including a bias term. The dependent variable `y` is a random vector.

```python
import gurobipy as gp
import numpy as np
from gurobipy import GRB

m = 40  # number of examples
n = 3   # number of features
X = np.random.rand(m, n)
X = np.hstack((np.ones((m, 1)), X))  # add a ones column

y = np.random.randn(m, 1)
```

**Building the Gurobi Model:**
Now, let's set up the Gurobi optimization model. We create a linear regression model and define the objective function, which is the least squares loss. The model is then optimized.

```python
model = gp.Model()
beta = model.addMVar(shape=n + 1, vtype=GRB.CONTINUOUS, lb=float('-inf'))

obj = y.T @ y - 2 * beta.T @ X.T @ y + beta.T @ X.T @ X @ beta

model.setObjective(obj, GRB.MINIMIZE)
model.optimize()
```

**Displaying Gurobi Results:**
After optimization, we can display the coefficients of our linear regression model.

```python
display(beta.X.tolist())
```

**Scikit-learn Comparison:**
Next, we compare the Gurobi results with scikit-learn's linear regression implementation.

```python
from sklearn.linear_model import LinearRegression

clf = LinearRegression()
clf.fit(X[:, 1:], y)
parameters = [clf.intercept_[0]] + clf.coef_.flatten().tolist()
display(parameters)
```

**Visualizing the Results:**
Finally, let's visualize the actual vs. predicted values using matplotlib.

```python
import matplotlib.pyplot as plt

plt.scatter(X[:, 1:].mean(axis=1), y, label='Actual (y)')
plt.plot(X[:, 1:].mean(axis=1), X @ np.asarray(parameters), c='red', label='Predicted (y_hat)')
plt.legend(loc='lower right')
plt.show()
```

**Conclusion:**
In this blog post, we've explored how to implement linear regression using the Gurobi optimization library and compared the results with scikit-learn. Gurobi provides a powerful tool for optimization problems, and its use extends beyond linear regression to more complex models and scenarios.

**Appendix: Derivation and Interpretation of the Linear Regression Objective Function**

The expression \\( (y - X B)^T (y - X B) \\) encapsulates the squared residual sum in the context of linear regression. In this section, we will delve into the derivation and interpretation of this expression.

The linear regression objective function, denoted as \\( J(B) \\), is conventionally defined as the sum of squared residuals:

\\[ J(B) = (y - X B)^T (y - X B) \\]

Here, \\( J(B) \\) signifies the objective function to be minimized, \\( B \\) is the vector of coefficients, \\( X \\) is the input matrix, and \\( y \\) is the target vector.

Let's dissect the expression \\( (y - X B)^T (y - X B) \\) step by step:

\\[ (y - X B)^T (y - X B) = (y^T - B^T X^T) (y - X B) \\]

Expanding the product:

\\[ y^T y - y^T X B - B^T X^T y + B^T X^T X B \\]

Rearranging the terms:

\\[ y^T y - 2 B^T X^T y + B^T X^T X B \\]

This expression precisely corresponds to the sum of squared residuals. When employed as the objective function in linear regression, the objective is to minimize this quantity. The optimal coefficients \\( B \\) are obtained by differentiating \\( J(B) \\) with respect to \\( B \\), setting the result to zero, and solving for \\( B \\).

In the context of the provided Gurobi code snippet:

```python
obj = y.T @ y + (-2 * y.T @ X) @ beta + beta @ (X.T @ X) @ beta
```

The term \\( (y - X B)^T (y - X B) \\) is represented as \\( y^T y - 2 B^T X^T y + B^T X^T X B \\). Gurobi is utilized to determine the values of \\( B \\) that minimize this objective function, aligning with the fundamental principles of linear regression optimization.

The optimization problem represented by the objective function \\( (y - X B)^T (y - X B) \\) in the context of linear regression is a **quadratic optimization problem**. Specifically, it is a **quadratic least squares optimization problem**.

In a quadratic optimization problem, the objective function is quadratic, and the goal is to find the values of the decision variables (in this case, the coefficients \\( B \\)) that minimize or maximize the quadratic expression subject to any constraints.

In the given linear regression objective function, the term \\( (y - X B)^T (y - X B) \\) is a quadratic expression in terms of the coefficients \\( B \\). The optimization task is to adjust the values of \\( B \\) to minimize the sum of squared residuals, which is a fundamental objective in linear regression. 