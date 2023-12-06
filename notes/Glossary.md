---
id: v4t96j5kch5mq12272qsyih
title: Glossary
desc: ''
updated: 1700240957152
created: 1700240802023
---
### **Point outlier:**

- A point outlier is a datum that behaves unusual in a specific time instant when compared either to the other values in the time series (global outlier) or to its neighboring points (local outlier).[1]

### **Subsequences:**

- This term refers to consecutive points in time whose joint behavior is unusual, although each observation individually is not necessarily a point outlier.[1]

[1]:<https://s-ai-f.github.io/Time-Series/outlier-detection-in-time-series.html>

### **Outlier Estimation and methods:**

- If the outlier is obtained based on the past,current and future data then it is called the estimation method. If the outlier is obtained based on only past data then the method is prediction method.
  
- Some methods:
    1. Descriptive statistics :
        - **_Finding maximum and minimum_** in the data - for example if the the data is regarding grades of the students and the maximum possible value is 100 but due to mistake if the data has 1000 as maximum value this can be found by retrieveing the range of the data.
        - **_Histogram_** , **_Boxplots_** of the data can be used to visualise the outlier. In Boxplots all the observations beyond the interquartile range criterion($I=[q_{0.25}-1.5.IQR;q_{0.75}+1.5.IQR]$) is considered as outlier.
        - **_Percentiles_** All the observations that are beyond a percentile of interes is considered as outlier.
        - **_Z-Scores_** if the data has a normal distribution. Data are categorised as outliers based on their z-score
        - **_
    2. Statistical tests : These tests requires the data is normally distributed. This can be checked by either visualsing the data using a histogram or using shapiro-Wilk normality test - shapiro.text().
        - Grubb's test: The Grubbs test allows to detect whether the highest or lowest value in a dataset is an outlier.
        - Dixon's test : Tests if a particular value is outlier or not
        - Rosner's test: used to detect several outliers as once.