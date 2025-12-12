# Nested ANOVA Calculation by Hand

## Data Setup
- **Factors**: Gym (top-level factor, a = 2 levels: G1, G2). Athlete (nested within Gym, b = 3 levels per gym).
- **Observations**: n = 1 per athlete (single Bench_1RM value).
- **Data Table**:

| Gym | Athlete | Bench_1RM |
|-----|---------|-----------|
| G1  | A1      | 110       |
| G1  | A2      | 115       |
| G1  | A3      | 120       |
| G2  | A4      | 125       |
| G2  | A5      | 130       |
| G2  | A6      | 128       |

- Total observations: N = 6.

## Step 1: Calculate Means
- Gym means (ȳ_i•):
  - G1: (110 + 115 + 120) / 3 = 345 / 3 = 115
  - G2: (125 + 130 + 128) / 3 = 383 / 3 ≈ 127.6667
- Grand mean (ȳ••): (345 + 383) / 6 = 728 / 6 ≈ 121.3333

## Step 2: Calculate Sum of Squares (SS)

- **SS_Total** = Σ(y_{ij} - ȳ••)²  
  Sum of all y² = 110² + 115² + 120² + 125² + 130² + 128²  
  = 12100 + 13225 + 14400 + 15625 + 16900 + 16384 = 88634  
  Correction factor = (728)² / 6 = 529984 / 6 ≈ 88330.6667  
  SS_Total = 88634 - 88330.6667 ≈ 303.3333

- **SS_Gym** (between gyms) = b × Σ(ȳ_i• - ȳ••)², where b = 3  
  (115 - 121.3333)² ≈ 40.1111  
  (127.6667 - 121.3333)² ≈ 40.1111  
  SS_Gym = 3 × (40.1111 + 40.1111) = 3 × 80.2222 ≈ 240.6667

- **SS_Athlete(Gym)** = SS_Total - SS_Gym ≈ 303.3333 - 240.6667 ≈ 62.6667  
  (Alternative calculation within each gym):  
  - G1: (110-115)² + (115-115)² + (120-115)² = 25 + 0 + 25 = 50  
  - G2: (125-127.6667)² + (130-127.6667)² + (128-127.6667)² ≈ 7.1111 + 5.4444 + 0.1111 ≈ 12.6667  
  Total SS_Athlete(Gym) ≈ 62.6667

## Step 3: Degrees of Freedom (df)
- df_Gym = a - 1 = 2 - 1 = 1
- df_Athlete(Gym) = a(b - 1) = 2 × (3 - 1) = 4
- df_Total = N - 1 = 6 - 1 = 5

## Step 4: Mean Squares (MS)
- MS_Gym = SS_Gym / df_Gym ≈ 240.6667 / 1 = 240.6667
- MS_Athlete(Gym) = SS_Athlete / df_Athlete ≈ 62.6667 / 4 ≈ 15.6667

## Step 5: F-Statistic
- F = MS_Gym / MS_Athlete(Gym) ≈ 240.6667 / 15.6667 ≈ 15.36
- Critical F(1,4) at α = 0.05 ≈ 7.71 → significant Gym effect (p < 0.05)

## ANOVA Table

| Source            | df | SS       | MS       | F     |
|-------------------|----|----------|----------|-------|
| Gym               | 1  | 240.67   | 240.67   | 15.36 |
| Athlete (within Gym) | 4  | 62.67    | 15.67    |       |
| Total             | 5  | 303.33   |          |       |
