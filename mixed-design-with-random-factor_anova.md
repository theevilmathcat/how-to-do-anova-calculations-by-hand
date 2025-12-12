# Mixed ANOVA by Hand: One Fixed Factor (Program), One Random Nested Factor (Coach(Program))

Data (two athletes per coach):

| Program | Coach | Athlete | Squat_1RM |
|---------|-------|---------|-----------|
| A       | C1    | 1       | 150       |
| A       | C1    | 2       | 152       |
| A       | C2    | 3       | 155       |
| A       | C2    | 4       | 157       |
| B       | C3    | 5       | 160       |
| B       | C3    | 6       | 162       |
| B       | C4    | 7       | 158       |
| B       | C4    | 8       | 161       |

### Step 1: Compute Means

- Grand mean (GM): 156.875
- Program A mean: 153.5
- Program B mean: 160.25

- Coach means:
  - A-C1: 151
  - A-C2: 156
  - B-C3: 161
  - B-C4: 159.5

### Step 2: Sum of Squares

**SS Total** = Σ(all scores - GM)² = 128.875

**SS Program (fixed factor A)**  
= (number of athletes per program) × Σ(program mean - GM)²  
= 4 × [(153.5 - 156.875)² + (160.25 - 156.875)²] = 91.125

**SS Coach(Program) (random nested factor)**  
For each program:  
Program A: 2 × [(151 - 153.5)² + (156 - 153.5)²] = 2 × (6.25 + 6.25) = 25  
Program B: 2 × [(161 - 160.25)² + (159.5 - 160.25)²] = 2 × (0.5625 + 0.5625) = 2.25  
Total SS Coach(Program) = 25 + 2.25 = 27.25

**SS Error** (within coaches) = Σ(all scores - own coach mean)² = 10.5  
(Details per coach: each pair deviates by ±1 or ±1.5, squared sum per coach = 2 or 4.5, total 10.5)

Check: 91.125 + 27.25 + 10.5 = 128.875 ✓

### Step 3: Degrees of Freedom

- df Program = a - 1 = 2 - 1 = 1
- df Coach(Program) = a × (coaches per program - 1) = 2 × (2 - 1) = 2
- df Error = total coaches × (athletes per coach - 1) = 4 × (2 - 1) = 4
- df Total = N - 1 = 8 - 1 = 7

### Step 4: Mean Squares

- MS Program = SS Program / df Program = 91.125 / 1 = 91.125
- MS Coach(Program) = 27.25 / 2 = 13.625
- MS Error = 10.5 / 4 = 2.625

### Step 5: F-Statistic for Program (Fixed Effect)

In mixed ANOVA with Coach random nested in Program, test Program using MS Coach(Program) as denominator (quasi-F or approximate).  

F = MS Program / MS Coach(Program) = 91.125 / 13.625 ≈ 6.69  

(df = 1, 2)

### ANOVA Table

| Source              | SS      | df | MS      | F     |
|---------------------|---------|----|---------|-------|
| Program (fixed)     | 91.125 | 1  | 91.125 | 6.69  |
| Coach(Program) (random) | 27.25  | 2  | 13.625 |       |
| Error (within coaches) | 10.5   | 4  | 2.625  |       |
| Total               | 128.875| 7  |         |       |

(Note: Error term can also be used to test Coach(Program) if needed, but primary interest is usually the fixed factor Program.)
