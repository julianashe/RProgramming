## R Programming on Coursera, Week 1
## Date: 06/03/2014
## Topic: Data Types
========================================================

  ## atomic classes: numeric, logical, character, integer, complex
  ## vectors, lists
  ## factors
  ## missing values
  ## data frames
  ## names

## Entering input
1 ## treated as numeric
1L ## integer
1/Inf ## infinite, returns 0
1/0 ## returns infinite
0/0 ## not valid, returns missing value NaN

x <- 1 ## assignment operator, assign value 1 to symbol x
print(x) ## prints the value of x
x ## prints the value of x (alternative way)
msg <- "hello" ## assigning value of string "hello"

## evaluation

x <- 5 ## noting printed
x ## auto-printing occurs
print(x) ## explicit printing
  ## the "[1]" in returned results indicates the element
x <- 1:20 # create integer sequences
x #return the integer sequences

## creating vectors

x <- c(0.5, 0.6) ## numeric
x <- c(TRUE, FALSE) ## logical
x <- c(T, F) ## logical 
x <- c("a", "b", "c") ## character
x <- 9:29 # integer 
x <- c(1+0i, 2+4i) ## complex
  ##using vector() function
x <- vector("numeric", length = 10)
x # returns ten 0s in sequence

## mixing objects-->coercion occurs so that every element 
  ## in the vector is of the same class

y <- c(1.7, "a")  ## character
y <- c(TRUE, 2) ## numeric
y <- c("a", TRUE) ## character

## explicit coercion
  ## objects can be explicitly coerced from one class to other
  ## using the as.* functions, if available

x <- 0:6
class(x)
as.numeric(x) ## returns 0 1 2 3 ...
as.logical(x) ## returns FALSE TRUE TRUE...
as.character(x) ## returns "0" "1" "2" ...
  ## note that coercion does not always work
  ## nonsensical coercion results in NAs, e.g.
x <- c("a", "b", "c")
as.numeric ## returns NA NA NA and a warning message
as.logical(x) ## returns NA NA NA
x <- 1:6
as.complex(x) ## returns 0+0i 1+0i 2+0i ...

## Matrices
  ## vectors with a dimension attribute
  ## the dimension attribute is itself an integer vector 
  ##of length 2(nrow, ncol)

m <- matrix (nrow = 2, ncol = 3) ## assign mattrix w 2 rows 3 cols
m ## print m as matrix, with NAs as values 
dim(m) ## give dimension attributes, nrow, ncol
attributes(m) ## returns first attribute $dim and nrow, ncol
  ## matrices are constructed column-wise
  ## entries starting in the upper left and running down the columns
m <- matrix((1:6), nrow = 2, ncol = 3)
m #values of 1:6 assigned to matrix column-wise
  ##adding a dimention attribute later
m <- 1:10
m
dim(m) <- c(2,5) ## assigning dimensional attributes to matrix
m ## m now is a matrix of 1:10 with 2 rows, 5 cols

## column-binding and row-binding
x <- 1:3
y <- 10:12
cbind(x,y) ##column-binding x, y
rbind(x,y) ##row-binding x, y

## lists
  ## special type of vector that can contain elements of different classes
  ## important in R
x <- list(1, "a", TRUE, 1 + 4i)
x ## does not print out as vecotr, but each element by class seperately
  ## this seperates lists from other types of vectors

## Factors
  ## used to represent categorical data
  ## can be unordered or ordered 
  ## e.g. unordered: male, female
  ## e.g. ordered: assistant, associate, and full professors
  ## factors are treated specially by modeling functions like lm() glm()
  ## factors with labels is better than using integers as factors are self-describing
  ## e.g. better "male" and "female" than 1 and 2

x <- factor(c("yes", "yes", "no", "yes", "no")) ## create the factors
x ## print x, also returns two levels: no yes
table(x) 
unclass(x) ## unclass can bring it down to integer factor, yes coded as 2, no coded as 1
attr(x, "levels") ## returns the "levels" attributes: "no" "yes"
  ## can order the levels using levels argument
x <- factor(c("yes", "yes", "no", "yes", "no"),
            levels = c("yes", "no")) ## ordering levels in the factor function
x ## returns factor, and levels in order: yes no

## missing values
  ## denoted by NA or NaN
  ## NaN for mathematical, NA for everything else
  ## is.na() can test objects if they are NA
  ## is.nan() can test for NaN
  ## NA values have a class also, e.g. integer NA, character NA, etc.
  ## A NaN value is also NA, but the converse is not true

x <- c(1, 2, NA, 10, 3)
is.na(x) ## returns F F T F F
is.nan(x) ## returns F F F F F
x <- c(1, 2, NaN, NA, 4)
is.na(x) ## returns F F T T F, a NaN is also a NA
is.nan(x) ## returns F F T F F, a NA is not a NaN

## Data Frames
  ## important to store tabular data
  ## special type of list: every element of the list has the same length
  ## each element of the list can be thought of a column
  ## the length of each element of the list is the number of rows
  ## unlike matrices, data frames can store different classes of objects in each column
  ## special attribute: row.names
  ## usually created by calling read.table() or read.csv()
  ## can be convered to a matrix by calling data.matrix()

x <- data.frame(foo = 1:4, bar = c(T, T, F, F))
x ## 4 rows, 2 cols data frame
nrow(x)
ncol(x)

## Names
  ##useful for writing readable code and self-describing objects
x <- 1:3
names(x) ## no names originally, returns NULL
names(x) <- c("foo", "bar", "norf") ## names each element
x ## now each element has a name on the top
names(x) ## the names function returns names only
  ## lists can also have names
x <- list(a = 1, b = 2, c = 3) ## a, b, c as names of elements
x ## returns elements seperately with names and values
  ## matrices can have names
m <- matrix(1:4, nrow = 2, ncol = 2)
dimnames(m) <- list(c("a", "b"), c("c", "d")) ## creating dimension names using list function
  ##first vector as row names, second vector as column names
m ## returns the matrix with row and column names



























