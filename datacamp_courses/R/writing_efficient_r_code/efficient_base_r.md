# Fine-tuning: Efficient base R

Fine-tuning refers to the process of optimizing R code for performance. While R is generally a high-level language that abstracts away many low-levels details, there are several techniques that can be employed to improve the efficiency of your code.

- [Fine-tuning: Efficient base R](#fine-tuning-efficient-base-r)
  - [Memory allocation](#memory-allocation)
    - [Memory management in R](#memory-management-in-r)
    - [Growing vectors](#growing-vectors)
  - [Vectorization](#vectorization)
  - [Dataframes vs Matrices](#dataframes-vs-matrices)
    - [Memory Allocation](#memory-allocation-1)
    - [Performance implications](#performance-implications)
    - [When to use Matrices v Dataframes](#when-to-use-matrices-v-dataframes)
  - [Best practices for R performance](#best-practices-for-r-performance)

## Memory allocation

### Memory management in R

Unlike many other programming languages, R does not provide explicit memory allocation and deallocation mechanisms. Instead, it employs a dynamic memory management system that automatically allocates and deallocates memory as needed. This approach can be convenient for developers, as it eliminates the risk of memory leaks and simplifies memory management.

While R's automatic memory management is generally efficient, it can become slow if not used carefully, When R allocates memory, it may need to reallocate a larger block of memory if the curren block is insufficient. This process can be time-consuming, especially for frequent allocations and deallocations.

### Growing vectors

One common mistake in R programming is to repeatedly grow a vector by appending elements to it. This approach can lead to significant performance degradation due to frequent reallocations, Each time a vector is grown, R needs to create a new, lager vector and copy the existing elements to it. This can be particularly inefficient for large vectors.

## Vectorization

Vectorization is a fundamental technique in R that involves performing operations on entire vectors or matrices at once, rather than element-by-element. This approach can significantly improve performance by leveraging the efficiency of underlying C or Fortran implementations. Whenever possible, use vectorized functions like `apply`, `mapply`, or `sapply` to avoid loops.

```R
# Creating and pre-allocating vector
x <- vector("numeric", n)

# Applying vectorized function
x <- rnorm(n)

# Applying non-vectorized function
for (i in seq_along(n))
    x[i] <- rnorm(1)
```

## Dataframes vs Matrices

When working with tabular data in R, the choice between matrices and dataframes can significantly impact performance. While both data structures are used to store and manipulate data, they have distinct characteristics that influence memory allocation and computational efficiency.

### Memory Allocation

Matrices are designed to store homogeneous data, typically numeric values. They are allocated in contiguous blocks of memory, which can lead to more efficient memory access and faster computations.

Dataframes are more flexible than matrices, allowing for heterogeneous data types in different columns. This flexibility comes at a cost, specifically being stored as lists of vectors, which can result in fragmented memory allocation and potentially slower access times.

### Performance implications

Matrices are generally more efficient for numerical operations than dataframes. This is because matrix operations can be optimized to take advantage of contiguous memory allocation and vectorized computations. Dataframes, on the other hand, may require more overhead for type checking and coercion, which can slow down operations.

Matrices are often more memory-efficient than dataframes, especially when dealing with large datasets of numeric data. Dataframes can consume more memory due to the overhead of storing column names, data types , and potential fragmentation.

### When to use Matrices v Dataframes

Use matrices when dealing primarily with numeric data and performing frequent numerical operations. Examples include linear algebra, statistical calculations, and machine learning tasks.

Dataframes are used when working with heterogeneous data or when you need more flexibility in terms of data types and column names. Dataframes are often more suitable for data analysis tasks that involve data cleaning, transformation, and visualization.

## Best practices for performance in R 

- **Pre-allocate vectors**: Whenever possible, pre-allocate vectors to their final size before adding elements. This prevents unnecessary reallocations.
- **Use vectorizes solutions**: As said above, R has optimized solutions built in for problems in form of vectors functions, this goes the fastest to highly optimized C and Fortran underlying code.
- **Use specialized data structures**: For specific use cases, specialized data structures like sparse matrices or hash tables can offer more efficient memory usage.
- **Avoid unnecessary copying**: Minimize the number of times data is copied. Use references whenever possible to avoid creating new copies.
