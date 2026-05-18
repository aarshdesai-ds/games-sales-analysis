# Video Game Sales Analysis

A comprehensive exploratory data analysis of global video game sales, examining commercial performance across genres, platforms, regions, and time periods using Python and Jupyter.

---

## Dataset

**Source:** [Kaggle — Video Game Sales with Ratings](https://www.kaggle.com/datasets/gregorut/videogame-sales-with-ratings)

| Attribute | Value |
|---|---|
| Raw records | 16,928 |
| Records after cleaning | 16,620 |
| Features | 17 (Name, Platform, Genre, Publisher, Year_of_Release, User_Score, Rating, regional & global sales) |
| Sales columns | NA_Sales, EU_Sales, JP_Sales, Other_Sales, Global_Sales |
| Year range | 1980 – 2020 |
| Missing values addressed | Year_of_Release (273), Publisher (55), User_Score (6,769), Rating (6,836), Developer (6,688) |

---

## Data Cleaning

- Dropped rows with null values in `Name`, `Genre`, `Year_of_Release`, and `Publisher`
- Converted `Year_of_Release` from float to integer
- Converted `User_Score` to numeric; filled 6,769 missing values with the column mean (7.13)
- Filled missing `Rating` and `Developer` with `"Unknown"`
- Dropped `Critic_Score`, `Critic_Count`, and `User_Count` due to >50% missingness (~8,518–9,034 nulls each)

---

## Summary Statistics

| Metric | NA_Sales | EU_Sales | JP_Sales | Other_Sales | Global_Sales |
|---|---|---|---|---|---|
| Mean | 0.27M | 0.15M | 0.08M | 0.05M | 0.54M |
| Median | 0.08M | 0.02M | 0.00M | 0.01M | 0.17M |
| Std Dev | 0.82M | 0.51M | 0.31M | 0.19M | 1.56M |
| Max | 41.36M | 28.96M | 10.22M | 10.57M | 82.53M |

---

## Key Findings

### Publishers
- **Electronic Arts** leads all publishers with ~1,400 games released
- The top 10 publishers include Activision, Namco Bandai, Ubisoft, THQ, and Konami — a mix of Western and Japanese companies
- Top 20 publishers account for a disproportionate share of total game output

### Global Sales Distribution
- Sales are **heavily right-skewed** — the vast majority of games sell under **1 million copies**
- A small number of blockbuster titles (e.g., Wii Sports at **82.53M**) generate outsized revenue
- Median global sales sit at just **0.17M**, reinforcing the winner-takes-most dynamic in the industry

### Genre Performance

| Genre | Total Global Sales |
|---|---|
| Action | Highest (~1,750M) |
| Sports | Second |
| Shooter | Third |
| Role-Playing | Fourth |
| Platform | Fifth |
| Strategy / Puzzle / Adventure | Lower tail |

- **Action** games lead both in number of titles and cumulative global sales
- **Sports** and **Shooter** benefit from strong franchise loyalty and repeat purchases
- **Strategy**, **Puzzle**, and **Adventure** represent niche but stable segments

### Platform Performance (Top 5 by Global Sales)

| Platform | Rank |
|---|---|
| PS2 | 1st |
| X360 | 2nd |
| PS3 | 3rd |
| Wii | 4th |
| DS | 5th |

- **PS2** holds clear lifetime dominance; handheld platforms DS and GBA also rank highly
- **Wii and DS** saw peak sales between **2006–2010**, driven by Nintendo's casual gaming push
- All top platforms show a sales decline post-2012, marking a generational transition

### Top 10 Best-Selling Games

| Rank | Game | Global Sales |
|---|---|---|
| 1 | Wii Sports | 82.53M |
| 2 | Super Mario Bros. | 40.24M |
| 3 | Mario Kart Wii | 35.52M |
| 4 | Wii Sports Resort | 32.77M |
| 5 | Pokemon Red/Blue | 31.37M |
| 6 | Tetris | 30.26M |
| 7 | New Super Mario Bros. | 29.80M |
| 8 | Wii Play | 28.92M |
| 9 | New Super Mario Bros. Wii | 28.32M |
| 10 | Duck Hunt | 28.31M |

- Nintendo dominates the top 10, with 9 of the 10 best-selling titles
- **Wii Sports** benefited heavily from console bundling
- Classic titles like **Tetris** and **Duck Hunt** show the long-tail staying power of early hits

### Regional Sales Breakdown

| Region | Share of Global Sales |
|---|---|
| North America | ~49% |
| Europe | ~27% |
| Japan | ~15% |
| Other | ~9% |

- NA and EU show high inter-correlation (**r = 0.77**): games that sell well in one typically sell well in the other
- `NA_Sales` correlates with `Global_Sales` at **r = 0.94**, `EU_Sales` at **r = 0.90**
- Japan shows lower correlation with global totals (**r = 0.61**), reflecting distinct market preferences

### Temporal Trends
- Game releases and revenue **peaked around 2008–2009**
- The **2005–2010 window** was the most prolific period in traditional console/PC publishing
- A decline post-2010 aligns with the industry's shift toward digital and mobile platforms (partially a data coverage limitation)

### User Scores
- Average user score: **7.13 / 10**
- Most scores cluster between **6 and 8**
- Very few games receive scores below 4 or above 9 — the distribution is narrow and moderately right-peaked
- User scores remained stable across years, with a median close to **7** in most release years

### ESRB Ratings
- **E (Everyone)** is the most common rating among labeled games, reflecting a strong focus on family-friendly content
- **T (Teen)** and **M (Mature)** account for a significant secondary share
- A large portion of records fall under **"Unknown"** due to missing/unrated data

---

## Correlation Analysis

| Variable Pair | Pearson r |
|---|---|
| NA_Sales ↔ Global_Sales | 0.94 |
| EU_Sales ↔ Global_Sales | 0.90 |
| Other_Sales ↔ Global_Sales | 0.75 |
| JP_Sales ↔ Global_Sales | 0.61 |
| NA_Sales ↔ EU_Sales | 0.77 |
| User_Score ↔ Global_Sales | 0.07 |
| Year_of_Release ↔ Global_Sales | ~0.00 |

- Regional sales are the strongest predictors of global performance
- `User_Score` has near-zero linear relationship with sales — popularity is not driven by ratings
- `Year_of_Release` has no consistent directional effect on sales

---

## Statistical Tests

| Test | Variables | Result |
|---|---|---|
| Pearson Correlation | User_Score vs Global_Sales | r = 0.07, p < 0.0001 — statistically significant but weak |
| Welch's T-Test | Action vs Strategy (Global_Sales) | t = 9.25, p < 0.0001 — Action significantly outsells Strategy |
| One-Way ANOVA | ESRB Rating vs Global_Sales | F = 20.53, p < 0.0001 — ratings significantly affect sales |
| Chi-Square Test | Genre vs Rating | χ² = 6448.46, df = 88, p < 0.0001 — genre and rating are not independent |

---

## Tech Stack

- Python 3
- Pandas, NumPy
- Matplotlib, Seaborn
- SciPy (Pearson, T-Test, ANOVA, Chi-Square)

---

## How to Run

```bash
git clone https://github.com/aarshdesai-ds/games-sales-analysis.git
cd games-sales-analysis
jupyter notebook video-game-sales-analysis.ipynb
```

Run all cells to reproduce all visualizations and statistical outputs.

---

## Takeaways

- **Action and Sports** lead in both game count and total global revenue
- **PS2** is the highest-grossing platform of all time in this dataset; Nintendo dominates the all-time sales chart
- **North America** drives ~49% of global sales — it is the single most important market for publishers
- Sales distributions are right-skewed: most games sell modestly while a few titles generate outsized returns
- **User scores** (r = 0.07) are a poor predictor of commercial success — marketing, branding, and platform partnerships matter far more
- Statistical tests confirm that genre and ESRB rating both have significant effects on expected sales
- The **2008–2009 era** represents peak release volume and revenue for traditional gaming platforms
