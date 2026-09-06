# Prostate Cancer Biochemical Recurrence Prediction

## Project Overview

This project uses machine learning to predict **biochemical recurrence** in prostate cancer patients.

The project includes data cleaning, preprocessing, exploratory analysis, feature encoding, model training, model evaluation, and feature importance analysis.

Two classification models were tested:

* Logistic Regression
* Random Forest

The models were compared using Accuracy, Precision, Recall, F1 Score, and ROC-AUC.

## Project Goal

The main goal is to build a machine learning model that can classify patients based on the target variable:

* **No Recurrence**
* **Recurrence**

This project is an educational machine learning project and is not intended for medical diagnosis or clinical use.

## Dataset

The original dataset contains:

* **505 rows**
* **69 columns**

After removing metadata and records without the target value, the final dataset contains:

* **431 patients**
* **47 initial features**

The target variable is:

`Biochemical Recurrence Indicator`

The target values were converted to:

* `NO` → 0
* `YES` → 1

## Data Preprocessing

The following preprocessing steps were used:

1. Load the prostate dataset from a TSV file.
2. Remove metadata rows.
3. Replace missing-value labels with `NaN`.
4. Remove records without the target value.
5. Convert the target variable to binary values.
6. Convert selected columns to numeric values.
7. Remove unused columns.
8. Apply one-hot encoding to categorical features.
9. Convert boolean values to numeric values.
10. Fill missing values using median imputation.
11. Split the data into training and testing sets.
12. Standardize features for Logistic Regression.

After preprocessing and encoding, the dataset contained **97 features**.

## Machine Learning Models

### Logistic Regression

Logistic Regression was used as a baseline classification model.

Results:

* Accuracy: **87.36%**
* Precision: **54.55%**
* Recall: **50.00%**
* F1 Score: **52.17%**
* ROC-AUC: **0.888**

### Random Forest

Random Forest was used as a tree-based classification model with **200 trees**.

Results:

* Accuracy: **91.95%**
* Precision: **100.00%**
* Recall: **41.67%**
* F1 Score: **58.82%**
* ROC-AUC: **0.989**

## Model Comparison

| Model               |   Accuracy |   Precision | Recall |   F1 Score |   ROC-AUC |
| ------------------- | ---------: | ----------: | -----: | ---------: | --------: |
| Logistic Regression |     87.36% |      54.55% | 50.00% |     52.17% |     0.888 |
| **Random Forest**   | **91.95%** | **100.00%** | 41.67% | **58.82%** | **0.989** |

## Best Model

The **Random Forest** model achieved the highest ROC-AUC score:

**ROC-AUC: 0.989**

It also achieved the highest accuracy and F1 score among the tested models.

However, the Recall for the Recurrence class was **41.67%**. This means the model did not identify all recurrence cases in the test set.

Because the dataset contains fewer recurrence cases than no-recurrence cases, Accuracy alone should not be used to judge the model.

## Visualizations

The notebook includes several visualizations:

* Biochemical Recurrence Distribution
* Confusion Matrix
* ROC Curve
* Top 15 Important Features

The feature importance analysis shows which features were most important for the Random Forest model.

## Project Structure

```text
predict_prostat/
│
├── main.ipynb
├── prostat.tsv
└── README.md
```

## Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Jupyter Notebook

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/OmidDevAi/predict_prostat.git
cd predict_prostat
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the environment

Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 4. Install the required packages

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

### 5. Open the notebook

```bash
jupyter notebook
```

Then open:

```text
main.ipynb
```

## Limitations

This project has several limitations:

* The dataset is relatively small.
* The recurrence class contains fewer samples than the no-recurrence class.
* Only two machine learning models were tested.
* The evaluation uses a single train-test split.
* No external clinical validation was performed.
* The model is not designed for medical diagnosis.

## Future Improvements

Possible future improvements include:

* Test additional classification algorithms.
* Use stratified cross-validation.
* Handle class imbalance with appropriate methods.
* Perform hyperparameter tuning.
* Compare additional evaluation metrics.
* Improve feature engineering.
* Add model explainability.
* Create a simple prediction application.

## Key Takeaway

This project demonstrates a complete machine learning classification workflow using a prostate cancer dataset.

The **Random Forest** model achieved the best ROC-AUC score of **0.989** among the tested models.

The project also shows why multiple evaluation metrics are important, especially when the target classes are not balanced.

## Author

**Omid Rezapour**

GitHub: [OmidDevAi](https://github.com/OmidDevAi)
