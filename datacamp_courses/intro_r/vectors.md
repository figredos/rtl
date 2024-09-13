# Vectors

Vectors are one of the fundamental data structures in R. They are ordered collections of elements of the same data type. Elements in a vector are indexed starting from 1.

- [Vectors](#vectors)
  - [Create a vector](#create-a-vector)
  - [Naming a vector](#naming-a-vector)
  - [Operations with vectors](#operations-with-vectors)
  - [Vector selection](#vector-selection)

## Create a vector

To create a vector in R, you use the `c()` function, which stands for "combine". You pass the individual elements as arguments to the function, separated by commas. For example, to create a numeric vector containing the numbers 1, 2, and 3, you would write:

```R
numbers <- c(1, 2, 3)
```

## Naming a vector

In R, you can assign names to individual elements of a vector using the `names` function. This allows you to easily identify and reference specific elements within the vector. To name a vector, you simply assign a character vector of the same length as the original vector to the `names` attribute. For example, to name the elements of the vector `numbers` as first, second and third, you would write:

```R
numbers <- c(1, 2, 3)

names(numbers) <- c("first", "second", "third")
```

## Operations with vectors

In R, you can perform various operations on vectors, including arithmetic operations, logical operations, and statistical functions. For example, to add two numeric vectors element-wise, you can simply use the `+` operator.

To multiply a vector by a scalar you can use the `*` operator. You can also apply logical operators like `>`, `<`, `==`, `!=`, `&&`, and `||` to vectors to create logical vectors indicating whether the corresponding elements meet certain conditions.

Additionally, R provides numerous statistical functions like `mean`, `median`, `sd`, `var`, `min`, and `max` that can be applied to vectors to calculate various statistics.

## Vector selection

Vector selection in R refers to the process of extracting specific elements from a vector based on their indices or logical conditions. You can use square brackets (`[]`) to select elements.

```R
numbers <- c(1, 2, 3, 4, 5)

names(numbers) <- c("first", "second", "third", "forth", "fifth")

numbers[1]  # Returns 1

numbers[2:4]    # Returns 2, 3, and 4

numbers["first"]    # Returns 1

numbers[c(1, 3, 5)] # Returns 1, 3, 5
```

You can also select elements in a vector by comparison.

```R
numbers <- c(1, 2, 3)

numbers >=2 # Returns FALSE, TRUE, TRUE

numbers[numbers >=] # Returns 2, 3
```
