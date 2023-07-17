### 1. Proportion tests
- if u r measuring the probability of success the use prop.test to test whether the difference btw groups is statistically larger
```R
prop.test(x,n,p=NULL,
		 alternative,
		 conf.level,
		 correct=TRUE)
```
### 2. Binomial Tests
```R
binom.test(x,n,p=0.5,
		  alternative,conf.level)
```
### 3. Tabular data tests
- hypothesis 2 variables are independent
- alternative - not independent
- for small use fisher test
```R
fisher.test(x,y=NULL,workspace=20000,hybrid=False,
		   alternative,conf.level,simulate.p.value=FALSE,B=2000)
```
![[Pasted image 20230717230922.png]]

- chisquare tests as fisher test is intensive computationally
```R
chisq.test(x,y=NULL,correct=TRUE,
		  p = rep(1/length(x), length(x)), rescale.p = FALSE,
		  simulate.p.value = FALSE, B = 200)
```

### Non-Parametric Tabular Data Tests
- Friedman rank-sum countepart to 2 way anova tests
![[Pasted image 20230717231357.png]]