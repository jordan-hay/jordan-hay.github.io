---
layout: post
title:  "How to Push a Python Pandas Dataframe from Google Colaboratory to a Microsoft Fabric Lakehouse Using Microsoft Azure App Registrations and API Permissions"
date:   2024-2-10 06:25:17 -0800
categories: jekyll update technology
---

## Introduction:

In the era of data-driven decision-making, integrating and managing data seamlessly is paramount. Microsoft Azure provides a robust platform for handling data, and this technical guide will walk you through the steps of setting up an Azure environment to facilitate data integration using Python, Microsoft Fabric and the Azure Storage service.

## Home:

Before diving into the technical details, ensure that you are logged into the Azure portal and are on the Home page.

## Manage Microsoft Entrata ID:

To get started, manage your Microsoft Entrata ID. This includes key details such as Application ID, Client Secret Value, Directory ID, User Name, and Password. These credentials will be crucial for authenticating and accessing Azure services programmatically. Navigate to App registrations, All applications, and create an application.

## Google Colaboratory:

```python
Application_ID = "?????"  # e.g. "00aa00aaa000-0a0a-a0aa-00aaa0aaaa0a"
Client_Secret_Value = "?????" # e.g. "aa111a~aa1aaaa1aaaa1aaaaaaaaaa1aaaaaaaa00"
Directory_ID = "?????" # e.g. "1s0a1a11-1a11-1a11-1111-aaaa11aa1111"
User_Name = "?????" # the email you log into Azure with
Password = "?????"   # the password you use to log into Azure with

# In Microsoft Fabric go to Lakehouse Explorer, Files, Properties
FilesURL = # e.g. "https://onelake.dfs.fabric.microsoft.com/myworkspace/mylakehouse.Lakehouse/Files/"
```

## Enroll in Free Azure Trial:

If you haven't already, enroll in the Azure free trial to access essential Azure services.

## Add Storage to Azure:

Once enrolled, add storage to your Azure account. This will serve as the repository for your data files.

## API Permissions - Add Azure Storage:

Grant API permissions for Azure Storage to ensure that your application has the necessary access.

## Entrata - Overview, Properties, Manage Security Defaults:

In Entrata, go to Overview, Properties, and manage security defaults. This step ensures that your environment is secured appropriately.

## Disable Security Defaults:

Disable security defaults if they are enabled. This provides more control over the security settings within your Azure environment.

## Python Script

Now, let's dive into the Python script that utilizes the obtained credentials and configured Azure environment for data integration.

```python
# Python script for Azure Data Integration

import requests
import json
import pandas as pd

# Obtain Access Token
token_url = f"https://login.microsoftonline.com/{Directory_ID}/oauth2/token"
token_data = {
    "grant_type": "password",
    "client_id": Application_ID,
    "client_secret": Client_Secret_Value,
    "resource": "https://storage.azure.com/",
    "scope": "https://graph.microsoft.com",
    "username": User_Name,
    "password": Password,
}

token_response = requests.post(token_url, data=token_data)
token_response = json.loads(token_response.text)
token = token_response["access_token"]
print(token)

# Create a DataFrame and convert to CSV
csvfilename = 'datafile.csv'
df = pd.DataFrame(
    {'a': ['1ee', 2, 999],
     'b': [4, 5, 6],
     'c': [7, 8, 9]})
file_contents = df.to_csv(index=False)

# Upload CSV to Azure Storage
token_url = f"{FilesURL}{csvfilename}?resource=file"
token_headers = {"Authorization": "Bearer " + token}
response = requests.put(token_url, data={}, headers=token_headers)

# Append data to the CSV in Azure Storage
token_url = f"{FilesURL}{csvfilename}?position=0&action=append&flush=true"
response = requests.patch(token_url, data=file_contents, headers=token_headers)
print(response.text)
```

The csv file should now be in the Microsoft Fabric lakehouse folder.

## Summary:

In conclusion, this script showcases the process of obtaining an access token and using it to interact with Azure Storage for data integration. With the right configuration and credentials, Microsoft Azure provides a powerful platform for seamless data integration, allowing you to harness the full potential of your data.