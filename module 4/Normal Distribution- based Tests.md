### comparing means - anova & t.test

| Feature | t-test | ANOVA |
|---|---|---|
| Assumptions | Data is normally distributed | Data does not have to be normally distributed |
| Power | More powerful | Less powerful |
| Number of groups | Two groups | Three or more groups |

```R
t.test(x, y = NULL,
alternative = c("two.sided", "less", "greater"),
mu = 0, paired = FALSE, var.equal = FALSE,
conf.level = 0.95, ...)
```

*anova is called analysis of variance as inferences about means are made by analyzing variance*


### Steps in hypothesis testing

1. input
2. test statistics calculation
3. tvalue=ratio of mean difference and SE ; Fvalue = ratio of variability btw groups and variability if observations within each groups
4.  tabulated value at DOF and confidence (two sided or one sided)
5. comparision between calculated and tabulated if calculated is higher null hypothesis is rejected
*for a given level of confidence as the DOF increase tabulated value decrease so as sample size increase the significan*ce level increases

### types of t test
- one sample t test - group vs standard
- two sample t test - 2 sample from 2 dif groups
- paired - when the 2 sample from same

### comparing paired data
 paired=TRUE
 SPECint2006
 ![[Pasted image 20230717210240.png]]

### comparing variances of two populations


| Statistical Test | Purpose | Number of Groups | Type of Data | Comparison |
|------------------|---------|-----------------|--------------|------------|
| F-test           | Compare variances or ratios of variances between groups | More than two groups | Continuous data | Variances/ratios of variances between groups |
| t-test           | Compare means between two groups | Two groups | Continuous data | Means between two groups |
| ANOVA (Analysis of Variance) | Compare means between multiple groups | More than two groups | Continuous data | Means between multiple groups |

```R
var.test(x,y,ratio=1,
alternate=c("two-sided","less","grater"),
conf.level=0.95,...)
```
the above is the f test

### comparing means across more than two groups
```R
aov(formula,data=NULL(dataframe),projections=FALSE,qr=TRUE,contrasts=NULL...)
```
![[Pasted image 20230717212322.png]]
[make me understand](https://chat.openai.com/share/920f8e40-96aa-4144-909e-ad74f7e9550d)

### pairwise t tests btw multiple groups
- not interested in difference across groups 
- like to know more details about differences
- for it perform t test btw every pair of groups
```R
pairwise.t.test(x, g, p.adjust.method = p.adjust.methods,pool.sd =!paired, paired = FALSE,alternative = c("two.sided", "less", "greater"), ...)
```
![[Pasted image 20230717214428.png]]

### Normality test
**shapiro-wilk test**
```R
a=shapiro.test(x)
```

a$p-value >0.05 then normally distributed

### kstest
kolmogorow smirnov test to see if vector came from arbitrary probability distribution

- testing if two vectors came from same distribution
```R
ks.test(data$1,data$2)

```
if p value>0.05 then same distribution

### Correlation test
```R
cor.test(x,y,
		alternative=c(),
		method=c("pearson","kendall","spearman"),
		exact=NULL,conf.level=0.95)
```