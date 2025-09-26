---
layout: post
title:  "Exploring Full-Funnel Advertising Strategies with Markov Chains and Python SymPy"
date:   2025-9-24 09:25:17 -0800
categories: jekyll update data
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Exploring_Full_Funnel_Advertising_Strategies_with_Python_SymPy.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

In the world of digital advertising, understanding how users move through the marketing funnel is key to designing effective ad campaigns. Here we are exploring full-funnel advertising, which integrates brand awareness and performance-driven ads to maximize conversions. To model this process, we treat the funnel as a Markov chain, where users transition between stages (Not Aware → Aware → Purchase) with certain probabilities. In this post, we’ll walk through a simulation model based on Markov chains that helps analyze different ad strategies using Python and SymPy.


<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="d4b2190f-bb8c-4a4b-9c69-4dfec6da1a12" class="plotly-graph-div" style="height:600px; width:900px;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("d4b2190f-bb8c-4a4b-9c69-4dfec6da1a12")) {                    Plotly.newPlot(                        "d4b2190f-bb8c-4a4b-9c69-4dfec6da1a12",                        [{"hovertemplate":"Step %{x}\u003cbr\u003ePurchase fraction: %{y:.4f}\u003cextra\u003e\u003c\u002fextra\u003e","mode":"lines+markers","name":"Brand-Ads-Only - Purchase","x":[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],"y":[0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0],"type":"scatter"},{"hovertemplate":"Step %{x}\u003cbr\u003ePurchase fraction: %{y:.4f}\u003cextra\u003e\u003c\u002fextra\u003e","mode":"lines+markers","name":"Performance-Ads-Only - Purchase","x":[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],"y":[0.0,0.12,0.204,0.2628,0.30395999999999995,0.33277199999999996,0.35294039999999993,0.3670582799999999,0.3769407959999999,0.3838585571999999,0.3887009900399999,0.3920906930279999,0.39446348511959994,0.39612443958371996,0.397287107708604,0.3981009753960228,0.39867068277721596,0.3990694779440512,0.3993486345608358,0.39954404419258505,0.39968083093480955],"type":"scatter"},{"hovertemplate":"Step %{x}\u003cbr\u003ePurchase fraction: %{y:.4f}\u003cextra\u003e\u003c\u002fextra\u003e","mode":"lines+markers","name":"Brand-Plus-Performance - Purchase","x":[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],"y":[0.0,0.0,0.156,0.156,0.294,0.294,0.41363999999999995,0.41363999999999995,0.51582,0.51582,0.6020916,0.6020916,0.6742781999999999,0.6742781999999999,0.734246004,0.734246004,0.783773214,0.783773214,0.82448205876,0.82448205876,0.8578100883],"type":"scatter"},{"hovertemplate":"Step %{x}\u003cbr\u003ePurchase fraction: %{y:.4f}\u003cextra\u003e\u003c\u002fextra\u003e","mode":"lines+markers","name":"Full-Funnel - Purchase","x":[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],"y":[0.0,0.12,0.24,0.3528,0.4548,0.544632,0.62226,0.68839608,0.74412852,0.7906909752,0.8293244916,0.861199791288,0.887377971636,0.90879507433272,0.92626094738292,0.9404661794480568,0.95199313863765,0.9613286474655632,0.9688768135612609,0.9749711777611759,0.9798857510474578],"type":"scatter"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"white","showlakes":true,"showland":true,"subunitcolor":"#C8D4E3"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"white","polar":{"angularaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""},"bgcolor":"white","radialaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"yaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"zaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"baxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"bgcolor":"white","caxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2}}},"legend":{"orientation":"v"},"title":{"text":"Progression to Purchase over time for different strategies (Plotly)"},"xaxis":{"title":{"text":"Step"}},"yaxis":{"title":{"text":"Fraction of users in Purchase"}},"width":900,"height":600},                        {"responsive": true}                    )                };                            </script>        </div>



---

## The Funnel Model

We model user behavior with a **three-stage funnel**:

1. **Not Aware** – Users who have not yet seen the brand.
2. **Aware** – Users who know the brand but haven’t purchased.
3. **Purchase** – Users who have purchased the brand (terminal stage).

We assume:

* Users arrive with a fraction `μ` in Not Aware and `1-μ` in Aware.
* Brand ads move users from Not Aware → Aware with probability `p_ba`.
* Performance ads move users from Aware → Purchase with probability `p_pa`.
* Users progress **linearly** through the funnel (no skipping stages or moving backward).

---

## Setting Up the Model Symbolically

We start by defining symbolic variables and transition matrices with `sympy`:

```python
import sympy as sp
from IPython.display import display, Math
import numpy as np
import matplotlib.pyplot as plt

mu, p_ba, p_pa = sp.symbols('mu p_ba p_pa')
display(mu, p_ba, p_pa)

# Initial distribution
x0 = sp.Matrix([mu, 1 - mu, 0])
x0

B = sp.Matrix([
  [1- p_ba, 0, 0   ],
  [p_ba, 1, 0 ],
  [0, 0, 1 ]])

B

P = sp.Matrix([
    [1,        0, 0],
    [0, 1 - p_pa, 0],
    [0,      p_pa, 1]
])
P

F = sp.Matrix([
  [1-p_ba, 0, 0],
  [p_ba, 1-p_pa, 0],
  [0, p_pa,1]
])
F
```

Here:

* `B` represents **Brand ads**
* `P` represents **Performance ads**
* `F` represents **Full-funnel ads** (stage-dependent)

---

## Simulating One-Step Progression

We can compute the distribution after one or two exposures:

```python
x1_B = (B*x0)
x2_B = (B*x1_B)
display(x1_B, x2_B)

x1_P = (P*x0)
x2_P = (P*x1_P)
display(x1_P, x2_P)

x1_BP = (B*x0)
x2_BP = (P*x1_BP)
display(x1_BP, x2_BP)

x1_F = (F*x0)
x2_F = (F*x1_F)
display(x1_F, x2_F)
```

This allows us to **symbolically track user fractions** as they move through the funnel for each strategy:

* Brand-Ads-Only
* Performance-Ads-Only
* Brand-Plus-Performance
* Full-Funnel

---

## Moving to Numerical Simulation

Now we assign **numerical values** for simulation:

```python
# Parameters
mu = 0.6      # fraction initially Not Aware
p_ba = 0.2    # Brand ad conversion
p_pa = 0.3    # Performance ad conversion
steps = 20    # Number of time steps

# Initial distribution
x0 = np.array([mu, 1-mu, 0])

# Transition matrices
B = np.array([
    [1-p_ba, 0, 0],
    [p_ba, 1, 0],
    [0, 0, 1]
])

P_mat = np.array([
    [1, 0, 0],
    [0, 1-p_pa, 0],
    [0, p_pa, 1]
])

F = np.array([
    [1-p_ba, 0, 0],
    [p_ba, 1-p_pa, 0],
    [0, p_pa, 1]
])
```

---

## Simulating Multiple Steps

We define a function to **apply the transition matrices repeatedly**:

```python
# Function to simulate repeated application of matrices
def simulate_steps(x0, matrices, steps):
    traj = [x0.copy()]
    x = x0.copy()
    n_mats = len(matrices)
    for i in range(steps):
        # Cycle through matrices (strategy can have multiple types)
        M = matrices[i % n_mats]
        x = M @ x
        traj.append(x.copy())
    return np.array(traj)
```

---

## Defining Strategies

We simulate four strategies:

```python
# Define strategies
strategies = {
    "Brand-Ads-Only": [B],
    "Performance-Ads-Only": [P_mat],
    "Brand-Plus-Performance": [B, P_mat],
    "Full-Funnel": [F]
}

# Run simulations
results = {}
for name, mats in strategies.items():
    results[name] = simulate_steps(x0, mats, steps)
```

---

## Visualizing the Funnel Dynamics

Finally, we can **plot the fraction of users who have purchased** over time:

```python
# Plot results
plt.figure(figsize=(12, 8))
for name, traj in results.items():
    plt.plot(traj[:,2], label=f'{name} - Purchase')  # focus on Purchase fraction
plt.xlabel("Step")
plt.ylabel("Fraction of users in Purchase")
plt.title("Progression to Purchase over time for different strategies")
plt.legend()
plt.grid(True)
plt.show()
```

This plot reveals which advertising strategy **converts users most efficiently** over multiple exposures. You can easily extend it to plot **Not Aware** or **Aware** stages as well.

---

## Conclusion

Using symbolic matrices and numerical simulations, we can **model and compare advertising strategies** in a full-funnel context:

* Brand-Ads-Only increases awareness but may leave many users unconverted.
* Performance-Ads-Only targets already aware users but ignores those who need awareness.
* Brand-Plus-Performance combines both sequentially.
* Full-Funnel dynamically chooses the best ad for each stage, often leading to faster conversions.

This approach provides a **transparent, data-driven way** to evaluate ad campaigns before spending on real-world ads.

Perfect! I understand — you want the **symbolic equations in a neat, step-by-step matrix multiplication style**, similar to a textbook. Let’s create an appendix with all four strategies in that style. I’ll keep it in **LaTeX-style equations** for clarity.

---

# Appendix: Symbolic Step-By-Step Funnel Calculations

We define:
$$
\begin{aligned}
x_0 = \begin{bmatrix} \mu \\ 1-\mu \\ 0 \end{bmatrix}, \quad
B = \begin{bmatrix} 1-p_{ba} & 0 & 0 \\ p_{ba} & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}, \quad
P = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1-p_{pa} & 0 \\ 0 & p_{pa} & 1 \end{bmatrix}, \quad
F = \begin{bmatrix} 1-p_{ba} & 0 & 0 \\ p_{ba} & 1-p_{pa} & 0 \\ 0 & p_{pa} & 1 \end{bmatrix}
\end{aligned}
$$
---

## **1. Brand Ads Only**

**Step 1:**

$$
x_1 = B x_0 =
\begin{bmatrix} 1-p_{ba} & 0 & 0 \\ p_{ba} & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
\begin{bmatrix} \mu \\ 1-\mu \\ 0 \end{bmatrix}
$$
$$
=
\begin{bmatrix} \mu (1-p_{ba}) \\ (1-\mu) + \mu p_{ba} \\ 0 \end{bmatrix}
$$

**Step 2:**

$$
x_2 = B x_1 =
\begin{bmatrix} 1-p_{ba} & 0 & 0 \\ p_{ba} & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
\begin{bmatrix} \mu (1-p_{ba}) \\ (1-\mu) + \mu p_{ba} \\ 0 \end{bmatrix}
$$
$$
=
\begin{bmatrix} \mu (1-p_{ba})^2 \\ (1-\mu) + \mu p_{ba} (2-p_{ba}) \\ 0 \end{bmatrix}
$$

---

## **2. Performance Ads Only**

**Step 1:**

$$
x_1 = P x_0 =
\begin{bmatrix} 1 & 0 & 0 \\ 0 & 1-p_{pa} & 0 \\ 0 & p_{pa} & 1 \end{bmatrix}
\begin{bmatrix} \mu \\ 1-\mu \\ 0 \end{bmatrix}
$$
$$
=
\begin{bmatrix} \mu \\ (1-\mu)(1-p_{pa}) \\ (1-\mu)p_{pa} \end{bmatrix}
$$

**Step 2:**

$$
x_2 = P x_1 =
\begin{bmatrix} 1 & 0 & 0 \\ 0 & 1-p_{pa} & 0 \\ 0 & p_{pa} & 1 \end{bmatrix}
\begin{bmatrix} \mu \\ (1-\mu)(1-p_{pa}) \\ (1-\mu)p_{pa} \end{bmatrix}
$$
$$
=
\begin{bmatrix} \mu \\ (1-\mu)(1-p_{pa})^2 \\ (1-\mu)(1-(1-p_{pa})^2) \end{bmatrix}
$$

---

## **3. Brand-Plus-Performance**

**Step 1 (Brand):**

$$
x_1 = B x_0 =
\begin{bmatrix} 1-p_{ba} & 0 & 0 \\ p_{ba} & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
\begin{bmatrix} \mu \\ 1-\mu \\ 0 \end{bmatrix}
$$
$$
=
\begin{bmatrix} \mu (1-p_{ba}) \\ (1-\mu) + \mu p_{ba} \\ 0 \end{bmatrix}
$$

**Step 2 (Performance):**

$$
x_2 = P x_1 =
\begin{bmatrix} 1 & 0 & 0 \\ 0 & 1-p_{pa} & 0 \\ 0 & p_{pa} & 1 \end{bmatrix}
\begin{bmatrix} \mu (1-p_{ba}) \\ (1-\mu) + \mu p_{ba} \\ 0 \end{bmatrix}
$$
$$
=
\begin{bmatrix} \mu (1-p_{ba}) \\ ((1-\mu)+\mu p_{ba})(1-p_{pa}) \\ ((1-\mu)+\mu p_{ba})p_{pa} \end{bmatrix}
$$

---

## **4. Full-Funnel**

**Step 1:**

$$
x_1 = F x_0 =
\begin{bmatrix} 1-p_{ba} & 0 & 0 \\ p_{ba} & 1-p_{pa} & 0 \\ 0 & p_{pa} & 1 \end{bmatrix}
\begin{bmatrix} \mu \\ 1-\mu \\ 0 \end{bmatrix}
$$
$$
=
\begin{bmatrix} \mu (1-p_{ba}) \\ \mu p_{ba} + (1-\mu)(1-p_{pa}) \\ (1-\mu)p_{pa} \end{bmatrix}
$$

**Step 2:**

$$
x_2 = F x_1 =
\begin{bmatrix} 1-p_{ba} & 0 & 0 \\ p_{ba} & 1-p_{pa} & 0 \\ 0 & p_{pa} & 1 \end{bmatrix}
\begin{bmatrix} \mu (1-p_{ba}) \\ \mu p_{ba} + (1-\mu)(1-p_{pa}) \\ (1-\mu)p_{pa} \end{bmatrix}
$$
$$
=
\begin{bmatrix}
\mu(1-p_{ba})^2 \\
\mu p_{ba}(1-p_{ba}) + (1-p_{pa})(\mu p_{ba} + (1-\mu)(1-p_{pa})) \\
p_{pa}(1-\mu) + p_{pa}(\mu p_{ba} + (1-\mu)(1-p_{pa}))
\end{bmatrix}
$$



---

# Appendix: How B, P, and F Matrices Were Derived

The matrices represent **stage-to-stage probabilities** in the marketing funnel. The funnel has three stages:

1. **Not Aware (N)**
2. **Aware (A)**
3. **Purchase (P)**

We assume:

* Users progress linearly through the funnel: N → A → P
* Users cannot skip stages or go backward
* Purchase is a terminal stage

---

## **1. Brand Ads Matrix (B)**

Brand ads **only affect users who are Not Aware**, moving them to Aware with probability `p_ba`.

* If a user is Not Aware, they either stay Not Aware (`1-p_ba`) or become Aware (`p_ba`).
* Aware users are **not affected by brand ads**, so they stay Aware.
* Purchase is terminal.

Thus, the matrix is:

```python
B = sp.Matrix([
  [1- p_ba, 0, 0],
  [p_ba, 1, 0],
  [0, 0, 1]
])
```

| From \ To | Not Aware | Aware | Purchase |
| --------- | --------- | ----- | -------- |
| Not Aware | 1-p_ba    | p_ba  | 0        |
| Aware     | 0         | 1     | 0        |
| Purchase  | 0         | 0     | 1        |

**Explanation:** Only Not Aware → Aware is possible; others remain unchanged.

---

## **2. Performance Ads Matrix (P)**

Performance ads **only affect users who are Aware**, moving them to Purchase with probability `p_pa`.

* Not Aware users are unaffected.
* Aware users either stay Aware (`1-p_pa`) or Purchase (`p_pa`).
* Purchase is terminal.

Matrix:

```python
P = sp.Matrix([
    [1, 0, 0],
    [0, 1 - p_pa, 0],
    [0, p_pa, 1]
])
```

| From \ To | Not Aware | Aware  | Purchase |
| --------- | --------- | ------ | -------- |
| Not Aware | 1         | 0      | 0        |
| Aware     | 0         | 1-p_pa | p_pa     |
| Purchase  | 0         | 0      | 1        |

**Explanation:** Only Aware → Purchase is possible; others remain unchanged.

---

## **3. Full-Funnel Matrix (F)**

The Full-Funnel strategy **targets the right ad based on the user’s stage**:

* Not Aware → Brand ad → moves to Aware with `p_ba`
* Aware → Performance ad → moves to Purchase with `p_pa`
* Purchase is terminal

This combines the effects of both B and P in one matrix:

```python
F = sp.Matrix([
  [1-p_ba, 0, 0],
  [p_ba, 1-p_pa, 0],
  [0, p_pa, 1]
])
```

| From \ To                                                                                  | Not Aware | Aware  | Purchase |
| ------------------------------------------------------------------------------------------ | --------- | ------ | -------- |
| Not Aware                                                                                  | 1-p_ba    | 0      | 0        |
| Aware                                                                                      | p_ba      | 1-p_pa | 0        |
| Purchase                                                                                   | 0         | p_pa   | 1        |


**Explanation:**

* Row 1: Not Aware users → either stay Not Aware or move to Aware via brand ad
* Row 2: Aware users → stay Aware or move to Purchase via performance ad
* Row 3: Purchase is terminal

This matrix **dynamically applies the correct ad per user stage**, making it the most realistic full-funnel model.

---

### **Summary of Derivation Logic**

1. Identify which **funnel stage the ad affects**
2. Assign probabilities for **progressing to the next stage** (`p_ba` or `p_pa`)
3. Ensure **no backward movement**
4. Terminal stage (Purchase) always remains `1`








