# NBA Career Longevity Prediction: Feature Engineering & Data Preparation

## **Project Overview**
This project focuses on conducting **feature engineering** on professional basketball player performance records to predict career longevity. Working with data representative of the National Basketball Association (NBA), the primary objective is to determine whether a player's professional career will last at least **five years** (`target_5yrs`). 

The insights and processed dataset generated in this pipeline serve as the foundation for downstream predictive machine learning models (such as Naive Bayes classifiers).

---

## **Project Pipeline & Steps**

### **1. Imports & Environment Setup**
* Imported standard data manipulation libraries (`pandas`).
* Loaded the dataset (`nba-players.csv`) into a pandas DataFrame using the first column as the row index.

### **2. Exploratory Data Analysis (EDA)**
* **Dataset Shape:** 1,340 rows and 21 columns consisting of player biometric and performance metrics.
* **Data Types:** Numerical features (float64 and int64) alongside one categorical identifier (`name`).
* **Missing Value Check:** Confirmed zero missing or null values across all columns.
* **Class Balance Evaluation:** Analyzed the target variable (`target_5yrs`) distribution:
  * $\approx 62\%$ of players achieved a career duration $\ge 5$ years (Class 1).
  * $\approx 38\%$ of players had shorter careers (Class 0).
  * *Conclusion:* The dataset exhibits a manageable class split, avoiding severe class imbalance concerns.

### **3. Feature Selection**
* Filtered out uninformative or potentially biased attributes (e.g., player `name`).
* Retained robust performance percentages and core metrics:
  * Field goal percentage (`fg`)
  * Three-point percentage (`3p`)
  * Free throw percentage (`ft`)
  * Total rebounds (`reb`)
  * Assists (`ast`), steals (`stl`), blocks (`blk`), and turnovers (`tov`).

### **4. Feature Extraction & Transformation**
To enhance predictive power, two new features were engineered:
* **`total_points`**: Calculated as games played multiplied by average points per game ($\text{gp} \times \text{pts}$).
* **`efficiency`**: Calculated as total points earned divided by total minutes played ($\frac{\text{total points}}{\text{min} \times \text{gp}}$), serving as a measure of scoring efficiency per minute.
* **Dimensionality Reduction:** Dropped raw aggregated columns (`gp`, `pts`, `min`) to satisfy feature independence assumptions required for future Naive Bayes modeling.

### **5. Exporting Processed Data**
* Exported the final cleaned and engineered feature set into a new production-ready CSV file: `extracted_nba_players_data.csv`.

---

## **Key Takeaways & Stakeholder Summary**
* **Feature Engineering Impact:** Combining raw averages into holistic metrics like total production and efficiency yields stronger predictive indicators.
* **Model Readiness:** The extracted dataset is fully cleaned, transformed, and decoupled of redundant features, making it ready for ingestion into classification models.
* **Next Steps:** Proceed to model training, hyperparameter tuning, and performance evaluation to deliver actionable player retention insights to NBA managers and coaches.
