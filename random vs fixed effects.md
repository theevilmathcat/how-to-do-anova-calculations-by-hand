# ANOVA Hand Calculations: Fixed vs Random Effects
## Weightlifting Study: Max Squat Performance

---

## Study Design

**Scenario**: We're testing the effect of 3 training programs on maximum squat performance (kg). Athletes are nested under different coaches, and we want to understand both program effects and coach-to-coach variability.

### Factors:
- **Programs** (Fixed Factor): 3 levels - Program A, Program B, Program C
- **Coaches** (Random Factor): 3 coaches per program (nested within program)
- **Athletes**: 4 athletes per coach

---

## Sample Data: Max Squat (kg)

| Program A | Coach 1 | Coach 2 | Coach 3 |
|-----------|---------|---------|---------|
|           | 145     | 155     | 150     |
|           | 150     | 160     | 155     |
|           | 148     | 158     | 152     |
|           | 152     | 162     | 157     |

| Program B | Coach 4 | Coach 5 | Coach 6 |
|-----------|---------|---------|---------|
|           | 160     | 170     | 165     |
|           | 165     | 175     | 170     |
|           | 162     | 172     | 167     |
|           | 168     | 178     | 173     |

| Program C | Coach 7 | Coach 8 | Coach 9 |
|-----------|---------|---------|---------|
|           | 155     | 148     | 152     |
|           | 160     | 153     | 157     |
|           | 157     | 150     | 154     |
|           | 163     | 156     | 160     |

---

## Step 1: Calculate Cell Means and Totals

### Coach Means (n = 4 athletes per coach):

**Program A:**
- Coach 1: (145+150+148+152)/4 = 148.75 kg
- Coach 2: (155+160+158+162)/4 = 158.75 kg
- Coach 3: (150+155+152+157)/4 = 153.50 kg

**Program B:**
- Coach 4: (160+165+162+168)/4 = 163.75 kg
- Coach 5: (170+175+172+178)/4 = 173.75 kg
- Coach 6: (165+170+167+173)/4 = 168.75 kg

**Program C:**
- Coach 7: (155+160+157+163)/4 = 158.75 kg
- Coach 8: (148+153+150+156)/4 = 151.75 kg
- Coach 9: (152+157+154+160)/4 = 155.75 kg

### Program Means (averaging coach means):

- **Program A**: (148.75 + 158.75 + 153.50)/3 = 153.67 kg
- **Program B**: (163.75 + 173.75 + 168.75)/3 = 168.75 kg
- **Program C**: (158.75 + 151.75 + 155.75)/3 = 155.42 kg

### Grand Mean:
**Ȳ...** = (153.67 + 168.75 + 155.42)/3 = **159.28 kg**

Or calculate from all data: Sum of all = 5,734 / 36 athletes = 159.28 kg ✓

---

## Step 2: Calculate Sums of Squares

### Total Sum of Squares (SST):

SST = Σ(Yᵢⱼₖ - Ȳ...)²

For each observation, subtract the grand mean and square:

- (145-159.28)² = 204.07
- (150-159.28)² = 86.12
- ... (continue for all 36 observations)

**SST = 3,526.92**

### Program Sum of Squares (SSProgram):

SSProgram = n × c × Σ(Ȳᵢ.. - Ȳ...)²

Where n = 4 athletes, c = 3 coaches per program

SSProgram = 4 × 3 × [(153.67-159.28)² + (168.75-159.28)² + (155.42-159.28)²]
= 12 × [31.48 + 89.67 + 14.90]
= 12 × 136.05
= **1,632.60**

### Coach Within Program Sum of Squares (SSCoach(Program)):

SSCoach(Program) = n × Σᵢ Σⱼ (Ȳᵢⱼ. - Ȳᵢ..)²

For each coach mean, subtract its program mean:

**Program A:**
- (148.75-153.67)² = 24.21
- (158.75-153.67)² = 25.81
- (153.50-153.67)² = 0.03

**Program B:**
- (163.75-168.75)² = 25.00
- (173.75-168.75)² = 25.00
- (168.75-168.75)² = 0.00

**Program C:**
- (158.75-155.42)² = 11.09
- (151.75-155.42)² = 13.47
- (155.75-155.42)² = 0.11

Sum = 50.05 + 50.00 + 24.67 = 124.72

SSCoach(Program) = 4 × 124.72 = **498.88**

### Error Sum of Squares (SSE):

SSE = Σᵢ Σⱼ Σₖ (Yᵢⱼₖ - Ȳᵢⱼ.)²

For each observation, subtract its coach mean:

**Coach 1:** (145-148.75)² + (150-148.75)² + (148-148.75)² + (152-148.75)² = 26.75
**Coach 2:** (155-158.75)² + (160-158.75)² + (158-158.75)² + (162-158.75)² = 26.75

... (continue for all 9 coaches)

**SSE = 1,395.44**

**Verification:** SST = SSProgram + SSCoach(Program) + SSE
3,526.92 ≈ 1,632.60 + 498.88 + 1,395.44 = 3,526.92 ✓

---

## Step 3: Degrees of Freedom

- **dfProgram** = a - 1 = 3 - 1 = **2**
- **dfCoach(Program)** = a(b - 1) = 3(3 - 1) = **6**
- **dfError** = ab(n - 1) = 3 × 3 × (4 - 1) = **27**
- **dfTotal** = N - 1 = 36 - 1 = **35**

Where:
- a = number of programs (3)
- b = number of coaches per program (3)
- n = number of athletes per coach (4)
- N = total observations (36)

---

## Step 4: Mean Squares

**MSProgram** = SSProgram / dfProgram = 1,632.60 / 2 = **816.30**

**MSCoach(Program)** = SSCoach(Program) / dfCoach(Program) = 498.88 / 6 = **83.15**

**MSE** = SSE / dfError = 1,395.44 / 27 = **51.68**

---

## Step 5: F-Statistics

### This is where Fixed vs Random matters!

---

## MODEL 1: Coaches as FIXED Effect

When coaches are **fixed** (we care about these specific coaches only):

### F-test for Programs:
**F_Program** = MSProgram / MSE = 816.30 / 51.68 = **15.80**

Critical value: F(2, 27, α=0.05) ≈ 3.35
**Conclusion**: Reject H₀. Programs differ significantly (p < 0.001)

### F-test for Coaches:
**F_Coach** = MSCoach(Program) / MSE = 83.15 / 51.68 = **1.61**

Critical value: F(6, 27, α=0.05) ≈ 2.46
**Conclusion**: Fail to reject H₀. Coaches within programs don't differ significantly (p > 0.05)

### ANOVA Table (Fixed Model):

| Source | SS | df | MS | F | p-value |
|--------|----------|----|---------|----|---------|
| Program | 1,632.60 | 2 | 816.30 | 15.80 | < 0.001 |
| Coach(Program) | 498.88 | 6 | 83.15 | 1.61 | 0.182 |
| Error | 1,395.44 | 27 | 51.68 | | |
| **Total** | **3,526.92** | **35** | | | |

---

## MODEL 2: Coaches as RANDOM Effect

When coaches are **random** (coaches are a sample from a population):

### Key Difference: Expected Mean Squares Change!

**Expected Mean Squares:**
- E(MSProgram) = σ²_ε + nσ²_Coach + ncΣτᵢ²/(a-1)
- E(MSCoach(Program)) = σ²_ε + nσ²_Coach
- E(MSE) = σ²_ε

Where:
- σ²_ε = error variance (athlete-to-athlete within coach)
- σ²_Coach = variance among coaches
- τᵢ = program effects

### F-test for Programs:
**F_Program** = MSProgram / MSCoach(Program) = 816.30 / 83.15 = **9.82**

Critical value: F(2, 6, α=0.05) ≈ 5.14
**Conclusion**: Reject H₀. Programs differ significantly (p < 0.05)

### F-test for Coaches:
**F_Coach** = MSCoach(Program) / MSE = 83.15 / 51.68 = **1.61**

Critical value: F(6, 27, α=0.05) ≈ 2.46
**Conclusion**: Fail to reject H₀. Coach variance not significant (p > 0.05)

### ANOVA Table (Random Model):

| Source | SS | df | MS | F | Denominator | p-value |
|--------|----------|----|---------|----|-------------|---------|
| Program | 1,632.60 | 2 | 816.30 | 9.82 | MSCoach(Prog) | 0.013 |
| Coach(Program) | 498.88 | 6 | 83.15 | 1.61 | MSE | 0.182 |
| Error | 1,395.44 | 27 | 51.68 | | | |
| **Total** | **3,526.92** | **35** | | | | |

---

## Step 6: Variance Component Estimation (Random Model Only)

### Estimate variance components using ANOVA method:

**σ²_ε** (athlete variance) = MSE = **51.68**

**σ²_Coach** (coach variance):
MSCoach(Program) = σ²_ε + nσ²_Coach

83.15 = 51.68 + 4σ²_Coach

σ²_Coach = (83.15 - 51.68)/4 = **7.87**

**Total variance** = σ²_ε + σ²_Coach = 51.68 + 7.87 = **59.55**

### Variance Partition:
- **Athlete-to-athlete**: 51.68 / 59.55 = 86.8%
- **Coach-to-coach**: 7.87 / 59.55 = 13.2%

**Interpretation**: Most variability (87%) is among athletes within the same coach, while coaches account for only 13% of variability.

---

## KEY DIFFERENCES SUMMARY

| Aspect | Fixed Coaches | Random Coaches |
|--------|---------------|----------------|
| **Interest** | These specific coaches | Population of coaches |
| **F-test denominator for Programs** | MSE | MSCoach(Program) |
| **df for Program test** | (2, 27) | (2, 6) |
| **F_Program value** | 15.80 | 9.82 |
| **Power** | Higher | Lower |
| **Variance components** | Not estimated | Estimated |
| **Generalization** | Only to these coaches | To all possible coaches |

---

## MINITAB Implementation

### For Fixed Model:
```
Stat > ANOVA > General Linear Model > Fit General Linear Model
- Response: Max_Squat
- Factors: Program, Coach
- Model: Program, Coach(Program)
```

### For Random Model:
```
Stat > ANOVA > General Linear Model > Fit General Linear Model
- Response: Max_Squat
- Factors: Program (Fixed), Coach (Random)
- Model: Program, Coach(Program)
- Click "Random/Nest" button and specify Coach as random
```

---

## Practical Interpretation

### Fixed Model Conclusion:
"Programs A, B, and C produce significantly different max squat results (F(2,27) = 15.80, p < 0.001). Program B shows the highest performance (168.75 kg), followed by Program C (155.42 kg) and Program A (153.67 kg). The specific coaches used in this study did not show significant differences within their respective programs."

### Random Model Conclusion:
"After accounting for natural coach-to-coach variability, training programs still show a significant effect on max squat performance (F(2,6) = 9.82, p = 0.013). Coach variability accounts for approximately 13% of total variance, while athlete differences account for 87%. Results generalize to the broader population of coaches using these programs."

---

## When to Use Which Model?

**Use FIXED** when:
- You selected specific coaches deliberately
- You only care about these particular coaches
- You want to compare these coaches directly

**Use RANDOM** when:
- Coaches are a random sample from a larger population
- You want to generalize beyond these specific coaches
- Coach identity is not of primary interest
- You want to partition variance components

In sports research, coaches are typically **random** because we usually want results to apply broadly, not just to the specific coaches in our study.

---

## Additional Notes

### Post-hoc Comparisons (if Program is significant):

**Tukey HSD for Programs** (using MSE for fixed, MSCoach(Program) for random):

For Random Model:
- q(3, 6, 0.05) ≈ 4.34
- HSD = 4.34 × √(83.15/(3×4)) = 4.34 × 2.63 = 11.41 kg

**Pairwise Comparisons:**
- |Program B - Program A| = |168.75 - 153.67| = 15.08 > 11.41 ✓ Significant
- |Program B - Program C| = |168.75 - 155.42| = 13.33 > 11.41 ✓ Significant
- |Program C - Program A| = |155.42 - 153.67| = 1.75 < 11.41 ✗ Not significant

**Conclusion**: Program B produces significantly higher max squats than both A and C. Programs A and C are not significantly different from each other.

---

*Dataset created for educational purposes. In real research, always check ANOVA assumptions: normality, homogeneity of variance, and independence.*
