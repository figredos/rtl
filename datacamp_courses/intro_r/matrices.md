# Matrices

Matrices are two-dimensional arrays of elements of the same data type. They are often used to represent tabular data or linear transformations. In R, matrices are created using the `matrix()` function, which takes arguments specifying the number of rows, columns, the data to be filled into the matrix, and optionally the order of filling (by row or by column).

- [Matrices](#matrices)
  - [Creating matrices](#creating-matrices)
  - [Naming a matrix](#naming-a-matrix)
  - [Adding Rows and Columns](#adding-rows-and-columns)
  - [Selection of matrices elements](#selection-of-matrices-elements)
  - [Arithmetic Operations with Matrices](#arithmetic-operations-with-matrices)

## Creating matrices

As previously said, matrices in R are created by using the `matrix()` function. This function takes some arguments, the `data` as a vector containing the elements to be filled into the matrix, `nrow` the number of rows in the matrix, `ncol` the number of columns in the matrix, `byrow` a logical value indicating whether the matrix should be filled by row (TRUE) or by column (FALSE).

```R
my_matrix <- matrix(1:9, nrow = 3, ncol = 3, byrow = TRUE)
```

## Naming a matrix

In R, you can assign names to the columns and rows of a matrix using the `colnames` and `rownames` functions, respectively. This makes it easier to identify and reference specific elements within the matrix. To assign names to the columns of a matrix, you simply pass a character vector of the same length as the number of columns to the `colnames` function.

Similarly, to assign names to the rows, you pass a character vector of the same length as the number of rows to the `rownames` function.

```R
colnames(my_matrix) <- c("column1", "column2", "column3")

rownames(my_matrix) <- c("row1", "row2", "row3")
```

## Adding Rows and Columns

To add columns or rows to an existing matrix in R, you can use the `cbind` and ` rbind` functions, respectively. The `cbind` function combines matrices or vectors column-wise, while the `rbind` function combines them row-wise.

Adding columns:

```R
new_column <- c(10, 20, 30)
my_matrix <- cbind(my_matrix, new_column)
```

Adding rows:

```R
new_row <- c(40, 50, 60)
my_matrix <- rbind(my_matrix, new_row)
```

## Selection of matrices elements

To select specific elements from a matrix in R, you can use square brackets (`[]`) with indices specifying the row and column positions. For example, `my_matrix[1, 2]` extracts the element at the first row and second column. You can also use logical indexing to select elements based on conditions.

For instance, `my_matrix[my_matrix > 5]` extracts elements greater than 5. Additionally, you can use functions like `diag` to extract the diagonal elements, `t` to transpose the matrix, and `solve` to find the inverse of a square matrix.

## Arithmetic Operations with Matrices

In R, you can perform various arithmetic operations on matrices, including addition, subtractions, multiplication, and division. To add or subtract two matrices of the same dimensions, you simply use the `+` or `-` operators, respectively. Matrix multiplication is performed using the `%*%` which calculates the dot product of the corresponding rows and columns.

Scalar multiplication and division can be performed by multiplying or dividing each element of the element by the scalar. However, matrix division is not defined in the same way as scalar division, and it requires finding the inverse of a matrix using the `solve` function.
