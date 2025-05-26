# 🎮 Video Game Sales Analysis & Insights

This project performs an extensive exploratory data analysis and statistical study of global video game sales, leveraging visualizations and hypothesis testing to uncover trends, relationships, and market patterns in the gaming industry.

We use:

✅ Python & Pandas for data wrangling  
📊 Seaborn & Matplotlib for rich visualizations  
📈 Scipy stats for formal hypothesis testing  
🧠 Insight-driven markdown for reporting and presentation  

---

## 📦 Dataset Overview

**Source**: [Kaggle – Video Game Sales Dataset](https://www.kaggle.com/datasets/gregorut/videogame-sales-with-ratings)

The dataset includes:

- 16,500+ game records  
- Key features: `Name`, `Platform`, `Genre`, `Publisher`, `Year_of_Release`, `User_Score`, `Rating`  
- Sales data by region: `NA_Sales`, `EU_Sales`, `JP_Sales`, `Other_Sales`, and `Global_Sales`

---

## 🧠 Analysis Pipeline

### 📌 1. Data Preprocessing & Cleaning
- Handled missing values in key fields (e.g., `Year_of_Release`, `Publisher`, `Rating`)
- Converted `User_Score` to numeric
- Dropped incomplete rating/critic fields
- Standardized text fields for consistency

### 📊 2. Exploratory Data Visualization
- Distribution of global sales
- Game output over time
- Top-selling games and publishers
- Regional sales breakdown
- Score and rating distributions
- Genre and platform trends

### 🧪 3. Statistical Testing
- ✅ **Pearson Correlation** between `User_Score` and `Global_Sales`
- ⚔️ **T-Test**: Action vs Strategy genre sales
- 🧠 **ANOVA**: Global sales across ESRB `Rating` groups
- 🎲 **Chi-Square Test**: Dependence between `Genre` and `Rating`

---

## 📊 Results Summary

| Test / Insight          | Key Finding |
|-------------------------|-------------|
| User Score Correlation  | No strong correlation with sales |
| Action vs Strategy      | Action games sell significantly more |
| Rating vs Sales (ANOVA) | Sales vary significantly by rating |
| Genre ↔ Rating (Chi2)   | Strong dependency observed |

---

## 📈 Visual Insights

- 📉 Most games sell < 1M copies, while top games sell > 40M  
- 🕹️ Platforms like PS2, Wii, and DS dominate lifetime sales  
- 🎯 Action and Sports are the most prolific and profitable genres  
- 🌍 North America accounts for nearly half of global sales  
- 🧮 Ratings and genre heavily influence market placement

---

## 🧰 Tech Stack

- Python 3  
- Pandas, NumPy  
- Matplotlib, Seaborn  
- Scikit-learn (for preprocessing)  
- SciPy stats (Pearson, t-test, ANOVA, Chi2)

---

## 🚀 How to Run

1. Clone the repository  
`git clone https://github.com/<your-username>/video-game-sales-analysis.git`

2. Launch the notebook
 `jupyter notebook video-game-sales-analysis.ipynb`

3. Run all cells to reproduce the visualizations and statistical outputs

---

## ✅ Key Takeaways

- 🎮 **Action and Sports** genres lead both in number of titles and total global sales
- 🕹️ **PS2, Wii, and DS** are the top platforms in lifetime global sales
- 🌍 **North America** contributes nearly half of all global sales, followed by Europe and Japan
- 📉 **Most games sell under 1 million copies**, showing a right-skewed market distribution
- ⭐ **User scores** have weak correlation with sales — popularity isn’t always predictive
- 🧪 **Statistical tests** confirmed:
  - Action games significantly outsell Strategy games
  - ESRB ratings affect average sales (via ANOVA)
  - Game genres are statistically associated with content ratings (Chi-Square)
- 📈 Peak release years were around **2008–2010**, aligning with console booms
- 📊 Combining EDA with statistical testing offers **powerful insights** for developers, marketers, and analysts

> This project showcases how structured EDA and classic statistics can unlock trends and guide strategic decisions in the gaming industry.
