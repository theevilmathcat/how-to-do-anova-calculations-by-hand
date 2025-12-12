# One-Way ANOVA: Manual Calculations

## Design Characteristics

**Design Type:** Between-subjects (independent groups)
- Each salesperson represents a different independent group
- Different individuals in each group

**Balance:** Unbalanced design
- Salesperson A: n = 6 observations
- Salesperson B: n = 5 observations  
- Salesperson C: n = 4 observations
- Groups have different sample sizes

**Crossed Design:** Not applicable
- This is a single-factor design with only one independent variable (Salesperson)
- "Crossed" applies to designs with two or more factors

## Data Summary

| Column A | Column B | Column C |
|----------|----------|----------|
| 45.20    | 53.20    | 52.50    |
| 60.10    | 56.60    | 73.60    |
| 52.80    | 68.70    | 63.30    |
| 31.70    | 51.80    | 51.80    |
| 33.60    | 54.20    |          |
| 39.40    |          |          |

## Step 1: Calculate Group Statistics

### Salesperson A (Column A)
- n₁ = 6
- Sum₁ = 45.20 + 60.10 + 52.80 + 31.70 + 33.60 + 39.40 = 262.80
- Mean₁ (M₁) = 262.80 / 6 = 43.80

### Salesperson B (Column B)
- n₂ = 5
- Sum₂ = 53.20 + 56.60 + 68.70 + 51.80 + 54.20 = 284.50
- Mean₂ (M₂) = 284.50 / 5 = 56.90

### Salesperson C (Column C)
- n₃ = 4
- Sum₃ = 52.50 + 73.60 + 63.30 + 51.80 = 241.20
- Mean₃ (M₃) = 241.20 / 4 = 60.30

### Overall Statistics
- N (total observations) = 6 + 5 + 4 = 15
- Grand Sum = 262.80 + 284.50 + 241.20 = 788.50
- Grand Mean (GM) = 788.50 / 15 = 52.57

## Step 2: Calculate Sum of Squares Between Groups (SSB)

SSB measures variability between group means.

Formula: SSB = Σ nᵢ(Mᵢ - GM)²

SSB = n₁(M₁ - GM)² + n₂(M₂ - GM)² + n₃(M₃ - GM)²

SSB = 6(43.80 - 52.57)² + 5(56.90 - 52.57)² + 4(60.30 - 52.57)²

SSB = 6(-8.77)² + 5(4.33)² + 4(7.73)²

SSB = 6(76.91) + 5(18.75) + 4(59.75)

SSB = 461.46 + 93.75 + 239.00

**SSB = 794.21**

## Step 3: Calculate Sum of Squares Within Groups (SSW)

SSW measures variability within each group.

Formula: SSW = Σ(Xᵢⱼ - Mᵢ)²

### For Salesperson A:
- (45.20 - 43.80)² = 1.96
- (60.10 - 43.80)² = 265.69
- (52.80 - 43.80)² = 81.00
- (31.70 - 43.80)² = 146.41
- (33.60 - 43.80)² = 104.04
- (39.40 - 43.80)² = 19.36

SSW₁ = 618.46

### For Salesperson B:
- (53.20 - 56.90)² = 13.69
- (56.60 - 56.90)² = 0.09
- (68.70 - 56.90)² = 139.24
- (51.80 - 56.90)² = 26.01
- (54.20 - 56.90)² = 7.29

SSW₂ = 186.32

### For Salesperson C:
- (52.50 - 60.30)² = 60.84
- (73.60 - 60.30)² = 177.69
- (63.30 - 60.30)² = 9.00
- (51.80 - 60.30)² = 72.25

SSW₃ = 319.78

**SSW = 618.46 + 186.32 + 319.78 = 1124.56**

## Step 4: Calculate Total Sum of Squares (SST)

Check: SST = SSB + SSW

SST = 794.21 + 1124.56 = 1918.77

## Step 5: Calculate Degrees of Freedom

- **df_between** = k - 1 = 3 - 1 = **2**
  - (k = number of groups)

- **df_within** = N - k = 15 - 3 = **12**
  - (N = total observations)

- **df_total** = N - 1 = 15 - 1 = **14**

## Step 6: Calculate Mean Squares

**Mean Square Between (MSB):**
MSB = SSB / df_between = 794.21 / 2 = **397.11**

**Mean Square Within (MSW):**
MSW = SSW / df_within = 1124.56 / 12 = **93.71**

## Step 7: Calculate F-statistic

F = MSB / MSW = 397.11 / 93.71 = **4.24**

## Step 8: Determine Critical Value and Conclusion

For α = 0.05, df₁ = 2, df₂ = 12:
- Critical F-value ≈ 3.89

**Decision:**
Since F_calculated (4.24) > F_critical (3.89), we **reject the null hypothesis**.

**Conclusion:** There is a statistically significant difference in the average time spent on the phone among the three salespeople at the α = 0.05 level.

## ANOVA Summary Table

| Source    | SS      | df  | MS     | F    | p-value |
|-----------|---------|-----|--------|------|---------|
| Between   | 794.21  | 2   | 397.11 | 4.24 | < 0.05  |
| Within    | 1124.56 | 12  | 93.71  |      |         |
| **Total** | 1918.77 | 14  |        |      |         |

## Interpretation

The significant F-statistic indicates that not all salespeople spend the same average time on the phone. To determine specifically which salespeople differ from each other, you would need to conduct post-hoc tests (such as Tukey's HSD test).

From the means:
- Salesperson A: 43.80 minutes (lowest)
- Salesperson B: 56.90 minutes (middle)
- Salesperson C: 60.30 minutes (highest)
