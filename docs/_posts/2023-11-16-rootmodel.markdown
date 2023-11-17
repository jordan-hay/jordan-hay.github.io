---
layout: post
title:  "Mathematical Modeling of Root Growth Trajectory"
date:   2023-11-16 06:25:17 -0800
categories: jekyll update biology
---

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>                <div id="728218da-8827-41c5-a5d7-9eb432f88808" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("728218da-8827-41c5-a5d7-9eb432f88808")) {                    Plotly.newPlot(                        "728218da-8827-41c5-a5d7-9eb432f88808",                        [{"marker":{"color":"red","size":10},"mode":"markers","name":"Original Points","x":[0.0,1.6765069307335931,1.7410843200375428,7.73987674858963,8.0],"y":[-0.0,-1.6,-2.7,-4.0,-5.0],"type":"scatter"},{"line":{"color":"blue"},"mode":"lines","name":"Spline Interpolation","x":[0.0,0.2553827073816337,0.48878593513983126,0.7010243370193833,0.8929125667650799,1.0652652781217118,1.2188971248340696,1.3546227606469434,1.4732568393051242,1.575614014553402,1.6625089401365678,1.7347562697994117,1.7931706572867243,1.8385667563432957,1.8717592207139164,1.8935627041433782,1.90479186037647,1.9062613431579827,1.8987858062327079,1.8831799033454342,1.860258288240953,1.8308356146640552,1.795726536359531,1.7557457070721707,1.7117077805467649,1.6644274105281034,1.6147192507609776,1.5633979549901778,1.5112781769604944,1.459174570416718,1.407901789103639,1.3582744867660475,1.3111073171487344,1.26721493399649,1.2274119910541048,1.1925131420663697,1.1633330407780749,1.1406863409340104,1.1253876962789675,1.1182517605577362,1.120093187515107,1.1317266308958702,1.153966744444817,1.1876281819067371,1.2335255970264214,1.2924736435486606,1.3652869752182446,1.4527802457799641,1.5557681089786093,1.675065218558971,1.811446613613456,1.9647761962296235,2.1340067314901856,2.3180513698254726,2.515823261665816,2.7262355574415404,2.9482014075829803,3.180633962520459,3.422446372684309,3.672551788504862,3.9298633604124413,4.193294238837383,4.461757574210008,4.734166516960654,5.009434217519644,5.286473826317306,5.5641984937839775,5.84152137034998,6.117355606445648,6.390614352501305,6.660210758947285,6.925057976213913,7.184069154731521,7.436157444930439,7.680235997240994,7.915217962093518,8.140016489918336,8.35354473114578,8.554715836206178,8.742442955529858,8.915639239547154,9.07321783868839,9.214091903383899,9.337174584064007,9.441379031159043,9.525618395099341,9.588805826315227,9.629854475237028,9.647677492295077,9.6411880279197,9.609299232541227,9.550924256589989,9.464976250496312,9.350368364690528,9.206013749602967,9.030825555663958,8.823716933303826,8.5836010329529,8.309391005041517,8.0],"y":[0.0,-0.08700211652971568,-0.1716214623877106,-0.25392399662372095,-0.333975678287483,-0.41184246642873296,-0.4875903200972069,-0.5612851983426411,-0.632993060214772,-0.7027798647633355,-0.7707115710380681,-0.8368541380887057,-0.9012735249649848,-0.9640356907166414,-1.0252065943934119,-1.084852195045032,-1.143038451721239,-1.1998313234717684,-1.255296769346356,-1.309500748394739,-1.3625092196666526,-1.4143881422118336,-1.4652034750800185,-1.5150211773209428,-1.563907207984343,-1.6119275261199555,-1.6591480907775167,-1.7056348610067622,-1.7514537958574286,-1.7966708543792518,-1.8413519956219684,-1.8855631786353144,-1.9293703624690264,-1.9728395061728399,-2.016036568796492,-2.059027509389718,-2.1018782870022545,-2.1446548606838376,-2.1874231894842042,-2.2302492324530894,-2.2731989486402306,-2.316338297095363,-2.3597332368682236,-2.4034497270085478,-2.4475537265660727,-2.492111194590534,-2.537188090131668,-2.58285037223921,-2.629163999962898,-2.6761949323524674,-2.724006654993289,-2.772605763790337,-2.821941964968187,-2.87196249128705,-2.922614575507138,-2.9738454503886604,-3.02560234869183,-3.077832503176856,-3.1304831466039507,-3.183501511733325,-3.23683483132519,-3.290430338139756,-3.344235264937234,-3.398196844477837,-3.4522623095217733,-3.506378892829255,-3.5604938271604945,-3.6145543452757,-3.668507679935086,-3.7223010638988607,-3.775881729927236,-3.8291969107804236,-3.882193839218633,-3.9348197480020763,-3.9870218698909654,-4.03874743764551,-4.089943684025921,-4.140557841792409,-4.190537143705187,-4.239828822524466,-4.288380111010455,-4.336138241923367,-4.38305044802341,-4.429063962070798,-4.474126016825742,-4.518183845048451,-4.561184679499138,-4.603075752938012,-4.643804298125286,-4.6833175478211695,-4.721562734785874,-4.758487091779613,-4.794037851562594,-4.828162246895029,-4.86080751053713,-4.891920875249107,-4.921449573791171,-4.949340838923535,-4.975541903406407,-5.0],"type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"title":{"text":"Root Trajectory Projection in 2D with Spline Interpolation"},"xaxis":{"title":{"text":"x-axis"}},"yaxis":{"title":{"text":"y-axis"}},"showlegend":true},                        {"responsive": true}                    )                };                            </script>        </div>

# Introduction:
In the realm of plant biology, root growth trajectories are adaptive mechanisms that optimize resource utilization. In this exploration, we focus on the mathematical aspects of root growth, specifically addressing the minimization of soil resistance as a key factor in efficient penetration. Our subject is a corn root, initiating its growth in loamy soil at point P, and the goal is to delineate the trajectory that minimizes energy expenditure.

This investigation introduces a mathematical model that accounts for soil resistance factors in loamy, clayey, sandy, and muddy soils. By defining variables and equations tied to the coordinates of the root's trajectory, we seek to unravel the optimal path - one that enables the root to navigate through various soil types swiftly and with minimal energy consumption.
#Specific Problem
In the soil matrix, a maize root encounters a spatial challenge. Originating at a locus, P, within loamy soil, the root traverses a span of 8 meters. However, this path is complicated by the succession of four distinct soil types, each characterized by unique resistance factors: loamy (0.0031), clayey (0.04), sandy (0.0023), and muddy (0.009).

The core objective is to optimize the root's trajectory in the x-direction, dictated by the x-coordinates of three pivotal points (Q1, Q2, Q3). This optimization involves the minimization of the cumulative resistance experienced across the diverse soil types. The mathematical formulation entails the construction of a resistance function, R(x), embodying the Euclidean distances between successive points and the corresponding resistance factors.

# Model
To formulate the equations for the minimization problem, we need to define the resistance function \\( R(x) \\), where \\( x = [x_1, x_2, x_3]^T \\) are the x-coordinates of the endpoints of the three first lines.

Let's denote the points in the x-y plane as follows:

- \\( P = (0, 0) \\) is the starting point.
- \\( Q_1 = (x_1, 1.6) \\) is the point where the root transitions from loamy soil to clayey soil.
- \\( Q_2 = (x_2, 2.7) \\) is the point where the root transitions from clayey soil to sandy soil.
- \\( Q_3 = (x_3, 4.0) \\) is the point where the root transitions from sandy soil to muddy soil.
- \\( Q_4 = (8.0, 5.0) \\) is the point where the root reaches the most mechanically stable spot.

The resistance \\( R(x) \\) can be calculated as the sum of the resistances in each soil type:

\\\[ R(x) = R_{\text{loamy}}(P, Q_1) + R_{\text{clayey}}(Q_1, Q_2) + R_{\text{sandy}}(Q_2, Q_3) + R_{\text{muddy}}(Q_3, Q_4) \\]

Now, let's express each resistance term:

1. **Resistance in loamy soil: \\(R_{\text{loamy}}\\):**
   \\[ R_{\text{loamy}}(P, Q_1) = 0.0031 \cdot \sqrt{(x_1 - 0)^2 + (1.6 - 0)^2} \\]

2. **Resistance in clayey soil: \\(R_{\text{clayey}}\\):**
   \\[ R_{\text{clayey}}(Q_1, Q_2) = 0.04 \cdot \sqrt{(x_2 - x_1)^2 + (2.7 - 1.6)^2} \\]

3. **Resistance in sandy soil: \\(R_{\text{sandy}}\\):**
   \\[ R_{\text{sandy}}(Q_2, Q_3) = 0.0023 \cdot \sqrt{(x_3 - x_2)^2 + (4.0 - 2.7)^2} \\]

4. **Resistance in muddy soil: \\(R_{\text{muddy}}\\):**
   \\[ R_{\text{muddy}}(Q_3, Q_4) = 0.009 \cdot \sqrt{(8.0 - x_3)^2 + (5.0 - 4.0)^2} \\]

Finally, the total resistance function \\( R(x) \\) is the sum of these individual resistances.

To find the minimum resistance path, you would need to solve the minimization problem:

\\[ \text{Minimize } R(x) \\]

Subject to the constraint:

\\[ 0 \leq x_1 \leq x_2 \leq x_3 \leq 8.0 \\]

This constraint ensures that the root grows in the positive x-direction and doesn't backtrack.

Solving this optimization problem will give you the x-coordinates of the endpoints of the three first lines that minimize the total resistance experienced by the root.

# Gradient:

In mathematical optimization, the gradient plays a crucial role in finding the minimum of a function. The gradient of a function is a vector that points in the direction of the steepest increase of the function at a given point. In our case, the function of interest is the total resistance function, \\(R(x)\\), representing the cumulative resistance experienced by the corn root across different soil types.

The gradient of a multivariate function is a vector of its partial derivatives with respect to each variable. For our optimization problem, the gradient of \\(R(x)\\) with respect to \\(x\\) can be expressed as follows:

\\[ \nabla R(x) = \begin{bmatrix}
\frac{\partial R}{\partial x_1} \\
\frac{\partial R}{\partial x_2} \\
\frac{\partial R}{\partial x_3}
\end{bmatrix} \\]

To compute the partial derivatives, we differentiate the total resistance function with respect to each variable:

1. **Partial derivative with respect to \\(x_1\\):**
   \\[ \frac{\partial R}{\partial x_1} = \frac{\partial R_{\text{loamy}}}{\partial x_1} + \frac{\partial R_{\text{clayey}}}{\partial x_1} \\]

2. **Partial derivative with respect to \\(x_2\\):**
   \\[ \frac{\partial R}{\partial x_2} = \frac{\partial R_{\text{clayey}}}{\partial x_2} + \frac{\partial R_{\text{sandy}}}{\partial x_2} \\]

3. **Partial derivative with respect to \\(x_3\\):**
   \\[ \frac{\partial R}{\partial x_3} = \frac{\partial R_{\text{sandy}}}{\partial x_3} + \frac{\partial R_{\text{muddy}}}{\partial x_3} \\]

Now, let's express the individual partial derivatives:
\\[ \frac{\partial R_{\text{loamy}}}{\partial x_1}, \frac{\partial R_{\text{clayey}}}{\partial x_1}, \frac{\partial R_{\text{clayey}}}{\partial x_2}, \frac{\partial R_{\text{sandy}}}{\partial x_2}, \frac{\partial R_{\text{sandy}}}{\partial x_3}, \text{ and } \frac{\partial R_{\text{muddy}}}{\partial x_3} \\]


The gradient vector provides information about the direction in which the resistance function increases most rapidly. Minimizing the total resistance involves moving in the opposite direction, and iterative optimization algorithms utilize the gradient information to converge towards the optimal solution.

# Jacobian of the Gradient:

The Jacobian matrix is an extension of the gradient vector for vector-valued functions. In our case, the gradient vector (\\(\nabla R(x)\\)) is a vector-valued function. The Jacobian matrix, denoted by (\\(J(\nabla R)\\)), is a matrix of partial derivatives of each component of the gradient vector with respect to each variable.

\\[ J(\nabla R) = \begin{bmatrix}
\frac{\partial^2 R}{\partial x_1^2} & \frac{\partial^2 R}{\partial x_1 \partial x_2} & \frac{\partial^2 R}{\partial x_1 \partial x_3} ,
\frac{\partial^2 R}{\partial x_2 \partial x_1} & \frac{\partial^2 R}{\partial x_2^2} & \frac{\partial^2 R}{\partial x_2 \partial x_3} ,
\frac{\partial^2 R}{\partial x_3 \partial x_1} & \frac{\partial^2 R}{\partial x_3 \partial x_2} & \frac{\partial^2 R}{\partial x_3^2}
\end{bmatrix} \\]




The entries of this matrix are second-order partial derivatives of the total resistance function with respect to the variables \\(x_1, x_2, x_3\\). The Jacobian matrix provides information about how the gradient changes concerning changes in each variable, offering insights into the curvature and behavior of the resistance function.

# Hessian:

The Hessian matrix is the next level of abstraction, representing the second-order partial derivatives of a scalar-valued function. For our optimization problem, the Hessian matrix (\\(H(R)\\)) is the matrix of second-order partial derivatives of the total resistance function with respect to \\(x_1, x_2, x_3\\).

\\[ H(R) = \begin{bmatrix}
\frac{\partial^2 R}{\partial x_1^2} & \frac{\partial^2 R}{\partial x_1 \partial x_2} & \frac{\partial^2 R}{\partial x_1 \partial x_3} ,
\frac{\partial^2 R}{\partial x_2 \partial x_1} & \frac{\partial^2 R}{\partial x_2^2} & \frac{\partial^2 R}{\partial x_2 \partial x_3} ,
\frac{\partial^2 R}{\partial x_3 \partial x_1} & \frac{\partial^2 R}{\partial x_3 \partial x_2} & \frac{\partial^2 R}{\partial x_3^2}
\end{bmatrix} \\]
# Gradient, Jacobian, and Hessian Insights using Python
The Hessian matrix gives information about the curvature of the total resistance function. In optimization, the Hessian is crucial for determining the nature of critical points, distinguishing between minima, maxima, and saddle points. For our problem, analyzing the Hessian matrix is essential for ensuring that the identified solution corresponds to the minimum resistance path for the corn root's trajectory.

#### Import Libraries and Define Symbolic Variables

```python
import numpy as np
import sympy as sp
import matplotlib.pyplot as plt
x1, x2, x3 = sp.symbols('x1 x2 x3')
syms=[x1,x2,x3]
```
#### Define Total Resistance Function
```python
R_loamy = 0.0031 * sqrt(x1**2 + 1.6**2)
R_clayey = 0.04 * sqrt((x2 - x1)**2 + (2.7 - 1.6)**2)
R_sandy = 0.0023 * sqrt((x3 - x2)**2 + (4.0 - 2.7)**2)
R_muddy = 0.009 * sqrt((8 - x3)**2 + (5.0 - 4.0)**2)
T = R_loamy + R_clayey + R_sandy + R_muddy
T
```
- Defining the total resistance function `T` based on the given resistance terms for loamy, clayey, sandy, and muddy soils.

#### Gradient
```python
gradient = [sp.simplify(sp.diff(T, var)) for var in (x1, x2, x3)]
gradient = sp.Matrix(len(gradient), 1, gradient)
gradient
```
- Computing the gradient vector for the total resistance function.

```python
from IPython.display import display, Math
for i, grad in enumerate(gradient, start=1):
    latex_expr = sp.latex(grad)
    display(Math(latex_expr))
```
- Displaying the LaTeX representation of each component of the gradient vector.

#### Jacobian Matrix
```python
jacobian = gradient.jacobian(syms)
jacobian
```
- Computing the Jacobian matrix from the gradient vector.

```python
for i, jac in enumerate(jacobian, start=1):
    latex_expr = sp.latex(jac)
    display(Math(latex_expr))
```
- Displaying the LaTeX representation of each component of the Jacobian matrix.

#### Hessian Matrix
```python
hessian_matrix = sp.hessian(T, (x1, x2, x3))
hessian_matrix
```
- Computing the Hessian matrix for the total resistance function.

```python
for i, hess in enumerate(hessian_matrix, start=1):
    latex_expr = sp.latex(hess)
    display(Math(latex_expr))
```
- Displaying the LaTeX representation of each component of the Hessian matrix.

####  Functions for Gradient and Total Resistance
```python
gradient_func = sp.lambdify(syms, gradient)
total_resistance = sp.lambdify(syms, T)
```
- Creating lambda functions for the gradient and total resistance to be used in numerical computations.

#### Gradient Descent Function
```python
def gradient_descent(initial_x, learning_rate, tolerance):
    x= initial_x
    prev_x = np.zeros_like(x)  # Initialize prev_x with zeros for the first iteration
    iteration = 0

    while np.linalg.norm(x - prev_x) > tolerance:
        prev_x = x.copy()
        x -= learning_rate * gradient_func(*x.flatten())
        iteration += 1

    print(f"Converged in {iteration} iterations.")
    return x
```
- Gradient descent optimization algorithm using the given initial guess, learning rate, and tolerance.

```python
# Initial guess for x1, x2, x3
initial_guess = np.array([[0.0, 3.0, 5.0]]).T
learning_rate = 0.001
tolerance=.000001
# Run the gradient descent algorithm
optimal_x = gradient_descent(initial_guess, learning_rate, tolerance)
# Output the result
for x,sym in zip(optimal_x.flatten(),syms):
  print(sym.name,':',x)
print("Minimum total resistance:", total_resistance(*optimal_x.flatten()))
```

- Running the gradient descent algorithm with an initial guess, learning rate, and tolerance.

#### Scipy Minimization for Comparison
```python
import numpy as np
from scipy.optimize import minimize
# Define the objective function for minimization
def objective(x):
  return total_resistance(*x)

# Initial guess for x1, x2, x3
initial_guess = np.array([0.0, 3.0, 5.0])

# Use scipy.optimize.minimize to find the minimum
result = minimize(objective, initial_guess, method='BFGS')

# Output the result
optimal_x = result.x
for x,sym in zip(optimal_x.flatten(),syms):
  print(sym.name,':',x)
# Output the result

print("Minimum total resistance:", total_resistance(*optimal_x.flatten()))
```

- Using Scipy's `minimize` function for comparison with the gradient descent result.

#### Newton's Method Function
jacobian_func=sp.lambdify(syms,jacobian)
def newtons_method(initial_x, num_iterations):
    x = initial_x
    prev_x = np.zeros_like(x)  
    iteration = 0
    convergence_data = []
    while np.linalg.norm(x - prev_x) > tolerance:
        prev_x = x.copy()
    
        gradient = gradient_func(*x.flatten())
        jacobian_inv = np.linalg.pinv(jacobian_func(*x.flatten()))
        x = x - .0001*jacobian_inv @ gradient
        iteration+=1
        convergence_data.append(np.linalg.norm(x - prev_x))
    print(f"Converged in {iteration} iterations.")
    print(jacobian_inv @ gradient)
    print(np.linalg.norm(gradient))
    plt.plot(convergence_data)
    return x
```

- Defining Newton's method for optimization using the given initial guess and number of iterations.

```python
# Initial guess for x1, x2, x3
initial_guess = np.array([[0.0, 3.0, 5.0]]).T

# Number of iterations
tolerance = .000001

# Run Newton's method
optimal_x = newtons_method(initial_guess, tolerance)

for x,sym in zip(optimal_x.flatten(),syms):
  print(sym.name,':',x)
# Output the result

print("Minimum total resistance:", total_resistance(*optimal_x.flatten()))
```

- Running Newton's method with an initial guess and specified number of iterations.

#### Visualization
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.interpolate import CubicSpline

# Extract x, y, and z coordinates from the 3D plot
x_coordinates = np.array([0, optimal_x[0, 0], optimal_x[1, 0], optimal_x[2, 0], 8])
y_coordinates = -np.array([0, 1.6, 2.7, 4.0, 5.0])

# Create a spline interpolation
t = np.linspace(0, len(x_coordinates)-1, len(x_coordinates))
cs_x = CubicSpline(t, x_coordinates)
cs_y = CubicSpline(t, y_coordinates)

# Generate more points for a smoother curve
t_smooth = np.linspace(0, len(x_coordinates)-1, 100)
x_smooth = cs_x(t_smooth)
y_smooth = cs_y(t_smooth)

# Plot the 2D trajectory with spline interpolation
plt.figure(figsize=(8, 6))
plt.plot(x_coordinates, y_coordinates, 'ro-', label='Original Points')
plt.plot(x_smooth, y_smooth, 'b-', label='Spline Interpolation')
plt.xlabel('x-axis')
plt.ylabel('y-axis')
plt.title('Root Trajectory Projection in 2D with Spline Interpolation')
plt.legend()
plt.grid(True)
plt.show()
```

- Plotting the trajectory of the root through soil layers in a 3D graph using Matplotlib.
