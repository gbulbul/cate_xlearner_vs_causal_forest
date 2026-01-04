## Outcome Definition

### Primary Outcome

The primary outcome is the **diabetes progression score**, a continuous numeric variable provided directly by the dataset.

- The progression score summarizes disease severity and progression.
- Higher values indicate **worse disease progression**.
- The outcome is **observed for all individuals** after treatment assignment.

> **Note:**  
> The outcome unit is the dataset’s native progression score (dimensionless).  
> No rescaling or unit transformation was applied in this analysis.

Formally, the observed outcome for individual *i* is defined as:
$$
Y_i \in \mathbb{R}
$$

---

## Treatment Definition

Treatment assignment is **deterministic** and based on a BMI threshold.

- **Covariate used:** BMI  
- **Median BMI value:**  
\[
\text{Median} = 0.0017505
\]

- **Treatment group (High BMI):**
\[
T_i = 1 \quad \text{if } \text{BMI}_i > 0.0017505
\]

- **Control group (Low BMI):**
\[
T_i = 0 \quad \text{if } \text{BMI}_i \le 0.0017505
\]

This is **not a randomized assignment**.  
The study therefore uses **observational causal inference methods**.

---

## Estimands of Interest

We estimate **Conditional Average Treatment Effects (CATE)**:
\[
\text{CATE}(X) = \mathbb{E}[Y(1) - Y(0) \mid X]
\]

and subgroup‑specific **Average Treatment Effects (ATEs)** by BMI group:
\[
\widehat{ATE}_g = \frac{1}{n_g} \sum_{i: G_i=g} \hat{\tau}_i
\]

where:
- \( g = 0 \): Low BMI group  
- \( g = 1 \): High BMI group  

---

## Key Outcome Results (Subgroup Comparison)

### X‑Learner Results

- **Low BMI (Control):** CATE ≈ 28.72  
- **High BMI (Treatment):** CATE ≈ 30.52  

\[
\text{CATE}_{High} - \text{CATE}_{Low} \approx +1.8
\]

➡ High‑BMI individuals experience a **slightly larger treatment effect**  
➡ Indicates **mild treatment effect heterogeneity**

---

### Causal Forest Results

- **Low BMI:** CATE ≈ 62.30  
- **High BMI:** CATE ≈ 50.79  

➡ Suggests **stronger heterogeneity**, with larger effects among low‑BMI individuals  
➡ Causal Forest is more sensitive to subgroup variation by design

---

## Visualization

### Subgroup Treatment Effect Comparison

The following figure compares subgroup‑specific treatment effects estimated by the X‑Learner and Causal Forest.

