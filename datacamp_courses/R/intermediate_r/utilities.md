# Utilities

- [Utilities](#utilities)
  - [Useful functions](#useful-functions)
    - [Mathematical Utilities](#mathematical-utilities)
      - [Trigonometric functions](#trigonometric-functions)
      - [Logarithmic functions](#logarithmic-functions)
      - [Probability distributions](#probability-distributions)
    - [Data Structure Utilities](#data-structure-utilities)
    - [Regular expressions](#regular-expressions)
      - [Additional functions and packages](#additional-functions-and-packages)
      - [Regular Expression Syntax](#regular-expression-syntax)
  - [Time and dates](#time-and-dates)
    - [Basic Date and Time Objects](#basic-date-and-time-objects)
    - [Common Operations](#common-operations)
    - [Unclass](#unclass)

## Useful functions

Some of the most common useful functions are the `apply` family, the `print` function, and the `identical` function. There are some other types of functions as well, as shown bellow.

### Mathematical Utilities

R provides a rich set of built-in mathematical functions, covering a wide range of operations from basic arithmetic to advanced statistical calculations. These functions are essential for performing numerical computations, data analysis, and scientific modelling.

Bellow there are just a few examples of the many mathematical functions available in R. The specific functions you'll need will depend on the nature of your calculations and the types of data you're working with. By understanding and utilizing these functions effectively, you can perform a wide range of mathematical operations and analyses in R.

#### Trigonometric functions

- `sin`, `cos`, `tan`: Sine, cosine, and tangent
- `asin`, `acos`, `atan`: Inverse sine, cosine, and tangent

#### Logarithmic functions

- `mean`, `median`, `mode`: Mean, median, and mode
- `sd`, `var`: Standard deviation and Variance
- `quantile`: Quantiles (percentiles)
- `min`, `max`: Minimum and maximum values
- `sum`, `prod`: Sum and product

#### Probability distributions

- `sqrt`: Square root
- `abs`: Absolute value
- `ceiling`, `floor`: Rounding up and down to nearest integer
- `round`: Rounding to nearest integer
- `factorial`: Factorial
- `choose`: Combinations

### Data Structure Utilities

R offers a rich set of data structures and functions that are essential for data analysis and manipulation. These tools provide a flexible framework for working with different types of data, from simple vectors to complex matrices and data frames.

General functions:

- `seq`: Creates a sequence of numbers.
- `rep`: Replicates elements of a vector.
- `sort`: Sorts elements of a vector.
- `str`: Provides a concise summary of an object's structure.
- `rev`: Reverses the order of elements in a vector.
- `is.*()` family: Checks if an object is of a specific type.
- `as.*()` family: Converts an object into a specific type.
- `unclass`: The unclass function removes the class attributes from an object, returning the underlying data structure.

List functions:

- `append`: Adds element to a list.
- `unlist`: Flattens a list into a vector.

Packages:

- `dplyr` **package**: this popular package offers a grammar of data manipulation, providing functions like `filter`, `select`, `mutate`, `arrange`, and `summarize` for common data operations.
- `ggplot2` **package**: A powerful visualization package that uses a grammar of graphics to create a wide variety of plots, including scatter plots, histograms, bar charts, and line charts.
- `tidyr` **package**: This package is designed for data tidying, helping to reshape data into a more consistent format. Function like `gather`, `spread`, amd `separate` are useful for this purpose.

### Regular expressions

Regular expressions are powerful tools for pattern matching and text manipulation. They provide a flexible and concise way to search for specific sequences of characters within a string. R offers several functions and packages that support regular expressions, making them easy to incorporate into data analysis workflows.

Base REGEX functions:

- `grep`: Searches for a pattern within a character vector and returns the indices of matching elements.
- `grepl`: Searches for a pattern within a character vector and returns a logical vector indicating whether each element matches.
- `sub`: Only substitutes one occurrence of a pattern within a character vector with a replacement string.
- `gsub`: Substitutes all occurrences of a pattern within a character vector with a replacement string.
- `regexpr`: Searches for the first occurrence of a pattern within a character vector and returns information about the match, including its start and end positions.

#### Additional functions and packages

- `stringr` **package**: Provides a consistent interface for string manipulation, including functions for regular expressions.
- `stringi` **package**: Offers advanced string manipulation capabilities, including support for Unicode characters.
- `PCRE2` **package**: Provides an interface to the PCRE2 regular expressoin library, offering high performance and advanced features.

#### Regular Expression Syntax

- **Literal characters**: Match the exact character.
- **MetaCharacters**: Have special meanings, such as `.` (any character), `^` (beginning of string), `$` (end of string), `*` (zero or more occurrences), `+` (one or more occurrences), `?` (zero or one occurrences), `|` (alternation), `[]` (character class), and `()` (grouping).
- **Quantifiers**: Specify the number of times a pattern can occur.
- **Character classes**: Define sets of characters.
- **Escape sequences**: Represent special characters or control codes.

```R
# Match email addresses
email_pattern <- "^\\w+@\\w+\\.\\w+$"
```

By understanding regular expressions and leveraging the available functions and packages in R, you can effectively search, manipulate, and extract information from text data.

## Time and dates

R provides a robust set of functions and data structures for working with times and dates, making it a powerful tool for time-series analysis and data manipulation. The `lubridate` package is particularly useful for handling date and time data efficiently.

### Basic Date and Time Objects

- `Date` **objects**: Represent date without time components. They can be created using the `as.Date()` function.
- `POSIXct` **objects**: Represent dates and times in a specific time zone. They can be created using the `as.POSIXct()` function.
- `POSIXlt` **objects**: Represent dates and times in a list-like structure, providing more detailed information about the time components.

### Common Operations

- Conversion between time zones: Use the `with_tz()` function to convert between time zones.
- Date arithmetic: Perform operations like adding or subtracting days, weeks , or months using functions like `+`, `-`, `days`, `weeks`, `months`.
- Time extraction: Extract specific components of a date or time object using functions like `year`, `month`, `hour`, `minute`, and `second`.
- Formatting: Format dates and times using the `format` function.
- Time intervals: Create and manipulate time intervals using functions like `interval`, `start`, and `end`

### Unclass

By using the `unclass` function with `Date` objects, the numeric representation is the number of days since the origin date, which is January 1, 1970. So the value 19986 represents 19986 days since January 1, 1970.

While you might not often need to unclass a `Date` object directly, understanding how it works can be helpful in situations where you need to manipulate the underlying data or integrate it with other systems that expect numeric representations of dates. Additionally, it can be useful for debugging or understanding how R handles data internally.
