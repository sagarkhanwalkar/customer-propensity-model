Customer Propensity Model

A machine-learning propensity model for identifying customers with a higher likelihood of subscribing to a marketing offer.

Project Overview

This project demonstrates an end-to-end customer propensity modeling workflow using Python and XGBoost, including exploratory data analysis, model benchmarking, hyperparameter tuning, and business-oriented targeting analysis.

The dataset contains 45,211 customer records, with an overall subscription rate of 11.7%.

Key Results
Metric	Result
Final ROC-AUC	0.7579
Final PR-AUC	0.4035
Top 10% Precision	44.69%
Top 10% Recall	38.19%
Top 10% Lift	3.82×

The final XGBoost model was evaluated on a held-out test set. Customers were also ranked by predicted propensity to evaluate how effectively the model concentrated observed subscribers within the highest-ranked segments.

Targeting Results
Customers Targeted	Precision	Recall	Lift
Top 10%	44.69%	38.19%	3.82×
Top 20%	30.86%	52.74%	2.64×
Top 30%	24.96%	63.99%	2.13×
Top 40%	21.43%	73.25%	1.83×
Top 50%	18.51%	79.11%	1.58×
Modeling Approach

The project evaluates:

Logistic Regression as a baseline

Random Forest

XGBoost

Cross-validated XGBoost hyperparameter tuning

Precision, recall, F1, ROC-AUC, and PR-AUC

Top-k targeting and cumulative lift

The final model uses customer characteristics and prior campaign behavior, including age, job, education, balance, housing, loan status, contact information, and previous campaign outcomes.

The duration feature was intentionally excluded because it represents the duration of the current marketing interaction and would not be available when generating a pre-contact propensity score.

Business Perspective

The model is evaluated as a ranking system, rather than relying solely on a fixed classification threshold.

For example, targeting the top 10% of customers produced:

44.69% observed subscription rate

38.19% of all observed subscribers captured

3.82× lift relative to the overall subscription rate

The appropriate targeting level would depend on campaign capacity, contact costs, customer value, and conversion economics.

Lift represents an association between model-ranked propensity and observed outcomes and should not be interpreted as a causal increase in conversion.

Repository Structure
customer-propensity-model/
│
├── data/
│   └── .gitkeep
│
├── notebooks/
│   ├── 01_eda.ipynb
│   └── 02_modeling.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore

Tools & Technologies

Python · Pandas · NumPy · Scikit-learn · XGBoost · PySpark · SQL · Jupyter · AWS

Future Improvements

Temporal validation using reliable future campaign dates

Probability calibration

Cost-sensitive targeting based on campaign economics

SHAP-based customer-level model explanations

Model drift and performance monitoring

Production scoring pipeline using AWS or Databricks

Author

Senior Data Scientist specializing in machine learning, predictive modeling, customer analytics, and large-scale data science.
