# 3-Way ANOVA: Weightlifting Performance

## Study Design
**DV:** Squat weight lifted (kg)  
**IV1:** Training program (A: Power, B: Hypertrophy)  
**IV2:** Diet (1: High protein, 2: Moderate protein)  
**IV3:** Experience (X: Novice, Y: Advanced)

## Data (n=2 per cell)

| Program | Diet | Experience | Weights (kg) |
|---------|------|------------|--------------|
| A       | 1    | X          | 120, 130     |
| A       | 1    | Y          | 180, 190     |
| A       | 2    | X          | 110, 120     |
| A       | 2    | Y          | 170, 180     |
| B       | 1    | X          | 115, 125     |
| B       | 1    | Y          | 175, 185     |
| B       | 2    | X          | 105, 115     |
| B       | 2    | Y          | 165, 175     |

## Hand Calculations

### Step 1: Basic Values
- N = 16 (total observations)
- a = 2, b = 2, c = 2, n = 2 (levels & reps)
- Grand sum (ΣX) = 2105
- Grand mean (X̄) = 2105/16 = 131.56

### Step 2: Sum of Squares Total (SST)
ΣX² = 120² + 130² + 180² + ... + 165² + 175² = 301,325

SST = ΣX² - (ΣX)²/N = 301,325 - (2105)²/16 = 301,325 - 276,940.06 = **24,384.94**

### Step 3: Cell Totals
| A-1-X | A-1-Y | A-2-X | A-2-Y | B-1-X | B-1-Y | B-2-X | B-2-Y |
|-------|-------|-------|-------|-------|-------|-------|-------|
| 250   | 370   | 230   | 350   | 240   | 360   | 220   | 340   |

### Step 4: Main Effects

**Program (A):**
- A total = 1200, B total = 905
- SSₐ = (1200²/8 + 905²/8) - (2105)²/16 = 5,439.06

**Diet (B):**
- Diet 1 total = 1220, Diet 2 total = 885
- SSᵦ = (1220²/8 + 885²/8) - (2105)²/16 = 7,006.56

**Experience (C):**
- Novice total = 940, Advanced total = 1165
- SSᵨ = (940²/8 + 1165²/8) - (2105)²/16 = 3,165.06

### Step 5: Two-Way Interactions

**A×B:**
- A-1 total = 620, A-2 total = 580, B-1 total = 600, B-2 total = 560
- SSₐᵦ = (620²/4 + 580²/4 + 600²/4 + 560²/4) - (2105)²/16 - SSₐ - SSᵦ = **6.56**

**A×C:**
- SSₐᵨ = (490²/4 + 710²/4 + 450²/4 + 690²/4) - (2105)²/16 - SSₐ - SSᵨ = **0.06**

**B×C:**
- SSᵦᵨ = (480²/4 + 740²/4 + 460²/4 + 720²/4) - (2105)²/16 - SSᵦ - SSᵨ = **0.06**

### Step 6: Three-Way Interaction
SSₐᵦᵨ = (250²/2 + 370²/2 + ... + 340²/2) - (2105)²/16 - SSₐ - SSᵦ - SSᵨ - SSₐᵦ - SSₐᵨ - SSᵦᵨ = **0.06**

### Step 7: Error
SSₑ = SST - SSₐ - SSᵦ - SSᵨ - SSₐᵦ - SSₐᵨ - SSᵦᵨ - SSₐᵦᵨ = **8,767.50**

### Step 8: ANOVA Table

| Source    | SS       | df | MS       | F     | p      |
|-----------|----------|----|----------|-------|--------|
| Program   | 5,439.06 | 1  | 5,439.06 | 4.97  | < .05  |
| Diet      | 7,006.56 | 1  | 7,006.56 | 6.40  | < .05  |
| Experience| 3,165.06 | 1  | 3,165.06 | 2.89  | ns     |
| A×B       | 6.56     | 1  | 6.56     | 0.01  | ns     |
| A×C       | 0.06     | 1  | 0.06     | 0.00  | ns     |
| B×C       | 0.06     | 1  | 0.06     | 0.00  | ns     |
| A×B×C     | 0.06     | 1  | 0.06     | 0.00  | ns     |
| Error     | 8,767.50 | 8  | 1,095.94 |       |        |
| **Total** | 24,384.94| 15 |          |       |        |

**df calculations:** Program (a-1=1), Diet (b-1=1), Experience (c-1=1), interactions (product of component dfs), Error (abc(n-1)=8), Total (N-1=15)

## Interpretation
- **Training program** significantly affects squat weight (F=4.97, p<.05): Power training yields higher lifts
- **Diet** significantly affects performance (F=6.40, p<.05): High protein diet produces better results
- **Experience** shows no significant effect (F=2.89, ns)
- **No significant interactions**: Effects are independent

## Conclusion
Both training program and diet independently improve squat performance, with no interaction effects detected.
