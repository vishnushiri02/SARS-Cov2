---
id: r423m96u71ix4pb458fk8u2
title: Work_documented
desc: 'This is file contains all the steps done for the master thesis'
updated: 1701796500850
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
- Mapping Lineages: To map lineages to their parent lineages, mutation data is required. This is again downloaded from the GISAID using the self-modified GISAIDR Download function ```Work/Data_Analysis/Modified_GISAIDRdownload.R```
- The data is stored into 10 files by the country. From these 10 files the columns corresponding to the mutations and pango lineage was extracted and stored in a different file ```Work/Data_Analysis/ten_country_mut_data/ten_country_lineage_mut.csv```.
This is done using awk command:
```bash{cmd}
awk -F";" '{gsub(/[()]/,"",$6);print $5";"$6}' ten_country_mut_data/* >ten_country_mut_data/ten_country_lineage_mut.csv
```
>gsub is used to remove the brackets in the AA_mutations column

>Note: Columns of the CSV files are separated by a semicolon ';'

# Mapping lineages:

- All the mutations pertaining to each of the lineage was combined.
- From this only the spike mutations were considered for the downstream work.
- Jaccard index (intersections of sets/Union of sets). If the Jaccard index is more than 0.5 then the lineages being compared are either considered as parental or neighbour depending on their pangolineage string.
- For Pangolineages that are considered as VOI/VUM/VOC, the  mapping is directly given in GISAID. This can be found in the file ```Work/Data_Analysis/GISAID_VOI_VOC_VOM_list.txt```. This was obtained by first downloading the Clade/Lineage
- The Lineages were mapped to parental lineage based on the the calculated jaaccard index which is based on the number of common spike mutations between pangolineages that have same names dropping the last character. VOC/VUM/VOI were explicitely mapped based on the list taken from GISAID.
- After mapping, for each country the frequency of presernce of each lineage in a month is calculated (count of lineage B in jul/total entries in jul) and plotted. To make it more convenient plots for each lineage grouped by country was plotted to do the analysis. 
- These plots are analysed to bring out the difference in the lineage trend among countries. An entire spreedsheet was developed manually basically describing the variant trends in words.

[Definition Reference](https://www.cdc.gov/coronavirus/2019-ncov/variants/variant-classifications.html)

