
### Activity Monitoring Analysis

#### Read Data
```{r}
   setwd("~/Data Science Specialization/Reproducible Research/ProgrammingAssignment1")
   activity_data <- read.csv("activity.csv",sep=",")
```

### 1) What is mean total number of steps taken per day?

```{r} 
 
  totsteps <- aggregate(steps ~ date,activity_data,sum)

```
#### Show two copies of plot indicating mean and median respectively 

```{r} 
 par(mfrow=c(2,1))

 hist(totsteps[,2], xlab="total steps taken per day", ylab="Frequency", breaks = 20, freq = TRUE, main="Total Steps per Day (Frequency)")
 abline(v=mean(totsteps[,2],na.rm=FALSE),col=4,lty=1,par(lwd=2))
 text( mean(totsteps[,2],na.rm=FALSE) + 1700,9,paste("---mean(",sprintf("%.2f",mean(totsteps[,2],na.rm=FALSE)),")"),col=4)

 hist(totsteps[,2], xlab="total steps taken per day", ylab="Frequency", breaks = 20, freq = TRUE, main="Total Steps per Day (Frequency)")
 abline(v=median(totsteps[,2],na.rm=FALSE),col=2,lty=1,par(lwd=2))
 text( median(totsteps[,2],na.rm=FALSE) + 2000,9,paste("---median(",median(totsteps[,2],na.rm=FALSE),")"),col=2)

```
#### 2) What is the average Daily Activity Pattern?
```{r}
activity_data <- read.csv("activity.csv",sep=",")
 
totStepsPerInterval <- aggregate(steps ~ interval,activity_data,mean)

maxInterval <- subset(totStepsPerInterval,steps == max(steps))


```

```{r}

par(mfrow=c(1,1))

plot(totStepsPerInterval$interval, totStepsPerInterval$steps,type="s",lab=c(24,5,3))
abline(v=maxInterval$interval,col=3,lty=1,par(lwd=2))
text( maxInterval$interval + 150,200,paste("---maximum(",maxInterval$interval,")"),col=3)

```


