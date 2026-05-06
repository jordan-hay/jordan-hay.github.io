---
layout: post
title:  "Representative Markov Chain Examples"
date:   2026-03-18 09:25:17 -0800
categories: jekyll update data
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Representative_Markov_Chain_Examples.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>


<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="cdd3ec7c-1f04-43c8-b5c9-1aa7457dbf2d" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("cdd3ec7c-1f04-43c8-b5c9-1aa7457dbf2d")) {                    Plotly.newPlot(                        "cdd3ec7c-1f04-43c8-b5c9-1aa7457dbf2d",                        [{"coloraxis":"coloraxis","name":"0","texttemplate":"%{z}","x":["irreducible","aperiodic","ergodic","communicating_classes","closed_classes","absorbing_states","recurrent_states","transient_states","avg_period"],"y":["ergodic_chain","periodic_chain","absorbing_chain","multiple_closed_classes","fully_connected","transient_to_closed","self_loop_aperiodic","three_cycle","identity_chain","random_chain"],"z":[[1.0,1.0,1.0,1.0,1.0,0.0,2.0,0.0,1.0],[1.0,0.0,0.0,1.0,1.0,0.0,2.0,0.0,2.0],[0.0,1.0,0.0,2.0,1.0,1.0,1.0,1.0,1.0],[0.0,1.0,0.0,4.0,2.0,2.0,2.0,2.0,1.0],[1.0,1.0,1.0,1.0,1.0,0.0,3.0,0.0,1.0],[0.0,1.0,0.0,2.0,1.0,0.0,2.0,1.0,1.0],[1.0,1.0,1.0,1.0,1.0,0.0,2.0,0.0,1.0],[1.0,0.0,0.0,1.0,1.0,0.0,3.0,0.0,3.0],[0.0,1.0,0.0,3.0,3.0,3.0,3.0,0.0,1.0],[1.0,1.0,1.0,1.0,1.0,0.0,3.0,0.0,1.0]],"type":"heatmap","xaxis":"x","yaxis":"y","hovertemplate":"x: %{x}\u003cbr\u003echain: %{y}\u003cbr\u003ecolor: %{z}\u003cextra\u003e\u003c\u002fextra\u003e"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#f2f5fa"},"error_y":{"color":"#f2f5fa"},"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"baxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"line":{"color":"#283442"}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"marker":{"line":{"color":"#283442"}},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#506784"},"line":{"color":"rgb(17,17,17)"}},"header":{"fill":{"color":"#2a3f5f"},"line":{"color":"rgb(17,17,17)"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#f2f5fa","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#f2f5fa"},"geo":{"bgcolor":"rgb(17,17,17)","lakecolor":"rgb(17,17,17)","landcolor":"rgb(17,17,17)","showlakes":true,"showland":true,"subunitcolor":"#506784"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"dark"},"paper_bgcolor":"rgb(17,17,17)","plot_bgcolor":"rgb(17,17,17)","polar":{"angularaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","radialaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"yaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"zaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"}},"shapedefaults":{"line":{"color":"#f2f5fa"}},"sliderdefaults":{"bgcolor":"#C8D4E3","bordercolor":"rgb(17,17,17)","borderwidth":1,"tickwidth":0},"ternary":{"aaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"baxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","caxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"title":{"x":0.05},"updatemenudefaults":{"bgcolor":"#506784","borderwidth":0},"xaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Property"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"autorange":"reversed","title":{"text":"Markov Chain"}},"coloraxis":{"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]},"title":{"text":"Structural Properties of Markov Chains"}},                        {"responsive": true}                    )                };                            </script>        </div>
# Introduction

Markov chains {% cite durrett2012essentials %} are one of the simplest and most powerful mathematical models for stochastic systems.

They appear everywhere:

- web-page ranking
    
- reinforcement learning
    
- queueing systems
    
- finance
    
- genetics
    
- statistical physics
    
- language models
    

The central idea is simple:

> The future depends only on the present state, not on the full history.

Formally, a Markov chain satisfies

$$  
P(X_{t+1}=j \mid X_t=i, X_{t-1}, \dots, X_0)

P(X_{t+1}=j \mid X_t=i)  
$$

where:

- $$X_t$$ is the state at time $$t$$
    
- $$P(X_{t+1}=j \mid X_t=i)$$ is the transition probability from state $$i$$ to state $$j$$
    

A finite Markov chain is completely described by its transition matrix:

$$  
P =  
\begin{bmatrix}  
p_{11} & p_{12} & \cdots & p_{1n} \\  
p_{21} & p_{22} & \cdots & p_{2n} \\  
\vdots & \vdots & \ddots & \vdots \\  
p_{n1} & p_{n2} & \cdots & p_{nn}  \\
\end{bmatrix}  
$$

Each row sums to $$1$$:

$$  
\sum_{j=1}^n p_{ij} = 1  
$$

In this post, we'll walk through several representative examples and explain the most important structural properties of Markov chains.

---

# 1. Ergodic Chain

Consider:

$$  
P =  
\begin{bmatrix}  
0.5 & 0.5 \\ 
0.2 & 0.8  \\
\end{bmatrix}  
$$

This chain is:

- irreducible
    
- aperiodic
    
- ergodic
    

## Irreducibility

A chain is irreducible if every state can eventually reach every other state.

Here:

- state $$0$$ can reach state $$1$$
    
- state $$1$$ can reach state $$0$$
    

So the state space forms a single communicating class.

---

## Aperiodicity

A state has period

$$  
d(i)

\gcd  
{  
n \ge 1 : P^n(i,i) > 0  
}  
$$

Because both states have self-loops:

$$  
P(0 \to 0) = 0.5  
$$

and

$$  
P(1 \to 1) = 0.8  
$$

the chain can return in one step, giving period $$1$$.

---

## Ergodicity

An irreducible + aperiodic finite chain is ergodic.

That means:

$$  
P^n \to  
\begin{bmatrix}  
\pi \  
\pi \  
\vdots  
\end{bmatrix}  
\quad \text{as } n \to \infty  
$$

where $$\pi$$ is the stationary distribution.

The stationary distribution solves:

$$  
\pi P = \pi  
$$

with

$$  
\sum_i \pi_i = 1  
$$

For this chain:

$$  
\pi =  
\begin{bmatrix}  
0.2857 & 0.7143  
\end{bmatrix}  
$$

meaning the chain spends about $$71%$$ of its time in state $$1$$ long-run.

---

# 2. Periodic Chain

Now consider:

$$  
P =  
\begin{bmatrix}  
0 & 1 \\
1 & 0  \\
\end{bmatrix}  
$$

This chain alternates forever:

$$  
0 \to 1 \to 0 \to 1 \to \cdots  
$$

The return times to state $$0$$ are:

$$  
2,4,6,8,\dots  
$$

Thus:

$$  
d(0)=2  
$$

and similarly:

$$  
d(1)=2  
$$

The chain is irreducible but periodic.

---

## Why Periodicity Matters

Even though a stationary distribution exists:

$$  
\pi =  
\begin{bmatrix}  
0.5 & 0.5  
\end{bmatrix}  
$$

the powers of the transition matrix do not converge:

$$  
P^{2n} =  
\begin{bmatrix}  
1 & 0 \\
0 & 1 \\ 
\end{bmatrix}  
$$

while

$$  
P^{2n+1} =  
\begin{bmatrix}  
0 & 1 \\ 
1 & 0 \\ 
\end{bmatrix}  
$$

The system oscillates forever.

---

# 3. Absorbing Chain

Consider:

$$  
P =  
\begin{bmatrix}  
1.0 & 0.0 \\  
0.4 & 0.6  \\
\end{bmatrix}  
$$

State $$0$$ is absorbing because:

$$  
P(0 \to 0)=1  
$$

Once entered, it can never be left.

---

## Long-Term Behavior

State $$1$$ eventually flows into state $$0$$.

Repeated multiplication shows:

$$  
P^n  
\to  
\begin{bmatrix}  
1 & 0 \\
1 & 0 \\ 
\end{bmatrix}  
$$

Eventually all probability mass accumulates in the absorbing state.

---

# 4. Multiple Closed Classes

Now consider:

$$  
P =  
\begin{bmatrix}  
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0.5 & 0 & 0.5 & 0 \\  
0 & 0.5 & 0 & 0.5 \\ 
\end{bmatrix}  
$$

States $$0$$ and $$1$$ are absorbing closed classes.

States $$2$$ and $$3$$ are transient.

Eventually:

- state $$2$$ gets trapped in class $${0}$$
    
- state $$3$$ gets trapped in class $${1}$$
    

This chain is reducible because not all states communicate.

---

# 5. Fully Connected Chain

A more "generic" stochastic system:

$$  
P =  
\begin{bmatrix}  
0.2 & 0.3 & 0.5 \\ 
0.4 & 0.4 & 0.2 \\
0.3 & 0.3 & 0.4 \\
\end{bmatrix}  
$$

Every state communicates with every other state in one step.

The chain is:

- irreducible
    
- aperiodic
    
- ergodic
    

Because all entries are positive:

$$  
p_{ij} > 0  
$$

the chain mixes rapidly toward equilibrium.

---

# 6. Transient to Closed Flow

Consider:

$$  
P =  
\begin{bmatrix}  
0.2 & 0.8 & 0.0 \\  
0.0 & 0.5 & 0.5 \\ 
0.0 & 0.4 & 0.6 \\ 
\end{bmatrix}  
$$

State $$0$$ is transient.

Once the chain enters $${1,2}$$, it never returns to $$0$$.

The subset:

$$  
{1,2}  
$$

forms a closed irreducible class.

This structure appears frequently in:

- queueing systems
    
- epidemic models
    
- reinforcement learning environments
    

where some states act as temporary entry points before long-run equilibrium behavior emerges.

---

# 7. Self-Loops Create Aperiodicity

Consider:

$$  
P =  
\begin{bmatrix}  
0.1 & 0.9 \\
0.7 & 0.3 \\
\end{bmatrix}  
$$

Even a tiny self-loop can destroy periodicity.

Because:

$$  
P(0 \to 0)=0.1  
$$

the chain can return in one step.

Thus:

$$  
d(0)=1  
$$

and the entire irreducible chain becomes aperiodic.

This is why adding "noise" or "lazy steps" is a common trick in Markov Chain Monte Carlo (MCMC).

---

# 8. Three-Cycle Periodic Chain

Consider:

$$  
P =  
\begin{bmatrix}  
0 & 1 & 0 \\  
0 & 0 & 1 \\ 
1 & 0 & 0 \\
\end{bmatrix}  
$$

The chain cycles deterministically:

$$  
0 \to 1 \to 2 \to 0  
$$

Returns occur only at times:

$$  
3,6,9,\dots  
$$

So:

$$  
d(i)=3  
$$

for every state.

The chain is irreducible but not ergodic.

---

# 9. Identity Chain

The identity matrix:

$$  
P = I  
$$

gives:

$$  
P =  
\begin{bmatrix}  
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\ 
\end{bmatrix}  
$$

Every state is absorbing.

Nothing ever changes.

This is the most degenerate possible Markov chain.

---

# 10. Random Stochastic Matrix

Your helper function generates matrices by:

1. sampling random positive entries
    
2. normalizing rows
    
3. rounding entries
    
4. fixing row sums
    

Mathematically:

$$  
P_{ij}

\frac{A_{ij}}  
{\sum_k A_{ik}}  
$$

where $$A_{ij}>0$$ are random draws.

Most randomly generated positive matrices are:

- irreducible
    
- aperiodic
    
- ergodic
    

because positive entries imply strong connectivity.

---

# Communicating Classes

One of the most important structural ideas in Markov chains is communication.

State $$i$$ communicates with state $$j$$ if:

$$  
i \leftrightarrow j  
$$

meaning:

$$  
i \to j  
\quad \text{and} \quad  
j \to i  
$$

A communicating class is a maximal set of mutually reachable states.

These classes determine the chain's long-run structure.

---

# Transient vs Recurrent States

A state is:

- recurrent if it is revisited infinitely often
    
- transient if it can eventually be abandoned forever
    

For finite chains:

- closed irreducible classes are recurrent
    
- states outside closed classes are transient
    

This decomposition is fundamental to Markov chain theory.

---

# Stationary Distributions

A stationary distribution satisfies:

$$  
\pi P = \pi  
$$

Interpretation:

If the chain starts distributed as $$\pi$$, it remains distributed as $$\pi$$ forever.

For ergodic chains:

$$  
\lim_{n\to\infty} P^n(i,j)=\pi_j  
$$

independent of the starting state.

This is the mathematical basis of:

- PageRank
    
- MCMC
    
- Gibbs sampling
    
- Hidden Markov Models
    
- stochastic optimization
    

---

# Final Thoughts

These examples capture the major behaviors finite Markov chains can exhibit:

|Type|Key Feature|
|---|---|
|Ergodic|Converges to equilibrium|
|Periodic|Oscillates forever|
|Absorbing|Gets trapped|
|Reducible|Splits into disconnected regions|
|Fully connected|Rapid mixing|
|Transient flow|Temporary states vanish|

Markov chains are deceptively simple objects.

Yet from the single equation

$$  
P(X_{t+1}=j \mid X_t=i)  
$$

emerges an enormous theory connecting:

- probability
    
- linear algebra
    
- dynamical systems
    
- statistical mechanics
    
- machine learning
    

and modern AI itself.

# Appendix: Code Walkthrough

The code begins by defining a helper function, `random_stochastic_matrix(n=3, decimals=1)`, which generates a random stochastic matrix by first sampling a random positive matrix with `np.random.rand(n, n)`, normalizing each row so that the entries sum to $$1$$, rounding the entries for readability, and then correcting the final entry in each row to ensure exact row sums after rounding. A dictionary called `examples` stores a collection of representative Markov-chain transition matrices, including ergodic chains, periodic chains, absorbing chains, reducible chains, fully connected systems, transient-to-recurrent systems, and randomly generated chains. Each dictionary key is a descriptive label, while each value is a NumPy array representing the transition matrix. The program then initializes an empty dictionary called `results` and iterates through every example using `for name, P in examples.items():`. For each transition matrix $$P$$, the code prints the matrix, calls `classify_markov_chain(P)` to compute structural properties of the chain, stores the returned properties in the `results` dictionary, and prints a formatted summary of key characteristics including irreducibility, aperiodicity, ergodicity, communicating classes, closed classes, absorbing states, recurrent states, transient states, and periods. If the classification routine determines that a stationary distribution exists, the code prints the stationary distribution rounded to four decimal places using `np.round`. Overall, the script acts as a compact framework for generating, analyzing, and comparing representative finite-state Markov chains.

# References

{% bibliography --cited %}


<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="56abbd84-7825-4609-be40-64d647c2d6df" class="plotly-graph-div" style="height:100%; width:100%;">           <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("56abbd84-7825-4609-be40-64d647c2d6df")) {                    Plotly.newPlot(                        "56abbd84-7825-4609-be40-64d647c2d6df",                        [{"coloraxis":"coloraxis","name":"0","z":[[0.4,0.3,0.30000000000000004],[0.2,0.5,0.30000000000000004],[0.1,0.6,0.30000000000000004]],"type":"heatmap","xaxis":"x","yaxis":"y","hovertemplate":"To State: %{x}\u003cbr\u003eFrom State: %{y}\u003cbr\u003eProbability: %{z}\u003cextra\u003e\u003c\u002fextra\u003e"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#f2f5fa"},"error_y":{"color":"#f2f5fa"},"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"baxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"line":{"color":"#283442"}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"marker":{"line":{"color":"#283442"}},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#506784"},"line":{"color":"rgb(17,17,17)"}},"header":{"fill":{"color":"#2a3f5f"},"line":{"color":"rgb(17,17,17)"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#f2f5fa","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#f2f5fa"},"geo":{"bgcolor":"rgb(17,17,17)","lakecolor":"rgb(17,17,17)","landcolor":"rgb(17,17,17)","showlakes":true,"showland":true,"subunitcolor":"#506784"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"dark"},"paper_bgcolor":"rgb(17,17,17)","plot_bgcolor":"rgb(17,17,17)","polar":{"angularaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","radialaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"yaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"zaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"}},"shapedefaults":{"line":{"color":"#f2f5fa"}},"sliderdefaults":{"bgcolor":"#C8D4E3","bordercolor":"rgb(17,17,17)","borderwidth":1,"tickwidth":0},"ternary":{"aaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"baxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","caxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"title":{"x":0.05},"updatemenudefaults":{"bgcolor":"#506784","borderwidth":0},"xaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"scaleanchor":"y","constrain":"domain","title":{"text":"To State"},"tickmode":"linear","tick0":0,"dtick":1},"yaxis":{"anchor":"x","domain":[0.0,1.0],"autorange":"reversed","constrain":"domain","title":{"text":"From State"},"tickmode":"linear","tick0":0,"dtick":1},"coloraxis":{"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]],"cmin":0,"cmax":1},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"updatemenus":[{"buttons":[{"args":[null,{"frame":{"duration":500,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":500,"easing":"linear"}}],"label":"&#9654;","method":"animate"},{"args":[[null],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"&#9724;","method":"animate"}],"direction":"left","pad":{"r":10,"t":70},"showactive":false,"type":"buttons","x":0.1,"xanchor":"right","y":0,"yanchor":"top"}],"sliders":[{"active":0,"currentvalue":{"prefix":"Power="},"len":0.9,"pad":{"b":10,"t":60},"steps":[{"args":[["0"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"0","method":"animate"},{"args":[["1"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"1","method":"animate"},{"args":[["2"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"2","method":"animate"},{"args":[["3"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"3","method":"animate"},{"args":[["4"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"4","method":"animate"},{"args":[["5"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"5","method":"animate"},{"args":[["6"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"6","method":"animate"},{"args":[["7"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"7","method":"animate"},{"args":[["8"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"8","method":"animate"},{"args":[["9"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"9","method":"animate"},{"args":[["10"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"10","method":"animate"},{"args":[["11"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"11","method":"animate"},{"args":[["12"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"12","method":"animate"},{"args":[["13"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"13","method":"animate"},{"args":[["14"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"14","method":"animate"},{"args":[["15"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"15","method":"animate"},{"args":[["16"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"16","method":"animate"},{"args":[["17"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"17","method":"animate"},{"args":[["18"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"18","method":"animate"},{"args":[["19"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"19","method":"animate"}],"x":0.1,"xanchor":"left","y":0,"yanchor":"top"}]},                        {"responsive": true}                    ).then(function(){
                            Plotly.addFrames('56abbd84-7825-4609-be40-64d647c2d6df', [{"data":[{"coloraxis":"coloraxis","name":"0","z":[[0.4,0.3,0.30000000000000004],[0.2,0.5,0.30000000000000004],[0.1,0.6,0.30000000000000004]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"0"},{"data":[{"coloraxis":"coloraxis","name":"1","z":[[0.25000000000000006,0.45,0.30000000000000004],[0.21000000000000002,0.49,0.30000000000000004],[0.19,0.51,0.30000000000000004]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"1"},{"data":[{"coloraxis":"coloraxis","name":"2","z":[[0.22000000000000003,0.48000000000000004,0.3000000000000001],[0.21200000000000002,0.488,0.30000000000000004],[0.20800000000000002,0.492,0.3000000000000001]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"2"},{"data":[{"coloraxis":"coloraxis","name":"3","z":[[0.21400000000000005,0.48600000000000004,0.3000000000000001],[0.21240000000000006,0.48760000000000003,0.30000000000000004],[0.21160000000000004,0.48840000000000006,0.3000000000000001]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"3"},{"data":[{"coloraxis":"coloraxis","name":"4","z":[[0.21280000000000004,0.4872000000000001,0.3000000000000001],[0.21248000000000006,0.48752000000000006,0.3000000000000001],[0.21232000000000004,0.48768000000000006,0.30000000000000004]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"4"},{"data":[{"coloraxis":"coloraxis","name":"5","z":[[0.21256000000000005,0.4874400000000001,0.3000000000000001],[0.21249600000000005,0.48750400000000005,0.3000000000000001],[0.21246400000000004,0.4875360000000001,0.3000000000000001]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"5"},{"data":[{"coloraxis":"coloraxis","name":"6","z":[[0.21251200000000006,0.48748800000000014,0.3000000000000001],[0.21249920000000005,0.4875008000000001,0.3000000000000001],[0.21249280000000006,0.4875072000000001,0.3000000000000001]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"6"},{"data":[{"coloraxis":"coloraxis","name":"7","z":[[0.2125024000000001,0.48749760000000014,0.30000000000000016],[0.21249984000000008,0.4875001600000001,0.3000000000000001],[0.2124985600000001,0.4875014400000001,0.30000000000000016]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"7"},{"data":[{"coloraxis":"coloraxis","name":"8","z":[[0.2125004800000001,0.48749952000000013,0.30000000000000016],[0.2124999680000001,0.48750003200000014,0.30000000000000016],[0.2124997120000001,0.4875002880000001,0.30000000000000016]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"8"},{"data":[{"coloraxis":"coloraxis","name":"9","z":[[0.2125000960000001,0.48749990400000015,0.30000000000000016],[0.2124999936000001,0.48750000640000013,0.30000000000000016],[0.21249994240000009,0.48750005760000015,0.30000000000000016]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"9"},{"data":[{"coloraxis":"coloraxis","name":"10","z":[[0.2125000192000001,0.4874999808000002,0.30000000000000016],[0.2124999987200001,0.4875000012800002,0.30000000000000016],[0.2124999884800001,0.48750001152000016,0.30000000000000016]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"10"},{"data":[{"coloraxis":"coloraxis","name":"11","z":[[0.21250000384000012,0.4874999961600002,0.30000000000000016],[0.2124999997440001,0.4875000002560002,0.30000000000000016],[0.21249999769600011,0.48750000230400026,0.30000000000000016]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"11"},{"data":[{"coloraxis":"coloraxis","name":"12","z":[[0.21250000076800013,0.48749999923200027,0.3000000000000002],[0.21249999994880012,0.48750000005120026,0.3000000000000002],[0.21249999953920012,0.48750000046080016,0.30000000000000016]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"12"},{"data":[{"coloraxis":"coloraxis","name":"13","z":[[0.21250000015360013,0.48749999984640024,0.3000000000000002],[0.2124999999897601,0.48750000001024024,0.30000000000000016],[0.21249999990784013,0.48750000009216027,0.3000000000000002]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"13"},{"data":[{"coloraxis":"coloraxis","name":"14","z":[[0.21250000003072014,0.4874999999692803,0.3000000000000002],[0.21249999999795213,0.4875000000020483,0.3000000000000002],[0.21249999998156813,0.48750000001843224,0.3000000000000002]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"14"},{"data":[{"coloraxis":"coloraxis","name":"15","z":[[0.21250000000614416,0.4874999999938563,0.30000000000000027],[0.21249999999959054,0.4875000000004099,0.3000000000000002],[0.21249999999631378,0.4875000000036867,0.30000000000000027]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"15"},{"data":[{"coloraxis":"coloraxis","name":"16","z":[[0.21250000000122896,0.4874999999987715,0.30000000000000027],[0.21249999999991825,0.48750000000008226,0.30000000000000027],[0.21249999999926286,0.4875000000007376,0.30000000000000027]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"16"},{"data":[{"coloraxis":"coloraxis","name":"17","z":[[0.21250000000024594,0.48749999999975463,0.30000000000000027],[0.21249999999998379,0.4875000000000167,0.30000000000000027],[0.2124999999998527,0.4875000000001478,0.30000000000000027]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"17"},{"data":[{"coloraxis":"coloraxis","name":"18","z":[[0.21250000000004934,0.48749999999995125,0.30000000000000027],[0.2124999999999969,0.48750000000000365,0.30000000000000027],[0.21249999999997068,0.48750000000002985,0.30000000000000027]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"18"},{"data":[{"coloraxis":"coloraxis","name":"19","z":[[0.21250000000001004,0.48749999999999055,0.3000000000000003],[0.21249999999999952,0.48750000000000104,0.30000000000000027],[0.2124999999999943,0.48750000000000626,0.3000000000000003]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: random_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"19"}]);
                        }).then(function(){
                            Plotly.animate('56abbd84-7825-4609-be40-64d647c2d6df', null);
                        })                };                            </script>        


<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="0f432133-5f75-4617-93c5-e284df99e555" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("0f432133-5f75-4617-93c5-e284df99e555")) {                    Plotly.newPlot(                        "0f432133-5f75-4617-93c5-e284df99e555",                        [{"coloraxis":"coloraxis","name":"0","z":[[1.0,0.0],[0.4,0.6]],"type":"heatmap","xaxis":"x","yaxis":"y","hovertemplate":"To State: %{x}\u003cbr\u003eFrom State: %{y}\u003cbr\u003eProbability: %{z}\u003cextra\u003e\u003c\u002fextra\u003e"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#f2f5fa"},"error_y":{"color":"#f2f5fa"},"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"baxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"line":{"color":"#283442"}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"marker":{"line":{"color":"#283442"}},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#506784"},"line":{"color":"rgb(17,17,17)"}},"header":{"fill":{"color":"#2a3f5f"},"line":{"color":"rgb(17,17,17)"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#f2f5fa","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#f2f5fa"},"geo":{"bgcolor":"rgb(17,17,17)","lakecolor":"rgb(17,17,17)","landcolor":"rgb(17,17,17)","showlakes":true,"showland":true,"subunitcolor":"#506784"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"dark"},"paper_bgcolor":"rgb(17,17,17)","plot_bgcolor":"rgb(17,17,17)","polar":{"angularaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","radialaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"yaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"zaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"}},"shapedefaults":{"line":{"color":"#f2f5fa"}},"sliderdefaults":{"bgcolor":"#C8D4E3","bordercolor":"rgb(17,17,17)","borderwidth":1,"tickwidth":0},"ternary":{"aaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"baxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","caxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"title":{"x":0.05},"updatemenudefaults":{"bgcolor":"#506784","borderwidth":0},"xaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"scaleanchor":"y","constrain":"domain","title":{"text":"To State"},"tickmode":"linear","tick0":0,"dtick":1},"yaxis":{"anchor":"x","domain":[0.0,1.0],"autorange":"reversed","constrain":"domain","title":{"text":"From State"},"tickmode":"linear","tick0":0,"dtick":1},"coloraxis":{"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]],"cmin":0,"cmax":1},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"updatemenus":[{"buttons":[{"args":[null,{"frame":{"duration":500,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":500,"easing":"linear"}}],"label":"&#9654;","method":"animate"},{"args":[[null],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"&#9724;","method":"animate"}],"direction":"left","pad":{"r":10,"t":70},"showactive":false,"type":"buttons","x":0.1,"xanchor":"right","y":0,"yanchor":"top"}],"sliders":[{"active":0,"currentvalue":{"prefix":"Power="},"len":0.9,"pad":{"b":10,"t":60},"steps":[{"args":[["0"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"0","method":"animate"},{"args":[["1"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"1","method":"animate"},{"args":[["2"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"2","method":"animate"},{"args":[["3"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"3","method":"animate"},{"args":[["4"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"4","method":"animate"},{"args":[["5"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"5","method":"animate"},{"args":[["6"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"6","method":"animate"},{"args":[["7"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"7","method":"animate"},{"args":[["8"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"8","method":"animate"},{"args":[["9"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"9","method":"animate"},{"args":[["10"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"10","method":"animate"},{"args":[["11"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"11","method":"animate"},{"args":[["12"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"12","method":"animate"},{"args":[["13"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"13","method":"animate"},{"args":[["14"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"14","method":"animate"},{"args":[["15"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"15","method":"animate"},{"args":[["16"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"16","method":"animate"},{"args":[["17"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"17","method":"animate"},{"args":[["18"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"18","method":"animate"},{"args":[["19"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"19","method":"animate"}],"x":0.1,"xanchor":"left","y":0,"yanchor":"top"}]},                        {"responsive": true}                    ).then(function(){
                            Plotly.addFrames('0f432133-5f75-4617-93c5-e284df99e555', [{"data":[{"coloraxis":"coloraxis","name":"0","z":[[1.0,0.0],[0.4,0.6]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"0"},{"data":[{"coloraxis":"coloraxis","name":"1","z":[[1.0,0.0],[0.64,0.36]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"1"},{"data":[{"coloraxis":"coloraxis","name":"2","z":[[1.0,0.0],[0.784,0.216]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"2"},{"data":[{"coloraxis":"coloraxis","name":"3","z":[[1.0,0.0],[0.8704000000000001,0.1296]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"3"},{"data":[{"coloraxis":"coloraxis","name":"4","z":[[1.0,0.0],[0.9222400000000001,0.07776]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"4"},{"data":[{"coloraxis":"coloraxis","name":"5","z":[[1.0,0.0],[0.953344,0.046655999999999996]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"5"},{"data":[{"coloraxis":"coloraxis","name":"6","z":[[1.0,0.0],[0.9720064,0.027993599999999997]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"6"},{"data":[{"coloraxis":"coloraxis","name":"7","z":[[1.0,0.0],[0.98320384,0.016796159999999997]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"7"},{"data":[{"coloraxis":"coloraxis","name":"8","z":[[1.0,0.0],[0.989922304,0.010077695999999999]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"8"},{"data":[{"coloraxis":"coloraxis","name":"9","z":[[1.0,0.0],[0.9939533824,0.006046617599999999]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"9"},{"data":[{"coloraxis":"coloraxis","name":"10","z":[[1.0,0.0],[0.99637202944,0.0036279705599999994]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"10"},{"data":[{"coloraxis":"coloraxis","name":"11","z":[[1.0,0.0],[0.9978232176640001,0.0021767823359999995]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"11"},{"data":[{"coloraxis":"coloraxis","name":"12","z":[[1.0,0.0],[0.9986939305984001,0.0013060694015999998]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"12"},{"data":[{"coloraxis":"coloraxis","name":"13","z":[[1.0,0.0],[0.99921635835904,0.0007836416409599998]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"13"},{"data":[{"coloraxis":"coloraxis","name":"14","z":[[1.0,0.0],[0.999529815015424,0.0004701849845759999]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"14"},{"data":[{"coloraxis":"coloraxis","name":"15","z":[[1.0,0.0],[0.9997178890092544,0.0002821109907455999]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"15"},{"data":[{"coloraxis":"coloraxis","name":"16","z":[[1.0,0.0],[0.9998307334055526,0.00016926659444735994]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"16"},{"data":[{"coloraxis":"coloraxis","name":"17","z":[[1.0,0.0],[0.9998984400433316,0.00010155995666841596]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"17"},{"data":[{"coloraxis":"coloraxis","name":"18","z":[[1.0,0.0],[0.999939064025999,0.00006093597400104958]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"18"},{"data":[{"coloraxis":"coloraxis","name":"19","z":[[1.0,0.0],[0.9999634384155994,0.00003656158440062975]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: absorbing_chain"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"19"}]);
                        }).then(function(){
                            Plotly.animate('0f432133-5f75-4617-93c5-e284df99e555', null);
                        })                };                            </script>        

    

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="a8ff4a41-2cbb-4203-80d0-895bf7642f27" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("a8ff4a41-2cbb-4203-80d0-895bf7642f27")) {                    Plotly.newPlot(                        "a8ff4a41-2cbb-4203-80d0-895bf7642f27",                        [{"coloraxis":"coloraxis","name":"0","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.5,0.0,0.5,0.0],[0.0,0.5,0.0,0.5]],"type":"heatmap","xaxis":"x","yaxis":"y","hovertemplate":"To State: %{x}\u003cbr\u003eFrom State: %{y}\u003cbr\u003eProbability: %{z}\u003cextra\u003e\u003c\u002fextra\u003e"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#f2f5fa"},"error_y":{"color":"#f2f5fa"},"marker":{"line":{"color":"rgb(17,17,17)","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"baxis":{"endlinecolor":"#A2B1C6","gridcolor":"#506784","linecolor":"#506784","minorgridcolor":"#506784","startlinecolor":"#A2B1C6"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"line":{"color":"#283442"}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"marker":{"line":{"color":"#283442"}},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#506784"},"line":{"color":"rgb(17,17,17)"}},"header":{"fill":{"color":"#2a3f5f"},"line":{"color":"rgb(17,17,17)"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#f2f5fa","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#f2f5fa"},"geo":{"bgcolor":"rgb(17,17,17)","lakecolor":"rgb(17,17,17)","landcolor":"rgb(17,17,17)","showlakes":true,"showland":true,"subunitcolor":"#506784"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"dark"},"paper_bgcolor":"rgb(17,17,17)","plot_bgcolor":"rgb(17,17,17)","polar":{"angularaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","radialaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"yaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"},"zaxis":{"backgroundcolor":"rgb(17,17,17)","gridcolor":"#506784","gridwidth":2,"linecolor":"#506784","showbackground":true,"ticks":"","zerolinecolor":"#C8D4E3"}},"shapedefaults":{"line":{"color":"#f2f5fa"}},"sliderdefaults":{"bgcolor":"#C8D4E3","bordercolor":"rgb(17,17,17)","borderwidth":1,"tickwidth":0},"ternary":{"aaxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"baxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""},"bgcolor":"rgb(17,17,17)","caxis":{"gridcolor":"#506784","linecolor":"#506784","ticks":""}},"title":{"x":0.05},"updatemenudefaults":{"bgcolor":"#506784","borderwidth":0},"xaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#283442","linecolor":"#506784","ticks":"","title":{"standoff":15},"zerolinecolor":"#283442","zerolinewidth":2}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"scaleanchor":"y","constrain":"domain","title":{"text":"To State"},"tickmode":"linear","tick0":0,"dtick":1},"yaxis":{"anchor":"x","domain":[0.0,1.0],"autorange":"reversed","constrain":"domain","title":{"text":"From State"},"tickmode":"linear","tick0":0,"dtick":1},"coloraxis":{"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]],"cmin":0,"cmax":1},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"updatemenus":[{"buttons":[{"args":[null,{"frame":{"duration":500,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":500,"easing":"linear"}}],"label":"&#9654;","method":"animate"},{"args":[[null],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"&#9724;","method":"animate"}],"direction":"left","pad":{"r":10,"t":70},"showactive":false,"type":"buttons","x":0.1,"xanchor":"right","y":0,"yanchor":"top"}],"sliders":[{"active":0,"currentvalue":{"prefix":"Power="},"len":0.9,"pad":{"b":10,"t":60},"steps":[{"args":[["0"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"0","method":"animate"},{"args":[["1"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"1","method":"animate"},{"args":[["2"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"2","method":"animate"},{"args":[["3"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"3","method":"animate"},{"args":[["4"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"4","method":"animate"},{"args":[["5"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"5","method":"animate"},{"args":[["6"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"6","method":"animate"},{"args":[["7"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"7","method":"animate"},{"args":[["8"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"8","method":"animate"},{"args":[["9"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"9","method":"animate"},{"args":[["10"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"10","method":"animate"},{"args":[["11"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"11","method":"animate"},{"args":[["12"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"12","method":"animate"},{"args":[["13"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"13","method":"animate"},{"args":[["14"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"14","method":"animate"},{"args":[["15"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"15","method":"animate"},{"args":[["16"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"16","method":"animate"},{"args":[["17"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"17","method":"animate"},{"args":[["18"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"18","method":"animate"},{"args":[["19"],{"frame":{"duration":0,"redraw":true},"mode":"immediate","fromcurrent":true,"transition":{"duration":0,"easing":"linear"}}],"label":"19","method":"animate"}],"x":0.1,"xanchor":"left","y":0,"yanchor":"top"}]},                        {"responsive": true}                    ).then(function(){
                            Plotly.addFrames('a8ff4a41-2cbb-4203-80d0-895bf7642f27', [{"data":[{"coloraxis":"coloraxis","name":"0","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.5,0.0,0.5,0.0],[0.0,0.5,0.0,0.5]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"0"},{"data":[{"coloraxis":"coloraxis","name":"1","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.75,0.0,0.25,0.0],[0.0,0.75,0.0,0.25]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"1"},{"data":[{"coloraxis":"coloraxis","name":"2","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.875,0.0,0.125,0.0],[0.0,0.875,0.0,0.125]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"2"},{"data":[{"coloraxis":"coloraxis","name":"3","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9375,0.0,0.0625,0.0],[0.0,0.9375,0.0,0.0625]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"3"},{"data":[{"coloraxis":"coloraxis","name":"4","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.96875,0.0,0.03125,0.0],[0.0,0.96875,0.0,0.03125]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"4"},{"data":[{"coloraxis":"coloraxis","name":"5","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.984375,0.0,0.015625,0.0],[0.0,0.984375,0.0,0.015625]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"5"},{"data":[{"coloraxis":"coloraxis","name":"6","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9921875,0.0,0.0078125,0.0],[0.0,0.9921875,0.0,0.0078125]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"6"},{"data":[{"coloraxis":"coloraxis","name":"7","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.99609375,0.0,0.00390625,0.0],[0.0,0.99609375,0.0,0.00390625]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"7"},{"data":[{"coloraxis":"coloraxis","name":"8","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.998046875,0.0,0.001953125,0.0],[0.0,0.998046875,0.0,0.001953125]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"8"},{"data":[{"coloraxis":"coloraxis","name":"9","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9990234375,0.0,0.0009765625,0.0],[0.0,0.9990234375,0.0,0.0009765625]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"9"},{"data":[{"coloraxis":"coloraxis","name":"10","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.99951171875,0.0,0.00048828125,0.0],[0.0,0.99951171875,0.0,0.00048828125]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"10"},{"data":[{"coloraxis":"coloraxis","name":"11","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.999755859375,0.0,0.000244140625,0.0],[0.0,0.999755859375,0.0,0.000244140625]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"11"},{"data":[{"coloraxis":"coloraxis","name":"12","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9998779296875,0.0,0.0001220703125,0.0],[0.0,0.9998779296875,0.0,0.0001220703125]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"12"},{"data":[{"coloraxis":"coloraxis","name":"13","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.99993896484375,0.0,0.00006103515625,0.0],[0.0,0.99993896484375,0.0,0.00006103515625]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"13"},{"data":[{"coloraxis":"coloraxis","name":"14","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.999969482421875,0.0,0.000030517578125,0.0],[0.0,0.999969482421875,0.0,0.000030517578125]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"14"},{"data":[{"coloraxis":"coloraxis","name":"15","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9999847412109375,0.0,0.0000152587890625,0.0],[0.0,0.9999847412109375,0.0,0.0000152587890625]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"15"},{"data":[{"coloraxis":"coloraxis","name":"16","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9999923706054688,0.0,7.62939453125e-6,0.0],[0.0,0.9999923706054688,0.0,7.62939453125e-6]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"16"},{"data":[{"coloraxis":"coloraxis","name":"17","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9999961853027344,0.0,3.814697265625e-6,0.0],[0.0,0.9999961853027344,0.0,3.814697265625e-6]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"17"},{"data":[{"coloraxis":"coloraxis","name":"18","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9999980926513672,0.0,1.9073486328125e-6,0.0],[0.0,0.9999980926513672,0.0,1.9073486328125e-6]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"18"},{"data":[{"coloraxis":"coloraxis","name":"19","z":[[1.0,0.0,0.0,0.0],[0.0,1.0,0.0,0.0],[0.9999990463256836,0.0,9.5367431640625e-7,0.0],[0.0,0.9999990463256836,0.0,9.5367431640625e-7]],"type":"heatmap"}],"layout":{"xaxis":{"constrain":"domain","scaleanchor":"y"},"yaxis":{"autorange":"reversed","constrain":"domain"},"title":{"text":"Evolution of Transition Matrix Powers: multiple_closed_classes"},"coloraxis":{"cmax":1,"cmin":0,"colorbar":{"title":{"text":"Probability"}},"colorscale":[[0.0,"#440154"],[0.1111111111111111,"#482878"],[0.2222222222222222,"#3e4989"],[0.3333333333333333,"#31688e"],[0.4444444444444444,"#26828e"],[0.5555555555555556,"#1f9e89"],[0.6666666666666666,"#35b779"],[0.7777777777777778,"#6ece58"],[0.8888888888888888,"#b5de2b"],[1.0,"#fde725"]]}},"name":"19"}]);
                        }).then(function(){
                            Plotly.animate('a8ff4a41-2cbb-4203-80d0-895bf7642f27', null);
                        })                };                            </script>        </div>