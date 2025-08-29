---
layout: post
title:  "Generating and Analyzing Random Python Avatars with Machine Learning"
date:   2025-8-24 09:25:17 -0800
categories: jekyll update data
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Generating_and_Analyzing_Random_Python_Avatars_with_Machine_Learning.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

![image tooltip here](/assets/images/avneighbors.png){: width="500" }


Avatars are a fun and creative way to represent users in applications. Today, we’ll explore how to generate **random Python avatars** using the `python-avatars` library, convert them to machine-readable vectors, and find visually similar avatars using a **Nearest Neighbors** approach.

We’ll also visualize the results to better understand avatar similarity.

---

## Installation

To get started, we need a few Python libraries. Run the following commands:

```python
!pip install python-avatars
!pip install cairosvg
```

---

## Importing Required Libraries

```python
import python_avatars as pa
from IPython.display import Image as IPyImage
import random
import json
import numpy as np
import cairosvg
import PIL
from io import BytesIO
```

These imports include:

* `python-avatars` for avatar generation.
* `cairosvg` and `PIL` for converting SVGs to PNGs.
* `numpy` for numerical operations.
* `IPython.display` for inline display in Jupyter notebooks.

---

## Converting Avatars to PNG Bytes

To work with avatars as images, we convert them from SVG to PNG:

```python
def python_avatar_to_png_bytes(avatar):
    raw_png_bytes = cairosvg.svg2png(bytestring=avatar.render())
    pil_img = PIL.Image.open(BytesIO(raw_png_bytes)).convert("RGB")
    buf = BytesIO()
    pil_img.save(buf, format='PNG')
    return buf.getvalue()
```

This function:

1. Renders the avatar as SVG.
2. Converts it to a PNG image.
3. Returns the image bytes for further processing.

---

## Defining Avatar Traits

`python-avatars` supports multiple traits. We define all possible traits:

```python
# Define all traits
traits = {
    "Hair Type": list(pa.HairType),
    "Hair Color": list(pa.HairColor),
    "Facial Hair Type": list(pa.FacialHairType),
    "Eye Type": list(pa.EyeType),
    "Eyebrow Type": list(pa.EyebrowType),
    "Mouth Type": list(pa.MouthType),
    "Nose Type": list(pa.NoseType),
    "Skin Color": list(pa.SkinColor),
    "Clothing Type": list(pa.ClothingType),
    "Clothing Color": list(pa.ClothingColor),
    "Background Color": [list(pa.BackgroundColor)[0]],
    "Avatar Style": [list(pa.AvatarStyle)[0]]
}
```

---

## Generating a Random Avatar

We can create avatars with random combinations of traits:

```python
def generate_random_python_avatar():

  selected_traits = {k: random.choice(v) for k, v in traits.items()}

  # Create avatar
  avatar = pa.Avatar(
      style=selected_traits["Avatar Style"],
      top=selected_traits["Hair Type"],
      hair_color=selected_traits["Hair Color"],
      mouth=selected_traits["Mouth Type"],
      eyes=selected_traits["Eye Type"],
      nose=selected_traits["Nose Type"],
      eyebrows=selected_traits["Eyebrow Type"],
      skin_color=selected_traits["Skin Color"],
      clothing=selected_traits["Clothing Type"],
      clothing_color=selected_traits["Clothing Color"],
      background_color=selected_traits["Background Color"],
      facial_hair=selected_traits["Facial Hair Type"]
  )

  avatar_data = {k: v.name for k, v in selected_traits.items()}
  return (python_avatar_to_png_bytes(avatar),json.dumps(avatar_data))

random_avatar = generate_random_python_avatar()
display(IPyImage(random_avatar[0]))
display(random_avatar[1])
```

This function returns both the PNG image and a JSON string describing the avatar's traits.

---

## Converting PNG to RGB Vector

To use machine learning, we convert images into numeric vectors:

```python
def png_bytes_to_rgb_vector (pngbytes):
  data = np.array(PIL.Image.open(BytesIO(pngbytes)).convert('RGB')).flatten()
  return data

avatar = pa.Avatar()
pngbytes = python_avatar_to_png_bytes(avatar)
png_bytes_to_rgb_vector(pngbytes)
```

Here, each pixel's RGB values are flattened into a 1D array.

---

## Finding Similar Avatars with Nearest Neighbors

We can generate multiple avatars and use the **Euclidean distance** between their RGB vectors to find similar-looking avatars:

```python
from sklearn.neighbors import NearestNeighbors

# Generate random avatars
avatars = [generate_random_python_avatar() for _ in range(3000)]
avatar_images = [a[0] for a in avatars]

# Convert to RGB vectors
rgb_vectors = np.array([png_bytes_to_rgb_vector(img) for img in avatar_images])

# Find 5 nearest neighbors for the first avatar
nbrs = NearestNeighbors(n_neighbors=4, algorithm='auto', metric='euclidean').fit(rgb_vectors)
distances, indices = nbrs.kneighbors([rgb_vectors[0]])

# Show first avatar
print("First avatar:")
display(IPyImage(avatar_images[0]))
print("Traits:", avatars[0][1])

# Show 5 nearest neighbors
print("5 nearest neighbors:")
for idx in indices[0][1:]:
    display(IPyImage(avatar_images[idx]))
    print("Traits:", avatars[idx][1])
```

---

## Visualizing Similar Avatars

Finally, we create a grid to visualize the first avatar and its closest neighbors:

```python
import matplotlib.pyplot as plt

# Get the first avatar and its 5 nearest neighbors
neighbor_indices = indices[0]  # includes the first avatar itself
all_indices = neighbor_indices  # 6 avatars: first + 5 neighbors

# Number of columns in the grid
n_cols = 4
n_rows = (len(all_indices) + n_cols - 1) // n_cols

plt.figure(figsize=(n_cols*3, n_rows*3))

for i, idx in enumerate(all_indices):
    plt.subplot(n_rows, n_cols, i+1)
    img = PIL.Image.open(BytesIO(avatar_images[idx]))
    plt.imshow(img)
    plt.axis('off')
    if i == 0:
        plt.title("Original")
    else:
        plt.title(f"Neighbor {i}")

plt.tight_layout()
plt.show()
```

This allows us to visually inspect which avatars are closest in appearance to the original.

---

## Conclusion

With just a few lines of Python, we can:

* Generate random avatars.
* Convert avatars to machine-readable vectors.
* Find visually similar avatars using nearest neighbor search.
* Visualize and analyze avatar similarity.

This workflow can be extended for applications like:

* Profile picture suggestions.
* Avatar clustering and analytics.
* Personalized gaming or social media avatars.


