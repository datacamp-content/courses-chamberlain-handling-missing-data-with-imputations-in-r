---
title: Insert title here
key: 7f3002bc5fc4ccdff32c9d6cdb715bc7

---
## Introduction to the mice package

```yaml
type: "TitleSlide"
key: "433cb61289"
```

`@lower_third`

name: Chamberlain Mbah
title: Data scientist at Tobania


`@script`
Welcome to the course, my name is Chamberlain Mbah, I am a data scientist. Lets get start.


---
## Inspecting incomplete data

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
This course is all about missing values and how to work with them. 

First lets look at a typical dataset with missing values. 

The mice package which will be our main tool in this course contains several datasets.  
{{1}} First lets load mice 

Now that we have loaded mice,  all the datasets within mice are available to us.

{{2}} Lets have a look at the nhanes dataset  introduced Schafer's, 1997 paper in Table 6.14.

The nhanes dataset is a small dataset with missing values.

It contains 25 observations although, I have only shown  6 of them with the head function in R. 

There are four variables:  age group, body mass index, hypertension and cholesterol (mg/dL).


Notice that each of these variables have missing values represented in R with NAs. 

Lets study the messing data pattern further in the next slide


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
{{1}} If you use the md.pattern() function in mice you will get the following missing pattern. {{2}}

What do we see here? 

We see a matrix, first ignore the first column, the last column and the last row. 

A 1 represents data is present and a 0 represents  missingness. 

Now lets jump to to the last row of the matrix
The missingness pattern shows that there are 27 missing values in total: 

10 of them cholesterol , 9 for bmi and 8 for hyp and no missing values for age.

Moreover, there are 13 completely observed rows, four rows with 1 missing, one row with 2 missings and seven rows with 3 missings. Looking at the missing data pattern is always useful (but may be difficult for datasets with many variables). It can give you an indication on how much information is missing and how the missingness is distributed.


The heatmap also conveys the same information about about the missing values


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
```


`@script`



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
```{{1}}

```r
head(complete(imp),n=1)
  age     bmi      hyp   chl
1   1 26.5625 1.235294 191.4
```
{{2}}

```r
head(nhanes,n=1)
  age  bmi hyp chl
1   1   NA  NA  NA
2   2 22.7   1 187
```
{{3}}


`@script`



---
## Let's try out some exercises

```yaml
type: "FinalSlide"
key: "5e76b31415"
```

`@script`
Time to put all you have learned into practice

