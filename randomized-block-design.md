# Randomized Block Design ANOVA (By Hand Calculation)

## Scenario
A strength coach wants to test 3 different training programs (Treatment) on squat performance. Since lifters vary greatly in baseline strength, each lifter (Block) tries all 3 programs in random order with washout periods between. We measure max squat (kg) after each program.

**Key Point**: Blocks control for individual differences. Each lifter is a "block" that experiences all treatments.

## Data

| Lifter (Block) | Program A | Program B | Program C | Block Total | Block Mean |
|----------------|-----------|-----------|-----------|-------------|------------|
| Lifter 1       | 140       | 145       | 150       | 435         | 145.0      |
| Lifter 2       | 160       | 168       | 175       | 503         | 167.7      |
| Lifter 3       | 120       | 125       | 128       | 373         | 124.3      |
| Lifter 4       | 180       | 188       | 195       | 563         | 187.7      |
| Lifter 5       | 150       | 155       | 162       | 467         | 155.7      |
| **Treatment Total** | **750** | **781** | **810** | **2341** | |
| **Treatment Mean** | **150.0** | **156.2** | **162.0** | | **156.1** (Grand Mean) |

n = 5 lifters (blocks)
k = 3 programs (treatments)
N = 15 total observations

## Step 1: Calculate Sum of Squares Total (SST)

**Formula**: SST = Σ(X - X̄)²

```
SST = (140-156.1)² + (145-156.1)² + (150-156.1)² +
      (160-156.1)² + (168-156.1)² + (175-156.1)² +
      (120-156.1)² + (125-156.1)² + (128-156.1)² +
      (180-156.1)² + (188-156.1)² + (195-156.1)² +
      (150-156.1)² + (155-156.1)² + (162-156.1)²

SST = 259.21 + 123.21 + 37.21 + 15.21 + 141.61 + 357.21 +
      1303.21 + 967.21 + 789.61 + 571.21 + 1017.61 + 1512.81 +
      37.21 + 1.21 + 34.81

SST = 7168.54
```

## Step 2: Calculate Sum of Squares Between Treatments (SSA)

**Formula**: SSA = n × Σ(X̄ⱼ - X̄)²

Where n = number of blocks per treatment

```
SSA = 5 × [(150.0-156.1)² + (156.2-156.1)² + (162.0-156.1)²]

SSA = 5 × [37.21 + 0.01 + 34.81]

SSA = 5 × 72.03

SSA = 360.15
```

## Step 3: Calculate Sum of Squares Between Blocks (SSB)

**Formula**: SSB = k × Σ(X̄ᵢ - X̄)²

Where k = number of treatments per block

```
SSB = 3 × [(145.0-156.1)² + (167.7-156.1)² + (124.3-156.1)² + 
           (187.7-156.1)² + (155.7-156.1)²]

SSB = 3 × [123.21 + 134.56 + 1011.24 + 998.56 + 0.16]

SSB = 3 × 2267.73

SSB = 6803.19
```

## Step 4: Calculate Sum of Squares Error (SSE)

**Formula**: SSE = SST - SSA - SSB

```
SSE = 7168.54 - 360.15 - 6803.19

SSE = 5.20
```

## Step 5: Calculate Degrees of Freedom

```
df_Total = N - 1 = 15 - 1 = 14

df_Treatment = k - 1 = 3 - 1 = 2

df_Block = n - 1 = 5 - 1 = 4

df_Error = (n-1)(k-1) = (5-1)(3-1) = 4 × 2 = 8
```

**Check**: df_Treatment + df_Block + df_Error = 2 + 4 + 8 = 14 ✓

## Step 6: Calculate Mean Squares

```
MS_Treatment = SSA / df_Treatment = 360.15 / 2 = 180.08

MS_Block = SSB / df_Block = 6803.19 / 4 = 1700.80

MS_Error = SSE / df_Error = 5.20 / 8 = 0.65
```

## Step 7: Calculate F-Statistics

**For Treatment Effect:**
```
F_Treatment = MS_Treatment / MS_Error = 180.08 / 0.65 = 277.05
```

**For Block Effect (usually not tested, but can be):**
```
F_Block = MS_Block / MS_Error = 1700.80 / 0.65 = 2616.62
```

## Step 8: ANOVA Summary Table

| Source      | SS      | df | MS      | F       | Critical F (α=0.05) | Decision |
|-------------|---------|----|---------|---------|--------------------|----------|
| Treatment   | 360.15  | 2  | 180.08  | 277.05  | F(2,8) = 4.46      | Reject H₀ |
| Block       | 6803.19 | 4  | 1700.80 | 2616.62 | F(4,8) = 3.84      | (Nuisance) |
| Error       | 5.20    | 8  | 0.65    |         |                    |          |
| **Total**   | **7168.54** | **14** |     |         |                    |          |

## Interpretation

**Treatment Effect**: F(2,8) = 277.05, p < 0.001
- There is a significant difference between training programs
- Program C (162 kg) > Program B (156.2 kg) > Program A (150 kg)

**Block Effect**: The large F-value for blocks confirms that lifters differ substantially in baseline strength (as expected). This is why we blocked on lifter—it removes this variance from error, making our treatment test more powerful.

**Effect Size (Partial η²)**:
```
η²_Treatment = SSA / (SSA + SSE) = 360.15 / 365.35 = 0.986

This is a huge effect! Programs explain 98.6% of the variance after controlling for lifter differences.
```

## Why Randomized Block Design?

**Compared to One-Way Between-Subjects**:
- If we ignored blocks and treated this as one-way ANOVA, MS_Error would include all the between-lifter variance
- MS_Error would be approximately (6803.19 + 5.20) / 12 = 567.37
- F would be 180.08 / 567.37 = 0.32 (not significant!)
- **Blocking increased our F-ratio by 866x** by removing nuisance variance

**When to Use**:
- When experimental units are heterogeneous (lifters vary in strength)
- When you can group units into homogeneous blocks
- When each treatment can be applied within each block
- Similar to within-subjects, but without repeated measures on same DV

## Post-Hoc Comparisons

With significant F, compare treatment means using Tukey HSD or Bonferroni:

**Example: Tukey HSD**
```
HSD = q × √(MS_Error / n)

For α=0.05, df_error=8, k=3 treatments: q ≈ 4.04

HSD = 4.04 × √(0.65 / 5) = 4.04 × 0.36 = 1.45 kg

Pairwise differences:
- Program C vs A: 162.0 - 150.0 = 12.0 kg > 1.45 (significant)
- Program C vs B: 162.0 - 156.2 = 5.8 kg > 1.45 (significant)
- Program B vs A: 156.2 - 150.0 = 6.2 kg > 1.45 (significant)

All programs differ significantly from each other.
```

## Assumptions

1. **Independence**: Observations are independent across blocks (different lifters)
2. **Normality**: Residuals are normally distributed
3. **Homogeneity of Variance**: Variance is constant across treatment-block combinations
4. **No Treatment-Block Interaction**: Effect of treatment is same across all blocks (if violated, consider two-way ANOVA with interaction)

## R Code (Verification)

```r
lifter <- factor(rep(1:5, each=3))
program <- factor(rep(c("A","B","C"), 5))
squat <- c(140,145,150, 160,168,175, 120,125,128, 180,188,195, 150,155,162)

model <- aov(squat ~ program + lifter)
summary(model)
```
