# Machine Learning Dataset Division

This README provides an overview of best practices for dividing datasets in machine learning, based on the Google Machine Learning Crash Course on overfitting and dataset division.

## Overview

Just as software engineering projects require thorough testing, machine learning models need robust evaluation to ensure accurate predictions. A key aspect of this is properly dividing your dataset into subsets for training, validation, and testing.

## Dataset Division: Training, Validation, and Test Sets

### Why Divide the Dataset?

Testing a model on the same data used for training doesn't provide a reliable measure of its performance on new, unseen data. To properly evaluate a model's fitness, you must test it against different examples.

### Traditional Two-Way Split (Not Recommended)

Initially, you might think to split the dataset into just two parts:

- **Training Set**: Used to train the model (~80% of data)
- **Test Set**: Used for final evaluation (~20% of data)

However, this approach has limitations when it comes to tuning hyperparameters and feature selection.

### Recommended Three-Way Split

A better approach divides the dataset into three subsets:

- **Training Set** (~70%): Used to train the model
- **Validation Set** (~15%): Used for initial testing and hyperparameter tuning during training
- **Test Set** (~15%): Used for final evaluation after model development

While 70/15/15 is a standard starting point and could be a guideline, it's not a hard rule. The actual number of rows matters more than the percentage.

When deciding on your split, keep these two principles in mind:

1. **Statistical significance**: Is the validation/test set large enough?
2. **Representativeness**: Does your validation/test set "look like" the real world?

> **Note**: If you have millions of rows, even a 1% split is plenty (98/1/1). If your dataset is tiny, you'll likely need to use 'Cross-Validation' techniques instead to avoid wasting valuable training data.

![Dataset Division](https://developers.google.com/static/machine-learning/crash-course/images/PartitionThreeSets.png)

_Figure: Recommended dataset split - 70% training, 15% validation, 15% test_

## Workflow for Model Development

1. **Train** the model on the training set
2. **Evaluate** the model on the validation set
3. **Tweak** the model based on validation results (adjust hyperparameters, features, etc.)
4. **Repeat** steps 1-3 until satisfied with validation performance
5. **Final Evaluation**: Test the chosen model on the test set

![Workflow](https://developers.google.com/static/machine-learning/crash-course/images/workflow_with_validation_set.svg)

_Figure: Optimal workflow using training, validation, and test sets_

**Important Note**: Any transformations applied to the training set must also be applied to the validation and test sets, as well as real-world data.

## Additional Considerations

### Test Set "Wear Out"

With repeated use, validation and test sets can become less effective for unbiased evaluation. Consider collecting more data to refresh these sets periodically.

### Avoiding Data Leakage

- **Duplicates**: Remove any duplicate examples between training and test/validation sets
- **Data Scrubbing**: Ensure no test examples were inadvertently used in training
- **Representativeness**: Test and validation sets should represent the overall dataset and real-world data

### Test Set Requirements

A good test set should be:

- **Large enough** for statistically significant results
- **Representative** of the entire dataset
- **Representative** of real-world data the model will encounter
- **Free of duplicates** from the training set

## Common Pitfalls

- Using the test set for hyperparameter tuning
- Having duplicate examples across splits
- Test sets that don't reflect real-world data distribution
- Insufficient test set size for reliable evaluation

## Key Terms

- **Training Set**: Data used to train the model
- **Validation Set**: Data used for tuning and intermediate evaluation
- **Test Set**: Data used for final, unbiased model evaluation

## Resources

- [Google ML Crash Course: Dividing Datasets](https://developers.google.com/machine-learning/crash-course/overfitting/dividing-datasets)
- [Machine Learning Glossary](https://developers.google.com/machine-learning/glossary)

---

_Based on Google Machine Learning Crash Course content. Last updated: February 2, 2026_
