# Writing functions

Functions are fundamental units of code in R, encapsulating a sequence of instructions that peform a specific task. They allow you to break down complex problems into smaller, more manageable components, promoting code reusability and organization.

By defining functions, you can avoid redundant code, enhance readability, and facilitate collaboration.

- [Writing functions](#writing-functions)
  - [Calling functions](#calling-functions)
    - [Using named arguments](#using-named-arguments)
    - [Only name rare arguments](#only-name-rare-arguments)
    - [Order of arguments](#order-of-arguments)
  - [Benefits of Using Functions](#benefits-of-using-functions)
  - [Basic Usage](#basic-usage)
    - [Functions sections](#functions-sections)
  - [Best practices](#best-practices)

## Calling functions

When calling functions, it's crucial to adhere to good practices to ensure clarity, readability and maintainability of the code.

### Using named arguments

One important practice is to use named arguments whenever possible. This explicitly associates each argument with its corresponding parameter, making the code more self-documenting and reducing the likelihood of errors.

```R
# Instead of
my_func(10, "hello")

# Use
my_func(x = 10, y = "hello")
```

### Only name rare arguments

However, it's generally recommended to use named arguments only for less common or optional parameters. For frequently used arguments using unnamed arguments can be more can be more concise and readable. For instance, the `mean` function always should receive the `x` argument, making naming it unnecessary, as for other arguments such as `na.rm` naming would be recommended

```R
# Instead of
mean(c(1, 2, 3), FALSE)

# Or even
mean(x = c(1, 2, 3), na.rm = FALSE)

# Use
mean(c(1, 2, 3), na.rm = FALSE)
```

### Order of arguments

When calling a function, it's generally best to pass arguments in the same order as they are declared in the function definition. This ensure that the arguments are matched correctly to their corresponding parameters, making your code more readable and less prone to errors.

Using named arguments can provide flexibility, but it's often unnecessary when the argument order is straightforward (as discussed above). By following the natural order of the function's parameters, you make your coe more intuitive for both yourself and other who might read it later.

## Benefits of Using Functions

- **Improved code organization**: Functions break down complex tasks into smaller, manageable units, making your code easier to understand and maintain.
- **Enhanced code reusability**: By defining functions, you can avoid writing the same code multiple times, saving time and effort.
- **Increased readability**: Functions provide a clear and concise way to describe the purpose of a block of code.
- **Enhanced collaboration**: Functions can be shared and reused among team members, improving collaboration and efficiency.

## Basic Usage

Functions are defined using the function keyword followed by a list of arguments and the function body enclosed in curly braces. The arguments are the inputs that the function takes, while the body contains the instructions to be executed.

### Functions sections

- **Header or Signature**: This is the first line of the execution, which includes the function name and a list of arguments enclosed in parentheses.

```R
my_function <- function(arguments){}
```

- **Body**: This is the section enclosed in curly braces that contains the instructions to be executed when the function is called.

```R
my_function <- function(arguments){
    function body
}
```

- **Return value**: A function may or may not return a value. If it does, the value is specified using the return keyword, or by specifying the argument as the last line of the function body.

To call a function, you provide the function name and the provided arguments. The function will then execute its instructions and return the specified value, if any.

## Best practices

Some best practices for using and writing functions include:

- Functions names should contain a verb, being more important to know what it does instead of it looking good.
- Understanding code is more important than typing it.
- Putting arguments in a sensible order when creating a function, data arguments should precede detail arguments
- There are as mentioned two types of arguments, data arguments are the values that are computed upon, whereas detail arguments, are details on how the computation should be performed.
