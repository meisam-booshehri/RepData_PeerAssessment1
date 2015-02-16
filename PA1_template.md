---
title: "Peer Assignment 1 for the course reproducible research"
output: html_document
---

This is an R Markdown document created by Meisam Booshehri for the peer assignment 1 for the course "reproducible research".

###Loading and preprocessing the data
in this section the dataset is loaded to R by using the following R code:


```r
dt<-read.csv("activity.csv")
head(dt)
```

```
##   steps       date interval
## 1    NA 2012-10-01        0
## 2    NA 2012-10-01        5
## 3    NA 2012-10-01       10
## 4    NA 2012-10-01       15
## 5    NA 2012-10-01       20
## 6    NA 2012-10-01       25
```


###What is mean total number of steps taken per day?
In this section we will ignore the missing values in the dataset.

1. Calculate the total number of steps taken per day

```r
good<- complete.cases(dt)
newdt<-dt[good,]
df<-aggregate(steps ~ date, data = newdt, sum)
colnames(df)<-c("Date","total_number_of_steps")
df
```

```
##          Date total_number_of_steps
## 1  2012-10-02                   126
## 2  2012-10-03                 11352
## 3  2012-10-04                 12116
## 4  2012-10-05                 13294
## 5  2012-10-06                 15420
## 6  2012-10-07                 11015
## 7  2012-10-09                 12811
## 8  2012-10-10                  9900
## 9  2012-10-11                 10304
## 10 2012-10-12                 17382
## 11 2012-10-13                 12426
## 12 2012-10-14                 15098
## 13 2012-10-15                 10139
## 14 2012-10-16                 15084
## 15 2012-10-17                 13452
## 16 2012-10-18                 10056
## 17 2012-10-19                 11829
## 18 2012-10-20                 10395
## 19 2012-10-21                  8821
## 20 2012-10-22                 13460
## 21 2012-10-23                  8918
## 22 2012-10-24                  8355
## 23 2012-10-25                  2492
## 24 2012-10-26                  6778
## 25 2012-10-27                 10119
## 26 2012-10-28                 11458
## 27 2012-10-29                  5018
## 28 2012-10-30                  9819
## 29 2012-10-31                 15414
## 30 2012-11-02                 10600
## 31 2012-11-03                 10571
## 32 2012-11-05                 10439
## 33 2012-11-06                  8334
## 34 2012-11-07                 12883
## 35 2012-11-08                  3219
## 36 2012-11-11                 12608
## 37 2012-11-12                 10765
## 38 2012-11-13                  7336
## 39 2012-11-15                    41
## 40 2012-11-16                  5441
## 41 2012-11-17                 14339
## 42 2012-11-18                 15110
## 43 2012-11-19                  8841
## 44 2012-11-20                  4472
## 45 2012-11-21                 12787
## 46 2012-11-22                 20427
## 47 2012-11-23                 21194
## 48 2012-11-24                 14478
## 49 2012-11-25                 11834
## 50 2012-11-26                 11162
## 51 2012-11-27                 13646
## 52 2012-11-28                 10183
## 53 2012-11-29                  7047
```

2. Here is a histrogram of the total numebr of steps taken per day

```r
hist(df$total_number_of_steps,main="Total number of steps taken per day",breaks=100)
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) 


3. Calculate and report the mean and the median of the number of steps taken per day


```r
meanTable<-aggregate(steps ~ date, data = newdt, mean)
colnames(meanTable)<-c("date","averageSteps")
meanTable
```

```
##          date averageSteps
## 1  2012-10-02    0.4375000
## 2  2012-10-03   39.4166667
## 3  2012-10-04   42.0694444
## 4  2012-10-05   46.1597222
## 5  2012-10-06   53.5416667
## 6  2012-10-07   38.2465278
## 7  2012-10-09   44.4826389
## 8  2012-10-10   34.3750000
## 9  2012-10-11   35.7777778
## 10 2012-10-12   60.3541667
## 11 2012-10-13   43.1458333
## 12 2012-10-14   52.4236111
## 13 2012-10-15   35.2048611
## 14 2012-10-16   52.3750000
## 15 2012-10-17   46.7083333
## 16 2012-10-18   34.9166667
## 17 2012-10-19   41.0729167
## 18 2012-10-20   36.0937500
## 19 2012-10-21   30.6284722
## 20 2012-10-22   46.7361111
## 21 2012-10-23   30.9652778
## 22 2012-10-24   29.0104167
## 23 2012-10-25    8.6527778
## 24 2012-10-26   23.5347222
## 25 2012-10-27   35.1354167
## 26 2012-10-28   39.7847222
## 27 2012-10-29   17.4236111
## 28 2012-10-30   34.0937500
## 29 2012-10-31   53.5208333
## 30 2012-11-02   36.8055556
## 31 2012-11-03   36.7048611
## 32 2012-11-05   36.2465278
## 33 2012-11-06   28.9375000
## 34 2012-11-07   44.7326389
## 35 2012-11-08   11.1770833
## 36 2012-11-11   43.7777778
## 37 2012-11-12   37.3784722
## 38 2012-11-13   25.4722222
## 39 2012-11-15    0.1423611
## 40 2012-11-16   18.8923611
## 41 2012-11-17   49.7881944
## 42 2012-11-18   52.4652778
## 43 2012-11-19   30.6979167
## 44 2012-11-20   15.5277778
## 45 2012-11-21   44.3993056
## 46 2012-11-22   70.9270833
## 47 2012-11-23   73.5902778
## 48 2012-11-24   50.2708333
## 49 2012-11-25   41.0902778
## 50 2012-11-26   38.7569444
## 51 2012-11-27   47.3819444
## 52 2012-11-28   35.3576389
## 53 2012-11-29   24.4687500
```

```r
aggregate(steps ~ date, data = newdt, median,na.rm=TRUE)
```

```
##          date steps
## 1  2012-10-02     0
## 2  2012-10-03     0
## 3  2012-10-04     0
## 4  2012-10-05     0
## 5  2012-10-06     0
## 6  2012-10-07     0
## 7  2012-10-09     0
## 8  2012-10-10     0
## 9  2012-10-11     0
## 10 2012-10-12     0
## 11 2012-10-13     0
## 12 2012-10-14     0
## 13 2012-10-15     0
## 14 2012-10-16     0
## 15 2012-10-17     0
## 16 2012-10-18     0
## 17 2012-10-19     0
## 18 2012-10-20     0
## 19 2012-10-21     0
## 20 2012-10-22     0
## 21 2012-10-23     0
## 22 2012-10-24     0
## 23 2012-10-25     0
## 24 2012-10-26     0
## 25 2012-10-27     0
## 26 2012-10-28     0
## 27 2012-10-29     0
## 28 2012-10-30     0
## 29 2012-10-31     0
## 30 2012-11-02     0
## 31 2012-11-03     0
## 32 2012-11-05     0
## 33 2012-11-06     0
## 34 2012-11-07     0
## 35 2012-11-08     0
## 36 2012-11-11     0
## 37 2012-11-12     0
## 38 2012-11-13     0
## 39 2012-11-15     0
## 40 2012-11-16     0
## 41 2012-11-17     0
## 42 2012-11-18     0
## 43 2012-11-19     0
## 44 2012-11-20     0
## 45 2012-11-21     0
## 46 2012-11-22     0
## 47 2012-11-23     0
## 48 2012-11-24     0
## 49 2012-11-25     0
## 50 2012-11-26     0
## 51 2012-11-27     0
## 52 2012-11-28     0
## 53 2012-11-29     0
```

###What is the average daily pattern?

1. In this section a time series plot of the 5-minute interval and the average number of steps taken is shown.


```r
newdf<-aggregate(steps ~ interval, data = newdt, mean)
colnames(newdf)<-c("interval","averageSteps")
X1<-newdf$interval
X2<-newdf$averageSteps
plot(X1,X2, type='l', xlab="intervals", ylab="average of steps across all days")
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5-1.png) 

```r
head(newdf)
```

```
##   interval averageSteps
## 1        0    1.7169811
## 2        5    0.3396226
## 3       10    0.1320755
## 4       15    0.1509434
## 5       20    0.0754717
## 6       25    2.0943396
```

2. The following 5-minute interval contains the maximum number of steps according to the daily pattern:

```r
newdf[newdf$averageSteps==max(newdf$averageSteps),]
```

```
##     interval averageSteps
## 104      835     206.1698
```


###Imputing missing Values
1. The number of missing values are as follows:

```r
sapply(dt, function(x) sum(is.na(x)))
```

```
##    steps     date interval 
##     2304        0        0
```

2.Our strategy for filling in all the missing values in the dataset is to make use of the mean of steps in the intervals across all the days as computed above.Please see below. dt2 is the new data set with the missing values filled in by the average number of steps taken per interval, averaged across all days.


```r
bad<-is.na(dt$steps)
dt2<-dt

for(i in 1:nrow(dt2[bad,])){
  Temp<-subset(newdf, interval==dt2[bad,][i,"interval"], select = c(interval,averageSteps))
  dt2[bad,][i,"steps"]=Temp[1,"averageSteps"]
}
```

3. For the new imputed dataset a histogram has been shown below. Thererafter you can see a report on the new mean and median.

```r
df2<-aggregate(steps ~ date, data = dt2, sum)
colnames(df2)<-c("Date","total_number_of_steps")

hist(df2$total_number_of_steps,col="red",xlab="total number of steps",main="Total number of steps taken per day",breaks=100)
```

![plot of chunk unnamed-chunk-9](figure/unnamed-chunk-9-1.png) 

```r
meanTable2<-aggregate(steps ~ date, data = dt2, mean)
colnames(meanTable2)<-c("date","averageSteps")
meanTable2
```

```
##          date averageSteps
## 1  2012-10-01   37.3825996
## 2  2012-10-02    0.4375000
## 3  2012-10-03   39.4166667
## 4  2012-10-04   42.0694444
## 5  2012-10-05   46.1597222
## 6  2012-10-06   53.5416667
## 7  2012-10-07   38.2465278
## 8  2012-10-08   37.3825996
## 9  2012-10-09   44.4826389
## 10 2012-10-10   34.3750000
## 11 2012-10-11   35.7777778
## 12 2012-10-12   60.3541667
## 13 2012-10-13   43.1458333
## 14 2012-10-14   52.4236111
## 15 2012-10-15   35.2048611
## 16 2012-10-16   52.3750000
## 17 2012-10-17   46.7083333
## 18 2012-10-18   34.9166667
## 19 2012-10-19   41.0729167
## 20 2012-10-20   36.0937500
## 21 2012-10-21   30.6284722
## 22 2012-10-22   46.7361111
## 23 2012-10-23   30.9652778
## 24 2012-10-24   29.0104167
## 25 2012-10-25    8.6527778
## 26 2012-10-26   23.5347222
## 27 2012-10-27   35.1354167
## 28 2012-10-28   39.7847222
## 29 2012-10-29   17.4236111
## 30 2012-10-30   34.0937500
## 31 2012-10-31   53.5208333
## 32 2012-11-01   37.3825996
## 33 2012-11-02   36.8055556
## 34 2012-11-03   36.7048611
## 35 2012-11-04   37.3825996
## 36 2012-11-05   36.2465278
## 37 2012-11-06   28.9375000
## 38 2012-11-07   44.7326389
## 39 2012-11-08   11.1770833
## 40 2012-11-09   37.3825996
## 41 2012-11-10   37.3825996
## 42 2012-11-11   43.7777778
## 43 2012-11-12   37.3784722
## 44 2012-11-13   25.4722222
## 45 2012-11-14   37.3825996
## 46 2012-11-15    0.1423611
## 47 2012-11-16   18.8923611
## 48 2012-11-17   49.7881944
## 49 2012-11-18   52.4652778
## 50 2012-11-19   30.6979167
## 51 2012-11-20   15.5277778
## 52 2012-11-21   44.3993056
## 53 2012-11-22   70.9270833
## 54 2012-11-23   73.5902778
## 55 2012-11-24   50.2708333
## 56 2012-11-25   41.0902778
## 57 2012-11-26   38.7569444
## 58 2012-11-27   47.3819444
## 59 2012-11-28   35.3576389
## 60 2012-11-29   24.4687500
## 61 2012-11-30   37.3825996
```

```r
medianTable2<-aggregate(steps ~ date, data = dt2, median)
colnames(medianTable2)<-c("date","averageSteps")
medianTable2
```

```
##          date averageSteps
## 1  2012-10-01     34.11321
## 2  2012-10-02      0.00000
## 3  2012-10-03      0.00000
## 4  2012-10-04      0.00000
## 5  2012-10-05      0.00000
## 6  2012-10-06      0.00000
## 7  2012-10-07      0.00000
## 8  2012-10-08     34.11321
## 9  2012-10-09      0.00000
## 10 2012-10-10      0.00000
## 11 2012-10-11      0.00000
## 12 2012-10-12      0.00000
## 13 2012-10-13      0.00000
## 14 2012-10-14      0.00000
## 15 2012-10-15      0.00000
## 16 2012-10-16      0.00000
## 17 2012-10-17      0.00000
## 18 2012-10-18      0.00000
## 19 2012-10-19      0.00000
## 20 2012-10-20      0.00000
## 21 2012-10-21      0.00000
## 22 2012-10-22      0.00000
## 23 2012-10-23      0.00000
## 24 2012-10-24      0.00000
## 25 2012-10-25      0.00000
## 26 2012-10-26      0.00000
## 27 2012-10-27      0.00000
## 28 2012-10-28      0.00000
## 29 2012-10-29      0.00000
## 30 2012-10-30      0.00000
## 31 2012-10-31      0.00000
## 32 2012-11-01     34.11321
## 33 2012-11-02      0.00000
## 34 2012-11-03      0.00000
## 35 2012-11-04     34.11321
## 36 2012-11-05      0.00000
## 37 2012-11-06      0.00000
## 38 2012-11-07      0.00000
## 39 2012-11-08      0.00000
## 40 2012-11-09     34.11321
## 41 2012-11-10     34.11321
## 42 2012-11-11      0.00000
## 43 2012-11-12      0.00000
## 44 2012-11-13      0.00000
## 45 2012-11-14     34.11321
## 46 2012-11-15      0.00000
## 47 2012-11-16      0.00000
## 48 2012-11-17      0.00000
## 49 2012-11-18      0.00000
## 50 2012-11-19      0.00000
## 51 2012-11-20      0.00000
## 52 2012-11-21      0.00000
## 53 2012-11-22      0.00000
## 54 2012-11-23      0.00000
## 55 2012-11-24      0.00000
## 56 2012-11-25      0.00000
## 57 2012-11-26      0.00000
## 58 2012-11-27      0.00000
## 59 2012-11-28      0.00000
## 60 2012-11-29      0.00000
## 61 2012-11-30     34.11321
```

###Are there differences in activity patterns between weekdays and weekends?

1. Below, you can see the analysis to show the difference between the activity patterns in the weekends and weekdays.


```r
Sys.setlocale("LC_TIME", "English")
```

```
## [1] "English_United States.1252"
```

```r
levels=factor(ifelse(weekdays(as.Date(newdt$date))== "Saturday" |weekdays(as.Date(newdt$date))== "Sunday", "weekend", "weekday"),levels=c("weekday","weekend"))

newdt2<-cbind(newdt,levels)
colnames(newdt2)<-c("steps","date","interval","levels")


newdf2<-aggregate(steps~interval, data = subset(newdt2, levels=="weekday",select=c(steps,interval)), mean)

colnames(newdf2)<-c("interval","averageSteps")
X1<-newdf2$interval
X2<-newdf2$averageSteps
par(mfcol=c(1,2))

plot(X1,X2, type='l', col="blue",xlab="intervals", ylab="average of steps across all days", main="Weekdays")




newdf3<-aggregate(steps~interval, data = subset(newdt2, levels=="weekend",select=c(steps,interval)), mean)
X3<-newdf3$interval
X4<-newdf3$averageSteps
plot(X3,X4, type='l', col="blue",xlab="intervals", ylab="average of steps across all days", main="Weekends")
```

![plot of chunk unnamed-chunk-10](figure/unnamed-chunk-10-1.png) 
