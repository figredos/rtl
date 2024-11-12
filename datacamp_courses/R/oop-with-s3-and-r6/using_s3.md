# Using S3

The S3 package is a fundamental mechanism in R for creating generic functions and methods. It provides a flexible way to define functions that can dispatch to different methods based on the class of the first argument. This allow for code reuse and customization, as the same function can be applied to objects of different classes with tailored behaviors.

S3 is often used for creating custom data structures and methods, extending existing R functions and implementing domain-specific languages. While it's a powerful tool, S3's simplicity can sometimes lead to less formal object-oriented structures compared to more advanced systems.

- [Using S3](#using-s3)
  - [Generics and methods of function overload](#generics-and-methods-of-function-overload)
  - [Creating a S3 function](#creating-a-s3-function)
    - [Creating a generic](#creating-a-generic)
    - [Creating a method](#creating-a-method)
    - [Creating default method](#creating-default-method)
  - [Methodical thinking](#methodical-thinking)
  - [Method lookup for primitive generics](#method-lookup-for-primitive-generics)
  - [More than one class](#more-than-one-class)

## Generics and methods of function overload

Having different behaviours fo functions under different kinds of input is called Function Overload, and its main purpose is to simplify code. The S3 system does this by splitting functions into two parts, a generic function, and a method function for each class.

S3 methods follow two main conditions:

- The name of each method must be the name of the generic, then a dot, then the class of the variable
  - `generic.class`
- The arguments to the method must include all the arguments to the generic
  - `generic(x, ...)` : `generic.class(x, ..., other_arg)`

When creating these functions, its considered good practice to include `...` on both the generic and the method functions. Also the naming of the functions must always follow either `snake_case` or `lowerCamelCase` (preferably the former), and should never be of `leopard.case`.

To check whether a function is a S3 generic of a S3 method, use `is_s3_generic` and `is_s3_method` respectively, from the `pryr` package.

## Creating a S3 function

Creating a S3 function is a simple process, it consists of two parts, as mentioned before. First a generic then specific methods.

### Creating a generic

To create a generic function, write a function like usual, pass it arguments, and name it. The only thing that sets a generic apart from a normal function, is that the body needs to contain a call of `UseMethod("generic name")`. The first argument is generally `x`, and as said before, you should pass `...` as an argument.

```R
any_generic <- function(x, ...){
    UseMethod("any_generic")
}
```

### Creating a method

Writing a method function is simpler than creating a generic, being closer to creating a normal function. This comes in the form of setting the datatype the function is meant for after the generic's name. The rest of the function is done normally.

```R
any_generic.numeric <- function(x, ...){
    x^2
}
```

### Creating default method

There is also the case of the datatype the user wants to use, not being defined for the generic. S3 has a form of dealing with this potential problem, by creating a default method, it will be used to handle the function call, providing a fallback mechanism when a more specific method is not available.

```R
print_object <- function(x) {
    UseMethod("print_object")
}

print_object.default <- function(x) {
    cat("Default method for printing:", class(x), "\n")
    print(x)
}
```

## Methodical thinking

It's useful to know which methods are available for any given S3 method. To do this, use the `methods` function, that lists what methods any S3 function has, and what are them. The same can be done in the reverse, for instance, if you have a class and want to know which arguments are available for that class of object, you simply pass the desired object class to the `method` function in the argument `class`. This however returns both the S3 and the S4 methods, if you only want to see the S3 methods, you should use the `.S3methods`, similarly use `.S4methods` to find only S4 methods.

## Method lookup for primitive generics

Primitive generics in R are a special type of generic function that are built into the R language itself. They act as intermediaries between R and its underlying C code. Functions like `exp`, `sin`, `+`, `-`, `if`, `for`, are all examples of primitive generics. To see a list of primitive generics, simply use .S3primitives, its always preferable to use them since they offer more optimized code. It's also important to note that, although their class can be changed by assigning new values to `class`, they are read in a different way and will never throw errors unlike other objects/functions.

## More than one class

Objects can have more than one class, and they can be assigned by using `class` and setting instead of a string, a vector of strings, with each one being a class said object belongs to. Most generic classes always come last, with more specific classes always coming first. This allows the usage of the functions from the `is.*` family, or even `inherits(object, type)` that simply says if an object has the type that is passed as an argument. `inherits` is slower than a more specific function. This also allows using `NextMethod` that calls the method for a more specific type the object has.
