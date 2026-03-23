# 💎 Diamond Price Classification using Machine Learning

## 📌 Project Overview
This project aims to predict diamond price categories using machine learning techniques.  
The original regression problem was transformed into a **multi-class classification task** by grouping prices into three categories: Low, Medium, and High.

The pipeline includes:
- Data preprocessing & cleaning
- Feature engineering
- Model training & evaluation
- Hyperparameter optimization using Optuna
- Synthetic data generation using CTGAN

---

## 📊 Dataset
The dataset contains information about diamonds, including:

- Numerical features: `carat`, `depth`, `table`, `price`, `x`, `y`, `z`
- Categorical features: `cut`, `color`, `clarity`

### 🔧 Data Preprocessing
- Removed duplicates and invalid values
- Handled missing values using median (numerical) and mode (categorical)
- Removed outliers (extreme carat and price values)
- Ensured valid dimensions (x, y, z > 0)

---

## 🧠 Feature Engineering
- Created new features:
  - `volume = x * y * z`
  - `density = carat / volume`
  - Ratio features (xy, xz, yz)
- Applied **ordinal encoding**:
  - Cut: Fair → Ideal
  - Color: J → D
  - Clarity: I1 → IF

---

## 🎯 Target Variable
- Converted `price` into 3 balanced categories using quantiles:
  - `0 → Low`
  - `1 → Medium`
  - `2 → High`

---

## ⚙️ Model Training
Data was split into:
- 80% Training
- 10% Validation
- 10% Test

Features were scaled using **StandardScaler**.

---

## 🔍 Hyperparameter Optimization
Used **Optuna** for tuning Random Forest:

**Best Parameters:**
- `n_estimators`: 149  
- `max_depth`: 12  
- `min_samples_split`: 5  
- `min_samples_leaf`: 3  
- `max_features`: None  

---

## 📈 Model Performance

### ✅ Random Forest (Best Model)
- **Validation Accuracy:** 96%  
- **Test Accuracy:** 95%  

✔️ Indicates strong performance and good generalization.

---



## 🤖 Synthetic Data Generation
Synthetic data was generated using **CTGAN** to evaluate model robustness.

### 📊 Results (5-Fold Cross-Validation)
- Mean Accuracy: **84.35%**
- Standard Deviation: **0.0063**

### 🔍 Insight
- Slight drop compared to real data (expected)
- Model remains stable and robust under new data distribution

---

## 📌 Key Insights
- Random Forest provides strong and reliable performance for structured data
- Hyperparameter tuning significantly improves model accuracy
- Synthetic data helps evaluate model generalization
- Feature engineering plays a critical role in performance

---

## 🚀 Technologies Used
- Python
- Pandas, NumPy
- Scikit-learn
- Optuna
- CTGAN
- Matplotlib, Seaborn

