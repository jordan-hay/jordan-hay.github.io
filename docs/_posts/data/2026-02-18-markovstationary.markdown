---
layout: post
title:  "Understanding the Stationary Distribution in Markov Chains"
date:   2026-02-18 09:25:17 -0800
categories: jekyll update data
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Understanding_the_Stationary_Distribution_in_Markov_Chains.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="8cc3cb67-a346-4374-8e74-2c24ee608d8d" class="plotly-graph-div" style="height:900px; width:1300px;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("8cc3cb67-a346-4374-8e74-2c24ee608d8d")) {                    Plotly.newPlot(                        "8cc3cb67-a346-4374-8e74-2c24ee608d8d",                        [{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S1 → S1\u003cbr\u003eP=0.20"],"x":[1.0,1.0],"y":[0.0,0.0],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":3.4},"mode":"lines","opacity":0.8,"showlegend":false,"text":["S1 → S2\u003cbr\u003eP=0.30"],"x":[1.0,0.3090169521873281],"y":[0.0,0.9510565683560541],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":1.8},"mode":"lines","opacity":0.6,"showlegend":false,"text":["S1 → S3\u003cbr\u003eP=0.10"],"x":[1.0,-0.8090170564954595],"y":[0.0,0.587785261505403],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S1 → S4\u003cbr\u003eP=0.20"],"x":[1.0,-0.809016996890813],"y":[0.0,-0.5877853211100496],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S1 → S5\u003cbr\u003eP=0.20"],"x":[1.0,0.3090171011989445],"y":[0.0,-0.9510565087514076],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":1.8},"mode":"lines","opacity":0.6,"showlegend":false,"text":["S2 → S1\u003cbr\u003eP=0.10"],"x":[0.3090169521873281,1.0],"y":[0.9510565683560541,0.0],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":4.2},"mode":"lines","opacity":0.9,"showlegend":false,"text":["S2 → S2\u003cbr\u003eP=0.40"],"x":[0.3090169521873281,0.3090169521873281],"y":[0.9510565683560541,0.9510565683560541],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S2 → S3\u003cbr\u003eP=0.20"],"x":[0.3090169521873281,-0.8090170564954595],"y":[0.9510565683560541,0.587785261505403],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S2 → S4\u003cbr\u003eP=0.20"],"x":[0.3090169521873281,-0.809016996890813],"y":[0.9510565683560541,-0.5877853211100496],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":1.8},"mode":"lines","opacity":0.6,"showlegend":false,"text":["S2 → S5\u003cbr\u003eP=0.10"],"x":[0.3090169521873281,0.3090171011989445],"y":[0.9510565683560541,-0.9510565087514076],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":3.4},"mode":"lines","opacity":0.8,"showlegend":false,"text":["S3 → S1\u003cbr\u003eP=0.30"],"x":[-0.8090170564954595,1.0],"y":[0.587785261505403,0.0],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S3 → S2\u003cbr\u003eP=0.20"],"x":[-0.8090170564954595,0.3090169521873281],"y":[0.587785261505403,0.9510565683560541],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S3 → S3\u003cbr\u003eP=0.20"],"x":[-0.8090170564954595,-0.8090170564954595],"y":[0.587785261505403,0.587785261505403],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":1.8},"mode":"lines","opacity":0.6,"showlegend":false,"text":["S3 → S4\u003cbr\u003eP=0.10"],"x":[-0.8090170564954595,-0.809016996890813],"y":[0.587785261505403,-0.5877853211100496],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S3 → S5\u003cbr\u003eP=0.20"],"x":[-0.8090170564954595,0.3090171011989445],"y":[0.587785261505403,-0.9510565087514076],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":3.0},"mode":"lines","opacity":0.75,"showlegend":false,"text":["S4 → S1\u003cbr\u003eP=0.25"],"x":[-0.809016996890813,1.0],"y":[-0.5877853211100496,0.0],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.2},"mode":"lines","opacity":0.65,"showlegend":false,"text":["S4 → S2\u003cbr\u003eP=0.15"],"x":[-0.809016996890813,0.3090169521873281],"y":[-0.5877853211100496,0.9510565683560541],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":3.0},"mode":"lines","opacity":0.75,"showlegend":false,"text":["S4 → S3\u003cbr\u003eP=0.25"],"x":[-0.809016996890813,-0.8090170564954595],"y":[-0.5877853211100496,0.587785261505403],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S4 → S4\u003cbr\u003eP=0.20"],"x":[-0.809016996890813,-0.809016996890813],"y":[-0.5877853211100496,-0.5877853211100496],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.2},"mode":"lines","opacity":0.65,"showlegend":false,"text":["S4 → S5\u003cbr\u003eP=0.15"],"x":[-0.809016996890813,0.3090171011989445],"y":[-0.5877853211100496,-0.9510565087514076],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S5 → S1\u003cbr\u003eP=0.20"],"x":[0.3090171011989445,1.0],"y":[-0.9510565087514076,0.0],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S5 → S2\u003cbr\u003eP=0.20"],"x":[0.3090171011989445,0.3090169521873281],"y":[-0.9510565087514076,0.9510565683560541],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":2.6},"mode":"lines","opacity":0.7,"showlegend":false,"text":["S5 → S3\u003cbr\u003eP=0.20"],"x":[0.3090171011989445,-0.8090170564954595],"y":[-0.9510565087514076,0.587785261505403],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":1.8},"mode":"lines","opacity":0.6,"showlegend":false,"text":["S5 → S4\u003cbr\u003eP=0.10"],"x":[0.3090171011989445,-0.809016996890813],"y":[-0.9510565087514076,-0.5877853211100496],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","line":{"width":3.4},"mode":"lines","opacity":0.8,"showlegend":false,"text":["S5 → S5\u003cbr\u003eP=0.30"],"x":[0.3090171011989445,0.3090171011989445],"y":[-0.9510565087514076,-0.9510565087514076],"type":"scatter","xaxis":"x","yaxis":"y"},{"hoverinfo":"text","hovertext":["State: S1\u003cbr\u003eStationary Probability: 0.2005","State: S2\u003cbr\u003eStationary Probability: 0.2649","State: S3\u003cbr\u003eStationary Probability: 0.1881","State: S4\u003cbr\u003eStationary Probability: 0.1628","State: S5\u003cbr\u003eStationary Probability: 0.1837"],"marker":{"color":[0.20046208208752378,0.26488176134819247,0.18809459092144604,0.16281598260396846,0.18374558303886926],"colorbar":{"title":{"text":"Stationary\u003cbr\u003eProbability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]],"line":{"width":2},"showscale":true,"size":[61.08317477575428,72.67871704267463,58.857026365860285,54.306876868714326,58.07420494699647]},"mode":"markers+text","showlegend":false,"text":["S1\u003cbr\u003eπ=0.200","S2\u003cbr\u003eπ=0.265","S3\u003cbr\u003eπ=0.188","S4\u003cbr\u003eπ=0.163","S5\u003cbr\u003eπ=0.184"],"textposition":"top center","x":[1.0,0.3090169521873281,-0.8090170564954595,-0.809016996890813,0.3090171011989445],"y":[0.0,0.9510565683560541,0.587785261505403,-0.5877853211100496,-0.9510565087514076],"type":"scatter","xaxis":"x","yaxis":"y"},{"colorscale":[[0.0,"rgb(247,251,255)"],[0.125,"rgb(222,235,247)"],[0.25,"rgb(198,219,239)"],[0.375,"rgb(158,202,225)"],[0.5,"rgb(107,174,214)"],[0.625,"rgb(66,146,198)"],[0.75,"rgb(33,113,181)"],[0.875,"rgb(8,81,156)"],[1.0,"rgb(8,48,107)"]],"hovertemplate":"From %{y} → %{x}\u003cbr\u003eP = %{z:.2f}\u003cextra\u003e\u003c\u002fextra\u003e","text":[[0.2,0.3,0.1,0.2,0.2],[0.1,0.4,0.2,0.2,0.1],[0.3,0.2,0.2,0.1,0.2],[0.25,0.15,0.25,0.2,0.15],[0.2,0.2,0.2,0.1,0.3]],"texttemplate":"%{text}","x":["S1","S2","S3","S4","S5"],"y":["S1","S2","S3","S4","S5"],"z":[[0.2,0.3,0.1,0.2,0.2],[0.1,0.4,0.2,0.2,0.1],[0.3,0.2,0.2,0.1,0.2],[0.25,0.15,0.25,0.2,0.15],[0.2,0.2,0.2,0.1,0.3]],"type":"heatmap","xaxis":"x2","yaxis":"y2"},{"text":["0.200","0.265","0.188","0.163","0.184"],"textposition":"outside","x":["S1","S2","S3","S4","S5"],"y":[0.20046208208752378,0.26488176134819247,0.18809459092144604,0.16281598260396846,0.18374558303886926],"type":"bar","xaxis":"x3","yaxis":"y3"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"white","showlakes":true,"showland":true,"subunitcolor":"#C8D4E3"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"white","polar":{"angularaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""},"bgcolor":"white","radialaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"yaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"zaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"baxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"bgcolor":"white","caxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2}}},"xaxis":{"anchor":"y","domain":[0.0,0.44],"visible":false},"yaxis":{"anchor":"x","domain":[0.575,1.0],"visible":false},"xaxis2":{"anchor":"y2","domain":[0.56,1.0],"title":{"text":"Next State"}},"yaxis2":{"anchor":"x2","domain":[0.575,1.0],"title":{"text":"Current State"}},"xaxis3":{"anchor":"y3","domain":[0.0,1.0],"title":{"text":"State"}},"yaxis3":{"anchor":"x3","domain":[0.0,0.425],"title":{"text":"Probability"}},"annotations":[{"font":{"size":16},"showarrow":false,"text":"Markov Chain Network","x":0.22,"xanchor":"center","xref":"paper","y":1.0,"yanchor":"bottom","yref":"paper"},{"font":{"size":16},"showarrow":false,"text":"Transition Matrix Heatmap","x":0.78,"xanchor":"center","xref":"paper","y":1.0,"yanchor":"bottom","yref":"paper"},{"font":{"size":16},"showarrow":false,"text":"Stationary Distribution","x":0.5,"xanchor":"center","xref":"paper","y":0.425,"yanchor":"bottom","yref":"paper"}],"title":{"text":"Markov Chain Visualization Dashboard\u003cbr\u003e\u003csup\u003eNetwork Structure, Transition Matrix, and Stationary Distribution\u003c\u002fsup\u003e"},"height":900,"width":1300},                        {"responsive": true}                    )                };                            </script>        </div>

# Introduction to Markov Chains

A Markov chain is a mathematical model used to describe systems that transition between different states over time according to fixed probabilities.

The defining property of a Markov chain is the **Markov property**:

> The future state depends only on the current state, not on the sequence of states that came before it.

Formally, if $$X_t$$ denotes the state at time $$t$$, then

$$  
P(X_{t+1}=j \mid X_t=i, X_{t-1}, \dots, X_0) =

P(X_{t+1}=j \mid X_t=i)  
$$

This means that once the present state is known, the past provides no additional information about the future.

A Markov chain consists of:

- A finite or countable set of states
    
- Transition probabilities between states
    
- An initial state distribution
    

The probability of moving from state $$i$$ to state $$j$$ is called the **transition probability** and is written as

$$  
p_{ij} = P(X_{t+1}=j \mid X_t=i)  
$$

These probabilities are organized into a **transition matrix**:

$$  
P =  
\begin{bmatrix}  
p_{11} & p_{12} & \cdots & p_{1n} \\ 

p_{21} & p_{22} & \cdots & p_{2n} \\ 

\vdots & \vdots & \ddots & \vdots \\

p_{n1} & p_{n2} & \cdots & p_{nn}  
\end{bmatrix}  
$$

Each row of the matrix must sum to $$1$$:

$$  
\sum_{j=1}^{n} p_{ij} = 1  
$$

since the system must transition to some state after each step.

Markov chains are widely used in probability theory, statistics, economics, computer science, and machine learning. Common applications include weather prediction, queueing systems, stock market modeling, PageRank, and hidden Markov models used in speech recognition and natural language processing.

Markov chains are one of the most elegant ideas in probability theory. At their core, they model systems that â€œmoveâ€ between states according to fixed probabilities.

One of the most important equations in Markov chain theory is:

$$
\pi = \pi P
$$

This equation defines the **stationary distribution** of the chain.

In this article, weâ€™ll break down:

- What $$\pi = \pi P$$ means
- Why it matters
- How to solve for $$\pi$$
- A complete $$5 \times 5$$ example
- Full Gaussâ€“Jordan row elimination using matrices

---

# What Does $$\pi = \pi P$$ Mean?

Suppose we have a Markov chain with transition matrix $$P$$.

Each row of $$P$$ tells us the probabilities of moving from one state to another.

If:

$$
\pi =
\begin{bmatrix}
\pi_1 & \pi_2 & \pi_3 & \pi_4 & \pi_5
\end{bmatrix}
$$

then $$\pi_i$$ represents the long-run probability of being in state $$i$$.

The equation

$$
\pi = \pi P
$$

means:

> If the system already has distribution $$\pi$$, then after one transition using $$P$$, the distribution stays the same.

This is why $$\pi$$ is called the **stationary distribution**.

---

# A 5-State Markov Chain

Consider the transition matrix:

$$
P =
\begin{bmatrix}
0.2 & 0.3 & 0.1 & 0.2 & 0.2 \\
0.1 & 0.4 & 0.2 & 0.2 & 0.1 \\
0.3 & 0.2 & 0.2 & 0.1 & 0.2 \\
0.25 & 0.15 & 0.25 & 0.2 & 0.15 \\
0.2 & 0.2 & 0.2 & 0.1 & 0.3
\end{bmatrix}
$$

Notice every row sums to $$1$$, as required for a stochastic matrix.

We seek:

$$
\pi =
\begin{bmatrix}
\pi_1 & \pi_2 & \pi_3 & \pi_4 & \pi_5
\end{bmatrix}
$$

such that:

$$
\pi = \pi P
$$

and

$$
\pi_1 + \pi_2 + \pi_3 + \pi_4 + \pi_5 = 1
$$

---

# Step 1: Rewrite the Equation

Starting from

$$
\pi = \pi P
$$

move everything to one side:

$$
\pi(P - I) = 0
$$

Equivalently:

$$
(P^T - I)\pi^T = 0
$$

We now compute $$P^T - I$$.

---

# Step 2: Compute $$P^T - I$$

First transpose $$P$$:

$$
P^T =
\begin{bmatrix}
0.2 & 0.1 & 0.3 & 0.25 & 0.2 \\
0.3 & 0.4 & 0.2 & 0.15 & 0.2 \\
0.1 & 0.2 & 0.2 & 0.25 & 0.2 \\
0.2 & 0.2 & 0.1 & 0.2 & 0.1 \\
0.2 & 0.1 & 0.2 & 0.15 & 0.3
\end{bmatrix}
$$

Subtract the identity matrix:

$$
P^T - I =
\begin{bmatrix}
-0.8 & 0.1 & 0.3 & 0.25 & 0.2 \\
0.3 & -0.6 & 0.2 & 0.15 & 0.2 \\
0.1 & 0.2 & -0.8 & 0.25 & 0.2 \\
0.2 & 0.2 & 0.1 & -0.8 & 0.1 \\
0.2 & 0.1 & 0.2 & 0.15 & -0.7
\end{bmatrix}
$$

We append the normalization equation:

$$
\pi_1 + \pi_2 + \pi_3 + \pi_4 + \pi_5 = 1
$$

and replace the final row with:

$$
\begin{bmatrix}
1 & 1 & 1 & 1 & 1
\end{bmatrix}
$$

giving the augmented matrix:

$$
\left[
\begin{array}{ccccc|c}
-0.8 & 0.1 & 0.3 & 0.25 & 0.2 & 0 \\
0.3 & -0.6 & 0.2 & 0.15 & 0.2 & 0 \\
0.1 & 0.2 & -0.8 & 0.25 & 0.2 & 0 \\
0.2 & 0.2 & 0.1 & -0.8 & 0.1 & 0 \\
1 & 1 & 1 & 1 & 1 & 1
\end{array}
\right]
$$

---

# Step 3: Begin Gaussâ€“Jordan Elimination

Swap $$R_1$$ and $$R_5$$:

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 1 & 1 & 1 & 1 \\
0.3 & -0.6 & 0.2 & 0.15 & 0.2 & 0 \\
0.1 & 0.2 & -0.8 & 0.25 & 0.2 & 0 \\
0.2 & 0.2 & 0.1 & -0.8 & 0.1 & 0 \\
-0.8 & 0.1 & 0.3 & 0.25 & 0.2 & 0
\end{array}
\right]
$$

---

# Eliminate the First Column

Perform:

$$
\begin{aligned}
R_2 &\to R_2 - 0.3R_1 \\
R_3 &\to R_3 - 0.1R_1 \\
R_4 &\to R_4 - 0.2R_1 \\
R_5 &\to R_5 + 0.8R_1
\end{aligned}
$$

Result:

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 1 & 1 & 1 & 1 \\
0 & -0.9 & -0.1 & -0.15 & -0.1 & -0.3 \\
0 & 0.1 & -0.9 & 0.15 & 0.1 & -0.1 \\
0 & 0 & -0.1 & -1.0 & -0.1 & -0.2 \\
0 & 0.9 & 1.1 & 1.05 & 1.0 & 0.8
\end{array}
\right]
$$

---

# Normalize the Second Pivot

Divide $$R_2$$ by $$-0.9$$:

$$
R_2 \to \frac{1}{-0.9}R_2
$$

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 1 & 1 & 1 & 1 \\
0 & 1 & 0.111 & 0.167 & 0.111 & 0.333 \\
0 & 0.1 & -0.9 & 0.15 & 0.1 & -0.1 \\
0 & 0 & -0.1 & -1.0 & -0.1 & -0.2 \\
0 & 0.9 & 1.1 & 1.05 & 1.0 & 0.8
\end{array}
\right]
$$

---

# Eliminate the Second Column

Perform:

$$
\begin{aligned}
R_1 &\to R_1 - R_2 \\
R_3 &\to R_3 - 0.1R_2 \\
R_5 &\to R_5 - 0.9R_2
\end{aligned}
$$

Result:

$$
\left[
\begin{array}{ccccc|c}
1 & 0 & 0.889 & 0.833 & 0.889 & 0.667 \\
0 & 1 & 0.111 & 0.167 & 0.111 & 0.333 \\
0 & 0 & -0.911 & 0.133 & 0.089 & -0.133 \\
0 & 0 & -0.1 & -1.0 & -0.1 & -0.2 \\
0 & 0 & 1.0 & 0.9 & 0.9 & 0.5
\end{array}
\right]
$$

---

# Normalize the Third Pivot

Divide $$R_3$$ by $$-0.911$$:

$$
R_3 \to \frac{1}{-0.911}R_3
$$

Approximately:

$$
\left[
\begin{array}{ccccc|c}
1 & 0 & 0.889 & 0.833 & 0.889 & 0.667 \\
0 & 1 & 0.111 & 0.167 & 0.111 & 0.333 \\
0 & 0 & 1 & -0.146 & -0.098 & 0.146 \\
0 & 0 & -0.1 & -1.0 & -0.1 & -0.2 \\
0 & 0 & 1.0 & 0.9 & 0.9 & 0.5
\end{array}
\right]
$$

---

# Eliminate the Third Column

Perform:

$$
\begin{aligned}
R_1 &\to R_1 - 0.889R_3 \\
R_2 &\to R_2 - 0.111R_3 \\
R_4 &\to R_4 + 0.1R_3 \\
R_5 &\to R_5 - R_3
\end{aligned}
$$

Result:

$$
\left[
\begin{array}{ccccc|c}
1 & 0 & 0 & 0.963 & 0.976 & 0.537 \\
0 & 1 & 0 & 0.183 & 0.122 & 0.317 \\
0 & 0 & 1 & -0.146 & -0.098 & 0.146 \\
0 & 0 & 0 & -1.015 & -0.110 & -0.185 \\
0 & 0 & 0 & 1.046 & 0.998 & 0.354
\end{array}
\right]
$$

---

# Continue Reduction

Normalize $$R_4$$:

$$
R_4 \to \frac{1}{-1.015}R_4
$$

$$
\left[
\begin{array}{ccccc|c}
1 & 0 & 0 & 0.963 & 0.976 & 0.537 \\
0 & 1 & 0 & 0.183 & 0.122 & 0.317 \\
0 & 0 & 1 & -0.146 & -0.098 & 0.146 \\
0 & 0 & 0 & 1 & 0.108 & 0.182 \\
0 & 0 & 0 & 1.046 & 0.998 & 0.354
\end{array}
\right]
$$

Eliminate column 4:

$$
R_5 \to R_5 - 1.046R_4
$$

giving:

$$
\left[
\begin{array}{ccccc|c}
1 & 0 & 0 & 0.963 & 0.976 & 0.537 \\
0 & 1 & 0 & 0.183 & 0.122 & 0.317 \\
0 & 0 & 1 & -0.146 & -0.098 & 0.146 \\
0 & 0 & 0 & 1 & 0.108 & 0.182 \\
0 & 0 & 0 & 0 & 0.885 & 0.164
\end{array}
\right]
$$

---

# Solve for $$\pi_5$$

$$
0.885\pi_5 = 0.164
$$

so:

$$
\pi_5 \approx 0.185
$$

Then:

$$
\pi_4 + 0.108(0.185) = 0.182
$$

giving:

$$
\pi_4 \approx 0.162
$$

Next:

$$
\pi_3 -0.146(0.162)-0.098(0.185)=0.146
$$

so:

$$
\pi_3 \approx 0.188
$$

Then:

$$
\pi_2 +0.183(0.162)+0.122(0.185)=0.317
$$

giving:

$$
\pi_2 \approx 0.265
$$

Finally:

$$
\pi_1 +0.963(0.162)+0.976(0.185)=0.537
$$

yielding:

$$
\pi_1 \approx 0.201
$$

---

# Final Stationary Distribution

Thus:

$$
\pi \approx
\begin{bmatrix}
0.201 &
0.265 &
0.188 &
0.162 &
0.185
\end{bmatrix}
$$

Check that the entries sum to $$1$$:

$$
0.201 + 0.265 + 0.188 + 0.162 + 0.185 \approx 1
$$

and indeed:

$$
\pi P = \pi
$$

---

# Why the Stationary Distribution Matters

The stationary distribution tells us the **long-run behavior** of the Markov chain.

Even if the system starts somewhere else, after many transitions the probabilities converge toward $$\pi$$.

Applications include:

- Google PageRank
- Queueing systems
- Population dynamics
- Weather models
- Financial modeling
- Reinforcement learning

---

# The Big Idea

The equation

$$
\pi = \pi P
$$

captures equilibrium in a stochastic system.

The distribution reproduces itself after every transition.

Solving it ultimately becomes a linear algebra problem:

- Form a homogeneous system
- Add a normalization equation
- Use Gaussâ€“Jordan elimination
- Interpret the resulting probability vector

This is one of the most beautiful intersections of probability theory and linear algebra.

# Appendix: Solving the Stationary Distribution Using SymPy

This appendix shows how to compute the stationary distribution using Pythonâ€™s SymPy symbolic mathematics library instead of performing Gaussâ€“Jordan elimination by hand.

---

# Why Use SymPy?

Manual elimination is excellent for understanding the mathematics, but for larger Markov chains it becomes tedious and error-prone.

SymPy allows us to:

- Construct matrices symbolically
- Solve linear systems exactly
- Compute stationary distributions efficiently
- Verify results automatically

---

# Step 1: Import SymPy

{% raw %}
```python
import sympy as sp
```
{% endraw %}

---

# Step 2: Define the Transition Matrix

We define the same transition matrix \(P\):

{% raw %}
```python
P = sp.Matrix([
    [0.2, 0.3, 0.1, 0.2, 0.2],
    [0.1, 0.4, 0.2, 0.2, 0.1],
    [0.3, 0.2, 0.2, 0.1, 0.2],
    [0.25, 0.15, 0.25, 0.2, 0.15],
    [0.2, 0.2, 0.2, 0.1, 0.3]
])
```
{% endraw %}

---

# Step 3: Create the Unknown Variables

We define the stationary probabilities:

{% raw %}
```python
pi1, pi2, pi3, pi4, pi5 = sp.symbols(
    'pi1 pi2 pi3 pi4 pi5'
)
```
{% endraw %}

Form the vector:

{% raw %}
```python
pi = sp.Matrix([[pi1, pi2, pi3, pi4, pi5]])
```
{% endraw %}

---

# Step 4: Write the Stationary Equation

We solve:

$$
\pi = \pi P
$$

which becomes:

{% raw %}
```python
equations = list(pi * P - pi)
```
{% endraw %}

This produces the homogeneous system:

{% raw %}
```python
(piP - pi) = 0
```
{% endraw %}

---

# Step 5: Add the Normalization Equation

A probability distribution must satisfy:

$$
\pi_1 + \pi_2 + \pi_3 + \pi_4 + \pi_5 = 1
$$

Add this equation:

{% raw %}
```python
equations.append(
    pi1 + pi2 + pi3 + pi4 + pi5 - 1
)
```
{% endraw %}

---

# Step 6: Solve the System

Now solve all equations simultaneously:

{% raw %}
```python
solution = sp.solve(
    equations,
    [pi1, pi2, pi3, pi4, pi5]
)

print(solution)
```
{% endraw %}

---

# Complete Program

{% raw %}
```python
import sympy as sp

# Transition matrix
P = sp.Matrix([
    [0.2, 0.3, 0.1, 0.2, 0.2],
    [0.1, 0.4, 0.2, 0.2, 0.1],
    [0.3, 0.2, 0.2, 0.1, 0.2],
    [0.25, 0.15, 0.25, 0.2, 0.15],
    [0.2, 0.2, 0.2, 0.1, 0.3]
])

# Unknown stationary probabilities
pi1, pi2, pi3, pi4, pi5 = sp.symbols(
    'pi1 pi2 pi3 pi4 pi5'
)

# Row vector
pi = sp.Matrix([[pi1, pi2, pi3, pi4, pi5]])

# Stationary equations
equations = list(pi * P - pi)

# Normalization condition
equations.append(
    pi1 + pi2 + pi3 + pi4 + pi5 - 1
)

# Solve system
solution = sp.solve(
    equations,
    [pi1, pi2, pi3, pi4, pi5]
)

print(solution)
```
{% endraw %}

---

# Expected Output

SymPy returns values close to:

{% raw %}
```python
{
 pi1: 0.201,
 pi2: 0.265,
 pi3: 0.188,
 pi4: 0.162,
 pi5: 0.185
}
```
{% endraw %}

Thus:

$$
\pi \approx
\begin{bmatrix}
0.201 &
0.265 &
0.188 &
0.162 &
0.185
\end{bmatrix}
$$

which matches the result obtained through Gaussâ€“Jordan elimination.

---

# Verifying the Result

We can also verify that:

$$
\pi P = \pi
$$

using:

{% raw %}
```python
pi_numeric = sp.Matrix([[
    solution[pi1],
    solution[pi2],
    solution[pi3],
    solution[pi4],
    solution[pi5]
]])

print(pi_numeric * P)
```
{% endraw %}

The output equals the original vector $$\pi$$, confirming the stationary distribution.

---

# Alternative Method: Eigenvectors

Another elegant approach uses eigenvectors.

The stationary distribution satisfies:

$$
P^T\pi^T = \pi^T
$$

meaning $$\pi^T$$ is an eigenvector of $$P^T$$ with eigenvalue $$1$$.

In SymPy:

{% raw %}
```python
eigen_data = P.T.eigenvects()

print(eigen_data)
```
{% endraw %}

You would then extract the eigenvector associated with eigenvalue $$1$$ and normalize it so its entries sum to $$1$$.

---

# Final Remarks

Using SymPy transforms the stationary distribution problem into a compact symbolic computation workflow:

1. Define the transition matrix
2. Construct the equations
3. Add normalization
4. Solve symbolically
5. Verify the result

For large Markov chains, symbolic and numerical tools become essential, and SymPy provides a clean bridge between probability theory and computational linear algebra.
