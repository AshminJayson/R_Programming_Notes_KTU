```R
power.prop.test(n = NULL, p1 = NULL, p2 = NULL, sig.level = 0.05,
				power = NULL,
				alternative = c("two.sided", "one.sided"),
				strict = FALSE)
```
- This function will calculate either n, p1, p2, sig.level, or power, depending on the input. 
- You must specify at least four of these parameters: n, p1, p2, sig.level, power.