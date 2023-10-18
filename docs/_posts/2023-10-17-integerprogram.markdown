---
layout: post
title:  "Solving Integer Programs: Designing a Vacation Package with Gurobi Python Optimization
"
date:   2023-10-17 06:25:17 -0800
categories: jekyll update
---

# Designing a Vacation Package with Gurobi Optimization

Planning the perfect vacation can be a daunting task, especially with so many choices to make - from choosing activities and accommodations to upgrades and transportation options. This is where mathematical optimization comes into play. In this blog post, we'll explore how to use Gurobi, a powerful mathematical optimization library in Python, to design the perfect vacation package while minimizing costs.

## Introduction

We have a set of decisions to make for our vacation package:

1. **Activities:** We can choose from three activities (Activity 1, Activity 2, and Activity 3).
2. **Upgrades:** There are two possible upgrades (Upgrade 1 and Upgrade 2) available for our activities.
3. **Accommodations:** We can choose from two accommodation options (Accommodation 1 and Accommodation 2).
4. **Transportation:** There are two transportation options (Transportation 1 and Transportation 2).

Our goal is to minimize the overall cost of the vacation package while ensuring that our vacation package meets certain constraints.

## Setting Up the Model

To set up the optimization model, we use the Gurobi Python package. We create binary decision variables for each choice, where '1' represents selection, and '0' represents non-selection. The objective is to minimize the total cost of the vacation package.

```python
import gurobipy as gp

# Create a model
model = gp.Model("Vacation_Package_Design")

# Create binary decision variables
a1 = model.addVar(vtype=gp.GRB.BINARY, name="Activity1")
a2 = model.addVar(vtype=gp.GRB.BINARY, name="Activity2")
a3 = model.addVar(vtype=gp.GRB.BINARY, name="Activity3")
u1 = model.addVar(vtype=gp.GRB.BINARY, name="Upgrade1")
u2 = model.addVar(vtype=gp.GRB.BINARY, name="Upgrade2")
b1 = model.addVar(vtype=gp.GRB.BINARY, name="Accommodation1")
b2 = model.addVar(vtype=gp.GRB.BINARY, name="Accommodation2")
t1 = model.addVar(vtype=gp.GRB.BINARY, name="Transportation1")
t2 = model.addVar(vtype=gp.GRB.BINARY, name="Transportation2")

# Set objective to minimize cost
model.setObjective(5200 * a1 + 5500 * a2 + 6300 * a3 + 510 * u1 + 500 * u2 +
                   500 * b1 + 800 * b2 + 1700 * t1 + 2500 * t2, gp.GRB.MINIMIZE)
```

## Adding Constraints

A vacation package should adhere to certain constraints to be enjoyable. Here are the constraints we've added to our model:

1. **Select Exactly One Activity:** We ensure that at least one activity is selected.

```python
model.addConstr(a1 + a2 + a3 == 1, "One_Activity")
```

2. **Upgrades Based on Activities:** You can only choose upgrades for the selected activities.

```python
model.addConstr(u1 <= a1, "Upgrade_Activity1")
model.addConstr(u2 <= a2, "Upgrade_Activity2")
```

3. **Select Only One Upgrade:** You can select only one upgrade.

```python
model.addConstr(u1 + u2 <= 1, "Only_One_Upgrade")
```

4. **Select One Accommodation:** You must choose one accommodation.

```python
model.addConstr(b1 + b2 == 1, "One_Accommodation")
```

5. **Upgrade Constraint for Accommodation:** You must choose Accommodation 2 if you select an upgrade.

```python
model.addConstr(u1 + u2 <= b2, "Upgrade_Accommodation2")
```

6. **Transportation Constraint for Activity 3:** Transportation 1 can only be used if you do Activity 3 or upgrade. 

```python
model.addConstr(t1 <= a3 + u1 + u2, "Transportation1_Condition")
```

7. **Minimum Time Spent Constraint:** Your total time spent on activities and upgrades should be at least 90 units.

```python
model.addConstr(35 * a1 + 70 * a2 + 65 * a3 + 30 * u1 + 25 * u2 >= 90, "Minimum_Time_Spent")
```

## Optimization

After setting up the model and constraints, it's time to find the optimal solution that minimizes the cost.

```python
# Optimize the model
model.optimize()
```

## Analyzing the Results

The optimization process will determine the optimal vacation package for you. If a feasible solution is found, the details will be printed, including the selected activities, upgrades, accommodations, and transportation options.

```python
# Print the results
if model.status == gp.GRB.OPTIMAL:
    print(f"Optimal Solution Found: Cost = ${model.objVal:.2f}")
    print("Activity 1:", a1.X)
    print("Activity 2:", a2.X)
    print("Activity 3:", a3.X)
    print("Upgrade 1:", u1.X)
    print("Upgrade 2:", u2.X)
    print("Accommodation 1:", b1.X)
    print("Accommodation 2:", b2.X)
    print("Transportation 1:", t1.X)
    print("Transportation 2:", t2.X)
else:
    print("No optimal solution found.")
```

## Conclusion

Optimizing your vacation package with Gurobi ensures that you can enjoy your dream vacation while minimizing costs and adhering to your preferences. This example demonstrates how mathematical optimization can be a valuable tool in decision-making processes, helping you make the most of your travel plans.

The optimal solution we found recommends the following choices for your vacation package:

- **Cost:** $8,500.00
- **Activity Selection:**
   - Activity 1: Not selected
   - Activity 2: Selected
   - Activity 3: Not selected
- **Upgrade Selection:**
   - Upgrade 1: Not selected
   - Upgrade 2: Selected
- **Accommodation Selection:**
   - Accommodation 1: Not selected
   - Accommodation 2: Selected
- **Transportation Selection:**
   - Transportation 1: Selected
   - Transportation 2: Not selected

This package balances preferences and constraints while minimizing costs, ensuring an enjoyable and cost-effective vacation experience.

With the power of mathematical optimization, you can now embark on your perfect vacation adventure, knowing that your choices have been carefully crafted to maximize your experience and minimize expenses.
