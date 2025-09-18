
# **Task 4: Predictive Modeling (Regression)**

## **Introduction**

In this task, we aim to build and evaluate regression models to predict a continuous variable. Regression is a statistical technique used to model the relationship between independent variables (features) and a dependent variable (target). The goal is to predict the target variable with minimal error.

We will use **linear regression** as the baseline model and experiment with advanced models like **Decision Trees** and **Random Forests** to compare performance.

---

## **Objectives**

* Split the dataset into **training** and **testing** sets.
* Train a **Linear Regression model** using scikit-learn.
* Evaluate model performance using **Mean Squared Error (MSE)** and **R-squared (R²)**.
* Experiment with alternative models (**Decision Tree** and **Random Forest**) and compare their performance.

---

## **Steps**

### **1. Import Libraries**

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.tree import DecisionTreeRegressor
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, r2_score
import matplotlib.pyplot as plt
import seaborn as sns
```

---

### **2. Load Dataset**


```python
# Example: Boston housing dataset (if available)
from sklearn.datasets import fetch_california_housing
data = fetch_california_housing(as_frame=True)

df = data.frame
print(df.head())
```

---

### **3. Define Features and Target**

```python
X = df.drop("MedHouseVal", axis=1)   # Features
y = df["MedHouseVal"]               # Target variable
```

---

### **4. Train-Test Split**

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

---

### **5. Train and Evaluate Linear Regression**

```python
lin_reg = LinearRegression()
lin_reg.fit(X_train, y_train)

y_pred_lr = lin_reg.predict(X_test)

mse_lr = mean_squared_error(y_test, y_pred_lr)
r2_lr = r2_score(y_test, y_pred_lr)

print("Linear Regression Results:")
print(f"Mean Squared Error: {mse_lr:.4f}")
print(f"R-squared: {r2_lr:.4f}")
```

---

### **6. Train and Evaluate Decision Tree**

```python
tree_reg = DecisionTreeRegressor(random_state=42)
tree_reg.fit(X_train, y_train)

y_pred_tree = tree_reg.predict(X_test)

mse_tree = mean_squared_error(y_test, y_pred_tree)
r2_tree = r2_score(y_test, y_pred_tree)

print("\nDecision Tree Results:")
print(f"Mean Squared Error: {mse_tree:.4f}")
print(f"R-squared: {r2_tree:.4f}")
```

---

### **7. Train and Evaluate Random Forest**

```python
rf_reg = RandomForestRegressor(n_estimators=100, random_state=42)
rf_reg.fit(X_train, y_train)

y_pred_rf = rf_reg.predict(X_test)

mse_rf = mean_squared_error(y_test, y_pred_rf)
r2_rf = r2_score(y_test, y_pred_rf)

print("\nRandom Forest Results:")
print(f"Mean Squared Error: {mse_rf:.4f}")
print(f"R-squared: {r2_rf:.4f}")
```

---

### **8. Compare Model Performance**

```python
results = pd.DataFrame({
    "Model": ["Linear Regression", "Decision Tree", "Random Forest"],
    "MSE": [mse_lr, mse_tree, mse_rf],
    "R-squared": [r2_lr, r2_tree, r2_rf]
})

print("\nModel Comparison:")
print(results)

sns.barplot(x="Model", y="R-squared", data=results)
plt.title("Model Performance Comparison")
plt.show()
```

---

## **Results**

* **Linear Regression** provides a baseline model with interpretable coefficients but may underfit complex relationships.
* **Decision Tree** captures non-linear patterns but risks overfitting.
* **Random Forest** generally achieves the best performance by combining multiple trees, reducing variance.

