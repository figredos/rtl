# Loops

Loops are programming constructs used to repeatedly execute a block of code until a certain condition is met. They are essential for automating tasks and performing repetitive calculations. R provides two primary types of loops, the `for` and `while` loops.

- [Loops](#loops)
  - [While loops](#while-loops)
  - [For loops](#for-loops)

## While loops

While loops are code blocks that repeatedly execute a their body as long as a specified condition remais true. Unlike `for` loops, which iterate a predetermined number of times, `while` loops continue to execute until a certain condition is no longer met.

This makes them particularly useful for tasks where the number of iterations is unknown beforehand, such as reading data from a file line by line or performing iterative calculations until a desired outcome is reached.

```R
while (condition) {
    expr
}
```

## For loops

For loops are code blocks used to iterate over a sequence of values and execute a block of code for each value. They are particularly useful when you know in advance the number of times you need to repeat a task.

For example, you could use a `for` loop to iterate over the elements in a vector, list, or data frame, performing a specific operation on each element. The loop continues until it has processed all the values in the sequence.

```R
for (element in iterable) {
    expr
}
```
