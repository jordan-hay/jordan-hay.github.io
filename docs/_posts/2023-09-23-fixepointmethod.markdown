---
layout: post
title:  "Exploring Fixed-Point Iteration and Its Applications"
date:   2023-09-23 06:25:17 -0800
categories: jekyll update
---

Fixed-point iteration is a powerful numerical method used to find approximate solutions to equations. It's a fundamental tool in mathematics and has numerous applications in various fields, including engineering, physics, and computer science. In this blog, we'll dive into the world of fixed-point iteration and explore its applications through a set of mathematical functions and their corresponding fixed-point iteration methods.

## Understanding Fixed-Point Iteration

Before we delve into specific examples, let's establish a fundamental understanding of fixed-point iteration. The method aims to find a fixed point (i.e., a value where the function equals its input) of a given function. In mathematical terms, if we have a function $$f(x)$$, we seek to find a value $$x_0$$ such that $$f(x_0) = x_0$$.

The fixed-point iteration process involves repeatedly applying a function $$g(x)$$ to an initial guess $$x_0$$ until the value converges to the desired fixed point. The iteration continues until the difference between consecutive approximations falls below a predefined tolerance level ($$tol$$).

## Example 1: Solving $$f_1(x)$$

Let's start by solving the equation $$f_1(x) = x^3 + 4x^2 - 10$$. We have three candidate functions $$g_{11}(x)$$, $$g_{12}(x)$$, and $$g_{13}(x)$$ to apply for fixed-point iteration. We will analyze each one.

**Selecting Suitable Candidate Functions**

*Rearrange the Equation:*

   Start by rewriting the original equation $$x^3 + 4x^2 - 10 = 0$$ in the form $$x = g(x)$$. To do this, you'll need to isolate $$x$$ on one side of the equation. In our case:

$$x^3 + 4x^2 - 10 = 0$$
   
$$x^3 = 10 - 4x^2$$
  
$$x = \sqrt[3]{10 - 4x^2}$$

*Identify Candidate Functions:*

   The function on the right-hand side of the equation $$x = \sqrt[3]{10 - 4x^2}$$ can serve as a potential candidate function, $$g(x)$$, for our fixed-point iteration. However, it's important to ensure that $$g(x)$$ is continuous and has a derivative in the interval we are interested in.

*Analyze Convergence:*

   After identifying a candidate function, analyze its convergence behavior. One common criterion for convergence is that $$\lvert g'(x) \rvert < 1$$ for all $$x$$ in the interval of interest. This condition ensures that the fixed-point iteration will converge. Calculate the derivative $$g'(x)$$ and evaluate it over the interval to check for convergence.



### Using $$g_{11}(x)$$

$$g_{11}(x) = x - \frac{x^3 + 4x^2 - 10}{3x^2 + 8x}$$

We initiate the fixed-point iteration process with an initial guess $$x_0 = 0.1$$, and after several iterations, it successfully converges to the root, which is approximately 1.365.

### Using $$g_{12}(x)$$

$$g_{12}(x) = \sqrt{\frac{10 - x^3}{4}}$$

Starting with an initial guess $$x_0 = 0.1$$, we perform several iterations, ultimately leading us to the root, which is approximately 1.365 as well.

### Using $$g_{13}(x)$$

$$g_{13}(x) = \sqrt[3]{10 - 4x^2}$$

For this case, we initiate the process with $$x_0 = 0.1$$. However, it's important to note that $$g_{13}(x)$$ does not converge to a root after 1,000 iterations. The reason for this lack of convergence lies in the properties of the function $$g_{13}(x)$$ and the specific characteristics of the equation $$f_1(x)$$. In this case, the derivative of $$g_{13}(x)$$ at the root is greater than 1 in magnitude, indicating that $$g_{13}(x)$$ is not a contraction mapping near the root $$x_r = 1$$, which leads to non-convergence.

## Example 2: Solving $$f_2(x)$$

Now, let's explore the equation $$f_2(x) = x^5 - 2x + 1$$. We have three candidate functions $$g_{21}(x)$$, $$g_{22}(x)$$, and $$g_{23}(x)$$ to apply for fixed-point iteration. 

### Using $$g_{21}(x)$$

$$g_{21}(x) = \sqrt[5]{2x - 1}$$

We initiate the process with $$x_0 = 0.1$$, and successfully find a root after 20 iterations. However, it's important to note that $$g_{21}(x)$$ returns a complex number as a root instead of a real number, specifically $$1.0000000021054976+5.493866534381359e-09j$$. This behavior can occur when dealing with functions that have complex roots, especially when the initial guess or the specific characteristics of the function lead to such results.


### Using $$g_{22}(x)$$

Now, let's introduce a different candidate function for fixed-point iteration, $$g_{22}(x) = \frac{1}{2}(x^5 + 1)$$, and apply it to solve the equation $$f_1(x) = x^3 + 4x^2 - 10$$.

We'll begin with an initial guess $$x_0 = 0.1$$ and observe how the fixed-point iteration process behaves.

1. **Initial Guess**: Set $$x_0 = 0.1$$.

2. **Fixed-Point Iteration**:

   - Iteration 1: $$x_1 = g_{22}(0.1) = \frac{1}{2}((0.1)^5 + 1)$$
   - Iteration 2: $$x_2 = g_{22}(x_1) = \frac{1}{2}((x_1)^5 + 1)$$
   - Continue this process until the difference between consecutive approximations falls below a predefined tolerance level ($$tol$$).

3. **Convergence**: Observe how the values of $$x_n$$ evolve with each iteration and whether they converge to the root of the equation, which is approximately 0.519.

This example demonstrates how a different choice of candidate function, in this case, $$g_{22}(x)$$, can lead to convergence to the desired root. It also highlights the importance of selecting an appropriate $$g(x)$$ and initial guess for fixed-point iteration.

Certainly, here's a concise version of the section with the equation for $$g_{23}(x)$$ and the result:

### Using $$g_{23}(x)$$

Now, let's introduce another candidate function for fixed-point iteration, $$g_{23}(x) = x - \frac{x^5 - 2x + 1}{5x^4 - 2}$$, and apply it to solve the equation $$f_2(x) = x^5 - 2x + 1$$. We'll begin with an initial guess $$x_0 = 0.1$$.

With this initial guess, the fixed-point iteration process converges to a root, approximately $$x \approx 0.519$$, without showing the detailed iterations.

Notably, if the starting point is $$x_0 = 0.9$$, the fixed-point iteration converges to a different root, specifically $$x \approx 1$$, showcasing the sensitivity of the method to initial guesses.


## Conclusion

Fixed-point iteration is a versatile numerical method used to approximate solutions to equations. In this blog, we've explored two different equations ($$f_1(x)$$ and $$f_2(x)$$) and applied various candidate functions for fixed-point iteration. We've seen how each choice of $$g(x)$$ and initial guess $$x_0$$ affects the convergence to the root.

Whether you're solving complex mathematical equations or tackling real-world problems, fixed-point iteration is a valuable tool in your mathematical toolbox. By choosing appropriate $$g(x)$$ functions and initial guesses, you can efficiently find solutions to a wide range of problems. So, the next time you encounter a challenging equation, consider the power of fixed-point iteration in your problem-solving arsenal. However, be aware that in some cases, fixed-point iteration may return complex roots, and careful analysis is necessary to ensure the results align with your expectations.



## Implementing Fixed-Point Iteration in Python

In this section, we'll delve into the practical implementation of fixed-point iteration using Python. We'll use this numerical method to find approximate solutions to equations and explore its applications with real Python code.

### Setting Up the Equations

To get started, let's define the equations we'll be working with. We'll tackle two examples: $$f_1(x) = x^3 + 4x^2 - 10$$ and $$f_2(x) = x^5 - 2x + 1$$.

```python
# Define the functions f1(x) and f2(x)
def f1(x):
    return x**3 + 4*x**2 - 10

def f2(x):
    return x**5 - 2*x + 1
```

### Candidate Functions for Fixed-Point Iteration

For each equation, we need candidate functions $$g(x)$$ to apply the fixed-point iteration method. Let's define these functions:

#### Example 1: $$f_1(x)$$

For the first example, we have three candidate functions: $$g_{11}(x)$$, $$g_{12}(x)$$, and $$g_{13}(x)$$.

```python
def g11(x):
    return x - (x**3 + 4*x**2 - 10) / (3*x**2 + 8*x)

def g12(x):
    return ((10 - x**3) / 4)**(1/2)

def g13(x):
    return (10 - 4*x**2)**(1/3)
```

#### Example 2: $$f_2(x)$$

For the second example, we also have three candidate functions: $$g_{21}(x)$$, $$g_{22}(x)$$, and $$g_{23}(x)$$.

```python
def g21(x):
    return (2*x - 1)**(1/5)

def g22(x):
    return (1/2)*(x**5 + 1)

def g23(x):
    return x - (x**5 - 2*x + 1) / (5*x**4 - 2)
```

### Implementing Fixed-Point Iteration

Now, let's put everything together and implement the fixed-point iteration method.

```python
# Set the tolerance level for convergence
tol = 1E-8

# Define the fixed-point iteration method
def fixed_point(x_0, f):
    count = 0
    x_1 = f(x_0)
    max_count = 1E3

    while abs(x_1 - x_0) > tol and count < max_count:
        x_0 = x_1
        x_1 = f(x_0)
        count += 1

    return x_1, count
```

### Using the Fixed-Point Iteration Method

With the equations, candidate functions, and the fixed-point iteration method defined, you can now apply this numerical technique to find approximate solutions to equations. Simply provide an initial guess and the corresponding function to the `fixed_point` method to find roots.

```python
# Example 1: Using g11(x) with an initial guess of 0.1
root, iterations = fixed_point(0.1, g11)
print("Root:", root)
print("Iterations:", iterations)
print(":", iterations)
print(f"f1({root}):",f1(root))

# Example 2: Using g23(x) with an initial guess of 0.9
root, iterations = fixed_point(0.9, g23)
print("Root:", root)
print("Iterations:", iterations)
print(f"f2({root}):",f2(root))
```

This Python code enables you to explore the power of fixed-point iteration for solving equations efficiently. You can experiment with different initial guesses and candidate functions to better understand how this method behaves and converges to solutions.
