---
layout: post
title:  "Geospatial Analysis of City Amenities Using Overpass API"
date:   2025-4-25 07:25:17 -0800
categories: jekyll update data
---


<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Geospatial_Analysis_of_City_Amenities_Using_Overpass_API.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>



# Introduction

Understanding the distribution of key amenities like grocery stores, convenience stores, and schools is essential for urban planning, transportation analysis, and service accessibility studies. In this blog post, we use Python and open geospatial data to locate these places within Boise, Idaho. We then visualize the results on an interactive map and refine the address information through reverse geocoding. 

This end-to-end workflow showcases practical geospatial analysis techniques using Overpass API and Folium.

---

## Extracting Location Data with Overpass API

We begin by querying the Overpass API, which allows access to OpenStreetMap (OSM) data. Our goal is to retrieve the location of supermarkets, grocery stores, convenience stores, and schools in Boise.

```python
import requests
import pandas as pd
pd.set_option('display.max_rows', None)

# Overpass API URL
overpass_url = "http://overpass-api.de/api/interpreter"

# Overpass query for grocery stores, convenience stores, and schools
query = """
[out:json][timeout:25];
area["name"="Boise"]->.searchArea;

(
  node["shop"="supermarket"](area.searchArea);
  node["shop"="grocery"](area.searchArea);
  node["shop"="convenience"](area.searchArea);
  node["amenity"="school"](area.searchArea);
);
out body;
"""

# Send request to Overpass API
response = requests.get(overpass_url, params={'data': query})
data = response.json()

# List to hold store details
stores = []

# Loop through each element to extract address and type
for element in data['elements']:
    tags = element.get('tags', {})

    # Get the name of the store
    name = tags.get('name', 'N/A')

    # Get coordinates (latitude and longitude)
    lat = element.get('lat')
    lon = element.get('lon')

    # Get address components
    street = tags.get('addr:street', '')
    number = tags.get('addr:housenumber', '')
    city = tags.get('addr:city', '')
    state = tags.get('addr:state', '')
    postcode = tags.get('addr:postcode', '')

    # Build the full address
    address = f"{number} {street}, {city}, {state} {postcode}".strip().strip(',')

    # Determine the type of place (grocery, convenience, etc.)
    place_type = 'N/A'
    if 'shop' in tags:
        if tags['shop'] in ['supermarket', 'grocery', 'convenience']:
            place_type = tags['shop']
    elif 'amenity' in tags and tags['amenity'] == 'school':
        place_type = 'school'

    # Add the store information to the list
    stores.append({
        'Name': name,
        'Address': address,
        'Latitude': lat,
        'Longitude': lon,
        'Type': place_type
    })

# Create DataFrame from the list of stores
df = pd.DataFrame(stores)

# Display the DataFrame
df
```

This first part of the workflow creates a detailed DataFrame, capturing the name, type, latitude, longitude, and partial addresses of relevant locations across Boise.

---

## Visualizing Locations on an Interactive Map

To better understand the spatial patterns of these amenities, we use Folium to create an interactive map centered around the median latitude and longitude of the points we gathered.

```python
import folium

# Create a map 
m = folium.Map(location=[ df.Latitude.median(),df.Longitude.median()], zoom_start=12)

# Add markers for each store to the map
for index, row in df.iterrows():
    folium.Marker(
        location=[row['Latitude'], row['Longitude']],
        popup=row['Name'],  # Display the store name in the popup
        tooltip=row['Address'], # Display address on hover
    ).add_to(m)

# Display the map
m
```

Each marker on the map represents either a grocery store, convenience store, or school. Hovering over a marker reveals the address, while clicking pops up the name of the establishment. This visualization makes it easy to spot clustering patterns and coverage gaps in the city.

---

## Enhancing Address Accuracy with Reverse Geocoding

Some of the original data from OpenStreetMap may be incomplete or missing address details. To improve the quality of our dataset, we use Nominatim's reverse geocoding API to retrieve a formatted address for each set of coordinates.

```python
from time import sleep

# Function for reverse geocoding
def reverse_geocode(lat, lon):
    url = "https://nominatim.openstreetmap.org/reverse"
    params = {
        'format': 'jsonv2',
        'lat': lat,
        'lon': lon,
        'addressdetails': 1
    }
    headers = {
        'User-Agent': 'Mozilla/5.0 (compatible; example script)'
    }

    try:
        response = requests.get(url, params=params, headers=headers)
        if response.status_code == 200:
            data = response.json()
            return data.get('display_name', 'Not found')
        else:
            return f"Error {response.status_code}"
    except Exception as e:
        return str(e)

# Loop through rows and apply reverse geocoding
addresses = []
for i, row in df.iterrows():
    addr = reverse_geocode(row['Latitude'], row['Longitude'])
    addresses.append(addr)
    print(f"Row {i}: {addr}")
    #sleep(1)  # Nominatim rate limit: 1 request per second

# Add the addresses to the DataFrame
df['New_Address'] = addresses

# Display the updated DataFrame
df
```

Reverse geocoding refines our dataset by filling in detailed, standardized address information, improving the reliability of our mapping and any downstream analysis.

---

## Conclusion

This geospatial workflow shows how to leverage open data sources and Python tools for spatial analysis and visualization. We efficiently queried locations of interest in Boise, mapped them interactively, and enriched our data with high-quality address information. 

This method can easily be extended to other cities, expanded to other types of amenities, or enhanced with clustering and proximity analysis for deeper urban insights. Geospatial analysis like this is a powerful approach for researchers, planners, and businesses who want to understand the layout and accessibility of services within a community.


<iframe src="/assets/boise.html" height="300" width="100%"></iframe>