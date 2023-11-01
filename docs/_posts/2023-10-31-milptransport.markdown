---
layout: post
title:  "Mixed-Integer Linear Programming for Transportation and Distribution Optimization"
date:   2023-10-31 06:25:17 -0800
categories: jekyll update
---

### Introduction:

In today's globalized world, efficient transportation plays a crucial role in ensuring that school supplies reach educational institutions reliably and cost-effectively. This blog post introduces a transportation optimization problem that addresses the supply of school supplies kits from four U.S. cities to four Asian cities and eight schools. We'll delve into the code that models and solves this optimization problem using Gurobi, a powerful optimization tool.

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="40b68a8a-12ab-4a59-a887-d82253c3e7dd" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("40b68a8a-12ab-4a59-a887-d82253c3e7dd")) {                    Plotly.newPlot(                        "40b68a8a-12ab-4a59-a887-d82253c3e7dd",                        [{"hovertemplate":"School=School1\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School1","marker":{"color":"#636efa","symbol":"circle"},"mode":"markers","name":"School1","scene":"scene","showlegend":true,"x":["Los Angeles","Los Angeles","Houston"],"y":["Tokyo","Bangkok","Tokyo"],"z":[76,62,58],"type":"scatter3d"},{"hovertemplate":"School=School3\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School3","marker":{"color":"#EF553B","symbol":"circle"},"mode":"markers","name":"School3","scene":"scene","showlegend":true,"x":["Los Angeles","Houston","Miami"],"y":["Tokyo","Tokyo","Tokyo"],"z":[125,125,116],"type":"scatter3d"},{"hovertemplate":"School=School2\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School2","marker":{"color":"#00cc96","symbol":"circle"},"mode":"markers","name":"School2","scene":"scene","showlegend":true,"x":["Los Angeles","Chicago","Miami"],"y":["Seoul","Seoul","Seoul"],"z":[49,88,37],"type":"scatter3d"},{"hovertemplate":"School=School4\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School4","marker":{"color":"#ab63fa","symbol":"circle"},"mode":"markers","name":"School4","scene":"scene","showlegend":true,"x":["Los Angeles","Houston","Miami"],"y":["Bangkok","Bangkok","Beijing"],"z":[125,125,39],"type":"scatter3d"},{"hovertemplate":"School=School8\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School8","marker":{"color":"#FFA15A","symbol":"circle"},"mode":"markers","name":"School8","scene":"scene","showlegend":true,"x":["Los Angeles","Houston","Houston","Miami"],"y":["Bangkok","Beijing","Bangkok","Beijing"],"z":[63,78,39,53],"type":"scatter3d"},{"hovertemplate":"School=School7\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School7","marker":{"color":"#19d3f3","symbol":"circle"},"mode":"markers","name":"School7","scene":"scene","showlegend":true,"x":["Chicago","Miami"],"y":["Beijing","Beijing"],"z":[125,105],"type":"scatter3d"},{"hovertemplate":"School=School5\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School5","marker":{"color":"#FF6692","symbol":"circle"},"mode":"markers","name":"School5","scene":"scene","showlegend":true,"x":["Chicago"],"y":["Seoul"],"z":[85],"type":"scatter3d"},{"hovertemplate":"School=School6\u003cbr\u003eUS City=%{x}\u003cbr\u003eAsian City=%{y}\u003cbr\u003eKits Shipped=%{z}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"School6","marker":{"color":"#B6E880","symbol":"circle"},"mode":"markers","name":"School6","scene":"scene","showlegend":true,"x":["Chicago"],"y":["Seoul"],"z":[77],"type":"scatter3d"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"scene":{"domain":{"x":[0.0,1.0],"y":[0.0,1.0]},"xaxis":{"title":{"text":"US City"}},"yaxis":{"title":{"text":"Asian City"}},"zaxis":{"title":{"text":"Kits Shipped"}}},"legend":{"title":{"text":"School"},"tracegroupgap":0},"title":{"text":"Optimal Kit Shipments from U.S. Cities to Asian Cities and Schools"},"barmode":"stack"},                        {"responsive": true}                    )                };                            </script>        </div>

### Setting the Stage

Before we dive into the code, let's understand the problem at hand. We have the following key components:

**Sets:**
- **I**: U.S. cities (Los Angeles, Chicago, Houston, Miami)
- **J**: Asian cities (Tokyo, Beijing, Seoul, Bangkok)
- **K**: Schools (School1, School2, School3, School4, School5, School6, School7, School8)

**Parameters:**
- **Cost Matrix (c)**: The cost of shipping from each U.S. city to each Asian city.
- **Quality Values (q)**: The quality ratings for each U.S. city.
- **Cost Matrix (p)**: The cost of shipping from each Asian city to each school.
- **Supply (s)**: The supply of school supply kits in each U.S. city.
- **Demand (d)**: The demand for school supply kits in each Asian city.
- **School Requirements (r)**: The required kits for each school.
- **Freight Size Limit (L)**: The maximum freight size.
- **Capacity Constraint (N)**: Capacity constraint for each U.S. city to Asian cities.

### Model Definition

The core of our optimization problem is defined in the code using Gurobi:

```python
# Define the Gurobi model
model = gp.Model('SchoolSuppliesKitTransport')

# Define the decision variables
x = {}
for i in I:
    for j in J:
        for k in K:
            x[i, j, k] = model.addVar(lb=0, vtype=gp.GRB.INTEGER, name=f'x_{i}_{j}_{k}')

# Update the model to include the variables
model.update()

# Set the objective function
model.setObjective(gp.quicksum((c[I.index(i), J.index(j)]  + p[J.index(j), K.index(k)]) * x[i, j, k] for i in I for j in J for k in K), gp.GRB.MINIMIZE)
```

In this model, we define decision variables, set the objective function to minimize the total cost of transportation, and add constraints for supply, capacity, and quality. Here's a breakdown of these constraints:

### Constraints

1. **Supply Constraints:**

```python
for i in I:
    model.addConstr(gp.quicksum(x[i, j, k] for j in J for k in K) == s[i], name=f'Supply_{i}')
```

These constraints ensure that the supply of kits from U.S. cities is met.

2. **Capacity Constraints:**

```python
for j in J:
    model.addConstr(gp.quicksum(x[i, j, k] for i in I for k in K) <= d[j], name=f'Capacity_{j}')
```

These constraints guarantee that demand in Asian cities does not exceed their capacity.

3. **Maximum Kits from U.S. to Asian Locations Constraint:**

```python
for i in I:
    for j in J:
        model.addConstr(gp.quicksum(x[i, j, k] for k in K) <= N, name=f'MaxKits_US_{i}_{j}')
```

These constraints limit the number of kits transported from U.S. cities to Asian cities.

4. **Minimum Capacity Usage Constraint:**

```python
for j in J:
    model.addConstr(gp.quicksum(x[i, j, k] for i in I for k in K) >= 0.8 * d[j], name=f'MinCapacity_{j}')
```

These constraints ensure that Asian cities utilize at least 80% of their capacity.

5. **Maximum Kits to Schools Constraint:**

```python
for i in I:
    for j in J:
        for k in K:
            model.addConstr(x[i, j, k] <= L, name=f'MaxKits_{i}_{j}_{k}')
```

These constraints set a limit on the number of kits that can be transported to each school.

6. **Minimum Kits to Schools Constraint:**

```python
for k in K:
    model.addConstr(gp.quicksum(x[i, j, k] for i in I for j in J) >= 0.85 * r[k], name=f'MinKits_{k}')
```

These constraints ensure that at least 85% of each school's requirements are met.

7. **Quality Constraints:**

```python
for j in J:
    model.addConstr(
        gp.quicksum(x[i, j, k] * q[i] for i in I for k in K) >= 8.55 * gp.quicksum(x[i, j, k]  for i in I for k in K),
        name=f'Quality_{j}'
    )
```

These constraints take quality into account, ensuring that the weighted quality exceeds a certain threshold for each Asian city.

### Solving and Printing Results

Finally, we solve the optimization model and print the results:

```python
# Solve the optimization model
model.optimize()

# Print the results
if model.status == gp.GRB.OPTIMAL:
    print("Optimal Solution Found:")
    for i in I:
        for j in J:
            for k in K:
                quantity = x[i, j, k].x
                if quantity > 0:
                    print(f'Ship {quantity} kits from {i} to {j} to {k}')
    print(f'Total Cost: ${model.objVal}')
else:
    print("No optimal solution found.")
```

The code finds the optimal solution and displays the transportation plan and total cost.


### Analyzing the Optimal Solution

After running the optimization model, the output reveals an "Optimal Solution Found." This means that the model has successfully determined the most cost-efficient way to distribute school supply kits from U.S. cities to Asian cities and schools. Let's delve into the details of this optimal solution and understand the implications of the transportation plan:

1. **Optimal Kit Shipments:**

   - From Los Angeles:
     - 76 kits are shipped to Tokyo, specifically to School1.
     - 125 kits are shipped to Tokyo, specifically to School3.
     - 49 kits are shipped to Seoul, specifically to School2.
     - 62 kits are shipped to Bangkok, specifically to School1.
     - 125 kits are shipped to Bangkok, specifically to School4.
     - 63 kits are shipped to Bangkok, specifically to School8.

   - From Chicago:
     - 125 kits are shipped to Beijing, specifically to School7.
     - 88 kits are shipped to Seoul, specifically to School2.
     - 85 kits are shipped to Seoul, specifically to School5.
     - 77 kits are shipped to Seoul, specifically to School6.

   - From Houston:
     - 58 kits are shipped to Tokyo, specifically to School1.
     - 125 kits are shipped to Tokyo, specifically to School3.
     - 78 kits are shipped to Beijing, specifically to School8.
     - 125 kits are shipped to Bangkok, specifically to School4.
     - 39 kits are shipped to Bangkok, specifically to School8.

   - From Miami:
     - 116 kits are shipped to Tokyo, specifically to School3.
     - 39 kits are shipped to Beijing, specifically to School4.
     - 105 kits are shipped to Beijing, specifically to School7.
     - 53 kits are shipped to Beijing, specifically to School8.
     - 37 kits are shipped to Seoul, specifically to School2.

2. **Total Cost: $15,960.90**

   The total cost associated with this optimal distribution plan is approximately $15,960.90. This represents the minimum cost required to meet the supply and demand while adhering to the constraints set in the model.

#### Key Takeaways

- The optimal solution ensures that all supply and demand requirements are met, taking into account various constraints such as capacity, quality, and kit size limits.

- The model has effectively allocated kits from U.S. cities to Asian cities and schools in a way that minimizes the overall transportation cost.

- By considering the quality constraints, the solution aims to ensure that the transported kits meet certain quality standards, which is an important aspect of the problem.

- The transportation plan can guide real-world decision-making in terms of logistics and supply chain management, helping organizations minimize costs and optimize their distribution processes.

In conclusion, the optimal solution found in this transportation and distribution problem is not only cost-effective but also ensures that school supply kits reach their intended destinations efficiently, meeting both supply and demand while considering quality and capacity constraints. This demonstrates the power of mixed-integer linear programming in solving complex logistics and supply chain optimization challenges.

#### Output From Python

```python
Optimal Solution Found:
Ship 76.0 kits from Los Angeles to Tokyo to School1
Ship 125.0 kits from Los Angeles to Tokyo to School3
Ship 49.0 kits from Los Angeles to Seoul to School2
Ship 62.0 kits from Los Angeles to Bangkok to School1
Ship 125.0 kits from Los Angeles to Bangkok to School4
Ship 63.0 kits from Los Angeles to Bangkok to School8
Ship 125.0 kits from Chicago to Beijing to School7
Ship 88.0 kits from Chicago to Seoul to School2
Ship 85.0 kits from Chicago to Seoul to School5
Ship 77.0 kits from Chicago to Seoul to School6
Ship 58.0 kits from Houston to Tokyo to School1
Ship 125.0 kits from Houston to Tokyo to School3
Ship 78.0 kits from Houston to Beijing to School8
Ship 125.0 kits from Houston to Bangkok to School4
Ship 39.0 kits from Houston to Bangkok to School8
Ship 116.0 kits from Miami to Tokyo to School3
Ship 39.0 kits from Miami to Beijing to School4
Ship 105.0 kits from Miami to Beijing to School7
Ship 53.0 kits from Miami to Beijing to School8
Ship 37.0 kits from Miami to Seoul to School2
Total Cost: $15960.90
```

### Conclusion

Optimizing school supplies kit transportation involves balancing cost, quality, and various constraints. With Gurobi, we can efficiently model and solve such complex transportation problems. By using this code as a template, we can adapt it to address similar supply chain optimization challenges in various real-world scenarios.