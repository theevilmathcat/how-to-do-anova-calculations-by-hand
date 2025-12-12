# ANCOVA Analysis: Deadlift Performance by Bodyweight

## Dataset Overview
- **Response Variable (Y):** Deadlift_kg
- **Covariate (X):** Bodyweight_kg  
- **Grouping Variable:** Group (all "Experienced" in this dataset)
- **Sample Size:** n = 25

## Raw Data Summary

| Deadlift (Y) | Bodyweight (X) |
|--------------|----------------|
| 195, 225, 210, 240, 205, 230, 250, 215, 235, 200, 245, 220, 255 | 78, 85, 80, 92, 79, 88, 95, 82, 90, 77, 94, 84, 98 |
| 208, 238, 192, 260, 228, 242, 218, 233, 248, 212, 226, 237 | 81, 91, 76, 100, 87, 93, 83, 89, 96, 80, 86, 90 |

---

## Step 1: Calculate Summary Statistics

### Basic Summations
- ΣX = 2,174
- ΣY = 5,622
- ΣX² = 190,458
- ΣY² = 1,270,114
- ΣXY = 490,459
- n = 25

### Means
- X̄ = ΣX/n = 2,174/25 = **86.96**
- Ȳ = ΣY/n = 5,622/25 = **224.88**

---

## Step 2: Calculate Sums of Squares and Cross Products

### Total Sums of Squares
**SSₓ (Total):**
```
SSₓ = ΣX² - (ΣX)²/n
SSₓ = 190,458 - (2,174)²/25
SSₓ = 190,458 - 188,969.76
SSₓ = 1,488.24
```

**SSᵧ (Total):**
```
SSᵧ = ΣY² - (ΣY)²/n
SSᵧ = 1,270,114 - (5,622)²/25
SSᵧ = 1,270,114 - 1,263,651.36
SSᵧ = 6,462.64
```

**SPₓᵧ (Cross Product):**
```
SPₓᵧ = ΣXY - (ΣX)(ΣY)/n
SPₓᵧ = 490,459 - (2,174)(5,622)/25
SPₓᵧ = 490,459 - 488,734.08
SPₓᵧ = 1,724.92
```

---

## Step 3: Calculate Regression Slope and Intercept

### Slope (b₁)
```
b₁ = SPₓᵧ / SSₓ
b₁ = 1,724.92 / 1,488.24
b₁ = 1.159
```

### Intercept (b₀)
```
b₀ = Ȳ - b₁X̄
b₀ = 224.88 - 1.159(86.96)
b₀ = 224.88 - 100.79
b₀ = 124.09
```

### Regression Equation
**Ŷ = 124.09 + 1.159X**

---

## Step 4: ANCOVA Partitioning

### Regression Sum of Squares (SSᵣₑ𝓰)
```
SSᵣₑ𝓰 = (SPₓᵧ)² / SSₓ
SSᵣₑ𝓰 = (1,724.92)² / 1,488.24
SSᵣₑ𝓰 = 1,999.27
```

### Residual Sum of Squares (SSᵣₑₛ)
```
SSᵣₑₛ = SSᵧ - SSᵣₑ𝓰
SSᵣₑₛ = 6,462.64 - 1,999.27
SSᵣₑₛ = 4,463.37
```

---

## Step 5: ANCOVA Table

| Source | SS | df | MS | F |
|--------|---------|----|---------|----|
| Regression (Covariate) | 1,999.27 | 1 | 1,999.27 | 10.30 |
| Residual (Error) | 4,463.37 | 23 | 194.06 | |
| **Total** | **6,462.64** | **24** | | |

### Mean Squares
- MSᵣₑ𝓰 = SSᵣₑ𝓰/1 = 1,999.27
- MSᵣₑₛ = SSᵣₑₛ/23 = 194.06

### F-statistic
```
F = MSᵣₑ𝓰 / MSᵣₑₛ
F = 1,999.27 / 194.06
F = 10.30
```

**Critical value:** F₀.₀₅(1, 23) ≈ 4.28

**Conclusion:** F = 10.30 > 4.28, so bodyweight is a **significant** covariate (p < 0.05).

---

## Step 6: Hypothesis Test for Slope = 2.7

### Hypotheses
- **H₀:** β₁ = 2.7 (slope equals 2.7)
- **Hₐ:** β₁ ≠ 2.7 (slope differs from 2.7)
- **Significance level:** α = 0.05

### Standard Error of Slope
```
SE(b₁) = √(MSᵣₑₛ / SSₓ)
SE(b₁) = √(194.06 / 1,488.24)
SE(b₁) = √0.1304
SE(b₁) = 0.361
```

### Test Statistic
```
t = (b₁ - β₁₀) / SE(b₁)
t = (1.159 - 2.7) / 0.361
t = -1.541 / 0.361
t = -4.27
```

### Critical Value and Decision
- **Degrees of freedom:** df = n - 2 = 23
- **Critical value:** t₀.₀₂₅(23) ≈ ±2.069 (two-tailed test)

```
|t| = |-4.27| = 4.27 > 2.069
```

**Decision:** **REJECT H₀**

**Conclusion:** There is sufficient evidence at the 5% significance level to conclude that the slope is **significantly different from 2.7** (p < 0.05). The observed slope of 1.159 is statistically significantly lower than 2.7.

---

## Additional Statistics

### R-squared (Coefficient of Determination)
```
R² = SSᵣₑ𝓰 / SSᵧ
R² = 1,999.27 / 6,462.64
R² = 0.309 or 30.9%
```

**Interpretation:** Approximately 30.9% of the variance in deadlift performance is explained by bodyweight.

### 95% Confidence Interval for Slope
```
CI = b₁ ± t₀.₀₂₅(23) × SE(b₁)
CI = 1.159 ± 2.069 × 0.361
CI = 1.159 ± 0.747
CI = [0.412, 1.906]
```

The true slope is estimated to be between 0.412 and 1.906 with 95% confidence. Note that 2.7 falls outside this interval, confirming our hypothesis test result.

---

## Summary

1. **ANCOVA Result:** Bodyweight is a significant predictor of deadlift performance (F = 10.30, p < 0.05)

2. **Regression Model:** Each 1 kg increase in bodyweight is associated with a 1.16 kg increase in deadlift performance

3. **Hypothesis Test:** The slope is significantly different from 2.7 (t = -4.27, p < 0.05), specifically it is significantly **lower** than 2.7
