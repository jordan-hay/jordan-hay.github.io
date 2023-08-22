---
layout: post
title:  "Visualizing Financial Flows: Unraveling a Rental Property's Cash Flow with Plotly Sankey Diagrams"
date:   2023-08-22 06:25:17 -0800
categories: jekyll update
---

In the realm of data visualization, there's a potent tool that possesses the capability to elegantly portray intricate relationships and flows - the Plotly Sankey diagram. This unique visualization method excels at illustrating the movement of resources, values, or quantities as they traverse through interconnected pathways. Today, let's delve into the captivating realm of Plotly Sankey diagrams using a concrete example.

Consider a scenario where you're a real estate investor trying to understand the financial breakdown of a rental property. You have various income streams and expenses, and you want to visualize how they all contribute to your overall profit. This is where the Plotly Sankey diagram comes into play.

To add depth to our understanding, let's integrate a data table into our exploration:

| lvl1 | lvl2 | lvl3           | Count |
|------|------|----------------|-------|
| Rent |      | Profit         | 19559 |
| Rent | PITI | Property Taxes | 8145  |
| Rent | PITI | Home Insurance | 3383  |
| Rent | PITI | Principal      | 2800  |
| Rent | PITI | Interest       | 14681 |
| Rent | Other Costs | Management Costs | 2769  |
| Rent | Other Costs | Vacancy    | 2868  |
| Rent | Other Costs | Repairs    | 2795  |
| Rent | Other Costs | Maintenance| 3000  |

The table provides a hierarchical view of your financial data, showing different levels of categorization for the flows. For example, you have "Profit" as well as "PITI" (Principal, Interest, Taxes, and Insurance). Under "PITI," you have "Property Taxes," "Home Insurance," "Principal," and "Interest." Similarly, "Other Costs" are categorized into "Management Costs," "Vacancy," "Repairs," and "Maintenance."

The foundation of this visualization journey is rooted in structured data:

```python
[
    ['Rent', 'Profit', 19559.0],
    ['Rent', 'PITI', 8145.0],
    ['PITI', 'Property Taxes', 8145.0],
    ['Rent', 'PITI', 3383.0],
    ['PITI', 'Home Insurance', 3383.0],
    ['Rent', 'PITI', 2800.0],
    ['PITI', 'Principal', 2800.0],
    ['Rent', 'PITI', 14681.0],
    ['PITI', 'Interest', 14681.0],
    ['Rent', 'Other Costs', 2769.0],
    ['Other Costs', 'Management Costs', 2769.0],
    ['Rent', 'Other Costs', 2868.0],
    ['Other Costs', 'Vacancy', 2868.0],
    ['Rent', 'Other Costs', 2795.0],
    ['Other Costs', 'Repairs', 2795.0],
    ['Rent', 'Other Costs', 3000.0],
    ['Other Costs', 'Maintenance', 3000.0]
]
```




```python
categories = ['Rent', 'PITI', 'Other Costs', 'Profit', 'Property Taxes', 'Home Insurance', 'Principal', 'Interest', 'Management Costs', 'Vacancy', 'Repairs', 'Maintenance']
source_indices = [0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 2, 0, 2, 0, 2, 0, 2]
target_indices = [3, 1, 4, 1, 5, 1, 6, 1, 7, 2, 8, 2, 9, 2, 10, 2, 11]
values = [19559.0, 8145.0, 8145.0, 3383.0, 3383.0, 2800.0, 2800.0, 14681.0, 14681.0, 2769.0, 2769.0, 2868.0, 2868.0, 2795.0, 2795.0, 3000.0, 3000.0]
```

These data encapsulate the essence of your rental property's financial landscape. Each category, such as "Rent," "PITI," and "Other Costs," serves as a fundamental node, linked by flows represented by the provided indices and values.

Transforming this data into a Plotly Sankey diagram involves leveraging Python code:

```python
import plotly.graph_objects as go

# Create a Sankey diagram trace
trace = go.Sankey(
    node=dict(
        pad=15,
        thickness=20,
        line=dict(color="black", width=0.5),
        label=categories
    ),
    link=dict(
        source=source_indices,
        target=target_indices,
        value=values
    )
)

# Create a figure
fig = go.Figure(trace)

fig.update_layout(
    title="Real Estate Cash Flow"
)

# Show the figure
fig.show()
```

This code is a blueprint to transform your data into a captivating visualization. By executing it, you craft a Sankey diagram that artfully delineates how income from "Rent" channels into "Profit," or how "PITI" branches into "Principal," "Interest," "Property Taxes," and "Home Insurance." Each flow's width mirrors the value's magnitude, enabling swift comprehension of financial dynamics.

Here's how your provided data translates into a Plotly Sankey diagram:

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="65ca4955-ee3d-4229-aaea-3176c4907428" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("65ca4955-ee3d-4229-aaea-3176c4907428")) {                    Plotly.newPlot(                        "65ca4955-ee3d-4229-aaea-3176c4907428",                        [{"link":{"source":[0,0,1,0,1,0,1,0,1,0,2,0,2,0,2,0,2],"target":[3,1,4,1,5,1,6,1,7,2,8,2,9,2,10,2,11],"value":[19559.0,8145.0,8145.0,3383.0,3383.0,2800.0,2800.0,14681.0,14681.0,2769.0,2769.0,2868.0,2868.0,2795.0,2795.0,3000.0,3000.0]},"node":{"label":["Rent","PITI","Other Costs","Profit","Property Taxes","Home Insurance","Principal","Interest","Management Costs","Vacancy","Repairs","Maintenance"],"line":{"color":"black","width":0.5},"pad":15,"thickness":20},"type":"sankey"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"title":{"text":"Real Estate Cash Flow"}},                        {"responsive": true}                    )                };                            </script>        </div>


Incorporating this visual masterpiece and the accompanied data table into your analysis, you can unravel the intricate financial tapestry of your rental property. The Sankey diagram shines a light on your income sources, expense destinations, and the myriad pathways that connect them.

In conclusion, the Plotly Sankey diagram stands as a powerful ally in unraveling intricate financial flows within datasets. It breathes life into complex relationships, offering insights that evade traditional charts. So, whether deciphering financial data, untangling supply chain intricacies, or exploring resource allocation, remember the Plotly Sankey diagram's prowess. It may be the key to unlocking revelations that lie hidden within your data.

