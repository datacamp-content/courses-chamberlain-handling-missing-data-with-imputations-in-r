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
type: "TwoColumns"
key: "92849ed01d"
```

`@part1`
```{r}
library(mice)
```
{{1}}
```{r}
head(nhanes)
  age  bmi hyp chl
1   1   NA  NA  NA
2   2 22.7   1 187
3   1   NA   1 187
4   3   NA  NA  NA
5   1 20.4   1 113
6   3   NA  NA 184

```
{{2}}


`@part2`
```{r}
summary(nhanes)
```
{{3}}
```{r}
     age           bmi          hyp           chl     
 Min.   :1.0   Min.   :20   Min.   :1.0   Min.   :113  
 1st Qu.:1.0   1st Qu.:23   1st Qu.:1.0   1st Qu.:185  
 Median :2.0   Median :27   Median :1.0   Median :187  
 Mean   :1.8   Mean   :27   Mean   :1.2   Mean   :191  
 3rd Qu.:2.0   3rd Qu.:29   3rd Qu.:1.0   3rd Qu.:212  
 Max.   :3.0   Max.   :35   Max.   :2.0   Max.   :284  
               NA's   :9    NA's   :8     NA's   :10   

```

{{4}}


`@citations`
(Schafer, 1997, Table 6.14)


`@script`
The mice package contains several datasets. Once the package is loaded, these datasets are available for use. Lets load mice. After the load the mice package, nhanes data set is then available for us.By typing head(nhanes) we observe the first 6 rows of the nhanes dataset. The nhanes dataset is a small data set with some missing values represented here with NAs. It contains 25 observations on four variables: age group, body mass index, hypertension and cholesterol.


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


---
## Inspecting incomplete data

```yaml
type: "FinalSlide"
key: "5e76b31415"
```

`@script`


