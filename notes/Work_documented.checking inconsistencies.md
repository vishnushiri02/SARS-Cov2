---
id: o7n9flqgbqf3xbm437bc0ih
title: checking inconsistencies
desc: 'What was done to know about the inconsistencies'
updated: 1702042333839
created: 1702040914123
---

- It was seen that the numbers in the ```Work/Data_Analysis/chosen_ten_country_submission.csv``` do not match to the number of downloaded entries. 
- The number of downloaded entries are always higher than the numbers in the file.
- Month wise counts were calculated from the downloaded entries using the group_by function
  
```r
month_numbers<-list()
for(i in names(ten_country_mut_data)){
  month_numbers[[i]]<-data.frame(ten_country_mut_data[[i]] %>% \
  group_by(format(Collected_date,"%Y-%m")) %>% count())
  colnames(month_numbers[[i]])<-c("Month","number")
}
```

- The result of the above code was manually compared with the numbers in the file. Months where the deviation occured were noted.

- GISAID was again queried for number of entries for one of the months for which the values deviated in South_korea data (OCT23).
- The result of the query neighter matched with the number in the file or with the number got from the snippet. It was higher than both.
- This it when I realised that entries from older months are uploaded to GISAID anytime. This can be seen through the submission date column in GISAID - Entries with old collection date and recent submission date.
- So the difference between the numbers in the file and the numbers from downloaded entries could be reasoned out to be the data submitted during the time gaap between compiling the csv file and downloading the data (nearly 1 week).

