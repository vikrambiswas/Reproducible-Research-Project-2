# Reproducible-Research-Project-2
## Loading and preprocessing the data
Unzip data to obtain a csv file.

```
library("data.table")

fileUrl <- "https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip"
download.file(fileUrl, destfile = paste0(getwd(), '/repdata%2Fdata%2Factivity.zip'), method = "curl")
unzip("repdata%2Fdata%2Factivity.zip",exdir = "data")
```

## Reading csv Data into Data.Table.
```
activityDT <- data.table::fread(input = "data/activity.csv")
```
## What is mean total number of steps taken per day?

Calculate the total number of steps taken per day
```
Total_Steps <- activityDT[, c(lapply(.SD, sum, na.rm = TRUE)), .SDcols = c("steps"), by = .(date)] 

head(Total_Steps, 10)

#          date steps
# 1: 2012-10-01     0
# 2: 2012-10-02   126
# 3: 2012-10-03 11352
# 4: 2012-10-04 12116
# 5: 2012-10-05 13294
# 6: 2012-10-06 15420
# 7: 2012-10-07 11015
# 8: 2012-10-08     0
# 9: 2012-10-09 12811
# 10: 2012-10-10  990
```
