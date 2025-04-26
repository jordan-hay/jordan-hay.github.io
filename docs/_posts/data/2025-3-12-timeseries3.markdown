---
layout: post
title:  "Chapter 1 Practice: Introductory Time Series with R by Cowpertwait and Metcalfe"
date:   2025-3-12 07:25:17 -0800
categories: jekyll update data
---


<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Chap_1_Practice_Introductory_Time_Series_with_R_by_Cowpertwait_and_Metcalfe.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

# Introduction

In this blog, we explore the first chapter of <a href="https://link.springer.com/book/10.1007/978-0-387-88698-5" target="_blank">"Introductory Time Series with R" by Cowpertwait and Metcalfe</a>. This chapter serves as an introduction to basic time series analysis concepts and demonstrates how to work with time series data in R. We will cover several <a href="https://github.com/dallascard/Introductory_Time_Series_with_R_datasets" target="_blank">datasets</a> and apply various techniques such as plotting, decomposition, and analysis of seasonality and trends.

## Air Passengers Data

We start by working with the `AirPassengers` dataset, which represents the number of air passengers (in thousands) from 1949 to 1960. This dataset is built into R, making it an excellent starting point for learning about time series.

```r
data(AirPassengers)
AP <- AirPassengers
AP
```

### Class and Summary of Air Passengers

To understand the dataset, we begin by checking its class and obtaining a summary.

```r
class(AP)
summary(AP)
```

We also examine the start, end, and frequency of the time series:

```r
start(AP); end(AP); frequency(AP)
```

### Plotting the Air Passengers Data

We then plot the data to visualize the number of passengers over time:

```r
plot(AP, ylab = "Passengers (1000's)")
```

### Aggregating and Boxplot of Air Passengers

Next, we aggregate the data and visualize it using a boxplot to examine the seasonal effects.

```r
aggregate(AP)
plot(aggregate(ts))
boxplot(AP ~ cycle(AP))
```

### Cycle and Time Points

We also extract the cycle (seasonality) and display it alongside the time points:

```r
cycle(AP)
data.frame(AP = AP, cycle = cycle(AP))
```

### Layout for Multiple Plots

Using `layout()`, we display two plots side-by-side: the aggregated data and a boxplot of the time series grouped by the cycle.

```r
layout(matrix(1:2, nrow = 1))
plot(aggregate(AP))
boxplot(AP ~ cycle(AP))
```

## Maine Unemployment Data

Next, we load the Maine unemployment data, which records the unemployment rate in Maine from 1996 to the present.

```r
www <- "https://raw.githubusercontent.com/dallascard/Introductory_Time_Series_with_R_datasets/refs/heads/master/Maine.dat"
Maine.month <- read.table(www, header = TRUE)
attach(Maine.month)
class(Maine.month)
Maine.month
```

We convert the data to a time series object, `Maine.month.ts`, and then aggregate it annually:

```r
Maine.month.ts <- ts(unemploy, start = c(1996, 1), freq = 12)
Maine.month.ts
Maine.annual.ts <- aggregate(Maine.month.ts)/12
Maine.annual.ts
```

### Plotting the Unemployment Data

We plot both the monthly and annual unemployment rates:

```r
layout(matrix(1:2, nrow = 1))
plot(Maine.month.ts, ylab = "Unemployed (%)")
plot(Maine.annual.ts, ylab = "Unemployed (%)")
```

### Comparing Unemployment Rates in February and August

We compare the unemployment rates in February and August relative to the overall average:

```r
Maine.Feb <- window(Maine.month.ts, start = c(1996,2), freq = TRUE)
Maine.Aug <- window(Maine.month.ts, start = c(1996,8), freq = TRUE)
Feb.ratio <- mean(Maine.Feb) / mean(Maine.month.ts)
Aug.ratio <- mean(Maine.Aug) / mean(Maine.month.ts)
print(Feb.ratio)
print(Aug.ratio)
```

## US Unemployment Data

The next dataset we analyze is the US unemployment data, covering monthly unemployment rates from 1996 to 2006.

```r
www <- "https://raw.githubusercontent.com/dallascard/Introductory_Time_Series_with_R_datasets/refs/heads/master/USunemp.dat"
US.month <- read.table(www, header = TRUE)
attach(US.month)
head(US.month)
USun
US.month.ts <- ts(USun, start=c(1996,1), end=c(2006,10), freq = 12)
plot(US.month.ts, ylab = "Unemployed (%)")
```

## Electricity, Beer, and Chocolate Production

We examine another dataset covering electricity production, beer consumption, and chocolate production from 1958 to 1990.

```r
www <- "https://raw.githubusercontent.com/dallascard/Introductory_Time_Series_with_R_datasets/refs/heads/master/cbe.dat"
CBE <- read.table(www, header = TRUE)
Elec.ts <- ts(CBE[, 3], start = 1958, freq = 12)
Beer.ts <- ts(CBE[, 2], start = 1958, freq = 12)
Choc.ts <- ts(CBE[, 1], start = 1958, freq = 12)
plot(cbind(Elec.ts, Beer.ts, Choc.ts), main = "Chocolate, Beer, and Electricity Production: 1958-1990")
```

### Correlation Between Air Passengers and Electricity

We investigate the correlation between the air passengers dataset and electricity production:

```r
AP.elec <- ts.intersect(AP, Elec.ts)
start(AP.elec)
end(AP.elec)
AP.elec[1:3, ]
AP <- AP.elec[,1]; Elec <- AP.elec[,2]
layout(1:2)
plot(AP, main = "", ylab = "Air passengers / 1000's")
plot(Elec, main = "", ylab = "Electricity production / MkWh")
plot(as.vector(AP), as.vector(Elec), xlab = "Air passengers / 1000's", ylab = "Electricity production / MWh")
abline(reg = lm(Elec ~ AP))
cor(AP, Elec)
```

## Exchange Rate Data

Next, we analyze quarterly exchange rate data for the New Zealand Dollar (NZD) to the British Pound from 1991 to 1998.

```r
www <- "https://raw.githubusercontent.com/dallascard/Introductory_Time_Series_with_R_datasets/refs/heads/master/pounds_nz.dat"
Z <- read.table(www, header = TRUE)
Z.ts <- ts(Z, start = 1991, freq = 4)
plot(Z.ts, xlab = "Time / years", ylab = "Quarterly exchange rate in $NZ / pound")
```

### Exchange Rate from 1992 to 1996 and 1996 to 1998

We plot exchange rates for two distinct periods:

```r
Z.92.96 <- window(Z.ts, start = c(1992, 1), end = c(1996, 1))
Z.96.98 <- window(Z.ts, start = c(1996, 1), end = c(1998, 1))
layout(matrix(1:2, nrow = 1))
plot(Z.92.96, ylab = "Exchange rate in $NZ/pound", xlab = "Time (years)")
plot(Z.96.98, ylab = "Exchange rate in $NZ/pound", xlab = "Time (years)")
print("Figure 1.9: Exchange Rates (1992–1998)")
```

## Global Temperature Data

Lastly, we analyze global temperature data from 1856 to 2005. The data is aggregated to yearly averages and plotted.

```r
www <- "https://raw.githubusercontent.com/dallascard/Introductory_Time_Series_with_R_datasets/refs/heads/master/global.dat"
Global <- scan(www)
Global.ts <- ts(Global, start = c(1856, 1), end = c(2005, 12), frequency = 12)
Global.annual <- aggregate(Global.ts, FUN = mean)
plot(Global.ts)
plot(Global.annual)
```

### Linear Trend in Global Temperature

We extract a portion of the data from 1970 to 2005 and fit a linear regression line to examine the trend:

```r
New.series <- window(Global.ts, start = c(1970, 1), end = c(2005, 12))
New.time <- time(New.series)
plot(New.series)
abline(lm(New.series ~ New.time), col = "red")
model <- lm(New.series ~ New.time)
coef(model)
```

## Decomposition of Time Series

Finally, we perform a multiplicative decomposition on the electricity production data to separate the trend and seasonal components.

```r
plot(decompose(Elec.ts))
Elec.decom <- decompose(Elec.ts, type = "multiplicative")
plot(Elec.decom)
Trend <- Elec.decom$trend
Seasonal <- Elec.decom$seasonal
Trend <- na.omit(Trend)
ts.plot(cbind(Trend, Trend * Seasonal), lty = 1:2, col = c("blue", "red"))
```

## Conclusion

Chapter 1 of *Introductory Time Series with R* introduces essential concepts and techniques for working with time series data in R. Through hands-on examples, we explored various datasets, performed basic analyses, and visualized trends and seasonal patterns. As we progress in the book, we will continue building on these foundations to tackle more complex time series analysis tasks.