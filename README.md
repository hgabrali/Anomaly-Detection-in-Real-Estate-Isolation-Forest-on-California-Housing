# 🏡 Isolation Forest Explorer: Detecting Anomalies in California Housing Data

## Project Overview

This repository features a hands-on exercise in **Anomaly Detection** using the powerful **Isolation Forest** algorithm. The core objective is to identify and analyze unusual property listings within the **California Housing Dataset**—defined as homes exhibiting extreme or rare combinations of characteristics (e.g., highly unusual median income, room count, or geographic coordinates).

**Source Material:** This project was completed as part of the **Masterschool Unsupervised Learning** curriculum, focusing on practical implementation and deep analysis of outlier detection methods.

---

## 🎯 Project Goals

The primary goal is to move beyond mere detection and conduct a detailed analysis of the flagged anomalies, validating the model's sensitivity to parameter choices.

### 🛠️ Technical Workflow

1.  **Data Ingestion & Preparation:** Load the California Housing dataset, create a `pandas DataFrame`, and perform necessary feature scaling to ensure stable distance calculations.
2.  **Model Fitting:** Initialize and fit the **Isolation Forest** model, requiring the selection and justification of an appropriate **`contamination` rate**.
3.  **Scoring & Labeling:** Use the model to generate anomaly scores and assign binary labels (`1` for anomaly, `0` for normal).
4.  **Exploratory Results:** Create a scatter plot visualizing the distribution of normal points and highlighting anomalies based on key features (e.g., `MedInc` vs. `HouseAge`).
5.  **Sensitivity Analysis:** Empirically assess how changes in the **`contamination`** rate (1%, 2%, 5%, 10%) impact the outcome.

### ❓ Analytical Questions & Analysis

The final deliverable includes a written analysis addressing the following comparative questions:

* **Feature Extremity:** Which features are most extreme among the top 10 flagged anomalies? A direct comparison of `MedInc`, `AveRooms`, `AveBedrms`, and `HouseAge` values is performed.
* **Geographic Clustering:** Are the identified anomalies concentrated in specific regions (analyzed via `Lat/Lon` coordinates) or are they geographically dispersed?
* **Contamination Impact:** How does altering the `contamination` rate affect:
    * The total number of flagged points?
    * The **character** of the flagged outliers (i.e., do they remain "extreme" by the same features, or do less extreme points become included)?

---

## ⚙️ Dependencies

* `pandas`
* `scikit-learn` (for `IsolationForest`, data loading, and preprocessing)
* `matplotlib` / `seaborn` (for visualization)
