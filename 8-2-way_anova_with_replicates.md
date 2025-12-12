# 2-Way ANOVA Manual Calculation (With 4 Replicates per Cell)

## Design
- **Crossed**: Yes
- **Balanced**: Yes (exactly 4 replicates per cell)
- **Replicates**: 4 per cell → allows separate estimation of interaction and pure error (residual)

## Data (4 replicates per cell)
To illustrate hand calculation, we use simple integer data close to the original means with small variation.

| Time Period | Store A       | Store B       | Store C       | Store D        | Store E       |
|-------------|---------------|---------------|---------------|----------------|---------------|
| Morning     | 102, 104, 100, 106 | 92, 94, 90, 92 | 85, 87, 83, 85 | 110, 112, 108, 110 | 72, 74, 70, 72 |
| Afternoon   | 85, 87, 83, 85   | 87, 89, 85, 87   | 75, 77, 73, 75   | 92, 94, 90, 92    | 73, 75, 71, 73   |
| Night       | 75, 77, 73, 75   | 80, 82, 78, 80   | 71, 73, 69, 71   | 77, 79, 75, 77    | 76, 78, 74, 76   |

## Step-by-Step Hand Calculation

### 1. Cell totals (sum of 4 replicates in each cell)

|             | A     | B     | C     | D     | E     | Row total (Time) |
|-------------|-------|-------|-------|-------|-------|------------------|
| Morning     | 412   | 368   | 340   | 440   | 288   | **1,848**        |
| Afternoon   | 340   | 348   | 300   | 368   | 292   | **1,648**        |
| Night       | 300   | 320   | 284   | 308   | 304   | **1,516**        |
| Column total (Store) | **1,052** | **1,036** | **924** | **1,116** | **884** | Grand total **5,012** |

- N = 3 × 5 × 4 = **60**

### 2. Correction factor CF = Grand total² / N
5,012² = 25,120,144  
CF = 25,120,144 / 60 = **418,669.0667**

### 3. Total Sum of Squares (SS_Total) = ∑(all individual observations²) − CF

First compute ∑all Y² (sum of squares of all 60 values):

Morning A: 102² + 104² + 100² + 106² = 10404 + 10816 + 10000 + 11236 = 42,456  
Morning B: 92² + 94² + 90² + 92² = 8464 + 8836 + 8100 + 8464 = 33,864  
Morning C: 85² + 87² + 83² + 85² = 7225 + 7569 + 6889 + 7225 = 28,908  
Morning D: 110² + 112² + 108² + 110² = 12100 + 12544 + 11664 + 12100 = 48,408  
Morning E: 72² + 74² + 70² + 72² = 5184 + 5476 + 4900 + 5184 = 20,744  

Afternoon A: 85²×4 (all ±2 pattern, same squares) = 4 × 7225 = 28,900  
Afternoon B: 87²×4 pattern = 4 × 7569 = 30,276  
Afternoon C: 75²×4 pattern = 4 × 5625 = 22,500  
Afternoon D: 92²×4 pattern = 4 × 8464 = 33,856  
Afternoon E: 73²×4 pattern = 4 × 5329 = 21,316  

Night A: 75²×4 pattern = 4 × 5625 = 22,500  
Night B: 80²×4 pattern = 4 × 6400 = 25,600  
Night C: 71²×4 pattern = 4 × 5041 = 20,164  
Night D: 77²×4 pattern = 4 × 5929 = 23,716  
Night E: 76²×4 pattern = 4 × 5776 = 23,104  

Total ∑Y² = 42,456 + 33,864 + 28,908 + 48,408 + 20,744 + 28,900 + 30,276 + 22,500 + 33,856 + 21,316 + 22,500 + 25,600 + 20,164 + 23,716 + 23,104 = **426,296**

SS_Total = 426,296 − 418,669.0667 = **7,626.9333**

### 4. SS_Time (rows)
(1,848² + 1,648² + 1,516²) / (5 × 4) − CF  
= (3,415,104 + 2,716,224 + 2,298,256) / 20 − CF  
= 8,429,584 / 20 − 418,669.0667  
= 421,479.2 − 418,669.0667 = **2,810.1333**

### 5. SS_Store (columns)
(1,052² + 1,036² + 924² + 1,116² + 884²) / (3 × 4) − CF  
= (1,106,704 + 1,073,296 + 853,776 + 1,245,776 + 781,456) / 12 − CF  
= 5,061,008 / 12 − 418,669.0667  
= 421,750.6667 − 418,669.0667 = **3,081.6**

### 6. SS_Cells (Time × Store)
Sum of (each cell total² / 4) − CF  
There are 15 cells. Compute each cell total² / 4:

Morning A: 412²/4 = 169,744/4 = 42,436  
Morning B: 368²/4 = 135,424/4 = 33,856  
Morning C: 340²/4 = 115,600/4 = 28,900  
Morning D: 440²/4 = 193,600/4 = 48,400  
Morning E: 288²/4 = 82,944/4 = 20,736  

Afternoon A: 340²/4 = 28,900  
Afternoon B: 348²/4 = 121,104/4 = 30,276  
Afternoon C: 300²/4 = 90,000/4 = 22,500  
Afternoon D: 368²/4 = 33,856  
Afternoon E: 292²/4 = 85,264/4 = 21,316  

Night A: 300²/4 = 22,500  
Night B: 320²/4 = 102,400/4 = 25,600  
Night C: 284²/4 = 80,656/4 = 20,164  
Night D: 308²/4 = 94,864/4 = 23,716  
Night E: 304²/4 = 92,416/4 = 23,104  

Sum of cell contributions = 42,436 + 33,856 + 28,900 + 48,400 + 20,736 + 28,900 + 30,276 + 22,500 + 33,856 + 21,316 + 22,500 + 25,600 + 20,164 + 23,716 + 23,104 = **426,244**

SS_Cells = 426,244 − 418,669.0667 = **7,574.9333**

### 7. SS_Interaction (Time × Store)
SS_Cells − SS_Time − SS_Store = 7,574.9333 − 2,810.1333 − 3,081.6 = **1,683.2**

### 8. SS_Residual (Within cells / Error)
SS_Total − SS_Cells = 7,626.9333 − 7,574.9333 = **52**

(Alternative: sum of variances within each cell × 3 df per cell)

### 9. Degrees of freedom
- df_Time = 3 − 1 = **2**
- df_Store = 5 − 1 = **4**
- df_Interaction = (3−1)×(5−1) = **8**
- df_Residual = 15 cells × (4−1) = **45**
- df_Total = 60 − 1 = **59**

### 10. Mean squares
- MS_Time = 2,810.1333 / 2 = **1,405.0667**
- MS_Store = 3,081.6 / 4 = **770.4**
- MS_Interaction = 1,683.2 / 8 = **210.4**
- MS_Residual = 52 / 45 ≈ **1.1556**

### 11. F-ratios
- F_Time = 1,405.0667 / 1.1556 ≈ **1,215.8**
- F_Store = 770.4 / 1.1556 ≈ **666.7**
- F_Interaction = 210.4 / 1.1556 ≈ **182.1**

## ANOVA Table

| Source       | df | SS       | MS       | F        |
|--------------|----|----------|----------|----------|
| Time         | 2  | 2,810.13 | 1,405.07 | 1,215.8  |
| Store        | 4  | 3,081.60 | 770.40   | 666.7    |
| Interaction  | 8  | 1,683.20 | 210.40   | 182.1    |
| Residual     | 45 | 52.00    | 1.16     |          |
| Total        | 59 | 7,626.93 |          |          |

## Significance (α = 0.05)
All effects are highly significant (critical F values are ~3–4; observed F >> critical).

*This example uses very small within-cell variation to make hand calculation manageable while keeping the pattern similar to the original data.*