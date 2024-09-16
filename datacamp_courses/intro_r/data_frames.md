# DataFrames

DataFrames in R are a fundamental data structure used to store and manipulate tabular data. They are essentially two-dimensional data structures where data is organized into rows and columns.

Each row represents an observation or record, and each column represents a variable or feature. DataFrames are flexible and can accommodate a variety of data types within their columns, including numeric, character, logical, and factors.

This versatility makes them a powerful tool for data analysis and manipulation tasks in R.

- [DataFrames](#dataframes)
  - [Str](#str)
  - [Creating DataFrames](#creating-dataframes)
  - [Selecting elements from DFs](#selecting-elements-from-dfs)
  - [Sorting DataFrames](#sorting-dataframes)

## Str

The `str` function in R is a versatile tool for examining the structure of an object, including data frames. When applied to a data frame, it provides a concise overview of the object's dimensions (number of rows and columns), the data types contained within each column, and a sample of the first few values in each column.

This information is invaluable for understanding the data's organization, identifying potential inconsistencies, and ensuring that the data is in the correct format for further analysis. By using `str`, you can quickly gain insights into the characteristics of your data frame and make informed decisions about how to proceed with your data analysis tasks.

```R
str(mtcars)
```

Output:

```
'data.frame':   32 obs. of  11 variables:
 $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
 $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
 $ disp: num  160 160 108 258 360 ...
 $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
 $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
 $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
 $ qsec: num  16.5 17 18.6 19.4 17 ...
 $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
 $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
 $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
 $ carb: num  4 4 1 1 2 1 4 2 2 4 ...
```

## Creating DataFrames

Creating a DataFrame in R is a straightforward process involving the `data.frame()` function. This function takes a list of vectors as input, where each vector represents a column in the DataFrame.

This vectors should be of equal length to ensure consistent data structure. The resulting DataFrame will have rows representing individual observations, with each row containing values from the specified columns

```R
# Creating vectors
language_names <- c("c", "python", "r")
ages <- c(52, 35, 31)
countries <- c("United States", "Netherlands","New Zealand")

# Creating DataFrame
programming_languages_df <- data.frame(Name = language_names, Age = ages, Countries = countries)

# Showing DataFrame
programming_languages_df
```

Output:

```
    Name Age     Countries
1      c  52 United States
2 python  35   Netherlands
3      r  31   New Zealand
```

## Selecting elements from DFs

Selecting elements from a DataFrame in R involves specifying the desired rows and columns using various indexing methods. You can use numeric indices to select specific rows or columns, logical vectors to filter based on conditions, or character strings to select columns by name. For example, to extract the first row of the DataFrame above, we could use `programming_languages_df[1,]`.

Conversely, to select only the "Name" column we could use one of two methods, with both yielding the same results, `programming_languages_df[,"Names"]` or `programming_languages_df$Names`.

Additionally, you can combine the methods for selecting columns and rows to select specific subsets of the data based on the analysis needs.

## Sorting DataFrames

Sorting DataFrames in R is a common task for organizing and analysing data. The `order()` function is often used to create an index of sorted values, which can then be used to rearrange the DataFrame.

For example, to sort the `programming_languages_df` shown above, we can use `programming_languages_df[order(programming_languages_df$Age)]` to sort the DataFrame based on the sorted "Age" column's indexes.
