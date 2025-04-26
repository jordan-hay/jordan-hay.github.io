---
layout: post
title:  "Time Series Analysis in R: A Hands-on Approach"
date:   2025-2-11 07:25:17 -0800
categories: jekyll update data
---


<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Time_Series_Analysis_in_R_A_Hands_on_Approach.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

# Inroduction

Time series analysis is a crucial technique in understanding data that is indexed by time, such as stock prices, weather patterns, or agricultural outputs. In R, there are several ways to manipulate and analyze time series data. In this blog post, we'll walk through a basic example of time series analysis using a dataset from the <a href="https://github.com/FinYang/tsdl" target="_blank">`tsdl`</a> package. We'll cover how to subset, manipulate, and visualize time series data, focusing on essential functions in R for time series analysis. 

## Time Series in R

Time series analysis involves working with data points collected or recorded at specific time intervals. The primary goal is to analyze patterns, such as trends, seasonality, and cycles, within the data. R offers several packages and built-in functions to facilitate time series analysis, one of which is `tsdl`. This package contains various datasets related to different subjects, including agriculture, which we'll use in this example.

To begin, we need to install and load the necessary library. We will also take a look at a sample time series dataset related to agriculture.

```r
devtools::install_github("FinYang/tsdl")
library(tsdl)
print(tsdl)
```

Once the package is loaded, we can explore the available datasets. We choose a subject, specify the frequency (the number of observations per year), and select an example dataset.

## Subsetting and Exploring Time Series Data

Let's dive deeper into how to subset the data and extract a specific time series. Here, we'll focus on agricultural data with a monthly frequency. 

```r
subject <- "Agriculture"
frequency <- 12
example <- 2
ts <- subset(tsdl, frequency, subject)
ts <- ts[[example]]
ts
```

In this code, we selected the "Agriculture" dataset, with monthly observations (`frequency = 12`), and chose the second example time series.

### Time Points and Periods

After loading the time series data, it's important to inspect its structure. For example, we can extract the time points and periods (months) in the dataset.

```r
time_points <- time(ts)
time_points
```

```r
periods = cycle(ts)
periods
```

The `time()` function gives us the specific time points for each observation, while `cycle()` helps us identify the period (in this case, the month) within the series.

### Extracting Years and Attributes

Understanding the temporal structure of the time series is essential. We can extract the year information and other attributes related to the time series.

```r
years <- floor(time_points)
years
```

```r
attributes = attributes(ts)
attributes
```

Here, the `floor()` function extracts the integer part of the time points, essentially identifying the year, while `attributes()` provides metadata about the time series, such as the description, start date, and frequency.

### Plotting the Time Series

Visualization is key to understanding time series data. The following code plots the time series with a descriptive title:

```r
plot(ts, main = attributes$description)
```

This plot provides a visual representation of the data, making it easier to spot trends, seasonal patterns, and anomalies.

## Basic Time Series Operations

### Saving Data

You might want to save the time series data to a file for further analysis. Here's how to write it to a CSV file:

```r
write.csv(ts, "data.csv", row.names = FALSE)
```

### Time Series Summary

To understand the general properties of the time series, you can use the `summary()` function. This gives you a summary of the data, including basic statistics.

```r
summary(ts)
```

Additionally, functions like `start()`, `end()`, and `frequency()` provide details on the start and end points, as well as the frequency of the data.

```r
start(ts); end(ts); frequency(ts)
```

### Aggregation and Boxplots

Aggregating the data is useful when we want to analyze the data at a different frequency (e.g., yearly instead of monthly). We can aggregate the data and visualize it.

```r
ts_aggregated <- aggregate(ts)
plot(ts_aggregated)
```

Boxplots are another great way to understand the distribution and variability of data over time. Here, we create boxplots grouped by the cycle (month) and by the year.

```r
boxplot(ts ~ cycle(ts))
boxplot(ts ~ floor(time(ts)))
```

These boxplots allow us to compare data across different months or years, helping identify seasonal variations and trends.

## Conclusion

In this blog post, we explored the basics of time series analysis in R using the `tsdl` package. We walked through how to subset a dataset, extract time points and periods, plot the data, and perform basic operations like aggregation and boxplots. Time series analysis is a powerful tool for uncovering patterns in data, and R provides a rich set of functions to help make this process easier.

By following the steps outlined in this example, you can begin analyzing time series data in your own projects, whether you're studying agriculture, economics, or any other field that involves temporal data.