```R
power.t.test(n = NULL, delta = NULL, sd = 1, sig.level = 0.05,
		power = NULL,
		type = c("two.sample", "one.sample", "paired"),
		alternative = c("two.sided", "one.sided"),
		strict = FALSE)
```

- This function will calculate either n, delta, sig.Level, sd, or power, depending on the input.
-  Have to specify at least four of these parameters: n, delta, sd, sig.Level, power.