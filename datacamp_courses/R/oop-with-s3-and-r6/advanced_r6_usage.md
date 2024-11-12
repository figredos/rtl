# Advanced R6 Usage

Advanced R6 usage involves leveraging the package's features to create complex and flexible object-oriented systems. This includes utilizing environments to share data between instances of a same object, cloning R6 objects, and shutting a class down by severing its connection to a possible database, using its finalize method.

- [Advanced R6 Usage](#advanced-r6-usage)
  - [Environments, Reference Behaviour, and Shared Fields](#environments-reference-behaviour-and-shared-fields)
  - [Cloning R6 objects](#cloning-r6-objects)
  - [Shutting it down](#shutting-it-down)

## Environments, Reference Behaviour, and Shared Fields

Environments as well as lists can be used to store other variables. Environments are named collections of objects, such as functions, variables, and data frames, that are organized in a hierarchical structure.

The advantage of using dataframes comes to how they are stored in memory. Lists use a copy by value structure, meaning, when you copy a variable, each version of the variable has its own copies of the values. In contrast, environments use copy by reference, meaning, when you copy them, each copy refers to the same copy of the values.

Environments can be created by using the `new.env()` function, or by converting a list into an environment using `list2env()`. Environments are created empty when using `new.env`, and you add elements to it the same way as you would to a list, either by using `$` or `[[]]`. This means that if you copy an environment, and change them, the copy also changes, because they are referencing the same elements in memory.

When using R6Classes, you can take advantage of this to share some data between all instances of a single object. By convention this should be stored in an argument from the `private` element called `shared`. In this argument you should create an environment, create any desired variable, and return said environment.

## Cloning R6 objects

Just copying R6 objects is not always the desired behaviour, therefore, all R6 classes have a method named "clone" to allow independent copies. To clone, assign the clone method to a new variable. This eliminates the copy by reference that R6 classes that is inherent to these objects. This doesn't work for internal classes, unless you set the `deep` argument to true.

## Shutting it down

Its dangerous to simply delete an R6 object if it connects to a database or file. Similarly to the `initialize` method, there is a method called `finalize`, this method allows custom behaviour when an object is being disposed.

Finalize is defined in the public element, and it should, by convention, take no arguments. It's automatically called when the object is garbage collected by R's memory management system.

Its also worth mentioning that an object can be deleted from memory using `rm` and `gc` and can force garbage collection to take place.
