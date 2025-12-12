# One-Way Between-Subjects ANOVA Calculation by Hand

## Scenario
Independent factor: Program (3 levels: A, B, C)  
Dependent variable: Squat_1RM  
Between-subjects design (different lifters in each group)  
n = 2 per group, total N = 6

## Data Table

| Lifter | Program | Squat_1RM |
|--------|---------|-----------|
| 1      | A       | 150       |
| 2      | A       | 155       |
| 3      | B       | 145       |
| 4      | B       | 142       |
| 5      | C       | 170       |
| 6      | C       | 168       |

## Step 1: Calculate Group Means and Grand Mean
- Program A: (150 + 155) / 2 = 305 / 2 = 152.5
- Program B: (145 + 142) / 2 = 287 / 2 = 143.5
- Program C: (170 + 168) / 2 = 338 / 2 = 169.0
- Grand mean (ȳ••): Total sum = 150+155+145+142+170+168 = 930  
  ȳ•• = 930 / 6 = 155

## Step 2: Sum of Squares (SS)

### Method 1: Computational Formula
- Sum of all y² = 150² + 155² + 145² + 142² + 170² + 168²  
  = 22500 + 24025 + 21025 + 20164 + 28900 + 28224 = 144838
- Correction factor = (total sum)² / N = 930² / 6 = 864900 / 6 = 144150

- **SS_Total** = Σy² - correction = 144838 - 144150 = 688

- **SS_Between** (Program) = Σ(n_i × (ȳ_i - ȳ••)²)  
  = 2×(152.5 - 155)² + 2×(143.5 - 155)² + 2×(169 - 155)²  
  = 2×(-2.5)² + 2×(-11.5)² + 2×(14)²  
  = 2×6.25 + 2×132.25 + 2×196  
  = 12.5 + 264.5 + 392 = 669

- **SS_Within** (Error) = SS_Total - SS_Between = 688 - 669 = 19

### Alternative Within-Group Calculation (for verification)
- Group A: (150-152.5)² + (155-152.5)² = 6.25 + 6.25 = 12.5
- Group B: (145-143.5)² + (142-143.5)² = 2.25 + 2.25 = 4.5
- Group C: (170-169)² + (168-169)² = 1 + 1 = 2
- Total SS_Within = 12.5 + 4.5 + 2 = 19

## Step 3: Degrees of Freedom (df)
- df_Between = k - 1 = 3 - 1 = 2 (k = number of groups)
- df_Within  = N - k = 6 - 3 = 3
- df_Total   = N - 1 = 5

## Step 4: Mean Squares (MS)
- MS_Between = SS_Between / df_Between = 669 / 2 = 334.5
- MS_Within  = SS_Within / df_Within   = 19 / 3 ≈ 6.3333

## Step 5: F-Statistic
- F = MS_Between / MS_Within = 334.5 / 6.3333 ≈ 52.82
- Critical F(2,3) at α = 0.05 ≈ 9.55 (from F-table)  
  Since 52.82 >> 9.55 → significant effect of Program (p < 0.05)

## ANOVA Table

| Source      | df | SS    | MS     | F      |
|-------------|----|-------|--------|--------|
| Program     | 2  | 669   | 334.5  | 52.82  |
| Within (Error) | 3  | 19    | 6.33   |        |
| Total       | 5  | 688   |        |        |
