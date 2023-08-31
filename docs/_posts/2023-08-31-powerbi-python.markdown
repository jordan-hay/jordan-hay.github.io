---
layout: post
title:  "Executing DAX Queries in Power BI Using Python within Jupyter Notebook"
date:   2023-08-31 06:25:17 -0800
categories: jekyll update
category:
---

<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Using_ Python_to_Execute_DAX_Queries_in_Power_BI.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>




In the realm of business intelligence and data visualization, Power BI stands as one of the premier tools for creating insightful reports and dashboards. It allows users to connect to various data sources, model data, and then visualize it in a way that supports data-driven decision-making. While Power BI offers a robust set of features, there might be cases where you want to leverage Python for more advanced data manipulation and analysis. In this blog post, we will explore how to use Python to execute DAX (Data Analysis Expressions) queries within Power BI, enhancing your data analysis capabilities.

## Setting Up the Scene

Let's begin by creating a scenario where we have a Power BI report named `practice.pbix`. Our objective is to integrate Python code that fetches data and performs some initial preprocessing. Here's how you can do it:

1. **Fetching Data with Python**: First, we utilize Python to retrieve data. We use the `pandas` library to read data from different CSV sources. This data is then combined and transformed into a unified DataFrame named `df`. This DataFrame contains employee earnings data for the years 2020, 2021, and 2022.
```python
import pandas as pd
df2022=pd.read_csv('https://data.boston.gov/dataset/418983dc-7cae-42bb-88e4-d56f5adcf869/resource/63ac638b-36c4-487d-9453-1d83eb5090d2/download/finalconsolidatedcy22earnings_feb2023.xlsx-sheet1.csv')
names=df2022.columns
df2021=pd.read_csv('https://data.boston.gov/dataset/418983dc-7cae-42bb-88e4-d56f5adcf869/resource/ec5aaf93-1509-4641-9310-28e62e028457/download/employee-earnings-report-2021.csv',encoding= 'unicode_escape',skiprows=1,names=names)
df2020=pd.read_csv('https://data.boston.gov/dataset/418983dc-7cae-42bb-88e4-d56f5adcf869/resource/e2e2c23a-6fc7-4456-8751-5321d8aa869b/download/city-of-boston-calendar-year-2020-earnings.csv',encoding= 'unicode_escape',skiprows=1,names=names)
df2022["Month"]="1/1/2022"
df2021["Month"]="1/1/2021"
df2020["Month"]="1/1/2020"
df0=pd.concat([df2022, df2021 ,df2020])
dtype = {'col1':str, 'col2':str,'col3':str,'col4':float,'col5':float,'col6': float,'col7': float,'col8': float,'col9': float,'col10': float,'col11': float,'col12': int,'col13':str}
for key,col in zip(dtype.keys(),df0.columns):
  if dtype[key]==float:
    df0[col]=pd.to_numeric(df0[col].str.replace(",","").str.replace("$","").str.replace(" ","").str.replace("(","-").str.replace(")",""))
months=pd.concat([df0.Month.str.replace("1/1/",str(i)+"/1/") for i in range(1,13)])
df=pd.concat([df0 for i in range(1,13)])
df.Month=months
cols=df.select_dtypes(include=float).columns
df[cols] = df[cols].div(12)
from pandas.tseries.offsets import MonthEnd
df['Month'] = pd.to_datetime(df['Month'], format="%m/%d/%Y") + MonthEnd(1)
```

2. **Creating a Date Table in Power BI**: Within Power BI, we create a calculated table named `Calendar` to serve as a date table. This table contains a range of dates from January 1, 2020, to December 31, 2022. This table is marked as a date table, which is essential for time-based calculations.

3. **Establishing Connections**: We establish a connection between the `Month` column in our Python-loaded DataFrame (`df`) and the `Date` column in the `Calendar` table in Power BI. This connection ensures that date-based calculations can be performed seamlessly.

## Connecting DAX Studio to Your Power BI Model

Before delving into executing DAX queries using Python, it's important to set up the connection between DAX Studio and your Power BI model. Here's how you can do it:

1. **Connect to Power BI Model**: Open DAX Studio and navigate to the "Connect" menu. From the dropdown, select "Power BI / SSDT Model" and then choose your Power BI model (in this case, `practice.pbix`) to connect.

2. **Retrieve Catalog Information**: With the Power BI model connected, run the following SQL query in the DAX Studio query window to retrieve the catalog information:
```
SELECT * FROM $SYSTEM.DBSCHEMA_CATALOGS
```This query provides metadata about the available catalogs, and it includes the catalog number you need for the connection.

3. **Note the Port Number**: While connected to your Power BI model in DAX Studio, you'll notice the port number displayed at the bottom right corner of the DAX Studio window. Make a note of this port number.

Now that you have the catalog number and the port number, you can use them in your Python code to establish a connection to your Power BI model as demonstrated below.



## Using Jupyter Notebook to Execute DAX Queries

Now comes the exciting part - executing DAX queries using Python within a Jupyter Notebook. This integration enhances our analytical capabilities by allowing more complex calculations and manipulations.

### Importing Required Libraries

To get started, you need to import the required libraries and set up the connection to your Power BI model:

```python
import pandas as pd
from sys import path
path.append('\\Program Files\Microsoft.NET\\ADOMD.NET\\160')
from pyadomd import Pyadomd
```

### Establishing a Connection

The next step is to establish a connection to your Power BI model using the `pyadomd` library. You need the `model_name` (catalog number) and the `port_number` (found at the bottom of DAX Studio) to form the connection string:

```python
model_name = 'YOUR_MODEL_NAME'
port_number = 'YOUR_PORT_NUMBER'
connection_string = f'Provider=MSOLAP;Data Source={port_number};Catalog={model_name};'
con = Pyadomd(connection_string)
```

### Creating a Custom DAX Query Magic

Now, we can create a custom DAX query magic for Jupyter Notebook, which will allow us to execute DAX queries directly within the notebook:

```python
from IPython.core.magic import (register_line_magic, register_cell_magic)

@register_cell_magic
def dax(line, cell):
    conn = Pyadomd(connection_string)
    try:
        conn.open()
        result = conn.cursor().execute(cell)
        return pd.DataFrame(result.fetchone())
        conn.close()
    except:
        conn.close()
```

### Running DAX Queries

With the custom magic in place, you can now run DAX queries directly within your Jupyter Notebook cells using the `%%dax` magic command. Here are some examples:

```python
%%dax
EVALUATE
FILTER(SUMMARIZE(COLUMNSTATISTICS(), [Table Name], [Column Name]), [Table Name] = "df")
```


```python
%%dax
EVALUATE
FILTER(df, [TITLE] = "Teacher")
```
The following DAX code block encapsulates a series of calculations and data transformations to derive insightful metrics from the `df` dataset, which presumably contains employee earnings data. In this code, a custom measure named `Total Monthly Gross` is defined to calculate the sum of the `TOTAL_ GROSS` values, but only for records where the `TITLE` is "Teacher". Subsequently, the `EVALUATE` statement is used in conjunction with several DAX functions to construct a table of aggregated results. This table is created by summarizing and filtering the `df` dataset specifically for records with the `TITLE` "Teacher". The summarized results include the teacher's title, the corresponding month, the count of employees (`Number of EE`), and the year-to-date sum of the `Total Monthly Gross`. Additionally, a calculated column computes the "Monthly Gross / person" ratio by dividing the YTD value by the number of employees. The final result is then ordered in ascending order first by teacher title and then by month, facilitating a clear presentation of the derived metrics. This complex DAX script showcases the ability to transform raw data into meaningful insights within Power BI.

```python
%%dax
DEFINE MEASURE df[Total Monthly Gross] = CALCULATE(
    SUM(df[TOTAL_ GROSS]),
    df[TITLE] = "Teacher"
)

EVALUATE
ADDCOLUMNS(
    SUMMARIZE(
        FILTER(df, df[TITLE] = "Teacher"),
        df[TITLE],
        df[Month],
        "Number of EE", COUNT(df[NAME]),
        "YTD", CALCULATE(TOTALYTD(df[Total Monthly Gross], 'Calendar'[Date], ALL(df)))
    ),
    "Monthly Gross / person", [YTD] / [Number of EE]
)

ORDER BY
    df[TITLE] ASC,
    df[Month] ASC
```

## Conclusion

Integrating Python and Power BI opens up a world of possibilities for advanced data analysis and visualization. By leveraging the power of Python to preprocess and manipulate data, and executing complex DAX queries directly from Jupyter Notebook, you can unlock deeper insights and enhance the value of your Power BI reports. This integration demonstrates the synergy between two powerful tools, allowing you to create more sophisticated and insightful data stories.
