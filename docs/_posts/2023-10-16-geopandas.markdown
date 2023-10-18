---
layout: post
title:  "Creating Interactive Maps with GeoPandas and Folium"
date:   2023-10-16 06:25:17 -0800
categories: jekyll update
---
## Introduction

In the world of data visualization, maps provide a powerful way to convey information. They allow us to explore geographical data and gain insights into spatial relationships. With Python libraries like GeoPandas and Folium, you can easily create interactive maps that visualize data in a visually appealing and informative manner.

<iframe src="/assets/los_angeles_map.html" height="200" width="100%"></iframe>

You can explore this map on it's own web page ([here](https://jordan-hay.github.io/assets/los_angeles_map.html){:target="_blank"}).

## What is GeoPandas?

GeoPandas is an open-source Python library that simplifies working with geospatial data. It extends the capabilities of the popular data manipulation library, Pandas, by adding support for geometric objects. This allows you to work with datasets that have a spatial component, such as points, lines, and polygons.

## What is Folium?

Folium is another Python library that works hand-in-hand with GeoPandas. It's a simple, yet powerful, library for creating interactive maps that can be embedded in web pages or Jupyter notebooks. Folium builds on the Leaflet JavaScript library, providing a high-level interface for creating maps with just a few lines of code.

In this blog post, we'll walk you through how to use GeoPandas and Folium to create an interactive map. We'll use the city of Los Angeles as an example and plot its boundary and a few museums on the map.

## Installation

Before we dive into the code, make sure you have both GeoPandas and Folium installed. You can use pip to install them:

```python
!pip install geopandas folium > /dev/null
```

## Creating the Map

We'll start by creating a GeoDataFrame for Los Angeles's boundary and a GeoDataFrame for some museums. Then, we'll use Folium to visualize these datasets on an interactive map.

```python
import geopandas as gpd
import folium
from shapely.geometry import Polygon, Point

# Create a Polygon for Los Angeles's boundary
los_angeles_coordinates = [
    (-118.602309, 33.702343),
    (-118.189537, 33.702343),
    (-118.189537, 34.337536),
    (-118.602309, 34.337536),
    (-118.602309, 33.702343)
]
los_angeles_boundary = gpd.GeoDataFrame({'geometry': [Polygon(los_angeles_coordinates)]}, crs="EPSG:4326")

# Create Point geometries for museums
museum_coordinates = [
    (-118.2437, 34.0522),  # Museum 1 (Los Angeles)
    (-118.2551, 34.0498),  # Museum 2
    (-118.2352, 34.0653),  # Museum 3
    # Add more museum points as needed
]

museum_geometries = [Point(coord) for coord in museum_coordinates]
museum_gdf = gpd.GeoDataFrame(geometry=museum_geometries, crs="EPSG:4326")

# Create a Folium map centered around Los Angeles
m = folium.Map(location=[34.0522, -118.2437], zoom_start=10)

# Add the Los Angeles boundary to the map and shade it
folium.GeoJson(los_angeles_boundary).add_to(m)

# Add museum markers to the map
for index, row in museum_gdf.iterrows():
    folium.Marker([row.geometry.y, row.geometry.x]).add_to(m)

# Display the map
m.save("los_angeles_map.html")
```

In the code above, we first create the Los Angeles boundary as a Polygon and the museum locations as Points. We then use Folium to create an interactive map, add the boundary and museum markers to it, and save the map as an HTML file.

## Adding More Data with Web Scraping

Now that we have a basic map, let's enhance it by adding more data. We can scrape data from a public GIS server using the `requests` library and display additional information about each museum on the map.

```python
import requests
import json

# URL to scrape data from
url = "https://public.gis.lacounty.gov/public/rest/services/LACounty_Dynamic/LMS_Data_Public/MapServer/6/query?outFields=*&where=1%3D1&f=geojson"

try:
    # Send a GET request to the URL
    response = requests.get(url)

    # Check if the request was successful
    if response.status_code == 200:
        # Parse the JSON response
        data = response.json()

        # Save the JSON data to a file
        with open("lacounty_data.json", "w") as json_file:
            json.dump(data, json_file, indent=4)

        print("Data scraped and saved to lacounty_data.json")

    else:
        print(f"Failed to retrieve data. Status code: {response.status_code}")

except Exception as e:
    print(f"An error occurred: {str(e)}")

# Read the scraped data with GeoPandas
lac = gpd.read_file("lacounty_data.json")

# Add a boundary to the map and shade it
folium.GeoJson(lac).add_to(m)

# Add museum markers to the map with popups
for index, row in lac.iterrows():
    museum_url = ""
    try:
        museum_url = "https://" + row[14].replace("https://", "").replace("http://", "")
        if museum_url == "https://":
            museum_url = "https://" + row[15].replace("https://", "").replace("http://", "")
    except:
        pass

    museum_name = row[7]
    popup_link = f'<strong>{museum_name}</strong><br><a href="{museum_url}" target="_blank">Visit Museum</a>'
    popup_content = f"{popup_link}"
    folium.Marker([row.geometry.y, row.geometry.x], popup=popup_content).add_to(m)

# Display the map
m.save("los_angeles_map.html")
m
```

In this extended code, we scrape data from a Los Angeles County GIS server, which contains information about various places, including museums. We read this data into a GeoDataFrame and add it to our map. Additionally, we generate popups for each museum, providing users with the option to visit the museum's website.

## Conclusion

GeoPandas and Folium are a powerful combination for creating interactive maps in Python. They enable you to visualize geographical data, display boundaries, and provide detailed information about specific locations. This blog post demonstrates how to get started with these libraries and build informative maps that can be shared with others.



