---
layout: post
title:  "Understanding Newton's Divided Difference Interpolation Formula
"
date:   2023-10-13 06:25:17 -0800
categories: jekyll update
---

## Introduction

Interpolation is a fundamental concept in mathematics and science that allows us to estimate values between known data points. One of the most versatile and widely used interpolation methods is Newton's Divided Difference Interpolation Formula. This formula provides a way to approximate a function's values at intermediate points based on its values at a set of given data points. In this blog, we'll delve into the details of Newton's Divided Difference Interpolation Formula and understand how it works.

## The Formula

Newton's Divided Difference Interpolation Formula is a powerful tool that allows us to construct a polynomial that passes through a given set of data points. The formula consists of two parts, one for the forward difference and the other for the backward difference. Let's start by examining the forward difference formula:

### Forward Difference Formula:

$$
\begin{aligned}
f(x) & = f\left(x_0\right) + (x - x_0) f\left[x_0, x_1\right] + (x - x_0)(x - x_1) f\left[x_0, x_1, x_2\right] \\
& + (x - x_0)(x - x_1)(x - x_2) f\left[x_0, x_1, x_2, x_3\right] + \cdots \\
& + (x - x_0)(x - x_1)\cdots(x - x_n) f\left[x_0, x_1, x_2, \ldots, x_n\right].
\end{aligned}
$$

In this formula, $$f(x)$$ represents the interpolated function, and $$x_0, x_1, x_2, \ldots, x_n$$ are the given n+1 data points. The notation $$f[x_i, x_j]$$ represents the divided difference, which is a measure of how much the function values change between $$x_i$$ and $$x_j$$.

Now, let's explore the backward difference formula:

### Backward Difference Formula:

$$
\begin{aligned}
f(x) = f(x_n) & + (x - x_n) f[x_n, x_{n-1}] + (x - x_n)(x - x_{n-1}) f[x_n, x_{n-1}, x_{n-2}] \\
& + \cdots + (x - x_n)(x - x_{n-1})\cdots(x - x_1) f[x_n, x_{n-1}, \ldots, x_1, x_0].
\end{aligned}
$$

In this formula, $$f(x)$$ represents the interpolated function in a backward manner, starting from the last data point $$x_n$$ and working our way backward to $$x_0$$. The divided differences are calculated in a similar way as in the forward formula but in reverse order.

## Understanding Divided Differences

Divided differences play a crucial role in Newton's interpolation formula. These values are essentially the slopes of secant lines connecting pairs of data points. For example, $$f[x_i, x_j]$$ represents the divided difference between $$x_i$$ and $$x_j$$. To calculate these differences, you can use the following recursive formula:

$$
f[x_i, x_j] = \frac{f[x_j] - f[x_i]}{x_j - x_i}.
$$

This formula calculates the divided difference between $$x_i$$ and $$x_j$$ based on the function values at those points.


## Higher orders
 
Higher order divided differences are a more advanced concept in numerical analysis, often used in interpolation and polynomial approximation. While the basic divided differences represent the slope of secant lines connecting pairs of data points, higher order divided differences extend this concept to calculate the rate of change of slopes. They are useful when you need to interpolate a function using higher-degree polynomials.

To understand higher order divided differences, let's first look at the basic divided difference formula for two data points:

$$f[x_i, x_j] = \frac{f(x_j) - f(x_i)}{x_j - x_i}.$$

Now, let's introduce the concept of second-order divided differences. These represent the rate of change of slopes between three data points. The second-order divided difference between three data points $$x_i, x_j, x_k$$ is calculated as follows:

$$f[x_i, x_j, x_k] = \frac{f[x_j, x_k] - f[x_i, x_j]}{x_k - x_i}.$$

In this formula, $$f[x_j, x_k]$$ represents the divided difference between $$x_j$$ and $$x_k$$, and $$f[x_i, x_j]$$ represents the divided difference between $$x_i$$ and $$x_j$$.

Higher-order divided differences can be defined similarly. The third-order divided difference between four data points $$x_i, x_j, x_k, x_l$$ is calculated as:

$$f[x_i, x_j, x_k, x_l] = \frac{f[x_j, x_k, x_l] - f[x_i, x_j, x_k]}{x_l - x_i}.$$

In this case, $$f[x_j, x_k, x_l]$$ represents the divided difference between $$x_j, x_k,$$ and $$x_l$$, and $$f[x_i, x_j, x_k]$$ represents the divided difference between $$x_i, x_j,$$ and $$x_k$$.

Higher-order divided differences are essential when you're working with interpolation techniques involving polynomials of higher degrees. For example, when using Newton's Divided Difference Interpolation Formula to construct a polynomial of degree three or higher, you'll need to compute third or higher-order divided differences. These higher-degree interpolating polynomials can provide more accurate approximations of the underlying function, especially when the function itself has complex behavior or curvature.

In summary, higher-order divided differences extend the concept of basic divided differences to calculate the rate of change of slopes between multiple data points. They are particularly useful in interpolation methods that involve polynomials of higher degrees, allowing for more accurate approximations of functions with intricate characteristics.


- **First-Order Divided Difference** ($$f[x_0, x_1]$$):

To calculate the first-order divided difference, use the basic formula:

$$f[x_0, x_1] = \frac{f(x_1) - f(x_0)}{x_1 - x_0}.$$

This gives you the first-order divided difference between the data points $$x_0$$ and $$x_1$$.

- **Second-Order Divided Difference** ($$f[x_0, x_1, x_2]$$):

To calculate the second-order divided difference, you can use the following formula:

$$f[x_0, x_1, x_2] = \frac{f[x_1, x_2] - f[x_0, x_1]}{x_2 - x_0}.$$

This gives you the second-order divided difference between the data points $$x_0$$, $$x_1$$, and $$x_2$$.

- **Third-Order Divided Difference** ($$f[x_0, x_1, x_2, x_3]$$):

To calculate the third-order divided difference, you can use a similar approach:

$$f[x_0, x_1, x_2, x_3] = \frac{f[x_1, x_2, x_3] - f[x_0, x_1, x_2]}{x_3 - x_0}.$$

This provides you with the third-order divided difference between the data points $$x_0$$, $$x_1$$, $$x_2$$, and $$x_3$$.

You can continue this process for higher-order divided differences if needed. The key idea is to recursively apply the formula by building up from lower-order divided differences to higher-order ones. The information in your table is essentially showing how to calculate the divided differences step by step, considering one data point at a time and gradually incorporating additional data points in the calculation.

By following these formulas, you can calculate the divided differences and build interpolation polynomials of various orders, depending on the number of data points available.

To generalize a table of n points for up to the n-1 order divided differences, you can extend the table structure as follows:

 


| x   | f(x)            | First           | ...                | n-2              | n-1              |
|---------|------------------|------------------|--------------------|-------------------|-------------------|------------------|
| $$x_0$$   | $$f(x_0)$$         | | ...                |  | |
| $$x_1$$   | $$f(x_1)$$         | $$f[x_0, x_1]$$    | ...                |  | |
| $$x_2$$   | $$f(x_2)$$         | $$f[x_1, x_2]$$    | ...                |  | |
| ...     | ...              | ...              | ...                | | |
| $$x_{n-2}$$ | $$f(x_{n-2})$$   |$$f[x_{n-3},x_{n-2}]$$ | ...                |$$f[x_0, x_1, \ldots, x_{n-3},x_{n-2}]$$ | |
| $$x_{n-1}$$   | $$f(x_{n-1})$$         |  $$f[x_{n-2}, x_{n-1}]$$ |... | $$f[x_1, x_2, \ldots, x_{n-2},x_{n-1}]$$| $$f[x_0, x_1, \ldots, x_{n-3},x_{n-2},x_{n-1}]$$ |

In this generalized table, each row represents a specific data point ($$x_0$$, $$x_1$$, $$x_2$$, ..., $$x_n$$), and each column corresponds to a different order of divided difference. The nth-order divided differences are included in the nth column, following the same pattern as the first, second, and third-order differences.

You can populate the table by calculating the appropriate divided differences for your specific data points and desired order of interpolation. This table structure allows you to efficiently organize and calculate divided differences for constructing higher-degree interpolation polynomials using methods like Newton's Divided Difference Interpolation Formula.


## Calculating Divided Differences in Python

In the field of numerical analysis, the calculation of divided differences plays a pivotal role in constructing interpolation polynomials. Divided differences are fundamental to methods like Newton's Divided Difference Interpolation Formula. To efficiently compute these differences, Python offers a straightforward implementation that allows you to calculate divided differences of various orders using the `calculate_divided_differences` function.

### The `calculate_divided_differences` Function

Let's explore the Python code snippet provided for the `calculate_divided_differences` function:

```python
def calculate_divided_differences(x_values, y_values):
    n = len(x_values)
    divided_diff = []

    # Initialize the divided differences with the y values
    divided_diff.append(list(y_values))

    # Calculate the divided differences iteratively
    for j in range(1, n):
        next_row = []
        for i in range(n - j):
            diff = (divided_diff[j - 1][i + 1] - divided_diff[j - 1][i]) / (x_values[i + j] - x_values[i])
            next_row.append(diff)
        divided_diff.append(next_row)

    return divided_diff
```

### Understanding the Code

- **Input**: The function takes two lists as input:
    - `x_values`: A list of x-coordinates (independent variable).
    - `y_values`: A list of corresponding y-coordinates (function values).

- **Output**: The function returns a list, `divided_diff`, which contains the divided differences. Each row of `divided_diff` corresponds to a different order of divided difference.

- **Initialization**: The code initializes the `divided_diff` list with the y-values from the input data. The first row of `divided_diff` corresponds to the zeroth-order divided differences (simply the function values).

- **Iterative Calculation**: The function uses a nested loop to iteratively calculate higher-order divided differences. The outer loop (indexed by `j`) ranges from 1 to `n-1`, where `n` is the number of data points. The inner loop (indexed by `i`) iterates from 0 to `n-j-1`.

- **Divided Difference Calculation**: Within the nested loops, the function calculates each divided difference using the following formula:
  
  $$f[x_i, x_j] = \frac{f(x_j) - f(x_i)}{x_j - x_i}.$$

  Here, `f(x_j)` and `f(x_i)` are the function values at data points `x_j` and `x_i`, and `x_j - x_i` is the difference in x-coordinates.

- **Storage**: Each calculated row of divided differences is appended to the `divided_diff` list.

- **Return Value**: The function returns the `divided_diff` list, which now contains the divided differences of different orders.

### Example Usage

You can use the `calculate_divided_differences` function to efficiently compute divided differences for a set of data points, which can then be used for constructing interpolation polynomials or estimating function values at intermediate points. The result will be organized in the `divided_diff` list, with each row corresponding to a different order of divided difference.

## Interpolation Using the `interpolate_forward` Function

In the realm of numerical analysis and interpolation, the `interpolate_forward` function is a valuable tool. It allows you to use previously computed divided differences to perform forward interpolation. Let's dissect the code to understand its functionality:

```python
def interpolate_forward(x_values, divided_diff, x):
    n = len(x_values)
    result = divided_diff[0][0]
    term = 1

    x_terms = [1]
    diffs = [divided_diff[0][0]]

    for i in range(1, n):
        term *= (x - x_values[i - 1])
        result += term * divided_diff[i][0]
        x_terms.append(term)
        diffs.append(divided_diff[i][0])

    return result
```

### Understanding the Code

- **Inputs**:
  - `x_values`: A list of x-coordinates (data points).
  - `divided_diff`: A list containing the divided differences, typically computed using the `calculate_divided_differences` function.
  - `x`: The value at which you want to interpolate the function.

- **Output**: The function returns the interpolated value at `x` using the divided differences provided.

- **Initialization**: The code initializes `result` to the value of the zeroth-order divided difference, which is `divided_diff[0][0]`. It also initializes `term` to 1.

- **Iteration**:
  - The function iterates over the data points in the `x_values` list from the second point (`x_values[1]`) to the last point (`x_values[n-1]`).
  - In each iteration, it updates `term` by multiplying it by `(x - x_values[i-1])`. This is a fundamental step in forward interpolation.
  - The result is updated by adding the product of `term` and the first divided difference of the current order (`divided_diff[i][0]`). This is part of the forward interpolation process.

- **Storage**: The function also maintains two lists, `x_terms` and `diffs`, which store the terms in the interpolation polynomial and the corresponding divided differences for each order.

- **Return Value**: The function returns `result`, which is the interpolated value at `x`.

### Example Usage

You can use the `interpolate_forward` function to estimate function values at a desired point `x` using the divided differences calculated for a set of data points. This is particularly useful when you want to approximate function values between known data points using the Newton's Divided Difference Interpolation Formula.

In the function, the result is calculated incrementally by adding the contributions from each divided difference term, which depends on the difference between `x` and the data points. The terms and divided differences used in this calculation are also stored for reference, making it a valuable tool for understanding the interpolation process.

Remember to provide the `x_values` and `divided_diff` corresponding to your data, and specify the `x` value at which you want to perform the interpolation. The function will return the estimated function value at that point.


## Interpolation Using the `interpolate_backward` Function

The `interpolate_backward` function is another valuable tool in the field of numerical analysis and interpolation. It enables backward interpolation using previously calculated divided differences. Let's break down the code to understand how it works:

```python
def interpolate_backward(x_values, divided_diff, x):
    n = len(x_values)
    result = divided_diff[0][-1]
    term = 1

    x_terms = [1]
    diffs = [divided_diff[0][-1]]

    j = 1
    for i in range(n, 1, -1):
        term *= (x - x_values[i - 1])
        result += term * divided_diff[j][-1]
        x_terms.append(term)
        diffs.append(divided_diff[j][-1])
        j += 1

    return result
```

### Understanding the Code

- **Inputs**:
  - `x_values`: A list of x-coordinates (data points).
  - `divided_diff`: A list containing the divided differences, typically calculated using the `calculate_divided_differences` function.
  - `x`: The value at which you want to interpolate the function.

- **Output**: The function returns the interpolated value at `x` using the provided divided differences.

- **Initialization**: The code initializes `result` to the value of the last divided difference in the zeroth row, which is `divided_diff[0][-1]`. It also initializes `term` to 1.

- **Iteration**:
  - The function iterates over the data points in the `x_values` list from the last point (`x_values[n-1]`) to the second point (`x_values[1]`).
  - In each iteration, it updates `term` by multiplying it by `(x - x_values[i-1])`. This is a critical step in backward interpolation.
  - The result is updated by adding the product of `term` and the last divided difference of the current order (`divided_diff[j][-1]`). This is part of the backward interpolation process.

- **Storage**: The function also maintains two lists, `x_terms` and `diffs`, which store the terms in the interpolation polynomial and the corresponding divided differences for each order.

- **Return Value**: The function returns `result`, which is the interpolated value at `x`.

### Example Usage

You can use the `interpolate_backward` function to estimate function values at a specified point `x` using previously calculated divided differences for a set of data points. This is particularly useful when you need to approximate function values between known data points using methods such as Newton's Divided Difference Interpolation Formula, but in a backward manner.

In the function, the result is calculated incrementally by adding the contributions from each divided difference term, which depends on the difference between `x` and the data points. The terms and divided differences used in this calculation are also stored for reference, making it a valuable tool for understanding the interpolation process in a backward direction.

To use the function, provide the `x_values` and `divided_diff` corresponding to your data, and specify the `x` value at which you want to perform the interpolation. The function will return the estimated function value at that point, calculated in a backward fashion.

Summary

To demonstrate how to use the `calculate_divided_differences`, `interpolate_forward`, and `interpolate_backward` functions, let's work through an example where we have a set of data points and want to interpolate a function value at a specific point. In this example, we'll use the following data points:

- Data Points: $$(x_0, f(x_0)) = (1, 3), (x_1, f(x_1)) = (2, 8), (x_2, f(x_2)) = (3, 15)$$

We'll calculate the divided differences and then use the interpolated values at specific points using both forward and backward interpolation.

### Step 1: Calculating Divided Differences

First, calculate the divided differences using the `calculate_divided_differences` function. Here's how to do it:

```python
x_values = [1, 2, 3]
y_values = [3, 8, 15]

divided_diff = calculate_divided_differences(x_values, y_values)
```

### Step 2: Interpolation Using `interpolate_forward`

Now, let's interpolate a function value at a specific point (e.g., $$x = 2.5$$) using forward interpolation:

```python
x_interpolate = 2.5
result_forward = interpolate_forward(x_values, divided_diff, x_interpolate)

print(f"Interpolated value at x = {x_interpolate} (Forward Interpolation): {result_forward}")
```

### Step 3: Interpolation Using `interpolate_backward`

Next, we'll interpolate a function value at the same specific point (e.g., $$x = 2.5$$) using backward interpolation:

```python
x_interpolate = 2.5
result_backward = interpolate_backward(x_values, divided_diff, x_interpolate)

print(f"Interpolated value at x = {x_interpolate} (Backward Interpolation): {result_backward}")
```

### Complete Example

Here's the complete Python code for this example:

```python
# Import the functions
def calculate_divided_differences(x_values, y_values):
    n = len(x_values)
    divided_diff = []

    # Initialize the divided differences with the y values
    divided_diff.append(list(y_values))

    # Calculate the divided differences iteratively
    for j in range(1, n):
        next_row = []
        for i in range(n - j):
            diff = (divided_diff[j - 1][i + 1] - divided_diff[j - 1][i]) / (x_values[i + j] - x_values[i])
            next_row.append(diff)
        divided_diff.append(next_row)

    return divided_diff

def interpolate_forward(x_values, divided_diff, x):
    n = len(x_values)
    result = divided_diff[0][0]
    term = 1

    for i in range(1, n):
        term *= (x - x_values[i - 1])
        result += term * divided_diff[i][0]

    return result

def interpolate_backward(x_values, divided_diff, x):
    n = len(x_values)
    result = divided_diff[0][-1]
    term = 1

    j = 1
    for i in range(n, 1, -1):
        term *= (x - x_values[i - 1])
        result += term * divided_diff[j][-1]
        j += 1

    return result

# Data Points
x_values = [1, 2, 3]
y_values = [3, 8, 15]

# Calculate Divided Differences
divided_diff = calculate_divided_differences(x_values, y_values)

# Interpolate at a specific point using both forward and backward interpolation
x_interpolate = 2.5
result_forward = interpolate_forward(x_values, divided_diff, x_interpolate)
result_backward = interpolate_backward(x_values, divided_diff, x_interpolate)

# Print results
print(f"Interpolated value at x = {x_interpolate} (Forward Interpolation): {result_forward}")
print(f"Interpolated value at x = {x_interpolate} (Backward Interpolation): {result_backward}")
```

In this example, we've calculated the interpolated values at `x = 2.5` using both forward and backward interpolation methods. The `result_forward` and `result_backward` variables contain the respective interpolated values.


## Conclusion

Newton's Divided Difference Interpolation Formula is a powerful and versatile tool for estimating values between data points. Whether you're working on mathematical modeling, scientific research, or engineering problems, this formula provides a flexible approach to interpolation. By understanding the concept of divided differences and the forward and backward difference formulas, you can apply this method to a wide range of real-world problems, making it an invaluable tool for numerical analysis.


