# Analyzing Data
## Summary Statistics

```R
min(df)
max(df)
mean(df)
range(df) #Returns [min, max]
fivenum(df) #Returns five number summary
IQR(df) #Returns difference between 25% and 75%
str(df) #Returns df structure with open, close, high etc
stem(x, scale=1, width, atom) #x = numeric vector, scale = plot length, atom = tolerance factor

#optional na.rm = TRUE will ignore NA values
#option trim = x ; 0 < x < 1 will remove a fraction of observations from both sides
#summary function will return NA if NA is present in the data

```

## Statistical Tests

Steps in hypothesis testing
1. We take up two hypothesis *null hypothesis* and *alternative hypothesis*
2. The alternative hypothesis assumes that there is a statistically significant difference exists between the means, whereas the null hypothesis assumes that there is no statistically significant difference exists between the means.
3. First step is to calculate the test statistics *t value in T test * and *f value in ANOVA test*
4. In student's t test, calculated t value in the ratio of mean difference and standard
5. Find the tabulated value at degree of freedom for the given observations and desired level of confidence.
6. Compare the calculate value with the tabulated value
7. *If calculated value > tabulated value* -> *reject null hypothesis* else *do not reject null hypothesis*
> Higher degree of freedom will have a lower tabulated value for a given level of confidence

### Continuous Data
#### Normal Distribution Based Tests
	Can only be applied to normalized data
##### Comparing Means
###### T Test

```R
t.test(x, y, alternative=c("two.sides", "less", "greater"), mu=0, paired=FALSE, var.equal=FALSE, conf.level=0.95,...)

#mu = mean under null hypothesis
#var.equal implies if the variances are assumed to be the same
#paired implies that the vectors are paired
```

**Checks**
1. If groups come from a single population perform a paired t test
2. If groups come from two difference populations perform a two sample t test
3. If there is one group being compared to a standard value perform a one sample t test
4. If the check is to only find if one population is different from another perform a *two tailed t test* if the check if for mean difference perform *one tailed t test*
##### Comparing paired data
	Done by assigning a value of y as well as paired=TRUE

##### Comparing Variances of two populations
###### F test

```R
var.test(x, y, ratio=11, alternative=c("two.sided", "less", "greater", conf.level=0.95,...))
```

##### Comparing means across more that two groups
	Anova test is performed to calculate the variation of means across more that three groups
	Anova test assumes that the variance is equal across groups this can be compared using oneway.test(formula, data, subset, na.action, var.equal=FALSE)

```R
aovObj = aov(formula, data, projections=FALSE, qr=TRUE, constrasts=NULL,...)
# It is preferred to replace formula by lm(formula, data) for better information
model.tables(aovObj) # Displays more information regarding anova object
```

##### Pairwise t test across groups

```R
pairwise.t.test(x, g, p.adjust.method = p.adjust.methods, pool.sd = !paired, paired=FALSE, alternative=c())

#g is the factor to be used to group values
#pool.sd -> calculate single standard deviation across the groups and use that
```

##### Testing For Normality
```R
shapiro.test()

#if p value > 0.0.5 the data is normally distributed else otherwise
```

##### Check if data came from an arbitrary distribution

```R
#Kolmogorow-Smirnow test
ks.test(x, y, alternative, exact,...)

# If ties exists then the value is not actually distributed as per the y distribution
# Cutoff pvalue = 0.05
```

##### Correlation test

```R
cor.test(x, y, alternative, metohd=c("pearson", "kendall", "spearman"), exact=NULL, conf.level=0.95)

#alternative hypothesis -> true correlation is not equal to 0
```

#### Non-Parametric Tests

##### Comparing Means

```R
wilcox.test(x,y,alternative,mu,paired,exact,correct=TRUE,conf.int,conf.level=0.95,...)

#rank[i, j] = 1 is y[j] < x[i] or 0 otherwise
#It can lead to incorrect interpretation if there are many values with the same are there
```

##### Comparing more than one mean

```R
kruskal.test(x,g,...)
krusktal.test(formula, data)
```

##### Comparing Variances

```R
fligner.test(x, g, ...)
```

##### Difference in scale parameters

```R
ansari.test(x,y,alternative,exact,conf.int,conf.level)
mood.test(x,y,alternative)
```

### Discrete Data

#### Proportion Test

```R
prop.test(data)
```

#### Binomial Test

```R
binom.test(x,n,p=0.5,alternative,conf.level)
```

#### Tabular Data Test

```R
fisher.test(x,y=NULL, workspace, hybrid, control=list(), alternative, conf.int, conf.level, simulate.p.value=FALSE, B=2000)

#conf.int whether to compute and return confidence interval values
#B no of replicas in monte carlo
#simulate.p.val whether to use monte carlo simulation

#Fisher test is computationally intensive for larger tables hence we use

chisq.test(x,y=NULL,correct=TRUE,p,rescale.p, simulate.p.valu,B)
#Correct = whether to apply continuity correction
#p vector of probabilites to represent the hypothesis to test
```

#### Non parametric Tabular Data Tests

```R
friedman.test(y, groups, blocks,...)
```

## Power Tests
1. Very useful in designing experiment with emphasis on estimation of margin of difference needed in groups for the result to be statistically significant.
### T test Design

```R
power.t.test(n, delta, sd, sig.level, power, type, alternative, strict)

#Delta true difference between means
#sd true standard deviation
#sig.level type 1 error probability
#power type 2 error probabiliy
#strict, whether to use strict interpretations

#We have to specity at least 4 parameters in n, deltsa, sd, sig.level, power
```

### Proportion Test Design

```R
power.prop.test(n,p1,p2,sig.level,power,alternative,strict)
#p1 and p2 are probability of success in each group
#Atleast 4 of n,p1,p2,sig.level or power must be mentioned
```


### Anova Test Design

```R
power.anova.test(groups,n,between.var,within.var,sig.level.power)

#groups is the number of groups and n specifies the number of observations in a group
#Atleast 6 of n, sig.level, between.var, power, within.var, groups must be mentinoned
```

## Probability Distributions

### Normal Distribution 

```R
dnorm(x,mean=0,sd=1,log=FALSE) #Returns probability density at a given value
pnorm(q,mean,sd,lower.tail=TRUE,log.p=FALSE) #Returns the distribution function returns density sum upto q if lower.tail = TRUE else greater than q
qnorm(p,mean,sd,lower.tail=TRUE,log.p=FALSE) #Returns the value of q where pnorm(q) = p
rnomr(n,mean,sd) #Generates n random values from a given normal distribution mean and sd
```

### Binomial Distribution

```R
dbinom(x,size,prob)
pbinom(q,size,prob)
qbinom(p,size,prob)
rbinom(n,size,prob)
```

### Poisson Distribution

```R
dpois(x,lambda)
ppois(q,lambda)
qpois(p,lambda)
rpois(n,lambda)
```