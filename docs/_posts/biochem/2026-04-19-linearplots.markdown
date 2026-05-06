---
layout: post
title:  "Visualizing Michaelis–Menten Kinetics with Python"
date:   2026-04-19 06:25:17 -0800
categories: jekyll update biology
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Blog_of_Linear_Plots_Enzyme_Kinetics.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>
# Introduction

Enzyme kinetics is one of the foundational topics in biochemistry and computational biology. While the Michaelis--Menten equation describes the relationship between substrate concentration and reaction velocity, extracting meaningful kinetic parameters such as $$K_m$$ and $$V_{max}$$ often requires transforming nonlinear data into linear forms.

In this project, we use Python, NumPy, and Matplotlib to analyze enzyme kinetics using five classical linearization methods:

1. Lineweaver--Burk
    
2. Hanes--Woolf
    
3. Eadie--Hofstee
    
4. Direct Linear Transform
    
5. Eadie--Scatchard
    

The script computes linear regressions, estimates kinetic constants, and visualizes each transformation with annotated plots.

---

# The Michaelis--Menten Equation

The core equation of enzyme kinetics is:

$$
v = \frac{V_{max}[S]}{K_m + [S]}
$$

where:

- $$v$$ = reaction velocity
    
- $$[S]$$ = substrate concentration
    
- $$V_{max}$$ = maximum reaction velocity
    
- $$K_m$$ = Michaelis constant
    

Because this equation is nonlinear, several algebraic rearrangements have historically been used to estimate kinetic parameters through linear regression.

---

# Dataset

The experimental dataset {% cite segel1976biochemical %} consists of substrate concentrations and measured reaction velocities.

{% raw %}
```python
S = np.array([8.33e-6, 1.00e-5, 1.25e-5, 1.67e-5, 2.00e-5,
              2.50e-5, 3.33e-5, 4.00e-5, 5.00e-5,
              6.00e-5, 8.00e-5, 1.00e-4, 2.00e-4])

v = np.array([13.8, 16.0, 19.0, 23.6, 26.7,
              30.8, 36.3, 40.0, 44.4,
              48.0, 53.4, 57.1, 66.7])
```
{% endraw %}

These values represent a classic saturation curve where reaction velocity increases with substrate concentration and gradually approaches $$V_{max}$$.

<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="0405f1f9-446d-4c79-b1a9-e12d85429156" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("0405f1f9-446d-4c79-b1a9-e12d85429156")) {                    Plotly.newPlot(                        "0405f1f9-446d-4c79-b1a9-e12d85429156",                        [{"marker":{"size":9},"mode":"markers","name":"Experimental data","x":[0.833,1.0,1.25,1.67,2.0,2.5,3.0,3.33,4.0,5.0,6.0,8.0,10.0,20.0],"y":[13.8,16.0,19.0,23.6,26.7,30.8,34.3,36.3,40.0,44.4,48.0,53.3,57.1,66.7],"type":"scatter"},{"mode":"lines","name":"Hyperbolic fit: Vmax=79.98, Km=4.00","x":[0.833,0.8971036789297658,0.9612073578595317,1.0253110367892977,1.0894147157190635,1.1535183946488294,1.2176220735785952,1.2817257525083612,1.3458294314381272,1.409933110367893,1.4740367892976587,1.5381404682274247,1.6022441471571907,1.6663478260869566,1.7304515050167224,1.7945551839464882,1.8586588628762541,1.9227625418060201,1.986866220735786,2.050969899665552,2.1150735785953176,2.1791772575250836,2.243280936454849,2.307384615384615,2.371488294314381,2.435591973244147,2.499695652173913,2.563799331103679,2.627903010033445,2.6920066889632106,2.7561103678929766,2.820214046822742,2.884317725752508,2.948421404682274,3.01252508361204,3.076628762541806,3.140732441471572,3.204836120401338,3.268939799331104,3.333043478260869,3.397147157190635,3.461250836120401,3.525354515050167,3.589458193979933,3.653561872909699,3.717665551839465,3.781769230769231,3.845872909698997,3.909976588628763,3.974080267558528,4.038183946488294,4.10228762541806,4.166391304347826,4.230494983277592,4.294598662207358,4.358702341137124,4.42280602006689,4.486909698996656,4.551013377926421,4.615117056856187,4.679220735785953,4.743324414715719,4.807428093645485,4.871531772575251,4.935635451505017,4.999739130434783,5.063842809364549,5.127946488294315,5.192050167224081,5.256153846153846,5.320257525083612,5.384361204013378,5.448464882943144,5.51256856187291,5.576672240802676,5.640775919732442,5.704879598662208,5.768983277591974,5.833086956521739,5.897190635451505,5.961294314381271,6.025397993311037,6.089501672240803,6.153605351170569,6.217709030100335,6.281812709030101,6.345916387959867,6.410020066889632,6.474123745819398,6.538227424749164,6.60233110367893,6.666434782608696,6.730538461538462,6.794642140468228,6.858745819397994,6.92284949832776,6.986953177257526,7.051056856187291,7.115160535117057,7.179264214046823,7.243367892976589,7.307471571906355,7.371575250836121,7.435678929765887,7.499782608695653,7.563886287625419,7.627989966555184,7.69209364548495,7.756197324414716,7.820301003344482,7.884404682274248,7.948508361204014,8.01261204013378,8.076715719063545,8.140819397993312,8.204923076923077,8.269026755852842,8.333130434782609,8.397234113712374,8.46133779264214,8.525441471571906,8.589545150501673,8.653648829431438,8.717752508361205,8.78185618729097,8.845959866220737,8.910063545150502,8.974167224080269,9.038270903010034,9.102374581939799,9.166478260869566,9.23058193979933,9.294685618729098,9.358789297658863,9.42289297658863,9.486996655518395,9.551100334448162,9.615204013377927,9.679307692307692,9.743411371237459,9.807515050167224,9.87161872909699,9.935722408026756,9.999826086956523,10.063929765886288,10.128033444816054,10.19213712374582,10.256240802675585,10.320344481605352,10.384448160535117,10.448551839464884,10.512655518394649,10.576759197324415,10.64086287625418,10.704966555183947,10.769070234113713,10.833173913043478,10.897277591973245,10.96138127090301,11.025484949832776,11.089588628762542,11.153692307692308,11.217795986622074,11.28189966555184,11.346003344481606,11.41010702341137,11.474210702341137,11.538314381270903,11.60241806020067,11.666521739130435,11.730625418060201,11.794729096989967,11.858832775919733,11.922936454849498,11.987040133779264,12.05114381270903,12.115247491638796,12.179351170568562,12.243454849498328,12.307558528428094,12.37166220735786,12.435765886287626,12.499869565217391,12.563973244147157,12.628076923076923,12.692180602006689,12.756284280936455,12.82038795986622,12.884491638795987,12.948595317725752,13.01269899665552,13.076802675585284,13.140906354515051,13.205010033444816,13.269113712374581,13.333217391304348,13.397321070234113,13.46142474916388,13.525528428093645,13.589632107023412,13.653735785953177,13.717839464882944,13.78194314381271,13.846046822742474,13.910150501672241,13.974254180602006,14.038357859531773,14.102461538461538,14.166565217391305,14.23066889632107,14.294772575250837,14.358876254180602,14.422979933110367,14.487083612040134,14.5511872909699,14.615290969899666,14.679394648829431,14.743498327759198,14.807602006688963,14.87170568561873,14.935809364548495,14.99991304347826,15.064016722408027,15.128120401337792,15.19222408026756,15.256327759197324,15.320431438127091,15.384535117056856,15.448638795986623,15.512742474916388,15.576846153846153,15.64094983277592,15.705053511705685,15.769157190635452,15.833260869565217,15.897364548494984,15.96146822742475,16.025571906354514,16.08967558528428,16.153779264214045,16.217882943143813,16.28198662207358,16.346090301003343,16.41019397993311,16.474297658862877,16.538401337792642,16.602505016722407,16.666608695652172,16.730712374581937,16.794816053511706,16.85891973244147,16.923023411371236,16.987127090301,17.051230769230767,17.115334448160535,17.1794381270903,17.243541806020065,17.30764548494983,17.371749163879596,17.435852842809364,17.49995652173913,17.564060200668894,17.62816387959866,17.692267558528428,17.756371237458193,17.82047491638796,17.884578595317723,17.94868227424749,18.012785953177257,18.076889632107022,18.140993311036787,18.205096989966552,18.26920066889632,18.333304347826086,18.39740802675585,18.461511705685616,18.52561538461538,18.58971906354515,18.653822742474915,18.71792642140468,18.782030100334445,18.846133779264214,18.91023745819398,18.974341137123744,19.03844481605351,19.102548494983274,19.166652173913043,19.230755852842808,19.294859531772573,19.35896321070234,19.423066889632107,19.487170568561872,19.551274247491637,19.615377926421402,19.679481605351167,19.743585284280936,19.8076889632107,19.871792642140466,19.93589632107023,20.0],"y":[13.787335147542825,14.653955511126984,15.498178410056138,16.32086104786797,17.12281743619707,17.90482108132053,18.6676074726429,19.41187638994914,20.138294044639377,20.84749506871719,21.540084364012756,22.216638822966196,22.877708931259953,23.52382026165736,24.155474867567502,24.773152584102007,25.37731224370986,25.968392812862525,26.546814455707374,27.112979530105687,27.66727352101723,28.210065915781772,28.741711025473684,29.26254875616676,29.77290533363695,30.273093984749966,30.763415578524413,31.244159229627247,31.715602866845344,32.17801376888173,32.631649069646976,33.07675623505267,33.513573513165085,33.942330359439005,34.36324783862689,34.776539004842164,35.18240926114976,35.58105669995889,35.972672425403395,36.35744085881186,36.73554002829346,37.10714184339472,37.47241235571782,37.831512006330016,38.18459586073912,38.53181383215774,38.87331089373174,39.20922728036418,39.53969868072484,39.86485641999789,40.18482763388457,40.49973543434523,40.80969906753501,41.11483406435813,41.415252384040876,41.71106255109753,42.00236978604155,42.28927613017258,42.571880564750266,42.85027912484729,43.12456500815662,43.394828679011994,43.66115796786565,43.923638166452825,44.18235211886002,44.43738030870083,44.68880094259244,44.93669003011437,45.18112146042151,45.422167075673265,45.659896741432455,45.89437841417864,46.125678206073076,46.35386044710487,46.57898774474105,46.80112104119671,47.02031966843539,47.236641401003894,47.45014250680025,47.66087779586874,47.86890066731077,48.074263154395815,48.27701596795281,48.477208538117566,48.67488905450871,48.8701045049007,49.062900712458976,49.253322371599346,49.441413082530474,49.62721538453564,49.81077078804697,49.992119805563235,50.17130198145917,50.34835592073274,50.52331931673411,50.69622897791809,50.867120853660104,51.03603005917357,51.202990899564966,51.36803689306134,51.53120079344314,51.692514611713996,51.85200963703743,52.009716456969535,52.165664977014764,52.319884439531336,52.47240344201122,52.62324995475883,52.77245133799124,52.92003435838199,53.066025205069415,53.21044950514969,53.35333233867378,53.49469825316672,53.634571277686916,53.77297493644238,53.909932261980096,54.04546580796401,54.17959766155658,54.31234945541822,54.44374237933814,54.57379719150992,54.70253422946429,54.82997342067137,54.95613429282366,55.08103598381133,55.204697251400205,55.32713648262284,55.448371702892594,55.56842058485014,55.68730045695147,55.80502831180633,55.92162081427538,56.037094309334115,56.151464829711635,56.264748103311376,56.37695956042137,56.48811434072062,56.5982273000887,56.70731301722459,56.815385800081216,56.92245969212153,57.02854847840199,57.13366569148877,57.23782461721235,57.34103830026525,57.443319549648166,57.54468094396914,57.645134836600434,57.7446933606974,57.84336843408387,57.94117176400801,58.03811485177269,58.13420899724417,58.22946530324291,58.323894679820015,58.41750784842276,58.5103153459526,58.60232752871879,58.69355457629095,58.784006495253195,58.873693122863195,58.962624130618636,59.05080902773391,59.13825716452973,59.22497773573812,59.31097978372518,59.396272201634176,59.48086373645112,59.56476299199502,59.6479784318351,59.73051838213695,59.812391034439614,59.89360444836565,59.97416655426592,60.05408515580109,60.13336793246146,60.21202244202682,60.290056122968274,60.367476296793164,60.44429017033504,60.52050483799007,60.596127283901176,60.67116438409161,60.74562290854904,60.819509523261715,60.89283079220789,60.965593179299596,61.0378030502824,61.10946667459182,61.180590227167855,61.25117979022872,61.32124135500459,61.39078082343277,61.45980400981511,61.528316642438384,61.5963243651592,61.663832738953744,61.73084724343361,61.797373278328465,61.86341616493647,61.92898114754303,61.99407339480914,62.05869800112952,62.122859987961846,62.186564305127234,62.24981583208334,62.31261937917015,62.37497968882942,62.43690143679859,62.49838923327937,62.55944762408187,62.62008109174507,62.680294056633606,62.740090878012175,62.7994758550975,62.858453228088706,62.91702717917669,62.97520183353254,63.03298126027611,63.09036947342479,63.14737043282302,63.203988045053165,63.26022616432802,63.31608859336537,63.371579084245234,63.42670133924984,63.48145901168711,63.5358557066978,63.589894982046644,63.64358034889815,63.696915272576916,63.749903173313434,63.80254742697515,63.85485136578339,63.906818279016534,63.95845141369947,64.00975397527999,64.06072912829204,64.11137999700654,64.16170966606957,64.21172118112868,64.26141754944722,64.31080174050713,64.35987668660042,64.40864528340954,64.45711039057703,64.5052748322643,64.55314139770043,64.60071284172045,64.6479918852939,64.69498121604364,64.74168348875517,64.78810132587648,64.83423731800913,64.88009402438999,64.92567397336465,64.97097966285202,65.01601356080069,65.06077810563703,65.10527570670538,65.14950874470027,65.19347957209102,65.23719051353882,65.28064386630635,65.32384190066031,65.36678686026681,65.40948096257976,65.4519263992226,65.49412533636333,65.53607991508295,65.57779225173768,65.61926443831476,65.6604985427822,65.70149660943252,65.74226065922069,65.78279269009602,65.82309467732874,65.86316857383082,65.90301631047147,65.94263979638721,65.9820409192868,66.021221545751,66.0601835215274,66.09892867182018,66.13745880157518,66.17577569576021,66.21388111964062,66.25177681905045,66.2894645206591,66.32694593223346,66.36422274289599,66.40129662337843,66.43816922627133,66.47484218626975,66.51131712041474,66.54759562833107,66.58367929246099,66.61956967829444,66.6552683345954],"type":"scatter"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"white","showlakes":true,"showland":true,"subunitcolor":"#C8D4E3"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"white","polar":{"angularaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""},"bgcolor":"white","radialaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"yaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"zaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"baxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"bgcolor":"white","caxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2}}},"title":{"text":"Hyperbolic Curve: v vs [S]"},"xaxis":{"title":{"text":"[S] × 10⁵ M"}},"yaxis":{"title":{"text":"v × 10⁸ M min⁻¹"}}},                        {"responsive": true}                    )                };                            </script>        </div>


---

# Building a Reusable Linear Regression Function

To avoid repetitive code, the script defines a helper function for linear fitting:

{% raw %}
```python
def fit_line(x, y):
    m, b = np.polyfit(x, y, 1)
    yhat = m*x + b
    r2 = 1 - np.sum((y-yhat)**2)/np.sum((y-y.mean())**2)
    return m, b, r2
```
{% endraw %}

This function computes:

- slope ($$m$$)
    
- intercept ($$b$$)
    
- coefficient of determination ($$R^2$$)
    

The $$R^2$$ value helps evaluate how well the transformed data follows a linear relationship.

---

# 1. Lineweaver--Burk Plot

The Lineweaver--Burk transformation takes the reciprocal of both sides of the Michaelis--Menten equation.

$$
\frac{1}{v} = \frac{K_m}{V_{max}}\frac{1}{[S]} + \frac{1}{V_{max}}
$$

This produces a straight line where:

- slope = $$\frac{K_m}{V_{max}}$$
    
- intercept = $$\frac{1}{V_{max}}$$
    

## Advantages

- Historically important
    
- Easy visual interpretation
    

## Drawbacks

- Strongly amplifies experimental error at low substrate concentrations
    
- Reciprocal transformations distort variance
    

The script calculates:

{% raw %}
```python
Vmax = 100 / b
Km = (m * Vmax) / 1e6
```
{% endraw %}

and overlays the regression line directly on the scatter plot.

---

# 2. Hanes--Woolf Plot

The Hanes--Woolf transformation rearranges the equation into:

$$
\frac{[S]}{v} = \frac{1}{V_{max}}[S] + \frac{K_m}{V_{max}}
$$

Compared with Lineweaver--Burk, this method reduces the weighting problem caused by reciprocal velocity terms.

## Advantages

- Less sensitive to low-concentration noise
    
- More stable regression behavior
    

## Interpretation

- slope = $$\frac{1}{V_{max}}$$
    
- intercept = $$\frac{K_m}{V_{max}}$$
    

This transformation is often considered more reliable for experimental datasets.

---

# 3. Eadie--Hofstee Plot

The Eadie--Hofstee equation rearranges Michaelis--Menten into:

$$
v = -K_m\left(\frac{v}{[S]}\right) + V_{max}
$$

Unlike reciprocal methods, this transformation uses velocity on both axes.

## Interpretation

- slope = $$-K_m$$
    
- intercept = $$V_{max}$$
    

## Advantages

- Reduced distortion from reciprocal scaling
    
- Frequently produces visually balanced plots
    

## Drawbacks

- Correlated errors because $$v$$ appears in both variables
    

---

# 4. Direct Linear Transform

The direct linear transform uses:

$$
[S] = V_{max}\left(\frac{[S]}{v}\right) - K_m
$$

This formulation avoids reciprocal velocity terms entirely.

## Interpretation

- slope = $$V_{max}$$
    
- intercept = $$-K_m$$
    

This method is less commonly discussed in introductory biochemistry courses but can provide intuitive geometric insight.

---

# 5. Eadie--Scatchard Plot

The Eadie--Scatchard transformation is:

$$
\frac{v}{[S]} = -\frac{1}{K_m}v + \frac{V_{max}}{K_m}
$$

## Interpretation

- slope = $$-\frac{1}{K_m}$$
    
- intercept = $$\frac{V_{max}}{K_m}$$
    

This method is mathematically related to the Eadie--Hofstee plot but flips the variable arrangement.

---

# Visualization Strategy

The script uses Matplotlib to generate publication-style figures with:

- scatter plots for experimental data
    
- regression lines
    
- equation annotations
    
- estimated $$K_m$$
    
- estimated $$V_{max}$$
    
- slope/intercept values
    
- $$R^2$$ statistics
    

Example plotting structure:

{% raw %}
```python
plt.scatter(x, y)
plt.plot(x, m*x + b)

plt.title(
    rf"Lineweaver-Burk\n"
    rf"$K_m$ = {Km:.3e} M, "
    rf"$V_{{max}}$ = {Vmax:.2f}"
)
```
{% endraw %}

The use of raw formatted strings (`rf""`) allows LaTeX rendering and variable interpolation simultaneously.

---

# Why Multiple Linearizations Matter

Different transformations emphasize different regions of the experimental data.

|Method|Strength|Weakness|
|---|---|---|
|Lineweaver--Burk|Simple interpretation|Distorts low-$$[S]$$ errors|
|Hanes--Woolf|More stable regression|Still linearized|
|Eadie--Hofstee|Balanced visualization|Correlated variables|
|Direct Linear|Geometric intuition|Less commonly used|
|Eadie--Scatchard|Useful alternative form|Error propagation issues|

Modern enzyme kinetics often favors nonlinear regression directly on the Michaelis--Menten equation, but these classical plots remain valuable educational and analytical tools.

---

# Scientific Computing Takeaways

This project demonstrates several important computational techniques:

- numerical linear regression with NumPy
    
- statistical goodness-of-fit analysis
    
- scientific plotting with Matplotlib
    
- biochemical parameter estimation
    
- equation visualization using LaTeX formatting
    

It also highlights how mathematical transformations can drastically change the interpretation and stability of experimental data.

---

# Final Thoughts

Linear transformations of the Michaelis--Menten equation are a classic example of how mathematics and computation intersect with biochemistry. Although nonlinear fitting methods are now standard in research environments, understanding these linear plots provides deep intuition about enzyme behavior, parameter estimation, and error propagation.

With only NumPy and Matplotlib, Python becomes a powerful environment for biochemical data analysis and scientific visualization.

# Appendix: Code Walkthrough

This appendix explains what each section of the Python script does and how the values of $$K_m$$, $$V_{max}$$, and $$R^2$$ are obtained.

---

## 1. Importing Libraries

{% raw %}
```python
import numpy as np
import matplotlib.pyplot as plt
```
{% endraw %}

The script uses NumPy for numerical calculations and Matplotlib for plotting.

NumPy handles arrays, transformations, and linear regression through `np.polyfit`.

Matplotlib creates the scatter plots, regression lines, labels, titles, and annotations.

---

## 2. Setting Plot Styles

{% raw %}
```python
plt.rcParams.update({
    "font.size": 12,
    "axes.titlesize": 13,
    "axes.labelsize": 12
})
```
{% endraw %}

This updates the default appearance of all plots.

The font size is increased so that axis labels, titles, and annotations are easier to read.

---

## 3. Entering the Experimental Data

{% raw %}
```python
S = np.array([8.33e-6, 1.00e-5, 1.25e-5, 1.67e-5, 2.00e-5, 2.50e-5,
              3.33e-5, 4.00e-5, 5.00e-5, 6.00e-5, 8.00e-5, 1.00e-4, 2.00e-4])

v = np.array([13.8, 16.0, 19.0, 23.6, 26.7, 30.8,
              36.3, 40.0, 44.4, 48.0, 53.4, 57.1, 66.7])
```
{% endraw %}

`S` stores the substrate concentrations $$[S]$$ in molar units.

`v` stores the initial reaction velocities.

Each value in `S` corresponds to the velocity value at the same array position in `v`.

For example:

{% raw %}
```python
S[0] = 8.33e-6
v[0] = 13.8
```
{% endraw %}

This means that when $$[S] = 8.33 \times 10^{-6}$$ M, the measured velocity is $$13.8$$.

---

## 4. Defining the Linear Fit Function

{% raw %}
```python
def fit_line(x, y):
    m, b = np.polyfit(x, y, 1)
    yhat = m*x + b
    r2 = 1 - np.sum((y-yhat)**2)/np.sum((y-y.mean())**2)
    return m, b, r2
```
{% endraw %}

This function performs a linear regression of the form:

$$  
y = mx + b  
$$

where $$m$$ is the slope and $$b$$ is the y-intercept.

The line:

{% raw %}
```python
m, b = np.polyfit(x, y, 1)
```
{% endraw %}

fits a first-degree polynomial to the data.

A first-degree polynomial is a straight line:

$$  
y = mx + b  
$$

The next line calculates the predicted values:

{% raw %}
```python
yhat = m*x + b
```
{% endraw %}

These are the points on the best-fit line.

The script then calculates $$R^2$$:

{% raw %}
```python
r2 = 1 - np.sum((y-yhat)**2)/np.sum((y-y.mean())**2)
```
{% endraw %}

Mathematically, this is:

$$  
R^2 = 1 - \frac{\sum (y_i - \hat{y}_i)^2}{\sum (y_i - \bar{y})^2}  
$$

where $$\hat{y}_i$$ is the predicted value and $$\bar{y}$$ is the mean of the observed values.

A value of $$R^2$$ close to $$1$$ means the transformed data fits a straight line well.

---

## 5. Scaling the Data

{% raw %}
```python
S_s = S * 1e5
v_s = v

invS_s = (1/S) * 1e-4
invv_s = (1/v) * 100

v_by_S_s = (v/S) * 1e-6
S_by_v_s = (S/v) * 1e6
```
{% endraw %}

These lines create scaled variables for plotting.

The scaling does not change the relationship between variables. It only makes the axis numbers easier to read.

For example:

{% raw %}
```python
S_s = S * 1e5
```
{% endraw %}

converts very small molar concentrations into more convenient numbers.

If:

$$  
[S] = 8.33 \times 10^{-6}  
$$

then:

$$  
S_s = [S] \times 10^5 = 0.833  
$$

The reciprocal substrate concentration is scaled as:

{% raw %}
```python
invS_s = (1/S) * 1e-4
```
{% endraw %}

The reciprocal velocity is scaled as:

{% raw %}
```python
invv_s = (1/v) * 100
```
{% endraw %}

The velocity-over-substrate term is scaled as:

{% raw %}
```python
v_by_S_s = (v/S) * 1e-6
```
{% endraw %}

The substrate-over-velocity term is scaled as:

{% raw %}
```python
S_by_v_s = (S/v) * 1e6
```
{% endraw %}

These scaled variables are used in the five transformed plots.

---

## 6. Lineweaver--Burk Section

{% raw %}
```python
x = invS_s
y = invv_s
m, b, r2 = fit_line(x, y)
```
{% endraw %}

For the Lineweaver--Burk plot, the script sets:

$$  
x = \frac{1}{[S]}  
$$

and:

$$  
y = \frac{1}{v}  
$$

The Lineweaver--Burk equation is:

$$  
\frac{1}{v}

\frac{K_m}{V_{max}}\frac{1}{[S]}  
+  
\frac{1}{V_{max}}  
$$

After fitting the line, the script extracts $$V_{max}$$ and $$K_m$$:

{% raw %}
```python
Vmax = 100 / b
Km = (m * Vmax) / 1e6
```
{% endraw %}

Because the plotted $$y$$-axis is scaled as:

$$  
y = \frac{1}{v} \times 100  
$$

the intercept is:

$$  
b = \frac{100}{V_{max}}  
$$

Solving for $$V_{max}$$ gives:

$$  
V_{max} = \frac{100}{b}  
$$

Because the plotted $$x$$-axis is scaled as:

$$  
x = \frac{1}{[S]} \times 10^{-4}  
$$

the slope must be corrected for the scaling. The script calculates:

$$  
K_m = \frac{mV_{max}}{10^6}  
$$

The plot is then created using:

{% raw %}
```python
plt.scatter(x, y)
plt.plot(x, m*x + b)
```
{% endraw %}

The scatter points show the transformed data, and the line shows the linear fit.

---

## 7. Hanes--Woolf Section

{% raw %}
```python
x = S_s
y = S_by_v_s
m, b, r2 = fit_line(x, y)
```
{% endraw %}

For the Hanes--Woolf plot, the script uses:

$$  
x = [S]  
$$

and:

$$  
y = \frac{[S]}{v}  
$$

The Hanes--Woolf equation is:

$$  
\frac{[S]}{v}

\frac{1}{V_{max}}[S]  
+  
\frac{K_m}{V_{max}}  
$$

The script calculates:

{% raw %}
```python
Vmax = 10 / m
Km = (b * Vmax) / 1e6
```
{% endraw %}

The slope is related to $$V_{max}$$, but the factor of $$10$$ appears because both axes were scaled for readability.

The intercept is related to:

$$  
\frac{K_m}{V_{max}}  
$$

so multiplying the intercept by $$V_{max}$$ gives $$K_m$$, followed by the scaling correction.

---

## 8. Eadie--Hofstee Section

{% raw %}
```python
x = v_by_S_s
y = v_s
m, b, r2 = fit_line(x, y)
```
{% endraw %}

For the Eadie--Hofstee plot, the script uses:

$$  
x = \frac{v}{[S]}  
$$

and:

$$  
y = v  
$$

The Eadie--Hofstee equation is:

$$  
v

-K_m\left(\frac{v}{[S]}\right)  
+  
V_{max}  
$$

The script extracts the parameters using:

{% raw %}
```python
Vmax = b
Km = -m / 1e6
```
{% endraw %}

The intercept gives $$V_{max}$$ directly:

$$  
V_{max} = b  
$$

The slope is related to $$-K_m$$, but the $$x$$-axis is scaled by $$10^{-6}$$, so the script corrects the slope using:

$$  
K_m = \frac{-m}{10^6}  
$$

---

## 9. Direct Linear Transform Section

{% raw %}
```python
x = S_by_v_s
y = S_s
m, b, r2 = fit_line(x, y)
```
{% endraw %}

For the direct linear transform, the script uses:

$$  
x = \frac{[S]}{v}  
$$

and:

$$  
y = [S]  
$$

The transformed equation is:

$$  
[S]

V_{max}\left(\frac{[S]}{v}\right)

K_m  
$$

The script calculates:

{% raw %}
```python
Vmax = 10 * m
Km = -b / 1e5
```
{% endraw %}

The slope gives $$V_{max}$$ after correcting for the axis scaling.

The intercept represents $$-K_m$$, so:

$$  
K_m = -b  
$$

Because the plotted substrate concentration is scaled by $$10^5$$, the script converts it back using:

$$  
K_m = \frac{-b}{10^5}  
$$

---

## 10. Eadie--Scatchard Section

{% raw %}
```python
v_M = v * 1e-9
```
{% endraw %}

This converts velocity from nanomolar-style units into molar units.

Then the script rescales the velocity and velocity-over-substrate variables:

{% raw %}
```python
v_s = v_M * 1e9
v_by_S_s = (v_M / S) * 1e3
```
{% endraw %}

For the Eadie--Scatchard plot, the script uses:

$$  
x = v  
$$

and:

$$  
y = \frac{v}{[S]}  
$$

The Eadie--Scatchard equation is:

$$  
\frac{v}{[S]}

-\frac{1}{K_m}v  
+  
\frac{V_{max}}{K_m}  
$$

The regression is performed with:

{% raw %}
```python
x = v_s
y = v_by_S_s
m, b, r2 = fit_line(x, y)
```
{% endraw %}

The kinetic parameters are calculated using:

{% raw %}
```python
Km = -1e-6 / m
Vmax = (b * Km) / 1e-6
```
{% endraw %}

The slope is proportional to:

$$  
-\frac{1}{K_m}  
$$

After correcting for the scaling used on both axes, the script solves for:

$$  
K_m = \frac{-10^{-6}}{m}  
$$

The intercept is proportional to:

$$  
\frac{V_{max}}{K_m}  
$$

so rearranging gives:

$$  
V_{max} = \frac{bK_m}{10^{-6}}  
$$

---

## 11. Plot Labels and Titles

Each plot uses commands like:

{% raw %}
```python
plt.xlabel(...)
plt.ylabel(...)
plt.title(...)
```
{% endraw %}

For example:

{% raw %}
```python
plt.xlabel(r"$v$ ($\mathrm{M\cdot min^{-1}} \times 10^{9}$)")
```
{% endraw %}

The `r` before the string creates a raw string. This is useful when writing LaTeX-style math labels because backslashes are interpreted correctly.

The plot title includes calculated kinetic parameters:

{% raw %}
```python
plt.title(
    rf"Lineweaver-Burk"
    "\n"
    rf"$K_m = {Km:.3e}\ \mathrm{{M}},\ "
    rf"V_{{max}} = {Vmax:.2f}\ \mathrm{{nmol \cdot L^{{-1}} \cdot min^{{-1}}}}$"
)
```
{% endraw %}

The `rf` prefix means the string is both raw and formatted.

That allows math notation like:

$$  
K_m  
$$

and Python variables like:

{% raw %}
```python
{Km:.3e}
```
{% endraw %}

to appear in the same title.

---

## 12. Text Annotations

Each plot includes a text box:

{% raw %}
```python
plt.text(0.20*max(x), 0.75*max(y),
         "1/v = (Km/Vmax)(1/[S]) + 1/Vmax\n"
         f"slope = {m:.2e}\n"
         f"intercept = {b:.2e}\n"
         f"$R^2 = {r2:.4f}$",
         fontsize=9)
```
{% endraw %}

This places explanatory text inside the plot.

The coordinates:

{% raw %}
```python
0.20*max(x), 0.75*max(y)
```
{% endraw %}

position the text relative to the maximum axis values.

The annotation includes:

- the linearized equation
    
- slope
    
- intercept
    
- $$R^2$$
    

This makes each figure self-contained.

---

## 13. Displaying Each Plot

{% raw %}
```python
plt.show()
```
{% endraw %}

This displays the current figure.

Because the script calls `plt.figure()` before each plot, each method appears in its own separate window or output cell.

---

## 14. Overall Code Flow

The full script follows this pattern five times:

1. Choose the transformed $$x$$ and $$y$$ variables.
    
2. Fit a straight line with `fit_line(x, y)`.
    
3. Convert slope and intercept into $$K_m$$ and $$V_{max}$$.
    
4. Create a scatter plot.
    
5. Add the regression line.
    
6. Label the axes.
    
7. Add a title with the calculated kinetic constants.
    
8. Annotate the plot with the equation, slope, intercept, and $$R^2$$.
    
9. Display the figure.
    

The repeated structure makes the code easy to compare across the five linearization methods.



# References

{% bibliography %}