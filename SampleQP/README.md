Question 1:
Write a R program to add element “23” to the vector (24, 56, 67) in the second position.

R
Copy code
vector <- c(24, 56, 67)
vector <- append(vector, 0, after = 1)
vector[2] <- 23
print(vector)
Output: [24, 23, 56, 67]

Question 2:
Discuss the general list operations in R with example.

General list operations in R include creating a list, accessing elements, modifying elements, adding elements, and removing elements. Here are some examples:

R
Copy code

# Creating a list

my_list <- list("apple", 1, TRUE)

# Accessing elements

print(my_list[[1]]) # Output: "apple"
print(my_list[[2]]) # Output: 1

# Modifying elements

my_list[[1]] <- "banana"
print(my_list[[1]]) # Output: "banana"

# Adding elements

my_list[[4]] <- 3.14
print(my_list[[4]]) # Output: 3.14

# Removing elements

my_list <- my_list[-2]
print(my_list) # Output: ["banana", TRUE, 3.14]
Question 3:
Calculate the cumulative sum and cumulative product for the given data 23, 1, 7, 2, 8, 10, 17 using R program.

R
Copy code
data <- c(23, 1, 7, 2, 8, 10, 17)
cumulative_sum <- cumsum(data)
cumulative_product <- cumprod(data)
print(cumulative_sum)
print(cumulative_product)
Output:
Cumulative Sum: [23, 24, 31, 33, 41, 51, 68]
Cumulative Product: [23, 23, 161, 322, 2576, 25760, 438320]

Question 4:
Explain aggregate function in R.

The aggregate function in R allows you to apply a specific function to subsets of your data based on one or more grouping variables. It is used to perform summary statistics or computations on groups within a dataset. The syntax for the aggregate function is as follows:

R
Copy code
aggregate(formula, data, FUN)
"formula" specifies the variables involved in the computation.
"data" is the data frame containing the variables.
"FUN" is the function to be applied.
Example:

R
Copy code
data <- data.frame(
group = c("A", "A", "B", "B", "B"),
value = c(10, 15, 8, 6, 12)
)

result <- aggregate(value ~ group, data, mean)
print(result)
Output:
group value
1 A 12.5
2 B 8.666667

Question 5:
List the applications of R programming.

R programming has various applications, including:

Data analysis and statistical computing
Machine learning and predictive modeling
Data visualization and graphical representation
Financial analysis and risk modeling
Bioinformatics and genomics research
Social network analysis
Natural language processing
Time series analysis
Web scraping and data extraction
Geospatial analysis and mapping
Question 6:
Illustrate summary function.

The summary function in R provides a summary of statistical measures for a given dataset or object. It displays various statistics such as minimum, 1st quartile, median, mean, 3rd quartile, and maximum values for numeric variables. It also provides counts for categorical variables. Here's an example:

R
Copy code
data <- c(5, 10, 15, 20, 25)
summary(data)
Output:
Min. 1st Qu. Median Mean 3rd Qu. Max.
5.00 10.00 15.00 15.00 20.00 25.00

Question 7:
List any three graphics functions.

Three graphics functions in R are:

plot(): Creates a variety of plots, including scatter plots, line plots, bar plots, etc.
hist(): Generates a histogram to visualize the distribution of data.
boxplot(): Creates a box plot to display the distribution of a variable.
Question 8:
Explain Lattice function.

Lattice is a powerful graphics package in R that provides a high-level interface for creating conditioned plots, allowing you to divide the data into subsets based on one or more variables. It allows for the creation of trellis plots, which display multiple panels or facets to represent different groups or subsets of data. Lattice provides functions such as xyplot(), bwplot(), and levelplot() for creating various types of conditioned plots.

Question 9:
Suppose that you have a dataset D1 and you design a linear regression model of degree 3 polynomial and you found that the training and testing error is "0" or in other terms it perfectly fits the data. What will happen when you fit a degree 2 polynomial in linear regression?

If a degree 3 polynomial perfectly fits the data with zero training and testing error, it indicates that the model is likely overfitting the data. When fitting a degree 2 polynomial in linear regression, it may not perfectly fit the data and may have some training and testing error. The degree 2 polynomial is less flexible than the degree 3 polynomial, so it will have a simpler form and may provide a better balance between fitting the data and generalizing to new data.

Question 10:
Explain logistic regression function in R.

Logistic regression is a statistical method used for modeling the relationship between a binary dependent variable and one or more independent variables. In R, the logistic regression function is typically performed using the glm() function with a binomial family. Here's an example:

R
Copy code
data <- data.frame(
x1 = c(1, 2, 3, 4, 5),
x2 = c(0, 1, 0, 1, 0),
y = c(0, 0, 0, 1, 1)
)

model <- glm(y ~ x1 + x2, data = data, family = binomial)
summary(model)
The glm() function fits a logistic regression model, and the family argument specifies the binomial family for binary outcomes. The summary() function provides the summary of the fitted model, including coefficients, standard errors, p-values, and other relevant statistics.
