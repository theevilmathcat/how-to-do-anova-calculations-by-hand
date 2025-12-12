# 2-Way Within-Subjects (Repeated Measures) ANOVA Manual Calculation

## Design Characteristics

**Design Type:** Within-subjects (repeated measures) on BOTH factors
- Same lifters measured under all combinations of exercise and grip type
- Each lifter is their own control

**Balance:** Balanced design
- All lifters complete all 6 conditions (3 exercises × 2 grips = 6 measurements per lifter)

**Crossed:** Yes
- Every exercise is performed with every grip type
- Two factors: Exercise Type (3 levels) and Grip Type (2 levels)

## Scenario

5 weightlifters perform pulling exercises (kg) under different conditions:
- **Factor A (Exercise):** Deadlift, Romanian Deadlift (RDL), Rack Pull
- **Factor B (Grip):** Double Overhand, Hook Grip

Each lifter completes all 6 combinations in randomized order on different days.

## Data (Weight lifted in kg)

| Lifter | Deadlift-Overhand | Deadlift-Hook | RDL-Overhand | RDL-Hook | RackPull-Overhand | RackPull-Hook |
|--------|-------------------|---------------|--------------|----------|-------------------|---------------|
| L1     | 140               | 145           | 155          | 160      | 165               | 170           |
| L2     | 130               | 135           | 145          | 150      | 155               | 160           |
| L3     | 150               | 155           | 165          | 170      | 175               | 180           |
| L4     | 135               | 140           | 150          | 155      | 160               | 165           |
| L5     | 145               | 150           | 160          | 165      | 170               | 175           |

## Reorganized Data Table

|        | **Deadlift**    |      | **RDL**         |      | **Rack Pull**   |      |
|--------|-----------------|------|-----------------|------|-----------------|------|
|        | Overhand        | Hook | Overhand        | Hook | Overhand        | Hook |
| **L1** | 140             | 145  | 155             | 160  | 165             | 170  |
| **L2** | 130             | 135  | 145             | 150  | 155             | 160  |
| **L3** | 150             | 155  | 165             | 170  | 175             | 180  |
| **L4** | 135             | 140  | 150             | 155  | 160             | 165  |
| **L5** | 145             | 150  | 160             | 165  | 170             | 175  |

## Step 1: Calculate Basic Statistics

### Cell Totals (sum across 5 lifters)

|          | Overhand | Hook | **Row Total** |
|----------|----------|------|---------------|
| Deadlift | 700      | 725  | **1,425**     |
| RDL      | 775      | 800  | **1,575**     |
| Rack Pull| 825      | 850  | **1,675**     |
| **Col Total** | **2,300** | **2,375** | **Grand: 4,675** |

### Subject Totals (sum across all 6 conditions per lifter)

- L1: 140 + 145 + 155 + 160 + 165 + 170 = **935**
- L2: 130 + 135 + 145 + 150 + 155 + 160 = **875**
- L3: 150 + 155 + 165 + 170 + 175 + 180 = **995**
- L4: 135 + 140 + 150 + 155 + 160 + 165 = **905**
- L5: 145 + 150 + 160 + 165 + 170 + 175 = **965**

### Overall Statistics
- N = 5 lifters × 6 conditions = **30** total observations
- Grand Total (G) = **4,675**
- Grand Mean = 4,675 / 30 = **155.83 kg**

## Step 2: Correction Factor (CF)

CF = G² / N = 4,675² / 30 = 21,855,625 / 30 = **728,520.8333**

## Step 3: Total Sum of Squares (SS_Total)

Sum all individual squared values:

**Deadlift:**
- L1: 140² + 145² = 19,600 + 21,025 = 40,625
- L2: 130² + 135² = 16,900 + 18,225 = 35,125
- L3: 150² + 155² = 22,500 + 24,025 = 46,525
- L4: 135² + 140² = 18,225 + 19,600 = 37,825
- L5: 145² + 150² = 21,025 + 22,500 = 43,525

**RDL:**
- L1: 155² + 160² = 24,025 + 25,600 = 49,625
- L2: 145² + 150² = 21,025 + 22,500 = 43,525
- L3: 165² + 170² = 27,225 + 28,900 = 56,125
- L4: 150² + 155² = 22,500 + 24,025 = 46,525
- L5: 160² + 165² = 25,600 + 27,225 = 52,825

**Rack Pull:**
- L1: 165² + 170² = 27,225 + 28,900 = 56,125
- L2: 155² + 160² = 24,025 + 25,600 = 49,625
- L3: 175² + 180² = 30,625 + 32,400 = 63,025
- L4: 160² + 165² = 25,600 + 27,225 = 52,825
- L5: 170² + 175² = 28,900 + 30,625 = 59,525

ΣY² = 40,625 + 35,125 + 46,525 + 37,825 + 43,525 + 49,625 + 43,525 + 56,125 + 46,525 + 52,825 + 56,125 + 49,625 + 63,025 + 52,825 + 59,525 = **733,400**

**SS_Total = 733,400 - 728,520.8333 = 4,879.1667**

## Step 4: Between-Subjects Sum of Squares (SS_Subjects)

SS_Subjects = (Σ Subject totals² / number of conditions) - CF

= (935² + 875² + 995² + 905² + 965²) / 6 - CF

= (874,225 + 765,625 + 990,025 + 819,025 + 931,225) / 6 - CF

= 4,380,125 / 6 - 728,520.8333

= 730,020.8333 - 728,520.8333

**SS_Subjects = 1,500.0000**

## Step 5: Within-Subjects Sum of Squares

SS_Within = SS_Total - SS_Subjects = 4,879.1667 - 1,500.0000 = **3,379.1667**

## Step 6: Factor A (Exercise Type) Sum of Squares

SS_A = (Σ Exercise totals² / (n × b)) - CF

where n = 5 lifters, b = 2 grip types

= (1,425² + 1,575² + 1,675²) / (5 × 2) - CF

= (2,030,625 + 2,480,625 + 2,805,625) / 10 - CF

= 7,316,875 / 10 - 728,520.8333

= 731,687.5 - 728,520.8333

**SS_A = 3,166.6667**

## Step 7: Factor B (Grip Type) Sum of Squares

SS_B = (Σ Grip type totals² / (n × a)) - CF

where n = 5 lifters, a = 3 exercises

= (2,300² + 2,375²) / (5 × 3) - CF

= (5,290,000 + 5,640,625) / 15 - CF

= 10,930,625 / 15 - 728,520.8333

= 728,708.3333 - 728,520.8333

**SS_B = 187.5000**

## Step 8: A × B Interaction Sum of Squares

First calculate SS_AB (cells):

SS_Cells = (Σ Each cell total² / n) - CF

= (700² + 725² + 775² + 800² + 825² + 850²) / 5 - CF

= (490,000 + 525,625 + 600,625 + 640,000 + 680,625 + 722,500) / 5 - CF

= 3,659,375 / 5 - 728,520.8333

= 731,875 - 728,520.8333

= 3,354.1667

**SS_A×B = SS_Cells - SS_A - SS_B**

= 3,354.1667 - 3,166.6667 - 187.5000

**SS_A×B = 0.0000**

(No interaction in this dataset - effects are perfectly additive)

## Step 9: Error Terms (Residuals)

### SS_Subjects×A (Error term for Factor A)

This is the residual variation of subjects across levels of A, removing the main effect of A.

For each subject, calculate their totals at each level of A (collapsing across B):

|     | Deadlift | RDL  | Rack Pull |
|-----|----------|------|-----------|
| L1  | 285      | 315  | 335       |
| L2  | 265      | 295  | 315       |
| L3  | 305      | 335  | 355       |
| L4  | 275      | 305  | 325       |
| L5  | 295      | 325  | 345       |

Sum of squares for Subject×A table:

= (285² + 315² + 335² + 265² + 295² + 315² + 305² + 335² + 355² + 275² + 305² + 325² + 295² + 325² + 345²) / 2 - CF - SS_Subjects - SS_A

= (81,225 + 99,225 + 112,225 + 70,225 + 87,025 + 99,225 + 93,025 + 112,225 + 126,025 + 75,625 + 93,025 + 105,625 + 87,025 + 105,625 + 119,025) / 2 - CF - SS_Subjects - SS_A

= 1,466,375 / 2 - 728,520.8333 - 1,500.0000 - 3,166.6667

= 733,187.5 - 733,187.5

**SS_Subjects×A = 0.0000**

(Perfect additivity in this example)

### SS_Subjects×B (Error term for Factor B)

For each subject, calculate their totals at each level of B (collapsing across A):

|     | Overhand | Hook |
|-----|----------|------|
| L1  | 460      | 475  |
| L2  | 430      | 445  |
| L3  | 490      | 505  |
| L4  | 445      | 460  |
| L5  | 475      | 490  |

Sum of squares for Subject×B table:

= (460² + 475² + 430² + 445² + 490² + 505² + 445² + 460² + 475² + 490²) / 3 - CF - SS_Subjects - SS_B

= (211,600 + 225,625 + 184,900 + 198,025 + 240,100 + 255,025 + 198,025 + 211,600 + 225,625 + 240,100) / 3 - CF - SS_Subjects - SS_B

= 2,190,625 / 3 - 728,520.8333 - 1,500.0000 - 187.5000

= 730,208.3333 - 730,208.3333

**SS_Subjects×B = 0.0000**

### SS_Subjects×A×B (Residual error for interaction)

SS_Subjects×A×B = SS_Within - SS_A - SS_B - SS_A×B - SS_Subjects×A - SS_Subjects×B

= 3,379.1667 - 3,166.6667 - 187.5000 - 0 - 0 - 0

**SS_Subjects×A×B = 25.0000**

## Step 10: Degrees of Freedom

- **df_Subjects** = n - 1 = 5 - 1 = **4**
- **df_A (Exercise)** = a - 1 = 3 - 1 = **2**
- **df_B (Grip)** = b - 1 = 2 - 1 = **1**
- **df_A×B** = (a - 1)(b - 1) = 2 × 1 = **2**
- **df_Subjects×A** = (n - 1)(a - 1) = 4 × 2 = **8**
- **df_Subjects×B** = (n - 1)(b - 1) = 4 × 1 = **4**
- **df_Subjects×A×B** = (n - 1)(a - 1)(b - 1) = 4 × 2 × 1 = **8**
- **df_Total** = N - 1 = 30 - 1 = **29**

## Step 11: Mean Squares

- **MS_A** = SS_A / df_A = 3,166.6667 / 2 = **1,583.3333**
- **MS_B** = SS_B / df_B = 187.5000 / 1 = **187.5000**
- **MS_A×B** = SS_A×B / df_A×B = 0.0000 / 2 = **0.0000**
- **MS_Subjects×A** = SS_Subjects×A / df_Subjects×A = 0.0000 / 8 = **0.0000**
- **MS_Subjects×B** = SS_Subjects×B / df_Subjects×B = 0.0000 / 4 = **0.0000**
- **MS_Subjects×A×B** = SS_Subjects×A×B / df_Subjects×A×B = 25.0000 / 8 = **3.1250**

## Step 12: F-ratios

In 2-way within-subjects ANOVA, each effect has its own error term:

- **F_A** = MS_A / MS_Subjects×A = 1,583.3333 / 0.0000 = **∞** (undefined, but clearly significant)
  - Since error is 0, we can use MS_Subjects×A×B as conservative error: 1,583.3333 / 3.1250 = **506.67**

- **F_B** = MS_B / MS_Subjects×B = 187.5000 / 0.0000 = **∞** (undefined, but clearly significant)
  - Using MS_Subjects×A×B: 187.5000 / 3.1250 = **60.00**

- **F_A×B** = MS_A×B / MS_Subjects×A×B = 0.0000 / 3.1250 = **0.00**

## ANOVA Summary Table

| Source              | SS        | df | MS        | F       | p-value      |
|---------------------|-----------|----|-----------|---------| -------------|
| Between Subjects    |           |    |           |         |              |
| Subjects            | 1,500.00  | 4  | 375.00    |         |              |
| **Within Subjects** |           |    |           |         |              |
| Exercise (A)        | 3,166.67  | 2  | 1,583.33  | 506.67* | < .001       |
| Subjects×A          | 0.00      | 8  | 0.00      |         |              |
| Grip (B)            | 187.50    | 1  | 187.50    | 60.00*  | < .001       |
| Subjects×B          | 0.00      | 4  | 0.00      |         |              |
| A×B Interaction     | 0.00      | 2  | 0.00      | 0.00    | n.s.         |
| Subjects×A×B        | 25.00     | 8  | 3.13      |         |              |
| **Total**           | 4,879.17  | 29 |           |         |              |

*Used MS_Subjects×A×B as conservative error term when specific error = 0

## Critical F-values (α = 0.05)

- F_critical(2, 8) ≈ **4.46** → Exercise effect highly significant
- F_critical(1, 4) ≈ **7.71** → Grip effect highly significant
- F_critical(2, 8) ≈ **4.46** → No interaction

## Interpretation

**Main Effect of Exercise Type:** Highly significant. Lifters can handle progressively more weight: Deadlift (142.5kg) < RDL (157.5kg) < Rack Pull (167.5kg average). This makes sense as rack pulls have shorter range of motion.

**Main Effect of Grip Type:** Highly significant. Hook grip allows ~5kg heavier lifts on average (Overhand: 153.3kg vs Hook: 158.3kg). The hook grip provides better security on the bar.

**Interaction:** Not significant. The benefit of hook grip is consistent across all exercise types (always ~5kg advantage), and the weight progression across exercises is consistent for both grip types.

## Key Insight for Within-Subjects Design

The power of this design is that we **remove individual differences** (lifter strength variation) from the error term. Each lifter serves as their own control, making it easier to detect the effects of exercise type and grip type despite individual strength differences (L3 is strongest, L2 is weakest, but this doesn't obscure the treatment effects).

*Note: This example was constructed with perfect additivity (zero interactions and subject-interaction errors) to make hand calculation tractable while demonstrating the structure of 2-way repeated measures ANOVA.*
