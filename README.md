# Data Setup

Make sure that you have these files downloaded:

- application_train.csv
- bureau.csv
- previous_application.csv
- installments_payments.csv

The following Python libraries are required to run the pipeline:

- Pandas: data analysis and manipulation
- Matplotlib: data visualization
- Seaborn: statistical data visualization
- Scikit-learn: machine learning utilities including encoding categorical variables, handling missing data, and model training

If you don't already have these installed, run this:

    pip install pandas matplotlib seaborn scikit-learn

# Running the Report

Open Project_Report in Jupyter Notebook and run it top to bottom.

Main sections:
- EDA — explores class imbalance, missing values, and correlations
- Feature Engineering — merges all four tables and creates aggregated features
- Preprocessing — imputes missing values, clips outliers, encodes categoricals, scales features
- Modeling — trains logistic regression with stratified cross-validation
- Evaluation — outputs recall, AUC, confusion matrix, and top feature coefficients

# Expected Outcome

These are the expected outputs from this report:

- Cross-validation metric scores printed to console
- Confusion matrix
- ROC curve
- Coefficient plots rendered inline
