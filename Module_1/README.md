
## Introduction To R
- Named after **Robert Gentleman and Ross Ihaka**
- **Interpreted Language**
- Official R Download Link **[https://cran.r-project.org/](https://cran.r-project.org/)**
- Environment for data analysis, statistical computing and data visualization
- Offers support for simple and complex operations 
- Support for easy data manipulation and output storage
- Open source, well maintained and offers all programming constructs
- Offers a suite of operators and built in data structures for effective data modelling

### R Studio
- Popular open source IDE for working with R
#### Applications
- Network analysis
- Semantic analysis
- Web applications
  
### R console (Interactive and Batch Mode)
- Command typed in console are called expressions
- Interpreter responds to the expression via an error or result
- Up/Down array for recent commands
- *history()* retrieves recent command history
- *Tab* based autocompletion
- Batch Mode - Run large number of sequential commands

#### Batch file execution modes
- **R CMD BATCH generate_graphs.R** *This however cannot access system input*
- **RScript generate_graphs.R** *This helps ow*
- Executable can also be created via R and run as *./application*

### R Workspace
- getwd() and setwd(path) retrieves and sets working directory resp.
- ls() displays files

#### Workspace run methods
- Line by Line
- Source without echo
- Source with echo

*Comments are added in R using #*
*rm(var) deletes a variable*
*rm(list = ls()) can be used to clear all variables in current wd*

> Variables in an r session can be retrieved through the use of ls()
ls(pattern="pattern") # Retrieves all variables starting with pattern

### Saving Workspace (.RData file)
- save(a, file=filename) : saves single variable a
- save(list = ls(all.names = TRUE), file=filename) : saves all variables with name
- save.image() : same as above
- load(file=filename) 

### Packages
- Related set of functions, help files and data files bundled together
#### Working with packages
- getOption("defaultPackages") : Returns list of default loaded packages
- .packages() : Returns current list of loaded packages
- .packages(all.available=TRUE) : Returns list of all available packages
- *install.packages(packagename) and remove.packages(packagename)* Installs and removes a package resp.
- *library(packagename)* Loads a package onto current working directory

### Identifier Naming
- Letters, numbers, underscores and dots
- Can't start with number of underscore
- **Case sensitive**
- Guidelines : Separate words with . or _ , use all lower case

*Support both static and dynamic typing*
Arithmetic operators : + , - , / , * , ** or ^
Modulo operator : % %
Integer Division : % / %

	Predefined constants : Pi, letters, LETTERS, month.abb, month.name

### Data types
- Logical
- Integer
- Numeric
- Complex
- Character

#### Type casting and type check
> This is also termed as coercion
- typeof(var) : returns type of var
- *is*.datatype(var) : checks if var is datatype
- *as*.datatype(var) : converts var to datatype

	**;** can be used to group expressions together *eg: x = 5; y = 10*

### Special Value
- NA : Not available, represents missing value
	- Can be checked for with *is.na(x)*
- Inf and -Inf
- NaN : Not a number, returns as part of not meaningful results
- NULL : Indicates no argument, value given

## Basic IO
```R
scan(what=datatype()) #Takes input continuosly until tapping ENTER twice
as.datatype(readline(?prompt))

cat(var) #Print variable value
```
## Data Structures in R
### Vectors
- Ordered collection of basic data types
- Homogeneous

#### Creating Vectors
~~~R
vector(datatype, length = n) # Creates vector of length n of type datatype
c() # Combine function can be used to create vectors
c(a,b) # Returns the combination two vectors a and b 
#Sequence operator 
(a:b) # Returns a vector with values in range [a, b]
seq(from, to, by, length, along) # Returns vector with values in range [a, b] with step = by and max length = length 
#Assignments can be combined eg: x <- y <- 5:10
assign(var, values) # Creates a vector (var) with values
rep(val, times=n) # Creates a vector of length n with value = val
rep(val, each=n) #Creates vector with each value repeated n times

#Creating name value pair vectors
vec = c(x=val1,y=val2) #Creates a vector with name value pairs or
names(vec) = c(x,y) 
~~~

#### Indexing and values
```R
x[index]

#Indices in R start at 1
length(x) #Returns the length of vector x
# Index can be the following
#1 Logical Indexing 
#2 Positive Integral Values
#3 Negative Integral Values
#4 Character Values ; For vector as name value pairs
```
- var[index] operator returns value at index of values at indices
- *Index is of type var or a single integer, where var can contain indices or a vector of Boolean values indicating each position*

```R
vec[index] #Returns value at index or indices
#if index < 0, exclude element at index abs(index)
which(cond) #Returns indices that satisfy condition

#Assigments
vec[index] = value
#If index > length(vec), the length will update to index and the other values will be set as NA

```
#### Vector Operations
Follows a *vector/element by element*  approach to performing operations 

For vectors with n != m, the result would be of length max(n, m)

	Recycling: The vector of shorter length is duplicated to match longer vector

```R
#Conditional testing
#condition = x < y ; x and y are vectors
any(condition) # Returns TRUE if value in the vector or condition is true
all() # Returns TRUE if all values in the vector satisfy the condition

```

```R
nchar(vec) # Returns a vector with the lenght of each string in vec
#Other in-built operations
length(x)
sum(x)
prod(x)

#Ordering functions
rev(x)
sort(x, descreasing=TRUE/FALSE)

#Statistical functions
min(x,y...) #Returns the smallest values in all the vector
pmin(x,y...) #Returns a vector with a value of min for each vector
max(x)
pmax(x,y...)
#p stands for parallel
mean(x)
var(x)

range(x,y...) #Returns c(min(x,y..), max(x,y....))

#Complex numbers
sqrt(-17) #Error
sqrt(-17 + 0i) #Returns required value

#Conditionals
val %in% vec #Returns TRUE if val in vec, FALSE ow [returns vector is val is vector]

```

#### Vector based operations
```R
x%*%y #Dot product
crossprod(x, y) #Cross product
x%o%y or tcrossprod(x, y) #Outer product
```

### Factors
- Used to represent categorical data
- Can be assumed to be an integer vector having a label

#### Creation
```R
x = factor(z) #z = Any vector creation method with character values
levels(x) #Returns the unique factors in x in sorted ascending order
table(x) #Returns the count of each level in tabular form
nlevel(x) #Returns count of factors in x

#Ordered factor can be created via
x = ordered(z) #or
x = factor(z, orderered = TRUE by default)
#Ordered factor however sorts all results as per level hence it's easier to interpret
```

##### Tapply()

```R
tapply(x, index, func)
#Here index usually represent a particular subset of factors onto whom the function is to be applied
```
### Character Vectors
	Escape sequences are \t, \b, \n etc where \ is the escape character

```R
paste(x,y..., sep = separator) #Coerces/combines all values onto a character vector
```

### Matrices
- Multidimensional collection of data

#### Creating matrices

```R
matrix(data, nrow, ncol, byrow, dimnames=list(rowname, colnames))
#byrow = FALSE would arrange the items in column major and row major ow

dim(mat) #Returns [nrow, ncol]
nrow(mat) and ncol(mat) #Display row and column number resp..

#Naming rows and columns
rownames(mat)
colnames(mat)

#Creating diagonal matrices
diag(val, nrow, ncol) #Creates matrix with i,j = val where i == j , 0 rw
diag(mat) #Returns diagonal elements of the matrix

#Combining matrices and vectors to form matrices

cbind(arg1, arg2,...)
rbind(arg1, arg2,...)
#arg should be vectors or matrices of equal column size
```
#### Accessing matrix elements
> Matrix elements beyond length of rows or columns cannot be accessed  or assigned unlike vectors

```R
mat[x,y] #Returns all elements in cell x,y
mat[x,] #Returns all elements in row x
mat[,y] #Returns all elements in col y
```

#### Matrix operations
```R
t(mat) # Returns transpose of the matrix
solve(mat) #Returns the inverse of a matrix if it's solvable
solve(a, b) #Returns x such that b = ax

eigen(A, ?only.values=TRUE|FALSE) #Computes eigen values and vectors accessed via $val and $vec resp..


#Arithmetic
mat1 %*% mat2 #Matrix multiplication
+ - / * #Operate as expected

#Other operatins
rowSums(mat)
colSums(mat)
rowMeans(mat)
colMeans(mat)
```

#### Applying functions to matrices
```R
apply(mat, margin, func)
#margin = 1 indicates row and 2 indicates column

#Other functions
crossprod(a, b) #Returns aTb
a%o%b #Returns outer product
```

### Arrays
> N dimensional arrays in R

```R
array(vector=c(), ?dimensions=c(), ?dimnames=c())
```


### Lists
- Heterogeneous collection of data

#### Creation of lists
```R
list(values)

#Assigning names
names(l) = namearray
```

#### Accessing elements
```R
l[index] #Allows for regular accessing

#For names lists
l$name #Returns subset
l[name]
```

#### Operations on list
```R
#Lists do not support arithmetic operations 
unlist(l) #Returns vector from list

#Combining lists
c(list1, list2,...)
list(list1, list2,...)
```

### Data Frames
- Matrices with different typed column values

#### Creating Data Frames
```R
data.frame(col1, col2,...)

#Data can also be imported using
read.table(file, ?header=FALSE|TRUE, ?sep=' ', ?nrows=(entirefile), ?skip=0)
read.csv(file, ?header=TRUE|FALSE, ?sep=',', ?nrows=(entirefile), ?skip=0)

#Adding values
rbind(df, ...)
cbind(df, ...)

```

#### Accessing elements
```R

#Returns a dataframe itself
df[c()]

#These two forms on indexing will reduce the result to a vector
df[[c()]]
df$colname

subset(df, condition) #Returns a subset of the dataframe satisfying condition

edit(df) #Opens up df in visual editor mode
```

#### Operations on Data frames
```R
table(df$col1, df$col2) #Cross tabulates the given columns
summary(df$col) #min 1st median mean 3rd max

#Attach and detach or using with
attach(df)
function(colname) #df$colname can be replaced by colname using attach and detach
detach(df)

with(df, {
function(colname)
})

#Sorting wrt column values
order(df, decreasing=TRUE|FALSE, na.last=TRUE|FALSE, method=c("auto", "shell", "quick", "radix"))
#na.last = TRUE => NA values but at then end or first ow

#Removing missing values
complete.cases(df)
```

#### Exporting data
```R
wite.csv(df, file=filename)
write.table(df, file=filename,?row.names=TRUE|FALSE)
```


## Control Flow
### Loops
#### For loops
```R
for (iter in c()) {
	#Operation
}
```

#### While loops
```R
i <- 1
while(cond) {
#Operation
update(i)
}
```

### Controlling Loops
```R
break #Terminates loop
next #Equivalent to continue
```

### Functions as arguments and names arguments
>Treated as First class members and are also stored as variables

```R
increment <- function(vector, val, supportFunction) {
	return supportFunction(vector + val)
}

addition <- function(vector) {
	return sum(vector) 
}

x = c()
cat(increment(x, 10, addition)) #Normal parameter passing
cat(increment(vector=x, val=10, supportFunction=addition)) #Named arguments
```
