```R
> rbinom (n=1, size=10, prob=.4)
[1] 3
>rbinom(n=5, size=10, prob=.4)
[1] 4 3 5 2 5
rbinom (n=10, size=10, prob=.4)
[1] 5 2 7 4 7 3 2 3 3 3

> # probability of 3 successes out of 10
>dbinom(x=3, size=10, prob=.3)
[1] 0.2668279
> # probability of 3 or fewer successes out of 10
> pbinom(q=3, size=10, prob=.3)
[1] 0.6496107
> both functions can be vectorized
>dbinom(x=1:10, size=10, prob=.3)
[1] 0.1210608210 0.2334744405 0.2668279320 0.2001209490 0.1029193452
[6] 0.0367569090 0.0090016920 0.0014467005 0.0001377810 0.0000059049
```

