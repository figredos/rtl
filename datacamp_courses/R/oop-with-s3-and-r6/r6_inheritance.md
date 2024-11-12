# R6 inheritance

Inheritance is a fundamental concept in object-oriented programming that allows classes to inherit properties and methods from other classes. This creates a hierarchical relationship between classes, where a subclass (derived class) can reuse and extend the attributes and behaviours or its parent class (base class).

Inheritance promotes code reusability, modularity, and abstraction. It enables you to create a more organized and maintainable codebase by avoiding duplication and defining common functionality in a single place.

- [R6 inheritance](#r6-inheritance)
  - [Propagating functionality with inheritance](#propagating-functionality-with-inheritance)
  - [Embrace, extend, override](#embrace-extend-override)
  - [Multiple levels of inheritance](#multiple-levels-of-inheritance)

## Propagating functionality with inheritance

Inheritance as mentioned before, allows other classes to be created based on an existing class. They have the same methods and arguments, with parent classes being the ones inherited from, and child classes being the ones inheriting the methods and arguments.

You create a child class by setting the `inherit` argument to the factory of the desired parent class. Children get all functionality byt the converse it not true. There is also an `inherits` function that gets two arguments and returns a logical corresponding to an inheritance relationship between objects.

## Embrace, extend, override

Simply creating the new class isn't useful, you need to add something by either overwriting or extending existing methods in the parent class. To overwrite, simply create new elements with the same name as the original ones, whereas extending is done by using the `super$` keyword.

This keyword is used to access the data from the parent class, making it so that a method can complement what the original one has done.

## Multiple levels of inheritance

A class can have a line of inheritance, being the same object as its parent, its grandparent, and so on. This is simply done by using the child as a parent by another class. The children classes only have access to their direct parent, making it so that they can't use their grandparent's methods and elements.

There are workarounds for doing this. One way to do so is by creating an active binding that accesses the parent class. The method should just return `super$`, making the grandparent's method being accessible throughout the "lineage".
