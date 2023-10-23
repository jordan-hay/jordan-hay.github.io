---
layout: post
title:  "Optimizing a Product Mix using Linear Programming with Gurobi Python"
date:   2023-10-23 06:25:17 -0800
categories: jekyll update
---
## Optimizing Fertilizer Production with Gurobi

In the world of agriculture and farming, optimizing fertilizer production can have a significant impact on both the profit margins of a company and the overall health of crops. In this blog, we'll delve into a Python code snippet that utilizes the Gurobi library for mathematical optimization to determine the ideal combination of two types of fertilizer that will maximize profit contribution. 

## Introduction to Gurobi
Gurobi is a powerful mathematical optimization library in Python that can help businesses make informed decisions by solving complex optimization problems. In this example, we'll use Gurobi to create an optimization model for a fictional company called "Fertilizer Co" to determine the optimal production mix of two types of fertilizers - Fertilizer 1 and Fertilizer 2.

## Importing the Gurobi Library

The journey begins with importing the Gurobi library, a powerful tool for solving mathematical optimization problems. It provides an efficient way to find the best solution for complex decision-making scenarios.

```python
# Import the Gurobi library
import gurobipy as gp
```

## Setting up the Optimization Model

With Gurobi in our toolbox, we create an optimization model named "Fertilizer Co" to represent the decision-making process for our fertilizer production.

```python
# Create a new optimization model named "Fertilizer Co"
model = gp.Model("Fertilizer Co")
```

## Defining Decision Variables

The heart of the model involves two decision variables, 'x' and 'y,' which respectively represent the number of bags of Fertilizer 1 and Fertilizer 2 that should be produced. These variables are essential as they will be optimized to maximize profit.

```python
# Create decision variables:
# x represents the number of bags of Fertilizer 1, and y represents the number of bags of Fertilizer 2.
x = model.addVar(lb=0, vtype=gp.GRB.INTEGER, name="Fertilizer 1")
y = model.addVar(lb=0, vtype=gp.GRB.INTEGER, name="Fertilizer 2")
```

## Objective Function: Maximizing Profit Contribution

The objective function is crucial; it defines what we want to optimize. In this case, we want to maximize profit contribution. To calculate profit contribution, we subtract the total costs from the revenue. 

```python
# Set up the objective function to maximize profit contribution:
# We calculate the total profit as the revenue from selling bags of fertilizer minus the total costs.

# Revenue is calculated as the product of the number of bags and the selling price.
# The selling price for Fertilizer 1 is $30 per bag, and for Fertilizer 2, it's $33 per bag.
revenue = 30 * x + 33 * y

# Costs include:
# 1. The cost of nitrogen, phosphorous, and potassium ingredients used in each bag.
#    There are 12 pounds per bag, and 2000 pounds per ton.
#    The amount of each ingredient used in a bag is calculated based on the ingredient 
#    percentages fo nitrogen, phosphorous and potassium (0.6, 0.2, 0.2 for fertilizer 1; 
#    0.7, 0.1, 0.2 for fertilizer 2)
# 2. The cost of other ingredients ($10 per bag).
# 3. The cost of the bag itself (12 cents per bag).
# 4. The cost of filling and labeling each bag ($8 per bag).

ingredient_costs = (0.6 * x + 0.7 * y) * 12 * (532 / 2000) + (0.2 * x + 0.1 * y) * 12 * (345 / 2000) + (0.2 * x + 0.2 * y) * 12 * (475 / 2000)
other_ingredients_cost = 10 * (x + y)
bag_cost = 0.12 * (x + y)
filling_labeling_cost = 8 * (x + y)

# The objective function is to maximize revenue while subtracting the total costs.
model.setObjective(revenue - ingredient_costs - other_ingredients_cost - bag_cost - filling_labeling_cost, gp.GRB.MAXIMIZE)
```

## Adding Ingredient Constraints

Now that we've defined what we want to optimize, we need to consider real-world constraints. In this case, we have constraints related to the ingredients used in the fertilizer production. 

```python
# Add ingredient constraints:
# These constraints ensure that the amount of each ingredient used in the mix does not exceed the available quantities.

# For nitrogen, the constraint states that the amount of nitrogen used in both types of fertilizer (weighted by percentages) should not exceed 2.4 tons available.
model.addConstr(0.5 * 12 * x + 0.7 * 12 * y <= 2.40 * 2000 , "Nitrogen")

# For phosphorous, the constraint states that the amount of phosphorous used in both types of fertilizer (weighted by percentages) should not exceed 1.2 tons available.
model.addConstr(0.3 * 12 * x + 0.1 * 12 * y <= 1.20 * 2000, "Phosphorous")

# For potassium, the constraint states that the amount of potassium used in both types of fertilizer (weighted by percentages) should not exceed 1 ton available.
model.addConstr(0.2 * 12 * x + 0.2 * 12 * y <= 1.00 * 2000, "Potassium")
```

## Optimizing the Model

With the objective function and constraints in place, we can now optimize the model to determine the best combination of Fertilizer 1 and Fertilizer 2 quantities.

```python
# Optimize the model to find the best combination of Fertilizer 1 and Fertilizer 2 quantities.
model.optimize()
```

## Evaluating the Optimal Solution

Finally, it's time to see the results of our optimization. We check whether an optimal solution was found and if so, print the optimal quantities of Fertilizer 1 and Fertilizer 2 and the total profit contribution.

```python
# Check if an optimal solution was found.
if model.status == gp.GRB.OPTIMAL:
    print("Optimal Solution:")
    # Print the quantities of Fertilizer 1 and Fertilizer 2 to produce for maximum profit.
    print(f"Fertilizer 1 (x) = {x.x}")
    print(f"Fertilizer 2 (y) = {y.x}")
    # Print the total profit contribution obtained from the optimal solution.
    print(f"Total Profit Contribution = ${model.objVal:.2f}")
else:
    print("No optimal solution found")
```

The output:
```
Optimal Solution:
Fertilizer 1 (x) = 625.0
Fertilizer 2 (y) = 125.0
Total Profit Contribution = $7096.57
```


## Linear Program in Standard Form

The following is a concise form that represents the linear program while maximizing profit contribution, considering ingredient availability, ingredient costs, other ingredients costs, bag costs, and filling and labeling costs.

**Maximize:**
$$
30x + 33y - 12(0.6x + 0.7y)\left(\frac{532}{2000}\right) - 12(0.2x + 0.1y)\left(\frac{345}{2000}\right) - 12(0.2x + 0.2y)\left(\frac{475}{2000}\right) - 10(x + y) - 0.12(x + y) - 8(x + y)
$$

**Subject to:**

$$
0.5(12x) + 0.7(12y) \leq 2.40 \times 2000 \quad \text{(Nitrogen)}
$$

$$
0.3(12x) + 0.1(12y) \leq 1.20 \times 2000 \quad \text{(Phosphorous)}
$$

$$
0.2(12x) + 0.2(12y) \leq 1.00 \times 2000 \quad \text{(Potassium)}
$$

Where:
- $$x$$ represents the number of bags of Fertilizer 1.
- $$y$$ represents the number of bags of Fertilizer 2.

## Conclusion

This code demonstrates how mathematical optimization, with the help of the Gurobi library, can be used to make data-driven decisions that maximize profit while respecting real-world constraints. It's a powerful tool for businesses looking to optimize their processes and make the most out of their resources.
