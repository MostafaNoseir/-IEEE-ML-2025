# 📊 Logistic Regression on Food Items Dataset

## 📝 Overview
This notebook presents an end-to-end machine learning pipeline for **multiclass classification** using **Logistic Regression**. It compares **Multinomial Logistic Regression** with the **One-vs-Rest strategy**, explores regularization, and performs hyperparameter tuning to improve model performance.

---

## 📁 Dataset
- **Source**: Food Items Dataset  
- **Features**: Includes nutritional information like calories, protein, fat, etc.  
- **Target**: Multiclass labels indicating food categories.

---

## 🔍 Workflow Summary

### 1. Data Exploration
- Loaded and inspected the dataset.
- Performed summary statistics and null value checks.
- Remove Duplicates.
- Handle Outliers by remove them.
- Visualized feature Distributions and Correlation.

### 2. Data Preprocessing
- Ordinal Encoding for Target.
- Standardized numerical features using `StandardScaler`.
- Split data into training and test sets.
- Apply Feature Selection (optional).
- Handled class imbalance with techniques like **SMOTE** (optional).

### 3. Model Training
- Trained **Multinomial Logistic Regression** (`multi_class='multinomial'`).
- Trained **One-vs-Rest Logistic Regression** (`multi_class='ovr'`).

### 4. Evaluation Metrics
- Calculated:
  - Accuracy
  - Precision, Recall, F1-score (per class)
  - Macro & weighted averages
  - Confusion Matrix
  - **ROC-AUC** curves (using One-vs-Rest and `predict_proba`)

### 5. Visualization
- Plotted confusion matrices.
- Plotted ROC-AUC curves for each class.

### 6. Hyperparameter Tuning
- Performed **GridSearchCV** with 5-fold cross-validation.
- Tuned parameters:
  - `C`: [0.01, 0.1, 1, 10, 100]
  - `penalty`: ['l1', 'l2']
  - `solver`: ['saga', 'lbfgs']
- **Best Parameters**:
  ```python
  {'C': 10, 'penalty': 'l1', 'solver': 'saga'}
  ```

---

## ✅ Results Summary

| Model                    | Accuracy |
|--------------------------|----------|
| One-vs-Rest Logistic     | 0.81     |
| Multinomial Logistic     | 0.82     |
| Tuned Multinomial (Grid) | 0.83     |

- **Multinomial Logistic Regression** gave slightly better generalization.

---

## 🧠 Key Insights
- **Regularization** enhances generalization and reduces overfitting.
- **Multinomial Logistic Regression** is more suited for true multiclass problems than One-vs-Rest.
- **Hyperparameter tuning** can significantly improve performance.
