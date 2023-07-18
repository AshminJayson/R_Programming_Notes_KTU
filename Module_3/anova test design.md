```R
power.anova.test(groups = NULL, n = NULL, between.var = NULL, within.var = NULL, 
					sig.level = 0.05, power = NULL)
```

- This function will calculate either groups, n, sig.level, between.var, power, within.var, or sig.level, depending on the input. 

-  You must specify exactly six of these parameters, and the remaining argument must be null; this is the value that the function calculates.