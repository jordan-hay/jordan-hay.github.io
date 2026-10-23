---
layout: post
title:  "Decision Trees in Machine Learning: Understanding Entropy and Information Gain with Python"
date:   2026-9-10 09:25:17 -0800
categories: jekyll update data
---

<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/decision_tree_information_gain.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>
# Introduction

Decision trees are among the most intuitive machine learning algorithms. They make predictions by asking a sequence of questions about the input data. But how does a decision tree decide which question to ask first?

The answer lies in two fundamental concepts from information theory: Entropy and Information Gain.

In this tutorial, we will explore the mathematics behind decision trees, calculate information gain step by step using a weather dataset, and implement a decision tree using Python and scikit-learn.

By the end, you will understand not only how to train a decision tree but also how the algorithm selects its splitting features.

## 1. What Is a Decision Tree?

A decision tree is a supervised machine learning algorithm used for classification and regression.

In classification, the algorithm repeatedly divides a dataset into smaller groups based on feature values. Its objective is to create groups containing observations that belong to the same class.

For example, suppose we want to predict whether someone will play outside based on weather conditions.

Our dataset contains four input features:

- Outlook: Sunny, Overcast, or Rainy
- Temperature: Hot, Mild, or Cool
- Humidity: High or Normal
- Windy: True or False

The target variable is Play Outside, which has two possible classes: Yes and No.

A decision tree might begin by asking:

What is the outlook?

Depending on the answer, it may ask additional questions about humidity or wind.

However, a decision tree should not choose its first question randomly. It should select a feature that reduces uncertainty about the target variable as much as possible.

This is where entropy and information gain become important.

## 2. Understanding Entropy

Entropy is a mathematical measure of uncertainty in a dataset.

In machine learning classification, entropy measures how mixed the target classes are.

If every observation belongs to the same class, there is no uncertainty, and entropy is zero.

If the classes are equally represented, uncertainty is maximized.

### Entropy formula

For a target variable \\(Y\\) containing \\(k\\) classes:

\\[ \boxed{H(Y)=-\sum\_{i=1}^{k}p_i\log_2(p_i)} \\]

Where:

- \\(H(Y)\\) is the entropy of the target variable.
- \\(p_i\\) is the probability of class \\(i\\).
- \\(k\\) is the number of classes.
- \\(\log_2\\) is the logarithm with base 2.

For binary classification with Yes and No:

\\[ H(Y)=-p\_{\text{Yes}}\log_2(p\_{\text{Yes}})-p\_{\text{No}}\log_2(p\_{\text{No}}) \\]

We define \\(0\log_2(0)=0\\), so the formula works even when a class is absent.

### Example: A balanced dataset

Suppose we have 10 observations:

- 5 Yes
- 5 No

Then:

\\[ p\_{\text{Yes}}=0.5,\qquad p\_{\text{No}}=0.5 \\]

\\[ H(Y)=-0.5\log_2(0.5)-0.5\log_2(0.5) \\]

\\[ \boxed{H(Y)=1\text{ bit}} \\]

This is the maximum entropy for binary classification.

### Example: A perfectly pure dataset

Suppose all 10 observations belong to the Yes class.

\\[ p\_{\text{Yes}}=1,\qquad p\_{\text{No}}=0 \\]

\\[ H(Y)=-1\log_2(1)-0\log_2(0) \\]

\\[ \boxed{H(Y)=0} \\]

There is no uncertainty because every observation has the same label.

## 3. Creating the Weather Dataset

We will use a classic weather dataset containing 14 observations.

The following code is designed for Google Colab or Jupyter Notebook. The `%%writefile` command creates a CSV file in the current notebook directory.

```
%%writefile weather.csvOutlook,Temperature,Humidity,Windy,Play OutsideSunny,Hot,High,False,NoSunny,Hot,High,True,NoOvercast,Hot,High,False,YesRainy,Mild,High,False,YesRainy,Cool,Normal,False,YesRainy,Cool,Normal,True,NoOvercast,Cool,Normal,True,YesSunny,Mild,High,False,NoSunny,Cool,Normal,False,YesRainy,Mild,Normal,False,YesSunny,Mild,Normal,True,YesOvercast,Mild,High,True,YesOvercast,Hot,Normal,False,YesRainy,Mild,High,True,No
```

Now import the necessary libraries and load the dataset.

```
import pandas as pdimport numpy as npimport matplotlib.pyplot as pltfrom math import log2from sklearn.tree import (    DecisionTreeClassifier,    plot_tree,    _tree)from sklearn.preprocessing import OneHotEncoderweather = pd.read_csv("weather.csv")display(weather)print("Class counts:")print(weather["Play Outside"].value_counts())
```

The target distribution is:

| Class | Count | Probability |
| ----- | ----- | ----------- |
| Yes   | 9     | 9/14        |
| No    | 5     | 5/14        |
| Total | 14    | 1           |

This distribution will be used to calculate our initial entropy.

## 4. Calculating the Entropy of the Target Variable

We have 9 Yes observations and 5 No observations.

Therefore:

\\[ p\_{\text{Yes}}=\frac{9}{14} \\]

\\[ p\_{\text{No}}=\frac{5}{14} \\]

Substitute these probabilities into the entropy formula:

\\[ H(Y)=-\frac{9}{14}\log_2\left(\frac{9}{14}\right)-\frac{5}{14}\log_2\left(\frac{5}{14}\right) \\]

The result is:

\\[ \boxed{H(Y)\approx0.9403\text{ bits}} \\]

This is our starting uncertainty before asking any questions about the weather.

### Python implementation

We can calculate entropy using a reusable function.

```
def entropy(labels):    counts = pd.Series(labels).value_counts()    probabilities = counts / counts.sum()    return -sum(        p * log2(p)        for p in probabilities        if p > 0    )y = weather["Play Outside"]base_entropy = entropy(y)print("Yes =", (y == "Yes").sum())print("No =", (y == "No").sum())print(f"Entropy = {base_entropy:.6f} bits")
```

Expected output:

```
Yes = 9
No = 5
Entropy = 0.940286 bits
```

Now we need to determine which feature reduces this uncertainty the most.

## 5. What Is Information Gain?

Information Gain measures how much uncertainty is reduced after splitting a dataset using a particular feature.

In simple terms:

Information Gain = Entropy Before Splitting − Entropy After Splitting

The mathematical formula is:

\\[ \boxed{IG(Y,X)=H(Y)-H(Y\mid X)} \\]

Here:

- \\(Y\\) is the target variable.
- \\(X\\) is a candidate splitting feature.
- \\(H(Y)\\) is the entropy before splitting.
- \\(H(Y\mid X)\\) is the expected entropy after splitting.

For a categorical feature with multiple possible values:


\\[
\boxed{
IG(Y,X)=H(Y)-\sum_{v\in X}\frac{|S_v|}{|S|}H(Y\mid X=v)
}
\\]

Where \\(S\\) is the full dataset and \\(S_v\\) is the subset containing observations where feature \\(X\\) has value \\(v\\).

Each branch entropy is weighted by the proportion of observations belonging to that branch.

A feature with higher information gain is generally preferred because it provides a larger reduction in uncertainty.

## 6. Manual Calculation: Information Gain for Humidity

Let's evaluate Humidity as our first possible question.

Humidity has two categories: High and Normal.

The class distribution is:

| Humidity | Yes | No | Total |
| -------- | --- | -- | ----- |
| High     | 3   | 4  | 7     |
| Normal   | 6   | 1  | 7     |

### Step 1: Calculate entropy for High humidity

\\[ H(\text{High})=-\frac{3}{7}\log_2\left(\frac{3}{7}\right)-\frac{4}{7}\log_2\left(\frac{4}{7}\right) \\]

\\[ \boxed{H(\text{High})\approx0.9852} \\]

### Step 2: Calculate entropy for Normal humidity

\\[ H(\text{Normal})=-\frac{6}{7}\log_2\left(\frac{6}{7}\right)-\frac{1}{7}\log_2\left(\frac{1}{7}\right) \\]

\\[ \boxed{H(\text{Normal})\approx0.5917} \\]

### Step 3: Calculate weighted entropy

Each branch contains 7 of the 14 observations.

\\[ H(Y\mid\text{Humidity})=\frac{7}{14}(0.9852)+\frac{7}{14}(0.5917) \\]

\\[ \boxed{H(Y\mid\text{Humidity})\approx0.7885} \\]

### Step 4: Calculate information gain

\\[ IG(Y,\text{Humidity})=0.9403-0.7885 \\]

\\[ \boxed{IG(Y,\text{Humidity})\approx0.1518} \\]

By asking about humidity, we reduce the uncertainty by approximately 0.1518 bits.

### Python implementation

```
feature = "Humidity"weighted_after = 0.0for value, subset in weather.groupby(feature):    branch_entropy = entropy(subset["Play Outside"])    weight = len(subset) / len(weather)    weighted_after += weight * branch_entropy    print(        f"{value}: "        f"n={len(subset)}, "        f"Yes={(subset['Play Outside'] == 'Yes').sum()}, "        f"No={(subset['Play Outside'] == 'No').sum()}, "        f"Entropy={branch_entropy:.6f}, "        f"Weight={weight:.3f}"    )gain = base_entropy - weighted_afterprint(f"\nEntropy before: {base_entropy:.6f}")print(f"Entropy after: {weighted_after:.6f}")print(f"Information Gain: {gain:.6f}")
```

Humidity is a useful feature, but is it the best first question? To find out, we need to evaluate every candidate feature.

## 7. Comparing Information Gain Across All Features

Our dataset contains four candidate features:

1. Outlook
2. Temperature
3. Humidity
4. Windy

We calculate information gain for each feature using the same formula.

### Outlook

Outlook has three categories:

| Outlook  | Yes | No | Total | Entropy |
| -------- | --- | -- | ----- | ------- |
| Sunny    | 2   | 3  | 5     | 0.9710  |
| Overcast | 4   | 0  | 4     | 0       |
| Rainy    | 3   | 2  | 5     | 0.9710  |

The weighted entropy after splitting is:

\\[ H(Y\mid\text{Outlook})=\frac{5}{14}(0.9710)+\frac{4}{14}(0)+\frac{5}{14}(0.9710) \\]

\\[ H(Y\mid\text{Outlook})\approx0.6935 \\]

Therefore:

\\[ IG(Y,\text{Outlook})=0.9403-0.6935 \\]

\\[ \boxed{IG(Y,\text{Outlook})\approx0.2467} \\]

Notice that every Overcast observation belongs to the Yes class. This creates a perfectly pure branch with entropy zero.

### Information Gain comparison

The results for all four features are:

| Feature     | Entropy after | Information Gain |
| ----------- | ------------- | ---------------- |
| Outlook     | 0.6935        | 0.2467           |
| Humidity    | 0.7885        | 0.1518           |
| Windy       | 0.8922        | 0.0481           |
| Temperature | 0.9111        | 0.0292           |

Outlook has the highest information gain.

Therefore, for a multiway categorical decision tree:

\\[ \boxed{X\_{\text{best}}=\text{Outlook}} \\]

This means Outlook is the best first question among the four candidate features when we allow one branch for each category.

### Python implementation for all features

Rather than manually repeating calculations, we can create a function that computes information gain for any categorical feature.

```
        after += weight * branch_entropy        if verbose:            print(                f"{category}: "                f"n={len(subset)}, "                f"weight={weight:.3f}, "                f"entropy={branch_entropy:.6f}"            )    gain = before - after    return before, after, gainX = weather.drop(columns="Play Outside")scores = []for feature in X.columns:    before, after, gain = manual_information_gain(        weather,        feature    )    scores.append({        "Question": feature,        "Entropy before": before,        "Weighted entropy after": after,        "Information Gain": gain    })score_table = pd.DataFrame(scores).sort_values(    "Information Gain",    ascending=False)display(    score_table.style.format({        "Entropy before": "{:.4f}",        "Weighted entropy after": "{:.4f}",        "Information Gain": "{:.4f}"    }))best = score_table.iloc[0]print(    f"BEST FIRST QUESTION: {best['Question']} "    f"(IG = {best['Information Gain']:.6f})")print("\nDetailed calculation for the winner:")manual_information_gain(    weather,    best["Question"],    verbose=True)
```

We can also generate a bar chart in Python to compare the information gain values. The blog remains text-only; the following code produces the chart when executed in a notebook.

```
plt.figure(figsize=(8, 4))plt.bar(    score_table["Question"],    score_table["Information Gain"])plt.title("Manual Information Gain by Feature")plt.xlabel("Feature")plt.ylabel("Information Gain (bits)")plt.ylim(0, 0.30)plt.tight_layout()plt.show()
```

## 8. Training a Decision Tree with scikit-learn

Now that we understand the mathematical calculations, let's train a decision tree using scikit-learn.

We will use `DecisionTreeClassifier` with the entropy criterion.

One important consideration is that our input features are categorical. We need to convert them into numerical representations.

### One-hot encoding

One-hot encoding transforms each category into a separate binary column.

For example, Outlook becomes:

| Outlook  | Outlook_Sunny | Outlook_Overcast | Outlook_Rainy |
| -------- | ------------- | ---------------- | ------------- |
| Sunny    | 1             | 0                | 0             |
| Overcast | 0             | 1                | 0             |
| Rainy    | 0             | 0                | 1             |

This representation allows scikit-learn to perform binary splits.

Important distinction: Our manual Outlook calculation used a three-way split, while scikit-learn's decision tree uses binary splits on encoded features. The resulting root information gain may therefore differ.

### Train the model

```
X = weather.drop(columns="Play Outside")y = weather["Play Outside"]encoder = OneHotEncoder(    sparse_output=False,    handle_unknown="ignore")X_encoded = encoder.fit_transform(X)feature_names = encoder.get_feature_names_out(    X.columns)clf = DecisionTreeClassifier(    criterion="entropy",    random_state=42)clf.fit(X_encoded, y)print("Training accuracy:", clf.score(X_encoded, y))print(    "Root feature:",    feature_names[clf.tree_.feature[0]])
```

Here, `criterion="entropy"` tells scikit-learn to evaluate candidate splits using entropy reduction.

The `random_state=42` parameter makes the model's tie-breaking and other randomized behavior reproducible.

Training accuracy measures how well the model predicts the observations it was trained on. It should not be interpreted as performance on unseen data.

### Visualizing the trained tree with Python

```
plt.figure(figsize=(18, 9))plot_tree(    clf,    feature_names=feature_names,    class_names=clf.classes_,    filled=True,    rounded=True,    impurity=True,    proportion=False,    fontsize=9)plt.title(    "scikit-learn Decision Tree (Entropy Criterion)")plt.show()
```

Each internal node represents a binary question, such as whether an encoded feature is less than or equal to 0.5.

The node also reports its entropy, sample count, class distribution, and predicted class.

## 9. Calculating Information Gain from the Trained Tree

So far, we have manually calculated information gain for the original categorical features.

Now we will calculate information gain directly from the decision tree trained by scikit-learn.

The trained tree is accessible through:

```
clf.tree_
```

This object contains information about every node, including its entropy, number of samples, split feature, and child nodes.

For a binary split, information gain is:

\\[ \boxed{IG=H(P)-\frac{n_L}{n}H(L)-\frac{n_R}{n}H(R)} \\]

Where:

- \\(H(P)\\) is the parent node's entropy.
- \\(H(L)\\) and \\(H(R)\\) are the left and right child entropies.
- \\(n_L\\) and \\(n_R\\) are the weighted sample counts of the child nodes.
- \\(n\\) is the weighted sample count of the parent node.

### Python implementation

```
t = clf.tree_rows = []for node in range(t.node_count):    left = t.children_left[node]    right = t.children_right[node]    if left == _tree.TREE_LEAF:        continue    n = t.weighted_n_node_samples[node]    nl = t.weighted_n_node_samples[left]    nr = t.weighted_n_node_samples[right]    entropy_after = (        (nl / n) * t.impurity[left]        + (nr / n) * t.impurity[right]    )    gain = t.impurity[node] - entropy_after    rows.append({        "node": node,        "binary question": feature_names[t.feature[node]],        "samples": int(t.n_node_samples[node]),        "entropy before": round(t.impurity[node], 4),        "entropy after": round(entropy_after, 4),        "information gain": round(gain, 4)    })node_gains = pd.DataFrame(rows)display(node_gains)print(
```

The resulting table reports the local information gain for each internal node.

This is different from our manual comparison because the questions are binary splits of one-hot encoded columns rather than multiway splits of the original features.

## 10. Feature Importance: Combining Information Gain Across the Tree

A feature may be used more than once in a decision tree.

To measure its overall contribution, we can aggregate its information gain across all nodes where it is used.

However, a split affecting 100 observations should generally contribute more to global feature importance than an equally informative split affecting only 5 observations.

This motivates weighted information gain.

For node \\(t\\):

\\[ WIG_t=\frac{n_t}{N}IG_t \\]

Where:

- \\(n_t\\) is the weighted number of samples reaching node \\(t\\).
- \\(N\\) is the weighted total number of training samples.
- \\(IG_t\\) is the local information gain at node \\(t\\).

The total importance of a feature \\(X_j\\) is:

\\[ I(X_j)=\sum\_{t:\\,\text{split}(t)=X_j}\frac{n_t}{N}IG_t \\]

We then normalize the importance values:

\\[ \boxed{FI(X_j)=\frac{I(X_j)}{\sum_k I(X_k)}} \\]

This produces relative feature importance values that sum to 1, provided the tree has at least one positive-gain split.

### Python implementation

First, inspect the feature importance values provided by scikit-learn.

```
sklearn_importance = pd.Series(    clf.feature_importances_,    index=feature_names).sort_values(ascending=False)print("scikit-learn feature importance:")display(    sklearn_importance.to_frame("importance"))
```

Now calculate the weighted information gain ourselves, using unrounded node values to avoid unnecessary numerical error.

```
t = clf.tree_weighted_gains = []total_samples = t.weighted_n_node_samples[0]for node in range(t.node_count):    left = t.children_left[node]    right = t.children_right[node]    if left == _tree.TREE_LEAF:        continue    n = t.weighted_n_node_samples[node]    nl = t.weighted_n_node_samples[left]    nr = t.weighted_n_node_samples[right]    entropy_after = (        (nl / n) * t.impurity[left]        + (nr / n) * t.impurity[right]    )    gain = t.impurity[node] - entropy_after    weighted_gains.append({        "encoded_feature": feature_names[t.feature[node]],        "weighted_gain": (n / total_samples) * gain    })gain_df = pd.DataFrame(weighted_gains)encoded_importance = gain_df.groupby(    "encoded_feature")["weighted_gain"].sum()
```

To combine one-hot encoded columns into their original features, we can aggregate using the original feature names.

```
original_features = list(X.columns)def original_feature_name(encoded_name):    for feature in original_features:        if encoded_name.startswith(feature + "_"):            return feature    raise ValueError(f"Unknown feature: {encoded_name}")gain_df["feature"] = gain_df[    "encoded_feature"].apply(original_feature_name)feature_importance = gain_df.groupby(    "feature")["weighted_gain"].sum()feature_importance = (    feature_importance / feature_importance.sum()).sort_values(ascending=False)print("Aggregated feature importance:")print(feature_importance)
```

These values summarize the total entropy reduction contributed by each original feature across the trained binary tree.

They should not be confused with the information gain of a single multiway root question.

Also, impurity-based feature importance describes the fitted model; it does not necessarily establish causal importance or predictive usefulness on unseen data.

## 11. Why Might scikit-learn Choose a Different First Question?

This is one of the most important distinctions in the tutorial.

In our manual calculation, we evaluated the original Outlook feature as a multiway question:

What is the Outlook?

This creates three branches:

- Sunny
- Overcast
- Rainy

The corresponding information gain is approximately:

\\[ IG(\text{Outlook})=0.2467 \\]

However, after one-hot encoding, scikit-learn evaluates binary questions such as:

Is Outlook Overcast?

That question creates two groups:

- Overcast
- Not Overcast

The information gain of this particular binary split is approximately:

\\[ IG(\text{Outlook_Overcast})=0.2260 \\]

We can verify this manually.

For the Overcast branch, all 4 observations are Yes, so its entropy is 0.

For the Not Overcast branch, there are 5 Yes and 5 No observations, so its entropy is 1.

Therefore:

\\[ IG=0.9403-\left(\frac{4}{14}(0)+\frac{10}{14}(1)\right) \\]

\\[ \boxed{IG\approx0.2260} \\]

Compare the two:

| Question          | Split type | Information Gain |
| ----------------- | ---------- | ---------------- |
| Outlook?          | Three-way  | 0.2467           |
| Outlook Overcast? | Binary     | 0.2260           |

Both calculations are correct, but they represent different candidate splits.

The first calculation evaluates an entire categorical feature in one step. The second evaluates a single binary indicator.

This is why a manually constructed multiway decision tree and a scikit-learn decision tree may have different structures.

## 12. Entropy vs. Gini Impurity

Decision trees can use different measures to evaluate split quality.

Two common choices are entropy and Gini impurity.

### Entropy

\\[ H(Y)=-\sum\_{i=1}^{k}p_i\log_2(p_i) \\]

Entropy measures uncertainty in bits.

### Gini impurity

\\[ \boxed{G(Y)=1-\sum\_{i=1}^{k}p_i^2} \\]

Gini impurity measures how mixed the classes are using squared class probabilities.

For our dataset:

\\[ G(Y)=1-\left(\frac{9}{14}\right)^2-\left(\frac{5}{14}\right)^2 \\]

\\[ \boxed{G(Y)\approx0.4592} \\]

For a binary target, the maximum Gini impurity is 0.5, whereas the maximum entropy is 1 bit.

| Property                | Entropy                  | Gini               |
| ----------------------- | ------------------------ | ------------------ |
| Formula                 | \\(-\sum p_i\log_2p_i\\) | \\(1-\sum p_i^2\\) |
| Pure node               | 0                        | 0                  |
| Maximum for two classes | 1                        | 0.5                |
| Uses logarithms         | Yes                      | No                 |
| scikit-learn criterion  | `"entropy"`              | `"gini"`           |

We can compare the two criteria using Python.

```
entropy_tree = DecisionTreeClassifier(    criterion="entropy",    random_state=42)gini_tree = DecisionTreeClassifier(    criterion="gini",    random_state=42)entropy_tree.fit(X_encoded, y)gini_tree.fit(X_encoded, y)print("Entropy tree accuracy:",      entropy_tree.score(X_encoded, y))print("Gini tree accuracy:",      gini_tree.score(X_encoded, y))print(    "Entropy root:",    feature_names[entropy_tree.tree_.feature[0]])print(    "Gini root:",    feature_names[gini_tree.tree_.feature[0]])
```

The two criteria may select the same or different splits, depending on the dataset.

Neither is universally better. Their performance should be compared using appropriate validation data.

## 13. Limitations of Information Gain

Although information gain is useful, it has several limitations.

Bias toward features with many categories. In a multiway decision tree, a feature with many distinct values can create numerous small, potentially pure groups. Such splits may achieve high training information gain without generalizing well.

Overfitting. An unrestricted decision tree can learn patterns specific to the training data, including noise. Techniques such as maximum depth, minimum samples per leaf, and pruning can reduce overfitting.

Sensitivity to the training dataset. Small changes in the data can lead to different split choices and tree structures.

Feature importance is not causality. A feature that produces large impurity reductions is useful for the fitted tree, but that does not mean changing the feature would cause the predicted outcome to change.

For practical machine learning applications, evaluate decision trees on held-out data or with cross-validation rather than relying only on training accuracy.

## 14. Key Takeaways

We started with a simple question: How does a decision tree decide which feature to split on first?

We learned that entropy quantifies uncertainty, while information gain measures the reduction in uncertainty achieved by a split.

For our weather dataset:

\\[ H(\text{Play Outside})\approx0.9403 \\]

The manual multiway information gains were:

\\[ \begin{aligned} IG(\text{Outlook})&=0.2467\\\ IG(\text{Humidity})&=0.1518\\\ IG(\text{Windy})&=0.0481\\\ IG(\text{Temperature})&=0.0292 \end{aligned} \\]

Therefore, Outlook is the best first question for a multiway categorical decision tree.

We also implemented a decision tree with scikit-learn, extracted information gain from its trained nodes, and calculated normalized feature importance.

Most importantly, we saw why a manual multiway categorical split and a scikit-learn binary split are not directly interchangeable.

Understanding this distinction helps us move beyond simply calling `.fit()` and toward understanding how decision tree algorithms actually learn.

