

# 🏡 Task 6: Clustering (Unsupervised Learning)

## **Objective**

Implement **K-Means clustering** to group data points into clusters without labels (e.g., customer or house segmentation).

---

## **Steps Taken**

### 🔹 1. Data Preparation

* Loaded the dataset into pandas.
* Selected relevant features (excluding `SalePrice` to allow unbiased clustering).
* Scaled numerical features using **StandardScaler** for better clustering performance.

---

### 🔹 2. Choosing Number of Clusters

* Applied the **Elbow Method** by plotting Within-Cluster-Sum-of-Squares (WCSS) vs. number of clusters.
* Checked **Silhouette Scores** to evaluate cluster quality.
* Selected the optimal `k` (number of clusters) based on these methods.

---

### 🔹 3. K-Means Clustering

* Trained the **K-Means algorithm** with the chosen number of clusters.
* Assigned each data point to its cluster.

---

### 🔹 4. Dimensionality Reduction & Visualization

* Used **PCA (Principal Component Analysis)** to reduce dimensions to 2D space.
* Plotted clusters with different colors to visualize grouping.

---

### 🔹 5. Cluster Analysis

* Calculated **average `SalePrice` per cluster** to interpret business meaning:

  * Cluster 0 → Old/small houses → Lower average price.
  * Cluster 1 → Renovated/larger homes → Mid-range prices.
  * Cluster 2 → Luxury homes → High average price.
* Compared feature distributions (size, quality, location) across clusters.

---

## **Findings**

* Clusters revealed **natural segmentation** in the housing market.
* Even without using `SalePrice` directly, clusters showed distinct **price groupings**.
* This method can help with **market segmentation, pricing strategy, and targeted recommendations**.

---

## **Tools Used**

* Python
* pandas, numpy
* scikit-learn (KMeans, StandardScaler, PCA)
* matplotlib, seaborn

---

