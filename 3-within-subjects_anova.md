# Within-Subjects (Repeated Measures) ANOVA By Hand

## Data

| Lifter | Week1 | Week2 | Week3 | Week4 |
|--------|-------|-------|-------|-------|
| 1      | 100   | 105   | 108   | 112   |
| 2      | 120   | 122   | 125   | 130   |
| 3      | 90    | 95    | 98    | 100   |

n = 3 (subjects)  
k = 4 (conditions/weeks)  
Total observations N = 12

## Step 1: Compute Means

- Subject (row) means:  
  Lifter 1: (100 + 105 + 108 + 112)/4 = 106.25  
  Lifter 2: (120 + 122 + 125 + 130)/4 = 124.25  
  Lifter 3: (90 + 95 + 98 + 100)/4 = 95.75  

- Condition (column) means:  
  Week1: (100 + 120 + 90)/3 = 103.333  
  Week2: (105 + 122 + 95)/3 = 107.333  
  Week3: (108 + 125 + 98)/3 = 110.333  
  Week4: (112 + 130 + 100)/3 = 114.000  

- Grand mean: (sum of all scores)/12 = 1305 / 12 = **108.75**

## Step 2: Sum of Squares (SS)

### SS Total  
∑(each score - grand mean)²  

Calculations:  
100² term: (100 - 108.75)² = (-8.75)² = 76.5625  
105: (105 - 108.75)² = 14.0625  
108: 0.5625  
112: 10.5625  
120: 126.5625  
122: 174.5625  
125: 263.0625  
130: 441.5625  
90: 351.5625  
95: 189.0625  
98: 116.5625  
100: 76.5625  

SS Total = **1852.25**

### SS Subjects (Between Subjects)  
k × ∑(subject mean - grand mean)²  

(106.25 - 108.75)² = (-2.5)² = 6.25  
(124.25 - 108.75)² = (15.5)² = 240.25  
(95.75 - 108.75)² = (-13)² = 169  

Sum = 6.25 + 240.25 + 169 = 415.5  
SS Subjects = 4 × 415.5 = **1662**

### SS Treatments (Between Weeks)  
n × ∑(condition mean - grand mean)²  

(103.333 - 108.75)² ≈ (-5.417)² ≈ 29.34  
(107.333 - 108.75)² ≈ (-1.417)² ≈ 2.01  
(110.333 - 108.75)² ≈ (1.583)² ≈ 2.51  
(114 - 108.75)² = (5.25)² = 27.5625  

Sum ≈ 29.34 + 2.01 + 2.51 + 27.5625 ≈ 61.4325  
SS Treatments = 3 × 61.4325 ≈ **184.3**

(Exact: use fractions 310/3, 322/3, 331/3, 342/3  
Deviations: -65/12, -17/12, 19/12, 63/12  
Squares sum = (65² + 17² + 19² + 63²)/144 = (4225 + 289 + 361 + 3969)/144 = 8844/144 = 61.4167  
SS Treatments = 3 × 61.4167 = **184.25**)

### SS Within  
SS Total - SS Subjects = 1852.25 - 1662 = **190.25**

### SS Error (Residual)  
SS Within - SS Treatments = 190.25 - 184.25 = **6**

## Step 3: Degrees of Freedom

- df Treatments = k - 1 = 3  
- df Subjects = n - 1 = 2  
- df Error = (n - 1)(k - 1) = 2 × 3 = 6  
- df Within = n(k - 1) = 9  
- df Total = N - 1 = 11

## Step 4: Mean Squares

MS Treatments = SS Treatments / df Treatments = 184.25 / 3 ≈ **61.4167**  
MS Error = SS Error / df Error = 6 / 6 = **1**

## Step 5: F Statistic

F = MS Treatments / MS Error = 61.4167 / 1 = **61.42**

## ANOVA Table

| Source          | SS      | df | MS       | F      |
|-----------------|---------|----|----------|--------|
| Subjects        | 1662    | 2  |          |        |
| Treatments      | 184.25  | 3  | 61.4167  | 61.42  |
| Error           | 6       | 6  | 1        |        |
| Within          | 190.25  | 9  |          |        |
| Total           | 1852.25 | 11 |          |        |

Critical F(3,6) at α=0.05 ≈ 4.76. Since 61.42 > 4.76, the effect of weeks is significant.