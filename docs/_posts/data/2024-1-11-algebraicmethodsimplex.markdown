---
layout: post
title:  "Algebraic Method for Linear Programming Solutions using SymPy in Python"
date:   2024-1-11 07:25:17 -0800
categories: jekyll update data
---

## Introduction

Linear programming, a versatile optimization technique, finds applications across various domains. Among its solving algorithms, the simplex method stands out for its efficiency. In this blog post, we delve into the implementation of the algebraic method, acknowledging its less-than-optimal efficiency, and leverage the powerful SymPy library in Python. Our focal point is the maximization of the objective function \\( z = 6x_1 + 5x_2 \\) under the constraints \\(x_1 + x_2 \leq 5\\), \\(3x_1 + 2x_2 \leq 12\\), \\(x_1 \geq 0\\), and \\(x_2 \geq 0\\). This exploration combines theoretical insights with a detailed walkthrough of the implementation.


## Understanding the Linear Programming Problem

### Objective Function and Constraints:

The optimization goal is to maximize \\( z = 6x_1 + 5x_2 \\), subject to the constraints:

1. \\( x_1 + x_2 \leq 5 \\)
2. \\( 3x_1 + 2x_2 \leq 12 \\)
3. \\( x_1 \geq 0 \\)
4. \\( x_2 \geq 0 \\)

These constraints define a feasible region in the solution space.



## SymPy and the Algebraic Method

### SymPy: A Tool for Algebraic Computations

SymPy, a symbolic mathematics library, empowers us to implement the algebraic method. This approach involves manipulating algebraic expressions to systematically solve linear programming problems.

### Script Overview:

Our Python script utilizes SymPy for the algebraic method. The key components of the script are:

```python
from sympy import symbols, solve, lambdify
x1,x2,x3,x4,z=symbols('x1 x2 x3 x4 z')
import itertools
st = [x1, x2, x3, x4]
per = itertools.combinations(st,2)
for c in per:
  expr=solve((x1+x2+x3-5,3*x1+2*x2+x4-12,c[0],c[1]),x1,x2,x3,x4)
  print(expr)
  print('z = ', expr[x1]*6+expr[x2]*5)
```


## Script Walkthrough

### 1. Objective Function and Constraints

The script initiates by defining symbolic variables and expressing the objective function \\( z = 6x_1 + 5x_2 \\). Constraints are rewritten as a list of equations, capturing the limitations on \\( x_1 \\) and \\( x_2 \\).

### 2. Iterating through Variable Combinations

The script generates combinations of two variables, representing non-basic variables. It then iterates through these combinations.

### 3. Setting Non-Basic Variables to Zero

For each iteration, two non-basic variables are fixed, set to zero, to find feasible solutions.

### 4. System of Equations and Constraints

The script sets up a system of equations with the selected non-basic variables set to zero.

### 5. Solving Symbolically with SymPy

SymPy's `solve` function is then employed to find symbolic solutions for the remaining variables. These solutions represent the values of basic variables in the chosen scenario.

### 6. Displaying Results

The script prints the symbolic solutions for both basic and non-basic variables, providing insights into the selected scenario in the algebraic method. It also calculates and prints the symbolic value of the objective function, showcasing how the objective function is affected by the chosen combination of non-basic variables.



## Discussion of Results

The output of the algebraic method provides insights into feasible and infeasible solutions:

- **Feasible Solutions:**
  - Solutions where all variables are non-negative and constraints are satisfied are deemed feasible.
  - Example: {x1: 0, x2: 5, x3: 0, x4: 2} with \\(z = 25\\).

- **Infeasible Solutions:**
  - Solutions violating constraints, such as negative values for variables, are considered infeasible.
  - Example: {x1: 5, x2: 0, x3: 0, x4: -3} with \\(z = 30\\).

- **Optimal Solution:**
  - The optimal solution is the one that maximizes the objective function among feasible solutions.
  - Example: {x1: 2, x2: 3, x3: 0, x4: 0} with \\(z = 27\\).

Understanding the feasibility of solutions and the corresponding objective function values is crucial in interpreting the results of a linear programming problem. In this case, the algebraic method, powered by SymPy, facilitates a systematic exploration of solutions and provides valuable insights into the optimization process.


## Conclusion

In this exploration, we've implemented the algebraic method using SymPy in Python and scrutinized the output to discern feasible and infeasible solutions. The algebraic approach allows for a comprehensive understanding of the optimization process, shedding light on the interplay between variables and constraints.