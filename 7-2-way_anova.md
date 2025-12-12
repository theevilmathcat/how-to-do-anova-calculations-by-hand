# 2-Way ANOVA Manual Calculation

## Design
- **Crossed**: Yes (every time period is observed for every store).
- **Balanced**: Yes (exactly one observation per cell).

## Data

| Time Period | Store A | Store B | Store C | Store D | Store E |
|-------------|---------|---------|---------|---------|---------|
| Morning     | 102     | 92      | 85      | 110     | 72      |
| Afternoon   | 85      | 87      | 75      | 92      | 73      |
| Night       | 75      | 80      | 71      | 77      | 76      |

## Step-by-Step Calculations

### 1. Row sums (Time periods)
- Morning: 102 + 92 + 85 + 110 + 72 = **461**
- Afternoon: 85 + 87 + 75 + 92 + 73 = **412**
- Night: 75 + 80 + 71 + 77 + 76 = **379**

### 2. Column sums (Stores)
- A: 102 + 85 + 75 = **262**
- B: 92 + 87 + 80 = **259**
- C: 85 + 75 + 71 = **231**
- D: 110 + 92 + 77 = **279**
- E: 72 + 73 + 76 = **221**

### 3. Grand total and N
- Grand total (T) = 461 + 412 + 379 = **1252**
- N = 3 × 5 = **15**

### 4. Sum of squares of all observations (∑Y_ij²)
102² + 92² + 85² + 110² + 72² + 85² + 87² + 75² + 92² + 73² + 75² + 80² + 71² + 77² + 76² = **106,360**

### 5. Correction factor (T²/N)
1252² = 1,567,504  
1,567,504 / 15 = **104,500.2667**

### 6. SS_Total
106,360 − 104,500.2667 = **1,859.7333**

### 7. SS_Time (rows)
(461² + 412² + 379²) / 5 = 525,906 / 5 = 105,181.2  
105,181.2 − 104,500.2667 = **680.9333**

### 8. SS_Store (columns)
(262² + 259² + 231² + 279² + 221²) / 3 = 315,768 / 3 = 105,256  
105,256 − 104,500.2667 = **755.7333**

### 9. SS_Interaction
SS_Total − SS_Time − SS_Store = 1,859.7333 − 680.9333 − 755.7333 = **423.0667**

### 10. Degrees of freedom
- df_Time = 3 − 1 = **2**
- df_Store = 5 − 1 = **4**
- df_Interaction = 2 × 4 = **8**
- df_Total = 15 − 1 = **14**

### 11. Mean squares
- MS_Time = 680.9333 / 2 = **340.4667**
- MS_Store = 755.7333 / 4 = **188.9333**
- MS_Interaction = 423.0667 / 8 = **52.8833**

### 12. F-ratios
- F_Time = 340.4667 / 52.8833 ≈ **6.44**
- F_Store = 188.9333 / 52.8833 ≈ **3.57**

## ANOVA Table

| Source       | df | SS       | MS       | F     |
|--------------|----|----------|----------|-------|
| Time         | 2  | 680.93   | 340.47   | 6.44  |
| Store        | 4  | 755.73   | 188.93   | 3.57  |
| Interaction  | 8  | 423.07   | 52.88    |       |
| Total        | 14 | 1,859.73 |          |       |

## Significance (α = 0.05)
- Critical F(2,8) ≈ 4.46 → Time effect **significant** (6.44 > 4.46)
- Critical F(4,8) ≈ 3.84 → Store effect **not significant** (3.57 < 3.84)

*Note: With no replicates per cell, interaction term is used as the error term for testing main effects.*