---
layout: post
title:  "Solving Multivariate Time-Dependent Ordinary Differential Equations (ODE) with Runge-Kutta Method"
date:   2023-12-29 06:25:17 -0800
categories: jekyll update data
---
# Introduction

When delving into the simulation of physical systems, a common approach involves solving differential equations that describe the evolution of the system over time. In this blog post, we'll take a closer look at a specific example: the motion of an object subject to gravity and a time-dependent force. We'll represent the governing differential equation in matrix form, implement a numerical solution using the Runge-Kutta method in Python, and visualize the results using Matplotlib.

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="8addf313-3c73-4ea2-a549-98c2a211fcb9" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("8addf313-3c73-4ea2-a549-98c2a211fcb9")) {                    Plotly.newPlot(                        "8addf313-3c73-4ea2-a549-98c2a211fcb9",                        [{"line":{"color":"red"},"mode":"lines","name":"Height","x":[0.0,0.08,0.16,0.24,0.32,0.4,0.48,0.56,0.64,0.72,0.8,0.88,0.96,1.04,1.12,1.2,1.28,1.36,1.44,1.52,1.6,1.68,1.76,1.84,1.92,2.0,2.08,2.16,2.24,2.32,2.4,2.48,2.56,2.64,2.72,2.8000000000000003,2.88,2.96,3.04,3.12,3.2,3.2800000000000002,3.36,3.44,3.52,3.6,3.68,3.7600000000000002,3.84,3.92,4.0,4.08,4.16,4.24,4.32,4.4,4.48,4.5600000000000005,4.64,4.72,4.8,4.88,4.96,5.04,5.12,5.2,5.28,5.36,5.44,5.5200000000000005,5.6000000000000005,5.68,5.76,5.84,5.92,6.0,6.08,6.16,6.24,6.32,6.4,6.48,6.5600000000000005,6.640000000000001,6.72,6.8,6.88,6.96,7.04,7.12,7.2,7.28,7.36,7.44,7.5200000000000005,7.6000000000000005,7.68,7.76,7.84,7.92,8.0],"y":[100.0,99.99534575649372,100.0862323499824,100.42103648567456,101.12886368291274,102.31143610057626,104.03670095973095,106.33456116983716,109.19499641897316,112.56869278688531,116.3701413199615,120.48301087326658,124.76745762421459,129.06891197425148,133.2277907251995,137.08952427850457,140.51426881158076,143.3856931794929,145.61828842862892,147.16274063873513,148.00902949788983,148.18705791555334,147.76477311279152,146.84389724848367,145.55353584197235,144.04206559846605,142.46781135495976,140.98909794844843,139.7543020841406,138.89252928137876,138.50550169904227,138.66116655819695,139.38942676830317,140.68026201743916,142.4843583853513,144.7162069184275,147.25947647173257,149.97432322268057,152.70617757271745,155.29545632366546,157.58758987697053,159.4427344100467,160.74455877795884,161.40755402709485,161.38240623720105,160.65909509635574,159.26752351401927,157.27563871125744,154.7851628469496,151.92520144043826,148.84413119693198,145.70027695342569,142.65196354691435,139.8475676826065,137.41619487984468,135.45956729750822,134.04563215666292,133.20429236676912,132.9255276159051,133.16002398381724,133.82227251689343,134.79594207019852,135.94118882114654,137.10344317118344,138.12312192213145,138.84565547543653,139.13120000851274,138.8634243764249,137.95681962556088,136.3620718356671,134.06916069482182,131.10798911248534,127.54650430972352,123.48642844541568,119.05686703890436,114.40619679539807,109.6927425518918,105.07482914538046,100.70083328107262,96.6998604783108,93.17363289597432,90.19009775512902,87.77915796523523,85.93079321437122,84.59568958228336,83.68833811535956,83.09240766866463,82.66805441961264,82.26070876964954,81.71078752059755,80.86372107390262,79.57966560697882,77.74228997489097,75.26608522402697,72.10173743413318,68.23922629328789,63.708454710951415,58.577369908189596,52.947694043881754,46.94853263737042,40.728262393864135],"type":"scatter"},{"line":{"color":"blue"},"mode":"lines","name":"Velocity","x":[0.0,0.08,0.16,0.24,0.32,0.4,0.48,0.56,0.64,0.72,0.8,0.88,0.96,1.04,1.12,1.2,1.28,1.36,1.44,1.52,1.6,1.68,1.76,1.84,1.92,2.0,2.08,2.16,2.24,2.32,2.4,2.48,2.56,2.64,2.72,2.8000000000000003,2.88,2.96,3.04,3.12,3.2,3.2800000000000002,3.36,3.44,3.52,3.6,3.68,3.7600000000000002,3.84,3.92,4.0,4.08,4.16,4.24,4.32,4.4,4.48,4.5600000000000005,4.64,4.72,4.8,4.88,4.96,5.04,5.12,5.2,5.28,5.36,5.44,5.5200000000000005,5.6000000000000005,5.68,5.76,5.84,5.92,6.0,6.08,6.16,6.24,6.32,6.4,6.48,6.5600000000000005,6.640000000000001,6.72,6.8,6.88,6.96,7.04,7.12,7.2,7.28,7.36,7.44,7.5200000000000005,7.6000000000000005,7.68,7.76,7.84,7.92,8.0],"y":[0.0,0.2152304285627624,2.3676861245698047,6.2728085101702,11.63591251354868,18.070702715763677,25.123545712614582,32.301973569774646,39.105627394275075,45.05769672394157,49.73487928231892,52.7939786174976,53.99346839737547,53.208668397375476,50.4395786174976,45.810879282318915,39.56409672394156,32.042427394275066,23.669173569774635,14.921145712614573,6.298702715763666,-1.7056874864513318,-8.638391489829814,-14.113113875430212,-17.835169571437255,-19.620000000000022,-19.40476957143726,-17.252313875430215,-13.347191489829816,-7.984087486451335,-1.5492972842363413,5.503545712614565,12.681973569774627,19.485627394275056,25.437696723941546,30.1148792823189,33.17397861749758,34.373468397375454,33.58866839737546,30.81957861749759,26.190879282318907,19.94409672394155,12.422427394275054,4.049173569774625,-4.698854287385437,-13.321297284236344,-21.325687486451336,-28.258391489829815,-33.73311387543021,-37.45516957143726,-39.24000000000002,-39.02476957143727,-36.87231387543023,-32.96719148982984,-27.604087486451355,-21.169297284236357,-14.116454287385451,-6.938026430225389,-0.1343726057249608,5.8176967239415385,10.494879282318902,13.553978617497592,14.753468397375466,13.96866839737547,11.199578617497604,6.570879282318921,0.32409672394156885,-7.197572605724926,-15.570826430225356,-24.31885428738542,-32.94129728423633,-40.94568748645132,-47.87839148982981,-53.35311387543021,-57.075169571437264,-58.86000000000003,-58.64476957143728,-56.492313875430234,-52.58719148982984,-47.22408748645135,-40.789297284236355,-33.73645428738545,-26.558026430225386,-19.754372605724956,-13.80230327605847,-9.12512071768111,-6.0660213825024165,-4.866531602624548,-5.651331602624541,-8.420421382502397,-13.04912071768108,-19.29590327605843,-26.817572605724923,-35.19082643022536,-43.93885428738542,-52.561297284236325,-60.56568748645132,-67.49839148982981,-72.97311387543022,-76.69516957143728,-78.48000000000005],"type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"yaxis":{"tickfont":{"color":"red"},"title":{"text":"Height (m)"},"anchor":"x","overlaying":"y"},"yaxis2":{"title":{"text":"Velocity (m\u002fs)","font":{"color":"blue"}},"tickfont":{"color":"blue"},"anchor":"x","overlaying":"y","side":"right"},"xaxis":{"title":{"text":"Time (s)"}}},                        {"responsive": true}                    )                };                            </script>        </div>

## Understanding the Differential Equation

The differential equation that models the system is expressed in matrix form as:



$$
\frac{d}{dt} \begin{bmatrix} h \\ v \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix} \begin{bmatrix} h \\ v \end{bmatrix} + \begin{bmatrix} 0 \\ -g + F(t) \end{bmatrix}
$$

Here:
- \\( h \\) represents the height of the object.
- \\( v \\) represents its velocity.
- \\( g \\) is the gravitational constant (9.81 m/s<sup>2</sup>).
- \\( F(t) \\) is a time-dependent force, introduced here as \\( 100 \sin(\pi t) \\).

## Implementing the Runge-Kutta Method

The Python code provided implements the fourth-order Runge-Kutta method. This numerical technique involves iteratively updating the solution based on weighted averages of function evaluations at different points within each time step. Let's break down the key components of the code:

### The `f` Function

```python
def f(t, w):
    g = 9.81  # m/s^2, gravitational constant
    
    # Introduce a time-dependent force
    force = 100 * np.sin(np.pi * t)
    
    b = np.array([[0.], [-g + force]])

    L = np.array([[0., 1.], [0., 0.]])
    return L @ w + b
```

This function defines the right-hand side of the differential equation. It calculates the derivative of the state vector \\( \begin{bmatrix} h \\ v \end{bmatrix} \\) with respect to time.

### The `runge_kutta` Function

```python
def runge_kutta(f, a, b, N, alpha):
    h = (b - a) / N
    t = a
    w = alpha
    
    time_steps = [t]
    heights = [w[0, 0]]
    velocities = [w[1, 0]]

    for i in range(1, N+1):
        K1 = h * f(t, w)
        K2 = h * f(t + h/2, w + K1/2)
        K3 = h * f(t + h/2, w + K2/2)
        K4 = h * f(t + h, w + K3)

        w = w + (K1 + 2*K2 + 2*K3 + K4) / 6
        t = a + i * h

        time_steps.append(t)
        heights.append(w[0, 0])
        velocities.append(w[1, 0])

    return time_steps, heights, velocities
```

This function performs the actual numerical integration using the Runge-Kutta method. It takes the differential equation function `f`, the time interval `[a, b]`, the number of steps `N`, and the initial condition `alpha`.

### Initial Conditions and Time Parameters

```python
h0 = 100.0  # initial height
v0 = 0.0    # initial velocity
alpha = np.asarray([[h0], [v0]])
a = 0.0
b = 8.0
N = 100  # 
```

These variables set up the initial conditions of the system and define the time interval over which the simulation will run.

### Solving the Differential Equation and Plotting

```python
# Solve the differential equation using Runge-Kutta
time_steps, heights, velocities = runge_kutta(f, a, b, N, alpha)

# Plotting
fig, ax1 = plt.subplots()

color = 'tab:red'
ax1.set_xlabel('Time (s)')
ax1.set_ylabel('Height (m)', color=color)
ax1.plot(time_steps, heights, color=color)
ax1.tick_params(axis='y', labelcolor=color)

ax2 = ax1.twinx()
color = 'tab:blue'
ax2.set_ylabel('Velocity (m/s)', color=color)
ax2.plot(time_steps, velocities, color=color)
ax2.tick_params(axis='y', labelcolor=color)

fig.tight_layout()
plt.show()
```

This part of the code calls the `runge_kutta` function to obtain the solution and then visualizes the results using Matplotlib.

## Conclusion

In summary, this blog post has covered the matrix representation of a time-dependent differential equation, the implementation of the Runge-Kutta method in Python, and the visualization of the simulation results. Understanding and applying numerical methods to solve such equations are crucial skills in various scientific and engineering disciplines. Experiment with different parameters and initial conditions to observe how the system's behavior changes in response to these modifications.
