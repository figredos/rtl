# The apply family

The apply family in R is a set of functions that provide efficient ways to apply functions to multiple elements of an object. This family consists of three primary funcitons: `apply`, `lapply`, `sapply`, and `vapply`.

- [The apply family](#the-apply-family)
  - [apply](#apply)
  - [lapply](#lapply)
  - [sapply](#sapply)
  - [vapply](#vapply)

## apply

The `apply` function in R is primarily used for matrices and arrays. It takes a matrix or array as input, along with a margin (1 for rows, 2 for columns) and a function to be applied. The function is then applied to each row or column of the matrix or array, and the results are returned in a vector or matrix.

This makes `apply` a powerful tool for performing operations on entire rows or columns of data, such as calculating summary statistics, applying transformations, or filtering elements.

```R
# Creating matrix
my_matrix <- matrix(1:9, nrow = 3)

# Calculate the sum of each row
row_sums <- apply(my_matrix, 1, sum)

# Calculate the mean of each column
column_means <- apply(my_matrix, 2, mean)

# Apply a custom function to each element
squared_elements <- apply(my_matrix, 1:2, function(x) x^2)
```

## lapply

The `lapply` function in R is primarily used for lists. It takes a list as input, along with a function to be applied. The function is then applied to each element of the list, and the results are returned in a list.

This makes `lapply` a versatile tool for performing operations on each element of a list, such as applying transformations, filtering elements, or extractign specific values. It is especially useful when dealing with nested lists or complex data structures.

```R
# Creating a list
my_list <- list(a = 1:5, b = letters[1:3], c = c(TRUE, FALSE))

# Calculate the length of each element
lenghts <- lapply(my_list, length)

# Convert all elements to uppercase (if applicable)
uppercase <- lapply(my_list, toupper)

# Extract the first element of each element
first_elements <- lapply(my_list, function(x) x[1])
```

Output:

```
> lenghts
$a
[1] 5

$b
[1] 3

$c
[1] 2


> uppercase
$a
[1] "1" "2" "3" "4" "5"

$b
[1] "A" "B" "C"

$c
[1] "TRUE"  "FALSE"


> first_elements
$a
[1] 1

$b
[1] "a"

$c
[1] TRUE
```

## sapply

The `sapply` function in R is a simplified version of `lapply` that attempts to simplify the output based on the return type of the applied function. It takes a list as input, along with a function to be applied. The function is then applied to each element of the list, and the results are returned in a vector or matrix, depending on the consistency of the return values.

This can often make the output more readable and easier to work with compared to `lapply`, especially when the applied function returns atomic vectors of the same length.

```R
# Creating a list
my_list <- list(a = 1:5, b = letters[1:3], c = c(TRUE, FALSE))

# Calculate the length of each element
lenghts <- sapply(my_list, length)

# Convert all elements to uppercase (if applicable)
uppercase <- sapply(my_list, toupper)

# Extract the first element of each element
first_elements <- sapply(my_list, function(x) x[1])
```

Output:

```
> lenghts
a b c
5 3 2
> uppercase
$a
[1] "1" "2" "3" "4" "5"

$b
[1] "A" "B" "C"

$c
[1] "TRUE"  "FALSE"

> first_elements
     a      b      c
   "1"    "a" "TRUE"
```

## vapply

The `vapply` function in R is a more flexible version of `sapply` that allows you to specify the expected return type of the applied function. This can be useful when you want to ensure that the output is of a specific data type, or when you want to control the dimensions of the output.

By providing a `FUN.VALUE` argument, you can specify the desired return type and dimensions, and `vapply` will automatically coerce the results to match this specification. This can help to avoid unexpected data types or dimensions in your output, making your code more robust and predictable.

This also makes it so that R throws an error if the output doesn't match the desired output. This makes `vapply` a more recommended option over `sapply`.

```R
# Creating a list
my_list <- list(a = 1:5, b = letters[1:3], c = c(TRUE, FALSE))

# Calculate the length of each element
lenghts <- vapply(my_list, length, FUN.VALUE = numeric(1))

# Convert all elements to uppercase (if applicable)
uppercase <- vapply(my_list, toupper, FUN.VALUE = character(1))

# Extract the first element of each element
first_elements <- vapply(my_list, function(x) x[1], FUN.VALUE = character(1))
```

Output:

```
> lenghts
a b c
5 3 2
> uppercase <- vapply(my_list, toupper, FUN.VALUE = character(1))
Error in vapply(my_list, toupper, FUN.VALUE = character(1)) :
  values must be length 1,
 but FUN(X[[1]]) result is length 5
> first_elements <- vapply(my_list, function(x) x[1], FUN.VALUE = character(1))
Error in vapply(my_list, function(x) x[1], FUN.VALUE = character(1)) :
  values must be type 'character',
 but FUN(X[[1]]) result is type 'integer'
```
