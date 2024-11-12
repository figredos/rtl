# What is OOP

Object-Oriented Programming ia a programming paradigm that models real-world entities as objects. These objects have properties (attributes) and behaviours (methods). OOP promotes code reusability, modularity and maintainability through concepts like inheritance, polymorphism, and encapsulation.

Inheritance allows classes to inherit properties and methods from other classes, while polymorphism enables objects of different classes to be treated as if they were of the same type. Encapsulation ensures that data is protected and accessed only through defined methods, promoting data integrity.

Although OOP is an essential concept in programming, there are some caveats when it comes to using it with R. Most times you shouldn't use it, it doesn't have great performance, and it can be very convoluted when working with many objects, making it not great for using it within a data analysis context. The best approach for using OOP in R is very specific to when you're using few objects and understand them intrinsically, or when working with APIs.

- [What is OOP](#what-is-oop)
  - [Functional mindset vs Object oriented mindset](#functional-mindset-vs-object-oriented-mindset)
  - [The 9 systems](#the-9-systems)
  - [Distinguishing classes in R](#distinguishing-classes-in-r)
  - [Assigning classes](#assigning-classes)

## Functional mindset vs Object oriented mindset

When working with functions, the first step would be thinking what the function's functionality is, then the objects that will be passed to the function (arguments), and finally you think about what is going to come out of the function as its return.

By contrast, when working with an object oriented mindset, the first step will be what objects will be used, then the data you need to describe the object, and finally you think about the functionality of the object (methods, which are just functions in an OOP context).

## The 9 systems

In the case of object oriented programming in R, there are 9 different options of packages you can use to apply this paradigm:

- **R5**: Experimental system that never made into real world use before being abandoned.
- **mutatr**: Experimental system that never made into real world use before being abandoned.
- **OOP**: Defunct and no longer available.
- **proto**: Had a brief moment of popularity, as it was used as the underlying system in early versions of the ggplot2 package, but it's no longer used.
- **R.oo**: Has been around for years, but never really took off.
- **S3**: Introduced in the third version of `S`, the precursor of R, its been around since the 1980's, being completely mature and still in wide use. It only implements one feature of OOP, that is the ability to have functions work in different ways on different types of objects.
- **S4**: Introduced in the fourth version of `S`, its also been around for years, also completely mature and has a lot of code built to it. It's a more complex and complete implementation of OOP features in R.
- **ReferenceClasses**: ReferenceClasses are an attempt to create a system that behaves similarly to popular object-oriented languages like Java or C#. You get powerful features like encapsulation and inheritance.
- **R6**: 6 covers much of the same ground as ReferenceClasses but does so in a simpler way.

## Distinguishing classes in R

R has many ways of checking what type a certain object is of. There is the most common way of doing it, by simply using the `class()` function, and passing the object you desire to find the type of to it. This however imposes a problem when a class has been overwritten. To counter that, you are posed with other options such as `type_of()`, that checks what data type the object is, or what it's composed of (in case of a matrix, or vector). There are other ways such as `mode` or `storage.mode` but their functionality is supplied by the methods above.

## Assigning classes

As mentioned before, you can change an objects class, by assigning a new value to a call of the `class()` function.

```R
# Creating vector
x <- c(1, 2, 3)

# Will output "numeric"
class(x)

# Overwriting class
class(x) <- "numeric_vector"

# Will output "numeric_vector"
class(x)
```

There are some ways of checking the implicit class of a vector or datatype such as `x`, one is by using `type_of()`, and others would be by using functions such as the `is*()` family of functions.
