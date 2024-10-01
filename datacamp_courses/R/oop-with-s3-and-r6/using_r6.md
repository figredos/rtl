# Using R6

The R6 package provides a more formal object-oriented programming framework for R. Unlike S3, R6 offers features like inheritance, encapsulation, and public and private methods. This allows for creating more structured and reusable classes, promoting better code organization and maintainability.

R6 also supports methods like `initialize`, `clone`, and `print`, making it easier to manage and work with objects. While R6 might have a steeper learning curve compared to S3, it's well-suited for larger projects or when you need a more robust object-oriented approach.

- [Using R6](#using-r6)
  - [The object factory](#the-object-factory)
  - [Hiding complexity with Encapsulation](#hiding-complexity-with-encapsulation)
  - [Getting and setting active bindings](#getting-and-setting-active-bindings)

## The object factory

The R6 system provides a way of storing data and objects within the same variable, this is done by creating class generators that serve as templates for objects. These generators are also called factories, and they're defined by using the `R6Class.

The first argument of this function is a string representing the name of the class, it should be in `UpperCamelCase`. The second argument is called `private`, and it stores the objects data, It's always a list with named arguments.

```R
# Loading the R6 library
library(R6)

# Creating a R6 class
thing_factory <- R6Class(
    "ThingFactory",
    private = list(
        a_field = "a value",
        another_field = 123,
    )
)
```

There are also other important arguments, `public` and `active` that will be discussed further down this file. Finally, to create instances of R6 objects, use the factory's name followed by `$new()`, using the `new` method of the class, that is native to any R6 class.

```R
thing_1 <- thing_factory$new()
```

## Hiding complexity with Encapsulation

Encapsulation is the term used for separating the implementation of the objects from its interface. Implementation's details are stored in the aforementioned `private` element of the class. On the other hand, the user interface details are stored in the `public` element of the class.

The `public` argument also stores data within a list with named arguments.

To access the data stored within the `private` element of the class, it isn't as simple as just accessing from outside of the class, instead you need to set methods within the `public` element, and access the data using `private$`. This however can't be done from outside of methods. Conversely, you can access elements defined within the `public` element by using `self$`.

The organization of the class should be storing data in the private element and functions in the public.

Much like the `new` method, other methods are using in the same manner, using the new object's name followed by `$` and the method's name. There are also other "special" methods like `initialize` that allows for initialization of fields when creating a new object, this method should be set within the `public` element of the class.

```R
# Loading the R6 library
library(R6)

# Creating a R6 class
thing_factory <- R6Class(
    "ThingFactory",
    private = list(
        a_field = NULL,
        another_field = NULL
    )
    public = list(
        initialize = function(a_field, another_field) {
            if (!missing(a_field)) {
                private$a_field <- a_field
            }
            if (!missing(another_field)) {
                private$another_field <- another_field
            }
        }
    )
)

# Instantiating and initializing class's fields
an_object <- thing_factory("a value", 123)
```

## Getting and setting active bindings

Finally, the other very important argument for R6 classes, is the `active` argument. This field, like the others, is a list with named arguments, this on the other hand offers a way of implementing getters and setters. In R6, controlled access to private fields is achieved through active bindings (getters/setters), these bindings are defined like functions but accessed like data variables (without calling the function).

All public, private, and active arguments should have different names. In the case of active bindings, used to set values to private elements, the names still need to be different so use `..` before the names of private arguments to differentiate between these elements's arguments.

```R
# Loading the R6 library
library(R6)

# Creating a R6 class
thing_factory <- R6Class(
    "ThingFactory",
    private = list(
        ..a_field = "a value",
        ..another_field = 123,
    ),
    active = list(
        a_field = function(value) {
            if (missing(value)){
                private$..a_field
            }
            private$..a_field <- value
        },
        another_field = function(value) {
            if (missing(value)){
                private$..another_field
            }
            private$..another_field <- value
        }
    )
)
```
