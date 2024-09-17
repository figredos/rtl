# Conditionals and Control Flow

Conditionals and control flow are essential concepts in programming that allow you to make decisions and determine the order in which code is executed. Conditionals, such as `and` statements, enable programs to evaluate conditions and execute different code blocks based on the results.

Control flow statements, like `if else` blocks allow separating code when a certain condition is met. By effectively using conditionals and control flow, you can create programs that are more flexible, efficient, and capable of handling various scenarios.

- [Conditionals and Control Flow](#conditionals-and-control-flow)
  - [Relational operators](#relational-operators)
  - [Logical operators](#logical-operators)
  - [Conditional statements](#conditional-statements)

## Relational operators

Relational operators in R are used to compare values and return a logical value (TRUE or FALSE). They are essential for making decisions and controlling the flow of the code. Common relational operators include:

- `==` - equality: If two objects are equal, returns `TRUE` else `FALSE`. Can be used to compare numbers to strings.
- `!=` - inequality: Direct opposite of the equality operator.
- `<` - less than: If one object is less than the other, returns `TRUE` else `FALSE`.
- `>` - greater than: If one object is greater than the other, returns `TRUE` else `FALSE`.
- `<=` - less or equal than: If one object is less or equal than the other, returns `TRUE` else `FALSE`.
- `>=` - greater or equal than: If one object is greater or equal than the other, returns `TRUE` else `FALSE`.

Relational operators can also be used with matrices and vectors. When used, they return a series of logical values by comparing the object element-wise to the vector.

Its also important to note that when comparing string values, the ASCII value is used for each character.

## Logical operators

Logical operators are used to combine logical values (TRUE or FALSE) and return a new logical value.They are essential for creating complex conditions and controlling the flow of the code. Common logical operators include:

- `&` - AND: Logical and (both conditions must be true)
- `|` - OR: Logical or (only one condition must be true)
- `!` - NOT: Logical not (reverses the logical value)
- `&&` - logical AND: This operator evaluates its operands from left to right. If the first operand is false, the second operand is not evaluated. This is known as short-circuit evaluation. It's particularly useful when you want to avoid unnecessary computations.
- `||` - logical OR: Similar to `&&`, this operator also performs short-circuit evaluation, if the first operand is true, the second operand is not evaluated

By using logical operators in conjunction with conditional statements and relational operators, you can create more sophisticated and flexible scripts that can handle a wider range of scenarios and make informed decisions based on your data.

## Conditional statements

Conditional statements in R are essential for controlling the flow of the code based on specific conditions. They allow you to make decisions and execute different code blocks depending on whether a certain condition is true or false.

The most common conditional statement is the `if` statement, which checks a condition and executes a block of code if the condition is true. You can also use `else` to specify a block of code to execute if the condition is false. There is also the `else if` statement that allows a second condition to be checked if the initial `if` conditions amounts to false. Additionally, R provides the `ifelse` function for concisely performing conditional assignments.

By effectively using conditional statements, you can create more flexible and dynamic R scripts that can adapt to different scenarios and data.

```R
if (condition1) {
    expr
} else if (condition2) {
    expr
} else {
    expr
}
```

```R
x <- c(6:-4)
sqrt(x)  #- gives warning
sqrt(ifelse(x >= 0, x, NA))
```
