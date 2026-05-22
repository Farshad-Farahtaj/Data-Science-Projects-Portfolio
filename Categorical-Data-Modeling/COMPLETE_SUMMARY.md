# Statistical Analysis Summary

If you don't want to dig through the code cells in the Jupyter Notebook, here is the bottom line of the statistical methodologies and findings for each exercise.

### Exercise 1: Drug Consumption (Logistic Modeling)
For this section, I modeled the likelihood of a person consuming certain drugs based on their personality scores (like neuroticism or sensation-seeking) and demographics.
* **The Process:** I fitted a logistic regression model. Instead of just looking at raw classification accuracy, I focused on the odds ratios and coefficient significance.
* **Takeaway:** The model clearly showed that specific psychological profiles significantly shift the log-odds of drug consumption. I also checked for multicollinearity among the psychological traits to ensure the coefficients weren't artificially inflated or unstable.

### Exercise 2: Acute Inflammations (Log-Linear Models)
Here, the dataset consisted of categorical symptoms (yes/no for nausea, lumbar pain, etc.) and categorical diagnoses.
* **The Process:** Standard regression assumes a clear dependent variable. However, I used Log-Linear models to analyze the multi-way contingency tables. This allowed me to model the joint distribution of the symptoms and see how they interact with each other structurally.
* **Takeaway:** I identified strong conditional dependencies between specific symptoms. Once the interaction network was statistically mapped out, converting the relevant relationships into a logistic framework made predicting the actual disease extremely straightforward.

### Exercise 3: Asthma Attacks (Handling Overdispersion)
This was the most technically critical part of the Categorical-Data-Modeling. I needed to model the *count* of asthma attacks for patients.
* **The Problem:** The default GLM for count data is the Poisson distribution. However, Poisson strictly assumes that the mean equals the variance. When I evaluated the Poisson model, the residual deviance was vastly larger than the degrees of freedom—a massive red flag for overdispersion.
* **The Fix:** Because the data was overdispersed, the Poisson standard errors were artificially tiny, making irrelevant variables look "statistically significant." I corrected this by switching the underlying distribution to a Negative Binomial model.
* **The Result:** The Negative Binomial model absorbed the excess variance beautifully. The coefficients remained somewhat stable, but the standard errors expanded to realistic levels, giving us a mathematically honest and robust model.
