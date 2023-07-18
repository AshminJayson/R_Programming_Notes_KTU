1. The power function can be used to estimate how large a difference you need to see between groups to get statistically significant results.
2. In this example, we are testing the efficacy of a new drug for treating depression. We assume a standard deviation of 8.9 for this experiment and want a power of 0.95 for the experiment.
3. If we have 50 subjects for the study and split them into two groups of 25 people each, the difference in HAMD scores would need to be at least 9.26214 to be significant at this level.
4. If we doubled the number of subjects to 100, the difference in HAMD scores would need to be at least 6.480487 to be significant.
5. This means that increasing the sample size can reduce the minimum difference that needs to be seen in order to get statistically significant results. This is because a larger sample size makes it more likely that you will see a difference between the groups, even if the difference is small.

```R
power.t.test(power=0.95,sd=0.89,n=25,sig.level=0.05)
```
