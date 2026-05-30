# Netflix Movies — End-to-End Data Science Project

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-green)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-1.3-orange)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

## Project Overview

A complete end-to-end data science project analyzing 16,000 
Netflix movies — from raw messy data to trained machine learning 
models. Built to simulate a real-world analyst and data scientist 
workflow for a hypothetical media investment firm.

**The core question:** What does data tell us about what makes 
a movie financially successful — and can we predict it?

---

## Project Structure

```
netflix-movie-analysis/
│
├── data/
│   ├── netflix_titles.csv              # Raw original dataset
│   ├── netflix_cleaned.csv             # Cleaned dataset
│   └── netflix_financial_clean.csv     # Budget-filtered subset
│
├── charts/                             # All saved visualizations
│
├── netflix_analysis.ipynb              # Phase 1-4: Cleaning + EDA
├── netflix_visualizations.ipynb        # Phase 5: Matplotlib + Seaborn
├── netflix_ml.ipynb                    # Phase 6: ML Models
├── README.md
└── requirements.txt
```

---

## Pipeline Overview

```
Raw Data (16,000 rows, 18 columns)
        ↓
Phase 1 — Data Cleaning
  Resolved disguised missing values, wrong types,
  empty columns, text inconsistencies
        ↓
Phase 2 — Feature Engineering  
  Created profit, ROI, budget tiers, rating tiers,
  time features, genre explosion
        ↓
Phase 3 — EDA and Business Questions
  8 business questions answered with findings
        ↓
Phase 4 — Cleaning Log and Handoff
  Full audit trail of every transformation
        ↓
Phase 5 — Visualization
  11 charts — outlier discovered and corrected
  during visualization phase
        ↓
Phase 6 — Machine Learning
  5 models trained — classification and regression
  Data leakage identified and corrected
  Live prediction function built
```

---

## Dataset

- 16,000 Netflix movie records spanning 2010-2025
- Combined Netflix catalog and TMDB financial metadata
- Fields: title, genres, language, budget, revenue,
  vote_average, popularity, release_year, date_added

**Real data quality issues resolved:**
- 11,153 budget zeros — disguised missing data
- 10,355 revenue zeros — disguised missing data  
- 16,000 null duration column — dropped entirely
- 32 movies with budgets of $5-$105 — corrupt entries
  discovered during visualization, removed for analysis

---

## Key Findings

### Genre ROI — After Outlier Correction
| Genre | Median ROI |
|-------|-----------|
| Animation | 127% |
| Family | 117% |
| Horror | 108% |
| Comedy | 102% |
| Western | -41% (only loss-making genre) |

Thriller appeared strong at 488% mean ROI but dropped 
to 35.6% after removing corrupt budget entries — 
entirely outlier-driven.

### Flop Risk by Budget
| Budget Tier | Flop Rate |
|-------------|----------|
| Low (<$10M) | 43.3% |
| Mid ($10-50M) | 39.5% |
| High ($50-100M) | 23.3% |
| Blockbuster ($100M+) | 10.4% |

### Non-English Markets
Chinese language leads at $225M average revenue.
Korean content — best balance of volume and 
commercial performance at $42M across 61 films.

### Budget vs Quality
Budget and vote_average correlate at only 0.12.
Money does not buy audience satisfaction.

---

## Machine Learning Models

### Classification — Predicting Flop vs Success

**Important:** Initial model achieved 73.3% accuracy 
but included vote_count (post-release data) causing 
data leakage. Final model uses only pre-release 
features for honest real-world utility.

| Model | Accuracy |
|-------|---------|
| Logistic Regression | 61.1% |
| Decision Tree | 71.1% |
| Random Forest | 70.9% ✅ |
| Baseline (majority class) | 61.1% |

### Regression — Predicting Revenue

| Model | MAE | R² |
|-------|-----|----|
| Linear Regression | $62M | 0.644 |
| Random Forest | $50M | 0.719 ✅ |

### Live Prediction Example
```python
predict_movie_v2(
    budget=15_000_000,
    genre='Horror',
    language='en',
    popularity=25
)
# → SUCCESS (76% confidence)
# → Predicted revenue: $52.5M
# → Predicted profit: $37.5M
```

---

## Visualizations

| Chart | Key Insight |
|-------|------------|
| Genre Distribution | Drama dominates volume |
| ROI by Genre | Animation, Family, Horror lead |
| Revenue by Budget Tier | Linear increase to $536M |
| Flop Rate by Tier | Risk halves with budget size |
| Budget vs Revenue | 0.748 correlation confirmed |
| Quality Trend | Slow improvement 2011-2025 |
| Language Revenue | Chinese leads non-English |
| Correlation Heatmap | Budget barely predicts quality |
| Rating Distribution | Near-normal, slight left skew |
| Popularity Trend | Sharp spike from 2022 |
| Genre Ratings | Documentary highest rated |

---

## CEO Executive Summary

Based on 3,525 movies with verified financial data, 
the data recommends a clear investment strategy for 
Netflix film production. Horror emerges as the 
strongest risk-adjusted opportunity — delivering 108% 
median ROI on an average budget of just $14.7M, with 
Animation (127%) and Family (117%) close behind. 
The data strongly advises against Western productions, 
the only genre with negative median ROI at -41%, and 
against Thriller despite its reputation — after 
correcting for corrupt budget entries, Thriller's true 
median ROI is only 35.6%. The safe strategy is a 
mid-budget Horror or Animation production in the 
$10-50M range, optionally in Korean or Chinese to 
access markets generating $42-225M average revenue. 
The machine learning model independently validates 
this — a $15M Horror film is predicted as a success 
with 76% confidence and $52.5M projected revenue.

---

## Tools and Libraries

- Python 3.10
- Pandas — data cleaning and analysis
- NumPy — numerical operations
- Matplotlib and Seaborn — visualization
- Scikit-learn — machine learning models
- Jupyter Notebook

---

## How To Run

```bash
git clone https://github.com/ankit7756/netflix-movie-analysis
cd netflix-movie-analysis
pip install -r requirements.txt
jupyter notebook
```

Run notebooks in order:
1. `netflix_analysis.ipynb`
2. `netflix_visualizations.ipynb`
3. `netflix_ml.ipynb`

---

## Author

**Ankit Sharma**
BSc Computing — Softwarica College / Coventry University
[LinkedIn](https://www.linkedin.com/in/ankit7756/) •
[GitHub](https://github.com/ankit7756)
