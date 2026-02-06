# Statistics Basics: Mean, Median, Mode, and Beyond

This guide covers fundamental statistical concepts essential for understanding data in machine learning.

## Table of Contents

1. [Central Tendency Measures](#central-tendency-measures)
2. [Spread/Dispersion Measures](#spreaddispersion-measures)
3. [Distributions](#distributions)
4. [Histograms](#histograms)

---

## Central Tendency Measures

Central tendency measures describe the center or "typical" value of a dataset.

### Mean (Average)

The **mean** is the sum of all values divided by the number of values.

**Formula**: $\text{Mean} = \frac{\sum_{i=1}^{n} x_i}{n}$

**Example**:

- Data: [2, 4, 6, 8, 10]
- Mean = (2 + 4 + 6 + 8 + 10) / 5 = 30 / 5 = **6**

**When to use**: Use when data is normally distributed and there are no extreme outliers.

**Limitation**: Sensitive to outliers.

```
Data: [1, 2, 3, 4, 100]
Mean = 22  ← Skewed by the outlier 100
```

---

### Median

The **median** is the middle value when data is arranged in order.

**Example**:

- Data: [2, 4, 6, 8, 10]
- Median = **6** (middle value)

- Data (even count): [2, 4, 6, 8]
- Median = (4 + 6) / 2 = **5** (average of two middle values)

**When to use**: Use when data has outliers or is skewed. More robust than mean.

**Comparison**:

```
Dataset: [1, 2, 3, 4, 100]
Mean = 22
Median = 3  ← Better represents typical value
```

---

### Mode

The **mode** is the value that appears most frequently in a dataset.

**Example**:

- Data: [1, 2, 2, 3, 4, 4, 4, 5]
- Mode = **4** (appears 3 times)

**Types**:

- **Unimodal**: One mode (e.g., [1, 2, 2, 3] → mode = 2)
- **Bimodal**: Two modes (e.g., [1, 1, 2, 2, 3] → modes = 1 and 2)
- **Multimodal**: Multiple modes
- **No mode**: All values appear equally (e.g., [1, 2, 3, 4])

**When to use**: Use for categorical data or to identify the most common value.

---

### Visual Comparison

```
Normal Distribution:
Mean = Median = Mode
        │
        ▲
        │     ╱╲
        │    ╱  ╲
        │   ╱    ╲
        │  ╱      ╲
        │_╱________╲_
        ────────────────
   Mean/Median/Mode

Right-Skewed (positive skew):
Mode < Median < Mean
        │
        ▲     ╱╲
        │    ╱  ╲
        │   ╱    ╲
        │  ╱      ╲___
        │_╱___________╲_
        ────────────────
   Mode Median   Mean

Left-Skewed (negative skew):
Mean < Median < Mode
        │
        ▲        ╱╲
        │    ___╱  ╲
        │   ╱       ╲
        │  ╱         ╲
        │_╱___________╲_
        ────────────────
     Mean Median   Mode
```

---

## Spread/Dispersion Measures

Spread measures describe how far values are from the center.

### Variance

**Variance** measures how spread out data is from the mean. It's the average of squared differences from the mean.

**Formula**: $\text{Variance} = \sigma^2 = \frac{\sum_{i=1}^{n} (x_i - \text{mean})^2}{n}$

**Example**:

- Data: [2, 4, 6]
- Mean = 4
- Differences: [2-4, 4-4, 6-4] = [-2, 0, 2]
- Squared: [4, 0, 4]
- Variance = (4 + 0 + 4) / 3 = **2.67**

**Note**: We square differences to eliminate negatives and emphasize larger deviations.

---

### Standard Deviation

**Standard deviation** is the square root of variance. It's in the same units as the original data.

**Formula**: $\text{Standard Deviation} = \sigma = \sqrt{\text{Variance}}$

**Example**:

- Variance = 2.67
- Standard Deviation = √2.67 = **1.63**

**Interpretation (68-95-99.7 Rule)**:

```
Normal Distribution:
- 68% of data falls within 1 standard deviation of mean
- 95% within 2 standard deviations
- 99.7% within 3 standard deviations

        │
        ▲
        │       ╱╲
        │      ╱  ╲
    68% │     ╱▓▓▓▓▓╲
        │    ╱▓▓▓▓▓▓▓╲
        │   ╱▓▓▓▓▓▓▓▓▓╲
        │__╱▓▓▓▓▓▓▓▓▓▓▓╲___
        ─────────┬─────────
             Mean
         Mean±1σ (68%)
```

---

### Visual: Low vs High Variance

```
Low Variance:
All values clustered close to mean
        │
        ▲     ╱╲
        │    ╱  ╲
        │   ╱████╲
        │  ╱██████╲
        │_╱████████╲_
        ────────────────
         Mean

High Variance:
Values spread far from mean
        │
        ▲    ╱╲
        │   ╱  ╲
        │  ╱    ╲
        │ ╱██████╲
        │╱████████╲___
        ────────────────
         Mean
```

---

## Distributions

A **distribution** describes how values are spread across a range.

### Normal Distribution (Gaussian)

Symmetric, bell-shaped curve. Most values cluster around the mean.

**Characteristics**:

- Symmetric (mean = median = mode)
- Predictable: 68-95-99.7 rule
- Common in nature (heights, test scores, etc.)

```
        ▲
        │       ╱╲
        │      ╱  ╲
        │     ╱    ╲
        │    ╱      ╲
        │   ╱        ╲
        │  ╱          ╲
        │_╱____________╲_
        ──────────────────
         Mean
```

### Skewed Distributions

**Right-Skewed (Positive Skew)**:

- Tail points right
- Mean > Median
- Common in: income, age at death

```
        ▲
        │╱╲
        │  ╲
        │   ╲
        │    ╲___
        │________╲___
        ──────────────
       Median Mean
```

**Left-Skewed (Negative Skew)**:

- Tail points left
- Mean < Median
- Common in: test scores (ceiling effect)

```
        ▲
        │      ╱╲
        │   ___╱  ╲
        │  ╱       ╲
        │ ╱         ╲
        │╱____________
        ──────────────
      Mean Median
```

### Uniform Distribution

All values equally likely. Flat distribution.

```
        ▲
        │ ─────────
        │ │       │
        │ │       │
        │_│       │__
        ─────────────
         All values equally likely
```

---

## Histograms

A **histogram** is a visualization showing the frequency of values in ranges (bins).

### How to Read a Histogram

```
Frequency
    │
    ▲      ┌──┐
    │      │  │
  8 │      │  │         ┌──┐
    │      │  │         │  │
  6 │      │  │┌──┐     │  │
    │      │  ││  │     │  │
  4 │      │  ││  │┌──┐ │  │
    │      │  ││  ││  │ │  │
  2 │┌──┐  │  ││  ││  │ │  │
    ││  │  │  ││  ││  │ │  │
  0 └┴──┴──┴──┴┴──┴┴──┴─┴──┴──
    10-20 20-30 30-40 40-50 60-70
    Salary Ranges (in thousands)

Key Points:
- X-axis: Value ranges (bins)
- Y-axis: Frequency (count)
- Height of bar: Number of values in that range
```

### Histogram vs Distribution

| Histograms                     | Distributions                 |
| ------------------------------ | ----------------------------- |
| Actual data binned into ranges | Theoretical probability model |
| Shows what you actually have   | Shows what should happen      |
| Bar chart representation       | Smooth curve                  |

### Shape Analysis from Histogram

```
Normal Distribution Histogram:
        │     ┌──┐
        │     │  │
        │   ┌─┴──┴─┐
        │  ┌┘      └┐
        │ ┌         └┐
        └─┴──────────┴──
         Bell-shaped

Right-Skewed Histogram:
        │  ┌──┐
        │  │  │
        │  │  │
        │  │  │  ┌──┐
        │  │  │  │  │
        └──┴──┴──┴──┴──────
         Tail to right

Bimodal Histogram:
        │  ┌──┐    ┌──┐
        │  │  │    │  │
        │  │  │┌──┐│  │
        │  │  ││  ││  │
        └──┴──┴┴──┴┴──┴──
         Two peaks
```

---

## Practical Example: Analyzing Student Test Scores

**Data**: [65, 70, 72, 75, 78, 78, 80, 85, 88, 90, 92, 95]

### Calculations

```
Mean:
(65+70+72+75+78+78+80+85+88+90+92+95) / 12 = 998 / 12 = 83.17

Median:
Ordered: [65, 70, 72, 75, 78, 78, 80, 85, 88, 90, 92, 95]
         Position 6.5 → (78 + 80) / 2 = 79

Mode:
78 appears twice, all others once → Mode = 78

Variance & Std Dev:
- Differences from mean (83.17): [-18.17, -13.17, -11.17, ...]
- Squared: [330.15, 173.45, 124.77, ...]
- Variance = 82.64
- Std Dev = √82.64 = 9.09

Interpretation:
- Mean is slightly higher than median (slight right skew)
- 68% of scores fall between 74 (83.17-9.09) and 92 (83.17+9.09)
- Scores are fairly well spread (std dev of ~9)
```

---

## Quick Reference

| Measure      | What It Is                  | When to Use                 | Formula                                      |
| ------------ | --------------------------- | --------------------------- | -------------------------------------------- |
| **Mean**     | Average                     | Symmetric data, no outliers | $\bar{x} = \frac{\sum x_i}{n}$               |
| **Median**   | Middle value                | Skewed data, with outliers  | Middle position when ordered                 |
| **Mode**     | Most frequent               | Categorical data            | Most common value                            |
| **Variance** | Avg squared deviation       | Technical calculations      | $\sigma^2 = \frac{\sum(x_i - \bar{x})^2}{n}$ |
| **Std Dev**  | Spread (same units as data) | Interpretation & analysis   | $\sigma = \sqrt{\sigma^2}$                   |

---

## Key Takeaways

1. **Central Tendency** (mean, median, mode) tells you the "typical" value
2. **Spread** (variance, std dev) tells you how scattered the data is
3. **Distribution** shape tells you how data is organized
4. **Histograms** let you visualize actual data distributions
5. Always check for outliers and skewness when analyzing data
6. Use appropriate measures: median for skewed data, mean for normal data

---
