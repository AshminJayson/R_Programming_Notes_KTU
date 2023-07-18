![[Pasted image 20230718011845.png]]

probability density
```R
dnorm(x,mean=0,sd=1,log=FALSE)
```

pnorm- distribution fn for normal distribution

```R
pnorm(q, mean = 0, sd = 1, lower.tail = TRUE, log.p = FALSE)
```

- `q`: The value for which you want to calculate the cumulative probability. It represents a point on the x-axis of the normal distribution.
- `mean`: The mean of the normal distribution. It determines the center or average value of the distribution. The default value is 0.
- `sd`: The standard deviation of the normal distribution. It represents the spread or variability of the distribution. The default value is 1.
- `lower.tail`: A logical value that determines whether the cumulative probability should be calculated for values less than or equal to `q` (lower.tail = TRUE) or for values greater than `q` (lower.tail = FALSE). The default value is TRUE.
- `log.p`: A logical value that determines whether the result should be returned as the probability `p` (log.p = FALSE) or as the natural logarithm of `p` (log.p = TRUE). The default value is FALSE.

qnorm is the reverse of the distribution function
```R
qnorm(p, mean = 0, sd = 1, lower.tail = TRUE, log.p =FALSE)
```
*qnorm takes probability and returns z score while pnorm does the exact opposite*

rnorm return random values from normal distribution
```R
rnorm(n, mean = 0, sd = 1)
```

