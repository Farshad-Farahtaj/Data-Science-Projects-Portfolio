# Assignment 1: Statistical Models for Categorical Data

## Files in this Directory

- **assignment1_analysis.ipynb** - Complete Jupyter notebook with all three exercises
- **asthma.csv** - Dataset for Exercise 3 (provided)
- **drug_consumption.data** - Will be downloaded automatically when you run the notebook
- **diagnosis.data** - Will be downloaded automatically when you run the notebook
- **README.md** - This file

## How to Run

### Prerequisites

Install required Python packages:

```bash
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn scipy
```

### Running the Notebook

1. Open `assignment1_analysis.ipynb` in Jupyter Notebook, JupyterLab, or VS Code
2. Run all cells sequentially from top to bottom
3. The notebook will automatically download the required datasets for Exercises 1 and 2
4. All visualizations and results will be displayed inline

### Notebook Structure

**Exercise 3: Modeling Count Data (Asthma)**
- Section 3.1: Data Loading and Exploration
- Section 3.2: Poisson Regression Model
- Section 3.3: Overdispersion Diagnostics
- Section 3.4: Alternative Models (Negative Binomial, Quasi-Poisson)
- Section 3.5: Model Comparison and Selection

**Exercise 1: Logistic Modeling (Drug Consumption)**
- Section 1.1: Data Loading and Preprocessing
- Section 1.2: Exploratory Data Analysis
- Section 1.3: Binary Logistic Regression - Alcohol
- Section 1.4: Binary Logistic Regression - Cannabis
- Section 1.5: Multinomial Logistic Regression - Alcohol
- Section 1.6: Multinomial Logistic Regression - Cannabis
- Section 1.7: Model Comparison and Summary

**Exercise 2: Log-Linear and Logistic Models (Acute Inflammations)**
- Section 2.1: Data Loading and Preparation
- Section 2.2: Log-Linear Model Analysis
- Section 2.3: Logistic Regression Model
- Section 2.4: Equivalence Between Log-Linear and Logistic Models

## Expected Output

The notebook will produce:
- Descriptive statistics and data summaries
- Multiple statistical model summaries
- Visualizations (histograms, scatter plots, ROC curves, confusion matrices, etc.)
- Model comparison tables
- Interpretation of coefficients and statistical tests

## Notes

- **Individual/Group Work**: Remember to add a note in your submission folder specifying whether this was completed individually or as part of a group, and if in a group, list all members.
- **Report**: Create a PDF report summarizing your findings from all three exercises.
- **Datasets**: The UCI datasets will be downloaded automatically. If download fails, you can manually download from:
  - Drug Consumption: https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29
  - Acute Inflammations: https://archive.ics.uci.edu/ml/datasets/Acute+Inflammations

## Submission Checklist

Before submitting, ensure your folder contains:
- [ ] assignment1_report.pdf (PDF report with all three exercises)
- [ ] assignment1_analysis.ipynb (this notebook)
- [ ] work_note.txt (stating individual/group work and member names)
- [ ] Any downloaded datasets

## Contact

If you have questions about the analysis or code, please reach out to your instructor or teaching assistant.

---
Good luck with your assignment!
