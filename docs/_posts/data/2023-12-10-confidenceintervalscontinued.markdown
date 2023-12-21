---
layout: post
title:  "
Confidence Intervals: A Practical Guide in Python"
date:   2023-12-10 06:25:17 -0800
categories: jekyll update data
---


### Introduction:

In our original blog post, we delved into the world of confidence intervals, exploring their pivotal role in statistical inference. We uncovered the underlying principles, from the standard normal distribution to Z-scores and significance levels. The exploration was accompanied by Python code for visualizing these concepts, laying a solid foundation for understanding and applying confidence intervals.

Now, in this follow-up blog, we take a step further, building upon the knowledge gained. We'll address different practical scenarios, incorporating functions that calculate confidence intervals introduced in the original discussion. These functions, implemented using the scipy.stats library, empower us to handle diverse situations, whether we know the population standard deviation, need to plan sample sizes, or deal with unknown population standard deviations.

In the world of statistics, confidence intervals are invaluable tools for estimating the range within which a population parameter is likely to fall. Building upon our previous discussions, we'll delve deeper into practical scenarios using Python and the `scipy.stats` library.

### Calculating Confidence Intervals with Known Population Standard Deviation

In this section, we explore the function `calculate_confidence_interval_mean` designed for scenarios where we have a known population standard deviation. Here's a breakdown of the code:

```python
import scipy.stats as stats

def calculate_confidence_interval_mean(sample_mean, population_std, sample_size, confidence_level):
    # Calculate the Z-score based on the confidence level
    z_score = stats.norm.ppf(1 - (1 - confidence_level) / 2) # percent-point function

    # Calculate the margin of error
    margin_of_error = z_score * (population_std / (sample_size ** 0.5))

    # Calculate the confidence interval
    lower_bound = sample_mean - margin_of_error
    upper_bound = sample_mean + margin_of_error

    return lower_bound, upper_bound
```

**Explanation:**
- The function uses the Z-score, calculated using the percent-point function (`ppf`) of the standard normal distribution, to determine the critical value.
- It then computes the margin of error based on the Z-score, population standard deviation, and sample size.
- The confidence interval is formed by subtracting and adding the margin of error from the sample mean.

**Example Usage:**
```python
sample_mean = 75
population_std = 10
sample_size = 30
confidence_level = 0.95

lower, upper = calculate_confidence_interval_mean(sample_mean, population_std, sample_size, confidence_level)

print(f"{int(confidence_level*100)}% Confidence Interval for Mean: ({lower}, {upper})")
print(f"{int(confidence_level*100)}% Confidence Interval for Mean: {sample_mean} \u00B1 {round((upper-lower)/2,3)}")
```

This example demonstrates how to use the function to calculate a confidence interval for the mean when the population standard deviation is known.

### Planning Sample Sizes for Desired Margin of Error

Now, let's shift our focus to a different scenario where the objective is to plan sample sizes to achieve a specific margin of error. The function `calculate_sample_size_for_margin_of_error` is tailored for this purpose:

```python
import scipy.stats as stats

def calculate_sample_size_for_margin_of_error(margin_of_error, population_std, confidence_level):
    # Calculate the Z-score based on the confidence level
    z_score = stats.norm.ppf(1 - (1 - confidence_level) / 2)

    # Solve for sample size in the margin of error formula
    sample_size = ((z_score * population_std) / margin_of_error) ** 2

    return round(sample_size)
```

**Explanation:**
- Similar to the previous function, it computes the Z-score based on the confidence level.
- It then rearranges the margin of error formula to solve for the required sample size.

**Example Usage:**
```python
margin_of_error = 2
population_std = 10
confidence_level = 0.95

sample_size = calculate_sample_size_for_margin_of_error(margin_of_error, population_std, confidence_level)

print(f"To achieve a {int(confidence_level*100)}% confidence level with a margin of error of {margin_of_error}, you need a sample size of approximately {sample_size}.")
```

This example illustrates how to use the function to determine the sample size necessary to meet specific confidence level and margin of error criteria.

### Handling Unknown Population Standard Deviation

In scenarios where the population standard deviation is unknown, we turn to the `calculate_confidence_interval_mean_unknown_std` function:

```python
import scipy.stats as stats

def calculate_confidence_interval_mean_unknown_std(sample_mean, sample_std, sample_size, confidence_level):
    # Calculate the t-score based on the confidence level and degrees of freedom
    degrees_of_freedom = sample_size - 1
    t_score = stats.t.ppf(1 - (1 - confidence_level) / 2, degrees_of_freedom)

    # Calculate the margin of error
    margin_of_error = t_score * (sample_std / (sample_size ** 0.5))

    # Calculate the confidence interval
    lower_bound = sample_mean - margin_of_error
    upper_bound = sample_mean + margin_of_error

    return lower_bound, upper_bound
```

**Explanation:**
- Instead of using the Z-score, this function employs the t-score, calculated from the t-distribution, as the critical value.
- The degrees of freedom are determined by subtracting 1 from the sample size.
- The remaining steps are analogous to the first function.

**Example Usage:**
```python
sample_mean = 75
sample_std = 10
sample_size = 30
confidence_level = 0.95

lower, upper = calculate_confidence_interval_mean_unknown_std(sample_mean, sample_std, sample_size, confidence_level)

print(f"{int(confidence_level*100)}% Confidence Interval for Mean: ({lower}, {upper})")
print(f"{int(confidence_level*100)}% Confidence Interval for Mean: {sample_mean} \u00B1 {round((upper-lower)/2,3)}")
```

This example showcases how to use the function when the population standard deviation is unknown, relying on the t-distribution for critical values.





