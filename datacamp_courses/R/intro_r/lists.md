# Lists

Lists in R are versatile data structures that can hold elements of different data types within a singe object. Unlike vectors, which are restricted to a single data type, lists can contain a mix of characters, numbers, logical values, and even other lists or data frames. This flexibility makes lists ideal for storing complex and heterogeneous data.

- [Lists](#lists)
  - [Creating lists](#creating-lists)
  - [Selecting elements from lists](#selecting-elements-from-lists)

## Creating lists

Creating lists in R is straightforward. You use the `list()` function, enclosing each element within parentheses and separating them with commas. Elements can be of different data types, allowing you to store a variety of information within a single object.

```R
my_list <- list("string", c(1, 2, 3), TRUE)
```

The order in which you add elements to the list determines their position, which you can use to access them later using indexing.

## Selecting elements from lists

Selecting elements from lists in R is done using double square brackets and the corresponding index. The index refers to the position of the element within the list, starting from 1.

```R
# Creating list
my_list <- list("string", c(1, 2, 3), TRUE)

# Selecting the first element in the list
my_list[1]
```

You can also select multiple elements using a vector of indices. Additionally, you can extract elements based on their names if the list has named elements. This is done using the `$` operator followed by the name of the element.

```R
# Creating list
my_list <- list(String = "string", Vector = c(1, 2, 3), Logical = TRUE)

# Selecting second element from list's second element
my_list$Vector[2]
```

Output:

```
[1] 2
```
