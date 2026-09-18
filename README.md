# Prostate Cancer Biochemical Recurrence Prediction

## Project Overview

This project uses machine learning to explore prediction of biochemical recurrence in prostate cancer patients.

The workflow covers data cleaning, preprocessing, exploratory analysis, feature encoding, model training, model evaluation, and feature importance analysis.

Two classification models were evaluated:

- Logistic Regression
- Random Forest

The models were compared using Accuracy, Precision, Recall, F1 Score, and ROC-AUC.

> **Note:** This is an educational machine learning project. It is not intended for medical diagnosis or clinical use.

## Dataset

The original dataset contains:

- 505 rows
- 69 columns

After removing metadata and records without the target value, the working dataset contains:

- 431 patients
- 47 initial features

The target variable is:

`Biochemical Recurrence Indicator`

Target values were converted to:

- `NO` → 0
- `YES` → 1

## Data Preprocessing

The notebook follows these main steps:

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

After preprocessing and encoding, the dataset contains 97 features.

## Models and Results

### Logistic Regression

- Accuracy: **87.36%**
- Precision: **54.55%**
- Recall: **50.00%**
- F1 Score: **52.17%**
- ROC-AUC: **0.888**

### Random Forest

A Random Forest model with 200 trees was also evaluated.

- Accuracy: **91.95%**
- Precision: **100.00%**
- Recall: **41.67%**
- F1 Score: **58.82%**
- ROC-AUC: **0.989**

### Comparison

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 87.36% | 54.55% | 50.00% | 52.17% | 0.888 |
| Random Forest | 91.95% | 100.00% | 41.67% | 58.82% | 0.989 |

The reported test results show that Random Forest produced a higher ROC-AUC, accuracy, and F1 score on this particular train/test split. However, its recurrence-class recall was 41.67%, so it did not identify all recurrence cases.

Because the classes are imbalanced, accuracy and ROC-AUC should be considered together with class-specific metrics such as recall and F1 score.

## Visualizations

The notebook includes:

- Biochemical Recurrence Distribution
- Confusion Matrix
- ROC Curve
- Top 15 Random Forest Feature Importances

## Project Structure

```text
predict_prostat/
├── main.ipynb
├── prostat.tsv
├── .gitignore
└── README.md
```

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/OmidDevAi/predict_prostat.git
cd predict_prostat
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.\\.venv\\Scripts\\Activate.ps1
```

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

### 4. Open the notebook

```bash
jupyter notebook
```

Then open `main.ipynb`.

## Limitations

- The dataset is relatively small.
- The recurrence class contains fewer samples than the no-recurrence class.
- Only two classification models are included in this notebook.
- The reported metrics come from a single train/test split.
- No external clinical validation was performed.
- The model is not designed for medical diagnosis.

## Future Improvements

- Add stratified cross-validation.
- Test additional classification algorithms.
- Address class imbalance with appropriate methods.
- Tune model hyperparameters.
- Compare additional evaluation metrics.
- Improve feature engineering.
- Add model explainability.

## Key Takeaway

This project demonstrates a complete, practical classification workflow: loading real-world tabular data, cleaning and preprocessing it, training multiple models, evaluating class-specific performance, and examining feature importance.

The results also show why a single metric should not be used to evaluate a classification model when the target classes are imbalanced.

## Author

**Omid Rezapour**

GitHub: [OmidDevAi](https://github.com/OmidDevAi)
