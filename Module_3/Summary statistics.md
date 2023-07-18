- let dow30 be the dataset
```R
range(1:100) #returns the maximum and minimum of values
fivenum(values) #returns min 25th perc median 75thper max
IQR(values) #returns 75thpercentile-25thpercentile
summary(dataframe) #returns 5 num summary+ mean of every attribute of df
str(dataframe) #displays the structure of the object
stem(x,scale=1,width=80,atom=1e-08)
 - x-numeric vector,width - controls the width, atom - a tolerance factor
```

- stem function is a text based tool for looking at the distribution of a numeric 
- [gfg-stem and root](https://www.geeksforgeeks.org/r-stem-and-leaf-plots/)
