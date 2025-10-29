# 📈 Anomaly Detection Report: Isolation Forest on California Housing

This report summarizes the findings of the **Isolation Forest** application on the California Housing dataset (initial run with `contamination=0.05`), focusing on outlier characterization and model sensitivity.

---

## 1. Outlier Characterization (Top 10 Anomalies)

The most extreme anomalies, identified by the lowest **anomaly score**, consistently show distortion in features related to property size and population density:

| Feature Group | Finding | Implication |
| :--- | :--- | :--- |
| **Size & Density** | **`Population`** and **`AveOccup`** (Average Occupancy) show the most extreme, highly skewed values (e.g., `AveOccup` > 100 occupants per household). | Flags highly dense or specialized districts (e.g., institutional areas), not typical family homes. |
| **Room Counts** | **`AveRooms`** and **`AveBedrms`** exhibit unusually high averages (e.g., `AveRooms` > 20). | Suggests non-standard properties (hotels, large complexes, or data errors) rather than typical residential units. |
| **Income** | **`MedInc`** (Median Income) is **less dominant** in defining the top outliers, despite having some capped high values. | The model prioritizes structural/density anomalies over pure income extremes. |

---

## 2. Geographic Distribution (Spatial vs. Compositional Anomalies)

* **Finding:** The anomalies, defined by their extreme occupancy and room features, are **geographically spread out** across California (spanning various `Latitude` and `Longitude` coordinates).
* **Conclusion:** The Isolation Forest model is effectively identifying **unusual property characteristics (compositional anomalies)** rather than merely flagging geographical outliers (spatial anomalies).

---

## 3. Sensitivity Analysis: The Contamination Rate

The **`contamination`** parameter is critical as it acts solely as a **labeling threshold**; it **does not change the internal structure** (scores) of the trained forest.

| Contamination Rate | Effect on Number of Flagged Points | Effect on Character of Outliers |
| :--- | :--- | :--- |
| **1%** | Flags the **most extreme 1%** (approx. 206 points). | Flags only the **purest, high-confidence outliers** (e.g., highest `AveOccup` and `AveRooms`). Character is very consistent. |
| **10%** | Flags the **top 10%** (approx. 2064 points). | The character **dilutes significantly**. The pool includes numerous borderline cases (e.g., high `MedInc`, less extreme occupancy) that are merely unusual, not truly anomalous. |

### 🔑 Key Finding

The **core character** of the outliers (extreme density/size) is **robust** regardless of the threshold. However, a high `contamination` rate introduces many **False Positives** (borderline cases), emphasizing the need for a **carefully justified threshold** based on the use case and domain knowledge.
