# Return value and scope

Return values and scope in functions are fundamental concepts in programming. A return value is a value that a function sends back to the part of the code that called it. This value can be used for further calculations or to display output. The scope of a variable determines where it can be accessed within a program.

Variables declared inside a function have local scope, meaning they can only be used within that function. Variables declared outside functions have global scope, meaning they can be accessed anywhere in the program.

- [Return value and scope](#return-value-and-scope)
  - [Returning values early in functions](#returning-values-early-in-functions)
  - [The `invisible` function](#the-invisible-function)
  - [Returning Values in R functions](#returning-values-in-r-functions)
  - [Returning multiple values](#returning-multiple-values)
    - [Multi-assignment with `%<-%`](#multi-assignment-with--)
    - [Using attributes](#using-attributes)
  - [Environments](#environments)
  - [Scope and Precedence](#scope-and-precedence)

## Returning values early in functions

In programming, returning values early early from functions can significantly enhance code efficiency and readability. This practice involves exiting a function as soon as a specific condition is met, preventing unnecessary computations. By identifying conditions that lead to a definitive outcome, you can avoid redundant calculations and potentially improve the overall performance of your code.

For instance, if a function is designed to calculate the factorial of a number, and the input is zero, it's unnecessary to iterate through the entire calculation. Returning the value 1 immediately would be more efficient.

## The `invisible` function

The invisible function in R is a powerful tool for controlling the output behaviour of functions. When applied to a return value, it suppresses the printing of a value to the console. This is particularly useful when the return value is intended for further processing or assignment to variables rather than direct display. By using invisible, you can maintain a cleaner and more focused output environment, making it easier to interpret and analyze the results of your code.

## Returning Values in R functions

To return values from functions in R, you typically employ the `return` statement. This statement is followed by the value you wish to send back to the calling context. THe returned value can be of any data type, including scalars, vectors, lists, dataframes, or even custom objects. The other method is to leave the desired return value as the last line of the code.

```R
# Using the result function
sum_x_y <- function(x, y) {
    result <- x + y
    return(result)
}

# Simply leaving the result word as the last line
sum_x_y <- function(x, y) {
    result <- x + y
    result
}
```

## Returning multiple values

R functions don't really offer ways of returning multiple values in a single function, this has workarounds, like by using lists. There are ways to improve this, either by using techniques such as multi-assignment or accessing attributes.

### Multi-assignment with `%<-%`

By using the `%<-%` operator from the zeallot package, we can do multi-assignment in R. This operator enables you to assign multiple values returned by a function to corresponding variables in a single streamlined statement. This approach enhances code readability and reduces the need for intermediate variables.

```R
library(zeallot)

my_function <- function(x, y){
    sum <- x + y
    product <- x * y
    attr(sum, "product") <- product

    return(sum)
}

result <- my_function(5, 3)

c(sum, product) %<-% result
```

In the example, `sum` has a value of 8, and `product` has a value of 15.

### Using attributes

Another effective technique for returning multiple values involves the use of attributes. Attributes are metadata or additional information that can be attached to a returned value. By setting attributes within the function, you can associate auxiliary data or context-specific details with the primary result. These attributes can be accessed and manipulated using the `attr` function, providing a structured way to retrieve and utilize the supplementary information.

```R
attr(result, "product")
```

By using the last example's result, we can access the value of an attribute through its name.

## Environments

Environment in R are distinct from list in their structure and behaviour. While lists are ordered collections of elements, environments are more akin to name-value pairs, associating names with corresponding values. This allows environments to function as namespaces, providing hierarchical structure for organizing variables and functions.

To convert a list into an environment simply use the `list2env` function.

Parent environments form a chain of linked environments, where each environment has a parent environment. This hierarchy allows for scoping rules, determining the visibility of variables and functions based on their location in the environment chain.

To find the parent environment of a given environment, you can use the `parent.env` function. To search for a variable within an environment or its parent chain, you can employ the `exists` function.

This function takes the name of the variable, and the environment itself. There is an optional argument `inherits` that determines whether the variable is contained within the current environment.

## Scope and Precedence

Scope and precedence are essential concepts in R programming that govern the visibility and evaluation order of variable and expressions. Scope determines the region of code where a variable is accessible. Variables declared within a function have local scope, meaning they are only visible within that function.

Variables declared outside functions have global scope, allowing them to be accessed from anywhere in the program. Precedence establishes the order in which operators are evaluated in an expression. Operators with higher precedence are executed before those with lower precedence. Understanding these concepts is crucial for writing clear, correct, and efficient R code.
