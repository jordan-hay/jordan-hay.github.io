---
layout: post
title:  "Automating Avatar Rendering with Blender and Python in Google Colaboratory"
date:   2025-6-28 09:25:17 -0800
categories: jekyll update technology
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Automating_Avatar_Rendering_with_Blender_and_Python_in_Google_Colaboratory.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

![image tooltip here](/assets/images/avatararraypng.png){: width="500" }


In this tutorial, we’ll walk through a pipeline to fetch a diverse set of 3D avatar models from a GitHub repository, convert them into Blender-compatible `.blend` files, and generate randomized renders of full models and faces. This workflow is designed for technical users comfortable with Python, Blender, and command-line operations.

---

## 1. Cloning the Standard GitHub Avatar Repository

We start by cloning the [Validated Avatar Library](https://github.com/xrtlab/Validated-Avatar-Library-for-Inclusion-and-Diversity---VALID) which contains FBX assets for inclusion and diversity research:

```bash
#Clone the Standard Github Avatar Repo
!git clone https://github.com/xrtlab/Validated-Avatar-Library-for-Inclusion-and-Diversity---VALID.git
!cd Validated-Avatar-Library-for-Inclusion-and-Diversity---VALID/Avatars
```

---

## 2. Collecting All FBX Files

We traverse the repository to collect all `.fbx` files into a list of raw GitHub URLs:

```python
import os

base_raw_url = 'https://github.com/xrtlab/Validated-Avatar-Library-for-Inclusion-and-Diversity---VALID/raw/refs/heads/main/Avatars'
raws = []

for root, dirs, files in os.walk('.'):
    for file in files:
        if file.endswith('.fbx'):
            # Get last directory name from root
            last_subdir = os.path.basename(root)
            # Combine last subdir and filename
            partial_path = f"{last_subdir}/{file}"
            raws.append(f"{base_raw_url}/{partial_path}")
```

---

## 3. Downloading FBX Files Locally

We create a folder and download all FBX assets:

```bash
!mkdir fbxs

for raw_url in raws:
    file_name = os.path.basename(raw_url)
    !wget -q -O fbxs/{file_name} {raw_url}

import shutil
!zip -r fbxs.zip fbxs

zip_file_path = 'fbxs.zip'
```

---

## 4. Installing and Preparing Blender

Blender is required for importing FBX files and rendering them:

```bash
# Blender
import os
import inspect
from IPython.display import Image

# Download and Extract Blender
!wget https://download.blender.org/release/Blender4.4/blender-4.4.3-linux-x64.tar.xz  -O /content/BlenderDownload.tar.xz
!tar -xf /content/BlenderDownload.tar.xz -C /content/

blender_path = 'blender-4.4.3-linux-x64/blender'
```

---

## 5. Converting FBX to Blender `.blend` Files

We define a Blender Python script to import an FBX file and save it as a `.blend` file:

```python
%%writefile /content/fbx_to_blend.py
import bpy

# Clear existing scene
bpy.ops.wm.read_factory_settings(use_empty=True)

# Path to your FBX file
fbx_path = "/content/model.fbx"

# Import FBX
bpy.ops.import_scene.fbx(filepath=fbx_path)

# (Optional) Save the result
bpy.ops.wm.save_as_mainfile(filepath="/content/model.blend")

# Run Blender in background mode with the import script
#!./{blender_path} -b --python /content/fbx_to_blend.py

def fbx_to_blend():
  function_name = inspect.currentframe().f_code.co_name
  blender_cmd = f"./{blender_path} -b --python /content/{function_name}.py"
  os.system(blender_cmd)
```

Next, we batch process all FBX files:

```python
!mkdir blends

import os
import shutil

fbx_folder = '/content/fbxs'
temp_fbx_path = '/content/model.fbx'
blend_folder = '/content/blends'

# Loop through files in the 'fbxs' folder
for filename in os.listdir(fbx_folder):
    if filename.endswith(".fbx"):
        source_path = os.path.join(fbx_folder, filename)
        # Copy the FBX file to '/content/model.fbx'
        shutil.copyfile(source_path, temp_fbx_path)
        print(f"Copied {filename} to {temp_fbx_path}")
        fbx_to_blend()
        print(f"Processed {filename}")
        base, _ = os.path.splitext(filename)   # split name and extension
        new_filename = base + ".blend"   
        shutil.copyfile('/content/model.blend', os.path.join(blend_folder,new_filename))
```

---

## 6. Rendering Full Model Images

We create a Blender script to render full models with Cycles:

```python
%%writefile blend_to_png_model.py
import bpy
scene = bpy.context.scene
scene.render.engine = 'CYCLES'
scene.render.filepath = '/content/model.png'
scene.render.image_settings.file_format = 'PNG'

scene.cycles.samples = 8
scene.cycles.use_adaptive_sampling = True
scene.cycles.use_denoising = True
scene.render.resolution_x = 800
scene.render.resolution_y = 600
scene.render.resolution_percentage = 100

# Create a camera if one doesn't exist
cam_data = bpy.data.cameras.new(name="Camera")
cam = bpy.data.objects.new("Camera", cam_data)
bpy.context.collection.objects.link(cam)
scene.camera = cam

cam.rotation_euler = (0, 0, 0)
cam.location = (0, -5, 1.6)
cam.rotation_euler = (1.5708, 0, 0)

sun_data = bpy.data.lights.new(name="Sun", type='SUN')
sun_data.energy = 3.0
sun = bpy.data.objects.new(name="Sun", object_data=sun_data)
bpy.context.collection.objects.link(sun)
sun.location = (0, -2, 5)
sun.rotation_euler = (1.2, 0, 0)

# Optional: frame the mesh (if camera is new)
bpy.ops.object.select_all(action='DESELECT')
bpy.ops.object.select_by_type(type='MESH')
bpy.ops.view3d.camera_to_view_selected()

# Render the image
bpy.ops.render.render(write_still=True)
```

We define a helper function to execute Blender in background mode:

```python
def blend_to_png_model():
  function_name = inspect.currentframe().f_code.co_name
  blender_cmd = f"./{blender_path} -b /content/model.blend --python /content/{function_name}.py"
  os.system(blender_cmd)
  with open("model.png", "rb") as f:
    image_bytes = f.read()
  return image_bytes

bytes = blend_to_png_model()
Image(data=bytes)
```

---

## 7. Randomizing Model Selection

We can randomly select a `.blend` file and render it:

```python
import os
import random
import shutil

def model_random_choice():
  blends_folder = '/content/blends'
  destination_blend_path = '/content/model.blend'

  blend_files = [f for f in os.listdir(blends_folder) if f.endswith('.blend')]

  if blend_files:
      chosen_file = random.choice(blend_files)
      source_path = os.path.join(blends_folder, chosen_file)
      shutil.copyfile(source_path, destination_blend_path)
      print(f"Randomly selected and copied '{chosen_file}' to '{destination_blend_path}'")
  else:
      print(f"No .blend files found in '{blends_folder}'")

model_random_choice()
bytes = blend_to_png_model()
Image(data=bytes)
```

---

## 8. Rendering Randomized Close-Up Poses

To generate face-focused images with random angles and distances, we use:

```python
%%writefile /content/blend_to_png_face.py
import bpy
import mathutils
import random
import math

scene = bpy.context.scene
# (Camera, lighting, and render setup omitted for brevity—full code included in original snippet)
bpy.ops.render.render(write_still=True)
```

Finally, we define a function to generate a grid of random face images:

```python
import math
import io
from PIL import Image as PILImage
import matplotlib.pyplot as plt

def generate_random_images(num_images):
    images = []
    for _ in range(num_images):
        img_bytes = blend_to_png_face()
        pil_img = PILImage.open(io.BytesIO(img_bytes))
        images.append(pil_img)

    cols = math.ceil(math.sqrt(num_images))
    rows = math.ceil(num_images / cols)

    fig, axs = plt.subplots(rows, cols, figsize=(3*cols, 3*rows))
    axs = axs.flatten() if hasattr(axs, 'flatten') else [axs]

    for ax, img in zip(axs, images):
        ax.imshow(img)
        ax.axis("off")
    for ax in axs[len(images):]:
        ax.axis("off")
    plt.tight_layout()
    plt.show()

generate_random_images(6)
model_random_choice()
generate_random_images(3)
```

---

## Conclusion

This workflow demonstrates a fully automated pipeline for:

* Downloading FBX avatars from GitHub
* Converting them to `.blend` files
* Randomly rendering full-body and face-focused images

It’s ideal for research in diversity, gaming, VR, or AI dataset creation. With this setup, you can generate hundreds of avatar renders programmatically with Blender’s powerful rendering engine.

