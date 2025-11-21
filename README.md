# 🌍 Climate and Environmental Data Clustering & Forecasting

This project performs an in-depth analysis of global climate indicators for multiple countries (2000–2024). The main goals are:

- 🔍 Understand climate patterns
- 🌐 Group countries based on environmental similarity
- 📊 Visualize global climate structure
- 📈 Forecast CO₂ emissions for future years

This analysis uses real multi-year environmental indicators such as Temperature, CO₂ emissions, Rainfall, Population, Forest Cover, and Extreme Weather Events.

---

## 📁 Dataset Overview

Each row contains:

| Feature | Description |
|---------|-------------|
| **Country** | Country name |
| **Year** | Year of observation |
| **Avg_Temperature_degC** | Average annual temperature |
| **CO2_Emissions_tons_per_capita** | CO₂ emissions per capita |
| **Rainfall_mm** | Annual rainfall |
| **Population** | Total population |
| **Forest_Area_pct** | % of land covered by forest |
| **Renewable_Energy_pct** | % energy from renewable sources |
| **Extreme_Weather_Events** | Count of major events |
| **Sea_Level_Rise_mm** | Sea level change |

---

## 🔍 Exploratory Data Analysis (EDA)

✔ Null & duplicate check  
✔ Country & year counts  
✔ Summary statistics

### Correlation Heatmap Highlights

- **Population ↔ Extreme Events:** 0.58
- **Rainfall ↔ Forest Cover:** 0.51
- **Sea Level Rise ↔ Extreme Events:** 0.60
- **CO₂ ↔ Rainfall:** –0.56

### "Top 5" Visual Insights

- **Highest temperature** → Nigeria
- **Highest CO₂ per capita** → Saudi Arabia
- **Highest rainfall** → Indonesia
- **Highest forest area** → Brazil
- **Most extreme events** → United States

---

## 🧠 Clustering (K-Means)

### One-row-per-country transformation

Used:
```python
df_country = df.groupby("Country").mean(numeric_only=True).drop("Year", axis=1)
```

### Feature Scaling
StandardScaler applied

### KMeans
Applied with `n_clusters=4`

### Model Validation

**Silhouette Score:** `0.3559` → moderate, meaningful clusters

Also tested clusters for k = 2 to 6.

### Cluster Profiles

| Cluster | Description |
|---------|-------------|
| **0 – Industrialized Moderate Countries** | High CO₂, moderate climate (e.g., Germany, France, Japan) |
| **1 – Tropical, High Rainfall, Low CO₂** | Low emissions, high forest cover (Brazil, Indonesia, Nigeria) |
| **2 – High Population Developing Giants** | Massive population, rising CO₂ (China, India) |
| **3 – High CO₂ Outlier** | United States (unique profile) |

---

## 🖼 Dimensionality Reduction (PCA & t-SNE)

### PCA
- Shows global structure
- Good for linear variance understanding

### t-SNE
- Shows local cluster separation
- Best for visual cluster discovery

> **Note:** PCA and t-SNE do NOT match visually — this is expected due to different mathematical objectives.

Both visualizations color each country by cluster.

---

## 📈 CO₂ Forecasting using Linear Regression

A separate regression model is trained for each country:

```
X = Year
y = CO₂ Emissions per capita
```

**Predicted emissions for:** 2025, 2030, 2035

**Example output:**

```
Country: United States
2025: 17.10
2030: 17.56
2035: 18.01
```

### Why no train_test_split?

Linear Regression is used without `train_test_split`, because:

> Time series must preserve order (past → present → future), and random splitting breaks chronological structure.

---

## 🧾 Project Conclusion

- Countries cluster naturally into **four climate-environment groups**
- Industrialized nations have **high CO₂, moderate climate**
- Tropical nations have **low emissions, high rainfall, high forests**
- China & India form a **unique mega-population cluster**
- The USA forms a **stand-alone outlier cluster** due to extreme emissions and extreme weather frequency
- Forecasting shows which countries will see **rising CO₂ trends**

### This project demonstrates:

✔ EDA  
✔ Visualization  
✔ Clustering  
✔ Dimensionality reduction  
✔ Regression forecasting  
✔ Climate insight generation

---

## 🛠 Technologies Used

- **Python**
- **Pandas**
- **Seaborn / Matplotlib**
- **Scikit-learn** (KMeans, PCA, TSNE, LinearRegression)
- **NumPy**

---

## 📎 How to Run

VS Code

Jupyter Lab

Google Colab

---

## 🎯 Author

**Sourav Mondal**  
MBA – Business Analytics  
Data Science & Machine Learning Enthusiast

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!  
Feel free to check the [issues page](../../issues).

---

## ⭐ Show your support

Give a ⭐ if this project helped you!
