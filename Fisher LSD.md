# Fisher's Least Significant Difference (LSD) Test - Step by Step

## Context: Weightlifting Performance Analysis

After conducting a one-way ANOVA and finding a significant difference (p < 0.05) between training programs, we need to identify which specific pairs of programs differ significantly.

## Example Dataset

**Research Question:** Do 5 different training programs lead to different strength gains (measured in kg lifted on bench press)?

### Sample Data

| Program A | Program B | Program C | Program D | Program E |
|-----------|-----------|-----------|-----------|-----------|
| 85 kg     | 92 kg     | 78 kg     | 95 kg     | 88 kg     |
| 88 kg     | 95 kg     | 80 kg     | 98 kg     | 90 kg     |
| 82 kg     | 89 kg     | 75 kg     | 92 kg     | 85 kg     |
| 87 kg     | 94 kg     | 77 kg     | 96 kg     | 89 kg     |
| 86 kg     | 90 kg     | 79 kg     | 94 kg     | 87 kg     |

**n = 5** participants per program (total N = 25)

---

## Step 1: Calculate Group Means

For each training program, calculate the mean:

```
Mean_A = (85 + 88 + 82 + 87 + 86) / 5 = 428 / 5 = 85.6 kg
Mean_B = (92 + 95 + 89 + 94 + 90) / 5 = 460 / 5 = 92.0 kg
Mean_C = (78 + 80 + 75 + 77 + 79) / 5 = 389 / 5 = 77.8 kg
Mean_D = (95 + 98 + 92 + 96 + 94) / 5 = 475 / 5 = 95.0 kg
Mean_E = (88 + 90 + 85 + 89 + 87) / 5 = 439 / 5 = 87.8 kg
```

**Summary:**
- Program A: 85.6 kg
- Program B: 92.0 kg
- Program C: 77.8 kg
- Program D: 95.0 kg
- Program E: 87.8 kg

---

## Step 2: Calculate Mean Squared Error (MSE) from ANOVA

### Calculate Sum of Squares Within (SSW)

For each group, calculate the sum of squared deviations from the group mean:

**Program A:**
```
(85-85.6)² + (88-85.6)² + (82-85.6)² + (87-85.6)² + (86-85.6)² = 22.8
```

**Program B:**
```
(92-92)² + (95-92)² + (89-92)² + (94-92)² + (90-92)² = 26.0
```

**Program C:**
```
(78-77.8)² + (80-77.8)² + (75-77.8)² + (77-77.8)² + (79-77.8)² = 14.8
```

**Program D:**
```
(95-95)² + (98-95)² + (92-95)² + (96-95)² + (94-95)² = 20.0
```

**Program E:**
```
(88-87.8)² + (90-87.8)² + (85-87.8)² + (89-87.8)² + (87-87.8)² = 17.2
```

**Total SSW = 22.8 + 26.0 + 14.8 + 20.0 + 17.2 = 100.8**

### Calculate MSE

```
MSE = SSW / df_within
df_within = N - k = 25 - 5 = 20
MSE = 100.8 / 20 = 5.04
```

---

## Step 3: Find Critical t-value

For Fisher's LSD, we need the t-value from the t-distribution:

- **df = 20** (degrees of freedom within groups)
- **α = 0.05** (two-tailed test, so α/2 = 0.025 for each tail)
- **Critical t-value (from t-table) = 2.086**

---

## Step 4: Calculate LSD (Least Significant Difference)

The LSD formula when sample sizes are equal:

```
LSD = t_critical × √(2 × MSE / n)
```

Where:
- t_critical = 2.086
- MSE = 5.04
- n = 5 (sample size per group)

**Calculation:**
```
LSD = 2.086 × √(2 × 5.04 / 5)
LSD = 2.086 × √(10.08 / 5)
LSD = 2.086 × √2.016
LSD = 2.086 × 1.420
LSD = 2.96 kg
```

**Interpretation:** Any two means that differ by more than 2.96 kg are significantly different at α = 0.05.

---

## Step 5: Compare All Pairs

Calculate the absolute difference between each pair of means:

| Comparison | Mean Difference | Comparison to LSD | Significant? |
|------------|-----------------|-------------------|--------------|
| A vs B | 6.4 kg | > 2.96 | **Yes** ✓ |
| A vs C | 7.8 kg | > 2.96 | **Yes** ✓ |
| A vs D | 9.4 kg | > 2.96 | **Yes** ✓ |
| A vs E | 2.2 kg | < 2.96 | No |
| B vs C | 14.2 kg | > 2.96 | **Yes** ✓ |
| B vs D | 3.0 kg | > 2.96 | **Yes** ✓ |
| B vs E | 4.2 kg | > 2.96 | **Yes** ✓ |
| C vs D | 17.2 kg | > 2.96 | **Yes** ✓ |
| C vs E | 10.0 kg | > 2.96 | **Yes** ✓ |
| D vs E | 7.2 kg | > 2.96 | **Yes** ✓ |

---

## Step 6: Results Summary

**Significant Differences Found:**
- Program D (95.0 kg) > Program B (92.0 kg) > Program E (87.8 kg) > Program A (85.6 kg) > Program C (77.8 kg)
- Program A and E are NOT significantly different from each other
- All other pairs show significant differences

**Ranking (from highest to lowest mean):**
1. Program D: 95.0 kg
2. Program B: 92.0 kg
3. Program E: 87.8 kg
4. Program A: 85.6 kg
5. Program C: 77.8 kg

---

## Formula Summary

### General LSD Formula (equal sample sizes):
```
LSD = t_(α/2, df_within) × √(2 × MSE / n)
```

### General LSD Formula (unequal sample sizes):
```
LSD = t_(α/2, df_within) × √(MSE × (1/n_i + 1/n_j))
```

Where:
- **t_(α/2, df_within)**: Critical t-value from t-distribution
- **MSE**: Mean Square Error from ANOVA
- **n**: Sample size per group (n_i and n_j for unequal sizes)
- **df_within**: N - k (total observations - number of groups)

---

## Important Notes

1. **Fisher's LSD should only be used when the overall ANOVA F-test is significant** (p < 0.05). This is called the "protected" LSD test.

2. **Fisher's LSD does NOT control for familywise error rate** when making multiple comparisons. For more conservative tests, consider Tukey's HSD or Bonferroni correction.

3. **Assumptions:**
   - Independence of observations
   - Normality within each group
   - Homogeneity of variance (equal variances across groups)

4. **When to use Fisher's LSD:**
   - When you have a priori hypotheses about specific comparisons
   - When the number of comparisons is small
   - When the overall ANOVA is significant
   - When you want higher statistical power (but accept higher Type I error risk)

---

## Practice Problem

Try calculating Fisher's LSD for this dataset:

**Deadlift strength (kg) after 3 different programs:**

| Program X | Program Y | Program Z |
|-----------|-----------|-----------|
| 140       | 155       | 148       |
| 145       | 160       | 150       |
| 138       | 152       | 145       |
| 142       | 158       | 149       |

**Given:** MSE = 28.5, df_within = 9

**Challenge:** Calculate the LSD and determine which programs differ significantly!

---

**Last Updated:** December 2025
**Buy me cat food**
evilmathcat@yandex.com
