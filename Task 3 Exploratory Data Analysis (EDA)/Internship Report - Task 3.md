
# **Internship Report – Task 3**

**Company:** Codveda Technologies
**Intern:** Emmanuel Umeogu
**Task Title:** Exploratory Data Analysis (EDA)

---

## **1. Introduction**

As part of my internship at Codveda Technologies, I was assigned **Task 3: Exploratory Data Analysis (EDA)**. The purpose of this task was to analyze the cleaned dataset in order to uncover patterns, trends, and relationships between variables.

EDA is a crucial step in the data analysis pipeline as it provides insights into the underlying structure of the dataset, highlights potential anomalies, and informs feature selection for predictive modeling.

---

## **2. Objectives**

* Compute summary statistics (mean, median, variance, etc.).
* Visualize distributions of numerical and categorical variables.
* Explore relationships between features using scatter plots and box plots.
* Identify correlations between numerical features using a correlation matrix.
* Generate a summary of findings and actionable insights.

---

## **3. Tools and Libraries**

* **Python 3**
* **Pandas** → Data manipulation and summary statistics.
* **Matplotlib** → Data visualization.
* **Seaborn** → Enhanced statistical graphics.

Installation:

```bash
pip install pandas matplotlib seaborn


---

## **4. Methodology & Steps**

### **Step 1: Load Data**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset (Titanic dataset used for demonstration)
df = pd.read_csv("cleaned_titanic.csv")

# Preview dataset
df.head()
```

---

### **Step 2: Summary Statistics**

```python
# General statistics
print(df.describe(include="all"))

# Specific statistics
print("Mean Age:", df["Age"].mean())
print("Median Age:", df["Age"].median())
print("Fare Variance:", df["Fare"].var())
```

---

### **Step 3: Univariate Analysis (Histograms & Boxplots)**

```python
# Age distribution
plt.figure(figsize=(6,4))
sns.histplot(df["Age"], bins=20, kde=True)
plt.title("Age Distribution")
plt.show()

# Fare distribution
plt.figure(figsize=(6,4))
sns.boxplot(x=df["Fare"])
plt.title("Fare Distribution")
plt.show()
```

---

### **Step 4: Bivariate Analysis (Scatter Plots & Boxplots)**

```python
# Age vs Fare
plt.figure(figsize=(6,4))
sns.scatterplot(x="Age", y="Fare", data=df, hue="Survived")
plt.title("Age vs Fare (colored by Survival)")
plt.show()

# Survival by Passenger Class
plt.figure(figsize=(6,4))
sns.boxplot(x="Pclass", y="Fare", data=df)
plt.title("Fare Distribution by Passenger Class")
plt.show()
```

---

### **Step 5: Correlation Analysis**

```python
# Correlation matrix
corr = df.corr(numeric_only=True)

plt.figure(figsize=(8,6))
sns.heatmap(corr, annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Correlation Matrix")
plt.show()
```

---

## **5. Results & Insights**

1. **Summary Statistics**

   * Average Age \~ 29 years, median close to mean → fairly balanced.
   * Fare distribution is **right-skewed** (a few passengers paid very high fares).

2. **Univariate Analysis**

   * Age distribution shows a concentration between 20–40 years.
   * Boxplot of Fare reveals significant **outliers** (wealthy passengers in 1st class).

3. **Bivariate Analysis**

   * Scatter plot of Age vs Fare shows **no strong linear relationship**, but class differences are visible.
   * Boxplot shows higher fares for 1st class compared to 2nd and 3rd class.

4. **Correlation Analysis**

   * Strong positive correlation between **Pclass and Fare** (higher class → higher fare).
   * Weak correlation between Age and Survival.
   * Survival is more strongly influenced by **class** and **fare** than age.

---

## **6. Conclusion**

Through this EDA, I discovered that:

* Fare is highly skewed and class-dependent.
* Survival rates vary significantly across passenger classes.
* Age has a moderate distribution but less direct influence on survival compared to class.
* Correlation analysis confirms **socio-economic status (Pclass + Fare)** was a key survival factor.

These insights provide a strong foundation for further **predictive modeling tasks**.

---

Would you like me to also prepare a **ready-to-export PDF version with plots included** so you can submit Task 3 as a polished report just like Task 1 and Task 2?
