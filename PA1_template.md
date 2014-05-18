# Reproducible Research: Peer Assessment 1

## Loading and preprocessing the data

'''{r read_data, echo=TRUE}
library(ggplot2)
#Loading Data
data <- read.csv("activity.csv", header = T, colClasses = c("numeric", "character", "numeric"))
data$interval <- factor(data$interval)
data$date <- as.Date(data$date, format="%Y-%m-%d")
data_cleaned <- data[which(data$steps != "NA"), ]
'''
'''{r}
library(plyr)
total_by_day <- ddply(data_cleaned, .(date), summarise, steps=sum(steps))
hist(total_by_day$steps, main="Number of Steps", xlab="Total number of steps taken each day", col="light blue")

# mean and median total number of steps taken per day
mean(total_by_day$steps)
median(total_by_day$steps)
'''
## What is mean total number of steps taken per day?
