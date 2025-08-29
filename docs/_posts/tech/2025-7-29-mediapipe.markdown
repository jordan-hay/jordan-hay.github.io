---
layout: post
title:  "Automating Face Morphometrics Analysis with MediaPipe and Python"
date:   2025-7-29 09:25:17 -0800
categories: jekyll update technology
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Automating_Face_Morphometrics_Analysis_with_MediaPipe_and_Python.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

![image tooltip here](/assets/images/meshedface.png){: width="500" }


<div>                        <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="e7c5f10a-ee9e-4292-a76f-cea5fac67f65" class="plotly-graph-div" style="height:100%; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("e7c5f10a-ee9e-4292-a76f-cea5fac67f65")) {                    Plotly.newPlot(                        "e7c5f10a-ee9e-4292-a76f-cea5fac67f65",                        [{"marker":{"color":"skyblue","line":{"color":"black","width":1}},"nbinsx":15,"x":[348.1436485130815,363.02203789852757,362.00552481971874,357.0014005574768,366.0122948754591,345.00144927231827,362.0013812128346,360.01249978299364,354.05084380636634,354.00564967243105,359.01253460011674,367.0490430446591,356.0688135740057,359.0055709874152,360.23464575190434,357.0224082603219,366.001366117669,369.0663896916109,373.06567786383135,357.0224082603219,363.00137740785505,356.0688135740057,351.0056979594491,356.0126402250347,361.00554012369395,360.0,359.01253460011674,356.0505582076793,364.0219773585106,365.0123285589132,363.0881435684729,348.0014367786432,361.04985805287333,359.00139275495854,362.0220987729893,353.0354089889568,374.0120318920235,346.0,357.0224082603219,357.0014005574768,347.0,362.0013812128346,355.0,338.09466130064817,370.01216196227927,354.00564967243105,351.2406582387637,323.0061918911153,353.0509878190401,365.23143347745963,361.0013850388943,360.0013888862097,362.00552481971874,359.00139275495854,360.0013888862097,354.05084380636634,362.1118611699981,359.01253460011674,346.01300553591915,356.0688135740057,363.0,357.03501228871096,360.1999444752872,356.0126402250347,352.00142045167945,350.06999300139967,355.0126758300329,355.0126758300329,358.00558654859003,367.0,357.01260481949373,362.00552481971874,357.01260481949373,349.05157212079706,364.1977484828812,352.035509572543,365.0342449688796,339.05309318748294,351.00142449853394,359.0055709874152,335.00597009605667,362.067673232505,361.00554012369395,362.66789215479224,358.00558654859003,361.0013850388943,348.1738071710737,360.01249978299364,363.00137740785505,349.05157212079706,357.03501228871096,346.0057802985378,358.235955761004,363.0123964825444,352.00142045167945,362.0013812128346,360.0888779176608,342.01315764163223,347.17430780517157,357.0014005574768],"type":"histogram"}],                        {"template":{"data":{"barpolar":[{"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"white","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"#C8D4E3","linecolor":"#C8D4E3","minorgridcolor":"#C8D4E3","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"white","showlakes":true,"showland":true,"subunitcolor":"#C8D4E3"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"white","polar":{"angularaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""},"bgcolor":"white","radialaxis":{"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"yaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"},"zaxis":{"backgroundcolor":"white","gridcolor":"#DFE8F3","gridwidth":2,"linecolor":"#EBF0F8","showbackground":true,"ticks":"","zerolinecolor":"#EBF0F8"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"baxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""},"bgcolor":"white","caxis":{"gridcolor":"#DFE8F3","linecolor":"#A2B1C6","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"#EBF0F8","linecolor":"#EBF0F8","ticks":"","title":{"standoff":15},"zerolinecolor":"#EBF0F8","zerolinewidth":2}}},"title":{"text":"Histogram of Interocular Distances (100 Random Faces)"},"xaxis":{"title":{"text":"Interocular Distance (pixels)"}},"yaxis":{"title":{"text":"Count"}},"bargap":0.1},                        {"responsive": true}                    )                };                            </script>        </div>

In this blog, we'll walk through a practical workflow for downloading random synthetic faces, converting image formats, applying facial landmark detection with **MediaPipe**, and performing basic morphometric analysis. We'll also visualize results to explore variations in facial features, such as interocular distances, across random faces.

This tutorial assumes familiarity with Python, OpenCV, and basic image processing concepts.

---

## Installing Dependencies

We use **MediaPipe**, OpenCV, NumPy, Pillow, Matplotlib, and Plotly. First, install MediaPipe (the rest are standard in most Python environments).

```python
#Run this block more than once
!pip install mediapipe
import mediapipe as mp
```

---

## Downloading Random Faces

We can fetch synthetic faces from [thispersondoesnotexist.com](https://thispersondoesnotexist.com/) and save them locally.

```python
import requests

# Download 3 random faces
image_paths = ["/content/frontal1.jpg", "/content/frontal2.jpg", "/content/frontal3.jpg"]
for path in image_paths:
    resp = requests.get("https://thispersondoesnotexist.com/")
    if resp.status_code == 200:
        with open(path, "wb") as f:
            f.write(resp.content)
```

This creates three JPG images that we can process later.

---

## Viewing Images in Jupyter Notebook

We can read image files as bytes and display them inline.

```python
import cv2, numpy as np, mediapipe as mp
from PIL import Image
from io import BytesIO
from IPython.display import Image as IPyImage

def img_file_path_to_img_bytes(file_path):
  with open(file_path, 'rb') as f:
    return f.read()

img_bytes = img_file_path_to_img_bytes('frontal1.jpg')
IPyImage(img_bytes)
```

---

## Converting JPG to PNG

Sometimes downstream processing works better with PNGs due to lossless compression.

```python
from PIL import Image

def jpg_to_png(jpg_path, png_path):
  """Converts a JPG image to PNG format."""
  try:
    img = Image.open(jpg_path)
    img.save(png_path, 'PNG')
    print(f"Successfully converted {jpg_path} to {png_path}")
  except Exception as e:
    print(f"Error converting {jpg_path}: {e}")

# Example usage:
jpg_file = '/content/frontal1.jpg'
png_file = '/content/frontal1.png'
jpg_to_png(jpg_file, png_file)

img_bytes = img_file_path_to_img_bytes('frontal1.png')
IPyImage(img_bytes)
```

---

## Applying MediaPipe Face Mesh

MediaPipe Face Mesh allows detecting 468 3D facial landmarks. We can overlay these landmarks for visualization.

```python
def img_bytes_to_meshed_img_bytes(img_bytes):
    # Decode image from raw bytes
    img_array = np.frombuffer(img_bytes, dtype=np.uint8)
    image = cv2.imdecode(img_array, cv2.IMREAD_UNCHANGED)

    if image is None:
        raise ValueError("Could not decode image from bytes")

    # Handle alpha channel or grayscale
    if image.ndim == 3 and image.shape[2] == 4:
        image = cv2.cvtColor(image, cv2.COLOR_BGRA2BGR)
    elif image.ndim == 2:
        image = cv2.cvtColor(image, cv2.COLOR_GRAY2BGR)

    # Convert BGR → RGB
    img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

    # Run MediaPipe Face Mesh
    mp_face_mesh = mp.solutions.face_mesh
    with mp_face_mesh.FaceMesh(static_image_mode=True, max_num_faces=1, refine_landmarks=True) as face_mesh:
        results = face_mesh.process(img_rgb)

    # Copy for drawing
    output_img_rgb = img_rgb.copy()
    if results.multi_face_landmarks:
        mp_drawing = mp.solutions.drawing_utils
        for face_landmarks in results.multi_face_landmarks:
            mp_drawing.draw_landmarks(
                image=output_img_rgb,
                landmark_list=face_landmarks,
                connections=mp_face_mesh.FACEMESH_TESSELATION,
                landmark_drawing_spec=None,
                connection_drawing_spec=mp_drawing.DrawingSpec(
                    color=(0, 255, 0), thickness=1, circle_radius=0)
            )

    # Convert result back to PNG bytes
    img_pil = Image.fromarray(output_img_rgb)
    buf = BytesIO()
    img_pil.save(buf, format="PNG")
    buf.seek(0)
    return buf.getvalue()

# Example usage
img_mesh_bytes = img_bytes_to_meshed_img_bytes(img_bytes)
IPyImage(img_mesh_bytes)  # display in notebook
```

---

## Extracting Morphometric Measurements

We can measure distances between landmarks to obtain facial morphometrics such as **interocular distance**, **nose width**, or **mouth width**.

```python
from math import dist
import json

def png_bytes_to_morphometric_json(png_bytes):
    # Decode image from bytes
    png_array = np.frombuffer(png_bytes, dtype=np.uint8)
    image = cv2.imdecode(png_array, cv2.IMREAD_UNCHANGED)

    if image.shape[-1] == 4:
        image = cv2.cvtColor(image, cv2.COLOR_BGRA2BGR)
    elif len(image.shape) == 2:
        image = cv2.cvtColor(image, cv2.COLOR_GRAY2BGR)

    img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

    # Initialize Mediapipe FaceMesh
    mp_face_mesh = mp.solutions.face_mesh
    with mp_face_mesh.FaceMesh(
        static_image_mode=True,
        max_num_faces=1,
        refine_landmarks=True
    ) as face_mesh:

        results = face_mesh.process(img_rgb)

    if not results.multi_face_landmarks:
        return json.dumps({"error": "No face detected"})

    # Get image dimensions
    h, w, _ = img_rgb.shape
    face_landmarks = results.multi_face_landmarks[0]

    # Convert normalized landmarks to pixel coordinates
    landmarks = [(int(lm.x * w), int(lm.y * h)) for lm in face_landmarks.landmark]

    # Example morphometric measurements
    # Define some standard landmarks based on Mediapipe indices
    measurements = {}

    def euclidean(p1, p2):
        return dist(landmarks[p1], landmarks[p2])

    # Sample morphometrics
    measurements["interocular_distance"] = euclidean(33, 263)  # Eye corners
    measurements["eye_width_left"] = euclidean(133, 33)
    measurements["eye_width_right"] = euclidean(362, 263)
    measurements["nose_width"] = euclidean(97, 326)
    measurements["nose_length"] = euclidean(1, 2)
    measurements["mouth_width"] = euclidean(61, 291)
    measurements["face_width"] = euclidean(234, 454)
    measurements["face_height"] = euclidean(10, 152)

    # You can normalize or return raw pixels depending on your use case
    return json.dumps(measurements)

# Example usage
png_bytes_to_morphometric_json(img_bytes)
```

---

## Automating Face Download and Analysis

We can wrap random face downloads and analysis into a loop to collect statistics:

```python
import requests
import random

def get_random_face_bytes():
    """
    Downloads a random face from thispersondoesnotexist.com
    and returns it as raw image bytes.
    """
    url = "https://thispersondoesnotexist.com/"
    resp = requests.get(url)
    if resp.status_code != 200:
        raise RuntimeError(f"Failed to download image, status code: {resp.status_code}")
    return resp.content

# Example usage
img_bytes = get_random_face_bytes()

# Display in notebook
from IPython.display import Image as IPyImage
IPyImage(img_bytes)
```

---

## Collecting Interocular Distances from 100 Random Faces

```python
import json

io_distances = []

for i in range(100):
    try:
        img_bytes = get_random_face_bytes()
        morpho_json = png_bytes_to_morphometric_json(img_bytes)
        morpho = json.loads(morpho_json)  # <-- parse JSON

        if "interocular_distance" in morpho:
            io_distances.append(morpho["interocular_distance"])
    except Exception as e:
        print(f"Skipping face {i} due to error: {e}")
```

---

## Visualizing Morphometric Distributions

### Matplotlib Histogram

```python
import matplotlib.pyplot as plt
# Plot histogram
plt.figure(figsize=(10, 6))
plt.hist(io_distances, bins=15, color='skyblue', edgecolor='black')
plt.title("Histogram of Interocular Distances (100 Random Faces)")
plt.xlabel("Interocular Distance (pixels)")
plt.ylabel("Count")
plt.show()
```

### Interactive Plotly Histogram

```python
import plotly.graph_objects as go

fig = go.Figure()

fig.add_trace(go.Histogram(
    x=io_distances,
    nbinsx=15,
    marker_color='skyblue',
    marker_line_color='black',
    marker_line_width=1
))

fig.update_layout(
    title="Histogram of Interocular Distances (100 Random Faces)",
    xaxis_title="Interocular Distance (pixels)",
    yaxis_title="Count",
    bargap=0.1,
    template="plotly_white"
)

fig.show()
```

---

## Conclusion

In this post, we demonstrated:

* Downloading random synthetic faces
* Converting image formats (JPG → PNG)
* Applying **MediaPipe Face Mesh** for landmark detection
* Calculating basic morphometric features
* Aggregating statistics and visualizing distributions

This pipeline provides a solid foundation for large-scale facial morphometric analysis or synthetic dataset exploration. From here, you could expand to **3D face modeling, automated feature normalization, or machine learning pipelines**.


