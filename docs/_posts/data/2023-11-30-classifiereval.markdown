---
layout: post
title:  "Evaluation of Classifier Performance"
date:   2023-11-30 06:25:17 -0800
categories: jekyll update data
---
<a target="_blank" href="https://colab.research.google.com/github/jordan-hay/jordan-hay.github.io/blob/main/docs/assets/Evaluation_of_Classifier_Performance.ipynb
">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

### Introduction
In the realm of machine learning, the efficacy of a model extends beyond its training phase; assessing its performance on unseen data is equally critical. This review explores various methodologies employed for model evaluation and selection, shedding light on the diverse techniques that contribute to a thorough understanding of a model's capabilities.

#### Holdout Method
The holdout method is a straightforward approach where the dataset is split into two subsets: a training set used to train the model and a testing set used to evaluate its performance. The method allows assessing how well the model generalizes to unseen data.

#### Leave-One-Out Cross-Validation
Leave-One-Out cross-validation (LOOCV) is a special case of k-fold cross-validation where k is equal to the number of samples. For each iteration, one sample is used as the test set, and the model is trained on the remaining samples. This process is repeated for each sample. LOOCV is useful for small datasets, but it can be computationally expensive for larger datasets.

#### Bootstrap Resampling
Bootstrap resampling involves generating multiple bootstrap samples by randomly drawing with replacement from the original dataset. Each bootstrap sample is used to train and test the model. This technique helps assess the variability of the model's performance and provides more robust estimates.

#### Cross-Validation
Cross-validation is a systematic way to assess a model's performance by dividing the dataset into training and testing sets multiple times. Common methods include k-fold cross-validation, where the dataset is divided into k subsets, and stratified cross-validation, which ensures that each class is represented proportionally in both training and testing sets.

#### Stratified Cross-Validation
Stratified cross-validation is especially useful when dealing with imbalanced datasets. It ensures that each class is proportionally represented in both training and testing sets, reducing the risk of biased model evaluation.


#### Confusion Matrix
A confusion matrix provides a detailed breakdown of a model's performance by categorizing predictions into true positives, true negatives, false positives, and false negatives. It serves as the foundation for various performance metrics.

#### Sensitivity, Specificity, Precision, Recall, Accuracy
- Sensitivity (Recall): The proportion of actual positive instances correctly identified by the model.
- Specificity: The proportion of actual negative instances correctly identified by the model.
- Precision: The proportion of predicted positive instances that are actually positive.
- Recall: Synonymous with sensitivity, it measures the model's ability to capture all positive instances.
- Accuracy: The overall correctness of the model's predictions.

#### F1 Score

The F1 score is a metric commonly used in binary classification to evaluate the balance between precision and recall. It is the harmonic mean of precision and recall and is defined by the following formula:

$$ F1 = \frac{2 \times \text{precision} \times \text{recall}}{\text{precision} + \text{recall}} $$

where:
- Precision is the number of true positives divided by the sum of true positives and false positives: $\text{precision} = \frac{TP}{TP + FP}$
- Recall is the number of true positives divided by the sum of true positives and false negatives: $\text{recall} = \frac{TP}{TP + FN}$

The F1 score ranges from 0 to 1, with 1 being the best possible F1 score (perfect precision and recall) and 0 being the worst. The F1 score is particularly useful in situations where there is an uneven class distribution (imbalanced dataset) because it considers both false positives and false negatives.

In some cases, there may be a trade-off between precision and recall. The F1 score provides a single value that balances both measures, making it a useful metric for binary classification tasks.

#### Matthews Correlation Coefficient (MCC)
MCC is a correlation coefficient between the observed and predicted binary classifications. It considers all four elements of the confusion matrix and is particularly useful for imbalanced datasets.

The MCC is a measure of the quality of binary classifications, particularly in the context of imbalanced datasets. It takes into account true and false positives and negatives and is considered a balanced measure even if the classes are of very different sizes. MCC is calculated using the formula:

$$ MCC = \frac{TP \times TN - FP \times FN}{\sqrt{(TP + FP)(TP + FN)(TN + FP)(TN + FN)}} $$

where:
- $ TP $ is the number of true positives,
- $ TN $ is the number of true negatives,
- $ FP $ is the number of false positives, and
- $ FN $ is the number of false negatives.

MCC ranges from -1 to 1, where 1 indicates a perfect prediction, 0 indicates no better than random prediction, and -1 indicates total disagreement between prediction and observation.

Key points about MCC:

1. **Balance**: MCC is considered balanced even if the classes are of different sizes. This is particularly useful when dealing with imbalanced datasets where one class significantly outnumbers the other.

2. **Range**: The range of MCC is from -1 to 1, with 1 representing perfect prediction, 0 indicating random prediction, and -1 indicating complete disagreement between prediction and observation.

3. **Interpretation**:
   - $1$: Perfect agreement between prediction and observation.
   - $0$: No better than random prediction.
   - $-1$: Complete disagreement between prediction and observation.

4. **Use in Machine Learning**: MCC is commonly used in the evaluation of binary classification models, especially when the classes are imbalanced. It provides a comprehensive assessment by considering all four elements of the confusion matrix.

When working with imbalanced datasets or when a balanced evaluation metric is needed, MCC can be a more informative measure compared to accuracy, especially in situations where the distribution of the classes is uneven.

#### Receiver Operating Characteristic (ROC) Curve

The ROC curve is a graphical representation of a classifier's performance across different classification thresholds. It plots the true positive rate against the false positive rate, helping to visualize trade-offs between sensitivity and specificity.

#### Cumulative Gains Curve
The cumulative gains curve illustrates the cumulative proportion of positive instances captured by a model as a certain percentage of the sample is considered. It aids in understanding the model's effectiveness in identifying positive instances.

#### Lift Curve
The lift curve compares a model's performance to a random predictor. It shows how much better the model is at identifying positive instances compared to random chance, especially as the percentage of the sample increases.

#### Decile Lift Chart
The decile lift chart divides the data into ten equal parts based on predicted probabilities. It calculates the cumulative gains in each decile, helping to assess the model's performance across different segments of the data.

### Conclusion
These concepts collectively form a comprehensive toolkit for evaluating the performance of classification models, providing insights into their strengths, weaknesses, and areas for improvement.



# Appendix

## Exploratory Data Analysis (EDA)

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
import gdown

## Download and extract the dataset
url = "https://github.com/gedeck/dmba/raw/master/datasets/dmba-datasets.zip"
gdown.download(url, 'file.zip', quiet=True)
!unzip file.zip &> /dev/null

## Load the dataset
df = pd.read_csv('/content/dmba/eBayAuctions.csv')
df.head()
```

```python
# Visualize the distribution of the target variable 'Competitive?'
import seaborn as sns
sns.countplot(data=df, x='Competitive?')
```

## Data Preprocessing

```python
# One-hot encode categorical variables and handle the target variable
df = pd.get_dummies(data=df, columns=df.columns[0:-1], drop_first=True).assign(**{f"Competitive?": df['Competitive?'].to_list()})
df.head()
```

## Holdout Method Without Shuffling

```python
X = df.drop('Competitive?', axis=1)
y = df['Competitive?']
Xtrain, Xtest, ytrain, ytest = train_test_split(X, y, test_size=0.368, shuffle=False)
clf = LogisticRegression(random_state=42)
clf.fit(Xtrain, ytrain)
accuracy_score(ytest, clf.predict(Xtest))
```

## Holdout Method With Shuffling

```python
X = df.drop('Competitive?', axis=1)
y = df['Competitive?']
Xtrain, Xtest, ytrain, ytest = train_test_split(X, y, test_size=0.368, shuffle=True, random_state=42)
clf = LogisticRegression(random_state=42)
clf.fit(Xtrain, ytrain)
accuracy_score(ytest, clf.predict(Xtest))
```

## Holdout Method With Shuffling and Random Subsampling

```python
num_samples = 10
X = df.drop('Competitive?', axis=1)
y = df['Competitive?']
accuracies = []

for _ in range(num_samples):
    Xtrain, Xtest, ytrain, ytest = train_test_split(X, y, test_size=0.368, shuffle=True)
    clf = LogisticRegression(random_state=42)
    clf.fit(Xtrain, ytrain)
    accuracies.append(accuracy_score(ytest, clf.predict(Xtest)))

display(accuracies)
np.mean(accuracies)
```

## Leave-One-Out

```python
loo = LeaveOneOut()
X = df.drop('Competitive?', axis=1)
y = df['Competitive?']
accuracies = []

for train_index, test_index in loo.split(X):
    Xtrain, Xtest = X.iloc[train_index], X.iloc[test_index]
    ytrain, ytest = y.iloc[train_index], y.iloc[test_index]

    clf = LogisticRegression(random_state=42)
    clf.fit(Xtrain, ytrain)
    accuracies.append(accuracy_score(ytest, clf.predict(Xtest)))

np.mean(accuracies)
```

## Bootstrap

```python
# Set the random seed for reproducibility
np.random.seed(42)
data = df

# Number of bootstrap samples
num_samples = 10

# Initialize empty lists to store bootstrap samples and testing sets
bootstrap_training_sets = []
bootstrap_testing_sets = []

for _ in range(num_samples):
    # Perform bootstrap resampling
    bootstrap_sample_indices = np.random.choice(len(data), size=len(data), replace=True)
    bootstrap_sample = data.iloc[bootstrap_sample_indices, :]
    bootstrap_training_sets.append(bootstrap_sample)

    # Identify the indices of the testing set (unsampled data points)
    testing_set_indices = np.setdiff1d(np.arange(len(data)), bootstrap_sample_indices)
    testing_set = data.iloc[testing_set_indices, :]
    bootstrap_testing_sets.append(testing_set)

# Bootstrap fraction not chosen
(len(bootstrap_sample_indices) - len(np.unique(bootstrap_sample_indices))) / len(bootstrap_sample_indices)

# Bootstrap fraction chosen
len(np.unique(bootstrap_sample_indices)) / len(bootstrap_sample_indices)

# Bootstrap
accuracies = []
for training_set, testing_set in zip(bootstrap_training_sets, bootstrap_testing_sets):
    Xtrain = training_set.drop('Competitive?', axis=1)
    ytrain = training_set['Competitive?']
    Xtest = testing_set.drop('Competitive?', axis=1)
    ytest = testing_set['Competitive?']
    clf = LogisticRegression(random_state=42)
    clf.fit(Xtrain, ytrain)
    acctest = accuracy_score(ytest, clf.predict(Xtest))
    acctrain = accuracy_score(ytrain, clf.predict(Xtrain))
    ftest = len(ytest) / (len(ytest) + len(ytrain))
    ftrain = len(ytrain) / (len(ytest) + len(ytrain))
    accuracies.append(acctest * ftest + acctrain * ftrain)

display(accuracies)
np.mean(accuracies)
```

## Cross-Validation without Shuffling

```python
clf = LogisticRegression(random_state=42)
cv_results = cross_validate(clf, X, y, cv=10)
cv_results['test_score']
```

## Cross-Validation with Shuffling

```python
shuffled_df = df.sample(frac=1, random_state=42)
X_shuffled = shuffled_df.drop('Competitive?', axis=1)
y_shuffled = shuffled_df['Competitive?']
clf = LogisticRegression(random_state=42)
cv_results = cross_validate(clf, X_shuffled, y_shuffled, cv=10)
cv_results['test_score']
```

## Stratified Cross-Validation Without Shuffling

```python
skf = StratifiedKFold(n_splits=10, shuffle=False)
clf = LogisticRegression(random_state=42)
cv_results = cross_validate(clf, X, y, cv=skf)
cv_results['test_score']
```

## Stratified Cross-Validation With Shuffling

```python
skf = StratifiedKFold(n_splits=10, shuffle=True, random_state=42)
clf = LogisticRegression(random_state=42)
cv_results = cross_validate(clf, X, y, cv=skf)
cv_results['test_score']
```

## Stratified Cross-Validation Without Shuffling

```python
accuracies = []
skf = StratifiedKFold(n_splits=10, shuffle=False)
skf.get_n_splits(X, y)
for i, (train_index, test_index) in enumerate(skf.split(X, y)):
    Xtrain = X.iloc[train_index]
    Xtest = X.iloc[test_index]
    ytrain = y.iloc[train_index]
    ytest = y.iloc[test_index]
    clf = LogisticRegression(random_state=42)
    clf.fit(Xtrain, ytrain)
    accuracies.append(accuracy_score(ytest, clf.predict(Xtest)))

display(accuracies)
np.mean(accuracies)
```

## Stratified Cross-Validation With Shuffling

```python
accuracies = []
skf = StratifiedKFold(n_splits=10, shuffle=True, random_state=42)
skf.get_n_splits(X, y)
for i, (train_index, test_index) in enumerate(skf.split(X, y)):
    Xtrain = X.iloc[train_index]
    Xtest = X.iloc[test_index]
    ytrain = y.iloc[train_index]
    ytest = y.iloc[test_index]
    clf = LogisticRegression(random_state=42)
    clf.fit(Xtrain, ytrain)
    accuracies.append(accuracy_score(ytest, clf.predict(Xtest)))

display(accuracies)
np.mean(accuracies)
```


## Confusion Matrix with ConfusionMatrixDisplay

```python
X = df.drop('Competitive?', axis=1)
y = df['Competitive?']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=.368, random_state=42, shuffle=True)
clf = LogisticRegression(random_state=42)
clf.fit(X_train, y_train)
cm = ConfusionMatrixDisplay.from_estimator(clf, X_test, y_test)
```

## Confusion Matrix with confusion_matrix

```python
y_pred = clf.predict(X_test)
cm = confusion_matrix(y_test, y_pred)
cm
```

## Confusion Matrix with Seaborn heatmap

```python
plt.figure(figsize=(8, 6))
sns.heatmap(cm, annot=True, fmt="d", cmap="Blues", cbar=False)
plt.xlabel('Predicted')
plt.ylabel('True')
plt.title('Confusion Matrix')
plt.show()
```

## Metrics using classification_report (scikit-learn)

```python
y_pred = clf.predict(X_test)
print(classification_report(y_test, y_pred))
```

## Evaluation Metrics

```python
# True Positives, True Negatives, False Positives, False Negatives
tp = cm[1, 1]
tn = cm[0, 0]
fp = cm[0, 1]
fn = cm[1, 0]

# Sensitivity (Recall)
sensitivity = tp / (tp + fn)

# Specificity
specificity = tn / (tn + fp)

# Precision
precision = tp / (tp + fp)

# Recall
recall = recall_score(y_test, y_pred)

# Accuracy
accuracy = (tp + tn) / (tp + tn + fp + fn)

# F1 Score (F-measure)
f1 = f1_score(y_test, y_pred)
f1 = 2 * precision * recall / (precision + recall)

# F2 Score (you can adjust beta for different emphasis on precision or recall)
beta = 2
f2 = (1 + beta**2) * (precision * sensitivity) / ((beta**2 * precision) + sensitivity)

# Matthews Correlation Coefficient (MCC)
mcc = matthews_corrcoef(y_test, y_pred)
mcc = (tp * tn - fp * fn) / np.sqrt((tp + fp) * (tp + fn) * (tn + fp) * (tn + fn))

# Print the results
print(f"True Positives (TP): {tp}")
print(f"True Negatives (TN): {tn}")
print(f"False Positives (FP): {fp}")
print(f"False Negatives (FN): {fn}")
print(f"Sensitivity: {sensitivity}")
print(f"Specificity: {specificity}")
print(f"Precision: {precision}")
print(f"Recall: {recall}")
print(f"Accuracy: {accuracy}")
print(f"F1 Score: {f1}")
print(f"F2 Score: {f2}")
print(f"Matthews Correlation Coefficient (MCC): {mcc}")
```

## ROC Curve

```python
X = df.drop('Competitive?', axis=1)
y = df['Competitive?']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=.368, random_state=42, shuffle=True)
clf = LogisticRegression(random_state=42)
clf.fit(X_train, y_train)

y_true = y_test
probas = clf.predict_proba(X_test)[:, 1]

# Sort the probabilities and true labels by probabilities
sorted_indices = np.argsort(probas)
sorted_probs = probas[sorted_indices]
sorted_labels = np.array(y_true)[sorted_indices]

# Initialize variables for ROC curve
fpr = [0]
tpr = [0]
thresholds = [sorted_probs[0]]

# Calculate TPR and FPR for each threshold
for i in range(1, len(sorted_probs)):
    threshold = sorted_probs[i]
    tp = np.sum((sorted_probs >= threshold) & (sorted_labels == 1))
    fp = np.sum((sorted_probs >= threshold) & (sorted_labels == 0))
    tn = np.sum((sorted_probs < threshold) & (sorted_labels == 0))
    fn = np.sum((sorted_probs < threshold) & (sorted_labels == 1))

    tpr.append(tp / (tp + fn))
    fpr.append(fp / (fp + tn))
    thresholds.append(threshold)

# Convert lists to numpy arrays
fpr = np.array(fpr)
tpr = np.array(tpr)
thresholds = np.array(thresholds)

# Plot ROC curve
plt.figure(figsize=(8, 6))
plt.plot(fpr, tpr, color='darkorange', lw=2, label='ROC curve')
plt.plot([0, 1], [0, 1], color='navy', lw=2, linestyle='--', label='Random')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('Receiver Operating Characteristic (ROC) Curve')
plt.legend(loc='lower right')
plt.show()
```

## ROC Curve with roc_curve (scikit-learn) and Matplotlib

```python
fpr, tpr, thresholds = roc_curve(y_test, probas)
roc_auc = auc(fpr, tpr)

# Plot ROC curve
plt.figure(figsize=(8, 6))
plt.plot(fpr, tpr, color='darkorange', lw=2, label=f'ROC curve (AUC = {roc_auc:.2f})')
plt.plot([0, 1], [0, 1], color='navy', lw=2, linestyle='--', label='Random')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('Receiver Operating Characteristic (ROC) Curve')
plt.legend(loc='lower right')
plt.show()
```

## ROC Curve with RocCurveDisplay (scikit-learn)

```python
RocCurveDisplay.from_estimator(clf, X_test, y_test, color="darkorange")
plt.axis("square")
plt.xlabel("False Positive Rate")
plt.ylabel("True Positive Rate")
plt.title("Receiver Operating Characteristic (ROC) Curve")
plt.legend()
plt.show()
```


## Cumulative Gains Curve using scikit-plot
```python
!pip install scikit-plot &>/dev/null
import scikitplot as skplt
plt.figure(figsize=(7,7))
skplt.metrics.plot_cumulative_gain(y_test, clf.predict_proba(X_test))
plt.show()
```

## Cumulative Gains Curve

```python
# Assuming 'y_prob' contains the predicted probabilities for the positive class
y_prob = clf.predict_proba(X_test)[:, 1]

# Sort the predictions by probability
sorted_indices = np.argsort(y_prob, kind='mergesort')[::-1]
ytest_sorted = y_test.iloc[sorted_indices]

# Calculate cumulative gain values
percentile = np.linspace(0, 100, len(ytest_sorted))
gain = np.cumsum(ytest_sorted) / np.sum(ytest_sorted)

# Plot the cumulative gain curve
plt.figure(figsize=(7, 7))
plt.plot(percentile, gain, marker='o', linestyle='-', color='orange')

# Add labels and title
plt.xlabel('Percentage of Sample')
plt.ylabel('Gain')
plt.title('Cumulative Gains Curve')

# Show the plot
plt.grid(True)
plt.show()
```

## Lift Curve using scikit-plot
```python
plt.figure(figsize=(7,7))
skplt.metrics.plot_lift_curve(y_test, clf.predict_proba(X_test));
plt.show()
```

## Lift Curve

```python
y_prob = clf.predict_proba(X_test)[:, 1]

# Sort the predictions by probability
sorted_indices = np.argsort(y_prob, kind='mergesort')[::-1]
ytest_sorted = y_test.iloc[sorted_indices]

# Calculate cumulative gain values
percentile = np.linspace(0, 100, len(ytest_sorted))
cumulative_gain = np.cumsum(ytest_sorted) / np.sum(ytest_sorted)

# Calculate the baseline cumulative gain (if predictions were random)
baseline = np.linspace(0, 100, len(ytest_sorted))

# Calculate the lift values
lift_values = cumulative_gain / baseline

# Plot the lift chart
plt.figure(figsize=(7, 7))
plt.plot(percentile, lift_values, marker='o', linestyle='-', color='orange')

# Add labels and title
plt.xlabel('Percentage of Sample')
plt.ylabel('Lift')
plt.title('Lift Chart')

# Show the plot
plt.grid(True)
plt.show()
```

## Decile-wise Lift Chart
```python
df1=pd.DataFrame(clf.predict_proba(X_test),columns=['P0','P1'])
df1['ytest']=y_test.values
df1['ytest']=y_test.values
df1=df1.sort_values(by='P1',ascending=False)
df1['Decile'] = pd.qcut(df1['P1'], 10, labels=False)
df1['Decile']=df1['Decile']+1
df1['Decile']=list(df1['Decile'].loc[::-1])
df1['Cumulative Gain']=df1['ytest'].cumsum()
df1.head()

df2=df1.groupby(by=['Decile']).mean()
df2

df2['uplift']=df2['ytest']/df1.ytest.mean()
df2

#df2.reset_index().plot(kind='bar',x='Decile',y='uplift',ylabel='Lift',xlabel='Percential')

ax = df2.reset_index().plot(kind='bar', x='Decile', y='uplift', ylabel='Lift', xlabel='Percentile')

# Annotate the bars with actual values
for index, value in enumerate(df2['uplift']):
    ax.text(index, value, round(value, 1), ha='center', va='bottom')
```

## Cumulative Gains and Lift using DMBA Toolbox
```python
!pip install dmba &>/dev/null
from dmba import classificationSummary, regressionSummary, gainsChart, liftChart, AIC_score
y_prob = clf.predict_proba(X_test)[:, 1]
# Sort the predictions by probability
sorted_indices = np.argsort(y_prob, kind='mergesort')[::-1]
ytest_sorted = y_test.iloc[sorted_indices]

fig, axes = plt.subplots(nrows=1, ncols=2, figsize=(10, 4))
gainsChart(ytest_sorted, ax=axes[0])
liftChart(ytest_sorted, title=False, ax=axes[1])
plt.tight_layout()
plt.show()
```





