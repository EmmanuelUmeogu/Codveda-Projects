## Task 5: Classification with Logistic Regression (Extended to ROC Comparison)

### Objective
Compare **Logistic Regression, Random Forest, and SVM** classifiers on a multiclass dataset using ROC curves and AUC scores.

---

### Steps

1. **Preprocessing**
   - Encoded categorical variables using `pd.get_dummies()`.
   - Split dataset into training and test sets.
   - Standardized features using `StandardScaler()`.

2. **Model Training**
   - Trained three models:
     - Logistic Regression
     - Random Forest
     - Support Vector Machine (with `probability=True` for ROC curves)

3. **Predicted Probabilities**
   - Used `.predict_proba()` to obtain class probabilities for each model.
   - Applied **label binarization** (`label_binarize`) on `y_test` to handle the multiclass target.

4. **ROC Curve Generation**
   - For each class:
     - Computed False Positive Rate (FPR) and True Positive Rate (TPR) using `roc_curve`.
     - Plotted ROC curves for Logistic Regression, Random Forest, and SVM.
   - Added diagonal baseline (`y = x`) for reference.

5. **Evaluation Metrics**
   - Calculated **AUC (Area Under the Curve)** for each class and each model.
   - Computed **micro-averaged** and **macro-averaged** AUC scores for overall performance comparison.

---

### Results

- **ROC curves** provide a visual comparison of classifier performance across classes.
- **AUC Scores** (micro & macro averaged) summarize model performance in a single number:
  - Higher AUC = better overall classification performance.

---

### Tools
- **Python**
- **scikit-learn**
- **pandas**
- **matplotlib**
- **numpy**

---

✅ This approach gives both **class-wise ROC insights** and **overall performance metrics**, enabling a fair comparison of the three classifiers.
