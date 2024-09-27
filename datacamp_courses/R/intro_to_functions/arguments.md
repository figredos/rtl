# Function Arguments

In the realm of programming, arguments serve as the essential building blocks for functions. They act as the input values that functions receive, allowing them to perform specific tasks and return meaningful results. Understanding arguments is crucial for effectively utilizing R's vast library of functions and even creating your functions.

- [Function Arguments](#function-arguments)
  - [Default arguments](#default-arguments)
    - [Setting default values to other arguments](#setting-default-values-to-other-arguments)
    - [Setting default arguments to NULL](#setting-default-arguments-to-null)
    - [Setting categorical default arguments](#setting-categorical-default-arguments)
  - [Passing arguments from one function to another](#passing-arguments-from-one-function-to-another)
    - [The `...` operator](#the--operator)

## Default arguments

You can assign default values to function arguments, This means that if a user doesn't provide a value for that argument when calling the function, the default value will be used instead.

```R
add_x_and_y <- function(x, y = 10) {
    x + y
}
```

In the example above, the `y` argument has a default value of 10. If the function is called with `add_x_and_y(5)` the value of y will be 10, and the result will be 15.

### Setting default values to other arguments

You can set the default value of an argument to the value of another argument. This can be useful when arguments are related.

```R
add_x_and_y(x, y = x) {
    x + y
}
```

Here, the default value of y is x. This means that if y is not set when calling the function, its value will be the same as the one for x.

### Setting default arguments to NULL

There are two possible meanings for having the default value of an argument be `NULL`. The first is if the argument is optional, allowing functions to be able to handle different input scenarios. The second possibility is to say that the argument has some special handling and there is more information to be found in the docs.

### Setting categorical default arguments

By passing a character vector in the signature of the function, and using `match.arg()` in the body, we can set the arguments to a series of possible categories described as the elements in the vector.

```R
print_object_color <- function(object, color = c("blue", "red", "white")) {
    paste(object, color, sep = " ")
}
```

## Passing arguments from one function to another

The pipe operator (%>%) in R provides a convenient way to chain function calls together, passing the output of one function as an argument to the next. This can make your code more readable and concise, especially when dealing with complex data transformations.

```R
library(dplyr)

# Create a sample dataframe
df <- data.frame(x = 1.5, y = LETTERS[1:5])

# Chain function calls using %>%
df %>%
    # Adding z column
    mutate(z = x * 2) %>%
    # Only selecting rows where z is greater than 5
    filter(z > 5)
```

### The `...` operator

The `...` (ellipsis) operator in R is a placeholder for an arbitrary number of arguments. It allows you to create functions that can accept a variable number of inputs, making your code more flexible and adaptable.

```R
filter_by_columns <- functions(df, ...) {
    cols <- c(...)
    df %>%
    filter(across(all_of(cols), ~ .x > 0))
}
```

It has some benefits such as less typing and no need to match signatures, and some drawbacks by needing to trust the inner function, and being less obvious to users.
