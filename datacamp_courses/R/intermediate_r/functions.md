# Functions

Functions are reusable blocks of code that perform specific tasks. They allow you to organize your code into smaller, more manageable units, making it easier to read, understand, and maintain. Function can take input arguments, perform calculations or operations on those arguments, and return a result.

This modular approach promotes code reusability and efficiency, as you can define a function once and call it multiple times throughout the script.

- [Functions](#functions)
  - [Creating functions](#creating-functions)
  - [Required and Optional Arguments](#required-and-optional-arguments)
  - [Documentation](#documentation)
  - [Scope](#scope)
  - [Anonymous functions](#anonymous-functions)

## Creating functions

To create a function in R, you use the `function` keyword followed by parentheses containing the argument list and curly braces enclosing the function body.

```R
func <- function(arguments) {
    expr
}
```

A function can return a value in one of two ways, either with the last line of the function, or with the `return()` function.

## Required and Optional Arguments

Arguments are values that are passed to a function when it's called. They provide the function with the data it needs to perform its calculations. There are two different types of arguments, **required arguments** that must be provided when the function is called, and **optional arguments**.

Some other important things to note about arguments are their order and their names. The order in which arguments are passed to function matters. Required arguments must be passed in the correct order, while optional arguments can be passed in any order. Finally, you can pass arguments to a function by their names, which can make your code more readable.

```R
# Function that returns the sum of the arguments
sum <- function(x, y) {
    x + y
}

# Calling function with arguments names
sum(x = 10, y = 5)
```

## Documentation

Reading documentation is a crucial step in understanding their purpose, arguments, and return values. This documentation can be found in several ways:

- Help pages: by using the `?` operator followed by the function name to access the help page.
- Manuals: R comes with extensive online manuals that cover various topics, including function and packages. You can access these manuals through the help menu in R or by using the `help()` function.

## Scope

Variables defined within a function are local to that function and are not accessible outside.

## Anonymous functions

These are functions without a name, often used as arguments to other functions.
