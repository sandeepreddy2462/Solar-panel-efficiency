# ☀️ Solar Panel Efficiency Prediction 🚀

## 🧠 1. Problem Statement

The goal of this project is to **predict the efficiency** of solar panels ⚡ based on a mix of **environmental**, **installation**, and **operational** factors.

---

## 🛠️ 2. Tools & Technologies Used

* **Languages**: 🐍 Python
* **Libraries**:
  📊 `pandas`, `numpy` – Data Handling
  📈 `seaborn`, `matplotlib` – EDA & Visualization
  🤖 `scikit-learn` – Preprocessing & Modeling
* **Environment**: 🌐 Google Colab Notebook

---

## 🧹 3. Data Preprocessing

### 🔄 Invalid Entry Handling

Replaced `'unknown'`, `'badval'`, `'UNK'` in numeric object columns:
→ `humidity`, `wind_speed`, `pressure` with `NaN` and converted to numerics.

### 🧩 Missing Value Imputation

* 🔢 Numeric: filled with **median**
* 🔤 Categorical: filled with **mode**

### ✂️ Dropped Uncorrelated Features

Removed columns with weak correlation to `efficiency` based on heatmap:

```
['humidity', 'temperature', 'maintenance_count', 'cloud_coverage', 'wind_speed', 'pressure']
```

### 🚨 Outlier Handling

* Evaluated via boxplots 📦
* No rows removed to maintain data integrity 🔐

### 🧬 Encoding

* One-hot encoded:

  * `string_id`, `error_code`, `installation_type`
  * `drop_first=True` ✅ to avoid multicollinearity

### ⚖️ Test Data Alignment

* Used: `reindex(columns=train_columns, fill_value=0)`
* Ensures test features perfectly match train features 👯

---

## 📊 4. Feature Selection

* ❌ Removed `id` column
* 🎯 Target: `efficiency`
* ✅ Final features: **13**

---

## 🤖 5. Modeling

### 🧪 Models Evaluated:

* 🔹 Linear Regression
* 🌲 Random Forest Regressor
* 🌟 Gradient Boosting Regressor

### 🏆 Best Model: **Gradient Boosting Regressor**

* 🧮 **RMSE**: `0.1064`
* 📈 **R² Score**: `0.4364`

---

## 📁 6. Submission File

* Format:

  ```csv
  id, efficiency
  ```
* ✅ Predictions made on encoded test set using the best model

---

## 📝 7. Summary

This project involved building a **robust data pipeline** 🔧 that includes:

✅ Cleaning & imputing missing values
✅ Dropping uncorrelated features
✅ One-hot encoding for model compatibility
✅ Test-train feature alignment
✅ Model comparison with evaluation using RMSE & R²

📌 **Outcome**: A consistent and efficient model pipeline for solar panel efficiency prediction 🌞
