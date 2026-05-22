# Categorical Data & Generalized Linear Models (GLMs)

Welcome to my repository for Assignment 1 of the Advanced Statistical Learning and Modeling (Module B) course. 

## What is this project?
Real-world data is rarely perfectly continuous or normally distributed. This project focuses entirely on Generalized Linear Models (GLMs) tailored for categorical, binary, and count data. The goal here wasn't just to throw machine learning algorithms at a dataset, but to deeply understand the statistical properties, probability distributions, and structural relationships within the data.

The analysis is broken down into three distinct statistical exercises:

1. **Exercise 1: Drug Consumption (Logistic Regression)**
   Modeled the probability of drug usage based on psychological traits and demographic features. Analyzed odds ratios to interpret the true impact of personality metrics on behavior.
   
2. **Exercise 2: Acute Inflammations (Log-Linear Models)**
   Dealt with multi-way contingency tables. Instead of a simple input-output model, I used Log-Linear modeling to map the complex interaction structures and conditional dependencies between various medical symptoms.

3. **Exercise 3: Asthma Count Data (Overdispersion Handling)**
   Modeled the frequency of asthma attacks. Started with a standard Poisson GLM but detected severe overdispersion (variance significantly exceeding the mean). I then corrected this by fitting a Negative Binomial model to produce valid standard errors and robust inferences.

## Repository Structure
* `assignment1_analysis.ipynb`: The main Jupyter Notebook containing all the Python code, statistical tests, model diagnostics, and visualizations.
* `COMPLETE_SUMMARY.md`: A plain-English breakdown of the statistical findings and methodologies.
* `Instructions.pdf`: The official assignment guidelines.
* Datasets: `asthma.csv`, `drug_consumption.data`

## Tech Stack
* Python: `statsmodels` (for rigorous statistical modeling and inference), `scikit-learn`, `pandas`, `seaborn`, `matplotlib`.
