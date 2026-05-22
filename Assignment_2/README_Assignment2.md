# Multilevel Modeling of Educational Performance: Analyzing INVALSI Standardized Math Scores

## Project Overview
This project applies **Multilevel (Hierarchical) Linear Modeling (HLM)** to analyze the mathematics performance of fifth-grade students in Italy using the national **INVALSI (2023-2024)** assessment dataset. 

In educational research, data is inherently hierarchical: students (Level 1) are nested within classes or schools (Level 2). Standard ordinary least squares (OLS) regression violates the assumption of independent observations, leading to underestimated standard errors and inflated Type I error rates. This analysis implements mixed-effects models to partition the variance across different levels of the hierarchy, properly accounting for cluster-level correlations while identifying key student-level and school-level determinants of academic success.

---

## Methodological Framework & Model Progression

The statistical analysis follows a rigorous step-by-step model building progression to ensure robust inference and justification of model complexity:

### 1. The Baseline: Unconditional Null Model (Empty Model)
Before introducing any predictors, an empty model with only a random intercept is fitted to determine if a multilevel structure is statistically necessary.
* **Mathematical Formulation:**
  $$Y_{ij} = \beta_0 + u_{0j} + \varepsilon_{ij}$$
  Where $\beta_0$ is the grand mean, $u_{0j} \sim N(0, \sigma^2_{u0})$ is the random effect for school/class $j$, and $\varepsilon_{ij} \sim N(0, \sigma^2_\varepsilon)$ is the residual student-level error.
* **Intraclass Correlation Coefficient (ICC):**
  $$ICC = \frac{\sigma^2_{u0}}{\sigma^2_{u0} + \sigma^2_\varepsilon}$$
  The ICC quantifies the proportion of total variance in math scores that resides between classes/schools. A high ICC justifies the rejection of standard OLS regression in favor of mixed modeling.

### 2. Model 1: Random Intercept with Level-1 (Student-Level) Predictors
Individual student characteristics are added to the model as fixed effects, allowing the baseline performance to vary across schools while keeping the effect of the predictors constant.
* **Predictors Included:** Gender, origin (immigrant status), nursery/kindergarten attendance, and individual socio-economic index (`ESCS_student`).

### 3. Model 2: Random Intercept with Level-2 (Contextual & Environmental) Predictors
To explain the between-group variance ($\sigma^2_{u0}$), cluster-level variables and aggregated contextual metrics are introduced.
* **Predictors Included:** Aggregate class socio-economic status (`ESCS_class`) and geographic macro-regions (`GeoArea_5`). This stage tests whether school-level environments exert an independent effect on student achievement above and beyond individual backgrounds.

### 4. Model 3: Random Slope Model (Cross-Level Interaction)
This model tests whether the effect of an individual-level predictor (e.g., student socio-economic background) varies across different schools.
* **Mathematical Formulation:**
  $$Y_{ij} = \beta_{0j} + \beta_{1j}(ESCS\_student_{ij}) + \varepsilon_{ij}$$
  $$\beta_{0j} = \beta_0 + u_{0j}$$
  $$\beta_{1j} = \beta_1 + u_{1j}$$
  Where $u_{1j}$ allows the slope of socio-economic status to vary randomly across schools, exploring whether some school environments minimize or exacerbate educational inequality.

---

## Variable Specification & Selection Justification

### Target Variable: `WLE_MATH_200`
Instead of raw percentage scores, the analysis utilizes the **Weighted Likelihood Estimate (WLE)** scaled to a mean of 200. WLE scores are derived from Item Response Theory (IRT), adjusting for question difficulty and discrimination parameters. This yields a continuous, psychometrically valid, and approximately normally distributed outcome variable ideal for linear mixed-effects modeling.

### Predictor Taxonomy:
* **Level-1 (Student Level):**
  * `gender`: Binary indicator (Male/Female).
  * `origin`: Categorical (Native, First-Generation, Second-Generation Immigrant).
  * `nursery_attendance` / `kindergarten_attendance`: Binary indicators evaluating early childhood education impact.
  * `ESCS_student`: Economic, Social, and Cultural Status index centered at the individual level.
* **Level-2 (Class/School Level):**
  * `ESCS_class`: The mean socio-economic status of the class, capturing the "peer effect" or contextual privilege.
  * `GeoArea_5`: Categorical variable capturing macro-regional disparities in the Italian educational landscape (North-West, North-East, Center, South, South-Islands).

---

## Implementation & Diagnostics
* **Estimation Method:** Maximum Likelihood (ML) for comparing models with different fixed effects using Likelihood Ratio Tests (LRT); Restricted Maximum Likelihood (REML) for final variance component parameter estimations.
* **Model Selection Criteria:** Akaike Information Criterion (AIC), Bayesian Information Criterion (BIC), and Deviances ($-2 \log L$).
* **Software Stack:** Python (`statsmodels.regression.mixed_linear_model.MixedLM`, `pandas`, `numpy`, `seaborn`, `matplotlib`).

## File Inventory
* `assignment2_analysis.ipynb`: Documented Jupyter notebook containing data preprocessing, missing data analysis, iterative model building, parameter estimations, and residual diagnostics.
* `Instructions_2.pdf`: Official guidelines and structural constraints provided by the instructor.
* `INVALSI_data_MAT_2324 - Foglio 1.csv`: The primary hierarchical dataset.
* `MAT_05-2023-24_datadescription.xlsx - Foglio 1.csv`: Metadata and variable mapping documentation.
