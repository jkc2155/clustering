# clustering
Clustering example

```{r}
Data <- read.csv("online-tutor.csv")
View(Data)
```

# Determine number of clusters

```{r}
wss <- (nrow(Data)-1)*sum(apply(Data,2,var))
for (i in 2:15) wss[i] <- sum(kmeans(Data, 
  	centers=i)$withinss)
plot(1:15, wss, type="b", xlab="Number of Clusters",
  ylab="Within groups sum of squares")
  ```
 # K-Means Cluster Analysis
 ```{r}
fit <- kmeans(Data, 9) # 5 cluster solution
# get cluster means 
aggregate(Data,by=list(fit$cluster),FUN=mean)
```

# append cluster assignment
```{r}
Data <- data.frame(Data, fit$cluster) 
```
#Plot Cluster
```{r}
clusplot(Data, fit$cluster, color=TRUE, shade=TRUE, 
         labels=2, lines=0)
```