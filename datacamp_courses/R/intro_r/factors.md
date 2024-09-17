# Factors

Factors in R are a specialized data type used to represent categorical data. Unlike numeric or character data, factors store values as integers that correspond to specific levels. These levels are defined as a set of unique values that the factor can take.

Factors are crucial for statistical analysis, particularly when dealing with categorical variables, as they provide a structured way to represent and manipulate these types of data.

- [Factors](#factors)
  - [Creating factors](#creating-factors)
  - [Levels](#levels)
  - [Factors](#factors-1)
  - [Ordered Factors](#ordered-factors)

## Creating factors

Creating factors in R is straightforward using the `factor()` function. This function takes a vector of values as input and returns a factor object. Optional arguments allow you to specify the levels of the factor, ensuring that only valid values are included.

If levels are not explicitly provided, they are inferred from the unique values in the input vector. There are some other optional arguments, such as `labels` that allows specifying custom labels for the factor levels, `exclude` that allows certain values from being considered values in the factor, `ordered` that allows creating an ordered factor, where the levels have a specified hierarchy, and `nmax` limiting the number of levels in the factor, if the number of unique values excedes the maximum, the least frequent values will be excluded.

```R
vol_vector <- c("Low", "Medium", "Medium", "Low", "High")

factor_vol_vector <- factor(vol_vector, ordered = TRUE, levels = c("Low", "Medium", "High"))
```

Just like other data structured, you use square brackets to specify the position of the element you want to retrieve. Keep in mind that the indexing refers to the position of the element within the factor, not the specific level it represents.

## Levels

Levels in R factors are the unique values that a factor can take. They define the categories or groups within the categorical data. Levels are important because they provide a structured way to represent and analyze categorical data, allowing for statistical operations and visualizations that are specific to these types of variables.

They can be set from within the `factors` function or by using the designated `levels` function, that does pretty much the same thing, with the main difference being the ability to change the values that correspond to the current levels of a factor.

```R
temp_vector <- c("hot", "cold", "cold", "cold", "hot", "hot")

temp_factor <- factor(temp_vector)  # Current levels: cold, hot

levels(temp_factor) <- c("c", "h")  # Updated levels: c, h
```

We do need to be mindful of how the levels are ordered, meaning, if they don't get ordered in the beginning, they are automatically sorted by alphabetical order, so the levels in the function will be updated as such. If they were like `levels(temp_factor) <- c("h", "c")`, the `hot` elements would be `c` and vice-versa. The same logic applies to the ordered factors.

## Factors

Summarizing factors in R with the `summary()` function is a powerful way to gain insights into categorical data. By combining `summary()` with the `n()` function, you can easily count the occurrences of each factor leve. This is particularly useful for understanding the distribution of categories within a dataset.

For instance, if you gave a factor representing different colors. you can use `summary()` to determine the number of observations for each color, providing valuable information about the prevalence of each category.

```R
temp_vector <- c("hot", "cold", "cold", "cold", "hot", "hot")

temp_factor <- factor(temp_vector)  # Current levels: cold, hot

summary(temp_factor)
```

Returns the following:

```
cold  hot
   3    3
```

## Ordered Factors

Ordered factors in R are a special type of factor where the levels have a defined order or hierarchy. This is useful for variables with ordinal scales, such as "low", "medium", and "high", or "strongly disagree", "disagree", "neutral", "agree", and "strongly agree".

Unlike regular factors, ordered factors maintain the order of their levels, which is important for statistical analyses that require a specific ordering. To create an ordered factor, you set the `ordered` argument to `TRUE` in the `factor` function and specify the levels in the desired order.

```R
size_vector <- c("large", "large", "small", "medium", "medium", "large")

size_factor <- factor(size_vector, ordered = TRUE, levels = c("small", "medium", "large"))

size_factor
```

Output:

```
[1] large  large  small  medium medium large
Levels: small < medium < large
```
