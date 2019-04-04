---
title: Insert title here
key: 7f3002bc5fc4ccdff32c9d6cdb715bc7

---
## Introduction to missing data with mice

```yaml
type: "TitleSlide"
key: "433cb61289"
```

`@lower_third`

name: Chamberlain Mbah
title: Data scientist at Tobania


`@script`
Hello we come to this introduction chapter on missing values with mice

This chapter gives an overview of the mice package and how easy it is to get started


---
## The nhanes dataset

```yaml
type: "FullSlide"
key: "861914663f"
```

`@part1`
```r
library(mice)
```
{{1}}
```r
head(nhanes)
  age  bmi hyp chl
1   1   NA  NA  NA
2   2 22.7   1 187
3   1   NA   1 187
4   3   NA  NA  NA
5   1 20.4   1 113
6   3   NA  NA 184
```{{2}}


`@citations`
Schafer, J.L. (1997). Analysis of Incomplete Multivariate Data. London: Chapman & Hall. Table 6.14.


`@script`
The nhanes dataset that we will use through out this chapter, comes alongside with mice. 

And the nhanes dataset contains four variables age group bmi hyp and chl.

Each of these variables contains missing values which are represented here with NAs.

There are 25 observations in the dataset.

I have only shown the first 6 observations.


---
## Inspecting incomplete data

```yaml
type: "TwoColumns"
key: "5505bc5b97"
```

`@part1`
```r
md.pattern(nhanes)
```
{{1}}

```r
   age hyp bmi chl   
13   1   1   1   1  0
3    1   1   1   0  1
1    1   1   0   1  1
1    1   0   0   1  2
7    1   0   0   0  3
     0   8   9  10 27
```
{{2}}


`@part2`
![](https://assets.datacamp.com/production/repositories/4854/datasets/fccfb203083f12074da477d71340db7f7046c4ff/missingPatternVis.png){{3}}


`@script`
How do we get an overview of the missingness in the dataset? 
We use the md.pattern function from mice and this function gives  a matrix that has the following values.

27 here represents the total number of missingness in the dataset.
10 is missing values from chl as a variable alone
9 values are missing for bmi 
8 values for hyp and the age group has no missing value

We also see here that 13 rows are compete
4 rows have one missing value
1 row has two missing values
7 rows have three missing values

Another way of visualising the missingness is with this heatmap here.
We see that we have the same numbers on the axes here.

Missing values are represented with the red color here while complete values are 
represented with blue.


---
## Ad Hoc imputation methods

```yaml
type: "FullSlide"
key: "baf8c5f40e"
disable_transition: false
```

`@part1`
```r
imp <- mice(nhanes, method = "mean", m = 1, maxit = 1)
```{{1}}


`@script`
How can we quickly impute the missing values  we seen?

This can be done with the mice function that takes in the dataset and the method of imputation.

Here we use the means. So each variable that has a missing value will be replace by the mean of that variable.

There are two other parameters here m and maxit which we will ignore for the moment.
And once this command is run, we create a new object called imp.


---
## Ad Hoc imputation methods

```yaml
type: "FullSlide"
key: "3bb43f0ca3"
```

`@part1`
```r
colMeans(nhanes,na.rm = TRUE)
       age        bmi        hyp        chl 
  1.760000  26.562500   1.235294 191.400000 
```

```r
imp%>%complete()%>%head(n=1)
  age     bmi      hyp   chl
1   1 26.5625 1.235294 191.4
```
{{1}}

```r
head(nhanes,n=1)
  age  bmi hyp chl
1   1   NA  NA  NA
2   2 22.7   1 187
```
{{2}}


`@script`
Recall, here I show you the variable means of each variable.

And after imputation if we now  run the complete function on the impute object which is imp here. And look at the first row. We see that there no missing values for each variable. Comparing it to the original dataset that has 3 missing values for bmi hyp and chl. Observe here that each of the values, the missing values have been replaced with the variable means.


---
## Let's try out some exercises

```yaml
type: "FinalSlide"
key: "5e76b31415"
```

`@script`
Let's our hands on something

