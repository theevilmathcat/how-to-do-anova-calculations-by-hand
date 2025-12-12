# Mixed ANOVA By Hand: Example Data

## Data Table

| Lifter | Program (Between-subjects) | Week 1 (Within) | Week 2 | Week 3 |
|--------|----------------------------|-----------------|--------|--------|
| 1      | A                          | 80              | 82     | 85     |
| 2      | A                          | 75              | 78     | 80     |
| 3      | B                          | 80              | 85     | 90     |
| 4      | B                          | 70              | 76     | 82     |

All scores (in order): 80, 82, 85, 75, 78, 80, 80, 85, 90, 70, 76, 82  
N = 12 observations total  
a = 2 (programs: A, B)  
b = 3 (weeks)  
n = 2 (lifters per program)

## Step 1: Compute Key Means

- Subject (lifter) means:  
  Lifter 1: (80+82+85)/3 = 82.333  
  Lifter 2: (75+78+80)/3 = 77.667  
  Lifter 3: (80+85+90)/3 = 85.000  
  Lifter 4: (70+76+82)/3 = 76.000  

- Program means (average across lifters and weeks):  
  Program A: (82.333 + 77.667)/2 = 80.000  
  Program B: (85.000 + 76.000)/2 = 80.500  

- Week means (average across lifters):  
  Week 1: (80+75+80+70)/4 = 76.250  
  Week 2: (82+78+85+76)/4 = 80.250  
  Week 3: (85+80+90+82)/4 = 84.250  

- Grand mean: (76.250 + 80.250 + 84.250)/3 = 80.250  
  (or total sum 963 / 12 = 80.250)

## Step 2: Compute Sums of Squares (SS)

1. **SS Program** (between-subjects factor)  
   SS_Program = b × n × Σ (Program_mean - Grand_mean)²  
   = 3 × 2 × [(80.000 - 80.250)² + (80.500 - 80.250)²]  
   = 6 × (0.0625 + 0.0625) = 6 × 0.125 = **0.750**

2. **SS Subjects within groups** (error for Program)  
   SS_Subj_within = b × Σ (Subject_mean - Program_mean)² (within each group)  
   Group A: (82.333 - 80)^² + (77.667 - 80)^² = 5.444 + 5.444 = 10.889  
   Group B: (85 - 80.5)² + (76 - 80.5)² = 20.25 + 20.25 = 40.5  
   Total: 10.889 + 40.5 = 51.389  
   × 3 = **154.167**

3. **SS Week** (within-subjects factor)  
   SS_Week = a × n × Σ (Week_mean - Grand_mean)²  
   = 4 × [(76.25 - 80.25)² + (80.25 - 80.25)² + (84.25 - 80.25)²]  
   = 4 × (16 + 0 + 16) = 4 × 32 = **128.000**

4. **SS Program × Week** (interaction)  
   First, Program × Week cell means (same as program row means per week):  
   |        | Week 1 | Week 2 | Week 3 |
   |--------|--------|--------|--------|
   | A      | 77.5   | 80.0   | 82.5   |
   | B      | 75.0   | 80.5   | 86.0   |

   SS_Interaction = n × Σ (Cell_mean - Program_mean - Week_mean + Grand_mean)² (over all 6 cells)  
   Deviations:  
   A1: 77.5 - 80 - 76.25 + 80.25 = +1.5  
   A2: 80 - 80 - 80.25 + 80.25 = 0  
   A3: 82.5 - 80 - 84.25 + 80.25 = -1.5  
   B1: 75 - 80.5 - 76.25 + 80.25 = -1.5  
   B2: 80.5 - 80.5 - 80.25 + 80.25 = +0.25  
   B3: 86 - 80.5 - 84.25 + 80.25 = +1.5  

   Squared: 2.25, 0, 2.25, 2.25, 0.0625, 2.25  
   Sum squares = 9.0625  
   × n=2 = **18.125**

5. **SS Total**  
   SS_Total = Σ (each score - Grand_mean)² = **301.750**  
   (Verify: SS_Program + SS_Subj_within + SS_Week + SS_Interaction + SS_Residual should equal this)

6. **SS Residual** (Week × Subjects within groups)  
   SS_Residual = SS_Total - SS_Program - SS_Subj_within - SS_Week - SS_Interaction  
   = 301.750 - 0.750 - 154.167 - 128.000 - 18.125 = **0.708**

## Step 3: Degrees of Freedom (df)

- df_Program = a - 1 = 1  
- df_Subj_within = a(n - 1) = 2  
- df_Week = b - 1 = 2  
- df_Interaction = (a - 1)(b - 1) = 2  
- df_Residual = (b - 1) × a(n - 1) = 2 × 2 = 4  

## Step 4: Mean Squares (MS) and F Ratios

| Source              | SS      | df | MS         | F       | Denominator MS    |
|---------------------|---------|----|------------|---------|-------------------|
| Program (between)   | 0.750   | 1  | 0.750      | 0.01    | MS_Subj_within    |
| Subjects within     | 154.167 | 2  | 77.083     | -       | -                 |
| Week (within)       | 128.000 | 2  | 64.000     | 361.50  | MS_Residual       |
| Program × Week      | 18.125  | 2  | 9.0625     | 51.22   | MS_Residual       |
| Residual            | 0.708   | 4  | 0.177      | -       | -                 |

- F_Program = 0.750 / 77.083 ≈ 0.01 (n.s.)  
- F_Week = 64.000 / 0.177 ≈ 361.50 (p < .001)  
- F_Interaction = 9.0625 / 0.177 ≈ 51.22 (p < .001)

## Summary Table

| Source                  | SS      | df | MS      | F      |
|-------------------------|---------|----|---------|--------|
| Between subjects:       |         |    |         |        |
| Program                 | 0.750   | 1  | 0.750   | 0.01   |
| Subjects within groups  | 154.167 | 2  | 77.083  |        |
| Within subjects:        |         |    |         |        |
| Week                    | 128.000 | 2  | 64.000  | 361.50 |
| Program × Week          | 18.125  | 2  | 9.0625  | 51.22  |
| Residual                | 0.708   | 4  | 0.177   |        |
| Total                   | 301.750 | 11 |         |        |

Interpretation (brief): Significant main effect of Week and significant Program × Week interaction. No main effect of Program.
