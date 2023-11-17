---
id: r423m96u71ix4pb458fk8u2
title: Work_documented
desc: 'This is file contains all the steps done for the master thesis'
updated: 1700245382944
created: 1700240700998
---
# Data acquisition

- From the GISAID, the total number of **_high_**, **_coverge_** completed sequence deposited by each country (200+) in the past 22 months(Jan2022-Oct2023) were retrieved in a month wise fasion using the R Package GISAIDR.
- Countries that had more than 10,000 sequences deposited in total in the past 22 months were alone considered further. 
- This included 10 countries : India, South Korea, Denmark, Germany, Norway, Spain, United Kingdom, Canada, USA, Australia
- The trend of the time series data of these countries were plotted.
  ![Trends in 10 countries](assets/plots/Country_trend_plots.png)
- Outlier detection and pruning of the observation horizon(Time period considered): Extreme low values were searched for, using the MAD(Hampel filter) (one of the [[Outlier Estimation and methods|Glossary#outlier-estimation-and-methods]]). Since there were no extreme low values found in any of the countries, the observation time period was not pruned.
- The sequence data for 10 countries were downloaded. There are files with crude data - all data retrieved from GISAID for each of the accesssion ID (29 cols of data) and there are files with essential columns: strain,virus,collection_date,country,pangolineage,sequence, length of the sequence, GISAID accession_id.
- Fusing Lineages: To fuse lineages with their parent lineages mutation data is required. This is again downloaded from the GISAID using the self-modified GISAIDR Download function.

[Definition Reference](https://www.cdc.gov/coronavirus/2019-ncov/variants/variant-classifications.html)

