# Intro to basics

R is a programming language and environment for statistical computing and graphics. It is a GNU project which is similar to the S language and environment.

- [Intro to basics](#intro-to-basics)
  - [Arithmetic with R](#arithmetic-with-r)
  - [Variable assignment](#variable-assignment)
  - [Print Variables](#print-variables)
  - [Basic DataTypes](#basic-datatypes)

## Arithmetic with R

In its most basic form, R can be used as a simple calculator. It has a complete set of basic operations:

- Addition: +
- Subtraction: \*
- Division: /
- Exponentiation: ^
- Modulo: %%

The top 5 are pretty simple, but the last one is less known. The modulo returns the remainder of the division of the number to the left by the number on its right.

```R
# Addition
5 + 5

# Subtraction
5 - 5

# Multiplication
3 * 5

# Division
10 / 2

# Exponentiation
2^5

# Modulo
28 %% 6
```

## Variable assignment

In R, variables are assigned values using the assignment operator `<-`. This operator assigns the value on the right-hand side to the variable on the left-hand side. For instance, to assign the number 10 to a variable named `x`, you would write:

```R
x <- 10
```

R is dynamically typed, meaning you don't have to specify the data type of a variable when you create it. The data type is inferred based on the value assigned to it.

## Print Variables

Values can be printed by simply using their value/variables in the console.

## Basic DataTypes

R supports a variety of data types, but some of the most common include:

- Numerics: For storing numbers, both integers and floating-point values.
- Character: For storing text strings
- Logical: For storing Boolean values (TRUE or FALSE)
- Integer: For storing whole numbers
