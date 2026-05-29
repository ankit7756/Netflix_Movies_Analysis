# Netflix Movies — End-to-End Data Analysis

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-orange)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

## Project Overview

A complete end-to-end data analysis of 16,000 Netflix movies 
simulating a real-world analyst workflow. Starting from raw messy 
data and ending with business insights and investment 
recommendations for a hypothetical film production investor.

This project covers the full professional data analysis pipeline:
raw data → cleaning → feature engineering → EDA → visualization 
→ business recommendations.

---

## Business Questions Answered

- Which movie genres generate the highest return on investment?
- Do larger budgets guarantee higher revenue?
- Which non-English languages show strong commercial potential?
- What separates profitable movies from financial flops?
- How has Netflix content quality changed over time?
- What does a safe investment strategy look like based on data?

---

## Repository Structure

```
netflix-movie-analysis/
│
├── data/
│   ├── netflix_titles.csv           # Raw original dataset
│   ├── netflix_cleaned.csv          # Cleaned dataset after Phase 1-4
│   └── netflix_financial_clean.csv  # Budget-filtered financial subset
│
├── netflix_analysis.ipynb           # Pandas — cleaning, EDA, analysis
├── netflix_visualizations.ipynb     # Matplotlib — all 10 charts
├── README.md
└── requirements.txt
```

---

## Dataset

- 16,000 Netflix movie records spanning 2010-2025
- Combined Netflix catalog + TMDB financial metadata
- Key fields: title, genres, language, budget, revenue, 
  vote_average, popularity, release_year, date_added

**Data quality issues found and resolved:**
- 11,153 budget zeros and 10,355 revenue zeros 
  (disguised missing data)
- Entirely empty duration column (16,000 nulls)
- Date columns stored as text objects
- 32 movies with impossibly low budgets ($5-$105) 
  discovered during visualization — removed for ROI analysis

---

## Key Findings

### Financial Coverage
Only 3,540 movies (22.3%) have verified financial data. 
All financial findings apply to this subset only.

### Genre ROI — Corrected
After removing corrupt budget entries and using median ROI:

| Genre | Median ROI | Flop Rate |
|-------|-----------|-----------|
| Animation | 127% | — |
| Family | 117% | — |
| Horror | 108% | 35% |
| Comedy | 102% | — |
| Adventure | 102% | — |
| Western | -41% | — |

Horror stands out as the best risk-adjusted investment — 
strong ROI with relatively low average budget of $14.7M.

### Budget vs Revenue
Correlation of 0.748 confirms higher budgets generally 
produce higher revenue. However ROI does not improve 
proportionally — mid-budget films are nearly as efficient 
as blockbusters at a fraction of the capital risk.

### Flop Risk
36.7% of movies with financial data failed to recoup budget.
Risk by tier:
- Low (<$10M): 43.3% flop rate
- Mid ($10-50M): 39.5% flop rate  
- High ($50-100M): 23.3% flop rate
- Blockbuster ($100M+): 10.4% flop rate

### Non-English Markets
Chinese language content leads at $225M average revenue.
Korean content offers best balance of volume and 
commercial performance at $42M average across 61 films.

### Quality Over Time
Ratings improved slowly from 6.15 (2011) to 6.46 (2025).
Budget barely correlates with quality (r = 0.12) — 
money does not buy audience satisfaction.

---

## Visualizations

| Chart | Finding |
|-------|---------|
| Genre Distribution | Drama dominates volume, Horror underrepresented |
| ROI by Genre | Animation, Family, Horror lead after outlier correction |
| Revenue by Budget Tier | Linear increase from $16M to $536M average |
| Flop Rate by Tier | Risk halves between Low and High budget |
| Budget vs Revenue | Strong trend with wide variance |
| Quality Trend | Slow consistent improvement 2011-2025 |
| Language Revenue | Chinese leads, Korean most reliable non-English |
| Correlation Heatmap | Budget barely predicts quality (0.12) |
| Rating Distribution | Near-normal, slight left skew |
| Popularity Trend | Sharp acceleration from 2022, 2024 spike |

---

## CEO Executive Summary

Based on 3,540 movies with verified financial data, the data 
recommends a clear investment strategy for Netflix film 
production. Horror emerges as the strongest risk-adjusted 
opportunity — delivering 108% median ROI on an average budget 
of just $14.7M, with Animation (127% ROI) and Family (117% ROI) 
close behind for investors willing to accept higher production 
costs. The data strongly advises against Western productions, 
the only genre with negative median ROI at -41%, and against 
Thriller despite its reputation — after correcting for corrupt 
budget entries, Thriller's true median ROI is only 35.6%, 
well below the dataset average. The safe strategy is a 
mid-budget Horror or Animation production in the $10-50M range, 
optionally co-produced in Korean or Chinese to access markets 
that consistently generate $42-225M average revenue. Blockbuster 
budgets above $100M reduce flop risk to 10.4% but require 
enormous capital commitment for returns that are not 
proportionally better than mid-tier productions. The data is 
clear — spend smart, pick proven genres, consider Asian markets.

---

## Tools Used

- Python 3.10
- Pandas — data cleaning and analysis
- NumPy — numerical operations
- Matplotlib — visualizations
- Seaborn — statistical charts
- Jupyter Notebook

---

## How To Run

```bash
git clone https://github.com/ankit7756/netflix-movie-analysis
cd netflix-movie-analysis
pip install -r requirements.txt
jupyter notebook
```

Open `netflix_analysis.ipynb` first, then 
`netflix_visualizations.ipynb`.

---

## Author

**Ankit Sharma**  
BSc Computing — Softwarica College / Coventry University  
[LinkedIn](https://www.linkedin.com/in/ankit7756/) • 
[GitHub](https://github.com/ankit7756)
