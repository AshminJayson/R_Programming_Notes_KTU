- unknown distribution or not normal

### Comparing two means
wilkoxon rank-sum test is non parametric equivalent to t-test
```R
wilkox.test(x,y=NULL,
		   alternative=c("less","greater","two.sided"),
		   paired=FALSE,
		   conf.level=0.95,correct=TRUE,..)
```

it works by comparing ranks if the sum of all ranks should be approximately the half of no of samples
![[Pasted image 20230717223749.png]]
disadvantage- misleading results if the measurements are same

### kruskal -Wallis rank-sum test
![[Pasted image 20230717223858.png]]
anova equivalent

### fligner-killeen (median test)
![[Pasted image 20230717223947.png]]

### ansari.test

- based on difference in parameters
![[Pasted image 20230717224015.png]]

### moodtest
- based on difference in parameters
  ```R
  mood.test(x,y,alternate....)
```