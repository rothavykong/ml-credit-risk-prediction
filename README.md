{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "ab521a60-ed7b-4a76-ae6c-18fc020cc9a8",
   "metadata": {},
   "source": [
    "# Data Setup\n",
    "\n",
    "Make sure that you have these files downloaded\n",
    "\n",
    "- application_train.csv\n",
    "- bureau.csv\n",
    "- previous_application.csv\n",
    "- installments_payments.csv\n",
    "\n",
    "The following Python libraries are required to run the pipeline:,\n",
    "\n",
    "- Pandas: data analysis and manipulation\n",
    "- Matplotlib: data visualization\n",
    "- Seaborn: statistical data visualization\n",
    "- Scikit-learn: machine learning utilities including encoding categorical variables, handling missing data, and model training\n",
    "\n",
    "If you don't already have these installed, run this:\n",
    "- !pip install pandas \n",
    "- !pip install matplotlib \n",
    "- !pip install seaborn \n",
    "- !pip install scikit-learn"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "e76604d8-6edb-4b2e-8310-871647c11b6c",
   "metadata": {},
   "source": [
    "# Running the Report\n",
    "Open the Project_Report in jupyter notebook and run it top to bottom\n",
    "\n",
    "Here are the main sections in this report:\n",
    "- EDA — explores class imbalance, missing values, and correlations\n",
    "- Feature Engineering — merges all four tables and creates aggregated features\n",
    "- Preprocessing — imputes missing values, clips outliers, encodes categoricals, scales features\n",
    "- Modeling — trains logistic regression with stratified cross-validation\n",
    "- Evaluation — outputs recall, AUC, confusion matrix, and top feature coefficients"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "5f508e54-6731-4d97-b00f-c926850615ed",
   "metadata": {},
   "source": [
    "# Expected Outcome\n",
    "\n",
    "These are the expected outputs from this report:\n",
    "\n",
    "- Cross-validation metric scores printed to console\n",
    "- Confusion matrix\n",
    "- ROC curve\n",
    "- coefficient plots rendered inline"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python [conda env:base] *",
   "language": "python",
   "name": "conda-base-py"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.13.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
