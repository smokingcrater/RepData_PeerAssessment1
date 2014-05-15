# Reproducible Research: Peer Assessment 1



## Loading and preprocessing the data

__Show any code that is needed to__

* __Load the data (i.e. read.csv())__


```r
df_activity_raw <- read.csv("activity.csv")
```


* __Process/transform the data (if necessary) into a format suitable for your analysis__


```r
df_activity_raw[, 2] <- as.Date(df_activity_raw[, 2], format = "%Y-%m-%d")
```


## What is mean total number of steps taken per day?

__For this part of the assignment, you can ignore the missing values in the dataset.__

* __Make a histogram of the total number of steps taken each day__


```r
df_part1 <- aggregate(steps ~ date, data = df_activity_raw, FUN = sum)
hist(df_part1[, 2], main = "Total Number of Steps Taken Each Day", xlab = "Steps", 
    col = "red")
rug(df_part1[, 2])
```

![plot of chunk plot_steps_per_day](figure/plot_steps_per_day.png) 


* __Calculate and report the mean and median total number of steps taken per day__


```r
steps_mean <- mean(df_part1[, 2])
steps_mean
```

```
## [1] 10766
```

```r
steps_median <- median(df_part1[, 2])
steps_median
```

```
## [1] 10765
```


The mean is 10766.19.  
The median is 10765.00.

## What is the average daily activity pattern?

* __Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)__

* __Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?__

## Imputing missing values

__Note that there are a number of days/intervals where there are missing values (coded as NA). The presence of missing days may introduce bias into some calculations or summaries of the data.__

* __Calculate and report the total number of missing values in the dataset (i.e. the total number of rows with NAs)__

* __Devise a strategy for filling in all of the missing values in the dataset. The strategy does not need to be sophisticated. For example, you could use the mean/median for that day, or the mean for that 5-minute interval, etc.__

* __Create a new dataset that is equal to the original dataset but with the missing data filled in.__

* __Make a histogram of the total number of steps taken each day and Calculate and report the mean and median total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?__

## Are there differences in activity patterns between weekdays and weekends?

__For this part the weekdays() function may be of some help here. Use the dataset with the filled-in missing values for this part.__

* __Create a new factor variable in the dataset with two levels – “weekday” and “weekend” indicating whether a given date is a weekday or weekend day.__

* __Make a panel plot containing a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis).__
