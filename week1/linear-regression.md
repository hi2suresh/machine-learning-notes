# Linear Regression — Simple Guide for Everyone

This short README explains Linear Regression and related concepts in plain language, with simple diagrams and minimal math. It's designed for non-technical readers.

---

**What is Linear Regression?**

Linear Regression is a simple way to predict a number (the label) from one or more inputs (features). Think of it like drawing a straight line that best fits a set of points on a chart — then using that line to estimate unknown values.

Simple equation for a single input feature:

$\text{prediction} = w \cdot x + b$

- $x$ = feature (input)
- $w$ = weight (how strongly the input affects the prediction)
- $b$ = bias (also called intercept; the prediction when $x=0$)
- $\text{prediction}$ = the model's guessed output (label)

ASCII diagram (points and fitted line):

```
Value
  │             •
  │         •   •   •
  │       •      •
  │   •          •
  │ •
  └──────────────────
        Feature →

Fitted line: y = w x + b (a straight line through the points)
```

---

**Key Concepts (plain language)**n
- Feature: An input or attribute you use to make a prediction. Example: "hours studied".
- Label: The number you want to predict. Example: "test score".
- Prediction: The model's estimate for the label given a feature value.
- Weight (`w`): How much the feature changes the prediction. Larger magnitude → bigger effect.
- Bias (`b`): A baseline prediction when all features are zero (like the line's starting point).

Example: If `prediction = 2 * hours + 50`, then each hour adds 2 points and the baseline score is 50.

---

**Loss — What we try to minimize**

Loss measures how wrong the model's predictions are compared to actual labels. Training a model means adjusting `w` and `b` to make the loss as small as possible.

Intuition: If predictions are close to actual values, loss is small. If predictions are far away, loss is large.

Popular loss functions for Linear Regression:

1) Mean Squared Error (MSE)

- Formula: $\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (\text{prediction}_i - y_i)^2$
- Explanation: Take the difference between predicted and actual, square it (so positives/negatives don't cancel and big errors are punished more), then average.
- When to use: Very common; works well for many problems and is differentiable (good for optimization).

2) Mean Absolute Error (MAE)

- Formula: $\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} |\text{prediction}_i - y_i|$
- Explanation: Average absolute differences; treats all errors proportionally, less sensitive to outliers than MSE.
- When to use: If you want a robust measure that’s less affected by large outliers.

3) Huber Loss (a mix of MSE and MAE)

- Explanation: Uses squared error for small mistakes and absolute error for large mistakes. It blends benefits of both MSE and MAE.
- When to use: When you want sensitivity to small errors but robustness to large outliers.

Short comparison:
- MSE: smooth, penalizes large errors strongly.
- MAE: robust, penalizes errors linearly.
- Huber: compromise between MSE and MAE.

---

**Small numeric example (MSE)**

Data (feature → label): [ (1→3), (2→5), (3→7) ]
Suppose model: prediction = 2*x + 0
Predictions: [2, 4, 6]
Errors: [1, 1, 1]
Squared errors: [1, 1, 1]
MSE = (1 + 1 + 1) / 3 = 1

Lower MSE means better fit.

---

**Why this matters (practical intuition)**

- If `w` is too big, predictions change too much for small feature changes (overreaction).
- If `w` is too small, predictions hardly change and model is not useful.
- The learning process adjusts `w` and `b` to reduce loss so predictions match reality.

---

**Diagrams (simple visual reminders)**

- Straight line model: a single slope and intercept.

```
  Prediction
    │      / (line)
    │     /
    │    /  • (points)
    │   /
    └───────── Feature
```

- Error illustration (vertical distance from point to line):

```
   •
   │  ← error (actual - predicted)
  ─┴────────────
   fitted line
```

---

**Quick glossary**
- Feature: input
- Label: true output
- Prediction: model output
- Weight: slope (importance of feature)
- Bias: intercept (baseline)
- Loss: a number measuring prediction error

---

If you want, I can:
- Add simple plots (PNG) showing examples, or
- Create a notebook demonstrating linear regression on real data.

*File created: `week1/read.me`. Last updated: February 6, 2026.*