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
title: Data scientist


`@script`



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
```r
colMeans(nhanes,na.rm = TRUE)
       age        bmi        hyp        chl 
  1.760000  26.562500   1.235294 191.400000 
```


`@script`



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
If you use the md.pattern() function in mice you will get the following missing pattern. 

The missingness pattern shows that there are 27 missing values in total: 10 for cholesterol , 9 for bmi and 8 for hyp and no missing values for age. Moreover, there are 13 completely observed rows, four rows with 1 missing, one row with 2 missings and seven rows with 3 missings. Looking at the missing data pattern is always useful (but may be difficult for datasets with many variables). It can give you an indication on how much information is missing and how the missingness is distributed.


The heatmap also conveys the same information about about the missing values


---
## Ad Hoc imputation methods

```yaml
type: "FullSlide"
key: "fd98bd8f30"
```

`@part1`
```r
imp <- mice(nhanes, method = "mean", m = 1, maxit = 1)
```
{{1}}


`@script`
Lets try out some basic and rather ad hoc imputations methods using mice on the nhanes dataset we saw in the previous slide.


---
## Let's try out some exercises

```yaml
type: "FinalSlide"
key: "5e76b31415"
```

`@script`
Time to put all you have learned into practice

